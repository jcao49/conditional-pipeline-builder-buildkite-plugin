# Conditional Pipeline Builder Buildkite Plugin

A helper tool that checks for the git diff of a branch against main and conditionally sets build meta-data depending on paths that the user specifies, used to build dynamic pipelines in which steps can be skipped.

## Example

Add the following to your `pipeline.yml`:

```yml
steps:
  - command: ls
    plugins:
      - https://github.com/jcao49/conditional-pipeline-builder-buildkite-plugin.git:
          conditional-pipeline-slug: "my-dynamic-pipeline"
          lint-group: ["packages/web/*", "packages/tests/*"]
```

## Configuration

### `conditional-pipeline-slug` (Required, string)

The dynamic pipeline that will conditionally run steps. 

### `lint-group`

The paths that you wish to trigger this step/group of lint tests to run on.

## TODOs:
- update the plugin so that it takes in a more flexible input:
```yml
steps:
  - command: ls
    plugins:
      - https://github.com/jcao49/conditional-pipeline-builder-buildkite-plugin.git:
          conditional-pipeline-slug: "my-dynamic-pipeline"
          lint-group:
              key: "lint-group-key"
              includes: ["packages/web/*", "packages/tests/*"]
              excludes: ["packages/blah/*"]
```
