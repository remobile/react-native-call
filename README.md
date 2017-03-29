# React Native Call (remobile)
A call phone number for react-native

## Installation
```sh
npm install @remobile/react-native-call --save
```
### Installation (iOS)
* Drag RCTCall.xcodeproj to your project on Xcode.
* Click on your main project file (the one that represents the .xcodeproj) select Build Phases and drag libRCTCall.a from the Products folder inside the RCTCall.xcodeproj.
* Look for Header Search Paths and make sure it contains both $(SRCROOT)/../../../react-native/React as recursive.

### Installation (Android)
```gradle
...
include ':react-native-call'
project(':react-native-call').projectDir = new File(settingsDir, '../node_modules/@remobile/react-native-call/android')
```

* In `android/app/build.gradle`

```gradle
...
dependencies {
    ...
    compile project(':react-native-call')
}
```

* register module (in MainApplication.java)

```java
......
import com.remobile.call.RCTCallPackage;  // <--- import

......

@Override
protected List<ReactPackage> getPackages() {
   ......
   new RCTCallPackage(),            // <------ add here
   ......
}

```

## Usage

### Example
```js
var React = require('react');
var ReactNative = require('react-native');
var {
    StyleSheet,
    View,
} = ReactNative;


var Button = require('@remobile/react-native-simple-button');
var Call = require('@remobile/react-native-call');

module.exports = React.createClass({
    callNumber() {
        Call.callNumber(()=>{
          }, ()=>{},
          "085186810083",
          true,
        );
    },
    render() {
        return (
            <View style={styles.container}>
                <Button onPress={this.callNumber}>
                    CallNumber
                </Button>
            </View>
        );
    },
});


var styles = StyleSheet.create({
    container: {
        flex: 1,
        justifyContent: 'space-around',
        alignItems: 'center',
        backgroundColor: 'transparent',
    }
});
```

### Method
* `callNumber` (success, failure, number, bypassAppChooser)
    * bypassAppChooser on support for android
