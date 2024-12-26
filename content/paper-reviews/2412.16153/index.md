---
title: "MotiF: Making Text Count in Image Animation with Motion Focal Loss"
summary: "MotiF: 움직임에 초점을 맞춘 손실 함수로 텍스트 기반 이미지 애니메이션 개선"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Video Understanding", "🏢 Brown University",]
showSummary: true
date: 2024-12-20
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.16153 {{< /keyword >}}
{{< keyword icon="writer" >}} Shijie Wang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-25 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.16153" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.16153" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/motif-making-text-count-in-image-animation" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 텍스트 기반 이미지 애니메이션(TI2V) 모델들은 **정적인 배경에 과도하게 의존**하여 텍스트에 맞는 동적인 영상 생성에 어려움을 겪었습니다. 특히, 움직임이 적은 영역과 많은 영역을 동일하게 처리하는 기존의 손실 함수(L2 loss)는 모델의 학습 방향을 제대로 제시하지 못했습니다. 본 논문에서는 이러한 문제점을 해결하기 위해, **광학 흐름(optical flow)**을 이용하여 **움직임 히트맵(motion heatmap)**을 생성하고, 이를 통해 **움직임이 많은 영역에 가중치를 부여**하는 새로운 손실 함수인 **MotiF(Motion Focal Loss)**를 제안합니다. 또한, 다양한 시나리오를 포함하는 새로운 **TI2V 벤치마크** 데이터셋을 제시하여 모델 성능을 객관적으로 평가했습니다.  실험 결과, MotiF는 기존 모델들보다 우수한 성능을 보였으며, 특히 텍스트 일치도와 움직임 생성 측면에서 큰 향상을 보였습니다. 이는 **TI2V 모델 학습 방식에 대한 새로운 접근법**을 제시하고, 향후 관련 연구에 중요한 기여를 할 것으로 기대됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} MotiF는 optical flow 기반의 motion heatmap을 이용하여 **움직임이 많은 영역에 가중치를 부여**, 텍스트 일치도 및 움직임 생성 성능 향상 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} TI2V Bench는 **다양한 시나리오와 이미지-텍스트 쌍**을 포함하는 새로운 벤치마크 데이터셋 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} MotiF는 기존 9개의 오픈소스 모델보다 우수한 성능(평균 72% 선호도)을 기록하며 **TI2V 분야의 기술 발전**에 기여 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **텍스트 기반 이미지 애니메이션** 분야의 중요한 문제점들을 해결하고 새로운 연구 방향을 제시하여, 해당 분야 연구자들에게 중요한 의미를 지닙니다. **TI2V 벤치마크** 제시를 통해 객관적인 평가 기준을 마련하고, **MotiF** 기법을 통해 성능 향상을 이끌어냄으로써, 향후 TI2V 모델 개발 및 성능 향상 연구에 큰 영향을 미칠 것으로 예상됩니다. 특히, **영상 생성의 움직임에 대한 집중도를 높이는 훈련 방식**은 향후 다른 영상 생성 모델 연구에도 적용될 수 있는 잠재력을 지니고 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.16153/x2.png)

> 🔼 본 논문의 그림 1은 MotiF의 동작 원리와 결과를 보여줍니다. (a)는 예시 비디오 프레임과 광학 흐름(optical flow)을 기반으로 계산된 모션 히트맵을 보여줍니다. 97%의 픽셀은 정지 상태이고, 단 3%만 의미있는 움직임을 보입니다. (b)는 표준 TI2V 학습 과정에서 모델이 L2 손실을 최소화하기 위해 조건 이미지(conditional image)에 과도하게 의존할 수 있음을 보여줍니다. 이 문제는 기존 연구 [53]에서 조건 이미지 누출(conditional image leakage)로 정의되었습니다. MotiF는 모션 히트맵 재가중치를 사용하여 모델 학습을 더 많은 움직임이 있는 영역으로 유도하여 이 문제를 해결합니다. (c)는 제안된 TI2V Bench의 예시를 사용하여 MotiF와 기준 모델(baseline)의 정성적 결과를 비교합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Motivation and results of MotiF. (a) Example video frames and the corresponding motion heatmaps calculated from optical flow. In this example, 97%percent9797\%97 % of the pixels are static while only 3%percent33\%3 % has meaningful motion. (b) In standard TI2V training pipeline, the model may learn to over-rely on the conditional image to optimize the L2 loss. This issue has been identified in [53] and termed as conditional image leakage. We propose MotiF to guide the model’s learning to focus on regions with more motion via motion heatmap re-weighting. (c) Qualitative results comparing MotiF to the baseline on examples from our proposed TI2V Bench.
> </details>





{{< table-caption >}}
| Name | Type | Text-Driven | Media-Text Pairs | Unique Media | Unique Text | Evaluation | Metrics |
|---|---|---|---|---|---|---|---| 
| I2V-Bench [33] | video-text | No | 2,950 | 2,950 | 2,950 | auto | visual quality, visual consistency |
| AIGCBench [13] | video-text | No | 1,000 | 1,000 | 1,000 | auto | MSE, SSIM, CLIP, etc |
| AIGCBench [13] | image-text | No | 925 | 925 | 925 | auto | MSE, SSIM, CLIP, etc |
| AIGCBench [13] | image(synthetic)-text | No | 2,003 | 2,003 | - | auto | MSE, SSIM, CLIP, etc |
| Animate Bench [51] | image(synthetic)-text | Yes | 105 | 35 | ~{}16 | auto | image alignment, text alignment |
| TI2V Bench (Ours) | image(synthetic)-text | Yes | 320 | 88 | 133 | human | TI2V score |{{< /table-caption >}}

> 🔼 표 1은 최근 Text-Image-to-Video (TI2V) 생성 평가 벤치마크를 보여줍니다.  논문에서는 TI2V 생성의 핵심이 텍스트가 동작을 설명하는 데 있다고 주장하며, 이를 '텍스트 기반'으로 명시합니다.  Animate Bench는 제안된 벤치마크와 유사하지만, 개인화 영역에 특화되어 데이터셋 크기와 다양성이 이미지와 텍스트 설명 모두에서 제한적입니다.  또한 기존 지표들은 모두 동작을 고려하지 않는 이미지 수준 평가라는 점을 지적합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Recent TI2V evaluation benchmarks. We believe the key for TI2V generation is that the text should describe the motion, termed as text-driven in the table. While Animate Bench is similar to our benchmark, it’s very specific for the personalization domain and the dataset size and diversity are limited in both the images and the text descriptions. Moreover, the proposed metrics are all image-level evaluations that do not account for motion.
> </details>





### In-depth insights


#### MotiF: Motion Focus
MotiF: Motion Focus는 영상 생성 모델의 훈련 과정에서 **움직임에 대한 집중도를 높이는 기법**입니다. 기존의 Text-Image-to-Video (TI2V) 모델들은 정지된 배경 영역과 움직이는 영역을 동일하게 처리하여 **움직임 정보 학습에 어려움**을 겪었습니다.  MotiF는 광학 흐름(optical flow)을 이용하여 움직임 히트맵(motion heatmap)을 생성하고, 이를 활용하여 손실 함수(loss function)의 가중치를 조절합니다. **움직임이 큰 영역의 손실에 더 큰 가중치**를 부여하여 모델이 움직임 정보에 집중하도록 유도하는 것입니다. 이를 통해 텍스트 프롬프트와 일치하는 동작 생성 능력과 텍스트 정합도가 향상됩니다. **Optical flow 기반의 motion heatmap 생성 및 L2 loss 가중치 조절**이라는 단순하지만 효과적인 방법을 사용하며, 추가적인 inference 단계 없이 훈련 과정에 통합되어 효율성을 높입니다.  기존 연구들과 달리 입력 신호 개선이 아닌 **훈련 목표 개선**에 초점을 맞춰 차별성을 갖습니다.

#### TI2V Bench: Dataset
본 논문에서 제시된 TI2V Bench 데이터셋은 기존 Text-to-Image-to-Video (TI2V) 모델 평가의 어려움을 해결하기 위해 고안되었습니다. **기존 데이터셋의 부족**으로 인해, 다양한 시나리오와 움직임을 포괄하는 새로운 벤치마크의 필요성이 대두되었고, 이에 따라 **320개의 이미지-텍스트 쌍**으로 구성된 TI2V Bench가 제작되었습니다. **다양한 시나리오와 스타일의 이미지**를 포함하여 모델의 견고성을 평가하고, **세밀한 동작 지시가 포함된 텍스트 프롬프트**를 통해 모델의 정확성을 높이는 데 중점을 두었습니다. 특히, **새로운 물체의 등장이나 세밀한 객체 조작** 등의 어려운 시나리오를 포함하여 모델의 한계를 드러내고자 하였습니다. 또한, **객관적인 자동 평가 지표의 한계**를 인지하여, **인간 평가를 통한 주관적인 평가 방식**을 도입하여, 이미지 정합도, 텍스트 일치도, 객체 움직임, 전반적인 품질 등 다양한 측면을 종합적으로 고려한 평가를 수행하였습니다.  TI2V Bench는 이처럼 **종합적이고 까다로운 평가를 위한 포괄적인 데이터셋**으로,  향후 TI2V 분야의 발전에 크게 기여할 것으로 기대됩니다. 

#### Human Evaluation
본 논문에서 인간 평가는 **정량적 지표의 한계를 극복**하기 위해 사용되었습니다. 기존 자동 평가 지표들이 영상의 질, 움직임 강도, 텍스트 정합성 등 여러 측면을 고려하지만, 실제 인간의 지각과 일치하지 않는 경우가 많다는 점을 인지하고 있습니다. 따라서 **주관적 평가를 통해 인간의 직관적인 판단을 반영**하고자 하였습니다.  A/B 테스트 방식과 JUICE 프로토콜을 참고하여, 평가자들이 두 개의 영상을 비교하여 더 나은 영상을 선택하고 그 이유를 여러 측면(영상과 텍스트의 정합성, 객체의 움직임, 전반적인 질)에서 구체적으로 설명하도록 설계했습니다. 이를 통해 **정량적 지표만으로는 알 수 없는 세부적인 강점과 약점을 파악**하고, 모형의 성능을 보다 정확하게 평가하고자 하였습니다. **인간 평가의 신뢰도를 높이기 위해** 다수의 평가자를 통해 결과를 도출하고, 주관적인 평가 편향을 최소화하기 위한 노력을 기울였습니다. 이러한 **다각적이고 심층적인 접근**을 통해 연구의 신뢰성을 더욱 높였습니다.

#### Ablation Studies
본 논문의 "Ablation Studies" 부분은 제안된 방법의 각 구성 요소의 중요성을 밝히는 데 중점을 둡니다. 특히, **Motion Focal Loss의 효과**를 검증하기 위해 해당 손실 함수를 제거한 기준 모델과 비교 분석하여 성능 향상을 정량적으로 보여줍니다.  **역 Motion Focal Loss**를 적용한 실험 결과를 통해 제안된 방식의 효율성을 더욱 강조합니다.  또한, **이미지 조건화 기법**에 대한 에이블레이션 연구를 통해 이미지 정보 통합 방식의 영향을 분석하고 최적의 방법을 제시합니다. 이러한 실험들을 통해, **Motion Focal Loss가 주요 성능 향상에 기여**하며, 제안된 이미지 조건화 방식이 전체적인 성능 향상에 도움이 됨을 입증합니다.  결과적으로, 본 연구는 제안된 방법의 각 구성요소에 대한 깊이 있는 분석을 제공하여 신뢰성을 높이고, 향후 연구를 위한 중요한 지침을 제시합니다.

#### Future Directions
본 논문에서 제시된 MotiF는 Text-Image-to-Video (TI2V) 생성에서 텍스트 정합도를 향상시키는 데 효과적임을 보여주었지만, **여전히 복잡한 시나리오에서는 한계를 드러냅니다.**  특히, 여러 개체가 등장하거나 새로운 개체가 등장하는 경우, 또는 세밀한 동작이 요구될 때는 성능이 저하될 수 있습니다. 따라서 **향후 연구 방향은 다음과 같이 설정될 수 있습니다.** 첫째, **더욱 정교한 모션 히트맵 생성 기법**을 개발하여 모션 정보를 보다 정확하게 포착하는 것입니다. 광학 흐름 외에,  세분화된 개체 분할 및 동작 인식 기술을 활용하는 것이 고려될 수 있습니다. 둘째, **모델 아키텍처 개선**을 통해 텍스트와 이미지 정보를 보다 효과적으로 통합하는 방법을 연구해야 합니다.  **모션 정보의 효과적인 표현 및 주입 방식**에 대한 탐구도 중요합니다. 셋째, **TI2V 벤치마크의 확장**이 필요합니다. 더욱 다양하고 복잡한 시나리오를 포함하여 벤치마크의 범위를 넓히는 연구가 필요하며, **정량적 평가 지표** 개발에 대한 연구도 중요합니다.  마지막으로 **모델의 일반화 능력을 향상**시키는 방법에 대한 연구가 필요합니다.  다양한 데이터셋에서의 성능 평가 및 안정적인 모델 학습 전략 개발이 중요한 과제입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.16153/x3.png)

> 🔼 이 그림은 MotiF와 기존 TI2V 방법들의 차이점을 보여줍니다. 기존 방법들은 모델에 추가적인 모션 신호(모션 점수나 마스크)를 입력으로 사용하여 모션 정보를 간접적으로 활용하는 데 초점을 맞춘 반면, MotiF는 학습 목표에 초점을 맞춰 광학 흐름(optical flow)으로부터 얻은 모션 강도에 따라 확산 손실(diffusion loss)의 가중치를 조정합니다. MotiF는 간단하고 효과적이며 추론 중에 추가적인 입력이 필요하지 않고 기존 기술들과 상호 보완적인 관계를 가집니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: High-level comparisons of MotiF vs. prior works. Previous TI2V generation methods mainly focused on deriving additional motion signals (motion score and/or motion mask) as inputs for the model to leverage implicitly. On the contrary, we focus on the learning objective and propose to weight the diffusion loss based on the motion intensity, that is derived from optical flow. Our method is simple, effective, and does not require additional inputs during inference. Moreover, MotiF is complementary to existing techniques.
> </details>



![](https://arxiv.org/html/2412.16153/x4.png)

> 🔼 그림 3은 논문에서 제안하는 TI2V Bench 데이터셋의 예시 이미지-텍스트 쌍들을 보여줍니다. 각 열(scenario)은 애니메이션을 통해 다양한 동작을 생성할 수 있는 잠재적인 장면을 나타냅니다.  여러 개의 물체(노란색/파란색/빨간색 풍선)가 초기 이미지에 포함되어 세밀한 제어가 가능하도록 하거나, 텍스트 프롬프트가 새로운 물체(프리스비, 거품)가 장면에 등장하는 것을 설명하는 등 어려운 시나리오가 포함되어 있습니다. 다양한 프롬프트를 사용하여 공개적으로 이용 가능한 Meta AI 도구를 통해 다양한 이미지를 생성하였으며, 품질이 낮거나 적절한 초기 상태가 아닌 이미지는 제거되었습니다.  이 그림은 TI2V Bench 데이터셋의 다양성과 난이도를 보여주는 대표적인 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Example image-text pairs in TI2V Bench. For each scenario (column), we first think of a scene that could be potentially animated to generate different types of motion. We include challenging scenarios when there are multiple objects (yellow/blue/red balloon) in the initial image for fine-grained control or the text prompt describes a new object (frisbee, bubbles) to enter the scene. Then we come up with different prompts and use the publicly available meta.ai tool to generate diverse sets of images. Images of low quality or those not in the appropriate initial state are removed.
> </details>



![](https://arxiv.org/html/2412.16153/x5.png)

> 🔼 그림 4는 제안된 TI2V Bench에서 MotiF와 9가지 오픈소스 모델 [46, 7, 25, 50, 9, 53, 28, 12, 33]의 성능을 비교한 사용자 평가 결과를 보여줍니다. MotiF는 평균 72%의 선호도를 보이며 모든 모델에 걸쳐 상당한 성능 향상을 달성했습니다. 정당화 선택을 분석한 결과, MotiF 모델은 텍스트 정렬 및 객체 동작 개선에 탁월한 성능을 보였으며, 이는 MotiF의 개발 동기와 일치합니다. 모든 비교 모델의 추론은 Brown University에서 수행되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Human evaluation results comparing MotiF to nine open-sourced models [46, 7, 25, 50, 9, 53, 28, 12, 33] on our proposed TI2V Bench. We achieved considerable improvements across the board with an average preference of 72%percent7272\%72 %. Through examining the justification choices, we found that our model mostly excel at improving text alignment and object motion, which matches very well with our motivation. Note that all the inference of prior works are done at Brown University.
> </details>



![](https://arxiv.org/html/2412.16153/x6.png)

> 🔼 본 그림은 논문의 TI2V Bench(Text-Image-to-Video Benchmark) 데이터셋을 사용하여, MotiF를 포함한 여러 기존 TI2V 모델들의 성능을 정성적으로 비교 분석한 결과를 보여줍니다. 왼쪽에서 오른쪽으로, 각 모델이 생성한 비디오의 일부 프레임들을 순차적으로 나열하여, 각 모델의 장단점과 시각적 품질을 직관적으로 비교할 수 있도록 구성되어 있습니다.  각 비디오는 동일한 이미지와 텍스트 프롬프트를 입력으로 사용하여 생성되었으며, 프레임들의 시각적 비교를 통해 각 모델이 제시하는 영상의 동작, 움직임의 자연스러움, 텍스트 및 이미지와의 일관성 등을 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Qualitative comparison to prior works on TI2V Bench. Sampled frames are ordered from left to right.
> </details>



![](https://arxiv.org/html/2412.16153/x7.png)

> 🔼 그림 6은 모션 포커스 손실(MotiF)이 고정밀도 영역의 손실을 얼마나 효과적으로 줄이는지 보여주는 손실 비교 그래프입니다.  다양한 시간 단계에서 검증 세트의 전체 평균 손실에 대한 고운동 영역의 평균 손실 비율을 계산하여 비교합니다. MotiF는 고운동 영역의 상대적 손실을 효과적으로 줄이는 것을 보여줍니다.  즉, MotiF가 정지된 배경보다는 실제로 움직이는 영역에 더 집중하여 학습함으로써 정확도 향상에 기여함을 시각적으로 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Loss comparison. We calculate the ratio of the average loss in the high motion region to the average overall loss on a hold-out validation set with different timesteps. MotiF can effectively reduce the relative loss of the high motion regions.
> </details>



![](https://arxiv.org/html/2412.16153/x8.png)

> 🔼 그림 A1은 논문에서 제시된 TI2V Bench 기준으로 기존 연구들과 MotiF의 비디오 생성 결과를 정성적으로 비교한 것입니다. MotiF는 텍스트 프롬프트와 더 잘 일치하는 비디오를 생성할 수 있음을 보여줍니다.  웹사이트에서 더 많은 비디오 샘플을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure A1: More qualitative comparison to prior works on TI2V Bench. MotiF can generate videos that align better with the text prompts. More video samples are available in the project website.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Loss | TI2V Score | Image Alignment | Text Alignment | Object Motion | Overall Quality |
|---|---|---|---|---|---| 
| w/o MotiF loss | **63.1**/36.9 | 10.3/**10.7** | **34.9**/16.4 | **32.9**/16.4 | 18.2/**20.8** |
| w/ Inv-MotiF loss | **61.9**/38.1 | 7.6/**9.2** | **34.8**/12.8 | **34.9**/15.4 | 14.3/**17.8** |{{< /table-caption >}}
> 🔼 이 표는 MotiF 모델의 설계 선택에 따른 ablation study 결과를 보여줍니다.  MotiF 모델과 기준 모델(baseline)의 성능을 비교하여 각 설계 선택이 모델 성능에 미치는 영향을 분석합니다. 표의 왼쪽 숫자는 MotiF 모델의 결과이고, 오른쪽 숫자는 기준 모델의 결과입니다.  결과적으로 MotiF는 텍스트 정렬 및 객체 모션 향상에 효과적임을 보여줍니다. 이는 이전 연구들과의 비교 결과와도 일치합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Ablation studies on different design choices. The numbers on the left is for MotiF and the right is for the baseline. Similarly to the comparisons to prior works, MotiF mostly excel in improving the text alignment and object motion.
> </details>

{{< table-caption >}}
| Image Condition | TI2V Score | Image Alignment | Text Alignment | Object Motion | Overall Quality |
|---|---|---|---|---|---| 
| cx-attn + x-cat | **58.1**/41.9 | **15.0**/14.6 | **31.5**/21.7 | **34.0**/21.6 | 18.8/**19.3** |
| cx-attn | **92.2**/7.8 | **56.8**/5.3 | **33.8**/3.8 | **41.3**/4.5 | **28.2**/5.7 |{{< /table-caption >}}
> 🔼 이 표는 이미지 조건화 기법에 대한 추가 실험 결과를 보여줍니다.  본 논문에서 제안하는 방법(x-cat)과 비교하여, cx-attn만 사용했을 때는 성능이 훨씬 저하되었고, 두 기법을 모두 사용했을 때도 최적이 아니었음을 보여줍니다.  모션 초점 손실(Motion Focal Loss)을 사용하지 않고 모델을 훈련하여 실험을 단순화했습니다.  표에는 각 방법에 대한 TI2V 점수, 이미지 정렬, 텍스트 정렬, 개체 모션, 전반적인 품질 점수가 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Ablation study on the image conditioning methods. Compared to our choice (x-cat), cx-attn alone leads to much worse results and using both is also sub-optimal. Here we train the models without motion focal loss to simplify the setting.
> </details>

{{< table-caption >}}
| Method | Image | Text |
|---|---|---|
| Baseline: static | 99.29 | 66.24 |
| Cinemo [25] | 93.28 | 66.16 |
| Cond-leak [53] | 94.05 | 66.56 |
| DynamiCrafter [46] | 93.41 | 66.58 |
| AnimateAnything [12] | 96.78 | 66.64 |
| VideoCrafter [8] | 84.45 | 66.94 |
| SEINE [9] | 91.55 | 67.22 |
| I2VGen-XL [50] | 87.13 | 67.97 |
| TI2V-Zero [28] | 73.78 | 68.89 |
| ConsistI2V [33] | 91.33 | 67.38 |
| MotiF (ours) | 92.68 | 67.73 |{{< /table-caption >}}
> 🔼 표 4는 Animate Bench 데이터셋 [51]을 사용한 자동 평가 지표를 보여줍니다. 첫 번째 행은 단순히 첫 번째 프레임을 반복하는 정지 영상 기준선을 보여주는데, 이는 이미지 정렬 점수가 가장 높고 텍스트 정렬 점수도 상당히 높은 것을 알 수 있습니다. MotiF는 기존 방법들과 비슷한 결과를 달성했습니다. 이 표는 자동화된 지표를 사용하여 MotiF 모델의 성능을 객관적으로 평가한 결과를 제시하며, 이미지 및 텍스트 정렬 측면에서 기존 방법과 유사한 수준임을 보여줍니다. 정지 영상 기준선과 비교하여 MotiF의 성능을 상대적으로 평가할 수 있도록 추가적인 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Automatic metrics on Animate Bench [51]. A simple static video baseline (repeating the first frame) can generate the best image alignment score and reasonable text alignment score (first row). MotiF achieved comparable results to prior works.
> </details>

{{< table-caption >}}
| TI2V | Image | Text | Object | Overall |
|---|---|---|---|---|
| Score ↑ | Alignment ↑ | Alignment ↑ | Motion ↑ | Quality ↑ |
| **58.8**/41.3 | 11.4/**12.1** | **34.0**/21.6 | **31.2**/22.4 | 15.0/**20.6** |{{< /table-caption >}}
> 🔼 이 표는 MotiF(Motion Focal Loss) 모델에서 사용된 모션 히트맵 생성 방법에 대한 비교 실험 결과를 보여줍니다.  MotiF 모델은 광학 흐름(optical flow)을 이용하여 모션 히트맵을 생성하는데, 본 실험에서는 SAM(Segment Anything Model)을 이용한 방법과의 성능 비교를 수행합니다. 표의 왼쪽 열은 광학 흐름 기반 MotiF의 결과를, 오른쪽 열은 SAM 기반 모션 히트맵을 사용한 결과를 보여줍니다.  각 열에는 TI2V 점수, 이미지 정렬, 텍스트 정렬, 객체 모션, 전반적인 품질 등 다섯 가지 지표에 대한 수치가 제시되어 있으며,  두 가지 방법의 성능 차이를 정량적으로 비교 분석할 수 있도록 합니다. 특히, 각 지표에 대한 수치 비교를 통해 어떤 방법이 각 지표에서 더 나은 성능을 보이는지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table A1: Ablation study comparing SAM heatmap to optical flow heatmap (MotiF). Numbers on the left are for MotiF and right for the SAM heatmap.
> </details>

{{< table-caption >}}
| λ | TI2V | Image | Text | Object | Overall |
|---|---|---|---|---|---| 
| 0.5 | **66.6**/33.4 | 10.0/**10.8** | **37.3**/13.7 | **39.8**/15.3 | 19.4/**19.7** |
| 2 | **63.8**/36.3 | **12.4**/7.6 | **33.0**/20.4 | **31.7**/21.1 | **27.5**/16.1 |
| 5 | **65.6**/34.4 | **15.2**/12.8 | **39.7**/15.9 | **36.8**/16.5 | **23.1**/17.8 |{{< /table-caption >}}
> 🔼 표 A2는 모션 초점 손실 가중치 λ에 대한 추가 실험 결과를 보여줍니다. 왼쪽 숫자는 MotiF를 사용한 결과이고, 오른쪽 숫자는 비교 대상 설정(λ 값을 변경한 설정)의 결과입니다.  각 열은 TI2V 점수, 이미지 정렬, 텍스트 정렬, 개체 움직임, 전반적인 품질을 나타내며, MotiF의 λ 값에 따른 성능 변화를 보여줍니다.  λ 값이 1일 때 가장 좋은 성능을 보이는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table A2: Ablation studies on the motion focal loss weight λ𝜆\lambdaitalic_λ. The numbers on the left is for MotiF and the right is for the comparing setting.
> </details>

{{< table-caption >}}
| Method | Subject ↑ | Background ↑ | Temporal ↑ | Motion ↑ | Dynamic ↑ | Aesthetic ↑ | Image ↑ | I2V ↑ | I2V ↑ | Camera ↑ |
|---|---|---|---|---|---|---|---|---|---|---|
| Baseline: static | 100.00 | 100.0 | 100.0 | 99.84 | 0 | 65.54 | 71.61 | 98.77 | 97.24 | 14.29 |
| DynamiCrafter | 94.70 | 97.55 | 95.17 | 97.39 | 39.51 | 60.40 | 68.16 | 96.89 | 96.68 | 30.88 |
| Cinemo | 96.80 | 99.04 | 98.67 | 98.95 | 17.32 | 59.92 | 64.37 | 97.43 | 98.14 | 15.83 |
| MotiF (ours) | 95.27 | 98.37 | 97.27 | 98.16 | 30.98 | 58.70 | 66.95 | 96.89 | 97.00 | 24.35 |{{< /table-caption >}}
> 🔼 표 A3는 VBench-I2V 벤치마크에 대한 MotiF 및 여러 기준 모델의 정량적 평가 결과를 보여줍니다. VBench-I2V는 실제 이미지와 텍스트 프롬프트로 구성된 I2V(Image-to-Video) 데이터셋이며, 카메라 동작 제어에 중점을 둡니다. 표는 일관성, 깜빡임, 부드러움, 동적 정도, 미적 품질, 이미지 품질, 주제 일관성, 배경 일관성, 카메라 동작, 전체 동작 품질 등 다양한 측면에서 MotiF와 기준 모델들을 비교 분석한 결과를 제시합니다. 정적 비디오 기준 모델은 대부분의 지표에서 MotiF보다 우수하지만, 동적 정도와 카메라 동작 측면에서는 MotiF가 더 나은 성능을 보입니다. 이는 자동 평가 지표의 한계와 전체적인 비디오 품질과 동적 요소 간의 상충 관계를 보여주는 결과입니다.
> <details>
> <summary>read the caption</summary>
> Table A3: Results on VBench-I2V.
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