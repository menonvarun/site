---
layout: default
title: Server Installation
permalink: server_installation.html
heading: Server Installation
---
##Pre-conditions:

1. Java jdk neeeds to be installed. More info is available at [link](http://java.com/en/download/index.jsp)

-----------------

## Deploy the downloaded files
The war is self contained including the database. 

The war can be deployed in two ways:

- **As a standalone server**.

To deploy the bot-bot server as a standalone server, go to the server folder under the latest download.
You will find a file with name "bot-bot-server-standalone.jar". Run the following command in the command prompt after going to the said folder.

{% highlight ruby %}
 java -jar bot-bot-server-standalone.jar
{% endhighlight %}
</br>
This will start the standalone bot-bot server. The server can be accessed using the url "http://localhost:8080/index.html".

- **On an servlet supported webserver**:

	Bot-bot server can be deployed to any of the servlet container like *Apache Tomcat*, *Jboss*, etc.To deploy the war do the following:
	- Create the war as mentioned in the *Build the war* section.
	- Copy the war from the target folder under the bot-bot/server to the webapps folder of your serrvlet container.
	- Start your server.
	- Access the server using the following URL

{% highlight ruby %}
http://<localhost or systemip>:<port>/bot-bot-server/index.html
{% endhighlight %}
</br>
Note: In case you are deploying the war on a servlet container server. You need update the "SERVER_NAME" under the recorder.properties file in the "recorder" section. The recorder is currently configured to record on the standalone bot-bot server deployment.

