---
title: "The Stochastic Parrot on LLM's Shoulder: A Summative Assessment of Physical Concept Understanding"
summary: "본 연구는 대규모 언어 모델(LLM)이 물리적 개념을 얼마나 잘 이해하는지 평가하기 위해,  'PHYSICO'라는 새로운 평가 기준을 제시합니다.  PHYSICO는 그리드 형태의 추상적인 표현을 사용하여 LLM의 암기 능력에 의존하지 않고, 개념에 대한 심층적인 이해 능력을 평가합니다. 연구 결과, 최첨단 LLM들도 여전히 인간보다 상당히 낮은 성능을 보이..."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Tencent AI Lab",]
showSummary: true
date: 2025-02-13
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.08946 {{< /keyword >}}
{{< keyword icon="writer" >}} Mo Yu et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-14 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.08946" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.08946" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/the-stochastic-parrot-on-llm-s-shoulder-a" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

최근 급속한 발전을 이룬 대규모 언어 모델(LLM)은 다양한 언어 관련 작업에서 놀라운 성능을 보여주고 있지만,  실제로 개념을 얼마나 이해하는지는 여전히 논란의 여지가 있습니다.  일부 연구자들은 LLM이 단순히 데이터 상의 통계적 상관관계를 기반으로 답변을 생성하는 '확률적 앵무새'일 뿐이라고 주장합니다. 

본 연구는 이러한 논란에 답하기 위해, 물리적 개념 이해 능력을 평가하는 새로운 기준인 PHYSICO를 제시합니다. PHYSICO는 그리드 형태의 추상적인 표현을 이용하여 LLM의 단순한 암기 능력이 아닌 심층적인 이해 능력을 평가합니다.  실험 결과, 최첨단 LLM들도 PHYSICO 과제에서 인간보다 훨씬 낮은 성능을 보였으며,  '확률적 앵무새' 현상이 실제로 존재함을 입증했습니다.  또한,  다양한 추가 실험을 통해 LLM의 어려움이 단순히 새로운 형식의 과제에 대한 익숙하지 않음 때문이 아니라,  개념에 대한 심층적 이해의 어려움 때문임을 밝혔습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} LLM이 물리적 개념에 대한 심층적인 이해 능력은 인간보다 현저히 낮다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} LLM에서 '확률적 앵무새(Stochastic Parrot)' 현상이 존재하며, 이는 LLM이 단순히 패턴을 암기하는 데 그치는 것을 의미한다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 그리드 기반 추론 과제를 통해 LLM의 심층 이해 능력을 효과적으로 평가할 수 있으며, 이는 향후 LLM 연구 및 개발에 중요한 시사점을 제공한다 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대규모 언어 모델(LLM)**이 물리적 개념을 실제로 이해하는지 여부를 정량적으로 평가하는 새로운 방법론을 제시하여, **LLM의 한계와 잠재력**에 대한 중요한 통찰력을 제공합니다.  현재 **LLM 연구의 주요 트렌드**인  LLM의 이해 능력 평가 및 한계 극복에 직접적으로 기여하며, 향후 연구 방향을 제시하는 데 중요한 의미를 가집니다.  특히, **그리드 기반 추론 과제**를 통해 LLM의 단순한 암기 능력을 넘어 심층적인 이해 능력을 평가하는 새로운 접근법을 제시한 점이 돋보입니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.08946/extracted/6193388/figure/teaser_new.png)

> 🔼 본 그림은 논문에서 제안하는 PhysiCo 과제를 통해 '확률적 앵무새(Stochastic Parrot)' 현상을 보여주는 예시입니다.  PhysiCo 과제는 저수준(low-level) 및 고수준(high-level)의 두 가지 하위 과제로 구성됩니다. 그림에서는 '중력(Gravity)' 개념을 예시로 사용하여, 대규모 언어 모델(LLM)이 자연어로는 중력을 정확하게 설명할 수 있지만, 격자 형식(grid-format)의 그림으로 표현된 중력 개념은 해석하지 못하는 현상을 보여줍니다.  즉, LLM이 단순히 단어의 상관관계를 기반으로 답을 생성하는 '앵무새'와 같은 행동을 한다는 것을 시각적으로 보여주는 것입니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Illustration of a “Stochastic Parrot” by our PhysiCo task consisting of both low-level and high-level subtasks in parallel. For a concept Gravity, an LLM can generate its accurate description in natural language, but cannot interpret its grid-format illustration.
> </details>





{{< table-caption >}}
| (a) | Mistral | Llama-3 | GPT-3.5 | GPT-4 |
|---|---|---|---|---|
|  | 81.0±1.3 | 88.5±0.7 | 97.3±0.3 | 95.0±0.9 |
| (b) | InternVL | LLaVA | GPT-4v | GPT-4o |
|---|---|---|---|---|
|  | 66.3±7.7 | 66.7±5.8 | 93.7±0.9 | 93.7±0.5 |{{< /table-caption >}}

> 🔼 본 표는 논문의 5.1절 개념 선택 하위 과제에서 다룬 두 가지 유형의 하위 과제, 즉 텍스트 기반과 시각 기반 하위 과제에 대한 정확도를 보여줍니다.  텍스트 기반 하위 과제는 Wikipedia에서 가져온 개념의 정의를 사용하고 시각 기반 하위 과제는 Google 이미지 검색에서 얻은 실제 이미지를 사용합니다. 각 과제에 대해 여러 최첨단 LLMs의 성능을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Accuracy on the text-based (a) and visual-based (b) concept selection subtasks.
> </details>





### In-depth insights


#### Stochastic Parrot Effect
본 논문은 대규모 언어 모델(LLM)이 **확률적 앵무새 효과(Stochastic Parrot Effect)**를 보이는지에 대한 심층적인 분석을 제시합니다.  LLM이 표면적으로는 물리적 개념을 이해하는 것처럼 보이지만, 실제로는 훈련 데이터의 통계적 상관관계에만 의존하여 반응하는 현상을 탐구합니다.  **저자들은 이를 검증하기 위해, 격자 형식의 입력을 사용하여 물리적 현상을 추상적으로 표현하는 새로운 평가 기준인 PHYSICO를 제안합니다.** 이는 단순한 암기가 아닌 진정한 이해를 측정하기 위한 것입니다. 실험 결과, 최첨단 LLM들도 PHYSICO 과제에서 인간보다 현저히 낮은 성능을 보이며, **저수준 과제에서는 높은 정확도를 보이지만 고수준 과제에서는 실패하는 모습을 보여 확률적 앵무새 효과를 입증합니다.**  이는 LLM이 텍스트 간의 통계적 상관관계를 학습하여 답변을 생성하지만, 실제로는 개념에 대한 심층적인 이해가 부족함을 의미합니다.  **본 연구는 LLM의 한계를 명확히 제시하며, 진정한 이해를 측정하는 새로운 평가 방법의 중요성을 강조합니다.**

#### PHYSICO Benchmark
PHYSICO 벤치마크는 **LLM의 물리적 개념 이해 능력을 평가하기 위한 종합적인 평가 도구**입니다. 기존 연구들이 LLM의 언어 능력에만 집중한 것과 달리, PHYSICO는 **그리드 형식의 추상적 표현을 사용하여 암기 문제를 완화**하고 다양한 이해 수준을 평가합니다. 특히, **저수준 이해(단순 암기)와 고수준 이해(추론 및 응용)**를 구분하여 LLM의 진정한 이해 능력을 측정하는 데 초점을 맞춥니다.  **블룸의 분류 체계를 기반**으로 설계된 과제들은 LLM의 개념 이해 능력을 심도 있게 평가하고, **Stochastic Parrot 현상의 존재 여부를 정량적으로 검증**합니다.  **실험 결과, 최첨단 LLM들도 고수준 이해 과제에서 인간보다 상당히 낮은 성능을 보였으며, 단순 암기 능력만으로는 고수준 이해가 어렵다는 것을 시사**합니다. 이는 LLM의 한계를 명확히 보여주는 동시에, 향후 LLM의 물리적 개념 이해 능력 향상을 위한 연구 방향을 제시합니다.

#### Multimodal LLM Limits
다중 모드 LLM의 한계는 **모델의 훈련 데이터의 편향성과 제한된 이해 능력**에서 비롯됩니다.  영상이나 음성과 같은 다양한 모드의 데이터를 처리할 수 있지만, 이러한 데이터를 **통합적으로 이해하고 추론하는 능력은 여전히 부족**합니다. 특히, 추상적 개념이나 복잡한 상황을 요구하는 과제에서는 인간 수준의 성능을 보여주지 못하고 **단순한 패턴 매칭이나 표면적인 이해**에 그치는 경우가 많습니다.  **데이터의 질과 양적 한계, 그리고 모델의 복잡성** 또한 다중 모드 LLM의 성능 향상에 걸림돌이 됩니다.  따라서, **보다 풍부하고 다양한 데이터로의 훈련, 그리고 보다 정교한 모델 아키텍처의 개발**이 다중 모드 LLM의 한계를 극복하기 위한 중요한 과제입니다.  또한, **인간과의 상호작용과 피드백을 통해 모델의 이해 능력을 향상**시키는 방안에 대한 연구 또한 필요합니다.

#### Grid-World Abstraction
본 논문에서 제안하는 그리드 월드 추상화는 **물리적 개념을 시각적으로 표현하는 새로운 방법**입니다. 기존의 자연어 기반 질문응답 방식에서 벗어나, 그리드 형태의 입력을 사용하여 추상적인 패턴 인식 및 추론 능력을 평가합니다. 이는 단순한 암기 능력이 아닌, **진정한 이해 능력을 측정**하기 위한 시도이며,  LLM이  **물리적 현상을 얼마나 깊이 이해하는지**에 대한 통찰력을 제공합니다. 그리드 월드는 다양한 수준의 이해를 평가할 수 있도록 설계되어,  **저수준의 단순 패턴 인식부터 고수준의 추상적 개념 이해까지** 포괄적인 평가가 가능합니다.  **블룸의 분류 체계**를 기반으로 설계된 과제는 다양한 이해 수준을 효과적으로 측정하며, 그리드 형태의 입력은 암기 효과를 최소화합니다.  **이러한 추상화 기법은 기존의 자연어 텍스트 기반 방식의 한계를 극복**하고, LLM의 물리적 개념 이해에 대한 심도있는 연구를 가능하게 합니다.  결과적으로 그리드 월드 추상화는 LLM의 물리적 개념 이해 능력을 평가하는데 있어서 효과적인 도구임을 보여줍니다.

#### Future Research
본 논문은 대규모 언어 모델(LLM)의 물리적 개념 이해에 대한 심층적인 평가를 제시하며, 특히 **확률적 앵무새(Stochastic Parrot)** 현상을 정량적으로 규명하는 데 초점을 맞추고 있습니다.  미래 연구는 **다양한 유형의 개념과 복잡한 작업**에 대한 LLM의 이해 능력을 평가하는 방향으로 확장될 수 있습니다.  예를 들어, 추상적 사고, 인과 관계 이해, 그리고 상식적 지식을 필요로 하는 더욱 복잡한 물리적 시나리오를 고려하는 것이죠. 또한,  **LLM의 내부 메커니즘**에 대한 깊이 있는 분석을 통해 확률적 앵무새 현상의 근본 원인을 밝히고, 이를 개선하기 위한 효과적인 학습 방법을 개발하는 연구가 필요합니다.  **다중 모달 LLM의 성능 향상**에 대한 연구도 중요합니다. 시각, 청각 등 다양한 감각 정보를 통합하여 물리적 개념에 대한 이해도를 높일 수 있는 방법을 모색하는 연구가 진행되어야 합니다.  마지막으로, **인간의 물리적 개념 이해 과정**과의 비교 연구를 통해 LLM의 강점과 약점을 명확하게 파악하고, 이를 바탕으로 더욱 인간 친화적이고 효율적인 LLM을 개발하는 방향으로 나아가야 할 것입니다.


### More visual insights




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | Score |
|---|---| 
| Mistral | 92.6 |
| Llama-3 | 100 |
| GPT-3.5 | 100 |
| GPT-4 | 100 |{{< /table-caption >}}
> 🔼 본 표는 5.2절의 개념 생성 하위 작업에 대한 인간 평가 결과를 보여줍니다.  각 생성된 설명에 대해, 전문가 평가자가 사실적 오류나 부정확한 예시가 있는지 여부를 이진 점수(0 또는 1)로 평가했습니다.  1점은 사실적 오류나 부정확한 예시가 없는 경우, 0점은 그 반대의 경우를 의미합니다.  Mistral, Llama-3, GPT-3.5, GPT-4 모델들의 성능을 비교하여 각 모델의 생성된 설명의 정확성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Human evaluations on concept generation.
> </details>

{{< table-caption >}}
Model|Dev|Test-Core|Test-Assoc.
---|---|---|---
Random|25.0|25.0|25.0
GPT-3.5|26.5 ± 2.5|24.4 ± 0.8|30.0 ± 2.5
GPT-4|41.3 ± 1.3|28.2 ± 2.3|38.3 ± 1.2
GPT-4o|34.0 ± 2.9|31.3 ± 2.9|35.5 ± 2.5
o3-mini-high|46.0*|46.5|42.5
Mistral|21.5 ± 0.3|26.0 ± 1.4|23.2 ± 0.4
Llama-3|23.5 ± 2.5|27.3 ± 0.6|21.7 ± 2.0
DeepSeek-R1|41.5|29.5|55.0
GPT-4v|34.2 ± 1.6|28.7 ± 2.4|32.0 ± 1.5
GPT-4o|52.3 ± 0.8|45.2 ± 2.3|36.5 ± 0.4
+CoT|46.0 ± 2.5|43.5 ± 0.8|39.5 ± 1.1
o1|53.0|42.5|34.5
Gemini2 FTE|49.8 ± 0.8|43.2 ± 2.0|36.8 ± 3.1
InternVL|26.3 ± 1.6|26.9 ± 4.1|24.8 ± 1.3
LLaVA|26.2 ± 1.1|28.5 ± 1.5|24.7 ± 3.2
Humans|92.0 ± 4.3|89.5 ± 5.1|77.8 ± 6.3{{< /table-caption >}}
> 🔼 본 표는 논문에서 제시된 과제에 대한 다양한 텍스트 전용 및 멀티모달 LLM(대규모 언어 모델)의 성능을 비교 분석한 결과를 보여줍니다.  InternVL은 InternVL-Chat-V1-5를, LLaVA는 LLaVA-NeXT-34B를 나타냅니다. Gemini FTE는 Gemini 2.0 플래시 씽킹 실험 모델을 의미합니다. 표에는 최근 개발된 모델들을 나타내는 데 기울임꼴을 사용했습니다.  표에는 각 모델의 과제별 정확도(Accuracy)가 제시되어 있으며,  LLM의 유형(텍스트 전용 또는 멀티모달), 사용된 모델, 그리고 각 과제(CORE-Dev, CORE-Test, Assoc)에 대한 성능을 비교하여 LLM의 개념 이해 능력을 평가하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Performance of different text-only and multi-modal LLMs on our tasks. InternVL denotes InternVL-Chat-V1-5 and LLaVA denotes LLaVA-NeXT-34B. Gemini FTE refers to the Gemini 2.0 Flash Thinking Experimental model. We use italic fonts to refer to the recent thinking models.
> </details>

{{< table-caption >}}
| CoT - definitions | 46.0<sub>±2.5</sub> | CoT - low-level | 50.7<sub>±0.5</sub> |
{{< /table-caption >}}
> 🔼 표 4는 격자 형식의 데이터에 대한 문맥 학습 또는 미세 조정을 사용한 대규모 언어 모델(LLM)의 성능을 보여줍니다.  표는 다양한 LLM이 격자 형식 데이터에 대한 문맥 학습 또는 미세 조정을 통해 성능이 얼마나 향상되는지 또는 변화하는지를 보여줍니다.  특히,  다양한 전략(예: 다른 개념에 대한 문맥 학습, 합성 행렬 데이터에 대한 미세 조정, ARC 작업에 대한 미세 조정)을 사용한 결과를 비교하여, 격자 형식 데이터의 숙련도가 LLM 성능에 미치는 영향을 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Performance of LLMs with in-context learning or fine-tuning on grid-format data.
> </details>

{{< table-caption >}}
| Models | Core | Assoc. |
|---|---|---|
| GPT-4 | 41.3<sub>±1.3</sub> | 39.0<sub>±0.6</sub> |
|  w/ ICL-3-shot | 39.5<sub>±1.6</sub> | 36.2<sub>±1.7</sub> |
|  w/ ICL-9-shot | 32.8<sub>±1.0</sub> | 39.0<sub>±1.6</sub> |
| Mistral | 21.5<sub>±0.3</sub> | 23.2<sub>±0.4</sub> |
|  w/ FT on syn-tasks | 20.9<sub>±0.7</sub> | 22.5<sub>±0.5</sub> |
|  w/ FT on ARC | 20.9<sub>±0.8</sub> | 25.5<sub>±0.9</sub> |
| Llama-3 | 23.5<sub>±2.5</sub> | 21.7<sub>±2.0</sub> |
|  w/ FT on syn-tasks | 23.0<sub>±1.1</sub> | 23.2<sub>±2.7</sub> |
|  w/ FT on ARC | 22.2<sub>±1.6</sub> | 22.4<sub>±1.2</sub> |{{< /table-caption >}}
> 🔼 본 표는 Core 하위 작업과 중복되는 개념을 가진 Associative 하위 작업의 하위 집합에 대한 정확도를 보여줍니다.  Core 하위 작업과 개념이 겹치는 Associative 하위 작업의 일부에 대해서만 제한된 범위의 실험을 수행했으며, 이 표는 그 결과를 나타냅니다.  LLM들이 Core 하위 작업의 데이터를 이용하여 학습했을 때 Associative 하위 작업에서의 성능 변화를 보여주는 대조 실험 결과입니다.  보다 자세한 내용은 본문을 참고하시기 바랍니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Accuracy on the subset of Associative subtask that has overlapped concepts with Core.
> </details>

{{< table-caption >}}
| Model | Score ± std | Model | Score ± std | Model | Score ± std |
|---|---|---|---|---|---| 
| GPT-4 | 42.9 ± 2.4 | GPT-4o | 40.4 ± 2.1 | Llama-3 | 22.1 ± 2.8 |
| + ICL on Core | 40.0 ± 1.0 | + ICL on Core | 37.1 ± 2.6 | + SFT on Core | 20.9 ± 2.7 |{{< /table-caption >}}
> 🔼 이 표는 논문의 PHYSICO-CORE-Dev 데이터셋에 포함된 개념들과 각 개념에 대한 인스턴스 수를 보여줍니다.  PHYSICO-CORE-Dev는 고등학교 수준의 기본적인 물리 개념들을 평가하기 위해 설계된 하위 과제이며, 이 표는 해당 하위 과제에 사용된 개념들의 종류와 각 개념별 데이터 양을 한눈에 파악하는 데 도움을 줍니다.  각 개념에 대한 인스턴스 수는 해당 개념과 관련된 문제(또는 예시)의 개수를 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Concepts and their corresponding number of instances in PhysiCo-Core-Dev.
> </details>

{{< table-caption >}}
| Model | Mistral | Llama-3 | GPT-3.5 | GPT-4 |
|---|---|---|---|---|
| Human | 92.6 | 100 | 100 | 100 |
| SP | 89.2 ± 1.6 | 91.9 ± 0.6 | 96.0 ± 0.4 | 99.8 ± 0.2 |{{< /table-caption >}}
> 🔼 이 표는 논문의 PHYSICO-CORE-Test 데이터셋에 포함된 개념들과 각 개념에 해당하는 인스턴스의 수를 보여줍니다.  PHYSICO-CORE-Test는 고등학교 수준의 기본적인 물리 개념들을 평가하기 위해 디자인된 하위 과제이며, 각 개념에 대해 다양한 수준의 이해를 평가하는 여러 문제들이 포함되어 있습니다. 표에는 각 개념에 대해 몇 개의 문제가 있는지를 나타내어, 데이터셋의 규모와 다양성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Concepts and their corresponding number of instances in PhysiCo-Core-Test.
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