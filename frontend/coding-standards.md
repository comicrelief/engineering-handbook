# Coding Standards
***

The aim for our frontend coding standards is to achieve the following goals,

* simple, clean, readable
* modular / component approach - always consider reusability and portability
* one method, one thing
* accessibility
* mobile first
* progressive enhancement - consider performance on different devices
* CSS naming conventions - we use [BEM](http://getbem.com/naming/) structure

## What good code should have

* follow coding Style
    * follow guidelines provided above
    * indentation 2 spaces
* have onboarding documentation
    * brief statement in file header
    * at least one line of comment for code block description
    * remove commented code and log
* no error logging
    * no error message in console
* follow security best practices
    * avoid issues such as [cross-site scripting vulnerabilities](https://www.owasp.org/index.php/Reviewing_Code_for_Cross-site_scripting)
* implementation
    * matches story acceptance criteria
    * matches design across breakpoint
    * pass Level1 browsers & devices
    
See our [production requirements](../opsec/prodreq.md) for more in depth information on the tooling and approaches that 
should be undertaken before an application enters production. 

## Tooling

We use the following tooling to ensure coding standards across our frontend projects,

#### Code quality 
* [ESlint](http://www.eslint.org/)
* [CSSlint](http://csslint.net/)
* [SCSSlint](https://github.com/brigade/scss-lint)

#### Testing
* [Jest](https://jestjs.io/)
* [Mocha](https://mochajs.org/)
* [Cypress](https://www.cypress.io/)

#### Performance
* [Google page speed insight](https://developers.google.com/speed/pagespeed/)
* [Lighthouse](https://github.com/GoogleChrome/lighthouse)
* [Phantomas](https://github.com/macbre/phantomas)

## Resource and further reading

* [JavaScript automated testing with Jasmine, Karma and Travis](https://medium.com/@koalamango/javascript-automated-testing-with-jasmine-karma-and-travis-c118a98223d9#.fb7rrqas4)
* [Measure, Optimise & Automate Frontend Performance](https://medium.com/@koalamango/measure-optimise-automate-frontend-performance-d55552fccdfe#.suoyd4u91)
* [MDN coding style](https://developer.mozilla.org/en-US/docs/Mozilla/Developer_guide/Coding_Style)
* [Javascript standard style](https://github.com/feross/standard)
* [React/JSX standard by Airbnb](https://github.com/airbnb/javascript/tree/master/react)
