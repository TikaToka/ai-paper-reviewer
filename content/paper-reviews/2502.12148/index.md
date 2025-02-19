---
title: "HermesFlow: Seamlessly Closing the Gap in Multimodal Understanding and Generation"
summary: "HermesFlow: 다중모드 이해 및 생성 간 격차 해소를 위한 새로운 프레임워크!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Vision-Language Models", "🏢 Peking University",]
showSummary: true
date: 2025-02-17
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.12148 {{< /keyword >}}
{{< keyword icon="writer" >}} Ling Yang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-18 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.12148" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.12148" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/hermesflow-seamlessly-closing-the-gap-in" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

다중 모드 대규모 언어 모델(MLLM)은 이미지 이해 및 생성 작업 모두에 사용되지만, 기존 모델들은 이해 능력은 뛰어나지만 생성 능력은 상대적으로 부족한 문제점을 가지고 있습니다. 이러한 **이해와 생성 능력 간의 격차**는 MLLM의 성능 향상에 큰 걸림돌이 되고 있습니다.

본 논문에서는 이러한 문제를 해결하기 위해 **HermesFlow**라는 새로운 프레임워크를 제안합니다. HermesFlow는 **동종 데이터를 활용하여 이해 및 생성 선호도 데이터를 생성**하고, **Pair-DPO 및 자기 향상 반복 최적화**를 통해 MLLM의 이해 및 생성 능력을 동시에 향상시킵니다. 실험 결과, HermesFlow는 기존 MLLM보다 **이해 및 생성 능력 모두에서 뛰어난 성능**을 보였으며, 특히 이해 및 생성 능력 간의 격차를 크게 줄이는 데 성공했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 다중 모드 대규모 언어 모델(MLLM)의 이해 능력이 생성 능력보다 뛰어나다는 것을 발견했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 동종 데이터를 활용한 Pair-DPO를 통해 MLLM의 이해와 생성 능력 간의 격차를 줄였습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 자기 향상 반복 최적화를 통해 MLLM의 이해와 생성 능력을 동시에 향상시켰습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **다중 모드 대규모 언어 모델(MLLM)의 이해 및 생성 능력 간의 격차를 해소하는 새로운 방법론**을 제시하여, 차세대 다중 모드 기반 모델 개발에 중요한 발전을 가져올 수 있습니다. 특히, **동종 데이터를 활용한 Pair-DPO**라는 새로운 프레임워크를 제시하여, MLLM의 이해와 생성 능력 간의 균형을 이루는 데 기여했습니다. 이러한 연구는 **다양한 다중 모드 작업에서 MLLM의 성능을 향상시키는 데 중요한 시사점**을 제공하며, 향후 연구를 위한 새로운 방향을 제시합니다.  기존의 연구들이 데이터 수준에서의 개선에 집중한 것과 달리, 본 논문은 **이해와 생성 능력 간의 격차 자체를 해소하는 데 초점**을 맞추고 있어, MLLM 연구에 새로운 패러다임을 제시합니다.

------
#### Visual Insights





{{< table-caption >}}
| Model | # Params | POPE↑ | MME↑ | Flickr30k↑ | VQAv2_(test)↑ | GQA↑ | MMMU↑ |
|---|---|---|---|---|---|---|---| 
| Gemini-Nano-1 (Team et al., 2023) | 1.8B | - | - | - | 62.7 | - | 26.3 |
| CoDI (Tang et al., 2024) | - | - | - | 12.8 | - | - | - |
| Emu (Sun et al., 2024c) | 13B | - | - | 77.4 | 57.2 | - | - |
| NExT-GPT (Wu et al., 2023) | 13B | - | - | 84.5 | 66.7 | - | - |
| SEED-X (Ge et al., 2024) | 17B | 84.2 | 1435.7 | 52.3 | - | 47.9 | 35.6 |
| DreamLLM (Dong et al., 2023) | 7B | - | - | - | 72.9 | - | - |
| Chameleon (Team, 2024) | 34B | - | - | 74.7 | 66.0 | - | - |
| Show-o (Xie et al., 2024a) | 1.3B | 80.0 | 1232.9 | 67.6 | 74.7 | 61.0 | 27.4 |
| **HermesFlow (Ours)** | **1.3B** | **81.4** | **1249.7** | **69.2** | **75.3** | **61.7** | **28.3** |{{< /table-caption >}}

> 🔼 표 1은 다양한 다중 모드 이해 벤치마크에 대한 평가 결과를 보여줍니다.  Show-o (Xie et al., 2024a) 논문의 결과를 기준선으로 사용하여 여러 모델들의 성능을 비교 분석합니다.  #Params 열은 모델의 매개변수 수를 나타내고, 나머지 열들은 각 벤치마크(POPE, MME, Flickr30k, VQAV2(test), GQA, MMMU)에서의 성능 점수를 나타냅니다.  점수가 높을수록 성능이 우수함을 의미합니다. 이 표는 제시된 다양한 다중모드 언어모델들의 이해 능력을 정량적으로 비교하여 HermesFlow 모델의 성능을 보다 명확하게 파악하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Evaluation on multimodal understanding benchmarks. The baseline data is quoted from Show-o (Xie et al., 2024a).
> </details>





### In-depth insights


#### Multimodal Gap
본 논문에서 다루는 "멀티모달 갭(Multimodal Gap)"은 멀티모달 대규모 언어 모델(Multimodal Large Language Model, MLLM)의 **이해 능력과 생성 능력 간의 성능 차이**를 의미합니다.  흥미롭게도, 연구 결과는 MLLM의 이해 능력이 생성 능력보다 훨씬 뛰어나다는 것을 보여줍니다. 이러한 **성능 불균형**은 모델의 아키텍처나 학습 데이터의 편향 등 여러 요인에 기인할 수 있으며,  **모델의 전체적인 성능 향상을 저해**하는 주요한 문제점으로 제기됩니다.  따라서 이 갭을 해소하기 위한 다양한 방법들이 제시되고 있으며, **데이터 균형**을 맞추거나 **모델의 아키텍처를 개선**하는 등의 접근 방식이 논의됩니다.  **HermesFlow**와 같은 새로운 프레임워크는 이러한 갭을 메우는 데 초점을 맞추고 있으며,  **이해와 생성 작업 간의 연관성**을 강화함으로써 모델의 전반적인 성능을 향상시키는 것을 목표로 합니다.  결론적으로, "멀티모달 갭"은 MLLM 연구의 중요한 과제이며, 향후 연구에서 이를 해결하기 위한 효과적인 전략을 개발하는 것이 중요합니다.  **균형있는 성능** 향상을 위해서는 단순히 이해 능력 또는 생성 능력 중 하나만 향상시키는 것이 아니라, 두 능력 간의 균형있는 발전이 필요하며, HermesFlow는 그러한 균형을 이루기 위한 시도로 볼 수 있습니다.

#### Pair-DPO Training
본 논문에서 제시된 Pair-DPO (Pairwise Direct Preference Optimization) 기법은 **다중 모드 이해와 생성 간의 간극을 메우는 핵심 전략**입니다.  기존 DPO 방식이 단일 모드(이해 또는 생성)에만 초점을 맞춘 것과 달리, Pair-DPO는 **이해 및 생성에 대한 상호 관련된 선호도 데이터를 활용**하여 동시에 두 가지 능력을 향상시킵니다.  **상동 데이터(homologous data)에서 추출된 선호도 정보**를 통해, 모델은 이해와 생성 과정에서의 균형을 이루고, 상호 보완적인 학습을 수행합니다. 이는 단순히 데이터 양을 늘리는 것보다 **효율적이고 효과적인 성능 향상**을 가져옵니다.  **자기 반복 최적화(self-play iterative optimization)**와 결합하여, Pair-DPO는 모델의 이해 및 생성 능력을 반복적으로 개선하며, 외부 고품질 데이터에 의존하지 않고도 지속적인 성능 향상을 가능하게 합니다. 따라서 Pair-DPO Training은 **다중 모드 기반 모델의 성능 향상에 대한 새로운 패러다임**을 제시한다고 볼 수 있습니다.

#### Iterative Refinement
반복적 개선(Iterative Refinement)은 **다양한 머신러닝 모델의 성능을 향상시키는 핵심 전략**입니다. 특히, 생성 모델이나 다중 모달 모델과 같이 복잡하고, 상호작용이 많은 모델의 경우, 초기 결과물을 반복적으로 수정하고 개선함으로써 최종 성능을 크게 높일 수 있습니다. 이 과정에서 **데이터의 질적 향상**, **모델 파라미터의 미세 조정**, 그리고 **알고리즘 자체의 개선**과 같은 다양한 요소들이 고려될 수 있습니다.  **HermesFlow와 같은 프레임워크**는 이러한 반복적 개선 과정을 효율적으로 구현하는 데 도움을 줍니다.  **Pair-DPO(Pair Direct Preference Optimization)와 같은 알고리즘**을 통해, 모델의 이해 능력과 생성 능력 간의 불균형을 해소하고, 상호 보완적인 발전을 이끌어낼 수 있습니다.  **자기-플레이(Self-Play) 방식**은 모델 스스로 학습 데이터를 생성하고, 이를 통해 반복적인 개선을 가능하게 합니다.  **결론적으로, 반복적 개선은 모델 성능 향상에 매우 효과적이며, 특히 다중 모달 모델의 성능 한계를 극복하는 데 중요한 역할**을 합니다.  하지만, 반복 횟수나 데이터 품질 관리 등의 **세부적인 요소들도 신중하게 고려**되어야 합니다.

#### Homologous Data
본 논문에서 제시된 '상동 데이터(Homologous Data)' 개념은 **다중 모드 이해 및 생성 성능 간의 격차 해소**라는 핵심 목표를 달성하기 위한 핵심 전략입니다.  **이미지와 캡션 또는 프롬프트의 쌍**으로 구성된 상동 데이터는 이해와 생성 과정에 모두 사용되어 두 과정 간의 일관성을 확보합니다.  **이해를 위한 상동 데이터**는 동일한 이미지에 대한 여러 캡션을 생성하고 BERT 유사도를 기반으로 선별하여 만들어집니다. **생성을 위한 상동 데이터**는 동일한 프롬프트에 대한 여러 이미지를 생성하고 GPT-4 기반 자체 평가를 통해 선별합니다. 이러한 방식으로 생성된 상동 데이터는 **Pair-DPO(Pairwise Direct Preference Optimization)** 알고리즘에 사용되어 이해와 생성 성능을 동시에 개선하고, 그 격차를 줄이는데 기여합니다. **자기-플레이 반복 최적화**를 통해 이 과정은 여러 번 반복되며, **모델의 이해 및 생성 능력을 자체적으로 향상**시키는 효과를 보입니다.  즉, 상동 데이터는 단순히 데이터의 양적 증가가 아닌, **질적 개선**을 통해 다중 모드 모델의 성능을 균형 있게 향상시키는 역할을 수행하는 핵심 요소입니다.

#### Future Extensions
미래 확장에 대한 심도있는 논의는 본 논문의 핵심 주제인 **다중 모드 이해와 생성 간의 격차 해소**라는 맥락에서 이루어져야 합니다.  향후 연구는 **다양한 다중 모드 데이터셋**을 활용하여 HermesFlow의 일반화 성능을 평가하고, **더욱 복잡한 다중 모드 작업** (예: 장면 이해, 비디오 생성)으로 확장하는 데 초점을 맞춰야 합니다.  또한, **Pair-DPO의 효율성을 개선**하기 위한 알고리즘 최적화 연구와, **자체 학습 반복 최적화의 수렴 속도 개선**을 위한 연구가 필요합니다.  **다른 유형의 다중 모드 모델** (예: 확산 모델)과의 비교 연구를 통해 HermesFlow의 강점과 한계를 명확히 밝히고, **실제 응용 사례** (예: 이미지 편집, 지능형 에이전트) 개발을 위한 연구도 중요합니다.  궁극적으로는, HermesFlow가 **차세대 다중 모드 기반 모델**을 위한 일반적인 프레임워크로 자리매김할 수 있도록 연구를 지속해야 합니다.


### More visual insights




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Methods | #params | Single Obj. | Two Obj. | Counting | Colors | Position | Color Attri. | Overall | Average |
|---|---|---|---|---|---|---|---|---|---| 
| **Diffusion Model** |  |  |  |  |  |  |  |  |  |
| LDM (Rombach et al., 2022) | 1.4B | 0.92 | 0.29 | 0.23 | 0.70 | 0.02 | 0.05 | 0.37 | - |
| DALL-E 2 (Ramesh et al., 2022) | 4.2B | 0.94 | 0.66 | 0.49 | 0.77 | 0.10 | 0.19 | 0.52 | - |
| SD 1.5 (Rombach et al., 2022) | 860M | 0.94 | 0.37 | 0.27 | 0.72 | 0.05 | 0.07 | 0.40 | 63.18 |
| SD 2.1 (Rombach et al., 2022) | 865M | 0.97 | 0.50 | 0.46 | 0.80 | 0.07 | 0.14 | 0.49 | 68.09 |
| **Autoregressive Model** |  |  |  |  |  |  |  |  |  |
| LlamaGen (Sun et al., 2024b) | 775M | 0.87 | 0.25 | 0.23 | 0.51 | 0.06 | 0.04 | 0.32 | 65.16 |
| Emu (Sun et al., 2024c) | 14B | 0.87 | 0.34 | 0.26 | 0.56 | 0.07 | 0.06 | 0.36 | - |
| Chameleon (Team, 2024) | 34B | 0.89 | 0.39 | 0.28 | 0.66 | 0.08 | 0.07 | 0.40 | - |
| LWM (Liu et al., 2024b) | 7B | 0.93 | 0.41 | 0.46 | 0.79 | 0.09 | 0.15 | 0.47 | - |
| SEED-X (Ge et al., 2024) | 17B | 0.97 | 0.58 | 0.26 | 0.80 | 0.19 | 0.14 | 0.49 | - |
| Show-o (Xie et al., 2024a) | 1.3B | 0.95 | 0.52 | 0.49 | 0.82 | 0.11 | 0.28 | 0.53 | 67.48 |
| Janus (Wu et al., 2024a) | 1.3B | 0.97 | 0.68 | 0.30 | **0.84** | **0.46** | 0.42 | 0.61 | - |
| **HermesFlow (Ours)** | 1.3B | **0.98** | **0.84** | **0.66** | 0.82 | 0.32 | **0.52** | **0.69** | **70.22** |{{< /table-caption >}}
> 🔼 표 2는 GenEval (Ghosh et al., 2024) 및 DPG-Bench (Hu et al., 2024)라는 두 가지 시각적 생성 벤치마크에 대한 모델 성능 평가 결과를 보여줍니다.  각 벤치마크는 시각적 생성 능력의 여러 측면(예: 개체 수 세기, 색상, 위치 등)을 평가하는 여러 하위 벤치마크로 구성됩니다. 표는 제안된 HermesFlow 모델을 포함한 다양한 최첨단 모델의 성능을 비교하여, 각 모델이 각 하위 벤치마크에서 얼마나 잘 수행했는지 보여줍니다. 이를 통해 HermesFlow 모델의 시각적 생성 능력을 종합적으로 평가하고 다른 모델들과 비교 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Evaluation on visual generation benchmarks: GenEval (Ghosh et al., 2024) and DPG-Bench (Hu et al., 2024).
> </details>

{{< table-caption >}}
| Method | # Params | FID↓ | CLIP-Score↑ |
|---|---|---|---| 
| LDM (Rombach et al., 2022) | 1.4B | 12.64 | - |
| DALL·E 2 (Ramesh et al., 2022) | 6.5B | 10.39 | - |
| SD 1.5 (Rombach et al., 2022) | 860M | 9.62 | 30.23 |
| SD 2.1 (Rombach et al., 2022) | 865M | 8.03 | 30.87 |
| LlamaGen (Sun et al., 2024b) | 775M | 9.45 | 29.12 |
| Emu (Sun et al., 2024c) | 14B | 11.02 | 28.98 |
| LWM (Liu et al., 2024b) | 7B | 12.68 | - |
| SEED-X (Ge et al., 2024) | 17B | 14.99 | - |
| Show-o (Xie et al., 2024a) | 1.3B | 9.24 | 30.63 |
| **HermesFlow (Ours)** | **1.3B** | **9.07** | **31.08** |{{< /table-caption >}}
> 🔼 표 3은 MSCOCO 데이터셋을 사용하여 제로샷 설정에서 평가된 HermesFlow 모델의 FID(Fréchet Inception Distance) 점수와 CLIP(Contrastive Language–Image Pre-training) 점수를 보여줍니다. FID 점수는 생성된 이미지의 품질을, CLIP 점수는 생성된 이미지와 텍스트 프롬프트 사이의 일관성을 측정합니다.  낮은 FID 점수와 높은 CLIP 점수는 더 나은 성능을 나타냅니다. 이 표는 HermesFlow 모델의 이미지 생성 능력을 다른 모델들과 비교하여 보여주는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 3: MSCOCO zero-shot FID and CLIP-Score.
> </details>

{{< table-caption >}}
| Method | # Params | Understanding Score ↑ | Generation Score ↑ | Gap ↓ |
|---|---|---|---|---|
| VILA-U (Wu et al., 2024c) (Xie et al., 2024a) | 7B | 0.646 | 0.477 | 0.169 |
| Janus (Wu et al., 2024a) | 1.3B | 0.599 | 0.417 | 0.182 |
| Show-o (Xie et al., 2024a) | 1.3B | 0.520 | 0.433 | 0.087 |
| HermesFlow (Ours) | 1.3B | 0.533 | 0.497 | 0.036 |{{< /table-caption >}}
> 🔼 표 4는 다양한 다중 모드 대규모 언어 모델(MLLM)의 이해 및 생성 능력 간의 차이를 정량적으로 평가한 결과를 보여줍니다.  각 모델에 대해, 이미지 이해 점수와 이미지 생성 점수를 제시하고, 두 점수의 차이를 계산하여 모델의 이해와 생성 능력 간격을 보여줍니다. 이는 MLLM의 이해 능력이 생성 능력보다 일반적으로 뛰어나다는 것을 보여주는 중요한 실험 결과입니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Quantitative assess of MLLM’s Understanding and Generation Gap.
> </details>

{{< table-caption >}}
| Methods |  | Understanding Bench |  | Generation Bench | 
|---|---|---|---|---|---| 
|  | Show-o (Xie et al., 2024a) | 80.0 | 1232.9 | 27.4 | 0.53 | 67.48 |
|  | DPO (Understanding) | 80.8 | 1242.2 | 27.8 | 0.58 | 67.88 |
|  | DPO (Generation) | 80.5 | 1239.3 | 27.5 | 0.70 | 70.03 |
|  | Pair-DPO (Iter. 0) (Show-o) | 80.0 | 1232.9 | 27.4 | 0.53 | 67.48 |
|  | Pair-DPO (Iter. 1) | 81.1 | 1246.7 | 28.0 | 0.68 | 70.19 |
|  | Pair-DPO (Iter. 2) | 81.3 | 1248.3 | 28.1 | 0.69 | 70.21 |
|  | Pair-DPO (Iter. 3) | **81.4** | **1249.7** | **28.3** | **0.69** | **70.22** |{{< /table-caption >}}
> 🔼 표 5는 Pair-DPO와 DPO의 성능 비교 및 Pair-DPO 반복 횟수의 영향을 보여줍니다.  Pair-DPO는 이해와 생성 두 가지 모두에 대한 성능 향상을 보이며, 특히 단일 모드(이해 또는 생성) DPO보다 우수한 결과를 보입니다.  반복 횟수가 증가할수록 성능이 향상되지만, 특정 시점 이후에는 성능 향상이 미미해짐을 알 수 있습니다.  표에는 이해(POPE, MME, MMMU) 및 생성(GenEval, DPG-Bench) 작업에 대한 다양한 지표가 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Comparison of Pair-DPO vs. DPO and the Effect of Pair-DPO Iterations.
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