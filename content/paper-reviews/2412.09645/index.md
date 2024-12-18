---
title: "Evaluation Agent: Efficient and Promptable Evaluation Framework for Visual Generative Models"
summary: "Evaluation Agent: 더 빠르고, 유연하며, 설명 가능한 시각적 생성 모델 평가 프레임워크."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Generation", "🏢 Shanghai Artificial Intelligence Laboratory",]
showSummary: true
date: 2024-12-10
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.09645 {{< /keyword >}}
{{< keyword icon="writer" >}} Fan Zhang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-17 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.09645" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.09645" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/evaluation-agent-efficient-and-promptable" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

**고품질 이미지와 비디오를 생성하는 시각적 생성 모델**은 콘텐츠 제작, 디자인 등 다양한 분야에서 혁신을 일으키고 있습니다. 하지만 이러한 모델의 평가는 방대한 샘플링이 필요하며, 특히 확산 기반 모델의 경우 **계산 비용이 많이 들고 시간이 오래 걸립니다.** 기존 평가 방법은 **엄격한 파이프라인과 사전 정의된 기준**에 의존하여 사용자의 특정 요구를 충족하기 어렵고, 단순한 숫자 점수만 제공하여 해석에 어려움을 겪습니다. 인간 평가자는 몇 개의 샘플만으로도 모델의 성능에 대한 이해를 빠르게 얻을 수 있습니다.

이 논문에서는 **인간과 유사한 전략을 사용하여 시각적 생성 모델을 효율적으로 평가하는 Evaluation Agent 프레임워크를 제시**합니다. 이 프레임워크는 라운드당 적은 수의 샘플을 사용하여 **효율적이고 동적이며 다중 라운드 평가**를 수행하면서 상세하고 사용자 맞춤형 분석을 제공합니다. 핵심 기능으로는 **효율성, 프롬프트 가능한 평가, 설명 가능성, 확장성**이 있습니다. 실험 결과, Evaluation Agent는 기존 방법 대비 평가 시간을 10%로 단축하면서도 유사한 결과를 제공하는 것으로 나타났습니다. 이는 시각적 생성 모델 연구 및 효율적인 평가 발전에 크게 기여할 것으로 기대됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} Evaluation Agent는 기존 벤치마크 대비 평가 시간을 최대 90%까지 단축합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 사용자 지정 쿼리와 다양한 모델 및 도구와 호환됩니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 상세한 텍스트 분석과 함께 해석 가능한 결과를 제공합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**생성적 AI 모델 평가는 시간이 많이 걸리고 사용자 정의가 어렵습니다.** 이 논문은 평가 시간을 단축하고 해석 가능한 결과를 제공하며 다양한 사용자 쿼리를 처리하는 **새로운 프레임워크인 Evaluation Agent를 제시**합니다. 이는 생성적 AI 모델의 평가 방식을 재정의하고, 현재 연구 동향과 관련이 있으며, 보다 유연하고 효율적인 평가 방법 개발을 위한 새로운 길을 열어줍니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.09645/x1.png)

> 🔼 평가 에이전트의 예시를 보여줍니다. 기존 평가 방식은 고정된 벤치마크에서 대량의 샘플을 추출하여 시각 생성 모델을 평가합니다. 반면, 제안하는 평가 에이전트 프레임워크는 사용자의 특정 평가 요청에 맞춰 소량의 이미지 또는 비디오 샘플만 필요로 합니다. 또한, 단순한 수치 점수를 제공하는 것을 넘어 평가 결론에 대한 자세한 설명을 제공합니다. 그림에서 사용자는 VideoCrafter-2.0 모델이 객체와 객체의 속성을 얼마나 잘 생성하는지 묻고, 평가 에이전트는 여러 단계의 추론을 통해 모델의 성능을 분석하고 요약된 설명을 제공하는 과정을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: An Example of Evaluation Agent. Existing evaluation methods typically assess visual generative models by extensively sampling from a fixed benchmark. In contrast, our Evaluation Agent framework requires only a small number of sampled images or videos, tailored to the user’s specific evaluation request. Additionally, it goes beyond providing a simple numerical score by offering detailed explanations to the evaluation conclusions.
> </details>





{{< table-caption >}}
| Benchmark | Analysis | Customized<br>Supported<br># Required<br>Open Evaluation<br>Dynamic<br>Open<br>Tool-Use | Queries |  |  |  |  |
|---|---|---|---|---|---|---|---| 
|  |  | Queries |  |  |  |  |  |
|  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |
|  |  |  |  |  |  |  |  |
|  | Tool-Use |  |  |  |  |  |  |
| FID / FVD [Unterthiner et al. (2018); Heusel et al. (2017)] | ✗ | ✗ | T2I / T2V | 2,048 | ✗ (Fixed-Form) | ✗ | ✗ |
| T2I-CompBench [Huang et al. (2023)] | ✗ | ✗ | T2I | 18,000 | ✗ (Pre-Defined) | ✗ | ✗ |
| VBench [Huang et al. (2024a)] | ✗ | ✗ | T2V | 4,730 | ✗ (Pre-Defined) | ✗ | ✗ |
| **Evaluation Agent (Ours)** | ✓ | ✓ | T2I & T2V | 400 | ✓ (Open-Ended) | ✓ | ✓ |{{< /table-caption >}}

> 🔼 이 표는 평가 에이전트 프레임워크와 기존 텍스트-이미지(T2I), 텍스트-비디오(T2V) 벤치마크를 비교합니다. 평가 에이전트는 맞춤형 사용자 쿼리를 자연어로 지원하며 T2I 및 T2V 모델 모두에서 작동합니다. 기존 벤치마크와 달리, 여러 도구를 사용하여 평가 프로세스를 동적으로 업데이트하여 자세한 텍스트 분석과 함께 종합적이고 설명 가능한 결과를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparison of the Evaluation Agent Framework with Traditional T2I and T2V Benchmarks. The Evaluation Agent framework supports customized user queries in natural language and works with both T2I and T2V models. Unlike traditional benchmarks, it dynamically updates the evaluation process using multiple tools, providing comprehensive and explainable results with detailed textual analysis.
> </details>





### In-depth insights


#### EvalAgent Framework
**EvalAgent 프레임워크**는 시각적 생성 모델 평가를 위한 효율적이고 프롬프트 가능한 접근 방식을 소개합니다. 기존 벤치마크의 한계를 해결하기 위해 인간과 유사한 평가 전략을 모방한 **동적**이고 **다중 라운드** 평가 프로세스를 사용합니다. EvalAgent는 먼저 사용자 쿼리에 따라 평가할 초기 하위 측면을 식별한 다음 중간 결과로부터 피드백을 기반으로 반복적으로 개선합니다. 이 동적 접근 방식을 통해 EvalAgent는 모델 기능의 미묘한 차이를 발견하고 강점과 약점에 대한 자세한 분석을 제공할 수 있습니다. 또한, EvalAgent는 **개방형 사용자 입력**을 수용하며 고정된 프롬프트와 평가 지표에 의존하지 않습니다. **설명 가능**하고 **상세한 통찰력**을 제공하여 단일 숫자 점수를 넘어 결과에 대한 포괄적인 이해를 제공합니다. 마지막으로, EvalAgent는 다양한 메트릭 및 평가 도구와 원활하게 통합되어 **확장성**과 성장을 보장합니다. 요약하면, EvalAgent 프레임워크는 효율성, 프롬프트 가능성, 설명 가능성, 확장성을 결합하여 시각적 생성 모델을 평가하는 견고하고 다재다능한 방법을 제공합니다.

#### Dynamic Multi-Round Eval
**동적 다중 라운드 평가**는 생성 모델을 평가하는 혁신적인 접근 방식입니다. 기존 벤치마크의 정적인 특성과 달리 이 방법은 **반복적인 평가 프로세스**를 사용합니다. 모델은 여러 라운드에 걸쳐 평가되고 각 라운드는 이전 라운드의 결과를 기반으로 합니다. 이 동적 특성을 통해 **미묘한 모델 동작과 한계**를 밝혀낼 수 있습니다. **사용자 지정 프롬프트**를 사용하여 각 라운드를 조정하여 특정 사용자 요구 사항을 충족할 수 있습니다. 또한 이 반복적인 프로세스는 **필요한 샘플 수를 줄여** 특히 확산 기반 모델에 유용합니다. 전반적으로 동적 다중 라운드 평가는 **효율성, 유연성 및 사용자 맞춤 설정**을 제공하여 생성 모델에 대한 더 깊고 의미 있는 평가를 가능하게 합니다.

#### Open-Ended Query Eval
**개방형 쿼리 평가**는 사용자의 **특정 요구**에 맞춰 모델을 평가하는 데 중점을 둡니다. 고정된 벤치마크와 달리 **유연한 프롬프트 디자인**과 **동적 평가**를 통해 **다양한 시나리오**를 처리합니다. 이는 모델의 **강점과 약점**에 대한 **세부적인 분석**을 가능하게 하여 특정 영역에서의 성능을 정확하게 파악할 수 있도록 합니다. 또한 복잡한 스타일 통합과 같은 **고급 기능**을 평가하고 **창의적인 프롬프트**를 효과적으로 처리하는 능력을 테스트하여 모델의 **한계**를 밝혀냅니다.

#### Benchmark Comparison
**벤치마크 비교**는 시각적 생성 모델 평가에 있어 중요한 부분입니다.  기존 벤치마크는 **고정된 프롬프트와 평가 지표**를 사용하여 모델의 다양한 기능을 평가하지만, 샘플링 수가 많아 **계산 비용이 많이 들고 시간이 오래 걸립니다.** 또한, **단일 수치 점수**만 제공하여 사용자가 의미 있는 분석을 위해 추가 노력을 기울여야 하며, **개방형 입력이나 다양한 사용자 요구 사항에 대한 적응성이 떨어집니다.** 따라서, 평가의 효율성과 유연성을 개선하기 위해서는 동적인 다단계 평가 및 사용자 정의 쿼리에 대한 지원 등이 필요합니다.  **인간 평가자처럼** 소수의 샘플만으로도 모델 성능에 대한 전반적인 이해를 얻는 방식이 효율적인 평가를 위한 한 가지 방법이 될 수 있습니다.

#### LLM Agent Limits
**LLM 에이전트의 한계**는 현재 연구 분야에서 중요한 문제입니다. LLM은 **추론 및 계획 능력**이 뛰어나지만, **도구 사용**과 관련하여 몇 가지 제약이 있습니다. 예를 들어, LLM은 종종 특정 작업에 **잘못된 도구**를 선택하여 평가의 정확성에 부정적인 영향을 미칩니다. 또한 LLM은 **반복적인 출력**을 생성하고 **최종 결과를 생성하지 못하는** 경우가 있습니다. 이러한 제약은 **복잡한 평가 작업**에서 LLM 에이전트의 효율성을 제한합니다. 향후 연구는 LLM의 **도구 사용 기능**을 개선하여 이러한 문제를 해결해야 합니다. **새로운 평가 패러다임**과 **인간 중심 평가 도구 키트**의 개발은 LLM 에이전트의 전반적인 성능 향상에 중요한 역할을 할 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.09645/x2.png)

> 🔼 평가 에이전트 프레임워크는 두 단계로 작동합니다. (a) 제안 단계: 사용자 쿼리를 하위 측면으로 분해하고 프롬프트를 생성합니다. (b) 실행 단계: 시각적 콘텐츠를 생성하고 평가 툴킷을 사용하여 평가합니다. 이 두 단계는 사용자 쿼리를 기반으로 모델을 동적으로 평가하기 위해 반복적으로 상호 작용합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Overview of Evaluation Agent Framework. This framework leverages LLM-powered agents for efficient and flexible visual model assessments. As shown, it consists of two stages: (a) the Proposal Stage, where user queries are decomposed into sub-aspects, and prompts are generated, and (b) the Execution Stage, where visual content is generated and evaluated using an Evaluation Toolkit. The two stages interact iteratively to dynamically assess models based on user queries.
> </details>



![](https://arxiv.org/html/2412.09645/extracted/6071683/figures/fig_prompts_abl.png)

> 🔼 이 그림은 VBench 벤치마크에서 특정 기능 차원(예: Human Action, Scene, Color, Object Class)에 대한 평가 결과를 비교하여 평가 에이전트의 성능을 검증한 결과를 보여줍니다. 각 모델과 차원에 대해 두 세트의 막대가 표시되는데, 밝은 막대는 원래 설정(적은 수의 프롬프트)을 사용한 결과를, 어두운 막대는 프롬프트 수를 늘린 후의 결과를 나타냅니다. 각 막대에서 해칭된 부분은 정확한 범위 내의 예측을 나타내고, 채워진 부분은 한 범위의 오차 범위 내의 예측을 나타냅니다. 프롬프트 수를 늘리면 전반적으로 정확도가 향상됨을 알 수 있습니다. 자세한 수치 결과는 표 6에 제공됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Validation on VBench Percentage Dimensions. We conducted additional validation experiments on VBench by increasing the number of prompts in each evaluation. For each model and dimension, lighter bars represent results with the original settings, darker bars with increased sample size. Hatched portions indicate predictions within the exact range, and solid portions within an error margin of one range. Specific numerical results are provided in Table 6
> </details>



![](https://arxiv.org/html/2412.09645/x3.png)

> 🔼 이 그림은 사용자의 질문 '모델이 원본 스타일을 유지하면서 기존 아트워크의 변형을 생성할 수 있습니까?'에 대해 평가 에이전트가 어떻게 단계적으로 모델의 능력을 평가하는지 보여줍니다. 각 단계마다 하위 측면, 생각, 샘플 이미지, 질문 및 답변, 프롬프트가 자세히 설명되어 있습니다. 평가 에이전트는 기본적인 예술 스타일 복제부터 시작하여 세부 지향적인 아트워크의 스타일 일관성, 다양한 스타일의 혼합, 그리고 마지막으로 여러 문화 예술 스타일 통합이라는 복잡한 작업까지 탐구합니다. 각 단계는 이전 단계의 결과를 바탕으로 모델의 기능에 대한 심층적인 분석과 요약을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: A Case of Open-Ended User Query Evaluation. For open-ended user queries, the Evaluation Agent systematically explores the model’s capabilities in specific areas, starting from basic aspects and gradually delving deeper, culminating in a detailed analysis and summary. Please refer to the Appendix E.2 for the complete results.
> </details>



![](https://arxiv.org/html/2412.09645/extracted/6071683/figures/open_dataset_stats.png)

> 🔼 이 그림은 논문에서 생성된 Open-Ended User Query Dataset의 데이터 분포를 세 가지 측면(일반/구체적, 능력, 특정 도메인)에서 분석한 결과를 보여줍니다. 데이터셋은 이러한 차원에서 비교적 균형 잡힌 분포를 보입니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Data Distribution of Open-Ended User Query Dataset. We analyze the constructed open-ended user query dataset from three aspects: General/Specific, Ability, and Specific Domain. The results indicate that our dataset exhibits a relatively balanced distribution across these dimensions.
> </details>



![](https://arxiv.org/html/2412.09645/extracted/6071683/figures/fig_performance_ind.png)

> 🔼 이 그림은 다양한 백본 모델(GPT-40 및 Claude 포함)의 VBench 벤치마크 각 차원에 대한 성능 비교를 시각적으로 보여줍니다. 각 차원에 대한 정확한 예측 범위(빗금 표시)와 오차 범위 내 예측(채워진 막대)이 표시됩니다. 자세한 수치 결과는 표 C.2와 표 8에 나와 있습니다. 이 시각화를 통해 서로 다른 모델들의 강점과 약점을 비교하여 각 모델이 어떤 측면에서 뛰어난지 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Performance Comparison across VBench Dimensions for Different Base Models. This visualization highlights the performance of all backbone models, including GPT-4o and Claude models, providing a comprehensive comparison in each dimension for different backbone models. Hatched portions indicate predictions within the exact range, and solid portions within an error margin of one range. Specific numerical results are provided in Table C.2 and Table 8
> </details>



![](https://arxiv.org/html/2412.09645/x4.png)

> 🔼 Gemini 모델은 평가 도구 선택에 있어 잦은 오류를 보였습니다. 그림에서 보이는 예시와 같이, '모델의 미적 측면에서의 성능은 어떠한가?'라는 질문에 '주제 일관성' 도구를 선택하는 오류를 범했습니다. 정확한 평가를 위해서는 '미적 품질' 도구를 사용했어야 합니다. 이러한 잘못된 도구 선택은 이후 평가의 정확성을 떨어뜨리는 결과를 초래했습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: A Common Failure Pattern in Tool Selection. As shown in the figure, Gemini frequently selected an incorrect tool for evaluation. In this case, the model should have selected the “Aesthetic Quality” tool, but it incorrectly chose “Subject Consistency,” leading to inaccuracies in subsequent assessments.
> </details>



![](https://arxiv.org/html/2412.09645/x5.png)

> 🔼 이 그림은 Gemini 모델을 기반으로 하는 평가 에이전트가 새로운 하위 측면을 제안하고 최종 응답을 완료하는 데 있어 두 가지 중요한 실패 사례를 보여줍니다. 첫째, Gemini는 이전 라운드의 관찰 결과를 바탕으로 새로운 하위 측면을 제안하지 못하고 제공된 지침을 엄격하게 준수하지 않고 반복적이고 의미 없는 루프에 빠집니다. 둘째, 이러한 반복적인 동작은 멈추지 않는 루프로 이어져 결국 사용자 쿼리에 대한 의미 있는 최종 응답을 생성하지 못합니다. 그림에서 첫 번째 실패는 두 번째 질문에서 Agent가 첫 번째 질문과 동일한 하위 측면과 생각을 제안하는 것을 보여줍니다. 또한 프레임워크 프로토콜에 의해 중지될 때까지 Agent는 동일한 응답을 반복합니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Common Failures in Generating Sub-Aspects and Finalizing Responses. The figure highlights two critical failures: first, Gemini fails to propose new sub-aspects based on observations from previous rounds, instead engaging in repetitive and meaningless loops without strictly adhering to the provided instructions. Second, this repetitive behavior leads to a non-stopping loop, ultimately failing to generate a meaningful final response to the user’s query.
> </details>



![](https://arxiv.org/html/2412.09645/x6.png)

> 🔼 이 그림은 사용자의 질의 '모델이 기존 작품의 변형을 생성하면서 원래 스타일을 유지할 수 있습니까?'에 대한 평가 에이전트의 응답을 보여주는 예시입니다. 평가 에이전트는 여러 단계에 걸쳐 모델의 능력을 평가합니다. 먼저 기본적인 예술 스타일 복제 능력을 평가한 후, 세부 사항이 중요한 작품에서 스타일 일관성 유지 능력을 평가합니다. 마지막으로, 기존 미적을 유지하면서 새로운 요소를 도입하고 여러 문화적 예술 스타일을 통합하는 능력을 평가합니다. 각 단계마다 생성된 이미지, 질문, 답변이 제시되어 있으며, 최종적으로는 모델의 능력에 대한 분석 및 요약을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: A Case of Open-Ended User Query Evaluation. This figure illustrates the Evaluation Agent’s response to the user query, “Can the model generate variations of existing artwork while maintaining the original style?”
> </details>



![](https://arxiv.org/html/2412.09645/x7.png)

> 🔼 이 그림은 사용자가 '사용자가 객체 관계를 얼마나 정확하게 지정할 수 있습니까?'라는 질문에 대해 평가 에이전트가 어떻게 응답하는지 보여주는 예시입니다. 에이전트는 먼저 간단한 두 객체의 공간적 관계(''고양이가 매트 위에 앉아 있다''와 같이)를 평가하여 모델의 기본적인 객체 배열 해석 능력을 확인합니다. 그런 다음 세 개 이상의 객체를 포함하는 더 복잡한 관계(''고양이가 테이블 아래에 누워 있는 개 옆에 있는 매트 위에 앉아 있다''와 같이)로 진행하여 모델이 여러 관계를 동시에 정확하게 유지할 수 있는지 여부를 평가합니다. 추가적으로, 에이전트는 '투명한 정육면체 안에 있는 고양이와 그 주위를 맴도는 개'와 같이 추상적이거나 덜 일반적인 공간적 관계를 탐색하여 덜 틀에 박힌 장면을 나타내는 모델의 능력을 테스트합니다. 마지막으로, 에이전트는 '나무가 거꾸로 자라고 고양이는 나무 꼭대기(바닥)에 누워 있다'와 같이 표준적이지 않거나 상상력이 풍부한 시나리오를 포함하는 객체 관계를 처리하는 모델의 능력을 평가하여 초현실적이거나 비표준적인 객체 관계를 해석하는 데 있어 모델의 한계를 더 자세히 조사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: A Case of Open-Ended User Query Evaluation. This figure illustrates the Evaluation Agent’s response to the user query, “How precisely can the user specify object relationships?”
> </details>



![](https://arxiv.org/html/2412.09645/x8.png)

> 🔼 이 그림은 사용자 쿼리 '모델이 특정 개수의 객체를 얼마나 잘 생성할 수 있습니까?'에 대한 평가 에이전트의 응답을 보여줍니다. 평가 에이전트는 객체의 종류(사과, 장미, 백합 등), 개수, 배열 및 배경과 같은 다양한 하위 측면을 테스트하여 모델의 기능을 평가합니다. 각 하위 측면에 대해 생성된 이미지, 관련 질문 및 답변과 함께 단계별 평가 프로세스가 표시됩니다. 마지막으로 에이전트는 모델이 요청된 대로 특정 개수의 객체를 생성하는 데 상당한 제한이 있음을 보여주는 종합적인 분석 및 요약을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: A Case of Open-Ended User Query Evaluation. This figure illustrates the Evaluation Agent’s response to the user query, “How well the model can generate a specific number of objects?”
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Models | Subject | Background | Motion | Dynamic | Aesthetic | Imaging | Object | Class |
|---|---|---|---|---|---|---|---|---| 
| Consistency | **Subject** | | | | | | | |
| Consistency | **Background** | | | | | | | |
| Consistency | **Motion** | | | | | | | |
| Smoothness | **Dynamic** | | | | | | | | 
| Degree | **Aesthetic** | | | | | | | |
| Quality | **Imaging** | | | | | | | |
| Quality | **Object** | | | | | | | |
| Class |  | | | | | | | |
| Latte-1 <cite class="ltx_cite ltx_citemacro_cite">Ma et al. (2024)</cite> | 50% / 80% | 0% / 30% | 40% / 70% | 30% / 70% | 60% / 100% | 70% / 100% | 40% / 50% | |
| ModelScope <cite class="ltx_cite ltx_centering ltx_citemacro_cite">Wang et al. (2023)</cite> | 80% / 80% | 80% / 90% | 60% / 80% | 60% / 100% | 60% / 100% | 100% / 100% | 0% / 50% | |
| VideoCrafter-0.9 <cite class="ltx_cite ltx_centering ltx_citemacro_cite">He et al. (2022)</cite> | 100% / 100% | 80% / 100% | 70% / 100% | 80% / 100% | 90% / 100% | 20% / 100% | 20% / 60% | |
| VideoCrafter-2 <cite class="ltx_cite ltx_centering ltx_citemacro_cite">Chen et al. (2024a)</cite> | 10% / 100% | 60% / 100% | 30% / 90% | 30% / 80% | 80% / 100% | 50% / 100% | 70% / 100% | |{{< /table-caption >}}
> 🔼 Evaluation Agent의 평가 결과를 VBench 벤치마크와 비교한 표입니다. 15개의 특정 능력 차원에서 비디오 생성 모델을 평가하고, 정확도 측면에서 VBench 결과와 비교했습니다. 표의 숫자는 Evaluation Agent의 정확한 예측 비율(왼쪽)과 오차 범위 내 예측 비율(오른쪽)을 나타냅니다. 10번의 시도에 따른 결과입니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Evaluation Results Comparison with VBench Huang et al. (2024a). We evaluated 15 specific ability dimensions in VBench using our Evaluation Agent and compared its results against VBench in terms of conclusion accuracy. The numerical results show the percentages of the Evaluation Agent’s correct predictions falling either within the exact range (left) or within an error margin of one range (right) across ten trials.
> </details>

{{< table-caption >}}
| Multiple Objects | Human | Spatial | Scene | Temporal | Overall | Consistency |  |
|---|---|---|---|---|---|---|---| 
| Objects | **Human** |  |  |  |  |  |  |
| Action | **Color** | **Spatial** |  |  |  |  |  |
| Relationship | **Scene** | **Appearance** |  |  |  |  |  |
| Style | **Temporal** |  |  |  |  |  |  |
| Style | **Overall** |  |  |  |  |  |  |
| Consistency |  |  |  |  |  |  |  |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 40% / 100% | 10% / 10% | 30% / 70% | 10% / 80% | 20% / 40% | 70% / 90% | 40% / 100% | 70% / 100% |
| 50% / 100% | 10% / 40% | 0% / 20% | 10% / 30% | 20% / 100% | 90% / 100% | 50% / 90% | 20% / 100% |
| 80% / 100% | 10% / 30% | 10% / 40% | 20% / 100% | 30% / 100% | 60% / 100% | 80% / 100% | 0% / 80% |
| 20% / 60% | 10% / 90% | 90% / 100% | 0% / 70% | 0% / 10% | 80% / 100% | 80% / 100% | 60% / 100% |
| --- |  |  |  |  |  |  |  |{{< /table-caption >}}
> 🔼 표 3은 평가 에이전트와 T2I-CompBench의 결과 비교를 보여줍니다. 평가 에이전트는 T2I-CompBench의 4가지 능력 차원을 평가하고 결론 정확도 측면에서 T2I-CompBench의 결과와 비교합니다. 숫자 결과는 10회 시행에서 평가 에이전트의 정확한 예측이 정확한 범위(왼쪽) 또는 한 범위의 오차 범위(오른쪽) 내에 속하는 비율을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Evaluation Results Comparison with T2I-CompBench Huang et al. (2023). We evaluated four ability dimensions in T2I-CompBench using our Evaluation Agent and compared its results with those of T2I-CompBench in terms of conclusion accuracy. The numerical results show the percentages of the Evaluation Agent’s correct predictions falling either within the exact range (left) or within an error margin of one range (right) across ten trials.
> </details>

{{< table-caption >}}
| Models | Color | Shape | Texture | Non-Spatial |
|---|---|---|---|---| 
| --- | --- | --- | --- | --- |
| SD1.4 Rombach et al. (2022) | 50% / 100% | 100% / 100% | 0% / 100% | 50% / 100% |
| SD2.1 Rombach et al. (2022) | 100% / 100% | 60% / 100% | 80% / 100% | 60% / 100% |
| SDXL Podell et al. (2023) | 100% / 100% | 20% / 100% | 80% / 100% | 60% / 100% |
| SD3.0 Esser et al. (2024) | 20% / 90% | 0% / 90% | 0% / 70% | 80% / 90% |{{< /table-caption >}}
> 🔼 VBench 벤치마크에서 4가지 모델(Latte-1, ModelScope, VideoCrafter-0.9, VideoCrafter-2)에 대한 기존 평가 방식과 제안된 평가 에이전트 방식의 평가 시간 및 샘플 수를 비교한 표입니다. 평가 에이전트를 사용하면 평가 시간이 10배 이상 단축되고 필요한 샘플 수도 크게 줄어듭니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Time Cost Comparison across Models for VBench Dimensions. This table compares the evaluation time of four different models using the original VBench pipelines versus the Evaluation Agent. The Evaluation Agent significantly reduces the overall evaluation time.
> </details>

{{< table-caption >}}
| Models | VBench (Total Cost) ↓ | VBench (Avg. Cost per Dimension) ↓ | Evaluation Agent (Ours) ↓ |
|---|---|---|---|
| Latte-1 Ma et al. (2024) | 2557 min, 4355 samples | 170 min, 290 samples | 15 min, 25 samples |
| ModelScope Wang et al. (2023) | 1160 min, 4355 samples | 77 min, 290 samples | 6 min, 23 samples |
| VideoCrafter-0.9 He et al. (2022) | 1459 min, 4355 samples | 97 min, 290 samples | 9 min, 24 samples |
| VideoCrafter-2 Chen et al. (2024a) | 4261 min, 4355 samples | 284 min, 290 samples | 24 min, 23 samples |{{< /table-caption >}}
> 🔼 이 표는 T2I-CompBench 벤치마크의 여러 차원에서 4가지 모델을 평가하는 데 필요한 비용을 기존 T2I-CompBench 파이프라인과 제안된 평가 에이전트를 사용하여 비교합니다. 평가 에이전트는 기존 방식에 비해 평가 시간을 크게 단축합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Time Cost Comparison across Models for T2I-CompBench Dimensions. This table compares the evaluation costs for assessing four models across T2I-CompBench dimensions using both the original T2I-CompBench pipelines and our Evaluation Agent. The Evaluation Agent achieves a substantial reduction in evaluation time compared to the traditional pipelines.
> </details>

{{< table-caption >}}
| Models | T2I-Comp (Total Cost) ↓ | T2I-Comp (Avg. Cost per Dimension) ↓ | Evaluation Agent (Ours) ↓ |
|---|---|---|---| 
| SD1.4 Rombach et al. (2022) | 563 min, 12000 samples | 141 min, 3000 samples | 5 min, 26 samples |
| SD2.1 Rombach et al. (2022) | 782 min, 12000 samples | 196 min, 3000 samples | 6 min, 26 samples |
| SDXL Podell et al. (2023) | 1543 min, 12000 samples | 386 min, 3000 samples | 8 min, 26 samples |
| SD3.0 Esser et al. (2024) | 1410 min, 12000 samples | 353 min, 3000 samples | 7 min, 25 samples |{{< /table-caption >}}
> 🔼 이 표는 VBench 벤치마크의 백분율 기반 차원에 대한 평가 에이전트의 성능을 보여줍니다. 10회 시행에서 정확한 범위(왼쪽) 또는 오차 범위 하나(오른쪽) 내에 속하는 예측 비율을 표시합니다. 즉, 에이전트가 VBench의 결과와 얼마나 일치하는지를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Validation on VBench Percentage Dimensions. The numerical results show the percentages of the Evaluation Agent’s correct predictions falling either within the exact range (left) or within an error margin of one range (right) across ten trials.
> </details>

{{< table-caption >}}
| Models | Human | | | |
|---|---|---|---|---| 
| | Scene | Color | Object | |
| | | | Class | |
| --- | --- | --- | --- | --- |
| Latte-1 (default) [Ma et al. (2024)](https://arxiv.org/html/2412.09645v2#bib.bib21) | 10% / 10% | 20% / 40% | 30% / 70% | 40% / 50% |
| Latte-1 (30 prompts) [Ma et al. (2024)](https://arxiv.org/html/2412.09645v2#bib.bib21) | 10% / 60% | 30% / 50% | 30% / 70% | 40% / 80% |
| ModelScope (default) [Wang et al. (2023)](https://arxiv.org/html/2412.09645v2#bib.bib33) | 10% / 40% | 20% / 100% | 0% / 20% | 0% / 50% |
| ModelScope (30 prompts) [Wang et al. (2023)](https://arxiv.org/html/2412.09645v2#bib.bib33) | 30% / 50% | 30% / 100% | 10% / 30% | 10% / 60% |{{< /table-caption >}}
> 🔼 이 표는 Claude를 기반 모델로 사용하여 VBench 벤치마크에서 비디오 생성 모델을 평가한 결과를 보여줍니다. 계획 및 추론 에이전트의 백본으로 claude-3-5-sonnet-20241022를 사용하여 다양한 측면(주제 일관성, 배경 일관성, 모션 부드러움 등)에서 모델 성능을 평가했습니다. 표에는 각 모델에 대한 평가 결과가 요약되어 있으며, 주요 실험에서와 동일한 실험 설정 및 매개변수를 사용했음을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Evaluation Results Comparison with VBench Huang et al. (2024a) using Claude as Base Model. We adhere to the same experimental settings and parameters as in the main experiments, but we replace the planning and reasoning agents’ backbones with claude-3-5-sonnet-20241022 as the base model.
> </details>

{{< table-caption >}}
| Models | Subject | Background | Motion | Dynamic | Aesthetic | Imaging | Object | Class |
|---|---|---|---|---|---|---|---|---| 
| Consistency | **Models** | | | | | | | |
| Consistency | **Background** | | | | | | | |
| Consistency | **Motion** | | | | | | | |
| Smoothness | **Dynamic** | | | | | | | |
| Degree | **Aesthetic** | | | | | | | |
| Quality | **Imaging** | | | | | | | |
| Quality | **Object** | | | | | | | |
| Class |  | | | | | | | |
| Latte-1 <cite class="ltx_cite ltx_citemacro_cite">Ma et al. (2024)</cite> | 0% / 10% | 0% / 10% | 0% / 30% | 0% / 40% | 100% / 100% | 90% / 100% | 0% / 30% | |
| ModelScope <cite class="ltx_cite ltx_centering ltx_citemacro_cite">Wang et al. (2023)</cite> | 0% / 10% | 30% / 40% | 10% / 80% | 30% / 100% | 40% / 100% | 60% / 100% | 20% / 50% | |
| VideoCrafter-0.9 <cite class="ltx_cite ltx_centering ltx_citemacro_cite">He et al. (2022)</cite> | 40% / 100% | 30% / 80% | 40% / 90% | 90% / 100% | 90% / 100% | 20% / 100% | 10% / 40% | |
| VideoCrafter-2 <cite class="ltx_cite ltx_centering ltx_citemacro_cite">Chen et al. (2024a)</cite> | 50% / 100% | 0% / 100% | 0% / 10% | 60% / 100% | 100% / 100% | 80% / 100% | 60% / 90% | |{{< /table-caption >}}
> 🔼 표 8은 Claude를 기본 모델로 사용하여 T2I-CompBench(Huang et al., 2023)와 비교한 평가 결과를 보여줍니다. 계획 및 추론 에이전트의 백본을 claude-3-5-sonnet-20241022로 변경한 것을 제외하고는 본 논문의 주요 실험과 동일한 실험 설정 및 매개변수를 따랐습니다. 이 표는 색상 바인딩, 모양 바인딩, 질감 바인딩, 비공간적 관계의 네 가지 능력 차원에 대한 평가 결과를 보여주며, 각 모델에 대해 정확한 범위(왼쪽) 또는 하나의 범위 오차 범위(오른쪽) 내에 속하는 Evaluation Agent의 정확한 예측 비율(10회 시행 평균)을 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Evaluation Results Comparison with T2I-CompBench Huang et al. (2023) using Claude as Base Model. We follow the same experimental setting and the parameters in the main experiments but changing the planning and reasoning agent’s backbones with claude-3-5-sonnet-20241022 as the base model.
> </details>

{{< table-caption >}}
| Multiple Objects | Human | Spatial | Scene | Temporal | Overall | Consistency | 
|---|---|---|---|---|---|---| 
| --- | **Human** | | **Color** | | | | 
| Objects | | **Spatial** | | | | | 
| Action | **Color** | | **Scene** | | | | 
| Relationship | **Scene** | **Appearance** | | | | | 
| Style | **Temporal** | | | | | | 
| Style | **Overall** | | | | | | 
| Consistency | | | | | | | 
| 10% / 60% | 60% / 70% | 10% / 60% | 30% / 80% | 0% / 40% | 30% / 100% | 80% / 100% | 80% / 100% | 
| 90% / 100% | 40% / 90% | 10% / 20% | 50% / 80% | 40% / 100% | 70% / 100% | 90% / 100% | 40% / 100% | 
| 0% / 40% | 20% / 40% | 10% / 40% | 40% / 100% | 10% / 80% | 100% / 100% | 90% / 100% | 60% / 100% | 
| 50% / 100% | 50% / 80% | 60% / 90% | 50% / 100% | 0% / 50% | 10% / 100% | 80% / 100% | 80% / 100% |{{< /table-caption >}}
> 🔼 VBench 벤치마크에서 Claude를 기본 모델로 사용하여 여러 모델의 평가 시간을 비교한 표입니다. 원본 VBench 파이프라인과 평가 에이전트를 사용한 결과를 비교하여 평가 에이전트가 전체 평가 시간을 크게 단축함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Time Cost Comparison across Models for VBench Huang et al. (2024a) Dimensions using Claude as Base Model. This table compares the evaluation time of four different models using the original VBench pipelines versus the Evaluation Agent. The Evaluation Agent significantly reduces the overall evaluation time.
> </details>

{{< table-caption >}}
| Models | Color | Shape | Texture | Non-Spatial |
|---|---|---|---|---| 
| SD1.4 Rombach et al. (2022) | 80% / 100% | 70% / 100% | 80% / 100% | 70% / 100% |
| SD2.1 Rombach et al. (2022) | 80% / 100% | 30% / 100% | 60% / 100% | 70% / 100% |
| SDXL Podell et al. (2023) | 90% / 100% | 60% / 100% | 70% / 100% | 30% / 100% |
| SD3.0 Esser et al. (2024) | 10% / 100% | 20% / 100% | 30% / 100% | 20% / 100% |{{< /table-caption >}}
> 🔼 T2I-CompBench 벤치마크에서 Claude를 기본 모델로 사용하여 4가지 모델을 평가하는 데 드는 비용을 비교합니다. 원래 T2I-CompBench 파이프라인과 제안된 평가 에이전트를 모두 사용하여 비교합니다. 평가 에이전트는 기존 방식에 비해 평가 시간을 크게 단축합니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Time Cost Comparison across Models for T2I-CompBench Huang et al. (2023) Dimensions using Claude as Base Model. This table compares the evaluation costs for assessing four models across T2I-CompBench dimensions using both the original T2I-CompBench pipelines and our Evaluation Agent. The Evaluation Agent achieves a substantial reduction in evaluation time compared to the traditional pipelines.
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