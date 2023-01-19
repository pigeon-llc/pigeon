# pigeon


## Project Structure

* core - contains the encrypted messaging functionality, common shared libraries, etc.

* server - contains server-side tasks such as user authentication, message storage, database handling, etc.

* web - contains web front-end client

* desktop - contains desktop client app

* mobile - contains mobile client app



## CI / CD


### Branching Workflow

Three-way git branching model adapted for development:

* __release__ - used to prepare a release candidate. It is a branch that is created from the "main" branch and used to test and stabilize the codebase before it is released to production.

* __main__ - primary branch of the repository, and it is where the production-ready code is stored. It is the branch that is deployed to the production environment.

* _feature_ - An optional branch that is used to develop new features. It is created from the "main" branch and is used to develop new features before they are merged back into the "main" branch. This branch can be deleted after the feature is merged into the main branch.

This model keeps the main branch stable and only brings in new features that are thoroughly tested and validated. The release branch is used to stabilize the code and test it before it is deployed. The feature branch is used for development of new features, but it doesn't have to be used for every new feature, it depends on the team and project.

### Automation

Adapted __GitHub Actions__ tool for automating CI/CD pipelines (workflows)

```
CI/CD Workflow dependency graph:

                                                     +-------------+
                                                     |  Pipeline   |
                                                     +-----/\------+
                                                           ||
                                                           ||
                                                           ||
                                                           ||
       ____________________________________________________||_______________________________________________
       _____________________________________________________________________________________________________
       ||                       ||                       ||                      ||                       ||
+-------------+          +-------------+          +-------------+          +-------------+          +-------------+
|    Core     |          |     Web     |          |   Mobile    |          |   Server    |          |   Desktop   |
+-------------+          +-------------+          +-------------+          +-------------+          +-------------+
```

The workflow structure above consists of five separate workflows, one for each directory in the repository (_core_, _server_, _desktop_, _mobile_, _web_)
and one main workflow that depends on the successful completion of all the other workflows. Each workflow is triggered against changes in the corresponding directory, and the _pipeline_ workflow is triggered after all the other workflows have run successfully.
