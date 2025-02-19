---
title: "PhysReason: A Comprehensive Benchmark towards Physics-Based Reasoning"
summary: "PhysReason: 대규모 언어 모델의 물리 기반 추론 능력을 종합적으로 평가하는 새로운 벤치마크"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Xi'an Jiaotong University",]
showSummary: true
date: 2025-02-17
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.12054 {{< /keyword >}}
{{< keyword icon="writer" >}} Xinyu Zhang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-18 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.12054" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.12054" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/physreason-a-comprehensive-benchmark-towards" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

최근 대규모 언어 모델(LLM)은 수학, 논리 추론 등 다양한 분야에서 놀라운 성능을 보여주고 있지만, **물리 기반 추론** 능력은 여전히 부족합니다. 기존의 물리 문제 벤치마크는 추론 과정이 단순하고 단계별 평가가 부족하여, LLM의 물리적 현상 이해 및 문제 해결 능력을 정확하게 평가하기 어렵습니다. 

본 연구에서는 이러한 문제를 해결하기 위해, **1200개의 물리 문제**를 포함하는 새로운 벤치마크인 PhysReason을 제시합니다. PhysReason은 지식 기반 문제와 추론 기반 문제로 구성되며, 추론 기반 문제는 난이도에 따라 쉬움, 중간, 어려움 세 단계로 나뉩니다. 또한, **단계별 평가 프레임워크(PSAS)**를 통해 모델의 추론 과정을 상세히 분석하고, 물리 기반 추론 과정에서의 네 가지 주요 병목 현상을 밝힙니다. PhysReason은 LLM의 물리 기반 추론 능력을 종합적으로 평가하고, 향후 연구 방향을 제시하는 데 중요한 역할을 할 것으로 기대됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 1200개의 물리 문제를 포함하는 새로운 벤치마크 PhysReason 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 단계별 평가 프레임워크(PSAS)를 통해 모델의 추론 과정 심층 분석 및 성능 향상 방향 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 물리 기반 추론 과정의 네 가지 주요 병목 현상(물리 정리 적용, 물리 과정 이해, 계산, 물리 조건 분석)을 밝힘 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **물리 기반 추론 능력 평가를 위한 새로운 벤치마크인 PhysReason**을 제시하여, 대규모 언어 모델의 물리적 현상 이해 및 문제 해결 능력을 심층적으로 분석합니다. 이는 **자율 주행, 로보틱스 등 다양한 분야**에서 물리 기반 추론의 중요성이 증대함에 따라, 관련 연구의 발전에 중요한 기여를 할 것으로 예상됩니다. 또한, 제시된 **단계별 평가 프레임워크(PSAS)**는 모델의 추론 과정을 상세히 분석하여, 성능 향상을 위한 방향을 제시합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.12054/x1.png)

> 🔼 그림 1은 PhysReason 벤치마크의 예시 문제를 보여줍니다. 공간 제약으로 인해 주요 구성 요소만 표시되어 있습니다. 자세한 내용은 부록 D를 참조하십시오. 그림에는 문제에 대한 다이어그램, 맥락, 하위 질문, 솔루션, 단계 분석, 답변, 정리 및 난이도 등의 주요 구성 요소가 포함되어 있습니다. 이 그림은 PhysReason 데이터셋의 문제 유형과 구조를 보여주는 대표적인 예시 문제입니다. 각 문제는 다양한 물리적 개념, 수학적 원리 및 논리적 추론 능력을 요구하는 여러 하위 질문으로 구성됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: An illustration of example from our PhysReason benchmark. Due to space constraints, only key components are shown. Please refer to Appendix D for complete annotations.
> </details>





{{< table-caption >}}
| Model | Input | Knowledge | Easy | Medium | Hard | Avg. |
|---|---|---|---|---|---|---|
| **Non-O-like Models** |  |  |  |  |  |  |
| Qwen2VL-72B | Q, I | 25.40 | 27.00 | 11.4 | 8.5 | 18.07 |
| InternVL2.5-78B | Q, I | 37.90 | 20.60 | 18.14 | 7.97 | 21.15 |
| GPT-4o | Q, I | 51.12 | 31.95 | 20.75 | 12.54 | 29.09 |
| Claude-3.5-Sonnet | Q, I | 49.00 | 40.43 | 23.45 | 12.33 | 31.3 |
| Deepseek-V3-671B | Q, IC | 56.60 | 40.97 | 22.22 | 14.61 | 33.6 |
| Gemini-2.0-Flash | Q, I | 67.80 | 52.10 | 40.00 | 23.19 | 46.52 |
| Gemini-2.0-Pro | Q, I | 69.32 | 53.67 | 44.98 | 26.24 | 48.55 |
| **O-like Models** |  |  |  |  |  |  |
| o1-mini | Q, IC | 54.80 | 30.33 | 15.41 | 7.92 | 27.11 |
| QvQ-72B | Q, I | 51.17 | 37.10 | 29.83 | 22.13 | 35.06 |
| QwQ-32B | Q, IC | 64.4 | 50.07 | 38.88 | 27.45 | 45.20 |
| Gemini-2.0-T<sup>†</sup> | Q, I | 71.47 | 49.97 | 36.83 | 22.97 | 45.42 |
| GLM-Zero | Q, IC | 72.70 | 50.17 | 43.42 | 24.70 | 47.75 |
| o1 | Q, I | 72.47 | 53.37 | 49.31 | 25.32 | 50.12 |
| o3-mini-high | Q, IC | 71.10 | 63.20 | 47.02 | 31.93 | 53.31 |
| Gemini-2.0-T<sup>∗</sup> | Q, I | 76.33 | 56.87 | 51.85 | 32.61 | 54.42 |
| Deepseek-R1 | Q, IC | 85.17 | 60.77 | 47.24 | 33.23 | 56.60 |{{< /table-caption >}}

> 🔼 표 1은 PhysReason과 다른 물리 기반 추론 벤치마크 간의 비교 분석 결과를 보여줍니다.  'Knowledge' 열에서는 각 벤치마크의 문제 유형(경시대회, 대학, 대학 입시, 초중고등학교, 박사)을 나타내고, 'Question Type' 열에서는 문제 유형(개방형, 객관식)을 나타냅니다. 'Avg. T'는 문제당 평균 토큰 수, 'Avg. S'는 평균 해결 단계 수를 나타냅니다.  다양한 벤치마크의 규모, 문제 유형, 토큰 수, 해결 단계 수를 비교하여 PhysReason의 특징과 강점을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparative analysis of our PhysReason with other physics-based reasoning benchmarks. For Knowledge, COMP: Competition, COL: College, CEE: College Entrance Examination, K1-K12: Elementary and High School, PH.D: Doctor of Philosophy; For question type, OE: Open-ended, MC: Multiple-choice, Avg. T: Average Tokens; For solution type, Avg. S: Average Steps.
> </details>





### In-depth insights


#### Physics Reasoning Benchmarks
본 논문은 물리 추론 벤치마크에 대한 심도있는 논의를 제공합니다. **기존 벤치마크의 한계점을 명확히 지적**하며, 단순히 최종 답변만 평가하는 것이 아니라 **다단계 추론 과정을 상세히 평가**하는 새로운 벤치마크의 필요성을 강조합니다.  **물리적 지식과 추론 능력을 종합적으로 평가**하기 위해 계층적 난이도(지식, 쉬움, 중간, 어려움)를 도입하고, 다양한 유형의 문제를 포함시켜 모델의 견고성을 평가합니다. 또한, **다모달(텍스트 및 다이어그램) 데이터를 활용**하여 모델의 시각적 이해 능력까지 평가하며, **자동 채점 프레임워크**를 통해 효율적인 평가를 지원합니다. 이러한 벤치마크는 **LLM의 물리 추론 능력을 포괄적으로 평가**하는 데 중요한 역할을 하며, 향후 연구의 방향을 제시하는 중요한 기준이 될 것입니다.  **본 연구는 LLM의 물리 추론 능력 향상을 위한 구체적인 방향**을 제시하며, **실제 응용 분야(로보틱스, 자율주행 등)에서의 성능 향상**에 기여할 것으로 예상됩니다.

#### LLM Evaluation Metrics
LLM 평가 지표는 대규모 언어 모델의 성능을 측정하는 데 사용되는 다양한 방법들을 포함합니다.  **정확성(Accuracy)**은 모델이 질문에 대해 정확한 답을 제공하는 능력을 평가하며, **유창성(Fluency)**은 답변의 자연스러움과 문법적 정확성을 평가합니다. **일관성(Coherence)**은 답변의 논리적 흐름과 일관성을 평가하고, **적절성(Relevance)**은 답변이 질문과 얼마나 관련있는지를 평가합니다.  **효율성(Efficiency)**은 모델이 답변을 생성하는 속도와 필요한 자원을 평가합니다.  모델의 성능을 포괄적으로 평가하기 위해서는 이러한 다양한 지표들을 종합적으로 고려해야 합니다. 특히, **특정 과제에 맞는 지표 선택**이 중요하며, 새로운 평가 방법과 지표 개발을 위한 지속적인 연구가 필요합니다.  **데이터 편향(Data Bias)**과 같은 문제점들을 고려하여, 공정하고 신뢰할 수 있는 평가를 위해 노력해야 합니다.  **인간 평가자(Human Evaluator)**를 통한 주관적 평가는 객관적 지표만으로는 포착할 수 없는 측면을 보완할 수 있습니다. 따라서, 다양한 지표와 평가 방법의 장단점을 이해하고, 목적에 맞는 최적의 전략을 선택하는 것이 중요합니다.

#### PhysReason Framework
본 논문에서 제시된 PhysReason Framework는 **물리 기반 추론 능력 평가를 위한 포괄적인 평가 체계**입니다.  단순히 최종 답변의 정확성만 평가하는 기존 방식과 달리, **다단계 추론 과정 전반을 분석**하여 모델의 강점과 약점을 심층적으로 파악합니다.  **단계별 점수 및 오류 분석**을 통해 물리 법칙 적용, 물리 과정 이해, 계산 과정, 물리적 조건 분석 등 **추론 과정의 주요 병목 현상**을 식별하여 모델 개선 방향을 제시합니다. 이는 **정량적 평가와 정성적 분석을 결합**하여, 단순히 정확도만 평가하는 것에서 벗어나, 모델의 추론 전략 및 오류 패턴에 대한 통찰력을 제공하는 핵심적인 부분입니다.  따라서, PhysReason Framework는 **LLM의 물리 기반 추론 능력의 한계를 극복**하고 성능을 향상시키기 위한 중요한 이정표가 될 것입니다.

#### Reasoning Bottlenecks
본 논문에서 제시된 '추론 병목 현상'에 대한 심층적인 분석은 **물리적 현상에 대한 이해 부족**, **계산 과정의 오류**, **물리적 조건 분석의 실패**, 그리고 **물리적 법칙 적용의 어려움** 등 네 가지 주요한 제한점을 보여줍니다.  **물리적 현상에 대한 깊이 있는 이해**는 다양한 물리 법칙과 개념을 정확하게 적용하고 문제 해결 과정을 논리적으로 구성하는 데 필수적입니다.  하지만 많은 모델들이 물리적 원리를 제대로 파악하지 못해 추론 과정에서 실수를 범하는 것으로 나타났습니다.  **계산 오류** 또한 모델의 정확성을 저해하는 중요한 요인이며, 특히 복잡한 문제 해결 과정에서 더욱 두드러집니다.  모델은 **물리적 조건을 정확하게 분석**하고, 주어진 조건에 적절한 물리 법칙을 선택하여 적용하는 능력이 부족한 것으로 드러났습니다.  마지막으로 **물리 법칙을 올바르게 적용**하는 능력 또한 중요한데, 많은 모델들이 물리 법칙의 적용 범위나 조건을 제대로 이해하지 못해 실수를 범했습니다. 이러한 병목 현상들을 극복하기 위해서는 모델의 물리적 지식과 추론 능력을 향상시키는 방향으로 연구가 진행되어야 할 것입니다.

#### Future Work
본 논문은 물리 기반 추론 능력을 평가하기 위한 새로운 벤치마크인 PhysReason을 제시합니다.  **향후 연구 방향은 크게 세 가지로 나눌 수 있습니다.** 첫째, **PhysReason의 확장성을 높이는 것**입니다.  현재 벤치마크는 이상적인 조건 하의 물리 법칙 적용에 초점을 맞추고 있으므로, 실제 세계의 복잡한 상황을 반영하는 더욱 다양하고 현실적인 문제들을 추가해야 합니다.  예를 들어, 마찰력이나 공기 저항과 같은 요소들을 고려한 문제를 추가하고, 다양한 물리 시스템과 상호작용을 포함하는 문제를 설계할 수 있습니다. 둘째, **평가 프레임워크의 개선**입니다. 현재 사용하는 PSAS 프레임워크는 정확도가 높지만, 계산 비용이 상대적으로 높다는 단점이 있습니다. 따라서, 효율성을 높이면서 정확도를 유지할 수 있는 새로운 평가 방법을 연구해야 합니다.  마지막으로, **다양한 모델의 성능 비교 및 분석**을 통해 물리 기반 추론 능력 향상에 대한 통찰력을 제공해야 합니다.  특히, 모델의 성능 저하 원인을 분석하여 문제 해결 전략을 제시하고,  **대규모 언어 모델(LLM)의 물리적 지식 표현 및 추론 메커니즘**에 대한 심층적인 이해를 바탕으로 더욱 효과적인 학습 방법을 모색해야 합니다. 이를 통해, LLM의 물리 기반 추론 능력을 향상시키고, 실제 응용 분야에서의 활용 가능성을 높일 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.12054/extracted/6210222/fig/analysis_subplots_v2.png)

> 🔼 그림 2는 PhysReason 벤치마크 내 다양한 문제 범주에 걸쳐 해의 정리 수, 단계 수, 토큰 수를 분석한 결과를 보여줍니다.  SciBench, GPQA, OlympiadBench와 비교하여 어려움 정도에 따른 차이를 보여주고 있습니다.  세부적으로는, 문제의 난이도가 높아짐에 따라 해의 정리 수, 단계 수, 토큰 수가 증가하는 경향을 보여줍니다. 이는 문제의 복잡성이 증가함에 따라 더 많은 개념과 계산 단계가 필요함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Analysis of solution theorems, solution steps, and solution tokens across different problem categories, with comparisons from SciBench, GPQA, and OlympiadBench.
> </details>



![](https://arxiv.org/html/2502.12054/x2.png)

> 🔼 그림 3은 논문의 PSAS-S 프레임워크에서 얻은 단계별 평가의 예시를 보여줍니다.  PSAS-S는 각 추론 단계의 정확성을 평가하는 프레임워크이며, 모델이 정답에 도달하는 과정에서 각 단계별로 어떻게 추론하는지 자세히 분석합니다. 그림에서는 모델의 각 단계별 출력과, PSAS-S 프레임워크가 각 단계를 어떻게 평가하고 오류를 감지하는지 보여줍니다.  모델의 추론 과정 중 오류가 발생한 지점을 정확히 찾아내 오류 유형을 분류하고 분석하는 과정을 시각적으로 보여줌으로써, 모델의 추론 능력을 보다 정밀하게 평가할 수 있음을 보여주는 예시입니다. 
> <details>
> <summary>read the caption</summary>
> Figure 3: Step-level evaluation example obtained from PSAS-S framework.
> </details>



![](https://arxiv.org/html/2502.12054/extracted/6210222/fig/error_types_count_selected.png)

> 🔼 그림 4는 PhysReason-mini 벤치마크에서 PSAS-S 프레임워크를 사용하여 모델의 오류 분포를 보여줍니다. Gemini-T-1206과 Gemini-T-0121은 각각 Gemini-2.0-Flash-Thinking-1206과 Gemini-2.0-Flash-Thinking-0121 모델을 나타냅니다.  각 모델의 오류 유형별 비율을 보여주는 막대 그래프로,  물리적 정리 적용 오류, 물리적 과정 이해 오류, 계산 과정 오류, 물리적 조건 분석 오류 등 네 가지 주요 오류 유형을 보여줍니다. 이는 각 모델의 강점과 약점을 파악하고, 물리 기반 추론 능력 향상을 위한 방향을 제시하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Error statistics with PSAS-S framwork in PhysReason-mini, where Gemini-T-1206 and Gemini-T-0121 denote Gemini-2.0-Flash-Thinking-1206 and Gemini-2.0-Flash-Thinking-0121.
> </details>



![](https://arxiv.org/html/2502.12054/extracted/6210222/fig/model_performance_analysis_v2.png)

> 🔼 그림 5는 PhysReason-mini 데이터셋의 어려운 문제들에 대해 PSAS-S 프레임워크를 사용한 모델 성능을 보여줍니다.  각 모델의 누적 점수를 막대 그래프 형태로 나타내어, 어려운 문제에서 모델별 성능 차이를 시각적으로 비교 분석할 수 있도록 합니다.  각 막대는 특정 모델의 누적 점수를 나타내며, 서로 다른 모델 간의 상대적 성능을 쉽게 파악할 수 있도록 합니다. 이 그래프는 단순히 최종 정답의 정확도가 아닌, 문제 해결 과정의 단계별 정확성까지 고려하여 모델의 성능을 평가한 결과를 보여주는 것이 특징입니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Performance with PSAS-S framework in the hard problems from PhysReason-mini.
> </details>



![](https://arxiv.org/html/2502.12054/x3.png)

> 🔼 그림 6은 논문에서 설명하는 데이터 수집 과정을 보여주는 그림입니다. 데이터 수집은 크게 다섯 단계로 이루어집니다. 1단계는 다양한 출처(국제 물리 올림피아드, 중국 가오카오, 인도 공동 입학 시험, 기타 온라인 자료 등)에서 물리 문제를 수집하는 단계입니다. 2단계는 수집된 데이터를 표준화하는 단계로, MinerU 프레임워크를 사용하여 문제의 구조화된 정보를 추출하고, 중복 제거, 형식 및 용어 표준화 등의 과정을 거칩니다. 3단계는 번역 단계로, 다국어 문제를 영어로 통일합니다. 4단계는 검색 방지 단계로, 5분 안에 구글 검색으로 답을 찾을 수 있는 문제를 제거합니다. 5단계는 난이도 분류 단계로, 문제의 난이도를 지식 기반, 쉬움, 중간, 어려움 네 가지로 분류합니다. 이러한 과정을 거쳐 최종적으로 PhysReason 벤치마크에 사용될 1200개의 물리 문제를 확보하게 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Illustration of the data collection pipeline.
> </details>



![](https://arxiv.org/html/2502.12054/x4.png)

> 🔼 그림 7은 본 논문의 PhysReason 벤치마크에 포함된 지식 기반 문제의 예시를 보여줍니다. 그림에는 문제에 대한 다이어그램, 맥락 정보, 하위 질문, 솔루션, 단계별 분석, 답변, 정리 및 난이도 등이 포함되어 있습니다. 이 예시는 자기 유도에 대한 패러데이 법칙, 옴의 법칙, 줄의 법칙 등의 기본적인 물리학 개념을 이해하고 있는지 평가하기 위한 것입니다. 문제는 간단한 계산과 공식 적용을 통해 풀 수 있으며, 학생들이 물리학적 원리를 이해하고 있는지 확인하는 데 중점을 둡니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: A knowledge example in our benchmark.
> </details>



![](https://arxiv.org/html/2502.12054/x5.png)

> 🔼 그림 8은 논문의 벤치마크에서 쉬운 예시 문제를 보여줍니다. 그림에는 질문과 함께 문제 상황을 설명하는 다이어그램, 문제에 대한 풀이 과정, 각 단계별 분석, 사용된 물리 법칙 및 정리, 그리고 최종 답변이 포함되어 있습니다. 이 문제는 에너지 보존 법칙, 뉴턴의 운동 제2법칙, 운동량 보존 법칙 등의 기본적인 물리 개념과 공식을 적용하여 풀 수 있도록 설계되었습니다.  문제 해결 과정은 비교적 간단하고 단계별로 명확하게 제시되어 있어, 큰 어려움 없이 문제를 이해하고 풀이 과정을 따라갈 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: An easy example in our benchmark.
> </details>



![](https://arxiv.org/html/2502.12054/x6.png)

> 🔼 그림 9는 PhysReason 벤치마크에 포함된 중간 난이도의 문제 예시입니다. 그림에는 열전도성이 좋은 원통형 용기 안에 피스톤이 있는 이상기체가 들어 있습니다. 문제는 중력 가속도, 대기압 등을 고려하여, 용기의 방향을 바꾸거나 가열하는 등의 상황 변화에 따른 기체의 부피와 온도 변화를 계산하는 것입니다. 이 문제는 보일의 법칙과 이상기체 상태 방정식을 적용해야 하며, 여러 단계의 계산과 물리적 개념에 대한 이해가 필요합니다. 따라서, 단순한 공식 적용을 넘어, 다양한 물리적 원리를 통합적으로 이해하고 적용하는 능력을 평가하는 데 적합합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: A medium example in our benchmark.
> </details>



![](https://arxiv.org/html/2502.12054/x7.png)

> 🔼 그림 10은 PhysReason 벤치마크에 포함된 고난도 문제의 예시를 보여줍니다. 그림에는 경사면, 수평면, 원형 파이프, 반원형 트랙으로 이루어진 복잡한 트랙과, 트랙 위를 미끄러지는 슬라이더, 트랙과 충돌하는 작은 공, 그리고 삼각형 프리즘으로 구성된 장치가 포함되어 있습니다. 이 문제는 에너지 보존, 운동량 보존, 뉴턴의 운동 법칙 등 다양한 물리적 개념과 원리를 종합적으로 적용해야 해결할 수 있는 다단계 추론 과정을 요구합니다.  슬라이더의 초기 높이, 공의 최종 위치 등을 묻는 여러 하위 질문들이 제시되어 있으며, 각 하위 질문에 대한 답을 구하기 위해서는 여러 단계의 물리적 계산과 논리적 추론이 필요합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: A hard example in our benchmark.
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