---
title: "Parameter-Inverted Image Pyramid Networks for Visual Perception and Multimodal Understanding"
summary: "PIIP 네트워크: 고해상도 이미지 처리 효율 극대화!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Vision-Language Models", "🏢 Tsinghua University",]
showSummary: true
date: 2025-01-14
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.07783 {{< /keyword >}}
{{< keyword icon="writer" >}} Zhaokai Wang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-16 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.07783" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.07783" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/parameter-inverted-image-pyramid-networks-for" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 이미지 피라미드 방식은 고해상도 이미지를 처리할 때 계산 비용이 과도하게 증가하는 문제점을 가지고 있습니다.  또한, 기존의 멀티모달 모델들은 고해상도 이미지를 효율적으로 처리하지 못해 성능 향상에 제약이 있었습니다.  이러한 문제를 해결하기 위한 다양한 시도가 있었지만, 계산 비용과 성능 사이의 균형을 맞추는 데 어려움이 있었습니다.

본 논문에서는 이러한 문제를 해결하기 위해 **매개변수 반전 이미지 피라미드 네트워크(PIIP)**를 제안합니다. PIIP는 다양한 해상도의 이미지를 처리하기 위해 크기가 다른 사전 학습된 모델들을 사용하여 계산 비용을 줄이고 성능을 향상시킵니다.  또한, **다양한 비전 과제와 멀티모달 언어 모델에 PIIP를 적용**하여 실험을 진행했으며, **객체 탐지, 분할, 분류, 멀티모달 이해 등 다양한 작업에서 PIIP의 우수한 성능**을 확인했습니다.  PIIP는 **계산 효율성을 높이면서 성능 저하 없이 고해상도 이미지 처리가 가능**하도록 하여 컴퓨터 비전 및 멀티모달 이해 분야의 발전에 기여할 것으로 기대됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 계산 비용을 절감하면서도 성능 향상을 이룬 새로운 이미지 피라미드 네트워크(PIIP) 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 객체 탐지, 분할, 분류 등 다양한 컴퓨터 비전 작업에서 PIIP의 우수한 성능 검증 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 멀티모달 이해 모델에서도 PIIP의 효과적인 적용을 통해 성능 향상 확인 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **계산 비용을 줄이면서 성능을 향상시키는 새로운 이미지 피라미드 네트워크(PIIP)**를 제시하여 컴퓨터 비전 분야의 연구자들에게 중요한 의미를 가집니다.  **다양한 비전 모델과 멀티모달 모델에 적용 가능하며**, 기존의 이미지 피라미드 방식의 한계를 극복하여 **고해상도 이미지 처리의 효율성을 높였습니다**.  **PIIP의 설계 원리와 실험 결과는 향후 멀티 스케일 특징 추출 연구에 중요한 지침을 제공**할 것으로 기대됩니다. 이는 **컴퓨터 비전 및 멀티모달 이해 분야의 발전**에 크게 기여할 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.07783/x1.png)

> 🔼 그림 1은 시각적 인식과 다중 모드 이해에서 다양한 다중 해상도 설계를 보여줍니다. (a)와 (e)는 다중 스케일 특징이 없는 일반적인 네트워크를 나타냅니다. (b), (c), (f)는 모든 스케일에서 동일한 크기의 모델을 사용하는 비효율적인 이미지 피라미드 네트워크로, 가중치 공유 또는 개별 가중치와 상호 작용을 통해 구현됩니다. (d)는 고해상도 이미지를 큰 모델로 처리하여 높은 계산 비용이 드는 매개변수 직접 이미지 피라미드 네트워크입니다. (g)는 그리드 분할을 기반으로 다중 모드 작업에 대한 다중 해상도 접근 방식을 보여줍니다. (h)는 제안된 PIIP(Parameter-Inverted Image Pyramid Network)로, 감소하는 해상도의 이미지와 반대로 증가하는 매개변수 크기의 모델을 쌍으로 묶어 훨씬 적은 계산 비용으로 더 나은 성능을 달성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Different multi-resolution designs in visual perception and multimodal understanding. (a)(e) Plain network without multi-scale features. (b)(c)(f) Inefficient image pyramid networks using equivalently large models for all scales, either with shared weights or with separate weights and interactions. (d) Parameter-direct image pyramid network which processes high-resolution images with large models, leading to high computational cost. (g) Multi-resolution approaches on multimodal tasks based on grid partition. (h) Our efficient and effective parameter-inverted image pyramid network (PIIP), which pairs models of increasing parameter sizes inversely with images of decreasing resolution. It achieves better performance with much lower computational cost.
> </details>





{{< table-caption >}}
| Model | Resolution | #Param | #FLOPs | AP<sup>b</sup> | AP<sup>b</sup><sub>50</sub> | AP<sup>b</sup><sub>75</sub> | AP<sup>m</sup> | AP<sup>m</sup><sub>50</sub> | AP<sup>m</sup><sub>75</sub> |
|---|---|---|---|---|---|---|---|---|---| 
| ViTDet-B [68] | 1024 | 90M | 463G | 43.8 | 67.6 | 47.7 | 39.9 | 63.6 | 42.2 |
|  | 1120/896/448 | 146M | 243G | 43.9 | 65.7 | 47.5 | 38.6 | 61.8 | 40.6 |
| PIIP-TSB (ours) | 1568/896/448 | 147M | 287G | 45.0 | 67.0 | 48.7 | 40.2 | 63.8 | 42.6 |
|  | 1568/1120/672 | 149M | 453G | 46.6 | 68.4 | 51.1 | 41.4 | 65.2 | 44.3 |
| ViTDet-L [68] | 1024 | 308M | 1542G | 46.8 | 70.8 | 51.4 | 42.5 | 67.3 | 45.3 |
|  | 1120/672/448 | 493M | 727G | 46.7 | 69.0 | 50.6 | 40.8 | 65.2 | 42.8 |
| PIIP-SBL (ours) | 1344/896/448 | 495M | 1002G | 48.2 | 71.0 | 52.8 | 42.5 | 67.3 | 45.4 |
|  | 1568/896/672 | 497M | 1464G | 49.4 | 71.9 | 53.9 | 43.7 | 68.4 | 46.6 |
|  | 1344/896/672/448 | 506M | 755G | 46.9 | 69.9 | 50.6 | 41.6 | 65.9 | 44.1 |
| PIIP-TSBL (ours) | 1568/1120/672/448 | 507M | 861G | 48.2 | 70.5 | 52.7 | 42.8 | 66.9 | 45.6 |
|  | 1792/1568/1120/448 | 512M | 1535G | 49.6 | 72.4 | 54.2 | 44.2 | 69.2 | 47.5 |{{< /table-caption >}}

> 🔼 표 1은 COCO val2017 데이터셋에서 기본 모델과 비교한 결과를 보여줍니다. 백본의 파라미터 수와 FLOPs(연산량)을 함께 제시하며, 기본 모델과 비슷한 성능을 보이는 경우에는 밑줄을 그어 표시했습니다.  APb는 bounding box에 대한 평균 정밀도(Average Precision)를, APm은 segmentation mask에 대한 평균 정밀도를 나타냅니다.  다양한 해상도(Resolution)에서의 모델 성능과 효율성을 비교 분석하여 PIIP 모델의 우수성을 보여주는 표입니다.
> <details>
> <summary>read the caption</summary>
> TABLE I: Comparison with baseline on COCO val2017. We report the number of parameters and FLOPs of the backbone. Underline indicates FLOPs or metrics on par with the baseline. APbsuperscriptAPb\rm AP^{b}roman_AP start_POSTSUPERSCRIPT roman_b end_POSTSUPERSCRIPT and APmsuperscriptAPm\rm AP^{m}roman_AP start_POSTSUPERSCRIPT roman_m end_POSTSUPERSCRIPT represent box AP and mask AP, respectively.
> </details>





### In-depth insights


#### Inverted Image Pyramids
역전된 이미지 피라미드는 기존의 이미지 피라미드 방식을 뒤집어 고해상도 이미지는 작은 모델로, 저해상도 이미지는 큰 모델로 처리하는 새로운 접근법입니다. **계산 비용 절감**이 주요 목표이며, 고해상도 이미지의 세부 정보는 작은 모델로도 충분히 잡아낼 수 있다는 아이디어를 바탕으로 합니다.  **다양한 크기의 모델을 활용**하여 계산 효율을 높이는 동시에 다양한 크기의 객체를 효과적으로 인식하는 데 유용할 것으로 예상됩니다.  **모델 간 상호 작용 메커니즘**을 통해 서로 다른 해상도의 특징 정보를 효과적으로 통합하는 것이 중요하며, 이를 위한 다양한 기술들이 연구될 수 있습니다.  **다양한 비전 작업**에서의 실험 결과를 통해 역전된 이미지 피라미드의 효율성과 성능을 검증하고, **다중 모드 이해** 모델에도 적용 가능성을 확인할 수 있습니다.  **미래 연구**로는 다양한 모델 아키텍처와의 호환성, 더욱 정교한 특징 상호 작용 메커니즘 개발, 그리고 실제 응용 분야에 대한 추가적인 연구가 진행될 수 있습니다.

#### Multi-Scale Feature Fusion
본 논문에서 다루는 핵심 개념인 "다중 스케일 특징 융합"은 **다양한 해상도의 이미지 특징들을 효과적으로 통합하여** 보다 정확하고 풍부한 시각적 정보를 얻는 기술입니다.  단순히 여러 스케일의 이미지를 병렬적으로 처리하는 것이 아니라, **저해상도 특징의 시맨틱 정보와 고해상도 특징의 디테일 정보를 상호 보완적으로 결합**하는 것이 중요합니다.  **크로스-브랜치 상호작용 메커니즘**은 서로 다른 해상도의 특징 맵들 간의 정보 교환을 가능하게 하여, 각 스케일의 정보들이 전체적인 이해에 기여하도록 합니다.  **특징 융합 과정**은 단순한 합산이나 연결이 아닌, **학습 가능한 가중치를 활용**하거나, **어텐션 메커니즘**을 적용하여 중요한 정보를 선택적으로 통합하는 방식으로 이루어져야 합니다.  **계산 비용을 최소화하면서 성능을 극대화**하는 것이 다중 스케일 특징 융합의 핵심 과제이며, 본 논문의 PIIP(Parameter-Inverted Image Pyramid Network)는 이를 효과적으로 달성하는 구조를 제시합니다.

#### Model Efficiency Gains
본 논문에서 제시된 매개변수 반전 이미지 피라미드 네트워크 (PIIP)는 **계산 비용을 크게 줄이면서 성능을 유지 또는 개선**하는 뛰어난 모델 효율성 향상을 보여줍니다. 기존의 이미지 피라미드 방식과 달리, PIIP는 다양한 해상도의 이미지에 대해 서로 다른 크기의 사전 훈련된 모델을 사용합니다. 고해상도 이미지는 작은 모델로 처리하고, 저해상도 이미지는 큰 모델로 처리하여 계산량을 최적화합니다.  **크로스-브랜치 상호작용 메커니즘**을 통해 다양한 공간 스케일의 정보를 효과적으로 통합하여 성능을 더욱 향상시키는 것도 중요한 요소입니다.  PIIP는 다양한 비전 과제와 다중 모달 대규모 언어 모델에서 **일관되게 우수한 성능**을 보여주며, 특히 대규모 비전 기반 모델에서 효율성 향상이 두드러집니다.  **사전 훈련된 모델을 활용**하여 추가적인 훈련 없이도 효율성을 높일 수 있다는 점은 실용적인 측면에서 매우 중요한 장점입니다. 따라서 PIIP는 계산 자원이 제한적인 환경에서도 우수한 성능을 달성하는데 효과적인 방법론으로 평가될 수 있습니다.

#### MMLLM Enhancements
본 논문은 **다중 모드 대규모 언어 모델(MMLLM)**의 성능 향상에 중점을 두고 있습니다. 특히, **매개변수 반전 이미지 피라미드 네트워크(PIIP)**를 활용하여 고해상도 이미지 처리 시 발생하는 계산 비용 문제를 해결하고자 합니다. PIIP는 다양한 해상도의 이미지를 처리하기 위해 **서로 다른 크기의 사전 훈련된 모델을 활용**하여 효율성을 높입니다.  **고해상도 이미지는 작은 모델**, 저해상도 이미지는 큰 모델이 처리하는 방식으로, 계산 비용을 최소화하면서 성능을 향상시키는 전략입니다. 이러한 MMLLM 개선을 통해 객체 탐지, 분할, 이미지 분류 등의 시각적 인식 작업과 다중 모드 이해 작업에서 우수한 성능을 달성할 수 있습니다. 특히, **PIIP-LLaVa**와 같은 다중 모드 모델을 통해 텍스트VQA 및 MMBench와 같은 다양한 벤치마크에서 높은 정확도를 기록하였습니다.  **다양한 시각적 아키텍처와의 호환성** 또한 강점으로, ViT, CNN 등 다양한 모델에 적용 가능합니다.  이는 컴퓨터 비전 분야의 효율적인 다중 스케일 특징 구성에 대한 새로운 패러다임을 제시하며, **계산 자원 제약 하에서도 우수한 성능을 유지**할 수 있음을 보여줍니다.

#### Future Research
본 논문에서 제시된 Parameter-Inverted Image Pyramid Networks (PIIP)는 컴퓨팅 비용을 줄이면서 정확도를 높이는 데 성공했지만, **향후 연구 방향**은 여전히 많습니다.  **다양한 backbone 네트워크**와의 호환성을 높이고, **더욱 효율적인 cross-branch interaction mechanism**을 개발하는 것이 중요합니다.  **초고해상도 이미지 처리**에 대한 PIIP의 확장성을 검증하고, **다른 multimodal understanding tasks**에 적용하여 일반화 가능성을 높이는 연구도 필요합니다.  특히, **대규모 데이터셋**을 활용한 PIIP의 성능 향상 및 **다양한 하드웨어 플랫폼**에 대한 최적화 연구는 실용적인 측면에서 중요한 의미를 가집니다. 또한, PIIP의 **설계 원칙**에 대한 깊이 있는 분석을 통해 **더욱 효율적이고 강력한 multi-scale feature extraction 방법론**을 개발하는 연구가 필요합니다.  마지막으로, **PIIP의 한계점**을 명확히 파악하고, 이를 극복하기 위한 새로운 아이디어를 모색하는 것이 중요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.07783/x2.png)

> 🔼 그림 2는 PIIP(Parameter-Inverted Image Pyramid Networks)의 전체 아키텍처를 보여줍니다. PIIP는 다양한 해상도의 이미지를 처리하기 위해 다중 해상도 분기를 사용합니다. 큰 이미지는 작은 모델로 처리되어 계산 비용을 절감합니다. 각 분기는 사전 훈련된 ViT(Vision Transformer) 또는 CNN(Convolutional Neural Network)을 활용합니다. 상호 작용 유닛은 인접한 분기 간의 연결을 구축하고, 분기 병합은 모든 블록 뒤 또는 특정 중간 블록 내에서 모든 분기의 특징을 결합합니다. 이를 통해 다양한 해상도에서 효율적인 다중 스케일 특징 추출이 가능해집니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Overall architecture of PIIP. We use multi-resolution branches to process images of different resolutions, where larger images are handled by smaller models. Each branch leverages pretrained ViTs or CNNs. Interaction units build connections between adjacent branches. Branch merging is inserted after all the blocks or within certain intermediate blocks to combine the features of all branches.
> </details>



![](https://arxiv.org/html/2501.07783/x3.png)

> 🔼 그림 3은 PIIP-LLaVA의 다중 모드 이해를 위한 구조를 보여줍니다. PIIP-LLaVA는 다양한 해상도의 이미지를 처리하기 위해 여러 분기(branch)를 사용합니다. 각 분기는 미리 훈련된 Vision Transformer(ViT) 또는 Convolutional Neural Network(CNN)를 사용하여 특징을 추출합니다. 각 분기의 출력은 LLM(Large Language Model)의 언어 임베딩 공간과 정렬하기 위해 프로젝터(projector)를 거치고, 이렇게 처리된 시각적 특징들이 결합되어 최종적인 시각적 특징이 생성됩니다.  이를 통해 다양한 크기의 이미지에서도 효과적으로 시각 정보를 처리하고 이해할 수 있습니다. 고해상도 이미지는 세부 정보에 집중하고, 저해상도 이미지는 전체적인 맥락을 파악하는 방식으로 상호 보완적인 역할을 수행합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Illustration of PIIP-LLaVA for multimodal understanding. We use one projector after each branch to align the visual features with the language embedding space of the LLM, and combine the features to obtain the visual features.
> </details>



![](https://arxiv.org/html/2501.07783/x4.png)

> 🔼 그림 4는 PIIP 네트워크에서 사용된 상호 작용 유닛의 상세 구조를 보여줍니다. 이 유닛은 다양한 해상도의 피처 맵 간의 정보 교환을 담당하며, 두 개의 변형 가능한 어텐션(Deformable Attention) 모듈과 완전 연결 계층(Fully-connected layer), 그리고 피드포워드 네트워크(Feed-forward network)로 구성됩니다. 변형 가능한 어텐션은 입력 피처 맵의 특징을 효율적으로 포착하고, 완전 연결 계층은 차원 축소 및 특징 추출을 수행합니다. 마지막으로 피드포워드 네트워크는 채널 간의 상호 작용을 통해 다양한 해상도의 피처 맵을 통합하여 최종 출력을 생성합니다. 이러한 과정을 통해 다양한 스케일의 정보가 효과적으로 결합되어 보다 정확하고 풍부한 시각적 표현을 얻을 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Detailed structure of the interaction unit. It consists of two deformable attentions with fully-connect layers and feed-forward networks.
> </details>



![](https://arxiv.org/html/2501.07783/x5.png)

> 🔼 그림 5는 다양한 작업에 대한 분기 병합의 세부 설계를 보여줍니다. 객체 탐지, 분할 및 다중 모드 이해의 경우 모든 분기의 출력 특징은 투영 및 업샘플링을 통해 결합되어 후속 FPN 또는 LLM에 입력됩니다. 분류의 경우 원래 분류 헤드를 사용하여 로짓을 계산하고 평균을 내어 최종 예측으로 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Detailed design of branch merging in different tasks. For detection, segmentation and multimodal understanding, output features from all branches are fused together with projection and upsampling, and fed into the subsequent FPN or LLM. For classification, we employ the original classification heads to compute logits, and average them as the final prediction.
> </details>



![](https://arxiv.org/html/2501.07783/extracted/6128466/figures/interaction_types/inter_type_v4.png)

> 🔼 그림 10(a)는 PIIP-SBL 모델을 사용한 객체 탐지 결과를 보여줍니다. PIIP의 고해상도 처리 기능 덕분에 작은 물체까지 정확하게 탐지하는 것을 확인할 수 있습니다. 예를 들어, 왼쪽 상단 이미지의 작은 벤치와 사람들, 오른쪽 상단 이미지의 작은 차량들을 정확하게 식별합니다. 이는 PIIP가 시각적 인식 작업에서 우수한 성능을 보임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (a) Object detection
> </details>



![](https://arxiv.org/html/2501.07783/x6.png)

> 🔼 이 그림은 논문의 실험 결과 중 인스턴스 분할(Instance Segmentation) 결과를 보여줍니다.  다양한 이미지에 대해 모델이 객체의 경계를 정확하게 식별하고 분할하는 능력을 시각적으로 보여주는 여러 예시 이미지들이 포함되어 있습니다. 각 이미지는 모델이 예측한 인스턴스 분할 마스크와 함께 표시되어, 모델의 정확도를 평가할 수 있습니다. 특히, 고해상도 이미지 처리 능력을 강조하며, 작은 물체까지도 정확하게 분할하는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) Instance segmentation
> </details>



![](https://arxiv.org/html/2501.07783/x7.png)

> 🔼 그림 6은 PIIP의 여러 변형 모델들이 객체 탐지 및 인스턴스 분할 작업에서 입력 해상도 조정에 따른 성능을 보여줍니다.  각 변형 모델은 서로 다른 크기의 모델들을 사용하여 다양한 해상도의 이미지들을 처리합니다.  x축은 GFLOPs(초당 부동 소수점 연산 횟수)로 모델의 계산 비용을 나타내고, y축은 AP(평균 정밀도)로 모델의 성능을 나타냅니다. 객체 탐지와 인스턴스 분할 모두에서 PIIP 변형 모델들이 기준 모델보다 낮은 계산 비용으로 더 높은 성능을 달성함을 보여줍니다.  이는 PIIP의 효율성과 성능을 입증합니다. 특히 고해상도 입력에 대해 PIIP-TSBL 모델이 가장 효과적인 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Performance of different PIIP variants by adjusting input resolutions on object detection and instance segmentation.
> </details>



![](https://arxiv.org/html/2501.07783/x8.png)

> 🔼 표 V는 PIIP-SBL(Parameter-Inverted Image Pyramid Networks, 해상도 1568/1120/672) 모델에 대해 다양한 사전 훈련된 가중치를 사용하여 COCO val2017 데이터셋에서 실험한 결과를 보여줍니다.  각각 다른 사전 훈련 방법(예: AugReg, DeiT III, MAE, Uni-Perceiver, DINOv2, BEiTv2)으로 학습된 ViT-S 및 ViT-B 모델을 PIIP-SBL의 여러 브랜치에 적용하여 성능 변화를 비교 분석한 표입니다. 이를 통해 사전 훈련된 모델의 종류가 PIIP-SBL 모델의 객체 탐지 성능에 미치는 영향을 정량적으로 평가합니다.  APb와 APm 지표는 각각 bounding box와 mask에 대한 평균 정밀도(Average Precision)를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> TABLE V: Experiments of initializing with different pre-trained weights on COCO val2017 with PIIP-SBL 1568/1120/672.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | BranchesTiny | BranchesSmall | BranchesBase | Resolution | #FLOPs | Mask R-CNN 1x scheduleAP<sup>b</sup> | Mask R-CNN 1x scheduleAP<sup>m</sup> |
|---|---|---|---|---|---|---|---| 
| ViTDet-B [68] | - | - | ViT | 1024 | 463G | 43.8 | 39.9 |
| ConvNeXt-B [38] | - | - | ConvNeXt | 1024 | 321G | 42.4 | 38.7 |
|  | ViT | ViT | ViT | 1024/672/448 | 225G | 44.3 | 39.9 |
|  | ConvNeXt | ConvNeXt | ConvNeXt | 1024/672/448 | 326G | 46.4 | 41.7 |
|  | ConvNext | ViT | ViT | 1024/672/448 | 373G | 47.1 | 42.4 |
|  | ConvNext | ConvNext | ViT | 1024/672/448 | 431G | 46.8 | 42.2 |
|  | ConvNext | ViT | ConvNext | 1024/672/448 | 297G | 46.7 | 42.0 |
|  | ViT | ConvNext | ViT | 1024/672/448 | 291G | 45.4 | 40.9 |
|  | ViT | ConvNext | ConvNext | 1024/672/448 | 231G | 45.2 | 40.7 |
| PIIP-TSB (ours) | ViT | ViT | ConvNext | 1024/672/448 | 193G | 44.8 | 40.3 |{{< /table-caption >}}
> 🔼 표 II는 COCO val2017 데이터셋을 사용하여 CNN 기반 모델과 이종(heterogeneous) 모델의 성능을 비교한 결과를 보여줍니다.  'Branches' 열은 사용된 여러 가지 해상도의 분기 네트워크(branch) 수를 나타내고, 'Resolution' 열은 입력 이미지의 해상도를, '#FLOPS' 열은 연산량을, 'APb'와 'APm' 열은 각각 객체 검출(object detection)과 인스턴스 분할(instance segmentation) 작업에 대한 평균 정밀도(Average Precision)를 나타냅니다. 이 표는 PIIP(Parameter-Inverted Image Pyramid Network)의 효율성을 보여주기 위해 다양한 CNN 기반 아키텍처와 PIIP를 결합한 이종 모델의 성능을 비교 분석한 결과를 제시합니다.  다양한 분기 네트워크 수와 해상도 조합을 통해 연산량 대비 성능 향상을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> TABLE II: Performance of CNN-based and heterogeneous models on COCO val2017.
> </details>

{{< table-caption >}}
| Method | AP<sup>b</sup> | AP<sup>b</sup><sub>50</sub> | AP<sup>b</sup><sub>75</sub> | AP<sup>m</sup> | AP<sup>m</sup><sub>50</sub> | AP<sup>m</sup><sub>75</sub> |
|---|---|---|---|---|---|---|
| Mask R-CNN 1× schedule |
| PVTv2-B5 [66] | 47.4 | 68.6 | 51.9 | 42.5 | 65.7 | 46.0 |
| ViT-B [72] | 42.9 | 65.7 | 46.8 | 39.4 | 62.6 | 42.0 |
| ViTDet-B [68] | 43.2 | 65.8 | 46.9 | 39.2 | 62.7 | 41.4 |
| Swin-B [65] | 46.9 | - | - | 42.3 | - | - |
| ViT-Adapter-B [21] | 47.0 | 68.2 | 51.4 | 41.8 | 65.1 | 44.9 |
| PIIP-TSB (ours) | 47.9 | 70.2 | 52.5 | 42.6 | 67.2 | 45.5 |
| ViT-L [72] | 45.7 | 68.9 | 49.4 | 41.5 | 65.6 | 44.6 |
| ViTDet-L [68] | 46.2 | 69.2 | 50.3 | 41.4 | 65.8 | 44.1 |
| ViT-Adapter-L [21] | 48.7 | 70.1 | 53.2 | 43.3 | 67.0 | 46.9 |
| PIIP-SBL (ours) | 49.9 | 72.8 | 54.7 | 44.6 | 69.3 | 47.9 |
| DINO + MS schedule |
| PIIP-SBL-3× (ours) | 57.9 | 76.9 | 63.3 | - | - | - |
| PIIP-H6B-1× (ours) | 60.0 | 79.0 | 65.4 | - | - | - |{{< /table-caption >}}
> 🔼 표 III는 COCO val2017 데이터셋에서 수행된 객체 탐지 및 인스턴스 분할 성능을 보여줍니다.  'MS'는 다중 스케일 학습을 위해 AutoAugment [71]을 사용했음을 의미합니다.  대규모 모델은 ImageNet-21K에서 학습된 ViT 가중치를 사용합니다. 일부 결과는 [21]에서 가져왔습니다.  표는 다양한 모델의 AP(Average Precision) 값을 보여주며,  APb는 bounding box AP, APm은 mask AP를 나타냅니다.  다중 스케일 학습(MS) 여부와 모델의 크기(ViT-B, ViT-L 등)에 따라 성능 차이를 비교 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> TABLE III: Object detection and instance segmentation performance on COCO val2017. ‘MS’ means using AutoAugment [71] for multi-scale training. Large-size models use ViT weights trained on ImageNet-21K. Some results are from [21].
> </details>

{{< table-caption >}}
| Method | AP<sup>b</sup> | AP<sup>b</sup><sub>50</sub> | AP<sup>b</sup><sub>75</sub> | AP<sup>m</sup> | AP<sup>m</sup><sub>50</sub> | AP<sup>m</sup><sub>75</sub> |
|---|---|---|---|---|---|---|
| Cascade R-CNN 1× schedule |
| Swin-L [65] | 51.8 | 71.0 | 56.2 | 44.9 | 68.4 | 48.9 |
| ConvNeXt-L [38] | 53.5 | 72.8 | 58.3 | 46.4 | 70.2 | 50.2 |
| PIIP-SBL (ours) | 53.6 | 73.3 | 57.9 | 46.3 | 70.3 | 50.0 |
| Cascade R-CNN 3× + MS schedule |
| Swin-B [65] | 51.9 | 70.9 | 57.0 | - | - | - |
| Shuffle-B [73] | 52.2 | 71.3 | 57.0 | - | - | - |
| ViT-B [72] | 50.1 | 69.3 | 54.3 | - | - | - |
| ViT-Adapter-B [21] | 52.1 | 70.6 | 56.5 | - | - | - |
| PIIP-TSB (ours) | 53.1 | 72.3 | 57.4 | 46.5 | 70.1 | 51.1 |
| Swin-L [65] | 53.9 | 72.4 | 58.8 | 46.7 | 70.1 | 50.8 |
| RepLKNet-31L [74] | 53.9 | 72.5 | 58.6 | 46.5 | 70.0 | 50.6 |
| ConvNeXt-L [38] | 54.8 | 73.8 | 59.8 | 47.6 | 71.3 | 51.7 |
| PIIP-SBL (ours) | 54.5 | 73.8 | 59.1 | 47.7 | 71.6 | 52.1 |{{< /table-caption >}}
> 🔼 표 IV는 대규모 비전 기반 모델인 InternViT-6B에 대한 실험 결과를 보여줍니다.  InternViT-6B를 기반으로 한 PIIP의 성능을 Mask R-CNN 1× 스케줄을 사용하여 평가하였습니다. 표에는 모델, 매개변수 수, FLOPs, 해상도, APb(Box AP), APm(Mask AP), 그리고 크롭 크기 및 UperNet 160k에 대한 mIoU가 포함되어 있습니다. PIIP-LH6B(ours) 모델은 원본 InternViT-6B보다 낮은 계산 비용으로 유사하거나 더 나은 성능을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> TABLE IV: Experiments on the large-scale vision foundation model InternViT-6B.
> </details>

{{< table-caption >}}
| Model | #Param | #FLOPs | Resolution | AP<sup>b</sup> | AP<sup>m</sup> | Crop Size | #FLOPs | mIoU |
|---|---|---|---|---|---|---|---|---|
| InternViT-6B [39] | 5919M | 24418G | 1024 | 53.8 | 48.1 | 512 | 6105G | 58.36 |
|  | 7269M | 5643G | 1280/1024/256 | 53.5 | 47.5 | 640/512/192 | 1903G | 57.82 |
| PIIP-LH6B (ours) | 7271M | 10368G | 1280/1024/512 | 54.4 | 47.8 | 640/512/256 | 2592G | 58.42 |
|  | 7273M | 13911G | 1280/1024/640 | **55.7** | **49.0** | 640/512/384 | 4560G | **59.65** |{{< /table-caption >}}
> 🔼 표 X는 ImageNet-1K 데이터셋을 사용한 처음부터 학습(from-scratch pre-training) 설정과 결과를 보여줍니다.  (a) 부분은 모델의 구성을 보여주는데, 여러 해상도의 입력 이미지를 처리하는 여러 분기(branch)의 레이어 수, 차원, 헤드 수, 해상도, 파라미터 수, FLOPs(연산량) 등을 상세히 나타냅니다. 각 분기는 서로 다른 크기의 이미지를 효율적으로 처리하도록 설계되었으며, 상호 작용 유닛(interaction unit)을 통해 서로 다른 해상도의 특징을 통합합니다. (b) 부분은 처음부터 학습한 PIIP-B 모델과 기준 모델인 ViT-B의 성능을 비교 분석하여, 제안된 PIIP 구조가 ImageNet-1K 이미지 분류 작업에서 우수한 성능을 달성함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> TABLE X: From-scratch pre-training settings and results on ImageNet-1K.
> </details>

{{< table-caption >}}
| Model (backbone) | Model (backbone) | AP<sup>b</sup> | AP<sup>m</sup> |
|---|---|---|---| 
| **ViT-S** | **ViT-B / ViT-L** |  |  |
| AugReg [4] | AugReg [4] | 48.3 | 42.6 |
| DeiT III [3] | Uni-Perceiver [81] | 48.8 | 42.9 |
| DeiT III [3] | MAE [76] | 49.1 | 43.0 |
| DeiT III [3] | DeiT III [3] | 50.0 | 44.4 |
| DeiT III [3] | DINOv2 [82] | 51.0 | 44.7 |
| DeiT III [3] | BEiTv2 [83] | 51.8 | 45.4 |{{< /table-caption >}}
> 🔼 표 XI는 다양한 다중 모드 벤치마크에서 제시된 다중 해상도 기준 모델들과 PIIP-LLaVA의 성능을 비교한 것입니다. 모든 모델은 LLaVA-1.5 [24]의 학습 데이터를 사용하여 학습되었으며, 비전 인코더의 FLOPs(연산량)이 제시되어 있습니다. 이 표는 PIIP-LLaVA가 비슷한 연산량을 가진 기존의 다중 해상도 모델들에 비해 여러 다중 모드 작업에서 더 나은 성능을 보임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> TABLE XI: Comparison with multi-resolution baselines on multimodal benchmarks. All models are trained with LLaVA-1.5 [24] training data. We report #FLOPs of the vision encoder.
> </details>

{{< table-caption >}}
| Method | Crop Size | #FLOPS | mIoU |
|---|---|---|---|
| ViT-B | 640 | 159G | 51.0 |
| PIIP-TSB (ours) | 896/448/336 | 118G | 51.6 |
| ViT-L | 640 | 545G | 53.6 |
| PIIP-SBL (ours) | 1120/448/336 | 456G | 54.3 |{{< /table-caption >}}
> 🔼 표 XII는 다양한 멀티모달 대규모 언어 모델(MLLM)의 성능을 벤치마크한 결과를 보여줍니다.  여러 벤치마크 작업에 대한 각 모델의 성능과 함께 사용된 비전 인코더, 이미지 해상도, LLM, 학습 데이터 크기 등의 정보를 제공합니다.  특히 SQA-IMG 테스트 세트의 이미지가 훈련 중에 관찰되었기 때문에 해당 결과와 평균은 회색으로 표시되어 있습니다. 이 표는 PIIP-LLaVA 모델의 성능을 다른 최첨단 MLLM과 비교하여 PIIP-LLaVA의 효과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> TABLE XII:  Comparison with existing MLLMs on multimodal benchmarks. “Data” denotes the data size of all training stages. *Images from SQA-IMG test set are observed in training, so we mark its result and Avg in gray.
> </details>

{{< table-caption >}}
| Method | Crop Size | mIoU |
|---|---|---|
| Swin-B [65] | 512 | 48.1 |
| ConvNeXt-B [38] | 512 | 49.1 |
| RepLKNet-31B [74] | 512 | 49.9 |
| SLaK-B [84] | 512 | 50.2 |
| InternImage-B [18] | 512 | 50.2 |
| PIIP-TSB (ours) | 896/448/336 | **51.6** |
| Swin-L [65] | 640 | 52.1 |
| RepLKNet-31L [74] | 640 | 52.4 |
| ConvNeXt-L [38] | 640 | 53.2 |
| ConvNeXt-XL [38] | 640 | 53.6 |
| InternImage-L [18] | 640 | 53.9 |
| PIIP-SBL (ours) | 1120/448/336 | **54.3** |{{< /table-caption >}}
> 🔼 표 XIII는 CLIP-B, CLIP-L 및 Vicuna-7B를 사용한 다중 모드 이해에 대한 ablation study 결과를 보여줍니다.  다양한 상호 작용 횟수와 미세 조정 중에 해제된 모듈(vision encoder의 일부 또는 전체)을 변경하여 다중 모드 이해 작업에서 모델 성능에 미치는 영향을 분석합니다.  구체적으로는, 미세조정 단계에서 vision encoder의 특정 부분을 얼마나 풀어줄지, 그리고 여러 branch들 간의 상호작용 횟수를 달리하여 성능 변화를 측정합니다. 이를 통해 다중 모드 이해를 위한 최적의 설정을 도출하고자 하였습니다.
> <details>
> <summary>read the caption</summary>
> TABLE XIII: Ablation on multimodal understanding with CLIP-B, CLIP-L and Vicuna-7B.
> </details>

{{< table-caption >}}
| Model | Resolution | #FLOPs | Top-1 Acc |
|---|---|---|---| 
| DeiT-B [2] | 224 | 17.2G | 81.8 |
| PIIP-TSB (ours) | 368/192/128 | 17.4G | 82.1 |
| ViT-L [4] | 224 | 61.6G | 84.0 |
| ViT-L [4] (our impl.) | 224 | 61.6G | 85.2 |
| PIIP-SBL (ours) | 320/160/96 | 39.0G | 85.2 |
| PIIP-SBL (ours) | 384/192/128 | 61.2G | 85.9 |{{< /table-caption >}}
> 🔼 표 XIV는 이미지 피라미드와 파라미터 반전 설계에 대한 ablation study 결과를 보여줍니다.  'PI'는 파라미터 반전(parameter-inverted), 'IP'는 이미지 피라미드(image pyramid), 'Inter.'는 교차 피처 상호작용(interactions)을 나타냅니다. 'MS'는 논문 [71]에 따른 다중 스케일 학습(multi-scale training)을 의미합니다. 이 표는 다양한 이미지 피라미드 구조(단일 분기, 전통적인 이미지 피라미드, 파라미터 동등 이미지 피라미드, 파라미터 직접 이미지 피라미드, 그리고 제안된 파라미터 반전 이미지 피라미드)와 상호작용 유무에 따른 성능 및 계산 비용을 비교 분석하여, 제안된 파라미터 반전 이미지 피라미드 네트워크의 효율성과 효과를 보여줍니다.  각 구조는 매개변수 수, FLOPs, 그리고 여러 객체 탐지 지표(APb, APm 등)를 사용하여 비교됩니다.
> <details>
> <summary>read the caption</summary>
> TABLE XIV: Ablation on image pyramid and parameter-inverted design. ‘PI’, ‘IP’ and ‘Inter.’ represent parameter-inverted, image pyramid and interactions. ‘MS’ means multi-scale training, following [71].
> </details>

{{< table-caption >}}
| Out Branch | AP<sup>b</sup> | AP<sup>m</sup> |
|---|---|---|
| B | 43.1 | 37.0 |
| S | 44.7 | 39.1 |
| T | 45.6 | 40.6 |
| B+S | 45.4 | 39.8 |
| B+T | 46.3 | 41.1 |
| S+T | 46.2 | 40.9 |
| B+S+T | **46.6** | **41.4** |{{< /table-caption >}}
> 🔼 표 XV는 더 높은 해상도를 사용한 기준 모델에 대한 실험 결과를 보여줍니다.  기존 ViTDet-L 모델의 해상도를 1024에서 1792로 높였을 때의 성능과 FLOPs(연산량) 변화를 보여주는 비교표입니다.  또한, 제안된 PIIP-TSBL 모델의 1792/1568/1120/448 해상도에서의 성능과 FLOPs를 함께 제시하여 해상도 증가에 따른 성능 향상과 연산량 증가의 효율성을 비교 분석합니다.  PIIP-TSBL 모델이 더 높은 해상도에도 불구하고 비슷하거나 더 높은 정확도를 유지하면서 연산량을 효율적으로 관리함을 보여주는 표입니다.
> <details>
> <summary>read the caption</summary>
> TABLE XV: Baseline with higher resolution.
> </details>

{{< table-caption >}}
| Module | #Layers | Dim | #Heads | Resolution | #Param | #FLOPs |
|---|---|---|---|---|---|---|
| Branch 1 | 12 | 640 | 8 | 128 | 59.6M | 3.8G |
| Branch 2 | 12 | 320 | 4 | 256 | 15.1M | 4.3G |
| Branch 3 | 12 | 160 | 2 | 512 | 4.0M | 4.9G |
| Interactions | 12 | - | - | - | 21.2M | 5.1G |
| Branch Merging | - | - | - | - | 0.3M | 0.2G |{{< /table-caption >}}
> 🔼 표 XVI는 PIIP-TSB(Parameter-Inverted Image Pyramid Network, 해상도 1120/896/448) 모델의 성능에 대한 에이블레이션 연구 결과를 보여줍니다.  구체적으로는 크로스 어텐션(cross-attention) 구현 방식(일반 어텐션과 디포머블 어텐션)과 상호작용(interaction) 횟수를 변화시켜가며, 객체 탐지 성능(APb, APm, APs)에 미치는 영향을 분석합니다. 이를 통해 어떤 어텐션 메커니즘과 상호작용 횟수가 PIIP-TSB 모델의 성능 향상에 가장 효과적인지 확인하고자 합니다. FLOPs(연산량) 또한 함께 제시되어 연산량 대비 성능 개선 효과를 평가하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> TABLE XVI: Ablation on attention implementation and number of interactions with PIIP-TSB 1120/896/448.
> </details>

{{< table-caption >}}
| Model | Resolution | #Param | #FLOPs | Top-1 Acc |
|---|---|---|---|---|
| ViT-B (our impl.) | 224 | 86M | 17.5G | 82.0 |
| PIIP-B (ours) | 512/256/128 | 100M | 18.4G | 82.7 |{{< /table-caption >}}
> 🔼 표 XVII은 PIIP-TSB 모델의 해상도를 1120/896/448로 고정하고, 서로 다른 상호작용 방식(interaction directions)이 모델 성능에 미치는 영향을 실험한 결과를 보여줍니다. 다섯 가지 상호작용 방향(Type1-Type5)에 따른 FLOPs(연산량), APb(Bounding Box 평균 정밀도), APm(Mask 평균 정밀도)를 비교 분석하여 최적의 상호작용 방식을 제시합니다. 각 방식은 인접한 분기(branch) 간의 정보 흐름 방향을 다르게 설정하여 실험하였습니다.
> <details>
> <summary>read the caption</summary>
> TABLE XVII: Ablation on interaction directions with PIIP-TSB under resolution 1120/896/448.
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
{{< /gallery >}}