# Pipelines & Automated Testing
***

We utilise CI/CD systems to deploy all code and infrastructure. This as vitaly
important as it means that all knowledge around how applications and services
operate is stored in VCS.

Once changes have been through the [pull request](code-review.md) review
process and is merged into the master branch, it will trigger and flow through
its CI/CD pipeline until it hits production (provided that all tests pass).

We use [Concourse CI](https://concourse-ci.org/) to run all our pipelines.
Pipeline configuration is usually managed in separate bootstrap repos for each
project.

## Relevant Articles

- [Pipelines Everywhere](https://medium.com/comic-relief/pipelines-everywhere-9eb284f5bee3)
