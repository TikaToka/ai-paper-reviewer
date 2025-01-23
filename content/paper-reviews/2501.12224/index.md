---
title: "TokenVerse: Versatile Multi-concept Personalization in Token Modulation Space"
summary: "TokenVerse는 단일 이미지에서 복잡한 시각적 개념을 분리하고, 이를 새로운 방식으로 결합하여 창의적인 이미지를 생성하는 혁신적인 방법입니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Generation", "🏢 Google DeepMind",]
showSummary: true
date: 2025-01-21
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.12224 {{< /keyword >}}
{{< keyword icon="writer" >}} Daniel Garibi et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-22 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.12224" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.12224" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/tokenverse-versatile-multi-concept" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

텍스트-이미지 생성 모델은 이미지 생성에 있어 괄목할 만한 성과를 보였지만, 사용자가 생성된 이미지의 개별 개념들을 제어하는 것은 여전히 어려운 과제입니다. 기존의 개인화 방법들은 개별 개념을 분리하거나 여러 개념을 원활하게 조합하는 데 어려움을 겪습니다. 특히, 개체가 아닌 포즈, 소재, 조명과 같은 개념의 개인화는 더욱 어려운 문제입니다.

본 연구에서는 이러한 문제를 해결하기 위해 새로운 프레임워크인 TokenVerse를 제안합니다. TokenVerse는 사전 훈련된 텍스트-이미지 확산 모델을 활용하여 단일 이미지에서 여러 개념을 분리하고, 이를 유연하게 조합하여 새로운 이미지를 생성합니다.  개념 이미지와 캡션을 사용하여 각 텍스트 토큰에 대한 개인화된 표현을 학습하고, 이를 새로운 텍스트 프롬프트에 통합하여 창의적인 이미지를 생성합니다. 실험 결과, TokenVerse는 다양한 개인화 설정에서 우수한 성능을 보이며, 기존 방법보다 유연하고 효과적인 다중 개념 개인화를 제공함을 보여줍니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} TokenVerse는 단일 이미지에서 여러 개념을 효과적으로 분리하고 재결합하여 새로운 이미지를 생성할 수 있습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 개인화된 텍스트 토큰을 사용하여 다양한 시각적 요소(개체, 액세서리, 소재, 포즈, 조명 등)를 유연하게 조작할 수 있습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 본 연구는 다양한 개인화 설정에서 TokenVerse의 효과를 입증하고, 기존 방법에 비해 우수한 성능을 보여줍니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**본 논문은 다중 개념 이미지 개인화 분야에 중요한 기여를 합니다.** **기존 방법들의 한계를 극복하고 다양한 비주얼 요소들을 효과적으로 분리 및 조합하는 새로운 프레임워크를 제시합니다.**  **이는 향후 다양한 멀티미디어 콘텐츠 생성 및 편집 기술 발전에 크게 기여할 수 있으며, 스토리텔링 및 개인 맞춤형 콘텐츠 제작과 같은 응용 분야에서 혁신을 가져올 수 있습니다.**

------
#### Visual Insights



![](https://arxiv.org/html/2501.12224/x2.png)

> 🔼 이 그림은 TokenVerse가 여러 개념 이미지(위쪽)에서 독립적으로 복잡하고 구별되는 시각적 개념을 추출하고, 사용자가 새로운 다양한 구성으로 이러한 개념을 묘사하는 이미지를 생성할 수 있게 한다는 것을 보여줍니다(아래쪽).  TokenVerse 프레임워크는 각 개념 이미지를 독립적으로 처리하고, 추가적인 감독이나 마스크 없이 오직 수반되는 캡션에만 기반하여 개념을 분리하는 것을 학습합니다. 이는 소스 캡션의 각 토큰에 대한 개인화된 표현을 학습함으로써 달성됩니다. 여러 이미지에서 추출된 개인화된 텍스트 토큰은 새로운 텍스트 프롬프트(색상이 있는 단어)에 유연하게 통합되어 참신하고 창의적인 이미지를 생성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: TokenVerse extracts distinct complex visual concepts from a set of concept images (top), and allows users to generate images that depict these concepts in novel versatile compositions (bottom row). Our framework independently processes each concept image, and learns to disentangle its concepts based solely on an accompanying caption, without any additional supervision or masks. This is achieved by learning a personalized representation for each token in the source caption. Our personalized text tokens, extracted from multiple images, are then flexibly incorporated into new text prompts (colored words) to generate novel creative images.
> </details>





{{< table-caption >}}
| Method | Concept | Concept | masks |
|---|---|---|---| 
| **DB LoRA** | × | × | √ |
| **Break-A-Scene** | √ | × | × |
| **ConceptExpress** | √ | × | √ |
| **OMG** | × | √ | √ |
| **TokenVerse (Ours)** | √ | √ | √ |{{< /table-caption >}}

> 🔼 표 1은 기존 연구들의 성능을 비교 분석한 표입니다. DreamBooth, BAS, ConceptExpress, OMG 네 가지 기존 연구와 제안하는 방법(TokenVerse)을 비교하여 개별 이미지에서 여러 개체를 분리하고 개인화하는 개념 분해(Concept decomposition) 작업과, 여러 이미지에서 추출한 개념들을 결합하여 새로운 이미지를 생성하는 개념 구성(Composition) 작업에 대한 성능을 보여줍니다. 기존 연구들과 달리 제안하는 방법은 마스크 없이도 여러 개체를 분리하고 개인화할 수 있으며, 여러 개의 참조 이미지에서 추출한 개체들을 결합하여 이미지를 생성할 수 있다는 점을 강조하고 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Capabilities of competing baselines. The table lists the capabilities of DreamBooth [32], BAS [8], ConceptExpress [14], OMG [23] and our method. Concept decomposition is the task of disentangling and personalizing multiple objects from a single image. Composition is the task of combining separately learned concepts in a new generated image. Unlike existing approaches, our method enables mask-free multi-object disentangled personalization, as well as the composition of multiple objects from several reference images.
> </details>





### In-depth insights


#### TokenVerse: A New Approach
TokenVerse는 기존 텍스트-이미지 생성 모델의 한계를 극복하는 새로운 접근 방식을 제시합니다. **기존 방법들은 개별 이미지에서 개념을 분리하거나 여러 이미지의 개념을 결합하는 데 어려움**을 겪었지만, TokenVerse는 이러한 문제를 해결하기 위해 **토큰 변조 공간(Token Modulation Space)**을 활용합니다. 이는 각 텍스트 토큰에 대한 개별적인 변조 벡터를 학습하여 이미지의 개별 요소를 독립적으로 제어할 수 있게 합니다. **이를 통해 다수의 이미지에서 추출한 복잡한 시각적 개념들을 섬세하게 조합하여 새로운 창의적인 이미지를 생성**할 수 있습니다.  또한, 개체, 액세서리, 재료, 자세, 조명 등 다양한 개념을 처리할 수 있으며, **마스크나 경계 상자 없이도 여러 이미지의 개념을 자유롭게 결합**할 수 있다는 점에서 획기적입니다.  **비지도 학습 방식**을 통해 이러한 개념들을 분리하고 표현함으로써, 사용자는 다양한 시각적 요소들을 유연하게 조합하고 새로운 이미지를 생성하는 데 있어 탁월한 제어력을 확보할 수 있습니다.  결론적으로, TokenVerse는 **다양한 시각적 개념들을 효과적으로 다루고 사용자 제어 기능을 향상**시킨 혁신적인 텍스트-이미지 생성 모델로 평가될 수 있습니다.

#### Multi-Concept Personalization
본 논문에서 다루는 핵심 개념인 "다중 개념 개인화 (Multi-Concept Personalization)"는 **단일 이미지에서 여러 개의 시각적 개념을 분리하고 학습하여, 이를 유연하게 조합하여 새로운 이미지를 생성하는 기법**을 의미합니다. 기존의 개인화 기법들이 주로 단일 개념 또는 제한된 개념 조합에 초점을 맞춘 것과 달리, 본 연구는 **다양하고 복잡한 시각적 요소들을 (물체, 액세서리, 소재, 자세, 조명 등) 효과적으로 분리하고 독립적으로 표현**할 수 있는 방법을 제시합니다.  **이를 통해 사용자는 여러 이미지에서 추출된 개념들을 자유롭게 결합하여 창의적인 이미지를 생성**할 수 있으며, **기존 방법들보다 훨씬 다양하고 유연한 개인화가 가능**합니다. 특히, 단일 이미지만으로도 복수의 개념을 효과적으로 분리하는 능력은 이 기법의 가장 큰 강점이며,  이는 **텍스트-이미지 확산 모델의 모듈레이션 공간을 활용하여 구현**됩니다. 따라서, 단순히 개체만이 아닌 **자세, 조명, 소재 등 비(非)-객체 개념도 개인화**할 수 있다는 점이 중요한 차별점입니다.

#### Modulation Space Control
본 논문에서 제시된 ‘변조 공간 제어(Modulation Space Control)’는 **텍스트-이미지 생성 모델의 변조 공간 내에서 개별 토큰에 대한 제어를 통해 다양한 개념들을 분리하고 조합하는 기법**을 의미합니다.  기존 연구들과 달리, **마스크나 추가적인 지도 없이도 단일 이미지에서 여러 개념들을 분리**해 낼 수 있으며, **다양한 이미지들에서 추출된 개념들을 유연하게 결합하여 새로운 이미지를 생성**할 수 있다는 점이 핵심입니다.  이는 **개별 토큰에 대한 변조 벡터(modulation vector)를 최적화**하여 달성되는데, 이는 해당 토큰이 표현하는 시각적 요소를 개별적으로 조절할 수 있게 해줍니다.  **개념의 독립적 학습과 조합을 위한 최적화 기법**은 논문의 핵심적인 기여이며, **다양한 시각적 요소(객체, 액세서리, 소재, 자세, 조명 등)**에 대한 유연한 개인화를 가능하게 합니다.  하지만, 이러한 **세밀한 제어는 여러 이미지에서 추출된 개념들이 서로 간섭하는 문제**를 야기할 수 있으며, 이를 해결하기 위한 **개념 분리 손실(concept isolation loss)**이 제시되어 있습니다.  **결론적으로, 변조 공간 제어는 텍스트-이미지 생성 모델의 활용 범위를 획기적으로 확장**시키는 잠재력을 가지고 있으며, 스토리텔링, 개인화된 콘텐츠 생성 등 다양한 분야에 응용될 수 있습니다.

#### Concept Isolation
본 논문에서 제시된 "컨셉 분리(Concept Isolation)" 전략은 **다중 컨셉 이미지에서 개별 컨셉을 효과적으로 분리하고 표현하는 데 초점**을 맞춥니다.  이를 위해, **각 텍스트 토큰에 대해 개별적인 변조 벡터(modulation vector)를 최적화**하는 방식을 사용하여 각 컨셉에 대한 독립적인 표현을 학습합니다. 이는 기존 방식들처럼 공간적 마스크나 바운딩 박스에 의존하지 않고, 오로지 캡션 정보만을 활용하여 비지도 학습 방식으로 컨셉 분리를 달성합니다.  **텍스트 토큰 변조 공간(M+)**을 활용함으로써, 특정 텍스트 토큰에 대한 변조만으로 해당 컨셉에 국한된 변화를 유도하며 **컨셉 간의 간섭을 최소화**합니다.  더 나아가, **개별 블록 최적화와 컨셉 분리 손실 함수(concept isolation loss)**를 통해 컨셉 표현의 정확도와 독립성을 더욱 향상시킵니다.  **결과적으로, 다양한 컨셉의 조합 및 재구성을 가능하게 하는 모듈식 접근 방식**을 제시하며, 이는 이미지 내 겹치는 개체나 비개체 컨셉(자세, 조명, 재질 등)의 처리에도 효과적임을 보여줍니다.

#### Future Work & Limits
본 논문은 다중 개념 개인화를 위한 혁신적인 방법인 TokenVerse를 제시하지만, **여전히 개선의 여지가 있는 몇 가지 제한점**이 존재합니다.  향후 연구 방향으로는 **개별 개념 이미지에 대한 학습 과정을 개선**하여, 개념 간의 혼동을 최소화하는 것이 중요합니다.  **다양한 유형의 개념을 더욱 효과적으로 다루기 위한 추가적인 연구**도 필요합니다. 예를 들어, **복잡한 포즈나 중첩된 개체 등의 경우**에 대한 처리 성능을 향상시키는 것이 과제입니다. 또한, **비교적 소규모의 데이터셋을 사용**했기 때문에, 보다 **대규모의 데이터셋을 이용한 실험**을 통해 TokenVerse의 일반화 성능을 평가하고 개선하는 것이 필요합니다. 마지막으로, **다른 생성 모델이나 멀티모달 모델과의 통합**을 통해 TokenVerse의 활용 범위를 확장하는 연구가 이루어져야 할 것입니다. 이러한 제한점들을 해결하고 개선함으로써, TokenVerse는 더욱 강력하고 유용한 다중 개념 개인화 도구로 발전할 수 있을 것입니다.  **특히, 다양한 응용 분야에서의 활용성을 높이기 위한 추가적인 연구가 필요**합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.12224/x3.png)

> 🔼 그림 2는 전역 변조 공간(ℳ)과 토큰별 변조 공간(ℳ+)에서의 방향을 보여줍니다. 생성된 이미지(맨 위 행)가 주어지면, ℳ과 ℳ+ 공간 모두에서 텍스트 기반 방향을 사용하여 이미지를 수정합니다. (a) 모든 텍스트 및 이미지 토큰을 변조하는 데 사용되는 벡터에 방향을 추가하면(즉, ℳ 공간의 방향) 생성된 이미지에서 원하는 개념을 효과적으로 수정할 수 있습니다. 그러나 이는 종종 다른 개념에도 영향을 미치는 비국소적 변경으로 이어집니다. (b) 특정 텍스트 토큰(예: “강아지” 또는 “공”)의 변조 벡터에만 방향을 추가하면(즉, ℳ+ 공간의 방향) 관심 개념에 주로 영향을 미치는 국소적 수정이 가능합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Directions in the global modulation space (ℳℳ\mathcal{M}caligraphic_M) and our per-token modulation space (ℳ+superscriptℳ\mathcal{M}^{+}caligraphic_M start_POSTSUPERSCRIPT + end_POSTSUPERSCRIPT).  Given a generated image (top row), we modify it using text-driven directions in both ℳℳ\mathcal{M}caligraphic_M and ℳ+superscriptℳ\mathcal{M}^{+}caligraphic_M start_POSTSUPERSCRIPT + end_POSTSUPERSCRIPT spaces. (a) Adding a direction to the vector that is used to modulate all the text and image tokens (i.e. a direction in the space ℳℳ\mathcal{M}caligraphic_M) can be used to effectively modify desired concepts in the generated image. Yet, this often results in non-local changes that also affect other concepts in the generated image. (b) Adding a direction only to the modulation vector of a specific text token, like “dog” or “ball” (i.e. a direction in the space ℳ+superscriptℳ\mathcal{M}^{+}caligraphic_M start_POSTSUPERSCRIPT + end_POSTSUPERSCRIPT) leads to a localized modification that mostly affects the concept of interest.
> </details>



![](https://arxiv.org/html/2501.12224/x4.png)

> 🔼 그림 3은 TokenVerse의 개요를 보여줍니다. (a)는 사전 훈련된 텍스트-이미지 DiT 모델이 DiT 블록의 연속을 통해 이미지 및 텍스트 토큰을 처리하는 과정을 보여줍니다. 각 블록은 변조, 어텐션 및 피드포워드 모듈로 구성되며, 토큰은 풀링된 텍스트 임베딩에서 파생된 벡터 y를 통해 변조됩니다. (b)는 개념 이미지와 해당 캡션이 주어지면 TokenVerse가 각 텍스트 토큰에 대해 개인화된 변조 벡터 오프셋 Δ를 학습하는 과정을 보여줍니다. 이러한 오프셋은 변조 공간에서 개인화된 방향을 나타내며, 간단한 재구성 목표를 사용하여 학습됩니다. (c)는 추론 시 사전 학습된 방향 벡터를 사용하여 텍스트 토큰을 변조하여 개인화된 개념을 생성된 이미지에 주입하는 과정을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: TokenVerse overview. (a) A pre-trained text-to-image DiT model processes both image and text tokens via a series of DiT blocks. Each block consists of modulation, attention and feed-forward modules. We focus on the modulation block, in which the tokens are modulated via a vector y𝑦yitalic_y, which is derived from a pooled text embedding. (b) Given a concept image and its corresponding caption, TokenVerse learns a personalized modulation vector offset ΔΔ\Deltaroman_Δ for each text token. These offsets represent personalized directions in the modulation space and are learned using a simple reconstruction objective. (c) At inference, the pre-learned direction vectors are used to modulate the text tokens, enabling the injection of personalized concepts into the generated images.
> </details>



![](https://arxiv.org/html/2501.12224/x5.png)

> 🔼 그림 4는 개념 분리 손실에 대한 설명입니다. Concept-Mod를 훈련시킬 때, 훈련 단계의 50%에서 추가적인 개념 분리 손실을 적용합니다. 이 손실은 방향의 영향을 받지 않아야 하는 이미지 영역이 유사하게 유지되도록 함으로써 다른 이미지와 간섭하지 않는 방향을 학습하도록 합니다.  즉, 특정 개념을 표현하는 방향 벡터가 다른 개념에 영향을 주지 않고 해당 개념만 정확하게 변형하도록 훈련하는 것을 목표로 합니다.  이는 특정 개념에 대한 수정이 이미지의 다른 부분에 영향을 미치는 것을 방지하기 위해 개념 간의 독립성을 높이는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Concept isolation loss. When training Concept-Mod we apply an additional concept isolation loss in 50% of the training steps. This loss encourages learning directions that do not interfere with other images by enforcing that the parts in the image that should not be affected by the directions remain similar.
> </details>



![](https://arxiv.org/html/2501.12224/x6.png)

> 🔼 본 그림은 TokenVerse 모델의 질적 결과를 보여줍니다. 각 행은 네 개의 개념 이미지로 시작하며, 이러한 이미지로부터 TokenVerse 방법이 개념들을 독립적으로 추출하는 과정을 보여줍니다. 오른쪽에는 세 개의 생성된 이미지가 표시되는데, 이는 추출된 개념들을 새롭고 일관성 있는 출력물로 원활하게 결합하여 생성한 결과물입니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Qualitative results. Each row begins with a bank of four source images, from which our method independently extracts concepts. To the right, three generated images are shown, demonstrating the seamless combination of these concepts into new, coherent outputs.
> </details>



![](https://arxiv.org/html/2501.12224/x7.png)

> 🔼 그림 6은 TokenVerse 모델이 여러 개념을 결합하여 이미지를 생성하는 능력을 보여줍니다.  기존 방법들과 달리, TokenVerse는 이미지에 결합될 수 있는 개념의 수에 기술적인 제한이 없습니다. 이 그림은 다양한 개념 요소(사람, 동물, 의상, 소품, 배경 등)들이 복잡하게 조합된 이미지들을 보여주며, TokenVerse가 얼마나 다양하고 복잡한 시각적 개념들을 효과적으로 생성하는지 보여줍니다.  각 이미지는 여러 개의 개념 이미지에서 추출된 개념들을 조합하여 만들어졌으며, 개별 요소들이 명확하게 구분되어 있으면서도 자연스럽게 통합되어 있습니다. 이는 TokenVerse가 개념들을 효과적으로 분리하고 조합하는 능력을 시각적으로 보여주는 좋은 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Extreme multi-concept personalization. Our method has no technical constraint on the number of concepts that can be combined in an image. As can be seen, TokenVerse can generate images composing a significant number of concepts.
> </details>



![](https://arxiv.org/html/2501.12224/x8.png)

> 🔼 그림 7은 개체(곰, 개념 이미지는 표시되지 않음), 자세(왼쪽 열), 조명(위쪽 행)의 세 가지 유형의 개인화된 개념 조합을 보여줍니다. TokenVerse는 포즈를 취한 사람의 신원이나 특정 조명 장면에 과적합되지 않고 자세와 조명을 성공적으로 학습합니다.  즉, TokenVerse는 사물 뿐만 아니라 자세나 조명 등의 비사물 개념도 개인화할 수 있음을 보여줍니다.  다양한 개인화된 개념들을 조합하여 새로운 이미지를 생성할 수 있는 TokenVerse의 능력을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Concepts beyond objects. We demonstrate the composition of three types of personalized concepts: object (the bear; concept image not shown), pose (left column) and lighting (top row). TokenVerse successfully learns the pose and lighting without overfitting to the identity of the poser or the specific lit scene.
> </details>



![](https://arxiv.org/html/2501.12224/x9.png)

> 🔼 그림 8은 다섯 가지 방법(ConceptExpress, BAS, DreamBooth, OMG 및 본 연구의 방법)을 사용하여 생성된 이미지를 보여줍니다. 각 행은 두 개의 개념 이미지(왼쪽)와 이러한 개념의 조합을 포함하는 이미지를 보여줍니다. 녹색과 파란색 단어와 관련된 개념은 각각 왼쪽과 오른쪽 개념 이미지에서 가져온 것입니다. 이 그림은 본 연구의 방법이 개념 충실도를 유지하면서 두 개념을 최상으로 조합한다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Qualitative comparisons. Each row depicts two concept images (left) and images containing a combination of those concepts, generated by ConceptExpress [14], BAS [8], DreamBooth [32], OMG [23] and our method. The concepts associated with the green and blue words are taken from the left and right concept images, respectively. As can be seen, our method best composes the two concepts while preserving concept fidelity.
> </details>



![](https://arxiv.org/html/2501.12224/x10.png)

> 🔼 그림 9는 제시된 방법과 다른 기준 방법들을 정량적으로 비교한 결과를 보여줍니다. DreamBench++와 사용자 연구를 통해 개념 보존 및 프롬프트 충실도(높을수록 좋음) 측면에서 비교 분석했습니다. (a)에서는 세 가지 다른 설정(i) 서로 다른 이미지에서 두 가지 개념을 결합하는 개념 구성, (ii) 동일한 이미지에서 두 가지 개념을 분리하는 개념 분해, (iii) 두 가지 작업의 조합(전체 작업)을 비교 분석했습니다. (b)에서는 전체 작업에 대해 제시된 방법과 기존 방법들을 사용자 연구를 통해 비교했습니다. 제시된 방법은 개념 보존 측면에서 일관되게 최고 점수를 받았으며, 프롬프트 충실도 점수 또한 높게 유지했습니다. 자세한 수치는 부록 C.2를 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Figure 9: Quantitative comparison. We compare our method to other baselines on concept preservation and prompt fidelity (higher is better) using DreamBench++ and a user study. (a) We compare three different settings: (i)𝑖(i)( italic_i ) composing two concepts from different images (concept composition), (i⁢i)𝑖𝑖(ii)( italic_i italic_i ) decomposing two concepts from the same image (concept decomposition), and (i⁢i⁢i)𝑖𝑖𝑖(iii)( italic_i italic_i italic_i ) the combination of the two (full task). (b) We conduct a user study, comparing our method to existing methods on our full task. Our method consistently scores best in terms of concept preservation while maintaining high prompt fidelity scores. See App. C.2 for the exact metrics.
> </details>



![](https://arxiv.org/html/2501.12224/x11.png)

> 🔼 그림 10은 제안된 방법의 각 구성 요소의 기여도를 보여주는 비교 실험 결과를 보여줍니다. 왼쪽에는 결과 이미지를 생성하는 데 사용된 모든 개념 이미지가 나열되어 있습니다. (a)열부터 (d)열까지는 제안된 방법에 구성 요소가 추가됨에 따라 결과가 어떻게 달라지는지를 보여줍니다. (a)는 입력 텍스트 토큰에 대한 오프셋을 적용하는 방법을, (b)는 M+ 공간에서 오프셋을 적용하는 방법을, (c)는 블록별 오프셋을 추가하는 방법을, 그리고 (d)는 분리 손실을 추가한 전체 방법을 각각 보여줍니다. 이를 통해 M+ 공간 사용, 블록별 오프셋 적용, 그리고 분리 손실 추가가 개념 보존에 미치는 영향을 시각적으로 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Ablations. The left pane shows all the concepts used to generate the result images. Columns (a) to (d) shows the results of our method as additional components are progressively integrated.
> </details>



![](https://arxiv.org/html/2501.12224/x12.png)

> 🔼 그림 11은 TokenVerse 모델의 한계를 보여줍니다.  각 행은 여러 개념의 이미지와 TokenVerse를 사용하여 생성된 이미지를 보여줍니다. TokenVerse는 개념의 분리 학습과 다중 개념 구성 모두를 지원하지만, 여전히 몇 가지 한계가 있습니다. (a) 독립적인 개념 학습으로 인해 특정 조합에서 드물게 혼합이 발생할 수 있습니다.  (App. F 참조). (b) 같은 이름을 가진 개념을 사용할 경우 문제가 발생할 수 있지만, 다른 용어를 사용하면 완화할 수 있습니다. (c) 작은 팔다리를 가진 인형이 복잡한 자세를 취하는 것과 같이 특정한 조합은 원치 않는 결과를 초래할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Limitations. Concept images are shown in the top row, with the generated images using TokenVerse below in each case. While our method supports both disentangled learning and multi-concept composition, limitations remain. (a) Rare blending can occur in specific combinations due to independent training of concepts; We provide analysis and mitigations in App. F. (b) Challenges arise with concepts sharing the same name identifier, which can be mitigated by using distinct terms. (c) Certain incompatible combinations, such as a doll with tiny limbs in a complex pose, may result in undesired outputs.
> </details>



![](https://arxiv.org/html/2501.12224/x13.png)

> 🔼 그림 12는 증강 기법의 효과를 보여주는 비교 실험 결과입니다. 위쪽 행에는 결과 이미지 생성에 사용된 개념 이미지들이 나열되어 있습니다. (a)열은 본 논문에서 제시된 전체 방법론을 적용한 결과를, (b)열은 텍스트 및 이미지 증강 기법 없이 생성한 결과를 보여줍니다.  이를 통해 텍스트와 이미지 증강이 최종 결과 이미지 품질 향상에 미치는 영향을 명확하게 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Augmentations Ablation. The top row shows the concepts used to generate the result images. Column (a) displays the results of our full method, while column (b) shows the results without text and image augmentations.
> </details>



![](https://arxiv.org/html/2501.12224/x14.png)

> 🔼 그림 13은 TokenVerse를 사용하여 생성된 이미지에 개념을 점진적으로 추가하는 방법을 보여줍니다. 텍스트를 통해 생성된 이미지의 다른 모든 측면을 제어하면서 말이죠. 각 행에서 개체, 자세, 조명, 머리카락이 개별화되고, 배경은 텍스트로 설명됩니다(예: 맨 위 행의 경우 “뉴욕시”, “정원”, “화성”). 이 그림은 TokenVerse가 개별 이미지에서 추출한 여러 개념을 새로운 창의적인 구성으로 유연하게 통합하는 능력을 보여줍니다.  각 행은 개별 개념 이미지의 다양한 조합을 보여주는 세 개의 생성된 이미지와 함께 시작합니다. TokenVerse는 각 개념 이미지를 독립적으로 처리하고, 추가적인 감독이나 마스크 없이도 캡션에 따라 개념을 분리하는 방법을 학습합니다. 이는 여러 이미지에서 추출된 개인화된 텍스트 토큰을 새로운 텍스트 프롬프트에 유연하게 통합하여 새로운 창의적인 이미지를 생성하기 때문에 가능합니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: Progressive composition of concepts. TokenVerse can be used to progressively add concepts into a generated image, while controlling all other aspects of the generated images via text. In each row, the object, pose, lighting, and hair are personalized, while the background is described by text (e.g. “NY city”, “garden”, and “Mars” for the top row.)
> </details>



![](https://arxiv.org/html/2501.12224/x15.png)

> 🔼 그림 14는 모델이 개별적으로 학습된 개념들을 결합할 때 발생할 수 있는 문제점을 보여줍니다. (a)는 인형과 강아지처럼 서로 다른 두 개체를 하나의 이미지에 결합하는 일반적인 시나리오를 보여줍니다. (b)는 개념들을 독립적으로 학습시킬 경우 혼합된 개체가 생성되는 실패 사례를 보여줍니다. (c)는 두 개념을 함께 학습시켜 이러한 문제를 완화하는 방법을 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: Limitation – highly similar modulated tokens. (a) The common scenario of combining two distinct objects, such as a doll and a dog, into a single image. (b) A failure case where independent training of concepts leads to the creation of hybrid objects. (c) A potential mitigation for this issue by employing joint training on both concepts.
> </details>



![](https://arxiv.org/html/2501.12224/x16.png)

> 🔼 그림 15는 TokenVerse 모델의 한계를 보여줍니다. 특히, 같은 이름의 개체가 여러 개 있는 경우(예: 두 개의 인형), 모델이 제대로 작동하지 않을 수 있습니다. (a)는 이러한 문제가 발생하는 경우를 보여줍니다. 하지만 초기 학습 단계에서 각 개체에 고유한 식별자를 할당하면(예: 인형1, 인형2) 이 문제를 해결할 수 있습니다. (b)는 고유한 식별자를 사용하여 문제를 해결한 결과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 15: Limitations – colliding captions. Our method may fail when handling cases of colliding identifiers, such as two dolls (a). This issue can be easily resolved by assigning distinct identifiers to each object during the initial training (b).
> </details>



![](https://arxiv.org/html/2501.12224/x17.png)

> 🔼 그림 16은 TokenVerse 모델의 질적 결과를 보여줍니다. 각 행에는 두 개의 생성 이미지와 해당 이미지에 사용된 개념의 원본 이미지가 함께 표시됩니다. 이 그림은 TokenVerse가 여러 개념 이미지에서 개별 개념을 추출하고 이를 새로운 조합으로 결합하여 새로운 이미지를 생성할 수 있는 능력을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 16: Qualitative results. Each row contains two result images and the source images of the concepts that they contain.
> </details>



![](https://arxiv.org/html/2501.12224/x18.png)

> 🔼 그림 17은 TokenVerse 모델의 질적 결과를 보여줍니다. 각 행은 두 개의 생성된 이미지와 해당 이미지를 생성하는 데 사용된 개념 이미지들을 보여줍니다. 생성된 이미지들은 여러 개념 이미지들로부터 추출된 다양한 시각적 요소들의 독창적이고 다채로운 조합을 보여줍니다. 이를 통해 사용자는 원하는 시각적 요소들을 조합하여 새로운 창의적인 이미지를 생성할 수 있음을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 17: Qualitative results. Each row contains two result images and the source images of the concepts that they contain.
> </details>



![](https://arxiv.org/html/2501.12224/x19.png)

> 🔼 그림 18은 TokenVerse 모델의 질적 결과를 보여줍니다. 각 행은 두 개의 결과 이미지와 해당 이미지에 사용된 개념의 원본 이미지를 보여줍니다.  이 그림은 TokenVerse가 다양한 개념들을 성공적으로 결합하여 새로운 창의적인 이미지를 생성할 수 있음을 보여주는 여러 예시들을 제공합니다. 각각의 결과 이미지는 여러 개념 이미지로부터 추출된 개념들을 독창적인 방식으로 결합하여 생성되었습니다. 원본 이미지들은 다양한 개념 요소들을 포함하고 있으며, TokenVerse는 이러한 개념들을 성공적으로 분리하고 새로운 조합으로 결합하는 능력을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 18: Qualitative results. Each row contains two result images and the source images of the concepts that they contain.
> </details>



![](https://arxiv.org/html/2501.12224/x20.png)

> 🔼 그림 19는 제시된 방법을 이용한 스토리텔링 애플리케이션의 활용성을 보여주는 결과입니다. 그림 왼쪽에는 스토리에 등장하는 등장인물, 배경, 자세 등이 나열되어 있으며, 오른쪽에는 대형 언어 모델(LLM)을 사용하여 생성된 스토리가 제시되어 있습니다. 생성된 스토리는 다시 LLM을 통해 이미지 생성 프롬프트로 재처리되었으며, 이 프롬프트를 사용하여 첨부된 이미지들이 생성되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 19: Storytelling results. Demonstration of our method’s usability for storytelling applications. All the characters, scenes, and poses featured in the story are shown on the left. On the right is the story itself, generated by a language model (LLM). This story was then reprocessed by the LLM to generate prompts, which were used to create the accompanying images.
> </details>



![](https://arxiv.org/html/2501.12224/x21.png)

> 🔼 그림 20은 사용자 연구에서 질문한 예시 질문들을 보여줍니다. 생성된 이미지가 주어지면 사용자들은 텍스트와 입력 개념 모두와의 정렬에 대해 평가하라는 질문을 받게 됩니다.  구체적으로는 생성된 이미지가 주어진 텍스트 설명과 얼마나 잘 일치하는지, 그리고 입력 개념(예: 셔츠, 안경)이 생성된 이미지에 얼마나 잘 나타나는지를 1점에서 5점 척도로 평가합니다.
> <details>
> <summary>read the caption</summary>
> Figure 20: An example of the questions asked in the user study. Given a generated image the users are asked about its alignment with both the text and the input concepts
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Metric | Composition CP ↑ | Composition PF ↑ | Composition CP ⋅ PF ↑ | Decomposition CP ↑ | Decomposition PF ↑ | Decomposition CP ⋅ PF ↑ | Full task CP ↑ | Full task PF ↑ | Full task CP ⋅ PF ↑ |
|---|---|---|---|---|---|---|---|---|---| 
| Dreambooth | 0.280242 | **0.844422** | 0.236642 | **0.668524** | 0.660167 | **0.441337** | 0.207116 | **0.827521** | 0.171393 |
| DreamBoothjoint | 0.371304 | 0.619288 | 0.229944 | **0.668524** | 0.660167 | **0.441337** | 0.306262 | 0.591337 | 0.181104 |
| OMG | 0.238606 | **0.743968** | 0.177515 | 0.267477 | **0.791793** | 0.211787 | 0.207787 | **0.843395** | 0.175246 |
| Break-A-Scenejoint | **0.392912** | 0.372664 | 0.154380 | 0.598387 | 0.641935 | 0.384126 | **0.499054** | 0.641236 | **0.320011** |
| ConceptExpress | 0.214718 | 0.548723 | 0.117821 | 0.246387 | 0.695087 | 0.171260 | 0.187853 | 0.733286 | 0.137750 |
| Ours | **0.470108** | 0.688061 | **0.323463** | **0.669940** | **0.747698** | **0.500431** | **0.553125** | 0.821875 | **0.454600** |{{< /table-caption >}}
> 🔼 표 2는 본 논문의 정량적 비교 그래프를 보완하여 개념 보존(CP) 및 프롬프트 충실도(PF)의 정확한 측정값을 제시합니다.  DreamBench++ 평가 지표를 사용하여, 다양한 방법들의 개념 보존 및 프롬프트 충실도 성능을 정확한 수치로 비교 분석합니다.  구체적으로,  각 방법에 대해 개념 구성, 개념 분해, 전체 작업 세 가지 상황에서의 CP와 PF 값을 제시하며, 이를 통해 각 방법의 강점과 약점을 명확하게 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2:  Dreambench++ Evaluation We complement the quantitative comparison graphs of the main paper with the exact measurements of concept preservation (CP) and prompt fidelity (PF).
> </details>

{{< table-caption >}}
| Metric | CP ↑ | PF ↑ |
|---|---|---|
| Dreambooth | 2.2505 | **4.465** |
| DreamBooth<sub>joint</sub> | 2.7582 | 3.462 |
| OMG | 2.205 | 3.611 |
| Break-A-Scene<sub>joint</sub> | **3.203** | 3.151 |
| ConceptExpress | 2.211 | 2.686 |
| Ours | **4.078** | **4.292** |{{< /table-caption >}}
> 🔼 본 논문의 사용자 연구 결과 그래프를 보완하여 개념 보존 및 프롬프트 충실도에 대한 정확한 측정값을 제공하는 표입니다. 사용자 연구에서 참가자들은 생성된 이미지가 프롬프트와 얼마나 잘 일치하는지, 그리고 생성된 이미지에 원본 개념이 얼마나 잘 보존되는지를 평가했습니다. 이 표는 그러한 평가 결과를 수치적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3:  User Study We complement the user study results graphs of the main paper with the exact measurements of concept preservation and prompt fidelity.
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