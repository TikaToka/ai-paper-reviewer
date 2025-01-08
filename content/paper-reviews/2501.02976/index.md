---
title: "STAR: Spatial-Temporal Augmentation with Text-to-Video Models for Real-World Video Super-Resolution"
summary: "STAR: T2V 모델 기반 실세계 비디오 초고해상도 기술로 현실적인 공간적 세부 정보와 견고한 시간적 일관성을 달성!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Video Understanding", "🏢 Nanjing University",]
showSummary: true
date: 2025-01-06
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.02976 {{< /keyword >}}
{{< keyword icon="writer" >}} Rui Xie et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-07 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.02976" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.02976" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/star-spatial-temporal-augmentation-with-text" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 GAN 기반 실세계 비디오 초고해상도(VSR) 방법들은 과도한 평활화로 인해 세부 정보가 손실되고, 시간적 일관성을 유지하는 데 어려움을 겪었습니다.  이미지 확산 모델을 VSR에 적용하는 연구가 진행되었지만, 정지된 이미지를 기반으로 학습되어 시간적 동적 특징을 제대로 포착하지 못하고 시간적 일관성이 부족한 문제가 있었습니다.  또한 실제 세계의 복잡한 저해상도 비디오에는 다양한 왜곡이 존재하기 때문에 이를 처리하는 데 어려움이 있었습니다.

본 논문에서는 이러한 문제를 해결하기 위해, 텍스트-비디오(T2V) 모델을 활용하여 실세계 비디오 초고해상도를 수행하는 새로운 방법인 STAR를 제안합니다.  **STAR는 Local Information Enhancement Module(LIEM)을 통해 국부적인 세부 정보를 풍부하게 하고 왜곡 인공물을 완화**하며, **Dynamic Frequency(DF) Loss를 통해 충실도를 높여 고품질의 복원 비디오를 생성**합니다.  **다양한 합성 및 실세계 데이터셋에서 수행한 실험을 통해 STAR가 기존 최첨단 방법들을 능가하는 성능을 보임**을 확인했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 실세계 비디오 초고해상도(VSR)에서 텍스트-비디오(T2V) 모델을 활용하여 현실적인 공간적 세부 정보와 견고한 시간적 일관성을 동시에 달성 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 새로운 Local Information Enhancement Module(LIEM)과 Dynamic Frequency(DF) Loss를 제안하여, 기존 방법의 한계점인 인공물 제거 및 충실도 향상 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 다양한 합성 및 실세계 데이터셋에서 최첨단 성능을 달성,  실세계 VSR의 성능 향상에 크게 기여 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**본 논문은 실세계 비디오 초고해상도(VSR) 분야에 텍스트-비디오(T2V) 모델을 효과적으로 통합하는 새로운 방법을 제시하여, 기존 방법들의 한계를 극복하고 현실적인 공간적 세부 정보와 견고한 시간적 일관성을 달성한 연구입니다.**  이는 **실세계 VSR의 성능 향상에 크게 기여**하며, **향후 연구를 위한 새로운 방향을 제시**할 뿐만 아니라, **T2V 모델의 응용 분야를 확장**하는데 중요한 의미를 가집니다. 특히, **저품질 비디오의 복원 품질 개선**에 대한 연구에 큰 영향을 미칠 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.02976/x2.png)

> 🔼 그림 1은 실제 및 합성 저해상도 비디오에 대한 시각적 비교 결과를 보여줍니다. 최첨단 VSR 모델(73, 75)과 비교하여 본 논문의 결과는 더욱 자연스러운 얼굴 디테일과 향상된 텍스트 구조를 보여줍니다.  즉, 기존 모델들이 얼굴 특징이나 텍스트를 흐릿하게 처리하거나 자연스럽지 못하게 복원하는 반면, 본 논문에서 제시하는 방법은 더욱 선명하고 정확하게 복원하여 시각적 품질을 향상시킵니다. 그림을 확대하여 자세히 살펴보시면 차이점을 더욱 명확히 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Visualization comparisons on both real-world and synthetic low-resolution videos. Compared to the state-of-the-art VSR models [73, 75], our results demonstrate more natural facial details and better structure of the text. (Zoom-in for best view)
> </details>





{{< table-caption >}}
| Datasets | Metrics | Real-ESRGAN | DBVSR | RealBasicVSR | RealViformer | ResShift | StableSR | Upscale-A-Video | MGLDVSR | Ours |
|---|---|---|---|---|---|---|---|---|---|---|
| UDM10 | PSNR↑ | 22.41 | 19.65 | 23.64 | **24.00** | 22.90 | 23.50 | 21.29 | 23.74 | **23.91** |
|  | SSIM↑ | 0.6476 | 0.4747 | 0.6842 | **0.6896** | 0.5451 | 0.6599 | 0.5967 | 0.6826 | **0.7164** |
|  | LPIPS↓ | 0.2769 | 0.4566 | 0.2514 | 0.2325 | 0.4036 | 0.2785 | 0.3006 | **0.2195** | **0.1885** |
|  | DOVER↑ | 0.4831 | 0.0959 | 0.5039 | 0.5055 | 0.3252 | 0.3490 | **0.5309** | 0.4896 | **0.5422** |
|  | E*warp↓ | 11.17 | 12.56 | 5.14 | 3.57 | 12.69 | 8.89 | **2.83** | 6.03 | **2.68** |
| REDS30 | PSNR↑ | 19.56 | 14.85 | **20.85** | **20.86** | 19.93 | 20.32 | 19.71 | 20.57 | 20.29 |
|  | SSIM↑ | 0.4862 | 0.2941 | **0.5469** | 0.5377 | 0.4261 | 0.5043 | 0.4315 | 0.5113 | **0.5411** |
|  | LPIPS↓ | 0.3376 | 0.5915 | 0.2899 | **0.2597** | 0.4422 | 0.3857 | 0.3443 | **0.2240** | 0.2804 |
|  | DOVER↑ | 0.3182 | 0.0600 | 0.3483 | 0.3400 | 0.2221 | 0.2519 | 0.2857 | **0.3857** | **0.4017** |
|  | E*warp↓ | 19.1 | 18.00 | 8.32 | **6.06** | 17.40 | 22.14 | 15.65 | 12.28 | **7.30** |
| OpenVid30 | PSNR↑ | 24.62 | 21.14 | 24.63 | **26.21** | 24.29 | 24.91 | 24.41 | 24.73 | **25.30** |
|  | SSIM↑ | 0.7778 | 0.5887 | 0.7759 | **0.8080** | 0.6070 | 0.7633 | 0.7167 | 0.7686 | **0.8371** |
|  | LPIPS↓ | 0.1994 | 0.4207 | 0.2297 | **0.1881** | 0.3902 | 0.2102 | 0.2479 | 0.2074 | **0.1011** |
|  | DOVER↑ | 0.6992 | 0.1819 | **0.7345** | 0.7275 | 0.5435 | 0.6368 | 0.7201 | 0.7191 | **0.7393** |
|  | E*warp↓ | 8.46 | 12.11 | 4.12 | **2.52** | 9.78 | 8.87 | 4.72 | 4.82 | **1.82** |
| VideoLQ | ILNIQE↓ | 27.95 | 27.19 | 26.29 | 26.11 | 25.92 | 29.97 | **24.49** | **23.94** | 25.35 |
|  | DOVER↑ | 0.4967 | 0.3392 | **0.5285** | 0.4804 | 0.4113 | 0.4775 | 0.4833 | 0.5319 | **0.5431** |
|  | E*warp↓ | 8.00 | 7.75 | 6.52 | **5.10** | 8.33 | 9.26 | 10.89 | 7.82 | **6.38** |{{< /table-caption >}}

> 🔼 표 1은 다양한 합성(UDM10, REDS30, OpenVid30) 및 실제(VideoLQ) 비디오 초해상도 데이터셋에서 다양한 VSR(Video Super-Resolution) 알고리즘의 정량적 성능 평가 결과를 보여줍니다.  PSNR, SSIM, LPIPS, DOVER, 그리고 Ewarp(×10⁻³) 지표를 사용하여 각 알고리즘의 성능을 비교 분석합니다. 최고 성능은 굵은 글씨체로, 두 번째로 높은 성능은 밑줄로 표시되어 있습니다. 이 표는 제시된 다양한 VSR 방법들의 상대적 성능을 정확하게 비교하고 분석하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Quantitative evaluations on diverse VSR benchmarks from synthetic (UDM10, REDS30, OpenVid30) and real-world (VideoLQ) sources. The best performance is highlighted in bold, and the second-best in underlined. Ew⁢a⁢r⁢p∗subscriptsuperscriptabsent𝑤𝑎𝑟𝑝{}^{*}_{warp}start_FLOATSUPERSCRIPT ∗ end_FLOATSUPERSCRIPT start_POSTSUBSCRIPT italic_w italic_a italic_r italic_p end_POSTSUBSCRIPT refers to Ewarp (×10−3absentsuperscript103\times 10^{-3}× 10 start_POSTSUPERSCRIPT - 3 end_POSTSUPERSCRIPT).
> </details>





### In-depth insights


#### Real-World VSR
실세계 영상 초고해상화(Real-World VSR)는 **일반적인 저해상도 영상의 다양한 왜곡**을 고려해야 하므로, 합성 데이터 기반의 기존 기법들과는 차별화된 접근 방식이 필요합니다.  **알 수 없는 왜곡** 때문에 기존 VSR 방법들은 성능 저하를 보이는데, 이를 해결하기 위해 **실제 환경의 다양한 왜곡을 반영한 데이터셋**을 활용하거나 **강인한 모델 설계**가 요구됩니다.  본 논문에서는 **텍스트-비디오 모델(T2V)**을 활용하여 실제 저해상도 영상을 초고해상도로 복원하는 새로운 방법을 제시하고, **공간적 세부 정보와 시간적 일관성**을 향상시키기 위한 다양한 기법들을 소개합니다. 특히, **국소 정보 강화 모듈(LIEM)**과 **동적 주파수 손실 함수(DF Loss)**를 통해 왜곡 제거 및 복원 성능을 높이고,  실제 환경의 복잡한 왜곡에 대한 **강건성을 확보**합니다.  **T2V 모델의 강력한 생성 능력**을 활용하여 사실적인 영상 복원을 달성하는 것이 핵심이며,  향후 실세계 VSR 연구의 중요한 방향을 제시할 것으로 기대됩니다.

#### T2V Model Fusion
본 논문에서 제시된 "T2V 모델 융합" 개념은 텍스트-비디오 모델(T2V)을 활용하여 실제 영상 초고해상도화(VSR) 성능을 향상시키는 핵심 전략입니다.  **기존의 GAN 기반 VSR 방식의 과도한 평활화 문제를 해결하기 위해 이미지 확산 모델을 적용**하는 데서 나아가, **T2V 모델을 통합하여 시간적 일관성을 유지**하는 데 초점을 맞춥니다.  이는 정지 이미지로 학습된 기존 모델의 한계를 극복하고 동적인 영상 정보를 효과적으로 포착하기 위한 시도입니다.  하지만 **실제 환경의 복잡한 저하 및 강력한 T2V 모델의 생성 능력으로 인한 충실도 저하 문제**를 동시에 해결해야 하는 어려움이 있습니다.  이러한 문제를 해결하기 위해 **국소 정보 강화 모듈(LIEM)과 동적 주파수 손실 함수(DF Loss)**를 제안하여, **공간적 디테일 향상과 시간적 일관성 유지**를 동시에 달성합니다.  결과적으로, **자연스러운 얼굴 표정 및 텍스트 구조 개선** 등을 통해 더욱 사실적인 고해상도 영상을 생성하는 데 기여합니다.

#### LIEM & DF Loss
본 논문에서 제시된 LIEM(Local Information Enhancement Module)과 DF(Dynamic Frequency) Loss는 실제 세계 영상 초해상도(VSR) 문제에 대한 혁신적인 해결책을 제시합니다.  **LIEM은 기존 T2V 모델의 글로벌 정보 추출 중심의 한계를 극복하고, 로컬 정보를 풍부하게 하여 복잡한 저화질 영상에서 발생하는 인공물 제거에 효과적**입니다.  **DF Loss는 T2V 모델의 강력한 생성 능력으로 인해 발생할 수 있는 충실도 저하 문제를 해결**하기 위해 고안되었습니다.  **초기 단계에서는 저주파 성분 복원에 집중하고, 후기 단계에서는 고주파 성분 복원에 집중**하는 동적 전략을 통해 충실도를 향상시킵니다.  즉, LIEM은 공간적 세부 묘사를 향상시키고, DF Loss는 시간적 일관성과 충실도를 보장하는 역할을 합니다.  **두 모듈의 시너지 효과는 실제 세계 영상의 복잡한 저화질 문제에 대한 강력한 해결책**을 제공하며, **기존 VSR 방법론을 뛰어넘는 성능**을 보여줍니다.

#### Ablation Study
본 논문의 "Ablation Study" 부분은 **LIEM(Local Information Enhancement Module)의 위치 및 동적 주파수 손실(DF Loss)의 다양한 변형**에 대한 영향을 분석하는 데 중점을 둡니다.  **LIEM의 위치**에 대한 실험에서는 LIEM을 공간 및 시간 블록에 추가하는 것이 가장 좋은 성능을 보였으며, 시각적 비교를 통해 국소 정보 강화의 효과를 확인했습니다.  **DF Loss의 변형**에 대한 실험은 주파수 성분을 분리하고 초기 단계에서 저주파수, 후기 단계에서 고주파수에 중점을 두는 것이 최적임을 보여줍니다.  이러한 결과는 **모델의 아키텍처 및 손실 함수의 설계**가 실제 세계 비디오 초고해상도 복원의 성능에 큰 영향을 미친다는 것을 보여주는 동시에, **STAR 모델의 설계 선택이 최적화되었음**을 강조합니다.  즉, **LIEM과 DF Loss는 STAR 모델의 성능 향상에 필수적인 요소**임을 실험적으로 증명합니다.

#### Future Directions
미래 방향에 대한 심도있는 고찰은 **STAR 모델의 확장성과 한계점**을 동시에 고려해야 합니다.  **대용량 고품질 영상 데이터셋** 확보를 통한 모델 성능 향상은 필수적이며, **다양한 저해상도 영상의 왜곡 유형**에 대한 더욱 강건한 모델 개발이 중요합니다.  **시간적 일관성을 더욱 향상**시키는 기술 개발과 **실시간 처리 성능** 개선을 위한 효율적인 알고리즘 연구 또한 중요한 과제입니다.  **다른 딥러닝 모델과의 융합**을 통한 시너지 효과 창출도 고려해 볼 만한 방향이며,  **다양한 응용 분야** (예: 의료 영상 처리, 자율 주행) 에서의 활용 가능성을 탐색하는 연구도 필요합니다.  **모델의 설명 가능성**을 높이는 연구를 통해 신뢰도를 높이고,  **에너지 효율적인 모델** 개발을 통해 환경적인 지속가능성을 고려하는 것 또한 중요한 미래 연구 과제입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.02976/x3.png)

> 🔼 STAR 모델의 개요를 보여주는 그림입니다. 저해상도 비디오(LR video XL)와 텍스트가 입력으로 들어가고, VAE(Variational Autoencoder) 인코더를 통해 잠재 벡터(ZH, ZL)를 생성합니다. 텍스트 인코더는 텍스트 임베딩(Ctext)을 생성하고, 이는 ControlNet과 함께 T2V(Text-to-Video) 모델의 입력으로 사용됩니다. LIEM(Local Information Enhancement Module)은 글로벌 공간/시간적 자기 주의(G-SA) 전에 추가되어 국지적 세부 정보를 강화하고 아티팩트를 줄입니다. T2V 모델은 노이즈가 있는 잠재 벡터(Zt), 텍스트 임베딩(Ctext), 그리고 ControlNet로부터의 제어 신호(Ci)를 사용하여 속도(vt)를 예측합니다. 최종적으로 VAE 디코더를 통해 고해상도 비디오(HR video XH)를 출력합니다. 손실 함수는 속도 예측 손실(Lv)과 동적 주파수 손실(LDF)로 구성되어 있으며, 동적 주파수 손실은 고해상도 비디오의 충실도를 높이도록 설계되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Overview of the proposed STAR.
> </details>



![](https://arxiv.org/html/2501.02976/x4.png)

> 🔼 그림 3은 STAR 모델의 LIEM(Local Information Enhancement Module) 모듈의 효과를 보여줍니다. 왼쪽은 전역 구조만 사용하는 경우와 지역 및 전역 구조를 결합하는 경우의 영향을 보여주는 개략도입니다. 오른쪽은 실제 및 합성 비디오에 대한 시각적 비교를 보여줍니다.  LIEM 모듈을 추가함으로써, 전역적 정보 처리만 하는 기존 모델보다 더욱 향상된 지역적 세부 정보와 더욱 자연스럽고 사실적인 결과를 얻을 수 있음을 보여줍니다.  확대하여 보시면 더욱 자세히 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Motivation of LIEM. Left: schematic diagram illustrating the impact of using only global structure versus a combination of local and global structures. Right: visual comparison on real-world and synthetic videos. (Zoom-in for best view)
> </details>



![](https://arxiv.org/html/2501.02976/x5.png)

> 🔼 그림 4는 제안된 동적 주파수 손실(DF Loss)의 동작 원리를 보여줍니다. 왼쪽 그래프는 저주파수 및 고주파수 성분의 PSNR 값을 확산 단계에 따라 나타낸 것입니다. 저주파수 성분의 PSNR은 초기 단계에서 빠르게 증가하지만, 고주파수 성분의 PSNR은 후반부에 증가하는 것을 확인할 수 있습니다. 이는 초기 단계에서는 저주파수 성분을 중심으로 영상의 구조가 복원되고, 후반 단계에서는 고주파수 성분을 중심으로 세부적인 디테일이 추가되는 것을 의미합니다. 오른쪽 이미지들은 서로 다른 확산 단계에서 저주파수 및 고주파수 성분의 시각적 결과를 보여줍니다. 이를 통해 초기 단계에서는 큰 구조가, 후기 단계에서는 세부적인 디테일이 복원되는 것을 직관적으로 이해할 수 있습니다.  전체적으로 그림 4는 제안된 DF Loss가 영상 복원의 각 단계에 적합한 주파수 성분에 집중하도록 모델을 유도하여 복원된 영상의 질을 향상시키는 데 기여하는 메커니즘을 명확하게 설명합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Motivation of DF Loss. Left: PSNR curves of low- and high-frequency components relative to ground truth across diffusion steps. The low-frequency PSNR increases during the early diffusion steps, while the high-frequency PSNR rises in the later diffusion steps. Right: visual results of low- and high-frequency components at different diffusion stage. (Zoom-in for best view)
> </details>



![](https://arxiv.org/html/2501.02976/x6.png)

> 🔼 그림 5는 동적 주파수 손실(Dynamic Frequency Loss)에 대한 설명입니다. 왼쪽 그림은 가중치 함수 c(t)의 곡선을 α 값이 다를 때 보여줍니다. α 값에 따라 가중치 함수의 형태가 달라지는 것을 보여주는 것으로, 이는 동적 주파수 손실의 핵심 메커니즘을 시각적으로 보여줍니다. 오른쪽 그림은 동적 주파수 손실의 세부적인 계산 과정을 보여줍니다.  이 그림은 논문의 동적 주파수 손실에 대한 설명을 보다 명확하게 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Dynamic Frequency Loss. Left: curves of weighting function c⁢(t)𝑐𝑡c(t)italic_c ( italic_t ) for different α𝛼\alphaitalic_α. Right: details of DF loss.
> </details>



![](https://arxiv.org/html/2501.02976/x7.png)

> 🔼 그림 6은 OpenVid30 및 REDS30 데이터셋의 합성 저해상도 비디오에 대한 정성적 비교 결과를 보여줍니다.  각각의 저해상도 비디오에 대해, RealBasicVSR, Upscale-A-Video, RealViformer 및 제안된 STAR 모델을 포함한 여러 최첨단 VSR 모델의 결과를 보여줍니다.  이 그림은 다양한 모델이 저해상도 비디오를 고해상도로 복원하는 능력을 시각적으로 비교하여 STAR 모델의 성능을 강조합니다.  자세한 내용은 확대하여 확인하십시오.
> <details>
> <summary>read the caption</summary>
> Figure 6: Qualitative comparisons on synthetic LR videos from OpenVid30 and REDS30[35]. (Zoom-in for best view)
> </details>



![](https://arxiv.org/html/2501.02976/x8.png)

> 🔼 이 그림은 논문의 실제 세상 비디오 슈퍼 해상도(VSR) 성능을 보여주는 VideoLQ 데이터셋의 실제 세계 저해상도 비디오에 대한 정성적 비교 결과를 보여줍니다. 여러 최첨단 VSR 모델(Real-ESRGAN, DBVSR, RealBasicVSR, Upscale-A-Video, RealViformer, StableSR)과 제안된 STAR 모델의 결과를 보여주며,  STAR 모델이 더 자연스러운 얼굴의 디테일과 더욱 명확한 텍스트 구조를 생성하여 더 나은 성능을 보임을 시각적으로 확인할 수 있습니다.  특히, 복잡한 저하가 포함된 실제 세상 시나리오에서 STAR 모델의 우수성을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Qualitative comparisons on real-world test videos in VideoLQ [11] dataset. (Zoom-in for best view)
> </details>



![](https://arxiv.org/html/2501.02976/x9.png)

> 🔼 그림 8은 REDS30 [35] 및 OpenVid 데이터셋에서 시간적 일관성에 대한 정성적 비교를 보여줍니다.  각 비교는 저해상도(LR) 입력 비디오, 몇몇 최첨단(SOTA) 비디오 초고해상도(VSR) 모델의 결과, 그리고 제안된 STAR 모델의 결과를 보여줍니다. 이를 통해, 제안된 방법이 시간적 일관성 측면에서 SOTA 모델들보다 얼마나 우수한지 시각적으로 확인할 수 있습니다.  특히, 동영상의 움직임이 자연스럽고 매끄러운지, 시간에 따른 물체의 변화가 일관되게 표현되는지에 주목하여 비교하면 좋습니다.  확대하여 보면 더욱 자세한 차이점을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Qualitative comparisons on temporal consistency in REDS30 [35] and OpenVid dataset. (Zoom-in for best view)
> </details>



![](https://arxiv.org/html/2501.02976/x10.png)

> 🔼 그림 9는 LIEM(Local Information Enhancement Module)의 적용 위치에 따른 성능 변화를 보여주는 실험 결과입니다. 왼쪽은 LIEM의 구조와 세 가지 다른 적용 위치(i), (ii), (iii)를 보여줍니다. 오른쪽은 각 위치에 LIEM을 적용했을 때 실제 및 합성 비디오 데이터셋에서의 시각적 비교 결과를 보여줍니다.  세 가지 위치에서의 성능을 비교 분석하여 최적의 LIEM 적용 위치를 제시합니다.  각 위치의 차이는 LIEM이 네트워크의 어느 부분에 연결되느냐에 따라 글로벌 특징과 로컬 특징의 균형이 달라지고, 이로 인해 최종 결과 영상의 세부 묘사와 전체적인 일관성이 영향을 받는다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Ablation study about LIEM. Left: illustration of different insertion positions of LIEM and the structure of LIEM. Right: visual comparison on real-world and synthetic videos with different LIEM positions.
> </details>



![](https://arxiv.org/html/2501.02976/extracted/6113603/figure_of_supp/bt_ablation.png)

> 🔼 이 그림은 실제 저화질 비디오에 더 큰 t2v 모델을 사용하여 확장하는 것을 보여줍니다.  비교를 위해 입력 비디오와 RealViformer, Upscale-A-Video 및 제안된 STAR(I2VGen-XL과 CogVideoX-5B 두 가지 버전) 모델의 출력 결과가 함께 표시됩니다.  더 큰 t2v 모델을 사용하면 더욱 향상된 디테일과 사실감 있는 복원 결과를 얻을 수 있음을 시각적으로 보여줍니다. 확대하여 보면 더욱 자세히 확인 가능합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Illustration on scaling up with larger t2v models on a real-world low-quality video. (Zoom-in for best view)
> </details>



![](https://arxiv.org/html/2501.02976/x11.png)

> 🔼 그림 11은 초매개변수 β(b(t)에서 β)에 대한 ablation study 결과를 보여줍니다.  β 값이 높을수록 충실도(fidelity)가 높아지고, β 값이 낮을수록 지각 품질(perceptual quality)이 강조됨을 보여줍니다.  즉, β 값을 조절하여 재구성된 비디오의 충실도와 지각 품질 간의 균형을 조절할 수 있음을 시각적으로 나타냅니다. 이는 제안된 Dynamic Frequency Loss의 효과를 보여주는 중요한 결과입니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Ablation on b⁢(t)𝑏𝑡b(t)italic_b ( italic_t ). Higher hyper-parameter β𝛽\betaitalic_β produces results with greater fidelity, while lower β𝛽\betaitalic_β emphasizes more perceptual quality.
> </details>



![](https://arxiv.org/html/2501.02976/x12.png)

> 🔼 본 그림은 사용자 연구 결과를 보여줍니다.  구체적으로, 실제 사용자들이 비디오의 화질과 시간적 일관성(temporal consistency) 측면에서 STAR 모델을 선호하는 비율을 나타냅니다. REDS30과 VideoLQ 데이터셋에서 수행된 사용자 평가 결과를 원형 그래프로 표현하여 STAR의 우수성을 시각적으로 보여줍니다.  각 그래프는 화질과 시간적 일관성에 대한 선호도를 비교 분석한 결과이며, STAR가 다른 최첨단 모델들에 비해 압도적으로 높은 선호도를 받았음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: User study results. Our STAR is preferred by human evaluators for both visual quality and temporal consistency.
> </details>



![](https://arxiv.org/html/2501.02976/x13.png)

> 🔼 그림 13은 합성 데이터셋을 사용한 정량적 비교 결과를 보여줍니다.  STAR 모델은 기존의 최첨단 VSR 모델들보다 더욱 세밀하고 사실적인 결과를 생성함을 보여줍니다.  기존 모델들은 이미지의 일부 디테일을 과도하게 평활화하거나(over-smoothing) 혹은 인공적인 아티팩트를 생성하는 반면, STAR는 더욱 자연스럽고 선명한 결과를 제공합니다. 특히 얼굴, 글자, 건물 등의 세부적인 요소들이 더욱 명확하게 복원되는 것을 확인할 수 있습니다.  줌 기능을 사용하여 세부적인 부분까지 비교 분석하는 것이 좋습니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: Qualitative comparisons on synthetic datasets. Our STAR generates more detailed and realistic results. (Zoom-in for best view)
> </details>



![](https://arxiv.org/html/2501.02976/x14.png)

> 🔼 그림 14는 실제 세계 데이터셋에서 다양한 최첨단 VSR 모델들과 제안된 STAR 모델의 성능을 비교한 정성적 결과를 보여줍니다.  STAR는 얼굴의 세부 묘사를 가장 선명하게 복원하고 텍스트 구조를 가장 정확하게 재구성합니다.  각 모델의 결과를 자세히 비교해 보면 STAR가 얼굴의 미세한 표정이나 텍스트의 작은 글자까지도 더욱 정확하게 복원하여 더욱 사실적이고 자연스러운 고해상도 비디오를 생성하는 것을 확인할 수 있습니다.  특히, 흐릿하거나 왜곡된 저해상도 영상에서도 STAR가 다른 모델들보다 훨씬 더 우수한 성능을 보임을 알 수 있습니다.  확대해서 보시면 더욱 명확하게 차이를 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: Qualitative comparisons on real-world datasets. Our STAR produces the clearest facial details and the most accurate text structure. (Zoom-in for best view)
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | Dataset | Size | #Frames | Resolution |
|---|---|---|---|---|
| UAV<sup>[75]</sup> | WebVid<sup>[2]</sup> + YouHQ<sup>[75]</sup> | 335K+37K | - | 336×596, 1080×1920 |
| RealViformer<sup>[73]</sup> | REDS<sup>[35]</sup> | 300K | 100 | 720×1280 |
| Ours | OpenVid<sup>[36]</sup> | 200K | 32 | 720×1280 |{{< /table-caption >}}
> 🔼 표 2는 논문에서 사용된 훈련 데이터셋을 비교 분석한 표입니다.  데이터셋의 크기(샘플 수, 프레임 수), 해상도 정보를 비교하여 각 모델의 훈련 데이터 특징을 보여줍니다.  STAR 모델은 OpenVid-1M과 REDS, OpenVid 데이터셋의 일부를 사용하여 훈련되었음을 보여주는 표입니다.  다른 모델들과 비교하여 STAR 모델의 훈련 데이터셋 규모와 특징을 파악하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Training dataset comparison.
> </details>

{{< table-caption >}}
| Position | Spa-Local | Temp-Local | PSNR ↑ | LPIPS ↓ | E*warp ↓ |
|---|---|---|---|---|---| 
| (i) |  |  | 23.14 | 0.2015 | 2.83 |
|  | ✓ |  | 23.61 | 0.2013 | 2.82 |
|  |  | ✓ | 23.65 | 0.1945 | 2.92 |
| ✓ | ✓ | 23.69 | 0.1943 | 2.74 |
| (ii) |  | 23.27 | 0.2363 | 3.57 |
| (iii) | 24.51 | 0.2094 | 1.99 |{{< /table-caption >}}
> 🔼 이 표는 논문의 3.2절 'Local Information Enhancement Module'에서 LIEM(Local Information Enhancement Module)의 위치를 바꿔가며 실험한 결과를 보여줍니다.  세 가지 다른 위치 (i), (ii), (iii)에 LIEM을 적용했을 때의 PSNR, LPIPS, Ewarp 값을 비교하여 LIEM의 최적 위치를 확인합니다.  각 위치는 네트워크 구조도와 함께 제시되어, LIEM이 어디에 위치하는지 명확하게 보여줍니다.  결과적으로, LIEM을 Global Spatial/Temporal Self-Attention 앞에 배치하는 것이 가장 좋은 성능을 보였음을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Ablation of LIEM position.
> </details>

{{< table-caption >}}
| Seperate | Type | PSNR↑ | LPIPS↓ | E*warp↓ | 
|---|---|---|---|---| 
| w/o Frequency Loss |  | 23.69 | 0.1943 | 2.74 | 
| - | - | 23.72 | 0.1941 | 2.71 | 
| ✓ | Inverse | 23.67 | 0.1945 | 2.83 | 
| ✓ | Direct | **23.85** | **0.1903** | **2.69** | {{< /table-caption >}}
> 🔼 표 4는 제안된 동적 주파수 손실(DF Loss)의 다양한 변형에 대한 실험 결과를 보여줍니다.  'Separate' 열은 저주파수와 고주파수 성분을 분리하여 각각 제약 조건을 적용했는지 여부를 나타내고, 'Type' 열은 저주파수와 고주파수에 대한 가중치를 부여하는 방식(Inverse, Direct)을 의미합니다.  PSNR, LPIPS, Ewarp 지표를 통해 각 변형의 성능을 비교 분석하여 최적의 DF Loss 구성을 도출하기 위한 실험 결과를 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Ablation of different variants of DF loss.
> </details>

{{< table-caption >}}
| b(t) | <math>α</math> | PSNR<math>↑</math> | LPIPS<math>↓</math> | <math>E_{warp}^{*}↓</math> |
|---|---|---|---|---|
| Linear | 0.25 | 23.76 | 0.2030 | 2.72 |
|  | 0.5 | 23.71 | 0.2010 | 2.75 |
|  | 1 | 23.85 | 0.1903 | 2.69 |
|  | 1.5 | 23.53 | 0.1928 | 2.81 |
| 2 | 23.91 | 0.1885 | 2.61 |
| Exponential | 2 | 23.68 | 0.1990 | 2.78 |{{< /table-caption >}}
> 🔼 표 5는 STAR 모델의 손실 함수에서 가중치 함수 b(t)와 c(t)에 대한 하이퍼파라미터 α와 β의 영향을 ablation study를 통해 분석한 결과를 보여줍니다.  b(t)는 시간에 따라 동적으로 변화하는 가중치를 조절하고, c(t)는 주파수 성분에 대한 가중치를 조절하는 역할을 합니다.  이 표는  다양한 α와 β 값을 사용하여 실험을 진행했을 때, PSNR, LPIPS, 그리고 Ewarp 지표가 어떻게 변하는지 보여줌으로써, 최적의 하이퍼파라미터 값을 찾는 과정을 제시합니다.  결과적으로 최적의 하이퍼파라미터 조합을 통해 공간-시간적 화질을 개선하는 데 도움이 되는지를 보여주는 표입니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Ablation of b⁢(t)𝑏𝑡b(t)italic_b ( italic_t ) and α𝛼\alphaitalic_α in c⁢(t)𝑐𝑡c(t)italic_c ( italic_t ).
> </details>

{{< table-caption >}}
| Metrics | UAV | RealViformer | Ours (I2VGen-XL) | Ours (CogX-2B) | Ours (CogX-5B) |
|---|---|---|---|---|---| 
| PSNR ↑ | 22.46 | 22.90 | 21.46 | 23.18 | **23.60** |
| SSIM ↑ | 0.6552 | 0.6944 | 0.6715 | **0.7112** | **0.7400** |
| LPIPS ↓ | 0.2035 | 0.1823 | 0.1779 | **0.1571** | **0.1314** |
| DOVER ↑ | 0.6609 | 0.4286 | **0.7267** | 0.6955 | **0.7350** |
| $E_{warp}^{*}↓$ | 5.424 | 4.75 | 5.529 | **3.68** | 4.56 |{{< /table-caption >}}
> 🔼 표 6은 실제 환경의 비디오 초고해상도화(VSR)에서 텍스트-비디오(T2V) 확산 사전의 효과를 보여줍니다.  다양한 성능 지표(PSNR, SSIM, LPIPS, DOVER, Ewarp)를 사용하여  I2VGen-XL 모델과 더 큰 CogVideoX 모델(CogVideoX-2B, CogVideoX-5B)을 사용한 STAR의 성능을 비교 분석합니다.  실제 세계 VSR에서 T2V 모델의 크기가 성능에 미치는 영향을 보여주는 결과를 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Effectiveness of T2V diffusion prior for real-world VSR.
> </details>

{{< table-caption >}}
| β | PSNR ↑ | LPIPS ↓ | E*warp ↓ |
|---|---|---|---|
| 0.25 | 23.55 | **0.1825** | 2.88 |
| 0.75 | 23.76 | 0.1842 | 2.74 |
| 1.0 | 23.91 | 0.1885 | 2.68 |
| 1.5 | 24.08 | 0.2272 | 2.53 |
| 2.0 | **24.41** | 0.3339 | **2.21** |{{< /table-caption >}}
> 🔼 표 7은 초매개변수 β(beta) 값을 다르게 했을 때의 정성적 비교 결과를 보여줍니다.  β 값은 손실 함수에서 시간에 따른 가중치를 조절하는 역할을 하며, β 값이 클수록 충실도(fidelity)가 높아지고, 작을수록 지각 품질(perceptual quality)이 높아집니다.  표에는 PSNR, LPIPS, Ewarp 세 가지 지표가 제시되어 각 β 값에 따른 영상의 품질 차이를 정량적으로 비교합니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Qualitative comparison under different β𝛽\betaitalic_β of b⁢(t)𝑏𝑡b(t)italic_b ( italic_t ).
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