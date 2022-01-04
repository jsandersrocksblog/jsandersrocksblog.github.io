---
id: 653
title: How to iterate (list) all selected items in a Databound ListBox in .NET 4.0 Winforms
date: 2010-05-07T12:12:27-05:00
author: jsanders
layout: post
guid: http://jsandersblog.azurewebsites.net/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms/
permalink: /2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms/
orig_url:
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms.aspx
  - http://blogs.msdn.microsoft.com/b/jpsanders/archive/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms.aspx
orig_site_id:
  - "8394"
  - "8394"
  - "8394"
  - "8394"
  - "8394"
  - "8394"
  - "8394"
  - "8394"
  - "8394"
orig_post_id:
  - "10009320"
  - "10009320"
  - "10009320"
  - "10009320"
  - "10009320"
  - "10009320"
  - "10009320"
  - "10009320"
  - "10009320"
orig_parent_id:
  - "10009320"
  - "10009320"
  - "10009320"
  - "10009320"
  - "10009320"
  - "10009320"
  - "10009320"
  - "10009320"
  - "10009320"
orig_thread_id:
  - "715867"
  - "715867"
  - "715867"
  - "715867"
  - "715867"
  - "715867"
  - "715867"
  - "715867"
  - "715867"
orig_application_key:
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
orig_post_author_id:
  - "65385"
  - "65385"
  - "65385"
  - "65385"
  - "65385"
  - "65385"
  - "65385"
  - "65385"
  - "65385"
orig_post_author_username:
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
  - jpsanders
orig_post_author_created:
  - Jan 18 2007 01:34:53:000PM
  - Jan 18 2007 01:34:53:000PM
  - Jan 18 2007 01:34:53:000PM
  - Jan 18 2007 01:34:53:000PM
  - Jan 18 2007 01:34:53:000PM
  - Jan 18 2007 01:34:53:000PM
  - Jan 18 2007 01:34:53:000PM
  - Jan 18 2007 01:34:53:000PM
  - Jan 18 2007 01:34:53:000PM
orig_is_approved:
  - "1"
  - "1"
  - "1"
  - "1"
  - "1"
  - "1"
  - "1"
  - "1"
  - "1"
orig_attachment_count:
  - "0"
  - "0"
  - "0"
  - "0"
  - "0"
  - "0"
  - "0"
  - "0"
  - "0"
orig_url_title:
  - http://blogs.msdn.com/b/jpsanders/archive/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms.aspx
  - http://blogs.msdn.com/b/jpsanders/archive/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms.aspx
opengraph_tags:
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to iterate (list) all selected items in a Databound ListBox in .NET 4.0 Winforms" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="A seemingly easy thing to do that I could not find documentation for! string astr;foreach (DataRowView aRow in listBox1.SelectedItems ){&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicId&#8221;].ToString();&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicText&#8221;].ToString();} TopicId and TopicText are the name of the columns in the table of the Datasource that has been bound to the listbox control. Drop me a note if you..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to iterate (list) all selected items in a Databound ListBox in .NET 4.0 Winforms" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms/" />
    <meta name="twitter:description" content="A seemingly easy thing to do that I could not find documentation for! string astr;foreach (DataRowView aRow in listBox1.SelectedItems ){&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicId&#8221;].ToString();&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicText&#8221;].ToString();} TopicId and TopicText are the name of the columns in the table of the Datasource that has been bound to the listbox control. Drop me a note if you..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to iterate (list) all selected items in a Databound ListBox in .NET 4.0 Winforms" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="A seemingly easy thing to do that I could not find documentation for! string astr;foreach (DataRowView aRow in listBox1.SelectedItems ){&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicId&#8221;].ToString();&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicText&#8221;].ToString();} TopicId and TopicText are the name of the columns in the table of the Datasource that has been bound to the listbox control. Drop me a note if you..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to iterate (list) all selected items in a Databound ListBox in .NET 4.0 Winforms" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms/" />
    <meta name="twitter:description" content="A seemingly easy thing to do that I could not find documentation for! string astr;foreach (DataRowView aRow in listBox1.SelectedItems ){&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicId&#8221;].ToString();&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicText&#8221;].ToString();} TopicId and TopicText are the name of the columns in the table of the Datasource that has been bound to the listbox control. Drop me a note if you..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to iterate (list) all selected items in a Databound ListBox in .NET 4.0 Winforms" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="A seemingly easy thing to do that I could not find documentation for! string astr;foreach (DataRowView aRow in listBox1.SelectedItems ){&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicId&#8221;].ToString();&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicText&#8221;].ToString();} TopicId and TopicText are the name of the columns in the table of the Datasource that has been bound to the listbox control. Drop me a note if you..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to iterate (list) all selected items in a Databound ListBox in .NET 4.0 Winforms" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms/" />
    <meta name="twitter:description" content="A seemingly easy thing to do that I could not find documentation for! string astr;foreach (DataRowView aRow in listBox1.SelectedItems ){&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicId&#8221;].ToString();&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicText&#8221;].ToString();} TopicId and TopicText are the name of the columns in the table of the Datasource that has been bound to the listbox control. Drop me a note if you..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to iterate (list) all selected items in a Databound ListBox in .NET 4.0 Winforms" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="A seemingly easy thing to do that I could not find documentation for! string astr;foreach (DataRowView aRow in listBox1.SelectedItems ){&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicId&#8221;].ToString();&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicText&#8221;].ToString();} TopicId and TopicText are the name of the columns in the table of the Datasource that has been bound to the listbox control. Drop me a note if you..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to iterate (list) all selected items in a Databound ListBox in .NET 4.0 Winforms" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms/" />
    <meta name="twitter:description" content="A seemingly easy thing to do that I could not find documentation for! string astr;foreach (DataRowView aRow in listBox1.SelectedItems ){&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicId&#8221;].ToString();&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicText&#8221;].ToString();} TopicId and TopicText are the name of the columns in the table of the Datasource that has been bound to the listbox control. Drop me a note if you..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to iterate (list) all selected items in a Databound ListBox in .NET 4.0 Winforms" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="A seemingly easy thing to do that I could not find documentation for! string astr;foreach (DataRowView aRow in listBox1.SelectedItems ){&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicId&#8221;].ToString();&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicText&#8221;].ToString();} TopicId and TopicText are the name of the columns in the table of the Datasource that has been bound to the listbox control. Drop me a note if you..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to iterate (list) all selected items in a Databound ListBox in .NET 4.0 Winforms" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms/" />
    <meta name="twitter:description" content="A seemingly easy thing to do that I could not find documentation for! string astr;foreach (DataRowView aRow in listBox1.SelectedItems ){&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicId&#8221;].ToString();&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicText&#8221;].ToString();} TopicId and TopicText are the name of the columns in the table of the Datasource that has been bound to the listbox control. Drop me a note if you..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to iterate (list) all selected items in a Databound ListBox in .NET 4.0 Winforms" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="A seemingly easy thing to do that I could not find documentation for! string astr;foreach (DataRowView aRow in listBox1.SelectedItems ){&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicId&#8221;].ToString();&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicText&#8221;].ToString();} TopicId and TopicText are the name of the columns in the table of the Datasource that has been bound to the listbox control. Drop me a note if you..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to iterate (list) all selected items in a Databound ListBox in .NET 4.0 Winforms" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms/" />
    <meta name="twitter:description" content="A seemingly easy thing to do that I could not find documentation for! string astr;foreach (DataRowView aRow in listBox1.SelectedItems ){&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicId&#8221;].ToString();&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicText&#8221;].ToString();} TopicId and TopicText are the name of the columns in the table of the Datasource that has been bound to the listbox control. Drop me a note if you..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to iterate (list) all selected items in a Databound ListBox in .NET 4.0 Winforms" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="A seemingly easy thing to do that I could not find documentation for! string astr;foreach (DataRowView aRow in listBox1.SelectedItems ){&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicId&#8221;].ToString();&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicText&#8221;].ToString();} TopicId and TopicText are the name of the columns in the table of the Datasource that has been bound to the listbox control. Drop me a note if you..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to iterate (list) all selected items in a Databound ListBox in .NET 4.0 Winforms" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms/" />
    <meta name="twitter:description" content="A seemingly easy thing to do that I could not find documentation for! string astr;foreach (DataRowView aRow in listBox1.SelectedItems ){&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicId&#8221;].ToString();&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicText&#8221;].ToString();} TopicId and TopicText are the name of the columns in the table of the Datasource that has been bound to the listbox control. Drop me a note if you..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to iterate (list) all selected items in a Databound ListBox in .NET 4.0 Winforms" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="A seemingly easy thing to do that I could not find documentation for! string astr;foreach (DataRowView aRow in listBox1.SelectedItems ){&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicId&#8221;].ToString();&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicText&#8221;].ToString();} TopicId and TopicText are the name of the columns in the table of the Datasource that has been bound to the listbox control. Drop me a note if you..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to iterate (list) all selected items in a Databound ListBox in .NET 4.0 Winforms" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms/" />
    <meta name="twitter:description" content="A seemingly easy thing to do that I could not find documentation for! string astr;foreach (DataRowView aRow in listBox1.SelectedItems ){&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicId&#8221;].ToString();&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicText&#8221;].ToString();} TopicId and TopicText are the name of the columns in the table of the Datasource that has been bound to the listbox control. Drop me a note if you..." />
    
  - |
    <meta property="og:type" content="article" />
    <meta property="og:title" content="How to iterate (list) all selected items in a Databound ListBox in .NET 4.0 Winforms" />
    <meta property="og:url" content="https://blogs.msdn.microsoft.com/jpsanders/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms/" />
    <meta property="og:site_name" content="Http Client Protocol Issues (and other fun stuff I support)" />
    <meta property="og:description" content="A seemingly easy thing to do that I could not find documentation for! string astr;foreach (DataRowView aRow in listBox1.SelectedItems ){&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicId&#8221;].ToString();&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicText&#8221;].ToString();} TopicId and TopicText are the name of the columns in the table of the Datasource that has been bound to the listbox control. Drop me a note if you..." />
    <meta name="twitter:card" content="summary" />
    <meta name="twitter:title" content="How to iterate (list) all selected items in a Databound ListBox in .NET 4.0 Winforms" />
    <meta name="twitter:url" content="https://blogs.msdn.microsoft.com/jpsanders/2010/05/07/how-to-iterate-list-all-selected-items-in-a-databound-listbox-in-net-4-0-winforms/" />
    <meta name="twitter:description" content="A seemingly easy thing to do that I could not find documentation for! string astr;foreach (DataRowView aRow in listBox1.SelectedItems ){&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicId&#8221;].ToString();&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicText&#8221;].ToString();} TopicId and TopicText are the name of the columns in the table of the Datasource that has been bound to the listbox control. Drop me a note if you..." />
    
categories:
  - Uncategorized
---
A seemingly easy thing to do that I could not find documentation for!

string astr;  
foreach (DataRowView aRow in listBox1.SelectedItems )  
{  
&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicId&#8221;].ToString();  
&nbsp;&nbsp;&nbsp; astr = aRow[&#8220;TopicText&#8221;].ToString();  
} 

TopicId and TopicText are the name of the columns in the table of the Datasource that has been bound to the listbox control.

Drop me a note if you found this useful!