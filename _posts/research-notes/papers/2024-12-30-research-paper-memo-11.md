---
title: "A Gray Scale Correction Method for Side-Scan Sonar Images Considering Rugged Seafloor"
excerpt: "논문 공부"
thumbnail: study_notes/lab-paper/241230_00.png
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/241230_00.png">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/241230_00.png">
  </a>
  <figcaption>
  Fig.1 A Gray Scale Correction Method for Side-Scan Sonar Images Considering Rugged Seafloor
  </figcaption>
</figure>

Published in: IEEE Transactions on Geoscience and Remote Sensing ( Volume: 61) 

Date of Publication: 28 November 2023

DOI: 10.1109/TGRS.2023.3334492

# 내용

SSS

Transmission loss, incident angle, multiplicative attenuation model을 고려

attenuation 방향으로 segment를 나눠 incident angle 관련 factor를 계산

## related works

<div class="tex2jax_ignore">

[7]번 논문: TVG, ping간 intensity 보정, clustering으로 sediment 구분

하지만 clustering 과정은 flat하지 않은 지형에선 그림자때문에 방해됨
<br />*추후에 논문 확인

[11]번 논문: attenuation의 model eqn.의 constant를 curve fitting해서 보정

하지만 연산 시간이 오래 걸림
<br />*추후에 논문 확인

[12-14]번 논문: histogram normalization(=mean filter? 확인필요) 및 nonlinear compensation 활용

</div>

## TVG

$\alpha$는 익숙한 coefficient인데 $a$에 대한 확인 필요

## Incident angle

단순 $ \cos \theta $로 계산

## Segmentation

TVG와 입사각을 합쳐서 $ f(r) $로 치환하고, segmentation을 충분히 잘게 나누었을 경우, $ f(r) $을 식 (9)와 같이 나타낼 수 있다.

다만 여기서는 beam pattern을 고려하지 않았다는 점이 있다.

## Thresholds

Threshold $ c $는 그림자를 제외하고 intensity의 기하평균을 구하기 위해 사용된다.
<br />*기하평균인건 dB가 log scale이라서?

Threshold $ m $은 그림자를 제외하고 intensity를 보정하기 위해 사용된다.

용도를 보면 비슷해 보이지만, 식 (11)과 식 (12)를 보면 구분되어 사용됨을 확인할 수 있다.

$c$ 와 $m$ 은 ref 11번의 SIQEM, entropy, mean gradient, 그리고 gray difference를 비교하여 결정되었다.
<br /> SIQEM은 식 (13-14)를 확인 또는 ref. 확인

## Process

그림 5 를 참조하자.

## Exp. and analysis

비교군인 MGC, MSR, SDR, RCM, MIRA와 제안한 방법에 대해 SIQEM, entropy, mean gradient, 그리고 gray difference를 비교하여 결정되었다.

<div class="tex2jax_ignore">

비교군 방법들은 다음 ref. 를 참조하자: [7] [11] [12] [15] [26]

</div>

# Todo

* TVG 계산식에서 $a$ 확인 필요

* 비교군인 MGC, MSR, SDR, RCM, MIRA에 대해 확인: 코드 있는지와 레퍼런스 논문

* SIQEM ref. 확인해 물리적 의미 확인 및 코드 작성

* 본인 방법 수식 수립 및 이 논문과 비교

---

# 참고문헌

X. Ye, H. Yang, C. Li, Y. Jia, and P. Li, ‘A Gray Scale Correction Method for Side-Scan Sonar Images Based on Retinex’, Remote Sensing, vol. 11, no. 11, 2019.