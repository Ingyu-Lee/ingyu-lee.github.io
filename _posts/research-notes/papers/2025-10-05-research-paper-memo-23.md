---
title: "메모: "
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
  Fig.1 
  </figcaption>
</figure>

Published in: 

Date of Publication: 

# Introduction

테라헤르츠THz 이미지의 semantic segmentation을 위해 낮은 contrast를 개선하기 위한 YOLO 변형인 IYOLO를 제시한 논문.

Backbone feature extraction 강화를 위한 CST 모듈, feature upsampling 최적화를 위한 EUB, segmentation head에서의 model params의 최적화를 위한 SCLayer 세 가지 개선안을 제시한다.

퍼블릭 데이터셋을 바탕으로 검증했으며, 다른 SOTA methods와 비교하여 더 나은 결과를 확인. 

# Body

EUB는 channel operation, encoder-decoder structure, feature enhancement 세 가지를 integrates하여 image details와 features를 보존함.

SCLayer는 model params와 complexity를 감소.

## Related Works

3 가지 분야, THz detection, improved convolution structure, segmentation based on transformer 에서 각 논문을 확인 및 분석.

THz는 기존 연구의 한계 확인.

Improved convolution structure에선 이 convolution structure의 효과를 확인하고 이 논문에서 제시하는 IYOLO에 해당 스트럭쳐를 적용.

Segmentation based on transformer에서는 해당 논문들을 기반으로 CST모듈 설계.

## Method

제시하는 IYOLO의 overall structure는 그림 1 참조. U-net처럼 incoding-decoding 과정에서 특정 레이어를 같은 크기 다음 레이어로 가져오는 것도 보임.

CST, EUB로 복잡해신 과정을 SCLayer로 단순화시킨다고 함.

CST structure는 그림 2, EUB는 그림 3, SCLayer는 그림 4 참조. 본문에 좀 더 디테일한 수식 작성됨.

# Conclusion


# Memo



---

# 참고문헌

