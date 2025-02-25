---
title: "InterFeedback: Unveiling Interactive Intelligence of Large Multimodal Models via Human Feedback"
summary: "인간 피드백을 통한 대규모 다중 모드 모델의 상호 작용 지능 향상"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Human-AI Interaction", "🏢 Show Lab, National University of Singapore",]
showSummary: true
date: 2025-02-20
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.15027 {{< /keyword >}}
{{< keyword icon="writer" >}} Henry Hengyuan Zhao et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-24 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.15027" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.15027" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/interfeedback-unveiling-interactive" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

현존하는 벤치마크들은 대규모 다중 모드 모델(LMM)의 인간 사용자와의 상호 작용 지능을 평가하지 못한다는 문제가 있습니다.  이는 LMM이 실제 응용 프로그램에서 얼마나 효과적인지 판단하기 어렵게 만드는 요소입니다.  기존 벤치마크들은 주로 정적인 문제 해결 능력에 초점을 맞추고, **인간의 피드백을 통한 학습 및 적응 능력**에 대한 평가가 부족합니다.

본 연구에서는 **인간의 피드백을 활용하여 LMM의 상호 작용 지능을 평가하는 새로운 프레임워크 InterFeedback**을 제안합니다.  이 프레임워크를 기반으로 두 개의 대표적인 데이터셋을 사용하여 10가지의 오픈소스 LMM을 평가하고,  **상위 모델의 상호 작용 성능**과 **피드백 반영 능력**을 분석합니다.  **인간 참여자를 활용한 추가 실험**을 통해 실제 상황에서의 LMM 성능을 검증하고,  **피드백의 질**이 모델 성능에 미치는 영향을 분석합니다.  이 연구는 LMM의 상호 작용 지능을 향상시키기 위한 새로운 방법론 개발에 기여할 것으로 기대됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 새로운 상호 작용 프레임워크 InterFeedback 및 벤치마크 InterFeedback-Bench 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 인간 피드백을 통한 LMM 성능 향상 가능성 확인 및 한계점 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 다양한 유형의 피드백에 대한 LMM의 반응 분석을 통한 새로운 통찰력 제공 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대규모 다중 모드 모델(LMM)**의 상호 작용 지능을 평가하기 위한 새로운 벤치마크와 프레임워크를 제시하여, **인간의 피드백을 통해 LMM의 성능을 향상시키는 방법**을 연구하는 데 중요한 의미를 가집니다.  현재 LMM 연구의 주요 트렌드 중 하나인 **인간-AI 상호작용** 분야에 대한 새로운 관점을 제공하며,  향후 연구의 방향을 제시하는 데 기여합니다. 특히, **다양한 유형의 피드백과 모델의 상호 작용**에 대한 분석은 LMM의 한계와 개선 방향을 이해하는 데 중요한 통찰력을 제공합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.15027/x1.png)

> 🔼 그림 1은 대화형 피드백 시나리오를 보여줍니다. 모델이 잘못된 응답을 생성하면 사용자가 관련 피드백을 제공하여 반복적으로 답변을 개선하는 과정을 나타냅니다.  모델이 질문에 대한 답을 제시하고, 사용자가 답변이 정확하지 않을 경우 추가 정보를 제공하여 모델이 올바른 답을 찾을 수 있도록 유도하는 과정이 반복됩니다. 이는 인간의 개입을 통해 모델의 학습 및 성능 개선이 가능함을 시각적으로 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Illustration of an interactive feedback scenario. When models generate incorrect responses, human users provide pertinent feedback to iteratively refine the answers.
> </details>





{{< table-caption >}}
| Model | Acc (%) | # Neg | GPT-4o # Test | GPT-4o Detail (%) | GPT-4o Simple (%) | Gemini-1.5-Flash # Test | Gemini-1.5-Flash Detail (%) | Gemini-1.5-Flash Simple (%) | Claude-3.5-Sonnet # Test | Claude-3.5-Sonnet Detail (%) | Claude-3.5-Sonnet Simple (%) |
|---|---|---|---|---|---|---|---|---|---|---|---| 
| LLaVa-OneVision-7B | 25.6 | 2933 | 373 | 36.2 | 18.0 | 428 | 29.0 | 15.7 | 2953 | 4.1 | 2.4 |
| InternVL2-8B | 38.1 | 2440 | 379 | 49.6 | 41.2 | 375 | 48.8 | 44.4 | 376 | 43.4 | 40.2 |
| Molmo-7B | 25.6 | 2931 | 452 | 55.1 | 52.0 | 507 | 36.5 | 38.9 | 597 | 37.4 | 40.0 |
| MiniCPM-V | 16.2 | 3301 | 552 | 28.4 | 20.3 | 741 | 16.6 | 25.4 | 772 | 18.7 | 27.1 |
| GLM-4V-9B | 20.2 | 3146 | 440 | 38.6 | 28.2 | 568 | 30.1 | 29.9 | 603 | 30.0 | 26.4 |
| Phi3.5-Vision-4.2B | 19.0 | 3192 | 534 | 36.1 | 33.7 | 579 | 31.3 | 33.7 | 616 | 26.8 | 29.1 |
| LLaVa-1.5-7B | 13.5 | 3409 | 763 | 23.2 | 14.3 | 678 | 18.0 | 14.7 | 816 | 8.3 | 11.2 |
| LLaVa-1.6-Mistral-7B | 14.8 | 3357 | 549 | 41.0 | 35.9 | 661 | 5.9 | 5.9 | 617 | 33.5 | 33.2 |
| Fuyu-8B | 21.8 | 3083 | 582 | 24.1 | 19.8 | 635 | 15.0 | 12.9 | 755 | 14.0 | 11.5 |
| Qwen2-VL-7B | 22.5 | 3052 | 295 | 66.8 | 72.2 | 470 | 41.9 | 44.9 | 505 | 50.5 | 52.7 |{{< /table-caption >}}

> 🔼 표 1은 MathVerse 데이터셋에 대해 세 가지 피드백 제공자의 정정률 결과를 보여줍니다.  Acc(%)는 MathVerse의 testmini 세트의 평균 정확도를 나타냅니다. #Neg는 모델이 생성한 음성 샘플의 수, #Test는 평가된 테스트 샘플의 총 수, Detail(%)는 LMM이 생성한 피드백을 사용한 정정률, Simple(%)은 단순한 피드백(0 또는 1)을 사용한 정정률을 나타냅니다. 본 연구에서 직접 테스트한 결과입니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Correction Rate Results of three Feedback Providers on MathVerse Dataset. Acc (%): The average accuracy of MathVerse’s testmini set. The results are tested by ourselves. # Neg: The number of negative samples produced by the model. # Test: The total number of test samples evaluated. Detail (%): correction rate of using LMM-generated feedback. Simple (%): correction rate of using simple feedback (0 or 1).
> </details>





### In-depth insights


#### Interactive LMMs
본 논문은 **대규모 다중 모드 모델(LMM)**의 상호작용적 지능에 대한 흥미로운 통찰력을 제공합니다. 특히 **인간의 피드백을 통한 학습 능력**에 초점을 맞춰 기존 벤치마크의 한계를 넘어섭니다.  **상호작용적 LMM**은 단순히 문제를 해결하는 것을 넘어, 인간과의 상호작용을 통해 지속적으로 개선되는 능력을 보여줍니다. 이는 **일반적인 AI 어시스턴트** 개발에 매우 중요한 요소입니다.  그러나 실험 결과는 최첨단 LMM조차도 인간의 피드백을 50% 미만으로만 활용한다는 것을 보여주며, **피드백 해석 및 활용 능력 개선**이 시급함을 시사합니다.  **상호작용적 문제 해결 능력 평가를 위한 새로운 벤치마크** 제시와 함께, 다양한 모델의 성능 비교 분석 및 인간과의 상호작용 과정에 대한 심층적인 이해를 제공하여 향후 연구 방향을 제시하는데 기여합니다.  **고품질의 피드백**의 중요성 또한 강조되어,  단순한 정답 여부를 넘어 상세한 설명을 포함하는 피드백이 모델 성능 향상에 크게 기여함을 확인했습니다.  **결론적으로**,  인간과의 효과적인 상호작용을 통해 지속적으로 학습하고 발전하는 LMM 개발을 위한 새로운 방법론 및 연구가 필요함을 강조합니다.

#### InterFeedback Bench
InterFeedback Bench는 제시된 연구 논문에서 **대규모 다중 모드 모델(LMM)**의 대화형 지능을 평가하기 위한 벤치마크입니다.  기존 벤치마크들이 정적 평가에 초점을 맞춘 것과 달리, InterFeedback Bench는 **인간의 피드백을 통한 상호 작용**을 중시하며 LMM의 학습 능력 및 적응력을 측정합니다.  **두 가지 대표적인 데이터셋(MMMU-Pro와 MathVerse)**을 활용하여 다양한 LMM들의 성능을 비교 분석하고, 특히 **피드백 해석 및 활용 능력**에 대한 심층적인 평가를 수행합니다.  **인간 참여자를 통한 추가적인 실험**은 LMM의 한계점을 보여주는 동시에, 향후 **인간-AI 상호작용의 발전 방향**을 제시하는 귀중한 통찰력을 제공합니다.  **자동화된 모델 테스트의 어려움**을 해결하기 위한 InterFeedback 프레임워크의 도입은 벤치마크의 핵심적인 강점 중 하나이며,  향후 연구에서 LMM의 대화형 지능 향상을 위한 중요한 기준이 될 것입니다.

#### Human Feedback
본 논문에서 '인간 피드백'은 대규모 다중 모드 모델(LMM)의 성능 향상에 있어 핵심적인 역할을 한다는 점을 강조합니다. **인간이 제공하는 피드백은 LMM이 문제 해결 과정에서 실수를 수정하고, 성능을 개선하는 데 중요한 정보**를 제공합니다.  특히, 단순히 정답/오답 여부만 알려주는 것이 아니라, **상세한 설명을 포함한 피드백이 LMM의 학습에 더 효과적**이라는 점을 실험 결과를 통해 보여줍니다.  하지만, **모든 LMM이 인간 피드백을 효과적으로 활용하는 것은 아니며**, 일부 모델은 피드백을 통해 오히려 성능이 저하되는 경우도 있습니다.  이는 **LMM의 피드백 해석 및 적용 능력이 아직 미흡**하다는 것을 시사합니다. 따라서,  **향후 연구는 LMM이 인간 피드백을 효과적으로 활용할 수 있도록 하는 방법론 개발**에 초점을 맞춰야 합니다.  **단순히 정답률 향상뿐 아니라, 문제 해결 과정의 이해도 향상 및 추론 능력 향상**을 위한 연구가 필요하며, 이를 위해 다양한 종류의 피드백 방식과 데이터셋에 대한 추가적인 연구가 필요합니다.  더 나아가, **양질의 피드백 제공이 중요**하며, 낮은 질의 피드백은 오히려 성능 저하로 이어질 수 있음을 유의해야 합니다.

#### LMM Feedback
본 논문에서 'LMM 피드백'은 대규모 다중 모드 모델(LMM)의 성능 향상에 있어 인간 피드백의 역할을 중점적으로 다룹니다.  **기존 벤치마크들이 LMM의 정적 성능 평가에 치중한 반면,** 이 연구는 **인간과의 상호작용을 통한 LMM의 학습 및 적응 능력**에 초점을 맞춥니다.  이는 **일반적인 AI 어시스턴트 개발에 필수적인 요소**이기 때문입니다.  연구진은 인간 피드백을 활용한 LMM의 반복적인 문제 해결 과정을 분석하고, **피드백의 질적 수준이 성능에 미치는 영향**을 심도 있게 다룹니다. 특히, 단순한 정오 판단(0/1) 피드백과 상세한 설명을 포함한 피드백을 비교 분석하여, **상세한 피드백이 항상 효과적인 것은 아님**을 보여줍니다.  이는 **LMM이 인간 피드백을 효과적으로 해석하고 활용하는 능력의 부족**을 시사합니다.  **향후 연구 방향으로는 LMM의 피드백 해석 및 활용 능력 향상을 위한 새로운 방법론 개발**이 제시됩니다.

#### Future of LMMs
LMM(대규모 다중 모드 모델)의 미래는 **상호 작용 지능**과 **인간 피드백 처리 능력** 향상에 달려 있습니다.  현재 LMM은 뛰어난 문제 해결 능력을 가지고 있지만, 인간의 피드백을 통해 학습하고 자기 개선하는 능력은 미흡합니다.  향후 연구는 LMM이 인간의 다양한 유형의 피드백(단순 정답 여부, 자세한 설명 등)을 효과적으로 이해하고, 이를 토대로 성능을 개선하는 방법에 초점을 맞춰야 합니다.  **고품질 피드백의 중요성** 또한 간과할 수 없습니다.  잘못된 피드백은 오히려 성능 저하를 야기할 수 있으므로,  피드백 메커니즘 자체의 개선과 더불어 **인간-AI 상호 작용의 질적 향상**을 위한 노력이 필요합니다.  **다양한 상호작용 시나리오**에 대한 평가 기준 마련과 더불어,  **실제 응용 분야**에서의 성능 검증을 통해  진정한 범용 AI 어시스턴트로서의 LMM 발전을 도모해야 합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.15027/x2.png)

> 🔼 그림 2는 InterFeedback-Bench를 위한 테스트 데이터 구성 과정을 개괄적으로 보여줍니다. 피드백 수신기 역할을 하는 각각의 LMM에 대해, 대상 데이터셋(예: MathVerse)의 각 인스턴스를 처리하고 오류 케이스를 수집하여 음성 집합을 만듭니다. 그런 다음 피드백 제공자는 동일한 인스턴스를 처리하여 양성 집합을 만듭니다. 마지막으로 두 집합의 교집합을 선택하여 테스트 데이터를 구성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Overview of the test data construction process for InterFeedback-Bench. For each LMM serving as the feedback receiver, we process each instance from a target dataset (e.g., MathVerse) and collect the error cases to form a negative set. The feedback provider then processes the same instances to build a positive set. Finally, we curate test data by selecting the intersection of both sets.
> </details>



![](https://arxiv.org/html/2502.15027/x3.png)

> 🔼 그림 3은 제안된 InterFeedback 프레임워크의 개요를 보여줍니다. 이 프레임워크는 LMM(대규모 다중 모드 모델)이 피드백을 통해 자체적으로 문제 해결 능력을 향상시키는 능력을 평가하기 위해 고안되었습니다.  LMM은 인간과 상호 작용하여 문제를 단계적으로 해결하며, 각 대화 라운드 후 답변의 정확성을 검증합니다. 답변이 틀렸다면, LMM에 의해 유도된 인간이 건설적인 피드백을 제공합니다. LMM의 동작을 조사하기 위해 두 가지 유형의 피드백이 구현되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Overview of the proposed framework InterFeedback for assessing an LMM’s ability to improve itself through feedback. The model interacts with humans to progressively solve a problem, and after each conversation round, we verify the correctness of the answer. If the answer is incorrect, an LMM-stimulated human will provide constructive feedback. We implement two types of feedback to investigate the behavior of LMMs.
> </details>



![](https://arxiv.org/html/2502.15027/x8.png)

> 🔼 그림 4는 InterFeedback-Human 데이터셋에서 각 라운드별로 정답이 수정된 샘플의 분포를 보여줍니다.  각 모델(Gemini-2.0, GPT-40, OpenAI-01, Claude-3.5-Sonnet)에 대해 초기 정확도(Round 0)와 후속 라운드(Round 1, 2, 3)에서의 정답 수정 비율을 나타냅니다.  Claude-3.5-Sonnet 모델이 Round 0에서 가장 높은 정확도를 보이는 것을 확인할 수 있습니다.  이 그림은 각 모델의 초기 성능과 피드백을 통한 학습 능력을 시각적으로 비교 분석하는 데 유용합니다. 
> <details>
> <summary>read the caption</summary>
> Figure 4: Distribution of samples being corrected in each round. We can observe that Claude-3.5-Sonnet archives the best performance in round 0.
> </details>



![](https://arxiv.org/html/2502.15027/x9.png)

> 🔼 그림 5는 다양한 유형의 문제에 대한 정답 수정 비율을 라운드별로 보여줍니다. 시각적 논리 문제는 대부분 처음 두 라운드에서 해결되었지만, 텍스트 기반 수학 문제와 MMMU-Pro 문제는 1, 2라운드에서 정답 수정 비율이 낮았습니다. 반대로, 텍스트 기반 코딩 문제와 MathVerse 문제는 1, 2라운드에서 정답 수정이 이루어졌습니다. 이는 문제 유형에 따라 상호작용적 피드백을 통한 모델 학습 효과가 다르게 나타남을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Distribution of corrected samples across various task categories. Visual logic tasks are mostly resolved within the first two rounds, whereas Math (Text-only) and MMMU-Pro tasks show little corrections in rounds 1 and 2. In contrast, Coding (Text-only) and MathVerse tasks exhibit corrections during rounds 1 and 2.
> </details>



![](https://arxiv.org/html/2502.15027/x10.png)

> 🔼 그림 6은 서로 다른 대규모 다중 모드 모델(LMM)들이 동일한 문제에 대해 어떻게 다른 결과를 생성하는지 보여주는 정성적 결과를 보여줍니다. 각 LMM은 질문에 대한 답변과 함께, 사용자가 제시한 잘못된 답변에 대한 피드백을 처리하는 과정이 순차적으로 나열되어 있습니다. 이는 모델의 상호 작용 능력과 피드백 해석 능력을 비교 분석하는 데 유용합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Qualitative results on different LMMs.
> </details>



![](https://arxiv.org/html/2502.15027/x11.png)

> 🔼 그림 7은 서로 다른 대규모 다중 모드 모델(LMM)들이 상호작용적 문제 해결 과정에서 어떻게 다른 결과를 보이는지 보여주는 정성적 결과를 보여줍니다.  각 모델이 문제에 접근하는 방식과 인간 피드백에 대한 반응을 비교 분석하여 LMM의 상호작용 지능과 피드백 해석 능력의 차이를 보여줍니다. 특히, 모델이 정답에 도달하기까지의 단계와 과정, 그리고 인간 피드백을 통해 어떻게 수정해나가는지를 자세하게 제시하며, 다양한 모델들의 상호작용적 지능 수준을 비교 분석합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Qualitative results on different LMMs.
> </details>



![](https://arxiv.org/html/2502.15027/x12.png)

> 🔼 그림 8은 모델이 정답을 추측하는 경향이 있는 예시를 보여줍니다.  문제는 네 가지 선택지 중에서 순서를 완성하거나 패턴을 파악하는 가장 적절한 옵션을 선택하는 것입니다. 모델은 정답을 도출하는 논리적 추론 과정 없이, 단순히 선택지를 하나씩 제거해 나가는 방식으로 정답을 추측하는 모습을 보여줍니다. 이는 모델이 복잡한 문제 해결 과정보다는 단순한 패턴 인식에 의존하는 경향이 있음을 시사합니다.  이러한 추측 방식은 정확성이 낮고, 실제 문제 해결 능력이 부족함을 드러냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: An example that model tends to guess answers.
> </details>



![](https://arxiv.org/html/2502.15027/x13.png)

> 🔼 그림 9는 모델이 답을 추측하는 경향이 있는 예시를 보여줍니다. 문제는 네 가지 선택지 중에서 순서를 완성하거나 패턴을 파악하는 가장 적절한 옵션을 선택하는 것입니다. 정답은 A입니다. 이 문제는 도형의 유형을 파악하는 능력을 평가합니다. 첫 번째 그룹의 도형은 모두 평면 도형이고, 두 번째 그룹의 도형은 입체 도형입니다.  모델이 제시하는 답변들은 정답을 직접적으로 추론하기보다는, 제한된 선택지 안에서 답을 추측하는 경향을 보여줍니다.  특히, 모델은 문제 해결 과정에서 단서들을 체계적으로 분석하고 추론하는 능력보다는, 패턴을 단순히 인식하거나,  선택지 간의 관계를 통해 답을 유추하는 데 집중하는 경향이 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: An example that model tends to guess answers.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | Acc (%) | # Neg | GPT-4o # Test | GPT-4o Detail (%) | GPT-4o Simple (%) | Gemini-1.5-Flash # Test | Gemini-1.5-Flash Detail (%) | Gemini-1.5-Flash Simple (%) | Claude-3.5-Sonnet # Test | Claude-3.5-Sonnet Detail (%) | Claude-3.5-Sonnet Simple (%) |
|---|---|---|---|---|---|---|---|---|---|---|---| 
| LLaVa-OneVision-7B | 47.1 | 915 | 312 | 31.7 | 15.7 | 333 | 35.4 | 18.6 | 408 | 27.5 | 16.4 |
| InternVL2-8B | 45.7 | 939 | 343 | 50.1 | 41.4 | 329 | 57.1 | 50.2 | 437 | 50.1 | 41.2 |
| Molmo-7B | 43.8 | 973 | 362 | 51.7 | 48.9 | 383 | 41.5 | 43.1 | 436 | 29.8 | 27.5 |
| MiniCPM-V | 38.1 | 1071 | 410 | 27.3 | 23.7 | 503 | 21.5 | 21.7 | 540 | 24.4 | 23.3 |
| GLM-4V-9B | 46.0 | 935 | 327 | 38.8 | 30.0 | 359 | 38.7 | 31.5 | 441 | 34.9 | 27.9 |
| Phi3.5-Vision-4.2B | 43.2 | 983 | 366 | 44.3 | 42.3 | 396 | 40.9 | 39.6 | 484 | 39.9 | 38.0 |
| LLaVa-1.5-7B | 36.5 | 1099 | 506 | 31.9 | 12.3 | 470 | 20.0 | 16.0 | 595 | 13.9 | 13.4 |
| LLaVa-1.6-Mistral-7B | 38.8 | 1058 | 432 | 46.1 | 36.1 | 429 | 14.7 | 14.7 | 515 | 42.3 | 35.3 |
| Fuyu-8B | 34.1 | 1140 | 481 | 6.0 | 8.7 | 1140 | 3.7 | 3.5 | 612 | 9.5 | 6.9 |
| Qwen2-VL-7B | 48.1 | 898 | 268 | 50.4 | 44.8 | 322 | 39.4 | 37.6 | 389 | 42.9 | 37.3 |{{< /table-caption >}}
> 🔼 표 2는 MMMU-Pro 데이터셋에 대해 세 가지 피드백 제공자의 정정률 결과를 보여줍니다. 모델은 MMMU-Pro의 단일 이미지 설정에서 테스트됩니다. 이 표는 각 모델에 대한 정확도, 음성 샘플 수, 테스트 샘플 수, 세 가지 피드백 제공자(GPT-40, Gemini-1.5-Flash, Claude-3.5-Sonnet) 각각에 대한 자세한 피드백과 간단한 피드백을 사용한 정정률을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Correction Rate Results of three Feedback Providers on MMMU-Pro Dataset. We test models on a single image setting of MMMU-Pro.
> </details>

{{< table-caption >}}
| Model | Visual Logic | MMMU-Pro | MathVerse | Math<sup>Text</sup> | Coding<sup>Text</sup> | Average |
|---|---|---|---|---|---|---|
| Gemini-2.0 | 21.3 | 50.0 | 70.0 | 50.0 | 50.0 | 32.5 |
| Claude-3.5 | 37.5 | 60.0 | 80.0 | 70.0 | 70.0 | 48.3 |
| OpenAI-o1 | 28.8 | 60.0 | 90.0 | 90.0 | 90.0 | 46.7 |
| GPT-4o | 25.0 | 70.0 | 80.0 | 60.0 | 50.0 | 38.3 |{{< /table-caption >}}
> 🔼 표 3은 InterFeedback-Human 데이터셋을 사용하여 여러 대규모 다중 모드 모델(LMM)의 성능을 평가한 결과를 보여줍니다. MathText와 CodingText는 텍스트 기반 작업 유형을 나타내며, 각 점수는 전체 샘플 중 정답 샘플의 평균 비율을 나타냅니다.  즉, 각 LMM이 다양한 유형의 문제(시각적 논리, 수학, 코딩 등)에 대해 얼마나 정확하게 답변했는지를 보여주는 표입니다. 
> <details>
> <summary>read the caption</summary>
> Table 3: Human Evaluation Results across LMMs on InterFeedback-Human. MathTextText{}^{\text{Text}}start_FLOATSUPERSCRIPT Text end_FLOATSUPERSCRIPT and CodingTextText{}^{\text{Text}}start_FLOATSUPERSCRIPT Text end_FLOATSUPERSCRIPT represent two text-only task categories. The scores represent the average percentage of correct samples among all samples.
> </details>

{{< table-caption >}}
| Model | # Round | Visual Logic | MMMU-Pro | MathVerse | Math<sup>Text</sup> | Coding<sup>Text</sup> | Average |
|---|---|---|---|---|---|---|---| 
| Gemini-2.0 | 1 | 38.1 | 20.0 | 33.3 | 0.0 | 80.0 | 37.0 |
|  | 2 | 20.6 | 0.0 | 33.3 | 20.0 | 20.0 | 19.8 |
|  | 3 | 41.3 | 80.0 | 33.3 | 80.0 | 0.0 | 43.2 |
| Claude-3.5 | 1 | 38.0 | 0.0 | 50.0 | 33.3 | 66.7 | 37.1 |
|  | 2 | 32.0 | 25.0 | 50.0 | 33.3 | 66.7 | 30.6 |
|  | 3 | 30.0 | 75.0 | 0.0 | 66.7 | 0.0 | 32.3 |
| OpenAI-o1 | 1 | 38.6 | 0.0 | 100.0 | 11.1 | 100.0 | 39.1 |
|  | 2 | 21.1 | 0.0 | 0.0 | 0.0 | 0.0 | 18.8 |
|  | 3 | 40.4 | 100.0 | 0.0 | 0.0 | 0.0 | 42.2 |
| GPT-4o | 1 | 41.7 | 33.3 | 100.0 | 25.0 | 40.0 | 41.9 |
|  | 2 | 31.7 | 0.0 | 0.0 | 0.0 | 0.0 | 25.7 |
|  | 3 | 26.7 | 66.7 | 0.0 | 75.0 | 60.0 | 32.4 |{{< /table-caption >}}
> 🔼 표 4는 InterFeedback-Human 데이터셋에서 다양한 대규모 다중 모드 모델(LMM)의 정정률 결과를 보여줍니다. MathText와 CodingText는 텍스트만 사용하는 두 가지 작업 유형을 나타냅니다. # Round는 상호 작용 라운드 수를 나타내며, 정정률은 잘못된 샘플 중에서 정정된 샘플의 비율을 백분율로 나타냅니다. 이 표는 각 LMM이 피드백을 통해 문제 해결 능력을 향상시키는 능력을 평가하는 데 사용된 다양한 상호작용 라운드에서의 성능을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Correction Rate Results across various LMMs on InterFeedback-Human. MathTextText{}^{\text{Text}}start_FLOATSUPERSCRIPT Text end_FLOATSUPERSCRIPT and CodingTextText{}^{\text{Text}}start_FLOATSUPERSCRIPT Text end_FLOATSUPERSCRIPT represent two text-only task categories. # Round denotes the number of interaction rounds. The correction rate is the percentage of corrected samples among all erroneous samples.
> </details>

{{< table-caption >}}
| Model | Release Time | Source |
|---|---|---|
| _Closed-source Models_ |  |  |
| GPT-4o <cite class="ltx_cite ltx_citemacro_citep">(OpenAI, <a class="ltx_ref" href="https://arxiv.org/html/2502.15027v1#bib.bib30" title="">2023</a>)</cite> | 2024-08-26 | <a class="ltx_ref ltx_url ltx_font_typewriter" href="https://openai.com/index/hello-gpt-4o/" title="">https://openai.com/index/hello-gpt-4o/</a> |
| OpenAI-o1 <cite class="ltx_cite ltx_citemacro_citep">(OpenAI, <a class="ltx_ref" href="https://arxiv.org/html/2502.15027v1#bib.bib31" title="">2024</a>)</cite> | 2024-12-17 | <a class="ltx_ref ltx_url ltx_font_typewriter" href="https://openai.com/o1/" title="">https://openai.com/o1/</a> |
| Gemini-1.5-Flash <cite class="ltx_cite ltx_citemacro_citep">(Gemini, <a class="ltx_ref" href="https://arxiv.org/html/2502.15027v1#bib.bib11" title="">2024</a>)</cite> | 2024-09-24 | <a class="ltx_ref ltx_url ltx_font_typewriter" href="https://deepmind.google/technologies/gemini/" title="">https://deepmind.google/technologies/gemini/</a> |
| Gemini-2.0-Flash | 2025-01-21 | <a class="ltx_ref ltx_url ltx_font_typewriter" href="https://deepmind.google/technologies/gemini/" title="">https://deepmind.google/technologies/gemini/</a> |
| Claude-3.5-Sonnet | 2024-10-22 | <a class="ltx_ref ltx_url ltx_font_typewriter" href="https://www.anthropic.com/claude/sonnet" title="">https://www.anthropic.com/claude/sonnet</a> |
| _Closed-source Models_ |  |  |
| LLaVA-One-Vision | 2024-08-05 | <a class="ltx_ref ltx_url ltx_font_typewriter" href="https://llava-vl.github.io/blog/2024-08-05-llava-onevision/" title="">https://llava-vl.github.io/blog/2024-08-05-llava-onevision/</a> |
| InterVL2-8B | 2024-07-04 | <a class="ltx_ref ltx_url ltx_font_typewriter" href="https://internvl.github.io/blog/2024-07-02-InternVL-2.0/" title="">https://internvl.github.io/blog/2024-07-02-InternVL-2.0/</a> |
| Molmo-7B | 2024-09-24 | <a class="ltx_ref ltx_url ltx_font_typewriter" href="https://huggingface.co/allenai/Molmo-7B-D-0924" title="">https://huggingface.co/allenai/Molmo-7B-D-0924</a> |
| MiniCPM-V | 2024-08-03 | <a class="ltx_ref ltx_url ltx_font_typewriter" href="https://huggingface.co/openbmb/MiniCPM-V" title="">https://huggingface.co/openbmb/MiniCPM-V</a> |
| GLM-4V-9B | 2024-11-01 | <a class="ltx_ref ltx_url ltx_font_typewriter" href="https://huggingface.co/THUDM/glm-4v-9b" title="">https://huggingface.co/THUDM/glm-4v-9b</a> |
| Pih3.5-Vision-4.2B | 2024-08-20 | <a class="ltx_ref ltx_url ltx_font_typewriter" href="https://huggingface.co/microsoft/Phi-3.5-vision-instruct" title="">https://huggingface.co/microsoft/Phi-3.5-vision-instruct</a> |
| LLaVA-1.5-7B | 2023-10-05 | <a class="ltx_ref ltx_url ltx_font_typewriter" href="https://huggingface.co/liuhaotian/llava-v1.5-7b" title="">https://huggingface.co/liuhaotian/llava-v1.5-7b</a> |
| LLaVA-1.6-Mistral-7B | 2024-01-30 | <a class="ltx_ref ltx_url ltx_font_typewriter" href="https://huggingface.co/llava-hf/llava-v1.6-mistral-7b-hf" title="">https://huggingface.co/llava-hf/llava-v1.6-mistral-7b-hf</a> |
| Fuyu-8B | 2023-10-27 | <a class="ltx_ref ltx_url ltx_font_typewriter" href="https://huggingface.co/adept/fuyu-8b" title="">https://huggingface.co/adept/fuyu-8b</a> |
| Qwen2-VL-7B | 2024-08-30 | <a class="ltx_ref ltx_url ltx_font_typewriter" href="https://huggingface.co/Qwen/Qwen2-VL-7B" title="">https://huggingface.co/Qwen/Qwen2-VL-7B</a> |{{< /table-caption >}}
> 🔼 표 5는 InterFeedback-Bench 실험에 사용된 대규모 다중 모달 모델(LMM)의 출시 시점과 모델 소스를 보여줍니다.  각 모델의 이름, 출시일, 그리고 모델 정보를 얻을 수 있는 출처(주로 웹사이트 링크)를 제공하여, 사용된 LMM에 대한 상세한 정보를 제공합니다. 이는 본 논문의 재현성과 투명성을 높이기 위한 중요한 정보입니다.
> <details>
> <summary>read the caption</summary>
> Table 5: The release time and model source of LMMs used in our InterFeedback-Bench.
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