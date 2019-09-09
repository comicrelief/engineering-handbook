# Coding Standards
***
This page outlines the tooling and standards that we align ourselves to when writing backend applications. Our aim is to 
Produce clean & maintainable code, If our code lacks consistency, is poorly laid out and undocumented, we are 
adding to the overall complexity of our system.

## NodeJS Projects

In all cases, we use [ESLint](https://eslint.org/) to ensure that coding standards are adhered to.

We use the following ESLint plugins together to ensure conformity across our projects,

- [AirBNB Coding standards](https://www.npmjs.com/package/eslint-config-airbnb)
- [SonarJS rules](https://www.npmjs.com/package/eslint-plugin-sonarjs) to detect bugs and suspicious patterns in your code.
- [Unicorn Rules](https://www.npmjs.com/package/eslint-plugin-unicorn)

Rule exceptions should not be made in projects unless absolutely necessary, with an active effort to remove exceptions to 
rules wherever possible.

## PHP Projects

For our PHP projects we use [PHPCS](https://github.com/squizlabs/PHP_CodeSniffer) using the PSR2 coding standards.

We also use [PHPCD](https://github.com/sebastianbergmann/phpcpd) to ensure that code is not duplicated witin the project.


## Further Reading
- [Secure development and deployment guidance](https://www.ncsc.gov.uk/collection/developers-collection?curPage=/collection/developers-collection/principles/produce-clean-maintainable-code)
- [How ESLint Makes Me a Better React Developer](https://itnext.io/how-eslint-makes-me-a-better-react-developer-237fb14c00ae)
