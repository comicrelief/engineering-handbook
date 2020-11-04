# Supporter Data Flow

Upstream services (anything that interacts with end users) need to pass their data to `serverless-user-service` and `serverless-erp-service` for warehousing and analytics. The specifics of each integration and what data should be provided is to be defined in each service's documentation. This page documents the data flow process itself.

## Data Models

At the end of the journey:

- `serverless-user-service` should receive the user data required to generate a user entry
- `serverless-erp-service` should receive the data required to satisfy the Doc Types defined in ERP Next

Any request payload sent to `supporter-event-service` should validate against the `ProducerRequest` found in `data-models`, which has the following structure:

```javascript
{
  "user-service": PartialSignupRequest,
  "erp-service": ErpProducerRequest,
}
```

Neither key is required but at least one should be defined.

Both `PartialSignupRequest` and `ErpProducerRequest` are meant to be completed by `supporter-event-service`. With _completed_ we mean that sending the _incomplete_ request directly to downstream services will result in HTTP 400, and that `supporter-event-service` will add the missing required keys to the payload (see sections below for details).

See:
- [`ProducerRequest`](https://github.com/comicrelief/data-models/blob/master/src/schemas/supporter-events/models/requests/ProducerRequest.ts)
- [Complete examples (mocks)](https://github.com/comicrelief/data-models/blob/master/src/schemas/supporter-events/mocks/requests/ProducerRequest.mock.ts)
- [`PartialSignupRequest`](https://github.com/comicrelief/data-models/blob/master/src/schemas/user-service/models/requests/SignupRequest.ts)
- [`ErpProducerRequest`](https://github.com/comicrelief/data-models/blob/master/src/schemas/erp/models/requests/ProducerRequest.ts)

### `user-service` key

The `PartialSignupRequest` contains an `identities` key in which you provide a list of the user's identities, for example their email address or phone number. For each of these identities, `supporter-event-service` will hash `identities.content` and put the result in `identities.hash` if it is not already defined, effectively transforming a `PartialSignupRequest` (accepted by `supporter-event-service`) into a complete `SignupRequest` (accepted by `serverless-user-service`).

See:
- [`Identity`](https://github.com/comicrelief/data-models/blob/master/src/schemas/user-service/models/Identity.ts)
- [`PartialSignupRequest` and `SignupRequest`](https://github.com/comicrelief/data-models/blob/master/src/schemas/user-service/models/requests/SignupRequest.ts)

### `erp-service` key

The `ErpProducerRequest` is a simple object containing an array of `ErpAction` objects.

```javascript
{
  "actions": ErpAction[]
}
```

`ErpAction` is a base type for many specific actions relating to each service and the data it requires to submit to ERP. You can check out the structure of each specific action [in `data-models`](https://github.com/comicrelief/data-models/tree/master/src/schemas/erp/models/actions).

See:
- [ErpProducerRequest](https://github.com/comicrelief/data-models/blob/master/src/schemas/erp/models/requests/ProducerRequest.ts)
- [ErpProducerRequest examples (mocks)](https://github.com/comicrelief/data-models/blob/master/src/schemas/supporter-events/mocks/requests/ProducerRequest.mock.ts)

Each `ErpAction` should validate against the following:

```javascript
{
  "type": ErpPayloadTypes,
  "data": {
    // Upstream service specific data
    specific_data_1: any,
    specific_data_2: any,

    // The following key is likely to be required
    // for supporter-specific payloads
    // such as donations, prize tickets, etc.
    // See the `Supporter UUID` section for details
    supporter_uuid: String,

    // If your service doesn't have access
    // to supporter specific information
    // the payload will need to specify
    // the `identity_hash` key so that `supporter-event-service`
    // will be able to complete the payload
    identity_hash: String
  }
}
```

See:
- [`ErpPayloadTypes`](https://github.com/comicrelief/data-models/blob/master/src/schemas/erp/models/common.ts#ErpPayloadTypes)
- [List of `ErpAction` types](https://github.com/comicrelief/data-models/tree/master/src/schemas/erp/models/actions)

## Storing supporter information

Supporter information will be handled and stored by `serverless-user-service` and ERP Next. Upstream services should propagate any supporter information they receive and/or generate to `supporter-event-service` to be correctly pipelined.

When supporter information is propagated to `supporter-event-service`, they will receive one identity hash for each provided identity, which should be stored in the upstream service as part of any entity concerned with the supporter. Additional data, such as first name, last name, or even email and mobile number, should not be stored by default, as it will make it easier for us to handle data inconsinstencies (i.e. supporter information updates) and to comply with GDPR data removal requests. Identity hashes are anonymous and can be used to query `serverless-user-service` to retrieve the matching user.

However, upstream services may need to store additional supporter information. For example, a service may need to trigger emails in an API call that is not provided the email address of the supporter. Querying `serverless-user-service` directly is advised only when the querying service is allowed to fail and retry later.

## Supporter UUID

Your ERP payloads may be related to a specific supporter. This is true for transactions, prize tickets, Shopify orders, etc. The `data.supporter_uuid` key will be used by ERP Next to link the entity with a Supporter entity. However `supporter_uuid` cannot be guaranteed to upstream services as it will be stored on `serverless-user-service`. This is why `supporter-event-service` can help your upstream service complete its payload.

### Scenario 1: The upstream service provides a `user-service` specific payload

As part of your payload to `supporter-event-service` you can specify a `user-service` specific payload. Should `supporter-event-service` receive a `user-service` payload, it will use it to create a user entity on `serverless-user-service`, if it doesn't already exist.

The request to `serverless-user-service` will yield the user UUID, which will be used to populate `data.supporter_uuid`, if it isn't already defined, in all following `ErpAction` objects in the `erp-service` payload.

This means that the upstream service doesn't need to be concerned with `data.supporter_uuid` if it provides a `user-service` payload in the request.

### Scenario 2: The upstream doesn't have access to supporter specific information

Not all services may be storing extensive supporter information, such as plaintext email and mobile number. All they might have access to is an identity hash. This will be true if the service defines multiple endpoints that need to share incremental information with ERP Next, generated through multiple interactions with the service.

`serverless-prize-platform` is an example of such a service. While creating a ticket entry, the lambda will have access to all the user data; but picking a winner among the tickets won't have access to any supporter information that wasn't stored within the service itself.

`supporter-event-service` will need to handle this scenario as well. After all, it has direct access to `serverless-user-service`. Any payload requiring `data.supporter_uuid` can specify `data.identity_hash`. The upstream service should provide the identity hash associated with the supporter email as a standard.

While processing `erp-service` payloads, `supporter-event-service` will match identities to user UUIDs and complete the payload with `data.supporter_uuid` if it is not already defined. Please note that `data.identity_hash` **WILL NOT** be removed in the process.
