# Application Hosting
***

We currently use a couple of hosting providers, with our main provider being AWS. All other providers are now mostly legacy and are slowly being phased out.

## Providers

- [AWS](#aws)
- [Azure](#azure)
- [Heroku](#heroku)
- [Netlify](#netlify)
- [Pivotal Web Services (PWS)](#pivotal-web-services-pws)

## AWS

[AWS](https://aws.amazon.com/) is the main host for all of our applications.

### Accounts & Access

The main route to access AWS is via SSO, which will give you access to whichever account you require to access.

We generally try to limit access to AWS accounts. As a developer, you should be
able to perform most actions in-code via CI/CD and CloudFormation. Most repos
have pull request environments that are exact replicas of what is in production.

We do have a developer sandbox account to allows developers to try out certain
things that can only be tested from within the AWS Management Console.

### Services

The core services that we are using in AWS are listed here.

- **[API Gateway](https://aws.amazon.com/api-gateway/)** - All of our services
  that run on Lambda have an API Gateway instance in front of them.

- **[CloudFront](https://aws.amazon.com/cloudfront/)** - All of our
  public-facing frontends that are hosted on S3 use CloudFront as the primary
  CDN.

- **[EC2](https://aws.amazon.com/ec2/)** - We are slowly phasing out all legacy
  services that run on EC2. Our aim is to simplify our hosting solutions and
  minimise use of services that have high maintenance effort.

- **[Lambda](https://aws.amazon.com/lambda/)** - All of our Serverless
  applications run in Lambda. We also use it for some scheduled cron tasks.

- **[Lightsail](https://aws.amazon.com/lightsail/)** - We use Lightsail for a
  lot of our reporting services hosting, mostly due to its low cost and lack of
  complexity.

- **[RDS](https://aws.amazon.com/rds/)** - All of our web application databases
  are hosted on RDS.

- **[Route 53](https://aws.amazon.com/route53/)** - All of our domain name
  records are managed within Route 53.

- **[S3](https://aws.amazon.com/s3/)** - Our two main use cases for S3 are to
  store transitional data (deltas) and to host our frontend React applications.

- **[SQS](https://aws.amazon.com/sqs/)** - Provides all message queues for
  applications.

- **[WAF](https://aws.amazon.com/waf/)** - All of our backend services have AWS
  WAF in front of them to provide a layer of protection from DDoS attacks and
  other attacks and exploits.

We also use many other AWS services, so this is not a comprehensive list by any means.

## Azure

[Microsoft Azure](https://azure.microsoft.com/) hosts our data warehouse (SSV)
and its backing data ingestion pipeline.

## Heroku

We use [Heroku](https://www.heroku.com/) for
[Contentful](https://www.contentful.com/) preview environments for the Donation
platform CMS elements.

Deploys are triggered by webhooks from Contentful and via git commits to the master branch of the donation
frontend.

## Netlify

We use [Netlify](https://www.netlify.com/) to deploy pull request previews for
all of our React frontend applications.

## Pivotal Web Services (PWS)

[Pivotal Web Services](https://run.pivotal.io/) is the hosting platform for our
legacy PHP applications. Currently the only applications that
are still running on it are the legacy payment service layer and payin. Our aim is to retire these by the end of 2019, 
with the view of those being the last applications that will sit on PWS.

Deployments to PWS follow the same path as all other pull request environments and are triggered by pushes to 
GitHub.


