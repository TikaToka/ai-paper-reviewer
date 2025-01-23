---
title: "Reasoning Language Models: A Blueprint"
summary: "고급 추론 기능을 갖춘 추론 언어 모델(RLM) 구축을 위한 포괄적인 청사진을 제시하는 연구."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 ETH Zurich",]
showSummary: true
date: 2025-01-20
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.11223 {{< /keyword >}}
{{< keyword icon="writer" >}} Maciej Besta et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-22 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.11223" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.11223" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/reasoning-language-models-a-blueprint" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

현재의 대형 언어 모델(LLM)은 복잡한 추론 작업을 수행하는 데 어려움을 겪고 있으며, 이러한 한계를 극복하기 위해 **추론 메커니즘을 통합한 고급 추론 언어 모델(RLM)**이 등장하였습니다. 하지만, 기존 RLM은 높은 비용, 독점적인 특성, 복잡한 구조로 인해 접근성과 확장성에 어려움이 있습니다.

본 연구는 이러한 문제를 해결하기 위해 **RLM 구성 요소를 모듈식 프레임워크로 체계화**하여, 다양한 추론 구조, 전략, 강화 학습 개념, 감독 체계 등을 포괄적으로 제시합니다. 또한, RLM 프로토타이핑과 실험을 위한 **모듈식 구현체인 x1**을 소개하고, 효율적인 확장 및 현대적인 클라우드 배포에 대한 논의를 제공합니다.  이를 통해 **RLM 개발 및 실험의 진입 장벽을 낮추고, 혁신을 촉진**하는 데 기여합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} RLM 구성 요소를 모듈식 프레임워크로 구성하는 포괄적인 청사진 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 다양한 추론 구조, 전략, 강화 학습 개념, 감독 체계 등을 통합한 RLM 청사진 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} RLM 프로토타이핑 및 실험을 위한 모듈식 구현 x1 소개 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
이 논문은 **추론 언어 모델(RLM)**의 설계 및 구현을 간소화하는 청사진을 제공하여, **고급 추론 기능에 대한 접근성을 민주화**하고 연구 및 실무자 모두에게 혁신을 촉진합니다. 이는 **RLM 개발 및 실험의 진입 장벽을 낮추어** AI 연구의 발전에 크게 기여할 것입니다. 또한, **확장 가능한 클라우드 배포**에 대한 논의를 통해 실제 세계 적용에 대한 중요한 통찰력을 제공합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.11223/x2.png)

> 🔼 그림 2는 Reasoning Language Model (RLM)의 역사를 보여줍니다. RLM은 크게 세 가지 흐름에서 발전해 왔습니다. 첫째, AlphaZero [128]와 같은 강화학습 기반 모델입니다. 둘째, GPT-4 [109]와 같은 LLM 및 Transformer 기반 모델입니다. 셋째, 슈퍼컴퓨터 및 고성능 시스템의 컴퓨팅 성능과 데이터 처리 능력의 꾸준한 발전입니다. 이 세 가지 흐름이 합쳐져 현재의 정교한 RLM이 탄생하게 되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: The history of RLMs. This class of models has been the result of the development of three lines of works: (1) Reinforcement Learning based models such as AlphaZero [128], (2) LLM and Transformer based models such as GPT-4o [109], and (3) the continuous growth of compute power and data processing capabilities of supercomputers and high performance systems.
> </details>





{{< table-caption >}}
## Reasoning Language Models: A Blueprint

| Scheme | Structure | Step | Strategy | Gen. | Ref. | Agg. | Pr. | Res. | Sel. | BT | Bp. | Inter. | Final. | PM | VM | Inf. | Tr. | DG | Remarks |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| **Explicit RLMs (Section 5.1)** |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| rStar-Math [52] | E Tree | C Thought + Code Block | E MCTS | ✅ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |  |
| PRIME [163, 38] | E Multiple Chains | F Token<br>C Thought | E Best-of-N | ✅ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |  |
| Marco-o1 [174] | E Tree | F Token Sequence<br>C Thought | E MCTS | ✅ | ✅ | ❌ | ❌ | ❌ | ✅ | ❌ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |  |
| Journey Learning (Tr.) [113] | E Tree | E Thought | E Tree Search | ✅ | ✅ | ❌ | ✅ | ✅ | ❌ | ✅ | ❌ | ✅ | ✅ | ✅ | ✅ | ½* | ✅ | ✅ | *Separate Entry |
| OpenR [145] | E Tree | C Thought | E Best-of-N<br>E Beam Search<br>E MCTS | ✅ | ❌ | ❌ | ✅ | ❌ | ✅ | ❌ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |  |
| LLaMA-Berry [169] | E Tree of Chains | C Solution | E MCTS | ✅ | ✅ | ❌ | ❌ | ❌ | ✅ | ❌ | ✅ | ❌ | ✅ | ✅ | ✅ | ✅ | ✅ |  |
| ReST-MCTS* [170] | E Tree | C Thought | E MCTS | ✅ | ½* | ❌ | ❌ | ❌ | ✅ | ❌ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | *Advice by critic |
| AlphaMath Almost Zero [23] | E Tree | F Thought | E MCTS | ✅ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ✅ | ✅ | ✅ | ✅ | ½* | ½* | ✅ | ✅ | *Single model |
| MCTS-DPO [155] | E Tree | F Token Sequence | E MCTS | ✅ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ✅ | ✅ | ✅ | ✅ | ½* | ½* | ✅ | ✅ | *Single model |
| AlphaLLM [141] | E Tree | C Option | E MCTS | ✅ | ❌ | ❌ | ✅ | ❌ | ✅ | ❌ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |  |
| TS-LLM [45] | E Tree | F Token<br>F Sentence | E MCTS<br>E Tree Search | ✅ | ❌ | ❌ | ✅ | ❌ | ✅ | ❌ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ | ✅ |  |
| **Implicit RLMs (Section 5.2)** |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| QwQ [140] | I Chain* | F Token | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ½ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | *Linearized Tree |
| Journey Learning (Inf.) [113] | I Chain* | C Thought | I DFS | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ½ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | *Linearized Tree |
| **Structured Prompting Schemes (Section 5.3)** |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| Graph of Thoughts (GoT) [9] | E Graph* | C Thought | E Controller | ✅ | ✅ | ✅ | ❌ | ❌ | ❌ | ✅ | ✅ | ❌ | ✅ | ✅ | ❌ | ½ | ✅ | ❌ | *DAG |
| Tree of Thoughts (ToT) [161] | E Tree | C Thought | E Tree Search | ✅ | ❌ | ❌ | ✅ | ❌ | ✅ | ✅ | ❌ | ✅ | ✅ | ❌ | ½ | ✅ | ❌ | ❌ |  |
| Self-Consistency (SC) [150] | E Multiple Chains | C Thought | E Majority Voting | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ |  |
| Chain of Thought (CoT) [152] | I Chain | C Thought | ❌ | ✅ | ✅ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ❌ | ✅ | ❌ | ❌ | {{< /table-caption >}}

> 🔼 표는 논문의 4장과 그림 5절에서 제시된 분류 체계에 따라 다양한 추론 언어 모델(RLM)을 비교 분석한 결과를 보여줍니다.  '추론' 열에서는 각 RLM의 추론 구조(체인, 트리, 그래프 등)와 전략(MCTS, 빔 서치 등)을 구체적으로 설명합니다. '추론 연산자' 열에서는 주어진 RLM이 추론 구조에 대한 연산(생성, 개선, 집계, 제거, 재구성, 탐색, 백트래킹, 업데이트 등)을 지원하는지 여부와 구체적인 기능들을 나타냅니다. '모델' 열에서는 연산자 구현에 사용된 모델(정책 모델, 가치 모델)의 종류를 보여주고, '파이프라인' 열에서는 각 RLM에서 사용되는 파이프라인(추론, 학습, 데이터 생성)을 제시합니다.  약어 'E'는 명시적, 'I'는 암시적, 'F'는 세분화된, 'C'는 조악한을 의미하며, 배터리 아이콘은 각 기능 지원 정도를 나타냅니다.  (꽉 찬 배터리: 완전 지원, 반쯤 찬 배터리: 부분 지원, X: 지원 안 함)
> <details>
> <summary>read the caption</summary>
> TABLE I: Comparison of RLMs with respect to the provided taxonomy (Section 4 and Figure 5). “Reasoning”: Details of the reasoning approach, specifically what is its Structure and its Strategy? “Reasoning Operator”: Does a given scheme support operators on the reasoning structure? If yes, which classes (and specific functionalities) are supported Structure (“Gen.”: generate, “Ref.”: refine, “Agg.”: aggregate, “Pr.”: prune, “Res.”: restructure), Traversal (“Sel”: select, “BT”: backtrack), Update (“Bp.”: backpropagate), and Evaluation of “Inter.”: intermediate steps and “Final.”: final steps? “Model“: Does a given scheme use models to implement its operators and if so, which ones (“PM”: policy model, “VM”: value model)? “Pipeline”: Which pipelines are harnessed by a given scheme (“Inf.”: inference, Tr.”: training, “DG”: data generation)? When describing representations, we use the following abbreviations: “E”: explicit, “I”: implicit. “F”: fine-grained. “C”: coarse-grained. “\faBatteryFull”: full support (i.e., YES), “\faBatteryHalf”: partially [supported], “\faTimes”: no support (i.e., NO).
> </details>





### In-depth insights


#### RLM Blueprint
본 논문에서 제시된 "RLM Blueprint"는 **추론 언어 모델(RLM)**을 설계하고 구축하기 위한 포괄적인 프레임워크입니다. 이 청사진은 다양한 추론 구조(연결, 트리, 그래프, 중첩 형태)와 전략(몬테카를로 트리 탐색, 빔 탐색 등), 강화 학습 개념(정책, 가치 모델 등), 감독 체계(결과 기반 및 프로세스 기반 감독) 및 관련 개념(테스트 시간 계산, 검색 증강 생성 등)을 통합합니다.  **모듈식 아키텍처**를 통해 RLM의 다양한 구성 요소를 체계적으로 구성하여 유연성과 확장성을 제공합니다.  기존의 RLM 설계(LLaMA-Berry, QwQ 등)를 특수한 경우로 제시하여 **청사진의 다양성과 통합 잠재력**을 보여줍니다.  **x1 프레임워크**를 통해 RLM 프로토타입 제작 및 실험을 간소화하여 접근성을 높였습니다.  특히, 정책 및 가치 모델을 위한 다단계 훈련, 친숙한 훈련 분포의 중요성 등의 주요 통찰력을 제공하고, 확장 가능한 클라우드 배포와 광범위한 LLM 생태계와의 통합 방안을 제시합니다.  **결론적으로, 이 청사진은 RLM 구축 과정을 명확히 하고, 고급 추론 기능의 민주화를 통해 혁신을 촉진하여 '풍요로운 AI'와 '빈곤한 AI'의 격차를 해소하는 것을 목표**로 합니다.

#### Modular RLMs
모듈형 RLMs는 **각 구성 요소(추론 체계, 연산자, 모델)를 독립적으로 개발 및 유지보수**할 수 있도록 설계되어 유연성과 확장성을 높입니다. 이를 통해 연구자들은 다양한 추론 구조, 전략, 훈련 패러다임을 쉽게 통합하고 실험하여 특정 작업에 맞는 RLMs를 만들 수 있습니다.  **모듈화는 재사용성을 증가시켜** 개발 시간과 비용을 절감하고, **오류를 쉽게 파악 및 수정**할 수 있도록 지원합니다.  **각 모듈의 독립성**은 병렬 처리 및 분산 처리를 통해 확장성을 향상시키는 데 중요한 역할을 합니다.  **클라우드 기반 배포** 및 다양한 플랫폼 간 이식성 또한 향상시킵니다. 하지만 모듈 간의 상호작용과 통합을 효율적으로 관리하는 것이 **중요한 과제**이며, 과도한 모듈화는 오히려 복잡성을 증가시킬 수 있습니다. 따라서 적절한 수준의 모듈화를 유지하고 모듈 간의 인터페이스를 명확하게 정의하는 것이 중요합니다.  **모듈형 설계는 궁극적으로 RLM 개발의 민주화**에 기여하여 연구와 혁신을 가속화하고, 첨단 추론 기능을 더 많은 연구자와 실무자들에게 제공할 수 있게 합니다.

#### x1 Framework
논문에서 제시된 x1 프레임워크는 **RLM(Reasoning Language Model) 설계 및 실험을 간소화**하기 위해 고안된 모듈식 구현체입니다. 이는 다양한 추론 구조, 전략, 강화 학습 개념, 감독 방식 등을 통합하여 사용자의 특정 응용 프로그램에 맞춤화된 RLM을 개발할 수 있도록 유연성을 제공합니다.  **모듈식 설계**를 통해 구성 요소들을 쉽게 교체 및 조합할 수 있으며, **신속한 RLM 프로토타이핑**과 **실험**을 가능하게 합니다.  **다양한 최신 RLM 기법들을 특별한 경우로서 포함**하여 프레임워크의 다재다능함과 통합력을 입증하며, 클라우드 환경에서의 **확장성 있는 배포**를 위한 전략도 논의하고 있습니다.  **x1은 RLM 개발의 진입 장벽을 낮추고, 혁신을 촉진하며,  "풍부한 AI"와 "빈곤한 AI" 간의 격차를 해소**하는데 기여할 것으로 기대됩니다.

#### Training Insights
본 논문의 "Training Insights" 부분은 **두 가지 주요 훈련 전략**인 **지도 학습 미세 조정(SFT)**과 **강화 학습(RL)**을 효과적으로 결합하는 방법을 제시합니다.  **SFT는 모델이 기본적인 추론 패턴을 먼저 학습**하도록 하여 안정적인 기반을 마련하고, **RL은 복잡하고 적응적인 환경에서 모델의 성능을 향상**시킵니다.  특히, **익숙한 데이터 분포로 훈련하는 것이 초기 성능과 향후 개선에 중요한 영향**을 미친다는 점을 강조하며, **모델이 익숙한 패턴을 효과적으로 내재화**할 수 있도록 합니다.  반면, **프롬프트만으로 LLM의 자기 비판 및 평가를 유도하는 것은 불안정**할 수 있으며, **구조화된 훈련 방식과 신중한 연산자 설계**를 통해 **모델의 자기 개선 능력을 향상**시켜야 함을 시사합니다. **다양한 훈련 데이터 범위**에 따른 모델 성능의 차이점도 분석하며, **과정 기반 감독(PBS)**의 우수성을 강조합니다.  **PBS는 전체 추론 구조를 평가**하여 모델의 추론 경로를 세밀하게 다듬어 **정확도를 향상**시키는 반면, **결과 기반 감독(OBS)**은 최종 결과에만 초점을 맞추어 **정확도가 낮아질** 수 있습니다.  **샘플 수의 중요성**도 언급하며, **모델의 성능 측정에는 충분한 데이터가 필요**함을 강조합니다.

#### Benchmarking
논문의 벤치마킹 부분은 **다양한 종류의 추론 문제에 대한 RLMs의 성능을 평가하는 데 중점**을 둡니다.  수학적 추론, 논리적 추론, 인과 관계 추론, 상식적 추론, 코딩 및 추론 유틸리티 등 여러 영역을 아우르는 광범위한 벤치마킹 작업이 이루어졌습니다.  **GSM8K, MATH, AIME, AMC와 같은 기존 벤치마크와 더불어, 새로운 벤치마크**도 제시되어 RLMs의 일반화 능력 및 특정 도메인에 대한 전문성을 평가합니다.  **표본 크기의 중요성이 강조**되어, 신뢰할 수 있는 결과를 얻기 위해서는 충분한 데이터가 필요함을 시사합니다.  벤치마킹 과정에서 **모델의 출력 분산을 고려**하여, 공정하고 믿을 수 있는 성능 비교를 위한 방안을 제시합니다.  **벤치마킹 결과는 다양한 추론 접근 방식의 효과를 분석하는 데 활용**되며, 더 나은 RLM 설계를 위한 귀중한 통찰력을 제공합니다. 특히, **두 단계로 나누어 진행되는 훈련 전략의 효용성이 강조**됩니다.  **익숙한 데이터 분포에서의 훈련 중요성** 및 **프롬프트를 통한 LLMs의 자기 비판적 평가의 어려움**에 대한 논의도 포함되어, 더욱 효과적인 RLM 개발을 위한 중요한 지침을 제시합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.11223/x3.png)

> 🔼 그림 3은 언어 모델의 계층 구조와 추론 언어 모델(RLM)의 세 가지 기둥을 보여줍니다. 오른쪽에는 일반적인 언어 모델(LM)에서 대규모 언어 모델(LLM)로, 그리고 LLM에서 추론 언어 모델(RLM)로 이어지는 계층 구조가 표시되어 있습니다. RLM은 LLM과 강화 학습(RL), 고성능 컴퓨팅(HPC)이라는 세 가지 기둥 위에 구축됩니다. 각 기둥은 RLM의 특정 기능에 기여하는 고유한 강점과 한계가 있습니다. 그림의 왼쪽에는 이러한 세 가지 기둥이 자세히 설명되어 있으며, 각 기둥의 강점과 약점이 언급되어 있습니다. RLM은 이 세 가지 요소를 결합하여 뛰어난 추론 능력을 제공합니다. 명시적 RLM과 암시적 RLM이라는 두 가지 주요 RLM 유형이 제시되어 있습니다. 명시적 RLM은 추론 구조와 전략을 명시적으로 표현하는 반면, 암시적 RLM은 그러한 구조와 전략이 모델 가중치에 암시적으로 내장되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Hierarchy of language models (right) and the three pillars of RLMs (left).
> </details>



![](https://arxiv.org/html/2501.11223/x4.png)

> 🔼 이 그림은 추론 언어 모델(Reasoning Language Model, RLM)의 일반적인 설계와 핵심 개념을 보여줍니다. 그림의 왼쪽 상단에는 고차원 개요가, 오른쪽 상단에는 중간 수준의 개요가 제시되어 있습니다. 그림의 하단에는 추론 및 훈련 파이프라인을 자세히 보여주는 다이어그램이 있습니다. 추론 파이프라인에 대한 자세한 내용은 부록 C.1과 알고리즘 1에서, 다양한 훈련 단계 및 패러다임에 대한 자세한 내용은 부록 C.2와 C.3 및 알고리즘 2~7에서 확인할 수 있습니다. 데이터 생성 파이프라인은 부록 D에 자세히 설명되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Overview of a general RLM design and core concepts. We provide a high-level overview (the top-left part), a more detailed medium-level overview (the top-right part), and a very detailed diagram showing the inference and training pipelines (the bottom part). A detailed specification of the inference pipeline can be found in Appendix C.1 and in Algorithm 1. Details on the pipelines for different training phases and paradigms can be found in Appendices C.2 and C.3 as well as in Algorithms 2–7. The data generation pipeline is detailed in Appendix D.
> </details>



![](https://arxiv.org/html/2501.11223/x26.png)

> 🔼 그림 5는 추론 언어 모델(RLM)을 위한 청사진을 보여줍니다. 이 청사진은 추론 계획(상단), 연산자(하단 왼쪽), 그리고 모델(하단 오른쪽)이라는 네 가지 주요 도구 상자로 구성됩니다. 중앙에는 추론 파이프라인(부록 C.1 및 알고리즘 1 참조), 학습 파이프라인(부록 C.2, C.3, 알고리즘 2-7 참조), 그리고 데이터 생성 파이프라인(부록 D 참조)이 자세히 설명되어 있습니다. 각 도구 상자는 RLM의 다양한 구성 요소를 나타내며, 사용자는 이러한 구성 요소를 조합하여 다양한 유형의 RLM을 만들 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: A blueprint for reasoning LMs. It consists of four main toolboxes: the reasoning scheme (the top part), operators (the bottom-left part), and models (the bottom-right part); pipelines are mentioned in the center and detailed in Appendix C.1 and in Algorithm 1 (the inference pipeline), Appendix C.2, Appendix C.3, and in Algorithms 2–7 (the training pipelines), and in Appendix D (the data generation pipeline).
> </details>



![](https://arxiv.org/html/2501.11223/x27.png)

> 🔼 그림 6은 x1 프레임워크의 개요와 2단계 학습 과정을 보여줍니다. 1단계에서는 모델을 초기화하고, 2단계에서는 충분한 수의 MCTS 트리를 생성하고 이 트리에서 파생된 데이터로 모델을 반복적으로 개선하는 과정을 통해 모델을 정제합니다. 이 그림은 x1 프레임워크의 주요 구성 요소(정책 모델, 가치 모델, MCTS 알고리즘)와 데이터 생성 및 학습 파이프라인을 시각적으로 보여주어, x1 프레임워크의 작동 방식과 2단계 학습 전략을 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: An overview of the x1 framework is presented, highlighting its two-phase training process. In phase 1, the models are initialized, while in phase 2, the models are iteratively refined by alternating between constructing a sufficient number of MCTS trees and training the models on data derived from these trees.
> </details>



![](https://arxiv.org/html/2501.11223/x28.png)

> 🔼 이 그림은 논문의 7.6절, '토큰 확률 분포 분석'에서 나온 예시입니다. 모델이 수학 문제를 풀이하는 과정에서 각 단계별로 모델의 토큰 예측에 대한 확신 수준을 보여줍니다.  보라색은 확률이 0.8 미만으로, 낮은 확신 수준을 나타내고, 파란색은 두 번째로 높은 확률이 0.1을 초과하여 다른 토큰이 대안으로 고려될 수 있음을 의미하며, 빨간색은 두 가지 조건이 모두 충족되어 높은 불확실성을 나타냅니다. 이 그림은 모델이 불확실하거나 여러 가지 가능성을 고려하는 지점을 시각적으로 보여주어 추론 전략과 모델 설계를 개선하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> (a) 1st example
> </details>



![](https://arxiv.org/html/2501.11223/x29.png)

> 🔼 이 그림은 논문의 3.1절 'Reasoning Language Models의 본질'에서 RLMs의 추론 과정을 보여주는 그림의 두 번째 예시입니다.  구체적으로는, 숫자를 오름차순으로 정렬하는 문제에 대한 추론 과정을 보여줍니다.  사용자가 문제를 제시하면(Input task), RLM은 단계별로 추론을 수행하는데, 이는 텍스트로 표현된 추론 단계들(Reasoning steps)로 구성됩니다. 각 단계는  다음 단계로 이어지며(이는 트리 구조로 시각적으로 표현됨), 최종적으로 정렬된 숫자 목록을 출력합니다(Output). 이 예시는, RLMs이 복잡한 문제를 단계별 추론을 통해 해결하는 방법을 보여주는 것을 목표로 합니다.
> <details>
> <summary>read the caption</summary>
> (b) 2nd example
> </details>



![](https://arxiv.org/html/2501.11223/x30.png)

> 🔼 그림 (c)는 모델의 출력 결과를 보여주는 세 번째 예시입니다. 이 예시는 수학 문제 풀이 과정에 대한 모델의 추론 과정을 보여주며, 각 추론 단계에서 모델이 얼마나 확신을 가지고 있는지를 보여줍니다. 모델의 예측 확률 분포를 시각적으로 나타내어, 모델이 특정 토큰을 얼마나 확신하는지 또는 몇몇 토큰에 대해서 확신이 부족한지를 보여줍니다. 이는 모델이 추론 과정에서 불확실성을 어떻게 다루는지를 이해하는 데 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> (c) 3rd example
> </details>



![](https://arxiv.org/html/2501.11223/x31.png)

> 🔼 이 그림은 논문의 7.6절 '토큰 확률 분포 분석'에서 나온 예시 중 하나입니다.  이 그림은 모델이 문제를 푸는 과정에서 각 토큰을 생성할 확률을 시각적으로 보여줍니다.  구체적으로, 모델이 문제의 각 단계에서 어떤 토큰을 선택할지에 대한 확신도를 보여주는 확률 분포를 나타냅니다.  각 토큰의 확률이 높을수록 모델이 해당 토큰이 정답에 가깝다고 판단했음을 의미하며, 낮을수록 불확실성이 높다는 것을 보여줍니다. 여러 개의 토큰이 비슷한 높은 확률을 가질 경우, 모델은 답을 찾는 과정에서 여러 가지 가능성을 고려하고 있음을 의미합니다. 이 그림은 이러한 모델의 불확실성을 이해하고, 추론 과정을 개선하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> (d) 4th example
> </details>



![](https://arxiv.org/html/2501.11223/x32.png)

> 🔼 그림 7은 모델의 토큰 예측에 대한 신뢰도 수준을 반영하여 색상으로 구분한 모델 출력의 네 가지 예시를 보여줍니다. 가장 높은 확률이 0.8 미만이면 보라색으로 강조 표시되어 유의미한 경쟁 없이 낮은 확실성을 나타내고, 두 번째로 높은 확률이 0.1을 초과하면 파란색으로 강조 표시되어 다른 토큰이 근접한 대안이 되는 경쟁 상황을 나타내며, 두 가지 조건이 모두 충족되면 빨간색으로 강조 표시되어 높은 불확실성을 나타냅니다. 이러한 예시는 추론 단계에서 예측 신뢰도와 경쟁 수준의 다양성을 보여주며, 타당한 연속성 간의 모호성이나 경쟁이 높은 추론 과정의 지점을 강조합니다. 이러한 시각적 분석은 모델이 확신이 부족하거나 대안 사이에서 갈등하는 추론 과정의 지점을 파악하고, 추론 전략과 모델 설계를 개선하는 데 유용하며, 모델 성능을 향상시키기 위해 추가적인 감독이나 컨텍스트가 필요한 중요 영역을 정확히 파악하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Four examples of model output with highlighted tokens indicating uncertainty levels. The outputs have been color-coded to reflect the confidence levels of the model’s token predictions. Tokens are highlighted in purple when the highest probability is below 0.8 (indicating lower certainty without significant contention), in blue when the second-highest probability exceeds 0.1 (indicating contention, where another token is a close alternative), and in red when both conditions are met (indicating high uncertainty). These examples illustrate varying levels of prediction confidence and contention in reasoning steps, emphasizing regions of high ambiguity or competition between plausible continuations. This type of visual analysis is useful for identifying points in the reasoning process where the model lacks confidence or is torn between alternatives, guiding refinements in reasoning strategies and model design. It also helps pinpoint critical areas where additional supervision or context may improve model performance.
> </details>



![](https://arxiv.org/html/2501.11223/x33.png)

> 🔼 이 그림은 논문의 7.6절, '예시 분석: 토큰 확률 분포' 섹션에 있는 그림입니다. 그림의 캡션은 수학 문제 풀이 과정을 보여주는 네 가지 모델 출력 예시를 제시합니다. 각 예시는 토큰의 불확실성 수준을 나타내는 색상으로 강조 표시된 토큰을 포함합니다. 자주색으로 강조된 토큰은 가장 높은 확률이 0.8 미만임을 나타내고, 파란색은 두 번째로 높은 확률이 0.1을 초과함을 나타내며, 빨간색은 두 가지 조건을 모두 충족함을 나타냅니다. 이 그림은 모델의 예측 신뢰도와 경쟁 토큰 간의 경쟁을 보여주는 다양한 수준을 보여줍니다. 불확실성이 높은 영역이나 경쟁 토큰 간의 경쟁이 치열한 영역을 파악하여 추론 전략과 모델 설계를 개선하는 데 유용합니다. 또한 모델 성능을 향상시키기 위해 추가적인 감독이나 컨텍스트가 필요한 중요 영역을 식별하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> (a) To evaluate ⌈20⌉2superscript202\lceil{\sqrt{20}}\rceil^{2}⌈ square-root start_ARG 20 end_ARG ⌉ start_POSTSUPERSCRIPT 2 end_POSTSUPERSCRIPT, we need to follow the order of operations (PEMDAS):1. Evaluate the square root of 20: 20≈4.472204.472\sqrt{20}\approx 4.472square-root start_ARG 20 end_ARG ≈ 4.472 2. Round up to the nearest integer using the ceiling function: ⌈4.472⌉=54.4725\lceil 4.472\rceil=5⌈ 4.472 ⌉ = 5 3. Square the result: 52=25superscript52255^{2}=255 start_POSTSUPERSCRIPT 2 end_POSTSUPERSCRIPT = 25Therefore, the final answer is 2525\boxed{25}25.
> </details>



![](https://arxiv.org/html/2501.11223/x34.png)

> 🔼 이 그림은 논문의 7.6절 (예시 분석: 토큰 확률 분포)에 나오는 그림으로, 모델 출력의 불확실성 수준을 보여줍니다.  그림 (b)는 20의 제곱근을 구하고 올림 함수를 적용하는 문제에 대한 모델의 추론 과정을 보여주는 네 가지 예시 중 하나입니다. 각 예시는 모델이 추론 단계에서 생성한 토큰에 대한 확률 분포를 나타냅니다.  토큰의 색상은 모델의 확신 수준을 나타내며, 보라색은 확률이 0.8 미만(낮은 확신), 파란색은 두 번째로 높은 확률이 0.1을 초과(다른 토큰과 경쟁), 빨간색은 두 조건 모두 충족(높은 불확실성)을 의미합니다. 이러한 시각적 분석은 모델이 확신이 부족하거나 대안적인 답변 사이에서 갈등하는 추론 단계를 파악하는 데 유용합니다.  이를 통해 추론 전략과 모델 설계를 개선하고, 모델 성능을 향상시킬 수 있는 중요 영역을 찾아낼 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (b) <thought>First, we need to find the square root of 20, so let’s use a calculator to get an approximate value of 20≈4.472204.472\sqrt{20}\approx 4.472square-root start_ARG 20 end_ARG ≈ 4.472.<thought><thought>Since we’re dealing with the ceiling function, we should consider the smallest integer greater than or equal to the square root of 20, which is the ceiling of 2020\sqrt{20}square-root start_ARG 20 end_ARG. </thought><thought>We can also consider the perfect squares that are closest to 20, such as 16 and 25, to estimate the value of 2020\sqrt{20}square-root start_ARG 20 end_ARG and then apply the ceiling function.</thought>
> </details>



![](https://arxiv.org/html/2501.11223/x35.png)

> 🔼 그림은 논문의 7.6절(토큰 확률 분포의 예시 분석)에 있는 그림으로, 모델 출력의 예시와 해당 출력에 대한 토큰 확률 분포를 보여줍니다. (c)는 세 개의 연속적인 <thought> 블록으로 구성된 캡션을 가지고 있습니다. 각 블록은 모델이 제시한 추론 단계를 나타내며, 각 단계의 토큰에 대한 확률 값이 시각적으로 표현되어 있습니다. 첫 번째 <thought> 블록은 20의 제곱근을 계산하고 올림하는 과정을 설명합니다. 두 번째 <thought> 블록은 전체 표현식 ⌈√20⌉² 의 계산 과정을 개괄적으로 설명하고, 마지막 <thought> 블록은 천장 함수의 정의를 사용하여 수식을 풀이하는 과정을 보여줍니다. 그림은 각 토큰의 확률을 시각적으로 표현하여 모델의 확신도를 나타내고, 각 추론 단계의 신뢰도를 분석하는 데 사용됩니다. 높은 확률은 모델이 해당 토큰에 대한 높은 확신도를 가지고 있음을, 반대로 낮은 확률은 불확실성을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> (c) <thought>First, we need to find the square root of 20, which is approximately 4.472, so we can round up to the nearest whole number using the ceiling function, which gives us 5.</thought><thought>We can evaluate the expression ⌈20⌉2superscript202\lceil{\sqrt{20}}\rceil^{2}⌈ square-root start_ARG 20 end_ARG ⌉ start_POSTSUPERSCRIPT 2 end_POSTSUPERSCRIPT by first finding the square root of 20, then rounding up to the nearest whole number, and finally squaring the result.</thought><thought>Since ⌈x⌉𝑥\lceil{x}\rceil⌈ italic_x ⌉ is the ceiling function, we can rewrite the expression as ⌈20⌉2=⌈4.472⌉2=52=25superscript202superscript4.4722superscript5225\lceil{\sqrt{20}}\rceil^{2}=\lceil{4.472}\rceil^{2}=5^{2}=25⌈ square-root start_ARG 20 end_ARG ⌉ start_POSTSUPERSCRIPT 2 end_POSTSUPERSCRIPT = ⌈ 4.472 ⌉ start_POSTSUPERSCRIPT 2 end_POSTSUPERSCRIPT = 5 start_POSTSUPERSCRIPT 2 end_POSTSUPERSCRIPT = 25.</thought>
> </details>



![](https://arxiv.org/html/2501.11223/x36.png)

> 🔼 이 그림은 논문의 7.6절 '예시 분석: 토큰 확률 분포' 섹션에 속하며, 수학 문제 풀이 과정에서 언어 모델의 추론 과정에 대한 불확실성을 보여줍니다. 그림에는 모델의 추론 단계에서 각 토큰의 예측 확률을 시각적으로 나타낸 세 가지 예시가 포함되어 있습니다. 각 예시는 토큰의 불확실성 수준을 색상으로 구분하여 표시합니다. 자주색은 확률이 낮음을(즉, 모델이 확신하지 못함을), 파란색은 다른 토큰과의 경쟁이 있음을, 빨간색은 높은 불확실성을 나타냅니다. 이는 모델이 추론 과정에서 어떤 부분에서 확신이 부족하거나 여러 가능성을 고려하는지를 보여주는 시각적 도구입니다.  특히, 모델이 어떤 토큰을 선택할지 확신하지 못하는 부분은 추론 전략을 개선하거나 모델 설계를 개선하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> (d) <thought>First, we need to calculate the square root of 20.</thought><thought>We can start by finding the square root of 20, which is approximately 4.472, and then round up to the nearest whole number using the ceiling function.</thought><thought>Another approach is to recognize that 20 is between the perfect squares 16 and 25, so we can use this information to estimate the ceiling of the square root of 20.</thought>
> </details>



![](https://arxiv.org/html/2501.11223/x37.png)

> 🔼 그림 8은 모델 출력값의 처음 64개 토큰의 확률 분포를 보여줍니다. 가장 높은 확률을 가진 두 개의 토큰과 나머지 토큰의 확률 합계를 나타냅니다. 이는 모델이 각 단계에서 어떤 토큰을 선택할지에 대한 확신도를 시각적으로 보여주는 것으로, 각 토큰에 대한 확률 분포를 분석하여 추론 과정의 불확실성을 파악하는 데 도움이 됩니다. 예를 들어, 높은 확률을 가진 토큰이 하나만 있는 경우, 모델은 추론에 확신이 있는 반면, 높은 확률을 가진 토큰이 여러 개인 경우, 모델은 여러 경로를 탐색해야 할 가능성이 있음을 의미합니다. 이러한 시각적 분석은 모델의 불확실성이 높은 영역이나 다른 가능한 경로를 탐색해야 하는 영역을 식별하고, 추론 전략과 모델 설계를 개선하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Probabilities of the first 64 tokens of example model outputs. We show the two highest probabilities as well as the sum of the other probabilities.
> </details>



![](https://arxiv.org/html/2501.11223/x38.png)

> 🔼 이 그림은 논문의 7.6절에 있는 예시 분석 중 하나로, 토큰 확률 분포를 사용하여 추론 전략을 안내하는 방법을 보여줍니다. 그림 (a)는 ⌈√20⌉²를 계산하는 문제에 대한 모델의 출력과 토큰 확률 분포를 나타냅니다. 모델이 20의 제곱근을 계산하고, 올림 함수를 사용하여 가장 가까운 정수로 반올림하고, 마지막으로 결과를 제곱하는 단계를 거쳐 25라는 최종 답을 얻는 과정을 보여줍니다. 각 단계의 토큰에 대한 확률 분포는 모델의 확신 수준을 시각적으로 나타내며, 추론 과정에서 모델이 어떤 부분에서 확신이 부족하거나 여러 대안을 고려하는지 파악하는 데 유용합니다. 이러한 확률 분포 분석을 통해 모델의 추론 전략을 개선하고, 더 나은 의사결정을 내리는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> (a) To evaluate ⌈20⌉2superscript202\lceil{\sqrt{20}}\rceil^{2}⌈ square-root start_ARG 20 end_ARG ⌉ start_POSTSUPERSCRIPT 2 end_POSTSUPERSCRIPT, we need to follow the order of operations (PEMDAS):1. Evaluate the square root of 20: 20≈4.472204.472\sqrt{20}\approx 4.472square-root start_ARG 20 end_ARG ≈ 4.472 2. Round up to the nearest integer using the ceiling function: ⌈4.472⌉=54.4725\lceil 4.472\rceil=5⌈ 4.472 ⌉ = 5 3. Square the result: 52=25superscript52255^{2}=255 start_POSTSUPERSCRIPT 2 end_POSTSUPERSCRIPT = 25Therefore, the final answer is 2525\boxed{25}25.
> </details>



![](https://arxiv.org/html/2501.11223/x39.png)

> 🔼 이 그림은 논문의 7.6절, 'Example Analysis: Token Probability Distributions' 섹션에 속하며, 언어 모델의 추론 과정에서 토큰 확률 분포를 분석하는 예시를 보여줍니다. 그림의 캡션은 모델이 20의 제곱근을 구하고 올림 함수를 적용하는 과정을 설명하는 세 가지 다른 사고 과정을 보여주는 세 가지 다른 추론 단계를 보여줍니다. 각각의 추론 단계는 모델의 토큰 예측에 대한 확신 수준을 나타내는 색상으로 구분되어 있습니다. 자세히 살펴보면, 각 단계에서 모델이 어떤 토큰을 선택했는지, 그리고 그 확률은 얼마나 되는지에 대한 정보를 제공합니다. 이를 통해 모델의 추론 과정을 자세히 파악하고, 모델이 어떤 부분에서 확신이 부족한지 또는 어떤 부분에서 다른 가능성을 고려하는지를 이해할 수 있습니다. 이러한 분석은 모델의 추론 전략을 개선하고, 모델 설계를 개선하는 데 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> (b) <thought>First, we need to find the square root of 20, so let’s use a calculator to get an approximate value of 20≈4.472204.472\sqrt{20}\approx 4.472square-root start_ARG 20 end_ARG ≈ 4.472.<thought><thought>Since we’re dealing with the ceiling function, we should consider the smallest integer greater than or equal to the square root of 20, which is the ceiling of 2020\sqrt{20}square-root start_ARG 20 end_ARG. </thought><thought>We can also consider the perfect squares that are closest to 20, such as 16 and 25, to estimate the value of 2020\sqrt{20}square-root start_ARG 20 end_ARG and then apply the ceiling function.</thought>
> </details>



![](https://arxiv.org/html/2501.11223/x40.png)

> 🔼 이 그림은 논문의 7.6절 (예시 분석: 토큰 확률 분포)에 속하며, 언어 모델이 수학 문제를 푸는 과정에서 토큰의 확률 분포를 보여줍니다. 특히, ⌈√20⌉² 를 계산하는 세 가지 추론 단계를 보여주는 세 개의 <thought> 블록이 있습니다. 각 <thought> 블록은 모델의 추론 과정을 보여주는 텍스트와, 각 토큰의 확률을 나타내는 색상으로 표시된 토큰을 포함합니다. 낮은 확률의 토큰은 보라색, 두 번째로 높은 확률을 가진 토큰은 파란색, 그리고 두 조건을 모두 충족하는 토큰은 빨간색으로 강조 표시됩니다. 이는 모델의 추론 과정에서의 불확실성이나 다른 가능성 있는 선택지를 보여주는 시각적 분석 방법입니다.
> <details>
> <summary>read the caption</summary>
> (c) <thought>First, we need to find the square root of 20, which is approximately 4.472, so we can round up to the nearest whole number using the ceiling function, which gives us 5.</thought><thought>We can evaluate the expression ⌈20⌉2superscript202\lceil{\sqrt{20}}\rceil^{2}⌈ square-root start_ARG 20 end_ARG ⌉ start_POSTSUPERSCRIPT 2 end_POSTSUPERSCRIPT by first finding the square root of 20, then rounding up to the nearest whole number, and finally squaring the result.</thought><thought>Since ⌈x⌉𝑥\lceil{x}\rceil⌈ italic_x ⌉ is the ceiling function, we can rewrite the expression as ⌈20⌉2=⌈4.472⌉2=52=25superscript202superscript4.4722superscript5225\lceil{\sqrt{20}}\rceil^{2}=\lceil{4.472}\rceil^{2}=5^{2}=25⌈ square-root start_ARG 20 end_ARG ⌉ start_POSTSUPERSCRIPT 2 end_POSTSUPERSCRIPT = ⌈ 4.472 ⌉ start_POSTSUPERSCRIPT 2 end_POSTSUPERSCRIPT = 5 start_POSTSUPERSCRIPT 2 end_POSTSUPERSCRIPT = 25.</thought>
> </details>



![](https://arxiv.org/html/2501.11223/x41.png)

> 🔼 이 그림은 논문의 7.6절 (예시 분석: 토큰 확률 분포)에 속하며, 모델이 20의 제곱근의 올림 값을 계산하는 문제에 대한 네 가지 다른 추론 과정을 보여줍니다. 각각의 추론 과정은 모델의 토큰 예측에 대한 확신 수준을 나타내는 색상으로 구분된 하이라이트 토큰을 포함합니다. 보라색은 확신 수준이 낮음을, 파란색은 다른 토큰이 근접한 대안임을, 빨간색은 두 조건이 모두 충족됨을 나타냅니다. 이 그림은 모델의 추론 과정에서 불확실성이 높거나 대안적인 답이 존재하는 부분을 시각적으로 보여주고, 추론 전략과 모델 설계를 개선하는 데 도움이 됩니다.  또한 모델의 성능을 향상시키기 위해 추가적인 감독이나 맥락이 필요한 중요한 영역을 파악하는 데 유용합니다.
> <details>
> <summary>read the caption</summary>
> (d) <thought>First, we need to calculate the square root of 20.</thought><thought>We can start by finding the square root of 20, which is approximately 4.472, and then round up to the nearest whole number using the ceiling function.</thought><thought>Another approach is to recognize that 20 is between the perfect squares 16 and 25, so we can use this information to estimate the ceiling of the square root of 20.</thought>
> </details>



![](https://arxiv.org/html/2501.11223/x42.png)

> 🔼 그림 9는 모델의 출력 토큰 시퀀스의 처음 64개 토큰에 대해 분산, 엔트로피, VarEntropy 및 지니 계수와 같은 불확실성 척도를 플롯한 그래프입니다. 이는 모델이 토큰을 생성할 때의 불확실성 정도를 보여줍니다. 예를 들어, 분산이 낮으면 토큰 확률이 거의 균일하게 분포되어 있음을 나타내고, 높으면 몇몇 토큰에 확률이 집중되어 있음을 나타냅니다. 엔트로피는 불확실성의 정도를 나타내는 척도로, 엔트로피가 높으면 불확실성이 크다는 것을 의미합니다. VarEntropy는 엔트로피의 변동성을 나타내는 척도입니다. 지니 계수는 확률 분포의 불균형 정도를 나타내는 척도로, 지니 계수가 높으면 몇몇 토큰에 확률이 집중되어 있음을 의미합니다. 이러한 불확실성 척도를 분석하면 모델의 추론 전략을 개선하는 데 도움이 될 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Uncertainty metrics (variance, entropy, VarEntropy, and the Gini coefficient) plotted against the first 64 tokens of the output token sequence.
> </details>



![](https://arxiv.org/html/2501.11223/x43.png)

> 🔼 그림 10은 서로 다른 크기의 질문 집합에 대해 추정된 95% 신뢰 구간 길이를 보여줍니다. 이는 온도 1에서 질문당 8개의 생성된 답변을 가진 1000개 질문의 하위 집합에서 샘플링된 생성된 답변을 사용합니다. 신뢰 구간은 각 질문의 8개의 서로 다른 pass@1 하위 집합에 대해 계산되며, 각 크기에 대해 32개의 집합이 무작위로 복원 추출됩니다. 즉, 이 그래프는 질문 수가 증가함에 따라 신뢰 구간의 길이가 어떻게 변하는지 보여주는 것으로, 질문 수가 많을수록 신뢰 구간이 좁아지는 것을 알 수 있습니다. 이는 더 많은 데이터를 사용하면 추정의 정확도가 높아진다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Estimated 95%-confidence interval length for different question set sizes using sampled generated answers from a subset of 1000 questions with eight generated answers per question at temperature 1. The confidence interval is calculated over the eight different pass@1 subsets of each question with 32 sets randomly sampled with replacement for each set size.
> </details>



![](https://arxiv.org/html/2501.11223/x44.png)

> 🔼 그림 11은 논문의 9장 'RLM을 위한 벤치마크' 섹션에 포함된 그림으로, 다양한 유형의 추론 문제를 평가하기 위한 벤치마크 데이터셋의 개요를 보여줍니다.  수학적 추론, 논리적 추론, 인과 추론, 상식 추론, 코딩 관련 추론 및 추론 유틸리티 등 여러 범주로 나뉘어져 있으며, 각 범주 내에서 다양한 벤치마크 데이터셋이 제시되어 있습니다. 이 그림은 RLM 모델의 성능을 평가하고 비교하는 데 유용한 다양한 벤치마크 데이터셋의 종류와 특징을 한눈에 파악할 수 있도록 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Overview of benchmarks for RLMs.
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