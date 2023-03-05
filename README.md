## Flickr4Java

<p align="center">
<img src="https://upload.wikimedia.org/wikipedia/commons/thumb/9/9b/Flickr_logo.png/1200px-Flickr_logo.png" alt="flickrLogo" width="400px"/>


### Introduction

__Note:__ This API has been forked from [FlickrJ at Sourceforge](http://flickrj.sourceforge.net/).

This is a Java API which wraps the [REST-based Flickr API](http://www.flickr.com/services/api/).

It is designed to access the Flickr platform, and it's based on Flickr's RESTful web services architecture.

Flickr4Java provides interfaces and functions to be used by the API.

Some of the API features include the ability to upload, download, and search photos, manage albums and tags, and interact with other photos and users.
Also provides functionality for user authentication via OAuth, which allows applications to access user profile data and photos. Allows group management and viewing of user profile information.

Comments and questions should be raised on the [GitHub Repo issue tracker](https://github.com/boncey/Flickr4Java/issues).

## Table of contents

  - [1 - Usage](#1---usage)
  - [2 - Requirements](#2---requirements)
    - [2.1 - Required libraries](#21---required-libraries)
  - [3 - Gradle](#3---gradle)
  - [4 - Maven](#4---maven)
  - [5 - Testing](#5---testing)
    - [5.1 - Functional testing against the Flickr API](#51---functional-testing-against-the-flickr-api)
  - [6 - Team](#6---team)
  - [7 - License](#7---license)


## [1 - Usage](#table-of-contents)

To use the API just construct an instance of the class `com.flickr4java.flickr.test.Flickr` and request the interfaces which you need to work with.  
For example, to send a test ping to the Flickr service:

    String apiKey = "YOUR_API_KEY";
    String sharedSecret = "YOUR_SHARED_SECRET";
    Flickr f = new Flickr(apiKey, sharedSecret, new REST());
    TestInterface testInterface = f.getTestInterface();
    Collection results = testInterface.echo(Collections.EMPTY_MAP);
    
See `/src/examples/java` for more.

The API provides a class called Uploader that allows you to choose between uploading photos and videos synchronously or asynchronously, via a background task. And it supports uploading images in various sizes and formats, giving users more options to suit their needs.

## [2 - Requirements](#table-of-contents)

This API has been tested and built with JDK 1.8.

An API key is required to use this API.  You can [request one on Flickr](http://www.flickr.com/services/api/).

### [2.1 - Required libraries](#table-of-contents)

- [scribejava-api (v 6.9.0 onwards)](https://github.com/scribejava/scribejava) (required for the OAuth functionality)
- [SLF4J](https://www.slf4j.org) (runtime dependency for logging)

[See here](https://www.slf4j.org/manual.html#swapping) for details on how to choose and configure an SLF4J logging library.

## [3 - Gradle](#table-of-contents)

    compile 'com.flickr4java:flickr4java:3.0.6'
    
## [4 - Maven](#table-of-contents)

    <dependency>
      <groupId>com.flickr4java</groupId>
      <artifactId>flickr4java</artifactId>
      <version>3.0.6</version>
    </dependency>

Flickr4Java is available on Maven Central so the above settings should be all you need.

## [5 - Testing](#table-of-contents)
The tests now run against captured responses from Flickr (see `src/test/resources/payloads`) and don't contact the Flickr API at all.  
This means there is no longer any need to create a test account and populate a properties file.

### [5.1 - Functional testing against the Flickr API](#table-of-contents)
This is the setup to run the tests against the Flickr API.  
*Not for the faint-hearted. Only do this to test large refactorings etc.*  

Create up a `setup.properties` file (see `src/test/resources/setup.properties.example`) with details of a real account on Flickr (I recommend setting up a test account for this purpose).  
Run tests as follows.  

    mvn -DsetupPropertiesPath=/path/to/your/setup.properties clean install

Expect lots of failures and general flakiness as data has changed on Flickr and the tests or data need updating.


## [6 - Team](#table-of-contents)

Our team is made of two core members:

- [Darren Greaves (boncey)](https://github.com/boncey)

- [Allan (callmeal)](https://github.com/callmeal)

We also have an [community of developers](https://github.com/boncey/Flickr4Java/graphs/contributors) who help us improve our project together!

## [7 - License](#table-of-contents)
Flickr4Java is distributed under the [BSD 2-Clause "Simplified" License](/LICENSE.md).

