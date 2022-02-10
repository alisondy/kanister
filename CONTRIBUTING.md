# Contributing to Kanister

## How Can I Contribute?

### Reporting Bugs
Before creating bug reports, please check the list of issues as you might find out that a similar issue is already created and you don't need to create one. Also when creating a bug report, please include as many details as possible as this information may help us resolve the issue faster.

### Suggesting Enhancements
You can suggest minor improvements to existing functionality and or a completely new feature. For that, we recommend creating an issue at https://github.com/kanisterio/kanister/issues or reaching out to us at our [Slack](https://join.slack.com/t/kanisterio/shared_invite/enQtNzg2MDc4NzA0ODY4LTU1NDU2NDZhYjk3YmE5MWNlZWMwYzk1NjNjOGQ3NjAyMjcxMTIyNTE1YzZlMzgwYmIwNWFkNjU0NGFlMzNjNTk) workspace.

### Your first code contribution
You can start by looking through `good-first-issue` issues. 
  
#### Local Developement
Once we are done with the changes, we need to make sure, that the changes are not breaking anything and are passing the unit as well as the integration test.

```bash
#Run golint command to make sure your code is properly formatted
make golint

#build the project
make build

#Run unit test 
make test
```

We need to have a local Kubernetes cluster to deploy the controller with the changes included and run the integration test. 

We can use [Kind](https://kind.sigs.k8s.io/) to spin up a local Kubernetes cluster, `make start-kind` can be run from the project's root directory to create one. Similarly to delete the cluster we can run `make stop-kind`.

To deploy the controller to a Kubernetes cluster [this document](https://docs.kanister.io/install.html#building-and-deploying-from-source) can be referred.

Once the kanister controller is deployed, run the integration test.

```bash
# Run E2E test
# From the project root directory
make integration-test
```
The above command runs the integration test for all the applications. To run the integration test for a specific application use the following command.

```bash
# specify the application(or regex expression) for which the integration test needs to be run.
# For example ^PostgreSQL$
SHORT_APPS="^PostgreSQL$|^MySQL$|Elasticsearch|^MongoDB$|Maria|^MSSQL$"

# Run E2E test
# From the project root directory
./build/integration-test.sh ${SHORT_APPS}

```
**Note:** We can find the application name from `/pkg/testing/integration_register.go`

Once the integration test passes. Create a pull request with the changes for review. Please refer [Raising PR](#raising-pr)

### Contributing to documentation
For complete documentation visit https://docs.kanister.io/

Kanister docs are generated using [Sphinx](https://www.sphinx-doc.org/en/master/) and are written in [reStructuredText](https://docutils.sourceforge.io/rst.html). The source `.rst` files are in the Kanister repository under the `/docs` folder.

### Updating documentation
- We can modify or add `.rst` file(s) under the `/docs` folder.

- Build Docs locally
```bash
make docs
```

- The above command will build the documentation, check for errors and place the final output in the `/docs/_build/html` directory.

- The built docs can be viewed and validated visually by opening `/docs/_build/html/index.html`.

- Push a PR with the changes for review. Please see [Raising PR](#raising-pr)

## Raising PR 
* We follow the [Github Pull Request Model](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests) for all contributions.
* For new features, documentation must be included.
* Here are some guidelines that we should follow while writing a commit message:
  - Commit message should be imperative. For example, `Add go mod check while init` and not `Added go mod check while init`.
  - Commit message should not start with lower case.
  - Your commit message should not contain any whitespace errors.
  - Remove unnecessary punctuation marks.
  - Use the body to explain what changes you have made and why you made them.

## Contacting Developers
Using [Slack](https://join.slack.com/t/kanisterio/shared_invite/enQtNzg2MDc4NzA0ODY4LTU1NDU2NDZhYjk3YmE5MWNlZWMwYzk1NjNjOGQ3NjAyMjcxMTIyNTE1YzZlMzgwYmIwNWFkNjU0NGFlMzNjNTk) is the quickest way to get in touch with developers.
