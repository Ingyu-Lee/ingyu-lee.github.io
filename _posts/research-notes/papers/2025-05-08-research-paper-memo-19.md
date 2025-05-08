---
title: "메모: Exploring the impact of hyperparameter and data augmentation in YOLO V10 for accurate bone fracture detection from X-ray images"
excerpt: "논문 인트로 및 컨클루젼 번역기"
thumbnail: study_notes/lab-paper/250508_00.png
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/250508_00.png">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/250508_00.png">
  </a>
  <figcaption>
  Fig.1 Exploring the impact of hyperparameter and data augmentation in YOLO V10 for accurate bone fracture detection from X-ray images
  </figcaption>
</figure>

# Abstract

X-ray 이미지에서 골절을 정확히 식별하는 것은 신속하고 적절한 의료 처치를 위해 필수적입니다. 본 연구는 You Only Look Once (YOLO) V10 아키텍처를 이용한 골절 감지에서 하이퍼파라미터 및 데이터 증강 기법의 영향에 대해 탐구했습니다.

YOLO 아키텍처는 객체 감지 작업에 널리 사용되고 있지만, X-ray 이미지에서 골절을 인식하는 것은 미세하고 복잡한 패턴을 다루어야 하므로 보다 엄격한 모델 튜닝이 필요합니다. 이미지 증강은 이미지 언샤프 마스킹 기법과 대비 제한 적응형 히스토그램 평활화(CLAHE)를 사용하여 수행되었습니다. 증강된 이미지는 특징 식별을 돕고 모델 성능 향상에 기여했습니다.

본 연구는 학습률 및 에폭 수와 같은 하이퍼파라미터의 영향과 입력 데이터에 대한 데이터 증강 분석을 통해 광범위한 실험을 수행했습니다. 실험 결과, 특정 하이퍼파라미터 조합이 목표로 한 증강 전략과 결합되었을 때 골절 감지의 정확도와 정밀도가 향상됨이 입증되었습니다.

증강 데이터를 사용한 평가에서 제안된 모델은 0.964의 정확도를 나타냈습니다. 증강 이미지와 원본 이미지에서의 분류 정밀도는 각각 0.98과 0.95로 관찰되었습니다. 다른 딥러닝 모델과 비교했을 때, YOLO V10 모델의 실증적 평가 결과는 골절 감지에서 기존 접근법보다 우수한 성능을 보여주었습니다.

# Conclusion

본 연구는 YOLO V10 모델을 사용하여 X-ray 이미지에서 골절을 식별하는 것을 목표로 합니다. YOLO V10 모델은 에폭 수와 학습률을 변화시켜 다양한 하이퍼파라미터에 대해 분석되었습니다. 그러나 모델은 최소한의 변경으로도 거의 모든 구성에서 우수한 성능을 보였습니다.

에폭 수가 증가할수록 모델의 정확도가 향상되었지만, 학습 데이터에 대해서는 성능이 우수한 반면, 검증 데이터에 대해서는 분석에 어려움을 겪는 경향이 있었습니다. 또한, 이미지에 샤프닝과 대비 향상과 같은 데이터 증강이 수행되었고, 모델은 원본 데이터보다 약간 더 나은 성능을 보였습니다.

실험 결과에서 YOLO V10 모델은 원본 데이터와 비교했을 때 증강 데이터에서 더 강건한 성능을 나타냈습니다. 현재 데이터셋은 7개의 클래스(다중 클래스)로 구성되어 있으며, 모델은 다중 클래스 식별 작업에서 96.4%의 정확도를 달성했습니다. 모델은 이진 분류 작업보다 다중 클래스 식별에서 더 높은 성능을 보일 가능성이 있습니다.

객체를 이미지 내에서 로컬라이즈하는 데 있어 신뢰도 점수는 충분히 높은 수준으로 관찰되었습니다. 이미지에서 이상 부위를 보다 정확하게 식별하기 위해 컨텍스트 정보를 캡처하는 Transformer를 도입하면 성능이 더욱 향상될 수 있을 것으로 예상됩니다.

본 연구는 여러 버전의 YOLO V10 모델에 대해 확장 연구가 가능하며, 각 버전 간의 정확도와 계산 복잡성 간의 트레이드오프를 분석할 수 있습니다. 현재 연구에서는 최적화기와 정규화기(regularizer)에 대한 분석이 이루어지지 않았습니다. 이들은 모델 훈련 및 일반화에 있어 매우 중요한 요소이므로, 이를 평가하는 것도 의미가 있을 것입니다.

또한, YOLO V1부터 V10까지의 모든 버전에 대한 심층적인 서베이를 통해 객체 식별에서의 YOLO 모델 진화 과정과 헬스케어 분야에 미친 영향을 분석할 수도 있습니다. 현재 연구에서는 하이퍼파라미터의 영향을 제한적인 범위에서 분석했지만, Optuna와 같은 플랫폼을 사용하여 더 많은 하이퍼파라미터를 최적화할 수 있습니다.

또한, 데이터 누출(data leakage)의 영향을 고려하여 모델의 통계적 분석을 더욱 강화하는 것도 중요할 것입니다.

# Memo

X-ray에서 contrast를 강조하기 위해 unsharp masking과 CLAHE를 활용

Fig 18과 Table 5에서 augmented image가 결과에 긍정적 영향 있음을 보임


---

# 참고문헌

P. N. Srinivasu, G. L. A. Kumari, S. C. Narahari, S. Ahmed, and A. Alhumam, "Exploring the impact of hyperparameter and data augmentation in YOLO V10 for accurate bone fracture detection from X-ray images," Scientific Reports, vol. 15, no. 1, p. 9828, 2025/03/21 2025.
