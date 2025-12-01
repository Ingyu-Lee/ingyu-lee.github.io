---
title: "메모: Underwater Image Enhancement Using Deep Transfer Learning Based on a Color Restoration Model"
excerpt: ""
thumbnail: study_notes/lab-paper/251201_00.png
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251201_00.png">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251201_00.png">
  </a>
  <figcaption>
  Fig.1 Underwater Image Enhancement Using Deep Transfer Learning Based on a Color Restoration Model
  </figcaption>
</figure>

Published in: IEEE Journal of Oceanic Engineering ( Volume: 48, Issue: 2, April 2023) 

Date of Publication: 15 March 2023

# Introduction

Underwater vision data에서의 한계를 low visibility, blur, 그리고 color distortion으로 제시하고, 그 해결법을 transfer learning 기반 underwater image enhancement framework를 제시함. Domain transformation module, image enhancement module로 구성되어, color correction과 image enhancement를, 기존의 in-air image dehazing을 underwater image에 맞추어 변형해 적용함.

In-air 기법을 underwater data에 적용하기 위해 physical model을 반영하였으며, color restoration 적용, 그리고 color deviation 제거를 위해 coarse-grained similarity calculation을 적용함.

## Related Works

이 연구에서 주로 차용한 세 가지: underwater image degratation model, underwater image color restoration, deep transfer learning 세 가지 내용의 기존 연구와 underwater image에 그대로 적용할 때의 한계를 서술함.

A. Underwater Image Degradation Model

상세한 논문 레퍼런스 및 이론은 생략, 여튼 빛의 원리인 luminance 및 2가지 scattering을 수식으로 작성. 하지만 underwater에서는 빛의 주파수에 따라 absorption이 다르다는 점을 강조해, 한계가 있음을 강조함.

B. Underwater Image Color Restoration Using Haze-Lines

Haze-line 기반 color restoration 관련 논문 및 이론 열거. 하지만 마찬가지로 주파수에 따른 attenuation의 한계가 있으며, 이미 이에 대해 연구한 논문 레퍼 달고, 이 연구에선 어떻게 적용할지 언급.

C. Deep Transfer Learning

Transfer learning 및 domain adaptation 관련 설명 및 기존 연구 레퍼. 또한 기존 underwater image dataset은 synthetic dataset이기 때문에 실제 데이터와의 차이가 나는 한계 언급.

이러한 3가지 기존 연구들을 고려해서 본 연구에서는 두 가지 domain adaptation strategy를 도입.

1. Reconstruction-based method를 사용해 underwater image로부터 in-air 스타일의 image 생성.
2. Discrepancy-based method를 사용해 변환한 이미지를 image enhancement network의 training에 통합, the network를 fine-tuning해 underwater image에 적합하도록 변경함.

즉, 제안하는 모델은 in-air image와 underwater image를 같이 사용해 학습하며, underwater ground-truth image를 사용하지 않음.

# Body

크게 transfer learning framework, cross-domain transfer, 그리고 loss function 3 가지 subsection으로 구성됨.

A. Transfer Learning Framework

이 프레임워크는 2개의 domain adaptation module, reconstruction method에 기반한 모듈과 discrepancy-based method를 사용한 모듈로 구성됨. 각각, underwater image에서 in-air image로 변환, 그 반대 변환을 수행하는 모듈 하나와, 그 과정을 거친 이후의 underwater img를 enhancement하는 모듈로 구성됨.

B. Proposed Enhancement Method

그 각각의 모듈에 대해 상세 서술하는 subsection. 

## Method


# Conclusion



# Memo


---

# 참고문헌

