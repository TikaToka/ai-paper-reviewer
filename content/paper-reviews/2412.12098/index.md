---
title: "MaxInfoRL: Boosting exploration in reinforcement learning through information gain maximization"
summary: "정보 이득으로 강화 학습 탐색을 강화."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Machine Learning", "Reinforcement Learning", "🏢 ETH Zurich",]
showSummary: true
date: 2024-12-16
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.12098 {{< /keyword >}}
{{< keyword icon="writer" >}} Bhavya Sukhija et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-17 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.12098" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.12098" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/maxinforl-boosting-exploration-in" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

강화 학습은 에이전트가 최대 보상을 얻기 위해 환경과 상호 작용하는 방법을 배우는 머신 러닝 분야입니다. 탐색(새로운 행동 시도)과 활용(알려진 최상의 행동 사용) 간의 균형을 맞추는 것이 중요한 과제입니다. 기존의 많은 강화 학습 알고리즘은 무작위적인 탐색 전략에 의존하여, 특히 보상이 드물거나 국소 최적값이 존재하는 경우 비효율적일 수 있습니다. 이로 인해 샘플 비효율성이 발생하고 복잡한 작업을 해결하는 데 어려움이 따릅니다. MAXINFORL은 정보 이득을 통해 에이전트가 환경에 대한 정보를 최대한 얻는 행동을 선택하도록 유도하여 이 문제를 해결합니다. 이러한 접근 방식을 통해 에이전트는 무작위적인 탐색 대신 환경에 대한 더 많은 정보를 제공하는 전환을 우선적으로 탐색할 수 있습니다. Boltzmann 탐색과 결합된 MAXINFORL은 상태, 보상 및 행동에 대한 엔트로피를 최대화하는 것과 가치 함수를 최대화하는 것 사이의 균형을 자연스럽게 조정합니다. 이 프레임워크는 다양한 오프 정책 모델 없는 강화 학습 방법에 적용할 수 있으며, 어려운 탐색 문제와 시각적 제어 작업과 같은 복잡한 시나리오에서 뛰어난 성능을 보이는 새로운 알고리즘을 생성합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} MAXINFORL은 정보 이득을 활용해 탐색과 활용의 균형을 맞춘다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 다양한 강화 학습 벤치마크에서 최첨단 성능을 달성했다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 어려운 탐색 문제와 시각적 제어 작업에서 뛰어난 성능을 보인다 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**정보 이득 기반 탐색을 통해 강화 학습의 탐색 문제를 해결**하는 방법을 제시하며, 기존 탐색 기법보다 **효율적인 탐색 전략을 제공**합니다. 이는 **샘플 효율성 향상**과 **성능 개선**으로 이어져, 특히 **희소 보상 환경 및 시각적 제어 작업**과 같은 어려운 탐색 문제 해결에 기여할 수 있습니다. 이는 **로봇 공학 및 게임과 같은 다양한 분야에 적용**될 수 있어, 강화 학습 연구의 발전에 중요한 영향을 미칠 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.12098/x1.png)

> 🔼 이 그림은 상태 기반 작업에 대한 여러 딥 강화 학습 벤치마크에서 MaxInfoRL의 정규화된 평균 성능을 보여줍니다. MaxInfoRL은 일관되게 좋은 성능을 보이며 대부분의 환경에서 다른 기준선보다 우수한 성능을 보입니다.
> <details>
> <summary>read the caption</summary>
> (a) Normalized average performance of MaxInfoRL across several deep RL benchmarks on state-based tasks.
> </details>





{{< table-caption >}}
| Algorithm | Training time for 100k environment interactions |
|---|---| 
| SAC (SB3) | 16.96 min +/- 1.64317 min |
| MaxInfoSAC (SB3) | 39 min +/- 1 min |
| SAC (JaxRL) | 5.6 min +/- 0.2min |
| MaxInfoSAC (JaxRL) | 7.3 min +/- 0.75 |{{< /table-caption >}}

> 🔼 이 표는 NVIDIA GeForce RTX 2080 Ti에서 MaxInfoSAC의 계산 비용을 보여줍니다. MaxInfoSAC는 SAC보다 훈련하는 데 더 많은 시간이 필요합니다. 이는 동역학 모델 학습으로 인한 추가 계산 오버헤드 때문입니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Computation cost comparison for MaxInfoSAC on NVIDIA GeForce RTX 2080 Ti
> </details>





### In-depth insights


#### InfoGain Exploration
**정보 이득 탐색**은 에이전트가 환경에 대한 지식을 향상시키는 행동을 우선시하는 강화 학습(RL)의 중요한 탐색 전략입니다. 기본 아이디어는 모델 또는 환경에 대한 **정보 이득을 최대화하는 행동을 선택**하는 것입니다. 이는 에이전트가 **불확실성이 높은** 영역을 탐색하고 보상 최대화에 유용한 정보를 수집하도록 장려하여 **지시적이고 효율적인 탐색**을 가능하게 합니다. 정보 이득 탐색은 **호기심 기반 탐색**과 같은 다른 탐색 방법에 비해 몇 가지 이점을 제공합니다. 호기심 기반 탐색이 새로운 상태를 탐색하는 데 중점을 두는 반면, 정보 이득 탐색은 작업과 직접 관련된 정보를 명시적으로 찾습니다. 이는 특히 보상이 드문 환경에서 **샘플 효율성**을 향상시킵니다.

#### MAXINFORL Framework
**MAXINFORL**은 강화 학습에서 탐색과 활용 간의 균형을 효과적으로 맞추기 위한 프레임워크입니다. 본질적인 탐색 목표와 순수 외적 탐색 알고리즘을 결합하는 데 중점을 둡니다. **MAXINFORL**은 기존의 볼츠만 탐색을 기반으로 하며 정보 획득과 같은 본질적 보상을 통해 이를 안내합니다. 이 접근 방식은 상태, 보상 및 행동에 대한 엔트로피를 최대화하는 것과 가치 함수를 최대화하는 것 사이의 균형을 맞춥니다. **MAXINFORL**은 기존 RL 방법의 단순성을 유지하면서 본질적 보상을 통해 지시된 탐색을 추가합니다. 또한 외적 및 본질적 목표 간의 균형을 맞추는 실용적인 자동 조정 절차가 포함되어 있어 다양한 어려운 탐색 문제와 시각적 제어 작업과 같은 복잡한 시나리오에서 성능이 우수한 알고리즘을 생성합니다.

#### Boltzmann Integration
**볼츠만 탐색**은 강화 학습에서 **탐색과 활용의 균형**을 맞추는 데 널리 사용되는 방법입니다. 이 방법은 소프트 Q 함수와 온도 매개변수를 사용하여 정책 분포를 나타냅니다. 온도 매개변수는 탐색의 정도를 조절하여 값이 낮을수록 활용에, 값이 높을수록 탐색에 중점을 둡니다. 볼츠만 탐색은 ε-탐욕적 방법보다 부드러운 탐색을 제공하지만, 추정의 불확실성을 고려하지 않는다는 단점이 있습니다. 이로 인해 특히 연속 상태-행동 공간에서 탐색 작업이 어려울 수 있습니다. 이 논문에서는 정보 이득과 같은 본질적 보상을 사용하여 **볼츠만 탐색을 개선**하는 방법을 제안합니다. 제안된 MAXINFORL 프레임워크는 기존 RL 방법을 기반으로 하여 본질적 탐색 목표를 통합합니다. 이를 통해 에이전트는 기본 MDP에 대한 정보를 효율적으로 수집하면서 작업을 해결할 수 있습니다. 게다가, 외재적 및 내재적 목표 간의 균형을 맞추기 위한 실용적인 자동 조정 절차도 제시됩니다.

#### Visual Control Results
**시각 제어** 작업에서 MAXINFORL은 이미지 기반 관측에서 효과적으로 학습하는 능력을 보여주었습니다. DeepMind Control Suite의 다양한 작업과 HumanoidBench의 까다로운 Humanoid 작업에서 테스트되었습니다. MAXINFORL은 DrQ 및 DrQv2와 같은 최첨단 시각 제어 알고리즘과 결합되었으며, 그 결과 **샘플 효율성과 성능이 크게 향상**되었습니다. 특히, Humanoid 워크, 스탠드, 런과 같은 매우 어려운 탐색 작업에서 기존 방법보다 훨씬 뛰어난 성능을 보였습니다. 이러한 결과는 정보 이득 극대화를 통한 지시된 탐색의 이점과 **복잡한 시각 제어 문제에 대한 MAXINFORL의 확장성**을 강조합니다. 또한, 액션 노이즈가 없는 MAXINFODRQV2 실험을 통해 정보 이득 자체만으로도 효과적인 탐색을 위한 충분한 동기를 부여할 수 있음을 보여주었습니다. 전반적으로 이러한 결과는 다양한 까다로운 시각 제어 작업에서 MAXINFORL의 **강력한 성능과 잠재력**을 보여줍니다.

#### Sample Efficiency Gains
**샘플 효율성 향상**은 강화 학습(RL)에서 중요한 목표입니다. 샘플 효율적인 알고리즘은 **더 적은 훈련 데이터로 원하는 성능 수준에 도달**할 수 있으므로, 특히 데이터 수집 비용이 많이 드는 실제 애플리케이션에 유용합니다. 샘플 효율성을 높이기 위한 핵심 전략 중 하나는 **지시된 탐색**입니다. 이는 에이전트가 무작위로 행동하는 대신 환경에 대한 정보를 얻을 가능성이 가장 높은 행동을 선택하도록 유도하는 것을 포함합니다.  **내재적 보상**과 같은 기술은 에이전트의 호기심을 자극하고 새로운 경험을 추구하도록 동기를 부여하여 지시된 탐색을 장려하는 데 사용할 수 있습니다. 또한 **모델 기반 RL**과 같은 방법은 에이전트가 환경을 더 잘 이해하고 계획을 세울 수 있도록 하여 샘플 효율성을 높이는 데 효과적일 수 있습니다. 마지막으로 **오프 정책 학습**은 에이전트가 이전에 수집한 데이터에서 학습하여 학습 프로세스 속도를 높이고 샘플 효율성을 향상시킬 수 있습니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.12098/x2.png)

> 🔼 이 그림은 HumanoidBench 벤치마크의 세 가지 작업(서기, 걷기, 달리기)에 대한 MAXINFODRQV2의 정규화된 평균 성능을 보여줍니다. MAXINFODRQV2는 시각적 제어 작업을 위해 MAXINFORL을 DrQv2와 결합한 것입니다. 결과는 5개의 시드에 대해 평균이 계산되었으며 표준 오차가 표시되어 있으며 MAXINFODRQV2가 모든 작업에서 DrQv2보다 성능이 뛰어남을 보여줍니다. 서기 작업에서 약간의 수렴 지연이 있지만 전반적으로 더 높은 성능을 달성합니다.
> <details>
> <summary>read the caption</summary>
> (b) Normalized average performance of MaxInfoDrQv2 on the humanoid visual control tasks (stand, walk, and run).
> </details>



![](https://arxiv.org/html/2412.12098/x3.png)

> 🔼 이 그림은 MaxInfoRL의 여러 변형의 정규화된 성능을 요약한 것입니다. 상태 기반 제어에는 MaxInfoSAC를, 시각적 제어에는 MaxInfoDrQv2를 사용했습니다(자세한 내용은 4장 참조). 5개의 시드에 대한 평균 성능과 표준 오차를 나타냅니다. 왼쪽 그래프(a)는 상태 기반 작업에 대한 여러 딥 강화 학습 벤치마크에서 MaxInfoRL의 정규화된 평균 성능을 보여줍니다. 오른쪽 그래프(b)는 휴머노이드 시각 제어 작업(서기, 걷기, 달리기)에 대한 MaxInfoDrQv2의 정규화된 평균 성능을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: We summarize the normalized performance of different variants of MaxInfoRL; MaxInfoSAC for state-based control and MaxInfoDrQv2 for visual control (cf., Section 4 for more details). We report the mean performance across five seeds with one standard error.
> </details>



![](https://arxiv.org/html/2412.12098/x4.png)

> 🔼 이 그림은 OpenAI Gym과 DeepMind Control Suite 벤치마크의 여러 환경에서 MAXINFORL(녹색)을 포함한 다양한 강화 학습 알고리즘의 학습 곡선을 보여줍니다. MAXINFORL은 대부분의 작업에서 다른 방법보다 성능이 뛰어나 일관되게 더 높은 보상에 도달함을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Learning curves of all methods on several environments from the OpenAI gym and DMC suite benchmarks.
> </details>



![](https://arxiv.org/html/2412.12098/x5.png)

> 🔼 이 그림은 HumanoidBench 벤치마크에서 MaxInfoSAC와 SAC의 성능을 비교하여 보여줍니다. MaxInfoSAC는 stand 태스크를 제외한 모든 태스크에서 SAC보다 더 나은 성능을 달성했습니다. stand 태스크는 exploration이 필요없는 안정화 태스크이기 때문에, 두 알고리즘의 성능이 비슷합니다. 전반적으로 MaxInfoSAC는 SAC에 비해 샘플 효율성과 최종 성능 모두에서 향상된 결과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Performance of MaxInfoSAC and SAC on the HumanoidBench benchmark.
> </details>



![](https://arxiv.org/html/2412.12098/x6.png)

> 🔼 이 그림은 MaxInfoRL과 SAC 알고리즘을 Pendulum 환경에서 학습시키는 동안의 위상 플롯을 보여줍니다. MaxInfoSAC은 상태 공간을 SAC보다 훨씬 빠르게 커버하며, 10K 환경 interaction 내에 스윙업 과제(목표 지점: (0,0))를 효과적으로 해결합니다. SAC는 exploration이 느리기 때문에 학습 초기 단계에서 상태 공간을 효율적으로 커버하지 못합니다. 반면, MaxInfoSAC은 information gain을 통해 directed exploration을 수행하여 상태 공간을 빠르게 탐색하고 조기에 최적 정책으로 수렴합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Phase plots during learning of MaxInfoRL and SAC on the Pendulum environment. MaxInfoSAC covers the state space much faster and effectively solves the swing-up task within 10101010K environment interactions.
> </details>



![](https://arxiv.org/html/2412.12098/x7.png)

> 🔼 이 그림은 액션 비용 매개변수 \(K\)의 여러 값에 대해 상태 기반 작업에 대한 학습 곡선을 보여줍니다. 액션 비용은 에이전트가 큰 액션을 취할 때 패널티를 부과하는 데 사용됩니다. 이 그림은 MAXINFORL이 어려운 탐색 문제를 해결하는 데 있어서 기준선보다 성능이 뛰어나다는 것을 보여줍니다. 특히, MAXINFORL은 CartPole 및 Walker 작업에서 액션 비용이 있는 경우 기준선보다 성능이 뛰어납니다. 또한 그림은 펜듈럼 환경에서의 탐색 단계의 위상 도표를 보여주며, 여기서 MAXINFORL은 SAC보다 훨씬 빠르게 상태 공간을 커버합니다. 이것은 MAXINFORL이 주로 정보 획득을 통해 탐색을 유도하기 때문입니다.
> <details>
> <summary>read the caption</summary>
> Figure 5:   Learning curves for state-based tasks for different values of the action cost parameter K𝐾Kitalic_K.
> </details>



![](https://arxiv.org/html/2412.12098/x8.png)

> 🔼 이 그림은 DeepMind Control Suite의 다양한 시각적 제어 작업에 대한 학습 곡선을 보여줍니다. MAXINFODRQ(제안된 방법)는 DrQ 및 DrQv2와 비교됩니다. MAXINFODRQ가 모든 작업에서 더 높은 보상에 도달하고 기준선보다 더 나은 샘플 효율성을 달성함을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Learning curves from visual control tasks of the DMC suite.
> </details>



![](https://arxiv.org/html/2412.12098/x9.png)

> 🔼 이 그림은 DeepMind Control Suite의 Humanoid Stand, Walk, Run 태스크에 대한 학습 곡선을 보여줍니다. MAXINFODRQV2는 DrQv2에 비해 모든 태스크에서 더 높은 보상과 더 나은 샘플 효율성에 도달한다는 것을 알 수 있습니다. 이는 정보 이득을 통한 지시적 탐색의 이점을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Learning curves from the visual control humanoid tasks of the DMC suite.
> </details>



![](https://arxiv.org/html/2412.12098/x10.png)

> 🔼 이 그림은 SACEipo와 MaxInfoSAC의 내장 보상 계수 λ의 변화를 환경 상호 작용에 따라 보여줍니다. SACEipo의 경우, λ 값이 0으로 빠르게 감소하는 것을 볼 수 있는데, 이는 에이전트가 탐색을 멈추고 탐욕적인 행동을 하게 되어 지역 최적점에 수렴하게 됨을 나타냅니다. 반면, MaxInfoSAC의 경우, λ 값이 0으로 감소하지 않고, 내장 보상과 외적 보상 사이의 균형을 유지함으로써 더 나은 성능을 달성하는 것을 확인할 수 있습니다. 이는 MaxInfoSAC이 SACEipo보다 탐색과 활용 사이의 균형을 더 효과적으로 조정함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Evolution of the intrinsic reward coefficient λ𝜆\lambdaitalic_λ of SACEipo and MaxInfoSAC over environment interaction.
> </details>



![](https://arxiv.org/html/2412.12098/x11.png)

> 🔼 이 그림은 MaxInfoRL을 REDQ와 결합한 MaxInfoREDQ의 성능을 보여줍니다. Hopper, Walker, Humanoid 환경에서 SAC, REDQ, MaxInfoSAC와 MaxInfoREDQ의 학습 곡선을 비교하여 MaxInfoREDQ가 향상된 성능과 샘플 효율성을 보여주는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: We combine MaxInfoRL with REDQ (MaxInfoREDQ) and report the learning curves of SAC, REDQ, MaxInfoSAC, and MaxInfoREDQ.
> </details>



![](https://arxiv.org/html/2412.12098/x12.png)

> 🔼 이 그림은 DeepMind Control Suite의 여러 시각적 제어 작업에 대한 MaxInfoDrQv2, DrQv2, MaxInfoDrQ의 학습 곡선을 보여줍니다. MaxInfoDrQv2는 다양한 노이즈 레벨(𝜎=0.0 및 𝜎=0.2)에서 평가됩니다. 전반적으로 MaxInfoDrQv2는 모든 작업에서 다른 기준선보다 더 나은 성능과 샘플 효율성에 도달합니다. 흥미롭게도 MaxInfoDrQv2는 탐색을 위한 노이즈가 추가되지 않은 경우에도(𝜎=0.0) 여전히 DrQv2보다 성능이 뛰어납니다. 이는 정보 이득을 통해 지시된 탐색만으로도 효과적인 탐색을 달성할 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Learning curves of MaxInfoDrQv2 with different noise levels σ∈{0.0,0.2}𝜎0.00.2\sigma\in\{0.0,0.2\}italic_σ ∈ { 0.0 , 0.2 } compared to DrQv2 and MaxInfoDrQ.
> </details>



![](https://arxiv.org/html/2412.12098/x13.png)

> 🔼 이 그림은 DeepMind Control Suite의 Humanoid-Walk 태스크에 대한 MAXINFODRQV2의 성능을 DrQv2와 비교합니다. MAXINFODRQV2는 action noise 없이 학습되고 평가됩니다. action noise가 없는 DrQv2는 높은 reward를 얻는 데 어려움을 겪는 반면, action noise가 없는 MAXINFODRQV2는 여전히 좋은 성능을 보여줍니다. 이는 MAXINFODRQV2가 정보 이득을 통해 exploration을 효과적으로 수행함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: MaxInfoDrQv2 evaluated on the humanoid walk task with no action noise.
> </details>



![](https://arxiv.org/html/2412.12098/x14.png)

> 🔼 이 그림은 세 가지 다른 강화 학습 알고리즘인 MaxInfoSAC(정보 이득을 내재적 보상으로 사용), MaxInfoSAC[RND](RND를 내재적 보상으로 사용), 그리고 SAC(내재적 보상 없음)의 학습 곡선을 비교하여 보여줍니다. MaxInfoSAC[RND]는 정보 이득 대신 RND를 내재적 보상으로 사용하는 MaxInfoSAC의 변형입니다. 이 그림은 몇 가지 OpenAI Gym 및 DeepMind Control Suite 환경에서의 성능을 보여줍니다. action cost 매개변수 K의 값이 다른 세 가지 state-based 작업에 대한 학습 곡선을 표시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Learning curves of MaxInfoSAC with RND as the intrinsic reward, instead of the information gain, compared to SAC and standard MaxInfoSAC.
> </details>



![](https://arxiv.org/html/2412.12098/x15.png)

> 🔼 이 그림은 상태 기반 작업에 대한 ϵ-MaxInfoRL, SAC 및 MaxInfoSAC의 학습 곡선을 보여줍니다. ϵ-MaxInfoRL은 내재적 보상으로 불일치를 사용하며, 이는 동적 모델 앙상블의 예측 간의 차이로 계산됩니다. SAC는 순수한 외부 보상을 사용하는 반면, MaxInfoSAC는 내재적 보상과 외부 보상을 모두 사용합니다. 그림에서 볼 수 있듯이 ϵ-MaxInfoRL은 SAC보다 성능이 뛰어나고 MaxInfoSAC와 거의 동등한 성능을 보입니다. 이는 내재적 보상을 사용하여 탐색을 안내하면 순수한 외부 보상만 사용하는 것보다 더 나은 성능을 얻을 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: Learning curves of ϵitalic-ϵ\epsilonitalic_ϵ–MaxInfoRL with disagreement as the intrinsic reward, SAC and MaxInfoSAC.
> </details>



![](https://arxiv.org/html/2412.12098/x16.png)

> 🔼 이 그림은 ϵ-MaxInfoRL, SAC, MaxInfoSAC 알고리즘의 학습 곡선을 액션 비용 K의 여러 값에 대해 보여줍니다. ϵ-MaxInfoRL은 내재적 보상으로 불일치를 사용하고 기본 알고리즘으로 SAC를 사용합니다. 여기에는 Pendulum, CartPole[Swingup sparse], Walker[Run] 환경에 대한 결과가 표시됩니다. 이 그림은 섹션 4(실험)에 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: Learning curves of ϵitalic-ϵ\epsilonitalic_ϵ–MaxInfoRL with disagreement as the intrinsic reward, SAC and MaxInfoSAC for varying levels of action costs K𝐾Kitalic_K.
> </details>



![](https://arxiv.org/html/2412.12098/x17.png)

> 🔼 이 그림은 OpenAI Gym과 DeepMind Control Suite 벤치마크의 여러 환경에서 ϵ-MaxInfoRL(불일치 및 호기심을 내재적 보상으로 사용)의 학습 곡선과 SAC의 학습 곡선을 비교하여 보여줍니다. 전반적으로 불일치와 호기심 모두 SAC보다 성능이 뛰어나며 불일치가 호기심보다 약간 더 나은 성능을 보입니다.
> <details>
> <summary>read the caption</summary>
> Figure 15: Learning curves of ϵitalic-ϵ\epsilonitalic_ϵ–MaxInfoRL with disagreement and curiosity as the intrinsic reward compared with SAC.
> </details>



![](https://arxiv.org/html/2412.12098/x18.png)

> 🔼 이 그림은 ϵ-MaxInfoRL의 학습 곡선을 ϵ-MaxInfoRL이 extrinsic 정책과 intrinsic 정책 간에 전환하는 빈도를 변경하여 비교합니다. extrinsic 및 intrinsic 정책 간에 매 스텝마다 전환하는 ϵ-MaxInfoRL 버전과 32 스텝마다 전환하는 버전을 비교합니다. 결과적으로 32 스텝마다 전환하는 버전이 더 나은 성능을 보입니다. 이는 더 긴 탐색 데이터 trajectory를 수집할 수 있기 때문입니다. 따라서, 더 나은 탐색을 위해서는 exploration과 exploitation policy를 너무 자주 전환하지 않는 것이 더 좋다는 것을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 16: Learning curves of ϵitalic-ϵ\epsilonitalic_ϵ–MaxInfoRL with disagreement. We compare a version of ϵitalic-ϵ\epsilonitalic_ϵ–MaxInfoRL which switches between extrinsic and intrinsic policy every step with one which switches every 32 steps.
> </details>



![](https://arxiv.org/html/2412.12098/x19.png)

> 🔼 이 그림은 OpenAI Gym 및 DeepMind Control Suite 벤치마크의 여러 환경에서 Optimistic Actor Critic(OAC), MaxInfoSAC(본 연구에서 제안), MaxInfoRL 버전의 OAC(MaxInfoOAC)의 학습 곡선을 보여줍니다. OAC가 SAC보다 성능이 뛰어나지만 MaxInfoRL 알고리즘, 특히 MaxInfoSAC와 MaxInfoOAC는 다른 모든 방법보다 성능이 뛰어나다는 것을 알 수 있습니다. 이는 정보 이득을 통한 지시된 탐색의 이점을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 17: Learning curves of OAC compared with MaxInfoSAC and a MaxInfoRL version of OAC (MaxInfoOAC).
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