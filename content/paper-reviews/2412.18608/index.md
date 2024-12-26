---
title: "PartGen: Part-level 3D Generation and Reconstruction with Multi-View Diffusion Models"
summary: "PartGen: 다중 뷰 확산 모델을 이용, 텍스트, 이미지, 기존 3D 객체로부터 의미있는 부분으로 구성된 고품질 3D 객체 생성 및 재구성."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "3D Vision", "🏢 Meta AI",]
showSummary: true
date: 2024-12-24
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.18608 {{< /keyword >}}
{{< keyword icon="writer" >}} Minghao Chen et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-25 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.18608" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.18608" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/partgen-part-level-3d-generation-and" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

3D 객체 생성 및 스캐닝 기술이 발전했지만, 생성된 3D 자산은 단일 융합 표현 방식으로 구조적 정보가 부족하여 활용에 제약이 있었습니다. 특히 **의미있는 부분들로 구성되어야 하는 애플리케이션 (비디오 게임, 로보틱스)에서는 단일 객체 표현이 불리**하며, **부분별 수정 및 편집이 어렵다는 문제**가 있습니다.  PartGen은 이러한 문제 해결을 위해 **다중 뷰 확산 모델 기반의 새로운 파이프라인**을 제시합니다. 



PartGen은 **다중 뷰 확산 모델을 사용하여 3D 객체를 여러 부분으로 나누고, 각 부분의 가려진 영역을 완성하여 3D로 재구성**합니다. 이때 **다른 부분들과의 상호 작용을 고려**하여 부분들이 자연스럽게 결합되도록 합니다. PartGen은 **텍스트, 이미지, 기존 3D 객체 등 다양한 입력**을 지원하며, **3D 부분 편집 기능**도 제공합니다. 실험 결과를 통해 PartGen이 기존 방법보다 성능이 우수하며 다양한 애플리케이션에서 활용 가능성을 보여줍니다. 

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 다중 뷰 확산 모델을 이용하여 3D 객체를 의미있는 부분으로 분할하고, 각 부분을 완성하여 3D로 재구성하는 새로운 방법 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 텍스트, 이미지, 기존 3D 객체 등 다양한 입력 모달리티를 지원하며, 3D 부분 편집 등 다양한 하류 애플리케이션에 활용 가능 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 기존의 부분 분할 및 추출 기법 대비 성능 향상 및 다양한 실험 결과를 통해 성능 검증 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
이 논문은 **다양한 모달리티(텍스트, 이미지, 3D 객체)로부터 의미있는 부분들로 구성된 3D 객체를 생성하고 재구성하는 새로운 방법론**을 제시하여 3D 모델링 및 생성 분야에 중요한 발전을 가져올 수 있습니다. **다중 뷰 확산 모델을 이용한 부분 분할 및 완성 기법은 기존의 단일 융합 표현 방식의 한계를 극복하고**, 3D 객체의 구조적 이해 및 편집 기능을 향상시킵니다. 또한, **다양한 하류 애플리케이션(3D 부분 편집 등)에 활용 가능성**을 보여주어 연구의 파급 효과를 높입니다. 이러한 연구는 **3D 생성 기술의 실용성 및 창의성을 높여** 다양한 산업 분야에 기여할 수 있습니다. 

------
#### Visual Insights



![](https://arxiv.org/html/2412.18608/x2.png)

> 🔼 PartGen은 사람과 유사하게 구성적인 3D 객체를 생성하는 파이프라인입니다. 텍스트, 이미지 또는 기존의 비구조적 3D 객체에서 시작하여 작동합니다. PartGen은 가능성 있는 부분들을 자동으로 식별하는 다중 뷰 확산 모델과 이러한 부분들을 3D로 완성하고 재구성하는 다른 모델로 구성됩니다. 또한 PartGen은 텍스트 지침을 기반으로 3D 부분 편집을 가능하게 하여 3D 객체 생성의 유연성과 제어 기능을 향상시킵니다. 그림은 PartGen의 텍스트-3D, 이미지-3D 및 3D 객체 분해 기능을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  We introduce PartGen, a pipeline that generates compositional 3D objects similar to a human artist. It can start from text, an image, or an existing, unstructured 3D object. It consists of a multi-view diffusion model that identifies plausible parts automatically and another that completes and reconstructs them in 3D, accounting for their context, i.e., the other parts, to ensure that they fit together correctly. Additionally, PartGen enables 3D part editing based on text instructions, enhancing flexibility and control in 3D object creation.
> </details>





{{< table-caption >}}
| Method | Automatic mAP<sub>50</sub>↑ | Automatic mAP<sub>75</sub>↑ | Seeded mAP<sub>50</sub>↑ | Seeded mAP<sub>75</sub>↑ |
|---|---|---|---|---|
| Part123 [44] | 11.5 | 7.4 | 10.3 | 6.5 |
| SAM2<sup>†</sup> [70] | 20.3 | 11.8 | 24.6 | 13.1 |
| SAM2* [70] | 37.4 | 27.0 | 44.2 | 30.1 |
| SAM2 [70] | 35.3 | 23.4 | 41.4 | 27.4 |
| PartGen (1 sample) | 45.2 | 32.9 | 44.9 | 33.5 |
| PartGen (5 samples) | 54.2 | 33.9 | 51.3 | 32.9 |
| PartGen (10 samples) | 59.3 | 38.5 | 53.7 | 35.4 |{{< /table-caption >}}

> 🔼 표 1은 PartGen 모델의 핵심 구성 요소 중 하나인 3D 객체 분할 성능을 평가한 결과를 보여줍니다.  다양한 방법(SAM2*, SAM2†, Part123, PartGen)을 사용하여 3D 객체를 의미있는 부분들로 나누는 작업의 정확도를 평가했습니다. SAM2*는 PartGen의 데이터로 미세 조정되었고, SAM2†는 다중 뷰 분할을 위해 미세 조정되었습니다.  mAP(평균 정밀도) 지표를 사용하여 자동 및 시드 기반 분할 방식의 성능을 비교 분석하여 PartGen 모델의 우수성을 보여줍니다.  자동 분할은 모델이 독자적으로 객체를 분할하는 방식이고, 시드 분할은 사용자가 초기 지점을 지정하여 분할하는 방식입니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Segmentation results. SAM2∗superscriptSAM2\text{SAM2}^{*}SAM2 start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT is fine-tuned our data and SAM2†superscriptSAM2†\text{SAM2}^{{\dagger}}SAM2 start_POSTSUPERSCRIPT † end_POSTSUPERSCRIPT is fine-tuned for multi-view segmentation.
> </details>





### In-depth insights


#### Multi-view Diffusion
본 논문에서 제시된 멀티뷰 확산 모델은 **3D 객체를 다양한 각도에서 본 여러 이미지를 사용하여 3D 모델을 생성하고 재구성**하는 핵심적인 역할을 합니다. 단순히 하나의 관점만 고려하는 것이 아니라, **여러 시점의 정보를 통합**함으로써 3D 객체의 형태 및 텍스처를 더욱 정확하고 완성도 있게 표현할 수 있습니다. 특히, 부분적으로 가려진 영역을 복원하거나, 텍스트 또는 이미지 입력으로부터 3D 객체를 생성하는 과정에서 **결손된 부분을 추론**하는 데 효과적입니다.  **각 부분의 맥락을 고려**하여 일관성 있는 결과물을 생성하는 것은 멀티뷰 확산 모델의 중요한 특징입니다. 이를 통해, 인간의 예술가가 작품을 창조하는 과정과 유사하게, 3D 객체를 구성하는 **의미 있는 부분들을 식별하고 재구성**하는 것이 가능해집니다.  **확산 모델의 확률적 특성**을 활용하여 다양한 가능성을 탐색하고, 최적의 결과물을 얻는 데 기여합니다.  결론적으로, 멀티뷰 확산 모델은 3D 객체 생성 및 재구성 과정의 정확성, 완성도, 그리고 창의성을 높이는 데 중요한 역할을 합니다.

#### Part Segmentation
본 논문에서 제시된 파트 분할 방법은 **다중 뷰 확산 모델**을 기반으로 하여, 기존의 단일 뷰 기반 방법의 한계를 극복하고자 합니다. **다양한 관점의 이미지**를 활용하여 3D 객체를 파트 단위로 분할함으로써, **보다 정확하고 일관성 있는 분할 결과**를 얻을 수 있습니다. 또한, **확률적 생성 모델**을 활용하여 **여러 가지 가능한 분할 결과**를 생성하고, 이 중에서 가장 적절한 결과를 선택하는 방식을 통해 **모호성을 해결**하고자 합니다. 이를 위해 **다중 뷰 이미지 생성기**와 **파트 분할 네트워크**를 학습시키고, **세분화된 파트 분할 결과**를 얻어냅니다.  **문맥 정보**를 고려하여 부분적으로 가려진 파트도 정확하게 분할할 수 있도록 하였으며, 이는 3D 객체의 완전한 복원에 중요한 역할을 합니다. 뿐만 아니라, **다양한 입력 모드** (텍스트, 이미지, 3D 모델)에 대한 파트 분할이 가능하도록 설계되어 있어 **범용성이 높다**는 장점을 가집니다.

#### 3D Part Completion
본 논문에서 제시하는 3D 파트 완성(3D Part Completion) 기법은 **부분적으로 가려지거나 보이지 않는 3D 객체의 파트를 완성하는 데 중점**을 둡니다. 기존의 3D 재구성 모델이 가시적인 부분만을 다루는 것과 달리, **멀티-뷰 확산 모델을 활용하여 가려진 부분을 추론하고 완성**합니다. 이는 단순히 가려진 영역을 채우는 것이 아니라, **전체 객체의 맥락을 고려하여 파트들이 조화롭게 통합될 수 있도록 설계**되었습니다.  **특히, 완성 과정에서 발생하는 모호성을 확률적 확산 모델을 통해 해결**하려는 시도가 돋보입니다.  이는 다양한 해석이 가능한 파트 완성 작업의 특징을 잘 반영한 접근 방식입니다.  이러한 **확률적 완성은 다양한 가능성을 제공**하며, **사용자의 편의성과 3D 객체 생성의 유연성을 높일 수** 있습니다.  또한, **가려진 부분뿐만 아니라, 완전히 보이지 않는 부분도 추론하여 생성**할 수 있는 강점을 지니고 있습니다.  이러한 기능은 **3D 객체 편집 및 조작과 같은 다양한 응용 분야**에 큰 기여를 할 것으로 예상됩니다.

#### Compositional 3D
본 논문은 **합성적인 3D 객체 생성 및 재구성**에 중점을 두고 있습니다. 기존의 단일 표현 방식(implicit neural field, mesh 등)과 달리, **의미있는 부분들로 객체를 분해하여 생성 및 편집**하는 새로운 파이프라인을 제시합니다. 이는 다중 뷰 확산 모델을 활용하여, 먼저 객체의 부분들을 식별하고, 이후 각 부분을 3D로 완성하고 재구성하는 방식입니다. 특히, **가려진 부분에 대한 완성 및 다른 부분들과의 조화**에 초점을 맞춰, 보다 현실적이고 자연스러운 합성 객체를 생성합니다. 텍스트, 이미지, 기존의 비정형 3D 객체 등 다양한 입력을 통해 **유연성과 제어성**을 확보하며, 텍스트 기반 3D 부분 편집 기능까지 제공하여 활용성을 높였습니다. 이러한 합성적 3D 접근 방식은 **다양한 응용 분야** (비디오 게임, 로보틱스, 엠보디드 AI 등)에 유용하며, 향후 연구를 통해 **장면 수준 생성**으로까지 확장될 가능성을 보여줍니다.

#### PartGen Limitations
PartGen은 여러 측면에서 뛰어난 성과를 보이지만, 몇 가지 제한점 또한 가지고 있습니다. **데이터셋의 품질과 다양성에 대한 의존도가 높다**는 점이 가장 큰 한계입니다. 아티스트가 제작한 3D 자산에 의존하는 학습 방식은 데이터셋에 존재하는 편향을 그대로 반영할 수 있으며, 이는 결과물의 다양성과 일반화 능력에 제약을 초래합니다. 또한, **복잡한 장면이나 객체를 처리하는 데 어려움**을 보일 수 있습니다. 밀집된 배경이나 복잡한 형태의 객체는 정확한 파트 분할 및 재구성에 어려움을 야기하며, 이는 결과물의 정확도와 품질 저하로 이어집니다. **파트 수의 제한** 또한 고려해야 할 부분입니다. 현재 구현에서는 10개 이하의 파트로 구성된 객체에만 효과적으로 적용되며, 더 많은 파트로 구성된 객체는 파트 병합이나 분할 문제 발생 가능성이 높습니다. 마지막으로, **윤리적 문제**도 고려해야 합니다. 아티스트가 제작한 데이터를 사용하는 만큼, 결과물에 편향이나 부적절한 내용이 포함될 가능성이 있으며, 이에 대한 충분한 고려와 해결책 마련이 필요합니다. 따라서, PartGen의 실제 활용을 위해서는 데이터셋 확장 및 편향 완화 노력, 복잡한 객체 처리 능력 개선, 파트 수 제한 해결, 윤리적 문제 해결 등의 추가적인 연구가 필요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.18608/x3.png)

> 🔼 그림 2는 PartGen의 개요를 보여줍니다. PartGen은 텍스트, 단일 이미지 또는 기존 3D 객체를 입력받아 객체의 초기 그리드 뷰를 생성합니다. 이 뷰는 확산 기반 분할 네트워크에 의해 처리되어 다중 뷰 일관성 있는 부분 분할을 달성합니다. 다음으로, 분할된 부분과 상황 정보는 다중 뷰 부분 완성 네트워크에 입력되어 각 부분의 완전히 완성된 뷰를 생성합니다. 마지막으로, 사전 훈련된 재구성 모델이 3D 부분을 생성합니다.  간단히 말해, PartGen은 다중 뷰 확산 모델을 사용하여 3D 객체를 의미있는 부분으로 분할하고 재구성하는 파이프라인입니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Overview of PartGen. Our method begins with text, single images, or existing 3D objects to obtain an initial grid view of the object. This view is then processed by a diffusion-based segmentation network to achieve multi-view consistent part segmentation. Next, the segmented parts, along with contextual information, are input into a multi-view part completion network to generate a fully completed view of each part. Finally, a pre-trained reconstruction model generates the 3D parts.
> </details>



![](https://arxiv.org/html/2412.18608/x4.png)

> 🔼 그림 3은 논문에서 사용된 훈련 데이터셋을 보여줍니다. 아티스트가 제작한 3D 오브젝트들을 부품별로 분해하여 구성한 데이터셋으로, 아티스트의 디자인 의도에 따라 자연스럽게 부품 단위로 분해되어 있습니다. 각 부품은 의미 있는 개별 요소이며, 이러한 부품들의 조합으로 전체 3D 오브젝트를 구성합니다. 이 데이터셋은 PartGen 모델을 훈련하는 데 사용되었습니다. 그림에는 여러 3D 오브젝트와 해당 오브젝트의 부품들을 보여주는 예시들이 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Training data. We obtain a dataset of 3D objects decomposed into parts from assets created by artists. These come ‘naturally’ decomposed into parts according to the artist’s design.
> </details>



![](https://arxiv.org/html/2412.18608/x5.png)

> 🔼 그림 4는 제안된 PartGen 방법을 여러 번 실행하여 얻은 자동 다중 뷰 파트 분할의 예시를 보여줍니다. 각 실행마다 다른 분할 결과가 생성되며, 이는 사람의 의도를 다양하게 반영합니다. 즉, 같은 물체라도 사람마다 어떤 부분을 파트로 나누는지에 대한 기준이 다를 수 있고, PartGen은 이러한 다양성을 포괄하는 여러 가지 분할 결과를 생성할 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Examples of automatic multi-view part segmentations. By running our method several times, we obtain different segmentations, covering the space of artist intents.
> </details>



![](https://arxiv.org/html/2412.18608/x6.png)

> 🔼 그림 5는 PartGen의 부분 완성 기능의 정성적 결과를 보여줍니다. 파란색 테두리가 있는 이미지는 입력 이미지이며, 알고리즘은 여러 번 실행될 때마다 다양한 타당한 결과를 생성합니다. 비어있는 부분이 주어지더라도 PartGen은 모래나 바퀴와 같은 내부 구조를 생성하려고 시도합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Qualitative results of part completion. The images with blue borders are the inputs. Our algorithm produces various plausible outputs across different runs. Even if given an empty part, PartGen attempts to generate internal structures inside the object, such as sand or inner wheels.
> </details>



![](https://arxiv.org/html/2412.18608/x7.png)

> 🔼 그림 6은 PartGen의 다양한 활용 사례를 보여줍니다. PartGen은 텍스트 또는 이미지를 입력받아 의미 있고 사실적인 부분으로 구성된 3D 개체를 생성하거나 재구성할 수 있습니다. (a)에서는 텍스트 기반 3D 생성, (b)에서는 이미지 기반 3D 생성, (c)에서는 기존 3D 개체의 부분 분해를 보여줍니다. 각각의 경우 PartGen이 의미있는 부분을 식별하고, 이를 통합하여 완전한 3D 개체를 생성하거나 재구성하는 과정을 보여줍니다. 이는 다양한 응용 분야에 유용하게 활용될 수 있음을 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Examples of applications. PartGen can effectively generate or reconstruct 3D objects with meaningful and realistic parts in different scenarios: a) Part-aware text-to-3D generation; b) Part-aware image-to-3D generation; c) 3D decomposition.
> </details>



![](https://arxiv.org/html/2412.18608/x8.png)

> 🔼 그림 7은 PartGen 모델을 사용한 3D 객체 부분 편집 기능을 보여줍니다. 사용자가 텍스트 프롬프트를 통해 3D 객체의 개별 부분(예: 모자, 셔츠)의 모양과 외관을 변경할 수 있음을 보여줍니다.  각 이미지는 원본 객체, 특정 부분에 대한 텍스트 프롬프트, 그리고 편집된 결과를 보여줍니다. 이는 사용자가 PartGen을 통해 3D 모델의 세부적인 부분까지 제어하고 수정할 수 있음을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: 3D part editing. We can edit the appearance and shape of the 3D objects with text prompt.
> </details>



![](https://arxiv.org/html/2412.18608/x9.png)

> 🔼 그림 8은 PartGen의 3D 파트 편집 기능과 파트 캡션 생성 과정을 보여줍니다. 상단은 편집 네트워크의 학습 예시로, 마스크, 마스크 처리된 이미지, 텍스트 설명이 확산 네트워크에 입력되어 텍스트에 따른 파트가 채워지는 과정을 보여줍니다. 하단은 파트 캡션 생성 파이프라인의 입력 예시로, 큰 비전-언어 모델(LVLM)이 특정 파트를 식별하고 주석을 달도록 돕기 위해 빨간색 원과 강조 표시가 사용되는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: 3D part editing and captioning examples. The top section illustrates training examples for the editing network, where a mask, a masked image, and text instructions are provided as conditioning to the diffusion network, which fills in the part based on the given textual input. The bottom section demonstrates the input for the part captioning pipeline. Here, a red circle and highlights are used to help the large vision-language model (LVLM) identify and annotate the specific part.
> </details>



![](https://arxiv.org/html/2412.18608/x10.png)

> 🔼 그림 9는 다양한 방법들의 재현율 곡선을 보여줍니다.  x축은 상위 k개의 예측 결과를 나타내고, y축은 특정 IoU 임계값을 초과하는 정답 부분의 비율(재현율)을 나타냅니다.  이 그림은 PartGen 방법이 SAM2 및 그 변형 방법들보다 더 나은 성능을 달성했음을 보여줍니다.  즉, PartGen은 더 적은 수의 예측 결과에서도 더 높은 정확도로 물체의 부분을 식별합니다.  여러 IoU 임계값 (0.75, 0.5)에 대한 결과를 보여주어 방법의 성능을 다각적으로 비교 분석합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Recall curve of different methods. Our method achieve better performance comparing with SAM2 and its variants.
> </details>



![](https://arxiv.org/html/2412.18608/x11.png)

> 🔼 그림 10은 PartGen이 다양한 모달리티(텍스트, 이미지, 기존 3D 오브젝트)를 처리하여 개별적인 부품으로 구성된 고품질 3D 오브젝트를 생성하거나 재구성할 수 있음을 보여주는 추가적인 예시들을 보여줍니다. 각 예시는 입력과 PartGen에 의해 생성 또는 재구성된 3D 오브젝트와 그 구성 부품들을 보여줍니다. 이를 통해 PartGen의 다양한 활용 사례와 강력한 성능을 더욱 자세히 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: More examples. Additional examples illustrate that PartGen can process various modalities and effectively generate or reconstruct 3D objects with distinct parts.
> </details>



![](https://arxiv.org/html/2412.18608/x12.png)

> 🔼 그림 11은 PartGen 파이프라인의 결과를 반복적으로 부품을 추가하고 결합하여 3D 오브젝트를 생성하는 과정을 보여줍니다. 사용자는 하나의 부품부터 시작하여, 원하는 만큼 부품을 순차적으로 추가하고, PartGen이 각 부품을 생성하고 이전 부품들과 일관되게 통합하도록 합니다. 이를 통해 사용자는 보다 자유롭고 직관적으로 복잡한 3D 오브젝트를 디자인하고 제작할 수 있습니다.  이 과정은 부품 하나하나의 정확도와 전체 모델의 일관성을 유지하는 PartGen의 강점을 잘 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Iteratively adding parts. We show that users can iteratively add parts and combine the results of PartGen pipeline.
> </details>



![](https://arxiv.org/html/2412.18608/x13.png)

> 🔼 그림 12는 PartGen 모델의 실패 사례를 보여줍니다. (a)는 멀티뷰 그리드 생성 실패로, 생성된 뷰들이 3D 일관성이 부족한 경우입니다. (b)는 의미상 구분되는 파트들이 잘못 묶이는 분할 실패 사례입니다. (c)는 입력 객체의 복잡한 형상으로 인해 깊이 맵에 부정확성이 발생하는 재구성 모델 실패 사례입니다.  각각의 실패 유형은 모델의 제한점과 개선 방향을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Failure Cases. (a) Multi-view grid generation failure, where the generated views lack 3D consistency. (b) Segmentation failure, where semantically distinct parts are incorrectly grouped together. (c) Reconstruction model failure, where the complex geometry of the input leads to inaccuracies in the depth map.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
<table class="ltx_tabular ltx_guessed_headers ltx_align_middle" id="S4.T2.16.16">
<thead class="ltx_thead">
<tr class="ltx_tr" id="S4.T2.2.2.2">
<th class="ltx_td ltx_th ltx_th_row ltx_border_tt" id="S4.T2.2.2.2.3" style="padding-left:4.0pt;padding-right:4.0pt;"></th>
<th class="ltx_td ltx_th ltx_th_column ltx_border_tt" id="S4.T2.2.2.2.4" style="padding-left:4.0pt;padding-right:4.0pt;"></th>
<th class="ltx_td ltx_th ltx_th_column ltx_border_tt" id="S4.T2.2.2.2.5" style="padding-left:4.0pt;padding-right:4.0pt;"></th>
<th class="ltx_td ltx_th ltx_th_column ltx_border_tt" id="S4.T2.2.2.2.6" style="padding-left:4.0pt;padding-right:4.0pt;"></th>
<th class="ltx_td ltx_align_center ltx_th ltx_th_column ltx_border_tt" colspan="3" id="S4.T2.1.1.1.1" style="padding-left:4.0pt;padding-right:4.0pt;"><span class="ltx_text ltx_font_bold" id="S4.T2.1.1.1.1.1">View completion <math alttext="J" class="ltx_Math" display="inline" id="S4.T2.1.1.1.1.1.m1.1"><semantics id="S4.T2.1.1.1.1.1.m1.1a"><mi id="S4.T2.1.1.1.1.1.m1.1.1" xref="S4.T2.1.1.1.1.1.m1.1.1.cmml">J</mi><annotation-xml encoding="MathML-Content" id="S4.T2.1.1.1.1.1.m1.1b"><ci id="S4.T2.1.1.1.1.1.m1.1.1.cmml" xref="S4.T2.1.1.1.1.1.m1.1.1">𝐽</ci></annotation-xml><annotation encoding="application/x-tex" id="S4.T2.1.1.1.1.1.m1.1c">J</annotation><annotation encoding="application/x-llamapun" id="S4.T2.1.1.1.1.1.m1.1d">italic_J</annotation></semantics></math></span></th>
<th class="ltx_td ltx_align_center ltx_th ltx_th_column ltx_border_tt" colspan="3" id="S4.T2.2.2.2.2" style="padding-left:4.0pt;padding-right:4.0pt;"><span class="ltx_text ltx_font_bold" id="S4.T2.2.2.2.2.1">3D reconstruction <math alttext="\mathbf{S}" class="ltx_Math" display="inline" id="S4.T2.2.2.2.2.1.m1.1"><semantics id="S4.T2.2.2.2.2.1.m1.1a"><mi id="S4.T2.2.2.2.2.1.m1.1.1" xref="S4.T2.2.2.2.2.1.m1.1.1.cmml">𝐒</mi><annotation-xml encoding="MathML-Content" id="S4.T2.2.2.2.2.1.m1.1b"><ci id="S4.T2.2.2.2.2.1.m1.1.1.cmml" xref="S4.T2.2.2.2.2.1.m1.1.1">𝐒</ci></annotation-xml><annotation encoding="application/x-tex" id="S4.T2.2.2.2.2.1.m1.1c">\mathbf{S}</annotation><annotation encoding="application/x-llamapun" id="S4.T2.2.2.2.2.1.m1.1d">bold_S</annotation></semantics></math></span></th>
</tr>
<tr class="ltx_tr" id="S4.T2.8.8.8">
<th class="ltx_td ltx_align_left ltx_th ltx_th_column ltx_th_row" id="S4.T2.8.8.8.7" style="padding-left:4.0pt;padding-right:4.0pt;"><span class="ltx_text ltx_font_bold" id="S4.T2.8.8.8.7.1">Method</span></th>
<th class="ltx_td ltx_align_center ltx_th ltx_th_column" id="S4.T2.8.8.8.8" style="padding-left:4.0pt;padding-right:4.0pt;"><span class="ltx_text ltx_font_bold" id="S4.T2.8.8.8.8.1">Compl.</span></th>
<th class="ltx_td ltx_align_center ltx_th ltx_th_column" id="S4.T2.8.8.8.9" style="padding-left:4.0pt;padding-right:4.0pt;"><span class="ltx_text ltx_font_bold" id="S4.T2.8.8.8.9.1">Multi-view</span></th>
<th class="ltx_td ltx_align_center ltx_th ltx_th_column" id="S4.T2.8.8.8.10" style="padding-left:4.0pt;padding-right:4.0pt;"><span class="ltx_text ltx_font_bold" id="S4.T2.8.8.8.10.1">Context</span></th>
<th class="ltx_td ltx_align_center ltx_th ltx_th_column" id="S4.T2.3.3.3.1" style="padding-left:4.0pt;padding-right:4.0pt;">CLIP<math alttext="\uparrow" class="ltx_Math" display="inline" id="S4.T2.3.3.3.1.m1.1"><semantics id="S4.T2.3.3.3.1.m1.1a"><mo id="S4.T2.3.3.3.1.m1.1.1" stretchy="false" xref="S4.T2.3.3.3.1.m1.1.1.cmml">↑</mo><annotation-xml encoding="MathML-Content" id="S4.T2.3.3.3.1.m1.1b"><ci id="S4.T2.3.3.3.1.m1.1.1.cmml" xref="S4.T2.3.3.3.1.m1.1.1">↑</ci></annotation-xml><annotation encoding="application/x-tex" id="S4.T2.3.3.3.1.m1.1c">\uparrow</annotation><annotation encoding="application/x-llamapun" id="S4.T2.3.3.3.1.m1.1d">↑</annotation></semantics></math>
</th>
<th class="ltx_td ltx_align_center ltx_th ltx_th_column" id="S4.T2.4.4.4.2" style="padding-left:4.0pt;padding-right:4.0pt;">LPIPS<math alttext="\downarrow" class="ltx_Math" display="inline" id="S4.T2.4.4.4.2.m1.1"><semantics id="S4.T2.4.4.4.2.m1.1a"><mo id="S4.T2.4.4.4.2.m1.1.1" stretchy="false" xref="S4.T2.4.4.4.2.m1.1.1.cmml">↓</mo><annotation-xml encoding="MathML-Content" id="S4.T2.4.4.4.2.m1.1b"><ci id="S4.T2.4.4.4.2.m1.1.1.cmml" xref="S4.T2.4.4.4.2.m1.1.1">↓</ci></annotation-xml><annotation encoding="application/x-tex" id="S4.T2.4.4.4.2.m1.1c">\downarrow</annotation><annotation encoding="application/x-llamapun" id="S4.T2.4.4.4.2.m1.1d">↓</annotation></semantics></math>
</th>
<th class="ltx_td ltx_align_center ltx_th ltx_th_column" id="S4.T2.5.5.5.3" style="padding-left:4.0pt;padding-right:4.0pt;">PSNR<math alttext="\uparrow" class="ltx_Math" display="inline" id="S4.T2.5.5.5.3.m1.1"><semantics id="S4.T2.5.5.5.3.m1.1a"><mo id="S4.T2.5.5.5.3.m1.1.1" stretchy="false" xref="S4.T2.5.5.5.3.m1.1.1.cmml">↑</mo><annotation-xml encoding="MathML-Content" id="S4.T2.5.5.5.3.m1.1b"><ci id="S4.T2.5.5.5.3.m1.1.1.cmml" xref="S4.T2.5.5.5.3.m1.1.1">↑</ci></annotation-xml><annotation encoding="application/x-tex" id="S4.T2.5.5.5.3.m1.1c">\uparrow</annotation><annotation encoding="application/x-llamapun" id="S4.T2.5.5.5.3.m1.1d">↑</annotation></semantics></math>
</th>
<th class="ltx_td ltx_align_center ltx_th ltx_th_column" id="S4.T2.6.6.6.4" style="padding-left:4.0pt;padding-right:4.0pt;">CLIP<math alttext="\uparrow" class="ltx_Math" display="inline" id="S4.T2.6.6.6.4.m1.1"><semantics id="S4.T2.6.6.6.4.m1.1a"><mo id="S4.T2.6.6.6.4.m1.1.1" stretchy="false" xref="S4.T2.6.6.6.4.m1.1.1.cmml">↑</mo><annotation-xml encoding="MathML-Content" id="S4.T2.6.6.6.4.m1.1b"><ci id="S4.T2.6.6.6.4.m1.1.1.cmml" xref="S4.T2.6.6.6.4.m1.1.1">↑</ci></annotation-xml><annotation encoding="application/x-tex" id="S4.T2.6.6.6.4.m1.1c">\uparrow</annotation><annotation encoding="application/x-llamapun" id="S4.T2.6.6.6.4.m1.1d">↑</annotation></semantics></math>
</th>
<th class="ltx_td ltx_align_center ltx_th ltx_th_column" id="S4.T2.7.7.7.5" style="padding-left:4.0pt;padding-right:4.0pt;">LPIPS<math alttext="\downarrow" class="ltx_Math" display="inline" id="S4.T2.7.7.7.5.m1.1"><semantics id="S4.T2.7.7.7.5.m1.1a"><mo id="S4.T2.7.7.7.5.m1.1.1" stretchy="false" xref="S4.T2.7.7.7.5.m1.1.1.cmml">↓</mo><annotation-xml encoding="MathML-Content" id="S4.T2.7.7.7.5.m1.1b"><ci id="S4.T2.7.7.7.5.m1.1.1.cmml" xref="S4.T2.7.7.7.5.m1.1.1">↓</ci></annotation-xml><annotation encoding="application/x-tex" id="S4.T2.7.7.7.5.m1.1c">\downarrow</annotation><annotation encoding="application/x-llamapun" id="S4.T2.7.7.7.5.m1.1d">↓</annotation></semantics></math>
</th>
<th class="ltx_td ltx_align_center ltx_th ltx_th_column" id="S4.T2.8.8.8.6" style="padding-left:4.0pt;padding-right:4.0pt;">PSNR<math alttext="\uparrow" class="ltx_Math" display="inline" id="S4.T2.8.8.8.6.m1.1"><semantics id="S4.T2.8.8.8.6.m1.1a"><mo id="S4.T2.8.8.8.6.m1.1.1" stretchy="false" xref="S4.T2.8.8.8.6.m1.1.1.cmml">↑</mo><annotation-xml encoding="MathML-Content" id="S4.T2.8.8.8.6.m1.1b"><ci id="S4.T2.8.8.8.6.m1.1.1.cmml" xref="S4.T2.8.8.8.6.m1.1.1">↑</ci></annotation-xml><annotation encoding="application/x-tex" id="S4.T2.8.8.8.6.m1.1c">\uparrow</annotation><annotation encoding="application/x-llamapun" id="S4.T2.8.8.8.6.m1.1d">↑</annotation></semantics></math>
</th>
</tr>
<tr class="ltx_tr" id="S4.T2.10.10.10">
<th class="ltx_td ltx_align_left ltx_th ltx_th_column ltx_th_row ltx_border_t" id="S4.T2.9.9.9.1" style="padding-left:4.0pt;padding-right:4.0pt;">Oracle (<math alttext="\hat{J}=J" class="ltx_Math" display="inline" id="S4.T2.9.9.9.1.m1.1"><semantics id="S4.T2.9.9.9.1.m1.1a"><mrow id="S4.T2.9.9.9.1.m1.1.1" xref="S4.T2.9.9.9.1.m1.1.1.cmml"><mover accent="true" id="S4.T2.9.9.9.1.m1.1.1.2" xref="S4.T2.9.9.9.1.m1.1.1.2.cmml"><mi id="S4.T2.9.9.9.1.m1.1.1.2.2" xref="S4.T2.9.9.9.1.m1.1.1.2.2.cmml">J</mi><mo id="S4.T2.9.9.9.1.m1.1.1.2.1" xref="S4.T2.9.9.9.1.m1.1.1.2.1.cmml">^</mo></mover><mo id="S4.T2.9.9.9.1.m1.1.1.1" xref="S4.T2.9.9.9.1.m1.1.1.1.cmml">=</mo><mi id="S4.T2.9.9.9.1.m1.1.1.3" xref="S4.T2.9.9.9.1.m1.1.1.3.cmml">J</mi></mrow><annotation-xml encoding="MathML-Content" id="S4.T2.9.9.9.1.m1.1b"><apply id="S4.T2.9.9.9.1.m1.1.1.cmml" xref="S4.T2.9.9.9.1.m1.1.1"><eq id="S4.T2.9.9.9.1.m1.1.1.1.cmml" xref="S4.T2.9.9.9.1.m1.1.1.1"></eq><apply id="S4.T2.9.9.9.1.m1.1.1.2.cmml" xref="S4.T2.9.9.9.1.m1.1.1.2"><ci id="S4.T2.9.9.9.1.m1.1.1.2.1.cmml" xref="S4.T2.9.9.9.1.m1.1.1.2.1">^</ci><ci id="S4.T2.9.9.9.1.m1.1.1.2.2.cmml" xref="S4.T2.9.9.9.1.m1.1.1.2.2">𝐽</ci></apply><ci id="S4.T2.9.9.9.1.m1.1.1.3.cmml" xref="S4.T2.9.9.9.1.m1.1.1.3">𝐽</ci></apply></annotation-xml><annotation encoding="application/x-tex" id="S4.T2.9.9.9.1.m1.1c">\hat{J}=J</annotation><annotation encoding="application/x-llamapun" id="S4.T2.9.9.9.1.m1.1d">over^ start_ARG italic_J end_ARG = italic_J</annotation></semantics></math>)</th>
<th class="ltx_td ltx_align_center ltx_th ltx_th_column ltx_border_t" id="S4.T2.10.10.10.3" style="padding-left:4.0pt;padding-right:4.0pt;">GT</th>
<th class="ltx_td ltx_align_center ltx_th ltx_th_column ltx_border_t" id="S4.T2.10.10.10.4" style="padding-left:4.0pt;padding-right:4.0pt;">—</th>
<th class="ltx_td ltx_align_center ltx_th ltx_th_column ltx_border_t" id="S4.T2.10.10.10.5" style="padding-left:4.0pt;padding-right:4.0pt;">—</th>
<th class="ltx_td ltx_align_center ltx_th ltx_th_column ltx_border_t" id="S4.T2.10.10.10.6" style="padding-left:4.0pt;padding-right:4.0pt;">1.0</th>
<th class="ltx_td ltx_align_center ltx_th ltx_th_column ltx_border_t" id="S4.T2.10.10.10.7" style="padding-left:4.0pt;padding-right:4.0pt;">0.0</th>
<th class="ltx_td ltx_align_center ltx_th ltx_th_column ltx_border_t" id="S4.T2.10.10.10.2" style="padding-left:4.0pt;padding-right:4.0pt;"><math alttext="\infty" class="ltx_Math" display="inline" id="S4.T2.10.10.10.2.m1.1"><semantics id="S4.T2.10.10.10.2.m1.1a"><mi id="S4.T2.10.10.10.2.m1.1.1" mathvariant="normal" xref="S4.T2.10.10.10.2.m1.1.1.cmml">∞</mi><annotation-xml encoding="MathML-Content" id="S4.T2.10.10.10.2.m1.1b"><infinity id="S4.T2.10.10.10.2.m1.1.1.cmml" xref="S4.T2.10.10.10.2.m1.1.1"></infinity></annotation-xml><annotation encoding="application/x-tex" id="S4.T2.10.10.10.2.m1.1c">\infty</annotation><annotation encoding="application/x-llamapun" id="S4.T2.10.10.10.2.m1.1d">∞</annotation></semantics></math></th>
<th class="ltx_td ltx_align_center ltx_th ltx_th_column ltx_border_t" id="S4.T2.10.10.10.8" style="padding-left:4.0pt;padding-right:4.0pt;">0.957</th>
<th class="ltx_td ltx_align_center ltx_th ltx_th_column ltx_border_t" id="S4.T2.10.10.10.9" style="padding-left:4.0pt;padding-right:4.0pt;">0.027</th>
<th class="ltx_td ltx_align_center ltx_th ltx_th_column ltx_border_t" id="S4.T2.10.10.10.10" style="padding-left:4.0pt;padding-right:4.0pt;">18.91</th>
</tr>
</thead>
<tbody class="ltx_tbody">
<tr class="ltx_tr" id="S4.T2.11.11.11" style="background-color:#E6E6FF;">
<th class="ltx_td ltx_align_left ltx_th ltx_th_row ltx_border_t" id="S4.T2.11.11.11.1" style="padding-left:4.0pt;padding-right:4.0pt;"><span class="ltx_text" id="S4.T2.11.11.11.1.1" style="background-color:#E6E6FF;">PartGen (<math alttext="\hat{J}=\mathcal{B}(I\odot M,I)" class="ltx_Math" display="inline" id="S4.T2.11.11.11.1.1.m1.2"><semantics id="S4.T2.11.11.11.1.1.m1.2a"><mrow id="S4.T2.11.11.11.1.1.m1.2.2" xref="S4.T2.11.11.11.1.1.m1.2.2.cmml"><mover accent="true" id="S4.T2.11.11.11.1.1.m1.2.2.3" xref="S4.T2.11.11.11.1.1.m1.2.2.3.cmml"><mi id="S4.T2.11.11.11.1.1.m1.2.2.3.2" mathbackground="#E6E6FF" xref="S4.T2.11.11.11.1.1.m1.2.2.3.2.cmml">J</mi><mo id="S4.T2.11.11.11.1.1.m1.2.2.3.1" mathbackground="#E6E6FF" xref="S4.T2.11.11.11.1.1.m1.2.2.3.1.cmml">^</mo></mover><mo id="S4.T2.11.11.11.1.1.m1.2.2.2" mathbackground="#E6E6FF" xref="S4.T2.11.11.11.1.1.m1.2.2.2.cmml">=</mo><mrow id="S4.T2.11.11.11.1.1.m1.2.2.1" xref="S4.T2.11.11.11.1.1.m1.2.2.1.cmml"><mi class="ltx_font_mathcaligraphic" id="S4.T2.11.11.11.1.1.m1.2.2.1.3" mathbackground="#E6E6FF" xref="S4.T2.11.11.11.1.1.m1.2.2.1.3.cmml">ℬ</mi><mo id="S4.T2.11.11.11.1.1.m1.2.2.1.2" xref="S4.T2.11.11.11.1.1.m1.2.2.1.2.cmml">⁢</mo><mrow id="S4.T2.11.11.11.1.1.m1.2.2.1.1.1" xref="S4.T2.11.11.11.1.1.m1.2.2.1.1.2.cmml"><mo id="S4.T2.11.11.11.1.1.m1.2.2.1.1.1.2" mathbackground="#E6E6FF" stretchy="false" xref="S4.T2.11.11.11.1.1.m1.2.2.1.1.2.cmml">(</mo><mrow id="S4.T2.11.11.11.1.1.m1.2.2.1.1.1.1" xref="S4.T2.11.11.11.1.1.m1.2.2.1.1.1.1.cmml"><mi id="S4.T2.11.11.11.1.1.m1.2.2.1.1.1.1.2" mathbackground="#E6E6FF" xref="S4.T2.11.11.11.1.1.m1.2.2.1.1.1.1.2.cmml">I</mi><mo id="S4.T2.11.11.11.1.1.m1.2.2.1.1.1.1.1" lspace="0.222em" mathbackground="#E6E6FF" rspace="0.222em" xref="S4.T2.11.11.11.1.1.m1.2.2.1.1.1.1.1.cmml">⊙</mo><mi id="S4.T2.11.11.11.1.1.m1.2.2.1.1.1.1.3" mathbackground="#E6E6FF" xref="S4.T2.11.11.11.1.1.m1.2.2.1.1.1.1.3.cmml">M</mi></mrow><mo id="S4.T2.11.11.11.1.1.m1.2.2.1.1.1.3" mathbackground="#E6E6FF" xref="S4.T2.11.11.11.1.1.m1.2.2.1.1.2.cmml">,</mo><mi id="S4.T2.11.11.11.1.1.m1.1.1" mathbackground="#E6E6FF" xref="S4.T2.11.11.11.1.1.m1.1.1.cmml">I</mi><mo id="S4.T2.11.11.11.1.1.m1.2.2.1.1.1.4" mathbackground="#E6E6FF" stretchy="false" xref="S4.T2.11.11.11.1.1.m1.2.2.1.1.2.cmml">)</mo></mrow></mrow></mrow><annotation-xml encoding="MathML-Content" id="S4.T2.11.11.11.1.1.m1.2b"><apply id="S4.T2.11.11.11.1.1.m1.2.2.cmml" xref="S4.T2.11.11.11.1.1.m1.2.2"><eq id="S4.T2.11.11.11.1.1.m1.2.2.2.cmml" xref="S4.T2.11.11.11.1.1.m1.2.2.2"></eq><apply id="S4.T2.11.11.11.1.1.m1.2.2.3.cmml" xref="S4.T2.11.11.11.1.1.m1.2.2.3"><ci id="S4.T2.11.11.11.1.1.m1.2.2.3.1.cmml" xref="S4.T2.11.11.11.1.1.m1.2.2.3.1">^</ci><ci id="S4.T2.11.11.11.1.1.m1.2.2.3.2.cmml" xref="S4.T2.11.11.11.1.1.m1.2.2.3.2">𝐽</ci></apply><apply id="S4.T2.11.11.11.1.1.m1.2.2.1.cmml" xref="S4.T2.11.11.11.1.1.m1.2.2.1"><times id="S4.T2.11.11.11.1.1.m1.2.2.1.2.cmml" xref="S4.T2.11.11.11.1.1.m1.2.2.1.2"></times><ci id="S4.T2.11.11.11.1.1.m1.2.2.1.3.cmml" xref="S4.T2.11.11.11.1.1.m1.2.2.1.3">ℬ</ci><interval closure="open" id="S4.T2.11.11.11.1.1.m1.2.2.1.1.2.cmml" xref="S4.T2.11.11.11.1.1.m1.2.2.1.1.1"><apply id="S4.T2.11.11.11.1.1.m1.2.2.1.1.1.1.cmml" xref="S4.T2.11.11.11.1.1.m1.2.2.1.1.1.1"><csymbol cd="latexml" id="S4.T2.11.11.11.1.1.m1.2.2.1.1.1.1.1.cmml" xref="S4.T2.11.11.11.1.1.m1.2.2.1.1.1.1.1">direct-product</csymbol><ci id="S4.T2.11.11.11.1.1.m1.2.2.1.1.1.1.2.cmml" xref="S4.T2.11.11.11.1.1.m1.2.2.1.1.1.1.2">𝐼</ci><ci id="S4.T2.11.11.11.1.1.m1.2.2.1.1.1.1.3.cmml" xref="S4.T2.11.11.11.1.1.m1.2.2.1.1.1.1.3">𝑀</ci></apply><ci id="S4.T2.11.11.11.1.1.m1.1.1.cmml" xref="S4.T2.11.11.11.1.1.m1.1.1">𝐼</ci></interval></apply></apply></annotation-xml><annotation encoding="application/x-tex" id="S4.T2.11.11.11.1.1.m1.2c">\hat{J}=\mathcal{B}(I\odot M,I)</annotation><annotation encoding="application/x-llamapun" id="S4.T2.11.11.11.1.1.m1.2d">over^ start_ARG italic_J end_ARG = caligraphic_B ( italic_I ⊙ italic_M , italic_I )</annotation></semantics></math>)</span></th>
<td class="ltx_td ltx_align_center ltx_border_t" id="S4.T2.11.11.11.2" style="padding-left:4.0pt;padding-right:4.0pt;"><span class="ltx_text" id="S4.T2.11.11.11.2.1" style="background-color:#E6E6FF;">✓</span></td>
<td class="ltx_td ltx_align_center ltx_border_t" id="S4.T2.11.11.11.3" style="padding-left:4.0pt;padding-right:4.0pt;"><span class="ltx_text" id="S4.T2.11.11.11.3.1" style="background-color:#E6E6FF;">✓</span></td>
<td class="ltx_td ltx_align_center ltx_border_t" id="S4.T2.11.11.11.4" style="padding-left:4.0pt;padding-right:4.0pt;"><span class="ltx_text" id="S4.T2.11.11.11.4.1" style="background-color:#E6E6FF;">✓</span></td>
<td class="ltx_td ltx_align_center ltx_border_t" id="S4.T2.11.11.11.5" style="padding-left:4.0pt;padding-right:4.0pt;"><span class="ltx_text ltx_font_bold" id="S4.T2.11.11.11.5.1" style="background-color:#E6E6FF;">0.974</span></td>
<td class="ltx_td ltx_align_center ltx_border_t" id="S4.T2.11.11.11.6" style="padding-left:4.0pt;padding-right:4.0pt;"><span class="ltx_text ltx_font_bold" id="S4.T2.11.11.11.6.1" style="background-color:#E6E6FF;">0.015</span></td>
<td class="ltx_td ltx_align_center ltx_border_t" id="S4.T2.11.11.11.7" style="padding-left:4.0pt;padding-right:4.0pt;"><span class="ltx_text ltx_font_bold" id="S4.T2.11.11.11.7.1" style="background-color:#E6E6FF;">21.38</span></td>
<td class="ltx_td ltx_align_center ltx_border_t" id="S4.T2.11.11.11.8" style="padding-left:4.0pt;padding-right:4.0pt;"><span class="ltx_text ltx_font_bold" id="S4.T2.11.11.11.8.1" style="background-color:#E6E6FF;">0.936</span></td>
<td class="ltx_td ltx_align_center ltx_border_t" id="S4.T2.11.11.11.9" style="padding-left:4.0pt;padding-right:4.0pt;"><span class="ltx_text ltx_font_bold" id="S4.T2.11.11.11.9.1" style="background-color:#E6E6FF;">0.039</span></td>
<td class="ltx_td ltx_align_center ltx_border_t" id="S4.T2.11.11.11.10" style="padding-left:4.0pt;padding-right:4.0pt;"><span class="ltx_text ltx_font_bold" id="S4.T2.11.11.11.10.1" style="background-color:#E6E6FF;">17.16</span></td>
</tr>
<tr class="ltx_tr" id="S4.T2.13.13.13">
<th class="ltx_td ltx_align_left ltx_th ltx_th_row" id="S4.T2.13.13.13.2" style="padding-left:4.0pt;padding-right:4.0pt;">w/o context<sup class="ltx_sup" id="S4.T2.13.13.13.2.1"><span class="ltx_text ltx_font_italic" id="S4.T2.13.13.13.2.1.1">†</span></sup> (<math alttext="\hat{J}=\mathcal{B}(I\odot M)" class="ltx_Math" display="inline" id="S4.T2.13.13.13.2.m2.1"><semantics id="S4.T2.13.13.13.2.m2.1a"><mrow id="S4.T2.13.13.13.2.m2.1.1" xref="S4.T2.13.13.13.2.m2.1.1.cmml"><mover accent="true" id="S4.T2.13.13.13.2.m2.1.1.3" xref="S4.T2.13.13.13.2.m2.1.1.3.cmml"><mi id="S4.T2.13.13.13.2.m2.1.1.3.2" xref="S4.T2.13.13.13.2.m2.1.1.3.2.cmml">J</mi><mo id="S4.T2.13.13.13.2.m2.1.1.3.1" xref="S4.T2.13.13.13.2.m2.1.1.3.1.cmml">^</mo></mover><mo id="S4.T2.13.13.13.2.m2.1.1.2" xref="S4.T2.13.13.13.2.m2.1.1.2.cmml">=</mo><mrow id="S4.T2.13.13.13.2.m2.1.1.1" xref="S4.T2.13.13.13.2.m2.1.1.1.cmml"><mi class="ltx_font_mathcaligraphic" id="S4.T2.13.13.13.2.m2.1.1.1.3" xref="S4.T2.13.13.13.2.m2.1.1.1.3.cmml">ℬ</mi><mo id="S4.T2.13.13.13.2.m2.1.1.1.2" xref="S4.T2.13.13.13.2.m2.1.1.1.2.cmml">⁢</mo><mrow id="S4.T2.13.13.13.2.m2.1.1.1.1.1" xref="S4.T2.13.13.13.2.m2.1.1.1.1.1.1.cmml"><mo id="S4.T2.13.13.13.2.m2.1.1.1.1.1.2" stretchy="false" xref="S4.T2.13.13.13.2.m2.1.1.1.1.1.1.cmml">(</mo><mrow id="S4.T2.13.13.13.2.m2.1.1.1.1.1.1" xref="S4.T2.13.13.13.2.m2.1.1.1.1.1.1.cmml"><mi id="S4.T2.13.13.13.2.m2.1.1.1.1.1.1.2" xref="S4.T2.13.13.13.2.m2.1.1.1.1.1.1.2.cmml">I</mi><mo id="S4.T2.13.13.13.2.m2.1.1.1.1.1.1.1" lspace="0.222em" rspace="0.222em" xref="S4.T2.13.13.13.2.m2.1.1.1.1.1.1.1.cmml">⊙</mo><mi id="S4.T2.13.13.13.2.m2.1.1.1.1.1.1.3" xref="S4.T2.13.13.13.2.m2.1.1.1.1.1.1.3.cmml">M</mi></mrow><mo id="S4.T2.13.13.13.2.m2.1.1.1.1.1.3" stretchy="false" xref="S4.T2.13.13.13.2.m2.1.1.1.1.1.1.cmml">)</mo></mrow></mrow></mrow><annotation-xml encoding="MathML-Content" id="S4.T2.13.13.13.2.m2.1b"><apply id="S4.T2.13.13.13.2.m2.1.1.cmml" xref="S4.T2.13.13.13.2.m2.1.1"><eq id="S4.T2.13.13.13.2.m2.1.1.2.cmml" xref="S4.T2.13.13.13.2.m2.1.1.2"></eq><apply id="S4.T2.13.13.13.2.m2.1.1.3.cmml" xref="S4.T2.13.13.13.2.m2.1.1.3"><ci id="S4.T2.13.13.13.2.m2.1.1.3.1.cmml" xref="S4.T2.13.13.13.2.m2.1.1.3.1">^</ci><ci id="S4.T2.13.13.13.2.m2.1.1.3.2.cmml" xref="S4.T2.13.13.13.2.m2.1.1.3.2">𝐽</ci></apply><apply id="S4.T2.13.13.13.2.m2.1.1.1.cmml" xref="S4.T2.13.13.13.2.m2.1.1.1"><times id="S4.T2.13.13.13.2.m2.1.1.1.2.cmml" xref="S4.T2.13.13.13.2.m2.1.1.1.2"></times><ci id="S4.T2.13.13.13.2.m2.1.1.1.3.cmml" xref="S4.T2.13.13.13.2.m2.1.1.1.3">ℬ</ci><apply id="S4.T2.13.13.13.2.m2.1.1.1.1.1.1.cmml" xref="S4.T2.13.13.13.2.m2.1.1.1.1.1"><csymbol cd="latexml" id="S4.T2.13.13.13.2.m2.1.1.1.1.1.1.1.cmml" xref="S4.T2.13.13.13.2.m2.1.1.1.1.1.1.1">direct-product</csymbol><ci id="S4.T2.13.13.13.2.m2.1.1.1.1.1.1.2.cmml" xref="S4.T2.13.13.13.2.m2.1.1.1.1.1.1.2">𝐼</ci><ci id="S4.T2.13.13.13.2.m2.1.1.1.1.1.1.3.cmml" xref="S4.T2.13.13.13.2.m2.1.1.1.1.1.1.3">𝑀</ci></apply></apply></apply></annotation-xml><annotation encoding="application/x-tex" id="S4.T2.13.13.13.2.m2.1c">\hat{J}=\mathcal{B}(I\odot M)</annotation><annotation encoding="application/x-llamapun" id="S4.T2.13.13.13.2.m2.1d">over^ start_ARG italic_J end_ARG = caligraphic_B ( italic_I ⊙ italic_M )</annotation></semantics></math>)</th>
<td class="ltx_td ltx_align_center" id="S4.T2.13.13.13.3" style="padding-left:4.0pt;padding-right:4.0pt;">✓</td>
<td class="ltx_td ltx_align_center" id="S4.T2.13.13.13.4" style="padding-left:4.0pt;padding-right:4.0pt;">✓</td>
<td class="ltx_td ltx_align_center" id="S4.T2.13.13.13.5" style="padding-left:4.0pt;padding-right:4.0pt;">✗</td>
<td class="ltx_td ltx_align_center" id="S4.T2.13.13.13.6" style="padding-left:4.0pt;padding-right:4.0pt;">0.951</td>
<td class="ltx_td ltx_align_center" id="S4.T2.13.13.13.7" style="padding-left:4.0pt;padding-right:4.0pt;">0.028</td>
<td class="ltx_td ltx_align_center" id="S4.T2.13.13.13.8" style="padding-left:4.0pt;padding-right:4.0pt;">16.80</td>
<td class="ltx_td ltx_align_center" id="S4.T2.13.13.13.9" style="padding-left:4.0pt;padding-right:4.0pt;">0.923</td>
<td class="ltx_td ltx_align_center" id="S4.T2.13.13.13.10" style="padding-left:4.0pt;padding-right:4.0pt;">0.046</td>
<td class="ltx_td ltx_align_center" id="S4.T2.13.13.13.11" style="padding-left:4.0pt;padding-right:4.0pt;">14.83</td>
</tr>
<tr class="ltx_tr" id="S4.T2.15.15.15">
<th class="ltx_td ltx_align_left ltx_th ltx_th_row" id="S4.T2.15.15.15.2" style="padding-left:4.0pt;padding-right:4.0pt;">single view<sup class="ltx_sup" id="S4.T2.15.15.15.2.1"><span class="ltx_text ltx_font_italic" id="S4.T2.15.15.15.2.1.1">‡</span></sup> (<math alttext="\hat{J}_{v}=\mathcal{B}(I_{v}\odot M_{v},I_{v})" class="ltx_Math" display="inline" id="S4.T2.15.15.15.2.m2.2"><semantics id="S4.T2.15.15.15.2.m2.2a"><mrow id="S4.T2.15.15.15.2.m2.2.2" xref="S4.T2.15.15.15.2.m2.2.2.cmml"><msub id="S4.T2.15.15.15.2.m2.2.2.4" xref="S4.T2.15.15.15.2.m2.2.2.4.cmml"><mover accent="true" id="S4.T2.15.15.15.2.m2.2.2.4.2" xref="S4.T2.15.15.15.2.m2.2.2.4.2.cmml"><mi id="S4.T2.15.15.15.2.m2.2.2.4.2.2" xref="S4.T2.15.15.15.2.m2.2.2.4.2.2.cmml">J</mi><mo id="S4.T2.15.15.15.2.m2.2.2.4.2.1" xref="S4.T2.15.15.15.2.m2.2.2.4.2.1.cmml">^</mo></mover><mi id="S4.T2.15.15.15.2.m2.2.2.4.3" xref="S4.T2.15.15.15.2.m2.2.2.4.3.cmml">v</mi></msub><mo id="S4.T2.15.15.15.2.m2.2.2.3" xref="S4.T2.15.15.15.2.m2.2.2.3.cmml">=</mo><mrow id="S4.T2.15.15.15.2.m2.2.2.2" xref="S4.T2.15.15.15.2.m2.2.2.2.cmml"><mi class="ltx_font_mathcaligraphic" id="S4.T2.15.15.15.2.m2.2.2.2.4" xref="S4.T2.15.15.15.2.m2.2.2.2.4.cmml">ℬ</mi><mo id="S4.T2.15.15.15.2.m2.2.2.2.3" xref="S4.T2.15.15.15.2.m2.2.2.2.3.cmml">⁢</mo><mrow id="S4.T2.15.15.15.2.m2.2.2.2.2.2" xref="S4.T2.15.15.15.2.m2.2.2.2.2.3.cmml"><mo id="S4.T2.15.15.15.2.m2.2.2.2.2.2.3" stretchy="false" xref="S4.T2.15.15.15.2.m2.2.2.2.2.3.cmml">(</mo><mrow id="S4.T2.15.15.15.2.m2.1.1.1.1.1.1" xref="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.cmml"><msub id="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.2" xref="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.2.cmml"><mi id="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.2.2" xref="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.2.2.cmml">I</mi><mi id="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.2.3" xref="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.2.3.cmml">v</mi></msub><mo id="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.1" lspace="0.222em" rspace="0.222em" xref="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.1.cmml">⊙</mo><msub id="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.3" xref="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.3.cmml"><mi id="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.3.2" xref="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.3.2.cmml">M</mi><mi id="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.3.3" xref="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.3.3.cmml">v</mi></msub></mrow><mo id="S4.T2.15.15.15.2.m2.2.2.2.2.2.4" xref="S4.T2.15.15.15.2.m2.2.2.2.2.3.cmml">,</mo><msub id="S4.T2.15.15.15.2.m2.2.2.2.2.2.2" xref="S4.T2.15.15.15.2.m2.2.2.2.2.2.2.cmml"><mi id="S4.T2.15.15.15.2.m2.2.2.2.2.2.2.2" xref="S4.T2.15.15.15.2.m2.2.2.2.2.2.2.2.cmml">I</mi><mi id="S4.T2.15.15.15.2.m2.2.2.2.2.2.2.3" xref="S4.T2.15.15.15.2.m2.2.2.2.2.2.2.3.cmml">v</mi></msub><mo id="S4.T2.15.15.15.2.m2.2.2.2.2.2.5" stretchy="false" xref="S4.T2.15.15.15.2.m2.2.2.2.2.3.cmml">)</mo></mrow></mrow></mrow><annotation-xml encoding="MathML-Content" id="S4.T2.15.15.15.2.m2.2b"><apply id="S4.T2.15.15.15.2.m2.2.2.cmml" xref="S4.T2.15.15.15.2.m2.2.2"><eq id="S4.T2.15.15.15.2.m2.2.2.3.cmml" xref="S4.T2.15.15.15.2.m2.2.2.3"></eq><apply id="S4.T2.15.15.15.2.m2.2.2.4.cmml" xref="S4.T2.15.15.15.2.m2.2.2.4"><csymbol cd="ambiguous" id="S4.T2.15.15.15.2.m2.2.2.4.1.cmml" xref="S4.T2.15.15.15.2.m2.2.2.4">subscript</csymbol><apply id="S4.T2.15.15.15.2.m2.2.2.4.2.cmml" xref="S4.T2.15.15.15.2.m2.2.2.4.2"><ci id="S4.T2.15.15.15.2.m2.2.2.4.2.1.cmml" xref="S4.T2.15.15.15.2.m2.2.2.4.2.1">^</ci><ci id="S4.T2.15.15.15.2.m2.2.2.4.2.2.cmml" xref="S4.T2.15.15.15.2.m2.2.2.4.2.2">𝐽</ci></apply><ci id="S4.T2.15.15.15.2.m2.2.2.4.3.cmml" xref="S4.T2.15.15.15.2.m2.2.2.4.3">𝑣</ci></apply><apply id="S4.T2.15.15.15.2.m2.2.2.2.cmml" xref="S4.T2.15.15.15.2.m2.2.2.2"><times id="S4.T2.15.15.15.2.m2.2.2.2.3.cmml" xref="S4.T2.15.15.15.2.m2.2.2.2.3"></times><ci id="S4.T2.15.15.15.2.m2.2.2.2.4.cmml" xref="S4.T2.15.15.15.2.m2.2.2.2.4">ℬ</ci><interval closure="open" id="S4.T2.15.15.15.2.m2.2.2.2.2.3.cmml" xref="S4.T2.15.15.15.2.m2.2.2.2.2.2"><apply id="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.cmml" xref="S4.T2.15.15.15.2.m2.1.1.1.1.1.1"><csymbol cd="latexml" id="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.1.cmml" xref="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.1">direct-product</csymbol><apply id="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.2.cmml" xref="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.2"><csymbol cd="ambiguous" id="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.2.1.cmml" xref="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.2">subscript</csymbol><ci id="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.2.2.cmml" xref="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.2.2">𝐼</ci><ci id="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.2.3.cmml" xref="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.2.3">𝑣</ci></apply><apply id="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.3.cmml" xref="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.3"><csymbol cd="ambiguous" id="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.3.1.cmml" xref="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.3">subscript</csymbol><ci id="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.3.2.cmml" xref="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.3.2">𝑀</ci><ci id="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.3.3.cmml" xref="S4.T2.15.15.15.2.m2.1.1.1.1.1.1.3.3">𝑣</ci></apply></apply><apply id="S4.T2.15.15.15.2.m2.2.2.2.2.2.2.cmml" xref="S4.T2.15.15.15.2.m2.2.2.2.2.2.2"><csymbol cd="ambiguous" id="S4.T2.15.15.15.2.m2.2.2.2.2.2.2.1.cmml" xref="S4.T2.15.15.15.2.m2.2.2.2.2.2.2">subscript</csymbol><ci id="S4.T2.15.15.15.2.m2.2.2.2.2.2.2.2.cmml" xref="S4.T2.15.15.15.2.m2.2.2.2.2.2.2.2">𝐼</ci><ci id="S4.T2.15.15.15.2.m2.2.2.2.2.2.2.3.cmml" xref="S4.T2.15.15.15.2.m2.2.2.2.2.2.2.3">𝑣</ci></apply></interval></apply></apply></annotation-xml><annotation encoding="application/x-tex" id="S4.T2.15.15.15.2.m2.2c">\hat{J}_{v}=\mathcal{B}(I_{v}\odot M_{v},I_{v})</annotation><annotation encoding="application/x-llamapun" id="S4.T2.15.15.15.2.m2.2d">over^ start_ARG italic_J end_ARG start_POSTSUBSCRIPT italic_v end_POSTSUBSCRIPT = caligraphic_B ( italic_I start_POSTSUBSCRIPT italic_v end_POSTSUBSCRIPT ⊙ italic_M start_POSTSUBSCRIPT italic_v end_POSTSUBSCRIPT , italic_I start_POSTSUBSCRIPT italic_v end_POSTSUBSCRIPT )</annotation></semantics></math>)</th>
<td class="ltx_td ltx_align_center" id="S4.T2.15.15.15.3" style="padding-left:4.0pt;padding-right:4.0pt;">✓</td>
<td class="ltx_td ltx_align_center" id="S4.T2.15.15.15.4" style="padding-left:4.0pt;padding-right:4.0pt;">✗</td>
<td class="ltx_td ltx_align_center" id="S4.T2.15.15.15.5" style="padding-left:4.0pt;padding-right:4.0pt;">✓</td>
<td class="ltx_td ltx_align_center" id="S4.T2.15.15.15.6" style="padding-left:4.0pt;padding-right:4.0pt;">0.944</td>
<td class="ltx_td ltx_align_center" id="S4.T2.15.15.15.7" style="padding-left:4.0pt;padding-right:4.0pt;">0.031</td>
<td class="ltx_td ltx_align_center" id="S4.T2.15.15.15.8" style="padding-left:4.0pt;padding-right:4.0pt;">15.92</td>
<td class="ltx_td ltx_align_center" id="S4.T2.15.15.15.9" style="padding-left:4.0pt;padding-right:4.0pt;">0.922</td>
<td class="ltx_td ltx_align_center" id="S4.T2.15.15.15.10" style="padding-left:4.0pt;padding-right:4.0pt;">0.051</td>
<td class="ltx_td ltx_align_center" id="S4.T2.15.15.15.11" style="padding-left:4.0pt;padding-right:4.0pt;">13.25</td>
</tr>
<tr class="ltx_tr" id="S4.T2.16.16.16">
<th class="ltx_td ltx_align_left ltx_th ltx_th_row ltx_border_bb ltx_border_t" id="S4.T2.16.16.16.1" style="padding-left:4.0pt;padding-right:4.0pt;">None (<math alttext="\hat{J}=I\odot M" class="ltx_Math" display="inline" id="S4.T2.16.16.16.1.m1.1"><semantics id="S4.T2.16.16.16.1.m1.1a"><mrow id="S4.T2.16.16.16.1.m1.1.1" xref="S4.T2.16.16.16.1.m1.1.1.cmml"><mover accent="true" id="S4.T2.16.16.16.1.m1.1.1.2" xref="S4.T2.16.16.16.1.m1.1.1.2.cmml"><mi id="S4.T2.16.16.16.1.m1.1.1.2.2" xref="S4.T2.16.16.16.1.m1.1.1.2.2.cmml">J</mi><mo id="S4.T2.16.16.16.1.m1.1.1.2.1" xref="S4.T2.16.16.16.1.m1.1.1.2.1.cmml">^</mo></mover><mo id="S4.T2.16.16.16.1.m1.1.1.1" xref="S4.T2.16.16.16.1.m1.1.1.1.cmml">=</mo><mrow id="S4.T2.16.16.16.1.m1.1.1.3" xref="S4.T2.16.16.16.1.m1.1.1.3.cmml"><mi id="S4.T2.16.16.16.1.m1.1.1.3.2" xref="S4.T2.16.16.16.1.m1.1.1.3.2.cmml">I</mi><mo id="S4.T2.16.16.16.1.m1.1.1.3.1" lspace="0.222em" rspace="0.222em" xref="S4.T2.16.16.16.1.m1.1.1.3.1.cmml">⊙</mo><mi id="S4.T2.16.16.16.1.m1.1.1.3.3" xref="S4.T2.16.16.16.1.m1.1.1.3.3.cmml">M</mi></mrow></mrow><annotation-xml encoding="MathML-Content" id="S4.T2.16.16.16.1.m1.1b"><apply id="S4.T2.16.16.16.1.m1.1.1.cmml" xref="S4.T2.16.16.16.1.m1.1.1"><eq id="S4.T2.16.16.16.1.m1.1.1.1.cmml" xref="S4.T2.16.16.16.1.m1.1.1.1"></eq><apply id="S4.T2.16.16.16.1.m1.1.1.2.cmml" xref="S4.T2.16.16.16.1.m1.1.1.2"><ci id="S4.T2.16.16.16.1.m1.1.1.2.1.cmml" xref="S4.T2.16.16.16.1.m1.1.1.2.1">^</ci><ci id="S4.T2.16.16.16.1.m1.1.1.2.2.cmml" xref="S4.T2.16.16.16.1.m1.1.1.2.2">𝐽</ci></apply><apply id="S4.T2.16.16.16.1.m1.1.1.3.cmml" xref="S4.T2.16.16.16.1.m1.1.1.3"><csymbol cd="latexml" id="S4.T2.16.16.16.1.m1.1.1.3.1.cmml" xref="S4.T2.16.16.16.1.m1.1.1.3.1">direct-product</csymbol><ci id="S4.T2.16.16.16.1.m1.1.1.3.2.cmml" xref="S4.T2.16.16.16.1.m1.1.1.3.2">𝐼</ci><ci id="S4.T2.16.16.16.1.m1.1.1.3.3.cmml" xref="S4.T2.16.16.16.1.m1.1.1.3.3">𝑀</ci></apply></apply></annotation-xml><annotation encoding="application/x-tex" id="S4.T2.16.16.16.1.m1.1c">\hat{J}=I\odot M</annotation><annotation encoding="application/x-llamapun" id="S4.T2.16.16.16.1.m1.1d">over^ start_ARG italic_J end_ARG = italic_I ⊙ italic_M</annotation></semantics></math>)</th>
<td class="ltx_td ltx_align_center ltx_border_bb ltx_border_t" id="S4.T2.16.16.16.2" style="padding-left:4.0pt;padding-right:4.0pt;">✗</td>
<td class="ltx_td ltx_align_center ltx_border_bb ltx_border_t" id="S4.T2.16.16.16.3" style="padding-left:4.0pt;padding-right:4.0pt;">—</td>
<td class="ltx_td ltx_align_center ltx_border_bb ltx_border_t" id="S4.T2.16.16.16.4" style="padding-left:4.0pt;padding-right:4.0pt;">—</td>
<td class="ltx_td ltx_align_center ltx_border_bb ltx_border_t" id="S4.T2.16.16.16.5" style="padding-left:4.0pt;padding-right:4.0pt;">0.932</td>
<td class="ltx_td ltx_align_center ltx_border_bb ltx_border_t" id="S4.T2.16.16.16.6" style="padding-left:4.0pt;padding-right:4.0pt;">0.039</td>
<td class="ltx_td ltx_align_center ltx_border_bb ltx_border_t" id="S4.T2.16.16.16.7" style="padding-left:4.0pt;padding-right:4.0pt;">13.24</td>
<td class="ltx_td ltx_align_center ltx_border_bb ltx_border_t" id="S4.T2.16.16.16.8" style="padding-left:4.0pt;padding-right:4.0pt;">0.913</td>
<td class="ltx_td ltx_align_center ltx_border_bb ltx_border_t" id="S4.T2.16.16.16.9" style="padding-left:4.0pt;padding-right:4.0pt;">0.059</td>
<td class="ltx_td ltx_align_center ltx_border_bb ltx_border_t" id="S4.T2.16.16.16.10" style="padding-left:4.0pt;padding-right:4.0pt;">12.32</td>
</tr>
</tbody>
</table>{{< /table-caption >}}
> 🔼 표 2는 PartGen 모델의 부분 완성 및 3D 재구성 성능을 평가한 결과를 보여줍니다. 먼저, 다중 뷰 부분 완성은 기준 다중 뷰 부분 이미지 J와 비교하여 점수를 계산하여 평가합니다. 다음으로, 각 부분 S를 재구성하고 렌더링하여 3D 부분 재구성을 평가합니다. 자세한 내용은 본문을 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Table 2: Part completion results. We first evaluate view part completion by computing scores w.r.t. the ground-truth multi-view part image J𝐽Jitalic_J. Then, we evaluate 3D part reconstruction by reconstructing each part 𝐒𝐒\mathbf{S}bold_S and rendering it. See text for details.
> </details>

{{< table-caption >}}
| Method | CLIP ↑ | LPIPS ↓ | PSNR ↑ |
|---|---|---|---|
| PartGen (<span class="ltx_text">$\hat{\mathbf{L}}=\bigcup_{k}\Phi(\hat{J}_{k})$</span>) | 0.952 | 0.065 | 20.33 |
| Unstructured (<span class="ltx_text">$\hat{\mathbf{L}}=\Phi(I)$</span>) | 0.955 | 0.064 | 20.47 |{{< /table-caption >}}
> 🔼 표 3은 PartGen 모델의 부품 재조합 결과를 보여줍니다. 전체 객체의 3D 재구성 품질이 부품 기반 구성 재구성과 거의 동일하다는 것을 보여주는 결과는 예측된 부품들이 잘 맞춰진다는 것을 증명합니다.  즉, PartGen이 객체를 부품으로 분해하고 다시 조립하는 과정에서 부품들의 정확도와 일관성을 잘 유지함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Model reassembling result. The quality of 3D reconstruction of the object as a whole is close to that of the part-based compositional reconstruction, which proves that the predicted parts fit together well.
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