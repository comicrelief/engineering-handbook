# Monitoring & Error Reporting
***
##Providers
We use a mixture of tools to provide a clear overview of what is happening at every stage and point within our systems.

- [AWS Cloudwatch](#aws-cloudwatch)
- [IOPipe](#iopipe)
- [Sentry](#sentry)
- [Statuspage.io](#statuspageio)
- [Wormly](#wormly)

### AWS Cloudwatch
All of our Serverless applications dump their logs to Cloudwatch.

We will generally us cloudwatch to dig deeper into errors once an errors has been identified via IOPipe or Sentry.

### IOPipe
All of our Serverless applications implement IOPipe to log all invocations and the events that happend withing them

IOPipe provides the following features within our services,

- **Tagging** provides us with custom tagging, searchability of sed tags and alerting when sed tags arise.
- **Timing** provides us with timing of external providers.
- **Alerts** provides us with alerts to slack on any event of our chosing.

IOPipe is generally injected into all of our projects via the Lambda wrapper, with all timing and measurement logic
being abstracted via lambda wrapper.

### Sentry
We us Sentry both on our frontend applications and our backend applications to record exceptions and alert us to our issues.

Sentry is part of our core monitoring strategy and gives us error volumes, allowing us to immediately focus in on our
biggest issues. It also automatically generates tickets in Github related to these issues.

All issues are reported to the relevant slack channels for a project and also generally via email.

### Slack
We use slack to alert all relevant people when an incident occurs within our team.

### Statuspage.io
We use statuspage.io to report on all erros and to provide summaries of all issues that have happened within our systems.
It is the first point of call for issue and error updates for our steakholders.

We will generally create an error report within statupage when an issue happens and up date the issue as problems are 
resolved.

Updates to incidents are reported to slack.

### Wormly
We set up Wormly alerts on all of our public api's, this provides immediate alerting if any of our public facing 
endpoints go down or if SSL certificates are expiring.

All alerts from Wormly go to a range of slack channels alongside sending out email alerts.

## Further Reading
- [Monitoring & Debugging Serverless Applications for Red Nose Day 2019](https://medium.com/comic-relief/monitoring-debugging-serverless-applications-for-red-nose-day-2019-b2e3dd43613b)
