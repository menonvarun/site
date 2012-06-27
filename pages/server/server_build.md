---
layout: default
title: Build from Source
permalink: server_build.html
heading: Build the Server from Source
---
##Pre-conditions:

1. Java jdk neeeds to be installed. More info is available at [link](http://java.com/en/download/index.jsp)
2. Maven has been installed. Maven can be downloaded from [link](http://maven.apache.org/download.html)

---------
##Build the war:

Once done run the following command at the root of the bot-bot/server folder

{% highlight ruby %}
mvn clean install
{% endhighlight %}

</br>
This will generate **_"bot-bot-server-standalone.jar"_** and **_"bot-bot-server.war"_** files under the bot-bot/server/target folder.
These files can then run using the guidelines provided in the server installation page. 

-----------------------
