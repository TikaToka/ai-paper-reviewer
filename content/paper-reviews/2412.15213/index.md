---
title: "Flowing from Words to Pixels: A Framework for Cross-Modality Evolution"
summary: "CrossFlow: 모달리티 간 직접적 변환 가능한 혁신적 프레임워크!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Vision-Language Models", "🏢 GenAI, Meta",]
showSummary: true
date: 2024-12-19
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.15213 {{< /keyword >}}
{{< keyword icon="writer" >}} Qihao Liu et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-20 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.15213" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.15213" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/flowing-from-words-to-pixels-a-framework-for" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 텍스트-이미지 생성 모델들은 복잡한 노이즈 기반 확산 과정이나 조건화 메커니즘을 사용하여, 훈련 및 추론 과정이 복잡하고 비효율적이었습니다. 또한, 특정 작업에 맞춰 아키텍처를 변경해야 하는 한계가 있었습니다. 

본 논문에서는 이러한 문제를 해결하기 위해 CrossFlow라는 새로운 프레임워크를 제시합니다. CrossFlow는 **변분 인코더(Variational Encoder)**를 사용하여 입력 데이터의 분포를 표준화하고, **크로스 어텐션 없이 일반적인 트랜스포머를 활용**하여 모달리티 간의 직접적인 매핑을 학습합니다.  **분류자 없는 가이드(Classifier-free guidance)** 기법을 적용하여 생성 품질을 향상시켰으며, 텍스트-이미지 생성뿐 아니라 이미지 캡셔닝, 깊이 추정, 이미지 초고해상도화 등 다양한 작업에서 최첨단 성능을 달성했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} CrossFlow는 노이즈 없이 모달리티 간 직접 변환을 가능하게 하는 새로운 프레임워크입니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 텍스트-이미지 생성을 비롯한 다양한 크로스-모달 및 인트라-모달 작업에서 최첨단 성능을 달성했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 단순한 아키텍처에도 불구하고 우수한 확장성과 효율성을 보여줍니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **다양한 모달리티 간의 매핑을 위한 일반적이고 간단한 프레임워크인 CrossFlow를 제시**합니다. 이는 기존의 노이즈 기반 확산 모델의 한계를 극복하고, **모달리티 간의 직접적인 변환을 가능하게** 합니다.  **다양한 크로스-모달 및 인트라-모달 작업에 대한 우수한 성능**을 보여주는 본 연구는 **미디어 생성 분야의 발전에 크게 기여**할 뿐만 아니라, **향후 연구의 새로운 방향을 제시**할 것입니다. 특히, **단순한 아키텍처로 우수한 성능을 달성**하여 효율성 측면에서도 강점을 가지고 있습니다.  이는 **컴퓨팅 자원이 제한적인 연구자들에게 매우 유용**할 것입니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.15213/x2.png)

> 🔼 본 그림은 논문에서 제안하는 CrossFlow 프레임워크를 보여줍니다. CrossFlow는 흐름 매칭(flow matching)을 사용하여 추가적인 조건 없이 한 모달리티를 다른 모달리티로 직접 변환하는 간단하고 일반적인 프레임워크입니다.  크로스 어텐션 없이 일반적인 트랜스포머를 사용하여 (a) 텍스트-이미지 생성과 같은 다양한 작업에서 최첨단 모델과 비교할 만한 성능을 달성합니다.  (b) 특정 작업에 맞는 아키텍처가 필요하지 않습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: We propose CrossFlow, a general and simple framework that directly evolves one modality to another using flow matching with no additional conditioning. This is enabled using a vanilla transformer without cross-attention, achieving comparable performance with state-of-the-art models on (a) text-to-image generation, and (b) various other tasks, without requiring task specific architectures.
> </details>





{{< table-caption >}}
| Method | #Params (B) | #Steps (K) | FID ↓ | CLIP ↑ |
|---|---|---|---|---|
| Standard FM (Baseline) | 1.04 | 300 | 10.79 | 0.29 |
| CrossFlow (Ours) | 0.95 | 300 | 10.13 | 0.29 |{{< /table-caption >}}

> 🔼 표 1은 제안된 CrossFlow 모델과 교차 어텐션을 사용하는 표준 흐름 매칭 모델의 성능을 비교한 표입니다. 두 모델 모두 동일한 설정으로 훈련되었으며, CrossFlow 모델이 제로샷 FID-30K 지표에서 표준 흐름 매칭 모델보다 약간 우수한 성능을 보였고, CLIP 점수에서는 비슷한 성능을 달성했습니다.  이 표는 두 모델의 성능 차이가 크지 않지만, CrossFlow 모델이 더 효율적일 수 있음을 시사합니다. 특히, CrossFlow는 교차 어텐션 계층 없이도 비슷한 성능을 달성하여, 모델의 복잡성을 줄이고 훈련 효율을 높일 수 있는 가능성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparison between our CrossFlow and standard flow matching with cross-attention. Both models are trained with the same settings. We find that our model slightly outperforms standard flow matching baseline in terms of zero-shot FID-30K and achieves comparable performance on the CLIP score.
> </details>





### In-depth insights


#### CrossFlow Framework
CrossFlow 프레임워크는 **단일 모달리티에서 다른 모달리티로의 직접적인 변환**을 가능하게 하는 혁신적인 접근 방식을 제시합니다. 기존의 잡음 기반 확산 모델과 달리, CrossFlow는 **소스 모달리티의 분포를 직접 타겟 모달리티의 분포로 매핑**하는 방식을 채택하여, 잡음 분포 및 조건화 메커니즘에 대한 의존성을 제거합니다. 이를 통해 단순하고 일반화된 구조를 가지면서도 **다양한 크로스-모달리티 작업**에서 우수한 성능을 달성합니다. 특히, 변분적 인코더(Variational Encoder)를 활용하여 **모달리티 간의 차이를 해소**하고, 분류기 없는 안내(Classifier-free guidance) 기법을 도입하여 생성 품질을 향상시키는 것이 주요 특징입니다.  **크로스 어텐션 없이도 우수한 성능**을 보이며, 모델 크기와 훈련 단계에 대한 확장성이 뛰어나다는 점도 중요한 강점입니다.  **잠재 공간 연산**을 지원하여 의미있는 잠재적 수학적 조작을 가능하게 하여 모델의 유연성과 활용도를 높였습니다.

#### VE & CFG Methods
본 논문에서 제시된 VE(Variational Encoder)와 CFG(Classifier-free Guidance) 방법론은 텍스트-이미지 생성 모델의 성능 향상에 중추적인 역할을 합니다.  **VE는 서로 다른 모달리티(텍스트와 이미지)의 데이터 분포 차이를 해소**하여, **흐름 일치(flow matching) 모델이 효과적으로 학습할 수 있도록 돕는 전처리 과정**으로 작용합니다.  즉, 텍스트 특징을 이미지 특징과 유사한 형태로 변환하여, 흐름 일치 모델이 직접적으로 한 모달리티에서 다른 모달리티로의 매핑을 학습하도록 지원합니다.  **CFG는 생성 과정에서 조건부(conditional) 및 무조건부(unconditional) 생성 결과를 혼합하여 이미지 품질을 향상**시키는 기술입니다.  이 방법은 기존 흐름 일치 모델에서 조건부 정보를 추가하는 대신, **훈련 과정에 이진 조건부 표시기를 도입**함으로써,  **별도의 조건부 메커니즘 없이도 CFG 효과를 구현**합니다.  **VE와 CFG의 결합**은 단순하면서도 효과적인 텍스트-이미지 생성 프레임워크를 가능하게 하며,  **다양한 크로스-모달/인트라-모달 작업에 적용 가능성**을 보여줍니다.  **특히,  교차 어텐션 없이도 우수한 성능**을 달성한 점은 주목할 만하며,  모델 크기 및 훈련 단계에 대한 확장성 또한 뛰어나다는 것을 보여줍니다.

#### T2I Experiments
본 논문의 "T2I Experiments" 부분은 텍스트-이미지 생성 모델의 성능을 평가하기 위한 다양한 실험들을 제시합니다. **기존의 텍스트-이미지 생성 모델들과의 비교 실험**을 통해 제안된 CrossFlow 모델의 우수성을 보여주는 것이 주요 목표입니다.  **다양한 규모의 모델과 훈련 반복 횟수에 따른 성능 변화 분석**을 통해 CrossFlow의 확장성을 검증하고, **다른 최첨단 모델들과의 비교**를 통해 경쟁력을 입증하는 방식으로 실험이 구성됩니다.  단순한 성능 비교뿐 아니라, **잠재 공간(latent space) 연산을 통한 이미지 편집 가능성**을 보여주는 실험도 포함되어 있으며,  **다양한 언어 모델들과의 호환성**도 확인합니다.  이러한 실험들은 CrossFlow 모델의 강점과 약점을 명확하게 드러내어, **향후 텍스트-이미지 생성 기술 발전에 중요한 통찰력**을 제공합니다. 특히, 잠재 공간 연산 실험은 CrossFlow가 **이미지 생성 과정에 대한 더욱 세밀한 제어**를 가능하게 함을 보여주는 중요한 결과입니다.

#### Latent Arithmetic
본 논문에서 제시된 '잠재적 연산(Latent Arithmetic)' 개념은 **매우 혁신적**입니다. 기존의 텍스트-이미지 생성 모델들이 노이즈 분포에서 이미지를 생성하는 것과 달리, 본 연구는 **모달 간의 직접적인 매핑을 학습**함으로써, 잠재 공간에서 직접적인 수학적 연산을 가능하게 합니다. 이를 통해 이미지의 의미론적 요소들을 잠재 공간에서 조작하여, **새로운 이미지를 생성하거나 기존 이미지를 편집**하는 강력한 도구를 제공합니다.  **예를 들어, 잠재 공간에서 "모자를 쓴 강아지" 벡터에서 "모자" 벡터를 빼고 "선글라스" 벡터를 더하면 "선글라스를 쓴 강아지" 이미지가 생성**될 수 있습니다. 이러한 잠재적 연산은 이미지 생성의 창의성과 유연성을 크게 향상시키며, **기존의 조건화 기법에 의존하지 않고도 의미있는 이미지 조작**을 가능하게 합니다.  하지만, 이러한 잠재 공간의 의미론적 해석과 연산의 정확성에 대한 추가적인 연구가 필요하며, **잠재 공간의 차원 축소 및 정규화** 과정에 대한 더 자세한 설명도 필요할 것으로 보입니다.  **다양한 모달에 적용 가능한 일반적인 프레임워크**를 제공한다는 점에서 높이 평가할 수 있습니다.

#### Future Directions
본 논문에서 제시된 CrossFlow는 잠재적인 가능성을 보여주지만, 향후 연구를 통해 개선될 여지가 많습니다. **다양한 모달리티 간의 매핑 성능 향상**을 위해, 더욱 정교한 변환기(transformer) 구조나 훈련 전략의 개발이 필요합니다. **대규모 데이터셋**을 활용한 추가적인 학습을 통해 일반화 능력을 높일 수 있으며, **다양한 하드웨어 플랫폼**에서의 효율적인 구현 연구도 중요한 과제입니다. 또한, CrossFlow의 잠재 공간 연산의 활용성을 극대화하기 위해, 보다 **직관적이고 효율적인 잠재 공간 조작 도구**의 개발이 요구됩니다. 마지막으로, **다른 생성 모델**과의 통합을 통한 시너지 효과 창출을 위한 연구가 필요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.15213/x3.png)

> 🔼 그림 2는 CrossFlow 아키텍처를 보여줍니다. CrossFlow는 두 가지 다른 모달리티 간의 직접적인 진화를 가능하게 합니다. 텍스트-이미지 생성을 예로 들면, T2I 모델은 텍스트 변분 인코더와 표준 흐름 매칭 모델이라는 두 가지 주요 구성 요소로 구성됩니다. 추론 시에는 텍스트 변분 인코더를 사용하여 언어 모델이 생성한 텍스트 임베딩 x∈ℝ<sup>n×d</sup>에서 텍스트 잠재 변수 z<sub>0</sub>∈ℝ<sup>h×w×c</sup>를 추출합니다. 그런 다음 이 텍스트 잠재 변수를 이미지 공간으로 직접 진화시켜 이미지 잠재 변수 z<sub>1</sub>∈ℝ<sup>h×w×c</sup>를 생성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: CrossFlow Architecture. CrossFlow enables direct evolution between two different modalities. Taking text-to-image generation as an example, our T2I model comprises two main components: a Text Variational Encoder and a standard flow matching model. At inference time, we utilize the Text Variational Encoder to extract the text latent z0∈ℝh×w×csubscript𝑧0superscriptℝℎ𝑤𝑐z_{0}\in\mathbb{R}^{h\times w\times c}italic_z start_POSTSUBSCRIPT 0 end_POSTSUBSCRIPT ∈ blackboard_R start_POSTSUPERSCRIPT italic_h × italic_w × italic_c end_POSTSUPERSCRIPT from text embedding x∈ℝn×d𝑥superscriptℝ𝑛𝑑x\in\mathbb{R}^{n\times d}italic_x ∈ blackboard_R start_POSTSUPERSCRIPT italic_n × italic_d end_POSTSUPERSCRIPT produced by any language model. Then we directly evolve this text latent into the image space to generate image latent z1∈ℝh×w×csubscript𝑧1superscriptℝℎ𝑤𝑐z_{1}\in\mathbb{R}^{h\times w\times c}italic_z start_POSTSUBSCRIPT 1 end_POSTSUBSCRIPT ∈ blackboard_R start_POSTSUPERSCRIPT italic_h × italic_w × italic_c end_POSTSUPERSCRIPT.
> </details>



![](https://arxiv.org/html/2412.15213/x4.png)

> 🔼 그림 3은 모델 파라미터와 반복 횟수에 따른 성능을 보여줍니다.  텍스트 크로스 어텐션을 사용하여 노이즈로부터 시작하는 기준 모델과 CrossFlow를 데이터, 모델 크기, 학습 단계를 동일하게 유지하며 비교합니다. 왼쪽 그래프는 더 큰 모델이 cross-modality 연결을 더 잘 활용할 수 있음을 보여주고, 오른쪽 그래프는 CrossFlow가 수렴하는 데 더 많은 단계가 필요하지만 최종적으로 더 나은 성능에 도달함을 보여줍니다. 전반적으로 CrossFlow는 기준 모델보다 확장성이 뛰어나며 미래의 미디어 생성 모델을 위한 프레임워크 역할을 할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Performance vs. Model Parameters and Iterations. We compare the baseline of starting from noise with text cross-attention with CrossFlow, while controlling for data, model size and training steps. Left: Larger models are able to exploit the cross-modality connection better. Right: CrossFlow needs more steps to converge, but converges to better final performance. Overall, CrossFlow scales better than the baseline and can serve as the framework for future media generation models.
> </details>



![](https://arxiv.org/html/2412.15213/x5.png)

> 🔼 그림 4는 CrossFlow 모델이 잠재 공간에서 매끄러운 보간을 제공하는 것을 보여줍니다. 그림에는 첫 번째(왼쪽) 및 두 번째(오른쪽) 텍스트 잠재값 사이의 선형 보간으로 생성된 이미지들이 나열되어 있습니다. CrossFlow는 객체 방향, 합성 색상, 모양, 배경 장면, 심지어 객체 범주까지도 매끄럽게 변환할 수 있습니다. 자세한 내용을 보려면 확대해서 보세요. 간결성을 위해 7개의 보간 이미지만 표시했으며, 추가 이미지는 부록 C(그림 10과 그림 11)에서 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: CrossFlow provides visually smooth interpolations in the latent space. We show images generated by linear interpolation between the first (left) and second (right) text latents. CrossFlow enables visually smooth transformations of object direction, composite colors, shapes, background scenes, and even object categories. Please zoom in for better visualization. For brevity, we display only 7 interpolating images here; additional interpolating images can be found in Appendix C (Fig. 10 and Fig. 11).
> </details>



![](https://arxiv.org/html/2412.15213/x6.png)

> 🔼 그림 5는 CrossFlow가 텍스트잠재공간에서 연산을 허용하는 것을 보여줍니다. 먼저 텍스트 변형 자동 인코더(VE)를 사용하여 입력 텍스트를 잠재 공간 z0으로 매핑합니다. 그런 다음 이 잠재 공간에서 산술 연산을 수행하고, 그 결과로 얻은 잠재 표현을 사용하여 해당 이미지를 생성합니다. 각 이미지를 생성하는 데 사용된 잠재 코드 z0가 하단에 표시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: CrossFlow allows arithmetic in text latent space. Using the Text Variational Encoder (VE), we first map the input text into the latent space z0subscript𝑧0z_{0}italic_z start_POSTSUBSCRIPT 0 end_POSTSUBSCRIPT. Arithmetic operations are then performed in this latent space, and the resulting latent representation is used to generate the corresponding image. The latent code z0subscript𝑧0z_{0}italic_z start_POSTSUBSCRIPT 0 end_POSTSUBSCRIPT used to generate each image is provided at the bottom.
> </details>



![](https://arxiv.org/html/2412.15213/x7.png)

> 🔼 그림 (a)는 본 논문에서 제안하는 CrossFlow 프레임워크가 텍스트를 이미지로 직접 변환하는 과정을 보여줍니다. 기존의 텍스트-이미지 생성 방식과 달리, CrossFlow는 노이즈 분포나 조건화 메커니즘 없이 하나의 모달리티를 다른 모달리티로 직접 변환합니다.  이를 통해 간단하고 효율적인 텍스트-이미지 생성이 가능함을 시사합니다.  구체적으로, 텍스트 입력은 텍스트 변환기(Text Variational Encoder)를 통해 이미지로 변환하기에 적합한 형태로 인코딩됩니다. 그런 다음, 인코딩된 텍스트는 흐름 일치(flow matching) 모듈을 통해 이미지 공간으로 직접 변환되어 이미지가 생성됩니다. 이 과정은 추가적인 조건화 없이 순차적으로 진행됩니다.
> <details>
> <summary>read the caption</summary>
> (a)
> </details>



![](https://arxiv.org/html/2412.15213/x8.png)

> 🔼 그림 (b)는 CrossFlow의 다양한 응용 사례를 보여줍니다. 텍스트-이미지 생성, 이미지 캡션 생성, 단일 이미지를 이용한 깊이 추정, 이미지 초고해상도화 등 다양한 작업에 CrossFlow가 적용될 수 있음을 시각적으로 보여줍니다. 각각의 작업에 대해 입력과 출력의 예시 이미지들이 제시되어 CrossFlow의 유연성과 일반성을 강조합니다.
> <details>
> <summary>read the caption</summary>
> (b)
> </details>



![](https://arxiv.org/html/2412.15213/x9.png)

> 🔼 그림 (c)는 다양한 작업에 CrossFlow 프레임워크를 적용한 결과를 보여줍니다. 텍스트-이미지 생성, 이미지 캡션 생성, 단일 이미지 깊이 추정, 이미지 초해상도 등 다양한 모달리티 변환 작업에 CrossFlow가 적용되었으며, 각 작업에 특정 아키텍처를 필요로 하지 않고 유사한 성능을 달성한 것을 보여줍니다. 이는 CrossFlow가 다양한 작업에 일반화될 수 있는 범용적인 프레임워크임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (c)
> </details>



![](https://arxiv.org/html/2412.15213/x10.png)

> 🔼 그림 (d)는 다양한 언어 모델(CLIP, T5-XXL, Llama3)을 사용하여 CrossFlow의 성능을 평가한 결과를 보여줍니다.  각 언어 모델에 대해서,  CrossFlow는 CFG 지표를 사용하여 텍스트-이미지 생성을 수행하며,  FID와 CLIP 점수로 성능을 측정합니다. 이를 통해 다양한 언어 모델과의 호환성 및 CFG 지표의 효과를 확인할 수 있습니다.  각 모델의 크기와 성능을 비교하여 CrossFlow의 효율성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (d)
> </details>



![](https://arxiv.org/html/2412.15213/x11.png)

> 🔼 그림 (e)는 다양한 언어 모델(CLIP, T5-XXL, Llama3)을 사용하여 CrossFlow를 훈련시킨 결과를 보여줍니다.  각 모델의 제로샷 FID와 CLIP 점수를 비교하여, CrossFlow가 다양한 언어 모델과 호환되고 성능 저하 없이 사용될 수 있음을 보여줍니다.  즉, CrossFlow 프레임워크가 특정 언어 모델에 의존하지 않고 다양한 언어 모델과의 통합성을 가지고 있음을 시각적으로 나타냅니다.
> <details>
> <summary>read the caption</summary>
> (e)
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | #Params. |  | FID-30K ↓ | GenEval ↑ |
|---|---|---|---|---|
| DALL·E [68] | 12.0B |  | 27.50 | - |
| GLIDE [59] | 5.0B |  | 12.24 | - |
| LDM [73] | 1.4B |  | 12.63 | - |
| DALL·E 2 [69] | 6.5B |  | 10.39 | 0.52 |
| LDMv1.5 [73] | 0.9B |  | 9.62 | 0.43 |
| Imagen [74] | 3.0B |  | 7.27 | - |
| RAPHAEL [88] | 3.0B |  | 6.61 | - |
| PixArt-α [10] | 0.6B |  | 7.32 | 0.48 |
| LDMv3 (512²) [22] | 8.0B |  | - | 0.68 |
| CrossFlow | 0.95B |  | 9.63 | 0.55 |{{< /table-caption >}}
> 🔼 표 2는 최근의 텍스트-이미지 생성(T2I) 모델들과 CrossFlow 모델의 성능을 비교한 표입니다. GenEval 평가 지표에 대한 전체 점수와 각 세부 과제별 점수는 본문의 B.1절에서 확인할 수 있습니다. CrossFlow는 텍스트를 이미지로 직접 변환하여 최첨단 T2I 모델들과 비슷한 성능을 달성합니다. 이 표는 CrossFlow 모델의 우수성을 보여주는 주요 결과 중 하나입니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Comparison with recent T2I models. For GenEval, we report the overall score here and provide task-specific scores in Sec. B.1. CrossFlow achieves comparable performance with state-of-the-art T2I models by directly evolving text into images.
> </details>

{{< table-caption >}}
| Text encoder | FID ↓ | CLIP ↑ |
|---|---|---|
| Encoder | 66.65 | 0.20 |
| Encoder + noise | 59.91 | 0.21 |
| Variational Encoder | 40.78 | 0.23 |{{< /table-caption >}}
> 🔼 이 표는 본 논문에서 제안하는 CrossFlow 모델의 성능 향상에 기여하는 요소들을 분석한 결과를 보여줍니다.  가장 작은 크기(70M 파라미터)의 모델을 사용하여, 텍스트 변환기(Variational Encoder), 학습 목표, 분류기 없는 안내(CFG), 언어 모델, 그리고 학습 전략 등 다양한 요소들을 제거하거나 변경하면서 제로샷 FID-10K 및 CLIP 점수를 측정했습니다.  표에는 각 실험 설정에 대한 결과가 제시되어 있으며, CrossFlow에 최종적으로 사용된 설정은 밑줄로 표시되어 있습니다.  AG는 Autoguidance를 의미하며, '*' 표시는 CFG를 적용하지 않은 결과임을 나타냅니다.  즉, 이 표는 CrossFlow 모델의 각 구성 요소의 효과를 정량적으로 보여주는 ablation study 결과를 담고 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Ablation study on Text Variational Encoder, training objective, CFG, language models, and training strategy. We conduct ablation study on our smallest model (70M), reporting zero-shot FID-10K and CLIP scores. Final settings used for CrossFlow are underlined. AG: Autoguidance. *: results without applying CFG.
> </details>

{{< table-caption >}}
| Loss | FID ↓ | CLIP ↑ |
|---|---|---|
| T-T Recon. | 40.78 | 0.23 |
| T-T Contrast. | 34.67 | 0.24 |
| I-T Contrast. | 33.41 | 0.24 |{{< /table-caption >}}
> 🔼 표 4는 COCO Karpathy 분할 데이터셋을 사용한 이미지 캡션링 결과를 보여줍니다. CrossFlow는 이미지를 텍스트로 직접 변환하여 이미지 캡션링 작업에서 최첨단 모델들과 비슷한 성능을 달성했습니다. 공정한 비교를 위해 CIDEr 최적화 없이 학습된 비자동 회귀 방식의 모델들만 고려했습니다.  이 표는 CrossFlow가 이미지에서 텍스트 생성 작업에 효과적임을 보여주는 증거를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Image captioning on COCO Karpathy split. CrossFlow directly evolves from image to text, achieving comparable performance to state-of-the-art models on image captioning. For a fair comparison, we only consider non-autoregressive methods that are trained without CIDEr optimization.
> </details>

{{< table-caption >}}
| Method | FID ↓ | CLIP ↑ |
|---|---|---|
| No guidance | 33.41 | 0.24 |
| AG | 26.36 | 0.25 |
| CFG indicator | 24.33 | 0.26 |{{< /table-caption >}}
> 🔼 표 5는 KITTI 및 NYUv2 데이터셋을 사용하여 단안 깊이 추정 작업에 대한 CrossFlow 모델의 성능을 보여줍니다. CrossFlow는 이미지에서 깊이 맵으로의 직접적인 매핑을 가능하게 하여 최첨단 모델들과 비교할 만한 성능을 달성합니다. 표에는 다양한 평가 지표(AbsRel, SqRel, RMSE, δ<1, δ<2, δ<3)에 따른 CrossFlow와 기존 최첨단 모델들의 성능이 정량적으로 비교되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Monocular depth estimation on KITTI and NYUv2. CrossFlow enables direct mapping from image to depth, achieving comparable performance to state-of-the-art models.
> </details>

{{< table-caption >}}
| Model |  | FID ↓ | CLIP ↑ |
|---|---|---|---| 
| CLIP (0.4B) |  | 24.33 | 0.26 |
| T5-XXL (11B) |  | 22.28 | 0.27 |
| Llama3 (7B) |  | 21.20 | 0.27 |{{< /table-caption >}}
> 🔼 표 6은 ImageNet 검증 세트에서 이미지 초해상도 결과를 보여줍니다. 표에는 제안된 방법(CrossFlow)과 흐름 일치를 사용하는 표준 초해상도(SR) 방법의 성능이 비교되어 있습니다. 결과는 제안된 직접 매핑 방법이 표준 SR 방법보다 더 나은 성능을 달성했음을 보여줍니다. 즉, 저해상도 이미지를 고해상도 이미지로 직접 변환하는 CrossFlow의 접근 방식이 중간 단계 없이 더 효율적이고 효과적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Image super-resolution on the ImageNet validation set. Compared with standard SR method with flow matching, our direct mapping method achieves better performance.
> </details>

{{< table-caption >}}
| Train strategy | FID ↓ | CLIP ↑ |
|---|---|---|
| 2-stage separate training | 32.55 | 0.24 |
| Joint training | 24.33 | 0.26 |
| 2-stage w/ joint finetuning | 23.79 | 0.26 |{{< /table-caption >}}
> 🔼 표 7은 GenEval 벤치마크에서 CrossFlow 모델의 성능을 최첨단 모델들(LDM-XL, DALL-E 2 등)과 비교한 결과를 보여줍니다.  CrossFlow는 간단한 구조에도 불구하고 최첨단 모델들과 비슷한 성능을 달성하여, 차세대 미디어 생성 기술에 대한 유망한 방향을 제시합니다.  표에는 전체 GenEval 점수와 개별 과제별 점수(개체 수 세기, 색상, 위치, 속성 바인딩)가 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: GenEval comparisons. Our model achieves comparable performance to state-of-the-art models such as LDM-XL and DALL·E 2, suggesting that CrossFlow is a simple and promising direction for state-of-the-art media generation.
> </details>

{{< table-caption >}}
| Method | B@4 ↑ | M ↑ | R ↑ | C ↑ | S ↑ |
|---|---|---|---|---|---| 
| MNIC [24] | 30.9 | 27.5 | 55.6 | 108.1 | 21.0 |
| MIR [43] | 32.5 | 27.2 | - | 109.5 | 20.6 |
| NAIC-CMAL [28] | 35.3 | 27.3 | 56.9 | 115.5 | 20.8 |
| SATIC [96] | 32.9 | 27.0 | - | 111.0 | 20.5 |
| SCD-Net [58] | 37.3 | 28.1 | 58.0 | 118.0 | 21.6 |
| CrossFlow (Ours) | 36.4 | 27.8 | 57.1 | 116.2 | 20.4 |{{< /table-caption >}}
> 🔼 표 8은 제로샷 깊이 추정 결과를 보여줍니다. 기준 성능은 Marigold [39] 논문의 결과를 사용했습니다. 본 논문에서는 Marigold와 동일한 데이터셋(Hypersim [72], Virtual KITTI [9])을 사용하여 CrossFlow 모델을 학습시켰습니다. 표에서 가장 좋은 성능, 두 번째로 좋은 성능, 세 번째로 좋은 성능을 각각 강조 표시했습니다. CrossFlow는 단일 프레임워크만으로도 다양한 크로스-모달 작업에서 우수하거나 동등한 성능을 달성하여 제로샷 깊이 추정 작업에서 뛰어난 성능을 보여주는 것을 확인했습니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Zero-shot depth estimation. Baseline results are reported by Marigold [39]. We follow Marigold and train our CrossFlow on the same datasets, i.e., Hypersim [72] and Virtual KITTI [9]. We highlight the best, second best, and third best entries. With just a unified framework, CrossFlow achieves comparable or even superior performance on complex zero-shot depth estimation, demonstrating the general-purpose nature of CrossFlow on various cross-modal tasks.
> </details>

{{< table-caption >}}
| Method | KITTI |  | NYUv2 |  |
|---|---|---|---|---|
| | AbsRel (↓) | **δ<sub>1</sub>** (↑) | AbsRel (↓) | **δ<sub>1</sub>** (↑) |
| TransDepth [89] | 0.064 | 0.956 | 0.106 | 0.900 |
| AdaBins [6] | 0.058 | 0.964 | 0.103 | 0.903 |
| DepthFormer [45] | 0.052 | 0.975 | 0.096 | 0.921 |
| BinsFormer [46] | 0.052 | 0.974 | 0.094 | 0.925 |
| DiffusionDepth [18] | 0.050 | 0.977 | 0.085 | 0.939 |
| CrossFlow (Ours) | 0.053 | 0.973 | 0.094 | 0.928 |{{< /table-caption >}}
> 🔼 표 9는 텍스트 압축에 대한 ablation study 결과를 보여줍니다.  기존의 텍스트 인코더와 본 논문에서 제안하는 Text Variational Encoder 모두 입력 정보의 대부분을 보존하면서 77 x 768 차원의 입력을 1 x 1024 차원으로 압축(14.4배 압축)하는 실험을 진행했습니다. 결과적으로, 큰 압축 비율에도 불구하고 두 인코더 모두 입력 정보의 손실이 거의 없음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Ablation on text compression. Both text encoder and Text Variational Encoder preserve most of the input information, despite the large compression ratio (77×768→1×1024→777681102477\times 768\rightarrow 1\times 102477 × 768 → 1 × 1024, 14.4×14.4\times14.4 ×).
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
{{< /gallery >}}