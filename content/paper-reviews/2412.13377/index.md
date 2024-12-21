---
title: "DateLogicQA: Benchmarking Temporal Biases in Large Language Models"
summary: "DateLogicQA: LLM의 시간적 추론 편향 벤치마크 제시! 토큰화, 표상 및 논리 수준 편향 분석으로 시간적 데이터 처리 개선 방안 제시!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 University of Aberdeen",]
showSummary: true
date: 2024-12-17
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.13377 {{< /keyword >}}
{{< keyword icon="writer" >}} Gagan Bhatia et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-20 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.13377" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.13377" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/datelogicqa-benchmarking-temporal-biases-in" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)은 날짜와 같은 시간 정보를 처리하는 데 어려움을 겪습니다. 이는 토큰화 과정에서의 불일치, 날짜 임베딩의 부정확성, 그리고 추론 과정에서의 논리적 오류로 인한 **표상 수준 편향**과 **논리 수준 편향** 때문입니다. 이러한 편향은 LLM이 실제 세계 문제를 해결하는 데 심각한 영향을 미칠 수 있습니다.

본 논문에서는 이러한 문제를 해결하기 위해 **190개의 질문으로 구성된 새로운 벤치마크인 DateLogicQA**를 제시합니다. DateLogicQA는 다양한 날짜 형식, 시간적 문맥, 그리고 추론 유형을 포함하여 LLM의 시간적 추론 능력을 포괄적으로 평가할 수 있도록 설계되었습니다. 또한, **토큰화 품질을 평가하기 위한 의미적 무결성 지표**와 **인간 평가를 통한 편향 분석**을 제시하여, 모델의 시간적 추론 성능을 향상시키기 위한 구체적인 방안을 제시합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} DateLogicQA: 다양한 날짜 형식과 추론 유형을 포함하는 새로운 시간적 추론 벤치마크 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 토큰화, 표상, 논리 수준 편향 분석을 통한 LLM의 시간적 추론 능력 평가 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} LLM의 시간적 추론 성능 향상을 위한 토큰화 전략, 사전 훈련 데이터 개선, 추가 훈련 기법 제시 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대규모 언어 모델(LLM)의 시간적 추론 편향을 평가하기 위한 새로운 벤치마크인 DateLogicQA**를 제시하여, LLM의 시간적 데이터 처리에 대한 중요한 통찰력을 제공합니다. **토큰화 과정의 편향, 표상 수준 편향, 논리 수준 편향**을 분석하여 LLM의 시간적 추론 성능을 향상시키기 위한 새로운 연구 방향을 제시하며, **시간적 추론에 대한 미래 연구의 기반**을 마련합니다. 또한, 본 연구는 다양한 날짜 형식과 문맥을 포괄적으로 다루어, LLM의 시간적 추론 능력에 대한 심층적인 이해를 가능하게 합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.13377/extracted/6077549/figures/intro_page.drawio.png)

> 🔼 그림 1은 대규모 언어 모델(LLM)에서 나타나는 시간적 편향의 예시를 보여줍니다. 사용자 질문에 대한 세 가지 유형의 응답이 제시됩니다. 첫 번째는 잘못된 응답, 두 번째는 날짜는 잘못되었지만 추론 과정은 정확하여 표현 수준의 시간적 편향을 나타내는 경우, 세 번째는 날짜는 정확하지만 추론 과정이 잘못되어 논리 수준의 시간적 편향을 나타내는 경우, 마지막으로 정확한 응답입니다. 이 그림은 LLM이 시간 정보를 처리하는 데 어려움을 겪는 다양한 방식을 보여주는 시각적 예시를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Examples of temporal biases in LLMs.   Incorrect Response,  Faulty Date but accurate reasoning indicating representation level temporal bias,   Faulty reasoning but accurate date indicating logical level temporal bias,   Correct response
> </details>





{{< table-caption >}}
| Concepts | Example |
|---|---| 
| **Numerical** | What is the time 7 years and 9 months after 27101446? |
| **Factual** | Which of the people died on 23041616?  A) Shah Jahan B) Miguel de Cervantes C) Princess Diana D) William Shakespeare |
| **Conceptual** | The first iPhone was released on 29062007. How many years has it been since its release? |
| **Commonsense** | John was born on 15-03-1985. He graduated from college on 01-05-2007. Was John older than 18 when he graduated? |{{< /table-caption >}}

> 🔼 표 1은 DateLogicQA 데이터셋의 다양한 시간 추론 개념들을 보여주는 예시들을 보여줍니다.  각 행은 질문 유형(수치적, 사실적, 개념적, 상식적), 질문 자체, 그리고 그에 대한 예시 답변들을 보여줍니다. 이 표는 다양한 시간적 맥락(과거, 현재, 미래)과 날짜 표현 방식을 사용하여 시간 추론 과제의 다양성을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Dataset samples illustrating different temporal reasoning concepts.
> </details>





### In-depth insights


#### Temporal Bias in LLMs
본 논문은 대규모 언어 모델(LLM)의 시간적 편향(Temporal Bias)에 대한 심층적인 분석을 제공합니다. **LLM이 날짜, 시간, 기간 등 시간 관련 정보를 처리하고 추론하는 과정에서 발생하는 다양한 오류와 편향**에 초점을 맞추고 있습니다.  특히, 토큰화 과정에서의 불일치로 인한 표현 수준 편향(Representation-Level Bias)과 추론 과정의 논리적 결함으로 인한 논리 수준 편향(Logical-Level Bias)을 구분하여 분석하고 있습니다. 이러한 편향은 LLM의 신뢰성과 정확성에 심각한 영향을 미치므로, **시간적 추론 성능을 향상시키기 위한 다양한 해결 방안**을 제시하고 있습니다.  **데이터셋의 다양성 확보, 사전 훈련 데이터 개선, 그리고 미세 조정 기법 등**을 통해 시간적 편향을 완화하고 더욱 정확한 시간적 추론을 가능하게 할 수 있다는 점을 강조합니다.  **토큰화 전략의 중요성,  다양한 날짜 형식에 대한 고려, 그리고 시간적 맥락 이해의 필요성** 등을 종합적으로 제시함으로써, LLM의 시간적 추론 능력 향상에 기여하는 연구입니다.  **인간 평가자를 통한 편향 분석 및 다양한 측정 지표 제시**는 본 연구의 신뢰도를 더욱 높여주는 요소입니다.

#### DateLogicQA Dataset
DateLogicQA 데이터셋은 **다양한 형식과 문맥의 날짜 정보를 포함하는 190개의 질문으로 구성된 벤치마크**입니다. 이는 LLMs의 날짜 토큰화 및 이해 능력을 평가하기 위해 고안되었습니다. **과거, 현재, 미래를 포함한 세 가지 시간적 맥락**과 **일곱 가지 날짜 형식**을 사용하여 LLMs의 성능을 다각적으로 분석할 수 있습니다. 질문 유형은 상식, 사실, 개념, 수치적 추론 등 다양하게 구성되어, LLMs의 시간적 추론 능력을 포괄적으로 평가합니다.  **토큰화 일관성과 추론 정확성**을 평가하는 지표를 제공하며, **토큰화 오류로 인한 표현 수준 편향과 추론 과정에서 발생하는 논리 수준 편향**을 분석하는 데 유용합니다.  **실제 시나리오를 반영하는 풍부한 문맥**을 제공하여 LLMs의 날짜 이해와 처리 능력을 현실적으로 평가할 수 있다는 장점이 있습니다.  결론적으로, DateLogicQA 데이터셋은 LLMs의 시간적 추론 능력 평가에 중요한 역할을 하며, **향후 LLMs의 시간적 편향성 해결에 기여**할 것으로 기대됩니다.

#### Semantic Integrity Metric
본 논문에서 제시된 의미론적 무결성 측정법(Semantic Integrity Metric)은 **토큰화 과정에서 날짜 정보의 의미론적 무결성을 평가하는 핵심 요소**입니다.  단순히 토큰의 개수나 형태만을 고려하는 것이 아니라, **원래 날짜의 의미가 토큰화 이후에도 얼마나 잘 보존되는지**를 정량적으로 측정합니다.  이는 특히 다양한 날짜 형식과 시간적 맥락을 다루는 자연어 처리 모델의 성능 평가에 중요한 시사점을 제공합니다.  **날짜 토큰화의 일관성과 정확성을 평가하여 표현 수준의 편향(Representation-Level Bias)을 탐지**하는 데 도움을 주며, **잘못된 토큰화로 인한 의미 왜곡을 방지**하는 데 기여합니다. 따라서,  의미론적 무결성 측정법은 자연어 처리 모델의 시계열 추론 능력을 향상시키기 위한 토큰화 전략 개선 및 모델 개발에 중요한 지표로 활용될 수 있습니다.  **특히 다양한 날짜 형식에 대한 일반화 능력을 평가하고, 불필요한 토큰 분할 및 과도한 토큰 수를 억제**하는 데 초점을 맞추어  모델의 효율성과 정확성을 동시에 개선하는 데 기여합니다. 이 측정법의 도입은 LLM의 시간적 추론 성능 향상을 위한 중요한 발걸음입니다.

#### Bias Analysis Methods
본 논문에서 제시된 편향 분석 방법론은 **토큰화 과정의 영향**을 면밀히 조사하는 것부터 시작합니다. 특히, 날짜 정보의 토큰화 일관성 여부를 평가하는 **의미적 무결성 지표**를 도입하여, 임베딩 수준에서의 표현 편향과 추론 과정에서의 논리적 편향을 구분하여 분석합니다. 이를 위해, **인간 평가자를 통한 주관적 판단**을 추가하여 자동화된 지표의 한계를 보완하고, 모델의 추론 능력과 편향의 상관관계를 더욱 정확하게 파악하고자 합니다. **다양한 날짜 형식과 시간적 맥락**을 고려한 질문들을 통해,  LLM의 시간적 추론 능력에 대한 포괄적인 평가를 수행합니다.  **임베딩 공간과 소프트맥스 계산**을 분석하여 표현 수준 및 논리 수준의 시간적 편향을 정량적으로 측정하며, 날짜 형식의 다양성에 따른 모델 민감도 또한 분석합니다.  이러한 다각적인 접근 방식을 통해, LLM의 시간적 추론 능력의 강점과 약점을 정확하게 파악하고, 향후 개선 방향을 제시하는 데 기여합니다.

#### Future Research
미래 연구는 **날짜 형식의 표준화**를 통해 LLM의 날짜 처리 효율성을 개선하는 데 초점을 맞춰야 합니다. 다양한 시대적 맥락(과거, 현재, 미래)을 포괄하는 **풍부한 데이터셋**을 사용하여 사전 훈련 데이터셋을 강화하고 **사전 훈련된 임베딩의 한계와 기본 지식의 정적 특성**과 같은 고유한 편향을 완화하기 위한 전략을 연구해야 합니다.  **Direct Preference Optimization(DPO)**와 같은 사후 훈련 기법과 **Retrieval-Augmented Generation(RAG)** 및 **Chain of Thought(CoT)** 프롬프팅과 같은 프롬프팅 기법을 활용하여 모델의 추론 능력을 향상시키는 연구도 필요합니다.  **토큰화 전략의 영향**에 대한 심층적인 조사가 필요하며, 특히 비표준 날짜 형식에 대한 민감도를 줄이는 연구가 중요합니다. 마지막으로, **인간 평가의 확장성 문제**를 해결하고 다양한 토큰화 전략과 편향 완화 기법의 효과를 정확하게 평가하는 새로운 방법론을 개발해야 합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.13377/extracted/6077549/figures/color_chartrq2v3.png)

> 🔼 그림 2는 논문의 인간 평가 기준표를 보여줍니다. 이 표는 LLM의 시간적 추론 능력을 평가하기 위해 사용자가 모델의 응답을 평가하는 방법을 설명합니다.  세 가지 유형의 오류가 있습니다. 첫째, 잘못된 날짜와 잘못된 추론입니다. 둘째, 정확한 날짜와 잘못된 추론이며, 셋째는 잘못된 날짜와 정확한 추론입니다. 각 유형은 모델의 시간적 편향을 나타내는 색상으로 표시됩니다. 올바른 답변은 녹색으로 표시됩니다. 이 표는 모델의 시간적 추론 능력을 더 잘 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Human evaluation rubric
> </details>



![](https://arxiv.org/html/2412.13377/extracted/6077549/figures/temporal_impact_semantic.png)

> 🔼 그림 3은 다양한 모델의 토크나이저가 시간 경과에 따라 달라지는 시맨틱 무결성 점수를 보여줍니다.  x축은 연도를 나타내고, y축은 시맨틱 무결성 점수를 나타냅니다. 각 선은 다른 모델의 토크나이저 성능을 나타내며, 시맨틱 무결성 점수는 0에서 1 사이의 값으로, 1에 가까울수록 토크나이저가 날짜 정보를 잘 보존함을 의미합니다. 그래프는 특정 토크나이저가 특정 기간 동안 더 높은 시맨틱 무결성 점수를 나타내는 경향이 있음을 보여주어, 시간에 따른 편향성(temporal bias)을 시사합니다. 예를 들어, 일부 토크나이저는 최근 연도에 대해 더 높은 점수를 보이는 반면, 다른 토크나이저는 과거 시대에 대해 높은 점수를 보입니다. 이는 모델이 훈련 데이터의 시간적 분포에 따라 달라지는 편향성을 가지고 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Temporal impact on semantic integrity
> </details>



![](https://arxiv.org/html/2412.13377/extracted/6077549/figures/date_format_vis2x.png)

> 🔼 그림 5는 다양한 날짜 형식에 따른 모델 성능을 보여줍니다. 각 막대는 잘못된 응답, 정확한 추론을 사용한 잘못된 날짜 (표현 수준 시간적 편향), 정확한 날짜를 사용한 잘못된 추론 (논리 수준 시간적 편향), 정답의 네 가지 범주로 나뉩니다. 이는 각 모델이 다양한 날짜 형식을 처리하는 능력을 비교 분석하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> (a) Date Format visualisation
> </details>



![](https://arxiv.org/html/2412.13377/extracted/6077549/figures/time_period_vis2x.png)

> 🔼 그림 (b)는 시간적 맥락(과거, 현재, 미래)에 따른 모델 성능을 시각적으로 보여줍니다. 각 시대별로 모델의 정답률, 잘못된 날짜/정확한 추론, 정확한 날짜/잘못된 추론, 완전히 잘못된 응답의 비율을 막대 그래프로 나타내어 시간에 따른 모델의 성능 변화를 명확하게 파악할 수 있도록 합니다.  세부적으로는 각 막대 그래프가 네 가지 유형(정답, 잘못된 날짜+정확한 추론, 정확한 날짜+잘못된 추론, 오답)으로 세분화되어 있어, 모델의 오류 유형까지 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (b) Time period visualisation
> </details>



![](https://arxiv.org/html/2412.13377/extracted/6077549/figures/quest_type_vis2x.png)

> 🔼 그림 (c)는 DateLogicQA 데이터셋의 질문 유형별 모델 성능을 보여줍니다. 세 가지 주요 질문 유형(상식적 추론, 사실적 추론, 개념적 추론)에 대한 각 모델의 정확도를 시각적으로 비교하여, 어떤 유형의 질문에서 모델이 강점과 약점을 보이는지 분석할 수 있도록 합니다.  각 막대는 세 가지 질문 유형에 대한 다양한 모델의 정확도를 나타내며, 다양한 모델의 상대적 강점과 약점을 비교 분석하는 데 도움이 됩니다. 이를 통해 특정 질문 유형에 대한 모델 성능의 차이를 파악하고, 개선 방향을 모색할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (c) Question Type visualisation
> </details>



![](https://arxiv.org/html/2412.13377/extracted/6077549/figures/model_vis2x.png)

> 🔼 그림 4는 DateLogicQA 데이터셋을 사용한 다양한 모델의 성능을 보여주는 시각화 자료입니다. (a)는 날짜 형식별, (b)는 기간별, (c)는 질문 유형별 성능을 보여줍니다. 각 막대는 올바른 응답, 날짜는 정확하지만 추론이 잘못된 경우(표현 수준의 시간적 편향), 추론은 정확하지만 날짜가 잘못된 경우(논리 수준의 시간적 편향), 그리고 올바른 응답으로 나뉘어져 있습니다. 이 시각화는 DateLogicQA 데이터셋에서 다양한 날짜 형식, 시제, 추론 유형에 따른 언어 모델의 성능 차이를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Results Visualisations
> </details>



![](https://arxiv.org/html/2412.13377/extracted/6077549/figures/Llama-3.2-3B-Instruct_embeddings.png)

> 🔼 그림 5는 다양한 언어 모델의 시간 추론 능력을 평가한 결과를 보여줍니다. 각 막대는 네 가지 색상으로 구분되어 응답의 질을 나타냅니다. 즉, 잘못된 응답, 날짜는 틀렸지만 추론은 정확한 경우(표현 수준 시간 편향), 날짜는 정확하지만 추론은 잘못된 경우(논리 수준 시간 편향), 그리고 정확한 응답을 의미합니다. 이는 모델이 시간 정보를 처리하는 과정에서 발생하는 다양한 유형의 편향을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Each bar is segmented into four colors representing the quality of responses:   Incorrect Response,  Faulty Date but accurate reasoning indicating representation level temporal bias,   Faulty reasoning but accurate date indicating logical level temporal bias,   Correct response
> </details>



![](https://arxiv.org/html/2412.13377/extracted/6077549/figures/Llama-3.2-3B-Instruct_softmax.png)

> 🔼 그림 6은 LLama 3.2 3B 모델을 사용하여 표현 수준 시간적 편향 분석을 보여줍니다. 이 그림은 과거, 현재, 미래의 세 가지 시간적 참조에 걸쳐 다양한 날짜 형식에 대한 모델의 내부 임베딩 공간과 소프트맥스 계산을 조사합니다. 각 열은 특정 날짜 형식을 나타내고, 각 행은 과거, 현재, 미래의 시간적 참조를 나타냅니다. 열 지도의 각 셀은 과거, 현재, 미래의 세 가지 시간적 참조 간의 임베딩 유사성 또는 소프트맥스 출력 확률의 차이를 나타냅니다. 이 그림을 통해 모델이 시간적 참조와 날짜 형식에 따라 내부적으로 시간 정보를 얼마나 다르게 인코딩하는지 이해하는 데 도움이 됩니다.  더 높은 유사성 값은 모델이 과거, 현재, 미래의 세 가지 시간적 참조에 걸쳐 유사한 방식으로 정보를 처리함을 의미합니다. 반면에 높은 발산 값은 시간적 참조에 따라 모델의 출력이 크게 달라짐을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Representation level Temporal Bias Analysis using LLama 3.2 3B
> </details>



![](https://arxiv.org/html/2412.13377/extracted/6077549/figures/token_count_semantic.png)

> 🔼 그림 7은 LLama 3.2 3B 모델을 사용한 논리적 수준의 시간적 편향 분석 결과를 보여줍니다.  이 그림은 과거, 현재, 미래의 세 가지 시간적 참조에 따른 모델의 내부 확률 분포(softmax)의 차이를 보여주는 열 지도(heatmap)를 나타냅니다.  각 열 지도는 다양한 날짜 형식에 대한 모델의 반응을 보여줍니다. 열 지도의 색깔은 과거, 현재, 미래 시점에 대한 모델의 확률 분포 차이를 나타내며, 색이 진할수록 차이가 큽니다. 이를 통해 모델이 특정 시간적 맥락에서 일관성 있게 추론하지 못하고, 시간적 참조에 따라 다른 확률 분포를 보이는 논리적 수준의 시간적 편향을 확인할 수 있습니다.  특히, 미래 시점에 대한 예측에서 편향이 더 크게 나타나는 것을 관찰할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Logical level Temporal Bias Analysis using LLama 3.2 3B
> </details>



![](https://arxiv.org/html/2412.13377/)

> 🔼 그림 8은 다양한 언어 모델의 토크나이저에 대한 의미적 무결성 점수와 토큰 수 간의 상관 관계를 보여주는 산점도입니다. 각 점은 특정 모델의 토크나이저 성능을 나타내며, x축은 토큰 수, y축은 의미적 무결성 점수를 나타냅니다. 이 그래프는 토큰 수가 많을수록 의미적 무결성 점수가 낮아지는 경향이 있음을 시각적으로 보여줍니다. 즉, 토큰화 과정에서 과도한 분할은 의미를 손상시킬 수 있음을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Correlation plot between semantic integrity score against token count
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Date Format | Example |
|---|---| 
| DDMMYYYY | 23041616 |
| MMDDYYYY | 04231616 |
| DDMonYYYY | 23April1616 |
| DD-MM-YY | 23-04-16 |
| YYYY, Mon DD | 1616, April 23 |
| DD/YYYY (Julian calendar) | 113/1616 |
| YYYY/DD (Julian calendar) | 1616/113 |{{< /table-caption >}}
> 🔼 표 2는 DateLogicQA 데이터셋에 사용된 다양한 날짜 형식의 예시를 보여줍니다.  날짜 형식은 연도(YYYY), 월(MM 또는 Mon), 일(DD)의 다양한 조합과 표기법을 포함합니다.  이는 모델이 다양한 날짜 표현 방식을 얼마나 잘 처리하는지 평가하기 위한 것입니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Dataset samples illustrating different date formats used.
> </details>

{{< table-caption >}}
| Model | SI | TC | PC | PS |
|---|---|---|---|---|
| Baseline | 1.00 | 4.30 | ✓ | ✓ |
| OLMoE | 0.77 | 5.08 | ≈ | ✓ |
| OLMo | 0.77 | 5.08 | ≈ | ✓ |
| Davinci-003 | 0.75 | 5.17 | × | ✓ |
| Llama 3 | 0.74 | 4.98 | × | ✓ |
| GPT-3.5 | 0.74 | 4.98 | × | ✓ |
| GPT-4 | 0.74 | 4.98 | × | ✓ |
| GPT-4o | 0.74 | 4.98 | × | ✓ |
| Qwen | 0.42 | 9.30 | × | ✓ |
| Cohere | 0.42 | 9.30 | × | ✓ |
| Gemma | 0.42 | 9.30 | × | ✓ |
| DeepSeek | 0.42 | 9.30 | × | ✓ |
| Llama 2 | 0.37 | 10.30 | × | ✓ |
| Mistral | 0.37 | 10.30 | × | ✓ |
| Phi 3.5 | 0.37 | 10.30 | × | ✓ |
| Llama 1 | 0.37 | 10.30 | × | ✓ |{{< /table-caption >}}
> 🔼 표 3은 다양한 언어 모델의 토큰화 성능을 비교 분석한 표입니다.  구체적으로, 의미적 무결성(Semantic Integrity), 토큰 수(Token Count), 구성 요소 및 구분 기호 보존(Preservation of Components and Separators) 세 가지 측면에서 모델들의 성능을 평가하여 비교하고 있습니다. 각 모델의 토큰화 과정에서 의미의 정확성, 토큰의 효율성, 날짜 정보의 구조적 무결성을 평가하여  모델별 특징과 차이점을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Performance comparison of various models on semantic integrity, token count, and preservation of components and separators.
> </details>

{{< table-caption >}}
| Format | Model | Date | Year | Time Period | Century | TC | Tokenized Output | SI | SC | PS |
|---|---|---|---|---|---|---|---|---|---|---|
| MMDDYYYY | Baseline | 10271606 | 1606 | Historical (Pre-2000) | 17th Century | 3 | 10 27 1606 | 1.00 | false | true |
| MMDDYYYY | OLMoE | 10271606 | 1606 | Historical (Pre-2000) | 17th Century | 4 | 10 27 16 06 | 0.66 | true | true |
| MMDDYYYY | OLMo | 10271606 | 1606 | Historical (Pre-2000) | 17th Century | 4 | 10 27 16 06 | 0.66 | true | true |
| MMDDYYYY | Llama 3 | 10271606 | 1606 | Historical (Pre-2000) | 17th Century | 3 | 102 716 06 | 0.60 | true | true |
| MMDDYYYY | Llama 3.1 | 10271606 | 1606 | Historical (Pre-2000) | 17th Century | 3 | 102 716 06 | 0.60 | true | true |
| MMDDYYYY | Llama 3.2 | 10271606 | 1606 | Historical (Pre-2000) | 17th Century | 3 | 102 716 06 | 0.60 | true | true |
| MMDDYYYY | Davinci-003 | 10271606 | 1606 | Historical (Pre-2000) | 17th Century | 3 | 1027 16 06 | 0.60 | true | true |
| MMDDYYYY | GPT-3.5 | 10271606 | 1606 | Historical (Pre-2000) | 17th Century | 3 | 102 716 06 | 0.60 | true | true |
| MMDDYYYY | GPT-4o | 10271606 | 1606 | Historical (Pre-2000) | 17th Century | 3 | 102 716 06 | 0.60 | true | true |
| MMDDYYYY | GPT-4 | 10271606 | 1606 | Historical (Pre-2000) | 17th Century | 3 | 102 716 06 | 0.60 | true | true |
| MMDDYYYY | Cohere Aya | 10271606 | 1606 | Historical (Pre-2000) | 17th Century | 8 | 1 0 2 7 1 6 0 6 | 0.45 | true | true |
| MMDDYYYY | Gemma | 10271606 | 1606 | Historical (Pre-2000) | 17th Century | 8 | 1 0 2 7 1 6 0 6 | 0.45 | true | true |
| MMDDYYYY | DeepSeek | 10271606 | 1606 | Historical (Pre-2000) | 17th Century | 8 | 1 0 2 7 1 6 0 6 | 0.45 | true | true |
| MMDDYYYY | Cohere | 10271606 | 1606 | Historical (Pre-2000) | 17th Century | 8 | 1 0 2 7 1 6 0 6 | 0.45 | true | true |
| MMDDYYYY | Qwen | 10271606 | 1606 | Historical (Pre-2000) | 17th Century | 8 | 1 0 2 7 1 6 0 6 | 0.45 | true | true |
| MMDDYYYY | Phi 3.5 | 10271606 | 1606 | Historical (Pre-2000) | 17th Century | 9 | _ 1 0 2 7 1 6 0 6 | 0.40 | true | true |
| MMDDYYYY | Llama 2 | 10271606 | 1606 | Historical (Pre-2000) | 17th Century | 9 | _ 1 0 2 7 1 6 0 6 | 0.40 | true | true |
| MMDDYYYY | Mistral | 10271606 | 1606 | Historical (Pre-2000) | 17th Century | 9 | _ 1 0 2 7 1 6 0 6 | 0.40 | true | true |
| MMDDYYYY | Llama 1 | 10271606 | 1606 | Historical (Pre-2000) | 17th Century | 9 | _ 1 0 2 7 1 6 0 6 | 0.40 | true | true |{{< /table-caption >}}
> 🔼 표 4는 다양한 모델의 토큰화 성능을 보여줍니다.  여러 모델의 토큰화기가 생성한 토큰 수 (TC), 구성 요소 보존 (PC), 구분 기호 보존 (PS), 의미 무결성 점수 (SI)를 비교 분석하여 각 모델의 날짜 토큰화 정확도를 평가합니다.  특히, 다양한 날짜 형식에 따른 각 모델의 성능 차이를 확인할 수 있습니다.  기준 모델(Baseline)과 비교하여 각 모델의 토큰화 정확도와 효율성을 평가하는 데 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Generated by Spread-LaTeX
> </details>

{{< table-caption >}}
| Type of Q | Question | Answer | Date Format | Llama3-70B | Qwen2.5-72B | GPT-4o | GPT-4-turbo | CMDR+ |
|---|---|---|---|---|---|---|---|---|---|
| Factual | Which of the following famous people died on 23041616? Answer only with A, B, C, or D: A) Shah Jahan B) Miguel de Cervantes C) Princess Diana D) William Shakespeare | William Shakespeare OR Miguel de Cervantes | DDMMYYYY | B) Miguel de Cervantes and D) William Shakespeare | B, D | B) Miguel de Cervantes | D)William Shakespeare | A |
| Conceptual | The Eiffel Tower was built between 028/1887 to 090/1889. How long did it take to build the Eiffel Tower? | 2 years, 2 months, and 3 days | DD/YYYY (Julian) | The Eiffel Tower took 2 years and 1 month to build. | 2 years, 10 months, 2 days. | 2 years and 1 month. | It took 2 years and 2 months to build. | Construction of the Eiffel Tower took about two years and two months. |
| Common Sense | A new electric car model is set to be released on 273/2040. Pre-orders open 6 months earlier. On what date can customers start preordering? | On March 30, 2040 | DD/YYYY (Julian) | 273/2040 - 6 months = 93/2039. Customers can start preordering on this date. | Pre-orders open on 273/2039. | Customers can start pre-ordering on March 273/2039. | Customers can start preordering on March 273, 2040. | The pre-order date is July 273, 2039. |
| Numerical | What is the time 7 years and 9 months after 10271446? | July 27, 1454 | MMDDYYYY | October 27, 2040. | 10271446 + 7 years 9 months = 10353406 | October 2023 plus 7 years and 9 months is July 2031. | Time: 10429846 (Unix timestamp format). | 10279141 |{{< /table-caption >}}
> 🔼 표 5는 DateLogicQA 데이터셋을 사용한 다양한 언어 모델들의 성능을 보여줍니다.  모델의 종류, 질문 유형(사실적, 개념적, 상식적, 수치적), 날짜 형식, 시간적 맥락(과거, 현재, 미래)에 따른 정확도를 비교 분석하여 각 모델의 강점과 약점을 파악하고, 시간적 추론 능력을 평가합니다. 특히, 각 모델의 응답 유형을 '정확한 응답', '날짜 오류, 추론 정확', '추론 오류, 날짜 정확', '잘못된 응답'으로 분류하여 세부적인 분석을 제공합니다. 이 표는 시간적 편향 및 토큰화 과정의 영향을 이해하는 데 중요한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Model Performance on DateLogicQA
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