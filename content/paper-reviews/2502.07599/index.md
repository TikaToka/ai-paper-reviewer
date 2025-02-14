---
title: "DPO-Shift: Shifting the Distribution of Direct Preference Optimization"
summary: "DPO-Shift는 **기존 직접 선호도 최적화(DPO)의 신뢰도 편향 문제를 해결**하기 위해 제안된 새로운 방법론입니다.  **선호도 확률 분포를 제어**하여 신뢰도 편향을 완화하고 다운스트림 작업에서 성능을 개선함을 보여줍니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 School of Data Science, The Chinese University of Hong Kong, Shenzhen",]
showSummary: true
date: 2025-02-11
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.07599 {{< /keyword >}}
{{< keyword icon="writer" >}} Xiliang Yang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-13 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.07599" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.07599" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/dpo-shift-shifting-the-distribution-of-direct" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)을 인간의 선호도에 맞추는 것은 AI 분야의 중요한 과제입니다. 직접 선호도 최적화(DPO)는 이를 위한 효과적인 방법으로 주목받았지만, **훈련 과정에서 선택된 응답의 확률이 감소하는 신뢰도 편향 문제**가 있습니다. 이는 모델의 일반화 능력 저하로 이어질 수 있습니다.

본 논문에서는 이 문제를 해결하기 위해 **DPO-Shift**라는 새로운 방법론을 제안합니다.  DPO-Shift는 선호도 확률 분포를 제어하여 신뢰도 편향을 완화하고, 선택 확률과 보상 마진 간의 균형을 제어하는 매개변수를 도입합니다. 실험 결과, DPO-Shift는 기존 DPO보다 **다운스트림 작업에서 우수한 성능**을 보이며 신뢰도 편향 문제를 효과적으로 완화함을 보여줍니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} DPO-Shift는 **직접 선호도 최적화(DPO)의 신뢰도 편향 문제를 해결**하는 새로운 방법론이다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} DPO-Shift는 **선택 확률을 개선**하지만 **보상 마진을 희생**하는 **기본적인 트레이드오프**를 보여준다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} DPO-Shift는 **다운스트림 작업에서 DPO보다 우수한 성능**을 보여준다.  {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **직접 선호도 최적화(DPO)**의 한계점을 해결하는 새로운 방법론인 **DPO-Shift**를 제시하여, 기존 DPO의 **가능성과 한계**를 명확히 밝히고 향상된 성능을 보여주는 연구입니다.  **기존 DPO의 신뢰도 편향 문제를 효과적으로 완화**하여, 더 나은 언어 모델 정렬을 가능하게 합니다. 이는 **다양한 응용 분야에서의 언어 모델 개선**에 기여할 수 있으며, **추후 연구**를 위한 새로운 방향을 제시합니다. 따라서, 언어 모델 정렬 및 향상에 관심 있는 연구자들에게 **중요한 지침**이 될 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.07599/x1.png)

> 🔼 그림 1은 세 가지 모델(SFT된 Llama 3-8B, DPO-Shift 전략으로 훈련된 모델, DPO로 훈련된 모델)에 대한 두 가지 분포를 보여줍니다. 왼쪽은 선택된 응답(yw)과 기각된 응답(yl)의 로그 확률(log πθ(yw|x) 와 log πθ(yl|x)) 분포를 나타내고, 오른쪽은 보상 차이(r(x, yw) - r(x, yl))에 대한 커널 밀도 추정(KDE)을 나타냅니다. 보상 정확도(r(x, yw) - r(x, yl) > 0인 (x, yw, yl) 샘플의 평균)도 함께 표시됩니다. y축 범위는 모든 하위 그림에서 동일합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Left: Distribution of log⁡πθ⁢(𝒚w|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑤𝒙\log\pi_{\theta}(\boldsymbol{y}_{w}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_w end_POSTSUBSCRIPT | bold_italic_x ) and log⁡πθ⁢(𝒚l|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑙𝒙\log\pi_{\theta}(\boldsymbol{y}_{l}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_l end_POSTSUBSCRIPT | bold_italic_x ). Right: Kernel density estimation (KDE) for the reward margin (r⁢(𝒙,𝒚w)−r⁢(𝒙,𝒚l))𝑟𝒙subscript𝒚𝑤𝑟𝒙subscript𝒚𝑙(r(\boldsymbol{x},\boldsymbol{y}_{w})-r(\boldsymbol{x},\boldsymbol{y}_{l}))( italic_r ( bold_italic_x , bold_italic_y start_POSTSUBSCRIPT italic_w end_POSTSUBSCRIPT ) - italic_r ( bold_italic_x , bold_italic_y start_POSTSUBSCRIPT italic_l end_POSTSUBSCRIPT ) ). The reward accuracy, which is the sample mean of 1⁢{(𝒙,𝒚w,𝒚l)|r⁢(𝒙,𝒚w)−r⁢(𝒙,𝒚l)>0}1conditional-set𝒙subscript𝒚𝑤subscript𝒚𝑙𝑟𝒙subscript𝒚𝑤𝑟𝒙subscript𝒚𝑙01\{(\boldsymbol{x},\boldsymbol{y}_{w},\boldsymbol{y}_{l})|r(\boldsymbol{x},% \boldsymbol{y}_{w})-r(\boldsymbol{x},\boldsymbol{y}_{l})>0\}1 { ( bold_italic_x , bold_italic_y start_POSTSUBSCRIPT italic_w end_POSTSUBSCRIPT , bold_italic_y start_POSTSUBSCRIPT italic_l end_POSTSUBSCRIPT ) | italic_r ( bold_italic_x , bold_italic_y start_POSTSUBSCRIPT italic_w end_POSTSUBSCRIPT ) - italic_r ( bold_italic_x , bold_italic_y start_POSTSUBSCRIPT italic_l end_POSTSUBSCRIPT ) > 0 } is listed. The three rows are plotted with three models including the SFTed Llama 3-8B, the model trained by one strategy of DPO-Shift, and the model trained by DPO (from top to bottom), separately. The ranges of the y-axis of all subfigures are the same.
> </details>





{{< table-caption >}}
| $f(\lambda)$ strategy | Llama 3-8B | Qwen 2-7B |
|---|---|---|
| **SFT** | 5.64 | 5.88 |
| **DPO** | 6.513 | 6.875 |
| `fixed` 0.5 | 6.118 | 6.150 |
| `fixed` 0.55 | 6.269 | 6.369 |
| `fixed` 0.6 | 6.169 | 6.331 |
| `fixed` 0.65 | 6.314 | 6.494 |
| `fixed` 0.7 | 6.500 | 6.581 |
| `fixed` 0.75 | 6.444 | 6.700 |
| `fixed` 0.8 | **6.731** | 6.869 |
| `fixed` 0.85 | 6.644 | 6.775 |
| `fixed` 0.9 | **6.738** | 6.725 |
| `fixed` 0.95 | 6.444 | 6.875 |
| `increase_linear` 0.75 | **6.588** | 6.775 |
| `increase_linear` 0.85 | 6.425 | 6.806 |
| `increase_linear` 0.95 | 6.519 | **7.044** |
| `decrease_linear` 0.75 | **6.613** | 6.742 |
| `decrease_linear` 0.85 | 6.481 | **6.906** |
| `decrease_linear` 0.95 | **6.606** | **6.944** |{{< /table-caption >}}

> 🔼 표 1은 UltraFeedback 데이터셋으로 학습된 Llama 3-8B 및 Qwen 2-7B 모델에 대한 MT-Bench(Zheng et al., 2023) 결과를 보여줍니다.  GPT-4가 평가 모델로 사용되었습니다.  표에는 기준 DPO 방법과 비교하여 DPO-Shift의 성능을 보여주는 세 가지 전략(fixed, linear_increase, linear_decrease)에 대한 결과가 포함되어 있습니다. DPO보다 성능이 좋은 결과는 굵게 표시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: MT-Bench (Zheng et al., 2023) results for Llama 3-8B and Qwen 2-7B trained on UltraFeedback, where GPT-4o is the judge model. The results better than DPO is bolded. Results for fixed, linear_increase, and linear_decrease are included.
> </details>





### In-depth insights


#### DPO's Shortcomings
본 논문에서 다루는 DPO(Direct Preference Optimization)의 주요 단점은 **가능도 변위(likelihood displacement)** 현상입니다. 이는 훈련 과정에서 선택된 응답의 확률이 감소하는 현상으로, 모델이 선호되는 응답과 기피되는 응답을 제대로 구분하지 못하게 되는 문제를 야기합니다. 이러한 현상은 모델의 용량 제한, 다수의 훈련 샘플 또는 출력 토큰, 초기 SFT(Supervised Fine-Tuning) 단계 등 여러 요인으로 인해 발생할 수 있습니다. **가능도 변위는 모델의 일반화 능력을 저해하고, 선호도가 없는 응답에 대한 확률을 예상치 못하게 증가시킬 수 있습니다.** 따라서 DPO의 효과적인 개선을 위해서는 이러한 가능도 변위 문제를 해결하는 것이 필수적입니다.  **본 논문은 DPO-Shift를 통해 이러한 문제를 해결하고자 합니다.** DPO-Shift는 선택된 확률의 분포를 제어하여 가능도 변위 문제를 완화시키는 동시에, 선택된 확률 향상과 보상 여유 감소 사이의 기본적인 트레이드오프를 보여줍니다. 이는 이론적 분석과 실험적 검증을 통해 뒷받침됩니다.

#### DPO-Shift: A Remedy
DPO-Shift는 기존 직접 선호도 최적화(DPO)의 한계를 극복하기 위한 **해결책**으로 제시됩니다. 기존 DPO는 학습 과정에서 선택된 응답의 확률이 감소하는 현상인 **우도 변위** 문제를 가지고 있습니다. 이는 모델의 일반화 능력 저하로 이어질 수 있습니다. DPO-Shift는 **선택 확률의 분포를 제어하여** 이 문제를 해결합니다.  **새로운 매개변수 함수 f(x)**를 도입하여 거절된 응답의 보상에 영향을 미쳐 선택 확률을 증가시키고 보상 간격을 조절하는 데 초점을 맞춥니다. 이는 선택 확률을 향상시키는 동시에 보상 간격을 유지하는 **기본적인 트레이드오프**를 보여줍니다.  **이론적 분석과 실험적 검증**을 통해 DPO-Shift의 우수성을 확인합니다.  다운스트림 작업에서도 DPO보다 우수한 성능을 보이며,  **선택 확률 조절 능력**을 실험적으로 증명합니다.  **단순성과 이론적 기반**을 바탕으로 DPO의 우도 변위 문제에 대한 효과적인 해결책을 제시한다는 점에서 큰 의의를 가집니다.

#### Trade-off Analysis
본 논문의 "Trade-off Analysis" 부분은 **DPO-Shift 알고리즘이 가져오는 기본적인 트레이드오프 관계**를 분석한 것으로 보입니다.  이는 선택 확률(chosen probability)을 향상시키는 것과 보상 마진(reward margin)을 유지하는 것 사이의 균형을 이루는 어려움을 다룹니다.  **이론적 분석과 실험적 검증을 통해 선택 확률을 높이면 보상 마진이 감소하고, 반대로 보상 마진을 유지하려면 선택 확률이 낮아진다는 점**을 보여줍니다.  **매개변수 함수 f(x)의 선택이 이러한 트레이드오프를 조절하는 중요한 역할**을 한다는 것을 강조하고,  실험 결과를 통해 최적의 f(x) 값을 찾는 방법을 제시합니다.  **단순히 선택 확률만 높이는 것이 아니라, 보상 마진과의 균형을 고려하여 모델 성능을 최적화**하는 데 중점을 두고 있음을 알 수 있습니다.  즉,  단순한 성능 향상이 아닌, **균형 잡힌 성능 개선을 위한 심층적인 분석**을 제공한다는 점에서 중요한 의미를 가집니다.  본 분석은 DPO-Shift 알고리즘의 실제 적용에 있어서 중요한 지침을 제공하고,  향후 연구 방향을 제시하는 데 기여합니다.  특히,  실험을 통해 얻은 결과는 이론적 분석을 뒷받침하며,  DPO-Shift의 실용성과 효율성을 보여줍니다.

#### Empirical Validation
본 논문의 "실증적 검증" 부분은 제시된 방법론의 실제 효과를 데이터 기반으로 평가하는 중요한 단계입니다.  **다양한 실험 설계와 충분한 데이터셋을 활용하여** 이루어진 검증은 신뢰도를 높입니다. 특히, **다양한 모델과 데이터셋에 대한 실험 결과**는 일반화 가능성을 보여주는 데 중요합니다.  **정량적 지표와 함께 정성적 분석을 병행한다면** 더욱 풍부한 결과 해석이 가능합니다.  예를 들어, 정량적 지표(예: 정확도, F1 스코어) 뿐 아니라, 모델 출력물의 질적 평가를 통해 방법론의 장단점을 명확하게 제시할 수 있습니다.  **실험 결과 분석 시 통계적 유의성 검정을 통해** 단순한 우연의 결과가 아닌, 실제 효과임을 밝히는 것이 중요합니다.  또한, 기존 방법론과의 비교 실험을 통해 **제시된 방법론의 우위성을 명확히 제시**하는 것이 중요하며,  **한계점과 개선 방향 제시**는 후속 연구에 대한 방향을 제시하고 논문의 신뢰성을 높입니다.  **재현성을 위해 실험 환경과 파라미터를 명확히 제시**하여 다른 연구자들이 결과를 재현하고 검증할 수 있도록 하는 것도 중요합니다.

#### Future Directions
본 논문에서 제시된 DPO-Shift는 기존 DPO의 likelihood displacement 문제를 해결하기 위한 효과적인 방법을 제시하지만, 여전히 개선의 여지가 있습니다. **향후 연구 방향**으로는 첫째, 다양한 f(x) 함수의 설계 및 성능 비교를 통한 최적화 전략 도출이 필요합니다.  둘째, **이론적 분석의 심화**를 통해 DPO-Shift의 성능을 더욱 정확하게 예측하고,  f(x) 함수의 선택에 대한 보다 명확한 가이드라인을 제공해야 합니다. 셋째, **다양한 데이터셋 및 모델에 대한 실험**을 통해 DPO-Shift의 일반화 성능을 검증하고, 실제 응용 분야에서의 효용성을 평가해야 합니다. 마지막으로, **DPO-Shift와 다른 방법론들과의 비교 연구**를 통해 상대적 장단점을 파악하고,  향후 연구 방향을 설정하는데 도움을 얻을 수 있을 것입니다. 이러한 노력을 통해 DPO-Shift는 더욱 강력하고 실용적인 언어 모델 정렬 기법으로 발전할 수 있을 것으로 기대됩니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.07599/x2.png)

> 🔼 그림 2는 UltraFeedback 데이터셋의 테스트셋 분할에서 UltraFeedback으로 학습된 Llama 3-8B 모델의 log πθ(yw|x)와 log πθ(yl|x)의 분포를 보여줍니다. 여기서 사용된 f(λ)는 고정 전략을 사용했습니다. 그림에는 제한된 f(λ)의 경우만 나열되어 있으며, 자세한 내용은 부록 A.2절을 참조하십시오. 모든 하위 그림의 y축 범위는 동일합니다. 이 그림은 DPO-Shift의 핵심 개념인 선택 확률 분포의 변화를 시각적으로 보여주는 데 중점을 둡니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Distribution for log⁡πθ⁢(𝒚w|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑤𝒙\log\pi_{\theta}(\boldsymbol{y}_{w}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_w end_POSTSUBSCRIPT | bold_italic_x ) and log⁡πθ⁢(𝒚l|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑙𝒙\log\pi_{\theta}(\boldsymbol{y}_{l}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_l end_POSTSUBSCRIPT | bold_italic_x ) on test set split of UltraFeedback for Llama 3-8B trained on UltraFeedback with fixed strategy. Only limited cases of f⁢(λ)𝑓𝜆f(\lambda)italic_f ( italic_λ ) are listed. For a full ablation study, please refer to Section A.2. The ranges of the y-axis of all subfigures are the same.
> </details>



![](https://arxiv.org/html/2502.07599/x3.png)

> 🔼 그림 3은 UltraFeedback 데이터셋으로 학습된 Llama 3-8B 모델에 대해, 고정된 f(λ) 값을 사용한 DPO-Shift의 보상 마진과 보상 정확도 분포를 보여줍니다. f(λ) 값이 0.55에서 0.95까지 변화함에 따라 보상 마진과 정확도의 변화를 보여주는 여러 하위 그림으로 구성되어 있습니다. 그림에서는 일부 f(λ) 값에 대한 결과만 제시하고 있으며, 자세한 내용은 부록 A.2절을 참조하라고 안내하고 있습니다. 모든 하위 그림의 y축 범위는 동일하게 설정되어 있습니다. 이 그림은 DPO-Shift의 f(λ) 매개변수가 모델 성능에 미치는 영향을 분석하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Distribution for reward margin and reward accuracy on test set split of UltraFeedback for Llama 3-8B trained on UltraFeedback with fixed strategy. Only limited cases of f⁢(λ)𝑓𝜆f(\lambda)italic_f ( italic_λ ) are listed. For a full ablation study, please refer to Section A.2. The ranges of the y-axis of all subfigures are the same.
> </details>



![](https://arxiv.org/html/2502.07599/x4.png)

> 🔼 그림 4는 UltraFeedback 데이터셋으로 학습된 Llama 3-8B 모델에 대해 고정된 f(λ) 전략을 사용하여 다양한 f(λ) 값([0.5, 0.55, 0.6, 0.65, 0.7, 0.75, 0.8, 0.85, 0.9, 0.95])에 따른 보상 정확도를 보여줍니다.  f(λ) 값이 증가함에 따라 보상 정확도가 어떻게 변하는지 보여주는 그래프입니다.  이 그래프는 DPO-Shift 방법의 성능을 평가하는 데 사용됩니다.  x축은 f(λ) 값을, y축은 보상 정확도를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Reward accuracy vs different f⁢(λ)𝑓𝜆f(\lambda)italic_f ( italic_λ ) (fixed strategy) for Llama 3-8B trained on UltraFeedback, where f⁢(λ)𝑓𝜆f(\lambda)italic_f ( italic_λ ) is selected from [0.5,0.55,0.6,0.65,0.7,0.75,0.8,0.85,0.9,0.95]0.50.550.60.650.70.750.80.850.90.95[0.5,0.55,0.6,0.65,0.7,0.75,0.8,0.85,0.9,0.95][ 0.5 , 0.55 , 0.6 , 0.65 , 0.7 , 0.75 , 0.8 , 0.85 , 0.9 , 0.95 ].
> </details>



![](https://arxiv.org/html/2502.07599/x5.png)

> 🔼 그림 5는 UltraFeedback 데이터셋으로 학습된 Llama 3-8B 모델에 대해 f(x) = 0.99인 DPO-Shift와 DPO의 성능을 비교 분석한 결과를 보여줍니다. 왼쪽 그림은 선택된 응답(y_w)의 로그 확률 분포 log πθ(yw|x)를 나타내며, 오른쪽 그림은 보상 정확도와 보상 마진의 분포를 보여줍니다.  두 모델의 선택된 응답 확률 분포와 보상 마진의 차이를 시각적으로 비교하여 DPO-Shift의 효과를 분석합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: The comparison between DPO-Shift with f⁢(λ)=0.99𝑓𝜆0.99f(\lambda)=0.99italic_f ( italic_λ ) = 0.99 and DPO on test set split of UltraFeedback for Llama 3-8B trained on UltraFeedback. Left: Distribution for log⁡πθ⁢(𝒚w|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑤𝒙\log\pi_{\theta}(\boldsymbol{y}_{w}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_w end_POSTSUBSCRIPT | bold_italic_x ). Right: Reward accuracy and distribution for reward margin.
> </details>



![](https://arxiv.org/html/2502.07599/x6.png)

> 🔼 그림 6은 UltraFeedback 데이터셋으로 학습된 Llama 3-8B 모델에 대한 테스트셋 결과를 보여줍니다.  고정 전략(f(λ) = 0.75)과 선형 감소 전략(λmin = 0.75)의 두 가지 f(x) 선택 전략을 비교 분석합니다. 왼쪽 그림은 선택된 응답(yw)과 기각된 응답(yl)의 로그 확률 분포를, 오른쪽 그림은 보상 정확도와 보상 마진 분포를 나타냅니다.  두 전략의 성능 차이와 보상 마진과 선택 확률 간의 상관관계를 시각적으로 보여주는 그림입니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: The comparison between fixed strategy with f⁢(λ)=0.75𝑓𝜆0.75f(\lambda)=0.75italic_f ( italic_λ ) = 0.75 and linear_decrease with λmin=0.75subscript𝜆0.75\lambda_{\min}=0.75italic_λ start_POSTSUBSCRIPT roman_min end_POSTSUBSCRIPT = 0.75 on test set split of UltraFeedback for Llama 3-8B trained on UltraFeedback. Left: Distribution for log⁡πθ⁢(𝒚w|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑤𝒙\log\pi_{\theta}(\boldsymbol{y}_{w}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_w end_POSTSUBSCRIPT | bold_italic_x ) and log⁡πθ⁢(𝒚l|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑙𝒙\log\pi_{\theta}(\boldsymbol{y}_{l}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_l end_POSTSUBSCRIPT | bold_italic_x ); Right: Reward accuracy and distribution for reward margin.
> </details>



![](https://arxiv.org/html/2502.07599/x7.png)

> 🔼 그림 7은 UltraFeedback 데이터셋으로 학습된 Llama 3-8B 모델을 사용하여 DPO와 DPO-Shift의 성능을 비교한 결과를 보여줍니다. UltraFeedback 데이터셋의 테스트 분할에서 가져온 질문들로 모델을 테스트했습니다. 이 실험은 DPO-Shift가 DPO보다 우수한 성능을 보이는지, 그리고 선택 확률과 보상 마진 사이의 균형을 어떻게 제어하는지를 보여주는 것을 목표로 합니다.  x축은 다양한 f(x) 전략을 나타내고 y축은 승률을 나타냅니다. 각 막대는 DPO-Shift와 DPO의 승률을 비교하여 DPO-Shift의 우위를 보여줍니다.  다양한 f(x) 값에 따른 승률 변화를 통해 DPO-Shift의 매개변수 조정의 효과를 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Win rate experiment against DPO using Llama 3-8B trained on the UltraFeedback dataset and tested with questions from the test split of UltraFeedback.
> </details>



![](https://arxiv.org/html/2502.07599/x8.png)

> 🔼 그림 8은 UltraFeedback 데이터셋으로 학습된 Llama 3-8B 모델에 대한 테스트셋 분할에서 log πθ(yw|x)와 log πθ(yl|x)의 분포를 보여줍니다. 여기서 DPO-Shift는 고정된 전략을 사용합니다.  각 하위 그림의 y축 범위는 동일합니다.  간단히 말해, 이 그림은 DPO-Shift 방법을 사용하여 다양한 f(x) 값에 따른 선택된 응답과 거부된 응답의 확률 분포를 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Distribution for log⁡πθ⁢(𝒚w|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑤𝒙\log\pi_{\theta}(\boldsymbol{y}_{w}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_w end_POSTSUBSCRIPT | bold_italic_x ) and log⁡πθ⁢(𝒚l|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑙𝒙\log\pi_{\theta}(\boldsymbol{y}_{l}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_l end_POSTSUBSCRIPT | bold_italic_x ) on test set split of UltraFeedback for Llama 3-8B trained on UltraFeedback, where DPO-Shift uses fixed strategy. The ranges of the y-axis of all subfigures are the same.
> </details>



![](https://arxiv.org/html/2502.07599/x9.png)

> 🔼 그림 9는 UltraFeedback 데이터셋으로 학습된 Llama 3-8B 모델에 대한 테스트셋 결과를 보여줍니다.  DPO-Shift 방법에서 고정된 f(x) 전략을 사용했을 때, 보상 마진과 보상 정확도의 분포를 나타냅니다.  각 하위 그림은 다른 f(x) 값에 해당하며, y축 범위는 모든 하위 그림에서 동일합니다.  이 그림을 통해 다양한 f(x) 값이 보상 마진과 정확도에 미치는 영향을 비교 분석할 수 있습니다. 특히,  f(x) 값의 변화에 따른 보상 마진 분포의 변화 양상과 보상 정확도 변화를 자세히 살펴볼 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Distribution for reward margin and reward accuracy on test set split of UltraFeedback for Llama 3-8B trained on UltraFeedback, where DPO-Shift uses fixed strategy. The ranges of the y-axis of all subfigures are the same.
> </details>



![](https://arxiv.org/html/2502.07599/x10.png)

> 🔼 그림 10은 Capybara 데이터셋으로 학습된 Llama 3-8B 모델에 대한 log πθ(yw|x)와 log πθ(yl|x)의 분포를 보여줍니다. 여기서 DPO-Shift는 고정된 전략(fixed strategy)을 사용합니다.  x는 프롬프트, yw는 선택된 응답, yl은 거부된 응답을 나타냅니다. 각 하위 그림의 y축 범위는 동일합니다. 이 그림은 DPO-Shift 방법이 모델의 선택 확률 분포에 어떻게 영향을 미치는지 시각적으로 보여줍니다.  각기 다른 f(x) 값에 따른 분포의 변화를 통해 likelihood displacement 문제 해결에 대한 DPO-Shift의 효과를 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Distribution for log⁡πθ⁢(𝒚w|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑤𝒙\log\pi_{\theta}(\boldsymbol{y}_{w}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_w end_POSTSUBSCRIPT | bold_italic_x ) and log⁡πθ⁢(𝒚l|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑙𝒙\log\pi_{\theta}(\boldsymbol{y}_{l}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_l end_POSTSUBSCRIPT | bold_italic_x ) on test set split of Capybara for Llama 3-8B trained on Capybara, where DPO-Shift uses fixed strategy. The ranges of the y-axis of all subfigures are the same.
> </details>



![](https://arxiv.org/html/2502.07599/x11.png)

> 🔼 그림 11은 캡션에서 언급한 것처럼 Capybara 데이터셋으로 학습된 Llama 3-8B 모델에 대한 결과를 보여줍니다.  DPO-Shift 기법을 사용하여  고정된 f(x) 전략을 적용했을 때의 보상 마진과 보상 정확도 분포를 보여줍니다.  각 하위 그림은 f(x) 값의 변화에 따른 결과를 나타내며, y축의 범위는 모두 동일하게 설정되어 있습니다.  이 그림을 통해 DPO-Shift의 고정된 f(x) 전략이 보상 마진 및 정확도에 미치는 영향을 시각적으로 비교 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Distribution for reward margin and reward accuracy on test set split of Capybara for Llama 3-8B trained on Capybara, where DPO-Shift uses fixed strategy. The ranges of the y-axis of all subfigures are the same.
> </details>



![](https://arxiv.org/html/2502.07599/x12.png)

> 🔼 그림 12는 UltraFeedback 데이터셋으로 학습된 Qwen 2-7B 모델에 대한 테스트셋 분할에서 log πθ(yw|x)와 log πθ(yl|x)의 분포를 보여줍니다. 여기서 DPO-Shift는 고정된 전략(fixed strategy)을 사용합니다.  모든 하위 그림의 y축 범위는 동일합니다. 이 그림은 DPO-Shift 방법이 고정된 f(x) 값을 사용할 때, 선택된 응답(yw)과 기각된 응답(yl)의 확률 분포에 어떻게 영향을 미치는지 시각적으로 보여줍니다.  각 하위 그림은 다른 f(x) 값에 따른 분포를 나타내며,  f(x) 값의 변화에 따른 분포 변화를 분석하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Distribution for log⁡πθ⁢(𝒚w|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑤𝒙\log\pi_{\theta}(\boldsymbol{y}_{w}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_w end_POSTSUBSCRIPT | bold_italic_x ) and log⁡πθ⁢(𝒚l|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑙𝒙\log\pi_{\theta}(\boldsymbol{y}_{l}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_l end_POSTSUBSCRIPT | bold_italic_x ) on test set split of UltraFeedback for Qwen 2-7B trained on UltraFeedback, where DPO-Shift uses fixed strategy. The ranges of the y-axis of all subfigures are the same.
> </details>



![](https://arxiv.org/html/2502.07599/x13.png)

> 🔼 그림 13은 UltraFeedback 데이터셋으로 학습된 Qwen 2-7B 모델에 대한 테스트셋 결과를 보여줍니다. DPO-Shift가 고정된 f(x) 전략을 사용했을 때, 보상 마진과 보상 정확도의 분포를 나타냅니다.  각 하위 그림은 서로 다른 f(x) 값에 따른 결과를 보여주며, y축 범위는 모든 하위 그림에서 동일하게 유지됩니다.  SFT(Supervised Fine-Tuning) 모델의 결과와 DPO(Direct Preference Optimization)의 결과도 비교를 위해 함께 제시되어 있습니다. 이를 통해 DPO-Shift의 f(x) 값 변화에 따른 성능 변화를 시각적으로 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: Distribution for reward margin and reward accuracy on test set split of UltraFeedback for Qwen 2-7B trained on UltraFeedback, where DPO-Shift uses fixed strategy. The ranges of the y-axis of all subfigures are the same.
> </details>



![](https://arxiv.org/html/2502.07599/x14.png)

> 🔼 그림 14는 Capybara 데이터셋으로 학습된 Qwen 2-7B 모델에 대해, DPO-Shift(고정 전략 사용)의 log πθ(yw|x)와 log πθ(yl|x)의 분포를 보여줍니다.  여기서 yw는 선택된 응답, yl은 기각된 응답을 나타냅니다.  각 하위 그림은 f(x)의 다양한 값에 따른 분포를 보여주며, y축의 범위는 모든 하위 그림에서 동일합니다.  이 그림은 DPO-Shift의 고정 전략이 선택 확률 분포에 미치는 영향을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: Distribution for log⁡πθ⁢(𝒚w|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑤𝒙\log\pi_{\theta}(\boldsymbol{y}_{w}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_w end_POSTSUBSCRIPT | bold_italic_x ) and log⁡πθ⁢(𝒚l|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑙𝒙\log\pi_{\theta}(\boldsymbol{y}_{l}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_l end_POSTSUBSCRIPT | bold_italic_x ) on test set split of Capybara for Qwen 2-7B trained on Capybara, where DPO-Shift uses fixed strategy. The ranges of the y-axis of all subfigures are the same.
> </details>



![](https://arxiv.org/html/2502.07599/x15.png)

> 🔼 그림 15는 Capybara 데이터셋으로 학습된 Qwen 2-7B 모델에 대해, DPO-Shift가 고정된 f(x) 전략을 사용했을 때 Capybara의 테스트셋 분할에 대한 보상 마진과 보상 정확도의 분포를 보여줍니다. 각 하위 그림의 y축 범위는 동일하며, SFT 모델, DPO 모델 및 다양한 f(x) 값을 가진 DPO-Shift 모델의 결과를 비교하여 보상 마진의 분포 변화와 보상 정확도의 변화를 시각적으로 보여줍니다. 이를 통해 DPO-Shift의 f(x) 매개변수가 모델 성능에 미치는 영향을 분석하고, 최적의 f(x) 값을 찾는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 15: Distribution for reward margin and reward accuracy on test set split of Capybara for Qwen 2-7B trained on Capybara, where DPO-Shift uses fixed strategy. The ranges of the y-axis of all subfigures are the same.
> </details>



![](https://arxiv.org/html/2502.07599/x16.png)

> 🔼 그림 16은 UltraFeedback 데이터셋으로 학습된 Llama 3-8B 모델에 대한 테스트셋 결과를 보여줍니다.  DPO-Shift의 linear_increase 및 linear_decrease 전략을 사용하여 log πθ(yw|x) 와 log πθ(yl|x) 의 분포를 나타냅니다.  여기서 yw는 선택된 응답, yl은 거절된 응답을 나타냅니다.  모든 하위 그림의 y축 범위는 동일합니다. 이 그림은 DPO-Shift 알고리즘이 선택 확률의 분포를 제어하는 데 사용하는 두 가지 전략의 효과를 시각적으로 비교 분석하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 16: Distribution for log⁡πθ⁢(𝒚w|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑤𝒙\log\pi_{\theta}(\boldsymbol{y}_{w}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_w end_POSTSUBSCRIPT | bold_italic_x ) and log⁡πθ⁢(𝒚l|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑙𝒙\log\pi_{\theta}(\boldsymbol{y}_{l}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_l end_POSTSUBSCRIPT | bold_italic_x ) on test set split of Ultrafeedback for Llama 3-8B trained on UltraFeedback, where DPO-Shift uses linear_increase and linear_decrease strategies. The ranges of the y-axis of all subfigures are the same.
> </details>



![](https://arxiv.org/html/2502.07599/x17.png)

> 🔼 그림 17은 UltraFeedback 데이터셋으로 학습된 Llama 3-8B 모델에 대해, DPO-Shift가 linear_increase 및 linear_decrease 전략을 사용할 때 테스트셋에서 얻은 reward margin과 reward accuracy의 분포를 보여줍니다.  각 하위 그림은 서로 다른 DPO-Shift 설정(linear_increase 또는 linear_decrease 전략과 Amin값) 또는 기준 DPO 방법을 나타냅니다.  y축의 범위는 모든 하위 그림에서 동일하게 설정되어 있어, 각 설정 간의 상대적인 차이를 비교하기 용이합니다.  이 그림은 DPO-Shift의 다양한 설정이 reward margin과 accuracy에 미치는 영향을 시각적으로 보여주는 역할을 합니다. 특히, reward margin과 accuracy 사이의 절충 관계를 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 17: Distribution for reward margin and reward accuracy on test set split of Ultrafeedback for Llama 3-8B trained on UltraFeedback, where DPO-Shift uses linear_increase and linear_decrease strategies. The ranges of the y-axis of all subfigures are the same.
> </details>



![](https://arxiv.org/html/2502.07599/x18.png)

> 🔼 그림 18은 Capybara 데이터셋으로 학습된 Llama 3-8B 모델에 대해,  Capybara 테스트셋을 사용하여 log πθ(yw|x) 와 log πθ(yl|x) 의 분포를 보여줍니다. 여기서 yw는 선택된 응답이고, yl은 기각된 응답입니다.  DPO-Shift 방법을 사용했으며, f(x) 함수는 linear_increase 및 linear_decrease 전략을 사용했습니다. 모든 서브 그림의 y축 범위는 동일합니다.  즉, 이 그림은 DPO-Shift의 두 가지 다른 f(x) 함수 적용 방식(선형 증가, 선형 감소)에 따른 선택된 응답과 기각된 응답의 확률 분포를 비교 분석한 것입니다.
> <details>
> <summary>read the caption</summary>
> Figure 18: Distribution for log⁡πθ⁢(𝒚w|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑤𝒙\log\pi_{\theta}(\boldsymbol{y}_{w}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_w end_POSTSUBSCRIPT | bold_italic_x ) and log⁡πθ⁢(𝒚l|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑙𝒙\log\pi_{\theta}(\boldsymbol{y}_{l}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_l end_POSTSUBSCRIPT | bold_italic_x ) on test set split of Capybara for Llama 3-8B trained on Capybara, where DPO-Shift uses linear_increase and linear_decrease strategies. The ranges of the y-axis of all subfigures are the same.
> </details>



![](https://arxiv.org/html/2502.07599/x19.png)

> 🔼 그림 19는 캡션에서 언급한 것처럼 카피바라 데이터셋으로 학습된 Llama 3-8B 모델에 대한 결과를 보여줍니다.  DPO-Shift 방법을 사용하여 선형 증가 및 선형 감소 전략을 적용했을 때의 보상 마진과 보상 정확도 분포를 나타냅니다.  각 하위 그림의 y축 범위는 동일하게 설정되어 있어, 서로 다른 전략 간의 직접적인 비교를 용이하게 합니다.  선형 증가와 선형 감소 전략 모두에 대한 보상 마진과 정확도의 분포를 시각적으로 비교 분석하여,  각 전략의 효과와 성능 차이를 파악하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 19: Distribution for reward margin and reward accuracy on test set split of Capybara for Llama 3-8B trained on Capybara, where DPO-Shift uses linear_increase and linear_decrease strategies. The ranges of the y-axis of all subfigures are the same.
> </details>



![](https://arxiv.org/html/2502.07599/x20.png)

> 🔼 그림 20은 UltraFeedback 데이터셋으로 학습된 Qwen 2-7B 모델에 대한 테스트셋 결과를 보여줍니다.  DPO-Shift 알고리즘의 linear_increase 및 linear_decrease 전략을 사용하여 log πθ(yw|x)와 log πθ(yl|x)의 분포를 보여줍니다.  여기서 yw는 선택된 응답이고, yl은 거부된 응답입니다.  모든 서브 그림의 y축 범위는 동일하게 설정되었습니다. 이 그림은 DPO-Shift 알고리즘의 두 가지 변형 전략이 선택 확률 분포에 미치는 영향을 시각적으로 비교 분석하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 20: Distribution for log⁡πθ⁢(𝒚w|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑤𝒙\log\pi_{\theta}(\boldsymbol{y}_{w}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_w end_POSTSUBSCRIPT | bold_italic_x ) and log⁡πθ⁢(𝒚l|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑙𝒙\log\pi_{\theta}(\boldsymbol{y}_{l}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_l end_POSTSUBSCRIPT | bold_italic_x ) on test set split of UltraFeedback for Qwen 2-7B trained on UltraFeedback, where DPO-Shift uses linear_increase and linear_decrease strategies. The ranges of the y-axis of all subfigures are the same.
> </details>



![](https://arxiv.org/html/2502.07599/x21.png)

> 🔼 그림 21은 UltraFeedback 데이터셋으로 학습된 Qwen 2-7B 모델에 대한 테스트셋 결과를 보여줍니다.  DPO-Shift의 linear_increase 및 linear_decrease 전략을 사용하여 reward margin과 reward accuracy의 분포를 나타냅니다.  각 하위 그림의 y축 범위는 동일합니다.  이 그림은 DPO-Shift의 두 가지 변형 방법이 reward margin과 reward accuracy에 미치는 영향을 비교 분석하는 데 사용됩니다.  각 전략의 성능을 reward margin과 accuracy의 분포를 통해 시각적으로 비교하여 DPO-Shift의 매개변수 조정 전략의 효과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 21: Distribution for reward margin and reward accuracy on test set split of UltraFeedback for Qwen 2-7B trained on UltraFeedback, where DPO-Shift uses linear_increase and linear_decrease strategies. The ranges of the y-axis of all subfigures are the same.
> </details>



![](https://arxiv.org/html/2502.07599/x22.png)

> 🔼 그림 22는 Capybara 데이터셋으로 학습된 Qwen 2-7B 모델에 대한 테스트셋 결과를 보여줍니다. DPO-Shift 방법을 사용하여 선형 증가 및 선형 감소 전략을 적용했을 때, 선택된 응답(yw)과 기각된 응답(yl)의 로그 확률 분포를 보여줍니다.  y축 범위는 모든 하위 그림에서 동일합니다. 이 그림은 DPO-Shift의 매개변수 함수 f(x)를 선형적으로 증가시키거나 감소시키는 전략의 효과를 시각적으로 비교 분석하는 데 사용됩니다.  즉, f(x)를 어떻게 조정하는지에 따라 선택된 응답의 확률 분포가 어떻게 변하는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 22: Distribution for log⁡πθ⁢(𝒚w|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑤𝒙\log\pi_{\theta}(\boldsymbol{y}_{w}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_w end_POSTSUBSCRIPT | bold_italic_x ) and log⁡πθ⁢(𝒚l|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑙𝒙\log\pi_{\theta}(\boldsymbol{y}_{l}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_l end_POSTSUBSCRIPT | bold_italic_x ) on test set split of Capybara for Qwen 2-7B trained on Capybara, where DPO-Shift uses linear_increase and linear_decrease strategies. The ranges of the y-axis of all subfigures are the same.
> </details>



![](https://arxiv.org/html/2502.07599/x23.png)

> 🔼 그림 23은 Capybara 데이터셋으로 학습된 Qwen 2-7B 모델에 대한 Capybara 테스트셋 분할 결과를 보여줍니다.  DPO-Shift의 linear_increase 및 linear_decrease 전략을 사용하여 reward margin과 reward 정확도의 분포를 나타냅니다.  각 하위 그림의 y축 범위는 동일하며, reward margin의 분포와 reward 정확도를 비교 분석하여 DPO-Shift의 성능을 평가하는 데 사용됩니다.  각 전략에서 reward margin의 분포와 reward 정확도를 비교하여 DPO-Shift의 성능과 안정성을 평가할 수 있습니다. 
> <details>
> <summary>read the caption</summary>
> Figure 23: Distribution for reward margin and reward accuracy on test set split of Capybara for Qwen 2-7B trained on Capybara, where DPO-Shift uses linear_increase and linear_decrease strategies. The ranges of the y-axis of all subfigures are the same.
> </details>



![](https://arxiv.org/html/2502.07599/x24.png)

> 🔼 그림 24는 UltraFeedback 데이터셋으로 학습된 Llama 3-8B 모델에 대한 테스트셋 분할에서 log πθ(yw|x)와 log πθ(yl|x)의 분포를 보여줍니다. 여기서 DPO-Shift는 고정된 전략을 사용합니다. y축 범위는 모든 하위 그림에서 동일합니다. 이 그림은 DPO-Shift의 고정 전략을 사용하여 모델이 선택된 응답과 기각된 응답의 확률을 어떻게 조정하는지 보여줍니다.  선택된 응답에 대한 확률은 증가하고, 기각된 응답에 대한 확률은 감소하는 경향이 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 24: Distribution for log⁡πθ⁢(𝒚w|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑤𝒙\log\pi_{\theta}(\boldsymbol{y}_{w}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_w end_POSTSUBSCRIPT | bold_italic_x ) and log⁡πθ⁢(𝒚l|𝒙)subscript𝜋𝜃conditionalsubscript𝒚𝑙𝒙\log\pi_{\theta}(\boldsymbol{y}_{l}|\boldsymbol{x})roman_log italic_π start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT ( bold_italic_y start_POSTSUBSCRIPT italic_l end_POSTSUBSCRIPT | bold_italic_x ) on test set split of UltraFeedback for Llama 3-8B trained on UltraFeedback, where DPO-Shift uses fixed strategy. The ranges of the y-axis of all subfigures are the same.
> </details>



![](https://arxiv.org/html/2502.07599/x25.png)

> 🔼 그림 25는 UltraFeedback 데이터셋으로 학습된 Llama 3-8B 모델에 대한 테스트셋 결과를 보여줍니다. DPO-Shift의 고정된 전략(fixed strategy)을 사용하여, 보상 마진(reward margin)과 보상 정확도(reward accuracy)의 분포를 보여줍니다.  각 하위 그림의 y축 범위는 동일하게 설정되었습니다.  이 그림은 DPO-Shift의 f(x) 값을 다르게 설정했을 때 보상 마진과 정확도에 미치는 영향을 시각적으로 보여주는 역할을 합니다.  다양한 f(x) 값에 따른 보상 마진과 정확도 분포의 변화를 통해 DPO-Shift 알고리즘의 성능을 분석하고 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 25: Distribution for reward margin and reward accuracy on test set split of UltraFeedback for Llama 3-8B trained on UltraFeedback, where DPO-Shift uses fixed strategy. The ranges of the y-axis of all subfigures are the same.
> </details>



![](https://arxiv.org/html/2502.07599/x26.png)

> 🔼 그림 26은 UltraFeedback 데이터셋으로 학습된 Llama 3-8B 모델을 사용하여 Capybara 테스트셋의 질문들에 대한 Win Rate 실험 결과를 보여줍니다.  UltraFeedback으로 미세 조정된 Llama 3-8B 모델과 다양한 f(x) 전략(fixed, linear_increase, linear_decrease 등)을 사용한 DPO-Shift 모델의 성능을 비교 분석합니다.  각 전략별로 모델이 올바른 응답을 선택한 비율(Win), 무승부 비율(Tie), 잘못된 응답을 선택한 비율(Loss)을 시각적으로 나타내어 DPO-Shift의 효과와 f(x) 선택 전략에 따른 성능 변화를 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 26: Win rate experiment for Llama 3-8B trained on UltraFeedback and tested with questions from the test split of Capybara.
> </details>



![](https://arxiv.org/html/2502.07599/x27.png)

> 🔼 이 그림은 UltraFeedback 데이터셋으로 학습된 Qwen 2-7B 모델을 사용하여 UltraFeedback의 테스트 집합에서 나온 질문들로 Win Rate 실험을 진행한 결과를 보여줍니다.  DPO와 DPO-Shift의 다양한 전략(f(x) 함수의 선택)을 비교하여 각 모델의 성능을 평가합니다.  세로축은 승률(Win), 무승부(Tie), 패배(Loss) 비율을 나타내고, 가로축은 사용된 DPO-Shift 전략(fixed, linear_increase, linear_decrease 등)을 나타냅니다. 각 전략에 따른 승률, 무승부, 패배 비율을 시각적으로 비교하여 어떤 DPO-Shift 전략이 DPO보다 더 나은 성능을 보이는지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 27: Win rate experiment for Qwen 2-7B trained on UltraFeedback and tested with questions from the test split of UltraFeedback.
> </details>



![](https://arxiv.org/html/2502.07599/x28.png)

> 🔼 이 그림은 UltraFeedback 데이터셋으로 학습된 Qwen 2-7B 모델을 사용하여 Capybara 테스트셋의 질문들에 대한 승률 실험 결과를 보여줍니다.  각 막대는 DPO와 DPO-Shift의 세 가지 전략(fixed, linear_increase, linear_decrease)에 따른 승률, 무승부, 패배 비율을 나타냅니다.  이를 통해 DPO-Shift의 다양한 f(x) 전략이 모델 성능에 미치는 영향을 비교 분석하고,  DPO-Shift가 DPO보다 더 나은 성능을 보이는지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 28: Win rate experiment for Qwen 2-7B trained on UltraFeedback and tested with questions from the test split of Capybara.
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