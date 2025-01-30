---
title: "DiffSplat: Repurposing Image Diffusion Models for Scalable Gaussian Splat Generation"
summary: "DIFFSPLAT: 웹 규모 2D 이미지 확산 모델을 활용, 3D 가우시안 스플랫 생성을 위한 확장 가능한 프레임워크 제시!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Generation", "🏢 Peking University",]
showSummary: true
date: 2025-01-28
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.16764 {{< /keyword >}}
{{< keyword icon="writer" >}} Chenguo Lin et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-29 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.16764" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.16764" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/diffsplat-repurposing-image-diffusion-models" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

3D 콘텐츠 생성은 게임, 디지털 아트 등 다양한 분야에서 중요하지만, 고품질 3D 데이터 부족과 2D 멀티뷰 생성의 불일치 문제로 인해 어려움을 겪고 있습니다. 특히, 기존의 방법들은 대규모 데이터셋을 필요로 하거나 3D 일관성을 유지하기 어려운 문제점이 있었습니다.

본 논문에서는 이러한 문제점을 해결하기 위해, **웹 규모의 2D 이미지 확산 모델을 활용하여 3D 가우시안 스플랫을 생성하는 새로운 프레임워크인 DIFFSPLAT을 제안**합니다.  DIFFSPLAT은 3D 일관성을 유지하면서 2D 이미지 확산 모델의 사전 학습된 정보를 활용하고, 경량화된 재구성 모델을 통해 확장 가능한 데이터셋을 구축합니다. 실험 결과, DIFFSPLAT은 기존 모델보다 우수한 성능을 보였으며, 각 설계 선택의 효과를 검증하는 추가 실험도 진행했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 웹 규모의 2D 이미지 확산 모델을 효과적으로 활용하여 3D 가우시안 스플랫을 생성하는 새로운 프레임워크 DIFFSPLAT 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 기존 3D 생성 모델의 한계점인 3D 데이터 부족 및 2D 멀티뷰 생성의 불일치 문제를 효과적으로 해결 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 3D 일관성 유지하면서 다양한 이미지 생성 기술을 3D 영역에 적용 가능하게 함으로써, 3D 콘텐츠 생성의 확장성과 품질 향상 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **웹 규모의 2D 이미지 확산 모델을 활용하여 3D 콘텐츠 생성의 확장성 및 품질을 크게 향상시키는 새로운 프레임워크인 DIFFSPLAT을 제시**함으로써, 3D 생성 분야 연구자들에게 중요한 의미를 지닙니다. **기존의 어려움을 극복하고 새로운 가능성을 제시**하여 향후 3D 생성 기술 발전에 크게 기여할 것으로 예상됩니다. 또한, 본 연구는 **다양한 이미지 생성 기술을 3D 영역에 원활하게 적용**할 수 있는 방법을 제시함으로써, 이미지 생성 분야 연구자들에게도 시사하는 바가 큽니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.16764/x1.png)

> 🔼 그림 1은 기존 3D 확산 생성 모델들과 본 논문에서 제안하는 DiffSplat 방법의 비교를 보여줍니다. (1) 기존의 Native 3D 방법과 (2) Rendering-based 방법은 3D 데이터셋의 부족으로 인해 3D 확산 모델 학습에 어려움을 겪습니다. (3) Reconstruction-based 방법은 생성된 멀티뷰 이미지의 일관성 문제를 가지고 있습니다. 반면에 (4) DiffSplat은 사전 학습된 이미지 확산 모델을 활용하여 3D Gaussian Splat(3DGS)를 직접 생성함으로써 2D 확산 사전 정보를 효과적으로 활용하고 3D 일관성을 유지합니다.  'GT'는 확산 손실 계산에 사용되는 3D 표현의 정답 데이터를 의미합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Comparison with Previous 3D Diffusion Generative Models. (1) Native 3D methods and (2) rendering-based methods encounter challenges in training 3D diffusion models from scratch with limited 3D data. (3) Reconstruction-based methods struggle with inconsistencies in generated multi-view images. In contrast, (4) DiffSplat leverages pretrained image diffusion models for the direct 3DGS generation, effectively utilizing 2D diffusion priors and maintaining 3D consistency. “GT” refers to ground-truth samples in a 3D representation used for diffusion loss computation.
> </details>





{{< table-caption >}}
| Single Object | ↑ CLIP Sim.% | DiffSplat | GVGEN | LN3Diff | DIRECT-3D | 3DTopia | LGM† | GRM† |
|---|---|---|---|---|---|---|---|---|
| ↑ CLIP Sim.% | **30.95** | 23.66 | 24.36 | 24.80 | 25.55 | **29.96** | 28.19 |
| ↑ CLIP R-Prec.% | **81.00** | 23.25 | 27.25 | 30.75 | 34.50 | **78.00** | 64.75 |
| ↑ ImageReward | **-0.491** | -2.156 | -2.008 | -2.005 | -1.998 | **-0.720** | -1.337 |
| Single Object w/ Sur. | ↑ CLIP Sim.% | **30.20** | 22.65 | 22.75 | 23.05 | 24.31 | **27.79** | 26.24 |
| ↑ CLIP R-Prec.% | **80.75** | 26.75 | 22.00 | 25.75 | 39.00 | **55.00** | 51.25 |
| ↑ ImageReward | **-0.674** | -2.251 | -2.244 | -2.191 | -2.230 | **-1.772** | -1.869 |
| Multiple Objects | ↑ CLIP Sim.% | **29.46** | 21.48 | 21.65 | 21.89 | 22.88 | **27.07** | 24.33 |
| ↑ CLIP R-Prec.% | **69.50** | 8.00 | 8.75 | 7.75 | 16.50 | **51.00** | 26.50 |
| ↑ ImageReward | **-0.849** | -2.272 | -2.267 | -2.249 | -2.225 | **-1.731** | -2.116 |{{< /table-caption >}}

> 🔼 표 1은 T3Bench 프롬프트에 대한 텍스트 조건 생성에 대한 정량적 평가 결과를 보여줍니다. 이 표는 다양한 방법들을 사용하여 생성된 3D 모델의 품질을 평가한 결과를 보여줍니다. 특히, CLIP 유사도 점수, CLIP R-정밀도, ImageReward 점수를 사용하여 텍스트 프롬프트와 생성된 이미지의 정렬 정도와 미적 선호도를 측정했습니다.  단일 개체, 주변 환경이 있는 단일 개체, 여러 개체 등 세 가지 유형의 프롬프트에 대해 평가를 수행하여 다양한 조건에서의 성능을 비교 분석합니다.  † 표시는 추가적인 텍스트 조건 다중 뷰 생성 모델이 필요한 재구성 기반 방법임을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Quantitive evaluations on T3Bench prompts for text-conditioned generation. † indicates reconstruction-based methods that require additional text-conditioned multi-view generative models.
> </details>





### In-depth insights


#### 2D Priors in 3D
본 논문에서 제시된 "2D Priors in 3D" 개념은 **2차원 이미지 데이터의 풍부한 사전 정보(prior)**를 활용하여 **3차원 콘텐츠 생성의 어려움을 극복**하는 전략을 의미합니다.  기존 3차원 생성 모델들은 3차원 데이터의 부족으로 인해 학습에 어려움을 겪고, 생성 결과의 품질과 일관성이 떨어지는 문제점을 가지고 있습니다.  이를 해결하기 위해, 본 논문에서는 **대규모 2차원 이미지 데이터셋을 사전 학습한 이미지 확산 모델(image diffusion model)의 지식을 3차원 생성에 활용**합니다.  즉, 2차원 이미지에서 얻은 풍부한 특징 정보들을 3차원 공간으로 전이하여 3차원 모델 학습에 활용함으로써, 데이터 부족 문제를 해결하고 생성 성능을 향상시키는 것입니다.  **이미지 확산 모델의 강력한 표현력과 일반화 능력**을 활용하여, **다양한 3차원 객체를 효율적이고 정확하게 생성**할 수 있습니다.  **핵심은 2차원 이미지 특징을 3차원 공간으로 매핑하는 기술**이며, 이는 3차원 객체의 다양한 뷰(view)를 정확하게 생성하는 데 중요한 역할을 합니다.  결과적으로, 본 논문은 2차원 이미지 데이터의 우수한 사전 정보를 적절히 활용하여 3차원 생성 모델의 성능 향상을 도모하는 혁신적인 방법을 제시합니다.

#### Splat Reconstruction
본 논문에서 제시된 '스플랫 재구성(Splat Reconstruction)'은 3D 콘텐츠 생성을 위한 **데이터 확보의 어려움**을 해결하기 위한 핵심 기법입니다. 기존의 방법들이 고품질 3D 데이터셋에 의존하는 반면, **저해상도 2D 이미지 여러 장**을 이용하여 3D 가우시안 스플랫(Gaussian splat)을 효율적으로 생성하는 방식입니다. 이는 웹 스케일의 방대한 2D 이미지 데이터를 활용하여 **데이터 부족 문제**를 해결하고, **3D 일관성**을 유지하며 **확장성 있는 3D 데이터셋**을 구축할 수 있다는 점에서 큰 장점이 있습니다.  **경량화된 재구성 모델**을 통해 다수의 2D 이미지로부터 스플랫 그리드를 빠르게 생성하고, 이를 기반으로 3D 렌더링 손실(loss)을 활용하여 각도에 따른 3D 일관성을 확보합니다.  이는 기존 방법들의 **고비용의 3D 데이터 수집** 및 **3D 일관성 유지의 어려움**을 극복하는 중요한 전략입니다.

#### DIFFSPLAT Model
DIFFSPLAT 모델은 텍스트 또는 이미지 조건으로 3D 가우시안 스플랫을 생성하는 새로운 생성적 프레임워크입니다.  **기존의 3D 생성 모델들과 달리 웹 규모의 2D 사전 학습된 이미지 확산 모델을 효과적으로 활용**하여 3D 일관성을 유지하면서 고품질의 3D 콘텐츠 생성을 가능하게 합니다.  **핵심은 대규모 2D 이미지 데이터셋의 생성적 사전 정보를 활용**하여 3D 가우시안 스플랫의 속성들을 직접 생성하는 것입니다.  여기에는 경량화된 재구성 모델을 통해 다중 뷰 가우시안 스플랫 그리드를 빠르게 생성하는 스케일러블한 데이터셋 생성 과정도 포함됩니다. **3D 일관성을 향상시키기 위해 3D 렌더링 손실을 추가**하여 임의의 뷰에서 3D 응집력을 유도합니다.  이러한 설계 덕분에 이미지 생성 기술들을 3D 영역에 매끄럽게 적용할 수 있으며, 다양한 하류 응용 분야에 활용 가능성이 높습니다.  **결론적으로 DIFFSPLAT는 2D 사전 정보의 효율적인 활용과 3D 일관성 유지**라는 두 마리 토끼를 잡은 혁신적인 모델로, 3D 콘텐츠 생성 분야에 중요한 발전을 가져올 것으로 예상됩니다.

#### Ablation Study
본 논문의 ablation study는 **DIFFSPLAT 모델의 각 구성 요소 및 설계 선택의 효과**를 체계적으로 평가하기 위해 수행되었습니다.  구체적으로, **구조화된 스플랫 재구성을 위한 다양한 입력(기하학적 안내 포함 여부), 스플랫 잠재 공간 표현 전략(VAE 미세 조정 전략), 및 DIFFSPLAT 생성 모델의 학습 목적 함수(확산 손실과 렌더링 손실의 상대적 가중치)**에 대한 실험 결과를 제시합니다.  각 실험은 **일관된 3D 일관성과 고품질 3D 콘텐츠 생성**이라는 두 가지 주요 목표에 미치는 영향을 정량적으로 측정하여 분석합니다.  **결과적으로, 각 구성 요소의 중요성과 상호 작용을 명확히 밝히고 최적의 모델 구성을 제시**함으로써, DIFFSPLAT 모델의 강건성과 일반화 성능을 향상시키는 데 기여합니다.  **특히, 렌더링 손실의 효과를 강조하며,** 이를 통해 생성된 3D 콘텐츠의 3D 일관성과 시각적 충실도를 크게 향상시킬 수 있음을 보여줍니다.

#### Future of 3DGen
3DGen의 미래는 **데이터, 모델, 그리고 응용 분야** 세 가지 측면에서 매우 흥미로운 가능성을 제시합니다.  **대용량 고품질 3D 데이터셋의 확보**는 여전히 핵심 과제이며,  합성 데이터 생성, 기존 2D 데이터 활용, 그리고 효율적인 데이터 증강 기술의 발전이 중요합니다.  **모델 측면**에서는, 더욱 **강력하고 일반화된 3D 생성 모델** 개발이 필요하며,  **다양한 3D 표현 방식** (메시, 볼륨, 점군 등) 간의 통합 및 상호 변환 기술, 그리고 **텍스트, 이미지, 비디오 등 다양한 조건**에 대한 효과적인 조건화 기법이 중요한 연구 방향입니다. 마지막으로, **응용 분야의 확장**은 3DGen 기술의 실질적인 가치를 결정합니다. 게임, 영화, 건축, 의료 등 다양한 분야에서의 혁신적인 응용 사례 개발과, **실시간 상호 작용 및 몰입형 경험 제공**을 위한 기술 발전이 3DGen의 미래를 좌우할 것입니다. 특히 **메타버스, 디지털 트윈, VR/AR 등 새로운 플랫폼**과의 결합은 3DGen 기술의 잠재력을 극대화할 수 있는 중요한 기회가 될 것입니다.  결론적으로 3DGen의 미래는 **데이터 기반의 지속적인 기술 발전과, 다양한 분야와의 융합을 통한 응용 확장**에 달려 있습니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.16764/x2.png)

> 🔼 그림 2는 DIFFSPLAT의 세 가지 주요 구성 요소를 보여주는 개념도입니다. 먼저, (1)에서 가벼운 재구성 모델을 사용하여 고품질의 구조화된 3D 데이터 표현을 생성하여 가상 데이터셋을 만드는 과정을 보여줍니다. 다음으로, (2)에서 이미지 VAE(Variational Autoencoder)를 미세 조정하여 가우시안 스플랫 속성을 공유된 잠재 공간에 인코딩하는 방법을 보여줍니다. 마지막으로, (3)에서 텍스트-이미지 확산 모델의 2D 사전 정보를 활용하여 이미지 및 텍스트 조건 하에 3D 콘텐츠를 생성하는 DIFFSPLAT 모델을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Method Overview. (1) A lightweight reconstruction model provides high-quality structured representation for “pseudo” dataset curation. (2) Image VAE is fine-tuned to encode Gaussian splat properties into a shared latent space. (3) DiffSplat is natively capable of generating 3D contents by image and text conditions utilizing 2D priors from text-to-image diffusion models.
> </details>



![](https://arxiv.org/html/2501.16764/x3.png)

> 🔼 그림 3은 텍스트 조건부 3D 생성에 대한 정성적 결과 및 비교를 보여줍니다. DiffSplat은 다양한 텍스트 프롬프트에 대해 고품질의 3D 모델을 생성하는 능력을 보여주는 반면, 다른 방법들은 품질이나 일관성 측면에서 부족함을 드러냅니다. DiffSplat 결과에 대한 추가 시각화는 부록 그림 9, 10 및 11에 제공됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Qualitative Results and Comparisons on Text-conditioned 3D Generation. More visualizations of DiffSplat results are provided in Appendix Figure 9, 10 and 11.
> </details>



![](https://arxiv.org/html/2501.16764/x4.png)

> 🔼 그림 4는 이미지 조건부 3D 생성에 대한 정성적 결과 및 비교를 보여줍니다. DiffSplat은 다양한 이미지를 입력으로 받아 3D 모델을 생성하는데, 이때 다양한 각도에서 생성된 결과를 보여줍니다. DiffSplat의 추가적인 시각화 결과는 부록 그림 12, 13, 14에서 확인할 수 있습니다.  이 그림은 다양한 기존 방법들과 DiffSplat의 성능을 비교하여 DiffSplat의 우수성을 보여주는 데 초점을 맞추고 있습니다. 각 이미지에 대해 DiffSplat이 생성한 여러 각도의 3D 모델이 제시되어 모델의 정확도와 일관성을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Qualitative Results and Comparisons on Image-conditioned 3D Generation. More visualizations of DiffSplat results are provided in Appendix Figure 12, 13 and 14.
> </details>



![](https://arxiv.org/html/2501.16764/x5.png)

> 🔼 그림 5는 제어 가능한 텍스트-3D 생성을 보여줍니다. ControlNet을 DiffSplat에 통합하여 법선, 깊이 맵, Canny 에지와 같은 다양한 형식의 제어를 사용하여 3D 모델을 생성할 수 있습니다. 이를 통해 사용자는 원하는 특징을 가진 3D 오브젝트를 생성할 수 있습니다. 예를 들어, 법선 맵을 사용하여 3D 오브젝트의 표면 질감을 제어하거나, 깊이 맵을 사용하여 3D 오브젝트의 형태를 조절하거나, Canny 에지를 사용하여 3D 오브젝트의 윤곽선을 명확하게 할 수 있습니다. ControlNet의 유연성과 DiffSplat의 3D 생성 기능이 결합되어 다양한 스타일과 형태의 3D 모델을 생성할 수 있는 가능성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Controllable Generation. ControlNet can seamlessly adapt to DiffSplat for controllable text-to-3D generation in various formats, such as normal and depth maps, and Canny edges.
> </details>



![](https://arxiv.org/html/2501.16764/x6.png)

> 🔼 표 3은 구조화된 스플랫 재구성을 위한 입력에 대한 추가적인 실험 결과를 보여줍니다.  다양한 입력 조합 (RGB 이미지만, 노말 맵 추가, 좌표 맵 추가, 세 가지 모두 사용)에 따른 재구성 성능을 정량적으로 비교하여,  각 입력이 스플랫 재구성에 미치는 영향과 효과를 분석합니다.  특히, 기하학적 정보를 제공하는 노말 맵과 좌표 맵이 RGB 이미지만을 사용하는 경우보다 더 나은 재구성 결과를 가져오는지 여부를 확인합니다. 이를 통해 스플랫 재구성에 가장 효과적인 입력 조합을 제시하고,  그 이유를 설명합니다.  해당 표는  DIFFSPLAT 모델의 데이터 준비 과정에서 스플랫 재구성의 중요성과 효율성을 강조하는 데 기여합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Ablation study of inputs for structured splat reconstruction.
> </details>



![](https://arxiv.org/html/2501.16764/x7.png)

> 🔼 이 표는 3D 객체를 나타내는 가우시안 스플랫 속성을 자동으로 인코딩하는 다양한 전략에 대한 실험 결과를 보여줍니다.  자동 인코딩 과정에서 원본 이미지 VAE를 고정하거나, 렌더링 손실을 사용하지 않거나, 다양한 사전 훈련된 이미지 확산 모델(SD1.5, SDXL, SD3)을 사용하는 등 여러 가지 변형을 시도하여 그 결과를 비교 분석합니다.  각 전략의 성능은 PSNR, SSIM, LPIPS 지표를 통해 평가됩니다. 이를 통해 어떤 전략이 가우시안 스플랫의 고품질 표현을 위한 최적의 자동 인코딩 방법인지 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Ablation study for Gaussian splat property auto-encoding strategies.
> </details>



![](https://arxiv.org/html/2501.16764/x8.png)

> 🔼 그림 6은 렌더링 손실 함수(ℒrender)의 영향을 보여줍니다. 텍스트 조건 및 이미지 조건 DiffSplat 모델 모두에서 렌더링 손실 함수를 사용하면 더욱 미적인 3D 콘텐츠가 생성되고, 투명한 부유물(translucent floaters)이 줄어드는 것을 확인할 수 있습니다.  즉, 렌더링 손실 함수는 3D 모델의 시각적 품질을 향상시키는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Ablation of ℒrendersubscriptℒrender\mathcal{L}_{\text{render}}caligraphic_L start_POSTSUBSCRIPT render end_POSTSUBSCRIPT. Both text- (1st row) and image-conditioned (2nd row) DiffSplat with ℒrendersubscriptℒrender\mathcal{L}_{\text{render}}caligraphic_L start_POSTSUBSCRIPT render end_POSTSUBSCRIPT produces more aesthetic and textured 3D content with fewer translucent floaters.
> </details>



![](https://arxiv.org/html/2501.16764/x9.png)

> 🔼 그림 7은 3D 가우시안 스플랫(3DGS) 속성을 시각화한 것으로, 여러 개의 뷰에서 얻은 가우시안 스플랫 그리드를 잠재 공간으로 인코딩하고, 이미지 확산 VAE로 디코딩하여 얻은 결과를 보여줍니다.  그리드 형태로 정리된 3DGS 속성들은 각각 색상(Color), 깊이(Depth), 불투명도(Opacity), 크기(Scale), 회전(Rotation) 등을 나타내며, 이미지 확산 VAE를 통해 디코딩된 가우시안 스플랫(Decoded GS)은 원본 개체를 특정 스타일로 표현하거나 특수한 조명 환경에서 렌더링한 것과 같습니다.  이를 통해 이미지 확산 모델을 3DGS 생성에 활용할 수 있는 가능성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Splat Latents Visualization. 3DGS properties are structured in grids. “Decoded GS” shows the splat latents decoded by an image diffusion VAE.
> </details>



![](https://arxiv.org/html/2501.16764/x10.png)

> 🔼 그림 8은 다양한 조건(텍스트 및 이미지)을 사용하여 3D 콘텐츠를 생성하는 DiffSplat의 제어 가능성을 보여줍니다.  단일 뷰 이미지와 텍스트 설명을 사용하여 정확한 3D 모델을 재구성하는 DiffSplat의 기능을 보여주는 여러 예시가 제시되어 있습니다.  DiffSplat은 텍스트 이해 능력을 기반으로 이미지 정보와 텍스트 정보를 효과적으로 결합하여 보다 정교하고 세밀한 3D 모델 생성을 가능하게 합니다.  여러가지 입력 조건을 처리하는 DiffSplat의 유연성과 강력함을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Controllable Generation with Multi-modal Conditions. DiffSplat can effectively utilize both text and image conditions for single-view reconstruction with text understanding.
> </details>



![](https://arxiv.org/html/2501.16764/x11.png)

> 🔼 이 그림은 논문의 텍스트 조건 DiffSplat 결과를 보여줍니다. 다양한 텍스트 프롬프트에 대한 3D Gaussian splat 모델의 생성 결과를 시각적으로 보여주는 여러 개의 이미지가 포함되어 있습니다. 각 이미지는 텍스트 프롬프트와 그에 따른 3D 모델의 다양한 각도에서의 렌더링 결과를 보여줍니다. 이를 통해 모델의 텍스트 이해 능력과 3D 모델 생성 능력을 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: More results of text-conditioned DiffSplat.
> </details>



![](https://arxiv.org/html/2501.16764/x12.png)

> 🔼 그림 10은 본 논문에서 제안하는 DiffSplat 모델을 사용하여 텍스트 조건으로 생성한 3D 모델들의 추가적인 결과물들을 보여줍니다. 다양한 텍스트 프롬프트(예: 모래사장에 있는 조개껍데기, 국그릇에 담긴 수저, 나뭇가지에 앉아있는 울새, 수정병에 꽂힌 빨간 장미 등)에 따른 3D Gaussian splat 모델 생성 결과를 시각적으로 보여줌으로써, DiffSplat 모델의 다양한 객체 및 장면 생성 능력을 확인할 수 있습니다. 각 프롬프트당 여러 각도에서 렌더링된 이미지들이 제시되어 3D 모델의 입체감과 정확성을 더욱 명확하게 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: More results of text-conditioned DiffSplat.
> </details>



![](https://arxiv.org/html/2501.16764/x13.png)

> 🔼 그림 11은 본 논문에서 제안하는 DiffSplat 모델을 사용하여 텍스트 조건으로 생성한 3D 모델의 추가 결과물들을 보여줍니다. 다양한 텍스트 프롬프트에 대한 3D 모델 생성 결과를 보여줌으로써, DiffSplat의 다양한 객체 및 장면 생성 능력을 시각적으로 보여줍니다. 각 프롬프트에 대해 여러 각도에서 본 3D 모델들을 보여주어, 생성된 모델의 3차원적 특징을 더욱 잘 이해할 수 있도록 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: More results of text-conditioned DiffSplat.
> </details>



![](https://arxiv.org/html/2501.16764/x14.png)

> 🔼 그림 12는 이미지를 조건으로 하여 DiffSplat 모델이 생성한 3D 모델들의 추가적인 결과물들을 보여줍니다.  다양한 종류의 물체들(인형, 동물 모형, 조명, 가구 등)에 대해 입력 이미지와 유사한 3D 모델들을 생성하는 DiffSplat의 성능을 보여주는 여러 관점(시각)에서의 렌더링 결과들이 포함되어 있습니다. 각 물체에 대해 여러 각도의 렌더링된 이미지들을 통해 3D 모델의 형태 및 질감이 잘 재현되었음을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: More results of image-conditioned DiffSplat.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
|Method|DiffSplat|3DTopia-XL|LN3Diff|LGM<sup>†</sup>|GRM<sup>†</sup>|LaRa<sup>†</sup>|CRM<sup>†</sup>|InstantMesh<sup>†</sup>|
|---|---|---|---|---|---|---|---|---|
|↑ PSNR|**22.91**|17.27|16.67|18.25|**19.65**|18.87|18.56|19.14|
|↑ SSIM|**0.892**|0.840|0.831|0.841|0.869|0.852|0.855|**0.876**|
|↓ LPIPS|**0.107**|0.175|0.177|0.166|0.141|0.202|0.149|**0.128**|{{< /table-caption >}}
> 🔼 표 2는 단일 이미지에서 3D 콘텐츠 생성을 위해 추가적인 이미지 생성 모델이 필요한 재구성 기반 방법을 나타내는 † 기호와 함께 이미지 조건부 생성에 대한 GSO 데이터셋에 대한 정량적 평가 결과를 보여줍니다.  이 표는 다양한 방법들의 PSNR, SSIM, LPIPS 지표를 비교하여 이미지 조건부 3D 생성 성능을 비교 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Quantitative evaluations on GSO for image-conditioned generation. † indicates reconstruction methods that require additional image generation models for single image-to-3D generation.
> </details>

{{< table-caption >}}
| Metric | ↑ PSNR | ↑ SSIM | ↓ LPIPS | #Param. |
|---|---|---|---|---|
| LGM | 26.48 | 0.892 | 0.077 | 415M |
| GRM | 28.04 | 0.959 | 0.031 | 179M |
| RGB | 27.43 | 0.956 | 0.041 | 42M |
| +Normal | 28.89 | 0.957 | 0.033 | 42M |
| +Coord. | 29.87 | 0.961 | 0.028 | 42M |
| Ours | **30.09** | **0.963** | **0.027** | 42M |{{< /table-caption >}}
> 🔼 표 5는 DiffSplat 모델의 설계 선택에 대한 ablation study 결과를 보여줍니다.  다양한 디자인 선택(예: multi-view 방식, 손실 함수, 기본 모델 등)을 변경하여 성능 변화를 정량적으로 분석합니다. 각 디자인 선택에 따른 CLIP 유사도, CLIP R-정밀도, ImageReward 점수, PSNR, SSIM, LPIPS 값을 비교하여 어떤 설계 선택이 3D 생성 성능에 가장 큰 영향을 미치는지 확인합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Ablation study of DiffSplat design choices.
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