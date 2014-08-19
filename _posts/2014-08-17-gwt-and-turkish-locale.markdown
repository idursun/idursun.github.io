---
layout: post
title:  "GWT and Turkish Locale"
date:   2014-08-17 01:03:00
tags: java gwt eclipse
comments: true
---
Well the worst thing about the java is the famious [Turkish I Problem][tr]. I wanted to try the latest version of [GWT] and found out that it suffers from this problem as well. 

What you have to fix this is to add the following to your run configuration:

`-Duser.language=en`

and everything should work fine.

[tr]: http://www.i18nguy.com/unicode/turkish-i18n.html
[GWT]: http://www.gwtproject.org/
