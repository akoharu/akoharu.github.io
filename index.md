---
layout: default
title: Home
---

<header class="clean" style="height: 350px; background-image: url({{ site.cover }});">
	{% include top.html %}
	<div id="home-title">
		<a href="{{ site.url }}">
			<img src="{{ site.me }}" class="site-icon">
		</a>
	</div>
</header>
<ul>
  {% for post in site.posts %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      {{ post.excerpt }}<br>
    </li>
  {% endfor %}
</ul>
<footer class="clean" style="background-image: url({{ site.cover }}); background-position: bottom; height: 60px;">
	<p class="copyright">&copy;{{ site.time | date: "%Y" }}, <a href="{{ site.copyright.url }}" target="_blank">{{ site.copyright.author }}</a>. <a href="{{ site.copyright.type_url }}" target="_blank">{{ site.copyright.type_title }}</a>.</p>
</footer>
