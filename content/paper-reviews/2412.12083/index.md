---
title: "IDArb: Intrinsic Decomposition for Arbitrary Number of Input Views and Illuminations"
summary: "IDArb:  Decomposition under varied lights."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "3D Vision", "🏢 Chinese University of Hong Kong",]
showSummary: true
date: 2024-12-16
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.12083 {{< /keyword >}}
{{< keyword icon="writer" >}} Zhibing Li et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-17 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.12083" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.12083" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/idarb-intrinsic-decomposition-for-arbitrary" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

**Traditional methods for separating an object's true color and material from lighting effects in images (intrinsic decomposition) struggle with long processing times and inaccuracies.** Optimization-based methods require hours and often mix lighting with material, while learning-based methods, though faster, are inconsistent across different viewpoints.  Existing datasets for this task are also limited in scope and diversity, making it hard to train truly robust models. **Accurate intrinsic decomposition is crucial** for applications like relighting objects in images, editing materials, and even creating realistic 3D models. 



IDArb tackles these challenges using a **new AI model that can handle any number of images of an object under different lighting conditions.** It employs clever attention mechanisms to ensure **consistent results across all viewpoints and disentangles material from lighting.**  It’s also trained on a new, massive dataset, ARB-Objaverse, containing millions of images with diverse objects and lighting, resulting in **more accurate and robust intrinsic decomposition.**  This enables significantly better results in various applications like **relighting, material editing, and 3D reconstruction.**

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} IDArb achieves multi-view consistent intrinsic decomposition under varying illuminations. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} A new dataset, ARB-Objaverse, provides large-scale multi-view intrinsic data with diverse lighting. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} IDArb facilitates downstream tasks like relighting, material editing, and 3D reconstruction, outperforming existing methods. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**IDArb presents a significant advancement in intrinsic image decomposition**, impacting researchers in computer vision and graphics. It offers a robust, efficient solution for **multi-view decomposition under varied lighting**, which is crucial for realistic 3D content creation.  The introduction of **ARB-Objaverse dataset** enables future research on robust intrinsic decomposition models. Its application in relighting, material editing, and 3D reconstruction opens **new possibilities for realistic content creation and editing.**

------
#### Visual Insights



![](https://arxiv.org/html/2412.12083/x1.png)

> 🔼 IDArb는 제약 없는 조명 조건에서 다양한 수의 뷰를 입력받아 내재 분해를 수행합니다. 학습 기반 방법과 비교하여 다중 뷰 일관성을 달성하고 최적화 기반 방법과 비교하여 학습된 사전 지식을 통해 조명 효과에서 내재 요소를 더 잘 분리합니다. 이미지 재조명 및 재질 편집, 사진 측량 스테레오, 3D 재구성과 같은 다양한 응용 분야를 향상시킬 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: IDArb tackles intrinsic decomposition for an arbitrary number of views under unconstrained illumination. Our approach (a) achieves multi-view consistency compared to learning-based methods and (b) better disentangles intrinsic components from lighting effects via learnt priors compared to optimization-based methods. Our method could enhance a wide range of applications such as image relighting and material editing, photometric stereo, and 3D reconstruction.
> </details>





{{< table-caption >}}
| | Albedo | | Normal | Metallic | Roughness |
|---|---|---|---|---|---|---| 
| | SSIM↑ | PSNR↑ | Cosine Similarity ↑ | MSE ↓ | MSE ↓ |
| IID | 0.901 | 27.35 | - | 0.192 | 0.131 |
| RGB↔X | 0.902 | 28.09 | 0.834 | 0.162 | 0.347 |
| IntrinsicAnything | 0.901 | 28.17 | - | - | - |
| GeoWizard | - | - | 0.871 | - | - |
| Ours(single) | **0.935** | **32.79** | **0.928** | **0.037** | **0.058** |
| Ours(multi) | **0.937** | **33.62** | **0.941** | **0.016** | **0.033** |{{< /table-caption >}}

> 🔼 IDArb가 다른 기준 모델들과 비교하여 모든 지표(알베도, 노멀, 메탈릭, 러프니스)에서 최고의 성능을 달성함을 보여주는 정량적 평가 결과를 나타낸 표입니다. IDArb는 단일 뷰 및 다중 뷰 설정 모두에서 다른 방법들보다 우수한 성능을 보입니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Quantitative evaluation of IDArb against baselines. IDArb consistently achieves the best results among all albedo, normal, metallic and roughness metrics.
> </details>





### In-depth insights


#### Intrinsic Decomp
**본질적 분해(Intrinsic Decomp)**는 컴퓨터 비전 및 그래픽에서 이미지의 기본 구성 요소를 추출하는 핵심 과제입니다. 이는 3D 장면 이해, 재질 편집, 재조명 등 다양한 응용 분야의 기반이 됩니다. 본질적 분해는 입력 이미지에서 **알베도, 법선, 금속성, 거칠기**와 같은 고유 속성을 분리하는 것을 목표로 합니다. 이러한 속성은 객체의 **모양, 재질, 조명과 무관**하며 장면의 진정한 본질을 나타냅니다. 전통적인 최적화 기반 방법은 계산적으로 **비싸고 조명과 재질의 모호성을 해결하는 데 어려움**을 겪습니다. 최근 딥러닝 기반의 방법은 **데이터 기반 사전 정보 활용**을 통해 **고품질 분해**를 달성하고 있습니다. 그러나 단일 이미지 기반 방법은 여러 뷰에서 **일관성 없는 결과**를 생성하는 경우가 있습니다. 다중 뷰 일관성을 유지하면서 본질적 분해를 수행하는 것은 어려운 과제로 남아 있으며, 뷰 간의 **정보 융합 및 모호성 해결을 위한 효과적인 전략**이 필요합니다.

#### Diffusion Model
**확산 모델**은 노이즈 제거를 통한 역 확산 프로세스로 **고품질 이미지 생성**에 널리 사용됩니다. **Stable Diffusion**과 같은 최신 모델은 텍스트-이미지 생성에서 주목할 만한 결과를 달성했으며, **다양한 응용 분야**에 걸쳐 유망한 결과를 보여주었습니다. 본 논문에서는 **내재적 분해**를 위해 **교차 도메인 어텐션 모듈**을 활용하여 **다양한 입력 뷰와 조명 조건**을 처리하는 확산 기반 모델을 제안합니다. 이 접근 방식을 통해 **사실적인 3D 콘텐츠 제작**을 위한 **멀티뷰 일관성** 및 **고주파 디테일**을 갖춘 **정확한 내재적 구성 요소 추정**을 가능하게 합니다.

#### Multi-view Data
**멀티 뷰 데이터는 물체나 장면에 대한 풍부하고 다양한 정보를 제공하여** 다양한 컴퓨터 비전 및 그래픽 작업에서 중요한 역할을 합니다. 여러 각도에서 캡처된 이미지는 객체의 **3차원 형상, 재질 속성, 주변 조명을** 보다 완벽하게 표현합니다. 이러한 데이터는 **깊이 추정, 3D 재구성, 물체 인식 및 장면 이해**와 같은 작업에서 유용하게 사용될 수 있습니다. **멀티 뷰 데이터는 데이터의 양과 다양성 덕분에** 훈련된 모델의 **일반화 성능을 향상시켜** 보다 **정확하고 강력한 예측을** 가능하게 합니다. 또한, **멀티 뷰 일관성을** 통해 여러 시점에서 **예측의 정확성과 안정성을 보장**할 수 있습니다. 멀티 뷰 데이터의 주요 과제 중 하나는 여러 시점에서 캡처된 정보를 효과적으로 통합하는 것입니다. 이 문제를 해결하기 위해 **교차 뷰 어텐션 메커니즘**과 같은 다양한 기술이 개발되었습니다. 이러한 메커니즘은 **다른 뷰 간의 관계를** 모델링하고 **전역 정보 교환을** 가능하게 하여 **일관되고 정확한** 멀티 뷰 재구성을 보장합니다. 요약하면, **멀티 뷰 데이터는** 컴퓨터 비전 및 그래픽 분야의 다양한 작업에서 **중요한 역할을** 하며, 멀티 뷰 데이터를 효과적으로 활용하는 기술은 **더욱 강력하고 사실적인 3D 모델 및 장면 표현을 향상시키는 데 중요**합니다.

#### Relighting App
**재조명 앱**은 이미지의 고유한 속성(알베도, 표면 법선, 금속성, 거칠기)을 분해하여 다양한 조명 조건에서 사실적인 이미지를 생성하는 애플리케이션입니다. 이러한 앱은 **역렌더링** 기술을 사용하여 이미지에서 기하학적 및 재질 정보를 추출하고, 이를 통해 사용자는 조명을 수정하거나 편집하여 원본 이미지의 모양을 변경할 수 있습니다. 예를 들어, 어두운 이미지를 밝게 하거나, 조명의 색상을 변경하거나, 그림자를 추가하거나 제거할 수 있습니다. 이러한 기능은 **사진 편집, 게임 개발, 영화 제작, 건축 디자인**과 같은 다양한 분야에서 활용될 수 있습니다. 특히, **가상 환경에서 사실적인 조명 효과를 시뮬레이션**하거나, **제품의 외관을 다양한 조명 조건에서 미리 확인**하는 데 유용합니다. 재조명 앱은 사용자에게 **창의적인 표현**을 위한 강력한 도구를 제공하며, **몰입형 경험**을 향상시키는 데 기여합니다. 이러한 앱의 발전은 **컴퓨터 비전 및 그래픽 기술의 발전**과 밀접하게 연관되어 있으며, 앞으로 더욱 사실적이고 다양한 기능을 제공할 것으로 기대됩니다.

#### Dataset & Limits
**ARB-Objaverse 데이터셋은 다양한 조명 조건에서 렌더링된 대규모 객체들을 제공하여 기존 데이터셋의 한계를 극복합니다.** 68k개의 3D 모델을 Objaverse에서 선택하고, 각 객체에 대해 다양한 조명으로 7개의 이미지를 12개 시점에서 렌더링하여 **5.7M개의 RGB 이미지와 조명 조건에 따른 본질적 요소**를 생성했습니다. 이는 **다양한 조명, 시점, 객체의 조합**으로 훈련 데이터의 다양성을 확보하고, **조명과 재질의 모호성 문제**를 완화하는 데 기여합니다. **하지만 실제 데이터 부족은 여전히 한계**로 남아있으며, 특히 복잡한 재질 변화를 가진 객체의 경우 과도하게 단순화된 결과를 초래할 수 있습니다. 따라서 **실제 데이터를 통합하는 비지도 학습 기법** 등 추가 연구가 필요합니다. **또한, 현재 교차 시점 어텐션 메커니즘의 O(N²) 복잡도는 고해상도 이미지 또는 많은 시점에서의 처리를 어렵게 합니다.** 향후 연구에서는 **효율적인 교차 시점 어텐션 메커니즘** 개발이 중요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.12083/x2.png)

> 🔼 IDArb는 다양한 조명 조건에서 촬영된 임의 개수의 이미지를 입력받아 intrinsic decomposition을 수행하는 확산 기반 모델입니다. 그림은 IDArb의 전체적인 구조와 UNet 내부의 attention block을 보여줍니다. 입력 이미지들은 N_v개의 시점과 N_i개의 조명 조건에서 샘플링되며, 각 이미지의 latent vector는 가우시안 노이즈와 연결되어 denoising에 사용됩니다. Intrinsic component는 Albedo, Normal, Metallic&Roughness의 세 가지 triplet으로 나뉘며, 각각 특정 텍스트 프롬프트를 사용하여 모델을 안내합니다. UNet 내부의 attention block은 cross-component attention과 cross-view attention 모듈을 통해 component와 시점 간의 정보 교환을 촉진하여, 전역 정보 교환을 가능하게 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Top: Overview of  IDArb. Bottom: Illustration of the attention block within the UNet. Our training batch consists of N𝑁Nitalic_N input images, sampled from Nvsubscript𝑁𝑣N_{v}italic_N start_POSTSUBSCRIPT italic_v end_POSTSUBSCRIPT viewpoints and Nisubscript𝑁𝑖N_{i}italic_N start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT illuminations. The latent vector for each image is concatenated with Gaussian noise for denoising. Intrinsic components are divided into three triplets (D𝐷Ditalic_D=3): Albedo, Normal and Metallic&Roughness. Specific text prompts are used to guide the model toward different intrinsic components. For attention block inside UNet, we introduce cross-component and cross-view attention module into it, where attention is applied across components and views, facilitating global information exchange.
> </details>



![](https://arxiv.org/html/2412.12083/x3.png)

> 🔼 ARB-Objaverse 데이터셋은 다양한 물체들을 여러 조명 조건에서 렌더링하여 조명 변화에 강인한 학습 데이터를 제공합니다. 각 물체는 albedo, normal, metallic, roughness와 같은 intrinsic 요소들과 함께 제공됩니다. 그림에서 ABO, G-Objaverse, A12-Objaverse 데이터셋과 비교하여 ARB-Objaverse의 다양한 물체 및 조명 조건을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Overview of the Arb-Objaverse dataset. Our custom dataset features a diverse collection of objects rendered under various lighting conditions, accompanied by their intrinsic components.
> </details>



![](https://arxiv.org/html/2412.12083/x4.png)

> 🔼 (a) 알베도 추정. IDArb는 학습 기반 접근 방식과 달리 하이라이트와 그림자를 효과적으로 제거하여 더 정확한 알베도 맵을 생성합니다. 최적화 기반 방법과 비교했을 때, IDArb는 조명 효과를 알베도에 삽입하지 않고 더 나은 결과를 보입니다.
> <details>
> <summary>read the caption</summary>
> (a) Albedo estimation. Our method effectively removes highlights and shadows.
> </details>



![](https://arxiv.org/html/2412.12083/x5.png)

> 🔼 IDArb가 다른 방법들(RGB→X, GeoWizard)과 비교하여, 평면을 올바르게 예측하면서도 물체의 형태를 잘 나타내는 노멀 맵을 생성하는 것을 보여줍니다. RGB→X는 물체의 텍스처에 의해 간섭을 받는 모습을 보이며, GeoWizard는 흐릿한 결과를 생성합니다.
> <details>
> <summary>read the caption</summary>
> (b) Normal estimation. Our method gives shape geometry while correctly predicting flat surface.
> </details>



![](https://arxiv.org/html/2412.12083/x6.png)

> 🔼 IDArb는 텍스처 패턴 및 조명의 간섭 없이 실제와 같은 결과를 생성하여 금속성 추정에서 IID 및 RGB↔X보다 성능이 뛰어납니다.
> <details>
> <summary>read the caption</summary>
> (c) Metallic estimation. Our method outperforms IID and RGB↔↔\leftrightarrow↔X with plausible results free of interference from texture patterns and lighting.
> </details>



![](https://arxiv.org/html/2412.12083/x7.png)

> 🔼 IDArb가 텍스처 패턴 및 조명의 간섭 없이 그럴듯한 결과를 생성하여 IID와 RGB↔X보다 우수한 성능으로 거칠기를 예측하는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (d) Roughness estimation. Our method outperforms IID and RGB↔↔\leftrightarrow↔X with plausible results free of interference from texture patterns and lighting.
> </details>



![](https://arxiv.org/html/2412.12083/x8.png)

> 🔼 IDArb 모델은 합성 데이터에서 다른 방법들과 비교하여 우수한 내재적 추정 결과를 보여줍니다. 그림은 albedo, normal, metallic, roughness 추정 결과를 IID, RGB→X, IntrinsicAnything, GeoWizard 와 같은 기존 방법들과 비교하고 있습니다. IDArb는 albedo에서 하이라이트와 그림자를 효과적으로 제거하고, normal에서 정확한 기하학적 형태를 제공하며, metallic과 roughness에서 텍스처 패턴 및 조명의 간섭을 제거하여 사실적인 결과를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Qualitative comparison on synthetic data.  IDArb demonstrates superior intrinsic estimation compared to all other methods.
> </details>



![](https://arxiv.org/html/2412.12083/x9.png)

> 🔼 이 그림은 실제 데이터에 대한 IDArb의 정성적 비교 결과를 보여줍니다. IDArb은 실제 데이터에 대해서도 잘 일반화되어 정확하고 설득력 있는 분해능과 고주파 디테일을 제공합니다. 왼쪽에서 오른쪽으로 입력 이미지, IntrinsicAnything로 예측한 결과, IDArb으로 예측한 알베도, 노말, 메탈릭, 러프니스를 보여줍니다. IDArb은 IntrinsicAnything보다 더 나은 디테일과 사실적인 결과를 생성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Qualitative comparison on real-world data.  IDArb generalizes well to real data, with accurate, convincing decompositions and high-frequency details.
> </details>



![](https://arxiv.org/html/2412.12083/x10.png)

> 🔼 (a) 여러 입력 이미지로 구성된 샘플의 다중 뷰 일관성 시각적 비교입니다. IDArb는 학습 기반 방법(IntrinsicAnything)과 비교하여 다중 뷰 일관성을 달성하고 최적화 기반 방법을 통해 학습된 사전을 통해 조명 효과에서 내재적 구성 요소를 더 잘 분리합니다.
> <details>
> <summary>read the caption</summary>
> (a)
> </details>



![](https://arxiv.org/html/2412.12083/x11.png)

> 🔼 (b) 최적화 기반 방법(NVDiffRecMC)과 학습 기반 방법(IntrinsicAnything)의 단점을 보여주는 그림입니다. NVDiffRecMC는 조명 효과가 재질에 잘못 반영되어(예: 금속성 오브젝트의 어두운 색상), IntrinsicAnything는 멀티 뷰 입력에 대해 일관성 없는 결과를 생성합니다. 이에 반해 IDArb는 학습 기반 방식으로 멀티 뷰 일관성을 유지하면서 조명 효과와 재질을 더 잘 분리합니다.
> <details>
> <summary>read the caption</summary>
> (b)
> </details>



![](https://arxiv.org/html/2412.12083/x12.png)

> 🔼 이 그림은 교차 구성 요소 주의 및 훈련 전략에 대한 절제 연구 결과를 보여줍니다. (a)는 교차 구성 요소 주의가 없을 때 금속 및 거칠기와 같은 본질적인 구성 요소의 예측이 저하됨을 보여주며, 이는 이러한 구성 요소 간의 상호 작용을 모델링하는 것의 중요성을 강조합니다. (b)는 다중 뷰 입력과 단일 이미지 입력을 모두 사용한 훈련 전략의 효과를 보여줍니다. 다중 뷰 입력만 사용하여 훈련하면 단일 이미지 입력에 대한 성능이 저하되는 반면, 제안된 훈련 전략은 다양한 입력 유형에 대한 강력한 일반화 기능을 보여줍니다. 또한, 높은 노이즈 레벨로 노이즈 스케줄러를 이동하면 금속 및 거칠기 구성 요소의 예측이 향상됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Ablative studies on (a) cross-component attention and (b) training strategy.
> </details>



![](https://arxiv.org/html/2412.12083/x13.png)

> 🔼 이 그림은 다양한 수의 뷰포인트와 조명 조건에서 IDArb 모델의 성능을 보여줍니다. 뷰포인트 수(#V)와 조명 조건 수(#L)를 다양하게 변경하며 실험한 결과, 뷰포인트와 조명 조건의 수가 증가할수록 전반적인 분해 성능이 향상됨을 알 수 있습니다. 특히 금속성 및 거칠기 예측의 경우, 다중 조명 캡처가 조명 효과로 인한 모호성을 해결하는 데 매우 효과적입니다. 8개 이상의 뷰포인트를 추가하면 성능 향상이 감소하는 경향을 보입니다. x축은 뷰포인트 수를 나타내고, y축은 알베도, 노멀, 메탈릭, 러프니스 각각의 성능 지표 값의 변화를 나타냅니다. 색상 변화를 통해 뷰포인트 수와 조명 조건 수에 따른 성능 변화를 시각적으로 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Effects of number of viewpoints and lighting conditions. We find increasing the number of viewpoints and the lighting conditions generally improves decomposition performance.
> </details>



![](https://arxiv.org/html/2412.12083/x14.png)

> 🔼 이 그림은 실제 환경에서 촬영된 이미지(a)를 사용하여 새로운 조명 조건에서의 리라이팅 결과(b)와 재질 속성 변경 결과(c)를 보여줍니다. IDArb 모델을 사용하면 입력 이미지에서 알베도, 노말, 메탈릭, 러프니스 등의 고유 요소를 추출하여 재질 및 조명 편집과 같은 다양한 다운스트림 작업에 활용할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Relighting and material editing results. From in-the-wild captures (a), our model allows for relighting under novel illumination (b) and material property modifications (c).
> </details>



![](https://arxiv.org/html/2412.12083/x15.png)

> 🔼 이 그림은 최적화 기반 역렌더링 기법인 NVDiffRecMC에 저자들이 제안한 방법을 적용하여 재질 추정 결과를 향상시킨 것을 보여줍니다. 저자들의 방법은 각 학습 이미지를 해당하는 재질 요소로 분해하고, 이를 pseudo-material label로 사용합니다. 매 반복마다 NVDiffRecMC에서 예측한 재질 요소와 저자들의 방법으로 예측한 값 사이의 L2 정규화 항을 추가하여 물리적 타당성을 보장합니다. 그림에서 볼 수 있듯이, 저자들의 방법을 적용하면 NVDiffRecMC에서 재구성된 albedo의 색상 변화 문제가 크게 완화되어, 더 나은 품질의 렌더링 결과를 얻을 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Optimization-based inverse rendering results. Our method guides NVDiffecMC generate more plausible material results.
> </details>



![](https://arxiv.org/html/2412.12083/x16.png)

> 🔼 이 그림은 OpenIllumination 및 NeRFactor 데이터셋에서 4개의 OLAT(One-Light-At-a-Time) 이미지를 사용하여 예측한 사진 측량 스테레오 결과를 보여줍니다. OLAT 조건에서는 각 이미지가 주변 조광 없이 단일 점 광원으로 조명되어 그림자가 생깁니다. 그림에는 입력 OLAT 이미지, 예측된 알베도 및 법선 맵이 표시되어 있습니다. IDArb은 OLAT와 같은 까다로운 조건에서도 실제 및 합성 데이터 모두에서 좋은 결과를 생성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Photometric stereo results using 4 OLAT images in OpenIllumination and NeRFactor.
> </details>



![](https://arxiv.org/html/2412.12083/x17.png)

> 🔼 이 그림은 실제 데이터에 대한 추가적인 결과를 보여줍니다. 각 행은 입력 이미지와 해당 이미지에서 추출한 알베도, 노멀, 메탈릭, 러프니스 맵을 나타냅니다. IDArb은 다양한 실제 물체에 대해 사실적이고 세부적인 결과를 생성합니다. 이는 IDArb이 합성 데이터로 훈련되었음에도 불구하고 실제 이미지에 잘 일반화됨을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: More results on real-world data.
> </details>



![](https://arxiv.org/html/2412.12083/x18.png)

> 🔼 이 그림은 실제 데이터에 대한 추가 결과와 재구성 및 재조명 이미지를 보여줍니다. 입력 이미지에서 예측된 albedo, normal, metallic, roughness를 사용하여 렌더링된 이미지(Recon)와 다양한 조명 조건에서 재조명된 이미지(Relit 1, 2, 3)를 통해 모델의 성능을 시각적으로 확인할 수 있습니다. 오토바이, 자동차, 트럼펫, 빵과 잼 등 다양한 종류의 물체에 대한 결과를 제시하여 모델의 일반화 능력을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: More results on real-world data. We also provide the reconstructed and relighting images.
> </details>



![](https://arxiv.org/html/2412.12083/x19.png)

> 🔼 이 그림은 여러 시점에서 촬영된 데이터에 대한 추가적인 결과를 보여줍니다. 각 행은 서로 다른 다중 시점 데이터셋을 나타내며, 입력 이미지와 함께 예측된 알베도, 노멀, 메탈릭, 러프니스 맵이 표시됩니다. 첫 번째 행은 드럼 세트, 두 번째 행은 다양한 음식이 담긴 접시, 세 번째 행은 샌드위치와 핫도그가 담긴 접시입니다. 이 그림을 통해 IDArb 모델이 다양한 다중 시점 데이터에서 일관성 있는 본질적 요소를 추출하는 능력을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: More results on multi-view data.
> </details>



![](https://arxiv.org/html/2412.12083/x20.png)

> 🔼 NeRD 데이터셋(Boss 외, 2021a)의 각 장면에 대해 4개의 뷰를 입력하여 극단적인 조명 변화가 있는 다중 뷰 이미지에서 본 모델의 성능을 평가합니다. 각 뷰는 서로 다른 조명 조건에서 렌더링됩니다. 입력 이미지, 알베도, 노멀, 메탈릭, 러프니스를 예측한 결과가 표시됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: Multiview images with extreme lighting variation. For each scene in NeRD dataset (Boss et al., 2021a), we input 4 views.
> </details>



![](https://arxiv.org/html/2412.12083/x21.png)

> 🔼 이 그림은 IDArb 모델의 실패 사례를 보여줍니다. 첫 번째 행은 야외 장면으로, 모델이 객체 중심 데이터에 대해 주로 훈련되었기 때문에 어려움을 겪습니다. 두 번째 행은 텍스트가 있는 이미지로, 모델이 올바른 텍스트 구조를 복구하지 못합니다. 세 번째 행은 전화기 이미지로, 모델이 미묘한 재질 디테일을 보존하지 못하고 지나치게 단순화된 출력을 생성합니다. 이러한 문제는 합성 훈련 데이터가 종종 더 단순한 재질 변형을 포함하고 있어 모델이 세밀한 재질 속성을 과도하게 단순화하게 만드는 것에서 비롯됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 15: Failure cases.
> </details>



![](https://arxiv.org/html/2412.12083/x22.png)

> 🔼 Mip-NeRF 360 데이터셋의 야외 장면에 대한 IDArb의 결과를 보여줍니다. 각 장면에 대해 4개의 뷰를 입력으로 사용했습니다. 그림에는 입력 이미지, 예측된 알베도, 법선, 메탈릭, 러프니스 맵이 포함되어 있습니다. IDArb은 다양한 야외 장면에서 일관되고 정확한 내재적 이미지 분해를 수행하는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 16: Results on Mip-NeRF 360 (Barron et al., 2022) (Part 1, outdoor). We input 4 views for each scene.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| # OLAT Images | 2 | 2 | 4 | 4 | 8 | 8 |
|---|---|---|---|---|---|---| 
| Methods | Albedo\uparrow | Normal\uparrow | Albedo\uparrow | Normal\uparrow | Albedo\uparrow | Normal\uparrow |
| IID | 22.23 | - | 22.40 | - | 22.86 | - |
| RGB <->X | 21.29 | 0.71 | 22.08 | 0.77 | 23.29 | 0.81 |
| SDM-UniPS | 22.95 | 0.74 | 23.20 | 0.76 | 23.37 | 0.81 |
| Ours | **23.50** | **0.83** | **23.64** | **0.84** | **25.15** | **0.85** |{{< /table-caption >}}
> 🔼 NeRFactor 데이터셋에서 Photometric Stereo에 대한 정량적 결과를 보여주는 표입니다. 2, 4, 8개의 OLAT(One-Light-At-a-Time) 이미지를 사용하여 성능을 평가했으며, 제안된 방법(Ours)이 비교된 모든 방법 중에서 최고의 성능을 달성했습니다.  OLAT은 각 이미지가 주변광 없이 단일 점 광원으로만 비춰지는 까다로운 조건으로, 그림자도 강하게 드리워집니다. 이러한 조건에서도 본 연구의 방법은 다른 방법들과 비교하여 albedo 및 normal 예측 정확도가 가장 높았습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Quantitative results for photometric stereo on NeRFactor. We evaluate performance using 2, 4, and 8 OLAT images, and achieve the best performance among all compared methods.
> </details>

{{< table-caption >}}
| | Nerfactor | | | Synthetic4Relight | | | |
|---|---|---|---|---|---|---|---|---| 
| | Albedo (raw) | Albedo (scaled) | Relighting | Albedo (raw) | Albedo (scaled) | Relighting | Roughness |
| NVDiffRecMC | 17.89 | 25.88 | 22.65 | 17.03 | 29.64 | 24.05 | 0.046 |
| NVDiffRecMC w/ Ours | **20.90** | **26.61** | **27.20** | **26.42** | **30.73** | **31.01** | **0.014** |{{< /table-caption >}}
> 🔼 IDArb를 pseudo label로 사용하여 최적화 기반 역렌더링 기법의 성능을 향상시키는 실험 결과를 NeRFactor 및 Synthetic4Relight 데이터셋에 대해 나타낸 표입니다. albedo, relighting, roughness에 대한 정량적 평가 결과를 IDArb를 사용하지 않은 경우와 비교하여 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Ablation on IDArb pseudo labels for optimization-based inverse rendering on NeRFactor and Synthetic4Relight datasets.
> </details>

{{< table-caption >}}
| # L | # V | 1 | 2 | 4 | 8 | 12 |
|---|---|---|---|---|---|---| 
| 1 | | 29.16 | 28.72 | 30.12 | 30.49 | 30.77 |
| 2 | | 29.96 | 30.26 | 30.96 | 31.13 | 31.26 |
| 3 | | 30.25 | 30.73 | 31.16 | 31.33 | 31.40 |{{< /table-caption >}}
> 🔼 이 표는 다양한 수의 뷰포인트(# V) 및 조명 조건(# L)에 따른 알베도 성능(PSNR, ↑↑는 값이 클수록 좋음)을 보여줍니다. 뷰포인트 수와 조명 조건 수가 증가함에 따라 알베도 추정 성능이 향상됨을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Albedo Performance ↑↑\uparrow↑ across different numbers of viewpoints (# V) and lightings (# L).
> </details>

{{< table-caption >}}
| # L | # V | 1 | 2 | 4 | 8 | 12 |
|---|---|---|---|---|---|---| 
| 1 |  | 0.909 | 0.910 | 0.925 | 0.930 | 0.932 |
| 2 |  | 0.922 | 0.927 | 0.930 | 0.933 | 0.934 |
| 3 |  | 0.926 | 0.931 | 0.931 | 0.934 | 0.935 |{{< /table-caption >}}
> 🔼 다양한 수의 뷰포인트(# V)와 조명 조건(# L)에 따른 법선 예측 성능(Cosine Similarity)을 보여주는 표입니다. 뷰포인트와 조명 조건 수가 증가함에 따라 법선 예측 성능이 향상되는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Normal Performance ↑↑\uparrow↑ across different numbers of viewpoints (# V) and lightings (# L).
> </details>

{{< table-caption >}}
| # L | # V | 1 | 2 | 4 | 8 | 12 |
|---|---|---|---|---|---|---| 
| 1 |   | 0.105 | 0.116 | 0.068 | 0.059 | 0.050 |
| 2 |   | 0.061 | 0.068 | 0.047 | 0.044 | 0.042 |
| 3 |   | 0.061 | 0.056 | 0.048 | 0.045 | 0.040 |{{< /table-caption >}}
> 🔼 이 표는 다양한 수의 뷰포인트(# V)와 조명 조건(# L)에 대한 금속성 성능을 정량적으로 보여줍니다. 뷰포인트 수와 조명 조건이 증가함에 따라 금속성 추정 성능이 향상됨을 보여줍니다. 숫자가 낮을수록 성능이 더 좋다는 것을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Metallic Performance ↓↓\downarrow↓ across different numbers of viewpoints (# V) and lightings (# L).
> </details>

{{< table-caption >}}
| # L | # V | 1 | 2 | 4 | 8 | 12 |
|---|---|---|---|---|---|---| 
| 1 | | 0.049 | 0.050 | 0.024 | 0.019 | 0.021 |
| 2 | | 0.043 | 0.026 | 0.019 | 0.016 | 0.015 |
| 3 | | 0.031 | 0.022 | 0.016 | 0.014 | 0.013 |{{< /table-caption >}}
> 🔼 이 표는 다양한 수의 뷰포인트(# V)와 조명 조건(# L)에 따른 거칠기 성능을 정량적으로 보여줍니다. 뷰포인트 수와 조명 조건이 증가함에 따라 거칠기 예측 성능이 향상되는 것을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Roughness Performance ↓↓\downarrow↓ across different numbers of viewpoints (# V) and lightings (# L).
> </details>

{{< table-caption >}}
| | SSIM↑ | PSNR↑ | LPIPS↓ |
|---|---|---|---| 
| Ours | 0.876 | **27.98** | **0.117** |
| IntrinsicAnything | **0.896** | 25.66 | 0.150 |{{< /table-caption >}}
> 🔼 MIT-Intrinsic 데이터셋에서 albedo 예측 정확도를 IntrinsicAnything와 비교한 표입니다. SSIM, PSNR, LPIPS 척도를 사용하여 평가했습니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Quantitative comparisons on MIT-Intrinsic.
> </details>

{{< table-caption >}}
|                      | Normal Cosine Distance↓ | Albedo SSIM↑ | Albedo PSNR↑ | Albedo LPIPS↓ | Re-rendering PSNR-H↑ | Re-rendering PSNR-L↑ | Re-rendering SSIM↑ | Re-rendering LPIPS↓ |
|----------------------|-----------------------|-------------|-------------|------------|-------------------|-------------------|----------------|----------------|
| Ours(single)        | 0.041                 | 0.978      | 41.30      | 0.039       | 24.11              | 31.28              | 0.969           | 0.024           |
| Ours(multi)         | **0.029**            | **0.978**   | **41.46**   | **0.038**    | **24.36**           | **31.43**           | **0.970**        | **0.024**        |
| StableNormal        | **0.038**            |             |             |            |                   |                   |                |                |
| IntrinsicNeRF       |                       | **0.981**   | 39.31      | 0.048       |                   |                   |                |                |{{< /table-caption >}}
> 🔼 Stanford-ORB 데이터셋에서의 정량적 비교 결과를 보여주는 표입니다. 단일 이미지 입력과 다중 이미지 입력에 대한 저희 모델(Ours)의 성능을 StableNormal 및 IntrinsicNeRF와 비교합니다. 노멀 추정, 알베도 추정, 그리고 리렌더링 결과에 대한 평가 결과를 포함하며, 각 메트릭에 대한 최고 성능은 볼드체로 표시됩니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Quantitative comparisons on Stanford-ORB.
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