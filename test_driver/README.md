# Writing / Running Integration tests

## Use flutter driver

  As per [Flutter docs](https://flutter.io/docs/testing#integration-testing), write 2 files;

  1. functionality to be tested

    test_driver/main.dart

  2. the test steps
  
    test_driver/main_test.dart

  3. run the test driver

    flutter drive --target=test_driver/main.dart

## Use Observatory and Hot Reload

  As per [Medium Article](https://medium.com/flutter-community/hot-reload-for-flutter-integration-tests-e0478b63bd54)

### (terminal window 1)

  **Start App with Observatory port specified**
  
    flutter run --observatory-port 8888 test_driver/main.dart

### (terminal window 2)

  **Export VM_SERVICE_URL**

    export VM_SERVICE_URL=http:127.0.0.1:8888

  **Run**
  
    dart test_driver/main_test.dart