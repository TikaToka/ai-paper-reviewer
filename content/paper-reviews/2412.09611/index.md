---
title: "FluxSpace: Disentangled Semantic Editing in Rectified Flow Transformers"
summary: "''"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Generation", "🏢 Virginia Tech",]
showSummary: true
date: 2024-12-12
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.09611 {{< /keyword >}}
{{< keyword icon="writer" >}} Yusuf Dalva et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-16 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.09611" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.09611" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/fluxspace-disentangled-semantic-editing-in" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

"""

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} "" {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} "" {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} "" {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
"""

------
#### Visual Insights



![](https://arxiv.org/html/2412.09611/x2.png)

> 🔼 FluxSpace는 Flux와 같은 정류 흐름 변환기에서 텍스트 기반 이미지 편집을 위한 접근 방식입니다. 이 그림은 사람, 동물, 자동차와 같은 다양한 영역에서 의미론적 편집을 일반화하고 거리 이미지와 같이 더 복잡한 장면으로 확장하는 방법을 보여줍니다. FluxSpace는 키워드로 설명된 편집 내용(예: 자동차를 트럭으로 변환하기 위한 '트럭')을 적용할 수 있으며 원본 이미지에서 특정 측면을 대상으로 하기 위해 수동으로 제공된 마스크가 필요하지 않은 얽히지 않은 편집 기능을 제공합니다. 또한 교육이 필요하지 않으며 추론 시간 동안 원하는 편집 내용을 적용할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: FluxSpace. We propose a text-guided image editing approach on rectified flow transformers [14], such as Flux. Our method can generalize to semantic edits on different domains such as humans, animals, cars, and extends to even more complex scenes such as an image of a street (third row, first example). FluxSpace can apply edits described as keywords (e.g. “truck” for transforming a car into a truck) and offers disentangled editing capabilities that do not require manually provided masks to target a specific aspect in the original image. In addition, our method does not require any training and can apply the desired edit during inference time.
> </details>





{{< table-caption >}}
|                                       | 
| :------------------------------------ | 
| ![Uncaptioned image](https://arxiv.org/html/2412.09611/x1.png)|{{< /table-caption >}}

> 🔼 이 표는 FluxSpace를 포함한 다양한 이미지 편집 방법의 성능을 정량적으로 비교한 결과를 보여줍니다. 성능 측정은 CLIP-T, CLIP-I, DINO 지표를 사용하여 텍스트 정렬 및 콘텐츠 보존 측면에서 이루어졌습니다. 비교 대상에는 Latent Diffusion 기반 방법(LEDITS++, TurboEdit)과 Flow-Matching 기반 방법(Sliders-FLUX, RF-Inversion)이 포함됩니다. 또한 사용자 연구를 통해 지각적 평가를 수행하여 FluxSpace가 다른 방법들보다 우수한 성능을 보인다는 주장을 뒷받침합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Quantitative Results. We quantitatively measure the editing performance of our method over competing approaches both in terms of text alignment using CLIP-T [34], and content preservation using CLIP-I [34] and DINO [7] metrics where higher is better for all metrics. We compare our method with both latent diffusion [6, 11], and flow-matching-based approaches [16, 37]. Overall, our method strikes a good balance in terms of alignment with the editing prompt and content preservation. Supplementary to these metrics, we also present a user study as a perceptual evaluation that aligns with our claims regarding edit performance, where our method outperforms the competing approaches.
> </details>





### In-depth insights


#### Rectified Flows
**Rectified Flows**는 이미지 생성에서 혁신적인 접근 방식으로, 노이즈 분포에서 데이터 분포로의 **직선 경로**를 통해 이미지를 생성합니다. GAN과 달리 고정된 latent space를 사용하지 않고 multi-step refinement process를 통해 이미지를 생성하며, 각 단계마다 복잡한 노이즈 패턴의 상호 작용이 발생합니다. 이러한 특징은 **고품질 이미지** 생성에 효과적이지만, latent space의 **해석과 편집이 어렵다는** 단점을 지닙니다. 그러나 **Flux**와 같은 flow-matching transformer는 rectified flow를 활용하여 **높은 충실도의 이미지 생성**을 가능하게 합니다. 본 논문은 rectified flow model에서의 disentangled editing에 대한 연구가 부족함을 지적하고, 의미론적 편집을 위한 새로운 접근 방식을 제시합니다.

#### FluxSpace Editing
**FluxSpace 편집**은 수정된 플로우 트랜스포머에서 의미론적 이미지 편집을 위한 새로운 프레임워크를 제시합니다. FluxSpace는 어텐션 레이어 출력을 활용하여 **세밀한 편집(예: 미소 추가)과 스타일 변경과 같은 거친 수준의 수정**을 모두 허용합니다. 이 방법은 **사전 훈련된 매개변수를 변경하지 않고** 어텐션 출력의 선형 조작을 기반으로 하므로 **추가 훈련 없이** 다양한 편집이 가능합니다. FluxSpace는 이미지 생성 중에 **점진적인 콘텐츠 개선**을 통해 어텐션 레이어가 **매우 분리된 의미 정보를 인코딩**하는 기능을 활용합니다. 이를 통해 **객체 속성에 대한 세부 조정** 또는 전반적인 스타일 변경과 같이 **다양한 시맨틱 편집 작업**을 가능하게 합니다. 게다가, FluxSpace는 편집 과정에서 **이미지 콘텐츠를 보존**하는 데 도움이 되는 **셀프 감독 마스크**를 통합하여 **원치 않는 변경 사항이나 아티팩트 없이** 원하는 편집이 이미지에 정확하게 적용되도록 합니다.

#### Disentanglement
**분리된 표현 학습**은 생성 모델, 특히 이미지 편집 분야에서 핵심 과제입니다. 이는 **서로 얽히지 않고 독립적으로 제어 가능한 특징을 나타내는 잠재 공간**을 학습하는 것을 목표로 합니다. 분리 표현을 통해 이미지의 특정 특징(예: 머리 색깔, 안경 착용 여부)을 다른 특징에 영향을 주지 않고 변경할 수 있습니다. 이러한 분리는 **더욱 정확하고 예측 가능한 편집 기능을 제공**하며 사용자가 원하는 결과를 더 잘 제어할 수 있도록 합니다. 하지만, 완벽한 분리는 어려운 문제이며 현재 연구의 주요 초점입니다. FluxSpace와 같은 최신 기법들은 **트랜스포머 아키텍처와 어텐션 메커니즘**을 활용하여 분리된 표현 학습을 개선하고, 이미지 편집 작업에서 더욱 세밀하고 사실적인 결과를 얻고 있습니다. 하지만 여전히 실제 이미지에 적용할 때의 어려움, 계산 비용 등의 문제점들이 존재합니다.

#### Linearity in Attn
**선형성 가정**은 FluxSpace의 핵심입니다. 어텐션 출력이 선형적으로 조합될 수 있다고 가정함으로써, 의미론적 편집 방향을 정의하고 편집 강도를 제어할 수 있습니다. 이러한 선형성은 의미론적 편집을 위한 **잠재 공간 탐색 및 조작**을 가능하게 합니다. 하지만 이 가정의 유효성은 어텐션 메커니즘의 복잡성과 이미지 생성 과정의 비선형성으로 인해 제한될 수 있습니다. **추가 연구**를 통해 선형성 가정의 한계를 탐구하고, 다양한 편집 작업과 이미지 도메인에서 그 유효성을 검증해야 합니다. 특히, 고차원 어텐션 공간에서의 선형성의 의미, 그리고 이 가정이 편집 결과의 품질과 일관성에 미치는 영향에 대한 깊이 있는 분석이 필요합니다. 궁극적으로, 선형성 가정에 대한 **더욱 엄격한 분석**은 FluxSpace와 같은 이미지 편집 기법의 발전에 중요한 역할을 할 것입니다.

#### Ethical Concerns
**이미지 편집 기술의 발전은 놀라운 가능성을 열었지만, 동시에 심각한 윤리적 문제를 제기합니다.** FluxSpace와 같은 첨단 도구는 이미지 조작을 매우 쉽게 만들어 악의적인 목적으로 사용될 수 있습니다. **개인정보 침해**는 가장 큰 우려 사항 중 하나입니다. 동의 없이 개인의 이미지를 변경하거나 악용할 수 있기 때문입니다. **허위 정보**도 주요 문제입니다. 가짜 뉴스를 만들거나 이미지를 조작하여 여론을 조작하는 데 사용될 수 있습니다. **진실성과 신뢰성 훼손**은 또 다른 중요한 문제입니다. 편집된 이미지가 원본과 구별할 수 없게 되면서 디지털 미디어의 신뢰도가 떨어지고 있습니다. 이러한 위험을 완화하기 위해서는 **책임감 있는 기술 사용을 보장하는 윤리 지침과 규제 프레임워크**를 개발하고 구현하는 것이 중요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.09611/x3.png)

> 🔼 FluxSpace 프레임워크는 Flux의 결합 트랜스포머 블록 내에서 이중 레벨 편집 체계를 도입하여 거친 시각 편집과 세밀한 시각 편집을 가능하게 합니다. 거친 편집은 스타일 변경과 같은 전역적 변경을 허용하며, 기본 조건(c_pool)과 편집 조건(c_e,pool)의 풀링된 표현과 스케일 λ_coarse로 제어됩니다(a). 세밀한 편집의 경우, 기본, 이전 및 편집 주의 출력을 사용하는 선형 편집 체계가 정의되며, 스케일 λ_fine에 의해 안내됩니다(b). 이 유연한 디자인을 통해 프레임워크는 선형으로 조정 가능한 스케일을 사용하여 거친 레벨과 세밀한 레벨 편집을 모두 수행할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: FluxSpace Framework. The FluxSpace framework introduces a dual-level editing scheme within the joint transformer blocks of Flux, enabling coarse and fine-grained visual editing. Coarse editing operates on pooled representations of base (cp⁢o⁢o⁢lsubscript𝑐𝑝𝑜𝑜𝑙c_{pool}italic_c start_POSTSUBSCRIPT italic_p italic_o italic_o italic_l end_POSTSUBSCRIPT) and edit (ce,p⁢o⁢o⁢lsubscript𝑐𝑒𝑝𝑜𝑜𝑙c_{e,pool}italic_c start_POSTSUBSCRIPT italic_e , italic_p italic_o italic_o italic_l end_POSTSUBSCRIPT) conditions, allowing global changes like stylization, controlled by the scale λc⁢o⁢a⁢r⁢s⁢esubscript𝜆𝑐𝑜𝑎𝑟𝑠𝑒\lambda_{coarse}italic_λ start_POSTSUBSCRIPT italic_c italic_o italic_a italic_r italic_s italic_e end_POSTSUBSCRIPT (a). For fine-grained editing, we define a linear editing scheme using base, prior, and edit attention outputs, guided by scale λf⁢i⁢n⁢esubscript𝜆𝑓𝑖𝑛𝑒\lambda_{fine}italic_λ start_POSTSUBSCRIPT italic_f italic_i italic_n italic_e end_POSTSUBSCRIPT (b). With this flexible design, our framework is both able to perform coarse-level and fine-grained editing, with a linearly adjustable scale.
> </details>



![](https://arxiv.org/html/2412.09611/x4.png)

> 🔼 이 그림은 FluxSpace의 얼굴 편집에 대한 정성적 결과를 보여줍니다. FluxSpace는 안경 추가와 같은 세밀한 편집부터 만화 스타일과 같은 이미지 전체 구조의 변경까지 다양한 편집을 수행할 수 있습니다. FluxSpace는 얽히지 않은 표현을 사용하여 이미지 편집을 수행하므로 원본 이미지의 속성을 유지하면서 다양한 속성을 정확하게 편집할 수 있습니다. 그림에서 첫 번째 행은 안경, 선글라스, 수염, 미소, 놀란 표정과 같은 세밀한 얼굴 편집 결과를 보여줍니다. 두 번째 행은 나이, 성별, 과체중, 광대 분장, 만화 스타일, 3D 만화 스타일과 같이 이미지 전체 구조를 변경하는 편집 결과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Qualitative Results on Face Editing. Our method can perform a variety of edits from fine-grained face editing (e.g. adding eyeglasses) to changes over the overall structure of the image (e.g. comics style). As our method utilizes disentangled representations to perform image editing, we can precisely edit a variety of attributes while preserving the properties of the original image.
> </details>



![](https://arxiv.org/html/2412.09611/x5.png)

> 🔼 이 그림은 FluxSpace의 이미지 편집 능력을 다른 최첨단 방법들과 질적으로 비교한 결과를 보여줍니다. 비교 대상에는 LEDITS++, TurboEdit, Sliders-FLUX, RF-Inversion이 포함되며, '미소', '안경', '나이'와 같은 다양한 편집 작업에 대한 질적 결과가 제시되어 있습니다. FluxSpace는 편집된 이미지가 의미적으로 정확할 뿐만 아니라 입력 이미지의 원래 특징을 잘 유지하는 측면에서 다른 방법들보다 우수함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Qualitative Comparisons. We compare our method both with latent diffusion-based approaches (LEDITS++ [6] and TurboEdit [11]) and flow-based methods (Sliders-FLUX [16] and RF-Inversion [37]) in terms of their disentangled editing capabilities. We present qualitative results for smile, eyeglasses, and age edits where our method succeeds over competing methods in both reflecting the semantic and preserving the input identity.
> </details>



![](https://arxiv.org/html/2412.09611/x6.png)

> 🔼 이 그림은 FluxSpace를 실제 이미지 편집에 적용한 결과를 보여줍니다. RF-Inversion[37]의 역변환 방식을 활용하여 FluxSpace를 실제 이미지에 적용했습니다. 그림에서 볼 수 있듯이, 동일한 역변환 설정을 사용하는 기준 접근 방식과 비교했을 때 FluxSpace는 나이, 성별과 같은 편집에서 향상된 분리 성능을 보입니다. 즉, 원하지 않는 부분의 변경 없이 원하는 편집만 적용됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Real Image Editing. By integrating FluxSpace on the inversion approach proposed by RF-Inversion [37], we extend our method for real image editing task. As we show qualitatively, our method achieves improved disentanglement over the performed edits compared to the baseline approach, where we use identical hyperparameters for the inversion task on both approaches.
> </details>



![](https://arxiv.org/html/2412.09611/extracted/6065524/figs/user_study_setup.png)

> 🔼 이 그림은 FluxSpace 프레임워크 내에서 도입된 하이퍼파라미터에 대한 절제 연구 결과를 보여줍니다. 구체적으로는 거친 편집 스케일(λc⁢o⁢a⁢r⁢s⁢e), 세밀한 편집 스케일(λf⁢i⁢n⁢e), 마스킹 계수(τm) 및 편집 시작 시점(t)에 대한 절제 연구를 수행했습니다. 모든 절제 연구에 대해 지정된 하이퍼파라미터 값을 변경하면서 얻은 정성적 결과를 보고합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Ablation Study. We present ablations over the hyperparameters introduced within the FluxSpace framework. Specifically, we perform ablations on coarse editing scale λc⁢o⁢a⁢r⁢s⁢esubscript𝜆𝑐𝑜𝑎𝑟𝑠𝑒\lambda_{coarse}italic_λ start_POSTSUBSCRIPT italic_c italic_o italic_a italic_r italic_s italic_e end_POSTSUBSCRIPT, fine-grained editing scale λf⁢i⁢n⁢esubscript𝜆𝑓𝑖𝑛𝑒\lambda_{fine}italic_λ start_POSTSUBSCRIPT italic_f italic_i italic_n italic_e end_POSTSUBSCRIPT, masking coefficient τmsubscript𝜏𝑚\tau_{m}italic_τ start_POSTSUBSCRIPT italic_m end_POSTSUBSCRIPT and timestep t𝑡titalic_t when the editing is initiated. For all ablations, we report qualitative results for changing values of the specified hyperparameters.
> </details>



![](https://arxiv.org/html/2412.09611/x7.png)

> 🔼 사용자 연구 설정: 편집되지 않은 이미지와 편집된 이미지 쌍을 사용하여 사용자 연구를 진행합니다. 각 편집 방법에 대해 편집이 적용되지 않은 원본 이미지와 편집된 이미지를 제공하고 사용자에게 1에서 5까지의 척도로 편집을 평가하도록 요청합니다. 사용자에게 선호도를 묻는 리커트 척도에서 1은 만족스럽지 않은 편집, 5는 만족스러운 편집에 해당합니다. 그림에서 왼쪽은 '웃지 않는' 원본 이미지이고, 오른쪽은 '웃는' 편집 이미지입니다. 사용자는 편집된 이미지가 원본 이미지의 얼굴 특징(예: 헤어스타일, 수염, 옷)을 유지하면서 얼마나 잘 '웃음'을 반영하는지 1점(매우 아님)에서 5점(매우 그렇다)까지 평가합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: User Study Setup. We conduct our user study on unedited-edited image pairs. For each editing method, we provide the original image where the edit is not applied, with the edited image, and ask the users to rate the edit from a scale of 1-to-5. On the Likert scale that the users are asked to provide their preference on, 1 corresponds to unsatisfactory editing and 5 corresponds to a satisfactory edit.
> </details>



![](https://arxiv.org/html/2412.09611/x8.png)

> 🔼 이 그림은 FluxSpace가 다른 편복원 기반 이미지 편집 방법(Prompt2Prompt, PnP-Diffusion)과 비교하여 어떻게 disentangled 편집을 더 잘 수행하는지 보여주는 추가적인 정성적 비교 결과를 제공합니다. FluxSpace는 안경 추가 및 나이 변경과 같은 다양한 편집 작업에서 원본 이미지의 내용을 보존하면서 의미적으로 정확한 편집을 달성하는 반면, 비교 대상 방법들은 편집된 결과에서 아티팩트를 생성하거나 피사체의 정체성을 크게 변경하는 경향이 있습니다. 특히, 안경 편집의 경우 두 비교 대상 방법 모두 아티팩트가 발생하고, 나이 편집의 경우 피사체의 정체성이 크게 변경됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Additional Qualitative Comparisons. In addition to comparisons provided in the main paper, we provide additional comparisons with Prompt2Prompt [18] (with Null-Text Inversion [27]) and PnP-Diffusion [39], as Stable Diffusion based editing methods. As we demonstrate qualitatively, FluxSpace both achieves disentangled and semantically correct edits where competing methods contain artifacts in edited results (see the edit “Eyeglasses” for both methods), and significantly alter the subject identity (see “Age” edit).
> </details>



![](https://arxiv.org/html/2412.09611/x9.png)

> 🔼 이 그림은 FluxSpace의 성별 편집 결과를 보여줍니다. 남성에서 여성, 여성에서 남성으로의 변환을 성공적으로 수행하며, 인물 사진과 복잡한 장면 모두에서 편집 결과를 제공합니다. 얼굴 세부 사항을 유지하고 배경과 같은 편집과 무관한 부분을 보존하면서 원하는 편집만 수행합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Gender Editing Results. We provide additional editing results for editing the gender semantics. As shown in the examples, our method succeeds in both male-to-female and female-to-male translations. We provide editing results on both portrait images, where our edits preserve the facial details, and edits on complex scenes where we succeed in only editing the human subject. Both in terms of preserving the identity of the subject and the background details, FluxSpace succeeds in the disentanglement editing task.
> </details>



![](https://arxiv.org/html/2412.09611/x10.png)

> 🔼 이 그림은 FluxSpace의 '선글라스 추가' 편집 기능에 대한 추가적인 정성적 결과를 보여줍니다. 인물 사진과 복잡한 장면 모두에서 사람 피사체에 대해 FluxSpace가 입력 마스크 없이도 편집이 적용되어야 할 위치를 정확하게 타겟팅하는 방법을 보여줍니다. 첫 번째 두 행은 사람 피사체가 이미지의 주요 초점인 경우를, 마지막 두 행은 사람 피사체가 장면의 일부인 경우를 나타냅니다. 두 경우 모두 FluxSpace는 원하는 편집을 수행하고 편집과 관련 없는 세부 정보를 보존하는 데 성공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Sunglasses Editing Results. We provide additional qualitative results for the edit “adding sunglasses”. As we demonstrate on human subjects in both portrait images and more complex scenes, our editing method can accurately target where the edit should be applied without any input mask. We show the editing capabilities of FluxSpace both in images where the human subject is the main focus of the image (first two rows) and with human subjects as a part of a scene (last two rows). In both cases, our method succeeds in performing the desired edit and preserving the edit-irrelevant details.
> </details>



![](https://arxiv.org/html/2412.09611/x11.png)

> 🔼 이 그림은 FluxSpace가 이미지의 전체적인 모습에 영향을 주는 추상적인 개념을 사용한 편집 결과를 보여줍니다. 첫 번째 행은 편집되지 않은 이미지의 구조를 해석하여 이미지 콘텐츠를 변경하는 편집(예: '벚꽃' 편집을 위한 배경의 나무)을 보여주고, 두 번째 행은 이미지의 스타일과 전체적인 모습을 변경하는 편집을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Conceptual Editing Results. We provide editing results with abstract concepts, that affect the overall appearance of the image. Our method succeeds in performing edits that alter the content of the image (top row) by being able to interpret the structures in the unedited image (e.g. the trees on the back for the edit “cherry blossom”) and can change the style and overall appearance of the image (bottom row).
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
{{< /gallery >}}