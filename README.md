# vegeta-runner

Wrapper for vegeta console utility for load testing.

## Usage

### Environment generation

Your custom configuration and load test results is called `environment`.
All environments are located under the `envs` folder. Each environment has strict predefined structure.
For example:

```
--envs/
  |
  |-- custom_env_1/
      |
      |-- outputs_bin/
      |-- outputs_html/
      |-- targets
```

Lets consider in more detail the structure:

* `outputs_bin` - keeps binary of the load test results
* `outputs_html` - keeps html representations of the binary load test results
* `targets` - the plain text file which contains a list of endpoints for load tests

This structure could be generated via `env-gen` CLI script. Usage help:

```
$ ./env-gen --help
Usage: env-gen [options]
        --name=NAME                  The name of environment which you want to create
    -h, --help                       Prints this help
```

So, usage is very simple. For example, `./env-gen --name=custom_env_1` which creates a new environment with name `custom_env_1`. Very easy!


### Run environment load test

To perform load test for first you have to specify the following options:

* _rate_ - the number of requests per second
* _duration_ - how long test should be performed

The CLI command for running test looks like the following:

```
$ ./vegeta-runner --help
Usage: vegeta-runner [options]
        --rate=RATE                  The rate number: requests per second
        --duration=DURATION          The duration of the test
        --e=ENV                      The environment which you want to test
        --open=OPEN                  Should the report be opened automatically or not
    -h, --help                       Prints this help
```

The additional option `open` could be `yes|true|+|1` which specifies whether html report should be opened in a browser or not.
