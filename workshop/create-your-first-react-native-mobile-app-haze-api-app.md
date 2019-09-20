---
description: Your own Haze Air Pollution Index mobile app
---

# Create your first React Native mobile app - Haze API App

## Overview

In this workshop we will be developing a React Native mobile app using Expo. We will use an API \(Application Programming Interface\) as the input/resources/database for the mobile application. The app would consume the JSON resources provided by the API to create a presentable interface where the user can check the daily haze Air Pollution Index in their mobile devices.

* We will be using [Expo Snack](http://snack.expo.io) online editor as the main tools to create this application.
* We will need your iOS or Android phone installed with the[ Expo mobile app](https://expo.io/tools#client), so that the app can tested on your phone.

### Goals 

1. Understand the basic concept of React/React Native
2. Publish the app to a website or at least run it on your phone 

## Before you start

* At least some basic understanding of programming is needed, preferably in JavaScript as this is the main language used throughout this course

{% hint style="info" %}
Doesn't know anything about programming? No worries! Armed with just some common sense and a bit of patience you can go through this workshop as well. If you need any help you can just raise your hand or message me at [@joevo2](https://twitter.com/joevo2)
{% endhint %}

## Getting started

1. Let's fire up[ Expo Snack](https://snack.expo.io/) to get started.
2. We will be presented with `App.js` in the text editor area, and on the right you will see preview of your app. Where you can toggle between iOS, Android and Web. 
3. To run your phone you can toggle it to iOS/Android and press the "Run on your device" , then scan the QR code using the installed [Expo app ](https://expo.io/tools#client)on your phone. 
4. The top part consists all the imports, some are library installed using NPM which you can see in your `package.json` . Some are imported locally such as the `AssetExample` component. 
5. In the `render()` function is where we have HTML-like syntax called JSX where we can create the screen for the app. Component such as `Text` , `View` can be imported from `react native` as shown in line 2. The full list of component can be referred at the[ official React Native documentation](https://facebook.github.io/react-native/docs/activityindicator).
6. From line 27 onward we can see the various of styling that has been set, and used by the `View` component in line 14 as such `View style={styles.container}>` . The styling syntax is similar to that of CSS but camel cased. The full list of supported styling can be referred [here](https://github.com/vhpoet/react-native-styling-cheat-sheet). 

{% code-tabs %}
{% code-tabs-item title="App.js" %}
```jsx
import * as 
from 'react';
import { Text, View, StyleSheet } from 'react-native';
import Constants from 'expo-constants';

// You can import from local files
import AssetExample from './components/AssetExample';

// or any pure javascript modules available in npm
import { Card } from 'react-native-paper';

export default class App extends React.Component {
  render() {
    return (
      <View style={styles.container}>
        <Text style={styles.paragraph}>
          Change code in the editor and watch it change on your phone! 
          Save to get a shareable url.
        </Text>
        <Card>
          <AssetExample />
        </Card>
      </View>
    );
  }
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    paddingTop: Constants.statusBarHeight,
    backgroundColor: '#ecf0f1',
    padding: 8,
  },
  paragraph: {
    margin: 24,
    fontSize: 18,
    fontWeight: 'bold',
    textAlign: 'center',
  },
});

```
{% endcode-tabs-item %}
{% endcode-tabs %}

## What is React? 

## How do I manipulate data? 

setState 

form 

## How do I make an API call? 

{% hint style="info" %}
**What is JSON \(JavaScript Object Notation\)?**  
An open-standard file format that uses human-readable text to transmit data objects consisting of attribute–value pairs and array data types

{% code-tabs %}
{% code-tabs-item title="Sample AQI JSON response" %}
```javascript
{
  "status": "ok",
  "data": {
    "aqi": 150,

    "city": {
      "geo": [
        3.139003,
        101.686855
      ],
      "name": "Kuala Lumpur",
      "url": "https://aqicn.org/city/kuala-lumpur"
    },
    "time": {
      "s": "2019-09-19 17:00:00",
      "tz": "+08:00",
      "v": 1568912400
    }
  }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}
{% endhint %}

