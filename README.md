# CircleCI learning path

<!-- TOC -->

- [Guidance](#guidance)
- [Lesson 1: Creating a simple workflow](#lesson-1-Creating-a-simple-workflow)
  - [Principle 1](#principle-1)
  - [Practice 1](#practice-1)
    - [Lab 1.1: Storing Data](#lab-11-storing-data)
    - [Lab 1.2: Reading Data](#lab-12-reading-data)
      - [Question: CloudFormation Console](#question-cloudformation-console)
    - [Lab 1.3: Integration with CloudFormation](#lab-13-integration-with-cloudformation)
  - [Retrospective](#retrospective)
    - [Question 1](#question-1)
    - [Question 2](#question-2)
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

### Retrospective 1

#### Question 1:
What is the difference between Organization, Project and Job environment variabls scopes?

#### Question 2:
Can you use pipeline values outside of job context. Can you use them for example in your shell script?


---

## Lesson 2: Persisting data in Workflows

https://circleci.com/blog/persisting-data-in-workflows-when-to-use-caching-artifacts-and-workspaces/


### Principle 1
[Caching](https://circleci.com/docs/2.0/caching/) is particularly useful with package dependency managers
Caching persists data between the same job in different Workflow builds.

### Practice 1

#### Lab 2.1: Cache dependencies
- [Caching](https://circleci.com/docs/2.0/caching/) is particularly useful with package dependency managers
- 
- Use the save_cache step to cache virtual environment and installed packages 
- Use the restore_cache step to restore cached files or directories.

### Principle 2
Workspaces persist data between jobs in a single Workflow. Unlike caching, workspaces are not shared between runs as they no longer exists once a workflow is complete.
### Practice 2

#### Lab 2.2: Use workspaces
[Workspaces](https://circleci.com/docs/2.0/configuration-reference/#persist_to_workspace) are a feature of Workflows and are used to move data from a job in a Workflow to subsequent jobs.
Unlike caching, workspaces are not shared between runs as they no longer exists once a workflow is complete

### Principle 3
Artifacts persist data after a Workflow has finished.
### Practice 3

#### Lab 2.3: Create artifacts in build job
- [Artifacts](https://circleci.com/docs/2.0/artifacts/)



#### Lab 1.4: Execute job only for a specific branch
- create a new branch in your repo
- configure execution of one of the jobs in the workflow to run only when changes pushed only to a new branch
- push your changes at first into main(master) branch - see if the job will run. Then push your changes into new branch and check again

#### Lab 1.4: Handle failure
- add steos that will execute on fail 

#### Lab 1.5: Add approval step
- add approval step between test and deploy jobs

Subjects:

https://circleci.com/blog/deep-diving-into-circleci-workspaces/

https://circleci.com/docs/2.0/artifacts/

* 00-setup-helloworld-project

* 01-jobs-workflows ( aproval steps, filter by branch name, on fail)
* 01-env-variables

* 02-sharing-files: workspace, cache, artifacts. test results
* artifacts and test results

* 04-reusable-commands


* orbs
* context - example slack integration
* Secrets Management and context

* [personal-api-token](https://circleci.com/docs/2.0/managing-api-tokens/#creating-a-personal-api-token)
* debug - rerun with ssh
* local CLI (https://circleci.com/docs/2.0/local-cli/)


* convenience-images (https://circleci.com/blog/announcing-our-next-generation-convenience-images-smaller-faster-more-deterministic/)
* working with API v2

## Further Reading

- [Using Custom-Built Docker Images](https://circleci.com/docs/2.0/custom-images/)
- <https://academy.circleci.com/>