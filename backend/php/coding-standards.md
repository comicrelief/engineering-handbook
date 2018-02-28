# Coding Standards

## Packages

* [Composer](https://getcomposer.org/) for everything.
* Check packages' history and adherence to [Semantic Versioning](https://semver.org/) carefully when choosing constraints for `composer.json`. Aim to make sure a `composer update` is always safe.
* Never `composer update` in production deploys. Update lock files regularly in version control - automatically if you can - but always deploy a well-defined, locked set of dependencies.

## PHP version & extensions

* In `composer.json`, define a PHP range. Aim for the highest feature version you know you can deploy with so that new language features are available and deployment to new platforms is safe.
* In `composer.json`, define *all* required extensions with `"ext-[name]": "*"`. This helps devs and is used automatically by PaaSs like Cloud Foundry.

## Autoloading

* First preference: [PSR-4](https://www.php-fig.org/psr/psr-4/)
* If not possible: [PSR-0](https://www.php-fig.org/psr/psr-0/)
* Last resort: custom autoloader [registered with Composer](https://getcomposer.org/doc/01-basic-usage.md#autoloading)

## Code style

* Always [PSR-2](https://www.php-fig.org/psr/psr-2/).
* "Mostly" follow [Symfony standards](https://symfony.com/doc/current/contributing/code/standards.html) - consider readability when deciding on things like [Yoda conditions](https://en.wikipedia.org/wiki/Yoda_conditions).
* Prefer `[short, array]` syntax for new code.
