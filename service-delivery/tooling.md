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

We use the following tools to provide API documentation to both internal and
external users of our services.

- **[apiDoc](https://apidocjs.com/)** used to document all of our Serverless
  NodeJS APIs.

## Automated Testing

We use the following tooling to automatically and manually test code.

- **[Artillery](https://artillery.io/)** is used to fire requests at a service
  and ensure that it can handle customer load.

- **[BackstopJS](https://garris.github.io/BackstopJS/)** for ensuring that
  webpages do not visually regress.

- **[Behat](http://behat.org/en/latest/)** is used for end-to-end testing of
  legacy PHP applications.

- **[BrowserStack](https://www.browserstack.com/)** is used by **Nightwatch**
  and **Behat** to test against a wide range of browsers and devices.

- **[Cypress](https://www.cypress.io/)** is used to run headless Chrome-based
  end-to-end tests on frontend repositories.

- **[Jest](https://jestjs.io/)** is used to take snapshots of visual components
  and to run unit tests.

- **[Lighthouse](https://developers.google.com/web/tools/lighthouse/)** for
  ensuring that web pages meet accessibility, performance and SEO standards.

- **[Nightwatch](https://nightwatchjs.org/)** is used for end-to-end testing
  journeys.

- **[Mocha](https://mochajs.org/)** is used to write unit, feature, integration
  and end-to-end tests.

- **[Postman](https://www.postman.com/)** is used to locally test APIs and
  share those tests among developers.

## Coding Standards

We use the following tools to ensure developers adhere to coding standards
across projects.

- **[ESLint](https://eslint.org/)** for ensuring code quality across our team.

- **[Prowler](https://github.com/toniblyx/prowler)** for ensuring compliance of
  architectural standards within AWS.

For more information, see the [coding standards guide](coding-standards.md).

## Content Management Systems

We use the following content management systems to provide an editor interface
to edit consumer-facing content.

- **[Contentful](https://www.contentful.com/)** is our new content management
  system, which exposes a GraphQL endpoint and allows for more flexible content
  use across our front and backend applications.

## Dependency Management

We use the following dependency management systems to pull in dependencies from
third parties.

- **[Composer](https://getcomposer.org/)** is used in our legacy PHP projects
  to bring in dependencies.

- **[Yarn](https://yarnpkg.com/)** is used in all of our NodeJS projects over
  NPM as we have generally found it to be faster.

# Domain Management

We use the following tools and services to manage our domains,

- **[AWS Route 53](https://aws.amazon.com/route53/)** provides the DNS for all
  of our domains and subdomains.

- **[CSC](https://www.cscglobal.com/service/dbs/digital-brand-services/)**
  is the registrar for all of our domains, and delegates the name servers to
  Route 53.

- **[Pulumi](https://www.pulumi.com/)** is used to orchestrate the
  CloudFormation to create and manage our domains.

For more information, see the [domain management guide here](../backend/domain-management.md)

## Hosting

We use the following hosting providers to host our consumer facing services and applications.

- **[AWS](https://aws.amazon.com/)** is used as the primary hosting service for
  all of our applications.

- **[Platform.sh](https://platform.sh/)** is used to host our legacy Drupal
  sites (comicrelief.com and sportrelief.com).

- **[Pivotal Web Services](https://run.pivotal.io/)** is a container service
  used to host our legacy PHP applications.

For more information, see the [hosting guide](hosting.md).

## Monitoring

We use the following systems to monitor and alert us to issues within our
applications and services.

- **[AWS CloudWatch](https://aws.amazon.com/cloudwatch/)** is used to store raw
  logs from our Serverless applications.

- **[Epsagon](https://epsagon.com/)** is used to aggregate runtime and
  invocation information and errors from our Serverless backends and raise
  alerts to errors.

- **[Sentry](https://sentry.io/)** is used to record and alert to errors in
  both frontend and backend code.

- **[Slack](https://slack.com/)** is used to alert developers to issues from
  all of our monitoring tools.

- **[Statusfy](https://statusfy.co/)** is used to communicate issues and
  degradation of functionality to our stakeholders.

- **[Wormly](https://www.wormly.com/)** used to monitor uptime of public-facing
  endpoints and test SSL validity.

For more information, see the [monitoring related guide](monitoring.md).

## Orchestration

We use the following products and services to orchestrate code deployment.

- **[CircleCI](https://circleci.com/)** for running tests on every pull request.
  These tests are great for testing things in isolation and are ideally suited
  for frontend tests or unit tests, although we’re using Cypress to do
  end-to-end testing against sandbox backend environments.

- **[Concourse CI](https://concourse-ci.org/)** for all staging and production
  deployments, running various test suites and all sorts of utility or
  housekeeping tasks that are essential to keeping platforms running happily.
  We also use this for periodical tasks such as running Lighthouse, performance
  reviews, visual regression, or longer-running end-to-end tests we don’t wish
  to run on every deployment.

- **[Travis CI](https://travis-ci.org/)** is now our legacy way of running
  tests at a pull request stage and is nearly fully replaced by CircleCI.

For more information, see the [pipeline guide](pipelines.md).

## Preview Environments

We try to provide preview environments for pull requests to allow easy review
and testing of code changes.

- **[AWS](https://aws.amazon.com/)** used to deploy branch previews of static
  web applications to AWS S3.

- **[Gatsby Preview](https://www.gatsbyjs.com/preview/)** is used to provide a
  realtime preview of changes in **Contentful** in our **Gatsby** sites.

- **[Netlify](https://www.netlify.com/)** for deployment previews of our static
  front-end applications, mostly the different ReactJS codebases.

- **[Platform.sh](https://platform.sh/)** used for pull request previews of our
  Drupal sites.

## Team Communication Tools

We use the following team communication tools to ensure a steady flow of
communication within the development team.

- **[Pull Panda](https://pullpanda.com/)** to provide statistics and reminders
  around pull requests and comments around them.

- **[Slack](https://slack.com/)** provides us with a platform to communicate
  within our team and also provides us with alerting to issues.

## Third Party Dependency Testing

The following tools are used to test third-party dependencies within our
codebases.

- **[Dependabot](https://dependabot.com/)** A free tool provided by GitHub that
  provides third-party dependency testing. Does the same as Snyk, but catches a
  varying range of errors.

- **[Roave Security Advisories](https://github.com/Roave/SecurityAdvisories)**
  is imported via Composer for all legacy PHP applications. It is a Composer
  package that prevents installation of packages with known security issues.

- **[Snyk](https://snyk.io/)** for automated testing of codebase dependencies,
  ensuring that packages are up to date and do not have any known security
  vulnerabilities.

## Version Control Systems

We use the following version control systems to track changes to code and as storage for it,

- **[Docker Hub](https://hub.docker.com/u/comicrelief)** is used to host docker
  images used for our CI/CD systems and legacy PHP applications.

- **[GitHub](https://github.com/comicrelief/)** is our primary VCS system and
  is used for the sharing of all public and private repositories.

- **[NPM](https://www.npmjs.com/)** is used to share our common tooling across
  projects and with the wider programming community.
