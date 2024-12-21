---
title: "AceMath: Advancing Frontier Math Reasoning with Post-Training and Reward Modeling"
summary: "AceMath는 사전 훈련 및 보상 모델링을 통해 최첨단 수학 추론 능력을 달성한 프런티어급 모델 시리즈입니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 NVIDIA Research",]
showSummary: true
date: 2024-12-19
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.15084 {{< /keyword >}}
{{< keyword icon="writer" >}} Zihan Liu et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-20 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.15084" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.15084" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/acemath-advancing-frontier-math-reasoning" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

최근 **대규모 언어 모델(LLM)**의 수학적 추론 능력 향상에 대한 관심이 높아지고 있지만, 여전히 복잡한 수학 문제 해결에 어려움을 겪고 있습니다. 기존 연구들은 주로 **지도 학습 방식**에 의존하거나 **보상 모델**의 성능이 제한적이었습니다. 이러한 문제를 해결하기 위해 본 연구에서는 **AceMath**라는 새로운 프런티어급 수학 모델을 제시합니다.



AceMath는 **사전 훈련 및 보상 모델링**을 결합한 새로운 접근 방식을 통해 개발되었습니다. **다양한 수학 문제 풀이 경험**을 바탕으로 **일반적인 영역에서의 성능**을 우선 확보하고, 이후 **수학 전용 데이터**를 이용하여 **미세 조정**을 수행했습니다. 또한, **새로운 수학 보상 모델 평가 기준**인 **AceMath-RewardBench**를 구축하고, 이를 바탕으로 **최고 성능의 보상 모델**을 개발했습니다. 이를 통해 **다양한 수학 추론 벤치마크**에서 **최고 성능**을 달성하여 기존 연구의 한계를 극복하고 새로운 연구의 토대를 마련하였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} AceMath 모델은 기존 최고 성능 모델들을 능가하는 수학 추론 성능을 보여줍니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} AceMath는 새로운 수학 보상 모델 평가 기준 및 훈련 전략을 제시합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} AceMath 모델과 데이터는 공개되어 후속 연구를 위한 토대를 마련합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **수학 추론 분야의 최첨단 모델을 개발**하고, **새로운 평가 기준 및 훈련 전략**을 제시하여 **향후 연구 방향**을 제시하는 데 중요한 의미를 가집니다. **대규모 언어 모델(LLM)**의 수학적 추론 능력 향상에 대한 연구가 활발히 진행되는 가운데, 본 연구는 이 분야에서 **최고 성능**을 달성함으로써 **기존 연구의 한계**를 극복하고 **새로운 연구의 토대**를 마련합니다.  또한, 공개된 모델 및 데이터를 통해 **다른 연구자들의 후속 연구**를 촉진할 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.15084/x1.png)

> 🔼 그림 1은 AceMath 모델과 주요 오픈소스 및 독점 LLM을 수학 추론 벤치마크에서 비교한 결과를 보여줍니다. AceMath-72B-RM 보상 모델을 사용한 rm@8 정확도(8개 중 최고)를 추가로 보고하고, Qwen2.5-Math의 공식 보고된 수치를 사용했습니다.  표는 다양한 수학 벤치마크(GSM8K, MATH, Minerva Math, Gaokao 2023 English, Olympiad Bench, College Math, MMLU STEM)에서 각 모델의 성능을 비교하여 AceMath의 우수성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: AceMath versus leading open-weights and proprietary LLMs on math reasoning benchmarks. Additionally, we report rm@8 accuracy (best of 8) with our reward model AceMath-72B-RM and use the official reported numbers from Qwen2.5-Math.
> </details>





{{< table-caption >}}
| Models | HumanEval | MBPP | GSM8K | MATH | MMLU | MMLU Pro | Avg. |
|---|---|---|---|---|---|---|---|
| DeepSeek-Coder-7B-Instruct-v1.5 | 64.10 | 64.60 | 72.60 | 34.10 | 49.50 | - | - |
| DeepSeek-Coder-7B-Base + Two-Stage SFT (Ours) | 78.05 | 73.54 | 82.56 | 55.62 | 54.65 | 33.28 | 62.95 |
| Llama3.1-8B-Instruct | 72.60 | 69.60 | 84.50 | 51.90 | 69.40 | 48.30 | 66.05 |
| Llama3.1-8B-Base + Two-Stage SFT (Ours) | 81.10 | 74.71 | 90.45 | 64.42 | 68.31 | 43.27 | 70.38 |
| Qwen2.5-1.5B-Instruct | 61.60 | 63.20 | 73.20 | 55.20 | 58.37 | 32.40 | 57.33 |
| Qwen2.5-1.5B-Base + Two-Stage SFT (Ours) | 73.17 | 65.76 | 80.44 | 60.34 | 58.17 | 33.78 | 61.94 |
| Qwen2.5-7B-Instruct | 84.80 | 79.20 | 91.60 | 75.50 | 74.51 | 56.30 | 76.99 |
| Qwen2.5-7B-Base + Two-Stage SFT (Ours) | 85.37 | 74.32 | 93.10 | 76.40 | 74.68 | 54.50 | 76.40 |
| Qwen2.5-72B-Instruct | 86.60 | 88.20 | 95.80 | 83.10 | 84.67 | 71.10 | 84.91 |
| Qwen2.5-72B-Base + Two-Stage SFT (Ours) | 89.63 | 83.66 | 96.36 | 84.50 | 83.88 | 66.10 | 84.02 |{{< /table-caption >}}

> 🔼 표 1은 본 논문에서 제안하는 2단계 학습 전략을 다양한 기본 모델에 적용하여 수행한 지도 학습 미세 조정(SFT) 결과를 보여줍니다.  여러 기본 모델들에 대해 미세 조정된 모델들을 해당 기본 모델들과 동일한 기본 모델을 사용하여 만들어진 지시어 기반 기준 모델들과 비교 분석합니다. 즉,  제안된 2단계 SFT 전략의 효과를 다양한 규모의 모델들에서 평가한 결과를 보여주는 표입니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Results of our general SFT models. We apply our proposed two-stage training strategy to conduct SFT on various base models. These finetuned models are then compared against the corresponding instruct baselines that are built upon the same base models.
> </details>





### In-depth insights


#### SFT for Math Models
본 논문에서 제시된 수학 모델을 위한 SFT(Supervised Fine-Tuning)는 **일반 영역에 대한 튜닝과 수학 영역에 대한 집중 튜닝의 두 단계**로 구성됩니다. 먼저 일반 영역에서 다양한 문제(코딩, 일반 지식 등)에 대한 튜닝을 통해 기초를 다지고, 이후 **수학 관련 데이터셋을 사용하여 수학적 추론 능력을 향상**시키는 방식입니다.  **정제된 프롬프트와 합성 응답 데이터**를 사용하여 SFT를 수행하며, **기존 모델보다 우수한 성능**을 달성합니다.  특히, 대규모 모델일수록 SFT를 통해 얻는 성능 향상이 더욱 크다는 점이 주목할 만합니다.  **다양한 수학 벤치마크에서의 성능 평가**를 통해 이러한 SFT 전략의 유효성을 검증합니다.  이는 단순히 수학 문제 해결 능력 향상뿐 아니라, **다양한 분야에서의 지시사항 따르기 및 추론 능력 향상**으로 이어지는 포괄적인 접근 방식임을 시사합니다.

#### Reward Model Design
본 논문은 수학 추론 문제에 대한 보상 모델 설계에 대해 심도있게 다룹니다. **목표는 모델이 생성한 답변의 정확성을 평가하고 올바른 답변을 신뢰성 있게 식별하는 효과적인 보상 모델을 개발하는 것**입니다. 이를 위해 다양한 문제와 난이도에 걸쳐 보상 모델을 평가하는 포괄적이고 강력한 벤치마크인 AceMath-RewardBench를 구축합니다.  **계획적인 접근 방식을 통해 수학 보상 모델을 구축**하고, 양성-음성 쌍 구성, 훈련 목표, 특정 LLM의 스타일 편향 제거 등 주요 측면을 체계적으로 조사합니다. **결과적으로 기존 최첨단 보상 모델을 능가하는 AceMath-72B-RM 모델을 제시**합니다. 이 모델은 다양한 문제와 난이도에서 일관되게 우수한 성능을 보이며, AceMath-72B-Instruct와 결합하여 수학 추론 벤치마크에서 최고의 평균 rm@8 점수를 달성합니다.  **개방형 가중치 기반 LLM과 수학 기반 LLM을 사용하여 사후 훈련 및 보상 모델링을 기반으로 수학 추론의 한계를 넓혔다**는 점이 중요한 성과입니다.

#### AceMath Benchmarks
AceMath 벤치마크는 논문에서 제시된 다양한 수학 추론 벤치마크에 대한 성능을 종합적으로 평가하는 척도입니다. **GSM8K, MATH, Minerva Math, Gaokao 2023 English, Olympiad Bench, College Math, 그리고 MMLU STEM**과 같은 기존 벤치마크 외에도 **AMC 2023과 AIME 2024** 와 같은 새로운 벤치마크도 포함되어 있습니다. 이를 통해 AceMath 모델의 폭넓은 수학적 문제 해결 능력을 다각적으로 평가하고, 다양한 난이도와 유형의 문제에 대한 일반화 능력을 검증합니다.  **다양한 벤치마크의 포괄적인 평가**는 AceMath 모델의 강점과 약점을 파악하고, 향후 모델 개선 방향을 제시하는데 중요한 역할을 합니다. 특히, **기존 벤치마크를 뛰어넘는 새로운 벤치마크의 도입**은 AceMath의 혁신성을 더욱 부각시키는 요소입니다.

#### Ablation Study Insights
본 논문의 ablation study는 **모델 성능에 영향을 미치는 요소들을 체계적으로 분석**하여, 각 요소의 중요성과 상호작용을 밝히는 데 중점을 두었습니다.  특히, **두 단계로 나누어진 SFT 전략**의 효과, **다양한 데이터 구성** (합성 데이터 포함)의 영향, 그리고 **보상 모델 학습 전략**의 최적화 등에 대한 심층적인 분석을 통해, 모델 성능 향상에 기여하는 핵심 요소들을 도출했습니다.  **일반적인 SFT와 수학 전용 SFT의 결합**, 그리고 **정제된 합성 데이터의 활용**이 특히 주목할 만한 결과를 보여주었습니다.  이러한 연구 결과는 향후 **대규모 언어 모델의 수학적 추론 능력 향상**을 위한 방향을 제시하는 동시에, **보상 모델 개발 및 평가를 위한 새로운 기준**을 마련하는 데 기여할 것으로 기대됩니다.

#### Future Research
미래 연구 방향으로는 **AceMath 모델의 확장성 및 일반화 능력 향상**을 위한 연구가 중요합니다. 더욱 다양하고 복잡한 수학 문제를 해결할 수 있도록 모델의 크기와 훈련 데이터의 질을 높이는 연구가 필요하며, 특히 **다양한 수학적 표현 방식**에 대한 모델의 이해도를 높이는 연구가 중요합니다. 또한, **보상 모델의 성능 향상**을 위해 보다 정교한 보상 함수를 설계하고, 다양한 유형의 오류를 효과적으로 식별할 수 있는 기법을 개발하는 것이 필요합니다.  **다른 분야와의 연계 연구**도 중요한데, 예를 들어 과학, 공학 분야의 문제 해결에 AceMath를 적용하거나,  **다국어 지원 및 다양한 수학 교육 환경**에 적용하는 연구가 미래 연구의 주요 과제가 될 것입니다.  **모델의 설명력 향상** 및 **윤리적 문제**에 대한 고려도 중요한 연구 과제입니다.  결론적으로, AceMath 모델의 잠재력을 최대한 활용하고 한계를 극복하기 위한 꾸준한 연구와 개발이 필요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.15084/x2.png)

> 🔼 그림 2는 본 논문에서 사용된 지도 학습 미세 조정(SFT) 데이터셋의 구성 비율을 보여줍니다.  전체 SFT 토큰 중 수학 관련 토큰, 코딩 관련 토큰, 그리고 기타 영역 토큰의 비율을 시각적으로 나타냅니다.  수학 및 코딩 영역에 상당한 양의 데이터가 투입되었음을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: The proportion of total SFT tokens for math, coding, and other categories.
> </details>



![](https://arxiv.org/html/2412.15084/x3.png)

> 🔼 본 그림은 AceMath-Instruct 모델의 성능에 대한 기본 모델 또는 수학 기반 모델을 백본으로 사용했을 때의 영향을 보여줍니다. 서로 다른 모델 유형 및 크기에 걸쳐 해당 수학 지시 모델과 비교하여 모델 성능을 평가하고 있습니다. 결과는 수학 벤치마크에 대한 탐욕적 디코딩의 평균 점수를 나타냅니다.  즉, 다양한 크기의 언어 모델을 기본 모델 또는 수학 전용으로 미세 조정된 모델을 기반으로 학습시켰을 때,  AceMath-Instruct 모델의 성능 변화를 보여주는 그래프입니다. 그래프를 통해 기본 모델과 수학 기반 모델을 백본으로 사용하는 것이 모델 성능에 미치는 영향을 비교 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Studies on the impact of using either the base model or the math base model as the backbone on the performance of our AceMath-Instruct models. We compare our models against the corresponding math-instruct baselines across different model types and sizes. Results are the average scores of greedy decoding over the math benchmarks.
> </details>



![](https://arxiv.org/html/2412.15084/x4.png)

> 🔼 그림 4는 AceMath-7B-Instruct 모델의 성능을 다양한 수학 벤치마크 데이터셋 7개에 대해 rm@k 지표를 사용하여 평가한 결과를 보여줍니다. rm@k는 모델이 생성한 k개의 응답 중 정답을 포함하는 비율을 나타내는 지표입니다. 이 그림은 모델 크기가 증가함에 따라 정확도가 향상되는 것을 보여주는 학습 곡선을 제시하며, AceMath-7B-Instruct 모델의 성능이 데이터셋 종류에 따라 어떻게 달라지는지 보여줍니다.  다양한 데이터셋에서 평균 정확도를 비교하여 모델의 전반적인 성능을 평가하고, rm@k 값의 변화를 통해 모델의 응답 정확도를 다각적으로 분석합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: rm@k𝑘kitalic_k evaluation on average accuracy of 7 datasets for AceMath-7B-Instruct.
> </details>



![](https://arxiv.org/html/2412.15084/x5.png)

> 🔼 그림 5는 보상 모델 학습에 대한 학습 곡선을 보여줍니다.  모델 크기(0.5B, 1.5B, 3B, 7B, 14B, 32B 매개변수)별로 다양한 수학 벤치마크(GSM8K, MATH500, Minerva Math, Gaokao 2023EN, Olympiad Bench, College Math, MMLU STEM)에서의 정확도 변화를 보여줍니다.  Qwen2.5-Instruct 계열의 모델들을 사용하여 학습하였으며, 학습 진행에 따른 정확도 향상 추세를 보여줍니다. 특히, 더 어려운 문제를 요구하는 벤치마크에서 더 큰 모델이 더 나은 성능을 보이는 경향을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Learning curves for reward model training. All models are trained from Qwen2.5-Instruct family.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Models | HumanEval | MBPP | GSM8K | MATH | MMLU | MMLU Pro | Avg. |
|---|---|---|---|---|---|---|---| 
| Llama3.1-8B-Base + Two-Stage SFT | **81.10** | **74.71** | **90.45** | **64.42** | **68.31** | **43.27** | **70.38** |
| Llama3.1-8B-Base + Single-Stage SFT w/ all general SFT data | 78.66 | 69.26 | 87.79 | 56.80 | 67.62 | 42.64 | 67.13 |
| Llama3.1-8B-Base + Single-Stage SFT w/ only stage-2 data | 73.78 | 67.32 | 88.17 | 55.84 | 67.48 | 42.85 | 65.91 |
| Qwen2.5-7B-Base + Two-Stage SFT | **85.37** | 74.32 | **93.10** | **76.40** | **74.68** | **54.50** | **76.40** |
| Qwen2.5-7B-Base + Single-Stage SFT w/ all general SFT data | 83.54 | **75.49** | 91.96 | 75.04 | 73.96 | 53.36 | 75.56 |
| Qwen2.5-7B-Base + Single-Stage SFT w/ only stage-2 data | 83.54 | 73.15 | 92.27 | 75.12 | 74.26 | 53.06 | 75.23 |{{< /table-caption >}}
> 🔼 표 2는 본 논문에서 제안하는 2단계 일반 SFT(Supervised Fine-Tuning) 전략의 효과를 평가하기 위한 실험 결과를 보여줍니다. 다양한 기본 모델(Llama3.1-8B, Qwen2.5-7B)에 대해 2단계 SFT 전략을 적용하고, 단일 단계 SFT 전략 (전체 일반 SFT 데이터 사용, 2단계 데이터만 사용)과 비교 분석합니다.  각 SFT 전략의 성능을 HumanEval, MBPP, GSM8K, MATH, MMLU, MMLU Pro 등 다양한 벤치마크에서 평가하여 2단계 전략의 효과를 정량적으로 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Ablation studies of our general SFT models regarding the effectiveness of the two-stage training strategy.
> </details>

{{< table-caption >}}
| Models | GSM8K | MATH | Minerva Math | GaoKao 2023 En | Olympiad Bench | College Math | MMLU STEM | Avg. |
|---|---|---|---|---|---|---|---|---|
| GPT-4o (2024-0806) | 92.90 | 81.10 | 50.74 | 67.50 | 43.30 | 48.50 | **87.99** | 67.43 |
| Claude-3.5 Sonnet (2024-1022) | 96.40 | 75.90 | 48.16 | 64.94 | 37.93 | 48.47 | 85.06 | 65.27 |
| Llama3.1-70B-Instruct | 94.10 | 65.70 | 34.20 | 54.00 | 27.70 | 42.50 | 80.40 | 56.94 |
| Llama3.1-405B-Instruct | **96.80** | 73.80 | 54.04 | 62.08 | 34.81 | 49.25 | 83.10 | 64.84 |
| OpenMath2-Llama3.1-8B | 91.70 | 67.80 | 16.91 | 53.76 | 28.00 | 46.13 | 46.02 | 50.08 |
| Qwen2.5-Math-1.5B-Instruct | 84.80 | 75.80 | 29.40 | 65.50 | 38.10 | 47.70 | 57.50 | 56.97 |
| Qwen2.5-Math-7B-Instruct | 95.20 | 83.60 | 37.10 | 66.80 | 41.60 | 46.80 | 71.90 | 63.29 |
| Qwen2.5-Math-72B-Instruct | 95.90 | 85.90 | 44.10 | 71.90 | **49.00** | 49.50 | 80.80 | 68.16 |
| AceMath-1.5B-Instruct (Ours) | 86.95 | 76.84 | 41.54 | 64.42 | 33.78 | 54.36 | 62.04 | 59.99 |
| AceMath-7B-Instruct (Ours) | 93.71 | 83.14 | 51.11 | 68.05 | 42.22 | 56.64 | 75.32 | 67.17 |
| AceMath-72B-Instruct (Ours) | 96.44 | **86.10** | **56.99** | **72.21** | 48.44 | **57.24** | 85.44 | **71.84** |{{< /table-caption >}}
> 🔼 표 3은 다양한 수학 벤치마크에서 수학 관련 지시 모델의 탐욕적 디코딩(pass@1) 결과를 보여줍니다. AceMath-1.5B/7B/72B-Instruct 모델은 Qwen2.5-Math-1.5B/7B/72B 기본 모델을 기반으로 구축되었으며, 특히 AceMath-72B-Instruct 모델은 이전 최첨단 수학 지시 모델인 Qwen2.5-Math-72B-Instruct 모델을 크게 능가합니다. 이 표는 다양한 크기의 모델들(1.5B, 7B, 72B)의 성능을 비교하여 모델 크기가 성능에 미치는 영향을 보여줍니다.  각 모델은 여러 수학 벤치마크(GSM8K, MATH, Minerva Math, Gaokao 2023 English, Olympiad Bench, College Math, MMLU STEM)에서 평가되었으며, pass@1 정확도가 제시됩니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Greedy decoding (pass@1) results of math instruct models on math benchmarks. Our AceMath-1.5B/7B/72B-Instruct models are built upon the Qwen2.5-Math-1.5B/7B/72B-base models. AceMath-72B-Instruct greatly surpasses the previous state-of-the-art math-instruct model, Qwen2.5-Math-72B-Instruct.
> </details>

{{< table-caption >}}
|Minerva|
|---|---| 
|Math|{{< /table-caption >}}
> 🔼 표 4는 AceMath-Instruct 모델 학습을 위한 다양한 기본 모델에 대한 학습 데이터 및 전략에 대한 추가 분석 결과를 보여줍니다. 이 표는 세 가지 측면으로 나뉘어져 있습니다. 첫째, GPT-40-mini 응답과 Qwen-2.5-Math-72B-Instruct 응답을 개별적으로 사용했을 때의 효과를 평가합니다. 둘째, 수학 SFT를 위한 다양한 수학 특정 샘플의 효과를 분석합니다. 셋째, 수학 SFT 전에 일반적인 SFT를 수행했을 때의 영향을 평가합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Ablation Studies on training data and strategies across various backbone models for training our AceMath-Instruct models. The ablation studies can be categorized into three parts: 1) evaluating the effectiveness of using either GPT-4o-mini responses or Qwen2.5-Math-72B-Instruct responses individually; 2) analyzing the effectiveness of different math-specific samples for math SFT; and 3) assessing the impact of conducting general SFT prior to math SFT.
> </details>

{{< table-caption >}}
| GaoKao |
|---|---| 
| 2023 En |{{< /table-caption >}}
> 🔼 이 표는 AceMath-Instruct 모델에 대한 에이블레이션 연구 결과를 보여줍니다.  Qwen2.5-7B-Base 모델을 백본으로 사용하여, 합성된 수학 SFT 데이터를 제거하거나 저품질의 합성 데이터를 추가했을 때의 성능 변화를 보여줍니다.  7개의 수학 벤치마크에 대한 평균 점수를 나타냅니다.  합성 데이터의 품질과 양이 모델 성능에 미치는 영향을 분석하기 위한 실험 결과입니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Ablation studies on the synthetic data, exploring the effects of removing all synthetic math SFT data and incorporating additional low-quality synthetic math SFT data. The backbone of AceMath-Instruct is Qwen2.5-7B-Base. Results are average across the seven math benchmark.
> </details>

{{< table-caption >}}
| Olympiad | Bench |
|---|---|{{< /table-caption >}}
> 🔼 표 6은 AceMath-RewardBench에 대한 reward model 평가 결과를 보여줍니다.  7개의 수학 벤치마크에 대해 평가했으며, 각 문제마다 8개의 LLM (Qwen{2/2.5}-Math-{7/72}B-Instruct, Llama-3.1-{8/70}B-Instruct, Mathtral-7B-v0.1, deepseek-math-7b-instruct)에서 생성된 64개의 응답 후보 중 8개를 무작위로 선택하여 rm@8 지표를 계산했습니다. 이 과정을 100번 반복하여 평균 rm@8 점수를 산출했습니다.  표에는 각 모델의 평균 rm@8 정확도와 7개 벤치마크별 성능이 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Reward model evaluation on AceMath-RewardBench. The average results (rm@8) of reward models on math benchmarks, randomly sample 8 responses from 64 candidates with 100 random seeds. Response candidates are generated from a pool of 8 LLMs (Qwen{2/2.5}-Math-{7/72}B-Instruct, Llama-3.1-{8/70}B-Instruct, Mathtral-7B-v0.1, deepseek-math-7b-instruct).
> </details>

{{< table-caption >}}
| College |
|---|---| 
| Math |{{< /table-caption >}}
> 🔼 표 7은 Lambert et al.(2024)의 RewardBench(MATH500)와 Kim et al.(2024)의 RewardMATH 두 가지 벤치마크에서 다양한 보상 모델의 정확도를 보여줍니다. RewardBench는 MATH 데이터셋의 500개 문제를 사용하며, 하나의 정답과 하나의 오답 후보를 제공하는 반면, RewardMATH는 하나의 정답(GPT-4가 다시 작성)과 9개의 오답 후보를 제공합니다.  표는 각 모델의 MATH500과 RewardMATH에서의 정확도(rm@8 지표 사용)를 보여주며, 최고 정확도(top-1)와 두 번째로 높은 정확도(top-2)를 굵은 글씨와 밑줄로 표시하여 시각적 이해를 돕습니다.  RewardMATH의 결과는 해당 논문에서 가져온 것입니다. 이 표는 보상 모델이 다양한 스타일과 복잡성의 수학 문제에 어떻게 반응하는지 비교 분석하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 7: The accuracy of reward models on RewardBench (MATH500) (Lambert et al., 2024) and RewardMATH (Kim et al., 2024). ††\dagger†: Results are copied from RewardMATH. Bold: top-1. Underline: top-2 accuracy.
> </details>

{{< table-caption >}}
| MMLU |
|---|---| 
| STEM |{{< /table-caption >}}
> 🔼 표 8은 AceMath-RewardBench를 사용하여 AceMath-7/72B-RM에 대한 추가 분석 결과를 보여줍니다.  기본 모델(Backbone)은 AceMath-7/72B-Instruct이며, 데이터는 보상 점수를 기반으로 정렬된 샘플링(reward score-sorted sampling) 방식을 사용했고, 손실 함수(Loss)는 listwise Bradley-Terry 함수를 사용했습니다. 이 표는 보상 모델의 성능에 영향을 미치는 요소들(예: 기본 모델, 데이터 샘플링 방법, 손실 함수)을 각각 변화시켜가며 실험한 결과를 비교 분석하여 어떤 요소가 가장 큰 영향을 주는지 파악하고, 보상 모델의 성능 향상에 기여할 수 있는 최적의 설정을 찾는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Ablation study of AceMath-7/72B-RM on AceMath-RewardBench (Backbone: AceMath-7/72B-Instruct; Data: reward score-sorted sampling; Loss: listwise Bradley-Terry.
> </details>

{{< table-caption >}}
| Models | GSM8K | MATH | Minerva | GaoKao | Olympiad | College | MMLU | Avg. |
|---|---|---|---|---|---|---|---|---|
| Backbone: Llama3.1-8B-Base |  |  |  |  |  |  |  |  |
| AceMath-Instruct | 91.51 | 69.06 | 31.99 | 59.74 | 32.00 | 49.08 | 67.94 | 57.33 |
| ▷ Only Qwen2.5-Math-72B-Instruct | 91.13 | 69.66 | 33.82 | 60.26 | 30.37 | 49.86 | 66.21 | 57.33 |
| ▷ Only GPT-4o-mini | 90.83 | 68.12 | 36.03 | 60.26 | 31.70 | 48.05 | 66.50 | **57.36** |
| ▷ Skipping general SFT | 91.81 | 68.70 | 31.99 | 59.48 | 31.11 | 48.40 | 62.76 | 56.32 |
| Backbone: Qwen2.5-7B-Base |  |  |  |  |  |  |  |  |
| AceMath-Instruct | 93.56 | 77.10 | 43.38 | 65.19 | 37.78 | 54.90 | 77.41 | **64.19** |
| ▷ Only Qwen2.5-Math-72B-Instruct | 92.80 | 76.96 | 41.91 | 63.64 | 38.07 | 54.93 | 75.64 | 63.42 |
| ▷ Only GPT-4o-mini | 91.66 | 74.14 | 43.75 | 64.42 | 39.26 | 52.27 | 76.03 | 63.08 |
| ▷ Math SFT with all math samples | 93.40 | 77.12 | 42.28 | 65.19 | 37.78 | 54.05 | 75.33 | 63.59 |
| ▷ Math SFT with only cross-checked samples | 92.72 | 76.76 | 41.54 | 65.97 | 36.74 | 54.33 | 76.78 | 63.55 |
| ▷ Skipping general SFT | 93.03 | 77.52 | 40.44 | 62.86 | 37.19 | 54.58 | 75.77 | 63.06 |
| Backbone: Qwen2.5-Math-72B-Base |  |  |  |  |  |  |  |  |
| AceMath-Instruct | 96.44 | 86.10 | 56.99 | 72.21 | 48.44 | 57.24 | 85.44 | **71.84** |
| ▷ Math SFT with all math samples | 96.29 | 86.06 | 55.15 | 70.13 | 46.67 | 57.49 | 84.96 | 70.96 |
| ▷ Skipping general SFT | 95.75 | 85.52 | 56.25 | 71.43 | 45.33 | 56.71 | 84.42 | 70.77 |{{< /table-caption >}}
> 🔼 표 9는 AceMath-Instruct 모델의 AIME 2024 및 AMC 2023 데이터셋에 대한 정답률을 보여줍니다.  Greedy decoding 방식을 사용하여 모델의 성능을 평가했습니다.  AIME 2024는 고난이도 수학 문제를 포함하고 있고, AMC 2023은 상대적으로 쉬운 문제들을 포함하고 있기 때문에, 두 데이터셋에 대한 결과를 비교함으로써 AceMath-Instruct 모델의 다양한 난이도의 문제에 대한 해결 능력을 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Greedy decoding results of AceMath-Instruct on AIME 2024 and AMC 2023.
> </details>

{{< table-caption >}}
|Minerva|
|---|---| 
|Math|{{< /table-caption >}}
> 🔼 표 10은 다양한 백본 모델을 사용하여 AceMath-Instruct 모델의 성능을 평가한 결과를 보여줍니다.  AceMath-Instruct 모델은 다양한 크기의 Qwen2.5, Llama 3.1, DeepSeek-Coder 백본 모델을 기반으로 미세 조정되었으며, GSM8K, MATH, Minerva Math, Gaokao 2023 English, Olympiad Bench, College Math, MMLU STEM 등 다양한 수학 벤치마크에서 성능을 평가했습니다. 이 표는 각 백본 모델의 종류와 크기, 그리고 AceMath-Instruct 모델의 성능을 비교하여 어떤 백본 모델이 AceMath-Instruct 모델의 성능에 가장 큰 영향을 미치는지 확인하고,  다양한 크기의 모델에서 AceMath-Instruct 모델의 일반화 능력을 분석하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Greedy decoding results of AceMath-Instruct across different backbone models.
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
{{< /gallery >}}