---
title: "메모: Boundary Dynamic Perception Detection Network for Low-Light Railway Environment"
excerpt: ""
thumbnail: study_notes/lab-paper/250924_01.jpeg
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/250924_01.jpeg">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/250924_01.jpeg">
  </a>
  <figcaption>
  Fig.1 Boundary Dynamic Perception Detection Network for Low-Light Railway Environment
  </figcaption>
</figure>

Published in: IEEE Sensors Journal ( Volume: 25, Issue: 8, 15 April 2025)

Date of Publication: 04 March 2025

# Introduction

Image enhancement보다는 새로운 network structure가 주안점인 논문. Parallel spatial enhancement convolutional two-branch network structure라는 긴 이름의 스트럭쳐이다. 이후 boundary dynamic representation module을 제안하여 fused feature information을 활용한다.

# Body

Literature review에서 이 논문의 주 목표와 관련된 기존 연구 내용을 분야별로 정리하고, research gap analysis를 통해 기존 연구의 한계와 이 연구의 의의를 설명하는 부분이 흥미롭다. 그래서 이 논문의 주된 기여는 다음과 같다:
1\. Spatial feature enhancement module을 제안하여 double-branch network로 넓은 영역과 작은 영역에서 전역/로컬 information을 획득한다.
2\. Probability density distribution model을 활용해 탐지된 객체의 위치를 정해진 포지션으로 잡지 않고 확률분포로 계산하여 regression accuracy를 높인다.

Methodology에선 세 가지 단계를 거친다.
1\. Light correction network를 통해 image enhancement를 수행
고전적인 enhancement가 아닌 작은 NN를 통해 수행했는데, 그 과정의 증명이 다소 약하다.
2\. Dual-backbone feature extraction module을 통해 

# Conclusion


# Memo



---

# 참고문헌

J. Wang, Z. Xie, Y. Qin, X. Zhang, Z. Wang and L. Wang, "Boundary Dynamic Perception Detection Network for Low-Light Railway Environment," in IEEE Sensors Journal, vol. 25, no. 8, pp. 14064-14079, 15 April15, 2025, doi: 10.1109/JSEN.2025.3543860.