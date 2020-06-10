# Production Requirements
***

The production requirements outline the basic tooling set-up, creation of a build pipeline, and how we work our way all
the way up to production deployment and day to day operation. Everyone in the software development life cycle is 
responsible for the security & operation of our products and services.


Our aim is to continuously deliver all products and services that we are creating and maintaining.

* [Architectural Review](#architectural-review)
* [Code Review](#code-review)
* [Data Protection Impact Assessment](#data-protection-impact-assessment)
* [Documentation](#documentation)
* [Failover](#failover)
* [Infrastructure as Code](#infrastructure-as-code)
* [Pipelines & Automated Testing](#pipelines--automated-testing)
* [Manual QA](#manual-qa)
* [Monitoring & Alerting](#monitoring--alerting)
* [Penetration testing](#penetration-testing)

## Architectural Review

When approaching a system that utilises cloud technologies that we do not currently have in our stack or is 
different to anything that we have in our stack. We should look to our cloud partners to provide architectural review at
both the scoping of the project and productionisation of a system. 

By engaging cloud partners at the start of a project,
we can ensure that our approach is sound and we are taking the best route to achieve what we want, our cloud partners
generally have a wide range of experience from different organisations and can be invaluable at this stage. 

By engaging cloud partners prior to taking a project into production, we can run through every section of the 
architecture and discuss assumptions. The review covers the following areas,

- Operational Excellence
- Security
- Reliability
- Performance Efficiency
- Cost Optimization

See the [third party validation](third-party-validation.md) documentation for more information on how we approach 
architectural review.

## Code Review

As part of how we undertake [pull requests](pull-requests.md) and how we deploy all our code via 
[pipelines](pipelines.md), code review is essential to ensure that the code, configuration & infrastructure being
deployed are secure and fit for purpose. We do this by having at least one member of the team review the code.

On all repositories we block deployments to the master environment and require reviews tp be made before merging. The
master environments are therefore treated as a direct representation of what is in production.

## Data Protection Impact Assessment


## Documentation


## Failover


## Infrastructure as Code


## Pipelines & Automated Testing
By undertaking continuous delivery it is imperative that we employ as much automated testing as possible to ensure code 
competence.

As part of taking any application to production, it should have a pipeline. Within that pipeline we should have at 
minimum a staging environment and end to end tests running against staging before deploying to production.

If the application is a frontend application, we should also have lighthouse running in the pipeline to ensure both
the accessibility and performance of the application.

At the pull request level we should be deploying to a preview environment, which should match the environment and
settings in production. By implementing [infrastructure as code](#infrastructure-as-code) this becomes a trivial
action.

See our documentation on [pipelines and automated testing](pipelines.md) for more information.

## Manual QA

See the [manual QA](../qa/manualQA.md) section for details on the QA that should be conducted on all pieces of an
application or service before reaching production.

## Monitoring & Alerting

When taking a product or service to production, we should ensure that we are sending any and all errors from the 
environment to our error logging platforms, this allows us to quantify all issues and allows us to fully utilise
our distributed tracing.

We should also be setting up any foreseeable alerting on all resources and services utilised by the application, to 
ensure the correct operation of these systems. 

See the [monitoring and alerting](monitoring.md) section for information on the monitoring & alerting tools that we employ.

## Penetration testing
It is vitaly important for us to undertake penetration testing in the event of the creation or significant change to any 
new system or application that will contain or transit customer or sensitive information.

See the [third party validation](third-party-validation.md) documentation for information on how we approach 
penetration testing.
