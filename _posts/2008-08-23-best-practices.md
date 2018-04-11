---
layout: post
title: Best Practices
date: 2008-08-23 15:24
author: spdenne
comments: true
---

My friend [Bevan](http://www.nichesoftware.co.nz/) points out a 
[post on NUnit Best Practices](http://scottwhite.blogspot.com/2008/05/nunit-best-practices.html) by 
[Scott White](http://scottwhite.blogspot.com/), and [asks](http://www.nichesoftware.co.nz/2008/08/21/nunit-best-practices.html)
whether we agree with them.
 
<!--more-->

Most of my coding these days is in java, so some of Scott's best practices need altering to my situation, e.g.
junit.jar instead of nunit.framework.dll.
 
For reference, I disagree to varying extents with #1, #2, #3, and #5, and agree with #4, #6, and #7.
 
However I believe that best practices are often relative to the situation you find yourself in. That situation includes
which IDE you are using, and how best to use it, how large your team is, how complex your application is, etc.
 
I also think that it is an excellent idea to consider which practices consciously or unconsciously drive your coding
practice, and whether any of them could be improved. Scott himself says that 
[best practices change over time](http://scottwhite.blogspot.com/2008/07/programming-mantras.html), 
and his blog seems to have a long running theme
of identifying some of these changes. I commend him for identifying and documenting what he does, providing advice for
others to consider, and asking for feedback.
 
Here are my reasons for disagreeing with some of his NUnit best practices, from my junit in eclipse standpoint:
 
\#1
 
I primarily disagree since all too often the tests are not distributed with the code being tested. When dealing with
some-one else's code, I don't have their test cases, so if I have problems with their code, I can't simply find out
whether their test cases still work in my environment, nor whether I'm using parts of their code which are not covered
by their tests.
 
Secondly, I disagree with "don't be lazy". We should all be striving to have our best practices also be the easiest
things to do.
 
\#2 & #3
 
These are things that should be integrated into your IDE and dependency management tools. They appear to be workarounds
for poor visual studio defaults when you wish to use NUnit to test your code.
 
\#5
 
I prefer the idea of starting by writing test cases in a style that documents what you want to achieve. That then
drives what methods you need, and perhaps how they should be collected into various interfaces. I refer to this as an
idea since I'm not particularly disciplined in developing in this way.
 
Overall though, I'd say that I agree with Scott in that solid unit testing using a tool like NUnit is best practice.
