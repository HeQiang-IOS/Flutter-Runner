# Flutter Runner

`flutter` as in Github Actions.

## Usage examples

This example first cleans any stale build, gets and updates the dependencies with `flutter pub get` and then
builds a release apk to run on all mobile devices(android) and runs the flutter tests in parallel.

```
action.yml
name: 'Flutter Runner'
description: 'Github action for apk building for flutter apps.'
runs:
  using: 'docker'
  image: 'Dockerfile'
  ---------------------------------------
main.yml
on: push
name: cleans, build and test app (mobile - android)
jobs:
  build:
    name: install dependencies
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@master

    - name: clean stale build and cache
      uses: ./action
      with:
        args: clean

    - name: install dependencies
      uses: ./action
      with:
        args: pub get

    - name: build apk
      uses: ./action
      with:
        args: build apk --release
```
