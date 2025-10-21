---
title: "메모: Dual-Branch Multiscale Optimization Network for Enhancing Low-Light Images in Rail Transit Obstacle Detection and Segmentation"
excerpt: ""
thumbnail: study_notes/lab-paper/251021_00.jpeg
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251021_00.jpeg">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251021_00.jpeg">
  </a>
  <figcaption>
  Fig.1 Dual-Branch Multiscale Optimization Network for Enhancing Low-Light Images in Rail Transit Obstacle Detection and Segmentation
  </figcaption>
</figure>

Published in: IEEE Sensors Journal ( Volume: 25, Issue: 3, 01 February 2025)

Date of Publication: 11 December 2024

# Introduction

이 논문은 어두운 환경에서의 road obstacle detection을 위해 dual-branch multiscale optimization (DBMO) network를 제시하는 논문.

DBMO는 global branch와 detailed branch로 구성됨.

Global branch는 multiscale network를 활용해 고해상도 입력 데이터를 기반으로 다양한 해상도에서 추출된 feature를 통합해 전반적인 feature를 추출함.

Detailed branch는 wavelet transform을 이용해 영상을 주파수 대역으로 분해, low-freq 성분에서는 명도와 대비를, high-freq 성분에서는 테두리 정보를 강조해 denoising 및 디테일을 향상시킴.

두 branch의 출력은 adaptive weighting과 feature fusion을 통해 합쳐짐.

각각의 branch에서의 상세한 세팅이나 레이어 등은 본문 사진 참조.

공개된 데이터셋을 바탕으로 YOLOv8과 Deeplab과 비교함.

# Body

## Related Works


## Method


# Conclusion


# Memo



---

# 참고문헌

