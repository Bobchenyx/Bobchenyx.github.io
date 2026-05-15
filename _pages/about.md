---
permalink: /
title: ""
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

<h2 id="about">About</h2>

I am a Machine Learning Engineer at EmbodyX Inc. & AIbao LLC. I started with real-time AI systems, building TTS-integrated chatting avatars and streaming pipelines. From there, I moved into MoE large model compression — pruning, quantization, and edge deployment. Recently, I have been exploring MoE efficient decoding and picking up vibe coding along the way. I am also a passionate open-source enthusiast and enjoy contributing to the community whenever I can.

Previously, I worked as a Software Engineering Co-op at Cognex Corporation, where I developed .NET wrapper layers and contributed to VisionPro software.

I received my M.S. in Electrical and Computer Engineering from Northeastern University and my B.E. in Electrical Engineering from Beijing University of Technology.

<h2 id="research-interests" class="no-underline">Research Interests</h2>

<div class="interest-tags">
  <span>MoE Efficient Decoding &amp; LLM Compression</span>
  <span>Edge Computing &amp; On-device AI Inference</span>
  <span>Computer Vision &amp; Autonomous Driving Perception</span>
</div>

<h2 id="publications" class="pub-heading">📝 Selected Publications
  <span class="pub-heading-meta">
    | <a href="{{ site.author.googlescholar }}" target="_blank" rel="noopener noreferrer">See All Publications &gt;</a>
  </span>
</h2>

{% assign sorted_pubs = site.publications | sort: 'date' | reverse %}
{% for post in sorted_pubs %}
<div class="paper-box">
  <div class="paper-box-image">
    {% if post.teaser and post.teaser != '' %}
    <img src="{{ '/images/' | append: post.teaser | relative_url }}" alt="paper teaser">
    {% else %}
    <img src="{{ '/images/paper-placeholder.svg' | relative_url }}" alt="paper teaser">
    {% endif %}
  </div>
  <div class="paper-box-text">
    <p class="paper-title">{{ post.title }}</p>
    {% if post.authors and post.authors != '' %}
    <p class="paper-authors">{{ post.authors }}</p>
    {% endif %}
    {% if post.description and post.description != '' %}
    <p class="paper-desc">{{ post.description }}</p>
    {% endif %}
    <p class="paper-links">
      {% if post.paperurl and post.paperurl != '' %}
        <a class="pub-venue" href="{{ post.paperurl }}" target="_blank" rel="noopener noreferrer">{{ post.venue }}</a>
      {% else %}
        <span class="pub-venue">{{ post.venue }}</span>
      {% endif %}
      {% if post.paperurl and post.paperurl != '' %}
        &nbsp;|&nbsp;<a class="pub-text-link" href="{{ post.paperurl }}" target="_blank" rel="noopener noreferrer"><i class="fas fa-file-pdf"></i> Paper</a>
      {% endif %}
      {% if post.projecturl and post.projecturl != '' %}
        &nbsp;|&nbsp;<a class="pub-text-link" href="{{ post.projecturl }}" target="_blank" rel="noopener noreferrer"><i class="fas fa-globe"></i> Project</a>
      {% endif %}
      {% if post.coderepo and post.coderepo != '' %}
        &nbsp;|&nbsp;<a href="{{ post.codeurl }}" target="_blank" rel="noopener noreferrer"><img src="https://img.shields.io/github/stars/{{ post.coderepo }}?style=social&label=Code%20Stars&logoColor=2c4a88" alt="Code Stars" class="stars-badge"></a>
      {% endif %}
    </p>
  </div>
</div>
{% endfor %}

<h2 id="education">Education</h2>

<ul class="timeline">
  <li>
    <strong>M.S. in Electrical and Computer Engineering</strong>, Northeastern University
    <span class="timeline-meta">09/2021 – 12/2023 · Boston, MA</span>
  </li>
  <li>
    <strong>B.E. in Electrical Engineering</strong>, Beijing University of Technology
    <span class="timeline-meta">09/2017 – 05/2021 · Beijing, China</span>
  </li>
</ul>

<h2 id="experience">Experience</h2>

<ul class="timeline">
  <li>
    <strong>Machine Learning Engineer</strong>, EmbodyX Inc. &amp; AIbao LLC
    <span class="timeline-meta">05/2024 – Present</span>
  </li>
  <li>
    <strong>Software Engineering Co-op</strong>, Cognex Corporation
    <span class="timeline-meta">01/2023 – 08/2023 · Natick, MA</span>
  </li>
</ul>

<style>
/* widen the main container + breathing room — desktop only */
@media (min-width: 64em) {
  #main { padding-left: 4em; }
}
@media (min-width: 80em) {
  #main { max-width: 1380px; }
}
h2.no-underline {
  border-bottom: none;
  padding-bottom: 0;
}
html {
  scroll-behavior: smooth;
}
/* Offset anchor jumps so content isn't hidden under the sticky masthead */
h2[id] {
  scroll-margin-top: 80px;
}
.interest-tags {
  display: flex;
  gap: 0.6rem;
  flex-wrap: wrap;
  margin-top: 0.6rem;
}
.interest-tags span {
  background: var(--global-footer-bg-color);
  border: 1px solid var(--global-border-color);
  padding: 0.35rem 0.9rem;
  border-radius: 20px;
  font-size: 0.85rem;
  color: var(--global-text-color);
  line-height: 1.3;
}
.pub-heading-meta {
  font-size: 0.8rem;
  font-weight: normal;
  color: var(--global-text-color-light);
}
.pub-heading-meta a {
  color: var(--global-link-color);
}
.paper-box {
  display: flex;
  gap: 1rem;
  padding: 0.9rem 0;
  border-bottom: 1px solid var(--global-border-color);
  align-items: stretch;
}
.paper-box:last-child { border-bottom: none; }
.paper-box-image {
  flex: 0 0 260px;
  max-width: 260px;
  align-self: stretch;
  position: relative;
  overflow: hidden;
  border: 1px solid var(--global-border-color);
  border-radius: 4px;
  background: var(--global-footer-bg-color);
}
.paper-box-image img {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: contain;
  display: block;
}
.paper-box-text { flex: 1; min-width: 0; }
.paper-box-text p { margin: 0.25rem 0; }
.paper-title {
  font-weight: 600;
  font-size: 0.98rem;
  line-height: 1.4;
  color: var(--global-text-color);
}
.paper-box .paper-authors {
  font-size: 0.8rem !important;
  color: var(--global-text-color-light);
  line-height: 1.5;
}
.paper-authors u {
  color: var(--global-text-color);
  font-weight: 600;
  text-decoration: none;
}
.paper-authors b { color: var(--global-text-color); font-weight: 600; }
.paper-desc {
  font-size: 0.87rem;
  color: var(--global-text-color-light);
  line-height: 1.5;
}
.paper-box .paper-links { font-size: 0.72rem !important; color: var(--global-text-color-light); }
.paper-box .paper-links .pub-text-link {
  color: var(--global-text-color) !important;
  font-size: 0.65rem !important;
  text-decoration: none;
}
.paper-box .paper-links .pub-text-link:hover { text-decoration: underline; }
.paper-box .paper-links .stars-badge { height: 18px; vertical-align: -20%; }
.pub-venue { font-weight: 600; color: var(--global-link-color); }
.paper-links a {
  font-size: 0.8rem;
  padding: 0.1rem 0.5rem;
  background: var(--global-footer-bg-color);
  border: 1px solid var(--global-border-color);
  border-radius: 4px;
  color: var(--global-link-color);
  text-decoration: none;
  margin-left: 0.25rem;
}
.paper-links a:hover {
  background: var(--global-link-color);
  color: #fff;
  text-decoration: none;
}
@media (max-width: 600px) {
  .paper-box { flex-direction: column; }
  .paper-box-image {
    flex: unset;
    width: 100%;
    max-width: 280px;
    aspect-ratio: 16 / 9;
    margin: 0 auto;
  }
}
ul.timeline {
  list-style: none;
  padding-left: 0;
}
ul.timeline li {
  padding: 0.5rem 0;
  border-left: 2px solid var(--global-border-color);
  padding-left: 1rem;
  margin-bottom: 0.4rem;
}
.timeline-meta {
  display: block;
  color: var(--global-text-color-light);
  font-size: 0.88rem;
  margin-top: 0.15rem;
}
</style>
