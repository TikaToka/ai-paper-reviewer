---
title: "rStar-Math: Small LLMs Can Master Math Reasoning with Self-Evolved Deep Thinking"
summary: "소규모 언어 모델이 자체 진화된 딥씽킹으로 수학 추론 능력을 획기적으로 향상시켰습니다!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Microsoft Research",]
showSummary: true
date: 2025-01-08
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.04519 {{< /keyword >}}
{{< keyword icon="writer" >}} Xinyu Guan et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-09 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.04519" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.04519" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/rstar-math-small-llms-can-master-math" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

최근 대규모 언어 모델(LLM)이 수학 문제 해결에 활용되고 있지만, 단일 추론으로는 오류 발생 가능성이 높고, 고품질의 훈련 데이터 확보가 어렵다는 문제가 있습니다. 특히, 중간 과정의 정확성을 평가하는 것은 어려운 과제입니다. 기존의 방법들은 상위 LLM에 의존하는 경우가 많아 소규모 모델을 이용한 수학 추론 성능 향상에는 한계가 있었습니다.

본 논문에서는 소규모 언어 모델(SLM)의 수학 추론 능력을 향상시키기 위해, MCTS(몬테 카를로 트리 탐색) 기반의 “딥 씽킹” 기법을 사용한 rStar-Math를 제안합니다. rStar-Math는 코드 증강 CoT 데이터 합성, 새로운 프로세스 보상 모델 훈련 방법, 그리고 자체 진화 과정을 통해 SLM의 수학 추론 성능을 획기적으로 향상시킵니다. 실험 결과, rStar-Math는 다양한 수학 문제 해결 과제에서 최첨단 성능을 달성하였으며, 특히 수학 경시대회 수준의 문제에서도 높은 정확도를 보였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 소규모 언어 모델(SLM)이 자체 진화를 통해 **최첨단 수학 추론 성능**을 달성 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} **코드 증강 CoT 데이터 합성 및 새로운 프로세스 보상 모델 훈련 기법** 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} **몬테 카를로 트리 탐색(MCTS)** 기반 딥씽킹을 통한 효과적인 추론 과정 구현 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **소규모 언어 모델(SLM)**을 사용하여 수학 추론 능력을 크게 향상시키는 새로운 방법을 제시함으로써, **수학적 문제 해결 분야의 연구**에 중요한 의미를 지닙니다.  **자체 진화 기법**을 통해 고품질 훈련 데이터를 생성하고, **새로운 프로세스 보상 모델 훈련 방법**을 제시하여 기존의 한계를 극복합니다. 이는 **대규모 언어 모델에 의존하지 않고**도 최첨단 성능을 달성할 수 있음을 보여주는 중요한 결과입니다. 본 연구는 **새로운 연구 방향**을 제시하고, 향후 수학 추론 분야의 발전에 크게 기여할 것으로 기대됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.04519/x1.png)

> 🔼 그림 1은 논문에서 제시하는 rStar-Math 시스템의 개요를 보여줍니다.  (a)는 MCTS(Monte Carlo Tree Search) 기반의 깊이 있는 추론 과정을 단계별로 검증된 추론 경로로 나타낸 것입니다.  각 단계는 SLM(Small Language Model) 기반의 정책 모델에 의해 생성되고, PPM(Process Preference Model) 기반의 보상 모델에 의해 평가됩니다. (b)는 Q-값(Q-value)에 기반하여 단계별 선호도 쌍을 구성하는 방법을 보여줍니다.  정확한 단계에는 높은 Q-값이, 잘못된 단계에는 낮은 Q-값이 할당되어 PPM 훈련에 사용됩니다.  (c)는 정책 SLM과 PPM을 처음부터 반복적으로 개선하는 4단계 자기 진화 과정을 보여줍니다. 각 라운드마다 MCTS를 통해 점점 더 높은 품질의 훈련 데이터를 생성하여 다음 라운드의 모델을 개선하는 과정을 반복합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: The overview of \sysname.
> </details>





{{< table-caption >}}
| Task | rStar-Math (Qwen-7B) | rStar-Math (Qwen-1.5B) | rStar-Math (Phi3-mini) | OpenAI o1-preview | OpenAI o1-mini | QWQ 32B-preview | GPT-4o | DeepSeek-V3 |
|---|---|---|---|---|---|---|---|---|
| MATH | 90.0 | 88.6 | 86.4 | 85.5 | 90.0 | 90.6 | 76.6 | 90.2 |
| AIME 2024 | 53.3 | 46.7 | 43.3 | 44.6 | 56.7 | 50.0 | 9.3 | 39.2 |
| Olympiad Bench | 65.6 | 64.6 | 60.3 | - | 65.3 | 61.2 | 43.3 | 55.4 |
| College Math | 60.5 | 59.3 | 59.1 | - | 57.8 | 55.8 | 48.5 | 58.9 |
| Omni-Math | 50.5 | 48.5 | 46.0 | 52.5 | 60.5 | 49.6 | 30.5 | 35.9 |{{< /table-caption >}}

> 🔼 표 1은 rStar-Math 모델이 64개의 시뮬레이션 경로를 통해 심층적 사고 과정을 거쳐 작은 언어 모델(SLM)의 수학적 추론 능력을 최첨단 수준으로 끌어올렸다는 것을 보여줍니다.  이 표는 다양한 수학 문제 해결 과제(MATH, AIΜΕ 2024, Olympiad Bench, College Math, Omni-Math)에서 rStar-Math를 적용했을 때의 성능을 보여주는 다양한 모델의 정확도(pass@1)를 비교하여, SLM의 성능 향상을 구체적으로 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: \sysname enables frontier math reasoning in SLMs via deep thinking over 64 trajectories.
> </details>





### In-depth insights


#### Small LLM Math
소형 LLM을 이용한 수학 문제 해결 능력 향상에 대한 연구는 **매우 중요한 의미**를 지닙니다.  대규모 언어 모델(LLM)의 성능이 뛰어나지만, 계산 비용 및 자원 제약으로 인해 소형 LLM의 활용이 더욱 중요해지고 있으며, **소형 LLM의 효율성 및 성능 개선**은 다양한 분야에 적용 가능하기 때문입니다.  본 연구는 소형 LLM이 스스로 진화하는 깊이 있는 사고 과정을 통해 복잡한 수학적 추론 능력을 향상시킬 수 있음을 보여줍니다.  **Monte Carlo Tree Search (MCTS)** 기법을 사용하여 효율적인 탐색 전략을 구현했으며, **코드 기반의 증명 방법**을 도입하여 추론 과정의 정확성을 높였습니다.  또한, **단계별 보상 모델 훈련 기법**을 통해 효과적인 학습을 가능하게 하였습니다.  **자기 진화적 접근 방식**을 통해 소형 LLM의 수학 문제 해결 능력을 꾸준히 향상시켰다는 점이 인상적이며, 향후 다양한 응용 분야에서 소형 LLM의 활용 가능성을 높일 수 있을 것으로 기대됩니다. 특히, 경쟁 수준의 수학 문제 해결 능력을 보여준 것은 **고무적인 결과**입니다.

#### Deep Thinking MCTS
본 논문에서 제시된 "Deep Thinking MCTS"는 **몬테 카를로 트리 탐색(MCTS)** 알고리즘을 기반으로 한 심층적 추론 과정을 의미합니다.  기존의 단순한 언어 모델 기반 답변 생성 방식과 달리, **다단계 추론 과정을 거쳐 문제 해결에 도달**합니다.  각 단계마다 언어 모델이 후보 답안을 생성하고, 보상 모델이 해당 답안의 질을 평가하여 최적의 경로를 선택하는 방식입니다.  이는 **인간의 심층적 사고 과정을 모방**한 것으로, 복잡한 수학 문제 해결에 효과적입니다.  **자체 진화 과정을 통해 정책 모델과 보상 모델의 성능이 향상**되며, 이는 고품질의 훈련 데이터를 자체적으로 생성하는 능력으로 이어집니다. 결과적으로, 작은 크기의 언어 모델이라도 MCTS 기반 심층적 사고를 통해 큰 모델에 버금가는 수학 추론 능력을 달성할 수 있음을 보여줍니다.  **코드 실행 검증을 통한 정확도 향상**은 또 다른 중요한 특징입니다.**

#### Self-Evolved System
자기 진화 시스템은 **반복적인 자기 개선**을 통해 성능을 향상시키는 시스템입니다. 이는 초기 모델의 한계를 극복하고, 데이터 부족 문제를 해결하며, **더욱 복잡한 문제**에 대한 해결 능력을 키우는 데 효과적입니다. **데이터 생성, 모델 학습, 성능 평가**의 과정이 순환적으로 반복되면서 시스템은 점진적으로 발전합니다.  **MCTS(몬테 카를로 트리 탐색)** 기반의 자기 진화는 효율적인 탐색과 고품질 데이터 생성을 가능하게 하며, 이는 **정책 모델과 보상 모델의 상호 작용**을 통해 이루어집니다.  하지만 이러한 시스템은 **계산 비용이 높고, 자기 진화 과정의 안정성**을 확보하는 것이 중요한 과제입니다.  **초기 모델의 성능**이 자기 진화의 성공 여부에 큰 영향을 미치며, **자기 진화의 횟수와 데이터의 품질** 또한 성능에 중요한 요소로 작용합니다.  **최종적으로 목표하는 성능**에 따라 자기 진화 시스템의 설계 및 구현 방식이 달라질 수 있습니다.

#### Process Reward Model
본 논문에서 제시된 '프로세스 보상 모델(Process Reward Model)'은 **중간 단계의 추론 과정의 질을 평가**하는 데 초점을 맞춘 핵심 구성 요소입니다. 단순히 최종 답변의 정확성만 평가하는 기존 방식과 달리, **각 단계별 추론의 타당성**을 평가하여 더욱 정교한 피드백을 제공합니다. 이를 통해 모델은 단순히 정답을 맞추는 것뿐 아니라, **문제 해결 과정 자체의 논리적 정합성**을 향상시킬 수 있습니다.  **단계별 점수 레이블링의 어려움을 해결하기 위한 혁신적인 방법**을 제시하며, 이는 **자동화된 평가 시스템** 구축에 중요한 기여를 합니다.  **자체 진화 과정**에서 프로세스 보상 모델은 정책 모델과 상호 작용하며, 지속적인 개선을 통해 더욱 효과적이고 정확한 추론 과정을 가능하게 합니다.  **정책 모델과의 상호 작용**을 통해, 단계별 추론의 질을 높이고, 궁극적으로 복잡한 수학 문제 해결 능력을 향상시키는 데 기여하는 것입니다.

#### Future of Reasoning
추론의 미래는 **대규모 언어 모델(LLM)**의 급속한 발전과 함께 크게 달라질 것입니다.  본 논문에서 제시된 자기 진화적 딥씽킹 기법처럼, **LLM의 한계를 극복하고 추론 능력을 향상시키는 새로운 방법론**이 지속적으로 개발될 것입니다.  **계산 비용 최소화**와 **데이터 효율성 극대화**를 위한 연구가 활발해질 것이며,  **상징적 추론**과 **비상징적 추론**의 통합을 통해 인간 수준의 추론 능력에 더욱 가까워질 것입니다.  특히, **과학적 발견, 의학적 진단, 법률적 판단** 등 복잡한 문제 해결에 **LLM 기반의 강력한 추론 시스템**이 광범위하게 적용될 것으로 예상됩니다.  하지만, **LLM의 윤리적 문제와 편향성**에 대한 우려 또한 해결해야 할 과제이며, **신뢰할 수 있고 투명한 추론 시스템** 구축을 위한 노력이 필수적입니다.  궁극적으로, 추론의 미래는 **인간과 AI의 협력적 지능**을 통해 더욱 발전된 사회를 만드는 데 기여할 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.04519/x2.png)

> 🔼 그림 2는 코드 증강형 CoT(Chain-of-Thought)의 예시를 보여줍니다.  수학 문제에 대한 풀이 과정을 자연어(NL, Natural Language)로 설명하는 것과 동시에, 그 과정을 파이썬 코드로 구현하여 실행 가능하도록 합니다. 이를 통해 단순히 정답만 맞추는 것이 아니라, 단계별 추론 과정의 정확성을 검증하고, 잘못된 중간 단계를 걸러낼 수 있습니다.  파이썬 코드는 자연어 설명을 주석으로 포함하여 코드의 각 단계가 어떤 추론 과정에 해당하는지 명확하게 나타냅니다.  코드가 성공적으로 실행되면 그 단계가 유효한 것으로 간주됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: An example of Code-augmented CoT.
> </details>



![](https://arxiv.org/html/2501.04519/extracted/6117756/scalinglaws.png)

> 🔼 본 그림은 테스트 시간 계산을 확장하여 추론 성능을 보여줍니다.  MATH, AIME 2024, Olympiad Bench, College Math 네 가지 벤치마크에 대해, 샘플링된 솔루션의 수(1, 2, 4, 8, 16, 32, 64)가 증가함에 따라 각 모델(OpenAI의 o1-preview 및 o1-mini, 그리고 제안된 rStar-Math 모델)의 정확도를 보여줍니다.  이를 통해 테스트 시간 계산을 늘림으로써 모델의 추론 능력이 향상되는 것을 확인할 수 있으며, 특히 rStar-Math 모델의 성능 향상이 두드러짐을 보여줍니다. 각 벤치마크별로 모델의 정확도 변화 추세를 비교 분석하여 rStar-Math의 효율성과 강점을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Reasoning performance under scaling up the test-time compute.
> </details>



![](https://arxiv.org/html/2501.04519/x3.png)

> 🔼  그림 4는 rStar-Math의 심층 사고 과정에서 보이는 내재적 자기 반성의 한 예시를 보여줍니다.  문제 풀이 과정에서 모델이 초기에 잘못된 방향으로 접근했지만,  자체적으로 이를 인지하고 수정하는 모습을 보여줍니다.  잘못된 방향으로 진행된 단계들은 낮은 PPM 점수를 받았고, 모델은 이를 통해 더 효율적인 해결책을 찾습니다.  이 과정에서 모델이 단순히 정답을 도출하는 것을 넘어,  문제 해결 과정에 대한 자기 평가 및 수정 능력을 가지고 있음을 시사합니다. 이는 단순히 정답을 맞추는 것을 넘어,  인간의 문제 해결 과정과 유사한 사고 과정을 모방하고 있음을 보여주는 중요한 증거입니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: An example of intrinsic self-reflection during \sysname deep thinking.
> </details>



![](https://arxiv.org/html/2501.04519/extracted/6117756/ppm_study.png)

> 🔼 그림 5는 다양한 보상 모델을 사용하여 시스템 2 추론을 적용하기 전과 후의 정책 모델의 Pass@1 정확도를 보여줍니다. 이 그림은 보상 모델이 최종 성능을 주로 결정한다는 것을 보여줍니다. 시스템 2 추론을 적용한 후 정확도가 크게 향상되었으며, 보상 모델의 중요성을 강조합니다.  다양한 크기의 정책 모델에 대한 결과가 제시되어 있으며, 보상 모델의 영향이 모델 크기에 따라 다르게 나타납니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Pass@1 accuracy of policy models and their accuracy after applying System 2 reasoning with various reward models, shows that reward models primarily determine the final performance.
> </details>



![](https://arxiv.org/html/2501.04519/extracted/6117756/passnrandom.png)

> 🔼 그림 6은 다양한 정책 모델에서 무작위 샘플링을 사용한 Pass@N 정확도를 보여줍니다. 공식적인 Qwen 지시 버전과 비교하여 본 논문의 정책 모델이 정답을 샘플링하는 능력이 더 뛰어남을 보여줍니다.  Pass@N은 모델이 N개의 솔루션을 생성하고 그 중 하나라도 정답이면 정답으로 간주하는 지표입니다. 이 그래프는 다양한 크기의 모델과 다양한 문제 유형에서 모델의 성능을 비교하여, 본 논문의 정책 모델이 무작위 샘플링보다 정답을 생성할 확률이 높다는 것을 시각적으로 보여줍니다.  특히, 샘플 수가 증가함에 따라 본 논문의 모델이 더욱 정확도가 높아짐을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Pass@N accuracy with random sampling from different policy models. Compared to the official Qwen instruct version, our policy model exhibits a stronger ability to sample correct solutions.
> </details>



![](https://arxiv.org/html/2501.04519/extracted/6117756/passnmcts.png)

> 🔼 그림 7은 PPM으로 개선된 MCTS를 사용한 Pass@N 정확도를 보여줍니다.  여러 크기의 정책 모델이 동일한 PPM 가이드라인 하에서 올바른 솔루션을 샘플링하는 능력이 수렴함을 보여줍니다.  즉, 모델의 크기가 달라도 PPM이라는 동일한 보상 모델을 사용하면 올바른 답을 도출하는 데 있어 성능이 유사해짐을 시각적으로 나타냅니다.  Pass@N은 N개의 솔루션 중 적어도 하나가 정답이면 정답으로 간주하는 지표입니다.  이 그래프는 모델 크기의 차이에도 불구하고,  PPM이라는 보상 메커니즘이 정확한 추론 과정을 유도하는 데 효과적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Pass@N accuracy with PPM-augmented MCTS. Under the same PPM guidance, the four policy models of varying sizes demonstrate convergent capabilities in sampling correct solutions.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| # | models in MCTS | GSM-level | MATH-level | Olympiad-level | All |
|---|---|---|---|---|---| 
| Round 1 | DeepSeek-Coder-V2-Instruct | 96.61% | 67.36% | 20.99% | 60.17% |
| Round 2 | policy SLM-r1 | 97.88% | 67.40% | 56.04% | 66.60% |
| Round 3 | policy SLM-r2, PPM-r2 | 98.15% | 88.69% | 62.16% | 77.86% |
| Round 4 | policy SLM-r3, PPM-r3 | 98.15% | 94.53% | 80.58% | 90.25% |{{< /table-caption >}}
> 🔼 표 2는 4회의 자기 진화 과정을 거친 후 각 라운드에서 정답이 있는 747,000개의 수학 문제 중 정확하게 풀린 문제의 비율을 보여줍니다.  첫 번째 라운드에서는 DeepSeek-Coder-Instruct 모델이 정책 LLM으로 사용되었고, 이후 라운드에서는 미세 조정된 7B 정책 SLM이 사용되었습니다. 이 표는 모델의 성능 향상을 보여주는 자기 진화 과정의 효과를 보여주는 중요한 지표입니다.  각 라운드별로 GSM 레벨, MATH 레벨, 올림피아드 레벨 문제에 대한 정확도를 개별적으로 제시하여 세부적인 성능 분석에 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Percentage of the 747k math problems correctly solved in each round. Only problems have correct solutions are included in the training set. The first round uses DeepSeek-Coder-Instruct as the policy LLM, while later rounds use our fine-tuned 7B policy SLM.
> </details>

{{< table-caption >}}
| Round# | MATH | AIME 2024 | AMC 2023 | Olympiad Bench | College Math | GSM8K | GaokaoEn 2023 |
|---|---|---|---|---|---|---|---| 
| DeepSeek-Coder-V2-Instruct (bootstrap model) | 75.3 | 13.3 | 57.5 | 37.6 | 46.2 | 94.9 | 64.7 |
| Base (Qwen2.5-Math-7B) | 58.8 | 0.0 | 22.5 | 21.8 | 41.6 | 91.6 | 51.7 |
| policy SLM-r1 | 69.6 | 3.3 | 30.0 | 34.7 | 44.5 | 88.4 | 57.4 |
| policy SLM-r2 | 73.6 | 10.0 | 35.0 | 39.0 | 45.7 | 89.1 | 59.7 |
| policy SLM-r3 | 75.8 | 16.7 | 45.0 | 44.1 | 49.6 | 89.3 | 62.8 |
| policy SLM-r4 | 78.4 | 26.7 | 47.5 | 47.1 | 52.5 | 89.7 | 65.7 |{{< /table-caption >}}
> 🔼 표 3은 rStar-Math 모델의 자기 진화 과정에서 각 라운드별로 도출된 정책 SLM의 Pass@1 정확도를 보여줍니다.  각 라운드마다 정책 SLM과 PPM이 향상되면서 성능이 지속적으로 개선되는 것을 확인할 수 있으며, 최종적으로는 초기 부트스트랩 모델을 능가하는 성능을 달성합니다.  이는 rStar-Math의 자기 진화 과정이 효과적임을 보여주는 증거입니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Pass@1 accuracy of the resulting policy SLM in each round, showing continuous improvement until surpassing the bootstrap model.
> </details>

{{< table-caption >}}
| Round# | MATH | AIME 2024 | AMC 2023 | Olympiad Bench | College Math | GSM8K | GaokaoEn 2023 |
|---|---|---|---|---|---|---|---| 
| PPM-r1 | 75.2 | 10.0 | 57.5 | 35.7 | 45.4 | 90.9 | 60.3 |
| PPM-r2 | 84.1 | 26.7 | 75.0 | 52.7 | 54.2 | 93.3 | 73.0 |
| PPM-r3 | 85.2 | 33.3 | 77.5 | 59.5 | 55.6 | 93.9 | 76.6 |
| PPM-r4 | 87.0 | 43.3 | 77.5 | 61.5 | 56.8 | 94.2 | 77.8 |{{< /table-caption >}}
> 🔼 표 4는 PPM의 성능이 반복 학습을 통해 지속적으로 향상됨을 보여줍니다. 공정한 비교를 위해 정책 모델은 SLM-r1로 고정되었습니다.  각 라운드에서의 MATH, AIME 2024, AMC 2023, Olympiad Bench, College Math, GSM8K, GaokaoEn 2023 데이터셋에 대한 PPM의 정확도(Pass@1)를 보여줍니다.  이를 통해 PPM의 성능 향상이 반복 학습에 따라 어떻게 개선되는지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: The quality of PPM consistently improves across rounds. The policy model has been fixed with policy SLM-r1 for a fair comparison.
> </details>

{{< table-caption >}}
| Model | Method | MATH | AIME 2024 | AMC 2023 | Olympiad Bench | College Math | GSM8K | Gaokao En 2023 |
|---|---|---|---|---|---|---|---|---|
| *Frontier LLMs* |  |  |  |  |  |  |  |  |
| GPT-4o | System 1 | 76.6 | 9.3 | 47.5 | 43.3 | 48.5 | 92.9 | 67.5 |
| Claude3.5-Sonnet | System 1 | 78.3 | 16.0 | - | - | - | 96.4 | - |
| GPT-o1-preview | - | 85.5 | 44.6 | 90.0 | - | - | - | - |
| GPT-o1-mini | - | **90.0** | **56.7** | **95.0** | **65.3** | 57.8 | 94.8 | 78.4 |
| *Open-Sourced Reasoning LLMs* |  |  |  |  |  |  |  |  |
| DeepSeek-Coder-V2-Instruct | System 1 | 75.3 | 13.3 | 57.5 | 37.6 | 46.2 | 94.9 | 64.7 |
| Mathstral-7B-v0.1 | System 1 | 57.8 | 0.0 | 37.5 | 21.5 | 33.7 | 84.9 | 46.0 |
| NuminaMath-72B-CoT | System 1 | 64.0 | 3.3 | 70.0 | 32.6 | 39.7 | 90.8 | 58.4 |
| LLaMA3.1-8B-Instruct | System 1 | 51.4 | 6.7 | 25.0 | 15.4 | 33.8 | 76.6 | 38.4 |
| LLaMA3.1-70B-Instruct | System 1 | 65.4 | 23.3 | 50.0 | 27.7 | 42.5 | 94.1 | 54.0 |
| Qwen2.5-Math-72B-Instruct | System 1 | 85.6 | 30.0 | 70.0 | 49.0 | 49.5 | 95.9 | 71.9 |
| Qwen2.5-Math-72B-Instruct+72B ORM | System 2 | 85.8 | 36.7 | 72.5 | 54.5 | 50.6 | 96.4 | 76.9 |
| *General Base Model: Phi3-mini-Instruct (3.8B)* |  |  |  |  |  |  |  |  |
| Phi3-mini-Instruct (base model) | System 1 | 41.4 | 3.33 | 7.5 | 12.3 | 33.1 | 85.7 | 37.1 |
| \sysname **(3.8B SLM+7B PPM)** | System 2 | **85.4** | **40.0** | **77.5** | **59.3** | **58.0** | **94.5** | **77.1** |
| \sysname<sup>*64*</sup> **(3.8B SLM+7B PPM)** | System 2 | **86.4** | **43.3** | **80.0** | **60.3** | **59.1** | **94.7** | **77.7** |
| *Math-Specialized Base Model: Qwen2.5-Math-1.5B* |  |  |  |  |  |  |  |  |
| Qwen2.5-Math-1.5B (base model) | System 1 | 51.2 | 0.0 | 22.5 | 16.7 | 38.4 | 74.6 | 46.5 |
| Qwen2.5-Math-1.5B-Instruct | System 1 | 60.0 | 10.0 | 60.0 | 38.1 | 47.7 | 84.8 | 65.5 |
| Qwen2.5-Math-1.5B-Instruct+72B ORM | System 2 | 83.4 | 20.0 | 72.5 | 47.3 | 50.2 | 94.1 | 73.0 |
| \sysname **(1.5B SLM+7B PPM)** | System 2 | **87.8** | **46.7** | **80.0** | **63.5** | **59.0** | **94.3** | **77.7** |
| \sysname<sup>*64*</sup> **(1.5B SLM+7B PPM)** | System 2 | **88.6** | **46.7** | **85.0** | **64.6** | **59.3** | **94.8** | **79.5** |
| *Math-Specialized Base Model: Qwen2.5-Math-7B* |  |  |  |  |  |  |  |  |
| Qwen2.5-Math-7B (base model) | System 1 | 53.4 | 3.3 | 25.0 | 17.3 | 39.4 | 80.4 | 47.3 |
| Qwen2.5-Math-7B-Instruct | System 1 | 73.2 | 13.3 | 62.5 | 38.2 | 45.9 | 89.9 | 62.1 |
| Qwen2.5-Math-7B-Instruct+72B ORM | System 2 | 83.4 | 23.3 | 62.5 | 47.6 | 47.9 | **95.1** | 71.9 |
| \sysname **(7B SLM+7B PPM)** | System 2 | **88.2** | **43.3** | **80.0** | **63.1** | **58.4** | 94.6 | **78.2** |
| \sysname<sup>*64*</sup> **(7B SLM+7B PPM)** | System 2 | **88.6** | **46.7** | **85.0** | **63.4** | **59.3** | 94.8 | **79.2** |
| Competition and College Level |  | MATH | AIME 2024 | AMC 2023 | Olympiad | College Math | GSM8K | Gaokao |
|---|---|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  | OOD |  |{{< /table-caption >}}
> 🔼 표 5는 rStar-Math를 포함한 최첨단 언어 모델들이 가장 어려운 수학 벤치마크에서 달성한 성능을 보여줍니다.  rStar-Math는 64개의 시뮬레이션 결과를 샘플링하여 얻은 정확도(Pass@1)를    rStar-Math64로 표시했습니다. 표에는 다양한 벤치마크(MATH, AIME 2024, AMC 2023, Olympiad Bench, College Math, GSM8K, GaokaoEn 2023)에 대한 각 모델의 Pass@1 정확도가 포함되어 있습니다.  이 표는 rStar-Math의 성능을 다른 최첨단 모델과 비교하여 rStar-Math의 우수성을 보여주는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 5: The results of \sysname and other frontier LLMs on the most challenging math benchmarks. \sysname64 shows the Pass@1 accuracy achieved when sampling 64 trajectories.
> </details>

{{< table-caption >}}
| Round# | MATH | AIME 2024 | AMC 2023 | Olympiad Bench | College Math | GSM8K | GaokaoEn 2023 |
|---|---|---|---|---|---|---|---| 
| GPT-4o | 76.6 | 9.3 | 47.5 | 43.3 | 48.5 | 92.9 | 67.5 |
| Base 7B model | 58.8 | 0.0 | 22.5 | 21.8 | 41.6 | 91.6 | 51.7 |
| Round 1 | 75.2 | 10.0 | 57.5 | 35.7 | 45.4 | 90.9 | 60.3 |
| Round 2 | 86.6 | 43.3 | 75.0 | 59.4 | 55.6 | 94.0 | 76.4 |
| Round 3 | 87.0 | 46.7 | 80.0 | 61.6 | 56.5 | 94.2 | 77.1 |
| Round 4 | 89.4 | 50.0 | 87.5 | 65.3 | 59.0 | 95.0 | 80.5 |{{< /table-caption >}}
> 🔼 표 6은 rStar-Math의 자기 진화적 심층 사고 과정을 보여줍니다. 4라운드의 자기 진화를 거치면서, rStar-Math는 수학 추론 능력이 지속적으로 향상되는 것을 확인할 수 있습니다. 특히 2라운드부터는 7B 기본 모델의 성능이 GPT-4o를 능가하는 것을 알 수 있습니다. 이 표는 MATH, AIME 2024, AMC 2023, Olympiad Bench, College Math, GSM8K, GaokaoEn 2023 등 다양한 수학 벤치마크에서 각 라운드별 성능을 비교 분석하여 rStar-Math의 효과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 6: The continuously improved math reasoning capabilities through \sysname self-evolved deep thinking. Starting from round 2, the 7B base model powered by \sysname surpasses GPT-4o.
> </details>

{{< table-caption >}}
| Dataset | MATH | AIME | AMC | Olympiad Bench | College Math | GSM8K | GaokaoEn 2023 |
|---|---|---|---|---|---|---|---| 
| GPT-4o | - | 76.6 | 9.3 | 47.5 | 43.3 | 48.5 | **92.9** | **67.5** |
| GPT4-distillation (Open-sourced) | MetaMath | 55.2 | 3.33 | 32.5 | 19.1 | 39.2 | 85.1 | 43.6 |
| NuminaMath-CoT | 69.6 | 10.0 | **50.0** | 37.2 | 43.4 | 89.8 | 59.5 |
| Self-generation by policy SLM-r3 | Random sample | 72.4 | 10.0 | 45.0 | 41.0 | 48.0 | 87.5 | 57.1 |
|  | Rejection sampling | 73.4 | 13.3 | 47.5 | 44.7 | 50.8 | 89.3 | 61.7 |
| Step-by-step verified (ours) | **78.4** | **26.7** | 47.5 | **47.1** | **52.5** | 89.7 | 65.7 |{{< /table-caption >}}
> 🔼 표 7은 단계별로 검증된 추론 경로의 효과를 평가하기 위한 실험 결과를 보여줍니다.  본 논문에서는  Qwen2.5-Math-7B 모델을 다양한 데이터셋으로 미세 조정하여  수학 추론 성능을 비교 분석했습니다.  표에는 MATH, AIME, AMC, Olympiad Bench, College Math, GSM8K, GaokaoEn 등 다양한 수학 문제 벤치마크에 대한 정확도(Pass@1)가 제시되어 있습니다. 각 데이터셋은 서로 다른 방식으로 생성되었으며,  본 논문에서 제시하는 단계별 검증된 추론 경로를 사용한 데이터셋의 우수성을 보여주고자 합니다.  이를 통해,  단계별 검증된 추론 경로 데이터셋이 Qwen2.5-Math-7B 모델의 수학 추론 능력 향상에 얼마나 효과적인지를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Ablation study on the effectiveness of our step-by-step verified reasoning trajectories as the SFT dataset. We report the SFT accuracy of Qwen2.5-Math-7B fine-tuned with different datasets.
> </details>

{{< table-caption >}}
| RM | Inference | MATH | AIME | AMC | Olympiad Bench | College Math | GSM8K | GaokaoEn |
|---|---|---|---|---|---|---|---|---|
| o1-mini | - | 90.0 | 56.7 | 95.0 | 65.3 | 55.6 | 94.8 | 78.6 |
| ORM | Best-of-N | 82.6 | 26.7 | 65.0 | 55.1 | 55.5 | 92.3 | 72.5 |
| PQM | MCTS | 88.2 | 46.7 | 85.0 | 62.9 | 57.6 | 94.6 | 79.5 |
| PPM | MCTS | 89.4 | 50.0 | 87.5 | 65.3 | 59.0 | 95.0 | 80.5 |{{< /table-caption >}}
> 🔼 표 8은 보상 모델에 대한 추가 분석 결과를 보여줍니다.  단순히 결과(Outcome)만을 보상으로 사용하는 ORM(Outcome Reward Model)과 중간 과정(Process)의 점수를 보상으로 사용하는 PQM(Process Reward Model), PPM(Process Preference Model) 세 가지 방법을 비교합니다. 그 결과, 중간 과정의 점수를 활용하는 PQM과 PPM이 ORM보다 성능이 우수하며, 특히 PPM이 수학 추론 능력의 최첨단을 이끌고 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Ablation study on the reward model. Process reward models (PQM and PPM) outperform ORM, with PPM pushing the frontier of math reasoning capabilities.
> </details>

{{< table-caption >}}
| MATH | AIME 2024 | AMC 2023 | Olympiad Bench | College Math | GSM8K | GaokaoEn 2023 |
|---|---|---|---|---|---|---|
| 5453 | 15693 | 14544 | 7889 | 4503 | 3299 | 6375 |{{< /table-caption >}}
> 🔼 표 9는 rStar-Math 모델이 주어진 질문에 대한 답을 생성하기 위해 생성해야 하는 토큰의 평균 개수를 보여줍니다.  각 질문 유형(MATH, AIME 2024, AMC 2023, Olympiad Bench, College Math, GSM8K, GaokaoEn 2023)에 대해 생성된 토큰의 평균 수를 제시하여, rStar-Math 모델의 추론 비용을 평가하는 데 도움을 줍니다.  이를 통해 각 문제 유형에 따른 모델의 계산 복잡도와 자원 소모량을 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Inference costs of \sysname. We show the average number of generated tokens required to generate a trajectory for a given question.
> </details>

{{< table-caption >}}
| Model | MATH | AIME 2024 | AMC 2023 | Olympiad Bench | College Math | GSM8K | GaokaoEn 2023 |
|---|---|---|---|---|---|---|---| 
| *General Base Model: Phi3-mini-Instruct (3.8B)* |  |  |  |  |  |  |  |
| Phi3-mini-Instruct | 41.4 | 3.33 | 7.5 | 12.3 | 33.1 | 85.7 | 37.1 |
| **Our policy model** | **68.0** | **10.0** | **37.5** | **36.6** | **48.7** | **87.9** | **53.2** |
| *Math-Specialized Base Model: Qwen2.5-Math-1.5B* |  |  |  |  |  |  |  |
| Qwen2.5-Math-1.5B | 51.2 | 0.0 | 22.5 | 16.7 | 38.4 | 74.6 | 46.5 |
| Qwen2.5-Math-1.5B-Instruct | 60.0 | 10.0 | **60.0** | 38.1 | 47.7 | **84.8** | 65.5 |
| **Our policy model** | **74.8** | **13.3** | 47.5 | **42.5** | **50.1** | 83.1 | **58.7** |
| *Math-Specialized Base Model: Qwen2-Math-7B* |  |  |  |  |  |  |  |
| Qwen2-Math-7B | 53.4 | 3.3 | 25.0 | 17.3 | 39.4 | 80.4 | 47.3 |
| Qwen2-Math-7B-Instruct | 73.2 | 13.3 | **62.5** | 38.2 | 45.9 | **89.9** | 62.1 |
| **Our policy model** | **73.8** | **16.7** | 45.0 | **43.9** | **52.0** | 88.3 | **65.2** |
| *Math-Specialized Base Model: Qwen2.5-Math-7B* |  |  |  |  |  |  |  |
| Qwen2.5-Math-7B | 58.8 | 0.0 | 22.5 | 21.8 | 41.6 | 91.6 | 51.7 |
| Qwen2.5-Math-7B-Instruct | **82.6** | 6.0 | **62.5** | 41.6 | 46.8 | **95.2** | **66.8** |
| **Our policy model** | 78.4 | **26.7** | 47.5 | **47.1** | **52.5** | 89.7 | 65.7 |{{< /table-caption >}}
> 🔼 표 10은 본 논문에서 제안하는 방법으로 미세 조정된 정책 모델들의 Pass@1 정확도를 보여줍니다.  Pass@1 정확도는 모델이 정답을 처음 제시했을 때의 정확도를 나타냅니다. 표에는 세 가지 크기의 언어 모델 (Phi3-mini, Qwen2.5-Math-1.5B, Qwen2-Math-7B, Qwen2.5-Math-7B)에 대한 Pass@1 정확도가 다양한 수학적 벤치마크에 대해 제시되어 있습니다.  각 모델의 기본 성능과 본 논문에서 제안하는 방법을 적용한 후의 성능을 비교하여, 제안하는 방법의 효과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Pass@1 (greedy) accuracy of our fine-tuned policy models for Phi3-mini, Qwen2.5-Math-1.5B, Qwen2-Math-7B and Qwen2.5-Math-7B.
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