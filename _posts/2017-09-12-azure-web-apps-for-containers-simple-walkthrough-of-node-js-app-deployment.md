This is a super simple walkthrough to show how to use Git and push your app to Azure Web Apps for Containers.&nbsp; It will not persist your Git repo but is a super quick way to show how this is done and perhaps help you if you are having troubles getting your app configured!

# 

# 

# 

# Walkthrough

Get a Cloud Shell by clicking on the >_ icon on the right side of the Azure Portal

[<img loading="lazy" title="capture20170911135221921" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170911135221921" src="/assets/images/2017/09/capture20170911135221921_thumb.png" width="557" height="327" />](/assets/images/2017/09/capture20170911135221921.png)

You may have to create a Storage Account (if so you will be prompted):

[<img loading="lazy" title="capture20170911135322767" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170911135322767" src="/assets/images/2017/09/capture20170911135322767_thumb.png" width="575" height="228" />](/assets/images/2017/09/capture20170911135322767.png)

Finally you will get a terminal session like this:

[<img loading="lazy" title="capture20170911135442597" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170911135442597" src="/assets/images/2017/09/capture20170911135442597_thumb.png" width="694" height="269" />](/assets/images/2017/09/capture20170911135442597.png)

In the terminal, pull down this sample from GitHub to the terminal using this command: 

**git clone** [**https://github.com/Azure-Samples/nodejs-docs-hello-world**](https://github.com/Azure-Samples/nodejs-docs-hello-world)

Change to the directory that contains the sample code with this command: ****

**cd nodejs-docs-hello-world**

Inspect the files that are there with this command: 

**ls**

Display the contents of the index.js file with this command: 

**more index.js**

[<img loading="lazy" title="capture20170911140318249" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170911140318249" src="/assets/images/2017/09/capture20170911140318249_thumb.png" width="475" height="355" />](/assets/images/2017/09/capture20170911140318249.png)

Create an Azure Web App, choosing Linux for the OS and the latest Node.js for the Runtime stack:

[<img loading="lazy" title="capture20170911142547882" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170911142547882" src="/assets/images/2017/09/capture20170911142547882_thumb.png" width="371" height="488" />](/assets/images/2017/09/capture20170911142547882.png)

&nbsp;

Once app is created, you need to ensure you have Deployment Credentials.&nbsp; If you already have Deployment Credentials great!&nbsp; If you don’t or you forgot your password, create a new user and pwd (and remember them):

[<img loading="lazy" title="capture20170911151030668" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170911151030668" src="/assets/images/2017/09/capture20170911151030668_thumb.png" width="450" height="283" />](/assets/images/2017/09/capture20170911151030668.png)

&nbsp;

Go to Deployment options and choose ‘Local Git Repository’ (don’t forget to save by hitting the ‘OK’ button) :

[<img loading="lazy" title="capture20170911140638585" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170911140638585" src="/assets/images/2017/09/capture20170911140638585_thumb.png" width="583" height="330" />](/assets/images/2017/09/capture20170911140638585.png)

Go to Properties and copy the GIT URL for future use:

[<img loading="lazy" title="capture20170911140833039" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170911140833039" src="/assets/images/2017/09/capture20170911140833039_thumb.png" width="742" height="228" />](/assets/images/2017/09/capture20170911140833039.png)

&nbsp;

In the local terminal window, add an remote repo named _azure_ to your local Git repository:

**git remote add azure <URI from previous step>**

Add the files and a commit message:

**git add -A  
git commit -m &#8220;my first node app push&#8221;**

&nbsp;

Notice you will get this next in the Bash terminal:

<font face="Courier New">*** Please tell me who you are.</font>

<font face="Courier New">Run</font>

<font face="Courier New">&nbsp; git config &#8211;global user.email &#8220;you@example.com&#8221;<br />&nbsp; git config &#8211;global user.name &#8220;Your Name&#8221;</font>

<font face="Courier New">to set your account&#8217;s default identity.<br />Omit &#8211;global to set the identity only in this repository.</font>

Don’t panic, just add an email and name like this (you do not have to use a real email or name… it is just a local identifier):

**git config &#8211;global user.email jsanderstesting@hotmail.com  
** **git config &#8211;global user.name jeff**

**  
** And then do the commit again:  
**git commit -m &#8220;my first node app push&#8221;**  
<font face="Courier New">On branch master<br />Your branch is up-to-date with &#8216;origin/master&#8217;.<br />nothing to commit, working directory clean</font>

Push to the Azure remote to deploy your app with the following command. When prompted for a password, make sure that you enter the password you got from the publish profile, not the password you use to log in to the Azure portal. 

**git push azure master**

<font face="Courier New">Password for &#8216;</font>[<font face="Courier New">https://jsandersftp2@jsandersnodejs.scm.azurewebsites.net:443&#8242;:</font>](https://jsandersftp2@jsandersnodejs.scm.azurewebsites.net:443':)

<font face="Courier New">Counting objects: 37, done.<br />Compressing objects: 100% (36/36), done.<br />Writing objects: 100% (37/37), 5.13 KiB | 0 bytes/s, done.<br />Total 37 (delta 16), reused 0 (delta 0)<br />remote: Updating branch &#8216;master&#8217;.<br />remote: Updating submodules.</font>

<font face="Courier New">….</font>

<font face="Courier New">remote: Running post deployment command(s)&#8230;<br />remote: Deployment successful.<br />remote: App container will begin restart within 10 seconds.</font>

&nbsp;

And you should be able to browse to your app!

&nbsp;

[<img loading="lazy" title="capture20170911150655040" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-rig
ht: 0px;border-top-width: 0px" border="0" alt="capture20170911150655040" src="/assets/images/2017/09/capture20170911150655040_thumb.png" width="337" height="119" />](/assets/images/2017/09/capture20170911150655040.png)

# Closing Notes

This is just a super easy way to explore this!&nbsp; The container is not persisted so you will not be able to use this for development.&nbsp; The Git repo and your code will disappear when this container is brought down or recycled.&nbsp; If you are doing real development you should install node and git and push from your local machine.&nbsp; Try playing with an editor like vim and changing the app.js file response.end statement to say something else and commit and push your changes!