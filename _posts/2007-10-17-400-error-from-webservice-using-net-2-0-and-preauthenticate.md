Prashant from my team&nbsp;found this interesting issue.&nbsp; I will blog it here until the KB comes out on this.

Problem  
======  
WebService server responds back with a HTTP 400 error when using PreAuthenticate on the WebServiceProxy class.&nbsp; This results in a System.Net.WebException: “The request failed with HTTP status 400: Bad Request”

Symptoms  
=============================  
Consuming a WebService that&nbsp;uses Basic Authentication from a .Net 2.0 client through a Proxy&nbsp;using NTLM authentication the&nbsp;WebService server responds back with a HTTP 400 error message.&nbsp; This happens only when using the PreAuthenticate property of the proxied WebService class.

Cause  
=============================  
When the client uses the PreAuthenticate property, the client tries to re-negotiate the NTLM handshake with the Proxy. When the Proxy sees that the connection has already been authenticated, it simply ignores the re-negotiation and forwards a blank request &#8211; with Content-Length: 0 to the server. The server expects a valid Content-Length followed by a soap-envelope which it never receives and hence responds back with a HTTP 400: Bad Request response.

Resolution  
=============================  
Do not set the HttpWebRequest.PreAuthenticate property (set it to false) when calling the Webservice with the above configuration.&nbsp; By default, the PreAuthenticate is turned off and set to false.<p mce_keep="true">&nbsp;</p>