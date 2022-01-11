The requirement was to assign a click event handler to all Label Controls contained in a .NET User Control.&nbsp; This is a simple technique but I found there was no good documentation on how to do this.&nbsp; 

To illustrate how to do this, I created a simple Windows Form application in C# and added a new Windows Forms User Control to the project.&nbsp; I called it AutoLabelClickControl.&nbsp; I placed a label right on the control called ‘Control Label’.&nbsp; I added a panel with a label on it called ‘Panel Label’ and then placed a panel contained in the first panel and put a label on it called ‘Panel in a Panel Label’.

<a href="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Howtoiterateovercontainedcontrolstos.NET_AC85/image_4.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Howtoiterateovercontainedcontrolstos.NET_AC85/image_4.png"><img loading="lazy" style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="image" border="0" alt="image" src="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Howtoiterateovercontainedcontrolstos.NET_AC85/image_thumb_1.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Howtoiterateovercontainedcontrolstos.NET_AC85/image_thumb_1.png" width="449" height="288" /></a> 

The idea now is that when the control ‘AutoLabelClickControl’ is loaded, code should hook up a common click event handler for all labels.&nbsp; Add a _Load event handler to your Control (not the Form) using the wizard and let’s add the necessary code:

// This is the Common Event Handler for all Label Clicks  
private void LabelClickEventHandler(object sender, EventArgs e)  
{  
&nbsp;&nbsp;&nbsp; // Ensure we can typecast correctly!  
&nbsp;&nbsp;&nbsp; if (sender is Label)  
&nbsp;&nbsp;&nbsp; {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // Do whatever you want&#8230; in this case show the Name of the control clicked  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Label aLabel = sender as Label;  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; MessageBox.Show(aLabel.Name);  
&nbsp;&nbsp;&nbsp; } 

} 

// Walk the collection recursively and find Label Controls and wire them up  
private void FindLabelControlsInContainerAndAssignEvent(Control.ControlCollection aCollection)  
{  
&nbsp;&nbsp;&nbsp; foreach (Control aControl in aCollection)  
&nbsp;&nbsp;&nbsp; {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // does this control contain other controls?  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if (aControl.Controls.Count > 0)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // call this function recursively!  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; FindLabelControlsInContainerAndAssignEvent(aControl.Controls);  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; } 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // wire up our Common Event Handler  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if (aControl is System.Windows.Forms.Label)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; aControl.Click += new System.EventHandler(LabelClickEventHandler);  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; } 

&nbsp;&nbsp;&nbsp; }  
} 

private void AutoLabelClickControl_Load(object sender, EventArgs e)  
{  
&nbsp;&nbsp;&nbsp; // When loading wire up the events for all contained Labels  
&nbsp;&nbsp;&nbsp; FindLabelControlsInContainerAndAssignEvent(this.Controls);  
} 

&nbsp;

And here is the test! 

<a href="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Howtoiterateovercontainedcontrolstos.NET_AC85/image_8.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Howtoiterateovercontainedcontrolstos.NET_AC85/image_8.png"><img loading="lazy" style="border-bottom: 0px; border-left: 0px; display: inline; border-top: 0px; border-right: 0px" title="image" border="0" alt="image" src="/assets/images/TNBlogsFS/BlogFileStorage/blogs_msdn/jpsanders/WindowsLiveWriter/Howtoiterateovercontainedcontrolstos.NET_AC85/image_thumb_3.png" original-url="http://blogs.msdn.com/blogfiles/jpsanders/WindowsLiveWriter/Howtoiterateovercontainedcontrolstos.NET_AC85/image_thumb_3.png" width="431" height="347" /></a> 

Note:&nbsp; Although you may think you cannot have a label contained in a label control, you can actually do this if you edit the Designer code (not recommended) and that is why I did not have an ‘else’ statement between these:

// does this control contain other controls?  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if (aControl.Controls.Count > 0)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // call this function recursively!  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; FindLabelControlsInContainerAndAssignEvent(aControl.Controls);  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; } 

// LOOK – NO ELSE STATEMENT… IN THEORY A LABEL COULD CONTAIN A LABEL BUT YOU WOULD HAVE TO HACK IT IN 

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; // wire up our Common Event Handler  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; if (aControl is System.Windows.Forms.Label)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; {  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; aControl.Click += new System.EventHandler(LabelClickEventHandler);  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; } 

It would be EXTREMELY weird for someone to do this but…&nbsp; I have been around a while so that is why I wrote that code that way 🙂

Note:&nbsp; It is up to you to apply proper error checking and try/catch blocks to this code.&nbsp; See the terms of use in my Blog header.

&nbsp;

Please drop me a note if you find this useful!