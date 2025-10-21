---
title: "메모: Infrared Multiobject Contrast Enhancement and Detection Based on Layered Visual Transformer Network for Autonomous Driving"
excerpt: ""
thumbnail: study_notes/lab-paper/251021_01.jpeg
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251021_01.jpeg">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251021_01.jpeg">
  </a>
  <figcaption>
  Fig.1 Infrared Multiobject Contrast Enhancement and Detection Based on Layered Visual Transformer Network for Autonomous Driving
  </figcaption>
</figure>

Published in: IEEE Sensors Journal ( Volume: 24, Issue: 22, 15 November 2024) 

Date of Publication: 30 September 2024

# Introduction

Infrared vision에 대해 visual transformer network 제시, 3가지 개선점을 제안함: backbone, encoder, 그리고 decoder&detection head. Backbone network인 layered visual transformer network(LVTN)은 IR데이터의 feature 추출함. Encoder는 기존의 attention mechanism을 대체하고 adaptive-feedback attention(AFA)를 도입해 객체 feauture에 집중하고 contrast를 향상시킴. Decoder and detection head는 training weight를 조정하고 multiscale 및 dense object detection 문제를 해결하는 fine-grained matching loss function(FMLF)을 도입함.

공개 데이터셋으로 보이는 FLIR-ADAS 및 KAIST dataset을 활용, SOTA와 비교해 우수함을 확인함.

# Body

## Related Works


## Method


# Conclusion


# Memo



---

# 참고문헌

