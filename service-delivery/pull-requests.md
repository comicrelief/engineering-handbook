# Pull Requests
***

A pull request is the main and only way that code should reach a production environment.

- [Developer Process](#developer-process)
- [Automated Tests](#automated-tests--tasks)

## Developer Process
A developer contributing code will take the following steps before it is merged into the master branch,

1. The developer will create a branch from the master branch on their local machine

2. They will then create commits with code changes, constantly pushing changes to their branch changes to github.

3. While they are still developing or after they have completed developing their changes, they will open a pull request.

4. Once the pull request has been opened, the developer will wait for all tests to pass and fix any bugs.

5. The developer will assign reviewers who will review the code and ensure that it is as good as it should be and 
fulfils its purpose.

6. Once reviewer approval has been marked on the pull request, the developer can then merge the pull request, which will
then be passed onto the [CI/CD pipeline](pipelines.md).

It should be noted that if the project is a shared node library, this will also trigger a release to npm. If it is a
docker image it will trigger a release to docker hub.

## Automated Tests & Tasks
We run automated tests against all PRs to ensure that they will not cause issues when merged into production. These 
generally consist of a mixture of the following types of tests,

- Unit Tests
- Code Style tests
- Performance testing
- Deployment and testing on PR environment
- Lighthouse testing
- Third party dependency testing
- Preview environment deployment

Please see the [tooling section](tooling.md) for more information on the tools that we use to test our code.
