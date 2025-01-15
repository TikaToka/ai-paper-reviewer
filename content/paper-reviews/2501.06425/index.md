---
title: "Tensor Product Attention Is All You Need"
summary: "TPA(텐서 곱 어텐션)는 메모리 효율적인 새로운 어텐션 메커니즘으로, 대규모 언어 모델의 확장성 문제를 해결합니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Tsinghua University",]
showSummary: true
date: 2025-01-11
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.06425 {{< /keyword >}}
{{< keyword icon="writer" >}} Yifan Zhang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-14 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.06425" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.06425" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/tensor-product-attention-is-all-you-need" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)은 긴 입력 시퀀스를 처리하는 데 어려움을 겪습니다. 특히, 추론 과정에서 키-밸류(KV) 캐시의 메모리 오버헤드가 매우 큽니다. 이 문제를 해결하기 위해 기존의 몇몇 방법들이 제시되었지만, 이러한 방법들은 메모리 효율성이나 성능 측면에서 한계를 가지고 있습니다. 예를 들어, 스파스 어텐션이나 토큰 제거는 중요한 정보를 잃을 위험이 있고, 칩 외부에 KV 상태를 저장하는 방법은 I/O 지연 시간이 증가하는 문제가 있습니다.

본 논문에서는 이러한 문제를 해결하기 위해 새로운 어텐션 메커니즘인 TPA(Tensor Product Attention)를 제안합니다. TPA는 텐서 분해를 통해 쿼리, 키, 밸류를 효율적으로 표현하여 KV 캐시 크기를 줄이고 메모리 효율성을 향상시킵니다. 또한, TPA는 RoPE(Rotary Position Embedding)와 호환되므로 기존의 LLM 아키텍처에 쉽게 통합될 수 있습니다. 다양한 언어 모델링 작업에 대한 실험 결과, T6는 MHA, MQA, GQA, MLA 등 기존의 트랜스포머 기반 모델들을 능가하는 성능을 보였습니다. 특히, TPA의 메모리 효율성 덕분에 제한된 자원 내에서 훨씬 긴 시퀀스를 처리할 수 있었습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} TPA는 텐서 분해를 이용해 쿼리, 키, 밸류를 효율적으로 표현하여 KV 캐시 크기를 대폭 줄입니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} T6 모델 아키텍처는 TPA를 기반으로 하여 기존 트랜스포머 기반 모델보다 성능이 우수합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} TPA는 RoPE와 호환되어 기존 모델에 쉽게 통합될 수 있습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **메모리 효율적인 새로운 어텐션 메커니즘인 TPA(Tensor Product Attention)와 이를 기반으로 한 새로운 모델 아키텍처 T6**을 제시하여 장문의 시퀀스 처리에 대한 어려움을 해결합니다. 이는 **최신 대규모 언어 모델의 확장성 문제에 대한 중요한 돌파구**를 제시하며, 관련 분야 연구자들에게 새로운 연구 방향과 기회를 제공합니다.  **TPA는 기존 어텐션 메커니즘의 단점을 극복**하고 **메모리 효율성과 성능을 동시에 향상**시키는 혁신적인 기술로 평가받고 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.06425/x1.png)

> 🔼 그림 1은 Tensor Product Attention Transformer (T6)에서 Tensor Product Attention (TPA) 메커니즘을 보여줍니다. 일반적인 멀티-헤드 어텐션과 달리, TPA는 각 레이어에서 은닉 상태를 먼저 여러 선형 레이어를 통과시켜 쿼리, 키, 값에 대한 잠재 요인 행렬 A와 B를 얻습니다.  쿼리와 키에는 추가적으로 RoPE(Rotary Position Embedding)가 B_Q와 B_K에 적용됩니다. 그런 다음, A와 B의 텐서 곱을 통해 멀티-헤드 쿼리, 키, 값 벡터가 생성됩니다.  최종적으로 TPA의 출력은 스케일드 닷-프로덕트 어텐션과 여러 헤드의 연결된 결과에 대한 선형 투영을 통해 생성됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Tensor Product Attention (TPA) in the Tensor ProducT ATTenTion Transformer (T6). Different from multi-head attention, in each layer, firstly the hidden state goes through different linear layers to get the latent factor matrices 𝐀𝐀\mathbf{A}bold_A’s and 𝐁𝐁\mathbf{B}bold_B’s for query, key, and value. We additionally apply RoPE to 𝐁Qsubscript𝐁𝑄\mathbf{B}_{Q}bold_B start_POSTSUBSCRIPT italic_Q end_POSTSUBSCRIPT and 𝐁Ksubscript𝐁𝐾\mathbf{B}_{K}bold_B start_POSTSUBSCRIPT italic_K end_POSTSUBSCRIPT for query and key. Then the multi-head query, key, and value vectors are attained by the tensor product of 𝐀(⋅)subscript𝐀⋅\mathbf{A}_{(\cdot)}bold_A start_POSTSUBSCRIPT ( ⋅ ) end_POSTSUBSCRIPT and 𝐁(⋅)subscript𝐁⋅\mathbf{B}_{(\cdot)}bold_B start_POSTSUBSCRIPT ( ⋅ ) end_POSTSUBSCRIPT. Finally, the output of TPA is produced by scaled dot-product attention followed by linear projection of concatenated results of multiple heads.
> </details>





{{< table-caption >}}
Method|KV Cache|# Parameters|# Query Heads|# KV Heads
MHA|2hd<sub>h</sub>|4d<sub>model</sub><sup>2</sup>|h|h
MQA|2d<sub>h</sub>|(2+2/h)d<sub>model</sub><sup>2</sup>|h|1
GQA|2gd<sub>h</sub>|(2+2g/h)d<sub>model</sub><sup>2</sup>|h|g
MLA|d<sub>c</sub>+d<sub>h</sub><sup>R</sup>|d<sub>c</sub>'(d<sub>model</sub>+hd<sub>h</sub>+hd<sub>h</sub><sup>R</sup>)+d<sub>model</sub>d<sub>h</sub><sup>R</sup>+d<sub>c</sub>(d<sub>model</sub>+2hd<sub>h</sub>)|h|h
TPA|(R<sub>K</sub>+R<sub>V</sub>)(h+d<sub>h</sub>)|d<sub>model</sub>(R<sub>Q</sub>+R<sub>K</sub>+R<sub>V</sub>)(h+d<sub>h</sub>)+d<sub>model</sub>hd<sub>h</sub>|h|h
TPA (KVonly)|(R<sub>K</sub>+R<sub>V</sub>)(h+d<sub>h</sub>)|d<sub>model</sub>(R<sub>K</sub>+R<sub>V</sub>)(h+d<sub>h</sub>)+2d<sub>model</sub>hd<sub>h</sub>|h|h
TPA (Non-contextual A)|(R<sub>K</sub>+R<sub>V</sub>)d<sub>h</sub>|(R<sub>Q</sub>+R<sub>K</sub>+R<sub>V</sub>)(d<sub>model</sub>d<sub>h</sub>+h)+d<sub>model</sub>hd<sub>h</sub>|h|h
TPA (Non-contextual B)|(R<sub>K</sub>+R<sub>V</sub>)h|(R<sub>Q</sub>+R<sub>K</sub>+R<sub>V</sub>)(d<sub>model</sub>h+d<sub>h</sub>)+d<sub>model</sub>hd<sub>h</sub>|h|h{{< /table-caption >}}

> 🔼 표 1은 다양한 어텐션 메커니즘들을 비교 분석한 표입니다.  TPA(Tensor Product Attention)의 쿼리, 키, 밸류에 대한 랭크(RQ, RK, RV)를 보여주고, TPA의 변형들(TPA(KVonly), TPA(Non-contextual A), TPA(Non-contextual B))과 MLA(Multi-head Latent Attention)와의 비교를 통해 매개변수 수, KV 캐시 크기, 쿼리 헤드 수, KV 헤드 수 등을 상세히 나타냅니다. 특히 MLA의 경우 RoPE(Rotary Position Embedding) 사용 여부에 따른 차원(dhR, dh)과 쿼리 및 키-밸류 벡터 압축 차원(dc′, dc)을 구분하여 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 1:  Comparison of different attention mechanisms. Here, RQsubscript𝑅𝑄R_{Q}italic_R start_POSTSUBSCRIPT italic_Q end_POSTSUBSCRIPT, RKsubscript𝑅𝐾R_{K}italic_R start_POSTSUBSCRIPT italic_K end_POSTSUBSCRIPT, and RVsubscript𝑅𝑉R_{V}italic_R start_POSTSUBSCRIPT italic_V end_POSTSUBSCRIPT denote the ranks for queries, keys, and values in TPA, respectively. Variants of TPA, such as TPA (KVonly), TPA (Non-contextual A), and TPA (Non-contextual B), are detailed in Section 3.5. For MLA, dhRsuperscriptsubscript𝑑ℎ𝑅d_{h}^{R}italic_d start_POSTSUBSCRIPT italic_h end_POSTSUBSCRIPT start_POSTSUPERSCRIPT italic_R end_POSTSUPERSCRIPT and dhsubscript𝑑ℎd_{h}italic_d start_POSTSUBSCRIPT italic_h end_POSTSUBSCRIPT are the dimensions for RoPE and non-RoPE parts; dc′superscriptsubscript𝑑𝑐′d_{c}^{\prime}italic_d start_POSTSUBSCRIPT italic_c end_POSTSUBSCRIPT start_POSTSUPERSCRIPT ′ end_POSTSUPERSCRIPT and dcsubscript𝑑𝑐d_{c}italic_d start_POSTSUBSCRIPT italic_c end_POSTSUBSCRIPT are the dimensions of compressed vectors for query and key-value, respectively.
> </details>





### In-depth insights


#### TPA: Key Innovation
본 논문에서 제안하는 TPA(Tensor Product Attention)의 핵심 혁신은 **메모리 효율성을 크게 향상시키면서도 모델 성능을 저하시키지 않는 새로운 어텐션 메커니즘**을 제공하는 데 있습니다.  기존의 어텐션 메커니즘은 입력 시퀀스 길이에 따라 KV 캐시 크기가 선형적으로 증가하는 문제점이 있었지만, TPA는 텐서 분해를 이용하여 쿼리, 키, 밸류를 효율적으로 표현함으로써 KV 캐시 크기를 획기적으로 줄입니다.  이는 특히 긴 시퀀스를 처리해야 하는 대규모 언어 모델에서 매우 중요한 이점입니다.  **TPA는 컨텍스트 정보를 활용한 낮은 랭크의 컨텍스트 분해를 통해 메모리 효율성과 모델 성능을 동시에 개선**하며,  **ROPE(Rotary Position Embedding)와의 원활한 통합**을 통해 위치 정보를 효과적으로 처리할 수 있습니다.  결과적으로, TPA는 기존의 MHA(Multi-Head Attention), MQA(Multi-Query Attention), GQA(Grouped-Query Attention), MLA(Multi-head Latent Attention) 등과 비교하여 다양한 언어 모델링 작업에서 우수한 성능을 보여주는 동시에 메모리 사용량을 획기적으로 줄일 수 있는 혁신적인 기술입니다.  **TPA의 메모리 효율성은 긴 시퀀스 처리에 대한 중요한 과제를 해결**, 현대적인 언어 모델의 확장성을 크게 향상시킬 수 있는 가능성을 제시합니다.

#### ROPE Integration
본 논문에서 제시된 텐서 곱셈 어텐션(TPA)은 회전 위치 임베딩(RoPE)와의 통합에 중점을 둡니다. **RoPE는 위치 정보를 효율적으로 인코딩하는 기법**으로, TPA의 성능 향상에 중요한 역할을 합니다.  **TPA는 RoPE와의 호환성을 유지하면서도 메모리 효율성을 높이는 구조**를 가지고 있어, 기존의 어텐션 메커니즘을 대체하는 데 용이합니다.  특히, **RoPE를 TPA의 텐서 분해 과정에 직접 통합**하여 계산 속도를 높이고, 추가적인 매개변수 없이 위치 정보를 효과적으로 처리할 수 있습니다.  **TPA의 RoPE 통합 방식은 기존 모델 아키텍처에 대한 수정을 최소화**하여, 실제 구현 및 적용을 간소화합니다.  **다양한 실험 결과를 통해 TPA가 RoPE와의 통합을 통해 성능 향상과 메모리 효율성을 동시에 달성**함을 보여줍니다.  결론적으로, TPA의 RoPE 통합은 **메모리 효율성과 성능 향상을 모두 고려한 실용적인 어텐션 메커니즘** 설계에 대한 중요한 시사점을 제공합니다.

#### Memory Efficiency
본 논문에서 제시된 텐서 곱셈 어텐션(TPA)은 **메모리 효율성**을 크게 향상시키는 핵심 요소입니다. 기존의 어텐션 메커니즘은 입력 시퀀스 길이에 따라 기하급수적으로 메모리 사용량이 증가하는 문제가 있었지만, TPA는 텐서 분해를 통해 쿼리, 키, 밸류를 효율적으로 표현하여 **KV 캐시 크기를 상당히 줄입니다**. 이는 특히 **긴 입력 시퀀스를 처리하는 데 필수적**이며, 제한된 하드웨어 자원 내에서도 더 긴 시퀀스를 처리할 수 있게 합니다.  **컨텍스트 분해**를 통해 문맥 정보를 효율적으로 담아내면서도 메모리 효율성을 유지하는 것이 TPA의 중요한 강점입니다.  TPA는 기존의 다양한 어텐션 메커니즘(MHA, MQA, GQA)을 일반화하는 틀을 제공하며, RoPE와의 호환성을 통해 실제 모델에 손쉽게 적용할 수 있습니다.  **TPA를 기반으로 한 T6 모델**은 다양한 언어 모델링 작업에서 우수한 성능을 보여주며, **메모리 효율성과 모델 성능을 동시에 개선**한다는 것을 실험적으로 증명합니다.  결론적으로 TPA는 **대규모 언어 모델의 확장성 문제 해결에 중요한 기여**를 할 것으로 기대됩니다.

#### Empirical Validation
본 논문의 "실험적 검증" 부분은 제시된 방법론의 효과를 객관적으로 평가하기 위해 다양한 실험과 분석을 수행한 결과를 제시합니다.  **다양한 벤치마크 데이터셋을 사용하여 제안된 모델의 성능을 기존 모델들과 비교**함으로써, **정량적인 성능 향상**을 보여주는 것이 중요합니다.  단순히 성능 수치만 제시하는 것이 아니라, **실험 설계 및 결과 해석에 대한 자세한 설명**이 필요하며, **통계적 유의성 검정**을 통해 얻은 결과의 신뢰성을 확보하는 것이 중요합니다. 또한, 실험 결과를 통해 **제안된 방법의 장점과 한계점을 명확히 제시**하고, **향후 연구 방향을 제시**하는 것도 중요한 부분입니다.  **계산 비용 및 메모리 효율성 측면에서의 비교 분석** 또한 중요한 평가 지표이며, 이를 통해 제안된 방법의 실용성을 강조할 수 있습니다.  **다양한 하이퍼파라미터에 대한 민감도 분석**을 통해 모델의 안정성을 평가하고, **결과의 일반화 가능성**을 높이는 것이 필요합니다.  마지막으로, **결론 부분에서는 실험 결과를 종합적으로 요약**하고, **제안된 모델의 강점과 약점을 명확히 제시**하여 연구의 기여도를 분명하게 밝히는 것이 중요합니다.

#### Future Extensions
**미래 확장에 대한 고찰은 본 논문의 핵심 내용을 넘어서는 중요한 부분입니다.**  향후 연구 방향을 제시하고, 논문의 한계점을 극복하며,  더욱 발전된 모델을 구축하기 위한 가능성을 모색하는 데 초점을 맞춰야 합니다.  **특히, 텐서곱 연산의 효율성을 높이는 알고리즘 개발은 중요한 과제입니다.** 현재 제시된 텐서 분해 기법을 넘어 더욱 고도화된 기법을 통해 계산 복잡도를 낮추고, 메모리 사용량을 최소화하는 방안을 연구할 수 있습니다. 또한, **다양한 자연어 처리 작업에 대한 적용 가능성을 확대하는 연구가 필요합니다.** 본 논문에서 다룬 언어 모델링 작업 외에 기계 번역, 질의응답, 텍스트 요약 등 다양한 분야에 대한 실험을 통해 TPA의 일반적인 성능을 평가하고,  각 작업에 특화된 TPA 변형 모델을 개발할 수 있습니다.  **더 나아가, TPA와 다른 최신 기술들과의 결합을 통한 시너지 효과를 연구하는 것도 중요한 미래 연구 방향입니다.** 예를 들어,  스파스 어텐션 메커니즘이나 양자 컴퓨팅 기술과 결합하여  TPA의 성능을 더욱 향상시키고, 확장성을 높일 수 있는 방안을 모색해야 합니다.  마지막으로, **윤리적, 사회적 함의에 대한 고찰을 통해 책임감 있는 AI 연구를 수행해야 합니다.**  강력한 언어 모델의 발전은 편향성, 오용 가능성 등 다양한 윤리적 문제를 야기할 수 있으므로,  이러한 문제점을 사전에 예방하고 해결하기 위한 방안을 모색해야 합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.06425/x2.png)

> 🔼 그림 2(a)는 FineWeb-Edu-100B 데이터셋을 사용하여 다양한 어텐션 메커니즘을 적용한 대규모(773M) 모델의 훈련 손실을 보여줍니다.  x축은 훈련 토큰 수 (단위: 10억)이고 y축은 훈련 손실 값입니다.  다양한 어텐션 메커니즘(MHA, MQA, GQA, MLA, TPA-KVonly, TPA)의 훈련 손실 곡선을 비교하여 각 메커니즘의 훈련 효율성을 시각적으로 나타냅니다.  TPA 기반 모델이 다른 모델들에 비해 훈련 손실이 낮은 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (a) Training Loss
> </details>



![](https://arxiv.org/html/2501.06425/x3.png)

> 🔼 그림 2(b)는 FineWeb-Edu-100B 데이터셋에서 다양한 어텐션 메커니즘을 사용하는 대규모(773M) 모델의 검증 손실을 보여줍니다. 훈련 토큰 수에 따른 검증 손실의 변화를 나타내며, TPA 및 TPA-KVonly 모델이 다른 기준 모델(MHA, MQA, GQA, MLA)에 비해 훈련 후반부까지 지속적으로 낮은 검증 손실을 유지하는 것을 보여줍니다. 이는 TPA 기반 모델의 우수한 성능을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) Validation Loss
> </details>



![](https://arxiv.org/html/2501.06425/x4.png)

> 🔼 그림 2는 FineWeb-Edu-100B 데이터셋을 사용하여 사전 훈련된 대규모(7억 7300만 매개변수) 모델에서 서로 다른 어텐션 메커니즘에 따른 훈련 손실 및 검증 손실을 보여줍니다.  다양한 어텐션 메커니즘(MHA, MQA, GQA, MLA, TPA-KVonly, TPA)의 성능을 비교하여 각 메커니즘의 훈련 효율성과 성능을 시각적으로 보여줍니다.  훈련 손실과 검증 손실의 추이를 통해 어떤 어텐션 메커니즘이 더 빠르게 수렴하고, 더 나은 성능을 보이는지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Training loss and validation loss of pretraining large-size (773M) models with different attention mechanisms on the FineWeb-Edu-100B dataset.
> </details>



![](https://arxiv.org/html/2501.06425/x5.png)

> 🔼 그림 2(a)는 FineWeb-Edu-100B 데이터셋을 사용하여 서로 다른 어텐션 메커니즘을 가진 대규모(773M) 모델의 훈련 손실을 보여줍니다.  x축은 훈련 토큰 수 (B 단위)이고, y축은 훈련 손실 값입니다.  여러 어텐션 메커니즘 (MHA, MQA, GQA, MLA, TPA-KVonly, TPA)의 훈련 손실 곡선이 표시되어 각 메커니즘의 훈련 효율성을 비교 분석하는 데 도움이 됩니다.  TPA 기반 모델이 다른 기준 모델들에 비해 훈련 손실이 더 낮은 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (a) Training Loss
> </details>



![](https://arxiv.org/html/2501.06425/x6.png)

> 🔼 그림 2(b)는 FineWeb-Edu-100B 데이터셋을 사용하여 훈련된 크기가 큰(773M) 모델의 검증 손실을 보여줍니다. 다양한 어텐션 메커니즘(MHA, MQA, GQA, MLA, TPA-KVonly, TPA)을 사용한 모델의 검증 손실 곡선을 비교하여 TPA 기반 모델이 다른 기준 모델보다 훨씬 낮은 검증 손실을 달성함을 보여줍니다. 특히, TPA와 TPA-KVonly 모델은 훈련 과정의 대부분에서 MHA 기준 모델보다 낮은 검증 손실을 유지합니다.
> <details>
> <summary>read the caption</summary>
> (b) Validation Loss
> </details>



![](https://arxiv.org/html/2501.06425/x7.png)

> 🔼 그림 3은 FineWeb-Edu 100B 데이터셋을 사용하여 다양한 어텐션 메커니즘을 적용한 중간 크기(353M) 모델의 학습 손실 및 검증 손실을 보여줍니다.  x축은 학습 토큰 수(단위: 10억)이고, y축은 손실 값입니다.  각 선은 서로 다른 어텐션 메커니즘(MHA, MQA, GQA, MLA, TPA-KVonly, TPA)을 사용한 모델의 손실을 나타냅니다. 이 그래프를 통해 다양한 어텐션 메커니즘의 학습 및 성능을 비교하고, TPA 기반 모델의 효율성을 시각적으로 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: The training loss and validation loss of medium-size (353M) models with different attention mechanisms on the FineWeb-Edu 100B dataset.
> </details>



![](https://arxiv.org/html/2501.06425/x8.png)

> 🔼 그림 4 (a)는 중간 크기(353M) 언어 모델의 검증 퍼플렉서티(perplexity)를 보여줍니다.  다양한 어텐션 메커니즘(MHA, MQA, GQA, MLA, TPA-KVonly, TPA)을 사용하여 FineWeb-Edu-100B 데이터셋으로 사전 훈련된 모델의 훈련 토큰 수에 따른 퍼플렉서티 변화를 나타냅니다.  이 그래프를 통해 각 어텐션 메커니즘의 성능을 비교하고, 특히 TPA 및 TPA-KVonly가 다른 방법들에 비해 더 낮은 퍼플렉서티를 달성함을 보여줍니다.  즉,  TPA 기반 모델이 더 나은 일반화 성능을 가짐을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (a) Validation Perplexity of Medium Models
> </details>



![](https://arxiv.org/html/2501.06425/x9.png)

> 🔼 이 그림은 논문의 큰 모델(773M 매개변수)에 대한 검증 퍼플렉서티(perplexity)를 보여줍니다.  다양한 어텐션 메커니즘(MHA, MQA, GQA, MLA, TPA-KVonly, TPA)을 사용한 모델의 학습 진행에 따른 검증 퍼플렉서티 변화를 나타냅니다.  그래프의 x축은 학습 토큰 수(B 단위), y축은 검증 퍼플렉서티 값입니다. 이를 통해 각 어텐션 메커니즘의 성능과 효율성을 비교 분석할 수 있습니다. 특히, TPA와 TPA-KVonly가 다른 메커니즘들보다 낮은 퍼플렉서티를 달성하여 더 나은 성능을 보임을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (b) Validation Perplexity of Large Models
> </details>



![](https://arxiv.org/html/2501.06425/x10.png)

> 🔼 그림 4는 FineWeb-Edu 100B 데이터셋에서 다양한 어텐션 메커니즘을 사용한 중간 크기(353M) 및 대규모(773M) 모델의 검증 퍼플렉서티를 보여줍니다.  x축은 학습 토큰 수 (단위: 10억)이고 y축은 검증 퍼플렉서티입니다.  다양한 어텐션 메커니즘(MHA, MQA, GQA, MLA, TPA-KVonly, TPA)의 성능을 비교하여 TPA 기반 모델이 다른 모델들에 비해 낮은 퍼플렉서티를 달성함을 보여줍니다. 이는 TPA가 메모리 효율성을 유지하면서 모델 성능을 향상시킬 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: The validation perplexity of medium-size (353M) models and large-size (773M) models with different attention mechanisms on the FineWeb-Edu 100B dataset.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | ARC-E | ARC-C | BoolQ | HellaSw. | OBQA | PIQA | W.G. | MMLU | SciQ | Avg. |
|---|---|---|---|---|---|---|---|---|---|---|
| MHA | 56.52 | 29.27 | 58.84 | 44.06 | 35.00 | 68.44 | 51.07 | 25.35 | 76.40 | 49.44 |
| MQA | 55.68 | 28.24 | 60.86 | 44.17 | 35.20 | 68.66 | 52.72 | 25.14 | 72.90 | 49.29 |
| GQA | 54.88 | 29.61 | 56.36 | 43.77 | 35.20 | 68.82 | 52.57 | 25.41 | 74.80 | 49.05 |
| MLA | 55.30 | 29.27 | 58.96 | 41.92 | 35.40 | 67.25 | 51.78 | 25.20 | 75.60 | 48.96 |
| **TPA-KVonly** | 57.11 | 30.03 | **61.25** | 44.83 | 34.60 | 69.04 | **54.54** | 23.35 | 74.60 | 49.93 |
| **TPA** | **59.30** | **31.91** | 60.98 | **45.57** | 34.60 | **69.48** | 53.91 | 24.93 | **77.20** | **50.88** |{{< /table-caption >}}
> 🔼 표 2는 FineWeb-Edu 100B 데이터셋을 사용하여 사전 훈련된 다양한 어텐션 메커니즘을 갖는 중간 크기 모델(353M 매개변수)의 0-shot 성능 평가 결과를 보여줍니다.  lm-evaluation-harness 도구를 사용하여 평가되었으며, 각 열의 최고 점수는 굵게 표시되어 있습니다. HellaSwag와 WinoGrande는 각각 HellaSw.와 W.G.로 약어 처리되었습니다.  표는 다양한 자연어 처리 과제(ARC-E, ARC-C, BoolQ, HellaSwag, OBQA, PIQA, WinoGrande, MMLU, SciQ)에 대한 정확도를 보여주어, 각 어텐션 메커니즘의 상대적 강점과 약점을 비교 분석하는 데 유용합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: The evaluation results of medium models with different attention mechanisms pretrained using the FineWeb-Edu 100B dataset (0-shot with lm-evaluation-harness). The best scores in each column are bolded. Abbreviations: HellaSw. = HellaSwag, W.G. = WinoGrande.
> </details>

{{< table-caption >}}
| Method | ARC-E | ARC-C | BoolQ | HellaSw. | OBQA | PIQA | W.G. | MMLU | SciQ | Avg. |
|---|---|---|---|---|---|---|---|---|---|---|
| MHA | 64.44 | 32.85 | 59.05 | 44.18 | 33.20 | 68.72 | 50.12 | 26.01 | 87.40 | 49.44 |
| MQA | 64.27 | 32.94 | 57.71 | 44.36 | 31.80 | 68.01 | 51.70 | 25.99 | 86.00 | 49.29 |
| GQA | 61.70 | 32.17 | 52.81 | 43.99 | 33.80 | 68.50 | 53.35 | 24.44 | 86.40 | 50.80 |
| MLA | 62.75 | 30.80 | 59.17 | 42.02 | 34.80 | 67.08 | 52.41 | 26.11 | 84.80 | 51.10 |
| **TPA-KVonly** | 65.99 | 33.70 | 57.49 | 44.47 | 34.20 | 69.53 | 53.28 | 24.23 | 86.50 | 49.93 |
| **TPA** | 66.54 | 34.47 | 58.96 | 45.35 | 33.00 | 69.21 | 53.99 | 24.51 | 91.30 | 53.04 |{{< /table-caption >}}
> 🔼 표 3은 FineWeb-Edu 100B 데이터셋을 사용하여 사전 훈련된 다양한 어텐션 메커니즘을 가진 중간 크기 모델의 평가 결과를 보여줍니다.  lm-evaluation-harness를 사용하여 2-shot 설정으로 평가되었으며, 각 열의 최고 점수는 굵게 표시되어 있습니다.  HellaSwag와 WinoGrande의 약어도 포함되어 있습니다. 이 표는 각 모델의 성능을 다양한 벤치마크에 걸쳐 비교하여, 어떤 어텐션 메커니즘이 주어진 작업에서 더 나은 성능을 발휘하는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: The evaluation results of medium models with different attention mechanisms pre-trained using the FineWeb-Edu 100B dataset (2-shot with lm-evaluation-harness). The best scores in each column are bolded. Abbreviations: HellaSw. = HellaSwag, W.G. = WinoGrande.
> </details>

{{< table-caption >}}
| Method | ARC-E | ARC-C | BoolQ | HellaSw. | OBQA | PIQA | W.G. | MMLU | SciQ | Avg. |
|---|---|---|---|---|---|---|---|---|---|---|
| MHA | 59.93 | 33.62 | 61.93 | 50.63 | 36.00 | 71.06 | 55.41 | 22.87 | **81.20** | 52.52 |
| MQA | 60.73 | 33.62 | 57.34 | 50.09 | 37.00 | 69.97 | 55.49 | 25.30 | 79.60 | 52.13 |
| GQA | 61.66 | 34.30 | 58.72 | 49.85 | **38.40** | 71.16 | 53.75 | 25.23 | 77.60 | 52.30 |
| MLA | 60.73 | 31.57 | **61.74** | 48.96 | 35.40 | 69.59 | 55.09 | **26.39** | 76.70 | 51.80 |
| **TPA-KVonly** | **63.26** | 34.13 | **61.96** | 50.66 | 37.20 | **72.09** | 55.25 | 26.06 | 81.10 | **53.52** |
| **TPA** | 63.22 | **35.58** | 60.03 | **51.26** | 36.80 | 71.44 | **55.56** | 24.77 | 79.60 | 53.10 |{{< /table-caption >}}
> 🔼 표 4는 FineWeb-Edu 100B 데이터셋을 사용하여 사전 훈련된 다양한 어텐션 메커니즘을 갖는 대규모 모델(매개변수 7억 7300만 개)의 평가 결과를 보여줍니다.  0-shot 설정(lm-evaluation-harness 사용)에서 각 모델의 성능을 ARC-E, ARC-C, BoolQ, HellaSwag, OBQA, PIQA, WinoGrande, MMLU, SciQ 등 다양한 벤치마크에 대해 평가하였습니다. 각 열의 최고 점수는 굵게 표시되어 있으며, HellaSwag는 HellaSwag의 약자이고, W.G.는 WinoGrande의 약자입니다. 이 표는 다양한 어텐션 메커니즘(MHA, MQA, GQA, MLA, TPA, TPA-KVonly)의 상대적 성능을 비교하여 TPA 기반 모델의 우수성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 4: The evaluation results of large models with different attention mechanisms pre-trained using the FineWeb-Edu 100B dataset (0-shot with lm-evaluation-harness). The best scores in each column are bolded. Abbreviations: HellaSw. = HellaSwag, W.G. = WinoGrande.
> </details>

{{< table-caption >}}
| Method | ARC-E | ARC-C | BoolQ | HellaSwag | OBQA | PIQA | WG | MMLU | SciQ | Avg. |
|---|---|---|---|---|---|---|---|---|---|---|
| MHA | 67.85 | 36.35 | 59.82 | 50.22 | 35.00 | 70.67 | 53.35 | 23.92 | 91.10 | 54.25 |
| MQA | 68.86 | 36.09 | 53.79 | 50.50 | 37.00 | 70.89 | 54.70 | 25.01 | 88.00 | 53.87 |
| GQA | 69.15 | 36.09 | 58.84 | 50.29 | 36.20 | 70.73 | 54.22 | 26.08 | 90.00 | 54.62 |
| MLA | 68.56 | 35.41 | 60.12 | 49.18 | 38.00 | 69.21 | 55.25 | 25.29 | 88.20 | 54.36 |
| **TPA-KVonly** | **71.34** | **37.71** | 59.76 | 51.10 | 36.00 | **71.49** | 54.62 | 25.83 | 90.10 | **55.33** |
| **TPA** | 70.41 | **37.71** | 60.06 | **51.30** | 34.00 | 71.06 | 54.54 | 25.79 | 90.30 | 55.02 |{{< /table-caption >}}
> 🔼 표 5는 FineWeb-Edu 100B 데이터셋을 사용하여 사전 훈련된 다양한 어텐션 메커니즘을 가진 대규모 모델(매개변수 7억 7300만 개)의 성능 평가 결과를 보여줍니다.  lm-evaluation-harness를 사용하여 2-shot 설정에서 평가되었으며, 각 열의 최고 점수는 굵게 표시되어 있습니다.  HellaSwag와 WinoGrande는 약어로 표기되었습니다. 이 표는 다양한 하위 작업(ARC-E, ARC-C, BoolQ, HellaSwag, OBQA, PIQA, WinoGrande, MMLU, SciQ)에 대한 각 모델의 정확도를 보여주어, 다양한 어텐션 메커니즘의 상대적 강점과 약점을 비교 분석하는 데 도움이 됩니다. 특히, TPA(Tensor Product Attention)와 TPA-KVonly가 다른 방법들에 비해 전반적으로 높은 성능을 보이는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: The evaluation results of large models with different attention mechanisms pre-trained using the FineWeb-Edu 100B dataset (2-shot with lm-evaluation-harness). The best scores in each column are bolded. Abbreviations: HellaSwag = HellaSwag, WG = WinoGrande.
> </details>

{{< table-caption >}}
| Model Size | #Param | Devices | Micro BS. | GAS. | #Layer | dmodel |
|---|---|---|---|---|---|---|
| Small | 124M | 4 × A100 GPUs | 24 | 5 | 12 | 768 |
| Medium | 353M | 8 × A100 GPUs | 20 | 3 | 24 | 1024 |
| Large | 772M | 8 × A100 GPUs | 15 | 4 | 36 | 1280 |{{< /table-caption >}}
> 🔼 표 6은 논문에서 사용된 세 가지 크기(작음, 중간, 큼)의 언어 모델에 대한 하이퍼파라미터와 학습 환경 설정을 보여줍니다. 각 모델의 파라미터 수, 사용된 GPU 수, 배치 크기, 그래디언트 누적 단계, 레이어 수, 임베딩 차원 등이 포함되어 있습니다.  이 표는 모델 아키텍처와 학습 설정에 대한 자세한 정보를 제공하여, 실험 결과의 재현성을 높이고 서로 다른 모델 간의 비교를 용이하게 합니다. 약어 BS는 배치 크기(Batch Size), GAS는 그래디언트 누적 단계(Gradient Accumulation Steps)를 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: The architecture hyper-parameters and training devices of models. Abbreviations: BS. = Batch Size, GAS. = Gradient Accumulation Steps.
> </details>

{{< table-caption >}}
| Model Size | Small | Medium | Large |
|---|---|---|---|
| h (MHA) | 12 | 16 | 20 |
| h (MQA) | 23 | 31 | 39 |
| h (GQA) | 22 | 30 | 38 |
| n<sub>h</sub> (MLA) | 12 | 23 | 34 |
| h (TPA-KVonly) | 22 | 29 | 37 |
| h (TPA) | 34 | 47 | 61 |
| d<sub>c</sub> (MLA) | 256 | 512 | 512 |
| d<sub>c</sub>' (MLA) | 512 | 1024 | 1024 |{{< /table-caption >}}
> 🔼 표 7은 논문에서 사용된 다양한 크기의 언어 모델에 대한 하이퍼파라미터들을 보여줍니다.  각 모델의 크기(작은 모델, 중간 모델, 큰 모델)별로 헤드 수(MHA, MQA, GQA, MLA, TPA-KVONLY, TPA), 잠재 차원(MLA), 그리고 모델의 다른 주요 구조적 하이퍼파라미터들을 비교하여 보여줍니다.  이 표는 모델 구조와 성능 간의 관계를 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 7: The architecture hyper-parameters for different models.
> </details>

{{< table-caption >}}
| Method | ARC-E | ARC-C | BoolQ | HellaSw. | OBQA | PIQA | W.G. | MMLU | SciQ | Avg. |
|---|---|---|---|---|---|---|---|---|---|---|
| MHA | 50.63 | 26.96 | 59.39 | 36.18 | 32.00 | 64.96 | **51.85** | 23.40 | 70.30 | 46.19 |
| MQA | 49.62 | 25.34 | 55.72 | 35.94 | 31.40 | 64.85 | 51.30 | 23.37 | 68.70 | 45.14 |
| GQA | 48.70 | 25.68 | 56.15 | 35.58 | 31.40 | 64.91 | 51.62 | 23.12 | 68.20 | 45.04 |
| MLA | 49.66 | 26.45 | **61.22** | 33.94 | 32.40 | 62.73 | 50.43 | 23.29 | 71.50 | 45.74 |
| **TPA-KVonly** | 51.05 | 26.54 | 57.25 | **36.77** | 32.60 | **65.02** | 50.91 | 23.64 | 69.70 | 45.94 |
| **TPA** | **51.26** | **27.39** | 57.00 | 36.68 | **32.80** | 64.47 | 49.72 | **24.61** | **72.00** | **46.21** |{{< /table-caption >}}
> 🔼 표 8은 FineWeb-Edu 100B 데이터셋을 사용하여 사전 훈련된 다양한 어텐션 메커니즘을 가진 소규모 모델의 평가 결과를 보여줍니다.  lm-evaluation-harness를 사용하여 0-shot 평가를 수행했습니다. 각 열에서 가장 좋은 점수는 굵게 표시되어 있으며, 약어는 HellaSw.는 HellaSwag, W.G.는 WinoGrande를 나타냅니다. 이 표는 다양한 자연어 처리 작업(ARC-E, ARC-C, BoolQ, HellaSwag, OBQA, PIQA, WinoGrande, MMLU, SciQ)에 대한 각 모델의 정확도를 보여주어, 어떤 어텐션 메커니즘이 특정 작업에 더 적합한지 비교 분석하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 8: The evaluation results of small models with different attention mechanisms pre-trained using FineWeb-Edu 100B dataset (0-shot with lm-evaluation-harness). The best scores in each column are bolded. Abbreviations: HellaSw. = HellaSwag, W.G. = WinoGrande.
> </details>

{{< table-caption >}}
| Method | ARC-E | ARC-C | BoolQ | HellaSw. | OBQA | PIQA | W.G. | MMLU | SciQ | Avg. |
|---|---|---|---|---|---|---|---|---|---|---|
| MHA | **57.66** | **28.24** | **57.28** | 36.43 | 29.60 | 64.09 | 51.14 | **26.57** | **82.00** | **48.11** |
| MQA | 53.79 | 26.35 | 44.95 | 34.18 | 28.80 | 62.79 | 52.01 | 25.91 | 78.10 | 45.21 |
| GQA | 55.01 | 25.94 | 55.72 | 35.68 | **31.80** | **65.29** | 51.93 | 25.27 | 77.80 | 47.16 |
| MLA | 52.78 | 26.19 | 57.25 | 33.19 | 29.60 | 63.98 | 50.43 | 24.90 | 76.00 | 46.04 |
| **TPA-KVonly** | 54.25 | 27.90 | 57.06 | 36.36 | **31.80** | 64.31 | **53.59** | 26.18 | 79.20 | 47.85 |
| **TPA** | 57.53 | 28.07 | 56.33 | **36.49** | **31.80** | 64.36 | 51.14 | 25.92 | 79.70 | 47.93 |{{< /table-caption >}}
> 🔼 표 9는 FineWeb-Edu 100B 데이터셋에서 다양한 어텐션 메커니즘을 사용하여 사전 훈련된 소규모 모델(매개변수 1억 2400만 개)의 평가 결과를 보여줍니다.  lm-evaluation-harness를 사용하여 2-shot 설정에서 평가하였습니다. 각 열의 최고 점수는 굵게 표시되어 있으며, 약어 HellaSw.는 HellaSwag를, W.G.는 WinoGrande를 나타냅니다.  표에는 다양한 벤치마크(ARC-E, ARC-C, BoolQ, HellaSwag, OBQA, PIQA, WinoGrande, MMLU, SciQ)에 대한 성능을 보여주는 다양한 지표가 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 9: The evaluation results of small models with different attention mechanisms on FineWeb-Edu 100B dataset (2-shot with lm-evaluation-harness). The best scores in each column are bolded. Abbreviations: HellaSw. = HellaSwag, W.G. = WinoGrande.
> </details>

{{< table-caption >}}
| Method | ARC-E | ARC-C | BoolQ | HellaSw. | OBQA | PIQA | W.G. | MMLU | SciQ | Avg. |
|---|---|---|---|---|---|---|---|---|---|---|
| MHA | **59.51** | 29.52 | 59.60 | 45.68 | 34.20 | 68.82 | 53.43 | 23.33 | 76.90 | 50.11 |
| MQA | 57.62 | **31.91** | 59.45 | 45.69 | 35.40 | 69.31 | 53.51 | **26.47** | 74.60 | 50.44 |
| GQA | 28.67 | 31.48 | 58.29 | 45.45 | 35.20 | 68.50 | **54.46** | 24.58 | 76.50 | 47.01 |
| MLA | 57.49 | 29.44 | **59.97** | 44.09 | 25.77 | 68.66 | 53.04 | 25.77 | 76.40 | 48.96 |
| **TPA-KVonly** | 58.01 | 30.12 | 58.01 | 45.95 | 35.60 | 69.10 | 53.12 | 25.39 | 75.10 | 50.04 |
| **TPA** | 58.38 | 31.57 | 59.39 | **46.83** | **37.00** | **70.02** | 54.06 | 25.52 | **79.90** | **51.41** |{{< /table-caption >}}
> 🔼 표 10은 FineWeb-Edu 100B 데이터셋을 사용하여 사전 훈련된 중간 크기 모델(학습률 6 × 10⁻⁴)의 다양한 어텐션 메커니즘에 대한 평가 결과를 보여줍니다.  lm-evaluation-harness를 사용하여 0-shot 평가를 수행했으며, 각 열의 최고 점수는 굵게 표시되어 있습니다.  HellaSwag는 HellaSwag의 약자이고, W.G.는 WinoGrande의 약자입니다. 이 표는 다양한 자연어 처리 작업(ARC-E, ARC-C, BoolQ, HellaSwag, OBQA, PIQA, WinoGrande, MMLU, SciQ)에서 각 어텐션 메커니즘의 성능을 비교 분석하여 어떤 어텐션 메커니즘이 특정 작업에 더 효과적인지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 10: The evaluation results of medium models (learning rate=6×10−46superscript1046\times 10^{-4}6 × 10 start_POSTSUPERSCRIPT - 4 end_POSTSUPERSCRIPT) with different attention mechanisms pre-trained using FineWeb-Edu 100B dataset (0-shot with lm-evaluation-harness). The best scores in each column are bolded. Abbreviations: HellaSw. = HellaSwag, W.G. = WinoGrande.
> </details>

{{< table-caption >}}
| Method | ARC-E | ARC-C | BoolQ | HellaSw. | OBQA | PIQA | W.G. | MMLU | SciQ | Avg. |
|---|---|---|---|---|---|---|---|---|---|---|
| MHA | 64.73 | 32.42 | 58.29 | 45.89 | 34.20 | 68.50 | 53.20 | 25.86 | 88.00 | 52.34 |
| MQA | 64.98 | 33.62 | 55.02 | 45.81 | 34.00 | 69.59 | 53.43 | 24.30 | 85.20 | 51.77 |
| GQA | 65.24 | 33.19 | 56.54 | 45.41 | 34.80 | 69.04 | 55.72 | 24.73 | 87.90 | 52.51 |
| MLA | 63.80 | 31.06 | 58.50 | 44.19 | 35.40 | 68.44 | 51.62 | 25.22 | 88.50 | 51.86 |
| **TPA-KVonly** | 64.69 | 32.34 | **59.48** | 46.23 | **35.40** | **70.08** | 54.06 | 25.64 | 86.30 | 52.69 |
| **TPA** | **67.97** | **34.56** | 57.22 | **46.87** | 34.60 | 69.91 | 52.01 | 25.07 | **89.90** | **53.12** |{{< /table-caption >}}
> 🔼 표 11은 FineWeb-Edu 100B 데이터셋을 사용하여 사전 훈련된 중간 크기 모델(학습률 6 × 10⁻⁴)에 대해 서로 다른 어텐션 메커니즘의 평가 결과를 보여줍니다.  lm-evaluation-harness를 사용하여 2-shot 설정으로 평가되었으며, 각 열의 최고 점수는 굵게 표시되어 있습니다.  HellaSw.는 HellaSwag를, W.G.는 WinoGrande를 나타냅니다.  표는 다양한 자연어 처리 작업에 대한 각 모델의 성능을 비교 분석하여, 어텐션 메커니즘 선택이 모델 성능에 미치는 영향을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 11: The evaluation results of medium models (learning rate 6×10−46superscript1046\times 10^{-4}6 × 10 start_POSTSUPERSCRIPT - 4 end_POSTSUPERSCRIPT) with different attention mechanisms pre-trained using FineWeb-Edu 100B dataset (2-shot with lm-evaluation-harness). The best scores in each column are bolded. Abbreviations: HellaSw. = HellaSwag, W.G. = WinoGrande.
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