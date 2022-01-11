Just a quicky!

If you are building a PhoneGap app using the preview bits of Windows Azure Mobile Services and you get this error: “Login is only supported from http:// and https:// URLs. Please host your page in a web server” you need to include the cordova library.

Here was how we got this resolved:

The new MobileServices.Web-1.0.0.js client library does work with PhoneGap 2.3+ and IE8+. However, we haven’t yet published any documentation about how to work with PhoneGap, so we understand it will not be clear right now how to get started!

Currently, the downloadable quickstart project is intended only for browser apps, not for PhoneGap apps. However, it is possible to tweak it to make it work in PhoneGap as follows:

  1. Add the following to your page’s <head> tag: **<meta name=&#8217;viewport&#8217; content=&#8217;width=device-width&#8217; />**
  2. Change the <script> tag that references jQuery to specify an explicit protocol in the URL, i.e., change this line:

<script src=&#8217;//ajax.aspnetcdn.com/ajax/jQuery/jquery-1.9.1.min.js&#8217;></script>

.. to this:

<script src=**&#8216;http:**//ajax.aspnetcdn.com/ajax/jQuery/jquery-1.9.1.min.js&#8217;></script>

  1. <font style="background-color: rgb(255, 255, 0);">Add a script tag that references cordova-x.x.x.js (for example, <script src=&#8217;cordova-2.5.0.js&#8217;></script> if you are using Cordova 2.5.0).</font>
  2. If you are targeting Windows Phone 7.5., there is a known issue you’ll need to work around. Add the following line of code anywhere in your application before you instantiate a MobileServiceClient. For example, add this to the very beginning of app.js:

> **XMLHttpRequest.prototype.withCredentials = false;**

We understand that this could be easier, so we are working on improving the quickstart. After an upcoming update, none of these steps will be necessary, except for adding a reference to cordova-x.x.x.js.

src: [http://social.msdn.microsoft.com/Forums/en-US/azuremobile/thread/a2386093-73cd-44fb-a418-4fa83a36c800](http://social.msdn.microsoft.com/Forums/en-US/azuremobile/thread/a2386093-73cd-44fb-a418-4fa83a36c800 "http://social.msdn.microsoft.com/Forums/en-US/azuremobile/thread/a2386093-73cd-44fb-a418-4fa83a36c800")

-Jeff