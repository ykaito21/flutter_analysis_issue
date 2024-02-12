# Flutter Analysis Issue Reproduction

This repository contains a minimal Flutter project set up to reproduce an issue where adding `custom_lint` to `pubspec.yaml` causes the Dart analyzer in Visual Studio Code to run indefinitely without completing.

## Issue Description

After adding the `custom_lint` plugin under the `analyzer` section in `analysis_options.yaml` and adding `custom_lint` to `dev_dependencies` in `pubspec.yaml`, the Dart analyzer in Visual Studio Code starts analyzing the code but never finishes. This issue occurs even without making any changes to the codebase.

## Steps to Reproduce

1. Clone this repository.
   ```
   git clone https://github.com/ykaito21/flutter_analysis_issue.git
   ```
2. Open the cloned repository in Visual Studio Code.
3. Ensure you have the Dart and Flutter extensions installed in Visual Studio Code.
4. Open the `pubspec.yaml` and run `flutter pub get` to fetch the dependencies.
5. Observe the Dart analyzer behavior in Visual Studio Code. The analyzer starts but does not complete, and memory usage may increase over time.

## Expected Behavior

The Dart analyzer should complete the analysis of the project files without getting stuck or causing excessive memory usage.

This issue seems to occur only when `custom_lint` is added to the project. Removing `custom_lint` from `analysis_options.yaml` resolves the issue, suggesting a potential problem with the interaction between `custom_lint`, the Dart analyzer, and Visual Studio Code.

## Environment Setup

This example was created with the following command:

```
flutter create repro_example
```

Then `custom_lint: ^0.6.0` was added to `dev_dependencies` in `pubspec.yaml`, and the `custom_lint` plugin was included under the `analyzer` section in `analysis_options.yaml`.

For any further details or updates on this issue, please refer to the corresponding issue threads on the [Dart](https://github.com/dart-lang/sdk/issues/54883) and [custom_lint](https://github.com/invertase/dart_custom_lint/issues/226) repositories.