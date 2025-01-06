---
title: "PoliFormer: Scaling On-Policy RL with Transformers Results in Masterful Navigators"
summary: "POLIFORMER: 대규모 트랜스포머 기반 강화학습으로 실제 환경에서도 탁월한 내비게이션 성능을 달성!"
categories: ["AI Generated", ]
tags: ["AI Applications", "Robotics", "🏢 Allen Institute for AI",]
showSummary: true
date: 2024-06-28
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2406.20083 {{< /keyword >}}
{{< keyword icon="writer" >}} Kuo-Hao Zeng et el. {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2406.20083" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2406.20083" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/poliformer-scaling-on-policy-rl-with" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 로봇 내비게이션 연구는 **제한된 환경이나 단순한 작업에 국한**되어 있었고, **복잡한 환경이나 다양한 목표를 가진 작업에는 성능이 저하**되는 문제가 있었습니다.  특히, **심층 신경망 기반의 정책 모델을 효율적으로 훈련**하는데 어려움이 많았습니다.

본 연구는 **대규모 시뮬레이션 환경에서 트랜스포머 기반의 강화학습 에이전트인 POLIFORMER를 개발**했습니다.  **다양한 환경에서 수억 건의 상호 작용을 통해 학습**시켰고, **병렬 컴퓨팅을 활용하여 효율적인 훈련을 가능**하게 했습니다. 그 결과, **다양한 로봇 플랫폼과 내비게이션 벤치마크에서 최첨단 성능을 달성**했습니다.  특히, **실제 환경에서도 추가적인 적응 없이 우수한 성능**을 보였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 대규모 시뮬레이션 데이터를 사용한 트랜스포머 기반 강화학습을 통해 실제 로봇 내비게이션에서 최첨단 성능을 달성함 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 다양한 로봇 플랫폼(LoCoBot, Stretch RE-1)과 벤치마크에서 우수한 성능을 검증함 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 제안된 방법론을 통해 객체 추적, 다중 객체 내비게이션 등 다양한 하위 작업으로 쉽게 확장 가능함 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
이 논문은 **대규모 시뮬레이션 기반 강화 학습을 통해 실제 환경에서도 일반화되는 로봇 내비게이션 에이전트를 개발**한 연구입니다.  **트랜스포머 기반 정책 모델과 병렬 학습 기법을 활용하여 기존의 한계를 극복**하고, 여러 로봇 플랫폼과 벤치마크에서 최첨단 성능을 달성했습니다.  이는 **로봇 내비게이션 분야의 발전과 다양한 응용 분야 확장**에 큰 영향을 미칠 것으로 예상됩니다.  또한 **대규모 트랜스포머 모델 훈련을 위한 효율적인 방법론을 제시**하여, 관련 분야 연구에도 중요한 시사점을 제공합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2406.20083/x1.png)

> 🔼 그림 1은 시뮬레이션에서 대규모 강화 학습(RL)을 사용하여 훈련된 트랜스포머 기반 정책인 PoliFormer를 보여줍니다. PoliFormer는 두 가지 임베디먼트(로봇)에서 시뮬레이션(왼쪽 하단)과 실제 환경(오른쪽 하단) 모두에서 상당한 성능 향상을 달성합니다. 성공률(SR)을 나타냅니다.  PoliFormer는 여러 차원에서 온-폴리시 RL 훈련을 확장합니다. 왼쪽 상단에는 RL 훈련의 규모를 키우면 성능이 지속적으로 향상되는 것을 보여주고, 가운데 상단에는 처리량을 높이기 위해 수백 개의 병렬 롤아웃을 활용하는 것을 보여주며, 오른쪽 상단에는 수억 개의 모델 매개변수를 가진 트랜스포머 기반 정책을 개발하는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: PoliFormer, a transformer-based policy trained using RL at scale in simulation, achieves significant performance improvements in simulation (bottom-left) and the real world (bottom-right), across two embodiments. SR denotes Success Rate. We scale on-policy RL training across multiple dimensions: (top-left) we observe continual performance improvement with scaling RL training; (top-middle) we leverage hundreds of parallel rollouts for higher throughput; (top-right) we develop a transformer-based policy scaling model parameters to hundreds of millions.
> </details>





{{< table-caption >}}
| Inputs | Model | Loss | Chores<span class="ltx_text ltx_font_upright">-<math alttext="\mathbb{S}" class="ltx_Math" display="inline" id="S4.T1.st1.1.1.1.1.1.1.m1.1"><semantics id="S4.T1.st1.1.1.1.1.1.1.m1.1a"><mi id="S4.T1.st1.1.1.1.1.1.1.m1.1.1" xref="S4.T1.st1.1.1.1.1.1.1.m1.1.1.cmml">𝕊</mi><annotation-xml encoding="MathML-Content" id="S4.T1.st1.1.1.1.1.1.1.m1.1b"><ci id="S4.T1.st1.1.1.1.1.1.1.m1.1.1.cmml" xref="S4.T1.st1.1.1.1.1.1.1.m1.1.1">𝕊</ci></annotation-xml><annotation encoding="application/x-tex" id="S4.T1.st1.1.1.1.1.1.1.m1.1c">\mathbb{S}</annotation><annotation encoding="application/x-llamapun" id="S4.T1.st1.1.1.1.1.1.1.m1.1d">blackboard_S</annotation></semantics></math> ObjectNav</span> | 
|---|---|---|---| 
| Success (SEL) |  |  |  | 
| RGB+text | SPOC [6] | IL | 57.0 (46.2) | 
|  | SPOC* | IL | 60.0 (30.5) | 
|  | EmbSigLIP [6] | RL | 36.5 (24.5) | 
|  | PoliFormer | RL | **85.5**(**61.2**) | 
| RGB | SPOC | IL | 85.0 (61.4) | 
| +text+b-box | PoliFormer | RL | **95.5**(**71.4**) | 
| RGB+b-box | PoliFormer | RL | 92.0 (73.9) |{{< /table-caption >}}

> 🔼 표 1(a)는 CHORES-S 벤치마크에서의 성공률(SEL)을 보여줍니다. 이 표는 다양한 모델과 학습 방법(모방 학습 또는 강화 학습)을 비교하여 정량적 성능을 보여줍니다.  Stretch RE-1 로봇을 사용한 실험 결과이며, POLIFORMER 모델이 기존 최고 성능(SoTA) 모델인 SPOC을 상당히 능가함을 보여줍니다.  다양한 입력(RGB+text, RGB)과 목표 지정 방법(텍스트, 바운딩 박스)에 따른 성능 차이도 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (a) Stretch RE-1 on Chores-𝕊𝕊\mathbb{S}blackboard_S
> </details>





### In-depth insights


#### Transformer Policy
본 논문에서 제시된 트랜스포머 기반 정책(Transformer Policy)은 **에이전트가 환경과 상호작용하며 시행착오를 통해 학습하는 강화학습(Reinforcement Learning)**에 기반합니다.  기존의 순환 신경망(RNN) 기반 방식과 달리, 트랜스포머의 장기 의존성(Long-term Dependency)을 활용하여 에이전트는 장기간의 기억과 추론 능력을 갖추게 됩니다.  특히 **인코더-디코더 구조**를 사용하여 시각 정보를 처리하고, 미래의 행동을 예측하는 데 효율성을 보입니다.  **주의 메커니즘(Attention Mechanism)**을 통해 에이전트는 중요한 정보에 집중하고, 비효율적인 탐색을 줄일 수 있습니다.  **KV-캐시(KV-Cache)**를 사용하여 계산 비용을 줄이고, 병렬 처리를 통해 학습 효율을 높인 점 또한 주목할 만합니다.  **대규모 시뮬레이션 환경**에서 학습된 이 정책은 실제 환경에서도 우수한 성능을 보이며, **실제 로봇에 대한 적응력**을 높였습니다.  결론적으로, 이 트랜스포머 정책은 강화학습 기반 로봇 내비게이션에서 **성능과 효율성을 크게 향상**시키는 핵심 요소임을 보여줍니다.

#### On-Policy RL Scaling
본 논문은 **온-폴리시 강화학습(RL)**의 확장성에 중점을 두고 있습니다. 온-폴리시 RL은 에이전트가 학습하는 동안 정책을 계속 업데이트하기 때문에 데이터 효율성이 떨어지는 단점이 있습니다. 그러나 이러한 단점에도 불구하고 **정책의 안정성**과 **탐험 능력**이라는 장점을 가지고 있습니다. 논문에서는 대규모 병렬 계산을 통해 수백만 번의 상호작용을 수행하여 이러한 단점을 극복하고 온-폴리시 RL의 효율성을 높이는 방법을 제시합니다. 또한, **트랜스포머 기반 정책 모델**을 사용하여 장기 메모리 및 추론 기능을 향상시켜 복잡한 탐색 문제에 대한 성능을 개선합니다. 이를 통해 온-폴리시 RL의 한계를 극복하고 실제 환경에서도 높은 성능을 달성할 수 있음을 보여줍니다. **특히, 다양한 로봇 플랫폼과 벤치마크에서 최첨단 성능**을 달성하여 온-폴리시 RL의 실용성을 강조합니다.  이는 **대규모 데이터셋과 고성능 모델을 활용한 온-폴리시 RL의 잠재력**을 보여주는 중요한 결과입니다.

#### Sim-to-Real Transfer
본 논문은 시뮬레이션 환경에서 훈련된 에이전트가 실제 환경에서도 성공적으로 작동하는지에 대한 심도있는 sim-to-real 전이 연구를 제시합니다. **핵심은 시뮬레이션 환경의 다양성과 현실성을 높이는 것**이며, 이를 위해 다양한 환경과 객체를 생성하는 방법론을 사용하고, 대규모의 병렬 학습을 통해 에이전트의 일반화 능력을 향상시키는 데 중점을 둡니다.  **실제 로봇 플랫폼에서의 실험 결과는 시뮬레이션 환경에서 훈련된 모델이 실제 환경에 적응력이 뛰어남을 보여줍니다.** 이는 **모델의 일반화 능력이 뛰어나다는 것을 의미**하며,  **심층 강화학습과 트랜스포머 기반 아키텍처의 효과적인 조합을 통해 sim-to-real 전이 문제를 효과적으로 해결**할 수 있음을 시사합니다. 하지만, **실제 환경의 복잡성과 예측 불가능성은 여전히 sim-to-real 전이 성공에 중요한 과제**로 남아있으며,  추가적인 연구를 통해 이러한 문제점들을 해결해야 실용적인 수준의 sim-to-real 전이 기술을 확보할 수 있을 것입니다.  **향후 연구 방향으로는 실제 환경과 시뮬레이션 환경 간의 불일치를 최소화하기 위한 더욱 정교한 시뮬레이션 환경 구축 및  강화학습 알고리즘의 개선** 등이 제시됩니다.

#### Benchmark Results
논문의 벤치마크 결과는 정량적 성과를 제시하며, **POLIFORMER의 우수성**을 보여줍니다. 다양한 벤치마크 환경에서 **최첨단 성능**을 달성했음을 보여주는 수치들이 제시될 것으로 예상됩니다. 이는 단순한 수치 제시를 넘어,  **실제 로봇 플랫폼에서의 실험 결과**를 포함하여, 시뮬레이션 환경과 실제 세계 간의 **일관된 성능**을 강조할 것입니다.  특히, **다양한 로봇 플랫폼** (예: LoCoBot, Stretch RE-1)에서의 실험은 일반화 능력을 평가하는 중요한 지표가 될 것입니다.  또한,  **다양한 난이도의 탐색 과제**에 대한 결과를 통해  POLIFORMER의 **강건성**을 확인할 수 있을 것입니다.  **기존 방법과의 비교 분석**을 통해 POLIFORMER의 개선점 및 우위를 명확히 제시하고, **정량적 지표**를 통해 그 효과를 뒷받침할 것으로 예상됩니다.  결과 해석은 **통계적 유의성**을 고려하여 신뢰도를 높일 것이며,  **한계점**과 **향후 연구 방향**에 대한 논의를 포함하여 균형 잡힌 분석을 제공할 것입니다.

#### Future Directions
본 논문의 핵심 아이디어는 **트랜스포머 기반 정책을 사용한 대규모 온-폴리시 강화학습**을 통해 실제 환경에서의 적응 없이도 실제 세계로 일반화되는 실내 내비게이션 에이전트를 훈련하는 것입니다.  미래 방향에 대해 생각해보면, **더욱 복잡한 작업(예: 조작)**으로 확장하기 위해서는 새로운 보상 모델을 설계해야 합니다. 또한, **심층 감지기(예: 심도 센서)**를 통합하여 모델의 성능과 일반화 능력을 향상시킬 수 있습니다.  **더욱 효율적인 훈련 방법** 또한 중요한데,  병렬 처리 기술과 더 큰 배치 크기를 활용하는 것이 핵심이 될 것입니다. **다양한 환경에서의 훈련 데이터 확장**을 통해 견고성을 더욱 높이는 것도 중요한 과제입니다. 마지막으로, **일반 목적 내비게이션 모델을 구축**하여 다운스트림 작업에 제로샷으로 활용할 수 있도록 하는 방향으로 연구가 진행될 수 있을 것입니다. 이를 통해, **실제 세계 문제 해결에 보다 쉽게 적용될 수 있는 강화학습 기반 로봇 제어 기술 개발**을 위한 중요한 발걸음을 내딛을 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2406.20083/x2.png)

> 🔼 그림 2는 PoliFormer의 아키텍처를 보여줍니다.  각 시간 단계 t에서, PoliFormer는 에고중심 RGB 관측값 i<sup>t</sup>을 받아들여 비전 트랜스포머 모델을 사용하여 시각적 표현 r<sup>t</sup>을 추출합니다. 그런 다음 시각적 표현과 목표 특징 g (그리고 선택적으로 감지된 바운딩 박스 목표 특징 g<sub>b</sub><sup>t</sup>)를 사용하여 상태 특징 s<sup>t</sup>를 추가로 인코딩합니다.  인과적 트랜스포머 디코더를 사용하여 시간에 따른 상태 신념 b<sup>t</sup>를 모델링하고, 마지막으로 선형 액터와 비평가 헤드를 통해 액션 로짓 a<sup>t</sup>와 값 추정 e<sup>t</sup>를 예측합니다.  롤아웃 수집 및 추론을 위해, 메모리 사용량을 줄이고 훈련 및 추론 속도를 높이기 위해 기존의 KV-캐시 [10]를 시간 캐시 전략으로 활용합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: PoliFormer is a fully transformer-based policy model. At each timestep t𝑡titalic_t, it takes an ego-centric RGB observation itsuperscript𝑖𝑡i^{t}italic_i start_POSTSUPERSCRIPT italic_t end_POSTSUPERSCRIPT, extracts visual representations rtsuperscript𝑟𝑡r^{t}italic_r start_POSTSUPERSCRIPT italic_t end_POSTSUPERSCRIPT using a vision transformer model, further encodes state features stsuperscript𝑠𝑡s^{t}italic_s start_POSTSUPERSCRIPT italic_t end_POSTSUPERSCRIPT using the visual representations and goal features g𝑔gitalic_g (and optional detected bounding box goal features gbtsuperscriptsubscript𝑔𝑏𝑡g_{b}^{t}italic_g start_POSTSUBSCRIPT italic_b end_POSTSUBSCRIPT start_POSTSUPERSCRIPT italic_t end_POSTSUPERSCRIPT), models state belief btsuperscript𝑏𝑡b^{t}italic_b start_POSTSUPERSCRIPT italic_t end_POSTSUPERSCRIPT over time, employing a causal transformer decoder, and, finally, predicts action logits atsuperscript𝑎𝑡a^{t}italic_a start_POSTSUPERSCRIPT italic_t end_POSTSUPERSCRIPT and a value estimation etsuperscript𝑒𝑡e^{t}italic_e start_POSTSUPERSCRIPT italic_t end_POSTSUPERSCRIPT via linear actor and critic heads, respectively. For rollout collection and inference, we leverage the KV-cache [10] as our temporal cache strategy to prevent recomputing the forward pass for all prior timesteps at each new timestep, saving memory and speeding up both training and inference.
> </details>



![](https://arxiv.org/html/2406.20083/x3.png)

> 🔼 이 그림은 PoliFormer-BoxNav 모델이 제로샷 방식으로 다양한 작업을 수행하는 모습을 보여줍니다. 특히, 특정 제목의 책 찾기, 부엌으로 이동하기, 여러 개의 물체를 순차적으로 찾아가기, 그리고 사무실 건물 주변을 따라 장난감 자동차를 따라가기 등의 작업을 수행하는 능력을 시각적으로 보여줍니다.  각 작업은 이미지와 함께 설명되어 있어, 모델의 이해력과 상황 적응력을 잘 보여줍니다.  이는 사전 훈련 없이도 다양한 명령을 이해하고 복잡한 탐색 작업을 수행할 수 있음을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: We use PoliFormer-BoxNav zero-shot to find a book with a particular title, navigate to a kitchen, navigate to multiple objects sequentially, and follow a toy car around an office building.
> </details>



![](https://arxiv.org/html/2406.20083/x4.png)

> 🔼 그림 4는 블록 하삼각형 구조를 사용한 학습을 위한 어텐션 마스크를 보여줍니다. 각 행은 하나의 에피소드를, 각 열은 시간 단계를 나타냅니다. 어텐션 마스크는 이전 시간 단계의 정보만 사용하여 각 시간 단계에서의 어텐션을 제한함으로써, 모델이 과거의 경험에만 의존하도록 합니다. 이는 장기적인 의존성을 유지하면서도 계산 비용을 줄이는 데 도움이 됩니다.  각 에피소드의 시작과 끝은 1로 표시됩니다.  0은 해당 시간 단계에서 어텐션이 불가능함을 의미합니다. 마스크의 하삼각형 형태는 모델이 과거 정보만 참조하도록 보장합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Attention Masks for training with block lower triangular structure.
> </details>



![](https://arxiv.org/html/2406.20083/x5.png)

> 🔼 그림 5는 다양한 시간적 캐시 전략과 이들이 학습 속도에 미치는 영향을 보여줍니다.  본 연구에서는 (i) No-Cache, (ii) Feature-Cache, (iii) State-Cache, 그리고 (iv) KV-Cache 등 네 가지 캐시 전략을 비교 분석했습니다. 그림 상단에는 네 가지 캐시 전략이, 하단에는 LoCoBot과 Stretch RE-1 에이전트 모두에 대한 각 전략별 학습 속도(초당 학습 단계, SPS)가 나타나 있습니다. No-Cache의 경우, 최악의 성능을 보이며, KV-Cache가 가장 효율적인 학습 속도를 제공하는 것을 확인할 수 있습니다.  이를 통해, KV-Cache가 장기간의 시퀀스를 효과적으로 처리하여 학습 시간을 단축시키는데 효과적임을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Different temporal cache strategies and their impact on the training speed. We ablate four different cache strategies, including (i) No-Cache, (ii) Feature-Cache, (iii) State-Cache, and (iv) KV-Cache, shown at top. The bottom chart shows the training Step per Second (SPS) achieved by different strategies, on both LoCoBot and Stretch RE-1 agents.
> </details>



![](https://arxiv.org/html/2406.20083/x6.png)

> 🔼 그림 6은 실제 환경에서 진행된 실험에 사용된 (a) LoCoBot과 (b) Stretch RE-1 로봇의 시작 위치를 보여줍니다. 화살표 방향은 로봇이 바라보는 방향을 나타냅니다.  각 로봇의 세 가지 시작 위치가 제시되어 있으며, 각 위치에서 로봇은 여러 가지 목표물 중 하나로 이동하는 과제를 수행합니다. 이 그림은 로봇의 시작 위치가 실험 결과에 어떤 영향을 미치는지 이해하는 데 도움을 줍니다. 실험의 객관성과 재현성을 확보하기 위해, 시작 위치는 사전에 정해지고 모든 시도에 대해 동일하게 유지되었습니다. 각 시작 위치는 다양한 실내 환경의 특징을 반영하여 선택되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Starting Poses of (a) LoCoBot and (b) Stretch RE-1 used in the real world experiments. The arrow direction indicates where the agent faces with.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Inputs | Model | ProcTHOR-10k | ArchitecTHOR | AI2-iTHOR |
|---|---|---|---|---|
| |  | Success (SPL) |  |  |
| RGB+text | ProcTHOR [11]³ | 67.7 (49.0) | 55.8 (38.3) | 70.0 (57.1) |
|  | SGC [63] | 70.8 (48.6) | 53.8 (34.8) | 71.4 (59.3) |
|  | EmbCodebook [86] | 73.7 (48.4) | 58.3 (35.6) | 78.4 (23.7) |
|  | PoliFormer | **82.4** (**58.5**) | **68.3** (**45.1**) | **85.3** (**72.7**) |
| RGB | PoliFormer | 90.4 (66.6) | 81.9 (55.6) | 94.9 (83.5) |
| RGB+text+b-box |  |  |  |  |
| RGB+b-box | PoliFormer | 87.4 (56.2) | 85.7 (47.6) | 92.1 (78.6) |{{< /table-caption >}}
> 🔼 이 표는 논문의 4.1절 'POLIFORMER는 네 개의 벤치마크에서 최첨단 성능을 달성합니다'에서 나온 결과를 보여줍니다.  특히 LoCoBot 로봇을 사용한 세 가지 시뮬레이션 환경(ProcTHOR-10k, ArchitecTHOR, AI2-iTHOR)에서의 객체 목표 탐색 성공률을 보여줍니다.  ProcTHOR-10k는 검증(validation) 세트, ArchitecTHOR와 AI2-iTHOR는 테스트(test) 세트 결과입니다.  여러 모델의 성능을 비교하여 POLIFORMER 모델의 우수성을 강조합니다.
> <details>
> <summary>read the caption</summary>
> (b) LoCoBot on ProcTHOR-10k (val), ArchitecTHOR and AI2-iTHOR (test)
> </details>

{{< table-caption >}}
| Model | ProcTHOR-10k (val) | ArchitecTHOR |
|---|---|---| 
| Vision Backbone | Encoder | Decoder | Success |
| CLIP (ResNet50) | 1x CNN | 1x GRU | 67.7 | 55.8 |
| DINOv2 (ViTs) | 1x CNN | 1x GRU | 73.1 | 60.8 |
| DINOv2 (ViTs) | 3x Tx | 3x GRU | 73.6 | 59.8 |
| DINOv2 (ViTs) | 3x Tx | 1x Tx | 77.2 | 59.1 |
| DINOv2 (ViTs) | 3x Tx | 3x Tx | 80.4 | 63.9 |
| DINOv2 (ViTb) | 3x Tx | 3x Tx | **82.4** | **68.3** |{{< /table-caption >}}
> 🔼 표 1은 PoliFormer가 네 개의 ObjectNav 벤치마크에서 최첨단 성능을 달성했음을 보여줍니다. (a)는 Stretch RE-1 구현체를 사용하는 Chores-S ObjectNav 벤치마크의 결과로, PoliFormer는 이전 최첨단(IL 기반 SPOC)을 압도적으로 능가합니다. (b)는 세 가지 LoCoBot 구현체 테스트 세트에 대한 결과로, PoliFormer는 기존의 모든 연구 결과(모두 RL을 사용하여 학습)를 능가합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Across four ObjectNav benchmarks, PoliFormer obtains SoTA performance. (a) Results on the Chores-𝕊𝕊\mathbb{S}blackboard_S ObjectNav benchmark, which uses the Stretch RE-1 embodiment, PoliFormer dramatically outperforms the previous SoTA, IL-trained SPOC. (b) On three LoCoBot-embodiment test suites, PoliFormer outperforms all prior work (all trained using RL).
> </details>

{{< table-caption >}}
| Model | Stretch RE-1 | LoCoBot |
|---|---|---|
| ProcTHOR [11] | - | 26.7 |
| Phone2Proc [17] | - | 66.7 |
| SPOC [6] | 50.0 | - |
| PoliFormer (ours) | **83.3** | **80.0** |
| SPOC+Detic [6] | 83.3 | - |
| PoliFormer +Detic (ours) | **88.9** | - |{{< /table-caption >}}
> 🔼 이 표는 모델 용량을 확장하기 위한 설계 선택에 대한 ablation 연구 결과를 보여줍니다.  다양한 비전 백본, 인코더, 디코더 아키텍처를 사용한 POLIFORMER의 성능을 비교하여, 각 구성 요소가 전체 모델 성능에 미치는 영향을 분석합니다.  이를 통해 모델의 성능 향상에 기여한 주요 요소를 파악하고,  향후 모델 개선 방향을 제시합니다.
> <details>
> <summary>read the caption</summary>
> (a) Ablations on design choices for scaling model capacity
> </details>

{{< table-caption >}}
| Parameter | Value |
|---|---| 
| Allowed Steps | 600 (Stretch RE-1), 500 (LoCoBot) |
| Total Rollouts | 192 (Stretch RE-1), 384 (LoCoBot) |
| Learing Rate | 0.002 |
| Mini Batch per Update | 1 |
| Update Repeats | 4 |
| Max Gradient Norm | 0.5 |
| Discount Value Factor  γ | 0.99 |
| GAE λ | 0.95 |
| PPO Surrogate Objective Clipping | 0.1 |
| Value Loss Weight | 0.5 |
| Entropy Loss Weight | 0.01 |
| Training Stages | 3 |
| Steps for PPO Update  Stage 1 | 32 |
| Steps for PPO Update  Stage 2 | 64 |
| Steps for PPO Update  Stage 3 | 128 |
| Transformer State Encoder Layers | 3 |
| Transformer State Encoder Hidden Dims | 512 |
| Transformer State Encoder Heads | 8 |
| Causal Transformer Deocder Layers | 3 |
| Causal Transformer Deocder Hidden Dims | 512 |
| Causal Transformer Deocder Heads | 8 |{{< /table-caption >}}
> 🔼 이 표는 실제 환경에서 POLIFORMER의 성능을 보여줍니다.  두 가지 로봇 플랫폼(Stretch RE-1과 LoCoBot)을 사용하여 실제 환경에서 여러 탐색 작업을 수행한 결과를 보여줍니다.  각 로봇과 작업에 대한 성공률을 보여주어, 시뮬레이션 환경에서만 훈련된 POLIFORMER가 실제 환경에서 얼마나 잘 일반화되는지 보여줍니다.  Phone2Proc과 같은 기존 방법과 비교하여 POLIFORMER의 성능 우위를 강조합니다.
> <details>
> <summary>read the caption</summary>
> (b) Real-world results - Success
> </details>

{{< table-caption >}}
| Inputs | Model | Loss | EasyObjectNav
Success (SEL) | RegularObjectNav
Success (SEL) | HardObjectNav
Success (SEL) |
|---|---|---|---|---|---| 
| RGB+text | SPOC [6] | IL | 62.9 (40.5) | 48.2 (38.9) | 34.1 (27.4) |
|  | SPOC* | IL | 69.7 (43.3) | 53.5 (34.3) | 31.0 (19.6) |
|  | PoliFormer | RL | **89.0** (**62.1**) | **82.6** (**71.8**) | **72.3** (**62.8**) |
| RGB | SPOC | IL | 90.3 (67.7) | 78.7 (62.6) | 70.6 (52.5) |
| +text+b-box | PoliFormer | RL | **98.1** (**86.5**) | **90.4** (**79.6**) | **86.0** (**75.0**) |
| RGB+b-box | PoliFormer | RL | 97.1 (83.2) | 91.9 (79.8) | 87.6 (75.0) |{{< /table-caption >}}
> 🔼 표 2는 모델의 용량을 확장하기 위한 설계 선택에 대한 ablation 연구와 두 가지 다른 임베디먼트에 대한 실제 환경 결과를 보여줍니다. (a)는 모델 용량 조정을 위한 설계 선택에 대한 ablation 연구 결과를, (b)는 두 가지 다른 로봇 플랫폼에서 얻은 실제 환경 결과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 2: We present (a) ablation studies on design choices for scaling up model capacity; and (b) the real-world results, on two different embodiements.
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