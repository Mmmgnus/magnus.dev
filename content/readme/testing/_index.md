---
title: "Testing"
date: 2019-06-17T23:20:06+02:00
draft: true
intro: "Testing of everything"
---

### What should we test?
### Requirements

* Try to use a global config file.
* Git-hocks, tests need to run before git commits can be done.

#### What we should have in mind:
* Skalbart
* Köra lokalt
* MSBuild compatible
* Continoues integration.
* SonarCube compatible
* Funka med olika ramverk och bibliotek. jQuery, Angular, React etc.
* Front end (JS, CSS etc.) och Back-end(C#) i samma testkörning.
* Browserstack

### How should we test that?



## Framworks
 * https://jasmine.github.io/
 * https://karma-runner.github.io/1.0/index.html
 * https://mochajs.org/
 * https://facebook.github.io/jest/
 * https://github.com/avajs/ava
 * http://qunitjs.com/
 * https://theintern.github.io
 
 ## Code quality:
 * https://www.sonarqube.org/

## Angular
 * http://www.protractortest.org/ (End-to-end testing ie. Intergration tests)

## Vue
* https://vue-test-utils.vuejs.org/en/ (Official unit testing utility library for Vue.js)

## Asserton library
 * Chai
 
## Unit test

## Usabillity testing
 * https://youtu.be/56zCnwj58e4 This video explaning a litle bit. One interesting ide is to use lighthouse CLI with grunt in some way to spot for example colors with bad contrast. This should not run all the time probably for performance.

## The thing between Unit and Integration test
There is some parts that is not unit test and integration test but something in between. Scripts doing DOM manipulations for example. **How do we test that?**

## Visual tester
 * BackstopJS
 * Webdriver.io

## Testing in TFS

## Writing testable Javascript

## Notes
 * Test behaviours not a method.
 * Seperate Unit (lightweight) tests and integration test. Don't put them in the same folder and make it possible to test them separately. 
 * Unit test is small test that test one thing, unit test != one function. 
 * Intergration tests testing pieces of things.

## Resources
### Mocha
 * https://www.npmjs.com/package/grunt-mocha-cli
 
### Books
 * http://www.bokus.com/bok/9780321146533/test-driven-development-by-example/
 * http://www.bokus.com/bok/9780321213358/refactoring-to-patterns/

### Links
* https://alexjoverm.github.io/2017/08/21/Write-the-first-Vue-js-Component-Unit-Test-in-Jest/
* https://blog.andrewray.me/webpack-when-to-use-and-why/
* http://randycoulman.com/blog/2016/03/22/testing-with-mocha-and-webpack/
* https://github.com/mojoaxel/awesome-regression-testing
* https://gist.github.com/cvrebert/adf91e429906a4d746cd
* https://www.browserstack.com/javascript-testing-api
* https://github.com/mawrkus/js-unit-testing-guide
* https://stackoverflow.com/questions/300855/javascript-unit-test-tools-for-tdd
* https://www.sitepen.com/blog/2017/06/22/intern-and-javascript-testing-in-2017/
* https://blog.kentcdodds.com/write-tests-not-too-many-mostly-integration-5e8c7fff591c

#### Webdriver.io regression testing
* https://medium.com/wehkamp-techblog/visual-regression-testing-with-webdriverio-browserstack-7cbd8eb682c

#### Intern
* http://developers.mobilesystem7.com/blog/post/automating-ui-tests/

### Videos
* https://www.youtube.com/watch?v=7RxjhaPlRw4
* https://vimeo.com/68375232
* https://www.youtube.com/watch?v=HNjlJpuA5kQ
* https://vimeo.com/182479015
