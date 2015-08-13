# Introduction #

This wiki page will walk you through how to upload a new build to the Google Code project downloads page: https://code.google.com/p/flickrj-android/downloads/list


# Details #
This task is utilizing the work from http://code.google.com/p/ant-googlecode/.

Run the following command would automatically upload a new build to the project site:
```xml

$ mvn clean javadoc:javadoc install -DskipTests -Prelease
$ cd flickrj-android
$ ant -Denv.gcode.user="XXX" -Denv.gcode.pwd=YYY
```

You would need to substitute the **XXX** with your GCode account name, and **YYY** with your password found at https://code.google.com/hosting/settings