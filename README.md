# CircleCI learning path

My work on online cource about CircleCI

<!-- TOC -->

- [Guidance](#guidance)

- [Lesson 1: Creating a simple workflow](#lesson-1-Creating-a-simple-workflow)
  - [Principle 1](#principle-1)
  - [Practice 1](#practice-1)
    - [Lab 1.1: Setup your first project](#lab-11-setup-your-first-project)
    - [Lab 1.2: Create jobs and workflow](#lab-12-create-jobs-and-workflow)
    - [Lab 1.3: Use built-in env variables](#lab-13-use-built-in-env-variables)
    - [Lab 1.4: Create env variables](#lab-14-create-env-variables)    
  - [Retrospective](#retrospective)
    - [Question 1](#question-1)
    - [Question 2](#question-2)
- [Lesson 2: Persisting data in Workflows](#lesson-2-persisting-data-in-workflows)
  - [Principle 1](#principle-1)
  - [Practice 1](#practice-1)
    - [Lab 2.1: Cache dependencies](#lab-21-cache-dependencies)
  - [Principle 2](#principle-2)  
  - [Practice 2](#practice-2)
    - [Lab 2.2: Use workspaces](#lab-22-use-workspaces)
  - [Principle 3](#principle-3)      
  - [Practice 3](#practice-3)
    - [Lab 2.3: Create artifacts](#lab-23-create-artifacts)
    - [Lab 2.4: Save test results](#lab-24-save-test-results)    
  - [Retrospective](#retrospective)
    - [Question 1](#question-1)
- [Lesson 3: Controlling jobs](#lesson-3-controlling-jobs)
  - [Principle 1](#principle-1)
  - [Practice 1](#practice-1)
- [Lesson 4: Manage Secrets](#lesson-4-manage-secrets)
  - [Principle 1](#principle-1)
  - [Practice 1](#practice-1)
- [Lesson 5: Appendix](#lesson-5-appendix)
  - [Principle 1](#principle-1)
  - [Practice 1](#practice-1)
- [Further Reading](#further-reading)
<!-- /TOC -->

## Guidance

## Lesson 1: Creating a simple workflow

### Principle 1
TODO: write prefrace Something about CI/CD and CircleCI

### Practice 1
Create your first first pipeline in CircleCI that will combine a few simple jobs 

#### Lab 1.1: Setup your first project
- connect github to CircleCI
- create new repo
- create simple config file (.circleci/config.yml)
- use docker image and echo some text
- set working_directory

#### Lab 1.2: Create jobs and workflow
- create workflow with 3 jobs: test build deploy
- create simple bash script that will echo some text and create file
- add checkout step
- add step where you execute your script

#### Lab 1.3: Use built-in env variables
- print: workflow id, branch name and number of the build

#### Lab 1.4: Create env variables
- add an environment variable in project settings
- add a job that will print your environment variable

### Retrospective

#### Question 1:
What is the difference between Organization, Project and Job environment variabls scopes?

#### Question 2:
Can you use pipeline values outside of job context. Can you use them for example in your shell script?


---

## Lesson 2: Persisting data in Workflows
Read about [persisting data in CircleCI](https://circleci.com/blog/persisting-data-in-workflows-when-to-use-caching-artifacts-and-workspaces/)

### Principle 1
[Caching](https://circleci.com/docs/2.0/caching/) is particularly useful with package dependency managers
Caching persists data between the same job in different Workflow builds.

### Practice 1


#### Lab 2.1: Cache dependencies
- create python virtual environment
- install packages
- Use the save_cache step to cache virtual environment and installed packages 
- Use the restore_cache step to restore cached files or directories.

### Principle 2 
[Workspaces](https://circleci.com/docs/2.0/configuration-reference/#persist_to_workspace) persist data between jobs in a single Workflow. Unlike caching, workspaces are not shared between runs as they no longer exists once a workflow is complete.
### Practice 2

#### Lab 2.2: Use workspaces
- 1
- 2

### Principle 3
[Artifacts](https://circleci.com/docs/2.0/artifacts/) persist data after a Workflow has finished.

### Practice 3

#### Lab 2.3: Create artifacts in build job
- 1
- 2

#### Lab 2.4: Save Test results
- 1
- 2

## Further Reading
- https://circleci.com/blog/deep-diving-into-circleci-workspaces/
- https://circleci.com/docs/2.0/configuration-reference/#executors-requires-version-21
---

## Lesson 3: Controlling jobs

### Principle 1

### Practice 1
Controlling workflow 

#### Lab 3.1: Execute job only for a specific branch
- create a new branch in your repo
- configure execution of one of the jobs in the workflow to run only when changes pushed only to a new branch
- push your changes at first into main(master) branch - see if the job will run. Then push your changes into new branch and check again


#### Lab 3.2: Handle failure
- add step that will execute on fail 

#### Lab 3.3: Add approval step
- add approval step between test and deploy jobs

#### Lab 3.4: Logic statements
- 

### Practice 2
Write a reusable command that destroys the stack if deployment failed

#### Lab 3.4: Use commands to perform rollback
- create a simple CloudFormation template that will create some infrastructure.
- write a job that creates a new stack using template you defined. You can use amazon/aws-cli image
- make your job intentionally fail
- Add a command-step that only executes if the job fails


#### Lab 3.5: Use orbs
* [orbs](https://circleci.com/docs/2.0/orb-intro/)


## Lesson 4: Manage Secrets

### Principle 1
- add_ssh_keys option

#### Lab 4.1: 
- Create a key pair
- add contents of PEM file to the SSH keys into CircleCI
- create CFN template that creates EC2 instance. Use your key pair


### Principle 2
- add context
- add slack integration

## Lesson 5: Appendix

* working with API v2
* [personal-api-token](https://circleci.com/docs/2.0/managing-api-tokens/#creating-a-personal-api-token)
* [local CLI](https://circleci.com/docs/2.0/local-cli/)
* SSH into your build

--- 

## Further Reading

- [Using Custom-Built Docker Images](https://circleci.com/docs/2.0/custom-images/)
- [CircleCI academy](https://academy.circleci.com/)
- [Convenience images](https://circleci.com/blog/announcing-our-next-generation-convenience-images-smaller-faster-more-deterministic/)