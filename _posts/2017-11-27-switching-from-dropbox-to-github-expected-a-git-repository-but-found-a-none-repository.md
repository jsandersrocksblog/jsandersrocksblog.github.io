If you have dropbox selected for a deployment option and want to switch to github you may get the error message:&nbsp; Expected a &#8216;Git&#8217; repository but found a &#8216;None&#8217; repository at path &#8216;D:\\home\\site\\wwwroot&#8217;.

## 

## Fix

To switch to Github you need to remove the Application Setting (in Application Settings of the Azure portal)&nbsp; SCM\_NO\_REPOSITORY.&nbsp; Click on the ‘…’ of that setting and choose ‘Delete’

[<img loading="lazy" title="capture20171127152623687" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20171127152623687" src="/assets/images/2017/11/capture20171127152623687_thumb.png" width="895" height="97" />](/assets/images/2017/11/capture20171127152623687.png)

Ref: [https://github.com/projectkudu/kudu/wiki/Deploying-inplace-and-without-repository](https://github.com/projectkudu/kudu/wiki/Deploying-inplace-and-without-repository "https://github.com/projectkudu/kudu/wiki/Deploying-inplace-and-without-repository")&nbsp; &#8211; search on Dropbox