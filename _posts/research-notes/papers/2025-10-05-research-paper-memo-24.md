---
title: "메모: DFIF: Dual-Modality Fusion Detection Under Low-Light Conditions"
excerpt: ""
thumbnail: study_notes/lab-paper/251005_01.jpeg
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251005_01.jpeg">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251005_01.jpeg">
  </a>
  <figcaption>
  Fig.1 DFIF: Dual-Modality Fusion Detection Under Low-Light Conditions
  </figcaption>
</figure>

Published in: IEEE Sensors Journal ( Volume: 25, Issue: 16, 15 August 2025)

Date of Publication: 10 July 2025

# Introduction

Low-light RGB 이미지와 적외선 영상을 기반으로 dual-modality fusion detection 및 four-head adaptively spatial feature fusion network를 제안하는 논문.

Dual-stream feature extraction 과정에서 DMAFF 모듈을 제안하고, 공개된 두 가지 RGBI 데이터셋에 대해 검증.

# Body

## Related Works

Dual-modality의 세 가지 유형 제시 후 각 유형의 특성 언급 후 선택. 해당 유형은 다른 논문에서도 넓은 영역-디테일한 영역으로 사용된 바 있음. 고려해 볼 수 있음.

다른 low-light image detection 논문 기반으로 plug-and-play image-enhancement network를 제시한다고 함(막상 plug-and-play network는 본문에 없음). End-to-end detector를 설계. 해당 netowork 도식은 그림 3에 제시됨.

## Method

세 가지 개선사항, LLIE network, DMAFF module, FASFF network를 제시함.

LLIE: end-to-end training process로 아무튼 target detection이 개선되는 image feature를 improve한다고 함. 나중에 천천히 end-to-end learning 을 확인해보자. 예: https://wikidocs.net/204321

DMAFF: 그림2에 layer 중간중간 DMAFF를 적용하는 것을 확인할 수 있거, 그림 4 에 그 구조를 확인할 수 있음. RGB와 infrared image 에서 feature extraction 중간중간에 complementary feature를 교환한다고 함.

FASFF: 그림2-그림5에서 볼 수 있듯, layer 중간중간에서 4 개의 feature map을 추출하여 weight를 적용해 합침.

최종적으로 DFIF의 loss function을 정의함. 각각의 term은 bounding box loss func, categorization loss func, distribution focus loss func로 이루어져 있고, 각각 정해진 weight coeff. 를 곱해서 더함.

# Conclusion


# Memo



---

# 참고문헌

