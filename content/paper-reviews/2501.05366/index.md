---
title: "Search-o1: Agentic Search-Enhanced Large Reasoning Models"
summary: "Search-01은 에이전트 기반 검색을 통합하여 LLM의 추론 능력을 강화하는 획기적인 프레임워크입니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Renmin University of China",]
showSummary: true
date: 2025-01-09
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.05366 {{< /keyword >}}
{{< keyword icon="writer" >}} Xiaoxi Li et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-09 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.05366" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.05366" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/search-o1-agentic-search-enhanced-large" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)은 뛰어난 추론 능력을 보이지만, 지식 부족으로 인해 오류가 발생하는 경우가 많습니다.  기존의 RAG(Retrieval-Augmented Generation) 방식은 이러한 문제를 완전히 해결하지 못합니다.  **외부 지식 검색의 효율성과 신뢰성이 부족**하고, **검색된 문서의 과다한 정보로 인해 추론 과정의 일관성이 깨질 수 있기 때문입니다. 

본 논문에서는 **Search-01**이라는 새로운 프레임워크를 제시합니다. Search-01은 **에이전트 기반의 RAG 메커니즘**과 **검색된 문서를 정제하는 Reason-in-Documents 모듈**을 결합하여 이러한 문제점을 해결합니다.  **동적 외부 지식 검색을 통해 추론 과정의 일관성 유지** 및 **신뢰성 높은 결과**를 도출합니다.  다양한 복잡 추론 과제에서의 실험 결과는 Search-01의 우수한 성능을 보여줍니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} Search-01은 에이전트 기반 검색을 통해 LLM의 추론 과정에 동적으로 외부 지식을 통합합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} Reason-in-Documents 모듈은 검색된 문서의 신뢰도를 높이고 일관된 추론 흐름을 유지합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 과학, 수학, 코딩 등 다양한 복잡 추론 과제에서 Search-01의 우수한 성능이 실험적으로 입증되었습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **복잡한 추론 과제에서 LLM의 신뢰성과 적용 가능성을 향상**시키는 데 중요한 의미를 지닙니다.  이는 현재 널리 퍼져있는 **RAG(Retrieval-Augmented Generation) 기반의 LLM 연구 동향에 직접적으로 기여**하며, **추후 연구를 위한 새로운 방향**을 제시합니다.  특히, **복잡한 추론 문제에 대한 LLM의 성능 향상**은 인공지능 분야 전반에 걸쳐 막대한 영향을 미칠 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.05366/x1.png)

> 🔼 그림 1은 QwQ-32B-Preview 모델을 사용한 추론 과정에서의 불확실성 분석 결과를 보여줍니다. 왼쪽은 추론 과정 중에 확인된 불확실한 단어들의 예시를 보여주고, 오른쪽은 GPQA 다이아몬드 세트의 출력 결과에서 고빈도 불확실 단어의 평균 출현 횟수를 나타냅니다. 왼쪽 그림은 모델이 추론 과정에서 확신하지 못하는 부분을 보여주는 대표적인 단어들을 예시로 제시하여 모델의 불확실성을 직관적으로 보여줍니다. 오른쪽 그림은 불확실성을 수치적으로 측정하여 모델의 전반적인 추론 신뢰도를 평가하는 데 도움을 줍니다.  두 그림을 통해 모델의 추론 과정에서 발생하는 불확실성의 유형과 빈도를 파악하고,  모델의 성능 향상을 위한 방향을 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  Analysis of reasoning uncertainty with QwQ-32B-Preview. Left: Examples of uncertain words identified during the reasoning process. Right: Average occurrence of high-frequency uncertain words per output in the GPQA diamond set.
> </details>





{{< table-caption >}}
| Cases of Model-Expressed Uncertainty |
|---|---|---|---|---|
| **Wait,** **perhaps** it’s referring to dimethyl sulfone, but that doesn’t seem right. |
| **Alternatively,** **perhaps** there’s a mistake in my understanding of epistasis. Let me look up epistasis quickly. Epistasis is … |
| **Alternatively,** HBr could also abstract a hydrogen atom from the alkene, leading to a … |
| As I recall, Quinuclidine is a seven-membered ring with a nitrogen atom, **likely** not having the required symmetry. |{{< /table-caption >}}

> 🔼 표 1은 과학, 수학, 코드 벤치마크를 포함한 어려운 추론 작업에 대한 주요 결과를 보여줍니다. Pass@1 지표를 모든 작업에 대해 보고합니다. 32B 매개변수를 가진 모델의 경우 최상의 결과는 굵게 표시되고 두 번째로 좋은 결과는 밑줄이 그어져 있습니다. 더 크거나 비독점적인 모델의 결과는 참조를 위해 회색으로 표시됩니다. 기호 “†”는 공식 출시의 결과를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Main results on challenging reasoning tasks, including PhD-level science QA, math, and code benchmarks. We report Pass@1 metric for all tasks. For models with 32B parameters, the best results are in bold and the second-best are underlined. Results from larger or non-proprietary models are in gray color for reference. Symbol “†” indicates results from their official releases.
> </details>





### In-depth insights


#### Agentic RAG
본 논문에서 제시된 에이전틱 RAG(Agentic RAG)는 기존의 RAG(Retrieval-Augmented Generation) 방식을 능동적으로 개선한 접근 방식입니다. **기존 RAG는 질문에 대한 답변을 생성하기 위해 사전에 정의된 검색어를 사용하여 정보를 검색하는 수동적인 방식**이지만, 에이전틱 RAG는 **모델이 스스로 검색 시점과 검색어를 결정**합니다. 이는 **모델의 불확실성이나 지식 부족을 감지**하고, **필요에 따라 능동적으로 외부 지식을 검색**하여 추론 과정에 통합하는 것을 의미합니다. 따라서 **더욱 정확하고 신뢰할 수 있는 추론 결과**를 얻을 수 있습니다.  **에이전틱 RAG의 핵심은 모델의 자율성**에 있습니다. 모델이 자신의 지식과 추론 과정을 스스로 모니터링하고, 부족한 부분을 파악하여 적절한 시점에 검색을 통해 보완하는 것입니다. 이를 통해 단순히 정보를 획득하는 것을 넘어, **추론 과정의 흐름을 유지하면서 효율적으로 외부 지식을 활용**할 수 있습니다.  결과적으로, **에이전틱 RAG는 더욱 강력하고 유연한 지능 시스템**을 구축하는 데 중요한 역할을 할 것으로 기대됩니다.

#### Reason-in-Docs
논문에서 제시된 'Reason-in-Docs' 모듈은 검색된 문서에서 추출된 정보를 단순히 LRM에 직접 주입하는 대신 **중요하고 간결한 정보만을 추출하여 기존 추론 과정에 매끄럽게 통합**하는 역할을 합니다.  **문서의 장황함과 관련 없는 정보는 제거**하여 추론 흐름을 방해하지 않고, **LRM의 추론 능력을 최대한 활용**할 수 있도록 합니다.  즉, 단순한 정보 검색 및 삽입을 넘어 **심층적인 분석 및 정제 과정**을 거쳐 LRM의 추론 과정에 최적화된 형태로 정보를 제공하는 것이 핵심입니다.  이를 통해 **추론의 정확성과 일관성을 높이고**, 외부 지식 활용의 효율성을 극대화하여 더욱 신뢰할 수 있는 지능형 시스템 구축에 기여하는 모듈이라고 할 수 있습니다.

#### Search-o1
본 논문에서 제시된 **Search-o1 프레임워크는 대규모 추론 모델(LRM)의 지식 부족 문제를 해결하기 위한 혁신적인 시도**입니다. 기존의 LRM은 장황한 추론 과정으로 인해 지식의 불확실성과 오류 가능성에 취약한데, Search-o1은 **에이전트 기반 검색과 문서 내 추론 모듈을 통합**하여 이 문제를 해결합니다. 에이전트 기반 검색은 LRM이 불확실한 지점을 만나면 외부 지식을 동적으로 검색하여 추론 과정에 통합하는 역할을 합니다.  **문서 내 추론 모듈은 검색된 문서들을 심층 분석하여 잡음을 최소화하고 일관된 추론 흐름을 유지**하도록 설계되었습니다. 과학, 수학, 코딩 등 다양한 복잡한 추론 과제에서 Search-o1의 성능이 우수함을 실험을 통해 입증하였으며, 이는 **LRM의 신뢰성과 적용 가능성을 향상**시키는 중요한 결과입니다.  **Search-o1은 LRM의 한계를 극복하고 더욱 강력하고 다재다능한 지능 시스템을 구축**하는 데 기여할 것으로 기대됩니다.

#### Benchmark Results
본 논문의 벤치마크 결과는 제시된 모델의 성능을 다양한 측면에서 평가한 **핵심적인 부분**입니다.  다양한 기준(예: 정확도, 효율성, 일반화 성능)에 따른 벤치마크 결과 분석을 통해 **모델의 강점과 약점**을 명확히 파악하고, 다른 최첨단 모델들과의 비교를 통해 **상대적인 우위**를 제시하는 것이 중요합니다. 특히, **다양한 유형의 과제** (예: 과학, 수학, 코딩 관련 문제)에 대한 벤치마크 결과를 제시하여 모델의 **범용성**을 평가하고, **실제 응용 가능성**을 높이는 데 초점을 맞춰야 합니다.  결과 해석 과정에서는 **통계적 유의성**을 고려하고, 결과의 신뢰도를 높이기 위한 **추가적인 실험**이나 분석이 필요할 수 있습니다.  **결론적으로**, 벤치마크 결과는 논문의 주장을 뒷받침하는 **결정적인 증거**로, 모델의 성능과 실용성에 대한 객관적인 평가를 제공해야 합니다.

#### Future of LRMs
**대규모 추론 모델(LRM)**의 미래는 **지식 획득 및 추론 능력 향상**에 달려 있습니다.  **에이전트 기반 검색 및 RAG(Retrieval-Augmented Generation) 기법**의 발전은 LRM이 외부 지식을 효율적으로 활용하여 불확실성을 줄이고 더욱 정확한 추론을 가능하게 할 것입니다.  **Reason-in-Documents 모듈**과 같은 지식 정제 기술은 검색된 정보의 잡음을 제거하고 추론 흐름을 일관되게 유지하는 데 중요한 역할을 할 것입니다.  **복합적인 추론 과제**에 대한 성능 향상과 더불어, **신뢰성과 적용성 확대**를 위한 연구가 지속적으로 필요합니다.  이는 **다양한 도메인에서의 실험 및 평가**, 그리고 **인간 수준의 추론 능력에 대한 지속적인 연구**를 통해 가능할 것입니다.  궁극적으로 LRM의 미래는 **더욱 신뢰할 수 있고 다재다능한 지능형 시스템**의 구축으로 이어질 것입니다.  **자율적인 지식 획득 및 정제**, 그리고 **일관성 있는 추론 능력**이 향상된 LRM은 인간의 문제 해결 능력을 뛰어넘는, 보다 혁신적이고 강력한 지능형 시스템으로 진화할 가능성이 높습니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.05366/x2.png)

> 🔼 그림 2는 세 가지 추론 방법(직접 추론, 에이전트 기반 검색 증강 추론, Search-01)을 비교하여 보여줍니다. (a) 직접 추론 방법은 외부 지식을 활용하지 않기 때문에 지식 부족으로 인한 부정확성이 발생할 수 있습니다. (b) 에이전트 기반 검색 증강 추론은 외부 지식 접근성을 향상시키지만, 과도하게 길고 중복된 문서를 반환하여 추론의 일관성을 저해할 수 있습니다. (c) Search-01은 간결하고 정확한 검색 결과를 추론 과정에 매끄럽게 통합하여 정확하고 일관된 문제 해결을 가능하게 합니다. Search-01은 에이전트 기반 검색과 문서 내 추론 모듈을 결합하여 이러한 문제를 해결합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2:  Comparison of reasoning approaches: (a) Direct reasoning without retrieval often results in inaccuracies due to missing knowledge. (b) Our agentic retrieval-augmented reasoning approach improves knowledge access but usually returns lengthy, redundant documents, disrupting coherent reasoning. (c) Our Search-o1 integrates concise and accurate retrieved knowledge seamlessly into the reasoning process, enabling precise and coherent problem-solving.
> </details>



![](https://arxiv.org/html/2501.05366/x3.png)

> 🔼 본 그림은 추론 과정에 사용된 상위 k개 검색 문서의 수에 따른 성능 변화를 보여줍니다. QwQ-32B-Preview 모델을 기반으로, 검색 문서의 수가 증가함에 따라 복잡한 추론 작업에서의 성능이 향상되는 것을 확인할 수 있습니다. 특히, 하나의 문서만 검색해도 직접 추론 및 표준 RAG(Retrieval-Augmented Generation) 모델보다 성능이 우수하며, 이는 본 논문에서 제시하는 에이전트 기반 검색 및 문서 내 추론 전략의 효과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3:  Scaling analysis of top-k retrieved documents utilized in reasoning. All results are based on QwQ-32B-Preview model.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | GPQA (PhD-Level Science QA) |  |  |  | Math Benchmarks |  |  | LiveCodeBench |  |  |  | 
|---|---|---|---|---|---|---|---|---|---|---|---| 
|  | Physics | Chemistry | Biology | Overall | MATH500 | AMC23 | AIME24 | Easy | Medium | Hard | Overall | 
| **Direct Reasoning (w/o Retrieval)** |  |  |  |  |  |  |  |  |  |  |  | 
| Qwen2.5-32B | 57.0 | 33.3 | 52.6 | 45.5 | 75.8 | 57.5 | 23.3 | 42.3 | 18.9 | 14.3 | 22.3 | 
| Qwen2.5-Coder-32B | 37.2 | 25.8 | 57.9 | 33.8 | 71.2 | 67.5 | 20.0 | 61.5 | 16.2 | 12.2 | 25.0 | 
| QwQ-32B | 75.6 | 39.8 | 68.4 | 58.1 | 83.2 | 82.5 | 53.3 | 61.5 | 29.7 | 20.4 | 33.0 | 
| Qwen2.5-72B | 57.0 | 37.6 | 68.4 | 49.0 | 79.4 | 67.5 | 20.0 | 53.8 | 29.7 | 24.5 | 33.0 | 
| Llama3.3-70B | 54.7 | 31.2 | 52.6 | 43.4 | 70.8 | 47.5 | 36.7 | 57.7 | 32.4 | 24.5 | 34.8 | 
| DeepSeek-R1-Lite† | - | - | - | 58.5 | 91.6 | - | 52.5 | - | - | - | 51.6 | 
| GPT-4o† | 59.5 | 40.2 | 61.6 | 50.6 | 60.3 | - | 9.3 | - | - | - | 33.4 | 
| o1-preview† | 89.4 | 59.9 | 65.9 | 73.3 | 85.5 | - | 44.6 | - | - | - | 53.6 | 
| **Retrieval-augmented Reasoning** |  |  |  |  |  |  |  |  |  |  |  | 
| RAG-Qwen2.5-32B | 57.0 | 37.6 | 52.6 | 47.5 | 82.6 | 72.5 | 30.0 | 61.5 | 24.3 | 8.2 | 25.9 | 
| RAG-QwQ-32B | 76.7 | 38.7 | 73.7 | 58.6 | 84.8 | 82.5 | 50.0 | 57.7 | 16.2 | 12.2 | 24.1 | 
| RAgent-Qwen2.5-32B | 58.1 | 33.3 | 63.2 | 47.0 | 74.8 | 65.0 | 20.0 | 57.7 | 24.3 | 6.1 | 24.1 | 
| RAgent-QwQ-32B | 76.7 | 46.2 | 68.4 | 61.6 | 85.0 | 85.0 | 56.7 | 65.4 | 18.9 | 12.2 | 26.8 | 
| **Retrieval-augmented Reasoning with Reason-in-Documents** |  |  |  |  |  |  |  |  |  |  |  | 
| Search-o1 (Ours) | 77.9 | 47.3 | 78.9 | 63.6 | 86.4 | 85.0 | 56.7 | 57.7 | 32.4 | 20.4 | 33.0 | {{< /table-caption >}}
> 🔼 표 2는 GPQA 확장 데이터셋 [52]에서 인간 전문가와의 성능 비교를 보여줍니다.  물리학, 화학, 생물학 세 가지 영역에서 인간 전문가 그룹의 정답률과, QwQ-32B 모델(단독 추론, RAG 기반 추론, Search-01)의 정답률을 비교하여 Search-01 모델의 성능 우수성을 보여줍니다.  각 영역별 및 전체 정답률을 제시하여 Search-01 모델이 인간 전문가 수준 또는 그 이상의 성능을 달성했는지 확인합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Performance comparison with human experts on the GPQA extended set [52].
> </details>

{{< table-caption >}}
| Method | Physics | Chemistry | Biology | Overall |
|---|---|---|---|---|
| **Human Experts** |  |  |  |  |
| Physicists | 57.9 | 31.6 | 42.0 | 39.9 |
| Chemists | 34.5 | 72.6 | 45.6 | 48.9 |
| Biologists | 30.4 | 28.8 | 68.9 | 37.2 |
| **Reasoning Models** |  |  |  |  |
| QwQ-32B | 61.7 | 36.9 | 61.0 | 51.8 |
| RAG-QwQ-32B | 64.3 | 38.3 | 66.7 | 54.6 |
| Search-o1 (Ours) | 68.7 | 40.7 | 69.5 | 57.9 |{{< /table-caption >}}
> 🔼 표 3은 단일 홉 QA 및 다중 홉 QA 데이터 세트를 포함한 오픈 도메인 QA 작업에 대한 성능 비교를 보여줍니다. 32B 매개변수를 가진 모델의 경우 최상의 결과는 굵게 표시되고 두 번째로 좋은 결과는 밑줄이 그어져 있습니다. 더 큰 모델의 결과는 참조를 위해 회색으로 표시됩니다. 이 표는 다양한 모델의 오픈 도메인 질문응답 성능을 비교 분석하여 각 모델의 강점과 약점을 파악하고, 특히 단일 홉과 다중 홉 질문에 대한 성능 차이를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Performance comparison on open-domain QA tasks, including single-hop QA and multi-hop QA datasets. For models with 32B parameters, the best results are in bold and the second-best are underlined. Results from larger models are in gray color for reference.
> </details>

{{< table-caption >}}
| Method | Single-hop QA |  |  |  | Multi-hop QA |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|  | NQ |  | TriviaQA |  | HotpotQA |  | 2WIKI |  | MuSiQue |  | Bamboogle |  |
|  | EM | F1 | EM | F1 | EM | F1 | EM | F1 | EM | F1 | EM | F1 |
| **Direct Reasoning (w/o Retrieval)** |  |  |  |  |  |  |  |  |  |  |  |  |
| Qwen2.5-32B | 22.8 | 33.9 | 52.0 | 60.3 | 25.4 | 34.7 | 29.8 | 36.3 | 8.4 | 18.0 | 49.6 | 63.2 |
| QwQ-32B | 23.0 | 33.1 | 53.8 | 60.7 | 25.4 | 33.3 | 34.4 | 40.9 | 9.0 | 18.9 | 38.4 | 53.7 |
| Qwen2.5-72B | 27.6 | 41.2 | 56.8 | 65.8 | 29.2 | 38.8 | 34.4 | 42.7 | 11.4 | 20.4 | 47.2 | 61.7 |
| Llama3.3-70B | 36.0 | 48.7 | 68.8 | 76.8 | 37.8 | 49.1 | 46.0 | 54.2 | 14.8 | 23.6 | 54.4 | 67.8 |
| **Retrieval-augmented Reasoning** |  |  |  |  |  |  |  |  |  |  |  |  |
| RAG-Qwen2.5-32B | 33.4 | 49.3 | 65.8 | 79.2 | 38.6 | 50.4 | 31.6 | 40.6 | 10.4 | 19.8 | 52.0 | 66.0 |
| RAG-QwQ-32B | 29.6 | 44.4 | 65.6 | 77.6 | 34.2 | 46.4 | 35.6 | 46.2 | 10.6 | 20.2 | 55.2 | 67.4 |
| RAgent-Qwen2.5-32B | 32.4 | 47.8 | 63.0 | 72.6 | 44.6 | 56.8 | 55.4 | 69.7 | 13.0 | 25.4 | 54.4 | 66.4 |
| RAgent-QwQ-32B | 33.6 | 48.4 | 62.0 | 74.0 | 43.0 | 55.2 | 58.4 | 71.2 | 13.6 | 25.5 | 52.0 | 64.7 |
| **Retrieval-augmented Reasoning with Reason-in-Documents** |  |  |  |  |  |  |  |  |  |  |  |  |
| Search-o1 (Ours) | 34.0 | 49.7 | 63.4 | 74.1 | 45.2 | 57.3 | 58.0 | 71.4 | 16.6 | 28.2 | 56.0 | 67.8 |{{< /table-caption >}}
> 🔼 표 4는 Search-o1 모델이 GPQA 데이터셋의 질문에 대해 추론하는 과정을 보여주는 예시입니다. 표에는 검색어와 검색 결과가 각각 녹색과 파란색 상자로 강조 표시되어 있습니다. 이를 통해 Search-o1 모델이 질문에 대한 답을 찾기 위해 어떻게 검색을 수행하고, 검색 결과를 추론 과정에 통합하는지 보여줍니다.  특히,  <|begin_search_query|> 와 <|end_search_query|> 태그는 모델이 검색을 수행한 부분을, <|begin_search_result|> 와 <|end_search_result|> 태그는 검색 결과를 나타냅니다. 이 예시는 Search-o1 모델의 작동 방식과 외부 지식을 활용하여 복잡한 추론 문제를 해결하는 능력을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 4: An example from Search-o1 on GPQA dataset, with special symbols used in the search queries and search results highlighted in  green box and  blue box, respectively.
> </details>

{{< table-caption >}}
| Example #1 from GPQA Dataset |
|---|---|---|---|---|
| **Question:** | trans-cinnamaldehyde was treated with methylmagnesium bromide, forming product 1. 1 was treated with pyridinium chlorochromate, forming product 2. 3 was treated with (dimethyl(oxo)-l6-sulfaneylidene)methane in DMSO at elevated temperature, forming product 3. how many carbon atoms are there in product 3? Choices: | (A) 10 | (B) 11 | (C) 14 | (D) 12 |
| **Labeled Answer:** | B |
| **Model Output by Search-o1** | Alright, so I have this problem here about some chemical reactions, and I need to figure out how many carbon atoms are in the final product, which is product 3. Let’s break this down step by step. First, there’s trans-cinnamaldehyde, and it’s being treated with methylmagnesium bromide to form product 1. I know that methylmagnesium bromide is a Grignard reagent, which is nucleophilic and usually adds to carbonyl compounds. So, trans-cinnamaldehyde has a carbonyl group, right? It’s an aldehyde, so it has a C=O bond. The Grignard reagent should attack the carbonyl carbon, adding the methyl group and turning the aldehyde into an alcohol, I think. But let me make sure. Wait, maybe I should look up what exactly happens when a Grignard reagent reacts with an aldehyde. Let me try to search for that. | https://arxiv.org/html/2501.05366/begin_search_query.png | https://arxiv.org/html/2501.05366/end_search_query.png |
|  | Reacting a Grignard reagent with an aldehyde results in the formation of a secondary alcohol, incorporating one additional carbon atom from the Grignard reagent. Therefore, if trans-cinnamaldehyde (9 carbon atoms) reacts with methylmagnesium bromide (1 carbon atom), the resulting product (product 1) will have 10 carbon atoms. Subsequent protonation to form product 2 and further reactions to form product 3 do not change the carbon atom count, assuming no carbon is added or removed in those steps. Hence, product 3 should have 10 carbon atoms. | https://arxiv.org/html/2501.05366/begin_search_result.png | https://arxiv.org/html/2501.05366/end_search_result.png |
|  | Hmm, according to this, product 1 should have 10 carbon atoms, starting from trans-cinnamaldehyde, which has 9 carbon atoms, plus the methyl group from the Grignard reagent, adding one more carbon atom. That makes sense. Next, product 1 is treated with pyridinium chlorochromate to form product 2. Pyridinium chlorochromate (PCC) is used for oxidations, particularly for oxidizing primary alcohols to aldehydes or secondary alcohols to ketones. Since product 1 is a secondary alcohol (from the previous step), PCC should oxidize it to a ketone. Again, this shouldn’t change the number of carbon atoms; it’s just changing the functional group. … Alternatively, perhaps the initial trans-cinnamaldehyde has more or fewer carbon atoms than I thought. Let me confirm its structure. |  |  |
|  | https://arxiv.org/html/2501.05366/begin_search_query.png | https://arxiv.org/html/2501.05366/end_search_query.png |
|  | Trans-cinnamaldehyde, also known as (E)-cinnamaldehyde, has the molecular formula C9H8O. It consists of a phenyl ring connected to a propenal group via a double bond, forming a conjugated system that makes the molecule planar. The structure comprises 9 carbon atoms, 8 hydrogen atoms, and 1 oxygen atom, with the functional groups indicating its reactivity in chemical transformations. | https://arxiv.org/html/2501.05366/begin_search_result.png | https://arxiv.org/html/2501.05366/end_search_result.png |
|  | Yes, confirmed: trans-cinnamaldehyde has 9 carbon atoms. Now, reacting with methylmagnesium bromide, which provides a methyl group (-CH3), adds one carbon atom, making product 1 have 10 carbon atoms. Then, oxidation with PCC to convert the alcohol to a ketone doesn’t change the carbon skeleton, so product 2 still has 10 carbon atoms. … Therefore, starting from 9 carbon atoms in trans-cinnamaldehyde, adding one carbon atom from the Grignard reagent to make 10, and then adding another carbon atom in the cyclopropanation to make 11. |  |  |
|  | So, the final answer is B |  |  |  |  |{{< /table-caption >}}
> 🔼 표 5는 Search-01 모델이 AMC2023 데이터셋의 문제를 푸는 과정을 보여줍니다.  표에는 Search-01이 검색어를 생성하고(녹색 박스), 검색 결과를 분석하여(파란색 박스) 문제 해결에 필요한 정보를 추출하는 과정이 단계별로 자세히 나와 있습니다.  이를 통해 Search-01의 검색 기반 추론 메커니즘을 명확히 이해할 수 있습니다. 특히, 검색어 생성 및 결과 분석 과정에서 사용되는 특수 기호(<|begin_search_query|> 와 <|end_search_query|> 등)가 어떻게 활용되는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 5: An example from Search-o1 on AMC2023 dataset, with special symbols used in the search queries and search results highlighted in  green box and  blue box, respectively.
> </details>

{{< table-caption >}}
## Example #2 from AMC2023 Dataset

| Question: |  |
|---|---| 
| There is a unique sequence of integers $a_{1},a_{2},\cdots a_{2023}$ such that $
\tan 2023x=
\frac{a_{1}
\tan x+a_{3}
\tan^{3}x+a_{5}
\tan^{5}x+
\cdots+a_{2023}
\tan^{2023}x}{1+a_{2}
\tan^{2}x+a_{4}
\tan^{4}x
\cdots+a_{2022}
\tan^{2022}x}$ whenever $
\tan 2023x$ is defined. What is $a_{2023}$? |  |
| Labeled Answer: | -1 |
| Model Output by Search-o1 |  |
| … |  |
| And I need to find the value of $a_{2023}$. |  |
| First off, I know that there are multiple-angle identities for tangent, but I’m not sure if there’s a direct formula for such a high multiple like 2023. Maybe there’s a general formula for $\tan nx$ in terms of $\tan x$, and perhaps this problem is asking for the coefficients in that expansion. |  |
| … |  |
| Wait, I remember that tangent of multiple angles can be expressed using the Bernoulli polynomials or something similar, but I’m not sure. Maybe I need to search for a general formula for $\tan nx$. |  |
| Let me try to search for ẗangent multiple angle formulaẗo see if there’s a general expression. |  |
| <svg class="ltx_picture" height="20.48" id="A2.T5.12.8.1.1.1.pic1" overflow="visible" version="1.1" width="160.54"><g transform="translate(0,20.48) matrix(1 0 0 -1 0 0) translate(80.27,0) translate(0,6.78)"><g fill="#000000" stroke="#056B34" stroke-width="0.8pt"><path d="M -79.72 -6.23 h 159.43 v 19.37 h -159.43 Z" style="fill:none"></path></g><g fill="#000000" stroke="#000000" stroke-width="0.8pt" transform="matrix(1.0 0.0 0.0 1.0 -76.95 0)"><foreignobject height="13.84" overflow="visible" transform="matrix(1 0 0 -1 0 16.6)" width="153.9"><span class="ltx_text ltx_font_bold" id="A2.T5.12.8.1.1.1.pic1.1.1.1.1.1" style="color:#056B34;">&lt;|begin_search_query|&gt;</span></foreignobject></g></g></svg>tangent multiple angle formula <svg class="ltx_picture" height="20.48" id="A2.T5.13.9.2.2.2.pic2" overflow="visible" version="1.1" width="149.39"><g transform="translate(0,20.48) matrix(1 0 0 -1 0 0) translate(74.7,0) translate(0,6.78)"><g fill="#000000" stroke="#056B34" stroke-width="0.8pt"><path d="M -74.14 -6.23 h 148.29 v 19.37 h -148.29 Z" style="fill:none"></path></g><g fill="#000000" stroke="#000000" stroke-width="0.8pt" transform="matrix(1.0 0.0 0.0 1.0 -71.38 0)"><foreignobject height="13.84" overflow="visible" transform="matrix(1 0 0 -1 0 16.6)" width="142.75"><span class="ltx_text ltx_font_bold" id="A2.T5.13.9.2.2.2.pic2.1.1.1.1.1" style="color:#056B34;">&lt;|end_search_query|&gt;</span></foreignobject></g></g></svg> |  |
| <svg class="ltx_picture" height="20.48" id="A2.T5.14.10.1.1.1.pic1" overflow="visible" version="1.1" width="160.62"><g transform="translate(0,20.48) matrix(1 0 0 -1 0 0) translate(80.31,0) translate(0,6.78)"><g fill="#000000" stroke="#054488" stroke-width="0.8pt"><path d="M -79.76 -6.23 h 159.51 v 19.37 h -159.51 Z" style="fill:none"></path></g><g fill="#000000" stroke="#000000" stroke-width="0.8pt" transform="matrix(1.0 0.0 0.0 1.0 -76.99 0)"><foreignobject height="13.84" overflow="visible" transform="matrix(1 0 0 -1 0 16.6)" width="153.98"><span class="ltx_text ltx_font_bold" id="A2.T5.14.10.1.1.1.pic1.1.1.1.1.1" style="color:#054488;">&lt;|begin_search_result|&gt;</span></foreignobject></g></g></svg>The recursive formula for tan(nθ) is given by: $\tan(n\theta)=
\frac{\tan[(n-1)\theta]+\tan\theta}{1-\tan[(n-1)\theta]\tan\theta}$ This formula can be used iteratively to compute tan(nθ) for any integer n, making it particularly useful for large values of n, such as n=2023, as encountered in the problem. This approach avoids the complexity of deriving high-degree polynomial expressions directly and leverages the tangent addition formula in a step-by-step manner. <svg class="ltx_picture" height="20.48" id="A2.T5.15.11.2.2.2.pic2" overflow="visible" version="1.1" width="149.47"><g transform="translate(0,20.48) matrix(1 0 0 -1 0 0) translate(74.74,0) translate(0,6.78)"><g fill="#000000" stroke="#054488" stroke-width="0.8pt"><path d="M -74.18 -6.23 h 148.36 v 19.37 h -148.36 Z" style="fill:none"></path></g><g fill="#000000" stroke="#000000" stroke-width="0.8pt" transform="matrix(1.0 0.0 0.0 1.0 -71.41 0)"><foreignobject height="13.84" overflow="visible" transform="matrix(1 0 0 -1 0 16.6)" width="143.21"><span class="ltx_text ltx_font_bold" id="A2.T5.15.11.2.2.2.pic2.1.1.1.1.1" style="color:#054488;">&lt;|end_search_result|&gt;</span></foreignobject></g></g></svg> |  |
| Okay, so there’s a recursive formula for $\tan(n\theta)$: $\tan(n\theta)=
\frac{\tan[(n-1)\theta]+\tan\theta}{1-\tan[(n-1)\theta]\tan\theta}$ That seems useful, especially for large $n$, like 2023. But I’m not sure how to apply this recursively up to 2023 without going through each step, which isn’t practical. |  |
| Maybe there’s a general expression for $\tan(nx)$ in terms of $\tan(x)$ as a rational function. |  |
| … |  |
| Looking at $n=1$: $\tan x=
\frac{a_{1}\tan x}{1}
\implies a_{1}=1$ For $n=3$, $a_{3}=-1$ |  |
| For $n=5$, $a_{5}=1$ |  |
| So it seems that $a_{n}=(-1)^{(n-1)/2}$ for odd $n$. |  |
| Wait, let’s check: |  |
| For $n=1$, $(-1)^{(1-1)/2}=(-1)^{0}=1$, which matches $a_{1}=1$ |  |
| For $n=3$, $(-1)^{(3-1)/2}=(-1)^{1}=-1$, which matches $a_{3}=-1$ |  |
| For $n=5$, $(-1)^{(5-1)/2}=(-1)^{2}=1$, which matches $a_{5}=1$ |  |
| So, generalizing, for odd $n$, $a_{n}=(-1)^{(n-1)/2}$ |  |
| Now, 2023 is odd, so $a_{2023}=(-1)^{(2023-1)/2}=(-1)^{1011}=-1$ |  |
| Therefore, $a_{2023}=-1$ |  |
| I think that’s the answer. |  |
| **Final Answer:** $
\boxed{-1}$ |  |{{< /table-caption >}}
> 🔼 표 6은 Search-o1 모델이 HotpotQA 데이터셋에서 질문에 답변하는 과정을 보여주는 예시입니다. 표에는 검색어와 검색 결과가 각각 녹색과 파란색 상자로 강조 표시되어 있습니다. Search-o1 모델은 질문에 대한 답을 찾기 위해 여러 번의 검색을 수행하고, 검색 결과를 분석하여 답변을 도출하는 과정을 보여줍니다. 이를 통해 Search-o1 모델이 어떻게 외부 지식을 활용하여 질문에 대한 답변을 생성하는지 자세히 보여줍니다.  특히, 검색어와 검색 결과에 대한 특수 심볼(<|begin_search_query|>와 <|end_search_query|>, <|begin_search_result|>와 <|end_search_result|>)을 사용하여 모델의 추론 과정을 명확하게 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 6: An example from Search-o1 on HotpotQA dataset, with special symbols used in the search queries and search results highlighted in  green box and  blue box, respectively.
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