---
layout: archive
title: "Blog"
permalink: /blog/
author_profile: true
---

{% include base_path %}

<hr>
<h2>Generative Adversarial Networks (GANs)</h2>
<hr>
{% for post in site.posts %}
    {% include archive-single.html %}
{% endfor %}

<hr>
