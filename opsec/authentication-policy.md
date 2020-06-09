# Authentication Policy

The engineering team implements a Zero Trust model, or the practice of shifting access control from the perimeter of the
org to the individuals.

Centralized access management is key to ensuring that the correct team-members have access to the correct data and 
systems and at the correct level. Our access controls are guided by the principle of least privilege and need-to-know. 
These controls apply to information and information processing systems at the application and services.

## Glossary

* [External User Access Policy](#external-user-access-policy)
* [Internal User Access Policy](#internal-user-access-policy)
    * [SSO](#sso)
    * [Rules of the Road](#rules-of-the-road)
* [Service Authorization Controls](#service-authorization-controls)

## External User Access Policy

## Internal User Access Policy
As a team we have the following requirements that reduce security risks, these should be implemented in addition to the 
Comic Relief IT policy.

### SSO
When provisioning or using a service for internal users, the first port of call should be to use SSO. We use three SSO
providers depending on the use case.

#### AWS SSO
This is used to access any of our cloud accounts and related monitoring tooling.

#### Comic Relief SSO (Azure AD)
This is used when accessing internal staff facing systems and is the easiest way for non-engineering members of staff to
access systems.

#### Github SSO
This is used for members of the Digital & Innovation team to access development & build tooling including CI/CD systems.

### Rules of the Road
#### Use a password manager

Use a password manager to store your passwords. This way, you only need to memorize a few strong passwords: your master 
password for the password manager and your laptop password. Make sure that the password manager supports two factor 
authentication and that the password manager password is unique.

#### Enable two factor authentication (if available)

Use 2 factor authentication whenever it is available. This should allow you to mitigate most risks from password 
compromise.

#### Use your Comic Relief email account

Don't use your personal email account to register for services. Comic Relief provides spam and virus filtering which
will detect a wide range of vulnerabilities.

#### No shared accounts

Unless there is no other option, then do not share your passwords or account with other members of staff.

#### Use unique and strong passwords

Use your password manager to generate a random unique password with a minimum of 12 characters for each service you use

## Service Authorization Controls
