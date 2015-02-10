---
layout: default
title: Runner
heading: Data-Driven Tests
permalink: runner_datadriven.html
---

##What is Data-Driven testing?

Data-driven testing in the field of automation means execution of a set of test-cases based on the different data-sets. It is one of the important concepts that is implemented many test-frameworks. 

For ex. There is a login screen with username and password fields. Now we need to test this login screen with different sets of username and passwords. In this case opening the main screen,entering username,entering password and clicking on login is the test-case. Where as multiple sets of username/password with which we need to test the functionality becomes the data.

The advantage of using data-driven testing is that in case there is an addition and deletion of data, the test-framework automatically takes care of execution without any functional changes.

----------------
##Data-Driven Tests

Bot-bot runner allows user to run Data-driven tests
Currently Data-driven testing is only supported for Robotium platform & data can be provided only from csv files.

Steps and conventions to be followed for data-driven tests:

1. Data-driven tests should be placed under folder named as 'datadriven'.

2. Data-driven test cases should end with '_datadriven.csv' eg. {testcasename}_datadriven.csv and Data files should end with '_data.csv'  
   eg {testcasename}_data.csv. Note:data file should be named as {testcasename}_data.csv 

3. Values which are to be provided from data.csv at run time should start with $ followed by identifier which would be present in data.csv eg. $title

4. Data files (_data.csv) should have first row as identifiers saperated by commas and other rows as set of data saperated by comma.

5. The first value in the row is considered as testcase name for generation of report, if left blank name of datadriven test case will be considered. Each row is taken as data for a test case.

6. For sample test case with datadriven approach see createNewPost_datadriven.csv and createNewPost_data.csv in datadriven folder present in testcases/wordpress/datadriven 
