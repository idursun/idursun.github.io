---
layout: post
title:  "Changing the base url of your rest endpoint"
date:   2014-06-18 11:28:17
tags: java spring-data 
comments: true
---

[Spring Data][spring-data] is great. It just works out of the box. The only thing I wanted to change was the base url of my repositories to /rest instead of the root. I've managed it by adding following class to my project.

{% highlight java %}

@Configuration
@Import(RepositoryRestMvcConfiguration.class)
public class MyRestConfig extends RepositoryRestMvcConfiguration {
    private static Log logger = LogFactory.getLog(MyRestConfig.class);

    @Override 
    protected void configureRepositoryRestConfiguration(RepositoryRestConfiguration config) {
        try {
            config.setBaseUri(new URI("/rest"));
        } catch (URISyntaxException e) {
            logger.error("failed to set base uri", e);
        }
    }
}

{% endhighlight %}

[spring-data]: http://projects.spring.io/spring-data
