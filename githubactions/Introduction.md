Understanding github actions


1. GitHub Actions is a continuous integration and continuous delivery (CI/CD) platform that allows you to automate your build, test, and deployment pipeline.

2. Github actions goes beyond just devops and lets you run "workflows" when other events happen in your repository.
   Example: You can run workflows to add labels whenever someone creates a new issue in your repository.

Components of Github Actions:

1. Workflow 
   
   1. Workflow is a configurable automated process that will run one or more jobs. 
   2. Workflows are defined by YAML files checked in to your repository and will run when triggered by an event.
   3. Workflows are defined in the ".github/workflows" directory in a repository and a repository can have multiple workflows.
   
   Example:
     1. One workflow to build and test pull request.
     2. Another workflow to deploy your application every time a release is created.

2. Events

   1. Event is a specific activity in a repository that triggeres a workflow run.
      
       Event can be a pull request / opens an issue / pushes a commit.

3. Jobs

   1. A job is a set of steps in a workflow that is executed on the same runner. 
   2. Each step is either a shell script that will be executed or an action that will be run. 
   3. Steps are executed in order and are dependent on each other.
   4. Data can be shared between steps.
   5. Jobs dependencies can