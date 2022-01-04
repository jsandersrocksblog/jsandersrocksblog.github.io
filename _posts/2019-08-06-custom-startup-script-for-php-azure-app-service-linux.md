---
id: 5543
title: 'Custom Startup script for PHP &#8211; Azure App Service Linux'
date: 2019-08-06T12:14:47-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=5543
permalink: /2019/08/06/custom-startup-script-for-php-azure-app-service-linux/
categories:
  - Uncategorized
---
You have an option to create a custom startup script when using our provided (commonly referred to as ‘blessed’) images for PHP

## Instructions

Create a Bash Script &#8211; 

In this example, I&#8217;ll be enabling Apache&#8217;s Header module, updating the Apache configuration file to add a new header and remove the &#8220;X-Powered-By&#8221; header, and then starting Apache.

  1. Using SSH, go to &#8220;/home&#8221; directory and create a file called &#8220;test.sh&#8221; using your favorite editor.
    
      * Add following content.</ol> 
    
    #!/bin/bash
    
    a2enmod headers
    
    echo &#8220;Header set MyHeader \&#8221;%D %t&#8221;\&#8221; >> /etc/apache2/apache2.conf
    
    echo &#8220;Header always unset \&#8221;X-Powered-By\&#8221;&#8221; >> /etc/apache2/apache2.conf
    
    echo &#8220;Header unset \&#8221;X-Powered-By\&#8221;&#8221; >> /etc/apache2/apache2.conf
    
    /usr/sbin/apache2ctl -D FOREGROUND
    
    <ol start="3">
      <li>
        <p>
          Save the file.
        </p>
      </li>
    </ol>
    
    Another example but with MySQL client installed as well.
    
    #!/bin/bash
    
    a2enmod headers
    
    echo &#8220;Header set MyHeader \&#8221;%D %t&#8221;\&#8221; >> /etc/apache2/apache2.conf
    
    echo &#8220;Header always unset \&#8221;X-Powered-By\&#8221;&#8221; >> /etc/apache2/apache2.conf
    
    echo &#8220;Header unset \&#8221;X-Powered-By\&#8221;&#8221; >> /etc/apache2/apache2.conf
    
    apt-get update
    
    apt-get install mysql-client -y
    
    /usr/sbin/apache2ctl -D FOREGROUND
    
    NOTE:&nbsp; Always ensure that &#8220;/usr/sbin/apache2ctl -D FOREGROUND&#8221; is in the script or your container will not start.
    
    Saving the Changes &#8211;
    
      1. In the Azure Portal, go to Configuration then the &#8220;General settings&#8221; section for your PHP Linux App.
        
          * In the &#8220;Startup Command&#8221; section, add &#8220;/home/test.sh&#8221; and press save.</ol> 
        
        Testing the Changes &#8211; 
        
        Prior to updating the Application Settings for our App, the headers returned for any calls made to my PHP site returned the following highlighted header.
        
        Content-Encoding:  
        gzip
        
        Content-Length:  
        29220
        
        Content-Type:  
        text/html; charset=UTF-8
        
        Date:  
        Tue, 02 Apr 2019 22:09:01 GMT
        
        Server:  
        Apache
        
        Vary:  
        Accept-Encoding
        
        X-Powered-By:  
        PHP/7.0.33
        
        After the changes, you can see the new header and the removed header.
        
        Content-Encoding:  
        gzip
        
        Content-Length:  
        29221
        
        Content-Type:  
        text/html; charset=UTF-8
        
        Date:  
        Tue, 02 Apr 2019 22:18:46 GMT
        
        MyHeader:  
        D=865306 t=1554243525454549
        
        Server:  
        Apache
        
        Vary:  
        Accept-Encoding
        
        X-Content-Type-Options:  
        nosniff
        
        FAQ&#8217;s/Troubleshooting
        
        Adding a &#8220;Command&#8221; In Startup File Prevents My Site from Starting &#8211; 
        
        You&#8217;ll always need to use a shell script if you intend to make any adjustments to our blessed image.&nbsp; For example, if a user tries to add just &#8220;a2enmod headers&#8221;, only this command will run.&nbsp; This will be an issue because Apache also needs to startup.&nbsp;&nbsp; So any changes will need to be in a shell script and end with &#8220;/usr/sbin/apache2ctl -D FOREGROUND&#8221; so that Apache can startup after the changes are made.
        
        What Happens By Default?
        
        If no &#8220;Startup File&#8221; is specified, the default startup command will be &#8220;/usr/sbin/apache2ctl -D FOREGROUND&#8221;.
        
        How Can I Troubleshoot My Custom Script?
        
        Enable Diagnostic Logs
        
        Enable Diagnostic Logs to see the startup command you are specifying. Information regarding the shell script will also be printed and can normally help with troubleshooting.&nbsp; Inspect the shell script if further troubleshooting is necessary.&nbsp; Example output below.
        
        2019-04-02T22:10:20.124899804Z&nbsp;&nbsp; \_____&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  
        2019-04-02T22:10:20.124950905Z&nbsp;&nbsp; /&nbsp; \_&nbsp; \ \_\___\___\___ \___\___\_\\_\_&nbsp;&nbsp; \_\___  
        2019-04-02T22:10:20.124961705Z&nbsp; /&nbsp; /\_\&nbsp; \\_\_\_&nbsp;&nbsp; /&nbsp; |&nbsp; \_&nbsp; \_\_ \_/ __ \  
        2019-04-02T22:10:20.124966305Z /&nbsp;&nbsp;&nbsp; |&nbsp;&nbsp;&nbsp; \/&nbsp;&nbsp;&nbsp; /|&nbsp; |&nbsp; /|&nbsp; | \/\&nbsp; \___/  
        2019-04-02T22:10:20.124970905Z \_\_\\_\_|\_\_&nbsp; /\_____ \_\_\\_\_/ |\_\_|&nbsp;&nbsp;&nbsp; \___&nbsp; >  
        2019-04-02T22:10:20.124975605Z&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; \/&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; \/&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; \/  
        2019-04-02T22:10:20.124979905Z A P P&nbsp;&nbsp; S E R V I C E&nbsp;&nbsp; O N&nbsp;&nbsp; L I N U X  
        2019-04-02T22:10:20.124984005Z  
        2019-04-02T22:10:20.124988005Z Documentation: [http://aka.ms/webapp-linux  
](http://aka.ms/webapp-linux) 2019-04-02T22:10:20.124991905Z PHP quickstart: [https://aka.ms/php-qs  
](https://aka.ms/php-qs) 2019-04-02T22:10:20.124996005Z PHP version : 7.0.33  
        2019-04-02T22:10:20.316877912Z Starting OpenBSD Secure Shell server: sshd.  
        2019-04-02T22:10:20.316930912Z Running /home/test.sh  
        2019-04-02T22:10:20.478652555Z Enabling module headers.  
        2019-04-02T22:10:20.509020720Z To activate the new configuration, you need to run:  
        2019-04-02T22:10:20.509035720Z&nbsp;&nbsp; service apache2 restart  
        2019-04-02T22:10:20.794898927Z AH00526: Syntax error on line 63 of /etc/apache2/apache2.conf:  
        2019-04-02T22:10:20.797728533Z Unknown parameter: %t  
        2019-04-02T22:10:20.813059165Z Action &#8216;-D FOREGROUND&#8217; failed.  
        2019-04-02T22:10:20.815994072Z The Apache error log may have more information.
        
        NOTE: Always make sure that the script is starting Apache as highlighted below.
        
        2019-04-02T22:18:32.179448369Z&nbsp;&nbsp; \_____&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  
        2019-04-02T22:18:32.179504969Z&nbsp;&nbsp; /&nbsp; \_&nbsp; \ \_\___\___\___ \___\___\_\\_\_&nbsp;&nbsp; \_\___  
        2019-04-02T22:18:32.179511669Z&nbsp; /&nbsp; /\_\&nbsp; \\_\_\_&nbsp;&nbsp; /&nbsp; |&nbsp; \_&nbsp; \_\_ \_/ __ \  
        2019-04-02T22:18:32.179515769Z /&nbsp;&nbsp;&nbsp; |&nbsp;&nbsp;&nbsp; \/&nbsp;&nbsp;&nbsp; /|&nbsp; |&nbsp; /|&nbsp; | \/\&nbsp; \___/  
        2019-04-02T22:18:32.179519669Z \_\_\\_\_|\_\_&nbsp; /\_____ \_\_\\_\_/ |\_\_|&nbsp;&nbsp;&nbsp; \___&nbsp; >  
        2019-04-02T22:18:32.179523769Z&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; \/&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; \/&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; \/  
        2019-04-02T22:18:32.179527569Z A P P&nbsp;&nbsp; S E R V I C E&nbsp;&nbsp; O N&nbsp;&nbsp; L I N U X  
        2019-04-02T22:18:32.179531370Z  
        2019-04-02T22:18:32.179535070Z Documentation: [http://aka.ms/webapp-linux  
](http://aka.ms/webapp-linux) 2019-04-02T22:18:32.179539370Z PHP quickstart: [https://aka.ms/php-qs  
](https://aka.ms/php-qs) 2019-04-02T22:18:32.179543070Z PHP version : 7.0.33  
        2019-04-02T22:18:32.787322622Z Starting OpenBSD Secure Shell server: sshd.  
        2019-04-02T22:18:32.909041713Z Running /home/test.sh  
        2019-04-02T22:18:33.547386039Z Enabling module headers.  
        2019-04-02T22:18:33.636235852Z To activate the new configuration, you need to run:  
        2019-04-02T22:18:33.636252352Z&nbsp;&nbsp; service apache2 restart  
        2019-04-02T22:18:34.223869056Z AH00558: apache2: Could not reliably determine the server&#8217;s fully qualified domain name, using 11.0.3.3. Set the &#8216;ServerName&#8217; directive globally to suppress this message  
        2019-04-02T22:18:34.293904223Z AH00558: apache2: Could not reliably determine the server&#8217;s fully qualified domain name, using 11.0.3.3. Set the &#8216;ServerName&#8217; directive globally to suppress this message  
        2019-04-02T22:18:34.780720587Z \[Tue Apr 02 22:18:34.773847 2019\] \[mpm_prefork:notice\] [pid 52] AH00163: Apache/2.4.25 (Debian) PHP/7.0.33 configured &#8212; resuming normal operations  
        2019-04-02T22:18:34.793733818Z \[Tue Apr 02 22:18:34.793676 2019\] \[core:notice\] [pid 52] AH00094: Command line: &#8216;/usr/sbin/apache2 -D FOREGROUND&#8217;
        
        Test the Shell Script using SSH
        
          1. Remove the shell script from the Application Settings.
            
              * After the App container restarts, SSH into the container using KUDU or Remote SSH.
                
                  * Locate the script and run &#8220;bash <script_name>&#8221;
                    
                      * Reload Apache by running &#8220;service apache2 reload&#8221; to test changes affecting Apache.
                        
                          * If the script is installing packages, check to see if those packages are installed.</ol> 
                        
                        Creating a Shell Script on Windows
                        
                          1. Creating a shell script using a text editor on Windows will likely not be formatted correctly since they use different end of line characters to Unix/Linux systems.&nbsp; One way to workaround this is to use Notepad++ -> Edit Menu -> EOL Conversion -> Unix.
                        
                        
                        
                        Let me know if this helped you!