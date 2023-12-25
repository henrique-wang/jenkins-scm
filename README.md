# jenkins-scm
Jenkins Pipeline SCM - Jenkinsfile properties study

## Scenarios

### Hello World
- Description: The Jenkins Pipeline just prints a "Hello World" message and the number of the current build.
- Branch: https://github.com/henrique-wang/jenkins-scm/tree/hello-world

## Input Parameters
- Description: The Jenkins Pipeline receives 5 different types parameters (STRING, TEXT, BOOLEAN, CHOICE, PASSWORD) and prints their respective values.
- Branch: https://github.com/henrique-wang/jenkins-scm/tree/jenkins-parameters

## Node Project coverage cover
- Description: Simulates a case where the coverage cover during the Test stage is less than minimum requirement. The Jenkins Pipeline aborts the job running, sets its status to "FAILED" and sends an e-mail to the user who triggered the job communicating the final result.
- Branch: https://github.com/henrique-wang/jenkins-scm/tree/node-coverage-cover-failed

## Node Project unit test failed
- Description: Simulates a case where an unit test fails during the Test stage. The Jenkins Pipeline aborts the job running, sets its status to "FAILED" and sends an e-mail to the user who triggered the job communicating the final result.
- Branch: https://github.com/henrique-wang/jenkins-scm/tree/node-failed-unit-test

## Node Project success deploy
- Description: Simulates a success deploy. The Jenkins Pipeline copies the Node project from the Git Repository, installs all dependencies, runs all unit tests, build a new Docker image and publish to the repository. Using a shared library, it sends an e-mail to the user who triggered the job communicating the final result.
- Branch: https://github.com/henrique-wang/jenkins-scm/tree/node-success-build
