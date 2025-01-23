---
title: "Hunyuan3D 2.0: Scaling Diffusion Models for High Resolution Textured 3D Assets Generation"
summary: "Hunyuan3D 2.0: 고해상도 텍스처 3D 자산 생성을 위한 대규모 확산 모델 시스템!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "3D Vision", "🏢 Tencent AI Lab",]
showSummary: true
date: 2025-01-21
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.12202 {{< /keyword >}}
{{< keyword icon="writer" >}} Zibo Zhao et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-22 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.12202" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.12202" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/hunyuan3d-2-0-scaling-diffusion-models-for" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

현대 사회에서 디지털 3D 자산의 중요성이 증대함에 따라, 고해상도 텍스처 3D 자산을 자동으로 생성하는 기술에 대한 요구가 높아지고 있습니다. 하지만 기존의 3D 생성 모델들은 해상도, 텍스처 품질, 조건 이미지와의 정합성 등에서 한계를 보였습니다.  이러한 문제를 해결하기 위해 본 논문에서는 새로운 대규모 3D 합성 시스템인 Hunyuan3D 2.0을 제안합니다.

Hunyuan3D 2.0은 **두 가지 기본 구성 요소**인 대규모 형태 생성 모델(Hunyuan3D-DiT)과 대규모 텍스처 생성 모델(Hunyuan3D-Paint)로 이루어져 있습니다. Hunyuan3D-DiT는 확장 가능한 흐름 기반 확산 변환기를 기반으로 하며, 주어진 조건 이미지와 정합되는 형태를 생성합니다. Hunyuan3D-Paint는 강력한 기하 및 확산 사전 정보를 활용하여 고해상도의 생생한 텍스처 맵을 생성합니다.  Hunyuan3D 2.0은 기존 최첨단 모델들을 능가하는 성능을 보이며, **오픈소스로 공개**되어 연구자들의 접근성을 높였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} Hunyuan3D 2.0은 고해상도 텍스처 3D 자산 생성을 위한 확장 가능한 시스템입니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 모델은 형태 생성 모델(Hunyuan3D-DiT)과 텍스처 생성 모델(Hunyuan3D-Paint)로 구성되며, 우수한 성능을 보입니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 오픈소스로 공개되어 연구자들의 접근성을 높이고 3D 생성 분야의 발전에 기여합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대규모 오픈소스 3D 생성 모델**의 부족을 해결하기 위해 **고해상도 텍스처 3D 자산 생성을 위한 확장 가능한 확산 모델 기반의 시스템인 Hunyuan3D 2.0을 제시**합니다. 이는 3D 자산 생성 분야의 발전에 크게 기여하며, 게임, 영화, 시뮬레이션, AI 등 다양한 분야에서 활용될 가능성을 제시합니다. 특히, **오픈소스로 공개**되어 연구자들의 접근성을 높이고 협업을 촉진하는 데 중요한 역할을 합니다. 향후 연구를 위한 새로운 방향을 제시하여 3D 생성 분야의 지속적인 발전에 기여할 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.12202/extracted/6148177/figures/teaser.png)

> 🔼 이 그림은 Hunyuan3D 2.0 시스템의 전반적인 구조를 보여줍니다.  Hunyuan3D-DiT는 입력 이미지를 기반으로 3D 모델의 기본 형상(메쉬)을 생성하고, Hunyuan3D-Paint는 생성된 또는 기존 메쉬에 고해상도의 질감 맵을 생성합니다. 마지막으로 Hunyuan3D-Studio는 사용자들이 쉽게 3D 모델을 생성하고 편집하며 애니메이션을 제작할 수 있도록 지원하는 플랫폼입니다.  다양한 종류의 3D 자산 생성 과정을 한 눈에 보여주는 개념도입니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: An overall of Hunyuan3D 2.0 system.
> </details>





{{< table-caption >}}
|                     | 3DShape2VecSet [111] | Michelangelo [118] | Direct3D [98] | Hunyuan3D-ShapeVAE (Ours) |
| :------------------ | :--------------------: | :------------------: | :---------------: | :-----------------------: |
| V-IoU(<img src="https://arxiv.org/html/2501.12202/uparrow.png">) | 87.88%                | 84.93%                | <ins>88.43</ins>%       | **93.6%**                    |
| S-IoU(<img src="https://arxiv.org/html/2501.12202/uparrow.png">) | 80.66%                | 76.27%                | <ins>81.55</ins>%       | **89.16%**                    |{{< /table-caption >}}

> 🔼 표 1은 Hunyuan3D-ShapeVAE 및 기준 모델의 재구성 성능을 부피 IoU (V-IoU) 및 표면 IoU (S-IoU)를 기반으로 평가한 결과를 보여줍니다.  V-IoU는 3D 모델의 부피 일치 정도를, S-IoU는 표면 일치 정도를 측정합니다.  결과는 Hunyuan3D-ShapeVAE가 모든 기준 모델보다 재구성 성능이 뛰어남을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Numerical comparisons. We evaluate the reconstruction performance of Hunyuan3D-ShapeVAE and baselines based on volume IoU (V-IoU) and Surface (S-IoU). The results indicate Hunyuan3D-ShapeVAE overwhelms all baselines in the reconstruction performance.
> </details>





### In-depth insights


#### 3D Diffusion Scaling
3D 확산 모델의 확장성에 대한 고찰은 **데이터 크기, 모델 크기, 그리고 계산 비용** 사이의 상호작용을 이해하는 데서 시작됩니다.  대용량 3D 데이터셋 확보의 어려움은 모델 성능 향상의 주요 병목 현상이며, 이를 극복하기 위한 전략으로 **데이터 증강 기법**이나 **합성 데이터 활용** 등이 논의될 수 있습니다.  모델 크기 확장은 **매개변수 효율성**을 고려하여 진행되어야 하며, **메모리 관리 및 병렬 처리**에 대한 효율적인 전략이 필요합니다.  계산 비용 또한 중요한 고려사항이며, **모델 경량화 기법**이나 **분산 학습** 등을 통해 이를 해결할 수 있습니다.  결과적으로, 성공적인 3D 확산 모델의 확장은 이 세 가지 요소 간의 균형 있는 조정을 통해 가능하며, **새로운 아키텍처 및 알고리즘** 개발을 통해 더욱 발전할 수 있을 것입니다.  **학습 전략 및 평가 지표** 또한 모델 확장 과정에서 중요한 역할을 수행합니다.

#### Shape & Texture Gen
본 논문에서 제시된 ‘Shape & Texture Gen’ 에 대한 심층적인 분석 결과를 요약하면 다음과 같습니다. **Hunyuan3D 2.0 시스템은 대규모 3D 자산 생성을 위해 확장 가능한 확산 모델을 사용합니다.** 이는 형태 생성 모델인 Hunyuan3D-DiT와 질감 생성 모델인 Hunyuan3D-Paint 두 가지 주요 구성 요소로 이루어져 있습니다.  Hunyuan3D-DiT는 확장 가능한 플로우 기반 확산 트랜스포머를 기반으로 하여 주어진 조건 이미지와 잘 정렬되는 형태를 생성하는 데 중점을 둡니다.  **Hunyuan3D-Paint는 기하학적 및 확산 사전 정보를 활용하여 고해상도의 생생한 질감 맵을 생성합니다.**  이는 생성된 또는 수작업으로 제작된 메시 모두에 적용될 수 있습니다.  두 모델은 모두 오픈 소스로 공개되어 3D 커뮤니티에 기여하고 있습니다.  **특히, 중요도 샘플링 기법을 사용한 Hunyuan3D-ShapeVAE의 자동 인코더는 메시의 미세한 부분까지 포착하여 고품질의 3D 모델 생성을 가능하게 합니다.**  이처럼 두 모델의 시너지 효과는 고품질 텍스처를 갖춘 고해상도 3D 모델 생성을 가능하게 하며, 이는 게임, 영화, 시뮬레이션 및 AI 분야에서 광범위하게 활용될 수 있을 것으로 예상됩니다.

#### Studio's Features
이 논문에서 제시된 ‘Studio’ 기능들은 3D 자산 제작 과정을 간소화하고 대중화하는 데 초점을 맞춥니다. **Sketch-to-3D** 기능은 2D 스케치를 고해상도 텍스처가 적용된 3D 자산으로 변환하여 디자인 효율성을 높입니다.  **Low-polygon Stylization** 기능은 폴리곤 수를 줄여 연산 비용을 절감하면서도 텍스처 품질을 유지합니다.  마지막으로, **3D Character Animation** 기능은 생성된 정적 3D 모델에 애니메이션을 부여하여 활용도를 넓힙니다. 이러한 기능들은 전문가뿐만 아니라 아마추어 사용자도 쉽게 고품질 3D 자산을 만들고 조작할 수 있도록 지원합니다.  **특히, 기존의 낮은 해상도, 낮은 정확도의 3D 모델 생성 방식을 뛰어넘어** 대규모 기반 생성 모델을 활용한 고품질 3D 모델 제작을 가능하게 합니다. 따라서 Hunyuan3D-Studio는 3D 콘텐츠 제작 과정 전반에 걸쳐 효율성과 접근성을 크게 향상시키는 핵심적인 역할을 합니다.

#### Mesh Reconstruction
본 논문에서 다루는 메쉬 재구성(Mesh Reconstruction)은 3D 모델링 분야에서 **핵심적인 과정**입니다. 손상되거나 불완전한 메쉬 데이터를 기반으로 원본 메쉬의 형태를 복원하는 기술이며, **정확도와 효율성**이 중요한 평가 지표입니다.  논문에서는 이를 위해 **자동 인코더(Autoencoder)**를 활용한 새로운 방법론을 제시하는데, 특히 **중요도 샘플링(Importance Sampling)** 기법을 도입하여 메쉬 표면의 상세한 특징을 효과적으로 포착하고 재구성하는 데 집중합니다.  **다양한 손실 함수**를 통해 모델의 학습을 최적화하고, **다중 해상도 전략**을 사용하여 계산 비용을 절감하면서 높은 정확도를 달성합니다.  이러한 메쉬 재구성의 정확성은 하류 작업(downstream task)인 텍스쳐 합성과 애니메이션 생성에 직접적인 영향을 미치므로, **전체 시스템의 성능**에 큰 영향을 미치는 핵심 모듈이라고 할 수 있습니다.  **경쟁 모델들과의 비교 실험 결과**를 통해 제시된 방법론의 우수성을 보여주는 것이 중요한데, 논문에서는 정량적 지표(IoU)와 시각적 비교를 통해 이를 입증합니다.  **결론적으로**, 높은 정확도와 효율성을 동시에 달성한 메쉬 재구성 방법은 **3D 모델 생성 파이프라인의 완성도를 높이는 데 크게 기여**할 것으로 예상됩니다.

#### Future of 3D Gen
3D 생성 기술의 미래는 **대규모 모델과 데이터**의 활용에 달려 있습니다.  Hunyuan3D 2.0과 같은 최신 모델들은 이미 방대한 데이터셋을 기반으로 높은 해상도의 텍스쳐를 가진 3D 자산 생성을 가능하게 합니다. 그러나 미래의 3D 생성 기술은 **더욱 현실적인 시각 효과와 물리적 특성**을 구현하는 데 초점을 맞출 것입니다.  **실시간 렌더링 기술**과의 통합 또한 중요한 발전 분야이며, 사용자의 상호 작용을 통해 실시간으로 3D 모델을 제작하고 수정하는 환경이 만들어질 것입니다.  **다양한 모달리티** (텍스트, 이미지, 음성)를 통합하여 더욱 직관적이고 창의적인 3D 모델링 도구가 개발될 것입니다.  **개방형 소스 모델**의 발전 또한 중요한데, Hunyuan3D 2.0처럼 공개된 모델들은 3D 생성 기술의 대중화에 크게 기여할 것입니다.  **윤리적 문제** 또한 고려되어야 하며, 생성된 3D 모델의 저작권 및 악용 방지에 대한 해결책이 필요할 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.12202/x1.png)

> 🔼 그림 2는 Hunyuan3D 2.0 시스템의 전체 아키텍처를 보여줍니다. 두 가지 주요 구성 요소인 Hunyuan3D-DiT와 Hunyuan3D-Paint로 구성됩니다. Hunyuan3D-DiT는 입력 이미지에서 3D 메시를 생성하고, Hunyuan3D-Paint는 생성된 메시에 대한 질감 맵을 생성합니다. Hunyuan3D-Paint는 생성된 메시의 노멀 맵과 위치 맵을 기하학적 조건으로 사용하여 질감 베이킹을 위한 다중 뷰 이미지를 생성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2:  An overall of Hunyuan3D 2.0 architecture for 3D generation. It consists of two main components: Hunyuan3D-DiT for generating bare mesh from a given input image and Hunyuan3D-Paint for generating a textured map for the generated bare mesh. Hunyuan3D-Paint takes geometry conditions – normal maps and position maps of generated mesh as inputs and generates multi-view images for texture baking.
> </details>



![](https://arxiv.org/html/2501.12202/x2.png)

> 🔼 그림 3은 Hunyuan3D-ShapeVAE의 전체 아키텍처를 보여줍니다. 기존의 균일한 표면 샘플링 대신, 모서리와 모서리와 같은 고주파수 세부 정보를 추출하기 위해 중요도 샘플링 전략을 개발했습니다. 이를 통해 모델은 3D 형상의 복잡한 세부 정보를 더 잘 포착하고 표현할 수 있습니다. 점 쿼리 생성 중에, 가장 먼 점 샘플링(FPS) 연산은 균일한 점 클라우드와 중요도 샘플링 점 클라우드에 대해 별도로 수행됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: The overall architecture of Hunyuan3D-ShapeVAE. Instead of only using uniform sampling on mesh surface, We have developed an importance sampling strategy to extract high-frequency detail information from the input mesh surface, such as edges and corners. This allows the model to better capture and represent the intricate details of 3D shapes. Note that during the point query construction, the Farthest Point Sampling (FPS) operation is performed separately for the uniform point cloud and the importance sampling point cloud.
> </details>



![](https://arxiv.org/html/2501.12202/x3.png)

> 🔼 그림 4는 Hunyuan3D-DiT의 개요를 보여줍니다.  Hunyuan3D-DiT는 이중 스트림 블록과 단일 스트림 블록을 모두 사용하는 트랜스포머 아키텍처를 채택합니다. 이러한 설계는 형태와 이미지 모달리티 간의 상호 작용에 유리하여 모델이 뛰어난 품질의 베어 메시를 생성하는 데 도움이 됩니다. 주황색 블록은 학습 가능한 매개변수가 없고, 파란색 블록은 학습 가능한 매개변수가 있으며, 회색 블록은 더 자세한 모듈을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Overview of Hunyuan3D-DiT. It adopts a transformer architecture with both double- and single-stream blocks. This design benefits the interaction between modalities of shape and image, helping our model to generate bare meshes with exceptional quality. (Note that the orange blocks have no learnable parameters, the blue blocks contain trainable parameters, and the gray blocks indicate a module composed of more details.)
> </details>



![](https://arxiv.org/html/2501.12202/x4.png)

> 🔼 그림 5는 Hunyuan3D-Paint의 개요를 보여줍니다. 이 시스템은 입력 이미지를 무조명 상태로 변환하여 조명에 영향을 받지 않는 텍스처 맵을 생성하는 이미지 디라이트 모듈을 활용합니다.  이 시스템은 모델에 충실한 조건부 이미지 특징을 제공하는 양방향 이미지 조건화 참조 네트워크를 특징으로 합니다. 또한 입력 이미지에 가깝게 일치하는 텍스처 맵 생성을 지원합니다. 다중 작업 어텐션 모듈은 모델이 다중 뷰 일관성 있는 이미지를 합성하도록 합니다. 이 모듈은 모든 생성된 이미지의 일관성을 유지하는 동시에 입력값을 준수합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Overview of Hunyuan3D-Paint. We leverage an image delighting module to convert the input image to an unlit state to produce light-invariant texture maps. The system features a double-stream image conditioning reference-net, which provides faithfully conditional image features to the model. Furthermore, it facilitates the production of texture maps that conform closely to the input image. The multi-task attention module ensures that the model synthesizes multi-view consistent images. This module maintains the coherence of all generated images while adhering to the input.
> </details>



![](https://arxiv.org/html/2501.12202/x5.png)

> 🔼 그림 6은 다양한 방법으로 재구성된 메쉬를 시각적으로 비교한 것입니다. 파란색으로 칠해진 메쉬는 세부적인 디테일을 더욱 잘 보여주기 위한 것입니다. 비교 결과, Hunyuan3D-ShapeVAE만이 미세한 표면 디테일과 깔끔한 공간을 가진 메쉬를 재구성하는 것을 보여줍니다. 그림을 확대하여 보면 더욱 효과적으로 비교할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Visual comparisons. We illustrate the reconstructed mesh (blue paint aims to show more details) in the figure, which showcases that only Hunyuan3D-ShapeVAE reconstructs mesh with fine-grained surface details and neat space. (Better viewed by zooming in.)
> </details>



![](https://arxiv.org/html/2501.12202/x6.png)

> 🔼 그림 7은 Hunyuan3D-DiT 모델의 3D 형태 생성 성능을 보여주는 시각적 비교 결과입니다. 입력 이미지와 다양한 방법으로 생성된 3D 메시(자세한 부분을 보여주기 위해 파란색으로 칠해짐)가 함께 표시됩니다. 그림에서 사람 얼굴과 피아노 건반은 Hunyuan3D-DiT가 세부 표면 요철을 정확하게 합성하고 완전성을 유지하면서 복잡한 구조를 생성할 수 있음을 보여줍니다. 여러 장면이나 로고는 Hunyuan3D-DiT가 매우 세밀한 부분까지 생성할 수 있음을 보여줍니다. (확대해서 보는 것이 좋습니다.)
> <details>
> <summary>read the caption</summary>
> Figure 7: Visual comparisons. We display the input image and the generated bare mesh (blue paint aims to show more details) from all methods in the figure. The human faces and piano keys show that Hunyuan3D-DiT could synthesize detailed surface bumps, maintaining completeness. Several scenes or logos demonstrate that Hunyuan3D-DiT could generate intricate details. (Better viewed by zooming in.)
> </details>



![](https://arxiv.org/html/2501.12202/x7.png)

> 🔼 그림 8은 Hunyuan3D-Paint의 성능을 보여주는 시각적 비교 결과를 보여줍니다.  다양한 기본 메시(bare mesh)에 대해 생성된 여러 질감 맵을 보여주며, 특히 물고기와 토끼 질감 맵은 Hunyuan3D-Paint가 텍스트와 가장 일치하는 결과를 생성함을 보여줍니다. 축구공은 매끄럽고 깨끗한 질감 맵을 합성할 수 있는 모델의 능력을 보여주고, 성과 곰은 복잡한 질감 맵을 생성할 수 있음을 시사합니다.  더 자세한 내용은 확대해서 보는 것이 좋습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Visual comparisons. We demonstrate several generated texture maps on different bare meshes. The fish and rabbit texture map showcases that Hunyuan3D-Paint produces the most text-conforming results. The football indicates that our model could synthesize seamless and clean texture maps. Moreover, Hunyuan3D-Paint could generate complex texture maps, like the castle and bear. (Better viewed by zooming in.)
> </details>



![](https://arxiv.org/html/2501.12202/x8.png)

> 🔼 그림 9는 Hunyuan3D-Paint의 질감 재스킨 기능을 검증하기 위해 두 가지 메시에 대해 서로 다른 질감 맵을 생성한 결과를 보여줍니다.  각 메시는 여러 가지 다른 질감으로 표현되어 있어 Hunyuan3D-Paint가 다양한 질감 스타일을 생성할 수 있음을 보여줍니다.  이 그림은 하나의 메시에 다양한 질감을 적용하는 모델의 능력을 보여주는 시각적 예시입니다. 확대하여 보시면 더 자세히 관찰할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Visual results. We generate different texture maps for two meshes, and the results validate the performance of Hunyuan3D-Paint on texture reskinning. (Better viewed by zooming in.)
> </details>



![](https://arxiv.org/html/2501.12202/extracted/6148177/figures/texture/skinning.png)

> 🔼 그림 10은 사용자 연구 결과를 보여줍니다. Hunyuan3D 2.0 모델과 비교 모델들에 대한 3가지 평가 지표 (전반적인 시각적 품질, 이미지 조건 준수 여부, 전반적인 만족도)에 대한 결과를 막대 그래프로 나타냅니다. Hunyuan3D 2.0는 특히 이미지 조건 충족 측면에서 다른 모델들에 비해 우수한 성능을 보입니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: The results of user study.
> </details>



![](https://arxiv.org/html/2501.12202/x9.png)

> 🔼 그림 11은 Hunyuan3D 2.0의 성능을 보여주는 시각적 비교 결과입니다. 첫 번째 그림(펭귄)은 Hunyuan3D 2.0가 세밀한 표면 요철과 정확한 질감 맵을 생성할 수 있음을 보여줍니다. 두 번째 그림(펭귄)은 복잡한 동작을 처리하는 모델의 능력을 보여주며, 마지막 그림(산)은 Hunyuan3D-DiT가 복잡한 구조를 생성하고 Hunyuan3D-Paint가 생생한 질감 맵을 합성할 수 있음을 보여줍니다. 자세히 보시려면 확대하여 보세요.
> <details>
> <summary>read the caption</summary>
> Figure 11: Visual comparisons. The first case reflects that Hunyuan3D 2.0 could synthesize detailed surface bumps and correct texture maps. The second penguin showcases our model’s ability to handle complex actions. The last mountain demonstrates that Hunyuan3D-DiT could produce intricate structures, and Hunyuan3D-Paint can synthesize vivid texture maps. (Better viewed by zooming in.)
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | ULIP-T(↑) | ULIP-I(↑) | Uni3D-T(↑) | Uni3D-I(↑) |
|---|---|---|---|---|
| Michelangelo [118] | 0.0752 | 0.1152 | 0.2133 | 0.2611 |
| Craftsman 1.5 [49] | 0.0745 | 0.1296 | 0.2375 | 0.2987 |
| Trellis [100] | 0.0769 | 0.1267 | 0.2496 | 0.3116 |
| Shape Model 1 | 0.0799 | 0.1181 | 0.2469 | 0.3064 |
| Shape Model 2 | 0.0741 | 0.1308 | 0.2464 | 0.3106 |
| Shape Model 3 | 0.0746 | 0.1284 | 0.2516 | 0.3131 |
| Hunyuan3D-DiT (Ours) | 0.0771 | 0.1303 | 0.2519 | 0.3151 |{{< /table-caption >}}
> 🔼 표 2는 Hunyuan3D-DiT의 성능을 평가한 결과를 보여줍니다.  ULIP-T/I와 Uni3D-T/I 지표를 사용하여 형태 생성 성능을 평가했으며, Hunyuan3D-DiT가 조건에 가장 잘 맞는 결과를 생성했음을 보여줍니다. 즉, 입력 이미지나 텍스트 조건에 따라 생성된 3D 모델의 형태가 얼마나 정확하게 일치하는지를 수치적으로 보여주는 표입니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Numerical comparisons. By evaluating the shape generation performance on ULIP-T/I, Uni3D-T/I, demostrating Hunyuan3D-DiT could produce the most condition followed results.
> </details>

{{< table-caption >}}
| Method | CMMD(↓) | FID<sub>CLIP</sub>(↓) | CLIP-score(↑) | LPIPS(↓) |
|---|---|---|---|---|
| TEXTure [73] | 3.047 | 35.75 | 0.8499 | 0.0076 |
| Text2Tex [9] | 2.811 | 31.72 | 0.8680 | 0.0071 |
| SyncMVD [59] | 2.584 | 29.93 | 0.8751 | 0.0063 |
| Paint3D [110] | 2.810 | 30.29 | 0.8724 | 0.0063 |
| TexPainter [112] | 2.483 | 28.83 | 0.8789 | 0.0062 |
| Hunyuan3D-Paint (Ours) | **2.318** | **26.44** | **0.8893** | **0.0059** |{{< /table-caption >}}
> 🔼 이 표는 Hunyuan3D-Paint 모델의 성능을 다른 기준 모델들과 비교하여 보여줍니다. 다양한 평가 지표(CMMD, FIDCLIP, CLIP-score, LPIPS)를 사용하여 비교 분석한 결과, Hunyuan3D-Paint 모델이 조건에 가장 부합하는 질감 맵을 생성하는 것으로 나타났습니다.  각 지표는 이미지 생성 모델의 성능을 평가하는 데 사용되는 지표이며, 낮을수록 좋거나 높을수록 좋은 등 다양한 해석이 가능하다는 점을 참고해야 합니다.  본 표는 Hunyuan3D-Paint의 우수성을 수치적으로 제시하여 모델의 효과성을 입증하는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Numerical comparisons. We compare Hunyuan3D-Paint with baselines on various metrics, and the results indicate that our model could produce the most condition-conforming texture maps.
> </details>

{{< table-caption >}}
|               | CMMD(↓) | FID<sub>CLIP</sub>(↓) | FID<sub>Incept</sub>(↓) | CLIP-score(↑) |
| :------------ | :------: | :----------------: | :------------------: | :-----------: |
| Trellis [100] |  3.591   |    54.639         |      289.287         |    0.787      |
| Model 1       |  3.600   |     55.866         |      305.922         |    0.779      |
| Model 2       |  3.368   |     49.744         |      294.628         |    0.806      |
| Model 3       |  3.218   |     51.574         |      295.691         |    0.799      |
| Hunyuan3D 2.0 (Ours) | **3.193** |  **49.165**        | **282.429**          |  **0.809**     |{{< /table-caption >}}
> 🔼 표 4는 Hunyuan3D-Paint 모델의 텍스처 맵 생성 성능을 다른 기존 모델들과 비교 분석한 결과를 보여줍니다.  CMMD, FIDCLIP, FIDIncept, CLIP-score, LPIPS 등 다양한 지표를 사용하여 정량적으로 평가하였으며, Hunyuan3D-Paint가 조건(conditional image)과 가장 잘 일치하는 텍스처 맵을 생성한다는 것을 보여줍니다.  즉, 입력 이미지의 특징을 가장 충실하게 반영하여 생성된 텍스처 맵의 품질과 정확성이 가장 우수함을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Numerical comparison. According to the results, Hunyuan3D-Paint produces the most condition-following texture maps.
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