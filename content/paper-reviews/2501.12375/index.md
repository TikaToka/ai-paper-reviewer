---
title: "Video Depth Anything: Consistent Depth Estimation for Super-Long Videos"
summary: "초장시간 비디오에 대한 일관된 깊이 추정을 위한 효율적이고 정확한 새로운 모델, Video Depth Anything을 소개합니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Video Understanding", "🏢 ByteDance",]
showSummary: true
date: 2025-01-21
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.12375 {{< /keyword >}}
{{< keyword icon="writer" >}} Sili Chen et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-22 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.12375" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.12375" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/video-depth-anything-consistent-depth" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 단일 이미지 깊이 추정 모델은 비디오에서 일관성 없는 깊이 예측으로 어려움을 겪었습니다. 이 문제를 해결하기 위해, 기존 모델을 개선하거나 추가적인 제약 조건을 도입하는 여러 시도가 있었지만, 계산 비용이 많이 들거나 짧은 비디오에만 적용 가능한 한계가 있었습니다.

본 논문에서는 Depth Anything V2 모델을 기반으로, 효율적인 공간-시간적 헤드를 새롭게 설계하고 시간적 일관성 손실을 도입하여 이 문제를 해결한 Video Depth Anything 모델을 제시합니다. 이 모델은 초장시간 비디오에서도 고품질의 일관된 깊이 예측을 제공하며, 계산 효율성도 뛰어납니다. 또한, 다양한 비디오 벤치마크에 대한 종합적인 평가를 통해 최첨단 성능을 달성함을 보여줍니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} Video Depth Anything 모델은 초장시간 비디오에 대해서도 정확하고 일관된 깊이 추정을 제공합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 제안된 모델은 기존의 방법들보다 계산 효율성이 뛰어나 실시간 응용이 가능합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 본 연구는 장시간 비디오 깊이 추정 분야에서 새로운 기술적 기준을 제시하며, 로보틱스, 증강 현실 등 다양한 분야에 응용될 수 있습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**본 논문은 초장시간 비디오에 대한 일관된 깊이 추정이라는 어려운 문제를 해결하여 연구자들에게 상당한 영향을 미칩니다.** 기존의 방법들은 짧은 비디오에만 적용 가능하거나 계산 비용이 많이 들었지만, 이 논문은 효율적이고 일반화된 모델을 제시하여 장시간 비디오에 대한 정확하고 일관된 깊이 추정을 가능하게 합니다. **이는 로보틱스, 증강 현실, 고급 비디오 편집과 같은 다양한 분야에 응용될 수 있으며, 향후 연구의 새로운 방향을 제시합니다.**

------
#### Visual Insights



![](https://arxiv.org/html/2501.12375/x2.png)

> 🔼 그림 1은 논문의 주요 결과를 보여줍니다. 왼쪽은 모델이 풍부한 동작을 포함하는 긴 비디오에 대해 일관된 깊이 예측을 생성할 수 있음을 보여주는 196초(4690 프레임)짜리 페어 스케이팅 영상의 예시입니다.  이 영상은 [14]에서 가져왔습니다. 오른쪽 그래프는 정확도(δ1), 일관성, Nvidia A100 GPU 상에서의 지연 시간 측면에서 제안된 모델과 기존 모델들의 비교 결과를 나타냅니다. 원의 크기는 지연 시간을 나타냅니다. 일관성은 모든 모델의 최대 시간 정렬 오류(TAE)에서 각 모델의 TAE를 뺀 값으로 정의됩니다. 제안된 모델은 모든 측면에서 최고의 성능을 달성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Left: Our model can generate consistent depth predictions for long videos with rich actions. The demo video shows a 196-second (4690 frames) long take of pair skating, as sourced from [14]. Right: Comparison to baselines in terms of accuracy (δ1subscript𝛿1\delta_{1}italic_δ start_POSTSUBSCRIPT 1 end_POSTSUBSCRIPT), consistency, and latency on the Nvidia A100 GPU (denoted with circle size). Consistency is defined as the maximum Temporal Alignment Error (TAE) among all models minus the TAE of each individual model. Our model achieves the best performance in all aspects.
> </details>





{{< table-caption >}}
| Method / Metrics | KITTI [11] |  | Scannet [7] |  | Bonn [24] |  | NYUv2 [22] |  | Sintel [5] (~50 frames) |  | Scannet (170 frames [40]) | δ₁ Rank | 
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| DAv2-L [42] | 0.137 | 0.815 | 0.150 | 0.768 | 0.127 | 0.864 | 0.094 | 0.928 | 0.390 | 0.541 | 1.140 | 3.6 |
| NVDS [38] | 0.233 | 0.614 | 0.207 | 0.628 | 0.199 | 0.674 | 0.217 | 0.598 | 0.408 | 0.464 | 2.176 | 6.8 |
| NVDS [38] + DAv2-L [42] | 0.227 | 0.617 | 0.194 | 0.658 | 0.191 | 0.700 | 0.184 | 0.679 | 0.449 | 0.503 | 2.536 | 5.8 |
| ChoronDepth [32] | 0.243 | 0.576 | 0.199 | 0.665 | 0.199 | 0.665 | 0.173 | 0.771 | 0.192 | 0.673 | 1.022 | 5.2 |
| DepthCrafter [13] | 0.164 | 0.753 | 0.169 | 0.730 | 0.153 | 0.803 | 0.141 | 0.822 | 0.299 | 0.695 | 0.639 | 3.4 |
| DepthAnyVideo [40] | - | - | - | - | - | - | - | - | 0.405 | 0.659 | 0.967 | - |
| VDA-S (Ours) | 0.086 | 0.942 | 0.110 | 0.876 | 0.083 | 0.950 | 0.077 | 0.959 | 0.339 | 0.584 | 0.703 | 2.6 |
| VDA-L (Ours) | 0.083 | 0.944 | 0.089 | 0.926 | 0.071 | 0.959 | 0.062 | 0.971 | 0.295 | 0.644 | 0.570 | 1.6 |{{< /table-caption >}}

> 🔼 표 1은 제로샷 비디오 깊이 추정 결과를 보여줍니다. 본 연구의 모델(VDA-S, VDA-L)은 비디오 깊이 추정 모델 [38, 32, 13, 40] 및 단일 이미지 깊이 추정 모델 [42]과 비교됩니다. VDA-S는 ViT-Small 백본을 사용한 모델이고, VDA-L은 ViT-Large 백본을 사용한 모델입니다.  표에는 정확도(AbsRel, δ1) 및 일관성(TAE) 지표를 사용하여 여러 비디오 데이터셋(KITTI, Scannet, Bonn, NYUv2, Sintel)에 대한 성능이 제시되어 있으며, 가장 좋은 결과와 두 번째로 좋은 결과는 강조 표시되어 있습니다.  이 표는 다양한 모델의 제로샷 비디오 깊이 추정 능력을 비교 분석하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Zero-shot video depth estimation results. We compare with representative single-image [42] and video depth estimation models [38, 32, 13, 40]. “VDA-S” denotes our model with ViT-Small backbone. “VDA-L” denotes our model with ViT-Large backbone. The best and the second best results are highlighted.
> </details>





### In-depth insights


#### Long Video Depth
본 논문은 초장시간 비디오에 대한 일관된 깊이 추정이라는 어려운 문제를 해결하기 위해 고안되었습니다. **기존의 방법들은 짧은 비디오에 대해서는 좋은 성능을 보였지만, 긴 비디오에 적용하면 일관성이 부족하고 계산 비용이 많이 드는 문제점**이 있었습니다.  연구진은 이러한 한계를 극복하고자 **Depth Anything V2를 기반으로 효율적인 공간-시간 헤드를 새롭게 설계**했습니다. 이를 통해 시간적 일관성 손실을 줄이고 연산 효율성을 높였습니다. 또한, **새로운 키프레임 기반 전략**을 통해 초장시간 비디오 추론을 효과적으로 수행할 수 있도록 하였습니다.  실험 결과, 제안된 모델은 여러 비디오 벤치마크에서 최첨단 성능을 달성하였으며, **일관성과 정확성을 유지하면서 처리 속도 또한 빨라**졌습니다. **특히, 실시간 처리가 가능한 작은 모델**까지 제공하여 다양한 상황에 적용 가능성을 높였습니다. 이 연구는 초장시간 비디오 깊이 추정 분야에 중요한 기여를 하였으며, 향후 로보틱스, 증강 현실, 고급 비디오 편집 등 다양한 분야에 응용될 수 있을 것으로 기대됩니다.

#### Temporal Consistency
본 논문에서 시간적 일관성(Temporal Consistency)은 비디오의 연속된 프레임에서 깊이 추정의 정확성과 일관성을 유지하는 핵심 개념입니다. 기존의 단일 이미지 깊이 추정 모델은 비디오에 적용 시 시간적 흔들림(flickering) 및 모션 블러가 발생하여, 로보틱스, 증강현실 등의 실시간 응용 분야에 적용이 어려웠습니다. **이 논문은 이러한 문제를 해결하기 위해, 시간적 깊이 기울기 매칭 손실(Temporal Gradient Matching Loss)**을 제안하여, 시간에 따른 깊이 변화의 기울기를 제약함으로써 일관성을 확보합니다. 기존의 광학 흐름(optical flow) 기반 방법들과 달리, **추가적인 기하학적 사전 정보나 비디오 생성 모델 없이 효율적으로 시간적 일관성을 달성**하는 것이 특징입니다.  **핵심 프레임 기반 전략**을 통해 초장시간 비디오 처리에도 효율적이며, 실험 결과를 통해 시간적 일관성 및 정확성에서 최첨단 성능을 달성함을 보여줍니다.  즉, **시간적 일관성 문제에 대한 효과적이고 효율적인 해결책**을 제시함으로써,  실제 응용 분야에서의 활용 가능성을 크게 높였습니다.

#### STH & TGM Loss
본 논문에서 제시된 STH(Spatio-Temporal Head)와 TGM(Temporal Gradient Matching) Loss는 장시간 비디오에 대한 일관된 깊이 추정이라는 어려운 문제에 대한 효과적인 해결책을 제시합니다. **STH는 기존 Depth Anything V2의 DPT 헤드를 대체하여 공간적 정보와 시간적 정보 간의 상호 작용을 가능하게 합니다.**  시간적 어텐션 레이어를 통해 연속된 프레임 간의 관계를 학습하며, 이는 움직임으로 인한 흔들림이나 모션 블러를 감소시키는데 중요합니다.  **TGM Loss는 기존의 광학 흐름에 의존하는 방법과 달리, 시간에 따른 깊이 변화의 그래디언트를 제약하여 일관성을 유지합니다.** 이는 광학 흐름 추정의 오류에 영향을 받지 않고, 계산 효율성을 높이는 장점을 가집니다.  **STH와 TGM Loss의 조합은 정확도와 일관성 모두에서 우수한 성능을 보이며, 특히 장시간 비디오에서 기존 방법들의 한계를 극복합니다.**  결론적으로, 이 두 요소는 **장시간 비디오에 대한 깊이 추정의 새로운 표준을 제시**하는 핵심적인 부분입니다.

#### Inference Strategy
본 논문에서 제시된 추론 전략은 **초장시간 비디오에 대한 깊이 추정**이라는 어려운 과제를 해결하기 위한 핵심적인 부분입니다. 단순히 긴 비디오를 작은 조각으로 나누어 처리하는 대신, **중첩된 프레임과 키프레임 기반의 전략**을 통해 매끄러운 깊이 예측을 가능하게 합니다. 이는 각 세그먼트의 처리 결과를 이전 세그먼트의 정보와 효과적으로 연결하여 누적 오차를 최소화하고, 전체 비디오에 걸쳐 일관성 있는 깊이 정보를 유지하는 데 중요합니다. 특히, **키프레임 참조 기법**은 이전에 예측된 깊이 정보의 스케일과 시프트 정보를 활용하여, 현재 세그먼트의 깊이 추정에 대한 기준을 제공함으로써, 장시간 비디오 처리 시 발생할 수 있는 누적 오차를 효과적으로 방지하는 역할을 수행합니다. 이러한 전략은 단순히 연산 효율성을 높이는 것뿐만 아니라, **깊이 예측의 정확도와 일관성을 동시에 향상**시키는 데 기여합니다.  결과적으로, 제안된 추론 전략은 초장시간 비디오에 대한 효율적이고 정확한 깊이 추정을 위한 실용적인 해결책을 제공하며, 이는 컴퓨터 비전 분야에서 중요한 발전으로 평가될 수 있습니다.

#### Future Directions
본 논문에서 제시된 Video Depth Anything 모델은 초장시간 비디오에 대한 일관된 깊이 추정이라는 중요한 문제에 대한 획기적인 해결책을 제시하지만, 여전히 개선의 여지가 있습니다. **향후 연구 방향은 더욱 방대한 양의 고품질 비디오 데이터를 활용하여 모델의 정확도와 일반화 능력을 향상시키는 데 집중**되어야 합니다. 또한, **실시간 처리 성능을 개선하기 위한 모델 경량화 및 효율적인 추론 전략 연구**가 필요합니다.  특히, **모델의 계산 복잡도를 줄이면서 정확도를 유지하는 기술 개발**은 모바일 및 임베디드 시스템과 같은 제약된 환경에서의 적용 가능성을 높일 것입니다.  **다양한 환경 및 조명 조건에서의 성능 향상**을 위해, 다양한 데이터 증강 기법과 강건한 학습 전략을 도입하는 것 또한 중요한 연구 과제입니다.  **깊이 추정의 정확도를 높이는 것은 물론, 깊이 정보의 시맨틱 이해를 향상**시키기 위한 연구가 필요합니다.  **깊이 정보와 다른 시각적 정보(예: 광학 흐름, 카메라 자세)를 통합**하여 더욱 정확하고 풍부한 정보를 제공하는 시스템을 구축하는 연구도 중요한 과제입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.12375/x3.png)

> 🔼 그림 2는 제안된 모델의 전체 파이프라인과 공간-시간적 헤드를 보여줍니다. 왼쪽은 Depth Anything V2의 백본 인코더와 새롭게 제안된 공간-시간적 헤드로 구성된 모델의 전체 구조를 보여줍니다. 모델은 지상 진실 심도 레이블을 사용하여 비디오 데이터를 공동으로 학습하고, 교사 모델에 의해 생성된 의사 레이블을 사용하여 비표지 이미지를 학습합니다. 학습 중에는 헤드만 학습됩니다. 오른쪽은 원래 DPT 헤드 [28]의 구조를 유지하면서 공간-시간적 헤드가 여러 시간적 레이어를 DPT 헤드에 삽입하는 방식을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Overall pipeline and the spatio-temporal head. Left: Our model is composed of a backbone encoder from Depth Anything V2 and a newly proposed spatio-temporal head. We jointly train our model on video data using ground-truth depth labels for supervision and on unlabeled images with pseudo labels generated by a teacher model. During training, only the head is learned. Right: Our spatiotemporal head inserts several temporal layers into the DPT head, while preserving the original structure of DPT head [28].
> </details>



![](https://arxiv.org/html/2501.12375/extracted/6147235/figures/imgs/performance_comparison.png)

> 🔼 그림 3은 초장시간 비디오에 대한 추론 전략을 보여줍니다. 모델이 처리하는 비디오 클립의 길이를 N으로 표시합니다. 각 추론 비디오 클립은 N-To-Tk개의 미래 프레임, To개의 겹치는/인접한 프레임, Tk개의 키 프레임으로 구성됩니다. 키 프레임은 이전 프레임에서 Δk 간격으로 역순으로 선택됩니다. 그런 다음 새로운 깊이 예측은 Tk개의 겹치는 프레임을 기반으로 이전 프레임에 스케일-쉬프트 방식으로 정렬됩니다. 그림에서는 N=32, To=8, Tk=2, Δk=12를 사용합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Inference strategy for long videos. N𝑁Nitalic_N is the video clip lenght consumed by our model. Each inference video clip is built by N−To−Tk𝑁subscript𝑇𝑜subscript𝑇𝑘N-T_{o}-T_{k}italic_N - italic_T start_POSTSUBSCRIPT italic_o end_POSTSUBSCRIPT - italic_T start_POSTSUBSCRIPT italic_k end_POSTSUBSCRIPT future frames, Tosubscript𝑇𝑜T_{o}italic_T start_POSTSUBSCRIPT italic_o end_POSTSUBSCRIPT overlapping/adjacent frames, and Tksubscript𝑇𝑘T_{k}italic_T start_POSTSUBSCRIPT italic_k end_POSTSUBSCRIPT key frames. The key frames are selected by taking every ΔksubscriptΔ𝑘\Delta_{k}roman_Δ start_POSTSUBSCRIPT italic_k end_POSTSUBSCRIPT-th frame going backward. Then, the new depth predictions will be scale-shift-aligned to the previous frames based on the Tksubscript𝑇𝑘T_{k}italic_T start_POSTSUBSCRIPT italic_k end_POSTSUBSCRIPT overlapping frames. We use N=32,To=8,Tk=2,Δk=12formulae-sequence𝑁32formulae-sequencesubscript𝑇𝑜8formulae-sequencesubscript𝑇𝑘2subscriptΔ𝑘12N=32,T_{o}=8,T_{k}=2,\Delta_{k}=12italic_N = 32 , italic_T start_POSTSUBSCRIPT italic_o end_POSTSUBSCRIPT = 8 , italic_T start_POSTSUBSCRIPT italic_k end_POSTSUBSCRIPT = 2 , roman_Δ start_POSTSUBSCRIPT italic_k end_POSTSUBSCRIPT = 12.
> </details>



![](https://arxiv.org/html/2501.12375/x4.png)

> 🔼 그림 4는 다양한 프레임 길이에 따른 비디오 깊이 추정 정확도를 보여줍니다.  Bonn [24], Scannet [7], NYUv2 [22] 데이터셋에서 110에서 500프레임까지, 제안된 모델(VDA-L)을 DepthCrafter [13]와 DepthAnyVideo [40]와 비교 분석했습니다.  이를 통해 프레임 길이 변화에 따른 각 모델의 성능 변화와 상대적 성능 차이를 정량적으로 비교하고, 제안 모델의 효율성과 정확성을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Video depth estimation accuracy for different frame length. We compare our model (VDA-L) with DepthCrafter [13] and DepthAnyVideo [40] from 110 to 500 frames on Bonn [24], Scannet [7], and NYUv2 [22].
> </details>



![](https://arxiv.org/html/2501.12375/x5.png)

> 🔼 그림 5는 실제 환경의 긴 비디오에 대한 깊이 추정 결과를 정성적으로 비교한 것입니다.  본 논문의 모델과 DAv2-L [42], DepthCrafter [13] 세 가지 모델의 결과를 Scannet [7]과 Bonn [24] 데이터셋의 500프레임 비디오를 사용하여 비교 분석했습니다.  각 모델의 깊이 추정 결과를 시각적으로 보여주어 성능 차이를 명확하게 드러냅니다.  특히, 본 논문의 모델이 다른 모델들에 비해 더욱 일관되고 정확한 깊이 정보를 제공하는 모습을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Qualitative comparison for real-world long video depth estimation. We compare our model with DAv2-L [42] and DepthCrafter [13] on 500-frame videos from Scannet [7] and Bonn [24].
> </details>



![](https://arxiv.org/html/2501.12375/x6.png)

> 🔼 그림 6은 다양한 환경에서 촬영된 짧은 비디오에 대한 심도 추정 결과를 정성적으로 비교한 것입니다. Depth-Anything-V2, DepthCrafter, DepthAnyVideo 세 가지 방법과 제안된 방법의 결과를 DAVIS 데이터셋의 100프레임 미만 비디오를 사용하여 비교하였습니다. 빨간색 박스는 잘못된 심도 추정을, 파란색 박스는 일관성 없는 심도 추정을 나타냅니다. 제안된 방법은 기존 방법들보다 더 정확하고 일관된 심도 추정 결과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Qualitative comparison for in-the-wild short video depth estimation. We compare with Depth-Anything-V2 [42], DepthCrafter [13] and DepthAnyVideo [40] on videos with less than 100 frames from DAVIS [26]. Red boxes show incorrect depth estimation while blue boxes show inconsistent depth estimation.
> </details>



![](https://arxiv.org/html/2501.12375/x7.png)

> 🔼 그림 7은 서로 다른 추론 전략의 정성적 비교를 보여줍니다. 7320프레임의 자체 촬영 비디오에서 제안된 중첩 보간 및 키프레임 참조(OI+KR) 방법과 중첩 정렬(OA) 방법을 비교합니다. OA는 이전에 예측된 깊이 정보를 사용하여 현재 세그먼트의 깊이를 보정하는 반면, OI+KR은 이전 세그먼트의 키프레임을 사용하여 부드러운 전환을 보장합니다. 이 그림은 OI+KR이 장시간 비디오에서 더욱 일관되고 부드러운 깊이 예측을 제공함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Qualitative comparisons of different inference strategies. We compare overlap alignment (OA) with our proposed overlap interpolation and key-frame referencing (OI + KR) on a self-captured video with 7320 frames.
> </details>



![](https://arxiv.org/html/2501.12375/x8.png)

> 🔼 그림 8은 정지 영상의 깊이 추정에 대한 정성적 비교를 보여줍니다.  본 논문의 모델을 Depth-Anything-V2 [42], DepthCrafter [13], Depth Any Video [40]와 비교하여 정지 영상에 대한 깊이 추정 결과를 시각화했습니다.  비교 결과, 본 논문의 모델은 Depth-Anything-V2 [42]와 비슷한 수준의 시각적 결과를 보여주는 것을 확인할 수 있습니다. 다양한 유형의 이미지들에 대한 깊이 추정 성능을 보여주는 여러 예시들이 포함되어 있습니다. 각 모델의 강점과 약점을 비교하여, 본 논문의 모델의 성능을 보다 명확하게 이해할 수 있도록 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Qualitative comparison for static image depth estimation. We compare our model with Depth-Anything-V2 [42], DepthCrafter [13], and Depth Any Video [40] on static image depth estimation. Our model demonstrates visualization results comparable to those of Depth-Anything-V2 [42].
> </details>



![](https://arxiv.org/html/2501.12375/x9.png)

> 🔼 그림 9는 실제 환경의 긴 비디오에 대한 깊이 추정 결과를 정성적으로 비교한 것입니다. Depth-Anything-V2 [42]와 DepthCrafter [13]의 결과와 본 논문에서 제안하는 모델의 결과를 Scannet [7] 및 Bonn [24] 데이터셋의 500프레임 비디오를 사용하여 비교합니다. 비디오의 수직 빨간색 선을 따라 시간에 따른 색상과 깊이의 변화를 보여줍니다. 흰색 상자는 일관성 없는 추정 결과를, 파란색 상자는 제안된 알고리즘의 정확도가 더 높은 부분을 나타냅니다.  본 논문의 모델이 다른 모델들보다 시간적 일관성이 더 높고 정확도가 더 높다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Qualitative comparison for real-world long video depth estimation. We compare with Depth-Anything-V2 [42] and DepthCrafter [13] on 500-frames videos from Scannet [7] and Bonn [24] . We show changes in color and depth over time at the vertical red line in videos. White boxes show inconsistent estimation. Blue boxes show our algorithm has higher accuracy.
> </details>



![](https://arxiv.org/html/2501.12375/x10.png)

> 🔼 그림 10은 Video Depth Anything 모델의 공간-시간적 헤드(STH) 내부 구조를 보여줍니다. 특히, 시간적 어텐션 메커니즘을 적용하기 위해 특징 맵의 형태를 조정하는 과정을 상세히 나타냅니다. 입력 특징 맵은 시간적 어텐션 계산을 위해 (B x Hf x Wf) x N x C 형태로 변환되고, 각 시간적 어텐션 레이어를 거친 후에는 (B x N) x C x Hf x Wf 형태로 다시 변환됩니다. 여기서 B는 배치 크기, N은 프레임 수, Hf와 Wf는 특징 맵의 높이와 너비, C는 채널 수를 나타냅니다. 이러한 과정을 통해 모델은 비디오 프레임 간의 시간적 관계를 효과적으로 학습하고, 일관성 있는 깊이 예측을 수행할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Temporal layer. The feature shape is adjusted for temporal attention.
> </details>



![](https://arxiv.org/html/2501.12375/x11.png)

> 🔼 이 그림은 논문의 3D 비디오 변환 섹션에 포함되어 있으며, DAVIS 데이터셋 [26]의 비디오를 모델을 사용하여 3D 비디오로 변환한 결과를 보여줍니다.  간단히 말해, 2차원 비디오를 입력받아 깊이 정보를 추정하여 3차원 비디오로 변환하는 모델의 성능을 시각적으로 보여주는 예시입니다.  이를 통해 모델이 2D 비디오에 깊이 정보를 효과적으로 추가하여 3D 효과를 생성할 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: 3D Video Conversion. A video from the DAVIS dataset [26] is transformed into a 3D video using our model.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method / Metrics | KITTI AbsRel (↓) | KITTI  δ₁ (↑) | Sintel AbsRel (↓) | Sintel  δ₁ (↑) | NYUv2 AbsRel (↓) | NYUv2  δ₁ (↑) | ETH3D AbsRel (↓) | ETH3D  δ₁ (↑) | DIODE AbsRel (↓) | DIODE  δ₁ (↑) | δ₁ Rank | 
|---|---|---|---|---|---|---|---|---|---|---|---| 
| DepthCrafter [13] | 0.107 | 0.891 | 0.568 | 0.652 | 0.082 | 0.936 | 0.179 | 0.793 | 0.141 | 0.857 | 4 | 
| DepthAnyVideo [40] | **0.073** | **0.946** | 0.687 | 0.692 | 0.058 | 0.963 | **0.123** | **0.881** | 0.072 | 0.942 | 2.4 | 
| DAv2-L [42] | **0.074** | **0.946** | **0.487** | **0.752** | **0.045** | **0.979** | **0.131** | **0.865** | **0.066** | **0.952** | 1.4 | 
| VDA-L (Ours) | 0.075 | **0.946** | **0.496** | **0.754** | **0.046** | **0.978** | 0.132 | 0.863 | **0.067** | **0.950** | 2 |{{< /table-caption >}}
> 🔼 표 2는 제로샷 단일 이미지 깊이 추정 결과를 보여줍니다. 본 연구의 모델(VDA-L, ViT-Large 백본 사용)을 단일 프레임 입력으로 단일 이미지 [42] 및 비디오 깊이 추정 모델 [13, 40]과 비교 분석했습니다. 가장 우수한 결과와 두 번째로 우수한 결과는 강조 표시되어 있습니다.  본 표는 다양한 데이터셋에서 모델의 공간적 정확도를 평가하고, 다른 최첨단 모델과의 성능을 비교 분석하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Zero-shot single-image depth estimation results. We compare with representative single-image [42] and video depth estimation models [13, 40] with single-frame inputs. “VDA-L” denotes our model with ViT-Large backbone. The best and the second best results are highlighted.
> </details>

{{< table-caption >}}
| Method | Precision | Latency (ms) |
|---|---|---|
| ChronoDepth | FP16 | 506 |
| DepthCrafter | FP16 | 910 |
| DepthAnyVideo | FP16 | 159 |
| NVDS | FP32 | 204 |
| DAv2-L | FP32 | 60 |
| VDA-L (Ours) | FP32 | 67 |
| VDA-S (Ours) | FP32 | 9.1 |{{< /table-caption >}}
> 🔼 표 3은 비디오 깊이 추정을 위한 각 프레임의 추론 지연 시간을 보여줍니다.  Nvidia A100 GPU에서 518x518 해상도로 측정한 결과이며, 각 모델의 평균 실행 시간을 나타냅니다.  ChronoDepth, DepthCrafter, DepthAny Video, NVDS, Depth Anything V2, 그리고 제안된 Video Depth Anything (VDA-L 및 VDA-S) 모델의 추론 속도를 비교하여 제안된 모델의 효율성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Inference latency comparisons for video depth estimation. We measure average runtime for each frame on a single A100 GPU with a resolution of 518×518518518518\times 518518 × 518.
> </details>

{{< table-caption >}}
| Loss | AbsRel (↓) | 
δ<sub>1</sub> (↑) | TAE (↓) |
|---|---|---|---|
| VideoAlign | **0.151** | **0.846** | 1.326 |
| VideoAlign+SSI | **0.151** | **0.848** | 1.207 |
| OPW [38]+SSI | 0.182 | 0.771 | 0.918 |
| SE+SSI | 0.160 | 0.836 | **0.753** |
| TGM+SSI (Ours) | 0.166 | 0.832 | **0.767** |{{< /table-caption >}}
> 🔼 표 4는 제안된 시간적 기울기 일치 손실(TGM)을 포함한 다양한 손실 함수의 효과를 비교 분석한 결과를 보여줍니다.  비교 대상 손실 함수는 전체 비디오에 공유된 스케일-쉬프트 정렬을 사용하는 공간 손실인 'VideoAlign', 논문 [42]에서 사용된 이미지 수준 공간 손실인 'SSI', 논문 [38]에서 설명된 광학 흐름 기반 왜곡 손실인 'OPW', 그리고 방정식 2에서 제시된 안정적인 오류(SE)입니다. 결과적으로 제안된 TGM 손실 함수가 다른 손실 함수들에 비해 시간적 일관성과 기하학적 정확도 측면에서 우수한 성능을 보임을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Ablation studies on the effectiveness of the temporal losses. “VideoAlign” denotes the spatial loss with a shared scale-shift alignment applied to the entire video. “SSI” is the image-level spatial loss used in [42]. “OPW” refers to the optical flow-based warping loss described in [38]. “SE” refers to the stable error as introduced in Equation 2. “TGM” represents our proposed temporal gradient matching loss.
> </details>

{{< table-caption >}}
| Strategy | Window | AbsRel (↓) | δ₁ (↑) | TAE (↓) |
|---|---|---|---|---|
| Baseline | 16 | 0.157 | 0.826 | 0.874 |
| OA | 16 | 0.146 | 0.845 | 0.792 |
| OI | 16 | 0.157 | 0.826 | 0.783 |
| OI+KR(Ours) | 16 | 0.145 | 0.849 | 0.761 |
| OI+KR(Ours) | 32 | 0.144 | 0.851 | 0.718 |
| OI+KR(Ours) | 48 | 0.143 | 0.852 | 0.732 |{{< /table-caption >}}
> 🔼 표 5는 서로 다른 추론 전략과 창 크기의 효과에 대한 추가 분석 결과를 보여줍니다.  '기준선(Baseline)'은 겹치는 부분 없이 비디오 클립을 직접 추론하는 방법을 의미합니다.  'OA(Overlap Alignment)'는 4프레임 겹침을 사용하고 창 간에 크기-이동 정렬을 수행하는 추론 방식을 의미합니다.  'OI(Overlap Interpolation)'는 4프레임 겹침을 사용하여 깊이 클립을 연결하는 추론 방식입니다.  'OI+KR(OI with Key-Frame Referencing)'은 제안된 키프레임 참조를 OI에 추가적으로 적용한 방법입니다. 키프레임 참조는 이전 창의 키프레임들을 현재 창의 추론에 추가적인 참조로 사용하는 기법입니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Ablation studies on the effectiveness of different inference strategies and window sizes. “Baseline” denotes directly inference for video clips without overlapping. “OA” denotes inference with a overlap of 4 frames and perform scale-shift alignment across windows. “OI” denotes depth clip stitching with a overlap of 4 frames. “OI+KR” combines the “OI” with our proposed key-frame referencing with extra 2 key-frames.
> </details>

{{< table-caption >}}
| Datasets | Image-datasets |  | Video-datasets |  |  |
|---|---|---|---|---|---|---|
|  | AbsRel (↓) | δ₁ (↑) | AbsRel (↓) | δ₁ (↑) | TAE (↓) |
|---|---|---|---|---|---|---|
| Video | 0.180 | 0.876 | 0.145 | 0.849 | 0.761 |
| Video + Image | **0.167** | **0.883** | **0.142** | **0.852** | **0.742** |{{< /table-caption >}}
> 🔼 표 6은 이미지 데이터 증류의 효과에 대한 추가 실험 결과를 보여줍니다. '비디오'는 비디오 데이터셋만을 사용하여 학습한 모델의 결과이고, '비디오 + 이미지'는 이미지 레벨 증류 기법 [42]을 사용하여 비디오와 이미지 데이터셋을 결합하여 학습한 모델의 결과입니다.  즉, 비디오 데이터만으로 학습한 모델과 비디오 및 이미지 데이터를 함께 사용하여 학습한 모델의 성능을 비교 분석하여 이미지 데이터 증류의 효과를 확인하는 실험입니다. 이를 통해 추가적인 이미지 데이터를 활용함으로써 모델 성능 향상에 미치는 영향을 정량적으로 평가합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Ablation studies on the effectiveness of the image dataset distillation. “Video” denotes training using only video datasets. “Video + Image” merges video and image datasets for training using image-level distillation [42].
> </details>

{{< table-caption >}}
| Method / Metrics | Params(M) | # Video Training Data(M) | KITTI(110) [11] |  | Bonn(110) [24] |  | Scannet(90) [7] |  |
|---|---|---|---|---|---|---|---|---|
| AbsRel (↓) | δ₁ (↑) | AbsRel (↓) | δ₁ (↑) | AbsRel (↓) | δ₁ (↑) |
| DepthCrafter | 2156.7 | 10.5~40.5 | 0.111 | 0.885 | 0.066 | 0.979 | 0.125 | 0.848 |
| DepthAnyVideo | 1422.8 | 6 | **0.073** | **0.957** | **0.051** | **0.981** | 0.112 | 0.883 |
| VDA-L (Ours) | 381.8 | 0.55 | **0.079** | **0.950** | **0.053** | 0.972 | **0.075** | **0.954** |{{< /table-caption >}}
> 🔼 표 7은 제로샷 단일 이미지 깊이 추정 결과를 보여줍니다. 이 표는 제안된 모델(VDA-L, ViT-Large 백본 사용)의 성능을 DepthCrafter [13] 및 DepthAnyVideo [40]와 비교하여 보여줍니다.  비교는 짧은 비디오 깊이 벤치마크 데이터셋에서 수행되었으며, 기본 추론 해상도는 짧은 쪽이 518픽셀로 유지되도록 종횡비를 유지했습니다. 최고 및 차고 성능 결과가 강조 표시되어 있습니다.  즉,  짧은 비디오에 대한 제로샷 깊이 추정 성능을 기존 방법들과 비교 분석한 표입니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Zero-shot short video depth estimation results. We compare with DepthCrafter [13] and DepthAnyVideo [40] in short video depth benchmark. “VDA-L” denotes our model with ViT-Large backbone. The default inference resolution of our model is set to 518 pixels on the short side, maintaining the aspect ratio. The best and the second best results are highlighted.
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