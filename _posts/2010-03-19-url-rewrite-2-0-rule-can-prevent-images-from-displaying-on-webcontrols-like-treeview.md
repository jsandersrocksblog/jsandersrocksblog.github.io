I was excited to try URL Rewrite to create some rules on my internal web site.&nbsp; I added a rule to map a query string like <http://mysite/treepage.aspx?nodeName=RedColors> to <http://mysite/RedColors> .&nbsp; After doing this I found that the images of the treeview web control now did not display.&nbsp; I enabled FREB tracing and found that this rule was translating webresource.axd improperly:

<samp><rule name=&#8221;RewriteUserFriendlyURL1&#8243; stopProcessing=&#8221;true&#8221;><br />&nbsp; <match url=&#8221;^([^/]+)/?$&#8221; /><br />&nbsp; <conditions><br />&nbsp;&nbsp;&nbsp; <add input=&#8221;{REQUEST_FILENAME}&#8221; matchType=&#8221;IsFile&#8221; negate=&#8221;true&#8221; /><br />&nbsp;&nbsp;&nbsp; <add input=&#8221;{REQUEST_FILENAME}&#8221; matchType=&#8221;IsDirectory&#8221; negate=&#8221;true&#8221; /><br /></samp> 

RequestURL&nbsp;&nbsp;&nbsp; <http://mysite:80/WebResource.axd?d=zGZU6qcW6fzAgYe-oI85v1qoiSgWelpv1EkImgNZdKA1&t=633802488069218315> 

RequestURL&nbsp;&nbsp;&nbsp; <http://mysite:80/treepage.aspx?nodeName=WebResource.axd&d=zGZU6qcW6fzAgYe-oI85v1qoiSgWelpv1EkImgNZdKA1&t=633802488069218315> 

Since the rule saw the ‘?’ char it was trying to map it.

To solve this add a rule to exclude processing of .axd files:

<samp><rule name=&#8221;RewriteUserFriendlyURL1&#8243; stopProcessing=&#8221;true&#8221;><br />&nbsp; <match url=&#8221;^([^/]+)/?$&#8221; /><br />&nbsp; <conditions><br />&nbsp;&nbsp;&nbsp; <add input=&#8221;{REQUEST_FILENAME}&#8221; matchType=&#8221;IsFile&#8221; negate=&#8221;true&#8221; /><br />&nbsp;&nbsp;&nbsp; <add input=&#8221;{REQUEST_FILENAME}&#8221; matchType=&#8221;IsDirectory&#8221; negate=&#8221;true&#8221; /><br />&nbsp;&nbsp;&nbsp; <!&#8211;&nbsp; The following condition prevents rule from rewriting requests to .axd files &#8211;><br />&nbsp;&nbsp;&nbsp; <add input=&#8221;{URL}&#8221; negate=&#8221;true&#8221; pattern=&#8221;\.axd$&#8221; /><br />&nbsp; </conditions><br /></samp> 

&nbsp;

Please let me know if you found this Post useful and if it solved your problem!