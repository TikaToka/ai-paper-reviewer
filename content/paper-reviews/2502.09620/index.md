---
title: "Exploring the Potential of Encoder-free Architectures in 3D LMMs"
summary: "인코더 없는 3D LMM 구조를 최초로 제시, 기존 인코더 기반 모델의 한계 극복!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Vision-Language Models", "🏢 Northwestern Polytechnical University",]
showSummary: true
date: 2025-02-13
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.09620 {{< /keyword >}}
{{< keyword icon="writer" >}} Yiwen Tang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-14 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.09620" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.09620" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/exploring-the-potential-of-encoder-free" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 3D 대규모 다중 모달 모델(LMM)은 인코더에 의존하여 **점 구름 해상도의 변화에 적응하지 못하고**, 인코더의 특징이 LLM의 의미적 요구 사항과 일치하지 않는 문제점을 가지고 있었습니다. 이러한 문제는 모델 성능 저하 및 제한된 활용성으로 이어집니다.

본 연구는 이러한 문제를 해결하기 위해 **인코더가 없는 최초의 3D LMM인 ENEL을 제시**합니다. ENEL은 **LLM이 3D 인코더의 역할을 수행**하도록 하여, 사전 훈련 단계에서 다양한 점 구름 자기 지도 학습 손실을 활용하고, 지침 미세 조정 단계에서 계층적 기하 집계 전략을 도입합니다. 그 결과, ENEL은 최첨단 모델과 유사한 성능을 달성하여, 인코더 없는 아키텍처의 효율성과 잠재력을 입증하였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 인코더 없는 아키텍처를 통해 3D LMM의 해상도 제약 및 의미적 불일치 문제 해결 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} LLM을 3D 인코더 역할로 활용하는 새로운 전략 제시 및 검증 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 제안된 ENEL 모델이 최첨단 성능과 비교 가능한 결과를 달성하며, 효율성과 확장성을 보임 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **3D LMM에서 인코더를 제거하는 혁신적인 접근 방식**을 제시하여, 기존의 한계를 극복하고 성능을 향상시켰다는 점에서 중요합니다. **해상도 제약 및 의미적 불일치 문제**를 해결함으로써, 3D 데이터 이해 분야의 발전에 크게 기여할 수 있으며, **향후 연구를 위한 새로운 방향**을 제시합니다. 특히, LLM을 3D 인코더의 역할을 수행하도록 함으로써, 모델의 확장성과 효율성을 높일 수 있는 가능성을 보여줍니다. 이는 **다양한 3D 애플리케이션 분야**에 널리 적용될 수 있으므로, 관련 연구자들에게 상당한 영향을 미칠 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.09620/extracted/6201996/intro3.png)

> 🔼 그림 1은 encoder 기반 3D LMM의 문제점을 보여줍니다. (a)는 Point Cloud Resolution Limitation을 보여주는 것으로, 학습 시에는 point cloud 크기(P.T. size)와 point token 크기가 각각 8192와 512로 고정되어 있지만, 추론 시에는 point cloud 크기는 2K에서 16K로, point token 크기는 128에서 2048로 조정됩니다. Objaverse 벤치마크의 captioning 작업에서 GPT-4 점수를 평가 지표로 사용하여 평가했습니다. (b)는 Embedding Semantic Discrepancy를 보여주는 것으로, 평균 text token의 point token에 대한 attention 점수를 시각화한 것입니다. 빨간색은 높은 값을 나타냅니다. encoder가 없는 구조의 point token은 LLM에 필요한 텍스트 의미적 관련성이 더 강합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Issues of encoder-based 3D LMMs. (a) Point Cloud Resolution Limitation. During training, the point cloud size (P.T. size) and point token size (P.T. size) are fixed at 8192 and 512, respectively. And we adjust these two sizes during inference, point cloud size from 2K to 16K and the corresponding point token size from 128 to 2048. We evaluate them on the captioning task of the Objaverse benchmark using GPT-4 scores as the evaluation metric. (b) Embedding Semantic Discrepancy. We visualize the attention scores of the average text token to the point tokens, where red indicates higher values. The point tokens in the encoder-free architecture exhibit stronger textual semantic relevance needed for the LLM.
> </details>





{{< table-caption >}}
| Method | Cls | Cap | Cap |
|---|---|---|---|
| **Method** | **Cls** | **Cap** | **Cap** |
| **GPT-4** | **GPT-4** | **S-BERT** |  |
| PointLLM-7B | 53.00 | 44.85 | 47.47 |
| - Encoder | 35.50 | 33.37 | 41.19 |
| + 2-layer T.E. | 42.50 | 41.35 | 44.25 |
| **+ 3-layer T.E.** | **47.31** | **43.86** | **45.89** |
| + 4-layer T.E. | 45.00 | 42.99 | 44.51 |{{< /table-caption >}}

> 🔼 표 1은 제안된 토큰 임베딩 모듈의 성능을 평가하기 위해 Objaverse 벤치마크에서 PointLLM-7B 모델을 기준으로 실험한 결과를 보여줍니다.  'Cls'와 'Cap'은 각각 분류와 캡션 생성 작업을 나타내며, S-BERT는 문장 BERT를 의미합니다.  T.E.는 연구팀에서 새롭게 설계한 토큰 임베딩 모듈을 가리킵니다.  이 표는 다양한 토큰 임베딩 방법(기준 모델과 2, 3, 4 레이어의 T.E.를 사용한 경우)의 분류 및 캡션 생성 성능을 GPT-4 점수와 S-BERT 점수를 사용하여 비교 분석한 결과를 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Token Embedding. We evaluate the performance on the Objaverse benchmark and adopt PointLLM-7B as the baseline model. ’Cls’ and ’Cap’ represent classification and captioning tasks, respectively. S-BERT refers to the Sentence-BERT. T.E. stands for our designed token embedding module.
> </details>





### In-depth insights


#### Encoder-Free 3D LLMs
본 논문은 **인코더가 없는 3D 거대 언어 모델(LLM)**의 잠재력을 탐구합니다. 기존의 인코더 기반 3D LLM들은 다양한 포인트 클라우드 해상도에 적응하지 못하고, 인코더의 포인트 특징이 LLM의 의미론적 요구를 충족시키지 못하는 등의 한계점을 지니고 있습니다. 이를 극복하기 위해, 본 논문은 **LLM이 3D 인코더의 역할을 수행**하도록 하는 전략을 제시합니다. 즉, **LLM이 포인트 클라우드를 직접 처리하여 의미론적 정보를 추출**하고, **계층적 기하 구조 집계 전략**을 통해 LLM 초기 레이어에 귀납적 편향을 통합하여 지역적 세부 정보에 집중하도록 합니다.  **사전 학습 단계**에서는 다양한 포인트 클라우드 자기 지도 학습 손실 함수들을 사용하여 LLM에 의미론적 정보를 삽입하고, **지침 미세 조정 단계**에서는 지역적 정보 집계를 수행합니다. 결과적으로, 인코더가 없는 최초의 3D LLM인 ENEL을 제시하고, 이 모델이 최첨단 모델과 경쟁력 있는 성능을 달성함을 보여줍니다.  **이 연구는 3D LLM 분야에서 인코더 없는 아키텍처의 가능성을 보여주는 중요한 결과물**입니다.

#### Semantic Encoding
본 논문에서 제시된 의미론적 인코딩(Semantic Encoding) 전략은 **기존의 3D 인코더를 제거하고 LLM이 3D 데이터를 직접 처리**할 수 있도록 하는 핵심 개념입니다. 이를 위해 **LLM의 초기 계층을 학습 가능**하게 설정하고 다양한 **자기 지도 학습 손실 함수**를 활용하여 LLM이 고차원적인 3D 의미 정보를 효과적으로 학습하도록 유도합니다. 특히 **하이브리드 의미론적 손실 함수(Hybrid Semantic Loss)**는 지역적 공간 정보와 고차원적 의미 정보를 동시에 학습하여 LLM의 3D 이해 능력을 향상시키는 데 중요한 역할을 합니다.  **마스크된 모델링 손실(Masked Modeling Loss), 재구성 손실(Reconstruction Loss), 대조 손실(Contrastive Loss)** 등 다양한 손실 함수들을 비교 분석하여 최적의 성능을 달성하는 방법을 제시합니다.  결과적으로 제시된 의미론적 인코딩은 **인코더 기반의 3D LMM의 한계를 극복**하고, LLM이 **점군 데이터의 고해상도 변화와 다양한 해상도에 효과적으로 적응**할 수 있게 만듭니다.

#### Geometric Aggregation
본 논문에서 제안하는 계층적 기하 집계 전략은 **3D LMM에서 인코더를 제거함으로써 발생하는 성능 저하를 완화하기 위한 핵심 전략**입니다.  기존 3D 인코더가 담당하던 **공간적 구조 정보 학습 기능을 LLM의 초기 계층으로 이전**하여, LLM이 3D 점 구름 데이터의 지역적 세부 정보에 집중하도록 유도합니다.  **FPS(Farthest Point Sampling)와 k-NN(k-Nearest Neighbor)** 알고리즘을 활용하여 점 구름의 기하학적 분포를 기반으로 토큰을 계층적으로 집계하고 전파하는 방식으로, LLM이 다양한 수준의 기하학적 세부 정보를 효과적으로 포착할 수 있도록 합니다.  이러한 전략은 LLM의 **초기 계층에 유도적 편향을 도입**하여, 3D 객체의 기하학적 특징을 보다 정확하게 이해하는 데 도움을 줍니다.  결과적으로, **인코더 없이도 우수한 3D 이해 능력을 갖춘 LLM을 구축**하는 데 기여합니다.

#### ENEL: A Case Study
**ENEL은 인코더 없는 3D 거대 다중 모달 모델의 잠재력을 보여주는 사례 연구입니다.** 본 연구는 기존의 인코더 기반 3D LMM의 한계를 극복하기 위해 LLM이 3D 인코더의 역할을 수행할 수 있도록 하는 새로운 설계를 제시합니다. **LLM 임베디드 의미 인코딩 전략**과 **계층적 기하 집계 전략**은 3D 의미를 효과적으로 포착하고 LLM에 통합하는 핵심입니다. 다양한 자체 감독 학습 손실 함수를 실험하여 하이브리드 의미 손실을 제안하며, 이는 LLM이 고차원 3D 의미를 학습하는 데 도움이 됩니다.  ENEL은 벤치마크에서 최첨단 성능을 달성하며, 인코더 없는 아키텍처의 효율성과 효과를 입증합니다. **특히, PointLLM-13B와 유사한 성능을 7B 모델로 달성하여 효율성을 보여줍니다.**  이 연구는 3D LMM에서 인코더 없는 아키텍처의 가능성을 보여주는 중요한 사례 연구이며, 향후 연구 방향을 제시하는 데 기여할 것입니다.

#### Future of 3D LLMs
3D 거대 언어 모델(LLM)의 미래는 **매우 밝지만 도전 과제 또한 많습니다.**  향후 연구는 **더욱 정교한 3D 데이터 표현과 처리 기술** 개발에 집중되어야 합니다.  **점군(point cloud) 데이터의 효율적인 처리 방식**과 **다양한 3D 데이터 형식(메쉬, 볼륨 등)에 대한 통합적 지원**은 필수적입니다. 또한, **LLM의 3D 이해 능력 향상**을 위한 새로운 학습 방법과 **다중 모달리티 통합** 기술 개발이 중요합니다.  **사전 학습된 3D 지식을 효과적으로 활용하는 기법**과 **다양한 3D 관련 작업(분류, 생성, 질의응답 등)에 대한 성능 향상**도 중요한 연구 방향입니다.  **윤리적 문제 및 편향성 해결**과 **데이터 프라이버시 보호**는 3D LLM 개발 과정에서 항상 고려되어야 합니다.  궁극적으로는 **현실 세계와의 상호작용이 가능한 지능형 3D LLM** 개발을 목표로 해야 합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.09620/x1.png)

> 🔼 그림 2는 ENEL의 전체 파이프라인을 보여줍니다. 훈련은 두 단계, 즉 사전 훈련 단계와 지시 튜닝 단계로 나뉩니다. 첫 번째 단계에서는 처음 K개의 레이어를 학습 가능하도록 설정하고 제안된 하이브리드 의미론적 손실을 적용하여 고차원 의미를 LLM에 포함시킵니다. 두 번째 단계에서는 계층적 기하학적 집계 전략을 채택하여 점 구름의 지역적 구조를 포착합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Overall Pipeline of Enel. The training is divided into two stages: the pre-training stage and the instruction tuning stage. In the first stage, we set the first K𝐾Kitalic_K layers to be learnable and apply the proposed Hybrid Semantic Loss to embed high-level semantics into the LLM. In the second stage, we adopt the Hierarchical Geometric Aggregation strategy to capture local structures of point clouds.
> </details>



![](https://arxiv.org/html/2502.09620/x2.png)

> 🔼 그림 3은 인코더가 없는 3D LMM을 위한 자기 지도 학습 손실 함수들을 보여줍니다.  (a)는 마스크 모델링 손실, (b)는 재구성 손실, (c)는 대조 손실, (d)는 지식 증류 손실을 나타냅니다. (e)는 본 논문에서 제안하는 하이브리드 의미론적 손실 함수로, 인코더가 없는 아키텍처를 위해 특별히 고안되었습니다. 이 그림은 다양한 자기 지도 학습 기법을 비교하여 인코더 없는 3D LMM의 성능 향상에 기여하는 최적의 방법을 찾는 과정을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Point Cloud Self-Supervised Learning Losses. In the pre-training stage, we explore common self-supervised learning losses for the encoder-free 3D LMM: (a) Masked Modeling Loss, (b) Reconstruction Loss, (c) Contrastive Loss, and (d) Knowledge Distillation Loss. The (e) represents our proposed Hybrid Semantic Loss, specifically designed for the encoder-free architecture.
> </details>



![](https://arxiv.org/html/2502.09620/x3.png)

> 🔼 그림 4는 ENEL 모델의 Instruction Tuning 단계에서 사용되는 계층적 기하학적 집계(Hierarchical Geometry Aggregation) 전략을 보여줍니다.  이 전략은 3D 포인트 클라우드의 국부적인 구조적 세부 정보를 포착하기 위해 포인트 토큰에 집계 및 전파 연산을 적용하는 방법을 나타냅니다.  구체적으로, 그림에서는 LLM의 초기 레이어에서 FPS(Farthest Point Sampling)와 k-NN(k-Nearest Neighbor)을 사용하여 포인트 토큰을 집계하고, 게이트된 자기 주의 메커니즘을 통해 국부적 기하학적 구조를 캡처하는 과정을 보여줍니다.  이후, 여러 번의 집계 및 전파 연산을 통해 다양한 수준의 국부 정보를 추출하여 LLM의 상위 레이어에 전달합니다. 이를 통해 LLM은 전역적 정보와 국부적 세부 정보 모두를 활용하여 3D 포인트 클라우드를 보다 정확하게 이해할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Hierarchical Geometry Aggregation Strategy. In the instruction tuning stage, we apply aggregation and propagation operations to the point tokens to capture the local structural details.
> </details>



![](https://arxiv.org/html/2502.09620/x4.png)

> 🔼 그림 5는 인코더 기반 및 인코더 없는 아키텍처의 의미론적 인코딩 잠재력을 비교하여 보여줍니다. Objaverse 데이터셋에서 평균 텍스트 토큰의 어텐션 점수를 시각화하여, 인코더 기반 모델과 인코더 없는 모델에서 3D 점 구름의 의미론적 표현의 차이를 보여줍니다. 빨간색은 더 높은 어텐션 점수를 나타냅니다. (a)는 의자, (b)는 비행기, (c)는 램프를 나타냅니다. 인코더 없는 모델은 텍스트와 3D 형상 사이의 더 강력한 의미론적 연관성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Difference in Semantic Encoding. By visualizing the attention scores of the average text token to the point tokens on the Objaverse dataset, we compare the semantic encoding potential of encoder-based and encoder-free architectures, where red indicates higher values. And (a) represents chairs, (b) represents airplanes, and (c) represents lamps.
> </details>



![](https://arxiv.org/html/2502.09620/extracted/6201996/loss2.png)

> 🔼 그림 6은 Point Cloud Self-Supervised Learning Loss의 세 가지 변형을 보여줍니다. (a)는 Masked Modeling Loss의 변형으로, 입력 포인트 클라우드의 일부를 마스킹하고 LLM이 마스킹된 부분을 예측하게 합니다. (b)는 Reconstruction Loss의 변형으로, LLM이 생성한 포인트 클라우드를 원래 포인트 클라우드와 비교하여 재구성 오차를 최소화하는 방식입니다. (c)는 Hybrid Semantic Loss의 변형으로, Masked Modeling Loss와 Reconstruction Loss를 결합하여 고차원 의미 정보와 저차원 공간 정보를 동시에 학습합니다.  각 변형은 LLM이 3D 포인트 클라우드의 의미적 및 기하학적 특징을 효과적으로 학습하는 데 기여합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Variants of Point Cloud Self-Supervised Learning Losses. (a) The Variant of Masked Modeling Loss, (b) The Variant of Reconstruction Loss, (c) The Variant of Hybrid Semantic Loss.
> </details>



![](https://arxiv.org/html/2502.09620/extracted/6201996/output3.png)

> 🔼 그림 7은 ENEL 모델이 다양한 유형의 3D 모델에 대한 질문에 대해 정확하고 다양한 응답을 생성할 수 있음을 보여주는 여러 예시들을 보여줍니다. 그림에는 3D 모델 이미지와 함께, 각 모델에 대한 질문과 ENEL이 생성한 응답이 함께 제시되어 있습니다.  예시 질문들은 3D 모델의 세부적인 설명, 특징 파악, 수량 질문 등 다양한 유형을 포함하며, ENEL은 각 질문에 대해 구체적이고 문맥에 맞는 답변을 제시합니다. 이를 통해 ENEL 모델의 강력한 3D 이해 능력과 다양한 질문 유형에 대한 적응력을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Enel Output Examples. We demonstrate that Enel provides precise and diverse responses when addressing different problems.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | LR | Cls | Cap | Cap |
|---|---|---|---|---|
| **Method** | **LR** | **Cls** | **Cap** | **Cap** |
|  |  | **GPT-4** | **GPT-4** | **S-BERT** |
| PointLLM-7B | 2e-3 | 53.00 | 44.85 | 47.47 |
| + 2 learnable layers | 2e-3 | 41.06 | 42.23 | 45.92 |
|  | 4e-4 | 45.5 | 44.72 | 47.35 |
| + 4 learnable layers | 2e-3 | 44.85 | 41.53 | 46.77 |
|  | 4e-4 | 49.11 | 45.39 | 47.71 |
| + 8 learnable layers | 2e-3 | 43.76 | 39.71 | 42.38 |
|  | 4e-4 | 48.00 | 44.49 | 47.21 |{{< /table-caption >}}
> 🔼 표 2는 LLM의 초기 레이어를 학습 가능하도록 설정한 추가적인 3D 인코딩 결과를 보여줍니다.  원래 학습률을 2e-3으로 설정했고, 표에는 학습률(LR)을 변경하면서 2개, 4개, 8개의 학습 가능한 레이어를 추가했을 때의 결과(GPT-4, S-BERT 기준)가 제시되어 있습니다.  각 설정에 따른 분류 및 캡션 생성 성능 변화를 비교하여 3D 인코딩 전략의 효과를 분석하기 위한 표입니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Further 3D Encoding. We set the LLM early layers to be learnable. LR represents the learning rate during the pre-training stage, with the original learning rate set to 2e-3.
> </details>

{{< table-caption >}}
| Method | Cls | Cap | Cap |
|---|---|---|---|
| **Method** | **Cls** | **Cap** | **Cap** |
| **GPT-4** | **GPT-4** | **S-BERT** |  |
| PointLLM-7B | 53.00 | 44.85 | 47.47 |
| Masked Modeling Loss<sub>patch</sub><sup>Ψ</sup> | 48.50 | 45.34 | 46.36 |
| Masked Modeling Loss<sub>patch</sub><sup>Φ</sup> | 50.00 | 46.80 | 47.29 |
| Masked Modeling Loss<sub>feat</sub><sup>Ψ</sup> | 50.00 | 45.80 | 46.29 |
| Masked Modeling Loss<sub>feat</sub><sup>Φ</sup> | 49.50 | 47.35 | 47.93 |
| Reconstruction Loss<sub>patch</sub> | 49.50 | 46.96 | 47.33 |
| Reconstruction Loss<sub>feat</sub> | 48.50 | 45.95 | 47.18 |
| Contrastive Loss | 43.50 | 42.91 | 44.77 |
| Knowledge Distillation Loss | 49.50 | 45.43 | 47.09 |
| Hybrid Semantic Loss<sub>patch</sub> | 50.50 | 46.84 | 47.59 |
| Hybrid Semantic Loss<sub>feat</sub> | 52.00 | 48.51 | 48.06 |
| **+ Position Embedding** | **53.00** | **48.85** | **48.00** |{{< /table-caption >}}
> 🔼 본 표는 논문의 2.2절 'LLM-embedded Semantic Encoding'에서 다양한 자기 지도 학습 손실 함수를 사용하여 3D 포인트 토큰을 학습시킨 결과를 보여줍니다.  특히, 마스크 비율(mask ratio)이 60%인 경우와 30%인 경우의 결과를 비교 분석하고 있습니다.  Hybrid Semantic Loss의 경우, patch와 feat는 각각 마스크 모델링 손실(masked modeling loss)과 재구성 손실(reconstruction loss)의 대상을 나타내며, 재구성 손실의 경우 feat와 patch 모두 대상이 됩니다.  각 손실 함수에 따른 GPT-4 점수와 S-BERT 점수를 비교하여 어떤 자기 지도 학습 방법이 3D LLM의 성능 향상에 가장 효과적인지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: LLM-embedded Semantic Encoding. In the pre-training stage, we explore the effects of various self-supervised learning losses targeting point tokens. ΨΨ\Psiroman_Ψ represents a mask ratio of 60%, while ΦΦ\Phiroman_Φ represents a mask ratio of 30%. The subscript patch and feat represent the loss target. For Hybrid Semantic Loss, the subscript patch and feat represent the masked modeling target, while the reconstruction target is the corresponding feat and patch.
> </details>

{{< table-caption >}}
| Method | Cls | Cap | Cap |
|---|---|---|---|
| **Method** | **Cls** | **Cap** | **Cap** |
| **GPT-4** | **GPT-4** | **S-BERT** |  |
| PointLLM-7B | 53.00 | 44.85 | 47.47 |
| l=1 | 52.50 | 48.86 | 48.14 |
| l=2 | 50.00 | 46.76 | 47.95 |
| l=3 | 48.00 | 45.51 | 46.85 |
| H=2 | 53.50 | 49.13 | 48.33 |
| H=4 | 52.50 | 48.39 | 47.75 |
| H=8 | 51.00 | 48.95 | 47.97 |
| **+ Self-Attn.** | **55.00** | **50.92** | **48.61** |{{< /table-caption >}}
> 🔼 표 4는 논문의 지시 조정 단계에서 계층적 기하학적 집계 전략에 대한 실험 결과를 보여줍니다.  l은 집계 및 전파 연산의 횟수를 나타내고, H는 l번의 집계와 l번의 전파 연산 사이에 있는 LLM 계층의 수를 나타냅니다. '+ Self-Attn.'은 게이트 제어 자기 주의 메커니즘을 집계 과정에 통합했음을 의미합니다. 이 표는 다양한 하이퍼파라미터 설정(l과 H의 조합)에 따른 모델 성능(GPT-4, Sentence-BERT, SimCSE 기준)을 비교 분석하여 최적의 계층적 기하학적 집계 전략을 찾는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Hierarchical Geometry Aggregation. In the instruction tuning stage, we conduct the experiments of Hierarchical Geometry Aggregation strategy. l𝑙litalic_l represents the number of aggregation and propagation operations. H𝐻Hitalic_H refers to the LLM layers between l𝑙litalic_l aggregation and l𝑙litalic_l propagation operations. + Self-Attn. represents the incorporation of the gated self-attention in the aggregation.
> </details>

{{< table-caption >}}
| Model | GPT-4 | Sentence-BERT | SimCSE | BLEU-1 | ROUGE-L | METEOR | GPT-4 | GPT-4 | QA |
|---|---|---|---|---|---|---|---|---|---|
| InstructBLIP-7B (Dai et al., 2023) | 45.34 | 47.41 | 48.48 | 4.27 | 8.28 | 12.99 | 43.50 |  – |  |
| InstructBLIP-13B (Dai et al., 2023) | 44.97 | 45.90 | 48.86 | 4.65 | 8.85 | 13.23 | 34.25 |  – |  |
| LLaVA-7B (Liu et al., 2024) | 46.71 | 45.61 | 47.10 | 3.64 | 7.70 | 12.14 | 50.00 |  – |  |
| LLaVA-13B (Liu et al., 2024) | 38.28 | 46.37 | 45.90 | 4.02 | 8.15 | 12.58 | 51.75 | 47.90 |  |
| 3D-LLM (Hong et al., 2023) | 33.42 | 44.48 | 43.68 | 16.91 | 19.48 | 19.73 | 45.25 |  – |  |
| PointLLM-7B (Xu et al., 2023) | 44.85 | 47.47 | 48.55 | 3.87 | 7.30 | 11.92 | 53.00 | 41.20 |  |
| PointLLM-13B (Xu et al., 2023) | 48.15 | 47.91 | 49.12 | 3.83 | 7.23 | 12.26 | 54.00 | 46.60 |  |
| ShapeLLM-7B (Qi et al., 2024) | 46.92 | 48.20 | 49.23 |  – |  – |  – | 54.50 | 47.40 |  |
| ShapeLLM-13B (Qi et al., 2024) | 48.94 | 48.52 | 49.98 |  – |  – |  – | 54.00 | 53.10 |  |
| Enel-7B | 50.92 | 48.61 | 49.31 | 3.88 | 7.20 | 12.50 | 55.00 | 42.70 |  |{{< /table-caption >}}
> 🔼 표 5는 다양한 3D 이해 과제에서 여러 모델의 성능을 비교한 표입니다. GPT-4 평가를 중심으로 하되, Sentence-BERT 및 SimCSE 와 같은 데이터 중심 지표도 함께 제시하여 모델 성능에 대한 보다 포괄적인 평가를 제공합니다.  다양한 3D 과제(분류, 캡션 생성, 질의응답)에 대한 각 모델의 GPT-4 점수, Sentence-BERT 점수, SimCSE 점수, 그리고 추가적인 지표(BLEU-1, ROUGE-L, METEOR)를 보여줍니다. 이를 통해 각 모델의 강점과 약점을 비교 분석하고, 3D 이해 분야에서의 최첨단 기술 동향을 파악하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Comparison of different models on various 3D understanding tasks. A primary focus is placed on GPT-4 evaluation, along with data-driven metrics (Sentence-BERT and SimCSE).
> </details>

{{< table-caption >}}
| Model | GPT-4 | Sentence-BERT | SimCSE | BLEU-1 | ROUGE-L | METEOR | Cls | GPT-4 |
|---|---|---|---|---|---|---|---|---|
| **Enel-7B** | 50.92 | 48.61 | 49.31 | 3.88 | 7.20 | 12.50 | 55.00 |
| – Hybrid Semantic Loss | 47.19 | 48.07 | 48.31 | 3.46 | 7.41 | 11.84 | 50.61 |
| Hybrid Semantic Loss<sub>patch</sub><sup>Φ</sup> | 49.05 | 48.82 | 49.20 | 4.01 | 7.25 | 12.38 | 52.20 |
| Hybrid Semantic Loss<sub>patch</sub><sup>Ψ</sup> | 48.96 | 48.38 | 49.00 | 3.66 | 6.97 | 11.98 | 52.00 |
| Hybrid Semantic Loss<sub>feat</sub><sup>Ψ</sup> | 49.63 | 48.00 | 48.62 | 3.78 | 6.88 | 12.33 | 51.50 |
| – gate mechanism | 49.26 | 48.41 | 48.93 | 3.71 | 7.12 | 12.47 | 53.50 |
| l=2,H=2,O=0 | 48.81 | 48.10 | 48.57 | 3.70 | 6.99 | 12.01 | 51.50 |
| l=2,H=4,O=0 | 49.02 | 48.47 | 48.61 | 3.65 | 7.10 | 12.31 | 52.00 |
| l=2,H=2,O=2 | 48.96 | 47.96 | 48.89 | 3.80 | 7.05 | 12.55 | 52.00 |
| l=2,H=4,O=2 | 49.58 | 48.70 | 48.84 | 3.84 | 7.56 | 12.76 | 53.00 |{{< /table-caption >}}
> 🔼 표 6은 ENEL 모델의 구성 요소를 하나씩 변경해 가며 ablation 실험을 진행한 결과를 보여줍니다.  mask 비율(Ψ는 60%, Φ는 30%), Hybrid Semantic Loss의 적용 방식 (patch와 feat), aggregation 및 propagation 연산 횟수(l), aggregation과 propagation 연산 사이의 LLM 레이어 수(H), 그리고 개별 aggregation 또는 propagation 연산 사이의 LLM 레이어 수(O) 등을 변경하며 실험하였습니다.  각 설정에 따른 GPT-4 기반 분류 및 캡션 생성 성능의 변화를 비교 분석하여 모델 성능에 대한 각 요소의 영향을 평가합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Ablation Experiments. We begin the ablation experiments by changing the single configuration of the module from Enel. ΨΨ\Psiroman_Ψ represents a mask ratio of 60%, while ΦΦ\Phiroman_Φ represents a mask ratio of 30%. For Hybrid Semantic Loss, the subscript p⁢a⁢t⁢c⁢h𝑝𝑎𝑡𝑐ℎpatchitalic_p italic_a italic_t italic_c italic_h and f⁢e⁢a⁢t𝑓𝑒𝑎𝑡featitalic_f italic_e italic_a italic_t represent the masked modeling target, while the reconstruction target is the corresponding f⁢e⁢a⁢t𝑓𝑒𝑎𝑡featitalic_f italic_e italic_a italic_t and p⁢a⁢t⁢c⁢h𝑝𝑎𝑡𝑐ℎpatchitalic_p italic_a italic_t italic_c italic_h. l𝑙litalic_l represents the number of aggregation and propagation operations. H𝐻Hitalic_H refers to the LLM layers between l𝑙litalic_l aggregation and l𝑙litalic_l propagation operations. O𝑂Oitalic_O refers to the LLM layer between two individual aggregation or propagation operations.
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
{{< /gallery >}}