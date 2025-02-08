---
title: "PILAF: Optimal Human Preference Sampling for Reward Modeling"
summary: "PILAF: 인간 선호도 데이터 수집 방식 개선으로 RLHF 효율 극대화!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 NYU",]
showSummary: true
date: 2025-02-06
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.04270 {{< /keyword >}}
{{< keyword icon="writer" >}} Yunzhen Feng et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-07 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.04270" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.04270" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)을 인간의 가치와 정렬시키는 RLHF(Reinforcement Learning from Human Feedback)는 중요한 연구 분야입니다.  하지만, RLHF는 **인간 선호도 데이터 수집에 많은 비용**이 들고, **기존의 근사적 보상 모델은 인간의 가치를 일관되게 최대화하지 못하는 문제**가 있습니다.  이러한 문제는 모델의 성능과 효율성을 저해하는 요인이 됩니다.

본 논문에서는 PILAF(Policy-Interpolated Learning for Aligned Feedback)라는 새로운 접근 방식을 제시합니다. PILAF는 선호도 라벨링을 위한 **새로운 응답 샘플링 전략**으로, 보상 모델 최적화와 가치 극대화를 명시적으로 정렬합니다.  **이론적 근거**를 바탕으로, 최적화 및 통계적 관점에서 PILAF의 효율성을 증명하고, 실험을 통해 기존 방법보다 우수한 성능을 보여줍니다.  PILAF는 **데이터 수집 과정을 간소화하여 비용을 절감**하고, **반복적 및 온라인 RLHF 환경**에서 강력한 성능을 보여줍니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} PILAF는 인간 선호도 데이터 수집 과정의 효율성을 높이는 새로운 방법론입니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} PILAF는 이론적으로 최적화 및 통계적 관점에서 모두 효율성을 증명하였습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} PILAF는 실험을 통해 기존 방법보다 우수한 성능과 효율성을 입증하였습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **RLHF(Reinforcement Learning from Human Feedback)**에서 **인간 선호도 데이터 수집의 효율성을 높이는 새로운 방법론**을 제시하여, 기존 방법의 한계를 극복하고 **모델 성능 및 효율성을 향상**시킬 수 있는 가능성을 보여줍니다.  **현재 AI 분야의 주요 연구 트렌드**인 RLHF의 효율성을 높이는 데 기여하며, **향후 연구 방향**에 대한 시사점을 제공합니다. 특히, 제한된 인적 자원을 효율적으로 활용하여 AI 모델을 최적화하고자 하는 연구에 큰 영향을 미칠 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.04270/x1.png)

> 🔼 본 그림은 PILAF 접근 방식에 대한 개요를 보여줍니다. (a)는 RLHF 학습 과정의 개요를 보여줍니다. 언어 모델 정책(LM policy)은 선호도 레이블링을 위해 데이터를 수집하는 적극적인 데이터 수집을 통해 반복적으로 개선됩니다. PILAF의 목표는 최적의 응답 샘플링 방법을 개발하는 것입니다. (b)는 PILAF를 소개합니다. PILAF는 현재 정책과 참조 정책 간의 보간을 통해 응답을 생성하여 탐색과 활용 간의 균형을 맞춥니다. (c)는 T-PILAF가 매개변수 기울기를 인간의 가치를 극대화하는 가장 가파른 방향과 정렬하고, 민감도가 높은 영역에서 더 나은 수렴을 달성함을 보여주는 이론적 분석을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Overview of our approach. (a) We consider a full RLHF training setup, where a language model (LM) policy is iteratively refined through active data collection. Our goal is to develop an optimal response sampling method for preference labeling. (b) We introduce PILAF, which generates responses by interpolating between the current policy and a reference policy, balancing exploration and exploitation. (c) Our theoretical analysis shows that T-PILAF aligns the parameter gradient with the steepest direction for maximizing human values and achieves more favorable convergence in regions of high sensitivity.
> </details>





{{< table-caption >}}
| Yunzhen Feng<sup>†</sup> | Ariel Kwiatkowski<sup>∗</sup> | Kunhao Zheng<sup>∗</sup> | Julia Kempe<sup>⋄</sup> | Yaqi Duan<sup>⋄</sup> |
|---|---|---|---|---|
| NYU | Meta FAIR | Meta FAIR | Meta FAIR & NYU | NYU |{{< /table-caption >}}

> 🔼 표 1은 제안된 PILAF 방법과 관련 연구에서 사용된 다른 샘플링 방법들의 비용을 비교 분석한 표입니다.  Xiong et al. (2024)의 Best-of-N 방법은 오라클 보상을 사용하여 모든 후보 응답을 평가한 후 최고점과 최저점을 선택하는 방식이지만, 본 논문에서는 오라클이 두 개의 응답만 비교하여 선호도 레이블을 제공하도록 제한합니다. 따라서, 본 논문에서는 DPO 내부 보상을 사용하여 응답을 선택한 후 선호도 레이블링을 적용하는 Best-of-N 변형 방식을 추가하여 제안된 PILAF 방법과 비교 분석합니다.  표에는 각 방법의 샘플링 비용과 주석 비용이 요약되어 있습니다.  특히 PILAF 방법의 효율성을 강조하기 위해 비용을 상세히 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 1:  A cost summary of PILAF and sampling methods from related works. Best-of-N method in Xiong et al. (2024) uses the oracle reward to score all candidate responses, then selects the highest- and lowest-scoring ones—instead of providing a preference label for only two responses. We restrict the oracle to providing only preference labels. Thus, we create a Best-of-N variant that uses the DPO internal reward for selection and then applies preference labeling, with an annotation cost of 2. We compare with this variant in the experiment.
> </details>





### In-depth insights


#### Optimal Sampling
본 논문에서 'Optimal Sampling'이라는 개념은 **인간의 선호도 데이터를 효율적으로 수집하는 방법**에 대한 고찰을 의미합니다.  기존의 RLHF(Reinforcement Learning from Human Feedback) 방식은 무작위 샘플링에 의존하여, 인간의 피드백이 제한적인 상황에서 모델의 성능 향상에 어려움을 겪습니다. 이에 따라 제시된  PILAF (Policy-Interpolated Learning for Aligned Feedback)는 **정책 간 보간을 통한 샘플링 전략**을 사용하여, 탐험과 활용의 균형을 맞추고, **오라클 보상을 극대화하는 방향**으로 학습을 효율적으로 유도합니다.  **이론적 근거**와 **실험 결과**를 통해 PILAF가 기존 방법보다 우수한 성능을 보임을 입증합니다.  특히, 제한된 인간 피드백 환경에서 **데이터 효율성**과 **모델 성능**을 동시에 개선하는 핵심 전략으로서,  **오라클 보상과 정책 최적화의 정렬**을 강조합니다.

#### Reward Alignment
강화학습에서 보상 함수는 에이전트의 행동을 유도하는 핵심 요소입니다.  **보상 정렬 (Reward Alignment)**은 학습된 에이전트가 의도한 대로 행동하도록 보상 함수를 설계하고 미세 조정하는 과정을 의미합니다.  **인간의 선호도를 정확히 반영하는 보상 함수를 만드는 것은 매우 어렵습니다.**  이는 인간의 가치 판단이 모호하고 일관성이 부족하며, 보상 함수의 설계 및 평가 과정 자체가 주관적일 수 있기 때문입니다.  본 논문에서 제시된 PILAF 알고리즘은 **인간의 피드백을 효율적으로 수집 및 활용하여 보상 함수를 최적화**하는 데 초점을 맞추고 있습니다.  **PILAF의 핵심은 정책 보간을 통한 탐험과 활용의 균형**입니다.  이는 기존 정책과 참조 정책 사이를 보간하여 데이터를 수집함으로써, 보상 모델 학습과 정책 최적화 사이의 불일치를 줄이고, 인간의 가치와 더욱 잘 정렬된 에이전트를 학습할 수 있도록 합니다.  **PILAF의 이론적 근거는 최적화 및 통계적 관점에서 보상 함수 최적화의 효율성을 보장**합니다.  실험 결과는 PILAF가 기존 방법들보다 우수한 성능을 보이며, 특히 반복적인 강화학습 환경에서 효과적임을 보여줍니다.

#### Theoretical Guarantees
본 논문에서 제시된 이론적 보장은 주로 **최적화 및 통계적 관점**에서 PILAF의 성능을 분석합니다.  **최적화 관점**에서는 PILAF의 샘플링 전략이 보상 모델링과 가치 최적화를 정렬시켜, 정책이 오라클 보상을 극대화하는 방향으로 학습될 수 있음을 보여줍니다.  이러한 정렬은 이론적으로 **기울기 정렬 특성**을 통해 증명되며, 효율적인 학습과 일반화 개선의 가능성을 시사합니다. **통계적 관점**에서는 PILAF가 샘플링된 선호도 데이터의 분산을 줄이고, 추정된 매개변수의 분포에 대한 **점근적(asymptotic) 결과**를 제시하여, 제한된 데이터로도 효율적이고 안정적인 학습을 가능하게 함을 보여줍니다.  즉, PILAF는 이론적으로 **최적화 및 통계적 효율성** 모두를 보장하는 샘플링 전략임을 제시하며, 실험 결과와 함께 이러한 이론적 결과들을 뒷받침합니다.

#### Empirical Validation
본 논문의 "실증적 검증" 부분은 제안된 방법의 실제 성능을 평가하는 데 중점을 둡니다.  **다양한 설정 하에서의 실험 결과를 통해 제안된 방법의 우수성을 보여주는 것이 중요합니다.** 이를 위해, **기존 방법들과의 비교 분석을 통해 제안된 방법의 성능 향상 및 효율성을 정량적으로 제시해야 합니다.**  단순한 성능 비교뿐만 아니라, **계산 비용, 데이터 효율성, 안정성 등 다양한 측면에서의 비교가 필요합니다.** 또한, **다양한 데이터셋 및 실험 환경에서의 견고성을 검증하는 것이 중요합니다.** 이러한 실험 결과들은 제안된 방법의 실용성과 일반화 가능성을 보여주는 데 중요한 역할을 합니다.  **실험 결과 분석에서는 통계적 유의성을 확보하고, 결과 해석에 있어서 신중한 접근이 필요합니다.**  결론적으로, "실증적 검증" 부분은 제안된 방법의 장점과 한계를 명확하게 제시하고, 향후 연구 방향을 제시하는 데 중요한 역할을 수행합니다.  **실험 설계의 타당성과 결과 해석의 정확성이 실증적 검증의 성공 여부를 결정짓는 중요한 요소**임을 강조합니다.

#### Future Extensions
본 논문은 RLHF(Reinforcement Learning from Human Feedback)에서 보상 모델링과 정책 최적화의 정렬을 개선하기 위해 PILAF(Policy-Interpolated Learning for Aligned Feedback)라는 새로운 샘플링 전략을 제시합니다.  **미래 확장 가능성**으로는, **다른 RLHF 패러다임(KTO, IPO 등)에 PILAF 적용 및 확장**을 고려할 수 있습니다.  또한, **더 큰 규모의 실험 및 실제 인간 피드백**을 통한 검증으로 결과의 일반화 가능성을 높일 수 있습니다.  **다양한 보상 모델과의 호환성 검토**도 중요한데,  다양한 모델에서 PILAF의 성능과 효율성을 평가하여 **범용성을 높이는 연구**가 필요합니다.  마지막으로, **PILAF를 활용한 오프라인 RLHF 및 온라인 RLHF 환경에서의 비교 분석**을 통해 PILAF의 적응력과 강건성을 평가하고 이를 바탕으로 보다 효율적이고 실용적인 RLHF 방법론을 제시하는 후속 연구가 기대됩니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.04270/x2.png)

> 🔼 그림 2는 반복적 DPO(Direct Preference Optimization) 설정에서 보상-KL 곡선을 보여줍니다. 모든 훈련 실행은 Vanilla Sampling을 통해 첫 번째 반복의 끝에서 얻은 동일한 모델에서 시작합니다. 각 점은 50번의 훈련 단계마다 수행된 평가를 나타냅니다. 이 그래프는 PILAF(Policy-Interpolated Learning for Aligned Feedback)가 반복적 DPO 환경에서 보상을 극대화하고 참조 모델과의 KL(Kullback-Leibler) 발산을 줄이는 데 효과적임을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Reward-KL curve for Iterative DPO. All training runs start from the same model obtained at the end of the first iteration via Vanilla Sampling. Each dot represents an evaluation performed every 50 training steps.
> </details>



![](https://arxiv.org/html/2502.04270/x3.png)

> 🔼 그림 3은 온라인 DPO 설정에서의 보상-KL 곡선을 보여줍니다. 각 점은 50번의 학습 단계마다 수행된 평가를 나타냅니다. 이 그래프는 온라인 학습 환경에서 PILAF 방법의 성능을 보여주는 데 중점을 둡니다. 즉, 모델이 학습하는 동안 지속적으로 미세 조정되고 새로운 선호도 데이터가 수집됩니다. 이는 모델이 인간의 선호도에 맞춰 효율적으로 학습될 수 있는지를 보여주는 시각적 자료입니다.  Vanilla, Hybrid, Best-of-N 등의 다른 방법과 비교하여 PILAF 방법이 보상을 높이고 참조 모델과의 KL 발산을 낮추는 방식을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Reward-KL curve for Online DPO. Each dot represents an evaluation performed every 50 training steps.
> </details>



![](https://arxiv.org/html/2502.04270/x4.png)

> 🔼 그림 4는 과적합된 초기 정책을 사용한 온라인 DPO의 결과를 보여줍니다. 각 점은 50번의 학습 단계마다 수행된 평가를 나타내며, 색상의 채도는 학습 단계를 나타냅니다. 어두운 색상일수록 더 늦은 단계임을 의미합니다. 이 그림은 과적합된 초기 정책으로 학습을 시작했을 때, PILAF가 기존 방법들보다 얼마나 더 강건하고 효율적인지 보여주는 실험 결과를 시각적으로 보여줍니다.  Vanilla Sampling의 경우 KL divergence가 급격히 증가하고 reward 향상은 정체되는 반면, PILAF는 초기에는 KL divergence 변동이 있지만, 결국 더 높은 reward와 더 낮은 KL divergence를 달성합니다. 이는 PILAF의 탐색 전략이 과적합된 초기 정책으로 인해 발생하는 지역적 최적화 문제에서 벗어나는 데 도움이 됨을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Online DPO with an overfitted initial policy. Each dot represents an evaluation performed every 50 training steps. Color saturation indicates the training step, with darker colors representing later steps.
> </details>



![](https://arxiv.org/html/2502.04270/x5.png)

> 🔼 그림 5는 과적합된 초기 정책을 사용한 온라인 DPO의 결과를 보여줍니다. 그림 4의 전체 결과를 보여주는 이 그림은 각 점이 50회의 학습 단계마다 수행된 평가를 나타내고, 색상 채도는 학습 단계를 나타내며, 어두운 색상일수록 더 늦은 학습 단계를 의미합니다.  과적합된 초기 정책으로 시작하여 Vanilla Sampling과 PILAF의 성능을 비교 분석한 결과, PILAF는 초기 단계에서 KL 발산이 변동하지만, 더 높은 보상을 달성하는 정책을 얻고, Vanilla Sampling보다 KL 발산이 훨씬 낮았습니다. 이는 PILAF의 탐색 전략이 과적합된 초기 정책의 최적화 과정에서 도움이 되었다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Online DPO with an overfitted initial policy. Full results of the Figure 4. Each dot represents an evaluation performed every 50 training steps. Color saturation indicates the training step, with darker colors representing later steps.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | 
\vec{\boldsymbol{y}}\!\,^{a} | 
\vec{\boldsymbol{y}}\!\,^{b} | Sampling Cost | Annotation Cost |
|---|---|---|---|---|
| *Vanilla* (Rafailov et al., 2023) | 
\uppi_{\theta} | 
\uppi_{\theta} | 2 | 2 |
| *Best-of-N* (Xiong et al., 2024), N=8 | best of \uppi_{\theta} | worst of \uppi_{\theta} | 8 | 8* |
| *Best-of-N* (with DPO reward), N=8 | best of \uppi_{\theta} | worst of \uppi_{\theta} | 8 | 2 |
| *Hybrid* (Xie et al., 2024) | \uppi_{\theta} | \uppi_{\text{ref}} | 2 | 2 |
| *PILAF* (OURS) | \uppi_{\theta}^{+}/\uppi_{\theta} | \uppi_{\theta}^{-}/\uppi_{\theta} | 3 | 2 |{{< /table-caption >}}
> 🔼 표 2는 반복적 DPO(Direct Preference Optimization) 결과를 보여줍니다. 테스트 세트에서 평균 보상, 참조 모델과의 KL(Kullback-Leibler) 발산, 그리고 목적 함수 J의 값을 보고합니다. 보상과 목적 함수 J 값이 높을수록, KL 발산이 낮을수록 성능이 좋습니다. 가장 좋은 결과는 굵게 표시하고, 두 번째로 좋은 결과는 밑줄로 표시했습니다. 이 표는 반복적 DPO 설정에서 PILAF(Policy-Interpolated Learning for Aligned Feedback) 방법의 효과를 보여주는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Results of Iterative DPO. We report the average reward, KL divergence from the reference model, and objective J𝐽Jitalic_J on the testset. Higher reward and J𝐽Jitalic_J are better, while lower KL divergence is better. We use boldface to indicate the best result and underline to denote the second-best result.
> </details>

{{< table-caption >}}
| Method | Reward (↑) | KL (↓) | J (↑) |
|---|---|---|---|
| *Vanilla* | -10.16 | 35.20 | -13.68 |
| *Best-of-N* | -10.13 | 32.38 | -13.37 |
| *Hybrid* | -10.51 | 22.86 | -12.80 |
| *PILAF* (Ours) | -9.80 | 25.01 | -12.30 |{{< /table-caption >}}
> 🔼 표 3은 본 논문의 온라인 DPO(Direct Preference Optimization) 실험 결과를 보여줍니다.  테스트 세트를 기준으로 평균 보상, 참조 모델(reference model)과의 KL(Kullback-Leibler) 발산, 그리고 목적 함수 J의 값을 제시합니다.  더 높은 보상과 J 값은 더 좋은 성능을, 낮은 KL 발산은 참조 모델과의 더 높은 유사성을 의미합니다. 이 표는 PILAF 방법이 다른 방법들에 비해 더 높은 보상과 더 낮은 KL 발산을 달성함을 보여주는 데 중요한 역할을 합니다.  즉, PILAF가 인간의 선호도를 더 잘 반영하는 정책을 학습한다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Results of Online DPO. We report the average reward, KL divergence from the reference model, and objective J𝐽Jitalic_J on the testset.
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