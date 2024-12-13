---
title: "Robust sonar-based underwater object recognition against angle-of-view variation"
excerpt: "연구실 논문 공부"
thumbnail: study_notes/lab-paper/241213_00.png
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/241213_00.png">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/241213_00.png">
  </a>
  <figcaption>
  Fig.1 Robust sonar-based underwater object recognition against angle-of-view variation
  </figcaption>
</figure>

IEEE Sensors Journal

Date of Publication: 02 November 2015

# 내용

시뮬레이션 데이터로 생성된 템플릿과 소나 데이터를 2D correlation으로 비교하여 underwater landmark를 인식하는 연구이다.

2D correlation과 살짝 다른 점은, 템플릿 이미지 각각의 column에 대해 1D correlation을 먼저 수행하고 maximum value를 계산해 합쳤다는 점이다. 이 점으로 앞서 리뷰했던 논문<sup>[2](#footnote_1)</sup> 에서는 소나가 움직이며 데이터를 얻을 경우 sawtooth pattern이 생기는 것에 대해 좀 더 robust한 게 아니었을까, 하는 생각이 든다.

Abrupt peak나 random distribution의 경우에도 히스토그램으로(~mean filter) 필터링하여 actual signal을 구분한다.

실험으로 증명되었다.

---

# 참고문헌

H. Cho, J. Gu and S. -C. Yu, "Robust Sonar-Based Underwater Object Recognition Against Angle-of-View Variation," in IEEE Sensors Journal, vol. 16, no. 4, pp. 1013-1025, Feb.15, 2016, doi: 10.1109/JSEN.2015.2496945.

<a name="footnote_1">2</a> Cho, H., Gu, J., Joe, H. et al. Acoustic beam profile-based rapid underwater object detection for an imaging sonar. J Mar Sci Technol 20, 180–197 (2015). https://doi.org/10.1007/s00773-014-0294-x