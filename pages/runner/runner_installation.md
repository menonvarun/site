---
layout: default
title: Runner
heading: Runner Instalaltion
permalink: runner_installation.html
---
##Pre-conditions:

1. Java jdk neeeds to be installed. More info is available at [link](http://java.com/en/download/index.jsp) 
2. Android SDK has been installed. More info is available at [link](http://developer.android.com/sdk/installing.html)
3. Apache ant 1.8.3 and higher needs to be installed.[link](http://ant.apache.org/)
4. Install one of the android SDK platform using the Android SDK managers.

---------
##Installation:

###For Robotium:

1. Apk file of the application that needs to be tested.
2. Open the resources/default.properties file and change the following values:
	- FRAMEWORK -> "robotium"
	- TESTCASE_FOLDER -> test-case folder name under *testcase* where you have your test-cases in csv format.
	- TEST_APK_FILENAME -> Apk file path of the application that needs to be tested.
	- APP_PACKAGE -> The app package name.
	- DEFAULT_ACTIVITY -> Default lanch activity
 	- ANDROID_VERSION -> The version of the android platform that you had downloaded using android sdk. This can be found out by going to the platforms under your **Android SDK** installation directory.
 	- key.store -> path to your keystore file to be used for signing the andorid application. Once you had installed Androdi SDK and configured a simulator this key store file will be automatically generated in your user home directory under *android* fodler.
	- key.store.password -> password of your keystore
	- key.alias -> Alias for you keystore file
	- key.alias.password -> Password of your keystore alias.

	In case you want to use the default keystore file please dont change the above keystore related values in the properties file.
 

	For finding the values of APP_PACKAGE & DEFAULT_ACTIVITY variables install your application on an emulator and start the application. And then watch the adb logs by typing the command *adb logcat*. And look for the following:

{% highlight ruby %}
"Starting activity: Intent { act=android.intent.action.MAIN cat=android.intent.category.LAUNCHER? flg=0x10200000 cmp=com.example.android/.DefaultLauncherActivity"
{% endhighlight %}


From the above APP_PACKAGE will be *com.example.android* and DEFAULT_ACTIVITY will be *DefaultLauncherActivity*.
	
	
3. Set the "ANDROID_HOME" enviornment variable to the Android SDK installation directory on your system ex. "/opt/softwares/android-sdk-linux"
4. Set the tools and platform-tools folder path to your enviornment PATH. ex. "/opt/softwares/android-sdk-linux/tools" & "/opt/softwares/android-sdk-linux/platform-tools"
5. Place your test-case csv files under a folder inside the *testcases* folder in root of the *runner*.
6. From the command-shell go to the the *bot-bot runner* folder and type the follwing command.
{% highlight C %}
ant
{% endhighlight %}

###For NativeDriver:

1. Export the bot-bot from git to your local system.
2. Import the source code of the android app that needs to be installed into your eclipse IDE.
3. Copy the "server-standalone.jar" from the bot-bot/runner/lib folder to the root of the Android project inside Eclipse IDE and add it to build path.
4. Open the AndroidManifest.xml file of your Android app and paste the following to it:

{% highlight ruby %}
< instrumentation android:targetPackage="{app package name}" android:name="com.google.android.testing.nativedriver.server.ServerInstrumentation" />
<uses-permission android:name="android.permission.INTERNET" /> 
< uses-permission android:name="android.permission.WAKE_LOCK" />
< uses-permission android:name="android.permission.DISABLE_KEYGUARD" />
{% endhighlight %}

Here the {app package name} needs to be replaced with the name of the package as specified in the mainfest element's package attribute.

5. Build and install the android app on to the simulator.

6. Go to the android sdk installation folder and inside it to platform-tools. Then run the following commands:

{% highlight ruby %}
adb shell am instrument {app_package_name}/com.google.android.testing.nativedriver.server.ServerInstrumentation
{% endhighlight %}

Here {app_package_name} needs to be replaced with the name of the package as specified in the mainfest element's package attribute.
	
{% highlight ruby %}
adb forward tcp:54129 tcp:54129
{% endhighlight %}

You can confirm that the instrumentation is started by running adb logcat and looking for a line like this:

{% highlight ruby %}
I/com.google.android.testing.nativedriver.server.ServerInstrumentation(  273): Jetty started on port 54129
{% endhighlight %}

7. Package name and initial activity name has to be defined in the BaseClass.java file. (This will be converted to properties file going forward)
8. Run the ant command at the root of the andro_auto_framework directory:

{% highlight ruby %}
ant
{% endhighlight %}

This will compile your code and execute your test cases. Currently TestNG , Junit & TestNG-xslt report are generated for the test execution.


-----------
##Data-Driven Tests

Currently Data-driven testing is only supported for Robotium platform & data can be provided only from csv files.

Steps and conventions to be followed for data-driven tests:

1. Data-driven tests should be placed under folder named as 'datadriven'.

2. Data-driven test cases should end with '_datadriven.csv' eg. {testcasename}_datadriven.csv and Data files should end with '_data.csv'  
   eg {testcasename}_data.csv. Note:data file should be named as {testcasename}_data.csv 

3. Values which are to be provided from data.csv at run time should start with $ followed by identifier which would be present in data.csv eg. $title

4. Data files (_data.csv) should have first row as identifiers saperated by commas and other rows as set of data saperated by comma.

5. The first value in the row is considered as testcase name for generation of report, if left blank name of datadriven test case will be considered. Each row is taken as data for a test case.

6. For sample test case with datadriven approach see createNewPost_datadriven.csv and createNewPost_data.csv in datadriven folder present in testcases/wordpress/datadriven 


------------------
##Keywords

Following is the list of keywords currently supported by bot-bot runner:

<table border="1"><tr><th>Keyword</th><th>Description</th></tr><tr><td><a name="assertbuttonpresent">assertbuttonpresent</a></td><td>Needs one argument button-text. Check whether a button with the said text button-text is present in the current view.</br>Fails the test in-case the said button is not found</td>
</tr>
<tr><td><a name="assertlocatorpresent">assertlocatorpresent</a></td><td>Needs one arugument the locator. Checks whether the said locator is available on the said page. Fails in case it is not found</td>
</tr>
<tr><td><a name="assertmenuitem">assertmenuitem</a></td><td>Needs one argument the menu-text that needs to be verified. Fails in case the menu-item is not found.</td>
</tr>
<tr><td><a name="assertpartialtextpresent">assertpartialtextpresent</a></td><td>Needs one argument text. Fails in case the text is not present on the current page. It checks for only partial text.</td>
</tr>
<tr><td><a name="assertradiobuttonpresent">assertradiobuttonpresent</a></td><td>Needs one argument radio button text. Fails in case no radio button with the said text is found.</td>
</tr>
<tr><td><a name="assertspinnerpresent">assertspinnerpresent</a></td><td></td>
</tr>
<tr><td><a name="asserttextpresent">asserttextpresent</a></td><td>Needs one argument text. Fails in case the text is not present on the current page</td>
</tr>
<tr><td><a name="checkbuttonpresent">checkbuttonpresent</a></td><td>Needs one argument button-text. Check whether a button with the said text button-text is present in the current view.</br> Shows warning message in case the said button is not found</td>
</tr>
<tr><td><a name="checklocatorpresent">checklocatorpresent</a></td><td>Needs one argument the locator. Checks whether the said locator is available on the said page.</br>Shows warning message in case its not found.</td>
</tr>
<tr><td><a name="checkradiobuttonpresent">checkradiobuttonpresent</a></td><td>Needs one argument radio button text. Shows warning in case no radio button with the said text is found.</td>
</tr>
<tr><td><a name="checktextpresent">checktextpresent</a></td><td>Needs one argument the said text. Checks for the said on the text. Shows warning message in case not found.</td>
</tr>
<tr><td><a name="clickback">clickback</a></td><td>Simulates clicking on back button. Can be used to hide the auto keyboard popped-up while running cases.</td>
</tr>
<tr><td><a name="clickbutton">clickbutton</a></td><td>Needs one argument button-text. Find and click on the button with the said text.</td>
</tr>
<tr><td><a name="clickbyid">clickbyid</a></td><td>Needs one argument id. This is available in the R.java file of the said android application. Finds and clicks on the said id.</td>
</tr>
<tr><td><a name="clickmenu">clickmenu</a></td><td>Simulates clicking on a Menu button</td>
</tr>
<tr><td><a name="clickradiobutton">clickradiobutton</a></td><td>Needs one argument radio button text. Finds and click on the radio button with the said text.</td>
</tr>
<tr><td><a name="clickspinner">clickspinner</a></td><td>Used to click on spinner and select a value. Takes two arguments “rid” and “value”(to be selected).</br>Currently selects the value only if it is available in the current view/ screen.</br> In case the user need to scroll for a value use clickbyid,scrollup/scrolldown & click text. </td>
</tr>
<tr><td><a name="clicktext">clicktext</a></td><td>Needs one argument text. Finds and clicks on the said text.</td>
</tr>
<tr><td><a name="entertext">entertext</a></td><td>Needs two arguments locator & the text.</br>Locator can be anything that is supported by selenium like (text,partialtext,id, etc).</br>The locator type and the actual locator should be differentiated by </td>
</tr>
<tr><td><a name="openapp">openapp</a></td><td>Not implemented currently</td>
</tr>
<tr><td><a name="scrolldown">scrolldown</a></td><td>Simulate scrolling downside. No of time to scroll can be provided as argument. Default being 1.</td>
</tr>
<tr><td><a name="scrollup">scrollup</a></td><td>Simulate scrolling upside. No of time to scroll can be provided as argument. Default being 1.</td>
</tr>
<tr><td><a name="verifyscreen">verifyscreen</a></td><td>Used to verify the screen. Takes one argument as past of the base image file.</br>The said file is matched with the current screen. This command uses sikuli internally.</td>
</tr>
<tr><td><a name="waitforscreen">waitforscreen</a></td><td>Waits for the said screen to appear.</td>
</tr>
</table>

