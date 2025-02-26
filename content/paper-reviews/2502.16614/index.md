---
title: "CodeCriticBench: A Holistic Code Critique Benchmark for Large Language Models"
summary: "CodeCriticBench: LLM의 코드 비평 능력을 위한 종합적 벤치마크"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 M-A-P",]
showSummary: true
date: 2025-02-23
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.16614 {{< /keyword >}}
{{< keyword icon="writer" >}} Alexander Zhang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-25 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.16614" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.16614" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/codecriticbench-a-holistic-code-critique" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 LLM 코드 비평 벤치마크는 코드 생성에만 초점을 맞추거나 평가 측면이 부족하다는 한계가 있었습니다.  이러한 문제를 해결하기 위해, 본 논문에서는 LLM의 코드 생성 및 코드 QA 능력을 종합적으로 평가하는 새로운 벤치마크인 CodeCriticBench를 제안합니다.

CodeCriticBench는 다양한 난이도의 코드 문제와 기본 및 고급 평가 프로토콜을 포함하며, 세분화된 평가 체크리스트를 통해 LLM의 코드 비평 능력을 더욱 정확하게 평가할 수 있도록 설계되었습니다.  실험 결과, 제안된 벤치마크는 기존 LLM의 성능을 효과적으로 평가하고 향후 LLM의 코드 비평 능력 향상을 위한 중요한 기준을 제시합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} CodeCriticBench는 LLM의 코드 생성 및 코드 QA 작업에 대한 **종합적인 평가**를 제공합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 기존 벤치마크의 한계를 극복하고 **다양한 난이도**의 코드 문제와 **세분화된 평가 기준**을 제공합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 실험 결과는 CodeCriticBench의 **효과성**과 **확장성**을 보여주며, LLM의 코드 비평 능력 향상에 기여할 수 있음을 시사합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **코드 평가 능력**을 종합적으로 평가하는 새로운 벤치마크인 CodeCriticBench를 제시하여, **LLM의 코드 비평 능력 평가**에 대한 새로운 가능성을 열었습니다. 기존 벤치마크의 한계를 극복하고 다양한 코드 작업과 평가 방법론을 제시하여, LLM의 코드 이해 및 비평 능력 향상에 기여할 수 있는 중요한 연구입니다.  향후 연구 방향으로 코드 저장소 수준의 평가 확장 및 다양한 영역으로의 적용 확대 가능성을 제시하여, **LLM의 코드 비평 능력 연구**를 위한 새로운 방향을 제시하고 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.16614/x1.png)

> 🔼 그림 1은 논문에서 제시하는 두 가지 코드 평가 방법, 기본 평가와 고급 평가의 예시를 보여줍니다. 기본 평가는 AI 어시스턴트의 답변이 정확한지 여부를 판단하는 간단한 이진 분류 방식입니다. 반면 고급 평가는 오류 유형, 시간 복잡도, 코드 가독성 등 다양한 측면을 고려하여 세분화된 평가 기준표를 사용하여 AI 어시스턴트의 성능을 평가하는 더욱 정교한 방식입니다. 그림은 각 평가 방법의 평가 과정, 요구 사항, 기준 및 출력 형식을 보여주는 예시를 통해 두 방법의 차이를 명확하게 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Illustration of the Basic Critique Evaluation and Advanced Critique Evaluation.
> </details>





{{< table-caption >}}
| Benchmark | Data Size | Code Gen. | Code QA | Basic | Advanced |
|---|---|---|---|---|---| 
| CriticBench | 3,825 | 464 | - | ✓ | × |
| CriticEval | 3,608 | 1,340 | - | ✓ | × |
| JudgeBench | 350 | 42 | - | ✓ | × |
| RealCritic | 2,093 | - | - | ✓ | × |
| CodeCriticBench | 4,300 | 3,200 | 1,100 | ✓ | ✓ |{{< /table-caption >}}

> 🔼 CodeCriticBench 데이터셋의 통계를 보여주는 표입니다. 문제의 수, 난이도(쉬움, 중간, 어려움), 길이(질문, 답변, 평가 체크리스트), 그리고 각 항목의 토큰 수를 보여줍니다.  CodeCriticBench 데이터셋의 전반적인 크기와 특징을 한눈에 파악할 수 있도록 구성되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Dataset statistics of CodeCriticBench.
> </details>





### In-depth insights


#### LLM Code Critique
LLM 코드 비평에 대한 심층적인 논의는 **LLM의 코드 생성 능력을 넘어선 코드 이해 및 평가 능력**에 초점을 맞춥니다.  단순한 코드 생성 벤치마크를 넘어, **LLM이 코드의 정확성, 효율성, 스타일, 유지보수 용이성 등 다양한 측면을 얼마나 잘 평가할 수 있는지**를 평가하는 것이 중요합니다. 이는 **실제 소프트웨어 개발 환경에서 LLM의 유용성을 판단하는 데 필수적**입니다.  **코드 오류 검출 및 수정 능력**, **코드 스타일 가이드라인 제시 능력**, **코드 개선 제안 능력** 등을 평가하는 다양한 지표가 필요하며, 이를 위해서는 **다양한 종류의 코드와 질의를 포함하는 종합적인 벤치마크**가 요구됩니다.  **인간 전문가의 평가와의 비교 분석**을 통해 LLM의 코드 비평 능력 수준을 객관적으로 평가해야 하며, **모델의 크기 및 아키텍처가 코드 비평 성능에 미치는 영향**을 분석하는 것도 중요한 연구 과제입니다.  **데이터셋의 질과 양**, **평가 지표의 적절성**, 그리고 **평가 방법의 객관성** 등을 고려하여 LLM 코드 비평 능력 연구가 체계적으로 수행되어야 합니다.  궁극적으로는 **LLM 코드 비평 기술의 발전**을 통해 **더욱 안전하고, 효율적이며, 유지보수가 용이한 소프트웨어 개발**을 가능하게 하는 것이 목표입니다.

#### Benchmark Design
본 논문의 벤치마크 설계는 **코드 생성 및 코드 질의응답 두 가지 주요 작업**에 초점을 맞추어 **다양한 난이도의 질의를 포함**하도록 구성되어 있습니다. 이는 단순히 정확성만 평가하는 기존 벤치마크의 한계를 극복하고, **모델의 코드 비판 능력을 종합적으로 평가**하기 위한 것입니다.  또한, 기본적인 정확성 평가 외에도, 세부적인 평가 기준표를 활용한 **고급 평가 방식**을 도입하여 모델의 코드 비판 능력을 더욱 정교하게 평가합니다. 이러한 **다차원적이고 세분화된 평가 체계**를 통해 기존 벤치마크보다 더욱 포괄적이고 심도있는 분석을 가능하게 합니다.  특히, **실제 소프트웨어 개발 상황을 반영**하기 위해 다양한 시나리오를 포함시킨 점이 중요합니다.  이를 통해 **실용성 높은 벤치마크**를 구축하고,  LLM의 코드 비판 능력 향상에 기여할 수 있을 것으로 예상됩니다.  **다양한 규모의 모델들에 대한 실험 결과**를 제시하여 벤치마크의 유효성을 검증한 것 또한 중요한 특징입니다.

#### Evaluation Metrics
논문의 "평가 지표" 부분은 모델 성능을 측정하기 위한 정량적 방법론을 제시합니다. **정확도(ACC)**는 기본 평가에서 모델 예측과 실제 레이블의 일치 정도를 나타내는 반면, **평균 제곱 오차(MSE)**는 고급 평가에서 다차원적 평가 점수의 오차를 측정합니다. **Pass@1 정확도**는 코드 오류 감지에서 적어도 하나의 오류를 정확히 식별하는 모델의 능력을 평가합니다.  이러한 지표들은 **모델의 코드 생성 및 코드 질의응답 능력**을 다각적으로 평가하는 데 사용되며, **모델 크기 및 유형**에 따른 성능 차이를 분석하는 데 중요한 역할을 합니다.  **기본 정확도와 고급 평가 점수 간의 상관관계 분석**을 통해 평가 체계의 타당성을 검증하고, **다양한 어려움 수준의 데이터셋**에 대한 모델 성능 비교를 통해 벤치마크의 견고성을 확인합니다.  **세분화된 평가 기준**을 통한 정밀한 분석은 모델의 강점과 약점을 파악하는 데 도움을 주며, 결과적으로 **LLM의 코드 비평 능력**에 대한 심도있는 이해를 제공합니다.

#### Scaling Law Analysis
본 논문의 "스케일링 법칙 분석" 부분은 모델의 크기가 커짐에 따라 성능이 향상되는지 여부를 규명하는 데 초점을 맞춥니다. **매개변수의 수가 증가함에 따라 정확도(ACC)가 향상되는 경향**을 보이는데, 이는 제시된 코드 비평 벤치마크의 **견고성**을 확인하는 데 중요합니다.  **스케일링 법칙은 일반적으로 대규모 언어 모델의 성능 향상을 예측하는 데 사용**되며, 이 분석을 통해 **본 벤치마크가 모델 크기에 따른 성능 변화를 잘 포착**하고 있음을 시사합니다.  다만, **모든 모델이 동일한 비율로 성능이 향상되는 것은 아니며, 모델의 구조나 훈련 방식에 따라 차이**가 있을 수 있습니다.  **일부 모델은 특정 크기에서 성능 향상의 한계점을 보이는 반면, 다른 모델은 계속해서 향상**됩니다.  따라서 단순한 매개변수 크기 증가만으로는 성능 향상을 보장할 수 없으며, 모델 구조 및 훈련 전략의 최적화가 동시에 중요하다는 결론을 제시합니다.  **이 분석은 벤치마크의 신뢰도를 높이는 데 기여**하며, 향후 대규모 언어 모델의 코드 비평 능력 연구에 중요한 기준을 제공할 것으로 예상됩니다.

#### Future Work
본 논문은 코드 평가 벤치마크인 CodeCriticBench를 제시하지만, **미래 연구 방향**으로 여러 가능성을 제시합니다.  가장 중요한 것은 벤치마크의 범위를 확장하는 것입니다. 현재는 단일 파일 단위의 코드에만 초점을 맞추고 있으므로, **다음 단계는 저장소 수준의 코드 평가**를 포함하도록 벤치마크를 확장하는 것입니다. 이는 보다 현실적인 소프트웨어 개발 환경을 반영하여 벤치마크의 유용성을 높일 수 있습니다.  또한, 코드에만 국한된 현재 범위를 벗어나 **다양한 도메인과 작업 유형으로 확장**하여 평가 능력을 더욱 포괄적으로 평가할 수 있도록 하는 것이 중요합니다.  **다른 프로그래밍 언어 지원** 및 **더욱 다양한 코드 복잡도**를 포함하는 것도 벤치마크의 강점을 극대화하는 데 도움이 될 것입니다.  **대규모 언어 모델(LLM)의 비판적 사고 능력 평가에 대한 새로운 지표**를 개발하는 것도 중요한 미래 연구 과제입니다. 현재 벤치마크에서 사용하는 기본 정확도와 고급 평가 지표 외에,  **LLM의 코드 이해 능력과 오류 수정 능력**을 보다 정교하게 측정할 수 있는 새로운 지표가 필요합니다.  마지막으로, **CodeCriticBench의 확장성과 적용성을 높이기 위한 연구**가 필요합니다.  예를 들어, 다양한 크기의 LLM에 대한 평가 결과를 분석하여 확장성을 평가하고,  실제 코드 검토 시스템과의 통합을 통해 실제 적용 가능성을 확인하는 연구를 진행하는 것이 중요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.16614/x2.png)

> 🔼 그림 2는 CodeCriticBench 데이터 수집 과정을 보여줍니다. CodeCriticBench는 코드 생성 및 코드 QA 두 가지 주요 코드 작업을 포함하는 종합적인 코드 비평 벤치마크입니다. 그림은 각 작업에 대한 데이터 수집 방법을 단계별로 보여주는 흐름도 형식입니다. 코드 생성 작업의 경우, CodeForces, MBPP, LiveCodeBench와 같은 다양한 소스에서 알고리즘 문제를 수집하고, 이를 DeepSeek-v3를 사용하여 개선합니다. 또한, 특정 프로그래밍 오류를 감지하기 위해 디버깅 하위 집합을 만들고, 전문가와 대형 언어 모델(LLM)의 검토를 통해 오류를 걸러냅니다. 코드 QA 작업의 경우, StackOverflow에서 질문과 답변 쌍을 수집하여 품질 필터링을 거칩니다. Qwen2.5-72B LLM을 사용하여 다양한 응답을 생성하고, 수동 및 LLM 기반 검토를 통해 고품질 하위 집합을 만듭니다. 이러한 과정을 통해 CodeCriticBench는 다양하고 고품질의 코드 비평 데이터를 확보합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Illustration of data collection process.
> </details>



![](https://arxiv.org/html/2502.16614/x3.png)

> 🔼 본 그림은 모델의 크기(파라미터 수)와 기본 코드 비평 평가 지표인 정확도(ACC) 간의 상관관계를 보여줍니다.  모델의 크기가 커짐에 따라 정확도가 향상되는 경향을 보여주는 스케일링 법칙을 나타냅니다. '*' 표시는 추정된 파라미터 크기를 나타냅니다. 즉, 모델의 크기가 클수록 코드 비평 작업에서 더 나은 성능을 보인다는 것을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Scaling law on basic critique evaluation (ACC) across models. “*” indicates an estimated parameter size.
> </details>



![](https://arxiv.org/html/2502.16614/x4.png)

> 🔼 그림 4는 논문의 'Code QA' 섹션에서 기본적인 비평 평가를 기준으로 여러 모델의 성능을 비교한 결과를 보여줍니다.  다양한 모델들의 크기와 종류에 따른 정확도를 보여주는 그래프 또는 차트 형태일 것이며, 각 모델의 정확도를 수치 또는 시각적으로 비교하여 모델의 비평 능력의 차이를 보여줍니다. 이는 코드 관련 질문에 대한 답변의 정확성을 평가하는 기본적인 척도를 통해 모델 성능을 평가한 결과를 시각적으로 표현한 것입니다.  특히, 서로 다른 모델들의 크기와 성능 간의 관계를 보여주는 것이 주요 내용일 것입니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Comparison across different models on “Code QA” (Basic Critique Evaluation).
> </details>



![](https://arxiv.org/html/2502.16614/x5.png)

> 🔼 그림 5는 기본적인 코드 평가 방식을 사용했을 때, 모델의 정확도(ACC)를 다양한 난이도(쉬움, 중간, 어려움)별로 보여줍니다. 각 난이도는 다양한 최첨단 언어 모델들이 문제를 얼마나 정확하게 풀었는지에 따라 분류되었습니다. 이 그림은 모델의 크기가 커질수록 정확도가 높아지는 경향이 있지만, 특히 어려운 문제의 경우에는 그 성능 향상이 제한적임을 보여줍니다. 특히, 'OpenAI 01-Preview'와 'DeepSeek-R1' 모델은 어려운 문제에서도 비교적 높은 정확도를 유지하는 모습을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Model performance (ACC) on different difficulty levels (Basic Critique Evaluation) .
> </details>



![](https://arxiv.org/html/2502.16614/x6.png)

> 🔼 본 그림은 다양한 크기의 모델들이 5가지 일반적인 프로그래밍 오류 유형을 얼마나 정확하게 식별하는지 비교 분석한 결과를 보여줍니다.  각 모델의 정확도를 오류 유형별로 시각화하여, 모델 크기와 오류 유형 식별 성능 간의 상관관계를 파악하는 데 도움을 줍니다.  더 큰 모델이 더 나은 성능을 보이는 경향이 있음을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Comparison of the accuracy of different models in identifying five common programming error types.
> </details>



![](https://arxiv.org/html/2502.16614/x7.png)

> 🔼 그림 7은 CodeCriticBench 데이터셋의 평가 점수 분포를 보여줍니다.  'Code Gen' 과 'Code QA' 두 가지 주요 코드 평가 작업에 대한 기본 정확도와 고급 평가 점수의 분포를 나타내는 히스토그램이 포함되어 있습니다. 이를 통해 각 작업의 난이도와 모델 성능을 파악하고 데이터셋의 신뢰성을 확인할 수 있습니다. x축은 평가 점수(1~10), y축은 각 점수를 받은 문제의 개수를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Rating distribution of the CodeCriticBench.
> </details>



![](https://arxiv.org/html/2502.16614/x8.png)

> 🔼 그림 8은 다양한 크기의 모델들이 다양한 유형의 코드 오류를 식별하는 실험적 정확도 결과를 보여줍니다.  세부적으로는,  각 모델이 '성능 문제', '보안 취약성', '참조 오류' 등의 오류 유형을 얼마나 정확하게 식별했는지 보여주는 막대 그래프로 구성되어 있습니다.  이를 통해 모델 크기와 오류 유형 식별 능력 간의 상관관계를 분석하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Experimental accuracy results of different models across various error types.
> </details>



![](https://arxiv.org/html/2502.16614/x9.png)

> 🔼 본 그림은 세 가지 평가 방법(기본 비평, 고급 비평, 인간 평가)에 따른 모델 응답 순위를 비교한 것입니다. 기본 비평은 모델의 응답이 정확한지 여부만 평가하는 반면, 고급 비평은 더욱 세분화된 평가 기준을 적용하여 모델 응답의 질적 측면을 종합적으로 평가합니다. 인간 평가는 전문가가 직접 모델의 응답을 평가한 결과입니다. 그림을 통해 세 가지 평가 방법 간의 상관관계 및 고급 비평의 유효성을 확인할 수 있습니다. 특히, 고급 비평 결과가 인간 평가 결과와 더 높은 상관관계를 보이는 경향을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Comparison of ranking of model responses by three methods: basic critique, advanced critique and human evaluations.
> </details>



![](https://arxiv.org/html/2502.16614/x10.png)

> 🔼 그림 10은 Code QA(코드 기반 질문 답변) 작업에 대한 예시를 보여줍니다. 질문과 답변 쌍, 다차원 평가 체크리스트, 관련 레이블이 포함되어 있습니다. 이 그림은 CodeCriticBench 데이터셋의 구성 요소를 보여주는 것으로, 질문에 대한 정확한 답변과 세부적인 평가 항목을 포함한 종합적인 평가를 제공하는 것을 보여줍니다.  정확도, 신뢰성 등 다양한 차원의 점수가 매겨져 있으며, 최종 점수 또한 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Example of correct case of code qa.
> </details>



![](https://arxiv.org/html/2502.16614/x11.png)

> 🔼 그림 11은 모델이 생성한 비평을 사용하여 답변을 개선하기 전과 후의 코드 질문 답변 쌍에 대한 점수를 보여줍니다.  모델의 비평을 적용하여 답변을 개선한 후에 점수가 어떻게 향상되었는지 보여주는 결과를 시각적으로 나타냅니다.  특히, 다양한 크기의 모델이 생성한 비평이 답변의 질에 미치는 영향을 상세히 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Scoring results of QA pairs before and after applying critiques to refine the answers.
> </details>



![](https://arxiv.org/html/2502.16614/x12.png)

> 🔼 그림은 CodeCriticBench 데이터셋의 Code Generation(코드 생성) 부분에 대한 통계를 보여줍니다.  x축은 평점(Rating)이고, y축은 각 평점에 해당하는 문제의 개수를 나타냅니다.  'Correct' 막대는 AI가 생성한 코드가 정답인 문제의 수를, 'Error' 막대는 AI가 생성한 코드가 오답인 문제의 수를 보여줍니다. 이 그래프는 CodeCriticBench 데이터셋의 코드 생성 태스크의 난이도 분포를 시각적으로 보여주어 데이터셋의 품질과 신뢰성을 평가하는 데 도움을 줍니다.  특히, 정답과 오답의 분포를 비교하여 모델의 성능 평가에 활용할 수 있는 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> (a) The Code Gen subset.
> </details>



![](https://arxiv.org/html/2502.16614/x13.png)

> 🔼 그림 2는 CodeCriticBench 데이터셋 구성 과정을 보여줍니다. CodeCriticBench는 코드 생성과 코드 QA 두 가지 주요 작업을 포함합니다. 코드 생성 작업의 경우, CodeForces, MBPP, LiveCodeBench 데이터셋에서 알고리즘 문제를 수집하고, DeepSeek-v3를 사용하여 문제를 다시 작성하여 다양성과 테스트 케이스 재사용성을 높였습니다. 또한, 특정 프로그래밍 오류를 감지하는 모델의 능력을 평가하기 위해 디버깅 하위 집합을 생성했습니다. 이를 위해, 전문가 및 LLMs와의 반복적인 논의를 통해 버그 목록을 수집하고, LLM이 검증된 정상적인 코드에 지정된 오류 유형을 삽입하도록 프롬프트했습니다. 수정된 샘플은 오류 발생을 확인하기 위해 샌드박스 실행을 거치고, 카테고리에 맞는 오류인지 확인하기 위해 수동 검토를 거쳤습니다. 코드 QA 작업의 경우, StackOverflow에서 실제 코드 요구 사항을 수집하고, Qwen2.5-72B를 사용하여 새로운 질문을 생성하여 다양한 응답을 만들었습니다. 그리고 수동 및 LLM 지원 검토를 통해 고품질 하위 집합을 형성했습니다. 그림은 이러한 데이터 수집 프로세스를 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) The Code QA subset.
> </details>



![](https://arxiv.org/html/2502.16614/x14.png)

> 🔼 그림 12는 CodeCriticBench 데이터셋의 품질을 보여주는 정확도(Correctness) 점수 분포를 나타냅니다. CodeCriticBench는 코드 생성(Code Generation) 및 코드 질의응답(Code QA) 두 가지 주요 작업에 대한 평가를 포함하며, 각 작업에 대한 정확도 점수의 분포를 보여줍니다. (a)는 코드 생성 작업에 대한 정확도 점수 분포를, (b)는 코드 질의응답 작업에 대한 정확도 점수 분포를 보여줍니다. 두 그래프 모두 정확도 점수가 높은 데이터가 많이 분포되어 있음을 보여주어, CodeCriticBench 데이터셋의 품질이 우수함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Rating distribution.
> </details>



![](https://arxiv.org/html/2502.16614/x15.png)

> 🔼  그림 13은 코드 생성 작업에 대한 정확한 예시를 보여줍니다.  이 그림은 사용자의 질문과 AI 어시스턴트의 응답을 보여주며, 기본적인 평가와 고급 평가 모두에서 정확한 답변을 제시합니다. 고급 평가에서는 세분화된 평가 체크리스트를 통해 코드의 정확성, 시간 복잡도 최적화, 유지보수 용이성 등 다양한 측면을 평가합니다.  이 예시는 CodeCriticBench가 코드 생성 작업에서 LLMs의 성능을 평가하는 데 얼마나 효과적인지를 보여줍니다. 그림에는 질문, 답변, 세분화된 평가 기준 및 점수, 그리고 최종 점수가 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: Example of correct case of code generation.
> </details>



![](https://arxiv.org/html/2502.16614/x16.png)

> 🔼 그림 14는 코드 생성 작업에서 오류가 발생한 사례를 보여줍니다.  이 그림에는 사용자 질문, AI가 생성한 잘못된 코드, 그리고 세부적인 오류 평가 체크리스트와 최종 평가 점수가 포함되어 있습니다.  AI가 생성한 코드에는 알고리즘 오류 또는 요구사항 불충족과 같은 문제가 있음을 보여주고, 이를 통해 코드 생성 모델의 성능 한계와 개선 방향을 제시합니다.  기본적인 코드 정확성 평가와 고급 평가 모두에서 낮은 점수를 받은 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: Example of error case of code generation.
> </details>



![](https://arxiv.org/html/2502.16614/x17.png)

> 🔼 그림 15는 Code QA 작업의 오류 사례를 보여줍니다. 질문과 답변, 세부적인 평가 체크리스트, 그리고 관련 레이블(정답/오답, 점수 등)이 포함되어 있습니다. 이 그림은 CodeCriticBench 데이터셋의 다양한 특징들을 보여주는 예시 중 하나입니다. 질문의 난이도와 관련된 정보도 포함되어 있습니다. 그림을 통해 사용자가 CodeCriticBench 데이터셋의 구성과 특징을 더 잘 이해할 수 있도록 돕습니다.
> <details>
> <summary>read the caption</summary>
> Figure 15: Example of error case of code qa.
> </details>



![](https://arxiv.org/html/2502.16614/x18.png)

> 🔼 본 그림(그림 16)은 다양한 크기의 언어 모델들에 대한 고급 평가 척도인 MSE(평균 제곱 오차)를 보여줍니다. 모델의 크기가 커짐에 따라 MSE가 감소하는 경향을 보여주는 그래프가 제시되어 있습니다. 이는 모델의 크기가 클수록 고급 평가 척도에서 더 나은 성능을 보인다는 것을 시사합니다.  별표(*)는 추정된 매개변수 크기를 나타냅니다.  본 그림은 모델의 크기와 성능 간의 상관관계를 보여주는 스케일링 법칙을 시각적으로 보여주는 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 16: Scaling law on advanced critique evaluation (MSE) across models. “*” indicates an estimated parameter size.
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