# Introduction #

This wiki page will works you through how to use this library building a Google Apple Engine application for Flickr.


# Details #

In order for using this library on Google App Engine, you would need to download and put the following jars into the **war/WEB-INF/lib** folder of your GAE project.
  * SLF4J for logging: http://www.slf4j.org/download.html, and you would only need **slf4j-api-xxx.jar** and **slf4j-jdk14-xxx.jar**.
  * org.json for JSON Processing: you can either download the source code from http://json.org/java/, or grab a jar from http://repo1.maven.org/maven2/org/json/json/20090211/json-20090211.jar