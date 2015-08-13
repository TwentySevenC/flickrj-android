# Introduction #

Generating a release within maven is very straight-forward. You need

  * maven
  * gnupg (including a key)

installed.

To make the jar accessible over google code, github and central repo, you furthermore need accounts for these and put them in _~/.m2/settings.xml_:

```
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
  http://maven.apache.org/xsd/settings-1.0.0.xsd">
  ...
 <servers>
  <server>
   <id>googlecode</id>
   <username>{your googlecode username}</username>
   <password>{your gooclecode password}</password>
  </server>
  <server>
   <id>sonatype-nexus-snapshots</id>
   <username>{your sonatype username}</username>
   <password>{your sonatype password}</password>
  </server>
  <server>
   <id>sonatype-nexus-staging</id>
   <username>{your sonatype username}</username>
   <password>{your sonatype password}</password>
  </server>
 </servers>
 <profiles>
  <profile>
   <id>github</id>
   <properties>
    <github.global.userName>{your github username}</github.global.userName>
    <github.global.password>{your github password}</github.global.password>
   </properties>
  </profile>  
 </profiles>

 <activeProfiles>
  <activeProfile>github</activeProfile>
 </activeProfiles>
</settings>
```

# Releasing a jar to the Snapshot Repo #

Simple deploy:
```

bash:FlickrjApi4Android$ cd flickrj-android
bash:flickrj-android$ mvn clean deploy -Prelease```

# Releasing a jar as new release #

Note that only the flickj-android is released, not the aggregator project:
  1. Adapt the version-number to bring the jar on a stable level in the root/pom.xml and the flickrj-android module
  1. Upload the jar
```
bash:FlickrjApi4Android$ cd flickrj-android
bash:flickrj-android$ mvn clean deploy -Prelease
```
  1. Go to https://oss.sonatype.org/ , login and release the staged repository

# Upload a new version of the Javadoc #

Note that the Javadoc is release over the aggregator project:
```
bash:flickrj-android$ cd ..
bash:FlickrjApi4Android$ mvn site:site
bash:FlickrjApi4Android$ mvn ghSite:site -N
```

# Further Information #

Information about deploying to central repo is available under https://docs.sonatype.org/display/Repository/Sonatype+OSS+Maven+Repository+Usage+Guide