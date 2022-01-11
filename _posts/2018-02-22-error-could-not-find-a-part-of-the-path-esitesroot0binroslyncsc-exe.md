After publishing the web app to Azure Cloud Services from Visual Studio 2017, it would not run and returned a 500 error.  Turning off custom error messages I was getting this error: _Could not find a part of the path &#8216;E:\sitesroot\0\bin\roslyn\csc.exe&#8217;._ In your solution explorer for your project, right click on the ‘References’ section for your WebRole and select ‘Manage NuGet Packages…’ _full stack:_ 

<pre>[DirectoryNotFoundException: Could not find a part of the path 'E:\sitesroot\0\bin\roslyn\csc.exe'.]
   System.IO.__Error.WinIOError(Int32 errorCode, String maybeFullPath) +548
   System.IO.FileStream.Init(String path, FileMode mode, FileAccess access, Int32 rights, Boolean useRights, FileShare share, Int32 bufferSize, FileOptions options, SECURITY_ATTRIBUTES secAttrs, String msgPath, Boolean bFromProxy, Boolean useLongPath, Boolean checkHost) +1159
   System.IO.FileStream..ctor(String path, FileMode mode, FileAccess access, FileShare share) +133
   Microsoft.CodeDom.Providers.DotNetCompilerPlatform.Compiler.get_CompilerName() +127
   Microsoft.CodeDom.Providers.DotNetCompilerPlatform.Compiler.FromFileBatch(CompilerParameters options, String[] fileNames) +832
   Microsoft.CodeDom.Providers.DotNetCompilerPlatform.Compiler.CompileAssemblyFromFileBatch(CompilerParameters options, String[] fileNames) +189
   System.Web.Compilation.AssemblyBuilder.Compile() +2038
   System.Web.Compilation.BuildProvidersCompiler.PerformBuild() +325
   System.Web.Compilation.ApplicationBuildProvider.GetGlobalAsaxBuildResult(Boolean isPrecompiledApp) +406
   System.Web.Compilation.BuildManager.CompileGlobalAsax() +47
   System.Web.Compilation.BuildManager.EnsureTopLevelFilesCompiled() +366
[HttpException (0x80004005): Could not find a part of the path 'E:\sitesroot\0\bin\roslyn\csc.exe'.]
   System.Web.Compilation.BuildManager.ReportTopLevelCompilationException() +76
   System.Web.Compilation.BuildManager.EnsureTopLevelFilesCompiled() +642
   System.Web.Compilation.BuildManager.CallAppInitializeMethod() +34
   System.Web.Hosting.HostingEnvironment.Initialize(ApplicationManager appManager, IApplicationHost appHost, IConfigMapPathFactory configMapPathFactory, HostingEnvironmentParameters hostingParameters, PolicyLevel policyLevel, Exception appDomainCreationException) +927
[HttpException (0x80004005): Could not find a part of the path 'E:\sitesroot\0\bin\roslyn\csc.exe'.]
   System.Web.HttpRuntime.FirstRequestInit(HttpContext context) +534
   System.Web.HttpRuntime.EnsureFirstRequestInit(HttpContext context) +119
   System.Web.HttpRuntime.ProcessRequestNotificationPrivate(IIS7WorkerRequest wr, HttpContext context) +726</pre>

## Cause

A bug in Microsoft.CodeDom.Providers.DotNetCompilerPlatform package 1.0.7

## Fix

Upgrade package to 1.0.8  
[<img loading="lazy" title="capture20180222162517321" style="padding-top: 0px;padding-left: 0px;padding-right: 0px;border: 0px" border="0" alt="capture20180222162517321" src="/assets/images/2018/02/capture20180222162517321_thumb.png" width="342" height="210" />](/assets/images/2018/02/capture20180222162517321.png)  
You will notice Updates will have some updates available and select the Microsoft.CodeDom.Providers.DotNetCompilerPlatform ‘Latest stable 1.0.8’ and hit the Update button.  
[<img loading="lazy" title="capture20180222160446837" style="padding-top: 0px;padding-left: 0px;padding-right: 0px;border: 0px" border="0" alt="capture20180222160446837" src="/assets/images/2018/02/capture20180222160446837_thumb.png" width="969" height="257" />](/assets/images/2018/02/capture20180222160446837.png)  
Publish your application.  
Now you may have to wait a bit as the role drains any existing connections, but eventually this will result in getting rid of this pesky error!