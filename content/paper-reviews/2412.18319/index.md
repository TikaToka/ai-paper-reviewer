---
title: "Mulberry: Empowering MLLM with o1-like Reasoning and Reflection via Collective Monte Carlo Tree Search"
summary: "Mulberry는 집단 몬테 카를로 트리 탐색(CoMCTS)을 이용, 단계적 추론 및 반성 능력을 갖춘 다중 모드 대규모 언어 모델(MLLM)을 개발한 연구입니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Vision-Language Models", "🏢 Tsinghua University",]
showSummary: true
date: 2024-12-24
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.18319 {{< /keyword >}}
{{< keyword icon="writer" >}} Huanjin Yao et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-26 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.18319" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.18319" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/mulberry-empowering-mllm-with-o1-like" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존 다중 모드 대규모 언어 모델(MLLM)은 복잡한 추론 과제 해결에 어려움을 겪고 있으며, 단순히 최종 답변만 생성하는 경향이 있습니다.  **단계별 추론 과정을 생성하여 이해도를 높이고, 효율적인 추론 경로를 찾는 것이 중요**한 과제로 떠오르고 있습니다.

본 연구는 이러한 문제를 해결하기 위해 **집단 학습 기반의 몬테 카를로 트리 탐색(CoMCTS)**이라는 새로운 추론 방법을 제시합니다.  CoMCTS는 여러 모델의 지식을 활용하여 추론 경로를 공동으로 예측하고, 탐색하며, 효율적인 경로를 찾아내는 것을 목표로 합니다.  **본 연구는 CoMCTS 기반의 새로운 다중 모드 데이터셋 Mulberry-260k와 이를 이용하여 훈련된 Mulberry 모델을 제시**하며, 다양한 벤치마크에서 기존 MLLM보다 우수한 성능을 보임을 실험적으로 증명합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 집단 몬테 카를로 트리 탐색(CoMCTS)을 통해 효율적이고 효과적인 추론 경로 탐색 및 학습 가능 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 새로운 다중 모드 데이터셋 Mulberry-260k 공개 및 단계적 추론 및 반성 기능을 갖춘 Mulberry 모델 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 다양한 벤치마크에서 기존 MLLM 대비 우수한 성능 입증 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **다중 모드 대규모 언어 모델(MLLM)**의 추론 능력 향상에 중점을 두고 있어, **단계별 추론 및 반성 능력을 갖춘 MLLM 개발**이라는 중요한 연구 분야에 기여합니다.  **집단 학습 기반의 몬테 카를로 트리 탐색(CoMCTS) 기법** 제시는 기존의 한계를 극복하고 효율적인 추론 경로를 찾는 새로운 방식을 제시하며, **다양한 벤치마크에서 우수한 성능**을 입증하여 향후 연구의 새로운 방향을 제시합니다.  **새로운 데이터셋 Mulberry-260k** 제공 또한 향후 관련 연구에 귀중한 자료가 될 것입니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.18319/x1.png)

> 🔼 그림 1은 두 개의 하위 그림으로 구성되어 있습니다. (a)는 제안된 CoMCTS 방법이 다른 트리 탐색 방법들에 비해 탐색 효율성과 효과 면에서 우수함을 보여줍니다.  (b)는 CoMCTS로 탐색된 데이터로 학습된 Mulberry 모델이 대부분의 오픈소스 MLLM을 능가하고, 클로즈드소스 모델에 대해서도 경쟁력 있는 결과를 달성하여 단계별 추론 및 반추 능력이 뛰어남을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  (a) Our CoMCTS shows great superiority in search effectiveness and efficiency against other tree search methods. (b) Our Mulberry, trained on CoMCTS-searched data, outperforms most open-sourced MLLMs and achieves competitive results against closed-source ones, showing outstanding abilities in step-by-step reasoning and reflection.
> </details>





{{< table-caption >}}
| Method | MathVista | MMStar | MMMU | ChartQA | DynaMath | HallBench | MM-Math | MME<sub>sum</sub> | AVG | 
|---|---|---|---|---|---|---|---|---|---| 
| *Closed-Source Model* |  |  |  |  |  |  |  |  |  | 
| GPT-4o [2024] | 63.8 | 63.9 | 69.1 | 85.7 | 63.7 | 55.0 | 31.8 | 2329 | 64.5 | 
| Claude-3.5 Sonnet [2024] | 67.7 | 62.2 | 68.3 | 90.8 | 64.8 | 55.0 | - | 1920 | - | 
| *Open-Source Model* |  |  |  |  |  |  |  |  |  | 
| DeepSeek-VL-7B [2024a] | 36.1 | 37.1 | 35.4 | 59.1 | 21.5 | - | - | - | - | 
| Cambrain-1-8B [2024] | 49.0 | - | 42.7 | 73.3 | - | - | - | - | - | 
| MM-1.5-7B [2024b] | 47.6 | - | 41.8 | 78.6 | - | - | - | 1861 | - | 
| Idefics3-LLaMA3-8B [2024] | 58.4 | 55.9 | 46.6 | 74.8 | - | - | - | 1937 | - | 
| InternVL2-8B [2024] | 58.3 | **61.5** | 51.8 | 83.3 | 39.7 | - | - | 2210 | - | 
| MiniCPM-Llama-V-2.5-8B [2024c] | 54.3 | 51.8 | 45.8 | - | - | 42.4 | - | 2025 | - | 
| MiniCPM-V-2.6-8B [2024c] | 60.6 | 57.5 | 49.8 | - | - | 48.1 | - | 2348 | - | 
| DeepSeek-VL2-MOE-4.5B [2024] | 62.8 | 61.3 | 51.1 | 86.0 | - | - | - | 2253 | - | 
| *Reasoning Model* |  |  |  |  |  |  |  |  |  | 
| LLaVA-CoT-11B [2024] | 54.8 | 57.6 | - | - | - | 47.8 | - | - | - | 
| LLaVA-Reasoner-8B [2024d] | 50.6 | 54.0 | 40.0 | 83.0 | - | - | - | - | - | 
| Insight-V-8B [2024] | 49.8 | 57.4 | 42.0 | 77.4 | - | - | - | 2069 | - | 
| LLaVA-NeXT-8B [2024] | 37.5 | 42.1 | 41.7 | 69.5 | 22.7 | 33.4 | 0.6 | 1957 | 39.7 | 
| Mulberry-LLaVA-8B | 56.3 | 54.5 | 43.0 | 79.5 | 34.1 | 47.5 | 18.9 | 2021 | 50.7<sup>**11**↑</sup> | 
| Llama-3.2-11B-V-Ins. [2024] | 48.6 | 49.8 | 41.7 | 83.4 | 34.3 | 40.3 | 4.1 | 1787 | 45.8 | 
| Mulberry-Llama-11B | 61.1 | 58.5 | 45.6 | 83.5 | 37.2 | 48.9 | 18.7 | 2035 | 53.3<sup>**7.5**↑</sup> | 
| Qwen2-VL-2B [2024b] | 43.0 | 48.0 | 41.1 | 73.5 | 24.9 | 41.7 | 1.0 | 1872 | 42.5 | 
| Qwen2-VL-7B [2024b] | 58.2 | 60.7 | 54.1 | 83.0 | 42.1 | 50.6 | 5.9 | 2327 | 54.7 | 
| Mulberry-7B | **63.1** | 61.3 | **55.0** | **83.9** | **45.1** | **54.1** | **23.7** | **2396** | **58.9**<sup>**4.2**↑</sup> | {{< /table-caption >}}

> 🔼 표 1은 Mulberry-260K 데이터셋과 Mulberry 모델의 효과를 검증하기 위해 수행된 광범위한 실험 결과를 보여줍니다.  총 8개의 다양한 벤치마크 데이터셋(일반적인 이해 능력, 수리 추론, 환각, 시각적 착시, 다학제적 이해 및 추론 등)을 사용하여  4개의 강력한 기준 모델을 기반으로 Mulberry 모델의 성능을 평가하고, 최첨단의 일반적 및 추론 기반 MLLM과 비교 분석했습니다. 이 표는 Mulberry 모델의 우수성과  CoMCTS 방법론의 효과를 보여주는 주요 결과들을 담고 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Main Results. To examine the effectiveness of the searched data (i.e., Mulberry-260K) and the trained models (i.e., Mulberry), we conduct extensive experiments with four powerful baseline models, and comprehensively benchmark our Mulberry with various state-of-the-arts, including general and reasoning-based MLLMs.
> </details>





### In-depth insights


#### CoMCTS: Core Idea
CoMCTS의 핵심 아이디어는 **다수의 MLLM(다중 모드 대규모 언어 모델)로부터 집단 지식을 활용하여 효과적이고 효율적인 추론 경로를 탐색하고 학습하는 것**입니다. 기존의 MCTS 방식과 달리, CoMCTS는 단일 MLLM의 추론 공간에 국한되지 않고 여러 MLLM의 추론 경로를 통합하여 다양하고 상호 보완적인 후보 추론 노드를 확장합니다. 이는 각 반복에서 여러 MLLM의 집단 지식을 활용하여 추론 경로를 효과적으로 찾고, 각 반복마다 여러 중간 단계를 건너뛰고 다음 시작 노드로 가장 최근의 정확한 단계를 선택함으로써 검색 시간을 단축하는 데 도움이 됩니다. 또한, CoMCTS는 **긍정적 및 부정적 추론 노드를 모두 활용하여 반추적 추론 경로를 검색하고 학습**함으로써 모델이 장기간 추론 과정에서 부정확한 추론 경로로부터 적절하게 수정할 수 있도록 합니다. 이를 통해 단계별 추론 및 반추 능력을 갖춘 MLLM을 효과적으로 훈련할 수 있습니다.  **집단 학습은 다양한 MLLM에서 얻은 상호 보완적인 정보를 통합**하여 단일 MLLM에서는 달성할 수 없는 수준의 성능을 얻을 수 있게 합니다.

#### Mulberry Dataset
본 논문에서 제시된 Mulberry 데이터셋은 **다중 모드(multimodal)** 학습-추론-반성(learning-to-reason-and-reflect) 데이터셋으로, **질문에 대한 풍부하고 명확하며 잘 정의된 추론 노드 트리(tree of rich, explicit and well-defined reasoning nodes)**를 제공합니다.  이는 기존의 단순한 답변 생성 방식에서 벗어나, **단계별 추론 과정(step-by-step reasoning)**을 학습하는 MLLM(다중 모드 대규모 언어 모델)을 위한 중요한 자원입니다.  **CoMCTS(Collective Monte Carlo Tree Search)** 알고리즘을 통해 생성된 Mulberry 데이터셋은 단순히 정답만을 제공하는 것이 아니라, **정답에 이르는 다양한 추론 경로(reasoning paths)** 및 **잘못된 추론 경로를 포함한 반성적 경로(reflective reasoning paths)**를 포함하여, 모델의 **오류 수정 및 반성 능력 향상(error correction and reflection)**에 도움을 줍니다.  **다양한 모드의 입력(multimodal inputs)**을 지원하며, 수학, 과학, 일반적인 상식 등 다양한 분야의 질문을 포함합니다.  **대규모의 데이터 크기(260k)**는 MLLM의 훈련에 충분한 양의 데이터를 제공하며, **효율적인 추론 경로 탐색(efficient reasoning-path searching)**을 위한 토대가 됩니다.  결과적으로 Mulberry 데이터셋은 MLLM의 **추론 능력(reasoning ability)**과 **반성 능력(reflection ability)**을 향상시키는 데 크게 기여할 것으로 예상됩니다.

#### Collective SFT
집단적 SFT는 여러 개의 다양한 MLLM을 활용하여 **집합적으로 지식을 활용**하고 **효율적인 추론 경로를 학습**하는 새로운 방법론입니다.  기존의 단일 모델 학습 방식과 달리, 여러 모델의 강점을 결합하여 **더욱 정확하고 효율적인 추론**을 가능하게 합니다.  이를 통해 각 모델의 한계를 극복하고, **복잡한 문제 해결 능력 향상**에 기여할 것으로 기대됩니다. **다양한 모델의 상호작용 및 협력 학습**을 통해 얻어지는 시너지 효과는, 단일 모델 학습보다 훨씬 우수한 성능을 보여줄 것으로 예상됩니다.  **데이터 효율성 측면**에서도, 집단 학습은 제한된 데이터로도 효과적인 학습을 가능하게 하여 **데이터 활용의 효율성을 높입니다.**  결론적으로, 집단적 SFT는 MLLM의 추론 능력을 향상시키고 데이터 효율성을 높이는 혁신적인 방법으로, 앞으로 **더욱 발전된 MLLM 개발**에 중요한 역할을 할 것으로 기대됩니다.

#### Ablation Studies
본 논문의 "절제 연구" 부분은 제안된 방법의 각 구성 요소가 전체 성능에 미치는 영향을 정량적으로 평가하는 데 중점을 둡니다.  **개별 모듈의 기여도를 측정하기 위해**  일련의 실험을 설계하여, 각 모듈을 제거하거나 변경했을 때의 성능 변화를 분석합니다. 이를 통해, **각 모듈의 중요성을 확인하고, 시스템의 강점과 약점을 파악**할 수 있습니다. 예를 들어, 특정 모듈을 제거했을 때 성능이 크게 저하된다면, 해당 모듈이 시스템의 핵심 구성 요소임을 시사합니다. 반대로, 성능 변화가 미미하다면, 해당 모듈의 중요성이 낮거나 다른 모듈에 의해 보완될 수 있음을 나타냅니다.  **절제 연구 결과는 제안된 방법의 신뢰성을 높이고, 향후 연구 방향을 제시**하는 데 중요한 역할을 합니다.  **각 모듈의 상호 작용 및 전체 시스템 성능에 대한 통찰력을 제공**하여, 시스템 개선 및 최적화에 대한 방향을 제시합니다.  또한, **다양한 변수에 따른 성능 변화를 분석하여, 시스템의 견고성과 일반화 능력을 평가**할 수 있습니다.  이는 실제 응용 환경에서의 성능을 예측하고, 시스템의 한계를 파악하는 데 도움이 됩니다.

#### Future Work
본 논문의 "향후 연구" 부분에 대한 심도있는 고찰을 통해, **집단 학습 기반의 MCTS (CoMCTS)의 확장성 및 일반화 능력 개선**에 대한 방향을 제시할 수 있습니다.  다양한 모달리티 데이터와 복잡한 추론 과제를 다루기 위한 CoMCTS의 적응성을 높이는 연구가 필요하며, **더욱 효율적인 탐색 알고리즘 개발** 및 **다양한 MLLM 아키텍처에 대한 적용성 연구**를 통해 Mulberry 모델의 성능 향상을 도모할 수 있습니다. 특히, **반추적 추론 경로 탐색의 효과적인 학습 방법론 개선**은 모델의 성능 향상과 더불어,  실제 문제 해결 능력 강화에 큰 영향을 미칠 것으로 예상됩니다. 또한, Mulberry-260k 데이터셋의 확장 및 다양한 분야의 데이터 통합을 통해 **더욱 강건하고 일반화된 MLLM 모델 개발**이 가능할 것입니다. 마지막으로, **CoMCTS의 이론적 토대 마련 및 성능 분석**을 위한 심층적인 연구를 통해, CoMCTS 기반의 추론 방법론의  신뢰성과 효율성을 더욱 높일 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.18319/x2.png)

> 🔼 그림 2는 CoMCTS 알고리즘이 Mulberry 모델을 훈련시키는 과정을 보여줍니다.  위쪽 부분은 CoMCTS가 반복적으로 추론 경로를 탐색하는 과정을 나타냅니다. 각 반복에서 CoMCTS는 여러 개의 MLLM(다중 모드 대규모 언어 모델)로부터 집단 지식을 활용하여 (a) 시작 노드로부터 다양하고 상호 보완적인 후속 추론 노드 후보를 확장하고, (b) 추론 결과를 시뮬레이션하고 오류 후보 노드를 식별하여 자식 노드와 함께 제거하고, (c) 점수와 방문 횟수를 아래에서 위로 업데이트하고, (d) UCB(Upper Confidence Bound) 값이 가장 높은 리프 노드를 다음 시작 노드로 선택합니다. 아래쪽 부분은 CoMCTS가 생성한 추론 트리로부터 모델을 학습시키는 과정을 보여줍니다.  즉, CoMCTS는 추론 경로를 탐색하고, 그 결과를 사용하여 Mulberry 모델을 훈련시키는 두 가지 단계를 번갈아 수행합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2:  Overview. Our CoMCTS trains Mulberry with two alternating phases. In top part, CoMCTS searches reasoning paths iteratively, and in each iteration, it utilizes collective knowledge from multiple MLLMs to jointly (a) expand diverse and complementary candidate subsequent reasoning nodes till the end from a given start node, (b) simulate reasoning outcomes, position error candidate nodes and prune them along with their child nodes, (c) backpropagate to update the score and visit count of each reasoning node in a bottom-up manner, and (d) select the leaf reasoning node with the highest UCB value as next start node. In bottom part, we train the model to learn from the reasoning trees constructed by CoMCTS.
> </details>



![](https://arxiv.org/html/2412.18319/x3.png)

> 🔼 CoMCTS 알고리즘을 사용하여 생성된 추론 트리의 정성적 예시입니다. 그림은 각 질문에 대해 풍부하고 명확하며 잘 정의된 추론 노드 트리를 보여줍니다. 각 레벨은 추론 과정의 단계를 나타내며,  다양한 모델에서 생성된 추론 노드를 색상으로 구분하여 보여줍니다.  이를 통해 CoMCTS가 복잡한 문제에 대한 단계별 추론 과정을 효과적으로 생성하고, 중간 단계의 추론 과정을 명확하게 제시함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Qualitative illustration of reasoning tree searched by CoMCTS with rich, explicit, well-defined reasoning nodes.
> </details>



![](https://arxiv.org/html/2412.18319/x4.png)

> 🔼 그림 4는 Mulberry-260K 데이터셋에서 추론 단계의 분포를 보여줍니다. Mulberry-260K는 다양한 모드의 질문들에 대한 풍부하고 명확하며 잘 정의된 추론 노드 트리를 제공하는, 다중 모드 학습-추론-반추 데이터셋입니다. 이 그림은 추론 단계의 빈도를 보여주는 히스토그램 세 개를 포함하고 있는데, 각각 전체 Mulberry-260K 데이터셋, 기하학 관련 하위 데이터셋, 그리고 차트 관련 하위 데이터셋을 나타냅니다. 이를 통해 단순한 추론 작업은 상대적으로 적은 추론 단계를, 복잡한 추론 작업은 더 많은 추론 단계를 필요로 한다는 것을 알 수 있습니다.  이러한 결과는 CoMCTS가 다양한 복잡성의 문제에 대해 유연하게 추론 단계 수를 조절할 수 있는 능력을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4:  Distribution of reasoning steps in Mulberry-260K data.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Direct Pred | CoMCTS | CoMCTS | CoMCTS | CoMCTS | S.S.R. |
|---|---|---|---|---|---|---|
| GPT-4o | GPT-4o | Qwen2-VL-7B | LLama3.2-11B | Qwen2-VL-72B | 58.2 |
|  | ✔ |  |  |  | 63.8 |
|  | ✔ | ✔ |  |  | 66.2 |
|  | ✔ | ✔ | ✔ |  | 69.7 |
|  | ✔ | ✔ | ✔ | ✔ | 80.2 |{{< /table-caption >}}
> 🔼 본 표는 CoMCTS의 집단 학습에 참여하는 각 모델이 전체 트리 탐색 성능(탐색 성공률, S.S.R.)에 어떻게 기여하는지에 대한 분석 결과를 보여줍니다.  각 모델의 기여도를 개별적으로 평가하여 CoMCTS의 성능 향상에 대한 통찰력을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 2:  Ablation Study on CoMCTS. We study how each model in CoMCTS collective learning contribute to overall tree search performance in Search Success Rate (S.S.R.).
> </details>

{{< table-caption >}}
| Benchmark | w/o Reflection Data | w/ Reflection Data |
|---|---|---|
| MathVista | 50.9 | 51.7 |{{< /table-caption >}}
> 🔼 본 표는 Mulberry 모델의 성능에 대한 실험 결과를 보여줍니다. Mulberry 모델은 CoMCTS(Collective Monte Carlo Tree Search)를 사용하여 생성된 효과적인 추론 데이터와 반추적인 추론 데이터로 학습되었습니다. 이 표는 각각의 데이터 유형이 Mulberry 모델의 성능에 미치는 영향을 분석하여, 효과적인 추론 데이터와 반추적인 추론 데이터가 Mulberry 모델의 성능 향상에 어떻게 기여하는지를 보여줍니다.  즉, 효과적인 추론 데이터만 사용했을 때와 효과적인 추론 데이터와 반추적인 추론 데이터를 함께 사용했을 때의 성능 차이를 비교 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 3:  Ablation Study on Mulberry. As Mulberry is trained with effective and reflective reasoning data searched by CoMCTS, we study their respective contributions.
> </details>

{{< table-caption >}}
| Methods | Search Success Rate ↑ | Average Search Iteration ↓ |
|---|---|---|
| GPT4o (direct) | 58.2 | - |
| MCTS | 63.8 | 42.1 |
| ReST-MCTS | 65.6 | 36.3 |
| Omega-MCTS | 66.2 | 24.3 |
| CoMCTS | 80.2 | 12.7 |{{< /table-caption >}}
> 🔼 표 4는 다양한 트리 탐색 방법들과 제안된 CoMCTS 방법의 성능을 비교 분석한 결과를 보여줍니다.  'GPT-4o (direct)'는 트리 탐색을 사용하지 않은 기준 모델을 나타냅니다.  표에는 각 방법의 검색 성공률(Search Success Rate)과 평균 검색 반복 횟수(Average Search Iteration)가 제시되어 있으며,  CoMCTS가 검색 효율성과 효과 면에서 다른 방법들에 비해 월등히 우수함을 보여줍니다.  검색 성공률은 높고 평균 검색 반복 횟수는 낮을수록 좋은 성능을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Comparison with other tree search methods. “GPT-4o (direct)” refers to the baseline without tree search. Our CoMCTS shows great superiority in search effectiveness and efficiency.
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
{{< /gallery >}}