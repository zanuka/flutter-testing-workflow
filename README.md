[![Build Status](https://travis-ci.org/zanuka/flutter-testing-workflow.svg?branch=master)](https://travis-ci.org/zanuka/flutter-testing-workflow)
[![codecov](https://codecov.io/gh/zanuka/flutter-testing-workflow/branch/master/graph/badge.svg)](https://codecov.io/gh/zanuka/flutter-testing-workflow)

# flutter testing workflow

- unit tests
- widget tests
- driver tests
- travis config
- codecov config

shout out to the [mmcc007/flutter_app](https://github.com/mmcc007/flutter_app) for the excellent travis config example

# unit / widget tests

    flutter tests --coverage

# driver tests

[Flutter Integration Testing Docs](https://flutter.io/docs/testing#integration-testing)

create a directory called `test_driver` in app root

`test_driver/main.dart` - enable extension and drive app

## running driver tests

    flutter drive --target=test_driver/main.dart
    

    
