---
layout: default
---

<h1>最新文章</h1>
<ul>
{% for post in site.posts %}
  <li>
    <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a>
    <span>{{ post.date | date: "%Y-%m-%d" }}</span>
  </li>
{% endfor %}
</ul>
