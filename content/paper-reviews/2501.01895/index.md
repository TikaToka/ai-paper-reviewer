---
title: "EnerVerse: Envisioning Embodied Future Space for Robotics Manipulation"
summary: "EnerVerse: 로봇 조작을 위한 미래 공간 생성 프레임워크가 장기간 작업에서 성능 향상을 달성했습니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["AI Applications", "Robotics", "🏢 AgiBot",]
showSummary: true
date: 2025-01-03
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.01895 {{< /keyword >}}
{{< keyword icon="writer" >}} Siyuan Huang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-06 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.01895" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.01895" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/enerverse-envisioning-embodied-future-space" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

현재 로봇 조작 분야는 **데이터 부족**과 **모달 간 정렬의 어려움**이라는 주요 과제에 직면하고 있습니다. 기존의 고용량 기본 모델은 다양한 모달리티에서 성공을 거두었지만, **실시간 상호작용**이 필요한 로봇 조작 분야에는 적용하기 어려운 한계가 있습니다. 특히, 물리적 세계와 상호작용하는 로봇의 경우 정확한 행동 계획과 실행이 필수적이며, **실제 데이터 확보의 어려움**은 모델 학습에 큰 장벽이 됩니다.

본 논문에서는 이러한 문제를 해결하기 위해 **EnerVerse**라는 새로운 프레임워크를 제안합니다. EnerVerse는 **비디오 생성 모델과 4D Gaussian Splatting을 통합**하여 데이터를 효율적으로 생성하고 품질을 향상시키는 데이터 엔진 파이프라인을 사용합니다. 또한, **Free Anchor View (FAV)**라는 새로운 개념을 도입하여 로봇의 관찰과 분석 능력을 향상시켰습니다. FAV는 다양한 작업 환경에서 로봇의 일반화 및 적응성을 높여주며, 실험 결과 **장기간 로봇 조작 작업에서 성능이 크게 향상**되는 것을 확인했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} EnerVerse는 로봇 조작을 위한 미래 공간 생성 프레임워크로, 장기간 작업에서 성능 향상을 달성했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 데이터 엔진 파이프라인과 4D Gaussian Splatting을 통합하여 데이터 품질과 다양성을 향상시켰습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} Free Anchor View를 도입하여 로봇의 일반화 및 적응성을 높였습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **로봇 조작을 위한 새로운 프레임워크인 EnerVerse**를 제시하여 시뮬레이션과 실제 환경 간의 격차를 줄이고 장기간의 로봇 작업 성능을 향상시키는 데 기여합니다. **데이터 엔진 파이프라인과 4D Gaussian Splatting을 통합**하여 데이터 품질과 다양성을 향상시키고, **새로운 Free Anchor View를 도입**하여 로봇의 일반화 및 적응성을 높였습니다. **장기간의 로봇 조작 작업에서 우수한 성능**을 보여주어, 관련 연구 분야에 큰 영향을 미칠 것으로 기대됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.01895/x1.png)

> 🔼 그림 1은 제안된 EnerVerse 모델의 개요를 보여줍니다. 세 가지 주요 구성 요소로 이루어져 있습니다. 첫째, 초기 재구성(Initial Reconstruction)은 로봇에 장착된 카메라의 관측 이미지를 사용하여 앵커 뷰(anchor view)를 설정하고 환경에 적응하고 작업별 요구사항을 충족하는 초기 3D 점 구름을 생성합니다. 둘째, 자유 앵커 뷰 렌더링(Free Anchor View Renders)은 이러한 앵커 뷰에서 렌더링된 이미지를 생성하여 포괄적인 장면 표현을 제공합니다. 셋째, 청크 단위 자기 회귀 생성(Chunk-wise Autoregressive Generation)은 작업 지침에 따라 청크 단위로 이미지 시퀀스를 생성하는 다중 뷰 비디오 확산(multi-view video diffusion)을 사용합니다. 정책 헤드(policy head)와 통합되면 이 모듈은 주어진 작업을 실행하기 위한 로봇 동작을 생성할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: The overview of our proposed EnerVerse model, consisting of three key components. First, Initial Reconstruction uses observation images from cameras mounted on the robot to build an initial 3D point cloud, with anchor views set to adapt to the environment and meet task-specific requirements. Second, Free Anchor View Renders generates rendered images from these anchor perspectives to provide comprehensive scene representations. Finally, Chunk-wise Autoregressive Generation employs a multi-view video diffusion to produce image sequences in chunks based on task instructions. When integrated with a policy head, this module can generate robotic actions to execute the given task.
> </details>





{{< table-caption >}}
| Method | PSNR↑ | FVD↓ | Quality↑ | Seman.↑ | Consist.↑ | Continuity↑ | Long Task Ability | 
|---|---|---|---|---|---|---|---| 
| **DC-FN** | 25.42 | 445.94 | 54 | 97 | **92** | 80 | × | 
| **EnerVerse** | **26.1** | **404.65** | **59** | 97 | 89 | **90** | ✓ | {{< /table-caption >}}

> 🔼 표 1은 제안된 EnerVerse 모델과 비교 모델인 DynamicCrafter (FN)의 성능을 비교 분석한 표입니다.  Atomic Task 지표(정량적 비교 및 사용자 연구)와 Long Task 능력 측면에서 두 모델의 성능 차이를 보여줍니다. 정량적 지표(PSNR, FVD) 뿐만 아니라,  비디오의 질, 의미적 정확성, 일관성, 연속성, 장기 작업 수행 능력 등 다양한 측면에서 사용자 연구를 통해 평가한 결과를 포함합니다.  EnerVerse 모델이 DynamicCrafter (FN)보다 대부분의 지표에서 우수한 성능을 보이며, 비디오 생성 및 작업 수행 능력이 뛰어남을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Performance comparison between DynamiCrafter (FN) and our proposed approach across Atomic Task metrics (Quantitative Comparison and User Study) and Long Task ability. The proposed method outperforms DynamiCrafter (FN) in most metrics, demonstrating its effectiveness in video generation and task performance.
> </details>





### In-depth insights


#### Embodied Future Space
본 논문에서 제시된 "구현된 미래 공간(Embodied Future Space)" 개념은 **로봇 조작 작업을 위한 혁신적인 접근법**입니다.  기존의 단순한 미래 예측을 넘어, 로봇의 **감각 정보(시각, 촉각 등)와 물리적 상호작용을 통합하여 미래 상황을 모델링**합니다. 이는 **장기적인 계획 수립과 불확실성에 대한 강인성을 향상**시키는 데 중요합니다.  특히, **여러 시점의 정보를 통합하여 3차원 공간 내에서의 물체와 로봇의 상호작용을 보다 정확하게 예측**함으로써, 기존의 제한된 관점에서의 예측으로 인한 오류를 최소화합니다.  **자유로운 기준점(Free Anchor View)** 개념은 다양한 시점에서의 정보를 활용하여 **로봇의 일반화 능력과 적응력을 향상**시키는 데 기여하며, 실제 환경에서의 제약을 극복하는 데 도움을 줍니다. 또한, 생성 모델과 4D 가우시안 스플래팅(4DGS)을 통합한 데이터 엔진은 **데이터의 질과 다양성을 개선**, 시뮬레이션과 현실 간의 차이를 줄이는 데 효과적입니다.  결론적으로, "구현된 미래 공간"은 **로봇 조작의 성능과 안정성을 크게 향상시킬 가능성**을 보여주는 중요한 개념입니다.

#### 4DGS Data Engine
본 논문에서 제시된 4DGS 데이터 엔진은 **시뮬레이션 데이터의 한계를 극복하고 실제 로봇 조작에 필요한 고품질 데이터를 생성하는 핵심 구성 요소**입니다.  **4D 가우시안 스플래팅(4DGS)**을 활용하여 다중 시점의 비디오 데이터로부터 **3D 공간 정보와 시각적 일관성을 유지하는 동적 장면을 재구성**합니다.  이는 시뮬레이션 환경과 실제 환경 간의 차이, 즉 **심-실 간극을 줄이는 데 효과적**입니다.  **생성 모델의 일반화 능력**과 **4DGS의 공간 제약 조건**을 결합하여 데이터 품질과 다양성을 반복적으로 향상시키는 **데이터 플라이휠 효과**를 창출하여, 실제 로봇 조작 데이터 부족 문제 해결에 기여합니다.  이러한 데이터 증강 전략은 로봇 정책의 예측 성능 향상에 크게 기여하며, 특히 장기간 로봇 조작 과제에서 성능 개선에 중요한 역할을 합니다.

#### Free Anchor View
본 논문에서 제시된 '자유앵커뷰(Free Anchor View, FAV)'는 로봇 조작 작업의 성능 향상을 위한 혁신적인 접근 방식입니다. **기존의 고정된 카메라 관점에서 벗어나**, 로봇의 기준 좌표계를 기반으로 임의의 위치에서 관측이 가능하도록 함으로써 **다양한 관점에서의 정보 획득**을 가능하게 합니다. 이는 **좁은 환경에서의 물리적 제약 해소**, **움직임 모델링의 모호성 제거**, 그리고 **다양한 작업 환경에 대한 적응력 향상**이라는 주요 장점을 제공합니다. FAV는 여러 개의 관점을 제공함으로써 **3D 공간 정보의 풍부한 획득**에 기여하며, 이는 정책(policy)의 성능 향상으로 직결됩니다.  **시뮬레이션 환경에서의 데이터 생성**을 통해 실제 환경에서의 데이터 획득 어려움을 극복하고, **4D 가우시안 스플래팅(4DGS)**과의 통합을 통해 시뮬레이션과 현실 간의 차이를 줄이는데 기여합니다.  결론적으로, FAV는 로봇의 상황 인식 및 적응 능력을 크게 개선하여 장기간에 걸친 로봇 조작 작업의 성능을 향상시키는 핵심 요소임을 알 수 있습니다.

#### Chunkwise Autoregressive
본 논문에서 제안하는 ‘Chunkwise Autoregressive’ 방법은 **장기적인 시계열 데이터를 효율적으로 처리하기 위한 핵심 전략**입니다.  이는 단순히 비디오 프레임을 순차적으로 생성하는 것이 아니라, **일정 길이(chunk)의 비디오 시퀀스를 독립적인 단위로 처리**하여 생성하는 방식입니다. 이를 통해 모델의 계산 복잡도를 줄이고, 장기적인 의존성 문제를 완화하여 더욱 안정적이고 효율적인 생성을 가능하게 합니다. **양방향 어텐션 메커니즘과 단방향 생성 패러다임의 결합**은 짧은 시퀀스 내에서 일관성과 연속성을 유지하면서, 동시에 무한히 긴 시퀀스를 생성할 수 있도록 합니다.  **희소 메모리 기법**을 활용하여 비디오 데이터의 중복성을 줄이고, 연산량을 감소시키는 점도 주목할 만합니다. 이러한 Chunkwise Autoregressive 접근 방식은 로봇 조작과 같은 복잡한 시계열 작업에 적용될 때, **모델의 일반화 능력과 적응성 향상에 크게 기여**할 것으로 예상됩니다.  이는 효율적인 연산과 함께 장기적인 시계열 예측의 정확성을 모두 확보하는 혁신적인 전략이라고 할 수 있습니다.

#### Sparse Memory Context
본 논문에서 제안하는 희소 메모리 구조는 **장기간의 시퀀스 생성을 위한 효율적인 메커니즘**으로써, 비디오 데이터의 고유한 중복성을 인지하고 불필요한 정보를 제거하여 메모리 사용량을 최소화하는 동시에 연속성과 일관성을 유지합니다. 기존의 연속적인 메모리 사용 방식과 달리, **필요한 정보만 선택적으로 저장하고 처리**함으로써 모델의 계산 비용을 줄이고, 특히 장기간 작업 수행 시 발생할 수 있는 메모리 과부하 문제를 해결합니다. 이를 통해 **무한히 긴 시퀀스 생성**이 가능해지며, 로봇 조작 작업의 복잡한 시계열 데이터를 효과적으로 처리할 수 있습니다.  **단순히 과거 정보를 반복적으로 저장하는 것이 아니라, 핵심 정보만 추출하여 저장하고 활용**하는 전략은 효율성을 높이는 동시에, 모델의 안정성과 일반화 능력을 향상시키는 데 크게 기여합니다.  **불필요한 정보 제거를 통해 모델 붕괴 현상을 방지하고 예측 성능을 향상**시키는 희소 메모리 구조는 장기적인 비전 생성 및 로봇 제어 분야에서 큰 가능성을 보여줍니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.01895/x2.png)

> 🔼 그림 2는 제안된 차례대로 확산 모델의 구조를 보여줍니다. (a)에서는 카메라 i에서 캡처한 관측 프레임 시퀀스와 해당 광선 방향 맵을 관측 사전 정보로 사용합니다. 이러한 카메라 관측을 활용하여 깊이 래핑 및 렌더링을 통해 초기 3D 재구성을 얻은 다음, 여러 개의 자유 앵커 뷰(FAV)를 설정합니다. 카메라 관측 프레임 외에도 FAV의 렌더링 프레임을 후속 청크 확산 모델의 컨텍스트 사전 정보로 사용합니다. 앵커 뷰 i+1 시퀀스를 합성하기 위해 해당 광선 방향 맵을 비디오 잠재 변수와 연결합니다. 카메라가 정지해 있을 때만 카메라의 관측 이미지를 선택적으로 사용하고, 모든 센서가 움직이는 경우 렌더링된 이미지만 컨텍스트 사전 정보로 사용할 수 있습니다. (b)는 청크 단위 자기 회귀 훈련 과정을 보여줍니다. 연속 시퀀스에서 무작위로 선택한 깨끗한 프레임을 노이즈 프레임과 연결하여 잡음 제거된 잠재 변수를 예측합니다. 추론 단계에서 잡음 제거된 프레임이 생성되면 다음 추론 단계를 위한 새로운 깨끗한 프레임으로 사용됩니다. 이러한 반복적인 과정은 미리 정의된 EOS(End-Of-Sequence) 프레임이 발생할 때까지 계속됩니다. 자기 회귀 생성 과정을 간소화하기 위해 (b)에서는 하나의 뷰만 시각화하지만, 모델은 다중 뷰 생성을 완벽하게 지원합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: The architecture of our proposed next-chunk diffusion model. As shown in Figure (a), a sequence of observational frames, captured by camera i𝑖iitalic_i and accompanied by the corresponding ray direction map, is utilized as observation priors. Leveraging these camera observations, an initial 3D reconstruction is obtained through depth wrapping and rendering Lassner and Zollhofer (2021), then several Free Anchor Views are established accordingly. In addition to camera observational frames, a render frame from the FAV is also employed as context priors for the subsequent chunk diffusion models. To synthesize the anchor view i+1𝑖1i+1italic_i + 1 sequence, the respective ray direction map is concatenated with the video latent. Notably, the observational image from the camera is optional and used only when the camera is static. If all sensors are in motion, the rendered image alone can serve as the context prior. In the context of the chunk-wise autoregressive training process, as depicted in Figure (b), clean frames selected at random from consecutive sequences are concatenated with noisy frames to forecast denoised latents. During the inference phase, once denoised frames are produced, they are utilized as the new set of clean frames for the following inference step. This iterative process persists until the predefined End-Of-Sequence (EOS) frame is encountered. Notably, we visualize only one view in Figure (b) to simplify the demonstration of the autoregressive generation process, but multi-view generation is fully supported by the model.
> </details>



![](https://arxiv.org/html/2501.01895/x3.png)

> 🔼 그림 3은 EnerVerse의 데이터 엔진으로서의 파이프라인을 보여줍니다. 여러 대의 카메라에서 캡처한 관측 이미지와 앵커 뷰에서 렌더링된 이미지가 다중 뷰 비디오 생성기를 통해 처리되어 잡음이 제거된 다중 뷰 비디오를 생성합니다. 이러한 비디오는 해당하는 카메라 포즈와 함께 4D 가우시안 스플래팅(4D GS)에 사용되어 4D 장면 재구성을 수행합니다. 재구성된 콘텐츠는 앵커 뷰에서 렌더링되어 고정밀 이미지를 생성하며, 이 이미지는 모션 일관성과 재구성 품질을 향상시키기 위해 반복적으로 파이프라인에 다시 입력됩니다. 이러한 반복 루프는 기하학적 일관성과 생성적 개선을 결합하여 로봇 조작과 같은 작업에 대해 고품질 출력을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: The pipeline for EnerVerse as a data engine. Observation images captured from multiple cameras, along with rendered images from anchor views, are processed by the multi-view video generator to produce denoised multi-view videos. These videos, paired with their corresponding camera poses, are utilized in 4D Gaussian Splatting (4D GS) for 4D scene reconstruction. The reconstructed content is rendered from anchor views to generate high-precision images, which are iteratively fed back into the pipeline to enhance motion consistency and reconstruction quality. This iterative loop combines geometric consistency with generative refinement, delivering high-fidelity outputs for tasks such as robotic manipulation.
> </details>



![](https://arxiv.org/html/2501.01895/x4.png)

> 🔼 그림 4는 LIBERO 벤치마크에서 자유 앵커 뷰(FAV) 생성을 보여줍니다. 앵커 뷰 1은 장착된 카메라로 캡처한 관찰 이미지를 나타냅니다. 앵커 뷰 2와 앵커 뷰 3은 깊이 래핑을 사용하여 앵커 뷰 1에서 재구성된 점 구름으로부터 렌더링하여 생성됩니다. 이 그림은 로봇이 다양한 각도에서 장면을 관찰할 수 있도록 여러 관점을 제공하는 FAV의 개념을 보여줍니다.  깊이 래핑을 통해 하나의 카메라 관찰만으로도 다양한 앵커 뷰를 생성할 수 있음을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Visualization of FAVs generation on the LIBERO benchmark. Anchor View 1 represents the observation image captured by a mounted camera. Anchor View 2 and Anchor View 3 are generated by rendering from a point cloud reconstructed from Anchor View 1 using depth wrapping.
> </details>



![](https://arxiv.org/html/2501.01895/x5.png)

> 🔼 그림 5는 RT-1 데이터셋에서 EnerVerse와 DynamiCrafter(FN)의 단일 뷰 비디오 생성에 대한 정성적 비교를 보여줍니다. EnerVerse는 42번째 프레임에서 EOS(End of Sequence) 프레임을 예측하므로, 생성된 시퀀스에서 8번째, 16번째, 24번째, 41번째 프레임을 시각화하여 비교합니다. DynamiCrafter(FN)에 의해 생성된 시퀀스는 장기 작업의 논리를 유지하지 못하고 시퀀스가 길어짐에 따라 많은 환각을 생성하는 반면, EnerVerse에 의해 생성된 시퀀스는 논리적으로 일관되고 지속적으로 작업의 전체 미래 공간을 생성하며 EOS 프레임을 정확하게 예측합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Qualitative comparison for single view video generation between EnerVerse and DynamiCrafter(FN) on RT-1 dataset. Since EnerVerse predict EOS frame at 42th frame for this task, we visualize 8th, 16th, 24th and 41th frame sampled from both generated sequence. The sequences generated by DynamiCrafter(FN) did not maintain the logic of the long-range task, producing many hallucinations as the sequence grew. In contrast, the sequence generated by EnerVerse was logically coherent, continuously and completely generating the future space of the entire task, and accurately predicting the EOS (End of Sequence) frame.
> </details>



![](https://arxiv.org/html/2501.01895/x6.png)

> 🔼 그림 6은 제시된 EnerVerse 모델이 여러 각도에서 생성한 비디오 프레임을 보여줍니다. 왼쪽은 LIBERO 벤치마크 데이터셋을 사용한 시뮬레이션 결과이고, 오른쪽은 AgiBot World AgiBot (2024) 데이터셋으로부터 수집된 실제 로봇 조작 데이터를 사용한 결과입니다. 하나의 뷰는 고정된 RGB 센서와 중복되고, 다른 뷰들은 수동으로 설정됩니다. 시각화된 프레임들은 생성된 시퀀스에서 균일하게 샘플링됩니다. 다양한 뷰에서 객체의 일관성을 강조하기 위해 빨간색 사각형으로 강조 표시했습니다.  이는 EnerVerse 모델의 다중 관점 비디오 생성 능력과 실제 로봇 조작 환경에 대한 적응력을 보여주는 정성적 결과입니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Qualitative results for multi anchor view generation on LIBERO benchmark (left) and real-world manipulation data (right), collected from AgiBot World AgiBot (2024). One view is overlapped with a fixed RGB sensor and other views are manully set. Visualized Frames are uniformly sampled from generated sequence. We emphasize the consistency of objects across views by highlighting them with a red rectangle.
> </details>



![](https://arxiv.org/html/2501.01895/x7.png)

> 🔼 그림 7은 비디오 생성에서 맥락 메모리 메커니즘의 제거 실험 결과를 보여줍니다.  연속적인 맥락을 사용하여 생성 모델에 과거 정보를 제공하면 (첫 번째 줄), 예상치 못한 모델 붕괴가 발생하는 경우가 많습니다. 반면에,  희소 메모리를 사용하는 모델은 (두 번째 줄) 강력한 성능을 보이며 컴퓨팅 자원을 절약합니다.  첫 번째 줄은 연속된 프레임들을 모두 사용하는 반면, 두 번째 줄은 일부 프레임만 선택적으로 사용하여 메모리 효율을 높이고, 과도한 정보로 인한 부정확성을 줄이는 효과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Ablation results for context memory mechanism in video generation. Providing history information to the generation model with consecutive context (first line) often leads to unexpected model collapse while the model with sparse memory (second line) shows robust performance and save mush computing resources.
> </details>



![](https://arxiv.org/html/2501.01895/x8.png)

> 🔼 그림 8은 모델의 여러 어텐션 헤드와 레이어에서의 어텐션 맵을 보여줍니다. Y축은 8단계에 걸친 예측된 액션 공간(쿼리)을 나타내고, X축은 키-값 공간을 나타냅니다. KV 공간의 처음 4열은 스파스 메모리 공간의 정보에 해당하고, 나머지 8열은 예측된 미래 공간에 해당합니다. 이 맵들은 모델이 액션을 예측할 때 스파스 메모리 조건(왼쪽)과 미래 공간 조건(오른쪽)에 어떻게 주의를 기울이는지 보여줍니다. 밝은 노란색은 더 높은 어텐션 점수를, 어두운 빨간색은 더 낮은 어텐션 점수를 나타냅니다.  각 열은 특정 시점의 정보를 나타내며, 모델이 시간이 지남에 따라 어떻게 주의를 집중하는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Attention maps from different attention heads and layers of the model. The y-axis represents the predicted action space (the Query), spanning 8 steps, while the x-axis represents the Key-Value space. The first 4 columns in the KV space correspond to information from the Sparse Memory space, while the last 8 columns correspond to the predicted future space. These maps highlight how the model attends to sparse memory conditions (left) and future space conditions (right) when predicting actions. The bright yellow indicates a higher attention score while dark red indicates a lower one.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | Visual Input | Spatial | Object | Goal | Long | Avg. |
|---|---|---|---|---|---|---|
| **Diffusion Policy** | One Third View | 78.3 | 92.5 | 68.3 | 50.5 | 72.4 |
| **Octo** | One Third View | 78.9 | 85.7 | **84.6** | 51.1 | 75.1 |
| **OpenVLA** | One Third View | 84.7 | 88.4 | 79.2 | 53.7 | 76.5 |
| **MDT** | One Third & One Wrist View | 78.5 | 87.5 | 73.5 | 64.8 | 76.1 |
| **MAIL** | One Third & One Wrist View | 74.3 | 90.1 | 81.8 | 78.6 | 83.5 |
| **EnerVerse** | One FAV | **92.1** | **93.2** | 78.1 | **73.0** | **84.1** |
| **EnerVerse** | Three FAVs | **91.2** | **97.7** | **85.0** | **80.0** | **88.5** |{{< /table-caption >}}
> 🔼 표 2는 LIBERO 벤치마크의 네 가지 작업 세트에 대한 평가 결과를 보여줍니다. 이 표는 단일 및 다중 시각 입력 설정 모두에서 제안된 EnerVerse 방법이 우수한 성능을 달성했음을 보여줍니다. EnerVerse는 단일 시각 입력에서 평균 점수 84.0을 달성하여 MAIL(83.5) 및 OpenVLA(76.5)와 같은 강력한 기준보다 우수한 성능을 보였습니다. 세 개의 시각 입력 구성은 성능을 더욱 향상시켜 88.5의 평균 점수를 달성했으며, 이는 더욱 풍부한 시각 정보가 성능 향상에 기여함을 보여줍니다. 특히 EnerVerse는 공간(92.1 및 91.2), 객체(93.2 및 97.7), 장기(73.0 및 80.0) 작업에서 뛰어난 성능을 보여주는 균형 잡힌 성능을 모든 작업에서 보여주었습니다. 이는 제안된 아키텍처의 효율성과 향상된 이해 및 작업 성능을 위한 다중 시각 입력 활용의 효과를 검증합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Evaluation results on the LIBERO benchmark across four task suites. Our method achieves superior performance in both single and multi-visual input settings.
> </details>

{{< table-caption >}}
| Setup | w/o Sparse Memory | w Sparse Memory |
|---|---|---|
| LIBERO-Long-SV | 30.8 | 73 |{{< /table-caption >}}
> 🔼 표 3은 LIBERO-Long 작업에서 희소 메모리를 사용했을 때와 사용하지 않았을 때의 성능을 비교한 표입니다.  희소 메모리는 장기간에 걸친 작업에서 모델의 성능을 유지하는 데 중요한 역할을 합니다.  이 표는 희소 메모리의 효과를 정량적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Performance comparison on the LIBERO-Long task with and without Sparse Memory.
> </details>

{{< table-caption >}}
| Strategy | All-Scratch | With DC Pretrain. | One-Stage Co-Train | Two-Stage Finetune |
|---|---|---|---|---|
| LIBERO-Spatial | Failed | 79 | 86.3 | 92.1 |{{< /table-caption >}}
> 🔼 표 4는 논문의 실험 부분에서 LIBERO-Spatial 작업 세트에 대해 서로 다른 훈련 전략들을 비교 분석한 결과를 보여줍니다.  여러가지 훈련 방법(전체 모델을 처음부터 훈련, 일반적인 비디오 생성기 사전 훈련된 가중치로 초기화 후 훈련, 비디오 생성 손실과 로봇 정책 행동 손실을 동시에 최적화하며 훈련, 사전 훈련된 비디오 생성기를 사용 후 로봇 정책 손실만 최적화하며 미세 조정하는 방식)을 적용하여 로봇 작업 성공률을 측정했습니다. 이 표는 다양한 훈련 전략의 효과를 비교하여 최적의 훈련 방법을 제시하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Performance comparison of different training strategies on the LIBERO-Spatial task suite. The metrics are the task success rates.
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