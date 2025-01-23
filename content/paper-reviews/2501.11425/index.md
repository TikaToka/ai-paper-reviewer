---
title: "Agent-R: Training Language Model Agents to Reflect via Iterative Self-Training"
summary: "Agent-R은 언어 모델 에이전트의 실시간 자기 반성 및 오류 수정 기능을 향상시켜 복잡한 상호 작용 환경에서 성능을 개선합니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Fudan University",]
showSummary: true
date: 2025-01-20
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.11425 {{< /keyword >}}
{{< keyword icon="writer" >}} Siyu Yuan et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-22 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.11425" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.11425" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/agent-r-training-language-model-agents-to" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM) 기반 에이전트는 상호 작용 환경에서 복잡한 작업을 수행하는 데 점점 중요해지고 있습니다. 하지만 기존의 행동 복제 방식은 실제 환경에서 오류 복구가 어려워 성능이 저하될 수 있습니다.  특히, 단계별 비평 데이터 수집의 어려움은 이러한 문제를 더욱 악화시키고 있습니다. 

Agent-R은 이러한 문제를 해결하기 위해 반복적인 자기 학습 프레임워크를 제안합니다. 이는 단순히 정확성에 따라 행동을 보상하거나 처벌하는 기존 방식과 달리, MCTS를 사용하여 오류를 수정하는 훈련 샘플을 생성합니다.  **에이전트는 오류 발생 시점에 바로 수정을 시도**,  효율적인 학습을 가능하게 합니다. 세 가지 대표적인 상호 작용 환경에서의 실험 결과, **Agent-R은 기존 방법보다 성능이 5.59% 향상**되는 것을 확인했습니다.  **에이전트가 오류를 효과적으로 식별하고 수정하면서 루프를 방지**하는 것을 보여주는 결과입니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} Agent-R은 MCTS를 활용하여 에이전트의 실시간 자기 반성 및 오류 수정 기능을 향상시킨다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} Agent-R은 반복적인 자기 학습을 통해 에이전트의 오류 수정 능력과 데이터셋 생성 능력을 지속적으로 향상시킨다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} Agent-R은 다양한 상호 작용 환경에서 기존 방법보다 우수한 성능을 보이며, 에이전트의 지능과 자율성을 향상시킨다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **상호작용 환경에서 언어 모델 에이전트의 오류 수정 능력 향상**이라는 중요한 문제를 해결하는 데 기여합니다. 기존의 접근 방식의 한계를 극복하고, **새로운 자기 개선 패러다임**을 제시하여 에이전트의 **실시간 자기 반성 및 오류 수정 능력**을 향상시키는 방법을 제시합니다. 이는 **자율적이고 지능적인 에이전트 개발**에 중요한 함의를 가지며, 관련 연구 분야의 발전에 큰 영향을 미칠 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.11425/x1.png)

> 🔼 그림 1은 에이전트가 생성하는 과정에서 오류 수정에 어려움을 겪는 언어 에이전트를 보여줍니다. 이러한 오류는 에이전트가 반복적인 동작을 하게 만들어 장기적인 경로 복구를 방해하고 최적이 아닌 결과를 초래할 수 있습니다. Agent-R은 에이전트가 실시간으로 오류를 효과적으로 감지하고 해결하여 장기적인 작업을 처리하고 반복적인 동작을 피하면서 향상된 자기 반성 능력을 갖도록 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Illustration of language agents struggling with error correction in trajectory generation. These errors can cause agents to enter loops, hindering recovery in long trajectories and resulting in suboptimal outcomes. Agent-R enables agents to effectively detect and address errors in real-time, handling long-horizon tasks and avoiding loops with greater self-reflection capabilities.
> </details>





{{< table-caption >}}
| Dataset | Simulation # | MCTS w/ Iter 1 Revision | MCTS w/ Iter 1 Good | MCTS w/ Iter 2 Revision | MCTS w/ Iter 2 Good | MCTS w/ Iter 3 Revision | MCTS w/ Iter 3 Good | Test Size |
|---|---|---|---|---|---|---|---|---|
| WebShop | 300 | 5500 | 600 | 8500 | 1800 | 9000 | 2000 | 200 |
| SciWorld | 200 | 8000 | 2500 | 4200 | 1800 | 5400 | 1200 | 200 |
| TextCraft | 200 | 6000 | 2000 | 7000 | 3200 | 8000 | 4000 | 100 |{{< /table-caption >}}

> 🔼 표 1은 세 가지 에이전트 상호작용 환경의 통계를 보여줍니다.  데이터셋, 시뮬레이션 수, MCTS를 사용한 반복 횟수, 수정 데이터와 정답 데이터 수, 테스트 데이터 크기 등의 정보를 포함하고 있습니다.  선택 기준에 따라 MCTS는 학습 단계에서 서로 다른 수의 수정 데이터와 정답 데이터를 수집할 수 있습니다.  즉, 각 환경에 따라 다양한 횟수의 수정 데이터와 성공적인 시도 데이터를 통해 에이전트 학습이 진행됨을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Statistics of three agent interactive environments. Due to different selection thresholds, MCTS can collect different numbers of revision data and good data for the training phase.
> </details>





### In-depth insights


#### Agent-R Framework
Agent-R 프레임워크는 대화형 환경에서 언어 모델 에이전트의 **자기 반성적 오류 수정 능력**을 향상시키는 혁신적인 방법입니다. **MCTS(Monte Carlo Tree Search)**를 활용하여 에이전트가 자신의 행동에 대한 **즉각적인 피드백**을 생성하고, 잘못된 경로를 수정하는 **수정 경로**를 동적으로 생성합니다. 이는 기존의 전적으로 정답만을 학습하는 방식과 달리, **실시간 오류 감지 및 수정**에 중점을 두어 보다 강건하고 효율적인 학습을 가능하게 합니다.  **반복적인 자기 학습**을 통해 에이전트는 오류 수정 능력과 데이터 생성 능력을 향상시키며, 장기적인 대화에서도 **루프에 빠지지 않고 최적의 경로**를 찾아나갈 수 있습니다.  **모델 기반의 수정 메커니즘**은 에이전트가 자신의 현재 능력 내에서 오류를 식별하고, 효율적인 수정을 가능하게 하여 학습 효율성을 높입니다.  Agent-R은 다양한 대화형 환경에서 우수한 성능을 보이며, **에이전트의 자기 반성 능력**을 고도화하는 중요한 발걸음입니다.

#### Iterative Self-Training
반복적 자기 학습은 **에이전트가 스스로의 실수를 인지하고 수정하는 능력을 향상시키는 핵심 전략**입니다. 이를 통해 모델은 과거의 잘못된 행동을 바탕으로 더 나은 결정을 내리고, 장기적인 상호 작용 환경에서 반복되는 오류를 피할 수 있습니다. **몬테 카를로 트리 탐색(MCTS)과 같은 알고리즘**은 에이전트가 다양한 경로를 탐색하고 최적의 경로를 찾는 데 도움이 되어, **자기 반성을 위한 고품질의 학습 데이터 생성**을 가능하게 합니다. 이 과정에서 **모델의 자기 수정 능력과 데이터 생성 능력을 동시에 향상시키는 반복적 개선**은 성능 향상에 중요한 역할을 합니다.  **실시간 오류 수정을 가능하게 하는 적시 수정**은 연쇄적인 실패를 막고 최적의 성능을 달성하는 데 필수적입니다.  **다양한 대화형 환경에서의 광범위한 실험**은 이 접근 방식의 효과를 입증하고 기존 방법보다 뛰어난 성능을 보여줍니다.

#### MCTS-Guided Reflection
**MCTS 기반 반성 기법은 에이전트가 상호작용 환경 내에서 자신의 행동을 반추하고 수정하는 과정을 효율적으로 안내하는 핵심 요소입니다.**  **몬테 카를로 트리 탐색(MCTS) 알고리즘을 활용하여 에이전트는 다양한 행동 경로를 탐색하고, 그 중에서 최적의 경로를 선택할 수 있습니다.** 이 과정에서 에이전트는 **잘못된 경로를 식별하고, 이를 수정하는 방법을 학습하게 됩니다.** 이를 통해 에이전트는 장기적인 상호작용에서 발생할 수 있는 **누적 오류를 방지하고, 보다 효율적이고 성공적인 결과를 달성할 수 있습니다.** MCTS 기반 반성은 단순히 성공/실패 여부만을 평가하는 기존의 강화 학습 방식과 달리, 에이전트의 **각 행동 단계에 대한 반성을 가능하게 함으로써, 보다 정교하고 지능적인 학습을 가능하게 합니다.**  **실시간으로 오류 수정을 가능하게 함으로써, 에이전트는 장기적인 상호작용에도 효과적으로 적응하고, 최적의 성과를 달성할 수 있다는 점이 중요합니다.**  전체적으로, MCTS 기반 반성은 에이전트의 자기 개선 능력을 향상시키고, 복잡한 상호작용 환경에서의 문제 해결 능력을 강화하는 데 크게 기여할 것으로 예상됩니다. 특히, **실시간 오류 수정 및 장기적인 상호작용 적응 능력 향상**이라는 측면에서 중요한 의미를 지닌다고 할 수 있습니다.

#### Multi-task Learning
본 논문에서 다루는 다중 작업 학습(Multi-task Learning)은 **여러 작업을 동시에 학습하여 모델의 일반화 성능을 향상시키는 기법**입니다.  특히, 상호작용적 환경에서 에이전트의 자기 반성 능력 향상에 초점을 맞춘 본 연구는 다중 작업 학습을 통해 에이전트가 **다양한 환경에서 발생하는 오류를 효율적으로 수정하고, 반복적인 실수를 피하며, 장기적인 상호작용 과제를 성공적으로 수행**할 수 있도록 지원합니다.  **개별 작업에 대한 전문성을 향상시키는 동시에 다양한 작업 간의 지식 전이를 가능하게 하여** 모델의 견고성과 적응력을 높이는 효과를 기대할 수 있습니다.  **모델이 여러 작업에서 축적한 경험과 지식을 공유함으로써 개별 작업에 대한 학습 효율을 높이고, 새로운 작업에 대한 적응력을 향상**시킬 수 있다는 점이 핵심입니다. 다만, **다중 작업 학습의 성능은 작업 간의 상관관계에 크게 좌우되므로**,  작업 선정 및 설계에 대한 신중한 고려가 필요합니다.  또한, **과도한 작업의 추가는 오히려 성능 저하를 야기할 수 있으므로** 적절한 작업 수를 선택하는 것이 중요합니다.

#### Error Correction
본 논문에서 제시된 에러 수정 기법은 **LLM 기반 에이전트의 자가 수정 능력을 향상**시키는 데 초점을 맞추고 있습니다. 기존의 강화 학습 방식과 달리, 에이전트는 단순히 보상이나 처벌을 통해 학습하는 것이 아니라, **실패한 시도에서부터 올바른 경로를 스스로 찾아가는 과정**을 거칩니다. 이는 MCTS(Monte Carlo Tree Search) 기반의 모델 가이드형 에러 수정 경로 생성 메커니즘을 통해 구현됩니다. 에이전트는 실패한 시도의 첫 번째 에러 지점을 파악하고, 이 지점부터는 성공 경로를 따라가도록 학습합니다.  **실시간 에러 수정**이 가능하도록 설계되어 있어, 연속적인 실패를 방지하고 작업 수행 효율을 높입니다.  **반복적인 자가 학습** 과정을 거치면서 에이전트의 에러 수정 능력과 데이터 생성 능력이 동시에 개선되는 모습을 보입니다.  **다양한 상호 작용 환경**에서 실험을 통해, 제시된 방법의 효과를 검증하였고, 기존 방법들에 비해 뛰어난 성능 향상을 확인하였습니다. 특히, 장기적인 상호 작용이 필요한 작업에서 더욱 효과적이며, 에이전트가 반복적인 루프에 빠지는 것을 방지하는 데에도 도움이 됩니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.11425/x2.png)

> 🔼 그림 2는 Agent-R의 프레임워크를 두 단계로 보여줍니다. 1단계에서는 MCTS와 모델 기반의 반성 메커니즘을 사용하여 수정된 경로(revision trajectories)를 생성합니다. 2단계에서는 수집된 수정된 경로를 사용하여 에이전트를 훈련시킵니다. 이 두 단계는 반복적으로 수행될 수 있습니다.  rs는 수정 신호(revision signal), t′는 잘못된 경로와 올바른 경로 사이의 전환점(transition point), L(θ)는 최적화해야 할 손실 함수(loss function)를 나타냅니다.  수정된 경로는 잘못된 경로를 수정하여 올바른 경로를 생성하는 과정에서 만들어집니다.  본 논문에서는 이러한 수정된 경로를 통해 에이전트의 자가 학습 및 성능 향상을 이끌어내는 방법을 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: The framework of Agent-R consists of two phases. In Phase I, we adopt MCTS and a model-guided reflection mechanism to construct revision trajectories. In Phase II, the agents are trained using the collected revision trajectories. These two phases can be repeated iteratively. rs is the revision signal, t′superscript𝑡′t^{\prime}italic_t start_POSTSUPERSCRIPT ′ end_POSTSUPERSCRIPT is the transition point between the bad and good trajectories, and L⁢(θ)𝐿𝜃L(\theta)italic_L ( italic_θ ) is the loss function to be optimized.
> </details>



![](https://arxiv.org/html/2501.11425/x3.png)

> 🔼 그림 3은 세 가지 상호작용 환경(WebShop, SciWorld, TextCraft)에서 서로 다른 반복 횟수에 따른 다양한 훈련 경로의 결과를 보여줍니다. 각 환경에 대해 세 가지 훈련 방법(기준, 최적 경로, Agent-R)의 평균 최종 점수를 반복 횟수별로 비교 분석하여 Agent-R의 성능 향상을 시각적으로 보여줍니다.  세 가지 환경 모두에서 Agent-R을 사용한 훈련이 반복 횟수가 증가함에 따라 성능이 지속적으로 향상되는 것을 알 수 있습니다. 이는 Agent-R이 반복적인 자기 학습을 통해 에이전트의 성능을 개선하는 데 효과적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Results of different training trajectories under different iterations on three interactive environments.
> </details>



![](https://arxiv.org/html/2501.11425/x4.png)

> 🔼 이 그림은 세 가지 상호 작용 환경(WebShop, SciWorld, TextCraft)에서 반복되는 행동의 평균 횟수를 다양한 훈련 경로와 반복 횟수에 따라 보여줍니다.  각 환경에 대해, 초기 상태(Vanilla), 최적 경로만 사용한 훈련(w/ Optimal), Agent-R을 사용한 훈련(w/ Agent-R #Iter1, #Iter2, #Iter3)의 네 가지 경우에 대한 반복 행동 시퀀스의 평균 길이를 보여줍니다.  Agent-R 훈련의 반복 횟수가 증가함에 따라 반복되는 행동의 횟수가 줄어드는 것을 확인할 수 있습니다.  이는 Agent-R이 에이전트가 반복적인 행동에 빠지는 것을 방지하는 데 효과적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Average count of repeated action lengths for different training trajectories and different iterations in three interactive environments.
> </details>



![](https://arxiv.org/html/2501.11425/x5.png)

> 🔼 그림 5는 세 가지 상호 작용 환경(WebShop, SciWorld, TextCraft)에서 Agent-R의 반복 훈련 횟수에 따른 평균 수정 길이를 보여줍니다.  수정 길이는 잘못된 경로를 처음 인식한 시점부터 올바른 경로로 전환하기까지 걸린 행동(action)의 수를 나타냅니다.  반복 훈련이 진행될수록 평균 수정 길이가 짧아지는 것을 확인할 수 있으며, 이는 Agent-R이 잘못된 행동을 더욱 빠르고 효율적으로 인지하고 수정할 수 있음을 시사합니다.  이는 에이전트의 자기 반성 능력 향상과 더 나은 경로 계획 능력을 보여주는 지표입니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Average revision length of different iterations on three interactive environments.
> </details>



![](https://arxiv.org/html/2501.11425/x6.png)

> 🔼 그림 6은 세 가지 상호작용 환경(WebShop, SciWorld, TextCraft)에서 서로 다른 학습 방법(단일 작업 학습, 직접 수정, Agent-R의 다중 작업 학습)의 성능을 비교한 그래프입니다. Agent-R의 다중 작업 학습 방법이 다른 방법들보다 우수한 성능을 보여줍니다. 특히 반복 학습을 거듭할수록 그 차이가 더욱 커지는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Comparison of different training methods on three interactive environments.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | WebShop | SciWorld | TextCraft | Average |
|---|---|---|---|---|
| *Close-sourced Models* |  |  |  |  |
| DeepSeek-Chat [2024a] | 11.00 | 16.80 | 23.00 | 16.93 |
| Claude-3-Haiku [2024] | 5.50 | 0.83 | 0.00 | 2.11 |
| Claude-3-Sonnet [2024] | 1.50 | 2.78 | 38.00 | 14.09 |
| GPT-3.5-Turbo [2022] | 12.50 | 7.64 | 47.00 | 22.38 |
| GPT-4-Turbo [2023] | 15.50 | 14.38 | 77.00 | 35.63 |
| GPT-4o [2023] | 25.48 | 46.91 | 64.00 | 45.46 |
| *Open-sourced Models* |  |  |  |  |
| Llama2-Chat-13B [2023] | 1.00 | 0.83 | 0.00 | 0.61 |
| AgentLM-7B [2024a] | 36.50 | 2.75 | 0.00 | 13.08 |
| AgentLM-13B [2024a] | 39.50 | 10.68 | 4.00 | 18.06 |
| Agent-FLAN [2024d] | 40.35 | 28.64 | 16.00 | 28.33 |
| Llama-3.1-8B-Instruct [2024] | 19.65 | 14.36 | 26.00 | 20.00 |
| w/ ETO [2024b] | 52.80 | 67.55 | 75.00 | 65.12 |
| w/ Direct-Revision | 54.44 | 66.65 | 66.00 | 62.36 |
| 1-5
w/ Agent-R | **63.91** | **70.23** | **78.00** | **70.71** |{{< /table-caption >}}
> 🔼 표 2는 세 가지 상호작용 환경(WebShop, SciWorld, TextCraft)에서 세 가지 모델(Close-sourced, Open-sourced, Agent-R)의 성능을 비교한 표입니다.  Agent-R은 Llama-3.1-8B 모델에 Agent-R에서 생성된 수정된 경로(revision trajectories)를 사용하여 3번의 반복 학습을 거친 모델입니다.  표에는 다양한 기준 모델들과 비교하여 Agent-R의 성능 향상을 보여줍니다.  Close-sourced 모델은 GPT-3.5-Turbo, GPT-4-Turbo, GPT-40, Claude 3, DeepSeek-Chat 등의 상용 모델들이고, Open-sourced 모델은 Llama2-Chat, AgentLM, Agent-FLAN, Llama-3.1-8B-Instruct 등의 오픈소스 모델들입니다.  Agent-R은 기준 모델들에 비해 상당히 높은 성능을 보여주는 것을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Results of three interactive environments. We train Llama-3.1-8B on revision trajectories collected from Agent-R for three iterations and compare its performance with various models.
> </details>

{{< table-caption >}}
| Method | WebShop | SciWorld | TextCraft | Average |
|---|---|---|---|---|
| GPT-4o | 24.10 | 35.56 | 8.22 | 22.63 |
| AgentLM-7B | 20.96 | 0.00 | 0.00 | 6.99 |
| AgentLM-13B | 23.20 | 0.22 | 0.00 | 7.81 |
| Agent-FLAN | 19.37 | 0.00 | 0.00 | 6.46 |
| _Llama-3.1-8B_ |  |  |  |  |
| w/ Optimal | 31.38 | 1.15 | 0.00 | 10.84 |
| w/ Optimal+ | 25.03 | 0.00 | 0.00 | 8.34 |
| w/ ETO | 35.78 | 3.47 | 0.00 | 13.08 |
| _Llama-3.1-8B w/ Direct-Revision Trajectories_ |  |  |  |  |
| # Iter1 | 40.26 | 19.09 | 11.35 | 23.57 |
| # Iter2 | 40.35 | 27.45 | 22.97 | 30.26 |
| # Iter3 | 42.02 | 35.27 | 29.73 | 35.67 |
| _Llama-3.1-8B w/ Trajectories from Agent-R_ |  |  |  |  |
| # Iter1 | 46.51 | 40.82 | 32.43 | 39.92 |
| # Iter2 | 47.51 | 45.22 | 35.14 | 42.62 |
| # Iter3 | 48.22 | 48.79 | 43.24 | 46.75 |{{< /table-caption >}}
> 🔼 표 3은 다양한 방법의 수정 결과를 보여줍니다.  Llama-3.1-8B 모델 학습에 사용된 최적의 궤적이 GPT-40에서 생성되었다는 것을 의미하는 'w/ Optimal+'은 최적의 궤적을 나타냅니다.  표는 다양한 방법(최적 궤적만 사용, 최적 및 우수 궤적 결합, 직접 수정 궤적 등)을 사용하여 Llama-3.1-8B 모델을 학습시켰을 때의 성능을 비교하여 Agent-R의 효과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: The revision results of different methods. w/ Optimal+ means the golden trajectories for training Llama-3.1-8B are generated from GPT-4o.
> </details>

{{< table-caption >}}
| Action: Action | Observation: Observation |
|---|---| 
| Log: Task Description: `{task description}` |  {history log} |
| Current Action: `{node action}` | Current Observation: `{node observation}` |
|  | You need to verify whether the current action is good or bad or uncertain. |
|  | - A good action is one that is greatly helpful to solve the task. |
|  | - A bad action is one that is greatly harmful to solve the task. |
|  | - An uncertain action is one that is neither good nor bad. You cannot judge based on the current information. |
|  | You must give reasons first and then give the response with the format: Judgment: <Good or Bad or Uncertain> |{{< /table-caption >}}
> 🔼 표 4는 Agent-R에서 전환점을 결정하기 위한 프롬프트 템플릿을 보여줍니다.  Agent-R은 에이전트가 잘못된 경로를 수정하여 올바른 경로를 찾을 수 있도록 돕는 반복적인 자기 학습 프레임워크입니다. 이 프롬프트는 에이전트가 현재 작업이 성공적인지 실패했는지 판단하고, 실패했다면 어디서부터 잘못되었는지 파악하는 데 사용됩니다.  이를 통해 에이전트는 잘못된 경로에서 나아가 올바른 경로로 이어지는 수정 경로를 생성할 수 있습니다. 프롬프트는 에이전트의 행동, 관찰, 작업 설명, 그리고 현재 시점까지의 이력 로그를 포함합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Prompt templates of determining transition point in Agent-R.
> </details>

{{< table-caption >}}
| Revision Thoughts |
|---|---| 
| Thought 1: I realize my approach was flawed. I need to revise it. |
| Thought 2: I took the wrong actions. I need to identify the right path. |
| Thought 3: My actions were incorrect. I must adjust my strategy. |
| Thought 4: I see an error in my actions. I need to fix it. |
| Thought 5: My judgment was incorrect. I need to rethink it. |
| Thought 6: I overlooked something important. I need to address it. |
| Thought 7: I recognize my mistake. Let’s find a better solution. |
| Thought 8: I recognize my failure. I need to learn and move forward. |
| Thought 9: My decision was wrong. I should reevaluate. |
| Thought 10: I made an error. I must determine how to correct it. |{{< /table-caption >}}
> 🔼 표 5는 에이전트가 잘못된 경로를 수정하고 올바른 경로를 생성하는 데 사용되는 10가지 수정 사고 방식을 보여줍니다. 각각의 수정 사고는 잘못된 행동을 수정하고 작업을 완료하기 위한 에이전트의 사고 과정을 반영합니다. 이러한 수정 사고들은 에이전트가 스스로 반성하고 복구하는 능력을 향상시키는 데 사용되는 자기 학습 프레임워크의 핵심 구성 요소입니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Ten revision thoughts to construct revision trajectories.
> </details>

{{< table-caption >}}
| Dataset | Iteration | Method | WebShop | SciWorld | TextCraft | Average |
|---|---|---|---|---|---|---|
| Direct-Revision + Good Trajectory | 1 | Single | 48.06 | 64.52 | 57.00 | 56.53 |
|  |  | Multi | 42.66 | 63.10 | 48.00 | 51.25 |
| 2-7 | 2 | Single | 55.56 | 64.52 | 63.00 | 61.03 |
|  |  | Multi | 46.93 | 64.23 | 64.00 | 58.39 |
| 2-7 | 3 | Single | 58.82 | 65.51 | 71.00 | 65.11 |
|  |  | Multi | 54.44 | 66.65 | 66.00 | 62.36 |
| Trajectory from Agent-R | 1 | Single | 49.80 | 64.02 | 60.00 | 57.94 |
|  |  | Multi | 45.84 | 66.71 | 64.00 | 58.85 |
| 2-7 | 2 | Single | 56.34 | 65.62 | 71.00 | 64.32 |
|  |  | Multi | 52.05 | 68.28 | 76.00 | 65.44 |
| 2-7 | 3 | Single | 60.66 | 67.22 | 76.00 | 67.96 |
|  |  | Multi | 63.91 | 70.23 | 78.00 | 70.71 |{{< /table-caption >}}
> 🔼 표 6은 세 가지 상호 작용 환경(WebShop, SciWorld, TextCraft)에서 다양한 학습 방법(단일 작업 학습, 다중 작업 학습, 직접 수정 및 우수 사례 병합)을 사용했을 때의 상세 결과를 보여줍니다. 각 환경에 대해 반복 횟수(1, 2, 3)별로 성공률을 비교하여 Agent-R을 포함한 다양한 방법의 성능을 평가합니다.  표는 각 학습 방법과 반복 횟수에 따른 세 가지 환경에서의 평균 최종 보상 또는 성공률을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Detailed Results of different training methods on three interactive environments.
> </details>

{{< table-caption >}}
| WebShop |  |  |
|---|---|---|
| **WebShop** |  |  |
| *Example 1:* |  |  |
| `Assistant`: Thought: I think I should search for light blue shorts in a specific size and price range to get more accurate results. Action: search[light blue 36w 30l price:40] |  |  |
| `Human`: [Search Result] |  |  |
| `Assistant`: Thought: I went in the wrong direction with my search. I need to reset and try again. |  |  |
| `Human`: ok. |  |  |
| `Assistant`: Thought: I need to back to search. Action: click[Back to Search] |  |  |
| `Human`: [Search Result] |  |  |
| *Example 2:* |  |  |
| `Assistant`: Thought: I think the second option is a bit off-topic, but it’s a good price, so I’ll consider it. Action: click[B08226NDZW] |  |  |
| `Human`: [Search Result] |  |  |
| `Assistant`: Thought: I recognize my mistake. Let’s find a better solution. Action: wait |  |  |
| `Human`: ok. |  |  |
| `Assistant`: Thought: I think the search query is not specific enough, so I’ll try to refine it by adding more keywords. Action: search[machine wash men’s dress shirts polyester heathered cotton classic fit men 3t price:50.00] |  |  |
| `Human`: [Search Result] |  |  |
| **Sciworld** |  |  |
| *Example 1:* |  |  |
| `Assistant`: Thought: I should open door to kitchen. Action: open door to kitchen |  |  |
| `Human`: The door is now open. |  |  |
| `Assistant`: Thought: I took the wrong steps. I need to identify the right path. Action: wait |  |  |
| `Human`: ok. |  |  |
| `Assistant`: Thought: I should go to kitchen. Action: go to kitchen |  |  |
| `Human`: You move to the kitchen. |  |  |
| *Example 2:* |  |  |
| `Assistant`: Thought: I think I should try to determine the temperature of the unknown substance B. Action: use thermometer on unknown substance B |  |  |
| `Human`: the thermometer measures a temperature of 19 degrees celsius |  |  |
| `Assistant`: Thought: I misunderstood the situation. Time to reassess. Action: wait |  |  |
| `Human`: ok. |  |  |
| `Assistant`: Thought: I think I should check the unknown substance B again to make sure the temperature is accurate. Action: use thermometer on unknown substance B |  |  |
| `Human`: the thermometer measures a temperature of 16 degrees celsius |  |  |
| **TextCraft** |  |  |
| *Example 1:* |  |  |
| `Assistant`: Thought: I should check if I can get blackstone directly from the environment or the inventory. Action: inventory |  |  |
| `Human`: Inventory: You are not carrying anything. |  |  |
| `Assistant`: Thought: I recognize my mistake. Let’s find a better solution. Action: wait |  |  |
| `Human`: ok. |  |  |
| `Assistant`: Thought: I should go get the blackstone from the environment. Action: get 3 blackstone |  |  |
| `Human`: Got 3 blackstone |  |  |
| *Example 2:* |  |  |
| `Assistant`: Thought: I can use the quartz slab to craft something else that might be useful. Action: craft quartz wall using 4 quartz slab |  |  |
| `Human`: Could not find enough items to craft minecraft:quartz_wall |  |  |
| `Assistant`: Thought: I realize I chose poorly. I must change direction. Action: wait |  |  |
| `Human`: ok. |  |  |
| `Assistant`: Thought: I think I should try to get more quartz to craft the quartz wall. Action: get 2 quartz slab |  |  |
| `Human`: Got 2 quartz slab |  |  |{{< /table-caption >}}
> 🔼 표 7은 Agent-R에서 생성된 궤적을 사용하여 세 번째 반복에서 Llama-3.1-8B에 의해 생성된 궤적에서 오류 수정의 예를 보여줍니다. WebShop의 검색 결과는 길이가 길어 생략되었습니다. 이 표는 잘못된 행동을 식별하고 수정하는 Agent-R의 능력을 보여주는 구체적인 예시를 제공합니다. 각 예시는 초기 잘못된 행동, Agent-R의 분석 및 수정된 행동을 보여주는 대화 형식으로 제시됩니다. 이를 통해 Agent-R이 어떻게 긴 시퀀스의 행동에서 오류를 감지하고 수정하는지 보다 자세히 이해할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Example of error correction from the trajectory generated by Llama-3.1-8B, trained on trajectories from Agent-R during the third iteration. The search results in WebShop are omitted due to their length.
> </details>

{{< table-caption >}}
| Platform | Judgment Category | Description |
|---|---|---|
| WebShop | Invalid Actions | The action is bad because it does not match the original search criteria. Therefore, Judgment: Bad |
|  | Mismatch Observation | However, the product does not match the description of a machine wash men’s dress shirt with polyester heathers, heathers cotton, cotton heather, needle sleeve, classic fit, and color heather grey, as specified in the task description. Therefore, Judgment: Bad |
|  | Irrelevant Actions | The action is bad because it is not relevant to the task of finding men’s shirts with specific characteristics. Therefore, Judgment: Bad |
| Sciworld | Invalid Actions | There is no orange mentioned in the environment, so this action is invalid. It’s not a helpful action, but rather an invalid input. Therefore, Judgment: Bad |
|  | Mismatch Observation | The current task is to determine if the aluminum foil is electrically conductive. The agent has already connected the aluminum foil to the battery and the green light bulb, and observed that the light bulb turned on. This suggests that the aluminum foil is electrically conductive. Moving the aluminum foil to the yellow box would mean that the agent is giving up on the possibility of the aluminum foil being conductive, which is not in line with the current observation. Therefore, Judgment: Bad |
|  | Irrelevant Actions | The agent is not using the art studio’s resources effectively, as the cup containing red paint is not related to the task of creating green paint. Therefore, Judgment: Bad |
| TextCraft | Invalid Actions | The agent is stuck in an infinite loop of trying to execute an invalid action, which is not helpful in solving the task. Therefore, Judgment: Bad |
|  | Mismatch Observation | The action is not good because it is not possible to craft a dried kelp block with 9 dried kelp. The observation suggests that the agent lacks the necessary items to craft the block. This action is actually harmful to the task of crafting the block. Therefore, Judgment: Bad |
|  | Irrelevant Actions | The agent is trying to craft diamond boots, which requires 4 diamonds. The agent has already obtained 4 diamonds, which is sufficient to craft the boots. However, the agent is trying to craft a diamond block instead, which requires 9 diamonds. This action is not helpful in achieving the goal of crafting diamond boots, as it will waste the 4 diamonds the agent already has. Therefore, Judgment: Bad |{{< /table-caption >}}
> 🔼 표 8은 적응형 전환점 평가의 예시 결과를 보여줍니다. 이 판단들은 모두 Agent-R에서 생성된 궤적을 사용하여 세 번째 반복 과정에서 훈련된 Llama-3.1-8B에 의해 생성되었습니다. 이 표는 세 가지 유형의 잘못된 행동(무효 행동, 불일치 관측, 무관 행동)을 보여주는 세 가지 예시를 제시하여 Agent-R이 생성한 훈련 데이터가 에이전트의 자가 반성 능력 향상에 어떻게 기여하는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Example results from the evaluation of adaptive transition points. These judgments are all generated by Llama-3.1-8B, trained on trajectories from Agent-R during the third iteration.
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