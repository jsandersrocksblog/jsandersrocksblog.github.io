There are new checks in Windows 7 to prevent you from doing bad things with the WinHttp APIs.&nbsp; In the sample code below, I do not get an error pre-Windows 7 but on Windows 7 the WinHttpWriteData call results in bResults being 0 and GetLastError() returns 87 (ERROR\_INVALID\_PARAMETER):

> LPSTR pszData = &#8220;WinHttpWriteData Example&#8221;; 
> 
> LPSTR pszMoreData = &#8220;WinHttpWriteData Example&#8221;;

&nbsp;&nbsp;&nbsp; // Send a Request.  
&nbsp;&nbsp;&nbsp; if (hRequest)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; bResults = WinHttpSendRequest( hRequest,  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; WINHTTP\_NO\_ADDITIONAL_HEADERS,  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0, pszData, strlen(pszData),  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; strlen(pszData), 0); 

&nbsp;&nbsp;&nbsp; // Write data to the server.  
&nbsp;&nbsp;&nbsp; if (bResults)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; bResults = WinHttpWriteData( hRequest, pszMoreData,  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; strlen(pszMoreData),  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &dwBytesWritten); 

Looking at a Network Monitor trace, you see something very strange in the HTTP traffic pre Windows 7: 

You see a POST &#8211; Http: Request, POST /ReadAll.asp ContentLength:&nbsp; 24 and the text I sent: HTTPPayloadLine: WinHttpWriteData Example 

and then the successful return code from the server -Http: Response, HTTP/1.1, Status Code = 200, URL: /ReadAll.asp 

But the following bunch of Data in the next frame! &#8211; HtmlPayload: WinHttpWriteData Example 

So the POST is being sent, then more data after the initial POST and 200 OK response from the server! 

Looking at the headers, you can see the Content-Length is set to 24 (this is what you set in WinHttpSendRequest the _dwTotalLength_ = strlen(pszData)), and that is why the server returns 200 (because as far as it is concerned you told it you were sending only 24 bytes of data and that was what your client had sent).&nbsp; However the extra 24 bytes of data gets sent by the WinHttpWriteData call! 

For Windows 7, a check was put in place internally to prevent you from making such a bad protocol violation.&nbsp; Now WinHttpWriteData will return 0 and GetLastError() will indicate 87 which means that you have passed invalid data.&nbsp; In this case the length of the data you intend to write exceeded what you set as the content length in WinHttpSendRequest!&nbsp; The fix is for you to correct your buggy code and indicate the correct content length by setting the _dwTotalLength_ parameter correctly in the call to WinHttpSendRequest.&nbsp; In this case I can change the code to this: 

&nbsp;

// Send a Request.  
&nbsp;&nbsp;&nbsp; if (hRequest)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; bResults = WinHttpSendRequest( hRequest,  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; WINHTTP\_NO\_ADDITIONAL_HEADERS,  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 0, pszData, strlen(pszData),  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; strlen(pszData)+ strlen(pszMoreData), 0); 

Please drop me a comment if you found this helpful! 

Reference: [http://msdn.microsoft.com/en-us/library/aa384110(VS.85).aspx](http://msdn.microsoft.com/en-us/library/aa384110(VS.85).aspx "http://msdn.microsoft.com/en-us/library/aa384110(VS.85).aspx")