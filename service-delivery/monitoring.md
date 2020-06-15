# Monitoring & Error Reporting
***

We use a mixture of tools to provide a clear overview of what is happening at every stage and point within our systems.

- [Slack](#slack)
- [AWS CloudWatch](#aws-cloudwatch)
- [AWS CloudTrail](#aws-cloudtrail)
- [Epsagon](#epsagon)
- [Sentry](#sentry)
- [Status Page](#status-page)
- [Wormly](#wormly)

## Slack

We use [Slack](https://slack.com/) as our instant messaging platform. Many of
our monitoring tools post messages to Slack to quickly alert all relevant
people when an incident occurs within our team.

See also our [list of Slack channels](../team-structure/slack-channels.md).

## AWS CloudWatch

All of our Serverless applications dump their logs to
[Amazon CloudWatch](https://aws.amazon.com/cloudwatch/).

We will generally use CloudWatch to dig deeper into errors once an error has
been identified via Epsagon or Sentry.

We also have a range of CloudWatch alarms monitoring resources that cannot be
tracked using other tooling. These send alerts on to AWS Chatbot and then onto
Slack.

## AWS CloudTrail

[AWS CloudTrail](https://aws.amazon.com/cloudtrail/) provides compliance
auditing by automatically recording and storing event logs for all actions made
within our AWS accounts. This includes all AWS Management Console actions and
API calls.

## Epsagon

All of our Serverless applications implement [Epsagon](https://epsagon.com/) to
log all function invocations and the events that happened within them.

Epsagon provides the following features within our services:

- **Tagging** provides us with custom tagging, searchability of tags and
  alerting when certain tags arise.
- **Timing** provides us with timing of external providers.
- **Alerts** provides us with alerts to Slack on any event of our choosing.

Epsagon is injected into all of our projects via the
[Lambda Wrapper](../backend/lambda-wrapper.md), with all timing and measurement
logic abstracted in Lambda Wrapper's Logger dependency.

## Sentry

We use [Sentry](https://sentry.io/) on both our frontend and backend
applications to record exceptions and alert us to issues.

Sentry is part of our core monitoring strategy and gives us error volumes, allowing us to immediately focus in on our
biggest issues. It also automatically generates tickets in GitHub related to these issues.

All issues are reported to the relevant Slack channels for a project and also generally via email.

## Status Page

We use [Statusfy](https://statusfy.co/) to report on all errors and to provide
summaries of all issues that have happened within our systems.
It is the first port of call for issue and error updates for our stakeholders.

We will generally create an error report within our status page when an issue happens and update the issue as problems are
resolved.

Updates to incidents are automatically reported to Slack.

The status page is available at [status.comicrelief.com](https://status.comicrelief.com/).

## Wormly

We set up [Wormly](https://www.wormly.com/) alerts on all of our public APIs.
This provides immediate alerting if any of our public-facing endpoints go down,
or if SSL certificates are expiring.

All alerts from Wormly go to Slack as well as sending out email alerts.

## Further Reading

- [Monitoring & Debugging Serverless Applications for Red Nose Day 2019](https://medium.com/comic-relief/monitoring-debugging-serverless-applications-for-red-nose-day-2019-b2e3dd43613b)
