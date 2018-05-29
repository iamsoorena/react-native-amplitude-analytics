
# react-native-amplitude-analytics

[![npm version](https://badge.fury.io/js/react-native-amplitude-analytics.svg)](https://badge.fury.io/js/react-native-amplitude-analytics)

## Dependencies

`react-native` version `>0.40`

## Installation

`npm i react-native-amplitude-analytics --save`

#### iOS installation

##### Option 1 (link):

1. `react-native link react-native-amplitude-analytics`
2. Either
- add the following line to your "Podfile": `pod 'Amplitude-iOS', '~> 4.0.4'` and run `pod install`

or

- download the Amplitude-iOS sdk from [here](https://amplitude.zendesk.com/hc/en-us/articles/115002278527#installation) and add it to your project manually.
3. Run your project (`Cmd+R`)

#### Option 2 (Cocoapods only)
1. Add the following line to your "Podfile": `pod 'react-native-amplitude-analytics', path: '../node_modules/react-native-amplitude-analytics'`
2. run `pod install`
3. Run your project (`Cmd+R`)



#### Android Manual installation

1. Open up `android/app/src/main/java/[...]/MainApplication.java`
  - Add 

    ```java
    import com.sudoplz.reactnativeamplitudeanalytics.RNAmplitudeSDKPackage;
    ```

   to the imports at the top of the file.
   
  - Add 

    ```java
    new RNAmplitudeSDKPackage(MainApplication.this),
    ``` 

  to the list returned by the `getPackages()` method
  
2. Append the following lines to `android/settings.gradle`:

  	```gradle
  	include ':react-native-amplitude-analytics'
    project(':react-native-amplitude-analytics').projectDir = new File(rootProject.projectDir, '../node_modules/react-native-amplitude-analytics/android')
  	```
3. Insert the following lines inside the dependencies block in `android/app/build.gradle`:

  	```gradle
	compile 'com.amplitude:android-sdk:2.13.4' // native sdk of amplitude
    compile project(':react-native-amplitude-analytics') // our react-native module
  	```

4. Add permissions. If you haven't already, add the INTERNET permission to your manifest file:

  	```
  	<uses-permission android:name="android.permission.INTERNET" />
  	```

## Usage 

  ```javascript

  import RNAmplitude from 'react-native-amplitude-analytics';

  ```


### Example 

```javascript
class testApp extends Component {
  constructor() {
    super();
	 const amplitude = new RNAmplitude('Your Amplitude key');
	 
	 // log an event
	 amplitude.logEvent(eventName);
	 
	 // log an event with data
	 amplitude.logEvent(eventName, { foo: bar });
	 
	 // set the user id
	 amplitude.setUserId('1D32FS45');
	 
 	 // set user props
	 amplitude.setUserProperties({ hairColor: 'brown' });

         // sets whether or not to opt a user out logging
         amplitude.setOptOut(true);
	 
	 // log revenue
	 amplitude.logRevenue(productIdentifier, quantity, amount)
  }
  ...
}
```

there's also an example project [here](https://github.com/SudoPlz/react-native-amplitude-analytics/tree/master/Example).
