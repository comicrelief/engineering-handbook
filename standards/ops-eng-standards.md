# OpsEng standards

**Rationale**
Ops Engineering is the process of ensuring that operational considerations are taken into account throughout a product's entire lifecycle.

In particular, we want to provide guidance when a new product is being specified, investigated, designed, or initially developed - by doing so, it means that we can be sure that it can be brought into production without any problems.

The following standards are a minimum set of criteria which applications need to meet in order to be operated by WebOps at short notice. If any derogations are required, then they MUST be discussed with WebOps during a product's initial design - this means that we will have the opportunity to suggest alternatives, or to plan any changes that will be needed to our infrastructure or processes.

## The Standards

### Components

* MUST run on either an Apache 2.4 or Nginx webserver
* MUST provide a status page, which provides a '200' HTTP status code when the application is available
* SHOULD be compatible with PHP 5.6
* SHOULD run within php5-fpm
* SHOULD have a Varnish front-end
* SHOULD use the CloudFront CDN to host all static assets
* MAY use a Memcached k/v store
* MAY use a Mysql 5.6 database
* MAY use a RabbitMQ message queue

### Configuration

* MUST be configurable dynamically, or provide a signal or hook through which we can reload configuration
* MUST allow WebOps to configure service endpoints and associated credentials (eg. for database, varnish admin, memcached, and third-party services)
* MUST NOT contain static configuration that can not be overridden
* SHOULD read configuration either from a YAML file in a known location, or from environment variables

### Delivery

* MUST be delivered in the form of an immutable deployment artefact (such as a .tar.gz). This artefact:
* MUST be built hermetically (ie. with freshly-installed build dependencies, preferably in a chroot or other clean environment)
* MUST be deployed in an identical manner on both staging and production
* MUST NOT need to be changed in order to be deployed into both staging and production
* MUST NOT be self-modifying
* SHOULD NOT require any changes to the deployed code to be made after deployment
* MUST be deployable to one server at a time without affecting service (ie. incompatible features should not be switched on until either a configuration value is changed or a db update is performed at the end of the deployment process
* MUST be fully idempotent - ie. the deployment process must always be safely repeatable no matter what state the service is currently in.
* SHOULD have a documented build process (specified by the developers, but built, maintained, and run by WebOps)
* SHOULD have a documented lifecycle (ie. how long will the application be live for? under what circumstances can it be taken offline in an emergency? who will need to be informed before planned maintenance or after downtime?)
