# Identity App

## Normal deployment pipeline

todo!

## Redis dependency

The ID app uses Redis for:

1. Rate limiting information: the number of recent requests per IP address. This is essential to prevent brute force attacks.
2. Caching public keys. This is required for loading specified, old public keys, but no essential clients use this yet. It provides a small performance improvement when loading the latest key as happens more often.

### Working around Redis maintenance

Currently Pivotal's [PCF Redis](http://docs.pivotal.io/redis/1-11/index.html) has downtime during essential maintenance.

The new on-demand instance type will allow them to reduce this downtime in the medium term, but there are no immediate plans which will eliminate it.

The app is designed to be able to work without Redis as well as is feasible. If the service is not bound at all or connections fail fully, rate limits and caching will be skipped. However because during maintenance and unexpected failure modes, we have seen Redis responding but not serving real requests successfully, we need to tell the app to not use it explictly when we know that Redis is coming during a mission-critical time for the ID app.

This is the role of the task _switch-off-id-redis-production_ in the _[DANGER ZONE](https://ci.apps.comicrelief.com/teams/main/pipelines/apps-cf-pws-frost-scheduled?groups=DANGER%20ZONE)_ CI group. There is a staging equivalent for testing too. 

These use app manifests that behave just like the normal ones except they don't bind the _id-redis_ service. The resource to deploy is the same as normal - the latest passing artefact from the GitHub repository's [master branch](https://github.com/comicrelief/id/tree/master).

To deploy with a maintenance CI task like this, click on the box for the task and press the **+** button to start a build.

When a maintenance window is (comfortably) over you can manually deploy in normal mode again by going into e.g. [identity-prod-deploy](https://ci.apps.comicrelief.com/teams/main/pipelines/giving-pages/jobs/identity-prod-deploy) and clicking the **+** there.

Both deployment types should be without significant downtime as they use the normal process [with autopilot]( todo link to Concourse overview file for more info ).
