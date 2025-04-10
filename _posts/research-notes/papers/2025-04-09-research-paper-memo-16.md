---
title: "Quantitative Backscatter Measurements With a Long-Range Side-Scan Sonar"
excerpt: "논문 공부"
thumbnail: study_notes/lab-paper/250409_00.png
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/250409_00.png">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/250409_00.png">
  </a>
  <figcaption>
  Fig.1 Quantitative Backscatter Measurements With a Long-Range Side-Scan Sonar
  </figcaption>
</figure>

Published in: IEEE Journal of Oceanic Engineering ( Volume: 14, Issue: 4, October 1989) 

DOI: 10.1109/48.35987

Date of Publication: 06 August 2002


# 요약

SSS의 backscatter를 정량적으로 확인하는 논문이다.

TVG와 빔패턴을 고려하여 acoustic model을 세우고, 그에 따른 backscatter 를 정량적으로 확인한다.

# 내용

## Intro

표면의 무차원 반사 계수(backscattering coefficient) $S\_b$는 다음과 같이 정의된다.

\begin{equation}
    S\_b = \frac{P\_b}{I\_i A}
\end{equation}

여기서 $P\_b$는 단위 입체각당 표면에서 반사된 파워 (W/steradian), $I\_i$는 표면에 입사된 음향 강도 (W/m²), $A$는 유효 조사 면적(effective insonified area, m²)이다.

반사 강도(backscattering strength)는 무차원 반사 계수의 로그 스케일로, $10 \log\_10 S\_b$ (dB)로 정의한다.

기존 [3-6] 연구에서는 입사각, sediment(거칠기와 acoustic impedance), 그리고 주파수와 어떤 관계가 있는지 연구하였다. 일반적으로 이러한 연구 결과에 따르면, 중간 입사각에서는 반사 강도와 입사각 간의 관계가 비교적 평탄한 반면, 정입사 방향에 가까워질수록 급격히 증가하고, 얕은 입사각에서는 급격히 감소하는 경향을 보인다. 대부분의 연구자들은 해저 유형에 따라 최대 25dB까지의 큰 차이가 존재한다는 데 동의한다.

## The Acoustic Model

이 연구에서 세운 acoustic model은 spherical spreading, exponential attenuation, beam pattern, 그리고 반사 면적(effective insonified area)의 식을 정리하여 만들어졌다.

\begin{equation}
    I\_b = PDb(\Phi) \frac{\exp(-2\alpha R)}{4\pi R^4}AS\_b
\end{equation}

단위는 $Wm^{-2}$ 이다. $R$은 거리, $P$는 power, $D$는 directivity factor, $b$는 beam directivity pattern, $\alpha$는 exponential attenuation coefficient(nepers/m), $A$는 effective insonified area이다.

단순화시킨 모델에서는 신호가 직선 경로를 따라 이동하며, 평평한 해저에 부딫힌다고 가정하였다. 해저면 대비 고도와 거리를 이용해 경사각 $\mu$를 계산하였으며, 방사각 $\Phi$는 $\Phi=\mu - 20^{\circ}$로 계산하였다. 소나 데이터에 대해 계산 결과는 본문의 fig.4 에서 확인할 수 있다.

## The Effects of Refraction and Topography

굴절 효과는 수심에 따른 수온 변화와 음속 변화에 따라 신호의 경로가 달라지는 것이다. 본문의 fig.6 에서 그 예시를 볼 수 있다. 

굴절 효과를 고려한 데이터는 fig.8 에서 확인할 수 있다.

## Limitations of the Acoustic Model

본 논문에서 고려한 음향 모델에도 몇 가지 한계가 있다. 반사파 경로에 대한 다중 경로(multiples), 수면 반사, yaw, 비구면 확산 손실 등은 고려되지 않았다는 것이다.

다중 경로 신호는 반사 강도가 매우 높은 물체 뒤에서 퍼진 신호로 관측된다. 그림 8(a)의 다중 경로 신호 M은 주 반사파 P보다 단지 15dB 낮을 뿐이다. 해저산맥과 같이 지형이 급변하는 지역에서는 해수면과 해저의 반사 계수를 정확히 추정할 수 없기 때문에
이러한 효과들을 제거하는 것은 매우 어렵다.

잔잔한 바다에서는 해수면에 의해 반사된 반사 에너지가 트랜스듀서로 되돌아오는 신호에 상당한 영향을 미친다. 또한, 트랜스듀서 배열의 요(yaw) 현상도 문제를 일으킨다. 요 현상이 발생하면, 배열 축이 송신 신호 방향에서 벗어나 있을 때 에너지가 수신되며, 이로 인해 소나 영상에 줄무늬 형태의 왜곡(striped appearance)이 나타난다.

# Results

[16], [4], [17] 에서는 낮은~중간 경사각에서의 반사 강도 결과가 Lambert 법칙에 잘 부합한다고 하였다. 본 연구에서도 마찬가지로 fig.11(a) 에서 볼 수 있듯이 Labert Law의 경향과 일치하는 것을 확인하였다.

다만, 데이터는 fitted manually되었으며, $S\_0$(Lambert Law의 y절편)는 다른 논문과 다른 값을 가졌다.

---

# 참고문헌

[1]	N. C. Mitchell and M. L. Somers, "Quantitative backscatter measurements with a long-range side-scan sonar," in IEEE Journal of Oceanic Engineering, vol. 14, no. 4, pp. 368-374, Oct. 1989, doi: 10.1109/48.35987.

