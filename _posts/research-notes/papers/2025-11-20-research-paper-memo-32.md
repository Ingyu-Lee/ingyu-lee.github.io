---
title: "메모: Real-Time Vehicle Classification and License Plate Recognition via Deformable Convolution-Based Yolo v8 Network"
excerpt: ""
thumbnail: study_notes/lab-paper/251120_00.jpeg
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251120_00.jpeg">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/251120_00.jpeg">
  </a>
  <figcaption>
  Fig.1 Real-Time Vehicle Classification and License Plate Recognition via Deformable Convolution-Based Yolo v8 Network
  </figcaption>
</figure>

Published in: IEEE Sensors Journal ( Volume: 24, Issue: 23, 01 December 2024) 

Date of Publication: 26 September 2024

# Introduction

차량 번호판 인식에 대해서 deformable convolution과 YOLO v8을 적용한 연구이다. 먼저 vehicle image에 low-light enhancement, superresolution, defogging 등의 preprocessing을 거친 후, YOLO v8에서 vehicle detection 후, 번호판 인식 후 글자 인식을 수행하는 방식이다.

# Body

## Related Works

번호판 인식에 관한 다양한 조사 및 단점 서술.

## Method

Dehazing은 DCP, contrast enhancement는 CLAHE, superresolution은 DL 기반 방법(명시되진 않음)을 사용했다고 함.

차량 인식에는 YOLOv8에 deformable convolution과 squeeze and excitation block을 도입함. YOLOv8의 C2f module에 deformable convolution을 적용해, multiscale objects를 보다 잘 인식하도록 개선함. 하지만 deformable convolution layer는 calculation cost가 높다는 점을 유의해야 함.

Squeeze and excitation block은 저렴한 cost로 characteristic 추출에 용이함.

# Conclusion



# Memo



---

# 참고문헌

