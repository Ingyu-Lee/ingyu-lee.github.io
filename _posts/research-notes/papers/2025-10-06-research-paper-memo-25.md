---
title: "메모: DIONet: An Illumination-Adaptive Network for Real-Time Road Obstacles Detection Under Low-Light Scenarios"
excerpt: ""
thumbnail: study_notes/lab-paper/251006_00.jpeg
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251006_00.jpeg">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251006_00.jpeg">
  </a>
  <figcaption>
  Fig.1 DIONet: An Illumination-Adaptive Network for Real-Time Road Obstacles Detection Under Low-Light Scenarios
  </figcaption>
</figure>

Published in: IEEE Sensors Journal ( Volume: 25, Issue: 17, 01 September 2025)

Date of Publication: 01 August 2025

# Introduction

이 논문은 어두운 환경에서의 road obstacle detection을 위해 DIONet(Dark Is OK Network)을 제안하는 논문이다.

총 4가지 개선 사항으로, OIT, FADC, AIFI, Inner-IoU를 제안한다.

OIT(Obstacle Illumination Transformer) 모듈은 multiscale transformer architecture를 활용해 어두운 이미지에서 illumination과 reflection components를 분리하여 detailed feature를 복구한다.

FADC(Frequency-Adaptive Dilated Convolution) 모듈은 다양한 크기의 물체 인식 및 어두운 이미지의 boundary blur를 제거함.

AIFI(Attention-based Intrascale Feature Interaction) 모듈은 작은 물체 인식률 향상을 위해 feature fusion을 최적화함. 이 최적화는 attention mechanism을 통해 이뤄짐.

Inner-IoU는 localization strategy를 변경해 작은 물체에 대한 인식률을 높임.

결과는 SOTA들과 비교함. YOLOv11, YOLOv12, LED-YOLO, EnlightenGAN-YOLO, PE-YOLO와 비교함. 다만 비교한 데이터셋은 독자적으로 만든 것이라고 함.

# Body

## Related Works


## Method


# Conclusion


# Memo



---

# 참고문헌

