---
title: "Multiresolution 3-D Reconstruction From Side-Scan Sonar Images"
excerpt: "Multiresolution 3-D Reconstruction From Side-Scan Sonar Images"
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
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/220812_underwater_3drecon_paperreview_03.png">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/220812_underwater_3drecon_paperreview_03.png" alt="">
  </a>
  <figcaption>
  Fig.1 Paper title and author
  </figcaption>
</figure>

# 요약

이 논문은 2007 년 1 월 IEEE Transactions on Image Processing에 실린 paper로, side-scan sonar(SSS)의 소나 이미지로부터 seabed elevation estimation을 수행하는 새로운 방법을 제시한 논문이다. Sonar scattering model에서 Lambertian model을 사용, multiresolution optimization 과정을 통해 sonar image에서 seabed feature를 추출하였다.

# Note

* Multi-beam sonar system에 비해 SSS가 comparably cheap

* 마찬가지로 아직은 SSS가 SAS보단 economically 유리함

* Lambertian model은 scattering에서 intensity 계산하는 모델(ref 2-4 참고)

- - -
# 참고문헌

E. Coiras, Y. Petillot and D. M. Lane, "Multiresolution 3-D Reconstruction From Side-Scan Sonar Images," in IEEE Transactions on Image Processing, vol. 16, no. 2, pp. 382-390, Feb. 2007, doi: 10.1109/TIP.2006.888337.
