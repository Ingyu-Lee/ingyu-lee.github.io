---
title: "Analysis of the sandwich piezoelectric ultrasonic transducer in coupled vibration"
excerpt: "Analysis of the sandwich piezoelectric ultrasonic transducer in coupled vibration"
thumbnail: 999999_category_research_paper_memo_00.jpg
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
last_modified_at: 2021-07-21T21:24:00
---

<figure class="align-center" style="width: 600px">
  <a href="/assets/images/210721_research_paper_memo_00_00.jpg">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/210721_research_paper_memo_00_00.jpg" alt="">
  </a>
</figure>

본 논문에선 길이 대비 반경이 두꺼운 Langevin transducer에 대해 resonance frequency를 analytic하게 예측하는 방법에 대해 다룬다. Length와 radius가 slender rod condition, 즉 \[ L > \lambda / 4 \]를 만족하지 않으면 Langevin transducer는 1-D vibration으로 가정할 수 없다. 이에 본 논문에서는 mechanical coupling coefficient를 통해 각 metal mass 와 piezoelectric ceramic의 radial resonance frequency equation, 그리고 metal mass의 longitudinal resonance frequency equation 총 세 수식을 통해 fundamental mode를 계산한다.

단, 본 논문에선 mechanical coupling coefficient의 계산 방법은 나오지 않았다. radial 과 transverse vibration에 대한 mechanical coupling coefficient인 것 같은데, 저자의 이전 논문을 찾아봐야 할 것으로 보인다.

또한, 수식이 복잡하여 quarter wavelength vibrator이고 좌우대칭 형태로 가정하여 계산하였다.

본 논문을 내 연구에 적용하기엔 이전 논문을 찾아봐야 하며, 좌우대칭이 아닌 형태에 대해선 좀 더 복잡할 해당 수식들에 대해 solver를 어떻게 적용해야 할 지 생각해 보아야 한다.

- - -
# 참고문헌

Lin, S. Y. (2005). Analysis of the sandwich piezoelectric ultrasonic transducer in coupled vibration. Journal of the Acoustical Society of America, 117(2), 653-661. doi:10.1121/1.1849960
