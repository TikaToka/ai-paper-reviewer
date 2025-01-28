---
title: "Denoising as Adaptation: Noise-Space Domain Adaptation for Image Restoration"
summary: "잡음 공간 도메인 적응을 활용, 합성 및 실제 이미지 간 차이 해소하며 이미지 복원 성능 향상!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Generation", "🏢 Nanyang Technological University",]
showSummary: true
date: 2024-06-26
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2406.18516 {{< /keyword >}}
{{< keyword icon="writer" >}} Kang Liao et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-27 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2406.18516" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2406.18516" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/denoising-as-adaptation-noise-space-domain" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

이미지 복원은 합성 데이터로 학습된 모델이 실제 환경에 적용될 때 성능이 저하되는 **도메인 격차 문제**를 가지고 있습니다. 기존 연구는 데이터 합성 개선, 손상 커널 추정, 심층 학습, 도메인 적응 및 규제 등의 방법으로 이 문제를 해결하려 했지만, 특히 저수준 비전 작업에서 안정적이고 효율적인 프레임워크를 제공하는 데 어려움이 있었습니다. 

본 논문에서는 **확산 모델을 이용하여 잡음 공간에서 도메인 적응을 수행**하는 새로운 방법을 제안합니다. 보조 조건 입력이 다단계 잡음 제거 과정에 미치는 영향을 활용하여, 합성 및 실제 복원 결과를 모두 목표 분포에 맞추는 의미있는 확산 손실을 도출했습니다.  **채널 섞기 및 잔차 교환 대조 학습** 등의 전략을 통해 공동 학습 중 지름길 학습을 방지하여 모델이 쉽게 구분되는 특징에 의존하지 않도록 했습니다. 실험 결과, 제안된 방법은 잡음 제거, 흐릿함 제거, 비 제거 등 세 가지 이미지 복원 작업에서 효과적임을 보였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 잡음 공간 도메인 적응 기법을 통해 합성 데이터와 실제 데이터 간의 차이를 효과적으로 해소 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 이미지 복원 네트워크의 일반화 성능 향상 및 다양한 이미지 복원 작업(잡음 제거, 흐릿함 제거, 비 제거)에 대한 성능 향상 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 채널 섞기 및 잔차 교환 대조 학습 등의 전략을 통해 단순한 지름길 학습을 방지하고 모델의 일반화 성능 향상 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
이 논문은 **합성 데이터와 실제 데이터 간의 도메인 격차를 해소**하는 새로운 방법을 제시하여 이미지 복원 분야의 발전에 크게 기여합니다. **잡음 공간 도메인 적응**이라는 참신한 접근 방식을 통해 다양한 이미지 복원 작업에 적용 가능하며, 기존 방법의 한계를 극복하고 성능을 향상시키는 데 중요한 의미를 가집니다. 또한, 제시된 방법은 **다양한 네트워크와 손쉽게 호환**되므로, 향후 연구에서 다양한 이미지 복원 모델에 적용하고 성능을 향상시킬 수 있는 잠재력이 높습니다. 이러한 연구 결과는 이미지 복원 분야의 새로운 연구 방향을 제시하고, 향후 관련 연구에 중요한 영향을 미칠 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2406.18516/x1.png)

> 🔼 그림 1은 확산 모델의 예측 오류가 조건부 입력의 품질에 크게 의존한다는 것을 보여줍니다. (a)에서는 원래의 잡음이 많은 입력과 함께 추가적인 조건을 도입하는 실험을 보여줍니다. 이 조건은 0에서 80까지의 잡음 수준(σ)을 가진 가산성 백색 가우스 잡음으로 손상된 동일한 대상 이미지입니다. 부록 A1.1에서 자세한 내용을 확인할 수 있습니다. (b)에서는 복원 네트워크가 확산 모델의 잡음 예측 오류를 최소화하기 위해 '양호한' 조건을 제공하도록 최적화되어 깨끗한 대상 분포를 목표로 하는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: (a) The prediction error of a diffusion model is highly dependent on the quality of the conditional inputs. In this experiment, we introduce an additional condition alongside the original noisy input. This condition is the same target image but corrupted with additive white Gaussian noise at a noise level σ∈[0,80]𝜎080\sigma\in[0,80]italic_σ ∈ [ 0 , 80 ]. More details can be found in the Appendix A1.1. (b) The restoration network is optimized to provide “good” conditions to minimize the diffusion model’s noise prediction error, aiming for a clean target distribution.
> </details>





{{< table-caption >}}
| Metrics | Vanilla | DANN | DSN | PixelDA | CyCADA | Ne2Ne | MaskedD | Ours |
|---|---|---|---|---|---|---|---|---|
| Space | - | Feature | Feature | Pixel | Feature&Pixel | - | - | Noise |
| Train Data | _syn_ | _both_ | _both_ | _both_ | _both_ | _real_ | _real_ | _both_ |
| PSNR ↑ | 26.58 | 30.09 | 28.40 | 29.24 | 30.81 | 25.61 | 28.51 | 34.71 |
| SSIM ↑ | 0.6132 | 0.7832 | 0.6984 | 0.7611 | 0.8067 | 0.5647 | 0.7196 | 0.9202 |
| LPIPS ↓ | 0.3171 | 0.1348 | 0.2265 | 0.1403 | 0.1256 | 0.3039 | 0.2348 | 0.0903 |{{< /table-caption >}}

> 🔼 표 1은 Abdelhamed 등(2018)이 제시한 SIDD 테스트 데이터셋을 사용하여 이미지 잡음 제거 작업에 대한 정량적 평가 결과를 보여줍니다.  'syn'은 합성 데이터로만 학습된 모델, 'real'은 실제 데이터(GT 없음)로만 학습된 모델, 'both'는 합성 및 실제 데이터(GT 없음) 모두로 학습된 모델을 나타냅니다.  각 모델의 성능은 PSNR(Peak Signal-to-Noise Ratio), SSIM(Structural Similarity Index), LPIPS(Learned Perceptual Image Patch Similarity) 세 가지 지표로 측정되었으며, 각 지표에서 가장 좋은 점수가 강조 표시되어 있습니다. 이 표는 제안된 방법이 다양한 학습 데이터 조건에서 이미지 잡음 제거 성능에 미치는 영향을 정량적으로 비교 분석하는 데 사용되었습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Quantitative evaluation of the image denoising task on SIDD test dataset (Abdelhamed et al., 2018). syn, real, both denote the model is trained on synthetic, real-world (w/o GT), and both synthetic and real-world (w/o GT) datasets, respectively. The best score is highlighted.
> </details>





### In-depth insights


#### Noise-Space Adaptation
본 논문에서 제안하는 '잡음 공간 적응(Noise-Space Adaptation)'은 기존의 특징 공간이나 픽셀 공간 기반의 도메인 적응 방식과 차별화되는 접근 방식입니다. **잡음 자체의 분포를 다루는 것이 핵심**이며, 이를 통해 합성 데이터와 실제 데이터 간의 차이를 효과적으로 해소합니다.  **확산 모델(diffusion model)의 고유한 특성**을 활용하여 합성 및 실제 복원 이미지의 잡음 분포를 목표하는 깨끗한 이미지 분포와 일치시키는 것이 핵심 아이디어입니다.  이는 단순히 특징이나 픽셀 값의 차이만을 고려하는 것이 아니라, 잡음의 생성 과정 자체를 모델링하여 도메인 불일치를 해결하려는 시도로 볼 수 있습니다.  **채널 섞기(channel-shuffling) 및 잔차 교환 대조 학습(residual-swapping contrastive learning)** 전략을 통해 단순한 지름길 학습(shortcut learning)을 방지하고, 모델이 실제 데이터에 대한 일반화 능력을 향상시키는 데 기여합니다.  결론적으로, 잡음 공간 적응은 이미지 복원 분야에서 도메인 적응 문제를 해결하기 위한 새로운 패러다임을 제시하며, **효율적이고 안정적인 도메인 적응**을 가능하게 합니다.

#### Diffusion Model Loss
본 논문에서 제시된 **확산 모델 손실 함수(Diffusion Model Loss)**는 기존의 이미지 복원 방법론들이 가진 한계점, 즉 합성 데이터와 실제 데이터 간의 차이로 인한 일반화 성능 저하 문제를 해결하기 위해 고안되었습니다.  **합성 데이터와 실제 데이터의 복원 결과를 모두 목표 분포(깨끗한 이미지 분포)에 맞추도록** 유도하는 것이 핵심 아이디어입니다.  이는 확산 모델의 특성, 즉 조건부 입력(auxiliary conditional inputs)이 다단계 잡음 제거 과정에 미치는 영향을 활용하여 가능해집니다.  즉, 복원 네트워크가 생성한 합성 및 실제 이미지를 조건으로 하여 확산 모델의 잡음 예측 오차를 최소화하는 방식으로 손실 함수를 정의합니다.  **이를 통해 복원 네트워크는 합성 및 실제 데이터 모두에서 깨끗한 이미지 분포에 가까운 결과를 생성하도록 학습**됩니다.  단순히 합성 및 실제 이미지 간의 차이를 줄이는 것을 넘어, **두 데이터의 복원 결과를 모두 동일한 깨끗한 이미지 분포에 맞추는 점**이 기존 방법과의 중요한 차별점입니다.  하지만 이러한 접근 방식은 단순히 채널 정보나 픽셀 유사도에 의존하는 지름길 학습(shortcut learning) 문제를 야기할 수 있습니다. 따라서 채널 셔플링 및 잔차 교환 대조 학습(residual-swapping contrastive learning)과 같은 추가적인 전략을 통해 이러한 문제를 해결하고 있습니다.

#### Shortcut Mitigation
본 논문에서 제시된 방법은 합성 데이터와 실제 데이터 간의 차이를 해소하기 위해 노이즈 공간에서 도메인 적응을 수행합니다. 하지만, **단순히 합성 데이터와 실제 데이터의 차이를 구분하는 지름길(shortcut)**을 학습하는 문제가 발생할 수 있습니다. 이러한 문제를 완화하기 위해, 본 논문에서는 두 가지 주요 전략을 제시합니다. 첫째, **채널 셔플링(channel-shuffling)** 레이어를 도입하여 합성 및 실제 데이터의 채널 인덱스를 무작위로 섞어, 모델이 쉬운 방법으로 데이터를 구분하는 것을 어렵게 만듭니다. 둘째, **잔차 스와핑 대조 학습(residual-swapping contrastive learning)** 전략을 통해 모델이 쉬운 특징에 의존하는 것을 방지하고, 합성 및 실제 데이터 간의 경계를 모호하게 만듭니다. 이러한 전략들을 통해, 모델은 쉽게 구분할 수 있는 특징에 의존하지 않고, 합성 데이터와 실제 데이터 모두에서 의미있는 표현을 학습하게 됩니다. 결과적으로, **더욱 안정적이고 일반화된 성능**을 얻을 수 있습니다. 이러한 **지름길 완화 전략**은 합성 데이터만으로 학습하는 모델보다 실제 데이터에 대한 일반화 능력이 뛰어난 모델을 만드는 데 중요한 역할을 합니다.

#### Restoration Networks
본 논문에서 제시된 "복원 네트워크(Restoration Networks)"는 **합성 및 실제 이미지 데이터 모두에서 훈련되어 실제 환경에 대한 일반화 능력을 향상**시키는 것을 목표로 합니다.  **디퓨전 모델을 활용하여 합성 및 실제 이미지의 복원 결과를 모두 표적 분포(깨끗한 이미지 분포)에 맞추는 방식**으로 작동합니다. 네트워크는 단순한 구조일 수 있지만,  **디퓨전 손실(Diffusion Loss)을 통해 복원 성능을 최적화**할 수 있습니다.  이는 단순히 손실 함수만 최소화하는 것이 아니라, **디퓨전 모델의 고유한 특성을 활용하여 합성 데이터와 실제 데이터 간의 차이를 해소**하는 핵심 전략입니다.  **채널 셔플링(Channel-Shuffling) 및 잔차 교환 대조 학습(Residual-Swapping Contrastive Learning)**과 같은 전략을 통해 단순한 지름길 학습을 방지하고, 네트워크가 실제 데이터에 효과적으로 적응할 수 있도록 유도합니다. **결과적으로, 복원 네트워크는 다양한 이미지 복원 작업(denoising, deblurring, deraining)에 적용 가능하며, 효율적이고 일반화된 성능을 보장**합니다.

#### Future Works
본 논문은 노이즈 공간 도메인 적응을 이용한 이미지 복원 방법을 제시하며, 합성 데이터와 실제 데이터 간의 차이를 줄이는 데 성공하였습니다. **향후 연구 방향**으로는 다음과 같은 세 가지를 제시할 수 있습니다. 첫째, **다양한 종류의 이미지 복원 작업** (예: 초해상도, 컬러화)에 대한 적용 가능성을 검토하고, 각 작업에 맞는 최적의 노이즈 공간 도메인 적응 전략을 연구할 필요가 있습니다. 둘째, **더욱 효율적이고 강건한 모델**을 개발하는 데 초점을 맞춰야 합니다. 현재 제시된 방법은 복잡한 확산 모델을 필요로 하기 때문에, 경량화된 모델을 개발하여 실시간 처리에 적합하도록 만들어야 합니다. 마지막으로, **실제 환경에서 다양한 노이즈 및 왜곡**을 고려하여 모델의 일반화 성능을 더욱 향상시키는 연구가 필요합니다. 이를 위해 더욱 다양하고 현실적인 데이터셋을 구축하여 모델을 학습시키고, 다양한 노이즈 및 왜곡 상황에 대한 강건성을 평가해야 합니다. 이러한 추가적인 연구를 통해 본 논문에서 제시된 방법의 실용성과 적용 범위를 더욱 확장할 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2406.18516/x2.png)

> 🔼 그림 2는 제안된 방법의 학습 과정을 보여줍니다. 합성 데이터의 복원 결과는 반복적인 학습을 통해 기대되는 분포(깨끗한 이미지의 분포)에 점차 수렴해갑니다. 그러나 모델은 실제 데이터에서 지름길을 찾으려는 경향이 있습니다. 즉, 조건(복원된 이미지)과 짝을 이루는 깨끗한 이미지 간의 유사성을 활용하거나 채널 인덱스를 기억하여 실제 데이터를 처리합니다. 그 결과, 복원 네트워크는 실제 이미지의 고주파수 세부 정보를 손상시키고, 확산 모델은 이러한 정보를 무시하는 경향이 있습니다. 이러한 단점을 극복하기 위해 채널 섞기(channel-shuffling) 및 잔차 교환 대조 학습(residual-swapping contrastive learning) 전략이 제안됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: During the joint training, the restored synthetic images smoothly converge to the expected distribution over the epochs. However, the model tends to find a shortcut in real data by matching the similarity between the conditions and the paired clean image or remembering the channel index. Consequently, the restoration network learns to corrupt the high-frequency details in real-world images and the diffusion model tends to ignore them.
> </details>



![](https://arxiv.org/html/2406.18516/x3.png)

> 🔼 이 그림은 확산 모델에서 지름길 학습을 방지하기 위한 제안된 해결책을 보여줍니다.  구체적으로는, 합성 데이터와 실제 데이터의 조건들을 구별하기 어렵게 만들어, 모델이 쉬운 방법 대신 실제로 이미지 복원을 학습하도록 유도하는 전략들을 보여줍니다.  여기에는 채널 셔플링 레이어를 확산 모델에 통합하고 잔차 스왑 대조 학습 전략을 설계하는 것이 포함됩니다.  이러한 전략들은 합성 데이터와 실제 데이터 사이의 경계를 모호하게 만들어 모델이 쉽게 구별할 수 있는 특징에 의존하지 않도록 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: The proposed solution to eliminate the shortcut learning in diffusion.
> </details>



![](https://arxiv.org/html/2406.18516/x4.png)

> 🔼 그림 4는 Abdelhamed 등의 연구(2018)에서 제시된 SIDD 테스트 데이터셋을 사용하여 이미지 잡음 제거 작업에 대한 다양한 방법의 시각적 비교 결과를 보여줍니다. 그림은 입력 이미지와 여러 잡음 제거 방법(Vanilla, DANN, DSN, PixelDA, CyCADA, Ne2Ne, MaskedD, 그리고 제안된 방법(Ours))을 적용한 결과 이미지를 보여줍니다. 이를 통해 각 방법의 성능을 시각적으로 비교하고, 제안된 방법의 우수성을 보여줍니다.  특히, 제안된 방법은 세부적인 디테일을 잘 보존하면서 잡음을 효과적으로 제거하는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Visual comparison of the image denoising task on SIDD test dataset (Abdelhamed et al., 2018).
> </details>



![](https://arxiv.org/html/2406.18516/x5.png)

> 🔼 그림 5는 Wang et al. (2019)의 SPA 데이터셋과 Rim et al. (2020)의 RealBlur-J 데이터셋을 사용하여 이미지 제거 및 이미지 디블러링 작업에 대한 시각적 비교 결과를 보여줍니다.  이 그림은 다양한 방법(Vanilla, DANN, DSN, PixelDA, CyCADA, NLCL, Restormer, Ours, Ours-Ex)으로 복원된 이미지들을 보여주어 각 방법의 성능을 시각적으로 비교 분석할 수 있도록 합니다. SPA 데이터셋은 비에 젖은 이미지를, RealBlur-J 데이터셋은 흐릿한 이미지를 각각 다룹니다. 따라서 그림은 제안된 방법(Ours)이 다양한 종류의 이미지 손상에 대해 얼마나 효과적으로 복원하는지 보여주는 역할을 합니다. Ours-Ex는 제안된 방법의 확장된 버전을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Visual comparison of the image deraining and image deblurring tasks on SPA Wang et al. (2019) and RealBlur-J Rim et al. (2020) test datasets.
> </details>



![](https://arxiv.org/html/2406.18516/x6.png)

> 🔼 그림 6은 제안된 방법의 ablation study 결과를 보여줍니다. (a)~(e)는 각각 다른 설정(Noise Sampling Range, Channel Shuffling, Residual-Swapping Contrastive Learning 적용 유무)에서의 결과를 보여주고, (f)는 제안된 방법의 완전한 버전의 결과를 보여줍니다.  (f)에서 제안된 방법이 시각적으로 만족스러운 결과와 최고의 복원 성능을 달성함을 보여줍니다. 각 설정에서의 변화를 통해, 제안된 방법의 각 구성 요소가 최종 성능에 미치는 영향을 분석하고, 어떤 요소들이 시각적 품질과 복원 성능 향상에 중요한 역할을 하는지를 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Visual comparison results of ablation studies. The complete version (f) of the proposed method achieves the best restoration results with visually pleasant appearances.
> </details>



![](https://arxiv.org/html/2406.18516/x7.png)

> 🔼 이 그림은 제안된 방법의 확장성을 다양한 네트워크 구조에서 보여줍니다.  여러 가지 크기와 유형의 네트워크(Unet-T, Unet-S, Unet-B, Uformer-T, Uformer-S, Uformer-B)를 사용하여 실험을 진행했고, 제안된 방법이 네트워크의 복잡성에 관계없이 일관되게 성능 향상을 제공함을 보여줍니다. 특히, 네트워크의 복잡성이 증가함에 따라 제안된 방법의 성능 향상 효과가 더욱 두드러짐을 확인할 수 있습니다. 이는 제안된 방법이 다양한 네트워크에 적용 가능하고,  네트워크의 크기와 관계없이 일반화 성능을 향상시킬 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Scalability of the proposed method on different network architectures.
> </details>



![](https://arxiv.org/html/2406.18516/x8.png)

> 🔼 그림 8은 제안된 방법을 사용하여 실제 환경에서 얻은 데이터셋에 대한 시각적 결과를 보여줍니다. Plotz & Roth (2017)의 DND(Denoising) 데이터셋과 Yang et al. (2017)의 'Real-Internet'(Deraining) 데이터셋에 대한 결과를 포함합니다.  이 그림은 제안된 방법이 훈련 과정에서 보지 못한 데이터셋에도 일반화될 수 있음을 보여주는 중요한 증거를 제시합니다.  다양한 이미지 복원 작업에서 제안된 방법의 성능과 일반화 능력을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Visual results of the proposed method on unseen real-world datasets: the denoising test dataset DND (Plotz & Roth, 2017) and deraining test dataset ‘Real-Internet’ (Yang et al., 2017).
> </details>



![](https://arxiv.org/html/2406.18516/x9.png)

> 🔼 그림 A1은 서로 다른 도메인 적응(DA) 방법의 개요를 보여줍니다. (a) 특징 공간 DA는 소스 도메인과 타겟 도메인 간의 중간 특징을 정렬합니다. (b) 픽셀 공간 DA는 적대적 학습을 통해 소스 데이터를 타겟 도메인의 스타일로 변환합니다. (c) 제안된 잡음 공간 DA는 이미지 복원을 위해 특별히 설계되었습니다. 다단계 잡음 제거를 통해 소스 도메인과 타겟 도메인의 결과를 타겟 클린 이미지 분포에 점진적으로 적응시킵니다. 특히, 기능 네트워크는 이미지 복원의 맥락에서 복원 네트워크를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure A1: Overview of different domain adaptation (DA) approaches. (a) Feature-space DA aligns the intermediate features across source and target domains. (b) Pixel-space DA translates source data to the “style' of the target domain through adversarial learning. (c) The proposed noise-space DA is specifically designed for image restoration. It gradually adapts the results from both source and target domains to the target clean image distribution, via multi-step denoising. Particularly, the function network represents a restoration network in the context of image restoration.
> </details>



![](https://arxiv.org/html/2406.18516/x10.png)

> 🔼 그림 A2는 제안된 방법이 세부적인 질감과 고주파수 구성요소를 복원하는 데 효과적임을 보여줍니다. 제안된 방법은 다양한 복원 네트워크에 확장 가능한 일반적인 학습 전략으로, 네트워크 복잡도가 증가함에 따라 성능 향상을 가져옵니다. (Ours*)는 더욱 복잡한 네트워크를 사용한 결과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure A2: Visual results on detailed textures and high-frequency components. The proposed method serves as a general learning strategy for the image restoration task, offering scalability across different restoration networks. It also enables performance improvements as the complexity of the restoration network increases (Ours*).
> </details>



![](https://arxiv.org/html/2406.18516/x11.png)

> 🔼 그림 A3은 Abdelhamed 등의 연구(2018)에서 제시된 SIDD 테스트 데이터셋을 사용하여 이미지 잡음 제거 작업에 대한 시각적 비교를 보여줍니다.  Vanilla(기본 모델), DANN, DSN, PixelDA, CyCADA, Ne2Ne, MaskedD, Ours, Ours-Ex 등 다양한 방법의 결과를 보여주며 각 방법의 이미지 잡음 제거 성능을 시각적으로 비교 분석할 수 있도록 합니다. 각 이미지는 확대된 부분을 통해 세부적인 차이를 더욱 명확하게 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure A3: Visual comparison of the image denoising task on SIDD test dataset (Abdelhamed et al., 2018).
> </details>



![](https://arxiv.org/html/2406.18516/x12.png)

> 🔼 그림 A4는 Wang 등의 논문(2019)에서 제시한 SPA 테스트 데이터셋을 사용하여 이미지 제비 제거 작업에 대한 다양한 방법의 시각적 비교 결과를 보여줍니다.  Vanilla, DANN, DSN, PixelDA, CyCADA, NLCL, Restormer, Ours, Ours-Ex 등 여러 알고리즘의 결과를 보여주며, 각 알고리즘의 비, 눈, 구름 등이 제거된 후 이미지의 질을 시각적으로 비교할 수 있습니다. 특히, 제안된 방법(Ours)과 그 확장(Ours-Ex)의 결과는 기존 방법들에 비해 개선된 성능을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure A4: Visual comparison of the image deraining task on SPA test dataset (Wang et al., 2019).
> </details>



![](https://arxiv.org/html/2406.18516/x13.png)

> 🔼 그림 A5는 RealBlur-J 데이터셋(Rim 등, 2020)의 테스트 이미지를 사용하여 수행된 이미지 탈블러링 작업에 대한 다양한 방법들의 시각적 비교 결과를 보여줍니다.  각 열은 다른 방법(Vanilla, DANN, PixelDA, CyCADA, SelfDeblur, Ours, Ours-Ex)을 나타내고, 각 행은 서로 다른 테스트 이미지를 나타냅니다.  Vanilla는 기본 U-Net 모델의 결과이며, 나머지는 각각 다른 도메인 적응 방법 또는 탈블러링 기법들을 나타냅니다. Ours는 본 논문에서 제안하는 방법의 결과이고, Ours-Ex는 제안된 방법의 확장된 버전(unpaired condition)의 결과입니다. 그림을 통해 각 방법의 탈블러링 성능을 시각적으로 비교하여 어떤 방법이 더 선명하고 왜곡이 적은 결과를 생성하는지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure A5: Visual comparison of the image deblurring task on RealBlur-J (Rim et al., 2020) test dataset.
> </details>



![](https://arxiv.org/html/2406.18516/x14.png)

> 🔼 그림 A6은 제안된 방법을 DND 실제 환경 노이즈 제거 테스트 데이터셋 (Plotz & Roth, 2017)에 적용한 시각적 결과를 보여줍니다.  입력 이미지와 제안된 방법을 통해 복원된 이미지를 비교하여, 제안된 방법의 노이즈 제거 성능을 다양한 이미지에서 시각적으로 확인할 수 있습니다. 특히, 세부적인 텍스처와 고주파수 성분을 얼마나 잘 복원하는지에 대한 비교가 가능합니다.  다양한 물체와 배경을 가진 이미지들을 사용하여 실제 환경 데이터셋에서의 성능을 보다 포괄적으로 평가하고 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure A6: Visual results of the proposed method on DND real-world denoising test dataset (Plotz & Roth, 2017).
> </details>



![](https://arxiv.org/html/2406.18516/x15.png)

> 🔼 그림 A7은 제안된 방법을 DND 실제 환경 노이즈 제거 테스트 데이터셋(Plotz & Roth, 2017)에 적용한 시각적 결과를 보여줍니다. 이 그림은 다양한 유형의 이미지(예: 조각상, 꽃, 나사못 등)에 대한 입력 이미지와 제안된 방법을 통해 복원된 이미지를 비교하여, 제안된 방법의 노이즈 제거 성능을 시각적으로 보여줍니다.  입력 이미지는 다양한 수준의 노이즈를 포함하고 있으며, 제안된 방법은 이러한 노이즈를 효과적으로 제거하여 원본 이미지에 가까운 결과를 얻는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure A7: Visual results of the proposed method on DND real-world denoising test dataset (Plotz & Roth, 2017).
> </details>



![](https://arxiv.org/html/2406.18516/x16.png)

> 🔼 그림 A8은 제안된 방법을 'Real-Internet' 실제 세계 강우 제거 테스트 데이터셋(Yang et al., 2017)에 적용한 시각적 결과를 보여줍니다.  이 그림은 다양한 실제 환경에서 촬영된 사진들에 적용된 제안된 모델의 강우 제거 성능을 보여주는 여러 예시들을 포함하고 있습니다.  각 예시는 원본 이미지(Input)와 제안된 방법을 적용한 후의 결과 이미지(Ours)를 비교하여, 모델이 얼마나 효과적으로 비, 즉 강우를 제거하는지 보여줍니다.  이를 통해 제안된 모델의 실제 환경 데이터에 대한 일반화 성능을 시각적으로 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure A8: Visual results of the proposed method on ‘Real-Internet’ real-world deraining test dataset (Yang et al., 2017).
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Metrics | Vanilla | DANN | DSN | PixelDA | CyCADA | NLCL | Restormer | Ours |
|---|---|---|---|---|---|---|---|---|
| Space | - | Feature | Feature | Pixel | Feature&Pixel | - | - | Noise |
| Train Data | _syn_ | _both_ | _both_ | _both_ | _both_ | _real_ | _syn_ | _both_ |
| PSNR ↑ | 33.04 | 32.21 | 33.56 | 30.20 | 32.21 | 20.68 | 34.17 | 34.39 |
| SSIM ↑ | 0.9540 | 0.9443 | 0.9552 | 0.9288 | 0.9442 | 0.8412 | 0.9492 | 0.9571 |
| LPIPS ↓ | 0.0477 | 0.0597 | 0.0512 | 0.0758 | 0.0597 | 0.0967 | 0.0488 | 0.0462 |{{< /table-caption >}}
> 🔼 표 2는 Wang et al.(2019)에서 제시한 SPA 테스트 데이터셋을 사용하여 이미지 제거 작업에 대한 정량적 평가 결과를 보여줍니다.  표에는 다양한 이미지 복원 방법(Vanilla, DANN, DSN, PixelDA, CyCADA, NLCL, Restormer, Ours)의 성능을 PSNR, SSIM, LPIPS 세 가지 지표를 사용하여 비교 분석한 결과가 제시되어 있습니다.  각 방법의 훈련 데이터 (합성 데이터, 실제 데이터, 합성 및 실제 데이터 모두) 종류에 따른 성능 차이도 보여줍니다.  이를 통해 다양한 방법들의 이미지 제거 성능을 객관적으로 비교하고, 제안된 방법(Ours)의 우수성을 수치적으로 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Quantitative evaluation of the image deraining task on SPA test dataset (Wang et al., 2019).
> </details>

{{< table-caption >}}
| Metrics | Vanilla | DANN | DSN | PixelDA | CyCADA | SelfDeblur | VDIP | Ours |
|---|---|---|---|---|---|---|---|---|
| Space | - | Feature | Feature | Pixel | Feature&Pixel | - | - | Noise |
| Train Data | _syn_ | _both_ | _both_ | _both_ | _both_ | _real_ | _real_ | _both_ |
| PSNR ↑ | 26.27 | 26.11 | 26.28 | 24.71 | 26.36 | 23.23 | 24.89 | **26.46** |
| SSIM ↑ | 0.8012 | 0.7945 | 0.8003 | 0.7646 | 0.7936 | 0.6699 | 0.7404 | **0.8048** |
| LPIPS ↓ | 0.1389 | 0.1345 | 0.1380 | 0.1583 | 0.1340 | **0.1340** | 0.1589 | 0.1363 |{{< /table-caption >}}
> 🔼 표 3은 RealBlur-J 테스트 데이터셋(Rim et al., 2020)을 사용한 이미지 디블러링 작업에 대한 정량적 평가 결과를 보여줍니다.  여러 이미지 복원 방법(Vanilla, DANN, DSN, PixelDA, CyCADA, SelfDeblur, VDIP, Ours)의 성능을 PSNR, SSIM, LPIPS 지표를 통해 비교 분석합니다. 각 방법은 합성 데이터, 실제 데이터(GT 없음), 합성 및 실제 데이터(GT 없음)로 훈련된 모델의 결과를 보여줍니다.  이 표는 제안된 방법의 성능을 기존 방법과 비교하여  디블러링 작업에서의 효과를 객관적으로 평가하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Quantitative evaluation of the image deblurring task on RealBlur-J test dataset (Rim et al., 2020).
> </details>

{{< table-caption >}}
| Exp. | Noise Sampling Range [1, 100] | Noise Sampling Range [900, 1000] | Noise Sampling Range [1, 1000] | Strategy CS | Strategy RS | Metrics PSNR↑ | Metrics SSIM↑ |
|---|---|---|---|---|---|---|---|
| (a) |  |  |  |  |  | 26.58 | 0.6132 |
| (b) | ✓ |  |  |  |  | 16.77 | 0.6070 |
| (c) |  | ✓ |  |  |  | 27.36 | 0.6590 |
| (d) |  |  | ✓ |  |  | 32.07 | 0.8706 |
| (e) |  |  | ✓ | ✓ |  | 32.91 | 0.9082 |
| (f) (Ours) |  |  | ✓ | ✓ | ✓ | **34.71** | **0.9202** |
| (Only *syn*) |  |  | ✓ |  |  | 26.83 | 0.6286 |
| (Only *real*) |  |  | ✓ |  |  | 32.60 | 0.8831 |{{< /table-caption >}}
> 🔼 표 4는 SIDD 이미지 제거 데이터셋에서 다양한 네트워크에 대한 에이블레이션 연구 결과를 보여줍니다. 이 표는 제안된 채널 셔플링 레이어(CS)와 잔차 스와핑 대조 학습 전략(RS)을 사용한 경우와 사용하지 않은 경우의 성능을 비교하여 각 구성 요소의 효과를 분석합니다.  구체적으로, 다양한 노이즈 샘플링 범위(예: [1, 100], [900, 1000], [1, 1000])에서의 성능을 비교 분석하고,  CS와 RS 전략을 적용했을 때와 적용하지 않았을 때의 PSNR과 SSIM 값을 제시하여  모델의 성능 향상에 기여하는 요소를 명확하게 보여줍니다. 또한, 합성 데이터만 사용하거나 실제 데이터만 사용했을 때의 결과도 함께 제시하여,  제안된 방법의 성능 향상에 합성 데이터와 실제 데이터 모두가 필수적인 요소임을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Ablation studies of variant networks on the SIDD test image denoising dataset. CS and RS represent the proposed channel shuffling layer and residual-swapping contrastive learning strategies, respectively.
> </details>

{{< table-caption >}}
| Metrics | C2N | AP-BSN† | Ours | Ours* |
|---|---|---|---|---|
| Space | - | - | Noise | Noise |
| Type | SS | SS | DA | DA |
| Train Data | both | real | both | both |
| PSNR ↑ | 35.35 | 34.90 | 34.71 | 35.52 |
| SSIM ↑ | 0.9370 | 0.9000 | 0.9202 | 0.9297 |{{< /table-caption >}}
> 🔼 표 5는 제안된 도메인 적응 전략을 사용하여 더 깊은 레이어를 가진 고급 복원 네트워크를 사용한 결과를 보여줍니다.  SS는 자가 지도 학습 방식을, DA는 도메인 적응 방식을 나타냅니다.  †는 blind-spot 네트워크에 비대칭 픽셀 셔플 다운샘플링을 사용했음을 의미합니다.  즉, 표는 제안된 방법의 확장성을 보여주는 다양한 네트워크 구조(U-Net, Uformer)와 다양한 학습 방법(자가 지도 학습, 도메인 적응)에 대한 성능 비교 결과를 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Ours* denotes using a more advanced restoration network with deeper layers, trained by our domain adaptation strategy. SS and DA represent the self-supervised and domain adaptation methods, respectively. † The asymmetric pixel-shuffle downsampling for the blind-spot network is exploited.
> </details>

{{< table-caption >}}
| Metrics | C2N | AP-BSN | Restormer | Selfdeblur | MaskedD | VDIP | Ours | Ours* |
|---|---|---|---|---|---|---|---|---|
| Parameter | 164.57 | 3.10 | 26.09 | 3.10 | 12.00 | 3.00 | 8.56 | 65.19 |
| GMACs | 280.48 | 60.62 | 35.24 | 23.83 | 188.03 | 23.77 | 12.48 | 22.46 |{{< /table-caption >}}
> 🔼 표 A1은 제안된 방법(Ours)과 쌍을 이루지 않은 조건의 확장(Ours-Ex)에 대한 정량적 지표를 보여줍니다.  PSNR, SSIM, LPIPS 세 가지 지표를 사용하여 결과를 나타내며, 각 과제(denoising, deraining, deblurring)에 대한 최고 및 두 번째로 좋은 점수는 강조 표시되어 있습니다. 이 표는 제안된 방법의 성능을 다양한 조건에서 비교 분석하는 데 사용됩니다.  쌍을 이루지 않은 조건에서도 제안된 방법이 우수한 성능을 유지함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table A1: Quantitative metrics of the proposed method (Ours) and its extension on unpaired condition case (Our-Ex). The results are formed with PSNR/SSIM/LPIPS. The best and second best scores are highlighted and underlined.
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