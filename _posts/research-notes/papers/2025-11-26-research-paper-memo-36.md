---
title: "메모: A Reinforcement Learning Paradigm of Configuring Visual Enhancement for Object Detection in Underwater Scenes"
excerpt: ""
thumbnail: study_notes/lab-paper/251126_00.jpeg
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251126_00.jpeg">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251126_00.jpeg">
  </a>
  <figcaption>
  Fig.1 A Reinforcement Learning Paradigm of Configuring Visual Enhancement for Object Detection in Underwater Scenes
  </figcaption>
</figure>

Published in: IEEE Journal of Oceanic Engineering ( Volume: 48, Issue: 2, April 2023) 

Date of Publication: 02 March 2023

# Introduction

Underwater object detection을 위한 reinforcement learning에 관한 논문. 기존의 visual enhancement에 관한 회의적 의견이 있다.

이 논문은 아래와 같은 3 가지의 기여를 주장한다.

1. Paradigm: 사람이 보기에 시각적으로 더 낫다고 여겨지는 image enhancement가 아닌, obj. detection 성능 향상을 위한 image enhancement algorithm을 제안함.

2. Implementation: backbone과 neck에서 feature extraction 후 feature를 state로, visual enhancement algorithms를 action으로, detection score 증가분을 reward로, dueling double deep Q network (DDDQN)를 reinforcement learning model로 사용해 learning을 수행함.

3. Baseline: 본 연구에서 제안하는 강화학습을 공개함.

## Related Works

왠진 모르겠지만 related works를 별도의 섹션으로 두지 않고, intro에서 subsection을 여럿 두어 설명했다.

Underwater image에 CLAHE, Water-Net 적용 후 YOLOv5s를 적용해, image enhancement가 항상 좋은 결과를 보이지는 않는다는 점 확인. CLAHE의 경우 긍정적이었지만, Water-Net의 경우 detection 결과가 좋지 않았음.

*개인적인 의견으로는, Water-Net의 경우 색상이 크게 변해 color channel에서 학습된 데이터와 크게 차이가 나서 그런 게 아닐까 생각이 듬. Color channel을 사용할 경우 바로 사용하기보다는, architecture의 변경이 필요하단 생각이 든다.

[57]논문을 언급하며 image enhancement를 적용할 경우, 학습도 다시 enhanced image로 적용해야 된다는 점을 언급.

# Body



## Method


# Conclusion



# Memo


---

# 참고문헌

