---
title: "LongDPO: Unlock Better Long-form Generation Abilities for LLMs via Critique-augmented Stepwise Information"
summary: "LongDPO는 단계별 감독과 외부 비평을 활용하여 장문 생성 능력을 향상시킨 새로운 방법론입니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Peking University",]
showSummary: true
date: 2025-02-04
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.02095 {{< /keyword >}}
{{< keyword icon="writer" >}} Bowen Ping et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-04 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.02095" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.02095" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 장문 생성 모델들은 길이 편차, 품질 저하 등의 문제를 가지고 있습니다. 이는 **결과 중심 감독(outcome supervision)**만으로는 세부적인 피드백을 제공하기 어렵기 때문입니다.  기존 방법들은 충분한 맥락 정보를 제공하지 못하여 질의 요구사항을 완전히 충족시키지 못하는 경우가 많았습니다.

본 논문에서는 **과정 중심 감독(process supervision)**을 이용한 LongDPO를 제안합니다. LongDPO는 Monte Carlo Tree Search(MCTS)를 사용하여 단계별 선호도 쌍을 수집하고, 외부 비평을 통합하여 선호도 쌍의 질을 높입니다.  **단계별 DPO(step-level DPO)**를 통해 모델을 학습시켜, 장문 생성 벤치마크에서 길이 및 품질을 향상시키고 일반적인 벤치마크에서는 성능 저하 없이 유지했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} LongDPO는 **단계별 감독(process supervision)**을 통해 장문 생성 모델의 성능을 향상시켰습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} **MCTS와 외부 비평(external critiques)**을 활용하여 품질 높은 단계별 선호도 쌍(stepwise preference pairs)을 수집하는 전략을 제시했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 다양한 모델 백본에서 거의 손실 없는 성능으로 **장문 생성 벤치마크에서 성능을 향상**시켰습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **장문 생성의 어려움을 해결하기 위한 새로운 방법론인 LongDPO를 제시**하여, 기존의 한계를 극복하고 더욱 향상된 성능을 달성했습니다.  **단계별 감독(process supervision)을 도입**하여 모델의 학습 과정을 개선하고, **외부 비평(external critiques)을 활용**하여 생성 품질을 높였습니다. 이는 장문 생성 분야 연구에 중요한 영향을 미칠 뿐 아니라, 다양한 모델 백본에 적용 가능하여 실용성이 높다는 점에서 큰 의의가 있습니다.  향후 장문 생성 모델 연구 방향을 제시하며, 다양한 응용 분야에 활용될 수 있는 잠재력을 가지고 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.02095/x1.png)

> 🔼 그림 1은 장문 생성 작업에서의 결과 감독(outcome supervision)과 장문 생성을 위한 제안된 방법인 LongDPO의 과정 감독(process supervision)을 비교하여 보여줍니다.  상단은 기존의 결과 감독 방식으로, 모델이 생성한 최종 결과물에 대한 평가만을 기반으로 학습합니다. 반면 하단의 LongDPO는, 몬테 카를로 트리 탐색(MCTS)을 사용하여 단계별로 선호도 쌍(preference pairs)을 수집하고, 전역 메모리(global memory)를 활용하여 사실적 일관성을 유지합니다.  또한, 낮은 보상을 받은 후보들을 외부 비평(external critiques)을 통해 개선하여, 더욱 정확하고 질 높은 선호도 쌍을 확보합니다.  즉, LongDPO는 단순히 최종 결과물뿐만 아니라 생성 과정 전반에 대한 피드백을 활용하여 장문 생성 능력을 향상시키는 것을 목표로 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  The above is outcome supervision in long-form generation tasks. Below is LongDPO uses process supervision with a global memory to maintain factual consistency, and external critiques to refine low-reward chosen candidates.
> </details>





{{< table-caption >}}
| Models | [0, 500) S<sub>l</sub> | [0, 500) S<sub>q</sub> | [500, 2k) S<sub>l</sub> | [500, 2k) S<sub>q</sub> | [2k, 4k) S<sub>l</sub> | [2k, 4k) S<sub>q</sub> | [4k, 20k) S<sub>l</sub> | [4k, 20k) S<sub>q</sub> | Average S<sub>l</sub> | Average S<sub>q</sub> |
|---|---|---|---|---|---|---|---|---|---|---|
| **LongWriter-Llama** | 88.10 | 86.00 | 74.50 | 86.90 | 89.10 | 88.30 | 80.80 | 79.20 | 83.12 | 85.10 |
|   <em>w/ DPO</em> | 90.93 | 85.78 | 76.67 | 85.46 | 90.01 | 90.53 | 81.07 | 80.90 | 85.55 | 85.66 |
|   <em>w/ LongDPO</em> | 90.68 | 86.27 | 77.23 | 91.25 | 93.35 | 90.53 | 88.25 | 85.06 | 87.38 | 88.28 |
| **LongWriter-Qwen** | 90.80 | 87.99 | 84.37 | 89.37 | 84.21 | 84.84 | 58.69 | 78.13 | 79.51 | 85.08 |
|   <em>w/ DPO</em> | 86.32 | 88.23 | 88.71 | 89.16 | 89.28 | 84.09 | 60.89 | 78.82 | 81.30 | 85.07 |
|   <em>w/ LongDPO</em> | 88.93 | 91.91 | 85.47 | 91.25 | 88.63 | 85.60 | 71.14 | 85.41 | 83.54 | 88.54 |{{< /table-caption >}}

> 🔼 표 1은 LongBench-Write-en 데이터셋을 사용한 실험 결과를 보여줍니다. LongWriter-Llama는 LongWriter-llama-8B 모델을, LongWriter-Qwen은 LongWriter-Qwen2.5-7B 모델을 나타냅니다. 제안된 방법은 네 가지 출력 길이 범위에서 성능을 향상시키며, 특히 4K를 초과하는 출력에서 성능 향상이 두드러집니다. 재현성을 확보하기 위해 난수 시드를 설정했습니다.  즉,  다양한 길이의 텍스트 생성 작업에서 제안된 방법(LongDPO)의 성능 향상을 보여주는 표입니다. 특히 긴 텍스트 생성에서의 성능 향상이 눈에 띄는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Evaluation results on LongBench-Write-en. LongWriter-Llama and LongWriter-Qwen represent LongWriter-llama-8B and LongWriter-Qwen2.5-7B, respectively. Our method improves performance across four output length ranges, particularly for outputs exceeding 4K. We have set a random seed to ensure reproducibility.
> </details>





### In-depth insights


#### Long-Form LLMs
장문 생성 능력은 학술 논문 작성이나 코드 생성과 같은 다양한 분야에서 매우 중요합니다. 하지만 기존의 대형 언어 모델(LLM)들은 **길이 제한**이나 **품질 저하** 문제로 장문 생성에 어려움을 겪고 있습니다. 이는 주로 결과 중심의 지도 학습 방식의 한계 때문입니다. 본 논문에서는 이러한 문제를 해결하기 위해 **과정 중심의 지도 학습**을 제안합니다.  **단계별 선호도 쌍**을 생성하고, 이를 통해 모델이 장문 생성 과정에서 일관성을 유지하고 품질을 향상시킬 수 있도록 돕습니다.  **몬테 카를로 트리 탐색(MCTS)**과 **외부 비평**을 활용하여 보다 효율적이고 효과적인 학습을 가능하게 합니다.  실험 결과, 제안된 방법은 다양한 모델에서 장문 생성 성능을 크게 향상시켰으며, 일반적인 벤치마크에서도 성능 저하 없이 작동하는 것을 보여줍니다.  **전반적으로, 본 논문은 LLM의 장문 생성 능력을 향상시키는 새로운 접근 방식을 제시하며, 향후 연구 방향을 제시하는 중요한 의미를 가집니다.**

#### Stepwise Supervision
본 논문에서 제안하는 단계적 감독(Stepwise Supervision)은 기존의 결과 중심 감독(Outcome Supervision)의 한계를 극복하기 위한 핵심 전략입니다.  **장문 생성 과정을 여러 단계로 나누어 각 단계별 피드백을 제공함으로써, 최종 결과물의 질 향상은 물론, 과정의 일관성 및 응집력을 높이는 데 기여**합니다.  이는 마치 건물을 짓는 과정에 비유할 수 있는데, 결과 중심 감독은 완성된 건물만 평가하는 반면, 단계적 감독은 기초 공사부터 마감까지 각 단계를 꼼꼼히 검토하고 수정하는 방식입니다.  **단계별 선호도 쌍(Preference Pairs)을 수집하기 위해 Monte Carlo Tree Search(MCTS)를 활용하여 효율성을 높였으며, 글로벌 메모리 풀(Global Memory Pool)을 통해 일관성을 유지**합니다.  또한, **외부 비평(External Critiques)을 통합하여 후보 선택의 질을 개선하고, 단계별 DPO(Direct Preference Optimization)를 적용하여 학습 효율을 극대화**했습니다.  이러한 다층적 접근 방식을 통해, 단순히 길이만 늘리는 것이 아니라 내용의 질과 일관성까지 고려한 진정한 의미의 장문 생성 능력 향상을 도모하는 것입니다.

#### MCTS for DPO
본 논문에서 제안하는 MCTS 기반 DPO 방법은 **장문 생성 과정의 단계별 피드백을 효과적으로 활용**하여 기존의 결과 중심 방식의 한계를 극복하고자 합니다.  MCTS를 통해 단계별 선호도 쌍을 수집함으로써, 모델이 장문 생성 과정의 각 단계에서 올바른 방향으로 나아가도록 유도합니다.  **전역 메모리 풀을 활용한 일관성 유지** 및 **외부 비평 통합**은 생성된 텍스트의 질적 향상에 기여하며, 이를 통해 **길이 편차 감소 및 품질 개선** 효과를 기대할 수 있습니다.  MCTS 기반 DPO는 단순히 최종 결과만을 평가하는 것이 아니라, **과정 전반에 걸친 세밀한 평가**를 통해 장문 생성 능력의 향상을 도모하는 핵심 전략임을 알 수 있습니다.  **단계별 DPO**를 통한 미세 조정은 기존의 결과 중심 접근 방식에 비해 **더욱 효과적이고 안정적인 학습**을 가능하게 할 것으로 예상됩니다.

#### Critique Refinement
본 논문에서 제안하는 'Critique Refinement'는 단순히 비판을 수용하는 것을 넘어, **LLM의 장문 생성 능력 향상**에 중요한 역할을 합니다.  MCTS(Monte Carlo Tree Search)를 통해 생성된 후보 답변 중 낮은 보상을 받은 것들에 대해 **외부 비판**을 통합하여 질을 개선하는 전략입니다.  **자기 비판만으로는 불안정한 성능 향상**을 초래할 수 있으므로, 외부 전문가 지식을 활용한 비판은 안정적이고 효과적인 개선을 가져옵니다. 이러한 과정은 **단계별 감독(stepwise supervision)**의 핵심 요소로, 최종 결과에 대한 평가만이 아닌 생성 과정 전반의 질적 향상을 이끌어냅니다.  결과적으로, 이러한 비판 기반의 개선은 **장문 생성의 일관성 및 질적 향상**이라는 핵심 목표 달성에 기여하며, 단순히 길이만 늘리는 것이 아니라 **내용의 충실성 및 질적 만족도**를 높이는 데 중요한 역할을 합니다.

#### Future of LongDPO
LongDPO는 장문 생성 능력 향상에 있어 고무적인 발걸음이지만, **향후 연구 방향**은 다음과 같이 요약할 수 있습니다.  **다양한 모델 아키텍처와의 호환성 확대**가 필요하며,  **다양한 유형의 장문 생성 작업**에 대한 적용성 검증이 중요합니다.  **단계별 감독 데이터의 효율적 수집 및 관리 방안**에 대한 연구도 필수적입니다.  **외부 비평의 질적 향상**을 위한 연구와 **다양한 비평 방식**의 통합도 고려해야 합니다.  나아가, **장문 생성 과정의 설명력 및 투명성**을 높이는 연구를 통해 신뢰성을 확보하는 것 또한 중요한 과제입니다.  **에너지 효율 및 연산량 최적화**에 대한 연구도 지속되어야 하며,  **윤리적 및 사회적 함의**에 대한 심도있는 논의가 필요합니다.  **최종적으로, LongDPO의 실질적인 활용 방안**을 모색하고, **다양한 응용 분야**에 적용하는 연구가 필요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.02095/x2.png)

> 🔼 그림 2는 LongDPO의 파이프라인을 보여줍니다. LongDPO는 과정 감독과 MCTS를 통합하여 단계별 선호도 데이터를 수집합니다. 여기서 선호도 데이터는 동일한 접두사를 공유하며 각 계층에서 한 쌍만 수집됩니다. 선택 단계에서 LongDPO는 글로벌 메모리 풀을 사용하여 불일치를 야기할 수 있는 후보를 걸러낸 다음, 가장 높은 점수를 받은 후보를 선택 후보로, 다른 하나를 임의로 선택된 후보로 합니다. 트리 확장 중에 일부 선택된 후보의 보상이 낮을 수 있는데, LongDPO는 외부 지식을 사용하여 개선을 위한 비판을 제공합니다. 그런 다음 수집된 선호도 쌍을 단계별 DPO 훈련에 사용합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2:  The pipeline of LongDPO. LongDPO incorporates process supervision and MCTS to collect stepwise preference data, where the preference data share the same prefix and only one pair is collected at each layer. During the selection phase, LongDPO uses the global memory pool to filter out candidates that may result in inconsistency, then selects the highest-scoring one as the chosen candidate, with another randomly selected as the rejected candidate. During tree expansion, some chosen candidates may have low rewards, LongDPO uses external knowledge to provide critiques for refinement. Then the collected preference pairs are used for step-level DPO training.
> </details>



![](https://arxiv.org/html/2502.02095/x3.png)

> 🔼 그림 3은 선택된 후보들의 보상 분석 결과를 보여줍니다. 각 선호도 쌍에서 선택된 후보만을 고려하여 평균 보상이 3.0 미만인 후보의 비율을 '0-3.0', 평균 보상이 3.0 이상이지만 3.5 미만인 후보의 비율을 '3.0-3.5'로 나타냅니다. 보다 자세한 보상 분포는 부록 6을 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Figure 3:  Reward analysis of the selected candidates, we focus solely on the chosen candidate in each preference pair. On the x-axis, ’0-3.0’ represents the proportion of candidates with an average reward <3.0absent3.0<3.0< 3.0, while ’3.0-3.5’ represents the proportion of candidates with an average reward ≥3.0absent3.0\geq 3.0≥ 3.0 but <3.5absent3.5<3.5< 3.5. Detailed reward distribution can be found in Appendix 6.
> </details>



![](https://arxiv.org/html/2502.02095/x4.png)

> 🔼 그림 4는 본 논문의 부록 A.2절에 자세히 설명된 비평(critique) 생성 과정의 주요 내용을 보여줍니다.  LLM이 생성한 긴 형식의 텍스트에 대한 비평을 생성하는 과정을 단계별로 보여주는 그림입니다.  각 단계는 분석(Analysis), 신뢰도 점수(Confidence Score), 정당화(Justification), 작성 제안(Writing Suggestion), 관련 텍스트(Relevant Text)로 구성되며,  이러한 요소들이 종합적으로 고려되어 긴 형식 텍스트의 질을 향상시키는 데 기여합니다.  각 요소는 모델의 자신감과 비평의 정확성을 평가하고,  텍스트의 개선 방향을 제시하는 역할을 수행합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Main body of generated critiques which have detailed in Appedix A.2
> </details>



![](https://arxiv.org/html/2502.02095/x5.png)

> 🔼 그림 5는 LongGenBench에서 무작위로 선택된 사례를 보여줍니다. 이 과제는 10주차부터 5주마다 농산물 시장을 방문하라는 지시사항을 포함합니다. 왼쪽 그림은 LongWriter-Llama 모델이 10주차에는 요구사항을 충족하지만 15주차에는 실패하는 모습을 보여줍니다. 반면 오른쪽 그림은 LongDPO를 적용한 후 LongWriter-Llama 모델이 지시사항을 일관되게 충족하는 것을 보여줍니다. 이는 LongDPO가 장문 생성 과제에서 모델의 성능을 향상시키는 데 효과적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5:  A case is randomly sampled from LongGenBench. The instruction primarily requires visiting the farmers’ market starting from week 10 and then every 5 weeks thereafter. On the left, LongWriter-Llama fulfills the requirement in week 10 but fails in week 15. On the right, after applying LongDPO, LongWriter-Llama is able to consistently meet the demands.
> </details>



![](https://arxiv.org/html/2502.02095/x6.png)

> 🔼 그림 6은 LongDPO 모델이 MCTS(Monte Carlo Tree Search)를 통해 생성한 긴 형식의 텍스트 생성 과정에서 선택된 후보군들의 보상(reward) 분포를 보여줍니다.  x축은 보상 점수의 범위를 나타내고, y축은 해당 범위에 속하는 선택된 후보들의 비율(백분율)을 나타냅니다. 이는 LongDPO가 단순히 최고 점수의 후보만을 선택하는 것이 아니라, 다양한 점수대의 후보들을 고려하여 균형을 맞추는 과정을 시각적으로 보여주는 그림입니다.  선택된 후보들의 보상 점수 분포를 분석하여 LongDPO의 성능 향상에 기여하는 요소를 이해하는데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 6:  Detailed reward analysis of the chosen candidates.
> </details>



![](https://arxiv.org/html/2502.02095/x7.png)

> 🔼 그림 7은 LongWriter-Llama 모델이 질문에 대한 정답을 제시하지 못하지만, LongDPO를 적용한 후에는 정답을 정확하게 제시할 수 있음을 보여줍니다. 빨간색으로 강조 표시된 부분이 질문에 대한 정답입니다. 이 그림은 LongDPO가 장문 생성 능력을 향상시키는 데 효과적임을 시각적으로 보여주는 사례입니다.
> <details>
> <summary>read the caption</summary>
> Figure 7:  The part highlighted in red is the correct answer to the question. LongWriter-Llama fails to provide the correct answer, but after applying LongDPO, it is able to answer correctly.
> </details>



![](https://arxiv.org/html/2502.02095/x8.png)

> 🔼 그림 8은 LongWriter-Llama 모델이 질문에 대한 답을 제대로 제공하지 못하지만, LongDPO를 적용한 후에는 정답을 정확하게 제시할 수 있음을 보여줍니다. 그림에서는 질문과 선택지가 제시되고, LongWriter-Llama는 잘못된 답을, LongDPO를 적용한 모델은 정답을 선택한 것을 볼 수 있습니다. 빨간색으로 강조된 부분이 정답입니다.  LongDPO가 장문 생성 능력을 향상시키는 데 효과적임을 시각적으로 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 8:  The part highlighted in red is the correct answer to the question. LongWriter-Llama fails to provide the correct answer, but after applying LongDPO, it is able to answer correctly.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Models | LongGenBench (16k) CR | LongGenBench (16k) STC1 | LongGenBench (16k) STC2 | LongGenBench (32k) CR | LongGenBench (32k) STC1 | LongGenBench (32k) STC2 | TruthfulQA ACC | TruthfulQA ACC | MMLU ACC | GSM8k ACC |
|---|---|---|---|---|---|---|---|---|---|---|
| **LongWriter-Llama** | 46.00 | 22.60 | 9.80 | 34.50 | **33.60** | 10.00 | 38.43 | 56.07 | 63.24 | 57.70 |
|  _w/ DPO_ | 64.99 | 25.99 | 16.29 | 65.24 | 32.47 | 20.39 | 38.17 | 55.68 | 63.30 | 59.20 |
|  _w/ LongDPO_ | **69.38** | **27.59** | **18.45** | **66.96** | 32.63 | **20.83** | **40.76** | **58.78** | **63.67** | **61.30** |
| **LongWriter-Qwen** | **98.94** | 31.39 | 31.02 | 58.67 | **33.58** | 18.93 | **45.29** | 61.78 | 74.16 | 83.78 |
|  _w/ DPO_ | 95.95 | 31.18 | 29.83 | 82.23 | 29.02 | 22.33 | 39.29 | 57.67 | 63.67 | 83.85 |
|  _w/ LongDPO_ | 98.51 | **33.07** | **32.52** | **84.95** | 29.86 | **24.32** | 44.92 | **62.75** | **74.25** | **84.08** |{{< /table-caption >}}
> 🔼 표 2는 LongGenBench를 포함한 다양한 장문 생성 및 일반적인 벤치마크에 대한 모델 성능을 비교한 표입니다. LongGenBench는 최대 32k 토큰 길이의 출력을 평가하는 데 사용되며, 다른 벤치마크는 유용성 및 추론과 같은 일반적인 작업에 대한 모델 성능을 평가합니다. TruthfulQA의 경우 'MC1' 및 'MC2' 파티션의 결과를 보고합니다. 모든 작업에 대해 세 가지 방법 모두 동일한 디코딩 설정을 사용했으며, 재현성을 보장하기 위해 난수 시드를 설정했습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Performance comparison across more long-form and general benchmarks. LongGenBench can be used to evaluate output lengths up to 32k. The other benchmarks assess the model’s performance on more general tasks like helpfulness and reasoning. For TruthfulQA, we report partition “MC1' and “MC2'. For each task, all three methods use the same decoding settings, and we have set a random seed to ensure reproducibility.
> </details>

{{< table-caption >}}
| Methods | [0, 500) $S_l$ | [0, 500) $S_q$ | [500, 2k) $S_l$ | [500, 2k) $S_q$ | [2k, 4k) $S_l$ | [2k, 4k) $S_q$ | [4k, 20k) $S_l$ | [4k, 20k) $S_q$ | Average $S_l$ | Average $S_q$ |
|---|---|---|---|---|---|---|---|---|---|---|
| **LongWriter-Llama** | 88.10 | 86.00 | 75.40 | 86.90 | 89.10 | 88.30 | 80.80 | 79.20 | 83.12 | 85.30 |
|   ***w/o critique*** | 89.69 | 87.00 | 75.46 | 89.58 | 92.72 | 89.01 | 83.93 | 79.51 | 85.45 | 86.27 |
|   ***w/ self-critique*** | 92.51 | 88.15 | 74.40 | 89.81 | 90.15 | 88.48 | 83.62 | 81.38 | 85.17 | 86.96 |
|   ***w/ LongDPO*** | 90.74 | 89.14 | 76.61 | 90.70 | 93.46 | 91.10 | 87.77 | 81.94 | **87.14** | **88.22** |
| **LongWriter-Qwen** | 90.80 | 87.99 | 84.37 | 89.37 | 84.21 | 84.84 | 58.69 | 78.13 | 79.51 | 85.08 |
|   ***w/o critique*** | 89.59 | 86.99 | 85.35 | 89.01 | 88.14 | 84.31 | 63.98 | 80.20 | 81.77 | 85.12 |
|   ***w/ self-critique*** | 90.67 | 90.68 | 83.60 | 93.26 | 87.46 | 86.61 | 65.20 | 78.24 | 81.73 | 87.20 |
|   ***w/ LongDPO*** | 89.36 | 91.18 | 85.48 | 92.10 | 89.60 | 87.16 | 67.66 | 83.17 | **83.03** | **88.40** |{{< /table-caption >}}
> 🔼 표 3은 LongDPO 모델의 성능 향상에 기여하는 요소를 분석하기 위한 추가 실험 결과를 보여줍니다.  구체적으로는, MCTS 과정에서 후보 답변을 개선하는 방법(외부 비평 사용 vs. 모델 자체 비평 사용 vs. 비평 없이 MCTS만 사용)과 임계값 η(eta)의 변화에 따른 성능 변화를 보여줍니다.  'w/o critique'는 외부 비평이나 자체 비평 없이 MCTS만 사용한 경우를, 'Self-critique'는 모델 자체가 생성한 비평을 사용한 경우를 나타냅니다.  다양한 η 값을 설정하여 모델의 일반화 능력을 확인하고 평균 결과를 제시합니다.  결과적으로 외부 비평을 사용한 LongDPO가 가장 우수한 성능을 보이며, 모델 자체 비평만 사용하는 경우에는 성능 향상에 있어 불안정성을 보이는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Ablation on refinement methods and “w/o critique' stands for without critiques meaning MCTS is applied alone. “Self-critique' refers to critiques generated by the model itself. To verify generalization, we set different values of η𝜂\etaitalic_η and report the average result.
> </details>

{{< table-caption >}}
| Rate | Diversity | Consistency | Informative |
|---|---|---|---| 
| Win | 65.0 | 61.7 | 61.7 |
| Tie | 8.30 | 16.7 | 6.70 |
| Lose | 26.7 | 21.6 | 31.6 |{{< /table-caption >}}
> 🔼 본 논문의 표 4는 세 가지 기준(다양성, 일관성, 정보성)을 바탕으로 한 인간 평가 결과를 보여줍니다. 각 기준에 대해 LongWriter 모델과 LongDPO를 적용한 모델의 응답이 얼마나 우수한지 비교 분석한 결과입니다. 다양성은 문장의 어휘, 의미, 구조의 다양성을 평가하고, 일관성은 주제, 논리, 사실의 일관성을 평가하며, 정보성은 정보의 정확성, 포괄성, 명료성, 가독성을 평가합니다. 표에는 각 기준에 대한 승률, 무승부율, 패률이 제시되어 있습니다. LongDPO를 적용한 모델이 세 가지 기준 모두에서 더 높은 승률을 보였습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Human evaluation with win rates under three criteria: Diversity, Consistency, and Informativeness
> </details>

{{< table-caption >}}
| Judge | Judge-1 | Judge-2 | Judge-3 |
|---|---|---|---|
| Judge-1 | - | 61.7 | 63.4 |
| Judge-2 | 61.7 | - | 61.7 |
| Judge-3 | 65.0 | 58.4 | - |{{< /table-caption >}}
> 🔼 표 5는 세 명의 인간 심사자가(Judge-1, Judge-2, Judge-3) 서로 다른 응답에 대해 일치율을 평가한 결과를 보여줍니다.  각 심사자는 다양성, 일관성, 정보성 세 가지 기준으로 응답을 평가했고, 표는 각 기준에 대한 심사자 간의 일치율을 백분율로 나타냅니다.  이 표는 인간 심사자의 평가 일관성을 보여주는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Human agreement between different annotators. Judge-1, Judge-2, and Judge-3 are three human judges.
> </details>

{{< table-caption >}}
| $S_q$ | Relevance | Accuracy | Coherence | Clarity | Breadth and Depth | Reading Experience |
|---|---|---|---|---|---|---| 
| LongWriter-Llama | 79.20 | 90.90 | 87.50 | 84.48 | 81.89 | 59.48 | 71.55 |
| +DPO | 80.90 | 93.75 | 83.33 | 77.08 | 77.08 | 83.33 | 70.83 |
| +LongDPO | 85.06 | 93.75 | 85.42 | 85.42 | 81.25 | 87.50 | 77.08 |
| LongWriter-Qwen | 78.13 | 83.33 | 81.25 | 83.33 | 77.08 | 68.75 | 75.00 |
| +DPO | 78.81 | 85.41 | 81.25 | 83.33 | 81.25 | 85.41 | 70.83 |
| +LongDPO | 85.41 | 91.67 | 91.67 | 83.33 | 83.33 | 83.33 | 79.16 |{{< /table-caption >}}
> 🔼 표 6은 LongBench-Write-en 벤치마크에서 길이가 4000단어를 초과하는 긴 형식의 글 생성 결과에 대한 세부 품질 점수를 보여줍니다.  각 지표(관련성, 정확성, 일관성, 명확성, 깊이 및 폭, 가독성)에 대한 평균 점수를 제시하여, LongDPO 모델을 적용했을 때 각 지표에서의 성능 변화를 자세히 분석합니다. 이를 통해 LongDPO가 긴 형식의 글 생성에서 품질 향상에 미치는 영향을 정량적으로 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Detailed quality score for length exceeding 4000 in LongBench-Write-en.
> </details>

{{< table-caption >}}
| LongWriter-Llama | [0, 500)  $S_l$ | [0, 500) $S_q$ | [500, 2k) $S_l$ | [500, 2k) $S_q$ | [2k, 4k) $S_l$ | [2k, 4k) $S_q$ | [4k, 20k) $S_l$ | [4k, 20k) $S_q$ | Average $S_l$ | Average $S_q$| 
|---|---|---|---|---|---|---|---|---|---|---| 
| Self-critique  _η≤2.0_ | 94.07 | 88.97 | 72.39 | 87.99 | 86.86 | 89.39 | 82.72 | 80.55 | 84.01 | 86.72 |
|  _η≤2.5_ | 93.08 | 88.48 | 76.43 | 91.04 | 91.66 | 88.54 | 84.63 | 82.35 | **86.45** | **87.60** |
|  _η≤3.0_ | 90.38 | 87.01 | 74.37 | 90.41 | 91.94 | 87.50 | 83.50 | 81.25 | 85.04 | 86.54 |
| LongDPO _η≤2.0_ | 92.01 | 92.91 | 72.55 | 91.45 | 93.35 | 93.75 | 88.86 | 80.20 | 86.69 | **89.57** |
|  _η≤2.5_ | 90.68 | 86.27 | 77.23 | 91.25 | 93.35 | 90.53 | 88.25 | 85.06 | **87.38** | 88.19 |
|  _η≤3.0_ | 89.51 | 88.23 | 80.04 | 89.39 | 93.68 | 89.01 | 86.19 | 80.55 | 86.47 | 86.80 |{{< /table-caption >}}
> 🔼 본 표는 Llama 기반 백본 모델을 사용하여 η 값을 변경했을 때의 결과를 보여줍니다.  η는 선택된 후보의 평균 보상이 임계값보다 낮을 때 미세 조정을 위한 후보를 선택하는 데 사용되는 임계값입니다.  표에는 다양한 η 값에 따른 [0, 500), [500, 2k), [2k, 4k), [4k, 20k)의 네 가지 길이 범위에 대한 성능(길이 점수 Si 및 품질 점수 Sq)이 요약되어 있습니다.  각 범위와 전반적인 평균 성능을 비교하여 η 값의 변경이 Llama 기반 모델의 성능에 미치는 영향을 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Results on changing η𝜂\etaitalic_η using llama-based backbones
> </details>

{{< table-caption >}}
| LongWriter-Qwen | [0, 500)  $S_l$ | [0, 500) $S_q$ | [500, 2k) $S_l$ | [500, 2k) $S_q$ | [2k, 4k) $S_l$ | [2k, 4k) $S_q$ | [4k, 20k) $S_l$ | [4k, 20k) $S_q$ | Average $S_l$ | Average $S_q$ |
|---|---|---|---|---|---|---|---|---|---|---|
| Self-critique  + $\eta \leq 2.0$ | 88.71 | 88.23 | 84.45 | 93.54 | 86.37 | 84.46 | 64.88 | 78.47 | 81.10 | 86.17 |
|  + $\eta \leq 2.5$ | 91.96 | 91.66 | 83.16 | 92.91 | 88.94 | 86.36 | 67.69 | 79.16 | **82.93** | 87.52 |
|  + $\eta \leq 3.0$ | 91.33 | 92.15 | 83.20 | 93.33 | 87.06 | 89.01 | 63.04 | 77.08 | 81.16 | **87.89** |
| LongDPO + $\eta \leq 2.0$ | 87.84 | 91.45 | 86.21 | 92.15 | 91.35 | 86.86 | 66.85 | 82.59 | 83.06 | 88.26 |
|  + $\eta \leq 2.5$ | 88.93 | 91.91 | 85.47 | 91.25 | 88.63 | 85.60 | 71.14 | 85.41 | **83.54** | **88.54** |
|  + $\eta \leq 3.0$ | 91.32 | 90.19 | 84.75 | 92.91 | 88.82 | 89.01 | 64.99 | 81.51 | 82.47 | 88.51 |{{< /table-caption >}}
> 🔼 표 8은 Qwen 기반 백본을 사용하여 η 값을 변경했을 때의 결과를 보여줍니다.  다양한 길이의 텍스트 생성에 대한 성능을 평가하기 위해 네 가지 길이 범주(0-500, 500-2k, 2k-4k, 4k-20k)를 사용했습니다. 각 범주에 대해,  LongWriter-Qwen 모델의 성능을 측정하고,  자체 비판(self-critique)과 LongDPO를 적용한 경우의 성능을 비교 분석합니다.  η의 값을 2.0, 2.5, 3.0으로 변화시키면서 실험을 수행하고,  각 경우에 대한 정밀도(S<sub>i</sub>) 및 품질(S<sub>q</sub>) 점수를 제시합니다. 이를 통해 LongDPO가 다양한 길이의 텍스트 생성에서 일관된 성능 향상을 보이는지, 그리고 η 값의 변화에 따른 민감도는 어떠한지를 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Results on changing η𝜂\etaitalic_η using Qwen-based backbones
> </details>

{{< table-caption >}}
| Evaluated Models | S<sub>q</sub> |
|---|---| 
| Claude 3.5 Sonnet | 87.7 ± 0.5 |
| GPT-4 Turbo | 86.6 ± 0.4 |
| GPT-4o mini | 90.3 ± 0.3 |
| GPT-4o | 91.8 ± 0.5 |
| GLM-4-9B-chat | 85.5 ± 0.4 |
| Llama-3.1-8B-Instruct | 70.6 ± 0.3 |
| Llama-3.1-70B-Instruct | 80.3 ± 0.3 |
| Mistral-Large-Instruct | 88.3 ± 0.4 |
| Suri-I-ORPO | 53.5 ± 0.5 |
| LongWriter-Llama | 82.2 ± 0.4 |
| LongWriter-Llama + LongDPO | 88.2 ± 0.5 |
| LongWriter-Qwen + LongDPO | 88.6 ± 0.5 |{{< /table-caption >}}
> 🔼 표 9는 다양한 언어 모델들의 품질 점수(Sq) 평균을 보여줍니다.  LongWriter-Llama + LongDPO와 LongWriter-Qwen + LongDPO 모델의 결과는 본 논문에서 직접 평가한 것이고, Bai et al.(2024c) 논문의 결과를 추가하여 다른 모델들과의 비교 분석을 수행했습니다.  본 표는 모델 성능 비교를 위한 종합적인 결과를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Evaluated Models and the average Sqsubscript𝑆𝑞S_{q}italic_S start_POSTSUBSCRIPT italic_q end_POSTSUBSCRIPT Scores. We evaluate LongWriter-Llama + LongDPO and LongWriter-Qwen + LongDPO, while Bai et al. (2024c) report the remaining results.
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