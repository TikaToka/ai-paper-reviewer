---
title: "Smaller Language Models Are Better Instruction Evolvers"
summary: "소형 언어 모델이 더 나은 명령 생성자!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Beijing University of Posts and Telecommunications",]
showSummary: true
date: 2024-12-15
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.11231 {{< /keyword >}}
{{< keyword icon="writer" >}} Tingfeng Hui et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-17 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.11231" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.11231" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/smaller-language-models-are-better" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

**대형 언어 모델(LLM)은 다양한 작업에 효과적이지만, 고품질 명령 튜닝 데이터가 필요합니다.** 복잡하고 다양한 명령을 생성하는 것은 어렵고 시간이 많이 걸립니다. 기존 연구는 LLM이 더 나은 명령 생성 능력을 가지고 있다고 가정했지만, 이 연구에서는 이러한 가정에 의문을 제기합니다.

본 연구는 **소형 언어 모델(SLM)이 LLM보다 더 효과적인 명령 생성자**임을 보여줍니다. 세 가지 명령 생성 시나리오에서 SLM은 **더 복잡하고 다양한 명령을 생성**했습니다. SLM은 **더 넓은 출력 공간을 가지므로 과신뢰도가 낮고 더 다양한 명령을 생성**할 수 있습니다. 또한 본 연구에서는 명령의 복잡성을 고려하는 새로운 평가 지표인 **IC-IFD(Instruction Complex-Aware IFD)**를 제안합니다. IC-IFD는 명령 데이터의 효과를 평가하는 데 있어 **기존 지표보다 정확**합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} SLM은 LLM보다 더 복잡하고 다양한 명령을 생성할 수 있습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} SLM은 LLM보다 더 넓은 출력 공간을 가지고 있으며, 과신뢰도가 낮습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} IC-IFD는 명령 데이터의 효과를 평가하는 데 있어 기존 지표보다 더 정확합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**소형 언어 모델(SLM)이 복잡한 명령 생성에 있어 대형 언어 모델(LLM)보다 더 효과적일 수 있다는 점**을 보여줍니다.  이는 SLM이 **더 넓은 출력 공간과 낮은 과신뢰도**를 가지기 때문입니다. 또한 명령의 복잡성을 고려하는 새로운 평가 지표인 **IC-IFD**를 제시하여 명령 데이터의 효과를 보다 정확하게 평가할 수 있도록 합니다. 이 연구는 **명령 데이터 생성 및 평가에 대한 새로운 관점**을 제시하며, **LLM의 효율적인 활용 및 성능 향상**을 위한  **SLM 연구의 중요성**을 강조합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.11231/x1.png)

> 🔼 이 그림은 Evol-Instruct 시나리오에서 Llama-3.1-8B-Instruct(SLM)와 Llama-3.1-70B-Instruct(LLM)를 각 라운드의 감독 모델로 사용하여 Llama-3-8B에 대해 세 번의 명령어 발전 반복 동안의 성능 비교를 보여줍니다. 4가지 벤치마크(IFEval Pr.(S), IFEval In.(S), IFEval Pr.(L), IFEval In.(L), GSM8K, MATH, HumanEval, MBPP)에서 SLM과 LLM으로 생성된 명령어 데이터로 훈련된 Llama-3-8B의 성능을 비교합니다. x축은 반복 횟수(0~3)를 나타내고, y축은 각 벤치마크의 성능 점수를 나타냅니다. 각 벤치마크에 대해 SLM 기반 명령어 데이터(파란색 실선)와 LLM 기반 명령어 데이터(주황색 실선)의 성능 곡선이 표시됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Comparison of performance on Llama-3-8B during three iterations of instruction evolution, using Llama-3.1-8B-Instruct and Llama-3.1-70B-Instruct as supervised models for each round under Evol-Instruct scenario.
> </details>





{{< table-caption >}}
| Model | Instruction Following (IFEval) | | Math Reasoning | | Code Generation | 
|---|---|---|---|---|---|---|---|---|---| 
| | Pr.(S) | In.(S) | Pr.(L) | In.(L) | | GSM8K | MATH | | HumanEval | MBPP |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|  Supervised Model: Llama-3.1-70B-Instruct | | | | | | | | | | |
| Mistral-7B-v0.3 | 19.59 | 31.77 | 22.74 | 34.65 | | 33.89 | **3.16** | | 24.39 | 6.00 |
| DeepSeek-7B | 36.23 | **48.20** | 41.04 | 52.52 | | **48.07** | 2.96 | | 28.66 | 33.00 |
| Llama-3.2-3B | 40.11 | 50.84 | 43.81 | 54.43 | | 53.75 | 6.60 | | 35.98 | **36.00** |
| Llama-3-8B | 33.83 | 46.28 | 36.41 | 49.28 | | 63.00 | 7.62 | | 43.90 | 36.20 |
| Llama-3.1-8B | 34.57 | 46.04 | 38.81 | 50.48 | | 64.22 | 11.32 | | **51.22** | 40.60 |
| InternLM-2-7B | 40.85 | 53.48 | 44.54 | 56.95 | | **68.31** | 19.50 | | 56.10 | 40.40 |
| Supervised Model: Llama-3.1-8B-Instruct||||| | | | | |
| Mistral-7B-v0.3 | **24.40** | **35.01** | **26.25** | **37.53** | | **40.18** | 2.84 | | **29.27** | **19.60** |
| DeepSeek-7B | **36.60** | 48.08 | **41.77** | **53.12** | | 47.92 | **3.56** | | **34.76** | **33.80** |
| Llama-3.2-3B | **41.59** | **53.48** | **45.66** | **57.07** | | **55.12** | **7.32** | | **39.02** | 32.80 |
| Llama-3-8B | **35.49** | **47.00** | **39.56** | **50.72** | | **63.38** | **11.44** | | **48.17** | **37.60** |
| Llama-3.1-8B | **38.45** | **50.96** | **43.81** | **55.28** | | **67.10** | **13.12** | | 48.78 | **41.60** |
| InternLM-2-7B | **43.07** | **54.80** | **47.32** | **58.39** | | 68.08 | **20.32** | | **57.93** | **40.80** |{{< /table-caption >}}

> 🔼 Llama-3.1-8B-Instruct 및 Llama-3.1-70B-Instruct를 Evol-Instruct 시나리오에서 각각 교사 모델로 사용하여 지시 진화 성능을 여러 모델에 대해 비교한 표입니다. 지시 따르기(IFEval), 수학적 추론(GSM8K, MATH), 코드 생성(HumanEval, MBPP)과 같은 다양한 작업에서 성능을 측정합니다. 표에서 Pr.(S)는 작은 모델을 사용한 프롬프트 점수를, In.(S)는 작은 모델을 사용한 지시 점수를, Pr.(L)는 큰 모델을 사용한 프롬프트 점수를, In.(L)는 큰 모델을 사용한 지시 점수를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparison of performance with Llama-3.1-8B-Instruct and Llama-3.1-70B-Instruct as supervised models under Evol-Instruct scenario.
> </details>





### In-depth insights


#### SLM Instruction Evolution
**SLM 명령어 진화**는 대규모 언어 모델(LLM)보다 작은 언어 모델(SLM)이 명령어 데이터를 진화시키는 데 **더 효과적**이라는 것을 시사합니다. 실험 결과, SLM은 **더 복잡하고 다양한 명령어**를 생성하여 향상된 성능을 보였습니다. SLM의 **더 넓은 출력 공간**은 LLM보다 **과적합 가능성이 낮고 더 다양한 토큰**을 생성할 수 있기 때문입니다. 또한 **IC-IFD**는 명령어 데이터의 복잡성을 고려하여 **명령어 튜닝 없이도** 명령어 데이터의 효과를 **더 정확하게 평가**할 수 있습니다. 이 연구는 SLM이 명령어 진화에서 중요한 역할을 할 수 있음을 보여주며, 효율적이고 효과적인 명령어 데이터 생성에 대한 새로운 가능성을 제시합니다.

#### Output Space Comparison
**출력 공간 비교**는 언어 모델의 창의성과 다양성을 이해하는 데 중요합니다. 더 큰 모델은 일반적으로 더 넓은 출력 공간에 접근할 수 있지만 출력이 더 예측 가능하고 덜 다양할 수 있다는 점을 강조하는 것이 중요합니다. 작은 모델은 제한된 공간에서 작동하지만 예상치 못한 독창적인 출력을 생성할 수 있습니다. **토큰 확률 분포 비교 및 MND(최소 이웃 거리)와 같은 메트릭**은 이러한 차이점을 정량화하는 데 도움이 될 수 있습니다. **출력 공간의 폭과 생성된 텍스트의 다양성 간의 균형을 이해하는 것**이 다양한 애플리케이션에 적합한 모델을 선택하는 데 중요합니다.

#### Instruction Complexity
**명령어 복잡성**은 LLM 성능에 중요한 역할을 합니다. 복잡한 명령어는 모델의 능력을 최대한 발휘하는 데 도움이 되지만 너무 복잡한 명령어는 역효과를 낳을 수 있습니다. 이 연구는 **작은 언어 모델(SLM)이 큰 언어 모델(LLM)보다 더 복잡하고 다양한 명령어를 생성하는 데 더 효과적**이라는 것을 보여줍니다. SLM은 **더 넓은 출력 공간**을 가지고 있어 **과신하는 경향이 적고** 다양한 토큰을 생성할 수 있기 때문입니다. 이 연구에서는 또한 명령어의 복잡성을 고려하는 새로운 지표인 **IC-IFD**를 제안합니다. IC-IFD는 명령어 튜닝 없이 명령어 데이터의 효과를 더 정확하게 평가할 수 있습니다. 이러한 발견은 LLM 훈련을 위한 고품질 명령어 데이터를 생성하는 새로운 방법에 대한 시사점을 제공합니다.

#### IC-IFD Metric
**IC-IFD(명령어 복잡도 인식 IFD)**는 기존 IFD 점수의 한계를 극복하기 위해 제안된 새로운 지표입니다. 기존 IFD는 명령어의 영향력을 측정하지만 명령어 자체의 복잡도는 고려하지 않았습니다. 이로 인해 복잡한 명령어가 높은 IFD 점수를 받더라도 실제 성능은 기대에 못 미치는 경우가 발생했습니다. IC-IFD는 이러한 문제를 해결하기 위해 **명령어의 난이도를 페널티 항으로 추가**합니다. 즉, 명령어가 복잡할수록 IC-IFD 점수는 낮아집니다. 이를 통해 **명령어 데이터의 품질을 더욱 정확하게 평가**하고, **명령어 튜닝 없이도 효과적인 명령어 데이터를 판별**할 수 있습니다. 실험 결과, IC-IFD는 다양한 설정에서 기존 IFD보다 성능 저하를 효과적으로 완화했습니다. 이는 IC-IFD가 **복잡한 명령어의 영향을 적절히 반영**하고 있음을 보여줍니다. IC-IFD는 향후 명령어 데이터 합성 연구에 **새로운 기준**을 제시할 것으로 기대됩니다.

#### SLM Potential & Limits
**소형 언어 모델(SLM)**은 **효율적인 명령어 생성**과 **다양한 출력**에서 강점을 보입니다. **더 적은 컴퓨팅 파워**와 **낮은 추론 능력**에도 불구하고, **복잡하고 다양한 명령어 생성**에서 대형 언어 모델(LLM)보다 뛰어난 성능을 발휘합니다. 이는 SLM이 **더 넓은 출력 공간**을 가지고, **과적합**될 가능성이 적기 때문입니다. 하지만 SLM은 **매우 어려운 명령어**를 생성할 경우 성능이 저하될 수 있으며, **다양한 작업**에 대한 평가가 필요합니다. 또한, **명령어 데이터의 효율성 평가**를 위한 **새로운 지표** 개발이 중요합니다. 향후 연구에서는 **다양한 도메인**에서의 SLM 성능과 **전체 명령어 데이터 합성 과정**에서의 역할을 탐구해야 합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.11231/x2.png)

> 🔼 이 그림은 Evol-Instruct 시나리오에서 Llama-3.1-8B-Instruct(SLM)와 Llama-3.1-70B-Instruct(LLM)를 감독 모델로 사용하여 세 번의 반복 동안 진화된 명령어의 난이도 분포를 보여줍니다. 각 라운드마다 SLM에서 생성된 명령어 데이터는 매우 쉬움, 쉬움, 중간, 어려움, 매우 어려움의 다섯 가지 난이도로 분류됩니다. 각 막대는 특정 난이도 범주에 속하는 명령어의 비율을 나타냅니다. 이 그림은 SLM이 LLM보다 더 복잡하고 어려운 명령어를 생성하는 경향이 있음을 보여줍니다. 특히 세 번째 반복에서 SLM에 의해 생성된 명령어의 대부분은 '매우 어려움'으로 분류되는 반면 LLM에서 생성된 명령어는 난이도가 낮은 경향이 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Distribution of difficulty levels for instructions evolved during three iterations, using Llama-3.1-8B-Instruct and Llama-3.1-70B-Instruct as supervised models for each round under Evol-Instruct scenario.
> </details>



![](https://arxiv.org/html/2412.11231/x3.png)

> 🔼 Qwen-2.5 시리즈 모델의 성능 비교를 보여주는 그림입니다. 이 그림은 Evol-Instruct 시나리오에서 다양한 크기의 Qwen-2.5 모델 (0.5B에서 72B까지)에 대해 SLM-INST와 LLM-INST의 성능을 비교하여 SLM이 더욱 복잡하고 어려운 명령 데이터를 생성할 수 있음을 보여줍니다. 자세한 결과는 표 11에서 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Comparison of performance among Qwen-2.5 series models. Detailed results can be found in Table 11.
> </details>



![](https://arxiv.org/html/2412.11231/x4.png)

> 🔼 이 그림은 AutoIF 시나리오에서 Llama-3.1-8B-Instruct와 Llama-3.1-70B-Instruct가 생성한 명령어에 대한 최소 이웃 거리 분포를 보여줍니다. 최소 이웃 거리는 임베딩 공간에서 명령어들 사이의 유사성을 측정한 것으로, 값이 클수록 다양성이 높음을 나타냅니다. 그림에서 SLM(Llama-3.1-8B-Instruct)이 생성한 명령어들이 LLM(Llama-3.1-70B-Instruct)보다 더 넓게 분포되어 있어, SLM이 더 다양한 명령어를 생성한다는 것을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Distribution of Minimum Neighbor Distance for instructions generated by Llama-3.1-8B-Instruct and Llama-3.1-70B-Instruct in the AutoIF scenario.
> </details>



![](https://arxiv.org/html/2412.11231/x5.png)

> 🔼 이 그림은 Evol-Instruct 시나리오에서 SLM(작은 언어 모델)과 LLM(큰 언어 모델)이 출력 토큰 확률 분포를 비교하여 보여줍니다. SLM은 LLM에 비해 상대적으로 약한 명령어 준수 능력으로 인해 출력 공간이 더 넓고 다양한 토큰을 생성하는 경향이 있음을 보여줍니다. 따라서 SLM은 LLM에 비해 더 복잡하고 다양한 명령을 생성할 수 있습니다. x축은 확률을 나타내고, y축은 밀도를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Comparison of output token probability distributions in the Evol-Instruct scenario.
> </details>



![](https://arxiv.org/html/2412.11231/x6.png)

> 🔼 이 그림은 세 가지 데이터 선택 비율(5%, 10%, 15%)에서 IC-IFD와 IFD를 사용하여 Alpaca 데이터셋의 상위 부분을 유지했을 때 Llama-3-8B 및 Llama-3.2-3B 모델의 성능을 비교하여 보여줍니다. 각 비율에 대해 IC-IFD가 IFD보다 더 나은 성능을 보이는 것을 알 수 있습니다. 즉, IC-IFD를 사용하여 데이터를 필터링하면 IFD를 사용하는 것보다 더 나은 결과를 얻을 수 있음을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Performance comparison of three data selection ratios on Alpaca dataset between IC-IFD and IFD.
> </details>



![](https://arxiv.org/html/2412.11231/x7.png)

> 🔼 이 그림은 세 가지 데이터 선택 비율(5%, 10%, 15%)에 대해 IC-IFD로 필터링된 데이터로 학습된 모델과 전체 Alpaca 데이터셋으로 학습된 모델의 성능을 비교하여 보여줍니다. Llama-3.2-3B와 Llama-3-8B 두 모델에 대해, IC-IFD로 필터링된 데이터로 학습된 모델이 전체 데이터셋으로 학습된 모델보다 더 나은 성능을 보이는 것을 알 수 있습니다. 이는 IC-IFD가 효과적으로 고품질의 명령 데이터를 선택하여 모델 성능 향상에 기여함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Performance comparison of three data selection ratios on Alpaca dataset between IC-IFD and full dataset.
> </details>



![](https://arxiv.org/html/2412.11231/x8.png)

> 🔼 이 그림은 Evol-Instruct 시나리오에서 '제약 조건 추가' 전략을 적용했을 때 LLM과 SLM이 생성한 지시문의 차이점을 보여주는 예시입니다. LLM은 주어진 '건강 유지 요령 3가지 제시' 지시문에 '적당한 생활 방식을 고려하여 건강을 유지하기 위한 실행 가능한 3가지 요령을 제시하고, 이를 일상에 어떻게 적용할 수 있는지 설명하라'는 조건을 추가했습니다. 반면, SLM은 '운동 시간이 제한되고 식단 제약이 있는 바쁜 일정을 가진 사람이 전반적인 건강과 웰빙을 유지하기 위한 근거 기반 요령 3가지를 제공하라'는 더욱 까다로운 조건을 추가했습니다. SLM은 같은 진화 전략 하에서 LLM보다 더 복잡하고 어려운 지시문을 생성할 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Comparison of cases between LLMs and SLMs under adding constraints strategy.
> </details>



![](https://arxiv.org/html/2412.11231/x9.png)

> 🔼 이 그림은 Evol-Instruct 시나리오에서 '심화' 전략을 사용하는 경우 LLM과 SLM이 생성한 지시사항의 차이점을 보여주는 예시를 제공합니다. LLM이 생성한 지시사항은 단순히 시간당 요금과 추가 근무 시간에 대한 질문을 추가하는 반면, SLM은 평일과 주말의 가변 시급, 추가 보너스, 시간 제한 등 더 복잡하고 다양한 조건을 포함하는 지시사항을 생성합니다. 즉, SLM은 동일한 전략에서 LLM보다 더 복잡하고 심층적인 지시사항을 생성할 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Comparison of cases between LLMs and SLMs under deepening strategy.
> </details>



![](https://arxiv.org/html/2412.11231/x10.png)

> 🔼 Evol-Instruct 시나리오에서 사용되는 심층 진화 프롬프트 템플릿입니다. 주어진 프롬프트를 더 복잡한 버전으로 다시 작성하여 ChatGPT 및 GPT-4와 같은 유명 AI 시스템이 처리하기 더 어렵게 만드는 것이 목표입니다. 다시 작성된 프롬프트는 합리적이어야 하고, 인간이 이해하고 응답할 수 있어야 합니다. 주어진 프롬프트를 복잡하게 만드는 방법(METHOD)이 제공되며, 다시 작성된 프롬프트는 간결해야 하고 주어진 프롬프트에 10~20단어만 추가할 수 있습니다. 출력에는 주어진 프롬프트와 다시 작성된 프롬프트 없이 새 프롬프트만 생성해야 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: In-depth evolution prompt template utilized in Evol-Instruct scenario.
> </details>



![](https://arxiv.org/html/2412.11231/x11.png)

> 🔼 Evol-Instruct 시나리오에서 사용되는 네 가지 심층 진화 방법을 설명합니다. 이러한 방법에는 제약 조건 추가, 질문 심화, 구체화, 추론 단계 추가가 포함됩니다. 제약 조건 추가는 주어진 프롬프트에 제약/요구 사항을 하나 더 추가하는 것을 포함합니다. 심화는 주어진 프롬프트에 특정 문제에 대한 질문이 포함된 경우 질문의 깊이와 폭을 증가시키는 것을 포함합니다. 구체화는 일반적인 개념을 더 구체적인 개념으로 대체하는 것을 포함합니다. 추론 단계 추가는 주어진 프롬프트를 몇 가지 간단한 사고 과정으로 해결할 수 있는 경우 명시적으로 여러 단계 추론을 요청하도록 다시 작성하는 것을 포함합니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Four in-depth methods utilized in Evol-Instruct scenario.
> </details>



![](https://arxiv.org/html/2412.11231/x12.png)

> 🔼 이 그림은 Evol-Instruct 시나리오에서 사용되는 너비 우선 진화 프롬프트 템플릿을 보여줍니다. 주어진 프롬프트에서 영감을 얻어 완전히 새로운 프롬프트를 생성하는 것이 목표입니다. 이 새로운 프롬프트는 주어진 프롬프트와 같은 도메인에 속해야 하지만 더 희귀해야 합니다. 생성된 프롬프트의 길이와 복잡성은 주어진 프롬프트와 유사해야 합니다. 생성된 프롬프트는 합리적이어야 하고 인간이나 최신 AI 챗봇이 이해하고 응답할 수 있어야 합니다. 다른 단어나 특수 기호 없이 새 프롬프트만 생성해야 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: In-breadth evolution prompt template utilized in Evol-Instruct scenario.
> </details>



![](https://arxiv.org/html/2412.11231/x13.png)

> 🔼 이 그림은 AutoIF 시나리오에서 Self-Instruct Seed Instructions의 프롬프트 템플릿을 보여줍니다. AutoIF는 소규모 시드 명령어 세트에서 시작하여 모델의 명령어 준수 능력을 향상시키기 위해 대규모의 안정적인 명령어를 자동으로 생성하는 것을 목표로 합니다. 이 그림에 표시된 프롬프트는 AutoIF의 첫 번째 단계에서 사용됩니다. 템플릿은 모델에 50개의 서로 다른 명령어를 제공하도록 요청하고 있으며, 각 명령어는 응답 형식에 관한 것이어야 하고 Python 함수로 쉽게 평가할 수 있어야 합니다. 또한 몇 가지 시드 명령어 예시와 원하지 않는 명령어 유형 예시를 제공합니다. 응답에서 각 명령어는 한 줄에 하나씩 생성되어야 하며 '-'로 시작해야 합니다. 또한 시드 명령어를 반복해서는 안 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: Prompt template of Self-Instruct Seed Instructions in AutoIF scenario.
> </details>



![](https://arxiv.org/html/2412.11231/x14.png)

> 🔼 AutoIF는 주어진 명령에 따라 응답이 생성되는지 확인하기 위해 Python에서 평가 함수를 작성하는 전문가 역할을 하는 프롬프트 템플릿입니다. 명령어가 주어지면, 입력 문자열 'response'가 해당 명령어를 따르는지 평가하는 'evaluate'라는 Python 함수를 작성해야 합니다. 따르는 경우 True를 반환하고, 그렇지 않으면 False를 반환합니다. 응답은 'func' 키에 평가 함수가 포함된 단일 JSON과 'cases' 키에 세 가지 테스트 케이스 목록이 포함되어야 하며, 각 테스트 케이스는 'input' 키에 입력과 'output' 키에 예상 출력(true 또는 false)을 포함합니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: Prompt template of Verification Funcs and Cases Generation in AutoIF scenario.
> </details>



![](https://arxiv.org/html/2412.11231/x15.png)

> 🔼 이 그림은 Auto Evol-Instruct 시나리오에서 사용되는 프롬프트 템플릿을 보여줍니다. 주어진 명령을 더 복잡한 버전으로 다시 작성하는 명령 다시 작성자 역할을 LLMs에게 요청합니다. 4단계의 계획을 세우고 실행하여 주어진 명령을 더 복잡하게 만들고 최종적으로 다시 작성된 명령을 제공합니다. 명령의 언어를 변경하는 방법은 제공하지 않도록 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 15: Prompt template of Auto Evol-Instruct scenario.
> </details>



![](https://arxiv.org/html/2412.11231/x16.png)

> 🔼 이 그림은 응답 생성에 사용되는 프롬프트 템플릿을 보여줍니다. 입력이 제공되는 경우, 주어진 명령과 입력을 바탕으로 포괄적이고 정확한 응답을 제공하도록 지시합니다. 입력이 제공되지 않는 경우, 주어진 명령을 바탕으로 포괄적이고 정확한 응답을 제공하도록 지시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 16: Prompt template of response generation.
> </details>



![](https://arxiv.org/html/2412.11231/x17.png)

> 🔼 이 그림은 주어진 사용자 쿼리의 내용을 기반으로 사용자 의도를 식별하고 쿼리의 난이도를 평가하는 프롬프트 템플릿을 보여줍니다. 프롬프트는 사용자 쿼리, 출력 형식(사용자 의도, 풀이에 필요한 지식, '매우 쉬움', '쉬움', '중간', '어려움', '매우 어려움' 중 하나인 난이도), 그리고 출력으로 구성됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 17: Prompt template of evaluating the difficulty levels.
> </details>



![](https://arxiv.org/html/2412.11231/x18.png)

> 🔼 이 그림은 진화 궤적에서 키워드를 추출하기 위한 프롬프트 템플릿을 보여줍니다. 주어진 지시 진화 궤적을 주의 깊게 읽고 핵심 개념이나 프로세스를 식별합니다. 궤적의 핵심 아이디어를 정확하게 요약하는 짧고 간단한 구문을 만듭니다. 요약은 간결해야 하고 진화 과정의 본질에 초점을 맞춰야 합니다. 구문에 불필요한 기호, 구두점 또는 서식이 포함되어 있지 않아야 합니다. 간략하고 명확한 메서드 설명이어야 합니다. 메서드 시작 부분에 있는 숫자 레이블이나 특수 식별자는 무시하십시오. 추가 설명이나 추가 정보 없이 요약 구문만 제공합니다. 지시 진화 궤적: {TRAJECTORY}
> <details>
> <summary>read the caption</summary>
> Figure 18: Prompt template of extracting the keywords from evolution trajectories.
> </details>



![](https://arxiv.org/html/2412.11231/x19.png)

> 🔼 이 그림은 사용자 쿼리의 난이도 점수를 평가하기 위한 프롬프트 템플릿을 보여줍니다. 프롬프트는 모델에게 주어진 사용자 쿼리의 의도를 먼저 식별한 다음, 쿼리의 내용을 기반으로 0에서 100까지의 난이도 점수를 매기도록 지시합니다. 출력은 다른 단어나 기호 없이 난이도 점수만 생성해야 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 19: Prompt template of evaluating the difficulty scores.
> </details>



![](https://arxiv.org/html/2412.11231/x20.png)

> 🔼 이 그림은 두 AI 어시스턴트의 응답을 비교하여 승패를 평가하는 데 사용되는 프롬프트 템플릿을 보여줍니다. 사용자 질문과 두 어시스턴트의 응답이 주어지면, 평가자는 응답이 사용자의 요구에 얼마나 잘 부합하는지, 간결하고 정확한지, 불필요한 정보 없이 포괄적인지, 논리적인 흐름을 따르는지, 정확한 기술 용어를 사용하는지, 사실적으로 정확하고 객관적인지 등을 기준으로 평가합니다. 마지막 줄에는 어떤 어시스턴트가 더 나은지, 혹은 동등한지 단일 레이블로 출력합니다.
> <details>
> <summary>read the caption</summary>
> Figure 20: Prompt template of evaluating the win-tie-lose rates.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | Instruction Following (IFEval) |   | Math Reasoning |   | Code Generation |   |
|---|---|---|---|---|---|---|---|
|       | Pr.(S) | In.(S) | Pr.(L) | In.(L) |   | GSM8K | MATH |   | HumanEval | MBPP |
|---|---|---|---|---|---|---|---|---|---|---| 
| **Supervised Model: Qwen-2-72B-Instruct** | | | | | | | | | |
| Mistral-7B-v0.3 | 20.15 | 30.94 | 23.84 | 34.41 |   | 46.93 | **3.26** |   | 32.32 | 1.80 |
| DeepSeek-7B | 35.67 | 47.12 | **39.56** | 50.84 |   | 44.81 | 2.76 |   | **36.59** | **34.00** |
| Llama-3.2-3B | 39.74 | 51.44 | 43.99 | 55.40 |   | 53.83 | **7.40** |   | 38.41 | 31.00 |
| Llama-3-8B | 34.75 | 45.80 | 37.71 | 48.92 |   | 63.76 | **10.06** |   | 43.90 | 35.40 |
| Llama-3.1-8B | **36.41** | **47.60** | 39.00 | 50.60 |   | 65.43 | 10.84 |   | **48.17** | 38.40 |
| InternLM-2-7B | 41.96 | 53.60 | 43.99 | 55.64 |   | 65.28 | 17.96 |   | 56.71 | 40.60 |
| **Supervised Model: Qwen-2-7B-Instruct** | | | | | | | | | |
| Mistral-7B-v0.3 | **25.32** | **37.17** | **29.76** | **41.01** |   | **47.31** | 2.20 |   | **32.93** | **12.00** |
| DeepSeek-7B | **36.41** | **48.56** | 39.37 | **51.32** |   | **48.07** | **3.82** |   | 35.37 | 33.20 |
| Llama-3.2-3B | **43.81** | **55.16** | **47.87** | **58.27** |   | **56.56** | 7.18 |   | **39.63** | **31.40** |
| Llama-3-8B | **38.92** | **48.33** | **43.81** | **52.19** |   | **63.91** | 8.66 |   | **45.73** | **38.40** |
| Llama-3.1-8B | 34.75 | 45.80 | **39.93** | **51.08** |   | **68.76** | **14.02** |   | 46.34 | **38.60** |
| InternLM-2-7B | **44.12** | **55.16** | **48.62** | **58.73** |   | **66.87** | **19.60** |   | **58.54** | **41.40** |{{< /table-caption >}}
> 🔼 Qwen-2-7B-Instruct(SLM)와 Qwen-2-72B-Instruct(LLM)를 Evol-Instruct 시나리오에서 지도 모델로 사용하여 성능을 비교한 표입니다.  IFEval, FollowBench, GSM8K, MATH, HumanEval, MBPP 등 다양한 벤치마크에서 성능을 측정했습니다.  Pr.(S)와 In.(S)는 각각 작은 모델로 생성한 명령과 지시에 대한 성능을 나타내며, Pr.(L)과 In.(L)는 큰 모델에 대한 성능을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Comparison of performance with Qwen-2-7B-Instruct and Qwen-2-72B-Instruct as supervised models under Evol-Instruct scenario.
> </details>

{{< table-caption >}}
| Model | IFEval | | | | FollowBench (HSR) | | | | | Common Abilities | |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---| 
| | Pr.(S) | In.(S) | Pr.(L) | In.(L) | | Level 1 | Level 2 | Level 3 | Level 4 | Level 5 | Avg. | | C-Eval | MMLU | HumanEval | GSM8K |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---| 
| *Supervision Model: Llama-3.1-70B-Instruct* | | | | | | | | | | | | | | | |
| Llama-3.2-3B | 40.85 | 51.92 | 42.33 | 53.84 | | **61.17** | 57.59 | **50.55** | 33.09 | 26.74 | 45.83 | | **41.37** | **52.65** | **29.88** | 27.07 |
| Llama-3-8B | 37.71 | 50.00 | 39.19 | 52.04 | | 49.64 | 46.60 | 41.56 | 27.05 | 22.37 | 37.44 | | 41.87 | 51.14 | 26.83 | 37.76 |
| Llama-3.1-8B | 41.96 | 53.36 | 42.70 | 54.20 | | 51.77 | 45.60 | 45.04 | 34.85 | 26.61 | 40.78 | | **44.50** | 56.39 | 31.10 | 38.21 |
| Qwen-2-7B | 41.96 | 53.60 | 43.62 | 55.64 | | 72.18 | 62.45 | **56.43** | 41.31 | 35.42 | 53.56 | | **81.08** | 55.71 | 57.32 | **79.68** |
| Qwen-2.5-7B | 49.17 | **60.31** | 50.46 | 61.51 | | **78.88** | **73.78** | **61.50** | 51.99 | 45.42 | **62.31** | | **80.46** | 58.39 | 67.68 | **85.90** |
| InternLM-2-7B | 46.21 | 56.71 | 48.06 | 58.63 | | 68.89 | 62.23 | 54.17 | 44.27 | 42.06 | 54.33 | | 60.11 | 60.59 | 65.35 | 50.00 |
| *Supervision Model: Llama-3.1-8B-Instruct* | | | | | | | | | | | | | | | |
| Llama-3.2-3B | **43.62** | **54.20** | **46.95** | **57.07** | | 56.95 | **61.46** | 50.20 | **37.65** | **34.16** | **48.08** | | 40.56 | 49.08 | 25.00 | **29.87** |
| Llama-3-8B | **41.04** | **51.32** | **42.88** | **53.11** | | **62.99** | **54.38** | **49.29** | **32.21** | **32.21** | **46.21** | | **43.49** | **55.63** | **37.20** | **45.26** |
| Llama-3.1-8B | **42.51** | **54.92** | **44.73** | **56.71** | | **63.99** | **58.15** | **53.29** | **39.49** | **36.02** | **50.19** | | 43.77 | **58.32** | **32.32** | **47.92** |
| Qwen-2-7B | **44.92** | **55.76** | **47.50** | **58.39** | | **78.75** | **63.30** | 52.31 | **50.28** | **43.08** | **57.54** | | 80.11 | **56.84** | **65.24** | 79.53 |
| Qwen-2.5-7B | **50.09** | 59.59 | **52.50** | **61.75** | | 77.86 | 70.22 | 59.86 | **53.35** | **47.18** | 61.69 | | 79.74 | **60.17** | **72.56** | 84.69 |
| InternLM-2-7B | **47.50** | **57.67** | **50.83** | **61.15** | | **74.73** | **66.16** | **61.94** | **54.10** | **46.28** | **60.64** | | **63.03** | **63.16** | **70.96** | **54.27** |{{< /table-caption >}}
> 🔼 이 표는 AutoIF 시나리오에서 Llama-3.1-8B-Instruct와 Llama-3.1-70B-Instruct를 지도 모델로 사용했을 때의 성능을 비교하여 보여줍니다. AutoIF는 소수의 초기 지침에서 대규모의 안정적인 지침을 자동으로 생성하는 것을 목표로 합니다. 표에서 Pr.(S) 및 In.(S)는 각각 작은 모델(Llama-3.1-8B-Instruct)로 지도 학습된 모델의 프롬프트 및 지침 수준에서의 IFEval 정확도를 나타내고, Pr.(L) 및 In.(L)은 큰 모델(Llama-3.1-70B-Instruct)로 지도 학습된 모델의 IFEval 정확도를 나타냅니다. FollowBench(HSR) 열은 다섯 가지 난이도 수준(1-5)과 평균 HSR(Hard Satisfaction Rate)을 보여주며, Common Abilities 열은 C-Eval, MMLU, HumanEval, GSM8K에서 모델의 성능을 보여줍니다. 이를 통해 다양한 측면에서 SLM과 LLM의 성능 차이를 비교할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Comparison of performance with Llama-3.1-8B-Instruct and Llama-3.1-70B-Instruct as supervised models under AutoIF scenario.
> </details>

{{< table-caption >}}
| Model | Instruction Following (IFEval) | | | | | Math Reasoning | | | Code Generation | |
|---|---|---|---|---|---|---|---|---|---|---| 
| | Pr.(S) | In.(S) | Pr.(L) | In.(L) | | GSM8K | MATH | | HumanEval | MBPP | 
|---|---|---|---|---|---|---|---|---|---|---| 
| Supervised Model: Llama-3.1-70B-Instruct | | | | | | | | | | | 
| Llama-3.2-3B | 36.60 | 48.68 | 39.00 | 51.08 | | 53.60 | 7.56 | | 35.37 | 33.00 | 
| Llama-3-8B | 35.86 | 47.60 | 38.63 | 50.24 | | 63.91 | 9.18 | | 38.41 | 32.40 | 
| Llama-3.1-8B | 36.97 | 47.60 | 40.30 | 51.08 | | 66.11 | 11.68 | | 40.85 | **40.40** | 
| Supervised Model: Llama-3.1-8B-Instruct | | | | | | | | | | | 
| Llama-3.2-3B | **45.47** | **57.43** | **50.28** | **61.27** | | **56.48** | **8.42** | | **38.41** | **34.40** | 
| Llama-3-8B | **37.34** | **49.64** | **39.74** | **51.56** | | **67.40** | **12.26** | | **43.90** | **34.80** | 
| Llama-3.1-8B | **38.08** | **49.76** | **40.48** | **52.40** | | **69.52** | **15.62** | | **51.22** | 38.80 |{{< /table-caption >}}
> 🔼 이 표는 Auto Evol-Instruct 시나리오에서 Llama-3.1-8B-Instruct와 Llama-3.1-70B-Instruct를 지도 모델로 사용한 성능 비교를 보여줍니다. Auto Evol-Instruct는 주어진 명령을 더 복잡한 버전으로 다시 작성하는 명령 재작성기입니다. 표에서 SLM(Llama-3.1-8B-Instruct)은 LLM(Llama-3.1-70B-Instruct)보다 더 효과적인 명령을 자동으로 진화시킬 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Comparison of performance with Llama-3.1-8B-Instruct and Llama-3.1-70B-Instruct as supervised models under Auto Evol-Instruct scenario.
> </details>

{{< table-caption >}}
| Metrics | IFEval | | | |
|---|---|---|---|---| 
| | Pr.(S) | In.(S) | Pr.(L) | In.(L) |
| Original | 33.09 | 44.72 | 36.41 | 48.32 |
| Instruction Len. | 29.94 | 39.69 | 33.83 | 43.53 |
| Instruction PPL | 27.91 | 39.69 | 32.35 | 44.36 |
| IFD | 30.87 | 43.53 | 36.04 | 47.60 |
| IC-IFD | **34.01** | **46.16** | **38.82** | **50.72** |{{< /table-caption >}}
> 🔼 이 표는 Llama-3-8B 모델에서 SLM으로 생성된 Alpaca-iter3 데이터의 25%를 사용하여 다양한 메트릭을 비교한 결과를 보여줍니다. 구체적으로, 명령 길이, 명령 PPL, IFD 및 IC-IFD와 같은 메트릭을 사용하여 데이터를 필터링하고 Llama-3-8B에서 IFEval 성능을 측정합니다. 이를 통해 IC-IFD가 명령 복잡도를 효과적으로 고려하여 다른 메트릭보다 더 정확한 데이터 품질 평가를 제공함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Comparison of different metrics under 25% of Alpaca-iter3 evolved by SLMs on Llama-3-8B.
> </details>

{{< table-caption >}}
| Hyperparameter | Value |
|---|---| 
| Learning Rate | 2 × 10⁻⁵ |
| Number of Epochs | 3 |
| Number of Devices | 8 |
| Per-device Batch Size | 1 |
| Gradient Accumulation Steps | 8 |
| Learning Rate Scheduler | cosine |
| Warmup Ratio | 0.03 |
| Max Sequence Length | 2048 |{{< /table-caption >}}
> 🔼 이 표는 Evol-Instruct, AutoIF, Auto Evol-Instruct 세 가지 시나리오에서 사용된 하이퍼파라미터들을 보여줍니다. 일반적인 하이퍼파라미터로는 epoch 수, 디바이스 수, 배치 크기, 그래디언트 누적 단계, 학습률 스케줄러, 웜업 비율, 최대 시퀀스 길이가 있습니다. LoRA 하이퍼파라미터로는 LoRA Rank, LoRA Alpha, LoRA Target, LoRA Dropout이 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Hyperparameters utilized in Evol-Instruct, AutoIF and Auto Evol-Instruct scenarios.
> </details>

{{< table-caption >}}
| Hyperparameter | Value |
|---|---| 
| **General Hyperparameters** | |
| Number of Epochs | 2 |
| Number of Devices | 8 |
| Per-device Batch Size | 1 |
| Gradient Accumulation Steps | 8 |
| Learning Rate Scheduler | cosine |
| Warmup Ratio | 0.03 |
| Max Sequence Length | 2048 |
| **LoRA Hyperparameters** |  |
| LoRA Rank | 8 |
| LoRA Alpha | 8 |
| LoRA Target | all module |
| LoRA Dropout | 0.0 |
| **Qwen-2.5-0.5B and 1.5B** | |
| Learning Rate | 1e-5 |
| **Qwen-2.5-3B and 7B** | |
| Learning Rate | 7e-6 |
| **Qwen-2.5-14B, 32B and 72B** | |
| Learning Rate | 5e-5 |{{< /table-caption >}}
> 🔼 이 표는 Qwen-2.5 시리즈 모델의 미세 조정에 사용된 하이퍼파라미터를 보여줍니다. 모델 크기에 따라 학습률과 LoRA 적용 여부가 다릅니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Hyperparameters utilized for fine-tuning Qwen-2.5 series models.
> </details>

{{< table-caption >}}
| | Seed Data | | 
| --- | ---: | ---: |
|  | **Dataset** | **Datasize** |
| Instruction Following | Alpaca | 51,983 |
| Mathematical Reasoning | GSM8K Train | 7,473 |
| Code Generation | Code Alpaca | 20,022 |{{< /table-caption >}}
> 🔼 이 표는 Evol-Instruct 및 Auto-Evol-Instruct 시나리오에 사용된 시드 명령 데이터의 통계를 제공합니다. 각 데이터 세트의 이름과 해당하는 데이터 크기가 나와 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Statistics of seed instruction data used in the Evol-Instruct and Auto-Evol-Instruct scenarios.
> </details>

{{< table-caption >}}
| Model | Instruction Following (IFEval) |   | Math Reasoning |   | Code Generation |   |
|---|---|---|---|---|---|---|---|
|       | Pr.(S) | In.(S) | Pr.(L) | In.(L) |   | GSM8K | MATH |   | HumanEval | MBPP |
|---|---|---|---|---|---|---|---|---|---|
|       |       |       |       |       |       |       |       |       |       |       |
| Mistral-7B-v0.3 | 17.01 | 26.86 | 19.04 | 29.14 |   | 27.07 | 0.12 |   | 10.20 | 8.80 |
| DeepSeek-7B | 22.00 | 34.05 | 23.48 | 35.73 |   | 44.05 | 0.56 |   | 25.61 | 33.80 |
| Llama-3.2-3B | 22.55 | 34.17 | 25.88 | 37.65 |   | 46.40 | 0.56 |   | 28.05 | 32.20 |
| Llama-3-8B | 23.11 | 32.97 | 24.77 | 35.13 |   | 53.68 | 0.22 |   | 25.00 | 28.60 |
| Llama-3.1-8B | 27.54 | 38.13 | 28.65 | 39.21 |   | 56.41 | 7.56 |   | 29.88 | 31.80 |
| InternLM-2-7B | 32.72 | 45.08 | 35.30 | 48.08 |   | 61.87 | 10.28 |   | 42.07 | 40.00 |{{< /table-caption >}}
> 🔼 이 표는 Evol-Instruct 및 Auto Evol-Instruct 시나리오에서 사용되는 시드 명령 데이터에 대한 실험 결과를 보여줍니다. Llama-3.2-3B, Llama-3-8B, Llama-3.1-8B, DeepSeek-7B, Mistral-7B-v0.3, InternLM-2-7B 등 다양한 모델에 대한 IFEval(명령어 수행), 수학적 추론(GSM8K, MATH), 코드 생성(HumanEval, MBPP) 성능을 보여줍니다. 표에서 볼 수 있듯이 이러한 시드 데이터로 학습된 모델의 성능은 최적이 아닙니다. 이는 현재 최신 기본 모델의 성능을 더욱 향상시키기에는 이러한 시드 데이터의 품질이 충분하지 않음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Results of seed instruction data.
> </details>

{{< table-caption >}}
| Model | Instruction Following (IFEval) |   | Math Reasoning |   | Code Generation |   |
|---|---|---|---|---|---|---| 
|  | Pr.(S) | In.(S) | Pr.(L) | In.(L) | GSM8K | MATH | HumanEval | MBPP |
|---|---|---|---|---|---|---|---|---| 
| *Supervised Model: Llama-3.1-70B-Instruct* |  |  |  |  |  |  |  |  |
| Iteration 1 | 33.83 | 46.28 | 36.41 | 49.28 | 63.00 | 7.62 | 43.90 | 36.20 |
| Iteration 2 | 32.53 | 43.76 | 34.20 | 46.16 | 64.59 | 10.04 | 42.07 | 36.60 |
| Iteration 3 | 35.12 | 47.36 | 36.97 | 49.28 | 64.75 | 11.82 | 43.29 | 37.20 |
| *Supervised Model: Llama-3.1-8B-Instruct* |  |  |  |  |  |  |  |  |
| Iteration 1 | 35.49 | 47.00 | 39.56 | 50.72 | 63.38 | 11.44 | 48.17 | 37.60 |
| Iteration 2 | 36.78 | 48.20 | 40.30 | 50.84 | 64.82 | 11.48 | 48.78 | 39.40 |
| Iteration 3 | 33.09 | 44.72 | 36.41 | 48.32 | 65.88 | 14.12 | 44.51 | 40.80 |{{< /table-caption >}}
> 🔼 이 표는 Evol-Instruct 시나리오에서 Llama-3-8B 모델에 대해 서로 다른 진화 반복(Iteration 1, 2, 3)을 적용한 후의 성능을 자세히 보여줍니다. Llama-3.1-70B-Instruct와 Llama-3.1-8B-Instruct를 각각 지도 모델로 사용하여 비교합니다. 성능 지표는 IFEval(Instruction Following), GSM8K, MATH(Math Reasoning), HumanEval, MBPP(Code Generation)를 포함합니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Detailed performance of different evolved iterations on Llama-3-8B refer to Figure 1.
> </details>

{{< table-caption >}}
| Model | Instruction Following (IFEval) | | | | | Math Reasoning | | | Code Generation | |
|---|---|---|---|---|---|---|---|---|---|---|
| | Pr.(S) | In.(S) | Pr.(L) | In.(L) | | GSM8K | MATH | | HumanEval | MBPP |
|---|---|---|---|---|---|---|---|---|---|---|
| Supervised Model: Llama-3.1-70B-Instruct | | | | | | | | | | |
| Qwen-2.5-0.5B | 18.48 | 32.73 | 22.00 | 35.85 | | 40.26 | 16.32 | | 30.49 | 27.60 |
| Qwen-2.5-1.5B | 28.84 | 42.67 | 31.98 | 46.04 | | 62.32 | 24.06 | | 50.00 | 43.20 |
| Qwen-2.5-3B | 37.89 | 48.56 | 42.70 | 53.60 | | 76.12 | 26.44 | | 63.41 | 55.40 |
| Qwen-2.5-7B | 46.21 | 56.83 | 50.64 | 60.79 | | 76.12 | 38.14 | | 70.73 | 61.60 |
| Qwen-2.5-14B (LoRA) | 40.11 | 54.43 | 48.24 | 61.99 | | 87.79 | 49.94 | | 75.00 | 67.20 |
| Qwen-2.5-32B (LoRA) | 42.88 | 57.31 | 51.20 | 64.15 | | 87.79 | 55.02 | | 80.49 | 71.20 |
| Qwen-2.5-72B (LoRA) | 50.63 | 68.43 | 57.12 | 70.98 | | 91.05 | 58.83 | | 82.93 | 76.00 |
| Supervised Model: Llama-3.1-8B-Instruct | | | | | | | | | | |
| Qwen-2.5-0.5B | 17.38 | 29.38 | 19.78 | 32.01 | | 40.71 | 16.26 | | 34.76 | 28.00 |
| Qwen-2.5-1.5B | 28.47 | 41.73 | 31.98 | 44.96 | | 65.35 | 27.84 | | 52.44 | 49.94 |
| Qwen-2.5-3B | 38.82 | 49.76 | 42.51 | 53.96 | | 76.57 | 30.92 | | 64.02 | 55.80 |
| Qwen-2.5-7B | 47.32 | 58.39 | 51.39 | 62.35 | | 82.03 | 43.78 | | 71.95 | 61.80 |
| Qwen-2.5-14B (LoRA) | 42.51 | 55.16 | 51.02 | 62.47 | | 88.17 | 52.22 | | 75.61 | 67.20 |
| Qwen-2.5-32B (LoRA) | 45.84 | 58.75 | 54.71 | 66.31 | | 89.61 | 55.28 | | 81.71 | 73.20 |
| Qwen-2.5-72B (LoRA) | 52.79 | 72.56 | 61.25 | 73.27 | | 91.36 | 60.75 | | 84.67 | 76.80 |{{< /table-caption >}}
> 🔼 Qwen-2.5 시리즈 모델의 성능 비교를 자세히 보여주는 표입니다. Figure 3에서 언급된 모델 크기 조정 실험의 결과를 자세히 보여줍니다. Llama-3.1-70B-Instruct 및 Llama-3.1-8B-Instruct를 감독 모델로 사용한 두 가지 설정에서 Qwen-2.5-0.5B, Qwen-2.5-1.5B, Qwen-2.5-3B, Qwen-2.5-7B, Qwen-2.5-14B (LORA), Qwen-2.5-32B (LORA), Qwen-2.5-72B (LORA) 모델의 성능을 IFEval (Pr.(S), In.(S), Pr.(L), In.(L)), GSM8K, MATH, HumanEval, MBPP 등의 벤치마크에서 평가한 결과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 11: Detailed performance among Qwen-2.5 series models refer to Figure 3.
> </details>

{{< table-caption >}}
| Temperature | HumanEval | MBPP | HumanEval | MBPP |
|---|---|---|---|---| 
| | *Supervised Model: Llama-3.1-70B-Instruct* | | *Supervised Model: Llama-3.1-8B-Instruct* | |
| greedy | 37.20 | 33.40 | **39.63** | **36.40** |
| 0.1 | 36.59 | 36.40 | **37.80** | **37.60** |
| 0.3 | 38.41 | 35.20 | **39.63** | **37.80** |
| 0.5 | 35.98 | 33.40 | **37.80** | **35.80** |
| 0.7 | 35.98 | **36.00** | **39.02** | 32.80 |
| 0.9 | 34.76 | 33.00 | **40.24** | **35.80** |{{< /table-caption >}}
> 🔼 이 표는 코드 생성 시나리오에서 다양한 온도 설정에 따른 Llama-3.2-3B 모델의 성능을 보여줍니다. 특히, greedy decoding (온도 0)과 0.1에서 0.9까지 다섯 가지 온도 설정에서 Code Alpaca 데이터에 대한 진화 과정을 거칩니다. 모든 응답 생성에는 Qwen-2.5-72B-Instruct를 사용합니다. 표는 HumanEval 및 MBPP 데이터 세트에 대한 pass@1 지표를 보여주며, Llama-3.1-70B-Instruct 및 Llama-3.1-8B-Instruct라는 두 가지 supervised model을 사용하여 fine-tuning한 결과를 비교합니다.
> <details>
> <summary>read the caption</summary>
> Table 12: Performance among different temperatures on Llama-3.2-3B under code generation scenario.
> </details>

{{< table-caption >}}
|                       | Alpaca | GSM8K Train | Code Alpaca |
| :-------------------- | :----: | :---------: | :--------: |
| Seed Instruction     | 27.63 |    34.05    |   26.01    |
| LLM-Inst Iter1      | 52.89 |    39.88    |   46.75    |
| **SLM-Inst Iter1** | **66.35** |  **48.85**  |  **58.86**  |
| LLM-Inst Iter2      | 68.16 |    47.14    |   65.02    |
| **SLM-Inst Iter2** | **77.62** |  **63.48**  |  **73.37**  |
| LLM-Inst Iter3      | 75.73 |    54.00    |   72.85    |
| **SLM-Inst Iter3** | **82.44** |  **72.12**  |  **79.19**  |{{< /table-caption >}}
> 🔼 이 표는 Evol-Instruct 시나리오에서 Llama-3.1-8B-Instruct(SLM)와 Llama-3.1-70B-Instruct(LLM)를 사용하여 3번의 반복 동안 진화된 명령어의 난이도 점수를 보여줍니다. 각 반복에서 SLM과 LLM으로 생성된 명령어 데이터셋(SLM-INST, LLM-INST)에 대해 Alpaca, GSM8K Train, Code Alpaca 데이터셋의 난이도 점수를 비교합니다. 난이도 점수는 Qwen-2.5-72B-Instruct 모델을 사용하여 평가되었습니다.
> <details>
> <summary>read the caption</summary>
> Table 13: Scores of difficulty levels for instructions evolved during three iterations, using Llama-3.1-8B-Instruct and Llama-3.1-70B-Instruct as supervised models for each round under Evol-Instruct scenario.
> </details>

{{< table-caption >}}
| Iteration | Average Reward | Average Reward | Average Reward |
|---|---|---|---| 
| | Alpaca | GSM8K | Code Alpaca |
|---|---|---|---| 
| *Supervised Model: Llama-3.1-70B-Instruct* | | | | 
| Iteration 1 | 1.54 | 0.74 | 1.10 |
| Iteration 2 | **1.68** | 0.73 | **1.19** |
| Iteration 3 | **1.56** | 0.69 | **1.14** |
| *Supervised Model: Llama-3.1-8B-Instruct* | | | |
| Iteration 1 | **1.59** | **1.01** | **1.23** |
| Iteration 2 | 1.54 | **0.79** | 0.96 |
| Iteration 3 | 1.42 | **0.97** | 1.03 |{{< /table-caption >}}
> 🔼 이 표는 Evol-Instruct 시나리오에서 서로 다른 반복 진행 후 진화된 명령 데이터의 평균 보상을 비교하여 SLM과 LLM 중 어떤 것이 더 나은 명령을 생성하는지 보여줍니다. Llama-3.1-70B-Instruct와 Llama-3.1-8B-Instruct를 감독 모델로 사용하고, 세 가지 데이터셋(Alpaca, GSM8K, Code Alpaca)에 대해 반복 1, 2, 3의 평균 보상 점수를 비교합니다.
> <details>
> <summary>read the caption</summary>
> Table 14: Comparison of average rewards among different iteration evolution instruction data.
> </details>

{{< table-caption >}}
| Datasets | IFD (%) | IC-IFD (%) | Performance |
|---|---|---|---| 
| SLMs (Alpaca iter 3) | **83.04** | 35.89 | 40.64 |
| LLMs (Alpaca iter 3) | 82.03 | **37.05** | **42.18** |{{< /table-caption >}}
> 🔼 이 표는 세 번째 진화 과정을 거친 Alpaca 데이터셋에서 SLM과 LLM으로 생성된 지시문의 IFD 및 IC-IFD 점수를 비교하여 보여줍니다. 지시문의 난이도가 매우 높은 경우, IFD 점수가 증가하는 경향이 있지만 미세 조정된 모델의 성능은 기대에 미치지 못하는 경우가 있음을 보여줍니다. 이와 반대로, IC-IFD 점수는 지시문 복잡성의 영향을 효과적으로 포착하여 보다 정확한 데이터 품질 평가를 제공합니다. Llama-3-8B 모델을 사용하여 두 데이터셋에 대한 IFEval의 평균 성능을 평가합니다.
> <details>
> <summary>read the caption</summary>
> Table 15: Comparison of IFD and IC-IFD on third-round evolved Alpaca datasets from SLMs and LLMs.
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