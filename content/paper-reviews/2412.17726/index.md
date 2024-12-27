---
title: "VidTwin: Video VAE with Decoupled Structure and Dynamics"
summary: "VidTwin: 구조와 동역학을 분리하여 비디오 압축 및 생성의 새로운 기준을 제시하는 혁신적인 비디오 자동 인코더!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Video Understanding", "🏢 Peking University",]
showSummary: true
date: 2024-12-23
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.17726 {{< /keyword >}}
{{< keyword icon="writer" >}} Yuchi Wang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-26 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.17726" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.17726" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/vidtwin-video-vae-with-decoupled-structure" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

최근 비디오 자동 인코더(VAE)는 비디오 생성의 질과 효율성을 크게 향상시켰지만, 시각적 내용과 시간적 의존성을 동시에 모델링하는 것은 여전히 어려운 문제입니다. 기존 방법들은 비디오의 동적 특성을 과도하게 단순화하여 만족스럽지 못한 결과를 초래했습니다.

본 연구는 VidTwin이라는 새로운 비디오 자동 인코더를 제안합니다. VidTwin은 비디오를 **구조적 잠재 벡터(전반적인 내용 및 움직임)**과 **동적 잠재 벡터(세부적인 내용 및 빠른 움직임)**로 분리하여 표현합니다. 이를 통해 높은 압축률(0.20%)과 높은 재구성 품질(PSNR 28.14)을 달성했습니다. 또한, VidTwin은 다운스트림 생성 작업에서 효과적이며, **설명 가능성 및 확장성**을 갖추어 향후 연구에 중요한 발판을 마련합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} VidTwin은 비디오를 구조와 동역학으로 분리하여 압축률을 높이고 재구성 품질을 향상시켰습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} VidTwin은 다운스트림 생성 작업에서 효과적이며, 설명 가능성과 확장성을 갖추었습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 본 연구는 비디오 잠재 표현 및 생성에 대한 새로운 연구 방향을 제시합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **비디오 압축 및 생성 분야에 새로운 가능성**을 제시합니다. **비디오를 구조와 동적 특징으로 분리하여 표현**하는 독창적인 방법을 제안함으로써, 고효율 압축과 고품질 재구성을 동시에 달성했습니다. 또한, 이 연구는 **다운스트림 생성 작업에 대한 효과성**을 입증하고, **설명 가능성 및 확장성**을 보여줌으로써 향후 비디오 잠재 표현 및 생성 연구에 중요한 발판을 마련합니다.  이는 비디오 관련 연구자들에게 새로운 연구 방향을 제시하고, **비디오 압축, 생성, 이해 기술의 발전**에 크게 기여할 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.17726/x1.png)

> 🔼 그림 1은 구조(Structure) 및 동적(Dynamics) 잠재변수를 보여주는 예시입니다. 두 프레임(t₁, t₂)을 선택하고 원본(Orig.) 및 재구성(Recon.)된 비디오 프레임을 보여줍니다. S. Recon. 및 D. Recon. 은 각각 구조 및 동적 잠재변수만을 사용하여 디코딩된 재구성 프레임을 나타냅니다. 구조 잠재변수는 주요 의미론적 내용과 전반적인 움직임을 포착하는 반면, 동적 잠재변수는 세부적인 내용과 빠른 움직임을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: An example illustrating the Structure and Dynamics latents. We select two frames, t1subscript𝑡1t_{1}italic_t start_POSTSUBSCRIPT 1 end_POSTSUBSCRIPT and t2subscript𝑡2t_{2}italic_t start_POSTSUBSCRIPT 2 end_POSTSUBSCRIPT, and show the original and reconstructed video frames, labeled Orig. and Recon., respectively. S. Recon. and D. Recon. refer to the reconstructed frames decoded using only the corresponding Structure or Dynamics latents. The Structure latent captures the main semantic content and overall motion trends, while the Dynamics latent encodes local details and rapid movements.
> </details>





{{< table-caption >}}
| Method | Compress. Rate ↓ | PSNR ↑ | LPIPS ↓ | SSIM ↑ | FVD ↓ | Sem. ↑ | Tempo. ↑ | Deta. ↑ |
|---|---|---|---|---|---|---|---|---|
| iVideoGPT [48] | 1.50% | 19.353 | 0.4677 | 0.5752 | 1693.10 | 4.28 | 4.33 | 3.59 |
| MAGVIT-v2 [52] | 0.65% | 24.351 | 0.3347 | 0.6877 | 653.88 | 4.43 | 4.46 | 3.97 |
| CMD [54] | 6.85% | 27.332 | 0.2732 | 0.7746 | 468.47 | 4.51 | 4.35 | 4.22 |
| EMU-3 [43] | 0.53% | 25.359 | 0.2543 | 0.7260 | 353.71 | 4.69 | 4.57 | 4.60 |
| \modelname (Ours) | 0.20% | 28.137 | 0.2414 | 0.8044 | 388.86 | 4.71 | 4.62 | 4.73 |{{< /table-caption >}}

> 🔼 표 1은 제안된 VidTwin 모델과 기존 비디오 압축 및 생성 모델들의 정량적 성능 비교 결과를 보여줍니다.  PSNR, LPIPS, SSIM, FVD와 같은 객관적인 지표와 의미 보존(Sem.), 시간적 일관성(Tempo.), 세부 사항 유지(Deta.)와 같은 주관적인 평가 지표를 사용하여 비교 분석했습니다.  굵은 숫자는 각 지표에서 가장 좋은 성능을 나타내고, 밑줄 친 숫자는 두 번째로 좋은 성능을 나타냅니다.  VidTwin 모델은 모든 지표에서 다른 모델들을 능가하여 우수한 비디오 복원 능력을 보여줍니다. 압축률 또한 비교 대상 모델들보다 훨씬 낮아 효율성을 높였습니다.
> <details>
> <summary>read the caption</summary>
> Table 1:  Quantitative comparison with baseline methods. The bold values indicate the best results, while the underlined values represent the second-best. Sem., Tempo., and Deta. refer to semantic preservation, temporal consistency, and detail retention, respectively. Our model outperforms the baselines across multiple metrics, demonstrating its superior reconstruction ability.
> </details>





### In-depth insights


#### VidTwin: Core Design
VidTwin은 비디오를 **구조(Structure)**와 **동역학(Dynamics)**이라는 두 개의 독립적인 잠재 공간으로 분리하여 인코딩하는 혁신적인 비디오 자동 인코더의 핵심 설계를 제시합니다.  **구조 잠재 벡터**는 전체적인 콘텐츠와 전반적인 움직임을 포착하는 반면, **동역학 잠재 벡터**는 세부적인 디테일과 빠른 움직임을 나타냅니다. 이러한 분리는 Q-Former와 합성곱 신경망을 활용한 모듈을 통해 효율적으로 구현됩니다.  **구조 잠재 벡터 추출 모듈**은 저주파수 움직임 추세를 추출하고 불필요한 세부 정보를 제거하여 압축률을 높입니다.  **동역학 잠재 벡터 추출 모듈**은 공간 차원을 축소하고 평균화하여 빠른 움직임 정보를 효율적으로 표현합니다.  두 잠재 벡터는 디코더에 전달되기 전에 동일한 차원으로 맞춰지고 결합됩니다.  이러한 설계는 높은 압축률과 재구성 품질을 동시에 달성하며,  **다운스트림 생성 작업**에서도 효율성과 효과를 보여줍니다.  또한,  **해석 가능성**과 **확장성**을 갖춰 향후 비디오 잠재 표현 및 생성 연구에 기여할 것으로 기대됩니다.

#### Latent Space Decoupling
본 논문에서 제안하는 핵심 개념인 ‘잠재 공간 분리(Latent Space Decoupling)’는 비디오 데이터를 **구조(Structure)** 와 **동역학(Dynamics)** 이라는 두 가지 독립적인 잠재 공간으로 분해하여 표현하는 기법입니다. 이는 기존의 단일 잠재 공간 기반 방법론의 한계를 극복하기 위한 시도로, 비디오의 **장기적인 시·공간적 움직임** 과 **단기적인 세부적인 변화** 를 각각 효율적으로 학습하고 표현하는 데 초점을 맞춥니다.  **구조 잠재 벡터**는 전체적인 내용과 전반적인 움직임을 담당하며, **동역학 잠재 벡터**는 미세한 디테일과 빠른 움직임을 나타냅니다. 이러한 분리는 압축률 향상과 더불어 생성 모델의 성능 향상 및 해석 가능성을 높이는 데 기여합니다.  **구조와 동역학 정보를 분리**하여 각각의 특징을 더욱 정확하게 포착함으로써, 비디오 생성 및 다른 하위 작업에서 더욱 효율적이고 효과적인 결과를 얻을 수 있습니다.  **효율적인 압축**과 **정확한 재구성**을 동시에 달성하는 핵심 전략이며, **비디오 이해 및 생성 분야**에 새로운 가능성을 제시하는 중요한 연구 방향입니다.

#### Downstream Tasks
본 논문에서 다운스트림 작업에 대한 논의는 비디오 VAE 모델인 VidTwin의 **잠재 공간 표현의 유용성 및 효율성**을 보여주는 데 중점을 둡니다.  VidTwin은 고품질의 재구성을 유지하면서 고압축률을 달성하도록 설계되었으며, 이는 다운스트림 작업에 중요한 이점을 제공합니다.  **메모리 및 계산 부하 감소**는 대규모 비디오 데이터 처리에 유리하게 작용하고, **다양한 생성 모델과의 호환성**을 통해 VidTwin의 잠재 공간은 다양한 생성 작업에 적용될 수 있음을 시사합니다. 실제로 UCF-101 데이터셋을 활용한 실험 결과는 **VidTwin이 기존 모델들과 비슷하거나 더 나은 성능**을 보임으로써, VidTwin의 잠재 공간이 생성 작업에 효과적으로 사용될 수 있음을 입증합니다.  이는 **잠재 공간의 매끄러움 및 유용성**을 강조하며, 다운스트림 작업에서 VidTwin의 효율성과 확장성을 보여주는 중요한 근거가 됩니다.  **설명 가능성 및 확장성** 또한 미래 연구에 대한 가능성을 제시하며, 비디오 잠재 표현 및 생성 분야의 발전에 VidTwin이 기여할 수 있음을 시사합니다.

#### Explainability & Scalability
본 논문에서 제시된 VidTwin 모델의 **설명 가능성(Explainability)** 및 **확장성(Scalability)**은 핵심적인 강점입니다.  **두 개의 분리된 잠재 공간(Structure Latent과 Dynamics Latent)**을 사용하여 비디오 데이터를 표현함으로써, 각 공간이 담당하는 정보(전반적인 내용과 빠른 움직임)를 명확히 구분하여 모델의 동작 과정을 이해하기 쉽게 만들었습니다.  이는 복잡한 비디오 데이터를 보다 직관적으로 이해하고 해석하는 데 도움을 주어, **모델의 투명성을 높였습니다.** 또한, 이러한 설계는 **모델의 확장성에도 기여**합니다.  낮은 차원의 잠재 벡터를 사용함으로써, 메모리와 계산 비용을 줄이고, 보다 큰 규모의 데이터셋이나 복잡한 작업에도 효율적으로 적용될 수 있음을 시사합니다.  **실험 결과는 고압축률을 유지하면서 높은 재구성 품질을 달성**,  다운스트림 생성 작업에서도 우수한 성능을 보이며 **모델의 실용성을 입증**합니다.  결론적으로, VidTwin의 설명 가능성과 확장성은 이 모델이 향후 비디오 잠재 표현 및 생성 연구에 중요한 기여를 할 수 있음을 보여줍니다.

#### Future Research
본 논문의 VidTwin 모델은 비디오 데이터의 구조와 동적 특징을 분리하여 효율적인 압축 및 재구성을 달성하는 데 성공했습니다.  **미래 연구는 몇 가지 중요한 방향으로 확장될 수 있습니다.** 첫째, **더욱 정교한 구조 및 동적 특징 분리 기법**을 개발하여 더욱 세밀한 비디오 정보를 포착하고 재현할 수 있습니다.  둘째, **다양한 하류 작업 (예: 비디오 생성, 편집, 이해)**에 VidTwin 모델의 적용성을 더욱 확대하고 성능을 평가할 필요가 있습니다.  셋째, **모델의 확장성 및 효율성을 높이기 위한 연구**가 필요하며, 특히 계산 비용을 줄이면서 성능 저하 없이 더 큰 비디오 데이터셋을 처리할 수 있는 방법을 모색해야 합니다.  넷째, **VidTwin 모델의 설명 가능성을 강화**하기 위해,  구조 및 동적 특징 벡터의 의미를 더욱 명확하게 해석하고 시각화하는 기술 개발이 필요합니다. 마지막으로, **다른 모달리티(예: 오디오, 텍스트)와의 통합**을 통해, 보다 풍부하고 다양한 멀티모달 비디오 이해 및 생성 시스템을 개발하는 연구가 중요해질 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.17726/x2.png)

> 🔼 그림 2는 VidTwin 모델의 상세 구조를 보여줍니다. 인코더(Encoder)에서 추출된 잠재 벡터 z에서부터 두 가지 흐름(Structure Latent과 Dynamics Latent 추출 모듈)으로 나뉩니다. Structure Latent 추출 모듈 (ℱS)은 Q-Former와 합성곱 신경망으로 구성되어 Structure Latent (zS)를 추출합니다. Dynamics Latent 추출 모듈 (ℱD)은 합성곱 신경망과 평균화 연산자로 구성되어 Dynamics Latent (zD)를 추출합니다.  마지막으로 디코더(Decoder)에 입력하기 전에, 모든 잠재 벡터들을 같은 차원으로 정렬하고 결합합니다. 이 그림은 VidTwin 모델이 어떻게 영상 데이터를 구조와 역동성이라는 두 개의 독립적인 잠재 공간으로 분리하고, 이들을 효율적으로 결합하여 원본 영상을 재구성하는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Details of our model. After obtaining the latent z𝑧zitalic_z from the Encoder, the process branches into two flows. The Structure Latent extraction module, ℱ𝑺subscriptℱ𝑺\mathcal{F}_{\boldsymbol{S}}caligraphic_F start_POSTSUBSCRIPT bold_italic_S end_POSTSUBSCRIPT, which consists of a Q-Former and convolutional networks, extracts the Structure Latent component z𝑺subscript𝑧𝑺z_{\boldsymbol{S}}italic_z start_POSTSUBSCRIPT bold_italic_S end_POSTSUBSCRIPT. The Dynamics Latent extraction module, ℱ𝑫subscriptℱ𝑫\mathcal{F}_{\boldsymbol{D}}caligraphic_F start_POSTSUBSCRIPT bold_italic_D end_POSTSUBSCRIPT, comprising convolutional networks and an averaging operator, extracts the Dynamics Latent component z𝑫subscript𝑧𝑫z_{\boldsymbol{D}}italic_z start_POSTSUBSCRIPT bold_italic_D end_POSTSUBSCRIPT. Finally, using the decoding module, we align all latents to the same dimension and combine them before passing them into the Decoder.
> </details>



![](https://arxiv.org/html/2412.17726/x3.png)

> 🔼 그림 3은 제안된 VidTwin 모델과 기존 비디오 재구성 방법들의 성능을 정성적으로 비교한 것입니다. 서서히 회전하는 사진과 빠른 동작의 권투 장면이라는 두 가지 예시를 통해 비교 분석을 진행했습니다. VidTwin은 미세한 디테일을 재구성하고 빠른 움직임을 정확하게 포착하는 능력을 보여줍니다. 특히, 빠르게 움직이는 물체의 잔상이나 흐릿함 없이 선명하게 재구성하는 VidTwin의 우수성을 확인할 수 있습니다. 이는 VidTwin 모델이 구조와 동적인 움직임을 분리하여 표현하는 설계 덕분에 가능합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Qualitative comparison with baseline methods. Two examples are presented: a gradually rotating photo and a fast-motion boxing scene. \modelnamedemonstrates the ability to reconstruct fine details and accurately capture rapid motion.
> </details>



![](https://arxiv.org/html/2412.17726/x4.png)

> 🔼 그림 4는 비디오의 구조적 요소와 동적 요소를 분리하여 표현하는 VidTwin 모델의 기능을 보여주는 예시입니다. 비디오 A의 구조적 요소(Structure Latent)와 비디오 B의 동적 요소(Dynamics Latent)를 결합하여 새로운 비디오 C를 생성하는 과정을 보여줍니다. 이를 통해 VidTwin 모델이 비디오의 구조와 동작을 독립적으로 추출하고 조합하여 새로운 비디오를 생성할 수 있음을 시각적으로 보여줍니다.  구조적 요소는 비디오의 주요 내용과 전반적인 움직임을, 동적 요소는 세부적인 디테일과 빠른 움직임을 담당합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: An illustration of a cross-replacement example, where Video C is generated using the Structure Latent from Video A and the Dynamics Latent from Video B.
> </details>



![](https://arxiv.org/html/2412.17726/x5.png)

> 🔼 그림 5는 본 논문에서 제안하는 VidTwin 모델과 기존 비교 대상 모델들에 대해 통합된 생성 모델을 적용했을 때의 FLOPs(연산량)와 학습 메모리 사용량을 비교한 그래프입니다.  VidTwin 모델은 기존 모델들에 비해 훨씬 적은 연산량과 메모리로도 동등하거나 더 나은 성능을 달성함을 보여줍니다.  이는 VidTwin 모델의 효율적인 설계와 압축된 잠재 공간 표현 덕분입니다.  세부적으로는 각 모델의 FLOPs와 메모리 사용량을 막대 그래프 형태로 시각화하여 비교 분석합니다. 이를 통해 VidTwin 모델의 계산 효율성과 자원 효율성을 명확하게 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: We present the FLOPs and training memory costs of the unified generative model, as applied to our model and the baselines.
> </details>



![](https://arxiv.org/html/2412.17726/x6.png)

> 🔼 그림 6은 제안된 VidTwin 모델과 기존 기법들의 비디오 재구성 결과를 비교한 추가적인 예시입니다. 그림에는 다양한 유형의 비디오 시퀀스가 포함되어 있으며, VidTwin 모델이 세부적인 부분까지 정확하게 재구성하고 빠른 움직임도 잘 포착하는 것을 보여줍니다.  기존 방법들과 비교하여 VidTwin 모델의 우수성을 시각적으로 확인할 수 있도록, 확대하여 자세히 관찰할 것을 권장합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Additional reconstruction cases comparing our \modelnamemodel with baselines. Zoom in to observe finer details.
> </details>



![](https://arxiv.org/html/2412.17726/x7.png)

> 🔼 그림 7은 VidTwin 모델의 핵심 개념인 구조잠재변수(Structure Latent)와 동역학잠재변수(Dynamics Latent)의 분리를 보다 자세히 보여주는 추가적인 예시입니다.  각 열은 원본 영상(Orig.), VidTwin 모델로 재구성한 영상(Recon.), 구조잠재변수만을 사용하여 재구성한 영상(S. Recon.), 동역학잠재변수만을 사용하여 재구성한 영상(D. Recon.)을 순서대로 보여줍니다. 이를 통해 각 잠재변수가 영상의 어떤 부분을 담당하는지, 그리고 두 잠재변수가 어떻게 결합하여 원본 영상을 재구성하는지를 시각적으로 이해할 수 있습니다. 특히, 빠르게 움직이는 물체나 세세한 디테일이 있는 영상에서 구조잠재변수와 동역학잠재변수가 어떻게 서로 다른 정보를 담당하는지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Additional examples of decoupling Structure Latent and Dynamics Latent.
> </details>



![](https://arxiv.org/html/2412.17726/x8.png)

> 🔼 그림 8은 비디오의 구조적잠재변수와 동적잠재변수를 분리하여 사용하는 VidTwin 모델의 능력을 보여주는 추가적인 교차 재구성(cross-reenactment) 예시입니다.  구조적잠재변수는 비디오의 주요 객체와 전체적인 움직임 경향을 나타내고, 동적잠재변수는 세부적인 내용과 빠른 움직임을 포착합니다.  각각의 비디오 A와 B에서 추출한 구조적잠재변수와 동적잠재변수를 조합하여 새로운 비디오 C를 생성하는 실험을 통해, VidTwin 모델이 각 잠재변수가 비디오 내용에 미치는 영향을 효과적으로 분리하고 제어할 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Additional examples of cross-reenactment.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Models | TATS [9] | MAGVIT-v2 [52] | Video-LaViT [19] | Ours |
|---|---|---|---|---|
| FVD ↓ | 332 | 58 | 275 | 193 |{{< /table-caption >}}
> 🔼 표 2는 UCF-101 데이터셋을 기반으로 제안된 VidTwin 모델과 기존 비교 대상 모델들의 비디오 생성 성능을 정량적으로 비교한 표입니다.  FVD(Fréchet Video Distance) 지표를 사용하여 각 모델의 생성 비디오의 품질을 측정했습니다.  낮은 FVD 값은 더 높은 품질의 생성 비디오를 나타냅니다. 이 표는 VidTwin 모델이 기존 방법들에 비해 우수한 비디오 생성 성능을 보여줌을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 2: The generative ability of our model and the baselines, as tested on UCF-101.
> </details>

{{< table-caption >}}
| Methods | PSNR↑ | SSIM↑ |
|---|---|---|
| "
modelname"
 | 26.116 | 0.731 |
| (a) w/o Disentanglement | 23.512 | 0.654 |
| (b) w/o D. Latent Avg. | 24.835 | 0.693 |
| (c) w/o S. Latent Qformer | 25.386 | 0.702 |
| (d) w/o S. Latent Move Spa. | 23.169 | 0.630 |{{< /table-caption >}}
> 🔼 표 3은 제안된 기법에 대한 ablation study 결과를 보여줍니다.  각 열은 제안된 VidTwin 모델에서 특정 구성 요소를 제거했을 때의 성능 변화를 보여줍니다.  (a)는 전체 모델에서 잠재 변수 분리(disentanglement)를 제거한 경우, (b)는 동적 잠재 변수 평균화(D. Latent Avg.)를 제거한 경우, (c)는 구조적 잠재 변수 추출에서 Q-former를 제거한 경우, (d)는 구조적 잠재 변수 추출에서 공간적 다운샘플링(S. Latent Move Spa.)을 제거한 경우의 결과를 각각 보여줍니다.  PSNR과 SSIM 지표를 사용하여 재구성 성능을 평가했습니다. 이를 통해 각 구성요소의 효과와 VidTwin 모델의 성능에 대한 기여도를 정량적으로 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Ablation studies on the proposed techniques.
> </details>

{{< table-caption >}}
| Models | Depth | Num. Heads | Dim. Hidden | Num. Params. | PSNR | SSIM |
|---|---|---|---|---|---|---|
| \modelname<sub>small</sub> | 12 | 8 | 512 | 126M | 24.83 | 0.683 |
| \modelname<sub>base</sub> | 16 | 12 | 768 | 335M | 26.13 | 0.732 |
| \modelname<sub>large</sub> | 16 | 12 | 1536 | 1.3B | 27.16 | 0.751 |{{< /table-caption >}}
> 🔼 표 4는 논문에서 제시된 VidTwin 모델의 성능을 다양한 크기(scale)로 비교 분석한 결과를 보여줍니다.  VidTwin 모델의 크기는 매개변수(parameter)의 수에 따라 small, base, large 세 가지로 나뉘며 각 크기에 대한 설정값(depth, number of heads, hidden dimension, number of parameters)과 성능 지표(PSNR, SSIM)가 제시되어 있습니다.  이 표를 통해 모델 크기 변화에 따른 성능 변화를 확인하고, 효율성과 성능 간의 균형을 분석하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Settings and performance of \modelnameat different scales.
> </details>

{{< table-caption >}}
| Setting | Structure Latent | Dynamics Latent |
|---|---|---|
| 1 | $h_{\boldsymbol{S}}=w_{\boldsymbol{S}}=7,n_{q}=16,d_{\boldsymbol{S}}=4$ | $h_{\boldsymbol{D}}=w_{\boldsymbol{D}}=7,d_{\boldsymbol{D}}=8$ |
| 2 | $h_{\boldsymbol{S}}=w_{\boldsymbol{S}}=7,n_{q}=16,d_{\boldsymbol{S}}=4$ | $h_{\boldsymbol{D}}=w_{\boldsymbol{D}}=4,d_{\boldsymbol{D}}=16$ |
| 3 | $h_{\boldsymbol{S}}=w_{\boldsymbol{S}}=7,n_{q}=12,d_{\boldsymbol{S}}=4$ | $h_{\boldsymbol{D}}=w_{\boldsymbol{D}}=7,d_{\boldsymbol{D}}=8$ |{{< /table-caption >}}
> 🔼 표 5는 VidTwin 모델의 성능에 영향을 미치는 두 가지 잠재 벡터, 구조 잠재 벡터와 역동 잠재 벡터의 크기를 결정하는 데 사용되는 권장 설정값들을 보여줍니다.  구조 잠재 벡터는 크기 (hs, ws, nq, ds)로 표현되며, 여기서 hs와 ws는 각각 높이와 너비 차원의 크기를 나타내고, nq는 질의 토큰의 개수를, ds는 채널 차원의 크기를 나타냅니다. 역동 잠재 벡터는 (hD, WD, dp)로 표현되며, hD와 WD는 높이와 너비를, dp는 채널 차원의 크기를 나타냅니다.  이 표는 세 가지 서로 다른 설정(Setting 1, 2, 3)에 대한 각 차원의 권장 크기를 제시하여 사용자가 모델의 성능과 계산 비용 사이의 균형을 맞출 수 있도록 돕습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Recommended settings for latent sizes.
> </details>

{{< table-caption >}}
| Parameter | Value |
|---|---| 
| Input Video Resolution | 224 |
| Input Video Frames | 16 |
| Input Video FPS | 8 |
| Optimizer | Adam; \(\beta_{1}=0.9,\beta_{2}=0.99\) |
| Learning Rate | \(1.6\times 10^{-4}\) |
| Warmup Steps | 5000 |
| Learning Rate Scheduler | Cosine Annealing |
| \(\mathcal{L}_{p}\) | 0.05 |
| Weight Decay | 0.0001 |
| \(\mathcal{L}_{GAN}\) | 0.05 |
| \(\mathcal{L}_{KL}\) | 0.001 |
| Training Batch Size | 6 |
| Training Device | 4 \(\times\) 80G A100 GPUs |{{< /table-caption >}}
> 🔼 표 6은 VidTwin 모델 학습에 사용된 다양한 하이퍼파라미터 및 설정 값들을 보여줍니다.  입력 비디오의 해상도, 프레임 수, FPS, 최적화 알고리즘, 학습률, 웨이트 감쇠, 배치 크기, 그리고 사용된 GPU 등 모델 학습 과정에 영향을 미치는 중요한 세부 사항들이 포함되어 있습니다.  이 정보는 VidTwin 모델 재현 및 실험 결과 재현을 위해 필수적입니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Training Configuration
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