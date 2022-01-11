A seemingly easy thing to do that I could not find documentation for!

string astr;  
foreach (DataRowView aRow in listBox1.SelectedItems )  
{  
&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicId&#8221;].ToString();  
&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicText&#8221;].ToString();  
} 

TopicId and TopicText are the name of the columns in the table of the Datasource that has been bound to the listbox control.

Drop me a note if you found this useful!