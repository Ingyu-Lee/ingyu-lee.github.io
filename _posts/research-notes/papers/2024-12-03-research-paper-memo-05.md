---
title: "On-Site Calibration-Based Estimation Method of Forward Seabed Elevation Using Forward Scan Sonar"
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
  Fig.1 On-Site Calibration-Based Estimation Method of Forward Seabed Elevation Using Forward Scan Sonar
  </figcaption>
</figure>

IEEE Sensors Journal

Date of Publication: 23 May 2019

# 내용

Forward looking sonar에서 틸트 방향 빔폭에 의한 ambiguity에 대해서, flat한 seabed에 대해 signal intensity-tilt angle 그래프에서 추세선을 Gaussian distribution으로 잡아, 그 intensity와 deviation을 function of range로 mapping하는 연구이다.

그 결과는 대체로 추세선은 비슷하며, 각도가 해저면에 수직할수록 그 intensity가 잘 맞는 편이고, 각도가 작아질수록 실험 intensity가 작은 편이다.

물체가 있는 경우 crosstalk에 의한 영향이 있는 편이다.

# 생각

Gaussian distribution 대신 Lambertian diffusion을 사용하고, azimuth/theta direction 각각에 beam pattern을 적용해보는건 어떨까. Azimuth angle에 대해선 제조사로부터 주어지는데 theta 방향으로는 한번 문의해봐야 할 필요성이 있다.

# Todo

* Azimuth angle에 대한 beam pattern 확인

* Theta angle에 대한 beam pattern 문의

---

# 참고문헌

J. Pyo, H. Cho and S. -C. Yu, "On-Site Calibration-Based Estimation Method of Forward Seabed Elevation Using Forward Scan Sonar," in IEEE Sensors Journal, vol. 19, no. 19, pp. 8832-8844, 1 Oct.1, 2019, doi: 10.1109/JSEN.2019.2918512.