There are lots of ways to do things in Azure.&nbsp; I could not find a current end to end sample of setting up and getting an Access Token using SSH on a Linux box.&nbsp; I chose the latest Ubuntu image up in Azure Virtual Machines for this overview.&nbsp; This is loosely based on this older blog which had you create a PEM certificate (which is no longer necessary) [https://blogs.msdn.microsoft.com/arsen/2015/09/18/certificate-based-auth-with-azure-service-principals-from-linux-command-line/](https://blogs.msdn.microsoft.com/arsen/2015/09/18/certificate-based-auth-with-azure-service-principals-from-linux-command-line/ "https://blogs.msdn.microsoft.com/arsen/2015/09/18/certificate-based-auth-with-azure-service-principals-from-linux-command-line/") .

# Steps

**Install Azure CLI 2.0**

[https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest "https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest")

I am installing on Ubuntu: [https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-apt?view=azure-cli-latest](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-apt?view=azure-cli-latest "https://docs.microsoft.com/en-us/cli/azure/install-azure-cli-apt?view=azure-cli-latest")

**Login** with an account that can create Service Principals using the interactive login (works with MFA):&nbsp; 

[https://docs.microsoft.com/en-us/cli/azure/authenticate-azure-cli?view=azure-cli-latest#interactive-log-in](https://docs.microsoft.com/en-us/cli/azure/authenticate-azure-cli?view=azure-cli-latest#interactive-log-in "https://docs.microsoft.com/en-us/cli/azure/authenticate-azure-cli?view=azure-cli-latest#interactive-log-in")

[<img loading="lazy" title="Login" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="Login" src="/assets/images/2018/05/Login_thumb.png" width="810" height="108" />](/assets/images/2018/05/Login1.png)

**Select the Target Subscription:**

In my case I have many subscriptions and I need to make active or select the one ending in ‘umption’.&nbsp; Here are the commands to do that:

[<img loading="lazy" title="Set Subcription edit 1" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="Set Subcription edit 1" src="/assets/images/2018/05/Set-Subcription-edit-1_thumb.png" width="756" height="183" />](/assets/images/2018/05/Set-Subcription-edit-1.png)

**Create Service Principal with Certificate**

[https://docs.microsoft.com/en-us/cli/azure/create-an-azure-service-principal-azure-cli?view=azure-cli-latest](https://docs.microsoft.com/en-us/cli/azure/create-an-azure-service-principal-azure-cli?view=azure-cli-latest "https://docs.microsoft.com/en-us/cli/azure/create-an-azure-service-principal-azure-cli?view=azure-cli-latest")

I used the default access and the&nbsp; &#8211;create-cert option like this: <font style="background-color: #ffff00">az ad sp create-for-rbac -n &#8220;ForMyAutomationApp&#8221; &#8211;create-cert</font>

[<img loading="lazy" title="createSPcert" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="createSPcert" src="/assets/images/2018/05/createSPcert_thumb.png" width="777" height="162" />](/assets/images/2018/05/createSPcert.png)

Copy all this information as you will need it to login using this Service Principle (to test access).

Note that location of the .pem file.&nbsp; Go there and you can list it out.&nbsp; You will need information from this certificate later to verify the signature of this token:

[<img loading="lazy" title="Cert" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="Cert" src="/assets/images/2018/05/Cert_thumb.png" width="362" height="645" />](/assets/images/2018/05/Cert.png)

**Copy the public key** which is the entire section _after_ &#8212;&#8211;END PRIVATE KEY&#8212;&#8211;

Like this:

&#8212;&#8211;BEGIN CERTIFICATE&#8212;&#8211;  
MIICoTCCA

…..

Y32P5WwcaOfX1hkzMtTj4DAmAAlhudWhnRmVBRUvSx7RmWMl1Fhe  
+ufr0jY=  
&#8212;&#8211;END CERTIFICATE&#8212;&#8211;

You will need this to test the signature of your JWT later.

&nbsp;

**Log out and test the Service Principal login (optional)**

Using the information you copied when creating the service principal you can test access.&nbsp; You may want to create your service principal with a certain role for access reasons.&nbsp; The default is Contributor which is fine for me:

**[<img loading="lazy" title="TestLogin" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="TestLogin" src="/assets/images/2018/05/TestLogin_thumb.png" width="981" height="211" />](/assets/images/2018/05/TestLogin.png)**

&nbsp;

**Sign the JWT Token** 

Note:&nbsp; This is accurate at time of publication, but these are all 3rd party Open Source tools that may change.&nbsp; Also I removed this service principal and PEM file before publishing file so this information won’t work for anything. 

You will need to first get the certificate thumbprint.&nbsp; You can get it using OpenSSL (which you may have to install) using this command.&nbsp; You will need to enter the path to the PEM file you generated earlier:&nbsp; echo $(openssl x509 -in /home/jsandersrocks/tmpgfr4s8q4.pem -fingerprint -noout) | sed &#8216;s/SHA1 Fingerprint=//g&#8217; | sed &#8216;s/://g&#8217; | xxd -r -ps | base64 

The result is a small string which is the thumbprint: **Pic3Y1tO/jwbLjppXwJdbiPAAro=** 

**Create Token.js and run in node to create Signed JWT** 

I used VIM and created a file called token.js to create the signed JWT.&nbsp; Choose appropriate values for your token based on the library documentation here: [https://www.npmjs.com/package/jsonwebtoken](https://www.npmjs.com/package/jsonwebtoken "https://www.npmjs.com/package/jsonwebtoken")&nbsp; 

In this script You need to add the highlighted portions from the data above to include the PEM file path to read the _cert_, the SHA1 thumbprint for _x5t_, the tenant ID in the _aud_ field and finally the appId for _iss_ and _sub_.

var jwt = require(&#8216;jsonwebtoken&#8217;);  
var fs = require(&#8216;fs&#8217;);

var cert = fs.readFileSync(<font style="background-color: #ffff00">&#8216;/home/jsandersrocks/tmpgfr4s8q4.pem&#8217;</font>);

var additionalHeaders = {

&#8220;x5t&#8221;:&#8221;<font style="background-color: #ffff00">Pic3Y1tO/jwbLjppXwJdbiPAAro=</font>&#8220;

}

var myJwt = {

&#8220;aud&#8221;: [https://login.microsoftonline.com/<font style="background-color: #ffff00">72f988bf-XXXXXXXXXXXX-2d7cd011db47</font>/oauth2/token](https://login.microsoftonline.com/72f988bf-XXXXXXXXXXXX-2d7cd011db47/oauth2/token),

&#8220;iss&#8221;: &#8220;<font style="background-color: #ffff00">81ad91de-0844-4547-88ed-bffed69e45f1</font>&#8220;,

&#8220;sub&#8221;: &#8220;<font style="background-color: #ffff00">81ad91de-0844-4547-88ed-bffed69e45f1</font>&#8220;,

&#8220;jti&#8221;: &#8220;&#8221; + Math.random(),

&nbsp;

&#8220;exp&#8221;: Math.floor(Date.now()/1000)+7*8640000

};

console.log(myJwt);

var token = jwt.sign(myJwt,cert,{algorithm:&#8217;RS256&#8242;, header:additionalHeaders});

console.log(token);

&nbsp;

Install node.js if necessary and then the jasonwebtoken package using this command: **npm install jsonwebtoken,** 

Finally run node pointing to your script file to generate the token! 

[<img loading="lazy" title="SignToken" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="SignToken" src="/assets/images/2018/05/SignToken_thumb.png" width="964" height="228" />](/assets/images/2018/05/SignToken.png) 

**Copy the Token and Verify the signature:** 

The signed token is the text above starting with “ey” and to the end of the string (in this case –SRg). 

Go to [https://jwt.io/](https://jwt.io/ "https://jwt.io/") and paste your token into the first field.&nbsp; Then past in the information from the public key (from the section above &#8211; **Copy the public key** ). 

&nbsp; 

[<img loading="lazy" title="image" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="image" src="/assets/images/2018/05/image_thumb226.png" width="699" height="548" />](/assets/images/2018/05/image295.png) 

&nbsp;

## 

# Next Steps

You can now use this JWT to get an access token and use this in REST APIs (see blog that inspired this in the opening statement).&nbsp; 

Here is an example of me generating a token and using it in curl to get an access token.&nbsp; The actual access token is the field after “access_token” in the below output.&nbsp; 

[<img loading="lazy" title="token2" style="border-top: 0px;border-right: 0px;border-bottom: 0px;padding-top: 0px;padding-left: 0px;border-left: 0px;padding-right: 0px" border="0" alt="token2" src="/assets/images/2018/05/token2_thumb.png" width="926" height="234" />](/assets/images/2018/05/token2.png)

&nbsp;

Note that there are so many different ways to use this token and you can generate this many ways.&nbsp; There are settings for expiration of this token and when it begins to be valid.&nbsp; I leave that research to you as it is adequately documented.&nbsp; A lot of these techniques are contained in the various libraries and APIs for different languages and I encourage you to use those whenever possible. 

Please drop me a note if you found this useful!