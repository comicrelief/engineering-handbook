# Load testing
***

We do continuous load testing to ensure that our platforms can handle the
required load, with tolerance for any surprises that could occur during
high-traffic events.

- [Approach](#approach)
- [Tooling](#tooling)
- [Methodology](#methodology)
- [Further Reading](#further-reading)

## Approach

We will generally run the following three types of tests against our
applications.

- **Drip tests** are usually throughout the period of a couple of days. These
  simulate a normal background load level so that we can observe the behaviour
  of the site under normal operation, and correlate any periods during which
  increased latencies or error rates are seen with activities known to be
  occurring during those periods (e.g. deployments, cache clears and the other
  elements of our load testing program).

- **Slam tests** simulate a sudden spike of traffic, which enables us to
  understand the behaviour of the service when faced with a traffic profile
  that has traditionally been difficult for automated scaling systems to handle
  appropriately. Our goal here is to determine the level and type of errors to
  expect during sudden traffic spikes. Due to the nature of Comic Relief,
  extremely sharp spikes of traffic can occur in response to news stories,
  appeal films shown on national television and other similar events.

- **Ramp tests** produce a gradually increasing level of traffic similar to
  that seen over the course of each day during the campaign period.

## Tooling

We use [Serverless Artillery](https://github.com/Nordstrom/serverless-artillery)
to load test all our applications, which uses AWS Lambda to generate traffic
to our backend APIs according to scripted scenarios.

We use [InfluxDB](https://www.influxdata.com/) and
[Grafana](https://grafana.com/) to report on these load tests.

## Methodology

Load testing is performed using our
[load testing repo](https://github.com/comicrelief/loadtest-artillery), which
contains traffic scenarios (typically at least one for each type of test listed
above) for all our services, and instructions for how to run them.

We will always create load testing plans that recreate actual traffic patterns. We will generally load test very far
over our expected load levels to ensure that we do no have any surprises down the line.

Before running the load test, we ensure that any changes made to the repo are
committed. This allows us to keep a record of every test configuration and
reproduce the test in the future.

We collect all responses from Serverless Artillery and then report and analyse
these results using Grafana.

We will then create a new release in the GitHub repo to document the test. The
release notes should state which test was run, and include a screenshot of the
traffic graph from Grafana and any relevant notes.

## Further Reading

- [Artillery docs](https://artillery.io/docs/)
- [Load testing serverless with serverless at Comic Relief](https://medium.com/comic-relief/load-testing-serverless-with-serverless-at-comic-relief-cb6b9fa026ee)
- [Serverless Artillery workshop](https://github.com/Nordstrom/serverless-artillery-workshop)
