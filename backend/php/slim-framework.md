# Slim Framework

Slim is small; it doesn't add too much to think about beyond the [general coding standards](coding-standards.md) but there are a couple of things to consider.

## Project structure

In newer Slim apps we've found the most maintainable pattern to include:

* a concise routes file ([ID example](https://github.com/comicrelief/id/blob/master/config/routes.php));
* `Action`s that you `__invoke()` independently ([ID example](https://github.com/comicrelief/id/blob/master/src/Action/PublicKeyCurrent.php)) - but [see below](#action-invocation-&-psr-15);
* dependency injection that makes services available with little or no configuration outside a global settings file ([ID example](https://github.com/comicrelief/id/blob/master/config/di/queue.php));
* [PSR-7](https://www.php-fig.org/psr/psr-7/) middleware that is reusable and can be applied to whole routing groups easily, namespaced by description of its behaviour rather than e.g. interface ([ID example](https://github.com/comicrelief/id/blob/master/src/RateLimit/RateLimiter.php));
* no controllers.

## Action invocation & PSR-15

It seems likely that as of the standardisation of [PSR-15](https://www.php-fig.org/psr/psr-15/), the above `Action` invocation pattern will become less common. We should keep tabs on what frameworks like Slim and Symfony do and try to follow latest common practice here if it carries no obvious downsides, while keeping actions and middlewares loosely coupled from each other.
