---
title: "Evolving Deeper LLM Thinking"
summary: "마음 진화(Mind Evolution)는 대규모 언어 모델(LLM)의 추론 시간 컴퓨팅을 확장하기 위한 새로운 진화적 검색 전략입니다. 이 전략은 형식적인 솔버 없이도 자연어 계획 문제에서 98% 이상의 문제를 해결하는 탁월한 성능을 보여줍니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Google DeepMind",]
showSummary: true
date: 2025-01-17
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.09891 {{< /keyword >}}
{{< keyword icon="writer" >}} Kuang-Huei Lee et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-20 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.09891" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.09891" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/evolving-deeper-llm-thinking" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)은 다양한 문제 해결에 활용되지만, 복잡한 문제에 대한 추론 능력 향상이 중요한 과제입니다.  기존 연구에서는 사고 연쇄(chain-of-thought), 자기 일관성(self-consistency), 순차적 수정(sequential revision) 등의 전략이 제시되었지만, 추가적인 연산을 효율적으로 활용하는 데 한계가 있었습니다. 특히, 해결책 평가자가 있을 때 검색 전략이 유리하지만, 모든 문제가 공식적으로 정의될 수 있는 것은 아닙니다. 

본 연구는 이러한 문제점을 해결하기 위해 LLM을 사용하여 후보 답변을 생성, 재조합 및 개선하는 새로운 진화적 검색 전략인 마음 진화(Mind Evolution)를 제시합니다. 마음 진화는 형식적 솔버 없이도 자연어 계획 문제에서 탁월한 성능을 보이며, 기존의 Best-of-N 및 순차적 수정 전략보다 월등한 성능을 보여줍니다.  특히, TravelPlanner와 Natural Plan 벤치마크에서 98% 이상의 문제를 해결하는 성과를 거두었습니다. 이는 LLM의 추론 시간 컴퓨팅을 효과적으로 활용하여 문제 해결 능력을 향상시킬 수 있음을 보여줍니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 마음 진화(Mind Evolution)는 LLM의 추론 시간 계산을 확장하는 새로운 진화적 검색 전략 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 자연어 계획 문제에서 기존 방법보다 우수한 성능을 보임 (TravelPlanner 및 Natural Plan 벤치마크에서 98% 이상의 문제 해결) {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 형식적인 솔버 없이도 복잡한 자연어 계획 문제 해결 가능 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대규모 언어 모델(LLM)의 추론 시간 계산을 확장하기 위한 새로운 진화적 검색 전략인 마음 진화(Mind Evolution)**을 제시하여 자연어 계획 문제에서 뛰어난 성능을 달성한 연구입니다.  LLM의 문제 해결 능력을 향상시키는 데 있어 추론 시간 계산의 중요성을 강조하고, 형식적 솔버 없이도 복잡한 문제를 해결할 수 있는 새로운 방법을 제시함으로써 **향후 연구에 대한 새로운 가능성을 열어줍니다.**  특히, 형식적인 솔버가 필요하지 않은 자연어 처리 분야에서 큰 영향을 미칠 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.09891/x1.png)

> 🔼  그림 1은 자연어 공간에서 작동하는 유전자 기반 진화형 검색 전략인 Mind Evolution을 보여줍니다. 이 그림은 여행 계획 작업에 대해 Mind Evolution이 더 높은 품질의 후보 솔루션으로 후보 솔루션 집단을 어떻게 진화시키는지 보여줍니다.  Mind Evolution은 각 반복에서 LLM을 사용하여 후보 솔루션을 재결합하고 개선하는 반복적인 프로세스를 통해 후보 솔루션 집단을 개선합니다.  그림은 후보 솔루션 생성, 평가, 재결합 및 개선의 과정을 시각적으로 보여줍니다.  각 단계에서 LLM이 어떻게 사용되는지 자세히 설명합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Mind Evolution is a genetic-based evolutionary search strategy that operates in natural language space. The figure illustrates how Mind Evolution evolves a population of solution candidates toward higher quality candidates for a travel planning task. The candidate population is improved through an iterative process, where an LLM is used to recombine and refine candidates in each iteration.
> </details>





{{< table-caption >}}
| Parameter | Default Value | Description |
|---|---|---|
| $N_{\text{gens}}$ | 10 | The maximum number of generations to search for a solution. |
| $N_{\text{island}}$ | 4 | How many independent populations to evolve. |
| $N_{\text{convs}}$ | 5 | How many conversations per island. |
| $N_{\text{seq}}$ | 4 | How many turns per conversation. |
| $N_{\text{reset interval}}$ | 3 | How frequently to reset islands in generations. |
| $N_{\text{reset}}$ | 2 | How many islands to reset. Lowest mean score islands are chosen. |
| $N_{\text{top}}$ | 5 | How many starting parents to transfer to islands when reset. |
| $N_{\text{candidate}}$ | 15 | How many candidate parents to consider when resetting islands with the LLM. |
| $N_{\text{parent}}$ | 5 | Maximum number of parents a conversation can have. |
| $Pr_{\text{no parents}}$ | 1/6 | Probability of a conversation having no parents. |
| $N_{\text{emigrate}}$ | 5 | How many plans to emigrate to the next island after each island. |
| $N_{\text{retries}}$ | 5 | How many times to try to generate a plan before giving up at each turn. |{{< /table-caption >}}

> 🔼 본 표는 Mind Evolution 알고리즘에서 사용되는 하이퍼파라미터들을 정의하고 있습니다. 각 하이퍼파라미터의 기본값과 역할에 대한 설명을 제공하며, 논문에서 수행된 실험들에서 별도로 명시되지 않은 경우 기본값들이 사용되었음을 밝히고 있습니다. 특히, 앞의 네 개 하이퍼파라미터의 곱은 생성되는 후보 솔루션의 최대 개수를 나타내며, 기본 설정에서는 800개의 후보 솔루션이 생성됩니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Definition of hyperparameters in Mind Evolution. Unless otherwise specified, the experiments in work use the default values. The product of the first four hyperparameters gives the maximum number of candidate solutions generated (800 in the default setting).
> </details>





### In-depth insights


#### LLM Evolutionary Search
LLM 진화적 탐색은 **대규모 언어 모델(LLM)의 추론 시간을 확장하여 복잡한 문제 해결 능력을 향상시키는 새로운 전략**입니다. 기존의 Best-of-N이나 순차적 수정과 같은 방법과 달리, LLM 진화적 탐색은 LLM을 이용해 후보 답변을 생성, 재결합, 개선하는 과정을 거치며, 형식적인 문제 정의 없이도 해결책 평가자가 있으면 효과적으로 작동합니다. 이는 **자연어 처리 분야에서 특히 유용**하며, 여행 계획 수립이나 자연어 계획과 같이 형식화하기 어려운 문제에 적용 가능합니다. **진화 알고리즘을 기반**으로 하며, 다양한 후보 솔루션들을 생성하고, 평가자의 피드백을 통해 우수한 솔루션들을 선택, 재결합하여 진화시켜 나갑니다. 이러한 접근 방식은 **병렬 처리가 용이**하며, LLM의 자연어 이해 및 생성 능력을 최대한 활용하여 효율적인 탐색을 수행합니다. **형식적 솔버 없이도 높은 정확도**를 달성할 수 있다는 점이 가장 큰 장점입니다. 다만, **솔루션 평가자의 정확성에 대한 의존도가 높다**는 점은 향후 연구에서 개선될 필요가 있습니다.

#### Mind Evolution Algorithm
마음 진화 알고리즘은 **LLM(대규모 언어 모델)의 추론 시간 연산을 확장하기 위해 진화적 검색 전략을 사용하는 혁신적인 방법**입니다. 이 알고리즘은 LLM을 사용하여 후보 답변을 생성, 재결합 및 개선하는 반복적인 과정을 통해 작동합니다.  **기존의 최적화 전략과 달리, 형식적인 솔버(solver) 없이도 자연어 계획 문제를 효과적으로 해결**할 수 있습니다. 이는 문제 해결 과정을 형식화할 필요 없이 평가자(evaluator)가 사용 가능한 경우에 특히 유용합니다. 마음 진화 알고리즘은 **자연어 생성, 재결합 및 개선의 3단계 과정**을 통해 작동하며, 이는 발산적 사고와 수렴적 사고를 결합하여 지능적인 문제 해결 행동을 모방합니다.  **병렬 처리가 용이하여 효율적인 연산이 가능**하며, 다양한 문제 유형에 적용 가능한 유연성을 제공합니다.  **여러 실험 결과를 통해 기존 방법 대비 성능 향상을 확인**하였으며, 특히 여행 계획 및 자연어 계획 작업에서 탁월한 성능을 보였습니다.  **향후 연구는 형식적 모델링이 어려운 문제 유형에도 적용 가능성을 확대**하는 데 초점을 맞출 것으로 보이며, 다양한 분야에서의 응용 가능성을 높일 수 있을 것입니다.

#### Natural Language Planning
자연어 계획(Natural Language Planning)은 **대규모 언어 모델(LLM)**이 자연어로 표현된 복잡한 문제를 해결하는 능력을 향상시키는 데 중점을 둡니다.  이 분야는 **형식적인 솔루션 평가자**가 있을 때 효과적인 전략을 제시합니다.  기존의 Best-of-N이나 순차적 수정과 같은 방법론은 제한적이지만,  **진화적 검색** 전략은 더욱 심층적이고 효율적인 추론을 가능하게 합니다.  LLM을 이용하여 후보 솔루션을 생성, 재결합, 개선하는 과정은 **인간의 사고 과정**을 모방하며,  문제를 형식화하지 않고도 해결책을 도출할 수 있습니다.  특히 여행 계획이나 자연어 계획과 같은 실제 문제에서 **뛰어난 성능**을 보이는데,  이는 **제약 조건 만족 문제**를 자연어로 표현하는 데서 기존 방법론의 한계를 극복하기 때문입니다.  향후 연구는 **LLM 기반 평가자** 개발을 통해 자연어 계획의 적용 범위를 더욱 넓히는 데 초점을 맞출 것입니다.

#### Benchmark Results Analysis
본 논문의 벤치마크 결과 분석 부분에서는 제안된 방법의 성능을 기존 방법들과 비교하여 **정량적 및 정성적 분석**을 통해 심층적인 통찰력을 제공할 것으로 예상됩니다.  **정량적 분석**은 정확도, 효율성, 실행 시간 등의 객관적인 지표를 사용하여 제안된 방법의 우수성을 수치적으로 입증하는 데 초점을 맞출 것입니다.  **정성적 분석**은 다양한 벤치마크 작업에서의 성능 차이에 대한 이유를 설명하고, 제안된 방법의 장단점과 한계를 명확하게 밝히는 데 중점을 둘 것입니다. 특히, **실험 결과의 해석**에 있어서는 통계적 유의성 검증을 통해 결과의 신뢰성을 확보하고, **다양한 변수** (예: 데이터 크기, 모델 크기 등)의 영향을 분석하여 제안된 방법의 일반화 가능성을 평가할 것입니다.  아울러, **향후 연구 방향**을 제시하여 본 연구의 한계점을 극복하고, 제안된 방법의 실용성을 더욱 높일 수 있는 방안을 모색할 것입니다.  결론적으로, 이 부분은 제안된 방법의 실제적인 효용성을 객관적이고 명확하게 보여주는 동시에,  **연구의 학문적 기여도**를 높이는 중요한 역할을 수행할 것으로 기대됩니다.

#### Future Research Scope
본 논문에서 제시된 Mind Evolution 알고리즘은 자연어 처리 문제 해결에 있어 상당한 성과를 보였지만, **향후 연구는 몇 가지 중요한 방향**으로 확장될 필요가 있습니다.  먼저, **현재 자연어 계획 문제에 초점**을 맞추고 있으므로, **다양한 문제 영역으로의 확장**이 필요합니다.  예를 들어, 코드 생성, 수학 문제 풀이, 논리적 추론 등 다양한 분야에서 Mind Evolution의 적용 가능성을 검토하고, 각 분야에 맞는 평가 지표 및 최적화 전략을 개발해야 합니다.  또한, **LLM 기반 평가자**를 개발하여 보다 광범위하고 견고한 평가 시스템을 구축하는 것이 중요하며, 이를 통해 Mind Evolution의 범용성을 더욱 높일 수 있을 것입니다.  **추가적으로, 다양한 LLM 모델**과의 호환성을 강화하고,  **계산 비용 최적화**를 위한 효율적인 알고리즘 개발도 중요한 연구 과제입니다.  마지막으로, Mind Evolution 알고리즘의 이론적 기반을 더욱 확립하고, **알고리즘의 성능을 제약하는 요인**들을 심층적으로 분석하는 연구를 통해 알고리즘의 성능 향상을 도모해야 할 것입니다.  이러한 노력을 통해 Mind Evolution은 더욱 강력하고 범용적인 문제 해결 도구로 발전할 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.09891/x2.png)

> 🔼 그림 2는 자연어 계획 문제에 대한 솔루션을 개선하는 반복적인 과정인 RCC(Refinement through Critical Conversation) 프로세스를 보여줍니다.  먼저 언어 모델이 초기 솔루션을 생성하고, 이 솔루션이 평가되면 비평가(Critic) 역할을 하는 언어 모델이 피드백을 제공합니다. 그런 다음, 작성자(Author) 역할을 하는 언어 모델이 이 피드백을 바탕으로 개선된 솔루션을 제안합니다. 이러한 비평가와 작성자 간의 대화를 통해 솔루션이 점진적으로 개선되어 가는 과정이 반복됩니다. 이 그림은 Mind Evolution 방법론의 핵심 구성 요소 중 하나인 RCC 프로세스를 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Illustrating the Refinement through Critical Conversation (RCC) process, where an initial solution is first proposed, then evaluated and subjected to feedback from a critic, after which an author proposed a refined solution and the process iterates.
> </details>



![](https://arxiv.org/html/2501.09891/x3.png)

> 🔼 그림 3은 TravelPlanner 벤치마크의 검증 세트에 대한 성공률을 보여줍니다. 문제 인스턴스의 난이도와 여행 일수에 따라 성공률을 분류하여 보여줍니다.  세 가지 난이도(쉬움, 중간, 어려움)와 세 가지 여행 기간(3일, 5일, 7일)에 따른 성공률을 비교 분석하여, 문제의 복잡성과 여행 기간이 성공률에 미치는 영향을 시각적으로 보여줍니다.  각 범주에 대한 성공률을 통해 Mind Evolution을 포함한 다양한 추론 전략의 성능을 비교 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Success rate on the validation set of the TravelPlanner benchmark, organized by problem instance difficulty and the number of travel days.
> </details>



![](https://arxiv.org/html/2501.09891/x4.png)

> 🔼 그림 4는 Trip Planning 벤치마크의 검증 세트에서 방문할 도시 수에 따른 성공률을 보여줍니다.  다시 말해, 여행 계획을 세울 때 방문할 도시의 수가 증가함에 따라 각 방법의 성공률이 어떻게 달라지는지를 보여주는 그래프입니다.  x축은 방문 도시의 수이고 y축은 성공률입니다.  여러 다른 계획 생성 전략(Mind Evolution, Sequential-Revision+, Best-of-N, 1-Pass)의 성공률을 비교하여 도시 수 증가에 따른 각 전략의 성능 변화를 시각적으로 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Success rate on the validation set of the Trip Planning benchmark per number of cities to visit.
> </details>



![](https://arxiv.org/html/2501.09891/x5.png)

> 🔼 그림 5는 여러 명의 사람들을 만나는 미팅 계획 수립 과제에 대한 검증 세트의 성공률을 보여줍니다. 성공률은 만나야 할 사람 수에 따라 달라집니다. 이 그래프는 다양한 수의 사람들을 만나는 미팅 계획 수립 문제에 대한 Mind Evolution 알고리즘의 성능을 보여주는 시각적 자료입니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Success rate on the validation set of the Meeting Planning benchmark per number of people to meet with.
> </details>



![](https://arxiv.org/html/2501.09891/x6.png)

> 🔼 그림 6은 Mind Evolution의 각 세대에서 자연어 계획 벤치마크에 대한 검증 세트의 성공률을 보여줍니다.  각 그래프는 TravelPlanner, Trip Planning, Meeting Planning 세 가지 벤치마크 작업에 대한 성공률을 나타내며, Mind Evolution 알고리즘이 진행됨에 따라 세대가 거듭될수록 성공률이 어떻게 변화하는지 보여줍니다. 이를 통해 Mind Evolution 알고리즘의 성능과 안정성을 시각적으로 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Success rate on the validation set for each natural language planning benchmark at each generation of Mind Evolution.
> </details>



![](https://arxiv.org/html/2501.09891/x7.png)

> 🔼 그림 7은 TravelPlanner 작업에서 후보 솔루션의 수가 증가함에 따라 성공률과 평가 점수가 어떻게 변하는지 보여줍니다.  x축은 생성된 후보 솔루션의 수를 나타내고, y축은 성공률과 평균 평가 점수를 나타냅니다. 이 그래프는 Mind Evolution, 순차적 수정+, Best-of-N 세 가지 방법의 성능을 비교하여 Mind Evolution이 다른 방법들보다 훨씬 더 높은 성공률과 더 높은 평균 평가 점수를 달성했음을 보여줍니다. 특히, 후보 솔루션의 수가 증가함에 따라 Mind Evolution의 성공률과 평가 점수가 꾸준히 향상되는 것을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: TravelPlanner success rates and evaluation scores as the number of candidate solutions is increased.
> </details>



![](https://arxiv.org/html/2501.09891/x8.png)

> 🔼 그림 8은 여행 계획 문제에 대한 다양한 솔루션 후보들을 생성하여 평가했을 때, 성공률과 평균 평가 점수가 후보 솔루션 개수에 따라 어떻게 변화하는지를 보여줍니다.  단순히 모델을 한번만 실행하는 1-Pass 방식이나, 여러 번 수정하는 순차적 수정 방식, 그리고 최고 N개의 결과만 선택하는 Best-of-N 방식과 비교하여, Mind Evolution 방식이 더 높은 성공률과 평균 평가 점수를 달성했음을 시각적으로 보여줍니다.  후보 솔루션의 개수가 증가함에 따라 성공률과 평균 평가 점수가 향상되는 경향을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Trip Planning success rates and evaluation scores as the number of candidate solutions is increased.
> </details>



![](https://arxiv.org/html/2501.09891/x9.png)

> 🔼 그림 9는 Meeting Planning 작업에서 후보 솔루션의 수가 증가함에 따라 성공률과 평가 점수가 어떻게 변하는지 보여줍니다.  다양한 검색 전략(Mind Evolution, 순차적 수정, Best-of-N)의 성능을 비교하여 Mind Evolution이 더 많은 후보 솔루션을 생성할 때 더 높은 성공률과 평가 점수를 달성함을 보여줍니다. 이는 Mind Evolution이 문제 해결에 효과적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Meeting Planning success rates and evaluation scores as the number of candidate solutions is increased.
> </details>



![](https://arxiv.org/html/2501.09891/x10.png)

> 🔼 그림 10은 StegPoet 문제의 예시를 보여줍니다. 왼쪽에는 StegPoet 문제의 인스턴스가, 오른쪽에는 숫자-단어 암호와 어린이 동시 작가 스타일의 시가 포함된 정답이 나와 있습니다. 그림에서 보이는 숨겨진 메시지(M)의 길이는 12입니다. 암호 단어를 강조하기 위해 대문자를 사용했습니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: StegPoet example. Example of the encoding of a StegPoet problem instance (left) and a correct solution (right) that includes the number-to-word cipher and a poem in the style of a children’s poetry author. Note that |M|=12𝑀12|M|=12| italic_M | = 12 in this instance. We added capitalization to the code words to highlight them.
> </details>



![](https://arxiv.org/html/2501.09891/extracted/6137017/ct1_v1.png)

> 🔼 그림 11은 StegPoet 과제의 각 난이도 수준에 대한 성공률 히스토그램을 보여줍니다. 성공률은 각 난이도 수준에서 Mind Evolution 알고리즘이 문제를 성공적으로 해결한 비율을 나타냅니다. 1-Pass 방법은 유효한 응답을 반환하지만 문제를 해결하지 못하므로 히스토그램에 표시되지 않습니다. 이 히스토그램은 Mind Evolution 알고리즘의 성능이 난이도 수준에 따라 어떻게 달라지는지 보여주는 시각적 자료입니다.  난이도 수준은 숨겨진 메시지의 길이, 메시지 내 숫자의 반복, 반복되는 숫자 사이의 근접성, 그리고 암호 단어 사이의 평균 단어 간격과 같은 요소에 따라 결정됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 11:  Histogram of Success Rate for each difficulty level. 1-Pass returns valid responses, but fails to solve any of the problems, so it is not visible in the histogram.
> </details>



![](https://arxiv.org/html/2501.09891/extracted/6137017/ct2_v1.png)

> 🔼 그림 12는 논문의 방법론 섹션에 있는 그림으로, 자연어 계획 문제에 대한 ‘마음 진화(Mind Evolution)’ 방법을 설명합니다.  특히 회의 계획(Meeting Planning) 과제를 예시로 들어, 언어 모델(LLM)에 제시하는 프롬프트와 이전 해결책(parent solutions)을 보여줍니다.  프롬프트는 일반적인 지침, 몇 가지 예시, 작업에 대한 설명, 그리고 평가와 함께 피드백을 제공하는 이전의 솔루션으로 구성되어 있습니다. 이 그림은 LLM이 어떻게 문제를 이해하고, 이전 해결책으로부터 학습하며, 새로운 해결책을 생성하는지를 보여주는 첫 번째 단계를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Example Meeting Planning prompt and model response with parent solutions given (Part 1)
> </details>



![](https://arxiv.org/html/2501.09891/extracted/6137017/ct3_v1.png)

> 🔼 그림 13은 논문의 방법 섹션에 있는 그림으로, 대규모 언어 모델(LLM)을 사용하여 미팅 계획 문제를 해결하는 과정을 보여줍니다. 그림은 미팅 계획 문제에 대한 설명과 이전에 생성된 솔루션, 평가 피드백을 보여주며, 이를 바탕으로 LLM이 새로운 솔루션을 생성하고 개선하는 과정을 단계별로 보여줍니다. 즉, LLM이 이전 솔루션의 문제점을 분석하고 개선된 솔루션을 제시하는 반복적인 과정을 보여줍니다. 이 과정은 자연어로 진행되며, LLM이 생성한 솔루션은 평가 함수를 통해 평가됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: Example Meeting Planning prompt and model response with parent solutions given (Part 2)
> </details>



![](https://arxiv.org/html/2501.09891/extracted/6137017/ct4_v1.png)

> 🔼 그림 14는 논문의 방법론 섹션에 있는 그림으로, 자연어 계획 문제에 대한 ‘마음 진화(Mind Evolution)’ 전략을 보여줍니다. 특히 회의 계획 문제를 예시로 들어, 언어 모델이 이전에 생성된 솔루션(부모 솔루션)과 평가 피드백을 사용하여 새로운 솔루션을 생성하고 개선하는 과정을 보여줍니다. 그림은 ‘비판적 대화를 통한 개선(Refinement through Critical Conversation, RCC)’이라는 과정을 중심으로, 비판적인 역할과 생성적인 역할을 하는 두 개체(Jane 과 John)의 대화 형식을 통해 솔루션이 점진적으로 개선되는 모습을 보여줍니다. 이를 통해 언어 모델이 생성한 솔루션의 질을 향상시키는 방법을 시각적으로 보여주는 것이 그림 14의 주요 목적입니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: Example Meeting Planning prompt and model response with parent solutions given (Part 3)
> </details>



![](https://arxiv.org/html/2501.09891/extracted/6137017/ct5_v1.png)

> 🔼 그림 15는 논문의 '방법' 섹션에 있는 그림으로, 회의 계획 문제에 대한 자연어 프롬프트와 모델 응답을 보여줍니다. 이 그림은 부모 솔루션(이전에 생성된 솔루션)과 함께 제공된 프롬프트의 일부분을 보여주며, 비판적 사고 지침에 따라 모델이 부모 솔루션을 개선하는 과정을 보여줍니다. 그림은 '비판가'와 '저자'라는 두 가지 역할을 수행하여 비판적 사고 능력을 향상시키는 방법을 보여줍니다. 비판가는 제공된 솔루션을 분석하고 평가하여 문제점을 지적하고 개선 방안을 제시하며, 저자는 비판가의 분석을 바탕으로 개선된 솔루션을 제안합니다. 그림은 이러한 과정을 반복하여 최종 솔루션에 도달하는 과정을 보여줍니다. 이 그림은 4번째 부분을 보여주는 일련의 그림 중 하나입니다.
> <details>
> <summary>read the caption</summary>
> Figure 15: Example Meeting Planning prompt and model response with parent solutions given (Part 4)
> </details>



![](https://arxiv.org/html/2501.09891/extracted/6137017/tp1.png)

> 🔼 그림 16은 논문의 방법론 섹션에 있는 그림으로, 자연어 계획 문제에 대한 대규모 언어 모델의 추론 능력을 향상시키는 방법인 마인드 에볼루션(Mind Evolution) 알고리즘을 보여줍니다.  구체적으로, 회의 계획 과제에 대해 이전에 생성된 솔루션(부모 솔루션)과 해당 평가 피드백이 주어진 상태에서, LLM이 부모 솔루션을 개선하는 방법을 보여줍니다. 그림은 LLM이 비판가(Critic)와 저자(Author)의 역할을 번갈아 수행하며, 반복적인 대화를 통해 솔루션을 다듬는 과정을 시각적으로 나타냅니다. 이를 통해 최종적으로 더 나은 품질의 솔루션에 도달하는 과정을 보여주는 예시입니다.  본 그림은 '마인드 에볼루션' 알고리즘의 반복적 개선 과정을 설명하는 다섯 번째 부분입니다.
> <details>
> <summary>read the caption</summary>
> Figure 16: Example Meeting Planning prompt and model response with parent solutions given (Part 5)
> </details>



![](https://arxiv.org/html/2501.09891/extracted/6137017/tp2.png)

> 🔼 그림 17은 TravelPlanner 작업에 대한 Mind Evolution의 프롬프트와 모델 응답의 예시를 보여줍니다. 여기에는 이전에 제안된 솔루션과 해당 문제점이 포함되어 있습니다. 이 그림은 논문의 방법론 부분에 자세히 설명된 Mind Evolution 알고리즘의 작동 방식을 보여주는 데 도움이 됩니다. 특히, LLM(대규모 언어 모델)을 사용하여 여행 계획을 생성하고 개선하는 방법과 평가 함수를 사용하여 생성된 계획의 품질을 평가하는 방법을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 17: Example TravelPlanner prompt and model response with parent solutions given (Part 1)
> </details>



![](https://arxiv.org/html/2501.09891/extracted/6137017/tp3.png)

> 🔼 그림 18은 논문의 TravelPlanner 부분에 있는 예시입니다. 사용자의 질문과 이전에 생성된 답변들을 보여주는 프롬프트와 모델의 응답을 보여줍니다. 이 그림은 Mind Evolution이 어떻게 작동하는지 보여주는 일련의 그림들 중 두 번째 그림입니다. 이 그림에서는 여행 계획을 세우는 작업에 대한 사용자의 질문과, 모델이 이전에 생성한 답변들에 대한 피드백이 포함되어 있습니다.  모델은 이 피드백을 사용하여 개선된 답변을 생성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 18: Example TravelPlanner prompt and model response with parent solutions given (Part 2)
> </details>



![](https://arxiv.org/html/2501.09891/extracted/6137017/tp4.png)

> 🔼 그림 19는 TravelPlanner 벤치마크에서 Mind Evolution의 성능을 보여주는 예시입니다. 사용자 질의와 이전에 제안된 답변(부모 솔루션)과 함께 제시된 프롬프트와 모델 응답을 보여줍니다. 이 그림은 Mind Evolution이 이전 솔루션의 문제점을 분석하고 개선된 솔루션을 생성하는 과정을 보여줍니다. 부모 솔루션의 문제점이 지적되고, 이를 해결하기 위한 구체적인 제안이 제시됩니다. 또한, 개선된 여행 계획을 위한 프롬프트와 수정된 여행 계획이 제시됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 19: Example TravelPlanner prompt and model response with parent solutions given (Part 3)
> </details>



![](https://arxiv.org/html/2501.09891/extracted/6137017/tp5.png)

> 🔼 그림 20은 여행 계획 세우기 문제에 대한 Mind Evolution의 프롬프트와 모델 응답을 보여주는 그림의 네 번째 부분입니다. 이 그림은 이전에 제안된 계획과 해당 문제점을 보여주는 부모 솔루션과 함께 제공됩니다. 부모 솔루션을 개선하는 방법에 대해 설명하는 비판적인 사고 지침이 포함되어 있습니다. 이 비판적인 사고 지침은 문제에 대한 전략적 질문을 포함하며, 모델이 부모 솔루션의 강점과 약점을 분석하고, 문제점을 해결하는 개선된 솔루션을 생성하도록 안내합니다. 이 그림은 Mind Evolution 알고리즘의 반복적 개선 프로세스를 시각적으로 보여주는 중요한 부분입니다.
> <details>
> <summary>read the caption</summary>
> Figure 20: Example TravelPlanner prompt and model response with parent solutions given (Part 4)
> </details>



![](https://arxiv.org/html/2501.09891/extracted/6137017/tp6.png)

> 🔼 그림 21은 TravelPlanner 문제에 대한 Mind Evolution의 작동 과정을 보여주는 예시입니다. 사용자의 여행 계획 요청과 이전에 생성된 계획(parent solutions) 및 해당 계획에 대한 평가 결과가 제시됩니다.  이전 계획의 문제점을 지적하고 개선된 계획을 제안하는 비평가(critic)와 개선된 계획을 제시하는 작성자(author)의 역할을 LLM이 수행하는 과정을 보여줍니다.  그림은 Mind Evolution에서 LLM이 생성, 재결합, 개선을 통해 해결책을 발전시키는 과정을 자세하게 설명합니다.  전체 과정은 자연어로 이루어지며, 공식적인 솔버 없이도 문제 해결에 접근하는 방식을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 21: Example TravelPlanner prompt and model response with parent solutions given (Part 5)
> </details>



![](https://arxiv.org/html/2501.09891/x11.png)

> 🔼 그림 22는 TravelPlanner 문제에 대한 Mind Evolution의 작동 방식을 보여주는 예시입니다. 이전에 제안된 솔루션과 그에 대한 평가 결과를 바탕으로, 비판적 사고 과정을 거쳐 개선된 여행 계획을 생성하는 과정을 보여줍니다. 그림에서는 LLM이 비판자와 저자의 역할을 번갈아 수행하며, 평가 피드백에 따라 여행 계획을 수정하는 대화 형식을 사용합니다. 최종적으로는 예상보다 개선된 여행 계획이 생성됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 22: Example TravelPlanner prompt and model response with parent solutions given (Part 6)
> </details>



![](https://arxiv.org/html/2501.09891/x12.png)

> 🔼 그림 23은 논문의 방법 섹션에 있는 그림으로, 자연어 계획 문제에 대한 미팅 계획 평가 함수의 첫 번째 부분을 보여줍니다. 이 함수는 제안된 계획의 품질을 평가하고 문제점을 지적하는 역할을 합니다. 자연어로 작성된 계획을 입력받아, 시간 제약 조건과 미팅 시간 충족 여부를 확인하고 점수를 매깁니다. 또한, 시간 형식 오류나 이전 단계와 시간적 모순과 같은 문제점을 감지하여 피드백 메시지를 생성합니다. 그림은 함수의 일부분만 보여주며, 전체 함수는 코드로 구현되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 23: The Meeting Planning evaluation function (part 1).
> </details>



![](https://arxiv.org/html/2501.09891/x13.png)

> 🔼 그림 24는 논문의 3장에 있는 '방법론' 섹션의 일부분으로,  Meeting Planning 작업에 대한 평가 함수의 두 번째 부분을 보여줍니다. 이 함수는 자연어로 작성된 계획의 품질을 평가하고, 각 단계에 대한 점수를 계산하며, 제약 조건 위반이나 최적화 목표 달성 실패 등의 문제점을 자세히 설명하는 피드백을 제공합니다. 코드는 계획의 각 단계를 순차적으로 처리하여 시간 제약 조건을 확인하고, 참석자의 일정과의 충돌을 감지하며, 미팅 시간 충족 여부 등을 평가합니다.  함수는 최종 점수와 문제점에 대한 상세한 설명을 반환합니다.
> <details>
> <summary>read the caption</summary>
> Figure 24: The Meeting Planning evaluation function (part 2).
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
TravelPlanner [42]

| 1-Pass | Set | Success Rate | LLM Calls | Input Tokens | Output Tokens | API Cost (Oct 2024) |
|---|---|---|---|---|---|---|
| 1-Pass | val | 10/180=5.6% | 1 | 0.009M | 0.001M | US$0.001 |
| (o1-preview 1-Pass) | val | 21/180=11.7% | 1 | 0.008M | 0.008M | US$0.601 |
| Best-of-N | val | 100/180=55.6% | 472 | 4.44M | 0.47M | US$0.47 |
| Sequential-Revision+ | val | 149/180=82.8% | 280 | 35.53M | 0.29M | US$2.75 |
| **Mind Evolution** | val | 172/180=**95.6%** | 174 | 3.10M | 0.18M | US$0.29 |
| **(+pro)** | val | 180/180=**100%** | (257) | (3.25M) | (0.19M) | (US$0.54) |
| **Mind Evolution** | test | 952/1000=**95.2%** | 167 | 3.02M | 0.18M | US$0.28 |
| **(+pro)** | test | 999/1000=**99.9%** | (67) | (3.05M) | (0.18M) | (US$0.33) |

Natural Plan Trip Planning

| 1-Pass | Set | Success Rate | LLM Calls | Input Tokens | Output Tokens | API Cost (Oct 2024) |
|---|---|---|---|---|---|---|
| 1-Pass | val | 66/320=20.6% | 1 | 0.002M | 0.001M | <US$0.001 |
| (o1-preview 1-Pass) | val | 116/320=36.2% | 1 | 0.002M | 0.008M | US$0.53 |
| Best-of-N | val | 247/320=77.2% | 274 | 0.61M | 0.18M | US$0.10 |
| Sequential-Revision+ | val | 238/320=74.4% | 391 | 41.57M | 0.38M | US$3.23 |
| **Mind Evolution** | val | 308/320=**96.2%** | 168 | 1.48M | 0.19M | US$0.17 |
| **(+pro)** | val | 320/320=**100%** | (111) | (1.51M) | (0.19M) | (US$0.22) |
| **Mind Evolution** | test | 1204/1280=**94.1%** | 196 | 1.78M | 0.22M | US$0.20 |
| **(+pro)** | test | 1275/1280=**99.6%** | (211) | (1.86M) | (0.24M) | (US$0.37) |

Natural Plan Meeting Planning

| 1-Pass | Set | Success Rate | LLM Calls | Input Tokens | Output Tokens | API Cost (Oct 2024) |
|---|---|---|---|---|---|---|
| 1-Pass | val | 104/500=20.8% | 1 | 0.007M | 0.001M | US$0.001 |
| (o1-preview 1-Pass) | val | 221/500=44.2% | 1 | 0.006M | 0.006M | US$0.47 |
| Best-of-N | val | 347/500=69.4% | 444 | 3.99M | 0.31M | US$0.39 |
| Sequential-Revision+ | val | 310/500=62.0% | 484 | 32.16M | 0.40M | US$2.53 |
| **Mind Evolution** | val | 425/500=**85.0%** | 406 | 5.35M | 0.41M | US$0.52 |
| **(+pro)** | val | 492/500=**98.4%** | (890) | (13.36M) | (0.91M) | (US$2.55) |
| **Mind Evolution** | test | 419/500=**83.8%** | 394 | 5.24M | 0.40M | US$0.51 |
| **(+pro)** | test | 491/500=**98.2%** | (828) | (12.25M) | (0.83M) | (US$2.34) |{{< /table-caption >}}
> 🔼 표 2는 여섯 가지 자연어 계획 작업에 대한 실험 결과를 보여줍니다. 여기에는 여행 계획, 여행 계획 세우기, 회의 계획 세우기 세 가지 작업이 포함됩니다. 각 작업에 대해 1-Pass, Best-of-N, 순차적 수정+, 마음 진화의 네 가지 방법을 사용하여 성공률, LLM 호출 수, 토큰 수, API 비용을 측정했습니다. 마음 진화 방법은 두 단계 접근 방식을 사용하여 Gemini 1.5 Pro 모델을 사용하여 Gemini 1.5 Flash 모델에서 해결되지 않은 문제를 해결했습니다. 두 단계 결과는 (+pro)로 표시되어 있으며, LLM 호출 수, 토큰 수 및 API 비용은 검증 또는 테스트 문제 집합 전체에 대해 평균되고 (+pro) 실험에 대한 나머지 문제에 대해서만 계산됩니다. 비교를 위해 OpenAI 01-preview 결과도 표에 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Experimental results on benchmark natural language planning tasks. “(+pro)” denotes the two-stage results, where we use Gemini 1.5 Pro to solve the problems that were not solved in experiments using Gemini 1.5 Flash. Number of LLM calls, token counts, and API cost are averaged across the validation or test problem set, and they are calculated only on the remaining problems for the “(+pro)” experiments. Here, we also show OpenAI o1-preview results as a reference.
> </details>

{{< table-caption >}}
| Method | Answer |
|---|---| 
| 1-Pass | Madrid (Day 1-7) → Santorini (Day 7-12) → Zurich (Day 12-14) → Frankfurt (Day 14-16) → Riga (Day 16-19)  7 days for Madrid instead of 5; 4 days for Riga instead of 3; 19 days in total instead of 16. |
| Best-of-N | Madrid (Day 1-7) → Santorini (Day 7-12) → Zurich (Day 12-14) → Frankfurt (Day 14-16) → Riga (Day 16-16) 7 days for Madrid instead of 5; 1 day for Riga instead of 3. |
| Sequential Revisions+ | Zurich (Day 1-3) → Frankfurt (Day 3-5) → Riga (Day 5-7) → Santorini (Day 7-12) → Madrid (Day 12-16) omitted the show in Madrid (Day 3-7); no direct flight from Riga to Santorini. |
| Mind Evolution (ours) | Frankfurt (Day 1-3) → Madrid (Day 3-7) → Santorini (Day 7-12) → Zurich (Day 12-14) → Riga (Day 14-16) |{{< /table-caption >}}
> 🔼 본 표는 논문의 Trip Planning 과제에서 Mind Evolution과 기준 모델들의 예측 계획을 보여주는 예시 문제를 제시합니다. 1-Pass와 Best-of-N 모델은 체류 기간에 실수를 저지르지만, 마드리드와 산토리니에 특정일에 머무는 요구사항은 충족합니다. 순차적 수정 모델은 마드리드에서 열리는 연례 행사를 누락하고 실제로 존재하지 않는 항공편을 계획하지만, 체류 기간은 정확하게 예측합니다. 반면에 Mind Evolution 모델은 모든 명시된 요구사항을 만족합니다.
> <details>
> <summary>read the caption</summary>
> Table 3:  An example problem instance from the Trip Planning task in Natural Plan, with the predicted plans from Mind Evolution and the baselines. 1-Pass and Best-of-N both make mistakes on number of days to stay, but satisfy the requirements of being in Madrid and Santorini on specific days. The Sequential-Revision+ plan omits the annual show in Madrid and plans a non-existent flight, but is correct in the number of days. In contrast, the Mind Evolution plan satisfies all specified requirements.
> </details>

{{< table-caption >}}
| Critic |  | ✓ | ✓ | ✓ | ✓ |
|---|---|---|---|---|---| 
| S/Q Prompts |  |  | ✓ | ✓ | ✓ |
| Textual Feedback |  |  |  | ✓ | ✓ |
| Reset with LLM |  |  |  |  | ✓ |
| Success Rate | 46.1% | 71.1% | 76.1% | 91.1% | 95.6% |{{< /table-caption >}}
> 🔼 표 4는 TravelPlanner 검증 세트에서 마음 진화 구성 요소에 대한 절제 연구 결과를 보여줍니다. 각 열은 구성 요소를 사용했는지 여부를 나타내는 ✓ 표시가 있는 실험을 보여줍니다. '비평가'가 비활성화되면 그림 2의 비평가 단계를 건너뛰고 작성자 단계로 바로 이동합니다. '전략/질문 프롬프트(S/Q Prompts)'는 중요한 사고 프롬프트의 추가적인 작업별 지침을 나타냅니다(자세한 내용은 A.1절 참조). '텍스트 피드백'이 비활성화되면 프롬프트에 평가 피드백이 포함되지 않습니다. 'LLM으로 재설정'이 비활성화되면 3.2절에 설명된 대로 LLM을 사용하여 선택하는 대신 섬 재설정 이벤트에서 평가 점수로 글로벌 엘리트를 직접 선택합니다.
> <details>
> <summary>read the caption</summary>
> Table 4:  An ablation study of Mind Evolution components on the TravelPlanner validation set. Each column in the table shows an experiment where ✓ indicates whether a component is used. If “Critic” is disabled, we skip the critic step in Figure 2 and go straight to the author step. “S/Q Prompts” stands for Strategy/Question prompts, which are additional task-specific instructions in the critical thinking prompts (see Section A.1 for details). If “Textual Feedback” is disabled, we do not include evaluation feedback in the prompts. If “Reset with LLM” is disabled, we directly select global elites by their evaluation scores in island reset events, rather than use an LLM to choose, as described in Section 3.2.
> </details>

{{< table-caption >}}
|                    | Succ. Rate |
|--------------------|-------------|
| $N_{island}=4, N_{convs}=5$ | 87.5%       |
| $N_{island}=1, N_{convs}=20$| 77.4%       |
| $N_{convs}=10, N_{gens}=5$ | 82.5%       |
| $N_{convs}=5, N_{gens}=10$ (default) | 87.5%       |
| $N_{convs}=4, N_{gens}=13$| 85.0%       |{{< /table-caption >}}
> 🔼 표 5는 Trip Planning 문제에서 도시 수가 10개인 경우의 하이퍼파라미터 연구 결과를 보여줍니다. 처음 두 행은 Island Model을 사용했을 때와 사용하지 않았을 때의 차이를 보여주고, 나머지 세 행은 각 세대당 후보 솔루션의 수와 세대 수 사이의 절충안을 보여줍니다. 마지막 행 (Nconvs=4, Ngens=13)은 800개가 조금 넘는(832개) 솔루션을 생성합니다.
> <details>
> <summary>read the caption</summary>
> Table 5:  Hyperparameter studies on the Trip Planning problem instances with 10 cities. The first two rows show the difference between enabling and disabling the island model. The bottom three rows illustrate a trade-off between the number of candidates per generation versus the number of generations. (Note that the bottom row (Nconvs=4,Ngens=13formulae-sequencesubscript𝑁convs4subscript𝑁gens13N_{\text{convs}}=4,N_{\text{gens}}=13italic_N start_POSTSUBSCRIPT convs end_POSTSUBSCRIPT = 4 , italic_N start_POSTSUBSCRIPT gens end_POSTSUBSCRIPT = 13) produces slightly more than 800 solutions (832).
> </details>

{{< table-caption >}}
| Task | Results (Cipher and Poem) |
|---|---|---|
| <a download="" href="data:text/plain;base64,TWVzc2FnZSBUbyBFbmNvZGUgKE0pOgogICAgICAgICAgICAxMCwyMCwzMCw0MCwKICAgICAgICAgICAgNTAsNjAsNzAsODAsCiAgICAgICAgICAgIDkwLDEwMCwxMCwyMAoKU3R5bGU6IFBvZW0KSW5zcGlyYXRpb246IFNoZWwgU2lsdmVyc3RlaW4KV29yZHMgQmV0d2VlbiAoQik6IDQKVG9waWM6ICJUaGUgRnVuIG9mIFdhbGtpbmci">⬇</a>Message To Encode (M):<br> 10,20,30,40,<br> 50,60,70,80,<br> 90,100,10,20<br>Style: Poem<br>Inspiration: Shel Silverstein<br>Words Between (B): 4<br>Topic: "The Fun of Walking" | <a download="" href="data:text/plain;base64,MTAgOiByb29zdGVyOwoyMCA6IGZsb3dlcnM7CjMwIDogYnJpZ2h0Owo0MCA6IGZsYW1lczsKNTAgOiBjaGVycnk7CjYwIDogY3JpbXNvbjsKNzAgOiBzW5zZXQ7CjgwIDogcnVieTsKOTAgOiBzY2FybGV0OwoxMDAgOiBidXJuaW5nOw==">⬇</a>10 : rooster;<br>20 : flowers;<br>30 : bright;<br>40 : flames;<br>50 : cherry;<br>60 : crimson;<br>70 : sunset;<br>80 : ruby;<br>90 : scarlet;<br>100 : burning; | <a download="" href="data:text/plain;base64,SSBsaWtlIHRvIHdhbGssIEkgbGlrZSB0byBzdHJpZGUsCldpdGggUk9PU1RFUiBjcm93cyBhbmQgRkxPV0VSUyBieSBteSBzaWRlLgpJIGxpa2UgdG8gd2FsaywgSSBsaWtlIHRvIHJvYW0sClBhc3QgQlJJR0hUIGdyZWVuIGZpZWxkcyBhbmQgRkxBTUVTIGF0IGhvbWUuCkkgbGlrZSB0byB3YWxrLCBJIGxpa2UgdG8gc3Ryb2xsLApUbyBzZWUgdGhlIENIRVJSWSB0cmVlcyBhbmQgYSBDUklNU09OIGhvbGUuCkkgbGlrZSB0byB3YWxrLCBJIGxpa2UgdG8gcmFtYmxlLApUbyB3YXRjaCB0aGUgU1VOU0VUIGFuZCBob2xkIGEgUlVCWSdzIGdhbWJsZS4KSSBsaWtlIHRvIHdhbGssIEkgbGlrZSB0byB3YW5kZXIsClRvIHdhdGNoIGEgU0NBUkxFVCBsZWFmLCBhbmQgYSBmaXJlLCBCVVJOSU5HLCB1bmRlci4KSSBsaWtlIHRvIHdhbGssIEkgbGlrZSB0byBzdHJpZGUsCldpdGggUk9PU1RFUiBjcm93cyBhbmQgRkxPV0VSUyBieSBteSBzaWRlLg==">⬇</a>I like to walk, I like to stride,<br>With ROOSTER crows and FLOWERS by my side.<br>I like to walk, I like to roam,<br>Past BRIGHT green fields and FLAMES at home.<br>I like to walk, I like to stroll,<br>To see the CHERRY trees and a CRIMSON hole.<br>I like to walk, I like to ramble,<br>To watch the SUNSET and hold a RUBY's gamble.<br>I like to walk, I like to wander,<br>To watch a SCARLET leaf, and a fire, BURNING, under.<br>I like to walk, I like to stride,<br>With ROOSTER crows and FLOWERS by my side.|{{< /table-caption >}}
> 🔼 표 6은 StegPoet 작업에 대한 실험 결과를 보여줍니다. 가격 및 토큰 수는 문제당 평균값입니다. 모든 결과는 Gemini 1.5 Flash를 사용하지만, (+pro)는 Flash 실행에서 해결되지 않은 문제를 Gemini 1.5 Pro를 사용하여 해결한 결과입니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Experimental results on StegPoet. Price and token counts are averages per problem. All results use Gemini 1.5 Flash, except (+pro), which solves the problems that were not solved in the Flash runs, using Gemini 1.5 Pro.
> </details>

{{< table-caption >}}
| Set | Success Rate | Input Tokens | Output Tokens | API Cost (Oct 2024) |
|---|---|---|---|---|
| 1-Pass | val | 0/101=0.0% | 0.002M | &lt;0.001M | 
| Best-of-N | val | 1/101=1.0% | 1.56M | 0.25M | 
| Sequential-Revision+ | val | 20/101=19.8% | 41.69M | 0.24M | 
| **Mind Evolution** | val | 47/101=**46.5%** | 3.56M | 0.20M | 
| **(+pro)** | val | 88/101=**87.1%** | 3.74M | 0.22M | 
| **Mind Evolution** | test | 106/245=**43.3%** | $0.34 | 3.63M | 
| **(+pro)** | test | 194/245=**79.2%** | $0.72 | 3.84M |{{< /table-caption >}}
> 🔼 표 7은 GPT-4o-Mini 모델을 사용하여 검증 세트에서 마음 진화 전략의 성능을 보여줍니다.  여러 가지 자연어 계획 작업에서 마음 진화 전략의 성공률을 보여주는 결과를 제시합니다.  세부적으로는 TravelPlanner, Trip Planning, Meeting Planning 세 가지 과제에 대한 성공률을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Mind Evolution with GPT-4o-Mini results on validation sets.
> </details>

{{< table-caption >}}
| Planner | Success Rate |
|---|---| 
| TravelPlanner [42] | 79.4% |
| Natural Plan [47] Trip Planning | 48.1% |
| Natural Plan [47] Meeting Planning | 86.4% |{{< /table-caption >}}
> 🔼 표 8은 2024년 10월 기준 각 언어 모델의 가격을 보여줍니다.  이 가격 차이는 모델 간 실제 계산 비용 차이를 대략적으로 나타냅니다.  즉,  토큰당 가격이 높을수록 해당 모델을 사용하여 추론을 실행하는 데 드는 비용이 더 많이 든다는 것을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Pricing at the time of writing (October 2024). These differences serve as a proxy for real computational cost differences among models.
> </details>

{{< table-caption >}}
| Model | Input Token | Output Token |
|---|---|---|
| Gemini 1.5 Flash | $0.075/M | $0.30/M |
| Gemini 1.5 Pro | $1.25/M | $5.00/M |
| GPT-4o-Mini | $0.15 | $0.60 |
| OpenAI o1-preview | $15.00/M | $60.00/M |{{< /table-caption >}}
> 🔼 표 9는 TravelPlanner 작업의 예시와 Mind Evolution 및 기준 방법에 의해 제안된 해결책을 보여줍니다. 여기에는 여행 계획에 대한 사용자 질의와 Mind Evolution, 1-Pass, Best-of-N, Sequential Revisions+를 포함한 여러 추론 전략에 의해 생성된 여행 계획이 포함됩니다. 각 계획은 경로, 숙박 시설, 식사, 관광 명소 등의 세부 정보를 제공하고, 비용과 제약 조건 준수 여부를 평가합니다. 이 표는 제안된 접근 방식의 효율성과 다양한 전략 간의 성능 차이를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 9: An example TravelPlanner task and the solutions proposed by Mind Evolution and the baselines method.
> </details>

{{< table-caption >}}
| Method | Answer |
|---|---| 
| 1-Pass | [Day 1] city: ‘from Chicago to Albany’, accommodation: ‘Spacious room with huge bay window & natural light, Albany’, attraction: ‘-’, breakfast: ‘-’, dinner: ‘Kaiser, Albany’, lunch: ‘-’, transportation’: ‘Flight Number: F3983351, from Chicago to Albany, Departure Time: 20:20, Arrival Time: 23:04’<br>[Day 2] city: ‘Albany’, accommodation: ‘Spacious room with huge bay window & natural light, Albany’, attraction: ‘Albany Pine Bush Preserve, Albany;New York State Museum, Albany;’, breakfast: ‘Desi Villa, Albany’, lunch: ‘Just Parkash, Albany’, dinner: ‘Kaiser, Albany’, ‘transportation’: ‘-’<br>[Day 3] city: ‘from Albany to Chicago’, accommodation: ‘-’, attraction: ‘Hear about Here, Albany;’, breakfast: ‘Cafe Coffee Day The Square, Albany’, lunch: ‘PiccoLicko, Albany’, dinner: ‘StarvinMarvin, Albany’, transportation: ‘Flight Number: F3813300, from Albany to Chicago, Departure Time: 16:40, Arrival Time: 17:52’<br>The total cost exceeds the budget of $2300 by $114, […] |
| Best-of-N | [Day 1] city: ‘from Chicago to Albany’, accommodation: ‘Mid Town East Side Apartment, Albany’, attraction: ‘New York State Museum, Albany’, breakfast: ‘-’, dinner: ‘Kaiser, Albany’, lunch: ‘-’, transportation’: ‘Taxi, from Chicago to Albany, duration: 12 hours 53 mins, distance: 723 km, cost: 532’<br>[Day 2] city: ‘Albany’, accommodation: ‘Mid Town East Side Apartment, Albany’, attraction: ‘Albany Institute of History & Art, Albany’, breakfast: ‘Echoes Satyaniketan, Albany’, lunch: ‘Cafe Coffee Day The Square, Albany’, dinner: ‘Urban Punjab, Albany’, ‘transportation’: ‘-’<br>[Day 3] city: ‘from Albany to Chicago’, accommodation: ‘-’, attraction: ‘Historic Cherry Hill, Albany’, breakfast: ‘Just Parkash, Albany’, lunch: ‘BKs The Juice Bar, Albany’, dinner: ‘-’, transportation: ‘Flight Number: F4008387, from Albany to Chicago, Departure Time: 05:05, Arrival Time: 06:11’<br>Taxi from Chicago to Albany on day 1 is not a valid option, […] |
| Sequential Revisions+ | [Day 1] city: ‘from Chicago to Albany’, accommodation: ‘2Br Union square Newly furnished’, Albany’, attraction: ‘-’, breakfast: ‘-’, dinner: ‘-’, lunch: ‘-’, transportation’: ‘Flight Number: F3983350, from Chicago to Albany, Departure Time: 14:29, Arrival Time: 17:03’<br>[Day 2] city: ‘Albany’, accommodation: ‘2Br Union square Newly furnished’, attraction: ‘New York State Museum, Albany;Albany Pine Bush Preserve, Albany’, breakfast: ‘Cafe Coffee Day, Albany’, lunch: ‘PiccoLicko, Albany’, dinner: ‘Kaiser, Albany’, ‘transportation’: ‘-’<br>[Day 3] city: ‘from Albany to Chicago’, accommodation: ‘-’, attraction: ‘The McPherson Legacy to the City of Albany - Robert Burns Statue, Albany’, breakfast: ‘-’, lunch: ‘-’, dinner: ‘-’, transportation: ‘Flight Number: F3732604, from Albany to Chicago, Departure Time: 05:53, Arrival Time: 07:24’<br>’2Br Union square Newly furnished’ requires staying at least 30 nights, […] |
| Mind Evolution (ours) | [Day 1] city: ‘from Chicago to Albany’, accommodation: ‘Mid Town East Side Apartment, Albany’, attraction: ‘-’, breakfast: ‘-’, dinner: ‘-’, lunch: ‘-’, transportation’: ‘Flight Number: F3983350, from Chicago to Albany, Departure Time: 14:29, Arrival Time: 17:03’<br>[Day 2] city: ‘Albany’, accommodation: ‘Mid Town East Side Apartment, Albany’, attraction: ‘Albany Institute of History & Art, Albany’, breakfast: ‘StarvinMarvin, Albany’, lunch: ‘Cafe Coffee Day The Square, Albany’, dinner: ‘PiccoLicko, Albany’, ‘transportation’: ‘-’<br>[Day 3] city: ‘from Albany to Chicago’, accommodation: ‘-’, attraction: ‘The McPherson Legacy to the City of Albany - Robert Burns Statue, Albany’, breakfast: ‘-’, lunch: ‘-’, dinner: ‘-’, transportation: ‘Flight Number: F4008387, from Albany to Chicago, Departure Time: 05:05, Arrival Time: 06:11’ |
{{< /table-caption >}}
> 🔼 표 10은 본 논문에서 제시된 회의 계획 문제의 예시와 Mind Evolution 및 기준 방법으로 제안된 해결책을 보여줍니다. 이 표는 다양한 방법들이 회의 일정 계획 문제에 어떻게 접근하는지 보여주는 비교 자료로 사용됩니다. 각 방법의 장단점과 효율성을 비교하여 Mind Evolution의 우수성을 강조하는 데 활용됩니다. 특히, 제약 조건을 고려한 최적의 일정 계획을 수립하는 능력을 비교합니다.
> <details>
> <summary>read the caption</summary>
> Table 10: An example Meeting Planning task and the solutions proposed by Mind Evolution and the baselines method.
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