---
title: "Edicho: Consistent Image Editing in the Wild"
summary: "Edicho: 이미지 간 일관성 유지하며 제로샷 이미지 편집 가능!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Generation", "🏢 Hong Kong University of Science and Technology",]
showSummary: true
date: 2024-12-30
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.21079 {{< /keyword >}}
{{< keyword icon="writer" >}} Qingyan Bai et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-31 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.21079" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.21079" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/edicho-consistent-image-editing-in-the-wild" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

이미지 편집 분야에서, 다양한 조건(물체 자세, 조명, 배경 등)으로 인해 **여러 이미지에 걸쳐 일관된 편집**을 수행하는 것은 매우 어려운 과제입니다. 기존의 방법들은 이미지 간의 암시적인 대응 관계에 의존하여 일관성 있는 편집을 시도했지만, 불안정한 결과를 초래하는 한계가 있었습니다. 



본 논문에서는 **명시적인 이미지 대응 관계를 활용**하여 이 문제를 해결하는 새로운 방법인 Edicho를 제시합니다. Edicho는 **훈련 과정 없이** 주어진 이미지들의 대응 관계를 정확하게 파악하고, 이를 기반으로 확산 모델의 자기 주의 메커니즘과 분류기 없는 안내(CFG) 전략을 개선하여 **일관성 있는 고품질 이미지 편집**을 수행합니다. 실험 결과, Edicho는 다양한 이미지와 편집 조건에서 기존 방법들보다 우수한 성능을 보였습니다. 이는 이미지 편집 기술 발전에 크게 기여할 뿐 아니라, 다양한 응용 분야(마케팅, 콘텐츠 제작 등)에 적용될 수 있는 잠재력을 가지고 있습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 명시적인 이미지 대응 관계를 활용하여 이미지 간 일관성 있는 편집을 달성 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 훈련이 필요 없는 방식으로, 다양한 이미지 및 편집 환경에 적용 가능 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 향상된 자기 주의 메커니즘 및 수정된 CFG 전략을 통해 고품질 이미지 편집 결과 제공 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
이 논문은 **일관된 이미지 편집**이라는 어려운 문제에 대한 새로운 접근 방식을 제시하여 다양한 분야의 연구자들에게 중요한 의미를 가집니다. **훈련 없이도 다양한 이미지에서 일관된 편집 결과**를 얻을 수 있는 방법을 제시함으로써, 이미지 처리 및 컴퓨터 비전 분야의 발전에 기여할 뿐만 아니라, 향후 연구에 대한 새로운 가능성을 열어줍니다. 특히, **명시적인 대응 관계를 활용**하여 이미지 간의 일관성을 유지하는 방식은 다양한 응용 분야에 적용될 수 있으며, 향후 연구자들이 이를 기반으로 더욱 정교하고 효율적인 이미지 편집 기술을 개발하는 데 도움이 될 것입니다.  또한, **제공된 코드**를 통해 다른 연구자들이 이 방법을 쉽게 활용하고, 발전시킬 수 있도록 지원합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.21079/x2.png)

> 🔼 이 그림은 논문에서 제시하는 Edicho 모델이 다양한 환경에서 촬영된 두 이미지에 대해 일관된 편집 결과를 제로샷 방식으로 생성하는 과정을 보여줍니다. 왼쪽은 부분 편집, 가운데는 개체 편집, 오른쪽은 전체 이미지 편집 결과를 보여주며, 명확한 대응 관계를 활용하여 정확한 일관성을 유지하는 Edicho 모델의 성능을 강조합니다.  모델은 이미지의 부분, 개체 또는 전체에 걸쳐 일관되게 편집을 적용하며, 이미지 간의 명확한 대응 관계(explicit correspondence)를 활용하여 정확성을 높입니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Given two images in the wild, Edicho generates consistent editing versions of them in a zero-shot manner. Our approach achieves precise consistency for editing parts (left), objects (middle), and the entire images (right) by leveraging explicit correspondence.
> </details>





{{< table-caption >}}
| Method | TA ↑ | EC ↑ |
|---|---|---|
| AF [45] | 0.3082 | 0.8569 |
| AD [12] | 0.2981 | 0.8320 |
| PBE [58] | 0.2969 | 0.8683 |
| Ours | **0.3176** | **0.8931** |{{< /table-caption >}}

> 🔼 표 1은 지역적 편집과 전역적 편집에 대한 정량적 결과를 보여줍니다. Custom Diffusion [31]을 따라 텍스트 정렬(TA) 및 편집 일관성(EC)을 기준으로 다양한 방법을 평가했습니다. TA는 생성된 이미지가 입력 프롬프트와 얼마나 잘 정렬되는지를 측정하고, EC는 여러 이미지에서 일관된 편집이 얼마나 잘 유지되는지를 측정합니다. 표에는 각 방법에 대한 TA 및 EC 점수가 나열되어 있으며, 제안된 방법이 다른 방법보다 우수한 성능을 보임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Quantitative results respectively on local and global editing. We follow Custom Diffusion [31] to evaluate various methods on text alignment (TA) and editing consistency (EC).
> </details>





### In-depth insights


#### Wild Image Editing
자연스러운 이미지 편집은 컴퓨터 비전 분야에서 오랫동안 주목받는 과제였습니다. 특히 다양한 조명, 배경, 객체의 포즈 등 예측할 수 없는 요소들이 존재하는 실제 환경(In-the-wild)의 이미지를 일관되게 편집하는 것은 더욱 어려운 문제입니다. **이미지 간 일관성을 유지하는 것은 마케팅 자료, 제품 이미지 향상, 테마 이벤트 사진 편집 등 다양한 응용 분야에서 중요한 요소입니다.** 기존의 이미지 편집 방법들은 각 이미지 별로 독립적으로 작동하거나, 훈련 데이터에 의존하는 한계가 있었습니다.  본 논문에서는 **훈련 없이도 이미지 간의 명시적인 대응 관계를 활용하여 일관성 있는 편집을 가능하게 하는 새로운 방법**을 제시합니다.  **확산 모델(diffusion model) 기반의 훈련 없는 접근 방식**을 통해,  **주의 메커니즘 조작 및 분류기 없는 가이드(CFG) 전략 개선**을 통해 정확한 일관성을 확보합니다. 이러한 기술은 다양한 설정에서 일관된 이미지 편집을 가능하게 하며, 향후 연구에 도움이 될 코드를 공개할 예정입니다.

#### Explicit Correspondence
본 논문에서 제시된 "명시적 대응(Explicit Correspondence)" 개념은 이미지 편집의 정확성과 일관성을 크게 향상시키는 핵심 요소입니다. **기존의 암시적 대응 방식과 달리, 명시적 대응은 이미지 간의 특징 매칭을 명확하게 정의하고, 이를 기반으로 편집 작업을 수행합니다.** 이는 다양한 조건(조명, 배경, 객체 자세 등)에서 촬영된 이미지들에 대해서도 일관된 편집 결과를 얻을 수 있게 해줍니다.  **특히, 어텐션 메커니즘과 CFG(Classifier-free Guidance)에 명시적 대응 정보를 통합함으로써, 이미지 간의 세밀한 특징 일치를 유도하고, 고품질의 편집 결과를 생성하는 데 기여합니다.**  **훈련 과정 없이 추론 단계에서만 적용되는 방식이므로, 다양한 확산 모델에 적용 가능하며 확장성이 뛰어나다는 장점**도 가지고 있습니다.  결론적으로, 명시적 대응 기법은 이미지 편집 분야에서 **일관성과 정확성을 획기적으로 개선**하는 혁신적인 기술이며, 향후 다양한 응용 분야에서 활용될 가능성이 높습니다.  **본 연구는 명시적 대응을 통해 이미지 편집의 새로운 지평을 열었다는 점에서 큰 의의**를 가집니다.

#### Diffusion Model Enhancements
본 논문에서 제시된 확산 모델 개선 사항은 **명시적 대응 관계(explicit correspondence)** 활용에 초점을 맞춥니다.  기존 암묵적 대응 관계 기반 방법들의 한계를 극복하기 위해, 이미지 간의 정확한 특징 매핑을 위해 **강건한 대응 관계 추출기**를 활용합니다.  이를 통해, **자기-주의 메커니즘(self-attention mechanism)**을 개선, 소스 이미지의 관련 특징을 효과적으로 타겟 이미지에 전달하여 일관성 있는 편집을 가능하게 합니다.  **분류기-자유 가이드(CFG, classifier-free guidance)** 전략 개선을 통해,  **사전 계산된 대응 관계**를 통합하여 편집 과정을 미세하게 제어하고 이미지 품질을 유지합니다.  **무조건적 임베딩(unconditional embedding)**을 융합하여 이미지 품질 저하 없이 일관성을 향상시키는 것도 중요한 개선점입니다.  결과적으로, 다양한 환경의 이미지에 대해서도 **강건하고 일관된 편집**을 수행할 수 있는 확산 모델 기반 방법론을 제시합니다.

#### Consistent Editing Results
논문의 "일관된 편집 결과" 제목에 대한 심층적인 분석 결과를 요약하면 다음과 같습니다. **본 연구는 다양한 이미지들에 걸쳐 일관된 편집 결과를 생성하는 새로운 방법론을 제시**합니다. 기존 방법론들이 개별 이미지에 대한 편집에 초점을 맞춘 것과 달리, **본 연구는 이미지 간의 명시적인 대응 관계를 활용하여 여러 이미지에 걸쳐 일관된 편집 결과를 보장**합니다. 이는 **주의 메커니즘과 분류자 없는 안내(CFG)를 개선하여 명시적인 대응 관계를 통합**함으로써 달성됩니다. 실험 결과는 **제안된 방법론이 기존 방법론들에 비해 정량적 및 정성적으로 우수한 성능**을 보임을 보여줍니다. 특히, **다양한 설정에서 일관된 이미지 편집을 효과적으로 수행**하는 능력이 뛰어납니다.  **본 연구는 다양한 응용 분야에서 활용될 수 있는 잠재력**을 지니고 있으며, 향후 연구에 중요한 기여를 할 것으로 예상됩니다.

#### Future Applications
논문의 "미래 응용 분야" 섹션에서는 **일관성 있는 이미지 편집 기술의 다양한 활용 가능성**에 대해 심도 있게 논의할 수 있을 것입니다. 예를 들어, **패션 및 디자인 분야**에서는 다양한 의상이나 액세서리의 이미지를 일관되게 편집하여 제품 카탈로그나 광고 이미지를 제작하는 데 활용될 수 있습니다. **마케팅 및 광고** 분야에서도 제품 이미지를 일관된 스타일로 편집하여 시각적 통일성을 확보하고 소비자에게 더욱 효과적으로 어필할 수 있습니다. 또한, **영화 및 게임 산업**에서는 다양한 캐릭터나 배경 이미지를 일관되게 편집하여 시각적 연출을 향상시키고 현실감을 더할 수 있습니다. **3D 모델링** 분야에서도 일관성 있는 이미지 편집 기술을 이용하여 다양한 각도에서 촬영한 이미지를 바탕으로 3D 모델을 생성하는 데 적용될 수 있습니다. **의료 영상** 분야에서도 여러 장의 의료 영상을 일관되게 분석하여 질병 진단 및 치료 계획 수립에 도움이 될 수 있습니다.  **메타버스 및 가상현실** 분야에서는 사용자들이 자신을 표현할 수 있는 아바타 이미지나 가상 공간의 배경 이미지를 일관되게 편집하여 자신만의 개성을 표현하는 데 활용될 수 있습니다.  **이 밖에도 다양한 분야**에서 일관성 있는 이미지 편집 기술이 활용될 수 있으며, 이 기술이 **향후 이미지 처리 및 편집 기술 발전에 중요한 역할**을 할 것으로 예상됩니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.21079/x3.png)

> 🔼 본 그림은 논문에서 제안하는 명시적 대응 방식과 기존의 암시적 대응 방식을 비교하여 자연스러운 이미지에서의 정확도와 안정성을 보여줍니다. 암시적 대응 방식은 이미지 간의 어텐션 계산을 통해 얻어지며, 노이즈 제거 단계 및 네트워크 레이어의 변화에 따라 정확도와 안정성이 떨어지는 반면, 명시적 대응 방식은 더욱 정확하고 안정적인 결과를 제공합니다. 이를 통해 명시적 대응 방식이 이미지 편집의 일관성을 유지하는 데 더 효과적임을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2:  Comparisons of the implicit and our explicit correspondence prediction for the images in the wild. The implicit correspondence from cross-image attention calculation is less accurate and unstable with the change of denoising steps and network layers.
> </details>



![](https://arxiv.org/html/2412.21079/x4.png)

> 🔼 그림 3은 Edicho의 프레임워크를 보여줍니다. 일관된 이미지 편집을 달성하기 위해, 먼저 입력 이미지에 대해 명시적인 대응 관계를 추출기로 예측합니다. 미리 계산된 대응 관계는 사전 훈련된 확산 모델에 주입되어 (a) 어텐션 특징과 (b) CFG의 잡음이 많은 잠재 변수의 두 가지 수준에서 잡음 제거 과정을 안내합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Framework of Edicho. To achieve consistent editing, we first predict the explicit correspondence with extractors for the input images. The pre-computed correspondence is injected into the pre-trained diffusion models and guide the denoising in the two levels of (a) attention features and (b) noisy latents in CFG.
> </details>



![](https://arxiv.org/html/2412.21079/x5.png)

> 🔼 그림 4는 Adobe Firefly (AF) [45], Anydoor (AD) [12], Paint-by-Example (PBE) [58] 세 가지 방법을 사용하여 이미지의 특정 영역을 편집(Inpainting) 했을 때의 결과를 비교한 것입니다.  각 방법은 입력 이미지의 일부분을 수정하도록 훈련되었으며,  이 그림은 각 방법이 얼마나 정확하게 원하는 부분만을 수정하고 나머지 부분은 보존하는지 보여줍니다.  수정된 영역은 빨간색으로 강조 표시되어 있어, 각 방법의 정확도와 자연스러움을 쉽게 비교할 수 있도록 합니다.  입력 이미지는 여러 유형의 이미지 (얼굴, 강아지, 신발)로 구성되어 있어 다양한 상황에서의 성능을 평가하고자 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4:  Qualitative comparisons on local editing with Adobe Firefly (AF) [45], Anydoor (AD) [12], and Paint-by-Example (PBE) [58]. The inpainted areas of the inputs are highlighted in red.
> </details>



![](https://arxiv.org/html/2412.21079/x6.png)

> 🔼 그림 5는 MasaCtrl [7], StyleAligned [18], Cross-Image-Attention [1] 세 가지 방법과 제안된 방법을 사용한 전역 이미지 편집 결과를 정성적으로 비교한 것입니다.  각 방법은 입력 이미지에 일관된 편집을 적용하는 능력을 보여주며, 제안된 방법이 다른 방법들보다 더 나은 시각적 일관성을 제공함을 보여줍니다.  예시 이미지들은 다양한 물체(자동차, 요정, 로봇 등)에 대한 편집을 포함합니다.  각 이미지의 텍스트 프롬프트는 사용된 편집 내용을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 5:  Qualitative comparisons on global editing with MasaCtrl (MC) [7], StyleAligned (SA) [18], and Cross-Image-Attention (CIA) [1].
> </details>



![](https://arxiv.org/html/2412.21079/x7.png)

> 🔼 그림 6은 제안된 방법의 ablation study 결과를 보여줍니다. (a)는 correspondence-guided attention manipulation (Corr-Attention)에 대한 ablation study 결과이고, (b)는 correspondence-guided CFG (Corr-CFG)에 대한 ablation study 결과입니다. 각 ablation study는 제안된 방법에서 해당 모듈을 제거했을 때의 결과를 보여줍니다. 이를 통해 각 모듈이 전체적인 성능에 미치는 영향을 정량적으로 분석하고, 제안된 방법의 효과를 검증합니다.  Corr-Attention과 Corr-CFG 모두 제안된 방법의 성능 향상에 중요한 역할을 한다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Ablation studies on the (a) correspondence-guided attention manipulation (Corr-Attention) and (b) correspondence-guided CFG (Corr-CFG).
> </details>



![](https://arxiv.org/html/2412.21079/x8.png)

> 🔼 그림 7은 논문에서 제시하는 일관된 이미지 편집 방법(위쪽)과 사용자 정의 기법[48]을 이용하여 생성 모델에 편집된 개념을 주입함으로써 얻을 수 있는 사용자 정의 생성(아래쪽)을 보여줍니다.  간단히 말해, 기존 이미지 편집 결과를 활용하여 새로운 개념을 생성하고 기존 개념을 편집하는 방법을 보여주는 예시입니다.  일관된 이미지 편집의 결과를 기반으로 사용자 정의 생성 모델을 미세 조정하여, 원하는 스타일이나 특징을 가진 새로운 이미지를 생성할 수 있음을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: With outputs from our consistent editing method (upper) and the customization [48] techniques, customized generation (lower) could be achieved by injecting the edited concepts into the generative model.
> </details>



![](https://arxiv.org/html/2412.21079/x9.png)

> 🔼 그림 8은 편집된 이미지를 기반으로 3D 공간에서 2D 점들을 매칭하여 3D 재구성을 수행하는 데 신경 회귀 모델 Dust3R [55]을 사용한 결과를 보여줍니다.  간단히 말해, 일관된 이미지 편집 결과를 이용하여 3D 모델을 재구성하는 과정을 보여주는 그림입니다.  이미지 편집의 일관성을 유지하면서 동시에 3D 정보까지 얻을 수 있음을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: We adopt the neural regressor Dust3R [55] for 3D reconstruction based on the edits by matching the 2D points in a 3D space.
> </details>



![](https://arxiv.org/html/2412.21079/x10.png)

> 🔼 그림 9는 제안된 방법을 사용하여 일관된 이미지 인페인팅(a) 및 변환(b)의 다양한 결과를 보여줍니다. (c)에서는 세 개의 이미지 집합에 대한 편집 결과를 보여줍니다. 그림은 제안된 방법이 다양한 유형의 이미지 편집 작업에 적용될 수 있음을 보여주는 여러 가지 예시를 제공합니다. (a)에서는 배경이나 물체의 일부분을 제거하거나 수정하는 인페인팅 작업의 결과를 보여주고 있으며, (b)에서는 이미지 전체의 스타일이나 색상을 바꾸는 변환 작업의 결과를 보여주고 있습니다. (c)에서는 동일한 방식으로 세 개의 이미지를 일관되게 편집한 결과를 보여줌으로써, 제안된 방법의 일관성과 확장성을 강조합니다. 각 이미지는 서로 다른 스타일, 색상, 구성 등을 가지고 있지만, 제안된 방법은 모든 이미지에 일관된 편집을 적용하여 자연스럽고 조화로운 결과를 얻어냈습니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Diverse results of consistent image inpainting (a) and translation (b) by the proposed method. Editing results for an image set of three images are demonstrated in (c).
> </details>



![](https://arxiv.org/html/2412.21079/x11.png)

> 🔼 그림 S1은 제안된 방법의 추가적인 ablation 연구 결과를 보여줍니다. 위쪽 부분은 correspondence-guided attention에 대한 ablation 연구 결과이고, 아래쪽 부분은 correspondence-guided CFG에 대한 ablation 연구 결과입니다.  각 ablation 연구는 제안된 방법의 특정 구성 요소를 제거하고 그 영향을 시각적으로 보여줍니다.  이는 제안된 방법의 각 구성 요소가 최종 결과에 미치는 영향을 정량적으로 평가하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure S1: Additional ablations on the correspondence-guided attention (upper) and CFG (lower).
> </details>



![](https://arxiv.org/html/2412.21079/x12.png)

> 🔼 그림 S2는 명시적 및 암시적 방법을 사용한 대응 예측의 정확성을 비교 분석한 결과를 보여줍니다.  '암시적' 뒤의 숫자는 각각 대응 예측을 위한 네트워크 계층과 잡음 제거 단계를 나타냅니다.  암시적 방법은 어텐션 메커니즘을 기반으로 이미지 간의 유사성을 계산하여 대응 관계를 예측하지만, 네트워크 계층과 잡음 제거 단계에 따라 예측의 정확성이 달라질 수 있습니다. 반면, 명시적 방법은 보다 강건하고 안정적인 대응 예측을 제공합니다. 이 그림은 본 논문의 제안된 방법의 강점을 보여주는 중요한 증거입니다.
> <details>
> <summary>read the caption</summary>
> Figure S2: Additional correspondence prediction comparisons. The numbers behind “Implicit” respectively indicate the network layer and denoising step for correspondence prediction.
> </details>



![](https://arxiv.org/html/2412.21079/x13.png)

> 🔼 그림 S3은 어텐션 시각화를 사용한 추가적인 대응 예측 결과를 보여줍니다. 가장 높은 가중치를 가진 영역은 점선 원으로 표시되어 있습니다. 이 그림은 명시적인 방법과 암시적인 방법 모두를 사용하여 이미지 간의 대응 관계를 예측한 결과를 보여주며, 어텐션 메커니즘을 통해 어떻게 이미지의 특징들이 서로 매핑되는지를 시각적으로 보여줍니다. 점선 원으로 강조된 영역은 어텐션 가중치가 가장 높은 영역으로, 이미지 간의 대응 관계 예측에 가장 중요한 영역임을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure S3:  Additional correspondence prediction results with attention visualization. Regions with the highest attention weights are outlined with dashed circles.
> </details>



![](https://arxiv.org/html/2412.21079/x14.png)

> 🔼 그림 S4는 논문의 사용자 연구 결과를 보여줍니다. 왼쪽은 일관된 지역 편집에 대한 결과이고, 오른쪽은 일관된 전역 편집에 대한 결과입니다. 사용자 연구에서는 30명의 참가자에게 일관성, 생성 품질, 지시 사항 준수를 기준으로 최상의 옵션을 선택하게 하였습니다. 결과적으로 제안된 방법이 기존 방법보다 상당히 높은 선호도를 얻었습니다. 특히 지역 편집과 전역 편집 모두에서 60% 이상의 참가자가 제안된 방법을 선택했습니다. 이러한 사용자 연구 결과는 제안된 방법의 실용적인 가치와 실제 응용 프로그램에서의 잠재적인 영향을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure S4: User study results of consistent local editing (left) and global editing (right).
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