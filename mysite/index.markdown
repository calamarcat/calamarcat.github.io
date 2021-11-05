---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
---
<main>
  {% for post in site.posts %}
      <h1><a href="{{ post.url }}">{{ post.title }}</a></h1>
      <p><em>{{ post.shortdate }} | {{ post.categories | join: ', ' }}</em></p>
      {{ post.excerpt }}
      {% if post.content.size > post.excerpt.size %}
        <p><a href="{{ post.url }}">(Read more...)</a></p>
      {% endif %}
    {% if forloop.last == false %}
      <hr>
    {% endif %}
  {% endfor %}
  </main>