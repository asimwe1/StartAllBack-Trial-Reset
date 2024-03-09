# Note
I do not condone piracy, if you find StartAllBack to be truly
useful and have some money to spare, consider buying a license
key: https://www.startisback.com/#buy-tab

---

# Reset Trial



My initial plan for this gist was to provide updated Registry paths
for resetting the StartAllBack trial.  Then I came to a conclusion
that this is not sufficient due to the nature of how StartAllBack
handles the trial state.

Here I'll outline all the steps required to manually figure out the
registry path related to the StartAllBack trial.

Before we begin please know that this should not be taken for granted
because no one is stopping the developers of StartAllBack from taking
a new approach as to how they handle the trial state in the app.

For future references I will not provide any support regarding this
topic because everything will be explained below on how to figure out
the correct
[CLSID](https://en.wikipedia.org/wiki/Universally_unique_identifier)
yourself.  For simple _issues_ you can quickly get an answer using
a search engine.

---

# DIY - Do It Yourself

If you don't have StartAllBack then [get it here](https://www.startallback.com/) and install it.

Then download [Process Monitor](https://learn.microsoft.com/en-us/sysinternals/downloads/procmon) ([Direct Link](https://download.sysinternals.com/files/ProcessMonitor.zip)) which is used to inspect function calls the program makes.  
When you start it for the first time, it will automatically begin to capture events of all running processes.

![image](https://user-images.githubusercontent.com/102489121/261901759-68d77378-c39f-4708-b336-d996e7dc81b5.png)

In the toolbar:  
Click on the 3rd icon (Ctrl + E) to stop the capture.  
Click on the 5th icon (Ctrl + X) to clear the previous capture log.  
Click on the 6th icon (Ctrl + L) to set up a specific filter:

![image](https://user-images.githubusercontent.com/102489121/261913507-a4388463-835b-4099-9558-e9700b7ee780.png)


Now click the 3rd icon (Ctrl + E) in the toolbar to begin capturing events matching the filter.



Open up StartAllBack properties:

![image](https://user-images.githubusercontent.com/102489121/261909296-abadf885-e5b7-4a0f-8ae7-e5a399c2fa81.png)

Once the window loads, go back to the Process Monitor window and you should see something similar to this:

![image](https://user-images.githubusercontent.com/102489121/261915930-c15c95c7-8453-470d-877c-79e6bfb99194.png)

|Disclaimer|
|-|
|In some cases the returned path will contain the CLSID `{yyyy yyyy}` because of a programming error. Removing it _should_ reset the trial as documented by other people in the comments.|

Right click on the path item in the Path column and click `Copy 'HKCU\Software\...`

Now open Command Prompt as Administrator and use the following command template to create the command matching your path:

```
reg delete "YOUR_PATH" /f
```

For this tutorial it is:

```
reg delete "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\CLSID\{36b74d56-9dfb-6ba1-cee4-0a97d8f99e0}" /f
```

![image](https://user-images.githubusercontent.com/102489121/261917022-b4a80f95-4778-4b6f-883c-329108bb77d2.png)

Before and after:

![image](https://user-images.githubusercontent.com/102489121/261918326-2fd47471-68e8-4fe8-9bf7-b1285759bdfb.png)

**\*** This requires reopening StartAllBack properties window.

---

# Previous gist

To see the commands provided before the tutorial, browse the [last known file](https://github.com/asimwe1/StartAllBack-Trial-Reset/blob/main/Commands.md) that contained them.

Those are outdated and should be ignored in favor of the tutorial.
