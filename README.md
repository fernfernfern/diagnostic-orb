# Diagnostic Orb
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
            - diagnostic-orb/store-report
```

The commands below are indended to be added as `pre-steps` for jobs you'd like to investigate.

### diagnostic-orb/env-info
Generate a report of various kinds of enviroment information. Helpful to find out what packages are install in the enviroment.

```yaml
diagnostic-orb/env-info
```

### diagnostic-orb/ios-logs
Save Fastlane and Xcode information from an iOS job, to be stored as artifacts and inspected later.

```yaml
diagnostic-orb/ios-logs
```

### diagnostic-orb/memory
Start top as a background process that appends output to a file. Helpful to see memory consumption and process lifecycle over the duration of a job

```yaml
diagnostic-orb/memory
```

### diagnostic-orb/test-results
Create sample test JUnit XML output for Test Summary report. Helpful if you want to sanity check if test data collection is working.

```yaml
diagnostic-orb/test-results
```

### diagnostic-orb/clear-dlc
Remove cached docker layers. Helpful to troubleshoot issues with image caches or to clear image cache space.

```yaml
diagnostic-orb/clear-dlc
```

## Contributing
We welcome [issues](https://github.com/CircleCI-Public/diagnostic-orb/issues) (bugs or feature requests) and [pull requests](https://github.com/CircleCI-Public/diagnostic-orb/pulls)!

For larger discussions, there is also an active community at https://discuss.circleci.com/c/orbs.
