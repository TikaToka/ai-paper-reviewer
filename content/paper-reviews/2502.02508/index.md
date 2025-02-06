---
title: "Satori: Reinforcement Learning with Chain-of-Action-Thought Enhances LLM Reasoning via Autoregressive Search"
summary: "Satori: 체인-오브-액션-토크(COAT) 추론과 강화 학습을 활용해 단일 LLM의 추론 능력을 획기적으로 향상시킨 연구!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 MIT",]
showSummary: true
date: 2025-02-04
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.02508 {{< /keyword >}}
{{< keyword icon="writer" >}} Maohao Shen et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-05 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.02508" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.02508" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/satori-reinforcement-learning-with-chain-of" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

LLM(대규모 언어 모델)은 다양한 영역에서 뛰어난 추론 능력을 보여주지만, 복잡한 문제 해결에는 여전히 어려움을 겪습니다. 기존 연구는 외부 검증자를 활용한 두 플레이어 시스템을 통해 이 문제를 해결하려 했지만, 효율성 및 단일 LLM의 자체적 문제 해결 능력 향상이라는 과제가 남아 있습니다.

본 논문에서는 이러한 문제를 해결하기 위해 **자기 반성과 자기 탐색 기능을 통합한 새로운 COAT(Chain-of-Action-Thought) 추론 방식**을 제안하고, 70억 매개변수의 Satori 모델을 개발했습니다.  **강화 학습 기반의 2단계 학습 과정**을 통해 Satori는 다양한 수학적 추론 과제에서 최첨단 성능을 달성했으며, 도메인 간 일반화 성능 또한 뛰어났습니다.  이는 단일 LLM이 복잡한 추론 과제를 효율적으로 처리할 수 있음을 보여줍니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 자기 반성 및 자기 탐색 기능을 갖춘 자동 회귀 검색 방식인 Chain-of-Action-Thought(COAT) 추론 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 소규모 형식 조정 및 대규모 자기 개선의 2단계 학습 방식으로 Satori 모델 개발 및 우수한 성능 검증 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 수학적 추론뿐 아니라 다양한 영역에서 우수한 일반화 성능을 보이며 최첨단 성능 달성 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **단일 LLM의 추론 능력을 향상시키는 새로운 방법**을 제시하여, 기존의 두 플레이어 시스템의 한계를 극복하고 효율성을 높였습니다.  **자기 반성 및 탐색 기능을 갖춘 자동 회귀 검색 방식**을 통해 수학적 추론 뿐 아니라 다양한 영역에서 성능 향상을 달성했습니다.  이러한 연구는 **오픈 소스 모델을 활용한 실험 결과**를 공개하여 재현성을 높이고, 향후 연구 방향을 제시하여 **LLM 추론 기술 발전**에 크게 기여할 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.02508/x1.png)

> 🔼 본 그림은 Satori의 훈련 프레임워크에 대한 개념도입니다. Satori는 두 단계의 훈련 과정을 거칩니다. 첫 번째 단계는 형식 조정(FT) 단계로, 소규모의 시범 경로 데이터를 사용하여 모방 학습을 통해 COAT 추론 형식을 학습하는 단계입니다. 두 번째 단계는 자기 개선 단계로, 대규모 강화 학습을 통해 COAT 추론 형식을 활용하여 자체적으로 성능을 향상시키는 단계입니다. 이를 통해 Satori는 복잡한 추론 문제를 해결하는 능력을 획득하게 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: A High-level Overview of Satori Training Framework: Format Tuning (FT) + Self-improvement. First, Satori learns COAT reasoning format through imitation learning on small-scale demonstration trajectories. Next, Satori further leverages COAT reasoning format to self-improve via large-scale reinforcement learning.
> </details>





{{< table-caption >}}
| Scale | Model | GSM8K | MATH500 | OlympiadBench | AMC2023 | AIME2024 | Avg. |
|---|---|---|---|---|---|---|---| 
| Large | GPT-4o | / | 60.3 | 43.3 | / | 9.3 | / |
|  | o1-preview | / | 85.5 | / | 82.5 | 44.6 | / |
|  | Llama-3.1-70B-Instruct | 94.1 | 68.0 | 29.4 | 42.5 | 13.3 | 49.5 |
|  | OpenMath2-Llama3.1-70B | 94.1 | 71.8 | 30.1 | 45.0 | 13.3 | 50.9 |
|  | QwQ-32B-Preview | 95.5 | 90.6 | 61.2 | 77.5 | 50.0 | 75.0 |
| Small | Llama-3.1-8b-Instruct | 84.4 | 51.9 | 15.1 | 22.5 | 3.3 | 35.4 |
|  | OpenMath2-Llama3.1-8B | 90.5 | 67.8 | 28.9 | 37.5 | 6.7 | 46.3 |
|  | NuminaMath-7B-CoT | 78.9 | 54.6 | 15.9 | 20.0 | 10.0 | 35.9 |
|  | Qwen-2.5-7B-Instruct | 91.6 | 75.5 | 35.5 | 52.5 | 6.7 | 52.4 |
|  | Qwen-2.5-Math-7B-Instruct | 95.2 | 83.6 | 41.6 | 62.5 | 16.7 | 59.9 |
|  | **Satori-Qwen-7B** | **93.2** | **85.6** | **46.6** | **67.5** | **20.0** | **62.6** |
|  | **Satori-Qwen-7B (Round 2)** | **93.9** | **83.6** | **48.5** | **72.5** | **23.3** | **64.4** |{{< /table-caption >}}

> 🔼 표 1은 수학 벤치마크에 대한 Satori-Qwen-7B의 결과를 보여줍니다. Satori-Qwen-7B는 다섯 가지 벤치마크에서 최첨단 성능을 달성했으며, 동일한 기반 모델인 Qwen-2.5-Math-7B를 사용하는 Qwen-2.5-Math-7B-Instruct보다 성능이 뛰어납니다. 2차 훈련 후 Satori-Qwen-7B (2차)는 어려운 과제에서 더욱 향상된 성능을 보여줍니다. 이 표는 모델의 성능을 다양한 수학적 추론 벤치마크에서 비교 분석하여 Satori-Qwen-7B 모델의 우수성을 보여줍니다. 특히, 동일한 기반 모델을 사용하는 다른 모델과 비교하여 Satori-Qwen-7B의 성능 향상을 명확하게 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Results on Mathematic Benchmarks. Satori-Qwen-7B achieves SOTA performance across five benchmarks, and outperforms Qwen-2.5-Math-7B-Instruct which uses the same base model Qwen-2.5-Math-7B. After round-2 training, Satori-Qwen-7B (Round 2) demonstrates even stronger performance on hard tasks.
> </details>





### In-depth insights


#### LLM Reasoning
LLM 추론에 대한 심층적인 논의는 **대규모 언어 모델(LLM)이 복잡한 추론 과제를 해결하는 능력**에 초점을 맞춥니다.  본 연구는 LLM의 추론 능력 향상을 위한 다양한 기법을 제시하며, 특히 **사전 훈련된 모델을 활용한 자기 반복적 학습(self-improvement)의 효과**에 주목합니다.  **체인-오브-액션-토크(COAT) 메커니즘**을 통해 모델은 다양한 메타 행동을 수행하며, **강화 학습(Reinforcement Learning)**을 통해 효율적인 문제 해결 전략을 학습합니다. 또한, 이 연구는 단일 LLM 내에서 **자기 반성 및 탐색 기능**을 내재화하는 방식을 제안하여, 기존의 외부 검증자(verifier)가 필요한 이중 시스템에 비해 **효율성을 높이고 확장성을 확보**합니다.  **수학적 추론뿐 아니라 다양한 영역으로의 일반화 가능성**을 보여주는 실험 결과는 LLM 추론 연구의 중요한 진전을 보여줍니다.  **오픈소스 기반의 접근 방식**은 연구의 투명성과 재현성을 높이는 데 기여합니다.

#### COAT Mechanism
본 논문에서 제시된 COAT(Chain-of-Action-Thought) 메커니즘은 **LLM의 추론 능력 향상**을 위한 핵심 구성 요소입니다. 기존의 CoT(Chain-of-Thought) 방식이 단순히 추론 단계를 나열하는 데 그쳤다면, COAT는 **메타-액션 토큰**을 도입하여 LLM이 추론 과정에서 **자기 반성 및 탐색**을 수행하도록 합니다.  **<|continue|>, <|reflect|>, <|explore|>** 와 같은 메타-액션 토큰은 LLM이 추론 과정을 주도적으로 제어하고, 실수를 수정하거나 대안적인 해결책을 모색할 수 있게 합니다.  이는 단순히 외부 지도에 의존하는 기존의 두 플레이어 시스템과 달리, **LLM 스스로 복잡한 문제 해결 과정을 내재화**할 수 있게 하는 혁신적인 접근 방식입니다.  **강화 학습**을 통해 LLM이 메타-액션 토큰 사용을 학습하고, 자기 개선을 통해 더욱 효과적인 추론 과정을 만들어낼 수 있습니다. 결과적으로 COAT는 **단일 LLM의 자율적이고 효율적인 추론 능력 향상**에 크게 기여합니다.

#### Two-Stage Training
본 논문에서 제안하는 **두 단계 학습 방식**은 LLMs의 추론 능력 향상에 있어 중요한 역할을 합니다. 첫 번째 단계인 **형식 조정(Format Tuning)** 단계에서는 소규모의 데모 데이터를 사용하여 모델이 COAT 추론 형식을 이해하도록 합니다. 이는 메타-액션 토큰을 사용하여 모델이 문제 해결 과정에서 자기 반성 및 탐색을 수행하도록 유도하는 데 필수적입니다.  두 번째 단계인 **자기 개선(Self-improvement)** 단계에서는 강화 학습을 통해 모델이 자체적으로 추론 능력을 향상시키도록 합니다.  **Restart and Explore (RAE) 전략**을 활용하여 모델이 중간 단계에서 다시 시작하고 대안을 탐색하도록 함으로써, 긴 시간적 지평선과 드문 보상 문제를 해결합니다.  **두 단계 학습 방식**을 통해 개발된 Satori 모델은 수학적 추론 벤치마크에서 최첨단 성능을 달성하고, 도메인 간 일반화에도 강점을 보입니다.  **형식 조정과 자기 개선의 조합**은 Satori의 효율성과 효과성을 보여주는 핵심 요소입니다.

#### Autoregressive Search
자연어 모델이 추론 능력을 향상시키는 데 있어서 **자기반복적 탐색(autoregressive search)**은 매우 중요한 개념입니다. 이는 모델이 스스로 추론 과정을 반복하고 수정하며, 더 나은 해결책을 찾아나가는 과정을 의미합니다. 기존의 방법들은 외부 평가자나 보상 모델에 의존하여 추론 과정을 제어했지만, 자기반복적 탐색은 모델 내부적으로 이러한 기능을 구현함으로써 효율성을 높이고, 단일 모델로 복잡한 문제를 해결할 수 있도록 합니다.  **체인-오브-액션-토트(COAT)** 와 같은 메커니즘을 통해 모델은 다양한 메타 행동(meta-action)을 수행하며, 스스로 반성하고 새로운 전략을 탐색할 수 있습니다. 강화학습(reinforcement learning)과 결합하여 모델이 자체적으로 성능을 향상시키는 **자기 개선(self-improvement)** 과정을 거치게 되면, **도메인 일반화(generalization)** 능력 또한 향상시킬 수 있습니다.  하지만, **긴 시퀀스와 희소한 보상(sparse rewards)** 문제와 같은 과제들을 해결하기 위한 추가적인 연구가 필요합니다. 특히, 자기반복적 탐색의 효과를 극대화하기 위해서는 메타 행동의 종류, 강화학습 알고리즘의 선택, 훈련 데이터의 구성 등을 신중하게 고려해야 합니다.

#### Future of LLMs
LLM의 미래는 **더욱 향상된 추론 능력과 일반화 능력**을 중심으로 전개될 것입니다.  본 논문에서 제시된 Satori 모델처럼 **자기 반성 및 자기 탐색 능력을 갖춘 단일 LLM**이 복잡한 문제 해결에 효과적인 접근 방식임을 보여줍니다. 향후 연구는 **더욱 다양한 메타-액션과 정교한 강화학습 알고리즘**을 통해 이러한 능력을 더욱 발전시키고, **일반적인 영역으로 확장**하는 데 집중할 것입니다.  **오픈소스 모델 및 데이터를 활용한 투명하고 재현 가능한 연구**는 LLM 발전에 중요한 역할을 할 것입니다. 또한, **효율적인 훈련 기법과 테스트 시간 확장 전략**의 발전은 LLM의 실용성을 높이는 데 기여할 것입니다.  **대규모 언어 모델의 윤리적 및 사회적 영향**에 대한 심도있는 고찰 또한 미래의 중요한 과제입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.02508/x2.png)

> 🔼 그림 2는 Satori-Qwen-7B와 Qwen-2.5-Math-7B-Instruct 모델의 학습 데이터 크기를 비교한 그래프입니다. Satori-Qwen-7B는 기존의 지도 학습 방식(Supervised Fine-tuning, SFT) 대신, 강화 학습(Reinforcement Learning, RL)을 통해 자기 개선을 중점적으로 학습하였습니다.  따라서 SFT 단계에서는 소규모(small-scale) 데이터만 사용했고, RL 단계에서는 대규모(large-scale) 데이터를 사용했습니다. 이 그래프는 Satori-Qwen-7B가 Qwen-2.5-Math-7B-Instruct보다 훨씬 적은 양의 지도 학습 데이터만으로도 우수한 성능을 달성했음을 보여줍니다.  이는 Satori-Qwen-7B의 자기 개선 학습 전략이 효과적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Number of Training Samples of Satori-Qwen-7B and Qwen-2.5-Math-7B-Instruct. Satori-Qwen-7B requires significantly less supervision (small-scale FT) and relies more on self-improvement (large-scale RL).
> </details>



![](https://arxiv.org/html/2502.02508/x3.png)

> 🔼 그림 3은 강화 학습 훈련 시간에 따른 정책 훈련 정확도와 응답 길이를 보여줍니다. 이 그래프는 Satori 모델이 강화 학습을 통해 더 긴 추론 과정을 거치면서 추론 성능을 향상시킨다는 것을 보여줍니다.  RL 훈련 단계가 진행될수록 정책 정확도가 증가하고 응답 길이도 증가하는 것을 알 수 있습니다. 이는 Satori가 더 복잡한 문제를 해결하기 위해 더 많은 시간을 할애하고 더욱 심도있는 추론을 수행함을 의미합니다. 초기 단계에서 응답 길이가 감소하는 현상은 초기 단계에서 Satori가 자기 반성 능력을 충분히 습득하지 못했기 때문으로 보입니다. 후반 단계로 진행되면서 응답 길이가 다시 증가하는 것은 Satori가 자기 반성을 통해 오류를 수정하고 더 나은 해결책을 찾는 능력이 향상되었기 때문입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Policy Training Acc. & Response length v.s. RL Train-time Compute. Through RL training, Satori learns to improve its reasoning performance through longer thinking.
> </details>



![](https://arxiv.org/html/2502.02508/x4.png)

> 🔼 그림 4는 모델의 테스트 시간 성능을 문제의 난이도에 따라 보여줍니다. 위쪽 그래프는 테스트 시간에 사용된 토큰 수(응답 길이)를, 아래쪽 그래프는 정확도를 나타냅니다.  문제의 난이도가 높아짐에 따라 Satori-Qwen 모델은 Satori-Qwen-FT 모델(format tuning만 거친 모델)보다 더 많은 계산 자원(테스트 시간)을 사용하지만, 더 높은 정확도를 달성합니다.  즉, 어려운 문제일수록 더 많은 계산을 통해 더 정확한 답을 찾는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Above: Test-time Response Length v.s. Problem Difficulty Level; Below: Test-time Accuracy v.s. Problem Difficulty Level. Compared to FT model (Satori-Qwen-FT), Satori-Qwen uses more test-time compute to tackle more challenging problems.
> </details>



![](https://arxiv.org/html/2502.02508/x5.png)

> 🔼 본 그림은 강력한 모델(Satori-Qwen-7B)에서 약한 기본 모델(Llama-8B 및 Granite-8B)로 증류하는 것이 약한 기본 모델에 직접 형식 조정을 적용하는 것보다 더 효과적임을 보여줍니다.  즉, 이미 잘 학습된 강력한 모델의 지식을 상대적으로 성능이 낮은 모델에 전이하여 성능 향상을 도모하는 전이 학습 방식이, 기본 모델의 학습만으로는 얻을 수 없는 성능 향상을 제공한다는 것을 시각적으로 보여줍니다.  그림은 두 가지 방법의 평균 정확도를 비교하여 이러한 차이를 명확하게 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Format Tuning v.s. Distillation. Distilling from a Stronger model (Satori-Qwen-7B) to weaker base models (Llama-8B and Granite-8B) are more effective than directly applying format tuning on weaker base models.
> </details>



![](https://arxiv.org/html/2502.02508/x6.png)

> 🔼 그림 6은 수학 문제 풀이 과정을 보여주는 예시입니다. Satori 모델은 중간 단계의 계산 과정이 정확한지 검증하고, 다음 단계로 넘어가기 전에 각 단계의 정확성을 확인합니다. 이를 통해 모델이 단순히 답을 예측하는 것이 아니라, 문제 해결 과정 자체를 이해하고 논리적으로 추론하며 단계별로 정확하게 풀이해 나가는 것을 보여줍니다.  문제는 '주어진 두 원의 교점을 지나는 직선의 기울기를 구하라'는 내용이며, Satori 모델은 단계별로 계산 과정을 제시하고, 각 단계마다 정확성을 검증하면서 최종 답을 도출합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Math Domain Example. Satori verifies the correctness of the intermediate steps and proceeds to the next reasoning step.
> </details>



![](https://arxiv.org/html/2502.02508/x7.png)

> 🔼 그림 7은 수학 문제 풀이 과정을 보여주는 예시입니다. Satori 모델은 이전 풀이 과정에서 발견된 오류를 파악하고, 대안적인 정답을 제시합니다. 이는 Satori 모델이 단순히 답을 맞추는 것이 아니라, 문제 해결 과정에 대한 이해와 자기 반성 능력을 가지고 있음을 보여줍니다. 그림에서는 잘못된 계산 과정과 그에 대한 수정 과정, 그리고 최종적인 정답 도출 과정이 상세히 나와 있습니다. 이를 통해 Satori 모델의 추론 능력과 오류 수정 능력을 효과적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Math Domain Example. Satori identifies the mistakes in the previous solution and proposes an alternative correct solution.
> </details>



![](https://arxiv.org/html/2502.02508/x8.png)

> 🔼 그림 8은 Satori 모델이 수학 문제 풀이 과정에서 이전 해결책의 정확성을 검증하고 다른 해결책을 제시하는 과정을 보여줍니다.  Satori는 중간 단계의 정확성을 확인하고, 잘못된 부분을 발견하면 다른 접근 방식을 사용하여 문제를 다시 풉니다. 이는 Satori가 단순히 답을 생성하는 것이 아니라, 문제 해결 과정 자체를 이해하고 반복적으로 개선하는 능력을 가지고 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Math Domain Example. Satori verifies the correctness of previous solution and initiates a different solution.
> </details>



![](https://arxiv.org/html/2502.02508/x9.png)

> 🔼 그림 9는 수학 문제 풀이 과정을 보여주는 예시입니다.  Satori 모델은 이전 풀이 과정의 정확성을 검증한 후 더 간결하고 효율적인 해결 방법을 탐색하는 과정을 보여줍니다.  기존 풀이 방법의 오류를 파악하고, 더 간단한 대안을 제시하여 문제 해결의 효율성을 높이는 Satori 모델의 능력을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Math Domain Example. Satori verifies the correctness of previous solution and further explores a simpler solution.
> </details>



![](https://arxiv.org/html/2502.02508/x10.png)

> 🔼  그림 10은 수학 문제 풀이 과정을 보여주는 예시입니다. 1) Satori는 초기 단계에서 중간 과정의 정확성을 검증합니다. 2) Satori는 이전 해결책이 잘못되었다는 것을 인식하고 대안적인 해결책을 제시합니다. 이 그림은 Satori 모델이 문제 풀이 과정에서 자기 반성 및 수정 능력을 갖추고 있음을 보여줍니다.  Satori가 중간 단계를 확인하고 수정하는 과정을 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Math Domain Example. 1) Satori verifies the correctness of intermediate steps in early stage. 2) Satori realizes that the pervious solution is actually erroneous and then proposes an alternative correct solution.
> </details>



![](https://arxiv.org/html/2502.02508/x11.png)

> 🔼 그림 11은 Satori 모델이 비수학적 추론 문제를 풀이하는 과정을 보여줍니다. 1) Satori는 중간 단계에서 잠재적인 실수를 파악하고 다른 해결책을 제시합니다. 2) 이전 해결책이 여전히 잘못되었음을 깨닫고 대안적인 정답을 제시합니다.  이를 통해 Satori가 자기 반성을 통해 문제 해결 능력을 향상시키는 과정을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Out-of-domain Example. 1) Satori identifies the potential mistakes in intermediate steps and initiates another solution. 2) Satori realizes that the pervious solution is still erroneous and then proposes an alternative correct solution.
> </details>



![](https://arxiv.org/html/2502.02508/x12.png)

> 🔼 그림 12는 본 논문에서 제시된 Satori 모델이 비수학 영역 문제를 해결하는 과정을 보여줍니다.  Satori는 중간 단계에서 발생할 수 있는 오류를 파악하고, 이를 바탕으로 보다 정확한 솔루션을 제시하는 과정을 보여주는 예시입니다.  단순히 최종 답만 제시하는 것이 아니라, 문제 풀이 과정의 각 단계를 검토하고 수정하는 Satori의 자기 반성 및 탐색 능력을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Out-of-domain Example. Satori identifies the potential mistakes in intermediate steps and initiates another correct solution.
> </details>



![](https://arxiv.org/html/2502.02508/x13.png)

> 🔼 그림 13은 Satori 모델이 비수학적 추론 문제를 해결하는 과정을 보여줍니다. 1단계에서는 Satori가 중간 단계의 정확성을 검증하고, 2단계에서는 잘못된 답변을 인지하고 대안적인 해결책을 제시합니다. 이는 Satori 모델의 자기 반성 및 문제 해결 능력을 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: Out-of-domain Example. 1) Satori verifies the correctness of intermediate steps in early stage. 2) Satori realizes that the pervious solution is actually erroneous and then proposes an alternative correct solution.
> </details>



![](https://arxiv.org/html/2502.02508/x14.png)

> 🔼 그림 14는 본 논문에서 제시된 Satori 모델이 비수학적 추론 문제를 해결하는 과정을 보여줍니다.  Satori는 중간 추론 단계에서 여러 번 자기 반성 과정을 거치는 모습을 보여주며, 이는 문제 해결을 위한 전략적 사고 과정을 시각적으로 보여주는 것입니다.  단순히 답을 제시하는 것이 아니라, 추론 과정의 각 단계에서 스스로의 추론을 검토하고 수정하며 나아가는 Satori의 특징을 잘 나타내고 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: Out-of-domain Example. Satori engages in multiple self-reflection processes during intermediate reasoning steps.
> </details>



![](https://arxiv.org/html/2502.02508/x15.png)

> 🔼 그림 15는 Satori 모델이 비수학적 추론 문제를 푸는 과정을 보여줍니다. 1) Satori는 초기 단계에서 중간 단계의 정확성을 검증합니다. 2) Satori는 이전 해결책이 잘못되었다는 것을 깨닫고 대안적인 정확한 해결책을 제시합니다. 이는 Satori가 복잡한 추론 과정에서 자기 반성과 수정 능력을 갖추고 있음을 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 15: Out-of-domain Example. 1) Satori verifies the correctness of intermediate steps in early stage. 2) Satori realizes that the pervious solution is actually erroneous and then proposes an alternative correct solution.
> </details>



![](https://arxiv.org/html/2502.02508/x16.png)

> 🔼 그림 16은 Satori 모델이 비수학 영역 문제를 푸는 과정을 보여줍니다. Satori는 처음 제시된 답변의 오류를 파악하고, 이를 수정하는 과정을 거쳐 올바른 답을 제시합니다. 이는 Satori 모델이 단순히 주어진 문제를 풀어내는 것이 아니라, 문제 해결 과정에 대한 이해를 바탕으로 자체적인 추론과 수정 능력을 갖추고 있음을 시사합니다.  이 그림은 본 논문의 핵심 주장인 Satori 모델의 강력한 추론 능력과 일반화 능력을 잘 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 16: Out-of-domain Example. Satori identifies the mistakes in previous solution and proposes an alternative correct solution.
> </details>



![](https://arxiv.org/html/2502.02508/x17.png)

> 🔼 그림 17은 합성 데이터셋을 생성하는 과정을 보여줍니다. 먼저, 생성기 모델에서 여러 개의 초기 추론 경로를 샘플링하고 비평가 모델에 보내 피드백을 요청합니다. 비평가 모델은 잘못된 최종 답변을 가진 경로의 실수를 식별하고 대안적인 해결책을 제시합니다. 정답을 가진 경로의 경우에는 비평가 모델이 정답 여부를 확인합니다. 피드백을 바탕으로 생성기는 이전 경로를 자체적으로 개선하고 잘못된 경로는 최대 m번 반복하여 추가적인 피드백을 위해 다시 비평가 모델에 보냅니다. 각 단계에서 성공적으로 개선된 경로는 보존되고 최종적으로 보상 모델이 고품질의 데모 경로를 평가하고 수집하여 합성 데이터셋 𝒟<sub>syn</sub>을 형성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 17: Demonstration Trajectories Synthesis. First, multiple initial reasoning trajectories are sampled from the generator and sent to critic to ask for feedback. The critic model identifies the mistake for trajectories with incorrect final answers and proposes an alternative solution. For trajectories with correct final answers, the critic model provides verification of its correctness. Based on the feedback, the generator self-refines its previous trajectories, and the incorrect trajectories are sent to the critic again for additional feedback with maximum m𝑚mitalic_m iterations. At each step, those trajectories with successful refinements are preserved and finally, a reward model rates and collects high-quality demonstration trajectories to form the synthetic dataset 𝒟synsubscript𝒟syn\mathcal{D}_{\text{syn}}caligraphic_D start_POSTSUBSCRIPT syn end_POSTSUBSCRIPT.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Scale | Model | FOLIO | BGQA | CRUXEval | StrategyQA | TableBench | STEM | Avg. | 
|---|---|---|---|---|---|---|---|---| 
| Large | Llama-3.1-70B-Instruct | 65.0 | 58.3 | 59.6 | 88.8 | 34.2 | 61.7 | 61.3 | 
|  | OpenMath2-Llama3.1-70B | 68.5 | 68.7 | 35.1 | 95.6 | 46.8 | 15.1 | 55.0 | 
|  | QwQ-32B-Preview | 84.2 | 71.1 | 65.2 | 88.2 | 51.5 | 71.3 | 71.9 | 
| Small | Llama-3.1-8b-Instruct | 63.5 | 50.3 | 38.5 | 92.2 | 32.4 | 43.4 | 53.4 | 
|  | OpenMath2-Llama3.1-8B | 57.1 | 49.0 | 11.1 | 84.4 | 34.2 | 10.9 | 41.1 | 
|  | NuminaMath-7B-CoT | 53.2 | 44.6 | 28.0 | 77.8 | 29.1 | 11.3 | 40.7 | 
|  | Qwen-2.5-7B-Instruct | 72.4 | 53.0 | 58.1 | 91.3 | 43.2 | 57.1 | 62.5 | 
|  | Qwen-2.5-Math-7B-Instruct | 68.9 | 51.3 | 28.0 | 85.3 | 36.2 | 45.2 | 52.5 | 
|  | **Satori-Qwen-7B** | 71.4 | 61.8 | 42.5 | 86.3 | 43.4 | 56.7 | 60.4 | 
|  | **Satori-Qwen-7B (Round 2)** | 72.9 | 58.5 | 41.1 | 90.4 | 44.6 | 57.4 | 60.8 | {{< /table-caption >}}
> 🔼 표 2는 수학 데이터셋으로만 학습된 Satori-Qwen-7B 모델이 다양한 도메인의 벤치마크에서 강력한 전이 학습 능력을 보여주고, Qwen-2.5-Math-7B-Instruct 모델보다 훨씬 뛰어난 성능을 달성함을 보여줍니다.  더욱이, 다른 도메인에 대한 학습 없이도 Satori-Qwen-7B는 다른 소규모 일반 지시 모델과 비교하여 동등하거나 그 이상의 성능을 달성합니다. 이 표는 Satori-Qwen-7B 모델의 일반화 능력과 범용성을 보여주는 주요 증거를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Results on Out-of-domain Benchmarks. Trained only on math datasets, Satori-Qwen-7B exhibits strong transferability across diverse out-of-domain benchmarks and outperforms Qwen-2.5-Math-7B-Instruct by a large margin. Moreover, despite not being trained in other domains, Satori-Qwen-7B achieves performance comparable to or exceeding other small-scale general instruct models.
> </details>

{{< table-caption >}}
| Model | GSM8K | MATH500 | Olym. | AMC2023 | AIME2024 |
|---|---|---|---|---|---| 
| Qwen-2.5-Math-7B-Instruct | 95.2 | 83.6 | 41.6 | 62.5 | 16.7 |
| Qwen-7B-CoT (SFT+RL) | 93.1 | 84.4 | 42.7 | 60.0 | 10.0 |
| Satori-Qwen-7B | 93.2 | 85.6 | 46.6 | 67.5 | 20.0 |{{< /table-caption >}}
> 🔼 표 3은 Chain-of-Action-Thought (COAT) 추론 방식과 기존 Chain-of-Thought (CoT) 추론 방식을 사용하여 학습된 모델의 성능을 비교한 표입니다.  동일한 기반 모델인 Qwen-2.5-Math-7B를 사용하여, COAT 방식으로 학습된 Satori-Qwen-7B 모델이 기존 CoT 방식으로 학습된 Qwen-7B-CoT 모델보다 우수한 성능을 보여줌을 보여줍니다.  이는 COAT 방식이 단일 LLM의 추론 능력 향상에 더 효과적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: COAT Training v.s. CoT Training. Qwen-2.5-Math-7B trained with COAT reasoning format (Satori-Qwen-7B) outperforms the same base model but trained with classical CoT reasoning format (Qwen-7B-CoT)
> </details>

{{< table-caption >}}
| Model | MATH500 T→F | MATH500 F→T | OlympiadBench T→F | OlympiadBench F→T | MMLUProSTEM T→F | MMLUProSTEM F→T |
|---|---|---|---|---|---|---|
| Satori-Qwen-7B-FT | 79.4% | 20.6% | 65.6% | 34.4% | 59.2% | 40.8% |
| Satori-Qwen-7B | 39.0% | 61.0% | 42.1% | 57.9% | 46.5% | 53.5% |{{< /table-caption >}}
> 🔼 표 4는 Satori 모델의 자가 수정 능력을 보여줍니다.  T→F는 잘못된 답을 잘못된 답으로 수정한 경우(자가 수정 실패)를, F→T는 잘못된 답을 올바른 답으로 수정한 경우(자가 수정 성공)를 나타냅니다.  표에는 다양한 문제 유형(도메인 내 MATH500 및 OlympiadBench, 도메인 외 MMLUProSTEM)에 대한 자가 수정 성공률과 실패율이 제시되어 있습니다. 이를 통해 Satori 모델이 다양한 유형의 문제에서 얼마나 효과적으로 자가 수정 능력을 발휘하는지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Satori’s Self-correction Capability. T→→\rightarrow→F: negative self-correction; F→→\rightarrow→T: positive self-correction.
> </details>

{{< table-caption >}}
| (In-domain) | GSM8K | MATH500 | Olym. | AMC2023 | AIME2024 |
|---|---|---|---|---|---|---|
| Qwen-2.5-Math-7B-Instruct | 95.2 | 83.6 | 41.6 | 62.5 | 16.7 |
| Satori-Qwen-7B-FT (300K) | 92.3 | 78.2 | 40.9 | 65.0 | 16.7 |
| **Satori-Qwen-7B** | 93.2 | 85.6 | 46.6 | 67.5 | 20.0 |
| (Out-of-domain) | BGQA | CRUX | STGQA | TableBench | STEM |
|---|---|---|---|---|---|---|
| Qwen-2.5-Math-7B-Instruct | 51.3 | 28.0 | 85.3 | 36.3 | 45.2 |
| Satori-Qwen-7B-FT (300K) | 50.5 | 29.5 | 74.0 | 35.0 | 47.8 |
| **Satori-Qwen-7B** | 61.8 | 42.5 | 86.3 | 43.4 | 56.7 |{{< /table-caption >}}
> 🔼 표 5는 대규모 미세 조정(Fine-tuning, FT)과 강화 학습(Reinforcement Learning, RL)을 사용한 Satori-Qwen 모델과, 동일한 기반 모델인 Qwen-2.5-Math-7B에 대해 30만 건의 FT 데이터만으로 학습한 모델의 성능을 비교한 표입니다.  Satori-Qwen 모델은 1만 건의 FT 데이터와 30만 건의 RL 데이터를 사용하여 학습되었으며, 수학 관련 과제와 도메인 외부 과제 모두에서 Qwen-2.5-Math-7B 모델보다 뛰어난 성능을 보여줍니다. 이는 강화 학습이 모델의 추론 능력 향상에 효과적임을 보여주는 결과입니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Large-scale FT V.S. Large-scale RL Satori-Qwen (10K FT data + 300K RL data) outperforms same base model Qwen-2.5-Math-7B trained with 300K FT data (w/o RL) across all math and out-of-domain benchmarks.
> </details>

{{< table-caption >}}
| Bonus Scale | GSM8K | MATH500 | Olym. | AMC2023 | AIME2024 |
|---|---|---|---|---|---| 
| 0.0 | 93.6 | 84.4 | 48.9 | 62.5 | 16.7 |
| 0.5 (default) | 93.2 | 85.6 | 46.6 | 67.5 | 20.0 |{{< /table-caption >}}
> 🔼 본 표는 reflection bonus의 영향을 분석하기 위해 ablation study를 수행한 결과를 보여줍니다.  reflection bonus는 모델이 self-reflection 능력을 향상시키도록 하는 보상 메커니즘입니다.  표는 reflection bonus의 크기(bonus scale)를 다르게 설정했을 때, 여러 수학 추론 벤치마크(GSM8K, MATH500, Olympiad, AMC2023, AIME2024)에서의 성능 변화를 보여줍니다.  기본값(default)인 0.5와 0.0의 두 가지 값을 비교하여 reflection bonus가 모델 성능에 미치는 영향을 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Ablation Study on Reflection Bonus.
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