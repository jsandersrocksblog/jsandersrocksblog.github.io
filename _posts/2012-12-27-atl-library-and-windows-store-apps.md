Just a quick post in case you run up against this issue.

You can use a subset of ATL Library code in your Windows Store app.&#160; You may run into errors with validation when compiling or when running the Windows App Certification Kit (WACK) tool.

If you include CComCriticalSection in your Windows Store app code and then run the WACK tool you will get these errors:

<font face="Consolas">Error Found: The supported APIs test detected the following errors:</font>

  * <font face="Consolas">API GetModuleHandleW in kernel32.dll is not supported for this application type. XXXXX.XXX calls this API. </font>
  * <font face="Consolas">API InitializeCriticalSectionAndSpinCount in kernel32.dll is not supported for this application type. XXXXX.XXX calls this API.</font>

This is caused by a bug in the current ATL Library.&#160; The workaround is to add this code to your project which will implement the correct code (add it to any of your CPP files):

<font face="Consolas">#if (_ATL_NTDDI_MIN >= NTDDI_VISTA) </font>

<font face="Consolas">namespace ATL { </font>

<font face="Consolas">BOOL _AtlInitializeCriticalSectionEx(__out LPCRITICAL_SECTION lpCriticalSection, __in DWORD dwSpinCount, __in DWORD Flags) <br /> { <br />&#160;&#160;&#160;&#160; return InitializeCriticalSectionEx(lpCriticalSection, dwSpinCount, Flags);&#160; <br /> } </font>

<font face="Consolas">} <br />#endif </font>

<font face="Consolas"></font>

Let me know if this helped you out!

-Jeff