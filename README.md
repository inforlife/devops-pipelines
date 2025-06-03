# DevOps Pipelines
This repository serves as the entry point for the automated processes defined by the Software Development Team at InfoRLife SA for building and deploying code.

The `dispatch` workflow [triggers a GitHub Actions workflow](https://docs.github.com/en/rest/repos/repos?apiVersion=2022-11-28#create-a-repository-dispatch-event) on a target repository to initiate the automated DevOps process.

The `dispatch` workflow is, in turn, triggered by adding a comment to the Issue named after the target repository. For instance, a comment added to an issue with the title `New App` will dispatch the event to the `new-app` repository (titles are lower and kebab-cased).

The content of the comment defines the event dispatched to the target repository, along with its optional payload. Currently, the payload may be formed by only one parameter.

The target repository must have a workflow triggered by the `repository_dispatch` event, with the dispatched event specified as `type`.

For instance, if the `touch` event is dispatched to the `new-app` repository, the `new-app` repository must have a workflow triggered by the `repository_dispatch` event, with the `touch` as `type`.

```
on:
  repository_dispatch:
    types: [touch]
```
