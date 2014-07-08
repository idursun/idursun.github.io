---
layout: post
title:  "Getting started with the Spring Framework"
date:   2014-06-17 11:28:17
tags: java spring rest
---
I am not a java guy. I don't like java at all but out of curiousity I am experimenting with [Spring Framework][spring] nowadays. 

I want to a single page application with a restful backend using whatever is provided by the Spring Framework. Eventually I am going to deploy it to a Linux server by using [Dokku][dokku].

Whenever I heard the name Spring Framework I immediately thought of XML files and it made my head spin but it is not the case anymore. [Spring Boot][spring-boot] project makes it possible to kick start a project with zero XML configuration. 

All you have to do is to set parent to the following in your pom file.
{% highlight xml %}
<parent>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-parent</artifactId>
    <version>1.1.3.RELEASE</version>
</parent>
{% endhighlight %}

and then you can start adding starter packs as dependencies. In my case I want to have Spring data and rest libraries present so I add the following dependencies.
{% highlight xml %}
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>

<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-rest</artifactId>
</dependency>
{% endhighlight %}

You might not able to or don't want to change the parent of your pom file, so in that case you can add the following bits instead: 

{% highlight xml %}
 <dependencyManagement>
    <dependencies>
        <dependency>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-dependencies</artifactId>
            <version>1.1.1.RELEASE</version>
            <type>pom</type>
            <scope>import</scope>
        </dependency>
    </dependencies>
</dependencyManagement>
{% endhighlight %}

In order to kick start your application add a class to your project like the following:

{% highlight java %}
@Configuration
@ComponentScan
@EnableAutoConfiguration
public class Application extends SpringBootServletInitializer {

    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }

}
{% endhighlight %}

You should be good to go.

[spring]: http://spring.io/
[spring-boot]: http://projects.spring.io/spring-boot
[dokku]: https://github.com/progrium/dokku
