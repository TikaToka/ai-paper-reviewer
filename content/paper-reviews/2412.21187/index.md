---
title: "Do NOT Think That Much for 2+3=? On the Overthinking of o1-Like LLMs"
summary: "대규모 언어 모델의 과도한 연산 문제 해결: 효율적인 추론을 위한 새로운 지표 및 자기 학습 전략 제시"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Tencent AI Lab",]
showSummary: true
date: 2024-12-30
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.21187 {{< /keyword >}}
{{< keyword icon="writer" >}} Xingyu Chen et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-31 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.21187" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.21187" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/do-not-think-that-much-for-2-3-on-the" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

최근 뛰어난 추론 능력을 보이는 'o1-like' 대규모 언어 모델은 복잡한 문제에 대해서도 인간처럼 장시간 사고하는 능력을 갖추고 있지만, 간단한 문제에도 과도하게 많은 연산 자원을 사용하는 **'과도한 사고(overthinking)' 문제점**을 가지고 있습니다.  이로 인해 **계산 비용이 증가**하고 **모델의 효율성이 저하**될 수 있습니다. 



본 연구는 이러한 문제를 해결하기 위해 **새로운 효율성 평가 지표**를 개발하고, **자기 학습 방식**을 이용하여 모델의 추론 과정을 간소화하는 방법을 제시합니다. 실험 결과, 제시된 방법론은 다양한 난이도의 문제에서 모델의 정확도를 유지하면서 연산량을 **최대 48.6%까지 감소**시키는 효과를 보였습니다. 이는 대규모 언어 모델의 효율적인 개발 및 활용에 큰 기여를 할 것으로 기대됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 대규모 언어 모델의 과도한 추론(overthinking) 문제를 최초로 정량적으로 분석하고, 이를 해결하기 위한 두 가지 새로운 지표 (outcome efficiency, process efficiency)를 제시했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 자기 학습(self-training) 기반의 새로운 방법론을 통해, 모델의 정확도를 유지하면서 과도한 추론을 줄이는 데 성공했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 다양한 난이도의 문제 집합(GSM8K, MATH500 등)에 대한 실험 결과를 통해 제시된 방법론의 효과와 견고성을 검증했습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **과도한 연산 자원 사용**이라는 문제점을 해결함으로써, **대규모 언어 모델의 효율성을 높이는 데 크게 기여**할 수 있습니다.  특히, **단순 문제에 대한 과도한 추론 과정을 줄이는 전략**을 제시하여, 연구자들이 모델의 성능과 효율성을 동시에 개선할 수 있는 새로운 방향을 제시합니다.  이는 현재 급증하는 대규모 언어 모델의 비용 문제 해결에 중요한 단서를 제공하며, 향후 연구에 대한 새로운 가능성을 열어줄 것으로 기대됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.21187/icml2024/figure/overthinking.pdf)

> 🔼 그림 1은 간단한 문제 '2+3의 답은?'에 대해,  o1 유사 모델(오른쪽 패널)이 다른 모델들(왼쪽과 가운데 패널)보다 훨씬 많은 토큰을 사용하는 과잉 사고 문제를 보여줍니다.  왼쪽과 가운데 패널에는 기존의 대규모 언어 모델들이 표시되어 있으며, 이들은 문제 해결에 필요한 최소한의 토큰만을 사용합니다. 반면, 오른쪽 패널의 o1 유사 모델은 과도하게 많은 토큰을 생성하며, 이는 계산 과정을 반복하거나 불필요한 단계를 거치는 등 비효율적인 추론 과정을 나타냅니다.  이러한 과잉 사고는 계산 자원의 낭비로 이어질 수 있으며, 모델의 효율성을 저하시키는 요인으로 작용합니다. 그림은 이러한 과잉 사고 문제의 시각적 증거를 제시하고, 본 논문에서 다루는 핵심 문제를 명확히 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Illustration of over-thinking issue: o1-like models (right panel) spent much more tokens for a simple problem “what is the answer of 2+3?” than other models (left and middle panels).
> </details>





{{< table-caption >}}
| Models | Accuracy | Response |  | Efficiency |  |
|---|---|---|---|---|---| 
| **ASDIV** |  |  |  |  |  |
| Llama-3.3-70B-Instruct | 95.6 | 1.0 | 167.4 | 95.6% | 100.0% |
| Qwen2.5-Math-72B-Instruct | 96.3 | 1.0 | 209.6 | 96.3% | 100.0% |
| QwQ-32B-Preview | 96.2 | 3.6 | 712.9 | 41.8% | 66.4% |
| **GSM8K** |  |  |  |  |  |
| Llama-3.3-70B-Instruct | 92.6 | 1.0 | 235.4 | 92.6% | 100.0% |
| Qwen2.5-Math-72B-Instruct | 95.8 | 1.0 | 312.1 | 95.8% | 100.0% |
| QwQ-32B-Preview | 94.3 | 3.2 | 745.6 | 50.4% | 67.7% |
| **MATH500** |  |  |  |  |  |
| Llama-3.3-70B-Instruct | 75.4 | 1.0 | 575.0 | 75.4% | 100.0% |
| Qwen2.5-Math-72B-Instruct | 86.8 | 1.0 | 561.5 | 86.8% | 100.0% |
| QwQ-32B-Preview | 92.8 | 3.3 | 2409.2 | 52.2% | 72.4% |
| DeepSeek-R1-Preview | 93.4 | 2.8 | 2168.6 | 58.9% | 76.0% |{{< /table-caption >}}

> 🔼 표 1은 쉬운 데이터셋에 대한 주요 결과를 보여줍니다.  '추가 응답'은 모델이 정답을 생성한 후에 나오는 후속 응답을 의미합니다. 이 표는 모델의 효율성을 평가하기 위해, 정답을 생성하기까지 사용된 토큰 수, 정답을 생성하는 데 걸린 시간, 정답에 도달하기 전까지 생성된 추가적인 응답(추가적 사고 과정)의 개수 등을 보여줍니다. 이를 통해 단순한 문제에 대해서도 과도한 계산을 수행하는 오버싱킹 현상을 보다 명확하게 이해하고 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Main result for easy dataset. “Additional Response” denotes the suffix response after the model generates the correct answer.
> </details>





### In-depth insights


#### Overthinking in LLMs
LLM에서의 과도한 사고(Overthinking)는 모델이 간단한 문제에 대해서도 과도하게 많은 연산을 수행하는 현상을 말합니다. 이는 **정확도 향상에 거의 기여하지 않으면서** 계산 자원을 낭비하는 비효율적인 측면을 보여줍니다. 이러한 과도한 사고는 모델이 **다양한 해결 전략을 탐색하고 여러 단계의 검증을 거치는 과정**에서 발생하는데, 이는 인간의 사고 과정을 모방하려는 시도의 부작용으로 볼 수 있습니다.  **단순 문제에 과도한 연산을 적용**하는 것은 자원 낭비일 뿐만 아니라, 모델의 효율성을 저하시키는 주요 원인이 됩니다. 따라서, LLM의 효율성을 높이기 위해서는 이러한 과도한 사고를 줄이는 전략이 필요하며, **정확도를 유지하면서 연산량을 줄이는 방안**을 모색해야 합니다.  이를 위해서는 과도한 사고를 측정하고 완화하는 새로운 지표 개발과 효율적인 학습 방법 연구가 중요합니다.

#### Efficiency Metrics
본 논문에서 제시된 효율성 지표는 단순히 정확도만을 평가하는 기존 방식에서 벗어나 **계산 자원의 효율적인 사용** 여부를 다각적으로 평가하고자 하는 시도입니다.  **결과(Outcome)** 및 **과정(Process)** 두 가지 관점에서 지표를 제시하여, 모델이 문제 해결에 필요한 계산량을 얼마나 효율적으로 사용하는지 측정합니다. 예를 들어, 단순한 문제에 과도한 계산을 수행하는 '과잉 사고(Overthinking)' 현상을 탐지하고, 이를 정량적으로 평가할 수 있는 지표를 제공합니다. 이는 단순히 정답률이 높은 것만이 아니라, **문제의 복잡도에 맞는 적절한 계산 자원을 활용하는 모델**을 평가하는 데 중요한 의미를 가집니다.  **새로운 효율성 지표**의 도입은 단순히 모델 성능 비교를 넘어, 모델의 '지능'을 평가하는 새로운 차원을 열어줄 가능성을 제시합니다.

#### Mitigating Overthinking
본 논문의 "과도한 추론 완화" 부분은 **대규모 언어 모델(LLM)의 과도한 계산 자원 사용 문제**를 해결하기 위한 다양한 전략을 제시합니다.  이는 단순한 문제에 대해서도 불필요하게 많은 연산을 수행하는 LLM의 경향을 다룹니다.  **자기 학습 패러다임**을 활용하여 모델이 불필요한 추론 단계를 줄이도록 유도하고, 이를 통해 정확도를 유지하면서 계산 비용을 절감하는 방법을 제시합니다.  **새로운 효율성 지표**를 통해 모델의 성능을 다각적으로 평가하고, 이를 기반으로 여러 전략들을 비교 분석합니다.  **최적 길이 조정 및 응답 단순화** 와 같은 구체적인 방법들을 제시하며, 실험 결과를 통해 이러한 방법들이 과도한 추론 문제를 효과적으로 완화하고 성능을 향상시킨다는 것을 보여줍니다.  이는 **효율적인 LLM 설계 및 활용**에 중요한 시사점을 제공합니다.

#### Self-Training Paradigm
자기훈련 패러다임은 **데이터 효율성** 및 **모델 성능 향상**이라는 두 가지 주요 목표를 달성하기 위해 **제한된 자원** 내에서 **최적의 성능**을 얻고자 하는 머신러닝 접근법입니다.  **부족한 레이블 데이터** 문제를 해결하기 위해, 자기훈련은 모델이 스스로 예측한 결과를 이용하여 추가적인 학습 데이터를 생성합니다. 이는 **데이터 증강**의 효과를 가지며, **일반화 성능** 향상에 기여할 수 있습니다.  그러나 **잘못된 예측**에 기반한 데이터는 오히려 모델의 성능을 저하시킬 수 있다는 점에 유의해야 합니다. 따라서 **신뢰할 수 있는 예측**만을 사용하거나, **예측의 신뢰도**를 고려하는 메커니즘을 도입하는 것이 중요합니다.  **자기훈련의 효과**는 모델의 복잡도, 데이터의 질, 그리고 자기훈련 과정의 설계에 따라 크게 달라질 수 있습니다. **성능 평가**를 위한 엄격한 기준을 설정하고, **과적합**을 방지하기 위한 전략을 수립하는 것이 자기훈련 패러다임을 성공적으로 적용하는 데 중요한 요소입니다. 효율적인 자기훈련은 **모델의 학습 과정**을 개선하고 **실제 응용 분야**에서의 성능을 향상시키는 데 크게 기여할 수 있습니다.

#### Future Research
본 논문은 과도한 추론(overthinking) 문제를 다루는 흥미로운 연구이지만, **여전히 해결해야 할 과제가 많이 남아있다**.  미래 연구는 **더 다양한 o1-like 모델에 대한 연구 확장**을 통해 일반화 가능성을 높이고, 더욱 효율적인 **다양성 측정 방법** 개발 및 **더 큰 규모의 데이터셋 활용**을 통해 견고성을 강화하는 데 집중해야 한다. 특히, **적응적 컴퓨팅 전략** 개발은 **문제의 복잡성에 따라 컴퓨팅 자원을 동적으로 조절**하여 효율성을 극대화하는 데 중요하며, **모델의 추론 과정을 보다 투명하고 이해하기 쉽게 만드는 연구**도 필요하다.  **다양한 모델 아키텍처와 추론 전략 간의 상호작용 연구**도 중요한 방향이며, 최종적으로는 **실제 응용 분야에서의 효율성과 성능을 평가하는 실험**이 중요한 다음 단계가 될 것이다. 이를 통해 과도한 추론 문제를 효과적으로 해결하고, o1-like 모델의 효율성과 실용성을 높일 수 있는 발전적인 연구가 기대된다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.21187/icml2024/figure/case_overview.pdf)

> 🔼 그림 2는 QwQ-32B-Preview 모델이 2+3=? 와 같은 간단한 수학 문제에 대해 13가지의 서로 다른 풀이과정을 제시하는 과잉 사고(overthinking) 현상을 보여주는 예시입니다.  각 풀이 과정은 모델이 생성한 토큰 수를 함께 표시하여,  불필요하게 많은 연산을 수행했음을 보여줍니다.  비교를 위해 기존의 다른 대규모 언어 모델(LLM)들의 답변도 함께 제시되어 있습니다.  이 그림은 모델이 단순한 문제에도 과도하게 복잡한 풀이를 시도하는 경향을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: An example of overthinking issue for QwQ-32B-Preview model’s output response that consists of 13 solutions. We also list the outputs of other conventional LLMs for reference.
> </details>



![](https://arxiv.org/html/2412.21187/icml2024/figure/count_distribution.pdf)

> 🔼 그림 3은 다양한 모델과 데이터셋에서 생성된 응답에 포함된 해의 개수 분포를 보여줍니다. 막대 그래프는 각 모델(QwQ-32B-Preview와 DeepSeek-R1-Preview)이 ASDIV, GSM8K, MATH500 데이터셋의 문제에 대해 생성한 응답에서 해의 개수 비율을 나타냅니다. 이를 통해 각 모델이 문제의 복잡도에 따라 서로 다른 수의 해를 생성하는 경향이 있음을 보여줍니다. 예를 들어, QwQ-32B-Preview 모델은 ASDIV 데이터셋에서는 평균 3.6개의 해를 생성하지만 MATH500 데이터셋에서는 평균 2.8개의 해를 생성합니다. 이는 더 쉬운 문제일수록 더 많은 해를 생성하는 과잉 사고(overthinking) 현상을 보여주는 것입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Distribution of solution number in the responses.
> </details>



![](https://arxiv.org/html/2412.21187/icml2024/figure/first_answer_distribution.pdf)

> 🔼 그림 4는 추가적인 솔루션 라운드가 정확도 향상에 거의 기여하지 않는다는 것을 보여줍니다.  더 자세히 설명하자면, 이 그림은 다양한 난이도의 문제에 대해 모델이 생성한 솔루션의 수와 해당 솔루션이 정답에 도달하는데 기여한 정도를 보여줍니다.  그림에서 알 수 있듯이, 초기 솔루션 라운드에서 이미 정답이 도출되는 경우가 많으며, 추가적인 솔루션은 정확도 향상에 미미한 영향을 미칩니다.  이는 모델이 간단한 문제에 대해 과도하게 생각하는 경향(overthinking)을 보이는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Additional rounds of solutions marginally contribute to accuracy improvement.
> </details>



![](https://arxiv.org/html/2412.21187/icml2024/figure/distinctness_ratio.pdf)

> 🔼 그림 5는 후속 라운드의 솔루션이 이전 라운드의 솔루션을 반복할 가능성이 더 높다는 것을 보여줍니다. 이는 모델이 새로운 통찰력을 제공하기보다는 기존 아이디어를 반복하는 경향이 있음을 시사합니다.  이러한 반복은 계산 자원의 비효율적인 사용으로 이어질 수 있으며, 모델의 효율성을 저해하는 과잉 사고의 징후일 수 있습니다.  그림은 다양한 데이터 세트(ASDIV, GSM8K, MATH500)와 모델(QwQ-32B-Preview, DeepSeek-R1-Preview)에 걸쳐 첫 번째 정답이 나타나는 솔루션 라운드의 분포를 보여줍니다. 초기 라운드에서 정답이 나올 확률이 매우 높고, 후속 라운드는 정확도 향상에 거의 기여하지 않는다는 것을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Subsequent rounds of solutions are more prone to repetition of earlier ones.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Methods | Accuracy | Whole Response Round | Whole Response Token | Additional Response Round | Additional Response Token |
|---|---|---|---|---|---| 
| **_ASDIV_** |  |  |  |  |  |
| Llama-3.3-70B-Instruct | 95.6 |  | 167.4 |  |  |
| Llama-3.1-405B-Instruct | 95.2 |  | 127.0 |  |  |
| Qwen2.5-Math-7B-Instruct | 96.2 |  | 206.8 |  |  |
| Qwen2.5-Math-72B-Instruct | 96.3 |  | 209.6 |  |  |
| QwQ-32B-Preview | 96.2 | 3.5 | 697.9 | 2.5 | 408.3 |
| +SFT<sub>Response</sub> | 95.7 |  | 647.8 |  |  |
| +DPO<sub>Response</sub> | 96.6 | 2.9 | 523.7 | 1.9 | 253.4 |
| +RPO<sub>Response</sub> | 96.5 | 3.0 | 524.0 | 2.0 | 255.5 |
| +SimPO<sub>Response</sub> | 95.7 |  | 506.0 |  |  |
| +SimPO<sub>Solution</sub> | 96.2 | 1.2 | 270.4 | 0.2 | 19.3 |
| **_GSM8K_** |  |  |  |  |  |
| Llama-3.3-70B-Instruct | 92.6 |  | 235.4 |  |  |
| Llama-3.1-405B-Instruct | 95.6 |  | 186.7 |  |  |
| Qwen2.5-Math-7B-Instruct | 95.5 |  | 305.9 |  |  |
| Qwen2.5-Math-72B-Instruct | 95.8 |  | 312.1 |  |  |
| QwQ-32B-Preview | 94.3 | 3.2 | 738.1 | 2.1 | 376.4 |
| +SFT<sub>Response</sub> | 94.5 | 3.0 | 689.0 | 1.9 | 324.0 |
| +DPO<sub>Response</sub> | 94.6 | 2.6 | 573.9 | 1.5 | 223.0 |
| +RPO<sub>Response</sub> | 94.5 | 2.6 | 564.5 | 1.5 | 216.6 |
| +SimPO<sub>Response</sub> | 94.5 |  | 537.6 |  |  |
| +SimPO<sub>Solution</sub> | 94.3 | 1.1 | 327.9 | 0.0 | 4.6 |
| **_MATH500_** |  |  |  |  |  |
| Llama-3.3-70B-Instruct | 75.4 |  | 575.0 |  |  |
| Llama-3.1-405B-Instruct | 72.0 |  | 470.3 |  |  |
| Qwen2.5-Math-7B-Instruct | 84.2 |  | 609.5 |  |  |
| Qwen2.5-Math-72B-Instruct | 86.8 |  | 561.5 |  |  |
| QwQ-32B-Preview | 92.8 | 3.2 | 2102.1 | 2.2 | 740.9 |
| +SFT<sub>Response</sub> | 92.4 | 3.0 | 2097.0 | 1.9 | 683.0 |
| +DPO<sub>Response</sub> | 92.8 | 2.8 | 1676.0 | 1.8 | 475.5 |
| +RPO<sub>Response</sub> | 92.6 | 2.7 | 1756.5 | 1.6 | 461.0 |
| +SimPO<sub>Response</sub> | 92.4 |  | 1847.7 |  |  |
| +SimPO<sub>Solution</sub> | 91.6 | 1.4 | 1032.1 | 0.2 | 77.0 |{{< /table-caption >}}
> 🔼 표 2는 쉬운 데이터셋에 대한 주요 결과를 보여줍니다. 표는 다양한 모델이 쉬운 수학 문제를 푸는 데 사용한 토큰 수와 정답률을 비교합니다. '추가 응답' 열은 모델이 정답을 생성한 후 추가적으로 생성한 응답을 나타냅니다. 이는 모델의 과도한 추론(overthinking) 경향을 파악하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Main result for easy dataset. “Additional Response” denotes the suffix response after the model generates the correct answer.
> </details>

{{< table-caption >}}
| Methods | Accuracy | Whole Response Round | Whole Response Token | Additional Response Round | Additional Response Token |
|---|---|---|---|---|---| 
| **AIME90** |  |  |  |  |  |
| Llama-3.3-70B-Instruct | 26.7 |  | 956.7 |  |  |
| Llama-3.1-405B-Instruct | 22.2 |  | 1099.9 |  |  |
| Qwen2.5-Math-7B-Instruct | 10.0 |  | 1109.8 |  |  |
| Qwen2.5-Math-72B-Instruct | 16.7 |  | 955.4 |  |  |
| QwQ-32B-Preview | 37.8 | 2.0 | 5879.8 | 0.7 | 392.4 |
|      +SFT<sub>Response</sub> | 42.2 | 1.8 | 5972.3 | 0.5 | 350.1 |
|      +DPO<sub>Response</sub> | 38.9 | 1.7 | 5945.8 | 0.5 | 309.2 |
|      +RPO<sub>Response</sub> | 38.9 | 1.8 | 5904.0 | 0.6 | 316.1 |
|      +SimPO<sub>Response</sub> | 33.3 |  | 6814.4 |  |  |
|      +SimPO<sub>Solution</sub> | 28.9 | 1.6 | 3750.3 | 0.1 | 12.7 |
| **GPQA** |  |  |  |  |  |
| Llama-3.3-70B-Instruct | 42.4 |  | 831.5 |  |  |
| Llama-3.1-405B-Instruct | 53.5 |  | 604.3 |  |  |
| Qwen2.5-Math-7B-Instruct | 31.8 |  | 762.0 |  |  |
| Qwen2.5-Math-72B-Instruct | 46.5 |  | 682.7 |  |  |
| QwQ-32B-Preview | 58.6 | 2.5 | 3098.1 | 0.8 | 484.8 |
|      +SFT<sub>Response</sub> | 53.5 | 2.2 | 2917.9 | 0.9 | 473.8 |
|      +DPO<sub>Response</sub> | 58.6 | 2.3 | 2775.3 | 0.7 | 347.7 |
|      +RPO<sub>Response</sub> | 56.1 | 2.3 | 2675.5 | 0.8 | 415.8 |
|      +SimPO<sub>Response</sub> | 57.6 |  | 2713.3 |  |  |
|      +SimPO<sub>Solution</sub> | 56.1 | 1.9 | 1726.0 | 0.3 | 97.3 |{{< /table-caption >}}
> 🔼 표 3은 어려운 데이터셋에 대한 주요 결과를 보여줍니다.  '추가 응답'은 모델이 정답을 생성한 후 추가적으로 생성된 응답을 의미합니다. 이 표는 모델이 문제를 해결하는 데 사용한 솔루션 수, 토큰 수, 결과 효율성(정답 도출 효율성 및 과정 효율성) 등을 보여줍니다.  어려운 문제에 대해 모델의 효율성을 평가하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Main result for hard dataset. “Additional Response” denotes the suffix response after the model generates the correct answer.
> </details>

{{< table-caption >}}
| Methods | Accuracy | Whole Response Token | Whole Response Round | Additional Response Round | Additional Response Token |
|---|---|---|---|---|---| 
| **GSM8K** |  |  |  |  |  |
| QwQ-32B-Preview | 94.3 |  | 772.8 |  |  |
| +SFT | 94.5 |  | 723.8 |  |  |
| +DPO | 94.6 |  | 595.8 |  |  |
| +RPO | 94.5 |  | 583.9 |  |  |
| **ASDIV** |  |  |  |  |  |
| QwQ-32B-Preview | 95.7 |  | 741.8 |  |  |
| +SFT | 95.4 |  | 728.5 |  |  |
| +DPO | 96.1 |  | 591.1 |  |  |
| +RPO | 96.1 |  | 595.7 |  |  |
| **MATH500** |  |  |  |  |  |
| QwQ-32B-Preview | 92.8 |  | 2407.9 |  |  |
| +SFT | 92.4 |  | 2347.2 |  |  |
| +DPO | 92.8 |  | 1937.4 |  |  |
| +RPO | 92.6 |  | 2039.2 |  |  |
| **AIME90** |  |  |  |  |  |
| QwQ-32B-Preview | 37.8 |  | 8241.2 |  |  |
| +SFT | 42.2 |  | 7960.1 |  |  |
| +DPO | 38.9 |  | 6880.5 |  |  |
| +RPO | 38.9 |  | 7365.6 |  |  |
| **GPQA** |  |  |  |  |  |
| QwQ-32B-Preview | 58.6 |  | 3228.4 |  |  |
| +SFT | 53.5 |  | 3665.8 |  |  |
| +DPO | 58.6 |  | 3075.2 |  |  |
| +RPO | 56.1 |  | 2855.0 |  |  |{{< /table-caption >}}
> 🔼 표 4는 긍정적 및 부정적 예시 선택 전략에 대한 비교 결과를 보여줍니다. SFT(Supervised Fine-Tuning)의 경우 미세 조정을 위해 긍정적 예시를 사용하며, 긍정적 예시는 QwQ 모델의 가장 짧은 샘플링 응답을, 부정적 예시는 QwQ 모델의 가장 긴 샘플링 응답을 사용합니다. 이 표는 다양한 방법(SFT, DPO, RPO, SimPO)으로 생성된 응답의 정확도, 솔루션 수, 토큰 수, 결과 효율성, 프로세스 효율성을 비교 분석하여 각 전략의 효율성을 평가합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Comparison about positive and negative example selection strategy. For SFT, we use positive example for finetuning. Positive examples: shortest response: shortest sampling response of QwQ model. Negative examples: longest response: longest sampling response of QwQ model.
> </details>

{{< table-caption >}}
| Methods | MATH500 | GPQA | AIME | Avg. |
|---|---|---|---|---|
| **Industrial Model** |  |  |  |  |
| GPT4 |  |  |  |  |
| OpenAI-O1 |  |  |  |  |
| **Open Source Model** |  |  |  |  |
| Llama3.1-8B-Instruct | 49.0 | 17.7 | 6.7 |  |
| Llama3.1-70B-Instruct | 67.8 | 39.9 | 23.3 |  |
| Llama3.1-405B-Instruct |  |  |  |  |
| Qwen2.5-Math-7B-Instruct | 84.2 | 31.8 | 20 |  |
| Qwen2.5-Math-72B-Instruct | 86.8 | 46.5 | 20 |  |
| QwQ-32B-Preview | 92.8 | 58.6 | 46.7 |  |
| Ours-QwQ-32B-Preview |  |  |  |  |{{< /table-caption >}}
> 🔼 표 5는 제안된 방법이 모든 기준 방법보다 우수하며 새로운 최첨단 기술을 달성했음을 보여줍니다.  표는 다양한 벤치마크 데이터셋(ASDIV, GSM8K, MATH500, GPQA, AIME)에 대한 정확도, 솔루션 수, 토큰 수, 결과 효율성 및 프로세스 효율성을 비교 분석합니다.  * 표시는 p<0.005의 유의 수준에서 통계적으로 유의미한 향상을 나타냅니다. 즉, 제안된 방법이 기존 방법보다 상당히 성능이 뛰어나다는 것을 의미합니다. 이 표를 통해 본 논문에서 제시된 방법의 효과와 일반화 성능을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Our proposed methods outperform all baseline methods and achieve a new state-of-the-art. *denotes the results are significantly better with p<0.005𝑝0.005p<0.005italic_p < 0.005.
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
{{< /gallery >}}