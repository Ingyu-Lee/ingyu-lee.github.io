---
title: "Two self-adaptive methods of improving multibeam backscatter image quality by removing angular response effect"
excerpt: "논문 공부"
thumbnail: study_notes/lab-paper/250410_00.png
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/250410_00.png">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/250410_00.png">
  </a>
  <figcaption>
  Fig.1 Two self-adaptive methods of improving multibeam backscatter image quality by removing angular response effect
  </figcaption>
</figure>



# 요약

이 논문은 multibeam echo sounder(MBES)의 각도 응답(AR, Angular Response) 효과를 제거하기 위한 두 가지 self-adaptive 보정 방법, AR 모델링 방법과 AR 클러스터링 방법을 제안한다. 전자는 평균 AR 곡선의 AR 파라미터를 이용해 모델링하고 보정하는 방식이며, 후자는 각 해저 퇴적물의 AR 곡선을 이용해 보정하는 방식이다.

# 내용

## Introduction

본 논문은 multibeam echo sounder(MBES)의 입사각에 따른 신호 왜곡을 보정하기 위한 기법을 소개한다. 기존 방법은 Lambert law를 사용하거나, 일부 개선한 모델을 사용하였는데[9], 이러한 모델은 sediment의 급격한 변화를 고려하지 못한다는 한계가 있다.

AR 파라미터는 sediment와 관련이 있으며, 많은 연구들에서 해저 분류를 위해 사용되어 왔다 [10–12]. 이는 적절한 AR 파라미터를 찾고 정확한 퇴적물 분류를 수행하면 AR 보정이 가능함을 시사한다. 이러한 아이디어를 바탕으로, 이 논문에서는 두 가지 self-adaptive 방법인 AR 모델링 방법과 AR 클러스터링 방법을 제안한다.

## Scattering pattern and AR parameters

그림 1에서 볼 수 있듯이, BSP(beam scattering pattern)는 각도에 따라 $BS\_1$, $BS\_2$, $BS\_3$ 3 가지로 분류되며, 그 세가지 영역에 대해 transition region $D\_1-D\_2$, $D\_2-D\_3$가 있다.

AR 파라미터는 다음과 같다.

* 도메인 간 boundary angle
* 각 도메인의 평균 BS
* 각 영역의 기울기 $k\_1$ $k\_2$ $k\_3$

## AR correction used in Kongsberg EM series

최신 다중빔 에코사운더(MBES) 시스템, 예를 들어 Kongsberg EM 시리즈는 스페큘러 영역($D\_1$)의 BS에는 선형 AR 보정을 적용하고, 산란 영역($D\_2$)과 고입사각 영역($D\_3$)의 BS에는 Lambert 법칙에 따른 보정을 적용한다.

그러나 EM 모델에는 다음과 같은 문제점이 존재한다:

$D\_1$과 $D\_2$만을 고려하고 있어, $D\_3$ 영역에서의 보정이 불완전하게 되고, 인접한 조사선의 중복 지역(co-located area)에서 BS 값에 불일치가 발생한다.

$D\_1$과 $D\_2$ 사이의 경계각(교차 각도)을 25°로 고정하지만,
실제로는 해저 퇴적물에 따라 5°~30° 사이로 달라진다 [14].

Kongsberg EM 시리즈는 BS 획득 시 실시간 데이터 처리를 보장하기 위해 이전 BS 데이터를 기반으로 실시간 보정 모델을 구축하는데, 이는 추정된 파라미터에 의해 부정확한 보정을 초래할 수 있다.

이러한 문제들로 인해 AR 보정이 불완전해지고, 그림 2b에 나타난 것처럼 다중빔 반사 영상에 “밝은 띠(brighter bands)” 현상이 나타난다.

## Method 1: the AR modeling method

제안된 방법은 AR 파라미터를 이용한 모델을 구축하여 AR 보정을 수행하며, 총 4단계로 구성된다: 평균 AR 곡선 추출, weighted moving average 처리, AR 파라미터 추출, 그리고 AR 모델링이다. 그 흐름도는 fig.3에 제시되어 있다.

### Step 1: getting the average AR curve of continual pings

BS 데이터에는 무작위 오차가 존재하므로, 정확한 AR 곡선을 얻기 위해 연속적인 핑(ping)을 평균을 낸다 [12, 15, 16]. 보정 대상 핑을 중심으로 N개의 핑을 평균하여 평균 AR 곡선을 계산한다.

이전에, 각 핑의 BS 데이터는 스플라인 보간법을 이용해 동일한 각도 간격으로 리샘플링되어야 한다. 각 간격은 원래 샘플링 간격과 유사하게 설정해야 한다. 이 과정은 그림 3a, 3b에 나타나 있다.

### Step 2: weighted moving average on the AR curve

Fig.3b처럼, 평균 AR 곡선을 부드럽게 하기 위해 가중 이동 평균 처리가 수행한다. 가중 이동 평균은 합성곱(convolution) 연산으로 볼 수 있다.

### Step 3: extracting AR parameters

앞서 결정한 AR 파라미터는 다음과 같음: 도메인 간의 경계, 각 도메인의 평균 BS, 그리고 AR 곡선의 기울기이다. 경계가 결정되면 각 도메인의 나머지 파라미터들을 구할 수 있으므로 경계부터 계산한다.

경계는 AR 곡선의 이차 미분 곡선에서 발견할 수 있다 [10]. D1과 D2의 경계는 5°~30° 사이에서 최대 봉우리를 찾고, D2와 D3의 경계는 45°~60° 사이에서 찾는다.

이차 미분 곡선을 이용한 자동 경계 검출은 그림 3d에 나타나며, 해당 경계는 그림 3e에 표시되어 있다. 이후 각 도메인에서 평균 BS는 해당 영역 내의 모든 BS 값을 평균하여 계산하며, 기울기는 linear regression을 통해 산출된다.

### Step 4: establishing the AR model for AR correction

$D\_2-D\_3$의 transition region은 매우 작으므로 무시한다.

수식 (3)은 1, 1-2, 2, 3 영역의 BS 수식이다.

$D\_1$ 및 $D\_3$ 영역은 linear function이다. $D\_1-D\_2$ 영역은 linear interpolation이다. $D2$ 영역은 Lambert Law를 사용하였다.

기존 EM 모델과의 비교에서 제안된 방법의 장점은 다음과 같다:

실제 AR 파라미터를 사용하여 AR 모델을 구축함으로써 실제 빔 산란 패턴(BSP)을 더 정확히 반영한다.

세 가지 주요 도메인(D1, D2, D3)과 전이 영역(D1–D2)에 대해 각각 모델을 구축함으로써 실제 AR 곡선을 더 정밀하게 근사할 수 있다.

## Method 2: the AR clustering method

앞서 소개한 AR 모델링 방법은 세 개의 영역 경계를 정확히 탐지하지 못하면 AR 보정이 부정확해지는 단점이 있다. 또, 해당 방법은 sediment의 AR 곡선에 미치는 영향을 고려하지 않는다.

AR 클러스터링 방법은 서로 다른 퇴적물의 AR 곡선을 얻어 AR 보정을 수행한다. 이 method는 총 4 단계, 적절한 AR 파라미터 선택, unsupervised classification, 다양한 퇴적물의 AR 곡선 획득, 그리고 AR 보정이라는 4 단계가 포함되며, 이는 그림 4에 나타나 있다.

### Step1: selecting AR parameters

앞서 정의한 AR parameters를 sediment classification에 사용한다.

### Step2: unsupervised seabed classification

Unsupervised seabed classification은 k-means clustering을 사용한다. simplicity, speediness and applicability라는 장점이 있으나, non-unique results를 갖는다는 문제와 classifying number k를 결정해야 하는 문제가 있다. Non-unique results 문제는 k-means++ 알고리즘으로 해결할 수 있다. k 결정 문제는 반복 연산을 수행하고, 이는 Discussion 장에서 설명한다.

Unsupervised seabed classification의 순서는 다음과 같다.

1. 초기 k를 설정하고, k-means++ 알고리즘을 사용하여 클러스터 중심을 초기화한다.

2. 아래 식으로 파라미터 집합($\rm{BS\_{0-1}}, \rm{BS\_{0-2}}, \rm{BS\_{0-3}}$)과 각각의 centroid 사이의 거리 $s\_i$를 계산한다.

\begin{equation}
    s\_i = \sqrt{(\rm{BS\_{0-1}}-c\_{i1})^2 + ( \rm{BS\_{0-2}}-c\_{i2} )^2 + ( \rm{BS\_{0-3}}-c\_{i3} )^2}
\end{equation}

3. 각 BS를 가장 가까운 중심을 가진 클러스터에 할당한다. 또는, 만약 재할당 시 클러스터 내 제곱합 거리의 총합이 감소한다면, 모든 BS를 개별적으로 다른 중심에 재할당한다.

4. 각 클러스터의 모든 BS 평균을 계산하여 k개의 새로운 중심 위치를 얻는다.

5. 클러스터 할당이나 분류가 변경되지 않거나 최대 반복 횟수에 도달할 때까지 (2)~(4)를 반복한다.

### Step 3: getting the AR curves of different sediments

Classified data에 대해 동일 각도 간격으로 리샘플링된 BS의 평균을 계산해 AR 곡선을 얻는다. 본문 fig. 4c에서 그 예시를 볼 수 있다.

### Step 4: AR correction

AR correction은 다음 식 (7)을 통해 보정된다.

\begin{equation}
    \rm{BS\_{c}} = \rm{BS\_{r}} - \rm{BS\_{ARC}} + \rm{BS\_{0-2}}
\end{equation}

여기서 $\rm{BS\_{r}}$은 raw data, $\rm{BS\_{ARC}}$는 입사각에 따른 값, $\rm{BS\_{0-2}}$는 AR 곡선의 $D2$ 평균 BS, $\rm{BS\_{c}}$는 보정된 BS이다.

Fig. 4e, 4f에서 이 과정을 확인할 수 있다. Raw data인 fig.4a와 fig.4d 를 비교해 보면, 그림 4a에 보이는 밝은 띠(bright band)가 그림 4d에서는 제거된 것을 확인할 수 있다.

## Experiments and Analysis

실험 데이터를 통해 검증하였다.

표 1에서 raw data, Kongsberg에서 제공하는 EM model, 본 논문에서 제시한 두 가지 방법을 mean deviation으로 비교하였다.

표 2에서 raw data, Kongsberg에서 제공하는 EM model, 본 논문에서 제시한 두 가지 방법을 STD로 비교하였다.

Sediment와 평균 필터의 크기, Hanning window의 크기 등 hyperparameter의 결정도 논의한다.

---

# 참고문헌

J. Zhao, J. Yan, H. Zhang, and J. Meng, "Two self-adaptive methods of improving multibeam backscatter image quality by removing angular response effect," Journal of Marine Science and Technology, vol. 22, no. 2, pp. 288-300, 2017/06/01 2017.
