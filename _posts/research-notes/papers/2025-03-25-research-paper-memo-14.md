---
title: "A Gray Scale Correction Method for Side-Scan Sonar Images Based on Retinex"
excerpt: "논문 공부"
thumbnail: study_notes/lab-paper/250325_00.png
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/250325_00.png">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/250325_00.png">
  </a>
  <figcaption>
  Fig.1 A Gray Scale Correction Method for Side-Scan Sonar Images Based on Retinex
  </figcaption>
</figure>

Remote Sens. 2019, 11(11), 1281; https://doi.org/10.3390/rs11111281

Submission received: 24 April 2019 / Revised: 23 May 2019 / Accepted: 25 May 2019 / Published: 29 May 2019 

# 메모

다양한 영상 처리 기법과 평가 기준들을 제시하여 공부하는 재미가 있던 논문이었다.

아쉬운 점이 있다면, intro에서 인용한 논문들이 각각 grey scale correction보다는 feature matching 위주의 논문, 중국 저널이라 조회 자체가 불가능한 논문, 그리고 MDPI 중에서도 Remote Sensing 저널은 낫다지만 여전히 MDPI라는 점이 신경쓰이는 논문이라 아쉬운 면이 있다.

그리고 평가한 소나 이미지의 개수도 제한되어 있어, 잘 나온 결과만 제시한게 아닌가 하는 의심도 든다.

# 내용

## Intro

소나 이미지에 영향을 주는 다양한 요인들에 대해 설명하고, grey scale correction에 대해 [10-12] 3개 논문을 인용한다.

## Related Works

### TVG

TVG 소개하나, 한계점 제시:
1. TVG 수식의 계수 결정이 어려움
2. 서로 다른 소나 이미지에 대해서 서로 다른 계수를 설정해야 함 → not universal

### Histogram Equalization

HE는 쉽게 말하면 영상의 대비를 강조시키는 기법이라고 할 수 있겠다. 기술적으로는, 영상의 히스토그램 distribution을 equalizaing하는 것이다.

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/250325_01.jpg">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/250325_01.jpg">
  </a>
  <figcaption>
  Fig.2 Histogram Equalization
  </figcaption>
</figure>

하지만 노이즈도 강조된다는 단점과 경계면이 흐릿해지는 단점이 있다.

### Function Fitting

앞서 <a href="https://ingyu-lee.github.io/studies/research-paper-memo-13/">확인한 논문</a>에서와 같이 exponential curve fitting, 또는 이후에 읽을 "Shade correction of side-scan sonar imagery by histogram transformation" 논문의 Rayleigh distribution으로 커브피팅하는 경우가 있다.

이 경우 별다른 단점을 작성하지 않았다.

### Sonar Propagation Attenuation Model

Intensity Correction of Side-Scan Sonar Images 논문에서처럼 모델 수식을 사용하는 경우가 있으나, 앞서 확인한 TVG처럼 계수 결정이 어려움.

### Beam Pattern

* Data correction for visualisation and classification of sidescan SONAR imagery 논문 확인 필요

Model equation 기반으로 iterative하게 조정을 거친 것으로 보이는데, 상세한 내용을 확인해야 한다. 하지만 이 방법 또한 sediment와 해저면 형태가 바뀌면 사용하기 어렵다고 한다.

## Grey Scale Correction Method Based on Retinex

Retinex algorithm은 영상의 contrast나 sharpness를 향상시키기 위해서 사용되는 기법이다. 기본 원리는 영상에서 배경 성분과 반사 성분을 나누어서, 흐릿한 배경 성분을 제거하는 것이다.

\begin{equation}
    S(x,y) = R(x,y) \star L(x,y)
\end{equation}

$ S(x,y) $는 원본 이미지, $R(x,y)$는 reflectance map, $ L(x,y) $는 illumination map이고, operation $\star$는 element-wise multiplication이다.

그러면 배경 성분 $L$을 어떻게 얻느냐, 원본 이미지에 low-pass filter를 적용한 후 그 흐릿한 이미지를 배경이라고 가정하여 계산한다.

\begin{equation}
    F(x,y) = \lambda e^{-\frac{(x^2 + y^2)}{c^2}}
\end{equation}

\begin{equation}
    r(x,y) = \log{S(x,y)} - \log{ \left[ F(x,y) \otimes S(x,y) \right] }
\end{equation}

$r=\log R = \log (S/L)$, $\lambda$는 scale, $\otimes$는 convolution operation이다.

이 방법은 Single Scale Retinex(SSR)이다. 이미지를 서로 다른 low pass filter로 사용해 weight를 가해 처리하는 경우를 Multi-Scale Retinex(MSR)이라고 한다.

\begin{equation}
    r(x,y) = \sum^K\_k W\_k \left[ \log{S(x,y)} - \log{ \left[ F\_k(x,y) \otimes S(x,y) \right] } \right]
\end{equation}

$K$가 low-pass filter의 개수이다.

## Method

\begin{equation}
    S'(x,y) = A \frac{S(x,y)}{S(x,y) \otimes F(x,y) + a}
    \label{eq:temp00}
\end{equation}

이 논문에서 제시하는 방법은 SSR과 다음 세 가지 면에서 차별점을 보인다.

1. SSR은 원본 이미지의 로그를 계산한 후 가우시안 필터를 사용해서 배경 성분을 계산하나, 본 논문에서 제시하는 방법은 원본 이미지를 직접 mean filter나 bilateral filter로 배경 성분을 계산함.
2. SSR은 배경 성분 계산에 있어 anti-log operation으로 계산하나, 이 경우 대비가 강조되는 경우가 있음. 본 논문은 반사 성분에 상수를 곱하여 배경 성분을 복원함.
3. SSR은 별도의 노이즈 방지 수단이 없으나, 본 논문에서 제시하는 방법은 스무딩된 이미지에 일정한 상수를 더하여 배경 성분을 계산하므로 노이즈를 방지할 수 있음.

이 점으로 인해서 SSS 이미지 처리에 보다 적합하다고 함.

## Experiment

이 논문은 여러 SSS experiment data를 활용하여 위 수식 \ref{eq:temp00}의 각 parameter에 대해 분석한다.

### Parameter A

$A$는 수식 \ref{eq:temp00}에서 볼 수 있듯이 결과의 크기에 관한 상수이다. 이 논문에서는 별다른 수학적 분석보다는 human perception을 근거로 적절한 값으로 결정한다.

### Parameter a

위와 마찬가지로, 논문에서는 직접 parameter a의 값을 변화시키며 그 결과의 차이를 확인하고, 적절한 값으로 결정한다.

하지만 이게 맞는지는 잘 모르겠다. 앞서 Method에서는 이 a의 목표가 노이즈 방지라고 설명했는데, 개인적으로는 이 노이즈 방지라는 의미가 NaN값을 방지하는 의도라고 생각한다. 즉, (original value) $\gg $ (filtered value)일 경우나, (filtered value) = 0 일 경우에 대한 값이라고 생각한다.

a=0라고 생각하면, 어떤 신호를 low-pass filtered value 으로 나눈다는 것이니, 저역대를 낮추고 고역대를 높인다는 느낌으로 생각해볼 수 있겠다.

a가 어떤 양수 값을 가진다는 것은, denominator의 frequency domain에서 DC성분이 늘어난다는 것을 의미한다. 즉, 결과 값의 전반적인 bias가 감소한다는 것이다.

그런 의미에서 논문에서 보인 결과를 다시 한번 보면, a가 커질수록 contrast가 커지는 것은, 결국 bias가 감소하니 signal intensity difference가 같더라도 더 contrast가 커지는 것이다.

### Smoothing Function

본 논문에선 retinex에서 배경 성분을 계산하기 위한 smoothing function으로 mean filter와 bilateral filter를 사용하여 비교하였다.

Bilateral filter는 gaussian filter kernel에 signal intensity 기반 gaussian distribution을 추가한 것으로, 2D filter에 대해 다음과 같다.

\begin{equation}
    I\_{\text{filtered}}(p) = \frac{1}{W(p)} \sum\_{q \in \Omega} G\_s\left( \| p - q \| \right) \cdot G\_r\left( I(p) - I(q) \right) \cdot I(q)
\end{equation}

$  I\_{\text{filtered}}$는 필터 결과 신호 강도, $W(p)$는 normalization factor, $ G\_s $는 spatial Gaussian kernel, $p, q$는 각 데이터 포인트의 위치, $G\_r$는 range Gaussian kernel, 즉 signal intensity 차이에 의한 weight, 그리고 $ I(p), I(q) $는 각 데이터 포인트의 signal intensity이다.

가우시안이 두 번 들어가는 점에서, Bilateral filter의 computational complexity는 Gaussian filter보다 kernel의 영향을 더 받는다.

하지만 본문의 figure 8에서 보이는 것처럼, edge preserving 덕분에 외곽에서 밝아지는 효과가 없다.

### Comparative Experiments and Analysis of Other Methods Based on Retinex

Retinex 기반 알고리즘, SSR, MSR, MSRCR, 그리고 MSRCP를 비교군으로 하여, PSNR, informational entropy, std, 그리고 average gradient를 평가 항목으로 하였다.

그리고, low-light image enhancement (LIME), naturalness preserved enhancement (NPE), simultaneous reflection and illumination estimation (SRIE), multi-deviation fusion method (MF), 그리고 논문에서 제시한 방법 중 mean filter를 사용한 경우와 bilateral filter를 사용한 경우를 추가로 비교하였다.

### Comparative Experiments and Analysis of Gray Scale Correction Methods for Side-Scan Sonar Images

Histogram equalization, non-linear compensation, 그리고 function fitting을 비교군으로 하여 PSNR, informational entropy, std, 그리고 average gradient를 평가 항목으로 하였다.


---

# 참고문헌

X. Ye, H. Yang, C. Li, Y. Jia and P. Li, "A gray scale correction method for side-scan sonar images based on retinex", *Remote Sens.*, vol. 11, no. 11, pp. 1281, May 2019.

E. H. Land, "The Retinex theory of color vision," Scientific American, vol. 237, no. 6, pp. 108–128, Dec. 1977.

<a href="https://kipl.tistory.com/65">Retinex 알고리즘</a>

C. Tomasi and R. Manduchi, "Bilateral filtering for gray and color images," Sixth International Conference on Computer Vision (IEEE Cat. No.98CH36271), Bombay, India, 1998, pp. 839-846, doi: 10.1109/ICCV.1998.710815.

<a href="https://velog.io/@jungizz_/%EC%98%81%EC%83%81%EC%B2%98%EB%A6%AC-5.5-Bilateral-Filtering">[영상처리] 5.5 Bilateral Filtering</a>
