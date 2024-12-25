---
title: "NILE: Internal Consistency Alignment in Large Language Models"
summary: "NILE 프레임워크는 LLM의 내부 지식과 IFT 데이터셋의 세계 지식 간 일관성을 높여 LLM 성능을 최대 68.5%까지 향상시킵니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Chinese University of Hong Kong",]
showSummary: true
date: 2024-12-21
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.16686 {{< /keyword >}}
{{< keyword icon="writer" >}} Minda Hu et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-24 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.16686" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.16686" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/nile-internal-consistency-alignment-in-large" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)의 성능 향상을 위해 지시 미세 조정(IFT)이 널리 활용되고 있지만, 기존 IFT 데이터셋은 LLM의 사전 훈련 과정에서 학습된 내부 지식과 불일치하는 경우가 많아 IFT의 효과를 저해하는 문제가 있습니다.

본 논문에서는 이러한 문제를 해결하기 위해 NILE(iNternal consIstency aLignmEnt) 프레임워크를 제시합니다. NILE은 LLM의 내부 지식을 활용하여 IFT 데이터셋을 최적화하고, LLM의 내부 지식과 일관성이 높은 샘플만을 선택하는 새로운 방법을 제안합니다.  실험 결과, NILE은 다양한 평가 벤치마크에서 LLM의 성능을 상당히 향상시키는 것으로 나타났습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} NILE 프레임워크는 LLM의 내부 지식과 IFT 데이터셋 간의 일관성을 개선하여 LLM 성능을 향상시킵니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} NILE은 LLM의 내부 지식을 활용하여 IFT 데이터셋을 개선하고, 일관성이 낮은 샘플을 제거하는 새로운 방법을 제시합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 실험 결과, NILE을 사용하여 개선된 데이터셋으로 학습된 LLM은 다양한 평가 벤치마크에서 상당한 성능 향상을 보였습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대규모 언어 모델(LLM)의 지시 미세 조정(IFT) 데이터셋의 품질 향상**이라는 중요한 문제를 해결하는 데 기여합니다.  **LLM의 내부 지식과 IFT 데이터셋의 세계 지식 간의 일관성**을 강조하여 성능 향상을 이끌어낸 연구는 LLM 개발 및 응용 분야에 중요한 시사점을 제공합니다.  **데이터 일관성 관리**의 중요성을 부각함으로써, 향후 연구의 방향을 제시하고 LLM 성능 향상을 위한 새로운 가능성을 열어줍니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.16686/x1.png)

> 🔼 본 그림은 Instruction Fine-Tuning (IFT) 데이터셋에서 LLM의 내부 지식과 외부 지식을 보여줍니다.  IFT 데이터셋은 LLM이 사전 훈련 단계에서 학습한 내부 지식과 일치하지 않는 지식을 포함할 수 있으며, 이는 IFT의 효율성에 큰 영향을 미칩니다. 그림은 질문과 답변 예시를 통해, LLM이 질문에 답변하기 위해 사용하는 내부 지식과 외부 지식 간의 상호 작용을 시각적으로 보여줍니다.  LLM의 내부 지식은 사전 훈련 데이터에서 학습된 지식을, 외부 지식은 IFT 데이터셋에서 가져온 지식을 나타냅니다. 그림을 통해 IFT 데이터셋의 질 향상을 위한 NILE 프레임워크의 개념을 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Demonstration of LLM internal knowledge and world knowledge from IFT datasets.
> </details>





{{< table-caption >}}
| Method | Arena-Hard ↑ | Alpaca-Eval V2 ↑ | MTBench ↑ | BBH ↑ |
|---|---|---|---|---|
| Mistral-7b-v0.3 |  |  |  |  |
| Alpaca vanilla | 3.00 | 11.73 / 7.39 | 6.37 | 34.46 |
| Alpaca + SR | 4.20 | 11.50 / 6.52 | 6.28 | 38.40 |
| Alpaca + NILE | **6.20** | **15.39** / **9.70** | **6.56** | **38.52** |
| Orca vanilla | 5.30 | 12.84 / 9.54 | 5.34 | 46.37 |
| Orca + SR | 5.70 | 18.19 / 15.24 | 6.13 | 46.01 |
| Orca + NILE | **6.70** | **21.63** / **17.25** | **6.73** | **51.01** |
| Meta-Llama-3.1-8B |  |  |  |  |
| Alpaca vanilla | 2.10 | 7.58 / 5.53 | 6.31 | 58.64 |
| Alpaca + SR | 3.30 | 9.08 / 6.84 | 6.39 | 59.91 |
| Alpaca + NILE | **4.80** | **10.69** / **10.43** | **6.90** | **61.40** |
| Orca vanilla | 3.60 | 10.84 / 7.52 | 7.01 | 63.02 |
| Orca + SR | 4.20 | 12.36 / 10.46 | 7.18 | 63.77 |
| Orca + NILE | **6.00** | **13.70** / **12.11** | **7.48** | **64.05** |{{< /table-caption >}}

> 🔼 이 표는 본 논문의 3.1절 '내부 지식 추출(IKE)'에서 설명하는 내용과 관련이 있습니다.  표의 목적은 사전 훈련된 거대 언어 모델(LLM)의 내부 지식을 효과적으로 추출하는 방법을 보여주는 것입니다.  이를 위해,  원래의 지시어(instruction)와 입력(input) 데이터를 사용하여 LLM이 내부 지식을 생성하도록 유도하는 프롬프트를 보여줍니다.  즉,  주어진 지시어와 입력에 대한 LLM의 내부 지식을 얻기 위한 프롬프트의 예시를 제공하는 표입니다.  `instruction` 과 `input` 은 각각 지시어와 입력 데이터를 의미하고,  `ikd`는 LLM이 생성한 내부 지식을 의미합니다.  이는 본 논문에서 제안하는 NILE 프레임워크의 핵심 구성 요소 중 하나이며,  후속 단계인 KSR(지식 기반 샘플 수정)에서 수정된 응답을 생성하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Prompt for generating internal knowledge demonstration i⁢kid𝑖subscriptsuperscript𝑘𝑑𝑖ik^{d}_{i}italic_i italic_k start_POSTSUPERSCRIPT italic_d end_POSTSUPERSCRIPT start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT related to qidsubscriptsuperscript𝑞𝑑𝑖q^{d}_{i}italic_q start_POSTSUPERSCRIPT italic_d end_POSTSUPERSCRIPT start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT.
> </details>





### In-depth insights


#### LLM Internal Knowledge
LLM 내부 지식은 **사전 학습 단계에서 방대한 데이터를 통해 학습된 지식**을 의미합니다. 이는 단순히 단어와 문장의 통계적 패턴을 넘어, **세계에 대한 이해, 개념 간의 관계, 추론 능력** 등을 포함하는 복잡한 구조입니다.  본 논문에서 강조하는 것은 이러한 내부 지식과 **Instruction Fine-Tuning(IFT) 데이터셋의 지식 간의 일관성**입니다. IFT 데이터셋의 품질이 LLM 성능에 큰 영향을 미치는데, **LLM의 내부 지식과 불일치하는 정보**는 오히려 성능 저하를 야기할 수 있습니다. 따라서, **데이터셋의 질 향상**은 LLM의 잠재력을 최대한 발휘하는 데 필수적이며,  **내부 지식과의 일관성 확보**가 중요한 요소임을 시사합니다.  이는 단순히 데이터 양 증가만으로는 해결되지 않고, **LLM의 내부 지식을 명확히 이해하고, 이를 고려한 데이터셋 구성 및 필터링** 전략이 필요함을 의미합니다.

#### NILE Framework
NILE 프레임워크는 **LLM의 내부 지식과 IFT 데이터셋의 일관성**을 중시하여 IFT 데이터셋을 최적화하는 데 중점을 둡니다.  기존의 IFT 접근 방식이 데이터 양에만 초점을 맞춘 것과 달리, NILE은 **LLM의 사전 학습된 지식**을 활용하여 IFT 데이터셋의 답변을 수정하고, LLM의 내부 지식과의 일관성이 낮은 샘플을 제거합니다. 이를 통해 LLM의 잠재력을 극대화하고, 다양한 LLM 평가 데이터셋에서 성능을 향상시키는 것을 목표로 합니다. **IKE, KSR, ICF 세 단계**를 통해 이러한 목표를 달성하며, 각 단계는 LLM의 내부 지식을 추출, IFT 데이터셋 수정, 일관성 있는 샘플 필터링이라는 고유한 기능을 수행합니다.  **데이터 일관성 확보**를 통해 LLM 성능 향상에 기여하는 핵심 요소임을 보여줍니다.

#### Dataset Revision
데이터 재검토는 **LLM의 내부 지식과 일관성을 유지**하는 데 중점을 둔 중요한 과정입니다.  기존의 지식 기반과의 불일치는 IFT의 효율성을 저해할 수 있으므로, **LLM의 내부적 이해와 부합하는 데이터를 생성하고 선택**하는 것이 필수적입니다.  이를 위해서는 **LLM이 보유한 지식을 활용하여 데이터를 수정하고, 일관성이 낮은 샘플은 제거**해야 합니다. 이러한 과정은 **LLM의 잠재력을 최대한 활용**하는 데 도움이 되며, 다양한 평가 데이터셋에서 성능 향상을 가져옵니다.  **데이터의 질적 향상**에 초점을 맞추어, 양적 확장보다는 **LLM의 내부 지식과의 일관성**을 확보하는 것이 중요합니다.  결론적으로, **데이터 재검토는 LLM의 성능 향상에 필수적인 요소**로,  **내부 지식과의 일관성**을 고려한 신중한 접근 방식이 필요합니다.

#### Future Work
본 논문의 "미래 연구" 부분에서는 **NILE 프레임워크의 확장성 및 개선**에 대한 중요한 방향을 제시합니다.  **OpenOrca 데이터셋 전체 활용**을 통한 더욱 견고한 성능 검증과, **반복적인 지시 개선 기능** 추가를 통한 NILE의 적응력 향상이 주요 과제입니다.  특히, 제한된 계산 자원으로 인해 OpenOrca의 일부만 사용했다는 점을 감안할 때, 전체 데이터셋을 활용한 실험은 NILE의 일반화 성능을 더욱 명확히 보여줄 것입니다. 또한, 현재 구현된 단일 개선 단계를 넘어, **반복적인 지시 개선 기능**을 구현하여 NILE이 더욱 다양하고 복잡한 지시에도 효과적으로 대응할 수 있도록 하는 연구가 필요합니다.  이러한 확장과 개선은 NILE의 실용성과 활용 범위를 크게 넓히는 데 기여할 것이며, **LLM의 지시어 따르기 성능 향상**이라는 궁극적인 목표 달성에 중요한 역할을 할 것으로 기대됩니다.  **윤리적 측면**에서도, 편향된 데이터 사용 방지 및 지속적인 모니터링을 통해 공정하고 안전한 AI 개발에 기여하는 방향으로 연구가 진행되어야 할 것입니다.

#### NILE Limitations
NILE의 제한점은 주로 **데이터 규모와 계산 자원의 제약**에 있습니다.  현재 NILE은 OpenOrca 데이터셋의 5%만을 사용하는데, 이는 전체 데이터셋을 활용하지 못함으로써 성능 향상의 여지를 남깁니다.  **계산 비용과 시간** 또한 제한적인 요소이며, 더 큰 규모의 데이터셋을 활용하려면 상당한 자원이 필요합니다.  또한, NILE은 현재 **단일 수정 단계**만을 사용하지만, 반복적인 개선을 통해 성능을 더욱 향상시킬 수 있는 가능성이 있습니다.  **추가적인 연구**를 통해 이러한 제한점을 해결하고 NILE의 적용 범위를 확장하여 다양한 지침 따르기 과제에 대한 성능을 더욱 향상시킬 수 있을 것입니다. 특히,  **윤리적인 측면**에서도 고려해야 할 부분이 있는데,  향후 연구에서는 불공정하거나 편향된 데이터를 걸러내는 메커니즘을 추가하는 것이 필요할 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.16686/x2.png)

> 🔼 그림 2는 본 논문에서 제안하는 NILE 프레임워크의 개요를 보여줍니다.  NILE은 사전 훈련된 거대 언어 모델(LLM)의 내부 지식과 지시 조정 데이터셋 간의 일관성을 높이기 위한 세 가지 주요 단계로 구성됩니다. 첫째, 내부 지식 추출(IKE) 단계에서는 사전 훈련된 LLM에서 지시어에 해당하는 내부 지식을 추출합니다. 둘째, 지식 기반 샘플 수정(KSR) 단계에서는 추출된 내부 지식을 사용하여 기존 데이터셋 샘플을 수정합니다. 마지막으로, 내부 일관성 필터링(ICF) 단계에서는 LLM의 내부 지식과의 일관성을 기준으로 훈련 샘플을 걸러냅니다. 이러한 세 단계를 통해 NILE은 LLM의 성능을 향상시키는 데 기여하는 최적화된 지시 조정 데이터셋을 생성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Overview of our NILE framework.
> </details>



![](https://arxiv.org/html/2412.16686/x3.png)

> 🔼 그림 3은 Mistral 모델에 대한 Alpaca 데이터셋에서 문장 임베딩 유사도 점수의 분포를 보여줍니다.  x축은 문장 임베딩 유사도 점수를 나타내고, y축은 각 점수에 해당하는 문장의 개수를 나타냅니다. 이 그래프는 Vanilla, KSR, SR 세 가지 방법을 사용하여 생성된 문장 임베딩의 유사도 점수 분포를 비교 분석하여, NILE 프레임워크의 KSR 단계가 문장 임베딩 유사도를 얼마나 향상시키는지 보여줍니다. Vanilla는 원본 데이터셋을 사용한 결과이고, KSR은 NILE 프레임워크의 지식 기반 샘플 수정 단계를 거친 결과이며, SR은 지식 기반 없이 샘플을 수정한 결과입니다. 그림을 통해 KSR이 Vanilla보다 더 높은 유사도 점수 분포를 보여주는 것을 확인할 수 있으며,  이는 KSR이 모델의 내부 지식과 데이터셋 간의 일관성을 향상시키는 데 효과적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Distribution plot of sentence embedding similarity score in Alpaca dataset for Mistral model.
> </details>



![](https://arxiv.org/html/2412.16686/x4.png)

> 🔼 그림 4는 서로 다른 대규모 언어 모델(LLM)과 지시 미세 조정(IFT) 데이터 세트에서 문장 임베딩 유사도의 분포를 보여줍니다.  각 그래프는 특정 LLM과 IFT 데이터 세트 조합에 대한 문장 임베딩 유사도의 히스토그램을 나타냅니다.  세 가지 다른 방법(Vanilla, KSR, SR)을 사용하여 생성된 문장 임베딩의 유사도 분포를 비교하여, 각 방법이 문장 임베딩 유사도에 미치는 영향을 시각적으로 보여줍니다. Vanilla는 원본 데이터셋, KSR은 내부 지식을 활용한 수정된 데이터셋, SR은 내부 지식 없이 수정된 데이터셋을 나타냅니다. 이를 통해 NILE 프레임워크의 KSR 모듈이 문장 임베딩 유사도 향상에 미치는 영향을 효과적으로 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Distribution of sentence embedding similarity across different LLMs and IFT datasets.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | Arena-Hard ↑ | Alpaca-Eval V2 ↑ | MTBench ↑ | BBH ↑ |
|---|---|---|---|---|
| Alpaca + KSR (Mistral) | 4.00 | 9.14 / 7.29 | 6.64 | 57.67 |
| Alpaca + KSR (Llama) | **4.80** | **10.75** / **9.38** | **6.67** | **60.73** |
| Orca + KSR (Mistral) | 5.10 | 12.50 / 10.25 | 5.93 | 22.32 |
| Orca + KSR (Llama) | **5.20** | **13.67** / **11.21** | **7.51** | **64.03** |{{< /table-caption >}}
> 🔼 이 표는 3.1절 내부 지식 추출(IKE) 단계에서 사용되는 프롬프트를 보여줍니다.  프롬프트는 사전 훈련된 LLM의 내부 지식을 추출하기 위해 소수의 몇몇 예시와 함께 원본 지침을 사용하여 LLM을 유도하는 방식입니다.  표에는 프롬프트의 구조와 내부 지식 추출에 필요한 정보, 즉 지침과 관련된 지식이 포함되어 있습니다.  A.1.3절에 더 자세한 설명이 나와 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Prompt for knowledge extraction. Sample few-shot demonstration prompt is listed in A.1.3.
> </details>

{{< table-caption >}}
| Method | Arena-Hard ↑ | Alpaca-Eval V2 ↑ | MTBench ↑ | BBH ↑ |
|---|---|---|---|---|
| Alpaca + KSR w. FD | **4.80** | 10.75 / 9.38 | 6.67 | **60.73** |
| Alpaca + KSR w. FS 1 IKE | **4.50** | **11.20** / **9.75** | **6.72** | 59.25 |
| Alpaca + KSR w. FS 2 IKE | **4.50** | **10.82** / **10.56** | **6.76** | **61.40** |
| Orca + KSR w. FD | **5.20** | **13.67** / **11.21** | **7.51** | **64.03** |
| Orca + KSR w. FS 1 IKE | 4.90 | 12.46 / 10.99 | 7.40 | 63.89 |
| Orca + KSR w. FS 2 IKE | **5.50** | **13.00** / **11.50** | **7.43** | **64.29** |{{< /table-caption >}}
> 🔼 이 표는 지식 기반 샘플 수정(KSR) 단계에서 사용되는 프롬프트를 보여줍니다.  원래 답변(a°)과 관련된 지식(ik)을 활용하여 개선된 답변(aik)을 생성하기 위한 지침을 담고 있습니다.  즉, 기존의 Instruction Fine-Tuning(IFT) 데이터셋의 응답을, 사전 훈련된 대규모 언어 모델(LLM)의 내부 지식과 일치하도록 수정하는 방법을 제시합니다.  프롬프트는 Instruction, Input, 그리고 Related Knowledge 세 부분으로 구성되어 있으며, 모델이 개선된 응답을 생성하는 데 필요한 모든 정보를 포함합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Prompt for Knowledge-aware Sample Revision.
> </details>

{{< table-caption >}}
| Method | Arena-Hard ↑ | Alpaca-Eval V2 ↑ | MTBench ↑ | BBH ↑ |
|---|---|---|---|---|
| Alpaca + NILE wo. ICF | 4.50 | 10.82 / 10.56 | 6.76 | 61.40 |
| Alpaca + NILE w. ICF (low) | 4.80 | 10.69 / 10.43 | 6.90 | 61.40 |
| Alpaca + NILE w. ICF (high) | 4.50 | 9.92 / 9.70 | 6.79 | 61.71 |
| Orca + NILE wo. ICF | 5.50 | 13.00 / 11.50 | 7.43 | 64.29 |
| Orca + NILE w. ICF (low) | 6.00 | 13.70 / 12.11 | 7.48 | 64.05 |
| Orca + NILE w. ICF (high) | 4.80 | 13.19 / 11.49 | 7.30 | 63.95 |{{< /table-caption >}}
> 🔼 표 4는 논문에서 제시된 Alpaca 및 OpenOrca 데이터셋을 사용한 주요 실험 결과를 보여줍니다.  각 지표(Arena-Hard, Alpaca-Eval V2, MTBench, BBH)에 대해 MISTRAL-7B-v0.3과 Meta-Llama-3.1-8B 두 가지 모델의 성능을 Vanilla(기본 설정), SR(Sample Revision), NILE(제안된 방법) 세 가지 방법으로 비교합니다.  가장 높은 값은 굵게 표시하고, 두 번째로 높은 값은 밑줄을 쳐서 각 데이터셋과 모델에서 각 방법의 상대적 성능을 명확하게 나타냅니다.  이 표는 NILE 프레임워크의 효과를 객관적으로 평가하는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Main experiment results on Alpaca and OpenOrca datasets. The highest values are bolded, and the second highest is underlined.
> </details>

{{< table-caption >}}
| Method | Arena-Hard ↑ | Alpaca-Eval V2 ↑ | MTBench ↑ | BBH ↑ |
|---|---|---|---|---|
| Orca + NILE w. Contriver | 4.70 | 14.63 / 12.17 | 7.29 | 64.00 |
| Orca + NILE w. BM25 | 5.50 | 13.00 / 11.50 | 7.43 | 64.29 |{{< /table-caption >}}
> 🔼 이 표는 Llama-3 모델을 미세 조정할 때 서로 다른 대규모 언어 모델(LLM)의 내부 지식을 사용하여 지식 기반 샘플 수정(KSR)의 효과를 보여줍니다.  다양한 평가 지표(Arena-Hard, Alpaca-Eval V2, MTBench, BBH)에서의 성능 향상을 보여주며, 각 지표에서 가장 높은 값은 굵은 글씨체로 표시되어 있습니다. 이를 통해 특정 LLM의 내부 지식을 활용하는 것이 미세 조정 성능에 미치는 영향을 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Effects of KSR in Llama-3 finetuning with internal knowledge from different LLMs. The highest values are bolded.
> </details>

{{< table-caption >}}
| Instruction | Response | Internal Knowledge |
|---|---|---|
| *Compose a new email subject line for a following email.* <br> **Input:** The email body contains a request to renew a subscription. | **Vanilla:** "Reminder: Renew Your Subscription Today!" <br> **Revised:** "<span class="ltx_text" id="A1.T13.1.2.1.2.1.1.3" style="color:#B30000;">Action Required:</span> Time to Renew Your Subscription!" | Email subject line: The subject line of an email is the first thing a recipient sees and can determine whether they open the email or not. It should be clear, concise, and relevant to the email content.* Subscription renewal: A subscription renewal is a request to continue receiving a service or product after the initial subscription period has ended. It is important to provide clear instructions and information about the renewal process.* Clear instructions: Providing clear instructions in the email body can help ensure that the recipient understands the request and knows what to do next. It is important to use simple language and avoid technical jargon.* Information about renewal process: Including information about the renewal process, such as the cost, payment options, and deadlines, can help the recipient make an informed decision and take the necessary steps to renew their subscription.<span class="ltx_text" id="A1.T13.1.2.1.3.1.1.1" style="color:#B30000;">* Call-to-action: Including a clear call-to-action in the email body can help ensure that the recipient knows what to do next and takes the desired action. It is important to use a strong and direct call-to-action that is easy to understand and takes the recipient to the next step.</span> |
| *Write a sentence containing a hyperbolic metaphor.* <br> **Input:** None | **Vanilla**: He was so hungry, he could eat an entire elephant. <br> **Revised**: He was so ravenous, <span class="ltx_text" id="A1.T13.1.3.2.2.1.1.3" style="color:#B30000;">he could devour a mountain of hamburgers as tall as Everest.</span> | Hyperbole is a figure of speech that uses exaggeration for emphasis or effect.<span class="ltx_text" id="A1.T13.1.3.2.3.1.1.1" style="color:#B30000;">* Hyperbolic metaphors are metaphors that use hyperbole to create a vivid and dramatic image.</span>* For example, "The crowd was so large that it stretched from one end of the stadium to the other." * This metaphor uses hyperbole to create a dramatic image of the crowd´s size.* Hyperbolic metaphors can be used to create a strong emotional response or to make a point more effectively.<span class="ltx_text" id="A1.T13.1.3.2.3.1.1.2" style="color:#B30000;">* They can also be used to add humor or to create a sense of exaggeration or absurdity.</span> |
| *Create a 3-5 sentence definition for the term "data science".* <br> **Input:** None | **Vanilla:** Data science is an interdisciplinary field that combines techniques from statistics, mathematics, computer science, and information science to extract insights and knowledge from data. This field deals with both structured and unstructured data, using algorithms, predictive models, and machine learning to make informed decisions. Data science has broad applications, from businesses and marketing to healthcare and scientific research, where it is used to answer questions, find patterns, and make strategic decisions. <br> **Revised:** Data science is an interdisciplinary field that uses methods from statistics, mathematics, computer science, and domain-specific knowledge to extract insights and information from both structured and unstructured data. It employs techniques such as machine learning, predictive modeling, and data mining to analyze data sets, identify patterns, and make predictions. <span class="ltx_text" id="A1.T13.1.4.3.2.1.1.3" style="color:#B30000;">The ultimate goal of data science is to help organizations make informed decisions, optimize processes, and solve complex problems by leveraging vast amounts of data. This field is critical across various industries, including healthcare, finance, and technology, where data-driven insights are essential for strategic decision-making and operational improvements</span>. | Data science is an interdisciplinary field that combines techniques from statistics, computer science, and domain knowledge to extract insights from data.* It involves the use of advanced analytics and machine learning algorithms to analyze large datasets and identify patterns, trends, and correlations.* Data scientists use various tools and techniques such as data mining, predictive modeling, and natural language processing to uncover insights and make predictions about future events.<span class="ltx_text" id="A1.T13.1.4.3.3.1.1.1" style="color:#B30000;">* The goal of data science is to use data to solve complex problems, make better decisions, and drive business value.* Data science has become increasingly important in recent years due to the rapid growth of data and the need for organizations to make sense of it.* Data scientists play a critical role in many industries, including healthcare, finance, retail, and technology, where they help organizations gain insights from data to improve operations, optimize processes, and make better decisions.</span> |{{< /table-caption >}}
> 🔼 표 6은 Llama-3 모델에서 IKE(Internal Knowledge Extraction) 단계에서 사용된 몇몇 샷(few-shot)의 수가 모델 성능에 미치는 영향을 보여줍니다.  세 가지 변형이 비교됩니다: 1) 고정된 2-샷 데모를 사용하는 W. FD, 2) BM25를 사용하여 가장 유사한 상위 1개의 샘플을 검색하는 W. FS 1 IKE, 3) BM25를 사용하여 가장 유사한 상위 2개의 샘플을 검색하는 W. FS 2 IKE. 각 변형에 대한 Arena-Hard, Alpaca-Eval V2, MTBench, BBH 지표가 제시되며, 가장 높은 값은 굵게 표시되고 두 번째로 높은 값은 밑줄이 그어져 있습니다. 이 표는 IKE에서 적절한 몇 샷 학습의 수를 결정하는 데 도움이 되는 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Effects of IKE with different fewshot numbers (FS) in Llama-3. The highest values are bolded, and the second highest is underlined.
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
{{< /gallery >}}