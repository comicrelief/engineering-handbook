# Lambda Wrapper
***

Our [Lambda Wrapper](https://github.com/comicrelief/lambda-wrapper) is a
publicly available NPM package that provides basic functionality common to all
our Serverless projects.

When writing Serverless endpoints, we found ourselves replicating a lot of
boilerplate code for basic actions, such as reading request parameters or
submitting data to Amazon SQS. The aim of this package is to reduce time spent
on project setup by providing a wrapper for our AWS Lambda functions, that
provides dependency and configuration injection, logging and metrics, and some
commonly used tools for working with request data and other AWS services.

The Lambda Wrapper centralises and enforces much of our security configuration
into a single location, meaning that if we do need to make changes, we can do
so in one location.

The package is open source
[on GitHub](https://github.com/comicrelief/lambda-wrapper)
and publicly available
[via NPM](https://www.npmjs.com/package/@comicrelief/lambda-wrapper).
