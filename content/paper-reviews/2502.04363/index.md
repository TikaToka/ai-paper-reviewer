---
title: "On-device Sora: Enabling Diffusion-Based Text-to-Video Generation for Mobile Devices"
summary: "On-device Sora: 스마트폰에서 텍스트 기반 고품질 비디오 생성을 가능하게 하는 혁신적인 기술!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Video Understanding", "🏢 Ulsan National Institute of Science and Technology",]
showSummary: true
date: 2025-02-05
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.04363 {{< /keyword >}}
{{< keyword icon="writer" >}} Bosung Kim et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-10 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.04363" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.04363" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/on-device-sora-enabling-diffusion-based-text" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

최근 생성 모델의 발전으로 텍스트 기반 고품질 비디오 생성이 가능해졌지만, 이는 일반적으로 고성능 GPU 기반의 대규모 데이터 센터 환경에서만 가능했습니다.  이는 비용이 많이 들고 프라이버시 문제와 클라우드 의존성 문제를 야기합니다. 따라서 모바일 환경에서 효율적인 비디오 생성 기술에 대한 필요성이 증가하고 있습니다.

본 연구에서는 스마트폰에서도 고품질 비디오 생성을 가능하게 하는 On-device Sora라는 새로운 프레임워크를 제시합니다.  연구진은 연산량을 줄이고 메모리 사용을 최적화하기 위해 세 가지 핵심 기술 (Linear Proportional Leap, Temporal Dimension Token Merging, Concurrent Inference with Dynamic Loading)을 개발했습니다.  실험 결과, On-device Sora는 고성능 GPU 기반 모델과 비교해도 우수한 성능을 보였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 스마트폰과 같은 모바일 기기에서 고품질 비디오를 생성하는 최초의 솔루션인 On-device Sora를 제시. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} Linear Proportional Leap(LPL), Temporal Dimension Token Merging(TDTM), Concurrent Inference with Dynamic Loading(CI-DL) 세 가지 새로운 기법을 통해 모바일 기기의 제한된 연산 및 메모리 자원을 효율적으로 사용. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} On-device Sora는 기존 고성능 GPU 기반 모델과 비교해도 손색없는 고품질 비디오를 생성하는 것을 실험적으로 입증하여, 모바일 기기에서의 고급 생성 기술 접근성을 높였습니다.  {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **모바일 기기에서의 효율적인 텍스트-비디오 생성을 가능하게 하는 최초의 솔루션**을 제시하여, **제한된 자원을 가진 모바일 기기에서도 고품질 비디오 생성이 가능함을 보여줍니다.** 이는 생성형 기술의 민주화에 크게 기여하며, 향후 연구에서 **모바일 기기에서의 고급 생성 기술의 발전**에 중요한 영향을 미칠 것입니다. 또한, 제시된 세 가지 기법 (LPL, TDTM, CI-DL)은 다른 유사한 모델에도 적용 가능하여, **다양한 응용 분야**에서 활용될 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.04363/x3.png)

> 🔼 그림 1은 Open-Sora의 작동 과정을 보여줍니다. 사용자의 텍스트 프롬프트를 입력받아 1) 프롬프트 임베딩 단계를 거쳐 텍스트를 벡터로 변환하고, 2) 잠재적 비디오 생성 단계에서 변환된 벡터를 기반으로 잠재적인 비디오 표현을 생성하며, 3) 비디오 디코딩 단계를 통해 잠재적 비디오 표현을 실제 비디오로 변환하는 과정을 세 단계로 나누어 설명합니다. 각 단계마다 사용되는 모델 (T5, STDiT, VAE)도 함께 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1. Open-Sora (Zheng et al., 2024) generates realistic videos from the user prompt (text) through three stages: 1) prompt embedding, 2) latent video generation, and 3) video decoding.
> </details>





{{< table-caption >}}
| Component | Iterations | Inference Time (s) | Total Latency (s) |
|---|---|---|---| 
| T5 (Raffel et al., 2020) | 1 | 110.505 | 110.505 |
| STDiT (Zheng et al., 2024) | 50 | 35.366 | 1768.320 |
| VAE (Doersch, 2016) | 1 | 135.047 | 135.047 |{{< /table-caption >}}

> 🔼 표 1은 Open-Sora 모델의 각 구성 요소(T5, STDiT, VAE)의 실행 횟수(반복 횟수)와 iPhone 15 Pro에서의 총 처리 시간을 보여줍니다.  Open-Sora는 본 논문에서 제안하는 On-device Sora의 기반 모델로 사용됩니다. 이 표는 On-device Sora의 성능 향상을 위한 세 가지 기법(Linear Proportional Leap, Temporal Dimension Token Merging, Concurrent Inference with Dynamic Loading)을 이해하는 데 중요한 역할을 합니다. 각 구성 요소의 실행 횟수와 처리 시간을 비교함으로써 On-device Sora에서의 성능 개선 효과를 정량적으로 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1. The number of executions (iterations) of each model component (i.e., T5 (Raffel et al., 2020), STDiT (Zheng et al., 2024), and VAE (Doersch, 2016)) in Open-Sora (Zheng et al., 2024) and their total latencies on iPhone 15 Pro (Apple, 2023).
> </details>





### In-depth insights


#### On-device Diffusion
본 논문에서 제시된 "온디바이스 확산(On-device Diffusion)" 개념은 모바일 기기에서의 효율적인 텍스트-비디오 생성을 위한 혁신적인 접근 방식을 의미합니다. **기존의 고성능 GPU 환경에 의존하던 텍스트-비디오 생성 모델을 모바일 기기에서도 실행 가능하게 하는 데 초점**을 맞추고 있습니다.  이는 제한된 연산 능력 및 메모리 용량을 갖는 모바일 환경에서 고품질 비디오 생성이라는 어려움을 극복하기 위해 **세 가지 핵심 기술 (Linear Proportional Leap, Temporal Dimension Token Merging, Concurrent Inference with Dynamic Loading)**을 제시하고 실험적으로 검증한 결과를 보여줍니다.  **각 기술은 연산량 감소, 메모리 효율 향상, 추론 속도 향상**이라는 목표를 달성하여, **온디바이스 비디오 생성의 실현 가능성 및 접근성을 크게 높였음**을 시사합니다. 특히, 개인정보 보호 및 클라우드 의존성 감소라는 측면에서도 중요한 의미를 지닌다고 할 수 있습니다.  향후 연구에서는 더욱 발전된 모바일 하드웨어(NPU 활용 등)와의 연동을 통한 성능 개선 및 더욱 다양한 모바일 기기에서의 확장성을 확보하는 연구가 필요할 것으로 예상됩니다.

#### Sora's Novel Methods
본 논문에서 제시된 On-device Sora는 모바일 환경에서의 텍스트 기반 비디오 생성의 어려움을 해결하기 위해 기존 Sora 모델을 효율적으로 개선한 세 가지 핵심 기법을 제시합니다. 첫째, **선형 비례 도약(LPL)**은 불필요한 디노이징 단계를 줄여 연산량을 감소시키고 처리 속도를 높입니다.  둘째, **시간 차원 토큰 병합(TDTM)**은 연속적인 토큰을 병합하여 메모리 사용량과 계산량을 줄이며, 효율적인 어텐션 메커니즘을 구현합니다.  셋째, **동시 추론 및 동적 로딩(CI-DL)**은 대규모 모델을 작은 블록으로 분할하여 메모리 제약을 극복하고 병렬 처리를 통해 추론 속도를 향상시킵니다. 이러한 세 가지 기법은 **모바일 기기의 제한된 자원 내에서도 고품질의 비디오 생성을 가능**하게 하여, 기존 클라우드 기반 시스템의 한계를 극복하고 폭넓은 접근성을 제공합니다. 특히, **개인 정보 보호 및 비용 절감** 측면에서도 상당한 장점을 제공하며, **모바일 및 임베디드 기기에서의 생성형 기술 대중화**에 기여할 것으로 기대됩니다.

#### Mobile Video Gen
모바일 기기에서의 비디오 생성(Mobile Video Gen)은 **계산 비용 및 메모리 제약**으로 인해 상당한 어려움을 겪는 분야입니다.  본 논문에서는 이러한 문제를 해결하기 위해 세 가지 혁신적인 기법을 제시합니다.  첫째, **선형 비례 도약(LPL)**은 비디오 확산 과정에서 불필요한 잡음 제거 단계를 줄여 효율성을 높입니다. 둘째, **시간 차원 토큰 병합(TDTM)**은 연속적인 토큰을 병합하여 어텐션 계층에서의 계산량을 최소화합니다. 마지막으로, **동시 추론 및 동적 로딩(CI-DL)**은 대규모 모델을 작은 블록으로 분할하여 메모리 제약을 효과적으로 해결합니다. 이러한 기법들을 통해, 스마트폰 수준의 기기에서도 고품질 비디오 생성을 가능하게 하여 접근성을 확대하고, 개인 정보 보호를 강화하며, 클라우드 의존성을 줄이고 비용을 절감할 수 있습니다. **특히, 기존의 고성능 GPU 환경에서만 가능했던 고품질 비디오 생성을 모바일 기기에서 구현**한 것은 매우 중요한 성과입니다.  **향후 연구**에서는 더욱 효율적인 모델 최적화 기법 및 다양한 모바일 기기에서의 성능 개선을 목표로 할 수 있을 것입니다.

#### Performance Analysis
본 논문은 모바일 기기에서의 효율적인 텍스트-비디오 생성을 위한 On-device Sora의 성능 분석에 초점을 맞춥니다. **iPhone 15 Pro에서의 실험 결과는 Open-Sora와 비교하여 고품질 비디오 생성 능력을 보여주며, 제안된 세 가지 기법(Linear Proportional Leap, Temporal Dimension Token Merging, Concurrent Inference with Dynamic Loading)의 효과를 입증합니다.** 특히, Linear Proportional Leap은 denoising 단계를 줄여 속도를 향상시키고, Temporal Dimension Token Merging은 token 처리 과정을 간소화하여 계산량을 감소시키며, Concurrent Inference with Dynamic Loading은 메모리 제약을 효과적으로 해결하여 고성능을 달성합니다.  **비디오 품질 측면에서는 Open-Sora 수준의 성능을 유지하면서 속도 향상을 달성한 점이 주목할 만합니다.**  **다양한 비교 실험을 통해 각 기법의 효과 및 전체 시스템의 성능 향상을 정량적으로 보여줌으로써, 제안된 On-device Sora의 실용성과 효율성을 강조합니다.**  향후 연구는 다양한 모바일 기기 및 더욱 발전된 모델 최적화 기법을 통해  **더욱 향상된 성능 및 확장성**을 확보하는 데 집중할 것으로 예상됩니다.

#### Future of Sora
Sora의 미래는 **모바일 및 임베디드 기기에서의 실시간 고품질 비디오 생성**으로 향하고 있습니다.  **On-device Sora**는 이러한 비전을 향한 중요한 첫걸음으로,  **제한된 자원 환경에서도 효율적인 비디오 생성을 가능하게** 합니다.  향후 발전 방향으로는 **더욱 작고 효율적인 모델 개발**, **NPU 활용 및 다양한 모바일 플랫폼 지원 확대**, **영상 품질 개선 및 다양한 생성 방식 지원**, **다중 모달 생성(텍스트와 이미지)** 등을 예상할 수 있습니다.  **개방형 소스 공유**를 통해 커뮤니티 기여를 장려하고, **상용화 및 서비스 확장**을 통해 더욱 많은 사용자에게 접근성을 높일 것입니다.  **개인정보보호 및 보안 강화**는 중요한 과제이며, 지속적인 연구개발을 통해 **사용자 경험을 극대화**하고, **차세대 생성 기술의 대중화**에 기여할 것으로 예상됩니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.04363/x4.png)

> 🔼 그림 2는 On-device Sora가 모바일 기기에서 효율적인 텍스트-비디오 생성을 가능하게 하는 세 가지 핵심 기법을 보여줍니다. 1) 선형 비례 도약(Linear Proportional Leap): 비디오 확산에서 과도한 잡음 제거 단계를 줄여 처리 속도를 높입니다. 2) 시간 차원 토큰 병합(Temporal Dimension Token Merging): 시간적으로 연속된 토큰을 병합하여 어텐션 계층에서의 계산량을 줄입니다. 3) 동시 추론 및 동적 로딩(Concurrent Inference with Dynamic Loading): 대용량 모델을 작은 블록으로 분할하여 메모리에 동시에 로딩하고 추론함으로써 제한된 메모리 용량 문제를 해결합니다. 이 그림은 On-device Sora의 작동 원리를 시각적으로 보여주는 개념도입니다.
> <details>
> <summary>read the caption</summary>
> Figure 2. On-device Sora enables efficient text-to-video generation directly on the device by employing three key approaches: 1) Linear Proportional Leap, 2) Temporal Dimension Token Merging, and 3) Concurrent Inference with Dynamic Loading.
> </details>



![](https://arxiv.org/html/2502.04363/x6.png)

> 🔼 그림 3은 Open-Sora 모델의 크기를 보여줍니다. T5(Raffel et al., 2020)는 18GB, STDiT(Zheng et al., 2024)는 4.5GB, VAE(Doersch, 2016)는 0.82GB입니다. 이는 iPhone 15 Pro(Apple, 2023)의 사용 가능한 메모리 용량인 3.3GB를 초과하는 크기입니다.  즉, Open-Sora 모델은 모바일 기기의 메모리 용량을 초과하여, 모바일 기기에서 직접 실행하는 데 어려움이 있음을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3. The size of Open-Sora models: T5 (Raffel et al., 2020) (18.00 GB), STDiT (Zheng et al., 2024) (4.50 GB), and VAE (Doersch, 2016) (0.82 GB), which exceeds the available memory capacity of iPhone 15 Pro (Apple, 2023) (3.3 GB).
> </details>



![](https://arxiv.org/html/2502.04363/x7.png)

> 🔼 그림 4는 K=30, n=15일 때의 궤적과 잠재적 시각화를 추상적으로 나타낸 그림입니다. (a)는 Liu et al.(2022)의 Rectified Flow를 사용하여 전체 30단계의 디노이징 과정을 거쳐 완전한 데이터를 생성하는 과정을 보여줍니다. (b)는 Liu et al.(2022)의 Rectified Flow를 사용하여 Linear Proportional Leap을 적용하지 않고 16단계의 디노이징 과정을 거쳤을 때, 큰 단계 크기(dtk)로 인해 분산이 커져 저품질의 데이터가 생성되는 것을 보여줍니다. (c)는 Linear Proportional Leap을 적용하여 16단계의 디노이징 과정을 거쳤을 때, (a)와 거의 동등한 데이터를 생성하는 것을 보여줍니다.  즉, Linear Proportional Leap이 효율적인 디노이징을 가능하게 함을 시각적으로 보여주는 그림입니다.
> <details>
> <summary>read the caption</summary>
> Figure 4. An abstracted illustration of trajectories and latent visualizations for K=30𝐾30K=30italic_K = 30 and n=15𝑛15n=15italic_n = 15: (a) Rectified Flow (Liu et al., 2022) with full k=30𝑘30k=30italic_k = 30 denoising steps, generating intact and complete data, (b) Rectified Flow (Liu et al., 2022) with n+1=16𝑛116n+1=16italic_n + 1 = 16 denoising steps without applying Linear Proportional Leap, resulting in low-quality data generation from variance with high step sizes (d⁢tk𝑑subscript𝑡𝑘dt_{k}italic_d italic_t start_POSTSUBSCRIPT italic_k end_POSTSUBSCRIPT), and (c) Linear Proportional Leap with n+1=15+1𝑛1151n+1=15+1italic_n + 1 = 15 + 1 denoising steps, producing data nearly equivalent to (a).
> </details>



![](https://arxiv.org/html/2502.04363/x8.png)

> 🔼 그림 5는 Open-Sora의 핵심 구성 요소인 STDiT 모델에서 추출한 두 연속적인 드리프트 벡터(v(Pn, tn)과 v(Pn-1, tn-1)) 사이의 코사인 유사도를 보여줍니다.  각 드리프트 벡터는 video generation 과정에서 특정 시간(tn 또는 tn-1)에 대한 video frame의 변화량을 나타냅니다.  그래프는 반복 횟수(denoising step)가 증가함에 따라 드리프트 벡터 간의 유사도가 어떻게 변하는지 보여줍니다.  빨간색 선(30 steps)과 파란색 선(50 steps)은 각각 30번과 50번의 denoising step을 거쳤을 때의 결과를 나타냅니다.  이 그래프를 통해, denoising step이 진행됨에 따라 드리프트 벡터 간의 유사도가 1에 가까워지는 것을 확인할 수 있으며, 이는 후반부의 드리프트 벡터들이 거의 선형적인 경향을 보임을 시사합니다. 이러한 선형적인 경향은 Linear Proportional Leap (LPL) 기법의 효율성을 뒷받침하는 근거가 됩니다. LPL은 이 선형적인 경향을 이용하여 video generation 과정의 denoising step을 줄임으로써 효율성을 높입니다.
> <details>
> <summary>read the caption</summary>
> Figure 5. An example of cosine similarities between two consecutive drifts estimated from STDiT (Zheng et al., 2024), i.e., 𝒗⁢(Pn,tn)𝒗subscript𝑃𝑛subscript𝑡𝑛\boldsymbol{v}(P_{n},t_{n})bold_italic_v ( italic_P start_POSTSUBSCRIPT italic_n end_POSTSUBSCRIPT , italic_t start_POSTSUBSCRIPT italic_n end_POSTSUBSCRIPT ) and 𝒗⁢(Pn−1,tn−1)𝒗subscript𝑃𝑛1subscript𝑡𝑛1\boldsymbol{v}(P_{n-1},t_{n-1})bold_italic_v ( italic_P start_POSTSUBSCRIPT italic_n - 1 end_POSTSUBSCRIPT , italic_t start_POSTSUBSCRIPT italic_n - 1 end_POSTSUBSCRIPT ) for 30 (red) and 50 steps (blue).
> </details>



![](https://arxiv.org/html/2502.04363/x9.png)

> 🔼 그림 6은 STDiT(Zheng et al., 2024)의 어텐션 레이어에서 시간적 차원을 따라 두 개의 연속된 토큰을 병합하고, 처리 후에 다시 분리하는 과정을 보여줍니다. 이를 통해 토큰의 크기는 절반으로 줄이고, 계산 복잡도는 최대 4분의 1까지 줄일 수 있습니다.  구체적으로는, 연속된 프레임들을 하나의 토큰으로 합쳐서 처리량을 줄이고, 이후 다시 원래대로 분리하여 시간적 정보를 유지합니다. 이 방법은 메모리 사용량을 줄이고, 속도를 향상시키는 효과가 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6. In attention layers of STDiT (Zheng et al., 2024), two consecutive tokens are merged along the temporal dimension and subsequently unmerged after processing, reducing the token size by half and the computational complexity up to a quarter.
> </details>



![](https://arxiv.org/html/2502.04363/x10.png)

> 🔼 그림 7은 Temporal Dimension Token Merging (TDTM) 기법을 설명하는 그림입니다. TDTM은 비디오 프레임들을 시계열적으로 묶어 토큰의 크기를 줄이는 기법입니다. 그림에서는 연속적인 두 프레임의 토큰을 평균내어 하나의 토큰으로 합치는 과정(Merge)과, attention 연산 후 다시 원래의 크기로 되돌리는 과정(Unmerge)을 보여줍니다. 이를 통해 attention 연산에 필요한 계산량을 줄여 처리 속도를 높입니다.
> <details>
> <summary>read the caption</summary>
> Figure 7. An illustration of the token merging and unmerging process over the temporal dimension.
> </details>



![](https://arxiv.org/html/2502.04363/x11.png)

> 🔼 그림 8은 모델 블록 로딩 및 추론 과정을 보여줍니다. (a)는 순차적 로딩 및 추론 방식으로, GPU가 각 블록을 로딩할 때까지 대기하며, 로딩이 완료된 후에야 실행을 시작합니다. 이로 인해 모델 추론의 전체 지연 시간이 크게 증가합니다. (b)는 제안된 병렬 처리 방식으로, CPU는 (i+1)번째 블록을 로딩하는 동안 GPU는 i번째 블록의 추론을 동시에 수행합니다. 이를 통해 CPU 및 GPU의 병렬 처리를 최대화하여 모델 추론의 지연 시간을 단축합니다.  각 블록의 로딩 및 추론 주기는 빨간색(로딩)과 검은색(추론) 상자로 표시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8. The block loading and inference cycles for (a) sequential loading and inference, and (b) concurrent inference.
> </details>



![](https://arxiv.org/html/2502.04363/x12.png)

> 🔼 그림 9는 본 논문에서 제안하는 On-device Sora와 기존의 Open-Sora (Zheng et al., 2024)를 사용하여 생성한 비디오의 예시를 보여줍니다. 두 모델 모두 '말라붙은 낙엽이 숲에서 타오르는 모습' 과 '여우원숭이 클로즈업' 이라는 두 가지 텍스트 프롬프트를 사용하여 68프레임, 256x256 해상도의 비디오를 생성했습니다. 이 그림은 On-device Sora가 다양한 시각적 콘텐츠를 생성할 수 있는 능력을 보여주는 시각적 증거로 사용됩니다.  On-device Sora가 생성한 비디오는 Open-Sora와 비교하여 비슷한 수준의 화질을 유지하면서도 모바일 기기에서 효율적으로 비디오를 생성할 수 있음을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 9. Example videos generated by On-device Sora and Open-Sora (Zheng et al., 2024) (68 frames, 256×256 resolution).
> </details>



![](https://arxiv.org/html/2502.04363/x13.png)

> 🔼 그림 10은 동시 추론과 함께 동적 로딩이 적용된 경우의 블록 로딩 및 추론 주기를 보여줍니다. 동적 로딩은 사용 가능한 메모리에 따라 모델 블록의 하위 집합을 메모리에 유지하는 동시에, CPU는 (i+1)번째 블록을 로딩하는 동안 GPU는 i번째 블록을 동시에 실행하는 동시 추론을 사용합니다. 이를 통해 블록 로딩 시간과 추론 시간의 겹침이 발생하여 전반적인 추론 지연 시간이 단축됩니다. 그림에서 빨간색 상자는 로딩 주기를 나타내고, 검은색 상자는 추론 주기를 나타냅니다. 동시 추론을 사용하면 GPU가 거의 유휴 상태가 되지 않고 블록 로딩 및 추론이 병렬로 수행됩니다. 이는 순차 로딩 및 추론에 비해 전체 추론 속도를 향상시킵니다. 동적 로딩은 CPU 및 GPU 사용률을 최적화하여 3.3GB의 제한된 메모리를 효율적으로 관리합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10. The block loading and inference cycle for Dynamic Loading applied with Concurrent Inference.
> </details>



![](https://arxiv.org/html/2502.04363/x14.png)

> 🔼 그림 11은 본 논문에서 제안된 On-device Sora와 Open-Sora (Zheng et al., 2024)를 사용하여 생성된 비디오를 VBench (Huang et al., 2024)를 이용하여 평가한 결과를 시각적으로 비교한 것입니다.  다양한 범주의 비디오(동물, 건축물, 음식, 사람, 라이프 스타일, 식물, 풍경, 차량)에 대해 On-device Sora와 Open-Sora가 생성한 비디오의 시각적 품질을 비교 분석하여, 각 비디오의 시간적 일관성, 배경 일관성, 깜박임, 움직임 부드러움, 역동성, 미적 품질, 영상 품질 등의 여러 요소를 평가한 결과를 보여줍니다. 이를 통해 On-device Sora의 성능과 Open-Sora와의 차이점을 명확하게 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 11. A visual comparison of videos generated by On-device Sora and Open-Sora (Zheng et al., 2024), evaluated using VBench (Huang et al., 2024).
> </details>



![](https://arxiv.org/html/2502.04363/x15.png)

> 🔼 그림 12는 본 논문의 4장에서 제안된 선형 비례 도약(LPL) 기법의 다양한 설정(표 3 참조)을 적용하여 생성된 비디오의 스냅샷을 보여줍니다. 각 비디오는 68프레임으로 구성되며, 해상도는 256x256 픽셀입니다. 그림은 LPL 설정에 따른 비디오의 시각적 차이를 보여주기 위한 예시로, 서로 다른 LPL 설정에서 생성된 비디오가 유사한 의미를 유지하면서도, 선형 비례 도약의 효과를 통해 생성 시간이 단축되는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 12. The snapshots of videos (68 frames, 256×256 resolution) applied with various LPL settings (Table 3).
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Iterations |
|---|---|{{< /table-caption >}}
> 🔼 표 2는 On-device Sora와 Open-Sora의 비디오 생성 성능을 비교 분석한 결과를 보여줍니다. VBench (Huang et al., 2024) 벤치마크를 사용하여 동물, 건축물, 음식, 인물, 생활 방식, 식물, 풍경, 차량 등 8가지 카테고리의 68프레임, 256x256 해상도 비디오에 대해 시간적 일관성, 배경 일관성, 깜빡임, 움직임 부드러움, 역동성, 미적 이미지 품질, 이미지 품질 등 다양한 지표로 평가하였습니다. 각 지표의 점수는 0에서 1 사이의 값으로 나타내며, 1에 가까울수록 성능이 우수함을 의미합니다. 이 표를 통해 On-device Sora가 Open-Sora와 비슷한 수준의 비디오 품질을 제공하면서도, 특히 역동성 측면에서 더 나은 성능을 보이는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2. The VBench (Huang et al., 2024) evaluation by category: On-device Sora vs. Open-Sora (Zheng et al., 2024) (68 frames, 256×256 resolution).
> </details>

{{< table-caption >}}
| Inference Time (s) |
|---|---|{{< /table-caption >}}
> 🔼 표 3은 Linear Proportional Leap (LPL)의 설정을 다르게 했을 때, 생성된 비디오의 화질과 속도 향상 정도를 보여줍니다.  LPL 설정은 전체 30단계의 denoising 과정 중 LPL을 적용한 단계의 수를 백분율(%)로 나타냅니다.  (예: 16/30 (53%)는 30단계 중 16단계에 LPL을 적용했다는 의미).  표에는 SSIM, FVD와 같은 비디오 화질 평가 지표와 함께, 각 LPL 설정에서  Open-Sora 대비 속도 향상 배수(Speedup)가 제시되어 있습니다.  Dynamic LPL 설정은 비디오 생성 과정 중 실시간으로 LPL 적용 여부를 결정하는 방식을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 3. The video quality and generation speedup under different settings of LPL (Linear Proportional Leap).
> </details>

{{< table-caption >}}
| Total Latency (s) |
|---|---|{{< /table-caption >}}
> 🔼 표 4는 TDTM(Temporal Dimension Token Merging)에서 토큰 병합 단계를 다르게 했을 때 비디오 품질과 속도 향상을 보여줍니다.  다양한 병합 단계(전체 30단계 중 일부 단계만 병합)에서 생성된 비디오의 품질을 SSIM, FVD, VBench 세 가지 지표로 평가하고, 병합 단계가 증가함에 따라 속도 향상이 어떻게 달라지는지 보여줍니다.  각 지표의 평균 점수와 속도 향상 배수를 제시하며, 비디오 품질과 속도 향상 간의 상관관계를 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 4. The video quality and speedup under different merging steps of TDTM (Temporal Dimension Token Merging).
> </details>

{{< table-caption >}}
| Category | Method | Temporal Quality ↑ | Temporal Quality ↑ | Temporal Quality ↑ | Temporal Quality ↑ | Temporal Quality ↑ | Frame-Wise Quality ↑ | Frame-Wise Quality ↑ |
|---|---|---|---|---|---|---|---|---|
| Animal | Open-Sora | 0.97 | 0.98 | 0.99 | 0.99 | 0.15 | 0.51 | 0.56 |
|  | On-device Sora | 0.95 | 0.97 | 0.99 | 0.99 | 0.28 | 0.48 | 0.55 |
| Architecture | Open-Sora | 0.99 | 0.98 | 0.99 | 0.99 | 0.05 | 0.53 | 0.60 |
|  | On-device Sora | 0.98 | 0.98 | 0.99 | 0.99 | 0.12 | 0.49 | 0.56 |
| Food | Open-Sora | 0.97 | 0.97 | 0.99 | 0.99 | 0.26 | 0.52 | 0.60 |
|  | On-device Sora | 0.95 | 0.97 | 0.99 | 0.99 | 0.38 | 0.48 | 0.53 |
| Human | Open-Sora | 0.96 | 0.97 | 0.99 | 0.99 | 0.38 | 0.48 | 0.57 |
|  | On-device Sora | 0.96 | 0.96 | 0.99 | 0.99 | 0.43 | 0.48 | 0.55 |
| Lifestyle | Open-Sora | 0.97 | 0.97 | 0.99 | 0.99 | 0.23 | 0.45 | 0.56 |
|  | On-device Sora | 0.96 | 0.97 | 0.99 | 0.99 | 0.25 | 0.45 | 0.53 |
| Plant | Open-Sora | 0.98 | 0.98 | 0.99 | 0.99 | 0.15 | 0.50 | 0.58 |
|  | On-device Sora | 0.97 | 0.98 | 0.99 | 0.99 | 0.16 | 0.46 | 0.55 |
| Scenery | Open-Sora | 0.98 | 0.98 | 0.99 | 0.99 | 0.10 | 0.50 | 0.50 |
|  | On-device Sora | 0.97 | 0.98 | 0.99 | 0.99 | 0.17 | 0.48 | 0.47 |
| Vehicles | Open-Sora | 0.97 | 0.97 | 0.99 | 0.99 | 0.37 | 0.48 | 0.54 |
|  | On-device Sora | 0.94 | 0.96 | 0.98 | 0.99 | 0.44 | 0.47 | 0.49 |{{< /table-caption >}}
> 🔼 표 5는 세 가지 제안된 방법(LPL, TDTM, CI-DL)을 개별적으로 적용했을 때와 세 가지 방법을 모두 결합했을 때(모두)의 비디오 생성 지연 시간(초)을 보여줍니다.  LPL은 15번째 디노이징 단계에서 활성화되었고, TDTM은 모든 단계에 적용되었습니다. 세 번의 독립적인 실험 결과의 평균값을 보고합니다. STDiT와 Total은 지연 시간이 STDiT에 대해서만 측정되었는지, 아니면 T5와 VAE를 포함한 전체 비디오 생성 과정에 대해서 측정되었는지 여부를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 5. Ablation study on video generation latency (s). ‘All’ denotes the combined application of LPL, TDTM, and CI-DL.
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