

# Introduction #
This is a Java API which wraps the REST-based Flickr API
(information available at http://www.flickr.com/services/api/), which promises better support for Android and Google App Engine.

It is a new library built on top of the <a href='http://flickrj.sourceforge.net/'>FlickrJ API</a>.

## What We Provide ##
It provides the following changes that compared with the original FlickrJ:
  * Java5 Syntax. The lack of support for the Java 5 syntax in FlickrJ has caused a lot of WARNING, and not leverage the latest JDK features such as Generics.
  * Support for Android and GAE. The old FlickrJ uses SOAP API which is not supported on GAE.
  * Support for the new Flickr OAuth 1a: http://www.flickr.com/services/api/auth.oauth.html. According to the official Flickr announcement, the old auth has been deprecated and will be soon retired.
  * Completely re-written with JSON response format
  * Now built by Maven instead of Ant
  * Use https by default for all API requests(thanks to Paul Bourke): http://code.flickr.net/2014/04/30/flickr-api-going-ssl-only-on-june-27th-2014/. Please use version 2.1.0+
  * Accessible over Maven-Central with the following dependency:
```
<dependency>
 <groupId>com.googlecode.flickrj-android</groupId>
 <artifactId>flickrj-android</artifactId>
 <version>2.1.0</version>
</dependency>
```
> > Alternatively you can directly download the binary jars from http://search.maven.org/#search%7Cga%7C1%7Ca%3A%22flickrj-android%22
  * Added many missing functions in the original FlickrJ, such as Gallery and Collection

## Release Notes ##
Check out our ReleaseNotes for what new features are currently available.

## Powered Applications ##
We have built two applications using this library for [Android Honeycomb tablets](http://code.google.com/p/flickr-viewer-for-honeycomb/) and [Google App Engine web app](http://code.google.com/p/flickr2twitter/) respectively.

[![](http://code.google.com/images/code_sm.png)](http://code.google.com/)
[![](http://farm7.static.flickr.com/6092/6219249467_54a26f7d5d_o.gif)](http://developer.android.com/index.html)
[![](http://maven.apache.org/images/logos/maven-feather.png)](http://maven.apache.org/)

[![](http://bighugelabs.com/flickr/profilewidget/interesting/000000/ffffff/8308954@N06.jpg)](http://flickr.com/photos/8308954@N06/)