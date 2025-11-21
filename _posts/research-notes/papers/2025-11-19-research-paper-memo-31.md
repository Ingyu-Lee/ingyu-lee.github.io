---
title: "메모: MOA-YOLO: An Accurate, Real-Time, and Lightweight YOLOv10-Based Algorithm for Deep-Sea Fish Detection"
excerpt: ""
thumbnail: study_notes/lab-paper/251119_01.jpeg
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251119_01.jpeg">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251119_01.jpeg">
  </a>
  <figcaption>
  Fig.1 MOA-YOLO: An Accurate, Real-Time, and Lightweight YOLOv10-Based Algorithm for Deep-Sea Fish Detection
  </figcaption>
</figure>

Published in: IEEE Sensors Journal ( Volume: 25, Issue: 13, 01 July 2025) 

Date of Publication: 04 June 2025

# Introduction

AUV 광학 이미지 기반 detection 개선 연구. YOLO v10을 바탕으로, color와 contrast 보정, head 개선, loss function 변경이 있다. 비교 대상은 주로 YOLO 버젼별로 비교하였다. 독특한 점은, 다른 논문들과 달리 연산 시간도 비교한 점이다. 기반이 된 YOLO v10보다 FLOPs가 적은 특징이 있다.

color 및 contrast 보정은 ASNet 기반 알고리즘이다.

Neck과 각각의 detecting head 사이에 MLA를 추가해 효과적인 feature 추출을 한다고 한다.

Detecting head에서는 small target detection을 위한 loss function 교체를 수행하였다.

Backbone 및 neck에서는 일부 모듈을 대체하여 parameter 감소 및 feature extraction 성능을 향상시켜 detection speed와 accuracy 사이의 균형을 달성하였다.

# Body

## Related Works

one-stage 및 two-stage detectors에 관한 개괄.

## Method

ASNet은 "Underwater image enhancement using adaptive standardization and normalization networks" 논문에서 연구된 network.

MLA[38]는 group query attention과 multiple attention heads를 통해 feature를 추출해 object와 주변 환경을 효과적으로 구분하는 모듈이다.

NWD loss function[41]은 작은 물체의 위치 편차에 대한 IoU의 민감도를 줄일 수 있으나, detection accuracy가 낮을 수 있다. 때문에 IOU, CIOU, NWD loss function을 weight를 부여하여 합친 loss function을 제안했다.

기존 convolution kernel은 param 수가 너무 많아 real-time performance에 영향을 주어, 이 연구에서는 AKConv[42]로 대체하였음. AKConv는 adaptively sampling size 및 shape를 조정할 수 있어 params의 수를 줄일 수 있음.

# Conclusion



# Memo



---

# 참고문헌

