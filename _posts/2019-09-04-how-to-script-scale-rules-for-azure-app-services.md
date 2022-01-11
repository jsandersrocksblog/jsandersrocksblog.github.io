In this example I am showing how you can script setting the properties correctly in script to set a Scale operation based on some values you want.

# Steps

Create a Test Web App and mock up the rules you want.&nbsp; You will use this to retrieve the JSON you need to set in your script.

Click on Azure Resource Explorer of the app you created to get to the rules:

[<img loading="lazy" width="478" height="397" title="image" style="display: inline; background-image: none;" alt="image" src="/assets/images/2019/09/image_thumb-6.png" border="0" />](/assets/images/2019/09/image-6.png)

Navigate to the autoscale rules.&nbsp; This is located in the resource group of your app under microsoft.insights:

[<img loading="lazy" width="667" height="482" title="clip_image001[4]" style="display: inline; background-image: none;" alt="clip_image001[4]" src="/assets/images/2019/09/clip_image0014_thumb.jpg" border="0" />](/assets/images/2019/09/clip_image0014.jpg)

Copy the Properties section to use later.

Click on the Powershell tab to get the example Powershell script (you want the Set properties one).

[<img loading="lazy" width="1055" height="346" title="clip_image001[6]" style="display: inline; background-image: none;" alt="clip_image001[6]" src="/assets/images/2019/09/clip_image0016_thumb.jpg" border="0" />](/assets/images/2019/09/clip_image0016.jpg)

And simply replace the $PropertiesObject variable with the properties you copied from above!



Let me know if this was Useful!