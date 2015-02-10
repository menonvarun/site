---
layout: default
title: Runner
heading: Runner
permalink: runner.html
---
##Introduction :

Runner is a test execution and report generation component of bot-bot.It is based on keyword driven approach. 

The test cases are defined in “csv” format which contains the keywords and their respective required parameters. These csv files are then interpreted by runner and executed on the application under test on an android device/emulator. At the end of the execution runner generates emailable html reports in the format of Junit and TestNG-xslt. These reports shows pie chart and % execution of your test-cases. For more info you can click [here]()
Runner supports 2 types of frameworks **NativeDriver** & **Robotium**. User can choose accordingly from any of the said frameworks.

Runner supports following features:

- Support for test-atuomation for an android application without the need of application source code.
- Execution of the test-case csv file on the said application and generate a test report for it.
- Users can easily add their own implementations to bot-bot and use them as keywords. Bot-bot framework will automatically identify these implementation and execute them accordingly.
- Support for native framework functions are supported out-of-the box.

Runner is mainly implemented using following open-source tools:

1. [Robotium](http://code.google.com/p/robotium/)
2. [Selenium Nativedriver](http://code.google.com/p/nativedriver/)
3. [TestNG](http://testng.org/doc/index.html)

**Note:** In case you need to use Nativedriver as your execution framework , you need to have the source code of the app that needs to be tested.

