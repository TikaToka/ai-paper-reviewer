---
title: "Parallelized Autoregressive Visual Generation"
summary: "본 연구는 토큰 의존성을 고려한 병렬화 전략을 통해 자동 회귀 시각적 생성의 속도를 최대 9.5배까지 향상시켰습니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Generation", "🏢 Peking University",]
showSummary: true
date: 2024-12-19
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.15119 {{< /keyword >}}
{{< keyword icon="writer" >}} Yuqing Wang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-23 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.15119" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.15119" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/parallelized-autoregressive-visual-generation" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 자동 회귀 시각 생성 모델은 토큰을 순차적으로 생성하기 때문에 속도가 느리다는 문제점이 있습니다. 이는 특히 고해상도 이미지나 비디오 생성에서 더욱 두드러집니다.  본 논문에서는 이러한 문제를 해결하기 위해 새로운 접근 방식을 제안합니다.

본 논문에서는 **토큰 간의 의존성을 분석**하여 병렬 처리가 가능한 토큰과 순차 처리가 필요한 토큰을 구분하는 알고리즘을 제시합니다.  이를 통해 기존 모델의 구조를 변경하지 않고도 **속도를 최대 9.5배까지 향상**시키면서 **생성 품질은 유지**하거나 **최소한으로 저하**시키는 결과를 얻었습니다.  ImageNet 및 UCF-101 데이터셋을 사용한 실험 결과를 통해 제안된 방법의 효과를 검증했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 토큰 의존성 분석을 통해 병렬 처리 가능한 토큰과 순차 처리가 필요한 토큰을 구분하는 전략을 제시했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} ImageNet과 UCF-101 데이터셋에서 이미지 및 비디오 생성 작업 모두에서 속도 향상과 품질 유지를 확인했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 기존의 자동 회귀 모델에 손쉽게 통합 가능한 방식으로, 모델의 복잡성을 증가시키지 않습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
이 논문은 **자동 회귀 시각적 생성의 속도를 크게 향상시키는 동시에 품질을 유지하는** 새로운 방법을 제시하여, 실제 응용 프로그램에서 자동 회귀 모델의 실용성을 높입니다.  **병렬 처리 전략**과 **토큰 종속성**에 대한 분석은 효율적인 시각적 생성 모델링에 대한 귀중한 통찰력을 제공하며, **미래 연구에 영감을 줄** 것입니다.  특히 **다양한 토큰화 방법 및 시각 영역에 대한 호환성**은 광범위한 연구 분야에 적용 가능성을 시사합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.15119/x1.png)

> 🔼 그림 1은 서로 다른 병렬 생성 전략을 비교한 것입니다. 두 전략 모두 초기 토큰 [1, 2, 3, 4]를 순차적으로 생성한 다음, [5a-5d]에서 [6a-6d]로, [7a-7d] 순으로 단계별로 여러 토큰을 병렬로 생성합니다. (a)는 본 연구에서 제안하는 방법으로, 비국소 영역에 걸쳐 약하게 종속적인 토큰들을 병렬로 생성하여 일관된 패턴과 지역적 세부 정보를 유지합니다. (b)는 단순한 방법으로, 국소 영역 내에서 강하게 종속적인 토큰들을 동시에 생성합니다. 강하게 상관관계가 있는 토큰들을 독립적으로 샘플링하면 불일치한 생성과 패턴이 깨지는 현상(예: 왜곡된 호랑이 얼굴과 조각난 얼룩말 줄무늬)이 발생할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Comparison of different parallel generation strategies. Both strategies generate initial tokens [1,2,3,4] sequentially then generate multiple tokens in parallel per step, following the order [5a-5d] to [6a-6d] to [7a-7d], etc. (a) Our approach generates weakly dependent tokens across non-local regions in parallel, preserving coherent patterns and local details. (b) The naive method generates strongly dependent tokens within local regions simultaneously, while independent sampling for strongly correlated tokens can cause inconsistent generation and disrupted patterns, such as distorted tiger faces and fragmented zebra stripes.
> </details>





{{< table-caption >}}
| Model | Params | Layers | Hidden | Heads |
|---|---|---|---|---|
| PAR-L | 343M | 24 | 1024 | 16 |
| PAR-XL | 775M | 36 | 1280 | 20 |
| PAR-XXL | 1.4B | 48 | 1536 | 24 |
| PAR-3B | 3.1B | 24 | 3200 | 32 |{{< /table-caption >}}

> 🔼 표 1은 논문에서 제안하는 병렬화된 자기회귀 시각 생성 모델(PAR)의 크기와 아키텍처 구성을 보여줍니다.  PAR 모델은 네 가지 크기(PAR-L, PAR-XL, PAR-XXL, PAR-3B)로 구성되며, 각 크기는 파라미터 수, 레이어 수, 히든 차원, 헤드 수가 다릅니다. 이러한 구성은 이전 연구 [36, 51, 32, 47]의 설정을 따릅니다.  이는 모델의 성능과 효율성에 대한 실험적 비교 분석을 위한 기준을 설정하고, 제안된 모델의 성능을 평가하기 위한 기준 모델을 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Model sizes and architecture configurations of PAR. The configurations are following previous works [36, 51, 32, 47].
> </details>





### In-depth insights


#### Parallel Visual Gen
본 논문의 "Parallel Visual Gen" 부분은 기존의 순차적인 autoregressive 방식의 시각적 생성 모델의 속도 저하 문제를 해결하기 위한 병렬화 전략을 제시합니다. **핵심 아이디어는 토큰 간의 의존성을 분석하여 약한 의존성을 가진 토큰들은 병렬적으로 생성하고, 강한 의존성을 가진 토큰들은 순차적으로 생성하는 것입니다.** 이를 위해 **공간적으로 멀리 떨어진 토큰들끼리는 의존성이 약하다는 점을 이용**하여, 특정 지역의 초기 토큰들을 순차적으로 생성한 후, 공간적으로 멀리 떨어진 영역들의 같은 위치의 토큰들을 병렬적으로 생성하는 방식을 제안합니다. 이러한 병렬화 전략은 모델의 아키텍처나 토크나이저를 변경하지 않고도 기존 autoregressive 모델에 통합될 수 있으며, **ImageNet 및 UCF-101 데이터셋에서의 실험 결과, 속도 향상과 생성 품질 유지를 동시에 달성**하는 것을 보여줍니다.  **특히, 토큰 의존성 분석을 통해 병렬화 전략의 효율성과 안정성을 확보**하는 점이 주목할 만합니다. 이는 시각적 생성 모델의 효율성을 크게 향상시키는 동시에,  **다양한 시각적 데이터와 토크나이저에 대한 유연성을 유지**하는 데 기여할 것으로 예상됩니다.

#### Token Dependency
토큰 의존성은 자연어 처리와 컴퓨터 비전 분야 모두에서 중요한 개념입니다. 특히, **자동 회귀 모델**에서 토큰 간의 순서와 상호 의존성은 모델의 성능과 효율성에 큰 영향을 미칩니다. 이 논문에서 제시된 병렬화된 자동 회귀 시각적 생성 방법은 **토큰 간의 의존성을 분석하여 효율적인 병렬화 전략**을 제시합니다. 강한 의존성을 가진 토큰은 순차적으로 생성하고, 약한 의존성을 가진 토큰은 병렬적으로 생성하여 생성 속도를 높입니다. 이는 **시각적 토큰의 공간적 거리**와 밀접한 관련이 있습니다. 즉, 공간적으로 멀리 떨어진 토큰은 상호 의존성이 약하기 때문에 병렬적으로 처리할 수 있지만, 인접한 토큰은 강한 의존성으로 인해 순차적 생성이 필요합니다. 따라서, **공간적 거리**를 고려한 토큰 그룹화 전략이 중요하며, 초기 토큰은 전역 구조를 확립하기 위해 순차적으로 생성되어야 합니다. 이러한 접근 방식은 모델의 복잡성을 높이지 않으면서도 생성 속도를 개선하는 효율적인 방법입니다.  **토큰 의존성 분석**은 병렬화 가능성을 정확하게 판단하고, 모델의 성능 저하를 최소화하는 데 중요한 역할을 합니다.

#### Non-local Parallelism
비국소적 병렬 처리 개념은 **공간적으로 멀리 떨어진 토큰들 간의 의존성이 약하다는 점**을 이용하여 병렬 처리의 효율성을 높이는 전략입니다.  이러한 전략은 순차적인 처리 방식의 한계를 극복하고, **자동 회귀 모델의 속도를 크게 향상**시키는 데 목표를 두고 있습니다.  단순히 모든 토큰을 동시에 생성하는 것이 아니라, **토큰 간의 의존성을 분석**하여, 상호 의존성이 적은 토큰들을 병렬적으로 처리함으로써, 계산 비용을 절감하고 처리 속도를 개선하는 데 초점이 맞춰져 있습니다. 이는 단순히 처리 속도 개선뿐 아니라, **전체 이미지나 비디오의 일관성과 질적 요소**까지 고려해야 하는 어려운 과제를 해결하기 위한 **핵심적인 전략**이라고 볼 수 있습니다.  **국소적 영역 내에서의 강한 상관관계**는 여전히 순차적 처리 방식을 유지해야 함을 시사하며, **글로벌 구조의 일관성 유지를 위한 전략**과 더불어 **모델의 복잡도 증가 없이 효율적인 병렬화**를 달성하고자 하는 시도입니다.  이러한 접근 방식의 효과는 실험 결과를 통해 검증되어야 하지만,  **자동 회귀 모델의 한계를 극복**하는 데 있어 중요한 발전으로 평가될 수 있습니다.

#### Ablation Experiments
본 논문의 "Ablation Experiments" 섹션은 모델의 성능에 기여하는 각 구성 요소의 중요성을 밝히는 데 중점을 둡니다. 이를 통해 **모델 설계의 핵심적인 통찰력**을 얻을 수 있습니다.  구체적으로는, 병렬화 전략의 효과, 토큰 의존성 처리, 그리고 어텐션 메커니즘의 선택 등이 실험적으로 검증됩니다. **각 구성 요소의 제거 또는 변형을 통해 성능 변화를 측정**하여, 어떤 요소가 성능 향상에 가장 크게 기여하는지, 그리고 어떤 요소들이 서로 상호 작용하는지를 분석합니다. 이러한 분석은 모델의 강점과 약점을 파악하고, 향후 연구 방향을 제시하는 데 중요한 역할을 합니다. 특히, **병렬화 전략의 효율성과 정확성 간의 절충 관계**를 분석하고, 최적의 병렬화 수준을 결정하는 데 중요한 정보를 제공할 것으로 예상됩니다. 또한, **토큰 간의 의존성을 효과적으로 처리하는 방법**에 대한 실험적 증거를 제시함으로써, 자연어 처리 및 컴퓨터 비전 분야에 시사하는 바가 클 것입니다.

#### Future of Autoregressive
자동 회귀 모델의 미래는 **매우 밝습니다**.  이 모델들은 이미 자연어 처리와 이미지 생성 분야에서 괄목할 만한 성과를 거두었지만, 여전히 개선의 여지가 많습니다. **병렬화**는 속도를 높이는 중요한 방향이며, 이를 통해 실시간 응용 분야에서의 활용이 더욱 확대될 것입니다.  **토큰 의존성**을 효과적으로 관리하는 새로운 기법의 개발 또한 필수적입니다.  **다양한 모달리티** (텍스트, 이미지, 비디오 등)를 통합하는 통합 모델의 연구도 중요한 과제입니다.  **효율적인 토큰화 기법**은 연산량을 줄이고 모델의 확장성을 높이는 데 기여할 것입니다.  마지막으로, **모델의 설명력을 높이는 연구**는 신뢰도 향상과 안전한 응용을 위해 중요합니다. 이러한 노력들이 결합되어 더욱 강력하고 효율적인 자동 회귀 모델이 탄생할 것으로 예상됩니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.15119/x2.png)

> 🔼 그림 2는 제안된 병렬 생성 방법(PAR)과 기존의 순차적 자기회귀 생성 방법(LlamaGen [47])의 비교 결과를 보여줍니다.  PAR은 LlamaGen에 비해 3.6배에서 최대 9.5배까지 속도 향상을 달성했으며, 생성 품질은 유사하게 유지했습니다.  구체적으로, 이미지 생성 시간이 LlamaGen의 12.41초에서 PAR-4x의 경우 3.46초, PAR-16x의 경우 1.31초로 단축되었습니다. 이러한 측정은 단일 A100 GPU에서 배치 크기 1로 수행되었습니다. 그림에는 각 방법으로 생성된 이미지들의 시각적 비교 결과가 나란히 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Visualization comparison of our parallel generation and traditional autoregressive generation (LlamaGen [47]). Our approach (PAR) achieves 3.6-9.5×\times× speedup over LlamaGen with comparable quality, reducing the generation time from 12.41s to 3.46s (PAR-4×\times×) and 1.31s (PAR-16×\times×) per image. Time measurements are conducted with a batch size of 1 on a single A100 GPU.
> </details>



![](https://arxiv.org/html/2412.15119/x3.png)

> 🔼 그림 3은 제안된 비국소적 병렬 생성 과정을 보여줍니다. 먼저, 점선으로 구분된 각 영역에 대해 초기 토큰(1-4)을 순차적으로 생성하여 전역 구조를 확립합니다. 그런 다음, 서로 다른 영역에서 정렬된 위치(예: 5a-5d)에 대해 병렬 생성을 수행하고, 다음 정렬된 위치(6a-6d, 7a-7d 등)로 이동하여 병렬 생성을 계속합니다. 같은 숫자는 같은 단계에서 생성된 토큰을 나타내고, 알파벳 접미사(a,b,c,d)는 서로 다른 영역을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Illustration of our non-local parallel generation process. Stage 1: sequential generation of initial tokens (1-4) for each region (separated by dotted lines) to establish global structure. Stage 2: parallel generation at aligned positions across different regions (e.g., 5a-5d), then moving to next aligned positions (6a-6d, 7a-7d, etc.) for parallel generation. Same numbers indicate tokens generated in the same step, and letter suffix (a,b,c,d) denotes different regions .
> </details>



![](https://arxiv.org/html/2412.15119/x4.png)

> 🔼 그림 4는 본 논문에서 제안하는 병렬화된 자기회귀적 시각 생성 프레임워크를 개괄적으로 보여줍니다. (a)는 모델 구현을 보여줍니다. 모델은 처음에 토큰 [1, 2, 3, 4]를 순차적으로 생성한 다음, 학습 가능한 토큰 [M1, M2, M3]을 사용하여 병렬 예측 모드로 전환합니다. (b)는 제안된 병렬 예측 방식(왼쪽)과 기존의 단일 토큰 예측 방식(오른쪽) 간의 가시적 컨텍스트 비교를 보여줍니다. 색상이 있는 셀은 생성 중에 사용 가능한 컨텍스트를 나타냅니다. 기존의 자기회귀적 방식에서는 토큰 6d를 예측할 때, 6a~6c를 포함한 이전 토큰에 모두 접근할 수 있습니다. 하지만 전체 어텐션 없이 병렬 방식을 사용하면 각 토큰(예: 6b)이 이전 그룹의 같은 위치까지의 토큰(예: 5b까지)만 볼 수 있습니다. 따라서 본 논문에서는 그룹 단위 전체 어텐션을 사용하여 이전 그룹 전체에 접근할 수 있도록 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Overview of our parallel autoregressive generation framework. (a) Model implementation. The model first generates initial tokens sequentially [1,2,3,4], then uses learnable tokens [M1,M2,M3] to help transition into parallel prediction mode. (b) Comparison of visible context between our parallel prediction approach (left) and traditional single-token prediction (right). The colored cells indicate available context during generation. In traditional AR, when predicting token 6⁢d6𝑑6d6 italic_d, the model can access all previous tokens including 6⁢a−6⁢c6𝑎6𝑐6a-6c6 italic_a - 6 italic_c. Without full attention, our parallel approach would limit each token (e.g., 6⁢b6𝑏6b6 italic_b) to only see tokens up to the same position in the previous group (e.g., up to 5⁢b5𝑏5b5 italic_b). We enable group-wise full attention to allow access to the entire previous group.
> </details>



![](https://arxiv.org/html/2412.15119/x5.png)

> 🔼 그림 5는 세 가지 병렬 생성 전략의 비교 결과를 보여줍니다. 상단은 순차적 초기 토큰 생성 후 병렬 원거리 토큰 예측을 결합한 본 논문의 방법을 보여줍니다. 이 방법은 고품질의 일관된 이미지를 생성합니다. 중간은 순차적 초기 토큰 생성 없이 직접 병렬 예측을 수행한 결과를 보여줍니다. 이 경우, 불일치하는 전역 구조가 나타납니다. 하단은 인접 토큰의 병렬 예측 결과를 보여줍니다. 이 경우 국소적인 패턴이 왜곡되고 세부 정보가 손상됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Qualitative comparison of parallel generation strategies. Top: Our method with sequential initial tokens followed by parallel distant token prediction produces high-quality and coherent images. Middle: Direct parallel prediction without sequential initial tokens leads to inconsistent global structures. Bottom: Parallel prediction of adjacent tokens results in distorted local patterns and broken details.
> </details>



![](https://arxiv.org/html/2412.15119/x6.png)

> 🔼 그림 6은 ImageNet [9] 데이터셋의 다양한 카테고리에 대해 PAR-4x 모델을 사용하여 생성한 이미지 결과를 추가적으로 보여줍니다.  PAR-4x는 제안된 병렬화된 자기회귀 방식을 4배의 병렬 처리를 통해 수행한 모델입니다.  이 그림은 다양한 물체와 장면을 묘사하는 이미지들을 보여주어 모델의 시각적 생성 능력을 보다 자세히 보여줍니다.  이미지들의 다양성과 세부 묘사의 정확도는 모델의 성능을 시각적으로 평가하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Additional image generation results of PAR-4×\times× across different ImageNet [9] categories.
> </details>



![](https://arxiv.org/html/2412.15119/x7.png)

> 🔼 그림 7은 본 논문에서 제안하는 병렬화된 자기회귀 시각 생성 모델(PAR)의 16배속 병렬 처리(PAR-16x)를 사용하여 생성한 이미지 결과를 보여줍니다.  다양한 ImageNet [9] 카테고리에 걸쳐 생성된 이미지들의 다양성과 화질을 보여주는 추가적인 시각적 증거를 제공합니다.  이미지들은 모델의 성능과 다양한 카테고리에 대한 적응력을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Additional image generation results of PAR-16×\times× across different ImageNet [9] categories.
> </details>



![](https://arxiv.org/html/2412.15119/x8.png)

> 🔼 그림 8은 제안된 병렬 오토 회귀 비디오 생성 방법의 성능을 UCF-101 데이터셋 [44]을 사용하여 보여줍니다. 각 행은 17프레임 시퀀스에서 샘플링된 프레임들을 보여주며, 해상도는 128x128입니다. PAR-1x는 기본적인 토큰 단위 생성 방법을, PAR-4x는 4개의 토큰을 병렬로 생성하는 방법을, PAR-16x는 16개의 토큰을 병렬로 생성하는 방법을 각각 나타냅니다. 서로 다른 동작 범주에 걸쳐 생성된 비디오의 시각적 결과를 비교하여 모델의 성능을 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Video generation results on UCF-101 [44]. Each row shows sampled frames from a 17-frame sequence at 128×128 resolution, generated by PAR-1×\times×, PAR-4×\times×, and PAR-16×\times× respectively across different action categories.
> </details>



![](https://arxiv.org/html/2412.15119/x9.png)

> 🔼 그림 9는 토큰의 조건부 엔트로피 맵을 시각화한 것입니다. 각 맵은 참조 토큰(파란색 정사각형)을 조건으로 했을 때 모든 토큰의 조건부 엔트로피를 보여줍니다. 더 어두운 빨간색은 더 낮은 조건부 엔트로피를 나타내며, 따라서 참조 토큰과의 강한 의존성을 나타냅니다. 시각화는 토큰이 공간적으로 가까운 이웃과는 강한 의존성을, 먼 지역과는 약한 의존성을 보임을 보여줍니다.  즉, 가까운 토큰일수록 서로의 영향을 많이 받고, 먼 토큰일수록 서로의 영향을 적게 받는다는 것을 시각적으로 보여주는 그림입니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Visualization of token conditional entropy maps. Each map shows the conditional entropy of all tokens when conditioned on a reference token (blue square). Darker red indicates lower conditional entropy and thus stronger dependency with the reference token. The visualization shows that tokens exhibit strong dependencies with their spatial neighbors and weak dependencies with distant regions.
> </details>



![](https://arxiv.org/html/2412.15119/x10.png)

> 🔼 그림 10은 서로 다른 순서(제안된 순서와 래스터 스캔 순서)로 병렬 및 순차적 생성 간의 조건부 엔트로피 차이를 보여줍니다. (a)(d)는 제안된 순서와 래스터 스캔 순서에 대한 병렬(4개 토큰) 생성 전략과 (b)(e)는 순차적 생성 전략을 보여줍니다. 숫자는 각 순서의 생성 단계를 나타냅니다. (c)(f)는 각 순서에 대해 순차적 생성에서 병렬 생성으로 전환할 때 조건부 엔트로피 증가를 시각화합니다. 여기서 어두운 빨간색은 더 큰 엔트로피 증가와 따라서 더 높은 예측 난이도를 나타냅니다. 두 순서 모두 처음 4개의 토큰을 순차적으로 생성합니다(엔트로피 맵의 흰색 영역으로 표시). 서로 다른 공간 블록의 토큰을 병렬로 생성하는 제안된 순서는 연속적인 토큰을 동시에 생성하는 래스터 스캔 순서보다 엔트로피 증가가 더 작아 공간 블록 간의 병렬 생성이 인접 토큰을 동시에 생성하는 것보다 예측 난이도가 더 낮음을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Conditional entropy differences between parallel and sequential generation in different orders. (a)(d) show parallel (4 tokens) generation strategies and (b)(e) show sequential generation strategies for our proposed order and raster scan order respectively. Numbers indicate generation step in each order. (c)(f) visualize the conditional entropy increase when switching from sequential to parallel generation for each order, where darker red indicates larger entropy increase and thus higher prediction difficulty. Both orders generate the first four tokens sequentially (shown as white regions in entropy maps). Our proposed order that generates tokens from different spatial blocks in parallel shows smaller entropy increases compared to raster scan order that generates consecutive tokens simultaneously, indicating parallel generation across spatial blocks introduces less prediction difficulty than generating adjacent tokens simultaneously.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Type | Model | #Para. | FID↓ | IS↑ | Precision↑ | Recall↑ | Steps | Time(s)↓ |
|---|---|---|---|---|---|---|---|---|
| GAN | BigGAN [3] | 112M | 6.95 | 224.5 | 0.89 | 0.38 | 1 | - |
|  | GigaGAN [19] | 569M | 3.45 | 225.5 | 0.84 | 0.61 | 1 | - |
|  | StyleGan-XL [40] | 166M | 2.30 | 265.1 | 0.78 | 0.53 | 1 | 0.08 |
| Diffusion | ADM [10] | 554M | 10.94 | 101.0 | 0.69 | 0.63 | 250 | 44.68 |
|  | CDM [16] | - | 4.88 | 158.7 | - | - | 8100 | - |
|  | LDM-4 [38] | 400M | 3.60 | 247.7 | - | - | 250 | - |
|  | DiT-XL/2 [34] | 675M | 2.27 | 278.2 | 0.83 | 0.57 | 250 | 11.97 |
| Mask | MaskGIT [5] | 227M | 6.18 | 182.1 | 0.80 | 0.51 | 8 | 0.13 |
| VAR | VAR-d30 [49] | 2B | 1.97 | 334.7 | 0.81 | 0.61 | 10 | 0.27 |
| MAR | MAR [25] | 943M | 1.55 | 303.7 | 0.81 | 0.62 | 64 | 28.24 |
| AR | VQGAN [11] | 227M | 18.65 | 80.4 | 0.78 | 0.26 | 256 | 5.05 |
|  | VQGAN [11] | 1.4B | 15.78 | 74.3 | - | - | 256 | 5.05 |
|  | VQGAN-re [11] | 1.4B | 5.20 | 280.3 | - | - | 256 | 6.38 |
|  | ViT-VQGAN [64] | 1.7B | 4.17 | 175.1 | - | - | 1024 | >6.38 |
|  | ViT-VQGAN-re [64] | 1.7B | 3.04 | 227.4 | - | - | 1024 | >6.38 |
|  | RQTran. [23] | 3.8B | 7.55 | 134.0 | - | - | 256 | 5.58 |
|  | RQTran.-re [23] | 3.8B | 3.80 | 323.7 | - | - | 256 | 5.58 |
|  | LlamaGen-L [47] | 343M | 3.07 | 256.1 | 0.83 | 0.52 | 576 | 12.58 |
|  | LlamaGen-XL [47] | 775M | 2.62 | 244.1 | 0.80 | 0.57 | 576 | 18.66 |
|  | LlamaGen-XXL [47] | 1.4B | 2.34 | 253.9 | 0.80 | 0.59 | 576 | 24.91 |
|  | LlamaGen-3B [47] | 3.1B | 2.18 | 263.3 | 0.81 | 0.58 | 576 | 12.41 |
| AR | PAR-L-4× | 343M | 3.76 | 218.9 | 0.84 | 0.50 | 147 | 3.38 |
|  | PAR-XL-4× | 775M | 2.61 | 259.2 | 0.82 | 0.56 | 147 | 4.94 |
|  | PAR-XXL-4× | 1.4B | 2.35 | 263.2 | 0.82 | 0.57 | 147 | 6.84 |
|  | PAR-3B-4× | 3.1B | 2.29 | 255.5 | 0.82 | 0.58 | 147 | 3.46 |
|  | PAR-XXL-16× | 1.4B | 3.02 | 270.6 | 0.81 | 0.56 | 51 | 2.28 |
|  | PAR-3B-16× | 3.1B | 2.88 | 262.5 | 0.82 | 0.56 | 51 | 1.31 |{{< /table-caption >}}
> 🔼 표 2는 ImageNet 데이터셋을 사용하여 256x256 해상도의 이미지 생성 작업에 대한 다양한 모델들의 성능을 비교 분석한 표입니다.  FID(Fréchet Inception Distance), IS(Inception Score), 정밀도, 재현율, 생성에 필요한 단계 수, 그리고 생성 시간을 측정하여 모델들의 이미지 생성 품질과 효율성을 평가합니다.  '↓'는 값이 낮을수록 좋고, '↑'는 값이 높을수록 좋다는 것을 의미합니다.  -re는 rejection sampling 기법을 사용했음을 나타내고, PAR-4x와 PAR-16x는 각각 한 번에 4개와 16개의 토큰을 병렬로 생성하는 PAR 모델의 변형을 의미합니다.  즉, 본 표는 제안된 PAR 모델의 다양한 설정과 기존의 다른 이미지 생성 모델들을 비교하여 성능을 정량적으로 보여주고 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Class-conditional image generation on ImageNet 256×\times×256 benchmark. “↓↓\downarrow↓” or “↑↑\uparrow↑” indicate lower or higher values are better. “-re” means using rejection sampling. PAR-4×\times× and PAR-16×\times× means generating 4 and 16 tokens per step in parallel, respectively.
> </details>

{{< table-caption >}}
|       | FID↓ | IS↑ | steps↓ |
|-------|------|------|-------|
| w/o   | 3.67 | 221.36 | 144 |
| w     | **2.61** | 259.17 | 147 |{{< /table-caption >}}
> 🔼 표 3은 UCF-101 벤치마크에서 클래스 조건부 비디오 생성 방법을 비교한 표입니다. FVD는 비디오 생성 품질을 측정하는 지표로, 값이 낮을수록 성능이 좋음을 의미합니다. PAR-1x는 본 논문에서 제안하는 방법의 토큰 단위 순차적 생성 기준 방식이고, PAR-4x와 PAR-16x는 병렬 생성 방식으로, 생성 속도 향상 비율이 다릅니다. 이 표는 경쟁력 있는 FVD 점수를 달성하면서 생성 단계와 처리 시간을 크게 줄인 병렬 생성 방식의 효과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Comparison of class-conditional video generation methods on UCF-101 benchmark. FVD measures generation quality, where lower values (↓↓\downarrow↓) indicate better performance. PAR-1×\times× represents our token-by-token baseline, while PAR-4×\times× and PAR-16×\times× indicate our parallel generation variants with different speedup ratios, achieving competitive FVD scores with significantly reduced generation steps and wall-clock time.
> </details>

{{< table-caption >}}
| n | FID ↓ | IS ↑ | steps ↓ |
|---|---|---|---|
| 1 | **2.34** | 253.90 | 576 |
| 4 | 2.35 | 263.24 | 147 |
| 16 | 3.02 | 270.57 | 51 |{{< /table-caption >}}
> 🔼 이 표는 초기 토큰 순차 생성의 중요성을 보여줍니다.  초기 토큰들을 순차적으로 생성하는 것이 FID(Fréchet Inception Distance) 점수를 1.06만큼 향상시키는 반면, 생성 단계 수는 거의 변화가 없음을 보여줍니다. 즉, 이미지 생성의 전반적인 품질을 크게 개선하면서도 효율성을 유지할 수 있음을 시사합니다.  이는 모델이 전역 구조를 잘 파악하고 일관성 있는 이미지를 생성하는 데 초기 토큰의 순차적 생성이 중요함을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> (a) Importance of initial sequential token generation. Sequential generation of initial tokens improves FID by 1.06 with negligible step increase.
> </details>

{{< table-caption >}}
| attn | FID ↓ | IS ↑ | steps ↓ |
|---|---|---|---|
| causal | 3.64 | 228.08 | 147 |
| full | **2.61** | 259.17 | 147 |{{< /table-caption >}}
> 🔼 표 4(b)는 PAR-XXL 모델에서 병렬로 예측되는 토큰의 수(n)에 따른 성능 변화를 보여줍니다. n=1은 기존의 토큰 단위 순차적 생성 방식(baseline)을 나타냅니다. n=4로 설정하면 생성 단계가 4배 줄어들고 FID 점수는 2.35에서 2.34로 거의 변화가 없음을 보여줍니다. 반면에, n=16으로 설정하면 생성 단계는 11.3배 감소하지만 FID 점수는 0.67 증가하는 것을 확인할 수 있습니다. 이는 병렬 생성의 수준을 높일수록 생성 속도는 빨라지지만, 이미지 품질 저하 가능성이 존재함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (b) Number of parallel predicted tokens (PAR-XXL). n=1 is the token-by-token baseline. n=4 reduces steps by 4×\times× with similar FID (2.35 vs. 2.34), while n=16 reduces steps by 11.3×\times× at the cost of 0.67 FID.
> </details>

{{< table-caption >}}
| order | pattern | FID↓ | IS↑ | steps↓ |
|---|---|---|---|---|
| raster | one | 2.62 | 244.08 | 576 |
| distant | one | 2.64 | 262.72 | 576 |
| raster | multi | 5.64 | 265.46 | 147 |
| distant | multi | **2.61** | 259.17 | 147 |{{< /table-caption >}}
> 🔼 이 표는 병렬 토큰들 간의 어텐션 패턴의 영향을 보여줍니다.  '전체 어텐션(full attention)'은 이전 병렬 그룹들로부터 모든 컨텍스트에 접근할 수 있게 해주는 반면, '인과적 어텐션(causal attention)'은 제한된 접근만 허용합니다.  전체 어텐션을 사용하면 FID가 1.03만큼 향상되는 것을 보여줍니다. 이는 병렬 처리를 효율적으로 하기 위해서는 이전에 생성된 모든 토큰에 접근하는 것이 중요하다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (c) Attention pattern between parallel tokens. Full attention allows complete context access from previous parallel groups (vs. causal attention’s limited access), bringing 1.03 FID improvement.
> </details>

{{< table-caption >}}
| Params | FID↓ | IS↑ | steps |
|---|---|---|---|
| 343M | 3.76 | 218.92 | 147 |
| 775M | 2.61 | 259.17 | 147 |
| 1.4B | 2.35 | 263.24 | 147 |
| 3.1B | **2.29** | 255.46 | 147 |{{< /table-caption >}}
> 🔼 이 표는 단일 토큰 예측과 다중 토큰 예측에서 서로 다른 스캔 순서(래스터 스캔과 본 논문에서 제안하는 지역 기반 거리 순서)의 성능을 비교한 것입니다. 단일 토큰 예측에서는 두 스캔 순서 모두 유사한 성능을 보이지만(FID 2.62 대 2.64), 다중 토큰 예측에서는 지역 기반 거리 순서가 래스터 스캔 순서보다 훨씬 뛰어난 성능을 보입니다(FID 2.61 대 5.64). 이는 다중 토큰을 동시에 예측할 때 인접한 토큰 간의 강한 종속성으로 인해 래스터 스캔 순서에서 문제가 발생하지만, 지역 기반 거리 순서는 종속성이 약한 토큰들을 그룹화하여 이러한 문제를 해결하기 때문입니다.
> <details>
> <summary>read the caption</summary>
> (d) Comparison of different scan orders under single-token and multi-token prediction. Our region-based distant ordering shows similar performance with raster scan in single-token setting, but significantly outperforms in multi-token prediction (2.61 vs. 5.64 FID).
> </details>

{{< table-caption >}}
| config | value |
|---|---| 
| ***training hyper-params*** |  | 
| optimizer | AdamW [28] | 
| learning rate | 1e-4(L,XL)/2e-4(XXL,3B) | 
| weight decay | 5e-2 | 
| optimizer momentum | (0.9, 0.95) | 
| batch size | 256(L,XL)/ 512(XXL,3B) | 
| learning rate schedule | cosine decay | 
| ending learning rate | 0 | 
| total epochs | 300 | 
| warmup epochs | 15 | 
| precision | bfloat16 | 
| max grad norm | 1.0 | 
| dropout rate | 0.1 | 
| attn dropout rate | 0.1 | 
| class label dropout rate | 0.1 | 
| ***sampling hyper-params*** |  | 
| temperature | 1.0 | 
| guidance scale | 1.60 (L) / 1.50 (XL) / 1.435 (XXL) / 1.345 (3B) | {{< /table-caption >}}
> 🔼 이 표는 모델 크기가 증가함에 따라 (4배 병렬 처리) 이미지 생성 품질이 향상되는 것을 보여줍니다.  3억 4300만개의 파라미터를 가진 모델의 FID(Fréchet Inception Distance) 점수는 3.76인 반면, 31억개의 파라미터를 가진 모델의 FID 점수는 2.29로 훨씬 낮아집니다. FID 점수가 낮을수록 생성된 이미지의 품질이 실제 이미지와 더 유사함을 나타냅니다. 즉, 파라미터 수가 증가하면 생성 품질이 지속적으로 향상됨을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (e) Scaling of model size (4×\times× parallel). Generation quality steadily improves with more parameters, from 343M (FID 3.76) to 3.1B (FID 2.29).
> </details>

{{< table-caption >}}
| config | value |
|---|---| 
| ***training hyper-params*** |  | 
|---|---| 
| optimizer | AdamW [28] | 
| learning rate | 1e-4 | 
| weight decay | 5e-2 | 
| optimizer momentum | (0.9, 0.95) | 
| batch size | 256 | 
| learning rate schedule | cosine decay | 
| ending learning rate | 0 | 
| total epochs | 3000 | 
| warmup epochs | 150 | 
| precision | bfloat16 | 
| max grad norm | 1.0 | 
| dropout rate | 0.1 | 
| attn dropout rate | 0.1 | 
| class label dropout rate | 0.1 | 
| ***sampling hyper-params*** |  | 
|---|---| 
| temperature | 1.0 | 
| guidance scale | 1.15 | 
| top-k | 8000 |{{< /table-caption >}}
> 🔼 표 4는 이미지 생성 모델 설계에 대한 ablation 연구 결과를 보여줍니다.  각 ablation 연구는 모델의 성능에 미치는 영향을 평가하기 위해, 초기 순차적 토큰 생성 여부, 병렬 예측되는 토큰 수, 어텐션 패턴, 그리고 모델 크기 등의 요소들을 변화시켜 수행되었습니다.  각 실험 조건에 따른 FID(Fréchet Inception Distance), IS(Inception Score), 그리고 생성에 필요한 단계 수를 비교하여, 각 요소가 이미지 생성 품질 및 효율에 미치는 영향을 정량적으로 분석하였습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Ablation studies on image generation model designs.
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
{{< /gallery >}}