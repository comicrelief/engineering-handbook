# Application & Cloud Security
***

By adopting NoOps, we shift many of the traditional concerns towards our cloud providers and extend what the 
infrastructure provides, shifting the traditional view of the shared security model.

In serverless computing the management and allocation of resources, such as uptime, server maintenance, patching, backup
and security are all managed by cloud providers instead of systems administrators and IT operations staff. Further to 
this, the execution environment is in an ephemeral container, with a read-only file system and highly restrictive 
permissions. Controls like these greatly improve inherent security.

With reduced need for infrastructure based protections, our Security is effectively reduced to solid coding and strict 
configuration management.

## Key Security Considerations
***

Our key security considerations and practices can be found below.

- [Authentication of users](#authentication-of-users)
- [Authorization controls](#authorization-controls)
- [Logging and maintaining audit trails](#audit-trail)
- [Application Layer Firewalls](#application-layer-firewall-waf)
- [Dependency Vulnerabilities](#dependency-vulnerabilities)
- [Least-privileged roles and permissions](#least-privileged-access)
- [Data leak prevention](#data-leak-prevention)
- [Static Analysis](#static-analysis)
- [Obsolete Application & Service Removal](#obsolete-application--service-removal)
- [End to end Observability](#end-to-end-observability)
- [Incidents](#incidents)
- [Alignment with Best Practices](#alignment-with-best-practices)
- [Security Automation](#security-automation)
- [Penetration Testing](#penetration-testing)
- [Production Requirements](#production-requirements)

### Authentication of users

For how we authenticate Comic Relief users, see the 
[external user access policy](authorization-policy.md#external-user-access-policy).

### Authorization controls

For how we implement authorization controls, see the 
[service authorization controls policy](authorization-policy.md#service-authorization-controls).

### Audit trail

It is imperative that we are able to track changes to all code and infrastructure. With all infrastructure and code 
being defined as code and stored within Github. 

This means that any changes have to be peer reviewed and are tested adequately before hitting production. Malicious 
actors cannot update code or infrastructure, without it firstly being reviewed by other members of the engineering team. 
Engineers should only have read only access to the GUI.

We also use AWS CloudTrail to track and record all changes to infrastructure and systems, to provide a log of all changes
that are made.

### Application Layer Firewall (WAF)

We implement AWS WAF on all endpoints that we deploy. We have implemented security rules based on the OWASP 
top 10 and also implement rules such as IP restrictions and rate limiting via the WAF.

### Dependency Vulnerabilities

We utilise snyk and github dependabot to check dependencies at the pull request and pipeline level to ensure that there
are no known security vulnerabilities within third party dependencies before shipping to production. 

### Least Privileged Access

See our [authentication policy](authorization-policy.md) for how we implement zero trust.

### Data leak prevention

For automated tooling to ensure alignment to coding standards, read the 
[following section](tooling.md#coding-standards) on the tooling that we implement.

For how we authenticate internal users, see the 
[internal user access policy](authorization-policy.md#internal-user-access-policy).

For how we implement authorization controls, see the 
[service authorization controls policy](authorization-policy.md#service-authorization-controls).

For how we penetration test and seek external validation of architectural decissions, see the
[third party validation policy](third-party-validation.md).

### Static Analysis

Static analysis of all code is performed as part of a [pull request](code-review.md). This ensures
that many potential code flaws can be detected early, before introduction into the production environment.

### Obsolete Application & Service Removal

We implement a quarterly review of all cloud assets and services to understand usage of cloud services and retire where
necessary. We do this in conjunction with our cloud monitoring tooling to understand application usage which provides a
fast way for candidature to retirement.

The following steps should be undertaken when retiring a service,

- Inform all stakeholders and give a one month notice period of retirement.
- Remove pipelines
- Remove all cloud resources via cloudformation or other tooling, never in the GUI.
- Remove logging and monitoring alerts
- Remove DNS entries where relevant.
- Archive relevant github repositories where necessary. 

### End to End Observability

Many monitoring and security tools work at the OS or the VM level. This isn’t an option with serverless computing. 
Serverless requires monitoring performance at the invocation level.

Inside all of our applications and services, we aim to surface any and all errors. This allows us to quickly quantify
and qualify issues for inspection.

We implement Epsagon distributed tracing to provide us with automated data correlation, payloa inspection, and 
end-to-end observability within all of our microservices. This allows us to reduce service costs and accelerate 
development through reduced application downtime, faster shipping of features, and saved time in identifying and 
correcting issues. It also allows us to specifically target suspicious behaviour.

We also implement Sentry on all of our backend's and frontend's, this allows us to also detect any client side issues and
remedy accordingly.

### Incidents

See the [Incident Documentation](Incidents/overview.md) documentation for information as to how we approach this.

### Alignment with Best Practices

We should always be aiming to align ourselves with the best standards available within our industry. Whether by 
implementing best in class [coding standards](coding-standards.md), automating security testing as
part of our [pipelines](pipelines.md) or by engaging external reviewers from the design stage to
ensure that our architecture is the best fit.

Our core premise is to reduce and offload attack surface wherever possible. We do this by utilising cloud services and
managed services wherever possible.

Whenever implementing new services we should be aiming to engage our cloud partners to provide insight into application 
design as part of our [production requirements](prodreq.md).

We also implement prowler as part of our security pipeline, this automatically scans all of our cloud infrastructure on a 
weekly basis and generates a report against the following compliance guidelines,

- Identity and Access Management
- Logging
- Monitoring
- Networking
- CIS Level 1
- CIS Level 2
- Forensics
- GDPR
- HIPAA
- Trust Boundaries

More information is available in the [Third Party Validation](third-party-validation.md) section as to how we engage
external partners to ensure the security and functionality of our systems.

### Penetration Testing

See the [Third Party Validation](third-party-validation.md) documentation for information as to how we approach this.

### Production Requirements

We have implemented a list of requirements which all of our production environments must contain in order to go to 
production, see the [production requirements documentation](prodreq.md) for more information.

