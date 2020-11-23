# Coding Standards
***

This page outlines the tooling and standards that we align ourselves to when writing backend applications. Our aim is to
produce clean and maintainable code. If our code lacks consistency, is poorly laid out and undocumented, we are
adding to the overall complexity of our system.

## NodeJS Projects

In all cases, we use [ESLint](https://eslint.org/) to ensure that coding standards are adhered to.

We use the following ESLint plugins together.

- [AirBNB coding standards](https://www.npmjs.com/package/eslint-config-airbnb)
- [SonarJS rules](https://www.npmjs.com/package/eslint-plugin-sonarjs) to detect bugs and suspicious patterns in your code.
- [Unicorn Rules](https://www.npmjs.com/package/eslint-plugin-unicorn)

Rule exceptions should not be made in projects unless absolutely necessary, with an active effort to remove exceptions to
rules wherever possible.

## PHP Projects

For our PHP projects we use [PHPCS](https://github.com/squizlabs/PHP_CodeSniffer) using the PSR2 coding standards.

We also use [PHPCD](https://github.com/sebastianbergmann/phpcpd) to ensure that code is not duplicated within the project.

## AWS Resource Naming

Historic resources don't follow an agreed convention. However, for all new resources, both in old and new projects, we should follow the schema:

`${service-name}-${service-stage}-${resource-type}-${resource-label}`

**Example 1**
- Where: `sls-best-of` (_staging_)
- What: DynamoDB Table
- Why: Keep references of the most interesting books we read
- Resource: `sls-best-of-staging-dynamodb-best-books`

**Example 2**
- Where: `sls-best-of` (_production_)
- What: DynamoDB Table
- Why: Keep references of the most interesting books we read
- Resource: `sls-best-of-production-dynamodb-best-books`

**Example 3**
- Where: `sls-best-of` (_staging_)
- What: S3 Bucket
- Why: Store photos of the best dishes we cooked
- Resource: `sls-best-of-staging-s3-best-meals-photos`

The advantage of the naming convention is that conveys all the required information to uniquely identity the _where_, _what_ and _why_ of a resource, without relying on contextual information.

## Further Reading

- [Secure development and deployment guidance](https://www.ncsc.gov.uk/collection/developers-collection?curPage=/collection/developers-collection/principles/produce-clean-maintainable-code)
- [How ESLint Makes Me a Better React Developer](https://itnext.io/how-eslint-makes-me-a-better-react-developer-237fb14c00ae)
