---
layout: post
title:  "Spring Security, OAuth and CORS"
date:   2014-08-14 15:09:00
tags: java spring-boot spring-security cors
comments: true
---
If your frontend and api service reside on different domains then you have to enable [CORS][cors] on the backend.

What you have to do is to add a CORS filter that can reply to OPTIONS requests.

{% highlight java %}
@Component
public class CorsFilter extends OncePerRequestFilter {

    @Override
    protected void doFilterInternal(HttpServletRequest request, HttpServletResponse response, FilterChain filterChain) throws ServletException, IOException {
        response.setHeader("Access-Control-Allow-Origin", "*");
        if ("OPTIONS".equals(request.getMethod())) {
            response.setHeader("Access-Control-Allow-Methods", "POST, GET, OPTIONS, DELETE");
            response.setHeader("Access-Control-Max-Age", "3600");
            response.setHeader("Access-Control-Allow-Headers", "authorization, content-type");
        }
        filterChain.doFilter(request, response);
    }
}
{% endhighlight %}

But there is still a problem to be solved. `/oauth/token` has basic authentication enabled. Chrome sends Authorization header in the OPTIONS request whereas Firefox does not and this causes preflight request to fail.

To solve this you should add a custom WebSecurityConfigurer which has a lower order than default oauth security configurer.

{% highlight java %}
@Configuration
@Order(-1)
public class CorsConfig extends WebSecurityConfigurerAdapter {
    @Override
    protected void configure(HttpSecurity http) throws Exception {

        http.requestMatchers().antMatchers(HttpMethod.OPTIONS, "/oauth/token", "/rest/**")
            .and()
                .csrf().disable()
            .authorizeRequests().anyRequest().permitAll()
            .and()
                .sessionManagement().sessionCreationPolicy(SessionCreationPolicy.STATELESS);
    }
}
{% endhighlight %}

This is going to disallow http basic authentication on /oauth/token for OPTIONS method.

[cors]: http://en.wikipedia.org/wiki/Cross-origin_resource_sharing