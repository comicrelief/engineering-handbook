# Runbooks
***

Our aim is to plan our response to potential incidents in advance. Principled
incident management can go out the window in real-life situations. Our runbooks,
alongside [gamedays](gamedays.md), aim to anticipate failure scenarios and plan
for them.

As part of our [production requirements](prodreq.md), runbooks should be created before a system is put into a
production settings.

At minimum, runbooks should analyse the following potential scenarios:

- Failure of any third party dependancies
- Failure of data infrastructure
- Failure of core hosting provider
- Failure of any hosting provider services
- Failure of domain routing and fallback

Each failure scenario should be marked based on the following grading:

1. Failure can be monitored within the team, but has automatic failover.

2. Failure will require some manual steps to resolve.

3. Stakeholders need to be communicated with and actions undertaken by them.

By undertaking the process of runbook creation, we should highlight which issues fall into category 3 and aim to develop
fallbacks that allow for these to be migrated into category 1 or 2 issues.

The runbooks should also contain a resolution strategy and a communication strategy for each scenario.

These runbooks should be freely visible by the engineering team and visible as
part of an application's documentation.
