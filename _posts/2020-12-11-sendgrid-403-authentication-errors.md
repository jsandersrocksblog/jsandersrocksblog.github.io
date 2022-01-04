---
id: 5679
title: SendGrid 403 authentication Errors
date: 2020-12-11T09:24:23-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/?p=5679
permalink: /2020/12/11/sendgrid-403-authentication-errors/
categories:
  - Uncategorized
---
SendGrid &#8211; Stopped sending emails due to SendGrid changing authentication requirements for the Sender of the email

## Background

SendGrid changed how they authenticate and require the sender address to be verified.

This is not an Microsoft issue.&nbsp; SendGrid is a 3<sup>rd</sup> party and solely supported by SendGrid.&nbsp; You can go to your SendGrid dashboard and contact SendGrid for additional support.

## Solution

How I fixed it…

Found the from email used in my app.

From the Azure Portal (using my default browser) navigated to the SendGrid account and then manage the SendGrid dashboard.

Followed the instructions to set up&nbsp; ‘Single Sender Verification’ using that email from my app

Sent the email for verification (it went to my junk folder) and clicked on the verify email. Since my browser is open to the SendGrid dashboard still it authenticated with out me having to try and log into the SendGrid portal

[<img loading="lazy" width="777" height="159" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2020/12/image_thumb.png" border="0" />](/assets/images/2020/12/image.png)

Sent a test mail from the app and it worked fine.

Any other questions? Ask SendGrid

## 

## More info

<a href="https://sendgrid.com/docs/ui/sending-email/senders/" target="_blank" rel="noopener noreferrer">Senders | SendGrid Documentation</a>