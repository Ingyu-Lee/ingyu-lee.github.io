---
layout: posts
title:  "Welcome to Jekyll!"
---

<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ "post.title0" }}</a>
    </li>
    <li>
      <a href="{{ post.url }}">{{ "post.title1" }}</a>
    </li>
  {% endfor %}
</ul>

# Welcome

**Hello world**, this is my first Jekyll blog post.

I hope you like it!

... which is shown in the screenshot below:
![My helpful screenshot](/assets/screenshot.png)
