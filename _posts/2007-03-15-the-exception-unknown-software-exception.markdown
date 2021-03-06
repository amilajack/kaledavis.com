--- 
layout: post
title: The exception unknown software exception (a.k.a. SysFader)
wordpress_url: http://kaledavis.com/2007/03/15/the-exception-unknown-software-exception/
---

> **Update 7/10/07**: kerwin left a comment about a new KB article and hotfix that Microsoft just released.  We tested it yesterday on a machine with both 2003 and 2007 Office components and it seemed to fix the error.  Note that although both the article and hotfix specify WSS 3.0 / MOSS 2007, it also should work with 2.0/2003 (which makes sense, this is a client issue). Thanks kerwin for the information and to all the other people who left helpful comments.

You have to enjoy that helpful IE7 error message right?  This past Monday I started getting an error everytime I tried to open an Office document from SharePoint 2003 (to be specific, a WSS 2.0 Team Site).

The exact error was:

    SysFader: iexplore.exe - Application Error : The exception unknown software exception (0xc06d007f)
    occurred in the application at location 0x7c812a5b.

After some searching, I found only one related link on SharePoint University that was close to what I was seeing.  It wasn't much help and basically said to reload XP, not the solution I was looking for.  I then started looking into the IE7 add-ons (Internet Options -&gt; Programs -&gt; Manage add-ons) and disabled the SharePoint ones I found.  That fixed it! Seems like the SharePoint OpenDocuments Class was causing the error.  With it disabled I was able to open the document, however it reduced the functionality of the drop down by removing the "Edit with..." option.

After a search for SharePoint OpenDocuments Class I found the answers in several blogs (Outlook by the sound, Shaune Donohue, and Michael Becker).  The issue is conflicting versions of the OWSSUPP.DLL file because you have both Office11 and Office12 installed.  You can check for these two folders in C:\Program Files\Microsoft Office.  I had both because I had installed Visio and Project 2007 while still running 2003 for the rest of the suite.  I renamed the Office12 version (once I am off of Office 2003 I will change this back) and enabled the add-on and everything works great.
The funny part is none of these blogs mentioned the error message (maybe they were getting a different one?), so I couldn't find them on my initial search.  Hopefully this post will be the "bridge" for others who get this annoying error message so that you can find the easy fix.  The only question that remains is what changed to start causing this (I've had Visio 2007 installed for at least five months).  If I find the answer to that I will update this or if you know please leave a comment.   
