---
title: "LIMO: Less is More for Reasoning"
summary: "소량의 데이터로 복잡한 수학적 추론 능력을 효과적으로 유도할 수 있다는 놀라운 발견!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Generative Al Research",]
showSummary: true
date: 2025-02-05
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.03387 {{< /keyword >}}
{{< keyword icon="writer" >}} Yixin Ye et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-06 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.03387" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.03387" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

기존 연구는 대규모 언어 모델(LLM)의 복잡한 추론 능력 향상을 위해 방대한 양의 훈련 데이터(10만 개 이상의 예제)가 필요하다고 주장해왔습니다. 하지만, 이러한 통념과 달리 본 논문에서는 **소량의 훈련 데이터만으로도 LLM의 복잡한 수학적 추론 능력을 효과적으로 이끌어낼 수 있다는 것을 실험적으로 증명**합니다. 기존의 지도 학습 방식은 주로 암기 효과에만 집중하는 반면, 본 연구는 소량의 정교하게 구성된 훈련 데이터를 사용하여 일반화 성능을 크게 향상시킬 수 있음을 보여줍니다.

본 연구는 제한된 훈련 데이터(817개의 예제)를 사용하여 개발된 LIMO 모델을 제시합니다. LIMO 모델은 기존의 최첨단 모델들을 능가하는 성능을 보여주며, 특히 **다양한 벤치마크에서 뛰어난 분포 외 일반화 성능**을 나타냅니다. 이러한 결과를 바탕으로, 본 논문에서는 **Less-Is-More 추론 가설(LIMO 가설)**을 제안하며, 이는 기초 모델에 포괄적으로 인코딩된 도메인 지식과 정교하게 구성된 인지 과정의 시연이 복잡한 추론 능력을 이끌어내는 데 중요한 역할을 한다는 것을 시사합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 소량의 데이터(817개의 예제)만으로도 복잡한 수학적 추론 과제에서 최첨단 성능을 달성 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 기존의 대규모 데이터 기반의 방식에 대한 도전: 최소한의 예제만으로도 우수한 일반화 성능을 보임 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} Less-Is-More 추론 가설 제시: 사전 학습된 기초 모델에서의 포괄적인 지식과 효과적인 후속 학습 예제의 중요성 강조 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **소량의 데이터만으로도 복잡한 추론 능력을 효과적으로 이끌어낼 수 있다는 것을 보여줌**으로써, 대규모 언어 모델(LLM)의 추론 능력 향상에 대한 기존의 통념에 도전합니다. 이는 **데이터 효율적인 AI 개발**에 대한 새로운 패러다임을 제시하며, 연구자들에게 **새로운 연구 방향**을 제시하고 **기존 연구의 한계를 극복**하는 데 중요한 의미를 가집니다. 또한, 제시된 LIMO 가설은 다른 분야의 복잡한 추론 문제에도 적용될 수 있는 잠재력을 가지고 있어, **향후 AI 연구의 폭넓은 발전**에 기여할 것으로 기대됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.03387/x1.png)

> 🔼 그림 1은 LIMO 모델이 NuminaMath 모델보다 훨씬 적은 훈련 데이터(샘플)만을 사용하면서도 다양한 수학 및 다학문적 벤치마크에서 뛰어난 성능을 달성했음을 보여줍니다.  LIMO는 제한된 훈련 데이터에도 불구하고,  다양한 종류의 복잡한 수학 문제 해결 능력을 효과적으로 보여주어 기존의 대규모 데이터 기반 학습에 대한 기존 통념에 도전합니다.  NuminaMath와 비교하여, LIMO는 훨씬 더 적은 훈련 샘플을 사용하여 상당한 성능 향상을 이루어냈다는 점을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  LIMO achieves substantial improvement over NuminaMath with fewer samples while excelling across diverse mathematical and multi-discipline benchmarks.
> </details>





{{< table-caption >}}
| Aspect | General Alignment (LIMA) | Complex Reasoning (LIMO) |
|---|---|---|
| **Core Capability** | Response format and style adaptation for general-purpose interaction | Multi-step logical inference and complex cognitive reasoning |
| **Knowledge Foundation** | * General text corpus sufficient<br>* Social interaction patterns<br>* Basic world knowledge | * Diverse reasoning paradigms and problem-solving approaches<br>* Rich context for exploring alternative solutions<br>* Deep conceptual connections across domains |
| **Computation Requirements** | * Fixed-length generation sufficient<br>* Single-pass processing adequate<br>* Limited context window acceptable | * Scalable inference-time computation essential<br>* Extended reasoning chain support required<br>* Large cognitive workspace necessary |
| **Historical Prerequisites** | Emerged in 2023, requiring only:<br>* Base models with general knowledge<br>* Basic prompt engineering techniques | Emerged in 2025, requiring convergence of:<br>* Advanced reasoning architectures<br>* Inference-time scaling revolution |
| **Training Data Quality** | * **Question Design:**<br>– Common interaction scenarios<br>– Standard task diversity<br>– Basic instruction following<br>* **Solution Quality:**<br>– Clear communication style<br>– Format consistency<br>– Appropriate tone | * **Question Design:**<br>– High-difficulty problems fostering complex reasoning<br>– Problems deviating from training distribution<br>– Cross-domain knowledge integration challenges<br>* **Solution Quality:**<br>– Optimal structure with adaptive step granularity<br>– Strategic cognitive scaffolding for reasoning<br>– Rigorous verification throughout solution |{{< /table-caption >}}

> 🔼 본 표는 대규모 언어 모델에서의 'Less-is-More' 현상을 비교 분석한 표입니다.  'Less-is-More' 현상이란, 복잡한 추론 능력을 향상시키기 위해 방대한 양의 데이터가 필요하다는 기존의 통념과 달리, 적은 양의 데이터만으로도 효과적으로 추론 능력을 이끌어낼 수 있다는 현상을 말합니다.  표는 일반적인 정렬(Alignment) 작업과 복잡한 추론(Reasoning) 작업에서의 'Less-is-More' 현상을 비교하여, 각 작업의 핵심 기능, 지식 기반, 계산 요구사항, 사전 조건, 학습 데이터의 질적 차이 등을 보여줍니다.  두 작업 간의 차이점을 명확히 하여 'Less-is-More' 현상이 어떻게 나타나는지에 대한 이해를 돕습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparative Analysis: Less-is-More Phenomena in Language Models
> </details>





### In-depth insights


#### LIMO Hypothesis
LIMO 가설은 대규모 언어 모델(LLM)에서 복잡한 추론 능력이 어떻게 나타나는지에 대한 기존의 이해에 도전하는 핵심 개념입니다. 기존의 통념과 달리 **방대한 훈련 데이터(10만 개 이상의 예시)**가 필요하지 않다는 것을 보여줍니다.  **소량의 정교하게 구성된 훈련 데이터(예시)**를 통해서도 복잡한 수학적 추론 능력을 효과적으로 이끌어낼 수 있다는 것입니다. 이는 **지도 학습 미세 조정이 주로 일반화보다는 암기**를 유발한다는 일반적인 믿음에도 도전합니다. LIMO 가설은 **사전 훈련 과정에서 모델에 포괄적으로 인코딩된 도메인 지식**과 **추론 과정을 보여주는 최소한의 정확하게 구성된 시범**이라는 두 가지 요소에 의해 복잡한 추론의 유도 임계값이 결정된다고 주장합니다.  **모델의 사전 훈련된 지식 기반의 완성도와 사후 훈련 예시의 효과**가 중요한 역할을 한다는 것입니다.  본 가설은 복잡한 추론이 과제의 복잡성보다는 이 두 요소에 의해 근본적으로 결정된다는 점을 시사합니다.

#### Data-Efficient Reasoning
본 논문은 **데이터 효율적인 추론(Data-Efficient Reasoning)**에 대한 심도있는 연구 결과를 제시합니다. 기존의 대규모 언어 모델(LLM) 훈련 방식은 방대한 데이터를 필요로 하지만, 본 연구는 소량의 고품질 데이터만으로도 복잡한 추론 능력을 효과적으로 향상시킬 수 있음을 보여줍니다. **핵심은 모델의 사전 학습 과정에서 이미 축적된 지식을 효과적으로 활용하는 데 있습니다.**  이는 적절히 구성된 소량의 데이터가 모델의 기존 지식을 활성화시키는 '인지적 템플릿' 역할을 한다는 **'Less-is-More 추론 가설'**을 통해 설명됩니다. 이 가설은  **방대한 데이터가 아닌, 질 높은 예시의 전략적 활용**이 효과적임을 시사하며,  향후 데이터 효율적인 AI 개발에 중요한 시사점을 제공합니다.  **추론 과정의 투명성 확보를 위한 고품질 해답 구성** 또한 중요하며,  모델의 추론 능력 향상과 일반화 성능 개선에 크게 기여합니다.

#### Reasoning Elicitation
본 논문은 **소량의 데이터만으로도 복잡한 추론 능력을 이끌어낼 수 있다**는 놀라운 발견을 제시합니다. 기존의 상식과는 달리, 방대한 데이터가 필요하지 않다는 점을 강조하며, **사전 학습된 모델의 지식 기반과 추론 과정을 효과적으로 보여주는 몇몇 예시만으로도 복잡한 추론 능력이 나타날 수 있다**고 주장합니다. 이는 **'Less-is-More Reasoning Hypothesis'**로 명명되며, **모델의 사전 지식과 추론 과정의 효율적인 제시가 추론 능력 향상의 핵심**임을 시사합니다.  **추론 능력을 효과적으로 이끌어내기 위한 핵심 요소는 양질의 데이터와 적절한 추론 과정의 시각화**이며, 이를 통해 모델은 기존 지식을 활용하여 복잡한 문제를 해결하는 능력을 향상시킬 수 있다는 점을 강조합니다. 이러한 접근 방식은 **데이터 효율성을 극대화하고 막대한 계산 비용을 절감**할 수 있는 잠재력을 가지고 있으며, 인공지능 분야에 대한 새로운 이해를 제시합니다.  결론적으로, **최소한의 예시만으로도 복잡한 추론 능력을 효과적으로 유도하는 방법**은 향후 인공지능 연구의 새로운 패러다임을 제시할 수 있습니다.

#### Cognitive Templates
본 논문에서 제시된 '인지적 템플릿(Cognitive Templates)' 개념은 **사전 훈련된 기초 모델이 이미 보유한 방대한 지식 기반을 효과적으로 활용하는 방법**을 설명하는 핵심 개념입니다.  **소량의 고품질 훈련 데이터(예시)**는 모델이 기존 지식을 복잡한 추론 과제 해결에 적용하는 방법을 보여주는 '템플릿' 역할을 합니다.  즉, 대량의 데이터가 아닌 **선별된 몇몇 예시**를 통해 모델이 스스로 추론 능력을 발휘하도록 유도하는 것입니다. 이는 기존의 대규모 데이터 기반 훈련 방식에 대한 새로운 관점을 제시하며, **데이터 효율성**을 극대화하는 훈련 전략의 중요성을 강조합니다.  **인지적 템플릿은 단순한 암기가 아닌 일반화된 추론 능력 신장**에 기여하며,  **모델의 사고 과정을 명시적으로 제시**함으로써 해결 과정의 투명성과 재현성을 높이는 데 기여할 수 있습니다.  따라서,  '인지적 템플릿'은 향후 효율적인 인공지능 모델 개발 및 고급 추론 능력 향상에 중요한 역할을 할 것으로 예상됩니다.

#### Future Research
본 논문의 "미래 연구" 부분은 **데이터 효율적인 추론에 대한 이해를 넓히는 것**에 초점을 맞춥니다.  **수학적 추론 영역을 넘어 과학적 추론, 논리적 추론, 인과 추론 등 다양한 영역으로 LIMO 가설을 확장**하는 연구가 필요하며, 이를 위해서는 **도메인별로 질적 지표를 조정**하고 **새로운 평가 프레임워크를 개발**해야 합니다.  또한, **추론 과정의 질적 측면을 자동화된 시스템으로 평가**하고 개선하는 연구가 중요하며,  **다중 모달 정보 통합**을 통한 추론 능력 향상 및 **실제 문제 해결**에 LIMO 원리를 적용하는 연구가 필요합니다.  **인지 과학적 관점을 통합하여** 효율적인 추론 전략을 개발하고, **LLM 의 추론 과정을 인간의 인지 과정과 비교**함으로써 LIMO 가설에 대한 이론적 토대를 마련하는 것도 중요합니다.  결론적으로, **LIMO 가설을 다양한 분야에 적용**하고 그 효과를 검증하며,  **효율적 추론 메커니즘에 대한 이론적 이해를 심화**하는 것이 미래 연구의 주요 방향입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.03387/extracted/6181360/figure/data-quality.png)

> 🔼 이 그림은 서로 다른 품질의 추론 체인으로 훈련된 모델들의 성능을 비교한 것입니다.  세로축은 정확도, 가로축은 추론 체인의 품질 수준을 나타냅니다.  그림에서 알 수 있듯이, 높은 품질의 추론 체인으로 훈련된 모델일수록 AIME24와 MATH500 벤치마크에서 더 높은 정확도를 달성합니다. 이는 고품질 추론 체인이 모델의 성능에 중요한 영향을 미친다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Comparison of models trained on reasoning chains of different quality levels.
> </details>



![](https://arxiv.org/html/2502.03387/extracted/6181360/figure/quality-1.png)

> 🔼 그림 3은 서로 다른 난이도의 질문들(Simple-500, Complex-500, Advanced-500)로 학습된 모델들의 MATH와 AIME 벤치마크 성능을 비교한 것입니다.  Simple-500은 MATH 1, 2단계의 간단한 문제 500개, Complex-500은 MATH 3, 4, 5단계의 복잡한 문제 500개, Advanced-500은 과거 AIME 시험의 고난도 문제 500개로 구성됩니다.  각 데이터셋으로 미세 조정된 모델들의 AIME와 MATH 점수를 비교하여 질문의 질이 모델 성능에 미치는 영향을 보여줍니다.  고난도 문제로 학습된 모델이 더 높은 정확도를 달성하는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3:  Performance comparison on MATH and AIME benchmarks between models trained on different question quality: Simple-500, Complex-500, and Advanced-500.
> </details>



![](https://arxiv.org/html/2502.03387/extracted/6181360/figure/llm-backbone.png)

> 🔼 그림 4는 사전 훈련된 모델 선택이 수학적 추론 성능에 미치는 영향을 보여줍니다.  두 가지 다른 사전 훈련된 모델(Qwen1.5-32B-Chat 및 Qwen2.5-32B-Instruct)을 사용하여 동일한 LIMO 데이터셋으로 미세 조정을 수행한 결과를 비교합니다.  Qwen2.5-32B-Instruct 모델은 AIME24 및 MATH500 벤치마크에서 Qwen1.5-32B-Chat 모델보다 상당히 높은 정확도를 달성했습니다. 이는 Qwen2.5-32B-Instruct 모델의 사전 훈련 데이터 품질이 수학적 추론 능력에 더욱 효과적임을 시사합니다. 이 그림은 사전 훈련된 모델의 지식 기반이 제한된 예시만으로도 복잡한 추론 능력을 활성화하는 데 중요한 역할을 한다는 LIMO 가설을 뒷받침합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Impact of Pre-trained Model Choice on Mathematical Reasoning Performance
> </details>



![](https://arxiv.org/html/2502.03387/x2.png)

> 🔼 그림 5는 세 가지 다른 언어 모델, 즉 Qwen2.5-32B-Instruct, DeepSeek-R1, 그리고 LIMO가 동일한 수학 문제에 대해 생성한 응답을 비교한 것입니다. 이 그림은 각 모델의 추론 능력과 문제 해결 과정을 보여줍니다. Qwen2.5-32B-Instruct는 기본 모델로, 제한된 추론 능력을 보여줍니다. DeepSeek-R1은 강화 학습을 통해 훈련된 모델로, 더욱 발전된 추론 능력을 보여주지만, 여전히 복잡한 문제를 해결하는 데 어려움을 겪습니다. 반면 LIMO는 소량의 데이터로 훈련되었음에도 불구하고, DeepSeek-R1과 유사한 수준의 추론 능력을 보여주며, 더욱 효율적이고 정확하게 문제를 해결합니다. 특히, LIMO는 추론 과정에서 자기 반성 및 장기적인 사고 과정을 보여줍니다. 그림을 통해 LIMO의 데이터 효율성과 강력한 추론 능력이 잘 드러납니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Comparison between the responses generated by Qwen2.5-32B-Instruct, DeepSeek-R1, and LIMO
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Aspect | RL Scaling (e.g., o1, R1) | LIMO |
|---|---|---|
| **First Principle** | An implementation of the general principle: searching for optimal reasoning trajectories through RL | The fundamental principle: reasoning capabilities exist and need to be activated by high-quality reasoning trajectories |
| **Solution Nature** | Discovers reasoning trajectories through extensive RL-based exploration | Directly constructs high-quality reasoning trajectories based on cognitive understanding |
| **Core Challenge** | How to efficiently search for effective reasoning trajectories in a large solution space | How to identify and construct optimal reasoning trajectories that activate existing capabilities |
| **Methodology** | Implicit trajectory discovery through large-scale RL optimization | Explicit trajectory design through cognitive templates |
| **Search Strategy** | Broad exploration of solution space using computational resources | Targeted exploration guided by cognitive principles |
| **Resource       Efficiency** | Resource-intensive search process | Resource-efficient direct construction |
| **Generalization** | Through extensive sampling of trajectory space | Through understanding of fundamental reasoning patterns |{{< /table-caption >}}
> 🔼 표 2는 강화 학습(RL) 기반의 확장 접근 방식과 LIMO(Less-Is-More Optimization) 접근 방식의 차이점을 비교 분석한 표입니다.  두 접근 방식의 기본 원리, 해결책의 특징, 주요 과제, 탐색 전략, 자원 효율성 및 일반화 능력 등 여러 측면에서 비교하여 각 접근 방식의 특징과 차이점을 명확히 보여줍니다.  특히, RL 기반 확장은 최적의 추론 경로를 찾기 위해 광범위한 탐색을 수행하는 반면, LIMO는 기존의 사전 학습된 지식을 활용하여 효율적으로 고품질 추론 경로를 구성하는 방식에 초점을 맞춘다는 점을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Comparative Analysis of LIMO and RL Scaling Approaches
> </details>

{{< table-caption >}}
| Datasets | OpenAI-o1-preview | Qwen2.5-32B-Instruct | QwQ-32B-preview | OpenThoughts(114k) | NuminaMath(100k) | LIMO ours(817) |
|---|---|---|---|---|---|---|
| In Domain |  |  |  |  |  |  |
| AIME24 | 44.6 | 16.5 | 50.0 | 50.2 | 6.5 | **57.1** |
| MATH500 | 85.5 | 79.4 | 89.8 | 80.6 | 59.2 | **94.8** |
| AMC23 | 81.8 | 64.0 | 83.6 | 80.5 | 40.6 | **92.0** |
| Out of Domain |  |  |  |  |  |  |
| OlympiadBench | 52.1 | 45.3 | 58.5 | 56.3 | 36.7 | **66.8** |
| CHMath | 50.0 | 27.3 | 68.5 | 74.1 | 11.2 | **75.4** |
| Gaokao | 62.1 | 72.1 | 80.1 | 63.2 | 49.4 | **81.0** |
| Kaoyan | 51.5 | 48.2 | 70.3 | 54.7 | 32.7 | **73.4** |
| GradeSchool | 62.8 | 56.7 | 63.8 | 39.0 | 36.2 | **76.2** |
| Minerva | **47.1** | 41.2 | 39.0 | 41.1 | 24.6 | 44.9 |
| GPQA | **73.3** | 48.0 | 65.1 | 42.9 | 25.8 | 66.7 |
| AVG. | 61.1 | 49.9 | 66.9 | 58.3 | 32.3 | **72.8** |{{< /table-caption >}}
> 🔼 표 3은 다양한 수학적 추론 벤치마크에 대한 모델 성능(pass@1)을 비교한 것입니다. 최첨단 LLMs(OpenAI-o1-preview, QwQ-32B-Preview), 기본 모델(Qwen2.5-32B-Instruct) 및 여러 데이터셋으로 미세 조정된 모델을 포함합니다. 괄호 안에는 학습 데이터 크기를 표시하며, 각 벤치마크에 대한 최상의 결과는 굵게 표시했습니다. 제안된 LIMO 모델(파란색으로 강조 표시)은 다른 미세 조정 모델(10만 개 이상)에 비해 훨씬 적은 학습 예제(817개)를 사용했음에도 불구하고 우수한 성능을 달성했습니다.
> <details>
> <summary>read the caption</summary>
> Table 3:  Comparison of model performance (pass@1) across various mathematical reasoning benchmarks Models include state-of-the-art LLMs (OpenAI-o1-preview, QwQ-32B-Preview), our base model (Qwen2.5-32B-Instruct), and models fine-tuned on different datasets. Training data sizes are shown in parentheses. Best results for each benchmark are shown in bold. Our proposed LIMO model (highlighted in blue) achieves superior performance despite using significantly fewer training examples (817) compared to other fine-tuned models (more than 100k).
> </details>

{{< table-caption >}}
| Data Quality Level | Avg. Tokens per response | Avg. Lines per response | Top 10 Frequently Occurring Keywords (in order) |
|---|---|---|---| 
| Level 1 | 230 | 9.21 | since, however, number, let, thus, which, get, two, triangle, theta |
| Level 2 | 444.88 | 50.68 | number, need, times, which, find, list, thus, since, triangle, sum |
| Level 3 | 4956.11 | 375.60 | perhaps, alternatively, consider, number, wait, which, sides, need, equal, seems |
| Level 4 | 4726.97 | 354.87 | wait, which, number, perhaps, therefore, let, since, maybe, sides, two |
| Level 5 | 5290.26 | 239.29 | wait, therefore, which, number, since, lets, two, sides, let, maybe |{{< /table-caption >}}
> 🔼 표 4는 다양한 품질의 예시로 훈련된 모델에 대한 통계적 분석을 보여줍니다. 이 표는 응답당 평균 토큰 수, 응답당 평균 줄 수, 그리고 모델이 생성한 응답에서 자주 사용되는 키워드라는 세 가지 주요 지표를 제시합니다. 추론 전환 및 불확실성과 관련된 키워드는 굵게 표시되며, 일반적인 불용어(예: “a”, “the”)는 실질적인 언어 패턴에 초점을 맞추기 위해 제외됩니다. 응답 길이와 키워드 사용 패턴의 현저한 차이는 다양한 수준의 추론 복잡성을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 4:  Statistical analysis of models trained with examples of varying data quality. This table presents three key metrics: average token count per response, average line count per response, and frequently occurring keywords in model-generated responses. Keywords associated with reasoning transitions and uncertainty are highlighted in bold, with common stop words (e.g., “a”, “the”) excluded to focus on substantive language patterns. Notable differences in response length and keyword usage patterns suggest varying levels of reasoning complexity.
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
{{< /gallery >}}