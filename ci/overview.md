# Continuous Delivery

An overview of our continuous delivery strategies and tools:

* Travis CI
* Concourse CI

Testing strategies and tools

## Concourse CI

TODO - Explain autopilot plugin for blue/green deployments

## Logging

As we use small, distributed apps, centralised logging is critical for visibility on deployed apps.

We currently use [Loggly](https://crfrost.loggly.com/search).

For Cloud Foundry apps running on PWS, binding the `logging` service automatically drains container level logs. You can pass it to Loggly [as done here]().

example TODO!
