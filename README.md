# FoxitPDFSDK for Web Example - React Native

This guide shows how to run this example.

## Prerequisites

- [FoxitPDFSDK for Web](https://developers.foxit.com/products/web/)
- [Android Studio](https://developer.android.com/studio) or [XCode](https://developer.apple.com/xcode/)

## Setting up the development environment
Follow the React Native docs to [setting up the development environment](https://reactnative.dev/docs/environment-setup). 

_Note: Please select the React Native document version 0.71.0 ._

_Note: Please select React Native CLI._

## Clone the repository to any location:

```bash
git clone xxx.git FoxitPDFSDKForWebReactNativeExample
```

## Installation dependencies

a. Nodejs dependencies

Navigate to `FoxitPDFSDKForWebReactNativeExample`, and execute:

```bash
npm install
```

b. Android dependencies

Navigate to `FoxitPDFSDKForWebReactNativeExample/android`, and execute:

```bash
./gradlew build
```

Execute "chmod +x gradlew" if don't have permission.

c. iOS dependencies

Navigate to `FoxitPDFSDKForWebReactNativeExample/ios`, and execute:

```bash
pod install
```

## Integrate FoxitPDFSDK for Web

1. Copy the following directories to `FoxitPDFSDKForWebReactNativeExample/html/Web.bundle` directory.

- FoxitPDFSDKForWeb_x_x_x_Full/lib
- FoxitPDFSDKForWeb_x_x_x_Full/external

2. Change the licenseSN and licenseKey.

Change the licenseSN and licenseKey values in `FoxitPDFSDKForWebReactNativeExample/html/index.html` to the values of file `FoxitPDFSDKForWeb_x_x_x_Full/examples/license-key.js`.

## Runnning the example

- Android

1. Start the Metro service, navigate to `FoxitPDFSDKForWebReactNativeExample`, and execute:
```bash
npx react-native start
```
2. Start Android Emulator.
3. In the new terminal, navigate to `FoxitPDFSDKForWebReactNativeExample`, and execute:
```bash
npx react-native run-android
```

- iOS

1. Start the Metro service, navigate to `FoxitPDFSDKForWebReactNativeExample`, and execute:
```bash
npx react-native start
```
2. In the new terminal, navigate to `FoxitPDFSDKForWebReactNativeExample`, and execute:
```bash
npx react-native run-ios
```
