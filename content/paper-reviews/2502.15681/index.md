---
title: "One-step Diffusion Models with $f$-Divergence Distribution Matching"
summary: "f-divergence 최소화를 통해 단일 단계 확산 모델의 생성 속도를 높이는 새로운 방법, f-distill 제시!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Generation", "🏢 NVIDIA",]
showSummary: true
date: 2025-02-21
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.15681 {{< /keyword >}}
{{< keyword icon="writer" >}} Yilun Xu et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-24 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.15681" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.15681" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 다단계 확산 모델은 이미지 생성에 시간이 오래 걸리는 단점이 있습니다. 이를 해결하기 위해, 최근에는 다단계 모델을 단일 단계 모델로 변환하는 연구가 활발히 진행되고 있습니다. 하지만 기존의 방법들은 특정 분포(reverse KL divergence)에만 의존하여 mode collapse 문제를 야기할 수 있다는 한계가 있었습니다. 

본 논문에서는 이러한 문제를 해결하기 위해 **f-divergence 최소화 프레임워크 기반의 새로운 방법론인 f-distill**을 제시합니다. f-distill은 다양한 f-divergence를 사용하여 학습 과정의 변동성과 모드 포착 능력 사이의 절충점을 찾아내어, 기존 방법들보다 더욱 다양하고 정확한 이미지를 생성할 수 있습니다. 실험 결과, **ImageNet64 및 MS-COCO 데이터셋에서 최첨단 성능**을 달성하였음을 보였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} f-divergence 최소화 프레임워크 기반의 새로운 단일 단계 확산 모델 생성 방법 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 다양한 f-divergence의 장단점 분석을 통해 mode coverage 및 학습 안정성 간의 최적 균형점 도출 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} ImageNet64 및 MS-COCO 데이터셋에서 최첨단 성능 달성 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **확산 모델의 느린 생성 속도 문제를 해결하기 위한 새로운 방법론**을 제시하여, 이미지 생성 분야의 연구에 상당한 영향을 미칠 것으로 예상됩니다. 특히, **다양한 f-divergence를 활용하여 학습 과정의 변동성과 모드 포착 능력 사이의 절충점을 찾는 새로운 접근법**은 향후 연구 방향에 중요한 시사점을 제공합니다. 또한, **다양한 데이터셋에서 최첨단 성능을 달성**함으로써, 실제 응용 분야에서의 활용 가능성을 높였습니다. 이러한 결과는 향후 **일반적인 생성 모델의 성능 향상 및 효율적인 학습 방법 개발**에 기여할 것으로 기대됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.15681/extracted/6217836/img/main_3.png)

> 🔼 그림 1은 제안된 f-distill 방법에서 한 단계 학습 모델의 기울기 업데이트 과정을 보여줍니다. 기울기는 교사 점수와 가짜 점수의 차이와 선택된 f-divergence와 밀도 비율에 따라 결정되는 가중치 함수의 곱으로 계산됩니다. 보조 GAN 목적 함수의 판별기에서 밀도 비율을 쉽게 구할 수 있습니다.  즉, 한 단계 생성 모델의 출력 분포와 사전 훈련된 교사 확산 모델의 출력 분포 간의 차이를 최소화하기 위해 f-divergence를 사용하여 기울기를 계산합니다. 이 때, 밀도 비율을 고려하는 가중치 함수가 사용되는데, 이는 보조 GAN에서 판별기를 통해 얻을 수 있습니다. 이 그림은 f-distill이 어떻게 교사 모델과 학생 모델의 점수 차이를 효율적으로 활용하여 학생 모델의 출력 분포를 교사 모델의 출력 분포에 맞추는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: The gradient update for the one-step student in f𝑓fitalic_f-distill. The gradient is a product of the difference between the teacher score and fake score, and a weighting function determined by the chosen f𝑓fitalic_f-divergence and density ratio. The density ratio is readily available from the discriminator in the auxiliary GAN objective.
> </details>





{{< table-caption >}}
| f(r) | h(r) | Mode-seeking? | Saturation? | Variance | 
|---|---|---|---|---| 
| reverse-KL | -log r | 1 | Yes | No | - | 
| softened RKL | (r+1)log((1/2)+(1/2r)) | 1/(r+1) | Yes | No | Low | 
| Jensen-Shannon | rlogr-(r+1)log((r+1)/2) | r/(r+1) | Medium | Yes | Low | 
| squared Hellinger | 1-√r | (1/4)r^(1/2) | Medium | Yes | Low | 
| forward-KL | rlogr | r | No | No | High | 
| Jeffreys | (r-1)log(r) | r+1 | No | No | High | {{< /table-caption >}}

> 🔼 이 표는 likelihood ratio r = p(x)/q(x) 의 함수로서 다양한 f-divergence 를 비교한 것입니다. 각 f-divergence 에 대해 mode-seeking 경향, saturation 정도, 그리고 학습 중 분산 정도를 보여줍니다.  reverse-KL, softened RKL, Jensen-Shannon, squared Hellinger, forward-KL, 그리고 Jeffreys divergence 가 포함되어 있으며, 각 divergence 의 mode-seeking 정도와 saturation 정도를 나타내는 값과 함께 분산 정도를 나타내는  variance 값이 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparison of different f𝑓fitalic_f-divergences as a function of the likelihood ratio r:=p⁢(𝐱)/q⁢(𝐱)assign𝑟𝑝𝐱𝑞𝐱r:=p({\mathbf{x}})/q({\mathbf{x}})italic_r := italic_p ( bold_x ) / italic_q ( bold_x )
> </details>





### In-depth insights


#### f-Divergence Distillation
본 논문에서 제안하는 f-Divergence Distillation은 기존의 변분 점수 증류(Variational Score Distillation) 방식을 일반화한 것으로, **다양한 f-다이버전스를 사용하여 teacher 모델과 student 모델 간의 분포 일치를 최적화**합니다.  이는 reverse KL 다이버전스의 mode-seeking 문제를 해결하기 위한 시도이며, forward KL, Jensen-Shannon 다이버전스 등 다양한 다이버전스의 모드 커버리지 및 훈련 분산 특성을 분석하여 **최적의 다이버전스 선택**을 가능하게 합니다.  **가중치 함수(weighting function)**를 도입하여 teacher 분포의 고밀도 영역을 강조함으로써 student 모델의 샘플링 속도 향상 및 다양성 확보에 기여합니다. 실험 결과는 제안된 방법이 기존 최고 성능의 방법들을 능가하는 것을 보여주며, 특히 Jensen-Shannon 다이버전스를 사용했을 때 ImageNet64 및 MS-COCO zero-shot text-to-image 생성에서 최첨단 성능을 달성함을 입증합니다.  **다양한 f-다이버전스의 장단점 비교 분석** 및 **실제 구현에 필요한 실용적인 가이드라인**도 제시되어 있어, 다양한 생성 모델에 적용 가능성을 높였습니다.

#### One-Step Diffusion
본 논문에서 제시된 'One-Step Diffusion' 개념은 기존의 다단계 확산 모델의 계산 비용과 시간 소모 문제를 해결하기 위한 혁신적인 시도입니다. **단일 단계 내에서 고품질 이미지 생성을 달성**함으로써 실시간 응용 및 상호작용 애플리케이션에 대한 활용 가능성을 크게 높입니다. 이는 기존의 반복적인 확산 과정을 생략하고, **단일 신경망을 통해 직접적으로 샘플링을 수행**함으로써 효율성을 극대화합니다.  **f-divergence 최소화 기법**을 활용하여 교사 모델과 학생 모델 간의 분포 불일치를 최소화함으로써, 학생 모델의 생성 품질을 향상시키는 데 주력합니다.  **다양한 f-divergence 함수**를 활용하여 모드 커버리지와 훈련 안정성 간의 절충점을 찾아, 최적의 성능을 달성하고자 합니다.  **Jensen-Shannon divergence**는 특히 주목할 만한데, 모드 커버리지와 분산 간의 균형을 잘 맞춰 실험 결과에서 최고 성능을 보였습니다.  하지만, **고차원 데이터셋 및 텍스트-이미지 생성과 같은 복잡한 작업**에서는 분산이 여전히 문제가 될 수 있다는 점에 유의해야 합니다. 따라서, 본 연구는 One-Step Diffusion 모델의 효율성과 성능 개선에 크게 기여하지만,  **지속적인 연구**를 통해 더욱 안정적이고 견고한 모델 개발이 필요함을 시사합니다.

#### Mode-Seeking Divergence
본 논문에서 다룬 "Mode-Seeking Divergence"는 **분포 일치(Distribution Matching)** 기법에서 사용되는 f-divergence의 특정한 종류를 지칭합니다.  f-divergence는 학습된 확률 분포 간의 차이를 측정하는 일반적인 척도로 다양한 종류의 divergence를 포함합니다.  **Mode-seeking divergence는 특정 모드(Mode)에 지나치게 집중하는 경향**이 있으며, 이는 다양한 모드를 학습한 Teacher 모델의 풍부한 정보를 제대로 활용하지 못하는 결과를 초래할 수 있습니다.  본 논문에서는 **Reverse-KL divergence가 mode-seeking 성향을 가지는 대표적인 예**임을 보이고, 이를 극복하기 위해 Forward-KL, Jensen-Shannon 등 다양한 f-divergence를 제안 및 평가하여 **모드 커버리지와 학습 안정성 간의 균형**을 이루는 최적의 divergence를 찾고자 합니다.  이는 단일 단계 확산 모델(One-step diffusion model)의 성능 향상에 중요한 요소로, 다양한 모드를 균형 있게 학습함으로써 보다 다채롭고 현실적인 이미지 생성을 가능하게 합니다.

#### GAN-Objective Synergy
본 논문에서 제시된 GAN-Objective Synergy는 단순히 GAN 손실을 추가하는 것을 넘어, **f-divergence 기반의 분포 일치 증류 접근 방식과 GAN 목적 함수 간의 시너지 효과**를 강조합니다.  GAN 손실은 학습 과정에서 발생할 수 있는 모드 붕괴 현상을 방지하고, 학생 생성기가 다양한 모드를 잘 포착할 수 있도록 돕습니다.  이는 f-divergence가 가진 모드 탐색 경향을 보완하는 역할을 합니다. 특히, **낮은 모드 탐색 경향을 지닌 f-divergence (예: Jensen-Shannon)** 를 사용하는 경우, GAN 손실이 학생 생성기의 성능 향상에 더욱 크게 기여하는 것을 확인할 수 있었습니다.  즉, f-divergence가 다양한 모드를 잘 표현하도록 유도하고, GAN은 그러한 다양성을 유지하며 안정적인 학습을 가능하게 합니다. **두 기법의 상호 보완적인 관계**는 고품질 이미지 생성을 위한 핵심 요소임을 강조합니다.  본 연구는 단순히 두 가지 손실 함수를 결합하는 것이 아니라, **두 기법 간의 상호작용과 시너지 효과**에 대한 깊이 있는 분석을 통해 최첨단 성능을 달성했습니다.

#### Variance and Normalization
본 논문에서 다루는 가중치 함수의 분산은 f-다이버전스의 선택에 따라 크게 달라지는데, **특히 모드를 적게 찾는(less mode-seeking) f-다이버전스일수록 분산이 커지는 경향**이 있습니다. 이는 모드를 적게 찾는 f-다이버전스가 밀도가 낮은 영역의 샘플에 작은 가중치를 부여함으로써 발생하는데, 이 영역에서의 기울기 추정이 부정확하기 때문입니다.  이러한 문제를 해결하기 위해 **두 단계의 정규화 기법**을 제안합니다.  첫 번째는 시간에 따른 밀도 비율을 정규화하고, 두 번째는 미니 배치 내에서 가중치 함수 자체를 정규화하여, **다양한 f-다이버전스에 대한 안정적인 학습을 가능하게 합니다.**  결과적으로, 제안된 정규화 기법은 고분산 f-다이버전스의 성능을 개선하여, 다양한 데이터셋에서 최첨단 성능을 달성하는 데 기여합니다.  **정규화 전략은 학습 과정의 안정성을 확보하는데 중요하며, 특히 고분산 f-다이버전스를 사용할 때 효과적**임을 보여줍니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.15681/x1.png)

> 🔼 그림 2는 2차원 예시에서 점수 차이와 가중치 함수를 보여줍니다.  forward-KL에서 가중치 함수는 h입니다.  왼쪽 아래 그림에서 어두운 색상은 점수 차이가 크다는 것을 나타내며, 이는 낮은 밀도 영역에서 교사와 가짜 점수가 자주 분기한다는 것을 의미합니다. 이러한 영역에서는 추정 오류가 더 클 수 있습니다. 가중치 함수는 f-distill의 기울기 업데이트 중에 이러한 영역(오른쪽 아래 그림의 밝은 색상)의 가중치를 낮춥니다. 즉, 낮은 밀도 영역에서의 점수 차이가 결과에 미치는 영향을 줄여 과적합을 방지하고 더 안정적인 학습을 유도합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Score difference and the weighting function on a 2D example. hℎhitalic_h is the weighting function in forward-KL. Observe that the teacher and fake scores often diverge in lower-density regions (darker colors in the bottom left figure indicate larger score differences), where larger estimation errors occur. The weighting function downweights these regions (lighter colors in the bottom right figure) during gradient updates for f𝑓fitalic_f-distill.
> </details>



![](https://arxiv.org/html/2502.15681/x2.png)

> 🔼 그림 (a)는 두 개의 1차원 가우스 분포 간의 평균 차이에 따른 다양한 f-다이버전스의 정규화된 분산을 보여줍니다. 그림은 정규화된 분산이 가우스 분포 간의 평균 차이가 증가함에 따라 역방향 KL 다이버전스와 제프리스 다이버전스의 경우 크게 증가하는 반면, 제곱 헬링거 다이버전스와 JS 다이버전스는 상대적으로 안정적인 것을 보여줍니다. 이는 훈련 과정에서 JS 다이버전스가 더 낮은 분산을 가지므로 더 나은 성능을 달성할 수 있다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (a)
> </details>



![](https://arxiv.org/html/2502.15681/x3.png)

> 🔼 그림 (b)는 서로 다른 f-다이버전스의 가중 함수 h(r)의 절대값을 보여줍니다. 가중 함수는 f-다이버전스와 밀도 비율에 따라 결정되며, 학습 과정에서 가중치를 조정하는 데 사용됩니다. 그래프에서 볼 수 있듯이, 역방향 KL 다이버전스의 가중 함수는 일정한 값을 유지하는 반면, 다른 다이버전스의 가중 함수는 밀도 비율에 따라 변화합니다. 이는 다양한 f-다이버전스가 학습 과정에 미치는 영향과 그 차이를 보여주는 중요한 시각적 자료입니다.
> <details>
> <summary>read the caption</summary>
> (b)
> </details>



![](https://arxiv.org/html/2502.15681/x4.png)

> 🔼 그림 3은 다양한 f-divergence에서 likelihood ratio r에 대한 f′(r)의 절대값과 가중치 함수 h(r)의 그래프를 보여줍니다.  f′(r)은 f-divergence의 기울기를 나타내며, h(r)은 f-distill에서 teacher와 student 분포 간의 차이에 가중치를 부여하는 함수입니다.  각 f-divergence는 mode coverage와 gradient variance 측면에서 서로 다른 특징을 보이는데, 이 그림은 이러한 특징을 시각적으로 보여주고 각 f-divergence의 mode-seeking 정도와 gradient saturation 정도를 이해하는 데 도움이 됩니다. reverse-KL은 mode-seeking 경향이 강하고, forward-KL은 mode-seeking 경향이 약하지만 variance가 큽니다. JS divergence는 mode-seeking과 variance 측면에서 중간 정도의 특징을 가집니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: The absolute value of f′superscript𝑓′f^{\prime}italic_f start_POSTSUPERSCRIPT ′ end_POSTSUPERSCRIPT (a) and weighting function h⁢(r)ℎ𝑟h(r)italic_h ( italic_r ) (b) in different f𝑓fitalic_f-divergences.
> </details>



![](https://arxiv.org/html/2502.15681/x5.png)

> 🔼 그림 4(a)는 두 개의 1차원 단위 분산 가우스 분포 사이의 평균 차이에 따른 정규화된 분산을 보여줍니다. 제시된 그래프는 전방 KL 발산과 제프리스 발산의 분산이 가우스 분포 간의 평균 차이가 증가함에 따라 현저하게 증가하는 반면, 젠슨-섀넌 발산과 제곱 헬링거 발산은 비교적 안정적인 것을 보여줍니다. 이러한 안정성은 실험 섹션에서 젠슨-섀넌 발산이 우수한 실험 성능을 달성하는 데 기여합니다.
> <details>
> <summary>read the caption</summary>
> (a)
> </details>



![](https://arxiv.org/html/2502.15681/x6.png)

> 🔼 그림 (b)는 서로 다른 f-다이버전스의 가중치 함수 h(r)를 보여줍니다. 가중치 함수는 f-다이버전스와 밀도 비율에 따라 결정되며, teacher 분포에서 밀도가 낮은 영역의 점수 차이에 가중치를 낮추는 역할을 합니다. 이는 낮은 밀도 영역에서 teacher의 점수 추정이 부정확할 수 있다는 최근 연구 결과와 일치합니다. 그림은 forward-KL의 가중치 함수가 다른 f-다이버전스에 비해 밀도가 낮은 영역에서 더 낮은 가중치를 부여함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b)
> </details>



![](https://arxiv.org/html/2502.15681/x7.png)

> 🔼 그림 4는 두 가지 가우스 분포 간의 평균 차이에 따른 정규화된 분산과 정규화를 적용한 경우와 적용하지 않은 경우의 forward-KL 손실을 보여줍니다. (a)는 두 가우스 분포의 평균 차이에 따른 정규화된 분산을 보여주는 그래프입니다. 가우스 분포 간의 평균 차이가 클수록 정규화된 분산이 커지는 것을 보여줍니다. (b)는 forward-KL 손실에 대한 학습 곡선이며, 정규화를 적용했을 때와 적용하지 않았을 때의 손실 차이를 보여줍니다. 정규화를 적용한 경우 손실의 변동이 감소하는 것을 확인할 수 있습니다. 이는 정규화 기법이 forward-KL 손실 학습의 안정성을 높이는 데 효과적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: (a) Normalized variance versus the mean difference between two Gaussians. (b) Training losses of forward-KL w/ and w/o normalizations.
> </details>



![](https://arxiv.org/html/2502.15681/x8.png)

> 🔼 그림 (a)는 두 개의 1차원 가우시안 분포 사이의 평균 차이에 따른 정규화된 분산을 보여줍니다.  전방 KL 발산과 제프리스 발산은 두 가우시안의 평균 차이가 커짐에 따라 분산이 크게 증가하지만, 젠슨-섀넌 발산과 제곱 헬링거 발산은 비교적 안정적인 분산을 유지합니다. 이는 훈련 안정성 측면에서 젠슨-섀넌 발산과 제곱 헬링거 발산이 더 유리함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (a)
> </details>



![](https://arxiv.org/html/2502.15681/extracted/6217836/img/vis_2.png)

> 🔼 그림 (b)는 다양한 f-다이버전스에 대한 가중 함수 h(r)의 절대값을 보여줍니다. 가중 함수는 f-다이버전스 최소화를 위한 그래디언트 업데이트에 사용되며, 각 f-다이버전스는 모드 탐색, 포화 및 분산이라는 세 가지 측면에서 서로 다른 특성을 보입니다. 그림은 역방향 KL 다이버전스가 낮은 밀도 영역에서 가중치를 낮게 부여하는 반면, 순방향 KL 다이버전스는 모든 영역에 가중치를 높게 부여하는 것을 보여줍니다.  이는 모드 탐색 및 포화 특성이 f-다이버전스 선택에 어떤 영향을 미치는지 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b)
> </details>



![](https://arxiv.org/html/2502.15681/x9.png)

> 🔼 그림 5는 서로 다른 f-다이버전스에 대한 가중치 함수 h와 점수 차이의 절대값을 보여줍니다. (a)는 CIFAR-10에서 forward-KL, (b)는 ImageNet-64에서 JS, (c)는 Stable Diffusion v1.5에서 JS에 대한 결과입니다.  각 그래프는 6,400개의 생성된 샘플의 점수 차이 순으로 정렬되어 있습니다. 이 그림은 가중치 함수 h가 점수 차이와 반대 방향으로 변하는 경향이 있음을 보여줍니다. 즉, 적은 모드-추구 경향을 가진 f-다이버전스를 사용할 때, f-distill은 교사와 가짜 점수 간의 불일치가 큰 영역(즉, 교사 분포의 저밀도 영역)의 샘플에 더 낮은 가중치를 할당하는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (c)
> </details>



![](https://arxiv.org/html/2502.15681/x10.png)

> 🔼 그림 5는 세 가지 다른 데이터셋(CIFAR-10, ImageNet-64, 그리고 Stable Diffusion v1.5)에서 생성된 6,400개의 샘플에 대한 가중치 함수 h와 점수 차이의 관계를 보여줍니다. 각 그래프는 점수 차이에 따라 정렬된 샘플의 인덱스를 x축으로, 가중치 함수 h를 y축으로 나타냅니다. (a)는 forward-KL divergence를 사용한 CIFAR-10 데이터셋, (b)는 Jensen-Shannon divergence를 사용한 ImageNet-64 데이터셋, (c)는 Jensen-Shannon divergence를 사용한 Stable Diffusion v1.5 데이터셋의 결과를 보여줍니다. 이 그림은 서로 다른 f-divergence가 샘플의 가중치에 어떻게 영향을 미치는지, 그리고 밀도가 낮은 영역에서 점수 차이가 큰 샘플에 대한 가중치가 어떻게 조정되는지를 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Normalized weighting function hℎhitalic_h and score difference versus the index of 6.4k generated samples, sorted by the score difference, on (a) CIFAR-10 with forward-KL; (b) ImageNet-64 with JS; (c) SDv1.5 with JS.
> </details>



![](https://arxiv.org/html/2502.15681/extracted/6217836/img/teaser_4.png)

> 🔼 그림 6은 f-distill을 이용한 1단계 생성 모델과 다단계 teacher 확산 모델이 생성한 샘플을 보여줍니다. (a)는 ImageNet-64 및 Stable Diffusion v1.5에 대해 각각 35단계와 50단계를 사용하는 teacher 모델과 동일한 난수 시드를 사용하여 생성된 샘플을 보여줍니다. (b)는 COYO 데이터셋의 프롬프트 '파란색과 흰색의 여객 열차가 정차하는 모습'을 사용하여 reverse-KL과 JS를 이용하여 생성된 샘플을 비교합니다.  f-distill 모델은 다단계 teacher 모델보다 빠르고 효율적인 이미지 생성을 가능하게 합니다.  두 가지 방법의 비교를 통해 f-distill의 성능과 다양한 f-divergence 사용의 효과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: (a) Uncurated generated samples by the multi-step teacher diffusion models (top), and one-step student in f𝑓fitalic_f-distill (bottom), using the same random seed. The teacher diffusion models use 35 and 50 steps on ImageNet-64 and Stable Diffusion v1.5, respectively. (b) Generated samples by reverse-KL and JS, using a prompt in COYO: “a blue and white passenger train coming to a stop”.
> </details>



![](https://arxiv.org/html/2502.15681/x11.png)

> 🔼 그림 4(a)는 두 개의 단위 분산 가우스 분포 간의 평균 차이에 따른 정규화된 분산을 보여줍니다.  정규화된 분산은 두 가우스 분포 간의 차이가 커질수록 전방 KL 발산과 제프리스 발산의 경우 크게 증가하지만, 젠슨-섀넌 발산과 제곱 헬링거 발산은 상대적으로 안정적인 것을 보여줍니다. 이는 낮은 분산을 가진 젠슨-섀넌 발산이 실험에서 우수한 성능을 보이는 이유를 설명합니다.
> <details>
> <summary>read the caption</summary>
> (a)
> </details>



![](https://arxiv.org/html/2502.15681/extracted/6217836/img/cp1.png)

> 🔼 그림 (b)는 서로 다른 f-다이버전스의 가중치 함수 h(r)의 절대값을 보여줍니다. 가중치 함수는 f-다이버전스의 2차 도함수와 확률 밀도비의 제곱의 곱으로 정의되며, 학습 과정에서 티처와 학생 분포 간의 차이를 조정하는 역할을 합니다. 그림에서는 역방향 KL 다이버전스의 경우 가중치 함수가 일정한 반면, 다른 f-다이버전스, 예를 들어 제곱 헬링거나 JS 다이버전스의 경우 가중치 함수가 증가하는 것을 볼 수 있습니다. 이는 가중치 함수가 밀도비가 클 때 더 큰 가중치를 부여하여 밀도가 낮은 영역의 영향을 줄이고, 학습의 안정성을 높이는 것을 시사합니다.  이는 모드 찾기에 덜 집중적인 f-다이버전스가 밀도가 낮은 영역에 대한 점수 차이를 줄이는 경향을 반영합니다.
> <details>
> <summary>read the caption</summary>
> (b)
> </details>



![](https://arxiv.org/html/2502.15681/extracted/6217836/img/cp2.png)

> 🔼 그림 7은 CIFAR-10 데이터셋에서 f-distill의 학습 과정 동안 FID 점수 변화를 보여줍니다. 세 가지 다른 설정을 비교합니다: 1) 가짜 점수(fake score)를 추출기(extractor)로 사용하고 GAN 판별자 손실에서 가짜 점수와 분류 헤드(classification head)를 모두 업데이트하는 경우, 2) 실제 점수(teacher score)를 추출기로 사용하고 GAN 판별자 손실에서 분류 헤드만 업데이트하는 경우, 3) 가짜 점수를 추출기로 사용하고 GAN 판별자 손실에서 분류 헤드만 업데이트하는 경우입니다. (a)는 (b)의 확대된 이미지입니다.  이를 통해 세 가지 설정에서의 FID 점수 변화 양상과 학습 안정성을 비교 분석하여 최적의 설정을 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: FID score versus training iteration on CIFAR-10. Fake score feature: fake score as the extractor, updating both the fake score and classification head in the GAN discriminator loss. Teacher score feature: teacher score as the extractor, updating classification head in the GAN discriminator loss. Teacher score feature, updating cls head: fake score as the extractor, updating classification head in the GAN discriminator loss. (a) is the zoomed-in visualization of (b).
> </details>



![](https://arxiv.org/html/2502.15681/extracted/6217836/img/cp3.png)

> 🔼 그림 8은 가중치 함수 h(빨간 점선)가 모드 탐색 분포(역 KL, h=1)와 비교하여 모드 탐색이 적은 분포(순방향 KL, h=p/q)에서 참 데이터 분포 p를 학습하는 데 어떻게 도움이 되는지 보여줍니다. 모드 탐색이 적은 분포를 사용하면 초기 생성 분포 q가 치우쳐져 있더라도 가중치 함수의 도움으로 다양한 모드를 더 잘 포착할 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Illustration of how the weighting function hℎhitalic_h (red dotted line) in less mode-seeking divergence (forward-KL, h=p/qℎ𝑝𝑞h=p/qitalic_h = italic_p / italic_q) helps to learn the true data distribution p𝑝pitalic_p, compared to more mode-seeking divergence (reverse-KL, h≡1ℎ1h\equiv 1italic_h ≡ 1). We illustrate how using a less mode-seeking divergence can better capture different modes, from a skewed initial generative distribution q𝑞qitalic_q, with the help of the weighting function.
> </details>



![](https://arxiv.org/html/2502.15681/extracted/6217836/img/cp4.png)

> 🔼 그림 9는 COYO-700M 데이터셋에서 Jensen-Shannon(JS) divergence와 forward-KL divergence의 학습 역학을 보여줍니다.  두 divergence 모두 생성 모델 학습에 사용되는데,  그림은 학습 과정 동안 손실 함수 값의 변화를 시각적으로 나타냅니다.  JS divergence와 forward-KL divergence의 손실 함수 값의 변화 패턴을 비교하여 각 divergence의 학습 안정성 및 효율성을 시각적으로 파악할 수 있습니다.  이를 통해 어떤 divergence가 COYO-700M 데이터셋에서 더 나은 성능을 보이는지, 학습 과정에서 어떤 차이점이 있는지를 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Training dynamics of JS and forward-KL on COYO-700M.
> </details>



![](https://arxiv.org/html/2502.15681/extracted/6217836/img/cp5.png)

> 🔼 그림 10은 다단계 확산 모델(teacher)과 단일 단계 생성 모델(student)에서 동일한 프롬프트와 랜덤 시드를 사용하여 생성된 샘플들을 보여줍니다. GAN 목적 함수를 위해 사용된 실제 데이터는 COYO-700M 데이터셋에서 가져왔습니다. 그림에는 teacher 모델과 student 모델의 결과를 비교하여 각 모델의 성능 차이를 시각적으로 보여줍니다.  teacher 모델은 여러 단계의 반복적인 과정을 통해 이미지를 생성하지만, student 모델은 단 한 단계의 처리만으로 이미지를 생성합니다. 이는 student 모델이 teacher 모델의 지식을 효율적으로 학습하여 빠른 이미지 생성 속도를 달성했음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Generated samples from multi-step teachers and single-step students, using the same prompts and random seeds. The real data used for GAN objective are from COYO-700M.
> </details>



![](https://arxiv.org/html/2502.15681/extracted/6217836/img/cp6.png)

> 🔼 그림 11은 다단계 확산 모델(teacher)과 단일 단계 생성 모델(student)에서 동일한 프롬프트와 랜덤 시드를 사용하여 생성한 샘플들을 보여줍니다. GAN 목적 함수에 사용된 실제 데이터는 COYO-700M 데이터셋에서 가져왔습니다.  각 열은 teacher 모델(50단계)과 student 모델(1단계)에서 생성된 이미지를 보여주며, 각 행은 다른 프롬프트에 해당합니다.  이 그림은 teacher 모델의 다단계 생성 과정을 단일 단계로 효과적으로 증류할 수 있는 f-distill 방법의 성능을 시각적으로 보여주기 위해 제시되었습니다.  각 이미지의 시각적 유사성을 비교함으로써, f-distill이 teacher 모델의 이미지 품질과 다양성을 잘 유지하면서 단일 단계로 생성하는 데 성공했음을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Generated samples from multi-step teachers and single-step students, using the same prompts and random seeds. The real data used for GAN objective are from COYO-700M.
> </details>



![](https://arxiv.org/html/2502.15681/extracted/6217836/img/cifar10_edm.png)

> 🔼 이 그림은 다양한 프롬프트와 동일한 랜덤 시드를 사용하여 다단계 티처 모델과 단일 단계 학생 모델에서 생성된 샘플들을 보여줍니다. GAN 목적 함수를 위해 사용된 실제 데이터는 COYO-700M에서 가져왔습니다.  단일 단계 모델은 제안된 f-distill 방법을 사용하여 훈련되었으며, 다양한 f-다이버전스를 사용한 결과를 비교 분석합니다. 그림은 티처 모델과 비교하여 단일 단계 모델의 성능과 다양성을 시각적으로 보여주는 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Generated samples from multi-step teachers and single-step students, using the same prompts and random seeds. The real data used for GAN objective are from COYO-700M.
> </details>



![](https://arxiv.org/html/2502.15681/extracted/6217836/img/cifar10_kl.png)

> 🔼 그림 13은 EDM [17]이라는 다단계 확산 모델을 사용하여 생성한 CIFAR-10 데이터셋의 이미지 샘플 64개를 보여줍니다. 이 이미지들은 35단계의 확산 과정을 거쳐 생성되었으며, FID(Fréchet Inception Distance) 점수는 1.79입니다. FID 점수는 생성된 이미지의 품질을 나타내는 지표로, 점수가 낮을수록 실제 데이터와 유사한 고품질 이미지를 생성했다는 것을 의미합니다.  이 그림은 논문의 실험 결과 부분에서, 제안된 단일 단계 확산 모델의 성능을 다단계 모델과 비교하기 위해 사용되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: 35-step generated CIFAR-10 samples, by EDM [17] (teacher). FID score: 1.79
> </details>



![](https://arxiv.org/html/2502.15681/extracted/6217836/img/imagenet_64_edm.png)

> 🔼 그림 14는 본 논문에서 제안하는 f-distill 방법을 사용하여 역방향 KL divergence를 최소화함으로써 생성된 CIFAR-10 이미지 샘플들을 보여줍니다.  이 그림은 한 단계(one-step) 생성 과정을 통해 얻어진 결과이며, FID(Fréchet Inception Distance) 점수는 1.92로, 이미지 품질을 정량적으로 평가합니다. 낮은 FID 점수는 생성된 이미지들이 실제 CIFAR-10 데이터셋과 유사하다는 것을 나타냅니다. 이는 f-distill이 효과적으로 이미지 생성을 수행함을 시각적으로 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: One-step generated CIFAR-10 samples, by KL in f𝑓fitalic_f-distill. FID score: 1.92
> </details>



![](https://arxiv.org/html/2502.15681/extracted/6217836/img/imagenet_64_js.png)

> 🔼 그림 15는 EDM [17]이라는 다단계 확산 모델을 사용하여 생성된 ImageNet-64 데이터셋의 샘플들을 보여줍니다.  총 79단계의 확산 과정을 거쳐 생성되었으며, FID(Fréchet Inception Distance) 점수는 2.35로 나타났습니다. 이 그림은 논문의 실험 결과를 보여주는 부분으로,  EDM 모델의 성능을 시각적으로 보여주고,  다음 섹션에서 소개될  f-distill 모델과의 성능 비교를 위한 기준점을 제공합니다.  ImageNet-64는 64x64 크기의 이미지로 구성된 대규모 이미지 데이터셋이며,  FID 점수는 이미지 생성 모델의 성능을 평가하는 지표 중 하나입니다. 낮은 FID 점수일수록 실제 이미지와 유사한 이미지를 생성하는 모델임을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Figure 15: 79-step generated ImageNet-64 samples, by EDM [17] (teacher). FID score: 2.35
> </details>



![](https://arxiv.org/html/2502.15681/extracted/6217836/img/sd_teacher.png)

> 🔼 그림 16은 제안된 f-distill 방법을 사용하여 Jensen-Shannon(JS) divergence를 최소화함으로써 생성된 ImageNet-64 데이터셋의 이미지들을 보여줍니다.  이 이미지들은 단 한 번의 네트워크 연산만으로 생성되었으며, FID(Fréchet Inception Distance) 점수가 1.16으로 매우 높은 화질을 보여줍니다. 이는 단일 단계 생성 모델의 성능이 다단계 확산 모델과 유사하거나 심지어 능가할 수 있음을 시사합니다. 그림은 다양한 물체와 배경을 가진 이미지들의 다양성을 보여주어, 모델의 높은 생성 품질과 다양성을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 16: One-step generated ImageNet-64 samples, by JS in f𝑓fitalic_f-distill. FID score: 1.16
> </details>



![](https://arxiv.org/html/2502.15681/extracted/6217836/img/sd_js.png)

> 🔼 그림 17은 50단계 확산 모델(SD v1.5)을 사용하여 COYO-700M 데이터셋에서 무작위로 선택된 프롬프트로 생성한 이미지 샘플들을 보여줍니다.  CFG(Classifier-Free Guidance) 값은 3으로 설정되었고,  FID(Fréchet Inception Distance) 점수는 8.59입니다.  이 그림은 논문의 실험 결과 부분에서,  단일 단계 생성 모델의 성능을 평가하기 위한 기준으로 사용된 다단계 확산 모델의 출력 결과를 보여주는 예시입니다.  즉,  단일 단계 모델과 비교를 위해 다단계 모델이 생성한 이미지의 질을 보여주는 것입니다.
> <details>
> <summary>read the caption</summary>
> Figure 17: 50-step generated SD v1.5 samples, using randomly sampled COYO-700M prompts, by SD v1.5 model [43] (teacher). CFG=3. FID score: 8.59
> </details>



![](https://arxiv.org/html/2502.15681/extracted/6217836/img/step_36000.png)

> 🔼 그림 18은 제안된 f-distill 방법을 사용하여 생성된 이미지를 보여줍니다.  구체적으로,  Jensen-Shannon(JS) f-divergence를 사용하여 사전 훈련된 Stable Diffusion v1.5 모델을 단일 단계 생성기로 증류했습니다.  COYO-700M 데이터셋에서 무작위로 선택된 프롬프트를 사용하여 생성되었으며, Classifier-Free Guidance (CFG) 값은 1.75로 설정되었습니다.  이 그림은 생성된 이미지의 다양성과 품질을 보여주며,  Fréchet Inception Distance (FID) 점수는 7.42로 측정되었습니다. 낮은 FID 점수는 생성된 이미지의 품질이 높다는 것을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 18: One-step generated SD v1.5 samples, using randomly sampled COYO-700M prompts, by JS in f𝑓fitalic_f-distill, with CFG=1.75. FID score: 7.42
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| FID ↓ | Recall ↑ |
|---|---|---| 
| EDM [17](https://arxiv.org/html/2502.15681/bib17.png) (NFE=35) | 1.79 | 0.63 |
| **Diffusion distillation** |  |  |
| Adversarial distillation | 2.60 |  |
| SiD [82](https://arxiv.org/html/2502.15681/bib82.png) | 1.71 |  |
| CTM [19](https://arxiv.org/html/2502.15681/bib19.png) | 1.73 |  |
| GDD-I [79](https://arxiv.org/html/2502.15681/bib79.png) | 1.44 |  |
| **f-distill** |  |  |
| reverse-KL (✓, DMD2 [71](https://arxiv.org/html/2502.15681/bib71.png)) | 2.13 | 0.60 |
| softened RKL (✓) | 2.21 | 0.60 |
| squared Hellinger (–) | 1.99 | 0.63 |
| JS (–) | 2.00 | 0.62 |
| Jeffreys (✗) | 2.05 | 0.62 |
| forward-KL (✗) | 1.92 | 0.62 |{{< /table-caption >}}
> 🔼 표 2는 CIFAR-10 데이터셋에서 다양한 f-다이버전스를 사용한 f-distill 방법과 기존의 방법들의 FID(Fréchet Inception Distance) 점수와 재현율 점수를 비교한 표입니다.  f-다이버전스의 모드 추구 경향(mode-seeking tendency)을  ✓(높음), –(중간), ✗(낮음)으로 표시하여, 모드 추구 경향이 결과에 미치는 영향을 분석하고 있습니다.  단일 단계 생성 모델(one-step generator)의 성능을 평가하는 지표로 FID 점수와 재현율 점수를 사용했습니다. FID 점수는 낮을수록 좋고, 재현율 점수는 높을수록 좋습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: FID and Recall scores on CIFAR-10. ✓/–/✗ stand for high/medium/low mode-seeking tendency for f𝑓fitalic_f-divergence.
> </details>

{{< table-caption >}}
| Model                     | FID ↓ | Recall ↑ | NFE |
|------------------------------|-------|----------|------|
| **Multi-step diffusion models** |       |          |      |
| EDM [17]                     | 2.35  | 0.68     | 79   |
| RIN [14]                     | 1.23  |          | 1000 |
| DisCo-Diff [69]              | 1.22  |          | 623  |
| **GANs**                      |       |          |      |
| BigGAN-deep [3]              | 4.06  | 0.48     | 1    |
| StyleGAN-XL [48]             | 1.52  |          | 1    |
| **Diffusion distillation**     |       |          |      |
| DSNO [80]                    | 7.83  | 0.61     | 1    |
| Diff-Instruct [33]           | 5.57  |          | 1    |
| iCT [55]                     | 4.02  | 0.63     | 1    |
| iCT-deep [55]                | 3.25  | 0.63     | 1    |
| Moment Matching [47]         | 3.00  |          | 1    |
| DMD [72]                     | 2.62  |          | 1    |
| ECM [9]                      | 2.49  |          | 1    |
| TCM [23]                     | 2.20  |          | 1    |
| EMD [66]                     | 2.20  | 0.59     | 1    |
| CTM [20]                     | 1.92  | 0.57     | 1    |
| Adversarial distillation     | 1.88  |          | 1    |
| SiD [82]                     | 1.52  | 0.63     | 1    |
| GDD [79]                     | 1.42  | 0.59     | 1    |
| GDD-I [79]                   | 1.16  | 0.60     | 1    |
| 1-4                           |       |          |      |
| f-distill                    |       |          |      |
| reverse-KL (DMD2 [71])       | 1.27  | 0.65     | 1    |
| forward-KL (ours)            | 1.21  | 0.65     | 1    |
| JS (ours)                    | **1.16** | **0.66** | 1    |{{< /table-caption >}}
> 🔼 이 표는 ImageNet-64 데이터셋에서 다양한 방법으로 생성된 이미지의 품질과 다양성을 비교 분석한 결과를 보여줍니다.  FID(Fréchet Inception Distance) 점수는 이미지의 품질을, Recall 점수는 이미지의 다양성을, NFE(Network Forward Evaluations)는 이미지 생성에 필요한 네트워크 연산 횟수를 나타냅니다.  표에는 여러 다양한 확산 모델(Multi-step diffusion models)과, 단일 단계 생성 모델을 학습하는 데 사용된 다양한 증류 방법(Diffusion distillation, Adversarial distillation)의 결과가 포함되어 있습니다.  특히, 논문에서 제안하는 f-distill 방법의 성능을 다양한 f-divergence를 사용하여 비교하고, 최첨단 기술(state-of-the-art)과의 비교 분석 결과를 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: FID score, Recall and NFE on ImageNet-64.
> </details>

{{< table-caption >}}
| Model | FID ↓ | CLIP score ↑ | Latency ↓ |
|---|---|---|---| 
| **Multi-step diffusion models** |  |  |  |
| LDM [42] | 12.63 |  | 3.7s |
| DALL·E 2 [40] | 10.39 |  | 27s |
| Imagen [45] | 7.27 | 0.28* | 9.1s |
| eDiff-I [1] | **6.95** | 0.29* | 32.0s |
| UniPC [78] | 19.57 |  | 0.26s |
| Restart [67] | 13.16 | 0.299 | 3.40s |
|  |  |  |  |
| **Teacher** |  |  |  |
| SDv1.5 (NFE=50, CFG=3, ODE) | 8.59 | 0.308 | 2.59s |
| SDv1.5 (NFE=200, CFG=2, SDE) | 7.21 | 0.301 | 10.25s |
|  |  |  |  |
| **GANs** |  |  |  |
| StyleGAN-T [49] | 13.90 | 0.29* | 0.10s |
| GigaGAN [16] | 9.09 |  | 0.13s |
|  |  |  |  |
| **Diffusion distillation** |  |  |  |
| SwiftBrush [36] | 16.67 | 0.29* | 0.09s |
| SwiftBrush v2 [6] | 8.14 | 0.32* | 0.06s |
| HiPA [77] | 13.91 |  | 0.09s |
| InstaFlow-0.9B [27] | 13.10 |  | 0.09s |
| UFOGen [70] | 12.78 |  | 0.09s |
| DMD [72] | 11.49 |  | 0.09s |
| EMD [66] | 9.66 |  | 0.09s |
|  |  |  |  |
| *CFG=1.75* |  |  |  |
| reverse-KL (DMD2 [71]) | 8.17 | 0.287 | 0.09s |
| JS (*ours*) | **7.42** | 0.292 | 0.09s |
|  |  |  |  |
| *CFG=5* |  |  |  |
| reverse-KL (DMD2 [71]) | 15.23 | 0.309 | 0.09s |
| JS (*ours*) | 14.25 | 0.311 | 0.09s |{{< /table-caption >}}
> 🔼 표 4는 제로샷 MS COCO-30k 512x512 데이터셋을 사용한 텍스트-이미지 생성 작업에서 여러 모델들의 성능을 비교한 표입니다. FID(Fréchet Inception Distance) 점수와 추론 지연 시간(Latency)을 나타냅니다. FID 점수는 이미지 생성 품질을 나타내며, 낮을수록 좋습니다. 추론 지연 시간은 이미지 하나를 생성하는 데 걸리는 시간을 나타내며, 짧을수록 좋습니다. 표에는 다양한 기존의 다단계 확산 모델, GAN(Generative Adversarial Network) 모델, 그리고 확산 증류(Diffusion Distillation) 기반 모델들이 포함되어 있으며, 본 논문에서 제안하는 f-distill 모델의 결과도 함께 제시되어 있습니다. * 표시는 해당 값이 해당 논문에서 가져온 값임을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 4: FID score together with inference latency on text-to-image generation, zero-shot MS COCO-30k 512×\times× 512. * denotes that the value is taken from the corresponding paper.
> </details>

{{< table-caption >}}
| Dataset          | CIFAR-10 | ImageNet-64 | COYO-700M |
|-----------------|----------|-------------|-----------|
| Batch size       | 2048     | 512         | 1024      |
| Fake score update frequency | 5         | 5           | 10        |
| GAN loss weight  | 1e-3     | 3e-3        | 1e-3      |
| GAN discriminator input resolution | (32, 16, 8) | (8)         | (8)        |
| Total iteration  | 60K      | 380K        | 60K       |
| Teacher          | EDM [17]  | EDM [17]     | Stable Diffusion v1.5 [43] |
| CFG weight       | 1         | 1           | 1.75      |
| Adam optimizer   |           |             |           |
| Learning rate    | 1e-4     | 2e-6        | 1e-5      |
| Learning rate for fine-tuning | -         | 5e-7        | -         |
| Weight decay     | 1e-2     | 1e-2        | 1e-2      |
| γ in R1 regularization | 1         | 0           | 1        |{{< /table-caption >}}
> 🔼 이 표는 논문의 실험 설정 부분에 있는 표로, 서로 다른 세 개의 데이터셋(CIFAR-10, ImageNet-64, COYO-700M)에서 f-distill 모델을 학습시키는 데 사용된 다양한 하이퍼파라미터 값들을 보여줍니다.  각 데이터셋에 대해 배치 크기, 가짜 점수 네트워크 업데이트 빈도, GAN 손실 가중치, GAN 판별자 입력 해상도, 총 반복 횟수, 티쳐 모델, CFG 가중치, 옵티마이저, 학습률, 가중치 감쇠 등의 하이퍼파라미터 값들을 상세하게 나타냅니다. 이 표는 f-distill 모델의 학습 과정과 성능에 영향을 미치는 다양한 요소들을 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Training configuration for f𝑓fitalic_f-distill on different datasets.
> </details>

{{< table-caption >}}
<table class="ltx_tabular ltx_centering ltx_align_middle" id="A3.T6.14">
<tr class="ltx_tr" id="A3.T6.14.15">
<td class="ltx_td ltx_border_tt" id="A3.T6.14.15.1"></td>
<td class="ltx_td ltx_align_center ltx_border_tt" id="A3.T6.14.15.2">reverse-KL</td>
<td class="ltx_td ltx_align_center ltx_border_tt" id="A3.T6.14.15.3">softened RKL</td>
<td class="ltx_td ltx_align_center ltx_border_tt" id="A3.T6.14.15.4">JS</td>
<td class="ltx_td ltx_align_center ltx_border_tt" id="A3.T6.14.15.5">squared Hellinger</td>
<td class="ltx_td ltx_align_center ltx_border_tt" id="A3.T6.14.15.6">forward-KL</td>
<td class="ltx_td ltx_align_center ltx_border_tt" id="A3.T6.14.15.7">Jefferys</td>
</tr>
<tr class="ltx_tr" id="A3.T6.7.7">
<td class="ltx_td ltx_align_left ltx_border_t" id="A3.T6.1.1.1">Rate of <math alttext="\lim_{r\to\infty}f^{\prime\prime}(r)" class="ltx_Math" display="inline" id="A3.T6.1.1.1.m1.1"><semantics id="A3.T6.1.1.1.m1.1a"><mrow id="A3.T6.1.1.1.m1.1.2" xref="A3.T6.1.1.1.m1.1.2.cmml"><msub id="A3.T6.1.1.1.m1.1.2.1" xref="A3.T6.1.1.1.m1.1.2.1.cmml"><mo id="A3.T6.1.1.1.m1.1.2.1.2" xref="A3.T6.1.1.1.m1.1.2.1.2.cmml">lim</mo><mrow id="A3.T6.1.1.1.m1.1.2.1.3" xref="A3.T6.1.1.1.m1.1.2.1.3.cmml"><mi id="A3.T6.1.1.1.m1.1.2.1.3.2" xref="A3.T6.1.1.1.m1.1.2.1.3.2.cmml">r</mi><mo id="A3.T6.1.1.1.m1.1.2.1.3.1" stretchy="false" xref="A3.T6.1.1.1.m1.1.2.1.3.1.cmml">→</mo><mi id="A3.T6.1.1.1.m1.1.2.1.3.3" mathvariant="normal" xref="A3.T6.1.1.1.m1.1.2.1.3.3.cmml">∞</mi></mrow></msub><mrow id="A3.T6.1.1.1.m1.1.2.2" xref="A3.T6.1.1.1.m1.1.2.2.cmml"><msup id="A3.T6.1.1.1.m1.1.2.2.2" xref="A3.T6.1.1.1.m1.1.2.2.2.cmml"><mi id="A3.T6.1.1.1.m1.1.2.2.2.2" xref="A3.T6.1.1.1.m1.1.2.2.2.2.cmml">f</mi><mo id="A3.T6.1.1.1.m1.1.2.2.2.3" xref="A3.T6.1.1.1.m1.1.2.2.2.3.cmml">′′</mo></msup><mo id="A3.T6.1.1.1.m1.1.2.2.1" xref="A3.T6.1.1.1.m1.1.2.2.1.cmml">⁢</mo><mrow id="A3.T6.1.1.1.m1.1.2.2.3.2" xref="A3.T6.1.1.1.m1.1.2.2.cmml"><mo id="A3.T6.1.1.1.m1.1.2.2.3.2.1" stretchy="false" xref="A3.T6.1.1.1.m1.1.2.2.cmml">(</mo><mi id="A3.T6.1.1.1.m1.1.1" xref="A3.T6.1.1.1.m1.1.1.cmml">r</mi><mo id="A3.T6.1.1.1.m1.1.2.2.3.2.2" stretchy="false" xref="A3.T6.1.1.1.m1.1.2.2.cmml">)</mo></mrow></mrow></mrow><annotation-xml encoding="MathML-Content" id="A3.T6.1.1.1.m1.1b"><apply id="A3.T6.1.1.1.m1.1.2.cmml" xref="A3.T6.1.1.1.m1.1.2"><apply id="A3.T6.1.1.1.m1.1.2.1.cmml" xref="A3.T6.1.1.1.m1.1.2.1"><csymbol cd="ambiguous" id="A3.T6.1.1.1.m1.1.2.1.1.cmml" xref="A3.T6.1.1.1.m1.1.2.1">subscript</csymbol><limit id="A3.T6.1.1.1.m1.1.2.1.2.cmml" xref="A3.T6.1.1.1.m1.1.2.1.2"></limit><apply id="A3.T6.1.1.1.m1.1.2.1.3.cmml" xref="A3.T6.1.1.1.m1.1.2.1.3"><ci id="A3.T6.1.1.1.m1.1.2.1.3.1.cmml" xref="A3.T6.1.1.1.m1.1.2.1.3.1">→</ci><ci id="A3.T6.1.1.1.m1.1.2.1.3.2.cmml" xref="A3.T6.1.1.1.m1.1.2.1.3.2">𝑟</ci><infinity id="A3.T6.1.1.1.m1.1.2.1.3.3.cmml" xref="A3.T6.1.1.1.m1.1.2.1.3.3"></infinity></apply></apply><apply id="A3.T6.1.1.1.m1.1.2.2.cmml" xref="A3.T6.1.1.1.m1.1.2.2"><times id="A3.T6.1.1.1.m1.1.2.2.1.cmml" xref="A3.T6.1.1.1.m1.1.2.2.1"></times><apply id="A3.T6.1.1.1.m1.1.2.2.2.cmml" xref="A3.T6.1.1.1.m1.1.2.2.2"><csymbol cd="ambiguous" id="A3.T6.1.1.1.m1.1.2.2.2.1.cmml" xref="A3.T6.1.1.1.m1.1.2.2.2">superscript</csymbol><ci id="A3.T6.1.1.1.m1.1.2.2.2.2.cmml" xref="A3.T6.1.1.1.m1.1.2.2.2.2">𝑓</ci><ci id="A3.T6.1.1.1.m1.1.2.2.2.3.cmml" xref="A3.T6.1.1.1.m1.1.2.2.2.3">′′</ci></apply><ci id="A3.T6.1.1.1.m1.1.1.cmml" xref="A3.T6.1.1.1.m1.1.1">𝑟</ci></apply></apply></annotation-xml><annotation encoding="application/x-tex" id="A3.T6.1.1.1.m1.1c">\lim_{r\to\infty}f^{\prime\prime}(r)</annotation><annotation encoding="application/x-llamapun" id="A3.T6.1.1.1.m1.1d">roman_lim start_POSTSUBSCRIPT italic_r → ∞ end_POSTSUBSCRIPT italic_f start_POSTSUPERSCRIPT ′ ′ end_POSTSUPERSCRIPT ( italic_r )</annotation></semantics></math>
</td>
<td class="ltx_td ltx_align_center ltx_border_t" id="A3.T6.2.2.2"><math alttext="{\mathcal{O}}(r^{-2})" class="ltx_Math" display="inline" id="A3.T6.2.2.2.m1.1"><semantics id="A3.T6.2.2.2.m1.1a"><mrow id="A3.T6.2.2.2.m1.1.1" xref="A3.T6.2.2.2.m1.1.1.cmml"><mi class="ltx_font_mathcaligraphic" id="A3.T6.2.2.2.m1.1.1.3" xref="A3.T6.2.2.2.m1.1.1.3.cmml">𝒪</mi><mo id="A3.T6.2.2.2.m1.1.1.2" xref="A3.T6.2.2.2.m1.1.1.2.cmml">⁢</mo><mrow id="A3.T6.2.2.2.m1.1.1.1.1" xref="A3.T6.2.2.2.m1.1.1.1.1.1.cmml"><mo id="A3.T6.2.2.2.m1.1.1.1.1.2" stretchy="false" xref="A3.T6.2.2.2.m1.1.1.1.1.1.cmml">(</mo><msup id="A3.T6.2.2.2.m1.1.1.1.1.1" xref="A3.T6.2.2.2.m1.1.1.1.1.1.cmml"><mi id="A3.T6.2.2.2.m1.1.1.1.1.1.2" xref="A3.T6.2.2.2.m1.1.1.1.1.1.2.cmml">r</mi><mrow id="A3.T6.2.2.2.m1.1.1.1.1.1.3" xref="A3.T6.2.2.2.m1.1.1.1.1.1.3.cmml"><mo id="A3.T6.2.2.2.m1.1.1.1.1.1.3a" xref="A3.T6.2.2.2.m1.1.1.1.1.1.3.cmml">−</mo><mn id="A3.T6.2.2.2.m1.1.1.1.1.1.3.2" xref="A3.T6.2.2.2.m1.1.1.1.1.1.3.2.cmml">2</mn></mrow></msup><mo id="A3.T6.2.2.2.m1.1.1.1.1.3" stretchy="false" xref="A3.T6.2.2.2.m1.1.1.1.1.1.cmml">)</mo></mrow></mrow><annotation-xml encoding="MathML-Content" id="A3.T6.2.2.2.m1.1b"><apply id="A3.T6.2.2.2.m1.1.1.cmml" xref="A3.T6.2.2.2.m1.1.1"><times id="A3.T6.2.2.2.m1.1.1.2.cmml" xref="A3.T6.2.2.2.m1.1.1.2"></times><ci id="A3.T6.2.2.2.m1.1.1.3.cmml" xref="A3.T6.2.2.2.m1.1.1.3">𝒪</ci><apply id="A3.T6.2.2.2.m1.1.1.1.1.1.cmml" xref="A3.T6.2.2.2.m1.1.1.1.1"><csymbol cd="ambiguous" id="A3.T6.2.2.2.m1.1.1.1.1.1.1.cmml" xref="A3.T6.2.2.2.m1.1.1.1.1">superscript</csymbol><ci id="A3.T6.2.2.2.m1.1.1.1.1.1.2.cmml" xref="A3.T6.2.2.2.m1.1.1.1.1.1.2">𝑟</ci><apply id="A3.T6.2.2.2.m1.1.1.1.1.1.3.cmml" xref="A3.T6.2.2.2.m1.1.1.1.1.1.3"><minus id="A3.T6.2.2.2.m1.1.1.1.1.1.3.1.cmml" xref="A3.T6.2.2.2.m1.1.1.1.1.1.3"></minus><cn id="A3.T6.2.2.2.m1.1.1.1.1.1.3.2.cmml" type="integer" xref="A3.T6.2.2.2.m1.1.1.1.1.1.3.2">2</cn></apply></apply></apply></annotation-xml><annotation encoding="application/x-tex" id="A3.T6.2.2.2.m1.1c">{\mathcal{O}}(r^{-2})</annotation><annotation encoding="application/x-llamapun" id="A3.T6.2.2.2.m1.1d">caligraphic_O ( italic_r start_POSTSUPERSCRIPT - 2 end_POSTSUPERSCRIPT )</annotation></semantics></math></td>
<td class="ltx_td ltx_align_center ltx_border_t" id="A3.T6.3.3.3"><math alttext="{\mathcal{O}}(r^{-3})" class="ltx_Math" display="inline" id="A3.T6.3.3.3.m1.1"><semantics id="A3.T6.3.3.3.m1.1a"><mrow id="A3.T6.3.3.3.m1.1.1" xref="A3.T6.3.3.3.m1.1.1.cmml"><mi class="ltx_font_mathcaligraphic" id="A3.T6.3.3.3.m1.1.1.3" xref="A3.T6.3.3.3.m1.1.1.3.cmml">𝒪</mi><mo id="A3.T6.3.3.3.m1.1.1.2" xref="A3.T6.3.3.3.m1.1.1.2.cmml">⁢</mo><mrow id="A3.T6.3.3.3.m1.1.1.1.1" xref="A3.T6.3.3.3.m1.1.1.1.1.1.cmml"><mo id="A3.T6.3.3.3.m1.1.1.1.1.2" stretchy="false" xref="A3.T6.3.3.3.m1.1.1.1.1.1.cmml">(</mo><msup id="A3.T6.3.3.3.m1.1.1.1.1.1" xref="A3.T6.3.3.3.m1.1.1.1.1.1.cmml"><mi id="A3.T6.3.3.3.m1.1.1.1.1.1.2" xref="A3.T6.3.3.3.m1.1.1.1.1.1.2.cmml">r</mi><mrow id="A3.T6.3.3.3.m1.1.1.1.1.1.3" xref="A3.T6.3.3.3.m1.1.1.1.1.1.3.cmml"><mo id="A3.T6.3.3.3.m1.1.1.1.1.1.3a" xref="A3.T6.3.3.3.m1.1.1.1.1.1.3.cmml">−</mo><mn id="A3.T6.3.3.3.m1.1.1.1.1.1.3.2" xref="A3.T6.3.3.3.m1.1.1.1.1.1.3.2.cmml">3</mn></mrow></msup><mo id="A3.T6.3.3.3.m1.1.1.1.1.3" stretchy="false" xref="A3.T6.3.3.3.m1.1.1.1.1.1.cmml">)</mo></mrow></mrow><annotation-xml encoding="MathML-Content" id="A3.T6.3.3.3.m1.1b"><apply id="A3.T6.3.3.3.m1.1.1.cmml" xref="A3.T6.3.3.3.m1.1.1"><times id="A3.T6.3.3.3.m1.1.1.2.cmml" xref="A3.T6.3.3.3.m1.1.1.2"></times><ci id="A3.T6.3.3.3.m1.1.1.3.cmml" xref="A3.T6.3.3.3.m1.1.1.3">𝒪</ci><apply id="A3.T6.3.3.3.m1.1.1.1.1.1.cmml" xref="A3.T6.3.3.3.m1.1.1.1.1"><csymbol cd="ambiguous" id="A3.T6.3.3.3.m1.1.1.1.1.1.1.cmml" xref="A3.T6.3.3.3.m1.1.1.1.1">superscript</csymbol><ci id="A3.T6.3.3.3.m1.1.1.1.1.1.2.cmml" xref="A3.T6.3.3.3.m1.1.1.1.1.1.2">𝑟</ci><apply id="A3.T6.3.3.3.m1.1.1.1.1.1.3.cmml" xref="A3.T6.3.3.3.m1.1.1.1.1.1.3"><minus id="A3.T6.3.3.3.m1.1.1.1.1.1.3.1.cmml" xref="A3.T6.3.3.3.m1.1.1.1.1.1.3"></minus><cn id="A3.T6.3.3.3.m1.1.1.1.1.1.3.2.cmml" type="integer" xref="A3.T6.3.3.3.m1.1.1.1.1.1.3.2">3</cn></apply></apply></apply></annotation-xml><annotation encoding="application/x-tex" id="A3.T6.3.3.3.m1.1c">{\mathcal{O}}(r^{-3})</annotation><annotation encoding="application/x-llamapun" id="A3.T6.3.3.3.m1.1d">caligraphic_O ( italic_r start_POSTSUPERSCRIPT - 3 end_POSTSUPERSCRIPT )</annotation></semantics></math></td>
<td class="ltx_td ltx_align_center ltx_border_t" id="A3.T6.4.4.4"><math alttext="{\mathcal{O}}(r^{-2})" class="ltx_Math" display="inline" id="A3.T6.4.4.4.m1.1"><semantics id="A3.T6.4.4.4.m1.1a"><mrow id="A3.T6.4.4.4.m1.1.1" xref="A3.T6.4.4.4.m1.1.1.cmml"><mi class="ltx_font_mathcaligraphic" id="A3.T6.4.4.4.m1.1.1.3" xref="A3.T6.4.4.4.m1.1.1.3.cmml">𝒪</mi><mo id="A3.T6.4.4.4.m1.1.1.2" xref="A3.T6.4.4.4.m1.1.1.2.cmml">⁢</mo><mrow id="A3.T6.4.4.4.m1.1.1.1.1" xref="A3.T6.4.4.4.m1.1.1.1.1.1.cmml"><mo id="A3.T6.4.4.4.m1.1.1.1.1.2" stretchy="false" xref="A3.T6.4.4.4.m1.1.1.1.1.1.cmml">(</mo><msup id="A3.T6.4.4.4.m1.1.1.1.1.1" xref="A3.T6.4.4.4.m1.1.1.1.1.1.cmml"><mi id="A3.T6.4.4.4.m1.1.1.1.1.1.2" xref="A3.T6.4.4.4.m1.1.1.1.1.1.2.cmml">r</mi><mrow id="A3.T6.4.4.4.m1.1.1.1.1.1.3" xref="A3.T6.4.4.4.m1.1.1.1.1.1.3.cmml"><mo id="A3.T6.4.4.4.m1.1.1.1.1.1.3a" xref="A3.T6.4.4.4.m1.1.1.1.1.1.3.cmml">−</mo><mn id="A3.T6.4.4.4.m1.1.1.1.1.1.3.2" xref="A3.T6.4.4.4.m1.1.1.1.1.1.3.2.cmml">2</mn></mrow></msup><mo id="A3.T6.4.4.4.m1.1.1.1.1.3" stretchy="false" xref="A3.T6.4.4.4.m1.1.1.1.1.1.cmml">)</mo></mrow></mrow><annotation-xml encoding="MathML-Content" id="A3.T6.4.4.4.m1.1b"><apply id="A3.T6.4.4.4.m1.1.1.cmml" xref="A3.T6.4.4.4.m1.1.1"><times id="A3.T6.4.4.4.m1.1.1.2.cmml" xref="A3.T6.4.4.4.m1.1.1.2"></times><ci id="A3.T6.4.4.4.m1.1.1.3.cmml" xref="A3.T6.4.4.4.m1.1.1.3">𝒪</ci><apply id="A3.T6.4.4.4.m1.1.1.1.1.1.cmml" xref="A3.T6.4.4.4.m1.1.1.1.1"><csymbol cd="ambiguous" id="A3.T6.4.4.4.m1.1.1.1.1.1.1.cmml" xref="A3.T6.4.4.4.m1.1.1.1.1">superscript</csymbol><ci id="A3.T6.4.4.4.m1.1.1.1.1.1.2.cmml" xref="A3.T6.4.4.4.m1.1.1.1.1.1.2">𝑟</ci><apply id="A3.T6.4.4.4.m1.1.1.1.1.1.3.cmml" xref="A3.T6.4.4.4.m1.1.1.1.1.1.3"><minus id="A3.T6.4.4.4.m1.1.1.1.1.1.3.1.cmml" xref="A3.T6.4.4.4.m1.1.1.1.1.1.3"></minus><cn id="A3.T6.4.4.4.m1.1.1.1.1.1.3.2.cmml" type="integer" xref="A3.T6.4.4.4.m1.1.1.1.1.1.3.2">2</cn></apply></apply></apply></annotation-xml><annotation encoding="application/x-tex" id="A3.T6.4.4.4.m1.1c">{\mathcal{O}}(r^{-2})</annotation><annotation encoding="application/x-llamapun" id="A3.T6.4.4.4.m1.1d">caligraphic_O ( italic_r start_POSTSUPERSCRIPT - 2 end_POSTSUPERSCRIPT )</annotation></semantics></math></td>
<td class="ltx_td ltx_align_center ltx_border_t" id="A3.T6.5.5.5"><math alttext="{\mathcal{O}}(r^{-\frac{3}{2}})" class="ltx_Math" display="inline" id="A3.T6.5.5.5.m1.1"><semantics id="A3.T6.5.5.5.m1.1a"><mrow id="A3.T6.5.5.5.m1.1.1" xref="A3.T6.5.5.5.m1.1.1.cmml"><mi class="ltx_font_mathcaligraphic" id="A3.T6.5.5.5.m1.1.1.3" xref="A3.T6.5.5.5.m1.1.1.3.cmml">𝒪</mi><mo id="A3.T6.5.5.5.m1.1.1.2" xref="A3.T6.5.5.5.m1.1.1.2.cmml">⁢</mo><mrow id="A3.T6.5.5.5.m1.1.1.1.1" xref="A3.T6.5.5.5.m1.1.1.1.1.1.cmml"><mo id="A3.T6.5.5.5.m1.1.1.1.1.2" stretchy="false" xref="A3.T6.5.5.5.m1.1.1.1.1.1.cmml">(</mo><msup id="A3.T6.5.5.5.m1.1.1.1.1.1" xref="A3.T6.5.5.5.m1.1.1.1.1.1.cmml"><mi id="A3.T6.5.5.5.m1.1.1.1.1.1.2" xref="A3.T6.5.5.5.m1.1.1.1.1.1.2.cmml">r</mi><mrow id="A3.T6.5.5.5.m1.1.1.1.1.1.3" xref="A3.T6.5.5.5.m1.1.1.1.1.1.3.cmml"><mo id="A3.T6.5.5.5.m1.1.1.1.1.1.3a" xref="A3.T6.5.5.5.m1.1.1.1.1.1.3.cmml">−</mo><mfrac id="A3.T6.5.5.5.m1.1.1.1.1.1.3.2" xref="A3.T6.5.5.5.m1.1.1.1.1.1.3.2.cmml"><mn id="A3.T6.5.5.5.m1.1.1.1.1.1.3.2.2" xref="A3.T6.5.5.5.m1.1.1.1.1.1.3.2.2.cmml">3</mn><mn id="A3.T6.5.5.5.m1.1.1.1.1.1.3.2.3" xref="A3.T6.5.5.5.m1.1.1.1.1.1.3.2.3.cmml">2</mn></mfrac></mrow></msup><mo id="A3.T6.5.5.5.m1.1.1.1.1.3" stretchy="false" xref="A3.T6.5.5.5.m1.1.1.1.1.1.cmml">)</mo></mrow></mrow><annotation-xml encoding="MathML-Content" id="A3.T6.5.5.5.m1.1b"><apply id="A3.T6.5.5.5.m1.1.1.cmml" xref="A3.T6.5.5.5.m1.1.1"><times id="A3.T6.5.5.5.m1.1.1.2.cmml" xref="A3.T6.5.5.5.m1.1.1.2"></times><ci id="A3.T6.5.5.5.m1.1.1.3.cmml" xref="A3.T6.5.5.5.m1.1.1.3">𝒪</ci><apply id="A3.T6.5.5.5.m1.1.1.1.1.1.cmml" xref="A3.T6.5.5.5.m1.1.1.1.1"><csymbol cd="ambiguous" id="A3.T6.5.5.5.m1.1.1.1.1.1.1.cmml" xref="A3.T6.5.5.5.m1.1.1.1.1">superscript</csymbol><ci id="A3.T6.5.5.5.m1.1.1.1.1.1.2.cmml" xref="A3.T6.5.5.5.m1.1.1.1.1.1.2">𝑟</ci><apply id="A3.T6.5.5.5.m1.1.1.1.1.1.3.cmml" xref="A3.T6.5.5.5.m1.1.1.1.1.1.3"><minus id="A3.T6.5.5.5.m1.1.1.1.1.1.3.1.cmml" xref="A3.T6.5.5.5.m1.1.1.1.1.1.3"></minus><apply id="A3.T6.5.5.5.m1.1.1.1.1.1.3.2.cmml" xref="A3.T6.5.5.5.m1.1.1.1.1.1.3.2"><divide id="A3.T6.5.5.5.m1.1.1.1.1.1.3.2.1.cmml" xref="A3.T6.5.5.5.m1.1.1.1.1.1.3.2"></divide><cn id="A3.T6.5.5.5.m1.1.1.1.1.1.3.2.2.cmml" type="integer" xref="A3.T6.5.5.5.m1.1.1.1.1.1.3.2.2">3</cn><cn id="A3.T6.5.5.5.m1.1.1.1.1.1.3.2.3.cmml" type="integer" xref="A3.T6.5.5.5.m1.1.1.1.1.1.3.2.3">2</cn></apply></apply></apply></apply></annotation-xml><annotation encoding="application/x-tex" id="A3.T6.5.5.5.m1.1c">{\mathcal{O}}(r^{-\frac{3}{2}})</annotation><annotation encoding="application/x-llamapun" id="A3.T6.5.5.5.m1.1d">caligraphic_O ( italic_r start_POSTSUPERSCRIPT - divide start_ARG 3 end_ARG start_ARG 2 end_ARG end_POSTSUPERSCRIPT )</annotation></semantics></math></td>
<td class="ltx_td ltx_align_center ltx_border_t" id="A3.T6.6.6.6"><math alttext="{\mathcal{O}}(r^{-1})" class="ltx_Math" display="inline" id="A3.T6.6.6.6.m1.1"><semantics id="A3.T6.6.6.6.m1.1a"><mrow id="A3.T6.6.6.6.m1.1.1" xref="A3.T6.6.6.6.m1.1.1.cmml"><mi class="ltx_font_mathcaligraphic" id="A3.T6.6.6.6.m1.1.1.3" xref="A3.T6.6.6.6.m1.1.1.3.cmml">𝒪</mi><mo id="A3.T6.6.6.6.m1.1.1.2" xref="A3.T6.6.6.6.m1.1.1.2.cmml">⁢</mo><mrow id="A3.T6.6.6.6.m1.1.1.1.1" xref="A3.T6.6.6.6.m1.1.1.1.1.1.cmml"><mo id="A3.T6.6.6.6.m1.1.1.1.1.2" stretchy="false" xref="A3.T6.6.6.6.m1.1.1.1.1.1.cmml">(</mo><msup id="A3.T6.6.6.6.m1.1.1.1.1.1" xref="A3.T6.6.6.6.m1.1.1.1.1.1.cmml"><mi id="A3.T6.6.6.6.m1.1.1.1.1.1.2" xref="A3.T6.6.6.6.m1.1.1.1.1.1.2.cmml">r</mi><mrow id="A3.T6.6.6.6.m1.1.1.1.1.1.3" xref="A3.T6.6.6.6.m1.1.1.1.1.1.3.cmml"><mo id="A3.T6.6.6.6.m1.1.1.1.1.1.3a" xref="A3.T6.6.6.6.m1.1.1.1.1.1.3.cmml">−</mo><mn id="A3.T6.6.6.6.m1.1.1.1.1.1.3.2" xref="A3.T6.6.6.6.m1.1.1.1.1.1.3.2.cmml">1</mn></mrow></msup><mo id="A3.T6.6.6.6.m1.1.1.1.1.3" stretchy="false" xref="A3.T6.6.6.6.m1.1.1.1.1.1.cmml">)</mo></mrow></mrow><annotation-xml encoding="MathML-Content" id="A3.T6.6.6.6.m1.1b"><apply id="A3.T6.6.6.6.m1.1.1.cmml" xref="A3.T6.6.6.6.m1.1.1"><times id="A3.T6.6.6.6.m1.1.1.2.cmml" xref="A3.T6.6.6.6.m1.1.1.2"></times><ci id="A3.T6.6.6.6.m1.1.1.3.cmml" xref="A3.T6.6.6.6.m1.1.1.3">𝒪</ci><apply id="A3.T6.6.6.6.m1.1.1.1.1.1.cmml" xref="A3.T6.6.6.6.m1.1.1.1.1"><csymbol cd="ambiguous" id="A3.T6.6.6.6.m1.1.1.1.1.1.1.cmml" xref="A3.T6.6.6.6.m1.1.1.1.1">superscript</csymbol><ci id="A3.T6.6.6.6.m1.1.1.1.1.1.2.cmml" xref="A3.T6.6.6.6.m1.1.1.1.1.1.2">𝑟</ci><apply id="A3.T6.6.6.6.m1.1.1.1.1.1.3.cmml" xref="A3.T6.6.6.6.m1.1.1.1.1.1.3"><minus id="A3.T6.6.6.6.m1.1.1.1.1.1.3.1.cmml" xref="A3.T6.6.6.6.m1.1.1.1.1.1.3"></minus><cn id="A3.T6.6.6.6.m1.1.1.1.1.1.3.2.cmml" type="integer" xref="A3.T6.6.6.6.m1.1.1.1.1.1.3.2">1</cn></apply></apply></apply></annotation-xml><annotation encoding="application/x-tex" id="A3.T6.6.6.6.m1.1c">{\mathcal{O}}(r^{-1})</annotation><annotation encoding="application/x-llamapun" id="A3.T6.6.6.6.m1.1d">caligraphic_O ( italic_r start_POSTSUPERSCRIPT - 1 end_POSTSUPERSCRIPT )</annotation></semantics></math></td>
<td class="ltx_td ltx_align_center ltx_border_t" id="A3.T6.7.7.7"><math alttext="{\mathcal{O}}(r^{-1})" class="ltx_Math" display="inline" id="A3.T6.7.7.7.m1.1"><semantics id="A3.T6.7.7.7.m1.1a"><mrow id="A3.T6.7.7.7.m1.1.1" xref="A3.T6.7.7.7.m1.1.1.cmml"><mi class="ltx_font_mathcaligraphic" id="A3.T6.7.7.7.m1.1.1.3" xref="A3.T6.7.7.7.m1.1.1.3.cmml">𝒪</mi><mo id="A3.T6.7.7.7.m1.1.1.2" xref="A3.T6.7.7.7.m1.1.1.2.cmml">⁢</mo><mrow id="A3.T6.7.7.7.m1.1.1.1.1" xref="A3.T6.7.7.7.m1.1.1.1.1.1.cmml"><mo id="A3.T6.7.7.7.m1.1.1.1.1.2" stretchy="false" xref="A3.T6.7.7.7.m1.1.1.1.1.1.cmml">(</mo><msup id="A3.T6.7.7.7.m1.1.1.1.1.1" xref="A3.T6.7.7.7.m1.1.1.1.1.1.cmml"><mi id="A3.T6.7.7.7.m1.1.1.1.1.1.2" xref="A3.T6.7.7.7.m1.1.1.1.1.1.2.cmml">r</mi><mrow id="A3.T6.7.7.7.m1.1.1.1.1.1.3" xref="A3.T6.7.7.7.m1.1.1.1.1.1.3.cmml"><mo id="A3.T6.7.7.7.m1.1.1.1.1.1.3a" xref="A3.T6.7.7.7.m1.1.1.1.1.1.3.cmml">−</mo><mn id="A3.T6.7.7.7.m1.1.1.1.1.1.3.2" xref="A3.T6.7.7.7.m1.1.1.1.1.1.3.2.cmml">1</mn></mrow></msup><mo id="A3.T6.7.7.7.m1.1.1.1.1.3" stretchy="false" xref="A3.T6.7.7.7.m1.1.1.1.1.1.cmml">)</mo></mrow></mrow><annotation-xml encoding="MathML-Content" id="A3.T6.7.7.7.m1.1b"><apply id="A3.T6.7.7.7.m1.1.1.cmml" xref="A3.T6.7.7.7.m1.1.1"><times id="A3.T6.7.7.7.m1.1.1.2.cmml" xref="A3.T6.7.7.7.m1.1.1.2"></times><ci id="A3.T6.7.7.7.m1.1.1.3.cmml" xref="A3.T6.7.7.7.m1.1.1.3">𝒪</ci><apply id="A3.T6.7.7.7.m1.1.1.1.1.1.cmml" xref="A3.T6.7.7.7.m1.1.1.1.1"><csymbol cd="ambiguous" id="A3.T6.7.7.7.m1.1.1.1.1.1.1.cmml" xref="A3.T6.7.7.7.m1.1.1.1.1">superscript</csymbol><ci id="A3.T6.7.7.7.m1.1.1.1.1.1.2.cmml" xref="A3.T6.7.7.7.m1.1.1.1.1.1.2">𝑟</ci><apply id="A3.T6.7.7.7.m1.1.1.1.1.1.3.cmml" xref="A3.T6.7.7.7.m1.1.1.1.1.1.3"><minus id="A3.T6.7.7.7.m1.1.1.1.1.1.3.1.cmml" xref="A3.T6.7.7.7.m1.1.1.1.1.1.3"></minus><cn id="A3.T6.7.7.7.m1.1.1.1.1.1.3.2.cmml" type="integer" xref="A3.T6.7.7.7.m1.1.1.1.1.1.3.2">1</cn></apply></apply></apply></annotation-xml><annotation encoding="application/x-tex" id="A3.T6.7.7.7.m1.1c">{\mathcal{O}}(r^{-1})</annotation><annotation encoding="application/x-llamapun" id="A3.T6.7.7.7.m1.1d">caligraphic_O ( italic_r start_POSTSUPERSCRIPT - 1 end_POSTSUPERSCRIPT )</annotation></semantics></math></td>
</tr>
<tr class="ltx_tr" id="A3.T6.14.14">
<td class="ltx_td ltx_align_left ltx_border_bb" id="A3.T6.8.8.1">Rate of <math alttext="\lim_{r\to 0}f^{\prime\prime}(r)" class="ltx_Math" display="inline" id="A3.T6.8.8.1.m1.1"><semantics id="A3.T6.8.8.1.m1.1a"><mrow id="A3.T6.8.8.1.m1.1.2" xref="A3.T6.8.8.1.m1.1.2.cmml"><msub id="A3.T6.8.8.1.m1.1.2.1" xref="A3.T6.8.8.1.m1.1.2.1.cmml"><mo id="A3.T6.8.8.1.m1.1.2.1.2" xref="A3.T6.8.8.1.m1.1.2.1.2.cmml">lim</mo><mrow id="A3.T6.8.8.1.m1.1.2.1.3" xref="A3.T6.8.8.1.m1.1.2.1.3.cmml"><mi id="A3.T6.8.8.1.m1.1.2.1.3.2" xref="A3.T6.8.8.1.m1.1.2.1.3.2.cmml">r</mi><mo id="A3.T6.8.8.1.m1.1.2.1.3.1" stretchy="false" xref="A3.T6.8.8.1.m1.1.2.1.3.1.cmml">→</mo><mn id="A3.T6.8.8.1.m1.1.2.1.3.3" xref="A3.T6.8.8.1.m1.1.2.1.3.3.cmml">0</mn></mrow></msub><mrow id="A3.T6.8.8.1.m1.1.2.2" xref="A3.T6.8.8.1.m1.1.2.2.cmml"><msup id="A3.T6.8.8.1.m1.1.2.2.2" xref="A3.T6.8.8.1.m1.1.2.2.2.cmml"><mi id="A3.T6.8.8.1.m1.1.2.2.2.2" xref="A3.T6.8.8.1.m1.1.2.2.2.2.cmml">f</mi><mo id="A3.T6.8.8.1.m1.1.2.2.2.3" xref="A3.T6.8.8.1.m1.1.2.2.2.3.cmml">′′</mo></msup><mo id="A3.T6.8.8.1.m1.1.2.2.1" xref="A3.T6.8.8.1.m1.1.2.2.1.cmml">⁢</mo><mrow id="A3.T6.8.8.1.m1.1.2.2.3.2" xref="A3.T6.8.8.1.m1.1.2.2.cmml"><mo id="A3.T6.8.8.1.m1.1.2.2.3.2.1" stretchy="false" xref="A3.T6.8.8.1.m1.1.2.2.cmml">(</mo><mi id="A3.T6.8.8.1.m1.1.1" xref="A3.T6.8.8.1.m1.1.1.cmml">r</mi><mo id="A3.T6.8.8.1.m1.1.2.2.3.2.2" stretchy="false" xref="A3.T6.8.8.1.m1.1.2.2.cmml">)</mo></mrow></mrow></mrow><annotation-xml encoding="MathML-Content" id="A3.T6.8.8.1.m1.1b"><apply id="A3.T6.8.8.1.m1.1.2.cmml" xref="A3.T6.8.8.1.m1.1.2"><apply id="A3.T6.8.8.1.m1.1.2.1.cmml" xref="A3.T6.8.8.1.m1.1.2.1"><csymbol cd="ambiguous" id="A3.T6.8.8.1.m1.1.2.1.1.cmml" xref="A3.T6.8.8.1.m1.1.2.1">subscript</csymbol><limit id="A3.T6.8.8.1.m1.1.2.1.2.cmml" xref="A3.T6.8.8.1.m1.1.2.1.2"></limit><apply id="A3.T6.8.8.1.m1.1.2.1.3.cmml" xref="A3.T6.8.8.1.m1.1.2.1.3"><ci id="A3.T6.8.8.1.m1.1.2.1.3.1.cmml" xref="A3.T6.8.8.1.m1.1.2.1.3.1">→</ci><ci id="A3.T6.8.8.1.m1.1.2.1.3.2.cmml" xref="A3.T6.8.8.1.m1.1.2.1.3.2">𝑟</ci><cn id="A3.T6.8.8.1.m1.1.2.1.3.3.cmml" type="integer" xref="A3.T6.8.8.1.m1.1.2.1.3.3">0</cn></apply></apply><apply id="A3.T6.8.8.1.m1.1.2.2.cmml" xref="A3.T6.8.8.1.m1.1.2.2"><times id="A3.T6.8.8.1.m1.1.2.2.1.cmml" xref="A3.T6.8.8.1.m1.1.2.2.1"></times><apply id="A3.T6.8.8.1.m1.1.2.2.2.cmml" xref="A3.T6.8.8.1.m1.1.2.2.2"><csymbol cd="ambiguous" id="A3.T6.8.8.1.m1.1.2.2.2.1.cmml" xref="A3.T6.8.8.1.m1.1.2.2.2">superscript</csymbol><ci id="A3.T6.8.8.1.m1.1.2.2.2.2.cmml" xref="A3.T6.8.8.1.m1.1.2.2.2.2">𝑓</ci><ci id="A3.T6.8.8.1.m1.1.2.2.2.3.cmml" xref="A3.T6.8.8.1.m1.1.2.2.2.3">′′</ci></apply><ci id="A3.T6.8.8.1.m1.1.1.cmml" xref="A3.T6.8.8.1.m1.1.1">𝑟</ci></apply></apply></annotation-xml><annotation encoding="application/x-tex" id="A3.T6.8.8.1.m1.1c">\lim_{r\to 0}f^{\prime\prime}(r)</annotation><annotation encoding="application/x-llamapun" id="A3.T6.8.8.1.m1.1d">roman_lim start_POSTSUBSCRIPT italic_r → 0 end_POSTSUBSCRIPT italic_f start_POSTSUPERSCRIPT ′ ′ end_POSTSUPERSCRIPT ( italic_r )</annotation></semantics></math>
</td>
<td class="ltx_td ltx_align_center ltx_border_bb" id="A3.T6.9.9.2"><math alttext="{\mathcal{O}}(r^{-2})" class="ltx_Math" display="inline" id="A3.T6.9.9.2.m1.1"><semantics id="A3.T6.9.9.2.m1.1a"><mrow id="A3.T6.9.9.2.m1.1.1" xref="A3.T6.9.9.2.m1.1.1.cmml"><mi class="ltx_font_mathcaligraphic" id="A3.T6.9.9.2.m1.1.1.3" xref="A3.T6.9.9.2.m1.1.1.3.cmml">𝒪</mi><mo id="A3.T6.9.9.2.m1.1.1.2" xref="A3.T6.9.9.2.m1.1.1.2.cmml">⁢</mo><mrow id="A3.T6.9.9.2.m1.1.1.1.1" xref="A3.T6.9.9.2.m1.1.1.1.1.1.cmml"><mo id="A3.T6.9.9.2.m1.1.1.1.1.2" stretchy="false" xref="A3.T6.9.9.2.m1.1.1.1.1.1.cmml">(</mo><msup id="A3.T6.9.9.2.m1.1.1.1.1.1" xref="A3.T6.9.9.2.m1.1.1.1.1.1.cmml"><mi id="A3.T6.9.9.2.m1.1.1.1.1.1.2" xref="A3.T6.9.9.2.m1.1.1.1.1.1.2.cmml">r</mi><mrow id="A3.T6.9.9.2.m1.1.1.1.1.1.3" xref="A3.T6.9.9.2.m1.1.1.1.1.1.3.cmml"><mo id="A3.T6.9.9.2.m1.1.1.1.1.1.3a" xref="A3.T6.9.9.2.m1.1.1.1.1.1.3.cmml">−</mo><mn id="A3.T6.9.9.2.m1.1.1.1.1.1.3.2" xref="A3.T6.9.9.2.m1.1.1.1.1.1.3.2.cmml">2</mn></mrow></msup><mo id="A3.T6.9.9.2.m1.1.1.1.1.3" stretchy="false" xref="A3.T6.9.9.2.m1.1.1.1.1.1.cmml">)</mo></mrow></mrow><annotation-xml encoding="MathML-Content" id="A3.T6.9.9.2.m1.1b"><apply id="A3.T6.9.9.2.m1.1.1.cmml" xref="A3.T6.9.9.2.m1.1.1"><times id="A3.T6.9.9.2.m1.1.1.2.cmml" xref="A3.T6.9.9.2.m1.1.1.2"></times><ci id="A3.T6.9.9.2.m1.1.1.3.cmml" xref="A3.T6.9.9.2.m1.1.1.3">𝒪</ci><apply id="A3.T6.9.9.2.m1.1.1.1.1.1.cmml" xref="A3.T6.9.9.2.m1.1.1.1.1"><csymbol cd="ambiguous" id="A3.T6.9.9.2.m1.1.1.1.1.1.1.cmml" xref="A3.T6.9.9.2.m1.1.1.1.1">superscript</csymbol><ci id="A3.T6.9.9.2.m1.1.1.1.1.1.2.cmml" xref="A3.T6.9.9.2.m1.1.1.1.1.1.2">𝑟</ci><apply id="A3.T6.9.9.2.m1.1.1.1.1.1.3.cmml" xref="A3.T6.9.9.2.m1.1.1.1.1.1.3"><minus id="A3.T6.9.9.2.m1.1.1.1.1.1.3.1.cmml" xref="A3.T6.9.9.2.m1.1.1.1.1.1.3"></minus><cn id="A3.T6.9.9.2.m1.1.1.1.1.1.3.2.cmml" type="integer" xref="A3.T6.9.9.2.m1.1.1.1.1.1.3.2">2</cn></apply></apply></apply></annotation-xml><annotation encoding="application/x-tex" id="A3.T6.9.9.2.m1.1c">{\mathcal{O}}(r^{-2})</annotation><annotation encoding="application/x-llamapun" id="A3.T6.9.9.2.m1.1d">caligraphic_O ( italic_r start_POSTSUPERSCRIPT - 2 end_POSTSUPERSCRIPT )</annotation></semantics></math></td>
<td class="ltx_td ltx_align_center ltx_border_bb" id="A3.T6.10.10.3"><math alttext="{\mathcal{O}}(r^{-2})" class="ltx_Math" display="inline" id="A3.T6.10.10.3.m1.1"><semantics id="A3.T6.10.10.3.m1.1a"><mrow id="A3.T6.10.10.3.m1.1.1" xref="A3.T6.10.10.3.m1.1.1.cmml"><mi class="ltx_font_mathcaligraphic" id="A3.T6.10.10.3.m1.1.1.3" xref="A3.T6.10.10.3.m1.1.1.3.cmml">𝒪</mi><mo id="A3.T6.10.10.3.m1.1.1.2" xref="A3.T6.10.10.3.m1.1.1.2.cmml">⁢</mo><mrow id="A3.T6.10.10.3.m1.1.1.1.1" xref="A3.T6.10.10.3.m1.1.1.1.1.1.cmml"><mo id="A3.T6.10.10.3.m1.1.1.1.1.2" stretchy="false" xref="A3.T6.10.10.3.m1.1.1.1.1.1.cmml">(</mo><msup id="A3.T6.10.10.3.m1.1.1.1.1.1" xref="A3.T6.10.10.3.m1.1.1.1.1.1.cmml"><mi id="A3.T6.10.10.3.m1.1.1.1.1.1.2" xref="A3.T6.10.10.3.m1.1.1.1.1.1.2.cmml">r</mi><mrow id="A3.T6.10.10.3.m1.1.1.1.1.1.3" xref="A3.T6.10.10.3.m1.1.1.1.1.1.3.cmml"><mo id="A3.T6.10.10.3.m1.1.1.1.1.1.3a" xref="A3.T6.10.10.3.m1.1.1.1.1.1.3.cmml">−</mo><mn id="A3.T6.10.10.3.m1.1.1.1.1.1.3.2" xref="A3.T6.10.10.3.m1.1.1.1.1.1.3.2.cmml">2</mn></mrow></msup><mo id="A3.T6.10.10.3.m1.1.1.1.1.3" stretchy="false" xref="A3.T6.10.10.3.m1.1.1.1.1.1.cmml">)</mo></mrow></mrow><annotation-xml encoding="MathML-Content" id="A3.T6.10.10.3.m1.1b"><apply id="A3.T6.10.10.3.m1.1.1.cmml" xref="A3.T6.10.10.3.m1.1.1"><times id="A3.T6.10.10.3.m1.1.1.2.cmml" xref="A3.T6.10.10.3.m1.1.1.2"></times><ci id="A3.T6.10.10.3.m1.1.1.3.cmml" xref="A3.T6.10.10.3.m1.1.1.3">𝒪</ci><apply id="A3.T6.10.10.3.m1.1.1.1.1.1.cmml" xref="A3.T6.10.10.3.m1.1.1.1.1"><csymbol cd="ambiguous" id="A3.T6.10.10.3.m1.1.1.1.1.1.1.cmml" xref="A3.T6.10.10.3.m1.1.1.1.1">superscript</csymbol><ci id="A3.T6.10.10.3.m1.1.1.1.1.1.2.cmml" xref="A3.T6.10.10.3.m1.1.1.1.1.1.2">𝑟</ci><apply id="A3.T6.10.10.3.m1.1.1.1.1.1.3.cmml" xref="A3.T6.10.10.3.m1.1.1.1.1.1.3"><minus id="A3.T6.10.10.3.m1.1.1.1.1.1.3.1.cmml" xref="A3.T6.10.10.3.m1.1.1.1.1.1.3"></minus><cn id="A3.T6.10.10.3.m1.1.1.1.1.1.3.2.cmml" type="integer" xref="A3.T6.10.10.3.m1.1.1.1.1.1.3.2">2</cn></apply></apply></apply></annotation-xml><annotation encoding="application/x-tex" id="A3.T6.10.10.3.m1.1c">{\mathcal{O}}(r^{-2})</annotation><annotation encoding="application/x-llamapun" id="A3.T6.10.10.3.m1.1d">caligraphic_O ( italic_r start_POSTSUPERSCRIPT - 2 end_POSTSUPERSCRIPT )</annotation></semantics></math></td>
<td class="ltx_td ltx_align_center ltx_border_bb" id="A3.T6.11.11.4"><math alttext="{\mathcal{O}}(r^{-1})" class="ltx_Math" display="inline" id="A3.T6.11.11.4.m1.1"><semantics id="A3.T6.11.11.4.m1.1a"><mrow id="A3.T6.11.11.4.m1.1.1" xref="A3.T6.11.11.4.m1.1.1.cmml"><mi class="ltx_font_mathcaligraphic" id="A3.T6.11.11.4.m1.1.1.3" xref="A3.T6.11.11.4.m1.1.1.3.cmml">𝒪</mi><mo id="A3.T6.11.11.4.m1.1.1.2" xref="A3.T6.11.11.4.m1.1.1.2.cmml">⁢</mo><mrow id="A3.T6.11.11.4.m1.1.1.1.1" xref="A3.T6.11.11.4.m1.1.1.1.1.1.cmml"><mo id="A3.T6.11.11.4.m1.1.1.1.1.2" stretchy="false" xref="A3.T6.11.11.4.m1.1.1.1.1.1.cmml">(</mo><msup id="A3.T6.11.11.4.m1.1.1.1.1.1" xref="A3.T6.11.11.4.m1.1.1.1.1.1.cmml"><mi id="A3.T6.11.11.4.m1.1.1.1.1.1.2" xref="A3.T6.11.11.4.m1.1.1.1.1.1.2.cmml">r</mi><mrow id="A3.T6.11.11.4.m1.1.1.1.1.1.3" xref="A3.T6.11.11.4.m1.1.1.1.1.1.3.cmml"><mo id="A3.T6.11.11.4.m1.1.1.1.1.1.3a" xref="A3.T6.11.11.4.m1.1.1.1.1.1.3.cmml">−</mo><mn id="A3.T6.11.11.4.m1.1.1.1.1.1.3.2" xref="A3.T6.11.11.4.m1.1.1.1.1.1.3.2.cmml">1</mn></mrow></msup><mo id="A3.T6.11.11.4.m1.1.1.1.1.3" stretchy="false" xref="A3.T6.11.11.4.m1.1.1.1.1.1.cmml">)</mo></mrow></mrow><annotation-xml encoding="MathML-Content" id="A3.T6.11.11.4.m1.1b"><apply id="A3.T6.11.11.4.m1.1.1.cmml" xref="A3.T6.11.11.4.m1.1.1"><times id="A3.T6.11.11.4.m1.1.1.2.cmml" xref="A3.T6.11.11.4.m1.1.1.2"></times><ci id="A3.T6.11.11.4.m1.1.1.3.cmml" xref="A3.T6.11.11.4.m1.1.1.3">𝒪</ci><apply id="A3.T6.11.11.4.m1.1.1.1.1.1.cmml" xref="A3.T6.11.11.4.m1.1.1.1.1"><csymbol cd="ambiguous" id="A3.T6.11.11.4.m1.1.1.1.1.1.1.cmml" xref="A3.T6.11.11.4.m1.1.1.1.1">superscript</csymbol><ci id="A3.T6.11.11.4.m1.1.1.1.1.1.2.cmml" xref="A3.T6.11.11.4.m1.1.1.1.1.1.2">𝑟</ci><apply id="A3.T6.11.11.4.m1.1.1.1.1.1.3.cmml" xref="A3.T6.11.11.4.m1.1.1.1.1.1.3"><minus id="A3.T6.11.11.4.m1.1.1.1.1.1.3.1.cmml" xref="A3.T6.11.11.4.m1.1.1.1.1.1.3"></minus><cn id="A3.T6.11.11.4.m1.1.1.1.1.1.3.2.cmml" type="integer" xref="A3.T6.11.11.4.m1.1.1.1.1.1.3.2">1</cn></apply></apply></apply></annotation-xml><annotation encoding="application/x-tex" id="A3.T6.11.11.4.m1.1c">{\mathcal{O}}(r^{-1})</annotation><annotation encoding="application/x-llamapun" id="A3.T6.11.11.4.m1.1d">caligraphic_O ( italic_r start_POSTSUPERSCRIPT - 1 end_POSTSUPERSCRIPT )</annotation></semantics></math></td>
<td class="ltx_td ltx_align_center ltx_border_bb" id="A3.T6.12.12.5"><math alttext="{\mathcal{O}}(r^{-\frac{3}{2}})" class="ltx_Math" display="inline" id="A3.T6.12.12.5.m1.1"><semantics id="A3.T6.12.12.5.m1.1a"><mrow id="A3.T6.12.12.5.m1.1.1" xref="A3.T6.12.12.5.m1.1.1.cmml"><mi class="ltx_font_mathcaligraphic" id="A3.T6.12.12.5.m1.1.1.3" xref="A3.T6.12.12.5.m1.1.1.3.cmml">𝒪</mi><mo id="A3.T6.12.12.5.m1.1.1.2" xref="A3.T6.12.12.5.m1.1.1.2.cmml">⁢</mo><mrow id="A3.T6.12.12.5.m1.1.1.1.1" xref="A3.T6.12.12.5.m1.1.1.1.1.1.cmml"><mo id="A3.T6.12.12.5.m1.1.1.1.1.2" stretchy="false" xref="A3.T6.12.12.5.m1.1.1.1.1.1.cmml">(</mo><msup id="A3.T6.12.12.5.m1.1.1.1.1.1" xref="A3.T6.12.12.5.m1.1.1.1.1.1.cmml"><mi id="A3.T6.12.12.5.m1.1.1.1.1.1.2" xref="A3.T6.12.12.5.m1.1.1.1.1.1.2.cmml">r</mi><mrow id="A3.T6.12.12.5.m1.1.1.1.1.1.3" xref="A3.T6.12.12.5.m1.1.1.1.1.1.3.cmml"><mo id="A3.T6.12.12.5.m1.1.1.1.1.1.3a" xref="A3.T6.12.12.5.m1.1.1.1.1.1.3.cmml">−</mo><mfrac id="A3.T6.12.12.5.m1.1.1.1.1.1.3.2" xref="A3.T6.12.12.5.m1.1.1.1.1.1.3.2.cmml"><mn id="A3.T6.12.12.5.m1.1.1.1.1.1.3.2.2" xref="A3.T6.12.12.5.m1.1.1.1.1.1.3.2.2.cmml">3</mn><mn id="A3.T6.12.12.5.m1.1.1.1.1.1.3.2.3" xref="A3.T6.12.12.5.m1.1.1.1.1.1.3.2.3.cmml">2</mn></mfrac></mrow></msup><mo id="A3.T6.12.12.5.m1.1.1.1.1.3" stretchy="false" xref="A3.T6.12.12.5.m1.1.1.1.1.1.cmml">)</mo></mrow></mrow><annotation-xml encoding="MathML-Content" id="A3.T6.12.12.5.m1.1b"><apply id="A3.T6.12.12.5.m1.1.1.cmml" xref="A3.T6.12.12.5.m1.1.1"><times id="A3.T6.12.12.5.m1.1.1.2.cmml" xref="A3.T6.12.12.5.m1.1.1.2"></times><ci id="A3.T6.12.12.5.m1.1.1.3.cmml" xref="A3.T6.12.12.5.m1.1.1.3">𝒪</ci><apply id="A3.T6.12.12.5.m1.1.1.1.1.1.cmml" xref="A3.T6.12.12.5.m1.1.1.1.1"><csymbol cd="ambiguous" id="A3.T6.12.12.5.m1.1.1.1.1.1.1.cmml" xref="A3.T6.12.12.5.m1.1.1.1.1">superscript</csymbol><ci id="A3.T6.12.12.5.m1.1.1.1.1.1.2.cmml" xref="A3.T6.12.12.5.m1.1.1.1.1.1.2">𝑟</ci><apply id="A3.T6.12.12.5.m1.1.1.1.1.1.3.cmml" xref="A3.T6.12.12.5.m1.1.1.1.1.1.3"><minus id="A3.T6.12.12.5.m1.1.1.1.1.1.3.1.cmml" xref="A3.T6.12.12.5.m1.1.1.1.1.1.3"></minus><apply id="A3.T6.12.12.5.m1.1.1.1.1.1.3.2.cmml" xref="A3.T6.12.12.5.m1.1.1.1.1.1.3.2"><divide id="A3.T6.12.12.5.m1.1.1.1.1.1.3.2.1.cmml" xref="A3.T6.12.12.5.m1.1.1.1.1.1.3.2"></divide><cn id="A3.T6.12.12.5.m1.1.1.1.1.1.3.2.2.cmml" type="integer" xref="A3.T6.12.12.5.m1.1.1.1.1.1.3.2.2">3</cn><cn id="A3.T6.12.12.5.m1.1.1.1.1.1.3.2.3.cmml" type="integer" xref="A3.T6.12.12.5.m1.1.1.1.1.1.3.2.3">2</cn></apply></apply></apply></apply></annotation-xml><annotation encoding="application/x-tex" id="A3.T6.12.12.5.m1.1c">{\mathcal{O}}(r^{-\frac{3}{2}})</annotation><annotation encoding="application/x-llamapun" id="A3.T6.12.12.5.m1.1d">caligraphic_O ( italic_r start_POSTSUPERSCRIPT - divide start_ARG 3 end_ARG start_ARG 2 end_ARG end_POSTSUPERSCRIPT )</annotation></semantics></math></td>
<td class="ltx_td ltx_align_center ltx_border_bb" id="A3.T6.13.13.6"><math alttext="{\mathcal{O}}(r^{-1})" class="ltx_Math" display="inline" id="A3.T6.13.13.6.m1.1"><semantics id="A3.T6.13.13.6.m1.1a"><mrow id="A3.T6.13.13.6.m1.1.1" xref="A3.T6.13.13.6.m1.1.1.cmml"><mi class="ltx_font_mathcaligraphic" id="A3.T6.13.13.6.m1.1.1.3" xref="A3.T6.13.13.6.m1.1.1.3.cmml">𝒪</mi><mo id="A3.T6.13.13.6.m1.1.1.2" xref="A3.T6.13.13.6.m1.1.1.2.cmml">⁢</mo><mrow id="A3.T6.13.13.6.m1.1.1.1.1" xref="A3.T6.13.13.6.m1.1.1.1.1.1.cmml"><mo id="A3.T6.13.13.6.m1.1.1.1.1.2" stretchy="false" xref="A3.T6.13.13.6.m1.1.1.1.1.1.cmml">(</mo><msup id="A3.T6.13.13.6.m1.1.1.1.1.1" xref="A3.T6.13.13.6.m1.1.1.1.1.1.cmml"><mi id="A3.T6.13.13.6.m1.1.1.1.1.1.2" xref="A3.T6.13.13.6.m1.1.1.1.1.1.2.cmml">r</mi><mrow id="A3.T6.13.13.6.m1.1.1.1.1.1.3" xref="A3.T6.13.13.6.m1.1.1.1.1.1.3.cmml"><mo id="A3.T6.13.13.6.m1.1.1.1.1.1.3a" xref="A3.T6.13.13.6.m1.1.1.1.1.1.3.cmml">−</mo><mn id="A3.T6.13.13.6.m1.1.1.1.1.1.3.2" xref="A3.T6.13.13.6.m1.1.1.1.1.1.3.2.cmml">1</mn></mrow></msup><mo id="A3.T6.13.13.6.m1.1.1.1.1.3" stretchy="false" xref="A3.T6.13.13.6.m1.1.1.1.1.1.cmml">)</mo></mrow></mrow><annotation-xml encoding="MathML-Content" id="A3.T6.13.13.6.m1.1b"><apply id="A3.T6.13.13.6.m1.1.1.cmml" xref="A3.T6.13.13.6.m1.1.1"><times id="A3.T6.13.13.6.m1.1.1.2.cmml" xref="A3.T6.13.13.6.m1.1.1.2"></times><ci id="A3.T6.13.13.6.m1.1.1.3.cmml" xref="A3.T6.13.13.6.m1.1.1.3">𝒪</ci><apply id="A3.T6.13.13.6.m1.1.1.1.1.1.cmml" xref="A3.T6.13.13.6.m1.1.1.1.1"><csymbol cd="ambiguous" id="A3.T6.13.13.6.m1.1.1.1.1.1.1.cmml" xref="A3.T6.13.13.6.m1.1.1.1.1">superscript</csymbol><ci id="A3.T6.13.13.6.m1.1.1.1.1.1.2.cmml" xref="A3.T6.13.13.6.m1.1.1.1.1.1.2">𝑟</ci><apply id="A3.T6.13.13.6.m1.1.1.1.1.1.3.cmml" xref="A3.T6.13.13.6.m1.1.1.1.1.1.3"><minus id="A3.T6.13.13.6.m1.1.1.1.1.1.3.1.cmml" xref="A3.T6.13.13.6.m1.1.1.1.1.1.3"></minus><cn id="A3.T6.13.13.6.m1.1.1.1.1.1.3.2.cmml" type="integer" xref="A3.T6.13.13.6.m1.1.1.1.1.1.3.2">1</cn></apply></apply></apply></annotation-xml><annotation encoding="application/x-tex" id="A3.T6.13.13.6.m1.1c">{\mathcal{O}}(r^{-1})</annotation><annotation encoding="application/x-llamapun" id="A3.T6.13.13.6.m1.1d">caligraphic_O ( italic_r start_POSTSUPERSCRIPT - 1 end_POSTSUPERSCRIPT )</annotation></semantics></math></td>
<td class="ltx_td ltx_align_center ltx_border_bb" id="A3.T6.14.14.7"><math alttext="{\mathcal{O}}(r^{-2})" class="ltx_Math" display="inline" id="A3.T6.14.14.7.m1.1"><semantics id="A3.T6.14.14.7.m1.1a"><mrow id="A3.T6.14.14.7.m1.1.1" xref="A3.T6.14.14.7.m1.1.1.cmml"><mi class="ltx_font_mathcaligraphic" id="A3.T6.14.14.7.m1.1.1.3" xref="A3.T6.14.14.7.m1.1.1.3.cmml">𝒪</mi><mo id="A3.T6.14.14.7.m1.1.1.2" xref="A3.T6.14.14.7.m1.1.1.2.cmml">⁢</mo><mrow id="A3.T6.14.14.7.m1.1.1.1.1" xref="A3.T6.14.14.7.m1.1.1.1.1.1.cmml"><mo id="A3.T6.14.14.7.m1.1.1.1.1.2" stretchy="false" xref="A3.T6.14.14.7.m1.1.1.1.1.1.cmml">(</mo><msup id="A3.T6.14.14.7.m1.1.1.1.1.1" xref="A3.T6.14.14.7.m1.1.1.1.1.1.cmml"><mi id="A3.T6.14.14.7.m1.1.1.1.1.1.2" xref="A3.T6.14.14.7.m1.1.1.1.1.1.2.cmml">r</mi><mrow id="A3.T6.14.14.7.m1.1.1.1.1.1.3" xref="A3.T6.14.14.7.m1.1.1.1.1.1.3.cmml"><mo id="A3.T6.14.14.7.m1.1.1.1.1.1.3a" xref="A3.T6.14.14.7.m1.1.1.1.1.1.3.cmml">−</mo><mn id="A3.T6.14.14.7.m1.1.1.1.1.1.3.2" xref="A3.T6.14.14.7.m1.1.1.1.1.1.3.2.cmml">2</mn></mrow></msup><mo id="A3.T6.14.14.7.m1.1.1.1.1.3" stretchy="false" xref="A3.T6.14.14.7.m1.1.1.1.1.1.cmml">)</mo></mrow></mrow><annotation-xml encoding="MathML-Content" id="A3.T6.14.14.7.m1.1b"><apply id="A3.T6.14.14.7.m1.1.1.cmml" xref="A3.T6.14.14.7.m1.1.1"><times id="A3.T6.14.14.7.m1.1.1.2.cmml" xref="A3.T6.14.14.7.m1.1.1.2"></times><ci id="A3.T6.14.14.7.m1.1.1.3.cmml" xref="A3.T6.14.14.7.m1.1.1.3">𝒪</ci><apply id="A3.T6.14.14.7.m1.1.1.1.1.1.cmml" xref="A3.T6.14.14.7.m1.1.1.1.1"><csymbol cd="ambiguous" id="A3.T6.14.14.7.m1.1.1.1.1.1.1.cmml" xref="A3.T6.14.14.7.m1.1.1.1.1">superscript</csymbol><ci id="A3.T6.14.14.7.m1.1.1.1.1.1.2.cmml" xref="A3.T6.14.14.7.m1.1.1.1.1.1.2">𝑟</ci><apply id="A3.T6.14.14.7.m1.1.1.1.1.1.3.cmml" xref="A3.T6.14.14.7.m1.1.1.1.1.1.3"><minus id="A3.T6.14.14.7.m1.1.1.1.1.1.3.1.cmml" xref="A3.T6.14.14.7.m1.1.1.1.1.1.3"></minus><cn id="A3.T6.14.14.7.m1.1.1.1.1.1.3.2.cmml" type="integer" xref="A3.T6.14.14.7.m1.1.1.1.1.1.3.2">2</cn></apply></apply></apply></annotation-xml><annotation encoding="application/x-tex" id="A3.T6.14.14.7.m1.1c">{\mathcal{O}}(r^{-2})</annotation><annotation encoding="application/x-llamapun" id="A3.T6.14.14.7.m1.1d">caligraphic_O ( italic_r start_POSTSUPERSCRIPT - 2 end_POSTSUPERSCRIPT )</annotation></semantics></math></td>
</tr>
</table>{{< /table-caption >}}
> 🔼 표 6은 다양한 f-다이버전스에 대한 왼쪽 및 오른쪽 꼬리 가중치를 보여줍니다.  '꼬리 가중치'는 f-다이버전스의 모드 추구(mode-seeking) 또는 모드 포함(mode-covering) 특성을 얼마나 강하게 처벌하는지를 나타냅니다.  더 큰 값은 모드 추구 동작에 더 큰 패널티를 부과함을 의미합니다.  표에서 볼 수 있듯이, 모드 추구 성향이 적은 f-다이버전스(예: forward-KL)는 더 큰 오른쪽 꼬리 가중치와 더 작은 왼쪽 꼬리 가중치를 가지는 경향이 있습니다. 이는 가중치 함수 h(r) = f''(r)r² 에서 증가하는 함수로 나타납니다.  증가하는 h는 낮은 밀도 영역에서 샘플에 더 적은 가중치를 부여하는 경향이 있습니다.  이러한 특성은 원래 논문 [52]의 꼬리 가중치 정의를 명확성을 위해 일정 값만큼 이동한 것입니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Right / left weight for different f𝑓fitalic_f-divergences. We shift the tail weight in [52] by a constant for clarity.
> </details>

{{< table-caption >}}
| FID ↓ | Recall ↑ | NFE |
|---|---|---|
| **Multi-step diffusion models** |  |  |  |
| DDPM [12] | 3.17 |  | 1000 |
| LSGM [61] | 2.10 |  | 138 |
| EDM [17] (teacher) | 1.79 |  | 35 |
| PFGM++ [68] | 1.74 |  | 35 |
| **GANs** |  |  |  |
| BigGAN [3] | 14.73 |  | 1 |
| StyleSAN-XL [48] | 1.36 |  | 1 |
| **Diffusion distillation** |  |  |  |
| Adversarial distillation | 2.60 |  | 1 |
| **f-distill** |  |  |  |
| reverse-KL (✓, DMD2 [71]) | 2.13 | 0.60 | 1 |
| softened RKL (✓) | 2.21 | 0.60 | 1 |
| squared Hellinger (–) | 1.99 | 0.63 | 1 |
| JS (–) | 2.00 | 0.62 | 1 |
| Jeffreys (✗) | 2.05 | 0.62 | 1 |
| forward-KL (✗) | 1.92 | 0.62 | 1 |{{< /table-caption >}}
> 🔼 표 7은 CIFAR-10 데이터셋에서 다양한 f-divergence 기반의 f-distill 모델의 성능을 FID(Fréchet Inception Distance) 점수와 재현율 점수로 비교한 표입니다.  f-divergence의 모드 추구 경향에 따라 ✓(높음), –(중간), ✗(낮음)으로 분류하여  모드 추구 경향이 모델 성능에 미치는 영향을 분석합니다.  각 f-divergence별 FID 점수와 재현율 점수를 비교함으로써, 어떤 f-divergence가 CIFAR-10 이미지 생성 작업에 더 적합한지 평가합니다.  결과적으로 모드 추구 경향이 낮은 f-divergence가 더 좋은 성능을 보여줌을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 7: FID and Recall scores on CIFAR-10. ✓/–/✗ stand for high/medium/low mode-seeking tendency for f𝑓fitalic_f-divergence.
> </details>

{{< table-caption >}}
| In-batch-sim ↓ |  | 
|---|---| 
| SDv1.5 (NFE=50, CFG=3, ODE) | 0.55 / 0.70 | 
| SDv1.5 (NFE=50, CFG=8, ODE) | 0.62 / 0.72 | 
| 1-2 |  | 
| *CFG=1.75* |  | 
| reverse-KL (DMD2 [71]) | 0.50 / 0.42 | 
| JS (*ours*) | 0.49 / 0.41 | 
| 1-2 |  | 
| *CFG=5* |  | 
| reverse-KL (DMD2 [71]) | 0.67 / 0.60 | 
| JS (*ours*) | 0.65 / 0.58 | {{< /table-caption >}}
> 🔼 표 8은 MS COCO 2014 데이터셋과 Parti-Prompt 데이터셋에서 배치 내 유사도(In-batch similarity)를 측정한 결과를 보여줍니다. 배치 내 유사도는 생성된 이미지들의 다양성을 평가하는 지표로, 값이 낮을수록 다양성이 높음을 의미합니다.  표는 서로 다른 설정(CFG 값, 사용된 f-divergence 등) 하에서 측정된 배치 내 유사도를 비교하여, 다양성 측면에서 각 설정의 성능을 평가하기 위한 것입니다.  특히,  다양성 측면에서 JS(Jensen-Shannon) divergence 기반의 f-distill 방법이 reverse-KL divergence 보다 우수함을 보여주는 결과가 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 8: In-batch similarity on MS COCO 2014 / Parti-Prompt
> </details>

{{< table-caption >}}
| Method | Anime | Photo | Concept Art | Painting |
|---|---|---|---|---|
| SDv1.5 (CFG=3) | 26.30 | 27.56 | 25.86 | 26.08 |
| SDv1.5 (CFG=8) | 27.53 | 28.46 | 26.94 | 26.83 |
| InstaFlow [27] | 25.98 | 26.32 | 25.79 | 25.93 |
| SwiftBrush [36] | 26.91 | 27.21 | 26.32 | 26.37 |
| SwiftBrush v2 [6] | 27.25 | 27.62 | 26.86 | 26.77 |
| *CFG=1.75* |  |  |  |  |
| reverse-KL (DMD2 [71]) | 26.20 | 27.33 | 25.82 | 25.68 |
| JS (*ours*) | 26.32 ↑ | 27.71 ↑ | 25.79 ↓ | 25.81 ↑ |
| *CFG=5* |  |  |  |  |
| reverse-KL (DMD2 [71]) | 26.52 | 27.86 | 26.25 | 26.10 |
| JS (*ours*) | 26.85 ↑ | 27.98 ↑ | 26.37 ↑ | 26.34 ↑ |{{< /table-caption >}}
> 🔼 표 9는 이미지 생성 품질을 평가하는 지표인 HPSv2 점수를 보여줍니다. HPSv2 점수는 다양한 스타일(애니메이션, 사진, 컨셉 아트, 그림)의 이미지에 대해 각각 계산되며, 점수가 높을수록 이미지의 품질이 높다는 것을 의미합니다. 이 표에서는 다양한 f-divergence 기법과 CFG(Classifier-Free Guidance) 가중치를 사용한 one-step 생성 모델과 multi-step 생성 모델의 HPSv2 점수를 비교하여, 제안된 f-distill 방법의 성능을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 9: HPSv2 score
> </details>

{{< table-caption >}}
|                     | w/o GAN loss | w/ GAN loss |
|-----------------|----------------|----------------|
| *CIFAR-10*       |                |                |
| reverse-KL (DMD2) | 4.07           | 2.13           |
| JS                | 3.98           | 2.00           |
| squared Hellinger | 3.81           | 1.99           |
| forward-KL        | **3.76**       | **1.92**       |
| *MS-COCO-30k*    |                |                |
| reverse-KL (DMD2) | 9.54           | 8.17           |
| JS                | **9.10**       | **7.42**       |{{< /table-caption >}}
> 🔼 이 표는 논문의 GAN 손실 제거 실험 결과를 보여줍니다.  CIFAR-10과 MS-COCO 데이터셋에서 GAN 손실을 사용했을 때와 사용하지 않았을 때의 FID(Fréchet Inception Distance) 점수를 비교하여, GAN 손실이 f-divergence 기반의 distillation 방법의 성능에 미치는 영향을 분석합니다.  다양한 f-divergence (역방향 KL, JS, 제곱 헬링거, 전방향 KL 등)에 대한 결과가 제시되어, GAN 손실의 유무에 따른 각 f-divergence의 성능 변화를 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 10: FID score for ablation study on GAN loss
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