---
title: "From Elements to Design: A Layered Approach for Automatic Graphic Design Composition"
summary: "LaDeCo: 계층적 접근 방식을 사용한 자동 그래픽 디자인 합성"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Vision-Language Models", "🏢 Xi'an Jiaotong University",]
showSummary: true
date: 2024-12-27
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.19712 {{< /keyword >}}
{{< keyword icon="writer" >}} Jiawei Lin et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-30 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.19712" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.19712" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/from-elements-to-design-a-layered-approach" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

그래픽 디자인 합성은 **다양한 다중 모달 요소를 통합하여 조화롭고 미적으로 즐거운 디자인을 만드는 어려운 작업**입니다. 기존 연구는 주로 특정 하위 작업에만 초점을 맞추거나 그래픽 디자인의 계층적 정보를 고려하지 않아 제한적입니다. 이 논문에서는 **LaDeCo라는 새로운 접근 방식**을 제시하여 이 문제를 해결합니다.



LaDeCo는 **계층적 디자인 원리를 LMM에 통합**하여 디자인 합성 작업을 수행합니다. 먼저, 입력 요소를 의미론적 계층으로 분할하고, 각 계층에 대한 요소 속성을 예측합니다. 이전에 생성된 계층의 렌더링된 이미지를 컨텍스트에 포함하여 후속 계층의 생성을 안내합니다. 실험 결과는 LaDeCo가 디자인 합성에서 **뛰어난 성능**을 보임을 보여줍니다. 또한, **해상도 조정, 요소 채우기, 디자인 변형 등 다양한 응용 프로그램**을 지원합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 계층적 디자인 원리를 사용하여 복잡한 그래픽 디자인 합성 문제를 해결 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 다층적 디자인 합성을 통해 고품질의 디자인 생성 및 다양한 응용 프로그램 가능 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 기존의 전문 모델보다 일부 디자인 하위 작업에서 성능 우수 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
이 논문은 **계층적 디자인 원리를 대규모 다중 모달 모델(LMM)에 도입**하여 그래픽 디자인 합성 과제를 해결하는 새로운 접근 방식을 제시합니다. **다층적 디자인 합성 방법을 통해 복잡한 과제를 더 작고 관리하기 쉬운 단계로 분해**하여 그래픽 디자인 생성 프로세스를 원활하게 합니다. 또한, 이 연구는 **해상도 조정, 요소 채우기, 디자인 변형 등 흥미로운 응용 프로그램을 가능하게** 하여 실제 그래픽 디자인 작업에 대한 실용성과 다양성을 보여줍니다. 이러한 기여는 그래픽 디자인 분야의 연구자들에게 중요한 의미를 지닙니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.19712/x2.png)

> 🔼 그림 1은 본 논문에서 제안하는 방법이 다양한 종류의 요소들을 입력받아 조화롭고 균형 잡힌, 그리고 미적으로 만족스러운 그래픽 디자인으로 자동 합성하는 과정을 보여줍니다. (a)는 입력으로 주어진 다양한 모드의 요소들을 보여주고, (b)는 전체 디자인을 의미론적 요소에 따라 계층적으로 나누어 계층별로 디자인을 구성하는 과정을 보여주며, (c)는 본 논문의 방법을 통해 생성된 고품질의 디자인 결과물들을 보여줍니다.  (b)에서 보이는 계층적 접근 방식은 배경, 하위 레이어, 로고/이미지, 텍스트, 장식 요소 등의 레이어로 나누어 각 레이어별로 순차적으로 디자인을 구성함으로써 복잡한 디자인 합성 작업을 보다 효율적으로 수행합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: (a) Given a set of multimodal elements as input, our approach automatically composes them into a cohesive, balanced, and aesthetically pleasing graphic design. (b) Since a holistic design can be divided into different layers according to element semantics, we achieve the design composition task in a layer-by-layer manner. (c) Our approach is able to craft high-quality design pieces.
> </details>





{{< table-caption >}}
| Methods | (i) | (ii) | (iii) | (iv) | (v) | Val | Ove | Ali | Und<sub>l</sub> | Und<sub>s</sub> |
|---|---|---|---|---|---|---|---|---|---|---|
| FlexDM [11] | 5.34 | 5.29 | 5.41 | 5.09 | 4.54 | 0.8757 | 0.3242 | **0.0016** | 0.7286 | 0.7298 |
| GPT-4o [1] | 6.53 | 6.49 | 6.60 | 6.27 | 5.69 | 0.9968 | 0.0595 | 0.0001 | 0.3780 | 0.5708 |
| LaDeCo (Ours) | **8.08** | **7.92** | **8.00** | **7.82** | **6.98** | **0.9365** | **0.0865** | 0.0013 | **0.6922** | **0.6580** |
| GT | 8.35 | 8.21 | 8.30 | 8.01 | 7.26 | 0.9265 | 0.0768 | 0.0015 | 0.6848 | 0.6732 |{{< /table-caption >}}

> 🔼 표 1은 디자인 구성 작업에 대한 정량적 비교 결과를 보여줍니다. LLaVA-OV 평가는 디자인 및 레이아웃, 콘텐츠 관련성, 타이포그래피 및 색상, 그래픽 및 이미지, 혁신성 및 독창성의 다섯 가지 측면을 포함합니다. 실제 데이터(GT로 표시)에서 계산된 점수에 가장 가까운 점수는 굵게 표시되어 있으며, 이는 다양한 방법 중에서 최상의 성능을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Quantitative comparison on the design composition task. LLaVA-OV evaluation includes the following aspects: (i) design and layout, (ii) content relevance, (iii) typography and color, (vi) graphics and images, and (v) innovation and originality. The score closest to the one calculated from real data (denoted as GT) is highlighted in bold, indicating the best performance among different methods.
> </details>





### In-depth insights


#### Layered Design
본 논문에서 제시된 계층적 디자인(Layered Design) 접근 방식은 그래픽 디자인 생성 과정에 대한 새로운 관점을 제시합니다. **기존의 단일 모델 접근 방식과 달리, 배경, 하위 레이어, 로고/이미지, 텍스트, 장식 요소 등을 개별 레이어로 분리하여 순차적으로 생성함으로써 디자인 복잡성을 줄이고 생성 과정의 효율성을 높입니다.**  각 레이어는 이전 레이어의 결과를 고려하여 생성되므로, 디자인 요소 간의 조화와 일관성을 유지하는 데 효과적입니다. 이러한 계층적 구조는 **디자인 구성의 직관성을 높이고, 각 레이어별로 특정 하위 작업(예: 콘텐츠 인식 레이아웃 생성, 타이포그래피 생성)을 수행할 수 있는 유연성을 제공합니다.**  **계층적 디자인 원리는 인간 디자이너의 작업 방식을 모방하여, 더욱 자연스럽고 효과적인 디자인 생성을 가능하게 합니다.**  실험 결과는 제시된 방법이 기존 방법보다 성능이 우수하며, 해상도 조정, 요소 채우기, 디자인 변형 등 다양한 응용 분야에 적용될 수 있음을 보여줍니다.  결론적으로, **계층적 디자인은 복잡한 그래픽 디자인 생성 문제를 더 작고 관리하기 쉬운 단계로 분해함으로써, 보다 효율적이고 효과적인 자동 그래픽 디자인 생성을 가능하게 하는 핵심 전략**임을 시사합니다.

#### LMM Composition
본 논문에서 제시된 LMM(Large Multimodal Model) 구성 방식은 **계층적 디자인 원칙**을 기반으로 합니다. 이는 그래픽 디자인의 본질적인 계층 구조를 인식하고, 배경, 하위 레이어, 로고/이미지, 텍스트, 장식 요소 등을 각기 다른 레이어로 분리하여 순차적으로 생성하는 방식입니다. 이를 통해 복잡한 디자인 작업을 **더 작고 관리 가능한 단계**로 나누어 전체적인 디자인의 일관성 및 효율성을 높입니다. **GPT-4를 활용한 레이어 계획 모듈**은 입력 요소들을 의미론적으로 분류하는 역할을 하며, 이후 LMM은 각 레이어에 대한 요소 속성을 예측합니다. 이전 레이어의 결과물은 이미지로 렌더링되어 다음 레이어의 생성에 **맥락 정보**를 제공합니다. 이러한 계층적이고 순차적인 접근 방식은 디자인 구성 과정을 보다 매끄럽고 명확하게 하여 고품질의 디자인 결과물을 생성하는 데 기여합니다.  **다양한 하위 작업에 대한 특별한 훈련 없이도**  해상도 조정, 요소 채우기, 디자인 변형 등 다양한 응용 프로그램도 지원합니다.

#### LaDeCo Model
LaDeCo 모델은 **계층적 디자인 원리를 대규모 다중 모드 모델(LMM)에 통합**하여 그래픽 디자인 구성 작업을 수행하는 혁신적인 접근 방식입니다.  **레이어 계획 모듈**을 통해 입력 요소들을 의미론적 레이어로 분류하고, **계층적 디자인 구성 과정**을 통해 각 레이어의 요소 속성들을 순차적으로 예측합니다. 이는 어려운 디자인 구성 작업을 더 작고 관리하기 쉬운 단계들로 분해하여 보다 원활하고 명확하게 만듭니다.  **이전 레이어의 렌더링 이미지를 현재 레이어 예측에 활용**하여 context를 제공, 레이어 간의 일관성을 유지하고 디자인의 통합성을 높입니다.  결과적으로 LaDeCo는 다양한 디자인 하위 작업에서 전문화된 모델들을 능가하는 성능을 보이며, 해상도 조정, 요소 채우기, 디자인 변형 등의 **흥미로운 응용**을 가능하게 합니다.  **모델의 유연성**은 특정 작업에 대한 학습 없이도 특정 디자인 하위 작업을 수행할 수 있음을 시사합니다.

#### Ablation Study
본 논문의 ablation study는 **계층적 디자인 원칙(layered design principle)**과 **계층 계획 모듈(layer planning module)**, 그리고 **계층적 디자인 구성 프로세스(layered design composition process)**의 효과를 체계적으로 평가하기 위해 설계되었습니다.  각 요소를 제거하거나 변경하여 모델 성능에 미치는 영향을 정량적, 정성적으로 분석함으로써, 제안된 방법의 핵심 구성 요소들의 중요성을 밝히고자 하였습니다. 특히, 계층적 디자인 원칙의 효과는 전체 디자인 구성 작업의 성능 향상에 크게 기여했음을 보여주며, 계층 계획 모듈 또한 레이어 간의 일관성 및 효율성을 높이는 데 중요한 역할을 수행했음을 확인했습니다.  **계층적 디자인 구성 프로세스는 모델의 이해력을 높여 다양한 하위 작업(예: 해상도 조정, 요소 채우기, 디자인 변형)을 수행하는 데 유연성을 제공**했습니다.  결과적으로 ablation study는 LaDeCo 모델의 설계 선택이 타당함을 입증하고, 각 구성요소의 상호작용과 전체 성능에 대한 통찰력을 제공하는 데 기여했습니다.  이는 LaDeCo의 강건성과 일반화 능력을 보여주는 중요한 증거입니다.

#### Future Work
본 논문은 계층적 디자인 원리를 활용한 그래픽 디자인 자동 합성에 대한 LaDeCo라는 새로운 접근법을 제시합니다.  **향후 연구 방향**으로는 **다양한 유형의 디자인 요소(텍스트, 이미지, 기타 장식 요소)에 대한 지원 확장**이 중요합니다.  예를 들어, 현재 모델은 일부 텍스트 속성만 고려하지만, 향후에는 서체, 크기, 색상, 정렬 등 보다 세밀한 텍스트 스타일을 제어할 수 있도록 개선해야 합니다.  또한, **사용자의 디자인 의도를 더 잘 반영하는 사용자 정의 기능**을 추가하는 것이 필요합니다.  예를 들어, 사용자가 특정 레이아웃이나 색상을 지정하거나, 특정 요소의 배치를 제어할 수 있는 기능을 제공할 수 있습니다.  **다른 디자인 도구나 플랫폼과의 통합** 역시 중요한 과제입니다.  LaDeCo를 다른 그래픽 디자인 도구 또는 플랫폼과 연동하여 사용자 경험을 향상시키고, 실제 디자인 작업에 효율적으로 활용할 수 있도록 해야 합니다.  마지막으로, **모델의 확장성과 효율성을 높이는 연구**가 필요합니다.  더욱 다양하고 복잡한 디자인을 처리할 수 있도록 모델의 용량을 늘리거나, 계산 효율을 개선하는 연구를 통해 실제 응용 가능성을 높여야 합니다. 이를 통해 LaDeCo는 더욱 강력하고 실용적인 그래픽 디자인 자동 합성 도구로 발전할 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.19712/x3.png)

> 🔼 그림 2는 제안된 LaDeCo의 작동 방식을 보여줍니다. 먼저, 입력 요소들에 대한 의미론적 레이블을 주석 처리하기 위해 GPT-4o [1]를 사용합니다. 예측을 통해 계층 구조를 얻은 후, LaDeCo는 LMM(Large Multimodal Model)을 미세 조정하여 계층적 디자인 구성을 수행합니다. 각 계층을 생성한 후, 중간 디자인 결과를 이미지로 렌더링하여 LMM에 다시 입력으로 제공하여 후속 계층 생성을 안내합니다.  즉, 배경부터 장식 요소까지 각 레이어별로 디자인 요소들을 생성하고, 이전 레이어의 결과를 다음 레이어 생성에 반영하여 최종 디자인을 완성하는 과정입니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Illustration of our proposed LaDeCo. First, it utilizes GPT-4o [1] to annotate the semantic labels for input elements. The layer structure is obtained from the predictions. Then LaDeCo fine-tunes LMMs to achieve layered design composition. After generating each layer, the intermediate designs will be rendered as images and fed back into LMMs to guide subsequent layer generation.
> </details>



![](https://arxiv.org/html/2412.19712/extracted/6098037/sec/images/layer.png)

> 🔼 그림 3은 제안된 LaDeCo 방법과 기존 방법(FlexDM, GPT-40) 및 실제 디자인(GT)을 비교하여 디자인 합성 성능을 보여줍니다. 여러 디자인 예시를 보여주며, 각 방법의 결과물을 실제 디자인과 나란히 배치하여 직관적인 비교를 가능하게 합니다. 자세히 보시려면 확대해서 보세요.
> <details>
> <summary>read the caption</summary>
> Figure 3: Qualitative comparison. We also show the ground truth designs for these samples. Please zoom in for a better view.
> </details>



![](https://arxiv.org/html/2412.19712/x4.png)

> 🔼 그림 4는 LaDeCo가 각 레이어별로 생성한 결과물들을 보여줍니다. 배경, 하단 레이어, 로고/이미지, 텍스트, 장식 요소 등 5가지 레이어로 나뉘어 각 레이어별 생성 결과가 순차적으로 나타나 있습니다. 이를 통해 LaDeCo의 계층적 디자인 생성 과정을 시각적으로 이해하는 데 도움을 줍니다. 각 레이어는 이전 레이어의 결과를 바탕으로 생성되므로, 전체 디자인의 일관성과 조화로움을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: The rendered results of different layers from LaDeCo.
> </details>



![](https://arxiv.org/html/2412.19712/x5.png)

> 🔼 그림 5는 LaDeCo가 동일한 입력 요소를 사용하여 다양한 캔버스 크기의 디자인을 생성하는 과정을 보여줍니다.  같은 요소들로도 캔버스 크기에 따라 디자인의 레이아웃과 요소들의 크기 및 배치가 어떻게 조정되는지를 보여주는 여러 디자인 사례들이 제시되어 있습니다. 이를 통해 LaDeCo가 다양한 크기의 캔버스에 적응하여 일관되고 시각적으로 만족스러운 디자인을 생성할 수 있는 능력을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: LaDeCo composes the same input elements to designs with different canvas sizes.
> </details>



![](https://arxiv.org/html/2412.19712/x6.png)

> 🔼 기존 디자인에 LaDeCo가 새로운 요소를 추가하여 더욱 매력적인 디자인을 만드는 과정을 보여줍니다.  기존 디자인에 새로운 요소들을 추가하는 방법과 그 결과를 시각적으로 보여주는 여러 예시들이 포함되어 있습니다.  각 예시는 새로운 요소들이 추가되기 전과 후의 디자인을 비교하여, LaDeCo가 디자인의 시각적 매력도를 높이는 데 효과적임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: LaDeCo adds new elements on a existing design to achieve a more appealing design.
> </details>



![](https://arxiv.org/html/2412.19712/x7.png)

> 🔼 그림 7은 동일한 요소들을 사용하여 LaDeCo가 다양한 디자인을 생성할 수 있음을 보여줍니다.  즉, 동일한 입력 요소 집합에도 불구하고 LaDeCo는 디자인의 레이아웃, 색상, 글꼴, 이미지 배치 등을 다르게 구성하여 여러 가지 시각적으로 매력적이고 다채로운 결과물을 만들어낼 수 있습니다. 이는 LaDeCo의 유연성과 창의성을 보여주는 좋은 예시입니다.  이는 디자인 변형 기능을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: LaDeCo creates diverse designs with the same elements.
> </details>



![](https://arxiv.org/html/2412.19712/x8.png)

> 🔼 그림 8은 콘텐츠 인식 레이아웃 생성 작업에 대한 정성적 비교를 보여줍니다. 노란색, 빨간색, 녹색, 분홍색 상자는 각각 언더레이, 이미지, 텍스트, 장식 요소를 나타냅니다. 이 그림은 다양한 방법(PosterLlama, PosterLLaVA, LaDeCo, GT)으로 생성된 콘텐츠 인식 레이아웃의 시각적 비교를 보여주어 각 모델의 강점과 약점을 파악하는 데 도움이 됩니다. 각 모델의 출력물은 레이아웃 구성, 콘텐츠 관련성, 타이포그래피 및 색상, 그래픽 및 이미지, 혁신성 및 독창성 측면에서 평가될 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Qualitative comparison on the content-aware layout generation task. The yellow, red, green, pink boxes represent underlay, image, text, and embellishment elements, respectively.
> </details>



![](https://arxiv.org/html/2412.19712/x9.png)

> 🔼 그림 9는 본 논문의 타이포그래피 생성에 대한 정성적 비교 결과를 보여줍니다. FlexDM과 OpenCOLE을 비롯한 다른 기존 방법들과 LaDeCo의 결과를 비교하여 LaDeCo의 우수성을 보여줍니다.  LaDeCo는 텍스트 레이아웃, 미적 요소, 가독성 등 여러 측면에서 더 나은 성능을 보여주는 것을 확인할 수 있습니다. 특히, 기존 방법들에서 나타나는 텍스트 중첩이나 가독성 저하와 같은 문제점들을 LaDeCo가 효과적으로 해결했음을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Qualitative comparison on typography generation.
> </details>



![](https://arxiv.org/html/2412.19712/x10.png)

> 🔼 그림 10은 LaDeCo가 생성한 다양한 그래픽 디자인들을 보여줍니다.  각 디자인은 다양한 스타일, 색상, 레이아웃, 그리고 시각적 요소들을 사용하여 만들어졌으며,  LaDeCo 모델의 다양한 디자인 생성 능력을 보여주는 좋은 예시입니다.  이 그림은 배경, 텍스트, 이미지, 기타 장식 요소 등 다양한 요소들이 어떻게 조화롭게 구성되는지를 보여주며, LaDeCo 모델의 레이어 기반 접근 방식의 효과를 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: A gallery of graphic designs created by LaDeCo.
> </details>



![](https://arxiv.org/html/2412.19712/x11.png)

> 🔼 그림 11은 LaDeCo의 계층적 디자인 구성 과정을 보여줍니다.  LaDeCo는 배경, 하단 레이어, 로고/이미지, 텍스트, 장식 요소 순서로 전체 디자인을 생성합니다. 각 레이어는 특정한 시각적 요소들을 포함하며, 이전 레이어의 결과를 바탕으로 다음 레이어가 생성됩니다. 이러한 계층적 접근 방식은 디자인 구성 과정을 더욱 체계적이고 효율적으로 만들어 줍니다.  각 레이어의 예시 이미지를 통해 각 레이어의 역할과 전체 디자인 구성에 대한 이해를 도울 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: The layered design composition process in LaDeCo. Our approach generates a holistic design in the order of background, underlay, logo/image, text, and embellishment layers.
> </details>



![](https://arxiv.org/html/2412.19712/x12.png)

> 🔼 그림 12는 동일한 입력에도 LaDeCo가 다양한 디자인을 생성할 수 있음을 보여주는 추가적인 결과입니다. 그림에는 다양한 스타일과 레이아웃을 가진 여러 디자인이 포함되어 있으며, LaDeCo의 유연성과 다양한 디자인 생성 능력을 강조합니다. 각 디자인은 배경, 언더레이, 로고/이미지, 텍스트, 장식 요소 등 여러 레이어로 구성되어 있으며, 각 레이어의 요소들이 조화롭게 배치되어 시각적으로 매력적인 결과물을 만들어냅니다. 이는 LaDeCo가 다양한 디자인 요구사항을 충족할 수 있는 잠재력을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: More results to demonstrate that LaDeCo can create diverse designs with the same input.
> </details>



![](https://arxiv.org/html/2412.19712/x13.png)

> 🔼 이 그림은 LaDeCo 모델이 다양한 종횡비(aspect ratio)를 가진 그래픽 디자인을 생성할 수 있음을 보여주는 추가적인 결과물들을 보여줍니다.  다양한 크기의 캔버스에 적용된 디자인들을 통해 모델의 유연성과 적응력을 확인할 수 있습니다.  각 디자인은 배경, 하단 레이어, 로고/이미지, 텍스트, 장식 요소 등 다양한 레이어로 구성되어 있으며, 각 레이어의 요소들은 종횡비에 맞춰 조정되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: More results to demonstrate that LaDeCo is able to generate graphic designs with different aspect ratios.
> </details>



![](https://arxiv.org/html/2412.19712/x14.png)

> 🔼 이 그림은 LaDeCo가 기존 디자인에 새로운 요소를 자연스럽게 추가할 수 있음을 보여주는 추가적인 결과들을 보여줍니다.  각각의 이미지 쌍은 기존 디자인과 새로운 요소들을 추가한 후의 디자인을 보여줍니다.  LaDeCo는 새로운 요소들이 기존 디자인과 시각적으로 조화롭게 어울리도록 배치하고 스타일을 일관성 있게 유지합니다. 이는 LaDeCo가 단순히 요소들을 추가하는 것이 아니라 디자인의 전체적인 조화와 일관성을 고려하여 새로운 요소들을 통합한다는 점을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: More results to demonstrate that LaDeCo can add new elements to an existing design in a plausible way.
> </details>



![](https://arxiv.org/html/2412.19712/x15.png)

> 🔼 그림 15는 LaDeCo의 디자인 구성 능력의 우수성을 보여주는 정성적 비교를 보여줍니다.  FlexDM, GPT-40, LaDeCo 세 가지 방법으로 생성된 디자인과 실제 디자인(GT)을 나란히 비교하여 시각적으로 LaDeCo의 성능을 보여줍니다.  각 방법의 디자인 결과는 레이아웃, 색상 조합, 폰트 선택, 이미지 배치 등 다양한 측면에서 차이를 보이며, LaDeCo가 가장 실제 디자인(GT)과 유사한 결과를 생성했음을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 15: More qualitative comparison to demonstrate the superiority of LaDeCo in design composition.
> </details>



![](https://arxiv.org/html/2412.19712/x16.png)

> 🔼 그림 16은 LaDeCo가 콘텐츠 인식 레이아웃 생성에서 우수성을 보여주는 보다 정성적인 비교를 보여줍니다. 그림은 콘텐츠 인식 레이아웃 생성 작업에 대한 LaDeCo와 다른 방법들의 결과를 보여주는 여러 디자인 예시들을 보여줍니다. 각 열은 서로 다른 방법(PosterLlama, PosterLLaVA, LaDeCo, GT)으로 생성된 디자인을 보여주고, 각 행은 다른 입력 콘텐츠 집합에 대한 결과를 보여줍니다. 이 그림을 통해 LaDeCo가 다른 방법들보다 콘텐츠를 더 잘 정렬하고 시각적으로 만족스러운 레이아웃을 생성하는 것을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 16: More qualitative comparison to demonstrate the superiority of LaDeCo in content-aware layout generation.
> </details>



![](https://arxiv.org/html/2412.19712/x17.png)

> 🔼 그림 17은 LaDeCo가 서체 생성 작업에서 우수함을 보여주는 정성적 비교를 더 자세히 보여줍니다.  다양한 디자인 예시를 통해 LaDeCo가 생성한 서체 디자인과 다른 기준 모델들(FlexDM, OpenCOLE)의 서체 디자인을 비교하여 LaDeCo의 성능을 시각적으로 보여줍니다. 각 이미지는 입력 요소와 LaDeCo 및 다른 모델이 생성한 서체의 시각적 결과를 보여줍니다. 이를 통해 사용자는 LaDeCo의 서체 생성 품질을 직관적으로 이해할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 17: More qualitative comparison to demonstrate the superiority of LaDeCo in typography generation.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Settings | (i) | (ii) | (iii) | (iv) | (v) | Val | Ove | Ali | Und<sub>l</sub> | Und<sub>s</sub> |
|---|---|---|---|---|---|---|---|---|---|---|
| Llama-3.1-8B (rank 16) | 8.03 | 7.89 | 8.00 | 7.75 | 6.90 | 0.9347 | 0.0796 | 0.0012 | 0.6900 | 0.6564 |
| Llama-3.1-8B (rank 64) | 8.10 | 7.94 | 8.04 | 7.83 | 6.98 | 0.9352 | 0.0787 | 0.0013 | 0.7084 | 0.6715 |
| llava-v1.5-7b (rank 32) | 8.00 | 7.86 | 8.02 | 7.78 | 6.90 | 0.9403 | 0.0940 | 0.0015 | 0.6703 | 0.6208 |
| Llama-3.1-8B-Instruct (rank 32) | 8.08 | 7.89 | 8.03 | 7.82 | 6.99 | 0.9388 | 0.0804 | 0.0015 | 0.6867 | 0.6640 |
| w/o LP, w/o LDC (rank 32) | 7.23 | 7.12 | 7.28 | 6.99 | 6.29 | 0.9325 | 0.0954 | 0.0013 | 0.6194 | 0.5875 |
| w/ LP, w/o LDC (rank 32) | 7.84 | 7.67 | 7.78 | 7.56 | 6.66 | 0.9389 | 0.0843 | 0.0013 | 0.6568 | 0.6242 |
| Llama-3.1-8B* (rank 32) | 8.22 | 8.06 | 8.22 | 7.94 | 7.09 | 0.9335 | 0.1029 | 0.0005 | 0.7321 | 0.7116 |
| Llama-3.1-8B (rank 32) | 8.08 | 7.92 | 8.00 | 7.82 | 6.98 | 0.9365 | 0.0865 | 0.0013 | 0.6922 | 0.6580 |
| GT | 8.35 | 8.21 | 8.30 | 8.01 | 7.26 | 0.9265 | 0.0768 | 0.0015 | 0.6848 | 0.6732 |{{< /table-caption >}}
> 🔼 표 2는 LaDeCo 모델의 성능에 영향을 미치는 요인들을 분석한 실험 결과를 보여줍니다.  총 4가지 측면을 다루고 있는데, (1) LoRA(Low-Rank Adaptation)에서 rank의 크기, (2) 기반 모델의 종류, (3) LaDeCo의 핵심 기법인 계층적 레이어 계획(Layer Planning, LP)과 계층적 디자인 구성(Layered Design Composition, LDC)의 적용 여부, (4) 데이터셋 크기입니다.  표에서 별표(*)가 표시된 모델은 Crello와 LargeCrello 데이터셋을 결합하여 학습한 모델이고, 별표가 없는 모델은 Crello 데이터셋만 사용하여 학습한 모델입니다. 이를 통해 각 요인이 LaDeCo의 성능에 어떤 영향을 미치는지 정량적으로 비교 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Ablation studies. Our investigation covers four aspects (from top to bottom): (1) the rank number in LoRA, (2) the base model, (3) the key techniques in LaDeCo, where LP denotes layer planning , and LDC represents layered design composition, (4) dataset size. The model with * to is trained on the combined Crello and LargeCrello datasets, while the models without * are trained on Crello only.
> </details>

{{< table-caption >}}
| Methods | Val | Ove | Ali | Und<sub>l</sub> | Und<sub>s</sub> | Uti | Occ | Rea |
|---|---|---|---|---|---|---|---|---|
| PosterLLaVa [32] | **0.9269** | 0.0685 | 0.0011 | 0.7879 | 0.7375 | 0.4199 | 0.1936 | **0.0747** |
| PosterLlama [27] | 0.8701 | 0.0868 | 0.0014 | 0.8483 | 0.7798 | 0.4115 | **0.1772** | 0.0694 |
| LaDeCo (Ours) | 0.9340 | **0.0805** | **0.0016** | **0.6851** | **0.6540** | **0.4414** | 0.1835 | 0.0768 |
| GT | 0.9265 | 0.0768 | 0.0015 | 0.6848 | 0.6732 | 0.4737 | 0.1628 | 0.0709 |{{< /table-caption >}}
> 🔼 표 3은 콘텐츠 인식 레이아웃 생성 하위 작업에 대한 정량적 결과를 보여줍니다. 실제 데이터(GT로 표시)에서 계산된 점수와 가장 가까운 점수는 굵게 표시되어 있으며, 이는 다양한 방법 중에서 최상의 성능을 나타냅니다.  각 방법의 성능을 평가하기 위해 디자인 및 레이아웃, 콘텐츠 관련성, 타이포그래피 및 색상, 그래픽 및 이미지, 혁신성 및 독창성의 다섯 가지 측면을 평가하는 LLaVA-OV 지표를 사용했습니다.  또한, 요소 유효성(Val), 중첩(Ove), 정렬(Ali), 하위 효과(Und₁, Unds), 활용도(Uti), 폐색(Occ), 가독성(Rea)과 같은 기하학적 지표도 함께 제시하여 레이아웃의 질을 다각적으로 분석하였습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Quantitative results on the content-aware layout generation subtask. The score closest to the one calculated from real data (denoted as GT) is highlighted in bold, indicating the best performance among different methods.
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