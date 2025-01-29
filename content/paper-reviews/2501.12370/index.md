---
title: "Parameters vs FLOPs: Scaling Laws for Optimal Sparsity for Mixture-of-Experts Language Models"
summary: "희소 혼합 전문가(MoE) 언어 모델의 최적 스파스성을 위한 스케일링 법칙을 규명"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Apple",]
showSummary: true
date: 2025-01-21
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.12370 {{< /keyword >}}
{{< keyword icon="writer" >}} Samira Abnar et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-28 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.12370" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.12370" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/parameters-vs-flops-scaling-laws-for-optimal" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델의 성능 향상을 위해서는 매개변수 수와 연산량(FLOPs)을 모두 늘리는 것이 일반적이지만, 이들의 상호 작용에 대한 명확한 이해는 부족했습니다. 특히, 희소 혼합 전문가(MoE) 모델은 매개변수 수를 늘리더라도 FLOPs는 비례적으로 증가하지 않아 효율적인 스케일링이 가능하지만, 최적의 스파스성 수준을 찾는 것은 여전히 어려운 문제였습니다.

본 연구는 MoE 모델에서 매개변수 수와 FLOPs의 상호 작용을 분석하여 최적의 스파스성 수준을 규명하고, 이를 스케일링 법칙에 통합한 새로운 모델을 제시합니다. 실험 결과, **특정 제약 조건 하에서 최적의 스파스성 수준이 존재**하며, 이를 통해 **훈련 효율성과 모델 성능을 동시에 향상**시킬 수 있음을 보였습니다. 이는 **더욱 효율적이고 성능 좋은 언어 모델 설계**에 대한 새로운 지침을 제공합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 매개변수 수와 FLOPs 간의 상호 작용을 고려한 최적 스파스성 도출 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 훈련 컴퓨팅 예산 내에서 스파스성 수준 조절을 통한 모델 성능 향상 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 스파스성을 스케일링 법칙에 통합하여 밀집 모델보다 효율적인 MoE 모델 설계 가능성 제시 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **희소 혼합 전문가(MoE) 언어 모델의 최적 스파스성을 위한 스케일링 법칙**을 제시하여, 매개변수 수와 연산량(FLOPs) 간의 상호 작용을 깊이 있게 이해하는 데 중요한 의미를 지닙니다. 이는 **효율적인 언어 모델 설계 및 구축**에 대한 새로운 방향을 제시하며, 관련 분야 연구자들에게 실질적인 영향을 미칠 수 있습니다. 특히, **제한된 컴퓨팅 자원 내에서 모델 성능을 극대화**하는 방법을 제시하여,  컴퓨팅 자원이 제한적인 연구 환경에서 큰 도움을 줄 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.12370/x1.png)

> 🔼 그림 1(a)는 Mixture-of-Experts (MoE) 언어 모델의 사전 훈련 손실, 총 매개변수 수, 그리고 스파스성 간의 관계를 보여주는 3차원 표면 그래프입니다.  IsoFLOP 표면이라고 불리는 이 그래프는 고정된 총 계산량(FLOPs) 하에서 스파스성이 변함에 따라 모델 크기가 손실에 미치는 영향을 시각적으로 보여줍니다.  총 매개변수 수는 모델의 용량을 나타내며, 스파스성은 비활성 매개변수의 비율을 나타냅니다.  이 그림은 특정 계산량 제약 조건 하에서 최적의 스파스성 수준을 찾는 데 도움이 되는 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> (a) IsoFLOP surface over sparsity and total parameters
> </details>





{{< table-caption >}}
| Symbol | Description |
|---|---| 
| N | Total number of model parameters |
| N<sub>a</sub> | Active number of model parameters |
| S | Sparsity level (ratio of non-active to total experts) |
| S* | Optimal sparsity level |
| L | Pretraining Loss (Categorical Cross-Entropy) |
| L* | Optimal pretraining loss |
| C | Total training compute budget (in FLOPs) |
| N* | Optimal total number of parameters |
| N*<sub>a</sub> | Optimal active number of parameters |
| E | Expansion factor (number of experts per MoE layer) |
| K | Number of selected experts per token |
| G | Granularity of experts (size relative to base MLP) |
| D | Dataset size (number of training tokens) |
| α,β,γ,λ,δ,a,b,c,d,e | Coefficients in the parametric scaling law equation |{{< /table-caption >}}

> 🔼 표 1은 논문의 실험 설정에서 사용된 하이퍼파라미터들의 설정값과 탐색 범위를 보여줍니다.  각 하이퍼파라미터별로 설정값이 고정되었는지(Constant), 아니면 실험적으로 조정되었는지(Tuned), 또는 탐색 범위가 지정되었는지(Search Space)를 나타냅니다.  특히, MoE(Mixture-of-Experts) 모델의 스파스성(Sparsity Level)과 관련된 하이퍼파라미터(전체 전문가 수, 활성 전문가 수, 그리고 그래뉼러리티)는 모델 성능에 큰 영향을 미치므로, 실험적으로 조정되었습니다. 학습률(Learning Rate) 및 웜업 스텝(Warm-up Steps)과 같은 다른 하이퍼파라미터들도 모델 성능에 따라 조정되었습니다.  이 표는 전체 실험의 재현성을 높이고, 사용된 하이퍼파라미터 설정의 세부 사항을 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Hyperparameter configurations and search spaces
> </details>





### In-depth insights


#### MoE Sparsity Laws
MoE (Mixture of Experts) 모델의 스파스성을 다루는 법칙은 **매개변수 수와 FLOP(연산 수) 간의 균형**을 이해하는 데 중요합니다.  이 논문은 **스파스성 수준을 변화시키면서 모델 크기와 성능 사이의 상호 작용**을 탐구합니다.  **최적의 스파스성은 고정된 컴퓨팅 예산 하에서 모델 크기에 따라 달라지며**,  **훈련 효율성과 성능 모두를 향상**시키는 수준이 존재합니다. **훈련 단계에서는 매개변수 수 증가가 FLOP 증가보다 더 유익**하지만, **추론 단계에서는 FLOP가 더 중요**한 역할을 합니다. 따라서,  **최적 스파스성을 찾는 것은 훈련과 추론의 효율성을 모두 고려**해야 함을 시사합니다. 이러한 법칙들은 MoE 모델 아키텍처의 설계와 최적화에 중요한 통찰력을 제공합니다.

#### Optimal Sparsity
본 논문에서 '최적 스파스성'에 대한 논의는 훈련 컴퓨팅 예산이 제한적인 상황에서 **매개변수 수와 예제당 FLOP 간의 최적 절충점**을 찾는 것을 의미합니다.  **스파스 믹스쳐-오브-익스퍼츠(MoE) 모델**의 맥락에서 스파스성 수준을 조절하여 매개변수 수를 늘리지 않고도 예제당 연산량을 줄일 수 있습니다.  연구 결과는 **훈련 효율성과 모델 성능을 동시에 향상시키는 최적 스파스성 수준**이 존재함을 보여줍니다.  **훈련 컴퓨팅 예산과 모델 크기 변화**에 따라 최적 스파스성이 달라지며, 무한 데이터 환경에서는 스파스성이 증가할수록 성능이 향상됩니다.  하지만, 제한된 컴퓨팅 환경에서는 **예제당 FLOP의 중요성**이 커지며, 특정 다운스트림 작업에서는 스파스 모델의 성능이 저하될 수 있다는 점도 주목할 만합니다.  결론적으로, 최적 스파스성은 모델 크기, 훈련 컴퓨팅 예산, 그리고 다운스트림 작업의 특성에 따라 다르게 나타나므로, **모델 설계시 종합적인 고려**가 필요합니다.

#### Downstream Tasks
본 논문에서 다루는 다운스트림 태스크는 사전 훈련된 언어 모델의 성능을 평가하기 위한 것입니다. **특히, 컨텍스트 몇 샷 학습 설정에서 모델이 새로운 작업에 얼마나 잘 적응하는지 평가하는 데 중점을 두고 있습니다.** 이는 모델의 일반화 능력과 몇 가지 제한된 예시만으로 새로운 작업을 수행할 수 있는 능력을 평가하는 중요한 지표가 됩니다. 다운스트림 태스크는 언어 이해, 상식 추론, 읽기 이해, 기호 추론과 같은 여러 범주로 나뉘어져 있습니다. 각 범주 내에서 다양한 특정 작업들을 통해 모델의 능력을 다각적으로 평가합니다.  **흥미로운 점은 업스트림(사전 훈련) 손실과 다운스트림 성능 간에 강한 상관관계가 있다는 것입니다.**  이는 사전 훈련 단계에서의 성능 개선이 다운스트림 작업에서의 성능 향상으로 직접적으로 이어짐을 시사합니다. 하지만, **모든 작업에서 이러한 상관관계가 동일하게 나타나는 것은 아닙니다.**  특히, 읽기 이해와 같은 특정 작업에서는 더 높은 추론 능력이 요구될 수 있으며, 이는 희소 모델의 성능 저하로 이어질 수 있습니다.

#### Scaling Laws
본 논문에서 제시된 스케일링 법칙은 언어 모델의 성능을 예측하고 향상시키는 데 중요한 역할을 합니다. **매개변수의 수와 샘플당 계산량(FLOPs)**은 모델 용량을 결정하는 두 가지 주요 요소이며, 이들의 상호 작용에 대한 이해가 스케일링 법칙의 핵심입니다. 특히, **희소 혼합 전문가(MoE) 모델**에서는 매개변수의 수를 증가시키더라도 샘플당 FLOPs는 비례적으로 증가하지 않으므로, 스케일링 법칙에 대한 심층적인 분석이 필요합니다. 이 연구는 다양한 스파스성 수준을 고려하여 사전 훈련 및 몇 번의 시도만으로 평가하는 과정에서 모델 성능에 미치는 영향을 분석합니다. **최적의 스파스성 수준**을 찾는 것이 효율성과 성능 향상의 관건이며, 이는 훈련 컴퓨팅 예산에 따라 달라집니다. 또한, 스케일링 법칙을 통해 **사전 훈련 손실과 다운스트림 작업 성능 간의 상관 관계**를 이해할 수 있습니다. 이 연구는 스파스성을 스케일링 법칙에 통합하여 모델의 성능을 더욱 정확하게 예측할 수 있는 새로운 매개변수 방정식을 제시합니다.

#### Future Work
본 논문의 "향후 연구" 부분은 **MoE(Mixture-of-Experts) 모델의 효율성을 더욱 높이기 위한 구체적인 방향**을 제시합니다. 특히, **매개변수 수와 FLOPs 간의 최적 균형점을 찾는 연구**는 인퍼런스 비용을 낮추면서 성능을 유지하는 데 중요합니다. 또한, 다양한 다운스트림 작업에 대한 모델 성능 분석을 통해 매개변수 할당 전략과 계산 요구량 균형을 최적화하는 방안을 모색해야 합니다.  **다양한 하드웨어 환경에 따른 성능 분석**과 **메모리 및 통신 오버헤드 고려**는 실제 적용 가능성을 높이는 데 필수적입니다.  **부정적 스파스성을 활용하는 모델**에 대한 연구는 새로운 효율성 개선 가능성을 제시합니다.  **이러한 추가적인 연구들을 통해 MoE 모델의 실제 적용 가능성을 확대하고, 보다 효율적이고 강력한 언어 모델 개발**에 기여할 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.12370/x2.png)

> 🔼 이 그림은 고정된 컴퓨팅 예산 하에서, 희소 혼합 전문가(MoE) 언어 모델의 성능에 대한 매개변수 수와 활성 매개변수 수의 상호 작용을 보여줍니다.  모델 크기(활성 매개변수)와 희소성 수준을 변화시키면서 손실을 시각화하여, 최적의 희소성 수준을 찾는 데 도움이 됩니다.  즉, 계산 효율성을 유지하면서 모델 성능을 최대화하는 희소성 수준을 보여주는 표면을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> (b) IsoFLOP surface over sparsity and active parameters
> </details>



![](https://arxiv.org/html/2501.12370/x3.png)

> 🔼 그림 1은 사전 학습 손실(L), 총 매개변수(N) 및 활성 매개변수(Na)와 스파스성(S)에 대한 등량 FLOP 표면을 보여줍니다. 실험 데이터를 사용하여 N(또는 Na), S 및 상호 작용을 L에 매핑하는 다항식 함수를 적합했습니다. 두 적합 모두 홀드아웃 집합에서 0.0001의 MSE 손실을 달성했습니다. 이러한 결과는 고정된 계산 예산의 경우 모델 스파스성을 높이면 사전 학습 손실이 감소한다는 것을 나타냅니다. 최적 모델 크기를 고려할 때 총 매개변수(N)(그림 a)와 활성 매개변수(Na)(그림 b)에 대해 반대되는 추세를 관찰했습니다. 그림 8에는 다양한 총 계산 예산(C)에 대한 결과가 나와있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: IsoFLOP surface over observed pretraining loss 𝐋𝐋\mathbf{L}bold_L, model size (in terms of total 𝐍𝐍\mathbf{N}bold_N and active parameters 𝐍𝐚subscript𝐍𝐚\mathbf{N_{a}}bold_N start_POSTSUBSCRIPT bold_a end_POSTSUBSCRIPT), and sparsity 𝐒𝐒\mathbf{S}bold_S. We fit a polynomial function mapping 𝐍𝐍\mathbf{N}bold_N (or 𝐍𝐚subscript𝐍𝐚\mathbf{N_{a}}bold_N start_POSTSUBSCRIPT bold_a end_POSTSUBSCRIPT), 𝐒𝐒\mathbf{S}bold_S, and their interaction to 𝐋𝐋\mathbf{L}bold_L, using empirical data. Both fits achieve an MSE loss of 0.0001 on a held-out set. These results indicate that for a fixed compute budget, increasing model sparsity leads to a reduction in pretraining loss. When considering optimal model size, we observe opposite trends for total parameters (𝐍𝐍\mathbf{N}bold_N) (Figure a) versus active parameters (𝐍𝐚subscript𝐍𝐚\mathbf{N_{a}}bold_N start_POSTSUBSCRIPT bold_a end_POSTSUBSCRIPT) (Figure b). (Figure 8 includes results Section D.1 for different total compute budgets C𝐶Citalic_C.)
> </details>



![](https://arxiv.org/html/2501.12370/x4.png)

> 🔼 그림 2는 고정된 컴퓨팅 예산(C=1e20) 하에서, sparsity (S)와 모델 크기 (N)가 손실(L)에 미치는 영향을 분석한 것입니다. 이 그림은 (a) N을 고정하고 S를 변화시켜 최적의 S를 찾고, (b) S를 고정하고 N을 변화시켜 최적의 N을 찾고, (c) S를 고정하고 활성 파라미터(Na)를 변화시켜 최적의 Na를 찾는 세 가지 방법으로 최적점을 확인합니다. 그림에서 보여주듯이, (a) 최적 sparsity S는 모델 크기 N이 증가함에 따라 증가하며 1에 수렴하고, (b)와 (c)에서는 최적 모델 크기 N과 활성 파라미터 수 Na가 sparsity S의 증가에 따라 각각 증가 및 감소하는 것을 알 수 있습니다. 부록 D.1의 그림 9에서는 다른 총 훈련 컴퓨팅 예산에 대한 결과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: IsoFLOP slices along Sparsity and Model Size (C=1⁢e⁢20𝐶1𝑒20C=1e20italic_C = 1 italic_e 20). We use fitted isoFLOP surfaces (Section 2) to analyze how sparsity 𝐒𝐒\mathbf{S}bold_S and model size 𝐍𝐍\mathbf{N}bold_N impact the loss 𝐋𝐋\mathbf{L}bold_L for a fixed compute budget. We identify optimal points by (a) fixing 𝐍𝐍\mathbf{N}bold_N and varying 𝐒𝐒\mathbf{S}bold_S, (b) fixing 𝐒𝐒\mathbf{S}bold_S and varying 𝐍𝐍\mathbf{N}bold_N and (c) fixing 𝐒𝐒\mathbf{S}bold_S and varying active parameters 𝐍𝐚subscript𝐍𝐚\mathbf{N_{a}}bold_N start_POSTSUBSCRIPT bold_a end_POSTSUBSCRIPT. Observe that (a) the optimal sparsity S𝑆Sitalic_S increases with increasing model size N𝑁Nitalic_N and converges to 1 while (b) and (c) show that the optimal model size N𝑁Nitalic_N and active parameter count Nasubscript𝑁𝑎N_{a}italic_N start_POSTSUBSCRIPT italic_a end_POSTSUBSCRIPT increase and decrease respectively with increasing sparsity levels. (see Figure 9 in Section D.1 for other total training compute budgets.)
> </details>



![](https://arxiv.org/html/2501.12370/x5.png)

> 🔼 그림 3은 모델 크기, 활성 매개변수 수, 그리고 스파스성에 따른 손실에 대한 컴퓨팅 예산의 영향을 보여줍니다. 모든 컴퓨팅 예산에서 (a) 최적 모델 크기 N은 스파스성이 증가함에 따라 증가하고, (b) 최적 활성 매개변수 수 Na는 스파스성이 증가함에 따라 감소하며, (c) 손실 L은 스파스성이 증가함에 따라 감소합니다. 이 그림은 훈련 컴퓨팅 예산이 증가함에 따라 모델 크기와 스파스성 간의 상호 작용에 미치는 영향을 보여주는 추가 분석을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3:  Effect of compute budget on model size, number of active parameters and loss with sparsity. Across all compute budgets, we observe that (a) the optimal model size N𝑁Nitalic_N increases with sparsity, (b) the optimal number of active parameters Nasubscript𝑁𝑎N_{a}italic_N start_POSTSUBSCRIPT italic_a end_POSTSUBSCRIPT decreases with sparsity, and (c) the loss L𝐿Litalic_L decreases with sparsity.
> </details>



![](https://arxiv.org/html/2501.12370/x6.png)

> 🔼 이 그림은 주어진 훈련 컴퓨팅 예산 하에서 최적의 MoE(Mixture-of-Experts) 스파스(sparsity) 수준이 모델의 파라미터 수와 훈련 컴퓨팅 예산에 따라 어떻게 변하는지 보여줍니다. x축은 로그 스케일로 표현된 총 파라미터 수를 나타내고, y축은 최적의 MoE 스파스 수준을 나타냅니다.  다양한 훈련 컴퓨팅 예산(C)에 대한 최적 스파스 수준(S*)의 변화를 보여주는 여러 선이 그려져 있습니다. 이 그림은 훈련 컴퓨팅 예산과 모델 크기가 MoE 스파스성과 최적화된 모델 성능 간의 상호 작용에 미치는 영향을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Effect of training budget C𝐶Citalic_C and total parameters N𝑁Nitalic_N on MoE sparsity. Optimal MoE sparsity S∗superscript𝑆S^{*}italic_S start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT changes with respect to the total number of parameters N𝑁Nitalic_N and the training budget C𝐶Citalic_C. The x𝑥xitalic_x-axis represents the total parameters N𝑁Nitalic_N on a logarithmic scale, and the y𝑦yitalic_y-axis shows the optimal MoE sparsity S∗superscript𝑆S^{*}italic_S start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT.
> </details>



![](https://arxiv.org/html/2501.12370/x7.png)

> 🔼 본 그림은 사전 학습 손실(업스트림)과 다양한 다운스트림 작업의 성능 간의 관계를 보여줍니다. 모든 다운스트림 작업에서 사전 학습 손실이 감소함에 따라 다운스트림 작업의 성능이 향상되는 밀접한 관계를 보여줍니다. 이는 희소성 수준에 관계없이 일관되게 나타나며, 사전 학습 성능이 다운스트림 작업 성능에 상당한 영향을 미침을 보여줍니다. 그러나, 읽기 이해 작업의 경우, 더 희소한 모델이 밀집 모델보다 성능이 떨어질 수 있습니다. 이는 더 적은 계산 비용으로 인해 발생할 수 있으며, 이에 대한 추가적인 분석이 필요합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5:  Effect of sparsity on downstream vs upstream performance. Downstream error shows a tight relationship with pretraining (“upstream”) loss across downstream tasks across all sparsity levels.
> </details>



![](https://arxiv.org/html/2501.12370/x8.png)

> 🔼 이 그림은 논문의 5장 '스파스성을 스케일링 법칙에 통합하기'에서 제시된 매개변수 스케일링 법칙을 데이터에 적합시키는 과정을 보여줍니다.  (a)는 계수를 추정하는 데 사용된 데이터에 대한 적합도를, (b)는 보유된 데이터 세트에 대한 스케일링 법칙의 유효성 검사 결과를 보여줍니다.  그림 (a)는 추정된 매개변수를 사용하여 생성된 손실과 실제 관찰된 손실 간의 관계를 보여주는 산점도입니다. 그림 (b)는 독립적인 데이터 세트에 대한 모델의 예측 성능을 평가한 결과입니다.  이는 제안된 스케일링 법칙의 정확성과 일반화 능력을 평가하는 데 중요한 부분입니다.
> <details>
> <summary>read the caption</summary>
> (a) Fit on data used to estimate coefficients.
> </details>



![](https://arxiv.org/html/2501.12370/x9.png)

> 🔼 그림 6(b)는 제시된 매개변수화된 스케일링 법칙의 예측 성능을 검증하기 위해 사용된 홀드아웃 데이터셋에 대한 결과를 보여줍니다.  이 그림은 스케일링 법칙이 훈련 연산량이 최적화된 모델에 대해 얼마나 잘 일반화되는지 보여줍니다.  x축은 실제 손실을, y축은 예측 손실을 나타냅니다.  각 점은 특정 모델 크기와 데이터셋 크기를 나타내며, 직선 y=x는 완벽한 예측을 나타냅니다. 점들이 직선에서 얼마나 벗어나 있는지 확인하면 모델의 예측 정확도를 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (b) Validating scaling law on held-out dataset.
> </details>



![](https://arxiv.org/html/2501.12370/x10.png)

> 🔼 그림 6은 계산량 최적화 모델 학습에서 얻은 데이터에 대한 스케일링 법칙 적합을 보여줍니다. (a)는 등식 6의 계수를 추정하는 데 사용된 데이터에 대한 적합을, (b)는 샘플 외 검증을 위해 S=0.98인 모든 데이터 지점을 제외하고 보류 데이터 세트에 대한 계수의 유효성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Scaling law fit on data obtained from training compute-optimal models. Figure 6(a) shows the fit on the data used to estimate the coefficients for equation 6, while Figure 6(b) validates these coefficients on a held-out dataset. All data points with S=0.98𝑆0.98S=0.98italic_S = 0.98 were excluded from the fitting process for out-of-sample validation.
> </details>



![](https://arxiv.org/html/2501.12370/x11.png)

> 🔼 그림 7은 Mixture-of-Experts(MoE) 모델에 대한 FLOPs 추정 방식의 정확도를 보여줍니다. 이 그림은 본 논문의 등식 (9)를 사용하여 계산된 MoE FLOPs 추정값과 6NaD 추정값의 비율을 모델의 총 파라미터 수의 함수로 나타냅니다. 고정된 context 길이 D=2048을 사용하여 실험에서 얻은 결과를 보여줍니다. 이 그림을 통해 MoE 모델에 대한 6NaD 추정 방식의 정확도를 파라미터 수에 따라 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Accuracy of 6⁢Na⁢D6subscript𝑁𝑎𝐷6N_{a}D6 italic_N start_POSTSUBSCRIPT italic_a end_POSTSUBSCRIPT italic_D FLOPs Estimator for MoEs. Ratio of the MoE FLOPs estimator (Equation 9) to the 6⁢Na⁢D6subscript𝑁𝑎𝐷6N_{a}D6 italic_N start_POSTSUBSCRIPT italic_a end_POSTSUBSCRIPT italic_D estimator as a function of the total number of parameters, for a fixed context length of D=2048𝐷2048D=2048italic_D = 2048, used in our experiments.
> </details>



![](https://arxiv.org/html/2501.12370/x12.png)

> 🔼 그림 8은 다양한 연산 예산(compute budget) 하에서 총 파라미터 수(N), MoE 스파스(S), 그리고 사전 훈련 손실(L)에 대한 IsoFLOP 표면을 보여줍니다. 각 행은 3e19, 6e19, 1e20, 3e20, 1e21의 예산으로 훈련된 모델을 사용하여 적합된 IsoFLOP 표면에 해당합니다. 왼쪽 하위 그림은 총 파라미터 수(N)와 스파스 수준(S)을 사전 훈련 손실(L)에 매핑하는 IsoFLOP 표면을 시각화합니다. 오른쪽 하위 그림은 보류된 데이터에 대한 추정 사전 훈련 손실과 실제 사전 훈련 손실의 상관 관계를 보여줍니다. 종합적으로 이러한 결과는 IsoFLOP 표면이 모델 크기와 MoE 스파스가 사전 훈련 손실에 미치는 영향을 이해하는 데 정확한 근사치임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8:  IsoFLOP surfaces over total parameters N𝑁Nitalic_N, MoE sparsity S𝑆Sitalic_S, and pretraining loss L𝐿Litalic_L for different compute budgets. The rows correspond to IsoFLOP surface fitted using models trained with a budget of 3e19, 6e19, 1e20, 3e20, and 1e21. The subplots on the left visualize IsoFLOP surfaces mapping total parameters N𝑁Nitalic_N and sparsity level S𝑆Sitalic_S to pretraining loss L𝐿Litalic_L. The subplots on the right correlate the ground-truth pretraining loss with the estimated pretraining loss on held-out data. Taken together, these results show that isoFLOP surfaces are accurate proxies for understanding how model size and MoE sparsity jointly impact pretraining loss.
> </details>



![](https://arxiv.org/html/2501.12370/x13.png)

> 🔼 그림 9는 학습 컴퓨팅 예산에 따라 최적의 MoE 구성이 예측 가능하게 변화하는 것을 보여줍니다. 각 행은 주어진 학습 컴퓨팅 예산에 대해 최적의 MoE 스파스성 (S*), 총 매개변수 (N*), 활성 매개변수 (Na*)가 어떻게 변하는지 분석한 결과입니다. 왼쪽 하위 그림은 (a) 학습 컴퓨팅 예산이 증가함에 따라 최소 사전 학습 손실을 가진 모델 크기(N)가 증가하고 (b) 학습 컴퓨팅 예산보다 작은 모델의 경우에는(예산이 증가함에 따라 증가), 스파스 MoE보다 조밀한 모델(즉, 스파스성 0%)이 더 좋은 성능을 보인다는 것을 보여줍니다. 두 번째와 세 번째 패널의 하위 그림은 (a) MoE 스파스성이 증가함에 따라 최적의 총 매개변수(N*)가 증가하고 최적의 활성 매개변수(Na*)가 감소하며 (b) 고정된 스파스성 수준에서 예산이 증가함에 따라 최적의 총 매개변수와 활성 매개변수가 모두 증가함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 9:  Optimal MoE configurations predictably change with training compute budget. Each row corresponds to an analysis of how optimal MoE sparsity S∗superscript𝑆S^{*}italic_S start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT, total parameters N∗superscript𝑁N^{*}italic_N start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT, and active parameters Na∗subscriptsuperscript𝑁𝑎N^{*}_{a}italic_N start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT start_POSTSUBSCRIPT italic_a end_POSTSUBSCRIPT change for a given training budget. The subplots on the left show that (a) increasing the training budget increases the model size N𝑁Nitalic_N (denoted with black dots) with the minimum pretraining loss and (b) for models smaller than a threshold (which increases with training budget), dense models (i.e., 0%percent00\%0 % sparsity) fare better than sparse MoEs. The subplots in the second and third panel show that (a) increasing MoE sparsity increases the optimal total parameters N∗superscript𝑁N^{*}italic_N start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT and decreases the optimal active parameters Na∗subscriptsuperscript𝑁𝑎N^{*}_{a}italic_N start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT start_POSTSUBSCRIPT italic_a end_POSTSUBSCRIPT. In both cases, for a fixed sparsity level, increasing the budget shifts increases the optimal total and active parameters.
> </details>



![](https://arxiv.org/html/2501.12370/x14.png)

> 🔼 그림 10은 업스트림 사전 훈련 손실(x축)과 다운스트림 작업 성능(y축) 간의 관계를 특정 작업에 대해 보여줍니다. 각 하위 그림은 특정 작업에 대한 업스트림 사전 훈련 손실과 다운스트림 작업 성능 간의 관계를 보여줍니다. 섹션 4의 결과와 마찬가지로, MoE 스파스성 수준은 업스트림 사전 훈련 손실과 다운스트림 작업 성능 간의 관계를 변경하지 않는다는 것을 알 수 있습니다. 이 그림은 다양한 다운스트림 작업에서 사전 훈련 손실과 성능 간의 관계가 MoE 스파스성 수준에 따라 어떻게 변하는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 10:  Downstream task performance vs. upstream pre-training loss. Each subplot shows the relationship between upstream pre-training loss (x-axis) and downstream task performance (y-axis) for a specific task. Similar to our results in Section 4, we find that the MoE sparsity level does not change the relationship between upstream pre-training loss and downstream task performance.
> </details>



![](https://arxiv.org/html/2501.12370/x15.png)

> 🔼 그림 11은 다양한 훈련 연산량 예산에서 MoE(Mixture-of-Experts)의 sparsity가 pretraining loss에 미치는 영향을 보여줍니다. sparsity가 증가함에 따라 검증 loss는 모든 연산량 예산에서 감소하며, 더 큰 예산(더 어두운 선)일수록 각 sparsity 수준에서 더 낮은 loss를 달성합니다. 이러한 경향은 3장의 결과와 일치하며, sparsity를 증가시키면 모든 훈련 연산량 예산에서 최적의 pretraining loss가 감소함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 11:  Effect of MoE sparsity on pretraining loss across different training compute budgets. As sparsity increases, the validation loss decreases for all compute budgets, with larger budgets (darker lines) achieving lower losses at each sparsity level. This trend is consistent with the findings from Section 3, demonstrating that increasing sparsity reduces the optimal pretraining loss across all compute budgets.
> </details>



![](https://arxiv.org/html/2501.12370/x16.png)

> 🔼 그림 12는 고정된 훈련 컴퓨팅 예산 하에서 다양한 훈련 컴퓨팅 예산에 걸쳐 최적의 총 매개변수와 활성 매개변수에 대한 MoE 스파스티의 효과를 보여줍니다. 각 행은 고정된 훈련 예산에 대해 스파스티 수준의 함수로 총 매개변수와 활성 매개변수의 변화를 보여줍니다. 스파스티가 증가함에 따라 최적의 총 매개변수는 증가하고 최적의 활성 매개변수는 감소하는데, 이는 2절(그림 2)의 결과와 일치합니다. 더 큰 훈련 컴퓨팅 예산은 모든 스파스티 수준에서 더 높은 최적의 (총 및 활성) 매개변수를 초래합니다.
> <details>
> <summary>read the caption</summary>
> Figure 12:  Effect of MoE sparsity on optimal total and active parameters across different training compute budgets. Each row shows the change in total and active parameters as a function of sparsity level for fixed training budgets. Increasing sparsity leads to an increase in the optimal total parameters while reducing the optimal active parameters, consistent with our findings in Section 2 (Figure 2). Larger training compute budgets result in higher optimal (total and active) parameters across all sparsity levels.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Hyperparameter | Configuration | Search Space |
|---|---|---|
| Sparsity Level | Tuned | {0,25,50,75,90,95,98}% |
| Number of Total Experts | Tuned | Adjusted depending on sparsity |
| Number of Active Experts | Tuned | Adjusted depending on sparsity |
| Granularity | Tuned | {1,2} |
| Learning Rate | Tuned | [0.003,0.002,0.001] |
| Load Balancing Factor | Tuned | {0.02,0.05} |
| Warm-up Steps | Tuned | {2,5,10}% |
| Batch Size | Constant | 1024 |
| Jitter Noise | Constant | 0 |
| z-Loss | Constant | 0 |
| z-Router Loss | Constant | 0.001 |
| QK Norm | Constant | Applied |{{< /table-caption >}}
> 🔼 표 2는 논문의 등식 6에서 계수를 추정하는 데 사용된 초기값을 보여줍니다.  이 표는 각 계수에 대해 사용된 초기값의 범위를 보여주며,  논문에서 제시된 매개변수화된 확장 법칙 모델을 학습시키는 데 사용된 최적화 알고리즘인 L-BFGS의 초기화에 중요한 역할을 합니다. 이 초기값들은 최종 추정값을 얻기 위한 반복적인 최적화 과정의 시작점을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Initial values used to estimate coefficients in Equation 6.
> </details>

{{< table-caption >}}
| Coefficients | Initial Values |
|---|---| 
| \log(a), \log(b), \log(c), \log(d) | \left[0,10,20\right] |
| \alpha, \beta, \gamma | \left[0,0.25,0.5,0.75,1,1.25\right] |
| \lambda, \delta | \left[-1,-0.5,0,0.5,1\right] |
| \log(e) | 1.5 |{{< /table-caption >}}
> 🔼 표 3은 논문의 등식 6에서 계수를 추정하기 위해 사용된 추정값을 보여줍니다. 이 표는 다양한 매개변수(α, β, γ, λ, δ, a, b, c, d, e)에 대한 추정값을 제공하며, 이러한 매개변수는 논문에서 제시된 파라메트릭 스케일링 법칙 모델의 성능을 평가하는 데 사용됩니다.  추정된 모델 계수의 성능은 보유 데이터 세트에 대한 평균 제곱 오차와 허버 손실 오차로 측정되며, 이는 표에 함께 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Estimated values for coefficients in Equation 6.
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