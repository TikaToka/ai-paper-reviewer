---
title: "Expect the Unexpected: FailSafe Long Context QA for Finance"
summary: "FailSafeQA 벤치마크: 금융 분야 LLM의 신뢰성 향상"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Question Answering", "🏢 OpenAI",]
showSummary: true
date: 2025-02-10
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.06329 {{< /keyword >}}
{{< keyword icon="writer" >}} Kiran Kamble et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-12 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.06329" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.06329" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

본 연구는 금융 분야에서 **LLM 기반 질의응답 시스템의 취약점을 다루는 새로운 벤치마크인 FailSafeQA**를 제시합니다. 기존 벤치마크와 달리, FailSafeQA는 **다양한 인간-LLM 상호작용 변형을 고려**하여 **질의 오류(Query Failure) 및 컨텍스트 오류(Context Failure)** 시나리오에 초점을 맞춥니다. 

연구진은 **LLM-as-a-judge 방법론**을 사용하여 24개의 LLM 모델을 평가하고, **강건성, 컨텍스트 기반, 규정 준수 점수**를 계산했습니다. 결과적으로, 일부 모델은 입력 변화에 잘 대처하지만, 환각(hallucination)을 생성하는 경향도 보여, **강건성과 환각 방지의 균형**이 중요함을 강조합니다. 이 연구는 **금융 애플리케이션을 위한 LLM 개발의 방향**을 제시하고, FailSafeQA 데이터셋을 공개하여 다른 연구자들이 활용할 수 있도록 지원합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} FailSafeQA는 금융 분야의 LLM을 위한 새로운 벤치마크입니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} FailSafeQA는 LLM의 강건성과 컨텍스트 인식 능력을 평가합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} FailSafeQA는 LLM이 금융 애플리케이션에서 신뢰할 수 있도록 개선하는 데 도움이 됩니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **금융 분야에서의 LLM(대규모 언어 모델)의 안정성과 견고성을 평가하기 위한 새로운 벤치마크인 FailSafeQA**를 제시하여, 연구자들이 **LLM의 신뢰성을 향상시키고 금융 응용 분야에서의 실제적인 문제를 해결**하는 데 도움을 줄 수 있기 때문에 중요합니다.  FailSafeQA는 다양한 실제 시나리오를 모방하여 **LLM의 강점과 약점을 폭넓게 평가**할 수 있습니다. 이러한 평가를 통해 **LLM 기반 금융 시스템의 위험을 줄이고, 금융 애플리케이션에서의 신뢰도를 높이는 데 기여**할 수 있습니다. 또한, FailSafeQA 데이터셋은 공개되어 있어 다른 연구자들도 활용할 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.06329/x1.png)

> 🔼 그림 1은 FailSafeQA 벤치마크의 핵심 개념을 보여줍니다.  FailSafeQA는 금융 분야에서 LLM 기반 질의응답 시스템의 강건성과 맥락 인식 능력을 평가하기 위한 새로운 벤치마크입니다. 그림은 질의 오류(Query Failure) 시나리오와 맥락 오류(Context Failure) 시나리오의 두 가지 사례 연구에 중점을 둡니다. 질의 오류 시나리오에서는 철자 오류, 질의어 형태 변경, 도메인 전문 용어 제외를 통한 질의 수정 등 세 가지 변형을 통해 원래 질의를 변경합니다. 맥락 오류 시나리오에서는 사용자가 문서를 업로드하지 못하거나, OCR로 인해 저하된 품질의 문서를 사용하거나, 질의와 관련 없는 문서를 업로드하는 세 가지 상황을 시뮬레이션합니다. 강건성(Robustness) 점수는 의도된 의미를 유지하는 변형(A~C, E)에 대한 모델 성능의 일관성을 평가하고, 맥락 기반(Context Grounding) 점수는 시나리오(D, F)에서의 환각을 방지하는 능력을 평가합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: FailSafeQA: Robustness and Context Grounding Evaluation We evaluate the resilience of an LLM-based QA system in two case studies: Query Failure and Context Failure. In the Query Failure scenario, we perturb the original query into three variants: containing spelling errors (Misspelled Query), query-term form (Incomplete Query), rephrased to exclude in-domain terminology (Out-of-Domain Query). In the Context Failure case, we assume users can either fail to upload the document (Missing Context) , use degraged quality documents due to OCR (OCRed Context) or upload a document irrelevant to the query (Irrelevant Context). Robustness involves maintaining consistent model performance across perturbations (A)-(C) and (E), which preserve the intended meaning, while Context Grounding involves preventing hallucinations in scenarios (D) and (F).
> </details>





{{< table-caption >}}
Model Name|Baseline|Mispelled (Δ)|Incomplete (Δ)|Out-of-Domain (Δ)|OCR Context (Δ)|Robustness (Δ)
---|---|---|---|---|---|---
Gemini 2.0 Flash Exp|0.95|0.95 (0.0)|0.95 (0.0)|0.88 (↓0.07)|0.91 (↓0.04)|0.83 (↓0.12)
Gemini 1.5 Pro 002|0.96|0.96 (0.0)|0.94 (↓0.02)|0.92 (↓0.04)|0.92 (↓0.04)|0.84 (↓0.12)
OpenAI GPT-4o|0.95|0.94 (↓0.01)|0.94 (↓0.01)|0.92 (↓0.03)|0.95 (0.0)|0.85 (↓0.1)
OpenAI o1|0.97|0.95 (↓0.02)|0.94 (↓0.03)|0.89 (↓0.08)|0.94 (↓0.03)|0.81 (↓0.16)
OpenAI o3-mini|0.98|0.96 (↓0.02)|0.96 (↓0.02)|0.95 (↓0.03)|0.90 (↓0.08)|0.90 (↓0.08)
DeepSeek-R1-Distill-Llama-8B|0.83|0.85 (↑0.02)|0.82 (↓0.01)|0.87 (↑0.04)|0.72 (↓0.11)|0.64 (↓0.19)
DeepSeek-R1-Distill-Qwen-14B|0.95|0.90 (↓0.05)|0.92 (↓0.03)|0.93 (↓0.02)|0.86 (↓0.09)|0.82 (↓0.13)
DeepSeek-R1-Distill-Qwen-32B|0.95|0.97 (↑0.02)|0.95 (0.0)|0.92 (↓0.03)|0.89 (↓0.06)|0.86 (↓0.09)
DeepSeek-R1-Distill-Llama-70B|0.96|0.97 (↑0.01)|0.95 (↓0.01)|0.94 (↓0.02)|0.93 (↓0.03)|0.89 (↓0.07)
DeepSeek-R1|0.94|0.94 (0.0)|0.93 (↓0.01)|0.91 (↓0.03)|0.88 (↓0.06)|0.80 (↓0.14)
Meta-Llama-3.1-8B-Instruct|0.91|0.90 (↓0.01)|0.86 (↓0.05)|0.82 (↓0.09)|0.80 (↓0.11)|0.70 (↓0.21)
Meta-Llama-3.1-70B-Instruct|0.94|0.92 (↓0.02)|0.94 (0.0)|0.87 (↓0.07)|0.88 (↓0.06)|0.80 (↓0.14)
Meta-Llama-3.3-70B-Instruct|0.95|0.92 (↓0.03)|0.93 (↓0.02)|0.90 (↓0.05)|0.89 (↓0.06)|0.82 (↓0.13)
Qwen2.5-7B-Instruct|0.92|0.91 (↓0.01)|0.90 (↓0.02)|0.85 (↓0.07)|0.80 (↓0.12)|0.75 (↓0.17)
Qwen2.5-14B-Instruct|0.95|0.94 (↓0.01)|0.94 (↓0.01)|0.94 (↓0.01)|0.88 (↓0.07)|0.86 (↓0.09)
Qwen2.5-32B-Instruct|0.95|0.94 (↓0.01)|0.93 (↓0.02)|0.92 (↓0.03)|0.92 (↓0.03)|0.85 (↓0.1)
Qwen2.5-72B-Instruct|0.94|0.94 (0.0)|0.94 (0.0)|0.92 (↓0.02)|0.91 (↓0.03)|0.84 (↓0.1)
Qwen2.5-7B-Instruct-1M|0.91|0.91 (0.0)|0.91 (0.0)|0.86 (↓0.05)|0.77 (↓0.14)|0.74 (↓0.17)
Qwen2.5-14B-Instruct-1M|0.95|0.92 (↓0.03)|0.91 (↓0.04)|0.91 (↓0.04)|0.89 (↓0.06)|0.80 (↓0.15)
Nemotron-70B-Instruct-HF|0.94|0.94 (0.0)|0.93 (↓0.01)|0.90 (↓0.04)|0.91 (↓0.03)|0.82 (↓0.12)
Phi-3-mini-128k-Instruct|0.86|0.85 (↓0.01)|0.78 (↓0.08)|0.79 (↓0.07)|0.69 (↓0.17)|0.58 (↓0.28)
Phi-3-small-128k-Instruct|0.88|0.84 (↓0.04)|0.88 (0.0)|0.83 (↓0.05)|0.78 (↓0.1)|0.70 (↓0.18)
Phi-3-medium-128k-Instruct|0.89|0.84 (↓0.05)|0.84 (↓0.05)|0.81 (↓0.08)|0.72 (↓0.17)|0.63 (↓0.26)
Palmyra-Fin-128k-Instruct|0.96|0.93 (↓0.03)|0.92 (↓0.04)|0.90 (↓0.06)|0.89 (↓0.07)|0.83 (↓0.13){{< /table-caption >}}

> 🔼 표 1은 다양한 입력 변형에 대한 여러 언어 모델의 강건성을 평가한 결과를 보여줍니다. 오타 및 불완전한 질의는 대부분의 모델에서 다룰 수 있었지만, OCR 오류가 포함된 질의에서는 Phi-3-mini-128k-Instruct 및 Phi-3-medium-128k-Instruct 모델의 성능이 최대 0.17까지 감소하는 등 상당한 성능 저하가 관찰되었습니다. 기준 성능은 대부분의 모델에서 0.98~0.81 범위였지만, 모든 변형에 대한 최소값을 비교했을 때 모델들이 다양한 입력 유형에 일관되게 적응하는 데 어려움을 겪는다는 것을 알 수 있습니다. 가장 강건한 모델인 OpenAI o3-mini조차도 기준 성능보다 0.08 감소했습니다. 각 범주별 최고 성능은 굵게 표시하고, 두 번째로 높은 성능은 밑줄로 표시했습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Robustness Results. Misspelled and incomplete queries seem manageable for all models; however, the most significant drop in performance, reaching up to 0.170.170.170.17 for Phi-3-mini-128k-Instruct and Phi-3-medium-128k-Instruct, is observed in cases involving OCRed queries. While the baseline performance appears relatively straightforward for all models, with scores ranging from 0.980.980.980.98 to 0.810.810.810.81, the point-wise minimum across all perturbations—indicative of robustness—reveals that models face challenges in consistently adapting to various input types. Even the most robust model, OpenAI o3-mini, experiences a decrease of 0.080.080.080.08 relative to the baseline. The best results in each category are in bold and second best are underlined.
> </details>





### In-depth insights


#### Financial LLM Robustness
금융 LLM 강건성에 대한 심층적인 논의는 **모델의 신뢰성과 안정성**을 확보하는 데 매우 중요합니다.  이는 다양한 금융 데이터와 질의에 대한 **일관된 성능**을 의미하며, 특히 오류가 포함된 입력이나 불완전한 정보에도 정확한 결과를 제공하는 능력을 포함합니다.  **데이터의 품질과 다양성**은 모델의 강건성을 평가하는 중요한 요소이며, 다양한 유형의 질의와 예외 상황에 대한 테스트를 통해 모델의 취약점을 파악하고 개선할 수 있습니다.  **실제 금융 환경의 복잡성**을 반영한 평가 기준을 마련하여, 실제 시스템 구축 시 발생할 수 있는 문제점을 예측하고 방지하는 전략을 세우는 것이 필수적입니다.  **모델의 투명성과 설명 가능성**을 높임으로써, 모델의 의사결정 과정에 대한 이해도를 높이고 신뢰도를 향상시킬 수 있습니다.  궁극적으로 금융 LLM 강건성 확보는 **금융 시스템 전반의 안전성**과 **투자자 보호**라는 측면에서 중요한 의미를 지니며, 지속적인 연구와 개선을 통해 더욱 신뢰할 수 있는 시스템을 구축해 나가야 합니다.  **리스크 관리 및 규제 준수** 또한 중요한 고려 사항입니다.

#### FailSafeQA Benchmark
FailSafeQA 벤치마크는 금융 분야에서 **장문 컨텍스트 질의응답 시스템의 강건성과 컨텍스트 인식 능력**을 평가하기 위한 새로운 벤치마크입니다. 기존의 금융 벤치마크와 달리, **실제 사용자 상호작용의 다양성**을 고려하여 질문의 오류 (철자 오류, 불완전한 질문, 도메인 외부 질문) 및 컨텍스트의 오류 (누락된 컨텍스트, 품질 저하된 컨텍스트, 무관한 컨텍스트)를 포함합니다.  **LLM-as-a-Judge 방법론**을 사용하여 24개의 모델을 평가하고, 강건성, 컨텍스트 기반, 그리고 규정 준수 점수를 계산합니다. 이를 통해 **모델의 신뢰성과 안정성**을 종합적으로 평가하고, 금융 애플리케이션에 최적화된 LLM 개발에 기여할 수 있습니다. 특히, 고성능 모델이라도 여전히 개선의 여지가 있음을 보여주는 결과는 **FailSafeQA 벤치마크의 중요성**을 강조합니다.  본 벤치마크는 다양한 오류 상황에서 모델의 성능을 평가함으로써 금융 분야에서 LLM의 안전하고 신뢰할 수 있는 활용을 위한 중요한 기준을 제시합니다.

#### Hallucination Tradeoffs
**환각(hallucination)**은 대규모 언어 모델(LLM)이 사실이 아닌 정보를 생성하는 현상을 말합니다.  본 논문에서 다루는 "환각 트레이드오프(Hallucination Tradeoffs)"는 LLM이 정확성과 유창성 사이에서 균형을 맞추는 어려움을 의미합니다.  **정확성**을 높이려면 모델이 더욱 신중하게 정보를 생성해야 하지만, 이는 **유창성**과 자연스러움을 희생할 수 있습니다. 반대로 유창성을 중시하면 모델이 더욱 자유롭게 정보를 생성하지만, **환각의 위험**이 증가합니다. 따라서, 적절한 환각 수준을 결정하는 것은 모델 개발의 주요 과제입니다. **이러한 트레이드오프는 모델의 설계, 훈련 데이터, 평가 지표 등 여러 요소에 따라 달라집니다.**  본 논문은 이러한 다양한 요소들을 고려하여 최적의 환각 수준을 찾는 방법에 대한 통찰력을 제공합니다.  **특히, 금융 분야와 같이 정확성이 매우 중요한 영역에서는 환각으로 인한 위험을 최소화하는 것이 필수적입니다.** 따라서,  본 논문의 "환각 트레이드오프"에 대한 분석은 LLM의 실제 적용 가능성을 높이는 데 중요한 시사점을 제공합니다.

#### Context Grounding
논문에서 'Context Grounding'은 **모델이 제공된 맥락을 정확하게 이해하고, 그 맥락에 기반하여 적절한 응답을 생성하는 능력**을 의미합니다.  이는 단순히 맥락을 인식하는 것을 넘어, **관련 없는 정보를 걸러내고, 질문의 의도를 정확하게 파악하여 답변의 정확성과 일관성을 유지**하는 것을 포함합니다. 높은 Context Grounding 점수는 모델이 **잘못된 정보나 엉뚱한 추론을 생성하지 않고, 질문에 대해 정확하고 관련성 있는 답변을 제공**함을 의미합니다.  반대로 낮은 점수는 모델이 **맥락을 제대로 이해하지 못하거나, 맥락과 무관한 정보를 답변에 포함시켜 오류를 발생**시킬 가능성이 높음을 시사합니다. 따라서 Context Grounding은 특히 금융과 같이 정보의 정확성과 신뢰성이 매우 중요한 분야에서 **LLM의 안전성과 신뢰도를 평가하는 중요한 지표**가 됩니다.  **FailSafeQA와 같은 벤치마크는 다양한 맥락 오류 시나리오를 통해 모델의 Context Grounding 능력을 종합적으로 평가**하고, 개선 방향을 제시하는 데 기여할 수 있습니다.

#### Future Research
본 논문은 금융 분야에서 장문 컨텍스트 질의응답에 대한 새로운 벤치마크인 FailSafeQA를 제시하며, **LLM의 강건성과 맥락적 기반을 평가**하는 데 초점을 맞추고 있습니다. 미래 연구는 몇 가지 방향으로 확장될 수 있습니다. 첫째, **다양한 금융 도메인과 컨텍스트 길이에 대한 FailSafeQA의 적용성을 확대**하여 더욱 포괄적인 평가를 수행할 수 있습니다. 둘째, **LLM의 신뢰성을 높이는 데 도움이 되는 새로운 LLM 아키텍처나 훈련 방법**을 탐구할 수 있습니다. 셋째, **사용자 인터페이스의 다양한 변화에 대한 LLM의 반응을 분석**하여 더욱 현실적인 시나리오를 만들 수 있습니다. 마지막으로, **장문 컨텍스트 내에서 환각을 줄이는 기술**을 개발하는 것은 중요한 연구 과제입니다. 본 논문의 결과는 이러한 미래 연구에 대한 방향을 제시하며, 금융 분야에서 신뢰할 수 있는 LLM 기반 시스템을 구축하는 데 중요한 역할을 할 것으로 기대됩니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.06329/extracted/6191732/assets/verb_dobj_base_new.png)

> 🔼 그림 2는 정규화된 각 질문의 첫 번째 문장에서 주어 동사와 목적어를 분석하여 상위 20개 동사와 상위 5개 목적어의 분포를 보여줍니다. 이 분포는 질문 답변(QA) 관련 작업이 83.0%, 텍스트 생성(TG) 관련 작업이 17.0%를 차지하는 데이터셋의 작업 다양성을 보여주는 대략적인 지표로 활용될 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: The Dataset Analysis of root verbs and their direct objects from the first sentence of each normalized query shows the top 20 verbs and their top five direct objects22footnotemark: 2. This distribution can be used as a proxy measure for the diversity of tasks in the dataset, with 83.0% related to question answering (QA) and 17.0% involving text generation (TG).
> </details>



![](https://arxiv.org/html/2502.06329/x2.png)

> 🔼 그림 3은 모델이 답변을 제공해야 하는 경우(ANSWER QUERY)와 관련 컨텍스트가 부족하여 답변을 거부해야 하는 경우(REFUSE QUERY)의 두 가지 시나리오를 평가한 결과를 보여줍니다. 실험 결과, 모든 모델이 컨텍스트가 충분하지 않은 상황에서 정당한 거부보다 적절한 답변을 제공하는 데 더 능숙한 것으로 나타났습니다. 평가된 모든 모델 중에서 Palmyra-Fin-128k-Instruct 모델이 두 가지 기능 간의 균형을 가장 효과적으로 맞춘 것으로 나타났습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Answer Relevance Classes We evaluate two scenarios in our benchmark: when models should provide an answer (ANSWER QUERY) and when they must decline to answer (REFUSE QUERY) due to lack of relevant context. Our findings reveal that all the tested models are more adept at offering suitable answers than providing a justified refusal in situations where the context lacks sufficient information. Among all models evaluated, Palmyra-Fin-128k-Instruct demonstrates the most effective balance between these capabilities.
> </details>



![](https://arxiv.org/html/2502.06329/x3.png)

> 🔼 그림 4는 모델의 강건성(Robustness)과 맥락 기반(Context Grounding) 성능을 보여줍니다. 왼쪽 그래프는 다양한 입력 섭동(perturbation)이 적용되었을 때, 24개 모델의 성능 저하를 보여줍니다. 특히, 도메인 외부 질문(Out-of-Domain)과 OCR 오류가 포함된 맥락(OCR context)에서 성능 저하가 가장 컸습니다. OpenAI o3-mini 모델이 가장 강건한 모델로 나타났습니다. 오른쪽 그래프는 OpenAI-o1/o3-mini 및 DeepSeek-R1 계열과 같은 추론 모델이 최대 0.59점의 점수를 달성한 반면, Qwen 모델은 일관되게 0.60점을 상회하는 성능을 보였음을 보여줍니다. Palmyra-Fin-128k-Instruct 모델은 0.80점의 최고 맥락 기반 점수를 기록했습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Robustness and Compliance (Left) All models lose with respect to the baseline when input perturbations are applied. The biggest drop is observed for Out-Of-Domain and OCR context perturbations. Among the 24242424 tested models, OpenAI o3-mini is the most robust. (Right) Reasoning models like OpenAI-o1/o3-mini and the DeepSeek-R1 series reach scores up to 0.590.590.590.59, while Qwen models consistently surpass 0.600.600.600.60. Palmyra-Fin-128k-Instruct excels with the highest Context Grounding score of 0.800.800.800.80.
> </details>



![](https://arxiv.org/html/2502.06329/extracted/6191732/assets2/robustness_query_type.png)

> 🔼 그림 5는 질문 유형에 따른 견고성을 보여줍니다. 왼쪽 그래프는 모든 모델에서 질문 답변(QA) 작업보다 텍스트 생성(TG) 작업에서 견고성 감소가 더 두드러짐을 보여줍니다. 오른쪽 그래프는 잘못된 문서(무관한 맥락)를 기반으로 답변을 거부하는 것이 빈 맥락(예: 문서 업로드 실패)을 처리하는 것보다 거의 모든 모델에서 더 쉽다는 것을 보여줍니다. 특히 모델이 텍스트를 생성하도록 요청받았을 때(예: 블로그 게시물), 관련 정보의 부족을 무시하고 세부 정보를 조작할 가능성이 더 큽니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Robustness vs. Query Type. (Left) Across all models, the decrease in robustness is more prominent in text generation (TG) than in question-answering (QA) tasks. (Right) Similar statement also holds true for Context Grounding - when a model is asked to generate text (e.g., a blog post), it is more likely to ignore the lack of relevant information and fabricate details. For almost all models, it is easier to refuse to answer based on a wrong document (irrelevant context) than to deal with empty context (e.g., due to a failed document upload).
> </details>



![](https://arxiv.org/html/2502.06329/extracted/6191732/assets2/context_grounding_query_type.png)

> 🔼 그림 6은 모델의 맥락 기반 이해 능력(Context Grounding)이 질의 유형(질문/답변(QA) vs. 텍스트 생성(TG))에 따라 어떻게 달라지는지를 보여줍니다. 왼쪽 그래프는 모든 모델에서 텍스트 생성 작업의 강건성(Robustness)이 질문/답변 작업보다 더 크게 감소함을 보여줍니다. 오른쪽 그래프는 맥락 기반 이해 능력 역시 유사한 경향을 보임을 보여줍니다. 특히, 모델이 텍스트(예: 블로그 게시물)를 생성하라는 요청을 받으면 관련 정보가 부족하더라도 무시하고 세부 정보를 만들어낼 가능성이 더 높습니다. 모든 모델에서 잘못된 문서(무관한 맥락)를 기반으로 답변을 거부하는 것이 빈 맥락(예: 문서 업로드 실패)을 다루는 것보다 더 쉽다는 것을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Context Grounding vs. Query Type. (Left) Across all models, the decrease in robustness is more prominent in text generation (TG) than in question-answering (QA) tasks. (Right) Similar statement also holds true for Context Grounding - when a model is asked to generate text (e.g., a blog post), it is more likely to ignore the lack of relevant information and fabricate details. For all models, it is easier to refuse to answer based on a wrong document (irrelevant context) than to deal with empty context (e.g., due to a failed document upload).
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