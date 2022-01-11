Application Insights is a powerful tool to visualize what is happening with your application.&nbsp; This quick query shows how to chart when instances are added and removed

# Walkthrough

Enable application insights for your app using the wizard in the portal or follow our documentation: <a href="https://docs.microsoft.com/en-us/azure/azure-monitor/app/azure-web-apps?tabs=net#enable-agent-based-monitoring" target="_blank" rel="noopener noreferrer">https://docs.microsoft.com/en-us/azure/azure-monitor/app/azure-web-apps?tabs=net#enable-agent-based-monitoring</a>

Open Application Insights from the app of concern from the portal and use a time based query similar to this

> customMetrics
> 
> | where timestamp >= ago(7d) and timestamp < ago(5m)
> 
> | where name == &#8220;HeartbeatState&#8221;
> 
> | summarize [&#8216;UniqueInstanceCount&#8217;] = dcount(cloud_RoleInstance) by bin(timestamp,5m)
> 
> | order by timestamp desc
> 
> | render timechart 



[<img loading="lazy" width="1220" height="536" title="appinsights" style="display: inline; background-image: none;" alt="appinsights" src="/assets/images/2020/05/appinsights_thumb.jpg" border="0" />](/assets/images/2020/05/appinsights.jpg)



Then you can use ‘Pin to dashboard’ to save this view!

Note that the default time period for charts will be 24 hours but you can change this by clicking on the …&nbsp; and setting a custom time range:

[<img loading="lazy" width="462" height="573" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2020/05/image_thumb.png" border="0" />](/assets/images/2020/05/image.png)



Drop me a note if you found this useful!



Jeff