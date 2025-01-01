---
title: "Efficiently Serving LLM Reasoning Programs with Certaindex"
summary: "Dynasor은 LLM 추론 프로그램의 자원 사용을 최적화하는 시스템으로, **certaindex**라는 새로운 지표를 활용하여 어려운 질의에는 더 많은 연산을, 간단한 질의에는 적은 연산을 할당하고, 전망이 없는 질의는 조기에 종료함으로써 정확도, 지연 시간 및 비용을 균형 있게 맞춥니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 UC San Diego",]
showSummary: true
date: 2024-12-30
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.20993 {{< /keyword >}}
{{< keyword icon="writer" >}} Yichao Fu et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-31 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.20993" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.20993" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/efficiently-serving-llm-reasoning-programs" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)은 수학 문제 해결, 코드 생성, 법률 분석 등의 고급 추론 작업에서 뛰어난 성능을 보여주고 있습니다. 하지만, 이러한 작업에는 여러 해결 경로를 탐색하는 추론 알고리즘이 필요하며, 이로 인해 컴퓨팅 자원 소모가 증가하고 응답 시간이 길어지는 문제가 발생합니다. 기존의 서빙 시스템은 이러한 알고리즘의 확장성이나 질의의 난이도 차이에 적응하지 못하여 자원을 비효율적으로 사용하고 지연 시간 목표를 달성하지 못하는 경우가 많습니다.

본 논문에서는 LLM 추론 쿼리에 대한 추론 시간 컴퓨팅을 최적화하는 Dynasor 시스템을 제시합니다. Dynasor은 통계적 추론 진행 상황을 측정하는 certaindex라는 프록시를 사용하여 컴퓨팅 자원을 동적으로 할당합니다. Dynasor은 추론 진행 상황에 따라 스케줄링을 공동으로 적용하여 어려운 쿼리에는 더 많은 컴퓨팅 자원을 할당하고, 간단한 쿼리에는 컴퓨팅 자원을 줄이며, 전망이 없는 쿼리는 조기에 종료합니다. 다양한 데이터 세트와 알고리즘에서 Dynasor은 배치 처리에서 최대 50%의 컴퓨팅 자원을 절감하고, 온라인 서비스에서 최대 3.3배 높은 쿼리 처리율 또는 4.7배 엄격한 지연 시간 목표를 유지합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} Dynasor은 **certaindex**라는 새로운 지표를 활용하여 LLM 추론 프로그램의 자원 할당을 동적으로 조정합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} Dynasor은 배치 처리에서 최대 50%의 연산량을 줄이고, 온라인 서비스에서 최대 3.3배 높은 질의율 또는 4.7배 더 엄격한 지연 시간 목표를 달성합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} Dynasor은 다양한 추론 알고리즘과 데이터 세트에 대한 실험을 통해 그 효과를 검증하였습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **LLM 추론 프로그램의 효율적인 자원 할당 및 스케줄링**에 대한 새로운 방법론을 제시하여, 연구자들에게 **추론 프로그램의 성능을 향상시키는 실질적인 방안**을 제공합니다. 특히, **자원 제약 하에서 LLM 추론 프로그램의 정확도와 지연 시간을 동시에 개선**하는 데 기여하며, 이는 현재 LLM 연구의 주요 과제 중 하나인 **확장성 및 효율성 문제**를 해결하는 데 중요한 의미를 가집니다.  본 연구는 **다양한 추론 알고리즘과 데이터 세트에 대한 실험 결과**를 통해 Dynasor 시스템의 효과를 검증하며, 향후 연구를 위한 **새로운 연구 방향 및 벤치마크**를 제시합니다. 따라서, LLM 추론 프로그램 개발 및 서빙 시스템 최적화에 관심 있는 연구자들에게 높은 가치를 제공할 것입니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.20993/extracted/6102352/figures/evaluation/inference_scaling.png)

> 🔼 (a) 그림은 자기 일관성(Self-Consistency, SC) 알고리즘을 사용하여 GSM8K 데이터셋에서 질문에 대한 답변을 생성할 때, 출력 토큰 수(x축)에 따른 정확도(y축)의 변화를 보여줍니다.  일반적으로 출력 토큰 수가 증가하면 정확도가 향상되다가 특정 지점을 넘어서면 더 이상 향상되지 않는 현상(포화 상태)을 보여줍니다.  이 그림은 LLM 추론 알고리즘의 성능 확장(inference-time scaling) 특징을 보여주는 대표적인 예시입니다.  이는 추론 알고리즘이 정확도를 높이기 위해 더 많은 계산 자원을 필요로 하지만, 어느 정도 이상의 계산 자원을 투입하면 효용이 감소하는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (a)
> </details>





{{< table-caption >}}
| Algorithm | Dataset | Thres. (<math alttext="\tilde{\mathcal{H}_{\tau}}" display="inline">\tilde{\mathcal{H}_{\tau}}</math>) | Thres. (<math alttext="\mathcal{R}_{\tau}" display="inline">\mathcal{R}_{\tau}</math>) | Detect @knob |
|---|---|---|---|---|
| SC | MATH | 0.7 | / | 5 |
| SC | GSM8K | 0.7 | / | 5 |
| SC | LiveCodeBench | 0.4 | / | 5 |
| MCTS | GSM8K | 0.99 | 0.4 | 3 |
| MCTS | ASDiv | / | 0.4 | 3 |
| Rebase | GSM8K | 0.85 | 0.99 | 16 |
| Rebase | MATH | 0.75 | / | 16 |{{< /table-caption >}}

> 🔼 표 1은 본 논문에서 제안하는 방법론인 Dynasor에서 사용되는 Certaindex의 하이퍼파라미터 설정값들을 보여줍니다. Certaindex는 LLM 추론 과정의 진행 상황을 측정하는 지표로 사용되는데, 이 표에서는 각 알고리즘(SC, MCTS, Rebase), 데이터셋(MATH, GSM8K, LiveCodeBench), 그리고 사용된 LLM 모델에 따라 어떻게 Certaindex의 임계값(Threshold)과 검출 단계(Detect @knob)가 설정되는지를 보여줍니다. 특히, Rebase 알고리즘의 경우 MATH 벤치마크의 MATH-OAI [28] 서브셋에서 평가되었음을 명시하고 있습니다.  즉, 어떤 알고리즘과 데이터셋에 대해서 얼마나 많은 토큰을 생성해야 정확한 결과를 얻을 수 있는지에 대한 정보를 포함하는 하이퍼파라미터들을 보여주는 표입니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Hyperparameter configurations for certaindex. Rebase is evaluated on the MATH-OAI [28] subset of the MATH benchmark.
> </details>





### In-depth insights


#### Adaptive Compute
**적응형 컴퓨팅(Adaptive Compute)**은 제한된 자원 내에서 최대의 성능을 달성하기 위해 인공지능 모델의 컴퓨팅 자원 할당을 동적으로 조절하는 기술입니다.  연구 논문에서 제시된 **Certaindex** 와 같은 지표를 사용하여 질의의 어려움 정도를 추정하고, **어려운 질의에는 더 많은 컴퓨팅 자원을 할당하고, 쉬운 질의에는 적은 자원을 할당하여** 효율성을 극대화합니다.  이는 **전체적인 정확도와 지연 시간을 최적화**하며 **자원 낭비를 줄이는** 데 중요한 역할을 합니다.  **Dynasor** 와 같은 시스템은 Certaindex 기반의 적응형 컴퓨팅을 통해 배치 처리 및 온라인 서비스 환경에서 모두 컴퓨팅 자원을 최대 50%까지 절감하고, 질의 처리 속도를 3.3배까지 높이거나 지연 시간 목표를 4.7배까지 개선하는 등 뛰어난 성능 향상을 보여줍니다.  **적응형 컴퓨팅은 LLM 추론 프로그램의 효율성과 확장성을 크게 개선하는 핵심 기술**이며, 향후 더욱 발전된 AI 시스템 구축에 중요한 역할을 할 것으로 예상됩니다.

#### Certaindex Metric
본 논문에서 제안하는 Certaindex 메트릭은 **LLM 추론 과정의 진행도를 측정하는 새로운 방법**입니다. 기존의 LLM 추론 알고리즘은 여러 경로를 탐색하여 최종 답을 도출하는데, Certaindex는 이러한 탐색 과정에서 모델의 확신도(certainty)를 정량화하여 추론 진행 상황을 나타냅니다.  **높은 Certaindex 값은 모델이 최종 답에 근접했거나, 더 이상 계산을 진행해도 결과가 바뀌지 않을 가능성이 높음**을 시사합니다.  이를 통해 시스템은 어려운 질의에는 더 많은 계산 자원을 할당하고, 간단한 질의에는 계산 자원을 줄이거나, 전망이 없는 질의는 조기에 종료시키는 등 **동적으로 자원을 할당**할 수 있습니다.  **Certaindex는 다양한 추론 알고리즘에 적용 가능하며**, 각 알고리즘의 특성에 맞춰 계산 방법을 조정할 수 있다는 장점이 있습니다.  **실험 결과, Certaindex는 추론 과정의 진행도와 높은 상관관계**를 보였으며, 이를 기반으로 자원 할당을 최적화한 Dynasor 시스템은 기존 시스템에 비해 컴퓨팅 자원 사용량을 최대 50%까지 줄이고, 질의 처리 속도를 최대 3.3배 향상시키는 등 우수한 성능을 보였습니다.  **Certaindex는 LLM 추론 서비스의 효율성을 크게 향상**시키는 핵심 요소로 평가될 수 있습니다.

#### Dynasor System
Dynasor 시스템은 LLM 추론 프로그램의 추론 시간 컴퓨팅을 최적화하기 위해 설계된 시스템입니다. 기존 시스템과 달리 Dynasor는 추론 쿼리 내의 요청을 추적하고 스케줄링하며, 모델의 확실성을 측정하는 지표인 certaindex를 사용하여 컴퓨팅 할당을 동적으로 안내합니다. **Dynasor의 핵심은 certaindex를 활용하여 어려운 쿼리에는 더 많은 컴퓨팅 자원을 할당하고, 간단한 쿼리에는 적은 자원을 할당하며, 전망이 없는 쿼리는 조기에 종료함으로써 정확도, 지연 시간 및 비용 간의 균형을 맞추는 것입니다.**  **Dynasor는 추론 진행 상황에 따라 스케줄링을 공동으로 조정하여 효율적인 자원 사용을 달성합니다.** 다양한 데이터셋과 알고리즘에서 Dynasor는 배치 처리에서 최대 50%의 컴퓨팅을 줄이고, 온라인 서비스에서 쿼리 속도를 3.3배 높이거나 지연 시간 SLO를 4.7배 더 엄격하게 유지합니다.  **Dynasor는 기존의 LLM 서비스 시스템의 한계를 극복하고, 추론 프로그램의 성능을 크게 향상시킨 혁신적인 시스템**임을 알 수 있습니다. 특히, certaindex를 이용한 동적 자원 할당은 다른 시스템에서는 볼 수 없는 독창적인 기능이며, 이를 통해 다양한 어려움의 쿼리에 대해 효율적으로 자원을 관리할 수 있습니다.

#### Empirical Studies
본 논문의 '실험적 연구' 부분은 제안된 시스템인 Dynasor의 성능을 다양한 측면에서 평가한 결과를 제시합니다. **대규모 언어 모델(LLM) 추론 프로그램의 서빙 효율성을 높이는 Dynasor의 핵심 기능인 Certaindex 기반 리소스 할당 및 스케줄링 전략의 효과**를 실험적으로 검증합니다. 배치 처리와 온라인 서빙 환경에서의 성능 비교를 통해, Dynasor가 기존 시스템보다 컴퓨팅 자원 소모를 최대 50%까지 줄이고, 질의 처리 속도를 최대 3.3배 향상시키거나 지연 시간을 4.7배까지 단축시키는 것을 보여줍니다. **다양한 데이터셋과 알고리즘에 대한 실험 결과를 통해 Dynasor의 일반성과 우수성**을 입증하며, Certaindex 지표의 효과성과 시스템 설계의 적절성을 확인합니다.  **특히, Certaindex를 이용한 어댑티브 컴퓨팅 자원 할당의 효과는 다양한 난이도의 질의에 대한 처리 속도와 정확도 측면에서 두드러지게 나타납니다.**  더불어, 실험 설계 및 결과 분석의 엄밀성을 통해 연구의 신뢰도를 높이고, 향후 연구 방향을 제시하는 데 도움을 줍니다.

#### Future Work
본 논문은 **Certaindex 기반의 동적 자원 할당을 사용한 LLM 추론 프로그램 제공 시스템인 Dynasor**를 제시합니다.  추후 연구 방향으로는 **다양한 추론 알고리즘과 작업에 대한 Certaindex 측정 방식의 일반화**가 중요합니다.  **더욱 정교한 자원 할당 전략** (예: 강화 학습 기반 최적화)을 통해 성능을 개선할 수 있을 것입니다.  또한, **다양한 서빙 엔진과의 호환성을 높이고, 대규모 다중 사용자 환경에서의 성능을 평가**하는 것이 필요합니다.  **실시간 시스템에서의 지연 시간 관리 및 공정성 향상을 위한 추가적인 기법** 개발도 중요한 과제입니다. 마지막으로, **Dynasor의 확장성과 안정성을 높이고, 다양한 하드웨어 플랫폼에서의 성능을 최적화**하는 추가적인 연구가 필요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.20993/extracted/6102352/figures/evaluation/canonical_resourece_allocation.png)

> 🔼 그림 1(b)는 기존 시스템의 자원 할당 방식과 이상적인 자원 할당 방식을 네 가지 질의(P1-P4)에 대해 비교한 그림입니다. 각 질의의 난이도가 다르기 때문에, 이상적인 자원 할당 방식은 난이도에 따라 계산량을 동적으로 조절하여 정확도와 지연 시간 사이의 균형을 맞춥니다. 그림에서 볼 수 있듯이, 기존 시스템은 모든 질의에 동일한 양의 자원을 할당하여 비효율적인 부분이 존재하며, 어려운 질의에는 충분한 자원이 할당되지 않고, 쉬운 질의에는 불필요하게 많은 자원이 할당되는 문제점을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b)
> </details>



![](https://arxiv.org/html/2412.20993/x1.png)

> 🔼 그림 1(c)는 LLM이 최종 답변에 접근하는 과정에서 얼마나 확신하는지를 나타내는 지표인 certaindex와 정답을 얻기 위해 필요한 계산량 간의 상관관계를 보여줍니다. certaindex 값이 높을수록 LLM은 현재 답변에 대해 더 확신하고 있음을 나타내며, 추가 계산을 통해 답변이 바뀔 가능성이 적다는 것을 의미합니다. 반대로 certaindex 값이 낮을수록 LLM은 현재 답변에 대해 불확실하며, 추가 계산을 통해 대안적인 해결책을 탐색하여 더 확실한 답변에 도달할 가능성이 높습니다.
> <details>
> <summary>read the caption</summary>
> (c)
> </details>



![](https://arxiv.org/html/2412.20993/x2.png)

> 🔼 그림 1은 LLM 추론 프로그램의 자원 할당 전략에 대한 세 가지 측면을 보여줍니다. (a)는 GSM8K 데이터셋에서 자기 일관성 알고리즘의 추론 시간 확장을 보여줍니다. 출력 토큰 수가 증가함에 따라 정확도가 증가하지만 특정 지점을 넘어서면 정체됩니다. (b)는 기존 시스템과 이상적인 시스템 간의 자원 할당 차이를 네 가지 질의에 대해 보여줍니다. 기존 시스템은 어려운 질의와 쉬운 질의에 동일한 양의 자원을 할당하지만, 이상적인 시스템은 어려운 질의에 더 많은 자원을 할당하고 쉬운 질의에는 적은 자원을 할당합니다. (c)는 정확한 답을 얻는 데 필요한 계산량과 Certaindex 간의 상관관계를 보여줍니다. Certaindex 값이 높을수록 필요한 계산량이 적습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: (a) Inference time scaling of self-consistency [48] on GSM8K [7]. As we uniformly increase the number of output tokens (x-axis) per question, the overall accuracy (y-axis) grows then plateaus (see §2.2). (b) Canonical resource allocation in existing systems vs. ideal allocation for four queries P1-P4 with vary difficulties. (c) Correlations between certaindex and the compute required to obtain a correct answer. Each point is a question. Statistically higher certaindex indicates lower compute needed.
> </details>



![](https://arxiv.org/html/2412.20993/x3.png)

> 🔼 그림 2는 논문 2.1절에서 논의된 다양한 LLM 추론 알고리즘의 워크플로우를 보여줍니다. 각 알고리즘(Self-consistency, Rebase, MCTS, ICoT)은 입력 프롬프트(P)에서 시작하여 후보 답변(A)에 도달하기 위한 여러 추론 경로를 탐색하는 과정을 보여줍니다. 각 알고리즘은 서로 다른 방법으로 추론 경로를 확장하고 집계하여 최종 답변을 도출합니다. 예를 들어 Self-consistency는 여러 경로를 생성하고 다수결 투표를 통해 최종 답변을 선택하는 반면, MCTS는 탐색 트리를 사용하여 최적의 경로를 찾고, Rebase는 중간 단계의 출력을 순위 매기고 더 나은 후보 답변을 생성하기 위해 상위 순위의 출력을 선택합니다. ICoT는 훈련 중에 추론 과정을 내재화하여 일련의 연속적인 추론 단계를 통해 답변을 생성합니다.  각 알고리즘의 'knob' 매개변수는 추론 연산의 양을 제어하는 역할을 하며, 이는 생성된 토큰 수, 탐색 트리의 깊이 또는 반복 횟수 등으로 나타낼 수 있습니다.  이 그림은 각 알고리즘의 주요 단계와 차이점을 시각적으로 비교하여 이해를 돕습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Illustration of the workflow of different LLM reasoning algorithms discussed in §2.1
> </details>



![](https://arxiv.org/html/2412.20993/x4.png)

> 🔼 그림 3은 다양한 알고리즘(SC, Rebase, MCTS, ICoT), 데이터셋(LiveCodeBench, GSM8K, ASDiv, GAME24), 그리고 언어 모델(Llama, Gemma, Phi, QWQ) 조합에 대해 certaindex 강도와 실제 해결 단계 간의 상관관계를 보여줍니다. 각 그래프의 y축 레이블은 certaindex 측정 방법을 나타냅니다. 검은색 선은 certaindex를 측정한 추론 단계를, 주황색 선은 임계값 기반 할당을, 녹색 선은 곡선 피팅을 통한 보다 세분화된 접근 방식을 나타냅니다. MCTS를 제외한 모든 그래프에서, certaindex 값과 오라클 단계는 여러 번의 실행에 걸쳐 평균을 내어 무작위성을 줄였습니다. 이 그림은 certaindex가 추론 과정의 진행 상황을 나타내는 지표로서의 유용성을 시각적으로 보여주는 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3:  Correlations between certaindex strength (y-axis) and ground truth steps to solution (x-axis) on 12 (algorithm, task dataset, LLM) settings where algorithm ∈\in∈ {SC, Rebase, MCTS, ICoT}, dataset ∈\in∈ {LiveCodeBench [19], GSM8K, ASDiv [34], GAME24 [54]}, and LLM ∈\in∈ {Llama [33], Gemma [46], Phi [2], QWQ [47]}. How certaindex is measured in each setting is shown in the y𝑦yitalic_y label of each plot. Certaindex is measured at the reasoning step marked by the black line. The orange line indicates the thresholding-based allocation. The green line illustrates a more fine-grained approach through curve fitting. For all plots (except MCTS), both certaindex values and oracle steps were averaged across multiple runs to combat randomness.
> </details>



![](https://arxiv.org/html/2412.20993/x5.png)

> 🔼 그림 4는 자기 일관성 추론에서 서로 다른 탐지 단계에서의 Certaindex 값을 보여줍니다. 이 그림은 자기 일관성 추론 알고리즘의 추론 과정에서 여러 시점에서 계산된 Certaindex 값을 시각적으로 보여줍니다. 각 점은 개별 문제를 나타내며, 세 가지 유형(조기 중단 가능 문제, 해결 가능 문제, 해결 불가능 문제)으로 분류됩니다. x축은 수행된 단계 수를, y축은 Certaindex 값을 나타냅니다. 이 그림은 Certaindex와 추론 단계 간의 상관관계를 보여주어 Certaindex 값이 높을수록 추론에 필요한 단계 수가 적음을 시사합니다. 이는 Certaindex가 추론 진행 상황을 효과적으로 측정하는 데 유용함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4:  Certaindex Values Across Different Detection Steps in Self-Consistency Reasoning
> </details>



![](https://arxiv.org/html/2412.20993/extracted/6102352/figures/gang2.jpg)

> 🔼 그림 5는 LLM 추론 과정에서의 확실성 측정값과 풀 수 있는 문제에 대한 평균 해결 단계 수 사이의 상관관계를 보여줍니다.  LLM을 여러 번 사용하여 질문을 풀고 평균 단계 수를 계산하여 실제 평균 단계 수를 얻었습니다.  즉, LLM이 얼마나 확실하게 답을 제시하는지(확실성 측정값)가 문제 해결에 필요한 단계 수와 얼마나 밀접하게 관련되어 있는지를 보여주는 그림입니다.  확실성이 높을수록 문제 해결에 필요한 단계 수가 적다는 것을 시각적으로 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Correlation between certainty measurements and mean steps required to solve problems on solvable problems. We obtain the ground-truth mean steps by solving the queries using the LLM multiple times and counting the average steps.
> </details>



![](https://arxiv.org/html/2412.20993/x6.png)

> 🔼 그림 6은 Dynasor 시스템의 아키텍처와 구성 요소에 대한 개요를 보여줍니다. 왼쪽 패널 (a)는 Dynasor의 전체 아키텍처를 보여주는 다이어그램입니다. 여기에는 추론 프로그램 추상화(Program), 응용 프로그램 런타임(Application Runtime), 시스템 런타임(System Runtime) 등 세 가지 주요 구성 요소가 포함되어 있습니다. 가운데 패널 (b)는 개발자가 Dynasor 내에서 다양한 추론 알고리즘을 정의할 수 있도록 하는 추론 프로그램 인터페이스(Reasoning Program Interface)에 대한 개요를 보여줍니다. 오른쪽 패널 (c)는 자기 일관성(Self-Consistency, SC) 알고리즘을 사용하는 추론 프로그램의 예를 보여줍니다. 이 예제는 certaindex를 업데이트하고 리소스를 할당하는 방법을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Left(a): Dynasor Architecture. Middle(b): Reasoning Program Interface. Right(c): Example Program (SC).
> </details>



![](https://arxiv.org/html/2412.20993/x7.png)

> 🔼 그림 7은 Dynasor 시스템의 Gang Scheduling의 효과를 보여줍니다. 두 프로그램이 동시에 도착하는 시나리오를 예시로, 각 프로그램은 두 개의 요청을 가지고 있습니다. 프로그램 1의 요청은 각각 4ms, 프로그램 2의 요청은 각각 5ms가 소요됩니다. 기존의 순차적 스케줄링 방식(오른쪽)은 프로그램 하나씩 순차적으로 처리하기 때문에 평균 대기 시간이 9ms가 됩니다. 하지만 Dynasor의 Gang Scheduling(왼쪽)은 같은 프로그램의 요청들을 묶어서 처리하기 때문에 평균 대기 시간을 6.5ms로 줄입니다. 이는 Gang Scheduling을 통해 대기 시간을 줄일 수 있음을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Illustration of Gang Scheduling
> </details>



![](https://arxiv.org/html/2412.20993/x8.png)

> 🔼 그림 8은 배치 처리 작업량에 대한 토큰-정확도 측정값을 보여줍니다.  x축은 사용된 토큰의 수(백만 단위)이고 y축은 달성된 정확도입니다. 각 알고리즘(SC, MCTS, Rebase)과 데이터셋(GSM8K, LiveCodeBench, MATH) 조합에 대해, Dynasor(본 논문에서 제안하는 시스템)의 성능과 기준 시스템(Baseline-even, Baseline-length)의 성능을 비교하여 나타냅니다.  Baseline-even은 모든 쿼리에 동일한 양의 토큰을 할당하는 반면, Baseline-length는 쿼리의 난이도에 따라 토큰을 할당합니다.  10회 반복 실험의 평균 성능과 표준 편차(에러 바)가 표시되어 있습니다. Dynasor는 기준 시스템에 비해 동일한 정확도를 유지하면서 사용된 토큰 수를 크게 줄이는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Token-to-accuracy metric on batch processing workloads. Mean performance and std (error bars) of 10 runs are reported.
> </details>



![](https://arxiv.org/html/2412.20993/x9.png)

> 🔼 그림 9는 Dynasor와 기준 시스템을 비교하여 세 가지 온라인 작업 부하에 대한 평가 결과를 보여줍니다. 위에서부터 아래로 (a) 프로그램 도착률 대비 SLO 달성률, (b) SLO 규모 대비 SLO 달성률, (c) 정확도 대비 SLO 달성률을 나타냅니다. Dynasor는 다양한 프로그램 도착률과 SLO 규모에서 기준 시스템보다 더 높은 SLO 달성률을 보이며, 제한된 리소스 내에서도 높은 정확도를 유지합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Evaluation on 3 online workloads on Dynasor against baselines. Rows from top to bottom: (a) Program arrival rate vs SLO attainment, (b) SLO scale vs SLO attainment, (c) Accuracy vs SLO Attainment.
> </details>



![](https://arxiv.org/html/2412.20993/x10.png)

> 🔼 그림 10은 온라인 셀프 일관성(GSM8K 작업)에서의 성능 향상을 보여줍니다.  초당 16개의 요청이라는 고정된 요청 속도에서 갱 스케줄링, certaindex 기반 리소스 할당, SJF(Shortest Job First)의 영향을 분석합니다. 이 그림은 각 기법이 평균 지연 시간에 미치는 영향을 보여주는 시각적 자료로, Dynasor 시스템의 각 구성 요소가 성능 향상에 어떻게 기여하는지 명확하게 이해하는 데 도움을 줍니다.  특히, certaindex 기반 리소스 할당과 갱 스케줄링의 중요성을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Performance improvement breakdown in online self-consistency (GSM8K) workload: Impact of gang scheduling, certaindex-based resource allocation, and SJF on mean latency given a fixed request rate of 16 pps.
> </details>



![](https://arxiv.org/html/2412.20993/x11.png)

> 🔼 그림 11은 고정된 P90 SLO 제약 조건 하에서 온라인 자기 일관성(MATH) 작업에 대한 성능 향상 분석을 보여줍니다.  이 그림은 Dynasor 시스템의 각 구성 요소(LPM, Gang 스케줄링, SJF, Certaindex 기반 리소스 관리)가 지연 시간 및 처리량 개선에 기여하는 정도를 보여주는 세부적인 분석 결과를 제공합니다.  각 구성 요소가 개별적으로 또는 결합하여 전체 시스템 성능에 미치는 영향을 정량적으로 비교하여 Dynasor의 효율성과 효과를 보여줍니다. 특히, Certaindex 기반 리소스 관리는 지연 시간을 최대 60%까지 줄이고 처리량을 1.2배 향상시키는 것으로 나타났습니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Performance improvement breakdown of online self-consistency (MATH) under fixed P90 SLO constraints.
> </details>



![](https://arxiv.org/html/2412.20993/x12.png)

> 🔼 그림 12는 다양한 엔트로피 임계값 또는 보상 점수 임계값을 사용하여 성능을 비교한 결과를 보여줍니다.  이 그림은 자세한 설명 없이도 다양한 알고리즘과 데이터셋에서 서로 다른 임계값 설정에 따른 모델의 성능 차이를 명확하게 보여줍니다.  특히, 특정 임계값을 사용했을 때 성능이 향상되거나 저하되는 현상을 시각적으로 확인할 수 있습니다. 각 그래프는 특정 알고리즘과 데이터셋에 대한 결과를 나타내며, x축은 토큰 수, y축은 정확도를 나타냅니다.  다양한 색상의 선은 서로 다른 임계값을 적용했을 때의 결과를 비교하여 보여줍니다.  이를 통해 연구자는 최적의 임계값을 선택하여 모델 성능을 최적화하는 데 도움을 받을 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Performance comparison with different entropy threshold or reward score threshold.
> </details>



![](https://arxiv.org/html/2412.20993/x13.png)

> 🔼 그림 13은 추론 과정에서 사용되는 자원 할당 전략을 비교 분석한 결과를 보여줍니다.  특히, LLM 활성화 기반 예측기와 출력 길이 기반 스케줄링 전략을 기존 방법과 비교하여 성능을 평가합니다.  그래프는 각 방법에 따른 정확도와 사용된 토큰 수의 관계를 보여주며, 제안된 Certaindex 기반 방법이 다른 방법들보다 더 높은 정확도를 더 적은 토큰으로 달성함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: Performance comparison with LLM activation-based predictor and output length based scheduling.
> </details>



![](https://arxiv.org/html/2412.20993/x14.png)

> 🔼 그림 14는 Dynasor 시스템의 공정성(fairness)을 보여줍니다.  특히, 각 프로그램의 처리 시간(latency)을 해당 프로그램이 사용한 토큰 수로 나눈 값(finish-time fairness)을 사용하여, 다양한 스케줄링 전략(certaindex 기반 리소스 할당, gang 스케줄링, SJF) 하에서의 공정성을 비교합니다. 이 그림은 Dynasor의 스케줄링 기법이 일부 프로그램의 과도한 지연을 방지하여 시스템의 전반적인 공정성을 개선함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: Finish-Time Fairness.
> </details>



![](https://arxiv.org/html/2412.20993/x15.png)

> 🔼 그림 15는 Dynasor을 사용하여 Qwen-QWQ 모델을 서비스하는 결과를 보여줍니다.  원래 Qwen-QWQ 모델은 긴 단일 CoT(Chain-of-Thought) 경로를 생성하고, 토큰 제한이 있을 때 결론에 도달하지 못하는 경우가 많아 토큰 대비 정확도 성능이 좋지 않았습니다. Dynasor는 각 반복마다 32개의 토큰을 생성하고 '최종 답변' 프롬프트를 추가하여 모델이 각 반복의 끝에서 답변을 도출하도록 유도함으로써 토큰 소비량을 30% 줄였습니다. 또한, Dynasor는 다양한 반복에서 나온 답변의 확신도(certaindex)를 모니터링하여, 확신도가 특정 임계값을 넘으면 생성을 중단하여 추가로 14%의 토큰 소비량 감소 효과를 얻었습니다. 이는 정확도를 유지하면서 효율적으로 최신 모델을 서비스할 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 15: Serving Qwen-QWQ using Dynasor.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| (Algo., Dataset, LLM) | Reward Model | # Samples | Resource Cap |
|---|---|---|---| 
| (SC, LCB, Llama3.1 8B) | / | 400 | 5,10,15,20,25,30 |
| (SC, GSM8K, Llama3.1 8B) | / | 1000 | 5,10,15,20,25,30 |
| (MCTS, ASDiv, Llama2 7B) | Skywork 7B | 300 | 3,7,10,15,20 |
| (MCTS, GSM8K, Llama2 7B) | Skywork 7B | 300 | 3,7,10,15,20 |
| (Rebase, MATH, Llemma 7B) | Llemma 34b | 500 | 16,32,64,128 |
| (Rebase, GSM8K, Llemma 34B) | Llemma 34b | 500 | 16,32,64,128 |{{< /table-caption >}}
> 🔼 표 2는 오프라인 작업 환경 설정을 보여줍니다. LiveCodeBench(LCB), Llama 2 7B, Skywork 7B, LLaMA 7B 및 34B는 LLM/보상 모델로 다양한 설정에서 미세 조정된 모델입니다. 각 행은 특정 알고리즘(SC, MCTS, Rebase), 데이터 세트(MATH, GSM8K, LiveCodeBench, ASDiv) 및 LLM/보상 모델에 대한 하이퍼파라미터 구성을 나타냅니다.  'Reward Model', '# Samples', 'Resource Cap' 열은 각 설정에 사용된 보상 모델, 샘플 수 및 리소스 상한을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Offline workload Configurations. LiveCodeBench (LCB), Llama2 7B [12], Skywork7B [35], Llemma 7B and 34B [51] are fine-tuned models used in different settings as LLM/reward model.
> </details>

{{< table-caption >}}
| Algorithm | Dataset | LLM | Reward Model | Base Deadline (s) |
|---|---|---|---|---|
| SC | MATH | Llama3.1 8B | / | 240 |
| MCTS | ASDiv | Llama2 7B | Skywork 7B | 60 |
| Rebase | GSM8K | Llemma 34B | Llemma 34b | 300 |{{< /table-caption >}}
> 🔼 표 3은 논문의 온라인 실험 환경 설정을 보여줍니다.  각 알고리즘(Self-Consistency, Monte Carlo Tree Search, Rebase), 데이터셋(GSM8K, ASDiv, MATH), 그리고 사용된 언어 모델(Llama 2 7B, Skywork 7B, Llemma 34B)별로 온라인 추론 작업에 대한 구성 정보를 제공합니다.  특히, 각 작업에 대한 보상 모델, 기본 마감 시간(초 단위) 등 세부 설정을 포함하여 실험의 재현성을 높입니다.  이 표는 실험 설정의 자세한 내용을 이해하는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Online workload Configurations
> </details>

{{< table-caption >}}
| Allocation Method | SC/MATH | MCTS/ASDiv |
|---|---|---|
| Baseline | 1.18M | 354K |
| Static Thres. (Ours) | 1.05M (-11.0%) | 308K (-13.0%) |
| + Initial Step Curve Fit.(Ours) | 1.04M (-11.9%) | 306K (-13.6%) |
| + 5-Step Thres. (Ours) | 1.03M (-12.7%) | 307K (-13.3%) |
| + Single-Step Thres. (Ours) | 1.03M (-12.7%) | 306K (-13.6%) |
| + Dynamic Curve Fitting (Ours) | 1.01M (-14.4%) | 298K (-15.8%) |{{< /table-caption >}}
> 🔼 표 4는 정확도를 유지하면서 다양한 스케줄링 전략을 사용했을 때 토큰 소비량을 비교한 표입니다.  여기에는 기준(Baseline) 성능과 Dynasor 시스템의 여러 가지 스케줄링 방법(Static Thres., Initial Step Curve Fit., 5-Step Thres., Single-Step Thres., Dynamic Curve Fitting)에 대한 결과가 포함되어 있습니다.  각 방법에 대한 SC/MATH 및 MCTS/ASDiv 작업에 대한 토큰 소비량(단위: 백만)이 제시되어 있으며, 기준선 대비 성능 향상률이 백분율(%)로 표시됩니다.  이 표는 Dynasor 시스템의 다양한 스케줄링 전략을 비교 분석하고, 각 전략의 효율성을 정량적으로 평가하는 데 도움을 줍니다. 특히, 정확도를 유지하면서 토큰 소비량을 최소화하는 최적의 스케줄링 전략을 선택하는 데 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Token consumption comparison of different scheduling strategies while maintaining accuracy
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