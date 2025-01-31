---
title: "Virus: Harmful Fine-tuning Attack for Large Language Models Bypassing Guardrail Moderation"
summary: "악의적인 미세 조정 공격으로부터 대규모 언어 모델(LLM)을 보호하는 가드레일의 한계를 밝히는 Virus 공격 기법 제시!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Georgia Institute of Technology",]
showSummary: true
date: 2025-01-29
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.17433 {{< /keyword >}}
{{< keyword icon="writer" >}} Tiansheng Huang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-30 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.17433" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.17433" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/virus-harmful-fine-tuning-attack-for-large" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

최근 연구는 대규모 언어 모델(LLM)이 악의적인 미세 조정 공격에 취약함을 보여주었습니다.  **악의적인 데이터**로 LLM을 재훈련하면 안전성이 저하될 수 있으며, 이는 서비스 제공업체에 심각한 위협이 됩니다. 따라서, 악의적인 데이터를 걸러내는 **가드레일**이 데이터 필터링에 사용되고 있습니다. 하지만, 이러한 가드레일만으로는 충분한 보안을 제공하지 못할 수 있습니다.

본 논문에서는 **Virus**라는 새로운 공격 기법을 제시합니다.  Virus는 악의적인 데이터를 약간 수정하여 가드레일을 우회하고 LLM의 안전성을 저하시키는 방법입니다. 실험 결과, Virus는 가드레일을 최대 100% 우회하며 동시에 공격 성능을 높였습니다. **이 연구는 가드레일만으로는 LLM의 안전성을 보장할 수 없다는 것을 강조**하며, 보다 강력한 보안 시스템 개발의 필요성을 시사합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 가드레일 방식의 LLM 보안 시스템이 **모든 악의적인 미세 조정 공격을 막을 수 없다**는 것을 보여줌 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} Virus 공격 기법이 가드레일을 우회하여 LLM의 안전성을 저해할 수 있음을 실험적으로 증명 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} **이중 목표 데이터 최적화 기법**을 통해 가드레일 우회 및 공격 효과를 동시에 달성하는 방법 제시 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대규모 언어 모델(LLM)**의 취약성을 보여주는 동시에, **안전한 LLM 개발 및 배포**에 대한 중요한 시사점을 제공합니다.  **보안 강화 및 안전한 LLM 사용**에 대한 연구 방향을 제시하며, 관련 분야 연구자들에게 중요한 자료가 될 것입니다.  특히, **가드레일 방식의 한계**를 지적하고, 이를 우회하는 공격 기법을 제시함으로써, **더욱 강력한 보안 시스템 개발**에 대한 필요성을 강조합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.17433/extracted/6163167/pic/virus.png)

> 🔼 그림 1은 Guardrail 완화 조치 하에서 악의적인 미세 조정 공격을 위한 3단계 파이프라인을 보여줍니다. 1단계에서는 정렬 데이터를 사용하여 모델이 안전하게 정렬됩니다. 2단계에서는 서비스 제공업체가 업로드된 미세 조정 데이터에서 악의적인 샘플을 걸러내기 위해 Guardrail 완화 조치를 적용합니다. 3단계에서는 필터링된 데이터를 사용하여 정렬된 LLM을 미세 조정합니다. 본 논문에서 제안하는 공격인 Virus는 Guardrail을 우회하고 피해자 LLM의 안전 정렬을 깨뜨릴 수 있는 사용자 데이터 세트를 구성하는 방법에 중점을 둡니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: A three stage pipeline for harmful fine-tuning attack under guardrail moderation. i) At the first stage, the model is safety aligned with alignment data. ii) At the second stage, the service provider applies guardrail moderation to filter out the harmful samples over the uploaded fine-tuning data. iii) At the third stage, the filtered data is used for fine-tuning the aligned LLM. Our attack Virus is concerning how to construct the user dataset that can bypass the guardrail and break the victim LLM’s safety alignment.
> </details>





{{< table-caption >}}
| Metrics\Methods | BFA | HFA | HFA w/o moderation |
|---|---|---|---| 
| Leakage ratio | 100% | 38% | 100% |
| Harmful score | 4.10 | 17.60 | 55.80 |{{< /table-caption >}}

> 🔼 이 표는 양성/악성 미세 조정 공격의 성능을 보여줍니다.  표에는 악성 데이터 비율(Harmful Ratio), 누출률(Leakage Ratio), 그리고 악성 점수(Harmful Score) 등의 지표가 포함되어 있습니다.  악성 데이터 비율은 미세 조정 데이터셋에서 악성 샘플이 차지하는 비율을 나타냅니다. 누출률은 보안 장벽(Guardrail)을 통과한 악성 샘플의 비율을 나타냅니다. 악성 점수는 미세 조정된 모델의 악의적인 행동 정도를 측정합니다.  표는 각 공격 방법(BFA, HFA, HFA w/o moderation)에 대한 이러한 지표들을 비교하여, 보안 장벽의 효과와 다양한 공격 방법의 성능 차이를 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Attack performance of benign/harmful fine-tuning attack. Attack methods are under guardrail moderation unless specified.
> </details>





### In-depth insights


#### Guardrail Bypass
본 논문에서 다룬 "Guardrail Bypass" 개념은 대규모 언어 모델(LLM)의 안전성을 강화하기 위해 사용되는 **보안 장치(Guardrail)**를 우회하는 공격 기법을 의미합니다.  **악의적인 미세 조정(Fine-tuning)** 공격을 통해 LLM의 안전 메커니즘을 무력화시키는 방법에 대한 연구입니다.  Guardrail은 유해한 데이터를 걸러내어 LLM의 학습에 사용되는 데이터의 품질을 관리하는 역할을 하지만, 이 연구는 **Guardrail이 완벽하지 않으며, 교묘하게 변형된 유해 데이터는 Guardrail을 우회하여 LLM에 악영향을 미칠 수 있음**을 보여줍니다.  이는 단순히 기술적 문제를 넘어, **LLM의 안전성에 대한 근본적인 질문**을 제기하며,  **안전한 LLM 개발 및 배포를 위한 새로운 접근 방식**의 필요성을 시사합니다.  **공격자의 데이터 조작 능력**과 **Guardrail의 한계**에 대한 심층적인 분석이 요구되며, 이를 통해 더욱 강력하고 안전한 Guardrail 및 방어 메커니즘 개발이 중요합니다.

#### Dual Goal Opt
논문에서 제시된 "Dual Goal Opt"는 **적대적 공격 성공률과 안전성 저하 사이의 균형**을 맞추는 데 초점을 맞춘, 새로운 데이터 최적화 기법을 의미합니다. 기존의 접근 방식들은 감시 시스템 우회에만 집중하여 실제 공격 성공률이 낮은 문제점을 가지고 있었습니다.  **Dual Goal Opt는 감시 시스템 우회와 동시에 대상 모델의 안전성을 크게 저하시키는 두 가지 목표를 동시에 달성**하는 것을 목표로 합니다. 이를 위해 감시 시스템을 속이는 손실 함수와, 공격 데이터의 그래디언트가 실제 유해 데이터의 그래디언트와 유사하도록 하는 손실 함수를 결합하여 최적화합니다.  **두 목표 간의 균형을 조절하는 하이퍼파라미터**를 통해,  **적대적 공격의 효과와 안전성 저하 사이의 최적점을 찾는** 것이 가능합니다.  이는 단순히 감시 시스템을 우회하는 것에 그치지 않고, **실제 공격 성공률을 높이는 동시에 모델의 안전성을 효과적으로 저하시키는 중요한 발전**으로 볼 수 있습니다.  **그래디언트 유사성**을 추가적인 목표로 설정함으로써, 감시 시스템 우회에 성공하더라도 안전성 저하 효과가 미미한 문제를 해결하고자 합니다. 따라서 Dual Goal Opt는 **실용적이고 효과적인 적대적 공격 기법**을 제시함으로써,  대규모 언어 모델의 안전성 향상에 대한 새로운 시각을 제시합니다.

#### Virus Attack
본 논문에서 제안된 바이러스 공격은 **대규모 언어 모델(LLM)**의 안전성을 위협하는 새로운 종류의 적대적 공격입니다. 이 공격은 **보안 장벽(guardrail)**을 우회하여 악의적인 미세 조정을 수행하는 방식으로 작동합니다.  **기존의 악의적인 미세 조정 공격은 보안 장벽에 의해 쉽게 탐지 및 차단되었지만**, 바이러스 공격은 악의적인 데이터를 약간 수정함으로써 보안 장벽을 우회합니다. 이를 통해 **높은 성공률로 악의적인 데이터를 삽입하여 LLM의 안전성을 저하시킬 수 있습니다.**  바이러스 공격의 주요 특징은 **이중 목표 데이터 최적화 기법**을 사용하는 것입니다. 이 기법은 보안 장벽을 우회하는 동시에 LLM의 안전성을 훼손하는 데 효과적입니다.  **실험 결과는 바이러스 공격이 최대 100%의 누출률을 달성하고 동시에 공격 성능을 크게 향상시킬 수 있음을 보여줍니다.**  이 연구는 LLM의 안전성에 대한 심각한 위협을 제기하며,  **보안 장벽에만 의존하는 것은 안전하지 않다**는 사실을 강조합니다. 따라서 LLM의 안전성을 보장하기 위한 더욱 강력한 방어 메커니즘의 개발이 시급합니다.

#### Grad Mismatch
본 논문에서 제기된 'Grad Mismatch' 가설은 **유해 데이터를 미세 조정 모델의 안전성을 저해하기 위해 최적화하는 과정에서 발생하는 중요한 문제**를 지적합니다.  단순히 가드레일을 우회하는 것만으로는 부족하며, **최적화된 데이터의 그래디언트가 원래의 유해 그래디언트와 상이해지면서 공격 성능이 저하**될 수 있다는 것입니다.  즉, 가드레일 우회에 성공하더라도, 그래디언트 불일치로 인해 **미세 조정 모델의 안전성이 유지되거나, 유해성이 충분히 감소되지 않는 현상**을 설명합니다. 이는 단순히 가드레일 우회만을 목표로 하는 기존 연구와 달리, **유해성 유지와 가드레일 우회라는 두 가지 목표**를 동시에 달성해야 하는 공격의 어려움을 보여줍니다. 따라서 **유해 데이터 최적화 전략은 가드레일 우회뿐 아니라, 원래 유해 데이터의 그래디언트와의 유사성 유지**에도 초점을 맞춰야 함을 시사합니다.  **Virus 공격 기법은 이러한 문제를 해결하기 위해 이중 목표 최적화를 도입**하여 가드레일 우회와 유해성 유지라는 두 가지 목표를 동시에 달성하고자 합니다.  결과적으로, 'Grad Mismatch'는 단순히 가드레일 우회를 넘어 **안전한 LLM 개발 및 보안 강화를 위한 중요한 설계 고려사항**임을 강조합니다.

#### Future Work
본 논문은 대규모 언어 모델(LLM)의 취약점을 보여주는 **Virus** 공격 기법을 제시하며, 이는 보안 강화 방안으로 사용되는 **방어 기제(guardrail)을 우회**하는 방법을 제시합니다. 따라서 향후 연구 방향은 **더욱 강력한 방어 메커니즘** 개발과 **공격의 다양성**에 대한 고찰입니다.  **Virus 공격의 한계점**을 극복하고, **다양한 유형의 방어 기제**에 대한 적응력을 높이는 방향으로 연구가 진행되어야 합니다. 또한, **실제 서비스 환경**에서의 공격 효과 및 대응 방안 연구가 필요하며, **LLM의 근본적인 안전성 문제** 해결을 위한 새로운 접근법 모색이 중요합니다.  **차세대 방어 기술**은  LLM의 구조적 취약성을 해결하거나,  공격에 대한 모델의 **내성을 강화**하는 방향으로 진행될 것입니다. 마지막으로 **윤리적 문제**에 대한 고려도 중요합니다. **악의적인 사용**을 막기 위한 기술적, 제도적 방안 마련이 필요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.17433/extracted/6163167/pic/HS_FS_hr.png)

> 🔼 그림 2는 유해 데이터 비율에 따른 유해 점수와 미세 조정 정확도를 보여줍니다. HFA는 유해 데이터 비율을 가진 유해 미세 조정 공격을 나타내고, BFA는 순수한 GSM8K 데이터를 사용한 양성 미세 조정 공격을 나타냅니다.  BF는 유해 비율이 0일 때 HFA의 특수한 경우입니다.  중재가 있는 HFA의 평균 누출 비율(유해 데이터의 누출 비율)은 0.348입니다. BFA의 모든 데이터는 중재를 통과합니다. 즉, 유해 데이터 비율이 증가할수록 유해 점수는 증가하지만 미세 조정 정확도는 크게 영향을 받지 않음을 보여줍니다. 중재는 유해 데이터의 일부만 걸러내므로 유해 점수를 완전히 낮추지는 못하지만, 여전히 유해 미세 조정 공격을 완화하는 효과가 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Harmful score and Fine-tune accuracy under different harmful ratio. HFA refers to harmful fine-tuning attack with a harmful ratio of harmful data. BFA refers to benign fine-tuning attack with pure GSM8K data. BF is a special case when harmful ratio=0 for HF. The average leakage ratio (ratio of leak-through harmful data) of HF w/ moderation is 0.348. All the data in BFA an leak through the moderation.
> </details>



![](https://arxiv.org/html/2501.17433/extracted/6163167/pic/example_figure.png)

> 🔼 그림 3은 다양한 미세 조정 공격 기법을 보여주는 예시 그림입니다. (a)는 정상적인 미세 조정 공격으로, 정상적인 질문과 답변 쌍을 미세 조정에 사용합니다. (b)는 악의적인 미세 조정 공격으로, 악의적인 샘플만을 사용합니다. (c)는 혼합 공격으로, 가드레일을 우회하기 위해 정상적인 질문과 답변에 악의적인 질문과 답변을 연결하지만, 성공적이지 못했습니다. (d)는 바이러스 기법으로, 정상적인 질문과 답변에 악의적인 질문과 답변을 연결하고, 악의적인 질문과 답변은 다음 두 가지 목표를 위해 최적화됩니다. 즉, 가드레일을 우회하고 공격 성능을 보장하는 것입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Example illustration of different fine-tuning attack techniques. a) For benign fine-tuning attack, benign QA pair is uploaded for fine-tuning. b) For harmful fine-tuning attack, only harmful samples are uploaded. c) For Mixing attack, a benign QA is concatenated with a harmful QA in order to circumvent guardrail, which unfortunately does not succeed. d) For Virus, the benign QA is concated with a harmful QA and the harmful QA is optimized with the dual goals: i) To bypass moderation. ii) To guarantee attack performance.
> </details>



![](https://arxiv.org/html/2501.17433/extracted/6163167/pic/statistic.png)

> 🔼 그림 4는 Virus 기법을 사용하여 최적화된 데이터를 사용하여 미세 조정 단계를 거칠 때, 다른 λ 값에 따라 손실 함수와 기울기 유사도가 미세 조정 라운드에 걸쳐 어떻게 변하는지 보여줍니다. λ=1인 경우, 해당 기법은 Guardrail Jailbreak이라는 실패 사례 중 하나로 귀결됩니다.  λ 값이 0에 가까울수록, 손실 함수는 감소하고 기울기 유사도는 높아지는 것을 확인할 수 있습니다. 이는 λ 값에 따라 Virus 기법의 성능과 안정성에 영향을 미치는 것을 보여줍니다.  특히, λ=1인 경우(Guardrail Jailbreak) 손실 함수가 충분히 감소하지 않고 오히려 증가하는 경향을 보이는데, 이는 최적화된 데이터의 기울기가 원래 데이터의 기울기와 크게 달라져서 모델의 안전성을 저해하지 못하기 때문입니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Stepping over the data optimized by Virus with different λ𝜆\lambdaitalic_λ, harmful loss and gradient similarity across fine-tuning rounds are displayed. When λ=1𝜆1\lambda=1italic_λ = 1, the method reduces to one of our failure attempt named guardrail jailbreak.
> </details>



![](https://arxiv.org/html/2501.17433/extracted/6163167/pic/onehot.png)

> 🔼 그림 5는 평탄화된 원-핫 벡터의 개념을 보여줍니다.  단어 집합(vocabulary)의 크기가 6이고, 최적화할 토큰의 수가 3이라고 가정합니다. 각 토큰 위치는 원-핫 벡터로 표현됩니다. 예를 들어, 첫 번째 토큰 위치는 'love' 단어를 나타내는 원-핫 벡터 [0, 0, 0, 0, 0, 1]로 표현되고, 두 번째 토큰 위치는 'you' 단어를 나타내는 원-핫 벡터 [0, 0, 0, 1, 0, 0]로 표현됩니다. 이러한 원-핫 벡터들은 연결되어 하나의 평탄화된 원-핫 벡터를 형성합니다. 이 그림은 본 논문에서 사용하는 원-핫 벡터 표현 방식을 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Illustration of flattened one-hot vector.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Metrics\Methods | HFA | Mixing | Mixing w/o moderation |
|---|---|---|---|
| Leakage ratio | 38% | 44% | 100% |
| Harmful score | 17.60 | 14.40 | 35.30 |{{< /table-caption >}}
> 🔼 표 2는 유해 미세 조정 공격(HFA)과 혼합 공격(Mixing)의 성능을 평가한 결과를 보여줍니다.  각 공격 방법에 대한 유해 점수(Harmful score)와 누출 비율(Leakage ratio)을 측정하여, 보호 장치(guardrail) 적용 유무에 따른 공격 성공률을 비교 분석합니다.  특히, 보호 장치가 적용된 경우(즉, 완화 기법이 적용된 경우) 공격 성공률에 어떤 영향을 미치는지 확인합니다.  표에서 BFA(Benign fine-tuning attack)는 기준선으로 사용되며, 보호 장치를 통과한 데이터의 비율과 유해 점수를 확인합니다. 이를 통해 보호 장치의 효과성과 공격 방법의 효율성을 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Evaluation of HFA/Mixing. Attack methods are under guardrail moderation unless specified.
> </details>

{{< table-caption >}}
| Metrics \Methods | HFA | Mixing | Guardrail Jailbreak |
|---|---|---|---|
| Gradient similarity | - | 1 | 0.826 |
| Leakage ratio | 38% | 44% | 100% |
| Harmful score | 17.60 | 14.40 | 14.10 |{{< /table-caption >}}
> 🔼 이 표는 경계선 무력화 설계의 평가 결과를 보여줍니다. 공격 방법은 경계선 조정을 거치지 않는 한 경계선 조정 하에서 수행됩니다. 최적화된 데이터의 그래디언트와 원래 혼합 데이터의 그래디언트 간의 유사성을 측정하기 위해 코사인 유사도를 사용합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Evaluation of guardrail jailbreak design. Attack methods are under guardrail moderation unless specified. We use cosine similarity to measure the similarity between the gradient of the optimizable data and the original mixing data.
> </details>

{{< table-caption >}}
| Metrics\Methods | Mixing | Guardrail Jailbreak | Only F<sub>2</sub> | Virus |
|---|---|---|---|---|
|  |  | (Only F<sub>1</sub>) |  |  |
| Grad similarity | 1 | 0.826 | 1 | **0.981** |
| Leakage ratio | 44% | 100% | 44% | **100%** |
| Harmful score | 14.40 | 14.10 | 14.00 | **30.40** |{{< /table-caption >}}
> 🔼 표 4는 Virus 기법의 성능 평가 결과를 보여줍니다.  각 공격 방법은 가드레일 모더레이션이 적용된 환경에서 평가되었으며,  최적화된 데이터의 기울기와 원래 혼합 데이터의 기울기 사이의 코사인 유사도를 측정하여 비교하였습니다.  표에는 각 기법의 유출 비율(Leakage ratio),  유해 점수(Harmful score),  기울기 유사도(Gradient similarity)가 표시되어 있습니다. 이를 통해 Virus 기법이 가드레일을 우회하고 공격 성능을 유지하는 데 효과적임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Evaluation of Virus design. Attack methods are under guardrail moderation unless specified. We use cosine similarity to measure the similarity between the gradient of the optimizable data and the original mixing data.
> </details>

{{< table-caption >}}
| Methods | p=0.01 | p=0.05 | p=0.1 | p=0.15 | p=0.2 | Average | p=0.01 | p=0.05 | p=0.1 | p=0.15 | p=0.2 | Average |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BFA | 4.10 | 4.10 | 4.10 | 4.10 | 4.10 | 4.10 | **32.00** | **32.00** | **32.00** | **32.00** | **32.00** | **32.00** |
| HFA | 3.20 | 9.30 | 17.60 | 20.20 | 26.20 | 15.30 | 27.50 | 27.40 | 29.00 | 29.70 | 29.70 | 28.66 |
| Mixing | 3.30 | 8.20 | 14.40 | 16.30 | 21.90 | 12.82 | 31.50 | 30.10 | 30.00 | 28.90 | 30.10 | 30.12 |
| Virus | **5.40** | **15.70** | **31.30** | **33.80** | **48.00** | **26.84** | 29.70 | 29.20 | 30.40 | 29.80 | 30.10 | 29.84 |{{< /table-caption >}}
> 🔼 표 5는 가드레일 조정 하에 다양한 공격 방법을 사용하여 유해 비율(p)을 다르게 했을 때의 평가 결과를 보여줍니다.  BFA(양성 파인튜닝 공격)의 통계는 유해 비율 p가 구현에 영향을 미치지 않기 때문에 모든 경우 동일합니다.  표는 각 공격 방법(BFA, HFA, Mixing, Virus)에 대한 유해 점수와 미세 조정 정확도를 유해 비율이 0.01, 0.05, 0.1, 0.15, 0.2일 때 각각 보여줍니다. 이를 통해 각 공격 방법의 효과와 유해 비율의 영향을 비교 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5:  Evaluation of different attack methods under guardrail moderation and different harmful ratio p𝑝pitalic_p. All the statistic of BFA for this table are the same because harmful ratio p𝑝pitalic_p does not affect its implementation.
> </details>

{{< table-caption >}}
| Methods | n=100 | n=200 | n=500 | n=800 | n=1000 | Average | n=100 | n=200 | n=500 | n=800 | n=1000 | Average |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| BFA | 2.20 | 2.90 | 4.10 | 4.70 | 5.60 | 3.90 | 22.20 | 26.90 | 32.00 | 31.80 | 36.20 | 29.82 |
| HFA | 3.10 | 5.60 | 17.60 | 24.70 | 31.80 | 16.56 | 22.20 | 27.20 | 29.00 | 32.70 | 33.20 | 28.86 |
| Mixing | 3.80 | 5.30 | 14.40 | 21.70 | 25.50 | 14.14 | 24.50 | 24.30 | 30.00 | 31.20 | 33.80 | 28.76 |
| Virus | 6.60 | 12.90 | 31.30 | 39.70 | 42.60 | 26.62 | 21.90 | 27.70 | 30.40 | 32.30 | 34.90 | 29.44 |{{< /table-caption >}}
> 🔼 이 표는 가드레일 모더레이션 하에서 다양한 공격 방법의 성능을 보여줍니다. 특히, 미세 조정 샘플의 개수(n)를 변경하면서 각 공격 방법의 유해 점수와 미세 조정 정확도를 비교 분석합니다.  다양한 샘플 수에 따른 공격 성공률과 모델 안전성 저하 정도를 파악하는 데 도움이 됩니다.  표에는 기준 방법(BFA, HFA)과 제안된 방법(Virus, Mixing)이 모두 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 6:  Evaluation of different attack methods under guardrail moderation and different number of fine-tune sample n𝑛nitalic_n.
> </details>

{{< table-caption >}}
| Methods | SST2 HS | SST2 FA | AgNews HS | AgNews FA | GSM8K HS | GSM8K FA | Average HS | Average FA |
|---|---|---|---|---|---|---|---|---|
| BFA | 2.20 | **93.69** | 1.30 | 79.30 | 4.10 | **32.00** | 2.53 | **68.33** |
| HFA | 13.40 | 92.78 | 13.90 | 54.00 | 17.60 | 29.00 | 14.97 | 58.59 |
| Mixing | 9.30 | **93.69** | 6.60 | **79.40** | 14.40 | 30.00 | 10.10 | 67.70 |
| Virus | **23.00** | 93.35 | **21.20** | 75.40 | **31.30** | 30.40 | **25.17** | 66.38 |{{< /table-caption >}}
> 🔼 본 표는 가드레일 조정이 적용된 환경에서 서로 다른 세 가지 미세 조정 작업(SST2, AGNEWS, GSM8K)에 대해 다양한 공격 방법(BFA, HFA, Mixing, Virus)의 성능을 평가한 결과를 보여줍니다.  각 방법의 유해 점수(Harmful Score)와 미세 조정 정확도(Finetune Accuracy)를 비교하여 가드레일 우회 공격의 효과를 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 7:  Evaluation of different attack methods under guardrail moderation and different fine-tuning tasks.
> </details>

{{< table-caption >}}
| Methods | Clocktime | GPU Memory |
|---|---|---|
| Only F<sub>1</sub> (λ=1) | 0.0828h | 34.37GB |
| Only F<sub>2</sub> (λ=0) | 0.2036h | 36.62GB |
| Virus | <span style="color:#FF0000;">0.2649h</span> | 39.68GB |{{< /table-caption >}}
> 🔼 표 8은 H100 GPU를 사용하여 Virus 공격 방법의 시스템 오버헤드를 평가한 결과를 보여줍니다.  세 가지 다른 방법(Only F1, Only F2, Virus)에 대한 GPU 메모리 사용량과 실행 시간을 비교하여 Virus 공격의 효율성과 실행 가능성을 보여줍니다. Only F1은 Guardrail Jailbreak loss만 최적화한 경우, Only F2는 Gradient Similarity loss만 최적화한 경우, Virus는 두 Loss를 모두 고려한 경우를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 8:  System evaluation for Virus on an H100.
> </details>

{{< table-caption >}}
| λ | 0 | 0.01 | 0.05 | 0.1 | 1 |
|---|---|---|---|---|---| 
| Gradient similarity | **1.000** | 0.9972 | 0.9840 | 0.9805 | 0.8264 |
| Leakage ratio | 44% | 66% | **100%** | **100%** | **100%** |
| Harmful score | 14.00 | 21.90 | 30.40 | **31.30** | 14.10 |
| Finetune accuracy | 30.10 | **30.70** | 29.60 | 30.40 | 27.10 |{{< /table-caption >}}
> 🔼 표 9는 하이퍼파라미터 λ의 영향을 보여줍니다. λ는 가드레일 탈옥 손실과 원래 혼합 데이터와의 기울기 유사성이라는 두 가지 목표 간의 절충을 제어하는 하이퍼파라미터입니다. 표는 λ의 다양한 값에 대한 기울기 유사도, 누출 비율, 유해 점수 및 미세 조정 정확도를 보여줍니다.  λ 값이 증가함에 따라 가드레일 탈옥 손실의 가중치가 커지고, 이로 인해 누출 비율과 유해 점수가 증가합니다. 그러나 λ가 너무 크면 원래 혼합 데이터와의 기울기 유사성이 감소하여 공격 성능이 저하됩니다.  미세 조정 정확도는 λ 값에 따라 다르지만, 일반적으로 상당한 영향을 받지 않습니다.
> <details>
> <summary>read the caption</summary>
> Table 9:  The impact of tradeoff hyper-parameter λ𝜆\lambdaitalic_λ.
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
{{< /gallery >}}