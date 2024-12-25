---
title: "Diving into Self-Evolving Training for Multimodal Reasoning"
summary: "M-STAR: 다모달 추론을 위한 자기 진화 훈련의 새로운 프레임워크를 제시!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Hong Kong University of Science and Technology",]
showSummary: true
date: 2024-12-23
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.17451 {{< /keyword >}}
{{< keyword icon="writer" >}} Wei Liu et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-24 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.17451" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.17451" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/diving-into-self-evolving-training-for" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델의 발전에도 불구하고, 특히 다모달 영역에서의 추론 능력 향상에는 여전히 어려움이 있습니다.  **다모달 체인-오브-스로트(CoT) 주석 데이터 부족**이 주요한 문제이며, 이는 자기 진화 훈련이라는 새로운 접근 방식을 통해 해결하려는 시도가 이루어지고 있습니다.  자기 진화 훈련은 모델이 자체 출력으로부터 학습하는 방식을 의미합니다.

본 논문에서는 **다모달 추론을 위한 자기 진화 훈련의 복잡성을 해결하기 위해 M-STAR라는 새로운 프레임워크를 제시**합니다.  **훈련 방법, 보상 모델, 프롬프트 변형** 등 세 가지 핵심 요소에 대한 체계적인 분석을 통해 최적의 설계를 도출하고,  **모델의 자기 진화 역동성**에 대한 심층적인 연구를 수행했습니다.  **다양한 크기의 모델과 여러 벤치마크에서 우수한 성능**을 달성하여 자기 진화 훈련의 실용성을 입증했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 다모달 추론을 위한 자기 진화 훈련의 세 가지 주요 요소(훈련 방법, 보상 모델, 프롬프트 변형)에 대한 심층적인 분석 결과를 제시합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 다양한 크기의 모델과 다양한 벤치마크에서 뛰어난 성능을 보이는 M-STAR라는 새로운 자기 진화 훈련 프레임워크를 제안합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 자기 진화 훈련 과정의 역동성을 모니터링하고 분석하여 적응형 탐색 전략을 통해 성능을 향상시키는 방법을 제시합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**본 논문은 다양한 크기의 모델에서 다양한 벤치마크에 걸쳐 범용적으로 효과적인 자기 진화 훈련 프레임워크인 M-STAR를 제시하여 다모달 추론 분야에 상당한 영향을 미칠 것으로 예상됩니다.**  **연구는 자기 진화 훈련의 세 가지 주요 요소(훈련 방법, 보상 모델, 프롬프트 변형)를 체계적으로 분석하고, 최적의 설계 선택을 밝혀냈습니다.**  **자기 진화 역학에 대한 심층적인 이해와 적응형 탐색 전략의 통합을 통해 다모달 추론의 미래 연구를 위한 강력한 기반을 마련할 것입니다.**

------
#### Visual Insights



![](https://arxiv.org/html/2412.17451/x1.png)

> 🔼 그림 1은 논문에서 제안하는 다중 모드 추론을 위한 자기 진화 학습 프레임워크의 개요를 보여줍니다. 이 프레임워크는 학습 방법(Training method), 보상 모델(Reward model), 프롬프트 변화(Prompt variation)의 세 가지 핵심 구성 요소를 중점적으로 다룹니다.  각 요소는 자기 진화 학습의 효과에 영향을 미치는 중요한 요인이며, 본 논문에서는 각 요소에 대한 다양한 구성을 체계적으로 조사하고 분석합니다.  정적 요소들(세 가지 구성 요소)과는 별도로, 자기 진화 과정의 역동성(Dynamics of self-evolution) 또한 모니터링하여 학습 과정에 제어 신호를 제공합니다.  즉, 모델의 성능 변화를 실시간으로 관찰하고, 이를 바탕으로 학습 과정을 조정하여 최적의 성능을 달성하는 것을 목표로 합니다. 이 그림은 자기 진화 학습의 전체적인 흐름과 주요 구성 요소 간의 상호 작용을 시각적으로 보여주는 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Overview of our self-evolving training framework for multimodal reasoning. We investigate the three essential design components of it, namely Training method (𝒯𝒯\mathcal{T}caligraphic_T), Reward model (ℛℛ\mathcal{R}caligraphic_R), and Prompt variation (𝒫𝒫\mathcal{P}caligraphic_P). Orthogonal to the static factors, the Dynamics of self-evoloution is also monitered, and provides control signals to the training process.
> </details>





{{< table-caption >}}
| Method | <math>\mathcal{M}</math> | <math>\mathcal{O}</math> | Iteration Interval (#) | MathV360K | MathVista |
|---|---|---|---|---|---| 
| MiniCPM-V-2.5 | - | - | - | 13.6 | 52.4 |
| +warmup | - | - | - | 38.8 | 52.6 |
| SFT | - | - | - | 44.3 | 54.8 |
| Iterative RFT | <math>\pi_{\theta}^{t}</math> | <math>\times</math> | 100%(180K) | 42.3 | 55.7 |
| Rest<sup>EM</sup> | <math>\pi_{\theta}^{0}</math> | <math>\times</math> | 100%(180K) | 42.3 | 55.1 |
| Continous Self-Evolving | <math>\pi_{\theta}^{t}</math> | <math>\checkmark</math> | 100%(180K) | 42.2 | 56.7 |
|  |  |  | 50%(90K) | 43.1 | 56.2 |
|  |  |  | 25%(45K) | 43.1 | 57.2 |
|  |  |  | 12.5%(22K) | 42.3 | 56.1 |
|  |  |  | 6.25%(11K) | 41.0 | 56.8 |{{< /table-caption >}}

> 🔼 표 1은 다양한 학습 방법과 반복 간격을 사용한 자기 진화 학습의 정확도 결과(%)를 보여줍니다. 반복 간격(#)은 한 번의 반복에서 처리하는 데이터의 비율을 나타내며, 해당 쿼리 수도 기록합니다. ℳℳ mathcal{M}은 각 반복에서 학습이 초기화되는 정책 모델을 나타냅니다. 𝒪𝒪 mathcal{O}는 최적화 프로세스가 연속적인지 여부, 즉 최적화기 상태와 학습률 스케줄러가 이전 체크포인트에서 상속되는지 여부를 나타냅니다. MathVista의 모든 하위 작업에 대한 전체 결과는 표 4를 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Table 1:  Accuracy results (%) of self-evolving training using various training methods and iteration intervals. Iteration Interval (#) stands for the ratio of data we traverse in one iteration, and we also record the number of corresponding queries. ℳℳ\mathcal{M}caligraphic_M represents the policy model from which training is initialized in each iteration. 𝒪𝒪\mathcal{O}caligraphic_O denotes whether the optimization process is continuous, i.e., the optimizer states and lr scheduler are inherited from the last checkpoint. Please refer to Table 4 to check the full results on all sub-tasks of MathVista.
> </details>





### In-depth insights


#### Self-Evolving LMMs
자기 진화형 거대 다중 모달 모델(LMMs)은 **자체 출력으로부터 학습**하여 추론 능력을 향상시키는 접근 방식입니다. 이는 다중 모달 사고 과정에 대한 주석이 달린 데이터가 부족한 상황에서 특히 효과적입니다. 본 논문에서는 훈련 방법, 보상 모델, 프롬프트 변화 등 세 가지 주요 요소를 체계적으로 분석하여 다중 모달 추론을 위한 자기 진화형 학습의 복잡성을 탐구합니다. 각 요소에 대한 최상의 사례를 제시하고, 학습 중 자기 진화 역학과 성능 향상에 있어서 자동 균형 메커니즘의 영향을 분석합니다. **최종적으로 M-STAR(다중 모달 자기 진화형 추론 학습) 프레임워크**를 제시하며, 이는 다양한 크기의 모델에서 광범위한 벤치마크에 대해 효과적임을 보여줍니다. **탐험과 활용의 균형을 맞추는 적응적 탐색 전략**을 통합하여 성능이 향상됩니다.

#### M-STAR Framework
M-STAR 프레임워크는 **다양한 크기의 모델에서 다양한 벤치마크를 통해 보편적으로 효과적**임을 보여주는 견고한 다중 모드 자기 진화 훈련 프레임워크입니다.  **훈련 방법, 보상 모델, 프롬프트 변화**의 세 가지 핵심 요소를 체계적으로 조사하여 각 요소에 대한 모범 사례를 제시합니다.  **자기 진화 역학**에 대한 분석을 통해 탐색과 활용 간의 균형을 맞추는 자동 균형 메커니즘의 영향을 밝힙니다.  **연구는 다양한 다중 모드 추론 벤치마크에서 우수한 성능을 달성**하며, 향후 연구를 위한 견고한 프레임워크를 제공합니다.  **모델의 성능 향상과 더불어, 탐색 능력 유지**를 위한 동적 온도 조절 기법도 제시하여 실질적 가치를 더합니다.  전반적으로, M-STAR는 다중 모드 추론을 위한 자기 진화 학습에 대한 심층적인 이해와 미래 연구를 위한 강력한 프레임워크를 제공합니다.

#### Reward Model Impact
본 논문에서 다룬 자기 진화 학습(Self-evolving training) 방법론의 핵심 요소 중 하나인 보상 모델(Reward Model)의 영향에 대한 심층적인 분석 결과를 요약하면 다음과 같습니다. **단순한 이진 보상(Binary reward) 방식 대신, 과정 기반 보상 모델(Process Reward Model, PRM)을 제안하여 중간 단계 추론 과정의 질적 측면까지 고려**함으로써 성능 향상을 도모했습니다.  **PRM은 단순히 정답/오답 여부만 평가하는 것이 아니라, 추론 과정의 각 단계별 점수를 종합적으로 고려**하여 보다 세분화된 피드백을 제공합니다.  실험 결과, PRM을 적용한 자기 진화 학습은 다양한 벤치마크에서 기존 방식보다 우수한 성능을 보였으며, 특히 **어려운 추론 문제에 대한 성능 향상이 두드러졌습니다**.  하지만, **PRM의 검증 능력(Verification ability)은 완벽하지 않아 보완이 필요**하다는 점도 지적되었습니다.  즉, PRM은 보상 신호를 생성하는 데 효과적이지만, 그 신호의 정확성을 완벽히 보장하지는 못한다는 제한점이 있음을 밝혔습니다. 따라서, **추후 연구에서는 보상 모델의 신뢰성 향상 및 보다 강건한 자기 진화 학습 프레임워크 구축**에 초점을 맞춰야 할 것으로 판단됩니다.  **다양한 보상 모델의 비교 및 분석**, 그리고 **보상 모델의 설계 및 훈련 전략에 대한 추가 연구**가 필요합니다.

#### Exploration Dynamics
본 논문에서 '탐색 역학(Exploration Dynamics)'은 **자기 진화 학습 과정에서 모델의 탐험 능력 변화**를 추적하고 분석하는 부분입니다.  단순히 정확도 향상만을 목표로 하는 것이 아니라, **모델이 새로운 해결책을 찾아내는 능력**, 즉 다양한 해결 전략을 시도하는 능력의 변화를 면밀히 관찰합니다.  **온라인 강화학습**과 유사하게, 모델은 탐색(exploration)과 활용(exploitation) 사이의 균형을 유지해야 합니다.  탐색이 부족하면 성능 향상에 한계가 있고, 과도한 탐색은 학습의 불안정성을 야기합니다.  따라서 논문에서는 **온도 매개변수를 동적으로 조절**하는 기법을 제시하여 이러한 균형을 유지하려고 시도합니다.  이는 모델의 학습 과정 전반에 걸쳐 **탐색과 활용의 동적인 상호작용**을 분석하고, 그 결과를 바탕으로 최적의 학습 전략을 제시하는 데 중요한 역할을 합니다.  결론적으로, '탐색 역학' 분석은 자기 진화 학습의 효율성과 안정성을 높이는 핵심 요소이며, **실제 응용을 위한 중요한 지침**을 제공합니다.

#### Future of Self-Evo
자기 진화 학습의 미래는 **더욱 정교한 보상 모델과 탐색-활용 전략의 개발**에 달려 있습니다.  현재의 자기 진화 학습은 모델이 스스로 생성한 데이터로부터 학습하기 때문에, 보상 모델의 질이 성능을 크게 좌우합니다. 따라서 **더욱 정확하고 일반화된 보상 모델**을 개발하는 것이 중요합니다. 또한, 모델이 학습 과정에서 지나치게 탐색 능력을 잃지 않도록 **탐색-활용의 균형을 유지하는 메커니즘**이 필요합니다.  **다양한 모달리티(텍스트, 이미지, 비디오 등)를 통합하는 다중 모달 자기 진화 학습** 또한 중요한 연구 방향입니다.  **인간의 개입을 최소화하면서 효율적으로 모델을 학습시키는 방법**에 대한 연구도 활발히 진행될 것으로 예상됩니다.  궁극적으로는 **인간 수준의 추론 능력을 갖춘 인공지능 모델**을 개발하는 데 자기 진화 학습이 중요한 역할을 할 것으로 기대됩니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.17451/x2.png)

> 🔼 그림 (a)는 다양한 온도에서의 Pass@K 지표 변화를 보여줍니다. Pass@K는 모델이 K개의 샘플을 생성할 때 적어도 하나의 정답을 생성하는 비율을 나타냅니다. 훈련 과정에서 Pass@K가 감소하는 경향이 나타나는데, 이는 모델의 탐색 능력 저하를 시사합니다. 높은 온도에서는 이러한 감소 경향이 다소 완화되는 것을 확인할 수 있습니다. 이는 온도가 모델의 탐색 능력에 영향을 미치며, 훈련 후반부에서도 탐색 능력을 유지하는 데 기여할 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (a)
> </details>



![](https://arxiv.org/html/2412.17451/x3.png)

> 🔼 그림 2(b)는 자가 진화 훈련 중 다양한 시도 횟수에 따른 최적 응답의 단계 수 분포를 보여줍니다. 자가 진화 과정에서 보상 모델이 중간 단계의 품질을 평가하여 상위 K개의 응답을 선택하는 전략을 사용합니다. 이 그림은 보상 모델이 선택한 상위 2개 응답과 나머지 정답의 단계 수를 비교 분석하여 보상 모델의 효과를 시각적으로 보여줍니다. 상위 2개 응답은 일반적으로 더 적은 단계로 문제를 해결하는 경향이 있으며, 이는 보상 모델이 더 효율적이고 정확한 추론 과정을 가진 응답을 잘 식별한다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (b)
> </details>



![](https://arxiv.org/html/2412.17451/x4.png)

> 🔼 그림 4 (c)는 자가 진화 훈련 과정에서 보상 기반 Pass@2 지표의 변화를 보여줍니다. 훈련이 진행됨에 따라 보상 모델의 활용 효율성을 나타내는 이 지표는 빠르게 안정화되는 것을 확인할 수 있습니다. 이는 보상 모델의 탐색 능력이 감소하고, 훈련 과정 후반부에 더 이상 새로운 고품질 응답을 찾지 못함을 시사합니다. 즉, 모델의 탐색 능력이 감소함에 따라 보상 모델이 더 이상 새로운 고품질 응답을 발견하지 못하게 되어 성능 향상에 한계가 발생함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (c)
> </details>



![](https://arxiv.org/html/2412.17451/x5.png)

> 🔼 그림 2는 자가 진화 학습에서 보상 모델을 사용하여 응답을 재순위화한 후, 정답을 생성한 여러 응답들 중 상위 2개와 나머지 응답들의 차이를 보여줍니다. (a)는 그리디 디코딩과 세 가지 선택 전략에 따른 검증 세트의 정확도를 다양한 롤아웃 수에 대해 나타낸 그래프입니다. (b)는 상위 2개 응답과 보상에 따라 재순위화된 나머지 응답들의 평균 단계 수 분포를 보여주는 히스토그램이고, (c)는 GPT-4에 의해 주석이 달린 상위 2개 응답과 나머지 응답들의 평균 상관 점수 분포를 나타낸 히스토그램입니다.  모든 분석은 정답만을 대상으로 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: (a): Accuracy on the val. set of greedy decoding and three selection strategy across different numbers of rollouts; (b)/(c): Distribution of average # of steps and average relativity score annotated by GPT4-o of Top 2 and the rest responses re-ranked by rewards, we only calculate on correct ones.
> </details>



![](https://arxiv.org/html/2412.17451/x6.png)

> 🔼 그림 3은 모델 학습 진행에 따른 Greedy Decoding 정확도와 Pass@K 지표의 상반된 추세를 보여줍니다. Greedy Decoding 정확도는 학습이 진행될수록 향상되는 반면, Pass@K 지표는 감소하는 것을 알 수 있습니다. 이는 모델이 학습 과정에서 탐색(exploration) 능력을 잃고, 최적의 답을 찾는 것에만 집중하게 됨을 시사합니다.  Pass@K 지표는 모델이 다양한 답변을 생성하는 능력을 나타내는 반면, Greedy Decoding 정확도는 모델이 단일 최적의 답변을 생성하는 능력을 나타냅니다. 따라서 두 지표의 상반된 추세는 모델의 탐색 능력 저하와 최적화 능력 향상 간의 상충 관계를 보여주는 중요한 지표입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: The opposite trend of Greedy Decoding Accuracy and Pass@K.
> </details>



![](https://arxiv.org/html/2412.17451/x7.png)

> 🔼 그림 4(a)는 다양한 온도에서 Pass@K 지표 변화를 보여줍니다. Pass@K는 모델이 K개의 후보 샘플 중 적어도 하나의 정답을 생성하는 비율을 나타냅니다. 훈련 과정에서 Pass@K가 감소하는 경향이 나타나는데, 이는 모델의 탐색 능력이 감소함을 의미합니다. 그러나 더 높은 온도에서는 이러한 감소 경향이 완화되는데, 이는 높은 온도가 모델의 탐색 능력을 유지하는 데 도움이 될 수 있음을 시사합니다.  이는 훈련 후반부에 모델의 탐색 능력 저하를 방지하기 위해 온도를 동적으로 조절해야 할 필요성을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (a)
> </details>



![](https://arxiv.org/html/2412.17451/x8.png)

> 🔼 그림 2(b)는 자가 진화 학습 중에 생성된 응답의 평균 단계 수 분포를 보여줍니다. 자가 진화 학습 과정에서 보상 모델에 의해 재순위 지정된 상위 2개의 정답과 나머지 정답들을 비교 분석하여, 보상 모델이 생성된 응답의 품질을 평가하는 데 어떻게 기여하는지 보여줍니다. 상위 2개의 정답은 일반적으로 더 적은 단계를 거쳐 생성되며, 이는 보상 모델이 더 효율적이고 정확한 추론 과정을 선호함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (b)
> </details>



![](https://arxiv.org/html/2412.17451/x9.png)

> 🔼 그림 2(c)는 자가 진화 학습 중에 생성된 응답의 상대 점수 분포를 보여줍니다. 자가 진화 학습 과정에서 보상 모델이 상위 2개의 응답을 선택하는 전략을 사용하는데, 이 그림은 보상 점수에 따라 재 순위가 매겨진 올바른 응답 중 상위 2개와 나머지 올바른 응답의 평균 단계 수와 상대 점수의 분포를 비교합니다.  상위 2개 응답이 다른 올바른 응답보다 단계 수가 적고 상대 점수가 높은 경향을 보이는 것을 확인할 수 있습니다. 이는 보상 모델이 실제로 질문과 밀접하게 관련된 고품질 응답을 효과적으로 식별하는 데 도움이 된다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (c)
> </details>



![](https://arxiv.org/html/2412.17451/x10.png)

> 🔼 그림 4는 자가 진화 학습 과정에서 다양한 온도 값에 따른 세 가지 지표의 변화를 보여줍니다. (a)는 다양한 온도에서 Pass@K 값의 감소 추세를, (b)는 Pass@K와 탐욕적 디코딩 간의 차이 변화를, (c)는 Reward-Pass@2 값의 빠른 포화 현상을 나타냅니다. 세 가지 지표 모두 검증 세트를 기반으로 계산되었습니다.  Pass@K는 모델이 K개의 후보 응답 중 적어도 하나의 정답을 생성하는 비율을 나타내며, 탐욕적 디코딩은 모델이 가장 높은 확률의 응답을 선택하는 방식입니다. Reward-Pass@2는 보상 모델에 의해 상위 2개의 응답 중에 정답이 있는 비율을 나타냅니다. 이 그림은 모델의 탐색 능력 저하 및 보상 모델의 효과 감소를 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: (a): Pass@K decreases for all different temperatures; (b): The gap between Pass@K and Greedy Decoding; (c): The Reward-Pass@2 saturates quickly. All metrics, including the greedy decoding accuracy, are calculated on validation set.
> </details>



![](https://arxiv.org/html/2412.17451/x11.png)

> 🔼 그림 5는 최적의 정적 훈련 과정(T=1.0으로 고정)과 비교하여 부드럽게 처리된 Pass@K 및 Reward-Pass@2 곡선을 비교한 것입니다.  Pass@K는 모델이 K개의 샘플을 생성할 때 적어도 하나의 정답을 생성하는 비율을 나타내며 모델의 탐색 능력을 측정합니다. Reward-Pass@2는 상위 2개의 응답 중에 정답이 있는 비율을 나타내며 보상 모델의 활용 효율성을 보여줍니다. 이 그림은 훈련 중 모델의 탐색 및 활용 능력의 변화 추이를 보여주며,  정적 온도 설정(T=1.0)과 비교하여 M-STAR 모델의 적응적 온도 조절 전략의 효과를 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Comparing the smoothed Pass@K and Reward-Pass@2 curves with the optimal static training progress, which fixs T=1.0𝑇1.0T=1.0italic_T = 1.0.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | \mathcal{H} | PRM | MathV360K | MathVista |
|---|---|---|---|---|
| Continuous Self-Evolving | - | \times | 43.1 | 57.2 |
| + Random Selection | \operatorname{Random-2} | \times | 41.0 | 55.5 |
| +PRM-based Selection | &gt;\alpha | \checkmark | 43.8 | 57.5 |
|  | \operatorname{Top-1} |  | 43.0 | 59.0 |
|  | \operatorname{Top-2} |  | 45.3 | 59.2 |
|  | \operatorname{Top-4} |  | 44.0 | 58.4 |{{< /table-caption >}}
> 🔼 표 2는 PRM(Process Reward Model)을 사용한 자기 진화 학습 결과를 보여줍니다.  여러 전략을 통해 정답 응답 중에서 고품질 응답을 선별하는 방법을 비교 분석합니다.  첫 번째 전략(Top-k)은 보상 점수가 가장 높은 K개의 정답 응답을 선택하고, 두 번째 전략(>α)는 보상 점수가 α보다 높은 정답 응답을 모두 선택합니다. MathVista의 모든 하위 작업에 대한 전체 결과는 표 4를 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Table 2: The results of self-evolving training with PRM and different strategies to leverage reward scores. ℋℋ\mathcal{H}caligraphic_H stands for the method to further pick out high-quality responses from the correct rollouts: (1) Top−kTopk\operatorname{Top-k}roman_Top - roman_k is we select K correct responses with highest rewards, and (2) >αabsent𝛼>\alpha> italic_α is we pick out the correct responses with reward scores larger than α𝛼\alphaitalic_α. Please refer to Table 4 to check the full results on all sub-tasks of MathVista.
> </details>

{{< table-caption >}}
| Oracle | PRM |  | MathV360K | MathVista |
|---|---|---|---|---|
| $T_{mixin}$ | × | - | 43.1 | 57.2 |
|  | ✓ | - | 45.3 | 59.2 |
| ✓ | × | 0% | 42.5 | 58.2 |
| ✓ | ✓ | 0% | 42.9 | 59.1 |
| × | ✓ | 0% | 43.3 | 58.2 |
| × | ✓ | 25% | 42.4 | 57.6 |
| × | ✓ | 50% | 42.9 | 58.2 |
| × | ✓ | 75% | 45.0 | 58.8 |{{< /table-caption >}}
> 🔼 표 3은 레이블이 없는 데이터를 사용한 결과를 보여줍니다.  `T_mixin`은 레이블 없는 데이터를 섞는 시점을 나타냅니다.  PRM의 사용은 3.3절과 동일하지만, 레이블 없는 프롬프트에 대한 가중치 투표를 통해 의사 ground truth를 먼저 얻는다는 점이 다릅니다. 이 표는 레이블 없는 데이터를 추가하여 모델 성능에 어떤 영향을 미치는지, 그리고 그 시점이 성능에 어떻게 영향을 주는지를 보여주는 실험 결과를 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Results of involving unlabeled data. Tmixinsubscript𝑇mixinT_{\texttt{mixin}}italic_T start_POSTSUBSCRIPT mixin end_POSTSUBSCRIPT denotes when to mixin the unlabeled data. The use of PRM follows §3.3, except we first get a pesudo “ground truth” through weighted voting on unlabeled prompts.
> </details>

{{< table-caption >}}
|           | MathVista | M3CoT | MMStar-R | MMBench-R | AI2D | Average |
| :--------- | :-------: | :-------: | :-------: | :-------: | :-------: | :-------: |
| MiniCPM-V-2.5 | 52.4 | 41.2 | 44.6 | 72.6 | 64.4 | 55.0 |
| + warmup | 52.6 | 47.8 | 45.1 | 76.9 | 65.9 | 57.7 |
| M-STaR      | **59.5**<sub>↑ 6.9</sub> | **48.7**<sub>↑ 0.9</sub> | **50.7**<sub>↑ 5.6</sub> | **79.9**<sub>↑ 3</sub> | **69.1**<sub>↑ 3.2</sub> | **61.6**<sub>↑ 3.9</sub> |
| Phi-3.5-vision | 46.5 | 39.4 | 42.5 | 56.8 | 47.5 | 46.5 |
| + warmup | 49.3 | 46.5 | 44.2 | 70.9 | 65.5 | 55.3 |
| M-STaR      | **54.5**<sub>↑ 5.2</sub> | **51.3**<sub>↑ 4.8</sub> | **48.8**<sub>↑ 4.6</sub> | **73.6**<sub>↑ 2.7</sub> | **67.9**<sub>↑ 2.4</sub> | **59.2**<sub>↑ 3.9</sub> |
| InternVL2-2B | 46.4 | 16.7 | 20.0 | 14.2 | 33.5 | 26.2 |
| + warmup | 47.6 | 45.6 | 41.8 | **68.8** | **60.0** | 52.8 |
| M-STaR      | **50.3**<sub>↑ 2.7</sub> | **47.1**<sub>↑ 1.5</sub> | **42.0**<sub>↑ 0.2</sub> | 67.3<sub>↓ 1.5</sub> | 59.7<sub>↓ 0.3</sub> | **53.3**<sub>↑ 0.5</sub> |{{< /table-caption >}}
> 🔼 표 4는 MathVista 데이터셋에 대한 자세한 분석 결과를 보여줍니다. MathVista는 다양한 유형의 수학적 추론 문제를 포함하고 있으며, 각 문제는 그림, 기하학적 도형, 수식, 교과서 내용, 이미지 등 다양한 형태로 제시됩니다. 표에는 다섯 가지 유형의 문제(FQA: 그림 질문 풀이, GPS: 기하 문제 풀이, MWP: 수학적 단어 문제, TQA: 교과서 질문 풀이, VQA: 시각적 질문 풀이)에 대한 M-STaR 모델의 성능이 자세히 제시되어 있습니다. 특히,  '+warmup' 행은 사전 학습된 모델에 비해 M-STaR 모델의 성능 향상 정도를 보여줍니다. 이를 통해 M-STaR 모델의 성능 우수성과 다양한 유형의 문제에 대한 일반화 능력을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Full analysis of MathVista. Task types: FQA: figure question answering, GPS: geometry problem solving, MWP: math word problem, TQA: textbook question answering, VQA: visual question answering. We highlight the relative improvement of M-STaR over the pre-evolved model, i.e., the “+warmup” row.
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