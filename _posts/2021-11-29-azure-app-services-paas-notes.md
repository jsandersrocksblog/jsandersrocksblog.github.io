 

People moving from an on-premise to Cloud implementation sometimes have difficulty understanding they do not have control over the underlying platform updates to their PaaS resources.&nbsp; Azure App Services is a Platform as a Service (PaaS).&nbsp; Simply put, a PaaS service gives you a platform to host your code and the provider updates the platform whenever necessary.&nbsp; You cannot control when the underlying platform gets updated nor what gets updated.&nbsp; You rely on the provider of the platform to handle security and platform updates and trust that the platform simply will work.&nbsp; There are many advantages to a PaaS environment that I will not cover here.&nbsp; We have learning resources that cover all the basics of Azure here: [https://docs.microsoft.com/en-us/learn/paths/az-900-describe-cloud-concepts/?wt.mc\_id=acom\_newtoazure\_webpage\_azuremktg](https://docs.microsoft.com/en-us/learn/paths/az-900-describe-cloud-concepts/?wt.mc_id=acom_newtoazure_webpage_azuremktg "https://docs.microsoft.com/en-us/learn/paths/az-900-describe-cloud-concepts/?wt.mc_id=acom_newtoazure_webpage_azuremktg")



## Details

What is PaaS?&nbsp; [https://azure.microsoft.com/en-us/overview/what-is-paas/](https://azure.microsoft.com/en-us/overview/what-is-paas/ "https://azure.microsoft.com/en-us/overview/what-is-paas/").

How to choose between different architectures? <https://docs.microsoft.com/en-us/azure/architecture/guide/technology-choices/compute-decision-tree#understand-the-hosting-models>

How does the OS and runtime get patched for App Services?&nbsp; <https://docs.microsoft.com/en-us/azure/app-service/overview-patch-os-runtime>

Demystifying the magic behind App Service OS updates: [https://azure.github.io/AppService/2018/01/18/Demystifying-the-magic-behind-App-Service-OS-updates.html](https://azure.github.io/AppService/2018/01/18/Demystifying-the-magic-behind-App-Service-OS-updates.html "https://azure.github.io/AppService/2018/01/18/Demystifying-the-magic-behind-App-Service-OS-updates.html")

So what if you don’t want someone else to manage your platform?&nbsp; Consider IaaS instead where you have more control:&nbsp; What is IaaS? [https://azure.microsoft.com/en-us/overview/what-is-iaas/](https://azure.microsoft.com/en-us/overview/what-is-iaas/ "https://azure.microsoft.com/en-us/overview/what-is-iaas/")



## 

## Final Note

It may seem scary for someone to manage your Platform but it relieves you from the worry and overhead of being up to date.&nbsp; You can even use custom containers on the PaaS platform if you wish to encapsulate a certain environment as a container.&nbsp; Be sure to reach out to Microsoft if you have any other questions about this!