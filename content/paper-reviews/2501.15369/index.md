---
title: "iFormer: Integrating ConvNet and Transformer for Mobile Application"
summary: "iFormer는 모바일 비전 애플리케이션을 위해 CNN과 Transformer의 장점을 결합한 새로운 하이브리드 아키텍처입니다.  ImageNet 분류에서 최첨단 성능을 달성했으며,  다양한 하드웨어에서 낮은 지연 시간을 유지합니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Classification", "🏢 Tsinghua University",]
showSummary: true
date: 2025-01-26
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.15369 {{< /keyword >}}
{{< keyword icon="writer" >}} Chuanyang Zheng et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-28 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.15369" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.15369" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/iformer-integrating-convnet-and-transformer" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

모바일 기기의 제한된 자원으로 인해 실시간 비전 애플리케이션 개발에 어려움이 있습니다. 기존 CNN은 지역적 특징 추출에 효과적이지만, 전역적 정보 처리에는 한계가 있으며, Transformer는 전역적 정보 처리에 뛰어나지만, 계산량이 많아 모바일 환경에 적합하지 않습니다. 따라서 기존 CNN과 Transformer의 장점만을 결합하여 효율적인 모바일 비전 네트워크를 설계하는 것이 중요합니다. 

본 연구에서는 이러한 문제를 해결하기 위해 CNN과 Transformer를 효과적으로 통합한 새로운 하이브리드 아키텍처인 iFormer를 제안합니다. iFormer는 경량화된 CNN을 기반으로 설계되어 낮은 지연 시간을 유지하며, 효율적인 모바일 모듈화 어텐션(SHMA) 메커니즘을 도입하여 동적인 전역 표현 능력을 향상시켰습니다.  ImageNet-1k 이미지 분류 작업에서 최첨단 성능을 달성했을 뿐만 아니라,  객체 탐지, 인스턴스 분할, 의미 분할 등 다양한 downstream 작업에서도 우수한 성능을 보였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} iFormer는 CNN과 Transformer의 장점을 통합하여 모바일 환경에서 속도와 정확성을 동시에 향상시켰습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} ImageNet-1k 분류 작업에서 경쟁력 있는 성능을 달성했으며, 모바일 기기에서 1.10ms의 낮은 지연 시간을 기록했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 객체 탐지, 인스턴스 분할, 의미 분할 등 다양한 downstream 작업에서도 우수한 성능을 보였습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **모바일 환경에서의 실시간 비전 애플리케이션을 위한 경량화된 뉴럴 네트워크 설계**에 중요한 의미를 지닙니다. **기존 CNN과 Transformer의 장점을 결합한 새로운 하이브리드 아키텍처**를 제시함으로써, 속도와 정확성 측면에서 뛰어난 성능을 보여줍니다. 이는 모바일 기기의 성능 제약을 극복하고 다양한 비전 작업에 적용 가능한 혁신적인 기술로, **모바일 비전 분야의 연구 방향**에 큰 영향을 미칠 것으로 예상됩니다. 또한, 제안된 방법은 향후 **다양한 하드웨어 플랫폼에 대한 최적화 연구** 및 **더욱 정교한 모델 개발**을 위한 새로운 가능성을 제시합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.15369/x1.png)

> 🔼 그림 1은 ImageNet-1k 데이터셋을 사용하여 iFormer와 다른 기존 경량화 모델들의 지연 시간과 정확도를 비교한 것입니다. iPhone 13에서 측정한 지연 시간을 기준으로, iFormer는 다른 모델들보다 우수한 성능을 보이며 Pareto 최적점에 위치하고 있음을 보여줍니다.  즉, 지연 시간을 더 줄이지 않고도 정확도를 더 높일 수 있는 성능을 의미합니다.  다양한 모델들의 지연 시간과 정확도를 비교하여 iFormer의 우수성을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Comparison of latency and accuracy between our iFormer and other existing methods on ImageNet-1k. The latency is measured on an iPhone 13. Our iFormer is Pareto-optimal.
> </details>





{{< table-caption >}}
| Models | Latency (ms) | Top-1 Acc. (%) |
|---|---|---|
| MHA Baseline | 1.40 | 79.9 |
| SHA Baseline | 1.12 (1.25×) | 79.8 |{{< /table-caption >}}

> 🔼 이 표는 논문의 3.3절 Single Head Modulation Attention에서 다루는 내용으로, 멀티-헤드 어텐션(MHA) 기반의 기준 모델과 싱글-헤드 어텐션(SHA) 기반의 기준 모델 간의 지연 시간(Latency) 및 Top-1 정확도(Accuracy)를 비교 분석한 결과를 보여줍니다.  MHA는 멀티-헤드 메커니즘으로 인해 추가적인 연산 및 메모리 접근이 필요하여 지연 시간이 길어지는 반면, SHA는 연산량이 적어 지연 시간을 단축시킬 수 있다는 점을 보여주는 실험 결과입니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Latency comparison between multi-head and single-head baseline.
> </details>





### In-depth insights


#### MobileNet Enhancements
모바일 환경에 최적화된 모델 개발에 있어 MobileNet의 향상은 **경량화**와 **효율성** 개선에 초점을 맞춥니다.  이는 연산량 감소를 위한 네트워크 구조의 변형,  **메모리 접근 최소화**를 위한 효율적인 연산 기법 도입, 그리고 **정확도 저하 최소화**를 위한 학습 전략 개선 등을 포함합니다. 특히, MobileNet의 주요 특징인 depthwise separable convolution을 기반으로 한 추가적인 최적화 기법들은 **모델 크기와 연산 속도**를 획기적으로 개선하는 데 중요한 역할을 합니다.  **하드웨어 가속**을 위한 설계 또한 중요하며, 이를 통해 모바일 기기에서의 실시간 처리 성능을 높일 수 있습니다.  **에너지 효율** 또한 중요한 고려 사항이며, 이를 위해 MobileNet의 연산량과 메모리 사용량을 최소화하는 것이 필수적입니다.  결론적으로, MobileNet 향상 연구는 **모바일 비전 시스템**의 성능과 효율성을 크게 높이는 데 기여합니다.

#### Hybrid Network Design
하이브리드 네트워크 설계는 **합성곱 신경망(CNN)**의 우수한 지역적 특징 추출 능력과 **트랜스포머(Transformer)**의 효율적인 전역적 모델링 기능을 결합하여 장점을 극대화하고 단점을 최소화하는 것을 목표로 합니다. 이는 모바일 환경과 같은 제한된 리소스 환경에서 성능과 효율성을 동시에 높이기 위한 중요한 전략입니다.  **CNN 기반의 초기 계층은 고해상도 입력에 대해 효율적으로 지역적 특징을 추출**하고, **Transformer 기반의 후기 계층은 저해상도 특징 맵을 사용하여 전역적 정보를 효율적으로 모델링**합니다. 이러한 하이브리드 접근 방식은 각 아키텍처의 강점을 활용하여 전체 네트워크의 성능을 향상시키는 동시에 계산량과 메모리 사용량을 줄입니다.  **모바일 어플리케이션에 최적화**하기 위해서는 연산량을 최소화하는 경량화된 CNN과 Transformer 아키텍처가 사용됩니다.  **메모리 효율적인 어텐션 메커니즘**을 적용하거나, **계층적 구조**를 통해 연산량을 분산시키는 등의 기술이 활용될 수 있습니다.  **모듈화된 설계**를 통해 다양한 모바일 기기 환경에 맞춰 네트워크를 유연하게 조정할 수 있습니다.

#### Efficient Attention
 효율적인 어텐션 메커니즘은 **계산 복잡도를 줄이고 속도를 높이는 데 중점**을 둡니다.  이는 특히 모바일이나 임베디드 시스템과 같은 제한된 자원 환경에서 중요합니다.  **기존의 어텐션 메커니즘은 계산량이 많아 처리 시간이 오래 걸리기 때문에** 효율적인 어텐션 메커니즘이 필요합니다.  본 논문에서 제시된 효율적인 어텐션 기법들은 **메모리 사용량 감소, 연산 속도 향상** 등의 장점을 제공하며, 다양한 비전 작업에서 우수한 성능을 보여줍니다.  **특히, 멀티-헤드 어텐션의 계산 비용을 줄이기 위한 다양한 기법들이 제시**되었으며, 이는 **모바일 환경에서의 실시간 처리를 가능하게 하는 데 중요한 역할**을 합니다.  **단일 헤드 어텐션이나 변형된 어텐션 메커니즘을 통해 효율성을 극대화**하면서 정확도 저하를 최소화하는 방안 또한 제시됩니다.  **이러한 효율적인 어텐션 메커니즘들은 모바일 비전 어플리케이션의 성능 향상에 크게 기여**할 것으로 예상됩니다.

#### Downstream Tasks
논문에서 다룬 다운스트림 작업(Downstream Tasks) 부분은 제시된 **iFormer 모델의 성능을 이미지 분류 외 다양한 비전 작업에서 평가**하기 위한 중요한 부분입니다.  **객체 탐지, 인스턴스 분할, 의미 분할과 같은 과제**에서 iFormer의 효율성과 정확성을 확인하고, 모바일 환경에서의 실시간 처리 가능성을 보여주는 실험 결과를 제시했을 것입니다.  이는 단순히 이미지 분류 성능만으로는 알 수 없는 **모델의 일반화 능력과 실용성을 보여주는 핵심적 증거**가 됩니다. 특히, 높은 해상도의 이미지를 처리하면서도 낮은 지연 시간을 유지하는 iFormer의 능력은 다운스트림 작업의 성능에 큰 영향을 미치며, **모바일 기기에서의 실시간 응용 가능성을 높이는 중요한 요소**임을 시사합니다.  따라서 다운스트림 작업에 대한 분석은 iFormer 모델의 실제 활용 가능성을 판단하는 데 매우 중요한 부분입니다.

#### Future Work
본 논문은 모바일 환경에 최적화된 경량화된 비전 트랜스포머인 iFormer를 제안합니다. **향후 연구 방향**으로는 다음과 같은 내용을 생각해 볼 수 있습니다. 첫째, **다양한 모바일 기기 및 하드웨어 플랫폼에 대한 최적화**를 통해 더욱 폭넓은 적용성을 확보하는 연구가 필요합니다. 둘째, **고해상도 이미지 처리 성능 향상**을 위한 효율적인 메커니즘 개발이 중요합니다.  현재의 window attention 방식은 메모리 사용량 측면에서 여전히 개선 여지가 있기 때문입니다.  셋째, **더욱 다양한 downstream task** (예: 비디오 분석, 3D 비전 등)에 대한 적용성을 확장하는 연구가 필요합니다.  넷째, **에너지 효율성**을 더욱 높이기 위한 연구가 필요합니다.  마지막으로, **모델의 훈련 및 최적화 전략**을 더욱 개선하여 성능과 효율성을 동시에 향상시키는 연구가 중요합니다.  이러한 방향으로 연구가 진행된다면 iFormer는 모바일 비전 분야에서 더욱 중요한 역할을 수행할 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.15369/x2.png)

> 🔼 그림 2는 일반적인 ConvNeXt 네트워크에서 경량화된 iFormer 네트워크로의 발전 과정을 보여줍니다. 주황색 막대는 모델의 정확도(Top-1 Accuracy)를, 연한 파란색 막대는 모델의 지연 시간(Latency)을 나타냅니다. 빨간색 점선은 지연 시간을 더욱 명확하게 보여주기 위한 가이드라인입니다. ConvNeXt를 기반으로, 여러 단계의 최적화를 거치면서 정확도를 유지하거나 향상시키면서 지연 시간을 줄여나가는 과정을 시각적으로 보여줍니다. 각 단계별 최적화 기법(예: 초기 컨볼루션 개선, 정규화 방식 변경, 네트워크 심화, 단계 비율 조정, 커널 크기 조정, 단일 헤드 변조 어텐션 사용, 위치 임베딩 추가 등)의 효과를 정확도와 지연 시간 변화를 통해 직관적으로 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Illustration of the evolution from the ConvNeXt baseline towards the lightweight iFormer. The orange bars are model accuracies and the light blue bars are model latencies. We also include a red latency outline for better visualization.
> </details>



![](https://arxiv.org/html/2501.15369/x4.png)

> 🔼 그림 4는 iFormer 아키텍처의 개요를 보여줍니다. iFormer는 효율적인 모바일 비전 애플리케이션을 위해 설계된 하이브리드 네트워크로, 빠른 지역적 표현 능력을 갖춘 합성곱 신경망(CNN)과 효율적인 전역 모델링 기능을 갖춘 자기 주의(self-attention) 메커니즘을 통합합니다. 그림은 iFormer의 구성 요소인 세부적인 합성곱 스템, 블록 디자인 및 SHMA(Single-Head Modulation Attention)을 보여줍니다. SHMA는 메모리 집약적인 재구성 연산을 제거하여 효율성을 높였으며, 쿼리와 키 채널 수를 줄이는 비율 R(iFormer에서는 2로 설정)을 사용합니다. 단순화를 위해 프로젝트 또는 합성곱 이후의 BN(Batch Normalization)은 생략되었습니다. 그림을 통해 iFormer의 아키텍처와 각 구성 요소의 상호 작용을 이해할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Overview of iFormer architecture, detailed convolutional stem, block design, and SHMA. The hatched area in SHMA indicates extra memory-intensive reshaping operations that are eliminated by SHMA. S⁢(⋅)𝑆⋅S(\cdot)italic_S ( ⋅ ) denotes the softmax function. R𝑅Ritalic_R is the ratio for reducing channels of query and key. It is set to 2 in iFormer. We omit BN following project or convolution for simplicity.
> </details>



![](https://arxiv.org/html/2501.15369/x5.png)

> 🔼 그림 5는 iFormer에서 제안하는 SHMA(Single-Head Modulation Attention)와 SHViT(Single-Head self-Attention)의 차이점을 보여줍니다. SHViT는 공간적 어텐션을 위해 입력 채널의 1/4.67만을 사용하는 반면, SHMA는 입력을 2배의 차원으로 투영하여 분할 및 연결 연산 없이 효율적인 어텐션을 수행합니다. 이는 모바일 환경에서 메모리와 연산량을 줄이는 데 효과적입니다. 그림은 두 방법의 구조적 차이를 명확하게 비교하여 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Comparison of SHMA and SHA in SHViT. In SHViT, r⁢C𝑟𝐶rCitalic_r italic_C channels are utilized for spatial attention, where r𝑟ritalic_r is set to 14.6714.67\frac{1}{4.67}divide start_ARG 1 end_ARG start_ARG 4.67 end_ARG. SHMA projects the input into a higher dimension of 1212\frac{1}{2}divide start_ARG 1 end_ARG start_ARG 2 end_ARGC (i.e., R=2) and avoids split and concatenation operations.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Kernel Size | Latency (ms) |
|---|---| 
| 3×3 | 1.00 |
| 7×7 | 1.01 |{{< /table-caption >}}
> 🔼 이 표는 다양한 크기의 합성곱 연산 커널을 사용했을 때의 지연 시간을 비교 분석한 결과를 보여줍니다.  모델의 효율성과 성능에 미치는 커널 크기의 영향을 이해하는 데 도움이 됩니다.  특히, 모바일 환경에서의 실시간 처리 성능 향상을 위한 최적의 커널 크기를 선택하는 데 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Latency under different convolutional kernel sizes.
> </details>

{{< table-caption >}}
| Model | Params (M) | GMACs | Latency (ms) | Reso. | Epochs | Top-1 (%) |
|---|---|---|---|---|---|---|
| MobileNetV2 1.0x (2018) | 3.4 | 0.30 | 0.73 | 224 | 500 | 72.0 |
| MobileNetV3-Large 0.75x (2019) | 4.0 | 0.16 | 0.67 | 224 | 600 | 73.3 |
| MNV4-Conv-S (2024) | 3.8 | 0.20 | 0.60 | 224 | 500 | 73.8 |
| **iFormer-T** | **2.9** | **0.53** | **0.60** | **224** | **300** | **74.1** |
| MobileNetV2 1.4x (2018) | 6.9 | 0.59 | 1.02 | 224 | 500 | 74.7 |
| MobileNetV3-Large 1.0x (2019) | 5.4 | 0.22 | 0.76 | 224 | 600 | 75.2 |
| SwiftFormer-XS (2023) | 3.5 | 0.60 | 0.95 | 224 | 300 | 75.7 |
| SBCFormer-XS (2024) | 5.6 | 0.70 | 0.79 | 224 | 300 | 75.8 |
| GhostNetV3 1.0x† (2024) | 6.1 | 0.17 | 0.99 | 224 | 600 | 77.1 |
| MobileOne-S2 (2023b) | 7.8 | 1.30 | 0.92 | 224 | 300 | 77.4 |
| RepViT-M1.0 (2024) | 6.8 | 1.10 | 0.85 | 224 | 300 | 78.6 |
| **iFormer-S** | **6.5** | **1.09** | **0.85** | **224** | **300** | **78.8** |
| EfficientMod-xxs (2024) | 4.7 | 0.60 | 1.29 | 224 | 300 | 76.0 |
| SBCFormer-S (2024) | 8.5 | 0.90 | 1.02 | 224 | 300 | 77.7 |
| MobileOne-S3 (2023b) | 10.1 | 1.90 | 1.16 | 224 | 300 | 78.1 |
| SwiftFormer-S (2023) | 6.1 | 1.00 | 1.12 | 224 | 300 | 78.5 |
| GhostNetV3 1.3x† (2024) | 8.9 | 0.27 | 1.24 | 224 | 600 | 79.1 |
| FastViT-T12 (2023a) | 6.8 | 1.40 | 1.12 | 256 | 300 | 79.1 |
| RepViT-M1.1 (2024) | 8.2 | 1.30 | 1.04 | 224 | 300 | 79.4 |
| MNV4-Conv-M (2024) | 9.2 | 1.00 | 1.08 | 256 | 500 | 79.9 |
| **iFormer-M** | **8.9** | **1.64** | **1.10** | **224** | **300** | **80.4** |
| Mobile-Former-294M (2022b) | 11.4 | 0.29 | 2.66 | 224 | 450 | 77.9 |
| MobileViT-S (2021) | 5.6 | 2.00 | 3.55 | 256 | 300 | 78.4 |
| MobileOne-S4 (2023b) | 14.8 | 2.98 | 1.74 | 224 | 300 | 79.4 |
| SBCFormer-B (2024) | 13.8 | 1.60 | 1.44 | 224 | 300 | 80.0 |
| GhostNetV3 1.6x† (2024) | 12.3 | 0.40 | 1.49 | 224 | 600 | 80.4 |
| EfficientViT-B1-r288 (2023) | 9.1 | 0.86 | 3.87 | 288 | 450 | 80.4 |
| FastViT-SA12 (2023a) | 10.9 | 1.90 | 1.50 | 256 | 300 | 80.6 |
| MNV4-Hybrid-M (2024) | 10.5 | 1.20 | 1.75 | 256 | 500 | 80.7 |
| SwiftFormer-L1 (2023) | 12.1 | 1.60 | 1.60 | 224 | 300 | 80.9 |
| EfficientMod-s (2024) | 12.9 | 1.40 | 2.57 | 224 | 300 | 81.0 |
| RepViT-M1.5 (2024) | 14.0 | 2.30 | 1.54 | 224 | 300 | 81.2 |
| **iFormer-L** | **14.7** | **2.63** | **1.60** | **224** | **300** | **81.9** |{{< /table-caption >}}
> 🔼 표 3은 ImageNet-1K 데이터셋을 사용한 이미지 분류 결과를 보여줍니다.  각 모델의 성능을 파라미터 수, 연산량(GMACS), 지연 시간(ms), 입력 이미지 해상도, 학습 에폭 수, 그리고 Top-1 정확도(%)를 기준으로 비교 분석했습니다.  † 표시는 재매개변수화, 지식 증류, 최적화 알고리즘 등 다양한 고급 학습 전략을 사용하여 학습된 모델임을 나타냅니다.  본 논문의 보충 자료 G절에 더 자세한 비교 결과가 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Classification results on ImageNet-1K. † indicates models that are trained with a variety of advanced training strategies including complex reparameterization, distillation, optimizer, and so on. We provide a more comprehensive comparison in Sec. G in the supplementary material.
> </details>

{{< table-caption >}}
| Model | Latency (ms) | Reso. | Epochs | Top-1 (%) |
|---|---|---|---|---|
| EfficientFormerV2-S1 (2023) | 1.02 | 224 | 300 | 79.0 |
| EfficientFormerV2-S1 (2023) | 1.02 | 224 | 450 | 79.7 |
| MobileViGv2-S* (2024) | 1.24 | 224 | 300 | 79.8 |
| FastViT-T12* (2023a) | 1.12 | 256 | 300 | 80.3 |
| RepViT-M1.1* (2024) | 1.04 | 224 | 300 | 80.7 |
| **iFormer-M** | **1.10** | 224 | 300 | **81.1** |
| SHViT-S4 (2024) | 1.48 | 224 | 300 | 80.2 |
| EfficientFormerV2-S2 (2023) | 1.60 | 224 | 300 | 81.6 |
| MobileViGv2-M (2024) | 1.70 | 224 | 300 | 81.7 |
| FastViT-SA12* (2023a) | 1.50 | 256 | 300 | 81.9 |
| EfficientFormerV2-S2 (2023) | 1.60 | 224 | 450 | 82.0 |
| RepViT-M1.5* (2024) | 1.54 | 224 | 300 | 82.3 |
| **iFormer-L** | **1.60** | 224 | 300 | **82.7** |{{< /table-caption >}}
> 🔼 표 4는 ImageNet-1K 데이터셋에서 지식 증류 기법을 사용하여 훈련된 모델들의 결과를 보여줍니다.  표에는 각 모델의 지연시간(ms), 이미지 해상도, 에폭 수, 그리고 Top-1 정확도(%)가 포함되어 있습니다.  '*' 표시는 재매개변수화와 같은 강력한 훈련 전략을 사용하여 훈련된 모델임을 나타냅니다.  이 표는 다양한 경량화 모델들의 성능을 비교하고 지식 증류가 모델 성능 향상에 미치는 영향을 분석하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Results with distillation on ImageNet-1K. * indicates the model is trained with a strong training strategy (i.e., reparameterization).
> </details>

{{< table-caption >}}
| Backbone | Param (M) | Latency (ms) | Object Detection AP<sup>box</sup> | AP<sup>box</sup><sub>50</sub> | AP<sup>box</sup><sub>75</sub> | Instance Segmentation AP<sup>mask</sup> | AP<sup>mask</sup><sub>50</sub> | AP<sup>mask</sup><sub>75</sub> | Semantic mIoU |
|---|---|---|---|---|---|---|---|---|---| 
| EfficientNet-B0 [2019] | 5.3 | 4.55 | 31.9 | 51.0 | 34.5 | 29.4 | 47.9 | 31.2 | - |
| ResNet18 [2016] | 11.7 | 2.85 | 34.0 | 54.0 | 36.7 | 31.2 | 51.0 | 32.7 | 32.9 |
| PoolFormer-S12 [2022] | 11.9 | 5.70 | 37.3 | 59.0 | 40.1 | 34.6 | 55.8 | 36.9 | 37.2 |
| EfficientFormer-L1 [2022b] | 12.3 | 3.50 | 37.9 | 60.3 | 41.0 | 35.4 | 57.3 | 37.3 | 38.9 |
| FastViT-SA12 [2023a] | 10.9 | 5.27 | 38.9 | 60.5 | 42.2 | 35.9 | 57.6 | 38.1 | 38.0 |
| RepViT-M1.1 [2024] | 8.2 | 3.18 | 39.8 | 61.9 | 43.5 | 37.2 | 58.8 | 40.1 | 40.6 |
| iFormer-M | 8.9 | 4.00 | 40.8 | 62.5 | 44.8 | 37.9 | 59.7 | 40.7 | 42.4 |
| ResNet50 [2016] | 25.5 | 7.20 | 38.0 | 58.6 | 41.4 | 34.4 | 55.1 | 36.7 | 36.7 |
| PoolFormer-S24 [2022] | 21.4 | 10.0 | 40.1 | 62.2 | 43.4 | 37.0 | 59.1 | 39.6 | 40.3 |
| ConvNeXt-T [2022] | 29.0 | 13.6 | 41.0 | 62.1 | 45.3 | 37.7 | 59.3 | 40.4 | 41.4 |
| EfficientFormer-L3 [2022b] | 31.3 | 8.40 | 41.4 | 63.9 | 44.7 | 38.1 | 61.0 | 40.4 | 43.5 |
| RepViT-M1.5 [2024] | 14.0 | 5.00 | 41.6 | 63.2 | 45.3 | 38.6 | 60.5 | 41.5 | 43.6 |
| PVTv2-B1 [2022] | 14.0 | 27.00 | 41.8 | 64.3 | 45.9 | 38.8 | 61.2 | 41.6 | 42.5 |
| FastViT-SA24 [2023a] | 20.6 | 8.97 | 42.0 | 63.5 | 45.8 | 38.0 | 60.5 | 40.5 | 41.0 |
| EfficientMod-S [2024] | 32.6 | 24.30 | 42.1 | 63.6 | 45.9 | 38.5 | 60.8 | 41.2 | 43.5 |
| Swin-T [2021a] | 28.3 | Failed | 42.2 | 64.4 | 46.2 | 39.1 | 61.6 | 42.0 | 41.5 |
| iFormer-L | 14.7 | 6.60 | 42.2 | 64.2 | 46.0 | 39.1 | 61.4 | 41.9 | 44.5 |{{< /table-caption >}}
> 🔼 표 5는 Mask R-CNN을 사용하여 MS COCO 2017 데이터셋에서 수행된 객체 탐지 및 인스턴스 분할 결과와 Semantic FPN 프레임워크를 사용하여 ADE20K 데이터셋에서 수행된 의미 분할 결과를 보여줍니다. 백본의 지연 시간은 iPhone 13에서 Core ML 툴을 사용하여 512x512 크기의 이미지를 처리하는 시간으로 측정했습니다. 'Failed'는 Core ML에서 모델 실행 시간이 너무 길어 지연 시간을 보고할 수 없음을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 5:  Object detection & instance segmentation results on MS COCO 2017 using Mask R-CNN. Semantic segmentation results on ADE20K using the Semantic FPN framework. We measure all backbone latencies with image crops of 512×\times×512 on iPhone 13 by Core ML Tools. Failed indicated that the model runs too long to report latency by the Core ML.
> </details>

{{< table-caption >}}
| SHMA Setting | Params (M) | GMACs | Latency (ms) | Top-1 Acc. (%) |
|---|---|---|---|---|
| SiLU + Post-BN | 8.9 | 1.60 | 1.10ms | Diverged |
| SiLU + Pre-LN | 8.9 | 1.64 | 1.17ms | 80.3 |
| Sigmoid + Post-BN | 8.9 | 1.60 | 1.10ms | 80.4 |{{< /table-caption >}}
> 🔼 이 표는 논문의 5장(Ablation Studies)에서 SHMA(Single-Head Modulation Attention)의 성능에 미치는 활성화 함수의 영향을 비교 분석한 결과를 보여줍니다.  Post-BN은 투영 후 배치 정규화(BN)를 적용한 경우이고, Pre-LN은 표준 MHA(Vaswani, 2017)처럼 투영 전 레이어 정규화(LN)를 적용한 경우를 나타냅니다.  다양한 활성화 함수(SiLU, Sigmoid)와 BN/LN 적용 위치의 조합에 따른 모델의 성능(매개변수 수, GMACs, 지연 시간, Top-1 정확도)을 비교하여 최적의 설정을 찾는 실험 결과를 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Activation function comparison in SHMA. Post-BN indicates that BN is applied after projection. Pre-LN means that LN is implemented before the projection, as in standard MHA (Vaswani, 2017).
> </details>

{{< table-caption >}}
| Ratio Setting | Params (M) | GMACs | Latency (ms) | Top-1 Acc. (%) |
|---|---|---|---|---|
| Baseline | 9.4M | 1760M | 1.0ms | 79.4 |
| Replacing 22% Conv Blocks in Stage 3 as SHA | 9.1M | 1724M | 1.02ms | 79.5 |
| Replacing 22% Conv Blocks in Stage 3 as SHMA | 9.2M | 1739M | 1.04ms | 79.6 |
| Replacing 50% Conv Blocks in Stage 3 as SHA | 8.8M | 1689M | 1.04ms | 79.5 |
| Replacing 50% Conv Blocks in Stage 3 as SHMA | 8.9M | 1712M | 1.07ms | 79.8 |
| Replacing 78% Conv Blocks in Stage 3 as SHA | 8.3M | 1635M | 1.12ms | 79.3 |
| Replacing 78% Conv Blocks in Stage 3 as SHMA | 8.5M | 1685M | 1.17ms | 79.6 |
| Replacing 100% Conv Blocks in Stage 3 as SHA | 7.9M | 1599M | 1.17ms | 78.1 |
| Replacing 100% Conv Blocks in Stage 3 as SHMA | 8.3M | 1665M | 1.25ms | 79.0 |
| Replacing 100% Conv Blocks in Stage 3 as SHMA and 100% in Stage 4 | 10.0M | 1792M | 1.15ms | 80.4 |{{< /table-caption >}}
> 🔼 이 표는 iFormer 모델의 성능에 대한 비교 분석 결과를 보여줍니다. 특히, ConvNeXt 기반 네트워크에서 ViT 블록의 비율을 다르게 적용했을 때의 정확도와 지연 시간의 변화를 보여줍니다.  ConvNeXt 네트워크의 일부 또는 전부를 새로 제안된 SHMA 블록으로 대체하여 네트워크의 효율성과 성능을 향상시키는 실험 결과가 담겨 있습니다.  각 열은 ViT 블록 대체 비율, 모델 크기, 연산량, 지연 시간, 그리고 ImageNet-1K 데이터셋에서의 Top-1 정확도를 나타냅니다. 이 표는 다양한 비율의 ViT 블록을 사용하는 iFormer 모델의 효율성과 정확도 간의 균형을 평가하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Different ratio of ViT Block.
> </details>

{{< table-caption >}}
| Model | Params (M) | GMACs (G) | Top-1 Acc. (%) |
|---|---|---|---|
| ConvNeXt-Base [2022] | 89 | 15.4 | 83.8 |
| TransNeXt-Base [2024] | 90 | 18.4 | 84.8 |
| iFormer-H (ours) | 99 | 15.5 | 84.8 |
| MaxViT-Base [2022] | 120 | 24.0 | 84.9 |{{< /table-caption >}}
> 🔼 표 8은 매개변수 99M개를 가진 더 큰 모델로 확장하는 결과를 보여줍니다.  기존의 경량 모델들과 비교하여 iFormer-H 모델의 성능과 효율성을 보여주는 표입니다.  특히, 계산량(GMACS) 대비 정확도(Top-1 Accuracy)를 비교하여 iFormer의 확장성 및 성능을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Scaling to the larger model with 99M parameters.
> </details>

{{< table-caption >}}
| Training Config             | iFormer-T/S/M/L/H |
|------------------------------|------------------|
| Resolution                  | 224<sup>2</sup>     |
| Weight Init                 | trunc. normal (0.2) |
| Optimizer                   | AdamW              |
| Base Learning Rate          | 4e-3 (T/S/M/L) 8e-3 |
| Weight Decay                | 0.05               |
| Optimizer Momentum          | β<sub>1</sub>,β<sub>2</sub>=0.9,0.999 |
| Batch Size                  | 4096 [T/S/M/L] 8192 [H] |
| Training Epochs             | 300                |
| Learning Rate Schedule      | cosine decay       |
| Warmup Epochs               | 20                 |
| Warmup Schedule             | linear             |
| Layer-wise LR Decay         | None                |
| Randaugment                 | (9, 0.5)           |
| Mixup                       | 0.8                |
| Cutmix                      | 1.0                |
| Random Erasing              | 0.25               |
| Label Smoothing             | 0.1                |
| Stochastic Depth            | 0.0 [T/S/M] 0.1 [L] 0.6 [H] |
| Layer Scale                 | None [T/S/M/L] 1e-6 [H] |
| Head Init Scale             | None                |
| Gradient Clip               | None                |
| Exp. Mov. Avg. (EMA)       | None                |{{< /table-caption >}}
> 🔼 표 9는 논문의 실험 설정 부분에서 ImageNet-1K 데이터셋을 이용한 이미지 분류 작업에 대한 학습 설정을 보여줍니다.  표에는 학습 해상도, 가중치 초기화 방법, 최적화 알고리즘, 학습률, 가중치 감쇠, 모멘텀, 배치 크기, 에폭 수, 학습률 조절 방식, 웜업 에폭, 데이터 증강 기법(RandAugment, Mixup, CutMix, Random Erasing), 레이블 스무딩, 확률적 심층화, 계층별 스케일링, 헤드 초기화 스케일, 그래디언트 클리핑, 지수 이동 평균(EMA) 등의 세부적인 학습 하이퍼파라미터들이 포함되어 있습니다. 이 표는 본 논문에서 사용된 ImageNet-1K 이미지 분류 모델 학습 과정을 명확히 이해하는데 필수적인 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 9: ImageNet-1K training settings.
> </details>

{{< table-caption >}}
| Reducing Setting | Params (M) | GMACs | Latency (ms) | Top-1 Acc. (%) |
|---|---|---|---|---|
| Baseline | 10.0 | 1.79 | 1.15 | 80.4 |
| Number of Blocks | 8.4 | 1.70 | 1.07 | 79.7 |
| FFN Width | 8.6 | 1.62 | 1.07 | 79.8 |
| Attn. Head and FFN Width | 8.9 | 1.64 | 1.10 | 80.2 |{{< /table-caption >}}
> 🔼 본 표는 모델의 지연 시간을 줄이기 위한 서로 다른 방법들을 비교 분석한 결과를 보여줍니다.  기준 모델(Baseline)을 바탕으로 블록 개수, FFN(Feed-Forward Network) 너비, 어텐션 헤드 수, FFN 확장 차원 등을 변화시켜가며 성능과 지연 시간의 변화를 측정하였습니다. 이를 통해 모델 경량화 과정에서 어떤 요소들이 지연 시간에 가장 큰 영향을 미치는지, 그리고 성능 저하를 최소화하면서 효율적으로 지연 시간을 줄이는 방법은 무엇인지를 알아볼 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Different ways for reducing latency.
> </details>

{{< table-caption >}}
| DW Conv in FFN | Params (M) | GMACs | Latency (ms) | Top-1 Acc. (%) |
|---|---|---|---|---|
| with | 9.6 | 1.83 | 1.43 | 80.5 |
| w/o. | 8.9 | 1.60 | 1.10 | 80.4 |{{< /table-caption >}}
> 🔼 표 11은 FFN(Feed-Forward Network)에 depthwise convolution을 적용했을 때와 적용하지 않았을 때의 성능 비교 결과를 보여줍니다.  depthwise convolution을 적용하면 연산량(FLOPs)이 14% 증가하고 지연 시간이 0.33ms 증가하지만, 정확도 향상은 미미합니다. 이는 depthwise convolution이 FFN의 성능 향상에 크게 기여하지 않음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 11: Comparison of FFN with and without depthwise convolution.
> </details>

{{< table-caption >}}
| Model | Params (M) | Latency (ms) | Reso. | Epochs | Top-1 (%) |
|---|---|---|---|---|---| 
| ConvNeXt-B (2022) | 89.0 | 7.54 | 224 | 300 | 83.8 |
| EfficientFormerV2-L (2023) | 26.1 | 2.40 | 224 | 450 | 83.5 |
| **iFormer-L2** | **24.5** | **2.30** | 224 | 450 | **83.9** |{{< /table-caption >}}
> 🔼 이 표는 ImageNet-1K 데이터셋에서 450 에폭 동안 증류(distillation) 기법을 사용하여 훈련한 모델들의 성능을 보여줍니다.  모델의 파라미터 수, 지연 시간(latency), 해상도, 에폭 수, 그리고 Top-1 정확도를 비교하여 모델의 효율성과 정확도를 종합적으로 평가합니다.  ConvNeXt-B, EfficientFormerV2-L과 iFormer-L2 모델의 결과를 보여주어 서로 다른 모델 아키텍처의 450 에폭 훈련 결과를 비교 분석하는 데 유용합니다.
> <details>
> <summary>read the caption</summary>
> Table 12: Training with distillation for 450 epochs on ImageNet-1K.
> </details>

{{< table-caption >}}
| Backbone | Param (M) | Latency (ms) | Pretrain Epochs | AP<sup>box</sup> | AP<sup>box</sup><sub>50</sub> | AP<sup>box</sup><sub>75</sub> | AP<sup>mask</sup> | AP<sup>mask</sup><sub>50</sub> | AP<sup>mask</sup><sub>75</sub> | Semantic mIoU |
|---|---|---|---|---|---|---|---|---|---|---|
| ResNet50 (2016) | 25.5 | 7.20 | 300 | 38.0 | 58.6 | 41.4 | 34.4 | 55.1 | 36.7 | 36.7 |
| PoolFormer-S24 (2022) | 21.4 | 12.30 | 300 | 40.1 | 62.2 | 43.4 | 37.0 | 59.1 | 39.6 | 40.3 |
| ConvNeXt-T (Liu et al., 2022) | 29.0 | 12.6 | 300 | 41.0 | 62.1 | 45.3 | 37.7 | 59.3 | 40.4 | 41.4 |
| EfficientFormer-L3 (2022b) | 31.3 | 8.40 | 300 | 41.4 | 63.9 | 44.7 | 38.1 | 61.0 | 40.4 | 43.5 |
| RepViT-M1.5 (2024) | 14.0 | 5.00 | 300 | 41.6 | 63.2 | 45.3 | 38.6 | 60.5 | 41.5 | 43.6 |
| PVTv2-B1 (2022) | 14.0 | 27.00 | 300 | 41.8 | 64.3 | 45.9 | 38.8 | 61.2 | 41.6 | 42.5 |
| FastViT-SA24 (2023a) | 20.6 | 8.97 | 300 | 42.0 | 63.5 | 45.8 | 38.0 | 60.5 | 40.5 | 41.0 |
| EfficientMod-S (2024) | 32.6 | 24.30 | 300 | 42.1 | 63.6 | 45.9 | 38.5 | 60.8 | 41.2 | 43.5 |
| Swin-T (2021a) | 28.3 | Failed | 300 | 42.2 | 64.4 | 46.2 | 39.1 | 61.6 | 42.0 | 41.5 |
| iFormer-L | 14.7 | 6.60 | 300 | 42.2 | 64.2 | 46.0 | 39.1 | 61.4 | 41.9 | 44.5 |
| EfficientFormerV2-L (2023) | 26.1 | 12.5 | 450 | 44.7 | 66.3 | 48.8 | 40.4 | 63.5 | 43.2 | 45.2 |
| iFormer-L2 | 24.5 | 9.06 | 450 | 44.6 | 66.7 | 49.1 | 41.1 | 64.0 | 44.1 | 46.2 |{{< /table-caption >}}
> 🔼 본 표는 ImageNet-1K 데이터셋에서 450 에폭 동안 사전 훈련된 백본 네트워크를 사용하여 Mask R-CNN 및 Semantic FPN 프레임워크로 수행된 객체 탐지 및 의미 분할 결과를 보여줍니다.  각 백본 모델에 대한 정밀도(APbox, APmask) 및 mIoU 지표와 함께 iPhone 13 기기에서 측정된 백본의 처리 속도(Latency)를 제시합니다.  이는 다양한 경량화 백본 모델들의 성능을 비교 분석하는 데 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 13:  Object detection & Semantic segmentation results using backbone pretrained for 450 epochs.
> </details>

{{< table-caption >}}
| Modification | Params(M) | GMACs | Latency (ms) | Top-1(%) |
|---|---|---|---|---|
| SHA Baseline without Modulation | 9.9M | 1758M | 1.12ms | 79.4 |
| + split | 9.9M | 1758M | 1.18ms | - |
| + attention on 1/4 channels | 8.3M | 1547M | 1.02ms | - |
| + concat | 8.7M | 1579M | 1.11ms | 79.5 |{{< /table-caption >}}
> 🔼 이 표는 iFormer에서 사용된 SHA(Single-Head self-Attention)를 SHViT(Single-Head Vision Transformer)의 SHA와 비교하여 변환 과정을 보여줍니다.  각 단계별로 모델의 매개변수 수, GMAC(giga multiply-accumulate operations), 지연 시간(ms), 그리고 ImageNet-1k 상위 1% 정확도를 측정했습니다.  중간 모델의 경우 지연 시간만 측정하였습니다. 이를 통해 SHA의 효율성과 SHViT와의 차이점을 정량적으로 분석하여 iFormer의 설계 방식을 보다 명확하게 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 14: Process of converting SHA in iFormer towards SHViT. Intermediate models are only measured by latency.
> </details>

{{< table-caption >}}
Stem | Output Size (Downs. Rate) | iFormer-T | iFormer-S | iFormer-M | iFormer-L
---|---|---|---|---|---
Stem | 56×56 (4×) | [Conv-BN-GELU 5×5 s2 d16] × 1 | [Conv-BN-GELU 5×5 s2 d16] × 1 | [Conv-BN-GELU 5×5 s2 d24] × 1 | [Conv-BN-GELU 5×5 s2 d24] × 1
 |  | [Conv-BN 5×5 s2 d64]
[Conv-BN 1×1 s1 d32] × 1 | [Conv-BN 5×5 s2 d64]
[Conv-BN 1×1 s1 d32] × 1 | [Conv-BN 5×5 s2 d96]
[Conv-BN 1×1 s1 d48] × 1 | [Conv-BN 5×5 s2 d96]
[Conv-BN 1×1 s1 d48] × 1
Stage 1 | 56×56 (4×) | [Conv-BN 7×7 s1 d32]
[Conv-BN-GELU 1×1 s1 d96]
Conv-BN 1x1 s1 d32 × 2 | [Conv-BN 7×7 s1 d32]
[Conv-BN-GELU 1×1 s1 d128]
Conv-BN 1x1 s1 d32 × 2 | [Conv-BN 7×7 s1d48]
[Conv-BN-GELU 1×1 s1 d192]
Conv-BN 1x1 s1 d48 × 2 | [Conv-BN 7×7 s1 d48]
[Conv-BN-GELU 1×1 s1 d192]
Conv-BN 1x1 s1 d48 × 2
Stage 2 | 28×28 (8×) | [Conv-BN 3×3 s2 d64] × 1 | [Conv-BN 3×3 s2 d64] × 1 | [Conv-BN 7×7 s1 d64]
[Conv-BN-GELU 1×1 s1 d192]
Conv-BN 1x1 s1 d64 × 2 | [Conv-BN 7×7 s1 d64]
[Conv-BN-GELU 1×1 s1 d256]
Conv-BN 1x1 s1 d64 × 2
Stage 3 | 14×14 (16×) | [Conv-BN 3×3 s2 d128] × 1 | [Conv-BN 3×3 s2 d176] × 1 | [Conv-BN 7×7 s1 d128]
[Conv-BN-GELU 1×1 s1 d384]
Conv-BN 1×1 s1 d128 × 6 | [Conv-BN 7×7 s1 d176]
[Conv-BN-GELU 1×1 s1 d704]
Conv-BN 1x1 s1 d176 × 9
Stage 4 | 7×7 (32×) | [Conv-BN 3×3 s2 d256] × 1 | [Conv-BN 3×3 s2 d320] × 1 | [Conv-BN 3×3 s2 d384] × 1 | [Conv-BN 3×3 s2 d384] × 1
 |  | [CPE 3×3]
SHMA hd64
FFN r2 × 2 | [CPE 3×3]
SHMA hd80
FFN r3 × 2 | [CPE 3×3]
SHMA hd96
FFN r3 × 2 | [CPE 3×3]
SHMA hd128
FFN r3 × 8
Params (M) |  | 2.9 | 6.5 | 8.9 | 14.7
GMacs |  | 0.53 | 1.09 | 1.64 | 2.63{{< /table-caption >}}
> 🔼 표 15는 논문의 iFormer 아키텍처 구성을 보여줍니다. 각 구성요소의 세부 정보와 하이퍼파라미터를 보여주는 상세한 표입니다.  BN(배치 정규화), SHMA(단일 헤드 변조 어텐션), DW(깊이 방향 합성곱)과 같은 약어가 사용되며, 합성곱 연산의 stride와 output 차원(s와 d), SHMA에서의 head 차원(hd), 그리고 FFN(피드 포워드 네트워크)에서의 확장 비율(r) 등이 포함되어 있습니다.  모든 변형에서 어텐션 헤드의 수는 1개이며, 각 변형의 주요 하이퍼파라미터가 명시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 15: iFormer architecture configurations. BN stands for Batch Normalization. SHMA stands for Singe-Head Modulation Attention. DW stands for Depthwise convolution. s and d means the stride and output dimension in convolution. hd denotes the head dimension in SHMA and the number of attention heads in all variants is 1. r means the expansion ratio in FFN.
> </details>

{{< table-caption >}}
| Output Size | (Downs. Rate) |
|---|---|{{< /table-caption >}}
> 🔼 표 16은 iFormer-M에서 사용된 서로 다른 어텐션 구조를 비교한 표입니다. 단순화를 위해 어텐션과 관련 없는 다른 블록들은 제외했습니다. ws는 윈도우 어텐션의 윈도우 크기를 나타냅니다. 이 표에서는 iFormer-M의 Stage 3과 Stage 4에서 사용된 기본 SHMA(Single-Head Modulation Attention),  SHMA에 위치 정보를 추가한 Hybrid SHMA, 그리고 SHMA에 윈도우 방식을 추가한 Chunk Hybrid SHMA의 성능을 비교하여 각 구조의 특징과 장단점을 보여줍니다. 각 구조의 매개변수 수, 연산량, 지연 시간, 그리고 ImageNet-1K 데이터셋에서의 정확도를 비교하여 어떤 어텐션 구조가 iFormer-M에 가장 적합한지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 16: Comparison of different attention designs in iFormer-M. For the sake of simplicity, we exclude other blocks that are not related to attention. ws is the window size for window attention.
> </details>

{{< table-caption >}}
Stage 3|Attention|SHMA|Hybrid SHMA|Chunk Hybrid SHMA
---|---|---|---|---
|14x14 (16x)|[CPE 3x3, Window Partitioning, ws16, Window SHMA hd96, ws16, FFN r3] x 1|[CPE 3x3, Chunk Window Partitioning, ws16, Window SHMA hd96, ws16, FFN r3] x 1
|[CPE 3x3, SHMA hd96, FFN r3] x 4|[CPE 3x3, Window SHMA hd96, ws16, FFN r3] x 2|[CPE 3x3, Window SHMA hd96, ws16, FFN r3] x 2
|[CPE 3x3, Window Reversing, ws16, SHMA hd96, FFN r3] x 1|[CPE 3x3, Chunk Window Reversing, ws16, SHMA hd96, FFN r3] x 1
Stage 4|Attention|SHMA|Hybrid SHMA|Chunk Hybrid SHMA
---|---|---|---|---
|7x7 (32x)|[CPE 3x3, Window Partitioning, ws16, Window SHMA hd96, FFN r3] x 1|[CPE 3x3, Chunk Window Partitioning, ws16, Window SHMA hd96, FFN r3] x 1
|[CPE 3x3, SHMA hd64, FFN r2] x 2|[CPE 3x3, Window Reversing, ws16, SHMA hd64, FFN r3] x 1|[CPE 3x3, Chunk Window Reversing, ws16, SHMA hd64, FFN r3] x 1{{< /table-caption >}}
> 🔼 표 17은 다양한 어텐션 메커니즘들의 지연 시간을 비교한 표입니다.  단순히 지연 시간만 비교하는 것이 아니라,  다양한 어텐션 방식(SHMA, Hybrid SHMA, Chunk Hybrid SHMA)을 512x512 해상도의 이미지에 적용했을 때의 성능을 보여줍니다.  이를 통해 각 어텐션 메커니즘의 효율성과 고해상도 이미지 처리에 대한 적합성을 비교 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 17: Latency comparison of different attention mechanisms.
> </details>

{{< table-caption >}}
| Attention | Resolution | Latency (ms) |
|---|---|---|
| SHMA | 224 | 1.10 |
| SHMA | 512 | Failed |
| Hybrid SHMA | 512 | 11.46 |
| CC Hybrid SHMA | 512 | 4.0 |{{< /table-caption >}}
> 🔼 표 18은 ImageNet-1K 데이터셋에서 iFormer와 기존 모델들의 성능을 비교한 결과를 보여줍니다.  모델의 매개변수 수, 연산량(GMACS), 지연 시간(ms), 이미지 해상도, 학습 에포크 수, 그리고 Top-1 정확도를 비교하여 iFormer의 효율성과 성능을 보여줍니다. 'Failed' 표시는 Core ML을 사용하여 측정했을 때 모델 실행 시간이 너무 길어 지연 시간을 측정할 수 없었음을 의미하며, 이는 과도한 메모리 접근으로 인한 것으로 추정됩니다.
> <details>
> <summary>read the caption</summary>
> Table 18: Comprehensive comparison between iFormer and the previously proposed models on ImageNet-1K.  Failed indicated that the model runs too long to report latency by the Core ML, often caused by excessive memory access.
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
<img src="paper_images/15.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/16.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/17.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/18.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/19.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/20.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
{{< /gallery >}}