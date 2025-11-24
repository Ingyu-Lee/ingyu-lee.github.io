---
title: "메모: An Improved YOLOv8-Based Shallow Sea Creatures Object Detection Method"
excerpt: ""
thumbnail: study_notes/lab-paper/251124_00.jpeg
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251124_00.jpeg">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251124_00.jpeg">
  </a>
  <figcaption>
  Fig.1 An Improved YOLOv8-Based Shallow Sea Creatures Object Detection Method
  </figcaption>
</figure>

Published in: IEEE Journal of Oceanic Engineering ( Volume: 50, Issue: 2, April 2025) 

Date of Publication: 21 March 2025

# Introduction

Shallow sea 환경에서 motion blur나 객체가 군집을 이뤄 인식하기 어려운 상황을 바탕으로 YOLOv8을 개선한 연구.

receptive-field coordinate attention (RFCA)를 C2f 모듈에 통합하여 low-contrast하고 blurry한 image에서 feature extraction 및 feature fusion 능력을 향상시키며, DCNv2 를 DCNv3로 변경하여 clustered objects의 탐지를 향상시켰음.

검증은 detecting underwater objects, underwater robot professional competition 2020, underwater target detection and classification 2020 datasets 기반으로 다른 YOLO 버젼들과 mAP를 비교하였음.

# Body

## Related Works

수중 물체 탐지에 있어 one-stage, two-stage 각각 서술 후 two-stage의 문제들, efficiency와 실시간성 부족 서술 후에, YOLO로 대표되는 one-stage 시리즈의 small object detection의 어려움 및 low-quality image에서의 detection의 어려움에 관해 서술

YOLO 시리즈의 발전과 우수성에 대해 서술(YOLO기반으로 한 이유)

small object detection을 위한 attention mechanism 관련 자료 조사 서술

## Method

A. Structure Diagram of Proposed Method

Backbone에서는 C2f 모듈을 그대로 유지함. C2f_RFCA는 backbone에서는 결과에 유의미한 차이는 없지만 FLOPs만 늘어남.

Neck에서는 모든 C2f를 C2f_RFCA로 대체함.

Head에서는 decoupled head를 DyHead3로 대체함.

B. C2f_RFCA: RFCA-Enhanced C2f Module for Optimized Feature Learning

기존의 YOLOv8의 구성 요소를 분석함. C2f 모듈의 설계와 특징을 확인하고, spatial attention mechanism, 즉 RFA와 RFCA 모듈을 적용하는 것에 대해 서술함. 특히 blurred image에 대해서는 grouped convolution이 object boundary 구분에 도움이 된다고 함.

C. Dynamic Head With DCNv3

Dynamic head [34]를 DCNv3 [35]와 결합하여 DyHead3을 제안함. 본 연구에서는 연산 방식을 고려하여 computational cost를 줄여 연산하는 방식을 고안한다. image의 3 dimension, 즉 layer, spatial dimension, channel 을 분리하여 연산함으로써 연산 코스트를 줄인다. 각각의 dimension에 대한 수식은 본문에 있다.

# Conclusion



# Memo



---

# 참고문헌

