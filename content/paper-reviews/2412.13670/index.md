---
title: "AntiLeak-Bench: Preventing Data Contamination by Automatically Constructing Benchmarks with Updated Real-World Knowledge"
summary: "AntiLeak-Bench: 자동화된 벤치마킹으로 LLM 데이터 오염 방지"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Nanyang Technological University",]
showSummary: true
date: 2024-12-18
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.13670 {{< /keyword >}}
{{< keyword icon="writer" >}} Xiaobao Wu et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-19 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.13670" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.13670" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/antileak-bench-preventing-data-contamination" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)의 성능 평가는 데이터 오염 문제로 인해 어려움을 겪고 있습니다. 기존 연구에서는 새로운 데이터로 벤치마크를 업데이트하려는 시도가 있었지만, 새 데이터에도 기존 지식이 포함될 수 있다는 점과 많은 인력이 필요하다는 한계점이 존재했습니다.

본 논문에서는 이러한 문제를 해결하기 위해 AntiLeak-Bench라는 자동화된 벤치마킹 프레임워크를 제안합니다. AntiLeak-Bench는 LLM 학습 데이터에는 없는 새로운 지식을 사용하여 샘플을 생성하고, 자동화된 워크플로우를 통해 벤치마크를 지속적으로 업데이트합니다. 이를 통해 데이터 오염 없는 LLM 평가를 보장하고, 유지보수 비용을 절감하며, 다국어 지원을 가능하게 합니다.  실험 결과, AntiLeak-Bench가 데이터 오염 문제를 효과적으로 해결하고 LLM의 성능을 정확하게 평가하는 데 효과적임을 보여줍니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 자동화된 벤치마킹 프레임워크 AntiLeak-Bench를 통해 LLM의 데이터 오염 문제 해결 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 실제 세계 지식 업데이트를 활용하여 오염 없는 평가 보장 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 인력 없이 벤치마크 자동 업데이트 및 유지보수 가능 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **데이터 오염 문제**를 해결하기 위한 새로운 벤치마킹 프레임워크를 제시하여, LLM 평가의 신뢰성과 타당성을 높이는 데 중요한 의미를 가집니다. **자동화된 워크플로우**를 통해 지속적인 벤치마크 유지보수 비용을 절감하고, 다양한 언어 지원을 통해 **다국어 평가**를 가능하게 합니다. 이는 LLM 연구의 발전에 기여하고, 향후 연구 방향을 제시할 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.13670/x1.png)

> 🔼 그림 1은 AntiLeak-Bench의 작동 방식을 보여줍니다. AntiLeak-Bench는 LLMs의 지식 차단 시간 이후에 업데이트된 지식을 사용하여 오염되지 않은 샘플을 생성합니다.  즉, LLMs의 학습 데이터셋에는 없는 최신 지식을 기반으로 샘플을 만듭니다. 이를 통해 LLMs의 평가 시 데이터 오염 문제를 해결합니다. 그림에서는 시간 경과에 따른 LLMs의 학습 데이터셋과 새롭게 추가된 지식, 그리고 AntiLeak-Bench가 생성하는 오염되지 않은 샘플 간의 관계를 시각적으로 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  Illustration of AntiLeak-Bench. It constructs contamination-free samples with the knowledge updated after LLMs’ cutoff time, which thus are not in LLMs’ training sets.
> </details>





{{< table-caption >}}
| Benchmark | Strictly Contamination-Free | Automated | Multilingual | Data Source |
|---|---|---|---|---|
| Realtime QA [Kasai et al. (2023)] | ✗ | ✗ | ✗ | Real world |
| LiveBench [White et al. (2024)] | ✗ | ✗ | ✗ | Real world |
| ADU [Ying et al. (2024)] | ✗ | ✓ | ✗ | LLM generation |
| **AntiLeak-Bench** | ✓ | ✓ | ✓ | Real world |{{< /table-caption >}}

> 🔼 표 1은 AntiLeak-Bench와 다른 벤치마킹 프레임워크들을 비교 분석한 표입니다. AntiLeak-Bench는 데이터 오염 방지를 위해 자동화된 워크플로우를 사용하여 최신 실제 세계 지식을 사용하는 샘플을 생성하고, 이를 통해 오염 없는 평가를 보장합니다. 이 표는 AntiLeak-Bench의 주요 특징인 데이터 오염 방지, 자동화, 다국어 지원 여부를 다른 프레임워크들과 비교하여 AntiLeak-Bench의 강점을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1:  Comparisons between AntiLeak-Bench and other benchmarking frameworks.
> </details>





### In-depth insights


#### LLM Data Leakage
LLM 데이터 유출은 대규모 언어 모델(LLM)의 훈련 데이터가 평가 데이터와 겹치는 현상을 말합니다. 이는 모델의 성능 평가에 심각한 영향을 미칩니다. **평가 데이터가 이미 모델의 훈련에 사용된 경우, 모델은 실제 성능보다 과장된 성능을 보일 수 있습니다.**  이는 모델의 일반화 능력을 제대로 평가하지 못하게 하여 잘못된 결론을 도출할 수 있습니다.  따라서 LLM 데이터 유출 문제는 **모델의 신뢰성과 유효성을 심각하게 저해**하는 문제입니다. 이를 해결하기 위한 다양한 방법들이 연구되고 있으며, 새로운 데이터를 사용하거나, 데이터 겹침을 방지하는 기술 등이 개발되고 있습니다.  **데이터 유출을 방지하는 것은 LLM의 공정하고 정확한 평가를 위해 매우 중요**하며, 앞으로도 지속적인 연구와 개선이 필요한 분야입니다.  특히, **자동화된 벤치마크 생성 및 업데이트**는 데이터 유출 문제 해결에 큰 도움이 될 것으로 예상됩니다.

#### AntiLeak-Bench
AntiLeak-Bench는 **데이터 오염** 문제를 해결하기 위해 고안된 자동화된 벤치마킹 프레임워크입니다. 기존 연구들이 새롭게 수집된 데이터를 사용하여 벤치마크를 업데이트하는 방식과 달리, AntiLeak-Bench는 **LLM의 학습 데이터에는 존재하지 않는 새로운 지식**을 사용하여 샘플을 생성합니다. 이를 통해 오염 없는 평가를 보장하고, **인력 의존도를 줄여 유지보수 비용을 절감**합니다.  자동화된 워크플로우를 통해 새로운 LLM이 등장해도 벤치마크를 손쉽게 업데이트할 수 있습니다. 실험 결과는 LLM의 차단 시간 이전에도 데이터 오염 가능성이 있음을 보여주며, AntiLeak-Bench가 이 문제를 효과적으로 해결함을 입증합니다. **실제 데이터**를 사용하고 **다국어 지원**으로 실용성과 확장성을 높인 점도 장점입니다.  그러나 **다양한 작업**에 대한 평가 확장 및 **데이터 소스의 정확성**에 대한 추가 검증이 향후 개선 과제로 남아있습니다.

#### Automated Workflow
본 논문에서 제시된 자동화 워크플로는 **인적 자원 없이도 벤치마크를 원활하게 업데이트**할 수 있게 함으로써, 새롭게 등장하는 LLM에 대한 적응력을 높이고 유지보수 비용을 크게 줄입니다.  **자동화된 프로세스**는 Wikidata와 Wikipedia의 최신 데이터를 활용하여 오래된 지식과 새로운 지식을 식별하고, 오염되지 않은 샘플을 생성하는 데 중점을 둡니다. 이러한 자동화는 **주기적인 유지보수 및 업데이트**를 가능하게 하여, 벤치마크의 실용성과 확장성을 향상시키는 핵심 요소가 됩니다.  하지만, **자동화 워크플로의 신뢰도**는 Wikidata 및 Wikipedia의 데이터 정확성에 의존하며, **새로운 지식의 정확성 검증**을 위한 추가적인 검증 절차가 필요할 수 있습니다.  **다양한 언어 지원**과 **다양한 작업 유형**에 대한 확장 가능성도 향후 개선 과제로 제시될 수 있습니다.

#### Multi-hop Reasoning
본 논문에서 다루는 멀티홉 추론(Multi-hop reasoning)은 **단일 정보원으로부터 답을 얻을 수 없는 질문들에 대한 능력**을 평가하는 데 초점을 맞춥니다.  이는 맥락(context) 내 여러 문장이나 지식베이스의 여러 항목을 종합적으로 이해하고, 그 관계를 파악하여 답을 도출하는 고차원적인 추론 능력을 요구합니다.  **단순한 키워드 매칭이나 표면적인 이해를 넘어, 깊이 있는 의미 이해와 지식 간의 연결 관계 파악**이 중요하며, 이는 **대규모 언어 모델(LLM)의 진정한 이해 능력**을 평가하는 데 중요한 지표가 됩니다.  따라서, 본 논문에서 제시된 멀티홉 추론 과제는 LLM의 성능 평가에 있어 중요한 역할을 하며, **단순한 퀴즈 풀이를 넘어선 진정한 추론 능력**을 측정하는 데 활용될 수 있음을 시사합니다.  **다양한 난이도의 멀티홉 추론 문제**를 통해 LLM의 추론 능력의 한계와 가능성을 더욱 정확하게 파악할 수 있습니다.

#### Benchmark Limits
본 논문에서 'Benchmark Limits' 라는 제목으로 다뤄질 만한 내용은 **기존 벤치마크의 한계점**에 대한 분석일 것입니다.  이는 크게 두 가지 측면에서 논의될 수 있습니다. 첫째는 **데이터 오염 문제**로, 기존 벤치마크의 테스트 데이터가 새로운 모델의 학습 데이터에 포함되어 성능 평가의 신뢰도를 떨어뜨리는 문제입니다.  둘째는 **유지보수의 어려움**으로, 새로운 언어 모델의 등장 및 지식의 급속한 변화에 따라 기존 벤치마크를 지속적으로 업데이트하는 데 많은 시간과 노력이 필요하다는 점입니다. 따라서 이 논문에서는 이러한 한계점을 극복하기 위해 **자동화된 벤치마크 생성 및 업데이트 시스템**을 제안할 것으로 예상됩니다.  이 시스템은 새롭게 등장한 지식만을 사용하여 데이터 오염을 방지하고, 자동화를 통해 유지보수 비용을 절감하여 **더욱 신뢰성 있고 지속 가능한 벤치마킹**을 가능하게 할 것으로 예상됩니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.13670/x2.png)

> 🔼 그림 2는 사람의 개입 없이 자동화된 벤치마크 구축 워크플로우를 보여줍니다. 데이터 준비 후, 세 가지 주요 단계가 있습니다. 1단계는 LLM의 차단 시간 이후에 업데이트된 지식을 식별하는 것입니다. 2단계는 위키피디아와 같은 신뢰할 수 있는 출처에서 업데이트된 지식에 대한 지원 문서를 구축하는 것입니다. 3단계는 오염이 없는 샘플을 생성하는 것입니다. 그림 3은 다단계 샘플을 만드는 방법을 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 2:  Illustration of the automated benchmark building workflow without human labor. After data preparation, it includes three main steps: (1) Identify updated knowledge after the cutoff time; (2) Build supporting documents; (3) Construct contamination-free samples (Figure 3 exemplifies how to construct multi-hop samples).
> </details>



![](https://arxiv.org/html/2412.13670/x3.png)

> 🔼 그림 3은 다단계 질문 생성 과정을 보여줍니다. 다단계 질문은 여러 개의 사실들을 연결하여 답을 도출해야 하는 질문 유형입니다. 그림에서는, 기존 지식(LLM의 학습 데이터에 존재하는 지식)과 새로운 지식(LLM의 학습 데이터에 없는, 최신 지식)을 연결하여 다단계 질문을 만드는 과정을 보여줍니다. 먼저, 새로운 지식을 나타내는 (주어, 관계, 목적어) 튜플을 기반으로 질문을 생성합니다. 이후 이전 목적어와 관련된 새로운 관계를 찾아 추가적인 지식을 연결합니다. 이런 과정을 반복하여 다단계 질문을 완성합니다.  최종 질문은 여러 단계의 추론을 거쳐 답을 얻어야 하는 복잡한 질문입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3:  Illustration of constructing multi-hop samples. Find the consequent relation of previous objects.
> </details>



![](https://arxiv.org/html/2412.13670/x4.png)

> 🔼 그림 4는 시간 경과에 따른 다양한 언어 모델(LLM)의 성능 변화를 보여줍니다. EM(정확히 일치)과 F1 점수는 각 시간 간격(예: 1월-2월, 3월-4월 등)에서 측정됩니다. 이를 통해 시간이 지남에 따라 LLM의 성능 변화를 추적하고 데이터 오염(data contamination)의 영향을 분석하는 데 도움이 됩니다. 각 그래프는 여러 개의 LLM에 대한 EM과 F1 점수를 보여주며, 시간대별 성능 변화를 비교할 수 있도록 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4:  EM and F1 performance at each time interval.
> </details>



![](https://arxiv.org/html/2412.13670/x5.png)

> 🔼 그림 5는 시간 경과에 따른 정답 옵션과 오래된 옵션의 비율을 보여줍니다. 각 시간 간격(예: 1월-2월, 3월-4월 등)에 대해 여러 언어 모델(LLM)이 정답 옵션을 선택한 비율과 오래된 옵션(즉, LLM의 지식 차단 시간 이전의 정보)을 선택한 비율을 나타냅니다. 이는 데이터 오염의 영향을 분석하고 시간에 따른 모델 성능 변화를 파악하는 데 사용됩니다. 각 LLM의 지식 차단 시간을 고려하여, 시간 경과에 따라 정답률이 감소하고 오래된 옵션 선택 비율이 증가하는 경향을 보이는지 확인합니다. 이를 통해 데이터 오염이 모델 평가에 미치는 영향을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5:  Correct and outdated option proportions at each time interval.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Attributes | Examples |
|---|---| 
| question<br/>(generation) | What sports team is Lionel Andrés Messi a member of? |
| answer<br/>(generation) | Inter Miami CF<br/>Inter Miami<br/>Club Internacional de Fútbol Miami |
| question<br/>(multi-choice) | What sports team is Lionel Andrés Messi a member of?<br/>A. Inter Miami CF<br/>B. Paris Saint-Germain F.C.<br/>C. Prime Minister of Romania<br/>D. Unknown. |
| answer<br/>(multi-choice) | A |
| subject | Lionel Messi<br/>Lionel Andres Messi<br/>Lionel Andrés Messi |
| pid | P54 (member of sports team) |
| object | Inter Miami CF<br/>Inter Miami<br/>Club Internacional de Fútbol Miami |
| object_old | Paris Saint-Germain F.C.<br/>Paris Saint-Germain Football Club<br/>Paris Saint-Germain FC |
| context | Lionel Andrés Messi (; born 24 June 1987), also known as Leo Messi, is an Argentine professional footballer who plays as a forward for Major League Soccer club Inter Miami… |{{< /table-caption >}}
> 🔼 표 2는 AntiLeak-Bench에서 생성된 샘플 데이터의 예시를 보여줍니다.  질문, 답변, 맥락, 그리고 각 항목에 대한 속성(주어, 관계, 목적어, 이전 목적어, 맥락)을 포함하여 AntiLeak-Bench 데이터의 구조와 내용을 이해하는 데 도움이 됩니다.  여러 언어를 지원하는 AntiLeak-Bench의 특징도 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 2:  An example from AntiLeak-Bench.
> </details>

{{< table-caption >}}
| Quality Metrics | Single-Hop Gold | Multi-Hop Gold |
|---|---|---|
| Context Accuracy | 97.3 | 98.7 |
| Answer Accuracy | 96.7 | 97.3 |{{< /table-caption >}}
> 🔼 본 논문의 표 3은 사람이 검증한 데이터의 품질을 보여줍니다.  정확도는 단일 단계 질문(Single-Hop Gold)에서 97.3%, 다중 단계 질문(Multi-Hop Gold)에서 96.7%로 매우 높습니다. 이는 AntiLeak-Bench 데이터셋의 높은 신뢰도를 보여주는 지표입니다.
> <details>
> <summary>read the caption</summary>
> Table 3:  Data quality by human verification.
> </details>

{{< table-caption >}}
| Language | Models | Single-Hop EM | Single-Hop F1 | Single-Hop EM | Single-Hop F1 | Single-Hop EM | Single-Hop F1 | Single-Hop EM | Single-Hop F1 | Multi-Hop EM | Multi-Hop F1 | Multi-Hop EM | Multi-Hop F1 | Multi-Hop EM | Multi-Hop F1 | Multi-Hop EM | Multi-Hop F1 | Avg EM | Avg F1 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|  |  | $N_d$=3 | $N_d$=5 | $N_d$=7 | $N_d$=3 | $N_d$=5 | $N_d$=7 | Gold | Gold |  |  |  |  |  |  |  |  |
| Llama-2-7B | 40.6 | 63.5 | 16.8 | 41.2 | 11.6 | 30.9 | 9.4 | 24.5 | 33.6 | 50.2 | 19.4 | 32.2 | 15.8 | 28.1 | 12.2 | 22.7 | 19.9 | 36.7 |
| Llama-2-13B | 42.7 | 65.3 | 14.0 | 40.6 | 9.4 | 30.6 | 7.0 | 24.0 | 13.3 | 34.6 | 4.1 | 21.5 | 2.7 | 17.8 | 2.3 | 15.2 | 11.9 | 31.2 |
| Mistral-7B | 65.4 | 77.2 | 27.8 | 41.3 | 16.7 | 27.3 | 7.3 | 15.3 | 21.4 | 27.9 | 11.5 | 17.2 | 8.1 | 14.3 | 6.5 | 11.1 | 20.6 | 29.0 |
| Vicuna-v1.5-7B | 66.8 | 79.9 | 39.1 | 60.4 | 25.8 | 48.3 | 15.3 | 39.1 | 26.0 | 43.5 | 11.1 | 22.9 | 8.1 | 19.5 | 5.4 | 15.7 | 24.7 | 41.2 |
| Longchat-v1.5-7B | 75.5 | 84.5 | 58.2 | 72.8 | 47.6 | 65.5 | 37.0 | 56.3 | 38.8 | 51.4 | 17.6 | 30.6 | 12.0 | 25.8 | 4.7 | 3.9 | 36.4 | 48.9 |
| Llama-3.1-8B | 19.2 | 66.2 | 21.4 | 59.4 | 18.1 | 53.5 | 14.2 | 45.7 | 24.4 | 50.2 | 11.7 | 33.0 | 9.4 | 27.5 | 6.8 | 21.9 | 15.6 | 44.7 |
| Phi-3.5-mini | 69.0 | 78.7 | 34.0 | 40.5 | 26.5 | 33.7 | 15.2 | 22.2 | 45.4 | 59.7 | 20.8 | 29.5 | 14.9 | 21.1 | 9.8 | 14.4 | 29.4 | 37.5 |
| Qwen-2-7B | 54.8 | 72.4 | 15.5 | 38.5 | 9.8 | 26.6 | 7.2 | 21.2 | 35.9 | 48.3 | 23.7 | 33.4 | 18.1 | 26.1 | 13.6 | 20.1 | 22.3 | 35.8 |
| Mistral-Nemo-12B | 82.7 | 89.7 | 75.6 | 83.8 | 66.3 | 75.1 | 51.8 | 62.2 | 57.7 | 67.3 | 39.1 | 47.7 | 33.8 | 41.4 | 24.0 | 29.0 | 53.9 | 62.0 |
| Gemma-2-9B | 85.0 | 91.6 | 80.2 | 86.2 | 68.8 | 75.2 | 55.4 | 61.2 | 82.7 | 86.4 | 63.0 | 68.3 | 55.8 | 61.2 | 49.0 | 53.5 | 67.5 | 73.0 |
| GPT-4o-mini | 78.5 | 88.1 | 80.3 | 89.2 | 79.1 | 88.1 | 79.2 | 88.5 | 68.8 | 83.1 | 60.5 | 75.3 | 57.1 | 73.1 | 54.2 | 70.6 | 69.7 | 82.0 |
| GPT-4o | 81.2 | 89.5 | 84.1 | 90.8 | 83.5 | 90.3 | 84.8 | 91.4 | 71.5 | 85.9 | 71.9 | 86.1 | 70.2 | 84.8 | 70.2 | 84.8 | 77.2 | 87.9 |}{{< /table-caption >}}
> 🔼 표 4는 AntiLeak-Bench의 성능 평가 결과를 보여줍니다.  EM(Exact Match)과 F1 점수는 생성형식 질문응답 태스크에 대한 결과를 나타내며, Gold는 방해 요소가 없는 데이터셋을 의미하고, Nd는 추가된 방해 요소(distracting documents)의 개수를 나타냅니다.  각 지표의 최고 점수는 굵게 표시되어 있습니다. 이 표는 다양한 규모와 종류의 언어 모델(LLM)의 성능을 비교하고,  AntiLeak-Bench 벤치마크에서 데이터 오염(data contamination)의 영향을 확인하기 위한 실험 결과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 4:  EM (Exact Match) and F1 results in the generation format on AntiLeak-Bench. Gold means only gold documents; Ndsubscript𝑁𝑑N_{d}italic_N start_POSTSUBSCRIPT italic_d end_POSTSUBSCRIPT is the number of distracting documents. The best is in bold.
> </details>

{{< table-caption >}}
| Language | Models | Single-Hop Acc | Single-Hop F1 | Single-Hop Acc | Single-Hop F1 | Single-Hop Acc | Single-Hop F1 | Single-Hop Acc | Single-Hop F1 | Multi-Hop Acc | Multi-Hop F1 | Multi-Hop Acc | Multi-Hop F1 | Multi-Hop Acc | Multi-Hop F1 | Multi-Hop Acc | Multi-Hop F1 | Avg Acc | Avg F1 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|  |  | $N_d$=3 | $N_d$=5 | $N_d$=7 | $N_d$=3 | $N_d$=5 | $N_d$=7 |  |  | $N_d$=3 | $N_d$=5 | $N_d$=7 |  |  |  |  |  |
| Llama-2-7B | 41.7 | 30.7 | 3.7 | 5.6 | 3.5 | 5.3 | 2.8 | 5.4 | 18.7 | 30.9 | 6.8 | 9.9 | 5.6 | 8.1 | 3.6 | 6.9 | 10.8 | 12.9 |
| Llama-2-13B | 82.1 | 82.2 | 73.7 | 73.6 | 60.1 | 59.9 | 51.7 | 51.3 | 97.5 | 97.5 | 88.5 | 88.5 | 82.8 | 83.1 | 75.2 | 75.2 | 76.5 | 76.4 |
| Mistral-7B | 81.8 | 81.8 | 65.9 | 65.8 | 58.3 | 58.2 | 52.3 | 52.3 | 88.7 | 88.6 | 77.2 | 77.2 | 72.7 | 72.8 | 67.7 | 67.2 | 70.6 | 70.5 |
| Vicuna-v1.5-7B | 80.1 | 80.0 | 75.6 | 75.4 | 73.1 | 72.9 | 69.6 | 69.4 | 96.8 | 96.9 | 84.0 | 84.2 | 82.6 | 83.0 | 77.0 | 77.2 | 79.8 | 79.9 |
| Longchat-v1.5-7B | 79.6 | 79.7 | 68.5 | 68.8 | 65.1 | 51.8 | 62.3 | 61.2 | 93.2 | 93.4 | 76.7 | 78.0 | 70.4 | 71.5 | 66.6 | 68.0 | 72.8 | 71.6 |
| Llama-3.1-8B | 86.7 | 90.4 | 62.2 | 74.0 | 48.9 | 62.9 | 37.8 | 52.9 | 70.5 | 81.4 | 50.7 | 64.8 | 40.9 | 56.2 | 30.8 | 44.9 | 53.6 | 65.9 |
| Phi-3.5-mini | 87.4 | 87.5 | 85.6 | 85.8 | 84.7 | 85.4 | 79.6 | 82.5 | 96.5 | 97.0 | 85.3 | 86.2 | 78.0 | 80.3 | 68.6 | 72.3 | 83.2 | 84.6 |
| Qwen-2-7B | 89.1 | 39.7 | 83.0 | 27.9 | 78.2 | 24.6 | 77.0 | 78.5 | 97.6 | 98.3 | 94.5 | 54.2 | 92.4 | 46.4 | 91.5 | 91.7 | 87.9 | 57.7 |
| Mistral-Nemo-12B | 88.5 | 71.1 | 88.8 | 71.8 | 84.7 | 70.2 | 77.8 | 83.8 | 91.1 | 94.6 | 77.1 | 68.4 | 69.9 | 64.0 | 43.1 | 58.7 | 77.6 | 72.8 |
| Gemma-2-9B | 92.4 | 92.4 | 86.7 | 86.5 | 76.9 | 61.6 | 69.4 | 69.3 | 97.1 | 97.1 | 88.3 | 88.3 | 81.8 | 65.4 | 77.4 | 77.4 | 83.8 | 79.8 |
| GPT-4o-mini | 93.2 | 93.2 | 93.8 | 93.8 | 93.3 | 93.3 | 93.5 | 93.5 | 98.5 | 98.5 | 96.4 | 96.4 | 95.4 | 95.4 | 93.5 | 93.5 | 94.7 | 94.7 |
| GPT-4o | 92.8 | 92.8 | 93.5 | 93.5 | 94.0 | 94.0 | 94.0 | 94.0 | 97.9 | 97.9 | 95.8 | 95.8 | 95.4 | 95.4 | 93.9 | 93.9 | 94.7 | 94.7 |{{< /table-caption >}}
> 🔼 표 5는 AntiLeak-Bench에서 다지선다 형식으로 평가한 결과를 보여줍니다.  Gold는 방해 요소가 없는 데이터셋을 의미하며, Nd는 추가된 방해 요소 문서의 개수입니다.  각 모델의 정확도(Acc)와 F1 점수가 제시되어 있으며, 가장 높은 점수는 굵게 표시되어 있습니다. 이 표는 모델의 성능을 다양한 수준의 난이도(방해 요소 문서 개수)에서 비교하고, AntiLeak-Bench의 효과성을 확인하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 5:  Acc and F1 results in the multi-choice format on AntiLeak-Bench. Gold means only gold documents; Ndsubscript𝑁𝑑N_{d}italic_N start_POSTSUBSCRIPT italic_d end_POSTSUBSCRIPT is the number of distracting documents. The best is in bold.
> </details>

{{< table-caption >}}
| Time period | Single-Hop |  |  |  | Multi-Hop |  |  |  |
|---|---|---|---|---|---|---|---|---|
|  | Gold |  Nd=3 | Nd=5 | Nd=7 | Gold | Nd=3 | Nd=5 | Nd=7 |
|---|---|---|---|---|---|---|---|---|
| 2022-01-01 to 2023-01-01 | 1090 | 1089 | 1088 | 1088 | 443 | 443 | 443 | 443 |
| 2023-05-01 to 2024-08-01 | 819 | 818 | 818 | 818 | 941 | 939 | 939 | 939 |{{< /table-caption >}}
> 🔼 이 표는 논문의 실험에서 사용된 AntiLeak-Bench의 구성에 대한 정보를 제공합니다. 각 시간대(2022년 1월 1일~2023년 1월 1일, 2023년 5월 1일~2024년 8월 1일)별로, Single-Hop(단일 단계 질문 답변)과 Multi-Hop(다단계 질문 답변) 작업에 대해 Gold(오염되지 않은 데이터), Na=3(3개의 방해 요소 문장), Na=5(5개의 방해 요소 문장), Na=7(7개의 방해 요소 문장) 데이터 세트의 크기(샘플 수)를 보여줍니다. AntiLeak-Bench는 데이터 오염을 방지하기 위해 업데이트된 실제 지식을 사용하여 생성된 벤치마크이므로, 이 표는 벤치마크의 크기와 구성을 이해하는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Table 6:  Sample sizes in the constructed AntiLeak-Bench in the experiments.
> </details>

{{< table-caption >}}
| Time period | Single-Hop |  |  |  | Multi-Hop |  |  |  |
|---|---|---|---|---|---|---|---|---|
| **Gold** | **Gold** |  **Nd=3** | **Nd=5** | **Nd=7** | **Gold** | **Nd=3** | **Nd=5** | **Nd=7** |
| 2022-01-01 to 2023-01-01 | 5998 | 23163 | 33867 | 46033 | 24646 | 40611 | 50846 | 61761 |
| 2023-05-01 to 2024-08-01 | 7210 | 27501 | 40800 | 54451 | 25505 | 43926 | 53898 | 66957 |{{< /table-caption >}}
> 🔼 본 표는 AntiLeak-Bench 데이터셋 구축 실험에서 사용된 샘플들의 평균 단어 수를 보여줍니다.  AntiLeak-Bench는  LLM의 학습 데이터에 없는 최신 실제 세계 지식을 사용하여 구축된 벤치마크입니다. 표는 두 가지 기간(2022년 1월 1일~2023년 1월 1일, 2023년 5월 1일~2024년 8월 1일)과 다양한 유형의 질문(단일 홉 골드, 단일 홉 Na=3, 단일 홉 Na=5, 단일 홉 Na=7, 다중 홉 골드, 다중 홉 Na=3, 다중 홉 Na=5, 다중 홉 Na=7)에 대해 각 샘플의 평균 단어 수를 나타냅니다.  Na는 방해 요소 문서의 수를 나타냅니다. 이 표는 AntiLeak-Bench 데이터셋의 크기와 복잡성에 대한 통찰력을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 7:  Average word counts of samples in the constructed AntiLeak-Bench in the experiments.
> </details>

{{< table-caption >}}
| Model | Release time | Knowledge cutoff time |
|---|---|---|
| Llama-2-7B | 2023-07 | 2022-09 |
| Llama-2-13B | 2023-07 | 2022-09 |
| Mistral-7B | 2023-09 | 2022* |
| Vicuna-v1.5-7B | 2023-07 | 2022-09 |
| Longchat-v1.5-7B | 2023-07 | 2022-09 |
| Llama-3.1-8B | 2024-07 | 2023-12 |
| Phi-3.5-mini | 2024-08 | 2023-10 |
| Qwen-2-7B | 2024-06 | 2023* |
| Mistral-Nemo-12B | 2024-07 | 2024-04 |
| Gemma-2-9B | 2024-08 | 2024-06* |
| GPT-4o-mini | 2024-07 | 2023-10 |
| GPT-4o | 2024-07 | 2023-12 |{{< /table-caption >}}
> 🔼 표 8은 논문에서 사용된 대규모 언어 모델(LLM)의 출시일과 지식 차단 시점을 보여줍니다. 지식 차단 시점이란 LLM이 훈련 데이터를 수집을 마친 시점을 의미하며, 이후의 지식은 LLM이 학습하지 못했음을 의미합니다. 표에는 모델 이름, 출시일, 그리고 지식 차단 시점이 나와 있으며, 일부 모델의 경우 지식 차단 시점은 추정값(*)으로 표시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 8:  Release dates and knowledge cutoff dates of LLMs. * means estimated time.
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