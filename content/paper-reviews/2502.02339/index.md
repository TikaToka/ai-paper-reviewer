---
title: "Boosting Multimodal Reasoning with MCTS-Automated Structured Thinking"
summary: "AStar: MCTS 기반의 자동화된 구조적 사고를 활용한 다중 모드 추론 개선"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Multimodal Reasoning", "🏢 Tsinghua University",]
showSummary: true
date: 2025-02-04
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.02339 {{< /keyword >}}
{{< keyword icon="writer" >}} Jinyang Wu et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-06 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.02339" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.02339" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/boosting-multimodal-reasoning-with-mcts" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

다중 모드 대규모 언어 모델(MLLM)은 복잡한 시각적 추론 작업에서 여전히 어려움을 겪고 있습니다. 최근 연구는 **OpenAI의 Chain-of-Thought(CoT)와 같은 구조적 사고를 도입하여 MLLM의 추론 능력을 향상**시키려고 시도했지만, 성능과 효율성 사이의 균형을 맞추는 데 어려움을 겪었습니다. 이는 **방대한 데이터와 검색 공간에 대한 의존도가 높기 때문**입니다. 본 논문에서는 이러한 문제를 해결하기 위해 **MCTS(Monte Carlo Tree Search) 기반의 자동화된 구조적 사고 패러다임인 AStar**를 제안합니다. AStar는 MCTS를 통해 제한된 데이터로부터 고차원적 인지 추론 패턴을 자동으로 도출하고, 이를 기반으로 모델의 내부 추론 능력과 외부 추론 지침을 원활하게 통합하는 통합 추론 프레임워크를 설계합니다.  이를 통해 최소한의 트리 반복 횟수로 효율적인 추론을 가능하게 합니다.  



본 논문에서는 광범위한 실험을 통해 AStar의 효과를 입증합니다. 특히 **MathVerse 벤치마크에서 7B 백본을 사용하여 54.0%의 정확도**를 달성하여 GPT-4(50.2%)를 능가하는 동시에 상당한 데이터 및 계산 효율성을 유지했습니다. 또한, **다양한 다중 모드 추론 작업에 대한 실험 결과**를 통해 AStar의 우수성을 보여주며, 제한된 데이터 환경에서 다중 모드 추론의 성능을 향상하는 데 중요한 의미를 가지는 새로운 방법론을 제시합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 제한된 데이터로 고성능 다중 모드 추론을 달성하는 AStar 프레임워크 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} MCTS 기반 계층적 구조를 통해 효율적인 추론 패턴 자동 도출 및 통합 추론 프레임워크 설계 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} MathVerse 벤치마크에서 GPT-4보다 높은 정확도 달성 및 데이터 및 계산 효율성 향상 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **제한된 데이터만으로 효율적인 다중 모드 추론을 가능하게 하는 새로운 구조적 사고 프레임워크인 AStar**를 제시하여 다중 모드 대규모 언어 모델(MLLM)의 추론 능력 향상에 크게 기여합니다. **MCTS 기반의 계층적 구조를 통해 효율적인 추론 패턴을 자동으로 도출하고, 내부 및 외부 추론 지침을 통합하는 통합 추론 프레임워크**를 설계하여 성능과 효율성을 균형 있게 유지합니다. 이는 **제한된 데이터 환경에서 다중 모드 추론 성능을 향상시키는 데 중요한 의미**를 가지며, 향후 연구의 새로운 방향을 제시합니다.  또한, **다양한 다중 모드 추론 벤치마크에 대한 실험 결과**를 통해 AStar의 우수성을 입증하며, 관련 분야 연구자들에게 중요한 시사점을 제공합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.02339/x12.png)

> 🔼 그림 1은 MathVerse 벤치마크에 대한 다양한 모델들의 성능 비교를 보여줍니다. AStar 프레임워크는 대부분의 오픈소스 및 클로즈드소스 MLLM(다중 모드 대형 언어 모델)에 비해 경쟁력 있는 결과를 달성하며, 뛰어난 구조적 사고 및 추론 능력을 보여줍니다.  차트는 MathVerse 벤치마크에서의 정확도를 모델 크기별로 비교 분석한 것입니다. AStar가 다른 모델들보다 우수한 성능을 보임을 보여줍니다. 특히, AStar는 7B 백본을 사용하여 MathVerse 벤치마크에서 54.0%의 정확도를 달성하여 GPT-4(50.2%)를 능가하는 성능을 기록했습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Performance comparison on the MathVerse benchmark. Our AStar framework achieves competitive results against most open-sourced MLLMs and closed-source ones, showing outstanding structured thinking and reasoning abilities.
> </details>





{{< table-caption >}}
| Model | #Params | MathVista ALL | MathVista ARI | MathVista LOG | MathVista STA | MathVista VQA | MathVerse ALL | MathVerse VI | MathVerse VD | MathVerse VO | MathVerse TD | MathVerse TL | MathVerse TO |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Random | - | 17.9 | 13.8 | 13.4 | 14.3 | 26.3 | 12.4 | 12.4 | 12.4 | 12.4 | 12.4 | 12.4 | 12.4 |
| Human | - | 60.3 | 59.2 | 40.7 | 63.9 | 55.9 | 64.9 | 61.4 | 68.3 | 66.7 | 71.2 | 70.9 | 41.7 |
| _Open-Source General MLLMs_ |  |  |  |  |  |  |  |  |  |  |  |  |  |
| mPLUG-Owl2-7B [Ye et al. (2023)] | 7B | 22.2 | 19.2 | 13.5 | 21.4 | 27.9 | 10.3 | 11.1 | 9.4 | 8.0 | 11.6 | 11.4 | 13.8 |
| MiniGPT4-7B [Zhu et al. (2023)] | 7B | 23.1 | 32.0 | 10.8 | 17.9 | 30.2 | 12.2 | 12.5 | 14.8 | 8.7 | 12.3 | 12.9 | 13.4 |
| LLaVA-1.5-13B [Liu et al. (2024a)] | 13B | 27.7 | 28.6 | 10.8 | 22.9 | 30.2 | 12.7 | 12.6 | 12.7 | 9.0 | 17.1 | 12.0 | 22.6 |
| SPHINX-V2-13B [Lin et al. (2023)] | 13B | 36.7 | 33.4 | 24.3 | 51.5 | 43.0 | 16.1 | 16.4 | 15.6 | 16.2 | 20.8 | 14.1 | 14.0 |
| SPHINX-MoE [Lin et al. (2023)] | 8x7B | 42.6 | 43.0 | 14.4 | 50.8 | 43.3 | 22.8 | 21.1 | 19.6 | 18.3 | 33.3 | 21.9 | 23.1 |
| LLaVA-NeXT-34B [Liu et al. (2024b)] | 34B | 46.5 | - | - | - | - | 34.6 | 35.2 | 28.9 | 22.4 | 49.0 | 37.6 | 30.1 |
| InternLM-XComposer2-VL [Dong et al. (2024c)] | 7B | 57.6 | 51.6 | 13.5 | 62.8 | 39.7 | 25.9 | 20.1 | 24.4 | 19.8 | 36.9 | 28.3 | 42.5 |
| Deepseek-VL [Lu et al. (2024)] | 7B | 34.9 | 38.8 | 18.9 | 33.2 | 34.6 | 19.3 | 20.2 | 18.4 | 11.8 | 23.0 | 23.2 | 23.1 |
| InternVL2-8B [Chen et al. (2024d)] | 8B | 58.3 | 56.4 | 10.8 | 68.8 | 49.7 | 35.9 | 32.2 | 30.9 | 27.7 | 39.0 | 33.8 | 36.0 |
| Qwen2-VL [Wang et al. (2024b)] | 7B | 58.9 | 57.5 | 24.3 | 43.1 | 58.1 | 33.6 | 31.3 | 30.3 | 28.1 | 37.4 | 33.5 | 35.0 |
| _Open-Source Math MLLMs (Large-Scale Training)_ |  |  |  |  |  |  |  |  |  |  |  |  |  |
| G-LLaVA-7B [Gao et al. (2023)] | 7B | 25.1 | 19.4 | 15.2 | 15.1 | 28.7 | 16.6 | 17.2 | 14.6 | 9.4 | 20.9 | 20.7 | 21.1 |
| Math-LLaVA-13B [Shi et al. (2024)] | 13B | 46.6 | 40.7 | 23.3 | 42.3 | 33.5 | 22.9 | 24.5 | 21.7 | 16.1 | 27.3 | 24.9 | 27.0 |
| Math-PUMA-Qwen2-7B [Zhuang et al. (2024)] | 7B | 47.9 | 46.2 | 21.6 | 55.8 | 30.2 | 33.6 | 33.4 | 31.6 | 26.0 | 42.1 | 35.0 | 39.8 |
| Math-PUMA-DeepSeek-Math [Zhuang et al. (2024)] | 7B | 44.7 | 41.9 | 8.1 | 50.8 | 31.3 | 31.8 | 33.6 | 31.6 | 14.7 | 43.4 | 35.4 | 47.5 |
| MAVIS-7B [Zhang et al. (2024d)] | 7B | - | - | - | - | - | 35.2 | 34.1 | 29.7 | 31.8 | 43.2 | 37.2 | - |
| InfiMM-Math [Han et al. (2024)] | 7B | - | - | - | - | - | 34.5 | 38.1 | 32.4 | 15.8 | 46.7 | 32.4 | - |
| MultiMath-7B [Peng et al. (2024)] | 7B | 50.0 | 42.2 | 23.3 | 64.9 | 49.2 | 27.7 | 28.1 | 25.9 | 15.0 | 34.8 | 30.8 | 35.3 |
| URSA-7B [Luo et al. (2025)] | 7B | 59.8 | 53.5 | 21.6 | 57.1 | 40.2 | 45.7 | 46.4 | 43.9 | 28.6 | 55.3 | 48.3 | 51.8 |
| AStar (Ours, Training-free Reasoning) | 7B | 63.5 | 63.1 | 61.3 | 68.8 | 60.1 | 54.0 | 46.8 | 61.8 | 46.4 | 53.9 | 44.3 | 53.9 |{{< /table-caption >}}

> 🔼 표 1은 MathVista와 MathVerse testmini 데이터셋에서 AStar의 추론 성능을 평가한 결과입니다. MathVista의 경우 전체 정확도(ALL), 산술 추론(ARI), 논리 추론(LOG), 통계 추론(STA), 시각적 질문 답변(VQA) 등 다섯 가지 범주로 나누어 평가하였고, MathVerse의 경우 전체 정확도(ALL), 시각 집중(VI), 시각 우세(VD), 시각 전용(VO), 텍스트 우세(TD), 텍스트 경량(TL), 텍스트 전용(TO) 등 일곱 가지 범주로 나누어 평가하였습니다. 가장 좋은 결과는 굵은 글씨체로 강조 표시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Evaluation of AStar’s reasoning capabilities on MathVista and MathVerse testmini. The best results are highlighted in bold. For MathVista, we pick five categories: ALL (overall accuracy), ARI (arithmetic reasoning), LOG (logical reasoning), STA (statistical reasoning), and VQA (visual question answering). For MathVerse, we present seven categories: ALL (overall accuracy), VI (vision intensive), VD (vision dominant), VO (vision only), TD (text dominant), TL (text lite), and TO (text only).
> </details>





### In-depth insights


#### Multimodal Reasoning
본 논문에서 다루는 핵심 개념 중 하나인 "다중 모드 추론(Multimodal Reasoning)"은 **시각적, 언어적 정보를 포함한 다양한 모드의 데이터를 통합하여 추론하는 능력**을 의미합니다.  이는 단순히 각 모드의 정보를 개별적으로 처리하는 것을 넘어, **모드 간의 상호작용과 연관성을 파악하고, 이를 바탕으로 복잡한 문제를 해결**하는 능력을 필요로 합니다.  **대규모 언어 모델(LLM)**은 이러한 다중 모드 추론 능력을 향상시키기 위한 중요한 연구 분야로, 특히 **시각적 추론(Visual Reasoning)** 과제에서의 성능 향상에 초점이 맞춰져 있습니다.  **구조화된 사고(Structured Thinking)**는 다중 모드 추론의 효율성과 정확도를 개선하는 데 중요한 역할을 하며, 본 논문에서는 **MCTS(Monte Carlo Tree Search)** 기반의 자동화된 구조적 사고 프레임워크를 제시하여 이러한 문제를 해결**하고자 합니다.  효율적인 다중 모달 추론을 위한 핵심적인 요소는 **데이터 활용의 효율성**과 **계산 효율성** 사이의 균형을 맞추는 것에 있습니다.

#### MCTS-AStar
MCTS-AStar는 **몬테 카를로 트리 탐색(MCTS)** 알고리즘을 기반으로 한 **자동화된 구조적 사고(Automated Structured Thinking)** 방식의 다중 모드 추론 방법론을 나타냅니다.  기존의 다중 모드 언어 모델(MLLM)의 추론 한계를 극복하기 위해, MCTS-AStar는 제한된 데이터를 사용하여 계층적 구조를 통해 고차원적 인지 추론 패턴을 자동으로 도출합니다.  이를 통해 MLLM의 내재적 추론 능력과 명시적 추론 지침을 원활하게 통합하여 최소한의 트리 반복으로 효율적인 추론을 가능하게 합니다. **성능과 효율성의 균형**을 이루는 혁신적인 패러다임으로, 제한된 데이터와 계산 자원으로도 우수한 정확도를 달성하는 것이 특징입니다. 특히 **MathVerse 벤치마크에서 GPT-4를 능가하는 성능**을 보이며 그 효과가 입증되었습니다.  **자동화된 추론 패러다임, 효율적인 액션 체인 기반 추론, 우수한 성능과 향상된 효율성**이 주요 강점입니다.

#### Reasoning Actions
논문에서 제시된 추론 행위는 **다양한 시각적 추론 과제를 효율적으로 해결하기 위한 핵심 구성 요소**입니다.  각 행위는 시각적 정보 처리, 문제 분석, 추론 단계 계획 및 검증 등의 **인지 과정을 모방**하여 설계되었으며,  **계층적이고 순차적인 추론 과정**을 가능하게 합니다.  **시각적 분석**은 시각 정보를 해석하고 핵심 요소를 파악하는 단계이며, **시스템 분석**은 문제의 구조와 조건을 파악하여 추론 방향을 설정하는 단계입니다. **일단계 추론**은 단순하고 직접적인 추론을 수행하는 반면, **연쇄 추론**은 복잡한 문제를 여러 단계로 나누어 해결하는 방식을 보여줍니다.  **분할 정복**은 복잡한 문제를 작은 하위 문제로 분해하고 각각을 해결하여 전체 문제를 해결하는 전략을 사용합니다.  **자기 반성**은 추론 과정을 검토하고 필요한 수정을 가하는 단계입니다.  이러한 추론 행위는 **인간의 인지 과정을 모방**함으로써, **다양한 유형의 시각적 추론 문제에 대한 적응력과 효율성을 향상**시키는 데 기여합니다.  본 논문의 핵심 아이디어는 이러한 행위를 **효과적으로 조합**하여 복잡한 시각적 추론 문제를 해결하는 것입니다.

#### Empirical Results
본 논문의 '실증적 결과' 부분은 제안된 방법의 성능을 다양한 측면에서 평가한 결과를 제시할 것으로 예상됩니다. **정확도, 효율성, 일반화 성능 등의 지표**를 사용하여 기존 방법들과 비교 분석하는 결과가 포함될 것입니다. 특히, **다양한 데이터셋과 모델 크기**에 대한 실험 결과를 통해 제안된 방법의 범용성과 확장성을 보여주는 것이 중요합니다.  **복잡한 추론 문제에 대한 해결 능력**을 평가하는 실험 결과는 제안된 방법의 우수성을 보여주는 핵심적인 부분이 될 것입니다.  또한, **계산 비용 및 데이터 사용량 측면**에서의 효율성을 비교 분석하여 제안된 방법의 실용성을 강조하는 것도 중요한 요소입니다.  **결과 분석을 통해 제안된 방법의 장점과 한계점**을 명확하게 제시하고, 향후 연구 방향을 제시하는 것도 중요합니다.  **도표나 그래프 등의 시각 자료**를 적절하게 활용하여 독자들이 결과를 쉽게 이해할 수 있도록 하는 것도 중요합니다.  전반적으로, 실증적 결과는 논문의 주장을 뒷받침하는 핵심적인 근거가 되므로, **신뢰성 있고 설득력 있는 결과**를 제시하는 것이 매우 중요합니다.

#### Future Work
본 논문의 "미래 연구" 부분에 대한 심층적인 고찰은 **다양한 모달리티를 포괄하는 더욱 복잡한 추론 작업에 대한 AStar의 확장성을 검토**하는 것부터 시작될 것입니다. 이는 더욱 다양한 데이터 세트와 더욱 강력한 백본 모델을 사용하여 AStar의 성능을 평가하는 것을 포함합니다. 또한, **추론 효율성 향상을 위한 MCTS 알고리즘 최적화** 연구도 중요한 과제입니다. 이를 위해, 트리 탐색 전략, 보상 함수 설계, 그리고 탐색 공간 관리 등의 측면에서 심층적인 분석이 필요합니다.  **AStar의 일반화 능력을 높이는 연구** 또한 필수적입니다. 특히, 다양한 분야의 문제들에 대한 AStar의 적용성을 평가하고, 낮은 데이터 조건에서의 성능을 개선하기 위한 연구가 필요합니다.  나아가, **다른 추론 패러다임과의 통합 연구**를 통해 AStar의 한계를 극복하고, 강점을 더욱 강화해야 합니다. 이를 위해, AStar와 기존의 teacher-guided training 방식 또는 symbolic reasoning 기법 등의 결합을 통해 새로운 추론 프레임워크를 구축하는 연구가 필요하며, 이는 **더욱 강력하고 효율적인 다중 모달 추론 시스템 개발**로 이어질 수 있습니다.  마지막으로, **AStar의 해석성을 높이는 연구** 또한 중요합니다. 이를 통해 AStar의 추론 과정을 이해하고, 더욱 신뢰할 수 있는 결과를 얻을 수 있도록 해야 합니다.


### More visual insights




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | #Params | MMStar | ChartQA |
|---|---|---|---| 
| *2B-Scale Baselines* |  |  |  |
| Qwen2-VL [Wang et al. (2024b)] | 2B | 48.0 | 73.5 |
| Mulberry [Yao et al. (2024)] | 2B | 51.3 | 77.7 |
| AStar (Ours) | 2B | **51.7** | **78.3** |
| ≥ 7B-Scale Baselines |  |  |  |
| Deepseek-VL [Lu et al. (2024)] | 7B | 36.1 | 59.1 |
| Qwen2-VL [Wang et al. (2024b)] | 7B | 60.7 | 83.0 |
| InternVL2 [Chen et al. (2024d)] | 8B | 61.5 | 83.3 |
| Insight-V [Dong et al. (2024d)] | 7B | 61.5 | 82.3 |
| Mulberry [Yao et al. (2024)] | 7B | 61.3 | **83.9** |
| LLaVA-CoT [Xu et al. (2024)] | 11B | 58.1 | - |
| LlamaV-o1 [Thawakar et al. (2025)] | 11B | 59.5 | - |
| AStar (Ours) | 7B | **61.7** | **83.9** |{{< /table-caption >}}
> 🔼 표 2는 MMStar와 ChartQA라는 두 가지 일반적인 VQA(Visual Question Answering) 데이터셋에서 강력한 기준 모델들과 비교한 AStar의 성능을 보여줍니다.  AStar 모델은 2B와 7B 파라미터 크기의 두 가지 버전으로 평가되었으며, 각 데이터셋에서의 정확도(Accuracy)를 비교하여 AStar의 효율성과 성능을 보여줍니다.  다양한 크기의 모델들에 대한 비교를 통해 AStar의 확장성과 효율성을 확인할 수 있습니다.  특히, 기존의 강력한 VQA 모델들과의 비교를 통해 AStar의 경쟁력을 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Comparison with powerful baselines on general VQA datasets: MMStar and ChartQA.
> </details>

{{< table-caption >}}
| Methods | Open-Source Only | Training-Free | Data Volume | Search Iter. ↓ | MathVista Acc. ↑ | MMStar Acc. ↑ | GAOKAO Acc. ↑ |
|---|---|---|---|---|---|---|---| 
| AR-MCTS [Dong et al. (2024a)](https://arxiv.org/html/2502.02339/bib13.png) | ✓ | ✗ | 34.5K | 32.0 | **64.1** | - | 37.4 |
| Mulberry [Yao et al. (2024)](https://arxiv.org/html/2502.02339/bib73.png) | ✗ | ✗ | 260K | - | 63.1 | 61.3 | - |
| Ours | ✓ | ✓ | 0.5K | **5.0** | 63.5 | **61.7<sup>0.4↑</sup>** | **49.7<sup>12.3↑</sup>** |{{< /table-caption >}}
> 🔼 표 3은 선행 연구들의 다양한 다중 모드 트리 기반 검색 방법들과 AStar 방법의 성능을 비교 분석한 표입니다.  AStar는 기존 방법들보다 훨씬 적은 데이터(0.5K)와 샘플 당 5번의 검색 반복만으로도 경쟁력 있는 성능을 달성하여 효율성과 효과성 면에서 우수함을 보여줍니다.  이는 AStar가 제한된 데이터로도 고차원적 사고 패턴을 효과적으로 추출하고 활용할 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Comparison with leading multimodal tree search methods. AStar achieves competitive performance with only 0.5K prior data and 5 search iterations per sample, demonstrating superior efficiency and effectiveness.
> </details>

{{< table-caption >}}
| Model Setting | MathVista | MathVerse | Average |
|---|---|---|---|
| AStar | **63.5** | **54.0** | **58.8** |
| - w/o thought cards (RA) | 58.9 | 48.5 | 53.7<sup>**-5.1**↓</sup> |
| - w/o card match (RC) | 61.3 | 50.3 | 55.8<sup>**-3.0**↓</sup> |
| - w/o verification (RS) | 62.0 | 51.6 | 56.8<sup>**-2.0**↓</sup> |
| - w/o verification (SC) | 63.0 | 51.8 | 57.4<sup>**-1.4**↓</sup> |{{< /table-caption >}}
> 🔼 표 4는 AStar-7B 모델에 대한 ablation study 결과를 보여줍니다. 각 구성 요소(thought card 생성, card 매칭, 추론 단계 선택, self-consistency 검증)의 중요성을 확인하기 위해, 각 구성 요소를 제거한 경우의 성능 변화를 측정했습니다.  결과적으로 모든 구성 요소가 최적의 성능 달성에 중요하다는 것을 보여줍니다.  'RA'는 무작위 행동, 'RC'는 무작위 카드, 'RS'는 무작위 선택, 'SC'는 self-consistency를 의미합니다.  각 요소를 제거했을 때 MathVista와 MathVerse 데이터셋에서의 정확도가 모두 감소하여, 각 구성 요소의 중요성을 입증합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Ablation results on AStar-7B. ‘RA’, ‘RC’, ‘RS’, ‘SC’ denotes ‘random actions’, ‘random card’, ‘random selection’, and ‘self-consistency’, respectively. We observe that every component is important for optimal performance.
> </details>

{{< table-caption >}}
| Character | Meaning |
|---|---| 
| \(\pi_{\theta}\) | policy MLLM |
| I | task instruction |
| \(\mathcal{D}_{I}\) | demonstration examples of I, which is \(\phi\) in zero-shot settings |
| \(D_{s}\) | seed data |
| \(D_{t}\) | test data |
| \(x_{t}\) | multimodal test problem, consisting of input question \(q\) and images \(i\) |
| \(y_{d}\) | decoded answer |
| \(y_{g}\) | gold standard answer |
| \(y_{t}\) | reasoning trajectory / solution |
| T | number of reasoning steps |
| \(T_{d}\) | number of tokens in decoded answer \(y_{p}\) |
| \(a_{t}\) | t-th decoded answer token of \(y_{d}\) |
| \(s_{t}\) | t-th reasoning step of trajectory \(y_{t}\) |
| \(S_{t}\) | t-th state, which consists of input x and preceding reasoning steps \((s_{1},s_{2},...,s_{t-1})\) |
| \(a_{t}\) | t-th action based on the previous state \(S_{t-1}\) |
| s | node s in the tree structure |
| p | parent node of s |
| \(Q(s)\) | reward value of node s |
| \(p_{\varphi}\) | process reward model |
| \(o_{\psi}\) | outcome reward model |{{< /table-caption >}}
> 🔼 표 5는 논문의 A. Preliminaries 섹션에 있는 표로, 논문에서 사용되는 다양한 기호와 약어에 대한 정의를 담고 있습니다. 각 기호는 영어로 된 의미와 함께 설명되어 있어 논문 전체를 이해하는 데 도움을 줍니다.  특히, MLLM 추론, MCTS, 검증 방법 등 논문의 핵심 개념을 이해하는 데 필요한 기호들이 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Notation Table
> </details>

{{< table-caption >}}
| Method | Open-Source Only | Data Volume | Training-Free | Training Cost ↓ | Inference Cost ↓ |
|---|---|---|---|---|---| 
| AR-MCTS [Dong et al. (2024a)](https://arxiv.org/html/2502.02339/bib13.png) | ✓ | 34.5K | ✓ | - | High |
| Mulberry [Yao et al. (2024)](https://arxiv.org/html/2502.02339/bib73.png) | ✗ | 260K | ✗ | High | Low |
| LLaVA-CoT [Xu et al. (2024)](https://arxiv.org/html/2502.02339/bib70.png) | ✗ | 100K | ✗ | High | Low |
| URSA [Luo et al. (2025)](https://arxiv.org/html/2502.02339/bib43.png) | ✗ | 1100K | ✗ | High | Low |
| LlamaV-o1 [Thawakar et al. (2025)](https://arxiv.org/html/2502.02339/bib59.png) | ✗ | 118K | ✗ | High | Low |
| AStar (Ours) | ✓ | 0.5K | ✓ | Low | Low |{{< /table-caption >}}
> 🔼 표 6은 최근 다양한 연구에서 제시된 다중 모드 구조적 추론 방법들을 비교 분석한 표입니다.  각 방법의 오픈소스 여부, 사용된 데이터 크기, 사전 학습 없이 사용 가능한지 여부, 학습 비용, 추론 비용 등 다섯 가지 측면을 비교하여 각 방법의 효율성과 성능을 종합적으로 평가하고 있습니다.  AStar를 포함한 여러 방법들이 비교 대상에 포함되어 있으며, AStar의 효율성 및 성능 우위를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Method Comparison: Recent Multimodal Structured Reasoning Approaches.
> </details>

{{< table-caption >}}
| Type | Method | Action Space |
|---|---|---|
| LLM | Tree-of-Thought Yao et al. (2023) | a<sub>3</sub>: one-step thought |
|  | RAP Hao et al. (2023) | a<sub>5</sub>: divide and conquer |
|  | ReST-MCTS* Zhang et al. (2024b) | a<sub>3</sub>: one-step thought |
|  | MCTSr Zhang et al. (2024a) | a<sub>4</sub>: chain-of-thought, a<sub>6</sub>: self-reflection |
| MLLM | AR-MCTS Dong et al. (2024a) | a<sub>3</sub>: one-step thought |
|  | LLaVA-CoT Xu et al. (2024) | a<sub>4</sub>: chain-of-thought |
|  | URSA Luo et al. (2025) | a<sub>4</sub>: chain-of-thought |
| Ours |  | a<sub>1</sub>, a<sub>2</sub>, a<sub>3</sub>, a<sub>4</sub>, a<sub>5</sub>, a<sub>6</sub> |{{< /table-caption >}}
> 🔼 표 7은 다양한 검색 기반 LLM 및 MLLM 방법들과의 비교를 보여줍니다. 대부분의 기존 방법들은 제한된 행동 공간을 가지고 있는 반면, 본 논문에서 제시하는 AStar 방법은 풍부한 추론 행동 집합을 정의하여 모델의 추론 능력 상한선을 높입니다.  즉, AStar는 다양하고 복잡한 추론 작업에 유연하게 대처할 수 있도록 더욱 확장된 행동 세트를 제공합니다. 이 표는 각 방법의 종류(LLM 또는 MLLM), 사용된 방법, 행동 공간 등을 비교하여 AStar의 우수성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Comparison with other search-based LLM and MLLM methods. Note that, most method contain limited space. In contrast, we define a rich set of reasoning actions, thus enhancing the upper bound of model reasoning capabilities.
> </details>

{{< table-caption >}}
| Type | Dataset | Evaluation Dimensions |
|---|---|---|
| Visual Question Answering | ChartQA Masry et al. (2022) | chart understanding and reasoning |
|  | MMStar Chen et al. (2024b) | 6 core capabilities, like scientific reasoning |
| Mathematics | MathVista Lu et al. (2023) | 12 core capabilities, like arithmetic reasoning |
|  | MathVerse Zhang et al. (2025) | 6 distinct versions-text-dominant |
|  | MathVision Wang et al. (2024a) | 16 mathematical domains |
| Commonsense and science | GAOKAO-MM Zong & Qiu (2024) | 8 subjects, like history |{{< /table-caption >}}
> 🔼 표 8은 다양한 검색 기반 LLM 및 MLLM 방법들과의 비교를 보여줍니다. 대부분의 기존 방법들은 제한된 행동 공간을 가지고 있는 반면, 본 논문에서 제시하는 AStar는 풍부한 추론 행동 집합을 정의하여 모델의 추론 능력 상한선을 높였습니다.  이 표를 통해 AStar가 어떻게 다양한 추론 작업에 적합한지, 그리고 기존 방법들보다 더 나은 성능을 보이는지 비교 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Comparison with other search-based LLM and MLLM methods. Note that, most method contain limited space. In contrast, we define a rich set of reasoning actions, thus enhancing the upper bound of model reasoning capabilities.
> </details>

{{< table-caption >}}
| Hyperparameter | Value | Description |
|---|---|---|
| temperature | 0.8 | vllm inference settings |
| top-p | 0.9 |  |
| top-k | 40 |  |
| repetition penalty | 1.0 |  |
| max tokens | 1024 |  |
| maximum tree depth  $d_{max}$ | 5 | MCTS |
| exploration weight  $w$ | 2.0 |  |
| predefined terminal threshold  $c$ | 0.90 |  |
| balance factor  $k$ | 0.95 | VOC-based optimal path selection in *Sec. [3.2](https://arxiv.org/html/2502.02339v1#S3.SS2)* Phase 2 |{{< /table-caption >}}
> 🔼 표 9는 본 논문에서 사용된 모든 초매개변수를 보여줍니다.  각 초매개변수는  모델의 추론 과정에서 어떤 역할을 하는지, 그리고 해당 값이 어떻게 설정되었는지에 대한 설명이 포함되어 있습니다.  온도(temperature), top-p, top-k와 같은 초매개변수는 모델의 확률적 행동을 제어하며, 반복 페널티(repetition penalty)는 생성 텍스트의 반복을 제한합니다.  최대 토큰 수(max tokens)는 모델이 생성하는 토큰의 최대 개수를 지정하며, 최대 트리 깊이(maximum tree depth)는 MCTS 알고리즘에서 트리의 최대 깊이를 제한합니다. 탐험 가중치(exploration weight)는 MCTS 알고리즘의 탐험-활용 균형을 조절하며, 미리 정의된 종결 임계값(predefined terminal threshold)은 MCTS 알고리즘이 종료될 조건을 나타냅니다. 마지막으로, 균형 요소(balance factor)는 비용과 이점 사이의 균형을 맞추는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 9: All hyperparameters utilized in this paper.
> </details>

{{< table-caption >}}
| Model | #Params | ALL | ALG | ARI | GEO | LOG | NUM | SCI | STA |
|---|---|---|---|---|---|---|---|---|---| 
| *Baselines* |  |  |  |  |  |  |  |  |  |
| Random Choice | - | 17.9 | 25.8 | 13.8 | 22.7 | 13.4 | 8.8 | 15.8 | 14.3 |
| Human Performance | - | 60.3 | 50.9 | 59.2 | 51.4 | 40.7 | 53.8 | 64.9 | 63.9 |
| *Closed-source MLLMs* |  |  |  |  |  |  |  |  |  |
| Qwen-VL-Plus [Bai et al. (2023)] | - | 43.3 | 39.1 | 32.0 | 39.3 | 18.9 | 26.4 | 59.0 | 56.1 |
| GPT-4V [OpenAI (2023)] | - | 49.9 | 53.0 | 49.0 | 51.0 | 21.6 | 20.1 | 63.1 | 55.8 |
| *Open-source Genreral MLLMs* |  |  |  |  |  |  |  |  |  |
| mPLUG-Owl2-7B [Ye et al. (2023)] | 7B | 22.2 | 23.6 | 19.2 | 23.9 | 13.5 | 12.7 | 26.3 | 21.4 |
| LLaVA-1.5-13B [Liu et al. (2024b)] | 13B | 25.7 | 19.6 | 28.6 | 17.6 | 10.8 | 27.8 | 33.6 | 22.9 |
| MiniGPT-v2 [Chen et al. (2023)] | 7B | 23.1 | 28.1 | 21.0 | 24.7 | 16.2 | 16.7 | 25.4 | 17.9 |
| InternLM-XComposer2-VL-7B [Dong et al. (2024c)] | 7B | 47.8 | 32.0 | 51.6 | 30.5 | 13.5 | 43.8 | 37.7 | 62.8 |
| SPHINX-MoE [Lin et al. (2023)] | 8\times7B | 42.3 | 31.7 | 41.6 | 30.5 | 16.2 | 27.1 | 50.8 | 50.8 |
| DeepSeek-VL [Lu et al. (2024)] | 7B | 34.9 | 29.2 | 38.8 | 27.2 | 18.9 | 43.1 | 35.3 | 33.2 |
| InternVL2-8B [Chen et al. (2024d)] | 8B | 58.3 | 59.8 | 56.4 | 60.3 | 10.8 | 30.6 | 59.0 | 68.8 |
| Qwen2-VL [Wang et al. (2024b)] | 7B | 58.9 | 44.1 | 57.5 | 43.1 | 24.3 | 41.7 | 66.4 | 75.1 |
| *Open-source Math MLLMs (Large-Scale Training)* |  |  |  |  |  |  |  |  |  |
| G-LLaVA [Gao et al. (2024)] | 7B | 25.1 | 36.0 | 19.4 | 37.6 | 15.2 | 17.7 | 21.0 | 15.1 |
| Math-LLaVA [Shi et al. (2024)] | 13B | 46.6 | 51.5 | 40.7 | 56.2 | 23.3 | 34.7 | 47.7 | 42.3 |
| Multimath-7B [Peng et al. (2024)] | 7B | 50.0 | 61.9 | 42.2 | 64.9 | 23.3 | 32.6 | 42.6 | 49.2 |
| Math-PUMA-Qwen2-7B [Zhuang et al. (2024)] | 7B | 47.9 | 47.7 | 46.2 | 47.3 | 21.6 | 32.6 | 42.6 | 55.8 |
| URSA-7B [Luo et al. (2025)] | 7B | 59.8 | 74.0 | 53.5 | 77.4 | 21.6 | 35.4 | 58.2 | 57.1 |
| AStar (Ours, Training-free Reasoning) | 7B | 63.5 | 69.0 | 63.1 | 71.7 | 61.3 | 60.0 | 48.2 | 68.8 |
| AStar (Ours, Training-free Reasoning) | 2B | 49.6 | 51.0 | 49.9 | 53.1 | 34.7 | 46.8 | 41.3 | 54.3 |{{< /table-caption >}}
> 🔼 표 10은 MathVista testmini 데이터셋을 사용하여 평가한 다양한 수학적 능력에 대한 자세한 결과를 보여줍니다.  표에서 폐쇄형(closed-source) MLLM의 최고 성능은 녹색으로, 개방형(open-source) MLLM의 최고 및 차고 성능은 각각 빨간색과 파란색으로 강조 표시되어 있습니다.  이 표는 모델 크기에 관계없이 AStar 추론 프레임워크가 다양한 수학적 능력에 대한 성능을 효과적으로 향상시킨다는 것을 보여줍니다. 특히, 추론 백본으로 Qwen2-VL-2B를 사용한 2B 모델은 InternLM-XComposer2-VL-7B 및 Math-LLaVA와 같은 대형 모델을 능가하여 GPT-4V와 비슷한 성능을 달성합니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Results on MathVista testmini detailed mathematics capabilities. The best results of closed-source MLLMs are highlighted in green. The best and second-best results of open-source MLLMs are highlighted in red and blue respectively.
> </details>

{{< table-caption >}}
| Model | MathVista | MathVerse | MathVision | Average |
|---|---|---|---|---|
| **Closed-Source Models** |  |  |  |  |
| GPT-4o-0513 [OpenAI (2024)] | 63.8 | 50.2 | 30.4 | 48.2 |
| GPT-4V [OpenAI (2023)] | 49.9 | 54.4 | 24.8 | 43.1 |
| Gemini-1.5-Pro [Team et al. (2023)] | 63.9 | 35.3 | 19.2 | 39.5 |
| Claude-3.5-Sonnet [Anthropic (2024)] | 67.7 | - | - | - |
| Qwen-VL-Plus [Bai et al. (2023)] | 43.3 | 21.3 | 10.8 | 25.2 |
| **Open-Source Models** |  |  |  |  |
| Qwen2-VL-72B [Wang et al. (2024b)] | **70.5** | - | 25.9 | - |
| LLaVA-OneVision-72B [Li et al. (2024)] | 67.5 | 39.1 | - | - |
| InternVL2.5-26B [Chen et al. (2024d)] | 67.7 | 40.1 | 28.0 | 45.3 |
| InternVL2-Llama3-76B [Chen et al. (2024d)] | 65.5 | 42.8 | 23.7 | 44.0 |
| Astar (Ours) | 63.5 | **54.0** | **32.4** | **50.0** |{{< /table-caption >}}
> 🔼 표 11은 주요 대규모 언어 모델(LLM)들과 AStar 모델의 성능을 비교한 표입니다.  MathVista, MathVerse, MathVision 세 가지 벤치마크에서의 정확도를 비교하여 AStar의 성능을 보여줍니다.  AStar는 특히 MathVerse와 MathVision과 같은 복잡한 문제에서 우수한 성능을 보여주는 반면, 기존의 오픈소스 및 클로즈드소스 LLM 모델들과의 성능 차이를 명확하게 보여줍니다. 표의 결과는 해당 모델의 공식 웹사이트에서 가져왔습니다.
> <details>
> <summary>read the caption</summary>
> Table 11: Comparison with leading LLMs. The best results are highlighted in bold. Results for off-the-shelf models are sourced from corresponding official websites.
> </details>

{{< table-caption >}}
| Model | Size | MMStar | ChartQA | MathVista | MathVerse |
|---|---|---|---|---|---| 
| *2B-Scale Baselines* |  |  |  |  |  |
| Mulberry Yao et al. (2024) | 2B | 51.3 | 77.7 | **51.7** | - |
| Astar (Ours) | 2B | **51.7** | **78.3** | 49.6 | **33.7** |
| ≥ 7B-Scale Baselines |  |  |  |  |  |
| Insight-V Dong et al. (2024d) | 7B | 61.5 | 81.5 | 59.9 | - |
| AR-MCTS Dong et al. (2024a) | 7B | - | - | **64.1** | - |
| Mulberry Yao et al. (2024) | 7B | 61.3 | **83.9** | 63.1 | - |
| LLaVA-CoT OpenAI (2024) | 11B | 57.6 | - | 54.8 | - |
| LlamaV-o1 Thawakar et al. (2025) | 11B | 59.6 | - | 54.4 | - |
| URSA Luo et al. (2025) | 7B | - | - | 59.8 | 45.7 |
| Virgo Luo et al. (2025) | 7B | - | - | - | 37.5 |
| Astar (Ours) | 7B | **61.7** | **83.9** | 63.5 | **54.0** |{{< /table-caption >}}
> 🔼 표 12는 구조화된 추론을 통해 향상된 다중 모드 추론을 목표로 하는 최근 연구들과의 비교 결과를 보여줍니다. 2B 및 7B 이상 규모의 기준 모델들을 나열하여 제시하고 있으며, 각 상자에 표시된 최고 성능 결과는 굵게 표시되어 있습니다. 본 연구의 방법론이 성능을 크게 향상시켰음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 12: Comparison with recent works targeting enhanced multimodal reasoning through structured thinking. We list 2B and ≥\geq≥ 7B-scale baselines. The best results in each box are highlighted in bold. Our method demonstrates significant performance improvements.
> </details>

{{< table-caption >}}
| Backbone | 1 | 2 | 3 | 4 | 5 | Average |
|---|---|---|---|---|---|---|
| Qwen2-VL-2B-Base | 20.8 | 20.7 | 21.4 | 17.8 | 10.2 | 18.2 |
| Qwen2-VL-2B | **25.0** | 20.0 | 15.6 | 16.7 | **17.6** | **22.3** |
| Qwen2-VL-7B-Base | 26.8 | 20.6 | 23.7 | 26.7 | 22.4 | 23.4 |
| Qwen2-VL-7B | 26.5 | **21.3** | **26.2** | **29.8** | **23.8** | **25.5** |{{< /table-caption >}}
> 🔼 표 13은 MathVision 데이터셋에서 SFT(Supervised Fine-Tuning)와 통합된 AStar 프레임워크의 성능을 평가한 결과를 보여줍니다.  Qwen2-VL-2B와 Qwen2-VL-7B 모델을 백본 모델로 사용하여 사전 훈련된 기본 모델과 SFT 변형 모델 모두를 다양한 난이도 수준에서 비교 분석했습니다.  표는 각 모델의 성능을 다양한 난이도(1~5)에 따라 평균 성능과 함께 제시하여 SFT와 AStar 프레임워크의 시너지 효과 및 각 모델의 강점과 약점을 파악하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 13: Integration With SFT on MathVision. We evaluate the AStar framework using Qwen2-VL-2B and Qwen2-VL-7B as backbone models, comparing both pre-trained base models and SFT variants across different difficulty levels.
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