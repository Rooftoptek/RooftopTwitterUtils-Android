# RooftopTwitterUtils-Android

A library that gives you access to the Rooftop cloud platform from your Android app with Twitter authorisation. For more information about Rooftop and its features, see the website and getting started.

## Download

To download SDK with gradle use the next tips.

<b> Step 1: </b>

Set the url to download the sdk in top-level (project-level) build.gradle file

```groovy
allprojects {
  repositories {
    ***
    maven { url 'https://raw.githubusercontent.com/Rooftoptek/Rooftop-SDK-Android/<release name>/releases/' }
    maven { url 'https://raw.githubusercontent.com/Rooftoptek/RooftopTwitterUtils-Android/<release name>/releases/' }
}
```

Url example for release 0.5.0:

```groovy
maven { url 'https://raw.githubusercontent.com/Rooftoptek/RooftopTwitterUtils-Android/0.5.0/releases/' }
```

<b> Step 2: </b>

Set the dependency of the "RooftopTwitterUtils" in the build.gradle file of the main module

```groovy
dependencies {
  ***
  compile(group: 'io.rftp', name: 'rooftoptwitterutils', version: '<release name>')
}
```

## Initialisation

To initialize SDK use the next tips.

<b> Step 1: </b>

Set android minSdkVersion not less than 15

<b> Step 2: </b>

Configure AndroidManifest.xml file of the main project:

  A. Set the permissions:
  
```groovy
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```

  B. Set rooftop credentials like meta-data in "application" section.

  B0. Modify AndroidManifest.xml:
  
```groovy
<application
***>
***
  <meta-data
    android:name="io.rftp.APPLICATION_ID"
    android:value="@string/rooftop_app_id" />
  <meta-data
    android:name="io.rftp.IDENTITY_POOL_ID"
    android:value="@string/rooftop_identity_pool_id" />
  <meta-data
    android:name="io.rftp.CLIENT_KEY"
    android:value="@string/rooftop_client_key" />
  <meta-data
    android:name="com.twitter.sdk.ConsumerKey"
    android:value="@string/twitter_app_key"/>
  <meta-data
    android:name="com.twitter.sdk.ConsumerSecret"
    android:value="@string/twitter_app_secret"/>
</application>
```

  B1. Put your credentials in strings.xml:

```groovy
<resources>
  ***
  <string name="rooftop_app_id">xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx</string>
  <string name="rooftop_identity_pool_id">xx-xxxx-x:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx</string>
  <string name="rooftop_client_key">xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx</string>
  <string name="twitter_app_key">xxxxxxxxxxxxxxxxxxxxxxxxx</string>
  <string name="twitter_app_secret">xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx</string>
</resources>
```

<b> Step 3: </b>

Call Rooftop.initialize(*) in onCreate(*) method of the Application class of the project

```java
public class MyApplication extends Application {
  @Override
  public void onCreate() {
    super.onCreate();
    ***
    Rooftop.initialize(this);
    RooftopTwitterUtils.initialize(this);
  }
}
```

<i> If you don't have your own Application class, create one. Specify usage of your MyApplication class in AndroidManifest-file:</i>

```groovy
<application
  ***
  android:name=".MyApplication">
    ***
</application>
```


## Basic API calls

<b> Login with Twitter </b>

Call corresponding login method from RooftopTwitterUtils SDK

```java
RooftopTwitterUtils.logIn(MainActivity.this, null);
```

<b> Logout with Twitter </b>

```java
RTUser.logOutInBackground();
```

For more information about Basic Rooftop API calls, see the website and getting started.

## License

```groovy
Copyright (c) 2016-present, RFTP Technologies Ltd.
All rights reserved.

```
