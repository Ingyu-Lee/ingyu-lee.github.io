---
title: "Unidimensional Modeling of Multi-Layered Piezoelectric Transducer Structures"
excerpt: "Unidimensional Modeling of Multi-Layered Piezoelectric Transducer Structures"
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
last_modified_at: 2021-09-01T18:30:00
---

<figure class="align-center" style="width: 600px">
  <a href="/assets/images/210901_research_paper_memo_02_00.jpg">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/210901_research_paper_memo_02_00.jpg" alt="">
  </a>
</figure>

본 논문은 multi-layered piezoelectric transducer의 unidimensional modeling에 관해, 그리고 실제 실험을 통해 실제 결과와 모델이 어떻게 다를 수 있는 지에 관해 다룬 논문이다. 본 논문을 통해 알게 된 1-D piezoelectric driving section modeling, 그리고 electric circuit 관점에서 본 multi-layer 구조의 단점, 그리고 wire에 대해서 메모하려 한다.

# 본 논문의 목적

Laminated piezoelectric transducer의 장점은 잘 알려져 있으나, 그 structure의 bondline, electrode, 그리고 다양한 layer는 설계를 복잡하게 만들고 resonance freq. 를 예측하기 어렵게 한다. 이에 본 논문에선 active layer와 inactive layer를 모두 다룰 수 있는 formulation을 만들고, bondline과 PCB를 포함한 structure에 대해 계산 상의 TVR과 실험에서의 TVR을 비교한다.

# PVDF(polyvinylidene fluoride)의 특징

* Poor electromechanical efficiency
* Low dielectric constant
* Available film thickness is less than 110 um, due to poling difficulties
* Using res. freq: high freq
* Using broadband: low freq
* High flexibility

# Formulation

1. Piezoelectric constitutive eqn. 두 개를 substitution
2. 1 의 결과인 wave eqn. 을 Laplace transform으로 변환, gen. sol. 도출
3. Elec. disp. 와 charge 간 관계식과 2. 의 disp. 의 gen. sol. 을 piezo. constitutive eqn. 에 넣어서 force를 gen. sol. 과 charge의 식으로 표현
4. 마찬가지로 piezo. constitutive eqn. 의 electrical part도 voltage를 gen. sol. 과 charge에 관한 식으로 표현
5. Wave eqn.의 gen. sol. 의 coefficient를 각각 forward/backward traveling waves of force로, 원 논문 (12) 및 (13) 식으로 표현하여 대입
6. 5 의 결과로 각 layer에 대해 forward force, backward force 그리고 voltage 표현
7. Laminated structure의 total charge는 각 layer의 charge의 합과 같으므로 Thevenin equiv. volt. 를 Thevenin equiv. cap., 각 layer의 cap., 그리고 각 layer의 volt. 로 표현
8. 7 식의 각 layer의 cap.를 6. 식의 volt. 표현식의 cap. 을 이용해 대입, 그럼 전체 volt.(=Thevenin equiv. volt.)를 forward force, backward force, Thevenin charge와 Thevenin cap.로 표현할 수 있음
9. 각 layer의 charge 표현식을 forward-force wave, backward-force wave 식에 대입
10. 8 의 식과 Thevenin volt. 와 Thevenin output impedance 간 관계를 통해 Thevenin volt. 식 유도 가능

결론적으로, forward-force wave, backward-force wave, 그리고 total volt. 수식을 유도할 수 있다.

# Performance accessment

## Impedance issue of multi-layered transducer

* Volt. source를 ideal source로 하면 single-layer와 double-layer 사이에 6 dB 차이가 나지만, \[R\_{\text{OUT}}\]을 고려하면 performance 차이 크게 없음
* 이는 multi-layered일 수록 capacitance가 작아지므로 그만큼 transducer에 걸리는 volt. 가 작아져서 생기는 현상
* 즉, 단순히 layer를 늘리는 것만이 아닌 volt. source와의 elec. impedance matching 또한 고려해야 함

## Effect on freq. response of bondline, and PCB

* 논문 그래프에선 첫번째 공진을 primary thickness mode, 두번째 공진을 first harmonic resonance로 칭함. 1-3 transducer라서 그런 것으로 보임
* Bondline이 두꺼울수록 prim. thickness mode의 freq와 strength는 낮아짐, first harmonic resonance또한 마찬가지
* PCB의 경우 first harmonic resonance는 오히려 strength가 slightly 커지는 효과 보임, 저자는 interface와 active layer가 비슷한 acoustic impedance를 가질 경우 공진에서 thickness는 큰 영향 없을 것으로 생각

## Transmission characteristics

* Near-field transient response를 측정하여 TVR를 계산
* Transient response를 보는 이유는 desired freq에서 보다 빨리 볼 수 있어서?
* Near-field 에서 보는 이유는 SNR이 더 높게 나오니 noise 영향 무시할 수 있어서?
* TVR 계산식 확인 필요
* Cable의 영향 - low freq. 에선 capacitive한, high freq.에선 inductive한 chracteristic 가짐
* Bondline의 두께를 active layer(PZT, PVDF)의 특정 비율(n %)로 고정하면 sensitivity는 layer수에 비례, resonance freq.는 layer 수와 independent하고 constant함
* Bondline 두께가 두꺼울수록 resonance freq.는 작아지긴 하지만 이건 bondline때문에 길이가 길어져서 그런 건 아님, 계산 상 크게 다름


# 이후 목표 정리

1. 위 formulation 기존 내가 한거랑 차이점 생각하고 바로 대입할수있는지 생각
2. TVR 계산식 확인

- - -
# 참고문헌

Powell, D. J., Hayward, G., & Ting, R. Y. (1998). Unidimensional modeling of multi-layered piezoelectric transducer structures. IEEE Transactions on Ultrasonics, Ferroelectrics, and Frequency Control, 45(3), 667-677. doi:10.1109/58.677611
