---
layout: default
title: Home
---

{% include navigation.html %}

More information will go here as I decide how I want to build this site out.

<div class="posts">
    {% for post in site.posts %}
    <ul>
      <li><span>{{ post.date | date_to_string }} </span> <a href="{{ post.url }}">{{ post.title }}</a></li>
    </ul>
    {% endfor %}
</div>
