---
title: "Chirpy3D: Continuous Part Latents for Creative 3D Bird Generation"
summary: "Chirpy3D: 부분 잠재 공간을 활용, 고품질 3D 새 생성!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Generation", "🏢 University of Surrey",]
showSummary: true
date: 2025-01-07
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.04144 {{< /keyword >}}
{{< keyword icon="writer" >}} Kam Woh Ng et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-09 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.04144" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.04144" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/chirpy3d-continuous-part-latents-for-creative" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

현재 **미세립 3D 객체 생성**은 **세부적인 디테일 부족** 또는 **기존 객체 모방**에 그치는 한계를 가지고 있습니다. **Chirpy3D**는 이러한 문제를 해결하기 위해 **다중 뷰 확산 모델**과 **부분 잠재 공간**을 활용합니다. 



Chirpy3D는 **2D 고해상도 이미지**를 **3D 공간**으로 전이하고, **연속적인 부분 잠재 공간**을 통해 **새로운 부분 생성** 및 **기존 부분 조작**을 가능하게 합니다. **자기 지도 학습 손실 함수**는 **미지 부분 생성 시 안정성**을 높이며, **다양한 종류의 새**를 생성하는 결과를 보여줍니다.  본 연구는 **미세립 3D 객체 생성 분야**에 **창의성과 정확성**을 모두 높이는 새로운 방향을 제시합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 부분 수준의 연속적 잠재 공간 모델링을 통한 창의적인 3D 객체 생성 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 다중 뷰 확산 모델을 이용한 2D 고해상도 정보의 3D 공간으로의 효과적인 전이 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 새로운 자기 지도 학습 손실 함수를 통한 안정적인 미지 부분 생성 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **미세립 3D 객체 생성의 창의성을 높이는 새로운 방법**을 제시하여, **기존의 한계를 뛰어넘는 고품질 3D 모델 생성**에 기여합니다. **부분 수준의 조작을 통한 창의적 제어**와 **새로운 부분 생성** 기능은 **다양한 응용 분야**에 영향을 미칠 수 있으며, 특히 **3D 자산 생성 분야**에 새로운 가능성을 제시합니다. **다른 도메인으로의 확장 가능성** 또한 언급되어, 관련 연구자들에게 **지속적인 연구**를 위한 동기를 부여합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.04144/x2.png)

> 🔼 그림 1은 다양한 부품으로 구성된 새의 3D 모델을 보여줍니다. Chirpy3D는 원시 2D 이미지에서 부품잠재공간을 학습하여 이 공간을 탐색함으로써 고품질의 창의적인 3D 새를 생성할 수 있습니다. 그림 상단에는 기존 종들이, 하단에는 새로운 종들이 나와있습니다.  Chirpy3D는 2D 이미지만으로 훈련되었음에도 불구하고 다양한 각도에서 고품질의 3D 모델을 생성할 수 있는 능력을 보여줍니다.  이를 통해 기존의 3D 모델 생성 방법의 한계를 뛰어넘어 보다 창의적이고 다양한 3D 모델을 생성할 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  Generated chirpy 3D birds composed of diverse parts. Our Chirpy3D learns a part latent space from raw 2D images and can generate high-quality creative 3D birds by exploring the part latent space. (Top) Existing species. (Bottom) Novel species.
> </details>





{{< table-caption >}}
| $D_{l}$ | 4 | 16 | 32 | 64 |
|---|---|---|---|---|
| $H$ | **4.81** | 4.68 | 4.67 | 4.33 |
| $e^{H}$ | **123.2** | 108.1 | 106.7 | 76.3 |{{< /table-caption >}}

> 🔼 표 1은 생성된 이미지의 주제 충실도를 평가하는 지표들을 보여줍니다.  DINO와 CLIP 두 가지 방법을 이용하여 생성된 이미지와 실제 이미지의 유사도를 측정했으며, FID와 FID-CLIP은 생성된 이미지의 품질을 평가하는 지표입니다.  각 지표의 값이 클수록 생성된 이미지가 실제 이미지와 더 유사하고, 품질이 더 높음을 의미합니다.  세 가지 모델(Textual Inversion, PartCraft, Chirpy3D)의 성능을 비교하여 Chirpy3D 모델의 우수성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Subject fidelity metrics.
> </details>





### In-depth insights


#### Fine-grained 3D
**미세립자 3D**는 기존의 3D 모델링 기법으로는 표현이 어려웠던 매우 정교하고 세밀한 형태의 3D 객체를 생성하는 기술을 의미합니다.  이 논문에서는 **다양한 종류의 새들의 고해상도 3D 모델 생성**이라는 구체적인 문제를 다루고 있습니다.  단순히 기존 새들의 모습을 모방하는 것을 넘어, **새로운 종류의 새를 창조하는 수준의 창의성**을 목표로 합니다. 이를 위해 **다중 뷰 확산 모델**을 활용하여 2D 이미지의 미세한 정보를 3D로 변환하는 기법을 제시하며, **부품 수준의 조작을 가능하게 하는 연속적인 잠재 공간**을 구축함으로써 **부품의 변형과 조합을 통한 창조적인 모델 생성**을 가능하게 합니다.  **자기 지도 학습 방식의 손실 함수**를 도입하여 새로운 부품의 안정적인 생성을 유도하며, 결과적으로 **종 특유의 세세한 디테일을 유지하면서도 완전히 새로운 3D 새 모델을 생성**할 수 있음을 보여줍니다.  **다양한 평가 지표**를 통해 기존 방법론과의 성능 비교를 제시하고, **새로운 3D 모델의 다양성과 질적 우수성**을 입증합니다.  결론적으로 이 논문은 미세립자 3D 생성 기술의 새로운 가능성을 제시하고 있으며,  다른 영역으로의 확장 가능성 또한 높게 평가됩니다.

#### Part-aware Latents
본 논문에서 제시된 'Part-aware Latents' 개념은 **미세한 세부 묘사를 갖춘 3D 객체 생성**이라는 어려운 과제에 대한 혁신적인 접근 방식을 보여줍니다.  기존의 방법들이 전체 객체를 한꺼번에 생성하는 데 초점을 맞춘 것과 달리, 이 방법은 객체를 구성하는 개별 부분들의 **연속적인 잠재 공간(continuous latent space)**을 학습하여 각 부분을 독립적으로 제어하고 조작할 수 있게 합니다. 이는 **새로운 부분들의 생성과 기존 부분들의 변형 및 조합**을 가능하게 하여 창의적인 3D 객체 디자인에 혁신을 가져옵니다.  **가우시안 분포(Gaussian distribution)로 모델링된 부분 잠재 공간**은 부분들 간의 매끄러운 보간 및 새로운 부분의 샘플링을 가능하게 하여 창의성을 더욱 증폭시키는 역할을 합니다.  **자기 지도 학습 기법(self-supervised learning)**을 통해 시스템은 본래 학습 데이터에는 존재하지 않는 새로운 부분들도 안정적으로 생성할 수 있게 됩니다.  이러한 혁신적인 접근 방식은 **세부적인 디테일과 창의성을 동시에 확보**,  **새로운 종류의 3D 객체 생성**이라는 목표 달성에 크게 기여한다는 점에서 매우 중요한 의미를 지닙니다.

#### Novel View Synth
**신규 뷰 합성(Novel View Synthesis)**은 3차원 공간에 대한 2차원 이미지를 사용하여 존재하지 않는 새로운 시점에서의 이미지를 생성하는 기술입니다. 이는 3차원 모델링이나 실제 물체를 직접 촬영하지 않고도 다양한 각도에서의 이미지를 얻을 수 있다는 점에서 큰 장점을 지닙니다.  **딥러닝 기반의 신규 뷰 합성**은 기존의 방법보다 더욱 정교하고 현실적인 이미지를 생성할 수 있으며, **다양한 분야**에 응용될 수 있는 잠재력을 가지고 있습니다.  **자율주행**, **가상현실/증강현실**, **로봇공학** 등의 분야에서 3차원 환경을 이해하고 상호 작용하는 데 필수적인 기술이 될 것입니다.  그러나 **데이터 요구량**, **계산 비용**, **합성 이미지의 품질** 등 해결해야 할 과제도 존재합니다. 특히, **고해상도** 및 **정교한 디테일**을 가진 이미지 생성에는 더욱 높은 성능의 컴퓨팅 자원과 더욱 발전된 알고리즘이 필요합니다.  앞으로 **데이터 효율성**을 높이고 **계산 효율성**을 개선하는 연구가 지속적으로 이루어진다면, 신규 뷰 합성 기술은 더욱 광범위하게 활용될 것으로 예상됩니다.

#### MVDream Fine-tune
본 논문에서 제시된 MVDream 파인튜닝 전략은 **고해상도 2D 이미지 데이터를 활용하여 3D 모델 생성의 정확도와 세밀함을 크게 향상시키는 데 중점**을 둡니다. 기존의 MVDream 모델은 텍스트 기반의 조건화에 의존했지만, **본 연구는 2D 이미지 데이터를 추가적인 조건으로 활용**, 보다 사실적이고 세부적인 3D 조형물을 생성하는 데 성공했습니다. 특히 **파인튜닝 과정에서 다중 뷰 일관성을 유지하는 점이 중요**하며, 이를 통해 다양한 각도에서 볼 때도 자연스럽고 일관된 3D 모델을 생성할 수 있게 되었습니다.  **연구의 핵심은 2D 이미지의 고해상도 디테일 정보를 효과적으로 3D 공간에 투영하는 기술**에 있으며, 이는 **새로운 수준의 시각적 사실성과 창의적인 3D 모델 생성**으로 이어집니다.  **파인튜닝 과정에서 모델의 안정성과 효율성을 높이기 위한 다양한 최적화 기법** 또한 제시되었으며, 이는 실제 응용 분야에서의 활용성을 높이는 데 기여할 것으로 예상됩니다.

#### Creative Generation
본 논문에서 제시된 "창의적인 생성(Creative Generation)" 개념은 **기존 방법들이 단순히 기존 객체를 모방하거나 세부적인 디테일이 부족한 것과 대조적으로**, **전혀 새로운 객체를 생성하는 능력**을 의미합니다.  이는 단순한 변형이나 조합을 넘어, **부분(part) 수준에서의 새로운 디자인을 생성하고 조합하는 능력**을 통해 구현됩니다.  **연속적인 부분잠재공간(continuous part latent space)**을 활용하여, 새로운 부분을 생성하고 기존 부분들과 자유롭게 조합하는 것이 핵심입니다. 이를 통해 **종(species)간의 중간 형태(hybrid)를 생성하거나, 실제 존재하지 않는 완전히 새로운 종을 만들어내는 창의적인 결과물**을 얻을 수 있다는 점이 중요합니다. 이러한 창의적인 생성 과정은 **자기 지도 학습(self-supervised learning)**을 통해 안정적으로 새로운 부분의 생성을 보장하며, 다양한 분야에 적용 가능한 범용적인 프레임워크를 제시합니다.  **세부적인 질감과 형태를 유지하면서도 독창적인 디자인을 생성하는 능력**은 **미세입자(fine-grained) 영역에서의 3D 생성 기술의 획기적인 발전**을 보여줍니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.04144/x3.png)

> 🔼 그림 2는 Chirpy3D의 전체 구조를 보여줍니다. (위쪽) 학습 중에는 2D 새 이미지만 사용하여 텍스트-다중 뷰 확산 모델(예: MVDream)을 미세 조정합니다. 연속적인 부분 인식 잠재 공간을 모델링하여 기본 부분 정보를 학습하는 것을 목표로 합니다. 이는 학습 가능한 f를 통해 일련의 종 임베딩 𝒆𝒆 을 부분 잠재 변수 𝒍𝒍 으로 투영하고, 학습 가능한 g를 통해 단어 임베딩 𝒕𝒕 으로 디코딩하여 텍스트 프롬프트에 삽입함으로써 달성됩니다. 확산 손실(식 5)과 여러 손실 목표(가우시안 분포로 부분 잠재 변수를 모델링하기 위한 ℒregsubscriptℒreg (식 2), 부분 분리을 위한 ℒattnsubscriptℒattn (식 6), 시각적 일관성을 높이기 위한 제안된 ℒclsubscriptℒcl (식 4))를 사용하여 확산 모델을 학습합니다. f와 g는 학습 가능한 모듈입니다. 효율적인 학습을 위해 U-Net의 크로스 어텐션 계층에 LoRA 계층을 추가했습니다. (아래쪽) 추론 중에는 원하는 부분 잠재 변수를 조건으로 사용하여 먼저 다중 뷰 이미지를 미리 본 다음 SDS 손실 ℒSDSsubscriptℒSDS 을 통해 3D 표현(예: NeRF)으로 변환할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2:  Overall architecture of our Chirpy3D. (Top) During training, we fine-tune a text-to-multi-view diffusion model (e.g., MVDream) with only 2D images of birds. We aim to learn the underlying part information by modeling a continuous part-aware latent space. This is achieved by learning a set of species embeddings 𝒆𝒆\bm{e}bold_italic_e, project them into part latents 𝒍𝒍\bm{l}bold_italic_l through learnable f𝑓fitalic_f, decode into word embeddings 𝒕𝒕\bm{t}bold_italic_t through learnable g𝑔gitalic_g and insert into text prompt. We train the diffusion model with diffusion loss (Eq. 5) and multiple loss objectives – ℒregsubscriptℒreg\mathcal{L}_{\text{reg}}caligraphic_L start_POSTSUBSCRIPT reg end_POSTSUBSCRIPT (Eq. 2) to model part latents as Gaussian distribution, ℒattnsubscriptℒattn\mathcal{L}_{\text{attn}}caligraphic_L start_POSTSUBSCRIPT attn end_POSTSUBSCRIPT (Eq. 6) for part disentanglement, and our proposed ℒclsubscriptℒcl\mathcal{L}_{\text{cl}}caligraphic_L start_POSTSUBSCRIPT cl end_POSTSUBSCRIPT (Eq. 4) to enhance visual coherency. f𝑓fitalic_f and g𝑔gitalic_g are trainable modules. For efficient training, we added LoRA layers into cross-attention layers of the U-Net. (Bottom) During inference, we can first preview multi-view images by selecting desired part latents as condition before turning them into 3D representations (e.g., NeRF) through SDS loss ℒSDSsubscriptℒSDS\mathcal{L}_{\text{SDS}}caligraphic_L start_POSTSUBSCRIPT SDS end_POSTSUBSCRIPT.
> </details>



![](https://arxiv.org/html/2501.04144/x4.png)

> 🔼 이 그림은 본 논문에서 제안하는 방법이 어떻게 새로운 부분(part)들을 생성하는지 보여줍니다.  새로운 부분에 대한 이미지 데이터가 없기 때문에, 기존의 자연 이미지들을 대신 사용합니다.  두 개의 노이즈가 포함된 잠재 벡터(latent)에 대해 크로스 어텐션 특징맵(cross-attention feature maps)을 추출하고, 두 맵 사이의 차이를 최소화하는 방식입니다.  이를 통해 모델이 어떤 잠재 벡터가 주어지더라도 유사한 특징맵을 생성하도록 유도하여, 결과적으로 보이지 않는 새로운 부분들에 대한 노이즈 제거(denoising) 과정을 안정적으로 만듭니다.  즉, 새로운 부분에 대한 이미지가 없어도, 유사한 특징을 가진 기존 이미지들을 활용하여 새로운 부분을 생성하고, 이 과정을 안정적으로 수행할 수 있도록 하는 메커니즘을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: As we do not have images of unseen part latents, we use real natural images as our proxy. We extract cross-attention feature maps F𝐹Fitalic_F of two noised latents, then minimize the discrepancy between the two feature maps. This will encourage the model to compute similar feature maps for any given part latents, which indirectly stabilizes the denoising process for unseen latents.
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/cls/subject_ti_2x.jpg)

> 🔼 그림 4는 Chirpy3D 모델이 새로운 새를 생성하는 세 가지 방법을 보여줍니다. (a)에서는 이미 학습 데이터에 존재하는 부분들을 선택하여 새로운 조합의 새를 만드는 과정을 보여줍니다. 이는 기존 부분들의 새로운 배열을 통해 새롭지만 현실적인 새를 생성하는 방식입니다. (b)에서는 모델이 학습 데이터에는 없던 완전히 새로운 부분들을 생성하는 방법을 보여줍니다. 이는 잠재 공간에서 샘플링을 통해 이전에 보지 못한 새로운 특징들을 가진 부분들을 생성하는 것을 의미합니다. 마지막으로 (c)에서는 기존 부분들을 보간하여 새로운 부분들을 생성하는 방법을 보여줍니다. 이는 기존 부분들의 특징들을 혼합하여 새로운, 그러나 현실적인 부분들을 만들어내는 방식입니다.  각 방법 모두 다양한 부분들의 조합을 통해 창의적인 새들을 생성할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: (a) Seen part selection generation. Unseen part synthesis via (b) novel sampling and (c) interpolation.
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/cls/subject_partcraft_2x.jpg)

> 🔼 그림은 논문의 실험 결과 중 하나로, 세 가지 다른 방법(Textual Inversion, PartCraft, Chirpy3D)을 사용하여 생성한 이미지들을 보여줍니다. Textual Inversion은 품질이 떨어지는 이미지를 생성하고, PartCraft는 다양성이 부족하며, Chirpy3D는 세 가지 방법 중 가장 품질이 좋고 다양한 이미지를 생성합니다. 각 방법은 이미지 생성에 대한 서로 다른 접근 방식을 보여주며, Chirpy3D가 가장 우수한 성능을 보임을 시각적으로 보여주는 비교 그림입니다.
> <details>
> <summary>read the caption</summary>
> (a) Textual Inversion
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/cls/subject_ours_2x.jpg)

> 🔼 그림은 논문의 Part Composition 섹션에 속하며, PartCraft 모델이 다양한 새 종의 부분들을 조합하여 새 이미지를 생성하는 능력을 보여줍니다.  각 열은 특정 새의 부분들을 다른 새의 부분들로 바꿔치기 한 결과를 보여주며,  PartCraft 모델이 부분들을 얼마나 잘 분리하고 조합할 수 있는지 시각적으로 보여줍니다.  각 행은 서로 다른 새들을 나타내며,  각 열은 원본 새의 앞쪽, 머리, 날개 부분을 각각 다른 새의 해당 부분으로 교체하여 생성한 결과 이미지를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) PartCraft
> </details>



![](https://arxiv.org/html/2501.04144/x5.png)

> 🔼 그림 (c)는 본 논문에서 제안하는 Chirpy3D 모델을 사용하여 생성한 다양한 새들의 3D 모델들을 보여줍니다.  Chirpy3D는 부분별 잠재 공간을 이용하여 기존 종의 특징을 유지하면서도 완전히 새로운 종류의 새들을 창의적으로 생성할 수 있습니다. 그림에서는 다양한 부리, 깃털, 머리 모양 등 새의 신체 부분들이 어떻게 조합되어 새로운 형태를 만들어내는지 보여줍니다. 이는 Chirpy3D 모델이 세밀한 부분까지 고려하여 사실적이고 다양한 새들을 생성할 수 있음을 시각적으로 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> (c) Chirpy3D (Ours)
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/interpolation/interpolate_ti.jpg)

> 🔼 그림 5는 논문에서 제시된 Chirpy3D 모델이 청딱따구리와 백펠리컨이라는 두 가지 서로 다른 종의 새를 생성하는 능력을 보여줍니다. 각 종에 대해 여러 개의 샘플 이미지가 제시되어 모델이 다양한 각도와 자세로 새를 생성할 수 있음을 시각적으로 보여줍니다.  이 이미지들은 모델의 정확성과 생성 품질을 평가하는 데 도움이 되며, 특히 미세한 디테일과 다양한 종류의 새를 생성하는 능력을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Subject generation of 2 different species -blue jay, white pelican.
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/interpolation/interpolate_partcraft.jpg)

> 🔼 그림 6은 부분 조성의 시각적 비교를 보여줍니다. 각 열은 (A) 빨간색 울새, (B) 윌슨 솔새, (C) 작은 바다오리, (D) 캘리포니아 갈매기, (E) 뿔 딱새, (F) 노래 참새의 세 가지 다른 종의 새들을 보여줍니다. 각 열의 상단은 원본 이미지를, 하단은 부분별 조성을 통해 생성된 이미지를 보여줍니다. 빨간색 원은 변경된 부분을 나타냅니다. 원본과 조성 이미지 모두 동일한 시드로 생성되었습니다. 이 그림은 모델이 개별 부분을 인식하고 조작하여 새로운 조합을 생성할 수 있는 능력을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Visual comparison of part composition. A,B,C,D,E,F𝐴𝐵𝐶𝐷𝐸𝐹A,B,C,D,E,Fitalic_A , italic_B , italic_C , italic_D , italic_E , italic_F represent cardinal, wilson warbler, least auklet, california gull, horned lark, and song sparrow respectively. Red circles indicate changed parts. All generated (including sources & targets) by the same seed.
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/interpolation/interpolate_ours.jpg)

> 🔼 그림은 논문의 4. 실험 섹션에 속하며, 세 가지 다른 방법(Textual Inversion, PartCraft, Chirpy3D)을 사용하여 생성된 이미지를 보여줍니다. Textual Inversion은 단순히 단어 임베딩을 직접 조작하여 이미지를 생성하지만, PartCraft와 Chirpy3D는 부품 수준의 조작을 통해 더욱 정교하고 창의적인 제어를 가능하게 합니다.  각 방법의 이미지 품질과 다양성을 비교하여 Chirpy3D의 우수성을 보여줍니다. 특히, Textual Inversion의 경우에는 이미지에 인공물이 많이 나타나는 것을 확인할 수 있으며, PartCraft는 다양성이 부족한 것으로 나타나 있습니다. 반면 Chirpy3D는 세 가지 방법 중 가장 높은 품질과 다양성을 보여주는 결과를 생성합니다.
> <details>
> <summary>read the caption</summary>
> (a) Textual Inversion
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/random/tsne_part_ti.png)

> 🔼 그림은 논문의 Part Composition 섹션에 속하며, PartCraft 모델이 다양한 조류 종의 부분들을 조합하여 새로운 조류 이미지를 생성하는 능력을 보여줍니다.  PartCraft 모델은 개별 부분들을 개별 토큰으로 인코딩하는 방식을 사용하며, 이 그림에서는 소스 이미지에서 특정 부분을 선택하여 타겟 이미지의 해당 부분과 교체하는 과정을 보여줍니다.  이를 통해 각 부분의 독립성과 모델의 조합 능력을 평가할 수 있습니다. 그림에는 여러 가지 조류 종의 이미지들이 나열되어 있으며, 각 이미지는 소스 이미지와 타겟 이미지로 나뉘어져,  PartCraft 모델이 어떻게 부분들을 조합하는지 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) PartCraft
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/random/tsne_partcraft.png)

> 🔼 이 그림은 논문의 핵심 방법론인 Chirpy3D 모델의 성능을 보여줍니다.  Chirpy3D는 기존 방법론들과 달리, 새롭고 사실적인 새의 부품들을 생성하고 이들을 결합하여 완전히 새로운 새들을 만들어낼 수 있습니다. 이 그림은 다양한 종류의 새들과, 기존에 존재하지 않는 새로운 새들을 보여주는 것으로, Chirpy3D가 얼마나 창의적이고 세밀한 3D 모델을 생성할 수 있는지를 시각적으로 보여줍니다.  위쪽에는 실제 존재하는 새들의 이미지가, 아래쪽에는 Chirpy3D가 생성한 새들의 이미지가 나와 있습니다.
> <details>
> <summary>read the caption</summary>
> (c) Chirpy3D (Ours)
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/random/tsne_ours_kl0001.png)

> 🔼 그림 7은 파란색 솔잣새와 추기새 두 종의 모든 부분잠재변수를 선형 보간한 결과를 보여줍니다. 한 가지 뷰만 표시되어 있습니다. Chirpy3D는 PartCraft와 달리 특정 단계 이후 갑작스러운 변화(빨간색 상자) 없이 훨씬 부드러운 보간을 달성합니다. PartCraft의 경우 보간 과정에서 갑작스럽게 다른 이미지로 바뀌는 현상이 발생하는데, 이는 부분잠재공간이 연속적이지 않기 때문일 수 있습니다. 반면 Chirpy3D는 연속적인 부분잠재공간을 사용하여 부드러운 전환을 생성합니다. 이는 새의 부분들을 자연스럽게 혼합하여 새로운 종류의 새를 만들어낼 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7:  Linear interpolation of all part latents between two different species – blue jay and cardinal. Only one view is shown. Our Chirpy3D achieves much smoother interpolation, unlike PartCraft exhibits an abrupt switch phenomenon after a certain step (red box).
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/random/random_ti.jpg)

> 🔼 그림은 논문의 실험 결과 중 하나로, 세 가지 다른 방법(Textual Inversion, PartCraft, Chirpy3D)을 사용하여 생성한 이미지들을 보여줍니다.  각 방법은 텍스트 기반으로 이미지를 생성하지만, Textual Inversion은 단순한 텍스트 조합에 의존하여 품질이 떨어지고, PartCraft는 부분적인 세부 묘사에는 강점을 보이지만 다양성이 부족한 반면, Chirpy3D는 세부적인 부분과 다양성 모두 우수함을 보여주는 것을 목적으로 합니다. 이는 본 논문에서 제안된 Chirpy3D 모델이 보다 창의적이고 정교한 이미지 생성에 효과적임을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (a) Textual Inversion
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/consistency/consistency_partcraft.jpg)

> 🔼 그림은 논문의 Part Composition 실험 결과를 보여줍니다. PartCraft 모델을 사용하여 기존 이미지의 일부를 다른 이미지의 해당 부분으로 바꿔치기하여 부분 조성을 평가합니다. 그림은 소스 이미지, 대상 이미지, 그리고 PartCraft 모델에 의해 생성된 이미지들을 보여주어 모델의 부분 조성 능력을 시각적으로 보여줍니다. 각 이미지는 새의 특정 부분(예: 머리, 날개, 몸통)을 강조하여 모델이 부분들을 어떻게 식별하고 조합하는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) PartCraft
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/random/random_ours.jpg)

> 🔼 그림 (c)는 본 논문에서 제안하는 Chirpy3D 모델이 생성한 이미지들을 보여줍니다. 이 그림은 다양한 종류의 새들을 매우 정교하고 사실적인 디테일로 묘사하고 있습니다. 기존 종들과 새로운 종들을 모두 포함하고 있으며, 각 새들의 부품들이 자연스럽게 조합되어 새롭고 독창적인 새들을 만들어내는 Chirpy3D의 창의적인 능력을 보여줍니다. 각 새들은 다양한 각도에서 촬영된 여러 뷰를 가지고 있어 3D 모델의 질감과 입체감을 더욱 생생하게 표현합니다.
> <details>
> <summary>read the caption</summary>
> (c) Chirpy3D (Ours)
> </details>



![](https://arxiv.org/html/2501.04144/x6.png)

> 🔼 그림 8은 생성된 이미지의 DINO 특징에 대한 t-SNE 임베딩을 보여줍니다. 파란색은 기존 종의 이미지 재구성을, 주황색은 새로운 종의 생성을 나타냅니다. 이 그림은 생성 모델이 기존 종의 특징을 얼마나 잘 학습했는지, 그리고 새로운 종을 얼마나 잘 생성하는지를 시각적으로 비교 분석하기 위해 사용되었습니다.  t-SNE는 고차원 데이터를 2차원 공간에 투영하여 시각화하는 기법으로, 유사한 특징을 가진 이미지들은 서로 가깝게 표현됩니다. 따라서 그림 8을 통해 생성된 이미지들의 특징 분포를 직관적으로 이해하고, 모델의 생성 능력을 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: t-SNE embeddings of DINO features of generated images. Blue represents images of subject reconstruction; Orange represents images of novel generation.
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/consistency/consistency_baseline.jpg)

> 🔼 그림은 논문의 4. Experiment 섹션의 일부이며, 세 가지 다른 방법(Textual Inversion, PartCraft, Chirpy3D)을 사용하여 생성된 이미지를 보여줍니다. Textual Inversion은 품질이 떨어지고, PartCraft는 다양성이 부족하며, Chirpy3D는 세 가지 방법 중 가장 우수한 성능을 보입니다. 이 그림은 각 방법의 장단점을 시각적으로 비교하여 논문에서 제시하는 Chirpy3D 모델의 성능을 강조합니다.  각각의 방법은 2D 이미지로부터 3D 조류 객체를 생성하며, Textual Inversion의 경우 생성된 이미지의 질이 떨어지고, PartCraft의 경우 다양성이 부족한 반면, Chirpy3D는 높은 질과 다양성을 보이는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (a) Textual Inversion
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/consistency/consistency_ours.jpg)

> 🔼 그림은 논문의 Part Composition 부분에 속하며, PartCraft 모델이 생성한 이미지들을 보여줍니다.  PartCraft는 부분 단위로 이미지를 조작하고 생성하는 모델인데, 이 그림에서는 기존 이미지의 특정 부분을 다른 이미지의 해당 부분으로 바꾸어 새로운 조합을 만들어낸 결과를 보여줍니다.  각 열은 특정 새의 여러 부분(몸통, 머리, 날개 등)을 서로 다른 새의 부분들로 교체해 생성한 이미지들을 나타냅니다.  이는 PartCraft 모델의 부분 교체 및 조합 능력을 시각적으로 보여주는 예시입니다.  다양한 새의 부분들이 결합되어 새로운 종류의 새와 같은 이미지들이 생성되는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (b) PartCraft
> </details>



![](https://arxiv.org/html/2501.04144/x7.png)

> 🔼 그림 (c)는 논문의 Chirpy3D 모델을 사용하여 생성한 다양한 새들의 3D 모델들을 보여줍니다. 이 그림은 Chirpy3D 모델이 기존 종의 특징을 유지하면서 새로운 종의 새를 생성할 수 있는 능력을 보여주는 여러 가지 예시들을 포함하고 있습니다. 각 새의 3D 모델은 다양한 각도에서 여러 뷰로 표현되어 모델의 정확성과 디테일을 더욱 자세히 보여줍니다.  이 이미지들은 Chirpy3D의 창의적인 3D 객체 생성 능력을 강조하며,  새로운 부분들을 생성하고 조합하여 다양한 시각적 결과물을 만들어낼 수 있는 잠재력을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (c) Chirpy3D (Ours)
> </details>



![](https://arxiv.org/html/2501.04144/x8.png)

> 🔼 그림 9는 무작위로 샘플링된 잠재 벡터/임베딩을 사용하여 생성된 이미지들을 보여줍니다. Textual Inversion은 단어 임베딩의 직접적인 보간으로 인해 이미지에 아티팩트가 자주 발생하는 반면, PartCraft는 아티팩트가 적게 발생하지만 일관성이 부족합니다. 반면 Chirpy3D는 더욱 다양한 새로운 이미지들을 생성합니다. 이 그림은 서로 다른 세 가지 방법(Textual Inversion, PartCraft, Chirpy3D)을 사용하여 생성된 이미지들을 비교하여 각 방법의 강점과 약점을 보여줍니다. 특히 Chirpy3D는 새로운 종류의 새들을 생성하는 데 뛰어난 다양성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Generated images with random sampled latents/embeddings. Textual Inversion often produces images with artifacts due to the direct interpolation of word embeddings. PartCraft can generate images with fewer artifacts but lacks consistency. In contrast, our Chirpy3D generates novel images with greater diversity.
> </details>



![](https://arxiv.org/html/2501.04144/x9.png)

> 🔼 그림 10은 본 논문에서 제안하는 Chirpy3D 모델이 학습한 3D 객체들을 NeRF(Neural Radiance Fields)를 사용하여 렌더링한 결과를 보여줍니다. 다양한 종류의 새들이 정교한 디테일과 함께 사실적으로 표현되어 있으며,  Chirpy3D가 2D 이미지 데이터로부터 고품질의 3D 모델 생성이 가능함을 시각적으로 보여줍니다.  각 이미지는 서로 다른 시드(seed) 값을 사용하여 생성되었으며, 모델의 생성 능력과 다양성을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: NeRF rendering of learned 3D objects.
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/supp/fg3d_dog.jpg)

> 🔼 그림은 논문의 4.3절(추가 분석)에서 언급된 내용과 관련이 있습니다.  ℒclsubscriptℒcl mathcal{L}_{ text{cl}}는 자기 지도 학습 손실 함수(self-supervised feature consistency loss)를 나타냅니다.  (a)는 이 손실 함수를 적용하지 않았을 때 생성된 이미지의 시각적 일관성을 보여줍니다.  즉, 생성된 새 부품(unseen parts)이 서로 일관성 있게 조합되지 않고 이미지에 인공물(artifacts)이 나타날 수 있음을 보여주는 것입니다.  이 그림은 모델이 새로운 부품을 생성하는 능력과 시각적 일관성을 유지하는 능력을 비교 분석하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> (a) Ours without ℒclsubscriptℒcl\mathcal{L}_{\text{cl}}caligraphic_L start_POSTSUBSCRIPT cl end_POSTSUBSCRIPT
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/supp/fg3d_animal.jpg)

> 🔼 그림은 논문의 3.3절 최적화 부분에서 언급하는, 제안된 feature consistency loss (ℒcl) 의 효과를 보여줍니다.  ℒcl을 적용했을 때 (b) 와 적용하지 않았을 때 (a) 의 시각적 일관성을 비교하여,  ℒcl 이 생성된 객체의 시각적 품질을 향상시키는 데 기여함을 보여주는 정성적 결과입니다.  특히,  보이지 않는 부분들에 대한 일관성을 유지하는 데 효과적임을 시각적으로 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (b) Ours with ℒclsubscriptℒcl\mathcal{L}_{\text{cl}}caligraphic_L start_POSTSUBSCRIPT cl end_POSTSUBSCRIPT
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/supp/reason_gs75_bird_10.jpg)

> 🔼 그림 11은 새로운 잠재 공간에서 무작위로 생성된 이미지를 보여줍니다. 모든 이미지는 동일한 카메라 위치에서 생성되었지만, 서로 다른 난수 시드를 사용했습니다. (a)는 제안된 특징 일관성 손실(ℒcl) 없이 생성된 이미지들이 일관성이 부족하고, 시각적 특징이 불일치하며, 인공적인 아티팩트가 많이 보이는 반면, (b)는 ℒcl을 적용하여 생성된 이미지들이 훨씬 더 일관성 있고, 시각적 특징이 일치하며, 아티팩트가 적다는 것을 보여줍니다. 이는 ℒcl이 생성된 이미지의 시각적 품질과 일관성을 향상시키는 데 중요한 역할을 한다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 11:  All images are generated with the same camera pose but with different seeds on unseen latent. (a) Without our feature consistency loss ℒclsubscriptℒcl\mathcal{L}_{\text{cl}}caligraphic_L start_POSTSUBSCRIPT cl end_POSTSUBSCRIPT, the generated images lack consistency (e.g., less artifact, and inconsistent visual feature) compared to (b).
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/supp/reason_gs75_cardinal_10.jpg)

> 🔼 이 그림은 본 논문에서 제시하는 방법을 사용하여 시베리안 허스키와 파피용이라는 두 개의 다른 견종의 특징을 결합하여 새로운 견종을 생성한 결과를 보여줍니다. 왼쪽에는 시베리안 허스키, 오른쪽에는 파피용, 그리고 가운데는 두 견종의 특징을 혼합하여 생성된 새로운 견종의 이미지가 각각 표시되어 있습니다. 이는 논문에서 제안하는 방법이 기존의 데이터셋을 넘어 새로운 종류의 이미지를 생성하는 데 효과적임을 보여주는 예시입니다. Stanford Dogs 데이터셋을 사용하여 훈련시킨 모델이 생성한 이미지입니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: A hybrid (middle) between siberian husky (left) and papillon (right), trained with Stanford Dogs [27].
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/supp/supp_cls_ti.jpg)

> 🔼 그림 13은 논문에서 제시된 Chirpy3D 모델을 사용하여 NeRF(Neural Radiance Fields) 또는 3DGS(3D Gaussian Splatting) 기반의 3D 오브젝트 생성 결과를 보여줍니다.  Chirpy3D는 2D 이미지 데이터를 기반으로 학습되었지만,  다양한 시점에서 일관된 3D 모델을 생성할 수 있음을 보여주는 예시입니다.  다양한 종류의 새들을 생성하고, 각 새의 다양한 시점을 보여줍니다. NeRF와 3DGS 모두에서 고품질의 3D 모델을 생성하는 Chirpy3D의 성능을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: Optimization-based 3D generation with NeRF or 3DGS.
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/supp/supp_cls_partcraft.jpg)

> 🔼 그림 14는 생성된 객체의 정면과 측면 사진을 사용하여 이미지를 3D로 변환하는 과정을 보여줍니다. InstantMesh를 사용하여 이미지를 3D 객체로 빠르게 변환하지만, 때때로 Zero123Plus 모델이 해당 객체나 유사한 객체를 학습하지 못했을 경우 부정확한 변환이 발생할 수 있습니다.  InstantMesh는 6개의 뷰를 예측하는 Zero123Plus에 의존하기 때문에 발생하는 제약입니다.  이러한 문제는 이미지에서 멀티뷰 모델을 미세 조정하는 데 필요한 3D 기반 데이터가 부족하기 때문입니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: Image-to-3D using front view and side view of generated object.
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/supp/supp_cls_ours_d32_kl001.jpg)

> 🔼 이 그림은 본 논문의 C. Other domains 섹션에 포함되어 있으며, 개의 품종을 혼합하여 새로운 품종을 생성하는 실험 결과를 보여줍니다. (a)에서는 차우차우와 골든 리트리버, 폼피니언과 퍼그를 혼합한 결과를 보여줍니다.  각 혼합 품종은 기존 품종들의 특징이 혼합된 새로운 외형을 가지고 있으며,  본 논문에서 제시하는 방법론의 다양한 품종 생성 능력을 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> (a) Mixing chow with golden retriever, pomeranian with pug.
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/supp/supp_cls_target.jpg)

> 🔼 그림 (b)는 본 논문에서 제시된 방법을 사용하여 생성된 새로운 동물 이미지들을 보여줍니다. 햄스터와 고양이, 햄스터와 말, 코끼리와 말을 결합한 새로운 종류의 동물들이 생성되었음을 보여줍니다. 이는 본 논문의 방법이 기존의 데이터셋에 존재하지 않는 새로운 형태의 객체를 생성할 수 있음을 시사합니다.  이러한 새로운 객체들은 단순히 기존 객체의 조합이 아니라, 새로운 특징들을 가지는 독창적인 결과물임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) Hamster-cat, Hamster-horse, Elephant-horse
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/supp/supp_random_ti.jpg)

> 🔼 그림 15는 제안된 방법의 다양한 적용 분야를 보여줍니다. (a)에서는 스탠포드 도그 데이터셋으로 훈련된 모델을 사용하여 기존 견종과 새로운 견종의 하이브리드를 생성한 결과를 보여줍니다. (b)에서는 다양한 동물 종을 포함하는 데이터셋으로 훈련된 모델을 사용하여 새로운 동물 종을 생성한 결과를 보여줍니다.  이를 통해 제안된 모델이 다양한 세분화된 객체 생성 작업에 적용될 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 15: (a) Dog generation. (b) Animal generation.
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/supp/supp_random_partcraft.jpg)

> 🔼 이 그림은 논문의 실험 결과 중 하나로, 'a bird, 3d asset' 이라는 간략한 제목으로 표현되어 있습니다. 이는 다양한 종류의 새를 3D 모델로 생성하는 모델의 성능을 보여주는 예시입니다. 그림은 새의 3D 모델을 여러 각도에서 보여주는 다양한 이미지들로 구성되어 있으며, 모델이 다양한 종류의 새를 정확하게 생성할 수 있음을 시각적으로 보여줍니다.  더 자세히 설명하자면,  논문에서 제시하는 Chirpy3D 모델이 텍스트 프롬프트(`a bird`)를 입력받아 실제로 존재하는 다양한 종류의 새들을 현실감 있게 3D 모델로 생성할 수 있음을 보여주는 예시입니다.  각 이미지는 모델의 생성 결과이며, 여러 각도에서 촬영된 듯한 다양한 시점의 이미지들이 포함되어 있습니다. 이를 통해 모델이 새의 형태를 입체적으로 잘 이해하고 있다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (a) a bird, 3d asset.
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/supp/supp_random_ours_d32_kl001.jpg)

> 🔼 이 그림은 논문의 실험 결과 중 하나로, 'cardinal' 이라는 세세한 종류를 지정하여 생성한 3D 새 모델을 보여줍니다.  단순히 '새' 라고만 지정했을 때보다 더욱 정교하고 사실적인 3D 모델이 생성되었음을 보여주는 예시입니다. 여러 각도에서 바라본 새의 모습을 보여주어, 3D 모델의 완성도를 시각적으로 확인할 수 있게 합니다.  각 이미지는 서로 다른 랜덤 시드를 사용하여 생성되었지만, 모두 카디널 새의 특징을 잘 나타내고 있습니다.
> <details>
> <summary>read the caption</summary>
> (b) a cardinal, 3d asset.
> </details>



![](https://arxiv.org/html/2501.04144/x10.png)

> 🔼 그림 16은 MVDream [52]을 사용하여 텍스트 프롬프트를 통해 생성된 다중 뷰 이미지를 보여줍니다. 가이드 스케일은 7.5로 설정되어 있습니다. 각 행은 다른 시드(seed)를 사용하여 생성되었으며, (a)는 일반적인 'bird' 토큰을 사용했을 때 시드에 따라 생성 결과가 다양하게 나타나는 반면, (b)는 보다 세분화된 'cardinal' 토큰을 사용했을 때 시드에 관계없이 매우 유사한 결과물이 생성되는 것을 보여줍니다. 이는 세분화된 토큰을 사용하면 SDS 손실에 대한 가이드 스케일을 낮출 수 있으며, 과포화 효과 없이 3D 생성이 가능함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 16: Multi-view generation with text prompt through MVDream [52]. The guidance scale is 7.5. Each row is a different seed. (a) The generation varies for different seeds for the token “bird”. (b) The generation with a fine-grained token “cardinal”. As highly similar objects are generated for each seed, we can use a lower guidance scale for SDS loss and enable 3D generation without oversaturated effect.
> </details>



![](https://arxiv.org/html/2501.04144/x11.png)

> 🔼 그림은 논문의 실험 결과 중 하나로, Textual Inversion 방법을 사용하여 생성한 이미지들을 보여줍니다.  Textual Inversion은 텍스트를 기반으로 이미지를 생성하는 방법론 중 하나이며, 이 그림에서는 해당 방법을 사용하여 생성한 결과물의 다양성이나 질을 평가하기 위한 목적으로 사용된 것으로 보입니다. 그림에는 다양한 종류의 새 이미지들이 여러 각도로 표현되어 있으며, 각 이미지의 세부적인 특징과 전체적인 구성에 대한 비교 분석을 통해 Textual Inversion의 성능을 평가하는 데 도움을 줄 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (a) Textual Inversion
> </details>



![](https://arxiv.org/html/2501.04144/x12.png)

> 🔼 그림은 논문의 Part Composition 부분에 속하며, PartCraft 모델이 부분 조합 작업을 수행한 결과를 보여줍니다.  PartCraft는 기존의 부분들을 조합하여 새로운 이미지를 생성하는 방식을 사용합니다. 그림은 기존 이미지의 일부 부분을 다른 이미지의 해당 부분으로 교체하여 생성한 결과물들을 보여주는 것으로 보입니다.  각 이미지는 소스 이미지와 타겟 이미지, 그리고 PartCraft 모델을 사용하여 생성된 이미지로 구성되어 있습니다. 이를 통해 PartCraft 모델이 부분 단위로 이미지를 조작하고 조합하는 능력을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) PartCraft
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/supp/supp_consistency_random_baseline.jpg)

> 🔼 그림은 논문의 실험 결과 중 하나로, 제안된 Chirpy3D 모델을 사용하여 생성된 새 이미지들을 보여줍니다.  Chirpy3D는 다양한 부분들로 구성된 고품질의 3D 새를 생성하는 데 뛰어난 성능을 보입니다. 특히, 기존 종과 유사하면서도 새로운 특징을 가진 창의적인 새들을 생성할 수 있다는 것을 보여줍니다. 이미지들은 다양한 각도에서 보이는 여러 뷰로 구성되어 있어, 3D 모델의 완성도를 더욱 잘 나타냅니다.
> <details>
> <summary>read the caption</summary>
> (c) Chirpy3D (Ours)
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/supp/supp_consistency_random_ours_d4.jpg)

> 🔼 그림 (d)는 논문의 실험 결과 중 하나로, 기존 종(existing species)에 대한 다양한 시각에서의 이미지 생성 결과를 보여줍니다.  Textual Inversion, PartCraft, 그리고 Chirpy3D 세 가지 방법을 사용하여 생성한 이미지가 각각 제시되어 있으며, 각 방법의 이미지 품질, 다양성, 그리고 정확성을 비교 분석하는 데 활용됩니다. 특히 Chirpy3D는 다른 두 방법에 비해 더욱 사실적이고 다양한 이미지를 생성하는 것을 보여줍니다. 각각의 이미지는 다양한 각도에서 촬영된 여러 장의 사진으로 구성되어 있으며, 각 종의 특징이 잘 드러나도록 세부적인 부분까지 고려하여 생성되었습니다.
> <details>
> <summary>read the caption</summary>
> (d)
> </details>



![](https://arxiv.org/html/2501.04144/x13.png)

> 🔼 그림 17은 기존 종에 대한 다중 뷰 생성 결과를 보여줍니다. 세 가지 방법(Textual Inversion, PartCraft, Chirpy3D)으로 학습된 모델이 각각 생성한 이미지들을 비교하여 보여줍니다. (a), (b), (c)는 각각 세 가지 방법으로 생성한 이미지들을, (d)는 해당 종의 실제 이미지 하나를 보여줍니다. Chirpy3D는 Textual Inversion과 PartCraft보다 다중 뷰 관점에서 더욱 정확하게 재구성하며, 생성된 이미지의 방향성이 일관되고 배경이 깔끔하다는 것을 보여줍니다.  즉, 기존 종을 대상으로 한 실제 이미지와 생성 이미지의 비교를 통해 Chirpy3D 모델의 우수성을 시각적으로 보여주는 그림입니다.
> <details>
> <summary>read the caption</summary>
> Figure 17: Multi-view generation on existing species, trained with respective methods (a, b, c). (d) One of the training images of the species. Not only our Chirpy3D (c) can reconstruct well in multi-view perspective comparing to Textual Inversion (a) and PartCraft (b), but our generated images are also consistent in terms of orientation and cleaner background.
> </details>



![](https://arxiv.org/html/2501.04144/x14.png)

> 🔼 그림은 논문의 실험 결과를 보여주는 것으로, 세 가지 다른 방법(Textual Inversion, PartCraft, Chirpy3D)을 사용하여 생성된 이미지들을 보여줍니다. 각 방법은 다양한 종류의 새들을 생성하며, Textual Inversion은 품질이 낮고 일관성이 부족한 반면, PartCraft는 품질이 더 높지만 다양성이 부족하며, Chirpy3D는 고품질의 이미지를 생성하고 다양성도 풍부하다는 것을 보여줍니다. 이를 통해 Chirpy3D 모델이 고품질의 다양한 새 이미지를 생성하는 데 효과적임을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (a) Textual Inversion
> </details>



![](https://arxiv.org/html/2501.04144/x15.png)

> 🔼 그림은 논문의 Part Composition 부분에 속하며, PartCraft 모델이 다양한 조류의 부분들을 조합하여 새로운 조류 이미지를 생성하는 과정을 보여줍니다.  PartCraft는 기존의 부분들을 조합하는 방식으로 새로운 이미지를 생성하지만, Chirpy3D와 비교했을 때 세밀한 부분과 다양성이 부족함을 보여주는 대조군 역할을 합니다.  이 그림을 통해 기존 모델과 Chirpy3D 모델의 생성 능력을 비교 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (b) PartCraft
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/supp/scale1.jpg)

> 🔼 그림은 논문의 실험 결과 중 하나로, 제안된 Chirpy3D 모델을 사용하여 생성된 다양한 새들의 3D 모델들을 보여줍니다.  Chirpy3D는 기존 방법들과 달리, 부분 단위의 연속적인 잠재 공간을 학습하여 새로운 종류의 새를 창의적으로 생성할 수 있습니다. 그림에서는 기존 종의 새들과 새로운 종의 새들을 함께 보여주어 Chirpy3D 모델의 창의적인 3D 조류 생성 능력을 강조합니다.  각 새는 다양한 부품들로 구성되어 있으며, 이러한 부품들은 서로 다른 종류의 새들에서 가져온 것들이거나, 모델이 스스로 새롭게 생성해낸 것들입니다. 이를 통해 Chirpy3D가 단순히 기존 객체를 모방하는 것이 아니라 새로운 것을 창조할 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (c) Chirpy3D (Ours)
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/supp/scale01.jpg)

> 🔼 그림 18은 서로 다른 방법으로 학습된 세 가지 모델(Textual Inversion, PartCraft, Chirpy3D)을 사용하여 새로운 종(novel species)의 새를 생성한 결과를 보여줍니다. 모든 이미지는 동일한 시드(seed)를 사용하여 생성되었지만, 서로 다른 부분잠재변수(part latents)를 샘플링했습니다. (a) Textual Inversion으로 학습된 모델은 단어 임베딩 공간에서 직접 샘플링하기 때문에 생성된 이미지가 종종 이해할 수 없으며 새로운 종을 생성하기에 부적절함을 보여줍니다. (b) PartCraft는 단어 임베딩을 투영하는 비선형 프로젝터를 가지고 있어 이해할 수 있는 개체를 생성할 수 있지만, 연속적인 부분잠재변수 분포로 학습되지 않았기 때문에 다양성이 부족합니다. (c) Chirpy3D는 다양한 종의 새 이미지를 안정적으로 생성할 수 있을 뿐만 아니라, 새의 자세도 일관성 있게 유지합니다.
> <details>
> <summary>read the caption</summary>
> Figure 18: Multi-view generation on novel species (random sampling), trained with respective methods. All were generated with the same seed but with different sampled part latents. (a) Trained with Textual Inversion, the generated images are often incomprehensible, indicating that direct sampling from word embedding space is insufficient to generate novel species. (b) PartCraft has a non-linear projector to project word embeddings, while able to generate comprehensible objects, but lacking diversity since it is not trained to have a continuous distribution of part latents. (c) Our Chirpy3D not only can generate images of diverse species, also stable in terms of bird pose.
> </details>



![](https://arxiv.org/html/2501.04144/extracted/6117322/figs/supp/scale001.jpg)

> 🔼 그림은 논문의 실험 결과 중 하나로, Textual Inversion 방법을 사용하여 생성한 이미지들을 보여줍니다. Textual Inversion은 텍스트를 이미지로 변환하는 기법 중 하나이며, 이 그림에서는 이 기법을 통해 생성된 다양한 새 이미지들을 보여줍니다.  본 그림은 단순히 새 이미지들을 나열한 것 이상으로, Textual Inversion 방법의 성능이나 특징을 보여주기 위한 시각적 증거로 활용됩니다.  이미지들의 세부적인 특징이나 다양성, 품질 등을 통해 Textual Inversion의 강점과 약점을 간접적으로 판단할 수 있도록 돕습니다.
> <details>
> <summary>read the caption</summary>
> (a) Textual Inversion
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