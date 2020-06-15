# Coding in the open
***

We code "in the open" for many of our projects at Comic Relief, which means
that our code is publicly visible. Some of these projects are contributed as
open-source projects, whilst others might not be relevant outside Comic Relief.
However, coding in the open encourages us to adhere to high development
standards and to be transparent with the tools we use.

## Before going open

* Secrets should never be added to a public repository, only references to secrets via environment variables can be part of the code
* Review the entire Git history, specifically checking for AWS keys, CI keys, passwords, URLs...

## Managing public projects in GitHub

* Is your PR attached to an issue in GitHub?
* We sometimes use GitHub projects for backlog organisation and for delivering our sprints. Don't use JIRA as that is not accessible to the general public.
* Are tests provided in the PR? To ensure this, use a PR template and enable Circle CI for running a build with tests.
