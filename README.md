# GraalVM Native Image Toolchain

This GitHub Action sets up a collection of tools for building GraalVM Native Image applications, including

* GraalVM
* Native Image
* Developer Command Prompt for Microsoft Visual C++ (Windows only)

# Usage

Add the `GraalVM Native Image Toolchain Action` to your workflow and run your build tool of choice.

```yml
jobs:
  build:
    runs-on: ubuntu-lastest
    steps:
      - name: Check out repository
        uses: actions/checkout@v2
      - name: helpermethod/graalvm-native-image-toolchain@0.0.1
        with:
          graalvm-version: 21.2.0
          java-version: 11
      - name: Build
        run: ./mvnw --batch-mode verify 
```

Works especially well with build matrices.

```yml
jobs:
  build:
    runs-on: ${{ matrix.os }}
    strategy:
      matrix:
        os: os: [ubuntu-latest, macos-latest, windows-latest]
    steps:
      steps:
        - name: Check out repository
          uses: actions/checkout@v2
        - name: helpermethod/graalvm-native-image-toolchain@0.0.1
          with:
            graalvm-version: 21.2.0
            java-version: 11
        - name: Build
          run: ./mvnw --batch-mode verify
```
