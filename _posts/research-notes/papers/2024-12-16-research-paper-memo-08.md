---
title: "Segmentation of Sidescan Sonar Imagery Using Markov Random Fields and Extreme Learning Machine"
excerpt: "논문 공부"
thumbnail: study_notes/lab-paper/241216_00.png
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/241216_00.png">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/241216_00.png">
  </a>
  <figcaption>
  Fig.1 Segmentation of Sidescan Sonar Imagery Using Markov Random Fields and Extreme Learning Machine
  </figcaption>
</figure>

IEEE Journal of Oceanic Engineering

Date of Publication: 18 May 2018

# 내용

일반적으로 MRF의 initial model은 k-means를 활용하는데, 소나 이미지의 노이즈로 인해 k-means classification에는 한계가 있어 extreme learning machine(ELM)을 활용한, 그 중에서도 asimpleensemble ELM(SE-ELM)을 MRF의 init. model로 사용한 연구이다.

<div class="tex2jax_ignore">

SSS image segmentation:

Ref. [2]-[3]: supervised method

Ref. [4]-[5]: unsupervised method

Ref. [9]: MRF 사용

</div>

기본적으로는 k-means 사용하는 MRF는 연산시간 꽤 김, 이 연구에서 사용한 컴퓨터로는 $ 170 \times 270 $ 픽셀 데이터 연산에만 48.21초 걸렸다고 함

결과는 accuracy와 연산 시간으로 구분해 총 다섯 가지 방법, ELM, KELM, SVM, CNN, 그리고 제안하는 SE-ELM, 을 구분하였다.

# 생각

CNN의 경우 이미지 3개를 학습하는데, $ 3 \times 3 $ kernel size로 $130 \times 400$, $70 \times 500$, 그리고 $170 \times 270$ 사이즈 이미지 3 개를 학습한다. 그런데 총 학습 샘플 수를 $ (130 - 3) \times (400 - 3) + ( 70 - 3) \times ( 500 - 3 ) + ( 170 - 3 ) \times ( 270 - 3 ) = 129832 $라고 할 수 있는가?

뭐 결과의 accuracy가 높으니 신경쓰지 않아도 되나 싶긴 하다.

# Todo

* 간단한 CNN 코드 짜두기

* Sonar data에 대해, ground truth data라고 할 만한 3-class data generation하는 방법 생각하기

---

# 참고문헌

Y. Song et al., "Segmentation of Sidescan Sonar Imagery Using Markov Random Fields and Extreme Learning Machine," in IEEE Journal of Oceanic Engineering, vol. 44, no. 2, pp. 502-513, April 2019, doi: 10.1109/JOE.2018.2819278.
