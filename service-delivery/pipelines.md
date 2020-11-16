# Pipelines & Automated Testing
***

We utilise CI/CD systems to deploy all code and infrastructure. This as vitaly
important as it means that all knowledge around how applications and services
operate is stored in VCS.

Once changes have been through the [pull request](code-review.md) review
process and is merged into the master branch, it will trigger and flow through
its CI/CD pipeline until it hits production (provided that all tests pass).

## Concourse

We use [Concourse CI](https://concourse-ci.org/) to run all our pipelines.
Pipeline configuration is usually managed in separate bootstrap repos for each
project.

### Naming

In order to get the best out of Concourse, we should name pipelines, jobs and tasks following a convention, enforcing clarity and simplicity.

#### Pipelines

A pipeline name should match the associated repository name when possible. This will allow us to find a pipeline by copy-pasting the repository name.

**Example**
- Repository: `serverless-user-service`
- Pipeline: `serverless-user-service`

#### Jobs

A job name should be a lowercased, hyphenated string. It should NOT be prefixed by the pipeline name.

The string should go from more generic to more specific identifiers, describing what a job is supposed to do. We should always try to re-use words across pipelines and to keep the job names short, so that reviewing a pipeline is easier at glance. `test` and `deploy` are common prefixes.

**Example**
- Repository: `supporter-event-service`
- Pipeline: `supporter-event-service`
- Job 1: `test-unit`
- Job 2: `test-feat`
- Job 3: `test-nightly`
- Job 4: `test-sanity`
- Job 5: `deploy-staging`
- Job 6: `deploy-production`

#### Tasks

A task name should be a lowercase, hyphenated string. Where the parent job contains only a task, the task name should match the job name. Otherwise, the task name should be composed by the job name, postfixed by a short description of the task.

**Example 1**
- Repository: `serverless-user-service`
- Job: `test-unit`
- Task: `test-unit`

**Example 2**
- Repository: `serverless-prize-platform`
- Job: `deploy-production`
- Task 1: `deploy-production-primary`
- Task 2: `deploy-production-sleep-5-minutes`
- Task 3: `deploy-production-secondary`

## Relevant Articles

- [Pipelines Everywhere](https://medium.com/comic-relief/pipelines-everywhere-9eb284f5bee3)
