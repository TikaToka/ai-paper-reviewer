---
title: "Enhancing Automated Interpretability with Output-Centric Feature Descriptions"
summary: "출력 중심적 특징 설명으로 자동화된 설명가능성 파이프라인 개선!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Blavatnik School of Computer Science and AI, Tel Aviv University",]
showSummary: true
date: 2025-01-14
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.08319 {{< /keyword >}}
{{< keyword icon="writer" >}} Yoav Gur-Arieh et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-15 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.08319" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.08319" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/enhancing-automated-interpretability-with" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)의 특징을 이해하는 것은 자연어 처리 분야의 중요한 과제입니다. 기존의 자동화된 설명가능성 파이프라인은 주로 입력 중심적 접근 방식을 사용하여 특징을 활성화하는 입력을 중심으로 설명을 생성합니다. 하지만 이러한 접근 방식은 특징의 **인과적 역할(causal role)**을 충분히 포착하지 못하고, **비용이 많이 들며 설명의 정확성이 떨어지는 문제점**을 가지고 있습니다.  또한, 특징 활성화 입력을 얻기 어려운 경우에도 설명 생성이 어렵다는 단점이 있습니다.

본 논문에서는 이러한 문제점을 해결하기 위해 **출력 중심적(output-centric)** 방법론을 제안합니다.  **VocabProj** 와 **TokenChange** 와 같은 새로운 방법론은 모델의 출력 분포 변화에 초점을 맞춰 특징 설명을 생성합니다.  이 방법은 입력 중심적 방법보다 **계산 효율성이 높고 인과적 역할을 더 잘 반영**하는 특징 설명을 생성합니다.  실험 결과는 제안된 방법론이 기존 방법보다 **입력 및 출력 평가 모두에서 더 나은 성능**을 보임을 보여줍니다.  특히, 출력 중심적 방법론은 기존에 ‘죽은(dead)’ 특징으로 간주되었던 특징에 대한 입력을 찾는 데에도 효과적임을 확인하였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 입력 중심적 접근 방식의 한계를 극복하는 **출력 중심적 특징 설명** 방법론 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} **VocabProj** 와 **TokenChange** 와 같은 효율적인 출력 중심적 방법론을 통해 **정확도 향상** {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} **입력 및 출력 평가**를 통한 종합적인 성능 평가 및 **새로운 통찰력** 제공 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **자동화된 설명가능성(interpretability)** 파이프라인을 향상시키는 데 중요한 의미를 지닙니다. **출력 중심적(output-centric)** 방법론을 제시하여 기존의 입력 중심적 접근 방식의 한계를 극복하고, **더욱 정확하고 효율적인 특징 설명**을 생성합니다.  이는 다양한 자연어 처리 모델의 이해와 제어에 큰 영향을 미치며, 향후 연구의 새로운 방향을 제시합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.08319/x1.png)

> 🔼 그림 1은 특징에 대한 충실한 설명은 특징을 활성화하는 모델 입력(왼쪽, 표시된 단어는 가장 높은 활성화를 유발함)과 특징이 모델 출력에 미치는 영향(오른쪽) 모두를 고려해야 한다는 점을 보여줍니다. 왼쪽에는 특징을 활성화하는 입력 단어들이, 오른쪽에는 특징 활성화가 모델 출력에 어떤 영향을 미치는지 보여주는 단어들이 제시되어 있습니다. 이는 단순히 특징을 활성화하는 입력만으로는 특징을 완전히 설명할 수 없다는 점을 강조합니다. 충실한 설명을 위해서는 입력과 출력 양쪽 모두를 고려해야 특징의 역할을 제대로 이해할 수 있다는 것을 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: We posit that a faithful description of a feature should consider both model inputs that activate it (left, marked words cause the highest activations) and the effect it introduces to the model’s outputs (right).
> </details>





{{< table-caption >}}
| Method           | Gemma-2 Res. SAE |       | Gemma-2 MLP SAE |       | Llama-3.1 Res. SAE |       | Llama-3.1 Inst. MLP |       |
|--------------------|-------------------|-------|-------------------|-------|--------------------|-------|----------------------|-------|
|                   | Input             | Output | Input             | Output | Input              | Output | Input                 | Output |
| MaxAct            | 56.6 ± 2.2         | 49.2 ± 2.2         | 50.4 ± 2.2         | 35.1 ± 2.1         | 30.3 ± 2.7          | 71.8 ± 2.6          | 85.6 ± 1.4              | 36.9 ± 1.9              |
| MaxAct++          | -                 | -      | -                 | -      | -                  | -      | **89.8 ± 1.2**         | 39 ± 1.9                |
| VocabProj         | 50.1 ± 2.2         | 56.5 ± 2.2         | 20.9 ± 1.8         | 37.2 ± 2.1         | 18.2 ± 2.2          | 64.2 ± 2.8          | 71.2 ± 1.8              | **45.8 ± 1.9**         |
| TokenChange       | 44.7 ± 2.2         | 54.9 ± 2.2         | 22.3 ± 1.8         | 40.3 ± 2.2         | 21.4 ± 2.4          | 72.0 ± 2.6          | 74 ± 1.7                | 43.8 ± 1.9              |
| EnsembleR (MA+VP) | **66.9 ± 2.1**     | 52 ± 2.2           | **56.6 ± 2.2**     | 38.6 ± 2.1         | **36.9 ± 2.8**        | 68.9 ± 2.7          | **86.7 ± 1.3**          | 40.7 ± 1.9              |
| EnsembleR (MA+TC) | **67 ± 2.1**       | 61.9 ± 2.1         | **56.4 ± 2.2**     | 46.2 ± 2.2         | **37.2 ± 2.8**        | 68.0 ± 2.7          | **87.2 ± 1.3**          | 41.7 ± 1.9              |
| EnsembleR (VP+TC) | 53.1 ± 2.2         | 63 ± 2.1           | 24.3 ± 1.9         | 46.6 ± 2.2         | 20.9 ± 2.3          | 67.4 ± 2.7          | 72.4 ± 1.7              | **44.3 ± 1.9**         |
| EnsembleR (All)   | **66.6 ± 2.1**     | **64.9 ± 2.1**     | **55.7 ± 2.2**     | **48.7 ± 2.2**     | **36 ± 2.8**          | 71.2 ± 2.6          | **86.2 ± 1.3**          | 41.8 ± 1.9              |
| EnsembleC (All)   | 57.7 ± 2.2         | **66.9 ± 2.1**     | 31.6 ± 2.1         | **49.9 ± 2.2**     | 28.5 ± 2.6          | **75.4 ± 2.5**         | 84.9 ± 1.4              | **44.6 ± 1.9**         |{{< /table-caption >}}

> 🔼 표 1은 다양한 특징 유형 및 모델에 걸쳐 평균화된 계층과 해당 95% 신뢰 구간을 포함하여 제안된 방법 및 앙상블의 입력 및 출력 기반 평가 결과를 보여줍니다. SAE 특징의 경우 모든 크기의 SAE에서 특징의 평균을 사용합니다. MaxAct는 MA로, VocabProj는 VP로, TokenChange는 TC로, EnsembleR과 EnsembleC는 원시 및 연결 기반 앙상블을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Input- and output-based evaluation results of the methods and their ensembles, over different feature types and models, averaged across model layers, along with their respective 95% confidence intervals. For SAE features we take the average over features from SAEs of all sizes. We denote MA for MaxAct, VP for VocabProj, TC for TokenChange, and EnsembleR and EnsembleC for the raw and concatenation based ensembles.
> </details>





### In-depth insights


#### Output-Centric NLP
**출력 중심 NLP**는 기존의 입력 중심 접근 방식과 달리, 언어 모델의 출력에 초점을 맞춰 모델의 동작 방식을 이해하고자 하는 새로운 패러다임입니다.  **기존 입력 중심 방식**은 모델의 특정 기능을 활성화하는 입력 데이터를 분석하지만, **출력 중심 방식**은 모델의 출력에 미치는 기능의 인과적 영향에 중점을 둡니다. 이는 모델이 어떻게 입력을 처리하고 출력을 생성하는지에 대한 보다 심층적인 이해를 제공합니다.  **입력과 출력 모두를 고려하는 혼합 접근 방식**은 더욱 정확하고 포괄적인 모델 해석을 가능하게 할 것입니다.  **효율적인 출력 중심 방법론**의 개발은 대규모 언어 모델의 해석 가능성을 높이고, 모델의 동작을 제어하는 새로운 방법을 제시할 수 있습니다.  특히, **'사용되지 않는' 기능을 발견하고 활성화**하는 데 효과적이며, 향후 **모델 스티어링 및 설명 가능한 AI 개발**에 중요한 역할을 할 것으로 예상됩니다.  **다양한 유형의 특징들(뉴런, SAE 등)**에 대한 실험을 통해 출력 중심 접근 방식의 효용성을 검증하고, **입력 중심 방식과의 비교 분석**을 통해 각 방식의 강점과 약점을 명확히 파악해야 합니다.  궁극적으로, 출력 중심 NLP는 **언어 모델의 투명성과 신뢰성을 향상시키는 데 크게 기여**할 것으로 전망됩니다.

#### Causal Feature Roles
**인과적 특징 역할**에 대한 심층적인 논의는 언어 모델의 내부 동작을 이해하는 데 중요한 부분입니다. 단순히 특징의 활성화 패턴만 분석하는 것이 아니라, **입력이 특징을 활성화하는 과정과 활성화된 특징이 출력에 영향을 미치는 인과적 메커니즘**을 밝히는 것이 중요합니다. 이를 통해 모델의 예측 결과에 대한 좀 더 정확하고 심층적인 설명을 제공할 수 있으며, **모델의 행동을 조절하고 제어하는 데 활용**할 수 있습니다.  본 연구에서는 이러한 인과적 메커니즘을 효과적으로 파악하기 위한 새로운 방법론을 제시하며, 기존의 입력 중심적 접근 방식의 한계를 극복하고, **출력 중심적 분석을 통해 더욱 정확하고 효율적인 특징 설명**을 얻을 수 있음을 보여줍니다. 특히, '죽은' 특징이라 불리는 활성화되지 않는 특징에 대한 새로운 해석과 활성화 방안을 제시하여, 언어 모델 해석의 범위를 넓히고, **모델의 투명성과 신뢰성을 향상**시키는 데 기여할 것으로 기대됩니다.

#### Efficient Interpretability
 효율적인 해석가능성이란, **대규모 언어 모델(LLM)의 내부 동작을 이해하기 위한 해석 방법의 효율성**을 높이는 것을 의미합니다.  본 논문에서는 입력 중심적 방법론의 한계를 극복하고, **출력 중심적 방법론**을 제시하여 계산 비용을 절감하는 동시에 모델의 출력에 미치는 특징의 인과적 영향을 더 잘 포착합니다.  **VocabProj와 TokenChange**는 각각 특징의 어휘 공간 투영 및 토큰 확률 변화를 활용하여 효율적으로 특징을 설명합니다.  **입력 및 출력 기반 평가를 통해** 기존 방법보다 우수한 성능을 보임을 확인하였고, 두 방법의 결합이 최상의 성능을 달성합니다.  결론적으로, 본 논문의 접근법은 **해석가능성 향상과 계산 효율성 개선**이라는 두 마리 토끼를 동시에 잡는 효과적인 전략을 제시합니다.  특히, **기존 방법으로는 발견하기 어려운 ‘잠재 특징’을 효율적으로 찾아내는 데에도 기여**할 수 있다는 점에서 큰 의의를 지닙니다.

#### Ensemble Methods
본 논문에서 제시된 앙상블 방법은 **단일 방법보다 우수한 성능**을 보입니다. 입력 중심 및 출력 중심 방법을 결합함으로써 입력 및 출력 평가 모두에서 최고의 성능을 달성합니다. 이는 **입력 중심적 접근 방식만으로는 언어 모델의 특징을 충분히 포착하지 못한다는 점**을 시사합니다.  **출력 중심적 접근 방식은 모델 출력에 대한 특징의 인과적 영향을 더 잘 포착**하지만, 두 접근 방식을 결합하면 입력 및 출력 평가 모두에서 최고의 성능을 얻을 수 있습니다. 특히, VocabProj와 TokenChange는 MaxAct보다 훨씬 계산 효율적이며, 특정 상황에서는 MaxAct에 준하는 성능을 보이면서도 훨씬 저렴한 대안으로 사용될 수 있습니다.  앙상블 기법을 통해  **'죽은' 특징을 효과적으로 발견하여 활성화하는 입력을 찾을 수 있다는 점**도 중요한 발견입니다.  이러한 결과는 자동화된 해석 가능성 파이프라인에 출력 중심적 방법을 통합하는 것이 중요함을 보여줍니다.

#### Future Directions
본 논문은 대규모 언어 모델(LLM)의 특징에 대한 자동화된 해석 가능성을 향상시키는 방법을 제시하며, 특히 **출력 중심적 특징 설명**의 중요성을 강조합니다. 미래 연구 방향으로는 다음 세 가지를 제시할 수 있습니다. 첫째, **더욱 정교한 평가 지표** 개발입니다. 본 논문에서 제시된 입력 및 출력 중심 평가는 유용하지만, LLM의 복잡성을 완전히 포착하지 못할 수 있습니다. 따라서, 다양한 측면을 고려하는 보다 포괄적인 평가 방법이 필요합니다.  둘째, **다양한 모델 및 특징 유형**에 대한 일반화 가능성을 높이는 것입니다.  본 논문은 특정 모델과 특징에 대한 실험 결과를 제시하지만, 다른 모델 및 특징 유형에서도 동일한 효과를 보이는지 확인할 필요가 있습니다. 마지막으로, **효율적인 설명 생성 기법**에 대한 연구가 필요합니다. 본 논문에서 제안된 방법은 계산 효율성을 고려했지만, 더욱 빠르고 효율적인 설명 생성 기법을 개발하는 연구가 지속되어야 LLM 해석 가능성 연구가 더욱 확장될 수 있습니다. 특히, **설명의 품질**을 높이기 위한 연구도 중요합니다. 현재의 설명 생성 방법은 때때로 모호하거나 불완전한 경우가 있으므로, 보다 정확하고 이해하기 쉬운 설명을 생성하는 기법이 필요합니다.  이는 향후 LLM의 신뢰성 및 투명성을 향상시키는 데 크게 기여할 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.08319/x2.png)

> 🔼 이 그림은 제안된 특징 설명 평가 방법을 보여줍니다.  이 방법은 모델의 입력(중간 패널)과 출력(아래 패널) 두 가지 측면 모두에서 특징 설명의 정확성을 평가합니다.  중간 패널에서는 특징을 활성화하는 입력을 얼마나 잘 캡처하는지 평가하고, 아래 패널에서는 특징 활성화가 모델 출력에 미치는 영향을 얼마나 잘 반영하는지 평가합니다.  두 가지 평가를 통해 모델의 특징 표현에 대한 더욱 포괄적인 이해를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Illustration of our feature description evaluation, considering the description’s faithfulness with respect to both the input (middle panel) and output (lower panel) of the model.
> </details>



![](https://arxiv.org/html/2501.08319/x3.png)

> 🔼 그림 (a)는 Gemma-2 모델의 잔차 스트림에서 추출한 너비 65k의 SAE(Sparse Autoencoder) 특징들을 보여줍니다.  SAE는 고차원의 데이터를 저차원의 특징 벡터로 효율적으로 변환하는 신경망으로, 본 논문에서는 언어 모델의 내부 표현을 이해하는 데 사용되었습니다.  이 그림은  특징들의 분포나 특징들의 활성화 패턴 등을 시각적으로 보여주어,  해당 특징들이 모델의 동작에 어떻게 영향을 미치는지를 분석하는 데 도움을 줄 수 있습니다.  각 막대는 특정 특징을 나타내며,  그 높이는 해당 특징의 활성화 정도 또는 중요도를 나타낼 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (a) Residual stream SAE features of width 65k from Gemma-2.
> </details>



![](https://arxiv.org/html/2501.08319/x4.png)

> 🔼 그림 (b)는 Gemma-2 모델에서 추출한 폭이 65k인 MLP SAE 특징을 보여줍니다. MLP(다층 퍼셉트론)는 인공 신경망의 한 유형이며, SAE(희소 자기 인코더)는 고차원 데이터를 저차원으로 효율적으로 표현하는 데 사용되는 기술입니다. 이 그림은 모델의 다양한 계층에서 추출된 특징들의 입력 및 출력 기반 평가 결과를 보여주는 일련의 그림들 중 하나입니다.  각 특징에 대한 설명이 입력(특징을 활성화하는 입력값)과 출력(특징 활성화가 모델 출력에 미치는 영향) 두 가지 관점에서 얼마나 정확하게 묘사되는지를 보여줍니다. 이는 모델의 내부 동작을 이해하는 데 중요한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> (b) MLP SAE features of width 65k from Gemma-2.
> </details>



![](https://arxiv.org/html/2501.08319/x5.png)

> 🔼 그림 (c)는 Llama-3.1 모델의 잔차 스트림에서 추출한 너비 32k의 SAE 특징을 보여줍니다.  SAE(Sparse Autoencoder)는 고차원 데이터를 저차원으로 효율적으로 표현하는 인코딩 및 디코딩 과정을 거치는 신경망입니다. 이 그림은 Llama-3.1 모델의 잔차 스트림 내부의 특징 표현을 분석하여, 각 특징이 모델의 입력과 출력에 미치는 영향을 시각화한 결과를 보여줄 것으로 예상됩니다. 이를 통해 모델의 내부 동작 방식에 대한 이해를 높이고, 특정 특징에 대한 해석 가능성을 향상시킬 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (c) Residual stream SAE features of width 32k from Llama-3.1.
> </details>



![](https://arxiv.org/html/2501.08319/x6.png)

> 🔼 그림 (d)는 Llama-3.1 8B Instruct 모델의 MLP(다층 퍼셉트론) 특징을 보여줍니다. 이 그림은 다양한 방법(MaxAct, VocabProj, TokenChange 및 여러 가지 앙상블 방법)을 사용하여 특징을 설명하고, 입력 기반 평가와 출력 기반 평가를 통해 각 방법의 성능을 비교 분석한 결과를 나타냅니다.  입력 기반 평가는 특징을 활성화하는 입력을 얼마나 정확하게 식별하는지를 측정하고, 출력 기반 평가는 모델 출력에 대한 특징의 인과적 영향을 얼마나 효과적으로 포착하는지를 평가합니다. 이를 통해 각 방법의 강점과 약점, 그리고 입력 중심 방법과 출력 중심 방법을 결합했을 때 얻을 수 있는 시너지 효과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (d) MLP features from Llama-3.1 8B Instruct.
> </details>



![](https://arxiv.org/html/2501.08319/x7.png)

> 🔼 그림 3은 제안된 평가 지표에 대한 다양한 방법들의 성능을 보여줍니다. Gemma-2 2B(상단), Llama-3.1 8B(하단 왼쪽), Llama-3.1 8B Instruct(하단 오른쪽) 세 가지 모델에 대해 입력 기반 및 출력 기반 평가를 수행했습니다. 출력 지표의 경우, 기준선(점선)은 1/3입니다. 이는 평가를 위해 세 가지 텍스트 집합 중 하나를 선택하는 LLM 판단자 때문입니다. 각 그래프는 입력 기반 평가와 출력 기반 평가의 정확도를 층별로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Performance of the various methods on the proposed metrics, for Gemma-2 2B (upper row), Llama-3.1 8B (lower left), and Llama-3.1 8B Instruct (lower right). For the output metric, the baseline (dashed black line) is 1/3131/31 / 3 since the judge LLM picks between three sets of texts.
> </details>



![](https://arxiv.org/html/2501.08319/x8.png)

> 🔼 그림 4는 본 논문의 입력 기반 평가에서 판정용 LLM에 주어지는 프롬프트를 보여줍니다.  LLM은 주어진 특징에 대한 설명을 받고, 그 특징을 활성화시키는 예시와 활성화시키지 않는 예시를 각각 5개씩 생성해야 합니다.  활성화 예시는 해당 특징을 강하게 활성화시키는 문장이어야 하며, 비활성화 예시는 해당 특징과 관련이 없는 문장이어야 합니다. 생성된 문장들은 모델에 입력되어 각 문장에 대한 특징의 활성화 정도를 측정하고, 이를 통해 설명의 정확성을 평가합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Prompt given to the judge LLM for the input-based evaluation.
> </details>



![](https://arxiv.org/html/2501.08319/x9.png)

> 🔼 그림 5는 본 논문의 출력 기반 평가에서 사용된 평가자 LLM 프롬프트를 보여줍니다.  프롬프트는 평가자가 특정 뉴런의 활성화 증폭 시 생성된 세 개의 텍스트 집합 중 어떤 것이 해당 뉴런의 설명과 가장 일치하는지 판단하는 데 사용됩니다. 각 집합에는 뉴런의 활성화를 증폭한 경우와 무작위 뉴런을 증폭한 경우에 생성된 텍스트가 포함됩니다. 프롬프트는 평가자가 텍스트 내용을 기반으로 판단하도록 안내하고, 언어 모델 출력의 품질보다는 내용 일치도에 중점을 두도록 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Prompt given to the judge LLM for the output-based evaluation.
> </details>



![](https://arxiv.org/html/2501.08319/x10.png)

> 🔼 이 그림은 논문의 VocabProj 방법에 대한 설명을 생성하는 데 사용된 프롬프트를 보여줍니다.  프롬프트는 특정 벡터와 관련된 토큰 목록을 제공받아, 이를 기반으로 벡터의 의미나 기능을 추론하도록 설계되었습니다.  프롬프트는  관련 없는 용어나 기호를 무시하고,  가장 관련성이 높은 토큰들 사이의 일관된 주제나 개념을 파악하도록 지시합니다.  최종적으로 벡터의 의미나 기능을 요약하는 간결한 문장을 생성하는 것을 목표로 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Prompt given to the explainer model for the VocabProj method.
> </details>



![](https://arxiv.org/html/2501.08319/x11.png)

> 🔼 그림 7은 VocabProj에 의해 생성된 설명('게임, 플레이어, 게임플레이 및 게임 메커니즘에 중점을 둔 게임')을 사용하여 활성화된, 이전에는 비활성으로 간주되었던 특징을 증폭시켰을 때 생성된 텍스트를 보여줍니다.  이 그림은 '죽은' 특징으로 분류된 특징이 적절한 설명과 입력을 통해 활성화될 수 있음을 보여주는 사례를 제시합니다.  즉, 단순히 입력 데이터에서 활성화되지 않는다고 해서 특징이 무의미하다는 것을 의미하지는 않으며,  적절한 방법으로 접근하면 그 기능을 이해하고 활용할 수 있다는 점을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Text generated when amplifying a feature pronounced to be dead, which we managed to activate using the explanation generated by VocabProj, which was “gaming, focusing on players, gameplay, and game mechanics”.
> </details>



![](https://arxiv.org/html/2501.08319/x12.png)

> 🔼 그림 3(a)는 Llama-3.1 모델의 32k 너비의 MLP SAE 특징을 보여줍니다.  이 그림은 다양한 특징 기술 방법 (MaxAct, VocabProj, TokenChange 및 앙상블)의 입력 및 출력 기반 평가 결과를 보여주는 막대 그래프입니다. 각 막대는 특정 방법의 정확도를 나타내며, 입력 기반 평가와 출력 기반 평가의 결과를 비교하여 모델 해석의 정확성을 평가합니다. 계층 그룹별 결과를 보여주어 모델의 서로 다른 계층에서의 해석 성능 차이를 분석합니다.
> <details>
> <summary>read the caption</summary>
> (a) MLP 32k SAE features from Llama-3.1.
> </details>



![](https://arxiv.org/html/2501.08319/x13.png)

> 🔼 그림 (b)는 GPT-2 small 모델의 중간 잔차 스트림에서 추출한 32k 크기의 SAE(Sparse AutoEncoder) 특징들을 보여줍니다.  SAE는 고차원의 데이터를 저차원의 특징으로 변환하는데 사용되는 기법이며, 이 그림에서는 GPT-2 small 모델의 중간 층에서 추출된 32,000개의 특징 벡터들을 시각화한 것으로 보입니다.  각 특징 벡터는 모델의 내부 표현을 반영하며, 이 그림은 해당 특징들의 분포나 특징 간의 관계를 보여주는 것으로 추정됩니다. 이를 통해 모델의 내부 동작에 대한 이해를 높일 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (b) Mid residual stream 32k SAE features from GPT-2 small.
> </details>



![](https://arxiv.org/html/2501.08319/x14.png)

> 🔼 이 그림은 GPT-2 small 모델의 잔차 스트림에서 추출한 32k 크기의 SAE 특징들을 보여줍니다.  SAE(Sparse Autoencoder)는 고차원 데이터를 저차원으로 효율적으로 압축하는 기술입니다. 잔차 스트림은 모델의 여러 레이어에서 나온 중간 표현들을 나타냅니다.  이 그림은 이러한 특징들의 분포나 특징들을 분석하는데 사용된 방법의 결과를 보여주는 시각화일 가능성이 높습니다. 그림 자체는  본문에서 설명하는 방법론의 성능 평가에 활용된 결과를 보여주는 하나의 시각적 요소일 것입니다.
> <details>
> <summary>read the caption</summary>
> (c) Residual stream 32k SAE features from GPT-2 small.
> </details>



![](https://arxiv.org/html/2501.08319/x15.png)

> 🔼 그림 (d)는 GPT-2 small 모델의 32k 차원의 희소 자동 인코더(SAE) 특징을 다룬 MLP 레이어의 결과를 보여줍니다. 이는 맥락을 고려하여 특징이 어떻게 모델 출력에 영향을 미치는지 보여주는 출력 중심적 방법론을 평가하기 위한 실험 결과의 일부입니다.  MaxAct, VocabProj, TokenChange 세 가지 방법론과 이들의 앙상블을 사용하여 생성된 특징 설명의 입력 기반 및 출력 기반 평가 결과를 보여주는 여러 그래프 중 하나입니다.
> <details>
> <summary>read the caption</summary>
> (d) MLP 32k SAE features from GPT-2 small.
> </details>



![](https://arxiv.org/html/2501.08319/x16.png)

> 🔼 그림 8은 제안된 평가 지표에 대한 다양한 방법들의 성능을 보여줍니다. Llama-3.1 8B(좌측 상단)과 GPT-2 small(우측 상단 및 하단) 모델에 대해 입력 기반 및 출력 기반 평가를 수행했습니다. 출력 기반 평가의 경우, 기준선(점선)은 1/3입니다. 이는 평가 LLM이 세 개의 텍스트 집합 중 하나를 선택하기 때문입니다. 그림은 각 방법의 입력 및 출력 기반 평가 점수를 비교하여 어떤 방법이 입력과 출력 모두에서 더 나은 성능을 보이는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Performance of the various methods on the proposed metrics, for Llama-3.1 8B (upper left) and GPT-2 small (upper right and lower row). For the output metric, the baseline (dashed black line) is 1/3131/31 / 3 since the judge LLM picks between three sets of texts.
> </details>



![](https://arxiv.org/html/2501.08319/x17.png)

> 🔼 본 그림은 세 가지 모델(Gemma-2 2B, Llama-3.1 8B, GPT-2 small)에 대해, 각 모델의 특징을 나타내는 토큰들과 해당 토큰에 대한 설명을 보여줍니다. 이러한 토큰들과 설명들은 기본 프롬프트에 추가되어 미세 조정된 프롬프트를 만드는 데 사용되었습니다.  각 모델마다 세 가지 벡터(Vector 1, Vector 2, Vector 3)에 대한 토큰 목록과 이를 설명하는 문장이 제시되어 있습니다. 이는 각 벡터가 나타내는 개념을 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Three demonstrations of tokens and their descriptions for each model, added to the base prompt forming a fine-tuned prompt.
> </details>



![](https://arxiv.org/html/2501.08319/x18.png)

> 🔼 그림 10은 Ensemble Raw 방법에 대한 설명 모델에 제공되는 프롬프트를 보여줍니다. 이 프롬프트는 신경망에서 뉴런의 동작을 설명하기 위해 설계되었습니다.  프롬프트는 뉴런의 입력과 출력을 모두 고려하여, 입력 활성화 값과 출력에 가장 관련있는 단어 목록을 함께 제시합니다.  설명 모델은 이 정보를 바탕으로 뉴런의 기능을 간략하게 설명하는 문장을 생성합니다.  입력 활성화 값은 0에서 10까지의 범위를 가지며, 0이 아닌 값은 뉴런이 특정 입력을 감지했음을 나타냅니다.  값이 높을수록 더 강한 일치를 의미합니다.  출력 단어 목록은 해당 뉴런의 벡터를 재구성하는 임베딩들의 조합을 나타내며, 관련 없는 단어나 기호가 포함될 수 있습니다.  설명 모델은 이러한 정보를 분석하여 뉴런의 주요 기능을 요약하는 문장을 생성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Prompt given to the explainer model for the Ensemble Raw method.
> </details>



![](https://arxiv.org/html/2501.08319/x19.png)

> 🔼 그림 11은 VocabProj 기법에 미세 조정된 프롬프트의 기본 형태를 보여줍니다. 이 프롬프트는 특정 벡터와 관련된 토큰 목록을 입력으로 받습니다. 이 토큰들은 벡터를 재구성하는 임베딩의 조합을 나타냅니다.  목표는 이러한 토큰들을 바탕으로 벡터의 의미나 기능을 추론하는 것입니다.  목록에는 무관한 용어, 기호 또는 프로그래밍 전문 용어와 같은 노이즈가 포함될 수 있습니다.  모델은 여러 언어의 단어가 섞여 있어도 이를 무시하고, 가장 관련성이 높은 토큰들이 공유하는 일관된 주제나 개념을 파악해야 합니다.  최종 응답은 벡터의 의미나 기능을 요약하는 간결한 문장이어야 합니다.  너무 일반적이거나 광범위한 답변은 피해야 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: The basic fine-tuned prompt VocabProj method.
> </details>



![](https://arxiv.org/html/2501.08319/x20.png)

> 🔼 그림 12는 본 논문의 출력 기반 평가 지표에 사용된 조종된 텍스트 집합의 예시를 보여줍니다.  출력 기반 평가는 특정 특징의 활성화가 모델 출력에 미치는 영향을 평가하는 데 중점을 둡니다. 이 그림은 다양한 강도의 특징 활성화(예: 저, 중, 고) 하에서 모델이 생성한 텍스트를 보여줍니다. 이를 통해 연구자들은 특징 활성화의 정도에 따라 모델 출력이 어떻게 변하는지 확인하고, 특징 설명의 정확성을 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: An example of steered text set for the output-based metric.
> </details>



![](https://arxiv.org/html/2501.08319/x21.png)

> 🔼 그림 13은 VocabProj 기법에 대한 일반적인 프롬프트의 첫 번째 변형을 보여줍니다. 이 프롬프트는 특정 벡터와 관련된 일련의 토큰을 입력으로 받아 해당 벡터의 의미 또는 기능을 추론하는 것을 목표로 합니다.  프롬프트는 관련 없는 용어, 기호 또는 프로그래밍 전문 용어를 포함할 수 있는 토큰 목록을 제공합니다.  모델은 입력 토큰에서 가장 관련성이 높은 토큰을 식별하고, 해당 토큰들을 통해 벡터의 의미 또는 기능을 요약하는 구문을 생성해야 합니다.  이 프롬프트는 여러 언어로 된 단어가 포함된 경우에도 단어의 언어를 고려하지 않고, 오직 의미나 개념에 집중하도록 설계되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: A first variant of a generic prompt for the VocabProj method.
> </details>



![](https://arxiv.org/html/2501.08319/x22.png)

> 🔼 그림 14는 VocabProj 방법에 사용되는 일반적인 프롬프트의 두 번째 변형을 보여줍니다. 이 프롬프트는 모델이 특정 벡터와 관련된 토큰 목록을 분석하고, 관련 없는 토큰이나 노이즈를 제거하고, 해당 벡터의 의미 또는 기능을 요약하는 간결한 문장을 생성하도록 합니다.  프롬프트는 모델이 여러 언어의 단어가 섞여 있어도 이를 고려하지 않고, 주요 토큰의 일관된 주제나 개념을 파악하여 요약하도록 지시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: A second variant of a generic prompt for the VocabProj method.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Relation | Example feature | Description by `MaxAct` | Description by `VocabProj` |
|---|---|---|---| 
| Similar <img src="https://arxiv.org/html/2501.08319/S6.T2.1.1.1.1.1.pic1.png" width="32.07" height="17.85"> | `3-MLP-16K/ 4878` | Terms and themes related to various genres of storytelling, particularly in horror, drama, and fantasy. | A blend of themes and genres commonly found in storytelling or media, with a specific focus on dramatic, horror, and suspenseful narratives. |
| Composition <img src="https://arxiv.org/html/2501.08319/S6.T2.2.2.1.1.1.pic1.png" width="32.07" height="17.85"> | `19-MLP-16K/ 5635` | References to political events and milestones. | Concepts related to time measurement such as days, weeks, weekends, and months, indicating it likely pertains to scheduling or planning events. |
| Abstraction <img src="https://arxiv.org/html/2501.08319/S6.T2.3.3.1.1.1.pic1.png" width="32.07" height="17.85"> | `21-RES-16K/ 10714` | Information related to bird species and wildlife activities. | Concepts related to birdwatching and ornithology, focusing on activities such as observing, spotting, and recording bird species in their natural habitats. |
| Different <img src="https://arxiv.org/html/2501.08319/S6.T2.4.4.1.1.1.pic1.png" width="32.07" height="17.85"> | `19-MLP-16K/ 1450` | Mentions of notable locations, organizations, or events, particularly in various contexts. | Concepts related to self-reflection, purpose, and generalization in various contexts, focusing on the exploration of identity and overarching themes in literature or philosophy. |{{< /table-caption >}}
> 🔼 이 표는 Gemma Scope의 SAE 특징 100개에 대한 MaxAct와 VocabProj에 의해 생성된 설명에 대한 사람의 평가 결과를 보여줍니다. 각 관계 범주(유사, 구성, 추상화, 상이)에 대해 관찰된 경우의 비율과 예시 특징에 대한 설명이 표시됩니다.  MaxAct와 VocabProj가 생성한 설명의 유사성, 상호 보완성, 추상화 수준, 그리고 상이점을 분석하여 각 방법의 강점과 약점을 보여주는 예시를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Human evaluation results of descriptions by MaxAct and VocabProj for 100 SAE features from Gemma Scope, showing for each relation category the fraction of observed cases and the descriptions of an example feature.
> </details>

{{< table-caption >}}
| Variant | Gemma-2 2B (Gemma Scope 16K) | Llama-3.1 8B (Llama Scope 32K) | GPT-2 small (OpenAI SAE 32K) |
|---|---|---|---|
| Dec & Unembed | 0.44 (0.31-0.58) | 0.27 (0.17-0.39) | 0.29 (0.12-0.50) |
| Enc & Unembed | 0.38 (0.27-0.52) | 0.14 (0.06-0.25) | 0.25 (0.12-0.46) |
| Dec & Embed | 0.52 (0.38-0.65) | 0.20 (0.11-0.31) | 0.25 (0.08-0.46) |
| Enc & Embed | 0.29 (0.17-0.42) | 0.16 (0.08-0.27) | 0.21 (0.08-0.42) |{{< /table-caption >}}
> 🔼 표 3은 VocabProj에서 생성된 설명에 대한 평균 입력 지표 결과의 신뢰 구간을 보여줍니다. 이 표는 디코딩과 인코딩 변형을 비교하기 위해 4가지 다른 방법으로 검색된 토큰을 사용하여 생성된 설명에 대한 평균 입력 지표 결과의 신뢰 구간을 보여줍니다.  신뢰 구간은 VocabProj 방법의 변형에서 디코딩 변형과 인코딩 변형을 비교하기 위해 사용된 4가지 다른 방법을 사용하여 생성된 설명에 대한 평균 입력 지표 결과를 보여줍니다.  각 방법은 모델의 어휘 공간에 대한 특징 벡터의 투영에 사용된 행렬(디코딩 또는 인코딩)과 특징 벡터를 생성하는 데 사용된 방법(디코딩 또는 인코딩)에 따라 다릅니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Confidence interval of mean input metric results on the descriptions generated by VocabProj using tokens retrieved by 4 different methods, to compare decoding vs. encoding variants.
> </details>

{{< table-caption >}}
| Variant | Gemma-2 2B (Gemma Scope 16K) | Llama-3.1 8B (Llama Scope 32K) | GPT-2 small (OpenAI SAE 32K) |
|---|---|---|---|
| Dec & Unembed | 0.41 (0.35-0.47) | 0.14 (0.11-0.19) | 0.20 (0.13-0.28) |
| Dec & Embed | 0.37 (0.31-0.43) | 0.12 (0.08-0.16) | 0.13 (0.08-0.21) |{{< /table-caption >}}
> 🔼 표 4는 VocabProj에서 생성된 설명에 대한 평균 입력 지표 결과의 신뢰 구간을 보여줍니다. 여기서 사용된 토큰은 디코딩 행렬을 사용하여 언임베딩과 임베딩 변형을 비교하기 위해 두 가지 다른 방법으로 검색됩니다.  즉, 이 표는 모델의 어휘 공간에 특징 벡터를 투영하여 얻은 단어들을 사용하여 특징을 설명하는 VocabProj 방법의 성능을 평가하고,  단어 임베딩을 사용하는 방법과 단어 언임베딩을 사용하는 방법의 성능 차이를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Confidence interval of mean input metric results on the descriptions generated by VocabProj using tokens retrieved by 2 different methods, to compare unembedding vs. embedding variants with the decoding matrix.
> </details>

{{< table-caption >}}
| Variant | Gemma-2 2B (Gemma Scope 16K) | Llama-3.1 8B (Llama Scope 32K) | GPT-2 small (OpenAI SAE 32K) | ALL |
|---|---|---|---|---|
| Neuronpedia | 0.49 (0.44-0.55) | 0.46 (0.41-0.52) | 0.41 (0.36-0.47) | 0.46 (0.43-0.49) |
| MaxAct | 0.52 (0.46-0.57) | 0.47 (0.42-0.53) | 0.44 (0.39-0.50) | 0.48 (0.45-0.51) |{{< /table-caption >}}
> 🔼 표 5는 Neuronpedia에서 가져온 설명과 MaxAct를 사용하여 생성된 설명에 대한 평균 입력 측정 결과의 신뢰 구간을 보여줍니다.  신뢰 구간은 각 설명 방법의 성능을 평가하는 데 사용되는 입력 기반 평가에서의 정확성을 나타냅니다. MaxAct는 제안된 출력 중심 방법과 비교하여 입력 중심 방법의 성능을 측정하는 데 사용됩니다. 이 표는 논문의 실험 결과를 보여주는 핵심 표 중 하나입니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Confidence interval of mean input metric results on the descriptions taken from Neuronpedia and those generated by MaxAct.
> </details>

{{< table-caption >}}
|           | Llama-3.1 MLP SAE |           | GPT2 Res. Mid. SAE |           | GPT2 Res. SAE |           | GPT2 MLP SAE |           |
| :--------- | :----------------- | :--------- | :----------------- | :--------- | :------------- | :--------- | :------------- | :--------- |
|           | Input              | Output     | Input              | Output     | Input          | Output     | Input          | Output     |
| MaxAct     | 56.4 ± 2.9         | 49.6 ± 2.9 | 43.8 ± 4.4         | **45.5 ± 4.5** | 42.4 ± 4.5    | 43.9 ± 4.5    | 41.3 ± 4.4    | 32.6 ± 4.2    |
| VocabProj | 20.2 ± 2.3         | 48.2 ± 2.9 | 23 ± 3.8           | **46.1 ± 4.5** | 19.2 ± 3.5    | 43.7 ± 4.5    | 6.9 ± 2.3     | 37.4 ± 4.4    |
| TokenChange | 25.4 ± 2.5         | **53.1 ± 2.9** | 25.3 ± 3.9         | 42.8 ± 4.4         | 22.4 ± 3.8    | 42.6 ± 4.5    | 6.1 ± 2.1     | 34.9 ± 4.3    |
| EnsembleR (MA+VP) | 62.1 ± 2.8         | 45.8 ± 2.9 | **56.8 ± 4.4**         | **45.7 ± 4.5** | **56.8 ± 4.5**    | **46.4 ± 4.5**    | **50.9 ± 4.5**    | 36.1 ± 4.3    |
| EnsembleR (MA+TC) | **65.8 ± 2.8**         | 48.9 ± 2.9 | **56.2 ± 4.4**         | **46.6 ± 4.5** | **58.9 ± 4.4**    | **49.4 ± 4.5**    | 50.5 ± 4.5    | **40 ± 4.4**    |
| EnsembleR (VP+TC) | 22.6 ± 2.4         | 50.7 ± 2.9 | 28.6 ± 4.1         | 44.3 ± 4.5         | 25.3 ± 3.9    | 44.3 ± 4.5    | 7.1 ± 2.3     | **43.6 ± 4.5**    |
| EnsembleR (All)    | 62.7 ± 2.8         | 51.6 ± 2.9 | **61 ± 4.4**           | **47.2 ± 4.5** | **59.1 ± 4.4**    | **48.7 ± 4.5**    | **50.1 ± 4.5**    | 36.9 ± 4.3    |
| EnsembleC (All)    | 39.1 ± 2.8         | **55.5 ± 2.9** | 40.1 ± 4.4         | **49.5 ± 4.5**         | 39.2 ± 4.4    | **46.4 ± 4.5**    | 25.2 ± 3.9    | 37.7 ± 4.4    |{{< /table-caption >}}
> 🔼 표 6은 다양한 특징 유형과 모델에 대해 평균화된 계층별 방법 및 앙상블의 입력 및 출력 기반 평가 결과와 각각의 95% 신뢰 구간을 보여줍니다. SAE 특징의 경우 모든 크기의 SAE에서 특징의 평균을 사용합니다. MaxAct는 MA, VocabProj는 VP, TokenChange는 TC, EnsembleR 및 EnsembleC는 원시 및 연결 기반 앙상블을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Input- and output-based evaluation results of the methods and their ensembles, over different feature types and models, averaged across model layers, along with their respective 95% confidence intervals. For SAE features we take the average over features from SAEs of all sizes. We denote MA for MaxAct, VP for VocabProj, TC for TokenChange, and EnsembleR and EnsembleC for the raw and concatenation based ensembles.
> </details>

{{< table-caption >}}
| Example feature | Description by `MaxAct` | Description by `VocabProj` | Description by `TokenChange` |
|---|---|---|---|
| layer-type/id |  |  |  |
| `3-MLP-16K/ 4878` | Terms and themes related to various genres of storytelling, particularly in horror, drama, and fantasy. | A blend of themes and genres commonly found in storytelling or media, with a specific focus on dramatic, horror, and suspenseful narratives. | Categorization or analysis of music and entertainment genres, possibly including content recommendations or thematic associations. |
| `19-MLP-16K/ 5635` | References to political events and milestones. | Concepts related to time measurement such as days, weeks, weekends, and months, indicating it likely pertains to scheduling or planning events. | Time periods, particularly weeks and weekends, along with some programming or markup elements for building or managing templates or components. |
| `21-RES-16K/ 10714` | Information related to bird species and wildlife activities. | Concepts related to birdwatching and ornithology, focusing on activities such as observing, spotting, and recording bird species in their natural habitats. | Enhancing or analyzing bird watching or ornithological data and experiences, possibly improving the tracking of bird sightings and interactions. |
| `19-MLP-16K/ 1450` | Mentions of notable locations, organizations, or events, particularly in various contexts. | Concepts related to self-reflection, purpose, and generalization in various contexts, focusing on the exploration of identity and overarching themes in literature or philosophy. | Recognize and generate variations of the term "general" and its context, along with concepts associated with insight and observation. |{{< /table-caption >}}
> 🔼 이 표는 GemmaScope의 SAE 특징에 대해 MaxAct, VocabProj, TokenChange 세 가지 방법으로 생성된 설명을 보여줍니다. 각 방법은 모델의 내부 표현을 설명하는 데 다른 접근 방식을 사용하며, 이 표는 각 방법이 생성하는 설명의 차이점을 보여주는 대표적인 예시를 제공합니다.  각 행은 하나의 SAE 특징과 그에 대한 세 가지 방법의 설명을 나타냅니다. 이를 통해 각 방법의 강점과 약점을 비교하고, 다양한 방법으로 생성된 설명을 종합적으로 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Example descriptions by MaxAct, VocabProj and TokenChange for 4 SAE features from GemmaScope.
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
{{< /gallery >}}