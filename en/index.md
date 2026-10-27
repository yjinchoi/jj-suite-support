---
layout: default
lang: en
permalink: /en/
alt: /
description: "Privacy policies and support pages for Easy Web Image Collector, Easy NAS Photo Viewer Easy NAS Download Manager and NAS Player"
---
# jj-suite app support

<p class="lead">Privacy policies and support pages for the following iOS and tvOS apps.</p>

<ul class="app-list">
{%- for pair in site.data.apps %}
{%- assign slug = pair[0] %}{%- assign app = pair[1] %}
{%- capture p_url %}/en/{{ slug }}/privacy/{% endcapture %}{%- capture s_url %}/en/{{ slug }}/support/{% endcapture %}
  <li>
    <img src="{{ app.icon | relative_url }}" alt="">
    <div>
      <strong>{{ app.name }}</strong>
      <span class="sub">{{ app.subtitle_en }}</span>
      <span class="links"><a href="{{ p_url | relative_url }}">Privacy Policy</a> · <a href="{{ s_url | relative_url }}">Support</a></span>
    </div>
  </li>
{%- endfor %}
</ul>
