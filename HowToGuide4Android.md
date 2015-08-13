# Introduction #

This wiki page will works you through how to use this library building an Android application for Flickr.


# Details #

## Required Jars ##
In order for using this library on Android, you would need to download and put the following jars into the **libs** folder of your Android project.
  * SLF4J Android for logging: http://www.slf4j.org/android/

## OAuth ##
Currently Flickr supports OAuth 1.0a as defined at http://www.flickr.com/services/api/auth.oauth.html. This is required if your app intends to access any protected resources. Otherwise, OAuth is not required.

### Register a Callback URL ###
First of all, you should register a unique scheme for your app in the AndroidManifest.xml file like illustrated below. This scheme would be used as call back URL used later.

```xml

<?xml version="1.0" encoding="utf-8"?>
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
package="com.gmail.yourpackagename" >
...
<application android:name="FlickrViewerApplication" ...>
<activity android:name="FlickrViewerActivity" ...>
<intent-filter>
<action android:name="android.intent.action.VIEW" />
<category android:name="android.intent.category.DEFAULT" />
<category android:name="android.intent.category.BROWSABLE" />
<data android:scheme="{a unique scheme for your app}" />


Unknown end tag for &lt;/intent-filter&gt;




Unknown end tag for &lt;/activity&gt;




Unknown end tag for &lt;/application&gt;




Unknown end tag for &lt;/manifest&gt;


```

A more complete sample could be found at [here](http://code.google.com/p/flickrj-android/source/browse/flickrj-android-sample-android/AndroidManifest.xml).

### Request a Token and Redirect User for Authorization ###
Then you would need to ask Flickr for a request token, and redirect users to the generated Authentication URL.

```java

public void initialOauth() {
String callBackUrl = "your_scheme_defined_in_androidmanifest.xml";
Flickr f = new Flickr("api_key", "api_secret");
//get a request token from Flickr
OAuthToken oauthToken = f.getOAuthInterface().getRequestToken(callBackUrl);
//you should save the request token and token secret to a preference store for later use.
saveToken(oauthToken);

//build the Authentication URL with the required permission
URL oauthUrl = f.getOAuthInterface().buildAuthenticationUrl(
Permission.WRITE, oauthToken);

//redirect user to the genreated URL.
redirect(oauthUrl);
}
```

A real world sample could be found at [here](http://code.google.com/p/flickrj-android/source/browse/flickrj-android-sample-android/src/com/gmail/yuyang226/flickrj/sample/android/tasks/OAuthTask.java).

### Handle the OAuth Callback and Get Access Token ###
```java

public class FlickrViewerActivity extends Activity {
public void onResume() {
super.onResume();
Intent intent = getActivity().getIntent();
String scheme = intent.getScheme();

//the scheme should be same as the what you defined in the AndroidManifest.xml file
if (Constants.ID_SCHEME.equals(scheme)) {
Uri uri = intent.getData();
String query = uri.getQuery();
//the query format should be oauthToken=XXX&oauthVerifier=XXX
String[] data = query.split("&");
if (data != null && data.length == 2) {
String oauthToken = data[0].substring(data[0].indexOf("=") + 1);
String oauthVerifier = data[1].substring(data[1].indexOf("=") + 1);

//retrieve the stored request token secret in earlier step
String requrestTokenSecret = getRequestTokenSecret();
if (secret != null) {
Flickr f = new Flickr("api_key", "api_secret");
OAuthInterface oauthApi = f.getOAuthInterface();

//exchange for an AccessToken from Flickr
OAuth oauth = oauthApi.getAccessToken(oauthToken, requrestTokenSecret,
oauthVerifier);
User user = oauth.getUser();
OAuthToken token = oauth.getToken();
saveFlickrAuthToken(oauth);
}
}
}
}
}
```

A real world sample could be found at [here](http://code.google.com/p/flickrj-android/source/browse/flickrj-android-sample-android/src/com/gmail/yuyang226/flickrj/sample/android/FlickrjAndroidSampleActivity.java).

### Accessing Protected Resources ###
Finally you can set the oauth token when accessing any protected resources like private photos.

```java

Flickr f = new Flickr("api_key", "api_secret");
OAuth auth = new OAuth();
auth.setToken(new OAuthToken("access_token", "token_secret"));

//oauth token should always set to RequestContext if your app is multi-threading or multi users
RequestContext.getRequestContext().setOAuth(auth);
User user = f.getOAuthInterface().testLogin();
```

## Sample Project ##
I am currently building a small working sample for Android. In the meantime, you can check out a more complete sample at a sub project named **flickrj-android-sample-android** or http://code.google.com/p/flickr-viewer-for-honeycomb/.