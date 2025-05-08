---
title: "메모: Computational methods for automatic traffic signs recognition in autonomous driving on road: A systematic review"
excerpt: "논문 인트로 및 컨클루젼 번역기"
thumbnail: study_notes/lab-paper/250508_01.png
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/250508_01.png">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/250508_01.png">
  </a>
  <figcaption>
  Fig.1 Computational methods for automatic traffic signs recognition in autonomous driving on road: A systematic review
  </figcaption>
</figure>

# Introduction

이 리뷰에서는 지난 10년 동안 교통 표지판 감지 및 인식 방법과 알고리즘의 발전을 논의하며, 각 알고리즘의 강점과 약점을 분석하였다. 최근 도로에서의 교통 표지판 인식 기술의 발전은 다양한 주행 시나리오에서 도로 표지판을 정밀하게 감지할 필요성을 강조한다. 또한, 딥러닝 도입 전후의 감지 알고리즘 간의 연관성도 드러냈다.

교통 표지판 인식 기술은 다양한 조건에서 다양한 형태, 크기, 방향 및 외관의 표지판을 식별할 수 있도록 개발되었다. 연구자들은 이러한 과제를 해결하기 위해 여러 알고리즘을 제안하였다. 본 논문에서는 교통 표지판 인식 방법을 전통적 기법, 딥러닝 기반 기법, 하이브리드 기반 기법의 세 가지로 분류하였다.

회귀(regression), 세그멘테이션(segmentation), 하이브리드 기법을 통해 SSD, YOLO, Faster R-CNN, Pixel Aggregation Network, Mask R-CNN 알고리즘이 서로 비교되었다. 결과적으로, 하이브리드 기반 감지 알고리즘이 진양성률(true-positive rate), 오탐률(false-positive rate), 테스트 이미지 수, 정확도 및 처리 시간 측면에서 다른 알고리즘보다 뛰어난 성능을 보였다. 이러한 결과는 하이브리드 방법이 정확하고 효율적인 TSD 시스템을 구축하는 데 잠재력이 있음을 보여주며, 이 분야에서의 추가 연구 가능성을 시사한다.

# Conclusion

이 논문에서는 교통 표지판 감지(TSD) 분야에서 딥러닝의 다양한 응용을 종합적으로 분석하였다. 우리는 회귀(regression), 세그멘테이션(segmentation), 하이브리드 접근 방식의 고유한 장점과 과제를 강조하였다. 연구 결과, 각 접근 방식이 특정 응용 시나리오에 적합하지만, 특히 여러 보완적 전략을 결합한 하이브리드 알고리즘이 복잡하고 동적인 환경에서 TSD 문제를 해결하는 데 있어 상당한 잠재력을 보유하고 있음을 확인했다.

회귀 기반 감지 알고리즘(예: YOLO 및 SSD)은 실시간 성능과 처리 속도가 우수하다. 그러나 복잡한 시나리오에서는 정확도가 다소 떨어진다. 반면, Faster R-CNN과 같은 알고리즘은 정확도 면에서 두드러진 이점을 보이지만, 처리 시간이 길어 높은 정확도가 요구되는 상황에서만 사용해야 한다.

세그멘테이션 기반 기법(예: Pixel Aggregation Network(PAN), Mask R-CNN)은 세부 처리와 경계 인식에서 강점을 보인다. 그러나 대규모 데이터를 처리할 때 계산 복잡도가 높아질 수 있다. 이러한 접근 방식은 복잡한 교통 환경에서 정밀한 경계 식별이 필요한 경우에 적합하다.

하이브리드 알고리즘: 데이터 증강(data augmentation), 전이 학습(transfer learning) 등 딥러닝 향상 기법과 색상 분할(color segmentation), 엣지 검출(edge detection)과 같은 전통적 전처리 기법을 결합하여 차별화된다. 이 조합은 다양한 환경에서 여러 가지 이점을 제공한다.

환경적 복잡성 대응: 전통적인 방법(예: 색상 분할)의 통합은 특정 색상 패턴(예: 교통 표지판)이 있는 시나리오에서 후보 영역을 효율적으로 로컬라이즈하는 데 유용하다. 이를 통해 딥러닝 모델이 복잡한 배경과 다양한 조명 조건에서도 관련 영역에만 집중하여 성능을 향상시킬 수 있다.

검출 강건성 향상: 전이 학습은 ImageNet과 같은 대규모 데이터셋에서 학습된 네트워크의 특징 추출 기능을 활용하여 새로운 작업에 빠르게 적응할 수 있게 한다. 이는 리소스가 제한된 환경에서 모델을 처음부터 학습시키는 것보다 훨씬 효율적이다.

속도와 정확성의 균형: Spatial Attention-based Detection(SAD)과 같은 하이브리드 기법은 회귀 기반 방법의 빠른 반응 속도와 세그멘테이션 기반 접근 방식의 세부 처리 기능을 결합하여, 실시간 검출이 중요한 자율 주행 및 지능형 교통 시스템에 적합한 높은 정확도를 유지하면서도 빠른 처리 속도를 달성할 수 있게 한다.

하이브리드 알고리즘은 회귀 기반 방법의 빠른 응답성과 세그멘테이션 기반 방법의 정밀한 세부 묘사 능력을 모두 활용함으로써 교통 표지판 감지 기술의 미래 발전에 중요한 역할을 할 수 있다.
미래 발전 방향:

향후 TSD 시스템은 알고리즘의 속도, 정확성 및 유연성을 통합하여 동적인 도로 환경에 효과적으로 적응할 수 있는 방향으로 발전할 것이다. 특히 하드웨어의 발전은 TSD 시스템의 실질적인 구현에 중요한 요소로 작용할 것이다. 카메라 해상도, 프레임 속도, 동적 범위와 같은 하드웨어 사양은 특히 악천후나 복잡한 환경에서 교통 표지판의 인식 정확도에 큰 영향을 미친다.

최신 연구에서는 단안 카메라(monocular camera)와 차량 내 카메라의 활용이 교통 표지판 감지의 정확도와 신뢰성을 높이는 데 유망한 결과를 보이고 있다. 이와 같은 기술은 다양한 환경에서의 적응성을 제공할 뿐만 아니라 AR 기반의 방법론을 도입하여 차량 간 협력적인 인식 체계를 구현할 가능성도 보여준다.

또한, 자율 주행 차량에 장착된 GPU 및 AI 가속기와 같은 컴퓨팅 자원의 성능은 실시간으로 딥러닝 모델을 효율적으로 실행하고 지연 시간을 최소화하며 에너지 소비를 최적화하는 데 중요한 역할을 한다.
향후 연구 방향:

기술적 진보 및 통합: LiDAR, 레이더 등 다양한 데이터 소스를 시각 기반 시스템과 결합하여 성능 및 신뢰성을 높이는 연구가 필요하다.

시스템 강건성 및 에너지 효율성: 자율 주행 환경에서의 다양한 조명 조건, 악천후, 가림 현상 등에 효과적으로 대응할 수 있는 강건한 알고리즘 개발이 필수적이다.

지식 전이 및 데이터 효율성: 지역 및 국가별 교통 표지판의 차이를 관리하기 위한 전이 학습 및 도메인 적응 연구가 중요하다.

임베디드 시스템 최적화: 차량 내장 시스템이나 모바일 기기에 탑재할 수 있도록 경량화된 모델 개발이 필요하다.

다국어 표지판 인식: 교통 표지판의 언어적 차이를 인식하고 이를 다국어 텍스트 인식 시스템에 통합하는 연구가 필요하다.

연합 학습: 데이터 프라이버시를 보호하면서도 다양한 지역의 데이터를 효과적으로 학습할 수 있는 분산 학습 기법을 연구할 필요가 있다.

사람-기계 상호작용: TSD 시스템이 운전자에게 직관적이고 유용한 정보를 제공할 수 있도록 사람 중심 설계를 도입하고, 실시간으로 사용자와의 상호작용을 최적화하는 연구도 필요하다.

결론적으로, TSD 분야에서의 연구 및 개발이 지속됨에 따라, 더욱 안전하고 스마트한 교통 시스템 구축에 기여할 보다 진보적이고 효율적인 솔루션이 등장할 것으로 기대된다.

# Memo

Data augmentation에서 color segmentation, edge detection 등의 고전적 방법을 씀

Training data가 부족할 때 효과적

---

# 참고문헌

H. Chen et al., "Computational methods for automatic traffic signs recognition in autonomous driving on road: A systematic review," Results in Engineering, vol. 24, p. 103553, 2024/12/01/ 2024.