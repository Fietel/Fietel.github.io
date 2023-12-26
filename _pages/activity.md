---
layout: archive
title: "Selected Activity"
permalink: /activity/
author_profile: true
---

{% include base_path %}

<hr>
2024: [Accepted journal paper at ACM SIGKDD Explorations]({% link _activity/2023-11-30-icdm.md %}) <br />
2023: [Accepted Conference Paper at IEEE ICDM Workshop on AI for time series data]({% link _activity/2023-11-30-icdm.md %})<br />
2023: [Interview with "Stern"](https://www.stern.de/stern-studien/stern-studie--arbeitgeber-mit-zukunft-in-deutschland-33701470.html) on working at e.mundo <br />
2023: Guest lecture at University of Siegen - Data Science in Medicine<br />
2022: [SFScon conference talk on reproducible machine learning](https://www.sfscon.it/talks/heading-towards-reproducible-machine-learning-research-for-medical-data/)<br />
2022: Published article at informatik-aktuell on [reproducible machine learning (german)](https://www.informatik-aktuell.de/betrieb/kuenstliche-intelligenz/<br />ecgan-reproduzierbares-maschinelles-lernen-fuer-ekg-daten.html)<br />
2021: [Published blog post](https://blog.e-mundo.de/post/ecgan-a-framework-for-reproducible-research-on-ecg-data/) on ecgan <br />
2021: [Published ecgan](https://github.com/emundo/ecgan), an open source reproducible ML framework to generate time series data and detect anomalies<br />
2020: [Article in ACM XRDS](https://dl.acm.org/doi/abs/10.1145/3416059) on modular chatbot architectures<br />
2020: Published article at informatik-aktuell on [modular chatbot architectures (german)](https://www.informatik-aktuell.de/betrieb/kuenstliche-intelligenz/chatbot-zaehmen-leicht-gemacht.html)<br />
2019: [Accepted paper](https://ieeexplore.ieee.org/abstract/document/8955499) at IEEE ICDM PhD Forum on GAN based anomaly detection in time series data <br />
2019: [SFScon conference talk](https://www.sfscon.it/talks/how-to-tame-your-chatbot/) on modular chatbot architectures<br />
2018: Published article at informatik-aktuell on [natural language understanding (german)](https://www.informatik-aktuell.de/betrieb/kuenstliche-intelligenz/natural-language-understanding-nlu.html)<br />

<hr>
<h2>More details on some topics</h2>
<hr>
{% assign reversed_activity = site.activity | reverse %}
{% for post in reversed_activity %}
  {% include archive-single.html %}
{% endfor %}

<hr>
