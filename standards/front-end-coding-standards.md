# Front end coding standards

This document is for Frontend coding standards, including recommended style, review guidelines and testing tools.

## Coding Style

General Principles
* Simple, clean, readable
* Modular / component approach - always consider reusability and portability
* One method, one thing
* Accessible (WCAG2.0 AA)
* Mobile first
* Progressive enhancement - consider performance on different devices
* CSS naming conventions - we use BEM structure

Style Guidelines
* MDN coding style: https://developer.mozilla.org/en-US/docs/Mozilla/Developer_guide/Coding_Style
* Javascript standard style: https://github.com/feross/standard
* React/JSX standard by Airbnb: https://github.com/airbnb/javascript/tree/master/react
 
### Code Review

Code review is about the code **NOT** the coder.

#### Essential checklist

Code
* Coding Style
  * Follow the guideline provide above
  * Indentation 2 spaces
* Comments
  * Brief statement in file header
  * At least one line of comment for code block description
  * Remove commented code and log
* Logging
  * No error message in console
* Security
  * Avoid cross-site scripting vulnerabilities: https://www.owasp.org/index.php/Reviewing_Code_for_Cross-site_scripting
* Implementation
  * Matches story acceptance criteria
  * Matches design across breakpoint

Look & Feel
* Copy and link
* Space and margin
* Colours
* Element behaviour across breakpoints
* Pass Level1 browsers & devices
 
#### Tools

Code quality 
* JSlint: http://www.jslint.com/
* CSSlint: http://csslint.net/
* SCSSlint: https://github.com/brigade/scss-lint

Testing
* Jasmine: http://jasmine.github.io/
* Karma: https://karma-runner.github.io/0.13/index.html

Performance
* Google page speed insight: https://developers.google.com/speed/pagespeed/
* Webpagetest: http://www.webpagetest.org/
* YSlow: http://yslow.org/
* Phantomas: https://github.com/macbre/phantomas
 
## Resources and further reading

* JavaScript automated testing with Jasmine, Karma and Travis: https://medium.com/@koalamango/javascript-automated-testing-with-jasmine-karma-and-travis-c118a98223d9#.fb7rrqas4
* Measure, Optimise & Automate Frontend Performance: https://medium.com/@koalamango/measure-optimise-automate-frontend-performance-d55552fccdfe#.suoyd4u91
