---
title: "The GAN is dead; long live the GAN! A Modern GAN Baseline"
summary: "R3GAN: 단순하지만 강력한 최신 GAN 기준 모델!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Generation", "🏢 Brown University",]
showSummary: true
date: 2025-01-09
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.05441 {{< /keyword >}}
{{< keyword icon="writer" >}} Yiwen Huang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-10 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.05441" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.05441" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/the-gan-is-dead-long-live-the-gan-a-modern" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

GAN(Generative Adversarial Network)은 이미지 생성 분야에서 널리 사용되지만, **훈련의 어려움과 불안정성**으로 인해 많은 제약이 있었습니다. 기존 연구는 임의적인 트릭들을 사용하여 이러한 문제를 해결하려 했지만, 이론적 기반이 부족하고 일반화가 어려웠습니다.  이 논문은 이러한 문제를 해결하기 위해  **새로운 연구가 필요함**을 시사합니다.

본 논문에서는 **수학적으로 안정성을 보장하는 새로운 GAN 손실 함수**를 제시하고, **최신 CNN 아키텍처**를 적용하여 간소화된 GAN 기준 모델인 R3GAN을 개발했습니다.  R3GAN은 기존의 복잡한 트릭들을 제거하고, 다양한 데이터셋에서 기존 최첨단 모델들을 능가하는 성능을 보임으로써, GAN 훈련의 어려움에 대한 기존의 인식을 바꾸고, **더욱 효율적이고 안정적인 GAN 연구**를 위한 새로운 가능성을 제시합니다.  단순함에도 불구하고 뛰어난 성능을 보이는 R3GAN은 향후 GAN 연구 및 다양한 생성 모델 개발에 중요한 기준 모델이 될 것으로 기대됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 수학적으로 안정적이고 효율적인 새로운 GAN 손실 함수를 도출했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 기존의 GAN 트릭 없이도 최첨단 성능을 달성하는 간소화된 GAN 기준 모델(R3GAN)을 개발했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} FFHQ, ImageNet, CIFAR, Stacked MNIST 데이터셋에서 StyleGAN2 및 기타 최첨단 GAN, 확산 모델을 능가하는 성능을 입증했습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **GAN 훈련의 어려움에 대한 기존 통념을 뒤집고**, 현대적인 기법을 사용하여 **간단하면서도 성능이 뛰어난 GAN 기준 모델 (R3GAN)**을 제시함으로써 GAN 연구에 중요한 전환점을 마련합니다.  **수학적 분석과 실험 결과를 통해 개선된 손실 함수와 최신 아키텍처의 효과**를 보여주며, GAN의 확장성과 응용 가능성을 높였습니다. 이는 GAN 분야의 발전과 다양한 생성 모델 연구에 큰 영향을 미칠 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.05441/x3.png)

> 🔼 그림 1은 서로 다른 목적 함수를 사용하여 GAN을 학습시키는 동안 생성기(G)의 손실 값을 보여줍니다.  R1 정규화만 사용할 경우 어떤 목적 함수를 사용하더라도 학습이 발산하지만, R1과 R2 정규화를 모두 사용하면 학습이 성공적으로 수렴함을 보여줍니다.  Lee 등(2021)의 연구에서도 R1 정규화만 사용했을 때 수렴 실패가 보고된 바 있습니다.  이 그림은 RpGAN의 안정성과 R1 및 R2 정규화의 중요성을 시각적으로 보여주는 중요한 결과를 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Generator G𝐺Gitalic_G loss for different objectives over training. Regardless of which objective is used, training diverges with only R1subscript𝑅1R_{1}italic_R start_POSTSUBSCRIPT 1 end_POSTSUBSCRIPT and succeeded with both R1subscript𝑅1R_{1}italic_R start_POSTSUBSCRIPT 1 end_POSTSUBSCRIPT and R2subscript𝑅2R_{2}italic_R start_POSTSUBSCRIPT 2 end_POSTSUBSCRIPT. Convergence failure with only R1subscript𝑅1R_{1}italic_R start_POSTSUBSCRIPT 1 end_POSTSUBSCRIPT was noted by Lee et al. [42].
> </details>





{{< table-caption >}}
| Loss | # modes ↑ | D<sub>KL</sub> ↓ |
|---|---|---|
| RpGAN +R<sub>1</sub>+R<sub>2</sub> | **1000** | **0.0781** |
| GAN +R<sub>1</sub>+R<sub>2</sub> | 693 | 0.9270 |
| RpGAN +R<sub>1</sub> | Fail | Fail |
| GAN +R<sub>1</sub> | Fail | Fail |{{< /table-caption >}}

> 🔼 이 표는 StyleGAN2 기반 모델을 단순화 및 현대화한 결과를 FFHQ-256 데이터셋에서 평가한 것입니다. StyleGAN2의 여러 기능을 제거하고 최신 아키텍처를 적용하여 성능을 개선하는 과정을 보여줍니다.  각 단계별(StyleGAN2, 기능 제거, 손실 함수 개선, 네트워크 현대화) FID(Fréchet Inception Distance) 점수 변화를 통해 모델의 단순화 및 개선 효과를 정량적으로 비교 분석합니다.  FID 점수는 이미지 생성 품질을 측정하는 지표로, 낮을수록 좋은 성능을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Effect of our simplification and modernization efforts evaluted on FFHQ-256.
> </details>





### In-depth insights


#### RpGAN Stability
본 논문에서 제시된 RpGAN의 안정성 분석은 기존 GAN의 한계를 극복하기 위한 중요한 시도입니다. **기존 Relativistic GAN의 모드 붕괴 문제를 해결하기 위해 RpGAN이 제안되었지만, 이 또한 수렴성을 보장하지 못한다는 점이 확인되었습니다.**  따라서, **RpGAN에 제로-센터드 그래디언트 페널티(R1, R2)를 추가하여 안정성을 확보하고 수렴성을 증명한 것이 핵심입니다.** 이를 통해 기존 GAN에서 사용되던 임의적인 트릭들을 배제하고 현대적인 네트워크 구조를 도입할 수 있는 토대를 마련하였습니다. **수학적 분석을 통해 R1, R2의 추가가 지역적 수렴성을 보장함을 증명**함으로써, RpGAN의 안정성 향상이 단순한 경험적 결과가 아닌 이론적 근거를 가지고 있음을 강조합니다. 이는 GAN 연구에 있어서 중요한 이정표가 될 수 있습니다.

#### Modern GAN Design
본 논문은 현대적인 GAN 설계에 대한 깊이 있는 통찰력을 제공합니다. **기존 GAN의 한계점을 극복하기 위해** 제안된 R3GAN은 과도한 경험적 트릭 없이도 우수한 성능을 달성합니다. 이는 **수학적으로 엄밀하게 정의된 손실 함수**와 **최신 아키텍처**의 조합 덕분입니다. 특히, R3GAN은 안정적인 훈련을 보장하고 모드 붕괴 문제를 해결하는데 탁월한 성능을 보입니다.  **단순성과 효율성을 중시하는 설계 철학**은 현대적인 컴퓨터 비전 기술을 효과적으로 적용하고, 이전 GAN의 복잡성을 제거하여 더욱 간결하고 이해하기 쉬운 모델을 구축하는데 기여합니다. **다양한 데이터셋에 대한 실험 결과**는 R3GAN의 우수성을 입증하며, 향후 GAN 연구에 새로운 방향을 제시합니다. 이러한 접근 방식은 **간결성과 강력한 성능**을 동시에 추구하는 현대적 GAN 설계의 새로운 기준을 제시하며,  향상된 안정성과 다양성을 통해 GAN의 잠재력을 더욱 넓힐 것으로 기대됩니다.

#### Empirical Analysis
본 논문의 가상의 "실증 분석" 부분은 **다양한 데이터셋에 걸쳐 제안된 GAN의 성능을 평가하는 데 중점**을 두었을 것입니다.  **FFHQ, ImageNet, CIFAR-10, Stacked MNIST와 같은 표준 이미지 데이터셋**을 사용하여 정량적 지표(예: FID, precision, recall)를 통해 모델의 성능을 측정하고, 다른 최첨단 GAN 및 확산 모델과 비교했을 것입니다. 이러한 실험 결과는 **제안된 방법의 우수성을 입증하고, 기존 방법의 한계를 극복**하는 데 기여했을 것입니다.  **모드 붕괴 및 수렴 실패와 같은 GAN 훈련의 어려움을 해결**하기 위해 사용된 기법들의 효과를 분석하고, 이를 통해 **더욱 안정적이고 효율적인 GAN 훈련 전략**을 제시했을 것입니다.  또한,  **다양한 하이퍼파라미터 설정 및 네트워크 아키텍처 변화**에 따른 모델 성능 변화를 분석하여 최적의 설정을 도출하는 과정 또한 포함되었을 것입니다.  **정량적 결과 외에도, 생성된 이미지의 질적 평가**를 통해 모델의 성능을 보다 포괄적으로 분석하고, 향후 연구 방향을 제시했을 것으로 예상됩니다.

#### R3GAN Baseline
본 논문에서 제시된 R3GAN Baseline은 **기존 GAN의 복잡성을 줄이고 성능을 개선**하기 위한 현대적인 접근 방식을 보여줍니다.  **단순화된 네트워크 구조**와 **수정된 손실 함수**를 통해 기존의 어려운 GAN 훈련 과정의 문제점을 해결하고자 하였으며, 이는 **모드 붕괴 및 수렴 실패**와 같은 문제들을 효과적으로 완화하는 데 기여합니다. 특히 **RpGAN 손실 함수에 R1 및 R2 제약 조건을 추가**하여 수렴성을 보장하고 다양성을 확보하는 데 성공하였습니다. 실험 결과는 FFHQ, ImageNet, CIFAR 및 Stacked MNIST 데이터셋에서 R3GAN이 기존 StyleGAN2를 능가하며, 최첨단 GAN 및 확산 모델과도 비교 우위를 보임을 보여줍니다.  **단순성과 성능을 동시에 확보**한 R3GAN Baseline은 GAN 연구의 새로운 기준을 제시하며, 향후 GAN 아키텍처 설계에 중요한 영향을 미칠 것으로 예상됩니다.

#### Future GANs
미래의 GAN은 **더욱 안정적이고 효율적인 훈련 방식**을 통해 더욱 발전할 것입니다. 이는 수학적으로 증명된 안정성을 갖는 손실 함수의 개발과 최신 컴퓨터 비전 기술을 활용한 **최신 아키텍처 채택**으로 가능해질 것입니다. 또한, **기존 GAN의 단점을 해결**하기 위한 다양한 시도와 더불어, **다양한 응용 분야**에서의 활용이 더욱 확대될 것입니다. **생성 모델의 질적 향상**을 위한 연구도 지속될 것이며, **모드 붕괴 및 과적합 문제**를 해결하는 새로운 기법들이 등장할 것입니다.  **이미지 편집, 제어 가능한 생성, 스타일 변환 등 다양한 작업**에 GAN이 활용될 것이며, 이를 위해 **특정 작업에 특화된 GAN 아키텍처**가 개발될 수 있습니다. 또한, GAN과 다른 생성 모델과의 결합을 통한 **하이브리드 접근 방식**도 활발히 연구될 것으로 예상됩니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.05441/)

> 🔼 그림 2는 서로 다른 GAN 손실 함수를 사용했을 때 StackedMNIST 데이터셋에서의 모드 커버리지 결과를 보여줍니다. StackedMNIST는 1000개의 고유한 모드(분포의 다양한 양상)를 가지고 있습니다. 각 손실 함수에 대해 학습 과정이 조기에 발산했는지 여부를 나타내는 'Fail' 표시와 함께, 생성된 샘플이 데이터셋의 얼마나 많은 모드를 커버하는지를 보여줍니다.  모드 커버리지가 1000에 가까울수록 생성 모델의 다양성이 높다는 것을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: StackedMNIST [46] result for each loss function. The maximum possible mode coverage is 1000. “Fail” indicates that training diverged early on.
> </details>



![](https://arxiv.org/html/2501.05441/extracted/6122118/figures/qualitative/ffhq64.png)

> 🔼 그림 3은 이미지 생성을 위한 생성자(G)와 판별자(D)의 아키텍처를 비교한 그림입니다.  StyleGAN2는 노이즈 벡터 z를 중간 스타일 공간 W로 매핑하는 네트워크를 사용하는 반면, 본 논문의 모델은 최소한의 작동 모델에 필요하지 않기 때문에 기존 생성자를 사용합니다. StyleGAN2의 구성 요소는 복잡한 계층을 가지고 있지만, 2015년 ConvNet 아키텍처를 기반으로 하여 비교적 단순합니다.  판별자에서는 ResNet의 아이덴티티 매핑 원칙도 위반됩니다.  반면, 본 논문에서는 불필요한 기법들을 제거하고 아키텍처를 현대화하여 깔끔한 계층과 더욱 강력한 ConvNet 아키텍처를 갖춘 설계를 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Architecture comparison. For image generation, G𝐺Gitalic_G and D𝐷Ditalic_D are often both deep ConvNets with either partially or fully symmetric architectures. (a) StyleGAN2 [31] G𝐺Gitalic_G uses a network to map noise vector z𝑧zitalic_z to an intermediate style space 𝒲𝒲\mathcal{W}caligraphic_W. We use a traditional generator as style mapping is not necessary for a minimal working model. (b) StyleGAN2’s building blocks have intricate layers but are themselves simple, with a ConvNet architecture from 2015 [38, 73, 16]. ResNet’s identity mapping principle is also violated in the discriminator. (c) We remove tricks and modernize the architecture. Our design has clean layers with a more powerful ConvNet architecture.
> </details>



![](https://arxiv.org/html/2501.05441/extracted/6122118/figures/qualitative/cifar-10-000222209.jpg)

> 🔼 그림 4는 제시된 논문에서 제안된 R3GAN 모델(Config E)을 사용하여 생성된 FFHQ-256 데이터셋의 이미지 샘플들을 보여줍니다.  이 그림은 R3GAN이 얼마나 사실적이고 다양한 이미지들을 생성할 수 있는지 보여주는 시각적 증거를 제공합니다.  다양한 연령, 인종, 성별, 표정 등의 사람 얼굴 이미지들이 포함되어 있어 R3GAN의 성능을 효과적으로 나타냅니다. 이미지의 질과 다양성은 논문의 주요 주장 중 하나인 R3GAN의 우수한 성능을 뒷받침하는 중요한 요소입니다.
> <details>
> <summary>read the caption</summary>
> Figure 4:  FFHQ-256. * denotes models that leak ImageNet features.
> </details>



![](https://arxiv.org/html/2501.05441/extracted/6122118/figures/qualitative/imgnet-32-000681275.jpg)

> 🔼 그림 5는 본 논문에서 제안하는 R3GAN 모델의 FFHQ-64 데이터셋에 대한 이미지 생성 결과를 보여줍니다. FFHQ-64는 64x64 해상도의 고해상도 얼굴 이미지 데이터셋입니다. 이 그림은 R3GAN이 생성한 다양한 얼굴 이미지들을 보여주며, 모델의 이미지 생성 품질과 다양성을 시각적으로 평가하는 데 도움이 됩니다. 이미지들은 다양한 연령대, 성별, 인종의 사람들을 포함하고 있으며, 자연스러운 표정과 세부적인 특징을 잘 보여주는 것으로 보입니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: FFHQ-64.
> </details>



![](https://arxiv.org/html/2501.05441/extracted/6122118/figures/qualitative/imgnet64.png)

> 🔼 이 그림은 CIFAR-10 데이터셋에서의 GAN 모델 성능을 보여줍니다. 가로축은 모델의 파라미터 수 (백만 단위), 세로축은 FID-50K 점수 (낮을수록 좋음)를 나타냅니다. 로그 스케일을 사용하여 파라미터 수의 넓은 범위를 표현합니다. 이 그래프는 다양한 GAN 모델의 파라미터 수와 성능 간의 관계를 시각적으로 보여주어, 모델의 크기가 성능에 미치는 영향을 분석하는 데 유용하게 사용될 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Millions of parameters vs. FID-50K (log scale) on CIFAR-10. Lower is better.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Configuration | FID↓ | G #params | D #params |
|---|---|---|---| 
| StyleGAN2 | 7.516 | 24.767M | 24.001M |
| Stripped StyleGAN2 |  |  |  |  
| - z normalization <br> - Minibatch stddev <br> - Equalized learning rate <br> - Mapping network <br> - Style injection <br> - Weight mod / demod <br> - Noise injection <br> - Mixing regularization <br> - Path length regularization <br> - Lazy regularization | 12.46 | 18.890M | 23.996M |
| Well-behaved Loss | 12.46 | 18.890M | 23.996M |
| + RpGAN loss | 11.77 | 18.890M | 23.996M |
| + R<sub>2</sub> gradient penalty | 11.65 | 18.890M | 23.996M |
| ConvNeXt-ify pt. 1 |  |  |  |  
| + ResNet-ify G & D | 10.17 | 23.400M | 23.282M |
| - Output skips | 9.950 | 23.378M | 23.282M |
| ConvNeXt-ify pt. 2 |  |  |  |  
| + ResNeXt-ify G & D | 7.507 | 23.188M | 23.091M |
| + Inverted bottleneck | 7.045 | 23.058M | 23.010M |{{< /table-caption >}}
> 🔼 이 표는 StackedMNIST 데이터셋에서 각 손실 함수의 모드 적합도를 보여줍니다. StackedMNIST는 1000개의 고유한 모드를 가진 합성 데이터셋입니다. 각 손실 함수에 대해 표는 달성된 모드 수와 역 KL 발산을 나타냅니다. 역 KL 발산은 생성된 분포와 실제 분포 사이의 차이를 측정하는 지표입니다. 낮은 역 KL 발산 값은 생성된 분포가 실제 분포와 더 유사함을 나타냅니다.  '실패'는 학습이 조기에 발산했음을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: StackedMNIST 1000-mode coverage.
> </details>

{{< table-caption >}}
| - z normalization
| - Minibatch stddev
| - Equalized learning rate
| - Mapping network
| - Style injection
| - Weight mod / demod
| - Noise injection
| - Mixing regularization
| - Path length regularization
| - Lazy regularization{{< /table-caption >}}
> 🔼 표 3은 CIFAR-10 데이터셋에서 다양한 GAN 모델들의 성능을 보여줍니다. FID(Fréchet Inception Distance) 점수를 통해 모델의 이미지 생성 품질을 평가합니다. FID 점수가 낮을수록 이미지 품질이 높음을 나타냅니다. 표에는 각 모델의 FID 점수와 모델의 생성 이미지 수(NFE)를 함께 제시하여 모델의 성능과 효율성을 비교 분석합니다. StyleGAN-XL 과 같은 일부 모델은 ImageNet 특징 누출(feature leakage) 현상을 보이며 FID 점수를 인위적으로 높입니다. 본 논문의 R3GAN 모델은 ImageNet 특징 누출 없이도 다른 최첨단 GAN 모델들에 비해 경쟁력 있는 성능을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: CIFAR-10 performance.
> </details>

{{< table-caption >}}
|---|---|---|---|---|---|---|---| 
|![Refer to caption](https://arxiv.org/html/2501.05441/image-64.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-65.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-66.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-67.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-128.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-69.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-70.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-71.jpg)| 
|![Refer to caption](https://arxiv.org/html/2501.05441/image-72.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-73.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-74.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-75.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-76.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-77.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-78.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-79.jpg)| 
|![Refer to caption](https://arxiv.org/html/2501.05441/image-80.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-81.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-82.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-83.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-84.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-85.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-86.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-87.jpg)| 
|![Refer to caption](https://arxiv.org/html/2501.05441/image-88.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-89.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-90.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-91.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-92.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-93.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-94.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-95.jpg)| 
|![Refer to caption](https://arxiv.org/html/2501.05441/image-96.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-97.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-98.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-99.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-100.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-101.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-102.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-103.jpg)| 
|![Refer to caption](https://arxiv.org/html/2501.05441/image-104.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-105.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-106.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-107.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-108.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-109.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-110.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-111.jpg)| 
|![Refer to caption](https://arxiv.org/html/2501.05441/image-112.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-113.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-114.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-115.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-116.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-117.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-118.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-119.jpg)| 
|![Refer to caption](https://arxiv.org/html/2501.05441/image-120.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-121.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-122.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-123.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-124.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-125.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-126.jpg)|![Refer to caption](https://arxiv.org/html/2501.05441/image-127.jpg)| {{< /table-caption >}}
> 🔼 표 9는 각 실험에 대한 하이퍼파라미터를 보여줍니다. EMA(Exponential Moving Average)의 감쇠 계수 β는  β=0.5^(Minibatch size/EMA half-life) 공식을 사용하여 계산할 수 있습니다. 예를 들어 CIFAR-10의 경우 EMA β는 0.5^(512/(5x10^6)) ≈ 0.9999 입니다.  이 표는 Stacked MNIST, CIFAR-10, FFHQ, ImageNet 데이터셋에 대한 다양한 하이퍼파라미터 설정(해상도, 배치 크기, 학습률,  EMA 수명 등)을 보여주어, 각 실험의 재현성을 높이는 데 도움이 됩니다.  각 하이퍼파라미터의 초기값과 목표값 사이의 코사인 스케줄을 사용하여 학습 초기에 빠른 수렴을 유도했습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Hyperparameters for each experiment. The decay factor β𝛽\betaitalic_β of EMA can be obtained using the formula β=0.5Minibatch sizeEMA half-life𝛽superscript0.5Minibatch sizeEMA half-life\beta=0.5^{\frac{\text{Minibatch size}}{\text{EMA half-life}}}italic_β = 0.5 start_POSTSUPERSCRIPT divide start_ARG Minibatch size end_ARG start_ARG EMA half-life end_ARG end_POSTSUPERSCRIPT, e.g. for CIFAR-10, EMA β=0.55125×106≈0.9999𝛽superscript0.55125superscript1060.9999\beta=0.5^{\frac{512}{5\times 10^{6}}}\approx 0.9999italic_β = 0.5 start_POSTSUPERSCRIPT divide start_ARG 512 end_ARG start_ARG 5 × 10 start_POSTSUPERSCRIPT 6 end_POSTSUPERSCRIPT end_ARG end_POSTSUPERSCRIPT ≈ 0.9999.
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