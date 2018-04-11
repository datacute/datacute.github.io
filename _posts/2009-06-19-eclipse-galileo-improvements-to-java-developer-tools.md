---
layout: post
title: Eclipse Galileo Improvements to Java Developer Tools
date: 2009-06-19 00:23
author: spdenne
comments: true
---
Here are some improvements to JDT Project in [Galileo](http://www.eclipse.org/galileo/) that I personally find useful<!--more-->:

1. Support for `{@inheritDoc}` in the javadoc popups.
   * This is encourages its use, which in turn encourages documenting *why* a method has been overridden, or
what's so special about this particular implementation, without having to repeat the purpose of the method itself.
2. Warnings when a method overrides a synchronized method, but isn’t synchronized itself.
   * It’s hard enough as it is to ensure you get the intended multi-threaded behaviour. This change can help prevent
an error that while not very common, can be very hard to spot.
3. When auto-reformatting an entire class, I can keep the line breaks that I’ve added.
   * This caters for where the formatting rules are too general, and are not aware that I’d find some things much
clearer if split into multiple lines in very specific places.
4. Constructor completion has been made more useful, by offering more appropriate suggestions.
   * I also often save myself some typing by writing the right hand side of the assignment, then using a quick assist
to assign the result to a new variable.
5. By holding down Ctrl, and hovering on a method, I can chose whether to jump to the declaration, or the
implementation.
   * I still find this method of navigation difficult though, preferring to keep my hands on the keyboard, navigating
to the method call, pressing Ctrl-T, and choosing which implementing or declaring class I wish to view. (That’s not a
new feature.)
   * What I’d like is a companion for F3’s mapping of “Go To Declaration” that with a single key press I can
“Go To Implementation”. However I can’t find that command in the key binding preferences page.


