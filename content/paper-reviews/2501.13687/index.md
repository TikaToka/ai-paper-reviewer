---
title: "Question Answering on Patient Medical Records with Private Fine-Tuned LLMs"
summary: "소규모 사전 학습된 LLM 파인튜닝을 통해 의료 데이터 질문 응답 시스템의 정확성과 효율성을 높이고, 프라이버시 문제를 해결했습니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Question Answering", "🏢 Stanford University",]
showSummary: true
date: 2025-01-23
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.13687 {{< /keyword >}}
{{< keyword icon="writer" >}} Sara Kothari et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-27 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.13687" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.13687" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/question-answering-on-patient-medical-records" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

본 연구는 **의료 데이터의 복잡성과 방대한 양**으로 인해 중요한 건강 정보를 얻기 어려운 문제를 다룹니다. 기존의 대규모 언어 모델(LLM)은 프라이버시 우려로 인해 의료 데이터에 적용하기 어렵다는 한계가 있었습니다. 

본 연구는 이러한 문제를 해결하기 위해 **소규모 오픈소스 LLM을 FHIR 데이터에 파인튜닝**하는 새로운 접근 방식을 제안합니다.  이는 의료 질문에 대한 관련 FHIR 리소스 식별(Task 1)과 질문 응답 생성(Task 2)의 두 단계로 구성됩니다. 실험 결과, 소규모 파인튜닝 모델은 GPT-4와 같은 대규모 모델보다 Task 1에서 0.55%, Task 2에서 42% 높은 성능을 보였습니다.  **엣지 환경에서의 프라이버시 보장** 및 여러 가지 모델 행동 양상에 대한 심층적인 분석도 함께 제시됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 소규모 LLM 파인튜닝을 통해 대규모 LLM과 비슷한 성능을 달성하면서도 효율성과 프라이버시를 개선할 수 있습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 연속적인 파인튜닝 기법은 다중 작업 성능에 영향을 미치며, 데이터셋 크기는 모델 성능에 영향을 미칩니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} LLM은 자기 평가 시스템에서 자기 선호도 편향을 보입니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
이 논문은 **의료 데이터 프라이버시**를 보장하면서 **의료 질문 응답 시스템**을 구축하는 데 있어서 **엣지 환경에서의 사전 학습된 LLM의 효과적인 활용** 방법을 제시합니다.  **소규모 모델의 파인튜닝**을 통해 대규모 모델과 비교했을 때 성능 저하 없이 효율성과 프라이버시를 확보할 수 있다는 것을 보여줍니다. 따라서 의료 인공지능 분야 연구자들에게 중요한 시사점을 제공하며, 향후 연구 방향에 대한 새로운 가능성을 제시합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.13687/extracted/6148904/Figures/CompleteApproach.png)

> 🔼 그림 1은 논문의 접근 방식을 보여주는 다이어그램입니다. 환자의 질문과 FHIR(Fast Healthcare Interoperability Resources) 형식의 EHR(Electronic Health Records) 기록이 주요 입력값으로 사용됩니다.  시스템은 먼저 환자의 질문과 관련된 FHIR 자원을 식별하는 작업 1을 수행합니다. 이를 위해 관련성이 있는 FHIR 자원을 분류하는 기계 학습 모델이 사용됩니다.  그 다음 작업 2에서, 작업 1에서 식별된 관련 FHIR 자원을 사용하여 환자의 질문에 대한 답변을 생성합니다.  이 과정에서 또 다른 기계 학습 모델이 질문에 대한 답변을 생성하는 데 사용됩니다.  결과적으로, 시스템은 환자의 질문에 대한 답변을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Complete Approach Diagram
> </details>







### In-depth insights


#### FHIR-LLM QA
**FHIR-LLM QA는 전자 건강 기록(EHR)의 효율적이고 개인 정보 보호를 준수하는 질의응답 시스템을 구축하기 위한 혁신적인 접근 방식**입니다. 이는 빠른 의료 상호 운용 자원(FHIR) 표준을 사용하여 EHR 데이터에 대한 의미론적 질의응답을 가능하게 합니다.  **LLM(대규모 언어 모델)의 발전은 의료 데이터에 대한 질의응답을 가능하게 하여 의료 정보 접근성을 개선**합니다. 하지만 개인 정보 보호와 규정 준수를 위해 **온-프레미스 또는 에지 환경에서 LLM을 배포하는 것이 중요**합니다.  **FHIR-LLM QA 시스템은 질의와 관련된 FHIR 리소스를 식별하고 해당 리소스를 사용하여 질의에 대한 답변을 생성**하는 두 단계로 나뉩니다.  이를 위해 미세 조정된 소규모 LLM을 사용하여 효율성과 개인정보 보호를 향상시키고, 합성 데이터를 활용하여 다양한 측면들을 평가합니다.  **연구 결과는 미세 조정된 LLM이 대규모 모델보다 정확성과 효율성 면에서 우수함을 보여주며**, 이는 의료 서비스 제공자에게 실용적이고 개인 정보 보호가 강화된 솔루션을 제공합니다.

#### Private LLMs
본 논문에서 다루는 "Private LLMs"는 **개인정보보호 및 규정 준수**를 위해 **엣지 또는 개인 서버**에 배포된 대규모 언어 모델을 의미합니다.  **클라우드 기반의 공개 LLM**을 사용할 때 발생할 수 있는 **개인정보 유출 위험**을 피하기 위해 **의료 데이터**와 같은 민감한 정보를 처리하는 데 적합한 방안입니다.  Private LLMs의 주요 장점은 **데이터 프라이버시 보장** 및 **규정 준수**에 있습니다. 특히 의료 데이터와 같은 민감한 정보를 다룰 때 중요하며,  HIPAA, CCPA, BIPA와 같은 규정을 준수해야 하는 의료 분야에서 필수적입니다.  **모델의 크기**를 줄여 **자원 제약 환경**에서도 효율적으로 운영할 수 있다는 점 또한 중요한 이점입니다. 하지만, Private LLMs는 **정확도**가 떨어지거나 **성능**이 저하될 수 있는 **제한점**을 가지고 있기 때문에, 이를 보완하기 위한  **최적화 기술** 및 **데이터 관리 전략** 연구가 필요합니다.  **모델의 정확성과 효율성**을 높이기 위해 **파인튜닝**과 같은 기법을 적용하며, **데이터셋의 크기**와 **훈련 방식**이 성능에 큰 영향을 미칩니다. 따라서 **적절한 데이터셋 구축** 및 **모델 성능 평가**가 중요합니다.

#### Fine-tuning
본 논문에서 'Fine-tuning'은 **소규모 오픈소스 모델을 의료 데이터에 적합하도록 조정하는 핵심 기술**로 제시됩니다.  기존의 대규모 언어 모델의 막대한 컴퓨팅 자원 요구사항과 개인정보보호 문제를 해결하기 위해,  **파라미터 효율적인 미세 조정 기법(PEFT)**, 특히 QLoRA를 활용하여 계산 비용을 절감하고 효율성을 높입니다. 이는 의료 데이터의 특수성을 고려하여 모델 성능을 향상시키는 동시에 **개인정보보호 및 엣지 환경 배포**에 적합한 솔루션을 제공합니다.  **다양한 크기의 학습 데이터셋을 사용한 실험**을 통해 미세조정의 효과와 데이터 규모의 영향을 분석하고,  **연속적인 미세조정**의 장단점을 다각적으로 평가합니다.  이는 **의료 질의응답 시스템의 실용성과 신뢰성을 높이기 위한 중요한 전략**임을 시사합니다.  **모델의 자기 선호 편향**과 같은 LLM의 고유한 특성도 고려하여,  보다 객관적이고 신뢰할 수 있는 평가 방식을 제시하고 있습니다.

#### Sequential FT
연구에서 제시된 순차적 파인튜닝(Sequential Fine-Tuning) 전략은 **다중 작업 학습**의 맥락에서 매우 중요합니다.  여러 작업에 대해 모델을 순차적으로 학습시키는 방식은 각 작업의 특징을 효과적으로 학습하는 데 기여할 수 있지만, 동시에 **이전 작업에 대한 지식을 잊어버리는 현상(Catastrophic Forgetting)**이 발생할 수 있다는 점을 시사합니다.  본 논문은 이러한 순차적 학습의 장단점을 다각적으로 분석하고, 특히 **다양한 모델 아키텍처(LLaMA, Mistral)**에 따라 순차적 파인튜닝의 효과가 다르게 나타나는 점을 강조합니다.  **데이터셋 크기** 또한 순차적 학습 결과에 영향을 미치는 중요한 변수로 제시되며, 이는 모델의 **일반화 능력**과 밀접한 관련이 있습니다. 따라서 순차적 파인튜닝 전략의 성공적인 적용을 위해서는 작업 순서, 모델 아키텍처, 그리고 데이터셋 크기 등의 요인들을 신중하게 고려해야 합니다.  **실험 결과**를 통해 순차적 학습의 효과는 단순히 작업 순서에만 의존하는 것이 아니라,  모델의 특성과 데이터 환경에 따라 상당히 달라질 수 있다는 점이 드러납니다.  이는 **최적의 파인튜닝 전략**을 선택하기 위해 보다 심도있는 분석이 필요함을 의미합니다.

#### Future Work
본 논문의 "향후 연구" 부분은 **다중 작업 학습(MTL)** 및 **지속적 사전 훈련(CPT)**을 활용하여 FHIR 데이터 질의 성능을 향상시키는 방향으로 진행될 것이라고 제시합니다.  특히, **단일 모델**을 개발하여 두 가지 작업(FHIR 자원 식별 및 질의 응답)을 동시에 효율적으로 처리하는 것을 목표로 합니다.  이는 **계산 효율성**과 **모델 성능**을 동시에 개선할 수 있는 유망한 접근 방식입니다.  **실제 환자 데이터**를 사용한 실험을 통해 합성 데이터 기반 실험의 결과를 검증하는 후속 연구도 필요합니다.  더불어,  **모델의 편향성** 문제를 해결하고, **모델의 설명 가능성**을 높이기 위한 추가 연구가 요구됩니다.  마지막으로,  **다양한 FHIR 리소스**와 **복잡한 의료 질의**에 대한 모델의 일반화 성능을 향상시키는 연구도 중요한 과제입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.13687/extracted/6148904/Figures/DataPrep.png)

> 🔼 이 그림은 논문의 데이터 준비 과정을 보여줍니다. Synthea를 사용하여 합성 FHIR 데이터를 생성하고, 불필요한 항목을 제거하여 환자에게 관련된 리소스만 남깁니다. GPT-4를 이용하여 질문을 생성하고, 관련/무관 리소스를 레이블링하여 Task 1과 Task 2를 위한 학습 데이터를 만듭니다.  Task 1은 질문과 FHIR 리소스의 관련성을 분류하는 것이고, Task 2는 관련 리소스를 바탕으로 질문에 답하는 것입니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Data Preparation Flow
> </details>



![](https://arxiv.org/html/2501.13687/extracted/6148904/Figures/task1exp1.png)

> 🔼 그림 3은 논문의 Task 1 Experiment 1 결과를 보여줍니다.  LLaMA 3.1 Base, LLaMA 3.1 Instruct, Mistral NeMo Base, Mistral NeMo Instruct 모델의 정확도, 정밀도, 재현율, F1 점수를 비교 분석한 표입니다.  각 모델의 크기(파라미터 수)도 함께 제시되어 있습니다. GPT-4와 Meditron 모델의 결과도 비교 대상으로 포함되어 있습니다. 미세 조정된 모델들이 기본 모델들보다 성능이 훨씬 우수함을 보여주고, 특히 LLaMA 3.1 Base 미세 조정 모델이 가장 높은 F1 점수를 기록했습니다.  GPT-4는 크기는 훨씬 크지만, F1 점수 측면에서는 미세 조정된 작은 모델들과 비슷한 성능을 보였습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Task 1 Experiment 1 Results
> </details>



![](https://arxiv.org/html/2501.13687/extracted/6148904/Figures/task1exp1f1.png)

> 🔼 그림 4는 논문의 Task 1 Experiment 1 결과에서 다양한 모델들의 F1 점수를 비교한 막대 그래프입니다.  LLaMA 3.1 Base와 Mistral NeMo Base 모델을 미세 조정한 결과, GPT-4와 Meditron 모델보다 높은 F1 점수를 달성했음을 보여줍니다. 특히, 미세 조정된 LLaMA 3.1 Base 모델은 GPT-4보다 우수한 성능을 나타냈고, 미세 조정 전의 기본 모델들보다 훨씬 향상된 성능을 보여줍니다. 이는 미세 조정을 통해 특정 작업에 대한 모델의 성능을 크게 향상시킬 수 있음을 시사합니다. 또한, Meditron 모델은 상대적으로 낮은 F1 점수를 기록하여, 특정 의료 데이터에 대한 미세 조정의 중요성을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Task 1 Experiment 1 F1 Scores
> </details>



![](https://arxiv.org/html/2501.13687/extracted/6148904/Figures/task1exp3.png)

> 🔼 그림 5는 논문의 실험 3 결과를 보여줍니다. 이 실험은 연속적인 파인튜닝이 모델의 성능에 미치는 영향을 분석하기 위해 수행되었습니다.  구체적으로는, 모델을 과제 1에 대해 먼저 파인튜닝한 후 과제 2에 대해 추가 파인튜닝을 수행하고, 그 역순으로도 실험을 진행하여 각 과제에 대한 성능 변화를 비교 분석했습니다.  표에는 각 모델의 정확도, 정밀도, 재현율, F1 점수와 매개변수 크기가 나타나 있으며, 과제 1에서 연속적인 파인튜닝을 수행했을 때 각 모델의 성능 변화를 명확하게 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Task 1 Experiment 3 Results
> </details>



![](https://arxiv.org/html/2501.13687/extracted/6148904/Figures/task2exp1.png)

> 🔼 그림 6은 논문의 Task 2 Experiment 1 결과를 보여줍니다.  다양한 모델(Mistral NeMo Base FT-4900, LLAMA Base FT-4900, GPT-4, LLAMA 3.1 Instruct, Mistral NeMo Base, Mistral NeMo Instruct, LLAMA 3.1 Base, Meditron)의 성능을 METEOR 점수로 비교하여 보여줍니다.  METEOR 점수는 질문 응답의 정확성을 평가하는 지표로, 높을수록 더 정확한 답변을 의미합니다.  이 표는 각 모델이 Task 2 (환자의 의료 질문에 답변 생성)에서 얼마나 좋은 성능을 보이는지 보여주는 결과를 요약한 것입니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Task 2 Experiment 1 Results
> </details>



![](https://arxiv.org/html/2501.13687/extracted/6148904/Figures/task2exp2.png)

> 🔼 그림 7은 논문의 5.2.2절 실험 결과를 보여줍니다. 이 실험은 Task 2에 대해, 학습 데이터 크기가 모델 성능에 미치는 영향을 평가하기 위해 4900개와 500개의 예제로 미세 조정된 Llama 3.1 기반과 Mistral NeMo 기반 모델들을 비교 분석한 결과를 나타냅니다.  x축은 모델 종류(Mistral NeMo Base FT, Llama Base FT), y축은 METEOR 점수를 나타내며, 막대 그래프는 4900개 예제와 500개 예제로 학습한 모델의 성능 차이를 시각적으로 보여줍니다.  결과적으로, 더 큰 데이터셋으로 학습된 모델들이 더 높은 METEOR 점수를 달성하여, 데이터 크기가 모델 성능 향상에 중요한 역할을 한다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Task 2 Experiment 2 Results
> </details>



![](https://arxiv.org/html/2501.13687/extracted/6148904/Figures/task2exp3.png)

> 🔼 그림 8은 논문의 5.2.3절 실험 3 결과를 보여줍니다. 이 실험에서는 Task 1과 Task 2에 순차적으로 미세 조정하는 방법과 Task 2에 직접 미세 조정하는 방법을 비교합니다. 표에는 여러 모델의 METEOR 점수가 나열되어 있으며, 각 모델의 Task 1 및 2에 대한 순차적 미세 조정 결과가 비교됩니다. 특히, Mistral NeMo 기반 모델과 LLaMA 기반 모델 간의 순차적 미세 조정 효과의 차이를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Task 2 Experiment 3 Results
> </details>



![](https://arxiv.org/html/2501.13687/extracted/6148904/Figures/llmjudge.png)

> 🔼 그림 9는 LLM이 평가자 역할을 맡았을 때의 승률 결과를 보여줍니다.  LLM(대규모 언어 모델)이 서로의 답변을 평가하는 실험 결과를 나타내며, '맹검' 평가(LLM이 어떤 모델의 응답인지 모르는 상태)와 '비맹검' 평가(LLM이 어떤 모델의 응답인지 아는 상태)의 결과를 비교하여 LLM의 자기 선호도 편향(자신의 응답을 더 선호하는 경향)을 분석합니다.  GPT-4와 Claude Sonnet 두 모델이 평가자로 사용되었으며, Mistral NeMo Sequential FT-4900 (Task 1 → Task 2)와 Mistral NeMo Base FT-4900 모델의 답변이 비교 대상이었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: LLM-as-a-judge Win Rate Results
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