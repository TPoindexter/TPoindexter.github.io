---
layout: default
---

  {% for post in site.posts %}
      href="{{ post.url }}">{{ post.title }}
  {% endfor %}
