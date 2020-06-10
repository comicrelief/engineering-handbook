# Lambda Wrapper
***

When writing Serverless endpoints, we have found ourselves replicating a lot of boiler plate code to do basic actions, 
such as reading request variables or writing to SQS. The aim of this package is to provide a wrapper for our lambda 
functions, to provide some level of dependency and configuration injection and to reduce time spent on project setup.

The lambda wrapper centralises and enforces much of our security configuration into a centralised location, meaning that
if we do need to make changes, we can change and fix much of the logic for all of our services from one location.

The lambda wrapper is open source and is publicly available, it is versioned via NPM and is imported via yarn in all of 
our projects.

See [Github](https://github.com/comicrelief/lambda-wrapper) for more information
