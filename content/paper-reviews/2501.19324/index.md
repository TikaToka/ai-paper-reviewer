---
title: "Reward-Guided Speculative Decoding for Efficient LLM Reasoning"
summary: "RSD는 경량 모델과 고성능 모델을 결합하여 LLM 추론의 효율성을 높이는 새로운 프레임워크입니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Salesforce AI Research",]
showSummary: true
date: 2025-01-31
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.19324 {{< /keyword >}}
{{< keyword icon="writer" >}} Baohao Liao et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-03 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.19324" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.19324" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/reward-guided-speculative-decoding-for" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)은 강력한 성능을 제공하지만, 추론 과정에서 높은 계산 비용이 발생하는 문제가 있습니다. 기존의 추론 가속화 기술은 모델의 크기와 복잡도에 따라 효율성이 제한적일 수 있습니다. 특히, 다단계 추론 작업에서는 정확성을 유지하면서 효율성을 개선하는 것이 어렵습니다. 

본 논문에서는 **보상 기반 예측적 디코딩(RSD)**이라는 새로운 프레임워크를 제시합니다. RSD는 경량 모델을 사용하여 후보 답변을 생성하고, 고성능 모델로 답변의 품질을 평가하여 계산 비용과 성능 간의 균형을 최적화합니다. 실험 결과, RSD는 기존 방법보다 **추론 속도를 최대 4.4배 향상시키고, 정확도를 최대 3.5% 향상**시키는 것으로 나타났습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 경량 모델과 고성능 모델을 결합하여 LLM 추론 속도 향상 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 기존 방법 대비 정확도 향상 및 연산량 감소 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 자원 제약 환경에서의 LLM 배포 효율성 증대 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대규모 언어 모델(LLM) 추론의 효율성을 크게 향상시키는 새로운 프레임워크인 RSD**를 제시하여, 자원 집약적인 환경에서 LLM을 배포하는 데 중요한 의미를 가집니다.  **기존의 추론 방법보다 속도와 정확성을 개선**하여, **LLM의 실용성을 높이고 연구의 새로운 방향을 제시**하는 데 기여합니다.  본 연구는 효율적인 LLM 추론에 대한 지속적인 연구를 위한 중요한 기반을 마련하며, 다양한 분야의 연구자들에게 영향을 미칠 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.19324/x1.png)

> 🔼 그림 1은 제안된 보상-유도 추론적 디코딩(RSD) 방법을 설명합니다. 기존의 추론적 디코딩(SD)은 초안 모델과 목표 모델 간의 토큰 일치 여부에 따라 계산을 수행하지만, RSD는 보상 신호(r)를 사용하여 초안 모델의 출력을 평가하고, 정확한 일치 여부와 관계없이 유용한 출력을 선택적으로 다듬어 효율성을 높입니다.  작고 빠른 초안 모델이 1차 결과를 생성하고, 그 뒤 더 크고 정확한 목표 모델이 결과를 검증하고 개선하는 과정을 보여줍니다. 어두운 배경 영역은 높은 계산 비용을 나타내며, SD는 거부된 토큰에 불필요한 계산을 수행하는 반면, RSD는 불필요한 단계를 줄여 효율성과 정확성의 균형을 맞춘다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Reward-Guided Speculative Decoding (RSD). This diagram illustrates how RSD improves upon standard speculative decoding (SD) by incorporating reward-guided selection. SD strictly enforces exact token matching between the draft and target model, leading to unnecessary computations when mismatched tokens are discarded. In contrast, RSD evaluates draft outputs based on reward signals r𝑟ritalic_r and selectively refines them, reducing reliance on exact matching and improving efficiency. The process starts with a small and fast draft model generating preliminary results, followed by a larger and more reliable target model verifying and refining predictions. Darker background regions indicate higher computational costs, showing how SD wastes resources on rejected tokens, whereas RSD reduces unnecessary steps by accepting useful draft outputs even when they do not exactly match, balancing efficiency and accuracy.
> </details>





{{< table-caption >}}
| Weighting Function | Definition |
|---|---| 
| \omega(r)=p | Constant  p\in(0,1) |
| \omega(r)=\mathbf{1}(r\geq\delta) | 1 if  r\geq\delta, else 0 |
| \omega(r)=\min(1,\max(0,r)) | Clipping  r within [0,1] |
| \omega(r)=\max(0,\frac{r}{1+r}) | Sigmoidal transformation |
| \omega(r)=\frac{1}{1+e^{-\alpha(r-\delta)}} | Logistic function |{{< /table-caption >}}

> 🔼 이 표는 논문의 2.1절 (RSD 알고리즘)에서 사용된 가중치 함수 ω(r)의 다양한 변형과 각 변형의 정의를 보여줍니다.  ω(r)은 드래프트 모델과 타겟 모델의 출력을 혼합하는 데 사용되는 함수로,  r은 각 단계의 출력 품질을 나타내는 보상 신호입니다. 표에는 상수 함수, 이진 함수, 클리핑 함수, 시그모이드 함수, 로지스틱 함수 등 다양한 ω(r) 함수의 유형과 수식이 제시되어 있습니다. 각 함수는 드래프트 모델의 출력을 얼마나 신뢰할지 결정하는 데 사용됩니다.  보상 신호 r의 값에 따라 가중치를 다르게 적용하여 효율성과 정확성 간의 균형을 맞추는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Variants of Weighting Function ω⁢(r)𝜔𝑟\omega(r)italic_ω ( italic_r ) and their definitions
> </details>





### In-depth insights


#### LLM Efficiency
본 논문은 대규모 언어 모델(LLM)의 추론 효율성을 향상시키는 새로운 프레임워크인 보상-유도 추측적 디코딩(RSD)을 제시합니다. **기존의 추측적 디코딩 방법은 엄격한 편향성 제거를 통해 대규모 모델과 소규모 모델 간의 일치성을 강조하지만, RSD는 보상 모델을 통합하여 고보상 출력을 우선시함으로써 효율성과 정확성 간의 균형을 최적화합니다.**  **RSD는 경량화된 초안 모델과 더 강력한 대상 모델을 결합하여 중간 디코딩 단계를 평가하고 대상 모델을 호출할지 여부를 동적으로 결정합니다.** 이는 계산 비용과 출력 품질 간의 절충을 최적화하는 데 도움이 됩니다.  **실험 결과는 RSD가 대상 모델만 사용하는 것보다 최대 4.4배 적은 FLOP를 사용하면서, 병렬 디코딩 방법보다 평균적으로 최대 3.5% 더 높은 정확도를 달성함을 보여줍니다.**  이는 RSD가 자원 집약적인 환경에서 LLM을 배포하는 데 효과적이고 비용 효율적인 접근 방식임을 강조합니다.  **결론적으로 RSD는 LLM 추론의 효율성을 크게 향상시키는 동시에 정확성을 유지하거나 능가하는 강력한 기술임을 확인시켜줍니다.**

#### RSD Framework
본 논문에서 제시된 RSD(Reward-Guided Speculative Decoding) 프레임워크는 대규모 언어 모델(LLM) 추론의 효율성을 높이기 위한 혁신적인 방법입니다.  **핵심은 경량화된 초안 모델과 강력한 목표 모델을 시너지 효과를 내도록 결합하여 고품질 출력을 우선적으로 생성하는 데 있습니다.** 기존의 예측적 디코딩 방법과 달리, RSD는 엄격한 편향 없는 접근 방식 대신 제어된 편향을 도입하여 보상 모델을 사용하여 중간 디코딩 단계를 평가하고 목표 모델을 호출할지 여부를 동적으로 결정합니다. 이를 통해 **계산 비용과 출력 품질 간의 균형을 최적화**하고, **자원 집약적인 환경에서 LLM을 효율적으로 배포**할 수 있게 합니다.  **임계값 기반 혼합 전략**은 자원 활용과 성능 간의 최적의 균형을 달성하는 이론적 근거를 제공합니다.  다양한 벤치마크 평가 결과는 RSD가 목표 모델만 사용하는 것보다 최대 4.4배 적은 FLOP으로 상당한 효율성 향상을 제공하며, 평균적으로 병렬 디코딩 방법보다 정확도가 최대 3.5% 더 높다는 것을 보여줍니다.

#### Reward Tuning
보상 튜닝은 강화 학습에서 중요한 개념으로, 에이전트가 환경과 상호작용하여 목표를 달성하도록 **보상 함수를 미세 조정하는 과정**을 의미합니다.  **보상 함수는 에이전트의 행동에 대한 가치를 정의**하며, 잘 설계된 보상 함수는 에이전트가 원하는 행동을 학습하도록 유도합니다. 논문에서 보상 튜닝은 에이전트(여기서는 언어 모델)의 추론 효율성 향상에 중점을 둡니다.  **잘못된 추론 단계를 걸러내고 정확한 추론 단계를 우선시**하는 보상 함수를 설계하여, 계산 비용을 절감하면서도 성능 저하 없이 추론 속도를 높일 수 있을 것입니다.  **보상 함수의 설계는 모델의 크기, 데이터셋 크기, 그리고 목표하는 추론 과제의 복잡도** 등 여러 요인에 따라 달라집니다. 따라서, **최적의 보상 함수를 찾기 위해서는 다양한 실험과 분석이 필요**하며, 이를 통해 보상 튜닝은 효율적인 언어 모델 추론 시스템 구축에 중요한 역할을 할 것으로 예상됩니다.  **실험 결과는 보상 튜닝이 추론 효율성을 크게 향상**시킨다는 것을 보여주는 동시에, 추론 과제의 복잡성에 따라 보상 함수를 조정하는 것이 중요함을 시사합니다.

#### Computational Cost
본 논문에서 다루는 계산 비용은 대규모 언어 모델(LLM) 추론의 효율성을 높이는 데 중점을 둡니다. **핵심은 경량화된 모델과 강력한 모델을 결합하여 계산 비용과 성능 간의 균형을 최적화하는 것**입니다. 저자들은 이를 통해 기존의 추론 방법보다 상당한 효율성 향상을 달성했습니다.  **특히, 문맥 정보를 활용하여 중간 단계의 디코딩을 평가하고, 필요에 따라 강력한 모델을 호출하는 전략**은 자원 사용량을 최소화하면서도 성능 저하 없이 추론 속도를 향상시킬 수 있음을 보여줍니다.  **임계값 기반 혼합 전략**을 통해 자원 활용과 성능 사이의 최적 균형을 이루는 것 또한 중요한 발견입니다.  계산 비용 절감 효과는 다양한 벤치마크에서 검증되었으며, 특히 복잡한 추론 작업에서 효과가 더욱 뛰어났습니다.  **결론적으로, 이 연구는 LLM의 실용적인 배포에 중요한 의미**를 지니며, **자원 제약이 심한 환경에서도 효율적이고 효과적인 추론**을 가능하게 합니다.

#### Future Work
본 논문은 효율적인 LLM 추론을 위한 새로운 프레임워크인 보상-유도 예측 디코딩(RSD)을 제시합니다. **향후 연구 방향**으로는 첫째, 다양한 보상 함수와 가중치 함수를 추가적으로 실험하여 RSD의 성능을 더욱 향상시키는 것을 고려할 수 있습니다.  둘째, **다양한 크기의 모델**을 결합하여 RSD의 일반화 성능을 평가하고 개선하는 연구가 필요합니다.  셋째, **전문화된 PRM**을 훈련하여 RSD의 효율성을 높이는 방안을 모색할 수 있습니다. 특히 수학, 코딩과 같은 특정 분야에 최적화된 PRM을 개발하면 RSD의 성능 향상에 기여할 것으로 예상됩니다. 넷째, 현재 RSD는 단일 단계 예측에 초점을 맞추고 있으나, **다단계 추론**에 대한 확장 및 적용에 대한 연구가 필요합니다.  다섯째, RSD와 기존의 다른 추론 가속화 기법들을 결합하여 시너지 효과를 창출하는 방안을 연구할 수 있습니다. 마지막으로, **다양한 하드웨어 플랫폼**에서의 RSD 성능을 평가하여 실제 환경에서의 적용 가능성을 확인하는 것이 중요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.19324/x2.png)

> 🔼 그림 2는 제안된 보상-유도 예측 디코딩(RSD) 방법을 보여줍니다.  이 그림은 소규모 모델(Pm)과 대규모 모델(PM)의 확률 분포와 이 두 모델을 보상 함수 r(yi|zi)에 따라 동적으로 혼합한 RSD 분포(PRSD)를 비교합니다.  출력 yi의 품질이 높을수록(r(yi|zi)값이 클수록) Pm의 가중치 w(yi|zi)가 커져서 PRSD는 Pm에 가까워지고, 효율성이 높아집니다. 반대로 출력 품질이 낮으면 PM의 가중치가 커져서 PRSD는 PM에 가까워지고, 성능 저하를 방지합니다. 이 그림은 RSD가 출력의 품질에 따라 소규모 모델과 대규모 모델을 효율적으로 혼합하여 계산 비용과 성능 간의 균형을 맞추는 방법을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Illustration of Reward-Guided Speculative Decoding
> </details>



![](https://arxiv.org/html/2501.19324/x3.png)

> 🔼 그림 3은 RSD 프레임워크 내에서 초안 모델과 대상 모델이 생성한 모든 질문에 대한 보상 점수를 비교한 것입니다. 왼쪽 그림은 모든 질문에 대한 보상 점수 비교를 보여주고, 가운데 그림은 초안 모델과 대상 모델이 정답을 맞춘 질문에 대한 보상 점수를 집중적으로 비교합니다. 오른쪽 그림은 초안 모델과 대상 모델 중 어떤 모델이 더 높은 보상 점수를 기록했는지 비율을 보여줍니다. 이 실험에서는 Qwen2.5-Math-1.5B-Instruct를 초안 모델로, Qwen2.5-Math-7B-Instruct를 대상 모델로, Skywork-o1-Open-PRM-7B를 PRM으로 사용했습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Left: A comparison of the reward scores for all questions generated by the draft model and the target model within the RSD framework. Middle: A focused comparison of the reward scores for correctly answered questions generated by the draft model and the target model in the RSD framework. Right: The winning rate (in terms of reward) comparison between the draft model and the target model, highlighting the proportion of cases where each model outperforms the other. RSD is configured with Qwen2.5-Math-1.5B-Instruct as the draft model, Qwen2.5-Math-7B-Instruct as the target model, and Skywork-o1-Open-PRM-7B as the PRM.
> </details>



![](https://arxiv.org/html/2501.19324/x4.png)

> 🔼 그림 4는 MATH500 데이터셋에서 연산량(FLOPs)과 정확도 간의 관계를 보여줍니다. 이 그래프는 제안된 RSD 방법과 기준 방법(단일 대규모 모델, SD, BON)의 성능을 비교하여, RSD가 더 적은 연산량으로도 높은 정확도를 달성함을 시각적으로 보여줍니다.  이는 RSD의 효율성을 강조하는 중요한 결과입니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Flops vs. accuracy on MATH500.
> </details>



![](https://arxiv.org/html/2501.19324/x5.png)

> 🔼 그림 5는 RSD(1.5B/7B/7B)에서 임계값 δ의 영향을 보여줍니다.  x축은 임계값 δ(0에서 1 사이의 값)이고, y축은 두 가지 지표를 나타냅니다. 하나는 정확도(Accuracy)이고 다른 하나는 초안 모델(draft model)만으로 해결된 질문의 비율(%)입니다. 이 그래프는 임계값 δ를 변화시키면서 정확도와 초안 모델 의존도의 변화를 보여주어, 효율성과 정확성 간의 균형을 맞추는 데 최적의 δ값을 선택하는 데 도움이 됩니다.  즉, 적절한 δ값을 선택하여 계산 비용을 줄이면서도 높은 정확도를 유지할 수 있음을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: The impact of threshold δ𝛿\deltaitalic_δ with RSD (1.5B/7B/7B).
> </details>



![](https://arxiv.org/html/2501.19324/x6.png)

> 🔼 그림 6은 본 논문의 표 1에 제시된 가중치 함수들을 사용하여 RSD (1.5B/7B/7B) 모델의 정확도를 비교한 그래프입니다. 모든 설정에서 추론 비용은 유사합니다. 가중치 함수의 종류에 따라 RSD 모델의 정확도가 어떻게 달라지는지를 보여줍니다. 상수 가중치 함수(Constant), 이진 가중치 함수(Binary), 로지스틱 함수(Logistic), 클리핑(Clipping), 시그모이드(Sigmoidal) 함수 등 다양한 가중치 함수의 성능을 비교하여, 어떤 함수가 RSD 모델의 정확도 향상에 가장 효과적인지를 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Accuracy of weighting functions from Table 1 with RSD (1.5B/7B/7B). All settings share a similar inference cost.
> </details>



![](https://arxiv.org/html/2501.19324/x7.png)

> 🔼 그림 B.1은 다양한 δ 값과 질문의 복잡도 수준(수준이 높을수록 질문이 어려움)에 따른 RSD(1.5B/7B/7B)의 동작을 보여줍니다. δ=0은 모든 질문이 초안 모델만으로 해결되었음을, δ=1은 모든 질문이 대상 모델만으로 해결되었음을 의미합니다. 전반적으로 대상 모델의 개입은 정확도를 향상시키며, 그 효과는 어려운 질문일수록 더욱 두드러집니다(4, 5레벨에서 +16). 또한, 동일한 δ에서 수준이 높아질수록 초안 모델만으로 해결되는 질문의 비율이 감소하여, 어려운 질문일수록 대상 모델의 개입이 더욱 필요함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure B.1: The behaviour of RSD (1.5B/7B/7B) for different δ𝛿\deltaitalic_δs and questions in different complexity levels (the higher the level, the harder the question.). δ=0𝛿0\delta=0italic_δ = 0 and δ=1𝛿1\delta=1italic_δ = 1 denotes all questions are solved by the draft model alone and the target model only, respectively. Overall, the involvement of the target model improves the accuracy. The improvement is more obvious for harder question, +16 for level 4 and 5. In addition, with an increasing level, the questions solved by the draft model only decrease for the same δ𝛿\deltaitalic_δ, demonstrating harder questions need more involvement of the target model.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
Method | Target | Draft | PRM | Setting | MATH500 | GSM8K | GaoKao | Olympiad | GPQA | MMLU | Avg. 
---|---|---|---|---|---|---|---|---|---|---|---
Math Model, Target and Draft: Qwen2.5-Math-Instruct, PRM: Skywork-o1-Open-PRM |  |  |  |  |  |  |  |  |  |  
Single Model | 7B | - | - | - | 83.2 | 95.7 | 66.8 | 41.2 | 32.8 | 32.8 | 65.3 
Majority Voting | - | 1.5B | - | maj@16 | 79.0 | 88.9 | 69.9 | 45.5 | 27.3 | 65.9 | 62.3 (-3.0) 
Best-of-N | - | 1.5B | 7B | N=16 | 82.2 | 93.3 | 69.4 | 44.9 | 27.3 | 71.4 | 64.8 (-0.5) 
SD | 7B | 1.5B | - | - | 83.4 | 95.6 | 67.3 | 40.6 | 28.8 | 72.0 | 64.6 (-0.7) 
RSD | 7B | 1.5B | 1.5B | δ=0.7 | 82.6 | 94.5 | 68.8 | 39.6 | 38.4 | 71.4 | 65.9 (+0.6) 
RSD | 7B | 1.5B | 7B | δ=0.7 | 84.6 | 95.5 | 68.3 | 42.1 | 33.8 | 72.3 | 66.1 (+0.8) 
RSD | 7B | 1.5B | 1.5B | δ* | 82.6 | 95.5 | 68.8 | 40.6 | 38.4 | 71.7 | 66.3 (+1.0) 
RSD | 7B | 1.5B | 7B | δ* | 84.6 | 95.8 | 68.3 | 43.6 | 34.3 | 72.6 | 66.5 (+1.2) 
Single Model | 72B | - | - | - | 85.6 | 95.8 | 73.0 | 48.4 | 42.4 | 85.8 | 71.8 
Majority Voting | - | 1.5B | - | maj@64 | 80.2 | 89.8 | 71.2 | 45.9 | 30.8 | 66.1 | 64.0 (-7.8) 
Best-of-N | - | 1.5B | 7B | N=64 | 82.4 | 94.5 | 68.6 | 44.3 | 27.8 | 72.4 | 65.0 (-6.8) 
Majority Voting | - | 7B | - | maj@64 | 88.0 | 96.5 | 73.8 | 47.6 | 35.9 | 77.2 | 69.8 (-2.0) 
Best-of-N | - | 7B | 7B | N=64 | 86.2 | 97.2 | 71.4 | 44.4 | 36.4 | 75.4 | 68.5 (-3.3) 
SD | 72B | 7B | - | - | 84.8 | 95.8 | 71.7 | 47.6 | 41.4 | 85.3 | 71.1 (-0.7) 
RSD | 72B | 7B | 1.5B | δ=0.7 | 86.4 | 96.4 | 73.0 | 49.8 | 42.9 | 84.7 | 72.2 (+0.4) 
RSD | 72B | 7B | 7B | δ=0.7 | 88.0 | 96.7 | 74.0 | 49.9 | 42.9 | 84.4 | 72.7 (+0.9) 
RSD | 72B | 7B | 1.5B | δ* | 86.6 | 97.0 | 73.2 | 49.8 | 43.9 | 85.2 | 72.6 (+0.8) 
RSD | 72B | 7B | 7B | δ* | 88.0 | 96.9 | 74.0 | 49.9 | 42.9 | 85.6 | 72.9 (+1.1) 
General Model, Target and Draft: Qwen2.5-Instruct, PRM: Skywork-o1-Open-PRM |  |  |  |  |  |  |  |  |  |  
Single Model | 7B | - | - | - | 77.4 | 92.0 | 64.9 | 38.8 | 28.8 | 57.4 | 59.9 
Majority Voting | - | 1.5B | - | maj@16 | 66.4 | 82.1 | 56.9 | 28.7 | 27.3 | 67.2 | 54.8 (-5.1) 
Best-of-N | - | 1.5B | 7B | N=16 | 73.4 | 89.7 | 60.5 | 32.7 | 23.7 | 69.4 | 58.2 (-1.7) 
SD | 7B | 1.5B | - | - | 77.8 | 91.8 | 63.1 | 39.1 | 26.3 | 56.2 | 59.1 (-0.8) 
RSD | 7B | 1.5B | 1.5B | δ=0.7 | 73.6 | 90.8 | 64.2 | 39.0 | 31.3 | 71.6 | 61.8 (+1.9) 
RSD | 7B | 1.5B | 7B | δ=0.7 | 75.0 | 93.3 | 66.2 | 39.9 | 20.2 | 61.8 | 59.4 (-0.5) 
General Model, Target and Draft: Llama-3.1-Instruct, PRM: Skywork-o1-Open-PRM |  |  |  |  |  |  |  |  |  |  
Single Model | 8B | - | - | - | 49.4 | 83.9 | 41.3 | 14.5 | 20.2 | 39.1 | 41.4 
Majority Voting | - | 1B | - | maj@16 | 38.0 | 60.2 | 32.2 | 9.5 | 19.7 | 24.9 | 30.8 (-10.6) 
Best-of-N | - | 1B | 7B | N=16 | 52.6 | 74.8 | 45.7 | 14.4 | 14.1 | 31.0 | 38.8 (-2.6) 
SD | 8B | 1B | - | - | 47.0 | 83.4 | 42.1 | 16.6 | 19.2 | 38.5 | 41.1 (-0.3) 
RSD | 8B | 1B | 1.5B | δ=0.7 | 50.0 | 83.9 | 41.8 | 15.7 | 20.2 | 37.2 | 41.5 (+0.1) 
RSD | 8B | 1B | 7B | δ=0.7 | 50.4 | 85.4 | 41.8 | 18.1 | 19.7 | 36.2 | 41.9 (+0.5) 
RSD | 8B | 1B | 1.5B | δ* | 50.0 | 84.1 | 43.4 | 18.1 | 20.2 | 38.8 | 42.4 (+1.0) 
RSD | 8B | 1B | 7B | δ* | 50.6 | 85.5 | 42.6 | 18.1 | 19.7 | 38.7 | 42.5 (+1.1){{< /table-caption >}}
> 🔼 표 2는 다양한 추론 벤치마크에 대한 RSD(Reward-Guided Speculative Decoding)의 정확도를 보여줍니다.  각 과제의 복잡도가 다르기 때문에, 일반적으로 정확도와 효율성 간의 최적의 균형을 제공하는 임계값(δ)은 0.7입니다. 하지만,  각 과제마다 최적화된 임계값 (δ*)이 존재하며, 이는 부록 B.1절에 자세히 설명되어 있습니다.  표에는 다양한 모델 크기(7B, 72B, 1.5B)와  방법(단일 모델, 다수결 투표, 최적 N개 중 선택,  SD, RSD)에 따른 정확도를 비교하여 보여줍니다.  벤치마크 데이터셋으로는 MATH500, GSM8K, Olympiad Bench, GaoKao 2023 En, GPQA, MMLU STEM 등이 사용되었습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Accuracy on reasoning benchmarks. In general, δ=0.7𝛿0.7\delta=0.7italic_δ = 0.7 offers a good trade-off between accuracy and efficiency for all tasks. δ∗superscript𝛿\delta^{*}italic_δ start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT is the optimized threshold for each task, as different tasks have a different complexity of reasoning. Refer to §B.1 for detailed results.
> </details>

{{< table-caption >}}
| Method | Setting | MATH 500 | GSM8K | Minerva Math | 
|---|---|---|---|---|
| Single Model (1.5B) | - | 73.8 | 85.0 | 29.0 |
| Process Best-of-N | N=8 | 75.8 | 87.8 | 32.7 |
| Process Best-of-N | N=16 | 76.0 | 87.9 | 31.2 |
| Beam Search | bs=4 | 78.2 | 88.9 | 33.5 |
| Beam Search | bs=8 | 78.2 | 88.4 | 32.4 |
| RSD (1.5B/7B/1.5B) | δ=0.7 | 82.6 | 94.5 | 34.6 |{{< /table-caption >}}
> 🔼 표 3은 탐색 기반 방법들과 RSD의 성능을 비교한 표입니다.  비교 대상 방법은 빔 서치와 프로세스 최고 N개 선택법(Process Best-of-N)이며, 두 방법 모두 1.5B 기반 모델과 1.5B PRM을 사용합니다. 표는 GSM8K, MATH500, Minerva Math 세 가지 벤치마크에 대한 정확도를 보여줍니다. 이를 통해 RSD가 탐색 기반 방법보다 우수한 성능을 보임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Comparison with search-based methods. Beam Search and Process Best-of-N𝑁Nitalic_N use a 1.5B base model and a 1.5B PRM.
> </details>

{{< table-caption >}}
| Method | Target | Draft | PRM | Setting | Avg. Accuracy |
|---|---|---|---|---|---| 
| Single Model | 7B | - | - | - | 65.3 |
| SD | 7B | 1.5B | - | - | 64.6 (-0.7) |
| RSD | 7B | 1.5B | 1.5B | δ=0.7 | 65.9 (+0.6) |
| RSD | 7B | 1.5B | 7B | δ=0.7 | 66.1 (+0.8) |
| RSD | 7B | 1.5B* | 1.5B* | δ=0.7 | 65.0 (-0.3) |
| RSD | 7B* | 1.5B | 7B* | δ=0.7 | 66.7 (+1.4) |{{< /table-caption >}}
> 🔼 표 4는 모델 병합의 정확도를 보여줍니다.  * 표시는 두 모델을 병합했음을 나타냅니다.  자세한 설정 및 수치는 본문의 §B.3절을 참조하십시오. 이 표는 다양한 모델 구성(대상 모델, 초안 모델, 보상 모델)을 사용한 실험 결과를 보여주며, 각 구성에 따른 모델 병합의 정확도를 비교 분석합니다.  특히, 대상 모델과 초안 모델을 각각 보상 모델과 병합한 경우의 정확도 변화를 통해 모델 병합 전략의 효과를 확인할 수 있습니다.  단일 모델의 성능과 비교하여 모델 병합 전략의 효율성과 정확도 개선 효과를 평가합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Accuracy of model merge. ∗ denotes that we merge these two models. Refer to §B.3 for detailed setting and number.
> </details>

{{< table-caption >}}
| Method | Target | Draft | PRM | Setting | CN Middle School 24 | College Math |
|---|---|---|---|---|---|---|
| Single Model | - | 1.5B | - | - | 75.2 | 48.0 |
| Single Model | 7B | - | - | - | 72.3 | 46.8 |
| SD | 7B | 1.5B | - | - | 73.3 | 46.9 |
| RSD | 7B | 1.5B | 7B | δ=0.7 | 78.2 | 48.2 |{{< /table-caption >}}
> 🔼 표 B.1은 CN 중학교 24 (Yang et al., 2024b) 및 대학 수학 (Tang et al., 2024) 데이터셋에서의 정확도를 보여줍니다. SD는 엄격한 비편향성으로 인해, 초안 모델이 목표 모델보다 성능이 우수한 경우 초안 모델보다 정확도가 낮아지는 현상이 발생하지만, RSD는 이러한 문제가 없습니다.  즉, 이 표는  두 가지 다른 수학 관련 데이터셋에서 단일 모델, SD, 그리고 RSD의 성능을 비교하여 RSD의 장점을 보여주는 표입니다.  특히, 초안 모델의 성능이 더 좋은 경우에도 RSD는 SD보다 더 좋은 성능을 보여주는 점이 강조되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table B.1: Accuracy on CN Middle School 24 (Yang et al., 2024b) and College Math (Tang et al., 2024). Due to SD’s strict unbiasedness, it achieves worse accuracy than the draft model if the draft model outperforms the target model, while RSD doesn’t have this issue.
> </details>

{{< table-caption >}}
Method | Target | Draft | PRM | Setting | MATH500 | GSM8K | GaoKao | Olympiad | GPQA | MMLU | Avg. |  
---|---|---|---|---|---|---|---|---|---|---|---|---
Math Model, Target and Draft: Qwen2.5-Math-Instruct, PRM: Skywork-o1-Open-PRM |  |  |  |  |  |  |  |  |  |  |  
RSD | 7B | 1.5B | 1.5B | $
\delta=0.6$ | 80.4 | 93.3 | 67.8 | 40.6 | 32.3 | 69.1 | 63.9  
RSD | 7B | 1.5B | 1.5B | $
\delta=0.7$| 82.6 | 94.5 | 68.8 | 39.6 | 38.4 | 71.4 | 65.9  
RSD | 7B | 1.5B | 1.5B | $
\delta=0.8$ | 82.6 | 95.3 | 68.1 | 39.4 | 37.4 | 71.7 | 65.8  
RSD | 7B | 1.5B | 1.5B | $
\delta=0.9$ | 81.2 | 95.5 | 68.3 | 39.4 | 32.3 | 71.6 | 64.7  
RSD | 7B | 1.5B | 7B | $
\delta=0.6$ | 83.6 | 95.4 | 68.3 | 43.6 | 30.3 | 71.6 | 65.5  
RSD | 7B | 1.5B | 7B | $
\delta=0.7$ | 84.6 | 95.5 | 68.3 | 42.1 | 33.8 | 72.3 | 66.1  
RSD | 7B | 1.5B | 7B | $
\delta=0.8$ | 83.6 | 95.8 | 67.8 | 40.9 | 34.3 | 72.6 | 65.8  
RSD | 7B | 1.5B | 7B | $
\delta=0.9$ | 83.4 | 95.7 | 68.1 | 40.1 | 32.8 | 72.5 | 65.4  
RSD | 72B | 1.5B | 1.5B | $
\delta=0.6$ | 83.0 | 93.5 | 71.9 | 48.4 | 36.9 | 78.1 | 68.6  
RSD | 72B | 1.5B | 1.5B | $
\delta=0.7$ | 83.6 | 94.7 | 72.7 | 47.7 | 40.4 | 82.5 | 70.3  
RSD | 72B | 1.5B | 1.5B | $
\delta=0.8$ | 86.6 | 95.6 | 71.4 | 48.0 | 40.9 | 85.1 | 71.3  
RSD | 72B | 1.5B | 1.5B | $
\delta=0.9$ | 85.4 | 95.6 | 72.2 | 47.7 | 44.4 | 85.5 | 71.8  
RSD | 72B | 1.5B | 7B | $
\delta=0.6$ | 85.8 | 96.0 | 72.5 | 49.0 | 41.9 | 82.5 | 71.3  
RSD | 72B | 1.5B | 7B | $
\delta=0.7$ | 86.8 | 96.3 | 72.7 | 49.0 | 41.9 | 84.6 | 71.9  
RSD | 72B | 1.5B | 7B | $
\delta=0.8$ | 87.4 | 96.3 | 73.0 | 48.3 | 40.9 | 85.4 | 71.9  
RSD | 72B | 1.5B | 7B | $
\delta=0.9$ | 86.2 | 96.0 | 72.7 | 48.9 | 41.4 | 85.6 | 71.8  
General Model, Target and Draft: Qwen2.5-Instruct, PRM: Skywork-o1-Open-PRM |  |  |  |  |  |  |  |  |  |  |  
RSD | 7B | 1.5B | 1.5B | $
\delta=0.6$ | 72.8 | 89.7 | 63.6 | 38.5 | 22.2 | 71.7 | 59.8  
RSD | 7B | 1.5B | 1.5B | $
\delta=0.7$ | 73.6 | 90.8 | 64.2 | 39.0 | 31.3 | 71.6 | 61.8  
RSD | 7B | 1.5B | 1.5B | $
\delta=0.8$ | 74.8 | 91.6 | 64.4 | 38.8 | 23.7 | 67.1 | 60.1  
RSD | 7B | 1.5B | 1.5B | $
\delta=0.9$ | 74.6 | 92.3 | 65.2 | 40.0 | 28.3 | 59.3 | 60.0  
General Model, Target and Draft: Llama-3.1-Instruct, PRM: Skywork-o1-Open-PRM |  |  |  |  |  |  |  |  |  |  |  
RSD | 8B | 1B | 1.5B | $
\delta=0.6$ | 49.0 | 82.6 | 40.8 | 18.1 | 19.2 | 34.5 | 40.7  
RSD | 8B | 1B | 1.5B | $
\delta=0.7$ | 50.0 | 83.9 | 41.8 | 15.7 | 20.2 | 37.2 | 41.5  
RSD | 8B | 1B | 7B | $
\delta=0.8$ | 48.6 | 84.1 | 41.8 | 16.3 | 18.7 | 38.8 | 41.4  
RSD | 8B | 1B | 7B | $
\delta=0.9$ | 50.0 | 84.0 | 43.4 | 15.3 | 17.7 | 38.6 | 41.5  
{{< /table-caption >}}
> 🔼 표 B.2는 다양한 δ 값에 따른 정확도를 보여줍니다. 전반적으로 δ=0.7이 다양한 모델과 작업에 적합하지만, 작업의 복잡도가 다르므로 δ를 약간 조정하면 정확도가 향상될 수 있습니다. 이 표는 다양한 모델(7B, 72B), 프롬프트 모델(1.5B, 7B), 그리고 과제 유형(수학, 일반)에 따른 여러 가지 설정에서 RSD의 성능을 보여줍니다. 각 설정에 대한 정확도를 GSM8K, MATH500, GaoKao 2023 En, Olympiad Bench, GPQA, 그리고 MMLU STEM과 같은 다양한 벤치마크에서 평가합니다.  δ 값을 0.6, 0.7, 0.8, 0.9로 변경하여 실험을 수행하고 결과를 비교 분석하여 최적의 δ 값을 찾습니다. 이를 통해 작업의 복잡도에 따른 최적의 δ 값을 찾고 RSD의 성능을 최적화하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table B.2: Accuracy with different δ𝛿\deltaitalic_δs. Overall, δ=0.7𝛿0.7\delta=0.7italic_δ = 0.7 works well for different models and tasks. However, since the complexity of different tasks varies, a slight tuning of δ𝛿\deltaitalic_δ offers better accuracy.
> </details>

{{< table-caption >}}
| Method | Target | Draft | PRM | Setting | MATH500 | GSM8K | GaoKao | Olympiad | GPQA | MMLU | Avg. |
|---|---|---|---|---|---|---|---|---|---|---|---| 
| Math Model, Target and Draft: Qwen2.5-Math-Instruct, PRM: Skywork-o1-Open-PRM |  |  |  |  |  |  |  |  |  |  |  |
| Single Model | 7B | - | - | - | 83.2 | 95.7 | 66.8 | 41.2 | 32.8 | 71.8 | 65.3 |
| SD | 7B | 1.5B | - | - | 83.4 | 95.6 | 67.3 | 40.6 | 28.8 | 72.0 | 64.6 (-0.7) |
| RSD | 7B | 1.5B | 1.5B | δ=0.7 | 82.6 | 94.5 | 68.8 | 39.6 | 38.4 | 71.4 | 65.9 (+0.6) |
| RSD | 7B | 1.5B | 7B | δ=0.7 | 84.6 | 95.5 | 68.3 | 42.1 | 33.8 | 72.3 | 66.1 (+0.8) |
| RSD | 7B | 1.5B* | 1.5B* | δ=0.7 | 83.4 | 95.1 | 67.3 | 39.3 | 33.3 | 71.6 | 65.0 (-0.3) |
| RSD | 7B* | 1.5B | 7B* | δ=0.7 | 84.0 | 95.6 | 69.4 | 43.0 | 35.4 | 72.6 | 66.7 (+1.4) |{{< /table-caption >}}
> 🔼 표 B.3는 모델 병합의 정확도를 보여줍니다.  이 표는 기본 모델(7B)과 보조 모델(1.5B 또는 7B)을 단독으로 사용했을 때의 정확도와,  두 모델을 다양한 방식으로 병합하여 사용했을 때의 정확도를 비교 분석합니다.  * 표시는 두 모델을 병합하여 사용한 경우를 나타냅니다.  단일 모델(Single Model)의 결과는 비교를 위한 기준선으로 사용됩니다.  표에는 MATH500, GSM8K, GaoKao 2023 En, Olympiad Bench, GPQA, MMLU Diamond STEM 등 다양한 추론 벤치마크에 대한 정확도가 제시되어 있으며,  각 벤치마크에서 병합 방식에 따른 정확도 변화를 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table B.3: Accuracy of model merge. ∗ denotes that we merge these two models.
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