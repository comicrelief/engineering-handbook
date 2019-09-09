# Code Delivery
***
For a lot of our products there is only one chance to get it right and very few production opportunities to learn non 
costly lessons. In this section we outline the basc requirements that all delivery of code and therefore the code itself 
should have.

We separate testing and deployment of our code into two distinct stages, these are,
- The [Pull Request (PR) stage](pull-requests.md), which is before the code has been reviewed and merged into the 
 projects master branch.
- The [Pipeline Stage](pipelines.md), which is once the pull request has been merged into the projects master branch and 
begins and then ends it journey into production.

## Sections
* [Coding in the Open](code-in-open.md)
* [Coding Standards](coding-standards.md)
* [Hosting](hosting.md)
* [Load Testing](load-testing.md)
* [Monitoring & Error Reporting](monitoring.md)
* [Pipelines](pipelines.md)
* [Pull Requests](pull-requests.md)
* [Tooling](tooling.md)

## Rules to die by
- No-one should ever be manually pushing code into staging or production environments.
- Secrets should never be stored inside a code repository, they should be handled by the CI system.
- All infrastructure should be managed within code.
- A plan of failure scenarios and their remedies should exist for every application and Service.
- Any new feature that could have an effect on how we handle load, should be load tested.
- At the very least, end to end test should exist for every feature.

## Relevant Articles
- [Pipelines Everywhere](https://medium.com/comic-relief/pipelines-everywhere-9eb284f5bee3)

- [Our approach on automated regression testing](https://medium.com/comic-relief/our-approach-on-automated-regression-testing-454731bac9b)

- [How Comic Relief’s used Snyk to automate security and boost productivity ](https://snyk.io/blog/case-study-comic-relief/)
