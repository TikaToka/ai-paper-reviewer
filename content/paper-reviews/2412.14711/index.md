---
title: "ReMoE: Fully Differentiable Mixture-of-Experts with ReLU Routing"
summary: "ReLU 라우팅을 사용하는 완전 미분 가능한 MoE 아키텍처 ReMoE를 통해 대규모 언어 모델의 확장성과 효율성을 획기적으로 개선했습니다!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Tsinghua University",]
showSummary: true
date: 2024-12-19
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.14711 {{< /keyword >}}
{{< keyword icon="writer" >}} Ziteng Wang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-25 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.14711" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.14711" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/remoe-fully-differentiable-mixture-of-experts" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)의 성능 향상을 위해서는 모델의 크기를 키우는 것이 일반적이지만, 계산 비용이 급격히 증가하는 문제가 있습니다. 이를 해결하기 위해 **희소하게 활성화되는 혼합 전문가(MoE) 모델**이 주목받고 있으며, 이는 일부 전문가만 선택적으로 활성화시켜 계산 비용을 절감하는 방식입니다. 하지만, 기존 MoE 모델에서 사용되는 TopK 라우터는 비미분 가능하여 성능 향상에 제약이 있었습니다. 



본 논문에서는 이러한 문제를 해결하기 위해 **ReLU 라우팅 기반의 완전히 미분 가능한 새로운 MoE 아키텍처인 ReMoE**를 제안합니다. ReMoE는 ReLU 활성화 함수를 라우터로 사용하여 연속적인 미분 가능성을 확보하고, 전문가 활성화의 희소성을 조절하여 계산 비용을 효율적으로 관리합니다. 실험 결과, ReMoE는 다양한 모델 크기, 전문가 수, 그리고 세분화 수준에서 기존 TopK 기반 MoE 모델보다 우수한 성능을 보였으며, 특히 전문가 수가 증가할수록 더욱 큰 성능 향상을 보여주었습니다.  이는 **대규모 언어 모델의 확장성 및 효율성을 크게 향상**시킬 수 있는 중요한 발견입니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} ReMoE는 기존 TopK 라우터의 비미분 가능성 문제를 ReLU 기반의 완전 미분 가능한 라우터로 해결했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} ReMoE는 토큰과 계층에 걸쳐 계산 자원을 효율적으로 동적으로 할당하여 기존 MoE 모델보다 우수한 확장성과 성능을 보였습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} ReMoE는 다양한 모델 크기, 전문가 수, 그리고 세분화 수준에서 TopK 기반 MoE 모델을 꾸준히 능가하는 성능을 입증했습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **희소하게 활성화되는 혼합 전문가(MoE) 모델의 확장성을 제한하는 기존의 비미분 가능한 TopK 라우터 문제를 해결**하기 위해 제시된 ReMoE의 중요성을 보여줍니다.  **ReMoE는 ReLU 기반의 완전 미분 가능한 라우터를 도입**하여 효율적인 계산 자원 할당을 가능하게 하고, 다양한 모델 크기와 전문가 수에 걸쳐 기존 TopK 기반 MoE 모델을 능가하는 성능을 보입니다. 이는 **대규모 언어 모델의 확장성과 효율성을 향상**시키는 데 중요한 발견이며, 향후 연구 방향에 대한 새로운 가능성을 제시합니다.  **특히, 대규모 모델 개발 및 배포에 직접적인 영향**을 미치며,  연구자들에게 실질적인 도움을 제공합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.14711/x1.png)

> 🔼 그림 1은 TopK 라우팅을 사용하는 기존 MoE 모델과 ReLU 라우팅을 사용하는 ReMoE 모델의 계산 흐름을 비교하여 보여줍니다.  양수는 주황색으로, 음수는 파란색으로 표시되며, 색깔이 진할수록 절대값이 큼을 나타냅니다.  0 값은 희색으로 표시되어 있으며, 이는 계산량 감소 및 스파스성을 의미합니다. TopK 라우팅에서는 빨간색 점선 화살표가 불연속적인 연산을 나타냅니다.  ReMoE는 ReLU를 사용하여 계산 흐름을 완전히 미분 가능하게 만들어, TopK 라우팅 방식의 MoE 모델과 비교하여 개선된 점을 보여줍니다.  각 토큰에 대한 가중치 합산 과정과 활성화된 전문가(expert)의 선택 과정을 시각적으로 보여주어 두 모델의 차이점을 명확히 이해할 수 있도록 도와줍니다. 특히, ReMoE는 연속적인 ReLU 함수를 사용하여 그래디언트 계산 과정에서 발생할 수 있는 불연속성 문제를 해결합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Compute flows of vanilla MoE with TopK routing and ReMoE with ReLU routing. Positive values are shown in orange, and negative values in blue, with deeper colors representing larger absolute values. Zeros, indicating sparsity and computation savings, are shown in white. The red dash arrows in TopK routing indicate discontinuous operations. Compared with TopK routing MoE, ReMoE uses ReLU to make the compute flow fully differentiable.
> </details>





{{< table-caption >}}
| Size | #Parameters | hidden_size | num_layers | num_heads | num_groups | GFLOPs |
|---|---|---|---|---|---|---|
| Small | 182M | 768 | 12 | 12 | 4 | 995 |
| Medium | 469M | 1024 | 24 | 16 | 4 | 2873 |
| Large | 978M | 1536 | 24 | 16 | 4 | 5991 |{{< /table-caption >}}

> 🔼 표 1은 논문에서 사용된 세 가지 크기의 기본 트랜스포머 모델(Small, Medium, Large)의 설정을 보여줍니다. 각 모델은 매개변수의 수, 은닉층 크기, 레이어 수, 헤드 수, 그룹 수, 그리고 단일 시퀀스에 대한 FLOP(부동 소수점 연산 수)를 나타냅니다. FLOP는 Narayanan et al.(2021)의 방법에 따라 계산됩니다. 이 표는 모델의 규모와 계산 비용을 비교하는 데 유용합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Configurations for the dense backbones. FLOPs are calculated with a single sequence according to Narayanan et al. (2021).
> </details>





### In-depth insights


#### MoE's Differentiability
본 논문에서 Mixture-of-Experts(MoE)의 미분 가능성에 대한 심층적인 논의는 TopK 라우터의 비연속성 문제를 해결하기 위한 ReMoE의 핵심 아이디어를 중심으로 전개됩니다. **기존 TopK 라우터는 이산적인 경사를 가지므로 역전파 과정에서 불안정성을 초래하지만**, ReMoE는 ReLU 라우터를 도입하여 **모델 전체를 완벽하게 미분 가능하게 만들었습니다.**  이를 통해 기울기 기반 학습의 효율성을 높이고, 모델의 안정적인 훈련 및 성능 향상을 도모합니다. ReLU 라우터의 연속적인 특성은 전문가들의 동적 할당 및 토큰 간의 계산 자원 효율적인 분배를 가능하게 하여, **모델의 확장성 및 스케일러빌리티 향상**에도 기여합니다.  **ReMoE의 미분 가능성은 단순한 기술적 개선을 넘어, MoE 모델의 이론적 이해와 실제 적용에 있어 중요한 전환점**을 제시합니다.  이러한 미분 가능성을 통해 더욱 복잡하고 정교한 MoE 아키텍처 개발의 토대를 마련할 뿐 아니라, 다양한 응용 분야에서 MoE 모델의 활용성을 극대화할 수 있는 가능성을 열어줍니다.

#### ReLU Routing
ReLU 라우팅은 기존의 TopK 라우팅 방식의 단점을 극복하기 위해 제안된 새로운 접근 방식입니다. **TopK 라우팅은 이산적이고 미분 불가능하여 성능 및 확장성에 제약이 있지만, ReLU 라우팅은 연속적이고 미분 가능하여 이러한 문제를 해결합니다.** ReLU 활성화 함수를 이용하여 각 전문가의 활성화 여부를 제어함으로써, **네트워크는 각 토큰에 대해 어떤 전문가를 활성화할지 연속적으로 학습할 수 있습니다.**  이는 계산 자원을 효율적으로 할당하고, 토큰과 레이어 간의 계산량을 동적으로 조절하는 데 도움이 됩니다. 특히, **ReLU 라우팅의 연속성은 학습 과정에서 안정성을 높이고, 다양한 모델 크기, 전문가 수, 그리고 세분화 수준에서 일관되게 우수한 성능을 보여줍니다.**  또한, 기존의 MoE 아키텍처보다 뛰어난 확장성을 제공하며, 전문가 수가 증가함에 따라 성능 향상이 더욱 두드러집니다.  **ReLU 라우팅은 단순하면서도 효과적인 TopK 라우팅의 대체 방식**으로, 다양한 모델과 작업에 적용 가능성이 높습니다.

#### Sparsity Control
본 논문에서 **희소성 제어(Sparsity Control)**는 ReLU 활성화 함수를 기반으로 하는 ReMoE 모델의 핵심 구성 요소입니다.  기존의 TopK 라우터 방식과 달리, ReMoE는 연속적이고 미분 가능한 ReLU 라우터를 사용하여 각 전문가(expert)의 활성화 여부를 부드럽게 조절합니다. 이를 통해 **불연속성으로 인한 학습의 어려움을 해결**하고, 모델의 성능과 확장성을 향상시킵니다.  **적응적 L1 정규화(Adaptive L1 Regularization)**를 통해 ReLU 라우터의 출력 값을 제어함으로써 목표 희소성을 달성합니다.  **목표 희소성 달성은 계산 비용 관리**와 직결되며,  **계산 자원의 효율적인 할당**을 가능하게 합니다.  또한,  **부하 균형(Load Balancing)**을 고려한 정규화 방식을 통해 특정 전문가에게 과도한 부하가 집중되는 현상을 방지합니다.  이러한 희소성 제어 전략은  **모델의 확장성과 성능 개선**에 중요한 역할을 수행합니다.

#### Scalability
본 논문에서 제시된 ReMoE 모델의 확장성은 여러 측면에서 주목할 만합니다. **매우 많은 매개변수를 가진 모델에서도 효율적으로 작동**하며, 기존의 MoE 모델이 갖는 한계를 극복합니다. 특히, **전문가 수 증가에 따른 성능 저하 없이 확장성을 유지**하는 점은 실용적인 측면에서 큰 의미를 지닙니다. 이는 ReMoE의 **연속적이고 미분 가능한 ReLU 라우팅 방식** 덕분이며, 기존의 이산적인 라우팅 방식의 단점을 해결합니다. 또한, ReMoE는 **다양한 크기의 모델과 계층 구조에 적용** 가능하며, **토큰과 계층에 걸쳐 계산 자원을 효율적으로 할당**합니다.  **토큰의 빈도에 따라 전문가를 동적으로 할당**하는 기능은 연산 효율성을 더욱 높입니다.  **그래뉼러티(Granularity) 수준에서도 성능 저하 없이 확장**되며, 이는 **다양한 모델 크기와 복잡도에 적용** 가능함을 시사합니다.  **결론적으로 ReMoE는 확장성과 효율성을 균형 있게 고려한 설계**로 기존 MoE 모델의 한계를 뛰어넘는 혁신적인 모델임을 보여줍니다.

#### Dynamic Allocation
본 논문에서 제시된 ReMoE 모델의 핵심적인 특징 중 하나는 **동적 자원 할당**입니다. 기존의 MoE 모델들은 특정 토큰에 대해 미리 정해진 전문가 집합을 활성화하는 반면, ReMoE는 ReLU 활성화 함수를 기반으로 각 토큰마다 필요한 전문가를 **실시간으로 선택**합니다.  이를 통해 각 토큰의 복잡도에 따라 계산 자원을 **유동적으로 배분**하여 효율성을 극대화합니다.  **빈도가 높은 토큰**에는 적은 수의 전문가를 할당하고, **빈도가 낮은 토큰**에는 더 많은 전문가를 할당하여 계산량을 최적화하는 동작을 보입니다.  이는 마치 Huffman 코딩과 유사한 방식으로, 빈번한 토큰에는 짧은 코드를, 드문 토큰에는 긴 코드를 할당하는 것과 같습니다.  **연산 자원의 효율적인 사용**은 ReMoE의 성능 향상에 중요한 요인이며, 특히 많은 수의 전문가를 사용하는 대규모 모델에서 그 효과가 더욱 두드러집니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.14711/x2.png)

> 🔼 그림 2는 TopK와 ReLU의 차이점을 보여줍니다. TopK는 k번째로 큰 값을 기준으로 그 값보다 작은 값은 0으로 설정하는 불연속적인 함수입니다. 반면에 ReLU는 0을 기준으로 0보다 작은 값은 0, 0보다 큰 값은 그대로 유지하는 연속적인 함수입니다. 이 그림은 TopK의 불연속성으로 인해 발생하는 문제점과 ReLU의 연속성이 제공하는 이점을 시각적으로 보여줍니다. ReLU의 연속적인 특성은 학습 과정에서 안정성과 효율성을 높입니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Comparison between TopK and ReLU.
> </details>



![](https://arxiv.org/html/2412.14711/x3.png)

> 🔼 그림 3은 E=8, k=1인 ReMoE 모델의 스파스성(희소성)을 보여줍니다. 목표로 하는 스파스성 수준을 효과적으로 유지함을 보여주는 그래프입니다. 모든 단계의 스파스성 값을 평균이나 샘플링 없이 그대로 플롯하여 나타냅니다. 처음 100단계의 워밍업 단계는 제외하고 평균과 표준 편차를 계산합니다. 즉, 그림은 ReMoE 모델이 학습 과정 전반에 걸쳐 원하는 수준의 스파스성을 잘 유지하며, 안정적으로 학습됨을 시각적으로 보여줍니다. 워밍업 단계를 제외한 이유는 초기 학습 단계에서는 모델이 아직 안정화되지 않았기 때문입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: The sparsity of ReMoE with E=8,k=1formulae-sequence𝐸8𝑘1E=8,k=1italic_E = 8 , italic_k = 1 is effectively maintained around the desired target. Sparsity values for all steps are plotted without averaging or sampling. The mean and standard deviation are calculated excluding the first 100 warm-up steps.
> </details>



![](https://arxiv.org/html/2412.14711/x4.png)

> 🔼 그림은 ReMoE의 훈련 과정에서 각 단계별 스파스(희소성) 수준을 보여줍니다.  세로축은 𝑖 번째 단계에서의 평균 스파스 값 Sᵢ 를 나타내고, 가로축은 훈련 단계를 나타냅니다. 그림을 통해 ReMoE 모델이 훈련 초기에 거의 모든 전문가를 활성화하는 밀집(dense) 단계, 이후 스파스성이 증가하는 과도기적 단계, 그리고 목표 스파스성에 도달하는 안정적인 단계를 거치는 것을 알 수 있습니다.  이는 ReMoE의 적응적 L1 정규화를 통해 제어되는 스파스성이 훈련 과정에서 어떻게 변화하는지를 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (a) Sparsity Sisubscript𝑆𝑖S_{i}italic_S start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT
> </details>



![](https://arxiv.org/html/2412.14711/x5.png)

> 🔼 그림 (b)는 ReMoE 모델 학습 중에 사용되는 두 가지 중요한 항을 보여줍니다. 첫 번째는 적응적 L1 규제화에 사용되는 계수 항 λi이며, 두 번째는 L1 규제화 항 Lreg 입니다. 이 그림은 각 항의 값이 학습 단계에 따라 어떻게 변화하는지 보여주는 그래프를 나타냅니다.  λi는 ReLU 출력의 스파스성을 제어하는 역할을 하며, Lreg는 모델의 스파스성을 유도하기 위해 손실 함수에 추가되는 규제화 항입니다. 이 두 항의 상호작용을 통해 ReMoE는 계산 비용을 제어하면서 성능을 향상시킬 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (b) Coefficient term λisubscript𝜆𝑖\lambda_{i}italic_λ start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT and regularization term ℒr⁢e⁢gsubscriptℒ𝑟𝑒𝑔\mathcal{L}_{reg}caligraphic_L start_POSTSUBSCRIPT italic_r italic_e italic_g end_POSTSUBSCRIPT
> </details>



![](https://arxiv.org/html/2412.14711/x6.png)

> 🔼 그림 (c)는 언어 모델 손실 함수 (ℒl⁢msubscriptℒ𝑙𝑚)와 전체 정규화 항 (λi⁢ℒr⁢e⁢gsubscript𝜆𝑖subscriptℒ𝑟𝑒𝑔)의 변화를 보여줍니다.  훈련 과정에서 언어 모델 손실은 감소하는 반면, 정규화 항은 처음에는 작게 시작하여 점차 증가합니다. 이는 ReMoE 모델이 희소성을 제어하고 과적합을 방지하기 위해 정규화를 사용하는 방법을 보여줍니다.  정규화 강도는 훈련 단계에 따라 조정되며, 손실 함수와 균형을 이루어 모델 성능을 최적화합니다. 초기 단계에서는 언어 모델의 성능 향상에 초점을 맞추고, 훈련이 진행됨에 따라 희소성을 높여 계산 비용을 줄이는 데 초점을 맞춥니다.
> <details>
> <summary>read the caption</summary>
> (c) Language model loss ℒl⁢msubscriptℒ𝑙𝑚\mathcal{L}_{lm}caligraphic_L start_POSTSUBSCRIPT italic_l italic_m end_POSTSUBSCRIPT and overall regularization λi⁢ℒr⁢e⁢gsubscript𝜆𝑖subscriptℒ𝑟𝑒𝑔\lambda_{i}\mathcal{L}_{reg}italic_λ start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT caligraphic_L start_POSTSUBSCRIPT italic_r italic_e italic_g end_POSTSUBSCRIPT
> </details>



![](https://arxiv.org/html/2412.14711/x7.png)

> 🔼 본 그림은 ReMoE 모델의 학습 과정에서 자연스럽게 나타나는 세 단계(Stage)를 보여줍니다. 먼저, Dense Stage에서는 모델이 전체 Expert들을 활성화하여 밀집된(dense) 방식으로 학습합니다. 이후, Dense to Sparse Stage에서는 ReLU 활성화 함수의 특성과 적응적 L1 정규화를 통해 점진적으로 Expert 활성화의 희소성(sparsity)을 높여갑니다. 마지막으로 Sparse Stage에서는 목표하는 희소성 수준에 도달하여 안정적인 학습을 수행합니다. 각 Stage별로 Sparsity, L1 정규화 계수(λi), 언어 모델 손실(Llm) 및 전체 정규화 손실(λiLreg)의 변화를 보여주는 그래프가 함께 제시되어, ReMoE 학습 과정의 동적인 특성을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Natural Three Stage Training in ReMoE.
> </details>



![](https://arxiv.org/html/2412.14711/x8.png)

> 🔼 그림 5는 다양한 라우팅 방법(TopK, ReLU, Lory, SparseMixer-v2, Expert Choice, Deterministic Hash 등)을 사용하여 학습된 Mixture-of-Experts (MoE) 모델의 학습 곡선을 보여줍니다.  각 라우팅 방법에 따른 손실 함수 값의 변화를 토큰 수에 따라 나타내어,  다양한 라우팅 기법의 학습 효율성과 수렴 속도를 비교 분석합니다.  ReMoE의 학습 곡선은 다른 방법들에 비해 안정적이고 빠른 수렴을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Training curves of different routing methods.
> </details>



![](https://arxiv.org/html/2412.14711/x9.png)

> 🔼 이 그림은 논문의 4.3절 'ReMoE의 확장성'에서 ReMoE 모델의 확장성을 보여줍니다.  특히 활성화 매개변수의 수(N)에 따른 ReMoE의 성능을 보여주는 그래프입니다.  다양한 크기의 모델(1억 8천2백만, 4억 6천9백만, 9억 7천8백만 매개변수)에 대해 ReMoE와 기존 MoE 모델의 검증 손실(validation loss)을 비교하여 ReMoE가 모델 크기가 증가함에 따라 기존 MoE보다 더 나은 성능을 보임을 시각적으로 나타냅니다.  세로축은 검증 손실을, 가로축은 매개변수의 수를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> (a) Scaling in N𝑁Nitalic_N
> </details>



![](https://arxiv.org/html/2412.14711/x10.png)

> 🔼 그림 (b)는 활성화 매개변수(N)와 그래뉼러리티(G)를 고정한 상태에서 전문가 수(E)에 따른 ReMoE의 확장성을 보여줍니다.  다양한 전문가 수(E)에 대해 검증 손실을 측정하여 ReMoE의 성능을 평가합니다. 이 그래프는 ReMoE가 전문가 수가 증가함에 따라 지속적으로 MoE를 능가하며, 특히 전문가 수가 많을 때 성능 향상이 더욱 두드러짐을 보여줍니다. ReMoE의 차별화된 라우팅 전략이 많은 전문가를 효과적으로 활용하여 모델의 표현력과 일반화 능력을 향상시키는 데 효과적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (b) Scaling in E𝐸Eitalic_E
> </details>



![](https://arxiv.org/html/2412.14711/x11.png)

> 🔼 그림 (c)는 ReMoE의 확장성을 보여주는 그래프입니다.  세로축은 검증 손실(validation loss)이고, 가로축은 모델의 세분성(granularity, G)입니다.  세분성이란 각 전문가(expert)를 더 작은 하위 전문가들로 나누는 정도를 나타냅니다.  이 그래프는 다양한 세분성 수준에서 ReMoE와 기존 MoE의 성능을 비교하여, ReMoE가 더 높은 세분성에서도 더 낮은 검증 손실을 유지하며 우수한 성능을 보임을 보여줍니다.  다양한 모델 크기(N), 전문가 수(E)에 대해서도 유사한 실험 결과를 보여주는 다른 그래프(a)와 (b)와 함께 ReMoE의 확장성을 종합적으로 제시합니다.
> <details>
> <summary>read the caption</summary>
> (c) Scaling in G𝐺Gitalic_G
> </details>



![](https://arxiv.org/html/2412.14711/x12.png)

> 🔼 그림 6은 활성 매개변수(N), 전문가 수(E) 및 세분성(G)에 따른 ReMoE의 확장성을 보여줍니다. 기본 설정은 N=182M, E=8, G=1, k=1입니다. Y축은 300억 토큰에 대한 학습 후 각 모델의 검증 손실을 나타냅니다. ReMoE는 모든 구성에서 MoE를 일관되게 능가합니다. 이 그림은 모델의 크기, 전문가 수 및 각 토큰에 대해 활성화되는 전문가의 세분성 수준을 변화시키면서 모델 성능에 미치는 영향을 보여줍니다. ReMoE 모델은 다른 설정에서도 일관되게 MoE 모델보다 성능이 우수하다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Scalability of ReMoE with respect to the number of active parameters (N𝑁Nitalic_N), expert count (E𝐸Eitalic_E), and granularity (G𝐺Gitalic_G). Default config is N=182⁢M,E=8,G=1,k=1formulae-sequence𝑁182Mformulae-sequence𝐸8formulae-sequence𝐺1𝑘1N=182\text{M},E=8,G=1,k=1italic_N = 182 M , italic_E = 8 , italic_G = 1 , italic_k = 1. The Y-axis represents the validation loss of each model after training on 30B tokens. ReMoE consistently outperforms MoE across all configurations.
> </details>



![](https://arxiv.org/html/2412.14711/x13.png)

> 🔼 이 그림은 ReMoE 모델에서 토큰의 빈도와 전문가 할당 간의 상관관계를 보여줍니다. x축은 평균 활성 전문가 수를 기준으로 정렬된 토큰 ID이고, y축은 토큰의 빈도(로그 스케일)입니다.  이 그림은 ReMoE 모델이 자주 등장하는 토큰에는 적은 수의 전문가를 할당하고, 드물게 등장하는 토큰에는 더 많은 전문가를 할당하여 계산 자원을 효율적으로 사용하는 것을 보여줍니다. 이는 허프만 트리의 원리와 유사하며, ReMoE 모델의 동적 전문가 할당 메커니즘을 시각적으로 보여주는 중요한 그림입니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Correlation between expert allocation and token frequency in ReMoE. X-axis is sorted by average active expert count and token frequency is in log-scale.
> </details>



![](https://arxiv.org/html/2412.14711/x14.png)

> 🔼 본 그림은 부하 균형을 적용한 경우와 적용하지 않은 경우에 대한 MoE(Mixture-of-Experts)와 ReMoE(ReLU Routing 기반 MoE)의 학습 곡선을 보여줍니다.  부하 균형은 모델의 성능 향상에 중요한 역할을 하며,  부하 균형을 적용했을 때 모델의 손실이 더 빨리 감소하는 것을 확인할 수 있습니다.  MoE와 ReMoE 모두 부하 균형 적용 시 성능이 향상되지만, ReMoE는 부하 균형 적용 여부에 덜 민감한 것을 보여줍니다.  그림은 ReMoE가 부하 균형이 없더라도 TopK 기반 MoE보다 우수한 성능을 낸다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (a) Training curves of MoE and ReMoE with and without load balancing
> </details>



![](https://arxiv.org/html/2412.14711/x15.png)

> 🔼 해당 그림은 부하 분산 (Load Balancing, LB) 없이 ReLU 라우팅을 사용하는 ReMoE 모델에서 각 전문가(Expert)에게 라우팅된 토큰의 평균 비율을 보여줍니다.  각 셀의 색깔은 해당 전문가에게 라우팅된 토큰의 비율을 나타내며, 흰색은 1/64 미만의 토큰이 라우팅된 비활성 전문가를 나타냅니다. 이를 통해 모델 내에서 전문가의 활성화 비율과 토큰 분포의 불균형 여부를 시각적으로 확인할 수 있습니다.  특히, 특정 전문가에게 과도하게 토큰이 집중되는 현상(부하 불균형)이 있는지 여부를 파악하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> (b) Average routed tokens ratio of ReMoE w.o. LB
> </details>



![](https://arxiv.org/html/2412.14711/x16.png)

> 🔼 이 그림은 Load Balancing을 적용한 ReMoE 모델에서 각 전문가에게 라우팅된 토큰의 평균 비율을 보여줍니다.  각 셀의 색깔은 해당 전문가에게 라우팅된 토큰의 비율을 나타내며, 흰색은 1/64 미만의 토큰이 라우팅된 비활성 전문가를 나타냅니다. 이는 ReMoE가 토큰을 전문가들에게 얼마나 효율적으로 분배하는지 보여주는 시각적 자료입니다.  다양한 레이어에서의 토큰 분배 패턴을 보여주어, 모델의 동작 방식에 대한 이해를 돕습니다.
> <details>
> <summary>read the caption</summary>
> (c) Average routed tokens ratio of ReMoE w. LB
> </details>



![](https://arxiv.org/html/2412.14711/x17.png)

> 🔼 이 그림은 ReMoE 모델에서 각 레이어별로 활성화되는 전문가(expert)의 비율, 즉 스파스티(sparsity)를 보여줍니다.  ReMoE는 ReLU 활성화 함수를 사용하여 전문가를 선택적으로 활성화하는데, 이 그림은 각 레이어에서 ReLU 게이트를 통과하여 실제로 활성화된 전문가의 비율을 시각적으로 나타냅니다.  레이어별 스파스티의 변화를 통해 ReMoE 모델의 학습 과정과 계층별 특징을 파악하는 데 도움이 됩니다.  수평축은 레이어 번호를 나타내고, 수직축은 각 레이어에서 활성화된 전문가의 비율을 나타냅니다. 높은 값은 해당 레이어에서 많은 전문가가 활성화되었다는 것을, 낮은 값은 소수의 전문가만 활성화되었다는 것을 의미합니다.
> <details>
> <summary>read the caption</summary>
> (d) Sparsity across different layers in ReMoE
> </details>



![](https://arxiv.org/html/2412.14711/x18.png)

> 🔼 그림 8은 MoE와 ReMoE에서 부하 분산의 역할에 대한 관찰 결과를 보여줍니다. (a)는 부하 분산을 적용했을 때와 적용하지 않았을 때 MoE와 ReMoE의 학습 곡선을 비교합니다. 부하 분산이 없는 MoE는 학습이 불안정하고 성능이 저하되는 반면, ReMoE는 부하 분산 여부에 관계없이 안정적인 성능을 보입니다. (b)는 부하 분산이 없는 ReMoE에서 라우팅된 토큰 비율의 평균을 보여주는 히트맵입니다. 흰색 정사각형은 64개 미만의 토큰이 라우팅된 비활성 전문가를 나타냅니다. 부하 분산이 없는 경우 일부 전문가가 비활성화되어 모델의 용량이 제한될 수 있습니다. (c)는 부하 분산이 있는 ReMoE에서 라우팅된 토큰 비율의 평균을 보여주는 히트맵입니다. 부하 분산을 통해 모든 전문가가 효율적으로 활용되고 있습니다. (d)는 ReMoE에서 계층별 스파스성을 보여주는 그래프입니다. 부하 분산을 통해 ReMoE는 계층 전반에 걸쳐 보다 부드러운 스파스성 분포를 달성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Observations on the role of load balancing in MoE and ReMoE. White squares in (b) represent inactive experts with fewer than 1/64 tokens routed to them.
> </details>



![](https://arxiv.org/html/2412.14711/x19.png)

> 🔼 그림 (a)는 다양한 도메인(Arxiv, Books, C4, Github, StackExchange, Wiki)에 걸쳐 MoE 모델의 각 계층(Layer 0부터 11까지)에서 각 전문가(Expert 0부터 7까지)가 처리한 토큰 비율을 보여줍니다.  각 막대는 특정 도메인의 토큰이 특정 계층의 특정 전문가에 할당된 비율을 나타냅니다. 이 그림은 ReMoE가 도메인 특화된 전문가를 학습하여 특정 도메인의 토큰을 특정 전문가에 집중적으로 할당하는 경향을 보이는 반면, MoE는 도메인에 관계없이 전문가에 대한 토큰 할당이 균일하게 분포됨을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (a) Domain specialization of MoE
> </details>



![](https://arxiv.org/html/2412.14711/x20.png)

> 🔼 그림 (b)는 ReMoE 모델에서 도메인 특수화 현상을 보여줍니다. ReMoE는 각 전문가가 특정 도메인(예: Arxiv, Books, C4, Github, StackExchange, Wikipedia)에 특화되는 경향을 보이는데, 이는 각 도메인의 고유한 특징을 효율적으로 학습하고 활용하여 계산 자원을 할당하기 때문입니다. 이 그림은 각 레이어와 전문가별로 도메인별 평균 라우팅 토큰 비율을 보여줍니다. 회색 점선은 균일한 분포를 나타냅니다. ReMoE는 도메인별로 전문가 활성화 비율이 다르게 나타나 도메인 특수화가 더 강하게 나타나는 것을 보여줍니다.  반면에 MoE는 전문가 활성화가 도메인에 걸쳐 비교적 균일하게 나타나 도메인 특수화 정도가 낮음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) Domain specialization of ReMoE
> </details>



![](https://arxiv.org/html/2412.14711/x21.png)

> 🔼  그림 9는 12개의 레이어와 8개의 전문가를 가진 MoE와 ReMoE 모델에서 다양한 도메인에 걸쳐 평균 라우팅 토큰 비율을 보여줍니다. 회색 점선은 균일한 분포를 나타냅니다. ReMoE는 MoE보다 강력한 도메인 특수화를 보여줍니다. 이 그림은 각 도메인(Arxiv, Books, C4, Github, StackExchange, Wiki)에 대한 각 레이어의 8개 전문가에 대한 평균 라우팅 토큰 비율을 시각적으로 보여줍니다. 각 전문가가 특정 도메인에 얼마나 집중하는지(전문화)를 보여줍니다. ReMoE는 일부 전문가가 특정 도메인에 집중하는 경향을 보이는 반면, MoE는 전문가들 간에 더 균일한 분포를 보입니다. 이는 ReMoE의 아키텍처가 도메인 관련 지식을 전문가에 효율적으로 할당할 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Average routed tokens ratio for MoE and ReMoE across 12 layers and 8 experts in different domains. The gray dashed lines indicate uniform distribution. ReMoE shows stronger domain specialization.
> </details>



![](https://arxiv.org/html/2412.14711/x22.png)

> 🔼 그림 10은 MoE(Mixture-of-Experts)와 ReMoE(ReLU 기반 MoE)의 라우팅 안정성을 비교 분석한 결과를 보여줍니다.  'Flip rate'는 각 훈련 단계에서 활성화 상태가 변경된 전문가(expert)의 비율을 나타내며, 'Flip count'는 평균적으로 활성화 상태가 변경된 전문가의 수를 나타냅니다.  이 그림은 ReMoE의 라우팅이 MoE보다 훨씬 안정적임을 보여주는 여러 실험 결과를 담고 있습니다.  특히, 전문가 수가 증가함에 따라 MoE의 불안정성이 더욱 심화되는 반면, ReMoE는 안정성을 유지하는 것을 확인할 수 있습니다.  이러한 결과는 ReLU 라우팅의 연속적인 특성과 TopK 라우팅의 불연속적인 특성의 차이에서 기인합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Flip rate and flip count of MoE and ReMoE
> </details>



![](https://arxiv.org/html/2412.14711/x23.png)

> 🔼 표 3은 ReMoE 모델 학습에서 사용되는 하이퍼파라미터 λ₀의 값을 다르게 변화시켰을 때의 모델 성능(검증 손실)과 학습 안정화에 도달하는 데 걸리는 시간(세틀링 타임)을 보여줍니다. α 값은 1.2로 고정하고, λ₀ 값을 1e-16부터 1까지 변화시키면서 실험을 진행하였습니다. 결과적으로 λ₀ 값이 1e-8 부근일 때 가장 낮은 검증 손실을 보이며, 세틀링 타임 또한 비교적 짧은 것을 확인할 수 있습니다.  특히 λ₀ 값이 1e-4 이상으로 커지면 검증 손실이 증가하고 세틀링 타임이 길어지는 경향을 보입니다.  이 표는 ReMoE 모델 학습의 안정성과 효율성을 높이는 데 적절한 λ₀ 값을 찾는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Valid loss and settling time for different values of λ0subscript𝜆0\lambda_{0}italic_λ start_POSTSUBSCRIPT 0 end_POSTSUBSCRIPT with α=1.2𝛼1.2\alpha=1.2italic_α = 1.2.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | ARC-c | ARC-e | BoolQ | HellaSwag | LAMBADA | PIQA | RACE | Avg. |
|---|---|---|---|---|---|---|---|---|
| Dense | 19.45 | 43.35 | 54.40 | 28.61 | 31.09 | 61.97 | 28.52 | 38.20 |
| Hash | 19.28 | 45.45 | 54.95 | 29.68 | 31.44 | 63.06 | 27.66 | 38.79 |
| Lory | 20.31 | 42.97 | 49.54 | 28.75 | 32.35 | 62.24 | 27.75 | 37.70 |
| SparseMixer-v2 | 19.80 | 46.72 | 45.96 | 30.24 | 34.12 | 62.89 | 29.00 | 38.39 |
| EC | 18.86 | 42.97 | 60.21 | 29.14 | 29.26 | 61.92 | 27.37 | 38.53 |
| dMoE | 20.05 | 45.16 | 57.83 | 29.83 | 32.97 | 63.55 | 28.33 | 39.67 |
| ReMoE | 20.22 | 46.68 | 54.16 | 30.26 | 35.94 | 63.55 | 29.38 | 40.03 |{{< /table-caption >}}
> 🔼 본 표는 다양한 라우팅 방법(TopK, ReLU, Lory, SparseMixer-v2, EC, dMoE 등)을 사용하여 사전 학습된 모델의 다운스트림 작업(ARC, BoolQ, HellaSwag, LAMBADA, PIQA, RACE)에 대한 제로샷 정확도를 비교 분석한 결과를 보여줍니다.  각 라우팅 방법의 성능을 여러 가지 다운스트림 작업에 걸쳐 측정하여 비교함으로써 다양한 모델 규모와 전문가 수에 따른 성능의 차이를 보여줍니다. 이 표는 다양한 라우팅 기법들의 상대적인 강점과 약점을 파악하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Zero-shot accuracy of different routing methods on downstream tasks.
> </details>

{{< table-caption >}}
| λ₀ | 1e⁻¹⁶ | 1e⁻¹² | 1e⁻⁸ | 1e⁻⁴ | 1 |
|---|---|---|---|---|---| 
| Valid Loss | 2.031 | 2.029 | 2.032 | 2.036 | 2.032 |
| Settling time | 138 | 136 | 110 | 55 | 92† |{{< /table-caption >}}
> 🔼 표 5는 469M개의 매개변수, 8개의 전문가, 그리고 활성 전문가 수 k=1을 갖는 모델을 1200억 개의 토큰으로 학습시킨 결과를 보여줍니다.  다양한 하류 작업(ARC-C, ARC-e, BoolQ, HellaSwag, LAMBADA, PIQA, RACE)에 대한 검증 손실 및 정확도 점수가 제시되어 있으며, ReMoE 모델의 성능 우수성을 더 긴 학습 시간 후에도 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Performance of training N=𝑁absentN=italic_N =469M, E=8𝐸8E=8italic_E = 8, k=1𝑘1k=1italic_k = 1 models for 120B tokens.
> </details>

{{< table-caption >}}
| 
α | 1.05 | 1.1 | 1.2 | 1.3 | 1.5 |
|---|---|---|---|---|---| 
| Valid Loss | 2.033 | 2.028 | 2.032 | 2.029 | 2.057* |
| Settling time | 414 | 211 | 110 | 80 | 52 |
{{< /table-caption >}}
> 🔼 표 6은 4억 6900만개의 매개변수(N=469M), 8개의 전문가(E=8), 활성화된 전문가 수 1개(k=1)로 구성된 모델을 1200억개의 토큰으로 학습시킨 결과에 대한 각 단계별(Stage I, II, III) 학습 시간을 비교한 표입니다.  총 학습 시간과 각 단계별 시간을 시간(hour) 단위로 나타내어, ReMoE와 기존 MoE의 학습 시간 효율성을 비교 분석하는 데 사용되었습니다.  Stage I과 II는 ReMoE의 초기 단계로, 대부분의 전문가가 활성화되는 단계입니다.
> <details>
> <summary>read the caption</summary>
> Table 6: End-to-end training time comparison across stages (in hours). The time is measured on N=𝑁absentN=italic_N = 469M, E=8𝐸8E=8italic_E = 8, k=1𝑘1k=1italic_k = 1 models training over 120B tokens.
> </details>

{{< table-caption >}}
| Model | Valid Loss | ARC-c | ARC-e | BoolQ | HellaSwag | LAMBADA | PIQA | RACE | Avg. |
|---|---|---|---|---|---|---|---|---|---| 
| MoE | 1.716 | 23.62 | 52.40 | 53.94 | 35.43 | 43.64 | 68.34 | **31.48** | 44.12 |
| ReMoE | **1.689** | **25.34** | **55.22** | **55.96** | **36.76** | **45.82** | **68.93** | 30.43 | **45.49** |{{< /table-caption >}}
> 🔼 표 7은 TopK 라우팅 방식을 사용하는 기존 MoE 모델과 ReLU 라우팅 방식을 사용하는 ReMoE 모델의 처리량을 비교한 표입니다. TP는 텐서 병렬 처리 크기를 나타내고, Train Diff.와 Infer Diff.는 ReMoE와 MoE 간의 상대적인 TFLOPS 차이를 나타냅니다. ↑는 ReMoE가 더 빠르다는 것을, ↓는 ReMoE가 더 느리다는 것을 의미합니다.  즉, 이 표는 다양한 크기의 모델과 텐서 병렬 처리 크기에 대해 ReMoE의 성능을 기존 MoE와 비교하여 ReMoE의 효율성을 보여줍니다.  모델 크기와 텐서 병렬 처리 크기가 증가함에 따라 ReMoE의 속도 변화를 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Throughput comparison between TopK-routed MoE and ReLU-routed ReMoE models. TP indicates the tensor parallel size. Train Diff. and Infer Diff. indicate the relative TFLOPS difference of ReMoE compared to MoE, where ↑ denotes ReMoE is faster, and ↓ denotes it is slower.
> </details>

{{< table-caption >}}
| Model | Stage I | Stage II | Stage III | Total |
|---|---|---|---|---|
| MoE | 0.12 | 0.41 | 119.12 | 119.65 |
| ReMoE | 0.32 | 0.91 | 119.25 | 120.48 |{{< /table-caption >}}
> 🔼 표 8은 활성 매개변수 N의 크기에 따른 모델 성능 변화를 보여줍니다.  다양한 크기의 모델(182M, 469M, 978M 매개변수)에 대해,  다운스트림 작업(ARC, ARC-e, BoolQ, HellaSwag, LAMBADA, PIQA, RACE)에서의 정확도를 비교 분석합니다.  각 모델의 활성 매개변수 수가 증가함에 따라 성능이 향상되는 양상을 보여주며, ReMoE 모델이 기존 MoE 모델보다 우수한 성능을 보임을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Downstream results of scaling in active parameters N𝑁Nitalic_N.
> </details>

{{< table-caption >}}
| # Parameters | TP | Model | Train TFLOPS | Train Diff. | Infer TFLOPS | Infer Diff. |
|---|---|---|---|---|---|---|
| 182M | 1 | MoE | 103.49 | ↑1.82% | 78.47 | ↑2.19% |
|  |  | ReMoE | 105.38 |  | 80.19 |  |
| 469M | 1 | MoE | 138.58 | ↓1.37% | 107.52 | ↑3.89% |
|  |  | ReMoE | 136.69 |  | 111.71 |  |
| 978M | 1 | MoE | 160.46 | ↓1.77% | 153.11 | ↓0.23% |
|  |  | ReMoE | 157.61 |  | 152.76 |  |
| 978M | 2 | MoE | 133.40 | ↓0.68% | 118.55 | ↓1.08% |
|  |  | ReMoE | 132.49 |  | 117.27 |  |
| 978M | 4 | MoE | 103.61 | ↓2.29% | 85.96 | ↑2.33% |
|  |  | ReMoE | 101.23 |  | 87.96 |  |{{< /table-caption >}}
> 🔼 표 9는 전문가 수(E)를 확장할 때의 다운스트림 결과를 보여줍니다. 이 표는 다양한 크기의 모델과 다양한 수의 전문가를 사용하여 여러 가지 하류 작업(ARC, ARC-e, BoolQ, HellaSwag, LAMBADA, PIQA, RACE)에 대한 정확도를 비교합니다. 이를 통해 전문가 수를 늘리는 것이 모델 성능에 미치는 영향과 ReMoE가 이러한 확장성 측면에서 어떻게 동작하는지에 대한 통찰력을 제공합니다.  다른 말로 하면, 이 표는 모델 크기와 전문가 수의 조합에 따른 성능을 보여주어, ReMoE의 확장성을 평가하는 데 유용합니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Downstream results of scaling in expert count E𝐸Eitalic_E.
> </details>

{{< table-caption >}}
| Model | N | ARC-c | ARC-e | BoolQ | HellaSwag | LAMBADA | PIQA | RACE | Avg. |
|---|---|---|---|---|---|---|---|---|---| 
| Dense | 182M | 19.45 | 43.35 | 54.40 | 28.61 | 31.09 | 61.97 | 28.52 | 38.20 |
|  | 469M | 21.50 | 49.12 | 56.88 | 31.12 | 36.74 | 64.47 | 30.53 | 41.48 |
|  | 978M | 21.93 | 50.88 | 60.24 | 32.42 | 41.06 | 67.46 | 31.77 | 43.68 |
| MoE | 182M | 20.82 | 45.03 | 57.55 | 29.84 | 31.81 | 63.28 | 28.42 | 39.53 |
|  | 469M | 23.63 | 52.40 | 53.94 | 32.43 | 43.64 | 68.34 | 31.48 | 43.69 |
|  | 978M | 23.81 | 52.90 | 58.90 | 35.01 | 44.42 | 67.90 | 31.48 | 44.91 |
| ReMoE | 182M | 20.22 | 46.68 | 54.16 | 30.26 | 35.94 | 63.55 | 29.38 | 40.03 |
|  | 469M | 21.67 | 53.16 | 58.75 | 33.80 | 40.66 | 67.95 | 31.20 | 43.88 |
|  | 978M | 24.06 | 55.26 | 57.28 | 35.93 | 44.42 | 68.99 | 30.43 | 45.20 |{{< /table-caption >}}
> 🔼 표 10은 모델의 성능이 세분화(granularity) 수준에 따라 어떻게 변하는지 보여줍니다.  다양한 크기의 모델(매개변수 수)에서 세분화 수준을 변경하면서 여러 가지 하류 작업(downstream tasks)에 대한 정확도를 측정합니다.  이 표는 ReMoE 모델이 세분화 수준이 증가함에 따라 성능이 향상되는 것을 보여주는  실험 결과를 제시합니다. 특히 기존 MoE 모델과 비교하여 ReMoE 모델의 확장성(scalability)을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Downstream results of scaling in granularity G𝐺Gitalic_G.
> </details>

{{< table-caption >}}
| Model | E | ARC-c | ARC-e | BoolQ | HellaSwag | LAMBADA | PIQA | RACE | Avg. |
|---|---|---|---|---|---|---|---|---|---| 
| Dense | - | 19.45 | 43.35 | 54.40 | 28.61 | 31.09 | 61.97 | 28.52 | 38.20 |
| MoE |  |  |  |  |  |  |  |  |  |
| 4 | 20.73 | 44.49 | 59.63 | 29.14 | 31.40 | 63.33 | 29.19 | 39.70 |
| 8 | 20.82 | 45.03 | 57.55 | 29.84 | 31.81 | 63.28 | 28.42 | 39.53 |
| 16 | 20.90 | 45.29 | 46.36 | 30.50 | 33.22 | 64.96 | 28.33 | 38.50 |
| 32 | 19.54 | 47.35 | 52.29 | 31.12 | 35.63 | 64.25 | 28.23 | 39.77 |
| 64 | 19.88 | 46.63 | 60.06 | 31.47 | 36.33 | 65.07 | 28.04 | 41.06 |
| 128 | 20.99 | 47.69 | 56.73 | 32.00 | 36.62 | 65.67 | 28.04 | 41.10 |
| ReMoE |  |  |  |  |  |  |  |  |  |
| 4 | 19.88 | 46.46 | 57.43 | 29.64 | 33.57 | 62.95 | 27.66 | 39.66 |
| 8 | 20.22 | 46.68 | 54.16 | 30.26 | 35.94 | 63.55 | 29.38 | 40.03 |
| 16 | 20.90 | 49.28 | 53.36 | 30.85 | 37.09 | 65.83 | 30.05 | 41.05 |
| 32 | 20.56 | 48.11 | 59.54 | 31.42 | 37.84 | 65.18 | 28.42 | 41.58 |
| 64 | 20.82 | 50.51 | 57.80 | 32.17 | 36.74 | 65.78 | 27.46 | 41.61 |
| 128 | 19.97 | 51.05 | 56.97 | 32.40 | 37.92 | 66.70 | 29.86 | 42.12 |{{< /table-caption >}}
> 🔼 표 11은 로드 밸런싱을 적용했을 때와 적용하지 않았을 때의 성능 비교 결과를 보여줍니다. 로드 밸런싱은 Mixture-of-Experts (MoE) 모델에서 특정 전문가에게 과도한 계산 부하가 집중되는 것을 방지하는 기법입니다.  본 표는 다양한 하위 작업(downstream tasks)에 대한 정확도를 비교하여 로드 밸런싱의 효과를 보여줍니다.  로드 밸런싱을 적용한 MoE와 ReMoE 모델이 성능 향상을 보이는지, 그리고 로드 밸런싱의 유무에 따라 성능 차이가 얼마나 나는지를 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 11: Downstream results of training with or without load balancing.
> </details>

{{< table-caption >}}
| Model | G | ARC-c | ARC-e | BoolQ | HellaSwag | LAMBADA | PIQA | RACE | Avg. |
|---|---|---|---|---|---|---|---|---|---|
| Dense | - | 19.45 | 43.35 | 54.40 | 28.61 | 31.09 | 61.97 | 28.52 | 38.20 |
| Dense × 8 | - | 22.78 | 48.11 | 59.66 | 31.11 | 35.65 | 65.02 | 29.57 | 41.70 |
| MoE 1 | 1 | 20.82 | 45.03 | 57.55 | 29.84 | 31.81 | 63.28 | 28.42 | 39.53 |
| MoE 2 | 2 | 21.42 | 46.55 | 54.25 | 29.95 | 32.52 | 64.09 | 28.61 | 39.62 |
| MoE 4 | 4 | 20.99 | 46.09 | 55.90 | 30.52 | 35.16 | 63.98 | 29.28 | 40.27 |
| MoE 8 | 8 | 21.59 | 47.73 | 60.70 | 30.83 | 36.41 | 64.69 | 28.04 | 41.42 |
| MoE 16 | 16 | 19.80 | 48.82 | 57.34 | 30.64 | 36.00 | 64.74 | 28.71 | 40.86 |
| MoE 32 | 32 | 21.67 | 48.78 | 57.85 | 31.27 | 37.10 | 64.69 | 28.52 | 41.41 |
| MoE 64 | 64 | 20.14 | 48.74 | 61.50 | 31.03 | 36.31 | 63.93 | 27.85 | 41.35 |
| ReMoE 1 | 1 | 20.22 | 46.68 | 54.16 | 30.26 | 35.94 | 63.55 | 29.38 | 40.03 |
| ReMoE 2 | 2 | 20.14 | 47.39 | 57.95 | 30.60 | 34.52 | 63.71 | 28.52 | 40.40 |
| ReMoE 4 | 4 | 20.39 | 47.94 | 55.35 | 31.04 | 36.11 | 64.64 | 29.00 | 40.64 |
| ReMoE 8 | 8 | 20.82 | 48.36 | 60.49 | 30.90 | 36.06 | 63.87 | 28.90 | 41.34 |
| ReMoE 16 | 16 | 21.25 | 49.41 | 56.06 | 30.91 | 36.23 | 64.91 | 29.95 | 41.25 |
| ReMoE 32 | 32 | 20.90 | 48.86 | 55.81 | 31.14 | 36.58 | 64.69 | 30.05 | 41.15 |
| ReMoE 64 | 64 | 20.65 | 48.74 | 60.06 | 31.56 | 36.43 | 65.40 | 29.00 | 41.69 |{{< /table-caption >}}
> 🔼 본 표는 ReMoE 모델의 5번째 레이어에서 특정 전문가(expert)에 높은 확률로 라우팅(routing)되는 토큰들을 보여줍니다. 각 전문가는 특정 도메인(예: Arxiv, Books, C4, Github, StackExchange, Wikipedia)과 관련된 단어들을 주로 처리하는 경향을 보이며, 이는 ReMoE 모델이 전문가들을 도메인별로 특화시켜 학습하는 것을 보여줍니다. 표는 전문가 ID와 함께 해당 전문가에 높은 확률로 라우팅되는 토큰들의 목록을 제시합니다. 예를 들어, 전문가 1은 'husband', 'wife', 'baby' 와 같은 단어들을 주로 처리하며, 전문가 6은 'variable', 'env', 'HEAD' 와 같은 단어들을 주로 처리합니다. 이는 ReMoE의 도메인 특화 기능을 잘 보여주는 사례입니다.
> <details>
> <summary>read the caption</summary>
> Table 12: Routed tokens with high probability for experts in Layer 5 of ReMoE
> </details>

{{< table-caption >}}
| Model | LB | ARC-c | ARC-e | BoolQ | HellaSwag | LAMBADA | PIQA | RACE | Avg. |
|---|---|---|---|---|---|---|---|---|---| 
| Dense | - | 19.45 | 43.35 | 54.40 | 28.61 | 31.09 | 61.97 | 28.52 | 38.20 |
| MoE | × | 19.20 | 44.74 | 50.80 | 28.60 | 30.18 | 62.24 | 27.94 | 37.67 |
| MoE | ✓ | 20.05 | 45.16 | **57.83** | 29.83 | 32.97 | **63.55** | 28.33 | 39.67 |
| ReMoE | × | 19.45 | 46.34 | 56.94 | 30.19 | 31.79 | 63.33 | 28.61 | 39.52 |
| ReMoE | ✓ | **20.22** | **46.68** | 54.16 | **30.26** | **35.94** | **63.55** | **29.38** | **40.03** |{{< /table-caption >}}
> 🔼 이 표는 근-조밀(near-dense) 워밍업을 사용한 MoE 모델의 성능을 보여줍니다.  'MoE with warmup' 열은 훈련 초기에 대부분의 전문가(expert)가 활성화되도록 하여 MoE 모델을 훈련시킨 결과를 나타냅니다.  이는 ReMoE의 훈련 과정에서 처음 두 단계와 유사합니다.  표에는 워밍업 기법을 적용한 MoE와 기본 MoE, ReMoE의 검증 손실(validation loss) 및 다운스트림 작업의 정확도가 포함되어 있으며, ReMoE가 다른 방법보다 우수함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 13: Performance of MoE with near-dense warmup
> </details>

{{< table-caption >}}
| Expert ID | Routed Tokens With High Probability |
|---|---| 
| 0 | `End`(100%); `folding`(100%); `Fill`(100%); `FILE`(100%); `NULL`(100%); `byte`(100%); `Release`(99.36%); `Del`(99.80%) |
| 1 | `husband`(100%); `ife`(100%); `baby`(100%); `human`(100%); `lover`(99.60%); `.`(99.86%); `),`(99.71%); `)...`(98.425%) |
| 2 | `invest`(100%); `Fortune`(100%); `exec` (100%); `0000`(100%); `Sorry`(100%); `bye`(97.82%); `If`(97.74%); `®`(97.63%) |
| 3 | `Conversely`(100%); `Methods`(100%); `flower`(100%); `Blossom`(99.93%); `Argentina`(100%); `Georgian`(100%); `Uruguay`(98.90%); `African` (100%) |
| 4 | `Spring`(100%); `Summer`(100%) `Autumn`(100%); `Winter`(100%); `seasons`(99.02%); `Temperature` (100%); `hot`(97.98%); `cold`(100%) |
| 5 | `è`(100%); `æ`(99.80%); `å`(98.59%); `Æ`(97.67%) |
| 6 | `]);`(100%); `gif`(100%); `size`(100%); `variable`(100%); `env`(100%); `begin`(97.95%); `HEAD`(97.94%); `|`(97.83%) |
| 7 | `Kuala`(100%); `Tus`(100%); `Lama`(100%); `Riley`(98.94%) |{{< /table-caption >}}
> 🔼 표 14는 다양한 전문가 수(E)에 따른 워밍업 과정을 거친 MoE 모델의 결과를 보여줍니다.  워밍업 단계에서 활성화되는 전문가 수를 조정하여 MoE 모델의 학습 과정에서 발생하는 계산 비용을 ReMoE 모델과 유사하게 맞추었습니다.  표에는 MoE 모델의 검증 손실과 정확도가 E 값에 따라 어떻게 변화하는지, 그리고 ReMoE 모델과의 성능 차이가 어떻게 나타나는지가 요약되어 있습니다.  워밍업 단계를 통해 MoE 모델의 성능이 향상되었지만, ReMoE 모델은 여전히 더 나은 성능을 보임을 알 수 있습니다. 특히, 전문가 수가 증가할수록 ReMoE의 우수성이 더욱 두드러집니다.
> <details>
> <summary>read the caption</summary>
> Table 14: Results for MoE with warmup under different expert count E𝐸Eitalic_E
> </details>

{{< table-caption >}}
| Model | Valid Loss | ARC-c | ARC-e | BoolQ | HellaSwag | LAM-BADA | PIQA | RACE | Avg. |
|---|---|---|---|---|---|---|---|---|---| 
| MoE | 1.936 | 20.82 | 45.03 | 57.55 | 29.84 | 31.81 | 63.28 | 28.42 | 39.53 |
| MoE with warmup | 1.928 | 20.73 | 46.38 | 52.35 | 30.28 | 33.90 | 63.76 | 27.66 | 39.29 |
| ReMoE | 1.921 | 20.22 | 46.68 | 54.16 | 30.26 | 35.94 | 63.55 | 29.38 | 40.03 |{{< /table-caption >}}
> 🔼 표 15는 다양한 워밍업 단계를 사용한 MoE의 최종 검증 손실을 보여줍니다.  이 표는  MoE 모델을 훈련시킬 때, 처음에 대부분의 전문가를 활성화하는 '거의 조밀한' 워밍업 단계를 추가하는 실험 결과를 나타냅니다. 이는 ReMoE의 3단계 훈련 과정과 비슷하게, 훈련 초기에 모델이 더 조밀한 상태로 시작하도록 하여 성능을 개선하는지 확인하기 위한 것입니다. 표에는 워밍업 단계의 수(0, 50, 100, 500, 1000)에 따른 MoE 모델의 최종 검증 손실이 나와 있으며, ReMoE 모델의 최종 검증 손실도 비교를 위해 함께 제시되어 있습니다. 이를 통해 워밍업 단계의 길이가 모델 성능에 미치는 영향을 분석하고, ReMoE의 훈련 전략의 효율성을 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 15: Final validation loss of MoE with different warmup steps
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