# Application Hosting
***

We currently use a couple of hosting providers, with our main provider being AWS. All other providers are now mostly legacy and are slowly being phased out.

## Providers
- [AWS](#aws)
- [Azure](#azure)
- [Heroku](#heroku)
- [Netlify](#netlify)
- [Pivotal Web Services (PWS)](#pivotal-web-services-pws)

### AWS
AWS is the main host for all of our applications.

#### Accounts & Access
The main route to access AWS is via SSO, which will give you access to whichever account you require to access.

We generally try to limit access to AWS accounts, as a developer most actions should be able to be performed in-code via
a CI/CD orchestration service, as developers do have their pull request environments which are exact replicas of what is 
in production.

We do have a developer sandbox account, that allows developers to test out certain things that can only be tested from 
the console rather than from Cloudformation. 

#### Services

The core services that we are using in AWS are,

- **API Gateway** - All of our services that run on Lambda have an API gateway instance in front of them.

- **Cloudfront** - All of our public-facing frontends that are hosted on S3 have Cloudfront in front of them as the 
primary CDN.

- **EC2** - We are slowly phasing out all legacy services that used to be on EC2. Our aim is to simplify our hosting 
solutions and host as little as possible that is high effort to maintain.

- **Lambda** - All of our Serverless applications run on top of Lambda; we also use it for some scheduled cron tasks.

- **Lightsail** - We use lightsail for a lot of our reporting services hosting, mostly due to its low cost and lack of 
complexity.

- **RDS** - All of our web application databases are hosted on RDS.

- **Route53** - All of our domain name records are managed within Route53.

- **S3** - Our two main use cases for S3 are to store transitional data (deltas) and to host our frontend React 
applications.

- **SQS** - Provides all message queues for applications.

- **WAF** - All of our backend services have AWS WAD in front of them to provide a layer of protection from DDoS attacks
and other forms of code injection.

We also use many other AWS services, so this is not a comprehensive list by any means.

### Azure
Azure hosts our data warehouse (SSV) and its backing data ingestion pipeline.

### Heroku
We use Heroku for Contentful preview environments for the Donation platform CMS elements.

Deploys are triggered by webhooks from Contentful and via git commits to the master branch of the donation
frontend.

### Netlify
We use Netlify to deploy pull request previews for all of our React frontend applications.

### Pivotal Web Services (PWS)
Pivotal Web Services is the hosting platform for our legacy PHP applications. Currently the only applications that
are still running on it are the legacy payment service layer and payin. Our aim is to retire these by the end of 2019, 
with the view of those being the last applications that will sit on PWS.

Deployments to PWS follow the same path as all other pull request environments and are triggered by pushes to 
github.


