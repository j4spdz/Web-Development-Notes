<!-- omit in TOC -->
# Introduction to Testing

<!-- omit in TOC -->
## Contents

- [Testing types](#testing-types)
  - [Unit Tests](#unit-tests)
  - [Integration Tests](#integration-tests)
  - [Automation Tests](#automation-tests)
- [Testing tools](#testing-tools)
  - [Tools unique to React](#tools-unique-to-react)
- [Jest](#jest)
  - [Snapshot](#snapshot)
  - [Test Coverage](#test-coverage)

## Testing types

### Unit Tests

Test individual functions or classes. Easiest to implement and well suited for functional programming i.e. pure functions

### Integration Tests

How different pieces of code work with each other.

### Automation Tests

Test entireprocess of the UI. Stimulate end-user behaviour. Take longer time especially if we worry about different browsers and different devices and they also cost a lot more money to run them repeatedly.

- **TestCafe:** Not worry about cross-browser
- **Webdriver IO:** Good documentation
- **Nightmare:** automate user actions and web scraping

## Testing tools

- **Testing Library**
  - Jasmine, Jest, Mocha
- **Assertion Library:** Tool to check whether the variables contain the expected value
- **Test Runner:** Test in different environments e.g. browser, Puppeteer, jsdom
- **Mocks, Spies and Stubs:**
  - Stubbing replaces selected functions with a function to ensure that the expected behavior happens
  - Mock's is like faking a function or a behavior to test different parts of a process.
- **Code Coverage:** test coverage in javascript files to show where tests are missing

### Tools unique to React

- Snapshot testing
- [Enzyme:](https://enzymejs.github.io/enzyme/) test React components

## Jest

[Jest CheatSheet](https://github.com/sapegin/jest-cheat-sheet)

### Snapshot

```javascript
import { shallow } from "enzyme";
import React from "react";
import Card from "./Card";

it("expect to render Card component", () => {
  expect(shallow(<Card />).debug()).toMatchSnapshot();
});
```

### Test Coverage

```bash
npm test -- --coverage --watchAll=false
```
