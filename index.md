---
layout: page
---

# Me in 10 seconds

# Me in 10 minutes?

See [my “about” page](about.md)

# What am I doing now?

See [my “now” page](now.md)

# Recent posts

<ul>
  {% for post in site.posts limit:5 %}
    <li><a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

[All posts]({{ site.baseurl }}/posts)
