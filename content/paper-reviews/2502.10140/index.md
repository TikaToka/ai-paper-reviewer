---
title: "Small Models, Big Impact: Efficient Corpus and Graph-Based Adaptation of Small Multilingual Language Models for Low-Resource Languages"
summary: "소규모 다국어 언어 모델을 저자원 언어에 효율적으로 적응시키는 새로운 방법 제시!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 German Research Center for Artificial Intelligence",]
showSummary: true
date: 2025-02-14
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.10140 {{< /keyword >}}
{{< keyword icon="writer" >}} Daniil Gurgurov et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-17 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.10140" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.10140" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

많은 언어, 특히 저자원 언어는 자연어 처리(NLP)에서 충분한 데이터 부족으로 어려움을 겪습니다. 최첨단 대규모 언어 모델(LLMs)조차도 이러한 언어에 대해서는 훌륭한 성능을 보이지 못합니다.  **본 연구는 이러한 문제를 해결하기 위해 소규모 다국어 언어 모델(mLMs)을 사용하고, 효율적인 어댑터 기반의 매개변수 조정 방법을 제시합니다.**

본 연구는 세 가지 어댑터 기반 아키텍처(순차적 병목, 가역적 병목, 저계수 적응)를 통해 mLMs를 저자원 언어에 적용합니다.  **구조화된 지식(ConceptNet)과 비구조화된 텍스트(GlotCC) 데이터를 통합하여 어댑터를 사전 훈련**하고, 다양한 하류 작업(예: 주제 분류, 감정 분석, 개체명 인식)에 대한 성능을 평가합니다. **실험 결과, 어댑터 기반 방법은 전체 미세 조정과 비교했을 때 더 적은 매개변수로 유사하거나 더 나은 성능을 보였습니다.**

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 소규모 다국어 언어 모델(mLMs)이 대규모 언어 모델(LLMs)보다 저자원 언어에 더 적합 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 어댑터 기반의 매개변수 효율적인 방법이 전체 미세 조정보다 우수한 성능 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 사전 학습 데이터 크기와 적응 데이터 크기가 성능에 미치는 영향 규명 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
이 논문은 **저자원 언어에 대한 효과적인 자연어 처리 모델 적응 방법**을 제시하여, **다양한 언어 모델 및 적응 기법에 대한 비교 분석**을 통해 연구의 범위를 넓혔습니다. 또한, **사전 학습 데이터 크기와 적응 데이터 크기의 상관관계**를 규명하여 향후 연구 방향을 제시합니다. 이는 **저자원 언어 처리 분야**의 발전과 **다양한 언어 모델의 효율적인 활용**에 크게 기여할 것입니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.10140/extracted/6204374/assets/data_downstream.png)

> 🔼 그림 1은 mBERT와 XLM-R의 사전 훈련 데이터 크기와 사전 적응 및 사후 적응 결과에 대한 다운스트림 작업 결과 간의 상관 관계를 보여줍니다. 세로 막대는 적응 데이터의 양을 나타냅니다. 두 모델 모두에서 다운스트림 작업 성능 향상은 사전 훈련 데이터 크기가 작은 언어에 집중되어 있으며, 그래프의 왼쪽에 위치해 있습니다. 반대로, 사전 훈련 데이터에서 상당한 표현을 가진 언어의 경우에는 성능 향상이 미미하거나 전혀 없습니다(7.4절 참조).
> <details>
> <summary>read the caption</summary>
> Figure 1: Correlation between the pre-training data sizes for mBERT and XLM-R and downstream task results for the pre-adaptation and post-adaptation results. The vertical bars indicate the amounts of adaptation data. The improvements in downstream performance for both models are primarily concentrated in languages with smaller pre-training data sizes, which are positioned on the left side of the plots. Conversely, for languages with substantial representation in the pre-training data, the improvements are less pronounced or nonexistent (Section 7.4).
> </details>





{{< table-caption >}}
| Model | #Params (B) | TC (↑) | NER (↑) |
|---|---|---|---|
| mBERT+<span class="ltx_text ltx_font_typewriter">Seq_bn_inv</span> | **0.177** | **71.92** | **85.28** |
| XLM-R+<span class="ltx_text ltx_font_typewriter">Seq_bn_inv</span> | **0.279** | **80.79** | **85.42** |
| DeepSeek-R1-D-Llama | 8 | 20.5 | - |
| DeepSeek-R1-D-Qwen | 14 | 41.88 | - |
| DeepSeek-R1-D-Qwen | 32 | 68.54 | - |
| DeepSeek-R1-D-Llama | 70 | 70.72 | - |
| LLaMA-3 | 8 | 65.8 | - |
| LLaMA-3.1 | 8 | 65.62 | - |
| Gemma | 7 | 60.21 | - |
| Gemma-2 | 9 | 44.27 | - |
| Qwen-1.5 | 7 | 40.41 | - |
| Qwen2 | 7 | 56.82 | - |
| GPT-3.5-turbo-0301 | - | - | 70.65 |
| GPT-3.5-turbo-0613 | - | 45.02 | - |
| GPT-4-0613 | - | 45.82 | - |
| LLaMA-2 | 7 | 18.24 | - |
| BLOOM | 7 | 13.02 | 31.35 |
| BLOOMz | 7 | 17.51 | 20.92 |
| mT0 | 13 | - | 17.48 |
| Occiglot-eu5 | 7 | 28.56 |  |
| XGLM | 7.5 | 29.98 | - |
| Yayi | 7 | 16.88 | - |
| LLaMAX2 Alpaca | 7 | 23.13 | - |
| Mala-500-v2 | 10 | 5.74 | - |{{< /table-caption >}}

> 🔼 표 1은 30개의 저자원 언어(LRL)에 대해 mBERT와 XLM-R 모델의 성능을 평가한 결과를 보여줍니다.  네 가지 과제(주제 분류, 개체명 인식, 감정 분석, 마스크 언어 모델링)에 대한 결과가 제시되며, 각 과제에 대해 사전 훈련 데이터에 포함된 언어와 포함되지 않은 언어로 나누어 평균 점수를 제시합니다.  베이스라인은 다운스트림 작업에 단일 태스크 어댑터를 사용하거나 MLM의 경우 어댑터를 사용하지 않은 모델입니다. 부록에는 각 과제에 대한 전체 결과가 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Results for mBERT and XLM-R across 4 tasks: Topic Classification (TC), Named Entity Recognition (NER), Sentiment Analysis (SA), Masked Language Modeling (MLM). All numbers are the averages for the 30 studied LRLs and provided separately for the languages included (”seen”) and languages not included (”unseen”) in the pre-training data of a model. The baselines are the models with a single task adapter for downstream tasks, or without adapters for MLM. The full results for each task are in the Appendix.
> </details>





### In-depth insights


#### mLMs for LRLs
본 논문은 저자원 언어(LRLs)에 대한 소규모 다국어 언어 모델(mLMs)의 적용 가능성에 대해 심도 있게 논의합니다. **mLMs는 대규모 언어 모델(LLMs)보다 매개변수가 적어 적은 훈련 데이터로도 효과적**이라는 점을 강조하며, 특히 LRLs에 적합함을 시사합니다.  **어댑터 기반의 매개변수 효율적인 방법**을 사용하여 mLMs를 LRLs에 적용하는 다양한 방법들을 제시하고 비교 분석합니다.  **비지도 학습 데이터와 구조화된 지식 그래프 데이터를 통합**하여 모델 성능 향상을 도모하는 전략도 포함되어 있습니다.  **전이 학습의 효율성**과 **사전 훈련 데이터 크기의 중요성**을 강조하면서, 제한된 데이터로도 상당한 성능 향상을 이끌어낼 수 있음을 보여줍니다.  **mLMs의 크기와 사전 훈련 데이터 크기 사이의 상관관계**를 분석하고, LRLs에 대한 적응력을 높이기 위한 중요한 요소임을 제시합니다.

#### Adapter Methods
본 논문에서 다루는 어댑터 기법은 **저자원 언어에 대한 소규모 다국어 언어 모델의 효율적인 적응**을 위한 매개변수 효율적인 방법입니다.  세 가지 주요 어댑터 구조인 순차적 병목(Sequential Bottleneck), 가역적 병목(Invertible Bottleneck), 그리고 저차원 적응(Low-Rank Adaptation)을 비교 분석하여 각 방법의 강점과 약점을 제시합니다. 특히, **순차적 병목 어댑터는 언어 모델링에서 뛰어난 성능**을 보이며, **가역적 병목 어댑터는 하위 작업에서 더 나은 임베딩 정렬과 더 많은 매개변수로 인해 다른 방법보다 약간 우수**한 것으로 나타났습니다.  전체적으로 어댑터 기반 방법은 매개변수 수가 훨씬 적으면서도 전체 미세 조정과 동등하거나 그 이상의 성능을 보여주는 매력적인 접근 방식임을 확인할 수 있습니다.

#### Data & Findings
본 논문의 데이터 및 결과 부분은 **저자원 언어(LRL)에 대한 다양한 언어 모델 적용의 효과성**을 면밀히 조사한 결과를 제시합니다.  **다양한 크기의 언어 모델과 어댑터 기반 방법론**을 사용하여,  구조화된 지식 그래프와 비구조화된 텍스트 데이터를 통합한 적응 전략이 LRL의 성능 향상에 미치는 영향을 분석했습니다. 특히, **소규모 다국어 모델(mLMs)이 대규모 언어 모델(LLMs)보다 LRL에 더 적합하며, 파라미터 효율적인 어댑터 기법이 전체 미세 조정보다 효과적**임을 보여줍니다.  **데이터 크기와 모델 성능 간의 상관관계 분석**을 통해, 사전 학습 데이터의 중요성과 제한된 적응 데이터의 효과를 확인할 수 있습니다.  **어댑터 아키텍처별 성능 비교**는 특정 작업에 대한 최적의 구조를 제시하고,  **다양한 언어 및 작업에 대한 일반적인 통찰력**을 제공합니다.  **결론적으로, 본 연구는 LRL에 대한 효율적이고 효과적인 언어 모델 적응 전략을 제시하며,  향후 연구 방향**을 제시합니다.

#### Small vs. Large LLMs
본 논문의 "Small vs. Large LLMs" 부분은 저자원 언어(LRLs)에 대한 효과적인 자연어 처리(NLP)를 위해 **소규모 다국어 언어 모델(mLMs)이 대규모 언어 모델(LLMs)보다 우수함**을 보여줍니다.  **mLMs는 제한된 용량으로 인해 다국어 표현을 효율적으로 정렬**하여, 제한된 데이터 환경에서도 LRLs에 일반화가 잘 됩니다. 반면, **LLMs는 막대한 매개변수에도 불구하고 LRLs에 대한 일반화에 어려움**을 겪습니다.  이는 제한된 용량이 모델이 언어 특징보다는 의미적 유사성에 집중하도록 유도하기 때문입니다.  **소규모 모델이 저자원 언어에 더 적합**하다는 기존 연구 결과와 일치합니다.  하지만, 사전 훈련 데이터의 크기 또한 성능에 중요한 영향을 미치므로, 이를 고려한 추가 연구가 필요합니다.

#### Future Work
본 논문은 저자원 언어에 대한 소규모 다국어 언어 모델 적응에 대해 심도있게 다루고 있지만, **미래 연구를 위한 흥미로운 가능성**을 여러 가지 제시합니다.  대규모 언어 모델에 대한 지식 그래프 통합 탐구는 **다국어 의미 관계를 더욱 풍부하게** 만들 수 있는 잠재력을 보여줍니다.  또한, **더 큰 적응 데이터셋**을 사용한 실험은 저자원 언어의 성능 향상에 어떤 영향을 미칠지 밝힐 수 있습니다.  **다양한 어댑터 아키텍처의 비교 분석**을 확장하고,  다양한 하이퍼파라미터에 대한 체계적인 연구는 **어댑터 기반 방법의 효율성을 최적화**하는 데 도움이 될 것입니다. 마지막으로, 제한된 용량 하에서 소규모 모델의 **교차 언어 전이 능력**에 대한 심층적인 분석은 **모델 아키텍처와 훈련 전략**의 개선에 중요한 통찰력을 제공할 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.10140/extracted/6204374/assets/ppl_vs_size.png)

> 🔼 이 그림은 mBERT와 XLM-R 모델의 사전 훈련 데이터 크기와 사전 적응 및 사후 적응 결과에 대한 의사-퍼플렉서티(pseudo-perplexity) 간의 상관관계를 보여줍니다. 로그 스케일로 값을 맞춰서 표현하였습니다.  그림은 사전 훈련 데이터 크기가 작은 언어일수록 적응 전후의 의사-퍼플렉서티 변화가 크다는 것을 보여줍니다. 즉, 사전 훈련 데이터가 부족한 저자원 언어일수록 적응을 통해 성능 향상을 더 크게 얻을 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Correlation between the pre-training data sizes for mBERT and XLM-R and the pseudo-perplexities with the values fit in the log-space for the pre-adaptation and post-adaptation results.
> </details>



![](https://arxiv.org/html/2502.10140/extracted/6204374/assets/base_cor_tasks.png)

> 🔼 그림 3은 mBERT와 XLM-R 모델의 성능과 관련된 상관관계를 보여줍니다.  구체적으로, 사전 적응(pre-adaptation) 전과 후의 다운스트림 작업 성능과 의사-퍼플렉서티(pseudo-perplexity) 간의 상관 관계를 나타냅니다. 이를 통해 각 모델의 사전 훈련 데이터 크기와 적응 데이터 크기가 다운스트림 작업 성능에 미치는 영향을 시각적으로 보여주고,  의사-퍼플렉서티가 다운스트림 작업 성능을 예측하는 지표로서의 유용성을 평가합니다.  각 그래프는 특정 다운스트림 작업 (주제 분류, NER, 감정 분석)에 대한 결과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Correlation between the downstream performance for mBERT and XLM-R pre- and post-adaptation and the pseudo-perplexities.
> </details>



![](https://arxiv.org/html/2502.10140/extracted/6204374/assets/tc_vs_data.png)

> 🔼 그림 4는 mBERT와 XLM-R 모델의 성능과 사전 학습 데이터 및 적응 데이터 간의 상관관계를 보여줍니다.  각 그래프는 특정 언어의 하위 작업(주제 분류, 개체명 인식, 감정 분석)에 대한 성능(F1 점수)과 사전 학습 데이터 크기(GB)의 관계를 나타냅니다.  색깔별 점들은 서로 다른 적응 데이터 크기를 나타내고, 선은 적합된 곡선입니다. 이 그림을 통해 사전 학습 데이터가 많을수록 적응 데이터의 효과가 감소하는 경향을 확인할 수 있으며, 특히 자원이 부족한 언어일수록 적은 적응 데이터로도 성능 향상에 큰 영향을 미치는 것을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Correlation between the downstream performance for mBERT and XLM-R and the pre-training data and adaptation data.
> </details>



![](https://arxiv.org/html/2502.10140/extracted/6204374/assets/ner_vs_data.png)

> 🔼 그림 5는 mBERT와 XLM-R 모델의 성능과 사전 학습 데이터 및 적응 데이터 간의 상관 관계를 보여줍니다.  x축은 사전 학습 데이터의 크기를 나타내고, y축은 다운스트림 작업(주제 분류, 개체명 인식, 감정 분석)의 F1 점수를 나타냅니다. 각 점은 특정 언어를 나타내며, 색상은 적응 데이터의 양을 나타냅니다. 그림은 사전 학습 데이터가 적은 저자원 언어일수록 적응 데이터가 성능 향상에 미치는 영향이 크다는 것을 보여줍니다. 반면, 사전 학습 데이터가 많은 고자원 언어에서는 적응 데이터의 효과가 감소합니다. 이는 모델이 이미 사전 학습 데이터를 통해 충분한 정보를 학습했기 때문으로 해석됩니다.  그림을 통해 저자원 언어에 대한 모델 적응 전략을 수립하는 데 도움이 되는 정보를 얻을 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Correlation between the downstream performance for mBERT and XLM-R and the pre-training data and adaptation data.
> </details>



![](https://arxiv.org/html/2502.10140/extracted/6204374/assets/sa_vs_data.png)

> 🔼 그림 6은 mBERT와 XLM-R 모델의 성능과 사전 학습 데이터 및 적응 데이터 간의 상관관계를 보여줍니다.  x축은 사전 학습 데이터의 크기(GB)를 나타내고, y축은 각 하위 작업(주제 분류, 개체명 인식, 감성 분석)의 F1 점수를 나타냅니다.  각 점은 특정 언어를 나타내며, 색깔은 적응 데이터의 크기를 나타냅니다.  그래프는 사전 학습 데이터가 많을수록 적응 데이터의 효과가 감소함을 보여주는 경향이 있습니다. 즉, 적은 양의 사전 학습 데이터를 가진 저자원 언어일수록 적응 데이터를 통해 더 큰 성능 향상을 보입니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Correlation between the downstream performance for mBERT and XLM-R and the pre-training data and adaptation data.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | TC (↑) | SA (↑) | NER (↑) |
|---|---|---|---|
| mBERT+<tt>Seq_bn_inv</tt> | **71.92** | **73.68** | **59.32** |
| XLM-R+<tt>Seq_bn_inv</tt> | **80.79** | **83.35** | **69.26** |
| LLaMA-3 Baseline | 31.93 | 58.83 | 45.18 |
| LLaMA-3+<tt>Seq_bn_inv</tt> | 60.26 | 68.68 | 45.12 |{{< /table-caption >}}
> 🔼 표 2는 TC와 NER 작업에 대해 중국어가 아닌 저자원 언어(LRL)에 대한 대규모 언어 모델(LLM)과 Glot 어댑터 기반의 소규모 다국어 모델(mLMs)의 평균 F1 점수를 보여줍니다.  프롬프팅 결과는 Ji et al.(2024)의 TC와 Asai et al.(2023)의 NER을 기반으로 3-shot입니다. NER의 경우 8개의 중복 언어에 대한 평균을 보고하며, GPT-3.5의 평균은 2개 언어에 대해서만 산출됩니다. Adelani et al.(2024a)가 보고한 바와 같이 GPT-3.5와 GPT-4의 TC 결과는 제로샷이며, DeepSeek 결과는 저자의 평가를 통해 제로샷으로 얻어졌습니다. 각 언어별 결과는 부록 U에 나와 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Average F1 scores on overlapping LRLs for LLMs and our Glot adapter-based mLMs on TC and NER. Prompting results are 3-shot, based on Ji et al. (2024) for TC and Asai et al. (2023) for NER. For NER, we report averages across eight overlapping languages, while the GPT-3.5 average is based on only two. TC results for GPT-3.5 and GPT-4 are zero-shot, as reported by Adelani et al. (2024a). DeepSeek results are zero-shot and were obtained in our evaluation. Per-language results are in Appendix U.
> </details>

{{< table-caption >}}
| ConceptNet Relationship | Natural Language Predicate |
|---|---| 
| Antonym | is the opposite of |
| DerivedFrom | is derived from |
| EtymologicallyDerivedFrom | is etymologically derived from |
| EtymologicallyRelatedTo | is etymologically related to |
| FormOf | is a form of |
| PartOf | is a part of |
| HasA | belongs to |
| UsedFor | is used for |
| AtLocation | is a typical location for |
| Causes | causes |
| CausesDesire | makes someone want |
| MadeOf | is made of |
| ReceivesAction | receives action of |
| HasSubevent | is a subevent of |
| HasFirstSubevent | is an event that begins with subevent |
| HasLastSubevent | is an event that concludes with subevent |
| HasPrerequisite | has prerequisite of |
| HasProperty | can be described as |
| MotivatedByGoal | is a step toward accomplishing the goal |
| ObstructedBy | is an obstacle in the way of |
| Desires | is a conscious entity that typically wants |
| CreatedBy | is a process or agent that creates |
| CapableOf | is capable of |
| HasContext | is a word used in the context of |
| IsA | is a type of |
| RelatedTo | is related to |
| SimilarTo | is similar to |
| Synonym | is a synonym of |
| SymbolOf | symbolically represents |
| DefinedAs | is a more explanatory version of |
| DistinctFrom | is distinct from |
| MannerOf | is a specific way to do |
| LocatedNear | is typically found near |{{< /table-caption >}}
> 🔼 본 표는 논문의 5개 저자원 언어(LRLs)에 대해 언어 어댑터로 미세 조정된 LLaMA-3-8B, mBERT, XLM-R 모델의 평균 F1 점수를 보여줍니다.  LLaMA-3 모델에 대한 기준선 결과도 포함되어 있으며, 이는 본 연구의 기준선과 유사하게 단일 Seq_bn 작업 어댑터를 사용한 결과입니다. 각 언어에 대한 자세한 결과는 부록 U에 나와 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Average F1 scores over 5 selected LRLs for language adapter-tuned LLaMa-3-8B, mBERT, and XLM-R. Additionally, we present results for LLaMA3 with a single Seq_bn task adapter, similar to our baselines. Per-language results are in Appendix U.
> </details>

{{< table-caption >}}
| Language | ISO | Language Family | CN (Sent-s) | CN (MB) | Glot (Doc-s) | Glot (MB) | mBERT? | XLM-R? | mBERT Data Size (GB) | XLM-R Data Size (GB) |
|---|---|---|---|---|---|---|---|---|---|---|
| Thai | th | Kra-Dai | 123,859 | 6.95 | 2,391,253 | 977.68 | ✓ | ✓ | 1.29 | 85.24 |
| Romanian | ro | Indo-European | 70,236 | 2.47 | 8,657,002 | 1002.36 | ✓ | ✓ | 1.22 | 83.29 |
| Bulgarian | bg | Indo-European | 162,181 | 8.02 | 5,192,702 | 1014.73 | ✓ | ✓ | 1.50 | 70.37 |
| Danish | da | Indo-European | 66,109 | 2.27 | 8,743,767 | 1006.91 | ✓ | ✓ | 0.81 | 62.39 |
| Greek | el | Indo-European | 89,016 | 4.17 | 4,789,519 | 980.94 | ✓ | ✓ | 1.85 | 57.30 |
| Hebrew | he | Afro-Asiatic | 41,444 | 1.62 | 5,287,428 | 991.82 | ✓ | ✓ | 2.73 | 40.87 |
| Slovak | sk | Indo-European | 22,460 | 0.81 | 9,294,165 | 1006.96 | ✓ | ✓ | 0.61 | 31.96 |
| Slovenian | sl | Indo-European | 85,882 | 2.98 | 9,301,902 | 1007.91 | ✓ | ✓ | 0.67 | 14.16 |
| Latvian | lv | Indo-European | 66,408 | 2.4 | 8,301,651 | 988.21 | ✓ | ✓ | 0.33 | 11.94 |
| Indonesian | ms | Austronesian | 175,246 | 6.21 | 8,024,827 | 1022.01 | ✓ | ✓ | 0.59 | 11.73 |
| Georgian | ka | Kartvelian | 35,331 | 1.89 | 3,463,631 | 1014.24 | ✓ | ✓ | 0.88 | 10.55 |
| Bengali | bn | Indo-European | 8,782 | 0.46 | 2,940,197 | 993.44 | ✓ | ✓ | 1.22 | 10.10 |
| Azerbaijani | az | Turkic | 15,149 | 0.57 | 6,179,152 | 1016.68 | ✓ | ✓ | 0.62 | 8.33 |
| Urdu | ur | Indo-European | 13,315 | 0.51 | 4,220,566 | 1009.42 | ✓ | ✓ | 0.54 | 6.97 |
| Macedonian | mk | Indo-European | 38,116 | 1.54 | 5,037,552 | 1005.62 | ✓ | ✓ | 0.86 | 5.76 |
| Telugu | te | Dravidian | 33,476 | 1.72 | 3,162,535 | 1005.55 | ✓ | ✓ | 0.88 | 5.46 |
| Nepali | ne | Indo-European | 4,456 | 0.21 | 2,569,572 | 1012.63 | ✓ | ✓ | 0.14 | 4.32 |
| Marathi | mr | Indo-European | 7,232 | 0.37 | 402,575 | 157.3 | ✓ | ✓ | 0.32 | 3.33 |
| Swahili | sw | Niger-Congo | 12,380 | 0.39 | 2,450,753 | 323.27 | ✓ | ✓ | 0.10 | 2.15 |
| Welsh | cy | Indo-European | 18,313 | 0.61 | 3,174,686 | 360.24 | ✓ | ✓ | 0.39 | 1.07 |
| Uzbek | uz | Turkic | 4,362 | 0.16 | 4,018,172 | 481.49 | ✓ | ✓ | 0.57 | 0.95 |
| Javanese | jv | Austronesian | 3,448 | 0.13 | 367,795 | 43.56 | ✓ | ✓ | 0.10 | 0.20 |
| Sundanese | su | Austronesian | 1,880 | 0.07 | 323,610 | 43.55 | ✓ | ✓ | 0.06 | 0.08 |
| Sinhala | si | Indo-European | 1,782 | 0.1 | 1,655,641 | 586.21 | ✘ | ✓ | ✘ | 4.27 |
| Amharic | am | Afro-Asiatic | 1,814 | 0.07 | 667,881 | 203.65 | ✘ | ✓ | ✘ | 1.00 |
| Kurdish | ku | Indo-European | 12,246 | 0.44 | 376,260 | 134.7 | ✘ | ✓ | ✘ | 0.52 |
| Uyghur | ug | Turkic | 1,715 | 0.06 | 976,010 | 233.61 | ✘ | ✓ | ✘ | 0.43 |
| Maltese | mt | Afro-Asiatic | 3,895 | 0.14 | 1,389,527 | 182.17 | ✘ | ✘ | ✘ | ✘ |
| Tibetan | bo | Sino-Tibetan | 4,768 | 0.21 | 288,847 | 165.31 | ✘ | ✘ | ✘ | ✘ |
| Yoruba | yo | Niger-Congo | 1,044 | 0.05 | 278,003 | 34.51 | ✓ | ✘ | 0.03 | ✘ |{{< /table-caption >}}
> 🔼 본 표는 ConceptNet 지식 그래프의 관계와 이에 상응하는 자연어술어 간의 매핑을 보여줍니다. ConceptNet의 관계는 지식 그래프의 에지를 나타내는 반면, 자연어술어는 이러한 관계를 표현하는 사람이 이해하기 쉬운 문장으로 변환된 것입니다. 이 매핑은 ConceptNet 지식 그래프 데이터를 자연어 텍스트로 변환하는 데 사용됩니다. 예를 들어, 'Antonym' 관계는 'is the opposite of' 라는 술어로 매핑되고, 'PartOf' 관계는 'is part of' 로 매핑됩니다. 이 표는 논문에서 ConceptNet 데이터를 사용한 실험에 대한 이해를 돕습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: ConceptNet relationships and their natural language predicates. This mapping is used for converting the ConceptNet KG data into natural language text.
> </details>

{{< table-caption >}}
| Language | ISO code | #train | #val | #test |
|---|---|---|---|---|
| Bulgarian | bg | 20000 | 10000 | 10000 |
| Indonesian | ms | 20000 | 1000 | 1000 |
| Maltese | mt | 100 | 100 | 100 |
| Nepali | ne | 100 | 100 | 100 |
| Javanese | jv | 100 | 100 | 100 |
| Uyghur | ug | 100 | 100 | 100 |
| Tibetan | bo | 100 | 100 | 100 |
| Sinhala | si | 100 | 100 | 100 |
| Sundanese | su | 100 | 100 | 100 |
| Amharic | am | 100 | 100 | 100 |
| Swahili | sw | 1000 | 1000 | 1000 |
| Georgian | ka | 10000 | 10000 | 10000 |
| Latvian | lv | 10000 | 10000 | 10000 |
| Slovak | sk | 20000 | 10000 | 10000 |
| Slovenian | sl | 15000 | 10000 | 10000 |
| Uzbek | uz | 1000 | 1000 | 1000 |
| Yoruba | yo | 100 | 100 | 100 |
| Urdu | ur | 20000 | 1000 | 1000 |
| Macedonian | mk | 10000 | 1000 | 1000 |
| Danish | da | 20000 | 10000 | 10000 |
| Marathi | mr | 5000 | 1000 | 1000 |
| Bengali | bn | 10000 | 1000 | 1000 |
| Hebrew | he | 20000 | 10000 | 10000 |
| Romanian | ro | 20000 | 10000 | 10000 |
| Telugu | te | 1000 | 1000 | 1000 |
| Welsh | cy | 10000 | 1000 | 1000 |
| Azerbaijani | az | 10000 | 1000 | 1000 |
| Greek | el | 20000 | 10000 | 10000 |
| Kurdish | ku | 100 | 100 | 100 |
| Thai | th | 20000 | 10000 | 10000 |{{< /table-caption >}}
> 🔼 표 5는 언어별 ConceptNet 3중항 및 GlotCC 문서의 수와 해당 데이터 크기를 보여줍니다. GlotCC 문서 수를 기준으로 내림차순으로 정렬되어 있습니다. 마지막 네 열은 각 언어가 mBERT 및 XLM-R 사전 훈련 데이터에 포함되었는지 여부와 해당 데이터 크기(GB)를 나타냅니다. 공개적으로 사용 가능한 CC100 및 위키피디아 데이터 세트를 기반으로 크기를 어림잡았습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Number of ConceptNet triples and GlotCC documents as well as corresponding data sizes per language, sorted by Glot (Doc-s) in descending order. The last four columns indicate the inclusion of the respective language in mBERT and XLM-R pre-training data, alongside the corresponding data sizes in GB. The sizes are approximated based on the openly available CC100 and WikiPedia datasets.
> </details>

{{< table-caption >}}
| ISO | ConceptNet |  |  |  |  |  | Glot |  |  |  |  |  | 
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| **mBERT** | **Seq_bn** | **LoRA** | **Seq_bn_inv** | **XLM-R** | **Seq_bn** | **LoRA** | **Seq_bn_inv** | **mBERT** | **Seq_bn** | **LoRA** | **Seq_bn_inv** | **XLM-R** | **Seq_bn** | **LoRA** | **Seq_bn_inv** |
| th | 1.21 | 1.24 | 1.2 | 1.42 | 1.42 | 1.35 | 0.46 | 0.54 | 0.45 | 1.55 | 1.65 | 1.53 |
| ro | 1.41 | 1.46 | 1.34 | 1.43 | 1.43 | 1.33 | 1.37 | 1.52 | 1.34 | 1.27 | 1.3 | 1.26 |
| bg | 0.68 | 0.71 | 0.66 | 0.87 | 0.87 | 0.81 | 1.09 | 1.25 | 1.07 | 1.83 | 1.8 | 1.8 |
| da | 1.24 | 1.29 | 1.19 | 1.35 | 1.36 | 1.26 | 1.39 | 1.54 | 1.36 | 1.28 | 1.36 | 1.26 |
| el | 1.13 | 1.18 | 1.12 | 1.36 | 1.36 | 1.29 | 0.67 | 0.77 | 0.66 | 0.84 | 0.9 | 0.83 |
| he | 1.35 | 1.38 | 1.32 | 1.47 | 1.46 | 1.4 | 1.3 | 1.41 | 1.28 | 1.29 | 1.38 | 1.28 |
| sk | 1.22 | 1.28 | 1.16 | 1.39 | 1.39 | 1.28 | 1.09 | 1.19 | 1.06 | 1.16 | 1.19 | 1.14 |
| sl | 0.83 | 0.91 | 0.79 | 1.05 | 1.09 | 0.98 | 1.16 | 1.28 | 1.13 | 1.22 | 1.28 | 1.21 |
| lv | 1.32 | 1.4 | 1.25 | 1.47 | 1.51 | 1.37 | 1.11 | 1.29 | 1.07 | 1.28 | 1.37 | 1.25 |
| ms | 1.57 | 1.63 | 1.5 | 1.59 | 1.57 | 1.47 | 1.52 | 1.65 | 1.48 | 1.55 | 1.6 | 1.54 |
| ka | 1.15 | 1.19 | 1.14 | 1.38 | 1.35 | 1.3 | 0.79 | 0.91 | 0.77 | 1.12 | 1.18 | 1.11 |
| bn | 0.99 | 1.03 | 0.97 | 1.37 | 1.37 | 1.3 | 1.05 | 1.16 | 1.03 | 1.44 | 1.49 | 1.42 |
| az | 1.33 | 1.37 | 1.29 | 1.5 | 1.55 | 1.42 | 0.89 | 1.02 | 0.86 | 1.19 | 1.31 | 1.15 |
| ur | 1.43 | 1.48 | 1.4 | 1.62 | 1.61 | 1.51 | 1.15 | 1.31 | 1.12 | 1.38 | 1.44 | 1.36 |
| mk | 1.42 | 1.44 | 1.38 | 1.59 | 1.54 | 1.45 | 0.89 | 0.99 | 0.87 | 1.41 | 1.4 | 1.41 |
| te | 1.09 | 1.12 | 1.07 | 1.29 | 1.29 | 1.22 | 0.83 | 0.94 | 0.81 | 1.33 | 1.4 | 1.31 |
| ne | 1.26 | 1.31 | 1.21 | 1.53 | 1.52 | 1.42 | 0.77 | 0.9 | 0.75 | 1.38 | 1.45 | 1.35 |
| mr | 1.08 | 1.12 | 1.04 | 1.46 | 1.45 | 1.37 | 0.94 | 1.07 | 0.92 | 1.43 | 1.49 | 1.41 |
| sw | 1.54 | 1.63 | 1.51 | 1.64 | 1.73 | 1.56 | 0.94 | 1.13 | 0.9 | 1.13 | 1.22 | 1.1 |
| cy | 1.55 | 1.6 | 1.48 | 1.83 | 1.91 | 1.76 | 0.81 | 0.99 | 0.77 | 0.95 | 1.06 | 0.92 |
| uz | 1.22 | 1.3 | 1.18 | 1.55 | 1.62 | 1.45 | 0.85 | 1.01 | 0.82 | 1.06 | 1.17 | 1.03 |
| jv | 1.44 | 1.5 | 1.4 | 1.55 | 1.56 | 1.48 | 2.11 | 2.21 | 2.08 | 2.63 | 2.66 | 2.54 |
| su | 1.51 | 1.56 | 1.47 | 1.38 | 1.4 | 1.38 | 1.14 | 1.28 | 1.11 | 1.21 | 1.35 | 1.18 |
| si | 1.4 | 1.33 | 1.38 | 1.31 | 1.25 | 1.25 | 0.82 | 0.88 | 0.8 | 1.21 | 1.29 | 1.19 |
| am | 1.47 | 1.51 | 1.58 | 1.22 | 1.29 | 1.13 | 1.25 | 1.31 | 1.23 | 1.2 | 1.31 | 1.19 |
| ku | 1.64 | 1.73 | 1.61 | 1.91 | 2.04 | 1.86 | 0.93 | 1.05 | 0.9 | 0.76 | 1.02 | 0.71 |
| ug | 1.09 | 1.13 | 1.07 | 1.57 | 1.59 | 1.47 | 0.46 | 0.57 | 0.44 | 0.79 | 0.94 | 0.76 |
| mt | 1.41 | 1.44 | 1.39 | 1.53 | 1.68 | 1.5 | 0.84 | 1.08 | 0.8 | 0.93 | 1.2 | 0.87 |
| bo | 1.0 | 1.01 | 0.98 | 0.63 | 0.64 | 0.62 | 0.24 | 0.28 | 0.24 | 0.72 | 0.73 | 0.71 |
| yo | 1.12 | 1.27 | 1.1 | 1.77 | 1.79 | 1.76 | 0.87 | 1.04 | 0.84 | 0.83 | 1.03 | 0.78 |{{< /table-caption >}}
> 🔼 표 6은 논문에서 사용된 감성 분석 데이터셋에 대한 세부 정보를 제공합니다. 각 언어에 대해 데이터 출처, 긍정적/부정적 리뷰 수, 학습/검증/테스트 데이터의 분할 비율이 제시되어 있습니다. 이 표는 다양한 언어의 감성 분석 작업에 사용된 데이터셋의 크기와 분포를 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 6:  Sentiment analysis data details.
> </details>

{{< table-caption >}}
| Adapter Type | mBERT |  |  | XLM-R |  |  | LLaMA-3 |  |
|---|---|---|---|---|---|---|---|---|
|  | Seq_bn | Seq_bn_inv | LoRA | Seq_bn | Seq_bn_inv | LoRA | Seq_bn | Seq_bn_inv |
| Trainable Params (No.) | 894,528 | 1,190,592 | 294,912 | 894,528 | 1,190,592 | 294,912 | 67,248,128 | 75,642,880 |
| Trainable Params (%) | 0.505% | 0.672% | 0.166% | 0.322% | 0.429% | 0.106% | 0.896% | 1.008% |
| Hyperparameters for LA | Batch Size: 16, Learning Rate: 1e-4,  Seq_bn and Seq_bn_inv: Reduction Factor = 16, LoRA: α=8, r=8 |  |  | Batch Size: 1, Learning Rate: 1e-4 |  |  |  |  |
| Hyperparameters for TA | Batch Size: 32, Learning Rate: 1e-4, Seq_bn: Reduction Factor = 16, LoRA: α=8, r=8 |  |  | Batch Size for TC: 16; for SA and NER: 8, Learning Rate: 2e-5 |  |  |  |  |{{< /table-caption >}}
> 🔼 표 7은 논문에서 사용된 30개 저자원 언어에 대한 개체명 인식(Named Entity Recognition, NER) 데이터셋의 세부 정보를 보여줍니다. 각 언어에 대해 학습, 검증 및 테스트 데이터의 수를 나타냅니다. 이 표는 모델의 NER 성능을 평가하는 데 사용된 데이터의 크기와 분포를 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Named entity recognition data details.
> </details>

{{< table-caption >}}
| Batch Size | Learning Rate | Seq_bn and Seq_bn_inv Reduction Factor | LoRA (α, r) |
|---|---|---|---| 
| 16 | 1e-4 | 16 | 8, 8 |{{< /table-caption >}}
> 🔼 이 표는 모델, 아키텍처 및 언어별로 언어 어댑터의 평가 손실을 보여줍니다.  평가 손실 값은 MLM 성능을 예측하는 데 도움이 되지 않았습니다.  가장 낮은 평가 손실을 기록한 Seq_bn_inv는 MLM 작업에서 성능이 저조했습니다. 이는 평가 손실이 신뢰할 수 없는 훈련 지표가 될 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Evaluation losses for language adapters by model, architecture, and language.
> </details>

{{< table-caption >}}
| Batch Size | Learning Rate |
|---|---| 
| 1 | 1e-4 |
{{< /table-caption >}}
> 🔼 이 표는 논문의 3.1절 모델 적응(Model Adaptation)에서 세 가지 어댑터 구조(Sequential Bottleneck, Sequential Bottleneck with Invertible Layers, Low-Rank Adaptation)를 사용하여 mBERT와 XLM-R, 그리고 LLaMA-3를 저자원 언어에 적응시키는 과정에서 사용된 매개변수의 수와 하이퍼파라미터를 보여줍니다.  각 모델과 어댑터 유형별로 학습 가능한 매개변수의 수와 전체 매개변수에서 차지하는 비율이 제시됩니다. 또한, 언어 어댑터(LA)와 작업 어댑터(TA)에 대해 각각 사용된 하이퍼파라미터 설정도 포함되어 있습니다. Adapterhub의 기본 어댑터 설정을 따르는 나머지 하이퍼파라미터는 표에 명시적으로 제시되지 않았습니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Trainable parameters and hyperparameters for different adapter types in mBERT, XLM-R, and LLaMA-3. The rest of hyperparameters are as specified in the default adapter configurations in Adapterhub. LA - Langauge adapter, TA - Task adapter.
> </details>

{{< table-caption >}}
| Batch Size | Learning Rate | Seq_bn Reduction Factor | LoRA α | LoRA r |
|---|---|---|---|---|
| 32 | 1e-4 | 16 | 8 | 8 |{{< /table-caption >}}
> 🔼 표 10은 ConceptNet과 Glot 데이터를 사용하여 mBERT에 대한 다양한 어댑터의 마스크 언어 모델링 성능을 비교한 것입니다.  †기호는 mBERT의 사전 훈련에 포함되지 않은 언어를 나타냅니다. FFT는 대상 언어의 Glot 데이터를 기반으로 한 기본 모델의 완전 미세 조정을 나타냅니다. 밑줄 친 FFT 점수는 해당 언어에 대해 최고 성능의 어댑터보다 FFT의 성능이 더 우수함을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Pseudo-perplexity scores comparison across different adapters for mBERT in ConceptNet and Glot. †Language not included in mBERT pre-training. FFT denotes full fine-tuning of a base model on the target-language Glot data. The underlined FFT scores indicate that FFT outperform the best performing adapter for a respective language.
> </details>

{{< table-caption >}}
| Batch Size for TC | Learning Rate |
|---|---| 
| 16 for TC; 8 for SA and NER | 2e-5 |{{< /table-caption >}}
> 🔼 표 11은 ConceptNet과 Glot 데이터셋에서 다양한 어댑터를 사용하여 XLM-R 모델의 마스크 언어 모델링(MLM) 성능을 비교한 결과입니다.  ‡ 표시는 XLM-R의 사전 훈련 데이터에 포함되지 않은 언어임을 나타냅니다.  FFT는 기본 모델을 대상 언어의 Glot 데이터로 미세 조정한 결과를 보여줍니다.  밑줄 친 FFT 점수는 해당 언어에 대해 최고 성능의 어댑터보다 FFT의 성능이 더 우수함을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 11: Pseudo-perplexity scores comparison for XLM-R across different adapters in ConceptNet and Glot. ‡Language not included in XLM-R pre-training. FFT denotes full fine-tuning of a base model on the target-language Glot data. The underlined FFT scores indicate that FFT outperform the best performing adapter for a respective language.
> </details>

{{< table-caption >}}
| ISO | mBERT | mBERT | mBERT | mBERT | mBERT | mBERT | mBERT | mBERT | mBERT |
|---|---|---|---|---|---|---|---|---|---|
|  | **Base** | **Seq_bn** | **LoRA** | **Seq_bn_inv** | **Seq_bn** | **LoRA** | **Seq_bn_inv** | **FFT** |
| he | 18.36 | 19.71 | 18.29 | 19.85 | **11.09** | 12.31 | 12.51 | 8.78 |
| el | 4.69 | 6.17 | 5.55 | 6.92 | **3.3** | 3.54 | 3.49 | 2.71 |
| bg | 10.84 | 14.99 | 12.65 | 20.93 | **5.4** | 5.9 | 6.09 | 4.67 |
| th | 3.87 | 4.13 | 4.29 | 4.07 | **2.94** | 3.34 | 3.18 | 2.54 |
| ro | 11.49 | 13.47 | 12.67 | 22.39 | **5.94** | 6.59 | 8.67 | 6.75 |
| bn | 11.97 | 14.94 | 13.53 | 15.99 | **9.11** | 10.05 | 10.32 | 8.42 |
| te | 7.92 | 8.9 | 8.34 | 9.33 | **6.09** | 6.13 | 6.4 | 5.32 |
| ka | 6.52 | 6.3 | 6.0 | 6.54 | **3.63** | 4.06 | 3.91 | 2.6 |
| mk | 11.95 | 14.5 | 12.3 | 13.26 | **5.83** | 6.33 | 6.54 | 5.53 |
| da | 19.16 | 19.29 | 25.39 | 30.87 | **11.13** | 11.8 | 13.02 | 8.76 |
| sl | 13.57 | 18.09 | 14.32 | 26.86 | **6.68** | 7.26 | 8.58 | 4.91 |
| az | 12.47 | 15.2 | 13.48 | 24.26 | **7.04** | 7.89 | 7.9 | 5.83 |
| sk | 11.5 | 13.86 | 12.37 | 19.29 | **5.98** | 6.64 | 7.14 | 6.03 |
| ms | 36.26 | 53.66 | 50.17 | 128.6 | **18.23** | 20.01 | 22.71 | 16.95 |
| uz | 26.65 | 31.41 | 23.43 | 40.35 | **5.84** | 7.21 | 9.22 | 3.84 |
| ur | 22.59 | 23.02 | 21.74 | 26.4 | **10.18** | 12.0 | 12.89 | 7.16 |
| cy | 21.24 | 22.13 | 23.0 | 39.75 | **6.08** | 7.8 | 9.06 | 4.89 |
| lv | 14.14 | 18.31 | 16.21 | 33.14 | **5.98** | 7.13 | 7.48 | 4.58 |
| mr | 12.51 | 12.9 | 12.21 | 14.0 | **5.84** | 6.78 | 6.85 | 6.71 |
| ne | 12.72 | 14.19 | 13.08 | 15.36 | **6.71** | 7.21 | 8.68 | 4.88 |
| jv | 83.84 | 115.27 | 132.08 | 146.64 | **19.4** | 22.86 | 31.6 | 19.19 |
| sw | 42.53 | 57.57 | 52.21 | 79.5 | **8.99** | 12.48 | 16.09 | 7.19 |
| su | 102.16 | 177.27 | 183.04 | 227.87 | **20.24** | 23.2 | 34.29 | 34.93 |
| yo | 85.21 | 293.99 | 210.43 | 370.71 | **23.14** | 31.96 | 86.79 | 38.89 |
| Avg. | 25.17 | 41.22 | 37.37 | 55.95 | **8.95** | 10.44 | 14.31 | 9.25 |
| mt† | 531.59 | 432.99 | 456.64 | 457.43 | **6.89** | 9.87 | 15.02 | 5.95 |
| ku† | **72.87** | 119.29 | 101.13 | 149.74 | 1524.98 | 559.83 | 173.24 | 6381.75 |
| ug† | 112.63 | 96.52 | 86.31 | 121.15 | **28.69** | 67.26 | 75.53 | 313.64 |
| si† | **16.29** | 96.5 | 40.3 | 103.36 | 15640.68 | 8981.09 | 157397.73 | 443921.11 |
| am† | **10.06** | 31.41 | 26.93 | 23.47 | 56052.75 | 34924.59 | 4223.4 | 38289.93 |
| bo† | **4.59** | 58.78 | 47.33 | 89.81 | 57.94 | 65.03 | 1136.47 | 41.99 |
| Avg. | **124.67** | 139.25 | 126.44 | 157.49 | 12218.65 | 7434.61 | 27170.23 | 81492.4 |
| Total | **45.07** | 60.83 | 55.18 | 76.26 | 2450.89 | 1495.27 | 5445.49 | 16305.88 |{{< /table-caption >}}
> 🔼 본 표는 사전 적응 전과 후의 mBERT 및 XLM-R 모델에 대해 의사-퍼플렉서티와 사전 학습 및 추가 학습 데이터 양 간의 피어슨 및 스피어만 상관 관계를 보여줍니다. 추가 학습 결과는 Seq_bn 언어 어댑터를 사용한 모델을 기반으로 하며, 사전 학습과 추가 학습 데이터 크기의 합계와 적응 후 의사-퍼플렉서티 점수 간의 상관 관계를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 12: Pearson and Spearman Correlations for mBERT and XLM-R between pseudo-perplexity and amounts of pre-training and post-training data for the pre-adaptation and post-adaptation results. Post-adaptation results are based on the models with Seq_bn language adapters and denote the correlation between the sum of the pre-training and adaptation data sizes and pseudo-perplexity scores after the adaptation.
> </details>

{{< table-caption >}}
| ISO | XLM-R |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|
| **ISO** | **XLM-R** |  |  |  |  |  |  |  |
|  |  | **ConceptNet** |  |  | **Glot** |  |  |  |
|  | **Base** | **Seq_bn** | **LoRA** | **Seq_bn_inv** | **Seq_bn** | **LoRA** | **Seq_bn_inv** | **FFT** |
| th | 7.83 | 8.67 | 8.86 | 10.11 | 8.78 | 7.97 | 9.39 | 22.16 |
| ro | 2.97 | 3.76 | 3.79 | 4.51 | 3.42 | **2.96** | 3.25 | 6.18 |
| bg | **3.61** | 4.88 | 5.51 | 5.4 | 3.63 | 3.7 | 3.64 | 6.12 |
| da | 4.29 | 5.56 | 5.94 | 6.21 | 6.69 | **4.21** | 4.58 | 7.9 |
| el | **2.56** | 3.17 | 3.1 | 3.46 | 2.97 | 2.63 | 2.87 | 3.81 |
| he | **5.74** | 6.17 | 6.36 | 6.74 | 5.8 | 5.84 | 5.99 | 10.95 |
| sk | 3.93 | 4.85 | 4.67 | 5.36 | 4.56 | **3.68** | 4.08 | 4.62 |
| sl | 4.79 | 7.31 | 7.41 | 8.68 | 4.35 | **4.01** | 4.95 | 5.3 |
| lv | 4.14 | 5.96 | 6.32 | 9.34 | 5.09 | **3.92** | 4.7 | **4.87** |
| ms | 10.79 | 15.02 | 15.82 | 17.26 | 8.97 | **8.8** | 9.65 | 12.55 |
| ka | **3.88** | 4.41 | 4.47 | 4.48 | 3.99 | 3.94 | 4.76 | 4.97 |
| bn | 6.5 | 7.22 | 7.17 | 7.6 | **5.95** | 6.28 | 8.0 | 6.69 |
| az | 7.52 | 11.21 | 11.45 | 15.95 | 8.27 | **7.58** | 9.7 | 14.11 |
| ur | 10.17 | 12.13 | 12.82 | 12.23 | **9.53** | 9.54 | 11.12 | 12.32 |
| mk | 5.19 | 6.74 | 7.51 | 7.28 | 4.82 | **4.78** | **4.78** | 8.14 |
| te | 6.76 | 8.12 | 8.11 | 8.31 | **6.41** | 6.66 | 9.92 | 7.6 |
| ne | 12.76 | 16.87 | 17.74 | 16.91 | 11.86 | **11.82** | 22.42 | 16.64 |
| si | 7.04 | 7.97 | 8.22 | 8.26 | **5.74** | 6.37 | 11.44 | 6.74 |
| mr | 10.25 | 11.83 | 12.12 | 12.67 | 9.11 | **8.9** | 16.42 | 21.99 |
| sw | 15.68 | 26.99 | 27.39 | 36.78 | **7.76** | 9.61 | 11.24 | 9.18 |
| cy | 9.37 | 13.94 | 16.05 | 17.51 | **5.08** | 5.88 | 8.11 | **4.7** |
| am | 10.87 | 14.77 | 15.4 | 15.15 | **7.32** | 8.44 | 17.0 | 10.49 |
| uz | 8.4 | 14.77 | 16.81 | 20.66 | **5.46** | 6.21 | 9.14 | 5.92 |
| ku | 159.39 | 72.75 | 84.04 | 69.25 | **2.95** | 4.34 | 19.27 | 3.88 |
| ug<sup>†</sup> | 6.87 | 13.97 | 12.48 | 16.76 | **4.99** | 5.97 | 12.48 | 16.13 |
| jv | 33.81 | 96.45 | 89.36 | 116.95 | **12.49** | 15.06 | 27.14 | 26.25 |
| su | 57.32 | 134.71 | 128.95 | 152.14 | **10.41** | 15.22 | 29.1 | 25.16 |
| Avg. | 15.65 | 20.01 | 20.29 | 22.81 | **6.53** | 6.83 | 10.56 | 10.57 |
| mt<sup>‡</sup> | 395.18 | 283.77 | 335.23 | 275.56 | **3.19** | 5.0 | 12.01 | 3.36 |
| bo<sup>‡</sup> | **9.45** | 937.1 | 2036.45 | 1209.39 | 353.49 | 274.66 | 1972.96 | 597.55 |
| yo<sup>‡</sup> | 207.26 | 225.8 | 335.24 | 223.49 | **9.57** | 14.31 | 155.99 | 19.12 |
| Avg. | 203.96 | 482.22 | 902.31 | 569.48 | 122.08 | **97.99** | 713.65 | 206.68 |
| Total | 34.48 | 66.23 | 108.49 | 77.48 | 18.09 | **15.94** | 80.87 | 30.18 |{{< /table-caption >}}
> 🔼 표 13은 세 가지 모델 구성(XLM-R 기본 모델, Glot 데이터로 적응된 XLM-R 기본 모델, XLM-R 대형 모델)에 대해 30개 언어의 평균 의사 퍼플렉서티 점수를 보여줍니다. 적응된 XLM-R 기본 모델의 경우 성능이 가장 좋은 어댑터의 결과를 사용했습니다. 이 표는 다양한 모델과 어댑터를 사용한 저자원 언어에 대한 언어 모델 적응의 효과를 비교 분석하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 13: Average pseudo-perplexity scores for 30 languages across three model configurations. For the adapted XLM-R-base, we pick the adapter with the best performance.
> </details>

{{< table-caption >}}
| Model | Pearson (p-value) | Spearman (p-value) |
|---|---|---|
| **Pre-adapt** |  |  |
| mBERT | -0.37 (0.07) | -0.51 (0.01) |
| XLM-R | -0.32 (0.1) | -0.39 (0.04) |
| **Post-adapt** |  |  |
| mBERT | -0.69 (¡0.001) | -0.79 (¡0.001) |
| XLM-R | -0.27 (0.16) | -0.79 (¡0.001) |{{< /table-caption >}}
> 🔼 본 표는 mBERT와 XLM-R 모델에 대해 사전 적응(Pre-Adapt) 및 사후 적응(Post-Adapt) 단계에서의 의사-퍼플렉서티(pseudo-perplexity)와 과제 성능 간의 상관관계를 피어슨(Pearson)과 스피어만(Spearman) 상관 계수를 사용하여 보여줍니다.  사후 적응 결과는 Seq_bn 언어 어댑터를 사용하여 적응된 모델을 기준으로 합니다.  즉, 모델의 언어 모델링 성능(의사-퍼플렉서티로 측정)이 하위 과제(예: 주제 분류, 감정 분석, 개체명 인식)의 성능과 얼마나 연관되어 있는지 분석한 결과를 보여줍니다.  사전 적응과 사후 적응 모두에 대한 상관관계가 제시되어 모델 적응 전후의 관계를 비교 분석하는 데 유용합니다.
> <details>
> <summary>read the caption</summary>
> Table 14: Pearson and Spearman Correlations for mBERT and XLM-R (Pre-Adapt and Post-Adapt) between pseudo-perplexity and task performance. Post-Adapt is represented by the models adapted with the Seq_bn language adapters.
> </details>

{{< table-caption >}}
| ISO | XLM-R-base | Adapted XLM-R-base | XLM-R-large | Glot-500m |
|---|---|---|---|---|
| th | 7.83 | 7.97 | **4.92** | 31.34 |
| ro | 2.97 | 2.96 | **2.06** | 13.29 |
| bg | 3.61 | 3.63 | **2.53** | 14.16 |
| da | 4.29 | 4.21 | **2.78** | 28.06 |
| el | 2.56 | 2.97 | **1.87** | 6.87 |
| he | 5.74 | 5.8 | **3.19** | 32.80 |
| sk | 3.93 | 3.68 | **2.30** | 26.36 |
| sl | 4.79 | 4.01 | **2.60** | 41.98 |
| lv | 4.14 | 3.92 | **2.51** | 14.55 |
| ms | 10.79 | 8.8 | **6.71** | 38.46 |
| ka | 3.88 | 3.94 | **2.69** | 10.77 |
| bn | 6.50 | 5.95 | **3.99** | 19.36 |
| az | 7.52 | 7.58 | **4.40** | 17.46 |
| ur | 10.17 | 9.53 | **6.10** | 25.60 |
| mk | 5.19 | 4.78 | **3.23** | 14.00 |
| te | 6.76 | 6.41 | **4.31** | 17.19 |
| ne | 12.76 | 11.82 | **8.06** | 23.19 |
| mr | 10.25 | 8.9 | **5.77** | 27.95 |
| sw | 15.68 | **7.76** | 8.90 | 44.82 |
| cy | 9.37 | 5.08 | **4.35** | 25.74 |
| uz | 8.40 | 5.46 | **3.92** | 15.33 |
| jv | 33.81 | **12.49** | 17.83 | 73.46 |
| su | 57.32 | **10.41** | 26.42 | 52.65 |
| si | 7.04 | 5.74 | **4.50** | 15.03 |
| am | 10.87 | 7.32 | **6.73** | 25.56 |
| ku | 159.39 | **2.95** | 126.40 | 23.35 |
| ug | 6.87 | 4.99 | **3.80** | 13.67 |
| Avg. | 15.65 | **6.26** | 10.11 | 25.66 |
| mt | 395.18 | **3.19** | 317.81 | 7.93 |
| bo | 9.45 | 274.66 | **3.99** | 26.74 |
| yo | 207.26 | **9.57** | 155.57 | 96.80 |
| Avg. | 203.96 | 95.81 | 159.12 | **43.82** |
| Total | 34.48 | **15.22** | 25.01 | 27.48 |{{< /table-caption >}}
> 🔼 표 15는 mBERT 모델을 사용하여 ConceptNet과 Glot 데이터셋에서 세 가지 다른 어댑터(Seq-bn, LORA, Seq-bn-inv)를 적용한 주제 분류 작업의 F1 점수를 비교한 결과입니다. 각 결과는 서로 다른 랜덤 시드를 사용하여 3회 독립적으로 실행한 결과의 평균값입니다.  이 표는 다양한 어댑터 아키텍처와 데이터셋 조합이 주제 분류 성능에 미치는 영향을 분석하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 15: F1 scores comparison across different adapters for mBERT in ConceptNet and Glot for topic classification. All results are averaged over 3 independent runs with different random seeds.
> </details>

{{< table-caption >}}
| Model | Task | Pre-Adapt Pearson (p-value) | Pre-Adapt Spearman (p-value) | Post-Adapt Pearson (p-value) | Post-Adapt Spearman (p-value) |
|---|---|---|---|---|---| 
| mBERT | TC | -0.09 (0.62) | -0.25 (0.18) | -0.66 (¡0.001) | -0.42 (0.02) |
|  | SA | -0.29 (0.12) | -0.15 (0.42) | -0.45 (0.01) | -0.23 (0.23) |
|  | NER | -0.28 (0.13) | -0.22 (0.24) | -0.54 (0.002) | -0.49 (0.006) |
| XLM-R | TC | -0.48 (0.007) | -0.68 (¡0.001) | -0.88 (¡0.001) | -0.20 (0.3) |
|  | SA | -0.47 (0.009) | -0.55 (0.002) | -0.64 (¡0.001) | -0.38 (0.04) |
|  | NER | -0.42 (0.02) | -0.62 (¡0.001) | -0.35 (0.06) | -0.28 (0.13) |{{< /table-caption >}}
> 🔼 표 16은 XLM-R 모델을 사용하여 ConceptNet과 Glot 데이터셋에서 주제 분류 작업에 대한 다양한 어댑터의 성능을 비교 분석한 결과를 보여줍니다.  세 가지 어댑터 구조 (Seq_bn, LORA, Seq_bn_inv)와 두 가지 데이터셋(ConceptNet, Glot)의 조합에 따른 F1 점수가 제시되어 있습니다. 각 실험은 서로 다른 난수 시드를 사용하여 세 번 독립적으로 수행되었으며, 표의 결과는 그 평균값을 나타냅니다.  본 표는 다양한 어댑터와 데이터셋 조합을 통해 XLM-R 모델의 주제 분류 성능에 미치는 영향을 정량적으로 비교 분석하는 데 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 16: F1 scores comparison across different adapters for XLM-R in ConceptNet and Glot for topic classification. All results are averaged over 3 independent runs with different random seeds.
> </details>

{{< table-caption >}}
| ISO | mBERT |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|
| **ISO** | **mBERT** |  |  |  |  |  |  |  |
|  |  | **ConceptNet** |  |  | **Glot** |  |  |  |
|  | **Base** | **Seq_bn** | **LoRA** | **Seq_bn_inv** | **Seq_bn** | **LoRA** | **Seq_bn_inv** | **FFT** |
| he | 79.79 | **83.99** | 82.87 | 82.11 | 83.26 | 83.43 | 83.91 | 83.24 |
| el | **79.47** | 77.95 | 79.14 | 78.12 | 76.65 | 77.92 | 76.64 | **84.81** |
| bg | **84.39** | 83.71 | 84.17 | 83.38 | 82.64 | 82.87 | 82.58 | **85.88** |
| th | 74.18 | **74.66** | 73.9 | 74.42 | 71.34 | 74.47 | 72.47 | **76.44** |
| ro | 86.95 | 87.86 | 86.45 | **88.37** | 85.8 | 86.63 | 86.8 | **89.06** |
| bn | 76.18 | 77.65 | 74.52 | 76.69 | 77.51 | **78.09** | 77.34 | 77.3 |
| te | 80.03 | **82.35** | 80.04 | 81.13 | 77.32 | 81.2 | 78.95 | 79.33 |
| ka | 76.28 | 73.26 | 74.26 | 74.07 | 75.68 | **78.23** | 75.19 | **79.82** |
| mk | 83.44 | 84.48 | 84.34 | 83.79 | 84.53 | 84.92 | **85.25** | 84.96 |
| da | 87.06 | 86.85 | 86.63 | **87.72** | 86.03 | 86.48 | 85.5 | 85.8 |
| sl | 83.6 | 85.07 | 83.75 | 86.22 | 86.71 | 85.39 | **86.73** | 86.43 |
| az | 81.09 | 83.72 | 82.53 | 83.38 | 82.93 | 82.55 | **84.29** | 82.01 |
| sk | 84.37 | 83.49 | 83.98 | **85.4** | 84.79 | 84.43 | 83.57 | 84.52 |
| ms | 84.31 | 84.65 | 84.1 | 82.94 | **85.4** | 84.59 | 83.39 | 84.38 |
| uz | 76.57 | 73.89 | 73.71 | 75.76 | **81.32** | 74.44 | 79.35 | **85.35** |
| ur | 76.7 | 73.7 | 74.85 | 74.76 | 76.06 | 75.26 | **76.94** | **78.18** |
| cy | 72.37 | 72.23 | 71.6 | 73.49 | **81.47** | 77.16 | 80.75 | **85.53** |
| lv | 82.28 | **83.63** | 82.42 | 82.45 | 83.48 | 82.56 | 80.94 | **85.02** |
| mr | 73.21 | **77.29** | 76.22 | 76.61 | 76.37 | 75.73 | 75.28 | **78.84** |
| ne | 73.72 | 77.55 | 74.62 | 76.02 | **81.59** | 75.21 | 80.8 | 79.11 |
| jv | 72.4 | 73.32 | **75.12** | 73.11 | 73.71 | 74.09 | 74.02 | **75.89** |
| sw | 69.17 | 70.53 | 69.89 | 70.21 | 73.93 | 69.05 | **77.15** | **85.89** |
| su | 76.15 | 77.42 | 77.62 | 77.0 | 78.21 | **79.2** | 78.63 | **79.97** |
| yo | 54.18 | 52.11 | 52.08 | 54.89 | 55.93 | 55.93 | **58.05** | **63.66** |
| Avg. | 77.67 | 78.39 | 77.87 | 78.42 | 79.28 | 78.74 | **79.35** | **81.73** |
| mt<sup class="ltx_sup"><i>†</i></sup> | 69.86 | 69.83 | 69.85 | 68.79 | 78.0 | 78.09 | **79.8** | **83.32** |
| ku<sup class="ltx_sup"><i>†</i></sup> | 28.76 | 23.78 | 15.71 | 19.93 | 46.41 | 40.22 | **46.85** | **52.82** |
| ug<sup class="ltx_sup"><i>†</i></sup> | 23.4 | 22.21 | 20.9 | 22.17 | 47.18 | 31.68 | **48.91** | **56.26** |
| si<sup class="ltx_sup"><i>†</i></sup> | 17.45 | 14.3 | 14.88 | 14.95 | **21.53** | 21.25 | 20.4 | 19.08 |
| am<sup class="ltx_sup"><i>†</i></sup> | 17.75 | 14.01 | 18.47 | 12.94 | 18.74 | **20.3** | 18.07 | 16.88 |
| bo<sup class="ltx_sup"><i>†</i></sup> | 12.59 | 11.08 | 9.48 | 6.33 | 36.67 | 28.36 | **39.17** | 33.53 |
| Avg. | 28.72 | 25.87 | 24.88 | 24.18 | 41.42 | 36.65 | **42.2** | **43.65** |
| Total avg. | 67.88 | 67.89 | 67.27 | 67.57 | 71.71 | 70.32 | **71.92** | **74.11** |{{< /table-caption >}}
> 🔼 본 표는 mBERT 및 XLM-R 모델에 대해 작업 성능과 데이터 양 간의 피어슨 및 스피어만 상관 관계를 보여줍니다.  '사전 적응' 열은 어댑터를 적용하기 전 모델의 사전 훈련 데이터 크기와 작업 성능 간의 상관 관계를 나타냅니다. '사후 적응' 열은 Seq_bn_inv 언어 어댑터를 사용하여 적응된 모델의 사전 훈련 및 적응 데이터 크기의 합과 작업 성능 간의 상관 관계를 나타냅니다.  본 분석은 사전 훈련 및 적응 데이터 크기가 작업 성능에 미치는 영향을 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 17: Pearson and Spearman Correlations for mBERT and XLM-R (Pre-Adapt and Post-Adapt) between task performance and data amounts. Post-Adapt is represented by the models adapted with the Seq_bn_inv language adapters and denote the correlation between the sum of the pre-training and adaptation data sizes and downstream task performance scores after the adaptation.
> </details>

{{< table-caption >}}
| ISO | XLM-R |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|
| | **XLM-R** |  |  |  |  |  |  |  |
| **ISO** |  | **ConceptNet** |  |  | **Glot** |  |  |  |
|  | **Base** | **Seq_bn** | **LoRA** | **Seq_bn_inv** | **Seq_bn** | **LoRA** | **Seq_bn_inv** | **FFT** |
| th | 87.93 | 87.19 | 87.22 | 85.99 | 86.97 | 86.8 | **88.5** | 84.21 |
| ro | 86.94 | 87.0 | 86.85 | **88.02** | 87.47 | 86.95 | 87.6 | **88.03** |
| bg | 86.55 | 86.0 | **87.81** | 86.41 | 86.46 | 86.33 | 86.19 | 87.53 |
| da | 86.04 | 84.94 | 83.7 | 84.26 | 86.47 | 84.88 | **86.41** | **87.06** |
| el | **86.74** | 85.59 | 85.64 | 84.32 | 85.77 | 85.28 | 86.6 | **88.1** |
| he | 85.02 | 84.9 | 83.8 | 84.79 | **86.62** | 84.19 | 83.36 | 84.67 |
| sk | **87.18** | 85.53 | 84.81 | 85.2 | 85.46 | 86.52 | 86.03 | 85.59 |
| sl | 85.47 | 86.24 | **86.95** | 86.28 | 84.94 | 86.67 | 85.28 | **88.12** |
| lv | 86.25 | 87.83 | 86.93 | **88.97** | 85.22 | 86.38 | 87.41 | 87.52 |
| ms | **88.12** | 87.11 | 85.82 | 85.81 | 87.94 | 85.21 | 87.94 | **89.49** |
| ka | 84.08 | **85.37** | 83.79 | 83.18 | 83.92 | 85.0 | 83.95 | 82.27 |
| bn | 80.29 | 81.11 | 80.85 | 82.09 | **83.56** | 82.59 | 83.38 | **84.95** |
| az | 84.05 | 85.86 | 84.24 | 85.07 | 84.43 | 85.16 | **86.39** | 86.08 |
| ur | **83.25** | 81.04 | 80.29 | 82.35 | 82.97 | 81.98 | 82.17 | **83.97** |
| mk | 86.45 | 86.41 | 86.99 | 85.45 | 86.94 | 85.97 | **87.15** | **88.15** |
| te | 83.58 | **83.64** | 84.26 | 83.13 | 82.43 | 84.13 | 83.43 | **85.65** |
| ne | 84.14 | 83.98 | 83.92 | 83.77 | 82.65 | **84.71** | 82.85 | 84.2 |
| si | 84.92 | 84.54 | 84.86 | 82.23 | 84.49 | 83.37 | **84.99** | 84.53 |
| mr | 81.03 | 82.84 | 81.34 | 80.08 | 82.2 | 79.54 | **84.23** | 84.21 |
| sw | 77.83 | 75.58 | 76.23 | 77.97 | 80.23 | 78.73 | **81.57** | **85.95** |
| cy | 79.54 | 78.44 | 80.1 | 78.99 | 78.83 | 79.15 | **81.37** | **85.17** |
| am | 77.5 | 78.4 | 77.93 | 77.91 | 80.67 | 77.52 | **81.51** | **84.22** |
| uz | 81.93 | 78.73 | 78.43 | 76.97 | **83.35** | 81.13 | 80.68 | **86.37** |
| ku | 13.49 | 14.09 | 15.76 | 17.28 | 68.57 | 46.29 | **73.97** | **81.72** |
| ug | 79.56 | 79.11 | 78.67 | 78.86 | 81.29 | **82.23** | 80.14 | **84.95** |
| jv | 81.35 | 79.32 | 82.23 | 81.43 | **83.59** | 81.84 | 81.74 | 81.2 |
| Avg. | 81.14 | 80.82 | 80.71 | 80.64 | 83.63 | 82.31 | **84.06** | **85.61** |
| mt<sup class="ltx_sup"><span class="ltx_text ltx_font_italic">‡</span></sup> | 64.56 | 63.62 | 61.43 | 64.43 | 77.39 | 69.74 | **77.92** | **84.35** |
| bo<sup class="ltx_sup"><span class="ltx_text ltx_font_italic">‡</span></sup> | 10.69 | 9.89 | 9.73 | 11.74 | 17.65 | **17.85** | 16.93 | **20.41** |
| yo<sup class="ltx_sup"><span class="ltx_text ltx_font_italic">‡</span></sup> | 28.29 | 26.06 | 16.07 | 24.6 | 54.13 | 35.24 | **59.44** | **67.13** |
| Avg. | 34.52 | 33.19 | 29.08 | 33.59 | 49.72 | 40.94 | **51.43** | **57.3** |
| Total avg. | 76.48 | 76.05 | 75.54 | 75.93 | 80.24 | 78.17 | **80.79** | **82.77** |{{< /table-caption >}}
> 🔼 표 18은 mBERT 모델을 사용하여 ConceptNet과 Glot 데이터셋에서 개체명 인식 작업에 대한 F1 점수 비교 결과를 보여줍니다.  각 결과는 서로 다른 난수 시드를 사용한 3번의 독립적인 실행에 대한 평균값입니다. 이 표는 다양한 어댑터 아키텍처(Seq_bn, LORA, Seq_bn_inv)와 두 가지 데이터 소스를 사용하여 모델 성능을 비교 분석한 결과를 제시하며, 어댑터 기반 접근 방식의 효과를 평가하는 데 도움을 줍니다.  특히, 각 어댑터 아키텍처가 ConceptNet과 Glot 데이터에서 개체명 인식 성능에 미치는 영향과, 데이터셋 유형에 따른 성능 차이를 분석하는 데 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 18: F1 scores comparison for mBERT in ConceptNet and Glot for named entity recognition. All results are averaged over 3 independent runs with different random seeds.
> </details>

{{< table-caption >}}
| Model | Task | Pre-Adapt | Pre-Adapt | Post-Adapt (Glot) | Post-Adapt (Glot) | Post-Adapt (CN) | Post-Adapt (CN) |
|---|---|---|---|---|---|---|---|
|  |  | P (p-value) | S (p-value) | P (p-value) | S (p-value) | P (p-value) | S (p-value) |
| mBERT | TC | 0.35 (_0.1_) | 0.53 (_0.008_) | 0.45 (_0.03_) | 0.32 (_0.13_) | 0.38 (_0.06_) | 0.55 (_0.006_) |
| XLM-R | TC | 0.28 (_0.16_) | 0.82 (_¡0.005_) | 0.55 (_0.002_) | 0.75 (_¡0.005_) | 0.28 (_0.15_) | 0.83 (_¡0.005_) |{{< /table-caption >}}
> 🔼 표 19는 XLM-R 모델을 사용하여 ConceptNet 및 Glot 데이터셋에서 개체명 인식 작업을 수행한 결과를 보여줍니다.  세 가지 다른 어댑터(Seq_bn, LORA, Seq_bn_inv) 아키텍처를 사용하여 각 언어에 대한 성능을 평가했습니다.  각 결과는 서로 다른 랜덤 시드를 사용하여 독립적으로 3회 실행한 평균값을 나타냅니다. ConceptNet과 Glot 데이터셋 모두에서 어댑터 기반 방법의 성능을 비교하여 어떤 데이터셋과 어댑터 조합이 개체명 인식 작업에 가장 효과적인지를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 19: F1 scores for XLM-R across ConceptNet and Glot for named entity recognition. All results are averaged over 3 independent runs with different random seeds.
> </details>

{{< table-caption >}}
| ISO | mBERT |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|---| 
| **ISO** | **mBERT** |  |  |  |  |  |  |  |  |
|  |  | **ConceptNet** |  |  | **Glot** |  |  | **Fusion** |  |
|  | **Base** | **Seq_bn** | **LoRA** | **Seq_bn_inv** | **Seq_bn** | **LoRA** | **Seq_bn_inv** | **Seq_bn** | **Seq_bn_inv** |
| he | 84.46 | 84.1 | 84.24 | 84.59 | 83.57 | 84.22 | 83.89 | **84.84** | 84.53 |
| el | 90.16 | 90.11 | 90.45 | 90.27 | 89.9 | **90.5** | 89.35 | 90.3 | 90.0 |
| bg | 91.25 | 91.64 | 91.64 | 91.48 | 91.64 | 91.59 | 91.56 | **91.78** | 91.76 |
| th | 67.34 | 65.65 | 66.79 | 66.68 | 67.22 | **67.8** | 66.95 | 67.36 | 67.57 |
| ro | 91.61 | 91.88 | 91.85 | 91.89 | 91.74 | 91.65 | 91.79 | 91.69 | **92.17** |
| bn | 95.46 | 96.07 | 95.82 | **96.49** | 96.42 | 96.03 | 96.3 | 95.86 | 96.1 |
| te | 75.41 | 76.17 | 76.94 | 75.29 | 75.51 | 74.69 | 75.37 | 76.53 | **77.02** |
| ka | **86.17** | 86.07 | 86.11 | 86.05 | 85.32 | 85.89 | 85.71 | 86.05 | 86.07 |
| mk | 92.43 | 92.09 | 92.3 | 92.2 | **92.62** | 92.2 | 92.02 | 91.61 | 91.98 |
| da | 89.76 | 90.08 | **90.33** | 89.74 | 90.02 | 89.72 | 88.99 | 89.41 | 89.48 |
| sl | 92.61 | 92.85 | 92.82 | 92.78 | **92.93** | 92.62 | 92.77 | 92.71 | 92.56 |
| az | 87.81 | 87.54 | 87.8 | **88.23** | 87.27 | 87.3 | 87.3 | 86.46 | 87.22 |
| sk | 90.87 | 90.88 | 90.89 | 90.96 | 90.83 | **91.3** | 90.99 | **91.04** | 90.84 |
| ms | 93.26 | 93.0 | 92.98 | 92.95 | 93.16 | **93.93** | 93.47 | 92.65 | 92.59 |
| uz | 86.48 | 86.69 | 86.58 | 86.33 | 86.87 | 86.46 | 87.73 | 87.5 | **88.45** |
| ur | 94.37 | 94.2 | 93.93 | 94.23 | 94.4 | 94.26 | 94.29 | 94.25 | **94.85** |
| cy | 88.72 | 89.34 | 89.35 | 89.05 | 89.18 | 89.36 | **90.02** | 88.95 | 88.71 |
| lv | 92.78 | 92.82 | 93.25 | 93.16 | 92.7 | 92.94 | 92.64 | **93.34** | 92.66 |
| mr | **86.34** | 86.19 | 85.97 | 86.29 | 86.32 | 86.07 | 84.35 | 86.24 | 86.22 |
| ne | 66.45 | 61.96 | 61.75 | 64.56 | **71.12** | 69.37 | 70.46 | 70.18 | 66.89 |
| jv | 52.87 | 62.83 | 61.76 | **65.3** | 63.97 | 58.73 | 63.34 | 57.21 | 58.67 |
| sw | 83.41 | 83.44 | 83.99 | 83.54 | 83.4 | 83.79 | **84.07** | 81.68 | 81.96 |
| su | 52.62 | 55.88 | 53.72 | 57.53 | 49.48 | 50.79 | 51.6 | 57.12 | **57.74** |
| yo | 79.0 | 83.02 | **83.87** | 83.1 | 81.48 | 79.58 | 79.74 | 79.81 | 78.54 |
| Avg. | 83.82 | 84.35 | 84.38 | **84.7** | 84.46 | 84.2 | 84.36 | 84.36 | 84.36 |
| mt† | 58.3 | 49.01 | 51.58 | 50.46 | 60.55 | 61.41 | **64.93** | 60.32 | 62.93 |
| ku† | 52.34 | 60.41 | **59.92** | 59.39 | 59.9 | 52.93 | 51.51 | 52.33 | 52.4 |
| ug† | 34.1 | 35.33 | 33.07 | 34.56 | 40.2 | 36.24 | 37.62 | 42.93 | **44.05** |
| si† | 16.59 | 13.41 | 14.06 | 13.94 | 22.97 | 14.58 | 19.94 | 20.7 | **24.24** |
| am† | 37.88 | 33.02 | 33.7 | 35.23 | 32.72 | 46.46 | **46.49** | 36.94 | 32.45 |
| bo† | **56.04** | 56.02 | 55.57 | 55.29 | 53.92 | 55.45 | 53.38 | 52.03 | 53.53 |
| Avg. | 42.54 | 41.2 | 41.32 | 41.48 | 45.04 | 44.51 | **45.64** | 44.21 | 44.93 |
| Total avg. | 75.56 | 75.72 | 75.77 | 76.05 | 76.58 | 76.26 | **76.62** | 76.33 | 76.47 |{{< /table-caption >}}
> 🔼 이 표는 mBERT와 XLM-R 모델에 대해 작업 성능과 데이터 양 간의 피어슨과 스피어먼 상관 관계를 보여줍니다.  특히, 사전 적응(Pre-Adapt)과 사후 적응(Post-Adapt) 모두에 대한 상관 관계가 제시됩니다. 사후 적응의 경우 Seq_bn_inv 언어 어댑터를 사용하여 모델을 적응시켰으며, 사전 학습 데이터와 적응 데이터 크기의 합계와 작업 성능 점수 간의 상관 관계를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 20: Pearson and Spearman Correlations for mBERT and XLM-R (Pre-Adapt and Post-Adapt) between task performance and data amounts. Post-Adapt is represented by the models adapted with the Seq_bn_inv language adapters and denote the correlation between the sum of the pre-training and adaptation data sizes and downstream task performance scores after the adaptation.
> </details>

{{< table-caption >}}
| ISO | XLM-R |  |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|---|---|
| **ISO** | **XLM-R** |  |  |  |  |  |  |  |  |  |
|  |  | **ConceptNet** |  |  | **Glot** |  |  | **Fusion** |  |  |
|  | **Base** | **Seq_bn** | **LoRA** | **Seq_bn_inv** | **Seq_bn** | **LoRA** | **Seq_bn_inv** | **Seq_bn** | **Seq_bn_inv** |
| th | 66.55 | 66.4 | **66.85** | 66.76 | 66.63 | 65.29 | 66.2 | 65.89 | 66.82 |
| ro | 91.78 | 91.79 | 91.78 | 91.92 | 92.0 | 91.87 | **92.18** | 92.02 | 92.05 |
| bg | 91.09 | 91.22 | 91.36 | **91.48** | 91.34 | 91.4 | 91.43 | 90.91 | 91.43 |
| da | 89.58 | 89.57 | 89.54 | 89.45 | 89.44 | 89.85 | 89.72 | 89.85 | **89.89** |
| el | 90.03 | 90.32 | 89.88 | 90.14 | 89.89 | 90.02 | 90.02 | 90.18 | **90.5** |
| he | 85.56 | 85.48 | 85.45 | 84.99 | 84.92 | **85.69** | 85.28 | 85.35 | 85.4 |
| sk | 91.36 | 91.19 | 91.21 | 91.26 | 91.32 | 91.45 | **91.49** | 91.4 | 91.24 |
| sl | 92.28 | **92.58** | 92.16 | 92.41 | 92.36 | 92.05 | 92.33 | 92.21 | 92.12 |
| lv | 92.64 | 92.73 | 92.65 | 92.95 | 92.84 | 92.88 | **93.1** | 92.99 | 92.93 |
| ms | 92.0 | 92.36 | 91.65 | 92.28 | 92.4 | 92.06 | 91.9 | **92.67** | 91.82 |
| ka | 86.96 | 86.77 | 86.88 | **87.73** | 87.31 | 87.66 | 87.37 | 86.59 | 87.33 |
| bn | 95.87 | 95.66 | 95.9 | 96.06 | 96.07 | 96.13 | 96.09 | 95.57 | **96.23** |
| az | 86.13 | 85.34 | 86.47 | 86.53 | 87.03 | 86.63 | **87.59** | 86.23 | 86.38 |
| ur | 95.02 | 94.57 | **95.04** | 94.86 | 94.43 | 94.89 | 94.27 | 94.4 | 94.56 |
| mk | 92.97 | 92.47 | **93.26** | 92.28 | 92.83 | 92.68 | 92.72 | 92.32 | 92.46 |
| te | 74.67 | 73.64 | **76.07** | 74.27 | 75.18 | 74.38 | 74.82 | 72.92 | 73.91 |
| ne | 55.47 | 53.0 | 60.02 | 60.0 | 59.08 | 54.99 | 56.61 | **67.84** | 67.34 |
| si | 63.85 | 58.43 | 63.83 | 57.43 | 68.15 | 60.34 | 66.2 | 71.94 | **73.66** |
| mr | 85.92 | 85.86 | 85.5 | 85.77 | 84.75 | 85.25 | **86.1** | 85.8 | 85.52 |
| sw | 84.34 | 83.31 | 84.37 | 84.26 | **84.72** | 84.4 | 84.47 | 84.56 | 83.5 |
| cy | 89.33 | 88.9 | 88.88 | 88.97 | 89.3 | **89.72** | 89.41 | 89.4 | 89.36 |
| am | 51.22 | 49.9 | 49.29 | 48.18 | 52.57 | 47.17 | 51.67 | **55.0** | 52.55 |
| uz | 89.64 | 88.66 | 87.51 | 87.89 | 88.64 | **89.97** | 86.86 | 89.05 | 87.64 |
| ku | 35.34 | 39.53 | 42.99 | 43.83 | 40.41 | 31.43 | 29.4 | **58.02** | 56.93 |
| ug | 42.36 | 52.63 | 50.67 | 51.98 | 49.88 | 50.5 | 52.63 | 53.12 | **58.5** |
| jv | 42.99 | 45.64 | 44.7 | 50.87 | 46.51 | 44.7 | 47.96 | **63.53** | 58.81 |
| su | 33.07 | 38.4 | 42.26 | 48.32 | 41.47 | 39.76 | 42.89 | **52.53** | 49.61 |
| Avg. | 77.33 | 77.64 | 78.38 | 78.62 | 78.57 | 77.52 | 78.17 | **80.83** | 80.68 |
| mt‡ | 46.31 | 32.69 | 40.11 | 32.13 | 48.03 | 41.54 | 53.57 | **64.31** | 57.57 |
| bo‡ | 43.51 | 44.29 | 44.55 | 46.41 | 41.86 | 39.64 | 38.27 | **48.15** | 47.55 |
| yo‡ | 73.54 | 71.2 | 73.46 | 74.59 | 73.3 | 74.87 | 75.09 | 73.04 | **75.8** |
| Avg. | 54.45 | 49.39 | 52.71 | 51.04 | 54.4 | 52.01 | 55.64 | **61.83** | 60.31 |
| Total avg. | 75.05 | 74.82 | 75.81 | 75.87 | 76.16 | 74.97 | 75.92 | **78.93** | 78.65 |{{< /table-caption >}}
> 🔼 본 표는 mBERT 모델을 사용하여 ConceptNet과 Glot 데이터셋에서 감정 분석 작업에 대한 다양한 어댑터(Seq-bn, LORA, Seq-bn-inv)의 성능을 비교 분석한 결과를 보여줍니다. ConceptNet과 Glot 데이터셋에서 각 어댑터의 F1 스코어를 제시하며, 각 결과는 서로 다른 난수 시드를 사용하여 3번 독립적으로 실행한 결과의 평균값입니다. 이를 통해 각 데이터셋과 어댑터 조합에 따른 감정 분석 성능의 차이를 보다 정확하게 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 21: F1 scores comparison across different adapters for mBERT in ConceptNet and Glot for sentiment analysis. All results are averaged over 3 independent runs with different random seeds.
> </details>

{{< table-caption >}}
| Model | Task | Pre-Adapt | Pre-Adapt | Post-Adapt (Glot) | Post-Adapt (Glot) | Post-Adapt (CN) | Post-Adapt (CN) |
|---|---|---|---|---|---|---|---| 
|  |  | P (p-value) | S (p-value) | P (p-value) | S (p-value) | P (p-value) | S (p-value) |
| mBERT | NER | 0.32 (0.1) | 0.32 (0.1) | 0.42 (0.04) | 0.29 (0.2) | 0.20 (0.3) | 0.44 (0.03) |
| XLM-R | NER | 0.31 (0.1) | 0.58 (0.002) | 0.31 (0.1) | 0.61 (¡0.005) | 0.32 (0.1) | 0.60 (¡0.005) |{{< /table-caption >}}
> 🔼 표 22는 XLM-R 언어 모델을 사용하여 ConceptNet과 Glot 데이터셋에서 세 가지 다른 어댑터(Seq-bn, LORA, Seq-bn-inv)를 적용한 감정 분석 결과를 보여줍니다. 세 가지 독립적인 실행 결과의 평균값을 제시하며, 각 언어에 대한 ConceptNet과 Glot 데이터셋의 성능을 비교합니다.  다양한 어댑터 아키텍처가 저자원 언어의 감정 분석 성능에 미치는 영향을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 22: F1 scores comparison across different adapters for XLM-R in ConceptNet and Glot for sentiment analysis. All results are averaged over 3 independent runs with different random seeds.
> </details>

{{< table-caption >}}
| ISO | mBERT |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|
| **ISO** | **mBERT** |  |  |  |  |  |  |  |
|  |  | **ConceptNet** |  |  | **Glot** |  |  |  |
|  | **Base** | **Seq_bn** | **LoRA** | **Seq_bn_inv** | **Seq_bn** | **LoRA** | **Seq_bn_inv** | **FFT** |
| he | 91.42 | 91.55 | 90.44 | 90.81 | 90.79 | 90.87 | **91.58** | 90.6 |
| el | **86.35** | 86.27 | 86.05 | 86.22 | 84.88 | 84.95 | 84.52 | 86.38 |
| bg | 88.82 | 89.41 | 89.17 | **89.54** | 88.76 | 88.65 | 89.2 | 89.99 |
| th | 81.68 | 81.97 | 81.92 | 82.45 | 82.57 | 82.0 | **83.23** | 83.19 |
| ro | 92.87 | 92.67 | 92.62 | 92.64 | 93.13 | **92.98** | 92.96 | 93.7 |
| bn | 92.28 | 92.16 | 92.6 | 91.88 | 92.26 | 92.56 | **92.57** | 92.48 |
| te | 83.49 | 83.29 | 84.17 | 85.01 | **85.55** | 84.45 | 85.26 | 88.41 |
| ka | 78.12 | 78.1 | 76.68 | 76.05 | 80.03 | 80.23 | **81.24** | 86.97 |
| mk | 62.47 | **69.01** | 66.4 | 62.07 | 67.54 | 65.06 | 65.21 | 68.98 |
| da | 95.71 | 95.33 | 95.77 | 95.33 | 95.95 | **96.15** | 96.09 | 96.84 |
| sl | 85.71 | 86.46 | 86.28 | 85.81 | 86.79 | 86.4 | **87.83** | 88.66 |
| az | 79.42 | 79.59 | 79.72 | 80.03 | 79.62 | **80.15** | 80.13 | 81.44 |
| sk | 91.11 | 88.86 | 89.9 | 89.73 | 90.87 | 91.16 | **92.18** | 91.08 |
| ms | 91.5 | 92.03 | 91.87 | 91.99 | 92.06 | 91.7 | **92.57** | 93.83 |
| uz | 86.84 | 85.67 | 86.76 | 85.85 | 86.52 | 86.36 | **86.85** | 88.33 |
| ur | 82.43 | 81.89 | 82.01 | 82.13 | 82.69 | 82.66 | **82.72** | 83.81 |
| cy | 87.28 | 86.99 | 87.82 | 86.15 | 87.71 | **87.76** | 87.42 | 88.53 |
| lv | 75.41 | 75.66 | 73.99 | 74.71 | 76.32 | 75.41 | **76.65** | 79.24 |
| mr | 88.7 | 88.76 | 89.0 | 88.67 | **89.43** | 89.13 | 88.97 | 90.43 |
| ne | 59.51 | 51.46 | **67.17** | 55.31 | 56.77 | 59.35 | 63.19 | 63.47 |
| jv | 75.38 | 74.24 | 74.75 | 73.94 | **76.16** | 75.7 | 75.43 | 75.44 |
| sw | 57.71 | 54.25 | 57.24 | 52.9 | 65.05 | 62.21 | **69.64** | 54.6 |
| su | 82.13 | 84.25 | 84.62 | 83.33 | 84.42 | **84.75** | 83.99 | 84.06 |
| yo | 76.1 | 75.66 | 75.24 | 75.35 | 75.93 | 75.43 | **77.85** | 77.32 |
| Avg. | 82.18 | 81.9 | 82.59 | 81.58 | 82.99 | 82.75 | **83.64** | 84.07 |
| mt† | 65.24 | 65.68 | 62.82 | 66.88 | 68.79 | **73.87** | 65.34 | 74.11 |
| ku† | 84.2 | 82.82 | 83.97 | 83.37 | 85.14 | 84.46 | **86.14** | 85.55 |
| ug† | 70.94 | 68.35 | 72.67 | 72.19 | 76.91 | 71.35 | **80.4** | 76.63 |
| si† | 64.97 | 64.89 | 65.01 | 64.67 | 65.42 | **66.02** | 65.62 | 66.26 |
| am† | 61.45 | 62.02 | 60.87 | 61.45 | 60.3 | 61.62 | **63.81** | 59.48 |
| bo† | 79.4 | 79.12 | 79.38 | 80.67 | **83.27** | 82.33 | 82.14 | 81.77 |
| Avg. | 71.03 | 70.48 | 70.79 | 71.54 | 73.3 | 73.27 | **73.91** | 73.97 |
| Total avg. | 79.95 | 79.61 | 80.23 | 79.57 | 81.05 | 80.86 | **81.69** | 82.05 |{{< /table-caption >}}
> 🔼 본 표는 mBERT와 XLM-R 모델에 대해 작업 성능과 데이터 양 간의 피어슨과 스피어먼 상관 관계를 보여줍니다.  Pre-Adapt 열은 어댑터를 적용하기 전의 모델의 사전 학습 데이터 크기와 작업 성능 간의 상관 관계를 나타내고, Post-Adapt 열은 Seq_bn_inv 언어 어댑터를 사용하여 어댑터를 적용한 후 사전 학습 및 적응 데이터 크기의 합과 작업 성능 간의 상관 관계를 나타냅니다.  각 모델의 작업(TC, SA, NER)에 대한 상관 관계가  p-값과 함께 제시됩니다.
> <details>
> <summary>read the caption</summary>
> Table 23: Pearson and Spearman Correlations for mBERT and XLM-R (Pre-Adapt and Post-Adapt) between task performance and data amounts. Post-Adapt is represented by the models adapted with the Seq_bn_inv language adapters and denote the correlation between the sum of the pre-training and adaptation data sizes and downstream task performance scores after the adaptation.
> </details>

{{< table-caption >}}
| ISO | XLM-R |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|
| **ISO** | **XLM-R** |  |  |  |  |  |  |  |
|  | **ConceptNet** |  |  | **Glot** |  |  |  |  |
|  | **Base** | **Seq_bn** | **LoRA** | **Seq_bn_inv** | **Seq_bn** | **LoRA** | **Seq_bn_inv** | **FFT** |
| th | 88.18 | 88.26 | 88.43 | **88.46** | 88.11 | 88.31 | 88.13 | 86.39 |
| ro | 94.37 | 94.84 | 95.03 | **95.04** | 94.74 | 94.67 | 95.03 | 94.55 |
| bg | 91.36 | 90.66 | **91.43** | 91.41 | 91.26 | 90.93 | 90.65 | 90.79 |
| da | 98.04 | 97.84 | **98.13** | 98.02 | 98.09 | 98.04 | 97.98 | 97.82 |
| el | 88.82 | 88.92 | **88.98** | 88.73 | 88.19 | 88.25 | 88.61 | 88.75 |
| he | 91.26 | 89.66 | **91.81** | 91.25 | 90.48 | 90.27 | 90.85 | 90.2 |
| sk | **94.6** | 93.86 | 93.87 | 93.43 | 93.22 | 93.72 | 93.44 | 94.03 |
| sl | 93.75 | 93.46 | **94.32** | 92.68 | 94.23 | 93.57 | 93.86 | 92.73 |
| lv | 83.3 | **83.78** | 83.36 | 83.83 | 82.47 | 83.12 | 83.65 | 82.97 |
| ms | 95.51 | 95.27 | **95.66** | 95.57 | 95.44 | 95.29 | 95.53 | 95.26 |
| ka | **91.92** | 91.51 | 90.8 | 91.21 | **91.92** | 91.11 | 91.41 | 93.33 |
| bn | 93.78 | 94.14 | 94.3 | **94.46** | 94.13 | 94.1 | 94.43 | 94.41 |
| az | 84.05 | 84.05 | 84.05 | 83.98 | 84.32 | 84.2 | **84.74** | 85.19 |
| ur | 85.6 | 85.99 | 85.67 | 85.85 | 85.89 | **86.7** | 86.25 | 87.27 |
| mk | 70.96 | 69.22 | 67.05 | 69.45 | **73.9** | 70.74 | 72.31 | 71.68 |
| te | 89.72 | 89.15 | 89.59 | 89.22 | 89.56 | 89.72 | **89.9** | 90.92 |
| ne | 64.6 | **69.37** | 64.06 | 63.02 | 67.49 | 68.38 | 68.65 | 65.46 |
| si | 92.49 | 92.59 | 92.18 | **93.21** | 92.49 | 91.78 | 91.96 | 92.85 |
| mr | 91.17 | 91.8 | 91.9 | 91.8 | 91.87 | **92.36** | 91.8 | 92.43 |
| sw | 70.08 | 65.37 | 77.11 | 75.3 | **79.52** | 77.24 | 74.45 | 83.84 |
| cy | 90.83 | 91.01 | 90.57 | 90.65 | 91.12 | 90.88 | **91.36** | 91.01 |
| am | 86.15 | 83.77 | 84.2 | 82.88 | 87.04 | **87.9** | 87.7 | 87.49 |
| uz | 87.63 | 88.24 | 88.37 | 88.13 | **88.47** | 87.98 | 88.39 | 90.08 |
| ku | 89.39 | 89.73 | 89.08 | 89.78 | 92.57 | 89.09 | **93.31** | 95.31 |
| ug | 88.97 | 88.88 | 89.91 | 87.64 | 88.81 | **90.01** | 89.65 | 91.72 |
| jv | 76.51 | 77.34 | 77.01 | 77.14 | 76.51 | 76.79 | **77.65** | 75.53 |
| su | 88.15 | 82.66 | 85.17 | 84.41 | 89.69 | **90.34** | 89.69 | 89.03 |
| Avg. | 87.45 | 87.09 | 87.48 | 87.28 | **88.2** | 87.98 | **88.2** | 88.56 |
| mt‡ | 55.63 | 55.19 | 55.32 | 54.13 | **69.4** | 63.15 | 69.31 | 70.38 |
| bo‡ | 51.81 | 47.33 | 51.07 | 49.34 | **52.92** | 50.9 | 50.69 | 55.19 |
| yo‡ | 74.73 | 73.4 | 73.6 | 75.09 | 75.5 | 72.0 | **77.65** | 78.99 |
| Avg. | 60.72 | 58.64 | 60.00 | 59.52 | **65.94** | 62.02 | 65.88 | 68.19 |
| Total avg. | 84.78 | 84.24 | 84.73 | 84.50 | **85.98** | 85.38 | 85.97 | 86.52 |{{< /table-caption >}}
> 🔼 표 24는 다양한 대규모 언어 모델의 주제 분류(TC) 성능을 보여줍니다. Ji et al.(2024)의 연구에서 보고된 바와 같이 3-shot 프롬프팅 방식을 사용하여 결과를 얻었습니다. Adelani et al.(2024a)의 연구에서 제시된 GPT-3.5와 GPT-4의 결과는 제로샷 설정에서 얻은 결과입니다. 이 표는 대규모 모델의 TC 작업 성능을 비교 분석하는 데 유용합니다. 각 모델의 성능을 숫자로 제시하여 직관적으로 비교할 수 있게 합니다. 특히 3-shot 프롬프팅과 제로샷 설정에서의 성능 차이를 명확히 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 24: F1 Scores for All Large-Scale Models on TC. The results are based on 3-shot prompting, as reported by Ji et al. (2024). GPT-3.5 and GPT-4 results are zero-shot, obtained from Adelani et al. (2024a).
> </details>

{{< table-caption >}}
| Model | Task | Pre-Adapt P (p-value) | Pre-Adapt S (p-value) | Post-Adapt (Glot) P (p-value) | Post-Adapt (Glot) S (p-value) | Post-Adapt (CN) P (p-value) | Post-Adapt (CN) S (p-value) |
|---|---|---|---|---|---|---|---| 
| mBERT | SA | 0.45 (_0.03_) | 0.50 (_0.01_) | 0.38 (_0.07_) | 0.41 (_0.05_) | 0.39 (_0.06_) | 0.52 (_0.009_) |
| XLM-R | SA | 0.36 (_0.07_) | 0.47 (_0.01_) | 0.32 (_0.1_) | 0.33 (_0.1_) | 0.38 (_0.05_) | 0.52 (_0.005_) |{{< /table-caption >}}
> 🔼 표 25는 Asai 외의 연구(2023)의 BUFFET 벤치마크에서 8개의 중복 언어에 대한 3-샷 NER 결과를 보여줍니다. GPT-3.5의 점수는 두 개의 언어에 대해서만 제공됩니다. 이 표는 다양한 대규모 언어 모델(LLM)의 몇몇 샷 학습 성능을 비교 분석하는 섹션의 일부입니다.  각 모델의 성능을 숫자로 명확하게 제시하여 저자들의 연구 결과를 뒷받침합니다.
> <details>
> <summary>read the caption</summary>
> Table 25: Three-shot NER results across eight overlapping languages from BUFFET Asai et al. (2023). The scores for GPT-3.5 are only provided for two languages.
> </details>

{{< table-caption >}}
|           | GPT-3.5-turbo-0613 | GPT-4-0613 | LLaMAX2-7B-Alpaca | Llama-2-7b-chat-hf | Meta-Llama-3-8B | Meta-Llama-3.1-8B | Qwen1.5-7B | Qwen2-7B | bloom-7b1 | bloomz-7b1 | gemma-2-9b | gemma-7b | mala-500-10b-v1 | mala-500-10b-v2 | occiglot-7b-eu5 | xglm-7.5B | yayi-7b-llama2 |
| :--------- | :----------------- | :---------- | :----------------- | :---------------- | :-------------- | :--------------- | :----------- | :--------- | :-------- | :--------- | :----------- | :-------- | :--------------- | :--------------- | :--------------- | :---------- | :--------------- |
| am         | 24.14              | 38.74       | 7.64               | 5.41              | 38.03           | 40.43            | 13.57        | 23.68       | 7.32      | 8.27       | 41.19         | 43.02      | 5.71             | 9.03             | 6.85             | 7.86        | 3.59             |
| az         | 52.17              | 44.27       | 30.81              | 20.54             | 73.78           | 71.97            | 51.86        | 65.86       | 10.08     | 16.68      | 57.95         | 68.79      | 5.71             | 5.71             | 31.37            | 26.56       | 17.55            |
| bn         | 54.29              | 50.55       | 23.79              | 9.35              | 65.89           | 63.43            | 42.62        | 66.08       | 10.75     | 20.93      | 51.22         | 66.91      | 5.71             | 5.69             | 22.42            | 28.25       | 12.99            |
| bo         | 2.90               | 1.94        | 3.69               | 4.63              | 40.80           | 48.83            | 10.15        | 12.41       | 6.44      | 10.56      | 12.12         | 20.23      | 5.71             | 3.63             | 11.65            | 7.06        | 6.61             |
| bg         | 54.80              | 58.33       | 31.47              | 29.92             | 64.95           | 63.53            | 55.15        | 77.06       | 20.17     | 16.58      | 51.85         | 63.26      | 5.71             | 5.23             | 44.70            | 41.81       | 24.77            |
| ku         | 38.74              | 38.10       | 19.71              | 7.67              | 68.26           | 65.47            | 21.71        | 33.20       | 10.26     | 8.63       | 33.49         | 44.59      | 5.71             | 6.86             | 14.07            | 9.31        | 7.81             |
| cy         | 43.08              | 42.47       | 26.76              | 18.08             | 68.75           | 68.69            | 37.47        | 49.93       | 10.45     | 18.09      | 50.38         | 56.87      | 5.71             | 5.71             | 26.21            | 17.57       | 19.37            |
| da         | 52.71              | 52.17       | 33.17              | 34.03             | 73.03           | 73.73            | 57.73        | 75.95       | 17.85     | 21.90      | 45.05         | 71.14      | 5.71             | 5.39             | 49.20            | 56.88       | 32.02            |
| el         | 54.29              | 60.27       | 21.84              | 21.69             | 70.22           | 73.70            | 46.99        | 63.73       | 11.97     | 11.90      | 39.08         | 67.20      | 5.71             | 5.71             | 31.48            | 55.80       | 20.84            |
| he         | 56.84              | 51.09       | 24.39              | 17.55             | 69.01           | 69.80            | 46.93        | 70.07       | 10.87     | 8.53       | 44.35         | 64.03      | 5.71             | 4.76             | 22.82            | 10.66       | 9.51             |
| jv         | 21.05              | 21.05       | 28.49              | 21.31             | 66.73           | 69.39            | 49.99        | 50.76       | 17.90     | 25.19      | 59.48         | 57.33      | 5.71             | 2.20             | 34.05            | 44.85       | 19.65            |
| ka         | 47.19              | 43.68       | 18.37              | 15.25             | 68.58           | 63.50            | 32.76        | 52.02       | 3.50      | 14.76      | 58.73         | 69.17      | 5.71             | 8.13             | 25.17            | 9.35        | 13.24            |
| lv         | 54.29              | 53.76       | 31.62              | 23.85             | 69.79           | 70.63            | 55.05        | 67.69       | 12.70     | 17.38      | 45.97         | 69.24      | 8.21             | 3.13             | 34.20            | 23.25       | 23.91            |
| mr         | 52.71              | 51.09       | 19.90              | 14.04             | 64.84           | 63.07            | 39.41        | 56.66       | 26.78     | 29.62      | 27.30         | 56.58      | 5.71             | 5.83             | 19.63            | 23.24       | 9.59             |
| mk         | 52.71              | 60.75       | 28.98              | 26.75             | 66.66           | 68.33            | 55.99        | 75.87       | 12.91     | 16.69      | 55.62         | 64.88      | 3.97             | 3.49             | 40.23            | 40.43       | 22.65            |
| mt         | 44.27              | 50.55       | 29.18              | 23.07             | 63.25           | 67.22            | 44.26        | 56.10       | 11.45     | 20.18      | 43.93         | 62.54      | 5.71             | 5.71             | 34.33            | 28.45       | 24.09            |
| ne         | 55.83              | 52.71       | 21.49              | 18.42             | 62.32           | 62.69            | 42.96        | 54.99       | 10.12     | 19.45      | 15.71         | 62.31      | 5.62             | 4.07             | 25.79            | 31.47       | 18.61            |
| ro         | 51.64              | 54.80       | 34.88              | 31.49             | 70.19           | 72.20            | 56.43        | 74.64       | 20.10     | 20.76      | 52.51         | 69.08      | 5.71             | 5.71             | 47.32            | 43.15       | 30.92            |
| si         | 23.38              | 62.63       | 8.66               | 4.81              | 60.25           | 57.45            | 12.49        | 29.29       | 5.98      | 9.38       | 46.12         | 65.92      | 6.60             | 2.20             | 10.82            | 5.48        | 5.71             |
| sk         | 52.17              | 52.71       | 28.65              | 29.75             | 70.57           | 72.77            | 55.40        | 74.63       | 20.27     | 17.58      | 35.52         | 68.94      | 5.71             | 8.49             | 43.66            | 39.12       | 27.70            |
| sl         | 53.76              | 47.76       | 33.60              | 31.05             | 75.67           | 70.18            | 55.53        | 63.56       | 11.10     | 17.18      | 48.42         | 67.87      | 9.22             | 3.30             | 40.19            | 30.21       | 28.09            |
| su         | 26.38              | 20.26       | 28.22              | 23.89             | 63.50           | 67.46            | 46.31        | 58.94       | 17.55     | 21.68      | 60.68         | 65.78      | 5.71             | 7.69             | 32.18            | 44.52       | 21.59            |
| sw         | 55.83              | 46.62       | 28.24              | 14.01             | 68.95           | 68.37            | 40.51        | 51.05       | 12.91     | 22.41      | 48.61         | 58.78      | 5.71             | 6.70             | 29.03            | 45.91       | 11.88            |
| te         | 57.84              | 50.00       | 5.92               | 5.78              | 64.72           | 62.36            | 27.29        | 55.69       | 16.89     | 20.13      | 47.24         | 68.93      | 5.71             | 5.17             | 12.91            | 49.59       | 4.73             |
| th         | 53.24              | 49.45       | 16.94              | 20.88             | 77.50           | 75.40            | 46.57        | 67.38       | 6.25      | 16.62      | 45.24         | 58.64      | 5.71             | 7.82             | 35.27            | 50.01       | 21.98            |
| ug         | 44.27              | 46.04       | 6.53               | 6.90              | 66.23           | 62.22            | 12.37        | 54.64       | 9.29      | 11.72      | 33.74         | 45.77      | 7.54             | 3.66             | 16.20            | 7.76        | 7.13             |
| ur         | 53.24              | 65.79       | 22.87              | 15.07             | 67.80           | 67.53            | 39.13        | 61.90       | 23.50     | 23.33      | 29.04         | 56.48      | 5.71             | 6.61             | 29.62            | 41.90       | 12.23            |
| uz         | 44.87              | 34.82       | 29.50              | 13.49             | 69.53           | 68.35            | 33.53        | 54.55       | 10.05     | 13.89      | 56.50         | 65.44      | 5.71             | 11.34            | 26.86            | 15.93       | 10.11            |
| yo         | 22.61              | 16.22       | 18.17              | 11.26             | 50.05           | 46.74            | 25.36        | 30.44       | 14.08     | 21.90      | 35.16         | 37.11      | 8.75             | 7.65             | 18.71            | 16.97       | 10.23            |
| ms         | 49.45              | 55.83       | 30.46              | 27.35             | 74.10           | 73.28            | 56.74        | 76.05       | 11.13     | 23.31      | 55.96         | 69.52      | 5.71             | 5.71             | 40.15            | 46.19       | 27.33            |
| Total avg. | 45.02              | 45.82       | 23.13              | 18.24             | 65.80           | 65.62            | 40.41        | 56.83       | 13.02     | 17.51      | 44.27         | 60.21      | 6.04             | 5.74             | 28.57            | 29.98       | 16.88            |{{< /table-caption >}}
> 🔼 표 26은 다양한 크기의 DeepSeek-R1 증류 모델에 대한 주제 분류(TC) 작업의 F1 점수를 보여줍니다. 이 결과는 제로샷 프롬프팅을 기반으로 하며, 본 연구의 평가에서 얻은 결과입니다. 표는 모델 크기별로 다양한 언어의 성능을 보여줍니다.  각 모델의 크기와 언어에 따른 성능을 비교하여 저자원 언어에 대한 모델의 일반화 성능을 분석하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 26: F1 Scores for DeepSeek-R1 distilled models of various sizes for TC. The results are based on zero-shot prompting and were obtained in our evaluation.
> </details>

{{< table-caption >}}
|       | Bloom | Bloomz | mT0 | GPT-3.5-turbo-0301 |
| :---- | ----: | ----: | ----: | ----: |
| th    | 1.0   | 0.2   | 1.4   | -     |
| el    | 19.7  | 13.0  | 12.8  | 69.3  |
| ur    | 71.7  | 47.3  | 47.1  | -     |
| te    | 5.3   | 3.8   | 3.3   | -     |
| sw    | 58.8  | 26.8  | 24.3  | -     |
| bg    | 29.6  | 19.7  | 14.7  | 72.0  |
| mr    | 27.9  | 20.4  | 12.3  | -     |
| bn    | 36.8  | 36.2  | 23.9  | -     |
| Total avg. | 31.35 | 20.92 | 17.48 | 70.65 |{{< /table-caption >}}
> 🔼 표 27은 과제 적응기를 사용하여 미세 조정된 LLaMA-3 기준 모델과 비교하여 TC, NER 및 SA에 대한 LLaMA-3+Seq-bn_inv의 F1 점수를 비교한 것입니다. 모든 결과는 서로 다른 난수 시드를 사용하여 3번의 독립 실행을 평균낸 것입니다.
> <details>
> <summary>read the caption</summary>
> Table 27: Comparison of F1 Scores for LLaMA-3 Baseline (fine-tuned with a task adapter) and LLaMA-3+Seq_bn_inv on TC, NER, and SA. All results are averaged over 3 independent runs with different random seeds.
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