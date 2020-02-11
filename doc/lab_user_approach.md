---
layout: post
title:  "Lab 1 - ota"
categories: [lab]
tags: [setup]
excerpt_separator: <!--more-->
permalink: /lab/lab-1
name: /lab/lab-1.html
---
# User Credential approach 1 Lab

In this lab, we will create a demo to provision personal user credential and Wi-Fi credential to device by android app once the device is powered at first time.


## Solution Architecture 

The solution architect would be separated into two part: (1) Get User Credential by Android app. (2) Android app provision the user credential to device.
(1)  Get User Credential by Android app：
![Device_certificate_creation.png](../pics/lab1/Device_certificate_creation.png) (2) Android app provision the user credential to device.
[Image: Android app provision.png]
## Prerequisite

1. This demo take Ameba Z2 as reference board, which have to build code by IAR.
2. An android Phone with Android 6 at least to support the AWS android SDK.
3. Download [Android Studio](https://developer.android.com/studio) and Android app code from:
4. Download Amazon FreeRTOS code which support approach 1 from:

## Step 1. - Use AWS Cloudformation to deploy your AWS Service configuration related to this demo.



## Step 2. - Configure, build, and install the android app.

1. Fill in app/src/main/java/com/amazonaws/youruserpools/AppHelper.java with the userPoolId, clientId, and clientSecret.
    1. check these information in your AWS Cognito Service:
    2. [Image: image.png]
    3. Fill in these information at this location:
    4. [Image: image.png]
2. Build and app and install it to the Android Phone.



## Step 3. - Build and Run the Amazon FreeRTOS approach 1 Project.

1. Fill in Soft AP SSID and password in amazon-freertos\demos\realtek\amebaz2\common\config_files\aws_wifi_config.h
2. [Image: image.png]
3. Fill in your endpoint information in amazon-freertos\demos\common\include\aws_clientcredential.h
4. [Image: image.png]
5. Build and flash to the device by IAR IDE, then reset the device to let it enter SoftAP mode.
6. [Image: image.png]

## Step 4. - Use the android app to get the user credential from AWS Service.

1. Log in the App.
2. [Image: image.png]
3. Go to “cert Provision” page and use the UID (Device ID) to get the user credential from AWS Service (push the RE-GENKEY). 
4. [Image: image.png]

[Image: image.png]
## Step 5. - Go to STEP 2 Page to fill in the Wi-Fi credential information which you want the device connect to, then push the “SETUP WIFI CONFIG“.

[Image: image.png]
## Step 6. - Reset the device to start to the Soft AP mode of the device, then use android app setting to connect to it.

Use the following button to reset the device.
[Image: image.png]
Then it will start Soft AP mode with previous Soft AP setting in Step 3, use android default app to connect to it.
[Image: Screenshot_20200210-141134.jpg]


## Step 7. - Go to page 3 (app STEP 3 page) to push the button to provision the user credential.

Use the button “CONNECT TO PROVISION” to connect to Soft AP, it will start provisioning once it connect to the Soft AP.
[Image: Screenshot_20200211-113458.jpg]
There will be a pop-up a message to show the provision result.

[Image: Screenshot_20200211-113455.jpg]
**Notice: There is a timeout in device soft AP started after android app connecting to it. If time’s up with no provision, then you need to push the reset button to restart the soft AP process. You can configure this timeout here:**
[Image: image.png]

## Step 8. - Check the user credential work or not. (By AWS IoT Core Test)

Resetting the device to let it connect to designated  WiFi SSID and send publish message to IoT Core.


