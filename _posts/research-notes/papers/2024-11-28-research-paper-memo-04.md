---
title: "Markov Random Field(MRF) image segmentation"
excerpt: "논문 공부"
thumbnail: study_notes/lab-paper/241121_00.jpg
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 30%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/241121_00.jpg">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/241121_00.jpg">
  </a>
  <figcaption>
  Fig.1 Markov Random Field Modeling in Image Analysis
  </figcaption>
</figure>

이 책의 모든 내용을 커버하기보다는, Markov random field를 활용한 image segmentation에서 사용되는 몇몇 변수들의 물리적 의미를 이해하는 선에서 그치고자 한다.

때문에 Ch. 1-2의 내용만을 다룬다.

# 내용

## MAP-MRF Framework

Image segmentation은 labeling problem이라고 할 수 있다. The problem은, a set of sites $ \mathcal{S} $를 a set of labels $ \mathcal{L} $로 매핑하는 함수 $f$라고 할 수 있다.

\begin{equation}
  \displaylines
  {
    f \\ : \\ \mathcal{S} \longrightarrow \mathcal{L}
  }
  \label{eq:eq00}
\end{equation}

예를 들어, $n \times m$ 이미지에서의 edge detection에서의 sites $ \mathcal{L} $와 labels $ \mathcal{L} $은 다음과 같이 생각할 수 있다.

\begin{equation}
  \displaylines
  {
    \mathcal{S} = \left\\{ \left( i, j \right) \vert 1 \leq i \leq n, \\ 1 \leq j \leq m \right\\}
  }
  \label{eq:eq01}
\end{equation}

\begin{equation}
  \displaylines
  {
    \mathcal{L} = \left\\{ \mbox{edge, nonedge} \right\\}
  }
  \label{eq:eq02}
\end{equation}

이 labeling problem은 site와 label의 성격에 따라 4 가지로 분류된다. 각각 site가 regular인지 irregular인지, label이 continuous한지 discrete한지에 따라 구분되는 식이다.

Regular와 irregular site는 각각 low-level processing인지, high-level processing인지로 나뉜다. Low-level processing의 예는, 앞서 예시를 든 edge detection이나, image restoration 또는 smoothing 등이 있다. High-level processing의 경우는 object matching, recognition, 또는 pose estimation 등이 있다.

Continuous label과 discrete label의 차이는 말 그대로 label이 continuous value를 가지는지, 또는 discrete한 value를 가지는지에 따라 구분된다. 예를 들어 앞서 예시를 든 edge detection의 경우 edge와 nonedge로 나누므로 discrete한 label이고, image smoothing의 경우 continuous한 pixel value를 다시 continuous한 pixel value로 mapping하는 것이므로 continuous label이라고 할 수 있겠다.

본인이 공부하고자 하는 MRF image segmentation의 경우 regular site, discrete label이므로 교과서에서 다루는 분류대로라면 LP2로 분류할 수 있겠다.

이 책에서 다루는 MAP-MRF Framework는 다음과 같다.

1. LP1-LP4 분류에 따라 적절한 mapping f를 결정한다.
2. Posterior energy를 계산한다.
3. MAP solution을 계산한다.

여기서 2번의 posterior energy 계산은 아래와 같이 수행한다.

1. Sites $ \mathcal{S} $의 neighborhood system $ \mathcal{N} $ 을 정의하고, 그 $ \mathcal{N} $의 set of cliques $ \mathcal{C} $를 정의한다.
2. Prior clique potentials $ V\_c\left( f \right) $를 정의하여 $U \left( f \right)$를 계산한다.
3. Likelihood energy $ U \left( d \\ \vert \\ f \right) $를 계산한다.
4. $U \left( f \right)$ 와 $ U \left( d \\ \vert \\ f \right) $ 를 더해 $ U \left( f \\ \vert \\ d \right) $를 계산한다.

MAP은 Maximum a posterior 의 준말로, 사후 확률 최대화의 의미이다. 베이즈 정리를 기반으로, Bayes risk를 최소화하는 것을 목표로 한다. Bayes risk는 아래 수식으로 표현된다.

\begin{equation}
  \displaylines
  {
    R \left( f^{\ast} \right) = \int\_{f \in \mathbb{F}}{C \left( f ^{\ast} , f \right) P \left( f \vert d \right) df }
  }
  \label{eq:eq03}
\end{equation}

여기서 $f$는 label, $f ^{\ast} $는 truth, $d$는 관측값observation, $C \left( f ^{\ast} , f \right)$는 cost function, 그리고 $P \left( f \vert d \right)$는 사후 분포posterior distribution이다.

Cost function은 quadratic cost function, 그리고 $ \delta \left( 0-1 \right) $ function 두 가지가 주로 사용된다. 각각 아래와 같다.

\begin{equation}
  \displaylines
  {
    C \left( f ^{\ast} , f \right) = \Vert f ^\ast - f \Vert ^2
  }
  \label{eq:eq04}
\end{equation}

\begin{equation}
  \displaylines
  {
    C \left( f ^{\ast} , f \right) = \left\\{ \begin{array}{cl} 0 & \mbox{if} \\ \\ \\ \Vert f^\ast - f \Vert \leq \delta \\\ 1 & \mbox{otherwise} \end{array} \right.
  }
  \label{eq:eq05}
\end{equation}

$P \left( f \vert d \right)$는 Bayes rule에 의해 아래와 같이 정리할 수 있다.

\begin{equation}
  \displaylines
  {
    P \left( f \vert d \right) = \frac{p \left( d \vert f \right) P\left( f \right) }{p \left( d \right)}
  }
  \label{eq:eq06}
\end{equation}

$ P\left( f \right) $는 probability of labelings, $ p \left( d \vert f \right) $는 conditional p.d.f. of the observation d, 그리고 $ p\left( d \right) $는 density of d로, d가 given이면 constant이다.

두 가지 cost function 각각에 대한 상세한 증명은 책을 찾아보기로 하고, 위 Bayes rule에 따라 minimal risk estimate는 다음과 같다.

\begin{equation}
  \displaylines
  {
    \begin{array}{ccl}
      f^\ast &=& \mbox{arg} \max\limits\_{f \in \mathbb{F}} P \left( f \\ \vert \\ d \right) \\\&=& \mbox{arg} \max\limits\_{f \in \mathbb{F}} \left\\{ p \left( d \\ \vert \\ f \right) P \left( f \right) \right\\}
    \end{array}
  }
  \label{eq:eq07}
\end{equation}

## Neighborhood system and cliques

Neighborhood system은 말 그대로 어떤 site의 성분에 대해 이웃한 system을 말한다. 예를 들어, 어떤 반경을 기반으로 한 neighborhood system은 아래와 같이 쓸 수 있다.

\begin{equation}
  \displaylines
  {
    \mathcal{N}\_i = \left\\{ i' \in \mathcal{S} \\ \vert \\ \left[ \text{dist(pixel\_{i'}, pixel\_{i})} \leq r, \\ i' \neq i \right] \right\\}
  }
  \label{eq:eq08}
\end{equation}

Clique는 subset of sites in $ \mathcal{S} $로 정의되고, 보통 single-site $ c=\\{i\\} $, pair-site $ c=\\{i, i'\\} $, 또는 triple-site $ c=\\{i, i', i''\\} $, 등이 있다. 각각 아래와 같이 정의된다.

\begin{equation}
  \displaylines
  {
    \mathcal{C}_1 = \left\\{ i \\ \vert \\ i \in \mathcal{S} \right\\}
  }
  \label{eq:eq09}
\end{equation}

\begin{equation}
  \displaylines
  {
    \mathcal{C}_2 = \left\\{ \left\\{ i, i' \right\\} \\ \vert \\ i' \in \mathcal{N}\_{i}, i \in \mathcal{S} \right\\}
  }
  \label{eq:eq10}
\end{equation}

\begin{equation}
  \displaylines
  {
    \mathcal{C}_3 = \left\\{ \left\\{ i, i', i'' \right\\} \\ \vert \\ i, i', i'' \in \mathcal{S} \\ \text{are in neighbors to one another} \right\\}
  }
  \label{eq:eq11}
\end{equation}

중요한 것은 clique는 ordered, 즉 순서가 있다. 다시 말해 $ \\{ i, i' \\} $와 $ \\{ i', i \\} $는 다르다는 것이다.

책 그림 2.1 과 2.2 에 각각 regular 및 irregular sites에 대해 neighborhood와 clique의 예시 이미지가 있으므로 참고해보도록 하자.

## Markov Random Fields

$ \mathcal{F} $는 $\mathcal{S}$에서 $\mathcal{N}$에 대해 if and only if 다음 두 조건, positivity와 Markovianity, 을 만족하는 경우 Markov random field라고 할 수 있다.

Positivity는 random field이므로 가져야 할 조건이다. Markovianity는 어떤 site에서의 label은 그 neighbor에 의해서만 영향을 받는다는 것이다. Positivity와 Markovianity를 수식으로 표현하면 아래와 같다.

1. $ P \left( f \right) > 0, \\ \\ \forall f \in \mathbb{F} $
2. $ P \left( f\_i \\ \vert \\ f\_{\mathcal{S}-\\{i\\} } \right) = P\left( f\_i \\ \vert \\ f\_{\mathcal{N}\_i} \right) $

$ \mathcal{S}-\\{i\\} $은 set difference, $ f\_{\mathcal{S}-\\{i\\}} $는 $ \mathcal{S}-\\{i\\} $에서의 set of labels, 그리고 $f\_{\mathcal{N}\_i}$는 $i$에 neighbor인 sites의 set of labels이다.

수식으로 보면, site $i$의 label은 $i$를 제외한 site 전체에 의한 확률과, $i$와 neighbor한 sites에 의한 확률이 동일하다는 것이다. 즉, site $i$의 label은 neighbor한 site에 의해서만 영향을 받는다.

## Gibbs Random Fields

Gibbs random field, GRF는 a set of random variables $F$가 $\mathcal{S}$에서 $\mathcal{N}$에 대해 Gibbs distribution을 만족할 때, $F$는 GRF라고 말할 수 있다.

Gibbs distribution은 아래 식과 같다.

\begin{equation}
  \displaylines
  {
    P(f) = Z^{-1} \times e^{-\frac{1}{T}U(f)}
  }
  \label{eq:eq12}
\end{equation}

여기서 $Z$는 normalizing constant로, partition function이라고도 하며, 아래와 같이 계산할 수 있다.

\begin{equation}
  \displaylines
  {
    P(f) = \sum\_{f \in \mathbb{F}} e^{-\frac{1}{T}U(f)}
  }
  \label{eq:eq13}
\end{equation}

$T$는 temperature인데, 열역학에서는 의미가 있는 값이었지만 여기서는 별도로 값을 넣지 않는 한 1로 고정한다. $U(f)$는 energy function으로, 모든 가능한 cliques $\mathcal{C}$에 대해 clique potentials $V\_{c}(f)$의 총합으로 계산한다. 수식으로는 아래와 같이 표현한다.

\begin{equation}
  \displaylines
  {
    U(f) = \sum\_{c \in \mathcal{C}}{V\_{c}(f)}
  }
  \label{eq:eq14}
\end{equation}

이 $U(f)$를 계산하는 것에 대해 책에서 식 (2.16-19)을 같이 봐도 좋을 듯 하다. Homogeneous한 cliques에 대해 pair-site까지 수식을 정리한 것이다.

## Markov-Gibbs Equivalence

앞서 다룬 MRF는 local property고, GRF는 global property이다. 그런데 이 둘은 서로 동등한 property라는 것이 증명되었다고 한다.

상세한 증명은 (Besag 1974), (Moussouris 1974) and (Kindermann and Snell 1980)에 맡기자.

그렇다면 그 의미가 뭐냐, clique potential functions $V\_c (f)$를 결정함으로써 joint probability $P(f)$를 결정할 수 있고, 그로부터 label 사이의 interaction을 알 수 있다는 것이다.

그래서 책의 후반부에서는 그 potential functions를 어떻게 결정하고 계산하는지에 대해 다룬다. 이 포스팅에서는 본인의 연구 목표, sonar image 즉 greyscale image에서의 segmentation, 을 위해 간단한 Gaussian distribution model과, optimization을 위한 ICM에 대해 마저 공부하기로 한다.

## Auto-models and Multi-level Logistic Model

Clique를 pair까지만 생각하면 에너지 $ U(f) $는 아래와 같이 쓸 수 있다.

\begin{equation}
  \displaylines
  {
    U(f) = \sum\_{i \in \mathcal{S}}{V\_{1}(f\_i)} + \sum\_{i \in \mathcal{S}}{  \sum\_{i' \in \mathcal{N}\_i}{ V\_{2}(f\_i, f\_{i'}) }  }
  }
  \label{eq:eq15}
\end{equation}

여기서 $ V\_{1}(f\_{i}) = f\_{i}G\_{i}(f\_{i})$, $V\_2 (f\_i , f\_{i'} = \beta\_{i,i'} f\_i f\_{i'})$이라고 하면 아래와 같이 다시 정리할 수 있다. 여기서 $G\_i(\cdot)$은 임의의 함수이고, $\beta\_{i, i'}$은 $i$와 $i'$ 사이의 pair-site interaction을 반영하는 상수이다.

\begin{equation}
  \displaylines
  {
    U(f) = \sum\_{i \in \mathcal{S}}{ f\_{i}G\_{i}(f\_{i}) } + \sum\_{i \in \mathcal{S}}{  \sum\_{i' \in \mathcal{N}\_i}{ \beta\_{i,i'} f\_i f\_{i'} }  }
  }
  \label{eq:eq16}
\end{equation}

책의 (2.44)번 수식으로 넘어가면, 위 식에서 single-site cliques의 상수를 $\alpha$, pair-site cliques의 상수를 $\beta$라고 두면 $V\_2(f\_i , f\_{i'})$을 아래와 같이 쓸 수 있다.

\begin{equation}
  \displaylines
  {
      V\_2(f\_i , f\_{i'}) = \left \\{ \begin{array}{cl} \beta\_c & \text{if sites on clique} \\ \\{ i, i' \\} = c \in \mathcal{C}\_2 \\ \text{have the same label} \\\ -\beta\_c & \text{otherwise} \end{array} \right.
  }
  \label{eq:eq17}
\end{equation}

대략적으로 $\beta$는 pair-site에서의 energy에 영향을 미치는 값이라고 생각해 볼 수 있겠다.

## Iterated Conditional Modes

Core idea는, full joint probability $ P(f \\ \vert \\ d) $를 최대화하는 대신, 각각의 variable $ f\_i $ 에 대해 local conditional probabilities $P( f\_i \\ \vert \\ d, \\ f\_{S-\\{i\\} } ) $​을 반복 계산하여 최대화하는 것이다.

2 가지 가정이 필요하다.

1. $d\_1 , \cdots , d\_m$ 는 $f$에 대해 conditionally independent하고, 각 $d\_i$ 는 $f\_i$에만 dependent한 같은 conditional density function $ p ( d\_i \vert f\_i ) $을 가진다.
2. 앞서 확인한 Markovianity

이를 각각 수식으로 표현하면 아래와 같다.

\begin{equation}
  \displaylines
  {
    p \left( d \\ \vert \\ f \right) = \prod\_{i}{ p \left( d\_i \\ \vert f\_i \right) }
  }
  \label{eq:eq18}
\end{equation}

\begin{equation}
  \displaylines
  {
    P \left( f\_i \\ \vert \\ f\_{\mathcal{S}-\\{i\\} } \right) = P\left( f\_i \\ \vert \\ f\_{\mathcal{N}\_i} \right)
  }
  \label{eq:eq19}
\end{equation}

위 두 가정과 베이즈 룰을 사용하면 아래와 같이 쓸 수 있다.

\begin{equation}
  \displaylines
  {
    P( f\_i \\ \vert \\ d , \\ f\_{\mathcal{S}-\\{i\\}}) \propto p( d\_i \\ \vert \\ f\_i ) P( f\_i \\ \vert \\ f\_{\mathcal{N}\_i})
  }
  \label{eq:eq20}
\end{equation}

식 \eqref{eq:eq20}을 최대화한다는 것은 해당하는 posterior potential을 최소화한다는 것과 같으므로, 아래와 같이 쓸 수 있다.

\begin{equation}
  \displaylines
  {
    f\_i^{(k+1)} \leftarrow \text{arg} \min\limits\_{f\_i} \sum\_{i' \in \mathcal{N}\_i} V( f\_i \\ \vert \\ f\_{i'}^{(k)}) + V( d\_i \\ \vert \\ f\_i )
  }
  \label{eq:eq21}
\end{equation}


상세한 내용은 MATLAB MRF Segmentation 코드<sup>[2](#footnote_2)</sup>를 확인하며 마저 적어보자.

# 생각


# Todo

* MATLAB 코드 실행 및 각 변수 확인

---

# 참고문헌

*책 ref.

<a name="footnote_2">2</a>: <a href = "https://kr.mathworks.com/matlabcentral/fileexchange/33592-image-segmentation-based-on-markov-random-fields">https://kr.mathworks.com/matlabcentral/fileexchange/33592-image-segmentation-based-on-markov-random-fields</a>

