# Coding in the open

We code in the open for many of the projects at Comic Relief. Some of these are contributed as open-source projects, whilst others might not be relevant outside Comic Relief. However, coding in the open keeps us adhering to high development standards and transparency with the tools we use.

### Checklist before going open

* Secrets should never be added to a public repository, only references to secrets via environment variables can be part of the code
* Review the entire github history, specifically checking for AWS keys, travis keys, passwords, urls... 

### Managing public projects in GitHub: a checklist

* Is your PR attached to an issue in GitHub?
* We sometimes use Github projects for backlog organisation and for delivering our sprints. Don't use JIRA as that is not accessible to the general public.

* Are tests provided in the PR? To ensure this, use a PR template and enable Travis for running a build with tests. 
