# Test Resources

While performing tests, both manual and automated, we need resources to emulate realistic scenarios. This page aims to be a repository of references of those resources.

## Test Credit Cards

Test credit cards are to be used in user journeys that require payments / donation. Donations and Prize Platform are examples of such workflows. We can use the test credit cards to validate the workflow, assuring the user journey completes successfuly, and to test how the backend services process the payment event.

### World Pay

World Pay supplies a test credit cards page allowing us to simulate most credit card vendors:

https://developer.worldpay.com/docs/wpg/reference/testvalues#test-card-numbers

### Braintree

Braintree test credit cards page 

https://developers.braintreepayments.com/guides/credit-cards/testing-go-live/php

### Stripe

Stripe test card numbers page

https://stripe.com/docs/testing

### Paypal

For paypal sandbox account details see below:

https://github.com/comicrelief/react-donation/blob/889e2a4fc34795e3136a705f2f5d49ec42ee76e6/tests/commands/paypal.js#L5

