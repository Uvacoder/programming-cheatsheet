# Interview - Tests

## Concepts

### Types of tests

- Unit tests (pol. jednostkowe)
  - **Chai** (expectation/assertion library, expect/should/assert)
  - **Jest** (developed by Facebook, Use Jest to capture snapshots of React components for certain time with props and states changes. Can be used together with Enzyme. Can mock clickable events to capture state changes in a snapshot)
  - **Jasmine** (test runner, run tests and log results)
  - **Mocha** (test runner, run tests and log results)

- Integration tests (pol. integracyjne)
  - **Enzyme** (developed by Airbnb. Testing utility for React that makes it easier to assert, manipulate, and traverse your React Components’ output. It simulates ReactDOM, and React Components like JQuery finding DOM. Can be used to shallow render React components.)
  - **Karma** is a testing environment. Karma works by running your unit tests inside of browsers (defaulting to PhantomJS, a headless WebKit browser), to allow you to test browser-based JavaScript code.
  - **react-testing-library**

- E2E tests (pol. systemowe)
  - **cypress**
  - **selenium**
 
- Regression tests (pol. regresyjne)

- Acceptance tests (pol. akceptacyjne)

## Questions

- What is Unit Testing?

## Terms
- Black-box testing
Wykorzystywane pojęcie w testach e2e, spojrzenie na system z zewnętrznego punktu widzenia; system jako „czarna skrzynka”, która ma realizować określone zadania i tylko pod tym kątem jest testowana – np. testy odbioru.


- White-box testing
Testowanie obejmujące wgląd we wnętrze programu: testujący przeprowadza test jednocześnie badając kod programu. Wymagane umiejętności programistyczne – np. testy jednostkowe.
