---
title: "Pandora3D: A Comprehensive Framework for High-Quality 3D Shape and Texture Generation"
summary: "Pandora3D: 이미지와 텍스트로 고품질 3D 모델과 질감 자동 생성!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "3D Vision", "🏢 Tencent XR Vision Labs",]
showSummary: true
date: 2025-02-20
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.14247 {{< /keyword >}}
{{< keyword icon="writer" >}} Jiayu Yang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-25 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.14247" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.14247" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/pandora3d-a-comprehensive-framework-for-high" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

3D 디지털 자산 생성은 게임, 영화, 로봇 공학 등 다양한 분야에서 중요하지만, 기존 방식은 복잡하고 비용이 많이 듭니다. **Pandora3D는 이미지, 텍스트, 다중 뷰 이미지 등 다양한 입력을 사용하여 고품질 3D 형태와 질감을 자동으로 생성하는 종합 프레임워크**입니다.  기존 방식의 어려움을 해결하기 위해 효율적인 3D 기하 구조 오토인코더와 다중 단계 텍스처 생성 과정을 제시합니다. 



Pandora3D는 VAE(Variational Autoencoder)를 사용하여 3D 기하 구조를 잠재 공간으로 압축하고, 확산 네트워크를 통해 입력 프롬프트를 조건으로 잠재 표현을 생성합니다. **여러 뷰의 텍스처 일관성을 강화하기 위해 각 단계에 일관성 스케줄러를 통합**했습니다. 실험 결과, 다양한 입력 형식에 효과적으로 대처하고 고품질 3D 콘텐츠를 생성하는 것으로 나타났습니다.  **소스 코드와 사전 훈련된 가중치를 공개**하여 다른 연구자의 후속 연구를 지원합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 다양한 입력(이미지, 텍스트)으로 고품질 3D 모델과 질감 생성 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} VAE와 확산 네트워크 기반의 효율적인 생성 파이프라인 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 픽셀 단위 일관성 유지를 위한 혁신적인 일관성 스케줄러 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**Pandora3D**는 고품질 3D 콘텐츠 생성 분야의 연구에 중요한 발전입니다. 다양한 입력 방식(이미지, 텍스트)을 지원하고 효율적인 3D 형태 및 질감 생성 파이프라인을 제시하여 **3D 모델링 및 텍스처링 기술 발전에 기여**합니다. 또한, **다양한 응용 분야** (게임, 영화, 로봇공학 등)에서 활용될 수 있는 고품질 3D 자산을 자동 생성함으로써 **시간 및 비용 절감**에 기여할 수 있습니다.  향후 연구를 위한 새로운 방향을 제시하고, 공개된 소스 코드와 사전 훈련된 가중치를 통해 **다른 연구자의 추가 연구 및 발전**을 촉진합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.14247/x1.png)

> 🔼 그림 1은 3D 기하학적 자기 인코더(Variational Autoencoder)의 구조를 보여줍니다. (A)는 기본적인 VAE 구조로, 3D 기하 형태를 잠재 공간(latent space)으로 압축하는 과정을 나타냅니다.  (B)는 효율적인 3D 기하학적 압축을 위해 개선된 VAE 구조입니다.  기본 VAE와 달리, (B)는 입력 점 구름(point cloud)의 모든 점을 활용하여 정보 손실을 최소화하고, 효율성을 높였습니다.  두 구조 모두 크로스 어텐션(Cross-Attention) 및 셀프 어텐션(Self-Attention) 메커니즘을 사용하여 기하학적 특징과 위치 정보를 효과적으로 통합합니다.  (B)는 점 샘플링(point sampling) 없이도 고해상도 점 구름 데이터를 효율적으로 처리할 수 있도록 설계되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: 3D Geometry variational autoencoder. (A): Our base VAE for 3D geometry compression. (B) Extended VAE for efficient 3D geometry compression.
> </details>







### In-depth insights


#### 3D Shape Encoding
3D 형상 인코딩은 3D 모델의 복잡한 기하학적 정보를 효율적으로 표현하는 핵심 과정입니다.  **자동화된 3D 콘텐츠 생성**에서 3D 형상 인코딩은 효과적인 표현과 처리를 위해 필수적입니다.  이 과정은 일반적으로 3D 형상을 저차원의 잠재 공간(latent space)으로 매핑하는 것을 포함합니다.  **Variational Autoencoder (VAE)** 와 같은 신경망 기반 기법은 고차원의 3D 데이터를 효과적으로 압축하여 잠재 표현을 생성하는데 사용됩니다.  **VAE는 3D 형상을 잠재 공간으로 인코딩하고 디코딩하는 과정을 통해 3D 형상의 주요 특징을 추출**하고 재구성하는 능력을 갖습니다.  **잠재 공간의 차원을 줄임으로써 계산 비용을 절감**하고, 노이즈에 대한 강건성을 높일 수 있습니다.  또한, 잠재 표현은 후속적인 처리 단계, 예를 들어 3D 형상 생성이나 변환에 직접 사용될 수 있습니다.  **효율적인 3D 형상 인코딩은 3D 모델의 크기와 복잡도를 줄이는 동시에 중요한 형상 정보를 보존**해야 하는 과제를 안고 있습니다. 따라서, 인코딩 방법의 선택은 생성되는 3D 콘텐츠의 질과 효율성에 직접적인 영향을 미칩니다.  **향후 연구는 더욱 효율적이고 정확한 3D 형상 인코딩 기법 개발**에 초점을 맞춰야 합니다.  특히, 복잡한 형상이나 다양한 3D 모델 표현 방식에 대한 대응 능력을 향상시키는 것이 중요합니다.

#### Diffusion Model
본 논문에서 다루는 확산 모델은 3D 형태 및 질감 생성에 핵심적인 역할을 합니다. **다양한 입력 프롬프트(이미지, 다중 뷰 이미지, 텍스트)**를 기반으로 잠재 공간 내에서 고품질 3D 콘텐츠를 생성하는 데 사용됩니다.  **잠재 공간을 효과적으로 압축 및 생성**하기 위해 VAE(Variational Autoencoder)와 확산 네트워크를 결합한 아키텍처를 사용합니다.  **다중 스케일 학습 전략**을 통해 모델의 용량을 향상시키고, 상세한 기하학적 특징까지 포착합니다. 특히, 텍스처 생성 단계에서는 일관성 있는 픽셀 단위 정합을 위해 **일관성 스케줄러**를 도입하여 매끄러운 통합을 보장합니다.  전반적으로, 이 확산 모델은 다양한 입력 형식을 효과적으로 처리하고, 고급 신경망 아키텍처와 새로운 방법론을 활용하여 고품질 3D 콘텐츠 생성을 가능하게 합니다.  이는 **실제 응용 분야에서의 활용 가능성**을 높여줍니다.

#### Multi-view Textures
다양한 시점에서 렌더링된 여러 이미지들을 통합하여 3D 모델의 질감을 표현하는 **멀티뷰 텍스처** 기법은 3D 모델의 사실성과 현실감을 높이는 데 매우 중요합니다. **단일 이미지만으로는 표현하기 어려운 입체감과 디테일을 다양한 각도의 이미지들을 활용하여 보다 풍부하게 표현**할 수 있습니다.  하지만 여러 이미지들을 조합하는 과정에서 **일관성을 유지하는 것이 관건**입니다.  **빛의 방향이나 그림자의 위치 등이 이미지 간에 불일치**하면 어색한 결과물이 나타나기 때문입니다. 따라서 이러한 문제를 해결하기 위해 **픽셀 단위의 일관성을 유지하는 기술**이 필수적입니다.  **일관성 유지를 위한 알고리즘**은 이미지 간의 차이를 최소화하고 자연스러운 연결을 만드는 데 초점을 맞춥니다.  **머신러닝 기반의 최적화 기법**을 활용하면 이 과정을 자동화하고 효율성을 높일 수 있습니다. 멀티뷰 텍스처는 **고품질 3D 모델 생성을 위한 핵심 요소**이며, **현실감 있는 시각적 경험**을 제공하는 데 크게 기여합니다. 앞으로 멀티뷰 텍스처 기술은 더욱 발전하여, 보다 효율적이고 정교한 3D 모델 제작을 가능하게 할 것으로 기대됩니다.

#### Mesh Generation
본 논문에서 제시된 메시 생성 방법은 크게 두 가지 접근 방식을 취하고 있습니다. 첫째, **Variational Autoencoder (VAE) 기반의 암시적 표현 방식**입니다. VAE는 복잡한 3D 기하 구조를 잠재 공간(latent space)으로 효율적으로 압축하여, 후속 단계의 확산 모델(diffusion model)이 입력 프롬프트를 조건으로 하여 잠재 변수를 생성하는 데 도움을 줍니다.  **다양한 입력 형태** (단일 이미지, 다중 뷰 이미지, 텍스트 설명)를 처리할 수 있도록 모델이 설계되었습니다. 둘째, **아티스트가 생성한 메시(AM) 생성 방식**은 단순한 형태의 3D 모델 생성에 유용한 대안으로 제시되었으며, 복잡한 형태의 모델 생성에는 VAE 기반 방식을 사용하는 것이 더 적합합니다. 두 방식 모두 효율적인 메시 생성을 위해 다양한 기법(예: 다중 해상도 학습, 점 클라우드 압축)을 활용합니다. **점 클라우드 압축 방식** 개선을 통해 고해상도의 정보 손실을 최소화하고자 하였으며, 고해상도 메시 생성을 위한 다양한 기법들을 제시합니다.  **일관성(consistency)**을 유지하는 메커니즘을 통해 고품질의 시각적 결과를 얻을 수 있도록 했습니다. 전체적으로, 제안된 메시 생성 방식은 다양한 입력과 첨단 신경망 아키텍처를 활용하여 효율적이고 고품질의 3D 메시를 생성하는 것을 목표로 합니다.

#### Future Enhancements
Pandora3D의 미래 개선 방향에 대한 심도있는 고찰은 **다양한 모달리티 입력(이미지, 텍스트, 멀티뷰)**에 대한 로버스트성 향상과 **고해상도 3D 모델 생성 능력 향상**에 초점을 맞춰야 합니다.  **메모리 효율적인 네트워크 구조 및 학습 전략** 개발을 통해 연산 비용을 낮추고, **더욱 사실적이고 디테일한 질감 생성**을 위한 새로운 텍스처 생성 알고리즘 연구도 필요합니다. **점진적 렌더링 기법 및 효율적인 메쉬 처리**를 통한 실시간 3D 콘텐츠 생성의 가능성도 탐구해야 합니다. 또한, **다양한 3D 애플리케이션과의 호환성**을 높이는 방향으로의 확장 및 다양한 도메인에 특화된 모델 개발도 중요한 과제입니다. **사용자 친화적인 인터페이스** 개발을 통해 전문가뿐 아니라 일반 사용자도 쉽게 사용할 수 있도록 하는 것도 중요한 고려 사항입니다.  마지막으로, **윤리적 및 사회적 영향**을 고려한 모델 개발 및 배포 전략 수립 또한 필수적입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.14247/extracted/6223781/figures/diffusion/diffusion.png)

> 🔼 그림 2는 텍스트 또는 이미지 프롬프트를 기반으로 3D 형상을 생성하는 확산 모델의 파이프라인을 보여줍니다.  이 과정에서 DinoV2는 이미지의 지역적 특징을 추출하고, CLIP은 전역적 특징을 추출하며, VAE 디코더는 잠재 공간 표현에서 3D 형상을 재구성하는 역할을 합니다.  훈련 과정 동안 DinoV2, CLIP, 그리고 VAE 디코더는 고정되어 있고, 확산 모델만 훈련됩니다. 이는 기존의 3D 형상 생성 모델과 비교하여 보다 효율적이고 안정적인 훈련을 가능하게 합니다. 그림은 각 구성 요소의 기능과 데이터 흐름을 명확하게 시각화하여 파이프라인의 전체적인 동작 원리를 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Diffusion pipline. In the process of training a diffusion model, the DinoV2, CLIP, and VAE Decoder components are kept frozen
> </details>



![](https://arxiv.org/html/2502.14247/extracted/6223781/figures/AM/am.png)

> 🔼 그림 3은 아티스트가 생성한 메시를 생성하기 위한 파이프라인을 보여줍니다. 먼저 메시를 불연속 토큰 시퀀스로 인코딩합니다. 그런 다음 이러한 시퀀스는 트랜스포머 네트워크 아키텍처를 사용하는 디코더 전용 자기 회귀 모델을 통해 처리됩니다. 다중 모드 조건 제어를 강화하기 위해 사전 훈련된 조건 인코더 네트워크가 사용됩니다. 이 네트워크는 다양한 모드를 효과적으로 통합하여 생성된 메시가 지정된 조건을 준수하도록 합니다. 간단히 말해, 이 그림은 다양한 입력(이미지, 텍스트 등)을 기반으로 아티스트 스타일의 3D 메시를 생성하는 과정을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Pipeline for Artist-Created Mesh Generation. Initially, meshes are encoded into discrete token sequences. These sequences are then processed through a decoder-only autoregressive model that utilizes a Transformer network architecture. To enforce multi-modality condition control, a pretrained condition encoder network is employed. This network effectively integrates diverse modalities, ensuring that the generated meshes adhere to specified conditions.
> </details>



![](https://arxiv.org/html/2502.14247/extracted/6223781/figures/AM/am4.png)

> 🔼 이 그림은 논문에서 제시된 '아티스트가 생성한 메시(Artist-Created Mesh) 생성 모델'을 사용하여 생성된 메시들의 예시를 보여줍니다.  모델이 생성한 메시들은 위상적 일관성(topological consistency)을 잘 유지하며, 고품질의 예술적인 메시를 생성하는 모델의 효과를 보여줍니다. 그림에는 다양한 형태와 복잡도의 메시들이 포함되어 있으며, 각 메시는 아티스트가 직접 제작한 듯한 디테일과 품질을 가지고 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Example Meshes Generated by Our Artist-Created Mesh Generation Model. The meshes produced by our model demonstrate superior performance in maintaining topological consistency, showcasing the effectiveness of our approach in generating high-quality artistic meshes.
> </details>



![](https://arxiv.org/html/2502.14247/extracted/6223781/figures/texture/texture_simp_2.jpg)

> 🔼 그림 5는 논문의 텍스처 생성 파이프라인을 보여줍니다. Trellis3D로부터 입력 이미지와 메시를 받아, 깊이 맵 생성, 프런트 이미지 생성, 멀티뷰 RGB 이미지 생성, 멀티뷰 PBR 이미지 생성, 고해상도 재구성 및 픽셀 일관성 강화의 여러 단계를 거쳐 최종 텍스처를 생성하는 과정을 시각적으로 보여줍니다. 각 단계는 다양한 신경망 아키텍처와 기법을 활용하여 고품질 텍스처를 생성하는 데 기여합니다. 특히, 다중 뷰 텍스처 일관성을 유지하기 위한 일관성 스케줄러(Consistency scheduler)의 역할이 강조됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Texture Generation Pipeline (input image and mesh from Trellis3D).
> </details>



![](https://arxiv.org/html/2502.14247/extracted/6223781/figures/texture/frontal.png)

> 🔼 그림 6은 텍스트 또는 이미지 프롬프트가 프런트 뷰 기하학과 정렬된 프런트 이미지로 변환되는 과정을 보여줍니다.  텍스트 프롬프트의 경우, 3D 메시를 깊이 맵으로 렌더링하고, 깊이 맵 조건부 확산 모델을 사용하여 프런트 이미지를 생성합니다. 이미지 프롬프트의 경우, IP-Adapter와 ControlNet을 통합하여 프런트 이미지를 생성합니다. 이렇게 생성된 프런트 이미지는 후속 텍스처 생성을 위한 입력으로 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Both textual and visual prompts are transformed into a frontal image that is aligned with the frontal-view geometry.
> </details>



![](https://arxiv.org/html/2502.14247/extracted/6223781/figures/texture/upscaled_albedo.png)

> 🔼 그림 7은 멀티뷰 텍스처 생성 파이프라인의 일부로 생성된 이미지들을 보여줍니다.  각각의 이미지는 3D 모델의 다양한 각도에서 렌더링된 결과이며, RGB 이미지 외에도 알베도(albedo), 메탈릭(metallic), 러프니스(roughness) 맵을 포함합니다. 이러한 맵들은 물리 기반 렌더링(PBR) 텍스처를 생성하는 데 사용되며, 최종적으로 사실적이고 디테일한 3D 모델 표현을 가능하게 합니다.  각 이미지는 512x512 픽셀 해상도를 가지고 있으며, 고해상도 이미지로의 업스케일링을 통해 더욱 향상된 품질을 얻을 수 있습니다. 이 그림은 멀티뷰 텍스처 생성의 중간 단계 결과물을 보여줌으로써, Pandora3D 시스템의 성능과 효율성을 시각적으로 보여주는 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Multi-view RGB, albedo, metallic and roughness images.
> </details>



![](https://arxiv.org/html/2502.14247/extracted/6223781/figures/dataset/process_pipeline.png)

> 🔼 그림 8은 고해상도 알베도 이미지를 보여줍니다. 3.4절 고해상도 개선 단계에서 생성된 이미지로,  다양한 뷰의 알베도 텍스처가 매우 세밀하게 표현되어 있습니다. 이 이미지들은 768x768과 1024x1024 해상도로 업스케일링된 후, Real-ESRGAN을 사용하여 3072x3072의 고해상도로 더욱 개선되었습니다.  이를 통해 생성된 3D 모델의 질감이 매우 사실적으로 표현되어, 더욱 현실감 있는 3D 모델 생성에 기여합니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: High-resolution albedo images.
> </details>



![](https://arxiv.org/html/2502.14247/extracted/6223781/figures/dataset/scanned_object_image.png)

> 🔼 그림 9는 논문에서 설명하는 3D 모델 데이터 처리 과정을 보여줍니다.  빨간색으로 표시된 부분은 데이터셋에 상관없이 한 번만 수행하는 단계이고, 초록색으로 표시된 부분은 사용된 알고리즘 모듈에 따라 맞춤형 개발이 필요한 단계입니다.  이 그림은 본 논문의 2절과 3.2절에서 설명하는 작업에 대한 예시 단계들을 보여줍니다.  즉, 데이터 전처리 과정의 전체 흐름을 한눈에 보여주는 개념도이며, 특히 각 단계의 특징과 논문의 다른 부분과의 연관성을 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Data processing pipline. The procedures marked in red are one-off implementations, while the green-boxed elements demand tailored development according to the algorithmic modules deployed on the dataset, we thereby provide exampled steps for jobs described in Section 2 and Section 3.2.
> </details>



![](https://arxiv.org/html/2502.14247/extracted/6223781/figures/dataset/mesh_classification_process.png)

> 🔼 이 그림은 Objaverse 데이터셋 [7]에 있는 스캔된 물체의 전형적인 이미지들을 보여줍니다. (A)와 (C)는 두 물체의 렌더링된 이미지이고, (B)와 (D)는 블렌더에서 해당 물체를 보여주는 사진입니다. 스캔된 물체는 파편화된 면이 많거나, 실제 '본체'가 없는 등의 문제점을 가지고 있어 3D 생성 모델 학습에 부정적인 영향을 미칠 수 있습니다. 이러한 문제점은 생성된 3D 모델의 품질 저하, 느린 렌더링 속도, 부적절한 모델 학습으로 이어집니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Typical images of scanned objects in Objaverse dataset [7]. (A) and (C) are rendered images of the two objects; (B) and (D) are corresponding object demonstration in blender.
> </details>



![](https://arxiv.org/html/2502.14247/extracted/6223781/figures/texture/image-2-mesh-res-01.png)

> 🔼 그림 11은 9개의 렌더링된 이미지를 사용하여 모델을 설명하도록 vLLM 모델을 활용하여 메시를 분류하는 과정을 보여줍니다. 빨간색 상자로 표시된 구조화된 데이터의 일부는 메시 분류에 사용될 수 있으며, 집계된 전체 문장은 메시의 캡션으로 사용될 수 있습니다.  더 자세히 설명하자면, vLLM(Very Large Language Model)을 이용하여 9개의 렌더링된 이미지를 입력으로 받아 모델의 기하학적 특징, 외관 특징, 건물 여부, 장면 여부, 품질 저하 여부 등을 포함한 구조화된 데이터를 생성합니다. 이 구조화된 데이터의 일부는 메시를 자동으로 분류하는 데 사용되고, 생성된 정보들을 종합한 문장은 메시에 대한 설명(캡션)으로 활용됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Classify mesh using vLLM by making the vLLM model to describe the model using 9999 rendered images. Some parts of the structured data (marked with red box) can be used to classify mesh; the aggregated full sentence can be used as the caption of the mesh.
> </details>



![](https://arxiv.org/html/2502.14247/extracted/6223781/figures/texture/text-2-mesh-res-01.png)

> 🔼 그림 12는 입력으로 컬러 이미지를 사용한 시각적 결과를 보여줍니다. 녹색 영역은 텍스처가 없는 렌더링된 다중 뷰 이미지를, 빨간색 영역은 텍스처가 있는 렌더링된 다중 뷰 이미지를 나타냅니다. 이 그림은 Pandora3D 모델이 입력 이미지에 따라 사실적인 3D 모델의 형태와 질감을 정확하게 생성할 수 있음을 보여줍니다.  다양한 각도에서 렌더링된 이미지는 생성된 모델의 완성도를 더욱 명확하게 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Visual results with color image as input, the green areas show the rendered multi-view images without textures and the red areas show the rendered multi-view images with textures.
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
{{< /gallery >}}