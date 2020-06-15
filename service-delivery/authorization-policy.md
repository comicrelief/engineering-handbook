# Authorization Policy
***

The engineering team implements a Zero Trust model, or the practice of shifting access control from the perimeter of the
org to the individuals.

## Glossary

* [External User Access Policy](#external-user-access-policy)
* [Internal User Access Policy](#internal-user-access-policy)
    * [SSO](#sso)
    * [Rules of the Road](#rules-of-the-road)
    * [Administrative Permissions](#administrative-permissions)
* [Service Authorization Controls](#service-authorization-controls)

## External User Access Policy

[AWS Cognito](https://aws.amazon.com/cognito/) is our primary authentication
provider for members of the public. As a default we should be implementing a
strong password policy and enforced two factor authentication for all users. This has the benefit of being automatically
scanned as part of our security review and is implemented using best-in-class technology from the world's leading hosting
provider.

Under no situation should we ever have the need to roll our own cryptography or authorization mechanisms.

## Internal User Access Policy

Centralized access management is key to ensuring that the correct team-members have access to the correct data and
systems and at the correct level.

Our access controls are guided by the principle of least privilege and need-to-know.
These controls apply to information and information processing systems at the application and services.

A team member or application should only be granted the minimum necessary access to perform their function. An access is
considered necessary only when a user cannot perform a function without that access. If an action can be performed
without the requested access, it's not considered necessary. Least privilege is important because it protects us and our
customers from unauthorized access and configuration changes and in the event of an account compromise by limiting access.

### Single Sign-On (SSO)

When provisioning or using a service for internal users, the first port of call should be to use SSO. We use three SSO
providers depending on the use case.

#### AWS SSO

This is used to access any of our cloud accounts and related monitoring tooling.
Users are able to create short-lived access tokens for interacting with AWS
services.

#### Comic Relief SSO (Azure AD)

This is used when accessing internal staff facing systems and is the easiest way for non-engineering members of staff to
access systems.

#### GitHub SSO

This is used for members of the Digital & Innovation team to access development
and build tooling including CI/CD systems.

### Rules of the Road

As a team we have the following requirements that reduce security risks. These
should be implemented in addition to the Comic Relief IT policy.

#### 1. Use a password manager

Use a password manager to store your passwords. This way, you only need to memorize a few strong passwords: your master
password for the password manager and your laptop password. Make sure that the password manager supports two factor
authentication and that the password manager password is unique.

#### 2. Enable two factor authentication (if available)

Use 2 factor authentication whenever it is available. This should allow you to mitigate most risks from password
compromise. We check and enforce this on a quarterly basis.

#### 3. Use your Comic Relief email account

Don't use your personal email account to register for services. Comic Relief provides spam and virus filtering which
will detect a wide range of vulnerabilities.

#### 4. No shared accounts

Unless there is no other option, then do not share your passwords or account with other members of staff.

#### 5. Use unique and strong passwords

Use your password manager to generate a unique random password, with a minimum
of 12 characters, for each service you use.

### Administrative permissions

Administrative permissions should be considered operational in nature. This means that they are granted for the sole
purpose of system management, configuration, and support. They should be recognized as privileged accounts and as such,
activities must be logged and the logs protected and regularly reviewed.

## Service Authorization Controls

When considering the implementation of any service and its communication with other resources and services within our
domain, blast radius reduction should be of primary concern.

The following authorization controls should be maintained and implemented for
all service implementations and communication:

- All applications should have their own deployment keys, and these should be
  cycled on a 3 month basis.

- All applications should only have access to the cloud resources that they need.

- Resources should not be shared between staging and production environments.

- Communication between services should be via HTTPS or message queues, and
  should be restricted by a unique API key for that service. In the event of a
  breach, this reduces blast area and allows us to track down the source much
  faster.

- Data should always be encrypted at rest and in transit. The preference here
  is to use native AWS encryption via KMS.

- Applications should be restricted by type to a dedicated cloud account for
  that type. An example of this would be data infrastructure not sitting within
  the same cloud account as public-facing API infrastructure, and only sending
  data to the data infrastructure using a key with no read permissions. This
  helps to reduce the blast radius of an infrastructure breach.
