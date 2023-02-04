# Basics of GitHub Actions

GitHub Actions is a platform for automating software workflows. It is built into GitHub, so you can use it to build, test, and deploy your code right from GitHub.

To use GitHub Actions, you create "workflows" in your repository's `.github/workflows` directory. A workflow is a set of rules that define how your code should be built, tested, and deployed. You can create multiple workflows in a single repository, and each workflow can have multiple steps.

### Features of GitHub Actions

* Workflow triggers: Workflows can be triggered by a variety of events, such as pushes to the repository, pull requests, or the creation of a release.
    
* Jobs and steps: Workflows are made up of one or more jobs, which are made up of steps. Steps are individual tasks that are executed in order, and can be run in parallel or sequentially.
    
* Actions: Steps in a job can be implemented using actions, which are pre-built blocks of code that perform specific tasks. You can use actions provided by GitHub or the community, or create your own custom actions.
    
* Matrix builds: You can use matrix builds to run a job with different configurations or environments, such as different versions of a programming language or different operating systems.
    
* Conditional execution: You can use conditions to control whether a step or job is executed based on certain criteria, such as the branch or event that triggered the workflow.
    
* Secrets: Secrets are encrypted environment variables that can be used in your workflows to store sensitive information like API keys or passwords.
    
* Artifacts: Artifacts are files that are produced by a job and can be shared with other jobs in the same workflow or saved for later use.
    
* Caching: You can use caching to speed up your workflows by storing dependencies and building outputs between runs.
    
* Marketplace:It is a platform for finding and purchasing tools and services that integrate with GitHub. It includes a wide range of products, including integrations, themes, and applications, as well as services like training and consulting.
    

### The syntax for GitHub Actions

GitHub Actions use YAML syntax to define workflows and actions. Here is the general structure of a workflow file:

```yaml

name: Name of the workflow

on:
  - event1
  - event2
  - …

jobs:
  job1:
    runs-on: ubuntu-latest
    steps:
      - step1
      - step2
      - …
  job2:
    runs-on: windows-latest
    steps:
      - step1
      - step2
      - …
```

* `name` is the name of the workflow, which will be displayed in the GitHub Actions tab of the repository.
    
* `on` is a list of events that will trigger the workflow to run. Possible events include `push`, `pull_request`, and `release`.
    
* `jobs` is a list of jobs that make up the workflow. Each job consists of a list of `steps` that are executed in order.
    
* `runs-on` specifies the operating system on which the job will run.
    
* `steps` is a list of actions that make up the job. Each step is a block of code that does a specific task, such as running tests or deploying code.
    

### Example :

Here's an example workflow that builds and tests a Node.js project

```yaml
name: Node.js CI

on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - uses: actions/setup-node@v1
      with:
        node-version: 12.x
    - run: npm install
    - run: npm test
```

This workflow will run every time you push code to your repository or open a pull request. It will run on the latest version of Ubuntu, install Node.js, run `npm install` to install your dependencies, and then run `npm test` to run your tests.

### actions/checkout

The `actions/checkout` action is a pre-built action in the GitHub Actions Marketplace that you can use in your workflows to check out a repository's code. It is commonly used as the first step in a workflow to retrieve the code that the workflow will operate on. We can also use

1. To check out a specific branch or commit: The `actions/checkout` action allows you to specify the `ref` option to check out a specific branch or commit. This is useful if you want to build, test, or deploy a specific version of your code.
    
2. To persist the repository's credentials: By default, the `actions/checkout` action does not persist the repository's credentials in the runner's environment. However, you can use the `persist-credentials` option to do this. This can be useful if you want to perform additional operations on the repository, such as pushing changes, from within the workflow.
    
3. To check out a subdirectory: The `actions/checkout` action allows you to specify the `paths` option to check out only a specific subdirectory of the repository. This is useful if you want to operate on only a part of the repository's code.
    

### Secrets

In GitHub, a "secret" is a secure environment variable that you can use in your Actions workflows. Secrets are stored encrypted and are only exposed to selected Actions in your workflows. They are useful for storing sensitive information like API keys, passwords, and private tokens that you do not want to hard code in your repository.

To use a secret in a workflow, you first need to create it in the repository's Settings tab. Go to the Settings tab, then click on "Secrets" in the left-hand menu. From here, you can add a new secret by giving it a name and entering its value.

Once you have created a secret, you can use it in your workflow by referencing it with the `${{ secrets.SECRET_NAME }}` syntax. For example:

```yaml
- name: Deploy to staging
  uses: actions/aws-lambda-deploy@v1
  with:
    access-key: ${{ secrets.AWS_ACCESS_KEY_ID }}
    secret-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
    region: us-east-1
    function-name: staging-lambda-function
    zip-file: dist/lambda.zip
```

In this example, the `access-key` and `secret-key` input parameters are being set to the values of the `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY` secrets, respectively.

Keep in mind that secrets are only accessible to the repository they are created in and are not shared with forks. This means that if you are using a fork of a repository in your workflow, you will need to create the necessary secrets in the fork as well.

### Matrix Build

Matrix builds allow you to test your code against multiple versions of dependencies or run tests on multiple operating systems or architectures. This is useful for ensuring that your code works across a wide range of environments.

To use matrix builds in GitHub Actions, you can use the `strategy` field in your workflow file to define the matrix. The `strategy` field takes an object with the `matrix` key, which specifies the variables you want to test.

Here is an example workflow that uses matrix builds to test a Node.js project against different versions of Node.js:

```yaml
name: Node.js CI

on: [push, pull_request]

jobs:
  build:
    name: Test on Node.js ${{ matrix.node-version }}
    strategy:
      matrix:
        node-version: [10.x, 12.x, 14.x]
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-node@v1
        with:
          node-version: ${{ matrix.node-version }}
      - run: npm install
      - run: npm test
```

This workflow will run a job for each value in the `node-version` matrix. The job will run on the latest version of Ubuntu, install the specified version of Node.js, run `npm install` to install the dependencies, and then run `npm test` to run the tests.

Matrix builds can also be combined with other features of GitHub Actions, such as secrets and self-hosted runners. For example, you could use matrix builds to test your code against different versions of dependencies on multiple operating systems, or to test your code on different architectures using self-hosted runners.

### Conclusion

GitHub Actions makes it easy to automate your software development process. You can use it to build, test, and deploy your code, as well as automate other tasks like releasing new versions of your software or deploying to different environments. To learn more, check out the documentation.