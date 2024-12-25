---
title: "Distilled Decoding 1: One-step Sampling of Image Auto-regressive Models with Flow Matching"
summary: "단일 단계 샘플링으로 이미지 자동 회귀 모델 속도를 획기적으로 향상시킨 증류 디코딩(DD) 기법 제안!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Generation", "🏢 Tsinghua University",]
showSummary: true
date: 2024-12-22
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.17153 {{< /keyword >}}
{{< keyword icon="writer" >}} Enshu Liu et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-24 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.17153" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.17153" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/distilled-decoding-1-one-step-sampling-of" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

자동 회귀(AR) 모델은 이미지 생성에서 최첨단 성능을 달성했지만, 토큰 단위의 순차적 생성 과정으로 속도가 매우 느린 것이 단점입니다. 기존의 다중 토큰 병렬 생성 기법들은 토큰 간의 조건부 종속성을 제대로 포착하지 못해 효과가 제한적이었습니다.  본 논문에서는 이러한 문제를 해결하기 위해 증류 디코딩(DD) 기법을 제시합니다.



DD는 흐름 일치(flow matching)를 이용하여 가우시안 분포에서 사전 훈련된 AR 모델의 출력 분포로의 결정적 매핑을 학습합니다. 이를 통해 AR 모델의 훈련 데이터 없이도 단일 또는 2단계 생성만으로 이미지를 생성할 수 있습니다. 실험 결과, DD는 기존 AR 모델에 비해 속도를 6.3배에서 217.8배까지 향상시켰으며, 이미지 품질 저하 또한 최소화했습니다.  **본 연구는 이미지 AR 모델의 단계를 획기적으로 줄이는 최초의 연구**이며, **향후 효율적인 AR 모델 개발 및 배포에 중요한 의미**를 가집니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 증류 디코딩(DD)은 흐름 일치(flow matching)를 이용하여 가우시안 분포에서 사전 훈련된 자동 회귀(AR) 모델의 출력 분포로의 결정적 매핑을 생성합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} DD는 이미지 자동 회귀 모델에서 단일 단계 생성을 가능하게 하여 속도를 획기적으로 향상시키면서도 FID 점수의 증가를 최소화합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} DD는 기존의 자동 회귀 모델의 속도 저하 문제를 해결하며, 효율적인 자동 회귀 모델 개발 및 배포를 위한 새로운 가능성을 제시합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **자동 회귀 모델의 속도 저하 문제를 해결**하기 위해 제안된 **증류 디코딩(DD)** 기법의 효과를 보여줍니다.  **단일 단계 샘플링을 통해 이미지 생성 속도를 획기적으로 향상**시키는 DD는 **다양한 AR 모델에 적용 가능**하며, **향후 효율적인 AR 모델 개발 및 배포에 큰 영향**을 미칠 것으로 예상됩니다.  **기존 연구의 한계를 극복**하고 **새로운 연구 방향을 제시**함으로써,  **AI 이미지 생성 분야의 발전에 중요한 기여**를 할 것으로 기대됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.17153/x1.png)

> 🔼 본 그림은 ImageNet 256x256 데이터셋에서 DD(Distilled Decoding) 모델과 기존 LlamaGen 모델(Sun et al., 2024)의 이미지 생성 결과를 비교한 것입니다. DD 모델은 기존 LlamaGen 모델보다 200배 이상 빠른 속도로 이미지를 생성하면서도, 생성 이미지의 품질 저하가 미미함을 보여줍니다. 그림에는 일부 생성 결과만 제시되어 있으며, 자세한 내용은 부록 F를 참조하시기 바랍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Qualitative comparisons between DD and vanilla LlamaGen Sun et al. (2024) on ImageNet 256×\times×256. We show that the generated images of DD have small quality loss compared to the pre-trained AR model, while achieving ≥\geq≥200×\times× speedup. More examples are in App. F.
> </details>





{{< table-caption >}}
| Type | Model | FID↓ | IS↑ | Pre↑ | Rec↑ | #Para | #Step | Time |
|---|---|---|---|---|---|---|---|---|
| GAN† | StyleGan-XL (Sauer et al., 2022) | 2.30 | 265.1 | 0.78 | 0.53 | 166M | 1 | 0.3 |
| Diff.† | ADM (Dhariwal & Nichol, 2021) | 10.94 | 101.0 | 0.69 | 0.63 | 554M | 250 | 168 |
| Diff.† | LDM-4-G (Rombach et al., 2022) | 3.60 | 247.7 | - | - | 400M | 250 | - |
| Diff.† | DiT-L/2 (Peebles & Xie, 2023) | 5.02 | 167.2 | 0.75 | 0.57 | 458M | 250 | 31 |
| Diff.† | L-DiT-7B (Peebles & Xie, 2023) | 2.28 | 316.2 | 0.83 | 0.58 | 7.0B | 250 | >45 |
| Mask.† | MaskGIT (Chang et al., 2022) | 6.18 | 182.1 | 0.80 | 0.51 | 227M | 8 | 0.5 |
| AR† | VQVAE-2† (Razavi et al., 2019) | 31.11 | ~45 | 0.36 | 0.57 | 13.5B | 5120 | - |
| AR† | VQGAN† (Esser et al., 2021) | 18.65 | 80.4 | 0.78 | 0.26 | 227M | 256 | 19 |
| AR | VQGAN (Esser et al., 2021) | 15.78 | 74.3 | - | - | 1.4B | 256 | 24 |
| AR | ViTVQ (Yu et al., 2021) | 4.17 | 175.1 | - | - | 1.7B | 1024 | >24 |
| AR | RQTran. (Lee et al., 2022) | 7.55 | 134.0 | - | - | 3.8B | 68 | 21 |
| AR | VAR-d16 (Tian et al., 2024) | 4.19 | 230.2 | 0.84 | 0.48 | 310M | 10 | 0.133 |
| AR | VAR-d20 (Tian et al., 2024) | 3.35 | 301.4 | 0.84 | 0.51 | 600M | 10 | - |
| AR | VAR-d24 (Tian et al., 2024) | 2.51 | 312.2 | 0.82 | 0.53 | 1.03B | 10 | - |
| AR | LlamaGen-B (Sun et al., 2024) | 5.42 | 193.5 | 0.83 | 0.44 | 111M | 256 | - |
| AR | LlamaGen-L (Sun et al., 2024) | 4.11 | 283.5 | 0.85 | 0.48 | 343M | 256 | 5.01 |
| Baseline | VAR-<i>skip-1</i> | 9.52 | 178.9 | 0.68 | 0.54 | 310M | 9 | 0.113 |
| Baseline | VAR-<i>skip-2</i> | 40.09 | 56.8 | 0.46 | 0.50 | 310M | 8 | 0.098 |
| Baseline | VAR-<i>onestep*</i> | 157.5 | - | - | - | 1 | - | - |
| Baseline | LlamaGen-<i>skip-106</i> | 19.14 | 80.39 | 0.42 | 0.43 | 343M | 150 | 2.94 |
| Baseline | LlamaGen-<i>skip-156</i> | 80.72 | 12.13 | 0.17 | 0.20 | 343M | 100 | 1.95 |
| Baseline | LlamaGen-<i>onestep*</i> | 220.2 | - | - | - | 1 | - | - |
| Ours | VAR-d16-DD | 9.94 | 193.6 | 0.80 | 0.37 | 327M | 1 | 0.021 (6.3×) |
| Ours | VAR-d16-DD | 7.82 | 197.0 | 0.80 | 0.41 | 327M | 2 | 0.036 (3.7×) |
| Ours | VAR-d20-DD | 9.55 | 197.2 | 0.78 | 0.38 | 635M | 1 | - |
| Ours | VAR-d20-DD | 7.33 | 204.5 | 0.82 | 0.40 | 635M | 2 | - |
| Ours | VAR-d24-DD | 8.92 | 202.8 | 0.78 | 0.39 | 1.09B | 1 | - |
| Ours | VAR-d24-DD | 6.95 | 222.5 | 0.83 | 0.43 | 1.09B | 2 | - |
| Ours | LlamaGen-B-DD | 15.50 | 135.4 | 0.76 | 0.26 | 98.3M | 1 | - |
| Ours | LlamaGen-B-DD | 11.17 | 154.8 | 0.80 | 0.31 | 98.3M | 2 | - |
| Ours | LlamaGen-L-DD | 11.35 | 193.6 | 0.81 | 0.30 | 326M | 1 | 0.023 (217.8×) |
| Ours | LlamaGen-L-DD | 7.58 | 237.5 | 0.84 | 0.37 | 326M | 2 | 0.043 (116.5×) |{{< /table-caption >}}

> 🔼 표 1은 클래스 조건부 ImageNet-256 데이터셋에서 여러 이미지 생성 모델의 성능을 비교 분석한 표입니다.  각 모델의 FID(Fréchet Inception Distance) 점수, Inception Score(IS), Precision, Recall, 매개변수 수, 이미지 생성에 필요한 단계 수(#Step), 그리고 안정적인 상태에서 이미지 하나를 생성하는 데 걸리는 시간(Time)을 보여줍니다.  #Step은 모델이 이미지를 생성하기 위해 거쳐야 하는 추론 단계 수를 나타내며, Time은 실제 소요 시간을 초 단위로 표시합니다.  Tian et al.(2024) 논문의 VAR 모델 결과는 † 표시로 구분되어 있습니다. 이 표는 다양한 모델의 생성 품질과 속도를 비교하여 DD 모델의 효율성을 보여주는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 1:  Generative performance on class-conditional ImageNet-256. “#Step” indicates the number of model inference to generate one image. “Time” is the wall-time of generating one image in the steady state. Results with † are taken from the VAR paper (Tian et al., 2024).
> </details>





### In-depth insights


#### One-Step AR Decoding
본 논문에서 제시된 'One-Step AR Decoding' 개념은 **자동 회귀(AR) 모델의 속도 저하 문제를 해결하기 위한 혁신적인 접근 방식**을 보여줍니다. 기존의 토큰 단위 생성 방식에서 벗어나, **전체 시퀀스를 한 번에 생성**함으로써 획기적인 속도 향상을 달성합니다. 이를 위해 **플로우 매칭(Flow Matching)** 기법을 활용하여 가우시안 분포를 AR 모델의 출력 분포에 매핑하고, 이 매핑을 학습 가능한 신경망으로 증류합니다. 이는 기존의 다중 토큰 병렬 생성 방식의 한계를 극복하고, 출력 분포를 정확하게 포착하는 데 중요한 역할을 합니다. 특히, **사전 훈련된 AR 모델의 학습 데이터 없이도 효과적으로 수행**될 수 있다는 점은 실용적인 측면에서 큰 장점입니다.  결과적으로, **훨씬 빠른 속도로 이미지 생성**을 가능하게 하여 AR 모델의 실제 적용 가능성을 크게 높일 것으로 예상됩니다.  하지만, 여전히 **단일 단계 생성의 정확도와 품질**에 대한 추가적인 연구가 필요하며, 다양한 AR 모델 및 데이터셋에 대한 실험적 검증을 통해 일반화 가능성을 더욱 높여야 할 것입니다.

#### Flow Matching Distillation
본 논문에서 제안하는 흐름 일치 증류(Flow Matching Distillation)는 **이미지 자기회귀 모델의 속도를 높이기 위한 핵심 기법**입니다. 기존의 토큰 단위 생성 방식의 속도 저하 문제를 해결하고자, 가우시안 분포에서 사전 훈련된 자기회귀 모델의 출력 분포로의 결정적 매핑을 생성합니다. 이를 위해 **흐름 일치(Flow Matching)** 기법을 활용하여 확률 경로를 생성하고, 이를 신경망으로 증류합니다. **이러한 과정을 통해 단일 또는 몇 단계의 생성만으로도 고품질 이미지 생성이 가능**해집니다. 특히, 기존 방식과 달리 원래 자기회귀 모델의 훈련 데이터가 필요 없어 실용성이 높다는 장점이 있습니다.  **다양한 이미지 자기회귀 모델에서의 실험 결과는 이 방법의 효과성을 보여줍니다.**  단계 수 감소에 따른 속도 향상은 물론, 생성 이미지의 품질 저하를 최소화하는 데 효과적임을 확인했습니다.  **본 연구는 자기회귀 모델의 속도 제한에 대한 기존의 인식에 도전**하며, 효율적인 이미지 생성을 위한 새로운 가능성을 제시합니다.

#### Few-Step AR Limits
본 논문의 "Few-Step AR Limits" 부분은 기존 오토리그레시브(AR) 모델의 주요 한계점인 느린 생성 속도를 다루고 있습니다. 토큰 단위 생성 방식의 AR 모델은 여러 단계를 거쳐야 하기에 속도가 느린데, 이를 단 몇 단계만으로 줄이는 방법의 어려움을 설명합니다. **기존의 여러 토큰을 동시에 생성하는 방법은 토큰 간의 조건부 종속성을 제대로 고려하지 못해 정확한 결과 분포를 캡처하지 못한다는 점**이 주요 문제점으로 지적됩니다.  이는 단계 수를 줄이려는 시도가 본질적으로 출력 분포를 왜곡시키기 때문에, 단순한 병렬화나 다중 토큰 생성으로는 근본적인 해결책이 될 수 없다는 것을 의미합니다.  **본 논문은 이러한 한계를 극복하기 위해 새로운 방법론을 제시하며,  이를 통해 AR 모델의 속도 향상과 효율적인 배포 가능성을 모색**합니다.  결론적으로, 이 섹션은 AR 모델의 속도 향상이 단순한 기술적 개선이 아닌, 기본적인 확률적 모델링의 한계를 극복하는 어려운 문제임을 강조합니다.

#### ImageNet-256 Results
이미지넷-256 결과는 논문에서 제시된 다양한 이미지 생성 모델의 성능을 평가하는 데 사용된 주요 지표입니다. **VAR 및 LlamaGen과 같은 최첨단 오토 회귀 모델의 성능을 측정**하기 위해 사용되었으며, FID(Fréchet Inception Distance) 점수를 통해 생성된 이미지의 품질을 정량적으로 비교했습니다.  **낮은 FID 점수는 더 높은 이미지 품질을 나타내며, 이는 모델의 성능을 평가하는 중요한 지표**입니다.  본 논문에서는 제안된 DD(Distilled Decoding) 방법의 효과를 보여주는 데 이 결과가 중요한 역할을 합니다. DD를 사용하여 생성된 이미지의 FID 점수가 기존 모델보다 높더라도, 속도 향상이 훨씬 크기 때문에 균형을 이루고 있음을 보여줍니다. **특히, 1단계 생성을 통해 극적인 속도 향상**을 달성한 점이 강조됩니다.  이러한 결과는 **DD가 이미지 생성 속도를 크게 향상시키면서도 이미지 품질을 유지할 수 있음을 입증**합니다.  결론적으로, ImageNet-256 결과는 DD의 효율성과 실용성을 보여주는 핵심적인 증거로 해석할 수 있습니다.

#### Future AR Research
미래의 자기회귀(AR) 모델 연구는 **단일 단계 생성의 실현 가능성**에 초점을 맞춰야 합니다. 본 논문에서 제시된 DD 기법은 AR 모델의 속도 향상에 중요한 진전을 가져왔지만, 여전히 개선의 여지가 있습니다. **더욱 효율적인 흐름 매칭 기법**의 개발과 **다양한 AR 모델 아키텍처**에 대한 DD의 적용 가능성을 탐구하는 것이 중요합니다. 또한, **텍스트 및 이미지 외 다른 모달리티**로의 확장 및 **대규모 언어 모델(LLM)**과의 통합을 통해 AR 모델의 활용 범위를 넓히는 연구가 필요합니다.  **훈련 데이터 없이 AR 모델을 효율적으로 학습**시키는 방법에 대한 연구도 중요한 과제입니다.  **샘플 품질과 속도 사이의 균형**을 최적화하는 연구도 지속적으로 필요하며, **다양한 응용 분야**에서 AR 모델의 효율성을 높이는 연구가 활발히 이루어져야 합니다.  궁극적으로는, **인간 수준의 생성 품질과 실시간 속도**를 동시에 만족하는 AR 모델을 개발하는 것이 미래 AR 연구의 목표가 될 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.17153/x2.png)

> 🔼 그림 2는 제안된 방법인 DD-2step을 사용한 텍스트-이미지 생성 결과를 보여줍니다. LlamaGen 모델을 기반으로 LAION-COCO 데이터셋의 프롬프트를 사용하여 DD-2step 모델을 학습시켰습니다.  기존 LlamaGen 모델에 비해 약 93배의 속도 향상을 보였습니다. 그림에는 네 가지 예시가 제시되어 있으며, 보다 자세한 결과는 부록 F에서 확인할 수 있습니다. 각 이미지는 주어진 텍스트 프롬프트에 대한 생성 결과를 보여줍니다. 예를 들어, 'Activate Upholstered Fabric Armchair' 프롬프트에 대해서는 안락의자 이미지가, 'Butterfly Women's T-Shirt' 에 대해서는 나비가 그려진 티셔츠 이미지가 생성되었습니다. 이는 DD-2step 모델이 다양한 텍스트 프롬프트에 대해 질적으로 우수한 이미지를 빠르게 생성할 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Qualitative results of DD-2step on text-to-image task. The model is distilled from LlamaGen model with prompts from LAION-COCO dataset. The speedup is around 93 ×\times× compared to the teacher model. More examples are in App. F.
> </details>



![](https://arxiv.org/html/2412.17153/x3.png)

> 🔼 그림 3은 사전 훈련된 이미지 자기회귀 모델의 추론 속도를 높이기 위한 다양한 방법들을 비교 분석한 결과를 보여줍니다.  DD(Distilled Decoding) 모델은 기존 사전 훈련된 모델들에 비해 추론 속도가 현저히 빠르면서도 성능 저하가 거의 없음을 보여줍니다. 반면, 다른 가속화 방법들은 추론 시간이 감소함에 따라 성능이 급격히 저하되는 것을 확인할 수 있습니다.  이를 통해 DD 모델이 이미지 생성 속도 향상에 있어 효율적이고 효과적인 방법임을 시사합니다.  그림에는 VAR 및 LlamaGen 모델에 대한 결과가 각각 표시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Comparison of DD models, pre-trained models, and other acceleration methods for pre-trained models. DD achieves significant speedup compared to pre-trained models with comparable performance. In contrast, other methods’ performance degrades quickly as inference time decreases.
> </details>



![](https://arxiv.org/html/2412.17153/x4.png)

> 🔼 그림 4는 제안된 증류 디코딩(DD) 방법과 기존 방법들의 차이를 보여줍니다. 토큰 시퀀스 qᵢ 를 생성하는 세 가지 방법을 비교합니다. (a) 일반적인 자기회귀(AR) 모델은 토큰을 하나씩 생성하므로 느립니다. (b) 병렬 디코딩은 여러 토큰을 동시에 생성하지만, 한 단계로 생성할 경우 원래 AR 모델의 출력 분포와 일치하지 않습니다. (c) 제안된 DD 방법은 가우시안 분포의 노이즈 토큰 ϵᵢ 를 사용하여 생성된 토큰 시퀀스 전체를 한 번에 매핑합니다. 이상적인 경우, 생성된 토큰의 분포는 원래 AR 모델의 분포와 일치합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: High-level comparison between our Distilled Decoding (DD) and prior work. To generate a sequence of tokens qisubscript𝑞𝑖q_{i}italic_q start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT: (a) the vanilla AR model generates token-by-token, thus being slow; (b) parallel decoding generates multiple tokens in parallel (Sec. 4.1), which fundamentally cannot match the generated distribution of the original AR model with one-step generation (see Sec. 3.1); (c) our DD maps noise tokens ϵisubscriptitalic-ϵ𝑖\epsilon_{i}italic_ϵ start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT from Gaussian distribution to the whole sequence of generated tokens directly in one step and it is guaranteed that (in the optimal case) the distribution of generated tokens matches that of the original AR model.
> </details>



![](https://arxiv.org/html/2412.17153/x5.png)

> 🔼 이 그림은 자기 회귀(AR) 흐름 매칭의 개념을 보여줍니다. 이전 토큰들이 주어지면, AR 모델은 다음 토큰에 대한 확률 벡터를 생성합니다. 이 벡터는 코드북 내 모든 토큰에 걸쳐 디랙 델타 분포의 혼합으로 정의됩니다.  이 그림은 가우시안 분포와 디랙 델타 분포 사이의 결정적 매핑을 흐름 매칭을 사용하여 생성하는 방법을 보여줍니다.  다음 노이즈 토큰 (ϵ4)는 가우시안 분포에서 샘플링되고, 코드북에서 해당 토큰 (q4)이 다음 토큰이 됩니다.  즉,  불확실성이 큰 가우시안 분포에서 샘플링된 노이즈를 결정론적인 방법으로 AR 모델의 출력 분포에 매칭시켜 다음 토큰을 예측하는 과정을 시각적으로 설명합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: AR flow matching. Given all previous tokens, the teacher AR model gives a probability vector for the next token, which defines a mixture of Dirac delta distributions over all tokens in the codebook. We then construct a deterministic mapping between the Gaussian distribution and the Dirac delta distribution with flow matching. The next noise token ϵ4subscriptitalic-ϵ4\epsilon_{4}italic_ϵ start_POSTSUBSCRIPT 4 end_POSTSUBSCRIPT is sampled from the Gaussian distribution, and its corresponding token in the codebook becomes the next token q4subscript𝑞4q_{4}italic_q start_POSTSUBSCRIPT 4 end_POSTSUBSCRIPT.
> </details>



![](https://arxiv.org/html/2412.17153/x6.png)

> 🔼 그림 6은 제안된 DD 모델의 학습 및 생성 과정을 보여줍니다. 잡음 토큰 ϵᵢ로 구성된 초기 시퀀스 X₁이 주어지면, 데이터 토큰 qᵢ와 잡음 토큰 ϵᵢ로 이루어진 전체 시퀀스 X₁, ..., X₅는 고유하게 결정됩니다(3.2절 참조). 시간 단계를 {t₁=1, t₂=3}으로 설정하면, 학습 과정(3.3절 참조)에서 DD 모델은 입력으로 X₁ 또는 X₃을 사용하여 X₅을 재구성하도록 학습됩니다. 이를 통해 DD 모델은 X₁ 및 X₃에서 후속 시퀀스의 임의 지점(예: X₁에서 {X₂, ..., X₅})으로 이동할 수 있습니다. 생성 과정(3.3절 참조)에서는 1단계(X₁→X₅) 또는 2단계(X₁→X₃→X₅) 생성을 수행할 수 있습니다. 또한, 생성 과정의 일부에 기존 AR 모델을 통합하여 더 많은 단계의 생성을 수행할 수도 있습니다(예: X₂→X₃에서 AR 모델을 사용하고 다른 단계에서는 DD 모델을 사용하는 3단계 생성 X₁→X₂→X₃→X₅).
> <details>
> <summary>read the caption</summary>
> Figure 6: The training and generation workflow of DD. Given X1subscript𝑋1X_{1}italic_X start_POSTSUBSCRIPT 1 end_POSTSUBSCRIPT with noise tokens ϵisubscriptitalic-ϵ𝑖\epsilon_{i}italic_ϵ start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT, the whole trajectory X1,⋯,X5subscript𝑋1⋯subscript𝑋5X_{1},\cdots,X_{5}italic_X start_POSTSUBSCRIPT 1 end_POSTSUBSCRIPT , ⋯ , italic_X start_POSTSUBSCRIPT 5 end_POSTSUBSCRIPT consists of data tokens qisubscript𝑞𝑖q_{i}italic_q start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT and noise tokens ϵisubscriptitalic-ϵ𝑖\epsilon_{i}italic_ϵ start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT is uniquely determined (Sec. 3.2). Assuming the timesteps are set to {t1=1,t2=3}formulae-sequencesubscript𝑡11subscript𝑡23\{t_{1}=1,t_{2}=3\}{ italic_t start_POSTSUBSCRIPT 1 end_POSTSUBSCRIPT = 1 , italic_t start_POSTSUBSCRIPT 2 end_POSTSUBSCRIPT = 3 }. During training (Sec. 3.3), we train DD model to reconstruct X5subscript𝑋5X_{5}italic_X start_POSTSUBSCRIPT 5 end_POSTSUBSCRIPT given X1subscript𝑋1X_{1}italic_X start_POSTSUBSCRIPT 1 end_POSTSUBSCRIPT or X3subscript𝑋3X_{3}italic_X start_POSTSUBSCRIPT 3 end_POSTSUBSCRIPT as input. The DD will then have the capability of jumping from X1subscript𝑋1X_{1}italic_X start_POSTSUBSCRIPT 1 end_POSTSUBSCRIPT and X3subscript𝑋3X_{3}italic_X start_POSTSUBSCRIPT 3 end_POSTSUBSCRIPT to any point in the later trajectory (e.g., X1subscript𝑋1X_{1}italic_X start_POSTSUBSCRIPT 1 end_POSTSUBSCRIPT to any of {X2,⋯,X5}subscript𝑋2⋯subscript𝑋5\{X_{2},\cdots,X_{5}\}{ italic_X start_POSTSUBSCRIPT 2 end_POSTSUBSCRIPT , ⋯ , italic_X start_POSTSUBSCRIPT 5 end_POSTSUBSCRIPT }). During generation (Sec. 3.3), we can either do 1-step (X1→X5→subscript𝑋1subscript𝑋5X_{1}\rightarrow X_{5}italic_X start_POSTSUBSCRIPT 1 end_POSTSUBSCRIPT → italic_X start_POSTSUBSCRIPT 5 end_POSTSUBSCRIPT) or 2-step generation (X1→X3→X5→subscript𝑋1subscript𝑋3→subscript𝑋5X_{1}\rightarrow X_{3}\rightarrow X_{5}italic_X start_POSTSUBSCRIPT 1 end_POSTSUBSCRIPT → italic_X start_POSTSUBSCRIPT 3 end_POSTSUBSCRIPT → italic_X start_POSTSUBSCRIPT 5 end_POSTSUBSCRIPT). Additionally, we can do generation with more steps by incorporating the teacher AR model in part of the generation process, such as 3-step generation X1→X2→X3→X5→subscript𝑋1subscript𝑋2→subscript𝑋3→subscript𝑋5X_{1}\rightarrow X_{2}\rightarrow X_{3}\rightarrow X_{5}italic_X start_POSTSUBSCRIPT 1 end_POSTSUBSCRIPT → italic_X start_POSTSUBSCRIPT 2 end_POSTSUBSCRIPT → italic_X start_POSTSUBSCRIPT 3 end_POSTSUBSCRIPT → italic_X start_POSTSUBSCRIPT 5 end_POSTSUBSCRIPT where X2→X3→subscript𝑋2subscript𝑋3X_{2}\rightarrow X_{3}italic_X start_POSTSUBSCRIPT 2 end_POSTSUBSCRIPT → italic_X start_POSTSUBSCRIPT 3 end_POSTSUBSCRIPT utilizes the AR model and other steps use the DD model.
> </details>



![](https://arxiv.org/html/2412.17153/extracted/6092433/fig/var1_update_samenoise.png)

> 🔼 그림 7은 다양한 중간 시간 단계에 대한 FID(Fréchet Inception Distance) 대비 에포크 또는 반복 횟수의 훈련 곡선을 보여줍니다. FID는 5,000개의 생성된 샘플을 사용하여 계산됩니다.  이 그래프는 모델이 훈련되는 동안 이미지 생성 품질의 변화를 보여주며, 서로 다른 중간 시간 단계를 사용했을 때 성능 변화를 비교 분석하는 데 도움이 됩니다. 각 곡선은 특정 중간 시간 단계 설정에서 모델의 FID 점수가 훈련 에포크 또는 반복 횟수에 따라 어떻게 변하는지를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: The training curve of FID vs. epoch or iteration for different intermediate timesteps. FIDs are calculated with 5k generated sample.
> </details>



![](https://arxiv.org/html/2412.17153/extracted/6092433/fig/var2_update_samenoise.png)

> 🔼 그림 8은 서로 다른 크기의 데이터셋을 사용하여 학습시킨 DD 모델의 FID(Fréchet Inception Distance) 점수 변화를 에폭(epoch)에 따라 보여줍니다. FID 점수는 생성된 샘플의 품질을 평가하는 지표로, 낮을수록 좋습니다. 이 그래프는 데이터셋 크기가 클수록 FID 점수가 더 낮아져 모델의 성능이 향상됨을 보여줍니다. 5,000개의 생성된 샘플을 사용하여 FID 점수를 계산했습니다.  즉, 더 많은 데이터로 학습할수록 이미지 생성 품질이 향상되는 것을 보여주는 그래프입니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: The training curve of FID vs. epoch for different dataset sizes. FIDs are calculated with 5k generated sample.
> </details>



![](https://arxiv.org/html/2412.17153/extracted/6092433/fig/llamagen1_update_samenoise.png)

> 🔼 그림 9는 VAR 모델(Tian et al., 2024)을 사용한 이미지 생성 결과를 보여줍니다. 왼쪽부터 순서대로 한 단계 DD 모델, 두 단계 DD 모델, DD-미세조정(4-6단계), 그리고 미세조정 전 VAR 모델의 결과 이미지가 나열되어 있습니다. 이 그림은 제안된 DD 방법이 VAR 모델의 이미지 생성 속도를 높이면서도 이미지 품질을 유지할 수 있음을 시각적으로 보여주기 위해 제시되었습니다.  각 모델의 이미지 생성 단계 수와 미세 조정 여부에 따른 이미지 품질 변화를 비교하여 DD 모델의 효율성과 성능을 직관적으로 이해할 수 있도록 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Generation results with VAR model (Tian et al., 2024). From left to right: one-step DD model, two-step DD model, DD-pre-trained-4-6, and the pre-trained VAR model.
> </details>



![](https://arxiv.org/html/2412.17153/extracted/6092433/fig/llamagen2_update_samenoise.png)

> 🔼 그림 10은 Tian et al.(2024)의 VAR 모델을 사용한 이미지 생성 결과를 보여줍니다. 왼쪽부터 차례대로 한 단계 DD 모델, 두 단계 DD 모델, DD-pre-trained-4-6 및 사전 훈련된 VAR 모델의 출력 결과가 나열되어 있습니다. 이 그림은 각 모델이 이미지를 생성하는 데 걸리는 단계 수와 생성된 이미지의 질적 차이를 비교하여 DD 모델의 효율성을 보여주는 것을 목적으로 합니다.  DD 모델은 기존 VAR 모델보다 훨씬 적은 단계로 비교적 좋은 화질의 이미지를 생성할 수 있음을 시각적으로 보여줍니다. 특히 DD-pre-trained-4-6 모델은 사전 훈련된 VAR 모델과 유사한 결과를 보여주면서도 생성 단계를 크게 줄였음을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Generation results with VAR model (Tian et al., 2024). From left to right: one-step DD model, two-step DD model, DD-pre-trained-4-6, and the pre-trained VAR model.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Type | Model | FID↓ | IS↑ | Pre↑ | Rec↑ | #Para | #Step | Time |
|---|---|---|---|---|---|---|---|---|
| AR | VAR (Tian et al., 2024) | 4.19 | 230.2 | 0.84 | 0.48 | 310M | 10 | 0.133 |
| AR | LlamaGen (Sun et al., 2024) | 4.11 | 283.5 | 0.865 | 0.48 | 343M | 256 | 5.01 |
| Ours | VAR-pre-trained-1-6 | 5.03 | 242.8 | 0.84 | 0.45 | 327M | 6 | 0.090 (1.5×) |
| Ours | VAR-pre-trained-4-6 | 5.47 | 230.5 | 0.84 | 0.43 | 327M | 4 | 0.062 (2.1×) |
| Ours | VAR-pre-trained-5-6 | 6.54 | 210.8 | 0.83 | 0.42 | 327M | 3 | 0.045 (2.6×) |
| Ours | LlamaGen-pre-trained-1-81 | 5.71 | 238.6 | 0.83 | 0.43 | 326M | 81 | 1.725 (2.9×) |
| Ours | LlamaGen-pre-trained-41-81 | 6.20 | 233.8 | 0.83 | 0.41 | 326M | 42 | 0.880 (5.7×) |
| Ours | LlamaGen-pre-trained-61-81 | 6.76 | 231.4 | 0.83 | 0.40 | 326M | 22 | 0.447 (11.2×) |{{< /table-caption >}}
> 🔼 표 2는 사전 훈련된 자동 회귀(AR) 모델을 샘플링 과정에 포함시켰을 때의 생성 품질을 보여줍니다.  'pre-trained-n-m' 표기법은 DD의 첫 번째 단계에서 생성된 시퀀스 내 n번째 토큰부터 m-1번째 토큰까지를 사전 훈련된 AR 모델을 사용하여 다시 생성했음을 의미합니다.  즉, DD 모델이 처음 몇 개의 토큰을 생성한 후, 사전 훈련된 AR 모델을 이용하여 추가적인 토큰들을 생성하는 하이브리드 방식의 결과를 보여주는 표입니다.  이를 통해 사전 훈련된 모델의 성능을 활용하면서도 DD 모델의 속도 향상 효과를 유지하는 방식의 성능을 비교 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Generation quality of involving the pre-trained AR model when sampling. The notation pre-trained-n-m means that the pre-trained AR model is used to re-generate the n𝑛nitalic_n-th to m−1𝑚1m-1italic_m - 1-th tokens in the sequence generated by the first step of DD.
> </details>

{{< table-caption >}}
| Type | Model | FID | #Param | #Step | Time |
|---|---|---|---|---|---| 
| AR | LlamaGen | 25.70 | 775M | 256 | 7.90 |
| Ours | LlamaGen-DD | 36.09 | 756M | 1 | 0.052 (151.9x) |
| Ours | LlamaGen-DD | 28.95 | 756M | 2 | 0.085 (92.9x) |{{< /table-caption >}}
> 🔼 표 3은 제시된 논문에서 DD(Distilled Decoding) 모델을 사용한 텍스트-이미지 생성 결과를 보여줍니다.  LlamaGen 모델을 기반으로 학습된 DD 모델이 이미지 생성 속도 향상에 미치는 영향을 FID(Fréchet Inception Distance) 점수, 매개변수 수, 생성 단계 수, 생성 시간 등을 통해 정량적으로 평가한 결과를 담고 있습니다.  본 표는 LlamaGen 모델의 기본 성능과 비교하여 DD 모델의 효율성 및 성능을 파악하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Generation results of DD on text-to-image task.
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