# FoxitPDFSDK for Web Example - React Native

These guides are divided into two parts:

- [Part 1: How to run this example](#part-1-how-to-run-this-example)
- [Part 2: Use FoxitPDFSDK for Web in React Native](#part-2-use-foxitpdfsdk-for-web-in-react-native)

## Prerequisites

- [FoxitPDFSDK for Web](https://developers.foxit.com/products/web/)
- [Android Studio](https://developer.android.com/studio) or [XCode](https://developer.apple.com/xcode/)

## System requirements

- react-native >= 0.71.0 and use React Native CLI not Expo Go.
- react-native-webview >= 11.26.0

## Part 1: How to run this example

### 1. Setting up the development environment

Follow the React Native docs to [setting up the development environment](https://reactnative.dev/docs/environment-setup). 

### 2. Installation dependencies

Assume you clone project into the `RNWebSDKExample` directory.

#### a. Nodejs dependencies

Navigate to `RNWebSDKExample`, and execute:

```bash
npm install
```

#### b. Android dependencies

Navigate to `RNWebSDKExample/android`, and execute:

```bash
./gradlew build
```

Execute "chmod +x gradlew" if you don't have permission.

#### c. iOS dependencies

Navigate to `RNWebSDKExample/ios`, and execute:

```bash
pod install
```

### 3. Integrate FoxitPDFSDK for Web

#### 3.1. Copy the following directories to `RNWebSDKExample/html/Web.bundle` directory

- FoxitPDFSDKForWeb_x_x_x_Full/lib
- FoxitPDFSDKForWeb_x_x_x_Full/external

#### 3.2. Change the licenseSN and licenseKey

Change the licenseSN and licenseKey values in `RNWebSDKExample/html/Web.bundle/index.html` to the values of file `FoxitPDFSDKForWeb_x_x_x_Full/examples/license-key.js`.

### 4. Running the example

#### Android

1. Start the Metro service, navigate to `RNWebSDKExample`, and execute:
```bash
npx react-native start
```
2. Start Android Emulator.
3. Run app, in the new terminal, navigate to `RNWebSDKExample`, and execute:
```bash
npx react-native run-android
```

Wait a while, your app will install and launch in Android emulator automatically.

#### iOS

1. Start the Metro service, navigate to `RNWebSDKExample`, and execute:
```bash
npx react-native start
```
2. Run app, in the new terminal, navigate to `RNWebSDKExample`, and execute:
```bash
npx react-native run-ios
```

Wait a while, your app will install and launch in iOS simulator automatically.

## Part 2: Use FoxitPDFSDK for Web in React Native

### 1. Setting up the development environment

Follow the React Native docs to [setting up the development environment](https://reactnative.dev/docs/environment-setup).

Assume you create project named `RNWebSDKExample`.

### 2. Integrate FoxitPDFSDK for Web

#### 2.1 Create a Web resource directory

1. Create a new `html` directory in the `RNWebSDKExample` directory and a new `Web.bundle` directory in the `html` directory.
2. Copy the following directories to `RNWebSDKExample/html/Web.bundle` directory.
- FoxitPDFSDKForWeb_x_x_x_Full/lib
- FoxitPDFSDKForWeb_x_x_x_Full/external
3. Copy the index.html file to the `RNWebSDKExample/html/Web.bundle` directory.
```html
<html>
<head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width,initial-scale=1">
    <link rel="stylesheet" type="text/css" href="./lib/PDFViewCtrl.css">
</head>
<body>
<input type="file" name="file" id="file" accept=".pdf">
<div style="width: 100%; height: 500px; overflow: auto;"><div id="pdf-viewer"></div></div>
 
<script src="./lib/PDFViewCtrl.full.js"></script>
<script>
    var licenseSN = 'xxx';
    var licenseKey = 'xxx';
 
    var PDFViewer = PDFViewCtrl.PDFViewer;
    var pdfViewer = new PDFViewer({
        libPath: './lib',
        jr: {
            licenseSN: licenseSN,
            licenseKey: licenseKey,
        },
        customs: {
            ScrollWrap: PDFViewCtrl.CustomScrollWrap
        }
    });
    pdfViewer.init('#pdf-viewer');
 
    document.getElementById('file').onchange = function (e) {
        if (!this.value) {
            return;
        }
        pdfViewer.openPDFByFile(e.target.files[0]);
        this.value = '';
    };
</script>
</body>
</html>
```
4. Change the licenseSN and licenseKey values in `RNWebSDKExample/html/Web.bundle/index.html` to the values of file `FoxitPDFSDKForWeb_x_x_x_Full/examples/license-key.js`.

#### 2.2 Set up Web resource directory

##### Android

1. Open the directory `RNWebSDKExample/android` using Android Studio.
2. Change `RNWebSDKExample/android/app/build.gradle`.
```diff
// ...
android {
    // ...
+    sourceSets {
+        main {
+            assets.srcDirs = ['src/main/assets', '../../html']
+        }
+    }
}
```

##### iOS

1. Open `RNWebSDKExample/ios/RNWebSDK.xcworkspace` with XCode.
2. Expand the left directory tree `RNWebSDKExample/RNWebSDKExample`, drag and drop `RNWebSDKExample/html/Web.bundle` to the directory tree `RNWebSDKExample/RNWebSDKExample`, in the window that pops up, do not check "Copy items if needed" and click "Finish" button.

#### 2.3 Add react-native-webview dependency

Navigate to `RNWebSDKExample`, and execute:

```bash
npm i react-native-webview
```

The official documentation explains this in detail: https://github.com/react-native-webview/react-native-webview/blob/master/docs/Getting-Started.md

#### 2.4 Use webview to load and render the FoxitPDFSDK for Web

There are two ways to load a Web page in webview, one is load a URL like this:

```js
<WebView
    source={{uri: 'https://www.xxx.com'}}
    originWhitelist={['*']}
/>
```

the other is load local Web resources, we will use this method below.

1. Create the `src` directory in the `RNWebSDKExample` directory and add the `App.tsx` file to the `src` directory.

```jsx
import React from 'react';
import {
  Platform,
  SafeAreaView,
  StatusBar,
  View
} from 'react-native';
import { WebView } from 'react-native-webview';
 
function App(): JSX.Element {
 
  const sourceUri = (Platform.OS === 'android' ? 'file:///android_asset/' : '') + 'Web.bundle/index.html';
 
  return (
    <SafeAreaView>
      <StatusBar/>
      <View style={{width: '100%', height: '100%'}}>
        <WebView
          source={{uri: sourceUri}}
          originWhitelist={['*']}
          allowFileAccessFromFileURLs={true}
          allowUniversalAccessFromFileURLs={true}
          allowFileAccess={true}
        />
      </View>
    </SafeAreaView>
  );
}
 
export default App;
```

2. Change `RNWebSDKExample/index.js`

```diff
import {AppRegistry} from 'react-native';
- import App from './App';
+ import App from './src/App';
import {name as appName} from './app.json';
 
AppRegistry.registerComponent(appName, () => App);
```

#### 2.5 Running the project

##### Android

1. Start the Metro service, navigate to `RNWebSDKExample`, and execute:
```bash
npx react-native start
```
2. Start Android Emulator.
3. Run app, in the new terminal, navigate to `RNWebSDKExample`, and execute:
```bash
npx react-native run-android
```

Wait a while, your app will install and launch in Android emulator automatically.

##### iOS

1. Start the Metro service, navigate to `RNWebSDKExample`, and execute:
```bash
npx react-native start
```
2. Run app, in the new terminal, navigate to `RNWebSDKExample`, and execute:
```bash
npx react-native run-ios
```

Wait a while, your app will install and launch in iOS simulator automatically.

