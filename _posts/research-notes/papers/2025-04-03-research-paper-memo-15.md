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

*다만 2008년 논문이어서인지 신호 모델 수식에 비해 fitting 수식은 2차함수로 간단하게 근사하였고, 때문에 fig.10 에서도 처음 바닥면에 닿는 신호의 일부분은 무시한 것을 확인할 수 있다.

*또 curve fitting을 데이터 누적 후 coordination transformation 후 median 값을 가져와 수행하기 때문에, real-time operation이 아니라는 한계도 있다.

# 내용

## Intro

제안된 방법은 얕은 수심과 저고도 조사에 적합하며, 보정된 데이터에 대해 향상된 classification 성능을 제공한다.

기존 연구 중에서는 선박 방향 정보를 활용한 연구도 있으나, 이 연구에서는 소나 데이터로부터 바로 보정치를 계산한다. 때문에 센서 데이터 누락 시에도 사용할 수 있다.

## Sidescan Data Interpretation

### Beam pattern

이 논문에서는 N-array transducer의 beam pattern 수식을 사용한다.

\begin{equation}
    B(\theta) = \left[ \frac{\sin\left( N \left( \pi d/\lambda \right) \sin\left( \theta \right) \right)}{N \sin\left( \left( \pi d/\lambda \right) \sin\left( \theta \right) \right)} \right]^2
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

각도 영향을 확인하기 위해 소나 데이터를 시간(=거리)축이 아닌, 각도 축으로 변환시킨다. 이 변환은 각 핑(ping)에서의 고도 추정을 기반으로 한 리샘플링 기법을 통해 수행된다.

리샘플링은 폴리페이즈 필터(polyphase filter) [3]를 사용하여 수행되며, sampling rate는 $d\_{ref} / d(n)$이다. 여기서 $n$은 데이터 라인 번호, $d\_{ref}$는 reference 데이터 라인의 첫번째 반사 위치 데이터 넘버, ${d(n)}$은 n번째 데이터 라인의 첫번째 반사 샘플 넘버이다.

*폴리페이즈 필터는 FIR interpolator 종류 중 하나이며, all-pass filter이며, 주로 위상 특성에서 차이를 보인다. 이로 인해 “폴리페이즈(polyphase)”라는 명칭이 붙는다. [3]

리샘플링 후, 각도 기준으로 모든 행에 대해 중앙값을 계산할 수 있다. 논문에서는 리샘플링된 이미지는 $I'(n, m)$로, 각도 기준 중앙값은 $\tilde{I}'(m)$로 표기하였다.

그림 7a, 7b는 그림 3의 데이터를 리샘플링 전후(빔 각도 기준 재정렬 전후)의 모습을 보여준다.

그림 7c, 7d는 각각 리샘플링 전후의 트랙 방향 중앙값 $\tilde{I}(m)$, $\tilde{I}'(m)$를 보여준다.

#### Intensity variation with altitude

아래 수식으로 $C^R$을 모델링했다.

\begin{equation}
    C^R\left( d(n) \right) = C1\left( \frac{d\_{ref}}{d(n)} \right)^2 + C2\left( \frac{d\_{ref}}{d(n)} \right) + C3
\end{equation}

본문의 그림 8처럼 데이터에 대해 curve fitting하여 $C^R$의 계수, $C1, C2, C3$를 계산한다.

#### Initialization

각도 보정 요소와 거리 보정 요소는 각각 $\tilde{I}$, $\tilde{I}'$에서 유도된다. 각도 효과는 트랜스듀서 근처에서, 거리 효과는 영상의 가장자리에서 더 우세하다고 가정하여, $\tilde{I}'(m)$에는 삼각형 가중치(triangular weighting)가 적용된다.

\begin{equation}
    C^G\_0(m) = \frac{1}{\tilde{I}(m)}
\end{equation}

\begin{equation}
    C^\theta\_0(m) = \frac{1}{W(m)\tilde{I}'(m)}
\end{equation}

\begin{equation}
    W(m) = (W\_{max} - W\_{min}) \times \left( 1 - \left| \frac{m}{M/2} -1 \right| \right) + W\_{min}
\end{equation}

가중치 한계 $W\_{max} = 1.9$, $W\_{min} = 0.1$로 설정하면, $W_T(m)$는 평균 가중치가 1.0이 되어 수중 컬럼 근처에서는 거리 효과를, 가장자리에서는 각도 효과를 일부 표현할 수 있도록 한다.
초기 거리 보정 계수는 모든 샘플에서 1.0으로 설정된다.

$C^G(m)$와 $C^\theta(m)$는 1로 normalize되므로 전체 데이터의 intensity는 남은 보정 계수인 $C^R$에 의해 결정된다.

#### Application of correction factors

보정 계수는 line by line으로 적용된다.

---

# 참고문헌

[1]	C. G. Capus, A. C. Banks, E. Coiras, I. Tena Ruiz, C. J. Smith, and Y. R. Petillot, "Data correction for visualisation and classification of sidescan SONAR imagery," *IET Radar, Sonar & Navigation*, vol. 2, no. 3, pp. 155-169, 2008/06/12 2008.

[2]	W. U. S. A. P. LAB., APL-UW High-Frequency Ocean Environmental Acoustic Models Handbook. Defense Technical Information Center, 1994.

[3]	J. G. Proakis and D. G. Manolakis, Digital signal processing (3rd ed.): principles, algorithms, and applications. Prentice-Hall, Inc., 1996.

