---
layout: post
title: Eclipse Helios Mostly Works
date: 2010-07-30 17:00
author: spdenne
comments: true
---
For development at work, I downloaded and started using Eclipse Helios packaged for J2EE development, wanting to see
what I could stumble upon as new or different, and whether I could recommend it to the rest of my team yet without
having to describe a whole lot of changes to our practices.

<!--more-->

We use a multi-module maven project, using mvn eclipse:eclipse to generate our eclipse projects, and that continued to
work just fine, with the projects seeming to be imported without issue.

I noticed that [Tomcat 7](http://tomcat.apache.org/tomcat-7.0-doc/index.html) is now listed in the set of servers that
can be configured, and indeed the [WTP 3.2.0 New and Noteworthy](http://www.eclipse.org/webtools/releases/3.2.0/NewAndNoteworthy/)
lists that in it's "Servers" section. Handy, but as we're hosting our own application, we do not need to test against Tomcat 7 yet.

I next noticed that the view of web projects added to the server included a couple of jars. Strange. I still haven't
figured out why a small number of the many included jars get shown in that view.

The first thing I tried to investigate showed that specifying what gets deployed as part of your web application has
been changed too. That's shown in the Java EE section of WTP's New and Noteworthy.

The applications deployed and ran ok, though a number of times I've tried starting tomcat only to have it complain that
one of the web applications can't find hibernate classes, and looking in the deployed directory, the jar is indeed
missing.

The next thing I noticed is that a whole lot of classes now show warnings. Apparently I should now change from using
@SuppressWarnings("unchecked") to the new and more accurate @SuppressWarnings("rawtypes") or according to the
[JDT New and Noteworthy](http://download.eclipse.org/eclipse/downloads/drops/R-3.6-201006080911/eclipse-news-part2.html), set the
suppressRawWhenUnchecked=true system property when starting eclipse.

Another JDT change highlighted that our method of starting up one of our application included an unused object
allocation. That actually highlighted that we were starting threads from within a constructor... something that is rife
with difficulties, and to be discouraged.

While investigating what [various people on StackOverflow recommend for eclipse.ini options](http://stackoverflow.com/questions/142357/what-are-the-best-jvm-settings-for-eclipse) I discovered the details
of Oracle's changing the executable and libraries' organisation meta-data, and how eclipse has been using those to
identify Sun's JVM and apply Sun's -XX:MaxPermSize setting. Oracle have changed the organisation back again for build 7
of Java 6 update 21.

I have not yet started using Helios for personal projects, since for the last little while I've been trying my hand at
creating an Android application, implementing a nice looking [Tree Mapping View](http://www.datacute.co.nz/pgquilt/pgquilt.html) showing space used by a various tables and indexes of a PostgreSQL
database. The page detailing how to set up the [eclipse plugins for Android development](http://developer.android.com/sdk/eclipse-adt.html) still says: "There are known issues with the ADT plugin
running with Eclipse 3.6. Please stay on 3.5 until further notice."

So far this sounds like a *lack of any compelling reasons to upgrade*.

**However…**

Using the market to install the SVN plugins we use was a much nicer experience than in previous versions, and being
able to find out about other plugins from within eclipse is great.

I’m also going to start using package name abbreviations, so that all our packages of the format:
```
nz.co.mycompany.myproduct.subcomponentA.internalpackage1
```
can be nicely and succinctly shown as
```
{A}.internalpackage1
```

Something I usually do with a new eclipse installation is tune the startup parameters, editing the eclipse.ini file to
show me the workspace location. This is because I often work with multiple workspaces, one showing the current
production code for investigating symptoms and behaviour of the production system, and one showing later code with a
number of development changes. Eclipse 3.6 has a new preferences option that lets you specify a workspace name to show
in the title, which works much better as you do not need to restart eclipse for it to take affect, you can use a short
code for your workspace, and it appears first in the title, before the perspective and application name.

Lastly I’m looking forward to experimenting with all the new options for controlling the formatter. I believe I can
finally now get it set up to alter the code formatting to my liking more consistently.
