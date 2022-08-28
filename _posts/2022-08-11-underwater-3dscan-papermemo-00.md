---
title: "3-D reconstruction of the underwater acoustic images using the GPS positioning and the image matching technology"
excerpt: "3-D reconstruction of the underwater acoustic images using the GPS positioning and the image matching technology"
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
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/220811_underwater_3drecon_paperreview_00.png">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/220811_underwater_3drecon_paperreview_00.png" alt="">
  </a>
  <figcaption>
  Fig.1 Paper title and author
  </figcaption>
</figure>

# 요약

2002년 10월 OCEANS 컨퍼런스에 수록된 paper로, GPS로 자함 위치를 파악하여 side-scan sonar(SSS)의 소나 이미지를 different viewpoint에서 sub-image로 해저 지형과의 거리를 기반으로 해저 지형을 3D reconstruction 한다.

SSS의 소나 이미지에서 grey zone, 즉 맨 처음 신호가 들어오는 거리 지점이 SSS에서 가장 가까운 지형 간의 거리라고 생각할 수 있다. 이를 이용해 ㄹ 자형 기동을 하여 두 지점에서 측정한 거리로 해저 지형의 높이를 계산한다. 여기서 두 측정 포인트에서 어떻게 같은 지점을 측정하는 지에 대한 문제가 있다. 복잡한 소나 이미지에서 어떤 지점이 실제로 같은 포인트를 측정할까? 같은 포인트를 찾는 것은 lack of image texture, object occlusion, acquisition noise 등 다양한 원인에 의해 어려운 task이고, 이에 대해 두 가지 method, are-based 그리고 feature-based method 가 널리 알려져 있다. 이 논문은 새로운 방법으로, multi-step grey-level projective matching with GPS positioning 이라는 method를 제안한다.

서로 다른 경로에서 소나 이미지가 겹치는 영역에 대해서, 두 측정 지점에서 SSS가 정확히 평행하게 스캔했을 가능성은 적다. 이를 motion estimation을 통해 보정하는 다양한 방법들이 개발되었다. 그런데 소나 이미지의 speckle noise에 의해 data corruption이 일어나기 때문에, 이 논문에서는 grey-level projection을 사용해 noise의 영향을 줄인다.

먼저 grey-level projection에서의 이미지 차이를 활용해 azimuthal direction에서의 correction을 수행한다. 이후 computational burden을 줄이기 위해 feature-point extraction을 수행하고, mutual matching으로 두 이미지에서 같은 지점을 찾아낸다.

이 논문은 실험을 통해 그 방법 중간중간의 데이터 처리 과정을 시각적으로 보였고, 최종적인 3D reconstruction 이미지를 보였다.

- - -
# 참고문헌

Y. Lu and M. Oshima, "3-D reconstruction of the underwater acoustic images using the GPS positioning and the image matching technology," OCEANS '02 MTS/IEEE, 2002, pp. 2273-2278 vol.4, doi: 10.1109/OCEANS.2002.1191984.
