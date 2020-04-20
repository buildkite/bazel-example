# Building with Bazel on Buildkite

[![Add to Buildkite](https://buildkite.com/button.svg)](https://buildkite.com/new)

This repository is an example of how to use [Bazel](https://www.bazel.build/) to build a C++ project on [Buildkite](https://buildkite.com/).

Note: this example assumes you've already installed Bazel on your Buildkite Agent.

## How does it work?

The empty `WORKSPACE` file marks the directory as a Bazel workspace, and the `main/BUILD` contains the Bazel build targets.

The Buildkite [pipeline.yml](.buildkite/pipeline.yml) file tells Bazel to build the `hello-world` target in `main/BUILD`:

```yml
steps:
  - label: ":bazel: Build"
    commands:
      - bazel build //main:hello-world
```

The `hello-world` target uses the Bazel`cc_binary` rule to build a `hello-world` executable from the source file `hello-world.cc`.

If you want to test the result by running the resulting binary, add the following line to your copy of the Pipeline:

```yml
        - bazel-bin/main/hello-world
```

## License

See [License.md](License.md) (MIT)
