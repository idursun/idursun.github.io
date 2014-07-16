---
layout: post
title:  "Adding dokku configuration to a spring boot project"
date:   2014-07-18 16:28:17
tags: java spring-boot dokku 
comments: true
---
You have to add following files to your repository to run your [spring boot][spring-boot] applications after pushing to dokku remote.

Add a file called *Procfile* with the following content:
{% highlight bash %}
web: java $JAVA_OPTS -Dserver.port=$PORT -jar target/APPJAR
{% endhighlight %}

where *APPJAR* is the name of the jar file created by running `mvn package`

another file called: *system.properties*
{% highlight bash %}
java.runtime.version=1.7
{% endhighlight %}

[spring-data]: http://projects.spring.io/spring-data
[spring-boot]: http://projects.spring.io/spring-boot
