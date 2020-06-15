# Domain Management
***

We manage all of our domains from the domains repository, which uses
[Pulumi](https://www.pulumi.com/) to deploy domain changes to
[Amazon Route 53](https://aws.amazon.com/route53/).

This is currently not in CI/CD, however the ongoing plan is to move it to an automated process.

The nameservers from CSC are delegated to Route 53.
