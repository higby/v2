---
layout: index
title: Branden Higby
permalink: /index.html
---
{%- assign date_format = "%b %-d, %Y" -%}
{% capture order %}essays,poetry,collections,programming,misc{% endcapture %}
{% assign order = order | split: "," %}
<nav>
<table>
{% for heading in order %}
{% for tag in site.tags %}
{% if tag[0] == heading %}
<tbody>
<tr>
<th colspan="2">
  {{ tag[0] | capitalize }}
</th>
</tr>
{% for post in tag[1] %}
  {% unless post.draft and jekyll.environment == "production" %}
<tr>
  <td>
    <time>{{ post.date | date: date_format }}</time>
  </td>
  <td>
    <a href="{{ post.url | relative_url | remove: ".html" }}" {% unless post.setup.style %}class="internal{% if post.draft %} draft{% endif %}" {% else %} {% if post.draft %} class="draft"{% endif %}{% endunless %}>{{ post.title | escape }}</a>
  </td></tr>
{% endunless %}
{% endfor %}
</tbody>
{% endif %}
{% endfor %}
{% endfor %}
</table>
</nav>
