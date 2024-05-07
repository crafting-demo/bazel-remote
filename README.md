# Bazel Remote Executor on Crafting Sandbox

This is a reference solution for running a lightweight Bazel Remote Executor
(backed by [nativelink](https://github.com/TraceMachina/nativelink))
in a Crafting workspace and turns the workspace into a Bazel Remote Executor.

## Quick Start

From Crafting WebConsole,
create a new sandbox from this git repository: `https://github.com/crafting-demo/bazel-remote`,
and wait until the sandbox is auto self-updated and then becoming ready.
Find the connect instruction from the overview of the sandbox.

## Customization

This is a reference solution, so customize based on your needs.

### Bazel Cache

Bazel cache is always required when running with a remote executor.
To use your own bazel cache,
please update `executors/nativelink/config.json` so _nativelink_ is able to use it.
Also add `--remote_cache=...` to the `bazel build` command line.

### Environment Consistency

Some bazel plugins requires consistency between your local environment and that in the remote executor (Crafting workspace),
regarding location and version of toolchains, environment variables etc.
Please pay attention to this when setting up local environment and the Crafting workspaces to avoid unexpected behavior.

### Alternative Executor

In this solution, [nativelink](https://github.com/TraceMachina/nativelink) is used because it's simple and lightweight.
Alternative executors can also be installed and running in the Crafting workspace, as long as it exposes the gRPC port,
the same connect instruction can be used.
