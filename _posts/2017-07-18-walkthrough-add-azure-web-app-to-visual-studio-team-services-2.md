---
id: 3395
title: 'Walkthrough&#8211;Add Azure Web App to Visual Studio Team Services'
date: 2017-07-18T12:40:39-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=3395
permalink: /2017/07/18/walkthrough-add-azure-web-app-to-visual-studio-team-services-2/
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="Walkthrough&ndash;Add Azure Web App to Visual Studio Team Services" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/07/18/walkthrough-add-azure-web-app-to-visual-studio-team-services-2/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="Overview In this walkthrough I will show&nbsp; you how to use Visual Studio Team Services with an existing Azure App Service project (specifically an Azure Web App).&nbsp; We will add a task to update/create the project database from a DACPAC file and enable CI (Continuous Integration). Sign up for Visual Studio Team Services&nbsp; Go to:..." />
    <meta property="og:image" content="/assets/images/2017/07/capture20170717092329860_thumb.png" />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="Walkthrough&ndash;Add Azure Web App to Visual Studio Team Services" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2017/07/18/walkthrough-add-azure-web-app-to-visual-studio-team-services-2/" />
    <meta name="twitter:description" content="Overview In this walkthrough I will show&nbsp; you how to use Visual Studio Team Services with an existing Azure App Service project (specifically an Azure Web App).&nbsp; We will add a task to update/create the project database from a DACPAC file and enable CI (Continuous Integration). Sign up for Visual Studio Team Services&nbsp; Go to:..." />
    <meta name="twitter:image" content="/assets/images/2017/07/capture20170717092329860_thumb.png" />
    
categories:
  - Uncategorized
--- 

 

In this walkthrough I will show&nbsp; you how to use Visual Studio Team Services with an existing Azure App Service project (specifically an Azure Web App).&nbsp; We will add a task to update/create the project database from a DACPAC file and enable CI (Continuous Integration).

# Sign up for Visual Studio Team Services&nbsp; 

Go to: [https://www.visualstudio.com/team-services/](https://www.visualstudio.com/team-services/ "https://www.visualstudio.com/team-services/")&nbsp;&nbsp; There is a link at the bottom to use the cloud services for free!&nbsp; Sign up to start using Visual Studio Team Services with your development projects.

Use the same login you use for logging into Visual Studio and the integration will allow you to easily sync your projects to Visual Studio Team Services.

# Add your project to the Visual Studio Team Services from Visual Studio 2017

Open Visual Studio and your existing project.&nbsp; The bottom right of the IDE you will see the&nbsp; ‘Add to Source Control’ menu:

[<img loading="lazy" title="capture20170717092329860" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170717092329860" src="/assets/images/2017/07/capture20170717092329860_thumb.png" width="205" height="117" />](/assets/images/2017/07/capture20170717092329860.png)

NOTE:&nbsp; In Visual Studio 2015 the menu item is ‘Publish’.&nbsp; This will publish a Git Repo with the name of your project for you.

Choose ‘Git’:

[<img loading="lazy" title="capture20170714144019299" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170714144019299" src="/assets/images/2017/07/capture20170714144019299_thumb.png" width="244" height="151" />](/assets/images/2017/07/capture20170714144019299.png)

&nbsp;

Once you have done this, a Repo is created on your local machine that will allow you to develop and track your changes.&nbsp; You can save your changes often to this local Repo so that if you make a mistake, you can easily back out your changes and revert to an older version.&nbsp; Once you are ready to publish these changes for others to use you can Publish the Git Repo to Visual Studio Team Services.&nbsp; This will allow others to work on the same project at the same time, and then use the tools to merge the work you are all doing into a single master branch, ready to publish.

Initial Publish Git Repo to Visual Studio Team Services (select the Publish Git Repo button):

[<img loading="lazy" title="capture20170718085313452" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170718085313452" src="/assets/images/2017/07/capture20170718085313452_thumb.png" width="339" height="252" />](/assets/images/2017/07/capture20170718085313452.png)

Give your Repo a name or use the default which will be the project name and push ‘Publish repository’:

[<img loading="lazy" title="capture20170718090059374" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170718090059374" src="/assets/images/2017/07/capture20170718090059374_thumb.png" width="343" height="349" />](/assets/images/2017/07/capture20170718090059374.png)

You can click on the hyperlink to see the files up in Visual Studio Team Services:

[<img loading="lazy" title="capture20170718090305819" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170718090305819" src="/assets/images/2017/07/capture20170718090305819_thumb.png" width="345" height="197" />](/assets/images/2017/07/capture20170718090305819.png)

[<img loading="lazy" title="capture20170718090438193" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170718090438193" src="/assets/images/2017/07/capture20170718090438193_thumb.png" width="940" height="324" />](/assets/images/2017/07/capture20170718090438193.png)

When you are developing and you hit a milestone you should Sync your changes to the local Git repo.&nbsp; In this case I added a default.aspx page and you can see it is marked with a ‘+’ to indicate it is a new item added and the solution has a red check indicating it has changed:

[<img loading="lazy" title="capture20170718090735697" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170718090735697" src="/assets/images/2017/07/capture20170718090735697_thumb.png" width="370" height="256" />](/assets/images/2017/07/capture20170718090735697.png)

Another indicator is the pencil icon in the lower right side if the IDE.&nbsp; It indicates there are 4 changes.&nbsp; Click on that icon, and you will see the Changes panel of Team Explorer.&nbsp; Enter a commit message and click the ‘Commit All’ button:

[<img loading="lazy" title="capture20170718091221482" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170718091221482" src="/assets/images/2017/07/capture20170718091221482_thumb.png" width="323" height="374" />](/assets/images/2017/07/capture20170718091221482.png)

You will see the Commit is created local, and it gives you an option to Sync up to VSTS (Visual Studio Team Services).&nbsp; You can also see the up arrow icon at the bottom of the IDE indicates there is ‘1’ Commit local that has not been pushed up to VSTS as of yet.

[<img loading="lazy" title="capture20170718091305021" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170718091305021" src="/assets/images/2017/07/capture20170718091305021_thumb.png" width="326" height="398" />](/assets/images/2017/07/capture20170718091305021.png)

When you are ready to share your changes up on VSTS you can hit the commit icon (up arrow at bottom) or choose the Sync link and push your changes to VSTS.&nbsp; Choose the ‘Push’ link to push the Commit:

[<img loading="lazy" title="capture20170718091618722" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170718091618722" src="/assets/images/2017/07/capture20170718091618722_thumb.png" width="320" height="372" />](/assets/images/2017/07/capture20170718091618722.png)

And again you can go to VSTS and see the added files:

[<img loading="lazy" title="capture20170718091838003" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;paddin
g-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170718091838003" src="/assets/images/2017/07/capture20170718091838003_thumb.png" width="456" height="311" />](/assets/images/2017/07/capture20170718091838003.png)

# Publish from Visual Studio Team Services

Once you are ready to deploy your changes, ensure you have an Azure Web App Resource already defined to in the Azure Portal to deploy to.&nbsp; Then you can build and deploy your code from VSTS to your Azure Web App.

Click on the ‘Build & Release’ tab in VSTS and since you have no build definitions create a ‘New definition’:

[<img loading="lazy" title="capture20170718092320857" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170718092320857" src="/assets/images/2017/07/capture20170718092320857_thumb.png" width="479" height="302" />](/assets/images/2017/07/capture20170718092320857.png)

Select and Apply the Azure Web App template:

[<img loading="lazy" title="capture20170718092407872" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170718092407872" src="/assets/images/2017/07/capture20170718092407872_thumb.png" width="528" height="417" />](/assets/images/2017/07/capture20170718092407872.png)

Fill in all the required information.&nbsp; Note that you must Authorize and add your credentials to be able to access the subscription and App Service:

[<img loading="lazy" title="capture20170718092539696" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170718092539696" src="/assets/images/2017/07/capture20170718092539696_thumb.png" width="695" height="453" />](/assets/images/2017/07/capture20170718092539696.png)

Note the Default agent queue should be Hosted, or Hosted VS2017.&nbsp; I chose the latter because my project is a VS2017 solution:

[<img loading="lazy" title="capture20170718092651972" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170718092651972" src="/assets/images/2017/07/capture20170718092651972_thumb.png" width="418" height="394" />](/assets/images/2017/07/capture20170718092651972.png)

Choose ‘Save & queue’ and optionally add some text to the ‘Commit’ field and press the ‘Queue’ button:

[<img loading="lazy" title="capture20170718092719872" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;margin: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170718092719872" src="/assets/images/2017/07/capture20170718092719872_thumb.png" width="213" height="186" />](/assets/images/2017/07/capture20170718092719872.png)[<img loading="lazy" title="capture20170718092753465" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170718092753465" src="/assets/images/2017/07/capture20170718092753465_thumb.png" width="452" height="425" />](/assets/images/2017/07/capture20170718092753465.png)

This will queue the build and release for you.&nbsp; Clicking on the link for the build (or going to history) will allow you to monitor the progress on the console view:

[<img loading="lazy" title="capture20170718092807848" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170718092807848" src="/assets/images/2017/07/capture20170718092807848_thumb.png" width="244" height="58" />](/assets/images/2017/07/capture20170718092807848.png)&nbsp;[<img loading="lazy" title="capture20170718092846066" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170718092846066" src="/assets/images/2017/07/capture20170718092846066_thumb.png" width="560" height="560" />](/assets/images/2017/07/capture20170718092846066.png)

# 

# Update a Database from your Project

Now that we know the build and release cycle is working properly, we will add a DACPAC file to update the database during the build and release Task.&nbsp; I will leave it to you to ‘Bing’ how to create a DACPAC file.

### Once you have the DACPAC, you want to add it to your solution:

Create a folder in the root of your solution called ‘App_Data’.&nbsp; The name of this folder is very important as we will use this to exclude this folder in the Build process from being pushed out to the application:

[<img loading="lazy" title="capture20170718094431737" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170718094431737" src="/assets/images/2017/07/capture20170718094431737_thumb.png" width="363" height="276" />](/assets/images/2017/07/capture20170718094431737.png)

Locate the DACPAC file and add it to the App_Data folder choosing ‘Add, Existing item…’:

[<img loading="lazy" title="capture20170718095418790" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170718095418790" src="/assets/images/2017/07/capture20170718095418790_thumb.png" width="396" height="319" />](/assets/images/2017/07/capture20170718095418790.png)

Then commit these changes and push it to VSTS as you did above for Default.aspx.

### Modify the Build in VSTS to exclude the DACPAC file from the release to the App Service

In VSTS click on the ‘Build & Release’ tab and select the Build Definition we created.&nbsp; Then click the ‘Edit’ icon on the top right of the view:

&nbsp;

[<img loading="lazy" title="capture20170718095806304" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170718095806304" src="/assets/images/2017/07/capture20170718095806304_thumb.png" width="631" height="270" />](/assets/images/2017/07/capture20170718095806304.png)

Click on the ‘Azure App Service Deploy…” step of the process and open the ‘Additional Deployment Options’ and select the option to ‘Exclude Files from the App_Data Folder’.&nbsp; Remember that is the folder we put the DACPAC file.&nbsp; There is no need to deploy that file to the Azure Web App because we are going to add a step to update the Database from the Build/Release again in VSTS.

[<img loading="lazy" title="capture20170718100024458" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170718100024458" src="https://ms
dnshared.blob.core.windows.net/media/2017/07/capture20170718100024458_thumb.png" width="695" height="474" />](/assets/images/2017/07/capture20170718100024458.png)

&nbsp;

Add a Task to the Build Definition to Update the Database from the DACPAC file

[<img loading="lazy" title="capture20170718100757786" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170718100757786" src="/assets/images/2017/07/capture20170718100757786_thumb.png" width="581" height="360" />](/assets/images/2017/07/capture20170718100757786.png)

Fill in the required fields and change the Azure Connection Type to ‘Azure Resource Manager’ and then Authorize using your subscription (as you did before)

[<img loading="lazy" title="capture20170718125746442" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20170718125746442" src="/assets/images/2017/07/capture20170718125746442_thumb.png" width="440" height="282" />](/assets/images/2017/07/capture20170718125746442.png)

You can get the server name from the Azure Portal by looking up you database the (it is in the Overview):

[<img loading="lazy" title="capture20170718130031575" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20170718130031575" src="/assets/images/2017/07/capture20170718130031575_thumb.png" width="896" height="278" />](/assets/images/2017/07/capture20170718130031575.png)

And fill in the rest of the information:

[<img loading="lazy" title="capture20170718130305679" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20170718130305679" src="/assets/images/2017/07/capture20170718130305679_thumb.png" width="387" height="560" />](/assets/images/2017/07/capture20170718130305679.png)

Finally select the DACPAC file from the path of you repository by hitting the ‘…’

[<img loading="lazy" title="capture20170718130533621" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20170718130533621" src="/assets/images/2017/07/capture20170718130533621_thumb.png" width="511" height="475" />](/assets/images/2017/07/capture20170718130533621.png)

Hit ‘Save and Queue’ again and Queue this build

At this point I got an error!

[<img loading="lazy" title="capture20170718130729625" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20170718130729625" src="/assets/images/2017/07/capture20170718130729625_thumb.png" width="741" height="151" />](/assets/images/2017/07/capture20170718130729625.png)

This is complaining that the Hosted VS 2017 agent does not support sqlpackage (that is all I added).&nbsp; The fix is to edit the build again, click on the top Process tab on the left side and set the ‘Default agent queue to ‘Hosted’.

[<img loading="lazy" title="capture20170718131041207" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20170718131041207" src="/assets/images/2017/07/capture20170718131041207_thumb.png" width="579" height="227" />](/assets/images/2017/07/capture20170718131041207.png)

Save and queue, and click on the build link as before to see the results and you will see the SQL Task:

[<img loading="lazy" title="capture20170718132331556" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20170718132331556" src="/assets/images/2017/07/capture20170718132331556_thumb.png" width="739" height="338" />](/assets/images/2017/07/capture20170718132331556.png)

&nbsp;

# Enable CI

For my example I want to have VSTS build and release to my Azure Web App whenever someone pushes changes in the Master branch.&nbsp; See the VSTS site for more options and examples.

This is as simple as Editing the Build definition again and navigating to the Triggers section.&nbsp; Here you simply choose to Enable the trigger, use the defaults and Save the Definition:

[<img loading="lazy" title="capture20170718133247128" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20170718133247128" src="/assets/images/2017/07/capture20170718133247128_thumb.png" width="463" height="495" />](/assets/images/2017/07/capture20170718133247128.png)

&nbsp;

# Conclusion

I hope this Walkthrough helps you set up your first Azure Web App using Visual Studio Team Services.&nbsp; Of course there are other ways to do what I showed you here, but this will get you started.

# Additional Links

<a title="https://www.visualstudio.com/team-services/" href="https://www.visualstudio.com/team-services/" target="_blank">https://www.visualstudio.com/team-services/</a>

<a title="https://www.visualstudio.com/learn-git/" href="https://www.visualstudio.com/learn-git/" target="_blank">https://www.visualstudio.com/learn-git/</a>