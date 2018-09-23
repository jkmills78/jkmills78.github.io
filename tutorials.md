---
layout: default
title: Code Examples
description: These are various code examples that I have built to help remind myself of how to do certain tasks.
---

{% for code in site.tutorials %}
<div class="code mb-5">
    <h4><a href="{{ code.url }}">{{ code.title }}</a><div class="dropdown-divider"></div></h4>
    <div class="code-synopsis">
        {{ code.description }}
    </div>
</div>
{% endfor %}