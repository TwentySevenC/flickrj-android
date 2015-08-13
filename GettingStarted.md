# Introduction #
This is a Java API which wraps the REST-based Flickr API
(information available at http://www.flickr.com/services/api/).

This API has been tested with **JDK 6.0**.

# Details #

To use the API just construct a instance of the class
'com.gmail.yuyang226.flickr.Flickr' and request the interfaces which you need to work with.  For example, to send a test ping to the Flickr service:

```java

String apiKey = YOUR_API_KEY
Flickr f = new Flickr(apiKey);
TestInterface testInterface = f.getTestInterface();
Collection results = testInterface.echo(Collections.EMPTY_LIST);
```

An API key is required to use this API.  You should contact Flickr to
acquire an API key.  More information is available at:
http://www.flickr.com/services/api/.

Comments and questions should be sent to flickrj-android@googlegroups.com, and issues could be directly submitted to http://code.google.com/p/flickrj-android/issues/list