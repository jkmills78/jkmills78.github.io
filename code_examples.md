---
layout: page
title: Code Examples
description: These are various code examples that I have built to help remind myself of how to do certain tasks.
---

{% for code in site.code_examples %}
<div class="code">
    <h2><a href="{{code.path}}">{{code.title}}</a></h2>
    <div class="code-synopsis">
        {{ code.description }}
</div>
{% endfor %}