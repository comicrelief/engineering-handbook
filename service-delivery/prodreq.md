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

If a new provider is being on-boarded or new classifications of data are being stored with that provider that has not
been through the DPIA process, a DPIA form has to be completed and reviewed / approved by the compliance team before the
new application or service enters production and takes data.

## Documentation

### Architectural
As part of any project it is imperative to document the architectural assumptions that were made as part of a readme.
This allows for engineers to pick up a project and gain a quick understanding of the bussiness and technology requirements
that have lead to architectural decisions to be made.

### API
When deploying an API we should provide full API documentation that is hosted alongside the API, this provides engineers
with a clear integration guide.

### Code
We should document code when it is not obvious as to the function of code. This is a dark art, so the default should be
if in doubt, add a comment. However clear function naming and abstractions, should remove the need for over documentation.

## Failover
For all applications, it is important to consider an application and all of it's components and how these may fail in
a production setting. We usually start the process of considering our failover strategy by building [runbooks](runbooks.md).

### Backend's
Serverless technologies by their very nature are usually highly fault, with applications 
sitting at the regional level. This means that they usually distributed across 3 availability zones and therefore
across 9 data centres at minimum

Dependant on the need for robustness of the application, we will also deploy to a backup region with a traffic routing 
policy. The traffic routing policy will analyse all dependencies of the application via a status endpoint, on failure
the status will return a failure and the route will divert to the failover region.

### Frontend's
All frontend's are hosted in S3 and via Cloudfront. As cloudfront is a globally hosted service spanning many data centres
we have very few worries in this area.

### Databases
Production databases should always be deployed with with a multi availability zone master, to provide redundancy in case
of issue with an availability zone. Read replicas should also always be in place, to ensure that large queries cannot
take down data ingress into the write database.

In certain applications such as live income reporting, we also deploy cross regions, however this is always based on a
risk vs reward basis.

## Infrastructure as Code
For all applications and services, architecture is defined by the configuration and code. There primary reasons to
to do this are as follows,

- All stages of the application match production, this ensures that any test results will match what we see in a 
production setting.
- We have a clear audit trail of changes made to architecture via VCS
- All changes to architecture go through the [code review](pull-requests.md) process.
- Individual knowledge of architecture is shared within the engineering team.

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
