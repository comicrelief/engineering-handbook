# Engineering at Comic Relief
[![Netlify Status](https://api.netlify.com/api/v1/badges/76bcd6b0-ac7a-49f1-9f87-8635f6c4ffe5/deploy-status)](https://app.netlify.com/sites/comicrelief-engineering-handbook/deploys)

The aim of this engineering handbook is to provide engineers with guidelines and directions for their day to day engineering tasks. We are writing this handbook collaboratively and in the open, much like we open source many of our applications \(check out [our Github](https://github.com/comicrelief)!\)

## Engineering Principles

We like to apply the following engineering principles in the way we develop our services and digital products.

* Reusable services as engineering products
* API-first
* Cloud-native
* Real-time data and monitoring
* [Accessibility](frontend/accessibility.md) at the heart of everything
* Going beyond the screen

We approach those principles in the following manner:

* Development of services over maintaining infrastructure and manual scaling. Functions over microservices, microservices over monoliths, managed services over self-managed services. [12-factor apps](https://12factor.net/) where applicable
* Use of and contribute to open source software. [Coding in the open as our default setting](code-delivery/code-in-open.md).
* Continuous delivery backed up by automated testing. Deploy to production systems multiple times a day.
* Real-time monitoring of live products through dashboards (e.g. Grafana), logs (e.g. Loggly, CloudWatch) and alerts (e.g. Wormly)
* Everything in code and everything code reviewed. In-code and live documentation over wiki documentation.

## How to contribue

You can edit this handbook locally using `gitbook`.

	yarn install

And then you can serve this locally using

	yarn start

And check out the handbook at 

	http://localhost:4000


