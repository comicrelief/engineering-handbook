# QA Process
***

## What is Manual Testing?

Manual testing means testing of an application manually by a human. A tester or QA performing manual testing for ensuring that a website or an application is working properly by various conditions which are written in test cases. 
Manual testing is the process of finding the Bug, Defect or issues in the Website. The aim of a software tester or QA is how to break the system. The tester also checks the UI design, functionality, and performance of the website by clicking on various elements.

## The Objective of Testing

- To ensure that the application meets the business and user requirements
- To identify bugs or defects in software to improve its quality

## QA Responsibilities

- Understading the software requirements. Liase with the Product Owners to have a better understanding of the business/functional requirements.
- Knowing how the end user will use the application
- Testing should meet Design standards
- Make sure that the application is defect free
- If defect found, communicate issues with developers and make sure bugs are fixed
- Perform the task again where the defect is found
- To ensure that website is stable, maintainable and supportable

## Breakpoints

There are four different breakpoints

- LG – Large Desktops
- MD – Desktops and Tablets landscape
- SM – Tablets Portrait view and Mobiles Landscape
- XS – Mobile Portrait View

Perform Positive and Negative testing on these different breakpoints

## Testing Approach

### Smoke Testing

A high level testing to check the stability of the build after new
functionality/feature is delivered to ensure the critical functionalities are
working.

### Sanity Testing

A high level testing to check the functional changes and bug fixes are working
and to ensure no further issues are introduced due to these changes.

### Validation Testing

Ensure that the system accepts expected inputs and rejects incorrect, invalid
or unexpected inputs.

### Regression Testing

Regression testing is the process of verifying that the software still performs
correctly after changes were introduced. This type of testing ensures any new
functionality added to the existing system or modifications made or the bug
fixes have not adversely affected what was previously tested. 

### Cross platforms, Browsers and Device Testing

- QA performs Level 1 testing on cross platforms, different browsers and devices (IOS and Android mobiles and tablets).
- Identify bugs on different devices and report issues on GitHub.
- Communicate issues with devs and make sure bugs are fixed, if not raise bug ticket.

**Follow the [Browser and Device Support Mandate file](https://comicrelief.app.box.com/file/292129841782).**
 
Testing on BroswerStack must be done based on the browsers, devices and OSes
listed in the [Browser and Device Support Matrix file](https://comicrelief.app.box.com/file/304111826495)

### Functional Testing

Below are the list of things that are as part of Functional testing 

- Feature functionality (acceptance tests)
- Happy path testing [go through this link](https://www.softwaretestinghelp.com/positive-testing/)
- Negative tests for journeys [go through this link](https://www.softwaretestinghelp.com/positive-testing/)
- Emails being triggered
- All copy being correct on all pages
- Correct validation messages
- Multi-browser tests (https://live.browserstack.com)_ask a Developer for Browserstack logins to test on multiple browsers and devices_
- Correct copy in emails

## Steps to create a bug/defect/issue

Example:

- Environment: Iphone 6 (12 IOS), iPad Air 2 (11 IOS), iPad Pro (11.2.2 IOS), Iphone 8 (11.2.6 IOS)
- Steps to Reproduce:

  1. Navigate to this URL - https://donation.comicrelief.com/?cartId=real_device_testing (or any other link)
  2. Enter all the input fields and click on 'Make the payment' button
  3. On success page click the 'Back' browser button
  4. Notice page is not redirected to the homepage
 
- Expected Results: Page should be redirected to the homepage when browser back button is clicked, as per the ticket requirement
- Actual Results: Page is redirected to 'Giftaid section' instead of homepage
- Attachments: add the screenshots 
- Label the GitHub issue as `bug`

## QA Bug Life Cycle

- QA raises issues after testing functionality/tickets  
- POs will go through the bugs and prioritize depending on the bug priority and assign it to the dev
- Dev fixes the bug
- Upon fixing the bug, QA re-test the fix following the different types of testing. 
- Once the issue has been fixed after testing, mark the label as `passed QA` on the bug ticket

