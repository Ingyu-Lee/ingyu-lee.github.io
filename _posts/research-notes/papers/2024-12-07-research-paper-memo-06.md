---
title: "Real-time sonar image enhancement for AUV-based acoustic vision"
excerpt: "연구실 논문 공부"
thumbnail: study_notes/lab-paper/241202_00.png
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/241202_00.png">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/241202_00.png">
  </a>
  <figcaption>
  Fig.1 Real-time sonar image enhancement for AUV-based acoustic vision
  </figcaption>
</figure>

Ocean Engineering

Volume 104, 1 August 2015, Pages 568-579

# 내용

Recursive least squares (RLS) 알고리즘에 adaptive control of window length를 적용해 소나 이미지의 speckle noise를 저감시키는 연구이다.

## Speckle Noise Model

Speckle noise 에 의한 pixel value는 다음과 같이 표현할 수 있다. <sup>[2](#footnote_1)</sup>

\begin{equation}
  \displaylines
  {
    y\_{ij} (t) = x\_{ij} (t) \times n\_{ij}(t)
  }
  \label{eq:eq00}
\end{equation}

\[y\_{ij}\]는 measured pixel value, \[x\_{ij}\]는 true data, 그리고 \[n\_{ij}\]는 speckle noise로, 평균이 1인 random variable로 가정된다.

RLS를 적용하기 위해서는 linearization이 필요하므로, 양변에 로그를 적용하여 아래와 같이 나타낸다.

\begin{equation}
  \displaylines
  {
    \ln \left( y\_{ij} (t) \right) = \ln \left( x\_{ij} (t) \right) + \ln \left( n\_{ij}(t) \right)
  }
  \label{eq:eq01}
\end{equation}

\begin{equation}
  \displaylines
  {
    d\_{ij} (t) = w\_{ij} (t) + v\_{ij} (t)
  }
  \label{eq:eq02}
\end{equation}

where \[ d\_{ij} (t) = \ln \left( y\_{ij} (t) \right) \], \[ w\_{ij} (t) = \ln \left( x\_{ij} (t) \right) \], and \[ v\_{ij} (t) = \ln \left( n\_{ij} (t) \right) \].

## RLS

신호 모델을 다음과 같이 가정한다.

\begin{equation}
  \displaylines
  {
    d (t) = \mathbf{u}^{T}(t) \mathbf{w} (t) + v (t)
  }
  \label{eq:eq03}
\end{equation}

\[ d (t) \]와 \[ v (t) \]는 각각 time \[t\]에서의 측정값과 측정 노이즈, 그리고 \[\mathbf{u}(t)\]와 \[\mathbf{w} (t)\]는 각각 input data vector와 찾아야 하는 unknown parameters이다.

RLS에서는 estimation of \[\mathbf{w} (t)\], 즉 \[\hat{\mathbf{w}} (t)\]를 다음과 같이 찾는다.

\begin{equation}
  \displaylines
  {
    \hat{\mathbf{w}} (t) = \arg \min\limits\_{\mathbf{w}} \sum^{t}\_{i=1}{\left( d(i) - \mathbf{u}^{T}(i) \mathbf{w} \right)^2 }
  }
  \label{eq:eq04}
\end{equation}

이 이후의 자세한 recursive eqn. 은 논문 본문의 식 (7)번 이후를 찾아보기로 하자. 위 식에서 볼 수 있는 건 \[i = 1 \rightarrow t\]까지 최소화를 시킨다는 것이다. 때문에 소나가 저속으로 움직일 때는 speckle noise removal이 잘 작동하나, 소나가 고속으로 움직일 때는 잘 작동하지 않는 모습을 보인다.

때문에 본 연구에서는 time domain에 대해 limited window를 적용하여, 고속으로 움직일 때와 저속으로 움직일 때의 window length에 차등을 두어 RLS를 적용했다.

결과는 실험 데이터를 standard RLS, fixed data length RLS, proposed method 3 가지 적용에 대해 peak SNR value와 연산 시간을 비교하였다.

# 생각

연구실 NAS에 코드가 있는지 찾아보고, median filter와 성능 비교를 해봐야겠다.

# Todo

* 연구실 NAS 코드 찾아보기

* C++ median filter 코드 찾아보기

---

# 참고문헌

H. Cho, and S. -C. Yu. "Real-time sonar image enhancement for AUV-based acoustic vision," in Ocean Engineering, vol. 104, pp. 568-579, 2015.

<a name="footnote_1">2</a> J. -S. Lee, "Digital Image Enhancement and Noise Filtering by Use of Local Statistics," in IEEE Transactions on Pattern Analysis and Machine Intelligence, vol. PAMI-2, no. 2, pp. 165-168, March 1980, doi: 10.1109/TPAMI.1980.4766994.