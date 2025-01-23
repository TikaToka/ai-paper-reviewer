---
title: "Mobile-Agent-E: Self-Evolving Mobile Assistant for Complex Tasks"
summary: "Mobile-Agent-E는 자체 진화 모듈을 갖춘 계층적 다중 에이전트 프레임워크로, 복잡한 실제 모바일 작업에서 뛰어난 성능을 보입니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Human-AI Interaction", "🏢 University of Illinois Urbana-Champaign",]
showSummary: true
date: 2025-01-20
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.11733 {{< /keyword >}}
{{< keyword icon="writer" >}} Zhenhailong Wang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-22 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.11733" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.11733" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/mobile-agent-e-self-evolving-mobile-assistant" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

현대 모바일 환경에서 복잡한 다단계 작업을 수행하는 것은 어렵습니다. 기존 모바일 에이전트는 **장기적인 계획, 다중 앱 상호 작용, 과거 경험 학습** 등의 어려움을 겪습니다. 이러한 문제를 해결하기 위해 많은 연구가 진행되었지만, 여전히 실제 사용자의 요구를 충족하는 데는 한계가 있습니다.

본 논문에서는 이러한 문제점들을 해결하기 위해 새로운 모바일 에이전트 프레임워크인 Mobile-Agent-E를 제시합니다. Mobile-Agent-E는 **계층적 다중 에이전트 아키텍처와 자체 진화 모듈**을 통해 고차원 계획과 저차원 행동 실행을 분리하고, 과거 경험으로부터 학습하여 성능과 효율성을 높입니다. 실험 결과, Mobile-Agent-E는 기존 최첨단 방식보다 **성능이 22% 향상**되었으며, 자체 진화 모듈은 추가적인 성능 향상을 가져왔습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} Mobile-Agent-E는 복잡한 실제 모바일 작업을 위한 새로운 벤치마크 Mobile-Eval-E를 제시합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} Mobile-Agent-E는 계층적 다중 에이전트 아키텍처와 자체 진화 모듈을 통해 성능을 향상시켰습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} Mobile-Agent-E는 기존 최첨단 모델보다 우수한 성능을 보이며 모바일 에이전트 연구의 새로운 방향을 제시합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **복잡한 실제 환경의 모바일 작업에 대한 새로운 벤치마크인 Mobile-Eval-E**를 제시하고, 기존의 모바일 에이전트 접근 방식의 한계를 극복하는 새로운 모바일 에이전트 프레임워크인 **Mobile-Agent-E**를 소개합니다. Mobile-Agent-E는 계층적 다중 에이전트 아키텍처와 자체 진화 모듈을 통해 장기적인 계획, 의사결정 정확도, 그리고 에러 복구 능력을 향상시켰습니다. 또한, Mobile-Agent-E는 **실험을 통해 기존 최첨단 모델보다 성능이 크게 향상됨**을 보여주며, **모바일 에이전트 연구에 새로운 방향**을 제시합니다. 이 연구는 모바일 에이전트 분야의 발전에 기여하며, **향후 연구를 위한 새로운 가능성**을 열어줍니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.11733/x2.png)

> 🔼 그림 1은 복잡한 실제 세계 작업에서 이전 최첨단 방식(Zhang et al., 2023; Wang et al., 2024b, a)보다 성능이 뛰어난 새로운 계층적 다중 에이전트 모바일 어시스턴트인 Mobile-Agent-E를 제안합니다. Mobile-Agent-E는 전용 에이전트를 사용하여 고급 계획 및 저급 작업 결정을 분리합니다. 새롭게 도입된 자기 진화 모듈을 통해 과거 경험에서 일반적인 팁과 재사용 가능한 바로 가기를 학습하는 Mobile-Agent-E는 성능과 효율성 모두 향상됨을 보여줍니다.  Mobile-Agent-E는 관리자 에이전트, 인지 에이전트, 운영 에이전트, 행동 반영 에이전트, 필기 에이전트의 다섯 가지 에이전트로 구성됩니다.  계층적 구조를 통해 각 에이전트는 특정 역할을 수행하며,  자기 진화 모듈은 장기 기억에 팁과 바로 가기를 저장하고 이를 통해 지속적인 성능 향상을 이룹니다. 그림에는 Mobile-Agent-E의 아키텍처와 다양한 작업 예시, 그리고 기존 최첨단 방식과의 성능 비교 결과가 시각적으로 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: We propose Mobile-Agent-E, a novel hierarchical multi-agent mobile assistant that outperforms previous state-of-the-art approaches (Zhang et al., 2023; Wang et al., 2024b, a) on complex real-world tasks. Mobile-Agent-E disentangles high-level planning and low-level action decision with dedicated agents. Equipped with a newly introduced self-evolution module that learns general Tips and reusable Shortcuts from past experiences, Mobile-Agent-E demonstrates further improvements in both performance and efficiency.
> </details>





{{< table-caption >}}
| Notation | Description |
|---|---| 
| *Environment* ||
|  $I$ | Input task query |
| $a^{t}$ | Action at time $t$ † <br> † $a_{t}$ can represent either a single atomic operation or a sequence of atomic operations if performing a Shortcut. |
| $s^{t}$ | Phone state (screenshot) at time $t$ |
| *Agents* ||
| $
mathcal{A}_{P}
$ | Perceptor |
| $
mathcal{A}_{M}
$ | Manager |
| $
mathcal{A}_{O}
$ | Operator |
| $
mathcal{A}_{R}
$ | Action Reflector |
| $
mathcal{A}_{N}
$ | Notetaker |
| $
mathcal{A}_{ES}
$ | Experience Reflector for Shortcuts |
| $
mathcal{A}_{ET}
$ | Experience Reflector for Tips |
| *Working Memory* ||
| $W_{V}^{t}$ | Visual perception result at time $t$ |
| $W_{P}^{t}$ | Overall plan (decomposed subgoals) at time $t$ |
| $W_{S}^{t}$ | Current subgoal at time $t$ |
| $W_{G}^{t}$ | Progress status at time $t$ |
| $W_{N}^{t}$ | Important notes at time $t$ |
| $W_{EF}^{t}$ | Error Escalation Flag at time $t$ |
| $
mathbf{W_{A}}
$ | Action history with outcome status |
| $
mathbf{W_{E}}
$ | Error history with feedback |
| *Long-term Memory* ||
| $L_{S}$ | Shortcuts |
| $L_{T}$ | Tips |{{< /table-caption >}}

> 🔼 표 1은 논문의 2장 Mobile-Agent-E 섹션에서 사용된 표기법에 대한 정의를 담고 있습니다.  환경, 에이전트, 작업 메모리, 장기 메모리 등 다양한 구성요소와 변수들에 대한 약어 및 설명을 제공하여 논문의 내용 이해를 돕습니다.  각 약어는 해당하는 구성요소나 변수를 나타내는 기호이며,  설명에는 그 의미와 기능이 간략하게 요약되어 있습니다. 이 표는 논문의 후속 섹션에서 사용되는 다양한 변수와 에이전트의 역할을 이해하는 데 필수적인 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Notation definitions.
> </details>





### In-depth insights


#### Mobile Agent E
Mobile Agent E는 복잡한 모바일 작업을 위한 자가 진화형 개인 비서 시스템으로, **계층적 다중 에이전트 구조**와 **자가 학습 메커니즘**을 통해 기존 모바일 에이전트의 한계를 극복합니다.  **계층적 구조**는 고차원 계획과 저차원 행동 실행을 분리하여 효율성을 높이고, **자가 진화 모듈**은 과거 경험으로부터 유용한 정보를 학습하여 성능과 효율성을 향상시킵니다.  **장기 기억 메커니즘**을 통해 Tips와 Shortcuts을 관리하여 반복적인 작업을 효율화하고, Mobile-Eval-E라는 새로운 벤치마크를 통해 실제 사용 환경에 가까운 복잡한 작업을 평가합니다.  결과적으로 기존 시스템보다 성능이 크게 향상되었으며, 특히 **자가 학습 기능**의 효과가 뚜렷하게 나타났습니다.  **실제 모바일 환경에서의 동적 평가**를 통해 실용성을 검증하였으며, 추후 개선 방향으로는 에이전트의 안정성과 개인화된 경험 제공에 대한 연구가 제시됩니다.

#### Hierarchical Framework
본 논문에서 제시된 계층적 프레임워크는 **복잡한 모바일 작업을 효율적으로 처리**하기 위해 고안되었습니다.  **상위 수준의 계획(high-level planning)**을 담당하는 관리자 에이전트와 **저수준의 행동 실행(low-level action execution)**을 담당하는 하위 에이전트들로 구성되어, **작업의 분할 및 위임**을 통해 효율성을 극대화합니다.  **계층적인 구조**는 상위 에이전트가 하위 에이전트의 결과를 바탕으로 계획을 세밀하게 조정하고, 하위 에이전트는 상위 에이전트의 지시에 따라 세부적인 작업을 수행하는 **협력적인 시스템**을 가능하게 합니다. 이를 통해 **장기간의 추론(long-horizon reasoning)**과 **다중 앱 상호작용(multi-app interaction)**이 필요한 복잡한 작업에서도 **정확성과 효율성**을 높일 수 있습니다.  **자기 진화 모듈**과의 결합은 과거 경험을 바탕으로 **지속적인 성능 개선**을 가능하게 하여, **더욱 유연하고 효과적인 모바일 어시스턴트** 개발에 기여할 것으로 예상됩니다.

#### Self-Evolution Module
본 논문에서 제시된 자기 진화 모듈은 **에이전트의 지속적인 성능 향상**을 위한 핵심 메커니즘입니다. 이 모듈은 과거 경험으로부터 **팁(Tips)** 과 **바로가기(Shortcuts)** 를 학습하고 장기 메모리에 저장합니다. 팁은 일반적인 가이드라인과 이전 작업에서 얻은 교훈을 담고 있으며, 바로가기는 특정 하위 루틴을 위한 재사용 가능한 원자적 작업의 순서를 나타냅니다.  **에이전트는 각 작업 후 이러한 팁과 바로가기를 업데이트**하여 지속적으로 개선됩니다.  이를 통해 에이전트는 반복적인 작업을 효율적으로 처리하고 새로운 작업에도 빠르게 적응할 수 있습니다.  **계층적 구조**를 통해 고차원 계획과 저차원 행동 실행을 분리하여 오류 복구 능력도 향상시킵니다.  **장기 메모리**는 팁과 바로가기를 지속적으로 관리하며, 이는 인간의 경험적 학습 방식을 모방한 것입니다.  **자기 진화 모듈은 에이전트의 효율성과 성능을 향상**시키는 핵심 요소이며, 실제 환경에서의 복잡한 작업 수행에 중요한 역할을 합니다.

#### MobileEval-E Benchmark
MobileEval-E 벤치마크는 기존 모바일 에이전트 평가의 한계를 극복하고자 **실제 사용자의 복잡한 요구사항을 반영한 실용적인 과제들을 포함**하도록 설계되었습니다.  단순하고 짧은 작업이 아닌, **여러 앱을 오가며 장시간에 걸쳐 추론과 계획을 필요로 하는 복잡한 시나리오**를 다루는 것이 특징입니다. 이를 통해 기존 벤치마크에서는 평가하기 어려웠던 **장기적 추론, 다중 앱 상호작용, 탐색적 행동** 등 실제 모바일 환경의 어려움을 더욱 정확하게 반영합니다.  **만족도 점수(Satisfaction Score)** 라는 새로운 평가 지표를 도입하여 단순한 성공/실패 여부를 넘어 사용자 경험까지 고려한 종합적인 평가를 가능하게 합니다.  **다양한 기초 모델과의 호환성**을 고려하여 개발되었으며,  향후 모바일 에이전트 연구의 발전에 중요한 기여를 할 것으로 기대됩니다.  특히 **자체 진화 모듈(self-evolution module)의 성능 평가**에도 적합하며,  **실용성과 난이도 측면에서 균형**을 이룬 벤치마크로써 모바일 에이전트 분야의 발전에 중요한 역할을 할 것으로 예상됩니다.

#### Future Work
본 논문은 모바일 환경에서 복잡한 작업을 수행하는 데 있어서 **계층적 다중 에이전트 프레임워크와 자기 진화 모듈**을 활용한 모바일 어시스턴트 Mobile-Agent-E를 제시합니다.  향후 연구 방향으로는 **숏컷(Shortcuts)의 오용 방지 및 에러 수정**, **개인 맞춤형 개선**, **안전성 강화** 등이 제시될 수 있습니다.  특히 숏컷의 경우, 사전 조건을 충족하는지 확인하는 메커니즘을 강화하고, 잘못 생성된 숏컷을 수정하는 기능을 추가하는 것이 중요합니다. 또한, 사용자의 선호도 및 사용 패턴을 학습하여 개인화된 서비스를 제공하는 방안을 고려해야 합니다. **사용자 데이터 보호 및 오용 방지**를 위한 안전장치 마련 또한 필수적입니다.  **에러 복구 기능**을 더욱 강화하고, 다양한 유형의 에러에 대한 대응 능력을 높이는 것도 중요한 과제입니다.  궁극적으로는 **사람과의 협업**을 강화하고, 사용자 피드백을 바탕으로 지속적인 학습 및 개선을 이루어나가는 것이 Mobile-Agent-E의 발전에 중요한 역할을 할 것입니다.


### More visual insights




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Benchmark | #Tasks | #Multi-AppTasks | #Apps | Avg #Ops | Total #Ops |
|---|---|---|---|---|---| 
| Mobile-Eval | 33 | 3 | 10 | 5.55 | 183 |
| Mobile-Eval-v2 | 44 | 4 | 10 | 5.57 | 245 |
| AppAgent | 45 | 0 | 9 | 6.31 | 284 |
| Mobile-Eval-E | 25 | 19 | 15 | 14.56 | 364 |{{< /table-caption >}}
> 🔼 이 표는 실제 모바일 기기에서 기존의 동적 평가 벤치마크와 Mobile-Eval-E를 비교한 것입니다. Mobile-Eval-E는 장기간에 걸친 복잡한 작업에 중점을 두고 있으며, 이는 상당히 많은 작업과 다양한 앱을 필요로 합니다.  기존 벤치마크는 단기간의 간단한 작업에 초점을 맞추는 반면, Mobile-Eval-E는 더욱 현실적인 사용 시나리오를 반영하여 다양한 앱을 조작하고 여러 단계를 거쳐야 하는 복잡한 작업을 포함합니다. 이를 통해 기존의 벤치마크보다 Mobile-Agent-E의 성능을 더욱 정확하게 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Comparison with existing dynamic evaluation benchmarks on real devices. Mobile-Eval-E emphasizes long-horizon, complex tasks that require significantly more operations and a wider variety of apps.
> </details>

{{< table-caption >}}
| #Multi-App | Tasks |
|---|---|{{< /table-caption >}}
> 🔼 표 3은 Mobile-Eval-E 벤치마크에서 GPT-40 백본을 사용하여 최첨단 모델과 Mobile-Agent-E의 성능을 비교한 표입니다. Mobile-Agent-E는 모든 지표에서 이전 SOTA 모델보다 훨씬 우수한 성능을 보여주며, 장기 계획, 의사 결정 정확도 및 오류 복구 능력이 뛰어남을 입증합니다. 자기 진화 기능을 활성화하면 (Mobile-Agent-E + Evo) 성능이 더욱 향상됩니다. AppAgent 및 Mobile-Agent-v1은 액션 리플렉터가 없으므로 반사 정확도는 생략되었습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Comparison with state-of-the-art models on the Mobile-Eval-E benchmark, using GPT-4o as the backbone. Mobile-Agent-E outperforms previous SOTA models by a significant margin across all metrics, demonstrating superior long-term planning, decision accuracy, and error recovery. Enabling self-evolution (Mobile-Agent-E + Evo) further enhances performance. Reflection Accuracy for AppAgent and Mobile-Agent-v1 are omitted since they do not have action reflectors.
> </details>

{{< table-caption >}}
| #Apps |
|---|{{< /table-caption >}}
> 🔼 표 4는 GPT-40, Gemini, Claude와 같은 다양한 대규모 다중 모드 모델 백본에서 Mobile-Agent-E의 성능을 보여줍니다.  SS(만족도 점수), AA(액션 정확도), RA(반성 정확도), TE(종료 오류)의 네 가지 지표가 백분율로 표시됩니다. 이 표는 다양한 기본 모델을 사용했을 때 Mobile-Agent-E의 성능 변화를 비교 분석하여, Mobile-Agent-E의 성능이 기본 모델의 선택에 따라 어떻게 달라지는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Results on different large multimodal model backbones, including GPT-4o, Gemini, and Claude. The metrics SS, AA, RA, and TE represent Satisfaction Score, Action Accuracy, Reflection Accuracy, and Termination Error, respectively, expressed as percentages.
> </details>

{{< table-caption >}}
| Avg # | Ops |
|---|---|{{< /table-caption >}}
> 🔼 표 5는 추론 과정의 연산 비용과 바로가기(Shortcut) 사용 현황을 분석한 결과를 보여줍니다. '추론 전용' 열은 추론 에이전트에 소요된 시간을, '인식 + 추론' 열은 CPU에서 수행된 인식 에이전트의 실행 시간을 포함합니다. 바로가기 사용 통계는 연산자에 의해 수행된 총 동작 수 대비 바로가기 사용 비율로 계산됩니다. 바로가기 사용은 추론 속도를 크게 향상시켜 이전의 단순한 프레임워크와 유사한 수준의 시간을 달성합니다.
> <details>
> <summary>read the caption</summary>
> Table 5:  Analysis of computational overhead and Shortcut usage. In the inference speed table, the reasoning only section accounts for time spent solely on reasoning agents, while perception + reasoning includes the runtime of the Perceptor on CPU. Shortcut usage statistics are calculated as the ratio of Shortcuts used to the total number of actions performed by the Operator. The use of Shortcuts significantly accelerates inference, achieving comparable times to previous, simpler frameworks.
> </details>

{{< table-caption >}}
| Total # | Ops |
|---|---|{{< /table-caption >}}
> 🔼 이 표는 Mobile-Agent-E의 성능 향상에 있어서 Tips의 고유한 영향을 조사하기 위해 작성되었습니다. 새로 생성된 Shortcuts가 경로에 사용되지 않은 인스턴스의 하위 집합에 대해 만족도 점수를 계산하여 Tips의 발전이 성능 향상에 얼마나 기여하는지 보여줍니다. 결과는 발전된 Tips가 성능 향상에 상당한 영향을 미친다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 6: To investigate the unique impact of Tips, we compute the Satisfaction Score on a subset of instances where no newly generated Shortcuts are used in the trajectory. The results show distinctive benefits from the evolved Tips.
> </details>

{{< table-caption >}}
| Model | Type | Satisfaction Score (%) ↑ | Action Accuracy (%) ↑ | Reflection Accuracy (%) ↑ | Termination Error (%) ↓ |
|---|---|---|---|---|---|
| AppAgent [2023] | Single-Agent | 25.2 | 60.7 | - | 96.0 |
| Mobile-Agent-v1 [2024b] | Single-Agent | 45.5 | 69.8 | - | 68.0 |
| Mobile-Agent-v2 [2024a] | Multi-Agent | 53.0 | 73.2 | 96.7 | 52.0 |
| Mobile-Agent-E | Multi-Agent | 75.1 | 85.9 | 97.4 | 32.0 |
| Mobile-Agent-E + Evo | Multi-Agent | **86.9** | **90.4** | **97.8** | **12.0** |{{< /table-caption >}}
> 🔼 표 7은 Mobile-Eval-E 벤치마크에 포함된 모든 작업 쿼리의 세부 정보를 보여줍니다. 각 행은 하나의 작업을 나타내며, 작업 ID, 관련 앱, 작업 쿼리, 시나리오(예: 레스토랑 추천, 정보 검색 등)를 포함합니다. 이 표는 논문에서 제시된 다양한 실제 시나리오를 기반으로 한 복잡하고 다단계적인 모바일 작업의 범위를 보여줍니다.  Mobile-Eval-E 벤치마크의 질문 목록을 전체적으로 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: All task queries in Mobile-Eval-E.
> </details>

{{< table-caption >}}
| Satisfaction Score | (%) ↑ |
|---|---|{{< /table-caption >}}
> 🔼 표 8은 Mobile-Agent-E 시스템에서 사용되는 기본적인 동작들을 보여줍니다.  각 동작의 이름과 간략한 설명을 통해 에이전트가 모바일 환경에서 어떤 작업들을 수행할 수 있는지 보여줍니다.  예를 들어, Open_App은 특정 앱을 여는 동작이고, Tap은 특정 좌표를 터치하는 동작입니다. 이 표는 Mobile-Agent-E의 작동 방식을 이해하는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Atomic operations space.
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