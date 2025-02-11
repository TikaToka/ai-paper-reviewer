---
title: "Continuous 3D Perception Model with Persistent State"
summary: "연속적인 상태를 지닌 혁신적인 3D 인식 모델이 등장하여, 제한된 시각 정보만으로도 실시간으로 정밀한 3D 환경 재구성이 가능해졌습니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "3D Vision", "🏢 Google DeepMind",]
showSummary: true
date: 2025-01-21
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.12387 {{< /keyword >}}
{{< keyword icon="writer" >}} Qianqian Wang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-10 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.12387" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.12387" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/continuous-3d-perception-model-with" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 3D 재구성 방법들은 제한된 관측치나 불안정한 조건에서는 성능이 저하되는 문제가 있었습니다. 특히 동적인 물체나 부족한 정보로 인해 정확한 3D 모델 생성에 어려움을 겪었습니다. 이러한 문제점들을 해결하기 위해, 연구자들은 **지속적인 상태를 유지하는 순환 신경망 기반의 통합 프레임워크**를 제시했습니다.

본 논문에서는 **CUT3R이라는 새로운 모델**을 제안하여, 이미지 스트림으로부터 연속적이고 정밀한 3D 재구성을 수행합니다. **CUT3R은 각 프레임마다 카메라 매개변수와 3D 기하학적 정보를 추정**하고, 이를 통해 다양한 3D 작업을 처리할 수 있습니다. **이 모델은 정적 및 동적 장면 모두에 적용 가능**하며, 비디오와 스파스 사진 컬렉션 모두에서 입력을 처리하여, 보이지 않는 영역까지 추론하는 기능을 제공합니다. 실험 결과는 제안된 모델이 다양한 3D 작업에서 최첨단 성능 또는 경쟁력 있는 성능을 달성함을 보여줍니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 지속적인 상태를 가진 연속적인 3D 인식 모델을 통해 비디오 및 이미지로부터 실시간으로 정밀한 3D 장면을 재구성할 수 있습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 제안된 모델은 정적 및 동적 장면 모두를 처리할 수 있는 유연성을 보여주며, 다양한 3D 작업에서 최첨단 성능을 달성합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 가상 뷰를 통해 보이지 않는 장면 영역까지 추론할 수 있는 기능을 갖추어, 3D 인식의 한계를 뛰어넘는 새로운 가능성을 제시합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**본 논문은 지속적인 상태를 가진 연속적인 3D 인식 모델을 제시하여, 비디오 또는 사진 컬렉션으로부터 온라인으로 밀집된 3D 재구성을 수행하는 방법을 보여줍니다.** 이는 3D 인식 분야의 주요 연구 동향이며, 다양한 3D 작업에 적용될 수 있는 유연성을 가지고 있습니다.  **이 연구는 특히 실시간 응용 분야나, 제한된 정보만으로도 3D 환경을 효율적으로 파악해야 하는 분야에 큰 영향을 미칠 수 있습니다.**

------
#### Visual Insights



![](https://arxiv.org/html/2501.12387/x2.png)

> 🔼 본 논문의 그림 1은 시스템의 개념을 보여주는 그림입니다. RGB 이미지 스트림을 입력받아, 카메라 파라미터와 3D 기하구조를 추정하여 온라인 및 연속적으로 고밀도 3D 재구성을 수행합니다.  비디오 시퀀스 및 스패스 사진 컬렉션의 입력을 처리하고 정적 및 동적 장면 모두를 처리할 수 있는 다양한 3D 작업을 지원하는 프레임워크입니다. 각 프레임마다 3D 점 구름을 생성하여 3D 공간에 대한 점진적인 이해를 구축합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Continuous 3D Perception. Given a stream of RGB images as input, our approach enables dense 3D reconstruction in an online, continuous manner, estimating both camera parameters and dense 3D geometry with each incoming frame. Our framework supports various 3D tasks, processes inputs from video sequences and sparse photo collections, and can handle both static and dynamic scenes.
> </details>





{{< table-caption >}}
| Method | Sintel Abs Rel ↓ | Sintel δ<1.25 ↑ | Bonn Abs Rel ↓ | Bonn δ<1.25 ↑ | KITTI Abs Rel ↓ | KITTI δ<1.25 ↑ | NYU-v2 Abs Rel ↓ | NYU-v2 δ<1.25 ↑ |
|---|---|---|---|---|---|---|---|---|
| DUSt3R | 0.424 | 58.7 | 0.141 | 82.5 | 0.112 | 86.3 | 0.080 | 90.7 |
| MASt3R | 0.340 | 60.4 | 0.142 | 82.0 | 0.079 | 94.7 | 0.129 | 84.9 |
| MonST3R | 0.358 | 54.8 | 0.076 | 93.9 | 0.100 | 89.3 | 0.102 | 88.0 |
| Spann3R | 0.470 | 53.9 | 0.118 | 85.9 | 0.128 | 84.6 | 0.122 | 84.9 |
| Ours | 0.428 | 55.4 | 0.063 | 96.2 | 0.092 | 91.3 | 0.086 | 90.9 |{{< /table-caption >}}

> 🔼 표 1은 단일 프레임 깊이 추정 결과를 보여줍니다. Sintel, Bonn, KITTI 및 NYU-v2 (정적) 데이터셋에서의 성능을 절대 상대 오차(Abs Rel)와 δ < 1.25 (실제 깊이의 1.25배 이내의 예측 깊이의 비율) 지표를 사용하여 평가했습니다. 각 데이터셋에 대해 프레임별 중앙값 스케일링을 적용했습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Single-frame Depth Evaluation. We report the performance on Sintel, Bonn, KITTI, and NYU-v2 (static) datasets.
> </details>





### In-depth insights


#### Persistent State
본 논문에서 제시된 지속적 상태(Persistent State)는 **연속적인 3D 인식을 위한 핵심 구성 요소**입니다.  이는 과거 관측값으로부터 학습한 지식을 활용하여 새로운 입력 정보를 처리하고 3D 환경에 대한 내부 표현을 지속적으로 업데이트하는 역할을 합니다. 이는 단순히 현재 프레임에 대한 정보만을 사용하는 것이 아니라 **과거 정보를 통합하여 더욱 정확하고 완전한 3D 재구성**을 가능하게 합니다.  **상태의 지속성**은 동적인 장면이나 부분적인 관측값으로 인한 불확실성을 해결하는 데 중요한 역할을 하며, **일관성 있는 좌표계 내에서 3D 정보를 누적 및 통합**하여 장기간에 걸친 3D 환경의 변화를 추적할 수 있도록 합니다.  따라서 이러한 지속적 상태는 모델의 강건성과 정확성을 크게 향상시키는 요인으로 작용합니다. 특히, 제한된 관측값이나 불완전한 정보가 주어지는 상황에서도 효과적으로 3D 인식을 수행할 수 있도록 돕습니다.

#### Online 3D Recon
본 논문에서 제시된 ‘온라인 3D 재구성(Online 3D Recon)’ 방법은 **지속적인 상태(Persistent State)** 를 유지하는 순환 모델을 기반으로 합니다. 이는 **각각의 새로운 관측치(새로운 이미지 프레임)** 가 들어올 때마다 모델의 내부 상태 표현을 지속적으로 업데이트한다는 것을 의미합니다. 이러한 상태 정보는 이전의 모든 관측치 정보를 담고 있으며, **새로운 이미지 프레임으로부터 메트릭 스케일의 점군(pointmap)** 을 생성하는데 활용됩니다.  **모든 점군은 공통 좌표계 내에 존재하며**, 새로운 이미지가 추가될 때마다 이 점군들이 누적되어 **일관되고 밀집된 3D 장면 재구성** 을 가능하게 합니다. 이 모델은 실제 세상 장면에 대한 풍부한 사전 정보(prior)를 학습하므로, 단순히 이미지 관측치로부터 점군을 예측할 뿐만 아니라 **관측되지 않은 영역도 추론** 할 수 있습니다.  **비디오 시퀀스 또는 무작위 사진 모음과 같이 다양한 길이의 이미지 입력** 이 가능하도록 설계되었으며, **정적 및 동적 콘텐츠 모두 처리** 할 수 있습니다.

#### Unseen Region
논문에서 '보이지 않는 영역(Unseen Region)'에 대한 논의는 **3차원 시각 정보의 한계를 극복하고자 하는 시도**를 보여줍니다.  기존의 3차원 재구성 기법은 관측된 영역에만 집중하는 반면, 이 논문에서는 **모델 내부의 상태 표현을 활용하여 관측되지 않은 영역까지 예측**하는 방법을 제시합니다.  이는 마치 사람이 부분적으로 가려진 물체를 보고 전체 형태를 상상하는 것과 유사합니다.  **잠재적인 상태 표현(latent state representation)은 과거 관측 정보를 축적하여 새로운 관측 없이도 숨겨진 부분을 추론**할 수 있게 합니다.  **가상 카메라(virtual camera)**를 이용한 질의를 통해 모델은 3차원 공간 내의 보이지 않는 지점에 대한 정보를 생성하는데, 이는 **단순한 외삽(extrapolation)이 아닌, 학습된 사전 지식을 기반으로 한 추론**임을 의미합니다.  결과적으로, **보이지 않는 영역에 대한 예측은 모델의 일반화 능력과 3차원 공간에 대한 풍부한 이해**를 보여주는 중요한 지표가 됩니다.  **실제 환경에서의 적용성**을 높이기 위해서는, 다양한 유형의 데이터셋을 사용한 훈련과 실제 시나리오에서의 성능 평가가 필수적입니다.  이 논문의 '보이지 않는 영역'에 대한 연구는 3차원 시각 인식 기술의 새로운 가능성을 제시하며, 향후 연구 방향에 대한 시사점을 제공합니다.

#### Method Overview
본 논문의 '방법 개요' 부분은 **연속적인 3D 인식 모델의 핵심 메커니즘**을 간략하게 설명합니다.  **지속적인 상태 표현(persistent internal state)**을 중심으로, 입력 이미지 스트림을 처리하는 과정을 보여줍니다.  각 이미지는 **ViT 인코더**를 통해 토큰으로 변환되고, **상태 업데이트 및 상태 판독 메커니즘**을 통해 모델의 상태와 상호 작용합니다. **상태 업데이트**는 새로운 정보를 상태에 통합하고, **상태 판독**은 과거 정보를 활용하여 현재 시점의 3D 정보(점군, 카메라 파라미터)를 예측합니다.  **가상 뷰(virtual view)**를 통해 미관측 영역의 3D 정보를 추론하는 기능도 포함되어 있어, **실시간 밀집 점군 생성 및 카메라 위치 추정**을 가능하게 합니다.  이러한 과정을 통해 **정적 및 동적 장면 모두 처리**하고, **다양한 3D 작업**에 적용될 수 있음을 보여줍니다.

#### Future Directions
본 논문은 지속적인 상태를 가진 연속적인 3D 인식 모델을 제시하며, 비디오 또는 사진 컬렉션으로부터의 이미지 스트림을 사용하여 온라인으로 밀집된 3D 재구성을 수행합니다.  **미래 연구 방향으로는 다음과 같은 측면을 고려할 수 있습니다.** 첫째, **장기간 시퀀스에 대한 누적 오차 문제 해결**을 위한 전역 정렬 기법 도입을 통해 모델의 정확도를 더욱 향상시킬 수 있습니다.  둘째, 결정론적 접근 방식의 한계를 극복하고 고품질 3D 구조 생성을 위해 **생성 모델을 통합**하는 것을 고려해야 합니다. 셋째, **효율적인 재귀 신경망 학습 전략**을 통해 모델의 학습 시간을 단축하고 확장성을 높일 수 있는 연구가 필요합니다.  마지막으로, 본 논문의 방법론을 다양한 3D/4D 작업(예: 동적 장면 처리, 물체 중심 3D 인식)에 적용하고, 다양한 유형의 센서 데이터와의 통합을 모색하는 추가 연구가 필요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.12387/x3.png)

> 🔼 그림 2는 본 논문에서 제안하는 방법이 이미지를 이용하여 장면을 재구성하는 것 외에도, 가상 카메라 쿼리(파란색으로 표시됨)를 통해 장면의 보이지 않는 부분에 대한 구조를 추론할 수 있음을 보여줍니다.  간단히 말해,  이미지 데이터만으로 3D 모델을 만드는 과정에서 실제로는 보이지 않는 부분까지 예측할 수 있다는 것을 보여주는 그림입니다.  이러한 기능은 실제 세상의 3D 환경을 더욱 완벽하게 이해하고 모델링하는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Querying Unseen Regions. In addition to reconstructing a scene from images, our method can also infer structure for unseen parts of the scene, given a virtual camera query (shown in blue).
> </details>



![](https://arxiv.org/html/2501.12387/x4.png)

> 🔼 이 그림은 논문의 방법론 섹션에 속하며, 지속적인 상태를 사용하여 이미지 스트림(비디오 프레임 또는 사진 모음)으로부터 실시간으로 밀집된 3D 재구성을 수행하는 방법을 보여줍니다. 각 입력 이미지는 공유 가중치를 가진 ViT 인코더를 통해 시각 토큰으로 인코딩되고, 이 토큰들은 상태 토큰과 상호 작용합니다. 상태 업데이트는 현재 이미지를 상태에 통합하고, 상태 판독은 예측을 위해 상태에 저장된 과거 컨텍스트를 검색합니다. 두 프로세스는 두 개의 상호 연결된 ViT 디코더를 통해 동시에 발생합니다. 출력에는 월드 프레임과 카메라 프레임의 포인트맵(월드 포인트맵만 표시됨)과 카메라에서 월드로의 변환이 포함됩니다. 오른쪽에는 쿼리 카메라(레이맵으로 표현)가 주어지면, 관찰되지 않은 영역의 포인트맵까지 예측하기 위해 상태로부터 정보를 읽는 방법을 보여줍니다. 상태 판독 시에는 상태가 업데이트되지 않습니다.  환각된 포인트맵은 파란색 테두리로 강조 표시됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Method Overview. Our method performs online dense 3D reconstruction from a stream of images (video frames or a photo collection) by using a persistent state. Each input image is encoded into visual tokens via a shared-weight ViT encoder. These tokens interact with state tokens, where state update integrates the current image into the state, and state readout retrieves the past context stored in the state for predictions. Both processes occur simultaneously through two interconnected ViT decoders. Outputs include pointmaps in world and camera frames (only world pointmaps are shown) and the camera-to-world transformation. On the right, we demonstrate our method’s ability to predict unseen views: given a query camera (as a raymap), it reads information from the state to predict its corresponding pointmap, even for unobserved regions. For these readouts, we do not update the state. The hallucinated pointmap is highlighted with a blue border.
> </details>



![](https://arxiv.org/html/2501.12387/x5.png)

> 🔼 그림 4는 실제 인터넷 비디오에 대한 정성적 결과를 보여줍니다. 이 그림에서는 제안된 방법을 Spann3R[101]과 MonST3R[125]과 비교하여, 제안된 방법이 가장 우수한 정성적 결과를 얻었다는 점을 보여줍니다.  제안된 방법은 동적인 장면에서도 견고하며, 비디오의 다양한 특성에도 잘 적응합니다.  비디오의 프레임이 부분적으로 가려져 있거나, 움직임이 많거나, 광원이 불규칙한 등 어려운 조건에서도, 제안된 방법은 보다 정확하고 일관된 3D 재구성 결과를 보여줍니다.  특히, Spann3R은 정적 장면에 최적화되어 동적 장면에서 성능이 떨어지는 반면, MonST3R은 동적 장면에 대해서는 우수하지만 정적 장면에서는 성능이 다소 저하됩니다.  제안된 방법은 이러한 두 가지 방법의 장점을 결합하여 다양한 장면에서 우수한 성능을 보입니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Qualitative Results on In-the-wild Internet Videos. We compare our method with concurrent works Spann3R [101] and MonST3R [125]. Our method achieves the best qualitative results.
> </details>



![](https://arxiv.org/html/2501.12387/x6.png)

> 🔼 그림 5는 모델의 상태 업데이트 메커니즘을 보여줍니다.  '온라인' 방식은 입력 이미지가 들어올 때마다 상태를 순차적으로 업데이트하는 반면, '재방문' 방식은 모든 이미지를 처리한 후 최종 상태를 이용하여 다시 한번 재구성을 수행합니다.  재방문 방식은 전체적인 맥락을 고려하여 더 나은 재구성 결과를 얻을 수 있으며, 특히 강조된 영역에서 그 효과가 두드러집니다.  이는 모델이 과거 정보를 활용하여 현재 관측값을 더욱 효과적으로 처리함을 보여주는 실험 결과입니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: State Update Analysis. Compared to online, revisiting incorporates global context which improves overall reconstruction results, especially in the highlighted regions.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Alignment | Method | Optim. | Onl. | Sintel Abs Rel ↓ | Sintel δ<1.25↑ | BONN Abs Rel ↓ | BONN δ<1.25↑ | KITTI Abs Rel ↓ | KITTI δ<1.25↑ | FPS |
|---|---|---|---|---|---|---|---|---|---|---|
| Per-sequence scale | DUSt3R-GA [107] | ✓ |  | 0.656 | 45.2 | 0.155 | 83.3 | 0.144 | 81.3 | 0.76 |
|  | MASt3R-GA [51] | ✓ |  | 0.641 | 43.9 | 0.252 | 70.1 | 0.183 | 74.5 | 0.31 |
|  | MonST3R-GA [125] | ✓ |  | 0.378 | 55.8 | 0.067 | 96.3 | 0.168 | 74.4 | 0.35 |
|  | Spann3R [101] |  | ✓ | 0.622 | 42.6 | 0.144 | 81.3 | 0.198 | 73.7 | 13.55 |
|  | Ours |  | ✓ | 0.421 | 47.9 | 0.078 | 93.7 | 0.118 | 88.1 | 16.58 |
| Metric scale | MASt3R-GA [51] | ✓ |  | 1.022 | 14.3 | 0.272 | 70.6 | 0.467 | 15.2 | 0.31 |
|  | Ours |  | ✓ | 1.029 | 23.8 | 0.103 | 88.5 | 0.122 | 85.5 | 16.58 |{{< /table-caption >}}
> 🔼 표 2는 Sintel, Bonn, KITTI 데이터셋에서 스케일 불변 심도 및 계량 심도 정확도를 보여줍니다. 전역 정렬이 필요한 방법은 'GA'로 표시되며, 'Optim.'과 'Onl.'은 각각 최적화 기반 방법과 온라인 방법을 나타냅니다. 또한, A100 GPU에서 모든 방법에 대해 512x144 이미지 해상도를 사용하여 KITTI 데이터셋의 FPS도 보고합니다. 단, Spann3R은 224x224 입력만 지원합니다. 본 표에는 일부 기준선만 제시되어 있으며, 전체 비교는 보충 자료를 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Table 2:  Video Depth Evaluation. We report scale-invariant depth and metric depth accuracy on Sintel, Bonn, and KITTI datasets. Methods requiring global alignment are marked “GA”, while “Optim.” and “Onl.” indicate optimization-based and online methods, respectively. We also report the FPS on KITTI dataset using 512×\times× 144 image resolution for all methods on an A100 GPU, except Spann3R which only supports 224×\times×224 inputs. We present a subset of baselines here; please refer to the supplementary material for full comparisons.
> </details>

{{< table-caption >}}
| Method | Optim. | Onl. | Sintel ATE ↓ | Sintel RPE trans ↓ | Sintel RPE rot ↓ | TUM-dynamics ATE ↓ | TUM-dynamics RPE trans ↓ | TUM-dynamics RPE rot ↓ | ScanNet ATE ↓ | ScanNet RPE trans ↓ | ScanNet RPE rot ↓ |
|---|---|---|---|---|---|---|---|---|---|---|---| 
| Particle-SfM [129] | ✓ |  | 0.129 | 0.031 | 0.535 | - | - | - | 0.136 | 0.023 | 0.836 |
| Robust-CVD [47] | ✓ |  | 0.360 | 0.154 | 3.443 | 0.153 | 0.026 | 3.528 | 0.227 | 0.064 | 7.374 |
| CasualSAM [128] | ✓ |  | 0.141 | 0.035 | 0.615 | 0.071 | 0.010 | 1.712 | 0.158 | 0.034 | 1.618 |
| DUSt3R-GA [107] | ✓ |  | 0.417 | 0.250 | 5.796 | 0.083 | 0.017 | 3.567 | 0.081 | 0.028 | 0.784 |
| MASt3R-GA [51] | ✓ |  | 0.185 | 0.060 | 1.496 | 0.038 | 0.012 | 0.448 | 0.078 | 0.020 | 0.475 |
| MonST3R-GA [125] | ✓ |  | 0.111 | 0.044 | 0.869 | 0.098 | 0.019 | 0.935 | 0.077 | 0.018 | 0.529 |
| DUSt3R [107] |  | ✓ | 0.290 | 0.132 | 7.869 | 0.140 | 0.106 | 3.286 | 0.246 | 0.108 | 8.210 |
| Spann3R [101] |  | ✓ | 0.329 | 0.110 | 4.471 | 0.056 | 0.021 | 0.591 | 0.096 | 0.023 | 0.661 |
| Ours |  | ✓ | 0.213 | 0.066 | 0.621 | 0.046 | 0.015 | 0.473 | 0.099 | 0.022 | 0.600 |{{< /table-caption >}}
> 🔼 표 3은 Sintel [12], TUM-dynamic [89], ScanNet [19] 데이터셋에서 카메라 자세 추정 성능을 평가한 결과를 보여줍니다.  각 데이터셋은 다양한 동적 및 정적 환경을 포함하고 있으며, 이는 다양한 어려움을 제시합니다.  표에는 각 방법의 절대 위치 오차(ATE), 상대적 위치 오차(RPE trans), 상대적 회전 오차(RPE rot)가 나타나 있습니다.  'Optim.' 열은 최적화 기반 방법을, 'Onl.' 열은 온라인 방법을 나타냅니다.  본 논문의 방법은 모든 온라인 방법 중에서 가장 우수한 전반적인 성능을 달성했습니다.  특히 동적 장면 처리 능력이 뛰어나며, 이는 지속적인 상태 업데이트 메커니즘 덕분입니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Evaluation on Camera Pose Estimation on Sintel [12], TUM-dynamic [89], and ScanNet [19] datasets. Our method achieves the best overall performance among all online methods.
> </details>

{{< table-caption >}}
| Method | Optim. | Onl. | 7 scenes Acc ↓ Mean | 7 scenes Acc ↓ Med. | 7 scenes Comp ↓ Mean | 7 scenes Comp ↓ Med. | NRGBD Acc ↓ Mean | NRGBD Acc ↓ Med. | NRGBD Comp ↓ Mean | NRGBD Comp ↓ Med. | FPS |
|---|---|---|---|---|---|---|---|---|---|---|---| 
| DUSt3R-GA [107] | ✓ |  | 0.146 | 0.077 | 0.181 | 0.067 | 0.736 | 0.839 | 0.144 | 0.019 | 0.68 |
| MASt3R-GA [51] | ✓ |  | 0.185 | 0.081 | 0.180 | 0.069 | 0.701 | 0.792 | 0.085 | 0.033 | 0.34 |
| MonST3R-GA [51] | ✓ |  | 0.248 | 0.185 | 0.266 | 0.167 | 0.672 | 0.759 | 0.272 | 0.114 | 0.39 |
| Spann3R [101] |  | ✓ | 0.298 | 0.226 | 0.205 | 0.112 | 0.650 | 0.730 | 0.416 | 0.323 | 12.97 |
| Ours |  | ✓ | 0.126 | 0.047 | 0.154 | 0.031 | 0.727 | 0.834 | 0.099 | 0.031 | 17.00 |{{< /table-caption >}}
> 🔼 표 4는 제안된 방법의 3D 재구성 성능을 7-Scenes 및 NRGBD 데이터셋에서 평가한 결과를 보여줍니다.  온라인으로 동작하는 본 연구의 방법은 전역 정렬을 사용하는 오프라인 방법들과 비교하여 경쟁력 있는 성능을 달성하며, 경우에 따라서는 능가하는 성능을 보입니다.  정량적인 비교를 통해 제안된 방법의 효율성과 정확성을 확인할 수 있습니다.  Acc(정확도), Comp(완성도), NC(일관성) 세 가지 지표를 사용하여 평가하였습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: 3D reconstruction comparison on 7-Scenes [83] and NRGBD [4] datasets. While operating online, our method achieves competitive performance, on par with and even surpassing offline methods that employ global alignment.
> </details>

{{< table-caption >}}
| Method | 7-Scenes Acc↓ | 7-Scenes Comp↓ | 7-Scenes NC↑ | NRGBD Acc↓ | NRGBD Comp↓ | NRGBD NC↑ |
|---|---|---|---|---|---|---|
| DUSt3R-GA [107] | 0.146 | 0.181 | **0.736** | 0.144 | 0.154 | **0.870** |
| Ours | **0.126** | **0.154** | 0.727 | **0.099** | **0.076** | 0.837 |
| Ours Revisit | **0.113** | **0.107** | **0.732** | **0.094** | **0.076** | **0.844** |{{< /table-caption >}}
> 🔼 표 5는 지속적으로 업데이트되는 상태 표현의 효과를 보여줍니다. 7-Scenes 및 NRGBD 데이터셋에서 온라인 및 재방문(revisiting) 방식으로 모델을 학습시킨 결과를 비교하여, 재방문 방식이 전체적인 재구성 결과를 향상시키는 것을 보여줍니다. 재방문 방식은 모델이 모든 이미지를 본 후 최종 상태를 고정하고 동일한 이미지 세트를 다시 처리하여 예측을 생성하는 방식입니다. 이를 통해 모델이 장면에 대한 완전한 맥락을 활용할 수 있게 되어 정확도가 향상됩니다. 이 표는 4.4절 분석 부분에 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: State Update Analysis on 7-Scenes [83] and NRGBD [4] datasets.
> </details>

{{< table-caption >}}
| Dataset Name | Scene Type | Metric? | Real? | Dynamic? | Camera only? | Single View? |
|---|---|---|---|---|---|---|
| ARKitScenes [5] | Indoor | Yes | Real | Static | No | No |
| ARKitScenes-HighRes [5] | Indoor | Yes | Real | Static | No | No |
| ScanNet [19] | Indoor | Yes | Real | Static | No | No |
| ScanNet++ [121] | Indoor | Yes | Real | Static | No | No |
| TartanAir [108] | Mixed | Yes | Synthetic | Dynamic | No | No |
| Waymo [93] | Outdoor | Yes | Real | Dynamic | No | No |
| MapFree [3] | Outdoor | Yes | Real | Static | No | No |
| BlendedMVS [120] | Mixed | No | Synthetic | Static | No | No |
| HyperSim [75] | Indoor | Yes | Synthetic | Static | No | No |
| MegaDepth [53] | Outdoor | No | Real | Static | No | No |
| Unreal4K [99] | Mixed | Yes | Synthetic | Static | No | No |
| DL3DV [55] | Mixed | No | Real | Static | No | No |
| CO3Dv2 [74] | Object-Centric | No | Real | Static | No | No |
| WildRGBD [115] | Object-Centric | Yes | Real | Static | No | No |
| VirtualKITTI2 [13] | Outdoor | Yes | Synthetic | Dynamic | No | No |
| Matterport3D [15] | Indoor | Yes | Real | Static | No | No |
| BEDLAM [9] | Mixed | Yes | Synthetic | Dynamic | No | No |
| Dynamic Replica [43] | Indoor | Yes | Synthetic | Dynamic | No | No |
| PointOdyssey [130] | Mixed | Yes | Synthetic | Dynamic | No | No |
| Spring [60] | Mixed | Yes | Synthetic | Dynamic | No | No |
| MVS-Synth [40] | Outdoor | Yes | Synthetic | Dynamic | No | No |
| UASOL [6] | Outdoor | Yes | Real | Static | No | No |
| OmniObject3D [114] | Object-Centric | Yes | Synthetic | Static | No | No |
| RealEstate10K [131] | Indoor | No | Real | Static | Yes | No |
| MVImgNet [123] | Object-Centric | No | Real | Static | Yes | No |
| CoP3D [84] | Object-Centric | No | Real | Dynamic | Yes | No |
| EDEN [50] | Outdoor | Yes | Synthetic | Static | No | Yes |
| IRS [105] | Indoor | Yes | Synthetic | Static | No | Yes |
| Synscapes [111] | Outdoor | Yes | Synthetic | Dynamic | No | Yes |
| 3D Ken Burns [67] | Mixed | No | Synthetic | Static | No | Yes |
| SmartPortraits [48] | Indoor | Yes | Real | Dynamic | No | Yes |
| UrbanSyn [32] | Outdoor | Yes | Synthetic | Dynamic | No | Yes |
| HOI4D [57] | Indoor | Yes | Real | Dynamic | No | Yes |{{< /table-caption >}}
> 🔼 표 6은 논문에서 사용된 32개의 데이터셋에 대한 상세 정보를 제공합니다. 각 데이터셋의 장면 유형(실내, 실외, 혼합), 측정값 유무, 실제 데이터 여부, 동적 개체 포함 여부, 카메라 매개변수만 제공 여부, 단일 뷰 데이터셋 여부 등을 보여줍니다.  '동적'으로 분류된 데이터셋은 사람과 같은 움직이는 개체에 대한 주석이 있는 데이터셋을 의미하며, '카메라 전용'은 카메라의 내부 및 외부 매개변수만 제공하는 데이터셋을, '단일 뷰'는 단일 뷰에 대한 깊이 정보와 내부 매개변수만 제공하는 데이터셋을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Training Datasets. We provide more details of our training datasets. We classify a dataset as dynamic if annotations exist for moving objects like humans. If there is only camera parameters (intrinsics and extrinsics) available, we mark them as “camera only”. If the dataset only contains depth and intrinsics for single views, we mark them as “single view”.
> </details>

{{< table-caption >}}
Dataset | Alignment
---|---|---|---|---|---|---|---|---
Sintel |  |  |  | Abs Rel ↓ | δ<1.25 ↑ | Abs Rel ↓ | δ<1.25 ↑ | Abs Rel ↓ | δ<1.25 ↑ | FPS
---|---|---|---|---|---|---|---|---|---|---
Per-sequence scale & shift | Marigold [44] |  | ✓ | 0.532 | 51.5 | 0.091 | 93.1 | 0.149 | 79.6 | &lt;0.1
Depth-Anything-V2 [117] |  | ✓ | 0.367 | 55.4 | 0.106 | 92.1 | 0.140 | 80.4 | 3.13
NVDS [109] |  | ✓ | 0.408 | 48.3 | 0.167 | 76.6 | 0.253 | 58.8 | -
ChronoDepth [82] |  | ✓ | 0.687 | 48.6 | 0.100 | 91.1 | 0.167 | 75.9 | 1.89
DepthCrafter [39] |  | ✓ | **0.292** | **69.7** | 0.075 | **97.1** | **0.110** | **88.1** | 0.97
Robust-CVD [47] |  | ✓ | 0.703 | 47.8 | - | - | - | - | -
CasualSAM [128] | ✓ |  | 0.387 | 54.7 | 0.169 | 73.7 | 0.246 | 62.2 | -
DUSt3R-GA [107] | ✓ |  | 0.531 | 51.2 | 0.156 | 83.1 | 0.135 | 81.8 | 0.76
MASt3R-GA [51] | ✓ |  | **0.327** | **59.4** | 0.167 | 78.5 | 0.137 | 83.6 | 0.31
MonST3R-GA [125] | ✓ |  | 0.333 | 59.0 | **0.066** | **96.4** | 0.157 | 73.8 | 0.35
Spann3R [101] |  | ✓ | 0.508 | 50.8 | 0.157 | 82.1 | 0.207 | 73.0 | 13.55
Ours |  | ✓ | 0.454 | 55.7 | **0.074** | 94.5 | **0.106** | **88.7** | 16.58
Per-sequence scale | DUSt3R-GA [107] | ✓ |  | 0.656 | 45.2 | 0.155 | 83.3 | **0.144** | **81.3** | 0.76
MASt3R-GA [51] | ✓ |  | 0.641 | 43.9 | 0.252 | 70.1 | 0.183 | 74.5 | 0.31
MonST3R-GA [125] | ✓ |  | **0.378** | **55.8** | **0.067** | **96.3** | 0.168 | 74.4 | 0.35
Spann3R [101] |  | ✓ | 0.622 | 42.6 | 0.144 | 81.3 | 0.198 | 73.7 | 13.55
Ours |  | ✓ | **0.421** | **47.9** | **0.078** | **93.7** | **0.118** | **88.1** | 16.58
Metric scale | MASt3R-GA [51] | ✓ |  | **1.022** | 14.3 | 0.272 | 70.6 | 0.467 | 15.2 | 0.31
Ours |  | ✓ | 1.029 | **23.8** | **0.103** | **88.5** | **0.122** | **85.5** | 16.58{{< /table-caption >}}
> 🔼 표 7은 Sintel, Bonn, KITTI 데이터셋에서 scale&shift-invariant depth, scale-invariant depth, metric depth 정확도를 비교 분석한 결과를 보여줍니다.  전체 프레임에 대한 평균값과 중앙값을 제시하며, 각 방법의 속도(FPS)도 KITTI 데이터셋 기준으로 측정하여 제시합니다.  전통적인 방식처럼 전역 정합(global alignment)이 필요한 방법과, 그렇지 않은 방법(optimization-based, online)을 구분하여 표시하고 있습니다. Spann3R은 224x224 해상도의 이미지만 처리 가능한 반면, 다른 방법들은 512x144 해상도의 이미지를 사용하여 비교 분석하였습니다.
> <details>
> <summary>read the caption</summary>
> Table 7:  Video Depth Evaluation. We report scale&shift-invariant depth, scale-invariant depth and metric depth accuracy on Sintel, Bonn, and KITTI datasets. Methods requiring global alignment are marked “GA”, while “Optim.” and “Onl.” indicate optimization-based and online methods, respectively. We also report the FPS on KITTI dataset using 512×\times× 144 image resolution for all methods, except Spann3R which only supports 224×\times×224 inputs.
> </details>

{{< table-caption >}}
| Method | Optim. | Onl. | Sintel ATE ↓ | Sintel RPE trans ↓ | Sintel RPE rot ↓ | TUM-dynamics ATE ↓ | TUM-dynamics RPE trans ↓ | TUM-dynamics RPE rot ↓ | ScanNet ATE ↓ | ScanNet RPE trans ↓ | ScanNet RPE rot ↓ |
|---|---|---|---|---|---|---|---|---|---|---|---| 
| DROID-SLAM [96] |  | ✓ | 0.175 | 0.084 | 1.912 | - | - | - | - | - | - |
| DPVO [97] |  | ✓ | 0.115 | 0.072 | 1.975 | - | - | - | - | - | - |
| LEAP-VO [17] |  | ✓ | 0.089 | 0.066 | 1.250 | 0.068 | 0.008 | 1.686 | 0.070 | 0.018 | 0.535 |
| Particle-SfM [129] | ✓ |  | 0.129 | 0.031 | 0.535 | - | - | - | 0.136 | 0.023 | 0.836 |
| Robust-CVD [47] | ✓ |  | 0.360 | 0.154 | 3.443 | 0.153 | 0.026 | 3.528 | 0.227 | 0.064 | 7.374 |
| CasualSAM [128] | ✓ |  | 0.141 | 0.035 | 0.615 | 0.071 | 0.010 | 1.712 | 0.158 | 0.034 | 1.618 |
| DUSt3R-GA [107] | ✓ |  | 0.417 | 0.250 | 5.796 | 0.083 | 0.017 | 3.567 | 0.081 | 0.028 | 0.784 |
| MASt3R-GA [51] | ✓ |  | 0.185 | 0.060 | 1.496 | 0.038 | 0.012 | 0.448 | 0.078 | 0.020 | 0.475 |
| MonST3R-GA [125] | ✓ |  | 0.111 | 0.044 | 0.869 | 0.098 | 0.019 | 0.935 | 0.077 | 0.018 | 0.529 |
| DUSt3R [107] |  | ✓ | 0.290 | 0.132 | 7.869 | 0.140 | 0.106 | 3.286 | 0.246 | 0.108 | 8.210 |
| Spann3R [101] |  | ✓ | 0.329 | 0.110 | 4.471 | 0.056 | 0.021 | 0.591 | 0.096 | 0.023 | 0.661 |
| Ours |  | ✓ | 0.213 | 0.066 | 0.621 | 0.046 | 0.015 | 0.473 | 0.099 | 0.022 | 0.600 |{{< /table-caption >}}
> 🔼 표 8은 Sintel, TUM-dynamic, ScanNet 데이터셋에서 카메라 자세 추정 성능을 평가한 결과를 보여줍니다.  이 표는 단일 프레임 깊이 추정과 비디오 깊이 추정 모두에 대한 결과를 포함하고 있습니다.  특히,  세 가지 방법(DROID-SLAM, DPVO, LEAP-VO)은 접근 방식이 다르기 때문에 기준 카메라 내부 매개변수가 필요하다는 점에 유의해야 합니다.  나머지 방법들은 이러한 기준 매개변수 없이도 성능을 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Evaluation on Camera Pose Estimation on Sintel [12], TUM-dynamic [89], and ScanNet [19] datasets. Note that unlike the the rest of the methods, the three methods in the first section require ground truth camera intrinsics as input.
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