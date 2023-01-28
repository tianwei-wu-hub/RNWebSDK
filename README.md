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

NPM,Android,iOS

a. 安装NPM依赖

Navigate to `FoxitPDFSDKForWebReactNativeExample/`, and execute:

```bash
npm install
```

b. 安装Android依赖

使用Android Studio打开目录FoxitPDFSDKForWebReactNativeExample/android，点击右上角gradle图标，安装依赖

c. 安装iOS依赖

Navigate to `FoxitPDFSDKForWebReactNativeExample/ios`, and execute:

```bash
pod install
```

## 整合FoxitPDFSDK for Web

1. 拷贝以下目录至FoxitPDFSDKForWebReactNativeExample/html/Web.bundle目录

- FoxitPDFSDKForWeb_x_x_x_Full/lib
- FoxitPDFSDKForWeb_x_x_x_Full/external

2. 修改licenseSN和licenseKey

修改FoxitPDFSDKForWebReactNativeExample/html/index.html中licenseSN和licenseKey为FoxitPDFSDKForWeb_x_x_x_Full/examples/license-key.js中的值

## Runnning the example

- Android

1. 启动Metro打包服务，在RNWebSDK目录执行`npx react-native start`
2. 启动Android模拟器
3. 打包运行Android项目，在RNWebSDK目录执行`npx react-native run-android`

- iOS

1. 启动Metro打包服务，在RNWebSDK目录执行`npx react-native start`
2. 打包运行iOS项目，在RNWebSDK目录执行`npx react-native run-ios`
