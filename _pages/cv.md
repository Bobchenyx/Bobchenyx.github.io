---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
published: false
redirect_from:
  - /resume
---

{% include base_path %}

Education
======
* M.S. in Electrical and Computer Engineering, Northeastern University, Boston, MA, 2023
* B.E. in Electrical Engineering, Beijing University of Technology, Beijing, China, 2021

Work Experience
======
* May 2024 - Present: Machine Learning Engineer
  * AIbao LLC & EmbodyX
  * Prune and quantize DeepSeek V3 model with MoE Pruning algorithm and Llamacpp. Deploy MoE LLM on AMD Windows platform with Vulkan and HIP/ROCm backend.
  * Develop real-time chatting system integrating LLMs and TTS, enabling seamless human-computer interaction.
  * Deploy Digital Avatar Projects with CoreML and TensorRT, accelerate inference for real-time performance.
  * Develop trajectory prediction assistant with transformer-based models for license learning exams.
  * Video data filtering with face centering and scene detection, audio filtering with multi expert mean score.

* January 2023 - August 2023: Computer Vision Engineering Co-op
  * Cognex Corporation, Natick, MA
  * Developed a .NET wrapper layer to port an Edge Learning Tool between two versions of VisionPro software.
  * Feature enhancement and bug fixes for VisionPro APIs in C++ and QuickBuild Edit Control UI in C#.
  * Utilized Doxygen and SandCastle in .NET programs to generate HTML documentation and CHM files.
  * Expanded testing coverage in C++ and C# as part of the CI Infrastructure.

Technical Skills
======
* Programming Languages: Python, C/C++, C#/.NET Core, SQL
* Tools & Frameworks: Linux Server, PyTorch, Git, llamacpp, KTransformers, TensorRT, CoreML
* Models: DeepSeek V2/V3, Qwen 2/2.5, LLaMA 2, ViT, ViM

Publications
======
  <ul>{% for post in site.publications reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>

<!-- Talks
======
  <ul>{% for post in site.talks reversed %}
    {% include archive-single-talk-cv.html  %}
  {% endfor %}</ul> -->

<!-- Teaching
======
  <ul>{% for post in site.teaching reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul> -->
