---
layout: archive
title: "Projects"
permalink: /projects/
author_profile: true
---

{% include base_path %}

<hr>
<h2>Generative Adversarial Networks (GANs)</h2>
{% for post in site.projects %}
    {% if post.topic == "GAN" %}
      {% include archive-single.html %}
    {% endif %}
{% endfor %}
<hr>
<h2>Natural Language Processing</h2>
{% for post in site.projects %}
    {% if post.topic == "nlp" %}
      {% include archive-single.html %}
    {% endif %}
{% endfor %}
