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

## Method

### Imaging model

\begin{equation}
    I(p) = G(p)R(p)B(\theta, p)\gamma(\theta,p)Z(p)
\end{equation}

여기서 $I(p)$는 signal intensity, $G(p)$는 TVG의 값, $R(p)$는 spreading 및 absorption에 의한 loss, $B(\theta, p)$는 beam pattern, $\gamma(\theta, p)$는 backscatter strength이다. $B$와 $\gamma$ 는 각도에 영향을 받고, $G$와 $R$은 거리에 영향을 받는다. 이 네 가지 요소를 보정하면, flat seabed를 가정할 때, $Z$는 표면의 거칠기 또는 질감으로 인한 반사 강도의 변화를 나타낸다.

본 논문에서는 이 모델을 직접 계산하기보다는, 이 모델을 기반으로 보정하기 위한 함수를 따로 제시한다.

\begin{equation}
    J(p) = I(p)C^R(p)C^G(p)C^\theta(p)
\end{equation}

$C^R(p)$는 거리에 따른 보정을 위한 quadratic function, $C^G(p)$는 소나 전반에 걸친 fixed gain, $C^\theta(p)$는 수직 방향 빔 패턴과 grazing angle에 의한 각도 보정을 위한 함수이다.

$C^R$과 $C^G$는 소나 고도 정보가 필요하기 때문에 bottom-tracking algorithm을 사용해 고도를 추정한다. 이 논문에서는 bottom-tracking을 위해 selection of maximum derivatives 방법을 사용한다. 이는 픽셀값의 변화가 가장 큰 지점을 찾는 방법이다.

### Symmetry

거리 및 fixed gain에 관한 $C^R$ 및 $C^G$는 좌우 대칭을 적용하나, 각도에 관한 $C^\theta$는 좌우대칭을 적용하지 않는다.

### Estimation of the correction factors

Iteratively 거리 방향 factor와 각도 방향 factor를 분리하여 확인한다.

#### Estimation by along-track averaging

SSS 스캔 방향에 대해 중간값median을 확인하여 보정치를 계산한다.

일정한 고도로 flat seabed를 스캔하는 경우 거리 영향과 각도 영향을 분리할 수 없으나, 센서 고도가 변하는 경우 data resampling을 통해 각도 영향을 강조할 수 있다.

#### Resampling

센서 고도의 변화가 있는 상황에서는, 데이터를 획득 시간(즉 거리)에 따라 정렬하는 대신, 빔 각도에 따라 데이터를 정렬함으로써 각도에 따른 강도 변화를 추정할 수 있다. 이 재정렬은 각 핑(ping) 시간에서의 고도 추정을 기반으로 한 리샘플링 기법을 통해 수행된다.

리샘플링은 폴리페이즈 필터(polyphase filter) [3]를 사용하여 수행되며, 샘플링 비율 변환은 비율 $d\_{ref} / d(n)$에 따라 결정된다. 여기서 dref는 기준 라인의 첫 반사 위치 샘플 번호이고, d(n)은 n번째 라인의 첫 반사 샘플 번호이다 (이들은 바닥 탐지 결과로부터 얻음).

리샘플링 후, 각도 기준으로 모든 행에 대해 중앙값을 계산할 수 있다.
리샘플링된 이미지는 **I′(n, m)**로 표기되며, 각도 기준 중앙값은 **Ĩ′(m)**로 나타낸다.

    그림 7a, 7b는 그림 3의 데이터를 리샘플링 전후(빔 각도 기준 재정렬 전후)의 모습을 보여준다.

    그림 7c, 7d는 각각 리샘플링 전후의 트랙 방향 중앙값 Ĩ(m), Ĩ′(m)를 보여준다.

주의: 리샘플링 후 중앙 수심 근처에서는 빔 패턴이 더 세밀하게 표현되지만, 가장자리로 갈수록 사용 가능한 샘플 수가 적어지기 때문에 노이즈가 증가한다. 누락된 데이터는 리샘플링된 이미지에서 검정색으로 표시된다.

---

# 참고문헌

[1]	C. G. Capus, A. C. Banks, E. Coiras, I. Tena Ruiz, C. J. Smith, and Y. R. Petillot, "Data correction for visualisation and classification of sidescan SONAR imagery," *IET Radar, Sonar & Navigation*, vol. 2, no. 3, pp. 155-169, 2008/06/12 2008.

[2]	W. U. S. A. P. LAB., APL-UW High-Frequency Ocean Environmental Acoustic Models Handbook. Defense Technical Information Center, 1994.
