---
title: "Text-to-CAD Generation Through Infusing Visual Feedback in Large Language Models"
summary: "CADFusion: 시각적 피드백을 활용한 텍스트-CAD 생성의 혁신!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 University of Toronto",]
showSummary: true
date: 2025-01-31
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.19054 {{< /keyword >}}
{{< keyword icon="writer" >}} Ruiyu Wang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-05 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.19054" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.19054" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/text-to-cad-generation-through-infusing" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존 Text-to-CAD 모델들은 **텍스트 설명만을 이용**하여 CAD 파라메트릭 시퀀스를 생성하는데, 이는 **다양한 시각적 특징과 다대일 매핑 특성**을 가진 CAD 모델의 복잡성을 충분히 반영하지 못했습니다.  따라서, 생성된 모델의 시각적 품질이 떨어지고, 다양한 디자인을 생성하는 데 어려움이 있었습니다.  이러한 문제를 해결하기 위해, 기존 연구들은 주로 정답 파라메트릭 시퀀스를 지도 학습에 활용해 왔으나,  시각 정보의 중요성을 간과했습니다.

본 논문에서는 **대규모 언어 모델(LLM)을 기반으로 시퀀셜 학습과 시각적 피드백을 결합**한 새로운 프레임워크 CADFusion을 제안합니다.  CADFusion은 **정답 파라메트릭 시퀀스를 이용한 시퀀셜 학습**으로 논리적으로 일관성 있는 파라메트릭 시퀀스 생성 능력을 향상시키고, **렌더링된 시각적 결과물에 대한 선호도 학습**을 통해 시각적으로 선호되는 객체를 생성하도록 모델을 학습시킵니다.  특히, 비차별화 가능한 렌더링 과정을 해결하기 위해 DPO(Direct Preference Optimization) 기법을 사용하고,  LVM(Large Vision-Language Model)을 이용해 효율적으로 선호도 데이터를 수집하는 파이프라인을 구축하여 실용성을 높였습니다.  실험 결과, CADFusion은 기존 방법들보다 정량적, 정성적으로 우수한 성능을 보였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 시각적 피드백을 통합한 LLM 기반 Text-to-CAD 프레임워크인 CADFusion 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 시퀀셜 학습과 시각적 피드백 단계를 번갈아 수행하는 반복적 학습 방식을 통해 성능 향상 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} DPO 기법과 LVM 기반의 자동화된 선호도 데이터 수집 파이프라인을 통해 효율적이고 효과적인 학습 달성 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **텍스트 기반 CAD 모델 생성 분야의 새로운 접근법**을 제시하여, 연구자들에게 **시각적 피드백을 활용한 효율적인 모델 학습 방식**을 제안합니다.  **대규모 언어 모델(LLM)**을 기반으로 시퀀셜 학습과 시각적 피드백을 결합하여 **정확도와 효율성을 향상**시킨 CADFusion 프레임워크는 해당 분야의 발전에 크게 기여하며, 향후 연구 방향을 제시합니다. 특히, **비차별화 가능한 렌더링 과정**을 우회하는 DPO 기법과 LVM 기반의 자동화된 선호도 데이터 수집 파이프라인은 **실용적인 측면**에서 큰 의미를 갖습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.19054/x1.png)

> 🔼 그림 1은 본 논문에서 제시하는 Text-to-CAD 모델의 개념을 보여주는 그림입니다. (a)는 사용자의 텍스트 입력을 보여주고, (b)는 이를 CAD 파라메트릭 시퀀스로 변환하는 과정을 나타냅니다. (b)와 (c)는 CAD 모델이 파라메트릭 시퀀스를 사용하여 생성되고 실제 사용을 위한 시각적 개체로 렌더링되는 다중 모드 특성을 보여줍니다. (d)는 서로 다른 파라메트릭 시퀀스가 동일한 시각적 개체를 생성할 수 있음을 보여주는 다대일 렌더링 특성을 보여줍니다.  즉, 텍스트 입력에서 CAD 모델 생성까지의 전 과정과 CAD 모델의 다중 모드 특징 및 다대일 렌더링 특징을 시각적으로 설명하고 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  (a) and (b): Illustration of Text-to-CAD, which converts a texutal description into CAD parametric sequences. (b) and (c): Illustration of multimodal characteristics. CAD models are created using parametric sequences and rendered as visual objects for practical use. (d): Illustration of many-to-one rendering characteristics. Different parametric sequences can produce identical visual objects.
> </details>





{{< table-caption >}}
| Method | Sketch F1↑ | Extrusion F1↑ | CD↓ | COV↑ | MMD↓ | JSD↓ | IR↓ | LVM Score↑ | Avg. Rank↓ |
|---|---|---|---|---|---|---|---|---|---| 
| **GPT-4o** | 82.96 | 85.72 | 85.04 | 72.40 | 6.60 | 37.93 | 74.26 | 5.13 | 3.22 |
| **Text2CAD** | 63.94 | 92.13 | 30.23 | - | - | - | - | 3.37 | 2.97 |
| **CADFusion** | 85.22 | 92.79 | 45.67 | 90.40 | 3.49 | 17.11 | 6.20 | 8.96 | 1.86 |{{< /table-caption >}}

> 🔼 표 1은 제안된 CADFusion 모델의 정량적 성능 평가 결과를 보여줍니다.  F1 점수(스케치 및 압출), 샴페르 거리(CD), 적용 범위(COV), 최소 매칭 거리(MMD), 젠센-섀넌 발산(JSD), 무효 비율(IR), LVM 점수 및 인간 평가에 따른 평균 순위(Avg. Rank) 등 다양한 지표를 사용하여 모델 성능을 평가했습니다.  화살표(↑ 또는 ↓)는 해당 지표에서 높은 값이 더 나은지(↑), 낮은 값이 더 나은지(↓)를 나타냅니다.  Text2CAD 모델의 경우, 설정 차이로 인해 COV, MMD, JSD 지표는 계산하지 못했습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Quantative results - Test results on F1 scores including Sketch (primitive, averaged) and Extrusion, Chamfer Distance (CD), Coverage (COV), Minimum Matching Distance (MMD), Jensen-Shannon Divergence (JSD), Invalidity Ratio (IR), the LVM Score and the average rank from human evaluation (Avg. Rank). An upward arrow (↑↑\uparrow↑) indicates that higher values are better, while a downward arrow (↓↓\downarrow↓) signifies that lower values are preferred. Since Text2CAD does not release COV, MMD, and JSD, and we were unable to compute them ourselves due to differences in setup, these values are unavailable.
> </details>





### In-depth insights


#### Visual Feedback Fusion
본 논문에서 제안하는 "Visual Feedback Fusion"은 **텍스트 기반 CAD 모델 생성**이라는 어려운 문제에 대한 혁신적인 접근 방식입니다. 기존의 순차적 신호(parametric sequences) 학습에 더하여 **렌더링된 시각적 객체**를 활용하여 모델의 성능을 향상시키는 데 초점을 맞춥니다.  **순차 학습(SL)** 단계와 **시각적 피드백(VF)** 단계를 번갈아 가며 진행하는 반복적인 학습 과정을 통해 **두 신호의 장점을 결합**합니다.  VF 단계는 차별화 불가능한 렌더링 과정을 극복하기 위해 **직접적 선호도 최적화(DPO)**를 사용하며, 대규모 비전-언어 모델(LVM)을 이용해 효율적으로 선호도 데이터를 수집합니다. 이러한 접근법은 **정확성과 시각적 품질** 모두를 향상시키는 데 기여하며, 특히 복잡한 기하학적 형태의 CAD 모델 생성에 효과적입니다.  **LLM(대규모 언어 모델)**을 백본으로 사용하여 자연어 이해 능력과 CAD 설계에 대한 기본 지식을 활용하고, **전이 학습**을 통해 효율성을 높입니다.  결론적으로, Visual Feedback Fusion은 텍스트를 CAD 모델로 변환하는 과정을 크게 개선하는 동시에 다양한 분야에서 CAD 모델 생성의 접근성을 높일 것으로 기대됩니다.

#### LLM-based CAD
LLM 기반 CAD는 **대규모 언어 모델(LLM)**의 잠재력을 활용하여 컴퓨터 지원 설계(CAD) 분야를 혁신할 가능성을 제시합니다.  텍스트 설명을 CAD 파라메트릭 시퀀스로 변환하는 능력은 설계 프로세스를 간소화하고 전문 지식이 부족한 사용자도 접근성을 높일 수 있습니다.  **다만, CAD 모델의 다중 모드 특성(파라메트릭 시퀀스와 렌더링된 비주얼 객체)**과 **다대일 매핑(여러 파라메트릭 시퀀스가 동일한 비주얼 객체 생성)**은 LLM 기반 CAD 개발에 중요한 과제를 제시합니다.  따라서, **시퀀셜 신호(파라메트릭 시퀀스)와 비주얼 신호(렌더링된 객체)** 모두를 활용하는 효과적인 학습 전략이 필요하며,  **순차 학습과 시각적 피드백을 번갈아 적용**하는 방식은 이러한 과제 해결에 도움이 될 수 있습니다.  **직접 선호도 최적화(DPO)와 같은 기술**을 통해 비미분 가능한 렌더링 과정을 해결하고, **대규모 비전-언어 모델(LVM)**을 활용하여 효율적인 선호도 데이터 수집이 가능합니다.  LLM 기반 CAD는 **자동화와 효율성을 높여 설계 시간을 단축**시키지만, **복잡한 형태나 다양한 객체 조합**에 대한 처리 능력 향상, 그리고 **인간의 개입을 최소화**하는 방향으로 발전해야 할 것입니다.  **데이터의 질적 향상과 모델의 일반화 능력 향상**을 위한 지속적인 연구가 필요합니다.

#### DPO for CAD
본 논문에서 제시된 DPO(Direct Preference Optimization) 기반 CAD(Computer-Aided Design) 접근법은 **차별화 가능하지 않은 렌더링 과정**이라는 난관을 극복하는 데 중점을 둡니다. 기존 강화학습 방식의 계산 비용 문제를 해결하기 위해, **직접적인 보상 최대화**를 통해 모델을 효율적으로 학습시키는 방식을 채택했습니다. 이는 CAD 모델의 시각적 피드백을 활용하여, 생성된 파라메트릭 시퀀스가 실제로 **선호도가 높은 시각적 객체**로 렌더링될 수 있도록 유도하는 역할을 합니다.  **비교 불가능한 렌더링 과정**을 우회함으로써, DPO는 다양한 시각적 피드백을 통합하고, 생성된 CAD 모델의 질적 향상을 도모하는 효과적인 전략으로 제시됩니다. 하지만, **신뢰할 수 있는 선호도 데이터 확보**의 어려움은 여전히 과제로 남아 있습니다. 본 논문에서는 대규모 비전-언어 모델을 활용한 자동화된 파이프라인을 통해 이 문제를 해결하고자 하였으나,  **데이터 품질 및 효율성** 측면에서 추가적인 연구가 필요해 보입니다.  결론적으로, DPO 기반 CAD 접근법은 매력적인 대안이지만, 선호도 데이터 수집 및 품질 관리에 대한 지속적인 개선 노력이 필요합니다.

#### Multimodal CAD
**멀티모달 CAD**는 텍스트, 이미지, 3D 모델과 같은 다양한 모달리티의 정보를 통합하여 CAD 모델링 과정을 향상시키는 접근 방식입니다. 기존의 텍스트 기반 CAD 생성 방식은 언어 모델의 제한으로 복잡한 형상을 생성하는 데 어려움을 겪었으나, **멀티모달 방식은 이미지나 3D 모델의 시각적 정보를 활용하여 이러한 문제를 해결할 수 있습니다.**  **이미지 기반 피드백**을 통해 생성된 모델의 시각적 품질을 높이고, **3D 모델의 형상 정보**를 활용하여 보다 정확하고 완성도 높은 CAD 모델을 생성할 수 있습니다.  하지만 **다양한 모달리티의 데이터를 효과적으로 통합하고 처리하는 기술**과 **모달리티 간의 일관성을 유지하는 방법**에 대한 연구가 더 필요합니다.  또한, **데이터 수집 및 주석 작업의 어려움**과 **모델의 해석력 향상**도 중요한 과제입니다.  **멀티모달 CAD는 사용자의 의도를 보다 정확하게 반영하고 효율성을 높이는 CAD 시스템 구축**에 기여할 수 있지만, 기술적 및 실용적 과제를 극복하기 위한 지속적인 연구가 필요합니다.

#### CADFusion Limits
CADFusion은 텍스트 기반 CAD 모델 생성 분야에서 괄목할 만한 성과를 보였지만, 여전히 몇 가지 제한점을 가지고 있습니다. **복잡한 형태의 객체 생성에 어려움을 겪는다**는 점이 가장 큰 한계입니다. 여러 개의 개별 요소를 결합하거나 복잡한 기하학적 변형을 포함하는 모델 생성 시 정확도가 떨어지고, 예상치 못한 결과를 생성할 가능성이 있습니다. 또한, **문자나 단어와 같은 특수한 형태의 객체를 생성하는 데에는 어려움이 있습니다.**  이러한 제한은 모델의 학습 데이터 및 아키텍처와 밀접한 관련이 있습니다.  **더욱 다양하고 복잡한 데이터로 모델을 학습시키고, 모델 아키텍처를 개선하여** 이러한 문제들을 해결하는 연구가 필요합니다.  **실시간 응용 프로그램**에 적용하기에는 처리 속도가 느릴 수 있으며, **다양한 CAD 소프트웨어와의 호환성**을 확보하는 것 또한 과제입니다.  **현실 세계의 다양한 디자인 요구사항을 충족하기 위해서는** 모델의 기능을 지속적으로 개선하고 확장하는 노력이 필요합니다.  마지막으로 **사용자의 의도를 정확하게 이해하고 반영**할 수 있는 기술적 한계 또한 존재합니다. 따라서, **자연어 처리 기술과 CAD 모델링 기술의 발전이 CADFusion의 성능 향상에 필수적**입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.19054/x2.png)

> 🔼 그림 2는 제안하는 CADFusion 프레임워크의 개요를 보여줍니다.  (a)는 지상 진실(ground-truth) CAD 매개변수 시퀀스를 사용하여 대규모 언어 모델(LLM)을 훈련시키는 순차 학습 단계를 설명합니다. 이 단계는 논리적으로 일관된 매개변수 시퀀스를 생성하는 데 중점을 둡니다. (b)는 시각적 피드백 단계를 보여줍니다. 이 단계에서는 렌더링된 시각적 객체가 선호되는 객체로 렌더링되는 매개변수 시퀀스에 보상을 하고 그렇지 않은 시퀀스에는 패널티를 부여하여 모델이 시각적 객체를 어떻게 인식하고 평가하는지 학습하도록 합니다. (c)는 두 단계가 번갈아 가면서 진행되어 두 신호의 장점을 모두 유지하는 반복적인 훈련 절차를 보여줍니다.  두 신호(순차 신호와 시각 신호)의 균형 잡힌 학습을 보장하고 양쪽 신호의 장점을 모두 보존합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2:  Overview of CADFusion. (a): The sequential learning stage trains LLMs using ground-truth CAD parametric sequences. (b): The visual feedback stage rewards CAD parametric sequences that render into preferred visual objects and penalizes those that do not. (c): The two stages are alternated to preserve contributions of both signals.
> </details>



![](https://arxiv.org/html/2501.19054/x3.png)

> 🔼 이 그림은 CADFusion 모델 훈련에 사용된 선호도 데이터 생성 과정을 보여줍니다. (a)는 샘플 CAD 매개변수 시퀀스를 생성하고 이를 시각적 개체로 렌더링하는 과정을, (b)는 다양한 측면(모양 품질, 수량, 분포)을 고려하는 대규모 비전 언어 모델(LVM)을 사용하여 시각적 개체를 평가하는 과정을, (c)는 LVM이 생성한 점수를 기반으로 선호도 데이터를 구성하는 과정을 각각 나타냅니다.  본 논문에서는 이 선호도 데이터를 활용하여 시각적 피드백을 모델 학습에 통합하는 방법을 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3:  Illustration of preference data construction. (a): Sample CAD parametric sequences and render them into visual objects. (b): Score the visual objects using LVMs with multi-aspect grading criteria. (c): Construct preference data based on LVM-generated scores.
> </details>



![](https://arxiv.org/html/2501.19054/x4.png)

> 🔼 본 그림은 논문의 3.3절 Visual Feedback 단계에서 사용된 다중 측면 평가 기준을 설명하는 그림입니다. 그림은 LVM(Large Vision-Language Model)이 CAD 모델의 시각적 품질을 평가할 때 고려하는 세 가지 기준(Shape Quality, Shape Quantity, Item Distribution)을 간략하게 보여줍니다. 각 기준은 CAD 모델의 모양 정확성, 구성 요소 수 일치 여부, 구성 요소 배치 자연스러움 등을 평가합니다. 그림의 목적은 LVM이 시각적 피드백을 효과적으로 처리하기 위해 어떤 요소들을 고려하는지 시각적으로 보여주는 것입니다.
> <details>
> <summary>read the caption</summary>
> Figure 4:  An illustrative example of the multi-aspect evaluation criteria used in LVM scoring. Note that the illustrations are simplified to conceptually represent each criterion.
> </details>



![](https://arxiv.org/html/2501.19054/x5.png)

> 🔼 그림 5는 본 논문에서 제시된 CADFusion 모델과 기존 모델들의 성능을 비교한 정성적 결과를 보여줍니다. 각 하위 섹션의 상단에는 입력 프롬프트가 표시되고, 이미지는 왼쪽에서 오른쪽으로 순서대로 정답, CADFusion, GPT-4, Text2CAD 결과 순으로 배열되어 있습니다. 렌더링할 수 없는 출력물에는 빨간색 십자 표시가 되어 있습니다. CADFusion은 모든 기준 모델보다 지시사항을 이해하고 순차적, 시각적으로 고품질의 CAD 객체를 생성하는 데 뛰어난 성능을 보여줍니다. 반면에 GPT-4는 잘못된 샘플을 자주 생성하고 형태의 세부 사항에 거의 주의를 기울이지 않습니다. Text2CAD는 규칙적인 외관을 가진 형태가 잘 갖춰진 기본적인 형태를 생성하지만, 지시사항을 정확하게 따르거나 복잡한 형태를 표현하는 데 어려움을 겪습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5:  Qualitative results. The input prompt is shown at the top of each subsection. Images are arranged from left to right in the following order: ground truth, CADFusion, GPT-4o, and Text2CAD. Outputs that cannot be rendered are marked with a red cross. CADFusion outperforms all baselines in understanding instructions and generating CAD objects that are both sequentially and visually high quality. GPT-4o frequently produces invalid samples and pays little attention to shape details. Text2CAD generates well-formed basic shapes with a regular appearance but struggles to accurately follow input instructions and represent complex geometries.
> </details>



![](https://arxiv.org/html/2501.19054/x6.png)

> 🔼 그림 6은 데이터 전처리 단계를 개괄적으로 보여줍니다. 원본 데이터셋은 텍스트 입력으로 사용될 캡션과, 정답 참조로 사용될 CAD 표현의 문자열로 변환됩니다.  구체적으로는, 원본 CAD 모델 데이터가 여러 단계를 거쳐 변환됩니다. 먼저, 각 CAD 모델에 대한 캡션을 생성하기 위해 Vision-Language Model (VLM)을 사용합니다. 그런 다음, 생성된 캡션의 정확도와 명확성을 높이기 위해 사람이 검토하고 수정하는 단계를 거칩니다.  동시에, 원본 CAD 모델 데이터는 CADFusion 시스템이 이해할 수 있는 문자열 형태의 CAD 표현으로 변환됩니다. 이렇게 생성된 텍스트 캡션과 문자열 형태의 CAD 표현은 Text-to-CAD 모델 학습에 사용되는 쌍(pair)으로 구성됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: An overview of the data preprocessing steps. The original dataset is transformed into captions that serve as textual inputs, while the corresponding stringified CAD representations are used as ground truth references.
> </details>



![](https://arxiv.org/html/2501.19054/x7.png)

> 🔼 그림 7은 여러 CAD 표현 방식과 그에 해당하는 캡션을 보여줍니다. 왼쪽에는 원시 SEM 형식의 CAD 표현과 함께 구문 분석된 시퀀스가 표시되며, 값은 디코딩에 사용된 패딩에 따라 다른 색상으로 강조 표시됩니다. 오른쪽에는 LVM이 생성하고 사람이 수정한 캡션이 표시됩니다. 사람이 미세 조정하는 동안 제거된 구절은 빨간색으로, 추가된 구절은 녹색으로 표시됩니다. 모든 표현과 캡션은 오른쪽 하단에 표시된 동일한 CAD 그림에 해당합니다.  이 그림은 Text-to-CAD 모델이 입력 텍스트를 CAD 파라메트릭 시퀀스로 변환하는 과정과, 생성된 시퀀스가 실제 CAD 모델과 얼마나 일치하는지를 보여주는 데 중요한 역할을 합니다. 원시 CAD 데이터의 복잡한 구조를 단순화하고 LLM이 이해할 수 있는 형태로 변환하는 과정과, LLM이 생성한 결과를 사람이 검토하고 수정하여 정확도를 높이는 과정을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: An overview of multiple CAD representations and their corresponding captions. Left: A CAD representation in the raw SEM format alongside its stringified sequence, with values highlighted in different colors based on the padding used for decoding. Right: Captions generated by the LVM and refined by human annotation. Phrases removed during human fine-tuning are marked in red, while those added by humans are marked in green. All representations and captions correspond to the same CAD figure, which is displayed in the bottom-right corner.
> </details>



![](https://arxiv.org/html/2501.19054/x8.png)

> 🔼 그림 8은 본 논문의 추가적인 정성적 결과를 보여줍니다. 그림은 패널과 원형 물체와 같은 범주로 그룹화되어 있으며, 각 하위 그림에는 실제 CAD 모델의 렌더링 이미지와 CADFusion 모델에 의해 생성된 이미지가 나란히 표시됩니다. 각 하위 그림의 아래에는 해당하는 텍스트 설명이 제공됩니다. 이를 통해, CADFusion 모델이 다양한 유형의 CAD 모델을 생성하는 데 성공했는지, 그리고 생성된 모델이 텍스트 설명과 얼마나 잘 일치하는지를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Additional qualitative results, Part 1. The results are grouped by categories such as panels and circular objects. In each sub-figure, the left image shows the figure rendered from the ground truth, while the right image displays the generation by CADFusion. The corresponding textual instructions are provided at the bottom.
> </details>



![](https://arxiv.org/html/2501.19054/x9.png)

> 🔼 그림 9는 논문의 추가적인 정성적 결과(2부)를 보여줍니다. 여러 개의 개별 항목과 복잡한 형태의 두 가지 범주로 결과가 그룹화되어 있습니다. 각 하위 그림에서 왼쪽 이미지는 실제 렌더링된 그림을, 오른쪽 이미지는 CADFusion에 의해 생성된 그림을 보여줍니다. 각 그림에 대한 텍스트 설명은 하단에 제공되어 있습니다. 이 그림은 다양한 복잡도의 CAD 모델 생성에 대한 CADFusion의 성능을 보여주는 여러 가지 예시를 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Additional qualitative results, Part 2. The results are grouped by categories such as multiple distinct items and complex shapes. In each sub-figure, the left image shows the figure rendered from the ground truth, while the right image displays the generation by CADFusion. The corresponding textual instructions are provided at the bottom.
> </details>



![](https://arxiv.org/html/2501.19054/x10.png)

> 🔼 그림 10은 하나의 프롬프트로부터 약간의 변형이 있는 CAD 인스턴스 생성에 대한 개요입니다. 각 하위 그림에서 왼쪽 상단 이미지는 실제 생성을 보여주고, 나머지 세 개는 CADFusion의 출력을 나타냅니다. 이 출력들은 두께, 너비, 그리고 잘라낸 크기의 변화를 보여줍니다. 각 하위 그림의 맨 위에는 프롬프트가 표시됩니다. 즉, 동일한 질의어에 대해서도 CADFusion 모델은 두께, 너비, 구멍 크기 등이 미세하게 다른 여러 결과물을 생성할 수 있음을 보여줍니다. 이는 사용자가 자신의 요구사항에 가장 적합한 디자인을 선택할 수 있도록 유연성을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: An overview of the generation of CAD instances with slight variations from a single prompt. In each sub-figure, the top-left image shows the ground truth generation, while the remaining three represent CADFusion’s outputs, which exhibit variations in thickness, width, and cutout size. The prompt is displayed at the top of each sub-figure.
> </details>



![](https://arxiv.org/html/2501.19054/x11.png)

> 🔼 그림 11은 CADFusion 모델이 잘못된 결과물을 생성하는 경우를 보여줍니다. 지시사항이 너무 복잡하거나 단어 모양 지식이 필요한 경우 잘못된 샘플이 생성되고, 생성해야 할 개별 항목이 너무 많거나 최종 CAD 인스턴스를 형성하기 위해 복잡한 병합이 필요한 경우 불일치 결과가 생성됩니다.  이 그림은 CADFusion이 단어나 숫자를 나타내는 모양을 생성하는 데 어려움을 겪는 경우와 여러 개의 개별 항목을 통합하는 데 어려움을 겪는 경우를 보여줍니다.  즉, 지시사항의 복잡성, 단어 모양 지식의 필요성, 생성해야 할 개별 항목의 수, 복잡한 형태 통합의 필요성 등이 CADFusion 모델의 성능에 영향을 미치는 요소임을 시각적으로 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Invalid and discrepant samples. CADFusion generates invalid samples when the instructions are too complex or involve word shape knowledge, and produces discrepant outcomes when there are too many distinct items to generate or when complex merges are required to form the final CAD instance.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | LVM Score ↑ | IR ↓ |
|---|---|---|
| CADFusion<sub>SL</sub> | 7.69 | 4.84 |
| CADFusion<sub>SL<sub>w/o HA</sub></sub> | 6.56 | 6.00 |
| CADFusion<sub>SL-VF</sub> | 5.94 | 88.87 |
| CADFusion<sub>SL-VF<sub>RPO</sub></sub> | 6.21 | 3.46 |
| CADFusion<sub>SL-VFSL(1)<sub>w/ HA</sub></sub> | 8.28 | 17.03 |
| CADFusion<sub>SL-VFSL(1)</sub> | 8.76 | 4.42 |
| CADFusion<sub>SL-VFSL(3)</sub> | 8.89 | 4.21 |
| CADFusion<sub>SL-VFSL(5)</sub> | 8.96 | 6.20 |{{< /table-caption >}}
> 🔼 표 2는 다양한 CADFusion 변형에 대한 LVM 점수와 무효 비율을 보여줍니다. 접미사 SL은 초기 순차 학습 단계로 모델을 학습시켰음을 나타내고, VF는 추가적인 순차 학습 없이 시각적 피드백 단계를 나타냅니다. VFSL은 순차 학습과 번갈아 가며 시각적 피드백을 나타냅니다. 태그 w/ HA는 데이터가 사람의 주석을 사용하여 전처리되었음을 나타내고, w/o HA는 사람의 주석이 없음을 나타냅니다. 괄호 안의 숫자는 VFSL 라운드의 수를 나타냅니다. RPO는 Liu et al.(2024)의 규제된 선호도 최적화(RPO)를 사용하여 DPO를 안정화시키는 모델을 참조합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: LVM scores and invalidity ratios across different CADFusion variants. The suffix SL indicates that the model is trained with the initial Sequential Learning stage, while VF denotes the Visual Feedback stage without additional Sequential Learning. VFSL represents Visual Feedback with alternating Sequential Learning. The tag w/ HA signifies that the data is preprocessed with human annotation, whereas w/o HA denotes the absence of human annotation. Numbers in parentheses indicate the number of VFSL rounds performed. RPO refers to the model using Regularized Preference Optimization (RPO) (Liu et al., 2024) to stabilize DPO.
> </details>

{{< table-caption >}}
| Method | Line | Arc | Circle | Extrusion | CD | 
|---|---|---|---|---|---| 
| **Text2CAD-intermediate** | 66.65 | 4.85 | 47.62 | **93.56** | 146.15 |
| **Text2CAD-expert** | 79.59 | 42.79 | 69.45 | 92.13 | **30.23** | 
| **Text2CAD-our-prompt** | 54.42 | 0.92 | 18.42 | 75.37 | 235.91 | 
| **CADFusion** | **83.71** | **81.99** | **89.97** | 92.79 | 45.67 | {{< /table-caption >}}
> 🔼 이 표는 본 논문에서 제안된 CADFusion 모델과 기존 Text2CAD 모델의 성능을 비교 분석한 결과를 보여줍니다.  Khan et al.(2024b)가 제시한 평가 지표(F1-Sketch, F1-Extrusion, CD, COV, MMD, JSD, IR)를 사용하여 모델 성능을 다각적으로 평가하였습니다.  Text2CAD 모델의 경우, 논문 저자들이 사용한 프롬프트(expert prompt)와 본 논문에서 사용한 프롬프트(our prompt), 중간 수준의 프롬프트(intermediate prompt) 세 가지 경우에 대해 성능을 측정하여 비교하였습니다.  CADFusion 모델은 본 논문에서 제시한 프롬프트를 사용하여 성능을 평가하였습니다.  표의 접미사는 각 모델의 프롬프트 유형을 나타냅니다. Text2CAD-ours와 CADFusion은 가장 유사한 프롬프트를 사용한 결과이고, Text2CAD-expert와 CADFusion은 본 논문의 주요 결과 비교에 사용된 모델입니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Results of our model and different Text2CAD prompts on metrics Proposed by Khan et al. (2024b). The suffix indicates the prompt type used for testing. Text2CAD-ours and CADFusion are the most aligned pairs, while Text2CAD-expert and CADFusion are the ones reported in the main paper.
> </details>

{{< table-caption >}}
| Method | LVM Score ↑ | IR ↓ |
|---|---|---|
| CADFusion<sub>SL</sub> | 7.69 | 4.84 |
| CADFusion<sub>SL<sub>w/o HA∼18k</sub></sub> | 6.56 | 6.00 |
| CADFusion<sub>SL<sub>w/o HA∼170k</sub></sub> | 6.60 | 9.04 |{{< /table-caption >}}
> 🔼 표 4는 서로 다른 CADFusion 변형에 대한 LVM 점수와 무효율을 보여줍니다. 세 가지 모델 모두 초기 순차 학습 단계만을 사용하여 훈련되었습니다. 접미사 w/o HA는 변형이 사람이 주석을 단 데이터를 사용하지 않음을 나타내고, 숫자는 훈련 세트의 크기를 나타냅니다. 이 표는 사람이 주석을 달지 않은 데이터를 사용한 변형과 훈련 데이터 크기의 차이에 따른 LVM 점수와 무효율의 변화를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 4: LVM scores and invalidity ratios across different CADFusion variants. All three models are trained using only the initial Sequential Learning stage. The suffix w/o HA indicates that the variant does not use human-annotated data, while the number denotes the size of the training set.
> </details>

{{< table-caption >}}
| Method | Avg. Rank ↓ |
|---|---| 
| **GPT-4o** -*8shot* | 3.22 |
| **Text2CAD** | 2.97 |
| **CADFusion**-*SFT only* | 2.03 |
| **CADFusion** | 1.86 |{{< /table-caption >}}
> 🔼 본 표는 인간 평가자들이 다양한 방법으로 생성된 CAD 모델의 품질을 평가한 결과를 보여줍니다. 평가자들은 각 모델이 생성한 CAD 모델들을 품질에 따라 순위를 매겼으며, 낮은 순위일수록 더 높은 품질을 나타냅니다.  표에는 GPT-40, Text2CAD, 그리고 본 논문에서 제시된 CADFusion 모델의 성능이 비교되어 있습니다. CADFusion 모델은 특히 시각적 피드백을 활용하여 품질이 향상되었음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Human Evaluation Results. Human annotators ranked the generations of different methods based on their quality, with a lower rank indicating higher human preference.
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