---
title: "ARR: Question Answering with Large Language Models via Analyzing, Retrieving, and Reasoning"
summary: "ARR 프롬프팅 기법을 통해 LLM의 질문 응답 성능을 향상시켰습니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Question Answering", "🏢 University of British Columbia",]
showSummary: true
date: 2025-02-07
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.04689 {{< /keyword >}}
{{< keyword icon="writer" >}} Yuwei Yin et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-10 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.04689" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.04689" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/arr-question-answering-with-large-language" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)은 다양한 질문응답 과제에서 놀라운 성능을 보이지만, 복잡한 추론이 필요한 질문에는 어려움을 겪습니다. 기존의 제로샷 체인-오브-토크(CoT) 프롬프팅은 추론을 향상시키지만, 모호하고 일반적인 지침만 제공합니다.  본 논문에서는 이러한 문제를 해결하기 위해 ARR이라는 새로운 제로샷 프롬프팅 기법을 제안합니다.

ARR은 질문 분석, 관련 정보 검색, 단계적 추론의 세 단계를 명시적으로 통합하여 LLM의 추론 과정을 개선합니다.  다양한 질문응답 데이터셋과 LLM 모델에 대한 실험 결과는 ARR이 기존 방법보다 성능이 우수함을 보여줍니다. 특히, 의도 분석 단계가 중요한 역할을 한다는 것을 밝혀냈으며, 모델 크기, LLM 시리즈, 생성 설정 등 다양한 조건에서의 추가 실험을 통해 ARR의 효율성, 강건성, 일반화 가능성을 확인했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} ARR 프롬프팅 기법은 질문 분석, 정보 검색, 단계적 추론의 3단계를 명시적으로 통합하여 LLM의 추론 능력을 향상시킵니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 다양한 모델과 데이터셋에 대한 실험 결과는 ARR의 효과와 일반화 가능성을 보여줍니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 의도 분석이 ARR의 성능 향상에 중요한 역할을 합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대규모 언어 모델(LLM)의 질문 응답 능력 향상**에 중요한 기여를 합니다. 기존의 제로샷 추론 방식의 한계를 극복하고, 질문 분석, 정보 검색, 단계적 추론의 세 단계를 명시적으로 통합한 ARR 프롬프팅 기법을 제시하여 LLM의 추론 성능을 향상시켰습니다. **다양한 모델과 데이터셋에 대한 실험 결과**는 ARR의 효과와 일반화 가능성을 보여주며, 향후 LLM 연구의 새로운 방향을 제시합니다. 특히, 의도 분석의 중요성을 강조하고 있으며, 다양한 설정에서의 추가 실험은 ARR의 강건성과 적응력을 확인시켜줍니다. 이는 **LLM 기반 질문 응답 시스템 개발**에 직접적인 영향을 미치며, 관련 분야 연구자들에게 귀중한 통찰력을 제공합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.04689/x1.png)

> 🔼 그림 1은 ARR(Analyzing, Retrieving, Reasoning)의 개념을 보여줍니다. 질문에 답하기 위해서는 질문의 의도를 분석하고, 관련 정보를 검색하고, 단계적으로 추론하는 세 가지 단계가 필요하다는 것을 보여주는 개념도입니다.  단순히 답을 찾는 것이 아니라, 질문 분석, 정보 탐색, 추론 과정을 거쳐 논리적으로 답을 도출하는 ARR의 핵심 개념을 시각적으로 설명합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: ARR motivation. To answer a question, we often need to analyze the question’s intent, retrieve relevant information, and reason step by step.
> </details>





{{< table-caption >}}
| QA Dataset | Split | # Item | # Token | # Class |
|---|---|---|---|---|
| BoolQ | Valid | 3,270 | 145 | 2 |
| LogiQA | Test | 651 | 192 | 4 |
| CSQA | Valid | 1,221 | 43 | 5 |
| SIQA | Valid | 1,954 | 51 | 3 |
| SciQ | Test | 1,000 | 132 | 4 |
| OBQA | Test | 500 | 55 | 4 |
| ARC | Test | 3,548 | 59 | 4 |
| BBH | Test | 5,281 | 112 | 2–18 |
| MMLU | Test | 13,842 | 108 | 4 |
| MMLU-Pro | Test | 12,032 | 186 | 10 |{{< /table-caption >}}

> 🔼 이 표는 논문에서 사용된 10개의 다중 선택 질문응답(MCQA) 데이터셋의 통계를 보여줍니다.  각 데이터셋에 대해 질문 옵션의 개수(# Class), 평가에 사용된 데이터 항목의 총 개수(# Item), 그리고 LLaMA 토크나이저로 토큰화했을 때 각 인스턴스(제로샷 프롬프트 포함)의 평균 토큰 수(# Token)가 제시되어 있습니다. 이 정보는 다양한 MCQA 작업에 걸친 실험 결과를 이해하는 데 중요한 맥락을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: QA dataset statistics. “# Class” is the number of options m𝑚mitalic_m, “# Item” is the total number of data items for evaluation, and “# Token¯¯# Token\overline{\text{\# Token}}over¯ start_ARG # Token end_ARG” is the average number of tokens per instance (zero-shot prompt), tokenized by the LLaMA Dubey et al. (2024) tokenizer.
> </details>





### In-depth insights


#### ARR Prompting
ARR 프롬프팅은 질문에 대한 답변을 도출하기 위해 **분석(Analyzing), 검색(Retrieving), 추론(Reasoning)**의 세 가지 단계를 명시적으로 통합하는 제로샷 프롬프팅 방법입니다.  이는 기존의 CoT 프롬프팅보다 구체적이고 효과적인 가이드라인을 제공하여 LLM의 추론 능력을 향상시키는 것을 목표로 합니다. **특히 질문 의도 분석(intent analysis)의 중요성을 강조**하며, 이를 통해 LLM이 관련 정보를 효과적으로 검색하고 단계적인 추론을 수행할 수 있도록 돕습니다. 다양한 QA 작업에 대한 실험 결과, ARR 프롬프팅은 기준 모델 및 CoT 프롬프팅을 꾸준히 능가하며, 각 구성 요소의 독자적인 기여를 입증합니다.  **모델 크기, LLM 시리즈 및 생성 설정에 따른 광범위한 평가를 통해 ARR의 효과, 견고성 및 일반화 가능성을 확인**했습니다. 이는 제로샷 설정에서 복잡한 질문에 대한 LLM의 응답 능력을 향상시키는 데 유용한 전략을 제시합니다.

#### Ablation Analysis
**절제 분석(Ablation Analysis)**는 주어진 모델 또는 시스템에서 특정 구성 요소의 중요성을 평가하기 위해 사용되는 중요한 기법입니다. 본 논문에서는 **ARR(Analyzing, Retrieving, and Reasoning)**이라는 제로샷 프롬프팅 방법의 효과를 입증하기 위해 절제 분석을 수행했습니다. 각 구성 요소(분석, 검색, 추론)를 제거하거나 비활성화하여 성능 변화를 측정함으로써 각 구성요소의 기여도와 상호작용을 정확하게 파악할 수 있었습니다.  **분석 단계의 중요성이 특히 두드러졌으며**, 분석 단계만을 사용한 경우에도 기준 모델 및 CoT(Chain-of-Thought) 프롬프팅보다 뛰어난 성능을 보였습니다. 이는 질문의 의도를 정확히 파악하는 것이 효과적인 질문응답에 매우 중요하다는 점을 시사합니다.  **절제 분석 결과는 ARR의 강점과 각 구성 요소의 상호 작용에 대한 깊이 있는 이해를 제공하며**,  ARR의 효과와 견고성을 더욱 확실하게 입증하는 데 중요한 역할을 합니다.

#### Generalizability Test
본 논문에서 "일반화 가능성 검정"이라는 제목의 섹션은 제시되지 않았지만, 만약 있다면 이는 제시된 방법론인 ARR(Analyzing, Retrieving, Reasoning)의 **범용성**과 **견고성**을 평가하는 데 초점을 맞출 것입니다.  다양한 모델 크기, LLM 시리즈, 생성 설정 등의 **다양한 조건** 하에서 ARR의 성능을 평가하여, 특정 조건에 국한되지 않고 **광범위한 상황**에서도 효과적임을 보여주는 데 목적이 있을 것입니다.  **다양한 데이터셋**에 대한 실험 결과를 통해 ARR이 특정 데이터셋에 과적합되지 않고, **일반적인 질문 응답 과제**에도 적용 가능함을 보여주는 것이 중요할 것입니다.  또한, **소규모 데이터**를 사용한 몇-샷 학습 환경에서의 성능을 평가하여,  데이터 부족 상황에서도 ARR이 효과적인지 확인하는 것이 포함될 수 있습니다.  결과적으로, 이 검정은 ARR의 **실용성**을 강조하고, 다양한 상황에서의 적용 가능성을 제시하는 데 기여할 것입니다.

#### Limitations
이 논문의 "한계" 섹션에서는 연구의 제한점을 솔직하게 인정하고 있습니다. **ARR 프롬프팅 기법의 다양한 변형이나 다른 표현 방식을 탐구하지 않았다**는 점을 지적하며, 이러한 요소가 성능에 미치는 영향을 추가적으로 분석할 필요가 있음을 시사합니다. 또한, **계산 자원의 제약으로 인해 80억 파라미터 이하의 오픈-웨이트 LLM에만 집중**했다는 점을 밝히고, 더 큰 모델에 대한 연구 확장의 필요성을 언급합니다.  **생성된 추론의 반복성과 중복성 문제** 역시 지적하며, 이를 해결하기 위한 동적 중단 전략이나 후처리 과정을 고려할 수 있음을 제안합니다.  즉, 이 논문은 자체적인 한계를 명확히 인지하고 있으며, 후속 연구를 위한 방향을 제시함으로써 연구의 신뢰성을 높이고 있습니다.  **추가적으로, 더욱 다양한 LLM 아키텍처나 생성 설정에 대한 실험을 수행하지 않은 점**도 잠재적인 한계로 볼 수 있습니다.

#### Future Work
본 논문에서 제시된 ARR 프롬프팅 기법의 **일반화 가능성 및 강건성을 더욱 높이는 방향**으로 연구를 확장할 수 있습니다.  다양한 크기와 아키텍처의 LLM에 대한 실험을 확대하고, **다양한 언어와 질문 유형**에 대한 성능을 평가하여 ARR의 범용성을 입증할 수 있습니다. 또한, **리트리벌 메커니즘의 개선**을 통해 관련 정보 검색의 정확성과 효율성을 향상시키고, **추론 과정의 투명성을 높이는 연구**를 통해 ARR의 해석 가능성을 개선하여 신뢰도를 높일 수 있습니다.  **다른 프롬프팅 기법들과의 비교 연구**를 통해 ARR의 우수성을 더욱 명확히 밝히는 것도 중요한 후속 연구 과제입니다.  **오류 분석 및 수정 메커니즘**을 도입하여 ARR의 성능을 추가적으로 개선하는 방안에 대한 연구도 필요합니다. 마지막으로, **실제 응용 환경**에서 ARR의 효용성을 검증하는 실증 연구를 진행하여 실용적인 가치를 제시하는 것도 중요한 미래 연구 과제입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.04689/x2.png)

> 🔼 이 그림은 대규모 언어 모델(LLM)을 사용한 질문 답변 과정을 보여줍니다.  먼저, 모델은 주어진 지문(passage), 질문(question), 그리고 선택지(options)를 입력받아 추론 과정(reasoning generation)을 거쳐 추론 결과(rationale)를 생성합니다.  그런 다음, 모델은 생성된 추론 결과와 각 선택지를 조합하여 언어 모델링 손실(language modeling loss)을 계산하고, 손실 값이 가장 작은 선택지를 최종 답변으로 선택합니다.  즉, 모델이 논리적 추론 과정을 거쳐 최적의 답변을 도출하는 과정을 단계별로 시각화한 것입니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Question answering with LLMs. We first obtain rationale risubscript𝑟𝑖r_{i}italic_r start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT by reasoning generation and then select the optimal option via evaluating the language modeling losses of different context-option combinations.
> </details>



![](https://arxiv.org/html/2502.04689/x3.png)

> 🔼 본 그림은 모델 크기가 커짐에 따라 질문 답변(QA) 성능이 어떻게 변하는지 보여줍니다.  LLaMA3-Chat 모델의 크기(1B, 3B, 8B 파라미터)가 커질수록 QA 정확도가 향상되는 경향을 보여줍니다. 이는 더 큰 모델이 더 나은 성능을 보인다는 것을 시각적으로 보여주는 그래프입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Model size experiments. The trend of QA performance changes as the model becomes larger.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | Reading |  | Commonsense |  | World Knowledge |  |  | Multitask Understanding |  |  | Avg. |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|  | BoolQ | LogiQA | CSQA | SIQA | SciQ | OBQA | ARC | BBH | MMLU | MMLU-Pro |  |
| Baseline | 84.16 | 35.79 | 72.97 | 69.55 | 85.90 | 72.20 | 82.59 | 52.19 | 60.67 | 38.75 | 65.48 |
| CoT | 84.65 | 38.10 | 73.71 | 68.12 | 93.70 | 78.20 | 84.31 | 58.40 | 62.08 | 40.10 | 68.14 |
| **ARR** | **86.33** | **39.02** | **74.94** | **70.98** | **94.40** | **80.00** | **84.84** | **59.01** | **63.51** | **42.72** | **69.58** |{{< /table-caption >}}
> 🔼 표 2는 LLaMA3-8B-Chat 모델을 사용하여 다양한 객관식 질문응답(QA) 데이터셋에서 제로샷 질문응답 성능을 보여줍니다. 세 가지 다른 접근 방식을 비교합니다. (1) 기준선: ϕ는 'Answer:'입니다. (2) CoT(Kojima et al., 2022): ϕ는 'Answer: Let’s think step by step.'입니다. (3) ARR: 질문 의도 분석, 정보 검색, 단계별 추론을 유도하는 제안된 방법입니다.  각 방법은 정확도(%)로 평가됩니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Main experiments. The zero-shot performance (Accuracy %) of the LLaMA3-8B-Chat model on various multiple-choice QA datasets using different answer trigger sentences ϕitalic-ϕ\phiitalic_ϕ. (1) Baseline: ϕitalic-ϕ\phiitalic_ϕ is “Answer:”; (2) CoT Kojima et al. (2022): ϕitalic-ϕ\phiitalic_ϕ is “Answer: Let’s think step by step.”; (3) ARR: our method that elicits intent analyzing, information retrieving, and step-by-step reasoning.
> </details>

{{< table-caption >}}
|   | **A** | **R** | **R** | Answer Trigger Sentence <math display="inline">ϕ</math> |
|---|---|---|---|---| 
| ➀ | ✔ | ✔ | ✔ | Answer: Let’s analyze the intent of the question, find relevant information, and answer the question with step-by-step reasoning. |
| ➁ | ✔ |  |  | Answer: Let’s analyze the intent of the question, and answer the question. |
| ➂ |  | ✔ |  | Answer: Let’s find relevant information, and answer the question. |
| ➃ |  |  | ✔ | Answer: Let’s answer the question with step-by-step reasoning. |
| ➄ |  |  |  | Answer: |{{< /table-caption >}}
> 🔼 표 3은 ARR(Analyzing, Retrieving, Reasoning) 방법의 각 구성 요소(분석, 검색, 추론)의 효과를 평가하기 위한 ablation study에 사용된 answer trigger sentence들을 보여줍니다.  다섯 가지 변형된 answer trigger sentence (①~⑤)가 제시되어 있으며, 각각 분석, 검색, 추론 중 어떤 요소를 포함하고 있는지 확인할 수 있습니다.  ①은 ARR의 모든 요소를 포함한 완전한 형태이고, ②, ③, ④는 각각 분석, 검색, 추론 요소만을 포함하고, ⑤는 기준선(Baseline) 방법으로 어떤 trigger sentence도 사용하지 않는 경우를 나타냅니다. 이를 통해 각 구성 요소가 ARR의 성능 향상에 미치는 영향을 개별적으로 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Ablation study prompts. The answer trigger sentences ϕitalic-ϕ\phiitalic_ϕ used in different ARR ablation study settings.
> </details>

{{< table-caption >}}
| | **Ablation** |  |  | **Reading** |  | **Commonsense** |  | **World Knowledge** |  | **Multitask Understanding** |  | **Avg.** |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|  | **A** | **R** | **R** | **BoolQ** | **LogiQA** | **CSQA** | **SIQA** | **SciQ** | **OBQA** | **ARC** | **BBH** | **MMLU** | **MMLU-Pro** |  |
| ➀ | ✔ | ✔ | ✔ | **86.33** | **39.02** | 74.94 | **70.98** | 94.40 | 80.00 | 84.84 | **59.01** | 63.51 | 42.72 | **69.58** |
| ➁ | ✔ |  |  | 86.09 | 38.40 | **75.76** | 70.78 | 94.30 | **86.80** | **85.83** | 57.08 | 63.66 | 42.54 | **70.12** |
| ➂ |  | ✔ |  | 85.35 | 37.79 | 75.59 | 68.01 | 92.80 | 81.20 | 85.33 | 58.27 | **63.73** | **43.08** | 69.12 |
| ➃ |  |  | ✔ | 85.87 | 38.86 | 74.53 | 68.01 | **94.50** | 82.60 | 85.03 | 58.96 | 61.77 | 41.11 | 69.12 |
| ➄ |  |  |  | 84.16 | 35.79 | 72.97 | 69.55 | 85.90 | 72.20 | 82.59 | 52.19 | 60.67 | 38.75 | 65.48 |{{< /table-caption >}}
> 🔼 표 4는 제안된 ARR 프롬프트의 각 구성 요소(분석, 검색, 추론)의 효과를 분석하기 위한 추가 실험 결과를 보여줍니다.  LLaMA3-8B-Chat 모델을 사용하여 다양한 다지선다형 질의응답(QA) 데이터셋에서 여러 가지 다른 응답 트리거 문장(φ)을 사용하여 정확도를 측정했습니다.  표는 각 구성 요소의 기여도를 개별적으로 평가하고 전체 ARR 프롬프트의 성능에 대한 통찰력을 제공합니다.  각 구성 요소의 독립적인 효과와 세 가지 구성 요소를 모두 포함한 전체 ARR 프롬프트의 효과를 비교하여 ARR의 효과를 더욱 자세히 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Ablation study results. The accuracy scores (%) of the LLaMA3-8B-Chat model on various multiple-choice QA datasets using different answer trigger sentences ϕitalic-ϕ\phiitalic_ϕ (Analyzing, Retrieving, and Reasoning).
> </details>

{{< table-caption >}}
| Task Input | Fact: the summer solstice is on June 21st in the northern hemisphere. Question: The summer solstice in the northern hemisphere is four months before (A) May  (B) July  (C) April  (D) October | 
|---|---| 
| Baseline  | Answer: | 
| Reasoning  | (B) July. Explanation: The summer solstice is the longest day of the year and marks the beginning of summer. It is four months before the beginning of winter. The beginning of winter is in December, so the summer solstice is in June. Therefore, the summer solstice is four months before July. | 
| CoT  | Answer: Let’s think step by step. | 
| Reasoning  | The summer solstice is on June 21st. If we count four months before that, we get March 21st. March is the third month of the year, so the answer is (C). April is the fourth month, May is the fifth month, and October is the tenth month. None of these months is four months before June. July is the seventh month, which is five months after June, so it is not the correct answer either. The correct answer is (C). | 
| ARR  | Answer: Let’s analyze the intent of the question, find relevant information, and answer the question with step-by-step reasoning. | 
| Reasoning  | The question asks for the month that is four months after the summer solstice. The summer solstice is on June 21st. Four months after June 21st is October 21st. Therefore, the correct answer is (D) October. | {{< /table-caption >}}
> 🔼 본 표는 OpenBookQA 데이터셋의 질문 하나에 대한 세 가지 제로샷 프롬프팅 방법(Baseline, CoT, ARR)의 결과를 비교 분석한 사례 연구입니다.  ARR 방법은 질문의 의도를 정확히 파악하고 관련 정보를 효과적으로 검색하여 단계별 추론을 통해 정답을 도출하지만, Baseline과 CoT는 질문의 의도를 오해하거나 잘못된 추론으로 인해 정답을 찾지 못하는 모습을 보여줍니다.  이를 통해 ARR 방법의 우수성과 Baseline 및 CoT 방법의 한계점을 보다 명확히 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Case study. An instance from the OpenBookQA dataset, where our ARR method correctly answers the question but the Baseline and CoT methods fail because of intent misunderstanding or faulty reasoning.
> </details>

{{< table-caption >}}
| Size | Method | BBH | MMLU | MMLU-Pro | Avg. |
|---|---|---|---|---|---| 
| 1B | Baseline | 35.88 | 43.27 | 21.62 | 33.59 |
|  | CoT | 36.30 | 41.10 | 22.74 | 33.38 |
|  | **ARR** | **39.02** | 42.70 | **23.49** | **35.07** |
| 3B | Baseline | 45.65 | 48.26 | 30.88 | 41.60 |
|  | CoT | 46.89 | 46.80 | 30.03 | 41.24 |
|  | **ARR** | **51.97** | **52.82** | **33.39** | **46.06** |
| 8B | Baseline | 52.19 | 60.67 | 38.75 | 50.54 |
|  | CoT | 58.40 | 62.08 | 40.10 | 53.53 |
|  | **ARR** | **59.01** | **63.51** | **42.72** | **55.08** |{{< /table-caption >}}
> 🔼 본 표는 LLaMA3-Chat 모델의 크기별 성능을 다양한 다지선다형 질의응답(QA) 데이터셋에서 평가한 결과를 보여줍니다.  'zero-shot' 방식으로 평가되었으며, 모델 크기가 커짐에 따라 정확도가 어떻게 변하는지 보여주는 표입니다.  다양한 크기의 모델(1B, 3B, 8B)을 사용하여, 각 모델의 크기에 따른 질의응답 성능의 변화 추세를 보여주고,  모델 크기가 질의응답 성능에 미치는 영향을 분석하는 데 유용한 정보를 제공합니다.  표에는 각 모델 크기별로, 다양한 QA 데이터셋에서 달성한 정확도(Accuracy %)가 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Model size experiments. The zero-shot performance (Accuracy %) of LLaMA3-Chat models of different sizes on multiple-choice QA datasets.
> </details>

{{< table-caption >}}
| Series | Method | BBH | MMLU | MMLU-Pro | Avg. |
|---|---|---|---|---|---| 
| Qwen | Baseline | 39.21 | 48.36 | 32.35 | 39.97 |
|  | CoT | 36.66 | 44.91 | 29.26 | 36.94 |
|  | **ARR** | **40.50** | **50.34** | **39.10** | **43.31** |
| Gemma | Baseline | 40.09 | 45.46 | 23.45 | 36.33 |
|  | CoT | 44.39 | 47.17 | 26.20 | 39.25 |
|  | **ARR** | **45.31** | **50.73** | **26.98** | **41.01** |
| Mistral | Baseline | 46.27 | 55.61 | 30.68 | 44.19 |
|  | CoT | 53.42 | 61.16 | 34.73 | 49.77 |
|  | **ARR** | **53.55** | **61.49** | **35.21** | **50.08** |{{< /table-caption >}}
> 🔼 이 표는 여러가지 대규모 언어 모델(LLM) 시리즈의 7B-Chat 모델을 사용하여 다양한 객관식 질문 답변(QA) 데이터셋에서 달성한 제로샷 성능(정확도 %)을 보여줍니다.  각 모델의 여러 QA 데이터셋에 대한 정확도를 비교하여 모델의 일반화 성능을 평가합니다.  LLM 시리즈 간의 성능 차이를 분석하여 특정 모델 아키텍처가 특정 QA 작업에 더 적합한지 여부를 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: LLM series experiments. The zero-shot performance (Accuracy %) of 7B-Chat models of different LLM series on multiple-choice QA datasets.
> </details>

{{< table-caption >}}
| Temp. | Method | BBH | MMLU | MMLU-Pro | Avg. |
|---|---|---|---|---|---| 
| 0.0 | Baseline | 52.19 | 60.67 | 38.75 | 50.54 |
| 0.0 | CoT | 58.40 | 62.08 | 40.10 | 53.53 |
| 0.0 | **ARR** | **59.01** | **63.51** | **42.72** | **55.08** |
| 0.5 | Baseline | 50.19 | 59.35 | 36.88 | 48.81 |
| 0.5 | CoT | 56.58 | 60.82 | 37.82 | 51.74 |
| 0.5 | **ARR** | **58.87** | **62.87** | **42.64** | **54.79** |
| 1.0 | Baseline | 46.33 | 54.80 | 33.10 | 44.74 |
| 1.0 | CoT | 51.46 | 55.57 | 33.00 | 46.68 |
| 1.0 | **ARR** | **52.90** | **56.58** | **36.73** | **48.74** |
| 1.5 | Baseline | 40.84 | 45.03 | 26.85 | 37.57 |
| 1.5 | CoT | 42.53 | 44.85 | 25.61 | 37.66 |
| 1.5 | **ARR** | **42.65** | **45.16** | **27.44** | **38.42** |{{< /table-caption >}}
> 🔼 본 표는 LLaMA3-8B-Chat 모델을 사용하여 다양한 생성 온도(기본값: 0.0)에서 여러 개의 다중 선택 QA 데이터셋에 대해 측정된 제로샷 성능(정확도 %)을 보여줍니다.  다양한 생성 온도에서 모델의 성능 변화를 비교 분석하여 생성 온도가 모델 성능에 미치는 영향을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Generation temperature experiments. The zero-shot performance (Accuracy %) of the LLaMA3-8B-Chat model on multiple-choice QA datasets using different generation temperatures (default: 0.0).
> </details>

{{< table-caption >}}
| Shot | Method | BBH | MMLU | MMLU-Pro | Avg. |
|---|---|---|---|---|---| 
| 0 | Baseline | 52.19 | 60.67 | 38.75 | 50.54 |
| 0 | CoT | 58.40 | 62.08 | 40.10 | 53.53 |
| 0 | **ARR** | **59.01** | **63.51** | **42.72** | **55.08** |
| 1 | Baseline | 35.68 | 44.80 | 28.62 | 36.37 |
| 1 | **CoT** | **47.39** | 48.36 | 31.07 | 42.27 |
| 1 | **ARR** | 47.22 | **49.29** | **34.33** | **43.61** |
| 3 | Baseline | 34.39 | 42.08 | 25.92 | 34.13 |
| 3 | **CoT** | **42.84** | 48.21 | 26.69 | 39.25 |
| 3 | **ARR** | 40.19 | **49.68** | **37.04** | **42.30** |
| 5 | Baseline | 34.11 | 41.14 | 25.76 | 33.67 |
| 5 | CoT | 39.92 | 47.48 | 26.12 | 37.84 |
| 5 | **ARR** | **40.68** | **49.19** | **36.62** | **42.16** |{{< /table-caption >}}
> 🔼 본 표는 LLaMA3-8B-Chat 모델을 사용하여 다양한 여러 선택지 질문 답변 데이터셋에서 1, 3, 5개의 몇몇 예시를 사용하여 얻은 결과를 보여줍니다. 각 예시는 추론 과정을 포함합니다.  표는 각 실험 설정에서 모델의 정확도(%)를 보여줍니다.  이는 몇몇 샷 학습이 모델 성능에 미치는 영향을 평가하기 위한 실험 결과입니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Few-shot experiments. The few-shot performance (Accuracy %) of the LLaMA3-8B-Chat model on multiple-choice QA datasets using 1, 3, and 5 few-show examples with rationales.
> </details>

{{< table-caption >}}
| QA Datasets | URL |
|---|---| 
| BoolQ Clark et al. (2019) | <https://huggingface.co/datasets/aps/super_glue> |
| LogiQA Liu et al. (2020) | <https://huggingface.co/datasets/EleutherAI/logiqa> |
| CSQA Talmor et al. (2019) | <https://huggingface.co/datasets/tau/commonsense_qa> |
| SIQA Sap et al. (2019) | <https://huggingface.co/datasets/allenai/social_i_qa> |
| SciQ Welbl et al. (2017) | <https://huggingface.co/datasets/allenai/sciq> |
| OBQA Mihaylov et al. (2018) | <https://huggingface.co/datasets/allenai/openbookqa> |
| ARC Clark et al. (2018) | <https://huggingface.co/datasets/allenai/ai2_arc> |
| BBH Suzgun et al. (2023) | <https://huggingface.co/datasets/lukaemon/bbh> |
| MMLU Hendrycks et al. (2021) | <https://huggingface.co/datasets/hails/mmlu_no_train> |
| MMLU-Pro Wang et al. (2024b) | <https://huggingface.co/datasets/TIGER-Lab/MMLU-Pro> |{{< /table-caption >}}
> 🔼 본 논문의 표 10은 논문에서 사용된 10개의 질의응답(QA) 데이터셋의 URL 링크를 보여줍니다. 각 데이터셋은 다양한 종류의 질문과 답변을 포함하고 있으며, 독해, 상식 추론, 세계 지식, 다중 작업 이해 등 다양한 측면에서 언어 모델의 능력을 평가하는 데 사용됩니다.  표에는 데이터셋 이름과 해당 URL 링크가 함께 제시되어,  연구의 재현성과 투명성을 높입니다.
> <details>
> <summary>read the caption</summary>
> Table 10: The URL links of adopted QA datasets.
> </details>

{{< table-caption >}}
| LLM Series | Size | Type | URL |
|---|---|---|---|
| LLaMA3 [Dubey et al. (2024)] | 8B | Chat | https://huggingface.co/meta-llama/Llama-3.1-8B-Instruct |
|  | 3B | Chat | https://huggingface.co/meta-llama/Llama-3.2-3B-Instruct |
|  | 1B | Chat | https://huggingface.co/meta-llama/Llama-3.2-1B-Instruct |
| Qwen2.5 [Yang et al. (2024)] | 7B | Chat | https://huggingface.co/Qwen/Qwen2.5-7B-Instruct |
| Gemma [Team et al. (2024b, c)] | 7B | Chat | https://huggingface.co/google/gemma-7b-it |
| Mistral [Jiang et al. (2023)] | 7B | Chat | https://huggingface.co/mistralai/Mistral-7B-Instruct-v0.3 |{{< /table-caption >}}
> 🔼 표 11은 논문에서 사용된 언어 모델과 토크나이저의 URL 링크를 보여줍니다.  LLaMA3, Qwen2.5, Gemma, Mistral 모델 시리즈와 그에 해당하는 토크나이저의 출처를 확인할 수 있습니다. 각 모델의 크기(Size)와 종류(Type), 그리고 URL 링크가 포함되어 있어, 독자들이 해당 모델과 토크나이저에 대한 추가 정보를 쉽게 찾을 수 있도록 합니다.
> <details>
> <summary>read the caption</summary>
> Table 11: The URL links of models and tokenizers.
> </details>

{{< table-caption >}}
| Task Input | Passage: Contour feathers are not uniformly distributed on the skin of the bird except in some groups such as the penguins, ratites and screamers. In most birds the feathers grow from specific tracts of skin called pterylae; between the pterylae there are regions which are free of feathers called apterylae (or apteria). Filoplumes and down may arise from the apterylae. The arrangement of these feather tracts, pterylosis or pterylography, varies across bird families and has been used in the past as a means for determining the evolutionary relationships of bird families. Question: Do penguins have feathers arising from the epidermis? | Baseline | Answer: | Reasoning | No, penguins have feathers arising from specific tracts of skin called pterylae. The pterylae are the areas of skin where the feathers grow. The pterylae are not uniformly distributed on the skin of the penguin. The feathers grow from the pterylae, and the areas between the pterylae are free of feathers and are called apterylae. The arrangement of these feather tracts, pterylosis or pterylography, varies across bird families. In penguins, the feathers are uniformly distributed on the skin, but they arise from specific tracts of skin called pterylae. The feathers do not arise from the epidermis. The epidermis is the outermost layer of the skin, and in most birds, the feathers grow from the dermal layer of the skin, not the epidermis. | CoT | Answer: Let’s think step by step. | Reasoning | Penguins are a group of birds that have feathers uniformly distributed on their skin. The passage states that in most birds, feathers grow from specific tracts of skin called pterylae, and between these tracts, there are regions called apterylae that are free of feathers. However, it also mentions that in some groups, such as penguins, ratites, and screamers, feathers are not uniformly distributed on the skin. This suggests that penguins do not have feathers arising from the epidermis. Therefore, the answer is no. Penguins do not have feathers arising from the epidermis. | ARR | Answer: Let’s analyze the intent of the question, find relevant information, and answer the question with step-by-step reasoning. | Reasoning | The question asks about the distribution of feathers on penguins. The passage states that in most birds, feathers grow from specific tracts of skin called pterylae, but penguins are an exception. The passage does not mention the epidermis, but it does mention that in penguins, feathers are uniformly distributed on the skin. This suggests that feathers in penguins may arise from the epidermis, as there are no specific tracts of skin called pterylae. Therefore, the answer is yes. |{{< /table-caption >}}
> 🔼 본 논문의 표 12는 BoolQ 데이터셋에서 ARR(Analyzing, Retrieving, Reasoning) 방법이 질문에 대해 정답을 제시하지만, 기준 방법(Baseline)과 CoT(Chain-of-Thought) 방법은 실패하는 사례를 보여줍니다.  표는 질문, Baseline과 CoT, 그리고 ARR의 답변 및 추론 과정을 비교하여 각 방법의 강점과 약점을 분석하고, ARR의 효과를 구체적으로 보여주는 예시를 제공합니다.  ARR 방법은 질문의 의도를 분석하고, 관련 정보를 검색하고, 단계별 추론을 통해 정답을 도출하는 과정을 명확하게 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 12: Case study. An instance from the Boolq dataset, where our ARR method correctly answers the question but the Baseline and CoT methods fail.
> </details>

{{< table-caption >}}
| Task Input | Passage: There are five stations set up from west to east along a section of the high-speed railway along the river. | Baseline | Answer: | Reasoning | Answer: (C) Jiushang Station is adjacent to Haoyun Station and west of Haoyun Station; | CoT | Answer: Let’s think step by step. | Reasoning | If Haoyun stands to the east of Jiushang Station, then Haoyun Station is west of Jiushang Station. | ARR | Answer: Let’s analyze the intent of the question, find relevant information, and answer the question with step-by-step reasoning. | Reasoning | The question asks us to determine the correct relationship between the stations based on the given information.  |{{< /table-caption >}}
> 🔼 본 표는 논문의 주요 실험 결과 중 하나인 LogiQA 데이터셋의 질문에 대한 세 가지 방법(Baseline, CoT, ARR)의 응답 결과를 보여줍니다. 특히, ARR 방법만 정답을 맞추고 Baseline과 CoT 방법은 틀린 사례를 제시합니다. 분석 결과에 따르면, 정답이 될 수 있는 역(驛) 순서는 Jiushang-Yinling-Haoyun-Fuyi-Huyao 또는 Yinling-Jiushang-Haoyun-Fuyi-Huyao 두 가지가 존재합니다. 이는 ARR 방법이 질문의 의도를 정확히 파악하고, 관련 정보를 효과적으로 검색하고, 단계적인 추론을 통해 정답에 도달함을 보여주는 대표적인 예시입니다.
> <details>
> <summary>read the caption</summary>
> Table 13: Case study. An instance from the LogiQA dataset, where our ARR method correctly answers the question but the Baseline and CoT methods fail. Analysis: the correct station order can be Jiushang-Yinling-Haoyun-Fuyi-Huyao or Yinling-Jiushang-Haoyun-Fuyi-Huyao.
> </details>

{{< table-caption >}}
| Task Input | Question: What do people aim to do at work? | Baseline | Answer: | Reasoning | 
|---|---|---|---|---| 
| **x<sub>i</sub>** | (A) complete job  (B) learn from each other  (C) kill animals  (D) wear hats  (E) talk to each other | **ϕ<sub>i</sub>** |  | **r<sub>i</sub>** | 
| **Baseline**  |  |  | (B) learn from each other. The best answer is B.  Step 1: Understand the context of the question: The question is asking about the purpose or goal of people at work. Step 2: Analyze the options given Option (A) "complete job" is a task-oriented answer, but it doesn’t necessarily imply learning or personal growth. Option (C) "kill animals" is unrelated to the typical goals of work in most industries. Option (D) "wear hats" is a superficial aspect of work attire and not a goal. Option (E) "talk to each other" is a common aspect of work but doesn’t necessarily imply learning. Step 3: Identify the most appropriate answer: Option (B) "learn from each other" is a goal that aligns with personal and professional development, which is a common aim in many workplaces. It suggests a focus on growth, improvement, and collaboration, which are key aspects of many work environments. The final answer is: B | 
| **CoT** |  | **ϕ<sub>i</sub>** | Answer: Let’s think step by step. | **r<sub>i</sub>** | 
|  |  |  | (B) People go to work to earn a living, but they also go to learn from each other and to be part of a community. Choice (A) is incorrect because people do not go to work to complete a job. They go to work to do a job. Choice (C) is incorrect because people do not go to work to kill animals. Choice (D) is incorrect because people do not go to work to wear hats. Choice (E) is incorrect because people do not go to work to talk to each other. They go to work to do a job. The best answer is B. | 
| **ARR** |  | **ϕ<sub>i</sub>** | Answer: Let’s analyze the intent of the question, find relevant information, and answer the question with step-by-step reasoning. | **r<sub>i</sub>** | 
|  |  |  | The question asks what people aim to do at work. The relevant information is that people go to work to earn a living. The answer is that people aim to complete their jobs at work. Choice (B) is incorrect because people may learn from each other at work, but that is not the main purpose of going to work. Choice (C) is incorrect because people do not go to work to kill animals. Choice (D) is incorrect because people do not go to work to wear hats. Choice (E) is incorrect because people do not go to work to talk to each other. The best answer is A. | {{< /table-caption >}}
> 🔼 본 논문의 표 14는 Commonsense QA 데이터셋의 질문에 대한 답변을 도출하는 과정을 보여주는 사례 연구입니다.  기존의 Baseline 및 CoT 방법은 질문에 대한 정확한 답을 도출하지 못했지만, ARR 방법은 정확한 답변과 함께 단계적인 추론 과정을 제시하여 질문의 의도를 명확히 파악하고 관련 정보를 효과적으로 활용하는 것을 보여줍니다.  이를 통해 ARR 방법의 우수성과 효율성을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 14: Case study. An instance from the Commonsense QA dataset, where our ARR method correctly answers the question but the Baseline and CoT methods fail.
> </details>

{{< table-caption >}}
| Task Input | Context: Alex grew closer to their significant other after they vacationed together. Question: How would Alex feel afterwards? (A) in love  (B) happy  (C) back from vacation | Baseline  | Answer: | Reasoning  | (B) happy Reasoning Skill: Empathy And Perspective Taking This question requires the test-taker to put themselves in Alex’s shoes and understand how they would feel after a positive experience like vacationing with their significant other. The correct answer, "happy", is a natural emotional response to a pleasant experience. The other options are not directly related to the emotional state of Alex after the vacation. "In love" is a more intense and long-term feeling, "back from vacation" is a factual statement rather than an emotional response, and "happy" is the most appropriate answer given the context.  | CoT  | Answer: Let’s think step by step. | Reasoning  | Alex grew closer to their significant other after they vacationed together. This implies that the vacation strengthened their relationship. Therefore, Alex would likely feel happy after the vacation. Reasoning skill: Empathy And Perspective Taking. This question requires the reader to put themselves in Alex’s shoes and understand how they would feel after a positive experience. It also requires the reader to consider the context of the situation and how it would impact Alex’s emotions. The best answer is (B) | ARR  | Answer: Let’s analyze the intent of the question, find relevant information, and answer the question with step-by-step reasoning. | Reasoning  | Step 1: Identify the context of the question. The context is about Alex growing closer to their significant other after a vacation. Step 2: Determine the emotional state of Alex after the vacation. The question asks how Alex would feel afterwards. Step 3: Analyze the relationship between Alex and their significant other. The question implies that the vacation strengthened their bond. Step 4: Determine the emotional state of Alex based on the context. Given that the vacation brought them closer together, it is likely that Alex would feel happy or in love. Step 5: Choose the most appropriate answer. Between "happy" and "in love", "in love" is a more intense emotion that aligns with the context of growing closer to someone. The final answer is: (A) in love. |{{< /table-caption >}}
> 🔼 표 15는 SocialIQA 데이터셋의 한 예시를 보여줍니다. ARR 방법은 질문에 대해 정답을 제시하지만, Baseline 및 CoT 방법은 실패합니다. 분석 결과, Option B도 틀린 답은 아니지만, Option A가  'significant other'라는 맥락을 고려했을 때 더 적절한 답입니다. 즉, 연애 관계임을 고려했을 때 Option A가 더 적합하다는 것을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 15: Case study. An instance from the SocialIQA dataset, where our ARR method correctly answers the question but the Baseline and CoT methods fail. Analysis: Option B is not wrong, but Option A is more appropriate as they are in a romantic relationship (“significant other”).
> </details>

{{< table-caption >}}
| Task Input | Question: Rupture can cause fragments of what to travel via the bloodstream and become lodged in other arteries? | Baseline | Answer: | Reasoning |  | CoT | Answer: Let’s think step by step. | Reasoning |  | ARR | Answer: Let’s analyze the intent of the question, find relevant information, and answer the question with step-by-step reasoning. | Reasoning |  |
|---|---|---|---|---|---|---|---|---|---|---|---|
| $x_{i}$ |  <br> **Question**: Rupture can cause fragments of what to travel via the bloodstream and become lodged in other arteries?<br>**(A)** red blood cells  **(B)** white blood cells  **(C)** plaque  **(D)** enamel | $\phi_{i}$ | Answer: | $r_{i}$ | <br>Rupture of an atherosclerotic plaque can cause fragments of the plaque to travel<br>via the bloodstream and become lodged in other arteries. This is known as an embolus.<br>Choice (B) is incorrect because white blood cells are not typically associated with atherosclerosis.<br>Choice (C) is incorrect because plaque is the substance that ruptures.<br>The best answer is (A). | $\phi_{i}$ | Answer: Let’s think step by step. | $r_{i}$ | <br>The question is asking about the consequences of a rupture, which implies a physical injury or damage to a structure.<br>The correct answer should be related to the physical structure that<br>can be damaged and cause fragments to travel through the bloodstream.<br>Option (A) red blood cells are a type of cell that carries oxygen throughout the body via the bloodstream,<br>and they can be damaged or ruptured in the event of a physical injury or damage to a blood vessel.<br>Option (B) white blood cells are part of the immune system and help fight infections,<br>but they are not a physical structure that can rupture and cause fragments to travel through the bloodstream.<br>Option (C) plaque is a sticky film of bacteria that can cause dental problems,<br>but it’s not a physical structure that can rupture and cause fragments to travel through the bloodstream.<br>Option (D) enamel is a hard, outer layer of teeth,<br>which is not directly related to the bloodstream or arteries.<br>Therefore, the correct answer is (A) red blood cells. | $\phi_{i}$ | Answer: Let’s analyze the intent of the question, find relevant information, and answer the question with step-by-step reasoning. | $r_{i}$ | <br>The question is asking about the consequences of a rupture, which is likely referring to a rupture of an aneurysm or<br>an atherosclerotic plaque. In the context of aneurysms or atherosclerosis, a rupture can lead to the release of fragments into<br>the bloodstream. These fragments can then travel to other parts of the body and become lodged in other arteries,<br>potentially causing blockages or other complications. Considering the options provided, the most relevant choice is (C) plaque,<br>as atherosclerotic plaque is a common cause of arterial blockages and can rupture, releasing fragments into the bloodstream.<br>The other options are not directly related to the consequences of a rupture in the context of aneurysms or atherosclerosis.|{{< /table-caption >}}
> 🔼 표 16은 본 논문에서 제안하는 ARR(Analyzing, Retrieving, Reasoning) 방법이 질문에 대한 답을 정확하게 제시하는 반면, 기준 방법(Baseline)과 CoT(Chain-of-Thought) 방법은 실패하는 사례를 보여줍니다.  SciQ 데이터셋의 질문 하나를 예시로 들어, 세 가지 방법의 추론 과정과 결과를 비교 분석하여 ARR의 우수성을 보여줍니다.  각 방법의 추론 과정을 자세히 분석함으로써 ARR이 질문의 의도를 정확히 파악하고 관련 정보를 효과적으로 검색 및 추론하여 정답을 도출하는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 16: Case study. An instance from the SciQ dataset, where our ARR method correctly answers the question but the Baseline and CoT methods fail.
> </details>

{{< table-caption >}}
| Task Input |  $x_{i}$ | Fact: force causes the speed of an object to decrease. Question: The amount of friction and the speed of an object have what kind of relationship? (A) inverse  (B) reverse  (C) direct  (D) equal | 
|---|---|---|
| Baseline  $ϕ_{i}$ | Answer: | 
| Reasoning $r_{i}$ | (C) Direct Explanation: The more friction an object has, the slower it will move. The less friction an object has, the faster it will move. This is a direct relationship. The amount of friction and the speed of an object are directly related. | 
| CoT $ϕ_{i}$ | Answer: Let’s think step by step. | 
| Reasoning $r_{i}$ | Step 1: Understand the relationship between friction and speed The relationship between friction and speed is that as friction increases, the speed of an object decreases. Step 2: Determine the type of relationship Since an increase in friction leads to a decrease in speed, this is a direct relationship. A direct relationship means that as one variable increases, the other variable also increases. Step 3: Choose the correct answer Based on the understanding of the relationship between friction and speed, the correct answer is (C) direct. | 
| ARR $ϕ_{i}$ | Answer: Let’s analyze the intent of the question, find relevant information, and answer the question with step-by-step reasoning. | 
| Reasoning $r_{i}$ | The question asks about the relationship between the amount of friction and the speed of an object. The relevant information is that force causes the speed of an object to decrease. The intent of the question is to determine the relationship between the amount of friction and the speed of an object. The correct answer is (A) inverse. The amount of friction and the speed of an object have an inverse relationship. The more friction, the slower the object moves. The less friction, the faster the object moves. |{{< /table-caption >}}
> 🔼 표 17은 OpenBookQA 데이터셋의 한 예시를 보여줍니다. ARR 방법은 질문에 대해 정답을 제시하지만, Baseline과 CoT 방법은 실패합니다. 분석 결과, CoT 방법은 직접적인 관계에 대한 올바른 사실을 제시하지만('직접적인 관계는...'), 마찰 증가가 속도 감소로 이어진다는 점에서 '이것은 직접적인 관계이다'라고 잘못 추론합니다. 이는 올바른 사실이 기술된 후에 잘못된 진술이 이루어지기 때문입니다(자기 회귀적 생성으로 인해). 반면 ARR 방법은 의도를 분석하고 관련 정보를 찾은 후 충분한 맥락에 기반하여 추론을 수행합니다.
> <details>
> <summary>read the caption</summary>
> Table 17: Case study. An instance from the OpenBookQA dataset, where our ARR method correctly answers the question but the Baseline and CoT methods fail. Analysis: The CoT method provides a correct fact about the direct relationship (“A direct relationship means that ……\dots…”), but wrongly infers that “this is a direct relationship” from “an increase in friction leads to a decrease in speed.” This is because the wrong statement is made without conditioning on the correct fact that is presented after the statement (due to the autoregressive generation). In contrast, the ARR method performs reasoning based on sufficient context after analyzing the intent and finding relevant information.
> </details>

{{< table-caption >}}
| Task Input | Question: A scientist maps a long region in which earthquakes originate and determines this region is a transform plate boundary. Which evidence would cause the scientist to reevaluate this determination? | Baseline | Answer: | Reasoning |  The best answer is C. Transform plate boundaries are characterized by horizontal motion and faulting, but the faulting is not necessarily extensive. Volcanism is characteristic of divergent and convergent plate boundaries, not transform plate boundaries. Shallow earthquake foci are characteristic of transform plate boundaries. Equal crust densities on opposite sides of the region would indicate that the region is a transform plate boundary. Therefore, (A), (B), and (D) are incorrect. (C) is correct because extensive faulting is characteristic of transform plate boundaries. | CoT | Answer: Let’s think step by step. | Reasoning | Transform plate boundaries are characterized by horizontal motion of the Earth’s crust, which is evidenced by faulting. Volcanism is characteristic of divergent and convergent plate boundaries, not transform plate boundaries. Therefore, (A) is incorrect. Earthquakes at transform plate boundaries can occur at any depth, so (B) is incorrect. (C) is correct because faulting is a characteristic of transform plate boundaries. (D) is incorrect because transform plate boundaries are characterized by horizontal motion of the Earth’s crust, not by equal crust densities. | ARR | Answer: Let’s analyze the intent of the question, find relevant information, and answer the question with step-by-step reasoning. | Reasoning | The question asks for evidence that would cause a scientist to reevaluate the determination that a region is a transform plate boundary. A transform plate boundary is a region where two plates slide past one another horizontally. The evidence that would cause a scientist to reevaluate this determination would be evidence that is characteristic of a different type of plate boundary. A divergent plate boundary is a region where two plates move apart from one another, and a convergent plate boundary is a region where two plates move toward one another. Volcanism is characteristic of a divergent plate boundary, so (A) is correct. |{{< /table-caption >}}
> 🔼 표 18은 본 논문에서 제안하는 ARR(Analyzing, Retrieving, Reasoning) 방법론이 질문응답(QA) 과제에서 기존 방법론(Baseline, CoT)보다 우수한 성능을 보이는 것을 보여주는 사례 연구를 담고 있습니다. ARC 데이터셋의 한 질문에 대한 Baseline, CoT, ARR 세 가지 방법론의 답변 과정을 비교 분석하여 ARR이 질문의 의도를 정확하게 파악하고 논리적인 추론 과정을 거쳐 정답에 도달하는 반면, Baseline과 CoT는 오류를 범하거나 불완전한 추론 과정을 보이는 것을 보여줍니다. 이를 통해 ARR이 질문 분석, 정보 검색, 단계적 추론이라는 세 가지 단계를 명시적으로 통합함으로써 더욱 효과적이고 정확한 질문 응답을 가능하게 함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 18: Case study. An instance from the ARC dataset, where our ARR method correctly answers the question but the Baseline and CoT methods fail.
> </details>

{{< table-caption >}}
<table class="ltx_tabular ltx_align_middle" id="A2.T19.8.8">
<tr class="ltx_tr" id="A2.T19.1.1.1">
<td class="ltx_td ltx_align_right ltx_border_tt ltx_border_t" id="A2.T19.1.1.1.1">
<span class="ltx_text ltx_font_bold" id="A2.T19.1.1.1.1.1">Task Input</span> <math alttext="x_{i}" class="ltx_Math" display="inline" id="A2.T19.1.1.1.1.m1.1"><semantics id="A2.T19.1.1.1.1.m1.1a"><msub id="A2.T19.1.1.1.1.m1.1.1" xref="A2.T19.1.1.1.1.m1.1.1.cmml"><mi id="A2.T19.1.1.1.1.m1.1.1.2" xref="A2.T19.1.1.1.1.m1.1.1.2.cmml">x</mi><mi id="A2.T19.1.1.1.1.m1.1.1.3" xref="A2.T19.1.1.1.1.m1.1.1.3.cmml">i</mi></msub><annotation-xml encoding="MathML-Content" id="A2.T19.1.1.1.1.m1.1b"><apply id="A2.T19.1.1.1.1.m1.1.1.cmml" xref="A2.T19.1.1.1.1.m1.1.1"><csymbol cd="ambiguous" id="A2.T19.1.1.1.1.m1.1.1.1.cmml" xref="A2.T19.1.1.1.1.m1.1.1">subscript</csymbol><ci id="A2.T19.1.1.1.1.m1.1.1.2.cmml" xref="A2.T19.1.1.1.1.m1.1.1.2">𝑥</ci><ci id="A2.T19.1.1.1.1.m1.1.1.3.cmml" xref="A2.T19.1.1.1.1.m1.1.1.3">𝑖</ci></apply></annotation-xml><annotation encoding="application/x-tex" id="A2.T19.1.1.1.1.m1.1c">x_{i}</annotation><annotation encoding="application/x-llamapun" id="A2.T19.1.1.1.1.m1.1d">italic_x start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT</annotation></semantics></math>
</td>
<td class="ltx_td ltx_align_left ltx_border_tt ltx_border_t" id="A2.T19.1.1.1.2">
<span class="ltx_text" id="A2.T19.1.1.1.2.1"></span><span class="ltx_text" id="A2.T19.1.1.1.2.2">
<span class="ltx_tabular ltx_align_middle" id="A2.T19.1.1.1.2.2.1">
<span class="ltx_tr" id="A2.T19.1.1.1.2.2.1.1">
<span class="ltx_td ltx_nopad_r ltx_align_left" id="A2.T19.1.1.1.2.2.1.1.1"><span class="ltx_text ltx_font_bold" id="A2.T19.1.1.1.2.2.1.1.1.1">Question</span>: The following paragraphs each describe a set of three objects arranged in a fixed order.</span></span>
<span class="ltx_tr" id="A2.T19.1.1.1.2.2.1.2">
<span class="ltx_td ltx_nopad_r ltx_align_left" id="A2.T19.1.1.1.2.2.1.2.1">The statements are logically consistent within each paragraph. A fruit stand sells three fruits: peaches, mangoes, and apples.</span></span>
<span class="ltx_tr" id="A2.T19.1.1.1.2.2.1.3">
<span class="ltx_td ltx_nopad_r ltx_align_left" id="A2.T19.1.1.1.2.2.1.3.1"><span class="ltx_text" id="A2.T19.1.1.1.2.2.1.3.1.1" style="color:#0000FF;">The peaches are more expensive than the apples. The mangoes are the cheapest.</span></span></span>
<span class="ltx_tr" id="A2.T19.1.1.1.2.2.1.4">
<span class="ltx_td ltx_nopad_r ltx_align_left" id="A2.T19.1.1.1.2.2.1.4.1"><span class="ltx_text ltx_font_bold" id="A2.T19.1.1.1.2.2.1.4.1.1">(A)</span> The peaches are the second-most expensive</span></span>
<span class="ltx_tr" id="A2.T19.1.1.1.2.2.1.5">
<span class="ltx_td ltx_nopad_r ltx_align_left" id="A2.T19.1.1.1.2.2.1.5.1"><span class="ltx_text ltx_font_bold" id="A2.T19.1.1.1.2.2.1.5.1.1">(B)</span> The mangoes are the second-most expensive</span></span>
<span class="ltx_tr" id="A2.T19.1.1.1.2.2.1.6">
<span class="ltx_td ltx_nopad_r ltx_align_left" id="A2.T19.1.1.1.2.2.1.6.1"><span class="ltx_text ltx_font_bold" id="A2.T19.1.1.1.2.2.1.6.1.1" style="color:#008080;">(C)</span> The apples are the second-most expensive</span></span>
</span></span><span class="ltx_text" id="A2.T19.1.1.1.2.3"></span></td>
</tr>
<tr class="ltx_tr" id="A2.T19.2.2.2">
<td class="ltx_td ltx_align_right ltx_border_t" id="A2.T19.2.2.2.1">
<span class="ltx_text ltx_font_bold" id="A2.T19.2.2.2.1.1">Baseline</span> <math alttext="\phi_{i}" class="ltx_Math" display="inline" id="A2.T19.2.2.2.1.m1.1"><semantics id="A2.T19.2.2.2.1.m1.1a"><msub id="A2.T19.2.2.2.1.m1.1.1" xref="A2.T19.2.2.2.1.m1.1.1.cmml"><mi id="A2.T19.2.2.2.1.m1.1.1.2" xref="A2.T19.2.2.2.1.m1.1.1.2.cmml">ϕ</mi><mi id="A2.T19.2.2.2.1.m1.1.1.3" xref="A2.T19.2.2.2.1.m1.1.1.3.cmml">i</mi></msub><annotation-xml encoding="MathML-Content" id="A2.T19.2.2.2.1.m1.1b"><apply id="A2.T19.2.2.2.1.m1.1.1.cmml" xref="A2.T19.2.2.2.1.m1.1.1"><csymbol cd="ambiguous" id="A2.T19.2.2.2.1.m1.1.1.1.cmml" xref="A2.T19.2.2.2.1.m1.1.1">subscript</csymbol><ci id="A2.T19.2.2.2.1.m1.1.1.2.cmml" xref="A2.T19.2.2.2.1.m1.1.1.2">italic-ϕ</ci><ci id="A2.T19.2.2.2.1.m1.1.1.3.cmml" xref="A2.T19.2.2.2.1.m1.1.1.3">𝑖</ci></apply></annotation-xml><annotation encoding="application/x-tex" id="A2.T19.2.2.2.1.m1.1c">\phi_{i}</annotation><annotation encoding="application/x-llamapun" id="A2.T19.2.2.2.1.m1.1d">italic_ϕ start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT</annotation></semantics></math>
</td>
<td class="ltx_td ltx_align_left ltx_border_t" id="A2.T19.2.2.2.2">Answer:</td>
</tr>
<tr class="ltx_tr" id="A2.T19.4.4.4">
<td class="ltx_td ltx_align_right" id="A2.T19.3.3.3.1">Reasoning <math alttext="r_{i}" class="ltx_Math" display="inline" id="A2.T19.3.3.3.1.m1.1"><semantics id="A2.T19.3.3.3.1.m1.1a"><msub id="A2.T19.3.3.3.1.m1.1.1" xref="A2.T19.3.3.3.1.m1.1.1.cmml"><mi id="A2.T19.3.3.3.1.m1.1.1.2" xref="A2.T19.3.3.3.1.m1.1.1.2.cmml">r</mi><mi id="A2.T19.3.3.3.1.m1.1.1.3" xref="A2.T19.3.3.3.1.m1.1.1.3.cmml">i</mi></msub><annotation-xml encoding="MathML-Content" id="A2.T19.3.3.3.1.m1.1b"><apply id="A2.T19.3.3.3.1.m1.1.1.cmml" xref="A2.T19.3.3.3.1.m1.1.1"><csymbol cd="ambiguous" id="A2.T19.3.3.3.1.m1.1.1.1.cmml" xref="A2.T19.3.3.3.1.m1.1.1">subscript</csymbol><ci id="A2.T19.3.3.3.1.m1.1.1.2.cmml" xref="A2.T19.3.3.3.1.m1.1.1.2">𝑟</ci><ci id="A2.T19.3.3.3.1.m1.1.1.3.cmml" xref="A2.T19.3.3.3.1.m1.1.1.3">𝑖</ci></apply></annotation-xml><annotation encoding="application/x-tex" id="A2.T19.3.3.3.1.m1.1c">r_{i}</annotation><annotation encoding="application/x-llamapun" id="A2.T19.3.3.3.1.m1.1d">italic_r start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT</annotation></semantics></math>
</td>
<td class="ltx_td ltx_align_left" id="A2.T19.4.4.4.2">
<span class="ltx_text" id="A2.T19.4.4.4.2.2"></span><span class="ltx_text" id="A2.T19.4.4.4.2.1">
<span class="ltx_tabular ltx_align_middle" id="A2.T19.4.4.4.2.1.1">
<span class="ltx_tr" id="A2.T19.4.4.4.2.1.1.2">
<span class="ltx_td ltx_nopad_r ltx_align_left" id="A2.T19.4.4.4.2.1.1.2.1"><span class="ltx_text" id="A2.T19.4.4.4.2.1.1.2.1.1" style="color:#FF0000;">The peaches are the second-most expensive</span>. The mangoes are the cheapest. The apples are the least expensive of the three fruits.</span></span>
<span class="ltx_tr" id="A2.T19.4.4.4.2.1.1.3">
<span class="ltx_td ltx_nopad_r ltx_align_left" id="A2.T19.4.4.4.2.1.1.3.1">The peaches are more expensive than the apples. The mangoes are the cheapest. The peaches are the second-most expensive.</span></span>
<span class="ltx_tr" id="A2.T19.4.4.4.2.1.1.4">
<span class="ltx_td ltx_nopad_r ltx_align_left" id="A2.T19.4.4.4.2.1.1.4.1">The mangoes are the cheapest. The apples are the least expensive of the three fruits. The peaches are more expensive than the apples.</span></span>
<span class="ltx_tr" id="A2.T19.4.4.4.2.1.1.1">
<span class="ltx_td ltx_nopad_r ltx_align_left" id="A2.T19.4.4.4.2.1.1.1.1">The mangoes are the cheapest <math alttext="\dots" class="ltx_Math" display="inline" id="A2.T19.4.4.4.2.1.1.1.1.m1.1"><semantics id="A2.T19.4.4.4.2.1.1.1.1.m1.1a"><mi id="A2.T19.4.4.4.2.1.1.1.1.m1.1.1" mathcolor="#FF0000" mathvariant="normal" xref="A2.T19.4.4.4.2.1.1.1.1.m1.1.1.cmml">…</mi><annotation-xml encoding="MathML-Content" id="A2.T19.4.4.4.2.1.1.1.1.m1.1b"><ci id="A2.T19.4.4.4.2.1.1.1.1.m1.1.1.cmml" xref="A2.T19.4.4.4.2.1.1.1.1.m1.1.1">…</ci></annotation-xml><annotation encoding="application/x-tex" id="A2.T19.4.4.4.2.1.1.1.1.m1.1c">\dots</annotation><annotation encoding="application/x-llamapun" id="A2.T19.4.4.4.2.1.1.1.1.m1.1d">…</annotation></semantics></math></span></span>
</span></span><span class="ltx_text" id="A2.T19.4.4.4.2.3"></span></td>
</tr>
<tr class="ltx_tr" id="A2.T19.5.5.5">
<td class="ltx_td ltx_align_right ltx_border_t" id="A2.T19.5.5.5.1">
<span class="ltx_text ltx_font_bold" id="A2.T19.5.5.5.1.1">CoT</span> <math alttext="\phi_{i}" class="ltx_Math" display="inline" id="A2.T19.5.5.5.1.m1.1"><semantics id="A2.T19.5.5.5.1.m1.1a"><msub id="A2.T19.5.5.5.1.m1.1.1" xref="A2.T19.5.5.5.1.m1.1.1.cmml"><mi id="A2.T19.5.5.5.1.m1.1.1.2" xref="A2.T19.5.5.5.1.m1.1.1.2.cmml">ϕ</mi><mi id="A2.T19.5.5.5.1.m1.1.1.3" xref="A2.T19.5.5.5.1.m1.1.1.3.cmml">i</mi></msub><annotation-xml encoding="MathML-Content" id="A2.T19.5.5.5.1.m1.1b"><apply id="A2.T19.5.5.5.1.m1.1.1.cmml" xref="A2.T19.5.5.5.1.m1.1.1"><csymbol cd="ambiguous" id="A2.T19.5.5.5.1.m1.1.1.1.cmml" xref="A2.T19.5.5.5.1.m1.1.1">subscript</csymbol><ci id="A2.T19.5.5.5.1.m1.1.1.2.cmml" xref="A2.T19.5.5.5.1.m1.1.1.2">italic-ϕ</ci><ci id="A2.T19.5.5.5.1.m1.1.1.3.cmml" xref="A2.T19.5.5.5.1.m1.1.1.3">𝑖</ci></apply></annotation-xml><annotation encoding="application/x-tex" id="A2.T19.5.5.5.1.m1.1c">\phi_{i}</annotation><annotation encoding="application/x-llamapun" id="A2.T19.5.5.5.1.m1.1d">italic_ϕ start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT</annotation></semantics></math>
</td>
<td class="ltx_td ltx_align_left ltx_border_t" id="A2.T19.5.5.5.2">Answer: Let’s think step by step.</td>
</tr>
<tr class="ltx_tr" id="A2.T19.6.6.6">
<td class="ltx_td ltx_align_right" id="A2.T19.6.6.6.1">Reasoning <math alttext="r_{i}" class="ltx_Math" display="inline" id="A2.T19.6.6.6.1.m1.1"><semantics id="A2.T19.6.6.6.1.m1.1a"><msub id="A2.T19.6.6.6.1.m1.1.1" xref="A2.T19.6.6.6.1.m1.1.1.cmml"><mi id="A2.T19.6.6.6.1.m1.1.1.2" xref="A2.T19.6.6.6.1.m1.1.1.2.cmml">r</mi><mi id="A2.T19.6.6.6.1.m1.1.1.3" xref="A2.T19.6.6.6.1.m1.1.1.3.cmml">i</mi></msub><annotation-xml encoding="MathML-Content" id="A2.T19.6.6.6.1.m1.1b"><apply id="A2.T19.6.6.6.1.m1.1.1.cmml" xref="A2.T19.6.6.6.1.m1.1.1"><csymbol cd="ambiguous" id="A2.T19.6.6.6.1.m1.1.1.1.cmml" xref="A2.T19.6.6.6.1.m1.1.1">subscript</csymbol><ci id="A2.T19.6.6.6.1.m1.1.1.2.cmml" xref="A2.T19.6.6.6.1.m1.1.1.2">𝑟</ci><ci id="A2.T19.6.6.6.1.m1.1.1.3.cmml" xref="A2.T19.6.6.6.1.m1.1.1.3">𝑖</ci></apply></annotation-xml><annotation encoding="application/x-tex" id="A2.T19.6.6.6.1.m1.1c">r_{i}</annotation><annotation encoding="application/x-llamapun" id="A2.T19.6.6.6.1.m1.1d">italic_r start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT</annotation></semantics></math>
</td>
<td class="ltx_td ltx_align_left" id="A2.T19.6.6.6.2">
<span class="ltx_text" id="A2.T19.6.6.6.2.1"></span><span class="ltx_text" id="A2.T19.6.6.6.2.2">
<span class="ltx_tabular ltx_align_middle" id="A2.T19.6.6.6.2.2.1">
<span class="ltx_tr" id="A2.T19.6.6.6.2.2.1.1">
<span class="ltx_td ltx_nopad_r ltx_align_left" id="A2.T19.6.6.6.2.2.1.1.1">The peaches are more expensive than the apples. The mangoes are the cheapest.</span></span>
<span class="ltx_tr" id="A2.T19.6.6.6.2.2.1.2">
<span class="ltx_td ltx_nopad_r ltx_align_left" id="A2.T19.6.6.6.2.2.1.2.1">Therefore, the mangoes are the least expensive of the three fruits.</span></span>
<span class="ltx_tr" id="A2.T19.6.6.6.2.2.1.3">
<span class="ltx_td ltx_nopad_r ltx_align_left" id="A2.T19.6.6.6.2.2.1.3.1"><span class="ltx_text" id="A2.T19.6.6.6.2.2.1.3.1.1" style="color:#0000FF;">The peaches are more expensive than the apples</span>, <span class="ltx_text" id="A2.T19.6.6.6.2.2.1.3.1.2" style="color:#FF0000;">so the peaches are the second-most expensive of the three fruits</span>.</span></span>
<span class="ltx_tr" id="A2.T19.6.6.6.2.2.1.4">
<span class="ltx_td ltx_nopad_r ltx_align_left" id="A2.T19.6.6.6.2.2.1.4.1">Choice (B) is incorrect. The mangoes are the cheapest of the three fruits. Choice (C) is incorrect.</span></span>
<span class="ltx_tr" id="A2.T19.6.6.6.2.2.1.5">
<span class="ltx_td ltx_nopad_r ltx_align_left" id="A2.T19.6.6.6.2.2.1.5.1">The apples are less expensive than the peaches. The best <span class="ltx_text" id="A2.T19.6.6.6.2.2.1.5.1.1" style="color:#FF0000;">answer is A</span>.</span></span>
</span></span><span class="ltx_text" id="A2.T19.6.6.6.2.3"></span></td>
</tr>
<tr class="ltx_tr" id="A2.T19.7.7.7">
<td class="ltx_td ltx_align_right ltx_border_t" id="A2.T19.7.7.7.1">
<span class="ltx_text ltx_font_bold" id="A2.T19.7.7.7.1.1">ARR</span> <math alttext="\phi_{i}" class="ltx_Math" display="inline" id="A2.T19.7.7.7.1.m1.1"><semantics id="A2.T19.7.7.7.1.m1.1a"><msub id="A2.T19.7.7.7.1.m1.1.1" xref="A2.T19.7.7.7.1.m1.1.1.cmml"><mi id="A2.T19.7.7.7.1.m1.1.1.2" xref="A2.T19.7.7.7.1.m1.1.1.2.cmml">ϕ</mi><mi id="A2.T19.7.7.7.1.m1.1.1.3" xref="A2.T19.7.7.7.1.m1.1.1.3.cmml">i</mi></msub><annotation-xml encoding="MathML-Content" id="A2.T19.7.7.7.1.m1.1b"><apply id="A2.T19.7.7.7.1.m1.1.1.cmml" xref="A2.T19.7.7.7.1.m1.1.1"><csymbol cd="ambiguous" id="A2.T19.7.7.7.1.m1.1.1.1.cmml" xref="A2.T19.7.7.7.1.m1.1.1">subscript</csymbol><ci id="A2.T19.7.7.7.1.m1.1.1.2.cmml" xref="A2.T19.7.7.7.1.m1.1.1.2">italic-ϕ</ci><ci id="A2.T19.7.7.7.1.m1.1.1.3.cmml" xref="A2.T19.7.7.7.1.m1.1.1.3">𝑖</ci></apply></annotation-xml><annotation encoding="application/x-tex" id="A2.T19.7.7.7.1.m1.1c">\phi_{i}</annotation><annotation encoding="application/x-llamapun" id="A2.T19.7.7.7.1.m1.1d">italic_ϕ start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT</annotation></semantics></math>
</td>
<td class="ltx_td ltx_align_left ltx_border_t" id="A2.T19.7.7.7.2">
<span class="ltx_text" id="A2.T19.7.7.7.2.1"></span><span class="ltx_text" id="A2.T19.7.7.7.2.2">
<span class="ltx_tabular ltx_align_middle" id="A2.T19.7.7.7.2.2.1">
<span class="ltx_tr" id="A2.T19.7.7.7.2.2.1.1">
<span class="ltx_td ltx_nopad_r ltx_align_left" id="A2.T19.7.7.7.2.2.1.1.1">Answer: Let’s analyze the intent of the question, find relevant information, and answer the question with step-by-step reasoning.</span></span>
</span></span><span class="ltx_text" id="A2.T19.7.7.7.2.3"></span></td>
</tr>
<tr class="ltx_tr" id="A2.T19.8.8.8">
<td class="ltx_td ltx_align_right ltx_border_bb ltx_border_b" id="A2.T19.8.8.8.1">Reasoning <math alttext="r_{i}" class="ltx_Math" display="inline" id="A2.T19.8.8.8.1.m1.1"><semantics id="A2.T19.8.8.8.1.m1.1a"><msub id="A2.T19.8.8.8.1.m1.1.1" xref="A2.T19.8.8.8.1.m1.1.1.cmml"><mi id="A2.T19.8.8.8.1.m1.1.1.2" xref="A2.T19.8.8.8.1.m1.1.1.2.cmml">r</mi><mi id="A2.T19.8.8.8.1.m1.1.1.3" xref="A2.T19.8.8.8.1.m1.1.1.3.cmml">i</mi></msub><annotation-xml encoding="MathML-Content" id="A2.T19.8.8.8.1.m1.1b"><apply id="A2.T19.8.8.8.1.m1.1.1.cmml" xref="A2.T19.8.8.8.1.m1.1.1"><csymbol cd="ambiguous" id="A2.T19.8.8.8.1.m1.1.1.1.cmml" xref="A2.T19.8.8.8.1.m1.1.1">subscript</csymbol><ci id="A2.T19.8.8.8.1.m1.1.1.2.cmml" xref="A2.T19.8.8.8.1.m1.1.1.2">𝑟</ci><ci id="A2.T19.8.8.8.1.m1.1.1.3.cmml" xref="A2.T19.8.8.8.1.m1.1.1.3">𝑖</ci></apply></annotation-xml><annotation encoding="application/x-tex" id="A2.T19.8.8.8.1.m1.1c">r_{i}</annotation><annotation encoding="application/x-llamapun" id="A2.T19.8.8.8.1.m1.1d">italic_r start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT</annotation></semantics></math>
</td>
<td class="ltx_td ltx_align_left ltx_border_bb ltx_border_b" id="A2.T19.8.8.8.2">
<span class="ltx_text" id="A2.T19.8.8.8.2.1"></span><span class="ltx_text" id="A2.T19.8.8.8.2.2">
<span class="ltx_tabular ltx_align_middle" id="A2.T19.8.8.8.2.2.1">
<span class="ltx_tr" id="A2.T19.8.8.8.2.2.1.1">
<span class="ltx_td ltx_nopad_r ltx_align_left" id="A2.T19.8.8.8.2.2.1.1.1">The question asks for the second-most expensive fruit. The peaches are more expensive than the apples,</span></span>
<span class="ltx_tr" id="A2.T19.8.8.8.2.2.1.2">
<span class="ltx_td ltx_nopad_r ltx_align_left" id="A2.T19.8.8.8.2.2.1.2.1">and the mangoes are the cheapest. Therefore, <span class="ltx_text" id="A2.T19.8.8.8.2.2.1.2.1.1" style="color:#008080;">the second-most expensive fruit is the apples</span>.</span></span>
<span class="ltx_tr" id="A2.T19.8.8.8.2.2.1.3">
<span class="ltx_td ltx_nopad_r ltx_align_left" id="A2.T19.8.8.8.2.2.1.3.1">Choice A is incorrect. The peaches are more expensive than the apples, and the mangoes are the cheapest.</span></span>
<span class="ltx_tr" id="A2.T19.8.8.8.2.2.1.4">
<span class="ltx_td ltx_nopad_r ltx_align_left" id="A2.T19.8.8.8.2.2.1.4.1">Therefore, the peaches are the most expensive fruit, not the second-most expensive.</span></span>
<span class="ltx_tr" id="A2.T19.8.8.8.2.2.1.5">
<span class="ltx_td ltx_nopad_r ltx_align_left" id="A2.T19.8.8.8.2.2.1.5.1">Choice B is incorrect. The mangoes are the cheapest fruit.</span></span>
</span></span><span class="ltx_text" id="A2.T19.8.8.8.2.3"></span></td>
</tr>
</table>{{< /table-caption >}}
> 🔼 표 19는 본 논문의 저자들이 제안한 ARR(Analyzing, Retrieving, Reasoning) 방법이 질문에 대한 답을 정확하게 제시하는 반면, 기준 방법(Baseline)과 CoT(Chain of Thought) 방법은 실패하는 사례를 보여줍니다. 분석에 따르면, 기준 방법은 결론을 서두르고 설명을 시도하지만, 잘못된 진술로 인해 추론 과정이 혼란스러워지고 모델이 무한한 자기 의심 루프에 빠지는 것을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 19: Case study. An instance from the BBH dataset, where our ARR method correctly answers the question but the Baseline and CoT methods fail. Analysis: The Baseline method rushes to conclusions and then tries to present an explanation. However, the false statement confuses the whole reasoning process and makes the model caught in an infinite self-doubting loop.
> </details>

{{< table-caption >}}
| Task Input | Question: Select the best translation into predicate logic. | 
|---|---| 
| $x_{i}$ | David teaches Chris. (c: Chris; d: David; Txy: x teaches y) <br> (A) Tdc  (B) **Tcd**  (C) Tcc  (D) dTc | 
| Baseline $\phi_{i}$ | Answer: | 
| Reasoning $r_{i}$ | (B) The translation of the sentence into predicate logic is **Tcd**, where Txy means x teaches y. <br> The subject of the sentence is David, the object is Chris, and the predicate is teaches. <br> The correct **translation is Tcd**, not Tdc, **because the subject comes before the predicate** in a predicate logic statement. <br> Choice (C) is incorrect because it **reverses the subject and object**. <br> Choice (D) is incorrect because it reverses the subject and predicate. | 
| CoT $\phi_{i}$ | Answer: Let’s think step by step. | 
| Reasoning $r_{i}$ | (B) The predicate logic translation of the sentence is **Tcd**, where Txy means x teaches y. The best answer is B. | 
| ARR $\phi_{i}$ | Answer: Let’s analyze the intent of the question, find relevant information, and answer the question with step-by-step reasoning. | 
| Reasoning $r_{i}$ | The question asks for the best translation into predicate logic. The relevant information is the statement "David teaches Chris." <br> The statement is in the active voice, so the **subject is the teacher, and the object is the student**. <br> The predicate logic translation is **Tdc**, where Txy means x teaches y, c is Chris, and d is David. <br> Choice (B) is incorrect. This is the translation of "Chris teaches David." <br> Choice (C) is incorrect. This is the translation of "Chris teaches Chris." <br> Choice (D) is incorrect. This is the translation of "David is taught by Chris." <br> The best **answer is A**.{{< /table-caption >}}
> 🔼 표 20은 MMLU 데이터셋의 질문에 대한 답변을 예시로 보여줍니다. ARR 방법은 질문에 대한 정답을 제시하지만, 기준 방법과 CoT 방법은 잘못된 결론에 확신을 가지고 도달합니다. ARR 방법은 먼저 질문을 이해하고 각 선택지를 정확하게 분석하는 반면, 기준 방법과 CoT 방법은 질문에 대한 이해 없이 답변을 합니다. 이는 ARR 방법이 질문에 대한 분석과 이해를 통해 정확한 답변을 도출하는 데 효과적임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 20: Case study. An instance from the MMLU dataset, where our ARR method correctly answers the question but the Baseline and CoT methods fail. Analysis: The Baseline and CoT methods jump to the wrong conclusions confidently, while the ARR method understands the question first and analyzes each option correctly.
> </details>

{{< table-caption >}}
| Task Input | Question: Which type of research methods are designed to elicit responses to predetermined, standardized questions from many respondents? (A) Non-probability.  (B) Cross-sectional.  (C) Qualitative.  (D) Ethnographic.  (E) Longitudinal. (F) Experimental.  (G) Probability.  (H) Observational.  (I) Case Study.  (J) Quantitative. | 
|---|---| 
| Baseline  | Answer: | 
| Reasoning  | The best answer is G. Probability sampling is a type of research method that is designed to elicit responses to predetermined, standardized questions from many respondents. Probability sampling is a type of sampling method that is used to select a sample of participants from a larger population. Probability sampling methods include simple random sampling, stratified sampling, and cluster sampling. | 
| CoT  | Answer: Let’s think step by step. | 
| Reasoning  | (G) Probability sampling is a method of selecting a sample from a population in which every member of the population has an equal chance of being selected. Probability sampling is used in research to ensure that the sample is representative of the population. | 
| ARR  | Answer: Let’s analyze the intent of the question, find relevant information, and answer the question with step-by-step reasoning. | 
| Reasoning  | The question asks about research methods that are designed to elicit responses to predetermined, standardized questions from many respondents. This is a clue that the research method is quantitative. Quantitative research methods are designed to elicit responses to predetermined, standardized questions from many respondents. The correct answer is (J). The other choices are incorrect because they are not quantitative research methods. | {{< /table-caption >}}
> 🔼 표 21은 본 논문의 ARR(Analyzing, Retrieving, Reasoning) 방법이 질문의 의도와 함의를 파악하여 정답을 제시하는 반면, 기준 방법(Baseline)과 CoT(Chain-of-Thought) 방법은 실패하는 사례를 보여줍니다. MMLU-Pro 데이터셋의 질문에 대해 세 가지 방법의 답변 과정을 비교 분석하여 ARR 방법의 우수성을 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Table 21: Case study. An instance from the MMLU-Pro dataset, where our ARR method correctly answers the question but the Baseline and CoT methods fail. Analysis: The ARR method grasps the question’s intent and implications before answering.
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