If you get an error similar to this:  
Changed service health to &#8216;Critical&#8217; (Service is unhealthy. Please check the service logs to determine the issue and how to correct it.)

And you check the logs in your dashboard and see similar to this:  
Found conflicts between different versions of the same dependent assembly &#8216;Microsoft.WindowsAzure.Storage&#8217;: 4.2.1.0. Please change your project to use version &#8216;3.1.0.1&#8217; which is the one currently supported by the hosting environment.

The log tells you what the resolution is (use the correct supported version of the package).

There are a few ways you can get yourself into this situation but lets just fix the issue shall we?

There are a ton of dependencies between packages you may add and the ones that are added by default.&#160; The easiest way to get out of this mess is to identify and find the correct version of the conflict so you can install it, and also reset all the other packages to their default and supported configuration.

How do you get the default configuration?

Easy!&#160;&#160; Backup the entire project somewhere (are you using VSO or something cool like that.. it makes it easy).&#160; Create a new Cloud app in Mobile Services (or download the starter project from your dashboard) and use the packages.config file to compare to your project’s packages.config file **(don’t forget to backup the entire project somewhere first)**.&#160; Then you can compare your broken packages.config with the default one and fix up the references… and remove the offending package.&#160; Sometimes it is easiest to replace your old config file with this new one and add back missing references identified by the build environment.

Finally add the correct version back.&#160; In this case open the package manager console <Tools> <NuGet Package Manager> <Package Manager Console> and type:&#160; Install-Package WindowsAzure.Storage -Version 3.1.0.1

Clean the Build.&#160; Then Build.&#160; When you build it will update the dependent references correctly.&#160; If you have added other references to your project be sure to add them back as well.

Then when you publish, Ensure you choose the option to replace all the destination files.

Let me know if this helps you!