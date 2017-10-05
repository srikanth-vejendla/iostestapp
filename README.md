## Native iOS Automation of Depoza application with XCTest and ScreenObject.

### A few examples of xcodebuild commands:

Shows a list of devices:
```
$ xcrun instruments -s
```
Create build for testing:
```
$ xcodebuild -workspace Depoza.xcworkspace -scheme Depoza -sdk iphonesimulator -destination 'platform=iOS Simulator,id=C1E29D4F-EC42-49CB-A464-2B98D3A5A1AA' -derivedDataPath ./build build-for-testing
```
Test the build from previous command and pipe reports to xcprety. 
```
$ xcodebuild -xctestrun ./build/Build/Products/Depoza_iphonesimulator10.3-x86_64.xctestrun -destination 'platform=iOS Simulator, id=C1E29D4F-EC42-49CB-A464-2B98D3A5A1AA' test-without-building | xcpretty -r junit -r html
```

### Keep in mind

Don't forget to set up simulator/device properly before testing (tick "Connect Hardware Keyboard", turn off "Auto-Capitalization" and "Auto-Correction").

Project uses CocoaPods, so launch 'Depoza.xcworkspace' instead of 'Depoza.xcodeproj'.

Test schemes named after test suites and contain corresponding tests ('Depoza' scheme, on the other hand, includes all of the tests).

Fastlane's snapshot is implemented (see 'fastlane/Snapfile' for more information).