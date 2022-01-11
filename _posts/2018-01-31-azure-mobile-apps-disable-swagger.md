

The Azure Mobile Apps quickstarts can support Swagger.&nbsp; What if you want to disable this?&nbsp; This walkthrough shows you where the Swagger routes come from and how to remove them

## Walkthrough – Node.js backend

The Node.js implementation is simply a property.&nbsp; All you need to do is remove the attribute in your code.&nbsp; For example, if you are simply developing in the portal you can use the App Service Editor.&nbsp; In your app chose ‘App Service Editor’ and hit go (pro tip shortcut:&nbsp; It is simply https://<the name of your app>.scm.azurewebsites.net/dev/&nbsp; “

[<img loading="lazy" title="capture20180131095116230" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20180131095116230" src="/assets/images/2018/01/capture20180131095116230_thumb.png" width="500" height="335" />](/assets/images/2018/01/capture20180131095116230.png)

Then navigate to the wwwroot/app.js file and change the existing entry _swagger: true_ to _swagger: false_ (the change will automatically be saved and restart the app):

[<img loading="lazy" title="capture20180131095511742" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20180131095511742" src="/assets/images/2018/01/capture20180131095511742_thumb.png" width="507" height="355" />](/assets/images/2018/01/capture20180131095511742.png)

If you are using source control, simply make the change in app.js to set swagger: false and push you changes to the app!

&nbsp;

## Walkthrough – C# backend

C# does not include swagger by default so you would have had to added it.&nbsp; If you need to remove it, simply remove the code configuring swagger.&nbsp; Example remove the call to ConfigureSwagger highlighted below:

[<img loading="lazy" title="capture20180131101259135" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="capture20180131101259135" src="/assets/images/2018/01/capture20180131101259135_thumb.png" width="244" height="220" />](/assets/images/2018/01/capture20180131101259135.png)

&nbsp;

## Conclusion

Swagger is useful but you don’t need it most cases.&nbsp; Let me know if you found this useful!

C# sample using swagger Ref: <a title="https://github.com/Azure/azure-mobile-apps-net-server/tree/master/samples/SampleApp" href="https://github.com/Azure/azure-mobile-apps-net-server/tree/master/samples/SampleApp" target="_blank">https://github.com/Azure/azure-mobile-apps-net-server/tree/master/samples/SampleApp</a>