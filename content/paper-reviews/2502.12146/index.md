---
title: "Diffusion-Sharpening: Fine-tuning Diffusion Models with Denoising Trajectory Sharpening"
summary: "Diffusion-Sharpening: 샘플링 경로 최적화를 통한 확산 모델 미세 조정으로, 빠른 수렴과 향상된 추론 효율성 달성!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Generation", "🏢 Peking University",]
showSummary: true
date: 2025-02-17
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.12146 {{< /keyword >}}
{{< keyword icon="writer" >}} Ye Tian et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-18 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.12146" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.12146" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/diffusion-sharpening-fine-tuning-diffusion" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 확산 모델 미세 조정 방법들은 **단일 학습 단계에만 초점**을 맞추거나 **추론 비용이 과다**하여 실제 적용에 어려움이 있었습니다. 본 논문에서는 **샘플링 경로 전체**를 최적화하는 새로운 방법인 Diffusion-Sharpening을 제안합니다.



Diffusion-Sharpening은 **경로 적분을 이용**하여 최적의 샘플링 경로를 선택하고, **보상 피드백**을 통해 모델을 학습시킵니다.  **SFT 및 RLHF 기반의 두 가지 구현 방식**을 제공하여 다양한 상황에 유연하게 적용할 수 있습니다. 실험 결과, Diffusion-Sharpening은 기존 방법들보다 빠른 수렴 속도와 향상된 추론 효율성을 보였으며, 다양한 평가 지표에서 우수한 성능을 달성했습니다.  이는 **텍스트 정렬, 구성 능력, 사용자 선호도** 등 다양한 측면에서의 성능 향상을 의미합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 샘플링 경로 최적화를 통해 확산 모델 미세 조정의 효율성을 크게 향상시켰습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 기존 RL 기반 방법 및 샘플링 경로 최적화 방법보다 다양한 지표에서 우수한 성능을 달성했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} SFT 및 RLHF 기반 두 가지 구현 방식을 제공하여 다양한 상황에 적용 가능성을 높였습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **확산 모델의 미세 조정에 대한 새로운 접근 방식**을 제시하여 기존 방법의 한계를 극복하고 향상된 성능과 효율성을 달성함으로써, **향후 연구에 새로운 가능성**을 제시합니다. 특히, 샘플링 경로 최적화를 통해 추론 비용을 줄이고 다양한 지표에서 우수한 성능을 보이는 것은 **실제 응용 분야에 대한 파급 효과**가 클 것으로 예상됩니다. 또한, 제시된 방법은 다양한 보상 모델과 호환되므로 **다양한 응용 분야**에 적용될 수 있는 확장성을 가지고 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.12146/x1.png)

> 🔼 그림 1은 보상 기반 최적화를 위한 세 가지 확산 모델 기반 방법을 비교한 것입니다. (i) 확산 강화 학습은 단일 훈련 단계에 초점을 맞춰 보상 신호를 최적화합니다. (ii) 확산 샘플링 경로 최적화는 샘플링 과정 전체에 걸쳐 최적화를 확장하여 생성 성능을 향상시킵니다. 하지만 이 방법은 상당한 추론 비용을 초래합니다. (iii) 확산 선명화는 경로 적분 프레임워크를 사용하여 훈련 중에 최적의 샘플링 경로를 선택하고 보상 피드백을 활용하여 추론 비용을 절감합니다. 이 그림은 세 가지 방법의 차이점과 확산 선명화의 효율성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Comparison of Three Diffusion-Based Methods for Reward-Driven Optimization: (i) Diffusion Reinforcement Learning, (ii) Diffusion Sampling Trajectory Optimization, and (iii) Diffusion Sharpening.
> </details>





{{< table-caption >}}
| Model | CLIP Score | Color | Shape | Texture | Spatial | Non-Spatial | Complex | Aesthetic | ImageReward | MLLM |
|---|---|---|---|---|---|---|---|---|---|---|
| SDXL | 0.322 | 0.6369 | 0.5408 | 0.5637 | 0.2032 | 0.3110 | 0.4091 | 5.531 | 0.780 | 0.780 |
| **Fine-tuning based Methods** |  |  |  |  |  |  |  |  |  |  |
| Standard Fine-tuning | 0.325 | 0.6437 | 0.5771 | 0.5692 | 0.2084 | 0.3147 | 0.4100 | 5.556 | 0.791 | 0.784 |
| Diffusion DPO (Wallace et al., 2024) | 0.334 | 0.6602 | 0.5553 | 0.5640 | 0.2112 | 0.3180 | 0.4055 | 5.754 | 1.352 | 0.864 |
| DDPO (Black et al., 2024) | 0.324 | 0.6435 | 0.5365 | 0.5531 | 0.2030 | 0.3142 | 0.4024 | 5.640 | 0.910 | 0.791 |
| D3PO (Yang et al., 2024a) | 0.328 | 0.6434 | 0.5435 | 0.5657 | 0.2114 | 0.3153 | 0.4102 | 5.528 | 0.982 | 0.785 |
| IterPO (Zhang et al., 2024b) | 0.335 | 0.6637 | 0.5593 | 0.6167 | 0.2128 | 0.3207 | 0.4377 | 5.923 | 1.408 | 0.884 |
| **Sampling Trajectory Optimization Methods** |  |  |  |  |  |  |  |  |  |  |
| Free<sup>2</sup>Guide (Kim et al., 2024) | 0.325 | 0.6321 | 0.5386 | 0.5548 | 0.2050 | 0.3125 | 0.4082 | 5.560 | 0.873 | 0.786 |
| Demon (Yeh et al., 2024) | 0.325 | 0.6502 | 0.5507 | 0.5602 | 0.2150 | 0.3158 | 0.4070 | 5.630 | 1.243 | 0.300 |
| Inference Scaling (Ma et al., 2025) | 0.328 | 0.6550 | 0.5527 | 0.5700 | 0.2204 | 0.3168 | 0.4265 | 5.752 | 1.329 | 0.872 |
| SFT Diffusion Sharpening | 0.334 | 0.6578 | 0.5692 | 0.5733 | 0.2120 | 0.3185 | 0.4125 | 5.785 | 1.301 | 0.864 |
| **RLHF Diffusion Sharpening** | 0.338 | 0.6841 | 0.5680 | 0.6401 | 0.2134 | 0.3220 | 0.4498 | 5.956 | 1.445 | 0.921 |{{< /table-caption >}}

> 🔼 표 1은 다양한 평가 지표에 걸쳐 여러 모델의 성능을 비교한 표입니다.  표에는 표준 미세 조정, 확산 DPO, DDPO, D3PO, IterPO와 같은 미세 조정 기반 방법과 Free Guide, Demon, Inference Scaling과 같은 샘플링 경로 최적화 방법의 결과가 포함되어 있습니다.  비교 대상에는 제안된 SFT 확산 선명화 및 RLHF 확산 선명화 방법도 포함됩니다. 각 모델은 CLIP 점수, 심미적 점수, MLLM 평가자 점수, 이미지 보상 점수, 색상, 모양, 질감, 공간적, 비공간적 복잡도와 같은 여러 지표를 사용하여 평가됩니다. 이 표는 여러 가지 방법론적 접근 방식에 대한 성능을 종합적으로 비교 분석하고, 제안된 확산 선명화 기법이 다른 방법에 비해 우수함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparison of Model Performance across Multiple Metrics
> </details>





### In-depth insights


#### Trajectory Optimization
본 논문에서 제시하는 **트레이젝토리 최적화**는 단순히 확률적 미분 방정식(SDE) 기반 확산 모델의 단일 시점을 최적화하는 것이 아니라, **전체 샘플링 과정의 경로(트레이젝토리)를 최적화**하는 데 초점을 맞춥니다. 이를 통해 기존 방법들이 간과했던 **트레이젝토리 수준의 정렬**을 달성하고, **추론 시 추가적인 계산 비용 없이 우수한 추론 효율성**을 확보할 수 있습니다. **경로 적분**을 활용하여 다양한 경로를 샘플링하고 보상을 계산하여 최적의 경로를 선택함으로써, **훈련 효율성을 높이고 빠른 수렴**을 가능하게 합니다.  **지도 학습 기반 방식과 강화 학습 기반 방식** 두 가지를 제시하여 다양한 상황에 적용 가능성을 높였으며, 다양한 평가 지표에서 기존 방법들을 능가하는 성능을 보입니다. 특히, **RLHF-Diffusion-Sharpening**은 데이터 준비 없이 자체적으로 긍정적, 부정적 샘플을 생성하여 자기 주도적 학습을 달성하는 점이 핵심입니다.  결론적으로, 본 논문의 트레이젝토리 최적화는 **확산 모델의 미세 조정**을 위한 **효율적이고 확장 가능한 솔루션**을 제공합니다.

#### SFT vs RLHF
본 논문은 확산 모델 미세 조정을 위한 두 가지 주요 방법인 SFT(Supervised Fine-Tuning)와 RLHF(Reinforcement Learning from Human Feedback)의 차이점과 장단점을 심층적으로 비교 분석합니다. **SFT는 기존의 지도 학습 방식을 활용하여, 대량의 이미지-텍스트 데이터셋을 이용하여 모델을 미세 조정**합니다. 이는 구현이 간단하고 학습 속도가 빠르다는 장점이 있지만, **데이터셋의 품질에 크게 의존하며, 다양한 사용자 선호도를 반영하기 어렵다**는 단점이 있습니다. 반면에 **RLHF는 사람의 피드백을 강화 학습에 활용하여 모델의 성능을 향상**시키는 방식입니다. 이는 **사용자 선호도를 직접적으로 반영**할 수 있고, **보다 다양하고 세련된 결과물을 생성**할 수 있지만, **구현이 복잡하고, 사람의 피드백을 수집하는 데 많은 비용과 시간이 소요**된다는 단점이 있습니다. 따라서 각 방법의 특징을 고려하여, 사용 목적과 상황에 맞는 최적의 방법을 선택하는 것이 중요하며, **본 논문에서 제시된 Diffusion-Sharpening 기법은 두 방법의 장점을 결합하여 효율성과 성능을 동시에 개선**하고자 하는 시도로 해석될 수 있습니다.

#### Reward Model Impact
본 논문에서 다루는  "Reward Model Impact" 에 대한 심층적인 분석은 다양한 보상 모델이 확산 모델 미세 조정 성능에 미치는 영향을 면밀히 조사하는 데 중점을 둡니다. **CLIP Score, Compositional Reward, MLLM grader, Human Preference와 같은 여러 보상 모델을 사용하여 실험을 수행하고 각 모델의 강점과 약점을 비교 분석합니다.** 이를 통해 어떤 유형의 보상 모델이 특정 하위 작업에 가장 적합한지, 그리고 어떻게 모델 성능을 개선할 수 있는지에 대한 귀중한 통찰력을 얻을 수 있습니다. **특히, 다양한 보상 신호의 조합을 통해 모델의 성능을 더욱 향상시킬 수 있는 가능성을 제시합니다.** 또한, 보상 모델의 선택이 최종 결과물의 질, 일관성, 창의성 등에 어떤 영향을 미치는지에 대한 정성적, 정량적 분석을 통해 보상 모델의 중요성을 보다 명확히 드러냅니다. **결과적으로, 이러한 분석은 미래의 확산 모델 미세 조정 연구에 있어서 보상 모델의 설계 및 선택에 대한 중요한 지침을 제공합니다.**

#### Efficiency Gains
본 논문은 확산 모델 미세 조정에서 **샘플링 경로 최적화**를 통해 효율성을 크게 향상시키는 방법인 Diffusion-Sharpening을 제시합니다. 기존 방법들과 달리, Diffusion-Sharpening은 **훈련 중에 최적 경로를 선택**하고 추론 비용을 절감하여 빠른 수렴과 우수한 추론 효율성을 달성합니다. 특히, SFT-Diffusion-Sharpening과 RLHF-Diffusion-Sharpening 두 가지 구현 방식을 통해 다양한 보상 모델과 호환성을 높였습니다. 실험 결과, Diffusion-Sharpening은 기존 미세 조정 및 샘플링 경로 최적화 방법들보다 **텍스트 정렬, 구성 능력 및 사용자 선호도** 측면에서 우수한 성능을 보였습니다.  **훈련 및 추론 속도 향상**은 Diffusion-Sharpening의 중요한 장점이며, 향후 확산 모델 미세 조정 연구에 기여할 것으로 기대됩니다.  **계산 비용 감소**는 실제 응용에 중요한 의미를 가지며, 본 연구는 이러한 측면에서 상당한 진전을 보여줍니다.

#### Future Directions
본 논문에서 제시된 Diffusion-Sharpening 기법은 확산 모델의 미세 조정을 위한 효율적이고 확장 가능한 솔루션을 제공하지만, **향후 연구 방향**은 다음과 같이 제시될 수 있습니다.  먼저, **다양한 보상 모델(Reward Model)의 탐색 및 개발**이 중요합니다. 본 논문에서는 CLIP Score, Compositional Reward, MLLM, Human Preference 등 다양한 보상 모델을 사용하였지만,  더욱 정교하고 다차원적인 평가 기준을 반영하는 새로운 보상 모델을 개발하여 모델 성능을 더욱 향상시킬 수 있을 것입니다.  또한, **현재 2가지 방법론(SFT, RLHF) 외에 다양한 학습 전략**을  Diffusion-Sharpening에 적용하는 연구가 필요합니다.  예를 들어, 강화학습 기법의 발전을 활용하거나,  비지도 학습 방식을 도입하여 데이터 의존성을 줄이는 방안을 모색할 수 있습니다. 마지막으로, **더욱 다양한 확산 모델 및 애플리케이션**에  Diffusion-Sharpening을 적용하는 실험이 필요합니다.  본 논문에서는 SDXL 모델을 중심으로 실험을 진행했지만, 다른 유형의 확산 모델이나 이미지 생성 외의 다른 분야 (예: 음성 합성, 비디오 생성)에도 적용 가능성을 검증하는 것이 중요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.12146/x2.png)

> 🔼 그림 2는 제안된 확산 모델 개선 프레임워크인 'Diffusion Sharpening'의 전반적인 과정을 보여줍니다. (i)는 학습 단계를 나타내는데, 잡음이 추가된 이미지에서 시작하여 여러 경로의 샘플링 과정을 거치고, 보상 모델을 통해 각 경로의 보상을 평가하여 최적의 경로를 선택하는 과정을 보여줍니다. (ii)는 추론 단계를 나타내는데, 학습된 모델을 이용하여 최적의 샘플링 경로를 따라 이미지를 생성하는 과정입니다. (iii)는 다양한 보상 모델 선택지를 보여주는데, CLIP 점수, 구성적 보상, 다중 모달 대형 언어 모델(MLLM) 평가 점수, 그리고 사람의 선호도 등 다양한 기준을 보상으로 사용할 수 있음을 시각적으로 보여줍니다. 이 그림은 Diffusion Sharpening이 어떻게 샘플링 경로를 최적화하여 이미지 생성 성능을 향상시키는지를 개괄적으로 설명합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Overview of Our Diffusion Sharpening Framework: (i) Training, (ii) Inference, and (iii) Reward Model Selection
> </details>



![](https://arxiv.org/html/2502.12146/x3.png)

> 🔼 그림 3은 다양한 보상 모델을 사용하여 확산 모델 미세 조정에서 SFT 확산 선명화 및 RLHF 확산 선명화의 효과를 보여주는 정성적 결과를 비교한 것입니다. CLIP 점수, 구성 보상, MLLM 및 인간 선호도를 보상 모델로 사용하여 생성된 이미지가 표시됩니다. 각 보상 모델은 이미지 생성에 다른 초점을 맞추고 있으며, 그에 따라 생성된 이미지의 특징도 다릅니다. 예를 들어, CLIP 점수를 보상 모델로 사용하면 이미지와 텍스트 간의 일관성이 높아지고, 구성 보상을 사용하면 이미지의 구성 요소 간의 관계가 더 잘 표현됩니다. MLLM은 이미지의 미학적 측면과 일관성에 중점을 두어 전체적인 품질 향상에 기여합니다. 인간 선호도를 사용하면 사용자의 주관적인 기호를 반영하여 생성된 이미지의 만족도를 높일 수 있습니다. SFT 확산 선명화와 RLHF 확산 선명화는 모두 미세 조정 성능을 향상시키지만, RLHF 확산 선명화는 데이터 큐레이션이 필요없이 온라인 방식으로 미세 조정을 수행하므로 더욱 효율적입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Qualitative results comparing Diffusion Sharpening methods using different reward models. The images show the generated results with CLIP Score, Compositional Reward, MLLM, and Human Preferences as reward models, showcasing the effectiveness of SFT Diffusion Sharpening and RLHF Diffusion Sharpening in diffusion finetuning.
> </details>



![](https://arxiv.org/html/2502.12146/x4.png)

> 🔼 그림 4는 서로 다른 세 가지 데이터셋(JourneyDB, Text-to-Image-2M, Pokemon)에서 SDXL 모델을 미세 조정하는 동안 손실 함수 값의 변화를 보여줍니다.  세 가지 데이터셋 모두에서 기본 SDXL 모델(Baseline)과 비교하여 SFT Diffusion-Sharpening 기법을 적용했을 때 손실 함수가 더 빠르게 감소하는 것을 확인할 수 있습니다. 이는 SFT Diffusion-Sharpening 기법이 미세 조정 과정에서 효율성을 높인다는 것을 시각적으로 보여주는 결과입니다.  각 데이터셋 별로 손실 함수 값이 감소하는 추세와 그 속도를 비교하여 미세 조정 성능의 차이를 명확하게 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: SDXL Finetuning Loss across Difference Datasets. Here ”Diffusion-Sharpening” represents SFT Diffusion-Sharpening specifically.
> </details>



![](https://arxiv.org/html/2502.12146/x5.png)

> 🔼 그림 5는 확산 모델 미세 조정에서 제안된 방법인 Diffusion Sharpening의 추론 성능을 보여줍니다.  x축은 추론에 사용된 노이즈 제거 단계의 수(NFE)를 나타내고, y축은 CLIP 점수를 나타냅니다.  이 그래프는 Diffusion Sharpening이 기존의 방법들(Demon, Free Guide, Inference Scaling)보다 훨씬 적은 NFE로도 우수한 CLIP 점수를 달성함을 보여줍니다. 기존 방법들은 높은 품질의 이미지 생성을 위해 많은 NFE가 필요하지만, Diffusion Sharpening은 훈련 중에 추론 최적화를 통합하여 적은 NFE로도 우수한 성능을 유지합니다. 이는 Diffusion Sharpening이 효율적인 추론 성능을 가짐을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Inference Performance of Diffusion Sharpening.
> </details>



![](https://arxiv.org/html/2502.12146/x6.png)

> 🔼 그림 6은 본 논문에서 제안하는 Diffusion Sharpening 방법의 효과를 보여주는 곡선 그래프입니다.  SFT(Supervised Fine-tuning) Diffusion Sharpening과 RLHF(Reinforcement Learning from Human Feedback) Diffusion Sharpening 두 가지 방법에 대해 훈련 단계별 보상(Reward) 값의 변화를 보여줍니다. 그래프는 훈련 과정에서 보상 값이 점진적으로 증가하고,  표준편차가 감소하는 것을 보여주어, Diffusion Sharpening 기법을 통해 모델이 최적의 샘플링 경로를 찾아가는 학습 과정을 효과적으로 시각적으로 보여줍니다.  그림을 통해 Diffusion Sharpening 기법이 안정적이고 효율적인 훈련을 가능하게 함을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Diffusion Sharpening Fine-tuning Reward Curve.
> </details>



![](https://arxiv.org/html/2502.12146/x7.png)

> 🔼 그림 7은 사용자 연구를 통해 제안된 확산 예리화 방법과 다른 방법들을 비교 분석한 결과를 보여줍니다. 사용자들은 세 가지 옵션(방법 1, 방법 2, 비교 결과) 중에서 선호하는 이미지를 선택하였습니다.  결과는 제안된 방법이 다른 방법들보다 더 많은 사용자 선호도를 얻었음을 보여줍니다. 이는 제안된 방법의 효과성을 추가적으로 입증하는 것입니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: User Study about Comparision with Other Methods
> </details>



![](https://arxiv.org/html/2502.12146/x8.png)

> 🔼 이 그림은 논문의 MMLLM 평가자를 사용한 평가에 대한 자세한 프롬프트를 보여줍니다.  MMLLM 평가자는 이미지 생성 모델의 성능을 평가하기 위해 사용되는 다중 모달 대규모 언어 모델입니다.  이 프롬프트는 평가자가 이미지의 정확성, 창의성, 시각적 품질, 일관성, 감정적 공명 등 다양한 측면을 평가하고 각 측면에 대한 점수 (0~10) 와 그 이유에 대한 간략한 설명을 제공하도록 안내합니다. 최종적으로는 이러한 개별 점수들을 종합하여 이미지에 대한 전반적인 점수를 산출하도록 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: The detailed prompt for evaluation with the MMLLM Grader.
> </details>



![](https://arxiv.org/html/2502.12146/x9.png)

> 🔼 그림 9는 SFT Diffusion-Sharpening 기법을 사용하여 생성된 이미지들의 추가적인 정성적 결과를 보여줍니다. 그림에는 다양한 스타일과 주제의 이미지들이 포함되어 있으며, SFT Diffusion-Sharpening이 다양한 시각적 요소들을 잘 표현하고 세부 묘사에도 뛰어난 성능을 보임을 보여줍니다. 각 이미지는 서로 다른 시각적 특징들을 보여주며,  SFT Diffusion-Sharpening의 다양한 생성 능력을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: More Qualitative Results for SFT Diffusion-Sharpening.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Number of Steps | CLIP Score | ImageReward | MLLM |
|---|---|---|---|
| 1 | 0.334 | 1.352 | 0.864 |
| 2 | 0.336 | 1.355 | 0.891 |
| **3** | **0.338** | 1.445 | **0.921** |
| 4 | 0.336 | **1.446** | 0.911 |
| 8 | 0.337 | 1.444 | 0.919 |{{< /table-caption >}}
> 🔼 본 표는 Diffusion Sharpening 모델 학습에서 사용된 샘플 수(n)에 따른 성능 변화를 보여줍니다.  표에는 샘플 수(Number of Samples)가 1부터 8까지 증가함에 따라 CLIP Score, ImageReward, MLLM 세 가지 평가 지표의 값이 어떻게 변하는지 나타나 있습니다.  각 샘플 수에 대한 세 가지 지표 값을 비교하여 최적의 샘플 수를 결정하는 데 활용됩니다.  각 지표는 이미지 생성 품질의 다양한 측면을 평가하며, CLIP Score는 이미지와 텍스트 간의 정합성, ImageReward는 심미적 품질 및 사용자 선호도, MLLM은 다차원적 품질 평가를 반영합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Performance of Different Number of Samples in Training
> </details>

{{< table-caption >}}
| Number of Steps | CLIP Score | ImageReward | MLLM |
|---|---|---|---|
| 1 | 0.322 | 1.321 | 0.897 |
| 2 | 0.328 | 1.357 | 0.902 |
| **3** | **0.338** | **1.445** | 0.921 |
| 4 | 0.334 | 1.442 | **0.923** |
| 8 | 0.321 | 1.376 | 0.912 |{{< /table-caption >}}
> 🔼 표 3은 학습 중 단계 수의 영향을 분석한 결과를 보여줍니다. 표에는 단계 수(1, 2, 3, 4, 8)에 따른 CLIP 점수, 이미지 보상, MLLM의 성능 변화가 나와 있습니다.  단계 수가 증가함에 따라 모델 성능이 향상되는 것을 확인할 수 있습니다. 즉, 더 많은 단계를 거치면서  샘플링 과정을 더욱 세밀하게 최적화하여 성능 개선에 도움이 됨을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Performance of Different Number of Steps in Training
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