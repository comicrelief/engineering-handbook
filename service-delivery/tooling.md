# Tooling
***

At Comic Relief, we have a long history of continuous integration and have been using tools such as Jenkins, Travis, 
Circle CI, Netlify and Concourse CI. Over the last couple of years, we have settled on the following tools:

- [API Documentation](#api-documentation)
- [Automated Testing](#automated-testing)
- [Coding Standards](#coding-standards)
- [Content Management Systems](#content-management-systems)
- [Dependency Management](#dependency-management)
- [Domain Management](#domain-management)
- [Hosting](#hosting)
- [Monitoring](#monitoring)
- [Orchestration](#orchestration)
- [Preview Environments](#preview-environments)
- [Team Communication Tools](#team-communication-tools)
- [Third Party Dependency Testing](#third-party-dependency-testing)
- [Version Control Systems](#version-control-systems)

## API Documentation
We use the following API documentation tools to provide API documentation to internal and external users of our services.

- **APIDoc** used to document all of our Serverless NodeJS APIs.

## Automated Testing
We use the following tooling to automatically and manually test code.

- **Artillery** is used to fire requests at a service and ensure that it can handle customer load.

- **BackstopJS** for ensuring that pages do not visually regress.

- **Behat** is used for end to end testing of legacy PHP applications.

- **Browserstack** is used by **Nightwatch** and **Behat** to test against browsers and devices.

- **Cypress** is used to run headless Chrome-based end to end tests on frontend repositories. 

- **Jest** is used to take snapshots of visual components and to run unit tests.

- **Lighthouse** for ensuring that web pages meet accessibility, performance and SEO standards.

- **Nightwatch** is used for end to end testing journeys.

- **Mocha** is used to write unit, feature, integration and end to end tests.

- **Postman** is used to locally test APIs and share those tests among developers.

## Coding Standards
We use the following tools to ensure developers adhere to coding standards across projects,

- **ESLint** for ensuring code quality / standards across our team.
- **Prowler** for ensuring compliance of architectural standards within AWS.

For more information, see the [coding standards guide here](coding-standards.md)

## Content Management Systems
We use the following content management systems to provide an editor interface to edit consumer facing content,

- **Contentful** is our new content management system, which exposes a GraphQL endpoint and allows for more flexible 
content use across our front and backend applications.

## Dependency Management
We use the following dependency management systems to pull in dependencies from third parties,

- **Composer** is used in our legacy PHP projects to bring in dependencies.

- **Yarn** is used in all of our NodeJS projects over NPM as we have generally found it to be faster.

# Domain Management
We use the following tools and services to manage our domains,

- **AWS Route53** provides the dns for all of our domains and sub-domains.

- **CSC** is the registrar for all of our domains and delegates the name servers to route53.

- **Pulumi** is used to orchestrate the cloudformation to create and manage our domains.

For more information, see the [domain management guide here](../backend/domain-management.md)

## Hosting
We use the following hosting providers to host our consumer facing services and applications,

- **AWS** is used as the primary hosting service for all of our applications

- **Platform.sh** is used to host our legacy Drupal sites (comicrelief.com and sportrelief.com)

- **Pivotal Web Services** is a container service used to host our legacy PHP applications

For more information, see the [hosting related guide here](hosting.md)

## Monitoring
We use the following systems to monitor and alert us to issues within our applications and services,

- **AWS Cloudwatch** is used to store raw logs from our Serverless applications.

- **IOPipe** is used to aggregate runtime and invocation information and errors from our Serverless backends and raise 
alerts to errors.

- **Sentry** is used to record and alert to errors in both frontend and backend code.

- **Slack** is used to alert developers to issues from all of our monitoring tools.

- **Statuspage.io** is used to communicate issues and degradation of functionality to our stakeholders.

- **Wormly** used to monitor uptime of public facing endpoints and test SSL validity.

For more information, see the [monitoring related guide here](monitoring.md)

## Orchestration
We use the following products and services to orchestrate code deployment.

- **CircleCI** for running tests on every pull request. These tests are great for testing 
things in isolation and are ideally suited for front-end tests or unit tests, although we’re using Cypress to do end-to-end 
testing against sandbox back-end environments.

- **Concourse CI** for all staging and production deployments, running various test suites and all sort of utility / 
housekeeping tasks that are essential to keeping platforms running happily. We also use this for periodical tasks such as 
running Lighthouse, performance reviews, visual regression, or longer-running end to end tests we don’t wish to run on 
every deployment.

- **Travis CI** is now our legacy way of running tests at a pull request stage and is nearly fully replaced by CircleCI 

For more information, see the [pipeline guide here](pipelines.md)

## Preview Environments
As much as possible we try to provide preview environments for pull requests, to allow easy review and testing of 
developer code changes.

- **AWS** used to deploy branch previews of static web applications to AWS S3.

- **Gatsby Preview** is used to provide real time preview of changes in **Contentful** in our **Gatsby** sites.

- **Netlify** for deployment previews of our static front-end applications, mostly the different ReactJS codebases.

- **Platform.sh** used for pull request previews of our Drupal sites.

## Team Communication Tools
We use the following team communication tools to ensure a steady flow of communication within the development team,

- **Pull Panda** to provide statistics and reminders around pull requests and comments around them.

- **Slack** provides us with a platform to communicate within our team and also provides us with alerting to issues.

## Third Party Dependency Testing
The following tools are used to test third party dependencies within our code bases.

- **Dependabot** A free tool provided by github that provides third party dependency testing. Does the same as Snyk, but
catches a varying range of errors.

- **Roave Secuirty Advisories** is imported via composer for all legacy PHP applications. It is a composer package that 
prevents installation of packages with known security issues.

- **Snyk** for automated testing of code base dependencies, ensuring that packages are up to date and do not have any 
known security vulnerabilities.

## Version Control Systems
We use the following version control systems to track changes to code and as storage for it,

- **Docker Hub** is used to host docker images used for our CI/CD systems and legacy PHP applications.

- **Github** is our primary VCS system and is used for the sharing of all public and private repositories.

- **NPM** is used to share our common tooling across projects and with the wider programming community.