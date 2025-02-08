---
title: "Beyond Prompt Content: Enhancing LLM Performance via Content-Format Integrated Prompt Optimization"
summary: "프롬프트 콘텐츠뿐 아니라 형식까지 통합적으로 최적화하여 LLM 성능을 향상시키는 혁신적인 방법론, CFPO 제시!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Microsoft Research",]
showSummary: true
date: 2025-02-06
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.04295 {{< /keyword >}}
{{< keyword icon="writer" >}} Yuanye Liu et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-07 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.04295" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.04295" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)의 성능은 프롬프트 디자인에 크게 의존합니다.  기존 연구는 주로 프롬프트 **콘텐츠 최적화**에 집중했지만, **프롬프트 형식**의 중요성은 간과되었습니다.  프롬프트 형식은 모델의 성능에 상당한 영향을 미치며, 콘텐츠와 상호 작용합니다.  따라서 콘텐츠와 형식을 모두 고려하는 최적화가 필요합니다.

본 연구는 **콘텐츠-형식 통합 프롬프트 최적화(CFPO)**라는 새로운 방법론을 제시합니다.  CFPO는 반복적인 개선 과정을 통해 프롬프트 콘텐츠와 형식을 동시에 최적화합니다.  자연어 변이를 활용하여 콘텐츠 변화를 탐색하고, 다양한 형식 옵션을 체계적으로 평가하는 동적 형식 탐색 전략을 사용합니다.  실험 결과, CFPO는 콘텐츠만 최적화하는 기존 방법보다 성능이 향상됨을 보여주며, **프롬프트 형식의 중요성과 통합 최적화의 효과**를 강조합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 콘텐츠와 형식을 통합적으로 최적화하는 CFPO 기법 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 다양한 LLM과 작업에서 CFPO의 성능 향상 효과 검증 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 프롬프트 형식 최적화의 중요성을 강조하고 새로운 연구 방향 제시 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **프롬프트 최적화** 분야에서 **콘텐츠와 형식을 통합적으로 최적화**하는 혁신적인 방법론을 제시하여 LLM 성능 향상에 크게 기여합니다. 기존 연구들이 주로 프롬프트 콘텐츠에만 초점을 맞춘 것과 달리, **프롬프트 형식의 중요성을 강조**하고 이를 체계적으로 최적화하는 방법을 제시함으로써 **LLM 성능 향상의 새로운 가능성**을 열어줍니다. 또한, 다양한 LLM과 작업에 대한 광범위한 실험을 통해 CFPO의 효과를 입증하여 실제 응용 가능성을 높였습니다.  향후 연구는 CFPO를 기반으로 더욱 효율적이고 강력한 프롬프트 최적화 기법을 개발하는 데 활용될 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.04295/extracted/6150185/fig/teaser6.png)

> 🔼 그림 1은 프롬프트 형식이 LLM 성능에 미치는 중요한 영향과 콘텐츠와의 상호 작용을 보여줍니다. (A)는 모델별 형식 편향을 보여주는 것으로, GSM8K 작업에서 두 가지 LLM이 서로 다른 형식 스타일에 대해 성능 민감도를 보이는 것을 보여줍니다. 무작위로 선택된 10가지 형식의 효과에 상당한 차이가 있음을 보여줍니다. (B)는 24가지의 서로 다른 형식에 대해 평가된 7가지의 서로 다른 프롬프트 콘텐츠에 대해, 성능 변화는 프롬프트 콘텐츠와 구조 간의 복잡하고 상호 의존적인 관계를 보여주는 것으로, 어떤 단일 형식도 보편적으로 효과를 극대화하지 못함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  The crucial role of prompt formatting and its interaction with content. (A): Model-specific format biases: Illustrates the performance sensitivity of two LLMs to different format styles on the GSM8K task, showing substantial variability in the effectiveness of 10 randomly selected formats. (B): For seven different prompt contents evaluated across 24 distinct formats, performance variations show the complex, interdependent relationship between prompt content and structure, demonstrating that no single format universally maximizes effectiveness.
> </details>





{{< table-caption >}}
| Method | Mistral-7B-v0.1 | LLaMA-3.1-8B | LLaMA-3-8B-Instruct | Phi-3-Mini-Instruct |
|---|---|---|---|---|
| **GSM8K** |
| Baseline (1-shot cot) | 36.85 | 50.03 | 74.00 | 83.45 |
| Baseline (8-shot cot) | 38.21 | 51.02 | 73.46 | 85.75 |
| GRIPS | 39.04 | 50.27 | 74.53 | 83.47 |
| APE | 40.33 | 52.39 | 75.13 | 83.85 |
| ProTeGi | 45.72 | 54.74 | 75.36 | 84.84 |
| SAMMO | 43.82 | 54.74 | 75.89 | 84.76 |
| **CFPO** (*Ours*) | **53.22** | **63.38** | **80.74** | **89.16** |
| **MATH-500** |
| Baseline (1-shot cot) | 4.60 | 10.58 | 12.20 | 12.60 |
| Baseline (4-shot cot) | 10.20 | 23.40 | 14.00 | 40.40 |
| GRIPS | 13.40 | 15.80 | 23.60 | 10.80 |
| APE | 11.60 | 12.80 | 22.80 | 30.60 |
| ProTeGi | 10.80 | 17.00 | 18.40 | 28.80 |
| SAMMO | 12.20 | 15.40 | 25.80 | 42.40 |
| **CFPO** (*Ours*) | **14.80** | **26.99** | **33.33** | **44.20** |
| **ARC-Challenge** |
| Baseline | 67.15 | 73.81 | 75.94 | 84.39 |
| GRIPS | 77.05 | 77.90 | 79.61 | 87.46 |
| APE | 75.85 | 77.05 | 78.67 | 87.63 |
| ProTeGi | 76.54 | 77.22 | 79.86 | 87.54 |
| SAMMO | 77.22 | 77.13 | 79.86 | 87.03 |
| **CFPO** (*Ours*) | **79.35** | **78.50** | **80.63** | **88.23** |
| **Big-Bench Classification** |
| Baseline | 56.00 | 64.00 | 70.00 | 54.00 |
| GRIPS | 86.00 | 67.00 | 84.00 | 69.00 |
| APE | 73.00 | 65.00 | 60.00 | 63.00 |
| ProTeGi | 83.00 | 81.00 | 82.00 | 76.00 |
| SAMMO | 86.00 | 80.00 | 86.00 | 78.00 |
| **CFPO** (*Ours*) | **94.00** | **90.00** | **91.00** | **87.00** |{{< /table-caption >}}

> 🔼 표 1은 수학 추론 과제와 상식 추론 과제에 대한 주요 결과를 보여줍니다.  다양한 모델(Mistral-7B-v0.1, LLaMA-3.1-8B, LLaMA-3-8B-Instruct, Phi-3-Mini-Instruct)과 여러 가지 과제(GSM8K, MATH500, ARC-Challenge, Big-Bench Classification)에서 제안된 CFPO 방법과 여러 기준 방법(Baseline, GRIPS, APE, ProTeGi, SAMMO)의 성능을 비교 분석하여 CFPO의 효과를 보여줍니다. 각 과제별로 1-shot 또는 8-shot 기준 성능과 CFPO를 적용한 성능을 비교하여 정량적인 성능 향상을 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 1:  Main results on math reasoning tasks and commonsense reasoning tasks.
> </details>





### In-depth insights


#### Prompt Format Bias
프롬프트 형식 편향은 **대규모 언어 모델(LLM)**의 성능에 상당한 영향을 미치는 중요한 요소입니다.  모델의 설계 및 학습 데이터의 특성에 따라 특정 형식에 대한 선호도가 존재하며, 이는 모델의 예측 정확도와 효율성에 영향을 미칩니다.  **일관되지 않은 형식**으로 인해 모델이 예상치 못한 결과를 생성하거나, 특정 형식에 최적화된 답변을 생성하지 못하는 경우가 발생할 수 있습니다. 따라서 **최적의 프롬프트 형식**을 결정하기 위한 체계적인 접근 방식이 필요하며, 이를 위해서는 다양한 형식을 실험하고 모델의 성능을 평가하는 엄격한 실험 설계가 필수적입니다.  **형식 편향을 완화하기 위한 전략**으로는 데이터 전처리 단계에서 일관된 형식을 유지하거나, 모델 학습 과정에서 다양한 형식의 데이터를 포함하는 등의 방법이 고려될 수 있습니다. **형식 편향에 대한 연구**는 LLM의 신뢰성과 범용성을 향상시키는 데 중요하며, 앞으로 더욱 심도있는 연구가 필요합니다.

#### CFPO Methodology
본 논문에서 제안하는 CFPO(Content-Format Integrated Prompt Optimization) 방법론은 **프롬프트의 내용과 형식을 동시에 최적화**하는 혁신적인 접근 방식입니다.  단순히 프롬프트 내용만을 최적화하는 기존 연구들과 달리, CFPO는 **반복적인 최적화 과정**을 통해 프롬프트 내용과 형식을 동시에 개선합니다.  **내용 최적화**는 몬테카를로 샘플링과 사례 분석을 통해 이루어지고, **형식 최적화**는 다양한 형식 옵션을 체계적으로 평가하는 동적 탐색 전략을 사용합니다.  **구조화된 프롬프트 템플릿**을 이용하여 내용과 형식을 효율적으로 구분하고 최적화함으로써, 다양한 LLM과 과제에서 성능 향상을 보입니다.  **LLM 기반 형식 생성기**를 통해 새로운 형식을 생성하고, UCT(Upper Confidence Bound applied to Trees) 알고리즘을 사용하여 효율적인 형식 탐색을 수행합니다.  결론적으로 CFPO는 **모델에 독립적인 실용적인 접근 방식**으로, LLM의 성능 향상에 크게 기여할 것으로 기대됩니다.

#### LLM Format Gen
LLM Format Gen은 본 논문에서 제시된 핵심적인 방법론으로, **LLM(대규모 언어 모델)을 활용하여 새로운 프롬프트 형식(format)을 생성하는 기법**을 의미합니다. 단순히 기존의 프롬프트 형식을 반복적으로 사용하는 것이 아니라, LLM의 창의성과 일반화 능력을 활용하여 다양하고 효과적인 새로운 형식을 탐색하는 데 중점을 둡니다.  이를 통해 프롬프트의 내용(content) 최적화와 더불어 형식 최적화를 동시에 수행함으로써, LLM의 성능을 향상시키는 데 기여합니다.  **LLM Format Gen은 단순한 무작위 생성이 아닌, 기존 프롬프트 형식을 학습하고, 이를 바탕으로 새로운 형식을 생성**하므로, 보다 효율적이고 목적 지향적인 형식 생성을 가능하게 합니다.  **이는 LLM의 메타인지 능력을 활용하여 자동으로 최적의 프롬프트 형식을 찾아나가는 혁신적인 접근 방식**이라 할 수 있으며,  기존의 수동적인 프롬프트 엔지니어링 방식의 한계를 극복하고, 모델 성능 향상에 크게 기여할 것으로 기대됩니다.  또한,  **다양한 LLM과 과제에 대한 실험 결과를 통해, LLM Format Gen의 효과와 일반화 능력을 검증**하였습니다.  이러한 결과는 LLM Format Gen이 향후 LLM 응용 연구 및 개발에 중요한 역할을 수행할 수 있음을 시사합니다.

#### Ablation Study
본 논문의 "Ablation Study" 부분은 **CFPO 모델의 성능에 기여하는 각 구성 요소의 중요성을 밝히는 데 중점**을 둡니다.  특히, **형태 최적화기의 효과를 검증하기 위해 형태 최적화기를 제거한 CFPOc와 형태 최적화 단계를 별도로 수행하는 CFPO+Format을 비교**합니다.  결과적으로, **두 가지 변형 모델 모두 완전한 CFPO 모델보다 성능이 떨어지는 것으로 나타나**, **내용과 형태를 통합적으로 최적화하는 것이 중요함**을 보여줍니다.  또한, **LLM을 활용한 형태 생성의 효과를 평가**하기 위해 형태 생성을 사용하지 않은 변형 모델과 비교 분석하여 **형태 생성이 CFPO의 성능 향상에 크게 기여**함을 확인합니다.  **마지막으로, 형태 선택 전략의 효과를 검증**하기 위해 UCT 기반 전략을 무작위 선택 및 탐욕적 선택 전략과 비교하여 **UCT 기반 전략의 우수성**을 입증합니다.  이러한 ablation study를 통해 **CFPO 모델의 각 구성 요소가 상호 작용하며 최적의 성능을 발휘**한다는 점을 명확히 제시합니다.

#### Future Work
본 논문에서 제시된 콘텐츠-형식 통합 프롬프트 최적화 (CFPO) 방법론은 프롬프트 최적화 분야에 중요한 발전을 가져왔지만, **향후 연구를 위한 다양한 방향**이 존재합니다.  먼저, **다양한 LLM 아키텍처 및 크기에 대한 CFPO의 일반화 가능성**을 더욱 심도 있게 연구할 필요가 있습니다. 현재 연구는 제한된 LLM 모델에 대한 평가에 초점을 맞추었으므로, 더욱 광범위한 모델에 대한 실험을 통해 CFPO의 범용성을 검증해야 합니다. 또한, **프롬프트 형식 생성 과정의 효율성 개선**에 대한 연구가 필요합니다.  현재 사용 중인 LLM 기반 형식 생성 방법은 계산 비용이 다소 높을 수 있으며, 더욱 효율적인 방법을 모색하여 최적화 과정의 속도를 높이는 것이 중요합니다.  **다양한 평가 지표 및 실제 응용 분야에 대한 CFPO 성능 평가** 또한 중요한 연구 과제입니다. 본 논문에서는 특정 작업에 대해 CFPO의 효과를 입증하였지만, 더 다양한 평가 지표를 사용하고 실제 응용 시나리오에 적용하여 CFPO의 실용성을 강화해야 합니다.  마지막으로, **CFPO와 다른 프롬프트 엔지니어링 기법들과의 결합 및 상호 작용 연구**를 통해 프롬프트 최적화의 전반적인 효율성을 극대화할 수 있습니다.  **이러한 후속 연구를 통해 CFPO의 이론적 기반을 강화하고, 실제 응용 분야에서의 효용성을 더욱 증대**시켜야 합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.04295/extracted/6150185/fig/pipeline3.png)

> 🔼 그림 2는 CFPO 파이프라인의 한 번의 반복 과정을 보여줍니다. 먼저, 구성 요소별 콘텐츠 최적화 단계에서 사례 진단 및 몬테카를로 샘플링을 사용하여 콘텐츠 변이를 생성합니다. 그런 다음, 형식 최적화 단계에서 각 콘텐츠 후보에 대해 가장 적합한 형식을 식별합니다. 노란색 점선은 LLM 최적화 장치를 사용하여 최적화 프로세스를 안내하는 부분을 나타냅니다.  즉, 콘텐츠 최적화 단계에서는 콘텐츠의 변형을 위해 사례 진단과 몬테카를로 샘플링 기법을 사용하고, 이후 형식 최적화 단계에서는 다양한 형식들을 평가하여 각 콘텐츠에 가장 적합한 형식을 찾습니다.  LLM 최적화기는 이러한 과정 전반에 걸쳐 최적화를 안내하는 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Illustration of the CFPO pipeline within a single iteration round. In the initial Component-wise Content Optimization stage, case-diagnosis and Monte-Carlo sampling are employed for content mutation. Subsequently, the Format Optimization stage identifies the most suitable format for each content candidate. The yellow dashed line indicates where the LLM optimizer is employed to guide the optimization process.
> </details>



![](https://arxiv.org/html/2502.04295/extracted/6150185/fig/template2.png)

> 🔼 그림 3은 논문에서 제안하는 구조화된 프롬프트 템플릿의 예시를 보여줍니다. 이 템플릿은 프롬프트를 각기 다른 기능을 수행하는 여러 구성 요소로 체계적으로 구성하여 프롬프트 생성 과정을 효율화합니다. 프롬프트를 만들 때, 먼저 Query Format을 사용하여 예시와 질문을 제시하고, 그런 다음 Prompt Renderer를 통해 모든 콘텐츠 구성 요소를 통합하여 완성된 프롬프트 문자열을 만듭니다. 이를 통해 프롬프트의 콘텐츠와 형식을 효과적으로 최적화할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: An illustrative example of our Structured Prompt Template. This template systematically organizes the prompt into distinct components, each serving a specific functional role. When formulating a prompt, the template first employs a Query format to present examples and queries, and then integrates all content components via the Prompt Renderer to construct the comprehensive prompt string.
> </details>



![](https://arxiv.org/html/2502.04295/extracted/6150185/fig/formats5.png)

> 🔼 그림 4는 초기 형식 풀에서 사용 가능한 내장 형식 및 렌더링 효과를 보여줍니다. 최종 형식 구성은 프롬프트 렌더러와 쿼리 형식 범주에서 요소를 선택하고 결합하여 생성됩니다.  프롬프트 렌더러는 프롬프트의 전반적인 구조를 결정하고, 쿼리 형식은 인 컨텍스트 예시와 질의의 렌더링 방식을 제어합니다. 다양한 프롬프트 렌더러(일반 텍스트, 마크다운, HTML, LaTeX, XML, JSON 등)와 쿼리 형식(Markdown-Ins-Res, Role-Mapping-Format, COT-Question-Answer, Multi-choice 등)을 보여주어, 이들을 조합하여 다양한 프롬프트 형식을 생성할 수 있음을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Built-in formats and rendering effects in our initial format pool. The final format configuration is achieved by selecting and combining elements from both the Prompt Renderer and the Query Format categories.
> </details>



![](https://arxiv.org/html/2502.04295/extracted/6150185/fig/results.png)

> 🔼 그림 5는 다양한 작업과 모델에 대해 문맥 내 예시와 텍스트 길이를 개괄적으로 보여줍니다.  각 작업(GSM8K, MATH500, ARC-Challenge, Big-Bench Classification)과 모델(Mistral-7B-v0.1, LLaMA-3.1-8B, LLaMA-3-8B-Instruct, Phi-3-Mini-Instruct)별로 최적화된 프롬프트의 문맥 내 예시 개수와 텍스트 길이를 비교 분석하여, 사전 훈련된 모델과 지시 튜닝된 모델 간의 차이점을 보여줍니다. 특히, 사전 훈련된 모델은 더 긴 텍스트 길이와 더 많은 문맥 내 예시를 선호하는 경향을 보이는 반면, 지시 튜닝된 모델은 프롬프트 길이와 문맥 내 예시 개수에 덜 민감한 것을 알 수 있습니다. 이는 사전 훈련된 모델이 명시적인 문맥과 상세한 추론 단계로부터 더 많은 이점을 얻는 반면, 지시 튜닝된 모델은 이미 작업 관련 지식을 갖고 있기 때문에 이러한 요소들에 덜 의존한다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Overview of in-context examples and text lengths for various tasks and models.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Task | Method | LLaMA-3.1-8B | LLaMA-3-8B-Instruct |
|---|---|---|---| 
| GSM8K | ProTeGi | 54.74 | 75.36 |
|  | CFPO<sub>c</sub> | 58.07 | 77.71 |
|  | CFPO<sub>c</sub>+Format | 61.94 | 79.30 |
|  | **CFPO** | **63.38** | **80.74** |
| BBC | ProTeGi | 81.00 | 82.00 |
|  | CFPO<sub>c</sub> | 85.00 | 85.00 |
|  | CFPO<sub>c</sub>+Format | 88.00 | 89.00 |
|  | **CFPO** | **90.00** | **91.00** |{{< /table-caption >}}
> 🔼 표 2는 형식 최적화기와 콘텐츠 최적화기의 효과를 비교 분석한 결과를 보여줍니다. CFPOc는 형식을 고정한 채 콘텐츠만 최적화하는 반면, CFPOc+Format은 콘텐츠 최적화 후 형식 최적화를 수행합니다. 이를 통해 형식 최적화기와 콘텐츠 최적화기 각각의 기여도와 두 기법의 통합이 가져오는 시너지 효과를 정확하게 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Ablation study of the format optimizer and content optimizer. CFPOc𝑐{c}italic_c performs content optimization with a fixed format. CFPOc𝑐{c}italic_c+Format performs format optimization after content optimization.
> </details>

{{< table-caption >}}
| Task | Method | LLaMA-3.1-8B | LLaMA-3-8B-Instruct |
|---|---|---|---| 
| GSM8K | w/o Format Gen | 62.70 | 78.85 |
|  | with Format Gen | **63.38** | **80.74** |
| BBC | w/o Format Gen | 88.00 | 87.00 |
|  | with Format Gen | **90.00** | **91.00** |{{< /table-caption >}}
> 🔼 본 표는 프롬프트 최적화 과정에서 형식 생성의 영향을 보여줍니다.  LLM을 사용하여 새로운 형식을 생성하는 것이 기존 형식 풀만 사용하는 것보다 GSM8K 및 Big-Bench Classification 작업에서 모두 성능 향상을 가져온다는 것을 보여줍니다.  이는 제안된 형식 탐색 메커니즘이 프롬프트의 품질과 다양성을 향상시키는 데 효과적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Impact of format generation during prompt optimization.
> </details>

{{< table-caption >}}
| Task | Method | LLaMA-3.1-8B | LLaMA-3-8B-Instruct |
|---|---|---|---| 
|  | Random | 62.40 | 78.82 |
| GSM8K | UCT(α=0) | 63.23 | 79.08 |
|  | UCT(ours) | 63.38 | 80.74 |
|  | Random | 85.00 | 87.00 |
| BBH | UCT(α=0) | 86.00 | 88.00 |
|  | UCT(ours) | 90.00 | 91.00 |{{< /table-caption >}}
> 🔼 표 4는 최적화 과정 동안 다양한 형식 선택 전략의 영향을 보여줍니다.  다양한 형식 선택 방법(무작위 선택, 탐색 없이 최적의 형식만 선택, UCT 알고리즘 사용)을 비교하여 CFPO의 UCT 기반 형식 선택 전략이 GSM8K 및 Big-Bench 두 작업 모두에서 가장 좋은 성능을 달성했음을 보여줍니다. 이는 CFPO의 형식 최적화 전략의 효과를 강조합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Impact of different format selection strategies during optimization.
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
{{< /gallery >}}