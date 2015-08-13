# Introduction #

This page summarizes the new features for each of the release.

_(Note to devs, release logs against the latest tag can be generated with:)_
```
git log --no-merges --pretty=format:' * %s (%an <%ae>)' $(git describe --abbrev=0)..master | grep -v maven-release-plugin
```

# 2.1.0 #
  * Use https by default for all API requests(thanks to Paul Bourke): http://code.flickr.net/2014/04/30/flickr-api-going-ssl-only-on-june-27th-2014/

Important Details:
  1. Non SSL access is being removed by Flickr, all new requests must go   to the https://api.flickr.com endpoint
  1. All requests to http://www.flickr.com will be redirected to the https version.

# 2.0.8 #
  * Fixed the problem when retrieving title of a photo for Photosets due to the recent change in the Flickr response message format.
  * Call setWidth() and setHeight() for the existing Size instances when parsing a photo

# 2.0.7 #
  * Making the Size class implement Comparable (Muhammad Ali <register2ali@gmail.com>)
  * Adding support for more sizes (Muhammad Ali <register2ali@gmail.com>)
  * Add video related constants to Size class (Paul Bourke <pauldbourke@gmail.com>)
  * Update the sample app imports and package name (Paul Bourke <pauldbourke@gmail.com>)

# 2.0.6 #
  * Flickr groups join/leave

# 2.0.5 #
  * bug fixes

# 2.0.4 #
  * Add OAuth for Photoset.getInfo if applicable
  * bug fixes

# 2.0.3 #
  * Changed the PhotosetsInterface.getPhotos to return Photoset instead of PhotoList

# 2.0.1 #
  * Minor bug fix

# 2.0.0 #
  * Changed package structure to com.googlecode.flickjandroid due to push on maven central
  * Changed groupId to com.googlecode.flickj-android due to push on maven central

# 1.0.2 #
  * Supports Large Square image size
  * Fixed the issue that photo dates not set when loading a photo

# 1.0.0 #
  * Initial Release based on flickrj
  * Compatible with both Android and Google App Engine
  * JSON based data format
  * Utilizing SLF4J for logging
  * Support Collection and Gallery
  * Support uploading
  * Plenty of exciting features waiting for you to discover

### Known Issues ###
  * The Uploader.replace() function does not work
  * Some photo details are not retrieved