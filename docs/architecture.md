# Architecture
***

While we prefer in-code and live documentation over wiki pages, these are best suited to single services and we don't have a place to document broader processes that involve the interaction of several services. This section aims to provide that overview of how various services fit together.

## `supporter-event-service`

The service aims to propagate [supporter identities](https://github.com/comicrelief/data-models/tree/master/src/schemas/user-service/models/requests) to `serverless-user-service` and [supporter events](https://github.com/comicrelief/data-models/tree/master/src/schemas/erp/models/actions) to `serverless-erp-service`.

`serverless-user-service` and `serverless-erp-service` exist on one region only because of their structure; should they be unavailable for any reason, propagation of data from upstream services may be interrupted. `supporter-event-service` is a multi-region service designed to handle incoming traffic from all sources. Events are queued to SQS and processed one by one.

When identities are supplied to the `serverless-user-service` section of the payload, `supporter-event-service` returns a salted hash of the identity that can be used by upstream services to identity resources, so that anonymisation won't break relationships between data and services.

`supporter-event-service` is supposed to handle only write requests to `serverless-user-service` and `serverless-erp-service`. If an upstream service requires data stored in either service, it should either:

- **For critical paths**: store a copy of the data in the service itself
- **For non-critical paths**: gracefully handle request failures

Critical path here means whether it is acceptable or not to present a failure to and end user.

Every service should be able to operate independently from `serverless-user-service` and `serverless-erp-service` for all the critical paths; if a path is deemed non-critical, the services can and should be queued directly.

While `serverless-user-service` and `serverless-erp-service` are unlikely to be unavailable, under no circumstances should a critical path upstream depend on either, for read or for writes, as they are not multiregional services.

### Supporter data flow

```mermaid
graph LR
  fundraiser-signups["serverless-contact-store (Tom)"] --- event
  giftaid["serverless-giftaid (Corin)"] --- event
  prize-platform["serverless-prize-platform (William)"] --- event
  sms[SMS] --- event
  psl["serverless-payments (Labib)"] --- event
  justgiving[JustGiving] --- event
  mobilise[Mobilise] --- event
  marketing-prefs["serverless-marketing-preferences (Adam)"] --- event
  esu["ESU (Adam)"] --- event
  rtbf[Right to be Forgotten] --- event
  shop["Shop (Seb)"] --- event

  event(supporter-event-service) --> producer

  subgraph supporter-event-service
    producer[Producer] -. SQS .-> consumer[Consumer]
    consumer --> action[Action]
  end

  action -- 1 --> user-service[serverless-user-service]
  action -- 2 --> erp-service[serverless-erp-service]

  classDef green fill:#8fd04e,stroke:#70a63b,stroke-width:2px;
  class fundraiser-signups,prize-platform green

  click fundraiser-signups "https://github.com/comicrelief/serverless-contact-store" "Click to go to Contact Store repo"
  click giftaid "https://github.com/comicrelief/serverless-giftaid" "Click to go to Giftaid repo"
  click prize-platform "https://github.com/comicrelief/serverless-prize-platform" "Click to go to Prize Platform repo"
  click psl "https://github.com/comicrelief/serverless-payments" "Click to go to Payments repo"
  click marketing-prefs "https://github.com/comicrelief/serverless-marketing-preferences" "Click to go to Marketing Preferences repo"

  click event "https://github.com/comicrelief/supporter-event-service" "Click to go to Supporter Events Service repo"
  click producer "https://github.com/comicrelief/supporter-event-service" "Click to go to Supporter Events Service repo"
  click consumer "https://github.com/comicrelief/supporter-event-service" "Click to go to Supporter Events Service repo"
  click action "https://github.com/comicrelief/supporter-event-service" "Click to go to Supporter Events Service repo"

  click user-service "https://github.com/comicrelief/serverless-user-service" "Click to go to User Service repo"
  click erp-service "https://github.com/comicrelief/serverless-erp-service" "Click to go to ERP Service repo"
```
