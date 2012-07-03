---
layout: post
title: "Just Loop on"
date: 2012-07-03 23:52
comments: true
categories: [javascript, loop, html, audio tag]
---
I can't be the only one who listens to a song on loop. White waiting for Tommy and Zi to wrap up work, here is something embarrassingly simple that does the looping, if you uses an audio tag and happen to have Zepto/jQuery like I do that is.

{% codeblock lang:javascript %}
$('audio').on('ended', function(){
  this.currentTime = 0;
  this.play();
})
{% endcodeblock %}