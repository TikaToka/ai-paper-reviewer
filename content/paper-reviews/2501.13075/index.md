---
title: "Evolution and The Knightian Blindspot of Machine Learning"
summary: "기계 학습이 미래의 불확실성을 다루는 데 어려움을 겪는 이유를 밝히고, 진화론적 접근 방식을 활용하여 이러한 문제를 해결하는 새로운 방법을 제시합니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["AI Theory", "Robustness", "🏢 Second Nature AI",]
showSummary: true
date: 2025-01-22
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.13075 {{< /keyword >}}
{{< keyword icon="writer" >}} Joel Lehman et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-24 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.13075" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.13075" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/evolution-and-the-knightian-blindspot-of" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

본 논문은 **기계 학습(ML)이 열린 세계에서의 미래에 대한 불확실성(나이트 기사 불확실성)**을 다루는 데 어려움을 겪는다는 점을 지적합니다.  ML은 주로 알려진 미지의 영역에 대한 강건성에 초점을 맞추는 반면, **진정한 지능은 예측 불가능한 미래 상황에도 견딜 수 있는 능력**을 필요로 합니다.  기존의 강화 학습(RL) 공식은 이러한 미래 불확실성을 제대로 다루지 못하는 제한점을 가지고 있으며, 이는 **마르코프 결정 과정(MDP)과 같은 단순화된 모델**에 기반한 것입니다.  이러한 단순화된 모델은 열린 세계의 복잡성을 충분히 반영하지 못하고, 예측 불가능한 상황에 취약한 에이전트를 만들어냅니다.



본 논문에서는 **생물학적 진화**의 메커니즘을 연구하여, ML의 한계를 극복하는 방법을 제시합니다.  생물학적 진화는 명시적인 이론이나 공식 없이도 예측 불가능한 환경 변화에 적응하는 강건한 에이전트를 만들어 왔습니다.  논문은 진화론적 과정에서 나타나는 **개방형 탐색 공간, 다양한 전략의 지속적인 생성, 상호 작용을 통한 새로운 환경 창출, 적응 실패에 따른 필터링** 등의 메커니즘을 분석합니다.  그리고 이러한 메커니즘을 기계 학습 알고리즘에 적용하여 **나이트 기사 불확실성에 강건한 인공지능 시스템**을 개발하는 방향을 제시합니다.  특히 인공 생명과 개방형 시스템 연구의 중요성을 강조하며, 기존 강화 학습 공식을 재검토하여 나이트 기사 불확실성을 관리하는 데 필요한 개선을 제시합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 기계 학습의 주요 한계점은 열린 세계 환경에서의 미래 불확실성에 대한 강건성 부족 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 생물학적 진화의 메커니즘을 모방하여 열린 세계 환경에서의 강건성을 향상시키는 새로운 방법 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 인공 생명과 개방형 시스템을 활용하여 나이트 기사 불확실성을 관리하는 새로운 알고리즘 개발의 가능성 제시 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
이 논문은 **기계 학습의 한계점을 극복하고 진정한 강건한 인공지능을 개발하는 데 중요한 의미**를 지닙니다.  연구의 잠재적 영향은 상당하며, 현재 연구 동향과 관련되어 있으며, 추가 연구를 위한 새로운 가능성을 제시합니다. 특히, **열린 세계 환경에서의 강건성을 향상시키기 위한 새로운 알고리즘 개발**에 대한 아이디어를 제공합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.13075/x1.png)

> 🔼 그림 1은 진화가 나이트식 불확실성(KU)에 대한 강인함을 가능하게 하는 상호 연관된 원리를 보여줍니다. (a) 진화는 인간의 두뇌, 다세포 생물, 전체 발달 시스템 및 광합성과 같은 광범위한 복잡한 적응을 암호화할 수 있을 만큼 개방적인 검색 공간 내에서 발생합니다. (b) 진화의 다양화 압력은 개방형 가능성 집합에서 지속적으로 새로운 행동과 적응을 만들어내는데, 이는 유기체와 그 계통이 미래에 어떻게 지속될 수 있는지에 대한 베팅으로 간주될 수 있습니다. (c) 유기체는 다른 유기체의 환경의 일부를 형성하므로, 한 계통의 새로운 행동과 적응은 외부 효과로서 다른 유기체에게 새로운 예측 불가능한 상황을 만듭니다. 예를 들어 나무의 높은 가지는 기린이 활용할 수 있는 새로운 상황을 제공합니다. (d) 다른 유기체에 의해 생성된 불확실성을 극복하지 못한 유기체는 걸러지며, KU를 통해 지속하는 방법에 대한 베팅이 무효화됩니다. 이미지는 4억 년 동안 지속되어 온 실러캔스(coelacanth)라는 물고기를 보여줍니다. 종합적으로 이러한 요소는 KU에 대처하는 방법에 대한 개방형 생성 및 반증 베팅의 형태로 볼 수 있습니다. 저자들은 이러한 원리를 ML 연구에 적용할 수 있는 방법이 있을 것이라고 생각합니다(5절 논의 참조).
> <details>
> <summary>read the caption</summary>
> Figure 1. Interlocking principles enabling evolution’s robustness to Knightian Uncertainty. (a) Evolution happens within a search space that is open-ended enough such that a vast array of complex adaptations can be encoded, e.g. the human brain, multicellularity, developmental systems as a whole, and photosynthesis. (b) Diversification pressure in evolution continually creates new behaviors and adaptations from the set of open-ended possibilities, which implicitly can be seen as bets about how the organism and its lineage can persist into the future. (c) Because organisms form part of the environment of other organisms, novel behaviors and adaptations in one lineage create novel unforeseen situations for other organisms as an externality, e.g. the high branches of a tree provide a novel situation a giraffe can exploit. (d) Organisms unable to persist across the uncertainty created by other organisms are filtered away, in effect invalidating their bets about how to persist through KU; the image shows a coelacanth, a fish that has persisted for 400 million years. In concert, these factors can be seen as a form of open-ended generation and falsification of bets about how to deal with KU. We believe there may be ways to adapt these principles to ML research (see discussion in Section 5).
> </details>





{{< table-caption >}}
| ** ** | **Knowns** | **Unknowns** |
|---|---|---|
| **Known** | Deterministic (Known Knowns) | Risk (Known Unknowns) |
| **Unknown** | Implicit Knowledge (Unknown Knowns) | Knightian Uncertainty (Unknown Unknowns) |{{< /table-caption >}}

> 🔼 표 1은 불확실성의 네 가지 유형(결정론적, 위험, 암묵적 지식, 나이트 불확실성)을 보여줍니다. 완전한 정보를 가진 결정론적 환경에서는 최적화가 가장 간단하지만, 매개변수가 알려져 있거나 추정 가능한 미지수가 있는 위험 상황에서는 더 어려워집니다. 질적으로 새로운 미래 가능성이 존재하여 예측하기 어렵거나 불가능한 미지의 미지수가 있는 상황(본 논문의 중심 주제)은 더욱 어렵습니다. 암묵적 지식(명시적으로 알려지지 않은 암묵적 지식을 에이전트 또는 시스템이 가지고 있는 경우)은 중요하지만 본 논문의 주장과는 관련성이 낮습니다. 간단히 말해 기계 학습은 결정론적 상황이나 위험 상황에서는 뛰어나지만 나이트 불확실성을 모델링하는 데는 어려움을 겪습니다.
> <details>
> <summary>read the caption</summary>
> Table 1. Types of Risk and Uncertainty. Optimization is most straightforward in deterministic settings with complete information, and more challenging in situations of risk, where there are unknowns, but their parameters are known or estimable. More challenging still are situations where there exist unknown unknowns, i.e. future possibilities that are qualitatively novel and difficult or impossible to anticipate (though they may seem obvious in hindsight) – the central topic of this paper. The fourth quadrant of unknown knowns (e.g. where an agent or system has implicit knowledge that is not explicitly known) is also important but less relevant to arguments here. In short, machine learning excels at situations of determinism or risk, but struggles to model Knightian uncertainty.
> </details>





### In-depth insights


#### Knightian Uncertainty
본 논문에서 다루는 '나이트식 불확실성(Knightian Uncertainty)'은 **정량화할 수 없는 불확실성**, 즉 미래에 대한 **알 수 없는 미지수**를 의미합니다.  전통적인 기계 학습(ML)은 이러한 불확실성을 다루지 못하는 한계를 가지고 있으며, 이는 **개방형 세계에서의 진정한 강건성을 확보하는 데 걸림돌**이 됩니다.  **강화 학습(RL)**의 핵심 공식들은 종종 폐쇄적인 세계를 가정하며, 알려지지 않은 미래 상황에 대한 대비가 부족합니다.  반면 **생물학적 진화**는 예측 불가능한 미래에 대한 강건성을 보여주는 좋은 예시로 제시됩니다. **진화 과정은 명시적인 공식이나 이론 없이**, 다양한 시도를 통해 환경에 적응하는 강건한 개체를 만들어 냅니다.  따라서,  **나이트식 불확실성을 효과적으로 다루기 위한 새로운 ML 알고리즘**과 **개방형 세계에 적합한 형식**에 대한 연구가 필요함을 시사합니다.  이는 인공 생명(ALife)과 개방성(open-endedness) 등의 개념을 활용하여 달성될 수 있습니다.

#### Evolution's Robustness
진화의 강인함은 **예측 불가능한 미래에 대한 놀라운 적응력**에서 드러납니다.  **수많은 종들이 예측하지 못한 환경 변화에도 불구하고 생존하고 번성**해 온 것은 단순한 우연이 아닙니다.  이는 **끊임없는 변이와 자연선택**이라는 진화의 메커니즘이 만들어낸 결과입니다.  **다양한 환경에 대한 적응력을 가진 개체들이 살아남고,  그들의 유전적 특징이 다음 세대로 이어짐**으로써 종 전체의 적응성이 향상됩니다.  또한, **진화는 폐쇄적인 시스템이 아닌 개방된 시스템**에서 일어나기 때문에, **끊임없이 새로운 환경과 도전에 직면**하며 진화합니다. 이러한 과정 속에서 **새로운 돌연변이와 혁신적인 적응**이 나타나고 종의 생존 능력을 높입니다.  따라서 진화의 강인함은 **단순한 생존뿐 아니라 끊임없는 혁신과 적응을 통한 지속가능한 발전**이라는 중요한 통찰을 제공합니다.  결론적으로,  진화의 강인함은 **불확실성에 대한 적응과 혁신의 지속성**에 있습니다.

#### RL's Formalism Limits
본 논문에서 제시된 "RL의 형식주의적 한계"에 대한 심층적인 고찰은 **강화학습(RL)의 핵심 형식인 마르코프 결정 과정(MDP)이 갖는 근본적인 가정들이 열린 세계 속의 불확실성을 제대로 다루지 못하는 점**을 강조합니다.  **MDP는 환경의 고정성, 시간의 유한성, 에피소드의 독립성 등을 가정**하는데, 이는 현실 세계의 복잡성과 역동성을 반영하지 못합니다. **열린 세계에서는 예측 불가능한 사건들이 발생**하고, 시간의 흐름에 따라 환경이 변화하며, 에피소드 간의 상호 작용이 발생하기 때문입니다. 따라서 RL은 **나이팅게일 불확실성(KU)에 대한 취약성**을 보이며, **알려지지 않은 미지의 위험에 제대로 대처하지 못할 가능성**이 있습니다. 이러한 한계를 극복하기 위해서는 기존의 형식주의적 제약에서 벗어나, **진화 과정에서 볼 수 있는 시간의 연속성, 개방성, 다양성, 적응성을 고려한 새로운 접근법**이 필요합니다.  **인공 생명(ALife) 및 개방형 끝없는 진화(Open-ended Evolution)**와 같은 연구 분야가 이러한 노력에 도움이 될 수 있습니다.

#### Open-Endedness Promise
본 논문에서 제시된 '열린 종결성의 약속(Open-Endedness Promise)'은 기존의 폐쇄적이고 목표 지향적인 기계 학습(ML) 방식에서 벗어나 **예측 불가능한 미래에 대한 적응력과 견고성**을 강조하는 개념입니다.  이는 **생물학적 진화** 과정에서 발견되는 열린 종결성, 즉 예측 불가능한 환경 변화 속에서도 지속적으로 새로운 적응과 혁신을 창출하는 능력에 착안한 것입니다. 기존 ML의 한계는 알려진 문제에 대한 최적화에 집중하는 반면, 열린 종결성은 **끊임없는 탐색과 다양성 확보**를 통해 미지의 미래에 대한 대비책을 마련하는 데 있습니다.  **인공 생명(ALife) 연구**는 이러한 열린 종결성을 구현하는 유망한 접근 방식으로 제시되며, 이를 통해 **새로운 알고리즘과 아키텍처**를 개발하고, **강화 학습(RL)의 기본적인 형식주의를 재검토**하여 진정으로 견고한 개방형 세계 AI를 만드는 데 기여할 수 있습니다.  **진화 과정의 지속적인 탐색과 선택**을 통해 열린 종결성의 약속은 미래를 예측할 수 없다는 현실을 받아들이고, 이를 극복하기 위한 전략을 제시한다는 점에서 큰 의미가 있습니다.

#### KU in Foundation Models
기반 모델에서의 KU(Knightian Uncertainty)는 **알려지지 않은 미지의 위험**에 대한 모델의 강건성을 다룹니다.  이는 모델이 훈련 데이터에 존재하지 않는 새로운 상황이나 유형의 입력에 어떻게 반응하는지에 대한 질문입니다. 기존의 기반 모델은 주로 알려진 위험(known unknowns)에 초점을 맞추어 훈련되지만,  **진정한 지능**은 예측 불가능한 미래의 상황에 대한 강건성을 포함해야 합니다.  KU를 고려한 훈련 전략은 모델의 안전성과 견고성을 높이는 데 중요하며, 이를 위해서는 **개방형 세계(open-world)** 시나리오에서의 강건성을 평가하는 새로운 방법론이 필요합니다. 또한, **지속적인 학습(continual learning)**과 **메타 학습(meta-learning)**과 같은 기술을 통해 알려지지 않은 미래 상황에 대처할 수 있는 모델의 적응력을 향상시키는 방안을 모색해야 합니다.  **인공 생명체(artificial life)**와 **개방형 발전(open-endedness)** 분야의 연구는 KU에 대한 강건성을 갖춘 시스템을 개발하는 데 새로운 접근 방식을 제공할 수 있습니다.  결론적으로,  기반 모델의 KU에 대한 저항력은 **진정한 인공지능**을 향한 중요한 단계이며, 지속적인 연구가 필요한 분야입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.13075/extracted/6148994/images/04png.png)

> 🔼 그림 2는 열린 세계(open world)에 대처하는 두 가지 전략을 보여줍니다. (a) 다양화 및 필터링(Diversify and Filter)은 미래의 예측 불가능한 상황에 대한 다양한 가설을 지속적으로 갱신하고 적응하는 과정입니다. 이러한 가설들은 나중에 예상치 못한 문제를 해결하는 데 성공함으로써 걸러집니다. 진화, 시장 경쟁, 과학은 이러한 패러다임을 통해 대체로 작동하는 것으로 볼 수 있습니다. 명시적인 형식은 없지만, 강건성은 린디 효과(Taleb, 2014)에 암묵적으로 의존합니다. 즉, 오랫동안 시험을 거친 적응 가능한 해결책은 시험되지 않은 해결책보다 더 오래 지속될 가능성이 높습니다. (b) 예측 및 훈련(Anticipate and Train)에서는 다양한 문제를 먼저 수집하고, 나중에 발생할 수 있는 새로운 상황에 대한 인간의 예측을 통해 보강합니다. 그런 다음, 단일 정책을 훈련하여 문제를 수렴할 때까지 해결하고, 그 정책을 변화하는 세계에 배포합니다. 현재의 기계 학습의 많은 부분이 이러한 패러다임을 채택합니다. 훈련에 사용된 폐쇄된 세계의 형식론이 배포된 열린 세계와 불일치하지만, 일반화를 통해 예상치 못한 문제에 대한 충분한 강건성을 확보할 수 있기를 기대합니다. 하나의 결론은 기계 학습이 자체 방법에 다양화 및 필터링 접근 방식을 더욱 심층적으로 통합하는 것을 배제하지 않는다는 것입니다(Lehman and Stanley, 2010; Kumar et al., 2020; Jaderberg et al., 2017; Lee et al., 2023). 또 다른 결론은 다양화 및 필터링이 새로운 문제가 발생하는 시점의 시간적 구조를 활용하고, 에이전트가 KU 문제를 직접적으로 해결하도록(그렇지 않으면 버려짐) 만든다는 것입니다.
> <details>
> <summary>read the caption</summary>
> Figure 2. Two Strategies for Dealing with an Open World. This figure describes two possible strategies for coping with an open changing world. In (a) diversify-and-filter, a process continually refreshes and adapts its diverse hypotheses about how to persist through the open-ended future. Such hypotheses are filtered through empirical success at tackling later unanticipated problems. Evolution, market competition, and science can be seen to largely operate through this paradigm. There is no explicit formalism, although robustness implicitly relies on the Lindy effect (Taleb, 2014), i.e. an adaptable solution long-tested by time is more likely than an untested one to persist yet longer. In (b) anticipate-and-train, diverse problems are first collected, and augmented through human anticipation about what novel situations might later arise. Then, a single policy is trained to solve the problems to convergence, and that policy is then deployed into a changing world. Much of current ML adopts this paradigm; although the closed-world formalism adopted in training mismatches the open world it is deployed into, the hope is that generalization will enable sufficient robustness to unforeseen challenges. One conclusion is that nothing precludes machine learning from more deeply integrating diversify-and-filter approaches into its methods (Lehman and Stanley, 2010; Kumar et al., 2020; Jaderberg et al., 2017; Lee et al., 2023). Another conclusion is that diversify-and-filter leverages the temporal structure of when novel problems arise, and forces agents to directly grapple with the issue of KU (if they do not, they are discarded).
> </details>



![](https://arxiv.org/html/2501.13075/extracted/6148994/images/03png.png)

> 🔼 그림 3은 알려진 미지수에 대한 최적화가 나이트식 불확실성으로부터 발생하는 위험을 악화시킬 수 있음을 보여줍니다. 폐쇄형 세계 가정을 하는 최적화 형식은 실험자가 예상하는 상황에서 에이전트의 성능을 향상시킬 것입니다. 그러나, 이러한 폐쇄형 세계 최적화 방식이 개방형 세계 에이전트를 공격적으로 훈련시키는 경우, 에이전트는 폐쇄형 세계 가정을 사실로 내면화하도록 유도되어 나이트식 불확실성에 대해 역설적으로 더욱 취약해질 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3. Optimizing for known unknowns can exacerbate risk from Knightian uncertainty. An optimization formalism that makes closed-world assumptions will indeed improve an agent’s performance on the situations an experimenter anticipates. However, if such a closed-world optimizer aggressively trains an open-world agent, the agent may perversely become more brittle to Knightian uncertainty, as it is incentivized to internalize the closed-world assumptions as true.
> </details>



![](https://arxiv.org/html/2501.13075/extracted/6148994/images/02png.png)

> 🔼 이 그림은 신기야 불확실성(Knightian Uncertainty)에 대한 기계학습의 한계를 보여줍니다. 강화 학습 정책의 일부로 에이전트가 먹을 수 있는지 또는 독성이 있는지 여부를 결정하는 상황을 보여줍니다. 훈련 중에 만난 버섯의 분포(빨간색 X와 녹색 +)가 테스트 중에 만난 분포를 반영한다고 가정하는 폐쇄된 환경에서는 에이전트가 훈련을 통해 학습한 결정 경계를 따를 것입니다. 그러나 개방된 환경에서는 모든 버섯 종류가 알려져 있지 않을 수 있고, 정책이 약간 다른 생태계에 배치될 수도 있거나, 새로운 버섯이 진화하거나 개발될 수도 있습니다. (a)에서 예상치 못한 버섯을 만났을 때, 개방형 세계 에이전트가 그것을 먹지 않는 것이 합리적일 것입니다. 신기야 불확실성은 알려진 것으로부터의 단순한 일반화만으로는 해결할 수 없다는 주장입니다.
> <details>
> <summary>read the caption</summary>
> Figure 4. Neural network generalization is not a general cure for Knightian Uncertainty. Imagine as part of a larger reinforcement learning policy, an agent decides whether to eat certain mushrooms, which can either be deadly or edible, and can be separated through features learned in training that correspond to the cap size of the mushroom and its thickness. (a) In a closed world, it is safe to assume that the distribution of mushrooms encountered during training (red ×\times×’s and green +++’s) reflects that encountered during testing, and the (b) NN decision boundary on whether to eat or not eat the mushroom learned through training will likely reflect this assumption. However, in an open world, not all mushroom varieties are known, the policy might be deployed in a slightly different ecosystem, or a new variety of mushroom might evolve or be bred. If encountering the unanticipated mushroom (question mark symbol) at the center of (a), it is likely rational for an open-world agent to forgo eating it, given its novelty and the risk of death. The claim is that simple generalization from what is known does not address Knightian uncertainty.
> </details>



![](https://arxiv.org/html/2501.13075/extracted/6148994/images/05png.png)

> 🔼 그림 5는 전형적인 메타 강화 학습 설정이 예측하지 못한 작업을 해결하는 방법을 학습하도록 유인하지 않는다는 것을 보여줍니다. 이 그림은 전형적인 메타-RL 형식에 따른 최적의 행동을 묘사하는 만화를 보여줍니다. 에이전트는 고정된 작업 분포에서 여러 번 훈련 작업에 노출됩니다. 따라서 에이전트는 작업을 해결하는 데 필요한 모든 정성적 기술을 훈련에서 학습하도록 유도됩니다. 많은 반복 훈련 후에는 IID 테스트 분포에서 새로운 작업을 해결할 때 에이전트에게 큰 놀라움이 남지 않게 됩니다(이것이 알고리즘의 공식적인 목표임). 훈련이 완료되면 최적의 에이전트 동작은 다음과 같이 설명됩니다. (1) 모호한(메타 학습의 필요성을 특징짓는) IID 테스트 분포에서 가져온 작업이 발생합니다. (2) 에이전트는 샘플링된 작업의 모호성을 최적으로 제거하기 위한 작업을 수행합니다. (3) 작업을 식별한 에이전트(훈련에서 유사한 여러 변형을 접했음)는 이전에 학습한 최적의 솔루션을 실행합니다. 실제로 최적의 동작에는 2단계와 3단계를 혼합하는 것이 포함되지만, 이 프로세스에서 공식에 따른 최적성은 일반화된 학습 방법을 학습하는 능력을 요구하지 않습니다. 결론적으로, 알 수 없는 알 수 없는 요소를 접하게 되는 변화하는 세계에 배치되면 에이전트가 원활하게 처리하는 데 어려움을 겪을 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5. Typical metalearning setups do not incentivize learning how to solve unforeseen tasks. This figure offers a caricature of optimal behavior under a typical meta-RL formalism, where an agent is trained across a fixed distribution of problems; this setup is similar to e.g. (Duan et al., 2016). In meta-RL, it is common for an agent to be exposed many times to training tasks covering all major necessary task-relevant skills. Thus the agent is incentivized to learn in training all qualitative skills needed to solve the tasks; after many iterations of training, there need be no significant remaining surprise for the agent when solving new tasks drawn from an IID test distribution (which is the formal goal of the algorithm). At completion of training, an optimal agent’s behavior is sketched as: (1) it encounters a task drawn from the IID test distribution, which is ambiguous (as this characterizes the need for metalearning); (2) the agent takes actions that optimally disambiguate the sampled task; and (3) having identified the task, which it has encountered many similar variants of before in training, the agent executes its previously-learned optimal solution. In practice, optimal behavior will entail mixing steps (2) and (3) together, but nowhere in this process does optimality under the formalism require the generalized ability to learn how to learn. The conclusion is that if then deployed into a changing world where it encounters an unknown unknown, the agent may struggle to handle it gracefully.
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