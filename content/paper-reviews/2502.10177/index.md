---
title: "STMA: A Spatio-Temporal Memory Agent for Long-Horizon Embodied Task Planning"
summary: "STMA: 시공간 기억을 활용한 장기간 임무 계획 에이전트가 30% 이상의 성능 향상을 달성했습니다!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["AI Applications", "Robotics", "🏢 Guangdong Provincial Key Laboratory of Future Networks of Intelligence",]
showSummary: true
date: 2025-02-14
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.10177 {{< /keyword >}}
{{< keyword icon="writer" >}} Mingcong Lei et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-17 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.10177" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.10177" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

많은 인공지능 시스템들이 역동적인 환경에서 장기간에 걸친 복잡한 작업을 수행하는 데 어려움을 겪고 있습니다. 특히 제한된 메모리 용량으로 인해 과거 정보를 효과적으로 통합하고 변화하는 환경에 적응하는 데 어려움이 있습니다.  이러한 문제는 의사 결정 정확도를 떨어뜨리고 장기간 작업 수행 능력을 저하시키는 주요 원인이 됩니다.

본 논문에서는 이러한 문제를 해결하기 위해 시공간 기억(Spatio-Temporal Memory)을 통합한 새로운 프레임워크인 STMA(Spatio-Temporal Memory Agent)를 제안합니다. STMA는 시공간 메모리 모듈, 동적 지식 그래프, 계획자-비평가 메커니즘으로 구성되어 있으며, 역동적인 환경에서의 적응적 공간 추론 및 작업 전략을 개선합니다. 실험 결과, STMA는 기존 최고 성능 모델에 비해 성공률 31.25%, 평균 점수 24.7% 향상을 보였습니다. 

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} STMA는 시공간 기억을 통합하여 장기간 임무 계획 및 실행 성능을 크게 향상시켰습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} STMA는 동적 KG 기반 공간 메모리, 계획자-비평가 폐쇄 루프 아키텍처, 그리고 개방형 모델 효율성을 갖춘 시공간 기억 메모리를 통해 강건성과 적응성을 높였습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} TextWorld 환경에서의 실험 결과는 STMA가 최첨단 모델에 비해 성공률과 평균 점수가 각각 31.25%, 24.7% 향상됨을 보여줍니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **장기간에 걸친 복잡한 작업 계획과 실행을 위한 새로운 프레임워크인 STMA**를 제시하여, **기존의 한계를 극복하고 에이전트의 기억 능력을 향상시키는 데 중요한 의미**를 가집니다.  **공개 소스 모델을 사용하여 높은 성능을 달성**한 점은 특히 주목할 만하며,  **실제 로봇 시스템 개발에 대한 새로운 가능성**을 열어줍니다. 또한, 제시된 **동적 KG 기반 공간 메모리, 계획자-비평가 폐쇄 루프 아키텍처, 개방형 모델 효율성을 갖춘 시공간 기억 메모리**는 **향후 연구 방향**을 제시하는 데 기여합니다.  이러한 연구는 **다양한 로봇 시스템에 적용 가능**하며, **인공지능 분야의 발전**에 기여할 것으로 기대됩니다. 

------
#### Visual Insights



![](https://arxiv.org/html/2502.10177/extracted/6203426/img/STMA_compare.jpg)

> 🔼 그림 1은 ReAct와 STMA의 비교 개요를 보여줍니다. (a) ReAct는 단순한 히스토리 버퍼를 사용하여 행동-피드백 쌍과 추론 정보를 저장하고, 한 번에 한 단계씩 행동을 생성합니다. 이 방법은 구조화된 시공간적 추론이 부족하여 복잡한 장기간 과제에 대한 적응성이 제한됩니다. (b) STMA는 전용 공간 메모리와 시간 메모리를 활용하여 대규모 모델의 기능을 사용하여 개선된 공간적 신념과 시간적 신념으로 요약합니다. 계획자-비평가 모듈을 통해 폐쇄 루프 계획이 가능하여 환경 피드백에 따라 동적으로 행동 순서를 검증하고 조정할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  Comparative overview of ReAct and STMA. (a) ReAct uses a simple history buffer to store action-feedback pairs and reasoning information, generating actions one step at a time. This approach lacks structured spatio-temporal reasoning, limiting its adaptability in complex, long-horizon tasks. (b) STMA utilizes dedicated spatial memory and temporal memory, summarized into refined spatial belief and temporal belief using the large model’s capabilities. The planner-critic module enables closed-loop planning, dynamically validating and adjusting action sequences based on environmental feedback.
> </details>





{{< table-caption >}}
| Difficulty Level | 1 |  | 2 |  | 3 |  | 4 |  |
|---|---|---|---|---|---|---|---|---|
|  | SR | AS | SR | AS | SR | AS | SR | AS |
| ReAct(GPT-4o) | 100.0 | 100.0 ± 0.0 | 62.5 | 76.5 ± 31.9 | 50.0 | 65.0 ± 39.4 | 25.0 | 43.3 ± 37.9 |
| Reflexion(GPT-4o) | 100.0 | 100.0 ± 0.0 | 62.5 | 78.6 ± 30.3 | 50.0 | 60.0 ± 40.9 | 25.0 | 51.0 ± 31.9 |
| AdaPlanner(GPT-4o) | 87.5 | 90.6 ± 24.8 | 37.5 | 51.8 ± 43.4 | 0.0 | 3.8 ± 4.8 | 0.0 | 1.9 ± 3.3 |
| **STMA(GPT-4o)** | **100.0** | **100.0 ± 0.0** | **75.0** | **91.1 ± 15.9** | **75.0** | **87.5 ± 26.3** | **37.5** | **60.6 ± 38.5** |
| ReAct(Qwen2.5-72b) | 75.0 | 75.0 ± 43.3 | 37.5 | 60.7 ± 34.1 | 12.5 | 37.5 ± 31.9 | 0.0 | 16.3 ± 9.0 |
| Reflexion(Qwen2.5-72b) | 100.0 | 100.0 ± 0.0 | 37.5 | 60.7 ± 32.5 | 25.0 | 61.2 ± 28.0 | 0.0 | 19.2 ± 7.7 |
| AdaPlanner(Qwen2.5-72b) | 100.0 | 100.0 ± 0.0 | 37.5 | 53.6 ± 41.5 | 0.0 | 3.8 ± 4.8 | 0.0 | 3.8 ± 5.4 |
| **STMA(Qwen2.5-72b)** | **100.0** | **100.0 ± 0.0** | **100.0** | **100.0 ± 0.0** | **62.5** | **81.2 ± 27.6** | **25.0** | **58.7 ± 30.3** |{{< /table-caption >}}

> 🔼 표 1은 STMA와 기준 모델 간의 성공률(SR)과 네 가지 난이도 수준에서의 평균 점수(AS)를 비교한 것입니다. 성능 지표는 표준 편차(σ)를 포함하여 AS±σ로 보고됩니다. 여기서 σ는 서로 다른 난이도 수준에 걸친 표준 편차를 나타냅니다. 즉, 표는 다양한 복잡성 수준의 작업에서 STMA의 성능을 기준 모델과 비교하여 STMA의 효과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparison of Success Rates (SR) and Average Scores (AS) across difficulty levels between STMA and baseline methods. Performance metrics are reported as A⁢S±σplus-or-minus𝐴𝑆𝜎AS\pm\sigmaitalic_A italic_S ± italic_σ, where σ𝜎\sigmaitalic_σ denotes the standard deviation across different difficulty levels.
> </details>





### In-depth insights


#### Spatio-temporal memory
본 논문에서 제안하는 **공간-시간 메모리**는 에이전트가 역동적인 환경에서 장기간에 걸친 작업 계획과 실행을 개선하기 위한 핵심 구성 요소입니다. **시간적 메모리**는 과거의 상호 작용 기록을 저장하고 압축하여 에이전트가 과거 경험을 효율적으로 활용할 수 있도록 합니다. **공간적 메모리**는 동적 지식 그래프를 통해 공간적 관계를 모델링하여 에이전트가 환경을 더욱 효과적으로 이해하고 탐색할 수 있도록 합니다. 두 메모리 시스템은 **계획-비평 메커니즘**과 통합되어 에이전트가 실시간으로 계획을 조정하고 최적의 전략을 신속하게 찾을 수 있도록 합니다. 이를 통해 에이전트는 부분적으로 관찰 가능한 환경에서 장기적인 계획을 세우고 실행하는 데 필요한 **적응력**과 **견고성**을 갖추게 됩니다.

#### Dynamic KG planning
**동적 KG 계획은 지식 그래프(KG)를 활용하여 동적으로 변화하는 환경에서 계획을 수립하는 방법론**입니다.  기존의 정적 계획은 환경 변화에 대한 적응력이 떨어지는 한계를 지니고 있으나, 동적 KG 계획은 **시간에 따른 변화를 반영하여** 계획을 지속적으로 업데이트함으로써 이러한 한계를 극복합니다.  **실시간으로 환경 정보를 수집하고 KG에 반영**하여, 에이전트는 최신 정보를 바탕으로 의사결정을 내리고 계획을 조정할 수 있습니다. 이는 특히 예측 불가능한 상황이나 장기간 계획이 필요한 경우에 유용합니다.  **계획의 유연성과 적응력을 높여** 에이전트가 복잡하고 역동적인 환경에서도 효과적으로 작동할 수 있도록 지원하는 핵심 기술입니다.  하지만 **KG의 크기와 복잡도가 증가**함에 따라 계산 비용이 증가하고, **계획 수립 시간이 늘어나는 문제점**도 존재합니다. 따라서 **효율적인 KG 관리 및 계획 알고리즘** 개발이 중요하며, 실제 구현에서는 이러한 trade-off를 고려해야 합니다.

#### Planner-critic model
본 논문에서 제안하는 **플래너-크리틱 모델**은 장기적이고 복잡한 임무를 수행하는 에이전트의 의사결정 능력을 향상시키기 위해 고안되었습니다.  **플래너**는 **공간-시간 메모리 모듈**에서 추출된 정보를 바탕으로 다단계 계획을 생성하는 역할을 합니다. 이는 단순히 다음 단계의 행동만을 예측하는 것이 아니라, 여러 단계에 걸친 계획을 수립하여 환경 변화에 대한 적응력을 높입니다.  **크리틱**은 플래너가 생성한 계획을 평가하고, 필요에 따라 계획을 수정하거나 새로운 계획을 생성하도록 유도합니다. 이러한 **닫힌 고리(closed-loop)** 방식은 에이전트가 **실시간 피드백**을 통해 계획을 지속적으로 개선하고, 예측하지 못한 상황에도 유연하게 대처할 수 있도록 합니다. 특히, **공간-시간 메모리**와의 통합은 에이전트가 과거 경험과 환경 정보를 효과적으로 활용하여 **장기적 계획 수립** 및 **실행**을 가능하게 합니다. 이는 기존의 단순한 기억 메커니즘을 넘어,  **동적이고 적응적인 의사결정**을 가능하게 하는 핵심 요소입니다.

#### TextWorld Evaluation
본 논문에서 제시된 STMA 에이전트의 성능을 평가하기 위해 TextWorld 환경을 사용한 실험 결과에 대한 심층적인 분석이 필요합니다. TextWorld는 다양한 복잡도의 요리 과제를 제공하는 부분 관찰 가능한 다중 작업 환경이기 때문에, **장기적인 계획 능력과 적응력**을 평가하기에 적합합니다. 성공률과 평균 점수를 주요 지표로 하여 STMA의 성능을 최첨단 모델과 비교 분석해야 합니다. 특히, 다양한 난이도 수준에서의 성능 차이를 분석하여 STMA의 강점과 약점을 파악하고, **공간-시간 메모리 모듈과 계획-비평 메커니즘의 효과**를 정량적으로 평가해야 합니다.  **실험 결과는 STMA가 기존 모델보다 성공률과 평균 점수에서 상당한 향상을 보였다는 것을 보여주어야** 합니다. 단순한 성능 비교를 넘어, STMA의 각 구성 요소 (공간 메모리, 시간 메모리, 계획-비평 메커니즘)가 성능 향상에 어떤 영향을 미쳤는지 분석하는 **추가적인 실험**도 필요합니다.  **에이전트의 계획 및 실행 과정을 자세히 분석**하여 STMA의 강점과 개선점을 도출하고,  **실제 로봇 시스템에 적용 가능성**을 논의해야 합니다.  마지막으로, **TextWorld 환경의 한계점과 STMA의 일반화 가능성**에 대한 논의를 통해 향후 연구 방향을 제시할 필요가 있습니다.

#### Ablation Study
본 논문의 절제 연구는 **STMA의 각 구성 요소의 중요성을 밝히는 데 중점을 둡니다.**  구체적으로, 공간-시간 기억 모듈, 요약기, 관계 집계기, 그리고 평론가의 제거 실험을 통해 각 구성 요소가 STMA의 전반적인 성능에 미치는 영향을 정량적으로 분석합니다.  **각 구성 요소의 제거는 상당한 성능 저하로 이어졌으며**, 특히 공간-시간 기억 모듈의 제거는 작업 성공률을 0%로 떨어뜨렸습니다. 이는 **장기간 계획과 동적 환경 적응에 있어서 공간-시간 기억 모듈의 필수적인 역할을 강조합니다.**  요약기와 관계 집계기의 제거는 특히 복잡한 작업에서 상당한 성능 저하를 야기했는데, 이는 **이러한 구성 요소들이 정보 처리 효율성과 공간 추론 능력을 향상시키는 데 중요한 역할**을 함을 시사합니다.  마지막으로, 평론가의 제거 실험은 **계획의 정확성과 적응성에 있어서 평론가의 중요성**을 보여주었습니다.  **전반적으로, 절제 연구는 STMA의 각 구성 요소들의 상호 작용과 중요성을 강조하며**, 이 모델의 설계 원칙과 강점을 더욱 명확히 이해하는 데 기여합니다. 이 연구는 **미래의 임베디드 인텔리전스 시스템 설계에 대한 중요한 시사점**을 제공합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.10177/extracted/6203426/img/main.jpg)

> 🔼 그림 2는 STMA의 개요를 보여줍니다. STMA는 공간-시간 기억 모듈과 계획-비평가 모듈의 두 가지 구성 요소로 구성됩니다. 공간-시간 기억 모듈은 시간 기억 하위 모듈과 공간 기억 하위 모듈로 나뉘며, 각각 시간적 신념과 공간적 신념을 제공합니다. 이러한 신념들은 계획-비평가 모듈에 대한 공간-시간적 맥락으로 작용합니다. 계획-비평가 모듈은 계획자와 비평가로 구성됩니다. 계획자는 신념에 따라 작업 계획을 수행하고 한 번에 여러 단계의 계획을 생성합니다. 비평가는 각 행동 단계 전에 계획을 평가하여 계획이 올바른지 그리고 현재 환경 조건과 일치하는지 확인합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Overview of STMA. STMA consists of two components: a spatio-temporal memory module and a planner-critic module. The spatio-temporal memory module is divided into a temporal memory submodule and a spatial memory submodule, which provide temporal and spatial beliefs, respectively. These beliefs serve as the spatio-temporal context for the planner-critic module. The planner-critic module consists of a planner and a critic. The planner performs action planning based on the belief and generates multi-step plans in a single pass. The critic evaluates the plan before each action step, verifying whether the plan is correct and aligns with the most current environmental conditions.
> </details>



![](https://arxiv.org/html/2502.10177/extracted/6203426/img/STMA_pro.jpg)

> 🔼 그림 3은 Textworld 환경과 에이전트 간의 상호작용을 보여줍니다. Textworld 환경은 에이전트에게 현재 관측치, 인벤토리, 그리고 가능한 행동 목록을 제공합니다. 에이전트가 행동을 수행하면 환경은 피드백을 제공합니다. 이러한 정보들은 STMA의 시공간 메모리에 기록되어 계획자-비평가 에이전트에게 필요한 정보를 제공합니다. 계획자와 비평가는 협력하여 행동 계획을 생성하고 환경과 상호 작용합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Interaction with the Textworld Environment. The interaction pattern between Textworld and our framework involves the environment providing the agent with the current observation, inventory, and a list of possible actions. Based on the agent’s executed actions, the environment returns feedback. These pieces of information are recorded in STMA’s spatio-temporal memory, serving as the necessary context for the planner-critic agent. Within this framework, the planner and critic collaborate to generate action plans and interact with the environment.
> </details>



![](https://arxiv.org/html/2502.10177/extracted/6203426/img/score_curve.png)

> 🔼 그림 4는 GPT-40을 사용하여 네 가지 다른 강화학습 프레임워크(ReAct, Reflexion, AdaPlanner, STMA)의 성능을 비교한 그래프입니다. 가로축은 에이전트가 작업을 완료하는 데 걸린 단계 수를 나타내고, 세로축은 평균 점수를 나타냅니다. 각 프레임워크는 네 가지 난이도의 요리 과제에 대해 평가되었으며, 그래프는 각 난이도별로 프레임워크의 평균 점수와 단계 수의 관계를 보여줍니다. 이를 통해 각 프레임워크의 효율성과 복잡한 작업에 대한 적응력을 비교 분석할 수 있습니다. STMA는 다른 프레임워크에 비해 더 높은 평균 점수를 달성하였고, 특히 복잡한 작업에서 더욱 효율적으로 작업을 수행함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Average score vs. steps of different frameworks (powered by GPT-4o)
> </details>



![](https://arxiv.org/html/2502.10177/extracted/6203426/img/1_1.jpg)

> 🔼 그림 5는 본 논문의 실험 환경 중 하나인 TextWorld 환경에서 요리 과제를 수행하는 STMA와 Reflexion 에이전트의 비교 결과를 보여줍니다.  Reflexion은 장기 기억 및 자기 반성 모듈을 사용하지만, STMA는 공간-시간 기억 모듈과 계획가-비평가 모듈을 통합하여 더욱 향상된 성능을 보입니다. 그림은 Reflexion 에이전트가 잘못된 조리 도구를 사용하여 과제를 실패한 반면, STMA 에이전트는 계획가-비평가 모듈의 상호 작용을 통해 오류를 수정하고 과제를 성공적으로 완료했음을 시각적으로 보여줍니다. 특히, STMA의 계획가가 처음에 잘못된 행동을 생성했지만, 비평가 모듈이 이를 감지하고 수정함으로써  STMA가 역동적인 환경에서도 강건한 의사결정 능력을 갖추고 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: STMA versus Reflexion in Case 1.
> </details>



![](https://arxiv.org/html/2502.10177/extracted/6203426/img/2_8.jpg)

> 🔼 그림 6은 본 논문의 5.2절 실험 결과 중 Case 2에 대한 비교 분석 결과를 보여줍니다.  Reflexion 모델과 STMA 모델의 성능을 비교하는데 초점을 맞추고 있습니다.  두 모델 모두 Textworld 환경에서 요리 레시피를 완료하는 작업을 수행하지만, Reflexion 모델은 공간적 기억 능력의 부족으로 잘못된 경로를 선택하는 반면, STMA 모델은 공간적 기억과 계획-비평 구조를 통해 최적 경로를 선택하고, 계획 과정에서 발생하는 오류를 비평 모듈을 통해 수정하여 최종적으로 레시피 완료에 성공하는 모습을 보여줍니다.  STMA의 공간 기억 및 계획-비평 메커니즘의 효과를 강조하고 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: STMA versus Reflexion in Case 2.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Difficulty Level | 1 |  | 2 |  | 3 |  | 4 |  |
|---|---|---|---|---|---|---|---|---|---| 
| STMA w/o Spatio-Temporal Memory | 0.0 | 0.0 ± 0.0 | 0.0 | 0.0 ± 0.0 | 0.0 | 0.0 ± 0.0 | 0.0 | 0.0 ± 0.0 |
| STMA w/o Summarizer | 87.5 | 87.5 ± 33.1 | 100.0 | 100.0 ± 0.0 | 25.0 | 55.0 ± 32.8 | 12.5 | 49.0 ± 28.5 |
| STMA w/o Summarizer for Spatial Memory | 100.0 | 100.0 ± 0.0 | 50.0 | 65.0 ± 40.6 | 12.5 | 37.5 ± 31.9 | 12.5 | 37.5 ± 35.1 |
| STMA w/o Spatial Memory | 87.5 | 93.8 ± 16.5 | 75.0 | 91.1 ± 15.9 | 50.0 | 65.0 ± 40.6 | 12.5 | 30.8 ± 28.0 |
| STMA w/o Relation Aggregator | 100.0 | 100.0 ± 0.0 | 87.5 | 96.4 ± 9.4 | 62.5 | 71.2 ± 37.2 | 25.0 | 51.0 ± 34.8 |
| STMA w/o Critic | 100.0 | 100.0 ± 0.0 | 75.0 | 85.7 ± 25.8 | 50.0 | 70.0 ± 33.5 | 0.0 | 26.0 ± 31.0 |
| **STMA** | **100.0** | **100.0 ± 0.0** | **100.0** | **100.0 ± 0.0** | **62.5** | **81.2 ± 27.6** | **25.0** | **58.7 ± 30.3** |{{< /table-caption >}}
> 🔼 표 2는 STMA의 성능에 대한 ablation study 결과를 보여줍니다. 각 모듈 (Spatio-Temporal Memory, Summarizer, Spatial Memory, Relation Aggregator, Critic)을 제거했을 때 네 가지 난이도 레벨에서 성공률(SR)과 평균 점수(AS)가 어떻게 변하는지 보여줍니다.  평균 점수는 표준 편차(σ)와 함께 제시됩니다. 이 표는 각 모듈의 STMA 성능에 대한 기여도를 정량적으로 비교 분석하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Ablation studies of the STMA. Success Rate (SR) and Average Score (AS) (A⁢S±σplus-or-minus𝐴𝑆𝜎AS\pm\sigmaitalic_A italic_S ± italic_σ) across four difficulty levels for model variants with individual modules are removed.
> </details>

{{< table-caption >}}
| Level | Rooms | Ingredients to Find | Steps in Recipe | Ingredients in Recipe | Total Score |
|---|---|---|---|---|---| 
| 1 | 6 | 0 | 4 | 1 | 4 |
| 2 | 9 | 1 | 6 | 2 | 7 |
| 3 | 9 | 2 | 8 | 3 | 10 |
| 4 | 12 | 3 | 10 | 4 | 13 |

| Scoring Points |  | Task Failures |  |
|---|---|---|---|
| Collecting specified ingredients |  | Using an incorrect cooking appliance |  |
| Processing ingredients with correct cooker |  | Incorrect processing technique (cut, dice, slice) |  |
| Handling ingredients properly (cut, dice, slice) |  | Repeating heat-based cooking steps causes burning |  |
| Executing final steps (e.g., "prepare meal") |  | Exceeding 50 turns without task completion |  |{{< /table-caption >}}
> 🔼 표 3은 TextWorld 환경에서 수행된 요리 작업의 난이도 설정, 채점 기준 및 실패 사유를 보여줍니다.  난이도 레벨(1~4)에 따라 방의 수, 찾아야 할 재료의 수, 레시피 단계 수 등이 증가합니다.  각 레벨의 점수는 재료 수집, 올바른 조리 기구 사용, 적절한 재료 처리, 최종 요리 완성 등에 따라 부여됩니다. 실패 사유는 잘못된 조리 기구 또는 방법 사용, 재료 태우기, 시간 초과 등으로 정의됩니다. 이 표는 실험 설정의 세부 사항을 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Task Difficulty Settings, Scoring Points, and Task Failures
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