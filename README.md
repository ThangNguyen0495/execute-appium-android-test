# Android Appium Workflow Action

A custom GitHub Action designed to run Appium tests for Android applications with Maven. This action sets up an Android emulator, installs dependencies, runs Appium tests, and generates test reports. It's ideal for integrating Appium-based Android tests into your CI/CD pipeline on GitHub Actions.

## Inputs

### `java_version` (Optional)
- **Description**: The version of Java to install.
- **Default**: `22`
- **Required**: No

### `api_level` (Optional)
- **Description**: The SDK level for the Android emulator.
- **Default**: `35`
- **Required**: No

### `node_version` (Optional)
- **Description**: The version of Node.js to install.
- **Default**: `21`
- **Required**: No

### `test_name` (Required)
- **Description**: The name of the test suite. This will be used when uploading test reports.
- **Required**: Yes

### `scripts` (Optional)
- **Description**: The Maven commands to execute the tests. If not provided, a default Maven command will be used.
- **Required**: No

---

## Example Workflow

Here’s an example of how to use this action in your workflow:

```yaml
name: Run Appium Tests

on:
  push:
    branches:
      - main

jobs:
  appium-tests:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v2

      - name: Run Appium Tests with Maven
        uses: ThangNguyen0495/execute-appium-android-test@v1.0.0
        with:
          java_version: '22'
          api_level: '35'
          node_version: '21'
          test_name: 'MyTestSuite'
          scripts: 'mvn test -DsuiteFile=testng.xml'
