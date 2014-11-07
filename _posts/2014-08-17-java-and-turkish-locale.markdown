---
layout: post
title:  "Java and Turkish Locale"
date:   2014-08-17 01:03:00
tags: java
comments: true
---
Well the worst thing about the java is the famious [Turkish I Problem][tr]. For example [Akka][akka] framework has this bug which has been fixed at 2.4 version which has not been released yet. [GWT][GWT] also has this problem.

I was looking for a permanent solution to fix this once for all and this worked:

Create an environment variable named `_JAVA_OPTIONS` and set its value to `-Duser.language=en`

and everything should work fine.

[tr]: http://www.i18nguy.com/unicode/turkish-i18n.html
[GWT]: http://www.gwtproject.org/
[akka]: http://www.akka.io/
