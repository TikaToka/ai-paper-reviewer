---
title: "Pippo: High-Resolution Multi-View Humans from a Single Image"
summary: "단일 이미지에서 1K 해상도의 다중 뷰 인간 비디오를 생성하는 Pippo 모델 발표!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Generation", "🏢 Meta Reality Labs",]
showSummary: true
date: 2025-02-11
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.07785 {{< /keyword >}}
{{< keyword icon="writer" >}} Yash Kant et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-12 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.07785" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.07785" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/pippo-high-resolution-multi-view-humans-from" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

고품질의 다중 시점 인간 모델 생성은 엔터테인먼트, 헬스케어 등 다양한 분야에서 중요하지만, 고품질의 다중 시점 데이터 확보의 어려움이 큰 과제였습니다. 기존 연구들은 정확한 카메라 매개변수나 사전 학습된 모델을 필요로 하거나, 3D 일관성이 부족한 한계를 가지고 있었습니다.

본 연구는 이러한 문제를 해결하기 위해, 단일 이미지로부터 고해상도(1K) 다중 뷰 인간 영상을 생성하는 새로운 모델인 Pippo를 제시합니다.  Pippo는 **단일 이미지만을 입력**으로 받아들여, **추가적인 정보 없이도** 여러 각도에서의 인간 이미지를 생성합니다. 또한,  **개선된 3D 일관성 평가 지표**를 도입하여, 기존 모델들보다 더욱 정확하고 일관성 있는 결과를 보여주었습니다.  본 연구는 **다중 시점 이미지 생성의 새로운 표준**을 제시함으로써 관련 분야 연구에 크게 기여할 것으로 기대됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 단일 이미지만으로 고해상도(1K) 다중 뷰 인간 영상 생성 가능 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 기존 방법 대비 뛰어난 3D 일관성 및 생성 품질 제공 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 새로운 3D 일관성 평가 지표 및 주의 집중 방식 제시 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **단일 이미지로부터 고해상도의 다중 뷰 인간 모델을 생성하는 새로운 방법**을 제시하여, 엔터테인먼트, 헬스케어, 패션, 소셜 미디어 등 다양한 분야에서 활용될 수 있는 혁신적인 기술을 선보였습니다.  **기존의 복잡한 3D 모델링이나 다량의 데이터가 필요 없이** 단일 이미지만으로도 고품질의 결과물을 얻을 수 있다는 점에서, 관련 연구 분야에 큰 영향을 미칠 것으로 예상됩니다.  **향후 연구 방향**으로는 생성 가능한 뷰 수 증가 및 영상 생성 등으로 확장하는 방안이 제시되었으며, **다양한 응용 분야**에 대한 추가 연구도 기대됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.07785/x1.png)

> 🔼 이 그림은 Pippo 모델이 단일 사진에서 고해상도, 다중 뷰, 스튜디오급 이미지를 생성하는 능력을 보여줍니다. 각 샘플에서 왼쪽 이미지는 입력 이미지이고, 그 뒤에 보이는 이미지들은 본 적 없는 대상의 새롭게 생성된 뷰입니다. 1, 2행은 휴대폰으로 촬영한 전신 및 얼굴 사진만을 이용하여 생성한 이미지를 보여주고, 3행은 스튜디오에서 촬영한 머리 부분만 있는 이미지를 이용하여 생성한 이미지를 보여줍니다. 마지막 행은 Pippo 모델이 관찰된 콘텐츠와 생성된 콘텐츠를 정확하게 조화시키는 능력을 보여주고, 해당 그라운드 트루스를 함께 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Pippo generates high-resolution, multi-view, studio-quality images from a single photo. In each sample, the left-most image is the input, followed by novel generated views of unseen subjects. First and second rows show generations from Full-body and Face-only photos captured in-the-wild using a mobile phone. Third row shows generation from a Head-only studio image. Last row illustrates Pippo’s capability to faithfully blend observed and generated content, alongside the corresponding ground truth.
> </details>





{{< table-caption >}}
| # | Method (M<sup>2</sup>@ 128) | PSNR<sub>val</sub> ↑ | PSNR<sub>train</sub> ↑ |
|---|---|---|---|
| 1. | Mid-trained (No Overfitting) | 19.23 | 19.70 |
| 2. | + Camera (w/ MLP) [47, 73] | 17.95<sub>-1.28</sub> | 19.92<sub>+0.22</sub> |
| 3. | + Plücker (w/ MLP) [8, 75, 37, 27] | 18.89<sub>-0.34</sub> | 20.74<sub>+1.04</sub> |
| 4. | + ControlMLP | 19.45<sub>+0.22</sub> | 29.36<sub>+9.66</sub> |
| 5. | + SIREN | 20.13<sub>+0.90</sub> | 30.19<sub>+10.49</sub> |
| 6. | + Spatial Anchor (Ours) | 22.60<sub>+3.37</sub> | 30.49<sub>+10.79</sub> |{{< /table-caption >}}

> 🔼 이 표는 논문의 3.3절 'Understanding and Improving Spatial Control'에서 다양한 공간 제어 방식의 성능을 평가하기 위해 수행된 실험 결과를 보여줍니다.  Head-only 데이터셋의 단일 장면에 대해 100개의 뷰를 사용하여 모델을 과적합(overfitting) 학습시킨 후, 공간 제어 방식(카메라 및 공간 앵커)만 변경하여 60개의 새로운 뷰에 대해 성능을 평가했습니다.  1행의 결과를 기준으로 각 방식의 성능 변화를 양수(+) 또는 음수(-)로 표시하여, 각 공간 제어 방식의 변조 강도(modulation strength)를 테스트했습니다.
> <details>
> <summary>read the caption</summary>
> Table 1:  Evaluating and Designing Spatial Controls (Sec. 3.3). We overfit our multi-view model for 10101010K iterations on 100 views of a single scene from our Head-only dataset, and evaluate on 60 novel views of this scene by only varying the spatial controls (camera and Spatial Anchor). We use this setup to test the modulation strength of different spatial controls. Subscript values green/red show deviations from Row 1.
> </details>





### In-depth insights


#### Pippo's Multi-View Synthesis
Pippo는 단일 이미지로부터 고해상도 다중 뷰 인간 표현을 생성하는 새로운 접근 방식입니다. **핵심은 단일 이미지만을 사용하여 사람의 다양한 각도의 사진을 생성하는 능력**에 있습니다. 기존 방법들과 달리, Pippo는 추가적인 입력 없이도(예: 피팅된 매개변수 모델이나 카메라 매개변수) 1K 해상도의 밀도 높은 결과물을 생성합니다. 이는 **다중 뷰 확산 변환기**를 사용하고, 30억 개가 넘는 인간 이미지를 사용하여 사전 훈련하는 방식으로 가능해집니다.  **중간 훈련 및 후속 훈련 단계**를 거치면서 스튜디오에서 촬영한 고품질 데이터를 활용하여 정확도를 높이고, **3D 일관성을 유지하는 기술**을 도입합니다.  결과적으로, Pippo는 기존 방법보다 우수한 성능을 보이며 **다양한 뷰의 생성 및 3D 일관성 평가를 위한 향상된 지표**를 제공합니다.  하지만, 이러한 강점에도 불구하고, **훈련 데이터의 규모와 뷰 수의 제한**은 향후 개선이 필요한 부분입니다.  결론적으로, Pippo는 고해상도 다중 뷰 인간 생성 분야에 중요한 발전을 가져온 모델이지만, 추가 연구를 통해 더욱 발전시킬 수 있는 가능성 또한 보여주고 있습니다.

#### 3D Consistency Metric
본 논문에서 제시된 3D 일관성 평가 지표는 기존의 2D 이미지 품질 평가 지표(PSNR, SSIM, LPIPS)의 한계를 극복하기 위해 고안되었습니다. **기존 지표들은 3D 일관성을 직접적으로 평가하지 못하고, 생성된 이미지가 고해상도일수록 오류를 더 크게 반영하는 경향이 있었습니다.** 따라서, 이 논문에서는 **2D 키포인트 매칭과 삼각측량을 이용하여 3D 점들을 생성하고, 이를 다시 2D로 투영하여 재투영 오류를 계산하는 새로운 방식**을 제안합니다. 이는 카메라 자세 정보를 입력으로 사용하며, 기존 방법들보다 더 정확하고 효율적인 측정을 가능하게 합니다. **이러한 새로운 지표는 단순히 이미지 유사도가 아닌, 3D 공간에서의 일관성을 정량적으로 평가함으로써, 보다 현실적인 3D 인간 모델 생성을 위한 중요한 기준**을 제공합니다.  결과적으로, 제안된 3D 일관성 평가 지표는 다양한 멀티뷰 인간 생성 모델들의 성능 비교에 유용하게 활용될 수 있으며, 향후 3D 인간 모델 생성 연구 발전에 크게 기여할 것으로 예상됩니다.

#### Multi-Stage Training
본 논문에서 제시된 다단계 학습 전략은 **이미지 전용 사전 학습, 다중 뷰 중간 학습, 다중 뷰 후속 학습**의 세 단계로 구성됩니다.  **사전 학습 단계**에서는 대규모 인간 중심 데이터셋을 사용하여 이미지 조건화를 통해 모델을 사전 학습시켜 일반화 능력을 향상시킵니다.  **중간 학습 단계**에서는 저해상도에서 다수의 뷰를 동시에 생성하는 능력을 빠르게 향상시키기 위해 스튜디오에서 캡처한 데이터를 사용합니다.  **마지막 후속 학습 단계**에서는 고해상도에서 3D 일관성을 높이기 위해 공간 앵커 및 플뤼커 광선과 같은 정렬된 제어를 추가하여 모델의 3D 생성 능력을 더욱 향상시킵니다.  이러한 다단계 접근 방식은 각 단계에서 특정 목표에 집중함으로써 **모델의 성능과 효율성을 극대화**하는 데 효과적입니다. 특히, 후속 학습 단계에서의 정밀한 제어는 **고해상도 다중 뷰 생성의 품질과 3D 일관성을 크게 개선**하는 데 중요한 역할을 합니다.  다양한 해상도와 뷰 수에 대한 실험 결과는 본 전략의 효과를 입증합니다.

#### Attention Biasing
본 논문에서 제시된 "어텐션 바이어싱(Attention Biasing)" 기법은 **멀티 뷰 이미지 생성 시 어텐션 메커니즘의 엔트로피 증가 문제를 해결**하기 위한 핵심 전략입니다.  훈련 단계에서 본 모델은 제한된 수의 뷰만 학습하지만, 추론 단계에서는 훨씬 더 많은 뷰를 생성해야 하는데, 단순히 뷰의 수를 늘리면 어텐션 메커니즘의 엔트로피가 증가하여 생성 이미지의 질이 저하되는 현상이 발생합니다.  이러한 문제를 해결하기 위해, **어텐션 스케일링 인자를 동적으로 조절**하는 방법이 제시됩니다.  이는 기존 슈퍼 레졸루션 연구에서 영감을 얻어, 훈련 시의 토큰 수와 추론 시의 토큰 수의 비율에 따라 스케일링 인자를 조정하여 엔트로피 증가를 억제합니다. **성능 평가 결과는 이 기법이 추론 시 훈련 시보다 5배 이상 많은 뷰를 생성하는 것을 가능하게 하면서도 이미지 품질 저하를 방지**하는 효과를 보여줍니다. 이는 **멀티 뷰 생성 모델의 확장성 및 실용성을 크게 향상**시키는 중요한 발견입니다.  **어텐션 바이어싱은 단순한 기술적 개선을 넘어, 멀티 뷰 생성 모델의 근본적인 한계를 극복**하려는 노력의 결과물이며, 향후 연구에서도 중요한 참고 자료가 될 것으로 예상됩니다.

#### Future Directions
본 논문의 "미래 방향"에 대한 심층적인 고찰은 **다양한 시점의 일관된 비디오 생성**으로 확장하는 것을 포함합니다. 현재의 1K 해상도 이미지 생성에 그치지 않고, 시간적 일관성을 유지하는 고해상도 비디오 생성으로 나아가야 합니다.  또한, **더욱 효율적인 계산 방법**을 모색하여, 현재 제한적인 동시 생성 가능한 뷰의 수를 극복하고 보다 다양하고 풍부한 뷰를 생성할 수 있도록 해야 합니다.  **대규모 데이터셋의 활용**은 모델의 일반화 성능 향상에 중요한 역할을 하므로, 더욱 방대한 양질의 데이터 확보 및 활용 전략 또한 중요한 미래 과제입니다.  **오클루전(occlusion) 처리 개선**을 통해 부분적으로 가려진 이미지에서도 정확한 3D 인간 표현 생성이 가능하도록 연구가 진행되어야 합니다. 마지막으로, **새로운 평가 지표 개발**을 통해 3D 일관성을 더욱 정확하고 포괄적으로 평가하는 연구가 필요합니다. 이러한 노력을 통해 Pippo 모델은 보다 완벽하고 실용적인 3D 인간 모델 생성 시스템으로 발전할 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.07785/x2.png)

> 🔼 그림 2는 Pippo 모델의 훈련 과정을 보여주는 개념도입니다. 왼쪽에는 스튜디오에서 촬영한 다양한 각도의 이미지 데이터를 사용하여 Pippo라는 다중 뷰 확산 변환 모델을 훈련하는 과정을 나타냅니다.  훈련 과정에는 전체 참조 사진과 얼굴 부분만 잘라낸 이미지, 그리고 목표하는 뷰의 카메라 위치 및 머리의 3차원 위치와 방향을 나타내는 2차원 투영 공간 앵커(Spatial Anchor)를 조건으로 사용합니다.  모델은 노이즈가 포함된 목표 뷰 이미지와 시간 단계 정보를 입력받아 노이즈를 제거한 이미지를 예측합니다. 실제로는 사람 주위에 분할 마스크를 적용합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Pipeline overview. This is an illustration of how we train our model. (Left) we use data from a studio capture and train our multi-view diffusion model (right). We condition on a full reference photo and a cropped face, as well as the target view cameras and 2D projected spatial anchor indicating head position and orientation. Our diffusion model also takes in noisy target views and a timestep in order to predict the denoised views (top). In practice, we apply a segmentation mask around the person.
> </details>



![](https://arxiv.org/html/2502.07785/x3.png)

> 🔼 그림 3은 Pippo 모델의 DiT(Diffusion Transformer) 블록과 ControlMLP 블록의 아키텍처를 보여줍니다. 왼쪽의 DiT 블록은 논문 [62]를 기반으로 하며, AdaIn(Adaptive Instance Normalization) 기반의 timestep modulation을 사용합니다. 어텐션과 MLP 블록을 병렬적으로 적용하고, 생성된 노이즈 이미지와 identity conditioning 토큰에 대해 공동으로 self-attention을 적용합니다. 오른쪽의 ControlMLP 블록은 Plücker 좌표와 공간 앵커(Spatial Anchor)를 이용하여 경량화된 공간 정렬 조건화를 제공합니다. 이를 통해 모델은 입력 이미지의 2D 정보와 3D 공간 정보를 결합하여 다양한 시점의 이미지를 생성할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: DiT and ControlMLP Block. Our DiT block (left) loosely follows [62], with a AdaIn-based timestep modulation. We apply attention and MLP blocks in parallel [13], and jointly apply self-attention to the noisy generated and identity conditioning tokens. ControlMLP block (right) is used to provide lightweight spatially-aligned conditioning - Plücker and Spatial Anchor.
> </details>



![](https://arxiv.org/html/2502.07785/x4.png)

> 🔼 그림 4는 다양한 수의 뷰(토큰)에 대한 엔트로피 대 성장 계수(γ)의 관계를 보여줍니다(3.4절 참조). 이 그림은 제안된 어텐션 바이어싱 기법([35]에서 영감을 얻음)의 엔트로피 결과(Y축)를 다양한 토큰 수(개별 선 그래프) 및 식(6)에서 제시된 다양한 스케일링 성장 계수 γ(X축)에 대해 보여줍니다. X축에서 '스케일링 없음'은 기본 어텐션 공식([82])을 나타내고, γ=1.0는 이전 연구([35])의 공식을 나타냅니다. 실험적으로 γ=1.4가 가장 좋은 시각적 결과를 제공함을 확인했습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Entropy vs Growth Factor (γ𝛾\gammaitalic_γ) for varying number of views (tokens) (Sec. 3.4). We present the entropy results (Y-axis) from our Attention Biasing technique inspired from [35] for varying number of tokens (individual line plots), and across different scaling growth factor γ𝛾\gammaitalic_γ introduced in Eq. (6) (X-axis). On X-axis, 'No scaling' refers to the default attention formulation [82] and γ=1.0𝛾1.0\gamma=1.0italic_γ = 1.0 refers previous work [35] formulation. Empirically, we find that a slightly higher value of γ=1.4𝛾1.4\gamma=1.4italic_γ = 1.4 leads to best visuals.
> </details>



![](https://arxiv.org/html/2502.07785/x5.png)

> 🔼 그림 5는 다양한 성장 계수(γ)를 사용하여 생성된 이미지를 보여줍니다. 각 행은 기본적인 어텐션 메커니즘 [82](스케일링 없음), 이전 연구 [35], 그리고 본 논문의 식 (6)에서 제시된 방법을 사용하여 생성된 뷰들을 보여줍니다. 성장 계수(γ)가 1.0보다 클 때 엔트로피 증가를 완화하는 데 중요한 역할을 한다는 것을 알 수 있습니다. 그림에서는 512x512 해상도로 생성된 총 60개의 뷰 중에서 균등하게 샘플링된 10개의 뷰만을 보여줍니다. 모델은 훈련 중에 단 12개의 뷰(Ni=5*Nt)만을 동시에 디노이징하도록 훈련되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Generations under varying strengths of growth factor γ𝛾\gammaitalic_γ (Sec. 3.4). On each row we show the generated views across vanilla attention [82] (No scaling), prior work [35] and our formulation Eq. (6). It can be seen that growth factor (γ𝛾\gammaitalic_γ) greater than 1.0 is crucial to mitigate the entropy buildup. We show only 10 views per row subsampled evenly from 60 views generated at 512×512512512512\times 512512 × 512 resolution. The model was trained to jointly denoised only 12 views (Ni=5∗Ntsubscript𝑁𝑖5subscript𝑁𝑡N_{i}=5*N_{t}italic_N start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT = 5 ∗ italic_N start_POSTSUBSCRIPT italic_t end_POSTSUBSCRIPT).
> </details>



![](https://arxiv.org/html/2502.07785/x6.png)

> 🔼 그림 6은 본 논문에서 제안하는 Pippo 모델과 기존 최첨단 모델인 DiffPortrait3D (얼굴만)과 SiTH (전신)의 시각적 비교 결과를 보여줍니다.  단일 이미지를 입력으로 사용하여 다양한 각도에서의 고해상도 이미지 생성 능력을 비교 분석합니다. Pippo 모델이 기존 모델들에 비해 더욱 사실적이고 다양한 각도에서의 이미지 생성 능력이 뛰어남을 시각적으로 보여줍니다. 특히, 사람의 자세나 표정을 정확하게 유지하면서, 새롭고 다양한 시점을 생성하는 Pippo 모델의 우수성을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Visual comparison with state-of-the-art methods. We visually compare Pippo with state-of-the-art baselines DiffPortrait3D [24] (head-only) and SiTH [29] (full-body) generation.
> </details>



![](https://arxiv.org/html/2502.07785/x7.png)

> 🔼 그림 7은 Pippo 모델이 단일 이미지 입력만으로 고해상도(1K) 다중 뷰 이미지를 생성하는 능력을 보여줍니다. 그림은 휴대폰으로 촬영한 사진과 스튜디오에서 촬영한 이미지를 모두 포함하는 다양한 입력에 대한 결과를 보여줍니다. 첫 번째 행은 휴대폰으로 촬영한 전신 사진과 스튜디오에서 촬영한 전신 사진의 결과를 보여주고, 두 번째 행은 휴대폰으로 촬영한 얼굴 사진의 결과를 보여줍니다. 세 번째와 네 번째 행은 스튜디오에서 촬영한 전신 사진의 결과를 보여주고, 마지막 두 행은 스튜디오에서 촬영한 단일 이미지에서 10개의 새로운 뷰를 동시에 생성한 결과를 보여줍니다.  각 블록의 왼쪽에는 입력 이미지가 표시되며, 점선으로 구분되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: High Resolution Multi-view Generation of Unseen subjects. Pippo enables generation of high-resolution 1K images given only a single image as input (left most in each block, separated with a dashed line). First row LHS shows generation from mobile captured photo, while the RHS shows unseen studio subject. Second row shows mobile captured face-only generations. Third and fourth row shows unseen studio subjects. Last two rows demonstrate simultaneous generation of 10 novel views given unseen studio subject.
> </details>



![](https://arxiv.org/html/2502.07785/x8.png)

> 🔼 그림 8은 Pippo가 부분적으로 또는 완전히 가려진 얼굴, 전체 신체 데이터셋의 테스트 분할에서 관찰되지 않은 티셔츠 디자인과 같이 불완전한 입력 이미지를 사용하여 생성한 결과를 보여줍니다.  Pippo가 알려진 내용을 충실하게 따르면서 보이지 않는 부분을 자동으로 완성하는지 확인하기 위해 파란색 점선으로 구분된 해당 그라운드 트루스도 함께 표시했습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Pippo can handle occluded inputs. We show Pippo’s generations given incomplete input images – such as partially or fully occluded faces, unobserved t-shirt designs on test split of Full-body dataset. We show corresponding ground truth separated with blue dotted line – it can be seen that Pippo faithfully follows the known content while auto-completing unseen segments.
> </details>



![](https://arxiv.org/html/2502.07785/x9.png)

> 🔼 그림 9는 다양한 성장 계수 γ(섹션 3.4)에서 생성된 뷰를 보여줍니다. 각 행에는 일반적인 어텐션 [82](스케일링 없음), 이전 연구 [35] 및 저희가 제안한 식 (6)의 결과가 나타납니다. 성장 계수(γ)가 1.0보다 크면 엔트로피 축적을 완화하는 데 도움이 되지만, γ가 1.6을 넘어서면 과포화 아티팩트가 발생합니다(높은 CFG 스케일에 가까움). 512x512 해상도로 생성된 60개의 뷰 중에서 균등하게 하위 샘플링된 6개의 뷰만 표시합니다. 모델은 12개의 뷰(Ni=5*Nt)를 공동으로 제거하도록 훈련되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Generations under varying strengths of growth factor γ𝛾\gammaitalic_γ (Sec. 3.4). On each row we show the generated views across vanilla attention [82] (No scaling), prior work [35] and our formulation Eq. (6). Growth factor (γ𝛾\gammaitalic_γ) greater than 1.0 helps mitigate the entropy buildup, however increasing γ𝛾\gammaitalic_γ beyond 1.61.61.61.6 leads to oversaturation artifacts (somewhat akin to high CFG scale). We show only 6 views per row subsampled evenly from 60 views generated at 512×512512512512\times 512512 × 512 resolution. The model was trained to jointly denoised only 12 views (Ni=5∗Ntsubscript𝑁𝑖5subscript𝑁𝑡N_{i}=5*N_{t}italic_N start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT = 5 ∗ italic_N start_POSTSUBSCRIPT italic_t end_POSTSUBSCRIPT).
> </details>



![](https://arxiv.org/html/2502.07785/x10.png)

> 🔼 그림 10은 연구에서 사용된 Humans-3B 데이터셋의 통계 정보를 보여줍니다.  가로축(X축)에는 사람 키, 이미지 너비, 사람 검출 신뢰도, 검출된 사람의 너비, 상체 가시성 점수, 전체 신체 가시성 점수, 이미지 품질 평점 등의 속성들이 구간화되어 표시되고, 세로축(Y축)에는 각 구간에 속하는 데이터의 비율(0에서 1 사이의 값)이 표시됩니다.  이러한 통계 정보를 이용하여 데이터 필터링을 수행하여 사람 검출 신뢰도와 이미지 품질이 높은 이미지를 유지합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Statistics of our curated Humans-3B dataset. We bucket these attributes in bins along X-axis and plot their respective sizes normalized between [0,1]01[0,1][ 0 , 1 ] on Y-axis. Filtering with these statistics enable us to retain images with detected-person confidence and image quality.
> </details>



![](https://arxiv.org/html/2502.07785/x11.png)

> 🔼 그림 11은 사전 훈련된 모델의 정성적 및 에이비에이션 시각 자료를 보여줍니다. 정량적 평가와 일치하게, 사람 중심 필터링을 사용하면 생성된 이미지의 화질이 향상되고, 이미지 조건부 모델은 시각적으로 실제 도메인(일상적인 아이폰 캡처)에 더 가까운 샘플을 생성합니다. 또한 해상도가 높아짐에 따라 화질이 크게 향상됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Qualitiative and ablation visuals from pretrained model. Consistent with quantitative evaluation, visual quality of generated images improves with using human-centric filtering, and image-conditioned models generate samples which are visually closer to the domain (casual iPhone captures). There is also an obvious boost in quality due to higher resolution.
> </details>



![](https://arxiv.org/html/2502.07785/x12.png)

> 🔼 그림 12는 공간 앵커의 누락 또는 불일치에 대한 실험 결과를 보여줍니다. 머리 부분만 있는 P1@512 모델을 사용하여 추론을 수행하고, 공간 앵커를 누락시키거나 입력 머리 자세와 일치하지 않게(바닥을 향해 90도 회전) 설정했습니다. 공간 앵커가 누락되면, 생성된 뷰에 피사체의 머리가 보이지 않는다는 것을 의미하기 때문에 Pippo는 종종 빈 이미지를 생성합니다. 그러나 Pippo는 앵커 회전에 대해 강건하며, 공간 앵커는 배치 제어에만 사용되고 입력 이미지에서 머리 자세를 추론한다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Ablation with Missing or Inconsistent Spatial Anchors. We run inference on the Head-only P1111@512 model with missing spatial anchor, or when it is inconsistent with input head pose rotated downwards towards the floor by 90∘.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| # | Method (Stage @ Resolution) | FID ↓ | 
|---|---|---|
| 1. | Pippo (P1@512) | **51.164** | 
| 2. | Human-centric Filtering (P1@128) | **75.639** | 
| 3. | No Filtering (P1@128) | 86.838 | 
| 4. | Image-conditioned (P1@128) | **75.639** | 
| 5. | Text-conditioned (P1@128) | 109.720 | {{< /table-caption >}}
> 🔼 표 2는 모델 전훈련 및 데이터 필터링에 대한 결과를 보여줍니다. 전체 전훈련된 모델 P1@512의 결과와 여러 가지 P1@128 모델의 비교 결과가 제시되어 있습니다. FID는 iPhone 데이터셋(1,000개 샘플)을 기반으로 계산되었습니다. 이 표는 모델의 성능에 미치는 전훈련 및 데이터 전처리의 영향을 보여주는 데 중점을 둡니다.
> <details>
> <summary>read the caption</summary>
> Table 2:  Pretraining and Data Filtering. We report results of the full pretrained model P1111@512, and compare several variants of P1111@128 models. We report FID on iPhone dataset (1k samples).
> </details>

{{< table-caption >}}
|                   | # | Split & Resolution | RE@SG ↓ | PSNR ↑ | SSIM ↑ | LPIPS ↓ | Face ↑ | Body ↑ |
|-------------------|----|----------------------|---------|---------|---------|---------|---------|--------|
| Head-only          | 1. | Studio (128)        | 3.3<sub>+0.8</sub> | 21.0    | 67.6    | 14.8    | 62.0<sub>-13.3</sub> | 61.5<sub>-16.2</sub> |
|                   | 2. | Studio (1K)         | 3.4<sub>+0.5</sub> | 20.3    | 72.0    | 26.2    | 73.5<sub>-2.5</sub>  | 79.4<sub>-0.1</sub>  |
|                   | 3. | iPhone Face (1K)     | 3.0      | -       | -       | -       | 67.6    | -      |
| Full-body         | 4. | Studio (128)        | 3.6<sub>+0.1</sub> | 22.8    | 84.0    | 10.0    | 41.7<sub>-8.5</sub>  | 67.1<sub>-9.4</sub>  |
|                   | 5. | Studio (1K)         | 1.5<sub>+0.1</sub> | 22.4    | 91.7    | 11.1    | 64.7<sub>-6.0</sub>  | 74.1<sub>-2.2</sub>  |
|                   | 6. | iPhone (1K)         | 1.7      | -       | -       | -       | 58.0    | 68.1   |{{< /table-caption >}}
> 🔼 표 3은 사전에 보지 못한 스튜디오 및 아이폰 데이터셋에 대한 실험 결과를 보여줍니다. 세 가지 해상도(128, 512, 1024)에서 사후 학습된 Pippo 모델의 성능을 평가했습니다. 3D 지표(PSNR, SSIM, LPIPS)와 제안된 Reprojection Error (RE@SG)를 측정하여 모델의 정확도와 3D 일관성을 평가하였습니다. RE@SG는 SuperGlue 추정 방식을 사용하며, 기준 진실 데이터가 필요하지 않습니다. 또한 얼굴과 신체 유사성(2D 지표)을 측정하여 신원 보존 능력을 평가했습니다. 표에서 빨간색 밑줄은 기준 진실 값과의 편차를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 3:  Results on Unseen Studio and iPhone data (Sec. 4.3.) We report results on Post-trained Pippo models at three different resolutions. We report 3D metrics PSNR, SSIM, and LPIPS; as well as our proposed Reprojection Error (RE@SG) under SuperGlue estimation which does not require ground truth (Sec. 3.5). We report 2D Face and Body similarities. Red subscript show deviation against ground truth value.
> </details>

{{< table-caption >}}
| # | Method & Resolution | RE@SG ↓ | Face ↑ | Body ↑ |
|---|---|---|---|---|
| 1. | MV-Adapter [32] (768) | 4.7 | 43.0 | 64.1 |
| 2. | Era3D [44] (512) | 4.1 | 38.1 | 64.4 |
| 3. | Wonder3D [48] (256) | 5.3 | 34.7 | 58.8 |
| 4. | Pippo (P3@1K) | 3.0 | 58.0 | 68.1 |{{< /table-caption >}}
> 🔼 본 표는 최첨단 다중 뷰 확산 모델들과 비교하여 Pippo의 성능을 정량적으로 비교 분석한 결과를 보여줍니다.  Pippo는 기존 모델들보다 높은 해상도에서 동작하면서도 얼굴과 신체 유사성(정체성 보존) 및 3D 일관성(RE@SG)을 더 잘 유지함을 보여줍니다.  즉, Pippo가 더욱 사실적이고 일관성 있는 다중 뷰 이미지를 생성한다는 것을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Quantitative comparison with SoTA multi-view models. We quantitatively compare Pippo against state-of-the-art multi-view diffusion models. We find that Pippo preserves identity (i.e., face and body similarity) and 3D consistency (RE) better while operating at a higher resolution compared to baselines.
> </details>

{{< table-caption >}}
| # | Dataset (P3@1K) | RE@SG ↓ | PSNR ↑ | SSIM ↑ | LPIPS ↓ | Face ↑ | Body ↑ |
|---|---|---|---|---|---|---|---| 
| 1. | Ava-256 (Head-only) | 3.8 | 20.1 | 68.7 | 26.6 | 72.9 | 76.8 |
| 2. | Goliath (Full-body) | 1.2 | 20.4 | 89.7 | 15.5 | 87.5 | 77.7 |{{< /table-caption >}}
> 🔼 표 5는 공개적으로 사용 가능한 Ava-256 및 Goliath 데이터셋을 사용하여 Pippo 모델의 성능을 벤치마킹한 결과를 보여줍니다.  이 표는 Pippo 모델이 내부 스튜디오 데이터셋에서 보여준 성능과 유사한 수준의 성능을 공개 데이터셋에서도 달성함을 보여줍니다.  이는 향후 다른 모델들과 Pippo 모델의 성능을 비교하는 데 유용한 기준을 제공합니다.  Ava-256 데이터셋은 머리 부분만 포함한 데이터이고 Goliath 데이터셋은 전신 데이터를 포함합니다.  Pippo 모델은 두 데이터셋 모두에서 내부 스튜디오 데이터셋과 비슷한 성능을 보여주어 모델의 일반화 성능이 뛰어남을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Benchmarking Pippo on public Ava-256 and Goliath datasets. We find that Pippo’s performance on these datasets is inline with its performance on internal studio datasets. This will aid future comparisons against Pippo.
> </details>

{{< table-caption >}}
| # | Method (Stage @ Res.) | RE@SG ↓ | PSNR ↑ | SSIM ↑ | LPIPS ↓ | Face ↑ | Body ↑ |
|---|---|---|---|---|---|---|---| 
| 1. | Pippo (P<sup>3</sup>@512) | 2.7<sub>+0.7</sub> | 21.7 | 71.7 | 21.5 | 74.1<sub>-2.0</sub> | 77.4<sub>-2.4</sub> |
| 2. | Pippo Face-only (P<sup>3</sup>@512) | 2.4<sub>+0.4</sub> | 20.5 | 70.3 | 25.3 | 74.3<sub>-1.7</sub> | 75.8<sub>-4.0</sub> |
| 3. | No Mid-train (P<sup>3</sup>@512) | 5.6<sub>+3.6</sub> | 14.5 | 59.5 | 44.2 | 20.4<sub>-55.6</sub> | 63.4<sub>-16.4</sub> |
| 4. | Pippo (P<sup>3</sup>@128) | 3.3<sub>+0.8</sub> | 21.0 | 67.6 | 14.8 | 62.0<sub>-13.3</sub> | 61.5<sub>-16.2</sub> |
| 5. | No Anchor (P<sup>3</sup>@128) | 11.5<sub>+9.0</sub> | 17.1 | 54.0 | 21.1 | 63.1<sub>-12.2</sub> | 68.3<sub>-9.3</sub> |
| 6. | No Plücker (P<sup>3</sup>@128) | 4.2<sub>+1.7</sub> | 20.2 | 64.5 | 16.1 | 63.5<sub>-11.8</sub> | 66.1<sub>-11.5</sub> |
| 7. | Pippo (M<sup>2</sup>@128) | 3.4<sub>+0.9</sub> | 19.1 | 61.4 | 17.2 | 60.0<sub>-15.3</sub> | 62.6<sub>-15.0</sub> |
| 8. | No Pre-train (M<sup>2</sup>@128) | 5.9<sub>+3.4</sub> | 13.1 | 39.3 | 44.9 | 19.5<sub>-55.8</sub> | 49.0<sub>-28.6</sub> |
| 9. | Cross-Attn (M<sup>2</sup>@128) | 3.5<sub>+1.0</sub> | 18.0 | 59.2 | 22.1 | 66.2<sub>-9.1</sub> | 70.7<sub>-7.0</sub> |
| 10. | Non-frontal (M<sup>2</sup>@128) | 5.8<sub>+3.3</sub> | 15.2 | 52.4 | 30.1 | 49.2<sub>-26.1</sub> | 60.7<sub>-16.9</sub> |{{< /table-caption >}}
> 🔼 표 6은 논문의 방법론 섹션(Method)에 있는 표로, 다양한 디자인 선택과 학습 단계에 따른 실험 결과를 보여줍니다.  Head-only 데이터셋을 사용하여 128x128과 512x512 해상도에서 여러 다중 뷰 모델을 평가했습니다.  Mid-training 및 Pre-training의 여부, 공간 제어 방식, 참조 조건화 방법 등을 비교 분석하여 각 요소의 영향을 확인합니다. 학습 단계는 M2(Mid-training)와 P3(Post-training)으로 표기되고, @ 기호 뒤에 해상도가 명시됩니다.
> <details>
> <summary>read the caption</summary>
> Table 6:  Ablation on design choices and training stages. We evaluate several multi-view models at 128×128128128128\times 128128 × 128 and 512×512512512512\times 512512 × 512 resolution at different training stages on Head-only dataset. We ablate the choice of doing Mid-training and Pre-training, along with different spatial controls and reference conditioning methods..The training stages are labeled as M2222 (Mid-training) and P3333 (Post-training), followed by @ specified resolution.
> </details>

{{< table-caption >}}
| # | Pretrain Data (M²@128) | RE@SG ↓ | PSNR ↑ | SSIM ↑ | LPIPS ↓ | Face ↑ | Body ↑ |
|---|---|---|---|---|---|---|---| 
| 1. | 30M (1% HQ) | 3.8 | 21.3 | 81.8 | 13.3 | 30.6 | 66.2 |
| 2. | 900M (30% Random) | 4.0 | 21.6 | 82.0 | 12.1 | 30.6 | 67.2 |
| 3. | 2.1B (70% Random) | 3.7 | 21.6 | 82.1 | 12.1 | 37.6 | 67.5 |
| 4. | Humans-3B (100%) | 3.7 | 21.9 | 82.3 | 12.7 | 41.7 | 67.2 |{{< /table-caption >}}
> 🔼 본 표는 Humans-3B 데이터셋의 서브셋 크기 변화에 따른 사전 훈련 효과를 보여줍니다.  전체 데이터셋의 1%, 30%, 70%, 100%를 사용하여 사전 훈련된 체크포인트를 이용, 본 논문의 Full-body 중간 훈련을 수행한 결과를 보여줍니다. 표의 결과는 대규모 데이터가 새로운 신원(즉, 얼굴 유사성)에 대한 일반화에 매우 중요함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Ablating the size of pre-training dataset on Humans-3B. We conduct Full-body mid-training with pretrained checkpoints trained on 1%, 30%, 70%, and 100% subsets of Humans-3B dataset. We found large-scale data is crucial for generalization to novel identities (i.e., face similarity).
> </details>

{{< table-caption >}}
| # | Method (Stage @ Resolution) | Views | Speed (sec) ↓ | 
|---|---|---|---| 
| 1. | Pretrained (P1@256) | 1 | 2.51 | 
| 2. | Pretrained (P1@512) | 1 | 2.59 | 
| 3. | Mid-trained (M2@128) | 4 | 6 | 
| 4. | Mid-trained (M2@128) | 48 | 14 | 
| 5. | Post-trained (P3@512) | 4 | 40 | 
| 6. | Post-trained (P3@512) | 48 | 490 | 
| 7. | Post-trained (P3@1K) | 4 | 185 | 
| 8. | Post-trained (P3@1K) | 12 | 622 | {{< /table-caption >}}
> 🔼 표 8은 Pippo 모델의 추론 속도를 보여줍니다. 다양한 해상도와 생성되는 뷰의 수에 따른 추론 속도를 bfloat16을 사용하여 최적화 없이 측정한 결과를 보여줍니다.  표에는 모델의 종류, 해상도, 생성된 뷰의 수, 그리고 각 조건에서의 추론에 걸린 시간(초)이 나와 있습니다. 이는 사용자가 Pippo 모델을 실제로 사용할 때 예상되는 추론 시간을 파악하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 8:  Inference Speed of Pippo. We show inference speed without any optimizations (using bfloat16) against varying resolution and number of views being generated.
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