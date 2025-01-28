---
title: "RealCritic: Towards Effectiveness-Driven Evaluation of Language Model Critiques"
summary: "RealCritic: LLM의 비판 능력을 효과적으로 평가하는 새로운 벤치마크"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 The Chinese University of Hong Kong, Shenzhen",]
showSummary: true
date: 2025-01-24
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.14492 {{< /keyword >}}
{{< keyword icon="writer" >}} Zhengyang Tang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-27 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.14492" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.14492" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/realcritic-towards-effectiveness-driven" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)의 성능 향상에 있어서 비판 능력은 매우 중요합니다. 하지만 기존의 LLM 평가 방식은 개방형 루프 방식으로, 비판의 질적 측면을 제대로 평가하지 못하는 한계가 있었습니다. 본 논문에서는 LLM의 비판 능력을 효과적으로 평가하기 위한 새로운 벤치마크인 RealCritic을 제시합니다. RealCritic은 폐쇄형 루프 방식을 채택하여, 비판에 따른 수정 결과의 질을 평가함으로써 비판의 효과를 직접적으로 측정합니다.

RealCritic은 자기 비판, 상호 비판, 반복 비판 등 다양한 비판 시나리오를 포함하고 있으며, 8가지 어려운 추론 과제를 활용하여 벤치마크를 구현합니다. 실험 결과, 기존의 LLM 모델들은 고급 추론 기반 모델에 비해 비판 능력이 현저히 떨어지는 것으로 나타났습니다. 특히 자기 비판 및 반복 비판 시나리오에서는 기존 모델의 성능이 기저 성능보다 낮은 경우도 있었습니다.  본 논문은 LLM의 비판 능력 향상에 기여할 뿐만 아니라, 향후 연구 방향을 제시하는 데 큰 의의가 있습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} LLM의 자기 비판 및 상호 비판 능력을 효과적으로 평가하는 새로운 벤치마크 RealCritic 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} RealCritic을 사용한 다양한 LLM 모델의 비판 능력 비교 분석 결과 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} LLM의 비판 능력 향상을 위한 향후 연구 방향 제시 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **LLM의 비판 능력 평가를 위한 새로운 벤치마크인 RealCritic**을 제시하여, LLM의 자기 비판 및 상호 비판 능력을 효과적으로 평가하는 방법을 제시합니다. 이는 **LLM의 성능 향상**에 중요한 기여를 할 뿐만 아니라, **향후 연구 방향**을 제시하는 데에도 큰 의미가 있습니다.  본 연구는 **다양한 LLM 모델의 비판 능력을 비교 분석**하여 각 모델의 강점과 약점을 파악하고, **향후 LLM 개발에 필요한 방향**을 제시합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.14492/x1.png)

> 🔼 그림 1은 다양한 언어 모델의 자기 비판 및 상호 비판 능력에 대한 벤치마크 결과를 보여줍니다.  자기 비판 과제에서는 01-mini 모델만 성능 향상을 보였고, 상호 비판 과제에서는 01-mini 모델이 가장 큰 성능 향상을 보였습니다. 이는 고전적인 언어 모델과 추론 기반의 고급 언어 모델 간의 명확한 차이를 보여줍니다.  01-mini 모델은 자기 비판 과제와 상호 비판 과제 모두에서 우수한 성능을 보여주어 추론 능력의 중요성을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Caption
> </details>





{{< table-caption >}}
| Benchmark | Output Format | Critique Type | Evaluation Method | Iterative Support | Human Anno. | Test Data Size | Public Release |
|---|---|---|---|---|---|---|---| 
| CriticBench-Google | C+V | Self+Cross | Verdict Judging | ✗ | ✗ | 0 | ✗ |
| CriticBench-THU | C+V | Cross | Verdict Judging | ✗ | ✓ | 3,825 | ✓ |
| CriticEval | C+S | Cross | Score Judging | ✗ | ✗ | 3,608 | ✓ |
| Shepherd | C | Cross | GPT-4 Comparison | ✗ | ✗ | 352 | ✗ |
| Auto-J | C | Cross | GPT-4 Comparison | ✗ | ✗ | 232 | ✓ |
| **RealCritic** | C+V+Corr | Self+Cross | Correction Matching | ✓ | ✗ | 2,093 | ✓ |
| Note: C = Critique, V = Verdict, S = Score, Corr = Correction. ✓= Yes, ✗ = No. |  |  |  |  |  |  | {{< /table-caption >}}

> 🔼 표 1은 기존의 비평 평가 방식들과 본 논문에서 제시하는 RealCritic 프레임워크를 비교 분석한 표입니다. RealCritic은 기존 방식들의 한계를 극복하고, 대규모 공개 벤치마크를 제공하여 포괄적인 비평 능력 평가를 가능하게 합니다. 표에는 데이터셋, 출력 형식, 비평 유형, 평가 방식, 반복 지원 여부, 테스트 데이터 크기, 공개 여부 등의 정보가 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparison of critique evaluation approaches. Our RealCritic framework introduces several key innovations while providing a large-scale, publicly available benchmark for comprehensive critique ability evaluation.
> </details>





### In-depth insights


#### Critique Benchmark
본 논문에서 제시된 평가 프레임워크의 핵심은 **실효성 기반 평가**입니다. 기존의 오픈루프 방식 평가와 달리, **클로즈드루프 방식**을 통해 비판의 질을 측정합니다. 즉, 비판에 따른 수정된 결과물의 질을 통해 비판의 질을 평가하는 것입니다. 이는 **LLM의 자기 개선 능력**을 직접적으로 측정하는 데 초점을 맞추고 있으며, **실제적인 개선 효과**를 중시하는 점이 특징입니다.  **자기 비판, 교차 비판, 반복 비판** 등 다양한 시나리오를 포함하여 LLM의 비판 능력을 종합적으로 평가하며, 특히 **추론 기반 LLM의 고유한 능력**을 평가하기 위한 설계가 돋보입니다.  이러한 접근 방식은 기존 비판 벤치마크의 한계를 극복하고, LLM의 비판 능력에 대한 더욱 정확하고 심도있는 평가를 가능하게 할 것으로 예상됩니다.

#### Closed-Loop Eval
**폐쇄 루프 평가(Closed-Loop Eval)**는 인공지능 모델의 성능을 평가하는 새로운 방식으로, 모델의 출력을 단순히 정답과 비교하는 기존의 오픈 루프 방식과는 다릅니다. **모델의 출력이 다시 모델의 입력으로 재사용**되어, 모델이 스스로 자신의 출력을 개선하고 학습하는 과정을 평가합니다. 이는 **모델의 자기 개선 능력**과 **실제 응용 환경에서의 성능**을 보다 정확하게 측정할 수 있게 합니다.  기존 방식은 정답 여부만 판단하지만, 폐쇄 루프 평가는 **개선 과정의 질적 측면**까지 고려하여, 모델이 어떻게 오류를 수정하고 성능을 향상시키는지를 분석합니다.  특히 **반복적인 피드백 루프**를 통해 모델의 장기적인 학습 효과를 평가할 수 있으며, **다양한 유형의 오류 수정 능력**을 종합적으로 평가할 수 있습니다. 따라서 폐쇄 루프 평가는 모델의 지능 수준을 더욱 정확하게 평가하는 데 유용하며, 향후 AI 모델 개발에 중요한 지표가 될 것입니다.

#### Critique Paradigms
본 논문에서 제시된 평가 프레임워크는 **자기 비판, 교차 비판, 반복 비판**이라는 세 가지 주요 패러다임을 통해 언어 모델의 비판 능력을 평가합니다.  **자기 비판**은 모델이 스스로 생성한 답변을 평가하는 능력을 측정하는 반면, **교차 비판**은 다른 모델이 생성한 답변을 평가하는 능력을 평가합니다.  **반복 비판**은 모델이 여러 번 반복하여 답변을 개선하는 능력을 평가하는 데 초점을 맞춥니다. 이러한 세 가지 패러다임은 각각 언어 모델의 다양한 측면을 평가하며, 모델의 비판 능력을 포괄적으로 이해하는 데 중요한 역할을 합니다.  특히, **반복 비판**은 고차원 추론 능력과 지속적인 학습 능력을 측정하기 때문에, **고급 언어 모델의 성능을 차별화**하는 데 중요한 지표가 될 수 있습니다.  각 패러다임의 성능을 비교 분석하여 언어 모델의 강점과 약점을 파악하고, 향후 모델 개발 방향을 제시하는 데 활용될 수 있습니다.

#### Iterative Critique
반복적인 비평(Iterative Critique)은 **대규모 언어 모델(LLM)**의 성능 향상을 위한 중요한 전략입니다. 이는 단순히 한 번의 수정으로 끝나는 것이 아니라, **수정 과정을 반복**하여 점진적으로 개선해 나가는 방식입니다.  **LLM이 스스로 생성한 답변에 대한 비평을 반복**함으로써, LLM은 **자체적인 오류를 파악하고 수정하는 능력**을 향상시킬 수 있습니다. 또한, **다른 모델의 답변에 대한 비평을 반복**하는 과정을 통해, LLM은 **다양한 관점과 해결 방식**을 이해하고 더욱 효과적인 비평을 수행할 수 있게 됩니다.  **반복적인 비평은 LLM의 장기적인 추론 능력**을 평가하는 데 유용한 지표이며, **모델의 적응력과 문제 해결 능력**을 보여주는 중요한 요소입니다.  하지만, **무분별한 반복은 오히려 성능 저하**를 초래할 수 있으므로, **적절한 제어 메커니즘**이 필요합니다. 따라서, 효과적인 반복적 비평 전략을 수립하는 것이 LLM의 발전에 필수적입니다.

#### Dataset Creation
본 논문에서 데이터셋 생성에 대한 심도있는 논의는 **다양한 기존 벤치마크의 한계점을 명확히 제시**하는 데서 시작됩니다.  기존 연구들은 **개방 루프 방식**을 주로 사용하여 비판 능력의 질을 측정하는 데 어려움을 겪었으며, **단일 지표에 의존**하는 경향이 있었습니다. 이러한 한계를 극복하기 위해, **실제적인 문제 해결 능력을 평가하는 폐쇄 루프 방식**의 새로운 벤치마크를 제안합니다.  **다양한 유형의 질문과 난이도**를 포괄하는 문제들을 수집하고, 여러 모델의 솔루션을 생성하여 솔루션의 정확성과 비판의 효과를 종합적으로 평가합니다. 특히, **자기 비판과 교차 비판, 반복 비판** 등의 고급 추론 능력 평가를 위한 다양한 시나리오를 포함하는 것이 핵심입니다.  **데이터셋의 질을 보장**하기 위한 다단계 검증 절차 및 인간 평가자에 의한 검증 결과 또한 제시되어,  **데이터셋의 신뢰성**을 강조합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.14492/x2.png)

> 🔼 그림 2는 CriticBench의 한계를 보여주는 예시입니다. CriticBench는 입력 솔루션의 정확도를 기반으로 평가를 하기 때문에, 솔루션의 정확도를 올바르게 예측하더라도 실제로는 질이 낮은 비평을 높은 품질의 비평으로 잘못 분류할 수 있습니다. 반면 RealCritic은 개선된 솔루션 생성에 미치는 영향을 바탕으로 비평의 질을 정확하게 평가합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: TODO.
> </details>



![](https://arxiv.org/html/2501.14492/x3.png)

> 🔼 그림 3은 논문의 평가 프레임워크를 보여줍니다.  CriticBench와 RealCritic의 평가 방법을 비교하여 보여줍니다. CriticBench는 오픈 루프 방식으로, 비판의 질을 솔루션의 정확성 예측에 따라 평가합니다. 반면 RealCritic은 클로즈드 루프 방식으로, 비판의 질을 비판에 따른 수정된 솔루션의 질을 바탕으로 평가합니다.  RealCritic은 CriticBench에 비해 솔루션 개선에 미치는 비판의 효과를 직접적으로 측정하는 방식으로, 보다 종합적인 평가를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Caption.
> </details>



![](https://arxiv.org/html/2501.14492/x4.png)

> 🔼 그림 4는 논문의 데이터 수집 과정을 보여줍니다. 이 과정은 크게 두 단계로 나뉩니다. 첫 번째 단계는 다양한 작업에서 질문을 수집하는 것이고, 두 번째 단계는 여러 모델을 사용하여 이러한 질문에 대한 답을 생성하는 것입니다. 수집된 질문과 답변은 모두 LLM의 비판 능력을 평가하는 데 사용됩니다.  데이터 수집 과정에 대한 자세한 설명은 4단계로 이루어져 있으며, 각 단계마다 구체적인 내용을 확인할 수 있습니다. 먼저 후보 데이터 세트를 선택하고, 모델 풀을 생성하고, 모든 모델에 대한 모든 데이터 세트의 솔루션을 생성하고, 마지막으로 모델의 능력에 따라 필터링합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Caption
> </details>



![](https://arxiv.org/html/2501.14492/x5.png)

> 🔼 그림 5는 자기 비판과 교차 비판 시나리오에서 I→C와 C→I의 성능을 보여줍니다. 여기서 'C'는 정답을, 'I'는 오답을 나타내며, 화살표는 비판 후 수정된 정답의 정확도 변화를 나타냅니다. 이 그림은 자기 비판과 교차 비판 모두에서 잘못된 입력 솔루션을 정답으로 바꾸는 능력(I→C)과 원래 정답 솔루션을 잘못된 솔루션으로 바꾸는 능력(C→I) 사이의 일관된 비대칭성을 보여줍니다. 대부분의 모델은 잘못된 솔루션을 개선하는 능력(I→C)이 제한적이지만, 원래 정답 솔루션을 비판할 때는 상당한 성능 저하(C→I)를 보입니다. 그러나 o1-mini는 ARC와 College Math에서 각각 25.85%와 24.37%의 I→C 개선을 보이는 눈에 띄는 예외이며, 솔루션 유지를 위해 여전히 고군분투하고 있습니다. 교차 비판의 경우, 대부분의 모델은 ARC와 GSM8K와 같은 기본적인 작업에서 I→C 개선(30~45%)을 상당히 보이지만, GPQA와 MMLU-STEM과 같은 특수 도메인에서는 솔루션 저하(C→I) 위험이 더 높습니다. 이는 비판 패러다임의 효과가 작업의 복잡성과 도메인 특수성에 크게 영향을 받으며, 기본적인 수학적 추론 작업이 특수 도메인 작업보다 신뢰할 수 있는 비판에 더 적합하다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Caption
> </details>



![](https://arxiv.org/html/2501.14492/x6.png)

> 🔼 그림 6은 반복적인 비판의 성능을 보여줍니다.  성능 변화는 8가지 과제에 걸쳐 평균화됩니다. 기준 해결책에 대한 성능 변화를 통해 비판의 효과를 측정합니다. 그림은 다양한 모델들에서 라운드에 따른 성능 변화의 다양한 추세를 보여줍니다. 특히, 일부 모델은 효과가 지속적으로 감소하는 반면, 다른 모델들은 일관되게 성능 향상을 유지합니다. 이러한 변화는 모델과 라운드에 따라 비판 효과의 역동적인 특징을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Caption
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Output | Format |
|---|---|{{< /table-caption >}}
> 🔼 CriticBench-THU의 비판 분석 결과를 보여주는 표입니다. 표에 따르면, 정확한 판단을 내린 경우(55.4%)에도 저품질 비판이 많은 것으로 나타났습니다(68.8%). 이는 효과적인 비판 생성의 어려움을 보여줍니다.  즉, 단순히 정답/오답 여부를 맞추는 것만으로는 비판의 질을 제대로 평가할 수 없음을 시사합니다.  정확한 판단에도 불구하고 비판의 내용 자체가 부실하거나, 논리적 오류가 있거나, 개선 방향 제시가 미흡한 경우가 많았다는 것을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Quality analysis of critiques in CriticBench-THU. All values are in percentages (%). Despite achieving correct verdicts in many cases (55.4%), the majority of critiques (68.8%) are still of low quality, highlighting the challenge in generating effective critiques.
> </details>

{{< table-caption >}}
| Critique | Type |
|---|---|{{< /table-caption >}}
> 🔼 표 3은 RealCritic 데이터셋의 각 하위 데이터셋에 포함된 질문의 총 개수와 정답과 오답으로 분류된 질문의 개수를 보여줍니다. 각 하위 데이터셋에 대해 정답과 오답의 비율이 균형을 이루도록 구성되었음을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: The total number of questions in each subset of RealCritic. Along with how many questions come with incorrect solutions and how many come with correct solutions.
> </details>

{{< table-caption >}}
| Evaluation | Method |
|---|---|{{< /table-caption >}}
> 🔼 표 4는 다양한 평가 방식에 따른 모델 성능을 비교한 표입니다.  '직접 풀이'는 모델이 문제를 직접 푸는 능력을 나타내고, '자기 비평'은 모델이 자신의 풀이를 비판하는 성능을, '다른 모델 비평'은 다른 모델의 풀이를 비판하는 성능을 보여줍니다.  Δ(자기 비평 대비 직접 풀이)는 자기 비평을 통해 직접 풀이보다 얼마나 성능이 향상되었는지, Δ(다른 모델 비평 대비 무작위)는 다른 모델의 풀이를 비판할 때 무작위로 답하는 것보다 얼마나 더 나은 성능을 보였는지 나타냅니다. 회색 행은 델타 지표를 강조 표시하며, 모든 수치는 백분율(%)로 표시됩니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Performance comparison across different evaluation modes. Direct Solution represents the model’s ability to solve problems directly. Self-Critique shows performance when the model critiques its own solutions. Cross-Model Critique indicates performance when critiquing other models’ solutions. Δ(Self vs. Direct) shows the improvement from self-critique over direct solution. Δ(Cross vs. Random) shows how much better the model performs compared to random chance (50%) in cross-model critique tasks. Gray rows highlight the delta metrics. All numbers are in percentages (%).
> </details>

{{< table-caption >}}
| Iterative | Support |
|---|---|{{< /table-caption >}}
> 🔼 표 5는 다양한 평가 지표에 따른 O1-mini와 Qwen2.5-72B-Instruct 모델의 성능 비교 결과를 보여줍니다.  구체적으로 자기 비판, 타 모델 비판, 반복 비판 등 세 가지 시나리오에서 각 모델의 성능을 다양한 측면에서 비교 분석하여, 각 모델의 강점과 약점을 보다 명확하게 파악할 수 있도록 합니다.  이 표를 통해, 각 모델의 비판 능력의 차이뿐 아니라,  다양한 평가 방법에 따른 성능 변화 양상도 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Performance comparison of O1-mini and Qwen2.5-72B-Instruct across different evaluation metrics
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