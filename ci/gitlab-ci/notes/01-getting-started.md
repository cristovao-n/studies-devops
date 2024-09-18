# Gitlab CI

## Architecture

-   Gitlab instance / Gitlab Server
-   Gitlab runners

### Gitlab Instance or Gitlab Server

Gitlab Server assigns pipelines jobs to available runners

### Gitlab runners

Server machines configured to run the CI/CD jobs

### Infrastructure

Gitlab offers a gitlab instance and gitlab runners to provide a fast getting started, but you can connect and setup your own infrastructure, which is a more professional and a common use case for companies

## First steps

Building a CI/CD pipeline for an application doesn't require in-depth knowledge of the source code or its implementation details. However, you need a solid understanding of the following aspects to construct the pipeline:

-   Familiarity with base technologies: Know the programming language, framework, package manager, testing tools, formatting tools, and linting tools being used.
-   App execution and deployment: Understand how to run the development server, build the application, and containerize it if necessary.
-   Running tests: Be aware of how to execute the application's test suite.
-   Code quality and guidelines: Know how to run tools related to code quality and best practices.

## Writing Pipeline

Pipeline is written in YAML format and is hosted in the application's repository as a file called `.gitlab-ci.yml`

### Jobs

Jobs are the most fundamental building block of a `.gitlab-ci.yml` file  
Jobs define what to do

#### Executors

We need to specify the environment where the job will be executed by the gitlab runner  
The Gitlab Runner will use a shell executor or a docker executor

##### Shell executor

-   Shell is the simplest executor
-   Jobs commands executed directly in the operating system

##### Docker executor

-   The gitlab runner only needs Docker to be installed
-   You can specify the base image for your container
-   Each job runs in a separate container

#### Services

> TODO:

#### Examples

A job that runs tests in a python application using a Docker executor with a python image and a before_script command to install the remaining needed dependencies

`.gitlab-ci.yml`

```yml
run_tests:
    image: python:3.9-slim-buster
    before_script:
        - apt update && apt install make
    script:
        - make test
```

### Variables

You can create variables to store sensible data that shouldn't be spelled directly in the code  
They'll be added as environment variables in the environment the job will be executed

Example of a Docker job that builds a new image and needs sensible credentials

```yml
build_image:
    image: docker:20.10.16
    before_script:
        - docker login -u $DOCKERHUB_USER -p $DOCKERHUB_PASSWORD
    script:
        - docker build -t
```

> TODO: Find a simpler example

### Stages

If we only specify the jobs, they'll run in parallel and no order is guaranteed  
To run the jobs sequentially, we need to define stages  
Multiple jobs in the same stage are executed in parallel

Defining stages

`.gitlab-ci.yml`

```yml
stages:
  - test
  - build

job1:
  stage: test
  ...

job2:
  stage: build
  ...
```

## Configuring Runners

...

## TODO

-   Artifacts
-   Caching
-   Job.Rules
-   Job.Extends
-   Job.Tags
-   Triggering jobs

---

## References

Youtube Video: https://www.youtube.com/watch?v=qP8kir2GUgo&t=87s
Demo Repository: https://gitlab.com/ncristovao/python-demoapp
