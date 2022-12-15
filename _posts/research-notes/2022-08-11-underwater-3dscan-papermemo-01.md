---
title: "Low cost stereo system for imaging and 3D reconstruction of underwater organisms"
excerpt: "Low cost stereo system for imaging and 3D reconstruction of underwater organisms"
thumbnail: 999999_category_research_paper_memo_00.jpg
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
toc: true
toc_sticky: true
categories:
  - Studies
tags:
  - Paper Reviews
sidebar:
  title: "Underwater 3D Scan<br>Literature Study"
  nav: aaa
---

<figure style="width: 100%" class="align-center">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/220811_underwater_3drecon_paperreview_01.png">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/220811_underwater_3drecon_paperreview_01.png" alt="">
  </a>
  <figcaption>
  Fig.1 Paper title and author
  </figcaption>
</figure>

# 요약

이 논문은 2015 년 5 월 OCEANS 학회에 실린 paper로, Raspberry Pi 및 camera module 각각 2 개를 장착한 low-cost robot을 사용해 stereo-vision으로 수중 생물의 형태를 3D reconstruction을 수행한 논문이다.

# Note

짧은 내용이지만, 아직 이 field에 익숙하지 않은 나는 주로 주목할 것이 두 가지 있다.

* Img acquisition - preprocessing - rectification - DSI computing - point cloud extraction - 3D model reconstruction 으로 이어지는 stereo vision을 활용한 3D reconstruction의 수행 과정

* <a href = "https://kr.mathworks.com/help/visionhdl/ug/stereoscopic-disparity.html">Stereo Disparity Using Semi-Global Block Matching</a> stereo vision에서 disparity mapping 으로 사용될 수 있는 알고리즘

- - -
# 참고문헌

L. Mazzei, L. Corgnati, S. Marini, E. Ottaviani and B. Isoppo, "Low cost stereo system for imaging and 3D reconstruction of underwater organisms," OCEANS 2015 - Genova, 2015, pp. 1-4, doi: 10.1109/OCEANS-Genova.2015.7271554.
