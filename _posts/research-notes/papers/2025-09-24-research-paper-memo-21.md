---
title: "메모: A Novel Day-to-Night Obstacle Detection Method for Excavators Based on Image Enhancement and Multisensor Fusion"
excerpt: ""
thumbnail: study_notes/lab-paper/250924_00.jpeg
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/250924_00.jpeg">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/250924_00.jpeg">
  </a>
  <figcaption>
  Fig.1 A Novel Day-to-Night Obstacle Detection Method for Excavators Based on Image Enhancement and Multisensor Fusion
  </figcaption>
</figure>

Published in: IEEE Sensors Journal ( Volume: 23, Issue: 10, 15 May 2023)

Date of Publication: 14 March 2023

# Introduction

Excavator에 3가지 센서-infrared camera, RGB camera, and LiDAR를 달아서 장애물 인식 연구. Infrared에 DoG(difference of Gaussian) 적용 후 YOLOv5로 detection, 그 이후 센서퓨전 시도. 어두울 때도 인식 잘 되는 점을 강조.

# Body

Related works에서 제시된 주요 기여:
주요 기여 1. DoG 기반 image enhancement로 image의 contrast와 texture information을 증가
주요 기여 2. YOLOv5 기반 multicategory obj. 를 더 잘 인식하기 위한 NN 모델 제시
주요 기여 3. Obj. detection 및 localization을 위한 카메라-LiDAR fusion strategy

그림 2 참조; 연구의 전체 메커니즘 및 주요 기여를 그림 하나로 표현

Methodology에서 상세 설명:
주요 기여 1. DoG는 그냥 수식만 좀 써놓고, 왜 이게 feature에 도움이 되는지는 다소 두루뭉술한 서술. 그냥 infrared vision의 노이즈가 가우시안으로 잘지워진다 정도만 씀.
주요 기여 2. YOLOv5 기반으로 뒤에 detection head 외에도 segmentation head도 붙임.
주요 기여 3. 카메라-라이다 퓨전 및 장애물 인식 및 위치 계산

# Conclusion

실험으로 검증. 주된 그래프와 숫자는 대부분 enhanced image와 raw image의 accuracy 비교.

# Memo



---

# 참고문헌

M. Zou, J. Yu, Y. Lv, B. Lu, W. Chi and L. Sun, "A Novel Day-to-Night Obstacle Detection Method for Excavators Based on Image Enhancement and Multisensor Fusion," in IEEE Sensors Journal, vol. 23, no. 10, pp. 10825-10835, 15 May15, 2023, doi: 10.1109/JSEN.2023.3254588.