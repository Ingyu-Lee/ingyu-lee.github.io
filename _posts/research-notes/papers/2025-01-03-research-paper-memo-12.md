---
title: "A New Radiometric Correction Method for Side-Scan Sonar Images in Consideration of Seabed Sediment Variation"
excerpt: "논문 공부"
thumbnail: study_notes/lab-paper/241231_00.png
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/241231_00.png">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/241231_00.png">
  </a>
  <figcaption>
  Fig.1 A New Radiometric Correction Method for Side-Scan Sonar Images in Consideration of Seabed Sediment Variation
  </figcaption>
</figure>

Remote Sens. 2017, 9(6), 575; https://doi.org/10.3390/rs9060575

Submission received: 12 April 2017 / Revised: 28 May 2017 / Accepted: 6 June 2017 / Published: 8 June 2017

TVG, 빔패턴 등 외에도 sediment까지 고려하여 signal distortion correction 수행 후 unsupervised sediment classification을 수행하는 연구

# 내용

## Related works

<div class="tex2jax_ignore">
Signal compensation 관련: [16] [7,17] [9, 10, 14, 15]

[15]에서 beam pattern prediction 관련 내용이 있다는 것 같음

[12]에서 impedance와 incident angle에 따른 angular response 다루는 것 같음
</div>

## Combined angular related effect

Beam pattern과 backscatter angle을 합쳐서 고려

본문 Fig. 7 을 보면, TVG로 absorption 영향 제거하고 z-score normalization하면, ping id, 즉 시간에 따라 그림 그래프의 경향이 매우 비슷하다는 것 확인 가능
<br />*flat한 해저면을 따라 스캔해서 angle 영향이 단순 intensity에만 영향 주는 게 아닌지

## k-means++

Sediment classification을 위한 iterative 하게 k-means++를 수행한다.

cluster의 비율과, cluster의 비율 크기를 비교해 k의 숫자를 조정

## Radiometric Correction

Flat한 바닥면의, 같은 sediment에 대해, n개의 데이터를 평균내어 angle-BS curve(ABC)를 계산한다.

논문 본문의 "4.Process of Radiometric Distortion Correction for SSS Images" 프로세스를 참고하자.

## Experiments

실험으로 증명되었다.

---

# 참고문헌

J. Zhao, J. Yan, H. Zhang, and J. Meng, ‘A New Radiometric Correction Method for Side-Scan Sonar Images in Consideration of Seabed Sediment Variation’, Remote Sensing, vol. 9, no. 6, 2017.