---
title: "Enhancing Cognition and Explainability of Multimodal Foundation Models with Self-Synthesized Data"
summary: "자체 생성 데이터를 활용, LMM의 인지 및 설명 가능성 향상!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Vision-Language Models", "🏢 School of Computing, University of Georgia",]
showSummary: true
date: 2025-02-19
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.14044 {{< /keyword >}}
{{< keyword icon="writer" >}} Yucheng Shi et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-21 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.14044" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.14044" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/enhancing-cognition-and-explainability-of" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 다중 모드 모델(LMM)은 다양한 시각적 작업에서 인상적인 성능을 보이지만, 세분화된 시각적 추론과 정당한 설명 제공에는 어려움을 겪습니다. 특히, 도메인 특정 지식이 필요한 시각적 분류 작업에서 LMM의 성능이 크게 저하되는 현상이 관찰됩니다. 기존의 방법들은 충분한 도메인 특정 데이터가 부족하여 한계를 보였습니다.

본 논문에서는 이러한 문제를 해결하기 위해 **자체 생성 데이터를 활용하는 새로운 시각적 거부 샘플링 프레임워크**를 제안합니다. 이 프레임워크는 해석 가능한 답변을 생성하고, 보상 모델이 없는 필터링 메커니즘을 통해 고품질의 해석 가능한 답변을 선택하여 모델의 미세 조정을 반복적으로 수행합니다. 실험 결과는 제안된 방법이 특수 시각 분류 작업에서 모델의 정확성과 설명 가능성을 모두 향상시키는 효과를 보임을 보여줍니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 새로운 시각적 거부 샘플링 프레임워크를 통해 LMM의 인지 및 설명 가능성 향상 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 도메인 특정 시각적 특징을 식별하고 해당 레이블과 연결하는 LMM의 능력 향상 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 정확하고 타당한 설명을 생성하는 모델의 능력 향상 및 다양한 시각적 분류 작업에서 성능 향상 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대규모 다중 모드 모델(LMM)**의 인지 및 설명 가능성을 향상시키는 데 중요한 의미를 지닙니다. 특히, **도메인 특정 시각적 분류 작업에서 LMM의 성능 저하 문제**를 해결하기 위한 새로운 방법을 제시하고, 자체 생성 데이터를 사용하여 모델의 정확도와 설명 가능성을 향상시키는 효과적인 접근 방식을 보여줍니다. 이는 **설명 가능한 AI 분야**의 발전에 기여하며, 다양한 도메인에서 **LMM의 활용 가능성**을 확장하는 데 중요한 영향을 미칠 것으로 예상됩니다.  또한, 제안된 방법은 다른 분야에도 적용될 수 있어 폭넓은 파급 효과가 기대됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.14044/x1.png)

> 🔼 그림 1은 LLaVA-1.5 모델이 개별 이미지의 주요 시각적 특징을 활용하여 추론하고 분류 작업에서 예측에 대한 설명을 생성하는 데 어려움을 겪는다는 것을 보여줍니다.  이미지에 제시된 새의 종을 식별하고 그 이유를 설명하는 두 가지 예시를 보여줍니다.  LLaVA-1.5는 이미지의 배경이나 일반적인 특징에 의존하여 잘못된 종을 예측하고 부적절한 설명을 제공합니다. 이는 모델이 도메인 특정 목표를 식별하고 정당한 설명을 제공하는 데 어려움을 겪음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: LLaVA-1.5 struggles to utilize key visual features in images for reasoning and explaining predictions in classification tasks.
> </details>





{{< table-caption >}}
| Dataset | Method | Accuracy ↑ | Per Iteration | Explanation | Quality | General | Ability | EE ↑ | CS ↑ | FS ↓ | MMMU ↑ |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| CUB-200 | Base | 2.69 | – | – | – |  |  | 0.92 | 0.67 | 4.28 | 35.56 |
|  | NL | 73.42 | 78.25 | 79.94 | 82.21 |  |  | 0.00 | – | – | 35.67 |
|  | L+GE | 61.48 | 72.23 | 73.23 | 73.06 |  |  | 1.00 | 0.70 | 6.84 | 34.89 |
|  | Ours | 80.24 | 83.76 | 84.69 | 85.02 |  |  | 1.00 | 0.82 | 6.53 | 35.00 |
| Stanford dogs | Base | 12.2 | – | – | – |  |  | 0.94 | 0.69 | 5.47 | 35.56 |
|  | NL | 82.73 | 82.34 | 84.03 | 84.27 |  |  | 0.00 | – | – | 34.67 |
|  | L+GE | 73.45 | 77.89 | 78.15 | 76.55 |  |  | 1.00 | 0.77 | 7.50 | 34.56 |
|  | Ours | 85.29 | 86.75 | 86.86 | 86.91 |  |  | 1.00 | 0.86 | 7.41 | 34.56 |
| FGVC-A | Base | 3.00 | – | – | – |  |  | 0.97 | 0.42 | 5.39 | 35.56 |
|  | NL | 83.47 | 87.28 | 87.82 | 87.73 |  |  | 0.00 | – | – | 35.56 |
|  | L+GE | 72.13 | 79.87 | 82.45 | 82.69 |  |  | 1.0 | 0.76 | 8.59 | 35.56 |
|  | Ours | 88.78 | 90.91 | 91.42 | 91.99 |  |  | 1.0 | 0.79 | 7.00 | 37.33 |
| PLD | Base | 0.00 | – | – | – |  |  | 0.95 | – | – | 35.56 |
|  | NL | 89.38 | 94.52 | 94.29 | 93.95 |  |  | 0.00 | – | – | 34.78 |
|  | L+GE | 24.03 | 25.27 | 24.56 | 24.90 |  |  | 1.00 | 0.76 | 10.45 | 35.44 |
|  | Ours | 75.96 | 92.80 | 96.59 | 97.16 |  |  | 1.00 | 0.86 | 9.01 | 35.22 |
| HAM10000 | Base | 1.62 | – | – | – |  |  | 0.98 | 0.63 | 3.93 | 35.56 |
|  | NL | 77.28 | 80.75 | 82.49 | 81.71 |  |  | 0.00 | – | – | 35.33 |
|  | L+GE | 7.47 | 8.83 | 9.35 | 8.45 |  |  | 1.00 | 0.94 | 9.68 | 35.22 |
|  | Ours | 79.37 | 82.29 | 83.69 | 85.06 |  |  | 1.00 | 0.87 | 7.43 | 35.89 |
| Chest X-ray Pneumonia (LLaVA-Med) | Base | 62.50 | – | – | – |  |  | 1.00 | 0.24 | 3.49 | – |
|  | NL | 85.58 | 89.10 | 85.90 | 89.58 |  |  | 0.00 | – | – | – |
|  | L+GE | 62.50 | 62.50 | 62.98 | 62.66 |  |  | 1.00 | 0.79 | 7.19 | – |
|  | Ours | 97.60 | 96.31 | 99.04 | 98.72 |  |  | 1.00 | 0.87 | 8.25 | – |{{< /table-caption >}}

> 🔼 표 1은 제안된 방법이 다양한 데이터셋에서 우수한 정확도와 설명 가능성을 달성함을 보여줍니다.  각 데이터셋(CUB-200, Stanford Dogs, FGVC-Aircraft, PLD, HAM10000, Chest X-Ray)에 대해 기준 모델(Base), 레이블만으로 학습한 모델(NL), 레이블과 일반적인 설명으로 학습한 모델(L+GE), 그리고 제안된 방법(Ours)의 정확도(Accuracy)와 설명의 질(Explanation Quality)을 비교합니다. 정확도는 4가지 지표(1,2,3,4)로 측정되며, 설명의 질은 설명의 존재 여부(EE), 인지 수준(CS), 유창성(FS), 일반화 능력(MMMU) 등으로 평가됩니다.  이 표는 제안된 방법이 기존 방법들보다 우수한 성능을 보임을 명확하게 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Our method achieves superior accuracy and explanation quality across diverse datasets.
> </details>





### In-depth insights


#### LMM Explainability
본 논문은 LMM(대규모 다중 모드 모델)의 설명 가능성을 향상시키는 데 중점을 둡니다. **핵심 아이디어는 자체 생성 데이터를 사용하여 LMM의 인지 능력과 설명 가능성을 향상시키는 새로운 시각적 거절 샘플링 프레임워크를 제시하는 것**입니다. 이는 해석 가능한 답변을 생성하고, 보상 모델이 없는 필터링 메커니즘을 사용하여 고품질 답변을 선택하고, 데이터 합성 및 미세 조정의 반복적인 과정을 통해 모델의 성능을 향상시키는 것을 포함합니다. **실험 결과는 특수 시각 분류 작업에서 정확도와 설명 가능성을 모두 향상시키는 방법의 효과를 보여줍니다.**  **특히, 이미지 특징을 선택하는 정보 병목 기술과 보상 모델이 없는 거절 샘플링 기법은 LMM의 설명 가능성 향상에 중요한 역할**을 합니다.  또한, 본 연구는 이러한 방법이 단순히 레이블만 사용하거나 일반적인 레이블 수준 특징만 사용하는 것보다 우수함을 보여주는 다양한 데이터셋에 대한 실험 결과를 제시합니다.  **결론적으로, 이 논문은 LMM의 설명 가능성을 높이는 효과적인 방법을 제시하며, 특수 시각 작업에서 LMM의 적용 가능성을 확장**하는 데 기여합니다. 

#### Data Synthesis
본 논문에서 제시된 데이터 합성 방법은 **해석 가능한 답변을 생성하기 위해 이미지, 질문, 답변 세 가지 요소를 결합**하는 접근 방식을 사용합니다. 이는 단순히 레이블만을 사용하는 기존 방법과 달리, 모델이 이미지의 시각적 특징을 이해하고 정당화할 수 있도록 돕습니다. 특히, 전문가가 정의한 개념을 기반으로 시각적 특징을 도출하고, 정보 병목 현상 기법을 통해 가장 관련성 높은 특징을 선택하여 해석 가능한 답변으로 변환하는 과정이 핵심입니다.  **반복적인 데이터 합성 및 미세 조정 과정**을 통해 모델은 점진적으로 정확하고 타당한 설명을 생성하는 능력을 향상시킵니다. 이는 **단순히 정확도 향상 뿐 아니라 설명 가능성까지 높이는 데 기여**하며, 특히 전문 분야의 시각적 분류 작업에서 유용하게 활용될 수 있습니다.  **보상 모델이 없는 필터링 메커니즘**을 통해 저품질 데이터를 걸러내고 고품질 데이터만을 사용함으로써 모델의 성능 향상과 안정성을 확보합니다.

#### Iterative Tuning
반복적 미세조정(Iterative Tuning)은 제한된 양의 고품질 훈련 데이터를 사용하여 다중 모드 기반 모델의 성능과 설명력을 향상시키는 데 중점을 둡니다. **핵심 아이디어는 모델이 스스로 해석 가능한 응답을 생성하고, 필터링 메커니즘을 통해 가장 우수한 응답만을 선택하여 다음 훈련 라운드에 사용하는 반복적 과정을 통해 데이터를 자체적으로 생성하고 개선하는 것입니다.** 이는 수작업 주석이 어려운 영역에서 특히 유용하며, **모델의 인지 능력과 설명 가능성을 향상**시킵니다.  각 반복마다 모델은 더욱 정확하고 이유 있는 설명을 생성하고, 데이터 품질이 향상되어 성능이 점진적으로 개선됩니다.  **보상 모델이 없는 필터링 기법**을 사용하여 고품질 데이터를 선택함으로써, 오버피팅을 방지하고 모델의 일반화 성능을 높입니다.  **정보 이론적 접근 방식**을 사용하여 이미지의 핵심 시각적 개념을 선택하고, 이를 해석 가능한 응답으로 변환하는 과정은 모델의 설명력 향상에 크게 기여합니다.  이러한 반복적 미세조정 전략은 특정 도메인의 시각적 분류 작업에서 모델의 정확성과 설명 가능성을 모두 향상시킵니다.

#### Concept Selection
본 논문에서 제시된 개념 선택(Concept Selection) 방법은 이미지의 시각적 특징을 정확하게 파악하고, 이를 설명 가능한 답변으로 변환하는 데 중요한 역할을 합니다. **정보 이론적 접근 방식**을 사용하여 이미지 내용과 관련성이 높으면서도 중복성이 적은 시각적 개념을 선택하는데, **InfoNCE 손실 함수**를 이용하여 고차원 이미지 공간에서의 상호 정보량을 효율적으로 계산합니다.  여러 개의 이미지 설명을 생성하고 이들을 종합하여 이미지 특징의 진정한 분포를 근사함으로써 개별 설명의 불완전성을 해결하려는 시도가 돋보입니다.  **반복적인 미세 조정 과정**을 통해 모델이 정확하고 논리적인 설명을 생성할 수 있도록 개선하며, **보상 모델이 없는 필터링 메커니즘**을 사용하여 최고 품질의 설명만을 다음 단계의 미세 조정에 사용합니다. 이러한 과정을 통해, 모델은 특정 시각적 분류 작업에서 정확도와 설명 가능성을 모두 향상시킬 수 있습니다.  **이미지 특징과 설명의 정합성을 정량적으로 평가**함으로써 설명의 품질을 효과적으로 관리하고, 최적의 설명을 선택하는 데 도움을 줍니다.

#### Cross-dataset Transfer
본 논문에서 다룬 cross-dataset transfer 성능 분석은 **제한된 성공**을 보였습니다. 특정 데이터셋(CUB-200)에서 학습된 모델을 다른 데이터셋(Stanford Dogs)에 적용했을 때, 성능 향상은 있었지만, **동일 데이터셋으로 학습한 모델보다 훨씬 낮았습니다.** 이는 **도메인 특이적 미세 조정의 중요성**을 강조하며, 일반적인 인지 능력 향상에는 도움이 되지만, 특정 분야의 높은 정확도 달성에는 전문적인 미세 조정이 필수적임을 시사합니다.  **일반화된 인지 능력 향상과 특정 도메인 전문성 사이의 균형**을 고려해야 하며, 추후 연구에서는 이러한 **일반화와 전문성의 균형**을 개선하기 위한 방안을 모색해야 할 것입니다.  결론적으로, cross-dataset transfer는 **일반적인 성능 향상**에는 기여할 수 있지만, 특정 과제에 대한 높은 정확도를 보장하지는 못하므로, **데이터셋 특징을 고려한 전략**이 필요함을 알 수 있습니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.14044/x2.png)

> 🔼 그림 2는 질문 Q에 대한 합성 답변의 예시를 보여줍니다. 첫 번째와 두 번째 유형의 데이터로 학습할 경우, 모델이 이미지의 세부적인 특징을 제대로 이해하지 못하고, 단순한 상관관계에만 의존하여 잘못된 예측을 하거나 지나치게 일반적인 설명을 생성하는 지름길 학습 또는 과잉 일반화 문제가 발생할 수 있음을 보여줍니다.  즉, 이미지 특징에 대한 진정한 이해 없이 단순히 레이블 또는 일반적인 특징에만 기반하여 답변을 생성하는 문제점을 시각적으로 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Examples of synthesized answers for query Q. Training with the first two types leads to shortcut learning or overgeneralization.
> </details>



![](https://arxiv.org/html/2502.14044/x3.png)

> 🔼 이 그림은 논문의 3장 Methodology 섹션에 있는 그림 3입니다. 이 그림은 데이터 합성과 모델 미세 조정의 반복적인 접근 방식을 보여주는 프레임워크를 설명합니다. 그림에서는 먼저 기본적인 다중 모달 모델(LLaVA)을 사용하여 초기 데이터를 합성하고, 이를 사용하여 모델을 미세 조정합니다. 미세 조정 후에는 보상 모델이 없는 필터링 메커니즘을 적용하여 고품질의 해석 가능한 답변을 선택하고 다음 미세 조정 라운드에 사용합니다. 이러한 데이터 합성과 미세 조정의 반복적인 프로세스를 통해 모델의 정확성과 설명 가능성을 향상시킵니다.  단계별로 살펴보면, 먼저 이미지와 레이블을 사용하여 이미지 수준의 시각적 개념을 선택하고, 이를 바탕으로 해석 가능한 답변을 생성합니다. 그런 다음, 보상 모델이 없는 필터링 메커니즘을 사용하여 고품질의 답변을 선택하고 다음 미세 조정 라운드에 사용합니다. 이 과정을 반복하여 모델의 정확성과 설명 가능성을 향상시키는 것이 핵심입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Our framework: An iterative approach of data synthesis and model fine-tuning.
> </details>



![](https://arxiv.org/html/2502.14044/x4.png)

> 🔼 그림 4는 본 논문에서 제안하는 방법을 사용하여 생성된 답변들이 세부적인 시각적 설명을 포함하고 있음을 보여줍니다. 각각의 이미지에 대해 모델이 생성한 답변은 해당 이미지의 특징적인 시각적 요소들을 자세하게 설명하며, 이를 통해 모델의 추론 과정을 명확하게 이해할 수 있도록 돕습니다.  다양한 종류의 이미지들(새, 개, 비행기 등)에 대한 답변들이 포함되어 있으며, 각각의 답변은 해당 객체의 특징적인 시각적 요소를 언급하여 답변의 정확성과 신뢰성을 높입니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Our generated answers contain detailed visual explanations.
> </details>



![](https://arxiv.org/html/2502.14044/x5.png)

> 🔼 그림 5는 제안된 방법이 GPT-40을 사용하는 방법에 비해 개념 선택 정확도가 우수함을 보여줍니다.  이 그래프는 이미지당 설명 개수가 증가함에 따라 제안된 방법의 정밀도가 어떻게 향상되는지를 보여줍니다.  GPT-40을 사용하는 기준 방법과 비교하여 제안된 방법의 성능 우수성을 시각적으로 명확하게 제시합니다.  다양한 설명 개수에 따른 정밀도의 변화를 통해 제안된 방법의 효율성과 안정성을 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Our method demonstrates superior precision in concept selection compared to applying GPT-4o.
> </details>



![](https://arxiv.org/html/2502.14044/x6.png)

> 🔼 그림 6은 같은 레이블을 가진 객체들에 대해 서로 다른 이미지 수준의 시각적 개념들을 보여줍니다.  즉, 같은 종류의 동물이나 식물이라도 이미지마다 다양한 시각적 특징들이 나타날 수 있음을 보여주는 예시입니다. 예를 들어, 같은 품종의 강아지 사진이라도 이미지에 따라 강조되는 시각적 특징 (털 색깔, 귀 모양, 얼굴 표정 등)이 다를 수 있습니다. 이는 모델이 이미지의 다양한 측면을 포착하고, 단순한 레이블 분류를 넘어 이미지의 세부적인 시각적 특징을 이해해야 함을 시사합니다. 따라서 이 그림은 본 논문에서 제시하는 방법론의 중요성을 강조하는 역할을 합니다. 즉, 모델이 이미지의 다양한 시각적 특징들을 잘 이해해야 정확하고 설명 가능한 예측을 할 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Different image-level visual concepts for objects with the same label.
> </details>



![](https://arxiv.org/html/2502.14044/x7.png)

> 🔼 그림 7은 서로 다른 데이터셋에 대한 히트맵 시각화를 보여줍니다. 각 그룹은 원본 이미지, NL 모델의 히트맵, 그리고 제안된 방법의 히트맵 세 가지 이미지로 구성됩니다. 이는 각 모델이 이미지의 어떤 부분에 주목하여 예측을 내리는지 시각적으로 비교 분석하기 위함입니다. 히트맵은 밝은 색상으로 나타낼수록 해당 영역이 예측에 더 큰 영향을 미쳤음을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 7:  Visualization of heatmaps for different datasets. From left to right in each triplet: Original Image, Heatmap of NL model, Heatmap of Ours.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Accuracy ↑ |
|---|---| 
| Per Iteration |{{< /table-caption >}}
> 🔼 표 2는 제안된 방법으로 미세 조정된 대규모 다중 모드 모델(LMM)이 사용자의 신뢰도를 높이는 검증 가능한 세부 정보를 제공함을 보여줍니다.  표에는 사용자 질문과 모델의 응답이 포함되어 있으며, 모델이 이미지의 시각적 특징을 사용하여 정확하고 설명 가능한 답변을 생성하는 능력을 보여줍니다. 각 예시는 모델이 어떻게 이미지의 세부 사항을 파악하고 이를 사용하여 답변을 뒷받침하는지 보여주는 구체적인 시각적 설명과 함께 제공됩니다.
> <details>
> <summary>read the caption</summary>
> Table 2: LMMs fine-tuned with our method provide verifiable details, enhancing user trust.
> </details>

{{< table-caption >}}
| Explanation | Quality |
|---|---|{{< /table-caption >}}
> 🔼 이 표는 CUB-200 데이터셋에서 새 이미지 분석을 위한 세 가지 프롬프트를 보여줍니다. 각 프롬프트는 이미지에서 새의 외형을 설명하는 데 중점을 두고 있으며, 배경이나 다른 요소는 언급하지 않습니다. 세 가지 프롬프트는 모두 유사하지만, 표현 방식에 미묘한 차이가 있어 모델이 다양한 관점에서 이미지를 분석하도록 유도합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Prompts for bird image analysis in CUB-200 dataset
> </details>

{{< table-caption >}}
| General | Ability |
|---|---|{{< /table-caption >}}
> 🔼 이 표는 논문의 3.2절 'Step 1: IMAGE-LEVEL VISUAL CONCEPT SELECTION'에서 사용된, 다양한 데이터셋에 대한 응답 재작성 프롬프트를 보여줍니다.  각 데이터셋 (CUB-200, Stanford Dogs, HAM10000, PLD, Chest X-ray)에 대해, 이미지의 시각적 특징을 설명하는 프롬프트와 질문을 생성하는 프롬프트를 제공하여, 모델이 이미지의 내용을 이해하고 설명하는 응답을 생성하도록 유도합니다.  이를 통해 생성된 응답의 질과 해석성을 높이는 것을 목표로 합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Answer rewrite prompts for different datasets.
> </details>

{{< table-caption >}}
| Image | Conversation |
|---|---| 
| https://arxiv.org/html/2502.14044/x8.jpg | User: What is the name of this leaf disease? Can you give me your reason?<br>LMM: The name of this leaf disease is **Bell Pepper Leaf with Bacterial Spot Disease**. The reason for this name is that the leaf has _brown or black necrotic spots_, which are characteristic of bacterial infections. These spots can coalesce, forming _larger necrotic areas_, and the leaf may exhibit _chlorosis or yellowing_ of surrounding leaf tissue. The spots are often located on _the underside of the leaf_, and the leaf may become _crinkled or deformed_ near affected areas. |
| https://arxiv.org/html/2502.14044/extracted/6217851/Figures/case_2.jpg | User: OK then, what chemical should I use to treat this disease?<br>LMM: It is recommended to use a **copper-based fungicide** to treat this disease.<br>User: Identify this bird. What features led to your conclusion?<br>LMM: The bird is a **male Northern Cardinal** with a _bright red plumage_ on its head, throat, and chest. The presence of _a crest on its head_ and a _black ”mask” around its eyes_ further supports the identification of this bird.<br>User: Where can I find this bird?<br>LMM: You can find this bird in **the United States**, specifically in the **eastern and central parts** of the country. The Northern Cardinal is a common resident bird in areas with dense woodlands, shrubs, and gardens.|{{< /table-caption >}}
> 🔼 표 5는 일반적인 이미지 데이터셋에 대해 이미지 특징을 기반으로 질문에 답하는 프롬프트를 보여줍니다.  이 표는 모델이 이미지의 시각적 특징을 사용하여 질문에 답할 수 있도록  구체적인 지시 사항을 제공하는 다양한 프롬프트를 제시합니다.  각 프롬프트는 이미지 특징을 묘사하고, 해당 이미지 특징에 근거한 응답을 생성하도록 모델을 안내합니다. 이를 통해, 모델은 단순히 레이블을 출력하는 대신, 이미지 내용을 이해하고 설명하는 능력을 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Prompt for answering questions based on image characteristics for general image datasets.
> </details>

{{< table-caption >}}
| Dataset Name | Test / Training Cases | Label Categories | Running Time Per Iter |
|---|---|---|---| 
| CUB-200-2011 | 5,794 / 5,994 | 200 | 143 minutes |
| FGVC-Aircraft | 3,333 / 6,667 | 100 | 171 minutes |
| Stanford Dogs | 8,580 / 12,000 | 120 | 310 minutes |
| Chest X-ray images | 624 / 5,216 | 2 | 113 minutes |
| HAM1000 | 5,008 / 5,007 | 7 | 107 minutes |
| PLD | 47,523 / 5,279 | 37 | 109 minutes |{{< /table-caption >}}
> 🔼 표 6은 모델이 생성한 답변의 설명 존재 여부(EE)와 인지 점수(CS)를 평가하기 위한 프롬프트들을 보여줍니다. EE 프롬프트는 답변에 유효한 설명이 포함되어 있는지 여부를 평가하고, CS 프롬프트는 제공된 개념들과 설명의 일관성 및 논리적 정합성을 평가합니다.  두 프롬프트 모두 정확하고 신뢰할 수 있는 평가를 위해 설계되었으며, 모델의 설명 능력을 객관적으로 평가하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Prompts for Explanation Existence (EE) and Cognition Score (CS).
> </details>

{{< table-caption >}}
| Image | User | LMM |
|---|---|---|
| [https://arxiv.org/html/2502.14044/image2.png](https://arxiv.org/html/2502.14044/image2.png) | Based on the visual content, what is the specific name of this bird? Provide an explanation. | The specific name of this bird is the Yellow breasted Chat. This bird is known for its bright yellow throat and chest, olive-green back, wings, and tail, and short, rounded wings. It is a small bird that is commonly found in the Americas, particularly in the United States and Canada. |
| [https://arxiv.org/html/2502.14044/image3.png](https://arxiv.org/html/2502.14044/image3.png) | Based on the visual content, what is the specific name of this bird? Provide an explanation. | The specific name of this bird is the Blue Grosbeak. The Blue Grosbeak is a small, colorful bird with a deep blue overall plumage in males and a brown overall coloration with subtle blue tinges and faint streaking in females. The bird has a slightly glossy sheen to its blue feathers and is known for its melodious songs. |
| [https://arxiv.org/html/2502.14044/image4.png](https://arxiv.org/html/2502.14044/image4.png) | Based on the visual content, what is the specific name of this bird? Provide an explanation. | The specific name of this bird is the Orchard Oriole. The bird has a black head, back, throat, and upper chest, with a rich chestnut-brown underparts. It has a black tail and a black throat patch developing. The bird’s wings are black with white wing bars, and it has a black bill. The Orchard Oriole is a small bird with a distinctive appearance, and it is known for its melodious songs. |
| [https://arxiv.org/html/2502.14044/image5.png](https://arxiv.org/html/2502.14044/image5.png) | Based on the visual content, what is the specific name of this bird? Provide an explanation. | The specific name of this bird is the Black throated Sparrow. This bird is known for its distinctive black throat patch and white stripe below its eyes. It is a small bird with a brown and white coloration, and it is often seen perched on branches or low vegetation.  |
| [https://arxiv.org/html/2502.14044/image6.png](https://arxiv.org/html/2502.14044/image6.png) | Based on the visual content, what is the specific name of this bird? Provide an explanation. | The specific name of this bird is the Henslow Sparrow. This bird is known for its olive-colored head, short, pointed bill, and pale eye-ring. It is a small bird with a brown and white coloration, and it is often seen flitting low in dense grassy habitats. |{{< /table-caption >}}
> 🔼 표 7은 개념 추출을 위한 프롬프트들을 보여줍니다.  더 자세히 설명하자면, 각 클래스 레이블에 일반적으로 연관된 시각적 특징들을 추출하기 위해 GPT-40에게 제시된 프롬프트들의 예시입니다.  이를 통해, 이미지에서 특정 클래스에 해당하는 중요한 시각적 특징들을 효과적으로 식별하는 데 도움이 됩니다.  예시로는 색상 패턴, 모양, 독특한 표식 등을 언급하는 프롬프트가 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Prompts for Concept Extraction.
> </details>

{{< table-caption >}}
| ![dog1](https://arxiv.org/html/2502.14044/dog1.png) | Concepts: | "Powerful, thick neck" |
|---|---|---|
|  |  | "Broad and strong back" |
|  |  | "Large and muscular build" |
|  |  | "Well-sprung ribs" |
| ![dog2](https://arxiv.org/html/2502.14044/dog2.png) | Concepts: | "Pure white or cream-colored fur" |
|---|---|---|
|  |  | "Well-feathered tail that blends with the body fur" |
|  |  | "Strong, straight legs" |
|  |  | "Broad head with a slightly rounded skull" |
| ![dog3](https://arxiv.org/html/2502.14044/dog3.png) | Concepts: | "Straight, arched tail that rests on the back" |
|---|---|---|
|  |  | "Broad, flat skull" |
|  |  | "Thick double coat, either rough or smooth" |
| ![dog4](https://arxiv.org/html/2502.14044/dog4.png) | Concepts: | "Deep-set, almond-shaped eyes" |
|---|---|---|
|  |  | "Erect, triangular ears" |
|  |  | "Thick ruff of fur around the neck" |
|  |  | "Thick double coat, either rough or smooth" |
| ![dog5](https://arxiv.org/html/2502.14044/dog5.png) | Concepts: | "Ears: Large, bat-like ears that stand erect and move attentively." |
|---|---|---|
|  |  | "Distinctive facial features: Elongated muzzle with a moderate stop and expressive eyes." |
|  |  | "Whiskers: Short or absent due to the lack of hair follicles around the muzzle area." |{{< /table-caption >}}
> 🔼 표 8은 논문에서 사용된 데이터셋들의 요약 정보를 보여줍니다.  각 데이터셋의 이름, 테스트/훈련 데이터 수, 레이블 카테고리 수, 그리고 각 반복당 실행 시간이 포함되어 있습니다.  CUB-200, FGVC-Aircraft, Stanford Dogs, Chest X-Ray, HAM1000, 그리고 PLD 데이터셋이 포함되어 있으며, 각 데이터셋의 크기와 레이블의 수가 다름을 보여줍니다. 이 정보는 데이터셋의 규모와 특징을 이해하는 데 도움이 되며, 실험 결과를 해석하는 데 중요한 맥락을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Summary of Selected Datasets
> </details>

{{< table-caption >}}
| Model | MMStar | SEED-Bench-2 Plus | MMBench | MME (Cognition) | Overall Improvement |
|---|---|---|---|---|---| 
| LLaVA-1.5 (Base) | 34.46 | 41.81 | 63.05 | 334.28 | – |
| Trained on CUB-200 | 33.40 | 41.78 | 63.14 | 355.00 | 3.2%↑ |
| Trained on Stanford Dogs | 34.93 | 40.97 | 63.06 | 365.71 | 8.3%↑ |
| Trained on FGVC-Aircraft | 35.14 | 40.14 | 63.23 | 348.57 | 2.1%↑ |
| Trained on PLD | 35.30 | 40.89 | 63.14 | 337.14 | 1.1%↑ |
| Trained on HAM10000 | 34.46 | 41.11 | 64.08 | 378.21 | 12.9%↑ |{{< /table-caption >}}
> 🔼 표 9는 모델이 생성한 답변의 예시들을 보여줍니다. 각 예시는 사용자의 질문과 모델이 생성한 답변(이미지에 대한 설명 포함)으로 구성됩니다. 이를 통해 모델이 생성한 답변의 품질과 설명의 적절성을 직관적으로 확인할 수 있습니다.  각 예시는 다양한 종류의 이미지(새, 비행기 등)를 포함하며, 모델이 이미지의 시각적 특징을 얼마나 잘 파악하고 설명하는지 보여주는 대표적인 사례들입니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Generated Answer Examples.
> </details>

{{< table-caption >}}
| Dataset | Method | Accuracy (Iter 1) | Accuracy (Iter 2) | Accuracy (Iter 3) | Accuracy (Iter 4) | CS Score |
|---|---|---|---|---|---|---|
| CUB-200 | w/o Filtering | 68.90 | 70.11 | 70.85 | 70.45 | 0.71 |
|  | Ours | 80.24 | 83.76 | 84.69 | 85.02 | 0.82 |
| FGVC-Aircraft | w/o Filtering | 76.36 | 76.60 | 77.11 | 76.78 | 0.72 |
|  | Ours | 88.78 | 90.91 | 91.42 | 91.99 | 0.79 |
| Stanford Dogs | w/o Filtering | 76.60 | 78.53 | 78.61 | 78.26 | 0.74 |
|  | Ours | 85.29 | 86.75 | 86.86 | 86.91 | 0.86 |
| PLD | w/o Filtering | 61.19 | 63.74 | 62.32 | 62.59 | 0.66 |
|  | Ours | 75.96 | 92.80 | 96.59 | 97.16 | 0.86 |
| HAM10000 | w/o Filtering | 71.79 | 72.10 | 72.34 | 72.29 | 0.75 |
|  | Ours | 79.37 | 82.29 | 83.69 | 85.06 | 0.87 |{{< /table-caption >}}
> 🔼 표 10은 다양한 이미지 데이터셋에서 사용된 개념 선택의 예시를 보여줍니다. 각 이미지에 대해 전문가가 정의한 시각적 개념들의 하위 집합이 선택되어, 이미지와 레이블 사이의 연결을 설명하는 데 사용됩니다.  이 표는 본 논문의 개념 선택 방법의 품질과 유용성을 보여주는 데 도움이 됩니다. 각 이미지에 대한 선택된 개념들은 해당 이미지의 주요 시각적 특징을 잘 반영하고 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Selected Concepts Examples.
> </details>

{{< table-caption >}}
| Text Encoder | Concept Selection Accuracy (%) |
|---|---| 
| E5 | 72.9 |
| BERT-Large | 71.4 |
| BERT-Base | 69.7 |{{< /table-caption >}}
> 🔼 표 11은 다양한 벤치마크에서 평가된 일반적인 능력을 보여줍니다. 결과는 미세 조정된 모델이 기본 LLaVA-1.5 모델에 비해 전반적인 성능 향상을 달성했을 뿐만 아니라 일반적인 능력도 유지했음을 보여줍니다.  각 벤치마크의 점수를 비교하여 미세 조정이 모델 성능에 미치는 영향을 자세히 살펴볼 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 11: General ability evaluation across additional benchmarks. The results demonstrate that our fine-tuned models not only retain their general abilities but also achieve overall improvements compared to the base LLaVA-1.5 model.
> </details>

{{< table-caption >}}
| Training Dataset | Evaluation Dataset | Accuracy (%) |
|---|---|---|
| None | Stanford Dogs | 12.20 |
| CUB-200 | Stanford Dogs | 16.60 |
| Stanford Dogs | Stanford Dogs | 86.91 |{{< /table-caption >}}
> 🔼 표 12는 필터링 없이 기준 모델을 사용했을 때와 제안된 방법을 사용했을 때의 정확도와 인식 점수(CS)를 반복별로 비교한 것입니다.  각 반복에서 필터링 없이 얻은 결과와 제안된 방법을 사용하여 얻은 결과를 비교하여 필터링 전략의 효과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 12: Comparison of accuracy and cognition scores (CS) for the baseline without filtering and our proposed method across iterations.
> </details>

{{< table-caption >}}
| Dataset | CS Value (Iter 1) | CS Value (Iter 2) | CS Value (Iter 3) | CS Value (Iter 4) | CS Improvement |
|---|---|---|---|---|---| 
| CUB-200 | 0.77 | 0.76 | 0.78 | 0.82 | 6.5%↑ |
| Stanford Dogs | 0.82 | 0.84 | 0.83 | 0.86 | 4.9%↑ |
| FGVC-Aircraft | 0.78 | 0.78 | 0.78 | 0.79 | 1.3%↑ |
| PLD | 0.84 | 0.85 | 0.85 | 0.86 | 2.4%↑ |
| HAM10000 | 0.77 | 0.84 | 0.83 | 0.87 | 13.0%↑ |
| Chest X-ray | 0.67 | 0.80 | 0.81 | 0.87 | 29.9%↑ |{{< /table-caption >}}
> 🔼 본 표는 다양한 Text Encoder를 사용하여 개념 선택 정확도를 비교 분석한 결과를 보여줍니다.  세 가지 Text Encoder (E5, BERT-Large, BERT-Base)를 사용하여 이미지의 핵심 시각적 특징을 나타내는 개념을 얼마나 정확하게 선택하는지 평가했습니다.  결과적으로 E5 모델이 가장 높은 정확도를 보였으며, 이는 더욱 강력한 Text Encoder를 사용하면 개념 선택의 질이 향상되고 최종 결과물의 정확성이 높아짐을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 13: Concept selection accuracy using different text encoders.
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