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
4. Referring to the code below, the top part consists all the imports, which consists all the library installed using NPM which you can see in your `package.json` . The rest are imported from other local file such as the `AssetExample` component. 
5. In the `render()` function is where we have HTML-like syntax called JSX where we can create the user interface for the app. Component such as `Text` , `View` can be imported from `react native` as shown in line 2. The full list of component can be referred at the[ official React Native documentation](https://facebook.github.io/react-native/docs/activityindicator).
6. From line 27 onward we can see the various of styling that has been set, and used by the `View` component in line 14 as such `View style={styles.container}>` . The styling syntax is similar to that of CSS but camel cased. The full list of supported styling can be referred [here](https://github.com/vhpoet/react-native-styling-cheat-sheet). 

{% code-tabs %}
{% code-tabs-item title="App.js" %}
```jsx
import * as from 'react';
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

## What is React? What about React Native?

> React is a JavaScript library for building user interfaces. It is maintained by Facebook and a community of individual developers and companies. React can be used as a base in the development of single-page or mobile applications, as it is optimal for fetching rapidly changing data that needs to be recorded

In layman term, we can use React to build interactive interface where we can manipulate the data on the screen, fetch data from database etc. 

In this workshop we will be using React Native instead React. React Native works the same as React but instead of using `div` and dealing with HTML, we would use React Native component like `View` and dealing with mobile app libraries.

The added benefit of using React Native is that instead of using Swift and Kotlin/Java to develop iOS and Android app, we could use JavaScript instead where it will be compiled by React Native into the respective code.

## How do I manipulate data? 

### State

React state allow us update a value efficiently in HTML DOM. As shown in the code below

{% code-tabs %}
{% code-tabs-item title="App.js" %}
```jsx
export default class App extends React.Component {
  state = {
    text: 'Testing',
  };

  onChangeText = incomingText => {
    this.setState({ text: incomingText });
  };

  render() {
    return (
      <View style={styles.container}>
        <Text style={styles.paragraph}>{this.state.text}</Text>
        <TextInput
          style={{ height: 40, borderColor: 'gray', borderWidth: 1 }}
          onChangeText={text => this.onChangeText(text)}
        />
      </View>
    )
  }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Props

Props allow to pass value or even function to component we created. 

{% code-tabs %}
{% code-tabs-item title="App.js" %}
```jsx
class MyComponent extends React.Component { 
  render() {
    return (
      <View>
        <Text>{this.props.text}</Text>
      </View>
    )
  }
}

export default class App extends React.Component 
  render() {
    return (
      <View style={styles.container}>
        <MyComponent text={new Date().toLocaleDateString()} />
      </View>
    );
  }
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## How do I make an API \(Application Programming Inteface\) call? 

### Register AQI API 

1. You will need to register an account [here](https://aqicn.org/data-platform/token/#/) first to get access to the API
2. You should receive a confirmation email with instruction on making a simple API call with your token
3. You should be presented with a link as shown [`https://api.waqi.info/feed/kualalumpur/?token=yourTokenHere`](https://api.waqi.info/feed/beijing/?token=19833cdd959dbedc59e4fa3ceb1bfdfd0f7cd5c6) where you can get a JSON response.
4. [Here](https://aqicn.org/json-api/doc/) is the full list of API you can give it a try.

{% hint style="info" %}
**Token** is use to uniquely identify you and your application where usage will be recorded for analytics, security and billing purpose.
{% endhint %}

{% hint style="info" %}
**JSON \(JavaScript Object Notation\)**  
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

### Getting the data

To make an API call we would be using [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) which is built in and also commonly being used in modern browser.

{% code-tabs %}
{% code-tabs-item title="App.js" %}
```jsx
export default class App extends React.Component {
  state = {
    aqi: 0,
    location: '',
  };

  componentDidMount() {
    const location = 'kualalumpur'
    const token = 'yourOwnTaken'
    fetch(
      `https://api.waqi.info/feed/${location}/?token=${token}`
    )
      .then(res => res.json())
      .then(fetchedData => {
        this.setState({
          location: fetchedData.data.city.name,
          aqi: fetchedData.data.aqi,
        });
      });
  }

  render() {
    return (
      <View style={styles.container}>
        <Text style={styles.paragraph}>{this.state.text}</Text>

        <Text>{this.state.aqi}</Text>
        <Text>{this.state.location}</Text>
        
      </View>
    );
  }
}

```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Presenting the data 

#### Flex

In React Native we will be using Flex to layout our UI. Here's the [official documentation](https://facebook.github.io/react-native/docs/flexbox) where you could learn how to position any item anywhere with ease. 

What you learnt here is applicable on both React Native development as well as web development.

#### Presenting the data 

In this workshop we will be using a third party library called [react-native-paper](https://callstack.github.io/react-native-paper/card.html) where it provide us with Material Designed style component where we could present our data in a modern and presentable fashion.

1. Try to have a concept of the user interface, you can sketch out your own or refer to other application. You can have a look at [dribbble](https://dribbble.com/) for app design inspiration. Here's an [example](https://apps.apple.com/us/app/airvisual-air-quality-forecast/id1048912974) of a pretty good UI for have app. Feel free to search up and draft up your simple UI.
2. After having your own concept of UI, try to create the component that are required in Snack Expo. 

{% hint style="info" %}
**Icons**

Expo have a built in set of open source icon. Here's the [directory](https://expo.github.io/vector-icons/) for the full list of icon. Below we have an example on how to implement it.

```jsx
import { Ionicons } from '@expo/vector-icons';

export default class IconExample extends React.Component {
  render() {
    return (
      <Ionicons name="md-checkmark-circle" size={32} color="green" />
    );
  }
}
```

Here's the [official documentation](https://docs.expo.io/versions/latest/guides/icons/) from expo for more details 
{% endhint %}

## Workshop Evaluation

Kindly fill up this [short survey](https://forms.gle/31dLHMfPog4kUGn38) so that we could further improve 😊

