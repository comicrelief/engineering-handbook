# Load testing
***

We do continuous load testing to ensure that our platforms can handle the required load in order to handle any surprises
that could occur from high traffic events.

- [Approach](#approach)
- [Tooling](#tooling)
- [Methodology](#methodology)
- [Further Reading](#further-reading)

## Approach
***

We will generally run the three following types of tests against our applications to ensure they hold up to the levels 
of load that we would expect during campaign.

- **Drip tests** are usually throughout the period of a couple of days. These ensure that we simulate a normal 
background load level, observe the behaviour of the site under normal operation and correlate any periods during which 
increased latencies or error rates are seen with activities known to be occurring during those periods (e.g. deployments, 
cache clears and the other elements of our load testing program).

- **Slam tests** to simulate a sudden spike of traffic, this enables us to understand the behaviour of the site when 
faced with a traffic profile that has traditionally been difficult for automated scaling systems to handle appropriately. 
Our goal here is to determine the level and type of errors to expect during sudden traffic spikes. Due to the nature of 
Comic Relief, extremely sharp spikes of traffic can occur in response to news stories, appeal films shown on national 
television and other similar events.

- **Ramp tests** produce a gradually increasing level of traffic similar to that seen over the course of each day during 
the campaign period.

## Tooling
***

We use Serverless Artillery to load test all of our applications, which uses Lambda to generate traffic against our 
backend APIs.

We also use InfluxDB and Grafana to report on these load tests.

## Methodology
***

We will always create load testing plans that recreate actual traffic patterns. We will generally load test very far
over our expected load levels to ensure that we do no have any surprises down the line.

We feed all responses from Serverless Artillery and then report / analyse these results using Grafana.

We will then create a report as a release in the load testing repository to document the load test so that we can go
back to it in the future.

## Further Reading
***

- [Load testing serverless with serverless at Comic Relief](https://medium.com/comic-relief/load-testing-serverless-with-serverless-at-comic-relief-cb6b9fa026ee)
- [Serverless Artillery workshop](https://github.com/Nordstrom/serverless-artillery-workshop)
