---
title: "BrushEdit: All-In-One Image Inpainting and Editing"
summary: "BrushEdit: All-in-One Image Inpainting & Editing."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Generation", "🏢 Peking University",]
showSummary: true
date: 2024-12-13
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.10316 {{< /keyword >}}
{{< keyword icon="writer" >}} Yaowei Li et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-17 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.10316" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.10316" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/brushedit-all-in-one-image-inpainting-and" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

**이미지 편집은 이미지 생성 모델의 발전에도 불구하고 쌍으로 된 데이터 부족과 편집 유형의 다양성으로 인해 여전히 어려움을 겪고 있습니다.** 기존의 반전 기반 방법은 큰 수정이나 구조적 변경에는 어려움을 겪고 있으며 명령어 기반 방법은 종종 블랙박스 작업으로 제한됩니다. **이러한 한계는 사용자의 직접적인 상호 작용과 미세 조정 기능을 제한합니다.**

**BrushEdit은 이러한 문제를 해결하기 위해 LLMs와 이미지 복원 모델을 결합한 획기적인 프레임워크입니다.** 사용자는 텍스트 명령어와 자유 형식 마스크를 통해 이미지를 편집할 수 있으며, 에이전트 기반 시스템이 편집 유형 분류, 객체 식별, 마스크 획득, 복원 영역 채우기를 처리합니다. **BrushEdit의 핵심은 이중 분기 이미지 복원 모델인데, 이 모델은 마스크 이미지 특징을 사전 훈련된 확산 네트워크에 주입하여 향상된 의미적 일관성과 배경 보존을 가능하게 합니다.** 또한, BrushEdit은 통합 마스크 훈련을 통해 다양한 마스크 유형에서 일관된 성능을 제공합니다. 이 프레임워크는 사용자에게 친숙하고, 자유 형식이며, 다중 턴의 대화형 명령어 편집 시스템을 제공하는 동시에 기존 방법의 한계를 해결합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} BrushEdit은 사용자 친화적인 인터페이스를 통해 텍스트 명령어와 자유 형식 마스크를 사용한 이미지 편집을 가능하게 합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 이중 분기 아키텍처와 통합 마스크 훈련 전략으로 편집된 영역과 편집되지 않은 영역 간의 일관성을 보장합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 사전 훈련된 확산 모델과 플러그 앤 플레이 통합이 되며, 규모 조정 및 편집 강도에 대한 유연한 제어를 제공합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**이미지 편집 및 복원 분야에서 혁신적인 프레임워크인 BrushEdit은 연구자들에게 상당한 발전을 가져다줍니다.** 이는 사용자 친화적인 인터페이스와 고품질 편집 기능을 결합한 덕분에 이미지 편집 작업의 효율성과 접근성을 크게 향상시킵니다. 또한, **다양한 사전 학습된 확산 모델과의 플러그 앤 플레이 통합 기능은 연구자들에게 폭넓은 실험 및 응용 분야를 제공합니다.** 게다가, **BrushEdit의 혁신적인 이중 분기 아키텍처와 훈련 전략은 마스크 기반 이미지 편집 및 복원을 위한 새로운 길을 열어줍니다. 마지막으로,** 연구원들은 추가적인 훈련 없이도 최첨단 MLLM과 비전 이해 모델을 활용하여 언어 이해와 제어 가능한 이미지 생성 기능을 향상시킬 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.10316/x2.png)

> 🔼 BrushEdit은 사용자가 자유롭게 그린 마스크를 사용하여 이미지의 일부를 수정하거나 삭제, 추가할 수 있도록 합니다. 이전 버전인 BrushNet-Ran과 BrushNet-Seg는 각각 랜덤 마스크와 세그멘테이션 마스크에 특화되어 학습되었기 때문에 사용자 마스크에서 발생하는 노이즈나 경계 불일치 문제가 있었지만, BrushEdit은 이러한 제약 없이 다양한 마스크 형태를 처리하여 자연스러운 결과물을 생성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: BrushEdit can achieve all-in-one inpainting for arbitrary mask shapes without requiring separate model training for each mask type. This flexibility in handling arbitrary shapes also enhances user-driven editing, as user-provided masks often combine segmentation-based structural details with random mask noise. By supporting arbitrary mask shapes, BrushEdit avoids the artifacts introduced by the random-mask version of BrushNet-Ran and the edge inconsistencies caused by the segmentation-mask version BrushNet-Seg’s strong reliance on boundary shapes.
> </details>





{{< table-caption >}}
| Editing Model | Plug-and-Play | Flexible-Scale | Multi-turn Interactive | Instruction Editing |
|---|---|---|---|---| 
| Prompt2Prompt [8] | ✓ | ✓ |  |  |
| MasaCtrl [9] | ✓ | ✓ |  |  |
| MagicQuill [17] | ✓ | ✓ | ✓ |  |
| InstructPix2Pix [13] |  |  |  | ✓ |
| GenArtist [25] | ✓ |  |  | ✓ |
| *BrushEdit* | ✓ | ✓ | ✓ | ✓ |
| Inpainting Model | Plug-and-Play | Flexible-Scale | Content-Aware | Shape-Aware |
| Blended Diffusion [26, 27] | ✓ |  |  |  |
| SmartBrush [28] |  |  |  | ✓ |
| SD Inpainting [5] |  |  | ✓ | ✓ |
| PowerPaint [29] |  |  | ✓ | ✓ |
| HD-Painter [30] |  |  | ✓ | ✓ |
| ReplaceAnything [31] |  |  | ✓ | ✓ |
| Imagen [32] |  |  | ✓ | ✓ |
| ControlNet-Inpainting [33] | ✓ | ✓ | ✓ |  |
| *BrushEdit* | ✓ | ✓ | ✓ | ✓ |{{< /table-caption >}}

> 🔼 BrushEdit과 기존 이미지 편집/인페인팅 방법을 비교한 표입니다. 이 표에는 일반적으로 사용되는 텍스트 기반 확산 모델만 포함되어 있습니다. 표에서 BrushEdit은 플러그 앤 플레이 방식의 유연한 규모 및 다중 턴 대화형 명령 편집, 플러그 앤 플레이 방식의 유연한 규모 및 콘텐츠 인식 형태 인식을 지원하는 것으로 나타났습니다.
> <details>
> <summary>read the caption</summary>
> TABLE I: Comparison of BrushEdit with Previous Image Editing/Inpainting Methods. Note that we only list commonly used text-guided diffusion methods in this table.
> </details>





### In-depth insights


#### Inpainting-Driven Edits
**인페인팅 기반 편집**은 이미지 수정에 대한 혁신적인 접근 방식으로, 이미지 인페인팅 모델과 언어 모델의 강점을 결합합니다. 이 패러다임은 사용자가 자유 형식 마스크와 텍스트 지침을 사용하여 이미지를 편집할 수 있도록 하여, 편집 유형과 강도를 정확하게 제어할 수 있도록 합니다. 인페인팅 기반 편집의 핵심은 **배경 보존**과 **텍스트 프롬프트 준수**에 있습니다. 편집된 영역과 원본 이미지의 배경 간의 **매끄러운 통합**을 보장하여 사실적이고 일관된 결과를 생성합니다. 또한, 이 기술은 객체 추가, 제거, 속성 수정, 객체 교환과 같은 다양한 편집 작업을 처리할 수 있는 **다재다능함**을 제공합니다. 인페인팅 기반 편집의 **대화형 특성**은 사용자가 편집 프로세스를 세밀하게 제어하여 원하는 결과를 얻을 수 있도록 합니다. 이러한 모든 장점으로 인해 이미지 편집에서 강력하고 사용자 친화적인 방법입니다.

#### MLLM-Guided Editing
**MLLM 기반 편집**은 이미지 편집 분야의 혁신적인 패러다임으로, 텍스트 명령어를 이해하고 시각적 콘텐츠를 생성하는 **멀티모달 대형 언어 모델(MLLM)**의 강점을 활용합니다. 이 접근 방식에서 사용자는 자연어로 편집 지시 사항을 입력하면 MLLM이 이를 해석하고 이미지에 적용할 편집 유형, 대상 객체, 편집 마스크, 대상 캡션을 식별합니다. 이 정보는 **이미지 인페인팅 모델**에 입력되어 마스크된 영역을 수정합니다. MLLM은 편집 프로세스를 안내하는 역할을 하며, 편집 유형 분류, 대상 객체 식별, 편집 마스크 및 캡션 생성과 같은 작업을 수행합니다. 인페인팅 모델은 MLLM에서 제공하는 정보를 기반으로 실제 이미지 편집을 수행합니다. **BrushEdit**과 같은 프레임워크는 MLLM과 이중 분기 인페인팅 모델을 결합하여 자유 형식, 다중 턴 대화형 명령어 편집을 지원하며, 사용자는 중간 제어 정보를 반복적으로 수정하여 원하는 결과를 얻을 수 있습니다. 이를 통해 사용자는 편집 프로세스를 완벽하게 제어할 수 있으며, **배경 충실도 유지**, **편집 지시 사항 준수**, **편집 마스크 경계의 부드러움**, **전반적인 콘텐츠 일관성** 측면에서 우수한 결과를 얻을 수 있습니다. MLLM 기반 편집은 이미지 편집 작업의 효율성과 품질을 크게 향상시킬 잠재력을 가지고 있습니다.

#### Dual-Branch BrushNet
**BrushNet의 이중 분기 구조**는 이미지 편집 및 복원 작업에서 혁신적인 역할을 합니다. 하나의 분기는 마스크 처리된 이미지를 처리하여 편집 지침에 따라 전경 내용을 생성하고, 다른 분기는 마스크 처리되지 않은 영역을 처리하여 배경의 무손실 보존을 보장합니다. 이러한 분리된 접근 방식을 통해 BrushNet은 마스크 경계에서 **일관성과 매끄러움**을 달성하여 생성된 전경과 기존 배경 사이의 **자연스러운 조화**를 이끌어냅니다. 또한, 이중 분기 설계는 **배경 정보가 텍스트 프롬프트의 영향을 받지 않도록 보호**하여 편집된 이미지의 **정확성과 충실도**를 더욱 향상시킵니다. 이는 특히 객체 추가 또는 제거와 같은 **복잡한 구조적 변경**을 수행할 때 기존 방법의 한계를 극복하는 데 중요한 역할을 합니다. 요약하면, BrushNet의 이중 분기 구조는 이미지 편집 및 복원 품질을 크게 향상시켜 **다양한 마스크 유형과 편집 작업에 대한 범용 솔루션**을 제공합니다.

#### Interactive Refinement
**대화형 개선**은 사용자 입력을 통합하여 이미지 편집 프로세스를 개선하는 **반복적 접근 방식**입니다. 사용자는 편집 마스크, 대상 캡션 또는 텍스트 프롬프트와 같은 중간 제어 정보를 수정하여 원하는 결과를 얻을 수 있습니다. 이 **유연성**을 통해 사용자는 편집 내용을 **세밀하게 제어**하고 편집 유형과 강도를 조정할 수 있습니다. 대화형 개선의 주요 이점은 편집의 **점진적 개선**과 **향상된 제어 기능**입니다. 사용자는 여러 단계에서 입력을 제공하여 편집을 **구체화**하고 **최적화**할 수 있으므로 최종 출력이 편집 의도와 **완벽하게 일치**하도록 할 수 있습니다. 또한 이 반복적인 프로세스는 편집 프로세스에서 **투명성**을 향상시켜 사용자가 **쉽게 조정**하고 **원하는 출력**을 얻을 수 있도록 합니다.

#### Arbitrary Mask Editing
**임의 마스크 편집**은 이미지 편집 및 복원에서 혁신적인 기능입니다. 사용자가 **원하는 모양의 마스크를 그리고 편집**할 수 있도록 하여 정확성과 제어 기능을 향상시킵니다. 전통적인 방식은 사각형이나 원형 마스크로 제한되었지만, 이 기술은 복잡한 객체나 불규칙한 영역에도 적용할 수 있습니다. **배경 보존 능력**과 **텍스트 정렬 기능**이 뛰어나 자연스럽고 일관된 결과물을 생성합니다. 또한, **사용자 상호 작용**을 통해 편집 유형 및 강도를 조정할 수 있어 **개인 맞춤형 편집 경험**을 제공합니다. 임의 마스크 편집은 이미지 편집 분야의 발전을 보여주는 핵심 기술입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.10316/x3.png)

> 🔼 BrushEdit 모델의 전체적인 작동 방식을 보여주는 그림입니다. 사용자가 마스크와 마스크된 이미지를 입력하면, 모델은 마스크를 다운샘플링하고 마스크된 이미지를 VAE 인코더에 입력하여 잠재 공간의 분포를 정렬합니다. 그런 다음 노이즈가 있는 잠재 이미지, 마스크된 이미지 잠재 이미지, 그리고 다운샘플링된 마스크를 연결하여 BrushEdit의 입력으로 사용합니다. BrushEdit에서 추출된 특징은 제로 컨볼루션 블록 이후 사전 훈련된 UNet 레이어에 레이어별로 추가됩니다. 노이즈 제거 후 생성된 이미지와 마스크된 이미지를 블러 처리된 마스크를 사용하여 혼합합니다. 이 그림은 BrushEdit이 어떻게 이미지 인페인팅을 수행하는지, 특히 잠재 공간 정렬, 마스크 처리, 특징 추출 및 UNet과의 통합, 그리고 최종 이미지 생성 과정을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Model overview. Our model outputs an inpainted image given the mask and masked image input. Firstly, we downsample the mask to accommodate the size of the latent, and input the masked image to the VAE encoder to align the distribution of latent space. Then, noisy latent, masked image latent, and downsampled mask are concatenated as the input of BrushEdit. The feature extracted from BrushEdit is added to pretrained UNet layer by layer after a zero convolution block[33]. After denoising, the generated image and masked image are blended with a blurred mask.
> </details>



![](https://arxiv.org/html/2412.10316/x4.png)

> 🔼 이 그림은 BrushEdit 평가에 사용된 벤치마크 데이터셋인 BrushBench와 EditBench의 개요를 보여줍니다. I과 II는 각각 BrushBench의 자연 이미지와 인공 이미지, 마스크, 캡션을 나타냅니다. (a)~(d)는 사람, 동물, 실내, 실외 시나리오 이미지를 보여주며, 각 이미지 그룹은 원본 이미지, 내부 인페인팅 마스크, 외부 인페인팅 마스크와 상단에 이미지 캡션을 포함합니다. III는 EditBench의 이미지, 마스크, 캡션을 보여주며, (e)는 생성된 이미지, (f)는 자연 이미지입니다. 모든 이미지는 각 벤치마크에서 무작위로 선택되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Benchmark overview. I and II separately show natural and artificial images, masks, and caption of BrushBench. (a) to (d) show images of humans, animals, indoor scenarios, and outdoor scenarios. Each group of images shows the original image, inside-inpainting mask, and outside-inpainting mask, with an image caption on the top. III show image, mask, and caption from EditBench [32], with (e) for generated images and (f) for natural images. The images are randomly selected from both benchmarks.
> </details>



![](https://arxiv.org/html/2412.10316/x5.png)

> 🔼 이 그림은 다양한 이미지 편집 작업에서 BrushEdit과 기존 편집 방법을 비교한 결과를 보여줍니다. 여기에는 객체 제거(I), 객체 추가(II), 속성 수정(III), 객체 교체(IV)와 같은 편집 작업이 포함됩니다. BrushEdit은 편집된 영역과 편집되지 않은 영역 간의 일관성, 편집 지침 준수, 편집 마스크 경계의 부드러움, 전반적인 콘텐츠 일관성 측면에서 기존 방법보다 우수한 결과를 보여줍니다. 특히 그림 I 및 II는 꽃이나 노트북 삭제, 칼라나 귀걸이 추가와 같은 작업을 보여주는 예시입니다. 기존 방법들은 반전 노이즈로 인한 구조적 아티팩트가 지속되어 만족스러운 결과를 내지 못하는 반면, BrushEdit은 의도한 작업을 성공적으로 수행하고 배경과 조화롭게 어울리는 매끄러운 편집 결과를 생성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Comparison of previous editing methods and BrushEdit on natural and synthetic images, covering image editing operations such as removing objects (I), adding objects (II), modifying attributes (III), and swapping objects (IV).
> </details>



![](https://arxiv.org/html/2412.10316/x6.png)

> 🔼 이 그림은 BrushEdit과 이전 이미지 인페인팅 기법들을 다양한 인페인팅 작업(랜덤 마스크 인페인팅, 세그멘테이션 마스크 인페인팅)에서 비교한 결과를 보여줍니다. 각 결과 그룹에는 Blended Latent Diffusion (BLD), Stable Diffusion Inpainting (SDI), HD-Painter (HDP), PowerPaint (PP), ControlNet-Inpainting (CNI), 이전 버전 BrushNet, 그리고 현재 버전 BrushEdit의 결과가 포함되어 있습니다. 그림 I은 랜덤 마스크 인페인팅, 그림 II는 세그멘테이션 마스크 인페인팅에 대한 결과를 보여주며, BrushEdit이 마스크 처리된 배경 보존과 이미지-텍스트 정렬 측면에서 우수한 성능을 보임을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Performance comparisons of BrushEdit and previous image inpainting methods across various inpainting tasks: (I) Random Mask Inpainting (II) Segmentation Mask Inpainting. Each group of results contains 7777 inpainting methods: (b) Blended Latent Diffusion (BLD) [27], (c) Stable Diffusion Inpainting (SDI) [5], (d) HD-Painter (HDP) [30], (e) PowerPaint (PP) [29], (f) ControlNet-Inpainting (CNI) [33], (g) Our Previous BrushNet and (h) Ours.
> </details>



![](https://arxiv.org/html/2412.10316/x7.png)

> 🔼 이 그림은 커뮤니티에서 미세 조정된 확산 모델에 BrushEdit을 통합하는 방법을 보여줍니다. Stable Diffusion v1.5에서 미세 조정된 5가지 인기 있는 커뮤니티 확산 모델(DreamShaper (DS), epiCRealism (ER), Henmix_Real (HR), MeinaMix (MM), Realistic Vision (RV))을 사용합니다. MM은 특히 애니메이션 이미지용으로 설계되었습니다. 그림은 입력 이미지(a), 다섯 가지 모델의 결과(b-f) 및 마스크(g)를 보여줍니다. 각 모델은 입력 이미지와 마스크를 사용하여 이미지의 마스크된 부분을 채웁니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Integrating BrushEdit to community fine-tuned diffusion models. We use five popular community diffusion models fine-tuned from stable diffusion v1.5: DreamShaper (DS) [99], epiCRealism (ER) [100], Henmix_Real (HR) [101], MeinaMix (MM) [102], and Realistic Vision (RV) [103]. MM is specifically designed for anime images.
> </details>



![](https://arxiv.org/html/2412.10316/x8.png)

> 🔼 BrushEdit의 유연한 제어 척도를 보여줍니다. (a)는 주어진 마스크 이미지를 보여주고, (b)-(h)는 제어 척도 *w*를 1.0에서 0.2까지 추가하는 것을 보여줍니다. 결과는 정밀한 제어에서 대략적인 제어까지 점진적으로 감소하는 제어 능력을 보여줍니다. *w* 값이 감소함에 따라 BrushEdit이 편집 또는 페인팅 중에 마스크되지 않은 영역을 보호하는 정도가 감소하여, 사용자가 정확성과 유연성 사이의 균형을 조정할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Flexible control scale of BrushEdit. (a) shows the given masked image, (b)-(h) show adding control scale w𝑤witalic_w from 1.01.01.01.0 to 0.20.20.20.2. Results show a gradually diminishing controllable ability from precise to rough control.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Inverse | Editing | PSNR ↑ | LPIPS×10³ ↓ | MSE×10⁴ ↓ | SSIM×10² ↑ | CLIP Similariy ↑ |
|---|---|---|---|---|---|---| 
| **DDIM** | **P2P** | 17.87 | 208.80 | 219.88 | 71.14 | 22.44 |
| **PnP** | **P2P** | 27.22 | 54.55 | 32.86 | 84.76 | 22.10 |
| **DDIM** | **MasaCtrl** | 22.17 | 106.62 | 86.97 | 79.67 | 21.16 |
| **PnP** | **MasaCtrl** | 22.64 | 87.94 | 81.09 | 81.33 | 21.35 |
| **DDIM** | **P2P-Zero** | 20.44 | 172.22 | 144.12 | 74.67 | 20.54 |
| **PnP** | **P2P-Zero** | 21.53 | 138.98 | 127.32 | 77.05 | 21.05 |
| **DDIM** | **PnP** | 22.28 | 113.46 | 83.64 | 79.05 | **22.55** |
| **PnP** | **PnP** | 22.46 | 106.06 | 80.45 | 79.68 | **22.62** |
| *BrushEdit* |  | **32.16** | **17.22** | **8.43** | **97.08** | 22.44 |{{< /table-caption >}}
> 🔼 PnpBench에서 BrushEdit와 다양한 편집 방법을 비교한 표입니다. 편집 방법으로는 Prompt-to-Prompt (P2P)[8], MasaCtrl[9], Pix2Pix-Zero (P2P-Zero)[9], Plug-and-Play (PnP)[66]가 있으며, 각각에 대해 DDIM Inversion (DDIM)[2]과 PnP Inversion (PnP)[11]의 두 가지 역변환 기법을 평가하여 더 강력한 기준선을 설정했습니다. 빨간색은 최고 결과, 파란색은 두 번째로 좋은 결과를 나타냅니다. 표에는 PSNR, LPIPS, MSE, SSIM, CLIP 유사도와 같은 메트릭을 사용하여 편집된 영역과 편집되지 않은 영역 모두에서 이미지 품질과 텍스트 정렬을 측정한 결과가 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> TABLE II: Comparison of BrushEdit with various editing methods in PnpBench. For editing methods Prompt-to-Prompt (P2P)[8], MasaCtrl[9], Pix2Pix-Zero (P2P-Zero)[9], and Plug-and-Play (PnP)[66], we evaluate two inversion techniques, DDIM Inversion (DDIM)[2] and PnP Inversion (PnP)[11], to establish stronger baselines. Red stands for the best result, Blue stands for the second best result.
> </details>

{{< table-caption >}}
| Methods | _BrushEdit_ | NP | EF | AIDI | EDICT | NT | Style Diffusion |
|---|---|---|---|---|---|---|---| 
| **Inference Time (s)** | **3.57** | **18.22** | 19.10 | 35.41 | 35.48 | 148.48 | 382.98 |{{< /table-caption >}}
> 🔼 BrushEdit은 이미지 편집 결과는 향상시키면서 다른 역전 기반 편집 방법보다 추론 시간이 훨씬 짧습니다. 표는 BrushEdit과 Negative-Prompt Inversion (NP), Edit Friendly Inversion (EF), AIDI, EDICT, Null-Text Inversion (NT), Style Diffusion + Prompt-to-Prompt 등 다른 역전 기반 방법의 추론 시간을 비교한 결과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> TABLE III: Comparison of inference time between our inpainting-based BrushEdit  and other inversion-based methods, including Negative-Prompt Inversion (NP), Edit Friendly Inversion (EF), AIDI[98], EDICT, Null-Text Inversion (NT), and Style Diffusion added with Prompt-to-Prompt. BrushEdit achieves better editing results with far less inference time than all inversion-based methods.
> </details>

{{< table-caption >}}
|                         | Inside-inpainting |                       Masked Background Fidelity | Text Align | Outside-inpainting |                       Masked Background Fidelity | Text Align |
| ----------------------- | :--------------- | :-------------------------------------------- | :--------- | :---------------- | :-------------------------------------------- | :--------- |
| **Metrics**            | **Models**       | PSNR↑ | MSE×10³↓ | LPIPS×10³↓ | SSIM↑ | **Models**      | PSNR↑ | MSE×10³↓ | LPIPS×10³↓ | SSIM↑ | CLIP Sim↑ |
|                         | **BLD (1)**     | 21.33 | 9.76      | 49.26      | 74.58 | **BLD (1)**    | 15.85 | 35.86      | 21.40      | 77.40 | 26.15     |
|                         | **SDI (2)**     | 21.52 | 13.87     | 48.39      | 89.07 | **SDI (2)**    | 18.04 | 19.87      | 15.13      | 91.42 | 26.17     |
|                         | **HDP (3)**     | 22.61 | 9.95      | 43.50      | 89.03 | **HDP (3)**    | 18.03 | 22.99      | 15.22      | 90.48 | 26.37     |
|                         | **PP (4)**      | 21.43 | 32.73     | 48.43      | 86.39 | **PP (4)**     | 18.04 | 31.78      | 15.13      | 90.11 | **26.48**    |
|                         | **CNI (5)**     | 12.39 | 78.78     | 243.62     | 65.25 | **CNI (5)**    | 11.91 | 83.03      | 58.16      | 66.80 | 26.73     |
|                         | **CNI* (5)**    | 22.73 | 24.58     | 43.49      | 91.53 | **CNI* (5)**   | 17.50 | 37.72      | 19.95      | 94.87 | 27.21     |
|                         | **BrushNet-Seg*** | **31.94** | **0.80**  | **18.67** | **96.55** | **BrushNet-Seg***| **27.82** | **2.25**  | **4.63** | **98.95** | **27.22**     |
|                         | *BrushEdit***      | **31.98** | **0.79**  | 18.92      | **96.68** | *BrushEdit***     | 27.65 | 2.30       | 4.90       | **98.97** | **27.29**    |{{< /table-caption >}}
> 🔼 BrushEdit 및 기타 확산 기반 이미지 보정 모델(Blended Latent Diffusion (BLD), Stable Diffusion Inpainting (SDI), HD-Painter (HDP), PowerPaint (PP), ControlNet-Inpainting (CNI), Segmentation-based BrushNet-Seg)을 BrushBench에서 비교한 정량적 결과입니다. 표는 내부 및 외부 보정 모두에 대한 배경 충실도 및 텍스트 정렬(텍스트 정렬) 지표를 보여줍니다. 모든 모델은 기본 모델로 Stable Diffusion V1.5를 사용합니다. 빨간색은 최고 결과를, 파란색은 두 번째로 좋은 결과를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> TABLE IV: Quantitative comparisons between BrushEdit and other diffusion-based inpainting models in BrushBench: Blended Latent Diffusion (BLD)[27], Stable Diffusion Inpainting (SDI)[5], HD-Painter (HDP)[30], PowerPaint (PP)[29], ControlNet-Inpainting (CNI)[33], and our previous Segmentation-based BrushNet-Seg[22]. The table shows metrics on background fidelity and text alignment (Text Align) for both inside- and outside-inpainting. All models use Stable Diffusion V1.5 as the base model. Red indicates the best result, while Blue indicates the second-best result.
> </details>

{{< table-caption >}}
| Metrics | Masked Background Fidelity | Text Align | CLIP Sim |
|---|---|---|---|---| 
| Models | PSNR↑ | MSE<sub>×10³</sub>↓ | LPIPS<sub>×10³</sub>↓ | SSIM<sub>×10³</sub>↑ | |
| **BLD**[27] | 20.89 | 10.93 | 31.90 | 85.09 | 28.62 |
| **SDI**[5] | 23.25 | 6.94 | 24.30 | 90.13 | 28.00 |
| **HDP**[30] | 23.07 | **6.70** | 24.32 | 92.56 | 28.34 |
| **PP**[29] | 23.34 | 20.12 | 24.12 | 91.49 | 27.80 |
| **CNI**[33] | 12.71 | 69.42 | 159.71 | 79.16 | 28.16 |
| **CNI***[33] | 22.61 | 35.93 | 26.14 | 94.05 | 27.74 |
| **BrushNet-Ran*** | **33.66** | **0.63** | **10.12** | **98.13** | **28.87** |
| *BrushEdit* | **32.97** | **0.70** | **7.24** | **98.60** | **29.62** |{{< /table-caption >}}
> 🔼 EditBench에서 BrushEdit과 다른 확산 기반 이미지 복원 모델(랜덤 마스크 기반 BrushNet-Ran 포함)을 정량적으로 비교한 표입니다. 비교 방법 및 메트릭에 대한 자세한 설명은 표 IV의 캡션을 참조하세요. 빨간색은 최고 결과, 파란색은 두 번째로 좋은 결과를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> TABLE V: Quantitative comparisons among BrushEdit and other diffusion-based inpainting models, Random-mask-based BrushNet-Ran in EditBench. A detailed explanation of compared methods and metrics can be found in the caption of Tab. IV. Red stands for the best result, Blue stands for the second best result.
> </details>

{{< table-caption >}}
| Metrics | Image Quality | | | Masked Region Preservation | | | Text Align | 
|---|---|---|---|---|---|---|---| 
| Model | IR×10↑ | HPS×10²↑ | AS↑ | PSNR↑ | MSE×10²↓ | LPIPS×10³↓ | CLIP Sim↑ |
|---|---|---|---|---|---|---|---| 
| SDI | 11.00 | 27.53 | 6.53 | 19.78 | 16.87 | 31.76 | 26.69 |
| w/o fine-tune | 11.59 | 27.71 | 6.59 | 19.86 | 16.09 | 31.68 | 26.91 |
| w/ fine-tune | **11.63** | **27.73** | **6.60** | **20.13** | **15.84** | **31.57** | **26.93** |{{< /table-caption >}}
> 🔼 이 표는 이중 분기 디자인에 대한 절제 연구 결과를 보여줍니다. Stable Diffusion Inpainting(SDI)은 전체 UNet이 미세 조정되는 단일 분기 디자인을 사용합니다. 기본 UNet을 미세 조정하는 것과 고정하는 두 가지 변형으로 이중 분기 모델을 학습하여 절제 분석을 수행했습니다. 결과는 이중 분기 디자인을 채택하여 달성한 우수한 성능을 보여줍니다. BrushEdit은 이미지 품질, 마스크 영역 보존, 텍스트 정렬의 세 가지 측면에서 평가됩니다. Image Quality는 생성된 이미지의 품질을 평가하고 Masked Region Preservation은 마스크되지 않은 영역이 얼마나 잘 보존되었는지 평가하고 Text Align은 생성된 이미지가 텍스트 프롬프트와 얼마나 잘 일치하는지 평가합니다. 각 메트릭에 대해 가장 높은 값이 빨간색으로 강조 표시됩니다.
> <details>
> <summary>read the caption</summary>
> TABLE VI: Ablation on dual-branch design. Stable Diffusion Inpainting (SDI) use single-branch design, where the entire UNet is fine-tuned. We conducted an ablation analysis by training a dual-branch model with two variations: one with the base UNet fine-tuned, and another with the base UNet forzened. Results demonstrate the superior performance achieved by adopting the dual-branch design. Red is the best result.
> </details>

{{< table-caption >}}
| Metrics | Image Quality | Masked Region Preservation | Text Align |
|---|---|---|---|---|---|---|---|---|---|
| Enc | Mask | Attn | UNet | Blend | IR×10↑ | HPS×10²↑ | AS↑ | PSNR↑ | MSE×10²↓ | LPIPS×10³↓ | CLIP Sim↑ |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Conv | w/ | w/o | full | w/o | 11.05 | 26.23 | 6.55 | 14.89 | 37.23 | 64.54 | 26.76 |
| VAE | w/o | w/o | full | w/o | 11.55 | 27.70 | 6.57 | 17.96 | 26.38 | 49.33 | 26.87 |
| VAE | w/ | w/ | full | w/o | 11.25 | 27.62 | 6.56 | 18.69 | 19.44 | 34.28 | 26.63 |
| Conv | w/ | w/ | CN | w/o | 9.58 | 26.85 | 6.47 | 12.15 | 80.91 | 150.89 | 26.88 |
| VAE | w/ | w/ | CN | w/o | 10.53 | 27.42 | 6.59 | 18.28 | 24.36 | 41.63 | 26.89 |
| VAE | w/ | w/o | CN | w/o | 11.42 | 27.69 | 6.58 | 18.49 | 24.09 | 36.33 | 26.86 |
| VAE | w/ | w/o | half | w/o | 11.47 | 27.70 | 6.57 | 19.01 | 23.77 | 33.57 | 26.87 |
| VAE | w/ | w/o | full | w/o | **11.76** | **27.94** | 6.59 | **29.88** | **1.53** | **11.65** | **26.91** |
| VAE | w/ | w/o | full | paste | 11.72 | 27.93 | 6.58 | - | - | - | 26.80 |
{{< /table-caption >}}
> 🔼 이 표는 이미지 인페인팅 작업에서 다양한 모델 디자인의 영향을 조사하기 위한 절제 연구 결과를 보여줍니다. BrushEdit은 이미지 인페인팅 모델을 기반으로 하므로 편집 작업은 MLLM, BrushEdit 및 객체 감지 모델을 에이전트로 연결하여 추론만으로 수행됩니다. 인페인팅 기능은 모델의 훈련 결과를 직접적으로 반영합니다. 표 VII은 이중 분기 및 단일 분기 설계를 비교하고 추가 분기 아키텍처에 대한 절제 연구를 강조 표시합니다.  BrushBench에서 수행된 절제 연구는 내부 인페인팅과 외부 인페인팅 모두에 대한 성능을 평균적으로 나타냅니다. 표에서 다음과 같은 구성 요소들을 변경하며 실험했습니다.  * 이미지 인코더(Enc): 무작위로 초기화된 컨볼루션(Conv) 및 VAE 중에서 선택 * 마스크 입력 포함(Mask): 추가(w/) 및 추가하지 않음(w/o) 중에서 선택 * 교차 주의 레이어 존재(Attn): 추가(w/) 및 추가하지 않음(w/o) 중에서 선택 * UNet 특징 추가 유형(UNet): 전체 UNet 특징 추가(full), UNet 특징의 절반 추가(half) 및 ControlNet과 같은 특징 추가(CN) 중에서 선택 * 혼합 연산(Blend): 추가하지 않음(w/o), 직접 붙여넣기(paste) 및 흐린 혼합(blur) 중에서 선택  결과는 이중 분기 설계가 단일 분기 설계보다 성능이 훨씬 뛰어나다는 것을 보여줍니다. 또한 이중 분기 설정에서 기본 확산 모델을 미세 조정하면 고정하는 것보다 우수한 결과를 얻을 수 있습니다. 그러나 미세 조정하면 모델에 대한 유연성과 제어가 제한될 수 있습니다. 성능과 유연성 사이의 균형을 고려하여 모델에 고정된 이중 분기 설계를 채택했습니다.
> <details>
> <summary>read the caption</summary>
> TABLE VII: Ablation on model architecture. We ablate on the following components: the image encoder (Enc), selected from a random initialized convolution (Conv) and a VAE; the inclusion of mask in input (Mask), chosen from adding (w/) and not adding (w/o); the presence of cross-attention layers (Attn), chosen from adding (w/) and not adding (w/o); the type of UNet feature addition (UNet), selected from adding the full UNet feature (full), adding half of the UNet feature (half), and adding the feature like ControlNet (CN); and finally, the blending operation (Blend), chosen from not adding (w/o), direct pasting (paste), and blurred blending (blur). Red is the best result.
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
{{< /gallery >}}