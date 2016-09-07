# react-native-simpledialog-android
React Native Android module to use Android's AlertDialog - same idea of AlertIOS

[![npm version](http://img.shields.io/npm/v/react-native-simpledialog-android.svg?style=flat-square)](https://npmjs.org/package/react-native-simpledialog-android "View this project on npm")
[![npm downloads](http://img.shields.io/npm/dm/react-native-simpledialog-android.svg?style=flat-square)](https://npmjs.org/package/react-native-simpledialog-android "View this project on npm")
[![npm licence](http://img.shields.io/npm/l/react-native-simpledialog-android.svg?style=flat-square)](https://npmjs.org/package/react-native-simpledialog-android "View this project on npm")


### Installation

```bash
npm install react-native-simpledialog-android --save
```

### Add it to your android project

* In `android/settings.gradle`

```gradle
...
include ':RNSimpleAlertDialogModule', ':app'
project(':RNSimpleAlertDialogModule').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-simpledialog-android/android')
```

* In `android/app/build.gradle`

```gradle
...
dependencies {
    ...
    compile project(':RNSimpleAlertDialogModule')
}
```

* Register Module >= 0.17 && <= 0.29(in ```MainActivity.java```)
* NOTE: >= RN 29 split ```MainActivity.java``` into ```MainActivity.java``` and
  ```MainApplication.java```.  So make modifications below to ```MainApplication.java```

```java
import com.burnweb.rnsimplealertdialog.RNSimpleAlertDialogPackage;  // <--- import

public class MainApplication extends Application implements ReactApplication {
  ......

  @Override
  protected List<ReactPackage> getPackages() {
    return Arrays.<ReactPackage>asList(
            new MainReactPackage(),
            new RNSimpleAlertDialogPackage()); // <------ add this line to your MainApplication class
  }

  ......

}
```

## Usage
This module are very similar to [AlertIOS](https://facebook.github.io/react-native/docs/alertios.html) native module, and only works with **alert** method *(prompt method aren't implemented yet)*.

The main difference are in the way that you declare buttons. In Android you can declare **up to 3 buttons** and in this module you have to declare what **type** the button is.
A button can be **SimpleAlert.POSITIVE_BUTTON**, **SimpleAlert.NEGATIVE_BUTTON** or **SimpleAlert.NEUTRAL_BUTTON**.

## Example
```javascript
var SimpleAlert = require('react-native-simpledialog-android');

function _onPress(event) {
    console.log(event);
};

SimpleAlert.alert(
    'Please read me!',
    'Want a warning alert?', [
      { type: SimpleAlert.POSITIVE_BUTTON, text: 'Yes', onPress: _onPress },
      { type: SimpleAlert.NEGATIVE_BUTTON, text: 'No', onPress: _onPress },
      { type: SimpleAlert.NEUTRAL_BUTTON, text: 'Neutral', onPress: _onPress },
    ]
);
```

## License
MIT
