---
title: "Rethinking Addressing in Language Models via Contexualized Equivariant Positional Encoding"
summary: "TAPE(conTextualized equivAriant Position Embedding) 프레임워크를 통해 문맥 정보를 활용한 동적 위치 인코딩으로 트랜스포머의 위치 기반 주소 지정 성능을 향상시켰습니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 University of Texas at Austin",]
showSummary: true
date: 2025-01-01
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.00712 {{< /keyword >}}
{{< keyword icon="writer" >}} Jiajun Zhu et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-03 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.00712" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.00712" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

본 논문은 기존의 위치 인코딩 방식의 한계를 극복하고 **트랜스포머 모델의 성능을 향상시키는 새로운 위치 인코딩 기법인 TAPE**를 제안합니다. 기존 방식들은 고정된 패턴으로 인해 장기 의존 관계를 제대로 모델링하지 못하고 다양한 작업에 적응하기 어려운 문제점이 있습니다. 또한, 대부분의 기존 방법들은 일반적인 바이어스로 학습되어 데이터셋 내 각 인스턴스에 필요한 특수성을 반영하지 못합니다.



TAPE는 **계층 간 시퀀스 콘텐츠를 통합하여 위치 임베딩을 향상**시키는 새로운 프레임워크입니다. TAPE는 순열 및 직교 등변성을 적용하여 업데이트 중 위치 인코딩의 안정성을 유지하고 강건성과 적응성을 향상시킵니다. TAPE는 사전 훈련된 트랜스포머에 쉽게 통합되어 최소한의 오버헤드로 매개변수 효율적인 미세 조정을 가능하게 합니다. 실험 결과, TAPE는 기존 위치 인코딩 기법보다 언어 모델링, 산술 추론, 장기 문맥 검색 작업에서 우수한 성능을 달성했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 문맥 정보를 통합한 동적 위치 인코딩으로 트랜스포머의 위치 기반 주소 지정 능력 향상 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 순열 및 직교 등변성을 통해 업데이트 중 위치 인코딩의 안정성 및 적응성 향상 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 매개변수 효율적인 미세 조정을 통해 사전 훈련된 트랜스포머에 쉽게 통합 가능 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **장기 문맥 맥락 이해와 복잡한 추론 작업에서의 성능 향상**에 대한 새로운 접근법을 제시하여, 자연어 처리 분야의 연구자들에게 중요한 의미를 가집니다. 제안된 방법은 기존의 한계를 극복하고 효율성을 높여, **장기 문맥 모델링 및 다양한 하류 작업의 발전**에 기여할 수 있습니다. 또한, 본 연구는 **새로운 연구 방향**을 제시함으로써 후속 연구에 대한 영감을 제공합니다. 이러한 측면에서 본 논문은 자연어 처리 분야의 발전에 크게 기여할 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.00712/x1.png)

> 🔼 그림 1은 논문에서 제안하는 TAPE(conTextualized equivariAnt Position Embedding)가 표준 디코더 전용 트랜스포머 아키텍처에 어떻게 통합되는지를 보여줍니다. 기존의 위치 임베딩 방식(a)과 TAPE를 사용한 향상된 인과적 어텐션 및 피드포워드 레이어가 있는 TAPE(b)를 비교하여 보여줍니다. TAPE는 레이어 간에 시퀀스 콘텐츠를 통합하여 위치 임베딩을 상황에 맞게 조정함으로써 위치 기반 주소 지정 기능을 향상시킵니다. 순방향 및 역방향 피드포워드 레이어에 의해 위치 정보가 지속적으로 업데이트됨을 확인할 수 있습니다.  또한,  TAPE는 순열 및 직교 등변성을 강화하여 업데이트 중 위치 임베딩의 안정성을 보장하고 견고성과 적응성을 향상시킵니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Overview of our proposed TAPE in standard decoder-only Transformer architecture.
> </details>





{{< table-caption >}}
| Metric (%) | QAS | QAS | CNLI | CNLI | NQA | QuAL | QMS | SumS | GovR |
|---|---|---|---|---|---|---|---|---|---|---|
|  | F1 | EM | F1 | EM | F1 | EM | Rgm | Rgm | Rgm |
| Median length | 5472 | 2148 | 57829 | 7171 | 14197 | 9046 | 8841 |  |  |
| RoPE (Kitaev et al., 2020) | 8.39 | 65.00 | 1.77 | 0.04 | 6.34 | 5.63 | 9.71 |  |  |
| ALiBi (Press et al., 2021a) | 8.25 | 69.62 | 4.11 | 0.0 | 9.92 | 9.78 | 18.81 |  |  |
| RandPE (Ruoss et al., 2023) | 13.44 | 62.01 | 4.63 | 0.38 | 8.43 | 8.31 | 8.93 |  |  |
| FIRE (Li et al., 2023) | 3.41 | 71.26 | 0.48 | 1.25 | 8.78 | 7.42 | 11.03 |  |  |
| xPos (Sun et al., 2022) | 9.02 | 71.75 | 4.83 | 0.24 | 10.73 | 9.38 | 16.38 |  |  |
| TAPE (ours) | 11.52 | 72.80 | 6.79 | 11.60 | 12.42 | 10.34 | 15.18 |  |  |{{< /table-caption >}}

> 🔼 본 논문의 표 1은 SCROLLS 벤치마크의 7가지 데이터셋에서 다양한 위치 인코딩 방법들의 성능을 비교 분석한 표입니다.  구체적으로, QAS, CNLI, NQA, QuAL, QMS, SumS, GovR 데이터셋을 사용하여 F1 점수, EM 점수, ROUGE 점수 등의 다양한 지표를 통해 ROPE, ALiBi, RandPE, FIRE, xPos 등의 기존 방법들과 제안된 TAPE 방법의 성능을 비교하고 있습니다.  표는 각 방법의 성능 차이를 정량적으로 보여주어, TAPE의 우수성을 보다 명확히 설명하는 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Performance comparison on seven datasets from SCROLLS benchmark.
> </details>





### In-depth insights


#### Contextualized PE
본 논문에서 제시된 "Contextualized PE"는 기존의 위치 정보(Positional Encoding)에 문맥 정보(context)를 결합하여 **장점을 극대화**하고 **단점을 최소화**하는 접근 방식입니다.  **순차적 데이터 내 위치 정보 표현의 한계를 극복**하기 위해, 단순히 고정된 패턴을 사용하는 것이 아니라, 각 시퀀스의 내용에 따라 동적으로 위치 정보를 생성하고 업데이트합니다. 이는 단순히 위치 정보만으로는 표현하기 어려운 **장거리 의존성(long-range dependency)**이나 **다양한 작업(diverse tasks)**에 대한 적응력을 높일 수 있다는 것을 의미합니다. 또한, **매개변수 효율성(parameter efficiency)**을 고려하여 기존의 사전 훈련된 모델에 손쉽게 통합될 수 있도록 설계되었습니다.  이는 훈련 비용 및 시간을 절감하는 데 기여하며, 실제 응용에 있어서도 중요한 부분입니다.  **변환 불변성(equivariance)**을 통해 모델의 안정성과 일반화 성능을 향상시키는 것은 핵심적이며,  이는 다양한 시퀀스 길이 및 데이터 분포에 대해서도 뛰어난 성능을 보장합니다.  결과적으로, Contextualized PE는 Transformer 모델의 위치 정보 표현 능력을 크게 개선하고 다양한 언어 관련 작업에서 **성능 향상**을 가져올 것으로 기대됩니다.

#### Equivariance in TAPE
TAPE의 핵심적인 부분 중 하나는 **등변성(equivariance)** 개념을 도입하여 위치 정보를 처리하는 방식입니다.  기존의 위치 인코딩 방식들은 순열이나 변환에 대해 불변성을 유지하지 못하는 한계가 있었습니다. 하지만 TAPE는 **순열 등변성(permutation equivariance)**과 **직교 등변성(orthogonal equivariance)**을 만족하도록 설계되어, 입력 시퀀스의 순서가 바뀌거나 회전 변환이 적용되더라도 위치 정보의 안정성을 유지합니다. 이는 모델의 견고성과 다양한 작업에 대한 적응력을 향상시키는 중요한 요소입니다.  **다층 구조에서의 컨텍스트 정보 활용**을 통해 동적인 위치 인코딩을 생성하며, 고정된 패턴에 의존하는 기존 방식의 한계를 극복합니다. 이러한 등변성은 모델 업데이트 과정에서 위치 인코딩의 안정성을 보장하여, 강건하고 적응력 있는 모델을 만드는데 기여합니다.  결과적으로, TAPE는 **매개변수 효율적인 미세 조정**을 가능하게 하여, 계산 비용을 최소화하면서 성능을 향상시킵니다.

#### TAPE's Superiority
본 논문에서 제시된 TAPE(conTextualized equivariAnt Position Embedding)는 기존의 위치 인코딩 방식의 한계를 극복하고, **문맥 정보를 활용한 동적인 위치 인코딩**을 통해 성능 향상을 이끌어냈다는 점에서 우수성을 보입니다.  기존 방식들은 고정된 패턴이나 일반적인 바이어스에 의존하는 반면, TAPE는 계층 간의 시퀀스 내용을 통합하여 **다양한 작업과 인스턴스에 대한 적응력을 높였습니다.**  특히, 순열 및 직교 동변환 불변성을 통해 안정성과 일반화 능력을 향상시켰으며, 최소한의 오버헤드로 기존 트랜스포머 모델에 쉽게 통합될 수 있다는 장점도 있습니다.  **매개변수 효율적인 파인 튜닝**을 지원하여 실제 적용 가능성을 높였고, 다양한 실험 결과들을 통해 언어 모델링, 산술 추론, 장문맥 검색 작업에서 우수한 성능을 입증하였습니다.  이는 **위치 기반 주소 지정 메커니즘의 효율성을 크게 개선**시킨 것으로 해석되며, 향후 대규모 언어 모델의 성능 향상에 크게 기여할 것으로 기대됩니다.

#### Efficiency Analysis
논문의 '효율성 분석' 부분은 제안된 방법의 계산 비용과 기존 방법들과의 비교를 통해 모델의 효율성을 평가합니다. **계산 복잡도(FLOPs, MACs)와 매개변수 수**를 측정하여, 제안된 방법이 기존 방법들과 비슷하거나 더 적은 계산 비용으로 유사하거나 더 나은 성능을 달성함을 보여줍니다. 특히, **메모리 효율적인 어텐션 메커니즘과의 호환성**을 강조하며, 이를 통해 실제 구현에서의 효율성을 높일 수 있음을 시사합니다. 추가적으로, **실행 시간과 처리량**에 대한 실험 결과를 제시하여, 제안된 방법의 실질적인 효율성을 뒷받침합니다. 이러한 분석은 제안된 방법의 실용성을 높이는 중요한 근거가 됩니다.  **매개변수 효율적인 미세 조정** 가능성도 언급하며, 이를 통해 기존 모델에 쉽게 통합하여 효율적으로 성능을 개선할 수 있음을 강조합니다.

#### Future of TAPE
TAPE의 미래는 **매우 밝습니다**.  본 논문에서 제시된 맥락 기반 등변 위치 인코딩(TAPE)은 기존의 위치 인코딩 방식의 한계를 극복하고, **장거리 의존성을 더 잘 모델링**하며, 다양한 작업에 대한 **적응력을 향상**시키는 잠재력을 보여주었습니다.  **매개변수 효율적인 미세 조정** 가능성은 실제 적용에 있어 큰 장점입니다. 앞으로 TAPE는 더 큰 규모의 언어 모델에 통합되어 성능 향상을 이끌어낼 수 있으며, 특히 **장문 맥락 처리**가 중요한 분야에서 혁신적인 결과를 가져올 것으로 예상됩니다.  또한, TAPE의 **등변성 원리**는 다른 유형의 순차 데이터에도 적용될 수 있어, 이미지, 오디오, 비디오와 같은 다양한 모달리티의 모델링에도 활용될 수 있는 **범용적인 프레임워크**로 발전할 가능성이 높습니다.  **연구의 지속적인 발전**을 통해 TAPE는 더욱 강력하고 효율적인 위치 인코딩 기법으로 자리매김하여, 차세대 언어 모델의 핵심 구성 요소가 될 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.00712/x2.png)

> 🔼 그림 2는 서로 다른 위치 인코딩 방법(RoPE, RandPE, NoPE, FIRE, TAPE)을 사용하여 2배 길이의 문맥 길이에서 덧셈 문제에 대한 정확도를 비교한 열 지도를 보여줍니다. 모델은 최대 길이 40의 시퀀스로 학습되었고, 최대 길이 80의 시퀀스로 테스트되었습니다. 열 지도의 평균 정확도는 RoPE, RandPE, NoPE, FIRE, TAPE에 대해 각각 26.32%, 26.56%, 22.45%, 26.98%, 32.82%입니다. 이는 TAPE가 더 긴 시퀀스에 대해서도 우수한 일반화 성능을 보임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Accuracy on addition task between different methods on 2×\times× context length. Models are trained on sequence with length up to 40 while test on sequence with length up to 80. The average accuracy across the heatmap is 26.32%, 26.56%, 22.45%, 26.98% and 32.82% respectively for RoPE, RandPE, NoPE, FIRE and TAPE.
> </details>



![](https://arxiv.org/html/2501.00712/x3.png)

> 🔼 그림 3은 Llama2 7B 모델에 다양한 미세 조정 방법을 적용했을 때, 문맥 길이가 1k에서 8k로 증가함에 따라 패스키 검색 정확도가 어떻게 변하는지 보여줍니다.  다양한 미세 조정 기법(LoRA, LongLoRA, Theta Scaling, TAPE)의 성능을 비교하여, 각 기법이 문맥 길이 변화에 따른 검색 성능에 미치는 영향을 시각적으로 나타냅니다.  이를 통해 어떤 미세조정 방법이 긴 문맥에서의 패스키 검색에 가장 효과적인지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Accuracy on passkey retrieval from 1k to 8k context length between Llama2 7B with different fine-tuning methods.
> </details>



![](https://arxiv.org/html/2501.00712/x4.png)

> 🔼 그림 4는 TAPE의 동작을 시각적으로 보여줍니다. 채널 차원은 단순화를 위해 생략되었으며, 모든 연산은 채널별로 수행될 수 있습니다. 어텐션 레이어에서 입력 토큰 임베딩은 N×B의 형태를 가지며, 위치 임베딩은 N×L×R의 형태를 가집니다. 피드포워드 레이어의 경우, 연산이 위치별로 수행되므로 N 차원은 생략됩니다. 그 결과, 입력 토큰 임베딩은 B(또는 B×1)의 형태를 가지며, 위치 임베딩은 L×R의 형태를 가집니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Visualization of TAPE’s operations. The channel dimension is omitted for simplicity as all operations can be channel-wise. In the attention layer, the input token embeddings have a shape of N×B𝑁𝐵N\times Bitalic_N × italic_B, and the position embeddings have a shape of N×L×R𝑁𝐿𝑅N\times L\times Ritalic_N × italic_L × italic_R. For the feed-forward layer, the N𝑁Nitalic_N dimension is omitted as its operations are position-wise. The input token embeddings then have a shape of B𝐵Bitalic_B (or B×1𝐵1B\times 1italic_B × 1), and the position embeddings have a shape of L×R𝐿𝑅L\times Ritalic_L × italic_R.
> </details>



![](https://arxiv.org/html/2501.00712/x5.png)

> 🔼 그림 5는 길이 20으로 학습된 덧셈 문제에 대한 정확도를 보여줍니다. 테스트는 문맥 길이가 2배인 데이터셋을 사용하여 진행되었습니다.  히트맵의 평균 정확도는 RoPE, RandPE, FIRE 및 TAPE에 대해 각각 26.12%, 26.12%, 39.44%, 41.42%입니다.  즉, TAPE 모델이 다른 세 가지 방법보다 덧셈 문제 풀이 정확도가 더 높음을 보여줍니다.  특히, FIRE 및 TAPE는 긴 문맥을 다루는 데 상당히 효과적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Accuracy on addition task trained with length 20 test on 2×\times× context length. The average accuracy across the heatmap is 26.12%, 26.12%, 39.44% and 41.42% respectively for RoPE, RandPE, FIRE and TAPE.
> </details>



![](https://arxiv.org/html/2501.00712/x6.png)

> 🔼 그림 6은 맥락 길이가 두 배인 덧셈 문제에 대한 정확도를 보여줍니다.  각 모델의 평균 정확도는 FIRE의 경우 26.98%, TAPE의 경우 32.82%, TAPE + YaRN의 경우 33.92% 입니다. 이 그래프는 서로 다른 모델들이 다양한 길이의 덧셈 문제에 대해 어떻게 다른 성능을 보이는지 시각적으로 보여줍니다. 특히, TAPE와 TAPE + YaRN의 우수한 성능을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Accuracy on addition task on 2×\times× context length. The average accuracy is 26.98%, 32.82% and 33.92% respectively for FIRE, TAPE and TAPE + YaRN.
> </details>



![](https://arxiv.org/html/2501.00712/extracted/6105208/fig/vis_dp.png)

> 🔼 그림은 TAPE와 RoPE의 위치 임베딩의 점곱 패턴을 보여줍니다.  TAPE는 긴 범위의 토큰 간 관계에 더 고르게 주의를 기울이는 반면, RoPE는 토큰의 국지적인 관계에 더 집중하는 것을 보여줍니다. TAPE의 점곱 패턴은 깊이가 깊어짐에 따라 대각선 패턴이 감소하고, 격자와 같은 패턴이 형성되는 것을 보여줍니다. 이는 모델이 먼 토큰에 구조적이고 주기적인 방식으로 더 집중하기 시작함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (a)  Dot-product patterns of positional embeddings of TAPE and RoPE.
> </details>



![](https://arxiv.org/html/2501.00712/extracted/6105208/fig/vis_attn_diff.png)

> 🔼 그림은 TAPE와 RoPE의 어텐션 패턴 차이를 보여줍니다. TAPE는 긴 범위의 토큰에도 고르게 주의를 기울이는 반면, RoPE는 대각선 패턴에 집중하여 지역적인 어텐션을 강조합니다. TAPE의 경우, 깊이가 깊어짐에 따라 대각선 패턴이 줄어들고, 멀리 떨어진 토큰에 대한 주의가 체계적으로 증가합니다.
> <details>
> <summary>read the caption</summary>
> (b)  Difference between TAPE and RoPE
> </details>



![](https://arxiv.org/html/2501.00712/x7.png)

> 🔼 그림 7은 위치 정보 임베딩의 내적 패턴과 그에 따른 어텐션 차이를 TAPE와 RoPE 방법론 측면에서 비교한 것입니다. (a)는 TAPE가 상대적으로 작은 동적 범위를 가진 주변 토큰에 대한 체계적인 어텐션을 보여주는 반면, RoPE는 뚜렷한 검은색 영역을 가진 대각선 패턴이 매우 두드러지는 것을 보여줍니다. (b)는 TAPE가 자기 토큰에 대한 과도한 어텐션을 피하면서 장거리 토큰에 효과적으로 어텐션을 집중시키는 반면 RoPE는 그렇지 않다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Comparison of TAPE and RoPE methods in terms of positional embedding dot-product patterns and their resulting attention differences. (a) TAPE demonstrates a systematic attention to surrounding tokens with relatively small dynamic ranges, whereas RoPE exhibits a highly significant diagonal pattern with distinctively black regions. (b) TAPE effectively attends to longer-range tokens, avoiding excessive attention to the self-token, in contrast to RoPE.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | Proof-pile 1024 | Proof-pile 2048 | Proof-pile 4096 | Proof-pile 8192 | PG19 1024 | PG19 2048 | PG19 4096 | PG19 8192 |
|---|---|---|---|---|---|---|---|---|
| LoRA | 3.828 | 3.369 | 3.064 | 2.867 | 9.791 | 9.098 | 8.572 | 8.199 |
| LongLoRA | 3.918 | 3.455 | 3.153 | 2.956 | 9.989 | 9.376 | 8.948 | 8.645 |
| Theta Scaling | 3.864 | 3.415 | 3.121 | 2.934 | 9.257 | 8.640 | 8.241 | 7.999 |
| TAPE | 3.641 | 3.196 | 2.901 | 2.708 | 8.226 | 7.642 | 7.278 | 7.063 |{{< /table-caption >}}
> 🔼 표 2는 다양한 문맥 길이에 따른 perplexity 평가 결과를 보여줍니다.  다양한 길이의 시퀀스에 대해 여러 모델의 perplexity 값을 비교하여 모델의 긴 문맥 처리 성능을 평가합니다.  구체적으로는  Proof-pile 과 PG19 데이터셋의 1024, 2048, 4096, 8192 토큰 길이에 대한 perplexity 수치를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Evaluation on perplexity across different context lengths.
> </details>

{{< table-caption >}}
| Method | TAPE | RoPE | FIRE | T5's relative bias |
|---|---|---|---|---|
| FLOPS (G) | 365.65 | 321.10 | 331.97 | 321.10 |
| MACs (G) | 180.69 | 160.46 | 165.69 | 160.46 |
| Params. (M) | 155.33 | 154.89 | 154.90 | 154.90 |{{< /table-caption >}}
> 🔼 본 표는 서로 다른 위치 인코딩 방식을 사용하는 모델들의 FLOPS, MACs 및 파라미터 수를 비교하여 효율성을 분석한 결과를 보여줍니다.  TAPE, ROPE, FIRE 및 T5의 상대적 편향 등 다양한 위치 인코딩 기법을 적용한 모델들의 성능을 계산량 측면에서 비교 분석합니다.  이를 통해 TAPE 모델의 효율성을 기존 방법들과 비교하여 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Comparison of FLOPS, MACs, and the number of parameters for models with different position embeddings.
> </details>

{{< table-caption >}}
| Method | TAPE w/ Fusion | TAPE w/o Fusion | RoPE | FIRE | T5's relative bias |
|---|---|---|---|---|---| 
| Time (×10⁻⁴) | 2.56 | 5.63 | 2.08 | 5.56 | 6.90 |
| Throughput | 3910 | 1775 | 4810 | 1799 | 1449 |
| Flash Attention | ✓ | ✓ | ✓ | ✗ | ✗ |{{< /table-caption >}}
> 🔼 표 4는 시스템 성능 측정 결과를 보여줍니다.  '시간' 행은 100회의 추론 단계에 걸친 평균 실행 시간을, '처리량' 행은 초당 반복 횟수를 나타냅니다. 이 표는 TAPE, RoPE, FIRE 및 T5의 상대적 편향을 가진 모델의 성능을 비교 분석하여 효율성을 평가하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 4: System measurement. We report execution time per step in the Time row and iteration per second in the Throughput row. The values are averaged over 100 inference steps.
> </details>

{{< table-caption >}}
| Method | Setting | 
|---|---| 
| Arithmetic (§4.1) | Sequence length: 80 | 
|  | Batch size: 512 | 
|  | Number of iterations: 20k | 
|  | Attention dropout prob.: 0.0 | 
|  | Optimizer: AdamW | 
|  | Learning rate: 1e-4 | 
| C4 Pre-training (§4.2) | Sequence length: 1024 | 
|  | Batch size: 512 | 
|  | Number of iterations: 10k | 
|  | Attention dropout prob.: 0.0 | 
|  | Optimizer: AdamW | 
|  | Learning rate: 1e-4 | 
| SCROLLS (§4.2) | Sequence length: 1024 | 
|  | Batch size: 64 | 
|  | Number of iterations: 1k | 
|  | Attention dropout prob.: 0.0 | 
|  | Optimizer: AdamW | 
|  | Learning rate: 1e-5 | 
| Context Extension (§4.3) | Sequence length: 8096 | 
|  | Batch size: 64 | 
|  | Number of iterations: 1k | 
|  | Attention dropout prob.: 0.0 | 
|  | Optimizer: AdamW | 
|  | Learning rate: 2e-5 | {{< /table-caption >}}
> 🔼 표 5는 논문의 실험에서 사용된 언어 모델 사전 학습 및 미세 조정에 대한 교육 설정을 보여줍니다. 표에는 각 실험 설정에 대한 시퀀스 길이, 배치 크기, 반복 횟수, 어텐션 드롭아웃 확률, 최적화기, 학습률 등의 세부 정보가 포함되어 있습니다. 사전 학습 및 미세 조정 모두에 대해 세 가지 실험 설정이 있습니다. 이 표는 논문의 실험 부분을 이해하는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Training recipe for language model pre-training and fine-tuning in experiments.
> </details>

{{< table-caption >}}
| Architecture | Perplexity |
|---|---|---|---|---|
| **Attention** | **Feed Forward** | **128** | **256** | **512** | **1024** |
| ✗ | ✗ | 139.2 | 92.8 | 69.3 | 57.2 |
| ✗ | ✓ | 143.3 | 95.0 | 70.7 | 58.4 |
| ✓ | ✗ | 142.7 | 94.3 | 70.1 | 57.6 |
| ✓ | ✓ | 132.0 | 86.6 | 63.9 | 52.2 |
| **Rotation Equivariance** | **Tensorial Embedding** |  |  |  |  |
| ✗ | ✗ | 140.7 | 92.1 | 68.2 | 56.2 |
| ✓ | ✗ | 138.4 | 91.3 | 67.8 | 55.7 |
| ✗ | ✓ | 132.9 | 87.8 | 65.4 | 54.1 |
| ✓ | ✓ | 132.0 | 86.6 | 63.9 | 52.2 |{{< /table-caption >}}
> 🔼 표 6은 TAPE 아키텍처에 대한 ablation 연구 결과를 보여줍니다.  다양한 시퀀스 길이에 대해 사전 훈련된 모델의 perplexity를 GitHub 테스트 세트에서 평가했습니다.  구체적으로, 어텐션 레이어와 MLP 레이어의 아키텍처 디자인, 회전 등변성(rotation equivariance), 텐서 임베딩(tensorial embedding)의 세 가지 측면에 대한 ablation 실험을 수행하여 각 요소가 모델 성능에 미치는 영향을 분석했습니다.  표에는 각 ablation 설정에 대한 perplexity 값이 다양한 시퀀스 길이에 대해 제시되어 있으며, 이를 통해 TAPE 아키텍처의 각 구성 요소의 중요성을 정량적으로 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Ablation study on TAPE architecture. We evalute pre-trained models’ perplexity across varying sequence lengths on the GitHub test set.
> </details>

{{< table-caption >}}
| **TAPE** | **Perplexity** |  |  |  |  |
|---|---|---|---|---|---| 
| **Added Params. (M)** | **$I$** | **128** | **256** | **512** | **1024** |
| 0.11 | 12 | 133.2 | 87.9 | 65.2 | 53.6 |
| 0.22 | 24 | 133.0 | 86.1 | 63.2 | 51.8 |
| 0.44 | 48 | 132.0 | 86.6 | 63.9 | 52.2 |
| 0.88 | 96 | 133.2 | 87.5 | 64.5 | 52.7 |
| 1.76 | 192 | 133.0 | 87.3 | 64.5 | 53.0 |{{< /table-caption >}}
> 🔼 표 7은 TAPE의 하이퍼파라미터 I의 영향을 평가하기 위한 실험 결과를 보여줍니다.  다양한 길이의 시퀀스에 대해 사전 훈련된 모델의 perplexity를 GitHub 테스트 세트에서 측정하였습니다.  이 표는 하이퍼파라미터 I의 값을 변경했을 때 perplexity에 어떤 영향이 있는지 보여줌으로써 최적의 I 값을 찾는 데 도움이 됩니다.  결과적으로, I의 값은 모델 성능에 미치는 영향이 제한적이지만 2H 에서 4H 사이의 값이 성능에 더 나은 결과를 가져오는 경향을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Ablation study on TAPE hyperparameter I𝐼Iitalic_I. We evalute pre-trained models’ perplexity across varying sequence lengths on the GitHub test set.
> </details>

{{< table-caption >}}
| Atten. Diff. (<math>\times 10^{-2}</math>) | Add Tokens |  |  |  | Shift IDs |  |  |  |  |
|---|---|---|---|---|---|---|---|---|---| 
|  | Layer 1 | Layer 2 | Layer 4 | Layer 8 | Layer 1 | Layer 2 | Layer 4 | Layer 8 |
|---|---|---|---|---|---|---|---|---|---|
| RoPE | 8.93 | 8.51 | 12.29 | 11.46 | 0.01 | 0.02 | 0.02 | 0.03 |
| TAPE | 9.08 | 11.24 | 12.23 | 13.78 | 0.01 | 0.02 | 0.04 | 0.04 |
| w/o EQ | 11.30 | 11.38 | 13.32 | 14.55 | 0.01 | 0.24 | 0.37 | 0.51 |{{< /table-caption >}}
> 🔼 표 8은 위치 이동에 따른 RoPE, TAPE 및 동변환 없는 TAPE의 비교를 보여줍니다.  위치 이동 방법은 두 가지로, 세 개의 [BOS] 토큰 추가 및 시작 위치 ID를 3으로 설정하는 방법입니다. 이 표는 두 가지 위치 이동 방법에 대해 각 층에서 어텐션 가중치(위쪽)와 위치 임베딩 내적(아래쪽)의 차이를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Comparison of RoPE, TAPE, and TAPE without equivariance (w/o EQ) under positional shifts. The table shows differences in attention weights (top) and positional embedding dot products (bottom) across layers for two shift methods: adding three [BOS] tokens (“Add Tokens”) and starting position IDs at 3 (“Shift IDs”).
> </details>

{{< table-caption >}}
| PE Dot Prod. | Diff. (%) | Add Tokens |  |  |  |  | Shift IDs |  |  |  |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|  |  | Layer 1 | Layer 2 | Layer 4 | Layer 8 | Layer 1 | Layer 2 | Layer 4 | Layer 8 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| RoPE | 0.03 | 0.03 | 0.03 | 0.03 | 0.03 | 0.03 | 0.03 | 0.03 | 0.03 |
| TAPE | 0.03 | 0.37 | 2.75 | 6.62 | 0.03 | 0.02 | 0.03 | 0.04 |
| w/o EQ | 0.03 | 2.29 | 3.34 | 6.37 | 0.03 | 0.54 | 0.44 | 0.86 |{{< /table-caption >}}
> 🔼 표 9는 다양한 방법들을 사용하여 측정된 여러 벤치마크에 대한 정확도를 백분율로 나타낸 것입니다.  MMLU(Massive Multitask Language Understanding) 및 ARC(AI2 Reasoning Challenge) 벤치마크의 하위 벤치마크(인문학, 사회과학, STEM, 기타, ARC Challenge, ARC Easy) 별로 LoRA, LongLoRA, ThetaScaling, TAPE의 정확도를 비교하여 보여줍니다. 이 표는 TAPE 모델의 성능을 다른 기존 방법들과 비교 분석하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Accuracy in Percentage Across Methods and Benchmarks
> </details>

{{< table-caption >}}
| Method | Humanities | Social Sciences | STEM | Other | ARC Challenge | ARC Easy |
|---|---|---|---|---|---|---|
| LoRA | 39.09 ± 0.69 | 46.47 ± 0.88 | 33.65 ± 0.83 | 45.83 ± 0.89 | 45.31 ± 1.45 | 74.28 ± 0.90 |
| LongLoRA | 37.53 ± 0.69 | 43.55 ± 0.88 | 32.54 ± 0.83 | 43.84 ± 0.88 | 45.31 ± 1.45 | 74.16 ± 0.90 |
| ThetaScaling | 37.45 ± 0.69 | 43.16 ± 0.88 | 33.05 ± 0.83 | 44.64 ± 0.88 | 45.65 ± 1.46 | 74.24 ± 0.90 |
| TAPE | 37.96 ± 0.69 | 45.40 ± 0.88 | 33.27 ± 0.83 | 45.06 ± 0.88 | 46.25 ± 1.46 | 74.16 ± 0.90 |{{< /table-caption >}}
> 🔼 본 표는 QuALITY 데이터셋의 두 질문에 대해 다양한 positional encoding 방법(TAPE, RoPE, xPos, RandPE, ALiBi)의 답변을 비교 분석한 결과를 보여줍니다. 각 방법의 정답 여부(EM)를 표시하여, TAPE의 성능 우수성과 다른 방법들의 한계점을 보여줍니다.  특히, TAPE는 정답 또는 정답과 유사한 답변을 생성하지만, 다른 방법들은 부정확하거나 비문맥적인 답변을 생성하는 경우가 많음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Comparing answers of different methods on example questions in QuALITY.
> </details>

{{< table-caption >}}
| Method | Question A | EM | Question B | EM |
|---|---|---|---|---|
| Ground Truth | The secret service budget was small | ✓ | Only the private quarters or the office restroom | ✓ |
| TAPE | The secret service budget was small | ✓ | Only the private quarters | ✗ |
| xPos | They were all they were waiting for | ✗ | Only a tiny part of the right of the right to leave foreverish | ✗ |
| RandPE | Their human opinion was trusted by others who have trust the services of their people | ✗ | Only a handsome man | ✗ |
| RoPE | Their orless them together with their repories did not only they didn’s never done was never done was never done… (repeating) | ✗ | The/O only the full-College All of the full-College All of the full-College… (repeating) | ✗ |
| ALiBi | Jimmy Carter is the president’s de facto president | ✗ | Jimmy Carter is the president’s de facto president | ✗ |{{< /table-caption >}}
> 🔼 표 11은 논문의 QuALITY 섹션에서 예시로 제시된 질문들을 보여줍니다.  각 질문은 QuALITY 데이터셋에 속하며, 긴 본문을 바탕으로 답을 유추해야 하는 특징을 가지고 있습니다.  표는 각 질문에 대한 맥락 정보와 정답 후보를 포함하고 있으며, 이를 통해  모델이 긴 문맥을 이해하고 정답을 도출하는 능력을 평가하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 11: Example Questions in QuALITY
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