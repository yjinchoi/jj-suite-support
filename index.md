---
layout: default
lang: ko
permalink: /
alt: /en/
description: "Easy Web Image Collector · Easy NAS Photo Viewer · Easy NAS Download Manager 의 개인정보 처리방침과 지원 페이지"
---
# jj-suite 앱 지원

<p class="lead">아래 iOS 앱들의 개인정보 처리방침과 지원 페이지입니다.</p>

<ul class="app-list">
{%- for pair in site.data.apps %}
{%- assign slug = pair[0] %}{%- assign app = pair[1] %}
{%- capture p_url %}/{{ slug }}/privacy/{% endcapture %}{%- capture s_url %}/{{ slug }}/support/{% endcapture %}
  <li>
    <img src="{{ app.icon | relative_url }}" alt="">
    <div>
      <strong>{{ app.name }}</strong>
      <span class="sub">{{ app.subtitle_ko }}</span>
      <span class="links"><a href="{{ p_url | relative_url }}">개인정보 처리방침</a> · <a href="{{ s_url | relative_url }}">지원</a></span>
    </div>
  </li>
{%- endfor %}
</ul>
