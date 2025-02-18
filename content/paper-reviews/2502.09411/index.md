---
title: "ImageRAG: Dynamic Image Retrieval for Reference-Guided Image Generation"
summary: "ImageRAG: 이미지 검색으로 고품질 이미지 생성"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Generation", "🏢 Tel Aviv University",]
showSummary: true
date: 2025-02-13
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.09411 {{< /keyword >}}
{{< keyword icon="writer" >}} Rotem Shalev-Arkushin et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-17 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.09411" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.09411" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/imagerag-dynamic-image-retrieval-for" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

현존하는 이미지 생성 모델들은 희귀하거나 독특한 개념을 생성하는 데 어려움을 겪습니다. 이러한 문제를 해결하기 위해, 연구자들은 이미지 검색 및 증강 생성(RAG) 기법을 활용하는 다양한 방법들을 제시해 왔습니다. 하지만 이전 연구들은 대부분 RAG 특화 모델을 학습하는 방식을 사용하여 모델의 적용 범위를 제한하는 단점을 가지고 있습니다.

본 논문에서는 이러한 문제를 해결하기 위해, **기존의 이미지 조건화 모델을 활용**하여 텍스트 프롬프트에 따라 관련 이미지를 동적으로 검색하고, 검색된 이미지를 기반으로 이미지 생성 과정을 안내하는 새로운 방법인 **ImageRAG**를 제안합니다. ImageRAG는 기존 모델의 기능을 활용하기 때문에 **별도의 RAG 특화 학습이 필요 없으며**, 다양한 모델에 적용 가능하고 **희귀 개념 및 세밀한 개념의 이미지 생성 성능을 향상**시키는 효과를 보입니다.  실험 결과는 ImageRAG의 우수성을 입증하며, 이미지 생성 분야에 새로운 가능성을 제시합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} ImageRAG는 기존 이미지 생성 모델의 한계를 극복하고 희귀 개념이나 세밀한 개념의 이미지 생성 능력을 향상시키는 새로운 방법을 제시합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} ImageRAG는 추가적인 모델 훈련 없이도 기존 이미지 생성 모델에 적용 가능하며, 다양한 모델에 적용 가능합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 실험 결과를 통해 ImageRAG가 희귀 개념 및 세밀한 개념의 이미지 생성 성능을 크게 향상시킴을 보여줍니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **기존 이미지 생성 모델의 한계를 극복**하고 **희귀 개념이나 세밀한 개념의 이미지 생성 능력을 향상**시키는 방법을 제시하여, 이미지 생성 분야의 연구에 중요한 발전을 가져올 수 있습니다. 특히, **기존 모델에 추가적인 훈련 없이도 성능 향상**을 이룰 수 있다는 점에서 실용적인 측면에서도 가치가 있으며, **다양한 모델에 적용 가능**하다는 점 또한 강점입니다.  향후 연구에서는 제시된 방법을 다른 영역에 확장하고, 더욱 효율적이고 정교한 이미지 검색 및 활용 전략을 개발하는 데 활용될 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.09411/x2.png)

> 🔼 이 그림은 ImageRAG가 이미지 생성 모델의 기능을 어떻게 확장하는지 보여줍니다. 텍스트 프롬프트가 주어지면 ImageRAG는 관련 이미지를 동적으로 검색하여 기본 텍스트-이미지 모델(T2I)에 제공합니다. ImageRAG는 SDXL(A) 또는 OmniGen(B, C)과 같은 다양한 모델 및 텍스트(A, B) 또는 개인화(C)와 같은 다양한 제어 방식과 함께 작동합니다.  (A)는 SDXL 모델을 사용하여  '골든 리트리버와 요람' 이라는 텍스트 프롬프트에 대한 이미지 생성 과정을, (B)는 OmniGen 모델을 사용하여 '유치원에서 놀고 있는 레드판다 사진' 이라는 텍스트 프롬프트에 대한 이미지 생성 과정을, (C)는 OmniGen 모델을 사용하여  '할로윈 의상을 입고 있는 모습' 이라는 텍스트 프롬프트에 대한 개인화된 이미지 생성 과정을 보여줍니다. 각 과정에서 검색된 참조 이미지가 이미지 생성에 어떻게 영향을 미치는지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  Using references broadens the generation capabilities of image generation models. Given a text prompt, ImageRAG dynamically retrieves relevant images and provides them to a base text-to-image model (T2I). ImageRAG works with different models, such as SDXL (A) or OmniGen (B, C), and different controls, e.g. text (A, B) or personalization (C).
> </details>





{{< table-caption >}}
| Prompt | Reference | OmniGen | SDXL | ImageRAG (OmniGen) | ImageRAG (SDXL+IP) |
|---|---|---|---|---|---| 
| Chow | https://arxiv.org/html/2502.09411/chow_ref.png | https://arxiv.org/html/2502.09411/chow_o.png | https://arxiv.org/html/2502.09411/chow_sd.png | https://arxiv.org/html/2502.09411/chow_imagerag_o.png | https://arxiv.org/html/2502.09411/chow_imagerag_sd.png |
| Boston bull | https://arxiv.org/html/2502.09411/boston_bull_ref.png | https://arxiv.org/html/2502.09411/boston_bull_o.png | https://arxiv.org/html/2502.09411/boston_bull_sd.png | https://arxiv.org/html/2502.09411/boston_bull_imagerag_o.png | https://arxiv.org/html/2502.09411/boston_bull_imagerag_sd.png |
| Cab | https://arxiv.org/html/2502.09411/cab_ref.png | https://arxiv.org/html/2502.09411/cab_o.png | https://arxiv.org/html/2502.09411/cab_sd.png | https://arxiv.org/html/2502.09411/cab_imagerag_o.png | https://arxiv.org/html/2502.09411/cab_imagerag_sd.png |
| Academic gown | https://arxiv.org/html/2502.09411/academic_gown_ref.png | https://arxiv.org/html/2502.09411/academic_gown_o.png | https://arxiv.org/html/2502.09411/academic_gown_sd.png | https://arxiv.org/html/2502.09411/academic_gown_imagerag_o.png | https://arxiv.org/html/2502.09411/academic_gown_imagerag_sd.png |
| Unicycle | https://arxiv.org/html/2502.09411/unicycle_ref.png | https://arxiv.org/html/2502.09411/unicycle_o.png | https://arxiv.org/html/2502.09411/unicycle_sd.png | https://arxiv.org/html/2502.09411/unicycle_imagerag_o.png | https://arxiv.org/html/2502.09411/unicycle_imagerag_sd.png |
| Geococcyx | https://arxiv.org/html/2502.09411/geo_ref.png | https://arxiv.org/html/2502.09411/geo_o.png | https://arxiv.org/html/2502.09411/geo_sd.png | https://arxiv.org/html/2502.09411/geo_imagerag_o.png | https://arxiv.org/html/2502.09411/geo_imagerag_sd.png |
| Cyanocitta cristata | https://arxiv.org/html/2502.09411/iNat_20_ref.png | https://arxiv.org/html/2502.09411/iNat_20_o.png | https://arxiv.org/html/2502.09411/iNat_20_sd.png | https://arxiv.org/html/2502.09411/iNat_20_imagerag_o.png | https://arxiv.org/html/2502.09411/iNat_20_imagerag_sd.png |{{< /table-caption >}}

> 🔼 표 1은 다양한 텍스트-이미지 생성 모델을 사용하여 세밀한 이미지 생성을 비교 분석한 결과를 보여줍니다. ImageNet, iNaturalist, CUB, Aircraft 데이터셋의 각 클래스에 대해, 텍스트-이미지 유사도를 측정하는 CLIP, SigLIP, DINO 지표의 평균(표준오차 포함)을 제시합니다. 표의 중간 부분은 OmniGen 기반 모델, 하단 부분은 SDXL 기반 모델의 결과를 보여주며, 각 부분에서 가장 좋은 결과는 굵게 표시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparisons on fine-grained image generation with text-to-image models. We use the ImageNet (Deng et al., 2009), iNaturalist (Van Horn et al., 2018), CUB (Wah et al., 2011), and Aircraft (Maji et al., 2013) datasets. For each set, we report mean (±plus-or-minus\pm± standard error) CLIP, SigLIP text-to-image similarities, and DINO similarity between real and generated images. Middle rows feature OmniGen-based models, while the bottom features SDXL-based models. In each part, best results are bolded.
> </details>





### In-depth insights


#### ImageRAG Overview
ImageRAG은 기존 이미지 생성 모델의 한계를 극복하기 위해 **이미지 검색(Retrieval)** 기능을 활용하는 참신한 방법입니다. 단순히 텍스트 프롬프트만으로는 생성이 어려운 희귀하거나 세밀한 개념의 이미지를 생성할 때, **관련 이미지들을 동적으로 검색하여 추가적인 맥락 정보**로 활용합니다. 이를 통해 모델이 **희귀 개념이나 사용자 지정 개념**을 보다 정확하게 이해하고 생성할 수 있도록 돕습니다. 기존의 검색 기반 이미지 생성 방식과 달리, ImageRAG는 **추가적인 학습 없이 기존 이미지 조건화 모델의 기능을 활용**한다는 점이 특징입니다.  **다양한 모델에 적용 가능**하며, 개인화된 이미지 생성에도 효과적입니다.  **VLM(Vision-Language Model)**을 이용하여 프롬프트에 부족한 개념을 파악하고 적절한 이미지를 검색하는 전략은 효율성을 높입니다.  하지만 VLM의 성능에 의존적이며, 검색 데이터셋의 질에 따라 성능 차이가 발생할 수 있다는 점은 한계점으로 지적될 수 있습니다.

#### RAG for Images
이 논문은 이미지 생성 모델의 성능 향상을 위해 **검색 증강 생성(RAG)** 기법을 이미지에 적용한 내용을 다룹니다. 기존의 텍스트 기반 RAG와 달리, 이미지 RAG는 텍스트 프롬프트에 따라 관련 이미지를 동적으로 검색하여 이미지 생성 과정에 추가적인 정보를 제공합니다. **기존 접근 방식과의 차별점은 RAG를 위한 별도의 모델 훈련 없이 기존 이미지 조건화 모델의 기능을 활용한다는 점**입니다. 이는 모델의 적응성을 높이고 다양한 모델에 적용 가능하다는 장점을 제공합니다.  **희귀하거나 세밀한 개념을 생성하는 데 어려움을 겪는 기존 이미지 생성 모델의 한계를 극복하기 위한 효과적인 방법**으로 제시되며, 다양한 기본 모델에서 상당한 성능 향상을 보여줍니다.  특히, **동적으로 이미지를 선택하는 과정과 기존 모델에 RAG를 통합하는 방법**은 이 연구의 중요한 기여입니다.  이러한 접근 방식은 사용자 지정 개념 생성 및 개인화된 이미지 생성에도 효과적으로 적용될 수 있습니다.

#### Image Retrieval
본 논문에서 제시된 이미지 검색(Image Retrieval) 방법은 **기존 이미지 생성 모델의 한계를 극복하기 위한 핵심 전략**입니다. 희귀하거나 특이한 개념의 이미지를 생성하는 데 어려움을 겪는 기존 모델의 문제점을 해결하고자, **텍스트 프롬프트에 따라 관련 이미지를 동적으로 검색하여 이미지 생성 과정에 추가적인 정보를 제공**하는 방식입니다. 이는 단순히 유사 이미지를 찾는 것을 넘어, **결과 이미지의 질적 향상과 다양성 확보**에 기여하며, **기존 모델의 재학습 없이도 효과적으로 적용**할 수 있다는 점에서 큰 의의를 가집니다.  **Vision-Language Model(VLM)을 활용**하여 부족한 이미지 구성요소를 식별하고, 관련 이미지를 효율적으로 검색하는 전략은 **ImageRAG의 핵심적인 강점**입니다.  **다양한 이미지 생성 모델과의 호환성**을 통해 폭넓은 적용성을 보여주는 것 또한 중요한 특징입니다.  **이미지 검색의 효율성과 정확도**는 전체 시스템의 성능에 직결되므로, **검색 기법의 발전**은 앞으로도 중요한 연구 과제가 될 것입니다.

#### Method Limits
이 논문에서 제시된 방법의 한계는 **데이터 의존성, 검색 메커니즘의 정확도, 그리고 기저 모델의 성능**에 달려 있다는 점입니다.  **특히 희귀 개념 생성에 있어서,  적절한 참조 이미지를 검색하는 능력이 결과 품질에 큰 영향**을 미치며, 검색 데이터셋의 크기 및 질이 중요한 요소가 됩니다.  또한, 사용된 VLM(Vision-Language Model)의 정확도가 전체 시스템의 신뢰성을 좌우하며, **VLM이 항상 개념을 정확히 파악하거나 올바른 캡션을 생성하는 것은 아닙니다.** 따라서, **VLM의 오류는 이미지 검색 및 최종 생성 결과에 부정적 영향**을 줄 수 있습니다.  마지막으로, **기저 모델 자체의 한계** 또한 고려되어야 하는데,  모델이 특정 유형의 이미지를 생성하는 데 어려움을 겪는 경우, ImageRAG가 효과를 발휘하지 못할 수 있습니다.  따라서,  **ImageRAG의 성능은 여러 요소의 복합적인 영향**을 받으므로, 이러한 한계들을 인지하고, 개선 방향을 모색하는 것이 중요합니다.

#### Future Work
본 논문에서 제시된 ImageRAG는 기존 이미지 생성 모델의 성능을 향상시키는 데 효과적임을 보여주었지만, **향후 연구를 통해 더욱 개선될 여지가 많습니다.**  **다양한 크기와 종류의 데이터셋에 대한 ImageRAG의 성능 평가**는 필수적이며, 이를 통해 모델의 일반화 능력을 향상시킬 수 있습니다. 또한, **현재 사용 중인 VLM의 한계를 극복하기 위한 새로운 방법론**을 모색해야 합니다.  VLM이 항상 정확하게 missing concept을 식별하는 것은 아니므로, 더욱 robust한 missing concept 식별 기법이 필요합니다.  더불어, **다양한 이미지 검색 기법과의 비교 분석**을 통해 ImageRAG의 효율성을 높이고,  **다양한 이미지 생성 모델에 대한 적용성을 확장**하는 연구가 필요합니다. 마지막으로, **윤리적인 문제점에 대한 심도있는 고찰**과 이를 해결하기 위한 방안을 제시해야 합니다. 예를 들어,  ImageRAG를 악용하여 가짜 이미지를 생성하는 것을 방지하기 위한 기술적, 제도적 장치 마련이 중요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.09411/x3.png)

> 🔼 이 그림은 텍스트-이미지 생성 모델이 프롬프트의 의미를 이해하지 못할 때 발생하는 '환각' 현상을 보여줍니다. 왼쪽에는 모델이 프롬프트와 관련없는 이미지를 생성하는 예시가 나와있고, 가운데에는 연구팀이 제안한 방법(ImageRAG)을 사용하여 관련 이미지를 검색하고 활용하여 생성 과정을 안내하는 과정이 나와있습니다. 오른쪽에는 ImageRAG를 적용하여 프롬프트에 적합한 이미지를 생성한 결과가 보여집니다.
> <details>
> <summary>read the caption</summary>
> Figure 2:  Hallucinations. When models do not know the meaning of a prompt, they may “hallucinate” and generate unrelated images (left). By applying our method to retrieve and utilize relevant references (mid), the base models can generate appropriate images (right).
> </details>



![](https://arxiv.org/html/2502.09411/x4.png)

> 🔼 그림 3은 ImageRAG 방법의 개념을 보여줍니다. 위쪽 부분은 ImageRAG의 전체적인 흐름을 간략하게 나타냅니다. 텍스트 프롬프트(p)를 입력받아 텍스트-이미지 생성 모델(T2I)을 사용하여 초기 이미지를 생성합니다.  그런 다음, 생성된 이미지와 프롬프트가 일치하는지 확인하기 위해 Vision-Language Model(VLM)을 사용합니다. 일치하지 않는 경우, VLM은 누락된 개념들을 파악하고, 각 개념에 맞는 이미지를 검색할 수 있는 캡션(cj)을 생성합니다.  이렇게 생성된 캡션을 이용해 외부 데이터베이스에서 관련 이미지(ij)를 검색하고, 이 이미지들을 T2I 모델에 추가적인 참고 자료로 제공하여 이미지 생성 과정을 안내합니다.  아래쪽 부분은 이러한 캡션 생성 과정을 자세히 보여줍니다. 초기 이미지와 프롬프트를 VLM에 입력하여 일치 여부를 판단하고, 일치하지 않으면 누락된 개념들을 식별하여 적절한 이미지를 검색할 수 있는 캡션을 생성하는 과정을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3:  Top: a high-level overview of our method. Given a text prompt <⁢p⁢>𝑝\mathord{<}p\mathord{>}< italic_p >, we generate an initial image using a text-to-image (T2I) model. Then, we generate retrieval-captions <⁢cj⁢>subscript𝑐𝑗\mathord{<}c_{j}\mathord{>}< italic_c start_POSTSUBSCRIPT italic_j end_POSTSUBSCRIPT >, retrieve images from an external database for each caption <⁢ij⁢>subscript𝑖𝑗\mathord{<}i_{j}\mathord{>}< italic_i start_POSTSUBSCRIPT italic_j end_POSTSUBSCRIPT >, and use them as references to the model for better generation. Bottom: the retrieval-caption generation block. We use a VLM to decide if the initial image matches the given prompt. If not, we ask it to list the missing concepts, and to create a caption that could be used to retrieve appropriate examples for each of these missing concepts.
> </details>



![](https://arxiv.org/html/2502.09411/x5.png)

> 🔼 그림 4는 ImageRAG가 개인화된 이미지 생성 방법과 병행하여 사용될 때 그 성능을 향상시키는 예시를 보여줍니다.  OmniGen과 같은 모델은 기존 이미지를 기반으로 특정 객체의 이미지를 생성할 수 있지만, 특정 개념을 생성하는 데는 어려움을 겪습니다.  ImageRAG는 이러한 문제를 해결하기 위해 관련 이미지를 검색하여 추가 정보로 제공함으로써,  OmniGen이 원하는 개념의 이미지를 생성할 수 있도록 돕습니다. 그림에서는 특정 고양이 사진을 기반으로,  ImageRAG를 통해 다양한 상황(머그컵에 그려진 고양이, 레고 고양이, 고양이가 수업을 하는 장면 등)에서 고양이 이미지를 생성하는 예시를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Personalized generation example. ImageRAG can work in parallel with personalization methods and enhance their capabilities. For example, although OmniGen can generate images of a subject based on an image, it struggles to generate some concepts. Using references retrieved by our method, it can generate the required result.
> </details>



![](https://arxiv.org/html/2502.09411/x6.png)

> 🔼 그림 5는 ImageNet과 Aircraft 데이터셋에서 검색 데이터셋 크기와 CLIP 점수 간의 관계를 보여줍니다. 점선은 기본 모델의 점수를 나타냅니다. 비교적 작고 전문화되지 않은 검색 데이터셋이라도 결과를 향상시킬 수 있습니다. 데이터가 많을수록 점수가 더 높아집니다. 하지만 작은 데이터셋에는 관련 검색 예시가 포함되지 않을 수 있으며, 특히 강력한 모델의 경우 결과에 해를 끼칠 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Retrieval dataset size vs. CLIP score on ImageNet (left) and Aircraft (right). Dashed lines represent the scores of the base models. Even relatively small, unspecialized retrieval sets can already improve results. More data leads to further increased scores. However, small sets may not contain relevant retrieval examples, and their use may harm results, particularly for stronger models.
> </details>



![](https://arxiv.org/html/2502.09411/x7.png)

> 🔼 본 그림은 사용자 연구 결과를 보여줍니다. 사용자들은 제시된 프롬프트에 대한 텍스트 정렬, 시각적 품질 및 전반적인 선호도 측면에서 ImageRAG 방법을 다른 방법들과 비교 평가했습니다. 각 기준에 따라 ImageRAG 방법이 다른 방법들보다 더 높은 선호도를 얻었음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: User study results. Users preference percentage of our method compared to other methods in terms of text alignment, visual quality, and overall preference.
> </details>



![](https://arxiv.org/html/2502.09411/x8.png)

> 🔼 그림 7은 ImageRAG, OmniGen, SDXL 세 가지 이미지 생성 모델을 사용하여 드문 개념의 이미지를 생성한 결과를 비교 분석한 것입니다. ImageNet, CUB, iNaturalist 데이터셋의 드문 개념(Chow Chow 강아지, Boston Bull 강아지, Geococcyx 등)을 사용하여 실험하였습니다.  왼쪽 열은 ImageRAG가 각 프롬프트에 대해 검색한 참조 이미지를 보여줍니다.  OmniGen과 SDXL 모델은 드문 개념을 생성하는 데 어려움을 겪어, Boston Bull의 경우 소나 젖소와 같은 유사한 개념을 생성하거나 Chow Chow나 Geococcyx처럼 완전히 관련 없는 이미지를 생성하는 경우가 있었습니다. 하지만 ImageRAG를 사용하면 두 모델 모두 정확한 개념의 이미지를 생성할 수 있었습니다. 이 그림은 ImageRAG가 이미지 검색 기능을 통해 이미지 생성 모델의 드문 개념 생성 능력을 향상시키는 데 효과적임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Qualitative comparisons: rare concept generation. Examples from ImageNet (Deng et al., 2009), CUB (Wah et al., 2011) and iNaturalist (Van Horn et al., 2018). The left-most image column is the retrieved reference using ImageRAG for each prompt. OmniGen and SDXL both struggle with the uncommon concepts, sometimes generating similar concepts such as a bull or a cow instead of the dog breed “Boston bull”, while in other times, they generate completely unrelated images, as in the case of “Chow”, or “Geococcyx”. When using ImageRAG both models generate the correct concept.
> </details>



![](https://arxiv.org/html/2502.09411/x9.png)

> 🔼 그림 8은 이미지 생성을 위해 검색을 사용하는 ImageRAG와 다른 방법들을 비교한 것입니다. 다른 방법들의 프롬프트와 결과는 해당 논문에서 가져왔습니다. 비교 대상 방법은 RDM(Blattmann et al., 2022), Re-Imagen(Chen et al., 2022), KNN-Diffusion(Sheynin et al., 2022)입니다.  각 방법은 다양한 프롬프트에 대해 생성된 이미지를 보여주며, ImageRAG의 성능을 다른 방법들과 비교하여 시각적으로 보여줍니다.  이 그림을 통해 ImageRAG가 복잡하거나 특이한 개념을 생성하는 데 있어 다른 방법들보다 얼마나 효과적인지를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Comparisons between ImageRAG and different methods using retrieval for generation. Prompts and results of all other methods are taken from their papers. The methods we compared to are RDM (Blattmann et al., 2022), Re-Imagen (Chen et al., 2022), and KNN-Diffusion (Sheynin et al., 2022).
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