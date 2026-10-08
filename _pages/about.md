---
permalink: /
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

<h2 id="about">About</h2>

I am an Engineer at <span class="nowrap"><img class="inline-logo" src="{{ '/images/logos/motional.jpeg' | relative_url }}" alt="Motional">Motional</span>, contributing to the mission to make driverless vehicles a safe, reliable, and accessible reality.

I was fortunate to work on efficient AI and large model deployment at
<span class="nowrap"><img class="inline-logo" src="{{ '/images/logos/embodyx.jpeg' | relative_url }}" alt="EmbodyX">EmbodyX</span> and
<span class="nowrap"><img class="inline-logo" src="{{ '/images/logos/northeastern.jpeg' | relative_url }}" alt="Northeastern">Northeastern</span> University, working with
[Weiwei Chen](https://www.linkedin.com/in/weiwei-c-01029421) and
[Yanzhi Wang](https://www.yanzhiwang.com/). Before that, I was a Software
Engineering Co-op at <span class="nowrap"><img class="inline-logo" src="{{ '/images/logos/cognex.png' | relative_url }}" alt="Cognex">Cognex</span> Corporation, working with
[Soon Neoh](https://www.linkedin.com/in/soon-neoh-230a073) on VisionPro software.

I received my M.S. from Northeastern University and my B.E. from Beijing University of Technology.

{% include experience.html %}

<h2 id="education">Education</h2>

<ul class="timeline with-logos">
  <li>
    <img class="timeline-logo" src="{{ '/images/logos/northeastern.jpeg' | relative_url }}" alt="Northeastern University logo">
    <div>
      <strong>M.S. in Electrical and Computer Engineering</strong>, Northeastern University
      <span class="timeline-meta">09/2021 – 12/2023 · Boston, MA</span>
    </div>
  </li>
  <li>
    <img class="timeline-logo" src="{{ '/images/logos/bjut.png' | relative_url }}" alt="Beijing University of Technology logo">
    <div>
      <strong>B.E. in Electrical Engineering</strong>, Beijing University of Technology
      <span class="timeline-meta">09/2017 – 05/2021 · Beijing, China</span>
    </div>
  </li>
</ul>

<h2 id="publications" class="pub-heading">📝 Selected Publications
  <span class="pub-heading-meta">
    | <a href="{{ '/publications/' | relative_url }}">See All Publications &gt;</a>
    | <span class="pub-legend"><sup>*</sup> Equal contribution &nbsp; <sup>†</sup> Corresponding author</span>
  </span>
</h2>

{% assign sorted_pubs = site.publications | where_exp: "p", "p.selected != false" | sort: 'date' | reverse %}
{% for post in sorted_pubs %}
{% include paper-box.html pub=post %}
{% endfor %}

{% include page-styles.html %}
