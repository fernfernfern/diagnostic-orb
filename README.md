# Diagnostic Orb [![CircleCI status](https://circleci.com/gh/CircleCI-Public/diagnostic-orb.svg)](https://circleci.com/gh/CircleCI-Public/diagnostic-orb)

The diagnostic orb is intented to serve two purposes:

1. Help guide people using CircleCI to solve problems and optimize their configurations.

2. Help surface and collect information so CircleCI engineers can help solve problems.


## Usage:

Reference the orb in your config.yml. 2.1 Build Processing must be enabled on the project. Check the bottom of your `Advanced Settings` section in your project settings.

```yaml
orbs:
  diagnostic-orb: circleci/diagnostic-orb@1.0.0
```

The diagnostic orb is intended to be applied as `pre-steps` and `post-steps` in most cases. Always include `diagnostic-orb/post-steps` to collect results generated in `pre-steps`.

```yaml
workflows:
  my-workflow:
    jobs:
      - my-super-neat-job:
          pre-steps:
            - diagnostic-orb/env-info
          post-steps:
            - diagnostic-orb/post-steps
```

The commands below are indended to be added as `pre-steps` for jobs you'd like to investigate.

### diagnostic-orb/env-info
Generate a report of various kinds of enviroment information. Helpful to find out what packages are install in the enviroment.

### diagnostic-orb/memory
Start top as a background process that appends output to a file. Helpful to see memory consumption and process lifecycle over the duration of a job

### diagnostic-orb/sample-test-data
Create sample test junit output for Test Summary report. Helpful if you want to sanity check if test data collection is working. Pass `upload: true` to have it automatically run `store_test_results`.

```yaml
daignostic-orb/sample-test-data:
  upload: true
```

## Contributing
We welcome [issues](https://github.com/CircleCI-Public/diagnostic-orb/issues) (bugs or feature requests) and [pull requests](https://github.com/CircleCI-Public/diagnostic-orb/pulls)!

For larger discussions, there is also an active community at https://discuss.circleci.com/c/orbs.
