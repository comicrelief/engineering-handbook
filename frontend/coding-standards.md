# Coding Standards

---
## Coding Style

### General Principle
* simple, clean, readable
* modular / component approach - always consider reusability and portability
* one method, one thing
* accessibility
* mobile first
* progressive enhancement - consider performance on different devices
* CSS naming conventions - we use [BEM](http://getbem.com/naming/) structure


### Style Guideline 

* [MDN coding style](https://developer.mozilla.org/en-US/docs/Mozilla/Developer_guide/Coding_Style)
* [Javascript standard style](https://github.com/feross/standard)
* [React/JSX standard by Airbnb](https://github.com/airbnb/javascript/tree/master/react)


---
## Coding Review

>First of all, code review is about the code *NOT* the coder.

### General Principle

#### Code

* coding Style
    * follow guideline provide above
    * indentation 2 spaces
* onboarding documentation
    * brief statement in file header
    * at least one line of comment for code block description
    * remove commented code and log
* logging
    * no error message in console
* security
    * avoid [cross-site scripting vulnerabilities](https://www.owasp.org/index.php/Reviewing_Code_for_Cross-site_scripting)
* implementation
    * matches story acceptance criteria
    * matches design across breakpoint

#### Look & Feel
* copy and link
* space and margin
* colours
* element behaviour across breakpoints
* pass Level1 browsers & devices


---
## Tools

#### Code quality 
* [JSlint](http://www.jslint.com/)
* [CSSlint](http://csslint.net/)
* [SCSSlint](https://github.com/brigade/scss-lint)

#### Testing
* [Jasmine](http://jasmine.github.io/)
* [Karma](https://karma-runner.github.io/0.13/index.html)

#### Performance
* [Google page speed insight](https://developers.google.com/speed/pagespeed/)
* [Webpagetest](http://www.webpagetest.org/)
* [YSlow](http://yslow.org/)
* [Phantomas](https://github.com/macbre/phantomas)


---
#### Resource and further reading:

* [JavaScript automated testing with Jasmine, Karma and Travis](https://medium.com/@koalamango/javascript-automated-testing-with-jasmine-karma-and-travis-c118a98223d9#.fb7rrqas4)
* [Measure, Optimise & Automate Frontend Performance](https://medium.com/@koalamango/measure-optimise-automate-frontend-performance-d55552fccdfe#.suoyd4u91)
