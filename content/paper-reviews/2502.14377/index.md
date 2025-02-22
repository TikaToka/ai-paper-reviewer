---
title: "RelaCtrl: Relevance-Guided Efficient Control for Diffusion Transformers"
summary: "RelaCtrl: 적은 매개변수로 효율적인 제어 가능한 이미지 생성"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Generation", "🏢 University of Science and Technology of China",]
showSummary: true
date: 2025-02-20
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.14377 {{< /keyword >}}
{{< keyword icon="writer" >}} Ke Cao et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-21 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.14377" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.14377" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/relactrl-relevance-guided-efficient-control" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 제어 가능한 확산 트랜스포머 모델들은 **매개변수가 많고 계산 비용이 높다는 문제점**을 가지고 있습니다. 또한, **모델의 각 계층에서 제어 정보의 중요도가 다르다는 점**을 고려하지 못해 효율성이 떨어집니다.  본 논문에서는 이러한 문제를 해결하기 위해 RelaCtrl 프레임워크를 제안합니다. 



RelaCtrl은 **각 계층에서의 제어 정보의 관련성을 평가**하고, 이를 바탕으로 **제어 계층의 위치, 매개변수 크기, 모델 용량을 조정**하여 불필요한 매개변수와 계산을 줄입니다. 또한, **2차원 셔플 믹서(TDSM)**를 사용하여 효율적인 구현을 가능하게 합니다. 실험 결과, RelaCtrl은 **기존 모델보다 적은 매개변수와 계산 복잡도로 더 나은 성능**을 보였습니다.  **특히 PixArt-d와 비교하여 85%의 매개변수와 계산 복잡도 감소**를 달성했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} RelaCtrl은 **제어 정보의 관련성을 분석하여 확산 트랜스포머의 계층별 제어 효율성을 향상**시킵니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 새로운 **2차원 셔플 믹서(TDSM)**는 기존의 자기-주의와 FFN을 대체하여 계산 복잡도를 줄입니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 실험 결과, RelaCtrl은 **기존 방식보다 적은 매개변수와 계산 복잡도로 우수한 성능**을 달성합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **확산 트랜스포머(Diffusion Transformer) 기반 제어 가능한 이미지 생성 분야의 효율성을 크게 향상**시키는 RelaCtrl 프레임워크를 제시하여, **매개변수와 계산 복잡도를 줄이면서 성능을 개선**하는 데 중요한 의미를 가집니다.  **관련성 분석을 통해 제어 신호를 효율적으로 통합**하고, **새로운 2차원 셔플 믹서(TDSM)를 도입**하여 계산 효율성을 높였습니다. 이는 **향후 연구에서 효율적인 제어 가능한 생성 모델 개발에 중요한 기여**를 할 것으로 예상되며, **다양한 응용 분야에서의 확산 트랜스포머 활용에 새로운 가능성**을 제시합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.14377/extracted/6219154/images/intro_fidandhdd.jpg)

> 🔼 그림 1은 ControlNet 블록 내 특정 위치를 건너뛰었을 때 생성된 이미지의 품질에 미치는 영향을 보여줍니다. FID와 HDD 값이 높을수록 건너뛴 계층이 최종 결과의 품질에 미치는 영향이 클수록 생성된 이미지 품질과의 상관관계가 강함을 의미합니다.  즉, 특정 계층을 제거했을 때 이미지 품질과 제어 효과에 큰 영향을 미치는 계층은 해당 이미지 생성에 중요한 역할을 수행한다는 것을 나타냅니다. 이는 ControlNet의 각 계층이 생성 품질에 기여하는 정도가 다르다는 것을 시각적으로 보여줍니다.  
> <details>
> <summary>read the caption</summary>
> Figure 1: Effect of skipping a specific position within the ControlNet block on the quality of the generated image. Higher FID and HDD indicate a more significant impact of the skipped layer on the quality of the final results, reflecting a stronger correlation with the generated image quality.
> </details>





{{< table-caption >}}
| Model | Method | Controllability | Quality | Text Consistency | Controllability | Quality | Text Consistency |
|---|---|---|---|---|---|---|---| 
| Canny |  |  |  |  | Hed |  |  |  |
| HDD↓ | FID↓ | CLIP-Ae↑ | CLIP-Score↑ | HDD↓ | FID↓ | CLIP-Ae↑ | CLIP-Score↑ |
| SD1.5 | Uni-ControlNet | 95.40 | 33.81 | 5.207 | 0.259 | 98.78 | 59.72 | 5.086 | 0.252 |
|  | Uni-Control | 97.90 | 91.29 | 4.965 | 0.249 | 100.52 | 91.94 | 4.819 | 0.251 |
| SDXL | ControlNet-XS | 101.34 | 21.57 | 5.134 | **0.286** | - | - | - | - |
|  | ControlNext | 117.59 | 49.32 | 4.816 | 0.275 | - | - | - | - |
| PixArt-α | PixArt-δ | 96.26 | 21.38 | 5.508 | 0.279 | 98.91 | 29.22 | 5.243 | 0.275 |
|  | RelaCtrl | **94.04** | **20.34** | **5.584** | 0.282 | **96.11** | **27.73** | **5.451** | **0.276** |
| Model | Method | Depth | Segmentation |
|---|---|---|---| 
| SD1.5 | Uni-ControlNet | 102.75 | 43.17 | 5.230 | 0.250 | 0.316 | 40.83 | 5.270 | 0.255 |
|  | Uni-Control | 102.46 | 91.94 | 5.327 | 0.249 | 0.382 | 40.74 | 5.462 | 0.258 |
| SDXL | ControlNet-XS | 99.20 | 34.38 | 5.235 | 0.281 | - | - | - | - |
|  | ControlNext | 101.63 | 73.26 | 4.919 | 0.253 | - | - | - | - |
| PixArt-α | PixArt-δ | 96.26 | 21.38 | 5.508 | 0.279 | 0.379 | 35.50 | 5.668 | 0.282 |
|  | RelaCtrl | 99.11 | 33.93 | 5.887 | 0.285 | 0.405 | 33.76 | 5.702 | 0.287 |{{< /table-caption >}}

> 🔼 표 1은 COCO 검증 세트(Lin et al., 2014)에서 다양한 방법들의 정량적 비교 결과를 보여줍니다.  본 논문에서 제안된 RelaCtrl 방법과 기존의 여러 제어 방식(Uni-ControlNet, Uni-Control, ControlNet-XS, ControlNext, PixArt-d, PixArt-a)의 성능을 비교 분석한 결과입니다.  각 방법에 대해 Canny, HED, Depth, Segmentation 네 가지 조건 하에서 제어 가능성(HDD, MSE-d, mIoU), 이미지 품질(FID, CLIP-Ae), 텍스트 일관성(CLIP-Score) 지표를 측정하였습니다.  가장 좋은 결과는 굵은 글씨체로, 두 번째로 좋은 결과는 밑줄로 표시되어 있습니다. 이 표는 RelaCtrl의 성능을 다른 방법들과 비교하여 정량적으로 보여주는 주요 결과를 담고 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Quantitative comparisons of different methods on the COCO validation set (Lin et al., 2014). The best results are highlighted in bold, while the second-best results are marked with underline.
> </details>





### In-depth insights


#### DiT Control Relevance
본 논문에서 DiT 제어 관련성 분석은 **제어 정보가 DiT의 다양한 레이어에 걸쳐 어떻게 다르게 영향을 미치는지**를 밝히는 데 중점을 둡니다.  연구진은 제어 신호의 생략이 생성 품질 및 제어 효과에 미치는 영향을 평가하여 각 레이어의 관련성 점수를 계산합니다. 이를 통해 **특정 레이어가 제어에 더 민감하게 반응**하고 일부 레이어는 상대적으로 영향이 적다는 것을 발견합니다. 이러한 통찰력을 바탕으로 연구진은 계산 비용을 절감하고 성능을 향상시키는 효율적인 제어 전략을 제시합니다.  **레이어별 관련성에 따른 매개변수 크기 및 모델링 용량 조정**은 DiT 제어의 효율성을 높이는 핵심 요소입니다.  결과적으로, 이러한 **세밀한 제어 전략**은 제한된 자원으로도 높은 성능을 달성할 수 있다는 점을 시사합니다.

#### TDSM Efficiency
본 논문에서 제안하는 Two-Dimensional Shuffle Mixer (TDSM)의 효율성은 **기존의 self-attention 및 FFN(Feed-Forward Network) 레이어를 대체하여 매개변수 수와 계산 복잡도를 줄이는 데** 있습니다.  TDSM은 토큰과 채널 믹싱을 하나의 연산으로 통합하여 효율성을 높입니다.  **임의의 토큰 및 채널 그룹 분할을 통해 지역적 그룹화의 한계를 극복하고 비국소적 모델링을 가능하게** 합니다.  이는 계산 비용을 상당히 절감하면서도 성능 저하 없이 효과적인 정보 믹싱을 제공합니다.  **관련성 분석을 기반으로 채널 그룹의 수를 조절하여 계산 효율성을 더욱 향상**시킵니다.  즉, 상관관계가 높은 영역에서는 채널 그룹의 수를 줄이고, 주목할 만한 특징 차원을 확장하여 모델링 성능을 높입니다.  결과적으로, TDSM은 DiT 기반 제어 생성 모델의 효율성을 크게 높이는 핵심 요소입니다.

#### RelaCtrl Framework
RelaCtrl 프레임워크는 **확산 트랜스포머(Diffusion Transformer)** 기반의 효율적인 제어 가능한 이미지 생성을 위한 혁신적인 구조입니다. 기존의 방법들이 매개변수와 계산 비용이 많이 들고, 제어 정보의 관련성을 고려하지 못하여 자원 할당이 비효율적인 문제를 해결합니다. **중요도에 기반한 계층적 제어 전략**을 통해 관련성이 높은 계층에 집중적으로 제어 신호를 적용하여 효율성을 높입니다.  **2차원 셔플 믹서(TDSM)**를 통해 기존의 자기 주의(self-attention) 및 FFN 계층을 대체하여 매개변수와 계산량을 줄이는 동시에 성능을 유지합니다.  **ControlNet 관련성 점수**를 활용하여 각 계층의 제어 정보 관련성을 평가하고, 이를 토대로 제어 계층의 위치, 매개변수 크기, 모델링 용량을 조정합니다.  **실험 결과**는 RelaCtrl이 기존 방법보다 매개변수와 계산량을 훨씬 줄이면서도 우수한 성능을 달성함을 보여줍니다. 이는 효율적인 제어 가능한 생성 모델을 구축하는 새로운 방향을 제시합니다.

#### Ablation Study
본 논문의 "절제 연구(Ablation Study)" 부분은 **RelaCtrl 모델의 성능에 기여하는 각 구성 요소의 중요성을 객관적으로 평가**하기 위해 설계되었습니다.  연구진은 **제어 블록 배치, RGLC 블록, 그리고 Prior 2의 영향을 체계적으로 분석**했습니다.  **관련성 점수를 기반으로 제어 블록의 수를 조절**하는 실험을 통해, **필수적인 제어 블록만 유지하면서도 성능 저하를 최소화**할 수 있음을 보여주었습니다.  또한, **RGLC 블록과 Prior 2의 제거 실험**을 통해 각 구성요소가 모델 성능에 미치는 긍정적 영향을 확인했습니다. 이러한 실험 결과들은 **RelaCtrl 모델의 설계 원칙의 타당성과 효율성을 입증**하며, **자원을 효율적으로 사용하면서 높은 성능을 유지**할 수 있는 설계의 우수성을 강조합니다. 특히, **RGLC 블록의 중요성**은 전체 모델의 성능에 크게 기여하는 것으로 나타나며,  **Prior 2 또한 모델의 성능 향상에 중요한 역할**을 수행함을 알 수 있습니다.  **전체적으로 절제 연구는 RelaCtrl 모델의 핵심 구성 요소들의 상호작용과 중요도를 명확히 보여줌으로써, 모델의 신뢰성과 실용성을 높이는 데 기여**합니다.

#### Future Work
본 논문의 RelaCtrl 모델은 확산 트랜스포머에서 제어 가능한 이미지 생성을 위한 효율적인 프레임워크를 제시하지만, **향후 연구를 통해 더욱 개선될 여지**가 있습니다.  먼저, **다양한 제어 신호 모달리티**에 대한 적용성을 확장하여 텍스트 외에도 오디오, 비디오 등 다양한 입력을 활용한 이미지 생성을 지원할 수 있도록 연구가 필요합니다.  또한, **계산 비용을 더욱 줄이기 위한 경량화 기술**을 추가적으로 개발하여, 모바일 및 임베디드 시스템과 같은 제약된 환경에서도 RelaCtrl을 효과적으로 활용할 수 있도록 하는 연구가 중요합니다.  마지막으로, **다양한 데이터셋과 태스크에 대한 일반화 성능을 향상**시키는 연구는 RelaCtrl의 실용성을 높이는 데 기여할 것입니다.  **특히, 고해상도 이미지 생성에 대한 성능 개선**은 앞으로의 중요한 연구 과제가 될 것입니다.  이러한 추가적인 연구를 통해 RelaCtrl은 더욱 강력하고 효율적인 제어 가능한 이미지 생성 모델로 발전할 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.14377/extracted/6219154/images/method_importance.png)

> 🔼 그림 2는 DiT-ControlNet의 여러 계층에 대한 관련성 다이어그램을 보여줍니다. FID와 HDD 순위를 기반으로 계산되었으며, 초기 증가 후 감소하는 전반적인 추세를 보여줍니다.  즉, DiT-ControlNet의 앞부분 중간 계층이 제어에 더 민감하고 뒷부분 계층은 덜 민감하다는 것을 의미합니다.  흰색 숫자는 PixArt-α에서 RelaCtrl의 선택된 배치 위치를 나타냅니다. 이는 RelaCtrl이 제어 정보의 관련성에 따라 효율적으로 제어 신호를 통합하기 위해  ControlNet의 특정 계층에만 제어 블록을 배치한다는 것을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: The relevance diagram of different layers in the DiT-ControlNet was calculated based on the FID and HDD ranks. The overall trend shows an initial increase followed by a decrease. The selected placement positions of RelaCtrl in PixArt-α𝛼\alphaitalic_α are marked with white numbers.
> </details>



![](https://arxiv.org/html/2502.14377/extracted/6219154/images/method_arch.png)

> 🔼 그림 3은 제안된 RelaCtrl 프레임워크의 전체 아키텍처를 보여줍니다. ControlNet Relevance Score를 기반으로 순위가 매겨진 제어 블록의 위치는 가장 높은 순위에서 가장 낮은 순위로 표시됩니다. 원래 ControlNet에서 메인 브랜치의 직접 복제는 신중하게 설계된 Reference-Guided Lightweight 제어 블록으로 대체되고, 이는 모델의 성능을 유지하면서 매개변수와 계산 오버헤드를 줄여줍니다. 또한, 2차원 셔플 믹서(TDSM)는 모델의 매개변수와 계산 오버헤드를 효과적으로 줄여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: The overall architecture of RelaCtrl. Control block locations are prioritized based on the ControlNet Relevance Score, ranked from highest to lowest. The direct duplication of the main branch in the original ControlNet is replaced with the carefully designed Reference-Guided Lightweight control block. Additionally, the Two-Dimensional Shuffle Mixer effectively reduces model parameters and computational overhead while preserving performance.
> </details>



![](https://arxiv.org/html/2502.14377/extracted/6219154/images/exp_compare.jpg)

> 🔼 그림 4는 다양한 제어 기법들을 사용한 이미지 생성 결과를 정성적으로 비교한 것입니다. 각 제어 기법(UniControl, Uni-ControlNet, ControlNet-XS, ControlNext, Pixart-8, RelaCtrl)은 다양한 조건(Canny, Depth) 하에서 이미지 생성 능력을 보여줍니다. 자세한 내용을 확인하려면 이미지를 확대하여 보시기 바랍니다. 그림은 각 제어 기법의 강점과 약점, 그리고 이미지 품질에 미치는 영향을 시각적으로 보여주는 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Qualitative comparison of different methods. Please zoom in for better details.
> </details>



![](https://arxiv.org/html/2502.14377/extracted/6219154/images/exp_visual.jpg)

> 🔼 그림 5는 다양한 제어 조건 하에서 RelaCtrl의 생성 효과를 보여줍니다.  각 행은 특정 제어 조건(예: Canny, Depth, HED, Segmentation)을 사용하여 생성된 이미지들을 보여주며,  RelaCtrl이 다양한 스타일과 세부적인 제어를 효과적으로 달성하는 것을 시각적으로 보여줍니다.  각 이미지는 RelaCtrl 모델이 입력 제어 정보를 얼마나 잘 해석하고 생성 과정에 반영하는지를 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Generation effects of RelaCtrl under varying control conditions.
> </details>



![](https://arxiv.org/html/2502.14377/extracted/6219154/images/appendix_full_image1.png)

> 🔼 그림 6은 제어 블록을 제거했을 때 생성된 지표에 미치는 영향을 보여줍니다. ControlNet에 27개와 13개의 블록을 사용한 두 가지 실험 결과를 비교하여 보여줍니다. 각 블록의 제거가 FID(Fréchet Inception Distance)와 HDD(Hausdorff Distance) 지표에 어떤 영향을 미치는지 보여주는 그래프가 포함되어 있습니다. 이를 통해, ControlNet 내 각 블록의 중요도와 제어 성능에 대한 기여도를 정량적으로 분석할 수 있습니다. 27개의 블록을 사용한 경우와 13개의 블록을 사용한 경우 모두 특정 블록을 제거했을 때 지표가 크게 변화하는 구간과 그렇지 않은 구간이 존재함을 알 수 있습니다. 이는 ControlNet 내에서도 블록의 중요도가 다르게 나타나며, 효율적인 제어를 위해서는 중요도가 높은 블록에 더 많은 자원을 할당해야 함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Impact of deleting specific locations on the generated metrics in ControlNet with 27 and 13 blocks.
> </details>



![](https://arxiv.org/html/2502.14377/extracted/6219154/images/appendix_remove3.jpg)

> 🔼 그림 7은 ControlNet의 특정 레이어(7, 9, 27)를 건너뛰었을 때 생성된 이미지에 미치는 영향의 정도(가장 높음, 중간, 가장 낮음)에 따른 추가적인 시각적 결과를 보여줍니다.  각 레이어를 건너뛰면 생성된 이미지의 품질과 제어 정확도에 어떤 영향을 미치는지 시각적으로 비교하여 보여주는 그림입니다.  레이어 7을 건너뛰면 이미지 품질과 제어 정확도가 크게 저하되는 반면, 레이어 27을 건너뛰는 경우에는 성능 저하가 거의 없는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Additional visual results of skipping specific ControlNet layers (7, 9, and 27), correspond to the highest, moderate, and lowest impact on the generated image.
> </details>



![](https://arxiv.org/html/2502.14377/extracted/6219154/images/appendix_flux.png)

> 🔼 그림 8은 Flux.1-dev 모델에서 세 가지 서로 다른 제어 방식(OminiControl, ControlNet, RelaCtrl)을 사용하여 생성된 이미지들을 비교한 것입니다. 각 제어 방식에 따른 이미지 생성 결과의 차이를 시각적으로 보여줍니다.  이는 RelaCtrl의 성능을 다른 최신 제어 방식들과 비교하여 효율성과 성능을 평가하기 위한 것입니다. 각각의 이미지는 특정 조건(예: 우주왕복선이 지구 상공을 비행하는 모습, 황량한 들판에 있는 바위들)을 제시하고, 각 제어 방식이 이러한 조건을 얼마나 잘 반영하여 이미지를 생성하는지 비교 분석합니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Visual comparison of different control methods on Flux.1-dev.
> </details>



![](https://arxiv.org/html/2502.14377/extracted/6219154/images/appendix_style.jpg)

> 🔼 그림 9는 미세 조정된 PixArt 모델에 대한 RelaCtrl의 제어 효과를 보여줍니다. 상단과 하단 행은 네 가지 변환을 보여줍니다. (1) Canny에서 페인트로, (2) 깊이에서 오일로, (3) HED에서 고풍으로, 그리고 (4) 분할에서 픽셀로의 변환입니다. 이 그림은 RelaCtrl이 다양한 제어 조건 하에서도 고품질 이미지를 생성하고, 입력 이미지의 특징을 효과적으로 반영하여 스타일과 분위기를 자연스럽게 변환할 수 있음을 시각적으로 보여줍니다. 특히, Canny와 같은 에지 정보를 바탕으로 페인트 스타일의 이미지를 생성하거나, 깊이 정보를 활용하여 오일 페인팅 느낌의 이미지를 생성하는 등 다양한 스타일 변환이 가능함을 보여주는 사례입니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: The control effect of RelaCtrl on the fine-tuned PixArt model. The upper and lower rows show the four transitions: (1) Canny to paint, (2) Depth to oil, (3) HED to gufeng, and (4) Segmentation to pixel.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | Parameters | Complexity | Inference | Memory |
|---|---|---|---|---|
| PixArt-α | 611.15 | 542.56 | 3.81 | 2114 |
| w/ ControlNet | +294.34 | +270.57 | +0.51 | +1694 |
|  | (+48.16%) | (+49.87%) | (+13.39%) | (+80.13%) |
| w/ RelaCtrl | +**45.15** | +**46.71** | +**0.24** | +**395** |
|  | (+**7.38%**)| (+**8.61%**)| (+**6.30%**)| (+**18.70%**)|{{< /table-caption >}}
> 🔼 표 2는 제안된 방법의 효율성을 평가한 결과를 보여줍니다.  네 가지 지표 (파라미터 수 (백만 단위), 연산 복잡도 (GFLOPs), 추론 시간 (초), 메모리 사용량 (MiB))에 대한 수치를 제시하여 RelaCtrl의 효율성을 다른 방법들과 비교 분석합니다.  PixArt-a 모델에 ControlNet과 RelaCtrl을 적용했을 때의 결과를 비교하여, 파라미터 증가율, 연산량 증가율, 추론 시간 증가율, 메모리 사용량 증가율을 각각 백분율로 표시합니다. 이를 통해 RelaCtrl이 기존 방법에 비해 얼마나 효율적인지 수치적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Evaluation of the proposed method’s effectiveness, with the following units for the four metrics: Parameters (M), Complexity (GFLOPs), Inference Time (s), and Memory Usage (MiB)
> </details>

{{< table-caption >}}
| Setting | HDD ↓ | FID ↓ | Para Ratio |
|---|---|---|---|
| ControlNet-top13 | 96.26 | 21.38 | 100% |
| Relevance-top13 | 94.57 | 20.31 | 100% |
| Relevance-top12 | 95.88 | 20.79 | 92.5% |
| Relevance-top11 | 95.57 | 21.28 | 84.6% |
| Relevance-top10 | 96.36 | 22.24 | 76.9% |{{< /table-caption >}}
> 🔼 이 표는 DiT-ControlNet Relevance에 따라 제어 블록 배치를 했을 때의 영향을 보여줍니다. 기준 모델은 메인 브랜치의 처음 13개 블록을 직접 복제한 ControlNet-top13입니다.  표에는 제어 블록의 수를 13개, 12개, 11개, 10개로 줄였을 때 FID와 HDD 지표의 변화와, ControlNet-top13 모델과 비교했을 때 파라미터 비율 변화를 보여줍니다.  이는 제어 블록의 수를 줄이면 FID와 HDD 지표가 점진적으로 감소하지만, Relevance 점수를 기반으로 11개의 블록만 사용해도 13개 블록을 사용했을 때와 비슷한 성능을 얻을 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: The impact of control block placement guided by DiT-ControlNet Relevance. ControlNet-top13, which directly replicates the first 13 blocks of the main branch, serves as the baseline for parameter volume comparison.
> </details>

{{< table-caption >}}
| Setting | HDD ↓ | FID ↓ | Para Ratio |
|---|---|---|---|
| RelaCtrl | 94.04 | 20.34 | 15.3% |
| w/o RGLC | 95.57 | 21.28 | 84.6% |
| w/o Prior2 | 97.30 | 22.47 | 17.1% |
| Baseline | 96.26 | 21.38 | 100% |{{< /table-caption >}}
> 🔼 표 4는 RGLC 블록과 TDSM 파티션 수가 생성 성능에 미치는 영향을 보여줍니다.  PixArt-δ (13개의 복제된 블록을 사용)가 매개변수 비교를 위한 기준으로 사용됩니다.  이 표는 RGLC 블록의 유무, 그리고 TDSM 파티션의 수를 변경했을 때 HDD, FID, 그리고 매개변수 비율(PixArt-δ 대비)이 어떻게 달라지는지 보여줍니다.  RGLC 블록이나 Prior 2가 없으면 성능이 저하되는 것을 확인할 수 있습니다. 이는 RGLC 블록과 Prior 2가 생성 성능에 중요한 역할을 한다는 것을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: The impact of the RGLC block and the number of TDSM partitions within it on generation performance. The PixArt-δ𝛿\deltaitalic_δ with 13 coped blocks serves as the baseline for parameter comparison.
> </details>

{{< table-caption >}}
| Setting | Parameters (M) | Complexity (GFLOPs) | Inference (s) |
|---|---|---|---|
| Flux.1-dev | 11901.39 | 9925.78 | 4.78 |
| +OminiControl | +14.49 | +6637.41 | +3.11 |
| +ControlNet | +2952.65 | +2578.33 | +0.79 |
| +RelaCtrl | +549.19 | +495.03 | +0.34 |{{< /table-caption >}}
> 🔼 표 5는 Flux.1-dev 모델을 사용하여 수행된 효율성 비교 실험의 결과를 보여줍니다.  각 방법(OminiControl, ControlNet, RelaCtrl)에 대한 매개변수 수, 계산 복잡도(GFLOPs), 추론 시간(초)을 비교하여 RelaCtrl의 효율성을 강조합니다.  특히 RelaCtrl은 매개변수와 계산량을 크게 줄이면서도 ControlNet과 유사한 성능을 유지함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Effectiveness comparison experiment conducted on Flux.1-dev model.
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