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

2\. Dual-backbone feature extraction module을 통해 main backbone과 auxiliary backbone을 나눔. Main은 high-level feature를 추출해 전반적인 정보를 확인하고, aux는 low-level feature를 추출해 상세한 정보를 확인한다. Main은 여러 장의 convolutional layer, pooling layer, and activation function으로 구성되며, aux는 shallow convolution layers와 pooling operation으로 구성된다. 그림 2에서 볼 수 있다. 또, 단순히 convolution layer만이 아닌 CSP layer를 활용함. CBLinear layer는 convolution, batch normalization, linear mapping을 합친 layer이다. 이를 통해 적은 연산량으로 feature extraction을 향상시킬 수 있다.

3\. Distributed Focus Loss Head: 어두운 환경에서의 데이터를 보정하다보면 noise도 같이 강조되거나 color distortion 등의 문제가 생긴다. 때문에 본 연구에서는 DFLHead라는 detection head를 제시한다. 본문의 사진5a를 참조하자. 세 파트로 구성되어 있다. Distribution Focal Loss, Feature Reassembling Module, 그리고 PCRC Module이다. 

DFL은 <a href="https://pajamacoder.tistory.com/74">이 블로그</a>내용을 참조하자면, bbox의 width와 height를 확률 분포로 표현하는 방식인 듯 하다.

Feature reassembling module은 서로 다른 scale의 feature를 합치는 모듈로, convolution, upsample, downsample, softmax를 활용해 features를 합친다.

PCRC module은 본문의 사진5b의 구조로, YOLOv9과 비교해 max-pooling layer를 통해 feature를 더 잘 유지하며 highlighting을 한다.

# Conclusion

3 가지 개선 사항에 대해 각각 적용한 결과와 전체를 적용한 결과를 비교해 더 좋은 결과가 나오는 것을 확인함. 평가 항목은 precision rate P, recall rate R, mAP0.5, mAP0.5:0.95 4가지 평가 항목을 사용했다. 연산 시간에 대해선 FLOPs를 비교하였다. FLOPs는 수식 20과 21을 전체 network에 대해 계산하였다.

# Memo

image enhancement 외에도 backbone과 head 개선을 통해 인식률 개선을 이룬 연구이다. Dual-backbone을 사용했는데 FLOPs가 비슷한건 신기하다.

---

# 참고문헌

J. Wang, Z. Xie, Y. Qin, X. Zhang, Z. Wang and L. Wang, "Boundary Dynamic Perception Detection Network for Low-Light Railway Environment," in IEEE Sensors Journal, vol. 25, no. 8, pp. 14064-14079, 15 April15, 2025, doi: 10.1109/JSEN.2025.3543860.