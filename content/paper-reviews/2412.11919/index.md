---
title: "RetroLLM: Empowering Large Language Models to Retrieve Fine-grained Evidence within Generation"
summary: "RetroLLM: 검색과 생성을 통합한 RAG 시스템"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Question Answering", "🏢 Renmin University of China",]
showSummary: true
date: 2024-12-16
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.11919 {{< /keyword >}}
{{< keyword icon="writer" >}} Xiaoxi Li et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-17 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.11919" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.11919" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/retrollm-empowering-large-language-models-to" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)은 인상적인 텍스트 생성 기능을 보여주지만, 사실적 오류 또는 '환각'에 취약합니다. 검색 증강 생성(RAG)은 외부 지식 소스를 통합하여 이러한 한계를 해결하지만, 별도의 검색기 배포 비용, 검색된 텍스트 청크의 중복 입력 토큰 및 검색과 생성 간 공동 최적화 부족과 같은 문제가 있습니다. 

기존 RAG의 문제점을 해결하기 위해, RetroLLM은 검색과 생성을 단일 프로세스로 통합하는 통합 프레임워크를 도입했습니다. 이를 통해 LLM은 제약된 디코딩을 사용하여 코퍼스에서 직접 미세 조정된 증거를 생성하여 별도의 검색 모델에 대한 필요성을 없앨 수 있습니다. 제약된 증거 생성에서 잘못된 가지치기 문제를 완화하기 위해, RetroLLM은 후보 문서의 하위 집합을 식별하기 위해 계층적 FM-Index 제약을 사용하고, 전방탐색 제약 디코딩 전략을 사용하여 미래 시퀀스의 관련성을 고려하여 증거 정확성을 향상시킵니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} RetroLLM은 단일 프로세스에서 검색과 생성을 통합하여 기존 RAG 시스템의 한계를 해결합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 계층적 FM-Index와 전방탐색 제약 디코딩은 잘못된 가지치기 문제를 완화하여 증거 정확성을 향상시킵니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} RetroLLM은 여러 QA 데이터 세트에서 우수한 성능과 토큰 소비 감소를 보여줍니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**RetroLLM은 검색 증강 생성(RAG) 시스템에 상당한 개선을 제공합니다.** 기존 RAG 방식이 별도의 검색기와 과도한 입력 토큰으로 어려움을 겪었던 반면, RetroLLM은 검색과 생성 프로세스를 통합하여 효율성과 정확성을 향상시킵니다. 이러한 통합된 접근 방식은 공동 학습을 가능하게 하고, 미세 조정된 증거 검색을 허용하며, 입력 토큰 소비를 줄여 RAG 연구에 새로운 길을 열어줍니다. RetroLLM은 환각을 줄이는 동시에 사실에 기반한 출력을 생성할 수 있는 LLM의 잠재력을 보여줍니다. 또한, 계층적 FM-Index 및 전방탐색 제약 디코딩과 같은 혁신적인 기술은 추가 탐구를 위한 유망한 길을 제시하며, RAG 개발을 위한 새로운 방향을 제시합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.11919/x1.png)

> 🔼 이 그림은 다양한 검색 증강 생성(RAG) 프레임워크를 비교합니다. (a) 기존 RAG는 문서 일치에 밀집 검색기를 사용하고, (b) 생성 RAG는 제약된 DocID 생성에 의존합니다. 두 가지 모두 검색된 문서 텍스트를 LLM에 입력하여 답변을 생성해야 합니다. (c) RetroLLM은 검색 및 생성을 단일 자동 회귀 디코딩 프로세스로 통합하여 FM-인덱스 제약 조건을 활용하여 세분화된 증거를 검색합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  Comparison of retrieval-augmented generation frameworks. (a) Traditional RAG uses a dense retriever for document matching, while (b) generative RAG relies on constrained DocID generation. Both require feeding retrieved document text into the LLM for answer generation. (c) Our RetroLLM unifies retrieval and generation in a single auto-regressive decoding process, leveraging FM-Index constraints to retrieve fine-grained evidence.
> </details>





{{< table-caption >}}
| Method | In-domain Datasets | | | | | | Out-of-domain Datasets | | | |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---| 
|  | NQ | | | TriviaQA | | | HotpotQA | | | PopQA | | | 2WIKI | | |
|  | Acc | F1 | Tok | Acc | F1 | Tok | Acc | F1 | Tok | Acc | F1 | Tok | Acc | F1 | Tok |
| **_Direct Generation_** | | | | | | | | | | | | | | | |
| Llama2-7B | 27.6 | 30.1 | 50 | 56.1 | 60.2 | 52 | 21.2 | 26.5 | 56 | 24.2 | 26.4 | 43 | 20.9 | 24.3 | 54 |
| Mistral-7B | 30.4 | 25.2 | 57 | 58.8 | 58.6 | 57 | 27.0 | 23.6 | 65 | 25.8 | 25.2 | 45 | 36.5 | 18.7 | 58 |
| Qwen-7B | 21.8 | 21.3 | 52 | 45.1 | 48.1 | 54 | 21.3 | 27.5 | 57 | 17.1 | 18.7 | 45 | 22.4 | 28.1 | 53 |
| ChatGPT | - | - | - | <span style="color:#808080;">77.0</span> | <span style="color:#808080;">52.9</span> | - | <span style="color:#808080;">33.8</span> | <span style="color:#808080;">24.0</span> | - | <span style="color:#808080;">26.6</span> | <span style="color:#808080;">13.2</span> | - | <span style="color:#808080;">38.0</span> | <span style="color:#808080;">21.3</span> | - |
| **_Retrieval-augmented Generation_** | | | | | | | | | | | | | | | |
| Naive RAG | **52.4** | 41.1 | 919 | 69.3 | 65.9 | **915** | **37.8** | 35.8 | **960** | 47.7 | 38.6 | 944 | **38.7** | 21.7 | **1000** |
| REPLUG | 41.6 | 41.2 | **903** | 65.4 | 66.5 | 939 | 27.8 | 31.7 | 965 | 38.2 | 37.0 | **921** | 24.5 | 20.8 | 1007 |
| Self-RAG | 41.8 | 45.2 | 1203 | 64.1 | 53.4 | 1267 | 32.1 | 29.6 | 1354 | 39.7 | 32.7 | 1236 | 30.3 | 25.7 | 1272 |
| IRCoT | 49.6 | 45.9 | 1598 | 66.0 | 66.1 | 1715 | 37.3 | **41.5** | 1842 | **59.8** | **45.6** | 1667 | 29.4 | **32.4** | 1707 |
| Iter-RetGen | 51.7 | **48.4** | 3002 | **71.0** | **69.9** | 2461 | 37.2 | 39.0 | 2545 | 51.7 | **47.5** | 2509 | 29.2 | 21.5 | 2669 |
| Adaptive-RAG | 50.5 | 46.6 | 946 | 65.1 | 65.6 | 958 | 37.1 | 39.1 | 2080 | 58.3 | 40.4 | 1681 | 32.1 | 28.4 | 2580 |
| **_Retrieval within Generation_** | | | | | | | | | | | | | | | |
| RetroLLM (Ours) | **61.6** | **49.8** | **302** | **74.3** | **72.8** | **287** | **61.9** | **47.2** | **607** | **65.7** | 43.0 | **355** | **48.9** | **36.2** | **661** |{{< /table-caption >}}

> 🔼 이 표는 단일 홉 및 다중 홉 QA 작업을 포함한 오픈 도메인 QA 데이터 세트에 대한 전반적인 성능을 보여줍니다. 최상의 결과는 굵게 표시되고 두 번째로 좋은 결과는 밑줄이 그어져 있습니다. 독점이 아닌 모델의 결과는 회색으로 표시됩니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Overall performance on open-domain QA datasets, including single-hop and multi-hop QA tasks. The best results are in bold and the second are underlined. Results from non-proprietary models are in gray color.
> </details>





### In-depth insights


#### LLM Hallucination
**LLM 환각**은 LLM이 **사실과 다른 출력**을 생성하는 현상을 말합니다. 이는 LLM의 **학습 데이터 편향**, **맥락 이해 부족**, **추론 능력 한계** 등 여러 요인이 복합적으로 작용하여 발생합니다. 환각은 LLM의 신뢰도를 떨어뜨리고, 잘못된 정보 확산으로 이어질 수 있어 심각한 문제입니다. 따라서 **환각 완화**는 LLM 연구의 핵심 과제입니다. 최근 연구들은 **외부 지식 활용**, **출력 검증 메커니즘 도입**, **학습 데이터 개선** 등 다양한 방식으로 환각 문제 해결을 시도하고 있습니다. 하지만 아직 완벽한 해결책은 없으며, **지속적인 연구 개발**이 필요합니다. LLM 환각은 단순한 기술적 문제를 넘어, **정보 생태계**와 **사회 전반**에 큰 영향을 미칠 수 있는 중요한 문제입니다.

#### RetroLLM Framework
**RetroLLM 프레임워크는 검색과 생성을 단일 프로세스로 통합**하여 대규모 언어 모델(LLM)이 FM-Index 제약 조건을 사용하여 코퍼스에서 직접 증거를 생성할 수 있도록 합니다. 이러한 **통합된 접근 방식은 별도의 검색기의 필요성을 없애고** 입력 토큰의 중복성을 줄여 효율성을 향상시킵니다. 또한 검색 및 생성 작업의 **공동 최적화를 가능하게 하여 전반적인 성능 향상**에 기여합니다. RetroLLM은 **계층적 FM-Index 제약 조건과 미래 지향적 제약 조건 디코딩 전략을 활용**하여 증거 정확도를 더욱 향상시킵니다. 계층적 제약 조건은 관련 문서의 하위 집합을 식별하여 관련 없는 디코딩 공간을 줄이고 미래 지향적 디코딩은 미래 시퀀스의 관련성을 고려하여 증거 생성을 안내합니다. 이러한 혁신적인 기능을 통해 RetroLLM은 **기존 RAG(검색 증강 생성) 방법과 복잡한 RAG 전략보다 뛰어난 성능**을 달성하여 생성 검색의 새로운 시대를 열었습니다.

#### Joint Optimization
**RetroLLM의 핵심은 검색과 생성을 하나의 프로세스로 통합**하여, 기존 RAG의 분리된 리트리버 운영 및 입력 토큰 증가 문제를 해결하고 **joint optimization을 가능하게** 하는 것입니다. 이러한 통합으로 인해 검색과 생성 간의 관계를 더 깊이 이해하고 전반적인 성능 향상을 도모합니다. 하지만 단순히 FM-Index를 적용하는 방식은 'false pruning' 문제를 야기할 수 있습니다. RetroLLM은 이를 완화하기 위해 hierarchical FM-Index constraints와 forward-looking constrained decoding 전략을 사용합니다. **Hierarchical FM-Index는 단계적 검색 공간을 줄여줌**으로써 효율적인 검색을 가능케 하고, **Forward-looking constrained decoding은 미래 시퀀스의 관련성을 고려하여 정확도 향상**에 기여합니다. 즉, RetroLLM은 joint optimization을 통해 검색과 생성을 효과적으로 결합하여 성능 및 효율성을 향상시킵니다.

#### Constrained Decoding
**제약된 디코딩**은 외부 지식을 활용하여 언어 모델의 생성 품질을 향상하는 데 중점을 둡니다. 이 기술은 사실성, 관련성 및 일관성을 보장하기 위해 미리 정의된 제약 조건 내에서 텍스트를 생성합니다. **주요 이점**으로는 환각 감소, 텍스트의 집중도 향상, 특정 기준 충족 등이 있습니다. 그러나 잘못된 가지치기, 즉 유효한 시퀀스가 너무 일찍 제거되는 문제가 발생할 수 있습니다. 이는 **초기 접두사 선택의 과도한 다양성**과 **미래 시퀀스 관련성에 대한 인식 부족**으로 인해 발생합니다. 이러한 문제를 해결하기 위해 **접두사 선택 감소 및 미래 관련성 인식 향상**과 같은 전략을 사용할 수 있습니다. 예를 들어 단서 생성을 사용하여 관련 문서의 하위 집합을 식별하여 접두사 선택을 줄이고 후속 디코딩을 안내할 수 있습니다. 또한 미래 창을 식별하고 점수를 매겨 모델이 더 관련성 높은 증거를 생성하고 잘못된 가지치기 문제를 완화하도록 할 수 있습니다.

#### Evidence Accuracy
**증거 정확도**는 RAG에서 중요합니다. RetroLLM은 **계층적 FM-Index** 및 **미래 예측 디코딩**을 사용하여 이를 향상시킵니다. **계층적 색인**은 관련 문서의 하위 집합을 먼저 식별하여 잘못된 가지치기 문제를 줄입니다. 그런 다음 **미래 예측 디코딩**은 관련성 점수가 높은 미래 윈도우를 기반으로 증거 생성을 안내합니다. 이러한 전략은 정확한 증거 검색을 보장합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.11919/x2.png)

> 🔼 이 그래프는 생성된 증거 시퀀스의 앞부분 n개 토큰과 쿼리 간의 관련성 점수를 보여줍니다. Corpus FM-Index 제약 조건을 사용하는 경우 처음 13개 토큰 내에서 관련성 점수가 급격히 감소하는 것을 관찰할 수 있는 반면, 관련 문서의 Doc FM-Index 제약 조건을 사용하는 경우 관련성 점수가 감소하지 않고 beam 크기에 따라 정확도가 향상됩니다.
> <details>
> <summary>read the caption</summary>
> (a) Sequence Relevance
> </details>



![](https://arxiv.org/html/2412.11919/x3.png)

> 🔼 이 그래프는 다양한 빔 크기에서 말뭉치 수준 FM-Index와 문서 수준 FM-Index를 사용한 제약 증강 생성에서의 전반적인 정확도를 비교합니다. 말뭉치 수준 제약은 특히 처음 몇 토큰 내에서 정확도가 크게 저하되는 반면, 문서 수준 제약은 이러한 저하를 완화하고 다양한 빔 크기에서 더 나은 정확도를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) Overall Accuracy
> </details>



![](https://arxiv.org/html/2412.11919/x4.png)

> 🔼 이 그림은 제한된 증거 생성에서 잘못된 가지치기 문제에 대한 실증적 연구 결과를 보여줍니다. 말뭉치 수준 FM-Index와 문서 수준 FM-Index 접근 방식을 비교하여 생성된 증거 시퀀스의 관련성 점수(bge-reranker-large 기준)가 자동 회귀 디코딩 프로세스 중에 어떻게 변하는지 보여줍니다. 레이블이 지정된 증거 시퀀스와 비교하여 말뭉치 FM-Index 제약 조건에서 접두사 관련성이 크게 감소하는 것을 알 수 있습니다. 특히 처음 13개 토큰 내에서 심각하게 감소합니다. FM-Index 제약 조건을 관련 문서로만 제한하면 이러한 저하가 크게 줄어들고 다양한 빔 크기에 걸쳐 증거 생성 정확도가 향상됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Empirical Study on false pruning problem in constrained evidence generation, comparing corpus-level and document-level FM-Index approaches.
> </details>



![](https://arxiv.org/html/2412.11919/x5.png)

> 🔼 RetroLLM은 계층적이고 미래 지향적인 FM-Index 제약 생성 프로세스를 통해 세분화된 증거를 검색하는 프레임워크입니다. 생성 중에 모델은 현재 컨텍스트의 충분성을 기반으로 추가 증거를 생성할지 아니면 최종 답변을 제공할지 자율적으로 결정합니다. 그림에서 (a)는 RetroLLM의 전체 프로세스 개요, (b)는 계층적 FM-Index 제약 조건 구성, (c)는 미래 지향적 제약 증거 생성 방식을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3:  Overview of the RetroLLM Framework, which retrieves fine-grained evidence through a hierarchical, forward-looking FM-Index constrained generation process. During generation, the model autonomously determines whether to generate additional evidence or provide the final answer, based on the sufficiency of the current context.
> </details>



![](https://arxiv.org/html/2412.11919/x6.png)

> 🔼 이 그래프는 다양한 매개변수 크기를 가진 여러 기본 LLM에서 RetroLLM의 성능을 보여줍니다. x축은 LLM의 매개변수 크기(1B에서 14B까지)를 나타내고 y축은 NQ, TriviaQA, HotpotQA, PopQA 및 2WIKI의 5개 데이터 세트에 대한 평균 정확도를 나타냅니다. 이 그림은 Llama3, Qwen2.5 및 Mistral의 세 가지 LLM 시리즈를 비교합니다. 매개변수 크기가 증가함에 따라 RetroLLM의 성능이 꾸준히 향상되어 스케일링 법칙과 일치하는 것을 알 수 있습니다. 또한 서로 다른 모델(Mistral, Llama3, Qwen2.5) 간에 약간의 성능 차이가 있으며, Mistral은 일반적으로 Llama3보다 성능이 우수하고, Llama3은 Qwen2.5보다 성능이 우수합니다. 그럼에도 불구하고 모든 모델에서 RetroLLM의 효과가 확인되었으며, Qwen2.5-1.5B와 같은 소규모 모델조차도 상당한 성능(예: NQ에서 50.1% 정확도, TriviaQA에서 57.2% 정확도)을 달성했습니다. 이는 RetroLLM이 다양한 기본 모델 및 매개변수 크기에서 강력함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (a) Parameters vs. Accuracy
> </details>



![](https://arxiv.org/html/2412.11919/x7.png)

> 🔼 이 그래프는 다양한 매개변수 크기의 기본 LLM을 사용하는 RetroLLM의 성능을 보여줍니다. 매개변수 크기가 증가함에 따라 RetroLLM의 성능이 꾸준히 향상되어 스케일링 법칙을 따릅니다. 또한 다양한 모델(Mistral, Llama3, Qwen2.5)에서 약간의 성능 차이가 있습니다. Mistral은 일반적으로 Llama3보다 성능이 우수하고 Llama3은 Qwen2.5보다 성능이 우수합니다. 그럼에도 불구하고 모든 모델은 RetroLLM의 효과를 확인합니다. 작은 모델(예: Qwen2.5-1.5B)도 상당한 성능(예: NQ에서 정확도 50.1%, TriviaQA에서 57.2%)을 달성하여 RetroLLM이 다양한 기본 모델과 매개변수 크기에 대해 강력함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) Parameters vs. F1
> </details>



![](https://arxiv.org/html/2412.11919/x8.png)

> 🔼 이 그림은 다양한 기본 LLM(Llama3, Qwen2.5, Mistral 시리즈)과 매개변수 크기(1B에서 14B까지)를 사용하여 RetroLLM의 성능을 비교합니다. 매개변수 크기가 증가함에 따라 RetroLLM의 성능이 향상되는 것을 보여주고, 다양한 모델 간의 약간의 성능 차이도 보여줍니다. 하지만 모든 모델에서 RetroLLM의 효과를 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Impact of performance with different base LLMs, reporting average performance on five datasets.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | Single-hop QA | | | Multi-hop QA | | |
|---|---|---|---|---|---|---| 
| | R@1 | R@5 | Num | R@1 | R@5 | Num |
|---|---|---|---|---|---|---| 
| BM25 | 37.8 | 56.3 | 5 | 26.9 | 43.1 | 5 |
| SPLADE-v3 | 50.6 | 69.7 | 5 | 27.5 | 42.9 | 5 |
| E5 | 54.3 | **74.3** | 5 | 26.9 | 45.9 | 5 |
| BGE | 53.3 | 72.8 | 5 | 27.4 | 46.8 | 5 |
| Naive Constrain | 15.7 | 31.7 | 5 | 10.6 | 20.3 | 5 |
| RetroLLM | **56.6** | 67.9 | **3.29** | **29.3** | **49.6** | **4.24** |{{< /table-caption >}}
> 🔼 이 표는 RetroLLM의 검색 성능을 희소, 밀집, 생성 검색 방법과 비교하여 분석한 내용입니다. 세 가지 단일 홉 및 두 가지 다중 홉 QA 데이터 세트에 대한 평균 성능을 보여줍니다. RetroLLM은 단일 홉 QA 작업에서 R@1 정확도가 우수하고 다중 홉 QA 작업에서도 다른 모든 방법보다 R@1과 R@5 모두에서 더 나은 정확도를 보입니다. 또한 RetroLLM은 검색된 구절의 평균 개수가 기준선보다 적어 검색 효율성이 더 높습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Analysis of retrieval performance of RetroLLM, compared with sparse, dense, and generative retrieval methods. We report average performance on three single-hop and two multi-hop QA datasets.
> </details>

{{< table-caption >}}
| Method | In-domain | | Out-of-domain | |
|---|---|---|---|---| 
| | Acc | F1 | Acc | F1 |
| RetroLLM | **66.0** | **56.6** | **57.3** | **39.6** |
| w/o Future Window | 44.3 | 43.2 | 40.9 | 33.8 |
| w/o Clue Generation | 60.6 | 52.1 | 56.4 | 38.1 |
| w/o Clue Expansion | 49.6 | 45.1 | 44.1 | 35.4 |
| w/ Naive Constraints | 27.2 | 28.0 | 21.8 | 20.7 |
| w/o Constraints | 41.6 | 43.0 | 31.6 | 28.1 |{{< /table-caption >}}
> 🔼 RetroLLM 성능에 대한 ablation study 결과를 보여주는 표입니다. 표에는 in-domain 데이터셋과 out-of-domain 데이터셋에 대한 성능 지표가 포함되어 있습니다. 또한 future window, clue 생성, clue 확장과 같은 RetroLLM의 각 구성 요소가 미치는 영향을 평가하여 이러한 구성 요소의 중요성을 보여줍니다. 마지막으로 순수하게 제약 조건 기반의 생성 검색만 사용했을 때의 성능 저하를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Ablation Studies of RetroLLM, considering in-domain and out-of-domain performance.
> </details>

{{< table-caption >}}
| Method | Latency (ms) |  |  | Token Num |  |  | # P |
|---|---|---|---|---|---|---|---| 
|  | Retr | Gen | Total | In | Out | Total | F1 |
| Naive RAG | **54** | **528** | **582** | 902 | **17** | 919 | 41.1 |
| SelfRAG | 89 | 3180 | 3269 | 1096 | 107 | 1203 | 45.2 |
| Iter-RetGen | 274 | 2058 | 2332 | 2963 | 39 | 3002 | 48.4 |
| IRCoT | 83 | 1759 | 1842 | 1535 | 63 | 1598 | 46.6 |
| RetroLLM | - | - | 786 | **18** | 297 | **315** | **49.8** |{{< /table-caption >}}
> 🔼 이 표는 RetroLLM의 효율성 분석 결과를 보여줍니다. 쿼리 지연 시간, 토큰 수 및 성능을 다른 RAG 메서드들과 비교하여 RetroLLM의 효율성을 평가합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Efficiency Analysis of RetroLLM, comparing query latency, number of tokens and performance (# P).
> </details>

{{< table-caption >}}
| Task | Dataset | # Train | # Test |
|---|---|---|---| 
| Single-hop QA | NQ | 79,168 | 3,610 |
| Single-hop QA | TriviaQA | 78,785 | 11,313 |
| Single-hop QA | PopQA | / | 14,267 |
| Multi-hop QA | HotpotQA | 90,447 | 7,405 |
| Multi-hop QA | 2WIKI | / | 12,576 |
| **Retrieval Corpus** | **# Passages** | **# Documents** | |
| Wikipedia | 21,015,324 | 3,232,907 | |{{< /table-caption >}}
> 🔼 이 표는 논문에서 사용된 데이터셋과 검색 코퍼스에 대한 자세한 통계를 제공합니다. 단일 홉 및 다중 홉 추론 능력을 평가하기 위해 다양한 질문 답변(QA) 데이터셋이 사용되었습니다. 단일 홉 QA의 경우, Natural Questions(NQ), TriviaQA, PopQA 데이터셋을 사용하고, 다중 홉 QA의 경우, HotpotQA 및 2WikiMultiHopQA(2WIKI) 데이터셋을 사용합니다. 검색 코퍼스로는 21,015,324개의 구절과 3,232,907개의 문서로 구성된 Wikipedia 데이터셋을 사용합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Detailed statistics of datasets and retrieval corpus utilized in our experiments.
> </details>

{{< table-caption >}}
| Method | NQ  |     |   | TriviaQA |     |   | HotpotQA |     |   | PopQA |     |   | 2WIKI |     |   |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---| 
|  **In-domain Datasets** | **R@1** | **R@5** | **Num** | **R@1** | **R@5** | **Num** | **R@1** | **R@5** | **Num** | **R@1** | **R@5** | **Num** | **R@1** | **R@5** | **Num** |
|  **Out-of-domain Datasets** |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| *Sparse Retrieval* |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| BM25 | 24.1 | 46.2 | 5 | 49.6 | 68.5 | 5 | 31.2 | 48.7 | 5 | 39.6 | 54.3 | 5 | 22.6 | 37.5 | 5 |
| SPLADE-v3 | 45.4 | 68.0 | 5 | 58.8 | 75.9 | 5 | 32.9 | 45.3 | 5 | 47.6 | 65.2 | 5 | 22.2 | 40.6 | 5 |
| *Dense Retrieval* |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| E5 | **55.7** | **77.3** | 5 | **61.6** | **77.8** | 5 | 32.3 | 52.0 | 5 | 51.7 | **70.9** | 5 | 21.6 | 39.8 | 5 |
| BGE | 50.3 | 73.6 | 5 | 58.7 | 75.1 | 5 | 33.7 | 54.7 | 5 | 50.8 | 69.6 | 5 | 21.1 | 38.9 | 5 |
| *Generative Retrieval* |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| Naive Constrain | 13.1 | 26.9 | 5 | 23.0 | 46.9 | 5 | 11.8 | 21.6 | 5 | 10.9 | 21.2 | 5 | 9.4 | 19.0 | 5 |
| RetroLLM | 51.6 | 62.5 | **3.20** | 61.1 | 71.0 | **2.80** | **35.6** | **57.3** | **3.86** | **57.0** | 70.1 | **4.07** | **23.0** | **41.8** | **4.40** |{{< /table-caption >}}
> 🔼 이 표는 희소, 밀집 및 생성 검색 방식을 비교하여 5개의 개방형 도메인 QA 데이터 세트에 대한 자세한 검색 성능을 보여줍니다. 단일 홉 및 다중 홉 QA 작업 모두에서 RetroLLM이 어떻게 다른 기준선과 비교하여 성능이 우수한지 강조 표시합니다. 또한 순진한 제약 빔 검색 방법이 직면한 잘못된 가지치기 문제를 강조 표시합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Detailed retrieval performance on five open-domain QA datasets, comparing sparse, dense, and generative approaches. The best results are highlighted in Bold.
> </details>

{{< table-caption >}}
| Base Model | In-domain Datasets |       |   | Out-of-domain Datasets |       |   |       |   |       |   |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
|     | NQ |   |   | TriviaQA |   |   | HotpotQA |   |   | PopQA |   |   |
|     | Acc | F1 | Tok | Acc | F1 | Tok | Acc | F1 | Tok | Acc | F1 | Tok |
| **_Llama3 Series_** |     |   |   |     |   |   |     |   |   |     |   |   |
| Llama3.2-1B | 54.4 | 35.8 | 260 | 64.4 | 52.9 | 288 | 58.8 | 33.5 | 573 | 63.3 | 32.9 | 344 |
| Llama3.2-3B | 58.9 | 45.4 | 278 | 67.8 | 62.1 | 267 | 61.3 | 37.8 | 609 | 64.7 | 40.4 | 338 |
| Llama3-8B | 59.2 | 46.4 | 306 | 72.7 | **69.3** | 256 | 62.2 | **47.4** | 575 | 65.2 | 41.4 | 338 |
| **_Qwen2.5 Series_** |     |   |   |     |   |   |     |   |   |     |   |   |
| Qwen2.5-1.5B | 50.1 | 34.3 | **200** | 57.2 | 51.2 | **170** | 57.0 | 32.6 | **539** | 59.5 | 32.6 | **286** |
| Qwen2.5-3B | 52.1 | 36.8 | 236 | 61.4 | 56.3 | 212 | 60.6 | 34.1 | 628 | 64.0 | 34.8 | 336 |
| Qwen2.5-7B | 54.9 | 42.3 | 230 | 64.5 | 62.4 | 196 | 61.9 | 42.0 | 549 | 62.8 | 37.1 | 313 |
| Qwen2.5-14B | 58.6 | **50.6** | 225 | **72.8** | 69.5 | 186 | **62.6** | 45.9 | 568 | 64.3 | 40.8 | 343 |
| **_Mistral Series_** |     |   |   |     |   |   |     |   |   |     |   |   |
| Mistral-7B | **61.6** | 49.8 | 302 | 74.3 | 72.8 | 287 | 61.9 | 47.2 | 607 | **65.7** | **43.0** | 355 |
| 2WIKI |   |   | |     |   |   | |       |       | |     |   |     |
|       | 44.5 | 28.5 | 583 | 47.3 | 32.2 | 632 | 48.7 | 36.1 | 668 | 47.5 | 26.3 | 650 |
|       | 48.1 | 30.6 | 694 | 48.7 | 32.5 | 634 | **51.3** | **36.9** | 687 | 48.9 | 36.2 | 661 |{{< /table-caption >}}
> 🔼 이 표는 다양한 기본 LLM을 사용한 RetroLLM의 성능 비교를 보여줍니다. Llama3 시리즈, Qwen-2.5 시리즈, Mistral 시리즈와 같이 매개변수 크기가 1B에서 14B까지인 다양한 LLM을 사용하여 실험을 진행했습니다. 모든 기본 모델은 instruction-tuned 버전을 사용했습니다. RetroLLM은 다양한 기본 모델과 매개변수 크기에서 강력한 성능을 보여줍니다. 매개변수 크기가 증가함에 따라 RetroLLM의 성능이 꾸준히 향상됩니다. 또한 Mistral, Llama3, Qwen2.5와 같은 다양한 모델 간에 약간의 성능 차이가 있습니다. 하지만 모든 모델에서 RetroLLM의 효과가 확인되었으며, 작은 모델(예: Qwen2.5-1.5B)도 상당한 성능을 달성합니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Detailed performance comparison of RetroLLM using various base models, including the Llama3 series, Qwen-2.5 series, and Mistral series, with parameter sizes ranging from 1B to 14B. All base models we used are the instruction-tuned versions. The best results are highlighted in Bold.
> </details>

{{< table-caption >}}
| # Num | NQ | TriviaQA | HotpotQA | PopQA | 2WIKI |
|---|---|---|---|---|---|---|---|---|---| 
| **In-domain Datasets** | | | | | | |
|  | Acc | F1 | Acc | F1 | Acc | F1 | Acc | F1 | Acc | F1 |
| **Out-of-domain Datasets** | | | | | | |
| **1** | 42.2 | 40.5 | 59.3 | 61.6 | 50.6 | 44.2 | 43.9 | 40.9 | 35.1 | 31.3 |
| **2** | 50.6 | 42.3 | 66.3 | 65.9 | 59.8 | 43.8 | 52.8 | 45.9 | 39.8 | 34.6 |
| **3** | 54.4 | 42.5 | 69.3 | 67.2 | 61.9 | 43.0 | 55.7 | 45.5 | 42.1 | 34.5 |
| **4** | 56.7 | 43.1 | 70.9 | 67.6 | 64.6 | 41.0 | 57.7 | 45.7 | 43.9 | 34.8 |
| **5** | 61.5 | 49.4 | 74.6 | 72.9 | 66.8 | 43.0 | 59.4 | 46.8 | 45.9 | 36.6 |
| **6** | 61.7 | 49.5 | 74.6 | 73.0 | 67.4 | 42.8 | 60.1 | 47.1 | 47.9 | 37.1 |
| **7** | 61.7 | 49.5 | 74.6 | 72.9 | 67.6 | 42.5 | 60.8 | 47.0 | 48.4 | 36.5 |
| **8** | 61.7 | 49.5 | 74.6 | 72.9 | 68.0 | 42.7 | 61.2 | 46.9 | 48.6 | 37.2 |
| **9** | 61.7 | 49.5 | 74.6 | 72.9 | 68.0 | 42.7 | 61.6 | 47.1 | 48.7 | 37.0 |
| **10** | 61.7 | 49.5 | 74.6 | 72.9 | 68.5 | 42.7 | 61.9 | 47.1 | 48.9 | 36.2 |{{< /table-caption >}}
> 🔼 이 표는 생성된 근거의 최대 개수를 1에서 10까지 다양하게 변경하면서 RetroLLM의 성능에 미치는 영향을 보여줍니다. 단일 홉 질의응답의 경우, 검색되는 근거가 최대 5개까지 증가함에 따라 성능이 향상되는 경향이 있지만, 다중 홉 질의응답의 경우 근거가 6개를 넘어가면 성능 향상이 제한적입니다. 이는 다중 홉 질의응답의 경우, 너무 많은 근거는 유용한 정보와 함께 방해가 되는 정보를 가져올 수 있어 추가적인 근거가 오히려 성능 향상에 도움이 되지 않을 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Detailed performance with different number of generated evidence.
> </details>

{{< table-caption >}}
| Dataset | Question | Labeled Answer | Model Input | Model Output | 
|---|---|---|---|---| 
| NQ Dataset | when does the movie the star come out? | ["November 17, 2017"] | Question: when does the movie the star come out?
Your Response: | <|clue|> The Star <|/clue|> <|evidence|> the film, then titled "The Lamb", was given an official release date of December 8, 2017. On June 20, 2016, it was announced that Brian Henson and Lisa Henson from the Jim Henson Company would be executive producers for the film, now titled "The Star", making it the first Henson-produced film for Sony since "The Adventures of Elmo in Grouchland" in 1999. <|sep|> The film’s title was changed from the working title "Dog Years", in a mutual decision between the filmmakers and A24 (who made the suggestion). It was released on February 22, 2018, through DirecTV Cinema before being released in a limited release and through video on demand on March 30, 2018. <|sep|> Chenoweth, Tracy Morgan, Tyler Perry, and Oprah Winfrey. The film was released by Columbia Pictures through its parental label Sony Pictures Entertainment on November 17, 2017 in the United States. The film received mixed reviews and grossed over $62 million worldwide. <|/evidence|> The answer is November 17, 2017. | 
| TriviaQA Dataset | Who was the man behind The Chipmunks? | ["David Seville"] | Question: Who was the man behind The Chipmunks?
Your Response: | <|clue|> The Chipmunks <|/clue|> <|evidence|> 1972), better known by the stage name David Seville, was an American singer-songwriter and actor, best known for creating the novelty musical group The Chipmunks (now better known as "Alvin and the Chipmunks"). Initially a stage and film actor, he rose to prominence in 1958 with the songs "Witch Doctor" and "The Chipmunk Song (Christmas Don’t Be Late)", which both became "Billboard" number-one singles. <|/evidence|> The answer is David Seville. | 
| PopQA Dataset | What is Carsten Carlsen’s occupation? | ["pianist", "composer"] | Question: What is Carsten Carlsen’s occupation?
Your Response: | <|clue|> Carlsen <|/clue|> <|evidence|> Carsten Carlsen (5 June 1892 – 28 August 1961) was a Norwegian pianist and composer. Carsten Marensius Carlsen was born in Oslo, Norway. His parents were Anton Carlsen (1862–1943) and Louise Larsen (1876–1957). <|sep|> Carlsen has directed more than 25 films, 19 for which he wrote the screenplay. In 2006, he received the Golden Swan Lifetime Achievement Award at the Copenhagen International Film Festival. Carlsen was born on 4 June 1927 in Aalborg, Denmark. <|/evidence|> The answer is pianist and composer. |{{< /table-caption >}}
> 🔼 이 표는 단일 홉 질문 답변 데이터셋에 대한 RetroLLM의 예시를 보여줍니다. 단서 생성 및 증거 생성 단계에 사용된 특수 토큰은 각각 주황색 상자와 파란색 상자로 강조 표시되어 있습니다. 생성된 모든 증거는 Wikipedia에서 가져온 것입니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Examples from RetroLLM on single-hop QA datasets, with special tokens used in the clue and evidence generation stages highlighted in  orange box and  blue box, respectively. All generated evidence is from Wikipedia.
> </details>

{{< table-caption >}}
| Example #1 from HotpotQA Dataset |                                                                                   |
| -------------------------------- | ------------------------------------------------------------------------------------- |
| **Question:**                   | Which American audio engineer and clandestine chemist, who was a key figure in the San Francisco Bay Area hippie movement during the 1960s recorded the album "Old and in the Way?" |
| **Labeled Answer:**             | ["Owsley Stanley"]                                                                  |
| **Results by RetroLLM**        |                                                                                   |
| **Model Input:**                | Question: Which American audio engineer and clandestine chemist, who was a key figure in the San Francisco Bay Area hippie movement during the 1960s recorded the album "Old and in the Way?" |
| **Model Output:**               | <|clue|> Old and in the Way <|sep|> Owsley Stanley <|/clue|> <|evidence|> Owsley Stanley III (January 19, 1935 – March 12, 2011) was an American audio engineer and clandestine chemist. He was a key figure in the San Francisco Bay Area hippie movement during the 1960s and played a pivotal role in the decade’s counterculture. <|sep|> Old & In the Way (album) Old & In the Way is the self-titled first album by the bluegrass band Old & In the Way. It was recorded 8 October 1973 at The Boarding House in San Francisco by Owsley Stanley and Vickie Babcock. <|sep|> The 1960s, elements of the expanding Beat movement were incorporated into the hippie and larger counterculture movements. Neal Cassady, as the driver for Ken Kesey’s bus Furthur, was the primary bridge between these two generations. Ginsberg’s work also became an integral element of early 1960s hippie culture. <|sep|> In San Francisco, including Quicksilver Messenger Service, Jefferson Airplane, early Jefferson Starship, Old & In the Way, Janis Joplin, Big Brother and the Holding Company, Taj Mahal, Santana, Miles Davis, The Flying Burrito Brothers, Jimi Hendrix, Johnny Cash, and Blue Cheer. <|/evidence|> The answer is Owsley Stanley. |
| **Example #2 from 2WikiMultiHopQA Dataset** |                                                                                   |
| **Question:**                    | Where was the director of film Ronnie Rocket born?                                       |
| **Labeled Answer:**            | ["Missoula", "Missoula, Montana"]                                                |
| **Results by RetroLLM**         |                                                                                   |
| **Model Input:**               | Question: Where was the director of film Ronnie Rocket born?                                       |
| **Model Output:**              | <|clue|> Ronnie Rocket <|/clue|> <|evidence|> Ronnie Rocket is an unfinished film project written by David Lynch, who also intended to direct it. Begun after the success of Lynch’s 1977 film "Eraserhead", "Ronnie Rocket" was shelved after Lynch felt he would be unable to find financial backing for the project. <|sep|> The script to the AFI, but they rejected it as they felt the planned 45-minute runtime was too long for such a figurative, nonlinear script. After the success of "Eraserhead", Lynch decided to focus on the screenplay of his second film, entitled "Ronnie Rocket", which he also wanted to direct. <|sep|> He can use to produce music or cause destruction. The boy names himself Ronnie Rocket and becomes a rock star, befriending a tap-dancer named Electra-Cute. The film was to make use of several themes that have since become recurring elements within David Lynch’s works, with a write-up for "The A.V. <|sep|> Dave Dennison, Max and Dani Dennison’s father, in Disney’s "Hocus Pocus". Rocket was born in Bangor, Maine, the son of Mary Aurelia (Fogler) and Sumner Abbott "Ham" Claverie. <|sep|> In 2008, Refn co-founded the Copenhagen-based production company Space Rocket Nation. Refn was born in Copenhagen, Denmark, and raised partly in New York, United States. Refn’s parents are Danish film director and editor Anders Refn and cinematographer Vibeke Winding. <|sep|> The two realized that "Ronnie Rocket" was unlikely to find sufficient financing to be produced, Lynch asked to see some already-written scripts to work from for his next film instead. Cornfeld found four scripts he felt Lynch would be interested in, but on hearing the name of the first, the director decided his next project would be "The Elephant Man". <|sep|> His next film, settling on what would become 1980’s "The Elephant Man". "Ronnie Rocket" was to feature many of the elements which have since come to be seen as Lynch’s hallmarks; including industrial art direction, 1950s popular culture and physical deformity. <|sep|> He shared with Billy Williams. Taylor was born in Hampstead, London and entered the film industry in his late teens working for Gainsborough Pictures at Lime Grove in Shepherds Bush. Taylor’s first film was as a clapper boy on "The Young Mr Pitt" (1942). <|sep|> In his films have earned them a reputation as works that "disturb, offend or mystify" general audiences. Although born in Missoula, Montana, Lynch spent his youth traveling across the United States due to his father Donald’s job for the Department of Agriculture; as a result, Lynch attended school across several states. <|/evidence|> The answer is Missoula, Montana. |{{< /table-caption >}}
> 🔼 이 표는 RetroLLM이 다중 홉 질의응답 데이터셋에서 생성한 예시를 보여주며, 단서 생성과 증거 생성 단계에 사용된 특수 토큰은 각각 주황색 상자와 파란색 상자로 강조 표시되어 있습니다. RetroLLM은 단서를 생성하여 관련 문서의 하위 집합을 식별한 다음, 이 하위 집합 내에서 순방향 탐색 제약 증거 생성을 수행합니다. 생성된 모든 증거는 Wikipedia에서 가져온 것입니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Examples from RetroLLM on multi-hop QA datasets, with special tokens used in the clue and evidence generation stages highlighted in  orange box and  blue box, respectively. All generated evidence is from Wikipedia.
> </details>

{{< table-caption >}}
| Example #1 from NQ Dataset |                                                                    |
| ------------------------- | ------------------------------------------------------------------ |
| Question:                 | who got the first nobel prize in physics?                           |
| Labeled Answer:          | ["Wilhelm Conrad Röntgen"]                                          |
| Results by RetroLLM      |                                                                    |
| Model Input:             | Question: who got the first nobel prize in physics?                           |
| Model Output:            | <|clue|> Nobel Prize <|sep|> Physics <|/clue|> <|evidence|> the others being the Nobel Prize in Chemistry, Nobel Prize in Literature, Nobel Peace Prize, and Nobel Prize in Physiology or Medicine. The first Nobel Prize in Physics was awarded to physicist <span style="color:#00994D;">Wilhelm Röntgen</span> in recognition of the extraordinary services he rendered by the discovery of the remarkable rays (or X-rays).  <|/evidence|> The answer is <span style="color:#00994D;">Wilhelm Röntgen</span>. |
| Results by Naive Constrained Beam Search |                                                                    |
| Model Input:             | Question: who got the first nobel prize in physics?                           |
| Model Output (beam_size = 5): |                                                                    |
| Beam 1:                  | <|evidence|> in 1901, the first year of play for the American League. The modern-era record for lowest batting average for a player that qualified for the batting title is .197 by roger maris in 1962.  <|/evidence|> The answer is <span style="color:#FF0000;">Roger Maris</span>. |
| Beam 2:                  | <|evidence|> the first physics and chemistry laboratory in a Danish school in 1903, the inclusion of housekeeping in the curriculum, and the first girls’ school to include carpentry in the curriculum in 1904.  <|/evidence|> The answer is <span style="color:#FF0000;">1903</span>. |
| Beam 3:                  | <|evidence|> william johnson Jonathan Elliot (historian) Jonathan Elliot (17842̆0131846) was a 19th-century  <|/evidence|> The answer is <span style="color:#FF0000;">Jonathan Elliot</span>. |
| Beam 4:                  | <|evidence|> the first physics Nobel prize winner born in an Arab country. In 2015, Cohen-Tannoudji signed the M̈ainau Declaration 2015ẅhich calls for a boycott of israel.  <|/evidence|> The answer is <span style="color:#FF0000;">Cohen - Tannoudji</span>. |
| Beam 5:                  | <|evidence|> the first prize was awarded in 2004. He was the sixth of the seven children in the Shaw family, and was nicknamed Uncle Six (L̈uk Sook)̈.  <|/evidence|> The answer is <span style="color:#FF0000;">He was the sixth of the seven children in the Shaw family</span>. |{{< /table-caption >}}
> 🔼 RetroLLM과 Naive 제약 빔 검색 방법의 출력을 비교한 예시입니다. 단서 및 증거 생성 단계에서 사용된 특수 토큰은 각각 주황색 상자와 파란색 상자로 강조 표시됩니다. 녹색으로 표시된 내용은 정답(또는 부분적으로 정답)을 나타내고 빨간색으로 표시된 내용은 오답을 나타냅니다. 모든 생성된 증거는 Wikipedia에서 가져온 것입니다. 이 표는 Naive 제약 빔 검색의 잘못된 가지치기 문제점과 RetroLLM이 이 문제를 해결하는 방법을 보여주는 사례 연구 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Table 11: An example comparing outputs from RetroLLM and the naive constrained beam search method. Special tokens used during the clue and evidence generation stages are highlighted in  orange boxes and  blue boxes, respectively. Content colored in green indicates correct (or partially correct) answers, whereas content colored in red indicates incorrect answers. All generated evidence is from Wikipedia.
> </details>

{{< table-caption >}}
| Example #2 from TriviaQA Dataset |                                                                         |
| :----------------------------- | :------------------------------------------------------------------- |
| **Question:**                 | Who was the man behind The Chipmunks?                               |
| **Labeled Answer:**            | ["David Seville"]                                                   |
| **Results by RetroLLM**        |                                                                      |
| **Model Input:**               | Question: Who was the man behind The Chipmunks?                       |
| **Model Output:**              | <|clue|> The Chipmunks <|/clue|> <|evidence|> known by the stage name David Seville, was an American singer-songwriter and actor, best known for creating the novelty musical group The Chipmunks (now better known as "Alvin and the Chipmunks"). Initially a stage and film actor, he rose to prominence in 1958 with the songs "Witch Doctor" and "The Chipmunk Song (Christmas Don’t Be Late),", which both became "Billboard" number-one singles. <|/evidence|> The answer is David Seville. |
| **Results by Naive Constrained Beam Search** |                                                                      |
| **Model Input:**               | Question: Who was the man behind The Chipmunks?                       |
| **Model Output (beam_size = 5):** |                                                                      |
| **Beam 1:**                   | <|evidence|> david was optioned to the Triple-A Richmond Braves to start the 1992 season. He made his major league debut for the Braves on <|/evidence|> The answer is David. |
| **Beam 2:**                   | <|evidence|> the chipmunks’ speech was created by speeding up sound clips of normal speech. In a number of the shorts that followed, many of these same sound clips were reused, but the chipmunks’ voices were created by using a higher pitch on the original recordings. <|/evidence|> The answer is Ross Bagdasarian. |
| **Beam 3:**                   | <|evidence|> alvinophilia is a partialism in which a man or woman is attracted to the human navel. According to a study, it is a moderately prevalent fetish among men, and less so among women. <|/evidence|> The answer is Alvin. |
| **Beam 4:**                   | <|evidence|> the chipmunks are also mostly supplemental prey but are considered more easily caught than tree squirrels, considering that they are more habitual terrestrial foragers. <|/evidence|> The answer is Alvin. |
| **Beam 5:**                   | <|evidence|> the chipmunks are also mostly supplemental prey but are considered more easily caught than tree squirrels, considering that they are more habitual terrestrial foragers. <|/evidence|> The answer is Tree Squirrels. |{{< /table-caption >}}
> 🔼 RetroLLM과 단순 제약 빔 검색 방법의 출력을 비교한 예시입니다. 단서 및 증거 생성 단계에 사용된 특수 토큰은 각각 주황색 상자와 파란색 상자로 강조 표시되어 있습니다. 녹색으로 표시된 내용은 정답을, 빨간색으로 표시된 내용은 오답을 나타냅니다. 모든 생성된 증거는 Wikipedia에서 가져온 것입니다.
> <details>
> <summary>read the caption</summary>
> Table 12: An example comparing outputs from RetroLLM and the naive constrained beam search method. Special tokens used during the clue and evidence generation stages are highlighted in  orange boxes and  blue boxes, respectively. Content colored in green indicates correct answers, whereas content colored in red indicates incorrect answers. All generated evidence is from Wikipedia.
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