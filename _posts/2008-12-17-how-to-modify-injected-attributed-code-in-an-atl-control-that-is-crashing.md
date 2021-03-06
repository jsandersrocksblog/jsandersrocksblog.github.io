(ATL Control Visual Studio 2003 Crashes long value) I found a problem in the injected code from Visual Studio 2003 for an ATL control that had a property that was&nbsp;a long (VT_I4) value.&nbsp; You could reliably crash the control if you put it into an html page and had jscript in a loop, setting the value over and over (100 X) in this case would crash it.&nbsp; To make the crash reliable, I turned off BSTR caching and set full gflags.&nbsp; You could see the issue was the freeing of a BSTR twice.&nbsp; 

Since Visual Studio 2003 is in extended support, getting a fix for this injected code was not possible so I had to fix it myself.&nbsp; The easiest fix is to simply build the control using Visual Studio 2008!

I STRONGLY recommend that rather than doing this for the control, instead simply build with the latest Visual Studio to avoid the problem.

You can generate the injected code in the project as follows:

  * <div>
      In the Solution Explorer right click on AtlCom1 and choose &lsquo;Properties&rsquo;
    </div>

  * <div>
      Enable: &lsquo;Expand Attributed Source&rsquo; Yes (/Fx)&nbsp; in the C/C++ Output Files section.
    </div>

  * <div>
      Clean and Build the project
    </div>

You will notice some files that have a .mrg string in the filename.&nbsp; This is the injected code from the compiler.&nbsp; You can edit these, remove the .mrg and rebuild to get your code changes.

Generating the merged code, I found that the ::Invoke call was calling ::VariantChangeType( ) on a variable that was passed in.&nbsp; This is evil because this code does not own the Variant passed in!&nbsp; What was happening is that the type was being changed to a long and calling ::SysFreeString on the BSTR in the passed in Variant.&nbsp; To fix this I just changed the code to make a copy of the Variant and pass that in instead.&nbsp; Actually I kind of cheated here and simply generated the injected code from building the project under Visual Studio 2005 and compared this to the 2003 code&nbsp;since I knew that code ran without causing the access violation.

Here are the steps I took:

  * <div>
      Save a copy of&nbsp;the control code that has the Invoke code <<somefile>>.h.&nbsp;
    </div>

  * <div>
      Delete <<somefile>>.h.&nbsp;
    </div>

  * <div>
      Rename the generated file <<somefile>>.mrg.h to <<somefile>>.h to replace the old file.
    </div>

  * <div>
      Edit <<somefile>>.h as follows:<br />a.&nbsp;Find the&nbsp; ::Invoke function definition and add a local variable ATL::CComVariant rgVars[1]; to the function.<br />b.&nbsp;Find this in the ::Invoke function: if (wFlags & 4) and replace the assignment of v = rgpVars[0]; in this block of code with this code:
    </div>

> > &nbsp;rgVars[0] = *rgpVars[0];  
> > &nbsp;v = &rgVars[0];

> Now your code block in that section should look something like this:

> > if (wFlags & 4) {  
> > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if (pDispParams->cArgs != 1) {  
> > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; return DISP\_E\_BADPARAMCOUNT;  
> > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }  
> > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  
> > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp; rgVars[0] = *rgpVars[0];  
> > &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;v = &rgVars[0];

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if (v->vt != VT\_I4 && FAILED(\_\_VariantChangeType(v, &v0, VT\_I4))) {

  * <div>
      You can compile the project and the problem will be circumvented.
    </div>

Again&#8230; 

I STRONGLY recommend that rather than doing this for the control, instead simply build with the latest Visual Studio to avoid the problem.

&nbsp;