---
title: "Critique Fine-Tuning: Learning to Critique is More Effective than Learning to Imitate"
summary: "비판적 사고를 활용한 새로운 언어 모델 학습 기법인 CFT가 기존 SFT보다 효율적임을 증명!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Carnegie Mellon University",]
showSummary: true
date: 2025-01-29
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.17703 {{< /keyword >}}
{{< keyword icon="writer" >}} Yubo Wang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-30 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.17703" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.17703" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/critique-fine-tuning-learning-to-critique-is" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 언어 모델 학습 방식인 **지도 학습 미세 조정(SFT)**은 방대한 양의 주석 달린 데이터를 필요로 하며, 이미 강력한 기반 모델에는 성능 향상에 한계가 있습니다.  본 논문은 이러한 문제를 해결하기 위해 **새로운 학습 방식인 비판적 미세 조정(CFT)**을 제안합니다. CFT는 모델이 정답을 단순히 모방하는 대신 오류가 있는 응답을 비판적으로 분석하고 개선하는 방식입니다.

본 연구는 CFT를 검증하기 위해 **5만 개의 데이터셋**을 구축하여 다양한 기반 모델과 벤치마크에 적용했습니다. 그 결과, CFT는 기존 SFT 방식보다 **4~10% 향상된 성능**을 보였으며, **기존 모델보다 적은 데이터**로도 우수한 성능을 달성했습니다.  특히, 수학 추론 벤치마크에서 큰 성능 향상을 보이며, **CFT가 효율적이고 강력한 학습 전략**임을 입증했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} CFT는 SFT보다 적은 데이터로도 우수한 성능을 달성합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} CFT는 다양한 기반 모델과 벤치마크에서 SFT를 능가하는 성능을 보여줍니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} CFT는 비판적 사고를 강조하여 보다 심층적인 이해와 미묘한 차이를 학습합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **기존의 지도 학습 방식(SFT)의 한계를 극복**하고 **더 효율적이고 효과적인 언어 모델 학습 방식**을 제시합니다.  **제한된 데이터로도 우수한 성능**을 달성함으로써, **연구자들이 보다 적은 비용과 노력으로 고성능 모델을 개발**할 수 있도록 돕습니다. 또한, **새로운 연구 방향**을 제시하여 **향후 연구의 발전**에 기여할 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.17703/x2.png)

> 🔼 그림 1은 WebInstruct 데이터셋(Yue et al., 2024b)의 50,000개 샘플을 사용하여 비교된 CFT(Critique Fine-Tuning)와 SFT(Supervised Fine-Tuning)의 성능을 보여줍니다.  SFT-verified는 GPT-4o에 의해 검증된 응답에 대해 SFT 훈련을 수행한 것을 의미하며, SFT-GPT4o는 GPT-4o가 생성한 응답에 대한 SFT 훈련을 의미합니다.  CFT는 본 논문에서 제안하는 방법으로, GPT-4o가 제공한 비평(critique)을 기반으로 훈련됩니다.  그림에서는 다양한 벤치마크(MATH, OlympiadBench 등)에서 CFT와 SFT의 평균 정확도를 비교하여 CFT의 우수성을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Comparison between CFT and SFT on 50K samples from WebInstruct (Yue et al., 2024b). SFT-verified means SFT training on the responses validated by GPT-4o, SFT-GPT4o means SFT training on the responses from GPT-4o. CFT is our approach, which trains on the critique provided by GPT-4o.
> </details>





{{< table-caption >}}
| Dataset | Size | Source or Seed | Discipline |
|---|---|---|---|
| **Supervised Fine-Tuning Data** |  |  |  |
| WizardMath | 96K | GSM8K, MATH | Math |
| MathInstruct | 260K | GSM8K, MATH, etc | Math |
| MetaMathQA | 395K | GSM8K, MATH | Math |
| XwinMath | 1.4M | GSM8K, MATH | Math |
| OrcaMath | 200K | GSM8K | Math |
| NuminaMath | 860K | GSM8K, MATH, AIME | Math |
| AceMath | 1.6M | GSM8K, MATH, AIME | Math |
| OpenMath-2 | 14M | GSM8K, MATH | Math |
| **Critique Fine-Tuning Data (Ours)** |  |  |  |
| CFT | 50K | WebInstruct | STEM |
| CFT-tiny | 4K | WebInstruct | STEM |{{< /table-caption >}}

> 🔼 표 1은 본 논문에서 제안하는 방법(CFT)의 효과를 검증하기 위해 사용된 데이터셋을 기존의 SFT 및 강화학습(RL) 기반 모델들과 비교 분석한 표입니다.  Mammoth3를 포함하여 WizardMath, MathInstruct, MetaMathQA, XWinMath, OrcaMath, NuminaMath, AceMath, OpenMathInstruc-2, Qwen2.5-Math 등 다양한 모델들의 데이터셋 크기, 데이터 소스, 그리고 해당 모델이 주로 다루는 학문 분야(주로 수학)를 비교하여 CFT 데이터셋의 특징(다양한 주제를 다루고 데이터 크기가 상대적으로 작음)을 부각하고 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: The comparison of MAmmoTH3 vs other SFT and RL models including WizardMath (Luo et al., 2023), MathInstruct (Yue et al., 2024a), MetaMathQA (Yu et al., 2024), XWinMath (Li et al., 2024a), OrcaMath (Mitra et al., 2024), NuminaMath (Li et al., 2024b), AceMath (Liu et al., 2024), OpenMathInsstruct-2 (Toshniwal et al., 2024) and Qwen2.5-Math (Yang et al., 2024c).
> </details>





### In-depth insights


#### Critique Fine-Tuning
본 논문에서 제시하는 "Critique Fine-Tuning (CFT)"은 기존의 지도 학습 방식인 SFT(Supervised Fine-Tuning)의 한계를 극복하기 위한 새로운 접근 방식입니다. **CFT는 모델이 정답을 단순히 모방하는 대신, 잘못된 답변을 비판하고 수정하는 과정을 통해 학습하도록 합니다.**  이를 통해 모델은 단순한 모방을 넘어 **더욱 깊이 있는 이해와 미묘한 차이를 구별하는 능력을 갖추게 됩니다.**  **인간의 학습 과정에서 비판적 사고의 중요성을 강조하여 영감을 얻은 CFT**는, 표면적으로 정답처럼 보이는 답변에도 함정이 있을 수 있음을 인지하고, **오류를 식별하고 수정하며, 정확성을 검증하는 능력**을 향상시킵니다.  **대규모 데이터셋 없이도 우수한 성능을 달성**한다는 점에서 효율성이 뛰어나며, 다양한 기반 모델과 벤치마크에서 SFT를 능가하는 성능을 보여줍니다.  하지만, **비판적 피드백의 질에 대한 의존성**과 **자기 비판 기능의 부재**는 향후 개선 과제로 남아있습니다.

#### CFT vs. SFT
본 논문은 지도 미세 조정(SFT)의 패러다임을 재고하고, **오류 있는 응답을 단순히 모방하는 대신, 모델이 소음이 많은 응답을 비판적으로 평가하도록 학습시키는 새로운 전략인 비판 미세 조정(CFT)**을 제안합니다.  **CFT는 인간의 학습 과정에서 중요한 역할을 하는 비판적 사고와 구조적 피드백을 활용하여 심층적 분석과 미묘한 이해를 장려**합니다.  실험 결과는 **CFT가 다양한 기본 모델과 벤치마크에서 SFT를 일관되게 능가**함을 보여줍니다.  특히, **CFT는 기존 SFT보다 적은 데이터(5만개 샘플)로도 유사하거나 더 나은 성능**을 달성하며 효율성을 입증합니다.  **CFT의 강점은 소음이 많은 응답의 출처와 교사 모델에 대한 견고성**에 있습니다.  즉, 데이터의 질에 덜 민감하고 다양한 상황에서도 우수한 성능을 유지합니다.  하지만, **CFT는 교사 모델의 오류에 취약하며, 자기 비판 기능이 부족**하여 추가 연구가 필요한 부분입니다.

#### CFT Datasets
본 논문에서 CFT(Critique Fine-Tuning) 데이터셋에 대한 심층적인 논의는 부족하지만, **웹데이터를 기반으로 생성된 50K 크기의 데이터셋**이 사용되었다는 점을 알 수 있습니다. 이는 기존 SFT 방식의 대규모 데이터셋에 비해 훨씬 작은 규모이지만, **GPT-4와 같은 고성능 모델이 생성한 질문과 답변, 그리고 그에 대한 비평을 포함**한다는 점에서 차별성을 가집니다.  **비평 데이터를 활용하여 모델이 단순히 모방하는 것을 넘어, 더욱 심층적인 이해와 분석 능력을 함양**하도록 설계되었다는 점이 중요합니다.  데이터셋의 크기가 작더라도, **비평이라는 새로운 학습 신호**를 통해 효율적인 학습을 가능하게 했다는 점을 시사합니다.  **다만, GPT-4에 의존적인 데이터 생성 방식**은 한계로 지적될 수 있으며, 향후 연구에서는 더 다양한 데이터 소스와 비평 생성 방식을 고려하는 것이 필요할 것입니다.  **데이터의 질적 측면** 또한 중요한 평가 요소이며, 향후 연구에서 데이터 품질 관리 및 개선 방안에 대한 추가적인 논의가 필요할 것으로 예상됩니다.

#### Ablation Studies
본 논문에서 제시된 ‘에이블레이션 스터디’는 **CFT(Critique Fine-Tuning)의 강건성과 효율성을 입증**하기 위한 중요한 부분입니다.  다양한 데이터 소스(WebInstruct, MetaMathQA, NuminaMath)를 사용한 실험을 통해 CFT의 **데이터 소스에 대한 강건성**을 확인했습니다.  또한, 다양한 노이즈 있는 응답 소스와 교사 모델을 사용한 실험으로 CFT의 **노이즈에 대한 강건성**과 **교사 모델 선택에 대한 유연성**을 보여주었습니다.  **결과적으로, CFT는 데이터 품질이나 모델 선택에 크게 영향받지 않고 일관된 성능 향상을 보여주어 실용적인 측면에서 높은 가치를 지닌다고 볼 수 있습니다.** 이러한 에이블레이션 스터디는 CFT의 메커니즘 이해와 실제 적용 가능성에 대한 믿음을 더욱 높여줍니다.  **향후 연구에서는 더욱 정교한 에이블레이션 스터디를 통해 CFT의 한계점을 규명하고 성능 개선 방안을 모색**하는 것이 중요할 것입니다.

#### Self-Critique Limits
자기 비판의 한계에 대한 심층적인 논의는 **모델의 자기 반성 능력의 부족**을 보여줍니다.  **완벽한 자기 평가는 아직 어렵고, 과도한 자기 확신이나 잘못된 오류 수정으로 이어질 수 있다는 점**을 시사합니다.  이는 **데이터 품질과 모델의 복잡성**에 영향을 받으며, **더욱 정교한 자기 비판 메커니즘** 개발이 필요함을 강조합니다.  **자기 비판 과정에서 발생하는 오류의 유형과 그 원인에 대한 분석**을 통해, 향후 연구 방향을 제시하고 **더욱 효과적인 자기 개선 전략**을 모색하는 데 도움을 줄 수 있습니다.  **데이터의 질적 향상 및 더욱 강력한 모델의 개발**은 자기 비판의 정확성을 높이는 데 중요하며, **인간 전문가의 개입을 통한 검증 및 보정**이 효과적인 해결책이 될 수 있습니다.  **자기 비판 과정의 투명성 확보 및 오류 분석 시스템 구축**도 중요한 과제로 제기됩니다.


### More visual insights




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | Method | MATH | Minerva-Math | GSM8K | OlympiadBench | AIME24 | AMC23 | AVG |
|---|---|---|---|---|---|---|---|---|
| DeepSeek-Math-7B | Base | 33.8 | 9.2 | 64.3 | 4.5 | 0.0 | 10.0 | 20.3 |
|  | WebInstruct-SFT | 26.3 | 12.1 | 34.7 | 6.2 | 0.0 | 17.5 | 16.1 |
|  | WebInstruct-verified-SFT | 35.8 | 10.7 | 67.5 | 9.3 | 0.0 | 7.5 | 21.8 |
|  | WebInstruct-GPT4o-SFT | 31.7 | 11.8 | 70.9 | 8.9 | 3.3 | 17.5 | 24.0 |
|  | WebInstruct-CFT | 42.2 | 12.5 | 74.5 | 12.4 | 3.3 | 20.0 | 27.5 |
|  | Δ = CFT- SFT<sub>best</sub> | 6.4 | 0.4 | 3.6 | 3.1 | 0.0 | 2.5 | 3.5 |
| Qwen2.5-7B | Base | 49.8 | 15.1 | 85.4 | 26.3 | 10.0 | 37.5 | 37.4 |
|  | WebInstruct-SFT | 30.8 | 6.6 | 59.5 | 5.8 | 3.3 | 15.0 | 20.2 |
|  | WebInstruct-verified-SFT | 61.5 | 16.2 | 70.8 | 30.1 | 13.3 | 37.5 | 38.2 |
|  | WebInstruct-GPT4o-SFT | 45.5 | 18.4 | 77.4 | 19.7 | 10.0 | 50.0 | 36.8 |
|  | WebInstruct-CFT | 71.1 | 27.9 | 88.8 | 35.7 | 13.3 | 55.0 | 48.6 |
|  | Δ = CFT- SFT<sub>best</sub> | 9.6 | 9.5 | 11.4 | 5.6 | 0.0 | 5.0 | 10.4 |
| Qwen2.5-Math-7B | Base | 55.4 | 13.6 | 91.6 | 16.1 | 10.0 | 40.0 | 37.8 |
|  | WebInstruct-SFT | 59.0 | 13.2 | 77.4 | 19.9 | 3.3 | 37.5 | 35.1 |
|  | WebInstruct-verified-SFT | 62.0 | 12.5 | 78.8 | 22.1 | 16.7 | 50.0 | 40.4 |
|  | WebInstruct-GPT4o-SFT | 73.2 | 25.7 | 90.0 | 37.6 | 13.3 | 62.5 | 50.4 |
|  | WebInstruct-CFT | 79.4 | 36.8 | 90.9 | 41.6 | 20.0 | 67.5 | 56.0 |
|  | Δ = CFT- SFT<sub>best</sub> | 6.2 | 11.1 | 0.9 | 4.0 | 3.3 | 5.0 | 5.7 |{{< /table-caption >}}
> 🔼 표 2는 다양한 기본 모델에 대한 SFT(Supervised Fine-Tuning)와 CFT(Critique Fine-Tuning)의 성능 비교 결과를 보여줍니다. 모든 실험은 WebInstruct 하위 집합을 사용하여 진행되었으며, 검증 점수가 가장 높은 체크포인트를 선택하여 결과를 보고합니다.  MATH, Minerva-Math, GSM8K, OlympiadBench, AIME24, AMC23의 여섯 가지 벤치마크에 대한 성능을 측정하여 평균 성능을 비교 분석합니다. DeepSeek-Math-7B, Qwen2.5-7B, Qwen2.5-Math-7B 세 가지 모델에 대해 SFT와 CFT를 적용한 결과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Performance comparison of SFT and CFT on different base models. All the experiments are trained with WebInstruct subset. We select the checkpoint with highest validation score and report their results.
> </details>

{{< table-caption >}}
| Model | #Data | MATH | GPQA | TheoremQA | MMLU-Pro | OlympiadBench | AIME24 | AMC23 | AVG |
|---|---|---|---|---|---|---|---|---|---| 
| Frontier Models |  |  |  |  |  |  |  |  |  |
| GPT-4o (2024-08-06) | - | 81.1 | 51.6 | 54.7 | 74.7 | 43.3 | 9.3 | 47.5 | 51.7 |
| GPT-o1-mini | - | 90.0 | 60.0 | 57.2 | 80.3 | 65.3 | 56.7 | 95.0 | 72.1 |
| Other Open-sourced Reasoning LLMs |  |  |  |  |  |  |  |  |  |
| Deepseek-Math-7B-Instruct | - | 44.3 | 31.8 | 23.7 | 35.3 | 13.6 | 3.3 | 15.0 | 23.9 |
| Mathstral-7B-v0.1 | - | 56.6 | 32.2 | 28.4 | 42.5 | 21.5 | 6.7 | 42.4 | 32.9 |
| NuminaMath-7B-CoT | - | 55.2 | 30.6 | 28.6 | 38.6 | 19.9 | 6.7 | 30.0 | 29.9 |
| Llama-3.1-8B-Instruct | - | 51.9 | 30.4 | 30.3 | 48.3 | 14.4 | 6.7 | 30.0 | 30.3 |
| Llama-3.1-70B-Instruct | - | 65.7 | 42.2 | 51.3 | 62.8 | 14.4 | 16.7 | 30.0 | 40.4 |
| NuminaMath-72B-CoT | - | 68.0 | 35.3 | 24.9 | 55.0 | 35.0 | 3.3 | 52.5 | 39.1 |
| Qwen2.5-Math-72B-Instruct | - | 85.9 | 49.0 | 50.3 | 60.3 | 49.0 | 30.0 | 70.0 | 56.4 |
| Initialized from Qwen2.5-Math-7B-Base |  |  |  |  |  |  |  |  |  |
| Qwen2.5-Math-Base | 0 | 55.4 | 31.0 | 37.4 | 39.3 | 16.1 | 10.0 | 40.0 | 32.7 |
| Eurus-2-SFT | 230K | 62.4 | 32.1 | 38.0 | 44.2 | 29.8 | 3.3 | 30.1 | 34.3 |
| rStar-Math@Greedy | 747K | 78.4 | - | - | - | 47.1 | 26.7 | 47.5 | - |
| AceMath-Qwen2.5-Math | 2.3M | 83.1 | 26.1 | 24.6 | 48.1 | 42.2 | 16.7 | 60.0 | 43.0 |
| Qwen2.5-Math-7B-Instruct | 2.5M | 83.6 | 31.1 | 37.0 | 39.5 | 41.6 | 16.7 | 62.5 | 44.6 |
| Qwen2.5-Math-7B-CFT | 50K | 79.4 | 39.4 | 40.4 | 47.5 | 41.6 | 20.0 | 67.5 | 48.0 |{{< /table-caption >}}
> 🔼 표 3은 제시된 모델과 다른 추론 전문 모델들의 성능 비교를 보여줍니다. 데이터 수는 전체 학습 데이터 크기를 나타내지만, 최고 검증 점수를 가진 체크포인트를 선택하여 결과를 제시합니다.  모델의 성능은 MATH, GPQA, TheoremQA, MMLU-Pro, OlympiadBench, AIME24, AMC23 등 다양한 벤치마크에 대한 평균 점수로 측정됩니다. 이 표는 제시된 CFT 모델이 다른 모델들보다 적은 학습 데이터로도 우수한 성능을 달성함을 보여주는 데 중점을 둡니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Performance comparison of our models vs. other reasoning-specialized models. #Data means the total training set size, but we select the checkpoint with highest validation score.
> </details>

{{< table-caption >}}
| Model | #Data | GPQA | TheoremQA | AMC23 |
|---|---|---|---|---|
| Qwen2.5-32B-Instruct | - | 49.5 | 44.6 | 72.5 |
| Sky-T1-32B-Preview | 17K | 49.5 | 48.9 | 67.5 |
| Qwen2.5-32B-Instruct-CFT | 4K | 52.5 | 48.1 | 77.5 |
| Δ (CFT - Sky-T1) | - | 3.0 | -0.8 | 10.0 |{{< /table-caption >}}
> 🔼 표 4는 수학적 추론 벤치마크에서 32B 모델의 성능을 비교한 것입니다.  Qwen2.5-32B-Instruct-CFT와 Sky-T1-32B-Preview 두 모델의 GPQA, TheoremQA, AMC23 세 가지 지표에 대한 성능을 보여줍니다.  특히, 데이터 효율성 측면에서 Qwen2.5-32B-Instruct-CFT가 Sky-T1-32B-Preview보다 훨씬 우수함을 보여줍니다. 즉, 훨씬 적은 훈련 데이터로도 경쟁력 있는 성능을 달성합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Performance Comparison of 32B Models across Mathematical Reasoning Benchmarks
> </details>

{{< table-caption >}}
| Task | MetaMathQA |  | NuminaMath |  | WebInstruct |  |
|---|---|---|---|---|---|---|
|  | SFT | CFT | SFT | CFT | SFT | CFT |
| MATH | 57.5 | 74.4 | 70.8 | 74.2 | 59.0 | 79.4 |
| Minerva-Math | 23.9 | 39.3 | 28.3 | 30.5 | 13.2 | 36.8 |
| GSM8K | 79.5 | 85.7 | 88.3 | 89.1 | 77.4 | 90.9 |
| OlympiadBench | 20.0 | 36.4 | 36.3 | 37.2 | 19.9 | 41.6 |
| AIME24 | 6.7 | 23.3 | 10.0 | 23.3 | 3.3 | 20.0 |
| AMC23 | 37.5 | 57.5 | 50.0 | 62.5 | 37.5 | 67.5 |
| AVG | 37.5 | 52.8 | 47.3 | 52.8 | 35.1 | 56.0 |{{< /table-caption >}}
> 🔼 표 5는 서로 다른 훈련 데이터셋을 사용하여 Qwen2.5-Math-7B 모델에 대해 SFT(Supervised Fine-Tuning)와 CFT(Critique Fine-Tuning)의 성능을 비교한 결과를 보여줍니다.  각 데이터셋(MetaMathQA, NuminaMath, WebInstruct)에서 모델 성능을 평가하여 SFT와 CFT의 효과를 다양한 상황에서 비교 분석합니다.  MATH, GSM8K, AIME24, AMC23 등 다양한 벤치마크에 대한 성능이 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Performance comparison of SFT and CFT with different training datasets on Qwen2.5-Math-7B.
> </details>

{{< table-caption >}}
| Task | Base | Self-generated | Reference |
|---|---|---|---|
| MATH | 55.4 | 78.2 | 79.4 |
| Minerva-Math | 13.6 | 29.4 | 36.8 |
| GSM8K | 91.6 | 92.4 | 90.9 |
| OlympiadBench | 16.1 | 42.5 | 41.6 |
| AIME24 | 10.0 | 16.7 | 20.0 |
| AMC23 | 40.0 | 67.5 | 67.5 |
| AVG | 37.8 | 54.5 | 56.0 |{{< /table-caption >}}
> 🔼 이 표는 CFT(Critique Fine-Tuning) 학습에 사용된 솔루션의 출처에 따른 성능 비교를 보여줍니다. Qwen2.5-Math-7B 모델이 자체적으로 생성한 솔루션과 WebInstruct 데이터셋의 참조 솔루션을 사용한 CFT 학습 결과를 비교 분석하여 각 솔루션 유형의 성능 차이와 효과를 제시합니다.  MATH, Minerva-Math, GSM8K, OlympiadBench, AIME24, AMC23 등 다양한 벤치마크에 대한 성능 결과를 포함합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Performance comparison between self-generated (by Qwen2.5-Math-7B) and reference solutions (from WebInstruct) for CFT training.
> </details>

{{< table-caption >}}
| Task | SFT-verified | GPT-4o-mini | GPT-4o-1120 |
|---|---|---|---| 
| MATH | 62.0 | 73.9 | 79.4 |
| Minerva-Math | 12.5 | 32.7 | 36.8 |
| GSM8K | 78.8 | 84.5 | 90.9 |
| OlympiadBench | 22.1 | 35.1 | 41.6 |
| AIME24 | 16.7 | 20.0 | 20.0 |
| AMC23 | 50.0 | 62.5 | 67.5 |
| AVG | 40.4 | 51.5 | 56.0 |{{< /table-caption >}}
> 🔼 표 7은 Qwen2.5-Math-7B 모델에 대해 서로 다른 교사 비평 모델을 사용한 CFT의 성능 비교를 보여줍니다.  다양한 비평 모델(예: GPT-40-mini, GPT-40-1120)을 사용하여 CFT를 훈련한 결과를 비교 분석하여, 비평 모델의 질이 CFT 성능에 미치는 영향을 평가합니다.  다양한 벤치마크 작업(예: MATH, Minerva-Math, GSM8K, OlympiadBench, AIME24, AMC23)에서의 성능을 정량적으로 비교하여, 어떤 비평 모델이 가장 효과적인지, 그리고 비평 모델의 질 향상이 CFT 성능 향상에 어떻게 기여하는지를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Performance comparison of CFT using different teacher critique models on Qwen2.5-Math-7B.
> </details>

{{< table-caption >}}
| Method | Temperature | MATH | Minerva-Math |
|---|---|---|---| 
| Direct inference | 0.0 | 79.4 | 36.8 |
|  | 0.1 | 78.8 | 35.9 |
|  | 0.3 | 77.5 | 34.7 |
|  | 0.6 | 75.2 | 33.1 |
| Single-pass self-critique | 0.1 | 77.2 | 33.7 |
|  | 0.3 | 76.1 | 32.2 |
|  | 0.6 | 73.5 | 31.3 |
| Two-stage self-critique | 0.1 | 77.9 | 35.2 |
|  | 0.3 | 75.8 | 32.4 |
|  | 0.6 | 74.6 | 31.5 |{{< /table-caption >}}
> 🔼 표 8은 다양한 온도 설정에서 여러 추론 방법의 성능을 비교한 표입니다.  직접 추론, 단일 패스 자기 비판, 그리고 2단계 자기 비판 방법의 세 가지 추론 방법에 대한 MATH 및 Minerva-Math 벤치마크 결과를 0.0, 0.1, 0.3, 0.6의 네 가지 온도에서 보여줍니다. 이 표는 자기 비판 방법이 직접 추론에 비해 성능이 떨어지고, 온도가 높아질수록 성능이 저하되는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Performance comparison of different inference methods across various temperature settings.
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