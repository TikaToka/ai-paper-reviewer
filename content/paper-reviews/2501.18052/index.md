---
title: "SAeUron: Interpretable Concept Unlearning in Diffusion Models with Sparse Autoencoders"
summary: "SAeUron: 희소 오토인코더를 이용한 해석 가능한 텍스트-이미지 확산 모델의 개념 제거"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Generation", "🏢 Warsaw University of Technology",]
showSummary: true
date: 2025-01-29
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.18052 {{< /keyword >}}
{{< keyword icon="writer" >}} Bartosz Cywiński et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-03 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.18052" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.18052" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/saeuron-interpretable-concept-unlearning-in" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존 텍스트-이미지 확산 모델들은 원치 않는 콘텐츠를 생성하는 문제점을 가지고 있습니다. 이 문제를 해결하기 위해 최근 머신 언러닝 기법이 제시되었지만,  투명성이 부족하고 적대적 공격에 취약한 단점이 존재합니다. 

본 논문에서는 희소 오토인코더(SAE)를 활용하여 이러한 문제점을 해결하는 새로운 방법인 SAeUron을 제안합니다.  SAeUron은 확산 모델의 활성화 값에서 특징을 추출하고, 원치 않는 개념과 관련된 특징을 제거함으로써 원치 않는 콘텐츠 생성을 방지합니다.  **UnlearnCanvas 벤치마크를 사용한 실험 결과, SAeUron은 기존 방법보다 우수한 성능을 보였으며 적대적 공격에도 강인한 모습을 보였습니다.**

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 희소 오토인코더(SAE)를 이용하여 확산 모델에서 원치 않는 개념을 효과적으로 제거하는 새로운 방법인 SAeUron을 제시했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} SAeUron은 기존 방법보다 성능이 우수하며, **개념별 특징을 식별하여 제거 과정을 투명하게 보여주는 해석 가능성**을 제공합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} SAeUron은 **적대적 공격에 강하며 여러 개념을 동시에 제거**할 수 있어 실제 적용 가능성이 높습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**본 논문은 확산 모델에서 원치 않는 개념을 제거하는 새로운 방법인 SAeUron을 제시하여 기존 방법보다 성능이 뛰어나고 투명성이 높다는 점에서 중요합니다.**  **연구는 기존 머신 언러닝 기법의 한계를 극복하고,  설명 가능한 AI 시스템 개발에 대한 요구를 충족합니다.** 또한, **추후 연구를 위한 새로운 방향을 제시**하여 확산 모델의 해석 가능성 및 안전성 향상에 크게 기여할 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.18052/x9.png)

> 🔼 SAeUron은 희망하지 않는 개념(이 그림에서는 만화 스타일)에 해당하는 SAE 특징을 찾아 제거하여 확산 모델의 전반적인 성능을 유지하면서 원치 않는 콘텐츠 생성을 방지하는 방법을 보여줍니다.  SAE 인코더는 입력 이미지에서 특징을 추출하고, '만화 스타일 특징은 통과할 수 없다'라는 문구처럼 특정 특징을 차단합니다.  그런 다음 SAE 디코더는 수정된 특징을 사용하여 이미지를 생성합니다.  이 과정을 통해 원치 않는 스타일이 제거된 이미지가 생성됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Concept unlearning in SAeUron. We localize and remove SAE features corresponding to the unwanted concept (Cartoon) while preserving the overall performance of the diffusion model.
> </details>





{{< table-caption >}}
Method|Style Unlearning| | | |Object Unlearning| | | | |FID (↓)|Memory (GB) (↓)|Storage (GB) (↓)
---|---|---|---|---|---|---|---|---|---|---|---|---
|---|---|---|---|---|---|---|---|---|---|---|---|---
ESD (Gandikota et al., 2023)|98.58%|80.97%|93.96%|91.17%|92.15%|55.78%|44.23%|64.05%|65.55|17.8|4.3
FMN (Zhang et al., 2024a)|88.48%|56.77%|46.60%|63.95%|45.64%|90.63%|73.46%|69.91%|131.37|17.9|4.2
UCE (Gandikota et al., 2024)|98.40%|60.22%|47.71%|68.78%|94.31%|39.35%|34.67%|56.11%|182.01|5.1|1.7
CA (Kumari et al., 2023)|60.82%|96.01%|92.70%|83.18%|46.67%|90.11%|81.97%|72.92%|54.21|10.1|4.2
SalUn (Fan et al., 2023)|86.26%|90.39%|95.08%|90.57%|86.91%|96.35%|99.59%|94.28%|61.05|30.8|4.0
SEOT (Li et al., 2024)|56.90%|94.68%|84.31%|78.63%|23.25%|95.57%|82.71%|67.18%|62.38|7.34|0.0
SPM (Lyu et al., 2024)|60.94%|92.39%|84.33%|79.22%|71.25%|90.79%|81.65%|81.23%|59.79|6.9|0.0
EDiff (Wu et al., 2024)|92.42%|73.91%|98.93%|88.42%|86.67%|94.03%|48.48%|76.39%|81.42|27.8|4.0
SHS (Wu & Harandi, 2024)|95.84%|80.42%|43.27%|73.18%|80.73%|81.15%|67.99%|76.62%|119.34|31.2|4.0
SAeUron|96.76%|98.70%|98.10%|97.85%|84.23%|90.05%|76.78%|83.69%|61.43|2.8|0.2{{< /table-caption >}}

> 🔼 본 표는 SAeUron과 최첨단 기법들을 스타일 및 개체 언러닝 작업에서 비교 평가한 결과를 보여줍니다. 각 지표에 대해 최고 성능은 굵게 표시하고, 두 번째로 높은 성능은 밑줄로 표시했습니다. SAeUron은 스타일 언러닝에서 다른 방법들을 상당히 능가하며, 개체 언러닝에서는 비슷한 수준의 성능을 보여줍니다. 중요한 점은 SAeUron이 모든 지표에서 일관된 성능을 보여준다는 것입니다.  FID는 Fréchet Inception Distance, UA는 Unlearning Accuracy, IRA는 In-domain Retain Accuracy, CRA는 Cross-domain Retain Accuracy를 나타냅니다.  평균값은 UA, IRA, CRA의 평균을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Evaluation of SAeUron against state-of-the-art methods on style and object unlearning. The best result for each metric is highlighted in bold, and the second-best is underlined. Our approach significantly outperforms others on style unlearning and performs comparably on object unlearning. Importantly, SAeUron demonstrates consistent performance across all metrics.
> </details>





### In-depth insights


#### Sparse Autoencoders
본 논문에서 스파스 오토인코더(SAE)는 텍스트-이미지 확산 모델의 내부 활성화를 학습하는 데 사용됩니다. **비지도 학습 방식**으로, 확산 모델의 여러 탈잡음 단계의 활성화를 통해 **희소적이고 해석 가능한 특징**을 학습합니다.  SAE는 특정 개념에 해당하는 특징을 식별하고 추론 중에 해당 특징을 제거하여 원치 않는 개념을 제거합니다. 이는 모델 성능을 유지하면서 특정 콘텐츠를 차단하는 정밀한 개입을 가능하게 합니다. **해석 가능성**은 SAE의 주요 장점 중 하나이며, 다른 방법과 달리 원치 않는 콘텐츠 생성 가능성을 줄이는 데 도움이 됩니다.  **다중 개념 동시 제거** 및 **적대적 공격에 대한 강인성**도 SAE의 중요한 특징입니다.  본 연구는 SAE가 확산 모델의 내부 메커니즘을 이해하는 데 유용한 도구임을 보여줍니다.

#### Unlearning Methods
본 논문은 **기존 머신 언러닝(unlearning) 방법론의 한계점을 극복**하기 위해 새로운 방법론을 제시합니다. 기존 방법론들은 대부분 미세조정(fine-tuning) 기반으로 투명성이 부족하고, 원하지 않는 결과물 생성 가능성이 높다는 단점이 있습니다. 이에 반해 본 논문에서는 **희소 오토인코더(sparse autoencoder)**를 활용하여 **해석 가능성과 성능을 동시에 확보**하는 새로운 접근 방식을 제시합니다. 희소 오토인코더는 확산 모델의 활성화(activation) 패턴에서 개념(concept)에 해당하는 특징을 효과적으로 추출하고, 이를 차단함으로써 원치 않는 콘텐츠 생성을 방지합니다. 특히, **다중 개념 동시 제거** 및 **적대적 공격(adversarial attack)에 대한 강인성**을 보이는 등 기존 방법론보다 우수한 성능을 보여줍니다.  본 연구의 핵심은 **해석 가능성을 높인 접근법**과 **강건한 성능**입니다. 이는 윤리적 및 안전 문제를 야기할 수 있는 생성 모델의 위험을 완화하는 데 크게 기여할 것으로 예상됩니다.

#### Interpretability
본 논문에서 제시된 SAeUron 모델의 핵심 강점 중 하나는 **해석 가능성(Interpretability)**입니다. 기존의 머신 언러닝 기법들은 모델의 내부 동작 과정을 이해하기 어려워 투명성이 부족한 반면, SAeUron은 **희소 자동 인코더(Sparse Autoencoder)**를 활용하여 **개념에 특정된 특징들을 식별하고 제거하는 과정을 명확하게 보여줍니다.**  이는 모델의 변경 사항을 직관적으로 파악할 수 있도록 하여, **윤리적 및 안전적인 문제 발생 가능성을 줄이고 신뢰성을 높입니다.** 특히, SAeUron이 학습 과정에서 추출한 특징들은 **해석 가능하며,  특정 개념과의 연관성을 시각적으로 확인할 수 있습니다.** 이러한 해석 가능성은 모델의 투명성을 높일 뿐만 아니라, **잘못된 결과 발생 원인을 분석하고 개선하는 데에도 도움을 줍니다.**  결론적으로, SAeUron의 해석 가능성은 단순한 성능 향상을 넘어,  **신뢰할 수 있는 인공지능 시스템 구축에 중요한 기여**를 할 수 있음을 시사합니다.

#### Adversarial Robustness
본 논문은 제한된 길이로 인해 ‘적대적 견고성(Adversarial Robustness)’에 대한 심층적인 논의를 충분히 다루지 못하지만, 핵심 내용을 요약하면 다음과 같습니다. **SAeUron 모델은 비지도 학습 방식으로 훈련되기 때문에 적대적 공격에 대한 견고성이 높다**는 것을 보여줍니다. 다른 기존의 방법들은 미세 조정 기반이기 때문에 적대적 공격에 취약하지만, SAeUron은 이러한 문제점을 완화합니다. 이는 **SAeUron이 특정 개념과 관련된 특징을 직접 제거하는 방식**으로 작동하기 때문입니다. **단순히 개념을 가리는 것이 아니라, 실제로 제거**하기 때문에 적대적 공격에 효과적으로 대응할 수 있습니다.  하지만, **모든 적대적 공격에 완벽하게 대응하는 것은 아니며**,  **향후 연구를 통해 더욱 강화**할 필요가 있습니다.  추가적으로,  **본 논문은 제한된 실험 결과**만 제시하고 있어,  다양한 적대적 공격에 대한  SAeUron의 견고성을 더욱 포괄적으로 검증할 필요가 있습니다.

#### Future Work
본 논문에서 제시된 SAeUron 모델은 뛰어난 성능을 보이지만, 향후 연구를 통해 개선될 여지가 있습니다. **추론 시간을 단축하고 메모리 사용량을 줄이는 방안**을 모색해야 합니다.  **더욱 다양하고 대규모의 데이터셋**을 활용하여 모델의 일반화 능력을 향상시키는 연구가 필요합니다. 또한, **적대적 공격에 대한 강인성을 더욱 높이는 연구**가 중요합니다.  **다양한 확산 모델 및 다른 모달리티** (예: 텍스트, 오디오)에 대한 SAeUron의 적용 가능성을 확장하는 연구도 필요합니다. 마지막으로, **설명 가능성을 더욱 높이기 위한 연구**가 필요합니다.  **개선된 특징 선택 방법이나 시각화 기법**을 개발하여 모델의 결정 과정에 대한 이해도를 높이는 것이 중요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.18052/x10.png)

> 🔼 그림 2는 SAeUron의 개념 제거 절차를 보여줍니다. (a)는 중요도 점수에 따라 제거할 개념별 특징을 선택하는 과정을, (b)는 확산 모델의 U-Net 추론 과정에서 선택된 크로스 어텐션 블록 간의 활성화를 훈련된 SAE를 통과시키는 과정을 보여줍니다.  선택된 SAE 특징들은 음수 승수 γc를 사용하여 제거되어 최종 출력에 미치는 영향을 제거합니다. 나머지 특징들은 변경되지 않아 전체 모델 성능에 대한 영향을 최소화합니다.  즉, 원치 않는 개념과 관련된 특징들을 제거하여 이미지 생성 결과에서 해당 개념이 나타나지 않도록 하면서, 전체적인 이미지 생성 품질은 유지하는 과정입니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Unlearning procedure in SAeUron. (a) Concept-specific features are selected for unlearning according to their importance scores. (b) During inference in the U-Net of the diffusion model, activation between selected cross-attention blocks is passed through a trained SAE. The selected SAE features are then ablated by scaling them with a negative multiplier γcsubscript𝛾𝑐\gamma_{c}italic_γ start_POSTSUBSCRIPT italic_c end_POSTSUBSCRIPT, removing their influence on the final output. The remaining features are left unchanged, ensuring minimal impact on the overall model performance.
> </details>



![](https://arxiv.org/html/2501.18052/x11.png)

> 🔼 이 그림은 SAE(Sparse Autoencoder)가 학습한 특징들의 중요도 점수를 보여줍니다. 대부분의 특징들은 중요도 점수가 거의 0에 가까운 반면, 소수의 특징들만 높은 점수를 가지고 있습니다. 이는 SAE가 개념 특징(concept-specific features)만을 학습한다는 것을 의미합니다. 평가 과정에서 점수의 백분위수를 기반으로 임계값을 설정하고, 이 임계값을 초과하는 특징들을 차단합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Feature importance scores. Most of the features have near-zero scores, indicating that SAE learns only a few concept-specific features. During the evaluation, we find a threshold based on percentile of scores and block features exceeding it.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Block | # Latents n | k | α | Fraction Var. Unexplained | Rate | Size | Learning Rate | Batch Size | Dead Feature Threshold | Epochs | Normalize | 
|---|---|---|---|---|---|---|---|---|---|---|---| 
| `up.1.1` | 20480 | 32 | 1/32 | 0.181 | 0.0004 | 4096 | 10M | 5 | √ | 
| `up.1.2` | 20480 | 32 | 1/32 | 0.198 | 0.0004 | 4096 | 10M | 10 | √ | {{< /table-caption >}}
> 🔼 표 2는 본 논문에서 사용된 희소 오토인코더(SAE) 학습에 대한 요약 정보를 제공합니다.  SAE는 텍스트-이미지 확산 모델의 활성화를 이용하여 학습되었으며, 표에는 각 SAE의 차원, 활성화 함수, 학습률, 배치 크기, 데드 특징 임계값, 에포크 수, 디코더 정규화 여부 등의 세부 정보가 포함되어 있습니다. 특히, 'up.1.1'과 'up.1.2' 블록에 대해 각각 학습된 두 개의 SAE에 대한 정보를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Summary of SAE trainings.
> </details>

{{< table-caption >}}
| Setup | UA (<img src="https://arxiv.org/html/2501.18052/uparrow.png" alt="\uparrow">) | IRA (<img src="https://arxiv.org/html/2501.18052/uparrow.png" alt="\uparrow">) | CRA (<img src="https://arxiv.org/html/2501.18052/uparrow.png" alt="\uparrow">) | Avg. (<img src="https://arxiv.org/html/2501.18052/uparrow.png" alt="\uparrow">) |
|---|---|---|---|---|
| All data | 75.00% | 90.18% | 80.74% | 81.97% |
| In-distribution | 99.76% | 99.23% | 98.48% | 99.16% |
| Out of distribution | 51.00% | 67.38% | 98.36% | 72.25% |{{< /table-caption >}}
> 🔼 이 표는 절반의 데이터로 학습된 SAE를 사용한 언러닝 성능을 보여줍니다.  '전체 데이터', '데이터 내', '데이터 외부' 세 가지 상황에서 언러닝 정확도(UA), 도메인 내 유지 정확도(IRA), 도메인 간 유지 정확도(CRA), 평균 정확도(Avg.)를 보여줍니다.  데이터 외부에서도 상당한 언러닝 정확도를 달성하여, SAE가 효과적으로 일반화하고 학습 데이터에 없는 개념도 제거할 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Unlearning performance with SAE trained on half of the data.
> </details>

{{< table-caption >}}
| Object | Percentile threshold  τc | Multiplier γc |
|---|---|---|
| Architectures | 99.999 | -30.0 |
| Bears | 99.999 | -5.0 |
| Birds | 99.999 | -5.0 |
| Butterfly | 99.99 | -5.0 |
| Cats | 99.999 | -30.0 |
| Dogs | 99.999 | -15.0 |
| Fishes | 99.995 | -30.0 |
| Flame | 99.995 | -1.0 |
| Flowers | 99.99 | -20.0 |
| Frogs | 99.999 | -30.0 |
| Horses | 99.99 | -20.0 |
| Human | 99.995 | -5.0 |
| Jellyfish | 99.999 | -1.0 |
| Rabbits | 99.99 | -10.0 |
| Sandwiches | 99.999 | -10.0 |
| Sea | 99.995 | -5.0 |
| Statues | 99.995 | -5.0 |
| Towers | 99.995 | -1.0 |
| Trees | 99.99 | -20.0 |
| Waterfalls | 99.99 | -1.0 |{{< /table-caption >}}
> 🔼 이 표는 본 논문의 객체 제거(unlearning) 방법에 사용된 초매개변수(hyperparameter)들을 보여줍니다.  각 객체에 대해, 점수 분포의 백분위수 임계값(percentile threshold)과 음수 승수(multiplier)의 값이 별도로 조정되었음을 나타냅니다.  이는 객체별로 최적의 성능을 얻기 위해 초매개변수를 미세 조정했음을 의미합니다. 각 객체에 대해 어떤 값들이 사용되었는지 상세하게 제시하고 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Hyperparameters of our method for object unlearning.
> </details>

{{< table-caption >}}
| Reference | Image | Without Steering | With Steering |
|---|---|---|---| 
| _Picasso_ | https://arxiv.org/html/2501.18052/figures/empty_prompt_steering_images/Picasso_ref.png | https://arxiv.org/html/2501.18052/figures/empty_prompt_steering_images/without_steering.png | https://arxiv.org/html/2501.18052/figures/empty_prompt_steering_images/Picasso.png |
| _Abstractionism_ | https://arxiv.org/html/2501.18052/figures/empty_prompt_steering_images/Abstractionism_ref.png | https://arxiv.org/html/2501.18052/figures/empty_prompt_steering_images/without_steering.png | https://arxiv.org/html/2501.18052/figures/empty_prompt_steering_images/Abstractionism.png |
| _Superstring_ | https://arxiv.org/html/2501.18052/figures/empty_prompt_steering_images/Superstring_ref.png | https://arxiv.org/html/2501.18052/figures/empty_prompt_steering_images/without_steering.png | https://arxiv.org/html/2501.18052/figures/empty_prompt_steering_images/Superstring.png |
| _Pastel_ | https://arxiv.org/html/2501.18052/figures/empty_prompt_steering_images/Pastel_ref.png | https://arxiv.org/html/2501.18052/figures/empty_prompt_steering_images/without_steering.png | https://arxiv.org/html/2501.18052/figures/empty_prompt_steering_images/Pastel.png |
| _Color Fantasy_ | https://arxiv.org/html/2501.18052/figures/empty_prompt_steering_images/Color_Fantasy_ref.png | https://arxiv.org/html/2501.18052/figures/empty_prompt_steering_images/without_steering.png | https://arxiv.org/html/2501.18052/figures/empty_prompt_steering_images/Color_Fantasy.png |{{< /table-caption >}}
> 🔼 표 5는 UnlearnDiffAtk 공격 전후의 이미지와 대상 개체 간의 CLIPScore를 보여줍니다.  CLIPScore는 이미지와 텍스트 간의 유사도를 측정하는 지표입니다.  표에서 볼 수 있듯이, 공격이 성공적이었음에도 불구하고, 대상 개체와의 유사도는 거의 변하지 않았습니다.  이는 SAeUron 기법이 대상 개체를 생성하지 않고, 다른 개체로 대체하는 방식으로 작동함을 보여줍니다.  즉, 분류기의 예측 결과는 무작위에 가까워지지만, 실제로는 대상 개체가 생성되지 않으므로 공격이 성공했다고 평가되는 현상을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 5: CLIPScore between images and targeted objects before and after the attack. Although the attack is successful, the similarity to the target object barely changes.
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