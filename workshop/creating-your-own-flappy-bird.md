---
description: 'On iOS, Android and Web'
---

# Creating your own Flappy Bird

{% hint style="info" %}
Due to time constraint we would not conduct this workshop today, but instead you can give this a try at your own time and do message or tweet me at  [@joevo2](https://twitter.com/joevo2) if you faced any issue.
{% endhint %}

## Before you start

* At least some basic understanding of programming is needed, preferably in JavaScript as this is the main language used throughout this course

_PS: But no worries, armed with just common sense and a bit of patience you can go through this workshop as well. If you need any help you can just raise your hand or message me at_ [_@joevo2_](https://twitter.com/joevo2)\_\_

## Goals 

1. Create your own game using Expo + PixiJS
2. Publish the app to a website or at least run it on your phone 

_**Extended**  
Export the Expo Snack project,_ [_run it locally_](https://expo.io/learn) _with Expo, initialise the project with Git and push it to your own GitHub repository so that you can showcase to the world what you've done and brag during interview :D_ 

## Overview

* We will be using [Expo Snack](http://snack.expo.io) online editor as the main tools to create this application.
* We will need your iOS or Android phone installed with the[ Expo mobile app](https://expo.io/tools#client), so that the app can tested on your phone as Three.js cannot run in the Expo Snack web environment.
* ~~Most of the workshop content will be based off this~~ [~~official tutorial~~](https://docs.expo.io/versions/v31.0.0/tutorials/create-floatyplane-game/) ~~written by~~ [~~@Baconbrix~~](https://twitter.com/Baconbrix)~~. Do give him a tweet of appreciation~~. _We will be using this_[ _source code_](https://github.com/EvanBacon/react-flappy-bird) _instead because it is more up to date._

_**Extended**   
You can download the source code with Expo Snack and run it on your local machine, push to GitHub and have your own production build of the app._

## Getting started

Let's fire up [Expo Snack](http://snack.expo.io) and clone our first repository by clicking the ... icon and click import git repository.

![](../.gitbook/assets/import-git-repo.PNG)

* Paste this git repository link [`https://github.com/EvanBacon/react-flappy-bird`](https://github.com/EvanBacon/react-flappy-bird) and press the import button.
* Press the add button on the lower left corner as shown below to add the PixiJS library into the project.

![](../.gitbook/assets/add-pixi-to-package.PNG)

* On the right panel you can press Run on your device and scan the QR code with the Expo app on your iOS/Android phone

{% hint style="info" %}
This guide is still a work in progress, do explore around the code and tweak around the value to understand how all the moving part works in the app.
{% endhint %}

