---
title: "Deep Learning Algorithms for Sonar Imagery Analysis and Its Application in Aquaculture: A Review"
excerpt: "논문 공부"
thumbnail: study_notes/lab-paper/250417_00.png
banner: 999999_home_image_banner_textbook.jpg
banner_caption: Research Memo
use_math: true
categories:
  - Studies
tags:
  - Paper Reviews
---

<figure class="align-center" style="width: 60%">
  <a href="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/250417_00.png">
  <img src="{{ site.url }}{{ site.baseurl }}/assets/images/study_notes/lab-paper/250417_00.png">
  </a>
  <figcaption>
  Fig.1 Deep Learning Algorithms for Sonar Imagery Analysis and Its Application in Aquaculture: A Review
  </figcaption>
</figure>



# 요약

소나 이미지에 대해 딥러닝 기법을 활용한 연구를 조사한 리뷰 논문이다.


# 내용

[7-9] 논문도 소나 이미지 처리 관련 리뷰논문

제 II장은 소나 이미지의 DL 기반 소나 이미지 처리 모델과 기법들을 소개

제 III장에서는 DL 기반 소나 이미지 처리의 양식 분야 응용을 소개: 과제 응용 가능성 확인

제 IV장에서는 공통적인 주요 도전 과제와 향후 연구 방향 설명

제 V장에서는 토론 및 결론 제시

## Denoising

### 전통적 노이즈 제거

두가지 종류, additive 와 multiplicative noise가 있음

소나 이미지에서 가장 흔한 노이즈는 speckle noise, multiplicative noise임

Speckle noise 제거는 다양한 방법이 있음[17-20], spatial domain filtering은 smooth but loss of edge detail의 특징이 있고, transform domain filtering은 good edge preserving effect but high-freq. data loss에 의한 loss of detail의 특징이 있음.

#### Spatial Domain Filtering

[12, 13] 레퍼런스 참조

미디언 필터링(median filtering)과 위너 필터링(Wiener filtering) 등

#### Transform Domain Filtering

[14] 레퍼런스 참조

웨이블릿 변환(wavelet transform), 푸리에 변환(Fourier transform), 주성분 분석(PCA) 등

### DL 활용 노이즈 제거

Speckle noise 제거에 대해 CNN 기반 residual learning을 수행 [21-22]

CNN 활용 crosstalk noise 제거[23]

## Feature Extraction

딥러닝 사용 전엔 ANN을 활용한 feature representation learning이 있었음 [24]

초기 CNN 활용 논문은 2017년이며, transfer learning을 활용함. [25-26]

VGG-16, VGG-19, VGG-f, AlexNet, ResNet-50, PoseNet 등의 사전 학습된 CNN 모델을 미세 조정(fine-tuning)하여 특징을 추출하고, 이를 SVM과 결합하여 성능을 향상시켰다 [25-29]. 이 중 VGG-19와 AlexNet은 우수한 성능을 보였으며, ResNet은 일반화 성능이 뛰어났다. 한편, PoseNet은 트리플릿(triplet)을 사용하여 학습하였다.

낮은 정확도, 불연속적인 경계 윤곽, 세부 특징 손실 등의 문제를 해결하기 위해, 20년에는 FCN을 활용한 논문[30], 22년에는 CAM(Channel Attention Module)을 활용한 논문[31], 그리고 22년 DSRM(Deep Separable Residual Module)을 활용한 논문[32]이 나옴.

Improved FCN은 batch normalization 레이어를 추가하여 스킵 구조를 향상시키고, mini-batch gradient descent method를 활용하여 세부 정보를 보다 정확하게 추출하고 통합함[30]. 평균 IoU(교차합/합)는 83.05% 임.

CAM은 the maximum pooling 과 the global average pooling results를 조합하여 더 많은 특징을 학습함.

DSRM은 DSRM은 multiscale features를 추출하고, MCFFM(Multichannel Feature Fusion Method)을 활용하여 특징 전달 능력을 강화함. DSRM은 모델의 학습 파라미터를 줄여 계산 복잡도를 낮춤. MCFFM은 channel merging technology를 활용해 서로 다른 단계의 feature information을 연결함.

기존 특징 추출 방법과 비교했을 때 DL 기반 방법은 보다 나은 feature discrimination 성능을 가짐. DL 기반 특징 추출에 대한 독립적인 연구보다는, 대부분의 연구는 후속 ATR 작업 속에서 포함되는 형태로 진행됨.

## Classification

Sonar image classification은 객체들의 특징을 기반으로 서로 다른 클래스의 객체를 구별하는 작업임. 특히 제한된 샘플 수나 제로 샘플(zero sample)의 상황에서 다양한 연구가 수행됨.

본문 그림 8은 classification method에 따른 논문 수

### Public Datasets

표3은 public dataset을 사용한 classification 논문의 종류 표

CKI, TDI-2017, TDI-2018의 세 가지 데이터셋은 submerged dummy를 포함하고 polarizing noise와 같은 다양한 노이즈 영향을 포함함

CKI 데이터셋은 clean water testbed에서 찍은 dataset

TDI-2017과 TDI-2018은 각각 2017년과 2018년에 실제 흐린 수중 환경의 dataset

GoogleNet [33]과 AlexNet [34]은 몸체(body)와 배경(background)을 분류하는 binary classification에 활용됨

SeabedObjects-KLSG dataset은 multiclass classification을 위한 dataset으로, 난파선(wreck), 익사자(drowning victim), 비행기(airplane), 기뢰(mine), 해저(seafloor)가 포함되어 있음. Huo et al. [35]와 Cheng et al. [31]은 해당 데이터셋을 기반으로 연구를 수행함.

Huo et al.은 fine-tuning pretrained CNN(VGG, ResNet 등)을 사용하였으며, [35-37] SeabedObjects-KLSG 70%와 광학 이미지 기반의 semisynthetic 비행기 및 익사자 데이터 30%를 사용해 훈련한 모델의 정확도가 97.76%인 것을 보임.

Cheng et al.은 MSRAM(Multiscale Repeated Attention Mechanism)을 기반으로 한 MDCTL(Multidomain Collaborative Transfer Learning) 기법을 제안함. [31] MDCTL은 low-level characteristic similarity btw. SSS and SAR images와 high-level representation similarity between SSS and optical images을 결합해 feature extraction을 향상시킴. MSRAM은 space와 CAM(Channel Attention Module) extract rich contour info. 를 조합하여 99.21%의 classification accuracy와 model generalization 능력을 달성함.

FLS marine debris dataset은 Aleem et al. 연구진이 VGG16과 ResNet-50을 활용해 10종류의 해양 폐기물을 분류하는데 사용됨. [36] 최종 분류 단계에서는 Faster R-CNN의 regional proposal network (RPN)에서 추출된 feature maps가 활용됨. VGG16보다 ResNet-50을 사용할 경우 더 많은 특징을 학습할 수 있음.

CIFAR-10 데이터셋은 Qin et al. 연구진이 다양한 CNN 모델을 활용하여 에서 퇴적물 분류 작업을 수행하는데 사용됨. 해당 연구진은 ResNet을 미세 조정하여 3.459%의 최저 오류율을 기록함. [37]

### Limited Training Samples

표4는 limited training samples를 사용한 classification 논문의 종류 표

SSS는 Mine-Like Object(MLO), Non-Mine-Like Object(NMLO), Other Significant Object(OSO), shipwreck, plain seabed sediment 등의 표적을 포착하는 데 자주 사용됨

학습 샘플이 부족하기 때문에, SSS 이미지 classification에서는 전이 학습이 여전히 유용한 방법이다. CNN [38-44], VGG [45-46], ResNet [47], AlexNet [48], InceptionNet [49] 등이 SSS 이미지의 객체 분류에 사용됨

VGG-11과 ResNet-18의 결합 [45]은 과적합을 효과적으로 피했다. SVM 분류기와 신경망의 모든 파라미터를 활용한 마지막 완전 연결 층의 미세 조정, CNN과 계층적 가우시안 프로세스(HGP) 분류기 및 머신러닝(ML)의 결합, 심층 신념망(DBN)의 가중치를 사용하는 적응형 가중치 CNN(AW-CNN)과 같은 전략들이 높은 정확도를 달성하는 데 기여했다. Ochal 등 [47]은 프로토타입 네트워크(PN), 관계 네트워크, 소프트 k-평균 PN, 일관된 PN(CPN) 등 몇 가지 소수 학습(FSL) 방법을 비교했으며, 대부분의 데이터셋에서 FSL 방법이 베이스라인 모델보다 더 좋은 성능을 보였다. 또한 GAN(생성 적대 신경망)을 사용하여 데이터셋을 확장하는 것 [40], [44]은 분류 성능 향상에 효과적이었다. 특정 표적에 대한 적절한 SSS 이미지가 전혀 존재하지 않는 극단적인 상황에서는 ‘제로샷 학습 문제(zero-shot learning problem)’가 발생한다 [50]. 이를 위해 DNN(심층 신경망)을 사용하여 의사 SSS 이미지를 학습하는 제로샷 분류 방법이 개발되었다. 이미지는 일반 광학 이미지와 사용 가능한 SSS 이미지를 사용해 고정된 스타일 변환 방법으로 합성되었다. 많은 파라미터와 높은 시간 복잡도 문제를 해결하기 위해 깊이별 분리 합성곱 특징 융합(DSCFF) [51] 방법이 제안되었고, 이는 효과적인 정보를 최대한 활용하여 90.1%의 정확도를 달성하였으며, VGG16과 ResNet50보다 더 나은 성능과 가벼운 모델을 보였다. 다양한 합성곱 층의 깊이에 따른 계산 속도와 정확도를 비교한 결과, 5층을 초과하는 합성곱 층은 정확도 향상에 기여하지만 비용이 증가했다 [43].

---

# 참고문헌

Y. Chai, H. Yu, L. Xu, D. Li and Y. Chen, "Deep Learning Algorithms for Sonar Imagery Analysis and Its Application in Aquaculture: A Review," in IEEE Sensors Journal, vol. 23, no. 23, pp. 28549-28563, 1 Dec.1, 2023, doi: 10.1109/
