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

이 논문은 사이드 스캔 소나(SSS) 데이터의 전처리를 제안한다.

이 논문에서 제안한 전처리는 소나 데이터 수신 과정의 수식 모델에 기반해 거리 및 각도에 대한 보정을 수행한다. 보정 후 mean과 std가 개선되는 것을 확인할 수 있다.

두 개의 실험 데이터로 검증한다. 기존 방법보다 accuracy, robustness, usability and execution times에 대해 더 나은 것을 보인다.

# 내용

## Intro

제안된 방법은 얕은 수심과 저고도 조사에 적합하며, 보정된 데이터에 대해 향상된 classification 성능을 제공한다.

기존 연구 중에서는 선박 방향 정보를 활용한 연구도 있으나, 이 연구에서는 소나 데이터로부터 바로 보정치를 계산한다. 때문에 센서 데이터 누락 시에도 사용할 수 있다.

## Sidescan Data Interpretation

### Beam pattern

이 논문에서는 N-array transducer의 beam pattern 수식을 사용한다.

\begin{equation}
    B(\theta) = \left[ \frac{\sin\left( N \left( \pi d/\lambda \right) \sin\left( \theta \right) \right)}{N \sin\left( \left( \pid/\lambda \right) \sin\left( \theta \right) \right)} \right]^2
\end{equation}

### Backscatter and grazing angle

이 논문에서는 backscatter intensity model로 University of Washington (APL-UW) models를 사용한다. [2] 다만 해당 책에는 요즘 소나만큼의 고주파 모델은 없다고 한다.

### Range dependent factors

TVG를 사용한다.

### Altitude variation

해저면에 대한 고도 계산은 water column을 기반으로 한 bottom-tracking 알고리즘을 사용한다.

---

# 참고문헌

[1]	C. G. Capus, A. C. Banks, E. Coiras, I. Tena Ruiz, C. J. Smith, and Y. R. Petillot, "Data correction for visualisation and classification of sidescan SONAR imagery," *IET Radar, Sonar & Navigation*, vol. 2, no. 3, pp. 155-169, 2008/06/12 2008.

[2]	W. U. S. A. P. LAB., APL-UW High-Frequency Ocean Environmental Acoustic Models Handbook. Defense Technical Information Center, 1994.
