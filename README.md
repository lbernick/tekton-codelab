This repo contains example Tekton Tasks and Pipelines to run CI/CD for a Dockerized application.

Contents:
- **basic-pod.yaml**: An example pod to experiment with
- **git-clone-task.yaml**: An example Task and TaskRun to experiment with
- CI Pipelines
  - **basic-ci-pipeline.yaml**: A Pipeline and PipelineRun that clone an example repository,
    build a Docker image, and push that image to GCR. This Pipeline is the starting point
    for all of the other Pipelines in this repo.
  - **ci-pipeline-with-tests.yaml**: A Pipeline and PipelineRun that include the functionality of
    the basic CI pipeline, plus unit tests and integration tests.
  - **ci-pipeline-with-gitcreds.yaml**: A Pipeline and PipelineRun that modify the basic
    CI pipeline so that it can be used with a private Git repository. This also requires
    creating a Kubernetes [secret](https://kubernetes.io/docs/concepts/configuration/secret/)
    to store GitHub credentials.

Setup required:
- Install Tekton Pipelines and [configure feature flags](https://tekton.dev/docs/pipelines/install/#customizing-the-pipelines-controller-behavior)
  to enable OCI bundles and other alpha features.