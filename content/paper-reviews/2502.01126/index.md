---
title: "Language Models Prefer What They Know: Relative Confidence Estimation via Confidence Preferences"
summary: "언어 모델의 신뢰도를 더 정확하게 측정하는 새로운 방법 제시!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Question Answering", "🏢 Stanford University",]
showSummary: true
date: 2025-02-03
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.01126 {{< /keyword >}}
{{< keyword icon="writer" >}} Vaishnavi Shrivastava et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-04 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.01126" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.01126" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

기존 언어 모델들은 질문에 대한 자신감을 0~1 사이의 숫자로 직접 평가하는 **절대적 신뢰도 추정** 방식을 사용하는데, 이는 모델의 불확실성을 제대로 반영하지 못하고 정확도를 제대로 평가하는 데 유용하지 않다는 문제가 있습니다.  본 논문에서는 이러한 문제를 해결하기 위해, **상대적 신뢰도 추정**이라는 새로운 방법을 제안합니다.  즉, 모델이 두 질문 중 어느 질문에 더 자신감이 있는지 비교하도록 하는 것입니다. 



본 논문에서는 상대적 신뢰도 추정을 위해, 각 질문을 '선수'로 간주하고 모델의 비교 결과를 '경기 결과'로 간주하여 Elo, TrueSkill, Bradley-Terry 등의 순위 집계 알고리즘을 사용하여 각 질문에 대한 신뢰도 점수를 산출합니다.  다양한 최첨단 언어 모델과 다양한 과학, 사회 과학, 상식 추론 질문에 대한 실험 결과, **상대적 신뢰도 추정이 절대적 신뢰도 추정보다 신뢰도 점수를 더욱 정확하게 산출한다는 것을 입증**했습니다.  특히, 선택적 분류 AUC(Area Under the Curve) 측면에서 절대적 신뢰도 추정보다 평균 3.5% 향상, 자기 일관성 접근 방식보다 1.7% 향상되는 결과를 얻었습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 상대적 신뢰도 추정이 절대적 신뢰도 추정보다 더 나은 신뢰도 점수를 제공한다는 것을 발견했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} Elo, TrueSkill, Bradley-Terry 등의 순위 집계 방법을 사용하여 상대적 신뢰도 비교 결과를 신뢰도 점수로 변환하는 방법을 제시했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 다양한 최첨단 언어 모델과 데이터셋에 걸쳐 상대적 신뢰도 추정 방법이 일관되게 더 나은 성능을 보여줍니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**본 논문은 언어 모델의 신뢰도 추정에 대한 새로운 접근 방식을 제시하여 연구자들에게 중요한 의미를 가집니다.** 기존의 절대적 신뢰도 평가 방식의 한계를 극복하고 상대적 신뢰도 평가를 통해 더욱 정확하고 신뢰할 수 있는 신뢰도 점수를 얻을 수 있음을 보여줍니다. 이는 사용자들이 언어 모델의 출력 결과를 더욱 효과적으로 활용하고, 모델의 한계를 인지하는 데 도움을 줄 수 있습니다. **또한, 본 논문에서 제시된 상대적 신뢰도 추정 방법은 다양한 언어 모델과 데이터셋에 적용될 수 있어 폭넓은 활용 가능성을 가지고 있습니다.**  향후 연구를 위한 새로운 방향을 제시하고, 언어 모델의 신뢰도 추정 분야에 대한 이해를 심화시키는 데 기여할 것으로 기대됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.01126/extracted/6173720/sections/figures/intro_fig.png)

> 🔼 그림 1은 언어 모델의 상대적 신뢰도 추정 방법을 보여줍니다. 먼저, 다양한 질문들에 대한 모델의 답변을 얻습니다. 각 질문  qᵢ 에 대해, 다른 n개의 질문 qⱼ 와 비교하여 신뢰도 비교 데이터를 생성합니다. 모델에게 두 질문 중 어떤 질문에 대해 더 자신 있게 답변할 수 있는지 묻습니다. 각 질문을 경쟁 게임의 '플레이어'로, 신뢰도 비교 결과를 매치 결과로 간주하여 Elo 등급과 같은 순위 집계 기술을 활용하여 모델의 신뢰도 선호도를 신뢰도 점수로 변환합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Relative Confidence Estimation. We first prompt models to elicit their answers to different questions. For each question qisubscript𝑞𝑖q_{i}italic_q start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT, we match qisubscript𝑞𝑖q_{i}italic_q start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT with n𝑛nitalic_n other questions qjsubscript𝑞𝑗q_{j}italic_q start_POSTSUBSCRIPT italic_j end_POSTSUBSCRIPT and generate confidence preference data. We ask the model to compare its level of confidence in the pair of questions and decide which question it is more confident in answering correctly. We treat the questions and answers as “players” in these matchups and the confidence preferences as match outcomes. Leveraging rank aggregation techniques used in competitive games, such as Elo rating, we translate the model’s confidence preferences into confidence scores.
> </details>





{{< table-caption >}}
| Category | Dataset | Direct | Hybrid SC | Elo Rating | TrueSkill | Bradley-Terry |
|---|---|---|---|---|---|---|
|  | GPQA | 0.356 | 0.293 | 0.453 | 0.454 | 0.451 |
|  | MedQA | 0.864 | 0.859 | 0.914 | 0.918 | 0.915 |
|  | OBQA | 0.926 | 0.959 | 0.970 | 0.969 | 0.968 |
|  | Physics | 0.862 | 0.793 | 0.907 | 0.934 | 0.938 |
|  | Algebra | 0.378 | 0.448 | 0.467 | 0.466 | 0.476 |
|  | Chem | 0.585 | 0.486 | 0.747 | 0.751 | 0.746 |
| STEM | Security | 0.861 | 0.899 | 0.895 | 0.910 | 0.908 |
|  | Law | 0.749 | 0.747 | 0.813 | 0.834 | 0.825 |
|  | Ethics | 0.889 | 0.963 | 0.922 | 0.922 | 0.917 |
|  | Econ | 0.711 | 0.703 | 0.778 | 0.770 | 0.748 |
| Social Sciences | Policy | 0.961 | 0.993 | 0.989 | 0.987 | 0.990 |
|  | TQA | 0.861 | 0.899 | 0.876 | 0.874 | 0.877 |
|  | CSQA | 0.837 | 0.920 | 0.865 | 0.868 | 0.870 |
| Commonsense Reasoning | SIQA | 0.830 | 0.879 | 0.868 | 0.867 | 0.871 |
|  | Average | 0.762 | 0.774 | 0.819 | 0.823 | 0.821 |{{< /table-caption >}}

> 🔼 본 표는 Llama 3.1 405B 모델을 사용하여 다양한 질문응답 데이터셋에 대해 절대적 신뢰도 추정과 상대적 신뢰도 추정 방법의 성능을 비교 분석한 결과를 보여줍니다. 절대적 신뢰도 추정 방법으로는 직접 프롬프팅(Direct)과 자기일관성 프롬프팅(Hybrid SC)이 사용되었고, 상대적 신뢰도 추정 방법으로는 Elo, TrueSkill, Bradley-Terry 세 가지 순위 집계 알고리즘이 사용되었습니다. 표에는 각 데이터셋별 AUC (Area Under the Curve) 값이 제시되어 있으며, STEM(과학, 기술, 공학, 수학) 데이터셋에서는 상대적 신뢰도 추정 방법이 절대적 신뢰도 추정 방법보다 성능이 우수한 반면, 상식 추론(Commonsense Reasoning) 데이터셋에서는 자기일관성 프롬프팅이 더 나은 성능을 보였습니다. 특히, TrueSkill 알고리즘을 사용한 상대적 신뢰도 추정 방법은 직접 프롬프팅 방식보다 6.1%, 자기일관성 프롬프팅 방식보다 4.9% 향상된 성능을 보였습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Llama 3.1 405B AUCs All Methods. We show the dataset-level results for Llama 3.1 405B, for the Direct and Hybrid SC absolute confidence baselines and for relative confidence estimation with different rank aggregation methods (Elo Rating, TrueSkill, Bradley-Terry). Relative confidences outperform absolute confidences for all STEM datasets, whereas absolute confidences with self-consistency (Hybrid SC) work best for commonsense reasoning tasks. Overall, relative confidences with TrueSkill rank aggregation lead to a 6.1% improvement over direct prompting and a 4.9% improvement over self-consistency prompting.
> </details>





### In-depth insights


#### Relative Confidence
본 논문에서 제안하는 상대적 신뢰도(Relative Confidence)는 언어 모델의 불확실성을 평가하는 새로운 방법입니다. **절대적 신뢰도(Absolute Confidence)** 측정 방식과 달리, 각 질문에 대한 신뢰도를 개별적으로 평가하는 대신, 질문 쌍을 비교하여 상대적인 신뢰도를 판단합니다.  이는 모델이 절대적인 확률을 추정하는 것보다 상대적인 비교를 더 잘 수행한다는 가정에 기반합니다. **Elo rating, Bradley-Terry, TrueSkill** 과 같은 순위 집계 방법을 사용하여 모델의 상대적 신뢰도 선호도를 신뢰도 점수로 변환하며, **선택적 분류 AUC(Selective Classification AUC)**를 통해 기존 방법보다 우수한 성능을 보입니다. **특히 STEM, 사회과학, 상식 추론 과제에서 기존 절대적 신뢰도 추정 방식보다 더 신뢰할 수 있는 신뢰도 점수를 제공**하는 것으로 나타났습니다.  상대적 신뢰도는  모델의 출력 해석에 있어 사용자의 의사결정에 도움을 줄 수 있는 중요한 지표가 될 것으로 예상됩니다.

#### Rank Aggregation
본 논문에서 제시된 순위 집계(Rank Aggregation) 방법은 언어 모델의 상대적 자신감을 정확하게 평가하는 데 중요한 역할을 합니다. **다양한 질문들에 대한 모델의 자신감 수준을 비교하여 순위를 매기고, 이를 통해 각 질문에 대한 자신감 점수를 산출하는 방식**입니다.  이 과정에서 Elo 등급, Bradley-Terry 모델, TrueSkill 알고리즘 등 다양한 순위 집계 기법을 활용하여 모델의 상대적 자신감을 보다 정교하게 측정하고자 하였습니다.  이는 **절대적 자신감 측정 방식의 한계를 극복**하기 위한 시도로, 절대적 점수 부여 방식의 모호성과 비효율성을 개선하는 데 초점을 맞추고 있습니다. **상대적 비교를 통해 얻어낸 순위 정보를 바탕으로 자신감 점수를 부여함으로써 모델의 성능 평가를 개선**하고, 사용자에게 보다 신뢰할 수 있는 결과를 제공하고자 하는 의도가 엿보입니다.  각 알고리즘의 강점과 약점을 비교 분석하고, **데이터의 노이즈와 불일치성에 대한 강건성**을 고려하여 적절한 알고리즘을 선택하는 것이 중요합니다.  **모델의 자신감을 보다 정확하고 효율적으로 평가**하고자 하는 노력은 향후 언어 모델의 신뢰성 향상에 크게 기여할 것으로 예상됩니다.

#### Model Comparisons
본 논문에서는 다양한 언어 모델의 성능을 비교 분석하는 "모델 비교" 섹션이 있었을 것이라고 추측해 볼 수 있습니다. 이 섹션에서는 **GPT-4, GPT-40, Gemini 1.5 Pro, Claude 3.5 Sonnet, Llama 3.1 405B 와 같은 최첨단 언어 모델들의 상대적 신뢰도 추정 성능**을 비교했을 것입니다.  특히, 절대적 신뢰도 추정과 상대적 신뢰도 추정 방법을 비교하여 상대적 신뢰도 추정의 우수성을 보여주는 결과를 제시했을 것으로 예상됩니다.  **다양한 STEM, 사회과학, 상식 추론 질문 응답 과제에 대한 실험 결과**를 통해, 상대적 신뢰도 추정 방법이 더욱 안정적이고 정확한 신뢰도 점수를 제공하며, 선택적 분류 AUC(Area Under the Curve)에서 상당한 성능 향상을 보였다는 점이 강조되었을 것입니다.  **Elo 평점, TrueSkill, Bradley-Terry와 같은 순위 집계 알고리즘**을 사용하여 상대적 신뢰도 점수를 산출한 방법과 그 결과도 자세히 다루었을 것으로 보입니다.  각 모델의 강점과 약점을 비교 분석하고, 어떤 모델이 특정 유형의 질문에 대해 더 나은 성능을 보이는지에 대한 통찰력을 제공했을 것으로 예상됩니다.  **결론적으로, 이 섹션은 상대적 신뢰도 추정의 효용성과 최첨단 언어 모델들의 신뢰도 추정 성능 비교**에 대한 심도있는 분석을 제공하여, 언어 모델의 신뢰성 향상에 기여하는 중요한 부분이었을 것입니다.

#### Future Directions
본 논문은 언어 모델의 신뢰도 추정에 대한 새로운 방법론을 제시하며, 특히 상대적 신뢰도 추정 방식의 효과성을 보여줍니다. **미래 연구 방향**으로는 첫째, **더욱 다양하고 정교한 상대적 신뢰도 선호도 데이터 수집 방식**을 개발하는 것이 중요합니다.  둘째, 현재 사용된 Elo, TrueSkill, Bradley-Terry 외 다양한 순위 집계 알고리즘을 추가적으로 비교 분석하여, 특정 모델이나 데이터셋에 최적화된 알고리즘을 찾아야 합니다. 셋째, **장문 생성에 대한 상대적 신뢰도 추정**으로 확장하여, 생성 텍스트의 완전성, 사실성 등 다양한 측면에 대한 신뢰도를 평가하는 연구가 필요합니다. 넷째, **난이도 추정치를 활용한 커리큘럼 학습**을 통해 모델의 신뢰도 향상을 도모할 수 있습니다. 마지막으로, 본 논문에서 제시된 상대적 신뢰도 추정 방식과 기존 절대적 신뢰도 추정 방식을 **상호 보완적으로 결합**하는 연구가 필요하며, 이를 통해 언어 모델의 신뢰도 평가를 더욱 정확하고 효과적으로 수행할 수 있을 것입니다. 이러한 연구들을 통해 언어 모델의 신뢰성을 높이고 사용자 경험을 개선하는 데 크게 기여할 수 있을 것으로 기대됩니다.

#### Limitations
본 논문은 언어 모델의 신뢰도 추정에 대한 새로운 방법론을 제시하지만, 몇 가지 제한점을 갖고 있습니다. **첫째**, 상대적 신뢰도 추정은 질문 쌍을 비교하는 방식이므로, 질문 간의 상호 의존성을 고려하지 못할 수 있습니다. **둘째**, 사용된 순위 집계 알고리즘은 최적의 순위를 보장하지 않으며, 노이즈가 많은 데이터에 민감할 수 있습니다.  **셋째**, 본 연구는 특정 언어 모델과 데이터셋에 국한되어 일반화 가능성이 제한적입니다.  **넷째**, 절대적 신뢰도 추정과의 비교에서 일부 모델에서는 상대적 신뢰도 추정이 더 나은 성능을 보이지 않을 수 있습니다. 따라서, **향후 연구에서는 질문 간의 상호작용을 고려하는 방법, 더욱 강건한 순위 집계 알고리즘, 다양한 언어 모델 및 데이터셋에 대한 추가 실험 등을 통해 본 연구의 제한점을 보완해야 합니다.**  다만, 상대적 신뢰도 추정이 절대적 신뢰도 추정보다 더 나은 성능을 보인다는 주요 결과는 여전히 유효하며, 언어 모델의 신뢰도 추정에 대한 새로운 관점을 제시했다는 점에서 의미가 있습니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.01126/extracted/6173720/sections/figures/direct_confidence_prompt_instruction.png)

> 🔼 그림 2는 언어 모델이 질문에 대한 답변에 대한 자신감을 직접 점수 매기도록 요청하는 직접적인 자신감 프롬프트 지침을 보여줍니다.  이 프롬프트는 모델이 0에서 1까지의 척도로 자신감을 평가하고, 0에 가까운 점수는 낮은 자신감을, 1에 가까운 점수는 높은 자신감을 나타낸다는 것을 명시적으로 지시합니다. 사용자는 모델이 질문에 대한 답변을 선택하고 자신감 점수를 제공해야 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Direct Confidence Prompt Instruction. Asks the model to directly score its confidence in its answer to a question.
> </details>



![](https://arxiv.org/html/2502.01126/extracted/6173720/sections/figures/relative_confidence_prompt.png)

> 🔼 이 그림은 모델이 두 질문에 대한 자신감을 비교하도록 요청하는 상대적 자신감 프롬프트를 보여줍니다.  두 질문과 각 질문에 대한 답변이 제시되고, 모델은 어느 질문에 대해 더 자신있게 정답을 제시할 수 있는지 선택해야 합니다. 이는 절대적 자신감 측정 대신 상대적 비교를 통해 모델의 자신감을 평가하는 방법을 보여주는 예시입니다.  이는 모델이 절대적인 확신 수준을 판단하는 것보다 상대적인 질문의 어려움을 비교하는 데 더 능숙하기 때문입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Relative Confidence Prompt. Asks model to compare its confidence in two questions.
> </details>



![](https://arxiv.org/html/2502.01126/extracted/6173720/sections/figures/auc_barplot.png)

> 🔼 그림 4는 14가지 과제에 걸쳐 평균낸 선택적 분류 AUC를 모델별로 보여줍니다. 각 모델에 대해, 다양한 신뢰도 추정 방법에 따른 선택적 분류 AUC를 보여줍니다. 절대적 신뢰도 추정 기준(직접 프롬프트, 하이브리드 자기 일관성)은 파란색으로 표시되고, 상대적 신뢰도 추정(Elo 등급, TrueSkill, Bradley-Terry)은 녹색으로 표시됩니다. Llama 3.1 405B, GPT-4, Gemini 1.5 Pro, GPT-4o의 경우 상대적 신뢰도 추정이 절대적 신뢰도 추정 기준보다 성능이 우수합니다. Claude 3.5 Sonnet의 경우 상대적 신뢰도 추정이 직접 프롬프트 방식보다 성능이 우수하지만 자기 일관성 프롬프트 방식보다는 약간 성능이 떨어집니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Selective Classification AUC Across Models. For each model, we plot the selective classification AUC averaged across the 14 tasks for each confidence estimation method. The absolute confidence estimation baselines—direct prompting (Direct) and self-consistency (Hybrid SC)—are indicated in blue, while relative confidence estimation with different rank aggregation methods is in green (Elo Rating, TrueSkill, Bradley-Terry). For Llama 3.1 405B, GPT-4, Gemini 1.5 Pro, and GPT-4o, relative confidence estimates outperform both the direct and hybrid SC absolute confidence baselines. For Claude 3.5 Sonnet, relative confidences outperform direct prompting but slightly underperform self-consistency prompting.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| # Model Calls | % Gains GPT-4o | % Gains Llama 3.1 |
|---|---|---|
| 5 | 0.9% | 2.2% |
| 10 | 1.8% | 3.2% |
| 15 | 1.8% | 4.9% |{{< /table-caption >}}
> 🔼 이 표는 질문당 모델 호출 수를 5, 10, 15회로 늘려가며 상대적 신뢰도 추정의 성능 향상을 보여줍니다.  자기 일관성 기법과 비교하여 상대적 신뢰도 추정의 성능 향상을 백분율(%)로 나타냅니다. GPT-40 및 Llama 3.1 모델에 대한 결과를 보여주며, 모델 호출 수를 늘릴수록 상대적 신뢰도 추정의 성능이 향상됨을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Gains by scaling up comparisons. We report the gains of relative confidence estimation over self-consistency across different numbers of model calls.
> </details>

{{< table-caption >}}
| Category | Dataset | Direct | Hybrid SC | Elo Rating | TrueSkill | Bradley-Terry |
|---|---|---|---|---|---|---|
|  | GPQA | 0.480 | 0.421 | **0.530** | 0.528 | 0.522 |
|  | MedQA | 0.923 | 0.931 | **0.944** | 0.943 | 0.943 |
|  | OBQA | 0.971 | 0.983 | **0.987** | 0.986 | **0.987** |
|  | Physics | 0.898 | 0.914 | 0.940 | 0.944 | **0.946** |
|  | Algebra | 0.655 | **0.743** | 0.722 | 0.710 | 0.694 |
|  | Chem | 0.741 | 0.700 | 0.795 | **0.806** | 0.802 |
| STEM | Security | 0.880 | 0.913 | **0.930** | 0.927 | 0.922 |
|  | Law | 0.859 | **0.872** | **0.872** | 0.867 | 0.867 |
|  | Ethics | 0.960 | **0.969** | 0.962 | 0.962 | 0.959 |
|  | Econ | 0.799 | 0.824 | **0.837** | 0.833 | 0.833 |
| Social Sciences | Policy | 0.962 | 0.965 | **0.983** | **0.983** | 0.980 |
|  | TQA | 0.906 | **0.935** | 0.908 | 0.911 | 0.911 |
|  | CSQA | 0.864 | **0.900** | 0.886 | 0.887 | 0.884 |
| Commonsense Reasoning | SIQA | 0.855 | 0.884 | 0.905 | 0.905 | **0.908** |
|  | Average | 0.840 | 0.854 | **0.872** | 0.871 | 0.868 |{{< /table-caption >}}
> 🔼 표 3은 GPT-40 모델의 절대적 신뢰도 추정 및 상대적 신뢰도 추정 방법의 성능을 비교 분석한 결과를 보여줍니다.  절대적 신뢰도 추정은 직접 프롬프팅(Direct)과 자기일관성 프롬프팅(Hybrid SC) 두 가지 방법을 사용했고, 상대적 신뢰도 추정에는 Elo 등급, TrueSkill, Bradley-Terry 세 가지 순위 집계 알고리즘을 적용했습니다. 표는 다양한 데이터셋(STEM, 사회과학, 상식 추론)에 대한 각 방법의 AUC(Selective Classification AUC) 값을 제시합니다. 결과적으로, STEM 및 사회과학 데이터셋의 대부분에서 상대적 신뢰도 추정이 절대적 신뢰도 추정보다 우수한 성능을 보였으며, 상식 추론 과제에서는 자기일관성 프롬프팅이 더 나은 성능을 나타냈습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: GPT-4o AUCs All Methods. We show the dataset-level results for GPT-4o, for the Direct and Hybrid SC absolute confidence baselines and for relative confidence estimation with different rank aggregation methods (Elo Rating, TrueSkill, Bradley-Terry). Relative confidences outperform absolute confidences for the majority of STEM and social science datasets, while absolute confidences with self-consistency tend to work better for commonsense reasoning tasks.
> </details>

{{< table-caption >}}
| Category | Dataset | Direct | Hybrid SC | Elo Rating | TrueSkill | Bradley-Terry |
|---|---|---|---|---|---|---|
|  | GPQA | 0.441 | 0.457 | 0.454 | 0.460 | **0.466** |
|  | MedQA | 0.904 | **0.920** | 0.893 | 0.900 | 0.901 |
|  | OBQA | 0.979 | 0.984 | 0.984 | 0.984 | **0.985** |
|  | Physics | 0.909 | 0.911 | 0.925 | **0.928** | 0.927 |
|  | Algebra | 0.802 | **0.811** | 0.806 | 0.805 | 0.804 |
|  | Chem | 0.832 | 0.840 | **0.864** | 0.854 | 0.850 |
| STEM | Security | 0.920 | 0.930 | **0.934** | 0.930 | 0.917 |
|  | Law | 0.789 | 0.809 | 0.799 | 0.815 | **0.816** |
|  | Ethics | 0.956 | 0.964 | **0.971** | 0.970 | 0.966 |
|  | Econ | 0.798 | 0.822 | 0.825 | **0.829** | 0.819 |
| Social Sciences | Policy | 0.991 | **0.995** | 0.982 | 0.980 | 0.982 |
|  | TQA | 0.880 | 0.889 | **0.918** | 0.917 | 0.917 |
|  | CSQA | 0.885 | **0.887** | 0.873 | 0.869 | 0.872 |
| Commonsense Reasoning | SIQA | 0.861 | **0.897** | 0.861 | 0.856 | 0.863 |
|  | Average | 0.853 | **0.865** | 0.863 | 0.864 | 0.863 |{{< /table-caption >}}
> 🔼 표 4는 Claude 3.5 Sonnet 모델에 대한 절대적 신뢰도 추정과 상대적 신뢰도 추정 결과를 보여줍니다. 절대적 신뢰도 추정은 직접 프롬프트 방식과 자기 일관성 프롬프트 방식을 사용하며, 상대적 신뢰도 추정은 Elo Rating, TrueSkill, Bradley-Terry 세 가지 순위 집계 방법을 사용합니다.  표는 14개 데이터셋(STEM, 사회과학, 상식 추론)에 대한 데이터셋별 AUC (Selective Classification AUC)를 제시합니다. 결과적으로 상대적 신뢰도 추정은 14개 데이터셋 중 9개에서 절대적 신뢰도 추정 방식보다 성능이 우수하며, 평균적으로 자기 일관성 프롬프트 방식과 거의 동일한 성능을 보입니다(AUC 차이는 0.1% 미만).
> <details>
> <summary>read the caption</summary>
> Table 4: Claude 3.5 Sonnet AUCs All Methods. We show the dataset-level results for Claude 3.5 Sonnet, for the Direct and Hybrid SC absolute confidence baselines and for relative confidence estimation with different rank aggregation methods (Elo Rating, TrueSkill, Bradley-Terry). Relative confidences outperform absolute confidence baselines for 9 out of 14 datasets across STEM, social science, and commonsense reasoning. On average, relative confidences closely match the performance of the best absolute confidence methods (only 0.1% lower AUC than self-consistency prompting).
> </details>

{{< table-caption >}}
| Category | Dataset | Direct | Hybrid SC | Elo Rating | TrueSkill | Bradley-Terry |
|---|---|---|---|---|---|---|
|  | GPQA | 0.395 | **0.424** | 0.410 | 0.409 | 0.413 |
|  | MedQA | 0.794 | **0.831** | 0.725 | 0.786 | 0.792 |
|  | OBQA | 0.955 | 0.959 | 0.979 | **0.985** | **0.985** |
|  | Physics | 0.878 | 0.922 | 0.927 | **0.936** | 0.934 |
|  | Algebra | 0.603 | 0.612 | 0.629 | **0.651** | 0.640 |
|  | Chem | 0.717 | 0.762 | 0.806 | **0.851** | 0.842 |
| STEM | Security | **0.868** | 0.863 | 0.850 | 0.824 | 0.837 |
|  | Law | 0.695 | 0.727 | 0.766 | 0.776 | **0.778** |
|  | Ethics | 0.903 | 0.910 | 0.949 | 0.954 | **0.957** |
|  | Econ | 0.684 | 0.734 | **0.747** | 0.732 | 0.736 |
| Social Sciences | Policy | 0.961 | 0.957 | **0.980** | 0.979 | 0.978 |
|  | TQA | 0.876 | **0.891** | 0.861 | 0.853 | 0.854 |
|  | CSQA | 0.835 | **0.889** | 0.860 | 0.869 | 0.872 |
| Commonsense Reasoning | SIQA | 0.854 | **0.874** | 0.840 | 0.854 | 0.848 |
|  | Average | 0.787 | 0.811 | 0.809 | 0.818 | **0.819** |{{< /table-caption >}}
> 🔼 표 5는 Gemini 1.5 Pro 모델에 대한 다양한 신뢰도 추정 방법(직접 프롬프트, 자기 일관성 프롬프트, 상대적 신뢰도 추정)의 데이터셋별 AUC 결과를 보여줍니다. 평균적으로 Bradley-Terry 방법을 사용한 상대적 신뢰도 추정이 직접 프롬프트 방식보다 3.2%, 자기 일관성 프롬프트 방식보다 0.8% 향상된 AUC를 기록했습니다.  각 데이터셋에 대한 자세한 AUC 점수와 세 가지 신뢰도 추정 방법의 성능 비교를 통해 모델의 신뢰도 추정 성능을 종합적으로 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Gemini 1.5 Pro AUCs All Methods. We show the dataset-level AUC results for Gemini 1.5 Pro. On average, relative confidence estimation with Bradley-Terry leads to the best AUC with a 3.2% improvement over direct prompting and a 0.8% improvement over self-consistency prompting.
> </details>

{{< table-caption >}}
| Category | Dataset | Direct | Hybrid SC | Elo Rating | TrueSkill | Bradley-Terry |
|---|---|---|---|---|---|---|
|  | GPQA | 0.393 | 0.383 | 0.377 | 0.404 | 0.394 |
|  | MedQA | 0.841 | 0.893 | 0.870 | 0.875 | 0.864 |
|  | OBQA | 0.966 | 0.979 | 0.990 | 0.990 | 0.989 |
|  | Physics | 0.818 | 0.851 | 0.908 | 0.918 | 0.917 |
|  | Algebra | 0.587 | 0.650 | 0.642 | 0.651 | 0.663 |
|  | Chem | 0.682 | 0.774 | 0.797 | 0.805 | 0.795 |
| STEM | Security | 0.911 | 0.916 | 0.933 | 0.927 | 0.922 |
|  | Law | 0.716 | 0.741 | 0.722 | 0.753 | 0.754 |
|  | Ethics | 0.870 | 0.915 | 0.908 | 0.914 | 0.911 |
|  | Econ | 0.634 | 0.638 | 0.717 | 0.714 | 0.725 |
| Social Sciences | Policy | 0.959 | 0.973 | 0.970 | 0.971 | 0.971 |
|  | TQA | 0.892 | 0.926 | 0.865 | 0.869 | 0.872 |
|  | CSQA | 0.831 | 0.868 | 0.835 | 0.841 | 0.837 |
| Commonsense Reasoning | SIQA | 0.851 | 0.872 | 0.886 | 0.888 | 0.887 |
|  | Average | 0.782 | 0.813 | 0.816 | 0.823 | 0.821 |{{< /table-caption >}}
> 🔼 표 6은 GPT-4 모델을 사용하여 절대적 신뢰도 추정 방법(직접 프롬프팅, 자기 일관성 프롬프팅)과 상대적 신뢰도 추정 방법(Elo 등급, TrueSkill, Bradley-Terry)을 비교 분석한 결과를 보여줍니다. TrueSkill 방법을 사용한 상대적 신뢰도 추정이 직접 프롬프팅 방식보다 평균 AUC 기준 4.1% 향상, 자기 일관성 프롬프팅 방식보다 1.0% 향상된 성능을 보였습니다. 표에는 다양한 범주(STEM, 사회과학, 상식 추론)의 데이터셋에 대한 각 방법의 AUC 점수가 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 6: GPT-4 AUCs All Methods. For GPT-4, relative confidences with TrueSkill lead to the best average AUC with a 4.1% improvement over direct prompting and a 1.0% improvement over self-consistency.
> </details>

{{< table-caption >}}
| Model | Direct | Hybrid SC | Elo Rating | TrueSkill | Bradley-Terry |
|---|---|---|---|---|---| 
| Llama 3.1 405B | 0.575 | 0.774 | 0.849 | **0.856** | 0.852 |
| GPT-4 | 0.642 | **0.730** | 0.708 | 0.719 | 0.713 |
| Gemini 1.5 Pro | 0.627 | 0.700 | 0.689 | **0.713** | 0.712 |
| GPT-4o | 0.698 | **0.774** | 0.762 | 0.763 | 0.758 |
| Claude 3.5 Sonnet | 0.685 | **0.726** | 0.711 | 0.713 | 0.713 |
| Average Across Models | 0.645 | 0.741 | 0.744 | **0.753** | 0.749 |{{< /table-caption >}}
> 🔼 표 7은 다섯 개의 최첨단 언어 모델에 대해 절대적 신뢰도 추정 방법(직접 프롬프트, 자기 일관성 프롬프팅)과 상대적 신뢰도 추정 방법(Elo 등급, TrueSkill, Bradley-Terry)을 비교하여 AUROC(Area Under the Receiver Operating Characteristic Curve) 성능을 보여줍니다. TrueSkill을 사용한 상대적 신뢰도 추정이 두 가지 절대적 신뢰도 방법보다 평균적으로 더 높은 AUROC를 기록했으며, 직접 프롬프트 방식보다 10.8%, 자기 일관성 프롬프트 방식보다 1.2% 향상되었습니다. 다섯 개 모델 중 두 개 모델에서는 TrueSkill을 사용한 상대적 신뢰도 추정이 가장 높은 AUROC를 달성했습니다. 이 표는 상대적 신뢰도 추정 방법의 우수성을 보여주는 증거입니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Model AUROCs. Relative confidences with TrueSkill lead to the best average AUROC for 2 out of 5 models, and a 10.8% gain over direct prompting and a 1.2% gain over self-consistency across all models.
> </details>

{{< table-caption >}}
| Elo Rating |  |  | TrueSkill |  |  |  | Bradley-Terry |  |
|---|---|---|---|---|---|---|---|---|---|
| Initial Score | K | # iterations | μ | σ | β | τ | max # iterations | λ |
|---|---|---|---|---|---|---|---|---|---|
| 1000 | 400 | 1 | 25.0 | μ/3.0 | μ/6.0 | μ/300.0 | 5 | 0.01 |{{< /table-caption >}}
> 🔼 표 8은 논문의 4.2절 '순위 집계'에서 사용된 세 가지 순위 집계 알고리즘(Elo 등급, TrueSkill, Bradley-Terry)의 하이퍼파라미터 값을 보여줍니다. 각 알고리즘에 대한 초기값, 반복 횟수, 정규화 상수 등의 값이 제시되어 있습니다. 이 표는 각 알고리즘의 하이퍼파라미터를 조정하여 최적의 결과를 얻기 위한 과정을 보여주는 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Rank Aggregation Hyperparameter Values.
> </details>

{{< table-caption >}}
| Algorithm | Parameter | Values |
|---|---|---|
| Elo Rating | # iters | [1-20] |
| TrueSkill | σ | [μ/3.0, μ/2.5, μ/2.2, μ/2.0] |
|  | β | [μ/6.0, μ/5.0, μ/4.0, μ/3.0] |
|  | τ | [μ/300.0, μ/250.0, μ/200.0, μ/150.0] |
| Bradley-Terry | max # iters | [1-20] |{{< /table-caption >}}
> 🔼 표 9는 논문의 4.2절 '순위 집계' 에서 다루는 순위 집계 알고리즘(Elo, TrueSkill, Bradley-Terry)의 하이퍼파라미터 범위를 보여줍니다. 각 알고리즘의 하이퍼파라미터별로 여러 값들을 테스트하여 최적의 성능을 찾기 위한 범위를 지정하고 있습니다.  각 범위는 실험을 통해 결정되었으며, 데이터셋의 크기나 모델의 특성에 따라 조정될 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Rank Aggregation Hyperparameter Ranges.
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
{{< /gallery >}}