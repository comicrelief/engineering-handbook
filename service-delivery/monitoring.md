# Monitoring & Error Reporting
***

## Providers

We use a mixture of tools to provide a clear overview of what is happening at every stage and point within our systems.

- [AWS Cloudwatch](#aws-cloudwatch)
- [AWS Cloudtrail](#aws-cloudtrail)
- [Epsagon](#epsagon)
- [Sentry](#sentry)
- [Status Page](#status-page)
- [Wormly](#wormly)

### AWS Cloudwatch
All of our Serverless applications dump their logs to Cloudwatch.

We will generally use Cloudwatch to dig deeper into errors once an error has been identified via Epsagon or Sentry.

We also have a range of cloudwatch alarms monitoring resource that cannot be tracked using other tooling, these send
alerting onwards to AWS chatbot and then onto Slack.

### AWS Cloudtrail

AWS CloudTrail provides compliance auditing by automatically recording and storing event logs for actions made within 
all of our AWS account. It records all of our user and resource activity by recording AWS Management Console actions 
and API calls.

### Epsagon
All of our Serverless applications implement Epsagon to log all invocations and the events that happened within them

Epsagon provides the following features within our services,

- **Tagging** provides us with custom tagging, searchability of sed tags and alerting when sed tags arise.
- **Timing** provides us with timing of external providers.
- **Alerts** provides us with alerts to slack on any event of our choosing.

Epsagon is generally injected into all of our projects via the Lambda wrapper, with all timing and measurement logic
being abstracted via lambda wrapper.

### Sentry
We use Sentry on both our frontend and backend applications to record exceptions and alert us to our issues.

Sentry is part of our core monitoring strategy and gives us error volumes, allowing us to immediately focus in on our
biggest issues. It also automatically generates tickets in Github related to these issues.

All issues are reported to the relevant slack channels for a project and also generally via email.

### Slack
We use slack to alert all relevant people when an incident occurs within our team.

### Status Page
We use statusif to report on all errors and to provide summaries of all issues that have happened within our systems.
It is the first port of call for issue and error updates for our stakeholders.

We will generally create an error report within our status page when an issue happens and update the issue as problems are 
resolved.

Updates to incidents are reported to slack.

The status page is available at [status.comicrelief.com](https://status.comicrelief.com/)

### Wormly
We set up Wormly alerts on all of our public APIs, this provides immediate alerting if any of our public facing 
endpoints go down or if SSL certificates are expiring.

All alerts from Wormly go to a range of slack channels alongside sending out email alerts.

## Further Reading

- [Monitoring & Debugging Serverless Applications for Red Nose Day 2019](https://medium.com/comic-relief/monitoring-debugging-serverless-applications-for-red-nose-day-2019-b2e3dd43613b)
