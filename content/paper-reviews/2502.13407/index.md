---
title: "JL1-CD: A New Benchmark for Remote Sensing Change Detection and a Robust Multi-Teacher Knowledge Distillation Framework"
summary: "JL1-CD: 새로운 원격 감지 변화 감지 벤치마크 및 강력한 다중 교사 지식 증류 프레임워크 제시!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Change Detection", "🏢 Tsinghua University",]
showSummary: true
date: 2025-02-19
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.13407 {{< /keyword >}}
{{< keyword icon="writer" >}} Ziyuan Liu et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-24 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.13407" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.13407" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/jl1-cd-a-new-benchmark-for-remote-sensing" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

원격 감지 영상의 변화 감지를 위한 딥러닝 기술은 발전했지만, **부족한 고해상도 데이터와 다양한 변화 유형에 대한 일관된 감지 성능**이라는 과제가 남아있습니다. 기존 방법들은 특정 변화 유형이나 면적에 치우쳐져, 일반화 성능이 떨어지는 한계를 보였습니다. 

본 연구는 이러한 문제를 해결하기 위해 **0.5~0.75m 해상도의 5,000개 영상 쌍으로 구성된 새로운 JL1-CD 데이터셋**을 제시합니다. 또한, **변화 면적 비율(CAR)에 따라 데이터셋을 분할하여 학습하는 O-P 전략과, 다중 교사 모델을 활용한 지식 증류 프레임워크(MTKD)**를 제안합니다.  실험 결과, 제안된 방법은 다양한 네트워크 구조와 매개변수 크기에 걸쳐 변화 감지 성능을 크게 향상시켜, 최첨단 성능을 달성함을 보였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 새로운 고해상도, 포괄적인 원격 감지 변화 감지 데이터셋 JL1-CD를 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 다양한 네트워크 구조에 적용 가능한 강력한 다중 교사 지식 증류 프레임워크를 개발 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} JL1-CD 및 기존 데이터셋에서 최첨단 성능 달성 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
이 논문은 **고해상도의 포괄적인 변화 감지 데이터셋**을 제공하고 다양한 네트워크 구조에 적용 가능한 강력한 **다중 교사 지식 증류 프레임워크**를 제시하여 원격 감지 변화 감지 분야의 연구에 중요한 기여를 합니다. 이는 **현실적인 문제 해결에 초점**을 맞춘 연구로, 기존 방법의 한계를 극복하고 새로운 연구 방향을 제시합니다. 특히, **다양한 변화 유형과 변화 면적 비율**을 고려한 데이터셋과 프레임워크는 향후 연구의 기반이 될 수 있으며, **다양한 응용 분야**로 확장 가능성도 높습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.13407/extracted/6215536/pic/survey.png)

> 🔼 그림 1은 심층 학습 기반 변화 탐지(CD) 방법의 주요 발전 과정을 시간 순으로 보여줍니다.  각각의 방법은 개발 연도와 함께 표시되어 있으며, 심층 학습 기반 CD 방법의 발전 경향을 한눈에 파악할 수 있도록 합니다.  단순한 CNN 기반 방법에서 Transformer, Foundation Model 기반 방법으로의 발전 양상을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Timeline of the development of mainstream DL-based CD methods.
> </details>





{{< table-caption >}}
| Dataset | Class | Image Pairs | Image Size | Resolution |
|---|---|---|---|---|
| SZTAKI[46] | 1 | 13 | 952 × 640, 1048 × 724 | 1.5 |
| DSIFN[31] | 1 | 394 | 512 × 512 | 2 |
| SECOND[39] | 6 | 4,662 | 512 × 512 | 0.5-3 |
| WHU-CD[47] | 1 | 1 | 32,20 × 15,354 | 0.2 |
| LEVIR-CD[32] | 1 | 637 | 1,024 × 1,024 | 0.3 |
| S2Looking[48] | 1 | 5,000 | 1,024 × 1,024 | 0.5-0.8 |
| CDD[49] | 1 | 16,000 | 256 × 256 | 0.03-1 |
| SYSU-CD[50] | 1 | 20,000 | 256 × 256 | 0.5 |
| JL1-CD | 1 | 5,000 | 512 × 512 | 0.5-0.75 |{{< /table-caption >}}

> 🔼 본 논문의 표 1은 기존의 오픈소스 변화탐지(CD) 데이터셋들과 새롭게 제안된 JL1-CD 데이터셋의 정보를 비교하여 보여줍니다.  각 데이터셋의 클래스 수, 이미지 쌍의 수, 이미지 크기, 해상도 등의 주요 특징들을 한눈에 파악할 수 있도록 정리되어 있습니다.  JL1-CD 데이터셋이 기존 데이터셋들에 비해 높은 해상도와 다양한 변화 유형을 포함하는 등의 강점을 보여주는 것을 목적으로 합니다.
> <details>
> <summary>read the caption</summary>
> TABLE I: Information of Open-Source CD Datasets and the Proposed JL1-CD Dataset
> </details>





### In-depth insights


#### JL1-CD Dataset
JL1-CD 데이터셋은 **고해상도(0.5-0.75미터)**의 **대규모(5,000쌍)** 원격 감지 이미지 쌍으로 구성된 새로운 벤치마크 데이터셋입니다. 기존 데이터셋의 한계를 극복하고자 **다양한 변화 유형(인공적 및 자연적)**을 포괄적으로 포함하며, **전체적인 변화 영역의 비율(CAR)**이 다양하게 분포되어 있습니다. 이는 기존 모델의 일반화 성능을 저해하는 **불균형 데이터 분포 문제**를 해결하는 데 기여하며, 보다 견고하고 일반화된 변화 검출 모델 개발에 중요한 역할을 합니다. **512x512 픽셀**의 이미지 크기는 계산 효율성과 성능 간의 균형을 유지하며, **개방형 데이터셋**으로 공개되어 연구자들의 접근성을 높였습니다.  **다양한 CAR 비율**을 가진 이미지들을 포함함으로써 모델의 범용성을 평가하는 데 유용하며,  향후 원격 감지 변화 검출 연구에 중요한 기여를 할 것으로 예상됩니다.

#### MTKD Framework
본 논문에서 제안하는 다중 교사 지식 증류(MTKD) 프레임워크는 **변화 탐지 모델의 성능을 크게 향상시키는 핵심 요소**입니다.  **O-P 전략**을 기반으로, 다양한 변화 영역 비율(CAR)에 최적화된 여러 개의 교사 모델을 훈련합니다. 이 교사 모델들은 각기 다른 CAR 수준에 특화된 지식을 가지고 있기 때문에, 이를 학생 모델에 증류함으로써 다양한 CAR 조건에서도 일관된 성능을 보장합니다. **학생 모델은 여러 교사 모델의 강점을 통합적으로 학습**하여, 어떤 CAR 조건에서도 우수한 변화 탐지 성능을 발휘합니다. **추론 과정에서 추가적인 계산 비용 없이** 이러한 성능 향상을 얻을 수 있다는 점이 큰 장점입니다.  **MTKD는 다양한 네트워크 구조와 매개변수 크기에 적용 가능**하며, 실험 결과를 통해 기존 최첨단 모델보다 우수한 성능을 달성함을 보여줍니다.  **특히, 소규모 변화 영역에 대한 탐지 성능 향상에 효과적**이며, 이는 다양한 실제 응용 분야에서 큰 의미를 가집니다.

#### O-P Training Strategy
본 논문에서 제안하는 O-P (Origin-Partition) 전략은 **변화 영역 비율(CAR)**을 기반으로 데이터셋을 분할하여 학습하는 새로운 방법입니다. 기존의 단일 모델 학습 방식과 달리, O-P 전략은 CAR 값에 따라 데이터를 작은, 중간, 큰 변화 영역으로 나누어 각각의 모델을 학습시킵니다. 이를 통해 **다양한 CAR 값을 갖는 이미지들에 대한 모델의 일반화 능력을 향상**시키고, 특정 CAR 값에 치우친 학습으로 인한 성능 저하를 방지하는 효과를 기대할 수 있습니다.  **다양한 크기의 변화 영역에 대한 모델의 적응력을 높이는데 중점**을 두고 있으며, 특히 전반적인 변화 탐지 정확도 향상에 기여할 것으로 예상됩니다.  **다양한 크기의 변화를 가진 데이터셋에 효과적**이며, 모델의 학습 과정을 개선하여 더욱 정확한 변화 탐지를 가능하게 합니다. 하지만 **추가적인 모델 학습 및 추론 시간 증가**라는 단점이 존재합니다.

#### CAR Impact Analysis
본 논문에서 제시된 다양한 변화 영역 비율(CAR)에 대한 영향 분석은 **모델의 일반화 성능과 견고성**을 평가하는 데 매우 중요합니다.  **저 CAR 영역**에서는 모델의 정확도가 높지만, **고 CAR 영역**으로 갈수록 정확도가 떨어지는 경향을 보였습니다. 이는 모델이 훈련 데이터의 CAR 분포에 치우쳐 학습되었을 가능성을 시사합니다. 따라서 **다양한 CAR 영역을 포함하는 균형 잡힌 데이터셋**을 사용하고, **CAR에 따른 데이터 분할 및 별도 학습**을 통해 모델의 견고성을 향상시킬 수 있습니다.  **MTKD 기법**은 다양한 CAR 영역에 특화된 여러 모델의 지식을 단일 학생 모델에 통합하여 이러한 문제를 해결하는 효과적인 방법으로 제시되었습니다.  **O-P 전략**과 결합하여 **낮은 CAR 영역에서 성능 향상**을 가져왔다는 점을 주목해야 합니다.  결론적으로 CAR 영향 분석은 모델 성능의 한계를 드러내고, **데이터 전처리 및 모델 설계** 개선의 필요성을 강조합니다.

#### Future Research
본 논문은 **고해상도, 포괄적인 변화 탐지 데이터셋 JL1-CD**와 강건한 다중 교사 지식 증류 프레임워크를 제시합니다.  향후 연구는 **더욱 다양한 변화 유형과 환경을 포함하는 더욱 방대한 데이터셋 구축**에 초점을 맞춰야 합니다. 또한, **다양한 모델 아키텍처와 매개변수 크기에 적용 가능한 일반화된 지식 증류 프레임워크 개발**이 중요합니다.  **계산 비용을 줄이면서 성능을 향상시키는 경량화된 모델 개발**과 **실시간 변화 탐지 시스템 구축**도 중요한 연구 방향입니다.  **다양한 지리적 위치와 시간적 변화 패턴에 대한 모델 일반화 능력 향상**을 위한 연구도 필요합니다.  마지막으로, **변화 탐지 결과의 신뢰도를 높이기 위한 불확실성 추정 및 오류 분석**에 대한 연구가 추가적으로 필요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.13407/extracted/6215536/pic/dataset-class.png)

> 🔼 그림 2는 JL1-CD 데이터셋의 샘플 이미지들을 보여줍니다. 각 행은 위에서부터 순서대로 시간 1의 이미지, 시간 2의 이미지, 그리고 정답 레이블을 나타냅니다. 각 열은 서로 다른 유형의 변화를 보여주는데, (a)는 삼림 감소, (b)는 건물 변화, (c)는 농경지에서 온실로의 전환, (d)는 도로 변화, (e)는 수역 변화, (f)는 중앙 지역의 지표면 경화를 나타냅니다.  이 그림은 다양한 유형의 변화와 각 변화의 시각적 특징을 보여주어 JL1-CD 데이터셋의 다양성과 포괄성을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Sample images from the JL1-CD dataset. Each row, from top to bottom, represents: the image at time 1, the image at time 2, and the ground truth label. Each column corresponds to different change types: (a) Decrease in woodland; (b) Building changes; (c) Conversion of cropland to greenhouses; (d) Road changes; (e) Waterbody changes; and (f) Surface hardening (central region).
> </details>



![](https://arxiv.org/html/2502.13407/extracted/6215536/pic/pipeline.png)

> 🔼 그림 3은 제안된 원본-분할(O-P) 전략과 다중 교사 지식 증류(MTKD) 프레임워크의 학습(녹색 상자) 및 테스트(분홍색 상자) 파이프라인 개요를 보여줍니다.  O-P 전략은 변화 영역 비율(CAR)을 기반으로 데이터셋을 분할하여 다양한 CAR 시나리오에 맞춰 모델을 학습시키는 방법입니다.  이렇게 학습된 모델들은 MTKD 프레임워크에서 교사 모델로 사용됩니다.  MTKD 프레임워크는 여러 교사 모델의 강점을 학습하여 추론 속도를 높이면서 정확도를 높이는 학생 모델을 학습하는 방법입니다.  그림은 O-P 전략과 MTKD 프레임워크의 각 단계(데이터 분할, 모델 학습, 학생 모델 학습 등)와  테스트 파이프라인을 자세히 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Overview of the training (green boxes) and testing (pink boxes) pipelines of the proposed Origin-Partition (O-P) strategy and Multi-Teacher Knowledge Distillation (MTKD) framework.
> </details>



![](https://arxiv.org/html/2502.13407/extracted/6215536/pic/dataset.png)

> 🔼 그림 4는 다양한 변화 면적 비율(CAR)을 가진 표본 이미지들을 보여줍니다. 각 열은 특정 CAR 값(a) 0.00%, (b) 19.98%, (c) 39.93%, (d) 59.96%, (e) 80.25%, (f) 100.00%)을 나타내는 이미지들을 보여줍니다. 이 그림은 변화 탐지 모델의 성능을 평가하기 위한 다양한 CAR 수준의 데이터를 JL1-CD 데이터셋이 포함하고 있음을 시각적으로 보여주기 위해 사용되었습니다.  각 이미지는 변화가 없는 영역부터 완전히 변화된 영역까지 다양한 변화의 정도를 보여줍니다. 이는 변화 탐지 모델이 다양한 CAR 조건에서 얼마나 잘 작동하는지 평가하는데 중요한 요소입니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Sample images with different change area ratios (CAR). Each column represents a specific CAR: (a) 0.00%; (b) 19.98%; (c) 39.93%; (d) 59.96%; (e) 80.25%; and (f) 100.00%.
> </details>



![](https://arxiv.org/html/2502.13407/extracted/6215536/pic/CAP.png)

> 🔼 JL1-CD 데이터셋의 훈련, 검증 및 테스트 세트에 대한 변화 면적 비율(CAR) 분포를 보여주는 그림입니다.  x축은 CAR 값(0에서 1 사이의 값으로, 0은 변화가 없음을, 1은 완전한 변화를 나타냄)을 나타내고, y축은 각 CAR 값에 해당하는 이미지 쌍의 개수를 나타냅니다.  각 막대는 특정 CAR 범위에 속하는 이미지 쌍의 수를 나타내며, 전체적으로 CAR 값의 분포를 확인할 수 있습니다.  이를 통해 JL1-CD 데이터셋 내 변화의 다양성과 난이도를 파악하는데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: CAR distribution of the training, validation and test sets in JL1-CD.
> </details>



![](https://arxiv.org/html/2502.13407/extracted/6215536/pic/CAP-SYSUCD.png)

> 🔼 그림 6은 SYSU-CD 데이터셋의 훈련 및 테스트 세트에 대한 CAR(변화 면적 비율) 분포를 보여줍니다.  x축은 CAR 값(0에서 1 사이의 값으로, 0은 변화가 없고 1은 완전한 변화를 나타냄)이고, y축은 각 CAR 값에 해당하는 이미지 쌍의 개수입니다. 히스토그램을 통해 훈련 및 테스트 세트에서 다양한 CAR 값을 가진 이미지 쌍의 분포를 파악할 수 있습니다.  이 분포는 모델의 성능 평가 및 일반화 능력을 이해하는 데 중요한 정보를 제공합니다. 특히, 특정 CAR 범위에 편향된 데이터 분포는 모델의 학습에 영향을 미칠 수 있기 때문에, 이러한 분포를 파악하는 것은 중요합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: CAR distribution of the training and test sets in SYSU-CD.
> </details>



![](https://arxiv.org/html/2502.13407/extracted/6215536/pic/visual.png)

> 🔼 그림 7은 JL1-CD 데이터셋에 대한 시각적 비교 결과를 보여줍니다. 각 행은 위에서부터 순서대로 시간 1의 이미지, 시간 2의 이미지, 정답, 원본 모델의 출력, O-P 전략의 출력, MTKD 프레임워크의 출력을 나타냅니다. 빨간색은 누락된 검출(FN, false negative)을, 파란색은 오경보(FP, false positive)를 나타냅니다. 선택된 알고리즘은 (a) BAN-ViT-L, (b) BIT, (c) TTP, (d) SNUNet, (e) IFN, (f) Changer-MiT-b1, (g) ChangeFormer-MiT-b1, (h) TinyCD, (i) CGNet입니다.  이 그림은 다양한 알고리즘들이 JL1-CD 데이터셋의 다양한 변화 영역을 얼마나 잘 감지하고 오류를 범하는지를 시각적으로 보여주는 대표적인 예시들을 제시합니다. 각 알고리즘의 성능을 정량적으로 비교하기 위한 표와 함께 해석해야 더욱 효과적입니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Visual comparison on the JL1-CD dataset. Each row, from top to bottom, represents the following: image at time 1, image at time 2, ground truth, output from the original model, output from the O-P strategy, and output from the MTKD framework. Red denotes missed detections (FN), while blue indicates false alarms (FP). The selected algorithms are: (a) BAN-ViT-L, (b) BIT, (c) TTP, (d) SNUNet, (e) IFN, (f) Changer-MiT-b1, (g) ChangeFormer-MiT-b1, (h) TinyCD, and (i) CGNet.
> </details>



![](https://arxiv.org/html/2502.13407/extracted/6215536/pic/CAR_per_Partition.png)

> 🔼 그림 8은 다양한 CAR(변화 면적 비율) 범위에 걸쳐 HANet, ChangeFormer-MiT-b1 및 TTP 세 가지 모델의 mIoU(Intersection over Union) 성능을 보여줍니다. 상단 두 행은 검증 세트에 대한 결과를, 하단 두 행은 테스트 세트에 대한 결과를 나타냅니다. 각 그래프의 왼쪽 y축은 CAR 크기를, 오른쪽 y축은 mIoU 값을 나타냅니다. 이 그림은 제안된 O-P 전략 및 MTKD 프레임워크가 다양한 CAR 범위의 이미지에 대해 어떻게 모델 성능을 향상시키는지 보여주는 시각적 증거를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: mIoU of HANet, ChangeFormer-MiT-b1, and TTP across different CAR ranges. The first and second rows show results on the validation and test sets, respectively. In each plot, the left y-axis represents CAR size, and the right y-axis represents mIoU.
> </details>



![](https://arxiv.org/html/2502.13407/extracted/6215536/pic/visual_sysucd.png)

> 🔼 그림 9는 SYSU-CD 데이터셋에서 다양한 변화 감지 모델의 성능을 시각적으로 비교한 것입니다. 빨간색은 미탐지(FN), 파란색은 오탐지(FP)를 나타냅니다.  (a)는 1차 이미지, (b)는 2차 이미지, (c)는 정답 마스크를 보여줍니다.  (d)~(i)는 각각 Changer-MiT-b1 (원본), Changer-MiT-b1 (MTKD 적용), CGNet (원본), CGNet (MTKD 적용), TTP (원본), TTP (MTKD 적용) 모델의 결과를 보여주는 이미지입니다. 각 모델의 변화 감지 결과를 정답과 비교하여 미탐지 및 오탐지 영역을 시각적으로 확인할 수 있도록 하였습니다. 이를 통해 각 모델의 장단점 및 MTKD 기법의 효과를 직관적으로 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Visual comparison on the SYSU-CD dataset. Red denotes missed detections (FN). Blue indicates false alarms (FP). (a) Image at Time 1. (b) Image at Time 2. (c) Ground Truth. (d) Changer-MiT-b1 (Original). (e) Changer-MiT-b1 (MTKD). (f) CGNet (Original). (g) CGNet (MTKD). (h) TTP (Original). (i) TTP (MTKD).
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Resolution |
|---|---| 
| 952 × 640 | 
| 1,048 × 724 |{{< /table-caption >}}
> 🔼 표 II는 논문에서 사용된 벤치마크 방법과 구현 세부 정보를 보여줍니다.  각 방법의 백본 네트워크, 파라미터 수, 연산량(FLOPs), 초기 학습률, 스케줄러, 배치 크기, GPU 정보 등을 포함하여 자세한 구현 사항을 제시합니다. 이를 통해 다양한 모델의 성능 비교를 위한 공정한 기준을 마련하고, 실험 결과의 신뢰성을 높이는 데 기여합니다.
> <details>
> <summary>read the caption</summary>
> TABLE II: Benchmark Methods and the Corresponding Implementation Details
> </details>

{{< table-caption >}}
| Method | Backbone | Param (M) | Flops (G) | Initial LR | λ | Scheduler | Batch Size | GPU |
|---|---|---|---|---|---|---|---|---|
| FC-EF<sup>[10]</sup> | CNN | 1.353 | 12.976 | 1e-3 | - | LinearLR | 8 | 3090 |
| FC-Siam-Conc<sup>[10]</sup> | CNN | 1.548 | 19.956 | 1e-3 | - | LinearLR | 8 | 3090 |
| FC-Siam-Diff<sup>[10]</sup> | CNN | 1.352 | 17.540 | 1e-3 | - | LinearLR | 8 | 3090 |
| STANet-Base<sup>[32]</sup> | ResNet-18 | 12.764 | 70.311 | 1e-3 | 5e-3 | LinearLR | 8 | 3090 |
| IFN<sup>[31]</sup> | VGG-16 | 35.995 | 323.584 | 1e-3 | 1e-4 | LinearLR | 8 | 3090 |
| SNUNet-c16<sup>[33]</sup> | CNN | 3.012 | 46.921 | 1e-3 | 1e-4 | LinearLR | 8 | 3090 |
| BIT<sup>[38]</sup> | ResNet-18 | 2.990 | 34.996 | 1e-3 | 1e-4 | LinearLR | 8 | 3090 |
|  | FarSeg (ResNet-18)<sup>[51]</sup> | 16.965 | 76.845 | 1e-3 | 1e-3 | LinearLR | 16 | 3090 |
| ChangeStar<sup>[34]</sup> | UPerNet (ResNet-18)<sup>[52]</sup> | 13.952 | 55.634 | 1e-3 | 1e-4 | LinearLR | 8 | 3090 |
|  | MiT-b0 | 3.847 | 11.380 | 6e-5 | 1e-3 | LinearLR | 8 | 3090 |
| ChangeFormer<sup>[13]</sup> | MiT-b1 | 13.941 | 26.422 | 6e-5 | 5e-4 | LinearLR | 8 | 3090 |
| TinyCD<sup>[36]</sup> | CNN | 0.285 | 5.791 | 3.57e-3 | 1e-5 | LinearLR | 8 | 3090 |
| HANet<sup>[35]</sup> | CNN | 3.028 | 97.548 | 1e-3 | 1e-3 | LinearLR | 8 | A800 |
|  | MiT-b0 | 3.457 | 8.523 | 1e-4 | 1e-4 | LinearLR | 8 | 3090 |
|  | MiT-b1 | 13.355 | 23.306 | 1e-4 | 1e-3 | LinearLR | 8 | 3090 |
|  | ResNet-18 | 11.391 | 23.820 | 5e-3 | 1e-3 | LinearLR | 8 | 3090 |
| Changer<sup>[14]</sup> | ResNeSt-50 | 26.693 | 67.241 | 5e-3 | 1e-5 | LinearLR | 8 | 3090 |
| LightCDNet-s<sup>[37]</sup> | CNN | 0.342 | 6.995 | 3e-3 | 5e-3 | LinearLR | 8 | 3090 |
| CGNet<sup>[11]</sup> | VGG-16 | 38.989 | 425.984 | 5e-4 | 1e-3 | LinearLR | 8 | A800 |
|  | ViT-B | 91.346 | 74.409 | 1e-4 | - | LinearLR | 8 | 3090 |
|  | ViT-B (IN21K) | 115.712 | 83.142 | 1e-4 | - | LinearLR | 8 | 3090 |
| BAN<sup>[19]</sup> | ViT-L | 261.120 | 346.112 | 1e-4 | 1e-3 | LinearLR | 8 | A800 |
| TTP<sup>[21]</sup> | SAM<sup>[17]</sup> | 361.472 | 929.792 | 4e-4 | 5e-3 | CosineAnnealingLR | 8 | A800 |{{< /table-caption >}}
> 🔼 표 III은 논문에서 제시된 JL1-CD 데이터셋의 테스트 결과를 보여줍니다.  각 모델의 성능을 Origin, O-P 전략, MTKD 프레임워크 세 가지 방법으로 비교 분석하여 mIoU, mAcc, mPrecision, mFscore 지표를 제시합니다.  이는 JL1-CD 데이터셋에 대한 다양한 변화 감지 모델의 성능을 종합적으로 평가한 결과를 담고 있습니다.
> <details>
> <summary>read the caption</summary>
> TABLE III: Experimental Results on JL1-CD Test Set
> </details>

{{< table-caption >}}
Method|Strategy|mIoU|mAcc|mPrecision|mFscore|Method|Strategy|mIoU|mAcc|mPrecision|mFscore
---|---|---|---|---|---|---|---|---|---|---|---|---
STANet (Base)|-|66.76|81.71|74.73|74.73|IFN|-|71.25|78.91|84.53|77.33
STANet (Base)|O-P|64.56|78.47|**78.47**|71.25|IFN|O-P|71.06|78.37|84.28|77.21
STANet (Base)|MTKD|**67.92**|**82.07**|76.24|**75.10**|IFN|MTKD|**72.72**|**80.28**|**84.66**|**78.80**
SNUNet (c16)|-|68.97|74.87|**85.06**|75.25|BIT|-|67.22|74.47|83.71|73.37
SNUNet (c16)|O-P|**71.39**|**78.60**|83.36|**77.98**|BIT|O-P|**69.41**|**76.29**|84.02|**75.77**
SNUNet (c16)|MTKD|71.12|78.27|84.96|77.56|BIT|MTKD|68.86|75.49|**84.71**|74.88
ChangeStar (FarSeg)|-|**69.47**|75.58|84.46|**75.57**|ChangeStar (UPerNet)|-|64.85|69.18|**88.26**|70.19
ChangeStar (FarSeg)|O-P|68.87|74.74|**84.90**|74.86|ChangeStar (UPerNet)|O-P|64.68|69.05|87.23|70.08
ChangeStar (FarSeg)|MTKD|69.14|**76.49**|82.09|75.41|ChangeStar (UPerNet)|MTKD|**65.10**|**70.26**|87.69|**70.58**
ChangeFormer (MiT-b0)|-|**73.51**|**80.46**|86.33|**79.70**|ChangeFormer (MiT-b1)|-|73.05|79.70|86.95|79.22
ChangeFormer (MiT-b0)|O-P|72.58|79.16|86.33|78.79|ChangeFormer (MiT-b1)|O-P|73.45|79.19|**87.45**|79.41
ChangeFormer (MiT-b0)|MTKD|73.25|79.20|**87.15**|79.30|ChangeFormer (MiT-b1)|MTKD|**73.92**|**80.43**|86.89|**80.18**
TinyCD|-|71.04|78.77|83.05|77.74|HANet|-|63.64|69.77|83.43|69.39
TinyCD|O-P|72.22|79.93|**83.49**|78.76|HANet|O-P|**69.05**|**76.53**|83.05|**75.66**
TinyCD|MTKD|**72.55**|**80.98**|83.17|**79.26**|HANet|MTKD|67.67|74.39|**84.38**|73.92
Changer (MiT-b0)|-|74.85|**81.84**|86.09|80.98|Changer (MiT-b1)|-|75.94|81.99|**87.74**|81.93
Changer (MiT-b0)|O-P|75.29|81.40|87.06|**81.32**|Changer (MiT-b1)|O-P|75.42|81.67|87.13|81.43
Changer (MiT-b0)|MTKD|**75.35**|81.76|**87.18**|81.28|Changer (MiT-b1)|MTKD|**76.15**|**82.85**|86.98|**82.13**
Changer (r18)|-|68.37|75.15|83.43|74.54|Changer (s50)|-|62.31|69.23|80.91|67.83
Changer (r18)|O-P|**70.76**|**77.42**|**83.86**|**77.01**|Changer (s50)|O-P|**71.80**|**79.76**|**83.15**|**78.23**
Changer (r18)|MTKD|69.45|77.26|81.50|75.86|Changer (s50)|MTKD|62.96|69.65|81.76|68.52
LightCDNet (s)|-|66.70|73.21|83.45|72.46|CGNet|-|73.37|80.31|85.33|79.65
LightCDNet (s)|O-P|**70.19**|**77.43**|**83.99**|**76.16**|CGNet|O-P|72.95|79.71|85.50|79.12
LightCDNet (s)|MTKD|65.99|72.44|83.86|71.48|CGNet|MTKD|**73.82**|**80.32**|**86.33**|**79.91**
BAN (ViT-L)|-|73.54|79.54|87.89|79.47|TTP|-|75.05|80.24|**89.82**|80.76
BAN (ViT-L)|O-P|73.61|79.17|**88.10**|79.45|TTP|O-P|76.69|**83.48**|87.27|82.52
BAN (ViT-L)|MTKD|**73.95**|**80.26**|87.12|**79.92**|TTP|MTKD|**76.85**|82.99|88.05|**82.56**
BAN (ViT-B)|-|**73.30**|**80.36**|85.91|**79.47**|BAN (ViT-B-IN21K)|-|**74.69**|**81.09**|**87.14**|**80.75**
BAN (ViT-B)|O-P|72.47|78.78|**86.31**|78.58|BAN (ViT-B-IN21K)|O-P|73.50|79.98|86.25|79.50
FC-EF|-|**57.08**|**61.90**|86.40|**61.28**|FC-Siam-Conc|-|**63.79**|**69.54**|84.77|**69.19**
FC-EF|O-P|49.59|53.30|**95.54**|51.47|FC-Siam-Conc|O-P|60.25|63.84|**91.19**|64.72
FC-EF|FC-Siam-Diff|**61.30**|**66.03**|86.45|**66.34**|FC-Siam-Conc|FC-Siam-Diff|-|-|-|-|-|-|-|-|-|-{{< /table-caption >}}
> 🔼 표 IV는 변화 클래스와 비변화 클래스에 대한 검출 결과를 비교 분석한 표입니다.  각 알고리즘(IFN, SNUNet(c16), ChangeFormer(MiT-b0, MiT-b1), TinyCD, Changer(MiT-b0, MiT-b1), CGNet, BAN(ViT-L), TTP) 별로 변화 클래스와 비변화 클래스에 대한 IoU, 정확도, 정밀도, F1 점수 변화량을 보여줍니다.  이를 통해 각 알고리즘이 변화 영역과 비변화 영역을 얼마나 잘 식별하는지, 그리고 O-P 전략이나 MTKD 프레임워크 적용이 이러한 성능에 어떤 영향을 미치는지 비교 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> TABLE IV: Comparison of Detection Results on Change and No-Change Classes
> </details>

{{< table-caption >}}
| Method | Class | IoU | Acc | Precision | Fscore |
|---|---|---|---|---|---| 
|  | unchanged | +0.24 | +0.29 | +0.04 | +0.12 |
| IFN | changed | **+2.71** | **+2.44** | **+0.22** | **+2.82** |
|  | unchanged | +0.10 | -0.60 | **+0.65** | +0.06 |
| SNUNet<br>(c16) | changed | **+4.21** | **+7.38** | -0.86 | **+4.54** |
|  | unchanged | **+0.21** | **-0.02** | +0.24 | **+0.18** |
| ChangeFormer<br>(MiT-b0) | changed | -0.74 | -2.51 | **+1.41** | -0.99 |
|  | unchanged | +0.07 | +0.12 | **-0.01** | +0.05 |
| ChangeFormer<br>(MiT-b1) | changed | **+1.68** | **+1.35** | -0.11 | **+1.86** |
|  | unchanged | +0.30 | +0.29 | +0.08 | +0.20 |
| TinyCD | changed | **+2.72** | **+4.13** | **+0.16** | **+2.85** |
|  | unchanged | +0.21 | **+0.32** | -0.14 | +0.19 |
| Changer<br>(MiT-b0) | changed | **+0.80** | -0.48 | **+2.32** | **+0.41** |
|  | unchanged | +0.02 | +0.09 | **-0.04** | -0.01 |
| Changer<br>(MiT-b1) | changed | **+0.41** | **+1.63** | -1.47 | **+0.42** |
|  | unchanged | +0.02 | -0.03 | -0.04 | -0.06 |
| CGNet | changed | **+0.88** | **+0.03** | **+2.04** | **+0.59** |
|  | unchanged | +0.12 | +0.23 | **-0.09** | +0.07 |
| BAN<br>(ViT-L) | changed | **+0.70** | **+1.21** | -1.46 | **+0.82** |
|  | unchanged | +0.23 | -0.19 | **+0.45** | +0.20 |
| TTP | changed | **+3.36** | **+5.69** | -3.99 | **+3.39** |{{< /table-caption >}}
> 🔼 이 표는 O-P 전략과 MTKD 프레임워크에서 교사 모델의 수가 성능에 미치는 영향을 보여줍니다.  다양한 수의 교사 모델(2개 또는 3개)을 사용하여 O-P 전략과 MTKD 프레임워크를 적용했을 때,  Changer(MiT-b0, MiT-b1), CGNet, TTP 모델의 mIoU, mAcc, mPrecision, mFscore 지표를 비교 분석합니다.  각 모델과 전략 조합에 대한 성능 변화를 정량적으로 제시하여 교사 모델 수의 최적화 방안을 제시하고, MTKD 프레임워크의 강건성을 평가합니다.
> <details>
> <summary>read the caption</summary>
> TABLE V: Impact of Different Numbers of Teacher Models on O-P and MTKD Performance
> </details>

{{< table-caption >}}
| Method | Strategy | No. of ℳ<sub>T</sub> | mIOU | mAcc | mPrecision | mFscore |
|---|---|---|---|---|---|---|
|  |  | 3 | 75.29 (+0.44) | 81.40 (-0.44) | **87.06 (+0.97)** | 81.32 (+0.34) |
|  | O-P | 2 | **75.44 (+0.59)** | **81.96 (+0.12)** | 85.85 (-0.24) | **81.51 (+0.53)** |
|  |  | 3 | 75.35 (+0.50) | 81.76 (-0.08) | **87.18 (+1.09)** | 81.28 (+0.30) |
| Changer<br>(MiT-b0) | MTKD | 2 | **75.72 (+0.87)** | **82.30 (+0.46)** | 86.80 (+0.71) | **81.66 (+0.68)** |
|  |  | 3 | 75.42 (-0.52) | 81.67 (-0.32) | 87.13 (-0.61) | 81.43 (-0.50) |
|  | O-P | 2 | **75.91 (-0.03)** | **82.11 (+0.12)** | **87.87 (+0.13)** | **81.97 (+0.04)** |
|  |  | 3 | 76.15 (+0.21) | 82.85 (+0.86) | 86.98 (-0.76) | 82.13 (+0.20) |
| Changer<br>(MiT-b1) | MTKD | 2 | **76.77 (+0.83)** | **83.38 (+1.39)** | **87.30 (-0.44)** | **82.66 (+0.73)** |
|  |  | 3 | 72.95 (-0.42) | 79.71 (-0.60) | **85.50 (+0.17)** | 79.12 (-0.53) |
|  | O-P | 2 | **73.56 (+0.19)** | **80.76 (+0.45)** | 85.07 (-0.26) | **79.92 (+0.27)** |
|  |  | 3 | **73.82 (+0.45)** | 80.32 (+0.01) | **86.33 (+1.00)** | **79.91 (+0.26)** |
| CGNet | MTKD | 2 | 73.78 (+0.41) | **80.61 (+0.29)** | 85.67 (+0.34) | 79.89 (+0.24) |
|  |  | 3 | **76.69 (+1.64)** | **83.48 (+3.24)** | 87.27 (-2.55) | **82.52 (+1.76)** |
|  | O-P | 2 | 76.65 (+1.60) | 82.98 (+2.74) | **87.39 (-2.43)** | 82.49 (+1.73) |
|  |  | 3 | **76.85 (+1.80)** | 82.99 (+2.75) | **88.05 (-1.77)** | **82.56 (+1.80)** |
| TTP | MTKD | 2 | 76.31 (+1.26) | **83.24 (+3.00)** | 86.81 (-3.01) | 82.22 (+1.46) |{{< /table-caption >}}
> 🔼 표 VI는 논문의 실험 결과 부분에서 SYSU-CD 테스트 세트에 대한 다양한 모델과 전략의 성능을 보여줍니다.  각 모델(Changer(MiT-b1), CGNet, TTP)에 대해 원본, O-P 전략, MTKD 프레임워크 세 가지 경우의 mIoU, mAcc, mPrecision, mFscore 지표 값을 제시하여, 제안된 방법의 효과를 정량적으로 비교 분석합니다. SYSU-CD 데이터셋은 JL1-CD와는 다른 특징을 가지므로, 이 표는 제안된 방법의 일반화 성능을 평가하는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> TABLE VI: Experimental Results on SYSU-CD Test Set
> </details>

</details>




### Full paper

{{< gallery >}}
<img src="paper_images/1.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/2.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/3.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/4.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/5.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/6.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/7.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/8.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/9.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/10.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/11.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/12.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/13.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/14.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
{{< /gallery >}}