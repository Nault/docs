---
layout: default
---

<h1>Welcome to Nault!</h1>
Here you will find any related documentation for [nault.cc](https://nault.cc).

Source code: [https://github.com/Nault/Nault](https://github.com/Nault/Nault)

<div class="posts">
  {% for post in site.posts %}
    <article class="post">

      <h2><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></h2>

      <div class="entry">
        {{ post.excerpt }}
      </div>

      <a href="{{ site.baseurl }}{{ post.url }}" class="read-more">Read More</a>
    </article>
  {% endfor %}
</div>
