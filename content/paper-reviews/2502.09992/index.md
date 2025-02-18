---
title: "Large Language Diffusion Models"
summary: "LLaDA: 대규모 언어 확산 모델이 자기회귀 모델을 능가하다!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Ant Group",]
showSummary: true
date: 2025-02-14
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.09992 {{< /keyword >}}
{{< keyword icon="writer" >}} Shen Nie et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-17 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.09992" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.09992" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 대규모 언어 모델(LLM)은 주로 자기회귀 모델(ARM)에 기반을 두고 있습니다.  ARM은 텍스트를 순차적으로 생성하는 방식으로, 확장성과 역추론 능력에 한계가 있습니다. 이러한 한계점을 극복하기 위해, 본 논문에서는 새로운 **확산 모델 기반의 LLM인 LLaDA**를 제안합니다.



LLaDA는 **데이터 마스킹 및 역방향 예측** 과정을 통해 확률적 추론을 수행합니다.  **다양한 벤치마크 실험**을 통해 LLaDA는 **기존 ARM 기반 모델을 능가하는 확장성과 성능**을 보였습니다. 특히, 문맥 학습 및 지시 따르기 능력에서 우수한 성능을 보였으며, 역추론 과제에서도 기존 모델보다 뛰어난 결과를 보였습니다.  본 연구는 **LLM 연구에 새로운 패러다임**을 제시하며, **ARM에 대한 의존도를 낮추고 LLM의 잠재력을 더욱 확장**할 수 있는 가능성을 제시합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} LLaDA는 **기존 자기회귀 모델 기반 LLM의 한계를 극복**하는 **새로운 확산 모델 기반 LLM**입니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} LLaDA는 **뛰어난 확장성과 성능**을 보이며, **다양한 벤치마크에서 우수한 결과**를 달성했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 본 연구는 **LLM 연구의 새로운 패러다임**을 제시하며, 향후 **LLM 개발 및 응용 분야 확장**에 기여할 것으로 기대됩니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대규모 언어 모델(LLM)의 기존 패러다임을 뛰어넘는 새로운 접근 방식**을 제시하여, 연구자들에게 **LLM의 확장성과 성능 향상을 위한 새로운 가능성**을 제시합니다.  **확산 모델 기반의 LLM인 LLaDA**의 우수한 성능과 확장성은 기존의 자기회귀 모델 기반의 LLM과 비교하여 **새로운 연구 방향**을 제시하며, 향후 **LLM 연구의 발전에 중요한 영향**을 미칠 것으로 예상됩니다. 특히, **비자기회귀적 특성**은 기존 모델의 한계를 극복하고 **새로운 기능**을 제공하여, 다양한 응용 분야에서의 LLM 활용 가능성을 더욱 확대할 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.09992/x1.png)

> 🔼 그림 1은 LLaDA의 제로샷 및 퓨샷 성능을 보여주는 벤치마크 결과를 나타냅니다.  연구진은 LLaDA를 80억 개의 파라미터로 처음부터 학습시켜 강력한 대규모 언어 모델들과 경쟁력 있는 성능을 달성했습니다. 이는 자체적으로 구축한 기준 모델보다 우수한 성능을 보여주는 것입니다.  LLaDA는 문맥 내 학습 및 지시 따르기 능력에서도 뛰어난 성능을 보였습니다.  특히 역순 시 쓰기 과제에서 GPT-40을 능가하는 결과를 보여주었습니다. 이러한 결과는 LLaDA가 기존의 자기 회귀 모델에 대한 강력한 대안이 될 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Zero/Few-Shot Benchmarks. We scale LLaDA to an unprecedented size of 8B parameters from scratch, achieving competitive performance with strong LLMs (Dubey et al., 2024).
> </details>





{{< table-caption >}}
|           | Forward | Reversal |
|-----------|---------|----------|
| GPT-4o (2024-08-06) | **82.7** | 34.3     |
| Qwen2.5 7B Instruct | 75.9    | 38.0     |
| LLaDA 8B Instruct   | 48.8    | **42.4**   |{{< /table-caption >}}

> 🔼 본 표는 사전 훈련된 대규모 언어 모델들의 벤치마크 결과를 보여줍니다. LLaDA 8B Base, LLaMA2 7B Base, LLaMA3 8B Base 세 모델은 동일한 프로토콜(Appendix B.5 참조)을 사용하여 평가되었음을 나타내는 * 표시가 되어 있습니다. †와 ¶로 표시된 결과는 각각 Chu et al. (2024), Yang et al. (2024), Bi et al. (2024) 논문에서 가져온 것입니다. 괄호 안의 숫자는 평가에 사용된 샷(shot) 수를 나타내며, '-'는 알 수 없는 데이터를 의미합니다.  표에는 일반적인 작업, 수학 및 과학, 코드, 중국어 등 다양한 작업에 대한 성능이 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Benchmark Results of Pre-trained LLMs. ∗ indicates that LLaDA 8B Base, LLaMA2 7B Base, and LLaMA3 8B Base are evaluated under the same protocol, detailed in Appendix B.5. Results indicated by † and ¶ are sourced from Chu et al. (2024); Yang et al. (2024) and Bi et al. (2024) respectively. The numbers in parentheses represent the number of shots used for evaluation. “-” indicates unknown data.
> </details>





### In-depth insights


#### LLaDA: Diffusion for LLMs
LLaDA는 **확산 모델을 사용하여 대규모 언어 모델(LLM)의 한계를 극복**하려는 시도입니다. 기존의 자기회귀 모델(ARM) 기반 LLM과 달리, LLaDA는 데이터의 확률적 분포를 학습하여 **더욱 강력한 확장성과 뛰어난 성능**을 보여줍니다. 특히 컨텍스트 학습 및 지시 따르기 능력에서 우수한 결과를 나타내며, 역추론 과제에서도 기존 모델들을 능가하는 성능을 보입니다. 이는 LLaDA가 **자기회귀적 특성에 의존하지 않고 생성 모델링의 원리를 활용**하여 LLM의 핵심 기능을 구현할 수 있음을 시사합니다. **확산 모델의 이점**, 즉 양방향 의존성 고려 및 역추론 문제 해결 능력을 통해 LLaDA는 LLM의 발전에 새로운 가능성을 제시합니다. 하지만, 아직 **확장성 및 성능 면에서 개선의 여지**가 있으며,  **다양한 과제에 대한 추가적인 연구**가 필요합니다.  LLaDA의 성공은 생성 모델링의 잠재력을 보여주는 동시에, 향후 LLM 연구 방향에 대한 중요한 시사점을 제공합니다.

#### Masked Diffusion Modeling
마스크 확산 모델링은 **자기 회귀적 접근 방식의 한계를 극복하기 위해 제안된 생성 모델링의 새로운 패러다임**입니다.  기존의 자기 회귀 모델들은 토큰을 순차적으로 예측하는 방식으로 인해 확장성과 계산 비용 면에서 어려움을 겪습니다.  반면 마스크 확산 모델링은 **데이터를 점진적으로 마스킹하는 순방향 과정과 마스킹된 토큰을 예측하여 원본 데이터를 복원하는 역방향 과정**을 통해 확률적 추론을 수행합니다.  이러한 접근 방식은 **토큰 간의 상호 의존성을 포착**하고 **양방향 정보 처리를 가능**하게 하여 자기 회귀 모델의 단점을 극복합니다.  **매개변수 효율성**이 높고, **다양한 작업에서 강력한 확장성과 성능**을 보여주는 등 여러 장점을 가지고 있지만,  **모델 훈련 및 추론 과정의 복잡성**이라는 과제도 있습니다.  향후 연구는 이러한 과제를 해결하고 마스크 확산 모델링의 잠재력을 더욱 발휘하는 데 집중되어야 합니다.

#### Scalability and Efficiency
본 논문에서 제시된 확산 모델의 확장성 및 효율성에 대한 심층적인 논의가 필요합니다. **매개변수의 규모를 늘리는 것의 효과**와 그에 따른 성능 향상 및 계산 비용 증가 사이의 균형점을 찾는 것이 중요합니다. **단순히 매개변수를 증가시키는 것만으로는 효율성이 보장되지 않으므로**, 모델 아키텍처 최적화, 훈련 전략 개선, 그리고 추론 과정의 효율화 등 다양한 측면에서의 고려가 필요합니다.  **자원 제약 조건 하에서 최대 성능을 달성하기 위한 전략**에 대한 논의를 통해 실질적인 적용 가능성을 높일 수 있습니다.  특히, **다양한 하드웨어 플랫폼에서의 성능 비교** 분석을 통해  확산 모델의 실제적인 효율성을 평가할 수 있습니다.  또한, 기존의 자기 회귀 모델과의 비교 분석을 통해 확산 모델의 경쟁력을 명확히 하는 것이 중요합니다. **확장성과 효율성은 상호 보완적인 관계**이며, 이 둘의 균형을 잘 맞춰야 실제 응용 분야에서 성공적으로 확산 모델을 적용할 수 있습니다.

#### Instruction Following
논문에서 "Instruction Following"이라는 제목 아래 제시된 내용은 **대규모 언어 모델(LLM)**이 지시사항을 얼마나 잘 따르는지를 평가하는 핵심 지표임을 보여줍니다.  이는 단순히 명령어를 이해하는 수준을 넘어, **복잡하고 다층적인 지시를 수행하는 능력**까지 포함합니다.  본 논문은 LLaDA 모델이 지시 따르기 능력에서 기존의 자가 생성적 모델보다 뛰어난 성능을 보임을 강조하며, 이는 **새로운 모델 설계** 덕분이라고 주장합니다.  **다중 회전 대화**와 같은 복잡한 과제에서도 LLaDA가 뛰어난 성과를 보였다는 점은 주목할 만합니다.  이는 LLaDA 모델의 **강력한 확장성**과 **상호 작용 능력**을 시사하며, 기존 LLM의 한계를 뛰어넘는 새로운 가능성을 제시합니다.  **역추론(reversal reasoning)** 능력 또한 평가되었는데, 이는 LLaDA가 순차적 처리 방식의 한계를 넘어서 **양방향적 사고** 능력을 갖추었음을 시사합니다.  이는 향후 LLM의 발전 방향에 대한 중요한 시사점을 제공합니다.

#### Future Research
본 논문은 대규모 언어 확산 모델(LLaDA)의 잠재력을 보여주는 중요한 첫걸음이지만, **여전히 개선의 여지가 많다**는 점을 인지해야 합니다. **향후 연구는 모델의 확장성을 높이고, 계산 효율성을 개선하며, 다양한 하류 작업에서의 성능을 향상시키는 데 초점을 맞춰야 합니다.** 특히, **강화 학습(RL)을 통한 정렬 과정**은 LLaDA의 지시 따르기 능력과 안전성을 크게 향상시킬 수 있을 것입니다.  또한, **다양한 모달리티 데이터를 통합**하여 LLaDA의 능력을 더욱 확장하는 연구도 중요합니다.  **역추론 능력 향상을 위한 연구**도 필요하며, 이는 텍스트 데이터의 순차적 처리 방식의 한계를 극복하는 데 도움이 될 것입니다.  더불어, **모델의 편향성을 완화하고, 안전성을 강화하는 연구**는 사회적 책임을 다하는 AI 개발에 필수적입니다.  **보다 효율적이고 확장 가능한 훈련 및 추론 전략** 또한 탐구되어야 할 중요한 분야입니다.  마지막으로, **LLaDA와 다른 종류의 언어 모델과의 비교 연구**를 통해 강점과 약점을 분석하고 상호 보완적인 방향을 모색하는 것이 중요합니다.  이러한 노력들을 통해 LLaDA는 더욱 강력하고 유용한 언어 모델로 발전할 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.09992/x2.png)

> 🔼 그림 2는 LLaDA의 개념적 개요를 보여줍니다. (a) 사전 훈련 단계에서는 0과 1 사이의 균일한 확률 분포(U[0,1])를 따르는 임의의 비율 t로 모든 토큰에 독립적으로 마스크를 적용하여 텍스트를 훈련시킵니다. (b) SFT(Supervised Fine-Tuning) 단계에서는 응답 토큰에만 마스크가 적용될 수 있습니다. (c) 샘플링 단계에서는 LLaDA가 t=1(완전히 마스크 처리됨)에서 t=0(마스크 처리되지 않음)으로 확산 과정을 시뮬레이션하고, 유연한 마스크 재적용 전략을 사용하여 각 단계에서 모든 마스크를 동시에 예측합니다. 이 그림은 LLaDA의 사전 훈련, SFT 및 샘플링 과정을 시각적으로 보여주어 LLaDA의 작동 원리를 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: A Conceptual Overview of LLaDA. (a) Pre-training. LLaDA is trained on text with random masks applied independently to all tokens at the same ratio t∼U⁢[0,1]similar-to𝑡𝑈01t\sim U[0,1]italic_t ∼ italic_U [ 0 , 1 ]. (b) SFT. Only response tokens are possibly masked. (c) Sampling. LLaDA simulates a diffusion process from t=1𝑡1t=1italic_t = 1 (fully masked) to t=0𝑡0t=0italic_t = 0 (unmasked), predicting all masks simultaneously at each step with flexible remask strategies.
> </details>



![](https://arxiv.org/html/2502.09992/x3.png)

> 🔼 그림 8은 LLaDA의 반자동 회귀적 샘플링 과정을 개념적으로 보여줍니다. 이 그림은 입력 프롬프트가 주어졌을 때, LLaDA가 어떻게 여러 블록으로 나누어 샘플링을 진행하고 각 블록 내에서 마스크 토큰을 예측하는지 시각적으로 설명합니다. 각 블록은 왼쪽에서 오른쪽으로 순차적으로 생성되며, 각 블록 내에서는 마스크 토큰의 예측 확률에 따라 마스크를 재조정하는 전략이 사용됩니다. 그림을 통해 LLaDA의 샘플링 메커니즘을 보다 명확하게 이해할 수 있습니다.  LLaDA는 이러한 전략을 통해 양방향 의존성을 고려하고, 단어 간의 관계를 더욱 효과적으로 학습할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: A Conceptual Overview of the Semi-autoregressive Sampling.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Sampling Process |  |
|---|---| 
| User | Lily can run 12 kilometers per hour for 4 hours. After that, she runs 6 kilometers per hour. How many kilometers can she run in 8 hours? |
| LLaDA | ![https://arxiv.org/html/2502.09992/extracted/6203716/imgs/visualization/diff_math.png](https://arxiv.org/html/2502.09992/extracted/6203716/imgs/visualization/diff_math.png) |
| Multi-round Dialogue Case |  |
| User | Could you please share with me what the initial two lines of the renowned poem ‘The Road Not Taken’? |
| LLaDA | Certainly! The initial two lines of the renowned poem “The Road Not Taken” by Robert Frost are: “Two roads diverged in a yellow wood, And sorry I could not travel both.” These lines set the stage for the poem, introducing the idea of a speaker facing a choice between two paths. |
| User | Please help me translate into Chinese. |
| LLaDA | Sure! The first two lines of “The Road Not Taken” by Robert Frost can be translated into Chinese as: {CJK}UTF8gbsn“两条路分岔在黄色的树林中，遗憾我不能同时走” |
| User | Please translate into German. |
| LLaDA | Sure! The first two lines of “The Road Not Taken” by Robert Frost can be translated into German as: “Zwei Wege trennten sich im gelben Wald, und leider konnte ich nicht beide tun.” |
| User | Please also write a poem about life choices. I require 5 sentences, and the first word of each sentence starts with C as the first letter. |
| LLaDA | Certainly! Here’s a poem about life choices, with each sentence starting with the letter “C”: Choices cascade through life’s journey, Creating connections with each decision, Careful consideration leads to better paths, Courageous choices shape our destiny, Choosing wisely guides us through the years. |{{< /table-caption >}}
> 🔼 표 2는 사후 학습된 대규모 언어 모델들의 벤치마크 결과를 보여줍니다. LLaDA는 지도 학습 미세 조정(SFT)만 사용한 반면, 다른 모델들은 강화 학습(RL)을 추가로 사용했습니다. 별표(*)는 LLaDA 8B Instruct, LLaMA2 7B Instruct, LLaMA3 8B Instruct가 부록 B.5에 자세히 설명된 동일한 프로토콜에 따라 평가되었음을 나타냅니다. †와 ¶는 각각 Yang et al.(2024)과 Bi et al.(2024)의 결과임을 나타냅니다. 괄호 안의 숫자는 문맥 학습에 사용된 샷의 수를 나타내며, '-'는 알 수 없는 데이터를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Benchmark Results of Post-trained LLMs. LLaDA only employs an SFT procedure while other models have extra reinforcement learning (RL) alignment. ∗ indicates that LLaDA 8B Instruct, LLaMA2 7B Instruct, and LLaMA3 8B Instruct are evaluated under the same protocol, detailed in Appendix B.5. Results indicated by † and ¶ are sourced from Yang et al. (2024) and Bi et al. (2024) respectively. The numbers in parentheses represent the number of shots used for in-context learning. “-” indicates unknown data.
> </details>

{{< table-caption >}}
| | 4 steps | 5 steps | 6 steps |
|---|---|---|---|
| LLaMA3 8B Base | 38.0 | 35.0 | 34.0 |
| LLaDA 8B Base | **64.0** | **41.0** | **44.0** |{{< /table-caption >}}
> 🔼 표 3은 시 완성 작업에서 GPT-40, Qwen2.5 7B Instruct 및 LLaDA 8B Instruct 세 가지 모델의 성능을 비교한 표입니다. 각 모델의 순방향(Forward) 및 역방향(Reversal) 작업 정확도를 보여줍니다. 역방향 작업은 특히 모델의 능력을 평가하는 데 중요하며, LLaDA 8B Instruct가 GPT-40보다 뛰어난 성능을 보입니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Comparison in the Poem Completion Task.
> </details>

{{< table-caption >}}
| User | LLaDA |
|---|---| 
| What are the benefits of regular exercise for physical and mental health? | <img src="https://arxiv.org/html/2502.09992/extracted/6203716/imgs/visualization/sar.jpg" width="449" height="113"> |{{< /table-caption >}}
> 🔼 표 5는 LLaDA와 기준 ARM 모델의 아키텍처를 비교하여 보여줍니다.  1B 및 7B 파라미터 기준 ARM 모델과 1B 및 8B 파라미터 LLaDA 모델, 그리고 8B 파라미터 LLaMA3 모델의 계층 수, 모델 차원, 어텐션 헤드 수, 어휘 크기, FFN 차원, Key/Value 헤드 수, 그리고 총 파라미터 수를 비교하여 제시합니다. 이 표는 본 논문에서 사용된 다양한 크기의 언어 모델의 아키텍처 구성을 자세하게 보여주어 모델 성능 비교에 대한 이해를 돕습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Model Architecture. We provide the configurations of our 1B and 7B ARM baselines, as well as the 1B and 8B LLaDA and the 8B LLaMA3 models.
> </details>

{{< table-caption >}}
| User | LLaDA |
|---|---| 
| I want to have a pet, but I don’t know whether to get a cat or a dog. Do you have any suggestions? | https://arxiv.org/html/2502.09992/extracted/6203716/imgs/visualization/multi0.png |
| I’m very busy at work, so it seems like a cat would be a more suitable option. Do you have any suggestions for getting a cat? | https://arxiv.org/html/2502.09992/extracted/6203716/imgs/visualization/multi1.png |{{< /table-caption >}}
> 🔼 본 논문의 표 6은 리마스킹(Remasking) 전략에 대한 비교 실험 결과를 보여줍니다. GSM8K 정확도를 평가 지표로 사용하여, 무작위 리마스킹, 최저 신뢰도 리마스킹, 그리고 최저 신뢰도와 준자동 회귀 리마스킹을 비교합니다. 준자동 회귀 리마스킹 전략은 블록 단위로 왼쪽에서 오른쪽으로 생성하면서 각 블록 내에서 최저 신뢰도 리마스킹 전략을 적용하는 방식입니다. 이 표는 각 리마스킹 전략이 LLaDA 8B 기본 모델과 LLaDA 8B 지시 모델에 미치는 영향을 보여주는 실험 결과를 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Ablation on Remasking. We use GSM8K accuracy as the evaluation metric. The lowest-confidence & semi-autoregressive remasking strategy refers to generating each block from left to right, while applying the lowest-confidence remasking strategy within each block.
> </details>

{{< table-caption >}}
| Daily life |  |
|---|---| 
| User | What’s a piece of advice you’ve received that you’ve found helpful? |
| LLaDA | One helpful piece of advice I’ve received is to always be open to learning and growth. I’ve found that being willing to explore new ideas and experiences has helped me become more resilient and adaptable. By embracing a growth mindset, I’ve been able to identify opportunities for improvement and development, both personally and professionally. |
| Daily life |  |
| User | Please recommend me three famous movies |
| LLaDA | Certainly! Here are three famous movies that have achieved widespread popularity and critical acclaim: |
|  | 1. **The Shawshank Redemption** (1994) - Inspired by a novella and directed by Frank Darabont, this film tells the story of Andy Dufresne, a man convicted of murdering his wife, dealing with his harsh life in Shawshank Prison and forming an unlikely friendship with a fellow inmate. |
|  | 2. **The Godfather** (1972) - Directed by Francis Ford Coppola, this film is based on Mario Puzo’s novel of the same name. It follows the story of the Corleone family, particularly Michael Corleone, who rises to power and takes over the family’s criminal empire. |
|  | 3. **The Empire Strikes Back** (1980) - Directed by George Lucas, this film continues the story of a young Skywalker in the Star Wars saga. It follows Luke Skywalker as he helps the Rebel Alliance fight against the Galactic Empire and destroy the powerful weapon, the Death Star. |
|  | All of these films are celebrated for their cinematic achievements, powerful storytelling, and memorable characters. |
| Translation |  |
| User | Please help me translate into Chinese: ‘What is now proved was once only imagined’ |
| LLaDA | UTF8gbsn现在被证明的曾经只是想象 |
| Translation |  |
| User | Please help me translate into German: ‘What is now proved was once only imagined’ |
| LLaDA | Wer heute bestätigt ist, war einst nur immaginiert. |
| Math |  |
| User | Emma decides to run 4 sprints 5 times a week. She runs 75 meters each sprint. How many total meters does she run a week? |
| LLaDA | Emma runs 4 sprints each time, so she runs a total of 4 x 5 = 20 sprints a week. Each sprint is 75 meters long, so Emma runs a total of 20 x 75 = 1500 meters a week. The final result is 1500 |
| Code |  |
| User | I am writing python code, I have an array, please help me sort it from largest to smallest |
| LLaDA | Certainly! You can sort an array from the largest to smallest in Python using the ‘sort()’ method or the ‘sorted()‘ function. Here’s an example: |
|  | ### Using ‘sort()’ method: |
|  | my_array = [3, 1, 4, 1, 5, 2] |
|  | my_array.sort(reverse=True) |
|  | print(my_array) |{{< /table-caption >}}
> 🔼 표 7은 생성된 길이에 대한 ablation 연구 결과를 보여줍니다.  GSM8K 정확도를 평가 지표로 사용했으며, 샘플링 단계 수는 생성된 길이의 절반으로 설정했습니다.  다양한 길이(256, 512, 1024)에 대해 LLaDA 8B 기본 모델과 LLaDA 8B 지시 모델의 성능을 비교하여 생성 길이가 모델 성능에 미치는 영향을 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Ablation on Generated Length. We use the GSM8K accuracy as the evaluation metric and set the number of sampling steps to half of the generated length.
> </details>

{{< table-caption >}}
| Daily life |  |
|---|---| 
| User | How do I prepare for a job interview? |
| LLaDA | To prepare for a job interview, you should research the company and the job, practice common interview questions, and dress appropriately. |
| User | What are some common interview questions? |
| LLaDA | Some common interview questions include “Tell me about yourself” and “Why do you want to work for us”? |
| Daily life |  |
|---|---| 
| User | How do I start learning programming? |
| LLaDA | To learn programming, you can start by choosing a programming language that you are interested in. Some popular languages include Python, Java, and C++. |
| User | Which programming language should I learn first? |
| LLaDA | It depends on your interests and goals. Python is a great language for beginners for its simplicity and versatility. |
| User | How long does it take to learn Python? |
| LLaDA | It can take anywhere from a few weeks to several months to learn Python. |
| User | What are some good Python projects for beginners? |
| LLaDA | Some good Python projects for beginners include building a simple calculator, a game, and a web application. |
| Math |  |
|---|---| 
| User | Natalia sold clips to 48 of her friends in April, and then she sold half as many clips in May. How many clips did Natalia sell altogether in April and May? |
| LLaDA | Natalia sold clips to 48 friends in April. She sold half as many clips in May, so she sold 48/2 = 24 clips in May. Altogether, Natalia sold 48 + 24 = 72 clips in April and May. The final result is 72. |
| User | Natalia sold three times as many items in June as she did in May. How many clips did Natalia sell altogether in these three months? |
| LLaDA | Natalia sold clips to 48 friends in April. She sold half as many clips in May, so she sold 48/2 = 24 clips in May. Natalia sold three times as many items in June as she did in May, so she sold 24 * 3 = 72 clips in June. Altogether, Natalia sold 48 + 24 + 72 = 144 clips in these three months. The final result is 144. |{{< /table-caption >}}
> 🔼 표 8은 LLaDA 8B Instruct 모델의 추론 설정을 보여줍니다. 모든 데이터셋에 대해서 low-confidence remasking 전략을 적용합니다. 블록 길이가 답변 길이보다 짧으면 semi-autoregressive remasking 전략을 사용하고, 그렇지 않으면 적용하지 않습니다. MMLU와 HellaSwag의 경우 답변 길이가 짧은 이유는 하나의 토큰(A, B, C, 또는 D)과 두 개의 특수 종결 토큰(모델 응답 종료 및 문장 종료)만 생성해야 하기 때문입니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Inference Configuration for LLaDA 8B Instruct. We apply the low-confidence remasking strategy across all datasets. A block length smaller than the answer length indicates the use of the semi-autoregressive remasking strategy; otherwise, it is not applied. The shorter answer lengths for MMLU and HellaSwag result from their requirement to generate only a single token (i.e., A, B, C, or D) and two special end tokens (i.e., end of the model response and end of the sentence).
> </details>

{{< table-caption >}}
| Question | User | GPT-4o | LLaDA |
|---|---|---|---|
| _Question1_ |  |  |  |
|  | “但闻人语响”的上一句是什么？ | “但闻人语响”的上一句是“无可奈何花落去”,这两句出自唐代词人李清照的（武陵春，春晚: 无可奈何花落去，但闻人语响。这首词表达了作者在春天时节的孤独与感伤，借花落和人语声的描写，反映出词人内心的无亲与失落。 | “但闻人语响”的上一句是“空山不见人” |
| _Question2_ |  |  |  |
|  | “夜静春山空”的上一句是什么？ | “夜静春山空”的上一句是“空山新雨后”.这两句出自唐代诗人王维的（山居秋膜）:空山新雨后，夜静春山空。这首诗描绘了春天山中雨后的寂静与空灵，表现出自然的宁静与和谐美。 | “夜静春山空”的上一句是“人闲桂花落” |{{< /table-caption >}}
> 🔼 표 9는 iGSM 데이터셋에서 LLaDA 8B 기본 모델과 LLaMA 3 기본 모델의 성능을 비교한 표입니다.  샘플링 단계를 4, 5, 6단계로 변화시켜가며 각 모델의 정확도를 측정했습니다. iGSM 데이터셋은 GSM8K와 유사하지만 무한한 크기의 합성 데이터셋이며, 문제의 난이도를 제어하는 매개변수를 가지고 있습니다. 이 표는 LLaDA 모델의 확장성과 일반화 능력을 보여주는 실험 결과를 요약하고 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Comparison on iGSM Dataset.
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