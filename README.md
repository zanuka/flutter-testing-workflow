[![Build Status](https://travis-ci.org/zanuka/flutter-testing-workflow.svg?branch=master)](https://travis-ci.org/zanuka/flutter-testing-workflow)
[![codecov](https://codecov.io/gh/zanuka/flutter-testing-workflow/branch/master/graph/badge.svg)](https://codecov.io/gh/zanuka/flutter-testing-workflow)

# flutter testing workflow

- unit tests
- widget tests
- integration tests
- travis config
- codecov config

shout out to the [mmcc007/flutter_app](https://github.com/mmcc007/flutter_app) for the excellent travis config example

# unit / widget tests

    flutter tests --coverage

# integration tests

[Flutter Integration Testing Docs](https://flutter.io/docs/testing#integration-testing)

create a directory called `test_driver` in app root

`test_driver/main.dart` - enable extension and drive app

```// This line imports the extension
   import 'package:flutter_driver/driver_extension.dart';
   import 'package:flutter_flow/main.dart' as app;
   
   void main() {
     // Enable integration testing with the Flutter Driver extension.
     // See https://flutter.io/testing/ for more info.
     // This line enables the extension
     enableFlutterDriverExtension();
     // Call the `main()` of your app or call `runApp` with whatever widget
     // you are interested in testing.
     app.main();
   }
```
  
`test_driver/main_test.dart` - integration tests

```// This is a basic Flutter Driver test for the application. A Flutter Driver
   // test is an end-to-end test that "drives" your application from another
   // process or even from another computer. If you are familiar with
   // Selenium/WebDriver for web, Espresso for Android or UI Automation for iOS,
   // this is simply Flutter's version of that.
   
   import 'package:flutter_driver/flutter_driver.dart';
   import 'package:test/test.dart';
   
   void main() {
     group('end-to-end test', () {
       FlutterDriver driver;
   
       setUpAll(() async {
         // Connect to a running Flutter application instance.
         driver = await FlutterDriver.connect(
           timeoutMultiplier: 4,
           printCommunication: true,
         );
       });
   
       tearDownAll(() async {
         if (driver != null) driver.close();
       });
   
       test('tap on the floating action button; verify counter', () async {
         // Finds the floating action button (fab) to tap on
         SerializableFinder fab = find.byTooltip('Increment');
   
         // Wait for the floating action button to appear
         await driver.waitFor(fab);
   
         // Tap on the fab
         await driver.tap(fab);
   
         // Wait for text to change to the desired value
         await driver.waitFor(find.text('1'));
       });
     });
   }
```

## running integration tests

    flutter drive --target=test_driver/main.dart
    

    