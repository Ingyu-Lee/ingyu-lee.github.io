---
title: "메모: MINIAOD: Lightweight Aerial Image Object Detection"
excerpt: ""
thumbnail: study_notes/lab-paper/251119_00.jpeg
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251119_00.jpeg">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251119_00.jpeg">
  </a>
  <figcaption>
  Fig.1 MINIAOD: Lightweight Aerial Image Object Detection
  </figcaption>
</figure>

Published in: IEEE Sensors Journal ( Volume: 25, Issue: 5, 01 March 2025) 

Date of Publication: 23 January 2025

# Introduction

UAV 데이터를 위한 인식 network architecture 개선 논문. Backbone 개선, feature enhancement 관련 module 제안, attention mechanism 관련 모듈 제안으로 작은 타깃에 대한 인식률 향상이 있다. 검증은 공개 dataset 기반 R-CNN, YOLO 등과 비교하여 개선됨을 보임.

# Body

## Related Works

## Method

제안하는 전체 network architecture는 그림2와 같음. Backbone은 Ghost module, 그 다음은 GSConv, GSC3ECA, ECA module 셋으로 feature enhancement network를 구성하며, 마지막으로는 rotation detection head가 있음.

28번 reference인 C3 module 기반으로 그림 4처럼 변경하여 backbone network를 구성함.

Ghostnet은 20년도 CVPR 논문으로, 훨씬 비용이 저렴한 convolution 대체 연산임. 본문에서는 feature extraction이 아닌 feature enhancement에 Ghostnet이 쓰일 경우 부정적 영향 있을 수 있음을 확인함(deeper layer에선 중복된 feature가 적다고 함). 때문에 GSConv module을 사용[56].

C3, CBL, ECA를 혼용하여 GSC3ECA라는 모듈을 설계함.

loss function은 multitask loss function을 사용했는데, 이건 aerial data의 특수성으로 기인한다고 함. Multitask loss function의 특징을 한번 확인하면 좋을듯.

# Conclusion



# Memo



---

# 참고문헌

