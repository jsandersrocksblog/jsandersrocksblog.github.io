By design the WebBrowser Control does not close the parent Form when WebBrowser Control is closed.&nbsp; Here is one way you can accomplish this.

The WebBrowser will send a WM_NOTIFYPARENT notification that can be captured and an event raised that a host can respond to.

Here is the documentation on the WM_NOTIFYPARENT notification:&nbsp; <http://msdn2.microsoft.com/en-us/library/ms632638.aspx>

In this case we care about when the WebBrowser is closed, so we will respond to the wParam WM_DESTROY only.&nbsp; Since I am going to override the WebBrowser control for other purposes, I will simply add an event to this control that any Form can act on.

First define a new VB Windows Project.&nbsp; Drag and drop the WebBrowser Control onto your form from the Common Controls section of the Toolbox.

Next we want to extend the WebBrowser control so we can process the WndProc function.&nbsp; Create a new Class(Add, Class) and call it MyExtendedBrowserControl.

<font color=#0000ff size=2>

Public

</font><font size=2> </font><font color=#0000ff size=2>Class</font><font size=2> MyExtendedBrowserControl  
</font><font color=#008000 size=2>&#8216; Based on WebBrowser  
</font><font color=#0000ff size=2>Inherits</font><font size=2> System.Windows.Forms.WebBrowser

</font><font color=#008000 size=2>&#8216; Define constants from winuser.h  
</font><font color=#0000ff size=2>Private</font><font size=2> </font><font color=#0000ff size=2>Const</font><font size=2> WM_PARENTNOTIFY </font><font color=#0000ff size=2>As</font><font size=2> </font><font color=#0000ff size=2>Integer</font><font size=2> = &H210  
</font><font color=#0000ff size=2>Private</font><font size=2> </font><font color=#0000ff size=2>Const</font><font size=2> WM_DESTROY </font><font color=#0000ff size=2>As</font><font size=2> </font><font color=#0000ff size=2>Integer</font><font size=2> = 2

</font><font color=#008000 size=2>&#8216;Define New event to fire  
</font><font color=#0000ff size=2>Public</font><font size=2> </font><font color=#0000ff size=2>Event</font><font size=2> WBWantsToClose()

</font><font color=#0000ff size=2>Protected</font><font size=2> </font><font color=#0000ff size=2>Overrides</font><font size=2> </font><font color=#0000ff size=2>Sub</font><font size=2> WndProc(</font><font color=#0000ff size=2>ByRef</font><font size=2> m </font><font color=#0000ff size=2>As</font><font size=2> Message)  
</font><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp; Select</font><font size=2> </font><font color=#0000ff size=2>Case</font><font size=2> m.Msg  
</font><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Case</font><font size=2> WM_PARENTNOTIFY  
</font><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; If</font><font size=2> (</font><font color=#0000ff size=2>Not</font><font size=2> DesignMode) </font><font color=#0000ff size=2>Then  
</font><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; If</font><font size=2> (m.WParam = WM_DESTROY) </font><font color=#0000ff size=2>Then  
</font><font color=#008000 size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; &#8216; Tell whoever cares we are closing  
</font><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; RaiseEvent</font><font size=2> WBWantsToClose()  
</font><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; End</font><font size=2> </font><font color=#0000ff size=2>If  
</font><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;End</font><font size=2> </font><font color=#0000ff size=2>If  
</font><font size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; DefWndProc(m)  
</font><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Case</font><font size=2> </font><font color=#0000ff size=2>Else  
</font><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; MyBase</font><font size=2>.WndProc(m)  
</font><font color=#0000ff size=2>&nbsp;&nbsp;&nbsp; End</font><font size=2> </font><font color=#0000ff size=2>Select  
</font><font color=#0000ff size=2>End</font><font size=2> </font><font color=#0000ff size=2>Sub

End

</font><font size=2> </font><font color=#0000ff size=2>Class</font>

Now we have to get into the guts of the Form.&nbsp; Although we dropped a WebBrowserControl on the form (and VB wired that up nicely for us) we REALLY want to create our new Control that extends the WebBrowser Control.

Choose File, Open from the Visual Studio menu and open the designer vb code (in this case Form1.Designer.vb).

Replace System.Windows.Forms.WebBrowser with the extended control MyExtendedBrowserControl.&nbsp; There should be Two Places:

<font size=2>

</font><font color=#0000ff size=2>Me</font><font size=2>.WebBrowser1 = </font><font color=#0000ff size=2>New</font><font size=2> VBCloseBrowser.ExtendedWebBrowser.ExtendWebBrowser</font><font size=2>

</font><font color=#0000ff size=2>Friend</font><font size=2> </font><font color=#0000ff size=2>WithEvents</font><font size=2> WebBrowser1 </font><font color=#0000ff size=2>As</font><font size=2> VBCloseBrowser.ExtendedWebBrowser.ExtendWebBrowser

</font>Save all the files and Build the project (you will see errors in the designers until you do build).

Now go to the design view of your Form.&nbsp; Right Click on the Browser control and choose Properties…&nbsp; Click on the Events Icon (the lightning bolt) and you will see at the bottom your new event WBWantsToClose.&nbsp; Double click on that name and you will automatically add the handler for that event.&nbsp; In my case, I simply want to close this form so I added Me.Close() in the handler.

Enjoy!