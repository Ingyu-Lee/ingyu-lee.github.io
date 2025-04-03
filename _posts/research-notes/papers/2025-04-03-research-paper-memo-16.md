---
title: "Data correction for visualisation and classification of sidescan SONAR imagery"
excerpt: "논문 공부"
thumbnail: study_notes/lab-paper/250403_00.png
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/250403_00.png">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/250403_00.png">
  </a>
  <figcaption>
  Fig.1 Data correction for visualisation and classification of sidescan SONAR imagery
  </figcaption>
</figure>

Publication: IET Radar, Sonar & Navigation Volume 2, Issue 3

https://doi.org/10.1049/iet-rsn:20070032

# Abstract

이 논문은 사이드 스캔 소나(SSS) 데이터를 전처리하는 방법을 제안한다.

SSS 데이터는 거리, 각도, 센서의 해저 대비 고도 등 다양한 영향을 받기 때문에 신호 전처리가 필요하다. 이 논문에서 제안된 방법은 소나 데이터 수신 과정의 물리학 및 기하학에 기반하여, 이미지 데이터로부터 거리 및 각도에 대한 보정 계수를 추정한다. 계산된 후 이 계수들은 전체 데이터에 대한 radiometric correction을 적용할 수 있다. 이미지 통계에서 swath 전반에 걸쳐 mean과 std가 더 안정적으로 개선되는 것을 확인할 수 있다.

이 방법은 각 전송 시점의 센서 고도를 추정하기 위한 정밀한 해저 탐지 알고리즘을 필요로 하며, 각도 의존성 보정 계수를 계산 및 적용하기 위한 리샘플링 기법을 포함한다. 두 개의 대규모 영역 조사를 통해 향상된 분류 성능을 보여주는 결과가 제시된다. 제안된 방법은 이전에 보고된 리샘플링 기법보다 더 나은 결과를 제공하며, 정확성, 견고성, 사용 용이성 및 실행 시간 측면에서 상당한 개선을 제공한다.

# 내용

## Intro



---

# 참고문헌

[1]	C. G. Capus, A. C. Banks, E. Coiras, I. Tena Ruiz, C. J. Smith, and Y. R. Petillot, "Data correction for visualisation and classification of sidescan SONAR imagery," *IET Radar, Sonar & Navigation*, vol. 2, no. 3, pp. 155-169, 2008/06/12 2008.
