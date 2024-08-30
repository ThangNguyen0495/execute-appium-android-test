# Android Appium Workflow Action

This custom GitHub Action is designed to run Appium tests using Maven for Android applications. It provides flexibility by allowing users to specify the Java and NodeJS versions, download artifacts, switch branches, run Appium on a specific port, and use custom Maven commands.

## Features

- **Java and NodeJS Version Support**: Install and use specified versions of Java (default is `22`) and NodeJS (default is `21`).
- **Artifact Download**: Optionally download an artifact containing the test source code.
- **Branch Switching**: Optionally switch to a different branch before running tests.
- **Appium Server Configuration**: Specify the port for the Appium server (default is `4723`).
- **Custom Maven Commands**: Run custom Maven commands to execute tests.
- **Automated Test Execution**: Easily configure and run Appium tests with various parameters.

## Inputs

| Input Name     | Description                                                             | Required | Default |
|----------------|-------------------------------------------------------------------------|----------|---------|
| `java_version` | The version of Java to install.                                          | false    | `22`    |
| `node_version` | The version of NodeJS to install.                                        | false    | `21`    |
| `artifact`     | The artifact to download, containing the test source code.               | false    |         |
| `test_config`  | The test configuration file to use.                                      | false    |         |
| `test_name`    | The name of the test suite.                                              | true     |         |
| `branch_name`  | The branch name to switch to.                                            | false    |         |
| `appium_port`  | The port on which the Appium server should run.                          | false    | `4723`  |
| `scripts`      | The Maven commands to execute the test.                                  | false    |         |

## Usage

To use this action in your GitHub workflow, include the following steps:

```yaml
name: Run Appium Tests

on:
  workflow_dispatch:

jobs:
  android-appium-tests:
    runs-on: ubuntu-latest

    steps:
    - name: Run Android Appium Workflow
      uses: ThangNguyen0495/execute-appium-android-test@v1.0.0
      with:
        java_version: '22'             # Optional: Specify Java version
        node_version: '21'             # Optional: Specify NodeJS version
        artifact: 'your-artifact-name' # Optional: Name of the artifact to download
        test_config: 'testng.xml'      # Optional: Path to the test configuration file
        test_name: 'MyTestSuite'       # Required: Name of the test suite
        branch_name: 'main'            # Optional: Branch to switch to
        appium_port: '4723'            # Optional: Port for the Appium server
        scripts: 'mvn clean test'      # Optional: Custom Maven commands to run the tests
