---
title: "ComplexFuncBench: Exploring Multi-Step and Constrained Function Calling under Long-Context Scenario"
summary: "ComplexFuncBench: 실제 시나리오에서 LLM의 다단계 제약 함수 호출 능력을 평가하는 새로운 벤치마크"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Tsinghua University",]
showSummary: true
date: 2025-01-17
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.10132 {{< /keyword >}}
{{< keyword icon="writer" >}} Lucen Zhong et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-20 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.10132" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.10132" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/complexfuncbench-exploring-multi-step-and" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)이 실시간 API와 통합되어 정확하고 최신 정보를 제공하는 데 중요한 발전을 이루었지만, 복잡한 함수 호출 능력 평가는 여전히 미개척 분야로 남아 있습니다. 기존 벤치마크는 단순한 시나리오에 국한되어 실제 응용 환경에서의 LLM 성능을 정확하게 반영하지 못합니다. 특히 다단계, 제약 조건, 매개변수 추론, 긴 매개변수, 긴 문맥 등 복잡한 요소들을 고려한 평가가 부족합니다.

본 연구는 이러한 한계를 극복하기 위해 **실제 시나리오를 반영한 ComplexFuncBench라는 새로운 벤치마크를 제시**합니다. 이 벤치마크는 다양한 실제 API를 사용한 다단계 및 제약 조건 함수 호출을 포함하며, 매개변수 추론 및 긴 문맥 처리 능력을 평가합니다. 또한, **자동화된 평가 프레임워크인 ComplexEval을 제안**하여 정확하고 효율적인 평가를 가능하게 합니다. ComplexEval은 규칙 기반 매칭, 응답 기반 매칭, LLM 기반 매칭 등의 다차원 매칭 방법을 통해 함수 호출의 정확성을 평가하며, 오류 정보를 제공하여 LLM의 자가 수정 능력까지 평가합니다.  실험 결과는 최첨단 LLM이 복잡한 함수 호출 과제에서 여전히 부족함을 보여주고, 향후 연구 방향을 제시합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} ComplexFuncBench는 다단계 및 제약 조건이 있는 함수 호출을 포함한 실제 시나리오에서 LLM의 기능 호출 성능을 평가하는 새로운 벤치마크입니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} ComplexEval은 다차원 일치 방법을 사용하여 LLM의 복잡한 함수 호출 성능을 자동으로 평가하는 프레임워크입니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 실험 결과는 최첨단 LLM이 복잡한 함수 호출에서 여전히 결함이 있음을 보여주며, 향후 연구를 위한 방향을 제시합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **복잡한 함수 호출을 평가하기 위한 새로운 벤치마크인 ComplexFuncBench와 자동 평가 프레임워크인 ComplexEval을 제시**함으로써, 실제 시나리오에서의 LLM 기능 호출 능력에 대한 이해를 높이는 데 중요한 역할을 합니다. 기존 연구의 한계를 극복하고, 다양한 측면(다단계, 제약 조건, 매개변수 추론, 긴 매개변수, 긴 문맥)을 고려하여 LLM의 복잡한 함수 호출 능력을 정량적으로 평가하는 방법을 제시합니다.  이는 **LLM의 기능 향상 및 실제 응용 프로그램 개발에 직접적으로 기여**하며, 향후 연구 방향을 제시하는 중요한 기여를 합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.10132/x1.png)

> 🔼 그림 1은 두 가지 시나리오에서의 함수 호출 과정을 보여줍니다. (a)는 단순 함수 호출로, 사용자의 질의에 대한 답변을 얻기 위해 단일 함수 호출만 필요한 경우를 나타냅니다. (b)는 복잡한 함수 호출로, 여러 단계의 함수 호출, 제약 조건, 매개변수 값 추론, 긴 매개변수 값 및 긴 컨텍스트를 포함하는 실제 시나리오를 보여줍니다. 각 기능(단계, 제약 조건 등)은 다른 색상으로 표시되어 구분됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: (a) Simple Function Calling. (b) Complex Function Calling with multi-step, constraints, parameter value reasoning, long parameter values and long context. Different colors correspond to the corresponding features marked in the figure.
> </details>





{{< table-caption >}}
| Feature | Real API Response | Multi-Step | Constraints | Parameter Value Reasoning | Long Parameter Values | Long-Context |
|---|---|---|---|---|---|---|
| **API-Bench** | ✗ | ✗ | ✗ | ✗ | ✗ | ✗ |
| **ToolBench** | ✓ | ✓ | ✗ | ✗ | ✗ | ✗ |
| **T-Eval** | ✓ | ✓ | ✗ | ✗ | ✗ | ✗ |
| **BFCL** | ✗ | ✓ | ✗ | ✗ | ✓ | ✓ |
| **Tool Sandbox** | ✗ | ✓ | ✗ | ✗ | ✗ | ✗ |
| **ComplexFuncBench** | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |{{< /table-caption >}}

> 🔼 표 1은 제안된 ComplexFuncBench와 기존 함수 호출 벤치마크 간의 비교 분석 결과를 보여줍니다.  다른 벤치마크들이 단순 함수 호출이나 제한된 상황만 고려하는 반면, ComplexFuncBench는 실제 시나리오를 반영하여 다단계, 제약 조건이 있는 함수 호출, 긴 매개변수, 매개변수 값 추론 및 긴 문맥(Long Context)을 포함하는 복잡한 함수 호출 기능을 평가합니다. 각 벤치마크가 지원하는 기능(여러 API 응답 처리, 다단계 호출, 제약 조건, 매개변수 값 추론, 긴 매개변수 값, 긴 문맥)을 표로 정리하여 비교합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: ComplexFuncBench compare with other function calling benchmarks.
> </details>





### In-depth insights


#### Multi-step Function Calls
연구 논문의 "다단계 함수 호출" 부분에 대한 심층적인 분석 결과를 요약하면 다음과 같습니다. **다단계 함수 호출은 사용자의 질의를 충족하기 위해 여러 개의 함수를 순차적으로 호출하는 과정**을 의미하며, 이는 **단일 함수 호출보다 훨씬 복잡하고 어려운 작업**입니다.  이러한 다단계 함수 호출의 성공 여부는 **각 단계에서의 매개변수 추론 능력,  함수 호출 순서의 정확성,  중간 결과의 정확한 해석** 등에 크게 의존합니다.  논문에서는 이러한 다단계 함수 호출 과정을 효과적으로 평가하기 위한 벤치마크와 평가 프레임워크를 제시하며,  **기존의 단순 함수 호출 평가 방식의 한계를 극복**하기 위해 노력하고 있음을 보여줍니다.  특히 **실제 시나리오를 반영한 다양한 제약 조건과 장기적인 컨텍스트를 고려**하여 평가의 신뢰성을 높이고, **LLM의 기능적 능력을 더욱 정확하게 측정**할 수 있는 방안을 모색하고 있습니다.  **실험 결과를 통해 다양한 LLM의 다단계 함수 호출 능력의 차이**를 분석하고 향후 개선 방향을 제시하는 것도 중요한 부분입니다.

#### Long-Context LLM
장문 맥락을 다루는 거대 언어 모델(LLM)은 **방대한 양의 정보를 처리하고 장기적인 의존성을 이해**할 수 있는 능력을 보여줍니다. 이는 기존의 LLM이 가진 맥락 처리 능력의 한계를 뛰어넘는 중요한 발전입니다.  **긴 문서나 대화 기록 전체를 고려하여 응답을 생성**할 수 있으므로, 보다 정확하고 맥락에 맞는 결과를 제공할 수 있습니다. 하지만, **매개변수의 수가 증가함에 따라 계산 비용과 메모리 사용량이 크게 증가**하는 문제점이 있습니다.  또한, **모델의 훈련 및 평가의 어려움**과 **과적합** 가능성 또한 고려해야 할 부분입니다.  **모델의 크기와 훈련 데이터의 양이 증가**함에 따라 성능 향상이 이루어지지만, 이는  **자원 집약적**이며, **일반화 성능**을 저해할 수도 있습니다. 따라서, **효율적인 메모리 관리 기법**과 **적절한 훈련 전략**의 개발이 **장문 맥락 LLM의 성능 향상과 실용화**에 중요한 역할을 할 것으로 예상됩니다.

#### ComplexFuncBench
ComplexFuncBench는 **장문 컨텍스트 시나리오에서 다단계 및 제약 조건이 있는 함수 호출을 평가하기 위한 벤치마크**로 제시되었습니다. 기존 벤치마크와 달리, ComplexFuncBench는 **실제 시나리오를 반영하여 다단계 함수 호출과 제약 조건을 포함**하며, 매개변수 값 추론, 긴 매개변수 값, 그리고 128k의 긴 컨텍스트를 필요로 합니다. 이를 통해 **LLM의 실제 세계 적용 가능성을 보다 정확하게 평가**할 수 있습니다.  **자동 평가 프레임워크인 ComplexEval**은 규칙 기반 매칭, 응답 기반 매칭, 그리고 LLM 기반 매칭을 결합하여 복잡한 함수 호출의 정확성을 다각적으로 평가합니다. Booking.com의 실제 API를 사용하여 구축된 데이터셋은 5가지 실제 시나리오를 다루고 있으며, 다양한 도메인과 다양한 복잡도의 함수 호출을 포함합니다. 이러한 특징은 기존 연구의 한계를 극복하고 LLM의 함수 호출 능력을 보다 정교하게 분석하는 데 기여하며, **향후 LLM의 기능 개선 및 연구 방향 제시**에 중요한 역할을 할 것으로 기대됩니다.

#### Automated Evaluation
자동 평가는 연구 논문에서 매우 중요한 부분입니다. **자동화된 시스템을 통해 방대한 양의 데이터를 효율적으로 분석하고 정확한 결과를 도출**할 수 있기 때문입니다. 특히, 본 논문에서 제시된 복잡한 함수 호출 시나리오 평가와 같이 인간의 개입이 어려운 경우 자동 평가의 필요성이 더욱 커집니다.  **자동 평가 시스템은 규칙 기반 매칭, 응답 기반 매칭, LLM 기반 매칭 등 다양한 방법론**을 통해 정확성을 높이고, 오류의 원인을 분석하는 데 도움을 줍니다. **정확성과 완성도라는 두 가지 측면**에서 모델의 성능을 평가함으로써, 모델의 강점과 약점을 파악하고 개선 방향을 제시하는 데 기여합니다. 그러나, **자동 평가 시스템 자체의 한계점과 개선 여지**에 대한 논의도 필요합니다. 예를 들어, LLM 기반 매칭은 LLM의 성능에 의존적이므로, LLM의 한계가 자동 평가의 정확성에 영향을 미칠 수 있습니다. 따라서, 자동 평가 시스템의 신뢰성을 높이기 위한 지속적인 연구가 필요합니다.

#### Future Research
본 논문에서 제시된 ComplexFuncBench는 다단계 및 제약 조건이 있는 함수 호출을 포함하여 장문 컨텍스트 시나리오에서 LLM의 기능 호출 능력을 평가하기 위한 포괄적인 벤치마크입니다.  **향후 연구는 몇 가지 방향으로 진행될 수 있습니다.** 첫째, **더욱 다양한 도메인과 복잡한 함수 호출 시나리오를 포함하도록 ComplexFuncBench를 확장**하는 것입니다.  다양한 API와 복잡한 상호 작용을 포함하여 현실 세계 시나리오를 더욱 잘 반영하는 것이 중요합니다.  둘째, **ComplexEval 프레임워크를 개선**하여 함수 호출의 정확성과 완전성을 더욱 정확하게 평가하는 방법을 개발하는 것입니다.  예를 들어,  모델이 생성한 응답의 품질을 평가하기 위해 더욱 정교한 지표와 방법론을 개발하는 것을 고려할 수 있습니다.  셋째, **다양한 모델 아키텍처와 훈련 방법이 복잡한 함수 호출 과제에 어떻게 영향을 미치는지 조사**하는 것입니다.  이를 통해 LLM의 기능 호출 능력을 향상시키는 새로운 아키텍처와 훈련 기술을 개발할 수 있습니다.  마지막으로, **ComplexFuncBench를 사용하여 다른 유형의 LLM에 대한 비교 연구를 수행**하는 것이 중요합니다.  이러한 연구는 다양한 LLM의 강점과 약점을 파악하고 향후 모델 개발을 위한 지침을 제공할 수 있습니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.10132/x2.png)

> 🔼 그림 2는 논문에서 사용된 복잡한 함수 호출 데이터셋 구축 과정을 보여줍니다. (a)는 데이터 수집의 전반적인 흐름을 개략적으로 나타낸 것이고, (b)는 사람이 직접 수정하는 과정의 예시, (c)는 모호성을 제거하는 과정의 예시입니다.  회색으로 표시된 부분은 주석 작업 중에 제거된 부분입니다. 그림에 대한 자세한 설명은 부록 A.1에서 확인할 수 있습니다.  데이터셋은 Booking.com 웹사이트의 실제 API를 기반으로 하며, 다단계 및 제약 조건이 있는 함수 호출 시나리오를 포함하도록 설계되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Overview of the data collection process. (a) is the high-level process of data collection. (b) is the example of human correction process.(c) is the example of disambiguation process. The grey part is removed during annotation. A detailed annotation example is shown in Appendix A.1.
> </details>



![](https://arxiv.org/html/2501.10132/x3.png)

> 🔼 그림 3은 논문에서 제안하는 복잡한 함수 호출 평가 프레임워크인 ComplexEval의 개요를 보여줍니다. 다양한 색상은 API 응답 유형을 나타냅니다. 파란색은 특정 오류 메시지가 포함된 형식 오류를 나타내고, 녹색은 해당하는 정답 API 응답을 가진 정확한 함수 호출을 나타내며, 빨간색은 일반적인 오류 메시지가 포함된 잘못된 함수 호출을 나타냅니다. 이 그림은 ComplexEval의 주요 구성 요소와 함수 호출 평가 과정을 시각적으로 설명합니다.  각 단계에서의 입력과 출력, 그리고 오류 처리 과정을 명확하게 보여주어 ComplexEval의 작동 방식을 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Overview of ComplexEval. Different colors represent different API response types. Color blue represents format error with specific error message. Color green represents correct function call with corresponding golden API response. Color red represents invalid function call with general error message.
> </details>



![](https://arxiv.org/html/2501.10132/extracted/6138262/images/error_analysis.png)

> 🔼 그림 4는 서로 다른 언어 모델들의 오류 유형 분석 결과를 보여줍니다. 각 모델별로 발생한 오류의 비율을 다양한 오류 유형 (함수 오류, 매개변수 누락, 환각, 값 오류, 조기 중지)별로 시각적으로 나타냅니다. 이를 통해 각 모델의 강점과 약점, 특히 어떤 유형의 오류에 취약한지 파악하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Error type analysis for different models.
> </details>



![](https://arxiv.org/html/2501.10132/extracted/6138262/images/value_error_distribution.png)

> 🔼 그림 5는 다양한 매개변수 유형에 대한 여러 모델의 오류율을 보여줍니다.  각 모델은 날짜, 시간, 위치 등 다양한 유형의 매개변수에 대해 다른 오류율을 보입니다. 이는 모델이 특정 유형의 매개변수를 처리하는 데 어려움을 겪는다는 것을 시사합니다. 예를 들어, '필터'와 '구간' 매개변수는 다른 매개변수보다 오류율이 상대적으로 높습니다. 이는 이러한 매개변수가 모델이 함수 호출 순서를 추론해야 하는 과제를 제시하기 때문입니다.  '값 오류'는 모든 모델에서 오류의 상당 부분을 차지합니다. 특히 Qwen2.5-72B 모델은 '값 오류' 비율이 78.8%로 높습니다. 이는 ComplexFuncBench가 제약된 매개변수 값 추론 및 긴 컨텍스트 매개변수 추출에 있어 LLM에 상당한 어려움을 제기한다는 것을 의미합니다.  '값 오류' 외에도, 네 가지 모델 모두 모든 정보를 수집하지 않고 함수 호출을 중단하는 경향이 있습니다.  '함수 오류'는 비교적 드물지만, 모델이 함수 설명을 제대로 이해하지 못한다는 점을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Error rates for each parameter type of different models
> </details>



![](https://arxiv.org/html/2501.10132/x4.png)

> 🔼 그림 6은 다양한 모델에 대한 함수 호출 단계의 분포를 보여줍니다. 각 모델에 대해 함수 호출의 최단 경로와 모델이 예측한 함수 호출 경로의 단계 수를 비교합니다. 이를 통해 각 모델의 함수 호출 전략 및 복잡한 함수 호출에 대한 성능을 파악할 수 있습니다. 특히, 최단 경로보다 더 많은 단계가 필요한 모델의 경우, 그 원인과 개선 방향에 대한 분석이 필요함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Function calling steps distribution.
> </details>



![](https://arxiv.org/html/2501.10132/x5.png)

> 🔼  그림 7은 골든 함수 호출 업데이트의 예시를 보여줍니다. 왼쪽 경로는 세 단계로 이루어진 어노테이션된 최단 함수 호출 경로입니다. 이 그림은 모델이 예측한 함수 호출과 실제 최단 경로의 함수 호출을 비교하여, 모델의 정확성과 효율성을 평가하는 데 사용됩니다. 각 단계에서 모델이 추가적인 함수 호출을 생성하거나, 불필요한 함수 호출을 제거하여 최적의 경로를 찾아가는 과정을 시각적으로 보여줍니다. 최종적으로, 그림은 모델의 함수 호출 능력과 API 활용 능력을 평가하는 데 도움이 되는 시각적 자료를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: An example for golden function call updating. Path on the left is the annotated shortest function call path with three steps.
> </details>



![](https://arxiv.org/html/2501.10132/x6.png)

> 🔼 그림 8은 GPT-4를 사용하여 복잡한 함수 호출을 요구하는 질문 1000개를 생성하는 데 사용된 프롬프트를 보여줍니다. 이 프롬프트는 다양한 도메인(호텔, 항공편, 관광지, 렌터카, 택시)에 걸쳐 복잡한 함수 호출을 생성하는 데 사용된 API 목록과 함께 사용 사례를 제공합니다.  프롬프트는 생성된 각 쿼리가 최소 3개의 연속적인 API 호출을 포함하고, 다양한 문장 구조와 어조를 사용하고, 다양한 주제(자신, 친구, 가족, 회사)를 다루도록 지시합니다. 또한, 날짜, 거리 등의 매개변수에 대한 정확한 정보를 포함하고, 특정 ID와 같은 잘못된 정보를 생성하지 않도록 지시합니다.  프롬프트는 또한 각 API 호출에 필요한 모든 정보가 쿼리에 포함되어 있는지 확인하고, 각 쿼리가 동일한 API를 여러 번 호출할 수 있으며, 각 단계에 여러 개의 병렬 호출이 포함될 수 있음을 강조합니다. 마지막으로 생성된 출력 형식이 JSON 형식을 따라야 함을 지정합니다. 이 프롬프트는 ComplexFuncBench 데이터셋 생성 과정의 중요한 부분으로, 복잡하고 현실적인 시나리오에서 LLM의 기능 호출 능력을 평가하는 데 사용되는 데이터의 품질과 다양성을 보장하는 데 기여합니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Prompt for Query Generation.
> </details>



![](https://arxiv.org/html/2501.10132/x7.png)

> 🔼 그림 9는 데이터셋을 확장하기 위해 사용된 GPT-40 프롬프트를 보여줍니다.  이 프롬프트는 다양한 실제 시나리오를 반영하는 1,000개의 복잡한 함수 호출 샘플을 생성하기 위해 설계되었습니다.  본래 100개의 샘플로 이루어진 초기 데이터셋을 기반으로, GPT-40은 위치, 날짜, 시간 등의 키워드를 변경하여 새로운 쿼리를 생성하고, 어노테이터들이 이를 검토하여 1,000개의 샘플을 완성하도록 합니다.  이 과정에서 문장 구조는 유지되지만, 특정 정보(인원수, 나이, 날짜, 거리, 시간 등)는 변화하여 데이터의 다양성을 확보합니다.  즉, 그림 9는 ComplexFuncBench 데이터셋 구축 과정에서 다양한 샘플을 생성하기 위한 지침을 제공하는 프롬프트의 내용을 보여주는 것입니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Prompt for Query Generalization.
> </details>



![](https://arxiv.org/html/2501.10132/x8.png)

> 🔼 그림 10은 LLM 기반 매칭을 위한 프롬프트를 보여줍니다. 이 프롬프트는 두 개의 함수 호출이 주어진 대화 내역과 함수 설명을 바탕으로 동등한지 여부를 판단하고 그 이유를 제시하는 작업을 LLM에게 지시합니다. 프롬프트는 동등성 판단을 위한 세 가지 기준 (다국어 표현, 의미 동일한 다른 형태의 매개변수, 국가 접미사 유무에 따른 위치 표현)을 명시하고, 매개변수 생략 가능성 및 매개변수 순서의 차이에 대한 고려 사항도 포함합니다.  예시를 통해 JSON 형식의 출력 (is_equal 필드와 reason 필드)을 명확히 제시하고 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Prompt for LLM-based Match.
> </details>



![](https://arxiv.org/html/2501.10132/x9.png)

> 🔼 그림 11은 모델이 생성한 응답이 사용자의 질문에 대해 얼마나 완벽하게 답변하는지를 평가하는 방법을 보여주는 프롬프트입니다.  세 가지 점수(0, 1, 2) 체계를 사용하여 응답의 완전성을 평가하고, 각 점수에 대한 구체적인 설명을 제공합니다.  0점은 질문과 관련된 정보가 전혀 없음을, 1점은 일부 정보만 포함됨을, 2점은 모든 정보를 완벽하게 포함함을 의미합니다.  이 프롬프트는 GPT-40과 같은 대규모 언어 모델을 사용하여 응답의 완전성을 자동으로 평가하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Prompt for Completeness Evaluation.
> </details>



![](https://arxiv.org/html/2501.10132/x10.png)

> 🔼 그림 12는 모델 응답의 정확성을 평가하기 위한 프롬프트(지시문)를 보여줍니다.  API 응답과 일치하는지 여부를 평가하는 기준과, 정확도 점수(0, 1, 2)를 매기는 방법, 점수에 대한 이유를 설명하는 방법 등이 자세히 제시되어 있습니다. 대화 내역, 함수 호출, API 응답 등을 포함한 전체적인 문맥을 고려하여 응답의 정확성을 판단하는 방식을 설명합니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Prompt for Correctness Evaluation.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | Hotels Success | Hotels Call Acc | Flights Success | Flights Call Acc | Car Rental Success | Car Rental Call Acc | Attraction Success | Attraction Call Acc | Cross Success | Cross Call Acc | Overall Success | Overall Call Acc | Completeness | Correctness |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| **close-source models** |  |  |  |  |  |  |  |  |  |  |  |  |  |
| Claude-3.5-Haiku | 36.00 | 50.62 | 50.67 | 75.63 | 59.33 | 74.05 | 58.00 | 75.37 | 38.00 | 70.00 | 45.80 | 69.50 | 1.79 | 1.71 |
| Claude-3.5-Sonnet | 54.67 | 68.17 | 54.00 | 79.50 | 76.67 | 86.01 | 69.33 | 83.33 | 57.00 | 79.33 | 61.00 | 79.27 | 1.84 | 1.85 |
| GLM-4-Long | 56.00 | 63.98 | 66.67 | 84.38 | 77.33 | 85.71 | 72.67 | 83.33 | 40.50 | 72.75 | 57.10 | 76.35 | 1.72 | 1.74 |
| GPT-4-Turbo | 54.67 | 68.48 | 48.67 | 76.5 | 44.67 | 71.14 | 70.67 | 76.48 | 41.75 | 69.38 | 49.50 | 71.38 | 1.72 | 1.81 |
| GPT-4o | 70.00 | 81.99 | 65.33 | 85.50 | 72.00 | 86.88 | 82.00 | 87.59 | 42.75 | 75.13 | 60.50 | 80.55 | 1.66 | 1.75 |
| **open-source models** |  |  |  |  |  |  |  |  |  |  |  |  |  |
| Qwen2.5-7B | 2.00 | 20.65 | 0.00 | 5.13 | 4.67 | 6.41 | 14.67 | 35.18 | 4.5 | 21.41 | 5.0 | 18.19 | 1.5 | 1.47 |
| Llama-3.1-8B | 0.00 | 0.00 | 0.00 | 1.00 | 0.00 | 1.89 | 0.67 | 2.78 | 0.00 | 1.00 | 0.10 | 1.34 | 0.18 | 0.09 |
| GLM-4-9B | 19.33 | 31.52 | 11.33 | 34.00 | 16.0 | 25.36 | 10.67 | 29.26 | 2.00 | 25.46 | 9.40 | 27.97 | 1.15 | 1.03 |
| Llama-3.1-70B | 2.00 | 10.71 | 0.67 | 2.63 | 6.67 | 10.06 | 4.67 | 11.11 | 1.50 | 8.13 | 2.70 | 8.17 | 0.67 | 0.36 |
| Llama-3.1-405B | 3.33 | 13.51 | 2.66 | 10.75 | 4.00 | 15.74 | 14.00 | 18.52 | 1.00 | 9.21 | 4.00 | 11.87 | 0.43 | 0.30 |
| Qwen2.5-72B | 40.00 | 60.24 | 31.33 | 49.25 | 48.67 | 57.58 | 63.33 | 67.41 | 31.50 | 59.00 | 40.10 | 58.32 | 1.80 | 1.75 |
| Mistral Large 2 | 19.33 | 34.32 | 20.67 | 52.88 | 40.67 | 58.16 | 25.33 | 40.18 | 10.50 | 50.54 | 20.10 | 48.78 | 0.94 | 1.0 |{{< /table-caption >}}
> 🔼 표 2는 논문에서 제시된 다양한 언어 모델들의 복잡한 함수 호출 기능 평가 결과를 보여줍니다. 모델들은 소스 코드 공개 여부, 매개변수 크기(10B 미만, 10B 이상)에 따라 세 가지 범주로 분류됩니다. 각 범주 내 상위 두 모델의 결과는 굵은 글씨와 밑줄로 강조 표시되어 있습니다. 표에는 각 모델의 성공률, 정확도, 완성도, 정확성 점수 등이 포함되어 있으며, 개별 도메인(호텔, 항공, 렌터카, 관광, 택시)별 성능과 전체 성능을 비교하여 각 모델의 강점과 약점을 분석하는 데 도움이 되는 정보를 제공합니다. 특히 오픈소스 모델의 경우, 특정 버전 정보가 명시되어 있어 결과 해석에 유용합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Main Results. We categorize models as close-source, open-source under 10B, and open-source above 10B. Top two results for each category are highlighted in bold and underline. The specific endpoint of open-source models are: gpt-4o-2024-08-06, gpt-4-turbo-2024-04-09, claude-3-5-sonnet-20241022 and claude-3-5-haiku-20241022.
> </details>

{{< table-caption >}}
|             | Hotels | Flights | Car Rental | Attraction | Cross | Total |
|-------------|--------|---------|-------------|------------|-------|-------|
| # Samples   | 150     | 150      | 150          | 150        | 400   | 1000  |
| Avg. Steps  | 3.33    | 3.33     | 2.87         | 2.86       | 3.5   | 3.26  |
| Avg. Calls  | 4.29    | 5.33     | 4.57         | 3.6        | 6.0   | 5.07  |{{< /table-caption >}}
> 🔼 ComplexFuncBench 데이터셋의 통계 정보를 보여주는 표입니다.  샘플 수, 평균 단계 수, 평균 호출 수를 호텔, 항공편, 렌터카, 관광, 택시 등 다섯 가지 도메인별로 그리고 전체적으로 나타냅니다. 이 표는 ComplexFuncBench 데이터셋의 규모와 복잡성을 파악하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Data statistics for ComplexFuncBench.
> </details>

{{< table-caption >}}
| Parameter | Example | Explanation |
|---|---|---|
| filter | filter = "facility::433, facility::107" | The filter parameter can be retrieved from the API response of the Get_Filter function. It often appears in queries with constraints, like: Find a few hotels with a pool and free wifi. "facility::433" and "facility::107" denote pool and free wifi, respectively. |
| legs | legs=[{"fromId": "DFW.CITY", "toId": "MUC.AIRPORT", "date": "2024-11-25"},{"fromId": "MUC.AIRPORT", "toId": "STO.CITY", "date": "2024-11-26"}, {"fromId": "STO.CITY","toId": "DFW.CITY","date": "2024-12-09"}] | The legs parameter is the multi-stop flights list which contains location and date. |
| token | token="d7699_H4sIAAAAAAAA_ … AAA." | The token parameter can be retrieved from the API response of multiple functions. For example, the Search_Flights function will return the token for different flights. |
| slug | slug="pr7jepixwlvr-private-guided-tour-orsay-museum-rare-languages" | The slug parameter can be retrieved from the API response of Search_Attraction_Location function as as 'productSlug' inside 'products' or 'destinations'. |
| date | date="2024-11-22" | Parameters related to dates, like: check-in-date, check-out-date,etc. |
| location | location="Amsterdam" | Parameters related to locations, like: country, city ,etc. |
| key | key= "eyJkcml2ZXJzQWdlIjozMCwiZ HJvcE…19GRUVTIl19" | The key parameter can be retrieved from the API response of multiple functions. For example, the Search_Car_Rentals function will return the key for different cars. |
| id | id="eyJ1ZmkiOi01NjQwNjR9" | The id parameter can be retrieved from the API response of multiple functions. For example, the Search_Attraction_Location function will return the id for different attractions. |
| time | time="08:00" | Parameters related to time, like: pick-up-time, drop-off-time,etc. |
| sort_by | sort_by="popularity" | The sort_by parameter controls the order in which hotel or flight results are presented. For example, the hotels can be sorted by price or popularity. |
| type | type="landmark" | The type parameter is the entity type, like landmark, city, etc. |
| age | age="8" | The age parameter is the age of people. |
| people | people=2 | The people parameter is the number of people. |{{< /table-caption >}}
> 🔼 표 4는 논문에서 다루는 다양한 매개변수 유형의 예시들을 보여줍니다. 각 매개변수 유형에 대한 설명과 함께 구체적인 예시 값들이 제시되어 있어, 모델이 실제 API 호출 시 다양한 매개변수들을 이해하고 사용하는 데 도움이 됩니다.  매개변수 유형에는 필터, 구간, 토큰, 슬러그, 날짜, 위치, 키, ID, 시간, 정렬 기준, 유형, 나이, 인원 등이 포함됩니다. 각 유형에 대한 설명과 예시를 통해 복잡한 함수 호출 시나리오에서 매개변수 처리 방법을 보다 명확하게 이해할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Examples of different parameter types.
> </details>

{{< table-caption >}}
| Query |  | 
|---|---| 
| **Initial** | My friend is planning a trip between December 15, 2024 and December 20, 2024 and he wants to fly from Sydney to Melbourne. Please help find the best flight options and book a 4star hotel near Fitzroy Gardens. They also need to rent a car and a taxi service from Melbourne Airport to the hotel. | 
| **Human Annotated** | Please help my friend finds the best flight from Sydney to Melbourne on 15 December 2024 and book a hotel within 10km of Fitzroy Gardens, Melbourne for one night. Remember to book a taxi to pick him up from the airport to the hotel an hour after the plane lands. | 
| **Explanation** | **Correction**. Rewrite query for clarity, such as the number of days for the hotel reservation, the departure location, and the time for the taxi. | 
| **Function call at step 1** |  | 
| **GPT Generated** | 1. {"name": "Search_Flight_Location", "arguments": {"query": "Sydney"}} | 
|  | 2. {"name": "Search_Flight_Location", "arguments": {"query": "Melbourne"}} | 
|  | 3. {"name": "Location_to_Lat_Long", "arguments": {"query": "Fitzroy Gardens, Melbourne"}} | 
|  | 4. {"name": "Taxi_Search_Location", "arguments": {"query": "Melbourne Airport"}} | 
| **Human Annotated** | 1. {"name": "Search_Flight_Location", "arguments": {"query": "Sydney"}} | 
|  | 2. {"name": "Search_Flight_Location", "arguments": {"query": "Melbourne"}} | 
|  | 3. {"name": "Location_to_Lat_Long", "arguments": {"query": "Fitzroy Gardens, Melbourne"}} | 
| **Explanation** | **Correction**. The arrive airport for the best flight may not be "Melbourne Airport". The model need to get the arrive airports before use "Taxi_Search_Location". | 
| **API response at step 1** |  | 
| **Initial** | 1. {"message": "Success", "data": [{"id": "SYD.AIRPORT", "name": "Sydney Kingsford Smith Airport"}, {"id": "YQY.AIRPORT", "name": "Sydney (Nova Scotia) Airport"}]} | 
|  | 2. {"message": "Success", "data": [{"id": "MEL.CITY", "name": "Melbourne"}, {"id": "MEL.AIRPORT", "name": "Melbourne Airport"}, {"id": "AVV.AIRPORT", "name": "Avalon Airport"}, {"id": "MEB.AIRPORT", "name": "Essendon Fields Airport"}, {"id": "MLB.AIRPORT", "name": "Melbourne International Airport"}]} | 
|  | 3. {"message": "Success", "data": [{"business_status": "OPERATIONAL", "formatted_address": "Wellington Parade, East Melbourne VIC 3002, Australia", "geometry": {"location": {"lat": -37.81272149999999, "lng": 144.9800679}},"name": "Fitzroy Gardens"}]} | 
|  | 4. {"message": "Success", "data": [{"longitude": 144.849, "city": "Melbourne", "name": "Melbourne Airport", "latitude": -37.6696}, {"city": "Melbourne", "longitude": -80.6456, "name": "Melbourne International Airport", "latitude": 28.1025}]} | 
| **Human Annotated** | 1. {"message": "Success", "data": [{ "id": "SYD.AIRPORT", "name": "Sydney Kingsford Smith Airport"}]}, | 
|  | 2. {"message": "Success", "data": [{"id": "MEL.CITY", "name": "Melbourne"}]}, | 
|  | 3. {"message": "Success", "data": [{"business_status": "OPERATIONAL", "formatted_address": "Wellington Parade, East Melbourne VIC 3002, Australia", "geometry": {"location": {"lat": -37.81272149999999, "lng": 144.9800679}},"name": "Fitzroy Gardens"}]} | 
| **Explanation** | **Disambiguation**. Delete API response that may cause ambiguation for subsequent steps. | 
| **Function call at step 2** |  | 
| **GPT Generated** | 1. {"name": "Search_Flights", "arguments": {"fromId": "SYD.AIRPORT", "toId": "MEL.CITY", "departDate": "2024-12-15", "sort": "BEST"}} | 
|  | 2. {"name": "Search_Flights", "arguments": {"fromId": "YQY.AIRPORT", "toId": "MEL.CITY", "departDate": "2024-12-15", "sort": "BEST"}} | 
|  | 3. {"name": "Search_Flights", "arguments": {"fromId": "SYD.AIRPORT", "toId": "AVV.AIRPORT", "departDate": "2024-12-15", "sort": "BEST"}} | 
|  | 4. {"name": "Search_Flights", "arguments": {"fromId": "YQY.AIRPORT", "toId": "AVV.AIRPORT", "departDate": "2024-12-15", "sort": "BEST"}} | 
|  | 5. {"name": "Search_Hotels_By_Coordinates", "arguments": {"latitude": "-37.81272149999999", "longitude": "144.9800679", "arrival_date": "2024-12-15", "departure_date": "2024-12-20", "radius": 10}} | 
| **Human Annotated** | 1. {"name": "Search_Flights", "arguments": {"fromId": "SYD.AIRPORT", "toId": "MEL.CITY", "departDate": "2024-12-15", "sort": "BEST"}} | 
|  | 2. {"name": "Search_Hotels_By_Coordinates", "arguments": {"latitude": "-37.81272149999999", "longitude": "144.9800679", "arrival_date": "2024-12-15", "departure_date": "2024-12-20", "radius": 10}} | 
| **Explanation** | **Correction**. After delete ambiguous information in the API response, we need to remove redundant function calls. | {{< /table-caption >}}
> 🔼 표 5는 실제 API 응답에서 많은 내용을 제거하여 가독성을 높이기 위해 편집된 주석 예시를 보여줍니다. 실제 API 응답은 128k 길이의 긴 컨텍스트를 포함하는 방대한 양의 정보를 담고 있습니다. 이 표는 질의, 사람이 작성한 주석, GPT가 생성한 함수 호출, API 응답 및 각 단계에 대한 설명을 보여줍니다.  각 단계의 함수 호출은 질의의 요구사항을 충족하기 위해 여러 API를 사용해야 하는 다중 단계 과정임을 보여줍니다. API 응답의 모호성을 제거하고 가장 짧은 함수 호출 경로를 얻기 위한 주석 수정 과정도 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Annotation Example. To make the content easy for reading, we have removed most of the content from the API response. The actual API response contains a large amount of information, reaching a context length of 128k.
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
{{< /gallery >}}