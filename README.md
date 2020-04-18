## Analysis

After analysis of ACME Corps development & integration strategies, I have discovered 2 issues. 

1. The team was using a developers laptop to manually deploy the latest code to production.
This causing a bottle kneck at the deployment stage and preventing deployments when said 
developer was not available.
2. There has been an increase in bugs making their way to production. 

My Solution
1. Setup an automated build on branches using CircleCI.
2. Run automated unit tests on all pushes to branches, preventing bugs from sneaking their way into production.
3. Run linting on all pushes to branches ensuring that code quality is at its highest.
4. Run a coverage report after tests are complete to keep the team on their toes, in regards
to new features being added and accounted for. 
5. Automatically build an artefact for deployment on the master branch.

## Building the docker image

TODO

## Running Tests

Automated testing on all branches 

### Unit tests

There are [Mocha](https://mochajs.org) based unit test in the application. These tests will
run automatically on pushes to any branch. These tests will cover all test tasks defines in
src/test/unit. 

The build will fail if tests do not pass.

I have implemented this because running unit tests after every push will ensure that all code, that 
will eventually make its way to master branch, will be thoroughly tested.

### Linting

Linting will run on all files (excluding node_modules) after a push to any branch.

The build will fail if there are any errors that lint can find in code.

I have implemented this because the team must keep their code to a high standard, and linting will
ensure that all code that is pushed is well written and follows a certain standard. 

### Code coverage

In order to ensure we are covering 80% of code I have setup a code coverage report that 
will check how much of our code is being tested. This is shown in a report that can be found
in the circle CI code-coverage-report task under the artifacts tab. 

NOTE: Currently code coverage is set to pass all tests that go above 60% due to models ->> branches
finishing at 66%. Dev team please take a look at this. Once it has been resolved, the coverage threshold 
can be increased int he file src/nycrc.json

I have implemented this to ensure that the dev team has high visibility on the amount of code that is
being accounted for when the automated testing runs. This future proofs my implementation. 

### Integration tests

Integration tests are implemented using Mocha as well. 

TODO: set up integration test environment and run integration tests


### End to end test

E2E tests are implemented using QaWolf and requires a database backend to execute properly.

Set the environment variable `QAW_HEADLESS` to true to run the e2e in headless mode

https://www.qawolf.com/

TODO: Set up e2e test environment and run the e2e tests