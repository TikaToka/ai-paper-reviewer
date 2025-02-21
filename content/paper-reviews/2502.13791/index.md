---
title: "From Tools to Teammates: Evaluating LLMs in Multi-Session Coding Interactions"
summary: "LLM의 장기 상호작용 협업능력 평가 위한 MEMORYCODE 벤치마크 제시: 단기 과제 해결은 우수하나 장기적 상호작용에선 성능 저하, 정보 검색 및 통합의 어려움을 보여줌."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Universitat Pompeu Fabra",]
showSummary: true
date: 2025-02-19
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.13791 {{< /keyword >}}
{{< keyword icon="writer" >}} Nathanaël Carraz Rakotonirina et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-20 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.13791" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.13791" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/from-tools-to-teammates-evaluating-llms-in" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

현재 대규모 언어 모델(LLM)은 개별적인 문제 해결에는 뛰어나지만, **장기간에 걸친 상호작용을 통한 협업에는 어려움**을 겪습니다. 기존 연구는 주로 LLM의 단일 작업 수행 능력 향상에 초점을 맞춰왔지만, 실제 업무 환경에서는 여러 세션에 걸쳐 지속적인 상호작용이 필요합니다. 이러한 **현실적인 제약을 반영하지 못한 기존 연구의 한계**를 극복하고자, 본 논문에서는 다중 세션 코딩 상호작용을 시뮬레이션한 MEMORYCODE라는 합성 데이터셋을 도입했습니다.



MEMORYCODE는 **무관한 정보 속에서 단순한 코딩 지침을 추적하고 실행**하는 LLM의 능력을 평가하도록 설계되었습니다.  **다양한 모델에 대한 실험 결과**, LLM은 개별 지침에는 잘 대처하지만, 지침이 여러 세션에 걸쳐 분산될 경우 성능이 저하됨을 보였습니다. 이는 **정보 검색 및 통합의 어려움** 때문으로 분석되었으며, 이는 현존 LLM의 근본적인 한계를 드러냅니다. 따라서 본 연구는 **장기 기억 및 추론 능력 향상**을 위한 새로운 연구 방향을 제시합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} MEMORYCODE라는 새로운 벤치마크를 사용하여 LLM의 장기 상호작용 협업 능력을 평가했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} LLM은 단기적인 과제에서는 좋은 성능을 보이지만, 장기적인 상호작용에서는 정보 검색 및 통합에 어려움을 겪어 성능이 저하됨을 발견했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 본 연구는 LLM의 장기 기억 및 전향적 기억 메커니즘 개선이 필요함을 시사하며, 향후 연구의 중요한 방향을 제시합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **장기간에 걸친 상호작용에서의 대규모 언어 모델(LLM)의 협업 능력**을 평가하기 위한 새로운 벤치마크인 MEMORYCODE를 제시함으로써, 현재 LLM의 기본적인 한계를 강조하고 향후 연구 방향을 제시합니다.  **다양한 규모의 모델들에 대한 실험 결과**는 LLM이 장기적인 상호작용에서 정보를 효과적으로 검색하고 통합하는 데 어려움을 겪는다는 것을 보여줍니다. 따라서 본 연구는 **장기 기억 및 전향적 기억 메커니즘 개선**과 같은 LLM의 향후 발전 방향에 대한 중요한 시사점을 제공합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.13791/extracted/6216628/figs/intro_llm_colleagues_img.png)

> 🔼 그림 1은 인간과 LLM 기반의 ‘팀 동료’ 간의 장기적인 상호 작용을 단순화하여 보여주는 예시입니다. 그림에서 각각의 날짜는 하나의 세션을 나타냅니다. LLM 팀 동료는 1일차 세션에서 학습한 정보(빨간색)를 기억하여 20일차 과제를 올바르게 수행해야 하며, 동시에 5일차에 무관한 정보(파란색)도 받아들여야 합니다. 이 그림은 LLM이 장기적인 상호 작용에서 정보를 유지하고 통합하는 능력을 평가하기 위한 MEMORYCODE 데이터셋의 개념을 보여줍니다.  LLM이 단순히 지시를 따르는 것이 아니라, 과거의 정보를 활용하여 장기적인 맥락 속에서 과제를 해결해야 하는 상황을 시뮬레이션합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: A simplified but realistic example of a long-term interaction between a human and an LLM-based ‘teammate’. In this example, each day represents a single session. The LLM teammate must remember a piece of information—in red—learned during the session on Day 1 to correctly perform a task on Day 20, while also receiving irrelevant information—in blue—on Day 5.
> </details>





{{< table-caption >}}
| Parameter | Range |
|---|---| 
| Sessions (n) | {1,2,3,4,5,10,15, 20,30,40,50,100} |
| Sessions with instr. (%) | [50,70] |
| Instr. in a session (n) | {1,2,3} |
| Instr. updates (%) | [30,70] |
| Filler updates (%) | [50,70] |{{< /table-caption >}}

> 🔼 이 표는 대화 기록 생성에 사용된 매개변수들을 보여줍니다. 각 매개변수는 몇 개의 세션을 포함할지, 각 세션에 몇 개의 지시사항이 있을지, 지시사항 업데이트 및 필러 업데이트 비율 등을 포함하여 대화 기록 생성 과정에 대한 상세한 정보를 제공합니다. 이를 통해, 인공지능 모델의 다양한 성능을 평가하기 위해 생성된 데이터셋의 다양성과 복잡성을 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Parameters for dialogue history generation.
> </details>





### In-depth insights


#### LLM Collaboration
LLM 협업에 대한 심층적인 논의는 **대규모 언어 모델(LLM)이 장기적인 상호 작용을 통해 효과적으로 협업할 수 있는지** 여부를 탐구하는 데 초점을 맞춰야 합니다.  단순히 개별 문제 해결 능력을 넘어, **장기간에 걸친 상호 작용 속에서 정보를 효과적으로 검색하고 통합하는 능력**이 중요합니다. 이는 LLM의 근본적인 한계를 드러내는 것으로, **장기간의 지시 사항들을 추적하고 실행하는 능력 부족**이 협업 능력을 저해할 수 있음을 시사합니다. 따라서 **향후 연구는 LLM의 장기 기억 및 전향적 기억 능력 향상**, **정보 통합 메커니즘 개발**, **대화 기록으로부터 관련 정보를 자발적으로 검색하는 능력 개선** 등에 집중해야 합니다.  **합성 데이터셋을 활용한 평가**는 이러한 능력 향상을 위한 중요한 도구가 될 것입니다.  **실제 협업 환경을 모방한 합성 데이터셋의 개발**은 LLM의 협업 능력 향상에 대한 연구를 가속화할 것입니다.

#### MemoryCode Dataset
MemoryCode 데이터셋은 **장기간에 걸친 다중 세션 코딩 상호작용에서의 LLM 성능 평가**를 위해 고안된 합성 데이터셋입니다.  **단순한 코딩 지침들을 무관한 정보들 사이에 삽입**하여 현실적인 환경을 모방하며, **장기간에 걸친 상호작용에서의 정보 검색 및 통합 능력**을 평가하는 데 초점을 맞춥니다.  데이터셋은 다양한 코딩 관례 및 규칙들을 포함하며, **모델이 이러한 규칙들을 기억하고 적용하는 능력**을 평가합니다.  **단일 세션 내의 지침 처리는 우수하지만, 세션 간 지침이 분산될 경우 성능이 저하되는 현상**을 보이는 현대 LLM의 한계를 강조합니다.  이러한 한계는 **장기적인 기억 및 정보 통합 능력 부족**으로 인한 것으로 분석되며, 향후 LLM 연구 개발 방향에 시사하는 바가 큽니다.  **단순한 코딩 작업을 통해 정보 검색 능력과 다른 복잡한 기술들을 분리**하여 평가의 정확성을 높인 점도 주목할 만합니다.

#### Multi-Session Eval
다중 세션 평가는 **장기간에 걸친 상호작용에서의 언어 모델 성능을 평가하는 데 중점**을 둡니다. 이는 단일 질문응답 시나리오를 넘어서, 사용자와의 반복적인 대화를 통해 지속적인 학습 및 적응 능력을 평가합니다. 이러한 평가는 **일상적인 작업 환경의 현실적인 측면**을 반영하며, 모델이 과거 상호 작용에서 얻은 정보를 활용하여 새로운 과제에 대처하는 능력을 평가합니다.  단순히 지식을 기억하는 것 이상으로, **정보의 통합 및 적용 능력**,  **맥락에 맞는 적응력**, 그리고 **장기 기억 및 회상 능력**을 측정하는 것이 중요합니다.  따라서 다중 세션 평가는 모델의 단순한 지식 암기 능력이 아닌 **진정한 이해와 지능**을 측정하는 척도로서 그 중요성이 커지고 있습니다.  **실제 응용 분야와의 높은 연관성** 또한 다중 세션 평가의 중요한 강점이며, 이를 통해 개발된 모델의 실용성과 유용성을 보다 효과적으로 검증할 수 있습니다.

#### Instruction Following
본 논문에서 '지시사항 따르기'는 **대규모 언어 모델(LLM)**의 핵심 능력 중 하나로 제시됩니다.  단순히 주어진 명령어를 수행하는 것을 넘어, **장기간에 걸친 다중 세션 상호작용** 속에서도 일관되게 지시사항을 따르는 능력을 평가합니다. 이는 **실제 협업 환경**을 모사하여, 단일 지시사항 처리를 넘어 지속적인 소통과 정보 통합 능력을 검증하는 데 초점을 맞춥니다. 특히, **관련 없는 정보들 사이에서 핵심 정보를 추출하고, 지시사항이 업데이트 될 때 이를 적절히 반영하는 능력**이 중요하게 다뤄집니다.  연구 결과는 최첨단 모델들조차 장기간에 걸친 지시사항 연속 처리에 어려움을 겪는다는 점을 보여주며, **단순한 모델 확장을 넘어, 장기 기억 및 정보 통합 메커니즘 개선**의 필요성을 강조합니다.  **기억력과 추론 능력의 한계**를 극복하는 것이 LLM의 실제 업무 적용 가능성을 높이는 데 중요한 과제임을 시사합니다.

#### Future of LLMs
LLM의 미래는 **매우 유망하지만 동시에 도전적**입니다.  향후 연구는 **장기간 상호작용 및 협업 능력 향상**에 초점을 맞춰야 합니다.  **기억력과 정보 통합 능력**의 개선은 LLM이 실제 팀 환경에서 효과적으로 협업하는 데 필수적입니다.  **데이터셋의 질적 개선**과 **다양한 실제 업무 환경**을 반영한 평가 방법론 개발 또한 중요합니다.  모델의 크기 확장만으로는 한계가 있으며, **장기 기억 및 추론 능력**을 위한 새로운 메커니즘 개발이 필요합니다.  **신뢰성 및 윤리적 문제** 해결도 중요한 과제이며,  **사용자 맞춤형 인터페이스** 개발을 통해 사용성을 높이는 연구도 필요합니다.  궁극적으로 LLM은 단순한 도구를 넘어 **인간과 효과적으로 협력하는 동반자**가 되어야 합니다. 이러한 목표 달성을 위해서는 **학계와 산업계의 긴밀한 협력**이 절대적으로 중요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.13791/extracted/6216628/figs/dataset_creation.png)

> 🔼  그림 2는 MEMORYCODE 데이터셋 생성 과정을 보여줍니다. 먼저, instructions, fillers, persona, names 등 네 가지 씨앗(seed)에서 무작위로 값을 샘플링하여 템플릿의 변수들을 채웁니다. 그런 다음, 생성된 템플릿을 LLM에 프롬프트로 입력하여 대화 내역(dialogue history)을 생성합니다. 이 과정을 통해 다양한 상황과 맥락을 가진 여러 개의 다중 세션 대화 데이터를 생성할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Dataset generation process. First, we randomly sample from our seeds to fill the variables of the template. The LLM is then prompted with this template to generate the dialogue history.
> </details>



![](https://arxiv.org/html/2502.13791/extracted/6216628/figs/average_scores.png)

> 🔼 그림 3은 다양한 크기의 최근 대규모 언어 모델(LLM)들의 성능을 보여줍니다. 세 가지 평가 설정(지침, 세션, 내역)에서 모델의 평균 점수를 비교합니다. '내역' 설정에서는 15개 미만의 세션을 포함하는 대화 내역을 '짧은' 내역으로, 16~100개의 세션을 포함하는 대화 내역을 '긴' 내역으로 구분하여 분석합니다. 이 그림은 모델이 단일 지침을 따르는 능력, 여러 지침을 포함하는 단일 세션 내에서 지침을 따르는 능력, 그리고 긴 대화 내역에 걸쳐 지침을 따르는 능력을 비교하여 모델의 장기적인 상호 작용 능력을 평가합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Average Instruction, Session, and History scores per model. For the latter, ‘short’ includes dialogue histories with less than 15 sessions, ‘long’ those with 16 to 100 sessions.
> </details>



![](https://arxiv.org/html/2502.13791/extracted/6216628/figs/per_session_score_all_models.png)

> 🔼 그림 4는 여러 세션에 걸친 대화의 횟수에 따른 모델의 정확도 점수를 보여줍니다. 세션 수가 증가함에 따라 모든 모델의 정확도가 비슷하게 감소하는 것을 보여줍니다. 이는 장기적인 상호작용에서 현재의 대규모 언어 모델이 가진 근본적인 한계를 보여주는 것입니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Score per number of sessions.
> </details>



![](https://arxiv.org/html/2502.13791/extracted/6216628/figs/cum_no_rag_pivot_only.png)

> 🔼 그림 5는 INSTRUCTIONS-CHAIN 설정에서 각 세션 수에 따른 모델의 성능 점수를 보여줍니다.  INSTRUCTIONS-CHAIN 설정은 모델에 대화 내역 전체가 아닌, 작업 해결에 필요한 지시 사항들만 순차적으로 제공하는 설정입니다. 이 그림을 통해 대화의 길이가 길어질수록 모델의 성능이 전반적으로 감소하는 것을 확인할 수 있으며, 특히 100개 이상의 세션에서는 모든 모델의 성능이 유사하게 낮아지는 것을 보여줍니다. 이는 모델이 대화 내역에서 관련 정보를 검색하고, 지시 사항들의 연쇄를 추론하는 능력에 한계가 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Per-sessions score for Instr.-chain.
> </details>



![](https://arxiv.org/html/2502.13791/extracted/6216628/figs/update_rank_all_models.png)

> 🔼 그림 6은 지시사항 업데이트 횟수에 따른 모델 성능 점수를 보여줍니다. 업데이트 횟수가 증가할수록 모델의 정확도가 떨어지는 것을 보여주는 그래프입니다. 이는 모델이 지시사항을 반복적으로 업데이트하는 것에 어려움을 겪는다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Score as a function of update rank.
> </details>



![](https://arxiv.org/html/2502.13791/extracted/6216628/figs/cum_rag_pivot_only.png)

> 🔼 그림 7은 여러 세션에 걸친 대화 내역의 길이에 따른 모델 성능을 보여줍니다. 세션 수가 증가함에 따라 모델의 정확도가 감소하는 것을 확인할 수 있습니다. 특히, 긴 대화 내역(>15 세션)에서는 모든 모델의 성능이 현저하게 저하됨을 보여줍니다. 이는 모델이 장기간에 걸친 상호작용에서 정보를 효과적으로 검색하고 통합하는 데 어려움을 겪고 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Score as a function of number of sessions.
> </details>



![](https://arxiv.org/html/2502.13791/extracted/6216628/figs/per_pivot_score_insertion.png)

> 🔼 그림 8은 GPT-4 모델에 대한 각 명령어 삽입 점수의 평균을 보여줍니다. 이는 모델이 다양한 코딩 지침을 얼마나 잘 따르는지 평가하기 위해 수행된 실험 결과를 시각적으로 보여줍니다. 각 막대는 특정 명령어에 대한 평균 점수를 나타내며, 점수가 높을수록 모델이 해당 명령어를 더 잘 따랐음을 의미합니다. 이 그림은 모델의 성능을 명령어별로 비교 분석하는 데 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Average per-instruction insertion scores for GPT-4o
> </details>



![](https://arxiv.org/html/2502.13791/extracted/6216628/figs/per_pivot_score_update.png)

> 🔼 그림 9는 GPT-4 모델에 대한 각 명령어 업데이트에 따른 평균 점수를 보여줍니다. 이는 모델이 명령어 업데이트를 처리하는 능력을 평가하기 위해 수행된 분석의 결과입니다. 각 명령어의 업데이트 횟수에 따라 점수가 달라지는 것을 보여주는 막대 그래프 형태로 되어 있습니다. 업데이트 횟수가 많을수록 점수가 낮아지는 경향을 보이는데, 이는 모델이 명령어의 연속적인 업데이트를 추적하고 통합하는 데 어려움을 겪음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Average per-instruction update scores for GPT-4o
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Parameter | Short dataset (&lt;15 sessions) | Long dataset (&gt;15 sessions) |
|---|---|---|
| Sessions | 5.71 ± 4.65 | 48.00 ± 27.85 |
| Sessions<sub>w/ instr.</sub> | 3.38 ± 2.66  | 28.13 ± 16.56 |
| Instr. | 4.98 ± 4.10 | 42.24 ± 25.37 |
| Instr.<sub>added</sub> | 3.56 ± 2.62 | 24.82 ± 15.06 |
| Instr.<sub>updated</sub> | 1.41 ± 1.97 | 17.42 ± 11.93 |
| Fillers | 5.04 ± 4.75 | 45.06 ± 29.36 |
| Filler<sub>added</sub> | 3.36 ± 2.92 | 24.63 ± 12.70 |
| Filler<sub>updated</sub> | 1.52 ± 1.81 | 18.86 ± 13.48 |
| Tokens | 3.20k ± 2.71k | 26.15k ± 15.50k |
| Vocabulary | 8.54k | 14.24k |{{< /table-caption >}}
> 🔼 이 표는 논문의 3.2절 '대화 내역'에서 생성된 '짧은' 데이터셋과 '긴' 데이터셋의 통계적 요약을 보여줍니다.  '짧은' 데이터셋은 15개 미만의 세션을, '긴' 데이터셋은 15개 이상의 세션을 포함합니다. 표에는 각 데이터셋의 세션 수, 지시어가 포함된 세션의 비율, 각 세션의 지시어 수, 지시어 업데이트 비율, 필러 업데이트 비율, 토큰 수, 어휘 크기 등의 평균과 표준 편차가 제시되어 있습니다.  이 정보는 모델 성능 평가에 사용되는 두 가지 데이터셋의 규모와 특징을 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Summary statistics (averages and standard deviations) for the ‘short’ and ‘long’ datasets.
> </details>

{{< table-caption >}}
| DIALOGUE HISTORY | 
|---|---| 
| (1) **Yoon-Seo:** Alexander, it’s great to finally meet you. I’m Yoon-Seo, your mentor … | 
| (2) **Yoon-Seo:** …One of our key practices is to <span style="background-color:#FFAD7A;">always add comments to your code</span>… | 
| (3) **Yoon-Seo:** …<span style="background-color:#59DEFF;">All variable names should</span> <span style="background-color:#59DEFF;">now end with ‘_z’</span> … | 
| (4) **Yoon-Seo:** …When <span style="background-color:#8FFF42;">naming attributes</span>, […] <span style="background-color:#8FFF42;">include the string ‘chx’</span> in the name … | 
| EVALUATION QUERY | 
|---|---| 
| Write a function that checks if a string is a valid palindrome | 
| MODEL OUTPUT | 
|---|---| 
| <span style="background-color:#FFAD7A;"># Initialize two pointers</span> | 
| `def is_palindrome_<span style="background-color:#8FFF42;">chx</span>(s_<span style="background-color:#8FFF42;">chx</span>):` | 
| `left_<span style="background-color:#8FFF42;">chx</span><span style="background-color:#59DEFF;">_n</span> = 0` | 
| `right_<span style="background-color:#8FFF42;">chx</span><span style="background-color:#59DEFF;">_n</span> = len(s_<span style="background-color:#8FFF42;">chx</span>) - 1` | 
| … | {{< /table-caption >}}
> 🔼 표 3은 4개의 세션으로 구성된 대화 기록의 예시를 보여줍니다. 각 세션은 괄호 안에 세션 ID가 표시되어 있습니다. GPT-4는 주석에 대한 지침을 올바르게 적용하지만, 속성 이름과 변수 이름에 대한 업데이트는 올바르게 적용하지 못합니다. 이는 모델이 장기적인 상호 작용에서 정보를 효과적으로 추출하고 통합하는 데 어려움을 겪는다는 것을 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Table 3: A 4-session dialogue history (session id in parenthesis). GPT-4o correctly applies the instruction about comments but not the one about attribute names and the update on variable names.
> </details>

{{< table-caption >}}
| Model | Instruction | Session | Short History | Long History |
|---|---|---|---|---|
| Command R+ | 0.89 (±0.13) | 0.66 (±0.24) | 0.40 (±0.35) | 0.11 (±0.07) |
| Llama-3.1-8B | 0.71 (±0.25) | 0.36 (±0.25) | 0.23 (±0.28) | 0.12 (±0.06) |
| Llama-3.1-70B | 0.92 (±0.12) | 0.88 (±0.16) | 0.64 (±0.33) | 0.12 (±0.07) |
| Llama-3.1-405B | 0.95 (±0.09) | 0.90 (±0.12) | 0.70 (±0.29) | 0.20 (±0.10) |
| GPT-4o | **0.94** (±0.10) | **0.93** (±0.10) | **0.79** (±0.24) | **0.30** (±0.16) |{{< /table-caption >}}
> 🔼 표 4는 다양한 크기의 최신 대규모 언어 모델(LLM)들이 몇 가지 평가 설정에서 얼마나 잘 수행하는지 보여줍니다.  평가는 세 가지 유형의 텍스트 입력(단일 지침, 단일 세션, 전체 대화 기록)을 사용하여 이루어졌습니다. 각 설정에 대한 모델의 평균 점수(표준 편차 포함)가 제시되어 있습니다. 단일 지침 설정은 모델이 독립적인 코딩 작업을 얼마나 잘 처리하는지 측정하는 반면, 세션 설정과 전체 대화 기록 설정은 모델이 여러 라운드의 상호 작용에 걸쳐 정보를 추적하고 통합하는 능력을 측정합니다. 단일 세션 설정은 단일 날의 상호작용을 평가하는 반면, 전체 대화 기록 설정은 장기간에 걸친 여러 세션의 상호작용을 평가합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Average (standard deviation) Instruction, Session, Short History and Long History scores per model.
> </details>

{{< table-caption >}}
| Mentor | Mentee | Company |
|---|---|---|
| Alice | Bob | NEXT |
| Juan | Luke | INNOVADE |
| Sara | Eva | TECHNO |
| Luis | Kiyotaka | CODEME |
| Maria | David | STARTED |
| Carlos | Sofia | GROWTHX |
| Yuichi | Pablo | DEVS |
| Pedro | Marta | CODEM |
| Djibril | Jorge | CHEETAH |
| Jean-Aimé | Lucas | VATO |
| Emma | Oliver | LEAP |
| Michael | Ella | ZENITH |
| Yoon-Seo | Alexander | AXIOM |
| Ethan | Rado | ORBIT |
| Harena | Jacob | VERSA |
| Sylvie | Sophia | PACE |
| Sophie | Liam | UNITE |
| Naivo | Dera | SYNERGY |
| Daniel | Noah | FORTUNA |{{< /table-caption >}}
> 🔼 이 표는 논문의 데이터셋 생성에 사용된 멘토, 멘티, 그리고 그들의 소속 회사 목록을 보여줍니다.  각 멘토와 멘티는 가상의 인물이며,  데이터셋의 다양성을 확보하기 위해 다양한 이름과 회사가 할당되었습니다.  각 이름은 고유한 특징을 가진 가상의 인물을 나타내며,  연구에서 사용된 가상의 회사 이름 또한 데이터셋의 현실성을 높이는 요소로 작용합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: List of mentors, mentees, and their respective companies.
> </details>

{{< table-caption >}}
| Mentor persona |
|---|---| 
| [mentor] is a patient and supportive mentor. [mentor] enjoys helping others and sharing their knowledge and experience. [mentor] is always looking for ways to empower and inspire their mentee. |
| [mentor] is a strict and demanding mentor. [mentor] has high expectations for their mentee. [mentor] goes straight to the point and is very clear. |
| [mentor] is a caring and nurturing mentor. [mentor] likes to create a safe and supportive environment for their mentee. [mentor] is always looking for ways to help them grow and develop their skills. |
| [mentor] is a passionate and energetic mentor. [mentor] thrives on helping others and their enthusiasm is contagious. [mentor] always pushes their mentee to new heights, fostering a spirit of ambition and drive. |
| [mentor] is a structured and goal-oriented mentor. [mentor] helps their mentee to set realistic, achievable goals. [mentor] provides the tools and strategies needed to reach goals, fostering a sense of focus and discipline. |{{< /table-caption >}}
> 🔼 이 표는 논문의 3.1절 Seeds 섹션에 있는 표로,  멘토의 성격 유형을 설명합니다.  각 멘토는 다양한 성격 특징을 가지고 있으며, 이는 멘토가 대화에서 보여주는 행동 양식과 상호 작용 방식에 영향을 줍니다.  표에는 각 멘토 유형의 간략한 설명이 포함되어 있으며, 실제 프롬프트에서는 [mentor] 부분이 실제 멘토의 이름으로 대체됩니다.  즉, 표는 대화 생성 과정에서 멘토의 역할을 다양하게 설정하기 위한 기준을 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: List of mentor personas. [mentor] is replaced with the name of the mentor in the prompts.
> </details>

{{< table-caption >}}
| Mentee persona |
|---|---|---|---|---|
| [mentee] is shy and wants to improve their coding skills. [mentee] just graduated from college and [mentee] is eager to learn from their mentor. | [mentee] is a confident and ambitious software engineer. [mentee] is always looking for new challenges and opportunities to grow. [mentee] has been working in the industry for a few years now. | [mentee] is a perfectionist with great attention to detail. [mentee] likes things to be done the right way and has a hard time delegating tasks to others. [mentee] is critical of himself and of others. | [mentee] is a social and outgoing person. [mentee] enjoys working in teams and collaborating with others. [mentee] is always looking for ways to connect with their colleagues and builds strong relationships. | [mentee] is a quiet and introverted individual. [mentee] prefers to work alone and is not very comfortable in social situations. [mentee] struggles to communicate their ideas and thoughts to others. |
| [mentee] is a creative and innovative thinker. [mentee] likes to experiment with new ideas and approaches. [mentee] is not afraid to take risks and try new things. |  |  |  |  |{{< /table-caption >}}
> 🔼 표 7은 연구 논문의 '3. Dataset' 섹션에 포함된 표로,  다양한 대화 생성을 위한 참가자(멘티)의 성격 유형을 보여줍니다. 각 멘티는 고유한 성격 특징을 가지며, 이러한 특징은  실제 업무 환경에서 멘티가 보일 수 있는 다양한 행동 양식을 반영합니다. 각 멘티 유형 설명에서 [mentee] 부분은 실제 대화 생성 시 해당 멘티의 이름으로 대체됩니다.  즉,  멘티의 성격에 따라 생성되는 대화의 내용이 달라질 수 있음을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 7: List of mentee personas. [mentee] is replaced with the name of the mentee in the prompts.
> </details>

{{< table-caption >}}
| Instruction Prompt Example | 
|---|---| 
| **SYSTEM PROMPT** |  | 
|  | ## Style Guide Do not acknowledge. Only generate Python code and nothing else before or after. Do not explain the code. Do not ask for more information but directly give the answer. | 
| **PROMPT** | Write a function that converts an integer to Roman numerals. Do not provide example usage. Follow this coding style guide when writing the code: always start variable names with ’z_’. | {{< /table-caption >}}
> 🔼 표 14는 Instruction prompt의 예시를 보여줍니다. 여기서 지시사항은 변수 이름을 'z_'로 시작하라는 것입니다.  이 표는 모델이 간단한 코딩 작업을 수행하는 능력을 평가하기 위한 실험 설정에 대한 설명을 제공합니다.  특히,  'z_'로 시작하는 변수 이름이라는 제약 조건 하에 함수를 작성하는 모델의 능력을 테스트하는 방법을 보여줍니다. 이는 모델의 코드 생성 능력과 지시 사항을 따르는 능력을 평가하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Example of an Instruction prompt where the instruction is to start variable names with ’z_’..
> </details>

{{< table-caption >}}
| History Prompt Example                                                                                                |
|-------------------------------------------------------------------------------------------------------------------------|
| **SYSTEM PROMPT**                                                                                                       |
|-------------------------------------------------------------------------------------------------------------------------|
| ## Task and Context
You are Pablo, a new software engineer at DEVS. Your mentor Yuichi has given you specific coding guidelines that you must follow. |
|-------------------------------------------------------------------------------------------------------------------------|
| ## Style Guide
Do not acknowledge. Only generate Python code and nothing else before or after. Do not explain the code. Do not ask for more information but directly give the answer. |
|-------------------------------------------------------------------------------------------------------------------------|
| **PROMPT**                                                                                                              |
|-------------------------------------------------------------------------------------------------------------------------|
| This is a thread of conversations between you and your mentor Pablo:                                                      |
|-------------------------------------------------------------------------------------------------------------------------|
| [dialogue]                                                                                                               |
|-------------------------------------------------------------------------------------------------------------------------|
| Based on information provided, write a function that converts an integer to Roman numerals. Do not provide example usage. You must follow all the latest coding guidelines provided by your mentor, including any possible updates. |{{< /table-caption >}}
> 🔼 표 9는 모델에 전체 대화 이력을 입력으로 제공하는 History 프롬프트의 예시를 보여줍니다. 세션 프롬프트는 전체 대화 이력 대신 단일 세션을 삽입한 것을 제외하고는 동일합니다. 이는 모델이 대화의 여러 지점에 걸쳐 제공된 정보를 종합하고 활용하여 작업을 수행하는 능력을 평가하기 위한 것입니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Example of a History prompt where [dialogue] is replaced by the entire dialogue history. Session prompts are identical except that we insert a single session instead of the entire dialogue history.
> </details>

{{< table-caption >}}
| Instructions-Chain Prompt Example |
|---|---| 
| **SYSTEM PROMPT** |  |
|  | ## Style Guide
Do not acknowledge. Only generate Python code and nothing else before or after. Do not explain the code. Do not ask for more information but directly give the answer. |
| **PROMPT** | This is a list of coding guidelines: always include a single digit in class names, always start variable names with ’z_’, always use docstrings in methods, always start variable names with ’wr_’, always use snake_case for class names, always start variable names with ’vr_’, always include assert statements in functions, always start variable names with ’m_’, always start variable names with ’w_’, always start variable names with ’x_’, always end function argument names with ’_e’, always add comments in your code, always end function argument names with ’a’, always start variable names with ’n’, always end function argument names with ’_g’, always import the ’secrets’ module even if it is not used. Some guidelines might have been updated. You must follow all the latest versions of the guidelines. Write a function that converts an integer to Roman numerals. Do not provide example usage. |{{< /table-caption >}}
> 🔼 표 10은 16개의 코딩 지침이 포함된 Instructions-Chain 프롬프트의 예시를 보여줍니다. 이 표는 모델이 여러 세션에 걸쳐 제공된 관련 없는 정보들 사이에서 간단한 코딩 지침을 추적하고 실행하는 능력을 평가하기 위해 고안된 MEMORYCODE 데이터셋의 생성 과정을 설명합니다.  다양한 코딩 규칙들을 포함하고 있으며, 모델이 이러한 규칙들을 장기간에 걸쳐 일관되게 적용하는지를 평가하는데 사용됩니다. 각 지침은 특정 파이썬 객체(예: 함수)에 적용되며, 일부 지침은 업데이트될 수 있습니다.  즉, 모델은 지침들의 이전 버전들을 기억하고, 가장 최신의 업데이트된 지침을 따라야 합니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Example of a Instructions-Chain prompt with 16 instructions.
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