# Tooling

At Comic Relief, we have a long history of continuous integration and have been using tools such as Jenkins, Travis, 
Circle CI, Netlify and Concourse CI. Over the last couple of years, we have settled on the following tools:

## API Documentation
- **APIDoc** used to document all of our Serverless NodeJS API's.
- **Swagger** used to document our legacy PHP API's.

## Coding Standards
- **ESLint** for ensuring code quality / standards across our team.

## Dependency Testing
- **Snyk** for automated testing of code base dependencies, ensuring that packages are up to date and do not have any 
known security vulnerabilities.

## Hosting
- **AWS** is used as the primary hosting service for all of our applications

- **Platform.sh** is used to host our legacy Drupal sites (comicrelief.com and sportrelief.com)

- **Pivotal Web Services** is a container service used to host our legacy PHP applications

For more information, see the [hosting related guide here](hosting.md)

## Monitoring
- **AWS Cloudwatch** is used to store raw logs from our Serverless applications.

- **IOPipe** is used to aggregate runtme and invocation information and errors from our Serverless backends and raise 
alerts to errors.

- **Sentry** is used to record and alert to errors in both frontend and backend code.

For more information, see the [monitoring related guide here](monitoring.md)

## Orchestration
- **CircleCI** for running tests on every pull request. These tests are great for testing 
things in isolation are ideally suited for front-end tests or unit tests, although we’re using Cypress to do end-to-end 
testing against sandbox back-end environments.

- **Travis CI** is now our legacy way of running tests at a pull request stage and is nearly fully replaced by CircleCI 

- **Concourse CI** for all staging and production deployments, running various test suites and all sort of utility / 
housekeeping tasks that are essential to keep platforms running happily. We also use this for periodical tasks such as 
running Lighthouse, performance reviews, visual regression, or longer-running end to end tests we don’t wish to run on 
every deployment.

## Preview Environments
- **AWS** used to deploy branch previews of static web applications to AWS S3.

- **Netlify** for deployment previews of our static front-end applications, mostly the different ReactJS codebases.

- **Platform.sh** used for pull request preview of our Drupal sites.

## Testing
- **BackstopJS** for ensuring that pages do not visually regress.

- **Behat** is used for end to end testing of legacy PHP applications.

- **Browserstack** is used by **Nightwatch** and **Behat** to test against browsers and devices.

- **Cypress** is used to run headless chrome based end to end tests on frontend repositories. 

- **Jest** is used to take snapshots of visual components and to run unit test.

- **Lighthouse** for ensuring that web pages meet accessibility, performance and SEO standards.

- **Nightwatch** is used for end to end testing journeys.

- **Mocha** is used to write unit, feature, integration and end to end tests.

- **Postman** is used to locally test API's and share those tests among developers.
