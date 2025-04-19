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

VGG-11과 ResNet-18의 결합 [45]은 overfitting을 효과적으로 피함

그 외엔 높은 정확도를 달성하는 것에 집중한 연구들임, 예를 들면 SVM classifier의 마지막 fully connected layer의 미세 조정과 신경망의 모든 파라미터를 활용한 경우가 있고, CNN과 HGP(Hierarchical Gaussian Process) classifier 및 ML의 조합을 활용한 경우가 있으며, DBN(Deep Belief Network)의 weight를 사용하는 AW-CNN(Adaptive Weights CNN) 활용한 경우 등이 있음.

Ochal et al. 연구진은 [47] 몇 가지 FSL(few-shot learning) 방법을 비교하였음, PN(Prototypical Network), relation network, soft k-means PN, CPN(consistent PN)을 비교함. 대부분의 데이터셋에서 FSL 방법이 baseline model보다 더 좋은 성능을 보임. 또한 GAN(Generative Adversarial Network)을 사용하여 데이터셋을 확장하는 것은 분류 성능 향상에 효과적임. [40], [44]

특정 표적에 대한 적절한 SSS 이미지가 전혀 존재하지 않는, 'zero-shot learning problem' 같은 극단적인 경우도 있음. [50] 이를 위해 DNN(Deep Neural Network)을 사용하여 pseudo SSS 이미지를 학습하는 제로샷 분류 방법이 개발됨. Pseudo SSS 이미지는 일반 광학 이미지와 사용 가능한 SSS 이미지를 사용해 fixed style-transfer method로 합성함.

많은 파라미터와 high time complexity 문제를 해결하기 위해 DSCFF(Depthwise Separable Convolution Feature Fusion) [51] 방법이 제안됨. 해당 방법은 90.1%의 정확도를 달성하였으며, VGG16과 ResNet50보다 더 나은 성능과 가벼운 모델을 보임. 다양한 CNN layer depth에 따른 계산 속도와 정확도를 비교한 결과, 5층을 초과하는 합성곱 층은 정확도 향상에 기여하지만 비용이 증가함. [43]

FLS의 경우, CNN은 잔해 물체 [52]와 해파리 [53]를 분류하는 데 사용됨. 해저 퇴적물 분류에는 WBPNN(Wavelet-BP Neural Network) [54]과 RPNet(Random Patches Network) [55]가 사용됨. WBPNN은 self-adaptive learning rate와 momentum factor를 가지고 있으며, network parameter initialization이 있음. RPNet은 노이즈와 소규모 샘플의 영향을 피할 수 있었음. 동시에, oversmoothness와 misclassification에 대해 RPNet은 decision fusion algorithm을 사용하여 단일 classifier보다 분류 정확도를 향상시킴.

SAS의 경우 FLS와 유사하게 CNN [25], [56-60]이 가장 널리 사용되는 방법임. 합성곱 층 네 개를 가진 CNN [56-57]이 가장 우수한 성능을 보임. Fine-tuning CNN [58] 을 활용해 소량의 라벨링된 데이터로 해저 유형을 분류하였으며, 정확도는 88.2%임. Synthetic image [59]를 이용해 CNN을 학습시킨 결과, 실제 데이터로 학습된 CNN과 동일한 성능을 보임. Binary classification task [60]에서는 low confident false alarms와 augmented data를 사용해 학습한 경우가 더 나은 성능을 보여줌.

Target-concept transfer learning, sensor transfer learning, and intramodality transfer learning은 지뢰에서 불발탄(UXO)으로 적용됨. [61-62] 이 중에선 intramodality transfer learning이 가장 뛰어난 성능을 보임.

또한, classification prediction results의 평균화, feature extraction data의 융합 [63], final dense layer와 output layer의 수정 [64], fully connected layers의 수 변경 [65], 전체 네트워크의 미세 조정 [66]은 더 풍부한 정보를 제공하고 성능을 향상함. ImageNet에서 사전 학습된 VGG와 NasNet-large는 미세 조정 후 최고의 성능을 달성함.

그 외에도 SAS 데이터의 phase information, frequency spectrum, amplitude content, 그리고 PSD(2-D power spectral density) [67-69]는 CNN에 활용될 경우 성능 향상에 긍정적 영향이 있었음. Phase information만 사용한 경우 [67], 이미지의 amplitude 정보만 사용한 경우보다 더 나은 classification 성능을 얻을 수 있음. Amplitude에 PSD 정보를 추가로 사용한 경우가 [68] 성능이 가장 뛰어남.

한편, ImageNet에서 사전 학습된 VGG 네트워크는 미세 조정(fine-training)을 통해 최고의 성능을 달성함. 위의 정보를 사용한 CNN의 파라미터 수는 적음. [69]

또한, 이미지 품질, local background environment, 물체의 형태, 방향, 길이 등의 보조 정보도 활용 가능함. Tiny CNNs [70], MLP(multilayer perceptron) [71], GoogleNet [72], CSDN(compound CNN) [73] 등이 classification에 사용됨. 높은 false alarm rate를 줄이기 위해 SPDRDL(Structural Prior-Driven Regularized DL) [74]이 제안되었으며, 이는 structural similarity prior와 structural scene context prior를 통합하였음. 또한, multiview SAS image classification에 대해선 image-fusion technique와 DBM(DL-based on Boltzmann Machines) 연구가 수행됨. [63], [75]

현재 소나 이미지에서 가장 많이 연구되는 과제는 classification임. 개요에서 볼 수 있듯이, CNN과 VGG 네트워크가 sonar image classification에 가장 많이 사용되는 방법임. Transfer learning은 optical image로 사전 학습하고 sonar image에서 fine-tuning하는 feasible method임.

## Detection

Object detection of sonar image는 ROI(Regions of Interest)를 인식하고, 각 객체의 위치와 크기를 boundary frame으로 예측하며, 신뢰도를 제공하는 것을 목표로 함.

현재 object detection 방법은 주로 두 가지 범주로 나뉨: two-stages와 one-stage 알고리즘임. Attention mechanism에 기반한 DL detection methods는 II-D3절에서 다룸. 그림 9는 detection method에 따른 논문 수를 나타내며, 표 V는 detection object에 따른 detection methods를 나타내는 표임.

### Two-Stage Detection

One-stage algorithm은 end-to-end 방식의 object detection 방법으로, 하나의 네트워크를 통해 객체의 클래스와 위치를 동시에 출력한다. 이 방법은 속도가 빠르지만 정밀도가 낮은 편으로, 특히 small target regression이 그러함. You Only Look Once(YOLO) 시리즈 기반의 target detection 알고리즘에 관한 연구가 활발히 이루어지고 있음.

YOLOv1 [78], YOLOv2 [79], YOLOv3 [80-83], DPFIN(YOLOv3-dual-path feature fusion neural network) [84], lightweight YOLOv4 [85], 트랜스포머 모듈과 YOLOv5s를 통합한 TR-YOLOv5s [86] 등이 객체 탐지에 사용됨. 회전된 객체 탐지를 위해 엔드-투-엔드 네트워크인 RBoxNet [87]이 제안되었으며, YOLOv2와 RBoxNet으로 구성된 파이프라인은 표적 탐지, 위치 및 회전 정보 산출에 활용되었다. RBoxNet은 정확도와 속도의 최적 균형을 이루었고, YOLOv2+RBoxNet은 16.19 FPS로 가장 빠른 속도를 보였다. YOLOv3는 YOLOv2 및 일반 CNN보다 뛰어난 성능을 보여 98.2%의 진양성률(true positive rate)을 기록하였다.

YOLOv1 [78], YOLOv2 [79], YOLOv3 [80], [81], [82], [83], YOLOv3-dual-path feature fusion neural network (DPFIN) [84], lightweight YOLOv4 [85], and integration of transformer module and YOLOv5s (TR-YOLOv5s) [86] were used to detect objects. For rotated object detection, an end-to-end network (RBoxNet) [87] was proposed and a pipeline composed of YOLOv2 and RBoxNet to detect targets and determine target position and rotation. The RBoxNet reached the optimum tradeoff between accuracy and speed, while YOLOv2+RBoxNet was the fastest at 16.19 FPS. YOLOv3 outperformed YOLOv2 and CNN at 98.2% of a true positive rate. 

소량의 유효 샘플과 낮은 신호대잡음비(SNR)를 가진 소나 데이터셋을 대상으로, YOLOv3-DPFIN은 듀얼 패스 네트워크(DPN) 모듈과 융합 전이 모듈을 통해 효과적인 특징을 추출하고, 조밀 연결을 통해 다중 스케일 예측 성능을 향상시켰다. 실험 결과, 두 개의 시뮬레이션 소나 데이터셋에서 84.4%의 mAP와 56 fps의 성능을 보였다. YOLOv3 개선에는 FPN, K-평균(K-means), 이진 분류 크로스 엔트로피 함수가 사용되었다.

Aiming at sonar datasets with small effective sample size and low SNR, YOLOV3-DPFIN extracted effective features through dual-path network (DPN) module and fusion transition module, and improved multiscale prediction by dense connection. The experiment showed that mAP was 84.4% with 56 fps on two simulated sonar datasets. FPN, K -means, and binary classification cross-entropy function were used to improve YOLOv3.

경량 YOLOv4는 YOLOv4의 특징 추출 네트워크인 CSPDarkNet-53을 개선하여 모델 파라미터와 네트워크 깊이를 줄였고, PANet 특징 강화 모듈을 적응형 공간 특징 융합 모듈(ASFF)로 대체하였으며, 융합 특징 층의 수를 증가시켰다. 그 결과, YOLOv4 및 YOLOv4-tiny보다 탐지 정확도와 속도 모두 향상되었다.

The lightweight YOLOv4 improved feature extraction network CSPDARKnet-53 of YOLOv4 to reduce the model parameters and network depth, replaced the PANet feature enhancement module with the adaptive spatial feature fusion module (ASFF), and increased the number of fused feature layers. The performance of the model in detection accuracy and speed improved compared to YOLOv4 and YOLOv4-tiny.

TR-YOLOv5s는 SSS 이미지에서 희소한 표적과 부족한 특징을 고려하여 주의 메커니즘(attention mechanism)을 도입하여 실시간 객체 탐지를 수행하였다. 해당 모델은 mAP 85.6%, macro-F2 87.8%, 이미지당 인식 속도 약 0.068초로 검증되었다.

TR-YOLOv5s introduced attention mechanism to complete real-time target detection in view of the characteristics of sparse targets and poor features in SSS images. The model was verified that the mAP was 85.6%, macro-F2 was 87.8%, and the real-time recognition speed was about 0.068 s per image.

또한, MLO(기뢰 유사 물체)를 탐지하기 위해 Gabor 기반 탐지기 [88]가 제안되었으며, 다른 탐지기들과 비교되었다. 이 방법은 약한 특징과 강한 특징을 모두 추출하여 다양한 크기의 MLO를 효과적으로 처리하였다. 특징 추출을 위해 파라미터화된 가보어(Gabor) 계층이 도입되었으며, 계단식 층 구조에 Gabor 필터링 모듈이 내장되었다. 이러한 개선은 탐지 속도와 정밀도를 높였다.

In addition, Gabor-based detector [88] was proposed to detect MLOs and compared to other detectors. The method extracted both weak and strong features, which effectively handled multiple scales MLOs. A parameterized Gabor layer was introduced to extract features. The cascaded layers embedded the Gabor filtering modules. These improvements enhanced detection speed and precision.

그 외에도 RetinaNet [89], [90], MiNet [91], CNN [64], [92], AlexNet [25] 등이 객체 탐지에 사용되었다. ResNet 기반의 RetinaNet 탐지 프레임워크 [89]는 바위를 탐지하기 위해 이미지 내 최소 3×3 픽셀이 필요했으며, 단일 스테이지 잔차 신경망 [90]을 사용하면 이미지 해상도를 개선할 수 있었다.

Besides, RetinaNet [89], [90], MiNet [91], CNN [64], [92], and AlexNet [25] were also used to detect objects. RetinaNet detection framework [89] based on ResNet needed to contain at least 3×3 pixels in the image to detect rock and using a single-stage residual network [90] could improve the resolution of the images.

MiNet [91]은 경량 모델로, AUV(자율 수중 차량)에 탑재하기 적합하며, 크기는 9.9MB, 연산량은 0.0122 GFLOPS였다. 모델 학습에는 점진적 학습 방식이 사용되었다. 반면, VGG 기반 CNN [92]을 사용한 MLO 탐지는 높은 오탐률을 유발하였다.

MiNet [91] was light to mount on autonomous underwater vehicle (AUV) at 9.9 MB and 0.0122 giga floating-point operations per second (GFLOPS) and used an incremental training procedure to train the model. However, using a VGG-like CNN [92] to detect MLO caused high false alarm rate.

### Attention Mechanism

1단계 및 2단계 탐지 방법 외에도, 어텐션 메커니즘 기반 모델들도 객체 탐지에 사용되었다. MRF-Net(Multiple Receptive Field Network) [93], AGFE-NET(Adaptive Global Feature Enhancement Network) [94], AutoDL(Automatic DL) [95], MB-CEDN(Multibranch Convolutional Encoder–Decoder Network) [96] 등이 수중 객체 탐지를 위해 사용되었다. 전이 학습 모델의 중복성과 일반화 능력 부족 문제를 해결하기 위해 AutoDL이 도입되었다. AutoDL의 파라미터 수는 ResNet50의 단 15.2%에 불과했지만, 높은 탐지 정확도와 속도를 달성하였다.

Except for one- and two-stage detection methods, attention mechanism-based models were also used for object detection. Multiple receptive field network (MRF-Net) [93], adaptive global feature enhancement network (AGFE-NET) [94], automatic DL (AutoDL) [95], and multibranch convolutional encoder–decoder network (MB-CEDN) [96] were used to detect underwater objects. Aiming at the problem of redundancy and poor generalization ability of transfer model, AutoDL was introduced. The number of parameters was only 15.2% of that of ResNet50, but the method achieved high detection precision and speeds.

탐지 방법 전반을 검토해보면, YOLO 시리즈는 소나 이미지에서 객체를 탐지하는 데 널리 사용된다. 사전 학습 및 파인튜닝된 기본 CNN 역시 인기 있는 객체 탐지 방법이다. 한편, Fast R-CNN, Faster R-CNN, YOLO, SSD 등의 성능이 비교되었다. 일반적으로, 사전 학습된 딥러닝 모델을 파인튜닝하는 것은 좋은 전략이다. 다양한 탐지 작업에 따라 서로 다른 방법이 필요하다. 과제의 차이점과 데이터셋의 부족으로 인해 탐지 방법을 평가할 수 있는 통일된 기준은 존재하지 않는다.

Reviewing all work of detection methods, YOLO series are widely used to detect objects in sonar images. Basic CNNs after pretraining and fine-tuning are also popular target detection methods. Meanwhile, fast R-CNN, faster R-CNN, YOLO, and SSD were compared. In general, fine-tuning a pretrained DL model is a good strategy. Different methods are required for different detection tasks. Different tasks and the lack of dataset result in no uniform standard for measuring detection methods.

## Segmentation

이미지 분할은 이미지의 픽셀을 고유한 특성을 가진 특정 클래스들로 나누고, 관심 대상을 제안하는 기술 및 과정이다. 소나 이미지에서의 ROI(관심 영역)는 객체에 의해 생기는 하이라이트와 그림자 영역으로, 이를 통해 객체의 크기와 형태를 파악한다. 소나 이미지 분할의 결과는 특정 영역에 특정 레이블이 할당된 마스크 이미지이다. 딥러닝 기반의 이미지 분할 기술은 일반적으로 두 가지 범주로 나뉜다: 의미론적 분할과 인스턴스 분할.

Image segmentation is the technology and process of dividing pixels of images into specific classes with unique properties and proposing the object of interest. The ROI for sonar images is the highlight and shadow areas caused by an object, which gets its size and shape. The result of sonar image segmentation is a masked image that specific regions are assigned to specific labels. Image segmentation techniques based on DL are commonly divided into two categories: semantic segmentation and instance segmentation.

개요는 다음 섹션에 나와 있다. 마찬가지로, 다양한 분할 방법에 대한 논문 수는 그림 10에 제시되어 있으며, 표 VI에는 의미론적 분할과 인스턴스 분할 방법이 나열되어 있다.

An overview is in the following section. Similarly, the number of papers for different segmentation methods is presented in Fig. 10 and Table VI lists semantic and instance segmentation methods.

### Semantic Segmentation

해당 방식은 각 픽셀에 클래스 레이블만 할당한다. FCN [30], [97], [98], DeepLab [99], DeepLabV3+ [100], CNN [6], [32], [101], SegNet [102], U-Net [103] 등이 소나 이미지의 의미론적 분할에 사용되었다. FCN은 사다리형 네트워크 아키텍처를 결합하여 파인튜닝할 수 있다. 마르코프 랜덤 필드는 FCN의 스무딩 결과를 최적화할 수 있으며, DeepLab과 결합하여 해저 정보를 식별할 수 있다. DeepLabV3+는 수중 컬럼의 강한 에코를 약화시키기 위해 대칭적 정보 합성 모듈(SISM)을 추가하였다. 해당 모델은 거칠게-정교하게(coarse-to-fine) 분할하는 전략으로 학습되었고, 평균 오류 1.1픽셀을 달성했다. CNN 기반 프레임워크 AR-Net [101]은 SegNet의 네트워크 구조 대칭성과 U-Net의 장점을 통합하였다. FCN, DeepLab, U-Net, SegNet, ResUNet-a, AR-Net 등 여섯 가지 분할 모델을 비교하여 그 성능을 검증하였다.

It only assigns a class label to each pixel. FCN [30], [97], [98], DeepLab [99], DeepLabV3+ [100], CNN [6], [32], [101], SegNet [102], and U-Net [103] were used for semantic segmentation of sonar images. FCN could join a ladder network architecture to fine-tune. The Markov random field could optimize the smoothing results of FCN and could be combined with DeepLab to identify seabed information. DeepLabV3+ added a symmetrical information synthesis module (SISM) to weaken the strong echoes of water column. The model was trained using a coarse-to-fine segmentation strategy. The result achieved 1.1 pixels of mean error. A CNN framework (AR-Net) [101] integrated the advantages of SegNet network structure symmetry and U-Net. The effectiveness was verified by comparing six different segmentation models, including FCN, Deeplab, U-Net, SegNet, ResUNet-a, and AR-Net.

실시간 분할 작업과 인코더–디코더 네트워크는 활발히 논의되고 있다. 효율적인 네트워크(ENet) [102], 효율적인 합성곱 신경망(ECNet) [104], 팽창 합성곱 신경망(DcNet) [105], 다중 분기 합성곱 인코더–디코더 네트워크(MB-CEDN) [96] 등은 인코더–디코더 네트워크로서 실시간 분할을 달성하였다. 일반적으로 인코더는 풍부한 계층적 특징을 학습하고, 디코더는 입력 크기와 동일한 해상도의 특징 맵을 복원한다. ENet에서는 여러 개의 사이드 출력을 갖는 단일 스트림 DNN이 엣지 분할을 최적화하고, 불균형 분류 문제를 완화하기 위해 가중 손실이 사용되었다. DcNet은 밝기 불균일성 문제 등 다양한 노이즈를 해결하고, 입력 이미지의 공간 차원을 줄이며, 타깃의 세부 정보를 복원하였다. 핵심 네트워크는 DCblock이라 불리는 블록 연결 구조로, 인코더와 디코더 사이에서 팽창 합성곱과 깊이별 분리 합성곱을 사용하여 이미지의 더 많은 문맥 정보를 확보하였다. MB-CEDN은 반지도 학습 모델로, 다중 타깃 분할을 위해 제안되었다. 이외에도 SC-CNN(Self-Cascaded CNN) [106], OS-ELM(Online Sequential Extreme Learning Machine) [107], IDUS(Iterative Deep Unsupervised Segmentation), IDSS(Iterative Deep Semi-supervised Segmentation) [108] 또한 실시간 분할을 달성하였다. SC-CNN은 스펙클 노이즈와 밝기 불균일성에 대응 가능하며, 지역적 및 전역적 특징을 동시에 활용한다. OS-ELM은 시간 가변 이득(TVG) 보정, 속도 보정, 집합 경험적 모드 분해(EEMD) 디노이징을 결합하였다. IDUS와 IDSS는 실시간 성능이 지도 학습 방식보다 우수했으며, 크기·무게·전력 소비가 적은 플랫폼에 적용되었다. 유사하게 MRF도 결과를 정제하는 데 유효하다. 이외에도 GAN [30]과 이미지 디노이징을 위한 딥 CNN(DnCNN) [109] 또한 분할에 사용되었다. DnCNN은 수용 영역 블록과 탐색 어텐션 메커니즘을 통합하여 단일 객체 이미지의 분할을 완성하였다. 이 모델은 더 많은 엣지 정보와 세부 사항을 유지할 수 있다.

Real-time segmentation tasks and encoder–decoder networks are hotly discussed. Efficient network (ENet) [102], efficient convolutional network (ECNet) [104], dilated CNN (DcNet) [105], and multibranch convolutional encoder–decoder network (MB-CEDN) [96] are encoder–decoder networks and achieved real-time segmentation. In general, an encoder learns rich hierarchical features and a decoder restores full input-size resolution feature maps. In ENet, a single stream DNN with multiple side outputs optimized edge segmentation and weighted loss was used to alleviate the influence of the imbalance classification. DcNet solved various noises, such as the intensity inhomogeneity problem, reduced the spatial dimension of input images, and recovered the details of the target. Its core network is a block connection named DCblock, which used dilated convolution and depthwise separable convolution between the encoder and the decoder to attain more context of images. MB-CEDN was a semisupervised learning model and was proposed for multitarget segmentation. In addition, self-cascaded CNN (SC-CNN) [106], online sequential extreme learning machine (OS-ELM) [107], iterative deep unsupervised segmentation (IDUS), and iterative deep semisupervised segmentation (IDSS) [108] also accomplished real-time segmentation. SC-CNN was available for speckle noise and intensity inhomogeneity and simultaneously used local and global features. OS-ELM combined with time-varying gain (TVG) correction, speed correction, and ensemble empirical mode decomposition (EEMD) denoising. Real-time of IDUS and IDSS outperformed supervised methods and applied to platform of low size, weight, and power. Similarly, MRF is available for refining the result. Besides, GAN [30] and deep CNN for image denoising (DnCNN) [109] were also used for segmentation. DnCNN integrated receptive field block and search attention mechanism to complete segmentation of a single object image. It retains more edge information and details.

### Instance Segmentation

이 방식은 클래스 레이블뿐만 아니라 ID도 함께 가진다. 위치 기반 객체 분할을 위한 이중 분할 어텐션(DSA-SOLO) [110]이 SSS 이미지 분할을 위해 제안되었으며, 공간 어텐션과 채널 어텐션을 융합하는 DSA 어텐션 모듈을 도입하였다. 해당 모델은 DSA를 SOLOv2의 FPN 네트워크에 임베딩하였고, 공개 데이터셋인 SCTD(sonar common target detection) [95]를 통해 학습되었다.

It has not only the class label but also an ID. A double split attention segmentation objects by locations (DSA-SOLO) [110] was proposed for SSS image segmentation, which introduced a DSA attention module to fuse spatial attention and channel attention. The model embedded DSA into the FPN network of SOLOv2 and was trained by a public dataset called sonar common target detection (SCTD) [95].

앞선 리뷰에서 볼 수 있듯, 연구는 의미론적 분할에 집중되고 있다. FCN과 인코더–디코더 구조는 전형적인 의미론적 분할 아키텍처이다. 분할 결과의 후처리에는 MRF가 유효하다. 한편, 공개 데이터셋의 부족으로 인해 각 분할 알고리즘은 특정한 분할 작업과 대상에 사용된다. 따라서 어떤 분할 방법이 가장 우수하다고 말하기는 어렵다. 인스턴스 분할 또한 더 많은 연구가 필요하다.

As seen from the above review, research focuses on semantic segmentation. FCN and encoder–decoder are typical semantic segmentation architectures. MRF is available for postprocessing the result of segmentation. Meanwhile, due to the lack of public datasets, each segmentation algorithm is used for specific segmentation tasks and targets. It is difficult to say which is the best method of segmentation. Instance segmentation also needs to be explored.

## DL and Sonar Image Processing

딥러닝 기술은 특징 추출, 분류, 탐지, 분할 등의 이미지 처리 작업에 사용되어 왔다. 또한, 딥러닝 모델은 광학 이미지, 의료 이미지, 현미경 이미지 등 다양한 유형의 이미지에 적용되어 왔다. 앞서 언급했듯이, 딥러닝은 소나 이미지 처리 분야에도 적용되었다. 딥러닝 모델은 더 많은 특징 정보를 포착할 수 있으며, ATR(자동 표적 인식) 작업의 정확도를 향상시킬 수 있다. 많은 딥러닝 방법들이 소나 이미지 분류, 탐지, 분할을 수행하기 위해 사용되었다. 이는 소나 이미지 정보를 더 쉽게 획득하는 데 도움을 준다. 하지만 대부분의 딥러닝 방법은 일반적으로 대량의 라벨링된 깨끗한 데이터를 필요로 한다. 이는 소나 이미지 처리에 있어 큰 도전 과제이다. 소나 이미지는 수집이 어렵고 심한 노이즈를 포함하고 있다. 이러한 문제는 모델의 과적합과 정확도 저하를 초래한다. 또한, 딥러닝 모델의 성능을 측정할 수 있는 통일된 기준이 존재하지 않는다. 따라서 딥러닝 기술을 활용한 소나 이미지 처리는 여전히 가치 있고 의미 있는 과제이다.

DL techniques have been used for image processing tasks, including feature extraction, classification, detection, and segmentation. Also, DL models have been applied to various types of images, such as optical images, medical images, and microscopic images. Meanwhile, as mentioned above, DL has also been applied to the field of sonar image processing. DL models can capture more feature information and improve the accuracy of ATR tasks. Many DL methods were used to process sonar images to complete classification, detection, and segmentation of sonar images. This helps us easier to obtain the information of sonar images. However, most DL methods typically require large amounts of labeled and clean data for training. This is a huge challenge for sonar image processing. Sonar images are not easy to collect and have severe noise. These problems make the models overfitting and precision degradation. Meanwhile, no uniform standard measures the performance of DL models. Thus, sonar image processing utilizing DL techniques is still a valuable and meaningful task.



---

# 참고문헌

Y. Chai, H. Yu, L. Xu, D. Li and Y. Chen, "Deep Learning Algorithms for Sonar Imagery Analysis and Its Application in Aquaculture: A Review," in IEEE Sensors Journal, vol. 23, no. 23, pp. 28549-28563, 1 Dec.1, 2023, doi: 10.1109/
