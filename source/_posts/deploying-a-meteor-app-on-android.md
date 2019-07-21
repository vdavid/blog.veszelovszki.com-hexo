---
title: Deploying a meteor app on Android
date: 2015-12-01 15:03:00
comments: true
tags:
 - english
 - meteor
 - javascript
 - howto
categories:
 - programming
disqusIdentifier: M5AWeJD9ppiZ41V4kJo4
thumbnailImage: meteor-logo-280.png
coverImage: 
hidden: false
---
An old article from 2015, when I fiddled with Meteor on Android.
<!-- excerpt -->

### Audience

This post is for those who run Windows and want to deploy a Meteor app on Android.  
It took me about 5 hours to figure out how to do this, so I've decided to share my findings.  
I run Windows 10, and I have a free EC2 instance on Amazon AWS, which runs Amazon Linux.  
I use the latest Meteor version, which is 1.2.1.  

### Setting up the SDK

- You cannot build an Android (nor iOS) app on Windows. You need Mac OS or Linux.
- Use [Docker](http://docker.com/) to start a local virtual server, or use any Linux server you have access to. I used my Amazon EC2.
- Connect to your server with [PuTTY](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) or your favorite console app.
- [Download](http://developer.android.com/sdk/index.html#Other) an Android SDK to your home directory ([Hint](http://askubuntu.com/questions/207265/how-to-download-a-file-from-a-website-via-terminal))
- Unpack the downloaded file in your home directory ([Hint](http://www.cyberciti.biz/faq/unpack-tgz-linux-command-line/))
- Add your unzipped android SDK's folder "tools" (~/android-sdk-linux/tools/) to the PATH so that its executables are accessible everywhere ([Hint](http://unix.stackexchange.com/questions/26047/how-to-correctly-add-a-path-to-path))
- Set your ANDROID_HOME environment variable to "~/android-sdk-linux/"Command:  
    `export ANDROID_HOME=~/android-sdk-linux/`
- Download the proper Android SDK version to build your app ([Hint](http://stackoverflow.com/questions/17963508/how-to-install-android-sdk-build-tools-on-the-command-line)). I used the version advised by Meteor, API 22.  
  I used this command:  
  `android update sdk -u -a -t 7,27`  
  To install these packages:
  - 7- Android SDK Build-tools, revision 22.0.1
  - 27- SDK Platform Android 5.1.1, API 22, revision 2

### Building the app

- Ensure that your app is deployed on a server (e.g. using `meteor deploy your-app.meteor.com`)
- Ensure there is a mobile-config.js file in your project root ([Hint](https://github.com/meteor/meteor/wiki/How-to-submit-your-Android-app-to-Play-Store)).
- Ensure that the referenced icons are present. I just downloaded some sample icons from [here](http://tekeye.biz/2013/android-icon-size) and added them as
`{application root}/resources/android/icons/*.png`

- Copy/upload your Meteor app to a folder on the server, or check it out from Github.
- Go to your project root directory.
- Run `meteor add-platform android --verbose`

- If there was an error in the previous step, try to resolve it through Google, and retry any time after running `meteor remove-platform android`

- Follow the directions [here](https://github.com/meteor/meteor/wiki/How-to-submit-your-Android-app-to-Play-Store) to build and sign your app, it's really not difficult.
- If everything went well, you have got an "android/release-unsigned.apk" file in your build folder.

### Deployment

- Finally, deployment. Connect your Android phone via USB, and put it in developer mode.
- Install the Android SDK on your Windows too. Just install Android Studio, it's a huge download but it solves all your problems. Or if you have IntelliJ IDEA, just download the Android plugins. There are plenty of instructions on how to do this. So from now on I assume you have the Android SDK on your Windows.
- Download the signed APK from your server and run `adb install {path-to-your-downloaded-apk}`
- Your app is now installed on your phone.

I hope I helped. Please leave comments if something does not go right for you and I will fo my best to update the instructions accordingly.
