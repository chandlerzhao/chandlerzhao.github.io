---
layout: default
---

<ul>
{% for post in site.posts %}
  <li>
    <a href="{{ post.url }}">
      <h2>{{ post.title }} - {{ post.date | date : "%F"}}</h2>
    </a>
  </li>
{% endfor %}
</ul>


jekyll命令运行时间：{{site.time | date: "%F %T"}}

