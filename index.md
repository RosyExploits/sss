---
layout: default
---

# Files in this directory


| File Name | Size |
| :--- | :--- |
{% for file in site.static_files %}
{% if file.path contains page.dir %}

| [{{ file.name }}]({{ site.baseurl }}{{ file.path }}) | {{ file.size | divided_by: 1024 }} KB |
{% endif %}
{% endfor %}
