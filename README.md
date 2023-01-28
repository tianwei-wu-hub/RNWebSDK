# FoxitPDFSDK for Web Example - React Native

This guide shows how to use this example.

### Prerequisites

- [FoxitPDFSDK for Web](https://developers.foxit.com/products/web/)
- [Android Studio](https://developer.android.com/studio)
- [XCode](https://developer.apple.com/xcode/)
- [Nodejs](https://nodejs.org/en/) and [NPM](https://www.npmjs.com)

## 搭建开发环境
参照react native官方文档：https://reactnative.dev/docs/environment-setup 搭建Android和iOS开发环境。

_Note:请选择“React Native CLI”的方式进行搭建，“Expo Go”为付费工具，不在本文讨论范围中。_

_Note:本文使用0.71.0版本的react-native和11.26.0版本的react-native-webview。_

## Clone the repository to any location:

```bash
git clone xxx.git FoxitPDFSDKForWebReactNativeExample
```

## 安装依赖

NPM,Android,iOS

### 安装NPM依赖

Navigate to `FoxitPDFSDKForWebReactNativeExample/`, and execute:

```bash
npm install
```

### 安装Android依赖

使用Android Studio打开目录FoxitPDFSDKForWebReactNativeExample/android，点击右上角gradle图标，安装依赖

### 安装iOS依赖

Navigate to `FoxitPDFSDKForWebReactNativeExample/ios`, and execute:

```bash
pod install
```

## 整合FoxitPDFSDK for Web

### 拷贝以下目录至FoxitPDFSDKForWebReactNativeExample/html/Web.bundle目录

- FoxitPDFSDKForWeb_x_x_x_Full/lib
- FoxitPDFSDKForWeb_x_x_x_Full/external

### 修改licenseSN和licenseKey

修改FoxitPDFSDKForWebReactNativeExample/html/index.html中licenseSN和licenseKey为FoxitPDFSDKForWeb_x_x_x_Full/examples/license-key.js中的值

## Runnning the example

- Android

1. 启动Metro打包服务，在RNWebSDK目录执行`npx react-native start`
2. 启动Android模拟器
3. 打包运行Android项目，在RNWebSDK目录执行`npx react-native run-android`

- iOS

1. 启动Metro打包服务，在RNWebSDK目录执行`npx react-native start`
2. 打包运行iOS项目，在RNWebSDK目录执行`npx react-native run-ios`
