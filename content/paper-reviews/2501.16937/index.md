---
title: "TAID: Temporally Adaptive Interpolated Distillation for Efficient Knowledge Transfer in Language Models"
summary: "TAID: 시간에 따라 적응적으로 변화하는 중간 분포를 통해 대규모 언어 모델의 지식을 소규모 모델에 효율적으로 전달하는 새로운 지식 증류 기법"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Sakana AI",]
showSummary: true
date: 2025-01-28
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.16937 {{< /keyword >}}
{{< keyword icon="writer" >}} Makoto Shing et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-29 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.16937" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.16937" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/taid-temporally-adaptive-interpolated" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)은 강력하지만 크기가 커서 배포가 어렵습니다. 지식 증류(KD)는 큰 모델의 지식을 작은 모델에 전달하여 이 문제를 해결하는 유망한 방법입니다. 하지만 기존 KD 기법은 교사 모델과 학생 모델 간의 차이(용량 차이, 모드 평균화, 모드 붕괴)로 인해 성능이 저하되는 문제가 있습니다. 

본 논문에서는 이러한 문제를 해결하기 위해 TAID(시간 적응형 보간 증류)라는 새로운 KD 기법을 제안합니다. TAID는 시간에 따라 변화하는 중간 분포를 사용하여 학생 모델의 분포를 점진적으로 교사 모델의 분포에 가깝게 만들어 용량 차이를 줄이고 모드 평균화/붕괴 문제를 방지합니다.  다양한 실험 결과를 통해 TAID가 다양한 모델 크기와 아키텍처에서 기존 기법보다 우수한 성능을 보임을 확인했습니다. 또한, TAID를 사용하여 개발한 두 개의 경량화된 기초 모델(TAID-LLM-1.5B, TAID-VLM-2B)이 각 분야에서 최첨단 성능을 달성했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} TAID는 시간에 따라 변화하는 중간 분포를 사용하여 대규모 언어 모델의 지식을 소규모 모델에 효율적으로 전달합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} TAID는 기존 방법들보다 다양한 모델 크기와 아키텍처에서 우수한 성능을 보이며, 모델 크기 차이 및 모드 평균화/붕괴 문제를 효과적으로 해결합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} TAID를 사용하여 개발된 TAID-LLM-1.5B 및 TAID-VLM-2B는 각각 2B 파라미터 미만의 언어 모델과 4B 파라미터 이하의 비전-언어 모델에서 최첨단 성능을 달성했습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대규모 언어 모델의 효율적인 지식 전달을 위한 새로운 방법론인 TAID를 제시**함으로써, 연구자들이 **더 작고 효율적인 언어 모델을 개발**하는 데 도움을 줍니다.  이는 자원 제약 환경에서의 AI 기술 접근성 향상에 기여하며, **모델 압축 및 지식 전이 분야의 연구 발전**에 중요한 의미를 지닙니다.  또한, 본 연구는 **다양한 모델 크기와 아키텍처에서의 실험 결과**를 제시하여 TAID의 우수성을 입증하고, **미래 연구를 위한 새로운 방향**을 제시합니다. 

------
#### Visual Insights



![](https://arxiv.org/html/2501.16937/x1.png)

> 🔼 그림 1은 표준 지식 증류(KD)와 TAID의 비교를 보여줍니다. 왼쪽은 기존의 표준 KD 방법이 고정된 teacher 분포를 향해 직접적으로 학습하는 과정을 나타냅니다. 반면 오른쪽 그림은 TAID가 시간에 따라 변화하는 중간 teacher 분포(녹색 점선)를 통해 동적으로 연결 다리를 만드는 방법을 보여줍니다. 이를 통해 학습 초기 단계의 student 분포에서 점진적으로 teacher 분포로 이동하는 유연한 전이가 가능해집니다.  TAID는 이러한 접근 방식을 통해 용량 차이를 효과적으로 해결하고 다양한 크기의 모델에서 지식 전달의 균형을 맞출 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Comparison of standard KD and TAID. (Left) Standard KD methods typically employ direct optimization towards a fixed teacher distribution. (Right) TAID creates a dynamic bridge through adaptive, time-dependent intermediate teacher distributions (green dashed lines), enabling gradual optimization of the student. This approach facilitates a flexible transition from the student’s initial distribution towards the teacher’s distribution over time, effectively addressing the capacity gap and balancing knowledge transfer across varying model sizes.
> </details>





{{< table-caption >}}
| Teacher | Phi-3-mini (3.8B) | Llama-2 (6.7B) | StableLM Zephyr (2.8B) |
|---|---|---|---| 
| **Method** | **Student** | TinyLlama (1.1B) | TinyLlama (1.1B) | Pythia (0.4B) |
|---|---|---|---| 
| SFT |  | 2.00 | 3.94 | 2.57 |
| KL [Hinton et al., 2015] |  | 2.71 | 3.99 | 2.74 |
| RKL [Wen et al., 2023; Gu et al., 2024] |  | 3.48 | 3.92 | 2.53 |
| TVD [Wen et al., 2023] |  | 3.27 | 3.64 | 2.57 |
| Adaptive KL [Wu et al., 2024] |  | 3.27 | 3.77 | 2.64 |
| GKD [Agarwal et al., 2024] |  | 2.24 | 3.82 | 2.59 |
| DistiLLM [Ko et al., 2024] |  | 3.23 | 3.97 | 2.97 |
| CTKD [Li et al., 2023b] |  | 1.78 | 2.84 | 1.39 |
| DKD [Zhao et al., 2022] |  | 2.70 | 4.14 | 2.90 |
| (Ours) TAID w/o adaptive update |  | 3.44 | 4.18 | 2.88 |
| (Ours) TAID |  | 4.05 | 4.27 | 3.05 |{{< /table-caption >}}

> 🔼 표 1은 LLM의 지시 조정을 위한 다양한 증류 방법을 평가한 결과를 보여줍니다. 훈련 후 MT-Bench 점수가 표시되며, 점수가 높을수록 더 나은 대화 능력을 나타냅니다. 세 가지 교사-학생 쌍 각각에 대해 제안된 TAID 방법을 포함한 여러 가지 증류 알고리즘을 비교합니다. 각 열의 최고 점수는 굵게 표시됩니다. 이 표는 다양한 모델 크기와 아키텍처에서 지시 조정과 사전 훈련 시나리오 모두에서 TAID의 우수한 성능을 보여주는 실험 결과의 일부입니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Evaluating distillation methods for LLM instruction tuning. The MT-Bench scores after training are listed, where higher scores indicate better conversational performance. For each of the three teacher-student pairs, different distillation algorithms, including the proposed TAID method, are compared. The highest score in each column is highlighted in bold.
> </details>





### In-depth insights


#### TAID: Adaptive KD
**TAID (Temporally Adaptive Interpolated Distillation)**는 기존 지식 증류(KD) 방식의 한계를 극복하기 위해 제안된 새로운 방법입니다.  기존 KD는 큰 teacher 모델과 작은 student 모델 간의 차이로 인해 mode collapse나 mode averaging 문제가 발생했지만, TAID는 **시간에 따라 teacher와 student 분포를 보간하는 중간 분포**를 사용하여 이 문제를 해결합니다. 이 중간 분포는 학습 초기에는 student 분포에 가깝게 시작하여 점진적으로 teacher 분포에 가까워지도록 설계되어, **모델의 용량 차이를 완화**하고 **부드러운 지식 전달**을 가능하게 합니다. **적응적 보간 파라미터 업데이트 메커니즘**을 통해 학습 과정을 효율적으로 제어하며, 이론적 분석을 통해 mode collapse를 방지하는 효과를 입증합니다.  실험 결과는 다양한 모델 크기와 구조에서 TAID의 우수한 성능을 보여주며,  **새로운 경량 기반 모델 개발**에 대한 실용적인 영향을 제시합니다.

#### Capacity Gap Issue
본 논문에서 논의되는 'Capacity Gap Issue'는 **큰 teacher 모델과 작은 student 모델 간의 용량 차이**로 인해 발생하는 지식 전이(knowledge transfer)의 어려움을 가리킵니다.  이는 teacher 모델의 풍부한 정보를 student 모델이 제대로 학습하지 못하고, 성능 향상에 제한이 생기는 현상으로 이어집니다.  **모델의 크기 차이가 클수록 이러한 문제는 더욱 심각해집니다.**  이 문제는 단순히 모델 크기의 차이뿐만 아니라, **teacher 모델의 복잡한 특징을 student 모델이 단순화하여 표현하는 과정에서 발생하는 mode averaging과 mode collapse**와도 밀접한 관련이 있습니다.  **TAID는 이러한 Capacity Gap Issue를 해결하기 위해, teacher와 student의 분포를 adaptive intermediate distribution을 통해 점진적으로 연결하는 방법을 제시합니다.** 이는 student 모델이 갑작스럽게 teacher 모델의 복잡한 분포를 따라가지 않고, **점진적인 학습을 통해 teacher의 지식을 효과적으로 흡수**하도록 돕습니다.  **TAID의 핵심은 시간에 따라 변화하는 중간 분포를 활용하여 capacity gap을 완화하고 mode averaging/collapse 문제를 동시에 해결**하는 것입니다.

#### Mode Collapse
모드 붕괴는 생성 모델, 특히 자연어 처리 분야에서 심각한 문제입니다. **모델이 다양한 출력을 생성하지 못하고 제한된 몇 가지 패턴만 반복하는 현상**을 말합니다. 이는 모델의 학습 데이터 분포를 제대로 학습하지 못하고 특정한 모드에 과도하게 집중하여 발생합니다. 본 논문에서 제시된 TAID 방법은 시간에 따라 적응적으로 중간 분포를 생성함으로써, **학습 초기에는 학생 모델의 고유 특징을 유지하면서 점진적으로 교사 모델의 분포에 가까워지도록** 합니다. 이러한 접근 방식은 모드 붕괴를 예방하고 다양한 출력을 생성하는 데 도움이 됩니다.  **TAID는 이론적 분석과 실험을 통해 모드 붕괴를 효과적으로 방지하고 성능 향상에 기여함**을 보여줍니다.  **모델 용량 차이 및 모드 평균화 문제도 함께 해결**하여, 효율적인 지식 전이를 위한 강력한 도구임을 시사합니다. 하지만 TAID가 모든 모드 붕괴 문제를 완벽히 해결하는 것은 아니며,  **학습 데이터의 질과 양, 모델 구조 등 다른 요인도 고려**해야 합니다.

#### TAID Experiments
본 논문에서 제시된 TAID(Temporally Adaptive Interpolated Distillation) 방법의 실험 결과는 다양한 크기와 구조의 언어 모델에서 우수한 성능을 보여줍니다. **특히, 기존의 지식 증류 방법들보다 성능 향상을 보이며, 특히 용량 차이가 큰 모델 간의 지식 전이에서 효과적임**을 보였습니다.  또한, 모드 평균화 및 모드 붕괴 문제를 효과적으로 해결하여 안정적인 학습을 가능하게 합니다.  **다양한 실험 설정에서 TAID의 우수성이 검증되었고, 특히, instruction tuning과 pre-training 시나리오 모두에서 뛰어난 성능**을 보여주는 두 개의 최첨단 모델 (TAID-LLM-1.5B, TAID-VLM-2B)을 개발했습니다.  **TAID는 모델 크기와 상관없이 일관되게 성능 향상**을 보여주는 강점을 가지고 있으며, 이는  대규모 언어 모델을 더욱 효율적이고 접근성 높은 기술로 발전시키는 데 기여할 것으로 기대됩니다.  **추가적으로, 이미지 분류 작업에서의 실험 결과를 통해, TAID가 다양한 작업에 적용 가능하며, 특히 복잡한 작업에서 더욱 효과적임**을 확인했습니다.  전반적으로, TAID 실험은 **제안된 방법의 효율성과 실용성을 명확하게 보여주는 긍정적인 결과**를 제시했습니다.

#### Future of TAID
TAID의 미래는 **대규모 언어 모델의 효율적인 지식 전이**에 대한 잠재력에 달려 있습니다.  **적응형 중간 분포**를 사용하여 학습 과정 전반에 걸쳐 교사와 학생 모델 간의 차이를 줄이는 TAID의 핵심 메커니즘은 다양한 모델 크기와 아키텍처에서 우수한 성능을 보여주었습니다.  향후 연구는 **다양한 거리 측정법**을 통합하고, **비선형 보간**을 탐구하고, **다중 교사 증류**로 확장하여 TAID의 강점을 더욱 발전시킬 수 있습니다.  특히, **다른 모달리티와 작업**으로의 확장은 TAID의 유연성과 실용성을 보여주며, 제한된 리소스 환경에서 고성능 모델을 개발하는 데 중요한 역할을 할 것입니다.  **실제 응용 프로그램**에서 TAID를 배포하고, 다양한 작업에 대한 효과를 평가하여 실용적인 영향을 더욱 강화하는 것도 중요합니다.  궁극적으로, TAID는 **더욱 접근 가능하고 효율적인 AI 기술** 개발을 위한 중요한 진전을 이룰 것입니다.


### More visual insights




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | ARC | HellaSwag | MMLU | TrustfulQA | Winogrande | GSM8K | Average |
|---|---|---|---|---|---|---|---| 
| SFT | 41.38 | 63.66 | 25.89 | 35.64 | 61.25 | 1.21 | 38.17 |
| KL (Hinton et al., 2015) | 44.97 | 65.43 | 25.11 | **37.95** | 63.22 | 2.80 | 39.91 |
| TVD (Wen et al., 2023) | 43.52 | 64.50 | 25.95 | 36.38 | 63.14 | 2.96 | 39.41 |
| Adaptive KL (Wu et al., 2024) | 43.77 | 63.09 | 26.04 | 36.42 | 63.22 | 2.12 | 39.11 |
| GJS (Agarwal et al., 2024) | 44.71 | **65.67** | 25.27 | 37.76 | 62.12 | 3.34 | 39.81 |
| Skew KL (Ko et al., 2024) | 44.62 | 65.25 | 25.79 | 37.45 | 62.51 | **3.41** | 39.84 |
| Skew RKL (Ko et al., 2024) | 44.11 | 64.80 | **26.07** | 36.76 | 62.83 | 3.03 | 39.60 |
| **(Ours) TAID** | **45.48** | 65.43 | 25.43 | 37.92 | **63.38** | 2.96 | **40.10** |{{< /table-caption >}}
> 🔼 표 2는 LLM의 지속적인 사전 훈련에 대한 다양한 증류 방법의 평가 결과를 보여줍니다. Open LLM 리더보드 점수를 사용하여 훈련 후 각 모델의 성능을 평가했습니다. 점수가 높을수록 성능이 우수함을 의미합니다. 표에는 6가지 과제에 대한 각 모델의 점수와 평균 점수가 나와 있으며, 각 열에서 가장 높은 점수는 굵게 표시되어 있습니다. 평균 점수는 일반적인 언어 능력의 지표로 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 2:  Evaluating distillation methods for LLM continued pre-training. The Open LLM Leaderboard scores after training are listed, with higher scores indicating better performance. The average score across the 6 tasks (Average column) is commonly used as an indicator of overall language proficiency. The highest score in each column is highlighted in bold.
> </details>

{{< table-caption >}}
| Method | Head | Tail |
|---|---|---|
| KL | 0.216 | 40.2 
× 10<sup>−7</sup> |
| RKL | 0.227 | 8.1 
× 10<sup>−7</sup> |
| TAID | 0.218 | 39.0 
× 10<sup>−7</sup> |{{< /table-caption >}}
> 🔼 표 3은 모델의 어휘 분포를 분석한 결과를 보여줍니다.  'Head'는 상위 10개 토큰의 확률 합계를, 'Tail'은 80-100번째 백분위수에 해당하는 토큰들의 확률 합계를 나타냅니다. 일반적으로 Head 토큰의 확률은 0.1에서 0.01 사이의 범위에 있으며, Tail 토큰의 확률은 0.0000000001에서 0.00000000001 사이입니다. 이 표는 TAID 방법이 어떻게  모드 평균화(mode averaging)와 모드 붕괴(mode collapse) 문제를 해결하는지 보여주는 주요 증거를 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Probability mass distribution analysis. Head: sum of probabilities for top-10 tokens. Tail: sum of probabilities for tokens in the 80–100th percentile.111Typically, probabilities range from 10−1superscript10110^{-1}10 start_POSTSUPERSCRIPT - 1 end_POSTSUPERSCRIPT to 10−2superscript10210^{-2}10 start_POSTSUPERSCRIPT - 2 end_POSTSUPERSCRIPT for Head tokens and from 10−10superscript101010^{-10}10 start_POSTSUPERSCRIPT - 10 end_POSTSUPERSCRIPT to 10−11superscript101110^{-11}10 start_POSTSUPERSCRIPT - 11 end_POSTSUPERSCRIPT for Tail tokens.
> </details>

{{< table-caption >}}
| Model | LightEval (↑) |
|---|---| 
| `Qwen2-1.5B` [Yang et al., 2024](https://arxiv.org/html/2501.16937v2#bib.bib56) | 46.19 |
| `Phi-1.5B` [Li et al., 2023a](https://arxiv.org/html/2501.16937v2#bib.bib29) | 50.39 |
| `StableLM-2-1.6B` [Bellagente et al., 2024](https://arxiv.org/html/2501.16937v2#bib.bib6) | 51.24 |
| `SmolLM-1.7B` [Allal et al., 2024](https://arxiv.org/html/2501.16937v2#bib.bib3) | 51.31 |
| **`TAID-LLM-1.5B`** | **52.27** |{{< /table-caption >}}
> 🔼 본 표는 서로 다른 크기의 교사 모델을 사용하여 TAID와 Skew KL의 성능을 비교한 결과를 보여줍니다. TAID는 교사 모델의 크기가 커짐에 따라 일관되게 성능이 향상되는 반면, Skew KL은 성능이 저하되는 것을 확인할 수 있습니다. 이는 TAID가 대용량 언어 모델을 효율적으로 압축하는 데 더 적합함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Performance comparison between TAID and Skew KL across different teacher sizes. TAID shows consistent improvement with larger teachers, while Skew KL’s performance degrades.
> </details>

{{< table-caption >}}
| Model | Open-VLM-LB (↑) | 
|---|---| 
| PaliGemma (Beyer et al., 2024) | 46.56 | 
| MiniCPM-V-2 (Yao et al., 2024) | 47.93 | 
| Phi-3-Vision (Abdin et al., 2024) | 53.60 | 
| InternVL2-2B (Chen et al., 2024) | 53.96 | 
| **TAID-VLM-2B** | **56.43** |{{< /table-caption >}}
> 🔼 표 7은 CIFAR-100 데이터셋에서 다양한 Teacher-Student 모델 조합에 대한 Top-1 정확도(%)를 보여줍니다.  각 Teacher 모델(ResNet56, ResNet110, ResNet32x4, WRN-40-2, WRN-40-1, VGG13)과 각 Student 모델(ResNet20, ResNet32, ResNet8x4, WRN-16-2, WRN-40-1, VGG8)의 조합에 따른 결과를 보여주어, 다양한 모델 크기와 구조에서의 지식 증류 효과를 비교 분석하는 데 유용한 정보를 제공합니다.  표에는 KL, CTKD, DKD, MLKD, TAID 등 다양한 지식 증류 방법의 성능이 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Top-1 accuracies (%) on the CIFAR-100 dataset. Results for different teacher-student pairs are shown.
> </details>

{{< table-caption >}}
| Method | 410M | 1B | 2.8B | 6.9B |
|---|---|---|---|---|
| TAID | 20.82 | 21.17 | 21.70 | 22.01 |
| SKL | 18.65 | 18.50 | 18.28 | 18.20 |{{< /table-caption >}}
> 🔼 이 표는 ImageNet 검증 세트에서 다양한 teacher-student 모델 쌍에 대한 Top-1 정확도를 보여줍니다.  다양한 teacher 모델(ResNet34, ResNet50)과 student 모델(ResNet18, MobileNet-V1) 조합에 따른 성능을 비교하여 TAID 방법의 효과를 보여줍니다.  각 셀의 값은 해당 teacher-student 조합에 대한 Top-1 정확도 백분율을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Top-1 accuracies (%) on the ImageNet validation set. Results for different teacher-student pairs are shown.
> </details>

{{< table-caption >}}
| Teacher | ResNet56 | ResNet110 | ResNet32x4 | WRN-40-2 | WRN-40-2 | VGG13 |
|---|---|---|---|---|---|---|
| **Method** | **Student** | ResNet20 | ResNet32 | ResNet8x4 | WRN-16-2 | WRN-40-1 | VGG8 |
| KL (Hinton et al., 2015) |  | 70.66 | 73.08 | 73.33 | 74.92 | 73.54 | 72.93 |
| CTKD (Li et al., 2023b) |  | 71.19 | 73.52 | 73.39 | 75.45 | 73.93 | 73.52 |
| DKD (Zhao et al., 2022) |  | 71.97 | 74.11 | 76.32 | 76.24 | 74.81 | 74.68 |
| MLKD (Jin et al., 2023) |  | 72.19 | **74.11** | **77.08** | **76.63** | **75.35** | **75.18** |
| (Ours) TAID |  | **72.25** | 73.51 | 74.85 | 75.81 | 74.51 | 74.38 |{{< /table-caption >}}
> 🔼 표 9는 2B 미만 매개변수를 가진 모델에 대해 TAID 기반으로 개발된 최첨단 LLM인 TAID-LLM-1.5B의 성능을 보여줍니다.  표에는 다양한 언어 모델 평가 벤치마크 작업에서 TAID-LLM-1.5B와 기존 최고 성능 모델들의 점수가 비교되어 있습니다.  각 작업에 대한 성능을 정량적으로 비교하여 TAID-LLM-1.5B의 우수성을 보여줍니다. 이를 통해 TAID 방법이 소규모 언어 모델에서도 우수한 성능을 달성하는 데 효과적임을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Performance of TAID-LLM-1.5B, our new state-of-the-art LLM for models under 2B parameters.
> </details>

{{< table-caption >}}
| Teacher | ResNet34 | ResNet50 |
|---|---|---| 
| **Method** | **Student** | ResNet18 | MN-V1 |
| KD (Hinton et al., 2015) |  | 71.03 | 70.50 |
| CTKD (Li et al., 2023b) |  | 71.38 | 71.16 |
| DKD (Zhao et al., 2022) |  | 71.70 | 72.05 |
| MLKD (Jin et al., 2023) |  | 71.90 | **73.01** |
| **(Ours) TAID** |  | **72.10** | 72.71 |{{< /table-caption >}}
> 🔼 표 10은 TAID 기법을 사용하여 개발한 최첨단 비전-언어 모델인 TAID-VLM-2B의 성능을 보여줍니다.  TAID-VLM-2B는 40억 개의 매개변수를 가진 모델 중 최고 성능을 보이며, 다양한 비전-언어 작업에서 경쟁력 있는 결과를 제공합니다. 표에는 MMBench_V11, MMStar, MMMU_VAL, MathVista, OCRBench, AI2D, HallusionBench, MMVet과 같은 여러 벤치마크 작업에 대한 점수가 나와있고 평균 점수도 함께 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Performance of TAID-VLM-2B, our new state-of-the-art VLM for models up to 4B parameters.
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