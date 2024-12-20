---
title: "VidTok: A Versatile and Open-Source Video Tokenizer"
summary: "VidTok: 오픈소스 고성능 비디오 토크나이저가 연속 및 이산 토큰화에서 최첨단 성능을 달성하며, 효율적인 학습 전략과 혁신적인 양자화 기법을 통해 영상 생성 및 이해 연구에 새로운 가능성을 열었습니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Video Understanding", "🏢 Microsoft Research",]
showSummary: true
date: 2024-12-17
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.13061 {{< /keyword >}}
{{< keyword icon="writer" >}} Anni Tang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-19 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.13061" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.13061" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/vidtok-a-versatile-and-open-source-video" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

최근 몇 년 동안 비디오 생성과 이해 분야는 비약적인 발전을 이루었지만, 픽셀 수준의 표현에 내재된 중복성 때문에 효율적인 모델 학습에 어려움이 있었습니다. 이러한 문제를 해결하기 위해, 고성능의 오픈소스 비디오 토크나이저가 요구되어 왔습니다. 기존의 비디오 토크나이저들은 연속 또는 이산 토큰화 중 하나에만 집중하거나, 훈련 안정성 및 코드북 붕괴 문제를 해결하지 못했습니다. 

본 논문에서는 VidTok이라는 새로운 비디오 토크나이저를 제안합니다. VidTok은 기존 방식보다 **모델 아키텍처, 고급 양자화 기법, 개선된 학습 전략** 등 여러 측면에서 발전된 기능을 제공합니다. 특히, **Finite Scalar Quantization (FSQ)**을 이산 토큰화에 통합하여 훈련 안정성 문제를 해결하고, **2단계 학습 과정 및 저감된 프레임 레이트**를 활용하여 훈련 효율성을 높였습니다. 다양한 평가 지표(PSNR, SSIM, LPIPS, FVD)에서 최첨단 성능을 달성하여 VidTok의 우수성을 입증했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} VidTok은 연속 및 이산 토큰화 모두에서 최첨단 성능을 달성했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 효율적인 학습 전략(2단계 학습 및 저감된 프레임 레이트 사용)과 혁신적인 양자화 기법(FSQ)을 통해 VidTok은 비용 효율적인 모델 학습을 가능하게 했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} VidTok은 오픈소스로 공개되어, 연구자들이 쉽게 접근하고 활용하여 영상 생성 및 이해 분야의 연구 발전에 크게 기여할 수 있습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **비디오 토크나이저 분야의 혁신적인 기술**을 제시하여, **영상 생성 및 이해 연구에 획기적인 발전**을 가져올 수 있습니다. **오픈소스로 공개**되어 접근성이 높고, 다양한 평가 지표에서 **최첨단 성능**을 입증하여 연구자들에게 큰 영향을 미칠 것으로 예상됩니다. 특히, **효율적인 학습 전략 및 고급 양자화 기법**을 통해 비용 효율적인 모델 개발을 가능하게 하고, 다양한 응용 분야에 적용 가능성을 보여줍니다. 따라서, 영상 처리 및 인공지능 분야 연구자들에게 필수적인 자료가 될 것입니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.13061/extracted/6076804/imgs/radar.png)

> 🔼 그림 1은 VidTok 모델과 최첨단 방법들을 대상으로, PSNR, SSIM, LPIPS, FVD의 네 가지 지표를 사용하여 이산 및 연속 토큰화 성능을 정량적으로 비교한 결과를 보여줍니다. 모든 성능 지표는 공정하고 비교 가능한 결과를 얻기 위해 일관된 평가 프로토콜을 사용하여 실험을 통해 얻었습니다. 차트 영역이 클수록 모든 지표에서 성능이 우수함을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Illustration of the quantitative comparison of discrete and continuous tokenization performance across our VidTok model and state-of-the-art methods, evaluated using four metrics: PSNR, SSIM, LPIPS, and FVD. All performance metrics are obtained through experiments conducted under a consistent evaluation protocol to ensure fairness and comparability. Larger chart areas correspond to better performance across all metrics.
> </details>





{{< table-caption >}}
| Method | Regularizer | Param. | MCL-JCV PSNR↑ | MCL-JCV SSIM↑ | MCL-JCV LPIPS↓ | MCL-JCV FVD↓ | WebVid-Val PSNR↑ | WebVid-Val SSIM↑ | WebVid-Val LPIPS↓ | WebVid-Val FVD↓ |
|---|---|---|---|---|---|---|---|---|---|---|
| MAGVIT-v2* | LFQ - 262,144 | - | 26.18 | - | 0.104 | - | - | - | - | - |
| OmniTokenizer | VQ - 8,192 | 51M | 26.93 | 0.841 | 0.165 | 232.7 | 26.26 | 0.883 | 0.112 | 48.46 |
| Cosmos-DV | FSQ - 64,000 | 101M | 28.07 | 0.743 | 0.212 | 227.7 | 29.39 | 0.741 | 0.170 | 57.97 |
| Ours-FSQ | FSQ - 32,768 | 157M | 29.16 | 0.854 | 0.117 | 196.9 | 31.04 | 0.883 | 0.089 | 45.34 |
| Ours-FSQ | FSQ - 262,144 | 157M | 29.82 | 0.867 | 0.106 | 160.1 | 31.76 | 0.896 | 0.080 | 38.17 |
| CV-VAE | KL - 4chn | 182M | 28.56 | 0.823 | 0.163 | 334.2 | 30.79 | 0.863 | 0.116 | 70.39 |
| Open-Sora-v1.2 | KL - 4chn | 393M | 29.44 | 0.766 | 0.164 | 350.7 | 31.02 | 0.764 | 0.137 | 112.34 |
| Open-Sora-Plan-v1.2 | KL - 4chn | 239M | 29.07 | 0.839 | 0.131 | 201.7 | 30.85 | 0.869 | 0.101 | 44.76 |
| Ours-KL | KL - 4chn | 157M | 29.64 | 0.852 | 0.114 | 194.2 | 31.53 | 0.878 | 0.087 | 36.88 |
| CogVideoX | KL - 16chn | 206M | 33.76 | 0.930 | 0.076 | 93.2 | 36.22 | 0.952 | 0.049 | 15.30 |
| Cosmos-CV | AE - 16chn | 101M | 31.27 | 0.817 | 0.149 | 153.7 | 33.04 | 0.818 | 0.107 | 23.85 |
| Ours-KL | KL - 16chn | 157M | 35.04 | 0.942 | 0.047 | 78.9 | 37.53 | 0.961 | 0.032 | 9.12 |{{< /table-caption >}}

> 🔼 표 1은 최첨단 비디오 토크나이저들과의 정량적 비교 결과를 보여줍니다. 모든 평가 모델은 인과적이며 4x8x8의 비디오 압축 비율을 갖습니다. 대부분의 모델에 대한 입력 해상도는 17x256x256이지만, 원 논문에 보고된 바와 같이 MAGVIT-v2*는 17x360x640에서 평가되었습니다. 테스트 데이터의 샘플링 속도는 30FPS입니다. 최고 및 두 번째로 좋은 수치는 각각 굵은 글씨체와 밑줄로 강조 표시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Quantitative comparison with the state-of-the-art video tokenizers. All evaluated models are causal and have a video compression ratio of 4×8×84884\times 8\times 84 × 8 × 8. The input resolution for most models is 17×256×2561725625617\times 256\times 25617 × 256 × 256, except for MAGVIT-v2∗, which is evaluated on 17×360×6401736064017\times 360\times 64017 × 360 × 640 as reported in the original study. The sample rate of testing data is 30 FPS. We highlight the best and the second-best numbers in bold and underline respectively.
> </details>





### In-depth insights


#### VidTok's Architecture
VidTok의 아키텍처는 공간 및 시간적 샘플링을 분리하여 계산 복잡도를 줄이면서 재구성 품질을 유지하는 데 중점을 둡니다. **2D 합성곱은 공간적 업/다운샘플링 모듈에 사용되고, AlphaBlender 연산자는 시간적 업/다운샘플링 모듈에 사용됩니다.** 나머지 부분은 정보 융합을 위해 3D 합성곱을 활용합니다.  **고급 양자화 기법으로 기존 벡터 양자화(VQ)의 훈련 불안정성 및 코드북 붕괴 문제를 해결하기 위해 유한 스칼라 양자화(FSQ)를 통합합니다.** 이는 암시적 코드북을 직접 최적화하여 성능을 크게 향상시킵니다. 또한, **두 단계 훈련 전략** (저해상도 비디오로 사전 훈련 후 고해상도 비디오로 디코더 미세 조정)과 **감소된 프레임 속도** 사용으로 훈련 효율성을 개선합니다. 이러한 발전을 통해 VidTok은 다양한 평가 지표에서 우수한 성능을 달성합니다.

#### Quantization Methods
본 논문에서는 영상 토크나이저의 핵심 구성 요소인 양자화 기법에 대한 심도있는 논의가 부족합니다. 하지만, **비트율을 줄이면서 주요 정보 손실을 최소화하는 효과적인 양자화 방법의 중요성**을 간접적으로 언급하고 있습니다. 특히, 기존의 벡터 양자화(VQ)의 한계를 지적하며, **훈련 불안정성과 코드북 붕괴 문제를 해결하기 위해 유한 스칼라 양자화(FSQ) 기법을 제안**하고 있습니다. FSQ는 각 스칼라 값을 미리 정의된 작은 값 집합으로 독립적으로 양자화하여 코드북 학습이 필요없고, 훈련 안정성을 높이는 장점을 제공합니다.  **본 논문은 FSQ가 코드북 활용률, 재구성 품질, 훈련 안정성 측면에서 기존 벡터 양자화보다 우수한 성능**을 보임을 실험적으로 확인했습니다.  하지만,  다양한 양자화 방법에 대한 비교 분석이 부족하여, FSQ의 성능 우위를 더욱 명확히 뒷받침할 필요가 있습니다. 또한, **향후 연구를 위해서는 다양한 양자화 기법에 대한 폭넓은 실험과 비교 분석**이 필요합니다. 이를 통해,  주어진 리소스와 응용 분야에 적합한 최적의 양자화 기법을 선택하는 지침을 제시할 수 있습니다.

#### Training Strategies
본 논문에서 제시된 비디오 토크나이저의 훈련 전략은 **두 단계 훈련 과정**과 **감소된 프레임 레이트 사용**이라는 두 가지 핵심 요소로 구성됩니다. 첫째, **저해상도 비디오를 이용한 초기 사전 훈련**을 통해 모델의 안정적인 학습을 유도하고, 이후 **고해상도 비디오를 이용한 미세 조정**으로 성능을 향상시키는 방식입니다. 이는 컴퓨팅 자원을 효율적으로 사용하고 훈련 시간을 단축하는 데 기여합니다. 둘째, **감소된 프레임 레이트**를 통해 모델의 모션 다이나믹스 학습 효율을 높여, 움직임 정보를 더욱 효과적으로 표현하도록 합니다. 이는 훈련 데이터의 크기를 줄이는 동시에 모델의 모션 표현 능력을 향상시키는 효과를 가져옵니다.  이러한 두 가지 전략을 통해 훈련 과정의 안정성과 효율성을 높이고, 최종적으로 비디오 토크나이저의 성능을 향상시킬 수 있었습니다.

#### Ablation Studies
본 논문에서 제시된 어떤 방법이나 모델의 성능에 대한 깊이 있는 이해를 위해 **절제 연구(Ablation Study)**는 매우 중요합니다.  **절제 연구는 특정 구성 요소나 하이퍼파라미터를 제거하거나 변경하여 모델의 성능 변화를 측정함으로써 각 요소의 기여도를 정량적으로 분석**하는 데 초점을 맞춥니다. 이를 통해 연구자들은 모델의 설계 결정이 최종 성능에 미치는 영향을 명확히 파악하고, **모델의 강점과 약점을 명확하게 드러낼 수 있습니다.**  **비교 실험을 통해 어떤 요소가 모델의 성능 향상에 가장 크게 기여했는지, 어떤 요소가 오히려 성능 저하를 야기했는지** 등을 알 수 있으며,  **개선 방향을 제시하는 데 유용한 통찰력을 제공**합니다. 따라서, 본 논문의 절제 연구는 제시된 방법의 핵심 구성요소의 중요성을 명확하게 보여주는 동시에, 추가적인 연구를 위한 방향성을 제시하는 데 필수적입니다.  **특히, 다양한 변수 조합에 따른 성능 변화를 분석함으로써 모델의 견고성 및 일반화 능력을 평가**할 수 있습니다.

#### Future Directions
본 논문에서 제시된 VidTok 모델은 비디오 토크나이저 분야에서 중요한 발전이지만, **향후 연구 방향**은 여전히 많습니다.  **더욱 효율적인 토크나이징 기법**의 개발은 필수적이며, **다양한 비디오 형식과 해상도**에 대한 적응력 향상 또한 중요합니다.  **대규모 데이터셋**을 활용한 훈련을 통해 성능을 더욱 개선하고, **다양한 하드웨어 플랫폼**에 대한 최적화 연구도 필요합니다.  **다른 모달리티와의 통합**, 예를 들어 텍스트나 오디오와의 결합을 통한 다중 모달 비디오 이해 모델 개발도 중요한 연구 방향입니다.  **새로운 평가 지표** 개발을 통해 비디오 토크나이저의 성능을 보다 정확하고 포괄적으로 평가하는 연구도 필요합니다. 마지막으로, **윤리적이고 책임감 있는 비디오 생성 및 활용**에 대한 고려가 중요하며, 이를 위한 연구가 필요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.13061/x1.png)

> 🔼 그림 2는 비디오 토크나이저의 개요를 보여줍니다. 입력 비디오는 인코더에 의해 압축된 잠재 공간(latent space)의 토큰으로 변환됩니다.  이 잠재 공간에서는 정규화(regularization)가 적용되어 과적합을 방지하고 새로운 데이터 생성 능력을 향상시킵니다.  잠재 토큰은 디코더에 의해 원본 비디오로 재구성됩니다.  토큰은 연속적(continuous)이거나 이산적(discrete)일 수 있으며, 이는 인코더-디코더 아키텍처의 설계에 영향을 미칩니다.  이 그림은 비디오 토크나이저의 일반적인 아키텍처를 간략하게 시각적으로 보여주는 개념도입니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: An overview of video tokenizers.
> </details>



![](https://arxiv.org/html/2412.13061/x2.png)

> 🔼 그림 3은 논문에서 제안하는 향상된 모델 아키텍처를 보여줍니다.  이 그림은 비디오 토크나이저의 인코더와 디코더를 포함한 전체 구조를 보여주는 상세한 다이어그램입니다.  특히, 입력 비디오의 시간적 및 공간적 차원을 처리하는 방법과 여러 컨볼루션 블록(3D, 2D+1D) 및 AlphaBlender 연산자를 활용하는 방식을 보여줍니다.  입력 비디오의 크기가 T×H×W = 17×256×256 이고 시간적 압축률이 4, 공간적 압축률이 8이라고 가정하면, 중간 표현의 크기는 T×H×W = 5×32×32로 줄어듭니다. 이는 인코더를 통해 입력 비디오를 효율적으로 압축하여 처리하는 과정을 시각적으로 보여줍니다.  다이어그램은 다양한 컨볼루션 블록과 AlphaBlender 연산자의 연결을 자세하게 나타내어, 모델의 구조와 동작 방식에 대한 이해를 돕습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: The improved model architecture. In the context of a causal setting, consider an input with dimensions T×H×W=17×256×256𝑇𝐻𝑊17256256T\times H\times W=17\times 256\times 256italic_T × italic_H × italic_W = 17 × 256 × 256. Assuming a temporal compression factor of 4444 and a spatial compression factor of 8888, the intermediate latent representation is reduced to dimensions T×H×W=5×32×32𝑇𝐻𝑊53232T\times H\times W=5\times 32\times 32italic_T × italic_H × italic_W = 5 × 32 × 32.
> </details>



![](https://arxiv.org/html/2412.13061/x3.png)

> 🔼 그림 4는 벡터 양자화(VQ)와 유한 스칼라 양자화(FSQ) 방법을 보여줍니다. 왼쪽은 VQ-VAE (Van Den Oord 외, 2017)에서 사용되는 벡터 양자화(VQ)를 나타냅니다. VQ는 고차원 벡터를 코드북에 있는 이산 벡터로 매핑하는 과정을 보여줍니다. 이는 입력 데이터를 압축하고 표현하는 데 유용하지만, 코드북 붕괴와 같은 문제가 발생할 수 있습니다. 오른쪽은 본 논문에서 제안하는 방법인 FSQ(Mentzer 외, 2024)를 보여줍니다. FSQ는 각 스칼라 값을 유한 개의 이산 값으로 양자화하여 VQ의 단점을 해결합니다. 코드북을 학습할 필요가 없어 훈련이 더 안정적이며, 코드북 붕괴 문제를 완화합니다. 두 방법 모두 고차원 데이터를 저차원 이산 표현으로 변환하여 효율적인 처리 및 압축을 가능하게 하지만, VQ보다 FSQ가 더 안정적이고 효율적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Left: Vector Quantization (VQ) employed in Vector Quantised-Variational AutoEncoder (VQ-VAE) (Van Den Oord et al., 2017). Right: Finite Scalar Quantization (FSQ) (Mentzer et al., 2024) utilized in our model.
> </details>



![](https://arxiv.org/html/2412.13061/extracted/6076804/imgs/results/full_comp.png)

> 🔼 그림 5는 본 논문에서 제시된 VidTok 모델과 최첨단 비디오 토크나이저들의 정성적 비교 결과를 보여줍니다.  여러 개의 비디오 클립에 대해, 지상 진실(Ground Truth)과 각 모델의 재구성 결과를 나란히 보여줌으로써, VidTok을 포함한 각 모델의 비디오 재구성 품질을 시각적으로 비교할 수 있도록 합니다.  특히,  세부적인 디테일과 동작 표현의 정확성 측면에서 VidTok의 성능을 직관적으로 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Qualitative comparison with the state-of-the-art video tokenizers.
> </details>



![](https://arxiv.org/html/2412.13061/extracted/6076804/imgs/results/fps8_fps3.png)

> 🔼 그림 6은 훈련 데이터의 프레임 속도가 모델 성능에 미치는 영향을 보여줍니다. 두 번째 줄은 8FPS의 훈련 데이터를 사용한 테스트 결과를, 세 번째 줄은 3FPS의 훈련 데이터를 사용한 테스트 결과를 보여줍니다. 결과는 감소된 프레임 속도의 훈련 데이터를 사용하면 모델이 동작 역학을 효과적으로 포착하는 능력이 향상됨을 보여줍니다. 즉, 프레임 속도를 낮추면 모델이 움직임을 더 잘 학습하고 재구성 성능이 향상된다는 것을 의미합니다.  이는 낮은 프레임 속도에서도 중요한 정보가 손실되지 않고, 오히려 불필요한 정보가 제거되어 모델 학습 효율이 높아지기 때문으로 해석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: The influence of different sample rates on model performance during training. The second row presents the test results obtained using training data with a sample rate of 8 FPS, while the third row shows the test results using training data with a sample rate of 3 FPS. The results demonstrate that employing training data with reduced frame rates enhances the model’s capacity to effectively capture motion dynamics.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | Param. | FLOPs | PSNR↑ | SSIM↑ | LPIPS↓ | FVD↓ |
|---|---|---|---|---|---|---|
| Variant 1 | 245M | 16.98 T | 29.39 | 0.847 | 0.117 | 176.9 |
| Variant 2 | 142M | 7.17 T | 29.36 | 0.846 | 0.119 | 185.7 |
| Variant 3 | 126M | 10.18 T | 29.26 | 0.846 | 0.120 | 200.6 |
| Ours | 157M | 10.35 T | 29.64 | 0.852 | 0.114 | 194.2 |{{< /table-caption >}}
> 🔼 표 2는 비디오 토크나이저 모델 아키텍처에 대한 ablation study 결과를 보여줍니다. 세 가지 변형 모델이 비교됩니다. Variant 1은 완전한 3D 아키텍처를 사용하고, Variant 2는 AlphaBlender를 제외하고, Variant 3은 3D 아키텍처를 사용하지 않습니다. 모든 설정에서 'KL - 4chn'을 정규화자로 사용했습니다. 표에는 각 변형 모델의 매개변수 수, FLOPS, PSNR, SSIM, LPIPS, FVD 값이 제시되어 모델 아키텍처 변경이 성능에 미치는 영향을 정량적으로 분석합니다. 
> <details>
> <summary>read the caption</summary>
> Table 2: Ablation study on the model architecture. Variant 1: fully 3D architecture. Variant 2: w/o AlphaBlender. Variant 3: w/o 3D architecture. We use ‘KL - 4chn’ as regularizer for all settings.
> </details>

{{< table-caption >}}
| Regularizer | w/ R.L. | PSNR↑ | SSIM↑ | LPIPS↓ | FVD↓ | U.R.↑ |
|---|---|---|---|---|---|---|
| VQ - 262,144 | 
<span class="ltx_ERROR undefined">\usym</span>2613 | - | - | - | - | - |
| VQ - 262,144 | ✓ | 23.22 | 0.657 | 0.336 | 960.5 | 0.2% |
| LFQ - 262,144 | 
<span class="ltx_ERROR undefined">\usym</span>2613 | 23.91 | 0.688 | 0.251 | 619.8 | 4.2% |
| LFQ - 262,144 | ✓ | 28.04 | 0.833 | 0.133 | 208.1 | 99.9% |
| FSQ - 262,144 | 
<span class="ltx_ERROR undefined">\usym</span>2613 | 29.75 | 0.866 | 0.109 | 167.5 | 99.8% |
| FSQ - 262,144 | ✓ | 29.82 | 0.867 | 0.106 | 160.1 | 99.8% |
| FSQ - 32,768 | ✓ | 29.16 | 0.854 | 0.117 | 196.9 | 100.0% |
| FSQ - 4,096 | ✓ | 28.36 | 0.832 | 0.133 | 218.1 | 100.0% |{{< /table-caption >}}
> 🔼 표 3은 다양한 이산화 기법이 모델 성능에 미치는 영향을 분석한 결과를 보여줍니다.  VQ, LFQ, FSQ 세 가지 이산화 방법을 사용하여, 각각 규제 손실 적용 여부에 따른 성능 변화를 PSNR, SSIM, LPIPS, FVD 지표로 측정하였습니다.  또한, 코드북 활용률(U.R.)을 함께 제시하여, 각 이산화 기법의 효율성을 비교 분석하였습니다.  표에서 확인할 수 있듯이, 규제 손실을 적용하지 않은 VQ는 코드북 활용률이 매우 낮고 성능이 저조하지만, LFQ와 FSQ는 규제 손실 적용 여부와 관계없이 높은 코드북 활용률과 향상된 성능을 보여줍니다. 특히 FSQ는 모든 지표에서 가장 우수한 성능을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Analysis of the impact of discrete techniques on model performance. R.L. denotes Regularization Loss, while U.R. represents Utilization Rate.
> </details>

{{< table-caption >}}
| Sample Rate | First Stage | Second Stage | Fix Enc. | PSNR↑ | SSIM↑ | LPIPS↓ | FVD↓ | GPU Hours |
|---|---|---|---|---|---|---|---|---|
| 3 FPS | 256×256 | - | - | 29.19 | 0.843 | 0.127 | 174.9 | 3,072 |
| 3 FPS | 128×128 | - | - | 29.02 | 0.838 | 0.130 | 221.7 | 960 |
| 3 FPS | 128×128 | 256×256 | ✓ | 29.15 | 0.842 | 0.127 | 203.2 | 1,728 |
| 3 FPS | 128×128 | 256×256 | ✓ | 29.21 | 0.843 | 0.125 | 189.8 | 1,536 |
| 8 FPS | 128×128 | 256×256 | ✓ | 29.02 | 0.839 | 0.126 | 219.2 | 1,536 |{{< /table-caption >}}
> 🔼 표 4는 제안된 두 단계 학습 전략에 대한 비교 실험 결과를 보여줍니다. 공정한 비교를 위해 두 단계 모두 학습 데이터 세트 1을 사용했습니다. 모든 설정에서 'KL - 4chn' 정규화기를 사용했습니다. NVIDIA A100 GPU를 사용하여 측정한 학습 연산 비용(GPU 시간)이 표에 제시되어 있습니다. 표에는 프레임 속도, 첫 번째 단계의 해상도, 두 번째 단계의 해상도, 인코더 고정 여부, PSNR, SSIM, LPIPS, FVD, GPU 시간 등의 정보가 포함되어 있습니다. 다양한 프레임 속도와 해상도 조합에 따른 성능 변화를 분석하여 효율적인 학습 전략을 제시하고자 합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Ablation study on the proposed training strategy. To ensure a fair comparison, both stages use training data from Training Set 1. Across all configurations, the regularizer ‘KL - 4chn’ is employed. The training computational cost, measured in GPU hours, is evaluated using NVIDIA A100 GPUs.
> </details>

{{< table-caption >}}
Regularizer|Causal|Input Size|VCR|Latent Size|Param.|PSNR ↑|SSIM ↑|LPIPS ↓|FVD ↓
---|---|---|---|---|---|---|---|---|
KL - 4chn|✓|17×256×256|4×8×8|5×32×32|157M|29.64|0.852|0.114|194.2
KL - 4chn|✓|17×256×256|4×16×16|5×16×16|199M|25.05|0.711|0.228|549.1
KL - 4chn|✓|16×256×256|4×8×8|4×32×32|158M|30.60|0.876|0.098|157.9
KL - 4chn|✓|16×256×256|4×16×16|4×16×16|199M|26.06|0.751|0.190|423.2
KL - 8chn|✓|17×256×256|4×8×8|5×32×32|157M|31.83|0.897|0.083|109.3
KL - 16chn|✓|17×256×256|4×8×8|5×32×32|157M|35.04|0.942|0.047|78.9
KL - 8chn|✓|17×256×256|2×8×8|9×32×32|149M|33.86|0.928|0.057|80.7
KL - 4chn|✓|17×256×256|4×4×4|5×64×64|155M|34.78|0.941|0.051|87.2
FSQ - 4,096|✓|17×256×256|4×8×8|5×32×32|157M|28.36|0.832|0.133|218.1
FSQ - 32,768|✓|17×256×256|4×8×8|5×32×32|157M|29.16|0.854|0.117|196.9
FSQ - 262,144|✓|17×256×256|4×8×8|5×32×32|157M|29.82|0.867|0.106|160.1
FSQ - 262,144|✓|17×256×256|4×16×16|5×16×16|199M|25.38|0.738|0.206|430.1
FSQ - 262,144|✓|16×256×256|4×8×8|4×32×32|157M|30.78|0.889|0.091|132.1
FSQ - 262,144|✓|16×256×256|4×16×16|4×16×16|199M|26.37|0.772|0.171|357.0{{< /table-caption >}}
> 🔼 표 5는 다양한 구성을 갖춘 모델들을 제시합니다. 연속 및 이산 토큰화, 다양한 비디오 압축률(VCR), 그리고 인과적 및 비인과적 시나리오를 모두 포함합니다. 이러한 구성은 다양한 다운스트림 작업의 고유한 요구 사항을 충족하도록 설계되었습니다.  더 자세히 설명하자면, 이 표는 VidTok 모델의 다양한 변형을 요약하여 보여줍니다. 각 변형은 토큰화 방식(연속 또는 이산), 비디오 압축 비율, 그리고 인과관계(causal) 여부 등의 특징을 가지고 있습니다. 이러한 다양한 모델 변형은 다양한 하류 작업에 유연하게 대응할 수 있도록 설계되었음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Model summary. We offer a suite of models with diverse configurations, encompassing both continuous and discrete tokenization, various video compression ratios (VCR), and options for causal and non-causal scenarios. These configurations are designed to address the distinct requirements of various downstream tasks.
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