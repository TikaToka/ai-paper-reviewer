---
title: "QLASS: Boosting Language Agent Inference via Q-Guided Stepwise Search"
summary: "QLASS: 제한된 지도 학습 데이터로도 뛰어난 언어 에이전트 추론 성능을 달성!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 UC Los Angeles",]
showSummary: true
date: 2025-02-04
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.02584 {{< /keyword >}}
{{< keyword icon="writer" >}} Zongyu Lin et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-05 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.02584" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.02584" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/qlass-boosting-language-agent-inference-via-q" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

많은 기존 연구는 언어 에이전트의 성능 향상을 위해 전체 경로에 대한 결과 보상 모델을 사용합니다. 하지만 이 방법은 중간 상호 작용 단계의 정보를 활용하지 못하여 최적이 아닌 정책을 생성하고 전반적인 성능을 저해할 수 있습니다. 특히, 중간 상호작용에 대한 주석이 부족하여 전체 경로에 대한 결과 보상만으로 학습하는 한계가 존재합니다.

본 논문에서는 이러한 문제를 해결하기 위해 단계별로 Q-값을 추정하여 주석을 자동 생성하는 QLASS(Q-guided Language Agent Stepwise Search)를 제안합니다. QLASS는 탐색 트리를 도입하고, 단계별 보상 모델링을 수행하여 각 단계에 효과적인 중간 지침을 제공합니다. **실험 결과, QLASS는 복잡한 상호 작용 에이전트 작업에서 모델 추론 중 성능을 크게 향상시키며, 기존 방법보다 효율적이고 효과적인 의사 결정을 가능하게 합니다.** 또한, 주석 데이터가 절반 수준이어도 강력한 성능을 유지함을 보여줍니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 제한된 지도 학습 데이터만으로도 우수한 성능을 보이는 QLASS 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 단계별 보상 모델링 및 Q-학습 기반의 탐색 트리를 통해 에이전트의 의사 결정 과정 개선 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 다양한 복잡한 상호 작용 에이전트 작업에서 효과적임을 실험적으로 검증 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 제한된 지도 학습 데이터를 사용하여 복잡한 상호 작용 에이전트 작업에서 언어 에이전트의 추론 성능을 크게 향상시키는 새로운 방법인 QLASS를 제시합니다. **QLASS는 단계별 보상 모델링과 Q-학습 기반의 탐색 트리를 사용하여 에이전트의 의사 결정 과정을 개선하고, 제한된 지도 데이터로도 강력한 성능을 유지합니다.** 이는 언어 에이전트 연구 분야에 중요한 발전이며, 향후 연구에 새로운 방향을 제시합니다. 특히, 제한된 데이터 환경에서 언어 모델의 자기 개선 기술 개발에 큰 영향을 미칠 것으로 예상됩니다. 또한, **단계별 보상 모델링과 Q-학습의 결합은 다양한 상호 작용 에이전트 작업에 적용 가능하며, 향후 더욱 효율적이고 일반적인 언어 에이전트를 개발하는 데 기여할 것**으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.02584/x1.png)

> 🔼 그림 1은 QLASS의 파이프라인을 개괄적으로 보여줍니다. QLASS는 크게 네 단계로 구성됩니다. 1단계는 전문가 데이터를 사용한 지도 학습 미세 조정(SFT)입니다. 2단계는 SFT 에이전트를 활용하여 환경을 탐색하고 각 작업에 대한 탐색 트리를 구성하는 단계입니다. 트리 구성 후에는 방정식 7을 기반으로 각 트리 노드의 Q-값을 추정합니다. 3단계는 추정된 Q-값을 사용하여 QNet을 훈련시키는 단계입니다. 4단계는 훈련된 QNet을 사용하여 각 단계에서 추론 안내를 제공하는 단계입니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: QLASS pipeline overview. QLASS involves mainly four stages: 1) Supervised fine-tuning (SFT) on expert data. 2) Leverage SFT agent to explore the environment and construct an exploration tree for each task. After construction, estimate the Q-value of each tree node based on Equation 7. 3) Train QNet on the estimated Q-values. 4) Use the trained QNet to provide inference guidance at each step.
> </details>





{{< table-caption >}}
| Dataset | #Train | #Test-Seen | #Test-Unseen | #Turns |
|---|---|---|---|---|
| WebShop | 1,938 | 200 | - | 4.9 |
| SciWorld | 1,483 | 194 | 241 | 14.4 |
| ALFWorld | 3,321 | 140 | 134 | 10.1 |{{< /table-caption >}}

> 🔼 표 1은 본 논문에서 사용된 세 가지 에이전트 데이터셋(WebShop, SciWorld, ALFWorld)의 통계를 보여줍니다.  데이터셋은 각각 훈련 세트와 테스트 세트(Test-Seen 및 Test-Unseen)로 나뉘며, Test-Seen은 훈련 중에 보였던 사례들을, Test-Unseen은 새로운 사례들을 포함합니다.  #Turns 열은 SFT(Supervised Fine-Tuning) 과정에서 에이전트 상호작용의 평균 턴 수를 나타냅니다. Song et al.(2024)의 ETO 논문과 동일한 설정을 따랐습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: The statistics of datasets (We follow the same setup as ETO (Song et al., 2024)). “Test-Seen” and “Test-Unseen” are test sets with seen and unseen cases respectively. “#Turns” means the average number of interaction turns for the SFT trajectories.
> </details>





### In-depth insights


#### Q-Learning for LLMs
**대규모 언어 모델(LLM)**에서 Q-학습의 적용은 **에이전트 기반 작업**에서 특히 유망합니다.  기존의 강화 학습 기법과 달리, Q-학습은 모델이 **상호작용을 통해 학습**하고 **장기적인 보상**을 최대화하도록 돕습니다.  LLM의 경우, Q-함수는 특정 상태에서 특정 행동을 취했을 때 예상되는 누적 보상을 나타냅니다.  **탐색 트리(exploration tree)**와 같은 구조를 통해 LLM이 다양한 상호작용 경로를 탐색하고, 각 단계에서의 Q-값을 추정하여 최적의 행동을 선택하도록 유도할 수 있습니다.  하지만, **높은 차원의 행동 공간**과 **희소한 보상** 문제는 Q-학습을 LLM에 직접 적용하는 데 어려움을 야기합니다. 따라서, **오프라인 학습(offline learning)**과 같은 전략을 통해 이러한 문제를 완화하고 효율적인 Q-학습을 가능하게 할 수 있습니다.  **제한된 감독** 환경에서도 효과적이도록 Q-학습을 설계하는 것이 중요하며, 이는 **자기 개선(self-improvement)** 알고리즘과 결합하여 더욱 강력한 LLM 에이전트를 구축하는 데 기여할 수 있습니다.

#### Stepwise Reward Model
논문에서 "Stepwise Reward Model"이라는 제목의 섹션에 대한 심층적인 분석을 통해 얻은 통찰력을 요약하면 다음과 같습니다. **단계별 보상 모델은 에이전트의 성과를 평가하는 기존의 단순한 최종 결과 보상 모델의 한계를 극복하기 위해 고안되었습니다.**  **중간 단계의 상호 작용에 대한 정보를 활용하여 각 단계의 결정이 장기적인 목표 달성에 얼마나 기여하는지를 평가합니다.** 이는 **에이전트가 단순히 최종 목표에 도달하는 것 이상으로,  최적의 경로를 찾아 효율성을 높이는 데 도움**을 줍니다. 이를 위해 **Q-학습과 같은 강화 학습 기법을 활용하여 각 단계별 Q-값을 추정**하고, 이를 토대로 **단계별 보상 모델을 구성**합니다.  **탐색 트리를 이용한 탐색 전략**은 에이전트가 효과적으로 단계별 보상을 수집하고 학습할 수 있도록 지원합니다.  결과적으로, **단계별 보상 모델은 제한된 감독 하에서도 강력한 성능을 유지하며, 효율적인 의사결정을 통해 에이전트의 전체적인 성능을 향상**시킵니다.  **이 모델은 복잡한 상호 작용이 포함된 작업에서 특히 유용하며, 긴 트래젝토리 내에서 각 단계의 중요도를 정확히 평가**할 수 있다는 점에서 혁신적입니다.  **하지만, Q-값 추정의 정확성 및 탐색 트리 구축의 효율성이 전체 모델의 성능에 영향**을 미칠 수 있다는 점을 유념해야 합니다.

#### QLASS Pipeline
QLASS 파이프라인은 **지도 학습 기반의 언어 에이전트 미세 조정**, **탐색 트리 생성 및 Q-값 추정**, **Q-네트워크 학습**, **Q-유도 생성**의 네 가지 주요 단계로 구성됩니다. 먼저, 전문가 데이터를 사용하여 언어 에이전트를 미세 조정합니다. 다음으로, 미세 조정된 에이전트를 사용하여 환경을 탐색하고 각 작업에 대한 탐색 트리를 구축하며, 벨만 방정식을 통해 각 트리 노드의 Q-값을 추정합니다.  이 Q-값들은 트리 구조를 기반으로 계산되며 장기적인 보상을 고려하여 단기적인 보상만 고려하는 기존 방법보다 더욱 효과적인 중간 단계 지침을 제공합니다.  추정된 Q-값들을 사용하여 Q-네트워크를 학습하고, 마지막으로 학습된 Q-네트워크를 사용하여 각 단계에서 에이전트의 의사결정을 안내합니다. **Q-값 기반의 단계적 안내**는 에이전트가 장기적인 가치에 더 잘 적응하고 복잡한 대화형 작업에서 성능을 크게 향상시키는 데 중요한 역할을 합니다.  **제한된 감독 데이터**를 사용하더라도 강력한 성능을 유지하며, 효율적인 의사결정을 통해 효과적인 중간 단계 지침을 제공합니다.

#### Limited Supervision
제한된 감독 환경에서의 언어 에이전트 성능 향상에 대한 연구는 **데이터 부족** 문제를 해결하는 중요한 과제입니다.  본 논문에서는 제한된 데이터로도 높은 성능을 유지하는 QLASS 모델의 효율성을 보여줍니다.  이는 **단계별 보상 모델링**을 통해 중간 단계의 상호작용에 대한 정보를 자동으로 생성하고, 이를 통해 에이전트가 장기적인 가치를 고려하여 더 효과적인 의사결정을 할 수 있도록 돕기 때문입니다.  **탐색 트리**를 이용하여 중간 단계의 가치를 추정하고, 이를 기반으로 **Q-학습** 알고리즘을 적용하여 단계별 가이드를 제공하는 전략은 제한된 감독 하에서도 높은 성능을 가능하게 합니다.  또한, **부분적인 해결책**에 대한 Q-값을 예측하는 기능은 효율적인 의사결정을 가능하게 하여, 제한된 감독 환경에서도 우수한 성능을 발휘합니다.  **정성적 분석**을 통해 QLASS의 효과적인 의사결정 능력을 추가적으로 확인하였습니다.  결론적으로, QLASS는 제한된 감독 하에서도 언어 에이전트의 추론 능력을 향상시키는 효과적인 방법임을 제시합니다.

#### Future Work
본 논문의 "향후 연구" 부분에 대한 심층적인 고찰은 **QLASS의 한계점을 극복하고, 성능을 더욱 향상시키기 위한 방향**을 제시해야 합니다.  **다양한 환경에서의 적용성 확대**를 위해 추가적인 실험이 필요하며, 특히 **데이터 효율성 개선** 및 **모델의 일반화 성능 향상**에 초점을 맞춰야 합니다.  **Q-value 추정의 정확도 향상**을 위한 새로운 방법론 연구와 **탐색 트리 생성 전략의 개선** 또한 중요한 과제입니다.  나아가, **다른 유형의 보상 모델**과의 통합 및 **다른 강화 학습 기법**과의 비교 분석을 통해 QLASS의 우수성을 더욱 명확히 밝힐 수 있습니다. 마지막으로, **실제 세계 문제에 대한 적용 가능성**을 검증하기 위한 실험과 **설명 가능성**을 높이기 위한 연구 또한 필요합니다. 이러한 노력들을 통해 QLASS가 다양한 분야에서 더욱 효과적으로 활용될 수 있도록 발전시킬 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.02584/x2.png)

> 🔼 그림 2는 탐색 트리 구성 과정을 보여주는 예시입니다. 회색 노드는 결과 보상이 0인 가지를 나타냅니다. 결과 보상이 0인 리프 노드가 감지되면 확장 중지 신호가 가지의 첫 번째 미확장 노드로 다시 전송됩니다. 녹색 노드는 결과 보상이 0이 아닌 가지에 있으며 계속 확장될 수 있습니다.  이 그림은 언어 에이전트가 환경을 탐색하고 의사 결정 트리를 생성하는 방법을 시각적으로 보여줍니다.  0이 아닌 보상을 받은 경로는 더 탐색하고, 0 보상을 받은 경로는 가지치기하여 효율적인 탐색을 수행합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Illustrative example of constructing a exploration tree. Grey nodes represent the branches with a zero outcome reward. Once the leaf node with a zero outcome reward is detected, a Stop expansion signal will be sent back to the first unexpanded node on the branch. Green nodes are on branches where zero outcome reward is not detected and can keep expanding.
> </details>



![](https://arxiv.org/html/2502.02584/x3.png)

> 🔼 그림 3은 추론 중에 생성된 경로에서 사용된 토큰 수를 x축으로 하여 서로 다른 검색 예산 하에서 QLASS와 Best-of-N의 성능을 비교한 그래프입니다. 각 테스트 집합의 모든 작업에 대해 평균을 낸 추론 중 생성된 경로에서 사용된 토큰 수를 나타냅니다. 이 그래프는 사용된 토큰 수가 증가함에 따라 두 방법 모두의 성능이 향상됨을 보여주지만, QLASS는 모든 검색 예산에서 Best-of-N보다 일관되게 더 나은 성능을 보여줍니다. 특히, Best-of-N은 360K 토큰에 도달하면 성능이 더 이상 향상되지 않지만, QLASS는 400K 토큰까지 계속해서 성능이 향상됩니다. 이를 통해 QLASS가 효율적인 추론 검색 방법임을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: QLASS and Best-of-N under different search budgets. The x-axis represents the number of tokens consumed by the trajectories generated during inference averaged on all the tasks in each test set.
> </details>



![](https://arxiv.org/html/2502.02584/x4.png)

> 🔼 이 그림은 서로 다른 세 가지 방법으로 생성된 자가 학습 기준 모델의 성능을 비교한 것입니다. 세 가지 방법 모두 2단계에서 생성된 동일한 탐색 트리를 사용하여 자가 학습 데이터 생성을 안내합니다.  각 방법은 다른 프로세스 보상 모델링 기법을 사용하며, 이를 통해 각 방법의 효과를 비교 분석할 수 있습니다.  세로줄무늬로 표시된 세 가지 방법은 각각 Q-값, 평균 보상, 그리고 보상 값을 프로세스 보상으로 사용합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Self-training baselines. The three methods marked with diagonal stripes leverage different process reward modeling based on the same exploration trees constructed in Stage 2 to guide self-training data generation.
> </details>



![](https://arxiv.org/html/2502.02584/x5.png)

> 🔼 그림 5는 ALFWorld 환경에서 QLASS와 SFT 기준 모델의 성능을 비교한 예시입니다. 왼쪽은 SFT 기준 모델의 행동을, 오른쪽은 QLASS의 행동을 보여줍니다. SFT 모델은 과제를 성공적으로 완료하지만 불필요한 행동(냉장고를 반복적으로 열고 닫는 행동)을 반복합니다. 반면에 QLASS는 단계별 보상 메커니즘을 통해 과제 달성 후 불필요한 행동을 하지 않고 효율적으로 과제를 완료합니다. 이는 QLASS가 단계별 보상 모델을 사용하여 더 효과적인 의사 결정을 내릴 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: One example on the ALFWorld, the right is QLASS and the left is the SFT baseline.
> </details>



![](https://arxiv.org/html/2502.02584/x6.png)

> 🔼 그림 6은 WebShop 환경에서 언어 에이전트에게 제공되는 지침 프롬프트를 보여줍니다.  이 프롬프트는 에이전트가 웹 쇼핑을 수행하는 동안 따라야 할 단계별 지침을 제공합니다.  에이전트는 주어진 관찰 결과와 지침을 바탕으로 행동을 결정해야 하며, 검색이나 클릭 가능한 버튼을 사용할 수 있습니다.  올바른 응답 형식은 `search[keywords]` 또는 `click[value]` 형식을 따라야 하며, 잘못된 동작은 아무것도 하지 않는 것으로 간주됩니다.  이 프롬프트는 에이전트가 효과적인 검색어를 만들고 올바른 형식을 사용하도록 안내하는 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: The instruction prompt provided to language agent on WebShop.
> </details>



![](https://arxiv.org/html/2502.02584/x7.png)

> 🔼 그림 7은 SciWorld 환경에서 언어 에이전트에게 제공되는 지침 프롬프트를 보여줍니다.  이 프롬프트는 에이전트가 과학 실험을 수행하기 위한 여러 가지 행동(예: 물체 열기, 닫기, 활성화, 비활성화, 연결, 분리, 사용, 둘러보기, 검사, 읽기, 옮기기, 집어 들기, 붓기, 섞기, 순간이동, 집중, 기다리기)을 설명합니다.  또한,  실험을 완료하기 위한 단계별 지침과 각 행동의 형식을 제시하여 에이전트가 환경과 상호 작용하고 과제를 완수할 수 있도록 안내합니다.  특히,  'lead를 끓이는' 과제에 대한 구체적인 설명이 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: The instruction prompt provided to language agent on SciWorld.
> </details>



![](https://arxiv.org/html/2502.02584/x8.png)

> 🔼 그림 8은 ALFWorld 환경에서 언어 에이전트에게 제공되는 지침 프롬프트를 보여줍니다. 이 프롬프트는 에이전트가 가정 환경에서 작업을 수행하는 역할을 하고 목표를 달성하기 위해 행동을 수행해야 함을 설명합니다. 프롬프트에는 현재 환경에 대한 설명과 달성해야 할 목표가 포함되어 있습니다. 또한, 에이전트는 매 턴마다 관찰 결과를 받고, 이를 기반으로 다음 행동을 계획하고 응답해야 합니다. 프롬프트는 허용되는 행동 목록과 응답 형식에 대한 지침도 제공합니다. 이러한 지침을 통해 언어 에이전트는 ALFWorld 환경 내에서 효과적으로 작업을 수행할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: The instruction prompt provided to language agent on ALFWorld.
> </details>



![](https://arxiv.org/html/2502.02584/x9.png)

> 🔼 그림 9는 본 논문에서 제안하는 QLASS 방법론의 일부인, 작업 묘사(task description)의 변형을 보여주는 예시입니다.  QLASS는 제한된 주석 데이터로도 효과적인 추론을 가능하게 하기 위해,  입력 질의를 여러 방식으로 바꿔서(paraphrasing) 모델의 일반화 능력을 높이는 기법을 사용합니다. 그림 9는 특정 향수를 구매하는 작업에 대해, 다양한 어구를 사용하여 동일한 의미를 표현하는 예시들을 보여줍니다. 이러한 변형된 질의들을 통해, 모델은 다양한 표현 방식에 대한 이해도를 높이고, 더욱 정확하고 견고한 결과를 도출할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: An illustrative example on task perturbation.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | WebShop | SciWorld Seen | SciWorld Unseen | ALFWorld Seen | ALFWorld Unseen |
|---|---|---|---|---|---| 
| GPT-4 | 63.2 | 64.8 | 64.4 | 42.9 | 38.1 |
| GPT-3.5-Turbo | 62.4 | 16.5 | 13.0 | 7.9 | 10.5 |
| Reflexion (Shinn et al., 2023) | 64.2 | 60.3 | 64.4 | 45.7 | 55.2 |
| Base Agent (Llama-2-7B-Chat) | 17.9 | 3.8 | 3.1 | 0.0 | 0.0 |
| SFT | 63.1 | 67.4 | 53.0 | 60.0 | 67.2 |
| RFT (Yuan et al., 2023) | 63.6 | 71.6 | 54.3 | 62.9 | 66.4 |
| PPO (Schulman et al., 2017) | 64.2 | 59.4 | 51.7 | 22.1 | 29.1 |
| Best-of-N | 67.9 | 70.2 | 57.6 | 62.1 | 69.4 |
| ETO (Song et al., 2024) | 67.4 | 73.8 | 65.0 | 68.6 | 72.4 |
| QCLASS | 70.3 | 75.3 | 66.4 | 77.9 | 82.8 |{{< /table-caption >}}
> 🔼 표 2는 WebShop, SciWorld, ALFWorld 세 가지 환경에서 다양한 기준모형들의 성능을 비교한 표입니다. 표는 크게 두 부분으로 나뉘는데, 첫 번째는 GPT-4와 같은 독점적 언어모델 기반 기준모형들의 결과를, 두 번째는 Llama-2-7B-Chat과 같은 공개된 언어모델 기반 기준모형들의 결과를 보여줍니다.  각 열에서 가장 좋은 결과는 굵은 글씨체로, 두 번째로 좋은 결과는 밑줄로 표시되어 있습니다.  ♠는 GPT-4o 기반 기준모형임을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Performance of all the baselines on WebShop, SciWorld and ALFWorld. The table is divided into two sections: the first presents the results of closed-source agents and the second includes open-sourced agents. ♠ indicates the baseline based on GPT-4o. In each column, the best result is bolded and the second-best result is underlined.111
> </details>

{{< table-caption >}}
| Method | WebShop | WebShop-1000 |
|---|---|---|
| SFT | 63.1 | 21.7 |
| ETO | 67.4 | 66.7 |
| Best-of-N | 67.9 | 47.1 |
| QLASS | 70.3 | 67.3 |{{< /table-caption >}}
> 🔼 이 표는 WebShop 데이터셋에서 1000개의 주석이 달린 궤적을 사용하여 학습된 다양한 모델들의 평균 보상을 비교한 것입니다.  행동 복제(Behavior Cloning) 단계에서 사용된 데이터의 양을 줄였을 때 각 모델의 성능을 평가하기 위한 실험 결과를 보여줍니다. 표의 각 열은 특정 모델의 평균 보상을 나타내며, 가장 높은 보상을 받은 모델은 굵게 표시되고, 두 번째로 높은 보상을 받은 모델은 밑줄이 그어져 있습니다. 이를 통해 제한된 데이터 환경에서도 QLASS가 강력한 성능을 유지하는지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Average reward comparison on WebShop with 1000 annotated trajectories for behavior cloning. The best result is bolded, and the second-best result is underlined.
> </details>

{{< table-caption >}}
| Base LLM | Method | SciWorld | SciWorld |
|---|---|---|---| 
|  |  | Seen | Unseen |
| Llama-2-13B | SFT | 68.1 | 57.6 |
| Llama-2-13B | ETO | 71.4 | 68.6 |
|  | QCLASS | 72.7 | 69.3 |{{< /table-caption >}}
> 🔼 표 4는 다양한 기반 언어 모델을 사용하여 SciWorld 환경에서 QLASS의 성능을 평가한 결과를 보여줍니다.  다른 크기의 언어 모델을 사용하여 실험했을 때, QLASS의 성능 변화를 확인할 수 있습니다.  특히, Llama-2-13B 와 같은 큰 모델에서도 QLASS가 기존 방법보다 우수한 성능을 유지하는지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: The performance on a different base LLM on SciWorld.
> </details>

{{< table-caption >}}
| Hyperparameter | Value |
|---|---| 
| Batch size | 64 |
| Number of training epochs | 3 |
| Weight decay | 0.0 |
| Warmup ratio | 0.03 |
| Learning rate | 1e-5 |
| LR scheduler type | Cosine |
| Logging steps | 5 |
| Model max length | 4096 |
| Discount factor γ | 0.9 |
| Maximum expansion depth D on WebShop | 3 |
| Maximum expansion depth D on SciWorld | 6 |
| Maximum expansion depth D on ALFWorld | 8 |
| Action candidate set size M for inference | 2 |
| Sampled trajectory number N for self-training | 1 |
| Exploration temperature | 0.7 |{{< /table-caption >}}
> 🔼 QLASS에서 사용된 하이퍼파라미터들을 정리한 표입니다. 배치 크기, 학습 에폭 수, 가중치 감쇠, 웜업 비율, 학습률, 학습률 스케줄러 유형, 로깅 단계, 모델 최대 길이, 할인율, WebShop, SciWorld, ALFWorld에 대한 최대 탐색 깊이, 추론을 위한 행동 후보 집합 크기, 자기 학습을 위한 샘플링된 궤적 수, 탐색 온도 등 다양한 하이퍼파라미터의 값을 보여줍니다. 이 표는 QLASS 모델의 성능에 영향을 미치는 요소들을 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Hyperparameters used in QLASS.
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