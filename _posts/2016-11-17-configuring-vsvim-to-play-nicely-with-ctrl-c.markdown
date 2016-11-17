---
layout: post
title:  "Configuring VsVim to be friendly with Ctrl+C in Visual Studio"
date:   2016-11-17 11:00:00
tags: vsvim visual-studio
---

I am used to expecting Ctrl+C to copy selected text in Visual Studio whereas the same command cancels the command series in Vim. So it is confusing me when I am using VsVim, command can do either of those.

To solve this I have added this configuration to vsvimfile.

{% highlight %}
vmap <C-c> "*y
{% endhighlight %}

Now when in visual mode, Ctrl+C copies the text and also ends the command.
