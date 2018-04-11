---
layout: post
title: Eclipse Ganymede Features
date: 2008-06-08 00:55
author: spdenne
comments: true
---
The Eclipse Ganymede release is only a few weeks away. As a long time eclipse user, inquisitive, early adopter, I've
been trying the milestone and release candidates of the java developer tools components. <!--more--> (Ganymede is a coordinated
release of an [enormous number of eclipse projects](http://wiki.eclipse.org/Ganymede). Several packages are available
[here](http://www.eclipse.org/downloads/packages/).)

The list of new features is no longer as easy to find, since it was linked to from the download page for the milestone
releases, and since the releases are now release candidates, there are no new features.

These will no doubt be combined into a single what's new page for the final release, but until then, the lists for each
milestone release are well worth a read:
[M1](http://archive.eclipse.org/eclipse/downloads/drops/S-3.4M1-200708091105/eclipse-news-M1.html) [M2](http://archive.eclipse.org/eclipse/downloads/drops/S-3.4M2-200709210919/eclipse-news-M2.html) [M3](http://archive.eclipse.org/eclipse/downloads/drops/S-3.4M3-200711012000/eclipse-news-M3.html) [M4](http://archive.eclipse.org/eclipse/downloads/drops/S-3.4M4-200712131700/eclipse-news-M4.html) [M5](http://archive.eclipse.org/eclipse/downloads/drops/S-3.4M5-200802071530/eclipse-news-M5.html) [M6](http://archive.eclipse.org/eclipse/downloads/drops/S-3.4M6-200803301350/eclipse-news-M6.html) [M7](http://archive.eclipse.org/eclipse/downloads/drops/S-3.4M7-200805020100/eclipse-news-M7.html)

**Update:** As expected, the release of 3.4 is accompanied by a new
[New and Noteworthy](http://ganymede-mirror2.eclipse.org/eclipse/downloads/drops/R-3.4-200806172000/whatsnew3.4/eclipse-news.html)
page. What's also worth reviewing is the [feature comparison](http://www.eclipse.org/downloads/packages/compare-packages) 
page for the various Ganymede packages.

My personal favourite dozen new features:

1. System Proxy Settings - One less place to change those settings when I plug the laptop in somewhere new.
2. Default console and file encoding - I develop on Windows for Linux.
3. Shearing - I love the pun.
4. The improved error log view, and the Plug-in registry view enhancements - these will help when trying out
misbehaving plug-ins.
5. Line support in overview ruler - much faster navigation.
6. Runnable JAR export wizard - no more searching for and installing third party plug-ins to do this simple thing.
7. Different highlighting for read and write occurrences of the selected or searched for element - this is fantastic.
8. Direct interaction with text hovers - less hand movement is good. Being able to click through to other javadocs is
fantastic.
9. Breadcrumb navigation - this is a quite good compromise between ease of use and screen real estate.
10. Support for external class folders - I haven't used this yet, but can think of some past experiences where it
would have been useful.
11. Java compiler on multi-CPU machines - parallelisation is how we go faster these days.
12. Quick Assist becomes even more helpful.

Eclipse's quick assist feature saves a huge amount of work. There's no need to go looking through menus and dialogs to
find the right place to activate the thing you want to do right now, you simply hit Ctrl-1 and what you want to do is
invariably in the short list that immediately pops up. The "what's new" pages list these additional assists and fixes:

- M1
  * Helps with regular expressions in find/replace
  * Helps correct spelling in CVS commits
- M2
  * PDE Quickfix for Java file issues
  * Add @throws or @exception javadoc tag
  * Select a missing method error in the Problems view and Quick Fix
  * Create getter and setters for fields (encapsulate fields)
  * Extract method on expressions
  * Helps with the new SWT Templates
  * Helps with user created templates
- M3
  * Code completion helps with casts
  * Complete static members of not yet imported types
- M4
  * Ensure source entries found in build.properties are properly accounted for in the plug-in manifest
  * Diagnosis (and removal quick fix) of redundant superinterfaces
  * Improved key binding support
  * Convert to StringBuffer
- M5
  * Improved cursor jumping
- M6
  * New Javadoc tags to annotate (PDE) API with explicit restrictions
  * Quick fix provided for missing or incorrect @since tags
  * The Java problem hover now offers all available quick fixes
  * Use MessageFormat for string concatenation
  * Extract local variable (without replacing all occurrences)
  * only show templates applicable at the current location
- M7
  * Remove invalid use of API Javadoc tags
  * Inserting parameter name also shows guessed arguments
  * Shows gory details of improved text search
