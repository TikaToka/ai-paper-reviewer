---
title: "TangoFlux: Super Fast and Faithful Text to Audio Generation with Flow Matching and Clap-Ranked Preference Optimization"
summary: "TANGOFLUX: 적은 매개변수로 초고속, 고품질 텍스트 음성 변환"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Text Generation", "🏢 Singapore University of Technology and Design",]
showSummary: true
date: 2024-12-30
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.21037 {{< /keyword >}}
{{< keyword icon="writer" >}} Chia-Yu Hung et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-31 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.21037" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.21037" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/tangoflux-super-fast-and-faithful-text-to" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

본 논문은 **텍스트 음성 변환(TTA)** 분야의 어려움, 특히 **오디오 선호도 데이터 생성의 어려움**과 **기존 모델의 속도 및 품질 한계**를 다룹니다. 기존 TTA 모델들은 긴 생성 시간, 많은 매개변수, 또는 품질 저하 문제를 갖고 있었습니다. 또한, TTA의 정렬 과정은 LLM과 달리 구조화된 메커니즘이 부족하여 선호도 쌍을 생성하기 어려웠습니다.

본 논문에서는 이러한 문제 해결을 위해 **TANGOFLUX**라는 새로운 TTA 모델과 **CLAP-Ranked Preference Optimization (CRPO)**라는 프레임워크를 제시합니다. TANGOFLUX는 적은 매개변수로 빠른 속도와 높은 품질을 달성하며, CRPO는 CLAP 모델을 활용하여 반복적인 데이터 생성 및 최적화를 통해 모델의 정렬을 개선합니다. 실험 결과는 TANGOFLUX가 다양한 벤치마크에서 최고 성능을 달성했음을 보여주며, 특히 다중 이벤트가 있는 복잡한 프롬프트에서 성능이 뛰어났습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} TANGOFLUX는 기존 최첨단 모델보다 적은 매개변수로 빠르고 정확한 텍스트 음성 변환을 달성했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} CLAP-Ranked Preference Optimization (CRPO)는 효율적인 오디오 선호도 데이터 생성 및 정렬 프레임워크입니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} TANGOFLUX는 다양한 벤치마크에서 최첨단 성능을 보였으며, 특히 다중 이벤트가 포함된 복잡한 프롬프트에 대한 성능이 뛰어났습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **빠르고 정확한 텍스트 음성 변환 모델을 개발**하고, **오디오 선호도 데이터 생성 및 정렬을 위한 새로운 프레임워크를 제시**함으로써, 관련 연구 분야의 발전에 크게 기여합니다. 특히, 제한된 매개변수로 고품질 오디오를 생성하는 효율적인 방법을 제시하고, 기존 방식의 한계를 극복하는 새로운 접근 방식을 제시함으로써, 향후 연구의 새로운 방향을 제시합니다. 또한, **실제 응용 분야에 활용될 수 있는 가능성**을 보여주는 실험 결과를 제시함으로써, 실용적인 측면에서도 높은 가치를 지닙니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.21037/x1.png)

> 🔼 그림 1은 TANGOFLUX의 전체 훈련 과정을 보여줍니다.  먼저, 사전 훈련 단계에서는 대규모 오디오 데이터셋을 사용하여 TANGOFLUX 모델의 기본 구조를 훈련합니다. 다음으로, 미세 조정 단계에서는 더 작은 크기의 고품질 데이터셋을 사용하여 모델의 성능을 개선합니다. 마지막으로, 온라인 반복 정렬 단계에서는 CLAP-Ranked Preference Optimization (CRPO) 기법을 사용하여 생성된 오디오의 품질을 지속적으로 향상시킵니다.  CRPO는 반복적으로 오디오 선호도 데이터를 생성하고 최적화하여, 모델이 사용자의 의도에 더 잘 맞는 오디오를 생성하도록 돕습니다. 이 그림은 각 단계의 주요 구성 요소와 데이터 흐름을 시각적으로 나타내어 TANGOFLUX의 훈련 과정을 명확하게 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: A depiction of the overall training pipeline of TangoFlux.
> </details>





{{< table-caption >}}
| Model | #Params. | Duration | Steps | FD<sub>openl3</sub> ↓ | KL<sub>passt</sub> ↓ | CLAP<sub>score</sub> ↑ | IS ↑ | Inference Time (s) |
|---|---|---|---|---|---|---|---|---|
| `AudioLDM 2`-`large` | 712M | 10 sec | 200 | 108.3 | 1.81 | 0.419 | 7.9 | 24.8 |
| `Stable Audio Open` | 1056M | 47 sec | 100 | 89.2 | 2.58 | 0.291 | 9.9 | 8.6 |
| `Tango 2` | 866M | 10 sec | 200 | 108.4 | **1.11** | 0.447 | 9.0 | 22.8 |
| **TangoFlux-base** | **515M** | 30 sec | 50 | 80.2 | 1.22 | 0.431 | 11.7 | **3.7** |
| **TangoFlux** | **515M** | 30 sec | 50 | **75.1** | 1.15 | **0.480** | **12.2** | **3.7** |{{< /table-caption >}}

> 🔼 표 1은 다양한 텍스트 음성 변환 모델의 성능을 여러 지표를 통해 비교 분석한 표입니다. 생성된 오디오의 길이(Output length), 프레셰 거리(FDopenl3), KL 발산(KLpasst), 정렬도(CLAP score) 등의 지표를 사용하여 모델의 성능을 평가하였습니다. 모든 추론 시간은 동일한 A40 GPU에서 측정되었으며, 학습 가능한 매개변수의 수(#Params)도 함께 제시되어 있습니다. 이 표는 제시된 다양한 지표를 통해 각 모델의 음성 생성 품질, 효율성 및 정확성을 비교 분석하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparison of audio generation models across various metrics. Output length represents the duration of the generated audio. Metrics include FDopenl3openl3{}_{\text{openl3}}start_FLOATSUBSCRIPT openl3 end_FLOATSUBSCRIPT for Frechet Distance, KLpasstpasst{}_{\text{passt}}start_FLOATSUBSCRIPT passt end_FLOATSUBSCRIPT for KL divergence, and CLAPscorescore{}_{\text{score}}start_FLOATSUBSCRIPT score end_FLOATSUBSCRIPT for alignment. All inference time is computed on the same A40 GPU. We report the trainable parameters in the #Params column.
> </details>





### In-depth insights


#### Fast TTA Generation
본 논문은 **빠른 텍스트 음성 변환(TTA)** 생성에 초점을 맞추고 있습니다.  기존의 TTA 모델들이 속도 면에서 제한적인 성능을 보이는 것과 달리, 본 연구는 훨씬 빠른 처리 속도를 달성하는 새로운 모델을 제시합니다. 이를 위해 **효율적인 모델 아키텍처**와 **최적화된 학습 전략**을 채택하여 연산 비용을 줄이고 생성 속도를 크게 향상시켰습니다.  특히 **고품질의 오디오를 신속하게 생성**하는 능력은 실시간 응용 분야나 대규모 데이터 처리에 매우 중요한 이점을 제공하며, **실용적인 측면**에서 큰 의미를 지닌다고 할 수 있습니다.  **향후 연구**에서는 본 모델의 성능을 더욱 개선하고, 다양한 응용 분야에 적용하여 그 효용성을 극대화하는 방안을 모색할 필요가 있습니다.  **모델의 경량화** 및 **범용성 확보** 또한 중요한 연구 과제입니다.

#### CRPO Alignment
본 논문에서 제시된 CRPO (CLAP-Ranked Preference Optimization) 정렬 기법은 기존의 텍스트-오디오 생성 모델의 한계를 극복하기 위한 혁신적인 접근 방식입니다. **기존 방법들이 어려움을 겪던 오디오 선호도 쌍 생성 문제를, CLAP 모델을 프록시 보상 모델로 활용하여 효과적으로 해결**합니다.  CRPO는 반복적인 데이터 샘플링, 선호도 쌍 생성 및 선호도 최적화 과정을 통해 모델의 정렬 성능을 향상시키는 데 초점을 맞춥니다.  **온라인 데이터 생성 전략을 통해 오프라인 방식의 한계를 극복하고 성능 저하를 방지**하며, **CLAP 모델을 이용한 효율적인 선호도 데이터 생성**은 모델의 학습 효율성을 높이는 데 기여합니다.  결과적으로 CRPO는 **보다 빠르고 정확한 텍스트-오디오 생성을 가능하게** 하며, 향상된 품질과 일관성을 제공하여,  **다양한 응용 분야에서 혁신적인 결과**를 보여줍니다.  **CRPO의 효율성과 성능 향상**은 특히 다중 이벤트를 포함하는 복잡한 프롬프트 처리에 있어 두드러지게 나타납니다.

#### Rectified Flow
본 논문에서 제시된 'Rectified Flow'는 기존 확산 모델(diffusion model)의 한계를 극복하기 위한 핵심적인 기법입니다. 기존 확산 모델은 노이즈 스케줄러(noise scheduler)에 민감하고, 많은 샘플링 단계를 필요로 하여 속도가 느린 단점이 있습니다.  **Rectified Flow는 이러한 문제를 해결하기 위해 노이즈와 출력 오디오 간의 직선 경로(straight path)를 학습하여, 더 적은 샘플링 단계로도 고품질 오디오를 생성할 수 있도록 합니다.** 이는 훈련 과정을 간소화하고 연산 비용을 절감하는 데 기여합니다. **특히, 본 논문에서는 rectified flow를  text-to-audio 생성 모델인 TANGOFLUX에 적용하여 빠른 추론 속도와 높은 오디오 품질을 동시에 달성**하였습니다.  **Rectified flow는 훈련 및 추론 과정의 효율성을 높여 실제 적용 가능성을 크게 향상**시켰다는 점에서 중요한 의미를 지닙니다.  더 나아가,  **CLAP-Ranked Preference Optimization (CRPO)와의 결합을 통해 선호도 학습(preference learning)의 효율성 또한 증대**시켰습니다.  결론적으로,  Rectified Flow는 text-to-audio 분야에서 모델의 효율성과 성능을 개선하는 데 중요한 역할을 수행하며,  **향후 연구에서도 효율적인 생성 모델 개발에 있어 중요한 참고 자료**가 될 것으로 예상됩니다.

#### Benchmark Results
본 논문의 벤치마크 결과는 **TANGOFLUX 모델이 기존 최첨단 Text-to-Audio (TTA) 모델들보다 우수한 성능을 보임**을 보여줍니다. 특히 다양한 객관적 지표(CLAP, FD, KL)에서 일관되게 높은 점수를 기록하며, **특히 다중 이벤트를 포함하는 복잡한 프롬프트에 대해서도 뛰어난 성능**을 유지합니다.  이는 TANGOFLUX의 효율적인 rectified flow 기반 아키텍처와 CLAP-Ranked Preference Optimization (CRPO) 전략의 효과를 입증하는 것입니다.  **CRPO는 기존의 방법보다 더 나은 오디오 선호도 데이터셋을 생성**하여 모델 성능 향상에 기여했습니다.  더불어, **TANGOFLUX는 빠른 추론 속도**를 제공하며, 이는 실제 응용 프로그램에 있어서 중요한 장점입니다.  **주목할 만한 점은 적은 매개변수로도 높은 성능을 달성**했다는 것입니다.  하지만, 주관적 평가 결과에 대한 추가 분석이 필요하며, 다양한 종류의 오디오 데이터셋을 사용한 추가 실험을 통해 일반화 성능을 더 검증할 필요가 있습니다.

#### Future of TTA
**텍스트 음성 변환(TTA)의 미래는 밝지만 도전과제도 많습니다.** 고품질, 다양한 스타일의 음성 생성, 빠른 추론 속도, 그리고 다양한 언어 지원은 앞으로 해결해야 할 주요 과제입니다.  **개인 맞춤형 음성 생성**은 특히 중요한데, 사용자의 목소리와 발음 특징을 반영하여 자연스럽고 개성있는 음성을 만들어내는 기술 개발이 필요합니다.  또한, **데이터 효율성 및 접근성** 문제도 해결해야 합니다.  **대규모 데이터셋**을 구축하고 관리하는 비용과 시간이 많이 들기 때문입니다.  마지막으로, **윤리적인 고려사항**도 중요합니다.  딥페이크와 같은 악용 가능성을 막고,  공정하고 편향되지 않은 TTA 모델 개발이 필요합니다.  이러한 과제들을 해결하기 위해서는 학계, 산업계, 정부의 협력이 필수적입니다.  **연구 개발 투자**, **데이터 공유**, **윤리적 가이드라인 제정** 등을 통해 TTA 기술의 긍정적인 발전을 도모해야 합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.21037/x2.png)

> 🔼 그림 2는 훈련 반복 횟수에 따른 CLAP 점수와 KL 발산의 추이를 보여줍니다. 이 그래프는 온라인 훈련과 오프라인 훈련 간의 뚜렷한 차이를 보여줍니다. 오프라인 훈련은 두 번째 반복에서 CLAP 점수가 최고점에 도달하고 KL 발산이 증가하는 것을 보여주는 반면, 온라인 훈련은 네 번째 반복까지 CLAP 점수가 계속 증가하고 KL 발산은 지속적으로 감소하는 것을 보여줍니다. 이는 온라인 훈련이 오프라인 훈련보다 더 효과적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: The trajectory of CLAP score and KL divergence across the training iterations. This plot shows the stark difference between online and offline training. Offline training clearly peaks early, by the second iteration, indicated by the peaking CLAP score and increasing KL. In contrast, the CLAP score of online training continues to increase until iteration 4, while the KL divergence has a clear downward trend throughout.
> </details>



![](https://arxiv.org/html/2412.21037/extracted/6101841/images/clap_vs_time_with_steps_legend.png)

> 🔼 그림 3은 각 반복에서  ℒDPO-FM 와 ℒCRPO 의 승자 손실과 패자 손실을 보여줍니다. 승자와 패자 손실 모두 각 반복마다 증가하고, 그 차이(마진) 또한 증가합니다. 이는 DPO(Direct Preference Optimization)를 사용하여 수정된 흐름(Rectified Flow)을 정렬할 때 승자와 패자의 상대적 가능성을 최적화하는 방식을 보여줍니다.  손실의 절대적인 크기보다는 두 손실 간의 마진이 중요하다는 점에 유의해야 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Winning and Losing losses of ℒDPO-FMsubscriptℒDPO-FM\mathcal{L}_{\text{DPO-FM}}caligraphic_L start_POSTSUBSCRIPT DPO-FM end_POSTSUBSCRIPT and ℒCRPOsubscriptℒCRPO\mathcal{L}_{\text{CRPO}}caligraphic_L start_POSTSUBSCRIPT CRPO end_POSTSUBSCRIPT at each iteration. Winning and Losing losses increase each iteration, as well as their margin.
> </details>



![](https://arxiv.org/html/2412.21037/extracted/6101841/images/fd_vs_time_without_legend.png)

> 🔼 그림은 제목에서 알 수 있듯이 CLAP 점수를 기반으로 한 결과를 보여줍니다.  CLAP 점수는 텍스트와 오디오 간의 유사도를 측정하는 지표이며, 점수가 높을수록 텍스트와 오디오가 잘 일치함을 의미합니다. 그림은  TANGOFLUX 모델과 다른 모델들의 성능을 비교하여 TANGOFLUX 모델의 우수성을 보여주는 데 사용되었습니다.  그림 자체는 간략하게 CLAP 점수만 표시하고 있지만, 논문의 내용을 참고하면  TANGOFLUX 모델이 다른 모델들보다 훨씬 높은 CLAP 점수를 기록하여 더 정확하고 충실하게 텍스트를 오디오로 변환했음을 알 수 있습니다. 
> <details>
> <summary>read the caption</summary>
> (a) CLAPscorescore{}_{\text{score}}start_FLOATSUBSCRIPT score end_FLOATSUBSCRIPT
> </details>



![](https://arxiv.org/html/2412.21037/extracted/6101841/images/annotation_form_tangoflux.png)

> 🔼 이 그림은 논문의 3.3절(객관적 평가)에서 다양한 텍스트 음성 생성 모델들의 성능을 비교 분석한 결과를 보여줍니다.  정확히는 Fréchet Distance (FD) 지표를 사용하여 생성된 오디오의 품질을 평가한 결과입니다. FDopenl3openl3{}_{ text{openl3}}는 오디오 품질을 평가하는 지표 중 하나이며, 낮을수록 생성된 오디오의 품질이 실제 오디오와 유사하다는 것을 의미합니다. 그림은 서로 다른 모델들의 FDopenl3openl3{}_{ text{openl3}}값을 비교하여 각 모델의 오디오 생성 성능 차이를 시각적으로 나타냅니다.  각 모델의 성능 차이를 명확히 보여주어 TANGOFLUX 모델의 우수성을 강조하는 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> (b) FDopenl3openl3{}_{\text{openl3}}start_FLOATSUBSCRIPT openl3 end_FLOATSUBSCRIPT
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Inference | Time (s) |
|---|---|{{< /table-caption >}}
> 🔼 표 2는 다중 이벤트 입력에 대한 다양한 음성합성 모델의 성능 비교 결과를 보여줍니다.  단순히 캡션만으로는 알 수 없는 세부적인 내용으로, 각 모델(AudioLDM 2-large, Stable Audio Open, Tango 2, TANGOFLUX-base, TANGOFLUX)의 매개변수 수, 생성된 오디오 길이,  Fréchet Distance (FDopenl3), Kullback-Leibler divergence (KLpasst), CLAP 점수, Inception Score (IS) 등의 지표를 사용하여 성능을 평가한 결과가 포함되어 있습니다.  다중 이벤트가 포함된 프롬프트를 사용하여 모델의 복잡한 지시사항 이해 및 처리 능력을 평가했음을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Comparison of text-to-audio models on multi-event inputs.
> </details>

{{< table-caption >}}
| Model | #Params. | Duration | FD<sub>openl3</sub> ↓ | KL<sub>passt</sub> ↓ | CLAP<sub>score</sub> ↑ | IS ↑ |
|---|---|---|---|---|---|---|
| AudioLDM 2-large | 712M | 10 sec | 107.9 | 1.83 | 0.415 | 7.3 |
| Stable Audio Open | 1056M | 47 sec | 88.5 | 2.67 | 0.286 | 9.3 |
| Tango 2 | 866M | 10 sec | 108.3 | 1.14 | 0.452 | 8.4 |
| TangoFlux-base | 515M | 30 sec | 79.7 | 1.23 | 0.438 | 10.7 |
| TangoFlux | 515M | 30 sec | 75.2 | 1.20 | 0.488 | 11.1 |{{< /table-caption >}}
> 🔼 표 3은 음성 선호도 미세 조정에 사용된 서로 다른 선호도 데이터셋의 비교 결과를 보여줍니다.  지표는 다음과 같습니다:  FDopenl3openl3{}_{\text{openl3}}start_FLOATSUBSCRIPT openl3 end_FLOATSUBSCRIPT (프레셰 거리), KLpasstpasst{}_{\text{passt}}start_FLOATSUBSCRIPT passt end_FLOATSUBSCRIPT (KL 발산), CLAPscorescore{}_{\text{score}}start_FLOATSUBSCRIPT score end_FLOATSUBSCRIPT (정렬). 이 표는 서로 다른 선호도 데이터셋(BATON, Audio Alpaca, CRPO)을 사용하여 미세 조정한 모델의 성능을 비교하여 CRPO 데이터셋의 효과를 보여줍니다. 각 지표는 음성 생성 모델의 정확성과 품질을 평가하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Comparison of difference preference dataset used for preference tuning. Metrics include FDopenl3openl3{}_{\text{openl3}}start_FLOATSUBSCRIPT openl3 end_FLOATSUBSCRIPT for Frechet Distance, KLpasstpasst{}_{\text{passt}}start_FLOATSUBSCRIPT passt end_FLOATSUBSCRIPT for KL divergence, and CLAPscorescore{}_{\text{score}}start_FLOATSUBSCRIPT score end_FLOATSUBSCRIPT for alignment.
> </details>

{{< table-caption >}}
| Dataset | FD<SUB>openl3</SUB> ↓ | KL<SUB>passt</SUB> ↓ | CLAP<SUB>score</SUB> ↑ |
|---|---|---|---|
| BATON | 80.5 | 1.20 | 0.437 |
| Audio Alpaca | 80.0 | 1.20 | 0.448 |
| CRPO | 79.1 | 1.18 | 0.453 |{{< /table-caption >}}
> 🔼 표 4는 음성 선호도 데이터셋을 미세 조정하는 데 사용된 다양한 데이터셋을 비교한 표입니다.  측정 지표는 Fréchet Distance(FDopenl3), KL divergence(KLpasst), 그리고 alignment(CLAPscore)를 포함합니다.  본 표는 각 데이터셋을 사용하여 미세 조정한 모델의 성능을 평가하는 데 사용되는 세 가지 측정 지표의 수치를 보여줍니다.  이는 모델의 음질, 설명과의 일관성, 그리고 전반적인 성능을 평가하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Comparison of different preference datasets used for preference tuning. Metrics include FDopenl3openl3{}_{\text{openl3}}start_FLOATSUBSCRIPT openl3 end_FLOATSUBSCRIPT for Fréchet Distance, KLpasstpasst{}_{\text{passt}}start_FLOATSUBSCRIPT passt end_FLOATSUBSCRIPT for KL divergence, and CLAPscorescore{}_{\text{score}}start_FLOATSUBSCRIPT score end_FLOATSUBSCRIPT for alignment.
> </details>

{{< table-caption >}}
| Model | N | FD<sub>openl3</sub> ↓ | KL<sub>passt</sub> ↓ | CLAP<sub>score</sub> ↑ |
|---|---|---|---|---|
| **TangoFlux** | 1 | 75.0 | 1.15 | 0.480 |
|  | 5 | 74.3 | 1.14 | 0.494 |
|  | 10 | 75.8 | 1.08 | 0.499 |
|  | 15 | 75.1 | 1.11 | 0.502 |
| `Tango 2` | 1 | 108.4 | 1.11 | 0.447 |
|  | 5 | 108.8 | 1.05 | 0.467 |
|  | 10 | 108.4 | 1.08 | 0.474 |
|  | 15 | 108.7 | 1.06 | 0.473 |{{< /table-caption >}}
> 🔼 표 5는 인간 평가자들이 평가한 오디오 품질(OVL)과 관련성(REL)이라는 두 가지 속성에 대한 결과를 보여줍니다.  이 표는 개별 평가자의 편향을 완화하고 상대적 성능 비교를 제시하기 위해 z 점수, 순위, Elo 점수를 보고합니다.  z 점수는 평가자의 평점의 표준화된 점수를 나타내고, 순위는 모델의 평균 및 최빈 순위를 보여주며, Elo 점수는 모델의 상대적 성능을 확률적이고 연속적인 점수로 나타냅니다.  이를 통해 다양한 관점에서 모델들의 성능을 종합적으로 비교 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Human evaluation results on two attributes: OVL (overall quality) and REL (relevance). We report the z-scores, ranking, and Elo scores to mitigate individual annotator biases and present a relative performance comparison.
> </details>

{{< table-caption >}}
| Model | z-scores |  | Ranking |  | Elo |  |
|---|---|---|---|---|---|---|---|
|  | OVL | REL | OVL | REL | OVL | REL |  |
| **Model** | **z-scores** |  | **Ranking** |  | **Elo** |  |  |
|  | **OVL** | **REL** | **Mean** | **Mode** | **Mean** | **Mode** | **OVL** | **REL** |
| AudioLDM 2 | -0.3020 | -0.4936 | 3.5 | 4 | 3.7 | 4 | 1,236 | 1,196 |
| Stable Audio Open | 0.0723 | -0.3584 | 2.4 | 1, 3 | 3.3 | 3 | 1,444 | 1,268 |
| Tango 2 | -0.019 | 0.1602 | 2.4 | 2 | 1.9 | 2 | 1,419 | 1,507 |
| **TangoFlux** | **0.2486** | **0.6919** | **1.7** | **2** | **1.1** | **1** | **1,501** | **1,628** |{{< /table-caption >}}
> 🔼 표 6은 다양한 Classifier-Free Guidance (CFG) 값을 사용했을 때 TANGOFLUX 모델의 성능을 보여줍니다.  CFG 값을 변경하면 모델의 충실도와 의미적 일관성 사이에 상충 관계가 발생하는 것을 보여주며,  실험 결과를 통해 최적의 CFG 값을 제시합니다.  구체적으로,  다양한 CFG 값에 따른 Fréchet Distance (FD), Kullback-Leibler divergence (KL), 그리고 CLAP 점수를 비교 분석하여 모델 성능에 미치는 영향을 정량적으로 평가합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: TangoFlux with different classifier free guidance (CFG) values.
> </details>

{{< table-caption >}}
| Model | Steps | CFG | FD<SUB>openl3</SUB> ↓ | KL<SUB>passt</SUB> ↓ | CLAP<SUB>score</SUB> ↑ |
|---|---|---|---|---|---| 
| **TangoFlux** | 50 | 3.0 | 77.7 | **1.14** | 0.479 |
|  | 50 | 3.5 | 76.1 | **1.14** | **0.481** |
|  | 50 | 4.0 | 74.9 | 1.15 | 0.476 |
|  | 50 | 4.5 | 75.1 | 1.15 | 0.480 |
|  | 50 | 5.0 | **74.6** | 1.15 | 0.472 |{{< /table-caption >}}
> 🔼 표 7은 논문의 인간 평가 부분에서 사용된 프롬프트들의 특징을 보여줍니다. 각 프롬프트는 여러 개의 사운드 이벤트를 포함하고 있으며, 이러한 이벤트들이 시간 순서대로 정렬되어 있는지 여부를 나타내는 Temporal Events 열이 추가되어 있습니다.  Multiple Events 열은 프롬프트에 포함된 사운드 이벤트의 개수를 나타냅니다. 이 표는 인간 평가자들이 다양하고 복잡한 오디오를 평가하는 데 사용된 프롬프트의 특성을 보다 명확하게 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Prompts used in human evaluation and their characteristics.
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