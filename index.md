---
layout: default
title: Main Directory
---

# 📂 Current Folders
{% assign folders = "" | split: "" %}
{% for file in site.static_files %}
  {% if file.path contains page.dir %}
    {% assign parts = file.path | replace: page.dir, "" | split: "/" %}
    {% if parts.size > 1 %}
      {% unless folders contains parts[0] %}
        {% assign folders = folders | push: parts[0] %}
      {% endunless %}
    {% endif %}
  {% endif %}
{% endfor %}

{% for folder in folders %}
* [**{{ folder }} (folder)**](./{{ folder }}/)
{% endfor %}

---

# 📄 Current Files
{% for file in site.static_files %}
  {% if file.path contains page.dir %}
    {% assign parts = file.path | replace: page.dir, "" | split: "/" %}
    {% if parts.size == 1 %}
* [{{ file.name }}]({{ site.baseurl }}{{ file.path }})
    {% endif %}
  {% endif %}
{% endfor %}
