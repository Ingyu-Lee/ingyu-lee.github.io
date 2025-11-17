---
title: "메모: IRMSD-YOLO: Multiscale Dilated Network With Inverted Residuals for Infrared Small Target Detection"
excerpt: ""
thumbnail: study_notes/lab-paper/251117_00.jpeg
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251117_00.jpeg">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251117_00.jpeg">
  </a>
  <figcaption>
  Fig.1 IRMSD-YOLO: Multiscale Dilated Network With Inverted Residuals for Infrared Small Target Detection
  </figcaption>
</figure>

Published in: IEEE Sensors Journal ( Volume: 25, Issue: 9, 01 May 2025) 

Date of Publication: 07 March 2025

# Introduction

Infrared vision에 대해 작은 target을 인식하기 위해 YOLO를 개선한 연구.

feature fusion 단계에서 inverted residual feature extraction (IRFE) module을 제시해, 서로 다른 frequency에서 feature fusion하였다고 함.

또한 복잡한 background에서 local contrast methods의 한계를 극복하기 위해 inverted residual multiscale dilated (IRMSD) attention module을 제시해 feature transformation과 multiscale dilated attention (MSDA)를 활용하여 background noise의 영향을 줄이고 receptive field를 확장했다고 함.

연구 목적인 infrared small targets 관련된 dataset이 없어서 자체 구축했다고 함(공유는 X). 그래도 공용 데이터셋으로 검증하긴 함.

# Body

## Related Works

1. Traditional methods에서는 threshold-based segmentation, background removal 등 DL 이전의 기법을 소개하고 한계를 서술함.
2. DL분야에서는 two-stage, one-stage, ... 를 다 제시하고, results에서도 다른 다양한 methods와 성능 비교함.

## Method

Head에선 별다른 특별한건 없어보이고, backbone에서의 IRFE module과 neck에서의 IRMSD로 이루어진 network architecture가 주된 기여로 보인다.

shallow layer에서는 noise가 많고 deeper layer일수록 작은 target을 인식하기 어려우므로, backbone에서 middle-layer를 neck에 더 많이 연결시킨 것으로 보임.

# Conclusion


# Memo

다른 중국 DL network structure 연구와 유사한 구조인 것으로 보임.

---

# 참고문헌

