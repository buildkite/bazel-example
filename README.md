# Building with Bazel on Buildkite

[![Add to Buildkite](https://buildkite.com/button.svg)](https://buildkite.com/new)

This repository is an example of how to use [Bazel](https://www.bazel.build/) to build a C++ project on [Buildkite](https://buildkite.com/).

Note: this example assumes you've already installed Bazel on your Buildkite Agent.

## How does it work?

The [pipeline.yml](.buildkite/pipeline.yml) tells Bazel to build the `hello-world` target in the `BUILD` file in the `main` directory.

```yml
steps:
  - label: ":bazel: Build"
    commands:
      - bazel build //main:hello-world
```