---
title: "Text2World: Benchmarking Large Language Models for Symbolic World Model Generation"
summary: "TEXT2WORLD 벤치마크: LLM의 상징적 세계 모델 생성 능력 평가 및 향상 전략 제시!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Hong Kong University of Science and Technology",]
showSummary: true
date: 2025-02-18
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.13092 {{< /keyword >}}
{{< keyword icon="writer" >}} Mengkang Hu et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-19 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.13092" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.13092" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

최근 대규모 언어 모델(LLM)을 이용한 상징적 세계 모델 생성에 대한 관심이 높아지고 있지만, 기존 연구는 **평가의 임의성, 간접 지표에 대한 의존성, 제한된 도메인 범위** 등의 문제점을 안고 있었습니다. 이는 LLM의 세계 모델링 능력을 정확하게 평가하고, 개선 방향을 제시하는 데 어려움을 초래했습니다.

본 논문에서는 PDDL(Planning Domain Definition Language)을 기반으로 한 새로운 벤치마크인 TEXT2WORLD를 제시합니다. TEXT2WORLD는 **다양한 도메인(수백 개)과 실행 기반의 다중 평가 지표**를 사용하여, 기존 연구의 한계를 극복하고 LLM의 세계 모델링 능력을 더욱 견고하게 평가할 수 있도록 설계되었습니다.  실험 결과, 강화 학습 기반의 대규모 추론 모델이 우수한 성능을 보였지만, 여전히 세계 모델링 능력에는 한계가 있음을 확인했습니다.  본 논문에서는 이러한 결과를 바탕으로 **테스트 시간 확장, 에이전트 훈련 등 LLM의 세계 모델링 능력을 향상시키기 위한 몇 가지 유망한 전략**들을 제시합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} TEXT2WORLD 벤치마크는 기존 연구의 한계를 극복한 **다양한 도메인과 엄격한 평가 기준**을 제공합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 강화 학습으로 훈련된 대규모 추론 모델이 **세계 모델 생성에서 우수한 성능**을 보였습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 테스트 시간 확장, 에이전트 훈련 등 **LLM의 세계 모델링 성능 향상을 위한 다양한 전략**이 제시되었습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대규모 언어 모델(LLM)**을 사용한 상징적 세계 모델 생성 분야에 중요한 기여를 합니다.  **TEXT2WORLD 벤치마크**는 기존 연구의 한계를 극복하고, LLM의 세계 모델링 능력을 더욱 정확하게 평가할 수 있는 견고한 기반을 제공합니다. 이는 **LLM의 한계점을 명확히 밝히고 향후 연구 방향을 제시**하여, 인공지능 분야의 발전에 크게 기여할 것입니다. 특히, **다양한 평가 지표와 광범위한 도메인을 포함**하여, LLM의 세계 모델링 성능을 보다 포괄적으로 평가할 수 있는 토대를 마련합니다.  **제시된 개선 전략**들은 LLM의 세계 모델링 능력 향상에 도움을 줄 것이며, **향후 연구를 위한 중요한 방향**을 제시할 것입니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.13092/x2.png)

> 🔼 그림 1은 TEXT2WORLD의 전반적인 구조를 보여줍니다. 자연어 설명을 입력으로 받아, 자동 오류 수정 및 생성 과정을 거쳐 PDDL(Planning Domain Definition Language) 형식의 세계 모델을 생성합니다. 생성된 모델은 실행 가능성, 구조적 유사성, 그리고 구성 요소별 F1 점수 등 다양한 기준으로 평가됩니다.  전체 과정은 사용자 프롬프트에서 시작하여, 세계 모델 생성, 다기준 평가, 오류 피드백으로 이어지는 반복적인 루프로 구성됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  Overview of Text2World.
> </details>





{{< table-caption >}}
| Statistic | Number |
|---|---| 
| _Domain Count_ |  |
| Domain | 103 |
| - Train | 2 |
| - Test | 101 |
| _Token Count_ |  |
| Description | 851.6 ± 515.2 |
| - Min/Max | [159, 2814] |
| Domain | 1187.2 ± 1212.1 |
| - Min/Max | [85, 7514] |
| _Line Count_ |  |
| Domain | 75.4 ± 62.9 |
| - Min/Max | [9, 394] |
| _Component Count_ |  |
| Actions | 4.5 ± 2.8 |
| - Min/Max | [1, 16] |
| Predicates | 8.1 ± 4.8 |
| - Min/Max | [1, 25] |
| Types | 1.1 ± 1.3 |
| - Min/Max | [1, 8] |{{< /table-caption >}}

> 🔼 표 1은 TEXT2WORLD 벤치마크에서 다양한 대규모 언어 모델(LLM)의 성능을 비교한 결과를 보여줍니다.  EC0는 수정 없이 제로샷으로 평가한 결과이고, EC3는 최대 3회의 수정을 허용한 후 평가한 결과입니다.  표에는 각 모델의 실행 가능성(EXEC.), 구조적 유사도(SIM.), 그리고 예측된 PDDL의 구성요소별 F1 점수(F1PRED, F1PARAM, F1PRECOND, F1EFF)가 포함되어 있습니다. 이를 통해 모델의 세계 모델 생성 능력을 다각적으로 평가합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Performance comparison of different LLMs on Text2World. ECk denotes the setting where models are allowed k correction attempts (EC0: zero-shot without correction, EC3: with 3 correction attempts).
> </details>





### In-depth insights


#### LLM World Modeling
LLM(대규모 언어 모델) 월드 모델링은 **텍스트 설명으로부터 상징적 월드 모델을 생성하는 LLM의 능력**을 평가하는 흥미로운 분야입니다.  **기존 연구는 몇 가지 제한점**을 가지고 있었는데, 제한된 도메인 범위, 평가의 무작위성, 간접적인 지표 사용 등이 포함됩니다.  따라서 **더욱 강력하고 견고한 평가 기준**이 필요합니다.  **텍스트 기반의 월드 모델 생성 평가 벤치마크**를 개발하고, 다양한 LLM을 평가하여 LLM의 강점과 약점을 분석하고, 향후 연구 방향을 제시하는 것이 중요합니다.  **강화 학습을 통해 훈련된 대규모 추론 모델**은 월드 모델링 작업에서 우수한 성능을 보이는 경향이 있습니다.  **테스트 시간 확장, 에이전트 훈련, 파인튜닝** 등의 전략을 통해 LLM의 월드 모델링 능력을 향상시킬 수 있는 가능성을 확인할 수 있습니다.  **데이터 오염 분석**을 통해 벤치마크의 신뢰성을 확보하고, **다중 기준, 실행 기반 평가 지표**를 사용하여 객관적인 평가를 수행하는 것이 중요합니다.  **향후 연구**에서는 더욱 다양한 도메인과 더욱 발전된 LLM을 대상으로 연구를 확장하여 LLM 월드 모델링 분야의 발전에 기여할 수 있을 것입니다.

#### TEXT2WORLD Benchmark
TEXT2WORLD 벤치마크는 **대규모 언어 모델(LLM)의 상징적 세계 모델 생성 능력을 평가하기 위한 새로운 벤치마크**입니다. 기존 연구의 한계점인 제한된 도메인 범위, 평가의 무작위성, 간접적인 평가 지표 사용 등을 해결하기 위해 **PDDL(Planning Domain Definition Language) 기반의 수백 개의 다양한 도메인과 실행 기반의 다기준 평가 지표**를 활용합니다.  **LLM의 세계 모델링 성능을 종합적으로 평가**하고, 강화 학습 기반의 대규모 추론 모델의 우수성과 더불어, **테스트 시간 확장, 에이전트 훈련 등의 향상 전략**의 효과를 제시합니다.  **다양한 LLM의 성능 비교**를 통해 세계 모델 생성의 어려움과 향후 연구 방향을 제시하며, **향후 LLM 기반 세계 모델 연구의 초석**을 마련합니다.

#### Multi-criteria Evaluation
논문에서 "다기준 평가"라는 제목의 섹션은 **모델의 성능을 다각적으로 평가하기 위한 척도들을 제시**하는 데 초점을 맞추고 있을 것입니다. 단순히 하나의 지표만으로는 모델의 강점과 약점을 제대로 파악하기 어렵기 때문에, **정확도, 실행 가능성, 구조적 유사성, 구성 요소별 정확도** 등 여러 기준을 종합적으로 고려하여 평가하는 것이 중요합니다. 이를 통해 **모델의 전반적인 성능뿐만 아니라, 특정 영역에서의 강점과 약점을 명확히 드러낼 수** 있습니다.  본 논문은 다기준 평가를 통해 **기존 연구의 한계점들을 극복**하고, 더욱 **객관적이고 포괄적인 평가 결과**를 도출하는 데 기여할 것으로 예상됩니다. 특히, **간접적인 평가 지표에 대한 의존성을 줄이고, 실행 기반의 직접적인 평가 방식을 도입**하여 평가의 신뢰성을 높이는 데 기여할 것입니다. 또한, **다양한 도메인에 걸쳐 모델의 일반화 성능을 평가**하는 데에도 초점을 맞출 것입니다.

#### Benchmark Limitations
본 논문에서 제시된 벤치마크의 주요 한계점은 다음과 같습니다. 첫째, **기존 연구들의 벤치마크는 적용되는 도메인의 범위가 제한적**이었습니다. 즉, 다양한 유형의 문제를 포괄하지 못하여, 제시된 모델의 일반화 성능을 제대로 평가하기 어려웠습니다. 둘째, **평가 과정에서의 무작위성**이 존재했습니다. 기존 연구들은 LLM 기반의 평가 방식을 사용하였는데, 이는 평가 결과에 추가적인 오차를 발생시키는 요인이 될 수 있습니다. 셋째, **간접적인 측정 방식**에 의존하는 경향이 있었습니다. 종단 간 성공률에만 초점을 맞추어 실제로 어떤 부분에서 실패가 발생하는지 자세히 파악하기 어려웠습니다. 따라서, 본 논문에서는 이러한 한계점을 극복하기 위해 다양한 도메인과 엄격한 평가 기준을 갖춘 새로운 벤치마크를 제시합니다. 이를 통해 더욱 견고하고 일반화된 성능 평가가 가능해질 것으로 기대됩니다.

#### Future Research
본 논문은 대규모 언어 모델(LLM)을 활용한 심볼릭 월드 모델 생성에 대한 새로운 벤치마크인 TEXT2WORLD를 제시합니다. **미래 연구는 TEXT2WORLD의 한계를 극복하고 LLM의 월드 모델링 성능을 향상시키는 데 집중해야 합니다.**  특히, **데이터셋 확장 및 다양화**, **LLM의 추론 능력 향상**, **다양한 평가 지표 개발** 등이 중요한 연구 방향이 될 것입니다.  **다양한 도메인에 대한 데이터를 추가적으로 확보하고 합성 데이터를 생성하는 연구**도 필요합니다.  더불어, **실제 세계에서의 적용 가능성을 높이기 위한 연구**도 중요한데, 이를 위해서는 보다 복잡하고 현실적인 상황을 반영한 벤치마크 개발이 필수적입니다. 또한, **LLM의 추론 과정에 대한 깊이 있는 분석**을 통해 한계점을 파악하고 개선 방안을 모색하는 것이 중요하며, **다양한 외부 지식을 활용하여 LLM의 월드 모델링 성능 향상을 위한 연구**가 필요합니다.  마지막으로, **새로운 평가 지표 개발 및 기존 지표의 한계점 개선**을 통해 더욱 견고하고 신뢰할 수 있는 평가 체계를 구축하는 연구가 중요합니다.  이러한 미래 연구를 통해 LLM 기반 월드 모델링 기술의 실용화 및 발전에 크게 기여할 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.13092/x4.png)

> 🔼 그림 2는 TEXT2WORLD 데이터셋 구축 과정을 보여줍니다. 왼쪽은 데이터셋 구축의 세 단계를 시각적으로 나타냅니다. (a) 데이터 수집: 다양한 공개 저장소와 계획 대회에서 PDDL 파일을 수집합니다. (b) 데이터 필터링 및 수동 선택: 수집된 데이터의 품질을 보장하기 위해, 구문 검증, 유사 중복 제거, 복잡도 제어, 토큰 길이 필터링 및 수동 선택과 같은 여러 단계의 필터링 과정을 거칩니다. (c) 데이터 주석 및 품질 보증: 전문가의 수동 주석을 통해 고품질의 자연어 설명을 생성하고, 여러 검토 단계를 거쳐 데이터 품질을 보장합니다. 오른쪽은 TEXT2WORLD의 주요 통계를 보여줍니다. 토큰 수는 GPT-2 토크나이저를 사용하여 계산되었으며, Chen et al.(2024b)의 스타일을 참고했습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Left: Dataset construction process including: (a) Data Acquisition (§3.1); (b) Data Filtering and Manual Selection (§3.2); (c) Data Annotation and Quality Assurance (§3.3 and §3.4). Right: Key statistics of Text2World. Tokens are counted by GPT-2 Radford et al. (2019) tokenizer. The style is referenced from Chen et al. (2024b).
> </details>



![](https://arxiv.org/html/2502.13092/x7.png)

> 🔼 그림 3은 TEXT2WORLD와 기존 연구에서 제시된 방법들의 n-gram 오염 비율을 비교 분석한 결과를 보여줍니다.  n-gram 오염은 모델이 훈련 데이터를 단순히 암기하는 현상을 나타내는 지표로, 오염률이 낮을수록 모델의 일반화 능력이 높다고 해석할 수 있습니다.  이 그림을 통해 TEXT2WORLD가 기존 연구들에 비해 훈련 데이터 오염이 현저히 낮음을 확인할 수 있으며, 이는 TEXT2WORLD의 평가의 신뢰성을 높여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3:  n-gram contamination rate of Text2World and prior works.
> </details>



![](https://arxiv.org/html/2502.13092/x8.png)

> 🔼 그림 4는 TEXT2WORLD 데이터셋의 특징을 보여주는 두 개의 그래프로 구성되어 있습니다. 위쪽 그래프는 TEXT2WORLD 데이터셋에 포함된 PDDL 도메인들이 어떤 종류의 요구사항(requirements)들을 얼마나 자주 포함하고 있는지를 보여주는 막대 그래프입니다. 예를 들어, ':strips' 나 ':typing' 과 같은 요구사항들이 다른 요구사항들보다 훨씬 더 자주 나타남을 알 수 있습니다. 아래쪽 그래프는 TEXT2WORLD 데이터셋에 있는 다양한 개념들을 단어 구름(word cloud) 형태로 시각화한 것입니다. 단어의 크기는 해당 단어가 데이터셋에서 얼마나 자주 등장하는지를 나타냅니다. 이를 통해, TEXT2WORLD 데이터셋에서 어떤 종류의 계획 문제(planning problem)들이 주로 다루어지는지를 한눈에 파악할 수 있습니다.  전반적으로, 이 그림은 TEXT2WORLD 데이터셋의 구성과 특징을 요약하여 보여주는 유용한 시각자료입니다.
> <details>
> <summary>read the caption</summary>
> Figure 4:  Top: The frequency of requirements distribution. Bottom: Word cloud of concepts in Text2World.
> </details>



![](https://arxiv.org/html/2502.13092/x9.png)

> 🔼 그림 5는 오류 수정 과정에서의 구문 오류와 의미 오류의 분포를 보여줍니다. 왼쪽 그림은 구문 오류 유형의 분포를 보여주고 있으며, 오류 수정 단계가 진행됨에 따라 특정 구문 오류(예: 괄호 불일치, 정의되지 않은 상수)의 비율이 감소하는 것을 보여줍니다. 반면, 다른 구문 오류(예: 정의되지 않은 도메인 이름, 정의되지 않은 유형)는 지속적으로 나타나는 것을 알 수 있습니다. 오른쪽 그림은 의미 오류 유형의 분포를 보여줍니다. 의미 오류는 기술서에 대한 직접적인 위반, 모델링의 불완전성, 불필요한 명세, 표면적 차이 등 네 가지 유형으로 분류됩니다. 이 그림은 모델이 생성한 심볼릭 월드 모델의 품질을 평가하는 데 사용된 다양한 오류 유형과 그 분포를 보여주어, 모델 성능 향상을 위한 추가적인 연구 방향을 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Left: The distribution of syntax error types during the progression of correction. Right: The distribution of semantic error types.
> </details>



![](https://arxiv.org/html/2502.13092/x10.png)

> 🔼 그림 6은 서로 다른 테스트 시간 컴퓨팅 예산 하에서 GPT-4o-mini(왼쪽)와 DeepSeek-v3(오른쪽)의 성능을 보여줍니다. 이 그래프는 컴퓨팅 예산이 증가함에 따라 두 모델 모두 일관되게 성능이 향상됨을 보여줍니다.  x축은 수정 시도 횟수를 나타내고, y축은 여러 지표(Exec, F1 pred, F1 param, F1 precond, F1 eff)에 대한 평균값을 백분율로 나타냅니다. 각 모델의 성능 향상 정도는 다르지만, 두 모델 모두 컴퓨팅 예산 증가에 따라 꾸준히 향상되는 경향을 보입니다. 이는 테스트 시간 확장 전략이 모델의 세계 모델링 능력을 향상시키는 데 효과적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6:  The performance of gpt-4o-mini (left) and deepseek-v3 (right) under different test-time compute budgets, showing consistent improvement with increased compute.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model Family | Version | Exec. ↑ EC<sub>0</sub> | Exec. ↑ EC<sub>3</sub> | Sim. ↑ EC<sub>0</sub> | Sim. ↑ EC<sub>3</sub> | F1<sub>pred</sub> ↑ EC<sub>0</sub> | F1<sub>pred</sub> ↑ EC<sub>3</sub> | F1<sub>param</sub> ↑ EC<sub>0</sub> | F1<sub>param</sub> ↑ EC<sub>3</sub> | F1<sub>precond</sub> ↑ EC<sub>0</sub> | F1<sub>precond</sub> ↑ EC<sub>3</sub> | F1<sub>eff</sub> ↑ EC<sub>0</sub> | F1<sub>eff</sub> ↑ EC<sub>3</sub> |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---| 
| **OpenAI-o1** | o1-mini | 49.5 | 69.3 | 82.5 | 82.2 | 48.4 | 66.3 | 36.4 | 49.7 | 28.9 | 38.0 | 31.7 | 42.1 |
| **OpenAI-o3** | o3-mini | 54.5 | 84.2 | 83.0 | 81.9 | 53.9 | 81.1 | 43.7 | 63.0 | 36.8 | 50.4 | 39.4 | 53.8 |
| **GPT-4** | gpt-4o | 60.4 | 75.2 | 84.5 | 84.1 | 59.6 | 72.1 | 56.5 | 68.1 | 49.3 | 56.4 | 47.8 | 56.7 |
|  | gpt-4o-mini | 48.5 | 72.3 | 82.6 | 82.2 | 48.1 | 70.1 | 47.1 | 67.3 | 34.9 | 47.5 | 38.2 | 52.7 |
| **GPT-3.5** | turbo-0125 | 41.6 | 56.4 | 81.9 | 81.6 | 41.2 | 55.8 | 39.6 | 53.8 | 30.2 | 39.2 | 27.5 | 37.7 |
| **Claude-3.5** | sonnet | 45.5 | 64.4 | 73.2 | 66.8 | 45.5 | 62.5 | 41.5 | 48.8 | 37.4 | 44.0 | 38.4 | 45.0 |
| **LLaMA-2** | 7b-instruct | 0.0 | 0.0 | 45.5 | 33.9 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 |
|  | 70b-instruct | 0.0 | 0.0 | 48.7 | 48.6 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 |
| **LLaMA-3.1** | 8b-instruct | 0.0 | 0.0 | 74.3 | 74.9 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 |
|  | 70b-instruct | 0.0 | 0.0 | 83.6 | 79.2 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 |
| **DeepSeek** | deepseek-v3 | 56.4 | 79.2 | **84.7** | **84.2** | 55.9 | 75.6 | 53.7 | 74.4 | 45.1 | 58.6 | 46.7 | 61.5 |
|  | deepseek-r1 | **72.3** | **89.1** | 84.3 | 84.0 | **71.7** | **86.7** | **64.0** | **76.3** | **57.6** | **65.0** | **58.8** | **67.3** |
| **CodeLLaMA** | 7b-instruct | 17.8 | 22.8 | 60.2 | 57.6 | 17.8 | 18.8 | 17.2 | 18.2 | 11.3 | 12.2 | 10.7 | 11.1 |
|  | 13b-instruct | 7.9 | 8.9 | 57.6 | 55.0 | 7.9 | 8.9 | 7.9 | 8.9 | 4.9 | 5.9 | 5.2 | 6.1 |
|  | 34b-instruct | 7.9 | 8.9 | 34.2 | 7.6 | 7.9 | 8.6 | 7.9 | 8.4 | 5.0 | 5.0 | 5.4 | 5.4 |
|  | 70b-instruct | 16.8 | 16.8 | 54.0 | 14.0 | 16.4 | 16.4 | 16.8 | 16.8 | 10.7 | 10.7 | 14.1 | 14.1 |{{< /table-caption >}}
> 🔼 표 2는 다양한 설정에서 모델의 실험 결과를 보여줍니다. 구체적으로, 세 가지 설정 – (1) 맥락 학습 (§6.2), (2) 미세 조정 및 LoRA를 사용한 미세 조정 Hu et al. (2021) (§6.3), (3) 에이전트 훈련 (§6.4) – 에서 모델 성능을 비교 분석합니다. 각 설정에 따른 모델의 실행 가능성, 구조적 유사성, 그리고 구성 요소별 F1 점수를 제시하여, 각 설정이 모델 성능에 미치는 영향을 종합적으로 평가합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: The experimental results of models under different settings: (1) In-context learning (§6.2); (2) Fine-tuning, and fine-tuning with LoRA Hu et al. (2021) (§6.3); (3) Agent training (§6.4).
> </details>

{{< table-caption >}}
| Model Family | Exec. EC<sub>0</sub> | Exec. EC<sub>3</sub> | Sim. EC<sub>0</sub> | Sim. EC<sub>3</sub> | F1<sub>pred</sub> EC<sub>0</sub> | F1<sub>pred</sub> EC<sub>3</sub> | F1<sub>param</sub> EC<sub>0</sub> | F1<sub>param</sub> EC<sub>3</sub> | F1<sub>precond</sub> EC<sub>0</sub> | F1<sub>precond</sub> EC<sub>3</sub> | F1<sub>eff</sub> EC<sub>0</sub> | F1<sub>eff</sub> EC<sub>3</sub> |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| *In-Context Learning* |  |  |  |  |  |  |  |  |  |  |  |  |
| Claude-3.5-sonnet | 45.5 | 64.4 | 73.2 | 66.8 | 45.5 | 62.5 | 41.5 | 48.8 | 37.4 | 44.0 | 38.4 | 45.0 |
| w. 2-shot | 78.2<sub>+32.7</sub> | 88.1<sub>+23.7</sub> | 83.9<sub>+10.7</sub> | 82.3<sub>+15.5</sub> | 77.0<sub>+31.5</sub> | 86.1<sub>+23.6</sub> | 75.2<sub>+33.7</sub> | 82.1<sub>+33.3</sub> | 65.6<sub>+28.2</sub> | 71.3<sub>+27.3</sub> | 67.2<sub>+28.8</sub> | 73.4<sub>+28.4</sub> |
| Deepseek-r1 | 72.3 | 89.1 | 84.3 | 84.0 | 71.7 | 86.7 | 64.0 | 76.3 | 57.6 | 65.0 | 58.8 | 67.3 |
| w. 2-shot | 69.3<sub>-3.0</sub> | 90.1<sub>+1.0</sub> | 83.8<sub>-0.5</sub> | 83.5<sub>-0.5</sub> | 68.4<sub>-3.3</sub> | 87.7<sub>+1.0</sub> | 64.6<sub>+0.6</sub> | 79.1<sub>+2.8</sub> | 56.0<sub>-1.6</sub> | 66.9<sub>+1.9</sub> | 57.6<sub>-1.2</sub> | 68.9<sub>+1.6</sub> |
| GPT-4o-mini | 48.5 | 72.3 | 82.6 | 82.2 | 48.1 | 70.1 | 47.1 | 67.3 | 34.9 | 47.5 | 38.2 | 52.7 |
| w. 2-shot | 40.6<sub>-7.9</sub> | 69.3<sub>-3</sub> | 82.9<sub>+0.3</sub> | 82.4<sub>+0.2</sub> | 40.3<sub>-7.8</sub> | 67.2<sub>-2.9</sub> | 40.1<sub>-7</sub> | 67.0<sub>-0.3</sub> | 31.6<sub>-3.3</sub> | 49.3<sub>+1.8</sub> | 32.5<sub>-5.7</sub> | 54.8<sub>+2.1</sub> |
| *Fine-tuning (FT)* |  |  |  |  |  |  |  |  |  |  |  |  |
| LLaMA-3.1-8B | 0.0 | 0.0 | 74.3 | 74.9 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 |
| w. FT | 52.5<sub>+52.5</sub> | 68.3<sub>+68.3</sub> | 80.8<sub>+6.5</sub> | 80.6<sub>+5.7</sub> | 51.4<sub>+51.4</sub> | 65.4<sub>+65.4</sub> | 48.5<sub>+48.5</sub> | 60.6<sub>+60.6</sub> | 31.5<sub>+31.5</sub> | 38.1<sub>+38.1</sub> | 32.4<sub>+32.4</sub> | 40.2<sub>+40.2</sub> |
| LLaMA-3.1-70B | 0.0 | 0.0 | 83.6 | 79.2 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 |
| w. LoRA | 48.5<sub>+48.5</sub> | 70.3<sub>+70.3</sub> | 83.8<sub>+0.2</sub> | 82.3<sub>+3.1</sub> | 47.9<sub>+47.9</sub> | 68.5<sub>+68.5</sub> | 48.5<sub>+48.5</sub> | 66.4<sub>+66.4</sub> | 39.9<sub>+39.9</sub> | 52.8<sub>+52.8</sub> | 40.6<sub>+40.6</sub> | 52.1<sub>+52.1</sub> |
| *Agent Training (AT)* |  |  |  |  |  |  |  |  |  |  |  |  |
| LLaMA-2-70B | 0.0 | 0.0 | 48.7 | 48.6 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 | 0.0 |
| w. AT | 7.9<sub>+7.9</sub> | 9.9<sub>+9.9</sub> | 65.6<sub>+16.9</sub> | 47.9<sub>-0.7</sub> | 7.3<sub>+7.3</sub> | 8.8<sub>+8.8</sub> | 7.3<sub>+7.3</sub> | 9.1<sub>+9.1</sub> | 6.1<sub>+6.1</sub> | 6.5<sub>+6.5</sub> | 5.7<sub>+5.7</sub> | 6.1<sub>+6.1</sub> |{{< /table-caption >}}
> 🔼 이 표는 TEXT2WORLD 벤치마크에서 퓨샷 설정 하에 Claude-3.5-sonnet 모델이 생성한 PDDL 도메인에서 발생한 오류 유형의 분포를 보여줍니다.  모델이 정확하게 PDDL 도메인을 생성한 비율과 구문 오류 및 의미 오류가 발생한 비율을 보여주는 세부 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Distribution of error types of claude-3.5-sonnect on Text2World under few-shot setting.
> </details>

{{< table-caption >}}
| Proportion (%) | Number |
|---|---|---| 
| **Correct** | 23.76 | 24 |
| **Syntax Error** | 11.88 | 12 |
| **Semantic Error** | 64.36 | 65 |
| **All** | 100.00 | 101 |{{< /table-caption >}}
> 🔼 표 4는 PDDL 생성 과정에서 발생한 구문 오류의 분포를 보여줍니다. 총 66개의 샘플을 분석하였으며, 각 작업에는 1개에서 4개의 샘플이 포함될 수 있습니다. 각 오류 유형에 대한 설명과 발생 비율이 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Distribution of Syntax Errors in PDDL Generation (Total Samples: 66, a task may have 1 to 4 samples.)
> </details>

{{< table-caption >}}
| Syntax Error | Explanation | Proportion (%) |
|---|---|---|
| UndefinedDomainName | Missing mandatory `(define (domain ...))` declaration in PDDL header | 33.33 |
| IncorrectParentheses | Invalid empty/mismatched parentheses | 3.03 |
| UndefinedConstant | Reference to undeclared constants in predicates or actions | 13.64 |
| MissingRequirements | Absence of required PDDL extension declarations (e.g., `:action-costs`) | 22.73 |
| UndefinedType | Undeclared parent type in hierarchical type definitions | 18.18 |
| UnsupportedFeature | Use of parser-incompatible language features (e.g., `either` types) | 3.03 |
| TypeMismatch | Parameter type conflict with declared type constraints | 1.52 |
| UndefinedVariable | Undeclared variables in action preconditions/effects | 1.52 |
| DuplicateDefinition | Multiple declarations of identical domain elements | 3.03 |{{< /table-caption >}}
> 🔼 표 5는 총 91개의 PDDL 생성 작업에 대한 의미론적 오류의 분포를 보여줍니다. 하나의 작업에 여러 개의 의미론적 오류가 있을 수 있습니다. 표는 각 의미론적 오류 유형의 비율과 해당 설명을 제공합니다.  의미론적 오류 유형에는 설명 불이행, 잘못된술어, 잘못된 동작, 모델 미완성, 잘못된 전제조건, 잘못된 효과, 중복 사양, 중복 전제조건, 중복 효과, 표면적 차이 등이 포함됩니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Distribution of Semantic Errors in PDDL Generation (Total Samples: 91, a task may have multiple semantic errors.)
> </details>

{{< table-caption >}}
| Semantic Error | Explanation | Proportion (%) |
|---|---|---|
| **DisobeyDescription** | Direct violation of semantic requirements explicitly stated in the task description. | **14.29** |
| IncorrectPredicate | Incorrect or missing the declaration of predicates. | 6.59 |
| IncorrectAction | Incorrect or missing the declaration of actions. | 7.69 |
| **IncompleteModeling** | Incomplete world modeling compared to basic requirements. | **58.24** |
| IncorrectPrecondition | The precondition of the action is deficient or incorrect. | 29.67 |
| IncorrectEffect | The effect of the action is deficient or incorrect. | 28.57 |
| **RedundantSpecifications** | Predicted domain includes superfluous preconditions or effects. | **17.58** |
| RedundantPrecondition | Predicted domain includes superfluous preconditions. | 10.99 |
| RedundantEffect | Predicted domain includes superfluous effects. | 6.59 |
| **SurfaceDivergence** | Surface variations preserving semantic equivalence with ground truth. | **9.89** |{{< /table-caption >}}
> 🔼 표 6은 구체적인 도메인 설명을 사용하여 TEXT2WORLD에 대한 다양한 LLM의 성능 비교를 보여줍니다. ECk는 모델이 k번의 수정 시도를 허용하는 설정을 나타냅니다. (EC0: 수정 없이 제로샷, EC3: 3번의 수정 시도).  표에는 각 모델의 실행 가능성(EXEC.), 구조적 유사성(SIM.), 예측된 PDDL과 실제 PDDL 간의 정밀도와 재현율을 조합한 조화 평균인 세분화된 F1 점수(F1PRED, F1PARAM, F1PRECOND, F1EFF)가 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Performance comparison of different LLMs on Text2World using concrete domain description. ECk denotes the setting where models are allowed k correction attempts (EC0: zero-shot without correction, EC3: with 3 correction attempts).
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