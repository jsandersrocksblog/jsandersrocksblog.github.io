---
id: 5799
title: Customize Azure Cloud Shell Bash Environment
date: 2021-09-24T09:58:39-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=5799
permalink: /2021/09/24/customize-azure-cloud-shell-bash-environment/
categories:
  - Uncategorized
---
I wanted to customize my Azure Cloud Shell Bash Environment to set the active subscription and define bash aliases at start up.&nbsp; I could not find a good reference so here is how to do some simple things.

## Bash file structure in Azure Cloud Shell

When your start the Cloud Shell it will prompt you to create an Azure Storage to persist state.&nbsp; After that the /home directory will have the files you place in it.&nbsp; Doing ls – all will show you the hidden files:

[<img loading="lazy" width="723" height="307" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/09/image_thumb-19.png" border="0" />](/assets/images/2021/09/image-19.png)

Inspecting .bashrc with code (type code .bashrc) I saw I could add a file .bash_aliases and it would be read on startup if it exists:

[<img loading="lazy" width="555" height="447" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/09/image_thumb-20.png" border="0" />](/assets/images/2021/09/image-20.png)

at first I created the file “.bash_aliases” and put my alias in there but decided instead to follow this pattern and create a file startup.sh to add some other commands to execute at startup.&nbsp; I added the lines you see above:

if [ -f ~/startup.sh ]; then  
&nbsp;&nbsp;&nbsp;&nbsp; . ~/startup.sh  
fi

and then created and edited a file “startup.sh”:

[<img loading="lazy" width="550" height="245" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/09/image_thumb-21.png" border="0" />](/assets/images/2021/09/image-21.png)

Closing and starting the Azure Cloud Shell now runs this and sets up my environment the way I want!

[<img loading="lazy" width="647" height="227" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2021/09/image_thumb-22.png" border="0" />](/assets/images/2021/09/image-22.png)