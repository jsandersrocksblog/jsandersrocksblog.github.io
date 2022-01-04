---
id: 5395
title: 'Azure App Service on Linux&ndash;Copy files from container that does not use WEBSITES_ENABLE_APP_SERVICE_STORAGE'
date: 2019-02-04T16:18:07-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=5395
permalink: /2019/02/04/azure-app-service-on-linux-copy-files-from-container-that-does-not-use-websites_enable_app_service_storage/
categories:
  - Uncategorized
---
 

If you need to move files from a container and you are not using WEBSITES\_ENABLE\_APP\_SERVICE\_STORAGE, you will notice you cannot see the files when you SSH into the Kudu container.&nbsp; In order to get these files into Kudu to easily transfer them you can use the linux tool ‘ncftp’.&nbsp; 

# Steps

In this example we will get the entire wwwroot directory.&nbsp; SSH into the container and install ncftp and zip as follows:

i. SSH into the Docker container and run the following to get into the correct directory and install zip and ncftp

cd /home/site/wwwroot  
apk update  
apk add zip  
apk add ncftp  
zip -r wwwroot.zip .&nbsp; (don&#8217;t forget the trailing &#8220;.&#8221;).

ii. In the Azure Portal, go to the Overview blade for the app and press &#8220;Get publish profile&#8221;  
iii. Find the username and password as well as the ftp site in that publish profile.&nbsp; Make sure you add the username in a single quote when connecting using ncftp as shown below.

ncftp -u &#8216;jefflinuxtest\$jefflinuxtest&#8217; <ftp://waws-prod-bay-081.ftp.azurewebsites.windows.net> site

iv. Enter your password then perform the following.

cd site/wwwroot  
put wwwroot.zip.

v. Sample output provided below.

c6b6f3bd43fd:/home/site/wwwroot# ncftp -u &#8216;jefflinuxtest\$jefflinuxtest&#8217; ftp  
://waws-prod-bay-081.ftp.azurewebsites.windows.net site  
NcFTP 3.2.6 (Dec 04, 2016) by Mike Gleason (<http://www.NcFTP.com/contact/)>.  
Connecting to 40.118.171.137&#8230;  
Microsoft FTP Service  
Logging in&#8230;  
Password requested by 40.118.171.137 for user &#8220;jefflinuxtest\$jefflinuxtest&#8221;.

&nbsp;&nbsp;&nbsp; Password required

Password: \***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***\***

User logged in.  
Logged in to waws-prod-bay-081.ftp.azurewebsites.windows.net.  
Current remote directory is /.  
ncftp / > cd site/wwwroot  
ncftp /site/wwwroot > put wwwroot.zip  
wwwroot.zip:&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 47.61 MB&nbsp;&nbsp; 42.56 MB/s  
ncftp /site > exit



&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Thank you for using NcFTP Client.  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; If you find it useful, please consider making a donation!  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <http://www.ncftp.com/ncftp/donate.html>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  
vi. Check that /home/site contains the wwwroot.zip file using KUDU/Bash.

vii.&nbsp; Now simply use the vfs feature of kudu to download the files!&nbsp;&nbsp; [https://github.com/projectkudu/kudu/wiki/REST-API](https://github.com/projectkudu/kudu/wiki/REST-API "https://github.com/projectkudu/kudu/wiki/REST-API")&nbsp;&nbsp;&nbsp; In this example go to [https://jsanderscontainerl.scm.azurewebsites.net/api/vfs/site/wwwroot/wwwroot.zip](https://jsanderscontainerl.scm.azurewebsites.net/api/vfs/site/wwwroot/wwwroot.zip "https://jsanderscontainerl.scm.azurewebsites.net/api/vfs/site/wwwroot/") in a browser and you can download the file!