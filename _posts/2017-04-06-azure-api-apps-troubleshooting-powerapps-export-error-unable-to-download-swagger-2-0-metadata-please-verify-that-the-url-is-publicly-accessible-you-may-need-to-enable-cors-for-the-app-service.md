There is functionality in the Azure Portal that allows you to use the API definition of your Azure App Service and Export this through the “Export to PowerApps + Microsoft Flow” button in the API definition blade of your app ref: <a href="https://docs.microsoft.com/azure/app-service/app-service-export-api-to-powerapps-and-flow" target="_blank">https://docs.microsoft.com/azure/app-service/app-service-export-api-to-powerapps-and-flow</a> .&nbsp; If you get the error: “Unable to download Swagger 2.0 metadata. Please verify that the URL is publicly accessible. You may need to enable CORS for the App Service portal extension located at”&nbsp; It can be sometimes difficult to resolve this error.&nbsp; This should help you however!

## 

## Solution

As the error suggests there are a couple of potential problems.&nbsp; You need to understand how to verify the Swagger 2.0 Metadata is formatted correctly, that it is publicly available, and is not restricted for access by your CORS settings.&nbsp; There is also a bug in certain browsers (that is being addressed currently) that requires you to use Edge or Chrome to use this feature.

### Are you using a supported Browser?

Currently only Edge and Chrome work.&nbsp; This is being fixed very soon.

### Is the Swagger endpoint HTTPS?

The API definition location has to be https (see below).&nbsp; If you try http in this setting it will fail with the error I mentioned above

### Is the Swagger publicly available?

Ensure that you can hit the API definition location in an In-Private or Incognito browser with no problem.&nbsp; You should not be prompted for any authentication and you should be able to download the JSON that defines your API in Swagger 2.0.&nbsp; If you cannot, you need to fix that first!&nbsp; You can see the API definition location in your portal (again, note it must be https://) :

[<img loading="lazy" title="capture20170406104837219" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170406104837219" src="/assets/images/2017/04/capture20170406104837219_thumb.png" width="660" height="269" />](/assets/images/2017/04/capture20170406104837219.png)

### 

### &nbsp;

### Is the Swagger properly configured?

Look at the download you got from your In-Private or Incognito test above.&nbsp; Does it look correct?

<pre class="code"><span style="color: black">{
  </span><span style="color: #2e75b6">"swagger"</span><span style="color: black">: </span><span style="color: #a31515">"2.0"</span><span style="color: black">,
  </span><span style="color: #2e75b6">"info"</span><span style="color: black">: {
    </span><span style="color: #2e75b6">"version"</span><span style="color: black">: </span><span style="color: #a31515">"v1"</span><span style="color: black">,
    </span><span style="color: #2e75b6">"title"</span><span style="color: black">: </span><span style="color: #a31515">"WebApplication6"
  </span><span style="color: black">},
  </span><span style="color: #2e75b6">"host"</span><span style="color: black">: </span><span style="color: #a31515">"webapplication620170406101400.azurewebsites.net"</span><span style="color: black">,
  </span><span style="color: #2e75b6">"schemes"</span><span style="color: black">: [ </span><span style="color: #a31515">"https" </span><span style="color: black">],
  </span><span style="color: #2e75b6">"paths"</span><span style="color: black">: {
    </span><span style="color: #2e75b6">"/api/Values"</span><span style="color: black">: {
      </span><span style="color: #2e75b6">"get"</span><span style="color: black">: {
        </span><span style="color: #2e75b6">"tags"</span><span style="color: black">: [ </span><span style="color: #a31515">"Values" </span><span style="color: black">],
        </span><span style="color: #2e75b6">"operationId"</span><span style="color: black">: </span><span style="color: #a31515">"GetAll"</span><span style="color: black">,
        </span><span style="color: #2e75b6">"consumes"</span><span style="color: black">: [],
        </span><span style="color: #2e75b6">"produces"</span><span style="color: black">: [ </span><span style="color: #a31515">"application/json"</span><span style="color: black">, </span><span style="color: #a31515">"text/json"</span><span style="color: black">, </span><span style="color: #a31515">"application/xml"</span><span style="color: black">, </span><span style="color: #a31515">"text/xml" </span><span style="color: black">],
        </span><span style="color: #2e75b6">"responses"</span><span style="color: black">: {
          </span><span style="color: #2e75b6">"200"</span><span style="color: black">: {
            </span><span style="color: #2e75b6">"description"</span><span style="color: black">: </span><span style="color: #a31515">"OK"</span><span style="color: black">,
            </span><span style="color: #2e75b6">"schema"</span><span style="color: black">: {
              </span><span style="color: #2e75b6">"type"</span><span style="color: black">: </span><span style="color: #a31515">"array"</span><span style="color: black">,
              </span><span style="color: #2e75b6">"items"</span><span style="color: black">: { </span><span style="color: #2e75b6">"type"</span><span style="color: black">: </span><span style="color: #a31515">"string" </span><span style="color: black">}
            }</span></pre>

ref: <a title="https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md" href="https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md" target="_blank">https://github.com/OAI/OpenAPI-Specification/blob/master/versions/2.0.md</a>

&nbsp;

### Is CORS configured correctly?

The error message should tell you what CORS entry you need.&nbsp; For example, I need to add <https://web1.appsvcux.ext.azure.com> to CORS and save it:

[<img loading="lazy" title="capture20170406105659264" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170406105659264" src="/assets/images/2017/04/capture20170406105659264_thumb.png" width="487" height="370" />](/assets/images/2017/04/capture20170406105659264.png)

[<img loading="lazy" title="capture20170406105822524" style="border-left-width: 0px;border-right-width: 0px;border-bottom-width: 0px;padding-top: 0px;padding-left: 0px;padding-right: 0px;border-top-width: 0px" border="0" alt="capture20170406105822524" src="/assets/images/2017/04/capture20170406105822524_thumb.png" width="485" height="309" />](/assets/images/2017/04/capture20170406105822524.png)

&nbsp;

## Conclusion

These are the basics to troubleshooting that error message.&nbsp; Please drop me a note if you found this useful!

Link to this functionality: <a href="https://docs.microsoft.com/azure/app-service/app-service-export-api-to-powerapps-and-flow" target="_blank">https://docs.microsoft.com/azure/app-service/app-service-export-api-to-powerapps-and-flow</a>