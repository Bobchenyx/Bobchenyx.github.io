---
permalink: /publications/
author_profile: true
---

<h2 id="publications" class="pub-heading">📝 Publications
  <span class="pub-heading-meta">
    | <a href="{{ site.author.googlescholar }}" target="_blank" rel="noopener noreferrer">Google Scholar &gt;</a>
    | <span class="pub-legend"><sup>*</sup> Equal contribution &nbsp; <sup>†</sup> Corresponding author</span>
  </span>
</h2>

{% assign sorted_pubs = site.publications | sort: 'date' | reverse %}
{% for post in sorted_pubs %}
{% include paper-box.html pub=post %}
{% endfor %}

{% include page-styles.html %}
