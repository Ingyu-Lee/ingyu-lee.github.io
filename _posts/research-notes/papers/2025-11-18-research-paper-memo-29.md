---
title: "메모: MDFANet: Multidomain Feature Alignment Surface Defect Detection for Aircraft Engine Turbine Blades"
excerpt: ""
thumbnail: study_notes/lab-paper/251117_01.jpeg
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251117_01.jpeg">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251117_01.jpeg">
  </a>
  <figcaption>
  Fig.1 MDFANet: Multidomain Feature Alignment Surface Defect Detection for Aircraft Engine Turbine Blades
  </figcaption>
</figure>

Published in: IEEE Sensors Journal ( Volume: 25, Issue: 13, 01 July 2025) 

Date of Publication: 12 May 2025

# Introduction

항공 엔진의 defect detection을 위한 인식 network architecture 개선 논문. dataset 구축, backbone layer에 신규 module 도입, YOLO v7 기반 신규 loss function 도입이 주요 내용으로 보인다.

Multiscale feature fusion(MFF) module은 shallow와 deep 두 region에서 feature fusion을 한다고 함.

Backbone에서의 module은 image-level domain adaptation (ILDA) module로, adversarial training을 수행함. 그리고 neck에서는 micro defect와 noise 구분을 위한 head integration을 수행함.

다른 방법들(해당 논문 레퍼런스 40-45번)과의 비교를 통해 입증함.

# Body

## Related Works

첫번째로는 object detection에 대해, two-stage detector와 one-stage detector를 개괄함.

두번째로는 항공 엔진 블레이드의 defect detection의 기존 연구를 개괄하며, 다른 YOLO 기반 연구도 일부 소개함.

세번째로는 unsupervised domain adaptation 관련 연구를 정리함.

## Method

제시하는 MDFANet process는 크게 네 단계, 즉 input, backbone, domain adaptation module, head임.

1. 학습 과정에서 labeled와 unlabeled를 병렬로 입력해, supervised 와 unsupervised feature를 동시 학습할 수 있게 만든다고 함.

2. backbone에서 앞서 intro에서 언급한 MFF와 ILDA를 수행해, cross-scale feature interaction과 adversarial training을 수행함.

이후 각 모듈의 상세 설명은 생략

# Conclusion



# Memo



---

# 참고문헌

