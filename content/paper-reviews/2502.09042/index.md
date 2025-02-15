---
title: "Typhoon T1: An Open Thai Reasoning Model"
summary: "타이어 추론 모델 Typhoon T1 공개: 저자원 언어에서도 효과적인 추론 성능을 보이며, 개방형 데이터셋과 모델 가중치를 제공합니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 SCB 10X R&D",]
showSummary: true
date: 2025-02-13
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.09042 {{< /keyword >}}
{{< keyword icon="writer" >}} Pittawat Taveekitworachai et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-14 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.09042" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.09042" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/typhoon-t1-an-open-thai-reasoning-model" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM) 기반의 추론 모델은 복잡한 작업에서 성능을 향상시키는 것으로 나타났지만, 특히 저자원 언어의 경우 개발 세부 정보가 제한적입니다.  기존 연구들은 주로 강화 학습(RL)에 의존했지만, RL은 불안정하고 비용이 많이 듭니다. 

본 연구는 타이어를 대상으로 하는 저자원 언어 추론 모델인 Typhoon T1을 소개합니다. Typhoon T1은 개방형 데이터셋을 사용한 지도 학습 파인튜닝을 통해 개발되어, RL보다 비용 효율적입니다.  본 연구에서는 합성 데이터 생성 및 훈련 과정, 데이터셋 및 모델 가중치에 대한 자세한 내용을 공개합니다. 또한, 다양한 도메인에서 일반화되고 저자원 언어로 추론 과정을 생성할 수 있는 추론 모델 개발에 대한 통찰력을 제공합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 타이어 저자원 언어 환경에서도 효과적인 추론 모델 Typhoon T1을 개발 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 지도 학습 기반의 파인튜닝을 통해 강화 학습보다 비용 효율적인 방식으로 추론 모델 개발 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 개방형 데이터셋, 모델 가중치 및 훈련 세부 정보 공개를 통한 재현성 및 후속 연구 지원 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **저자원 언어를 위한 추론 모델 개발의 어려움을 해결**하고, **다양한 분야에 걸쳐 일반화되는 추론 모델을 개발하는 데 대한 통찰력**을 제공합니다.  **개방형 데이터셋, 모델 가중치, 그리고 훈련 세부 정보를 공개**하여, 다른 연구자들이 타이어 추론 모델 개발을 위한 기반을 마련하고, 저자원 언어 처리 연구를 더욱 발전시키는 데 기여할 수 있습니다. 또한, **다국어 추론 모델 개발에 대한 새로운 접근 방식**을 제시하여, 앞으로의 연구 방향을 제시합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.09042/extracted/6200630/figures/overview.png)

> 🔼 그림 1은 논문의 2.2.1절과 2.2.2절에서 설명하는 장기적 사고 데이터 생성을 위한 변환 및 개선 파이프라인을 보여줍니다. 그림 상단은 파이프라인의 개요를, 그림 하단 왼쪽은 3.1절에서 설명하는 최적의 사고 방식인 구조화된 장기적 사고를 사용한 Typhoon T 모델의 학습 파이프라인을, 그림 하단 오른쪽은 3.4절에서 설명하는 영어-태국어 이중 언어 Typhoon T1 모델의 학습 파이프라인을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Top: The transformation-and-refinement pipeline used for long-thinking data generation described in Sections 2.2.1 and 2.2.2. Bottom-Left: The structured long-thinking (the best thinking format) training pipeline for Typhoon T, as described in Section 3.1. Bottom-Right: The bilingual English-Thai Typhoon T1 model training pipeline detailed in Section 3.4.
> </details>





{{< table-caption >}}
| Model | Datasets | Data Recipe | Training Recipe | Model Weights |
|---|---|---|---|---|
| OpenAI’s o-series | ✗ | ✗ | ✗ | ✗ |
| Google’s Gemini 2.0 Flash Thinking | ✗ | ✗ | ✗ | ✗ |
| Qwen’s QwQ | ✗ | ✗ | ✗ | ✓ |
| DeepSeek R1 | ✗ | ✗ | P | ✓ |
| **Typhoon T1** | ✓ | ✓ | ✓ | ✓ |{{< /table-caption >}}

> 🔼 표 1은 인기 있는 추론 모델들의 개방성을 데이터셋 가용성, 데이터 처리 투명성, 훈련 방법 및 모델 접근성이라는 네 가지 측면에서 비교 분석한 표입니다.  'P'는 부분적인 정보만 공개되었음을 나타냅니다. Typhoon T1 모델은 데이터 레시피를 포함한 모든 범주에서 완벽한 개방성을 제공하는 유일한 모델임을 보여줍니다.  즉, 다른 모델들과 달리 Typhoon T1은 사용된 데이터셋, 데이터 전처리 과정, 모델 훈련 과정, 그리고 모델 자체에 대한 모든 정보를 공개하여, 연구의 재현성과 투명성을 높였습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: A comparison of openness among popular reasoning models, focusing on dataset availability, data processing transparency, training methodology, and model accessibility. P denotes partial details. Typhoon T1 is the only model providing full openness across all categories, including its data recipe.
> </details>





### In-depth insights


#### Thai Reasoning Models
태국어 추론 모델은 **대규모 언어 모델(LLM)**을 기반으로 구축된 상대적으로 새로운 유형의 생성 모델입니다.  기존의 LLM과 달리, 태국어 추론 모델은 최종 답변에 도달하기 전에 장문의 추론 과정을 생성합니다. 이는 복잡한 작업에서 성능을 향상시키는 것으로 나타났습니다. 본 논문에서는 **저자원 언어인 태국어**에 대한 추론 모델 개발에 대한 자세한 내용을 설명하고 있습니다.  **지도 학습 미세 조정**을 사용하여 오픈 데이터셋을 활용함으로써 비용 효율적인 방식으로 모델을 개발하는 방법을 제시합니다. 또한, 이 논문에서는 **합성 데이터 생성 및 훈련**에 대한 세부 정보뿐만 아니라 데이터셋과 모델 가중치도 공개합니다.  이는 태국어 추론 모델 개발에서 얻은 통찰력을 제공하고, 다양한 영역에서 일반화되고 태국어로 추론 과정을 생성할 수 있는 모델을 개발하는 데 도움이 될 것입니다. **본 연구는 저자원 언어의 추론 모델 개발에 대한 중요한 기여**를 하고 있으며, 향후 연구를 위한 기반을 제공할 것으로 기대됩니다.

#### SFT Approach
본 논문에서 제시된 SFT(Supervised Fine-Tuning) 접근 방식은 **추론 모델 개발에 있어 비용 효율적인 대안**을 제시합니다. 강화 학습 대신 **개방형 데이터셋을 이용한 지도 학습 방식**을 채택하여, **장기 추론 능력**을 가진 모델을 보다 효과적으로 학습시킵니다. 이는 특히 **저자원 언어**에 대한 추론 모델 개발에 있어서 중요한 의미를 지닙니다.  **합성 데이터 생성 및 훈련 과정**에 대한 상세한 설명과 함께, **데이터셋 및 모델 가중치**를 공개하여 **추후 연구를 위한 기반**을 마련합니다.  **다양한 도메인에 걸쳐 일반화**할 수 있는 능력과 **저자원 언어(태국어)**로 추론 과정을 생성하는 능력을 보여주는 사례 연구를 통해, 본 연구는 추론 모델 개발에 대한 귀중한 통찰력을 제공합니다.  특히 **다양한 추론 형식(구조화, 준구조화, 비구조화)**에 대한 실험을 통해 최적의 형식을 제시하고자 하며, 이를 통해 **모델 성능 향상에 대한 심층적인 이해**를 도모합니다.

#### Data Quality
본 논문에서는 데이터 품질에 대한 심층적인 논의가 부족하지만, 데이터셋 구성 및 전처리 과정을 통해 데이터 품질 관리에 대한 중요성을 간접적으로 보여줍니다. **합성 데이터 생성 및 기존 데이터셋 활용**이라는 두 가지 전략을 통해 **다양한 도메인과 언어**를 포괄하는 데이터셋을 구축하려는 시도는 인상적입니다. 그러나 각 데이터셋의 품질, 특히 정확성과 일관성에 대한 명확한 평가 기준과 분석 결과가 제시되지 않아 아쉬움이 남습니다. **데이터 품질에 대한 객관적인 평가**가 부족함으로써 모델 성능 개선에 미치는 영향을 정확히 파악하기 어렵습니다. 추후 연구에서는 **다양한 데이터 품질 지표**를 활용하여 데이터셋의 특징을 자세히 분석하고, 모델 성능과의 상관관계를 명확히 밝히는 것이 필요합니다. 또한, **데이터 오류 및 편향**에 대한 분석과 이를 해결하기 위한 전략을 제시함으로써 데이터 품질 향상에 기여할 수 있을 것입니다.  **개방형 데이터셋 및 모델 가중치 공개**를 통해 연구의 재현성을 높이고, 다른 연구자들의 후속 연구를 촉진하는 데 기여할 수 있다는 점은 높이 평가할 만합니다.

#### Multilingual Reasoning
다국어 추론은 **단일 언어 모델을 넘어서 여러 언어를 이해하고 추론하는 능력**을 의미합니다. 이는 인공지능(AI)이 다양한 언어와 문화권의 정보를 처리하고, 문제 해결 능력을 향상시키는 데 중요한 발전입니다.  다국어 추론 모델은 **번역 작업 없이 다양한 언어로 된 텍스트를 직접 처리**할 수 있어,  글로벌 정보 접근성과 AI 활용도를 크게 높일 수 있습니다. 하지만 다국어 추론은 **데이터 부족 및 언어 간 불균형**과 같은 어려움을 안고 있습니다. 특정 언어의 데이터가 부족하거나, 언어 간 품질 차이가 발생하면 모델의 성능이 저하될 수 있기 때문입니다. 또한, **다국어 추론 모델은 단일 언어 모델보다 훨씬 복잡하고, 개발 비용이 많이 들** 수 있습니다. 따라서 효율적인 다국어 추론 모델 개발을 위해서는 **다양한 언어 데이터 확보, 언어 간 데이터 균형, 효율적인 모델 학습 기술** 등이 중요한 요소로 작용합니다. 앞으로 **다국어 추론 기술의 발전은 다양한 언어 사용자를 위한 AI 서비스 개발 및 글로벌 지식 활용**에 큰 영향을 미칠 것으로 예상됩니다.

#### Future Research
본 논문에서는 타이어 언어를 위한 오픈소스 추론 모델인 Typhoon T1을 제시하고 있습니다. **향후 연구 방향**으로는 몇 가지 중요한 측면들을 고려해 볼 수 있습니다.  먼저, **모델의 크기 확장**을 통해 성능 향상을 도모할 수 있습니다. 현재 3B 매개변수 모델로 제한되어 있으므로, 더 큰 모델을 사용하여 복잡한 추론 작업에 대한 성능을 개선할 수 있을 것입니다.  또한, **더 다양한 데이터셋**을 활용하여 모델의 일반화 능력을 높일 수 있습니다. 현재 사용된 다섯 가지 도메인의 데이터셋 외에, 다른 도메인의 데이터를 추가적으로 학습시켜 모델의 범용성을 향상시키는 것이 중요합니다.  **다양한 추론 전략**을 통합하는 것도 중요한 연구 과제입니다.  본 논문에서는 구조화된 사고 과정을 제시하였지만, 다른 추론 전략을 추가적으로 통합하여 모델의 추론 능력을 더욱 향상시킬 수 있을 것입니다.  **다국어 지원 능력 강화**도 중요한 연구 과제입니다. 타이어 언어에 대한 추론 능력을 향상시켰지만, 다른 언어에 대한 지원 능력을 확장하는 연구가 필요합니다. 마지막으로, **모델의 안전성 및 윤리성**에 대한 연구가 필요합니다.  **오픈 소스 모델**의 특성상, 악의적인 사용을 방지하고 윤리적인 사용을 권장하기 위한 추가적인 연구가 필요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.09042/extracted/6200630/figures/thinking_format.png)

> 🔼 그림 2는 세 가지 사고 방식의 차이점을 보여줍니다. (a) 비구조적 사고는 XML 구조 태그가 포함되지 않은 형태입니다. (b) 반구조적 사고는 비구조적 사고와 유사하지만 생각과 응답을 구분하기 위해 <thoughts> 및 <response> 태그를 추가합니다. (c) 구조적 사고는 생각 부분의 구조적 목적을 위해 추가 XML 태그를 도입합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Differences between three thinking formats: (a) Unstructured thinking, where no XML structural tags are included; (b) Semi-structured thinking, which is similar to unstructured thinking but adds <thoughts> and <response> tags to separate thoughts and responses; (c) Structured thinking, which introduces additional XML tags for structural purposes in the thoughts section.
> </details>



![](https://arxiv.org/html/2502.09042/extracted/6200630/figures/training_percentage.png)

> 🔼 본 그림은 훈련 데이터셋의 비율을 75%를 초과하여 증가시키면 일부 데이터셋의 성능이 저하되는 반면, GSM8K 데이터셋은 데이터 비율이 증가함에 따라 성능이 향상되는 경향을 보여줍니다.  다양한 데이터셋(GSM8K, HumanEval+, IFEval, GPQA, MMLU Pro, ThaiExam)에 대한 모델 성능을 비교 분석하여 데이터셋 크기가 모델 성능에 미치는 영향을 시각적으로 보여줍니다.  각 데이터셋에 대한 성능 향상 또는 저하 정도를 통해 적절한 훈련 데이터 크기를 결정하는 데 도움이 되는 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Increasing the proportion of the training set beyond 75% results in performance degradation for some datasets, while GSM8K generally shows a trend of performance improvement with the proportion.
> </details>



![](https://arxiv.org/html/2502.09042/extracted/6200630/figures/final_comparison.png)

> 🔼 그림 4는 Typhoon 2 3B Instruct 모델을 기준으로 6가지 평가 벤치마크에서 Typhoon T1-EN 및 Typhoon T1 모델의 최종 성능을 비교한 막대 그래프입니다.  각 벤치마크(GSM8K, HumanEval+, IFEval, GPQA, MMLU Pro, ThaiExam)에 대한 세 가지 모델의 성능 점수를 시각적으로 보여줍니다.  이를 통해 각 모델의 강점과 약점을 비교 분석하고, 다국어 추론 모델 개발 과정에서 데이터 및 학습 전략의 영향을 파악하는 데 도움을 줍니다. 특히, Typhoon T1-EN과 Typhoon T1 모델의 성능 차이를 통해 태국어 데이터 추가 학습의 효과를 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Final performance comparison of Typhoon T1-EN and Typhoon T1 against the baseline Typhoon T1 3B Instruct model across six evaluation benchmarks.
> </details>



![](https://arxiv.org/html/2502.09042/extracted/6200630/figures/domain_distribution.png)

> 🔼 그림 5는 본 논문의 실험에 사용된 훈련 데이터셋의 도메인 분포를 보여줍니다.  수학, 지시사항 따르기, 코딩, 안전, 금융 등 다섯 가지 도메인의 데이터 비율을 나타내는 원형 차트로, 각 도메인별 데이터셋의 크기와 비중을 한눈에 파악할 수 있도록 시각적으로 표현하고 있습니다. 이는 각 도메인 데이터의 균형을 확인하고, 실험 결과에 대한 도메인별 영향을 분석하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: This figures show domain distribution of the training set for the experiments.
> </details>



![](https://arxiv.org/html/2502.09042/extracted/6200630/figures/t1_reasoning.png)

> 🔼 그림 6은 영어로 훈련된 모델인 Typhoon T1-EN과 태국어 데이터로 추가 훈련된 모델인 Typhoon T1의 사고 과정을 보여줍니다. 두 모델 모두 동일한 수학 문제에 대해 응답하지만, Typhoon T1-EN은 영어로 사고 과정을 생성하는 반면, Typhoon T1은 태국어로 사고 과정을 생성합니다. 이는 Typhoon T1이 태국어 데이터를 통해 태국어 추론 능력을 갖추었음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: This figure shows Typhoon T1’s Thai thinking trace and Typhoon T1-EN’s English thinking trace.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | GSM8K | HumanEval+ | IFEval | GPQA | MMLU Pro | ThaiExam |
|---|---|---|---|---|---|---|
| **Typhoon 2** |  |  |  |  |  |  |
|  Zero-Shot | 57.32 | 63.51 | **69.32** | 25.00 | **26.61** | 32.69 |
|  Zero-Shot CoT | 53.83 | 0.00 | 68.95 | 25.45 | 23.36 | **33.27** |
|  SFT | 20.62 | 46.24 | 17.74 | 16.74 | 13.96 | 15.65 |
| **Typhoon T** |  |  |  |  |  |  |
|  Unstructured | 59.82 | 67.88 | 34.01 | 24.78 | 20.44 | 21.36 |
|  Semi-structured | 57.24 | **72.87** | 55.27 | **27.68** | 19.46 | 21.92 |
|  Structured | **62.02** | 69.76 | 53.60 | **27.23** | 23.56 | 22.84 |{{< /table-caption >}}
> 🔼 표 2는 다양한 모델의 벤치마크 성능을 보여줍니다.  높은 점수일수록 성능이 좋음을 나타냅니다.  굵은 글씨는 각 열에서 가장 높은 점수를 나타내고, 밑줄 친 점수는 기준 모델인 Typhoon 2 3B Instruct보다 성능이 향상되었음을 나타냅니다. Typhoon 2는 Typhoon 2 3B Instruct를, Typhoon T는 장기 사고 데이터셋으로 훈련된 변형 모델을 나타냅니다. SFT는 원본 데이터셋에 대한 지도 학습 미세 조정을 나타냅니다. 모든 추론 모델은 원본 데이터셋에서 SFT보다 성능이 향상되었습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Performance of models on each benchmark (higher is better). Bold indicates the best score in each column. Underlined scores denote improvements over the baseline, Typhoon 2 3B Instruct. We apply this convention across all results tables. Typhoon 2 refers to Typhoon 2 3B Instruct, and Typhoon T refers to its variant trained on a long-thinking dataset. SFT refers to supervised fine-tuning on the original datasets. All reasoning models show improvement over SFT on the original dataset.
> </details>

{{< table-caption >}}
| Model | GSM8K | HumanEval+ | IFEval | GPQA | MMLU Pro | ThaiExam |
|---|---|---|---|---|---|---|
| **Typhoon T1-EN** | **62.09** | **70.60** | 49.54 | **30.80** | **27.39** | 21.71 |
| + 1.5k, CSFT | 41.39 | 65.79 | 33.83 | 23.66 | 4.30 | 21.20 |
| + 1.5k | 60.12 | 67.90 | **51.76** | 29.91 | 19.32 | **23.56** |
| + 1k | 61.94 | 66.77 | **50.09** | 24.55 | 23.48 | 21.57 |
| + 0.5k | 60.88 | 68.24 | **49.72** | 25.45 | 23.05 | **22.62** |{{< /table-caption >}}
> 🔼 표 3은 추가적인 훈련 데이터의 영향을 평가하기 위해 다양한 벤치마크에서 모델 변형의 성능을 보여줍니다. CSFT는 지속적인 SFT(Supervised Fine-Tuning)를 의미합니다. 1.5k개의 샘플을 추가하면 IFEval과 ThaiExam 점수가 향상되지만, CSFT는 전반적인 성능을 크게 저하시킵니다. 이 표는 추가 데이터가 모델 성능에 미치는 영향과 지속적인 미세 조정의 위험성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Performance of model variants on various benchmarks, evaluating the impact of additional training data. CSFT refers to continual SFT. Adding 1.5k samples improves IFEval and ThaiExam scores, while CSFT significantly reduces overall performance.
> </details>

{{< table-caption >}}
| Model | GSM8K | HumanEval+ | IFEval | GPQA | MMLU Pro | ThaiExam |
|---|---|---|---|---|---|---|
| **Typhoon T1** | 60.12 | 67.90 | **51.76** | **29.91** | **19.32** | 23.56 |
| + EN | 46.17 | 0.00 | 48.98 | 26.56 | 16.55 | **25.31** |
| + TH | 48.29 | 0.00 | 44.73 | 25.67 | 16.05 | 24.66 |{{< /table-caption >}}
> 🔼 표 4는 Typhoon T1 모델이 영어 또는 태국어로 추론하도록 제약했을 때의 성능을 보여줍니다. 특정 언어로 추론하도록 제한하면 전반적인 정확도가 저하됩니다. 대부분의 벤치마크에서 영어 추론이 태국어 추론보다 약간 더 효과적입니다. 그러나 모델이 자체 사고 언어를 선택하도록 하면 최상의 성능을 얻을 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: EN denotes forced reasoning in English, and TH denotes forced reasoning in Thai. Constraining Typhoon T1 to reason in a specific language degrades overall accuracy. English reasoning is slightly more effective than Thai reasoning across most benchmarks. However, allowing the model to choose its own thinking language yields the best performance.
> </details>

{{< table-caption >}}
| Domain/Dataset | #Records |
|---|---| 
| _Mathematics_ | _21,941_ |
| MATH (Hendrycks et al., 2021) | 7,500 |
| Tulu 3 SFT Personas Math Grade (Lambert et al., 2025) | 7,497 |
| PRM800K Phase 2 (Lightman et al., 2024) | 5,809 |
| PRM800K Phase 1 (Lightman et al., 2024) | 808 |
| O1 Journey (Qin et al., 2024) | 327 |
| _Instruction Following_ | _13,188_ |
| No Robots (Rajani et al., 2023) | 9,500 |
| UltraFeedback (Cui et al., 2024) | 3,688 |
| _Coding_ | _10,814_ |
| Evol codealpaca v1 (Luo et al., 2023) | 5,564 |
| Tulu 3 SFT Personas Code (Lambert et al., 2025) | 5,250 |
| _Safety_ | _5,300_ |
| HelpSteer (Wang et al., 2023c) | 5,300 |
| _Finance_ | _4,434_ |
| Wealth Alpaca (Bharti, 2023) | 4,434 |
| **Total** | **55,677** |{{< /table-caption >}}
> 🔼 표 5는 논문에서 사용된 훈련 데이터셋의 데이터 분포를 보여줍니다.  수학, 지시사항 따르기, 코딩, 안전, 금융 등 다섯 가지 도메인에서 수집된 여러 개방형 데이터셋을 사용했으며, 각 도메인별 데이터셋의 종류와 개수를 상세히 나타냅니다.  데이터셋의 크기는 다양하지만, 총 55,677개의 레코드로 구성되어 있습니다.  본 표는 훈련 데이터셋의 구성을 이해하는 데 도움이 되는 세부 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Data mixture of the training set.
> </details>

{{< table-caption >}}
| Model | GSM8K | GPQA | MMLU Pro | ThaiExam |
|---|---|---|---|---|
| **Typhoon 2** |  |  |  |  |
| Zero-shot | 104.61 | 384.78 | 130.41 | 21.90 |
| Zero-shot CoT | 741.97 | 1238.54 | 1697.96 | 149.19 |
| SFT | 72.22 | 479.55 | 91.25 | 587.95 |
| **Typhoon T** |  |  |  |  |
| Unstructured | 169.03 | 478.53 | 491.33 | 829.21 |
| Semi-structured | 170.20 | 795.38 | 487.39 | 900.90 |
| Structured | 102.96 | 466.21 | 293.23 | 995.04 |{{< /table-caption >}}
> 🔼 표 6은 다양한 벤치마크에서 각 모델이 생성한 평균 출력 토큰 수를 보여줍니다. 각 모델의 성능을 비교하고 평균 출력 길이가 모델의 성능이나 특정 벤치마크에 미치는 영향을 분석하는 데 유용합니다.  제로샷, 제로샷 CoT, SFT, 그리고 세 가지 유형의 Typhoon T 모델(구조화되지 않음, 반구조화됨, 구조화됨)의 결과가 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Average number of output tokens generated by each model on the benchmarks.
> </details>

{{< table-caption >}}
| Dataset Size | GSM8K | HumanEval+ | IFEval | GPQA | MMLU Pro | ThaiExam |
|---|---|---|---|---|---|---|
| 100% | 62.02 | 69.76 | **53.60** | 27.23 | 23.56 | **22.84** |
| 75% | **62.09** | **70.60** | 49.54 | **30.80** | 27.39 | 21.71 |
| 50% | 61.87 | 64.59 | 48.80 | **29.46** | **27.63** | 20.36 |
| 25% | **62.09** | 66.93 | 50.46 | **29.69** | **30.05** | 20.54 |
| 10% | 60.20 | 65.51 | 50.65 | **29.24** | **29.03** | 21.07 |
| 5% | 60.88 | 64.62 | 47.13 | **30.13** | **29.65** | 19.91 |{{< /table-caption >}}
> 🔼 표 7은 다양한 크기의 데이터셋으로 훈련된 모델의 성능을 보여줍니다. 특히 GPQA 및 MMLU Pro와 같은 특정 벤치마크에서 더 작은 데이터셋이 100% 크기의 데이터셋보다 성능이 더 좋은 경우도 있습니다. 이는 과적합(overfitting)의 위험성을 고려하여 모델의 일반화 성능(generalization)과 과적합(overfitting) 간의 균형을 분석하는 데 중요한 결과입니다.  데이터셋 크기 변화에 따른 모델 성능 변화를 자세히 분석하여 최적의 데이터셋 크기를 결정하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Performance at different dataset sizes. Smaller dataset sizes can sometimes outperform the 100% baseline, particularly in GPQA and MMLU Pro.
> </details>

{{< table-caption >}}
| Model | GSM8K | HumanEval+ | IFEval | GPQA | MMLU Pro | ThaiExam |
|---|---|---|---|---|---|---|
| **Typhoon T1-EN** | **62.09** | **70.60** | 49.54 | **30.80** | 27.39 | 21.71 |
|  - IF | 59.59 | 69.57 | 46.58 | 29.02 | 26.34 | **22.64** |
|  - Math | 59.51 | 69.47 | **53.60** | *25.45* | **28.52** | 20.88 |
|  - Code | 56.94 | *64.24* | 41.96 | 27.68 | **27.65** | 19.57 |
|  - Safety | *56.71* | 64.35 | *41.59* | 30.13 | **29.38** | *17.19* |
|  - Finance | 61.94 | 67.06 | **50.65** | 27.90 | *20.45* | 18.68 |{{< /table-caption >}}
> 🔼 표 8은 특정 도메인을 제외하고 훈련시킨 모델의 성능을 평가하는 결과를 보여줍니다. 빨간색 값은 각 열에서 가장 큰 성능 저하를 나타냅니다. '-' 기호는 훈련에서 특정 도메인이 제거되었음을 나타냅니다. 수학적 추론을 제외하면 IFEval 성능이 크게 향상되는 반면, 안전 도메인을 제거하면 MMLU Pro 성능이 향상됩니다.  이 표는 다양한 도메인의 훈련 데이터가 모델 성능에 미치는 영향을 분석한 것입니다. 특정 도메인의 데이터를 제외했을 때, 다른 도메인의 성능에 어떤 영향을 주는지 자세히 살펴봅니다.  수학, 안전, 코딩, 금융, 지시사항 따르기 등 다섯 개의 도메인 데이터셋을 각각 제외한 경우에 대한 실험 결과를 보여주는 것으로,  각 도메인 데이터가 모델의 전반적인 추론 능력에 얼마나 중요한 역할을 하는지 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Leave-one-out experiment results, assessing the impact of removing specific domains from training. red values highlight the largest performance drop in each column. The “-” symbol denotes the removal of the corresponding domain from training. Excluding mathematical reasoning strongly improves IFEval performance, while safety removal boosts MMLU Pro.
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