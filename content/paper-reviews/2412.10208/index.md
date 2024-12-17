---
title: "Efficient Generative Modeling with Residual Vector Quantization-Based Tokens"
summary: "ResGen, 고품질 생성과 빠른 샘플링 속도를 모두 달성하는 효율적인 RVQ 기반 생성 모델."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Vision-Language Models", "🏢 NVIDIA Research",]
showSummary: true
date: 2024-12-13
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.10208 {{< /keyword >}}
{{< keyword icon="writer" >}} Jaehyeon Kim et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-16 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.10208" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.10208" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/efficient-generative-modeling-with-residual" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

고품질 생성을 위한 벡터 양자화(VQ) 기반 생성 모델의 등장. 깊이 있는 토큰 사용으로 충실도 높은 데이터 생성 가능. 그러나 토큰 수 증가는 추론 속도 저하 초래. RVQ는 짧은 길이지만 깊은 계층 구조 토큰 사용. 기존 autoregressive 모델은 샘플링 복잡도 증가 문제 발생. ResGen은 RVQ 기반 토큰을 사용하여 고품질 생성과 빠른 샘플링 속도를 모두 달성. 개별 토큰 대신 집합 토큰의 벡터 임베딩을 직접 예측. 샘플링 복잡도를 시퀀스 길이 및 깊이에서 분리. 토큰 마스킹 및 멀티토큰 예측 메커니즘. 이산 확산 프로세스 및 변이 추론을 사용한 확률적 프레임워크 내에서 공식화. 조건부 이미지 생성 및 제로샷 텍스트 음성 변환 합성에서 최첨단 모델과 비교할 수 있는 성능 입증.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} ResGen은 RVQ 기반 토큰으로 고품질 생성과 빠른 샘플링 속도를 달성합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} ResGen은 마스크된 토큰 예측을 이산 확산 프로세스 및 변이 추론으로 공식화합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} ResGen은 조건부 이미지 생성 및 제로샷 텍스트 음성 변환 합성에서 최첨단 모델과 비교할 수 있는 성능을 보입니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**ResGen**, RVQ 기반 생성 모델링에 효율적인 솔루션 제공. 토큰 깊이와 샘플링 속도 간의 균형 문제 해결. KV 캐싱, FSQ 지원, 이론적 분석 등 추가 연구 방향 제시. 이미지 생성 및 텍스트 음성 변환 합성에서 성능 향상. **다양한 분야 연구자에게 새로운 연구 가능성 제시.**

------
#### Visual Insights



![](https://arxiv.org/html/2412.10208/x1.png)

> 🔼 이 그림은 ResGen의 마스크 및 예측 프로세스를 보여줍니다. 상단 그림은 순방향 마스킹(오른쪽에서 왼쪽으로 진행)과 역방향 마스킹 해제(왼쪽에서 오른쪽으로 진행) 과정을 간략히 보여줍니다. 흰색 상자는 마스크된 토큰을, 색상이 있는 상자는 마스크가 해제된 토큰을 나타냅니다.  하단 그림은 역방향 마스킹 해제 과정을 자세히 보여줍니다. 마스크된 RVQ 토큰에서 시작하여 ResGen은 먼저 누적 RVQ 임베딩을 예측합니다. 예측된 임베딩은 양자화되고 다시 부분적으로 마스크됩니다. 이러한 반복적인 과정을 통해 마스크된 토큰의 값이 예측되고 채워지며, 최종적으로 전체 토큰 시퀀스가 완성됩니다. 각 반복에서 예측은 누적 임베딩을 기반으로 이루어지며, 이는 토큰의 계층적 구조를 효율적으로 처리하는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: An overview of the forward masking and reverse unmasking processes is shown at the top, with a detailed depiction of the reverse unmasking process below. In the top figure, forward masking proceeds from right to left, incrementally masking more tokens, while reverse unmasking progresses from left to right, iteratively revealing the masked tokens. White boxes denote masked tokens and colored boxes represent tokens that have been uncovered. The bottom figure illustrates the reverse unmasking process in detail. Starting from masked residual vector quantization (RVQ) tokens, our method first predicts cumulative RVQ embeddings. These embeddings are then quantized and partially masked again. Through a series of iterations, each round predicts the values of the masked tokens and replaces them until the entire token sequence is filled.
> </details>





{{< table-caption >}}
| Model | Code length | Params | FID (w/o CFG) ↓ | FID (w/ CFG) ↓ | Maximum batch size ↑ | 
|---|---|---|---|---|---| 
| MaskGiT | 256 | 277M | 6.18* | - | - | 
| DiT-XL/2 | 256 | 675M | 9.62* | 2.27* | 1159 | 
| VAR-d16 | 256 | 310M | 12.18 | 3.30* | 247 | 
| VAR-d20 | 256 | 600M | 8.60 | 2.57* | 148 | 
| VAR-d24 | 256 | 1.0B | 6.43 | 2.09* | 102 | 
| VAR-d30 | 256 | 2.0B | 5.31 | 1.92* | 60 | 
| MAR-B | 256 | 208M | 3.48* | 2.31* | 1738 | 
| MAR-L | 256 | 479M | <u>**2.60***</u> | <u>**1.78***</u> | 1167 | 
| MAR-H | 256 | 943M | **2.35*** | **1.55*** | 812 | 
| RQ-Transformer | 64 | 1.4B | 8.71* | 3.89* | 1151 | 
| RQ-Transformer | 64 | 3.8B | 7.55* | 3.80* | 390 | 
| ResGen-d8 | 64 | 574M | 6.56 | 2.71 | **1995** | 
| ResGen-d16 | 64 | 574M | 6.04 | 1.95 | <u>**1915**</u> |{{< /table-caption >}}

> 🔼 이 표는 ImageNet 256x256 데이터셋에서 클래스 조건부 이미지 생성에 대한 다양한 생성 모델의 성능을 비교합니다. 표에는 각 모델의 FID 점수(CFG 사용/미사용), 파라미터 수, 코드 길이, 최대 배치 크기가 포함되어 있습니다. 굵은 글꼴은 최고 결과를, 밑줄은 두 번째로 좋은 결과를, 별표는 원본 논문에서 보고된 점수를 나타냅니다. 코드 길이는 잠재 표현의 시퀀스 길이를 나타내고, 최대 배치 크기는 생성 모델이 동일한 장치에서 추론하는 동안 처리할 수 있는 최대 잠재 표현 수를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparison of different generative models on class-conditional ImageNet at a resolution of 256×256. The boldface indicates the best result, the underline denotes the second best, and the asterisk denotes the score reported in the original papers. The code length represents the sequence length of latent representations and the maximum batch size refers to the maximum number of latent representations that a generative model can process during inference.
> </details>





### In-depth insights


#### RVQ for Gen Models
**RVQ는 생성 모델에 계층적 토큰을 제공하여 고품질 생성을 가능하게 합니다.** RVQ의 깊이가 깊어질수록 더 세밀한 표현이 가능해지지만, 기존 autoregressive 모델에서는 샘플링 속도가 느려지는 문제가 발생합니다. ResGen은 이러한 문제를 해결하기 위해 **누적 벡터 임베딩을 예측하는 방식**을 제안합니다. 덕분에 토큰 깊이와 샘플링 복잡도를 분리하여 **고품질 생성과 빠른 샘플링 속도를 모두 달성**할 수 있습니다. 또한, ResGen은 마스크된 토큰 예측을 이산 확산 프로세스 및 변이 추론과 같은 확률적 프레임워크 내에서 공식화합니다. 이미지 생성 및 텍스트 음성 변환 실험에서 ResGen은 기존 autoregressive 모델보다 뛰어난 성능을 보여줍니다. **RVQ 깊이를 조정하여 생성 품질과 속도를 제어할 수 있는 ResGen의 유연성**은 다양한 생성 작업에 대한 적용 가능성을 시사합니다.

#### ResGen Framework
**ResGen**은 RVQ 기반 토큰을 활용하여 고품질 생성 모델링을 효율적으로 수행하는 프레임워크입니다. ResGen은 마스크된 토큰 예측을 **누적 벡터 임베딩** 예측으로 변환하여 생성 반복을 토큰 시퀀스 길이 및 깊이와 분리합니다. 이는 계층적 토큰 구조를 효율적으로 처리하고 샘플링 속도를 향상시킵니다. 또한 ResGen은 마스크된 토큰 예측 및 멀티토큰 예측 방법을 **확률적 프레임워크** 내에서 공식화하여 이산 확산 프로세스와 변이 추론을 활용합니다. 혼합 가우시안 분포를 사용한 잠재 임베딩 추정 및 모델 신뢰도 점수 기반 샘플링 전략을 통해 생성 품질을 더욱 향상시킵니다.

#### Probabilistic Model
**확률적 모델링**은 ResGen의 핵심입니다. 이는 마스크된 토큰 예측을 **불연속 확산 프로세스** 및 **변이 추론**이라는 원칙적인 확률적 프레임워크 내에서 공식화합니다. 이러한 접근 방식은 ResGen을 가능성 기반 생성 프로세스로 정의하고 설계에 대한 이론적 근거를 제공합니다. ResGen은 **토큰 마스킹**과 **멀티 토큰 예측**을 활용하여 고충실도 생성을 달성합니다. 마스킹 전략은 가장 높은 양자화 레이어에서 시작하여 점진적으로 토큰을 마스킹합니다. 멀티 토큰 예측은 개별 토큰이 아닌 집단 토큰의 누적 벡터 임베딩을 예측합니다. 이 방법은 RVQ 역양자화 프로세스와 자연스럽게 일치하며 생성 시간 복잡도를 토큰 깊이와 분리하여 샘플링 속도를 향상시킵니다.

#### Multimodal Results
**멀티모달 결과**는 다양한 데이터 유형을 결합하여 생성 모델의 성능을 평가하는 데 중요한 역할을 합니다. 이러한 결과는 이미지, 텍스트, 오디오와 같은 여러 양식을 동시에 처리하는 모델의 능력을 보여줍니다. **ResGen**과 같은 모델은 멀티모달 학습을 통해 이미지 생성과 텍스트 음성 변환(TTS) 모두에서 **뛰어난 성능**을 보입니다. 이미지 생성에서 ResGen은 **고충실도 샘플**을 생성하면서 빠른 샘플링 속도를 유지합니다. TTS에서는 WER 및 CER과 같은 객관적인 지표에서 최첨단 모델과 **견줄 만한 성능**을 달성하면서도 추론 단계 수가 **훨씬 적습니다**. 이러한 멀티모달 결과는 ResGen의 **다재다능함**과 다양한 애플리케이션에서의 **잠재력**을 보여줍니다.

#### Beyond RVQ Tokens
**RVQ 토큰을 넘어서는 확장**은 생성 모델의 성능과 효율성을 향상시키는 데 중요한 역할을 합니다. 본 논문에서는 RVQ 토큰 기반 생성 모델링의 한계를 극복하기 위한 여러 가지 방법을 제시합니다. 첫째, **토큰 마스킹 전략**을 통해 계층적 특성을 활용하여 고품질 샘플을 효율적으로 생성합니다. 둘째, **다중 토큰 예측**을 통해 개별 토큰 대신 집합적 벡터 임베딩을 예측하여 샘플링 속도를 향상시킵니다. 셋째, **확률적 프레임워크**를 기반으로 이산 확산 프로세스와 변분 추론을 활용하여 마스킹된 토큰 예측을 모델링합니다. 넷째, 잠재 임베딩 추정을 위한 **가우시안 혼합**과 모델 신뢰도 점수 기반 샘플링 전략을 통해 생성 품질을 향상시킵니다. 마지막으로, **FSQ와 같은 최신 양자화 기법**을 통합하여 토큰화 및 임베딩 프로세스를 개선하고 생성 성능을 향상시킬 수 있습니다. 추가적으로, **키-값 캐싱**을 활용하여 중복 계산을 줄이고 샘플링 속도를 더욱 향상시키는 방법을 고려할 수 있습니다. 또한, 노이즈가 있는 입력 대신 완전히 마스크되지 않은 토큰을 기반으로 예측하는 방식이 더 효율적인 이유에 대한 이론적 근거를 제시하는 것도 중요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.10208/x2.png)

> 🔼 이 그림은 다양한 생성 모델에서 샘플링 속도와 생성 품질 간의 관계를 보여줍니다. ResGen의 경우 점선은 다양한 샘플링 단계에 따른 성능을 나타내고 단계별 성능 향상을 강조합니다. 다른 모델의 경우 실선은 매개변수 크기 변화에 따른 결과를 연결합니다. ResGen에서 d는 모델의 깊이를 나타냅니다. 오른쪽 그림은 각 모델에 대해 추론 중에 달성 가능한 최대 배치 크기를 보여줍니다. 벽시계 추론 시간과 최대 추론 배치 크기는 모두 동일한 환경에서 측정됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: The left figure shows the trade-off between sampling speed and generation quality across various generative models. For ResGen, dotted lines indicate performance across different sampling steps, highlighting step-dependent performance improvements. For other models, solid lines connect results corresponding to variations in parameter size. Note that for ResGen, d represents the depth of the model. The right figure shows the maximum batch size achievable during inference for each model. Both wall-clock inference time and maximum inference batch size are measured in the same environment.
> </details>



![](https://arxiv.org/html/2412.10208/x3.png)

> 🔼 이 그림은 샘플링 단계 수를 변경했을 때 생성 품질의 변화를 보여주는 ablation study 결과입니다. 왼쪽(파란색)은 classifier-free guidance (CFG)를 사용했을 때의 결과이고, 오른쪽(녹색)은 CFG 없이 샘플링했을 때의 결과입니다. 두 경우 모두 샘플링 단계 수가 증가할수록 FID 점수가 낮아지는 것을 볼 수 있는데, 이는 샘플링 단계가 많을수록 모델이 출력을 더 정교하게 다듬어 생성 품질이 향상됨을 의미합니다.
> <details>
> <summary>read the caption</summary>
> (a) Step search
> </details>



![](https://arxiv.org/html/2412.10208/x4.png)

> 🔼 이 그림은 top-p 값을 변경하면서 생성 품질의 변화를 보여주는 ablation study 결과입니다. CFG(Classifier-Free Guidance)를 사용했을 때와 사용하지 않았을 때 top-p 값에 따른 FID 변화 추이를 각각 파란색과 초록색 선으로 표시했습니다. CFG를 사용하는 경우, top-p 값이 높을수록 생성 품질이 좋아지는 경향이 있고, CFG를 사용하지 않는 경우에는 top-p 값이 낮을수록 생성 품질이 좋아지는 것을 알 수 있습니다. 즉, CFG 사용 여부에 따라 top-p 값을 조정하는 것이 생성 품질 향상에 도움이 될 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (b) Top-p search
> </details>



![](https://arxiv.org/html/2412.10208/x5.png)

> 🔼 이 그림은 온도 스케일링이 생성 품질에 미치는 영향을 보여주는 ablation study 결과를 나타냅니다. ablation study는 샘플링 단계 수, top-p 값, 온도 스케일링 등의 하이퍼파라미터를 변경하며 ResGen의 샘플링 알고리즘의 특성을 분석하기 위해 수행되었습니다. 그림 3(c)에서 볼 수 있듯이, 적절한 온도를 사용하면 샘플링 중에 제어된 확률적 요소가 도입되어 RVQ 토큰 마스킹의 단조성을 완화하는 데 도움이 됩니다. ResGen에서는 신뢰도 점수에 따라 토큰 마스킹 순서가 정해지기 때문에 단조성 문제가 발생할 수 있습니다. 온도를 조정함으로써 다양성과 충실도 사이의 균형을 이루어 전반적인 생성 품질을 최적화할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (c) Temperature search
> </details>



![](https://arxiv.org/html/2412.10208/x6.png)

> 🔼 이 그림은 ResGen의 샘플링 방법에 대한 설정 검색 결과를 보여줍니다. 샘플링 단계 수, top-p 값, 온도 스케일링과 같은 다양한 하이퍼파라미터를 변경하여 생성 품질에 미치는 영향을 분석합니다. 그림 (a)는 샘플링 단계 수를 늘리면 CFG 유무에 관계없이 생성 품질이 향상됨을 보여줍니다. 그림 (b)는 CFG를 사용할 때 top-p 값이 높을수록 생성 품질이 향상되는 반면, CFG를 사용하지 않을 때는 top-p 값이 낮을수록 생성 품질이 향상됨을 보여줍니다. 그림 (c)는 적절한 온도 설정이 다양성과 충실도 사이의 균형을 맞춰 전반적인 생성 품질을 최적화하는 데 도움이 된다는 것을 보여줍니다. 파란색 선은 CFG를 사용한 결과를, 녹색 선은 CFG를 사용하지 않은 결과를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Configuration search results for sampling methods with (blue) and without (green) classifier-free guidance (CFG). (a) The effect of varying the number of sampling steps, (b) the impact of different top-p values, and (c) the influence of temperature scaling on confidence scores.
> </details>



![](https://arxiv.org/html/2412.10208/x7.png)

> 🔼 이 그림은 ImageNet 256x256 벤치마크에서 다양한 생성 모델의 성능을 비교하여 보여줍니다. (a)는 VAR-d30 모델로 생성된 이미지들을 보여주며, FID 점수는 1.92입니다. 이 그림은 논문의 다른 모델들(MAR-H, DiT-XL/2, ResGen)과 생성된 이미지 품질을 비교하기 위해 제시되었습니다. ResGen은 VAR-d30보다 빠른 샘플링 속도를 보이면서도 비슷한 FID 점수를 달성함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (a) VAR-d30 (FID=1.92)
> </details>



![](https://arxiv.org/html/2412.10208/x8.png)

> 🔼 이 그림은 ImageNet 256x256 벤치마크에서 MAR-H 모델이 생성한 이미지 샘플들을 보여줍니다. MAR-H는 1.55 FID 점수를 기록했습니다. 이는 그림 (d)의 ResGen (1.95 FID)보다 낮은 수치로, 더 높은 품질의 이미지 생성을 나타냅니다. MAR-H는 높은 해상도 이미지 합성을 위해 Latent Diffusion Model을 활용하는 모델입니다.
> <details>
> <summary>read the caption</summary>
> (b) MAR-H (FID=1.55)
> </details>



![](https://arxiv.org/html/2412.10208/x9.png)

> 🔼 이 그림은 DiT-XL/2 모델이 생성한 이미지들을 보여줍니다. DiT-XL/2는 256x256 해상도의 ImageNet 데이터셋에서 훈련되었으며, FID(Fréchet Inception Distance) 점수는 2.27입니다. FID는 생성된 이미지의 품질을 평가하는 지표로, 낮을수록 더 좋은 품질을 나타냅니다. ResGen과 비교했을 때, DiT-XL/2는 FID 점수가 더 높으므로 생성된 이미지의 품질이 약간 낮다고 볼 수 있습니다. 하지만 DiT-XL/2는 ResGen에 비해 파라미터 수가 적고 메모리 효율이 높다는 장점이 있습니다.
> <details>
> <summary>read the caption</summary>
> (c) DiT-XL/2 (FID=2.27)
> </details>



![](https://arxiv.org/html/2412.10208/x10.png)

> 🔼 이 그림은 ResGen 모델이 생성한 이미지 샘플들을 보여주고 있습니다. FID 점수는 1.95로, 다른 최신 모델들과 비교했을 때 경쟁력 있는 성능을 보여줍니다. ResGen은 깊이 있는 토큰을 사용하여 높은 충실도의 이미지를 생성하면서도 빠른 샘플링 속도를 유지하는 효율적인 RVQ 기반 확산 모델입니다. 이 샘플들은 ImageNet 256x256 벤치마크에서 생성된 것으로, ResGen의 우수한 생성 품질을 보여주는 예시입니다. 즉, ResGen은 단순히 샘플링 속도만 빠른 것이 아니라, 생성된 이미지의 품질 또한 매우 높다는 것을 의미합니다.
> <details>
> <summary>read the caption</summary>
> (d) ResGen, ours (FID=1.95)
> </details>



![](https://arxiv.org/html/2412.10208/x11.png)

> 🔼 이 그림은 ImageNet 256x256 벤치마크에서 ResGen을 다른 생성 모델(VAR, MAR, DiT)과 비교한 결과를 보여줍니다. 각 모델에서 생성된 이미지 샘플들을 통해 각 모델의 생성 품질을 시각적으로 비교할 수 있습니다. ResGen은 다른 모델들과 비슷하거나 더 나은 품질의 이미지를 생성하는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Model comparison on ImageNet 256×256 benchmark.
> </details>



![](https://arxiv.org/html/2412.10208/x12.png)

> 🔼 ResGen을 ImageNet에서 학습하여 생성한 랜덤 256x256 이미지 샘플입니다. 다양한 클래스의 이미지들이 생성되었으며, 품질 또한 높은 것을 확인할 수 있습니다. 이는 ResGen이 ImageNet 데이터셋의 다양한 특징을 잘 학습했음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Randomly generated 256×256 samples by ResGen trained on ImageNet.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | Params | FID (w/o CFG) ↓ | Inference Time ↓ |
|---|---|---|---| 
| ResGen (Ours) | 594M | 9.26 | 1.25s |
| RQ-transformer | 821M | 13.11 | 2.38s |{{< /table-caption >}}
> 🔼 ResGen과 RQ-transformer의 이미지 생성 품질 및 효율성 비교표입니다. 동일한 RVQ 토큰을 사용하여 평가되었으며, FID 점수와 추론 시간을 비교하여 ResGen의 우수한 성능을 보여줍니다. ResGen은 RQ-transformer보다 더 낮은 FID 점수를 달성하고, 더 빠른 추론 시간을 보입니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Comparison of image generation quality and efficiency between ResGen and the RQ-transformer, evaluated using the same RVQ tokens.
> </details>

{{< table-caption >}}
| Model | Params | WER ↓ | CER ↓ | SIM-o ↑ | SIM-r ↑ | Inference Steps ↓ |
|---|---|---|---|---|---|---| 
| Ground Truth | n/a | 2.2* | 0.61* | 0.754* | 0.754* | n/a |
| YourTTS | - | 7.57 | 3.06 | 0.3928 | - | **1** |
| Vall-E | 302M | 3.8* | - | 0.452* | 0.508* | - |
| Voicebox | 364M | 2.0* | - | **0.593*** | **0.616* | 64 |
| CLaM-TTS | 584M | 2.36* | 0.79* | 0.4767* | 0.5128* | - |
| DiTTo-en-L | 508M | 1.85 | 0.50 | 0.5596 | 0.5913 | 25 |
| DiTTo-en-XL | 740M | **1.78*** | **0.48*** | <ins>0.5773*</ins> | <ins>0.6075*</ins> | 25 |
| ResGen | 625M | <ins>**1.79**</ins> | <ins>**0.49**</ins> | 0.5743 | 0.5803 | <ins>**16**</ins> |{{< /table-caption >}}
> 🔼 이 표는 음성 생성 모델의 성능을 비교한 표입니다. 상단 표는 'continuation' 과제에 대한 결과이고, 하단 표는 'cross-sentence' 과제에 대한 결과입니다. 각 과제는 입력된 텍스트와 음성 조각을 기반으로 새로운 음성을 생성하는 과제입니다. 표에는 각 모델의 WER(단어 오류율), CER(문자 오류율), SIM-0(생성된 음성과 원본 음성의 유사도), SIM-r(원본 음성과 재구성된 음성의 유사도), 그리고 추론 단계 수가 포함되어 있습니다. 굵은 글씨는 최고 성능을, 밑줄은 두 번째로 좋은 성능을 나타내고, 별표는 기준 논문에서 보고된 점수임을 나타냅니다. ResGen 모델은 다른 모델들에 비해 적은 추론 단계를 사용하면서도 경쟁력 있는 성능을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Performances for the continuation task (top table) and the cross-sentence task (bottom table). The boldface indicates the best result, the underline denotes the second best, and the asterisk denotes the score reported in the baseline paper.
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