---
layout: default
title: Runner
heading: Supported Keywords
permalink: runner_keywords.html
---

Bot-bot is based on keyword driven approach. 

- Following table shows a list of keywords currently supported by bot-bot runner. 
- Other than the said list any functions supported by base frameworks like Robotium and NativerDriver can also be used as keyowrds. In such cases bot-bot automatically finds the keyword and execute them with passed parameters. 
- Bot-bot also allows user to define/add their own keywords and functionalities. This can be achieved very easily with minimal changes.


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
</table>
