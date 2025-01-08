---
title: "ToolHop: A Query-Driven Benchmark for Evaluating Large Language Models in Multi-Hop Tool Use"
summary: "ToolHop: 대규모 언어 모델의 다중 단계 도구 사용 능력을 엄격히 평가하는 새로운 벤치마크"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 ByteDance",]
showSummary: true
date: 2025-01-05
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.02506 {{< /keyword >}}
{{< keyword icon="writer" >}} Junjie Ye et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-07 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.02506" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.02506" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/toolhop-a-query-driven-benchmark-for" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)은 인간처럼 다양한 도구를 활용하여 복잡한 문제를 해결해야 실용적인 수준에 도달할 수 있습니다. 하지만, 기존 평가 방식은 LLM이 **실제 환경에서 여러 도구를 활용하여 문제를 해결하는 능력**을 제대로 평가하지 못한다는 한계가 있었습니다.

본 연구는 이러한 문제를 해결하고자 **새로운 벤치마크 데이터셋인 ToolHop**을 제시합니다. ToolHop은 다양한 종류의 **실제 사용자 질의**와 이에 해당하는 여러 도구를 포함하고 있으며, **LLM의 다중 단계 도구 사용 능력**을 엄밀하게 평가할 수 있도록 설계되었습니다. 연구진은 ToolHop을 사용하여 여러 LLM 모델을 평가하고, 그 결과를 분석하여 각 모델의 강점과 약점을 파악하고 개선 방향을 제시했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 새로운 벤치마크 ToolHop을 통해 다양한 LLM의 다중 단계 도구 사용 능력을 종합적으로 평가 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} LLM의 다중 단계 도구 사용 능력에 대한 심층 분석 및 개선 방향 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 실제 사용자 질의 기반의 혁신적인 데이터 구축 방법 제시 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **다중 단계 도구 사용 능력 평가를 위한 새로운 벤치마크인 ToolHop**을 제시하여, 대규모 언어 모델(LLM)의 도구 사용 능력을 엄격하게 평가하고 향상시키는 데 중요한 기여를 합니다. **다양한 LLM의 성능을 비교 분석하고, 향후 연구 방향을 제시함으로써 LLM의 도구 사용 능력 향상에 대한 새로운 가능성을 제시**합니다. 특히, **실제 사용자 질의를 기반으로 데이터를 구축한 점**과 **모델의 성능 차이를 분석하여 개선 방향을 제시**한 점이 높이 평가됩니다. 이는 **LLM의 실제 응용 분야에서의 성능 향상**을 위한 중요한 발걸음이 될 것입니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.02506/x1.png)

> 🔼 그림 1은 다단계 도구 사용의 과정을 보여줍니다. 복잡한 다단계 질의는 여러 개의 원자적 하위 질의로 분해되고, 적절한 도구가 순차적으로 호출되며, 도구 피드백에서 결과를 가져와 최종 답변이 도출될 때까지 반복됩니다. 이 과정은 이해, 추론 및 함수 호출 기능의 통합을 보여줍니다.  다단계 질의를 해결하기 위해 모델이 여러 도구를 순차적으로 사용하여 하위 질의를 처리하고, 각 도구의 결과를 다음 단계의 입력으로 사용하는 과정을 시각적으로 나타냅니다. 각 단계의 하위 질의, 도구 호출, 피드백, 그리고 최종 답변이 명확하게 표시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: An illustration of multi-hop tool use. The process entails decomposing a complex multi-hop query into multiple atomic sub-queries, sequentially invoking the appropriate tools, retrieving results from the tool feedback, and iterating until the final answer is derived. This demonstrates the integration of comprehension, reasoning, and function-calling capabilities.
> </details>





{{< table-caption >}}
| # Tools | Three | Four | Five | Six | Seven |
|---|---|---|---|---|---| 
| **# Data** | 428 | 353 | 136 | 10 | 68 |{{< /table-caption >}}

> 🔼 ToolHop 데이터셋에서 각 쿼리를 해결하는 데 필요한 도구의 수 분포를 보여줍니다.  세 개에서 일곱 개의 도구가 필요한 쿼리가 있으며, 이는 쿼리의 다양한 복잡성 수준을 반영합니다. 즉, 단순한 쿼리부터 여러 단계의 추론이 필요한 복잡한 쿼리까지 다양한 유형의 쿼리를 포함하고 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Distribution of the number of tools required to solve each query in ToolHop.
> </details>





### In-depth insights


#### Multi-hop Tool Use
연구 논문에서 '다단계 도구 사용(Multi-hop Tool Use)'에 대한 심층적인 분석은 **대규모 언어 모델(LLM)**의 **이해, 추론 및 함수 호출 능력**을 평가하는 데 매우 중요함을 시사합니다.  **복잡한 질문을 해결하기 위해 여러 도구를 순차적으로 사용하는 능력**은 진정한 인공 지능으로 가는 중요한 단계이며, 이를 효과적으로 평가하기 위한 벤치마크의 필요성을 강조합니다.  기존 연구들은 단순한 시뮬레이션 환경이나 단일 도구 사용에 초점을 맞추었지만, 이는 실제 세계의 복잡한 문제 해결에는 부족합니다.  **ToolHop과 같은 새로운 벤치마크**는 다양하고 상호 의존적인 도구들과 검증 가능한 답변을 포함하여 이러한 문제점을 해결하고자 노력합니다.  **질의 중심 데이터 구축 방식**은 도구의 상호 의존성을 보장하고, **다단계 추론을 필요로 하는 진정한 질의**를 생성하는 데 도움이 됩니다.  **LLM의 다단계 도구 사용 능력 평가**를 위한 체계적인 접근 방식을 제시하며, 향후 연구 방향을 제시하는 데 기여합니다.

#### Query-Driven Dataset
본 논문에서 제시된 '질의 중심 데이터셋(Query-Driven Dataset)'은 기존의 도구 중심 접근 방식과 차별화되는 혁신적인 방법론을 제시합니다. **기존 도구 중심 방식은 도구를 먼저 수집하고 그에 맞는 질의를 생성하는 반면,** **본 논문의 방법론은 사용자의 다양한 질의를 먼저 고려하여 필요한 도구를 생성하는 역 접근 방식**을 취합니다. 이는 **실제 사용자의 요구를 더욱 정확하게 반영하고, 도구 간의 의미있는 상호 의존성을 보장**하는데 큰 장점이 있습니다.  **다양한 질의를 통해 도구의 기능과 상호작용을 다각적으로 평가**할 수 있으며, **실제 현실 세계 문제 해결에 더욱 가까운 시나리오**를 만들 수 있다는 점도 주목할 만합니다.  **검증 가능한 답변과 상세한 피드백을 제공**하여 모델의 성능 평가를 더욱 엄격하고 신뢰할 수 있도록 합니다.  결과적으로, 이러한 **질의 중심 접근 방식은 대규모 언어 모델의 다중 도구 활용 능력 평가를 위한 보다 효과적이고 실용적인 데이터셋 구축**에 기여할 수 있습니다.  **데이터셋의 질적 향상**은 모델의 성능 개선과 더 나아가 인공지능 기술 전반의 발전에 큰 영향을 미칠 것입니다.

#### LLM Tool Evaluation
LLM 도구 평가는 대규모 언어 모델(LLM)이 다양한 도구를 얼마나 효과적으로 사용하는지 측정하는 데 중점을 둡니다. 이는 단순히 정확한 답변을 생성하는 것을 넘어 **도구 선택, 호출, 결과 해석**의 전 과정을 평가해야 하므로 복잡한 과제입니다.  **다양한 벤치마크**가 제시되고 있지만, 각 벤치마크는 고유한 강점과 약점을 가지고 있으며,  **다차원적 평가 지표** 개발이 필요합니다.  예를 들어, 단일 도구 사용 성공률 뿐 아니라, 도구 사용 전략, 오류 처리 방식 등을 분석해야 LLM의 도구 활용 능력을 종합적으로 이해할 수 있습니다. 또한, **실제 사용 시나리오**를 반영한 평가가 중요하며,  **데이터셋의 질**이 평가 결과의 신뢰성에 큰 영향을 미친다는 점을 고려해야 합니다.  궁극적으로, LLM 도구 평가는 LLM의 지능 수준 향상과 실제 응용 가능성 확대에 중요한 역할을 합니다.  **지속적인 연구 개발**을 통해, 보다 객관적이고 포괄적인 평가 체계를 구축하는 것이 필요합니다.

#### Model Family Analysis
본 논문에서 제시된 다양한 모델들을 모델 패밀리별로 분석하는 것은 **상당히 중요한 의미**를 지닌다. 각 모델 패밀리는 고유한 설계 철학과 강점, 약점을 가지고 있기 때문이다.  LLaMA3.1 패밀리는 자연어 처리와 코드 생성 능력에 초점을 맞춘 반면, Qwen2.5 패밀리는 수리 능력과 지식 표현에 강점을 보였다.  Gemini1.5 패밀리는 혼합 전문가(MoE) 아키텍처를 활용하여 복잡한 추론 과제에서 뛰어난 성능을 보였고, Claude3.5 패밀리는 지시 사항 따르기와 미묘한 추론 능력이 뛰어났다. 마지막으로 GPT 패밀리는 텍스트 생성과 다중 모드 이해, 도구 사용 능력에서 우수한 성능을 보였다. 이러한 **상호 비교 분석을 통해 각 모델 패밀리의 강점과 약점을 명확히 파악**할 수 있으며, 향후 모델 개발 방향을 설정하는 데 귀중한 정보를 제공한다. 특히,  **다양한 도구 사용 전략**과 **성능 차이**를 분석하여 효과적인 모델 개발을 위한 구체적인 방향을 제시할 수 있다는 점에서 가치가 크다.  **단순한 성능 비교를 넘어 각 모델의 내부 작동 방식과 설계 특징을 고려**하여 심층적인 분석을 수행하는 것이 중요하다.

#### Future Research
본 논문에서 제시된 ToolHop 데이터셋은 다양한 도메인과 복잡한 멀티-홉 질의를 포함하여 LLM의 툴 사용 능력을 평가하는 데 유용한 기반을 제공합니다.  하지만, **LLM의 툴 사용 능력 향상을 위한 구체적인 방법론은 제시하지 못하고 있다는 점이 한계**입니다. 따라서, 향후 연구는 ToolHop을 활용하여 **다양한 LLM 아키텍처와 학습 전략에 따른 성능 차이를 분석**하고, **멀티-홉 툴 사용에서의 어려움을 극복할 수 있는 새로운 모델 아키텍처 또는 학습 기법을 제안**하는 데 초점을 맞춰야 합니다. 특히, **오류 처리 및 피드백 메커니즘 개선**을 통해 모델의 견고성을 높이고, **실제 세계 문제 해결에 효과적인 툴 사용 전략을 개발**하는 것이 중요합니다.  더불어, **다양한 유형의 툴과 멀티모달 데이터를 포함하는 확장된 데이터셋 구축**은 LLM의 일반화 능력 향상에 기여할 것입니다.  **ToolHop의 범용성을 높이기 위한 추가적인 연구**도 필요하며, 특히 다양한 언어 및 문화적 배경을 고려한 다국어 지원 및 편향성 해소 연구는 중요한 과제입니다.  궁극적으로, 이러한 노력들을 통해 LLM의 지능적인 툴 사용 능력을 한층 더 발전시킬 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.02506/x2.png)

> 🔼 그림 2는 논문에서 제안하는 질의 중심 데이터 구성 방식을 보여줍니다. 이 방식은 도구 생성, 문서 개선, 코드 생성의 세 가지 주요 단계로 구성됩니다. 각각의 다단계 질의 내에 있는 원자적 하위 질의에 대해 자세한 도구 문서와 코드 구현을 점진적으로 개발하는 접근 방식입니다. 그림은 각 단계의 과정과 그 결과물을 시각적으로 보여주어, 다단계 질의를 처리하기 위한 도구 사용에 대한 이해를 돕습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: An illustration of our proposed query-driven data construction scheme, comprising three key processes: tool creation, document refinement, and code generation. This approach incrementally develops detailed tool document and code implementation for each atomic subquery within a multi-hop query.
> </details>



![](https://arxiv.org/html/2501.02506/x3.png)

> 🔼 ToolHop 데이터셋에 있는 995개의 멀티홉 질의가 47개의 도메인에 걸쳐 얼마나 다양하게 분포되어 있는지 보여주는 그림입니다. 각 도메인별 질의 수를 막대 그래프로 나타내어, 데이터셋의 다양성과 실제 사용자 질의의 다양성을 반영하고 있음을 시각적으로 보여줍니다.  이는 ToolHop 데이터셋이 다양한 종류의 질의를 잘 포괄하고 있음을 보여주는 중요한 지표입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Distribution of user queries across 47 domains in the ToolHop dataset.
> </details>



![](https://arxiv.org/html/2501.02506/x4.png)

> 🔼 이 그림은 문서 개선 전후의 도구 매개변수 수의 분포를 보여줍니다. 문서 개선 전에는 매개변수의 수가 적게 분포되어 있지만, 문서 개선 후에는 더 많은 수의 매개변수가 사용되는 것을 보여줍니다. 이는 문서 개선 과정을 통해 도구의 기능이 향상되고 복잡성이 증가했음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Distribution of the number of tool parameters before and after document refinement.
> </details>



![](https://arxiv.org/html/2501.02506/x5.png)

> 🔼 그림 5는 도구 매개변수의 자료형 분포를 도구 문서 개선 전과 후로 나누어 보여줍니다. 도구 문서 개선 전에는 문자열 자료형 매개변수가 대부분이었으나, 개선 후에는 배열, 정수, 객체 자료형 매개변수의 비중이 증가한 것을 보여줍니다. 이는 도구의 기능이 더욱 복잡해지고 다양한 입력을 처리할 수 있도록 개선되었음을 시각적으로 보여주는 것입니다.  개선 전과 후의 자료형 분포 차이를 통해 도구 문서 개선 과정의 효과를 명확하게 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Distribution of tool parameter types before and after document refinement.
> </details>



![](https://arxiv.org/html/2501.02506/x6.png)

> 🔼 ToolHop 데이터셋의 두 번째 원자적 하위 질문과 최종 답변에 대한 답변 유형 분포를 보여주는 그림입니다.  그림은 다양한 유형의 답변(예: 숫자, 날짜, 문자열, 개체 등)이 ToolHop 데이터셋에 얼마나 다양하게 포함되어 있는지를 시각적으로 보여줍니다. 이는 ToolHop 데이터셋이 다양한 유형의 질문과 답변을 포괄함으로써, 다양한 종류의 멀티홉 툴 사용 시나리오를 평가하는 데 적합함을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Distribution of answer types for the second atomic subquery and final answers in ToolHop.
> </details>



![](https://arxiv.org/html/2501.02506/x7.png)

> 🔼 그림 7은 Qwen2.5 계열의 대규모 언어 모델(LLM)이 필수 도구 사용 시나리오에서 병렬 도구 호출을 사용하는 경향이 있음을 보여줍니다. 이는 잘못된 답변을 초래할 수 있는 환각(hallucination)으로 이어질 수 있습니다.  이 그림은 Qwen2.5-Instruct-32B 모델이 하나의 질문에 여러 도구를 동시에 호출하려고 시도하는 과정을 보여줍니다. 각 도구 호출은 서로 의존적이며, 하나의 도구 결과가 다른 도구의 입력으로 사용됩니다. 그러나 병렬 처리로 인해 각 도구가 독립적으로 실행되어 예상치 못한 결과와 부정확한 최종 답변이 발생할 수 있습니다.  이를 통해 병렬 도구 호출 전략의 한계를 보여주며,  LLM이 다단계 도구 사용 시나리오에서  효율성과 정확성 사이의 균형을 맞추는 데 어려움을 겪는다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: The Qwen2.5 family of LLMs emphasizes parallel tool calls in the mandatory tool use scenario, which can lead to hallucinations and incorrect answers.
> </details>



![](https://arxiv.org/html/2501.02506/x8.png)

> 🔼 그림 8은 Claude 3.5 계열의 대규모 언어 모델(LLM)이 직접적인 답변 시나리오에서 사고 연쇄(CoT) 추론을 최적화하여 분석 및 문제 해결 능력을 향상시키는 것을 보여줍니다.  즉, 도구를 사용하지 않고 주어진 질문에 대해 모델이 스스로 추론하고 답을 도출하는 능력을 평가하는 것입니다. 이 그림은 Claude 3.5 모델이 단계별 추론 과정을 통해 복잡한 문제를 효과적으로 해결하는 능력을 시각적으로 보여주는 예시를 포함하고 있을 것으로 예상됩니다.  이를 통해 CoT 추론 전략이 모델의 성능 향상에 미치는 영향을 효과적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: The Claude 3.5 family of LLMs optimizes CoT reasoning in the direct answer scenario, enhancing their analytical and problem-solving capabilities.'
> </details>



![](https://arxiv.org/html/2501.02506/x9.png)

> 🔼 그림 9는 GPT 계열의 대규모 언어 모델(LLM)이 상세한 도구 피드백을 사용하여 도구 호출 동작을 개선함으로써 성능을 향상시키는 과정을 보여줍니다.  LLM이 도구를 사용하는 방식을 단계별로 보여주는 예시로,  도구 호출 시 발생하는 에러를 상세한 피드백을 통해 수정하고,  결과적으로 질의에 대한 정확한 답변을 도출하는 과정을 시각적으로 제시합니다.  이는 단순히 도구를 사용하는 것 이상으로,  LLM이 피드백을 통해 학습하고  오류를 수정하며  더욱 정교한 작업을 수행할 수 있음을 보여주는 중요한 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: The GPT family of LLMs improves performance by refining calling behavior through the use of detailed tool feedback.
> </details>



![](https://arxiv.org/html/2501.02506/x10.png)

> 🔼 그림 10은 GPT 계열의 대규모 언어 모델(LLM)이 최소한의 피드백만 제공받았을 때, 잘못된 툴 호출 동작을 수정하는 데 어려움을 겪는다는 것을 보여줍니다.  GPT 모델은 툴을 호출하는 과정에서 오류가 발생했을 때, 자세한 피드백이 없으면 올바른 결과를 얻기 위한 호출 동작을 수정하지 못하고, 잘못된 답변을 생성하는 경향을 보입니다. 이는  LLM이 툴 사용에 대한 충분한 이해와 적절한 오류 처리 능력을 갖추지 못했음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: The GPT fmaily of LLMs struggles to correct their calling behavior when provided with minimal feedback.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Refinement | Zero | One | Two | Three | Four |
|---|---|---|---|---|---| 
| Before | 2 | 2433 | 1250 | 202 | 25 |
| After | 2 | 2490 | 1198 | 200 | 22 |{{< /table-caption >}}
> 🔼 표 2는 문서 개선 전후에 필요한 매개변수의 수 분포를 보여줍니다.  문서 개선 과정을 거치면서 각 도구에 필요한 매개변수의 수가 어떻게 변화하는지 보여주는 표입니다.  'Refinement' 열은 문서 개선 단계를 나타내고, 'Zero', 'One', 'Two', 'Three', 'Four' 열은 각각 매개변수 개수가 0개, 1개, 2개, 3개, 4개 이상인 도구의 수를 나타냅니다. 'Before' 행은 문서 개선 전의 분포를, 'After' 행은 문서 개선 후의 분포를 보여줍니다.  이 표를 통해 문서 개선이 도구의 복잡성과 세련성을 높이는 데 어떤 영향을 미치는지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Distribution of the number of required parameters before and after document refinement.
> </details>

{{< table-caption >}}
| Refinement | string | boolean | array | integer | object | number |
|---|---|---|---|---|---|---|
| Before | 4758 | 2 | 404 | 333 | 24 | 114 |
| After | 4473 | 2 | 755 | 241 | 44 | 102 |{{< /table-caption >}}
> 🔼 본 표는 도구 매개변수 유형의 분포를 세분화하여 보여줍니다.  도구 개선 전과 후의 필수 매개변수의 유형별 개수를 비교 분석하여 도구 개선 과정에서 매개변수의 유형과 수에 어떤 변화가 있었는지 보여줍니다.  이는 모델의 도구 사용 능력 평가에 있어서 도구의 복잡성 변화를 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Distribution of required tool parameter types before and after refinement.
> </details>

{{< table-caption >}}
| Source | Family | Version | Direct | Mandatory | Free | Query | Instance |
|---|---|---|---|---|---|---|---|---|
|  |  | *Avg.* | *19.83* | *32.12* | *32.84* | *18.72* | *8.68* |
| Open-Source | LLaMA3.1 | Instruct-8B | 13.17 | 12.76 | 13.47 | 41.61 | 21.10 |
|  |  | Instruct-70B | 18.79 | 19.10 | 12.76 | 35.08 | 14.24 |
|  | Qwen2.5 | Instruct-7B | 11.46 | 9.85 | 16.18 | 28.84 | 7.09 |
|  |  | Instruct-14B | 17.39 | 26.38 | 26.13 | 15.78 | 6.82 |
|  |  | Instruct-32B | 20.00 | 25.03 | 22.61 | 12.46 | 3.46 |
|  |  | Instruct-72B | 17.89 | 45.43 | 38.29 | 13.27 | 4.93 |
| Closed-Source | Gemini1.5 | flash-002 | 18.59 | 29.35 | 32.76 | 13.59 | 6.69 |
|  |  | pro-002 | 18.89 | 31.16 | 33.07 | 14.57 | 6.61 |
|  | Claude3.5 | Haiku | 36.08 | 38.09 | 44.72 | 23.48 | 15.81 |
|  |  | Sonnet | 27.14 | 39.90 | 45.23 | 19.60 | 15.83 |
|  | GPT | 3.5-Turbo | 17.09 | 35.38 | 36.58 | 11.76 | 6.03 |
|  |  | 4o-mini | 19.40 | 40.20 | 43.42 | 11.66 | 3.58 |
|  |  | 4-Turbo | 18.59 | 47.94 | 46.83 | 10.95 | 4.97 |
|  |  | 4o | 23.12 | 49.04 | 47.74 | 9.45 | 4.31 |{{< /table-caption >}}
> 🔼 표 4는 다양한 대규모 언어 모델(LLM)의 ToolHop 데이터셋 성능을 보여줍니다.  세 가지 시나리오(직접 답변, 필수 도구 사용, 자유 선택)에서 모델의 정답률과 도구 호출 오류율을 비교 분석합니다.  '쿼리'와 '인스턴스'는 각각 오류가 발생한 쿼리와 도구 호출의 비율을 나타냅니다. 평균값보다 높은 값은 청록색으로, 낮은 값은 갈색으로 강조 표시되어 있으며, 음영의 농도는 평균값과의 차이를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Performance of various LLMs on ToolHop, including answer correctness and invocation error. ‘Direct,’ ‘Mandatory,’ and ‘Free’ denote the direct answer, mandatory tool use, and free choice scenarios, respectively. ‘Query’ and ‘Instance’ refer to the percentage of queries and tool invocation instances with errors, respectively. ‘Avg.’ represents the average across all LLMs. Values above the average are highlighted in teal, and those below are highlighted in maroon, with darker shades indicating larger deviations.
> </details>

{{< table-caption >}}
| Version | w/ Feedback | w/o Feedback | 
---|---|---| 
| 3.5-Turbo | 36.75 | 21.37 | 
| 4o-mini | 38.53 | 11.93 | 
| 4-Turbo | 29.31 | 12.07 | 
| 4o | 47.87 | 24.47 | {{< /table-caption >}}
> 🔼 표 5는 GPT 계열 모델의 호출 오류가 포함된 질문에 대한 답변 정확도를 보여줍니다. '피드백 있음'과 '피드백 없음'은 각각 자세한 피드백 또는 간단한 오류 보고서가 제공된 경우를 나타냅니다.  ΔC→I는 자세한 피드백에서 간단한 오류 보고서로 전환할 때 정답이 오답으로 변하는 비율을 나타내고, ΔI→C는 오답이 정답으로 변하는 비율을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Answer correctness of the GPT family of models in queries containing invocation error. ‘w/ Feedback’ and ‘w/o Feedback’ represent cases where detailed feedback or only simple error reporting is provided, respectively. ‘𝚫𝐂→𝐈subscript𝚫→𝐂𝐈\mathbf{\Delta_{C\to I}}bold_Δ start_POSTSUBSCRIPT bold_C → bold_I end_POSTSUBSCRIPT’ denotes the proportion of correct answers that become incorrect, while ‘𝚫𝐈→𝐂subscript𝚫→𝐈𝐂\mathbf{\Delta_{I\to C}}bold_Δ start_POSTSUBSCRIPT bold_I → bold_C end_POSTSUBSCRIPT’ represents the proportion of incorrect answers that become correct, when transitioning from detailed feedback to simple error reporting.
> </details>

{{< table-caption >}}
| Steps | Description |
|---|---| 
| 1. Analyze the Problem | Understand the question and determine the type of information required to answer it. |
| 2. Tool Design | Design a tool that can solve the problem, considering the complexity and additional functionalities it might need. |
| 3. Parameter Specification | Define the parameters for the tool, ensuring they are comprehensive and flexible for various use cases. |
| 4. Output Construction | Format the output in JSON, including both the analysis and the tool schema. |
| Notes | - Ensure the tool is versatile enough to handle similar queries for different sports figures.<br> - Consider edge cases. |
| Output Format | The output should be a JSON object with the following structure **without any other contents**: <br> - "analysis": A detailed analysis of the ideas behind the tool design.<br> - "tool": A JSON schema characterizing the tool, including its name, description, and parameters. |{{< /table-caption >}}
> 🔼 표 6는 툴 생성을 위한 프롬프트를 보여줍니다.  '{Example}'은 예시를, '{Question}'은 하위 질의를 각각 나타냅니다.  본질적으로 이 표는 대규모 언어 모델(LLM)이 다중 단계 툴 사용 과제를 수행하기 위해 필요한 툴을 생성하는 데 사용된 지침을 설명합니다.  이 지침에는 문제 분석, 툴 설계, 매개변수 명세, 출력 구성 등의 단계가 포함됩니다.  각 단계는 LLM이 툴을 효과적으로 설계하고 생성하는 데 필요한 구체적인 지침을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: The prompt for tool creation, where ‘{Example}’ and ‘{Question}’ represent the example and subquery, respectively.
> </details>

{{< table-caption >}}
{"analysis": "Analysis of ideas about refining the tool.", "refined_version": {}}{{< /table-caption >}}
> 🔼 표 7은 논문의 2.2절인 'Query-Driven Data Construction' 섹션에 포함된 표입니다. 이 표는 쿼리 기반 데이터 구성 방식에서 도구 문서를 개선하는 과정에 사용되는 프롬프트(지시어)를 보여줍니다.  프롬프트는 초기 단계에서 생성된 도구 문서({Tool})를 입력으로 받아, 도구의 설명을 개선하고, 매개변수의 복잡성을 높이는 것을 목표로 합니다.  즉, 초기 도구의 기능과 호환성을 유지하면서 더욱 세련되고, 다양한 상황에 적용 가능한 도구 문서를 만들기 위한 지시사항을 담고 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: The prompt for document refinement, where ‘{Tool}’ represents the preliminary document.
> </details>

{{< table-caption >}}
| Steps | Description |
|---|---| 
| 1. **Understand the Tool Document** | Review the tool document to identify the function name, parameter names, and types. |
| 2. **Analyze the Question and Answer** | Determine how the function should be used to answer the question. |
| 3. **Implement the Function** |  Use the tool name as the function name. Define parameters exactly as specified in the tool document. Implement the function logic to produce the correct answer for the given question. Simulate additional return values as specified in the tool document. |
| 4. **Error Handling** | Develop a robust error handling mechanism to return valid error messages for incorrect inputs or other issues. |
| Notes | Description |
|---|---| 
| - | Ensure parameter types and names match exactly with the tool document. |
| - | Simulate additional return values as needed based on the tool’s documentation. |
| - | Implement comprehensive error handling to cover potential issues. |
| Output format | Description |
|---|---| 
|  | Output the result in JSON format with the following structure **without any other contents**: {
"analysis": "Detailed analysis of how the function was designed, including reasoning for parameter choices and exception handling.",
"function": "The specific function design, including code and comments explaining each part."
} |
| *Tool Document* | {document} |
| *Question* | {question} |
| *Answer* | {answer} |{{< /table-caption >}}
> 🔼 표 8은 코드 생성을 위한 프롬프트를 보여줍니다.  여기서 {document}는 다듬어진 문서, {question}은 하위 질문, {answer}는 해당하는 답변을 각각 나타냅니다. 이 표는 논문의 2.2절 'Query-Driven Data Construction' 에서  다루어지는 질의 중심 데이터 생성 과정에서 사용되는 프롬프트를 설명합니다.  GPT-40과 같은 대규모 언어모델이 질문과 다듬어진 문서, 그리고 정답을 바탕으로 실제 실행 가능한 코드를 생성할 수 있도록 안내하는 프롬프트의 구조와 내용을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 8: The prompt for code generation, where ‘{document}’, ‘{question}’ and ‘{answer}’ represent the refined document, the subquery and the corresponding answer, respectively.
> </details>

{{< table-caption >}}
| Steps | Description |
|---|---| 
| 1. **Analyze the Sentence** | Break down the sentence to understand its components and context. |
| 2. **Identify Key Elements** | Look for specific terms or phrases that indicate the subject matter, such as names, dates, or specific topics. |
| 3. **Determine the Domain** | Based on the analysis, select the most appropriate domain that encapsulates the main focus of the sentence. |
| Output Format |  ```json
{
  "analysis": "Analysis of the given sentence.",
  "domain": "The domain of the sentence, as short as possible"
}
``` |
| Notes | - Ensure the domain is specific and directly related to the main subject of the sentence. <br> - Consider the broader context if the sentence includes specific names or events. |
| Sentence | {sentence} |{{< /table-caption >}}
> 🔼 표 9는 도메인 분류를 위한 프롬프트를 보여줍니다.  여기서 `{sentence}`는 다단계 질의를 나타냅니다. 이 프롬프트는 GPT-40을 사용하여 ToolHop 데이터셋 내 질의의 도메인을 분류하기 위해 사용됩니다.  프롬프트는 문장의 내용과 문맥을 분석하고, 주요 요소를 파악하여, 문장의 주제를 가장 잘 나타내는 단일 도메인을 식별하는 단계들을 포함합니다.  출력 형식은 분석 결과와 도메인을 포함하는 JSON 객체입니다.
> <details>
> <summary>read the caption</summary>
> Table 9: The prompt for domain classification, where ‘{sentence}’ represents the multi-hop query.
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