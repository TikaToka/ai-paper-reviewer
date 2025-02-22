---
title: "Discovering highly efficient low-weight quantum error-correcting codes with reinforcement learning"
summary: "강화 학습으로 저중량 양자 오류 정정 코드 설계의 난제 해결!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Machine Learning", "Reinforcement Learning", "🏢 University of Texas at Austin",]
showSummary: true
date: 2025-02-20
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.14372 {{< /keyword >}}
{{< keyword icon="writer" >}} Austin Yubo He et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-21 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.14372" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.14372" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/discovering-highly-efficient-low-weight" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

양자 컴퓨팅의 실용화를 위해서는 **양자 오류 정정 코드**의 효율성 향상이 필수적입니다. 특히, 오류 정보를 얻기 위한 측정의 가중치(weight)가 클수록 구현 비용이 증가하고 오류 발생 가능성이 높아지므로, 측정 가중치를 최소화하는 것이 중요합니다.  하지만 기존의 코드 설계 방법들은 이러한 측면에서 한계를 가지고 있으며, 특히 코드의 거리(distance)가 클수록 설계 난이도가 급격히 증가하는 문제가 있습니다.

본 연구에서는 **강화 학습(Reinforcement Learning)**을 이용하여 양자 오류 정정 코드의 가중치를 감소시키는 새로운 방법을 제시합니다.  이 방법을 통해 기존 방법보다 훨씬 효율적인 저중량 코드를 발견하였으며, **실제 양자 컴퓨팅 실험에 적용 가능한 수준**의 코드를 설계하는 데 성공했습니다. 특히, 가중치 6인 코드의 경우 기존 연구 결과 대비 1~2 Order of magnitude의 물리적 큐비트 오버헤드 감소를 달성했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 강화학습 기반의 저중량 양자 오류 정정 코드 설계 알고리즘 개발 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 기존 방법 대비 1~2 Order of magnitude 향상된 물리적 큐비트 오버헤드 감소 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 실용적인 양자 컴퓨팅 하드웨어에 적용 가능한 새로운 저중량 코드 발견 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **강화 학습을 이용한 양자 오류 정정 코드 설계의 새로운 접근법**을 제시하여, 기존 방법보다 훨씬 효율적이고 성능이 뛰어난 저중량 코드를 발견하는 데 성공했습니다. 이는 **실용적인 양자 컴퓨팅 구현에 중요한 진전**이며, 관련 연구 분야에 새로운 연구 방향을 제시합니다. 특히, **단기간 내 실현 가능한 양자 컴퓨팅 하드웨어에 적용 가능한 코드**를 발견한 것은 큰 의미가 있으며, 향후 연구의 초석을 다질 것으로 기대됩니다. 또한, **양자 코드 발견의 어려움을 극복하기 위한 강력한 도구**로서 강화 학습의 효용성을 보여주는 중요한 사례입니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.14372/extracted/6219227/training.png)

> 🔼 본 그림은 논문에서 제시하는 강화 학습(Reinforcement Learning, RL) 기반의 저중량 양자 오류 정정 코드 설계 기법을 보여줍니다. 왼쪽에는 탄너 그래프(Tanner graph)의 상태를 입력받아 간선을 추가하거나 제거하는 행위를 선택하는 RL 에이전트(agent)가 있습니다. 에이전트는 정책 네트워크(policy network)를 유지하며, 이 네트워크는 탄너 그래프의 상태를 기반으로 행위를 결정합니다. 오른쪽에는 환경(environment)이 있는데, 에이전트의 행위에 따라 그래프를 업데이트하고 코드의 새로운 거리(distance)와 가중치(weight)를 기반으로 보상(reward)을 반환합니다. 이 보상 신호는 정책 네트워크를 업데이트하는 데 사용되며, 더 나은 코드 설계를 향한 에이전트의 학습을 안내합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: An illustration of our RL scheme. The RL agent (left) maintains a policy network that, given the state of the Tanner graph, selects an action of adding or removing an edge. The environment (right) updates the graph accordingly and returns a reward based on the code’s new distance and weight. This reward signal is then used to update the policy network, guiding the agent toward better code designs.
> </details>





{{< table-caption >}}
Base Code|Hastings [44]|Sabo et al. [46]|RL(6,3)
---|---|---|---
[ [ 45 , 9 , 3 ] ] _(8,3)_|[ [ 2892 , 9 , 5 ] ] _(6,6)_|[ [ 65 , 9 , 4 ] ] _(6,3)_|[ [ 45 , 9 , 3 ] ] _(6,3)_
[ [ 74 , 4 , 4 ] ] _(6,4)_|[ [ 7466 , 4 , 6 ] ] _(6,8)_|[ [ 100 , 4 , 4 ] ] _(6,3)_|[ [ 74 , 4 , 4 ] ] _(6,3)_
[ [ 65 , 9 , 4 ] ] _(8,3)_|[ [ 6844 , 9 , 5 ] ] _(6,8)_|[ [ 89 , 9 , 4 ] ] _(6,3)_|[ [ 65 , 9 , 4 ] ] _(6,3)_
[ [ 58 , 16 , 3 ] ] _(8,3)_|[ [ 5085 , 16 , 3 ] ] _(6,8)_|[ [ 136 , 16 , 4 ] ] _(6,3)_|[ [ 58 , 16 , 3 ] ] _(6,3)_{{< /table-caption >}}

> 🔼 이 표는 Hastings 방법, Sabo 등의 방법[46], 그리고 본 논문의 강화학습(RL) 기반 가중치 감소 방법의 비교 결과를 보여줍니다.  각 방법은 기존의 양자 코드의 가중치를 줄이는 데 사용되었으며, 본 논문에서는 Hastings 방법의 결과는 참고문헌 [46]에서 가져왔습니다. 표에는 기존 코드와 각 방법을 적용한 후의 코드의 매개변수 (n, k, d, w, q)를 비교하여 각 방법의 효율성을 보여줍니다.  그림 4에서도 이 비교 결과를 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Some examples of Comparison of Hastings, Sabo et al. [46], and our RL weight reduction methods. Results using Hastings’ method are obtained from Ref. [46]. Data is also shown in Fig. 4
> </details>





### In-depth insights


#### RL for QEC Codes
본 논문은 양자 오류 정정(QEC) 코드 설계에 강화 학습(RL)을 적용하는 혁신적인 방법을 제시합니다. **기존의 QEC 코드 설계 방법들은 주로 수학적 최적화나 휴리스틱 알고리즘에 의존하여, 계산 비용이 많이 들고 코드의 성능을 제한적으로 개선하는 경향**이 있었습니다. 반면에 RL 기반의 접근 방식은 **코드의 파라미터 공간을 효율적으로 탐색하여, 기존 방법들보다 훨씬 우수한 성능을 가진 새로운 저중량 QEC 코드를 발견**할 수 있게 합니다. 특히, **RL 에이전트는 코드의 가중치와 거리 사이의 상호 작용을 학습하여, 코드의 물리적 큐비트 오버헤드를 최소화하면서 높은 오류 정정 능력을 유지**할 수 있는 최적의 코드를 설계하는데 도움을 줍니다. 이러한 RL 기반의 접근 방식은 향후 실험적인 양자 컴퓨팅 구현에 매우 유용하며, **실제 양자 컴퓨터 시스템에서의 오류 허용 범위를 확장**하는데 중요한 역할을 할 것으로 기대됩니다.

#### Weight Reduction
양자 오류 정정 코드에서 **측정 가중치(weight)**는 오류를 수정하는 데 필요한 정보를 추출하는 측정의 복잡성을 나타냅니다. 측정 가중치가 높으면 구현 비용이 증가하고 더 많은 오류가 발생할 수 있으므로, **가중치 감소(weight reduction)**는 효율적인 양자 오류 정정 코드 설계에 매우 중요합니다. 본 논문에서는 강화 학습을 이용하여 가중치 감소를 수행하는 새로운 방법을 제시합니다. 기존 방법들과 비교하여, **훨씬 적은 물리적 큐비트 오버헤드**로 높은 성능을 달성하는 새로운 저가중치 코드를 발견했습니다. 특히, **6 가중치 코드**에서 기존 결과 대비 1~2 단계의 오버헤드 감소를 보였으며, 이는 가까운 미래의 실험에서도 **실현 가능한 범위**로 가져왔습니다. 또한, 강화 학습 프레임워크를 통해 코드 파라미터 간의 상호 작용을 조사하여, 실용적인 코딩 전략의 잠재력과 효율성에 대한 새로운 통찰력을 제공합니다.

#### Code Discovery
본 논문에서 제시된 코드 발견(Code Discovery) 방법론은 강화 학습(Reinforcement Learning) 기반의 **가중치 감소(weight reduction)** 전략을 통해 양자 오류 정정 코드(Quantum Error-Correcting Code)의 효율성을 획기적으로 개선합니다. 기존의 방식들이 주로 작은 코드에 초점을 맞춰 제한적인 성과를 보였던 반면, 본 연구는 **실제적인 규모의 코드 설계**에 적용 가능한 RL 프레임워크를 제시함으로써 대규모 코드 설계의 새로운 가능성을 열었습니다. 특히, **초저가중치(low-weight)** 코드를 발견하는 데 초점을 맞춰, 기존 연구 대비 1~2차수의 물리적 큐비트 오버헤드 감소를 달성하였고, 이는 **실험적 구현의 현실성**을 크게 높였습니다.  **하이퍼그래프 곱 코드(Hypergraph Product Code)**를 기반으로 하여, RL 에이전트가 코드의 거리(distance)를 유지하면서 가중치를 효과적으로 줄이는 방법을 학습하도록 설계되어 있으며, 이를 통해 기존의 방식으로는 접근할 수 없었던 **높은 거리(high-distance)**를 갖는 코드들을 발견할 수 있었습니다. 이러한 성과는 실용적인 양자 컴퓨팅 구현에 중요한 발걸음이 될 것으로 예상됩니다.

#### RL Code Design
본 논문에서 다룬 RL 코드 설계는 기존의 양자 오류 정정 코드 설계 방식을 혁신적으로 개선한 접근 방식입니다. **강화 학습(RL)**을 기반으로, **특정 목표 거리(distance)를 가진 코드에서 시작하여 가중치(weight)를 감소시키는 전략**을 통해 보다 효율적인 코드를 발견합니다. 이는 기존의 거리 증가에 초점을 맞춘 방식과 대조적이며, **실제적인 제약 조건 하에서 더욱 효과적**임을 보여줍니다.  **특히, 하이퍼그래프 곱셈 코드(hypergraph product codes)**에 RL을 적용하여,  기존 방법 대비 훨씬 적은 물리적 큐비트 오버헤드로 높은 거리의 저가중치 코드를 생성하는 결과를 제시합니다. **실험적으로 구현 가능한 범위**까지 코드의 효율성을 높였으며, **향후 양자 오류 정정 기술의 실제 구현에 중요한 의미**를 갖습니다.  **다양한 코드 파라미터들 간의 상호 작용을 분석**하여, 실용적인 코드 전략에 대한 새로운 통찰력을 제공합니다.

#### Future Work
본 논문에서 제시된 강화학습 기반 저중량 안정화 QEC 코드 설계 기법은 **차세대 양자 컴퓨팅 기술 발전에 크게 기여할 잠재력**을 가지고 있습니다.  **향후 연구 방향**으로는 첫째, **다양한 제약 조건을 고려한 코드 설계**가 중요합니다. 기하학적 제약, 논리적 연산의 존재 여부, 큐비트 종류 등을 고려하여 보다 실용적인 코드를 발견해야 합니다. 둘째, **더욱 효율적인 강화학습 알고리즘**의 개발과 **대규모 코드 설계**를 위한 확장성 확보가 필수적입니다.  본 논문에서 사용한 PPO 알고리즘은 효율적이지만, 더욱 복잡한 코드 설계 문제에는 한계가 있을 수 있습니다.  따라서 더욱 발전된 알고리즘이나 병렬 컴퓨팅 기법을 활용하는 방안을 모색해야 합니다. 셋째, **실제 양자 컴퓨터 하드웨어와의 호환성**을 고려해야 합니다.  설계된 코드가 실제 하드웨어에서 효율적으로 구현될 수 있도록 아키텍처 및 제약 조건들을 고려해야 합니다. 마지막으로, **오류 정정 코드의 성능 분석**을 심층적으로 수행하고 **최적화 방안을 제시**해야 합니다. 특히, 다양한 오류 모델과 디코딩 알고리즘을 고려한 분석이 필요합니다. 이러한 연구들을 통해 **실제 양자 오류 허용 컴퓨팅 시스템 구축**에 더욱 가까이 다가갈 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.14372/extracted/6219227/evolution2.png)

> 🔼 그림 2(a)는 강화 학습 기반 코드 설계 과정에서 다양한 매개변수를 가진 코드들의 학습 경로를 보여줍니다. 세 개의 다른 코드([976,16,12](10,15), [865,49,10](16,13), [720,144,8](16,7))에 대한 학습 궤적을 평균 3회 실행하여 나타냈습니다. 각 코드의 매개변수는 시간에 따라 어떻게 변화하는지, 그리고 보상이 어떻게 변화하는지 보여줍니다. 이를 통해 강화 학습 에이전트가 시간이 지남에 따라 보다 효율적인 코드를 설계하는 방법을 이해할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (a)
> </details>



![](https://arxiv.org/html/2502.14372/extracted/6219227/pca.png)

> 🔼 그림 (b)는 강화 학습 기반 코드 설계의 한 에피소드에서 시간에 따른 매개변수의 변화를 보여줍니다. 세 개의 예시 코드에 대한 가중치, 차수, 거리 매개변수의 변화를 추적하여 시간에 따른 RL 에이전트의 학습 과정을 보여줍니다. 가중치와 차수가 점진적으로 감소함에 따라 거리가 감소하다가 일정 수준에 도달한 후 급격히 증가하는 것을 알 수 있습니다. 이는 RL 에이전트가 코드의 가중치와 차수를 줄이면서 동시에 거리를 유지하거나 개선하는 방법을 학습하는 것을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b)
> </details>



![](https://arxiv.org/html/2502.14372/extracted/6219227/parallel_coords_300dpi.png)

> 🔼 그림 (c)는 강화 학습 기반의 코드 설계 과정에서 10개 에피소드에 걸쳐 탐색된 탄너 그래프 상태 공간을 PCA(주성분 분석)로 분해하여 시각화한 것입니다. 각 색상은 하나의 에피소드를 나타내며, 시간에 따른 탄너 그래프의 변화 과정을 보여줍니다. 주성분 1(PC1)과 주성분 2(PC2)는 탄너 그래프의 주요 특징들을 반영하며, 에피소드가 진행됨에 따라 탄너 그래프가 어떻게 변화하고 최적화되는지 보여줍니다. 이 그림은 강화 학습 에이전트가 코드 설계 공간을 효율적으로 탐색하고, 최적의 코드 디자인을 찾아가는 과정을 시각적으로 보여주는 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> (c)
> </details>



![](https://arxiv.org/html/2502.14372/extracted/6219227/hastingsandn30.png)

> 🔼 그림 2는 강화 학습 기반 양자 오류 정정 코드 설계 과정을 보여줍니다. (a)는 다양한 매개변수를 가진 코드들의 훈련 경로를 3번의 실행에 걸쳐 평균낸 그래프입니다. 각 점은 특정 시점에서 코드의 성능을 나타내며, 전체적인 경향성을 파악하는 데 도움이 됩니다. (b)는 세 가지 예시 코드에 대해 한 에피소드 동안 매개변수의 변화를 보여주는 그래프입니다. 각 코드의 거리, 가중치, 차수 등의 매개변수가 시간에 따라 어떻게 변하는지 자세히 살펴볼 수 있습니다.  (c)는 주성분 분석(PCA)을 통해 차원 축소된 상태 공간에서 10개의 에피소드 탐색 경로를 다양한 색상으로 표현한 그래프입니다. 각 에피소드의 탐색 경로를 시각화하여 강화 학습 에이전트가 상태 공간을 어떻게 탐색하는지 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Reinforcement learning-driven code design. (a) Training trajectories of codes with varying parameters averaged over 3 runs. (b) Evolution of parameters in the three example codes throughout a single episode.(c) Exploration of 10 episodes (represented by different colors) over PCA decomposition of state space.
> </details>



![](https://arxiv.org/html/2502.14372/extracted/6219227/overheadoverall2.png)

> 🔼 그림 3은 가중치 감소 후 초대칭 곱 코드(파란색)와 강화 학습 최적화 코드(빨간색)의 매개변수를 비교한 병렬 좌표 플롯입니다. 각 색상에 대해 매개변수가 다른 475개의 코드(HGP-30 체제를 넘어서는 10개의 고거리 코드 포함)가 표시됩니다. 각 수직축은 해당 매개변수에 대해 관찰된 최대값으로 정규화되며, 각 선은 단일 코드의 매개변수를 모든 축에 걸쳐 추적합니다. 이 그림은 강화 학습 기반의 가중치 감소 방법을 사용하여 생성된 코드의 매개변수가 기존의 초대칭 곱 코드와 어떻게 다른지를 시각적으로 보여줍니다. 특히, 가중치와 큐비트 차수가 감소하고, 코드 길이가 증가하는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3:  Parallel coordinates plot comparing hypergraph product base codes (blue) and RL-optimized codes (red) after weight reduction. For each color, 475 codes (including 10 high-distance ones beyond the HGP-30 regime) with varying parameters are shown. Each vertical axis is normalized to the maximum observed value for that parameter, and each line traces a single code’s parameters across all axes.
> </details>



![](https://arxiv.org/html/2502.14372/extracted/6219227/ratevsreld.png)

> 🔼 그림 4는 제안된 강화 학습 기반 방법과 기존 가중치 감소 방법을 비교하여 얻은 결과를 보여줍니다. 상단 그래프는 Hastings [45] (Ref. [46]의 데이터 사용) 및 Sabo et al. [46]의 최첨단(SOTA) 결과와의 비교를 나타냅니다. 하단 그래프는 n≤30인 고전 부호로 구성된 모든 초그래프 곱 부호에 대한 SOTA 결과와의 비교를 보여줍니다. 표 1과 2에는 구체적인 부호 매개변수가 나와 있습니다. 이 그림은 제안된 방법이 기존 방법보다 훨씬 효율적이고 우수한 성능을 가짐을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4:  Comparisons of codes discovered by our RL-based scheme and existing weight reduction methods. (top) Comparison with Hastings [45] (data taken from Ref. [46]) and SOTA results from Sabo et al. [46]. (bottom) Comparisons with SOTA results on all hypergraph product codes constructed from n≤30𝑛30n\leq 30italic_n ≤ 30 classical codes. Explicit code parameters are shown in Table 1, 2.
> </details>



![](https://arxiv.org/html/2502.14372/extracted/6219227/rldistances.png)

> 🔼 그림 5는 다양한 코드 매개변수 (n, k, d)에 따른 오버헤드 계수를 히트맵으로 보여줍니다. 위쪽 행은 제시된 강화 학습 기반 가중치 축소 방식으로 생성된 코드를 나타내고 아래쪽 행은 Sabo 등의 방법으로 생성된 코드를 나타냅니다. 시각화를 위해 기울기는 구간화되어 있으며, 다양한 스케일로 인해 오버헤드 계수의 정확한 표현은 아닙니다. 이 그림은 코드의 크기(n)과 코드 비율(k/n), 거리(d)가 다양하게 변화할 때 RL 방법과 Sabo 등의 방법을 사용하여 가중치를 감소시켰을 때의 오버헤드 비율을 비교 분석합니다.  각 히트맵은 색상의 농도 차이를 통해 오버헤드 비율의 크기를 나타내며,  색상이 짙을수록 오버헤드 비율이 높음을 의미합니다. 이를 통해 두 가지 방법의 효율성을 시각적으로 비교하고 각 방법의 장단점을 파악할 수 있습니다. 특히 코드의 크기와 거리에 따른 오버헤드 비율의 변화 추이를 명확하게 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Breakdown of overhead factors shown by heatmaps at varying n𝑛nitalic_n, k𝑘kitalic_k, d𝑑ditalic_d parameters. The top and bottom rows correspond to codes discovered by our RL weight-reduction scheme and Sabo et al.’s method, respectively. Gradients are binned for ease of visualization and not exact representations of overhead factors, as seen in the varying scales.
> </details>



![](https://arxiv.org/html/2502.14372/extracted/6219227/hgpscatterplots.png)

> 🔼 그림 2(a)는 강화 학습 기반 코드 설계의 훈련 과정을 보여줍니다. 세 가지 다른 매개변수를 가진 코드에 대한 보상 곡선의 평균값을 3회 실행에 걸쳐 보여줍니다. 각 코드의 보상 곡선은 고유한 색상으로 표시되어 구별이 용이합니다. 그래프의 x축은 시간 단계를 나타내고 y축은 보상 값을 나타냅니다. 이 그래프는 강화 학습 에이전트가 시간이 지남에 따라 보상을 최대화하기 위해 코드 매개변수를 최적화하는 과정을 시각적으로 보여줍니다.  세 가지 다른 코드에 대한 보상 곡선을 비교하여, 서로 다른 초기 조건과 매개변수에서도 강화 학습 에이전트가 최적의 코드 디자인을 찾아가는 과정을 효과적으로 설명합니다.
> <details>
> <summary>read the caption</summary>
> (a)
> </details>



![](https://arxiv.org/html/2502.14372/extracted/6219227/rlscatterplots.png)

> 🔼 그림 (b)는 강화 학습 기반 코드 설계 과정을 보여줍니다. 세 개의 예시 코드에 대한 한 에피소드 동안의 가중치, 차수, 거리 매개변수의 변화를 시간에 따라 나타냅니다. 각 코드에 대해 세 가지 매개변수 (가중치, 차수, 거리)의 변화가 시간에 따라 그래프로 표시됩니다. 이를 통해 강화 학습 에이전트가 코드의 가중치와 차수를 점진적으로 줄이는 동시에 거리를 유지하거나 증가시키는 방법을 보여줍니다. 세 개의 예시 코드 모두 비슷한 범위의 보상에 수렴하지만, 더 큰 최대 거리를 가진 코드의 학습 과정은 더욱 확률적임을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (b)
> </details>



![](https://arxiv.org/html/2502.14372/extracted/6219227/reducedistance.png)

> 🔼 그림 (c)는 강화 학습 기반의 코드 설계 과정에서 탐색된 10개 에피소드의 탐색 영역을 주성분 분석(PCA)으로 축소하여 시각화한 것입니다. 각 색상은 하나의 에피소드를 나타내며, 가로축과 세로축은 주성분을 나타냅니다. 이 그림을 통해 RL 에이전트가 탐색 공간을 효율적으로 탐색하여 최적의 코드 디자인을 찾는 과정을 보여줍니다. 즉, 초기에는 다양한 코드 디자인을 탐색하다가, 학습이 진행될수록 더욱 효율적인 코드 디자인 영역에 집중하는 모습을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (c)
> </details>



![](https://arxiv.org/html/2502.14372/extracted/6219227/spectralgap.png)

> 🔼 그림 6은 RL 기반의 가중치 감소 및 코드 설계에 대한 기존 최고 성능(SOTA)과의 비교 결과를 보여줍니다. (a)는 고전적 코드를 기반으로 생성된 모든 초그래프 곱셈 코드에 대해 RL과 SOTA의 (6,3) 가중치 감소에 대한 큐비트 오버헤드를 비교한 것입니다. (b)는 가중치 감소된 코드와 초그래프 곱셈 기본 코드의 비율 대비 상대 거리를 비교한 것입니다. (c)는 다양한 대안 RL 코드 설계 방법과 코드 매개변수를 비교한 것으로, HGP-30 영역을 벗어난 추가적인 (6,3) 코드 10개가 RL 모델을 사용하여 생성되어 특히 높은 거리의 코드 예시를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6:  Comparisons against SOTA on weight reduction and RL code design. (a) Comparison of qubit overheads of weight reduction to (6,3) between RL and SOTA on all hypergraph product codes constructed from classical codes with n≤30𝑛30n\leq 30italic_n ≤ 30. (b) Rate vs. relative distance for weight-reduced vs. hypergraph product base codes. (c) Comparisons of code parameters against various alternative RL methods for code design. Ten additional (6,3) codes (labeled by diamonds) beyond the HGP-30 regime were produced using our RL model to display examples of particularly high distance codes.
> </details>



![](https://arxiv.org/html/2502.14372/extracted/6219227/eigenvaluespectrogram.png)

> 🔼 그림 (a)는 강화 학습 기반 코드 설계에서 에이전트가 시간 경과에 따라 학습한 내용을 보여줍니다.  x축은 시간 단계(Time Step)이고, y축은 보상(Reward)입니다.  세 개의 다른 코드(파란색, 주황색, 녹색)의 학습 경로가 표시되어 있습니다. 각 코드는 다른 매개변수를 가지며, 보상은 코드의 거리(distance)와 가중치(weight)를 고려하여 계산됩니다.  그림은 강화 학습 에이전트가 시간이 지남에 따라 보상을 극대화하도록 정책(policy)을 최적화하는 과정을 보여줍니다. 각 코드의 학습 경로는 다르지만, 전반적으로 보상이 시간이 지남에 따라 증가하는 경향을 보입니다.
> <details>
> <summary>read the caption</summary>
> (a)
> </details>



![](https://arxiv.org/html/2502.14372/extracted/6219227/paretofronts.png)

> 🔼 그림 2(b)는 강화 학습 기반 코드 설계 과정에서 세 가지 예시 코드의 매개변수 변화를 시간에 따라 보여줍니다. 세 가지 코드 모두에서 가중치, 차수, 거리 매개변수가 학습 에피소드 동안 어떻게 변화하는지를 보여주는 그래프가 포함되어 있습니다. 이를 통해 강화 학습 에이전트가 코드의 가중치와 차수를 감소시키면서 동시에 거리를 유지하거나 향상시키는 과정을 자세히 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> (b)
> </details>



![](https://arxiv.org/html/2502.14372/extracted/6219227/metaanalysisd.png)

> 🔼 그림 7은 RL 기반 가중치 감소 알고리즘을 적용하기 전과 후의 초고속 제품 코드(HGP-30)의 매개변수에 대한 쌍별 산점도를 보여줍니다. (a)는 가중치 감소 전의 초고속 제품 코드의 매개변수(n, k, d, w, q)를, (b)는 가중치 감소 후 RL 코드의 매개변수를 보여줍니다. 각각의 소그림은 두 개의 매개변수를 비교하며, 대각선 요소는 개별 매개변수의 분포를 나타냅니다. 이 그림을 통해 가중치 감소 전후의 코드 매개변수 변화를 직관적으로 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7:  Pairwise scatter plots for the parameters of the HGP-30 base codes and RL codes. (a) Hypergraph product code with parameters n,k,d,w,q𝑛𝑘𝑑𝑤𝑞n,k,d,w,qitalic_n , italic_k , italic_d , italic_w , italic_q before weight reduction, (b) RL codes after weight reduction. Each subplot compares two parameters (off-diagonal) while the diagonal entries depict individual parameter distributions.
> </details>



![](https://arxiv.org/html/2502.14372/extracted/6219227/metaanalysisk.png)

> 🔼 그림 8은 완화된 거리 제약 조건 하에서 최소 큐비트 오버헤드를 보여줍니다. 거리 d를 감소시키는 것을 허용하면 총 큐비트 오버헤드를 줄일 수 있습니다. 이 그림은 다양한 코드 매개변수를 가진 여러 코드에 대한 큐비트 오버헤드를 보여주는 히트맵으로 구성됩니다. 각 히트맵은 코드의 길이(n), 코드의 비율(k/n), 코드의 거리(d)의 세 가지 매개변수에 따른 오버헤드를 나타냅니다.  표 4는 각 히트맵에 사용된 코드 매개변수를 자세히 보여줍니다.  이를 통해 다양한 코드 매개변수 조합에서 최소 큐비트 오버헤드를 달성하기 위한 거리와 코드 매개변수 사이의 절충 관계를 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Minimum qubit overheads under relaxed distance constraints. Permitting the distance d𝑑ditalic_d to decrease can reduce the total qubit overhead. Code parameters are shown in Table 4
> </details>



![](https://arxiv.org/html/2502.14372/extracted/6219227/metaanalysishgpd.png)

> 🔼 그림 2(a)는 다양한 매개변수를 가진 코드의 강화 학습 기반 코드 설계에 대한 훈련 경로를 보여줍니다. 세 개의 다른 코드에 대한 평균 훈련 경로가 세 개의 별개의 선으로 표시됩니다. 각 코드의 매개변수는 코드의 길이(n), 논리 큐비트의 수(k), 코드 거리(d)를 나타냅니다.  시간 단계에 따른 보상의 변화를 보여주는 그래프로, 강화학습 에이전트가 최적의 코드 설계를 찾아가는 과정을 보여줍니다.  보상은 코드의 거리와 가중치에 따라 달라집니다. 이 그림은 강화 학습 알고리즘이 효과적으로 작동하고, 다양한 매개변수를 가진 코드를 설계할 수 있음을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (a)
> </details>



![](https://arxiv.org/html/2502.14372/extracted/6219227/metaanalysishgpk.png)

> 🔼 그림 2(b)는 강화 학습 기반 코드 설계 과정에서 세 가지 예시 코드의 매개변수 변화를 보여줍니다. 시간에 따른 가중치(weight), 차수(degree), 거리(distance) 매개변수의 변화 양상을 나타내는 그래프입니다. 각 매개변수는 학습 에피소드의 시간에 따라 어떻게 변화하는지 보여주며, 강화 학습 에이전트가 코드 최적화를 위해 매개변수들을 어떻게 조정하는지를 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b)
> </details>



![](https://arxiv.org/html/2502.14372/extracted/6219227/hgpregressions.png)

> 🔼 그림 9는 강화 학습 에이전트가 Tanner 그래프의 특성을 변화시키는 과정을 보여줍니다. (a)는 스펙트럼 간격(spectral gap)의 변화를, (b)는 Tanner 그래프의 고유값(eigenvalues) 분포 변화를 나타냅니다. 강화 학습 에이전트는 Tanner 그래프의 가중치와 차수를 줄이는 동시에 스펙트럼 간격을 0.5 이하로 감소시킵니다. 생성된 코드는 이론적 구조와 다르며, 거의 랜덤한 고유값 분포를 가집니다. 이는 확장 관련 논의에 의존하는 이론적 구조와는 다르지만, 메시지 전달 기반 디코딩 성능은 저하될 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: (a) Spectral gap evolution. Our RL agent causes the Tanner graphs to rapidly lose their expander properties, with the gap λ1−λ2subscript𝜆1subscript𝜆2\lambda_{1}-\lambda_{2}italic_λ start_POSTSUBSCRIPT 1 end_POSTSUBSCRIPT - italic_λ start_POSTSUBSCRIPT 2 end_POSTSUBSCRIPT stabilizing around ≤0.5absent0.5\leq 0.5≤ 0.5. This happens simultaneously to reduction of weight and degree in the Tanner graph. (b) Tanner graph eigenvalues evolution. The eigenvalues begin concentrated around +11+1+ 1 and −11-1- 1, and spread out quickly. It is interesting that the codes our agent finds are significantly less structured and tend to have nearly random eigenvalue distributions. This suggests that our agent finds codes largely outside the realm of theoretical constructions, which often tend to rely on expansion-related arguments, although this is also at the cost of worse performance on message-passing-based decoding.
> </details>



![](https://arxiv.org/html/2502.14372/extracted/6219227/rlregressions.png)

> 🔼 그림 10은 강화 학습(RL) 에이전트가 발견한 국소적으로 최적화된 (n, k, d) 코드의 파레토 프런트를 보여줍니다.  가로축은 물리적 큐비트 수(n), 세로축은 코드의 거리(d)를 나타냅니다. 각 점은 특정한 코드를 나타내며, 점의 좌표는 해당 코드의 n과 d 값입니다.  점들의 분포는 RL 알고리즘이 찾은 최적의 코드들이 어떤 성능 특징을 가지는지 보여줍니다. 특히, 가중치 감소 설정에서 k/n과 d/n을 개선할 수 있는 상당한 기회가 있음을 보여줍니다. 하이퍼그래프 곱셈 코드는 이론적 한계에 도달할 수 없기 때문에, RL 에이전트가 발견한 코드들은 이러한 제약을 뛰어넘는 가능성을 시사합니다.  본문에 언급된 추가적인 10개의 점은 그래프에서 제외되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Pareto fronts of n,k,d𝑛𝑘𝑑n,k,ditalic_n , italic_k , italic_d parameters. The plotted Pareto fronts show locally optimal (n,k,d)𝑛𝑘𝑑(n,k,d)( italic_n , italic_k , italic_d ) codes found by our RL agent. We observe there is considerable opportunity to improve k/n𝑘𝑛k/nitalic_k / italic_n and d/n𝑑𝑛d/nitalic_d / italic_n in the weight-reduction setting, especially since hypergraph product code codes cannot reach certain theoretical bounds. Note: The 10 additional points discussed in the main text are omitted from these plots.
> </details>



![](https://arxiv.org/html/2502.14372/extracted/6219227/extrapolations.png)

> 🔼 그림 2(a)는 강화 학습 기반 코드 설계의 훈련 과정을 보여줍니다. 세 가지 다른 매개변수를 가진 코드에 대한 3회 실행에 걸친 평균 보상 곡선을 나타냅니다. 각 곡선은 코드의 보상이 시간에 따라 어떻게 변화하는지 보여주는 것으로, 강화 학습 에이전트가 더 나은 코드 디자인을 찾아가는 과정을 시각적으로 보여줍니다. 세 가지 코드 모두 유사한 범위의 보상에 수렴하지만, 최대 거리가 더 큰 코드는 보다 불규칙적인 학습 과정을 보입니다. 이는 최대 거리가 클수록 강화 학습이 최적의 코드를 찾는 것이 더 어려움을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (a)
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
Base Code|RL(6,3)|RL(8,4)|SOTA
---|---|---|
[ [ 1741 , 1 , 30 ] ]<sub>(4,2)</sub>|[ [ 1741 , 1 , 30 ] ]<sub>(4,2)</sub>|[ [ 1741 , 1 , 30 ] ]<sub>(4,2)</sub>|[ [ 1741 , 1 , 30 ] ]<sub>(4,2)</sub>
[ [ 1684 , 4 , 20 ] ]<sub>(6,19)</sub>|[ [ 1802 , 4 , 20 ] ]<sub>(6,3)</sub>|[ [ 1741 , 4 , 20 ] ]<sub>(8,4)</sub>|[ [ 7444 , 4 , 36 ] ]<sub>(6,3)</sub>
[ [ 1629 , 9 , 16 ] ]<sub>(8,15)</sub>|[ [ 1745 , 9 , 16 ] ]<sub>(6,3)</sub>|[ [ 1745 , 9 , 16 ] ]<sub>(8,4)</sub>|[ [ 9389 , 9 , 29 ] ]<sub>(6,3)</sub>
[ [ 1576 , 16 , 16 ] ]<sub>(10,15)</sub>|[ [ 1930 , 16 , 16 ] ]<sub>(6,3)</sub>|[ [ 1690 , 16 , 16 ] ]<sub>(8,4)</sub>|[ [ 15496 , 16 , 33 ] ]<sub>(6,3)</sub>
[ [ 1525 , 25 , 15 ] ]<sub>(12,15)</sub>|[ [ 2125 , 25 , 15 ] ]<sub>(6,3)</sub>|[ [ 1997 , 25 , 15 ] ]<sub>(8,4)</sub>|[ [ 23557 , 25 , 33 ] ]<sub>(6,3)</sub>
[ [ 1476 , 36 , 14 ] ]<sub>(12,15)</sub>|[ [ 2330 , 36 , 14 ] ]<sub>(6,3)</sub>|[ [ 2066 , 36 , 14 ] ]<sub>(8,4)</sub>|[ [ 33300 , 36 , 36 ] ]<sub>(6,3)</sub>
[ [ 1429 , 49 , 12 ] ]<sub>(14,11)</sub>|[ [ 2137 , 49 , 12 ] ]<sub>(6,3)</sub>|[ [ 1765 , 49 , 12 ] ]<sub>(8,4)</sub>|[ [ 27637 , 49 , 28 ] ]<sub>(6,3)</sub>
[ [ 1384 , 64 , 12 ] ]<sub>(16,15)</sub>|[ [ 2624 , 64 , 12 ] ]<sub>(6,3)</sub>|[ [ 1954 , 64 , 12 ] ]<sub>(8,4)</sub>|[ [ 41504 , 64 , 33 ] ]<sub>(6,3)</sub>
[ [ 1341 , 81 , 12 ] ]<sub>(18,15)</sub>|[ [ 3161 , 81 , 12 ] ]<sub>(6,3)</sub>|[ [ 2153 , 81 , 12 ] ]<sub>(8,4)</sub>|[ [ 52853 , 81 , 33 ] ]<sub>(6,3)</sub>
[ [ 1300 , 100 , 11 ] ]<sub>(20,14)</sub>|[ [ 3412 , 100 , 11 ] ]<sub>(6,3)</sub>|[ [ 2228 , 100 , 11 ] ]<sub>(8,4)</sub>|[ [ 59908 , 100 , 35 ] ]<sub>(6,3)</sub>
[ [ 1261 , 121 , 10 ] ]<sub>(18,13)</sub>|[ [ 3673 , 121 , 10 ] ]<sub>(6,3)</sub>|[ [ 2173 , 121 , 10 ] ]<sub>(8,4)</sub>|[ [ 70373 , 121 , 32 ] ]<sub>(6,3)</sub>
[ [ 1224 , 144 , 9 ] ]<sub>(22,13)</sub>|[ [ 3944 , 144 , 9 ] ]<sub>(6,3)</sub>|[ [ 2120 , 144 , 9 ] ]<sub>(8,4)</sub>|[ [ 73800 , 144 , 28 ] ]<sub>(6,3)</sub>
[ [ 1189 , 169 , 8 ] ]<sub>(24,11)</sub>|[ [ 4225 , 169 , 8 ] ]<sub>(6,3)</sub>|[ [ 2069 , 169 , 8 ] ]<sub>(8,4)</sub>|[ [ 44785 , 169 , 22 ] ]<sub>(6,3)</sub>
[ [ 1156 , 196 , 8 ] ]<sub>(22,11)</sub>|[ [ 4706 , 196 , 8 ] ]<sub>(6,3)</sub>|[ [ 2146 , 196 , 8 ] ]<sub>(8,4)</sub>|[ [ 51940 , 196 , 23 ] ]<sub>(6,3)</sub>
[ [ 1125 , 225 , 8 ] ]<sub>(26,11)</sub>|[ [ 5417 , 225 , 8 ] ]<sub>(6,3)</sub>|[ [ 2493 , 225 , 8 ] ]<sub>(8,4)</sub>|[ [ 66346 , 225 , 23 ] ]<sub>(6,3)</sub>
[ [ 1096 , 256 , 7 ] ]<sub>(24,11)</sub>|[ [ 6626 , 256 , 7 ] ]<sub>(6,3)</sub>|[ [ 2440 , 256 , 7 ] ]<sub>(8,4)</sub>|[ [ 63496 , 256 , 22 ] ]<sub>(6,3)</sub>
[ [ 1069 , 289 , 6 ] ]<sub>(24,7)</sub>|[ [ 6529 , 289 , 6 ] ]<sub>(6,3)</sub>|[ [ 2389 , 289 , 6 ] ]<sub>(8,4)</sub>|[ [ 40757 , 289 , 15 ] ]<sub>(6,3)</sub>
[ [ 1044 , 324 , 6 ] ]<sub>(36,9)</sub>|[ [ 6660 , 324 , 7 ] ]<sub>(6,3)</sub>|[ [ 2612 , 324 , 6 ] ]<sub>(8,4)</sub>|[ [ 54612 , 324 , 18 ] ]<sub>(6,3)</sub>
[ [ 1021 , 361 , 6 ] ]<sub>(36,9)</sub>|[ [ 8761 , 361 , 6 ] ]<sub>(6,3)</sub>|[ [ 2845 , 361 , 6 ] ]<sub>(8,4)</sub>|[ [ 56293 , 361 , 20 ] ]<sub>(6,3)</sub>
[ [ 1000 , 400 , 5 ] ]<sub>(38,8)</sub>|[ [ 6928 , 400 , 5 ] ]<sub>(6,3)</sub>|[ [ 2792 , 400 , 5 ] ]<sub>(8,4)</sub>|[ [ 50128 , 400 , 20 ] ]<sub>(6,3)</sub>
[ [ 981 , 441 , 4 ] ]<sub>(32,5)</sub>|[ [ 7301 , 441 , 4 ] ]<sub>(6,3)</sub>|[ [ 2465 , 441 , 4 ] ]<sub>(8,4)</sub>|[ [ 10733 , 441 , 7 ] ]<sub>(6,3)</sub>
[ [ 964 , 484 , 4 ] ]<sub>(32,5)</sub>|[ [ 7684 , 484 , 4 ] ]<sub>(6,3)</sub>|[ [ 2692 , 484 , 4 ] ]<sub>(8,4)</sub>|[ [ 14692 , 484 , 7 ] ]<sub>(6,3)</sub>
[ [ 949 , 529 , 4 ] ]<sub>(28,5)</sub>|[ [ 9649 , 529 , 4 ] ]<sub>(6,3)</sub>|[ [ 2785 , 529 , 4 ] ]<sub>(8,4)</sub>|[ [ 12277 , 529 , 7 ] ]<sub>(6,3)</sub>
[ [ 936 , 576 , 4 ] ]<sub>(30,5)</sub>|[ [ 12456 , 576 , 4 ] ]<sub>(6,3)</sub>|[ [ 3026 , 576 , 4 ] ]<sub>(8,4)</sub>|[ [ 17960 , 576 , 11 ] ]<sub>(6,3)</sub>
[ [ 925 , 625 , 3 ] ]<sub>(32,5)</sub>|[ [ 6925 , 625 , 3 ] ]<sub>(6,3)</sub>|[ [ 3277 , 625 , 3 ] ]<sub>(8,4)</sub>|[ [ 15625 , 625 , 9 ] ]<sub>(6,3)</sub>
[ [ 916 , 676 , 2 ] ]<sub>(54,1)</sub>|[ [ 1396 , 676 , 2 ] ]<sub>(6,3)</sub>|[ [ 1396 , 676 , 2 ] ]<sub>(8,4)</sub>|[ [ 2294 , 676 , 2 ] ]<sub>(6,2)</sub>
[ [ 909 , 729 , 2 ] ]<sub>(56,1)</sub>|[ [ 1469 , 729 , 2 ] ]<sub>(6,3)</sub>|[ [ 1469 , 729 , 2 ] ]<sub>(8,4)</sub>|[ [ 3809 , 729 , 2 ] ]<sub>(6,2)</sub>
[ [ 904 , 784 , 2 ] ]<sub>(58,1)</sub>|[ [ 1544 , 784 , 2 ] ]<sub>(6,3)</sub>|[ [ 1544 , 784 , 2 ] ]<sub>(8,4)</sub>|[ [ 3920 , 784 , 2 ] ]<sub>(6,2)</sub>
[ [ 900 , 900 , 1 ] ]<sub>(2,1)</sub>|[ [ 900 , 900 , 1 ] ]<sub>(2,1)</sub>|[ [ 900 , 900 , 1 ] ]<sub>(2,1)</sub>|[ [ 900 , 900 , 1 ] ]<sub>(2,1)</sub>{{< /table-caption >}}
> 🔼 표 2는 논문의 주요 결과 중 하나로, 강화 학습(Reinforcement Learning) 기반의 오류 정정 코드 설계 방법의 성능을 보여줍니다.  특히, 기존 최고 성능(SOTA) 방법과 비교하여, 제한된 무게(weight)와 차수(degree)를 갖는 양자 오류 정정 코드의 생성에서 RL(6,3) 및 RL(8,4) 기법의 우수성을 보여주는 데이터를 제시합니다. 표에는 기존의 초고밀도 패리티 검사(LDPC) 코드 생성 방식을 기반으로 생성한 코드와 RL 기반 코드 생성 방식을 통해 얻어낸 코드들의 크기(n), 논리 큐비트 수(k), 최소 거리(d), 무게(w), 큐비트 차수(q) 등의 파라미터를 비교하여, RL 기법의 효율성을 보여줍니다. 그림 4에서도 이 표의 내용이 시각적으로 표현되어 있습니다.  이 표를 통해 독자는 RL 기반의 양자 오류 정정 코드 설계가 기존 방법보다 훨씬 효율적이며, 실제적인 양자 컴퓨팅 구현에 더욱 적합함을 이해할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Comparison of RL(6,3), RL(8,4), against SOTA on hypergraph product codes constructed from n=30𝑛30n=30italic_n = 30 classical codes. Data is also shown in Fig. 4
> </details>

{{< table-caption >}}
Reduced Code|Base Code
---|---|---
RL(6,3)|[\[[2257,25,15]\]]\[(6,3)\]|[\[[1525,25,15]\]]\[(12,15)\]
Sabo et al. [46]|[\[[2257,25,13]\]]\[(6,3)\]|[\[[277,25,6]\]]\[(6,10)\]
|[\[[3457,25,15]\]]\[(6,3)\]||[\[[325,25,7]\]]\[(12,7)\]
|[\[[4337,25,17]\]]\[(6,3)\]||[\[[377,25,9]\]]\[(12,7)\]
|[\[[4153,25,16]\]]\[(6,3)\]||[\[[433,25,8]\]]\[(10,7)\]
|[\[[4337,25,16]\]]\[(6,3)\]||[\[[493,25,8]\]]\[(10,7)\]
|[\[[4525,25,17]\]]\[(6,3)\]||[\[[557,25,8]\]]\[(10,7)\]{{< /table-caption >}}
> 🔼 이 표는 RL(Reinforcement Learning) 기반 방법과 Sabo 등의 방법[46]을 사용하여 생성된 코드의 매개변수를 비교한 것입니다.  Sabo 등의 방법은 여러 다른 기저 코드를 사용하여 100번의 시도를 거쳐 최대 거리를 갖는 코드를 선택하는 방식입니다. 표에는 RL 기반 방법으로 생성된 코드와 Sabo 등의 방법으로 생성된 코드의 매개변수 ([n, k, d](w, q))를 비교하여 RL 기반 방법의 우수성을 보여줍니다.  각 코드의 최대 거리는 Sabo 등의 방법에서는 100번의 시도 중 가장 큰 거리를 선택한 것이고, RL에서는 단일 실행에서 얻어진 결과임을 명심해야 합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Some examples of comparisons between a RL produced code and various codes produced by the method from Sabo et al. [46] with different base codes. On each code the highest distance over 100 tries was taken for the method by Ref. [46].
> </details>

{{< table-caption >}}
| [[2257,25,13]]_(6,3) | [[3457,25,15]]_(6,3) | [[4337,25,17]]_(6,3) | [[4153,25,16]]_(6,3) | [[4337,25,16]]_(6,3) | [[4525,25,17]]_(6,3) |{{< /table-caption >}}
> 🔼 표 4는 가중치(w)가 6이고 큐비트 차수(q)가 3일 때, 코드 거리(d)를 약간 감소시키는 것을 허용했을 때의 큐비트 오버헤드를 보여줍니다.  기존 코드의 거리(d)보다 1, 2, 3만큼 작은 거리를 갖는 코드들을 생성했을 때의 오버헤드를 보여줍니다.  이 표의 데이터는 그림 8에도 나타나 있습니다.  즉, 이 표는 주어진 가중치와 큐비트 차수 제약 조건 하에서 코드 거리와 큐비트 오버헤드 간의 절충 관계를 보여주는 실험 결과를 요약한 것입니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Qubit overheads when allowing small reductions in distance at w=6𝑤6w=6italic_w = 6, q=3𝑞3q=3italic_q = 3. Data is also shown in Fig. 8
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