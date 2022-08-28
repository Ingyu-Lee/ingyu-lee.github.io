---
title: "An approach to design a high power piezoelectric ultrasonic transducer"
excerpt: "An approach to design a high power piezoelectric ultrasonic transducer"
thumbnail: 999999_category_research_paper_memo_00.jpg
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
  - Mechanical Engineering
  - Ultrasonic Transducers
toc: true
last_modified_at: 2021-08-02T18:30:00
---

<figure class="align-center" style="width: 600px">
  <a href="/assets/images/210721_research_paper_memo_00_00.jpg">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/210802_research_paper_memo_01_00.jpg" alt="">
  </a>
</figure>

본 논문은 high power piezoelectric ultrasonic transducer, 그 중에서도 Langevin tranducer의 설계 과정에 대해 상세히 다룬 논문이다. 본 논문을 통해 설계 과정에 대해 잘 모르던 부분을 알게 되어 이 글에선 the transducer의 설계에 관해 상세한 내용을 메모하려 한다.

# 1-D vib. assumption

먼저 1-D longitudinal vibration을 가정한다. 즉, lateral pressure on the transducer가 없으며, 축을 따라 sinusoidal longitudinal plane wave가 전달된다고 가정한다. 이를 위해선 transducer의 max. diameter가 quarter wavelength보다 작아야 하고(wave prop. speed는 \[ c = \sqrt{Y/\rho} \] 로 가정한다), 공기의 acoustic impedance는 0으로 가정하여 transducer의 전체 길이가 standing wave generation에 적합하도록, 즉 diameter 대비 length ratio 가 1-D vib. 가정을 만족할 수 있어야 한다. 여기서 fillet과 chamfer의 영향은 무시한다.

# Stress calculation

필요한 pre-stress의 크기와 max. voltage를 구하기 위해 본 논문에선 piezoelectric  piezoelectric constitutive eqn. 과 transducer에서 이용할 piezoelectric material의 물성을 통해 그 크기를 구한다. Max. efficiency를 위해선 nodal plane이 piezo. stack에 있는 것이 유리한데 piezo. material의 fatigue limit(고체역학에서 fatigue 배울 때의 그 ㄴ자형 그래프의 그것)은 compressive fatigue limit의 크기가 tensile fatigue limit의 크기보다 훨씬 크기 때문에 prestress를 가하는 것이 operation vol. range면에서 더 이득을 볼 수 있다.

Nodal plane, 즉 displacement가 0이고 stress가 max. 이 되는 곳에서의 dynamic stress 크기는 \[ T\_{max} = Y \zeta\_{max} k \] 로 표현할 수 있다. 여기서 \[T\]는 stress, \[Y\]는 Young's modulus, \[\zeta\]는 displacement, 그리고 \[k\]는 wave number 이다. 즉, piezo. material의 max. displacement의 크기와 material properties를 알 수 있으면 dynaimc stress를 구할 수 있고, safety factor \[ \beta = 2 \]를 통해 필요한 prestress의 크기를 계산할 수 있다(safety factor의 크기는 본문에서 high freq. 에서의 durable life를 위해 추천되는 값이라고 함).

# Material selection for backing and matching layer

Acoustic impedance 계산을 통해 필요한 impedance를 계산하여 그 material을 찾는데, 필자가 연구할 wide-band airborne transducer와 본 논문의 single-freq. 이고 수중에서 작동할 transducer는 그 방향성이 다르기 때문에 그대로 적용하기는 어려울 것으로 보인다. 본 논문에선 이 부분에서 10, 16, 17, 18 번 ref. 를 참조했는데, 10, 16번은 textbook이고, matching layer에 구멍을 내어 그 impedance를 줄이는 것에 관한 내용이나 material을 stainless steel에서 aluminum과 titanium으로 바꾼 것으로 진동 크기가 증가한 것에 관해 다룬 것으로 보이는 17, 18번 ref. 는 특허로 보인다. 빠르게 시간을 내어서 훑어 보기로 하자.

# Lengths of the backing, piezoelectric, matching layer

논문에서 21, 22, 23 번 ref. 를 가져왔는데 conference proceedings이거나 원 자료를 찾을 수 없어 그 진위를 파악하기 어렵다. Power ultrasonics나 Transducers and Arrays for Underwater Sound 책을 찾아보자. 또, 본 논문에서 나오는 radiating face diameter가 최소 \[2.5 \lambda\_w/4\] 여야 한단 부분도 그러한 ultrasonic transducer관련된 textbooks에서 나올 수 있다. Bolted joint에서의 uniform stress distribution에 관해선 기계공학설계에서 다뤘던 교과서를 찾아보자.

# Central Bolt

본 논문에선 material이 서로 다를 때의 length of the bolt의 수식에 대해서도 나와 있으므로 이를 참고하면 좋을 것 같다.

# Compensative inductance

Piezoelectric material stack의 capacity에 의한 reactive current를 보상해주기 위해 필요한 inductance \[L\_{par}\]은 다음과 같이 계산할 수 있다.

\begin{equation}
  L\_{\text{par}} = \frac{1}{4\pi^2f\_{\text{s}}^2C\_0}
\end{equation}

# Selection of piezoceramics and number of the piezoceramics

원하는 output power를 얻기 위해 필요한 압전물질의 종류와 스택의 개수를 결정하기 위해 본 논문에선 각 piezoceramic의 단위면적당power(단위는 \[\text{W/cm}^2\])를 확인하여 목표 output power를 맞추었다. 단, 이를 내 연구에 바로 적용하기엔 damping이 크게 차이나기 때문에 어려울 것으로 보인다.

# Stress in the central bolt

앞서 계산한 prestress에 piezo. ceramics와 bolt의 면적비로 bolt에 가해지는 static stress를 계산하고, 앞서 dynamic stress 계산한 것과 동일하게 bolt의 dynamic stress를 계산한다. 면적 차이가 클 경우 그만큼 static stress 크기가 커지기 때문에 이를 계산해야 bolt의 fatigue를 막을 수 있을 것으로 보인다.

# Measurement of acoustic impedance of materials

질량과 부피 측정을 통해 acous. imped. 측정을 한다. 내 연구에서도 측정해야할 필요 있을지도?

# Applying the prestress

두 가지 방법이 있다. Torque meter 사용, 그리고 charge 측정이다. 전자의 경우 not a reliable method라는데 그 이유는 적혀있지 않다. 개인적인 생각으로는 friction coefficient가 ref. value와 다를 수 있어서 그런 게 아닐까 추측한다. 후자의 경우 병렬로 \[ \mu F \] capacitor를 연결한다. 본 논문에서 설정한 prestress를 가할 경우 \[ \mu C \]단위의 charge가 생기는데 이 값이 그대로 PZT에 charged되면 kV 단위의 전위를 가지기 때문에 이 과정에서 위험할 수 있으며, discharge되는 과정에서 prestress를 잃을 수 있으며, 그리고 charge가 매우 낮기 때문에 voltimeter가 제대로 측정하기 어렵다. 본 논문에선 원하는 prestress를 가했을때 약 1V가 측정되도록 capacitor의 크기를 결정하여 연결하였다.

또한 해당 방법에 교과서 ref.가 달린것을 보니 이미 Langevin transducer 조립에서 잘 쓰이는 방법으로 보이므로 앞서 언급했던 교과서를 빠르게 훑어봐야겠다.


# 이후 목표 정리

1. 교과서에서 charge measure 관련 찾아보기
2. 수업자료 또는 교과서에서 reactive current 보상 관련해 찾아보기
3. Material selection 관련해서 Al. 과 Ti., 그리고 St303, St304, Al7075-T6에 관한 17, 18, 25, 26 번 ref. 찾아보기
4. 2.5 \[\lambda\_w/4\], 그리고 bolted joint stress distribution 관련 교과서 찾아보기

- - -
# 참고문헌

Abdullah, A., Shahini, M., & Pak, A. (2009). An approach to design a high power piezoelectric ultrasonic transducer. Journal of Electroceramics, 22(4), 369-382. doi:10.1007/s10832-007-9408-8
