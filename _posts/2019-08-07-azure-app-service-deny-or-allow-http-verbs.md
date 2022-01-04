---
id: 5549
title: 'Azure App Service&ndash;Deny or Allow HTTP Verbs'
date: 2019-08-07T11:57:54-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=5549
permalink: /2019/08/07/azure-app-service-deny-or-allow-http-verbs/
categories:
  - Uncategorized
---
You may want to restrict what verbs you allow to your web apps in Azure App Services.&nbsp; The way you do this is really no different than how you would do this for these web servers on premise or in a VM!

## Windows based Web Apps

This is super simple!&nbsp; Just add to the web config what rules you wish to apply.&nbsp; For example to restrict everything but allow GET and POST you can add this entry (or update it if it already exists):

<configuration>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <system.webServer>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <security>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <requestFiltering>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <verbs allowUnlisted=&#8221;false&#8221;>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <add verb=&#8221;GET&#8221; allowed=&#8221;true&#8221; />  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <add verb=&#8221;POST&#8221; allowed=&#8221;true&#8221; />  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; <add verb=&#8221;HEAD&#8221; allowed=&#8221;true&#8221; />  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </verbs>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </requestFiltering>  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; </security>  
&nbsp;&nbsp;&nbsp; </system.webServer>

Refence for these settings: <a href="https://docs.microsoft.com/en-us/iis/configuration/system.webserver/security/requestfiltering/verbs/index#configuration" target="_blank" rel="noopener noreferrer">IIS Request Filtering &#8211; Verbs <verbs></a>

You can do this temporarily by editing this file in Kudu but this should be part of your project so when you deploy new versions you do not overwrite your changes!

## Linux based Web Apps

Again, very easy once you realize we are simply hosting a Web Server for you.&nbsp; For Linux based Web Apps we are hosting your code in a Docker Container.&nbsp; You simply need to configure that container just like you would anywhere else.

For example when running PHP the image uses Apache so you simply add the commands to Apache just like you would anywhere else.



## PHP 

You can run a custom startup script like I detail here: <http://jsandersblog.azurewebsites.net/2019/08/06/custom-startup-script-for-php-azure-app-service-linux/>&nbsp; Specifically to set the allowed headers you can use the Rewrite engine.

Follow the instructions for the script file but use this for the contents:

echo &#8220;RewriteEngine On&#8221; >> /etc/apache2/apache2.conf  
echo &#8220;RewriteCond %{REQUEST_METHOD} !^(GET|POST|HEAD)&#8221; >> /etc/apache2/apache2.conf  
echo &#8220;RewriteRule .* &#8211; [R=405,L]&#8221; >> /etc/apache2/apache2.conf

/usr/sbin/apache2ctl -D FOREGROUND

#### <font style="font-weight: bold;">Step by Step</font>

Go to the SSH console of your Azure App Service.

[<img loading="lazy" width="443" height="244" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/08/image_thumb.png" border="0" />](/assets/images/2019/08/image.png)

Change to the /home directory and create a startup.sh file

Put this in the file (using VIM for example) and save it

root@96a1004e60a7:/home# cat startup.sh  
echo &#8220;RewriteEngine On&#8221; >> /etc/apache2/apache2.conf  
echo &#8220;RewriteCond %{REQUEST_METHOD} !^(GET|POST|HEAD)&#8221; >> /etc/apache2/apache2.conf  
echo &#8220;RewriteRule .* &#8211; [R=405,L]&#8221; >> /etc/apache2/apache2.conf

/usr/sbin/apache2ctl -D FOREGROUND

This is what the startup file should look like:

root@6a6fb0697cf0:/home# cat startup.sh  
echo &#8220;RewriteEngine On&#8221; >> /etc/apache2/apache2.conf  
echo &#8220;RewriteCond %{REQUEST_METHOD} !^(GET|POST|HEAD)&#8221; >> /etc/apache2/apache2.conf  
echo &#8220;RewriteRule .* &#8211; [R=405,L]&#8221; >> /etc/apache2/apache2.conf

/usr/sbin/apache2ctl -D FOREGROUND  
root@6a6fb0697cf0:/home#



Then set this as the startup script in the general settings and save:

[<img loading="lazy" width="421" height="251" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/08/image_thumb-1.png" border="0" />](/assets/images/2019/08/image-1.png)



## Node

For Node, the easiest way to accomplish this without having to create your own custom container is to simply do this in your code:



<pre>const allowedMethods = ['GET','HEAD','POST'];

function onrequest(req, res) {
  if (!allowedMethods.includes(req.method))
    return res.end(405, 'Method Not Allowed');
  // ...
}</pre>



## 

## WordPress/Drupal



For wordpress/drupal, we allow you to add a custom nginx configuration in the /home/ folder. Add this line to server -> location directive: 

limit_except GET POST HEAD {

&nbsp;&nbsp;&nbsp; deny&nbsp; all;

}

## Java

Modify your application web.xml and add this

<security-constraint>  
<web-resource-collection>  
<url-pattern>/*</url-pattern>  
<http-method>GET</http-method>  
<http-method>POST</http-method>  
</web-resource-collection>  
<auth-constraint>  
<role-name>admin</role-name>  
</auth-constraint>  
</security-constraint>



## 

## Other environments

Similarly you would modify any of the other stacks, but substituting the appropriate commands based on the images web server used.

The current images are stored here: <https://github.com/Azure-App-Service?q=template>

You need to find your image and them based on that image type, simply add the commands in your code to deny the headers you wish.

For example:&nbsp; Ruby&nbsp; <https://github.com/Azure-App-Service/ruby-template>

You can find in master.json the versions supported:

<https://github.com/Azure-App-Service/ruby-template/blob/master/blessedImageConfig-master.json>



Let’s say you want to use the 2.3.8 version as you see it is there.&nbsp; This is running ruby on rails so lookup that environment and implement the filtering in your code.&nbsp; In this example you can use the request object:

[https://edgeguides.rubyonrails.org/action\_controller\_overview.html#the-request-and-response-objects](https://edgeguides.rubyonrails.org/action_controller_overview.html#the-request-and-response-objects)

and look at the Method.

You would probably want to do this in your application controller to catch all the requests:

[https://guides.rubyonrails.org/action\_controller\_overview.html](https://guides.rubyonrails.org/action_controller_overview.html)





## Custom image option

Finally you can also use any of the blessed images we use for these stacks and fork the container and configure it appropriately:

<https://docs.microsoft.com/en-us/azure/app-service/containers/app-service-linux-faq#built-in-images>





Let me know if you used this successfully!