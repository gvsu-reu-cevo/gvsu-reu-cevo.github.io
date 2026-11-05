---
layout: page
# title: Posts
# subtitle: Recent Posts
---

<div class="post-index">
{% assign postsCategory = site.posts | group_by_exp: "post", "post.categories" %}
{% for category in postsCategory %}
  <div class="post-group__head">
    <h3>{% if category.name != "" %}{{ category.name }}{% else %}Uncategorized{% endif %}</h3>
    <!-- <span class="post-group__count">{{ category.items | size }} post{% if category.items.size != 1 %}s{% endif %}</span> -->
    <span class="post-group__rule"></span>
  </div>

  <ul class="list-posts">
  {% for post in category.items %}
    <li>
      <a class="post-row" href="{{ post.url | prepend: site.baseurl }}">
        <span class="post-row__date">
          <span class="post-row__day">{{ post.date | date: "%d" }}</span>
          <span class="post-row__mon">{{ post.date | date: "%b %Y" }}</span>
        </span>
        <span class="post-row__title">{{ post.title }}</span>
        <span class="post-row__meta">{{ post.subtitle | strip_html | truncate: 90 }}</span>
        <span class="post-row__arrow" aria-hidden="true">&rarr;</span>
      </a>
    </li>
  {% endfor %}
  </ul>
{% endfor %}
</div>

<!-- original -->
<!-- <div>
{% assign postsCategory = site.posts | group_by_exp:"post", "post.categories"  %}
{% for category in postsCategory %}
<h4 class="post-teaser__month">
<strong>
{% if category.name %} 
&raquo; {{ category.name }}
{% else %} 
{{ Print }} 
{% endif %}
</strong>
</h4>
<ul class="list-posts">
{% for post in category.items %}
<li class="post-teaser">
<a href="{{ post.url | prepend: site.baseurl }}">
<span class="post-teaser__title">{{ post.title }}</span>
<span class="post-teaser__date">{{ post.date | date: "%d %B %Y" }}</span>
</a>
</li>
{% endfor %}
</ul>
{% endfor %}
</div> -->