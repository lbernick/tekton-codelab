This repo contains example Tekton Tasks and Pipelines to run CI/CD for a Dockerized application.

Contents:
- **kubernetes-intro**: simple Kubernetes API resource examples to experiment with
- **tekton-intro**: simple Tekton API resource examples to experiment with
- **docker-ci-example**: sample CI pipelines for a Dockerized web app.
  All examples use the Docker build Task (in build-task.yaml) and
  ServiceAccount (in serviceaccount.yaml). Requires
  [Workload identity](https://cloud.google.com/kubernetes-engine/docs/how-to/workload-identity)
  to be configured on the cluster.
  - **basic-ci-pipeline**: A Pipeline and PipelineRun that clone an example repository,
    build a Docker image, and push that image to GCR. This Pipeline is the starting point
    for all of the other Pipelines in this repo.
  - **ci-pipeline-with-tests**: A Pipeline and PipelineRun that include the functionality of
    the basic CI pipeline, plus unit tests and integration tests.
  - **ci-pipeline-with-gitcreds**: A Pipeline and PipelineRun that modify the basic
    CI pipeline so that it can be used with a private Git repository, plus an example
    Kubernetes [secret](https://kubernetes.io/docs/concepts/configuration/secret/)
    to store GitHub credentials.
  - **ci-pipeline-with-notify**: A Task that posts a message to Google chat, and a Pipeline
    and PipelineRun that modify the basic CI pipeline to notify Google chat with the status of
    the build. 
  - **remote-ci-pipeline**: A PipelineRun which runs the Pipeline defined in basic-ci-pipeline.
    This requires installing [Tekton remote resolution](https://github.com/tektoncd/resolution#install)
    and the [git resolver](https://github.com/tektoncd/resolution/tree/main/gitresolver#install).
  - **full-ci-pipeline**: A Pipeline and PipelineRun combining the functionality of all other
    Pipelines in this folder.

Setup required:
- Install Tekton Pipelines and [configure feature flags](https://tekton.dev/docs/pipelines/install/#customizing-the-pipelines-controller-behavior)
  to enable OCI bundles and alpha features.