---
title: "Through-The-Mask: Mask-based Motion Trajectories for Image-to-Video Generation"
summary: "마스크 기반 모션 경로를 이용한 2단계 이미지-비디오 생성 프레임워크인 THROUGH-THE-MASK가 다중 객체의 정확한 애니메이션을 가능하게 합니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Generation", "🏢 Meta",]
showSummary: true
date: 2025-01-06
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.03059 {{< /keyword >}}
{{< keyword icon="writer" >}} Guy Yariv et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-07 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.03059" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.03059" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/through-the-mask-mask-based-motion" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 이미지-비디오 생성 모델들은 다중 객체가 등장하는 복잡한 장면에서 객체의 움직임을 정확하고 일관되게 생성하는 데 어려움을 겪었습니다. 이는 객체의 의미와 움직임을 동시에 추론해야 하는 모델의 복잡성 때문입니다.  이 논문에서는 이 문제를 해결하기 위해 **마스크 기반 모션 경로**라는 새로운 중간 표현을 제안합니다. 이는 객체의 의미 정보와 움직임을 효율적으로 담고 있어, 모델이 보다 쉽게 객체의 동작을 이해하고 생성할 수 있도록 돕습니다.

제안된 방법은 이미지에서 마스크 기반 모션 경로를 생성하는 첫 번째 단계와, 이를 이용하여 최종 비디오를 생성하는 두 번째 단계로 구성됩니다.  실험 결과, 제안된 방법은 기존 모델들에 비해 **시간적 일관성, 모션 현실성, 시각적 일관성, 그리고 텍스트의 충실도 측면에서 모두 성능이 향상**되었음을 보여줍니다. 특히, 다중 객체가 등장하는 복잡한 장면에서도 우수한 성능을 보였습니다. 이 연구는 이미지-비디오 생성 분야의 발전에 중요한 기여를 할 것으로 기대됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 마스크 기반 모션 경로를 중간 표현으로 사용하는 새로운 2단계 이미지-비디오 생성 프레임워크 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 다중 객체 시나리오에서 정확하고 일관된 객체 모션 생성 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 기존 방법 대비 향상된 시간적 일관성, 모션 현실성, 시각적 일관성, 텍스트 충실도 달성 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
이 논문은 **복잡한 다중 객체 시나리오에서도 정확하고 일관된 객체 움직임을 생성하는 데 어려움을 겪는 기존 이미지-비디오 생성 모델의 한계를 해결**합니다.  마스크 기반 모션 경로를 중간 표현으로 사용하여 이미지-비디오 생성 과정을 두 단계로 분해하는 새로운 프레임워크를 제시함으로써, **보다 사실적이고 일관성 있는 비디오 생성**을 가능하게 합니다. 이는 이미지-비디오 생성 분야의 발전에 중요한 기여를 할 뿐만 아니라, 향후 연구를 위한 새로운 방향을 제시합니다. 특히, **다중 객체의 상호 작용 및 동작을 보다 정확하게 모델링하는 연구에 중요한 참고 자료**가 될 것입니다.  이 연구는 이미지-비디오 생성 기술의 실용성을 높이고 다양한 응용 분야에 적용 가능성을 확장하는 데 기여할 것입니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.03059/x2.png)

> 🔼 본 논문의 그림 1은 Through-The-Mask (TTM) 방법을 보여줍니다. TTM은 제공된 텍스트 자막을 기반으로 입력 이미지를 애니메이션으로 만드는 이미지-비디오 변환 기법입니다. 그림에서 2행과 4행은 TTM에 의해 생성된 비디오를 보여주고, 1행과 3행은 여러 객체의 정확한 애니메이션을 가능하게 하는 마스크 기반 모션 경로를 보여줍니다.  즉, TTM은 텍스트 설명을 사용하여 입력 이미지의 객체들을 자연스럽게 움직이는 비디오로 변환합니다. 이때, 객체의 움직임은 마스크 기반의 모션 경로를 통해 제어되어 여러 객체가 동시에 정확하게 움직이는 것을 가능하게 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  Through-The-Mask is an Image-to-Video method that animates an input image based on a provided text caption. The generated video (rows 2 and 4) leverages mask-based motion trajectories (rows 1 and 3), enabling accurate animation of multiple objects.
> </details>





{{< table-caption >}}
| Method | FVD ↓ | CF ↑ | ViCLIP-T ↑ | ViCLIP-V ↑ | AD | Text | Motion | Quality | FVD ↓ | CF ↑ | ViCLIP-T ↑ | ViCLIP-V ↑ | AD | Text | Motion | Quality |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Single-Object |  |  |  |  |  |  |  |  | Multi-Object |  |  |  |  |  |  |  |
|  |  |  |  |  |  | align. | consist. |  |  |  |  |  | align. | consist. |  |
| VideoCrafter [10] | 1484.18 | 0.966 | 0.209 | 0.796 | 2.93 | 84.3 | 84.3 | 81.2 | 1413.83 | 0.966 | 0.208 | 0.802 | 3.75 | 84.3 | 87.5 | 92.1 |
| DynamiCrafter [54] | 1442.48 | 0.942 | 0.214 | 0.817 | 8.94 | 75.0 | 81.2 | 82.8 | 1300.07 | 0.947 | 0.211 | 0.834 | 7.56 | 75.0 | 73.4 | 76.5 |
| Motion-I2V [43] | 1195.08 | 0.937 | 0.220 | 0.822 | 6.28 | 75.0 | 89.0 | 93.7 | 1162.06 | 0.935 | 0.219 | 0.821 | 6.97 | 81.0 | 89.0 | 95.3 |
| ConsistI2V [41] | 1206.61 | 0.951 | 0.218 | 0.839 | 5.21 | 65.6 | 78.1 | 81.2 | 1186.10 | 0.935 | 0.217 | 0.850 | 7.25 | 81.2 | 82.8 | 84.3 |
| TI2V (UNet) | 1285.99 | 0.942 | 0.219 | 0.877 | 5.90 | 53.1 | 59.3 | 70.3 | 1410.68 | 0.942 | 0.218 | 0.883 | 7.93 | 62.5 | 64.0 | 60.0 |
| Ours (UNet) | **925.39** | **0.969** | **0.220** | **0.888** | 4.70 | - | - | - | **1089.86** | **0.966** | **0.220** | **0.896** | 5.59 | - | - | - |
| TI2V (DiT) | 1232.89 | 0.924 | 0.223 | 0.797 | 10.87 | 65.6 | 73.4 | 68.7 | 1156.82 | 0.917 | 0.221 | 0.805 | 10.52 | 64.0 | 59.3 | 64.0 |
| Ours (DiT) | **1216.83** | **0.945** | **0.226** | **0.860** | 7.22 | - | - | - | **1134.71** | **0.948** | **0.225** | **0.863** | 7.48 | - | - | - |{{< /table-caption >}}

> 🔼 표 1은 SA-V-128 벤치마크에서 단일 객체 및 다중 객체 설정에 대한 결과를 보여줍니다.  FVD, CLIPFrame(CF), ViCLIP-T, ViCLIP-V, 평균 변위(AD) 지표와 더불어 사람의 평가 점수를 제시합니다. 사람 평가는 Through-The-Mask 결과를 선호하는 평가자의 비율을 보여줍니다.  즉, 제시된 다양한 지표를 통해 Through-The-Mask 모델의 성능을 정량적으로 평가하고 사람의 주관적 판단을 통해 정성적으로도 평가하여 모델의 효과성을 다각적으로 분석한 표입니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Results for single-object and multi-object settings on the SA-V-128 Benchmark. We report FVD, CLIPFrame (CF), ViCLIP-T, ViCLIP-V, and Average Displacement (AD), along with human ratings. Human evaluation shows the percentage of raters that prefer the results of Through-The-Mask.
> </details>





### In-depth insights


#### Mask-based Motion
본 논문에서 제시된 마스크 기반 모션은 이미지-비디오 생성에 있어 혁신적인 접근 방식을 제시합니다. **마스크를 활용하여 객체의 윤곽을 추출하고, 시간에 따른 변화를 추적함으로써 객체의 움직임을 정확하게 표현**합니다. 기존의 픽셀 단위 모션 추정 방식과 달리, 마스크 기반 모션은 **객체 단위의 추상적인 표현**을 제공하여 복잡한 다중 객체 시나리오에서도 정확하고 일관된 애니메이션을 가능하게 합니다. 또한, **마스크 기반 모션은 의미 정보와 운동 정보를 동시에 담고 있어** 비디오 생성 네트워크가 움직임과 의미를 효과적으로 통합하는 데 도움이 됩니다. 본 논문에서 제안한 방법은 기존의 단일 단계 접근 방식과 달리, 마스크 기반 모션을 중간 표현으로 사용하여 **두 단계로 구성된 계층적 생성 과정**을 통해 더욱 정확하고 사실적인 비디오를 생성합니다. 이는 **모션 예측의 정확도를 높이고, 다중 객체 간 상호 작용을 효과적으로 모델링**하는 데 기여합니다.  **마스크 기반 모션의 장점은 다중 객체 시나리오에서의 뛰어난 성능**에 있습니다. 즉, 여러 객체들이 동시에 복잡한 움직임을 보이는 경우에도 각 객체의 움직임을 정확하게 파악하여 자연스러운 애니메이션을 생성하는 것이 가능합니다.

#### Two-Stage I2V
이 논문에서 제안하는 **두 단계 I2V(Image-to-Video) 방법론**은 이미지를 비디오로 변환하는 과정을 **두 개의 독립적인 단계**로 분해하여 기존의 단일 단계 접근 방식의 한계를 극복합니다. 첫 번째 단계는 **중간 표현 생성 단계**로, 입력 이미지와 텍스트 설명을 바탕으로 마스크 기반 동작 궤적을 생성합니다. 이는 개체의 의미 정보와 움직임을 효율적으로 표현하여 **다중 개체의 정확한 애니메이션**을 가능하게 합니다. 두 번째 단계는 **비디오 생성 단계**로, 첫 번째 단계에서 생성된 중간 표현과 입력 이미지, 텍스트 설명을 조건으로 하여 최종 비디오를 생성합니다. 이러한 두 단계 접근 방식은 개체의 의미 정보와 움직임을 명시적으로 분리하여 모델링함으로써 **정확하고 일관성 있는 개체 움직임**을 생성하는 데 효과적입니다. 특히 **다중 개체 시나리오**에서 기존 방법론이 어려움을 겪는 문제점을 해결하는 데 강점을 보입니다.

#### Attention Blocks
본 논문에서 제시된 어텐션 블록은 **마스크 기반**이라는 점에서 독특합니다. 단순히 모든 픽셀에 대한 어텐션을 계산하는 대신, **객체별 마스크**를 활용하여 각 객체에 대한 어텐션을 독립적으로 계산합니다. 이는 여러 객체가 동시에 등장하는 복잡한 장면에서도 각 객체의 움직임과 상호작용을 정확하게 모델링할 수 있도록 합니다. 또한, **두 가지 유형의 어텐션 메커니즘** (마스크드 크로스-어텐션과 마스크드 셀프-어텐션)을 결합하여 **시-공간적 일관성**을 확보하고, 텍스트 프롬프트 정보를 효과적으로 통합합니다. 이러한 설계는 특히 다중 객체가 등장하는 어려운 시나리오에서 성능 향상에 기여하며, **실제적인 영상 생성**에 중요한 역할을 수행합니다. **단일 객체뿐 아니라 다중 객체** 상황 모두에서 뛰어난 성능을 보였고, 향후 영상 생성 모델 개발에 중요한 참고 자료가 될 것으로 기대됩니다.

#### Ablation Study
본 논문의 "절제 연구" 부분은 제안된 방법의 각 구성 요소의 중요성을 밝히는 데 중점을 둡니다. **마스크 기반 모션 경로 생성의 핵심적인 역할**을 보여주는 실험 결과를 통해, **마스크 기반 모션 정보가 단순 광학 흐름보다 우수한 성능을 제공**함을 입증합니다. 또한, **마스크 기반 어텐션 메커니즘의 효과**를 다양한 설정에서 평가하여 모델 성능 향상에 대한 기여도를 정량적으로 제시합니다. 특히, **마스크 크로스-어텐션과 마스크 셀프-어텐션의 상호작용**에 대한 분석을 통해, 개별 객체의 모션과 상호작용을 정확하게 모델링하는 데 중요한 역할을 수행함을 밝힙니다. 이러한 분석 결과는 제안된 방법의 설계가 효율적이며, 각 구성 요소가 전체 시스템 성능에 유의미한 영향을 미침을 보여줍니다.  **결과적으로, 이 절제 연구는 제안된 모델의 강점과 각 구성 요소의 상호 연관성을 명확히 제시하여 신뢰성을 높입니다.**

#### Future I2V
미래의 영상 생성(I2V) 기술은 **더욱 사실적이고, 일관성 있으며, 다양한 객체의 상호작용을 정확하게 표현하는 방향**으로 발전할 것입니다.  **텍스트 기반의 제어 기능 향상**은 물론, **다양한 모달리티(예: 오디오, 센서 데이터)와의 통합**을 통해 더욱 풍부하고 몰입적인 경험을 제공하는 시스템이 등장할 것입니다.  **효율성 향상**을 위한 경량화 모델 개발과 **실시간 처리** 기술 개발도 중요한 연구 과제입니다.  특히, **복잡한 움직임과 상호작용을 포함하는 다중 객체 시나리오**에서의 정확한 영상 생성은 앞으로 해결해야 할 주요 과제이며, 이를 위해서는 **더욱 발전된 시각적 이해 능력과 정교한 운동 모델링 기술**이 필요합니다.  또한, **윤리적 문제 및 개인정보 보호 문제**에 대한 고려 역시 미래 I2V 기술 개발에 있어서 중요한 요소가 될 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.03059/x3.png)

> 🔼 그림 2는 제안된 이미지-비디오 생성 프레임워크의 개요를 보여줍니다. 참조 이미지 x<sup>(0)</sup>와 텍스트 프롬프트 c를 일관된 비디오 시퀀스 x̂로 변환하는 과정을 나타냅니다. 미리 훈련된 LLM을 사용하여 동작 관련 프롬프트 c<sub>motion</sub>과 개별 객체 관련 프롬프트 c<sub>local</sub>={c<sub>local</sub><sup>(1)</sup>,...,c<sub>local</sub><sup>(L)</sup>}를 추출하여 각 객체의 의도된 동작을 포착합니다. SAM2를 사용하여 참조 이미지 x<sup>(0)</sup>로부터 초기 분할 마스크 s<sup>(0)</sup>을 생성합니다. 1단계에서는 이미지-동작 모델이 x<sup>(0)</sup>, s<sup>(0)</sup>, c<sub>motion</sub>을 사용하여 객체별 이동 경로를 나타내는 마스크 기반 동작 경로 ŝ를 생성합니다. 2단계에서는 동작-비디오 모델이 x<sup>(0)</sup>, 생성된 경로 ŝ, 전역 조건으로서의 텍스트 프롬프트 c, 마스크 어텐션 블록(3.3절)을 통해 객체별 프롬프트 c<sub>local</sub>을 입력받아 최종 비디오 x̂를 생성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2:  Overview of our I2V framework, transforming a reference image x(0)superscript𝑥0x^{(0)}italic_x start_POSTSUPERSCRIPT ( 0 ) end_POSTSUPERSCRIPT and text prompt c𝑐citalic_c into a coherent video sequence x^^𝑥\hat{x}over^ start_ARG italic_x end_ARG. A pre-trained LLM is used to derive the motion-specific prompt cm⁢o⁢t⁢i⁢o⁢nsubscript𝑐𝑚𝑜𝑡𝑖𝑜𝑛c_{motion}italic_c start_POSTSUBSCRIPT italic_m italic_o italic_t italic_i italic_o italic_n end_POSTSUBSCRIPT and object-specific prompts cl⁢o⁢c⁢a⁢l={cl⁢o⁢c⁢a⁢l(1),…,cl⁢o⁢c⁢a⁢l(L)}subscript𝑐𝑙𝑜𝑐𝑎𝑙superscriptsubscript𝑐𝑙𝑜𝑐𝑎𝑙1…superscriptsubscript𝑐𝑙𝑜𝑐𝑎𝑙𝐿c_{local}=\{c_{local}^{(1)},\dots,c_{local}^{(L)}\}italic_c start_POSTSUBSCRIPT italic_l italic_o italic_c italic_a italic_l end_POSTSUBSCRIPT = { italic_c start_POSTSUBSCRIPT italic_l italic_o italic_c italic_a italic_l end_POSTSUBSCRIPT start_POSTSUPERSCRIPT ( 1 ) end_POSTSUPERSCRIPT , … , italic_c start_POSTSUBSCRIPT italic_l italic_o italic_c italic_a italic_l end_POSTSUBSCRIPT start_POSTSUPERSCRIPT ( italic_L ) end_POSTSUPERSCRIPT }, capturing each object’s intended motion. We generate an initial segmentation mask s(0)superscript𝑠0s^{(0)}italic_s start_POSTSUPERSCRIPT ( 0 ) end_POSTSUPERSCRIPT from x(0)superscript𝑥0x^{(0)}italic_x start_POSTSUPERSCRIPT ( 0 ) end_POSTSUPERSCRIPT using SAM2. In Stage 1, the Image-to-Motion utilizes x(0)superscript𝑥0x^{(0)}italic_x start_POSTSUPERSCRIPT ( 0 ) end_POSTSUPERSCRIPT, s(0)superscript𝑠0s^{(0)}italic_s start_POSTSUPERSCRIPT ( 0 ) end_POSTSUPERSCRIPT, and cm⁢o⁢t⁢i⁢o⁢nsubscript𝑐𝑚𝑜𝑡𝑖𝑜𝑛c_{motion}italic_c start_POSTSUBSCRIPT italic_m italic_o italic_t italic_i italic_o italic_n end_POSTSUBSCRIPT to generate mask-based motion trajectories s^^𝑠\hat{s}over^ start_ARG italic_s end_ARG that represent object-specific movement paths. In Stage 2, the Motion-to-Video takes as input x(0)superscript𝑥0x^{(0)}italic_x start_POSTSUPERSCRIPT ( 0 ) end_POSTSUPERSCRIPT, the generated trajectories s^^𝑠\hat{s}over^ start_ARG italic_s end_ARG, the text prompt c𝑐citalic_c as a global condition, and object-specific prompts cl⁢o⁢c⁢a⁢lsubscript𝑐𝑙𝑜𝑐𝑎𝑙c_{local}italic_c start_POSTSUBSCRIPT italic_l italic_o italic_c italic_a italic_l end_POSTSUBSCRIPT through a masked attention blocks (Section 3.3), producing the final video x^^𝑥\hat{x}over^ start_ARG italic_x end_ARG.
> </details>



![](https://arxiv.org/html/2501.03059/x4.png)

> 🔼 그림 3은 마스크 처리된 어텐션 블록의 작동 방식을 보여줍니다. 정사각형은 비디오의 잠재 패치를 나타내며, 색상으로 객체(예: 고양이 또는 개)를 구분합니다. 삼각형은 프롬프트 토큰을 나타내며, 회색은 전체 프롬프트를, 객체별 색상은 지역 프롬프트를 나타냅니다. 이 과정은 모든 패치에 대한 자기 어텐션, 각 객체에 제한된 마스크 처리된 자기 어텐션, 전체 프롬프트를 통합하는 교차 어텐션, 그리고 객체별 프롬프트를 정렬하는 마스크 처리된 교차 어텐션을 포함합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Illustration of the masked attention block. Squares represent video latent patches, color-coded to indicate objects (e.g., cat or dog). Triangles denote prompt tokens: gray for global prompts and object-specific colors for local prompts. The pipeline features self-attention for all patches, masked self-attention restricted to each object, cross-attention integrating global prompts, and masked cross-attention aligning object-specific prompts.
> </details>



![](https://arxiv.org/html/2501.03059/x5.png)

> 🔼 본 그림은 논문의 SA-V-128 벤치마크에서 생성된 비디오의 시각적 비교를 보여줍니다. Through-The-Mask 모델과 TI2V 기준 모델의 결과를 비교하여 각 모델의 성능 차이를 보여줍니다. 여러 개의 객체가 포함된 복잡한 동작들을 얼마나 정확하게 애니메이션으로 만들었는지 보여주는 대표적인 예시들을 보여줍니다.  각 비디오는 입력 이미지와 텍스트 프롬프트를 기반으로 생성됩니다.  Through-The-Mask 모델은 여러 객체의 동작을 더욱 정확하고 일관되게 표현하는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Qualitative comparison: Visual examples of generated videos for Through-The-Mask compared to the TI2V baseline on examples from the SA-V-128 benchmark.
> </details>



![](https://arxiv.org/html/2501.03059/x6.png)

> 🔼 이 그림은 이미지에서 비디오 생성을 위한 중간 표현으로 분할 마스크와 광학 흐름을 사용하여 생성된 비디오의 질적 비교를 보여줍니다. 첫 번째 행은 입력 이미지와 텍스트, 두 번째 행은 생성된 마스크, 세 번째 행은 생성된 광학 흐름을 보여줍니다. 네 번째와 다섯 번째 행은 생성된 비디오를 보여주는데, 네 번째 행은 마스크 기반 모델을 사용하고, 다섯 번째 행은 흐름 기반 모델을 사용합니다. 이를 통해 마스크 기반 방법이 흐름 기반 방법보다 더 나은 비디오 품질을 생성한다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Qualitative comparison of generated videos using segmentation masks vs optical flow as an intermediate motion representation. The first row shows the input image and text, the second row displays the generated masks, and the third row presents the generated optical flow. The fourth and fifth rows show the generated videos, with the fourth row using our mask-based model and the fifth using our flow-based model.
> </details>



![](https://arxiv.org/html/2501.03059/x7.png)

> 🔼 그림 6은 제안된 Through-The-Mask 방법의 다양한 설정에서 생성된 비디오들을 정성적으로 비교한 것입니다. 마스크 기반 크로스 어텐션, 마스크 기반 셀프 어텐션, 두 기법 모두 적용한 경우, 그리고 마스크 어텐션을 전혀 사용하지 않은 경우의 네 가지 설정을 비교합니다. 마스크 어텐션을 사용하지 않은 경우, 만화 속 슈퍼히어로는 기도 동작을 제대로 수행하지 못합니다. 마스크 기반 셀프 어텐션만 사용한 경우에도 기도 동작은 완벽하지 않지만, 움직임이 더 부드럽고 일관성이 있습니다. 마스크 기반 크로스 어텐션을 사용한 경우, 슈퍼히어로는 기도 동작을 성공적으로 수행하지만 손가락이 파랗게 변하는 등의 오류가 발생합니다. 마지막으로, 마스크 기반 크로스 어텐션과 셀프 어텐션을 모두 적용한 Through-The-Mask의 경우, 슈퍼히어로가 기도 동작을 완벽하게 수행합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Qualitative comparison of generated videos for each configuration of Through-The-Mask. The results highlight differences when applying masked cross-attention (With cross-attn), self-attention (With self-attn), both (Ours), or no masked attention layers (No mask attn). Without masked attention, the cartoon superhero fails to perform a prayer. With masked self-attention, the superhero also fails, but the movement appears smoother and more consistent. With masked cross-attention, the superhero successfully performs the prayer, though his fingers turn blue. When integrating the full masked attention mechanism, the superhero performs the action correctly.
> </details>



![](https://arxiv.org/html/2501.03059/x8.png)

> 🔼 그림 7은 중간 모션 표현으로 분할 마스크와 광학 흐름을 사용하여 생성된 비디오의 질적 비교를 보여줍니다. 첫 번째 행에는 입력 이미지와 텍스트가 표시되고, 두 번째 행에는 생성된 마스크가 표시되고, 세 번째 행에는 생성된 광학 흐름이 표시됩니다. 네 번째와 다섯 번째 행에는 생성된 비디오가 표시되며, 네 번째 행은 마스크 기반 모델을 사용하고 다섯 번째 행은 흐름 기반 모델을 사용합니다. 이 그림은 마스크 기반 모션 표현이 흐름 기반 모션 표현보다 더 나은 결과를 생성함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Qualitative comparison of generated videos using segmentation masks vs optical flow as an intermediate motion representation. The first row shows the input image and text, the second row displays the generated masks, and the third row presents the generated optical flow. The fourth and fifth rows show the generated videos, with the fourth row using our mask-based model and the fifth using our flow-based model.
> </details>



![](https://arxiv.org/html/2501.03059/x9.png)

> 🔼 본 그림은 논문에서 제안하는 Through-The-Mask 모델(DiT 기반)과 기준 모델인 TI2V(DiT 기반)을 사용하여 생성한 비디오를 정성적으로 비교한 결과를 보여줍니다. Through-The-Mask는 마스크 기반의 동작 궤적을 사용하여 여러 개체의 동작을 정확하게 애니메이션화하는 기능을 보여주며, TI2V보다 더 사실적이고 일관성 있는 비디오 생성 결과를 보여줍니다.  두 가지 예시를 통해 전차가 움직이는 장면과 앵무새가 나는 장면을 비교합니다. 각 장면에서 Through-The-Mask 모델은 TI2V 모델보다 더 자연스럽고 정확한 움직임을 생성하는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Qualitative comparison of video generations produced by Through-The-Mask (DiT-based) and the TI2V baseline (DiT-based).
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | FVD ↓ | CF ↑ | ViCLIP-T ↑ | ViCLIP-V ↑ | AD | Text | Motion | Quality |
|---|---|---|---|---|---|---|---|---|
| VideoCrafter [10] | 266.83 | 0.961 | 0.195 | 0.810 | 4.87 | 78.9 | 78.1 | 80.4 |
| DynamiCrafter [54] | 217.40 | 0.946 | 0.200 | 0.840 | 8.28 | 55.4 | 53.9 | 53.9 |
| Motion-I2V [43] | 286.42 | 0.928 | 0.209 | 0.746 | 7.46 | 81.2 | 82.8 | 83.5 |
| ConsistI2V [41] | 283.59 | 0.938 | 0.202 | 0.838 | 6.38 | 57.0 | 67.1 | 65.6 |
| TI2V (UNet) | 242.18 | 0.954 | 0.203 | 0.858 | 5.99 | 49.2 | 57.8 | 66.4 |
| Ours (UNet) | **196.23** | **0.962** | **0.210** | **0.865** | 5.69 | - | - | - |
| TI2V (DiT) | 212.23 | 0.937 | 0.206 | 0.789 | 9.00 | 61.7 | 63.2 | 67.1 |
| Ours (DiT) | **192.45** | **0.948** | **0.215** | **0.847** | 7.42 | - | - | - |{{< /table-caption >}}
> 🔼 표 2는 Image-Animation-Bench에 대한 실험 결과를 보여줍니다.  FVD(Fréchet Video Distance), CF(CLIPFrame), ViCLIP-T, ViCLIP-V, AD(Average Displacement) 와 같은 다양한 객관적인 지표들을 사용하여 비디오 생성 모델의 성능을 평가했습니다.  또한 사람의 평가를 통해 Through-The-Mask 모델이 다른 모델들보다 얼마나 선호되는지 그 비율을 제시하여 주관적인 평가 결과도 포함하고 있습니다. 즉, 비디오의 현실감, 시간적 일관성, 텍스트 충실도, 이미지 충실도 그리고 동작의 자연스러움까지 다양한 측면에서 Through-The-Mask 모델의 성능을 객관적, 주관적 지표를 통해 종합적으로 평가한 표입니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Image-Animation-Bench results. We report FVD, CLIPFrame (CF), ViCLIP-T, ViCLIP-V, and Average Displacement (AD), along with human ratings. Human evaluation shows the percentage of raters that prefer the results of Through-The-Mask.
> </details>

{{< table-caption >}}
| Config. | FVD↓ | CF↑ | ViCLIP-T↑ | ViCLIP-V↑ | AD |
|---|---|---|---|---|---| 
| TI2V (UNet) | 974.07 | 0.942 | 0.218 | 0.880 | 6.91 |
| no mask attn (UNet) | 972.25 | 0.962 | 0.214 | 0.880 | 4.99 |
| w. cross-attn (UNet) | 670.92 | 0.965 | 0.220 | 0.890 | 5.25 |
| w. self-attn (UNet) | 658.92 | 0.968 | 0.218 | 0.892 | 5.00 |
| Ours (UNet) | **648.59** | **0.968** | **0.220** | **0.892** | 5.15 |
| TI2V (DiT) | 1199.86 | 0.921 | 0.222 | 0.802 | 10.70 |
| no mask attn (DiT) | 1182.49 | 0.943 | 0.223 | 0.851 | 6.78 |
| w. cross-attn (DiT) | 1105.91 | 0.945 | 0.226 | 0.859 | 7.23 |
| w. self-attn (DiT) | 1152.38 | 0.946 | 0.223 | 0.855 | 7.01 |
| Ours (DiT) | **1082.23** | **0.947** | **0.226** | **0.861** | 7.35 |{{< /table-caption >}}
> 🔼 이 표는 논문의 4.3절 실험 결과(Ablation Study)의 일부분으로, SA-V-128 벤치마크를 사용하여 U-Net과 DiT 기반 모델 모두에서 서로 다른 어텐션 구성(Masked Attention)의 성능을 비교 분석한 결과를 보여줍니다.  각 모델의 FVD, CF, ViCLIP-T, ViCLIP-V, AD 지표 값을 제시하여 어텐션 메커니즘이 모델 성능에 미치는 영향을 정량적으로 평가합니다.  구체적으로는 마스크드 어텐션을 적용하지 않은 경우, 마스크드 크로스 어텐션만 적용한 경우, 마스크드 셀프 어텐션만 적용한 경우, 그리고 마스크드 크로스 및 셀프 어텐션을 모두 적용한 경우(THROUGH-THE-MASK)의 성능을 비교하여 어텐션 메커니즘의 효과를 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Ablation study results on the SA-V-128 benchmark comparing the performance of different attention configurations, in both U-Net and DiT-based models.
> </details>

{{< table-caption >}}
| Configuration | FVD↓ | CF↑ | ViCLIP-T↑ | ViCLIP-V↑ | AD |
|---|---|---|---|---|---| 
| w. OF | 1014.72 | 0.934 | 0.219 | 0.879 | 7.04 |
| w. Seg. | **648.59** | **0.968** | **0.220** | **0.892** | 5.15 |{{< /table-caption >}}
> 🔼 이 표는 이미지-비디오 생성을 위한 두 가지 다른 모션 경로 표현 방식(분할 마스크와 광학 흐름)의 성능을 비교 분석한 결과를 보여줍니다.  'w. Seg'는 분할 마스크 기반 모션 경로를 사용한 모델,  'w. OF'는 광학 흐름 기반 모션 경로를 사용한 모델을 나타냅니다. 표에는 각 모델의 FVD, CF, ViCLIP-T, ViCLIP-V, AD 값이 제시되어 있어, 두 가지 방식의 성능 차이를 정량적으로 비교 분석하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Ablation study comparing segmentation masks and optical flow as motion trajectory representation. w. Seg refers to models with segmentation-based motion trajectories, while w. OF denotes models with optical flow-based motion trajectories.
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
{{< /gallery >}}