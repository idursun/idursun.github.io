---
layout: post
title:  "Changing default typescript compiler in Visual Studio Code"
date:   2016-07-11 10:00:00
tags: vscode typescript
---
In order to use a custom typescript for a specific project you need to create a settings.json file in `.settings` folder and add the following content to it:
{% highlight json %}
{
  "typescript.tsdk": "node_modules/typescript/lib"
}
{% endhighlight %}

Restart VsCode.

