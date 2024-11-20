---
title: "Multi-frequency Backscatter Variations for Classification of Mine-like Targets from Low-resolution Sonar Data"
excerpt: "논문 공부"
thumbnail: study_notes/lab-paper/241120_00.png
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/241120_00.png">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/241120_00.png">
  </a>
  <figcaption>
  Fig.1 Multi-frequency Backscatter Variations for Classification of Mine-like Targets from Low-resolution Sonar Data
  </figcaption>
</figure>

Proceedings of OCEANS 2005 MTS/IEEE

Date of Conference: 17-23 September 2005

# 내용

연구실에서도 사용하고 있는 Imagenex 881A rotating head sonar의 데이터를 사용하여 low-resolution data에서 유사한 데이터를 구분해내는 연구이다.

features를 뽑아낸 후 Kohonen layer를 사용한 NN를 통해 classification을 수행한다. 여기서 features는 신호의 peak value, half-power width/length(-3 dB), quarter-power width/length(-6 dB)이다.

실험으로 검증되었다.

# 생각

결과가 명확하지 않다. 실험 사진도 없을 뿐더러, feature 중 하나인 signal의 peak value는 노이즈가 끼기 쉽고 상황에 따라 크게 바뀔 수 있는 값인데, 이걸 왜 feature로 잡았는지 잘 모르겠다.

학회논문에 후속연구도 없을뿐더러 인용수도 적다. 이 연구는 크게 신경쓰지 않아도 될 것 같다.

---

# 참고문헌

J. R. Stack, G. Dobeck and C. Bernstein, "Multi-frequency backscatter variations for classification of mine-like targets from low-resolution sonar data," Proceedings of OCEANS 2005 MTS/IEEE, Washington, DC, USA, 2005, pp. 218-222 Vol. 1, doi: 10.1109/OCEANS.2005.1639765.