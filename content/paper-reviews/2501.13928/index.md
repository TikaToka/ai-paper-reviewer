---
title: "Fast3R: Towards 3D Reconstruction of 1000+ Images in One Forward Pass"
summary: "Fast3R: 단일 전방 패스로 1000개 이상의 이미지를 사용한 3D 재구성을 가능하게 하는 혁신적인 방법"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "3D Vision", "🏢 University of Michigan",]
showSummary: true
date: 2025-01-23
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.13928 {{< /keyword >}}
{{< keyword icon="writer" >}} Jianing Yang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-23 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.13928" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.13928" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/fast3r-towards-3d-reconstruction-of-1000" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 3D 재구성 방법들은 여러 이미지들을 쌍으로 처리하고 전역 정렬 과정을 거쳐야 하기 때문에 많은 계산 비용과 시간이 소요되고 확장성이 떨어지는 문제점이 있습니다. 특히, DUSt3R과 같은 최신 방법들도 두 개의 이미지만 처리할 수 있다는 한계를 가지고 있습니다. 

본 논문에서는 이러한 문제점을 해결하기 위해 Fast3R이라는 새로운 멀티뷰 3D 재구성 기법을 제시합니다. Fast3R은 Transformer 기반 아키텍처를 활용하여 여러 이미지들을 병렬로 처리함으로써, **반복적인 정렬 과정 없이 단일 전방 패스에서 N개의 이미지를 처리**할 수 있습니다. 이를 통해 **기존 방법들에 비해 속도와 정확도를 크게 향상**시키고, **확장성 문제도 효과적으로 해결**합니다. 실험 결과, Fast3R은 기존 최고 성능 기법들에 비해 상당한 성능 향상을 보였으며, 특히 추론 속도 측면에서 매우 큰 향상을 보였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 단일 전방 패스를 통해 1000개 이상의 비정렬 이미지에서 3D 재구성을 효율적으로 수행 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 기존의 쌍방향 접근 방식보다 속도와 정확도가 크게 향상됨 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} Transformer 기반 아키텍처를 사용하여 확장성과 강력한 성능을 구현 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **다양한 관점에서 정확하고 확장 가능한 표현을 필요로 하는 응용 분야**에 중요한 영향을 미칩니다. **단일 전방 패스에서 1000개 이상의 이미지를 처리**하여 기존 방법의 속도와 확장성 한계를 극복하는 새로운 가능성을 제시합니다. 또한, **정확도를 저하시키지 않고 효율성을 높이는 새로운 방법론**을 제시함으로써, 향후 연구에 대한 새로운 방향을 제시하며 컴퓨터 비전 분야 발전에 기여할 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.13928/x2.png)

> 🔼 이 그림은 Fast3R이라는 새로운 3D 재구성 방법을 보여줍니다. Fast3R은 1,000개 이상의 무질서하고 자세가 정해지지 않은 이미지들을 단일 전방 패스(single forward pass)로 처리하여 3D 모델을 생성합니다.  기존의 쌍방향(pairwise) 접근 방식과 달리, Fast3R은 모든 이미지를 동시에 처리하여 계산 효율성을 높이고 정확도를 향상시킵니다. 그림에서는 입력 이미지들, Fast3R의 처리 과정, 그리고 생성된 3D 모델과 카메라 위치를 보여줍니다. 이는 Fast3R의 핵심적인 특징과 성능을 한눈에 보여주는 시각적 설명입니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Fast3R is a method towards 3D reconstructing 1000+ unordered, unposed images in a single forward pass.
> </details>





{{< table-caption >}}
| Methods | Co3Dv2 [39] | RRA@15 ↑ | RRA@5 ↑ | RTA@15 ↑ | RTA@5 ↑ | mAA(30) ↑ | FPS |
|---|---|---|---|---|---|---|---| 
| Colmap+SG [9, 41] | 36.1 | 24.4 | 27.3 | 17.2 | 25.3 | 0.056 |
| PixSfM [28] | 33.7 | 26.1 | 32.9 | 17.6 | 30.1 | - |
| RelPose [70] | 57.1 | - | - | - | - | 0.02 |
| PosReg [59] | 53.2 | - | 49.1 | - | 45.0 | 0.015 |
| PoseDiff [59] | 80.5 | 59.5 | 79.8 | 61.7 | 66.5 | 0.015 |
| RelPose++ [27] | (85.5) | - | - | - | - | 0.02 |
| DUSt3R [60] | 96.2 | - | 86.8 | - | 76.7 | 0.78 |
| MASt3R [24] | 94.6 | 93.2 | 91.9 | 86.2 | 81.8 | 0.23 |
| **Fast3R (Ours)** | **99.7** | **97.4** | 87.1 | 76.1 | **82.5** | **251.1** |{{< /table-caption >}}

> 🔼 표 1은 CO3Dv2 데이터셋에서 무작위로 선택한 10개의 프레임을 사용하여 다양한 방법으로 수행된 다중 뷰 포즈 회귀 분석 결과를 보여줍니다. 괄호 안의 수치는 10개의 뷰가 아닌 8개의 뷰에 대한 결과를 나타내며, 비교를 위해 최고 성능을 기록한 결과를 제시합니다. Fast3R은 카메라 내부 매개변수를 알고 있다고 가정하지 않습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Multi-view pose regression on the CO3Dv2 [39] dataset with 10 random frames. Parentheses denote methods that do not report results on the 10 views set; we report their best for comparison (8 views). Fast3R does not assume known camera intrinsics.
> </details>





### In-depth insights


#### Multi-view 3D ReCon
다시 말해, **다시점 3D 재구성(Multi-view 3D Reconstruction)**은 여러 각도에서 촬영된 이미지들을 사용하여 3차원 모델을 만드는 기술입니다. 이는 자율주행, 증강현실, 로보틱스 등 다양한 분야에서 중요한 역할을 합니다. 기존의 방법들은 이미지 쌍을 처리하는 쌍방향 접근 방식을 사용하여 계산 비용이 많이 들고 확장성이 떨어집니다. 본 논문에서는 이러한 한계를 극복하기 위해 **단일 전방 패스(single forward pass) 내에서 여러 이미지를 병렬 처리하는 새로운 방법**을 제안합니다. 이를 통해 계산 효율성과 확장성을 크게 향상시키면서 정확도를 유지할 수 있습니다. **트랜스포머 기반 아키텍처**를 활용하여 이미지들을 동시에 처리하며, 반복적인 정렬 과정이 필요하지 않습니다. 이는 추론 속도를 높이고 오류 누적을 줄이는 데 기여합니다. 실험 결과는 제안된 방법이 최첨단 성능을 달성함을 보여주며, **다시점 애플리케이션에 대한 강력한 대안**임을 입증합니다. 특히 대규모 이미지 처리에 대한 확장성이 뛰어나 실시간 응용 분야에도 적용 가능성이 높습니다.

#### Transformer-based Arch
본 논문에서 제안하는 "Transformer 기반 아키텍처"는 다수의 이미지를 동시에 처리하여 효율적인 3D 재구성을 가능하게 하는 핵심 요소입니다. **기존의 쌍방향 접근 방식과 달리, Transformer는 여러 이미지 간의 관계를 병렬적으로 학습하여 시간 및 메모리 효율성을 크게 높입니다.**  이는 특히 많은 이미지를 처리해야 하는 대규모 3D 재구성 작업에서 매우 중요한 장점입니다.  **Transformer의 장점은 모든 입력 이미지들을 동시에 처리하여 정보 손실을 최소화하고 정확도를 높이는 것**입니다.  기존 방식처럼 순차적으로 이미지를 처리하는 경우, 전 단계의 오류가 누적되어 최종 결과의 정확도가 떨어질 수 있지만, Transformer 기반 아키텍처는 이러한 문제를 해결합니다.  **본 논문의 핵심 성과 중 하나는 Transformer를 통해 N개의 이미지를 단일 전달 단계에서 처리하는 것**으로, 반복적인 정렬 과정 없이 효율적이고 확장 가능한 3D 재구성을 가능하게 합니다.  이러한 아키텍처는 **향상된 확장성과 속도를 제공하며, 대규모 데이터셋을 효과적으로 처리할 수 있는 강력한 도구**임을 보여줍니다.  **Transformer의 다중 이미지 처리 능력은 Fast3R의 핵심 경쟁력**으로, 기존 방법 대비 속도와 정확도 측면에서 상당한 개선을 가져옵니다.

#### Scalability and Speed
본 논문에서 제시된 Fast3R 모델은 **기존의 쌍방향 접근 방식과 달리 여러 이미지를 동시에 처리하여 3D 재구성의 확장성과 속도를 크게 향상**시켰습니다.  Transformer 기반 아키텍처를 통해 반복적인 정렬 과정 없이 N개의 이미지를 단일 전달 패스로 처리함으로써 계산 비용을 절감하고 효율성을 높였습니다.  **다수의 이미지를 병렬적으로 처리**하는 Fast3R의 구조는 **속도 향상**에 크게 기여하며,  **이미지 수가 증가함에 따라 성능이 저하되지 않고 오히려 향상**되는 점을 실험적으로 증명하였습니다.  결과적으로 Fast3R은 대규모 이미지 데이터셋을 활용한 3D 재구성 작업에서 **뛰어난 확장성과 속도를 보장**하며 기존 방법론의 한계를 극복하는 실용적인 대안을 제시합니다.  **특히, 추론 속도가 기존 방법 대비 획기적으로 향상**되어 실시간 응용 분야에 적합합니다.

#### Pointmap Regression
포인트맵 회귀는 다수의 이미지에서 3D 구조를 직접 예측하는 혁신적인 방법입니다. 기존의 파이프라인 방식과 달리, **이미지 쌍 간의 대응 관계를 찾고 삼각측량을 수행하는 대신, 신경망이 여러 이미지에서 곧바로 3D 점들의 집합인 포인트맵을 예측**합니다. 이는 파이프라인의 오류 누적 문제를 줄이고, 계산 효율성을 높일 수 있습니다.  **DUSt3R과 같은 선구적인 연구**에서 이 접근법이 제시되었으며, Fast3R은 이를 여러 이미지에 확장한 사례입니다.  하지만, **포인트맵 회귀는 이미지의 순서에 대한 가정 없이 동작**하므로, 이미지 순서에 의존하는 기존 기법보다 확장성이 뛰어납니다.  **Fast3R의 성능 향상에 중요한 역할**을 하지만, 정확도와 계산 비용 간의 균형을 맞추는 것이 중요한 과제입니다.  **정확한 포인트맵을 생성하기 위한 모델의 학습 및 설계**가 중요하며, 특히 다양한 뷰포인트와 복잡한 장면을 처리할 수 있도록 충분한 데이터로 학습해야 합니다.  **실시간 응용 분야를 위해서는 연산 속도** 또한 중요하게 고려되어야 합니다.

#### Future Enhancements
본 논문의 Fast3R 모델은 다수의 이미지를 단일 전방 패스로 처리하여 3D 재구성을 수행하는 효율적인 방법을 제시하지만, 향후 개선을 위한 여러 가지 방향이 있습니다.  **첫째, 더욱 큰 규모의 데이터셋을 사용하여 모델의 성능을 향상시킬 수 있습니다.** 현재 사용된 데이터셋은 모델의 잠재력을 완전히 보여주지 못할 수 있습니다.  **둘째, 메모리 효율성을 더욱 개선하여 더 많은 이미지를 처리할 수 있도록 하는 연구가 필요합니다.** 현재 모델은 많은 이미지를 처리할 때 메모리 제한에 직면할 수 있습니다.  **셋째, 모델의 일반화 능력을 높이기 위한 연구가 필요합니다.**  다양한 조건에서 촬영된 이미지에 대해서도 안정적인 성능을 보이도록 모델을 개선해야 합니다. **넷째, 동적 환경에서의 3D 재구성 성능을 향상시키는 연구가 필요합니다.**  현재 모델은 정적인 환경에 초점을 맞추고 있으므로, 동적인 환경에서 발생하는 문제점을 해결해야 합니다.  **마지막으로, 모델의 설명력을 높이는 연구가 필요합니다.** 모델의 예측 결과에 대한 신뢰도를 높이고, 예측 과정을 이해하기 쉽도록 모델을 개선하는 것이 중요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.13928/x3.png)

> 🔼 그림 2는 Fast3R의 모델 아키텍처를 보여줍니다.  양방향 정보 흐름을 지원하는 새로운 Transformer 기반 아키텍처를 기반으로 Fast3R은 다수의 입력 뷰를 동시에 처리할 수 있습니다.  즉, 여러 개의 이미지를 순차적으로 처리하는 기존 방식과 달리 Fast3R은 여러 이미지를 병렬적으로 처리하여 3D 재구성 속도를 높이고 정확도를 향상시킵니다. 그림에는 이미지 인코더, 퓨전 트랜스포머, 포인트맵 디코더의 세 가지 주요 구성 요소가 나와 있으며, 각 요소의 기능과 상호 작용을 시각적으로 보여줍니다. 특히, 퓨전 트랜스포머는 모든 이미지 패치 간의 전역적 상호 작용을 가능하게 하여,  전체적인 맥락 정보를 활용한 보다 정확한 3D 재구성을 가능하게 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Model architecture of Fast3R. Built upon a novel Transformer-based architecture which supports bidirectional information flow, Fast3R is able to process dense input views simultaneously.
> </details>



![](https://arxiv.org/html/2501.13928/x4.png)

> 🔼 그림 3은 Fast3R의 출력 결과를 보여주는 정성적 예시입니다. 이미지는 다양한 각도에서 촬영된 여러 장면들을 보여주며, Fast3R이 이러한 여러 이미지들을 사용하여 정확하고 상세한 3D 모델을 재구성할 수 있음을 보여줍니다. 특히 그림의 노란색 표지판에 쓰인 'Caution, cleaning in progress' 문구는 확대 시 읽을 수 있을 정도로 선명하게 재구성되어 Fast3R의 높은 해상도와 정확도를 다시 한번 확인할 수 있습니다. 이 그림은 다양한 시각에서 촬영된 이미지들을 기반으로 3D 모델을 생성하는 Fast3R의 성능을 직관적으로 보여주는 대표적인 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Qualitative examples of Fast3R’s output. The text on the yellow sign says “Caution, cleaning in progress” and is legible if zoomed in.
> </details>



![](https://arxiv.org/html/2501.13928/x5.png)

> 🔼 그림 4는 Fast3R이 더 많은 뷰(이미지)를 사용할수록 정확도가 향상되는 것을 보여줍니다. 특히 방향(Orientation) 부분에서는 3~5개의 뷰만 사용해도 성능이 포화상태에 도달함을 보여줍니다.  즉, Fast3R은 제한된 수의 뷰만으로도 객체의 방향을 정확하게 추정할 수 있음을 시사합니다.  이것은 Fast3R이 여러 뷰들 간의 상호작용을 효과적으로 활용하여 정확도를 높일 수 있음을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Pose accuracy with more views: Fast3R improves with the context from more views. Fast3R saturates the orientation portion of the benchmark, even using 3-5 views.
> </details>



![](https://arxiv.org/html/2501.13928/extracted/6149191/fig/4d_reconstruction.png)

> 🔼 그림 5는 DTU 데이터셋에서 다양한 수의 테스트 뷰를 사용하여 3D 재구성의 정확도와 완성도를 보여줍니다.  정확도는 RRA@5(Relative Rotation Accuracy at 5 degrees) 지표로, 완성도는 Completion 지표로 측정됩니다. 두 지표 모두 값이 낮을수록 좋습니다. 이 그림은 테스트 시 사용된 뷰의 수가 증가함에 따라 모델의 정확도와 완성도가 향상됨을 보여줍니다. 즉, 더 많은 뷰를 사용할수록 더 정확하고 완성도 높은 3D 재구성 결과를 얻을 수 있음을 시각적으로 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: DTU reconstruction quality vs. test number of views. Accuracy and Completion (lower is better) get better as we inference with more views.
> </details>



![](https://arxiv.org/html/2501.13928/x6.png)

> 🔼 그림 6은 논문에서 제시된 Fast3R 모델을 DAVIS 데이터셋의 동적인 시퀀스에 적용하여 얻은 4D 재구성 결과를 보여줍니다. 한 번의 순전파(forward pass)만으로 결과를 얻었으며, TAP-Vid-DAVIS [11] 데이터셋의 ground-truth track annotations을 사용하여 시각화했습니다.  이는 Fast3R이 정적인 장면뿐 아니라 동적인 장면에서도 효과적임을 보여주는 정성적(qualitative) 평가입니다. 그림은 여러 시점에서의 3D 재구성 결과를 보여주어 시간에 따른 변화를 시각적으로 확인할 수 있게 해줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Qualitative 4D reconstruction results on unseen dynamic scenes in DAVIS. Results are obtained with one forward pass. The tracks are visualized using ground-truth track annotations from TAP-Vid-DAVIS [11].
> </details>



![](https://arxiv.org/html/2501.13928/x7.png)

> 🔼 그림 7은 CO3D 데이터셋을 사용하여 카메라 자세 추정을 위한 훈련 중에 사용된 뷰의 수를 늘렸을 때의 효과를 보여줍니다.  x축은 훈련에 사용된 뷰의 개수를 나타내고, y축은 RRA@5(방향 오류)와 RTA@5(변환 오류)를 나타냅니다. 그래프는 훈련 데이터에 사용된 뷰의 수가 증가함에 따라 방향 및 변환 추정의 정확도가 향상됨을 보여줍니다. 즉, 더 많은 뷰를 사용하여 모델을 훈련시키면 카메라의 방향과 위치를 더 정확하게 추정할 수 있음을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Increasing # views during training: camera pose estimation on CO3D. Estimates of both orientation (RRA@5) and translation (RTA@5) improve with more views.
> </details>



![](https://arxiv.org/html/2501.13928/x8.png)

> 🔼 그림 8은 Fast3R 모델을 훈련하는 데 사용된 이미지의 수가 증가함에 따라 7-Scenes 및 NRGBD 데이터셋에서의 3D 재구성 성능 변화를 보여줍니다.  정확도(Accuracy)와 완성도(Completion)는 값이 낮을수록 좋으며, 훈련에 사용된 이미지 수가 많아질수록 향상되는 것을 확인할 수 있습니다. 또한, Normal Consistency는 값이 높을수록 좋으며, 마찬가지로 훈련 이미지 수 증가에 따라 성능이 향상됨을 보여줍니다. 이는 더 많은 뷰를 사용하여 훈련하면 모델이 더 나은 맥락 정보를 학습하고, 그 결과 3D 재구성 성능이 향상됨을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Increasing # views during training: reconstruction on 7scenes and NRGBD. Accuracy and Completion (lower is better) get better as we train with more views. Normal Consistency (high is better) also gets better as we train with more views.
> </details>



![](https://arxiv.org/html/2501.13928/x9.png)

> 🔼 그림 9는 학습 중 이미지 인덱스 위치 임베딩을 샘플링하는 효과를 보여줍니다. 인덱스 임베딩 없이 모델을 학습시키면, 학습 시 보았던 것보다 더 많은 뷰(6배)로 테스트할 때 회귀 손실이 급증합니다(오렌지색). 하지만 제안된 임베딩 전략을 사용하면 학습 시 뷰의 개수보다 훨씬 많은 뷰를 사용한 테스트에서도 성능이 비슷하게 유지됨을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Effect of sampling image index PE during training. If we train the model without sampling index embeddings, regression loss spikes (orange) when testing with more views than seen at training (top). Our embedding strategy performs comparably even with 6×6\times6 × the number of views during training.
> </details>



![](https://arxiv.org/html/2501.13928/x10.png)

> 🔼 그림 10은 Fast3R이 NRGBD 실내 장면 데이터셋에서 3D 재구성 결과를 시각화한 것입니다. Fast3R은 실내 공간의 규칙적인 구조(정사각형 모양의 방 등)를 학습하고, '루프 클로저'(이전에 방문했던 장소를 다시 인식하는 능력) 기능을 보여줍니다. 이미지는 Fast3R이 다양한 각도에서 촬영된 여러 이미지를 기반으로 실내 공간의 3D 모델을 정확하게 재구성하고, 공간적인 연속성을 유지하며, 같은 위치를 여러 번 방문했을 때도 일관되게 인식하는 능력을 시각적으로 보여줍니다. 이는 Fast3R의 강력한 3D 재구성 성능을 보여주는 중요한 증거입니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Visualizations of results on NRGBD scenes. Fast3R learns the regularity of indoor rooms (square-like shapes) and demonstrates “loop closure” capabilities.
> </details>



![](https://arxiv.org/html/2501.13928/x11.png)

> 🔼 그림 11은 모델 크기가 Fusion Transformer의 성능에 미치는 영향을 보여줍니다. 모델 크기가 커질수록 카메라 자세 추정의 정확도는 높아지고(↑↑), 3D 재구성의 정확도는 향상됩니다(↓↓). 모든 모델은 60,000번의 step으로 학습되었으며, 이는 60 epoch에 해당합니다(본 논문에서는 100 epoch를 사용했습니다).  이 실험은 모델 크기가 증가함에 따라 카메라 자세 추정 및 3D 재구성 작업 모두에서 성능이 향상됨을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Model scaling effect. Increasing the size of the Fusion Transformer leads to better camera pose estimation (↑↑\uparrow↑) and 3D reconstruction (↓↓\downarrow↓). All models are trained for 60k steps (equivalent to 60 epochs; the main paper uses 100 epochs).
> </details>



![](https://arxiv.org/html/2501.13928/extracted/6149191/artifacts_for_suppl/gaussian_splat_bundle_adjustment/gaussian_vis_co3d.png)

> 🔼 그림 12는 데이터 크기가 모델 성능에 미치는 영향을 보여줍니다. 훈련 데이터의 양이 증가함에 따라 카메라 자세 추정 및 3D 재구성 성능이 향상되는 것을 보여줍니다. 모든 모델은 60,000번의 학습 단계(60 에폭에 해당, 본 논문에서는 100 에폭 사용)를 거쳤습니다.  이 그래프는 훈련 데이터의 양이 증가함에 따라 모델의 카메라 자세 추정 및 3D 재구성 정확도가 어떻게 개선되는지 보여주는 실험 결과를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Data scaling effect. More training data leads to better camera pose estimation (↑↑\uparrow↑) and 3D reconstruction (↓↓\downarrow↓). All models are trained for 60k steps (equivalent to 60 epochs; the main paper uses 100 epochs).
> </details>



![](https://arxiv.org/html/2501.13928/extracted/6149191/artifacts_for_suppl/gaussian_splat_bundle_adjustment/pose_vis_tnt.png)

> 🔼 그림 13은 Fast3R이 재구성에 사용되지 않은 카메라 자세에서 생성한 가우시안의 시각화입니다. 화살표 방향으로 시간 순서대로 정렬된 프레임들은 가우시안이 없는 넓은 영역으로 보아 재구성에 사용된 것과 매우 다른 자세를 보여줍니다. 이 장면은 CO3D의 7개 이미지에서 얻은 것입니다.  본래 캡션이 간략하여, 이해를 돕기 위해 보다 자세한 설명을 추가했습니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: Visualization of Gaussians from unseen poses. The frames are ordered temporally along the direction of the arrows. The middle frames show poses very different from those used for reconstruction, as is evidenced by the large areas with no Gausisans. The scene is fit from 7 images from CO3D.
> </details>



![](https://arxiv.org/html/2501.13928/x12.png)

> 🔼 그림 14는 번들 조정이 자세 추정을 개선하는 방법을 보여줍니다. 왼쪽에는 Fast3R의 재구성 결과가, 가운데에는 GS-BA(Gaussian Splatting 기반 번들 조정)를 적용하기 전의 원본 자세가, 오른쪽에는 GS-BA를 적용한 후의 자세가 각각 표시되어 있습니다. GS-BA를 적용하면 Fast3R의 재구성 결과를 더욱 개선할 수 있음을 보여줍니다.  원본 자세와 GS-BA 적용 후의 자세를 비교함으로써 번들 조정의 효과를 명확히 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: Bundle adjustment further improves pose. Left: reconstruction from Fast3R. Middle: Original poses pre-GS-BA. Right: Poses after GS-BA.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| # Views | Fast3R Time (s) | Fast3R Peak GPU Mem (GiB) | DUSt3R Time (s) | DUSt3R Peak GPU Mem (GiB) |
|---|---|---|---|---|
| 2 | 0.065 | 3.84 | 0.092 | 3.52 |
| 8 | 0.122 | 6.33 | 0.386 | 24.59 |
| 32 | 0.509 | 13.25 | 129.0 | 67.61 |
| 48 | 0.84 | 20.8 | OOM | OOM |
| 320 | 15.938 | 41.90 | OOM | OOM |
| 800 | 89.569 | 55.97 | OOM | OOM |
| 1000 | 137.62 | 63.01 | OOM | OOM |
| 1500 | 308.85 | 78.59 | OOM | OOM |{{< /table-caption >}}
> 🔼 표 2는 단일 A100 GPU에서 Fast3R과 DUSt3R의 시스템 성능 지표를 다양한 뷰 수에 대해 보여줍니다. 시간은 초(s) 단위로, 메모리는 기가바이트(GiB) 단위로 측정됩니다. 각 뷰의 해상도는 512x384입니다. DUSt3R의 경우 48개의 뷰에서 N² 쌍별 재구성이 글로벌 정렬 단계에서 모든 VRAM을 소모합니다. Fast3R의 보고된 최고 FPS인 251.1은 224x224 해상도의 108개 뷰를 사용합니다. 이 표는 Fast3R의 확장성과 효율성을 강조하며, 많은 수의 이미지를 처리하는 데 있어 DUSt3R보다 훨씬 우수한 성능을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 2: System performance metrics for different view counts on Fast3R and DUSt3R on a single A100. Time is measured in seconds (s), and memory is measured in gibibytes (GiB). Each view is 512x384 in resolution. For DUSt3R, at 48 views the N2superscript𝑁2N^{2}italic_N start_POSTSUPERSCRIPT 2 end_POSTSUPERSCRIPT pairwise reconstructions eventually consume all VRAM at its global alignment stage. Note that Fast3R’s reported fastest FPS of 251.1 uses 108 views in 224x224 resolution.
> </details>

{{< table-caption >}}
| Method | FPS | 7 scenes [47] Acc↓ | 7 scenes [47] Comp↓ | NRGBD [3] Acc↓ | NRGBD [3] Comp↓ |
|---|---|---|---|---|---| 
| F-Recon [65] | &lt;0.1 | 7.62 | 2.31 | 20.59 | 6.31 |
| DUSt3R† [61] | 0.78 | **1.23** | 0.91 | **2.51** | 1.03 |
| Spann3R [57] | 65.4 | 1.48 | **0.85** | 3.15 | 1.10 |
| **Fast3R (Ours)** | **251.1** | 1.58 | 0.93 | 3.40 | **1.01** |{{< /table-caption >}}
> 🔼 표 3은 7-Scenes [47] 및 NRGBD [3] 데이터셋에 대한 정량적 재구성 결과를 보여줍니다. 두 데이터셋 모두 500~1500프레임의 비디오 경로를 포함하며, 기준 모델들과 동일한 프레임 건너뛰기를 사용하여 평가했습니다. 7-Scenes의 경우 skip=20이고, NRGBD의 경우 skip=40입니다. DUSt3R†는 GPU 메모리에 맞추기 위해 224x224 이미지에서 DUSt3R의 최종 가중치를 사용했음을 나타냅니다. 거리는 선행 0.0을 제거하기 위해 100배 확장되었습니다. 전체 표는 부록에 있습니다.  간단히 말해, 이 표는 제시된 다양한 방법을 사용한 3D 재구성 정확도를 정량적으로 비교하여, Fast3R의 성능을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Quantitative reconstruction results on scene datasets: The numbers indicate median distance to GT points on 7-Scenes [47] and NRGBD [3] datasets. These datasets contain video trajectories of 500-1500 frames, and we evaluate using the same frame skip as other baselines. For 7-Scenes this is skip=20, and NRGBD uses skip=40. DUSt3R† indicates using DUSt3R’s final weights on 224×224224224224\times 224224 × 224 images, to fit within GPU memory. Distances are scaled 100×100\times100 × to remove the leading 0.0. We defer the full table to the appendix.
> </details>

{{< table-caption >}}
| Method | Views | Acc↓ (Med.) | Comp↓ (Med.) |
|---|---|---|---| 
| DUSt3R [61] | all/5 | **1.159** | 0.914 |
| DUSt3R† [61] | all/5 | 1.297 | 1.002 |
| Spann3R [57] | all/5 | 2.268 | 1.295 |
| **Fast3R (Ours)** | all/5 | 1.706 | **0.857** |{{< /table-caption >}}
> 🔼 표 4는 물체 중심 DTU 데이터셋 [1]에 대한 정량적 재구성 결과를 보여줍니다. 49개 프레임의 궤적에서 skip=5를 사용했습니다. 이 표는 다양한 방법을 사용하여 3D 재구성 작업의 정확도와 완성도를 평가한 결과를 보여줍니다.  정확도는 GT 점에 대한 중간 거리로 측정되며, 완성도는 GT 점을 얼마나 많이 재구성했는지 나타냅니다. 이러한 지표는 7-Scenes [47] 및 NRGBD [3] 데이터셋과 같은 다른 장면 데이터셋에 대한 결과와 비교하여 Fast3R의 성능을 평가하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Quantitative results on object-centric DTU [1] dataset. Using a skip=5 on trajectories of 49 frames.
> </details>

{{< table-caption >}}
| Method | 7-Scenes [47] |  | NRGBD [3] |  | DTU |  |
|---|---|---|---|---|---|---|
| Acc↓ | Comp↓ | Acc↓ | Comp↓ | Acc↓ | Comp↓ |  |
| Fast3R (ours) | 2.84 | 1.37 | 4.39 | 1.28 | 3.91 | 1.41 |
| w/o local head | 4.81 | 1.64 | 4.85 | 1.32 | 3.88 | 1.41 |
| Δ | +1.97 | +0.27 | +0.46 | +0.04 | -0.03 | 0.00 |{{< /table-caption >}}
> 🔼 이 표는 Fast3R 모델에서 Local head가 3D 재구성 성능에 미치는 영향을 보여줍니다.  Local head를 제거했을 때의 오류 변화를 정량적으로 분석합니다.  Global pointmap에 정렬된 local pointmap을 기준으로 오류 증감을 빨간색(증가)과 초록색(감소)으로 표시합니다.  이는 Local head가 3D 재구성의 세부적인 부분에 어떻게 기여하는지 보여주는 실험 결과입니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Ablation on the effect of local head on 3D reconstruction. Red/green indicate an increase/decrease in error compared to using the local pointmap aligned to the global pointmap.
> </details>

{{< table-caption >}}
| Method | RPE Rotation (↓) | RPE Translation (↓) |
|---|---|---|
| Fast3R | 27.9 | 7.64 |
| Fast3R w/ GS-BA | **11.0** | **1.80** |{{< /table-caption >}}
> 🔼 표 6은 번들 조정을 통해 자세 추정을 더욱 향상시킬 수 있음을 보여줍니다. InstantSplat [17]을 사용하여 Tanks and Temples의 'Family' 장면에서 예시를 보여줍니다.  번들 조정은 카메라 자세와 3D 지오메트리의 정확도를 높이는 과정으로, Fast3R 모델의 출력인 점 구름(point cloud)을 기반으로 합니다.  InstantSplat은 이 점 구름을 사용하여 가우시안 분포를 생성하고, 이 분포들을 최적화하여 재투영 오차를 최소화합니다.  본 표는 번들 조정 전후의 자세 평가 지표(RPE Rotation, RPE Translation)를 비교하여, 번들 조정을 통해 자세 추정의 정확도가 향상됨을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Pose estimation can further improve with Bundle Adjustment. We show an example on the ”Family” scene from Tanks and Temples, using InstantSplat [17].
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
{{< /gallery >}}