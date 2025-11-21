---
title: "메모: YOLOX-SAR: High-Precision Object Detection System Based on Visible and Infrared Sensors for SAR Remote Sensing"
excerpt: ""
thumbnail: study_notes/lab-paper/251120_01.jpeg
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251120_01.jpeg">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251120_01.jpeg">
  </a>
  <figcaption>
  Fig.1 YOLOX-SAR: High-Precision Object Detection System Based on Visible and Infrared Sensors for SAR Remote Sensing
  </figcaption>
</figure>

Published in: IEEE Sensors Journal ( Volume: 22, Issue: 17, 01 September 2022) 

Date of Publication: 08 July 2022

# Introduction

SAR(Synthetic Aperture Radar) image에 대한 object detection 개선에 관한 연구이다.

YOLOX 기반으로 adaptive activation function으로 Meta-ACON을 Backbone의 SPP module과 결합해 feature extraction ability를 향상시켰으며, FPN에 Convolutional Block Attention Model (CBAM)을 통합해 dense object scene에서 attention area를 보다 효과적으로 찾는다고 함. 그 외엔 data enhancement, MS-testing을 적용했다고 함.

결과는 YOLOX 기반으로, 이 연구에서 제시하는 기법들을 하나하나 적용해가며 mAP, Precision, Recall, F1 score를 비교하며, 각 객체별로 AP를 YOLOv3, Faster R-CNN, SSD, MFFD, MFFD-DIR과 비교한다.

# Body

## Related Works

본 연구와의 비교보다는, 이 연구에서 도입한 기법들에 관한 설명이 주. Activation functions, dynamic kernel, kernel design을 언급하는 A, B는 attention mechanism에 관한 트렌드, C는 YOLOX에 관한 설명임.

## Method

ACON[10]은 adaptive activation function으로, dynamic nonlinearity, 즉 학습 중 function이 linear하면 neuron을 deactivate한다고 함.

Convolutional Block Attention Module (CBAM)[25]는 attention module로, 쉽게 CNN architecture에 통합될 수 있음. 본 연구에서는 CBAM을 FPN에 결합해 적용함. CBAM은 channel attention module과 Spatial attention module로 이루어져 있어서 본문에서는 설명도 이어진다. 다른 블로그 참조: <a href="https://kmhana.tistory.com/21">https://kmhana.tistory.com/21</a>

C에서는 그렇게 적용한 YOLOX-SAR의 전체적인 framework를 확인한다.

# Conclusion



# Memo



---

# 참고문헌

