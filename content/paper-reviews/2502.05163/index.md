---
title: "DuoGuard: A Two-Player RL-Driven Framework for Multilingual LLM Guardrails"
summary: "DuoGuard: 적대적 생성 및 가드레일 모델을 동시에 학습시키는 2인용 강화학습 기반의 다국어 LLM 안전 시스템"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 UC Los Angeles",]
showSummary: true
date: 2025-02-07
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.05163 {{< /keyword >}}
{{< keyword icon="writer" >}} Yihe Deng et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-10 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.05163" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.05163" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/duoguard-a-two-player-rl-driven-framework-for" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)의 급속한 발전으로 인해, 특히 안전하지 않거나 불법적인 콘텐츠를 감지하는 측면에서 책임감 있는 사용을 보장하기 위한 가드레일 모델의 필요성이 증가했습니다. 하지만, 다른 언어에 대한 공개 안전 데이터의 부족으로 인해, 다국어 가드레일 모델링은 아직 미개척 분야로 남아 있습니다.  이러한 문제를 해결하기 위해, 본 논문에서는 영어와 다른 언어 간의 불균형을 해소하는 데 중점을 둡니다. 

본 논문에서는 생성기와 가드레일 모델이 상호 작용하는 새로운 2인용 강화학습 프레임워크인 DuoGuard를 제안합니다. 이 프레임워크는 다국어 가드레일 교육을 위한 고품질 합성 데이터를 생성합니다. 이론적 분석과 실험 평가 결과, DuoGuard는 기존 모델보다 뛰어난 성능을 보이며, 특히 저자원 언어의 안전성 작업에서 상당한 발전을 이루었습니다. 이는 다국어 LLM 안전을 향상시키는 데 기여하는 확장 가능하고 효율적인 접근 방식을 제시합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 다국어 LLM 가드레일 모델 교육을 위한 새로운 2인용 강화학습 프레임워크 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 합성 데이터 생성을 통해 다국어 안전 데이터 불균형 문제 해결 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 다양한 벤치마크에서 최첨단 성능 달성 및 추론 속도 향상 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **다국어 LLM 안전을 위한 확장 가능하고 효율적인 접근 방식**을 제시하여, 연구자들이 다국어 LLM의 안전성을 향상시키고, **다양한 언어의 데이터 불균형 문제를 해결**하는 데 도움이 됩니다. 또한, **합성 데이터 생성 및 가드레일 모델 교육 과정**에 대한 새로운 아이디어를 제시하여, 향후 연구의 새로운 방향을 제시합니다. 특히, **다국어 안전 데이터의 부족 문제를 해결**하는 데 기여하며, 향후 연구의 새로운 방향을 제시합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.05163/x1.png)

> 🔼 그림 1은 사용자와 LLM 간의 대화에서 중재자 역할을 하는 LLM 가드레일 모델의 사용 사례를 보여줍니다.  사용자의 입력이 안전하지 않은 경우(예: 유해하거나 불법적인 콘텐츠), 가드레일 모델이 이를 감지하여 LLM이 안전한 응답을 생성하도록 합니다. 이를 통해 LLM이 생성하는 응답의 안전성과 책임성을 높일 수 있습니다.  가드레일 모델은 LLM과 사용자 간의 상호 작용을 조절하여 부적절한 콘텐츠의 생성과 확산을 방지하는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Illustration of the use-case of a guardrail model for LLMs, which functions as moderation between the user-LLM conversation.
> </details>





{{< table-caption >}}
| Seed data | twats know fuck anything. |
|---|---| 
| Generator (selected) | Stinkkäfer kennen fiesen Scheiß von nichts |
| Translation | Stink bugs don’t know anything about nasty shits |
| Generator (filtered) | Arrogante Schwachköpfe behaupten, alles zu kennen, obschon sie eindeutig nichts Ahnung haben. |
| Translation | Arrogant idiots claim to know everything when they clearly have no idea. |{{< /table-caption >}}

> 🔼 표 1은 다양한 언어 모델의 성능을 평가하기 위해 사용된 여섯 가지 다양한 벤치마크에 대한 F1 점수를 자세히 보여줍니다. 표에는 LlamaGuard3, ShieldGemma, LlamaGuard2와 같은 기존 모델과 DuoGuard를 포함한 다양한 크기의 모델이 포함되어 있습니다. 각 모델의 F1 점수는 영어, 프랑스어, 스페인어, 독일어의 네 가지 언어로 나뉘어 표시됩니다. 또한, 각 언어에 대한 평균 F1 점수도 표시되어 있습니다. 굵은 숫자는 각 벤치마크에서 가장 높은 F1 점수를 나타내고, 밑줄 친 숫자는 두 번째로 높은 F1 점수를 나타냅니다. 이 표는 다양한 언어와 크기의 모델에 대한 성능 비교를 제공하여 DuoGuard의 성능 우수성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Detailed F-1 scores on the classification benchmarks. The bold numbers indicate the best results among the methods evaluated and the underscored numbers represent the second-best results.
> </details>





### In-depth insights


#### Multilingual LLM Safety
다국어 LLM 안전성은 영어 이외의 언어에 대한 안전 데이터 부족으로 인해 아직까지 충분히 연구되지 않은 분야입니다. 이는 **다국어 LLM의 책임감 있는 사용을 보장**하기 위해 극복해야 할 주요 과제입니다.  본 논문에서는 이러한 문제를 해결하기 위한 **두 명의 플레이어 기반 강화 학습 프레임워크**를 제시하여 다국어 안전 데이터를 생성하고 분류기를 개선합니다. 이는 생성자와 분류기가 상호 작용하며 고품질 합성 데이터를 생성하고, 이를 통해 다국어 안전 작업의 성능을 향상시키는 방식입니다. 특히, **저자원 언어의 불균형 문제**를 해결하고 다국어 안전 작업에 대한 상당한 발전을 이루어낸다는 점에서 큰 의의가 있습니다.  **합성 데이터 생성의 중요성**을 강조하는 실험 결과는 이러한 접근 방식의 효율성과 확장성을 입증합니다.  결론적으로, 이 연구는 **LLM의 안전한 다국어 사용을 위한 중요한 발걸음**이라고 할 수 있습니다. 

#### Two-Player RL
본 논문에서 제시된 ‘두 플레이어 강화 학습(Two-Player RL)’ 방식은 **합성 데이터 생성 및 분류기 학습을 동시에 개선**하는 참신한 접근법입니다.  생성자(generator)와 분류기(classifier)라는 두 에이전트가 상호 작용하며, **생성자는 분류기를 난처하게 만드는 데이터를 생성**하고, **분류기는 이를 통해 더욱 강건해집니다.** 이러한 반복적인 상호 작용은 마치 **적대적 생성 네트워크(GAN)**과 유사하지만, **강화 학습 기반**이라는 점에서 차별화됩니다.  **내쉬 균형(Nash Equilibrium)** 개념을 도입하여 이론적 토대를 마련하고, 수렴성을 증명한 점 또한 중요합니다.  **다국어 지원**이라는 측면에서도, 영어 중심의 기존 연구와 달리, 다양한 언어에 대한 합성 데이터 생성을 가능하게 하여 **자원이 부족한 언어에 대한 성능 불균형을 해소**하는 데 기여합니다.  그러나, **합성 데이터의 질**과 **생성 모델의 한계** 등은 여전히 고려해야 할 과제입니다.  결론적으로, 제시된 Two-Player RL은 다국어 LLM 안전성 향상을 위한 효율적인 방법론을 제시하지만,  **지속적인 개선과 추가 연구**를 통해 실제 적용 가능성을 더욱 높여야 할 것입니다.

#### Synthetic Data Gen
본 논문에서 인공 데이터 생성(Synthetic Data Gen)은 **다국어 LLM 안전성을 위한 핵심 전략**으로 제시됩니다. 기존의 다국어 데이터 부족 문제를 해결하기 위해, **생성자-감시자 모델 간의 적대적 학습**을 통해 양질의 합성 데이터를 생성하는 프레임워크를 제안합니다. 이는 단순히 데이터 양을 늘리는 것을 넘어, **다국어 균형을 맞추고 모델의 강건성을 높이는 효과적인 방법**임을 실험적으로 증명합니다. 특히, 영어 중심의 데이터 불균형 문제를 해결하여 저자원 언어에 대한 성능 향상에 크게 기여합니다. **두 플레이어의 상호 작용을 게임 이론으로 공식화하여 수렴성을 증명**한 점도 이론적 기여입니다.  하지만, **합성 데이터의 품질 및 신뢰성**에 대한 추가적인 연구가 필요하며, 생성된 데이터의 편향성 및 윤리적 문제에 대한 고려 또한 중요합니다.  **실제 데이터와의 균형**을 고려한 데이터셋 구성 전략 및 합성 데이터의 한계점을 보완하는 방안에 대한 추가 연구가 필요할 것입니다.

#### Convergence Analysis
본 논문의 ‘수렴 분석’ 부분은 이론적 토대를 갖춘 **두 플레이어 강화 학습 프레임워크**의 핵심입니다.  **내쉬 균형**으로의 수렴을 증명하는 것은 알고리즘의 안정성과 효율성에 대한 확신을 제공합니다.  **리프시츠 매핑**을 활용한 수렴 속도 분석은 실제 구현의 효율성을 예측하는 데 중요한 역할을 합니다.  **수렴 증명**은 이론적인 완전성을 보장하며, 실험 결과와 함께 알고리즘의 실용성을 뒷받침합니다.  그러나 **다양한 언어 데이터 불균형**과 같은 실제 문제에 대한 수렴 속도의 영향에 대한 심층 분석은 추가적인 연구를 필요로 합니다.  **실험적 결과**와 이론적 분석의 일치성 여부 또한 중요한 평가 지점입니다.

#### Future Work
본 논문의 핵심 아이디어는 **다국어 LLM 안전성을 위한 이중 플레이어 강화 학습 프레임워크**를 제시하는 것입니다.  향후 연구 방향은 몇 가지 중요한 측면을 고려해야 합니다. 첫째, **합성 데이터 생성 모델의 품질 향상**입니다. 현재 모델은 높은 성능을 보이지만, 더욱 다양하고 정교한 합성 데이터를 생성하여 모델의 일반화 능력을 향상시킬 수 있습니다. 둘째, **저자원 언어에 대한 성능 개선**입니다. 본 논문에서는 다국어 지원을 보여주지만,  일부 저자원 언어에 대한 성능 개선이 필요합니다.  다양한 저자원 언어 데이터를 확보하고, 더욱 효과적인 학습 기법을 개발하는 것이 중요합니다. 셋째, **다양한 안전성 평가 지표**를 사용하는 것입니다.  본 논문에서는 F1 스코어를 사용했지만, 다른 안전성 지표를 추가하여 모델의 안전성을 더욱 포괄적으로 평가할 필요가 있습니다. 마지막으로, **실제 환경 적용 및 실험**입니다.  실제 서비스 환경에서 모델을 적용하고, 그 성능과 안전성을 평가하는 것이 중요합니다. 이를 통해 모델의 실용성을 검증하고, 개선 방향을 도출할 수 있습니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.05163/x2.png)

> 🔼 그림 2는 본 논문의 주요 결과를 보여줍니다. 왼쪽 그림은 4개 언어에 대한 6개의 벤치마크에서 DuoGuard 모델의 평균 F1 점수가 일관되게 우수함을 보여줍니다. 오른쪽 그림은 DuoGuard 모델이 가장 낮은 추론 비용을 유지하면서 언어 전반에 걸쳐 우수한 평균 성능을 달성함을 보여줍니다. DuoGuard는 29개 언어를 지원하는 기본 모델인 Qwen-2.5를 기반으로 하므로, 두 플레이어 데이터 합성 프레임워크를 보여주기 위해 4개 언어에 중점을 두었지만, 다른 언어에도 적용할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Overview of our main results. In the left figure, we demonstrate a consistently superior performance of average f1 score across 6 benchmarks in the four languages. In the right figure, we show that our model maintains the lowest inference cost while achieving superior average performance across languages. We note that, although we focus on the four languages to demonstrate the two-player data synthesis framework, DuoGuard retains its base model Qwen-2.5’s capacity to support all 29 languages.
> </details>



![](https://arxiv.org/html/2502.05163/x3.png)

> 🔼 그림 3은 제안하는 두 플레이어 강화 학습 기반의 다국어 LLM 가드레일 모델 학습 과정을 보여줍니다. 먼저, 기존의 시드 데이터를 기반으로 생성 모델이 합성 데이터를 생성합니다. 분류 모델은 생성된 합성 데이터를 이용하여 예측을 수행하고, 시드 데이터의 레이블과 비교하여 정확도를 평가합니다. 이 과정에서 잘못 분류된 데이터는 생성 모델의 학습에 사용되어 더욱 어려운 예시를 생성하고, 분류 모델의 성능을 향상시키는 순환적 학습 과정을 거치게 됩니다. 이를 통해 생성 모델과 분류 모델이 상호작용하며 지속적으로 개선되는 자기 개선 시스템을 구축합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Overview of the two-player training pipeline. The generator produces synthetic data from seed data. The classifier makes predictions and we measure these examples as being predicted correctly or incorrectly based on their seed data label. We train the generator with DPO to create increasingly challenging examples, which in turn improve the classifier through iterative training.
> </details>



![](https://arxiv.org/html/2502.05163/x4.png)

> 🔼 그림 4는 DuoGuard의 영어 성능과 비교하여 다양한 모델의 평균 F1 점수(6개의 벤치마크와 3개 언어)의 상대적 성능 저하를 보여줍니다. 이는 다국어 지원 능력을 평가하기 위해 영어 이외의 언어(프랑스어, 스페인어, 독일어)에서의 성능 저하 정도를 보여줍니다. DuoGuard는 다른 모델에 비해 상대적으로 낮은 성능 저하를 보이며, 다국어 환경에서의 우수한 일반화 능력을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Relative performance decline (average F1 across six benchmarks and three languages) of various models compared to the English performance of DuoGuard.
> </details>



![](https://arxiv.org/html/2502.05163/x5.png)

> 🔼 그림 5는 본 논문에서 사용한 시드 데이터에 여러 언어의 데이터를 포함하여 학습시킨 모델의 OpenAI 벤치마크 F1 점수를 보여줍니다. 영어 데이터만 사용한 경우보다 영어와 프랑스어 데이터를 함께 사용한 경우 스페인어(36.9%에서 62.8%로)와 독일어(31.9%에서 59.6%로) 성능이 향상되는 것을 알 수 있습니다. 이는 다양한 언어의 데이터를 포함하는 것이 저자원 언어의 성능 향상에 도움이 된다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: The F1 score on OpenAI benchmark of models trained with data containing different languages in our seed data. The inclusion of French in addition to English improves model performance on Spanish (36.9% to 62.8%) and German (31.9 to 59.6).
> </details>



![](https://arxiv.org/html/2502.05163/x6.png)

> 🔼 이 그림은 씨드 데이터로 학습된 모델의 언어별 성능을 보여줍니다.  씨드 데이터에서 영어 데이터의 비중이 클수록 모델의 영어 평균 성능이 다른 언어보다 현저히 높다는 것을 보여줍니다. 이는 씨드 데이터의 언어별 불균형이 모델 성능에 영향을 미친다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Performance by languages of the model trained on seed data. With larger data proportion in seed data, the model’s average performance on English is markedly higher than on other languages.
> </details>



![](https://arxiv.org/html/2502.05163/x7.png)

> 🔼 그림 7은 DuoGuard 모델의 반복적인 성능 향상과 각 언어 데이터 분포 변화를 보여줍니다. (a)는 반복적인 학습을 통해 DuoGuard 모델의 성능이 지속적으로 향상되는 것을 보여주는 그래프입니다. 특히 영어 이외 언어들의 성능 향상이 두드러지며, 2회 반복 후에는 모든 언어의 성능이 비슷한 수준에 도달합니다. (b)는 각 반복 단계에서 영어를 포함한 각 언어 데이터의 비율 변화를 보여주는 그래프입니다. 1회 반복 후에는 영어 데이터 비율이 감소하고, 다른 언어 데이터 비율이 증가하여 데이터 불균형 문제가 완화되는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: (a) Iterative performance improvements of DuoGuard. (b) Shift in data distribution across languages over iterations.
> </details>



![](https://arxiv.org/html/2502.05163/x8.png)

> 🔼 그림 8은 논문에서 사용된 씨앗 데이터셋의 언어별 데이터 비율을 보여줍니다. 영어 데이터가 압도적으로 많고(81.4%), 프랑스어(8.9%), 스페인어(5.2%), 독일어(4.5%) 데이터는 상대적으로 적습니다. 이는 다국어 모델 학습에 있어 데이터 불균형 문제를 시사하며, 본 논문에서 제시하는 합성 데이터 생성 방법의 필요성을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Data proportion by language in our collected seed data from open sources.
> </details>



![](https://arxiv.org/html/2502.05163/x9.png)

> 🔼 그림 9는 시드 데이터로 학습된 분류기의 오탐과 미탐에 대한 출력 확률 분포를 보여줍니다. 오탐은 1에 치우쳐 있고 미탐은 0에 치우쳐 있는 비대칭 분포는 분류기가 잘못된 예측에 대해 더 높은 확신을 가지고 있음을 나타냅니다. 네 개의 프랑스어 데이터셋에 대한 분석 결과, 분류기는 잘못된 예측에 상당한 확신을 보이는 것으로 나타났습니다. 이는 시드 데이터에만 의존하여 훈련된 모델이 새로운 데이터나 분포 변화에 취약할 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Output Probability Distribution of False Positives and False Negatives in the Classifier Trained on Seed Data. A skewed distribution toward 0 for false negatives and toward 1 for false positives indicates higher classifier confidence in its incorrect predictions. Analysis across the four French datasets reveals that the classifier exhibits significant confidence in its false predictions.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Data type | bf16 |
|---|---| 
| Learning rate | 5e-5 |
| Optimizer | AdamW |
| Global batch size | 640 |
| Gradient accumulation steps | 4 |
| Scheduler | Cosine |
| Warmup ratio | 0.1 |
| Num train epochs | 2 |
| Group by length | True |
| Max grad norm | 1.0 |{{< /table-caption >}}
> 🔼 이 표는 두 플레이어 방식으로 생성된 데이터셋을 사용하여 훈련된 다양한 모델에 대한 언어별 평균 F1 점수를 보여줍니다.  Llama-3.2와 같은 다른 기본 모델과 1.5B와 같은 다른 규모에도 데이터셋이 쉽게 일반화될 수 있음을 보여줍니다.  즉, 본 논문에서 제시된 두 플레이어 강화학습 프레임워크를 통해 생성된 합성 데이터셋이 다양한 모델 구조와 크기에 대해서도 효과적으로 일반화될 수 있음을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Average F-1 scores across languages of different models trained with the dataset developed by our two-player scheme. The data can easily generalize to different base models (Llama-3.2) and different scales (1.5B).
> </details>

{{< table-caption >}}
| Data type | bf16 |
|---|---| 
| Learning rate | 5e-7 |
| Optimizer | AdamW |
| Global batch size | 64 |
| Gradient accumulation steps | 8 |
| Scheduler | Cosine |
| Warmup ratio | 0.1 |
| Beta | 0.01 |
| RPO alpha | 0.4 |
| Max length | 1024 |
| Num train epochs | 1 |{{< /table-caption >}}
> 🔼 표 3은 DuoGuard 모델의 성능을 보여주는 표입니다. 이 표는 반복적인 학습 과정의 첫 번째 반복(Iteration 1)에서 다양한 언어 데이터를 사용하여 훈련된 모델의 평균 F1 점수를 보여줍니다.  다양한 언어 조합(영어만, 영어와 프랑스어, 모든 언어)으로 학습된 모델의 성능을 비교하여, 다국어 데이터를 포함하는 것이 모델 성능 향상에 미치는 영향을 분석합니다.  각 언어별로 평균 F1 점수를 제시하여, 특정 언어에 대한 모델의 성능 편향을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Model’s average F1 with different training data at Iter1.
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