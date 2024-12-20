---
title: "Efficient Diffusion Transformer Policies with Mixture of Expert Denoisers for Multitask Learning"
summary: "MoDE: 효율적인 다중 작업 학습을 위한 전문가 혼합 잡음 제거기를 사용한 확산 트랜스포머 정책"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["AI Applications", "Robotics", "🏢 Karlsruhe Institute of Technology",]
showSummary: true
date: 2024-12-17
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.12953 {{< /keyword >}}
{{< keyword icon="writer" >}} Moritz Reuss et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-19 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.12953" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.12953" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/efficient-diffusion-transformer-policies-with" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)의 성공에 힘입어, 확산 모델 기반 정책은 모방 학습에서 인기를 얻고 있습니다. 하지만, 복잡한 작업을 처리하기 위해 모델이 커지면서 계산 비용이 크게 증가하는 문제점이 발생합니다. 이는 특히 컴퓨팅 자원이 제한적인 모바일 로봇과 같은 실제 로봇 시스템에 적용하는 데 큰 걸림돌이 됩니다.

본 논문에서는 이러한 문제를 해결하기 위해 Mixture-of-Experts (MoE) 기반의 새로운 확산 정책인 MoDE를 제안합니다. MoDE는 희소 전문가와 잡음 조건부 라우팅을 통해 매개변수를 40% 줄이고, 추론 비용을 90% 절감합니다. 또한, 잡음 조건부 자기 주의 메커니즘을 도입하여 다양한 잡음 수준에서 효과적인 잡음 제거를 가능하게 합니다. 실험 결과, MoDE는 134개의 다양한 작업에서 최첨단 성능을 달성하며, 계산 효율성도 크게 향상시켰음을 보여줍니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} MoDE는 기존의 트랜스포머 기반 확산 정책보다 우수한 성능을 보이며, 매개변수 효율적인 확장을 가능하게 합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} MoDE는 다양한 로보틱스 작업에서 최첨단 성능을 달성합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} MoDE는 잡음 조건부 자기 주의 메커니즘과 전문가 캐싱을 통해 추론 비용을 90%까지 줄입니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **매개변수 효율적인 확장** 및 **향상된 추론 속도**를 제공하는 효율적인 모E 기반 확산 정책을 제시함으로써, **대규모 모델의 계산 비용 문제**를 해결하는 데 중요한 의미를 가집니다.  또한, **다양한 로보틱스 과제에서 최첨단 성능**을 달성하여, 로보틱스 및 강화 학습 분야 연구에 **새로운 가능성**을 제시하고 있습니다.  본 논문의 발견은 **효율적인 트랜스포머 아키텍처 디자인**에 대한 통찰력을 제공하며,  향후 연구 방향에 대한 새로운 가능성을 열어줍니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.12953/x1.png)

> 🔼  그림 1은 제안된 MoDE 아키텍처를 보여줍니다. 왼쪽은 인과적 마스킹을 사용하는 트랜스포머를 보여주는데, 각 블록은 노이즈 조건부 자기 주의 메커니즘과 노이즈 수준에 따라 토큰을 전문가 모델에 할당하는 노이즈 조건부 라우터를 포함합니다. 이러한 설계는 효율적이고 확장 가능한 동작 생성을 가능하게 합니다. 오른쪽은 디노이징 중에 Swish-GLU 활성화 함수를 사용하는 간단한 MLP 전문가의 하위 집합을 라우터가 활성화하는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: The proposed MoDE architecture (left) uses a transformer with causal masking, where each block includes noise-conditional self-attention and a noise-conditioned router that assigns tokens to expert models based on the noise level. This design enables efficient, scalable action generation. On the right, the router’s activation of subsets of simple MLP experts with Swish-GLU activation during denoising is illustrated.
> </details>





{{< table-caption >}}
| Train→Test | Method | Active Params (in Million) | PrT | 1 | 2 | 3 | 4 | 5 | Avg. Len. |
|---|---|---|---|---|---|---|---|---|---|---|
| ABCD→D | Diff-P-CNN | 321 | × | 86.3% | 72.7% | 60.1% | 51.2% | 41.7% | 3.16±0.06 |
|  | Diff-P-T | 194 | × | 78.3% | 53.9% | 33.8% | 20.4% | 11.3% | 1.98±0.09 |
|  | RoboFlamingo | 1000 | ✓ | 96.4% | 89.6% | 82.4% | 74.0% | 66.0% | 4.09±0.00 |
|  | GR-1 | 130 | ✓ | 94.9% | 89.6% | 84.4% | 78.9% | 73.1% | 4.21±0.00 |
|  | **MoDE** | 277 | × | 96.6% | 90.6% | 86.6% | 80.9% | 75.5% | 4.30±0.02 |
|  | **MoDE** | 436 | ✓ | **97.1%** | **92.5%** | **87.9%** | **83.5%** | **77.9%** | **4.39±0.04** |
| ABC→D | Diff-P-CNN | 321 | × | 63.5% | 35.3% | 19.4% | 10.7% | 6.4% | 1.35±0.05 |
|  | Diff-P-T | 194 | × | 62.2% | 30.9% | 13.2% | 5.0% | 1.6% | 1.13±0.02 |
|  | RoboFlamingo | 1000 | ✓ | 82.4% | 61.9% | 46.6% | 33.1% | 23.5% | 2.47±0.00 |
|  | SuSIE | 860+ | ✓ | 87.0% | 69.0% | 49.0% | 38.0% | 26.0% | 2.69±0.00 |
|  | GR-1 | 130 | ✓ | 85.4% | 71.2% | 59.6% | 49.7% | 40.1% | 3.06±0.00 |
|  | **MoDE** | 307 | × | 91.5% | 79.2% | 67.3% | 55.8% | 45.3% | 3.39±0.03 |
|  | **MoDE** | 436 | ✓ | **96.2%** | **88.9%** | **81.1%** | **71.8%** | **63.5%** | **4.01±0.04** |{{< /table-caption >}}

> 🔼 표 1은 CALVIN 벤치마크의 두 가지 과제(ABCD→D 및 ABC→D)에 대한 다양한 모델의 성능을 비교한 표입니다.  1000개의 명령어 체인을 기준으로, 각 명령어 체인 내 개별 작업의 평균 성공률과 5개의 연속적인 명령어를 완료하는 데 걸리는 평균 롤아웃 길이(Avg. Len.)를 보여줍니다. 표준 편차가 0인 경우는 평균 성능이 보고되지 않은 모델을 나타냅니다.  'Prt'는 정책 사전 훈련이 필요한 모델을 나타내며, 매개변수 수는 언어 인코더를 제외합니다.  즉, 이 표는 다양한 모델들이 CALVIN 벤치마크의 여러 과제들을 얼마나 잘 수행하는지, 그리고 그 과정에서 얼마나 많은 계산이 필요한지를 보여주는 비교 분석 결과를 담고 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1:  Performance comparison on the two CALVIN challenges. The table reports average success rates for individual tasks within instruction chains and the average rollout length (Avg. Len.) to complete 5 consecutive instructions, based on 1000 chains. Zero standard deviation indicates methods without reported average performance. 'Prt' denotes models requiring policy pretraining. Parameter counts exclude language encoders.
> </details>





### In-depth insights


#### MoE Diffusion Policies
MoE(Mixture of Experts) 확산 정책은 **매개변수 효율적인 확장성**과 **다중 작업 학습 능력**을 결합하여 기존의 확산 기반 정책의 한계를 극복하는 혁신적인 방법입니다.  **희소 전문가**와 **잡음 조건화 라우팅**을 통해 활성 매개변수를 줄이고 추론 비용을 절감하면서도, **잡음 조건화 자기 주의 메커니즘**을 통해 다양한 잡음 수준에서 효과적인 잡음 제거가 가능합니다. 이는 특히 **대규모 모델**에서 효율성을 높이는 데 중요하며, 제한된 연산 자원을 가진 로봇 시스템에 적용하기에 적합합니다.  **다양한 로봇 작업 데이터**를 사전 학습하여 일반화 성능을 향상시키고, 다양한 벤치마크에서 최첨단 성능을 달성합니다.  MoE 확산 정책의 핵심은 **잡음 수준에 따른 전문가의 동적 할당**이며, 이를 통해 각 잡음 수준에 최적화된 전문가를 활용함으로써 효율성과 성능을 동시에 향상시킵니다.  향후 연구는 **더욱 정교한 라우팅 전략**과 **다양한 전문가 아키텍처**를 탐색하여 MoE 확산 정책의 성능과 확장성을 더욱 개선하는 데 초점을 맞출 수 있습니다.

#### Noise-Conditioned Routing
본 논문에서 제안하는 **잡음 조건부 라우팅(Noise-Conditioned Routing)**은 핵심적으로 **잡음 수준에 따라 토큰을 전문가 네트워크(expert network)에 분배하는 메커니즘**입니다. 기존의 MoE(Mixture-of-Experts) 방식과 달리, 입력 데이터의 내용뿐 아니라 **잡음의 강도**라는 추가적인 정보를 활용하여 라우팅을 수행합니다. 이는 잡음 제거 과정의 각 단계에서 필요한 전문가를 효율적으로 선택하고, **매 단계별로 특화된 전문가를 활용**할 수 있게 합니다.  **잡음 수준에 따른 전문가 활성화 패턴의 시각화**를 통해, 각 전문가가 잡음 수준에 따라 특정 영역에 집중하여 잡음 제거를 수행한다는 것을 보여줍니다.  이는 **모델의 파라미터 효율성**을 높이고 **추론 속도를 향상**시키는 데 중요한 역할을 합니다. 특히, **잡음 수준별로 전문가를 미리 계산하여 캐싱**하는 전략을 통해, 추론 단계에서의 계산 비용을 획기적으로 줄일 수 있습니다. 이러한 **효율적인 라우팅 메커니즘**은 대규모 멀티태스크 학습 환경에서도 효과적으로 모델을 확장하고, 높은 성능을 유지하는 데 기여합니다.

#### Efficient Inference
본 논문은 효율적인 추론(Efficient Inference)을 위해 **Mixture-of-Denoising Experts (MoDE)**라는 새로운 정책을 제안합니다. 기존의 Transformer 기반 확산 정책보다 매개변수를 40% 줄이고 추론 비용을 90% 절감하는 매개변수 효율적인 확장을 가능하게 합니다. 이는 **희소 전문가와 노이즈 조건부 라우팅**을 통해 달성됩니다.  MoDE는 노이즈 조건부 자기 주의 메커니즘을 사용하여 다양한 노이즈 수준에서 효과적인 잡음 제거를 가능하게 합니다. 또한, **노이즈 수준에 따른 전문가 캐싱**을 통해 추론 속도를 향상시킵니다.  이러한 효율성 향상은 다양한 로봇 작업에서 우수한 성능을 보여주는 실험 결과로 뒷받침됩니다.  결론적으로, MoDE는 계산 자원이 제한적인 환경에서도 복잡한 작업을 수행할 수 있는 **매개변수 효율적인 확산 정책**을 제공합니다.

#### Multitask Learning
본 논문에서 다루는 핵심 개념 중 하나인 "다중 작업 학습(Multitask Learning)"은 **단일 모델이 다양한 작업을 동시에 학습하고 수행**하는 것을 의미합니다.  이는 **모델의 효율성 및 일반화 성능 향상**에 크게 기여할 수 있습니다.  특히, 이 논문에서는 확산 모델(Diffusion Model) 기반의 정책(Policy)을 사용하여 다양한 로봇 제어 작업을 수행하는 데 있어 다중 작업 학습의 중요성을 강조합니다.  **각 작업마다 별도의 모델을 학습하는 대신, 하나의 모델로 여러 작업을 처리함으로써 파라미터 효율성을 높이고, 작업 간의 지식 전이를 통해 성능을 향상**시킬 수 있다는 점을 보여줍니다. 또한, **소수의 전문가 네트워크를 활용한 희소 다중 전문가(Sparse Mixture-of-Experts) 구조**를 통해 모델의 크기를 줄이고 연산 비용을 절감하면서도 성능을 유지할 수 있음을 실험적으로 증명합니다.  이러한 다중 작업 학습 방식은 **로봇 제어 분야의 다양한 과제를 해결**하는데 효과적인 전략이 될 수 있으며, **자원 효율적인 인공지능 모델 개발**에 중요한 시사점을 제공합니다.  결론적으로, 다중 작업 학습은 **모델의 효율성, 일반화 성능, 그리고 실제 로봇 시스템에의 적용 가능성**을 모두 높이는 핵심적인 전략으로 제시됩니다.

#### Ablation Studies
본 논문의 ‘절제 연구(Ablation Studies)’ 부분은 **MoDE 모델의 설계 선택이 성능에 미치는 영향을 면밀히 조사**합니다.  **잡음 주입, MoE 전략, 잠재 차원, 라우팅 전략** 등 다양한 요소를 체계적으로 제거하거나 변경하여 그 효과를 측정합니다. 이를 통해 핵심 구성 요소의 중요성을 파악하고 모델의 강점과 약점을 명확히 드러냅니다. 특히, **잡음 조건부 자기 주의 메커니즘과 잡음 입력 토큰의 중요성**을 강조하며, **효율적인 추론을 위한 잡음 조건부 라우팅 메커니즘의 효과**를 입증합니다.  또한, 최적의 전략을 찾기 위한 다양한 라우팅 기법의 비교 분석을 통해 **MoDE의 효율성과 확장성을 뒷받침**하는 증거를 제시합니다.  **전반적으로, 절제 연구는 MoDE 모델의 설계를 정교화하고, 성능 향상 및 효율적인 모델 구축에 대한 귀중한 통찰력을 제공**합니다.  이는 단순히 성능 수치를 넘어, 모델의 작동 원리를 심층적으로 이해하고, 향후 유사한 모델 개발에 대한 지침을 제공하는 데 중요한 역할을 합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.12953/x2.png)

> 🔼 본 그림은 MoDE 모델의 추론 과정에서 효율성을 높이는 전략을 보여줍니다. MoDE 학습 후, 노이즈 수준에 따라 전문가 네트워크(expert subnetworks)를 미리 선택하여 활성화하는 노이즈 조건부 라우터(noise-conditioned router)를 사용합니다.  이를 통해 추론 시 라우터를 제거하고 선택된 전문가 네트워크만 사용하므로, 계산 비용을 크게 줄이고 네트워크 효율성을 높일 수 있습니다.  각 노이즈 레벨에 대한 전문가 네트워크의 선택은 미리 계산되어 저장되므로 추론 속도 또한 향상됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: After training MoDE, the router is noise-conditioned, allowing pre-computation of the experts used at each noise level before inference. This enables removing the router and retaining only the selected experts, significantly improving network efficiency.
> </details>



![](https://arxiv.org/html/2412.12953/x3.png)

> 🔼 그림 (a)는 LIBERO-90 벤치마크에 포함된 다양한 작업 환경과 과제의 예시들을 보여줍니다. LIBERO-90 벤치마크는 다양한 로봇 제어 과제를 평가하기 위해 고안되었으며, 그림에서는 다양한 물체 조작, 움직임, 그리고 상호 작용을 필요로 하는 여러 과제들을 보여줍니다. 이러한 과제들은 로봇의 다양한 능력을 평가하는 데 사용되며, 각 과제는 특정한 목표와 상황을 가지고 있습니다. 그림은 이러한 다양한 과제들의 시각적인 예시를 제공하여, LIBERO-90 벤치마크의 복잡성과 다양성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (a) LIBERO-90 Tasks
> </details>



![](https://arxiv.org/html/2412.12953/x4.png)

> 🔼 그림 (b)는 LIBERO-10 과 LIBERO-90 벤치마크에 대한 실험 결과를 보여줍니다. LIBERO-10 은 다양한 설정에서 10가지의 장기간 과제에 대한 모델의 성능을 평가하고, LIBERO-90 은 90가지의 다양한 단기간 과제에 대한 모델의 성능을 평가합니다. 이 그림은 각 과제에 대해 평균 성공률을 보여주며,  MoDE가 다른 기준 모델들에 비해 우수한 성능을 보임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) Results for LIBERO-10 and LIBERO-90
> </details>



![](https://arxiv.org/html/2412.12953/x5.png)

> 🔼 그림 3은 LIBERO 환경에 대한 시각화와 결과를 보여줍니다. (a)는 LIBERO-90 작업 세트의 몇 가지 예시 환경과 작업을 보여주는 이미지입니다. (b)는 세 개의 시드에 대해 각 작업에 대해 20회씩 반복하여 평균낸 두 가지 LIBERO 과제에 대한 평균 결과를 나타내는 막대 그래프입니다. 이 그래프는 다양한 정책(알고리즘)들의 성공률을 비교하여 MoDE의 성능 우수성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Visualization and Results for LIBERO environment. (a) Few example environments and tasks of the LIBERO-90 task suite. (b) Average results for both LIBERO challenges averaged over 3333 seeds with 20202020 rollouts for each task.
> </details>



![](https://arxiv.org/html/2412.12953/x6.png)

> 🔼 그림 (a)는 CALVIN 환경의 개요를 보여줍니다. CALVIN 환경은 슬라이드, 서랍, 질감이 다른 네 가지 설정(A, B, C, D)으로 구성됩니다. 각 설정은 다양한 작업을 수행하는 데 사용할 수 있는 상호 작용 요소의 다른 구성을 가지고 있습니다.
> <details>
> <summary>read the caption</summary>
> (a) Environments
> </details>



![](https://arxiv.org/html/2412.12953/x8.png)

> 🔼 그림 (b)는 CALVIN 환경에서의 에이전트 동작 예시를 보여줍니다. 그림에는 5개의 연속적인 작업이 포함되어 있으며, 각 작업이 완료될 때마다 에이전트에게 다음 작업이 주어집니다. 이는 에이전트가 장기간에 걸쳐 여러 작업을 연속적으로 수행할 수 있는 능력을 보여주는 좋은 예시입니다.  에이전트가 각 작업을 성공적으로 완료하면 점수를 얻습니다. 이 그림은 CALVIN 벤치마크의 복잡성과 에이전트가 다양한 작업들을 연속적으로 수행해야 하는 어려움을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) Example CALVIN-Rollout
> </details>



![](https://arxiv.org/html/2412.12953/x9.png)

> 🔼 그림 4는 CALVIN 환경에 대한 개요를 보여줍니다. (a)는 슬라이드, 서랍, 질감이 다른 네 가지 설정(A, B, C, D)을 보여줍니다. (b)는 순차적으로 수행되는 5개의 작업으로 구성된 예시 시퀀스를 보여줍니다. 이전 작업을 완료해야만 다음 작업 목표가 정책에 제공됩니다.  원 논문의 캡션은 다소 간략하므로, 그림의 이해를 돕기 위해 추가적인 설명을 덧붙였습니다. 그림 (b)는 연속적인 작업 수행을 보여주는 시퀀스를 보여줍니다. 각 작업이 성공적으로 완료되어야만, 다음 작업이 제공됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Overview of the CALVIN environment. (a) CALVIN contains four different settings (A,B,C,D) with different configurations of slides, drawers and textures. (b) Example rollout consisting of 5555 tasks in sequence. The next goal is only given to the policy, if it manages to complete the prior.
> </details>



![](https://arxiv.org/html/2412.12953/x10.png)

> 🔼 그림 5는 동일한 매개변수 수를 가진 MoDE와 밀집 변환기 모델 간의 계산 효율성 비교를 보여줍니다. 왼쪽 그래프는 다양한 배치 크기에 대해 100회의 순전파에 대한 평균 추론 속도를 보여줍니다. 오른쪽 그래프는 밀집 기준 모델에 비해 라우터 캐싱을 사용한 MoDE와 사용하지 않은 MoDE의 FLOP 수를 비교합니다. MoDE는 라우터 캐싱과 희소 전문가 설계 덕분에 더 낮은 FLOP 수와 더 빠른 추론 속도를 통해 우수한 효율성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Computational efficiency comparison between MoDE and a Dense-Transformer model with the same number of parameters. Left: Average inference speed over 100 forward passes for various batch sizes. Right: FLOP count for MoDE with router cache and without compared against a dense baseline. MoDE demonstrates superior efficiency with lower FLOP count and faster inference thanks to its router caching and sparse expert design.
> </details>



![](https://arxiv.org/html/2412.12953/x11.png)

> 🔼 그림 6은 MoDE 모델의 모든 계층에 걸쳐 각 전문가의 평균 사용량을 시각적으로 보여줍니다. 보라색은 사용량이 적음을, 노란색은 사용량이 많음을 나타내며, 각 이미지는 개별적으로 정규화됩니다. 평균 활성화는 MoDE가 서로 다른 노이즈 수준에 대해 서로 다른 전문가를 활용하도록 학습함을 보여줍니다. 즉, 각 전문가는 특정 노이즈 수준에서 특정 작업을 수행하도록 전문화되어 있으며, 노이즈 수준에 따라 적절한 전문가를 선택적으로 활용하여 효율적인 추론을 가능하게 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Visualized Expert Utilization. The average usage of all experts in MoDE across all layers is shown. Purple color corresponds to low usage and yellow color to high one, and each image is separately normalized. The average activation shows that MoDE learns to utilize different experts for different noise levels.
> </details>



![](https://arxiv.org/html/2412.12953/x12.png)

> 🔼 그림 7은 SIMPLER Li et al. (2024b) 벤치마크의 예시 장면들을 보여줍니다. 이 벤치마크는 Bridge와 Google Fractal 데이터셋의 다양한 작업에 대해 일반적인 정책을 테스트하기 위해 사용됩니다. 그림은 다양한 물체 조작 작업을 수행하는 로봇의 이미지를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Example Scenes of the SIMPLER Li et al. (2024b) benchmark used to test generalist policies on various tasks from the Bridge and Google Fractal dataset.
> </details>



![](https://arxiv.org/html/2412.12953/x13.png)

> 🔼 그림 8은 CALVIN ABC 및 ABCD 환경에서 MoDE와 Dense-MoDE의 성능 확장을 보여줍니다. 각 환경에 대해 가장 성능이 좋은 변형을 사용하여 2, 4, 6, 8개의 전문가에 대한 평균 성능을 보여줍니다. 이 그림은 모델이 더 많은 전문가를 사용할 때 성능이 어떻게 변하는지 보여주는 것입니다.  특히, 전문가의 수가 증가함에 따라 성능이 어떻게 향상되거나 저하되는지, 그리고 각 환경에서 최적의 전문가 수는 무엇인지에 대한 통찰력을 제공합니다.  ABCD 환경은 ABC 환경보다 더 복잡한 작업을 포함하므로, 두 환경 모두에서 MoDE의 성능을 비교하여 일반화 능력과 복잡한 작업에 대한 모델의 적응력을 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Scaling performance of MoDE and Dense-MoDE on CALVIN ABC and ABCD environments, showing average performance for 2222 to 8888 experts using best-performing variants for each environment.
> </details>



![](https://arxiv.org/html/2412.12953/x14.png)

> 🔼 그림 (a)는 LIBERO-90 벤치마크의 일부 환경과 작업을 보여줍니다. LIBERO-90 벤치마크는 다양한 로봇 작업을 평가하기 위해 고안되었으며, 각 작업에는 고유한 환경 설정과 목표가 있습니다. 그림은 다양한 물체, 도구, 그리고 작업 공간의 모습을 보여줍니다. 이러한 다양한 시나리오는 다양한 로봇 기술과 전략을 요구하며, 모델의 일반화 능력과 적응력을 평가하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> (a)
> </details>



![](https://arxiv.org/html/2412.12953/x15.png)

> 🔼 그림 (b)는 LIBERO-10 및 LIBERO-90 벤치마크에서 다양한 모델의 평균 성공률을 보여줍니다. LIBERO-90 벤치마크는 90개의 다양한 단기 과제를, LIBERO-10 벤치마크는 10개의 장기 과제를 평가합니다. MoDE는 두 벤치마크 모두에서 가장 높은 평균 성공률을 달성합니다. 특히, LIBERO-10 벤치마크에서는 90%가 넘는 성공률을 기록하며, 기존의 최고 성능을 능가합니다. 이는 MoDE가 장기간의 과제 수행에도 효과적임을 보여줍니다. 또한, MoDE는 계산 효율성도 뛰어나, 기존 모델보다 적은 계산 비용으로 우수한 성능을 달성합니다.
> <details>
> <summary>read the caption</summary>
> (b)
> </details>



![](https://arxiv.org/html/2412.12953/x16.png)

> 🔼 그림 (c)는 다양한 부하 균형 손실 가중치(γLB ∈ [0.1, 0.01, 0.001, 0.0001])를 사용하여 LIBERO-10에서 훈련된 MoDE의 전문가 활용을 시각화한 것입니다. 각 이미지는 특정 잡음 수준에 걸쳐 모든 레이어에서 전문가의 평균 사용률을 보여줍니다. 보라색은 낮은 사용률을, 노란색은 높은 사용률을 나타냅니다. 각 이미지는 개별적으로 정규화됩니다. 이 시각화는 부하 균형 가중치가 잡음 수준에 따른 전문가 특수화의 균형에 미치는 영향을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (c)
> </details>



![](https://arxiv.org/html/2412.12953/x17.png)

> 🔼 이 그림은 MoDE 모델의 각 계층에서 다양한 노이즈 수준에 걸쳐 모든 전문가의 평균 사용량을 보여줍니다. 보라색은 낮은 사용량을, 노란색은 높은 사용량을 나타내며 각 이미지는 별도로 정규화됩니다. 평균 활성화는 MoDE가 다른 노이즈 수준에 대해 서로 다른 전문가를 사용하도록 학습한다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (d)
> </details>



![](https://arxiv.org/html/2412.12953/x18.png)

> 🔼 이 그림은 모든 잡음 제거 단계에서 다양한 부하 균형 가중치에 따른 평균 전문가 활용도를 보여줍니다.  각 그래프는 잡음 제거 단계(x축)에 따른 각 전문가(y축)의 활성화 비율을 보여줍니다.  다양한 가중치 값(0.1, 0.01, 0.001, 0.0001)에 따른 전문가 활용 패턴의 변화를 통해 부하 균형 가중치가 모델의 학습 능력과 전문가 특화에 미치는 영향을 시각적으로 보여줍니다.  색상은 활성화 비율을 나타내며, 진한 색일수록 활성화 비율이 높음을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Average Expert Utilization for different Load Balancing Weights across all denoising levels.
> </details>



![](https://arxiv.org/html/2412.12953/x19.png)

> 🔼 그림 (a)는 LIBERO-90 벤치마크의 일부 환경과 작업을 보여줍니다. LIBERO-90 벤치마크는 다양한 단기 목표 작업을 수행하는 로봇 정책을 평가하기 위해 고안되었습니다. 이 그림은 로봇이 성공적으로 완료해야 하는 다양한 작업을 보여줍니다. 각 작업에는 고유한 환경 설정과 목표가 있습니다. 이러한 이미지들은 정책이 얼마나 다양하고 복잡한 작업을 처리할 수 있는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (a)
> </details>



![](https://arxiv.org/html/2412.12953/x20.png)

> 🔼 그림 (b)는 LIBERO 환경에 대한 평균 성공률을 보여줍니다. LIBERO-10 과 LIBERO-90 챌린지 모두에 걸쳐 세 가지 시드에 대해 각 과제당 20회 시도를 평균한 결과입니다. MoDE는 두 가지 챌린지 모두에서 최고의 성능을 보였으며, 특히 장기간의 행동 생성을 요구하는 LIBERO-10 챌린지에서 그 차이가 더욱 두드러졌습니다.
> <details>
> <summary>read the caption</summary>
> (b)
> </details>



![](https://arxiv.org/html/2412.12953/x21.png)

> 🔼 그림 (c)는 다양한 로드 밸런싱 가중치(γLB ∈ [0.1, 0.01, 0.0001, 0.0001])를 사용하여 훈련된 MoDE 모델에서 각 전문가의 평균 사용량을 보여줍니다. 각 행은 레이어를 나타내고, 각 열은 전문가를 나타냅니다. 색상 그라디언트는 각 레이어 내에서 각 전문가에게 할당된 토큰의 비율을 나타냅니다. 이 그림은 각 전문가가 노이즈 레벨에 따라 어떻게 특화되는지, 그리고 로드 밸런싱 손실이 전문가 사용 분포에 미치는 영향을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (c)
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | Avg. Success. |
|---|---| 
| **MoDE** | **0.92** |
| - Input Noise Token | 0.90 |
| - Noise-cond Attention | 0.85 |
| FiLM Noise Conditioning | 0.81 |
| **TopK=1** | **0.91** |
| Shared Expert | 0.90 |
| <div>γ=0.1</div>  | 0.90 |
| <div>γ=0.001</div> | 0.86 |
| **256 Embed Dim** | **0.86** |
| **512 Embed Dim** | **0.87** |{{< /table-caption >}}
> 🔼 표 2는 LIBERO-10 벤치마크에서 MoDE의 다양한 설계 선택에 따른 성능 변화를 보여줍니다. 각 실험은 3개의 시드와 각 시드당 20회의 실행으로 평균을 내어 얻은 결과입니다. 표에는 노이즈 주입 방법, 전문가 수, 토큰 분포 전략 등 다양한 요소들을 변경하여 실험한 결과가 제시되어 있습니다. 이를 통해 각 요소가 MoDE의 전체 성능에 미치는 영향을 분석하고, 최적의 설계를 도출하기 위한 실험적 근거를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Ablation Studies for MoDE on LIBERO-10. All results are averaged over 3333 seeds with 20202020 rollouts each.
> </details>

{{< table-caption >}}
| Hyperparameter | CALVIN ABCD | CALVIN ABC | LIBERO-10 | LIBERO-90 | Pret-MoDE |
|---|---|---|---|---|---| 
| Number of Transformer Layers | 8 | 8 | 8 | 8 | 12 |
| Number Experts | 4 | 4 | 4 | 4 | 4 |
| Attention Heads | 8 | 8 | 8 | 8 | 8 |
| Action Chunk Size | 10 | 10 | 10 | 10 | 10 |
| History Length | 1 | 1 | 1 | 1 | 1 |
| Embedding Dimension | 1024 | 1024 | 1024 | 1024 | 1024 |
| Image Encoder | FiLM-ResNet18 | FiLM-ResNet50 | FiLM-ResNet18 | FiLM-ResNet18 | FiLM-ResNet50 |
| Goal Lang Encoder | CLIP ViT-B/32 | CLIP ViT-B/32 | CLIP ViT-B/32 | CLIP ViT-B/32 | CLIP ViT-B/32 |
| Attention Dropout | 0.3 | 0.3 | 0.3 | 0.3 | 0.3 |
| Residual Dropout | 0.1 | 0.1 | 0.1 | 0.1 | 0.1 |
| MLP Dropout | 0.1 | 0.1 | 0.1 | 0.1 | 0.1 |
| Optimizer | AdamW | AdamW | AdamW | AdamW | AdamW |
| Betas | [0.9, 0.95] | [0.9, 0.95] | [0.9, 0.95] | [0.9, 0.95] | [0.9, 0.95] |
| Learning Rate | 1e-4 | 1e-4 | 1e-4 | 1e-4 | 1e-4 |
| Transformer Weight Decay | 0.05 | 0.05 | 0.05 | 0.05 | 0.1 |
| Other weight decay | 0.05 | 0.05 | 0.05 | 0.05 | 0.1 |
| Batch Size | 512 | 512 | 512 | 512 | 512 |
| Train Steps in Thousands | 30 | 25 | 15 | 30 | 300 |
| σ<sub>max</sub> | 80 | 80 | 80 | 80 | 80 |
| σ<sub>min</sub> | 0.001 | 0.001 | 0.001 | 0.001 | 0.001 |
| σ<sub>t</sub> | 0.5 | 0.5 | 0.5 | 0.5 | 0.5 |
| EMA | True | True | True | True | True |
| Time steps | Exponential | Exponential | Exponential | Exponential | Exponential |
| Sampler | DDIM | DDIM | DDIM | DDIM | DDIM |
| Parameter Count (Millions) | 460 | 460 | 460 | 460 | 685 |{{< /table-caption >}}
> 🔼 이 표는 논문의 실험에서 사용된 MoDE 정책의 모든 하이퍼파라미터에 대한 요약을 보여줍니다.  Transformer 레이어의 수, 전문가 수, 어텐션 헤드 수, 액션 청크 크기, 히스토리 길이, 임베딩 차원, 이미지 인코더, 목표 언어 인코더, 드롭아웃 비율, 옵티마이저, 베타, 학습률, 가중치 감쇠, 배치 크기, 학습 단계, 시그마, EMA(지수 이동 평균) 및 샘플러와 같은 하이퍼파라미터가 포함되어 있습니다. 이러한 하이퍼파라미터는 MoDE 모델의 성능과 효율성에 영향을 미치는 중요한 요소입니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Summary of all the Hyperparameters for the MoDE policy used in our experiments.
> </details>

{{< table-caption >}}
| Dataset | Weight |
|---|---| 
| BC-Z | 0.258768 |
| LIBERO-10 | 0.043649 |
| BRIDGE | 0.188043 |
| CMU Play-Fusion | 0.101486 |
| Google Fractal | 0.162878 |
| DOBB-E | 0.245176 |
| **Total** | **1.000000** |{{< /table-caption >}}
> 🔼 이 표는 논문의 방법론 섹션(Method)에 있는 표 4입니다.  MoDE 모델을 학습시키는 데 사용된 데이터셋의 구성 비율을 보여줍니다. 총 196,000개의 트레이젝토리가 사용되었으며, 각 데이터셋 (BC-Z, LIBERO-10, BRIDGE, CMU Play-Fusion, Google Fractal, DOBB-E) 에 대한 가중치(Weight)를 나타냅니다.  각 데이터셋의 가중치는 해당 데이터셋이 MoDE 모델 학습에 기여하는 정도를 반영합니다.  즉, 가중치가 높을수록 해당 데이터셋의 트레이젝토리가 모델 학습에 더 많이 사용되었음을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Dataset sampling weights used for training MoDE on a small subset of trajectories. The total dataset consists of 196k trajectories.
> </details>

{{< table-caption >}}
| Benchmark | MoDE | DP-T | DP-CNN | Avg. Baseline | Improvement |
|---|---|---|---|---|---| 
| CALVIN ABC→D (norm.) | **0.678** | 0.226 | 0.270 | 0.248 | +151.1% |
| CALVIN ABCD→D (norm.) | **0.860** | 0.396 | 0.632 | 0.514 | +36.1% |
| LIBERO-90 | **0.910** | 0.690 | 0.780 | 0.735 | +16.7% |
| LIBERO-10 | **0.920** | 0.510 | 0.730 | 0.620 | +26.0% |
| Average Improvement Over Second-Best: |  |  |  |  | **57.5%** |{{< /table-caption >}}
> 🔼 표 5는 MoDE의 성능 향상 분석 결과를 보여줍니다. CALVIN 벤치마크의 점수는 LIBERO 벤치마크와 비교하기 위해 5로 나누어 정규화되었습니다. 성능 향상은 (MoDE - 평균 기준) / 평균 기준 × 100으로 계산됩니다. 최종 평균은 네 개의 벤치마크에서 두 번째로 좋은 확산 정책 변형과 비교하여 모든 벤치마크에 걸친 평균 성능 향상을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Detailed Performance Improvement Analysis. CALVIN scores are normalized by dividing by 5 to align with LIBERO scale. Improvement calculated as: (MoDE - Avg. Baseline) / Avg. Baseline × 100. Final average is the mean of improvements across all four benchmarks compared to the second best Diffusion Policy variant on each one.
> </details>

{{< table-caption >}}
| Metric | OpenVLA Score | OpenVLA Rank | Octo Base Score | Octo Base Rank | MoDe (ours) Score | MoDe (ours) Rank |
|---|---|---|---|---|---|---|
| Drawer Open | **16%** | **1** | 0% | 3 | 4.23% | 2 |
| Drawer Close | 20% | 2 | 2% | 3 | **34.92%** | **1** |
| Pick Can Horizontal | **71%** | **1** | 0% | 3 | 33.78% | 2 |
| Pick Can Vertical | 27% | 2 | 0% | 3 | **29.78%** | **1** |
| Pick Can Standing | **65%** | **1** | 0% | 3 | 36.44% | 2 |
| Move Near | **48%** | **1** | 3% | 3 | 30% | 2 |
| Drawer Open | 19% | 2 | 1% | 3 | **21.30%** | **1** |
| Drawer Close | 52% | 2 | 44% | 3 | **76.85%** | **1** |
| Pick Can Horizontal | **27%** | **1** | 21% | 3 | 22% | 2 |
| Pick Can Vertical | 3% | 3 | 21% | 2 | **40%** | **1** |
| Pick Can Standing | 19% | 2 | 9% | 3 | **35%** | **1** |
| Move Near | **46%** | **1** | 4% | 3 | 45.42% | 2 |
| Partial Put Spoon on Tablecloth | 4% | 3 | **35%** | **1** | 29.17% | 2 |
| Put Spoon on Tablecloth | 0% | 3 | 12% | **1** | **12.5%** | **1** |
| Partial Put Carrot on Plate | 33% | 2 | **53%** | **1** | 29.17% | 3 |
| Put Carrot on Plate | 0% | 3 | 8% | **1** | **8.33%** | 1 |
| Partial Stack Green Block on Yellow Block | 12% | 2 | **32%** | **1** | 8.33% | 3 |
| Stack Green Block on Yellow Block | 0% | 2 | 0% | 2 | 0% | 2 |
| Partial Put Eggplant in Basket | 8% | 3 | **67%** | **1** | 37.5% | 2 |
| Put Eggplant in Basket | 4% | 3 | **43%** | **1** | 8.33% | 2 |
| Average | 23.70% | 1.95 | 17.75% | 2.1 | **26.30%** | **1.65** |{{< /table-caption >}}
> 🔼 표 6은 SIMPLER 벤치마크의 모든 작업에 대해 2952개의 평가를 사용하여 최첨단 일반 정책인 OpenVLA(Kim et al., 2024)와 Octo(Octo Model Team et al., 2023)와 비교하여 MoDE의 성능을 자세히 비교한 것입니다.  이 표는 각 작업에 대한 성공률과 순위를 보여줍니다.  MoDE는 평균 성공률과 순위 모두에서 다른 두 가지 정책보다 우수한 성능을 보여주는 것을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Detailed comparison of MoDE against two sota Generalist Policies OpenVLA Kim et al. (2024) and Octo Octo Model Team et al. (2023) tested on all SIMPLER tasks with 2952 evals.
> </details>

{{< table-caption >}}
| Model | Block Push | Relay Kitchen | CAL ABC | CAL ABCD | L-10 | Average |
|---|---|---|---|---|---|---|
| Dense T | 0.96 ± 0.02 | 3.73 ± 0.12 | **2.83 ± 0.19** | 4.13 ± 0.11 | 0.91 ± 0.02 | 0.839 ± 0.144 |
| Token-Router | 0.97 ± 0.01 | **3.85 ± 0.03** | 2.67 ± 0.04 | 4.29 ± 0.08 | 0.90 ± 0.01 | 0.845 ± 0.161 |
| σ<sub>t</sub>-Router | *0.97 ± 0.01* | 3.79 ± 0.04 | *2.79 ± 0.16* | **4.30 ± 0.02** | **0.92 ± 0.02** | **0.851 ± 0.151** |{{< /table-caption >}}
> 🔼 표 7은 논문에서 제시된 MoDE 모델의 다섯 가지 벤치마크에 대한 세 가지 다른 토큰 라우팅 전략(Token-Router, στ-Router, Dense-T)의 성능을 보여줍니다. 각 벤치마크(Block Push, Relay Kitchen, CAL ABC, CAL ABCD, L-10)에 대해 최고 성능은 굵은 글씨체로, 두 번째로 좋은 성능은 기울임꼴로 표시되어 있습니다. CALVIN 벤치마크의 경우 CAL로 축약하여 표시했습니다. 전체 평균 성능은 모든 점수를 정규화하고 모든 환경에 걸쳐 평균을 계산하여 도출되었습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Overview of the performance of all different token routing strategies used for MoDE across 5555 benchmarks. We mark the best result for each environment in bold and the second best in cursive. We use CAL to represent CALVIN. To average the results, we normalize all scores and compute the average over all environments.
> </details>

{{< table-caption >}}
| Method | Active Params (M) | Total Params (M) | GFLOPS | PrT | Avg. Length | SF-Ratio | Inf. Time [ms] |
|---|---|---|---|---|---|---|---| 
| Diff-P-CNN | 321 | 321 | 1.28 | × | 1.35 | 1.05 | **11.7** |
| Diff-P-T | 194 | 194 | 2.16 | × | 1.13 | 0.53 | 16.2 |
| RoboFlamingo | 1000 | 1000 | 690 | ✓ | 2.47 | 0.004 | 65 |
| SuSIE | 860+ | 860+ | 60 | ✓ | 2.69 | 0.045 | 199 |
| GR-1 | **130** | **130** | 27.5 | ✓ | 3.06 | 0.11 | 12.6 |
| **MoDE (ours)** | 436 | 740 | 1.53 | ✓ | **4.01** | **2.6** | 12.2 |{{< /table-caption >}}
> 🔼 표 8은 CALVIN 벤치마크에 사용된 다양한 방법들의 총 매개변수와 활성 매개변수를 비교한 표입니다.  여기에는 각 방법이 필요로 하는 평균 FLOPS(단정밀도 부동소수점 연산), ABC 벤치마크에서의 평균 성능, 그리고 평균 롤아웃 길이와 GFLOPS를 비교한 SF 비율에 대한 추가적인 개요가 포함되어 있습니다. 즉, 모델의 크기, 계산 효율성, 그리고 성능을 종합적으로 비교 분석한 표입니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Comparison of total and active number of parameters of methods used in the CALVIN benchmark. Additional overview of average FLOPS required by the different methods together with their average performance on the ABC benchmark. SF-Ratio compares average rollout length with GFLOPS.
> </details>

{{< table-caption >}}
|                     | Block Push | Relay Kitchen |
| :------------------ | :---------: | :------------: |
| **C-BeT**           | 0.87 ± (0.07) | 3.09 ± (0.12)  |
| **VQ-BeT**          | 0.87 ± (0.02) | 3.78 ± (0.04)  |
| **BESO**            | 0.96 ± (0.02) | 3.73 ± (0.05)  |
| **MoDE**            | **0.97 ± (0.01)** | **3.79 ± (0.02)** |{{< /table-caption >}}
> 🔼 표 9는 상태 기반 목표 조건형 릴레이 키친 및 블록 푸시 환경에서 다양한 정책의 성능을 비교한 것입니다. 4개의 시드에 걸쳐 평균을 낸 결과, MoDE는 밀집 변압기 변형체인 BESO 및 기타 정책 표현보다 성능이 뛰어납니다. 이 표는 다양한 정책(MoDE, BESO, C-BeT, VQ-BeT)의 릴레이 키친 및 블록 푸시 작업에 대한 평균 성공률을 보여줍니다. 각 정책은 상태와 목표를 입력으로 받아 행동을 예측합니다. MoDE는 다른 정책보다 높은 성공률을 달성하여 상태 기반 작업에서의 우수한 성능을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Comparison of the performance of different policies on the state-based goal-conditioned relay-kitchen and block-push environment averaged over 4444 seeds. MoDE outperforms the dense transformer variant BESO and other policy representations on all baselines.
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