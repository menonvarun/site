---
layout: default
title: Server Installation
permalink: server_installation.html
heading: Server Installation
---

## Deploy the downloaded war
The war is self contained including the database. 

The war can be deployed in two ways:

- **As a standalone server**.

To deploy the bot-bot server as a standalone server, go to the server folder under the latest download.
You will find a file with name "bot-bot-server-standalone.jar". Run the following command in the command prompt after going to the said folder.

```bash
 java -jar bot-bot-server-standalone.jar
```

This will start the standalone bot-bot server. The server can be accessed using the url "http://localhost:8080/index.html".

- **On an servlet supported webserver**:

	Bot-bot server can be deployed to any of the servlet container like *Apache Tomcat*, *Jboss*, etc.To deploy the war do the following:
	- Create the war as mentioned in the *Build the war* section.
	- Copy the war from the target folder under the bot-bot/server to the webapps folder of your serrvlet container.
	- Start your server.
	- Access the server using the following URL

	```bash
	http://&lt;localhost or systemip&gt;:&lt;port&gt;/bot-bot-server/index.html
	```
	Note: In case you are deploying the war on a servlet container server. You need update the "SERVER_NAME" under the recorder.properties file in the "recorder" section. The recorder is currently configured to record on the standalone bot-bot server deployment.

------------
##Usage

Once recording starts the user can access the sessions on the server:
Following features are supported:

- Viewing the recorded seesions. The server shows all the recorded session on the server. Once user clicks on particular session, the recorded data that particular session will be shown.
- Viewing the recorded records for a session.
- Refresh the session page for a new recorded entries.
- Export as CSV -> Once clicked on "Export as CSV" link, server will give you download option for downloading your test-case as a csv file.
- Edit of an existing record. You can edit any existing recorde to change the command or update any other values.
- Add a new command row. You can add new command row before or after any existing rows to modify your test-case.

----------------
