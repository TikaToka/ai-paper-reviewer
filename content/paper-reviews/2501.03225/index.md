---
title: "Automated Generation of Challenging Multiple-Choice Questions for Vision Language Model Evaluation"
summary: "AutoConverter는 오픈엔드 방식의 VQA 질문을 다지선다형 질문으로 자동 변환하는 시스템입니다. 이를 통해 VLM(Vision Language Model) 평가의 객관성과 재현성을 높일 수 있습니다. 연구진은 AutoConverter를 사용하여 20개의 기존 VQA 데이터셋을 통합한 VMCBench라는 새로운 벤치마크를 구축했습니다.  VMCBen..."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Question Answering", "🏢 Stanford University",]
showSummary: true
date: 2025-01-06
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.03225 {{< /keyword >}}
{{< keyword icon="writer" >}} Yuhui Zhang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-07 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.03225" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.03225" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/automated-generation-of-challenging-multiple" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 시각 언어 모델(VLM) 평가는 오픈엔드 방식의 질문에 의존하여, 자연어 응답의 다양성으로 인해 정확한 평가가 어려웠습니다. 또한, 기존의 평가 방식들은 계산 비용이 많이 들거나, 모델 버전 변경에 따라 결과가 불안정한 문제점을 가지고 있었습니다.

본 논문에서는 이러한 문제점들을 해결하기 위해, 오픈엔드 질문을 다지선다형 질문으로 자동 변환하는 AutoConverter라는 시스템을 제안합니다. AutoConverter는 여러 에이전트를 활용하여 정확하고 어려운 다지선다형 질문을 생성하며, 이를 통해 객관적이고 재현 가능한 VLM 평가를 가능하게 합니다. 연구진은 AutoConverter를 이용하여 20개의 기존 VQA 데이터셋을 통합한 VMCBench라는 새로운 벤치마크를 구축하고, 33개의 최첨단 VLM을 평가하여 새로운 평가 기준을 제시했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} AutoConverter는 오픈엔드 VQA 질문을 다지선다형 질문으로 자동 변환하여 VLM 평가의 객관성과 재현성을 향상시킵니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} VMCBench는 20개의 기존 VQA 데이터셋을 통합한 새로운 벤치마크로, 33개의 최첨단 VLM을 종합적으로 평가하고 향상된 평가 기준을 제시합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 본 연구는 VLM 평가의 어려움을 해결하고, 확장성, 일관성, 재현성 있는 평가 방식을 제시하여 향후 VLM 연구에 중요한 기여를 합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **VLMs(Vision Language Models) 평가를 위한 새로운 기준을 제시**하여, **확장성, 일관성, 그리고 재현성이 향상된 평가 방식**을 제공합니다.  이는 기존의 오픈엔드 방식 VQA 평가의 한계점을 극복하고, 향후 VLM 연구의 발전에 크게 기여할 것으로 예상됩니다.  특히, **다양한 VQA 데이터셋을 통합한 VMCBench 벤치마크**는  다른 연구자들이 VLM 성능을 객관적으로 비교하고 평가할 수 있는 중요한 자원이 될 것입니다. 또한, AutoConverter는 **오픈엔드 질문을 객관적인 다지선다형 질문으로 변환**하는 데 사용될 수 있으며, 교육 및 기타 분야에도 응용 가능성을 가지고 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.03225/x1.png)

> 🔼 그림 1은 논문의 개요를 보여줍니다. 왼쪽 부분에서는 기존의 개방형 VQA 평가 지표들을 분석하고, 정확하고 재현 가능한 평가를 제공하는 데 있어서의 한계점들을 강조합니다. 가운데 부분에서는 개방형 질문들을 자동으로 객관식 형태로 변환하는 다중 에이전트 시스템인 AutoConverter를 소개하고, 비용이 많이 드는 질문 생성 과정을 줄이면서 객관적인 평가를 가능하게 하는 방법을 설명합니다. 오른쪽 부분에서는 AutoConverter를 사용하여 기존의 20개 VQA 데이터셋을 통합된 객관식 벤치마크로 변환하고, 미래의 VLM 연구를 지원하는 방법을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Overview. (Left) We analyze existing open-ended VQA evaluation metrics, underscoring their limitations in providing accurate and reproducible assessments. (Middle) We introduce AutoConverter, a multi-agent system that automatically converts open-ended questions into multiple-choice format, enabling objective assessment while reducing the costly question creation process. (Right) Using AutoConverter, we convert and refine 20 existing VQA datasets into a unified multiple-choice benchmark to support future VLM research.
> </details>





{{< table-caption >}}
| Method | C (↑) | M<sub>1</sub> | M<sub>2</sub> | M<sub>3</sub> | M<sub>4</sub> | Avg (↓) |
|---|---|---|---|---|---|---|
| Human | 4.59 | 33.4 | 35.2 | 46.0 | 52.4 | 41.8 |
| Naive | 4.59 | 34.2 | 40.6 | 50.2 | 59.0 | 46.0 |
| w/o Concept | 4.66 | 33.6 | 37.8 | 46.4 | 57.4 | 43.8 |
| w/o Reason | 4.69 | 30.0 | 40.2 | 47.8 | 56.2 | 43.5 |
| w/o Vision | 4.68 | 29.0 | 39.2 | 45.8 | 57.2 | 42.8 |
| w/o Data | 4.66 | 29.4 | 36.6 | 47.0 | 57.8 | 42.7 |
| w/o Bias | 4.65 | 30.6 | 37.6 | 48.6 | 60.2 | 44.2 |
| w/o Reviewer | 4.64 | 30.2 | 38.2 | 45.4 | 57.2 | 42.7 |
| w/o Refiner | 4.28 | 25.0 | 34.2 | 42.0 | 50.0 | 37.8 |
| *AutoConverter* | 4.69 | 27.8 | 37.2 | 44.2 | 53.6 | 40.7 |{{< /table-caption >}}

> 🔼 표 1은 논문에서 제시된 VMCBench 테스트 세트에 대해 33개의 최첨단 VLMs(Vision Language Models)의 성능을 보여줍니다.  각 모델의 일반 추론, OCR, 문서 및 차트 이해 세 가지 하위 작업에 대한 정확도 점수와 이 세 가지 작업에 대한 가중 평균 점수를 포함하여 모델의 전반적인 성능을 평가합니다. 이 표는 다양한 VLMs의 상대적인 강점과 약점을 비교하여 VLM 성능 평가를 위한 VMCBench의 유용성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Performance of 33 VLMs on VMCBench test set.
> </details>





### In-depth insights


#### VQA Evaluation
VQA(Visual Question Answering) 평가는 VLM(Vision Language Model) 성능을 측정하는 데 매우 중요합니다. 기존의 오픈엔디드 방식은 자연어 응답의 다양성으로 인해 정확한 평가가 어렵다는 한계가 있습니다. **AutoConverter는 이러한 문제를 해결하기 위해 오픈엔디드 질문을 객관적인 다지선다형 질문으로 변환하는 프레임워크**입니다. 이는 비용이 많이 드는 질문 생성 과정을 줄이면서 객관적인 평가를 가능하게 합니다.  **AutoConverter는 GPT-4를 기반으로 한 다중 에이전트 시스템**으로, 정확하고 어려운 다지선다형 질문을 자동 생성합니다.  여러 에이전트는 질문의 정확성과 난이도를 보장하기 위해 협업하며, **VMCBench라는 통합된 다지선다형 VQA 벤치마크**를 구축하여 다양한 최첨단 VLM의 성능을 포괄적으로 평가할 수 있는 기반을 마련했습니다.  **규칙 기반 및 모델 기반 평가 방식의 한계점을 명확히 제시**하고, AutoConverter가 이를 극복할 수 있는 대안임을 보여줍니다.  **VMCBench를 통해 확장 가능하고 일관된 재현 가능한 VLM 평가의 새로운 표준**을 제시합니다.

#### AutoConverter
본 논문에서 제시된 AutoConverter는 오픈 엔드형 VQA 질문을 객관적인 다지선다형 질문으로 자동 변환하는 시스템입니다. **GPT-4를 기반으로 한 다중 에이전트 시스템**으로, 정확성과 난이도를 모두 고려하여 질문을 생성합니다.  **여러 에이전트의 협업**을 통해 정확한 답변과 함께 학습자들이 흔히 저지르는 실수를 반영한 교묘한 오답들을 생성하여, **VLMs의 실질적인 이해도를 평가**할 수 있도록 설계되었습니다. 이는 기존의 오픈 엔드형 평가 방식의 한계를 극복하고, 더욱 정확하고 재현 가능한 VLM 평가를 가능하게 하는 혁신적인 방법론으로, **VMCBench 구축**에도 중요한 역할을 합니다.  AutoConverter의 효율성과 정확성은 실험 결과를 통해 검증되었으며, **VLM 평가의 새로운 표준**을 제시합니다.

#### VMCBench
VMCBench는 기존의 개방형 VQA 데이터셋들을 **다양한 유형의 질문과 어려운 수준의 방해요소들을 포함하는 통일된 다중 선택형 벤치마크**로 변환한 것입니다. 이는 기존 평가 방식의 한계를 극복하고, **객관적이고 재현 가능한 VLM 평가를 가능하게** 합니다.  **개방형 질문의 모호성과 주관성을 제거**하여 VLMs의 성능을 더욱 정확하게 측정할 수 있다는 점이 핵심입니다.  특히, **AutoConverter라는 시스템을 통해 자동으로 질문을 변환**함으로써, 비용과 시간을 절약하면서도 고품질의 다중 선택형 질문을 생성할 수 있습니다.  VMCBench는 다양한 VLM 모델의 능력을 평가하고 비교하는 데 유용한 표준화된 벤치마크로서, 향후 VLM 연구 발전에 크게 기여할 것으로 기대됩니다.  **33개의 최첨단 VLM을 포괄적으로 평가**하여 새로운 성능 기준을 제시했으며, **확장성과 재현성을 높인 평가 방식**을 제시했다는 점에서 중요한 의의를 갖습니다.

#### Multi-agent System
본 논문에서 제시된 다중 에이전트 시스템은 **자동화된 질문 생성 및 평가**를 위한 핵심 구성 요소입니다.  **GPT-4를 기반으로 한 여러 에이전트**들이 상호 작용하며, 오픈 엔드형 질문을 객관적인 다지선다형 질문으로 변환합니다.  각 에이전트는 **질문의 정확성, 난이도, 그리고 다양성**을 높이는 데 기여합니다.  예를 들어, 제안 에이전트는 다양한 오류 유형을 고려하여 오답을 생성하고, 검토 에이전트는 생성된 오답의 적절성을 평가하고 수정하며, 선택 에이전트는 최종적으로 가장 적합한 오답들을 선택합니다.  이러한 과정을 통해, **인간의 개입 없이도 질 높은 다지선다형 질문 생성**이 가능해집니다.  **효율성과 객관성**을 높이는 데 기여하는 다중 에이전트 시스템의 설계는,  **VLMs의 신뢰할 수 있는 평가**를 위한 중요한 발전입니다.

#### Future Work
본 논문은 시각 언어 모델(VLM) 평가를 위한 객관적이고 재현 가능한 다중 선택형 질문 생성 프레임워크인 AutoConverter를 제시합니다.  **향후 연구 방향**으로는, **AutoConverter의 적용 범위 확장**이 중요합니다. 현재는 영어 데이터셋에 집중되어 있으나, 다국어 지원 및 다양한 시각적 데이터 유형에 대한 확장성을 확보해야 합니다.  또한, **질문 생성 과정의 효율성 개선**을 위해, 현재 GPT-4에 의존하는 부분을 더욱 효율적인 모델로 대체하거나, 생성 과정을 최적화하는 연구가 필요합니다.  **더욱 어려운 질문 생성**을 위해, 다양한 유형의 오류 패턴을 고려한 distractor 생성 전략을 강화하고, 인간 전문가의 피드백을 적극적으로 활용하여 질문의 질을 더욱 높일 수 있습니다.  마지막으로, **VMCBench의 확장** 또한 중요합니다. 더욱 다양한 VQA 데이터셋을 포함하여 VLM 평가의 범위를 넓히고, 특정 도메인이나 유형에 편향되지 않도록 데이터 균형을 맞추는 노력이 필요합니다.  이러한 노력을 통해 AutoConverter와 VMCBench는 VLM 연구와 개발에 더욱 기여할 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.03225/x2.png)

> 🔼 그림 2는 개방형 질문 평가의 어려움을 보여줍니다. (왼쪽) 규칙 기반 평가 지표는 모델 성능을 과소평가하고 예상 형식을 엄격히 따르지 않는 모델을 불이익을 주는 반면, (오른쪽) 두 가지 다른 버전의 GPT를 사용한 모델 기반 평가는 상당히 다른 점수를 산출하여 비교의 일관성을 저해하고 재현성 문제를 야기합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Challenges in evaluating open-ended questions. (Left) Rule-based metrics significantly underestimate model performance and penalize models that do not strictly follow the expected format. (Right) Model-based evaluations using two different versions of GPT yield substantially different scores, making comparisons inconsistent and raising reproducibility issues.
> </details>



![](https://arxiv.org/html/2501.03225/x3.png)

> 🔼 그림 (a)는 AutoConverter 프레임워크의 개념적 구조를 보여줍니다. AutoConverter는 오픈 엔드형 VQA 질문을 객관적인 다지선다형 질문으로 변환하는 과정을 자동화하는 시스템입니다. 이 그림은 AutoConverter가 질문의 정확성을 보장하고 질문의 난이도를 높이는 방법을 설명하는 다양한 구성 요소(에이전트)를 보여줍니다. 각 에이전트는 오픈 엔드형 질문을 다지선다형 질문으로 변환하는 특정 단계를 담당합니다. 이 그림은 이러한 에이전트의 상호 작용 및 각 에이전트의 역할을 시각적으로 나타냅니다.
> <details>
> <summary>read the caption</summary>
> (a) AutoConverter framework.
> </details>



![](https://arxiv.org/html/2501.03225/extracted/6113068/figures/superhuman_v2.png)

> 🔼 그림 (b)는 MMMU 데이터셋에서 AutoConverter의 성능을 ablation study를 통해 분석한 결과를 보여줍니다.  C는 정답률(높을수록 좋음), Avg는 평균 모델 성능(낮을수록 좋음)을 나타냅니다. M1은 PaliGemma-3B, M2는 LLaVA-1.5-7B, M3는 Phi-3.5-Vision, M4는 Qwen2-VL-7B 모델을 의미합니다.  각 모델의 정답률과 평균 성능을 AutoConverter의 각 구성 요소(Concept, Reason, Vision, Data, Bias, Reviewer, Refiner)를 제거했을 때의 변화를 통해 AutoConverter의 효과를 정량적으로 분석한 결과입니다.
> <details>
> <summary>read the caption</summary>
> (b) Ablation of AutoConverter on MMMU. C𝐶Citalic_C is correctness (higher is better), Avg is average model performance (lower is better). M1subscript𝑀1M_{1}italic_M start_POSTSUBSCRIPT 1 end_POSTSUBSCRIPT is PaliGemma-3B, M2subscript𝑀2M_{2}italic_M start_POSTSUBSCRIPT 2 end_POSTSUBSCRIPT is LLaVA-1.5-7B, M3subscript𝑀3M_{3}italic_M start_POSTSUBSCRIPT 3 end_POSTSUBSCRIPT is Phi-3.5-Vision, M4subscript𝑀4M_{4}italic_M start_POSTSUBSCRIPT 4 end_POSTSUBSCRIPT is Qwen2-VL-7B.
> </details>



![](https://arxiv.org/html/2501.03225/x4.png)

> 🔼 그림 3은 AutoConverter 프레임워크와 결과를 보여줍니다. 왼쪽 그림은 어려움을 증가시키고 변환된 질문의 정확성을 보장하는 두 가지 주요 단계를 가진 AutoConverter의 다중 에이전트 프레임워크를 보여줍니다. 오른쪽 그림은 AutoConverter에 대한 ablation study 결과를 보여주며, 각 구성 요소가 질문의 정확성 향상과 원하는 수준의 난이도 달성에 중요한 역할을 한다는 것을 보여줍니다.  AutoConverter는 질문의 정확성과 난이도를 높이기 위해 반복적인 정제 과정을 거치는 다중 에이전트 시스템입니다.  에이전트들은 질문의 정확성을 평가하고, 난이도를 높이는 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: AutoConverter framework and results. (Left) AutoConverter is a multi-agent framework with two key steps: increasing difficulty and ensuring the correctness of the converted question. (Right) We perform an ablation study on AutoConverter and find that each component is crucial for enhancing question correctness and achieving the desired level of difficulty.
> </details>



![](https://arxiv.org/html/2501.03225/x5.png)

> 🔼 그림 4는 AutoConverter가 생성한 다지선다형 문제의 난이도를 보여줍니다. AutoConverter를 사용하여 기존의 다지선다형 VQA 데이터셋인 MMMU, MathVista, AI2D 세 가지 데이터셋의 질문과 답변에 대한 오답 선택지를 생성하고, 이를 기존의 사람이 생성한 오답 선택지와 비교했습니다.  다양한 VLMs을 AutoConverter가 생성한 문제와 기존 문제 모두에 대해 평가한 결과, VLMs는 기존 문제보다 AutoConverter가 생성한 문제에 대해 일관되게 비슷하거나 더 낮은 정확도를 보였습니다. 이는 AutoConverter가 기존 문제와 유사하거나 더 어려운 수준의 다지선다형 문제를 생성할 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: AutoConverter generates challenging multiple-choice questions. Using AutoConverter, we generated distractors for questions and answers from three existing multiple-choice datasets: MMMU, MathVista, and AI2D, and compared them with original human-created distractors. We evaluated various VLMs on both the AutoConverter-generated and the original questions, finding that VLMs consistently achieved similar or even lower accuracy on the AutoConverter-generated questions compared to the original ones.
> </details>



![](https://arxiv.org/html/2501.03225/extracted/6113068/figures/different_generator.png)

> 🔼 그림 5는 세 가지 방식으로 생성된 객관식 질문들을 비교 분석한 것입니다. 첫 번째는 원본 질문, 두 번째는 간단한 기준선을 사용하여 생성된 질문, 세 번째는 AutoConverter를 이용하여 생성된 질문입니다. AutoConverter는 다양한 관점에서 오류를 모방하여 정확하고 어려운 객관식 질문을 생성합니다. 그림은 각 방식의 질문 예시와 함께, AutoConverter가 어떻게 다양한 오류 유형을 시뮬레이션하여 질문의 난이도를 높이는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Qualitative comparison of the original questions, naive baseline-generated questions, and AutoConverter-generated questions. AutoConverter simulates errors from different perspectives and produces correct and challenging multiple-choice questions.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | General | Reasoning | OCR | Doc&Chart | Avg. |
|---|---|---|---|---|---| 
| Qwen2-VL-72B | 88.5 | 72.6 | 96.8 | 90.1 | 85.0 |
| GPT-4o | 85.2 | 66.9 | 96.4 | 83.1 | 80.3 |
| Molmo-72B | 82.9 | 66.6 | 94.7 | 81.1 | 78.7 |
| Qwen2-VL-7B | 84.5 | 62.7 | 96.4 | 80.1 | 78.1 |
| Claude-3.5-Sonnet | 81.3 | 62.8 | 93.4 | 84.6 | 77.8 |
| Cambrian-34B | 83.7 | 65.9 | 95.7 | 73.3 | 77.0 |
| Gemini-1.5-Pro | 79.6 | 64.7 | 92.6 | 72.6 | 74.7 |
| VILA1.5-40B | 82.5 | 65.3 | 93.2 | 67.4 | 74.7 |
| GPT-4o-Mini | 80.9 | 58.8 | 93.8 | 74.8 | 74.0 |
| Qwen2-VL-2B | 77.9 | 55.8 | 93.1 | 72.5 | 71.5 |
| CogVLM2-19B | 78.1 | 55.6 | 92.3 | 72.6 | 71.4 |
| Phi-3-Vision | 74.1 | 56.4 | 90.6 | 73.8 | 70.3 |
| Cambrian-13B | 79.3 | 54.6 | 92.3 | 66.6 | 70.0 |
| Cambrian-8B | 77.9 | 56.4 | 91.0 | 65.4 | 69.6 |
| Molmo-7B-D | 73.2 | 55.5 | 91.7 | 72.1 | 69.5 |
| Idefics2-8B | 77.8 | 55.8 | 92.7 | 61.8 | 68.7 |
| Molmo-7B-O | 72.6 | 54.3 | 88.5 | 68.9 | 67.8 |
| Phi-3.5-Vision | 71.4 | 55.3 | 87.2 | 68.6 | 67.4 |
| VILA1.5-13B | 74.6 | 54.1 | 85.3 | 50.2 | 63.4 |
| DeepSeek-VL-7B | 73.2 | 52.6 | 85.8 | 52.9 | 63.2 |
| Molmo-1B | 69.4 | 50.1 | 87.4 | 60.2 | 63.1 |
| CogVLM-17B | 72.3 | 48.8 | 77.8 | 54.6 | 61.3 |
| VILA1.5-8B | 72.4 | 51.8 | 81.8 | 46.5 | 60.7 |
| Gemini-1.5-Flash | 59.7 | 53.8 | 79.9 | 56.3 | 59.1 |
| PaliGemma-3B | 71.7 | 51.3 | 53.1 | 53.0 | 59.0 |
| VILA1.5-3B | 70.3 | 48.0 | 78.9 | 42.3 | 57.5 |
| DeepSeek-VL-1.3B | 68.9 | 43.6 | 79.5 | 43.8 | 56.1 |
| LLaVA1.5-13B | 66.4 | 46.2 | 75.8 | 37.0 | 53.9 |
| LLaVA1.5-7B | 63.6 | 44.7 | 74.0 | 35.0 | 51.8 |
| Chameleon-30B | 53.1 | 41.2 | 48.0 | 33.9 | 44.2 |
| InstructBLIP-7B | 55.1 | 35.2 | 47.7 | 29.9 | 42.1 |
| InstructBLIP-13B | 54.8 | 34.7 | 48.7 | 26.5 | 41.1 |
| Chameleon-7B | 41.0 | 34.7 | 42.3 | 29.6 | 36.4 |{{< /table-caption >}}
> 🔼 본 표는 개방형 질문에 대한 규칙 기반 평가 방식의 한계를 보여주는 예시입니다. 규칙 기반 방식은 의미적 유사성을 고려하지 않고 형식적 오류에 대해 불이익을 주기 때문에, 평가 결과가 매우 부정확하다는 것을 보여줍니다. 표에는 이미지와 질문, 정답, 모델의 예측값, 그리고 기존 VQA 점수와 모델 점수가 포함되어 있습니다.  각 예시는 규칙 기반 평가 방식이 의미적 차이를 제대로 포착하지 못하고 형식에만 집중하여 부정확한 평가 결과를 초래함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Examples of rule-based evaluation failures of open-ended questions. Rule-based methods fail to account for semantic similarity and penalize formatting errors, resulting in highly inaccurate evaluation results.
> </details>

{{< table-caption >}}
| Image | Question | Answer | Prediction | VQAScore | ModelScore |
|---|---|---|---|---|---| 
| <img src="https://arxiv.org/html/2501.03225/rule1.png" width=63 height=63> | Where is the man’s left hand holding? | chin | On his chin. | 0 | 1 |
| <img src="https://arxiv.org/html/2501.03225/rule2.png" width=63 height=63> | How many sinks are there? | 2 | Two sinks. | 0 | 1 |
| <img src="https://arxiv.org/html/2501.03225/rule3.png" width=63 height=63> | What is the light source? | street lights | Streetlights | 0 | 1 |
| <img src="https://arxiv.org/html/2501.03225/rule4.png" width=63 height=63> | What is the horse jumping over? | log | Log fence | 0 | 1 |
| <img src="https://arxiv.org/html/2501.03225/rule5.png" width=63 height=63> | Where is the train going? | svanemollen | Svanemøllen | 0 | 1 |
| <img src="https://arxiv.org/html/2501.03225/rule6.png" width=63 height=63> | What colors are on this train? | blue and yellow and silver | Blue, yellow, and silver. | 0 | 1 |{{< /table-caption >}}
> 🔼 본 표는 오픈엔드형 질문에 대한 모델 기반 평가의 어려움을 보여줍니다.  GPT-4 0806 모델은 유사한 예측과 답변에 대해 완벽한 점수(1.0)를 부여하는 경향이 있는 반면, GPT-4 0513 모델은 0.9점을 부여하는 경향이 있습니다. 이러한 차이는 평가 결과에 상당한 영향을 미치며, 연구의 재현성에 대한 우려를 제기합니다.  표에는 모델의 버전에 따른 불일치 사례 여섯 가지가 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Examples of model-based evaluation failures of open-ended questions. GPT-4o-0806 often assigns a perfect score of for similar predictions and answers, whereas GPT-4o-0513 tends to assign a score of 0.9. This behavior variation introduces significant differences in evaluation results and raises concerns about reproducibility in future research.
> </details>

{{< table-caption >}}
| Image | Question | Answer | Prediction | GPT-4o-0513 Score | GPT-4o-0806 Score |
|---|---|---|---|---|---| 
| ![model1](https://arxiv.org/html/2501.03225/images/model1.png) | Does the giraffe appear dangerous? | no | The giraffe in the image does not appear to be dangerous. It seems to be calm and at ease with the person’s presence, indicating a level of trust and familiarity between them. | 0.9 | 1.0 |
| ![model2](https://arxiv.org/html/2501.03225/images/model2.png) | Is the man happy? | yes | The man in the image appears to be happy. His facial expression, characterized by a broad smile and eyes that seem to be crinkling at the corners, typically indicates joy or amusement… | 0.9 | 1.0 |
| ![model3](https://arxiv.org/html/2501.03225/images/model3.png) | Is that wine in the background? | no | No, there is no wine in the background. The image shows a pizza and a can of Coca-Cola on a desk, with a laptop and some other items in the background. | 0.9 | 1.0 |
| ![model4](https://arxiv.org/html/2501.03225/images/model4.png) | What are all the scene text in the image? | S3302CD | The scene text in the image reads ’S 3302 CD’. | 0.9 | 1.0 |
| ![model5](https://arxiv.org/html/2501.03225/images/model5.png) | What is this banknote? | ten pound or 10 pound or British pound | This is a ten-pound banknote from the United Kingdom, featuring the portrait of Queen Elizabeth II. | 0.9 | 1.0 |
| ![model6](https://arxiv.org/html/2501.03225/images/model6.png) | How many birds are there? | 6 | There are six birds perched on the branch, each displaying a unique coloration and size, which suggests they may belong to different species. | 0.9 | 1.0 |{{< /table-caption >}}
> 🔼 본 표는 VMCBench 테스트 세트의 20개 하위 집합에 대해 33개의 최첨단 비전 언어 모델의 성능을 보여줍니다. 각 하위 집합은 특정한 비전 언어 작업(예: 일반 추론, OCR, 문서 및 차트 이해)에 초점을 맞추고 있으며, 각 모델의 성능은 해당 하위 집합에 대한 정확도로 측정됩니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Performance of 33 vision language models on 20 subsets of VMCBench test set.
> </details>

{{< table-caption >}}
Model|SEEDBench|MMStar|A-OKVQA|VizWiz|MMVet|VQAv2|OKVQA|MMMU|MathVista|ScienceQA|
---|---|---|---|---|---|---|---|---|---|---|
Qwen2-VL-72B|84.2|71.5|93.4|94.9|88.5|92.4|94.8|70.2|70.3|87.1|
GPT-4o|84.2|62.2|92.0|94.4|80.6|88.7|94.1|70.0|51.0|86.9|
Molmo-72B|82.0|62.5|88.5|88.5|79.1|85.6|94.1|59.4|60.9|89.4|
Qwen2-VL-7B|82.7|60.3|90.1|92.4|82.0|91.4|92.6|54.1|48.0|86.9|
Claude-3.5-Sonnet|78.3|53.7|86.4|87.2|87.8|84.7|91.1|59.6|56.9|79.9|
Cambrian-34B|83.5|59.4|91.1|90.7|81.3|88.4|91.9|55.0|60.9|83.5|
Gemini-1.5-Pro|77.3|52.0|88.0|89.0|79.9|80.8|90.4|59.6|56.9|83.0|
VILA1.5-40B|81.2|58.0|90.8|90.2|77.0|87.3|93.3|58.2|65.3|83.3|
GPT-4o-Mini|79.3|47.7|86.1|92.2|80.6|88.2|92.1|56.5|43.1|78.7|
Qwen2-VL-2B|77.8|44.7|86.6|88.2|70.5|88.7|88.6|46.2|39.1|76.0|
CogVLM2-19B|77.3|48.2|87.8|87.3|73.4|85.2|87.4|39.7|35.6|90.5|
Phi-3-Vision|78.3|46.8|81.6|79.9|67.6|79.2|85.2|44.7|38.6|92.1|
Cambrian-13B|79.3|48.5|86.4|87.3|76.3|87.0|90.6|41.3|39.6|77.4|
Cambrian-8B|78.3|53.0|84.5|88.0|68.3|85.6|87.9|43.3|45.5|77.4|
Molmo-7B-D|74.1|46.8|82.4|81.9|63.3|80.3|83.5|43.0|37.6|91.9|
Idefics2-8B|77.8|49.4|85.4|84.8|69.8|86.8|90.4|38.5|41.6|91.9|
Molmo-7B-O|75.1|45.8|80.5|78.9|66.2|78.2|83.2|44.0|35.6|90.0|
Phi-3.5-Vision|74.8|45.8|76.5|75.7|64.0|79.4|83.5|45.2|39.1|87.3|
VILA1.5-13B|77.5|44.9|81.9|83.3|63.3|82.4|88.6|42.8|48.5|72.6|
DeepSeek-VL-7B|75.6|39.9|80.5|82.1|63.3|83.6|87.7|41.1|33.2|86.7|
Molmo-1B|70.9|43.0|77.9|80.9|54.7|75.7|83.0|36.3|27.7|89.1|
CogVLM-17B|70.9|42.8|80.7|85.0|59.7|80.1|86.7|37.5|36.1|66.7|
VILA1.5-8B|74.3|40.9|77.9|79.4|64.7|80.8|88.6|38.0|49.0|71.5|
Gemini-1.5-Flash|56.3|38.0|67.0|68.5|53.2|64.1|70.6|48.1|57.9|66.3|
PaliGemma-3B|74.6|39.9|87.3|77.0|50.4|87.7|85.2|29.1|30.7|94.3|
VILA1.5-3B|74.3|38.5|76.9|80.9|57.6|78.5|85.4|34.4|39.6|64.9|
DeepSeek-VL-1.3B|70.9|37.5|74.4|82.1|52.5|80.3|84.7|31.0|22.3|63.8|
LLaVA1.5-13B|66.2|37.3|76.5|76.0|59.7|64.1|85.2|37.5|31.7|66.3|
LLaVA1.5-7B|62.2|34.2|72.5|73.8|54.0|66.7|82.2|35.6|31.2|68.6|
Chameleon-30B|53.6|33.0|57.2|52.2|48.9|58.3|68.6|34.4|32.7|57.9|
InstructBLIP-7B|52.8|34.7|61.9|65.4|39.6|59.7|71.9|31.0|22.8|46.8|
InstructBLIP-13B|48.4|29.0|63.3|64.2|43.2|64.1|71.6|25.7|19.8|50.0|
Chameleon-7B|44.9|31.6|46.4|40.4|29.5|41.4|53.1|32.7|22.3|53.6|{{< /table-caption >}}
> 🔼 이 표는 논문의 VMCBench 벤치마크 데이터셋의 일부 예시를 보여줍니다. VMCBench는 다양한 기존 VQA 데이터셋을 여러 선택지가 있는 질문 형식으로 통합한 것입니다. 각 행은 특정 데이터셋의 출처, 관련 이미지, 질문, 그리고 네 가지 선택지를 보여줍니다. 정답은 주황색으로 강조 표시되어 있습니다. 이 표는 VMCBench의 다양한 질문 유형과 데이터셋의 범위를 보여주는 데 초점을 맞추고 있습니다. 총 7개의 표로 나눠져 있으며, 이 표는 그 중 첫 번째 표입니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Examples of VMCBench (1/7). Each example has a dataset source, image, question, and four choices (correct choice highlighted in orange).
> </details>

{{< table-caption >}}
| Source | Image | Question | Choices |
|---|---|---|---| 
| A-OKVQA | https://arxiv.org/html/2501.03225/images/8255.png | What season of the year is shown here? | A. late summer with green leaves <br> B. early spring with blooming flowers <br> C. fall <br> D. early winter with snow | 
| A-OKVQA | https://arxiv.org/html/2501.03225/images/7998.png | What occasion are the bears probably sitting at the table enjoying? | A. Thanksgiving <br> B. Easter <br> C. New Year’s Eve <br> D. Christmas | 
| A-OKVQA | https://arxiv.org/html/2501.03225/images/8430.png | What kind of beverage is the red sign advertising? | A. Dr Pepper <br> B. Coca Cola <br> C. Red Bull <br> D. Pepsi | 
| AI2D | https://arxiv.org/html/2501.03225/images/1667.png | Which shows the first stage? | A. b <br> B. a <br> C. d <br> D. c | 
| AI2D | https://arxiv.org/html/2501.03225/images/1293.png | What part of plants the diagram depicts? | A. Leaf <br> B. Stem <br> C. Root <br> D. Flower petal | 
| AI2D | https://arxiv.org/html/2501.03225/images/1275.png | Which is the exterior portion of the earth? | A. A <br> B. D <br> C. C <br> D. B | 
| ChartQA | https://arxiv.org/html/2501.03225/images/7120.jpg | What percentage of respondents own lots of vinyl records? | A. 35 <br> B. 24 <br> C. 30 <br> D. 28 | 
| ChartQA | https://arxiv.org/html/2501.03225/images/7076.jpg | In which year is the ACSI score is lowest? | A. 2015 <br> B. 2017 <br> C. 2018 <br> D. 2010 | 
| ChartQA | https://arxiv.org/html/2501.03225/images/7073.jpg | What is the total ratio of 2014 through 2017? | A. 5.36 <br> B. 5.11 <br> C. 4.57 <br> D. 5.25 |{{< /table-caption >}}
> 🔼 표 6은 VMCBench의 일부 예시 (전체 7개 중 2번째)를 보여줍니다. 각 예시는 데이터셋 출처, 이미지, 질문, 그리고 네 가지 선택지 (정답은 주황색으로 강조 표시)로 구성됩니다. 이 표는 VMCBench 데이터셋의 다양한 유형과 복잡성을 보여주는 대표적인 예시들을 제시하여 독자의 이해를 돕고자 합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Examples of VMCBench (2/7). Each example has a dataset source, image, question, and four choices (correct choice highlighted in orange).
> </details>

{{< table-caption >}}
| Source | Image | Question | Choices |
|---|---|---|---| 
| DocVQA | https://arxiv.org/html/2501.03225/extracted/6113068/images/5929.png | What is the table number? | A. 7<br>B. 8<br>C. 10<br>D. 9 | 
| DocVQA | https://arxiv.org/html/2501.03225/extracted/6113068/images/5663.png | In the plot, what is the value of ”r”? | A. 0.994<br>B. 0.949<br>C. 1.004<br>D. 0.980 | 
| DocVQA | https://arxiv.org/html/2501.03225/extracted/6113068/images/5758.jpg | Which category item’s advertisement is this? | A. health supplements <br>B. foods<br>C. home appliances <br>D. clothing | 
| GQA | https://arxiv.org/html/2501.03225/extracted/6113068/images/7896.jpg | What food is to the left of the table? | A. can of soup <br>B. bag of flour <br>C. cereal box <br>D. dog food | 
| GQA | https://arxiv.org/html/2501.03225/extracted/6113068/images/7537.jpg | Who is looking at the cell phone? | A. man<br>B. tourist <br>C. child <br>D. nobody | 
| GQA | https://arxiv.org/html/2501.03225/extracted/6113068/images/7776.jpg | What does the woman hold? | A. cell phone<br>B. digital camera <br>C. remote control <br>D. compact mirror | 
| InfoVQA | https://arxiv.org/html/2501.03225/extracted/6113068/images/5343.jpg | Which states/UT has been included under “Certain” risk of community transmission? | A. manipur, tamil nadu <br>B. maharashtra, gujarat <br>C. rajasthan, karnataka <br>D. telangana, delhi | 
| InfoVQA | https://arxiv.org/html/2501.03225/extracted/6113068/images/4993.jpg | What percentage of Canadian still go to brick and mortar stores to buy items? | A. 30% <br>B. 70%<br>C. 80% <br>D. 60% | 
| InfoVQA | https://arxiv.org/html/2501.03225/extracted/6113068/images/5165.jpg | How many women out of every 4 women are domestic violence survivors? | A. 4 <br>B. 3<br>C. 1.5 <br>D. 2 |{{< /table-caption >}}
> 🔼 표 7은 VMCBench의 일부 질문들을 보여주는 예시입니다. VMCBench는 20개의 기존 VQA 데이터셋을 통합하여 만든 벤치마크이며, 각 예시는 데이터셋 출처, 이미지, 질문과 네 가지 선택지(정답은 주황색으로 표시)로 구성됩니다. 이 표는 VMCBench의 다양한 질문 유형과 난이도를 보여주는 대표적인 예시들을 제시하며, 전체 벤치마크의 규모와 다양성을 간략히 소개하는 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Examples of VMCBench (3/7). Each example has a dataset source, image, question, and four choices (correct choice highlighted in orange).
> </details>

{{< table-caption >}}
| Source | Image | Question | Choices |
|---|---|---|---| 
| MMMU | https://arxiv.org/html/2501.03225/images/343.png | The average wave velocity value of the bored pile body at a certain site is 3555.6m/s, and the low strain reflected wave dynamic test curve of a certain column is shown in Figure 10-3, corresponding to the values of time t1, t2, and t3 in the figure, which of the following options is the closest value to the length of the pile? | A. 22.0m <br> B. 24.0m <br> C. 26.0m <br> D. 23.0m |
| MMMU | https://arxiv.org/html/2501.03225/images/284.png | How many molecules of the sweetener saccharin can be prepared from 30 $C$ atoms, 25 $H$ atoms, 12 $O$ atoms, 8 $S$ atoms, and 14 $N$ atoms? | A. 6 <br> B. 4 <br> C. 2 <br> D. 5 |
| MMMU | https://arxiv.org/html/2501.03225/images/333.png | The accompanying sketch shows the schematic arrangement for measuring the thermal conductivity by the guarded hot plate method. Two similar 1 cm thick specimens receive heat from a 6.5 cm by 6.5 cm guard heater. When the power dissipation by the wattmeter was 15 W, the thermocouples inserted at the hot and cold surfaces indicated temperatures as 325 K and 300 K. What is the thermal conductivity of the test specimen material? | A. 0.86 W/m K <br> B. 0.5 W/m K <br> C. 0.68 W/m K <br> D. 0.71 W/m K |
| MMStar | https://arxiv.org/html/2501.03225/images/1194.jpg | What color is the ribbon that the man on the right is holding? | A. Red <br> B. Blue <br> C. Yellow <br> D. Green |
| MMStar | https://arxiv.org/html/2501.03225/images/1202.jpg | What is the main feature of the building in the image? | A. The colorful facade <br> B. The large stained glass windows <br> C. The marble columns <br> D. The stone wall |
| MMStar | https://arxiv.org/html/2501.03225/images/916.jpg | who is this person? | A. Awkwafina <br> B. Sandra Oh <br> C. Ali Wong <br> D. Lucy Liu |
| MMVet | https://arxiv.org/html/2501.03225/images/2784.jpg | What is the original price for pork belly before discount? | A. 10 <br> B. 12 <br> C. 14 <br> D. 15 |
| MMVet | https://arxiv.org/html/2501.03225/images/2773.jpg | What is the answer to the second equation on the right? | A. 11 <br> B. 5 <br> C. 7 <br> D. 9 |
| MMVet | https://arxiv.org/html/2501.03225/images/2902.jpg | What occasions would someone use this meme? | A. Sharing relatable humor about feeling sleepy or having conflicting desires, especially during the day. <br> B. Expressing excitement about a new bedtime routine <br> C. Celebrating an all-nighter successfully pulled off <br> D. Promoting productivity in the workplace |{{< /table-caption >}}
> 🔼 표 8은 VMCBench 데이터셋의 일부(4/7)를 보여줍니다. 각 행은 데이터셋 출처, 이미지, 질문, 그리고 정답이 주황색으로 표시된 네 가지 선택지로 구성됩니다. 이 표는 VMCBench의 다양한 질문 유형과 난이도를 보여주는 대표적인 예시들을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Examples of VMCBench (4/7). Each example has a dataset source, image, question, and four choices (correct choice highlighted in orange).
> </details>

{{< table-caption >}}
| Source | Image | Question | Choices |
|---|---|---|---| 
| MathVision | https://arxiv.org/html/2501.03225/images/3460.png | In the grid, how many grey squares have to be coloured white, so that in each row and each column there is exactly one grey square? | A. 5 <br> B. 8 <br> C. 6 <br> D. 7 | 
| MathVision | https://arxiv.org/html/2501.03225/images/3221.png | Tom, John and Lily each shot six arrows at a target. Arrows hitting anywhere within the same ring scored the same number of points. Tom scored 46 points and John scored 34 points, as shown. How many points did Lily score? | A. 42 <br> B. 40 <br> C. 44 <br> D. 38 | 
| MathVision | https://arxiv.org/html/2501.03225/images/3270.png | A point  𝑃  is chosen in the interior of  △ABC  so that when lines are drawn through  𝑃  parallel to the sides of  △ABC , the resulting smaller triangles,  𝑡₁, 𝑡₂, and  𝑡₃  in the figure, have areas 4, 9, and 49, respectively. Find the area of  △ABC . | A. 81 <br> B. 128 <br> C. 144 <br> D. 72 | 
| MathVista | https://arxiv.org/html/2501.03225/images/755.jpg | In the figure, ∠9=75. Find the measure of ∠6. | A. 120 <br> B. 135 <br> C. 150 <br> D. 105 | 
| MathVista | https://arxiv.org/html/2501.03225/images/766.jpg | (Original in Chinese) As shown in the figure, in △ABC, AD is the angle bisector, and AE is the altitude. If ∠B=40° and ∠C=70°, then the measure of ∠EAD is (). | A. 25° <br> B. 20° <br> C. 30° <br> D. 15° | 
| MathVista | https://arxiv.org/html/2501.03225/images/583.jpg | What is the green curve? | A. a cubic function <br> B. a trigonometric function <br> C. an exponential function <br> D. a logarithmic function | 
| OCRVQA | https://arxiv.org/html/2501.03225/images/6164.jpg | Who wrote this book? | A. John D. Smith <br> B. Ruth E. McCall BS MT(ASCP) <br> C. Michael A. Johnson <br> D. Emily J. Brown | 
| OCRVQA | https://arxiv.org/html/2501.03225/images/6102.jpg | What is the title of this book? | A. Climate Change and Urban Adaptation Strategies <br> B. Building a Sustainable Future: Climate Change Adaptation <br> C. Adapting Urban Spaces: Sustainability in the 21st Century <br> D. Adapting Buildings and Cities for Climate Change | 
| OCRVQA | https://arxiv.org/html/2501.03225/images/6145.jpg | What is the title of this book? | A. Cracking the PSAT/NMSQT, 2013 Edition (College Test Preparation) <br> B. Cracking the SAT, 2013 Edition (College Test Preparation) <br> C. Crushing the PSAT/NMSQT, 2013 Edition <br> D. Cracking the PSAT, 2014 Edition (College Test Preparation) |{{< /table-caption >}}
> 🔼 표 9는 VMCBench 데이터셋의 일부(5/7)를 보여줍니다. 각 행은 데이터셋 출처, 이미지, 질문, 그리고 네 가지 보기(정답은 주황색으로 표시)로 구성됩니다. 이 표는 VMCBench의 다양한 유형의 질문과 이미지들을 보여주는 예시들을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Examples of VMCBench (5/7). Each example has a dataset source, image, question, and four choices (correct choice highlighted in orange).
> </details>

{{< table-caption >}}
| Source | Image | Question | Choices |
|---|---|---|---| 
| OKVQA | https://arxiv.org/html/2501.03225/images/8935.png | What food is being sold? | A. hamburger <br> B. sandwich <br> C. hot dog <br> D. kebab | 
| OKVQA | https://arxiv.org/html/2501.03225/images/8827.png | What is the proper response when traveling in a vehicle and seeing a red traffic light? | A. proceed with caution <br> B. speed up to clear the intersection <br> C. stop <br> D. yield only if necessary | 
| OKVQA | https://arxiv.org/html/2501.03225/images/8885.png | How long does this animal usually live? | A. 25 years <br> B. 10 years <br> C. 20 years <br> D. 8 years | 
| RealWorldQA | https://arxiv.org/html/2501.03225/images/4406.jpg | How many oncoming vehicles are there? | A. 4 <br> B. 3 <br> C. 1 <br> D. 2 | 
| RealWorldQA | https://arxiv.org/html/2501.03225/images/4389.jpg | Which way does this door open? | A. The door opens outward, swinging to the right. <br> B. The door is a sliding door, moving to the right. <br> C. The door opens inward, swinging to the right. <br> D. The door opens outward, swinging to the left. | 
| RealWorldQA | https://arxiv.org/html/2501.03225/images/4311.jpg | Which object is bigger than the other? | A. Both objects are the same size. <br> B. The right object is bigger. <br> C. The left object has more volume. <br> D. The left object is bigger. | 
| SEEDBench | https://arxiv.org/html/2501.03225/images/2720.jpg | What can be found in the image? | A. A group of people sitting down and a young boy with a basketball player. <br> B. A basketball player signing autographs for a line of fans. <br> C. A group of musicians playing instruments <br> D. Several students in a classroom setting | 
| SEEDBench | https://arxiv.org/html/2501.03225/images/2551.jpg | Which object is emitting smoke in the image? | A. Factory smokestack in the background <br> B. House chimney <br> C. Chimney of a nearby house <br> D. Train | 
| SEEDBench | https://arxiv.org/html/2501.03225/images/2614.jpg | What is the boy doing in the image? | A. Jumping <br> B. Smiling <br> C. Reading a book <br> D. Waving |{{< /table-caption >}}
> 🔼 표 10은 VMCBench 데이터셋의 일부를 보여주는 예시입니다. VMCBench는 다양한 기존 VQA 데이터셋들을 하나의 다중 선택 질문 형식으로 통합한 벤치마크입니다. 이 표에는 각 예시에 대해 데이터셋 출처, 이미지, 질문, 그리고 네 가지 선택지 (정답은 주황색으로 표시)가 포함되어 있습니다. 이는 모델의 다양한 비전 언어 이해 능력을 평가하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Examples of VMCBench (6/7). Each example has a dataset source, image, question, and four choices (correct choice highlighted in orange).
> </details>

{{< table-caption >}}
| Source | Image | Question | Choices |
|---|---|---|---| 
| ScienceQA | https://arxiv.org/html/2501.03225/images/2139.png | What is the name of the colony shown? | A. Rhode Island<br>B. Connecticut<br>C. New Hampshire<br>D. Massachusetts | 
| ScienceQA | https://arxiv.org/html/2501.03225/images/2001.png | Which continent is highlighted? | A. Australia<br>B. Arctic<br>C. South America<br>D. Antarctica | 
| ScienceQA | https://arxiv.org/html/2501.03225/images/1815.png | What can Turner and Mona trade to each get what they want? | A. Turner can trade his tomatoes for Mona’s broccoli.<br>B. Turner can trade his oranges for Mona’s water. <br>C. Turner can trade his water for Mona’s almonds. <br>D. Turner can trade his sandwich for Mona’s hot dog. | 
| TableVQA-Bench | https://arxiv.org/html/2501.03225/images/3799.png | What is the total amount of Purchase Obligations due after 2021? | A. $6.5<br>B. $80.7<br>C. $0.0<br>D. $214.9 | 
| TableVQA-Bench | https://arxiv.org/html/2501.03225/images/3764.png | what other name did asian cougar have? | A. Gamma<br>B. Kooga<br>C. Kuuga<br>D. Black Buffalo | 
| TableVQA-Bench | https://arxiv.org/html/2501.03225/images/3504.png | how many metals did netherlands and the us win together? | A. 18<br>B. 20<br>C. 22<br>D. 19 | 
| TextVQA | https://arxiv.org/html/2501.03225/images/4635.jpg | what number is shown? | A. 21<br>B. 25<br>C. 22<br>D. 20 | 
| TextVQA | https://arxiv.org/html/2501.03225/images/4515.jpg | what male name is written on the white book? | A. mike<br>B. sean<br>C. dave<br>D. steve | 
| TextVQA | https://arxiv.org/html/2501.03225/images/4865.jpg | which company is giving the presentation? | A. ibm<br>B. sap<br>C. google<br>D. oracle |{{< /table-caption >}}
> 🔼 표 11은 VMCBench 데이터셋의 일부 예시를 보여줍니다.  총 20개의 기존 VQA 데이터셋을 하나로 통합한 VMCBench는 다양한 유형의 시각적 질문과 답변을 포함합니다. 각 행은 하나의 데이터셋 소스, 이미지, 질문, 그리고 정답이 주황색으로 강조된 네 가지 선택지를 보여줍니다. 이 표는 VMCBench의 다양성과 난이도를 보여주는 예시를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 11: Examples of VMCBench (7/7). Each example has a dataset source, image, question, and four choices (correct choice highlighted in orange).
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