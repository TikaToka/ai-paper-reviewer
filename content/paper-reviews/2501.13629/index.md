---
title: "Sigma: Differential Rescaling of Query, Key and Value for Efficient Language Models"
summary: "SIGMA는 질의, 키, 값 벡터를 차별적으로 재조정하여 대규모 언어 모델의 추론 속도를 최대 33.36% 향상시키는 효율적인 언어 모델입니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Microsoft Research",]
showSummary: true
date: 2025-01-23
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.13629 {{< /keyword >}}
{{< keyword icon="writer" >}} Zhenghao Lin et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-24 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.13629" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.13629" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/sigma-differential-rescaling-of-query-key-and" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

본 연구는 시스템 도메인에 특화된 효율적인 대규모 언어 모델인 SIGMA를 소개합니다. 기존 모델들은 키와 값 벡터의 압축에 있어서 균일한 접근 방식을 취했으나, SIGMA는 **질의(Q), 키(K), 값(V) 벡터의 영향력 차이를 고려하여 차별적인 최적화 전략**을 적용했습니다. 이를 통해, 특히 장문 컨텍스트에서 추론 속도를 크게 향상시켰습니다.  



SIGMA는 **6조 개의 토큰으로 사전 훈련**되었으며, 그중 195억 개는 연구진이 직접 수집한 시스템 도메인 데이터입니다. 실험 결과, SIGMA는 일반 도메인에서는 다른 최첨단 모델들과 비슷한 성능을 보였지만, 시스템 도메인에서는 모든 작업에서 뛰어난 성능을 보였고, 특히 GPT-4보다 최대 52.5%의 성능 향상을 달성했습니다.  또한, 연구진은 시스템 도메인 작업의 성능 평가를 위한 **종합적인 벤치마크 AIMICIUS**를 새롭게 제시했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 차별적 재조정(DiffQKV)을 통해 대규모 언어 모델의 추론 속도를 최대 33.36% 향상시켰습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 시스템 도메인에 특화된 6조 토큰의 데이터셋을 사용하여, 시스템 도메인 작업에서 GPT-4를 능가하는 성능을 달성했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 새로운 시스템 도메인 벤치마크 AIMICIUS를 제시하여, 시스템 도메인에서의 모델 성능을 종합적으로 평가할 수 있는 기준을 마련했습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대규모 언어 모델의 추론 효율성을 크게 향상시키는 새로운 방법론**을 제시하여, 시스템 도메인에서의 성능을 획기적으로 개선했습니다. 이는 시스템 도메인 연구의 새로운 지평을 열고, 향후 관련 연구의 발전에 중요한 영향을 미칠 것으로 예상됩니다. 또한, **제한된 자원 환경에서도 효율적으로 대규모 언어 모델을 활용할 수 있는 가능성**을 제시하여, 실용적인 측면에서도 큰 의의를 지닙니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.13629/x1.png)

> 🔼 그림 1은 제안된 DiffQKV 어텐션 메커니즘을 기존의 MHA, MQA, GQA와 비교하여 보여줍니다. DiffQKV 어텐션은 (1) K와 V 성분의 차등 압축: K 성분의 헤드 수와 차원을 V 성분보다 더 공격적으로 압축하여 K 캐시 크기를 더욱 효과적으로 줄입니다. 선택적 V 캐시 페칭을 통해 V 압축을 추가적으로 적용할 수도 있습니다. (2) 증강된 Q: KV 헤드보다 더 높은 차원을 Q 헤드에 적용하여 모델의 표현 능력을 향상시키는 두 가지 주요 기술을 포함합니다.  이 그림은 각 어텐션 메커니즘의 Q, K, V 벡터의 크기와 캐시 메모리 사용 방식을 시각적으로 보여주어 DiffQKV 어텐션의 효율성을 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Overview of our proposed method for differential rescaling of QKV, compared alongside Multi-Head Attention (MHA), Multi-Query Attention (MQA), and Grouped Query Attention (GQA). Specifically, our method involves: (1) differentially compressed KV: applying more aggressive compression on the number of K heads and their dimensions than on the V components, which more significantly reduces the size of K cache. We can also optionally adopt selective V cache fetching for V compression; (2) augmented Q: adopting a higher dimension for the Q head compared to the KV heads.
> </details>





{{< table-caption >}}
| Model | Overall | Hella. | ObQA | Wino. | ARC. | PIQA | SciQ | Bool. | Logi. | LAMB. |
|---|---|---|---|---|---|---|---|---|---|---|
| **MHA** ($n_{k}^{h}$=$n_{v}^{h}$=32) | **52.40** | 55.6 | 37.6 | 57.6 | 36.0 | 73.9 | 85.5 | 59.6 | 28.9 | 36.8 |
| -50% V Heads ($n_{v}^{h}$=16) | **51.74** (<span class="ltx_font_medium">↓0.66)</span> | 55.5 | 39.6 | 55.0 | 35.9 | 71.6 | 85.9 | 56.9 | 28.3 | 37.0 |
| -50% K Heads ($n_{k}^{h}$=16) | **52.83** (<span class="ltx_font_medium"><span class="ltx_framed ltx_framed_underline">↑0.43)</span></span> | 55.1 | 38.8 | 56.4 | 35.8 | 71.9 | 85.2 | 63.6 | 29.0 | 39.7 |
| **GQA** ($n_{k}^{h}$=$n_{v}^{h}$=16) | **52.14** | 55.1 | 39.6 | 56.3 | 35.4 | 71.9 | 85.0 | 61.4 | 27.8 | 36.8 |
| -75% V Heads ($n_{v}^{h}$=4) | **51.76** (<span class="ltx_font_medium">↓0.38)</span> | 54.0 | 38.2 | 55.6 | 34.8 | 72.7 | 85.0 | 60.3 | 29.9 | 35.3 |
| -75% K Heads ($n_{k}^{h}$=4) | **51.97** (<span class="ltx_font_medium"><span class="ltx_framed ltx_framed_underline">↓0.17)</span></span> | 54.6 | 37.8 | 57.1 | 35.1 | 72.3 | 84.1 | 62.5 | 28.3 | 36.0 |
| **GQA** ($n_{k}^{h}$=$n_{v}^{h}$=4) | **51.66** | 54.0 | 38.0 | 56.0 | 37.5 | 72.3 | 82.0 | 61.3 | 28.6 | 35.4 |
| -75% V Heads ($n_{v}^{h}$=1) | **51.03** (<span class="ltx_font_medium">↓0.63)</span> | 53.5 | 38.4 | 57.0 | 35.1 | 72.1 | 82.6 | 56.9 | 28.4 | 35.1 |
| -75% K Heads ($n_{k}^{h}$=1) | **51.67** (<span class="ltx_font_medium"><span class="ltx_framed ltx_framed_underline">↑0.01)</span></span> | 53.9 | 36.2 | 58.6 | 36.9 | 71.1 | 83.5 | 60.7 | 28.7 | 35.5 |{{< /table-caption >}}

> 🔼 이 표는 동일한 수의 K 헤드와 V 헤드를 줄였을 때 모델 성능을 비교한 결과를 보여줍니다. 모든 모델에 대해 Q 헤드의 수는 32로 고정되었습니다. 결과는 K 헤드의 수를 줄이는 것이 전체 모델 성능에 미치는 영향이 상대적으로 작다는 것을 보여줍니다. 즉, K 헤드의 차원과 개수를 줄이는 것이 모델 성능에 미치는 영향이 V 헤드보다 상대적으로 적다는 것을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparisons of model performance when reducing the same number of K heads versus V heads. The number of Q heads is 32 for all models (nqh=32superscriptsubscript𝑛𝑞ℎ32n_{q}^{h}=32italic_n start_POSTSUBSCRIPT italic_q end_POSTSUBSCRIPT start_POSTSUPERSCRIPT italic_h end_POSTSUPERSCRIPT = 32). The results show that compressing the number of K heads has a relatively smaller impact on the overall model performance.
> </details>





### In-depth insights


#### DiffQKV Attention
DiffQKV 어텐션은 기존의 어텐션 메커니즘의 효율성을 개선하기 위해 **쿼리(Q), 키(K), 밸류(V) 벡터들을 차별적으로 최적화**하는 새로운 아키텍처입니다.  **K와 V 벡터의 압축에 대한 모델의 민감도 차이**를 이용하여 K 벡터에는 더 공격적인 압축을, V 벡터에는 가벼운 압축을 적용합니다.  **어텐션 스코어의 높은 스파스성**을 활용하여 V 벡터를 선택적으로 로딩하여 메모리 사용량을 줄입니다.  또한, **Q 벡터의 차원을 확장**하여 모델의 표현 능력을 향상시키는 동시에 추론 속도에 미치는 영향을 최소화합니다.  이러한 차별적인 최적화 전략을 통해 DiffQKV 어텐션은 기존의 그룹 쿼리 어텐션(GQA)에 비해 추론 속도를 최대 33.36%까지 향상시키는 효율성을 제공합니다.  **특히 긴 문맥의 상황**에서 효과적이며, 시스템 도메인에 특화된 대규모 언어 모델에서의 효율성을 크게 높일 수 있습니다.

#### SIGMA Architecture
SIGMA 아키텍처는 **차별적 QKV 재조정(DiffQKV)** 어텐션 메커니즘을 중심으로 설계되었습니다. DiffQKV 어텐션은 **쿼리(Q), 키(K), 값(V) 벡터의 차원과 헤드 수를 다르게 조정**하여 기존의 어텐션 메커니즘의 병목 현상인 KV 캐시 문제를 해결합니다.  **K 벡터에 더 공격적인 압축을 적용하고 V 벡터는 가볍게 압축**하며, **Q 벡터의 차원을 확장**하여 모델의 표현 능력을 향상시키는 전략을 사용합니다. 이를 통해 연산 효율성을 높이고 메모리 사용량을 줄여 추론 속도를 향상시키는 효과를 거둘 수 있습니다.  **대규모 시스템 도메인 데이터를 사용**하여 사전 훈련된 SIGMA는 **시스템 도메인 특화 모델**로서 기존 모델들보다 뛰어난 성능을 보입니다. 특히, 새롭게 제시된 AIMICIUS 벤치마크에서 GPT-4를 상회하는 성능을 보여주는 것은 주목할 만한 부분입니다.  **모델의 효율성을 극대화**하기 위해 이론적 분석과 실험적 검증을 통해 최적의 QKV 구성을 찾았다는 점도 중요한 특징입니다.  **다양한 시스템 도메인 작업에 대한 뛰어난 성능**과 **향상된 추론 효율성**을 통해 SIGMA 아키텍처는 대규모 언어 모델의 효율성과 성능을 모두 개선하는 혁신적인 접근 방식임을 제시합니다.

#### System Domain Data
시스템 도메인 데이터는 시스템 영역에 특화된 대규모 언어 모델을 학습시키는 데 사용되는 데이터셋입니다.  **다양한 시스템 관련 웹사이트에서 수집된 195억 개의 토큰과 합성 및 재작성된 1조 개의 토큰**을 포함하여 총 6조 개의 토큰으로 구성되어 있습니다. 특히, **Azure 서비스를 기반으로 명령 생성, 벤치마크 검색, 토폴로지 최적화, 인프라 문제 분석 등 시스템 도메인 작업에 중점을 둔 15가지 주요 소스 카테고리를 신중하게 식별**하여 수집되었습니다. 이러한 데이터셋은 시스템 도메인에 대한 **포괄적인 벤치마크인 AIMICIUS**를 구축하는 데에도 사용되었습니다.  **데이터 품질을 보장하기 위해 철저한 검증 과정**을 거쳤고, 다양한 출처에서 얻은 데이터들을 균형 있게 포함하여 일반 도메인에서도 우수한 성능을 발휘하도록 설계되었습니다.  **시스템 도메인 특화 모델 학습에 필수적인 고품질 데이터**이며, **AIMICIUS 벤치마크의 신뢰성을 높이는데 기여**했습니다.

#### Efficiency Analysis
본 논문의 효율성 분석 부분은 **SIGMA 모델의 추론 속도 향상을 위한 DiffQKV 어텐션 메커니즘의 효과**를 이론적, 실험적으로 검증하는 데 초점을 맞춥니다. 이론적 분석에서는 DiffQKV 어텐션의 KV 캐시 크기 감소 및 어텐션 계산량 감소 효과를 수식으로 제시하여 **최대 37.5%의 속도 향상 가능성**을 예측합니다. 실험적 분석에서는 CUDA 이벤트 경과 시간 및 커널 실행 시간 측정을 통해 SIGMA가 기존 GQA 모델 대비 **추론 속도를 최대 33.36% 향상**시켰음을 보여줍니다. 특히 긴 컨텍스트 시나리오에서 효율성 향상이 두드러지게 나타나는데, 이는 **KV 캐시 크기 감소 및 어텐션 계산량 감소** 효과와 밀접한 관련이 있습니다.  **Augmented Q의 효과**도 검증하며, 추가적인 파라미터 투입으로 인한 성능 향상과 그로 인한 효율성 개선에 대한 심도 있는 분석이 이루어집니다.  결론적으로, 본 논문의 효율성 분석은 SIGMA 모델의 **차별화된 설계 및 최적화 기법**의 효과를 정량적으로 입증하며, 대규모 언어 모델의 효율성 향상에 대한 중요한 시사점을 제공합니다.

#### Future Work
논문의 "향후 연구" 부분에서 제시된 아이디어들은 주로 **SIGMA 모델의 효율성을 더욱 개선**하고 **시스템 도메인에 대한 적용 범위를 확장**하는 데 초점을 맞추고 있습니다.  **DiffQKV 어텐션 모듈의 아키텍처 최적화**, 특히 **Augmented Q와 FFN 파라미터 간의 최적 균형점**을 찾는 연구가 필요합니다. 또한, **다양한 시스템 도메인 과제들에 대한 SIGMA 모델의 성능 평가**를 통해 실제 적용 가능성을 더욱 높여야 합니다.  **합성 데이터 의존도 감소**를 위한 자기 진화 및 평생 학습 기법 도입도 중요한 연구 과제입니다.  궁극적으로는 **다양한 시스템 도메인 문제에 대한 SIGMA의 확장성과 효율성을 더욱 향상**시켜야 합니다. 이를 통해 더욱 강력하고 효율적인 대규모 언어 모델 개발에 기여할 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/kernel_cost_split.png)

> 🔼 그림 2는 FlexHeadFA의 분할 커널과 결합 커널에 대한 Kernel Execution Time(KET)을 표현합니다.  표현된 내용은 표준 모델(STD)과 SIGMA 모델의 두 가지 모델에 대한 것입니다.  x축은 접두사 길이를 나타내고, y축은 각 커널에 대한 KET(나노초 단위)를 보여줍니다. 이 그래프는 접두사 길이에 따른 분할 커널과 결합 커널의 KET을 비교하여 FlexHeadFA의 효율성을 평가하는 데 사용됩니다.  즉, 접두사의 길이가 길어짐에 따라 분할 커널과 결합 커널의 처리 시간이 어떻게 변하는지, 그리고 SIGMA 모델이 STD 모델에 비해 얼마나 효율적인지를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (a) KET of the split kernel.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/kernel_cost_combine.png)

> 🔼 그림 2(b)는 FlexHeadFA의 두 번째 주요 GPU 커널 연산인 `flash_fwd_splitkv_combine_kernel`의 수행 시간(KET)을 나타냅니다. 이 커널은 분할된 출력 청크를 완전한 출력 행렬로 조립하는 역할을 합니다. 그래프는 프리픽스 길이가 증가함에 따라 이 커널의 비용이 어떻게 변하는지 보여줍니다. 표 8에서 볼 수 있듯이, 프리픽스 길이가 증가함에 따라 이 커널의 비용 증가율은 첫 번째 커널보다 훨씬 느립니다. 이는 전체 계산 시간에서 차지하는 비율이 점차 감소함을 의미합니다. 상대적 개선율 측면에서는 프리픽스 길이가 증가함에 따라 효율성 향상이 점점 더 두드러지게 나타납니다.
> <details>
> <summary>read the caption</summary>
> (b) KET of the combine kernel.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/kernel_cost_tot.png)

> 🔼 그림 2는 표준 모델(STD)과 SIGMA의 FlexHeadFA 간의 KET(커널 실행 시간) 비교를 보여줍니다. (c)는 split 및 combine 커널의 KET 합계를 나타내는 총 KET 값을 보여줍니다. 그래프는 접두사 길이가 증가함에 따라 총 KET가 증가함을 보여주며, SIGMA가 STD보다 훨씬 효율적임을 나타냅니다. 이는 SIGMA가 채택한 DiffQKV 어텐션 메커니즘의 효율성 개선을 실증적으로 보여주는 결과입니다.
> <details>
> <summary>read the caption</summary>
> (c) Total KET.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/augq_cost_2k.png)

> 🔼 본 그림은 논문의 DiffQKV Attention 섹션에 포함되어 있으며, 표준 모델(Std)과 SIGMA 모델에서 FlexHeadFA의 성능을 비교 분석한 결과를 보여줍니다.  구체적으로, split kernel과 combine kernel의 Kernel Execution Time (KET)을 prefix length에 따라 비교하여 SIGMA 모델의 효율성 향상을 시각적으로 보여주고 있습니다.  그래프는 prefix length가 증가함에 따라 두 모델 모두 KET가 증가하지만, SIGMA 모델의 증가폭이 훨씬 작다는 것을 보여줍니다. 이는 SIGMA 모델의 DiffQKV attention 메커니즘이 KV cache 부하를 줄여 Inference 속도를 향상시키는 효과를 명확히 보여주는 결과입니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: KET comparison of FlexHeadFA between Standard model(Std) and Sigma.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/augq_cost_4k.png)

> 🔼 그림은 3.3절 실험 설정에서 언급된 Cuda 이벤트 경과 시간(CEET) 측정 방법을 사용하여 획득한 결과를 보여줍니다.  구체적으로는,  출력 토큰 길이가 2k일 때,  다양한 길이의 접두사(prefix)에 따른 계산 시간을 나타냅니다. 이는 SIGMA 모델의 효율성을 평가하기 위한 실험의 일부이며, 접두사 길이가 증가함에 따라 계산 시간이 어떻게 변하는지 보여줍니다.  결과는 다양한 길이의 컨텍스트에서 SIGMA의 효율성을 평가하는 데 중요한 역할을 합니다.  STD(표준 모델)와 비교하여 SIGMA의 성능을 분석하는 데 사용됩니다. 이를 통해 SIGMA 모델의 효율성 및 성능에 대한 통찰력을 얻을 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (a) Output Length =2⁢kOutput Length 2𝑘\text{Output Length }=2kOutput Length = 2 italic_k.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/augq_cost_8k.png)

> 🔼 그림 (b)는 출력 길이가 4k 토큰일 때, 표준 모델(STD)과 SIGMA 모델의 split 커널 및 combine 커널에 대한 Kernel Execution Time (KET)을 비교한 그래프입니다.  x축은 접두사 길이(prefix length)를 나타내고, y축은 각 커널의 수행 시간(KET, ns)을 나타냅니다.  이 그래프는 접두사 길이가 증가함에 따라 각 모델의 split 커널과 combine 커널의 수행 시간 변화를 보여줍니다.  특히 SIGMA 모델이 STD 모델보다 KET이 더 짧은 것을 확인할 수 있으며, 접두사 길이가 길어질수록 SIGMA 모델의 효율성이 더욱 향상됨을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) Output Length =4⁢kabsent4𝑘=4k= 4 italic_k.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/augq_cost_16k.png)

> 🔼 그림은 논문의 3.3절(실험적 분석)에서 SIGMA 모델과 기준 모델(STD)의 효율성을 비교 분석한 결과를 보여줍니다.  (c)는 출력 길이가 8,000 토큰일 때의 결과를 보여주는 부분입니다. 이 그림은  FlashAttention의 split kernel과 combine kernel의 수행 시간(KET, Kernel Execution Time)을 측정하여 SIGMA와 STD를 비교한 것입니다.  세부적으로는 split kernel과 combine kernel 각각의 KET 값과 전체 KET 값을 나타내며,  프리픽스 길이(Prefix Length)에 따른 성능 변화를 보여줍니다.  즉,  모델이 얼마나 효율적으로 어텐션 연산을 수행하는지를  프리픽스 길이와 출력 길이라는 두 가지 변수에 따라 정량적으로 비교하고 있습니다.
> <details>
> <summary>read the caption</summary>
> (c) Output Length =8⁢kabsent8𝑘=8k= 8 italic_k.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/augq_cost_32k.png)

> 🔼 그림 (d)는 컨텍스트 길이(prefix length)가 다양하게 변화하는 상황에서 모델의 출력 길이가 16k 토큰으로 고정되었을 때의 결과를 보여줍니다.  이 그림은 다양한 prefix length에 따른  모델의 처리 시간을 비교 분석하여, SIGMA 모델의 효율성을 보여주는 실험 결과를 시각적으로 나타낸 것입니다.  x축은 prefix length를, y축은 계산 시간(ms)을 나타내며, SIGMA와 STD 모델의 성능을 비교하여 각 prefix length에 대한 효율성 향상을 분석합니다. 이를 통해 prefix 길이에 따른 SIGMA 모델의 처리 시간 변화와 STD 모델과의 성능 차이를 명확하게 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (d) Output Length =16⁢kabsent16𝑘=16k= 16 italic_k.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/augq_cost_64k.png)

> 🔼 그림은 논문의 3.3.2절 실험 결과 부분에 있는 그림 3의 (e) 부분입니다. 이 그림은  FlexHeadFA의 두 가지 모델(표준 모델(STD)과 SIGMA)의 성능을 비교하는데, 특히 접두사 길이가 증가함에 따라  kernel 실행 시간을 보여줍니다. 세로축은 kernel 실행 시간(KET, ns 단위)이고 가로축은 접두사 길이(prefix length)이며, 이 경우 출력 길이(output length)가 32k로 설정되어 있습니다.  STD 모델과 SIGMA 모델의 성능 차이를 보여주는 그래프입니다. SIGMA 모델은 접두사 길이가 길어짐에 따라 표준 모델보다 효율성이 훨씬 더 높아짐을 보여줍니다. 이는 SIGMA 모델의 효율성 향상을 시각적으로 보여주는 중요한 결과입니다.
> <details>
> <summary>read the caption</summary>
> (e) Output Length =32⁢kabsent32𝑘=32k= 32 italic_k.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/augq_cost_delta.png)

> 🔼 그림 (f)는 출력 길이가 64k 토큰일 때의 결과를 보여줍니다. 이는 긴 문맥(long-context) 상황에서 SIGMA 모델의 효율성을 평가하기 위한 실험 결과로,  x축은 prefix 길이, y축은 CEET(Cuda Event Elapsed Time)를 나타냅니다.  다양한 prefix 길이에 따른 SIGMA와 기준 모델(STD)의 총 실행 시간을 비교하여 SIGMA의 성능 향상을 보여줍니다. 특히, 긴 prefix 길이에서 SIGMA의 성능 향상이 더욱 두드러짐을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (f) Output Length =64⁢kabsent64𝑘=64k= 64 italic_k.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/augq_cost_redelta.png)

> 🔼 그림 (g)는 표준 모델(STD)과 비교하여 SIGMA 모델의 CEET(CUDA 이벤트 경과 시간) 개선의 절대적인 크기를 보여줍니다. 이는 다양한 프리픽스 길이와 출력 길이에 따른 SIGMA의 성능 향상 정도를 시각적으로 나타냅니다. 그림은 SIGMA가 특히 긴 컨텍스트에서 표준 모델보다 훨씬 더 효율적임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (g) Sigma’s absolute CEET improvment vs Std.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/kvcache_cost_2k.png)

> 🔼 그림 (h)는 표준 모델(STD)을 기준으로 SIGMA의 상대적 CEET 개선율을 보여줍니다.  CEET(CUDA 이벤트 경과 시간)는 특정 연산의 총 실행 시간을 측정하는 지표이며, 이 그림에서는 SIGMA 모델이 STD 모델보다 얼마나 효율적으로 연산을 수행하는지 상대적인 비율로 나타냅니다.  그래프는 다양한 prefix 길이와 output 길이에 따른 SIGMA의 성능 개선 정도를 보여주는 상대적 비율(%)을 나타냅니다.  높은 값은 SIGMA가 STD보다 더 큰 성능 향상을 보였다는 것을 의미합니다.
> <details>
> <summary>read the caption</summary>
> (h) Sigma’s relative CEET improvment vs Std.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/kvcache_cost_4k.png)

> 🔼 그림 3은 표준 모델(Std)과 Sigma 모델 간의 증강 Q(Augmented Q)에 대한 CEET(CUDA 이벤트 경과 시간) 비교를 보여줍니다. (a)부터 (f)까지 출력 길이가 2k 토큰에서 64k 토큰으로 점진적으로 증가합니다. 이 그림은 서로 다른 출력 길이에 대해 증강 Q 모듈의 성능을 비교 분석하여,  모델의 효율성 개선에 미치는 영향을 보여줍니다.  특히, 출력 길이가 증가함에 따라 증강 Q 모듈의 효과가 더욱 두드러지게 나타나는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: CEET comparison of augmented Q between Standard model(Std) and Sigma. From (a) to (f), the output length increases progressively from 2k to 64k tokens.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/kvcache_cost_8k.png)

> 🔼 그림은 3.3절 실험 설정에서 설명하는 Cuda 이벤트 경과 시간 측정 방법을 사용하여 얻은 결과를 보여줍니다.  (a)는 출력 길이가 2k 토큰일 때의 결과입니다.  이 그림은 다양한 prefix 길이에 따른 모델의 계산 시간을 보여주어, prefix 길이와 계산 시간 간의 상관관계를 분석하는 데 도움이 됩니다. 이러한 분석은 모델의 효율성을 평가하고, 성능을 최적화하기 위한 전략을 수립하는 데 중요한 정보를 제공합니다.  각 prefix 길이에 따른 SIGMA와 STD 모델의 성능 차이를 비교함으로써,  SIGMA 모델의 효율성 향상을 정량적으로 보여줍니다. 
> <details>
> <summary>read the caption</summary>
> (a) Output Length =2⁢kabsent2𝑘=2k= 2 italic_k.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/kvcache_cost_16k.png)

> 🔼 그림 2는 표준 모델(STD)과 SIGMA 간의 FlexHeadFA에 대한 KET 비교를 보여줍니다. (b)는 출력 길이가 4k 토큰일 때의 결과를 보여줍니다.  이는 쿼리, 키, 값 행렬들을 작은 청크들로 나누고 곱셈을 수행한 후 다시 결합하는 과정을 측정하는 스플릿 커널과 결합 커널의 수행 시간을 보여줍니다.  이 그림은 입력 시퀀스 길이가 증가함에 따라 두 모델 간의 성능 차이가 어떻게 달라지는지를 보여주는 시각적 도구 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> (b) Output Length =4⁢kabsent4𝑘=4k= 4 italic_k.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/kvcache_cost_32k.png)

> 🔼 그림은 논문의 3.3절 실험 설정 부분에 속하며,  다양한 출력 길이에 따른 성능 비교 결과를 보여줍니다. 특히, (c)는 출력 길이가 8k 토큰일 때의 결과를 보여주는 것으로,  FlexHeadFA(유연한 헤드 어텐션)의 split kernel과 combine kernel의 실행 시간을 표시합니다.  이를 통해 SIGMA 모델이 기존의 표준 모델(STD)에 비해 효율성이 얼마나 향상되었는지, 특히 긴 문맥 길이에서 어떤 성능 개선을 보이는지 확인할 수 있습니다.  x축은 접두사 길이, y축은 실행 시간(ns)을 나타냅니다.  두 모델의 split kernel과 combine kernel의 실행 시간을 비교함으로써,  SIGMA 모델의 성능 개선 효과를 정량적으로 제시합니다.
> <details>
> <summary>read the caption</summary>
> (c) Output Length =8⁢kabsent8𝑘=8k= 8 italic_k.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/kvcache_cost_64k.png)

> 🔼 그림 (d)는 16k 토큰 길이의 출력 시퀀스를 생성하는 동안, 입력 시퀀스 길이(prefix length)가 변화함에 따라 SIGMA와 STD 모델의 Cuda Event Elapsed Time(CEET)을 비교한 그래프입니다.  이 그래프는 서로 다른 입력 길이에 대한 SIGMA와 STD 모델의 효율성 차이를 보여줍니다.  prefix length가 증가함에 따라 SIGMA의 효율성이 높아지는 경향을 보여주는 것을 확인할 수 있습니다.  특히, 긴 입력 시퀀스에 대한 효율성 향상을 강조합니다.
> <details>
> <summary>read the caption</summary>
> (d) Output Length =16⁢kabsent16𝑘=16k= 16 italic_k.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/kvcache_cost_delta.png)

> 🔼 그림은 논문의 3.3.2절 실험 결과에서 나온 것으로, 다양한 prefix 길이에 따른, 출력 길이가 32k일 때의 Cuda Event Elapsed Time (CEET)을 나타냅니다.  x축은 prefix 길이를 나타내고, y축은 CEET를 나타냅니다. SIGMA와 STD 두 모델의 결과가 비교되어 표시됩니다. 이를 통해 prefix 길이에 따른 두 모델의 효율성 차이를 비교 분석하고자 합니다.  특히, 긴 prefix 길이에서 SIGMA가 STD에 비해 훨씬 효율적임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (e) Output Length =32⁢kabsent32𝑘=32k= 32 italic_k.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/kvcache_cost_redelta.png)

> 🔼 그림 (f)는 출력 길이가 64k 토큰일 때의 결과를 보여줍니다. 이는 매우 긴 컨텍스트를 처리하는 경우 SIGMA 모델의 효율성을 평가하기 위한 것입니다. 이 그림에서는 표준 모델(STD)과 SIGMA 모델의 총 계산 시간(CEET)을 비교하여 SIGMA 모델의 성능 향상을 보여줍니다. 그림에서 확인할 수 있듯이, 출력 길이가 길어질수록 SIGMA 모델의 효율성이 더욱 두드러집니다. 특히, 64k 토큰의 출력 길이에서는 SIGMA 모델이 STD 모델보다 상당히 빠른 속도로 추론을 수행함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (f) Output Length =64⁢kabsent64𝑘=64k= 64 italic_k.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/attn_cost_2k.png)

> 🔼 그림 (g)는 표준 모델(STD) 대비 SIGMA 모델의 절대 CEET 개선(절대 시간 차이)을 보여줍니다.  x축은 prefix 길이, y축은 CEET(밀리초)를 나타냅니다. 여러 개의 선이 있는데, 각 선은 다른 출력 길이(output length)에 해당합니다.  각 선은 prefix 길이가 증가함에 따라 CEET가 어떻게 변하는지, 그리고 SIGMA가 STD보다 얼마나 더 빠른지 보여줍니다.  이 그림은 SIGMA 모델의 효율성 향상을 정량적으로 보여주는 주요 결과 중 하나입니다.
> <details>
> <summary>read the caption</summary>
> (g) Sigma’s absolute CEET improvment vs Std.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/attn_cost_4k.png)

> 🔼 그림 (h)는 표준 모델(STD)과 비교하여 SIGMA 모델의 CEET(CUDA 이벤트 경과 시간) 개선율을 보여줍니다.  이 그래프는 다양한 시퀀스 길이(prefix length와 output length)에 따른 성능 향상을 보여주는 열 지도 형태로,  각 셀의 색상은 상대적 성능 향상(백분율)을 나타냅니다.  즉, 더 진한 파란색은 더 큰 성능 향상을 나타내고, 더 진한 빨간색은 성능 저하를 나타냅니다. 이는 SIGMA 모델의 효율성이 시퀀스 길이에 따라 어떻게 달라지는지 보여주는 시각적 자료입니다. 특히 긴 시퀀스에서 상당한 성능 향상을 보이는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (h) Sigma’s relative CEET improvment vs Std.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/attn_cost_8k.png)

> 🔼 그림 4는 표준 모델(Std)과 Sigma 모델의 KV 캐시에 대한 CEET(CUDA 이벤트 경과 시간) 비교 결과를 보여줍니다.  (a)부터 (f)까지는 출력 길이가 2,000 토큰에서 64,000 토큰으로 점진적으로 증가하는 것을 나타냅니다.  각 그래프는 특정 출력 길이에 대한 KV 캐시 처리 시간을 보여주며, Std 모델과 Sigma 모델 간의 성능 차이를 시각적으로 비교하여 Sigma 모델의 효율성 향상을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: CEET comparison of KV cache between Standard model(Std) and Sigma. From (a) to (f), the output length increases progressively from 2k to 64k tokens.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/attn_cost_16k.png)

> 🔼 이 그림은 논문의 3.3.2절 실험 결과에서 2k 토큰 길이의 출력을 생성하는 동안, 접두사(prefix) 길이 변화에 따른 각기 다른 세 가지 측정 지표(split 커널의 KET, combine 커널의 KET, 총 KET)를 표현한 그래프 세 개를 보여줍니다. 각 그래프는 표준 모델(STD)과 SIGMA 모델의 성능을 비교하여 SIGMA의 효율성 향상을 시각적으로 보여줍니다.  x축은 접두사 길이이고 y축은 각 측정 지표의 값(ns)입니다.
> <details>
> <summary>read the caption</summary>
> (a) Output Length =2⁢kabsent2𝑘=2k= 2 italic_k.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/attn_cost_32k.png)

> 🔼 그림 (b)는 출력 길이가 4k 토큰일 때, 표준 모델(STD)과 SIGMA 모델의 성능을 비교한 결과를 보여줍니다. 4k는 prefix length를 의미하며,  x축은 prefix length, y축은 실행 시간(ns)을 나타냅니다. STD와 SIGMA모델 모두 split kernel과 combine kernel의 실행 시간을 측정하여 비교합니다. 이를 통해 SIGMA 모델의 효율성 향상을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) Output Length =4⁢kabsent4𝑘=4k= 4 italic_k.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/attn_cost_64k.png)

> 🔼 그림은 논문의 3.3절 실험 설정 부분에 속하며, 다양한 출력 길이(output length)에 따른 모델의 효율성을 비교 분석한 결과를 보여줍니다. 특히 (c) Output Length = 8k 부분은 입력 시퀀스 길이(prefix length)가 변화함에 따라 8k 길이의 출력 시퀀스를 생성하는 데 걸리는 시간을 측정한 결과입니다. 이를 통해 모델의 처리 속도와 효율성을 평가하고, 다른 조건들과의 비교 분석을 통해 최적의 모델 구성을 찾고자 하는 연구 목표를 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (c) Output Length =8⁢kabsent8𝑘=8k= 8 italic_k.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/attn_cost_delta.png)

> 🔼 그림 (d)는 긴 문맥(long-context) 상황에서의 추론 효율성을 분석한 결과를 보여줍니다.  특히, 출력 토큰의 길이가 16,000개일 때,  다양한 길이의 접두사(prefix) 토큰에 따른  SIGMA 모델과 기준 모델(STD)의  추론 시간을 비교 분석합니다. 이를 통해 SIGMA 모델의 DiffQKV 어텐션 메커니즘이 긴 문맥 상황에서 얼마나 효율적인지 보여줍니다.  세로축은 시간(ms)을, 가로축은 접두사 토큰의 길이를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> (d) Output Length =16⁢kabsent16𝑘=16k= 16 italic_k.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/attn_cost_redelta.png)

> 🔼 이 그림은 논문의 3.3.2절 실험 결과에서 Cuda Event Elapsed Time (CEET) 테스트 결과 중 출력 길이가 32k 토큰일 때의 결과를 보여줍니다.  그림은 접두사 길이(prefix length)가 변화함에 따라 SIGMA 모델과 표준 모델(STD)의 CEET 값을 비교하여, SIGMA 모델의 효율성 향상을 시각적으로 보여줍니다.  각 접두사 길이에 따른 CEET 값의 차이를 통해, SIGMA 모델이 특히 긴 문맥(long-context) 상황에서 얼마나 효율적인지 보여주는 것이 주요 내용입니다.  x축은 접두사 길이를, y축은 CEET 값(밀리초)을 나타냅니다.  두 모델의 CEET 값을 비교 분석하여 SIGMA의 효율성 향상 정도를 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (e) Output Length =32⁢kabsent32𝑘=32k= 32 italic_k.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/total_cost_2k.png)

> 🔼 그림 (f)는 출력 토큰의 길이가 64k일 때의 결과를 보여줍니다. 이는 긴 문맥(long-context) 시나리오에서 SIGMA 모델의 효율성을 평가하기 위한 실험 결과의 일부입니다.  x축은 입력 토큰(prefix)의 길이를 나타내고, y축은 특정 연산(예: KV 캐시 로딩, 어텐션 계산)에 소요된 시간을 측정한 CEET(Cuda Event Elapsed Time) 값을 나타냅니다. 이 그래프는 입력 길이가 증가함에 따라 SIGMA 모델의 성능이 어떻게 변화하는지 보여주는 다양한 실험 결과 중 하나입니다. 다른 그래프 (a)부터 (e)까지는 출력 토큰의 길이가 2k, 4k, 8k, 16k, 32k일 때의 결과를 각각 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (f) Output Length =64⁢kabsent64𝑘=64k= 64 italic_k.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/total_cost_4k.png)

> 🔼 그림 (g)는 표준 모델(STD)에 비해 SIGMA 모델의 절대적인 CEET(CUDA 이벤트 경과 시간) 개선 사항을 보여줍니다. 이 그림은 다양한 접두사 길이와 출력 길이에 따른 SIGMA의 성능 향상 정도를 보여주는 그래프를 포함하고 있습니다. 그림을 통해 SIGMA 모델이 표준 모델보다 얼마나 효율적으로 연산을 수행하는지 정량적으로 확인할 수 있습니다. 특히 긴 문맥을 처리하는 경우 SIGMA의 성능 향상이 더욱 두드러지게 나타납니다.
> <details>
> <summary>read the caption</summary>
> (g) Sigma’s absolute CEET improvment vs Std.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/total_cost_8k.png)

> 🔼 그림은 SIGMA 모델과 표준 모델(STD) 간의 상대적 CEET(CUDA 이벤트 경과 시간) 개선을 보여줍니다.  즉, SIGMA 모델이 STD 모델보다 얼마나 효율적인지, 특히 다양한 프리픽스 길이와 출력 길이에 따른 상대적 성능 향상 정도를 나타냅니다.  세로축은 상대적 성능 향상률을 백분율로 나타내고, 가로축은 프리픽스 길이를 나타냅니다. 여러 그래프가 출력 길이에 따라 나뉘어져 있을 것이며, 각 그래프는 특정 출력 길이에 대한 SIGMA 모델의 상대적 효율성 변화를 프리픽스 길이에 따라 보여줍니다. 이를 통해 특정 길이의 프리픽스와 출력에 대해 SIGMA 모델의 성능 향상 정도를 정량적으로 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (h) Sigma’s relative CEET improvment vs Std.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/total_cost_16k.png)

> 🔼 그림 5는 표준 모델(Std)과 시그마 모델 간의 어텐션 연산에 대한 CEET(CUDA 이벤트 경과 시간) 비교를 보여줍니다. (a)부터 (f)까지 출력 길이가 2k 토큰에서 64k 토큰으로 점진적으로 증가함에 따라, 시그마 모델의 어텐션 연산 속도가 표준 모델보다 훨씬 빠르다는 것을 보여줍니다. 이는 시그마 모델의 효율적인 설계와 최적화 기법을 반영한 결과입니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: CEET comparison of attention computation between Standard model(Std) and Sigma. From (a) to (f), the output length increases progressively from 2k to 64k tokens.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/total_cost_32k.png)

> 🔼 그림 3은 표준 모델(STD)과 SIGMA 간의 증강 Q의 CEET(CUDA 이벤트 경과 시간) 비교를 보여줍니다. (a)에서 (f)까지 출력 길이가 2k 토큰에서 64k 토큰으로 점진적으로 증가합니다.  각 그래프는 특정 출력 길이에 대한 접두사 길이와 CEET 간의 관계를 보여줍니다. 이 그림은 접두사 길이가 증가함에 따라 SIGMA의 CEET가 STD보다 훨씬 낮아짐을 보여줍니다.  이는 SIGMA의 설계 및 최적화 기법의 효율성을 입증합니다.  특히 긴 컨텍스트에서 SIGMA의 효율성 향상이 더 두드러집니다. 그림 (g)와 (h)는 STD에 대한 SIGMA의 CEET 절대 및 상대적 개선을 보여주는 열지도를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (a) Output Length =2⁢kabsent2𝑘=2k= 2 italic_k.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/total_cost_64k.png)

> 🔼 이 그림은 논문의 3.3.2절 실험 결과에서 FlexHeadFA의 두 가지 주요 GPU 커널 연산(split kernel과 combine kernel)의 수행 시간을 비교한 것입니다. 그래프는 접두사 길이(prefix length)가 2k, 4k, 16k, 32k로 증가함에 따라 각 커널의 실행 시간(KET, Kernel Execution Time)을 표시합니다.  SIGMA 1.5B 모델과 표준 모델(STD)의 성능을 비교하여 SIGMA 모델이  접두사 길이가 길어질수록 표준 모델보다 효율성이 더욱 향상됨을 보여줍니다. 특히, combine kernel의 경우 접두사 길이에 따른 시간 변화가 split kernel보다 훨씬 완만하여, SIGMA 모델의 효율성 향상에 기여하는 부분이 제한적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (b) Output Length =4⁢kabsent4𝑘=4k= 4 italic_k.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/total_cost_delta.png)

> 🔼 그림은 논문의 3.3.2절 실험 결과에서 나온 것으로, FlexHeadFA의 성능을 표준 모델(STD)과 SIGMA 모델 간에 비교 분석한 결과를 보여줍니다.  세부적으로는 prefix 길이가 2k, 4k, 16k, 32k일 때 split kernel과 combine kernel 각각에 대한 Kernel Execution Time (KET)을 측정하여 비교합니다.  출력 길이는 8k로 고정되어 있습니다.  결과적으로, SIGMA 모델이 prefix 길이가 길어질수록 STD 모델보다 훨씬 빠른 속도를 보임을 시각적으로 보여주는 그림입니다.
> <details>
> <summary>read the caption</summary>
> (c) Output Length =8⁢kabsent8𝑘=8k= 8 italic_k.
> </details>



![](https://arxiv.org/html/2501.13629/extracted/6151052/Figures/total_cost_redelta.png)

> 🔼 그림 (d)는 출력 길이가 16k 토큰일 때의 결과를 보여줍니다.  이 그림은 다양한 prefix 길이에 따른 SIGMA와 STD 모델의 Kernel Execution Time (KET)을 비교하여 SIGMA 모델의 효율성을 보여줍니다.  prefix 길이가 증가함에 따라, SIGMA 모델은 STD 모델보다 훨씬 빠른 속도를 보여주는 것을 알 수 있습니다. 이는 SIGMA 모델의 DiffQKV 어텐션 메커니즘이 장문맥 상황에서 효율성을 크게 향상시키는 것을 시각적으로 보여줍니다.  세부적으로는 split kernel 과 combine kernel 각각의 수행시간과 전체 수행시간을 비교 분석하여, SIGMA 모델이 어텐션 연산의 효율성을 개선하는 것을 보여줍니다. 
> <details>
> <summary>read the caption</summary>
> (d) Output Length =16⁢kabsent16𝑘=16k= 16 italic_k.
> </details>



![](https://arxiv.org/html/2501.13629/x2.png)

> 🔼 그림은 3.3절 실험 설정에서 설명하는 CUDA 이벤트 경과 시간(CEET) 테스트 결과를 보여줍니다.  이 테스트는 KV 캐시 로딩 및 저장, 어텐션 연산, 증강 Q의 세 가지 모듈의 비용을 측정합니다. 그래프는 출력 길이가 32k 토큰일 때 접두사 길이에 따른 각 모듈의 CEET를 보여줍니다.  접두사 길이가 증가함에 따라 모든 모듈의 CEET가 증가하지만, SIGMA 모델이 STD 모델보다 효율성이 더 높음을 보여줍니다. 이는 SIGMA 모델의 설계로 인해 KV 캐시 및 어텐션 연산에 대한 비용이 감소되었기 때문입니다.
> <details>
> <summary>read the caption</summary>
> (e) Output Length =32⁢kabsent32𝑘=32k= 32 italic_k.
> </details>



![](https://arxiv.org/html/2501.13629/x3.png)

> 🔼 그림 (f)는 출력 길이가 64k 토큰일 때, 표준 모델(STD)과 SIGMA 모델의 누적 CEET(Cuda Event Elapsed Time) 비용을 비교한 그래프입니다. 이 그래프는 서로 다른 prefix 길이에 따른 각 모델의 누적 CEET 비용을 보여줍니다. prefix 길이가 증가함에 따라 두 모델의 누적 CEET 비용이 모두 증가하지만, SIGMA 모델의 누적 CEET 비용이 STD 모델에 비해 상대적으로 낮은 것을 확인할 수 있습니다. 특히 prefix 길이가 길어질수록 SIGMA 모델의 성능 향상이 더욱 두드러집니다.
> <details>
> <summary>read the caption</summary>
> (f) Output Length =64⁢kabsent64𝑘=64k= 64 italic_k.
> </details>



![](https://arxiv.org/html/2501.13629/x4.png)

> 🔼 그림 (g)는 표준 모델(STD)에 비해 SIGMA 모델의 CEET(CUDA 이벤트 경과 시간) 개선의 절대적인 크기를 보여줍니다. 즉, 각 작업에 대해 SIGMA가 STD보다 얼마나 더 빠르게 실행되는지를 절대적인 시간(밀리초)으로 나타낸 것입니다.  x축은 접두사 길이(Prefix Length)를 나타내고, y축은 SIGMA와 STD의 CEET 차이를 나타냅니다.  그래프를 통해 접두사 길이가 길어짐에 따라 SIGMA의 성능 향상이 어떻게 변하는지 확인할 수 있습니다.  양수 값은 SIGMA가 STD보다 빠르다는 것을, 음수 값은 STD가 SIGMA보다 빠르다는 것을 의미합니다.
> <details>
> <summary>read the caption</summary>
> (g) Sigma’s absolute CEET improvment vs Std.
> </details>



![](https://arxiv.org/html/2501.13629/x5.png)

> 🔼 그림 (h)는 표준 모델(STD) 대비 SIGMA 모델의 상대적 CEET 개선율을 보여줍니다. 이 그림은 다양한 접두사 길이와 출력 길이에 따른 SIGMA의 효율성 향상 정도를 시각적으로 보여주는 여러 개의 하위 그림들로 구성되어 있습니다. 각 하위 그림은 특정 출력 길이에 대해, 접두사 길이가 증가함에 따라 SIGMA가 STD보다 얼마나 더 빠르게 연산을 수행하는지 보여줍니다. 이를 통해 SIGMA 모델의 효율성 개선이 접두사 길이에 따라 어떻게 변하는지, 그리고 전반적으로 얼마나 큰 효율성 향상을 가져오는지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (h) Sigma’s relative CEET improvment vs Std.
> </details>



![](https://arxiv.org/html/2501.13629/x6.png)

> 🔼 그림 6은 표준 모델(Std)과 Sigma 모델의 총 CEET(CUDA 이벤트 경과 시간) 비용을 비교한 그래프입니다. (a)부터 (f)까지 출력 길이가 2k에서 64k 토큰으로 점진적으로 증가합니다. 회색 점선은 두 모델의 추론 비용이 같은 지점을 나타냅니다. 출력 길이가 증가함에 따라 이 교차점은 점점 더 앞당겨집니다. 64k 토큰을 생성할 때, Sigma는 Std에 비해 최대 33%의 추론 비용 감소를 달성합니다. 이 그림은 입력 길이에 따른 두 모델의 성능 차이를 보여주며, 특히 긴 입력에 대해 Sigma 모델이 훨씬 효율적임을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Comparison of total CEET cost between Standard model(Std) and Sigma. From (a) to (f), the output length increases progressively from 2k to 64k tokens. The gray dashed line indicates where the inference costs of both models are equal. As the output length increases, this intersection point moves progressively earlier. When generating 64k tokens, Sigma achieves up to a 33% reduction in inference cost compared to Std.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | Overall | Hella. | ObQA | Wino. | ARC. | PIQA | SciQ | Bool. | Logi. | LAMB. |
|---|---|---|---|---|---|---|---|---|---|---|
| **MHA** (<span class="ltx_text ltx_font_bold">n<sub>k</sub><sup>h</sup></span>=<span class="ltx_text ltx_font_bold">n<sub>v</sub><sup>h</sup></span>=32) | **52.40** | 55.6 | 37.6 | 57.6 | 36.0 | 73.9 | 85.5 | 59.6 | 28.9 | 36.8 |
| _w/_ Half K Dim. | **52.56** (<span class="ltx_text ltx_font_medium">↑0.16</span>) | 55.2 | 39.4 | 56.9 | 36.9 | 72.7 | 84.1 | 63.3 | 27.8 | 36.8 |
| **GQA** (<span class="ltx_text ltx_font_bold">n<sub>k</sub><sup>h</sup></span>=<span class="ltx_text ltx_font_bold">n<sub>v</sub><sup>h</sup></span>=16) | **52.14** | 55.1 | 39.6 | 56.3 | 35.4 | 71.9 | 85.0 | 61.4 | 27.8 | 36.8 |
| _w/_ Half K Dim. | **52.06** (<span class="ltx_text ltx_font_medium">↓0.08</span>) | 54.3 | 39.8 | 56.9 | 36.7 | 72.0 | 83.9 | 59.5 | 29.2 | 36.2 |
| **GQA** (<span class="ltx_text ltx_font_bold">n<sub>k</sub><sup>h</sup></span>=<span class="ltx_text ltx_font_bold">n<sub>v</sub><sup>h</sup></span>=4) | **51.66** | 54.0 | 38.0 | 56.0 | 37.5 | 72.3 | 82.0 | 61.3 | 28.6 | 35.4 |
| _w/_ Half K Dim. | **51.92** (<span class="ltx_text ltx_font_medium">↑0.26</span>) | 53.4 | 39.2 | 56.6 | 35.6 | 72.5 | 84.0 | 62.3 | 28.9 | 34.8 |{{< /table-caption >}}
> 🔼 표 2는 K 헤드의 차원을 절반으로 줄였을 때의 실험 결과를 보여줍니다.  결과는 KV 캐시 크기를 줄임으로써 추론 효율성을 크게 향상시키는 동시에 성능 저하를 크게 유발하지 않음을 보여줍니다. 모든 모델에서 Q 헤드의 수는 32개로 동일하게 유지되었습니다(nqh=32). 이 표는 DiffQKV 어텐션 메커니즘에서 K 헤드 차원의 감소가 모델 성능에 미치는 영향을 분석한 것입니다. K 헤드의 차원을 줄이면 메모리 사용량이 줄어들어 추론 속도가 빨라질 수 있지만, 동시에 모델의 표현 능력이 감소하여 성능이 저하될 수 있습니다. 이 표는 그러한 절충점을 분석하고 최적의 K 헤드 차원을 찾는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 2: The ablation studies of halving the K head dimension. The results indicate that this adjustment, while largely improving the inference efficiency by reducing the size of KV cache, does not significantly compromise performance. The number of Q heads is 32 for all models (nqh=32superscriptsubscript𝑛𝑞ℎ32n_{q}^{h}=32italic_n start_POSTSUBSCRIPT italic_q end_POSTSUBSCRIPT start_POSTSUPERSCRIPT italic_h end_POSTSUPERSCRIPT = 32).
> </details>

{{< table-caption >}}
| Model | Overall | Hella. | ObQA | Wino. | ARC. | PIQA | SciQ | Bool. | Logi. | LAMB. |
|---|---|---|---|---|---|---|---|---|---|---|
| **MHA**  (n<sub>k</sub><sup>h</sup>=n<sub>v</sub><sup>h</sup>=32) | **52.40** | 55.6 | 37.6 | 57.6 | 36.0 | 73.9 | 85.5 | 59.6 | 28.9 | 36.8 |
| + Sel.V-top100 | **52.10** (↓0.30) | 55.6 | 37.6 | 57.6 | 36.0 | 74.0 | 84.8 | 59.3 | 27.0 | 36.9 |
| **GQA** (n<sub>k</sub><sup>h</sup>=n<sub>v</sub><sup>h</sup>=16) | **52.14** | 55.1 | 39.6 | 56.3 | 35.4 | 71.9 | 85.0 | 61.4 | 27.8 | 36.8 |
| + Sel.V-top100 | **52.08** (↓0.06) | 55.2 | 39.6 | 56.3 | 35.4 | 71.8 | 84.4 | 61.6 | 27.8 | 36.7 |
| **GQA** (n<sub>k</sub><sup>h</sup>=n<sub>v</sub><sup>h</sup>=4) | **51.66** | 54.0 | 38.0 | 56.0 | 37.5 | 72.3 | 82.0 | 61.3 | 28.6 | 35.4 |
| + Sel.V-top100 | **51.67** (↑0.01) | 54.0 | 38.2 | 55.9 | 37.5 | 72.2 | 82.0 | 61.2 | 28.6 | 35.4 |{{< /table-caption >}}
> 🔼 표 3은 어텐션 점수가 가장 높은 V 벡터만 선택적으로 로드하여 근사 계산을 수행했을 때 모델 성능에 대한 추가 분석 결과를 보여줍니다. 이 방법은 메모리 사용량을 줄여 추론 효율성을 크게 높입니다. 표에 있는 모든 모델의 Q 헤드 수는 32개입니다(nqh=32). 이 표는 선택적 V 벡터 로딩이 모델 성능에 미치는 영향을 정량적으로 분석하고, 메모리 효율과 성능 간의 균형을 찾는 데 도움이 되는 다양한 설정을 비교 분석합니다.  구체적으로는, V 벡터의 일부만 선택적으로 로드하여 추론 속도를 개선하는 전략을 제시하고, 실험을 통해 이 전략의 유효성을 검증합니다. 다양한 모델의 성능을 비교 분석하여 최적의 설정을 제시하고, SIGMA 모델의 효율성을 뒷받침하는 중요한 근거를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: The ablation studies of the model performance when only selectively loading the V vectors corresponding to the highest attention scores for approximate calculation. This operation significantly enhances inference efficiency by reducing memory usage. The number of Q heads is 32 for all models in the table (nqh=32superscriptsubscript𝑛𝑞ℎ32n_{q}^{h}=32italic_n start_POSTSUBSCRIPT italic_q end_POSTSUBSCRIPT start_POSTSUPERSCRIPT italic_h end_POSTSUPERSCRIPT = 32).
> </details>

{{< table-caption >}}
| Model | Overall | Hella. | ObQA | Wino. | ARC. | PIQA | SciQ | Bool. | Logi. | LAMB. |
|---|---|---|---|---|---|---|---|---|---|---|
| **MHA** | **52.40** | 55.6 | 37.6 | 57.6 | 36.0 | 73.9 | 85.5 | 59.6 | 28.9 | 36.8 |
| + AugQ ($d_{q}^{h}$=5632) | **53.03**<sup>**↑0.63**</sup> | 57.4 | 38.0 | 57.9 | 39.4 | 72.9 | 85.9 | 60.1 | 27.3 | 38.3 |
| **GQA** ($n_{k}^{h}$=$n_{v}^{h}$=16) | **52.14** | 55.1 | 39.6 | 56.3 | 35.4 | 71.9 | 85.0 | 61.4 | 27.8 | 36.8 |
| + AugQ ($d_{q}^{h}$=3072) | **53.38**<sup>**↑1.24**</sup> | 56.6 | 40.2 | 56.1 | 40.0 | 73.2 | 87.3 | 61.0 | 28.3 | 37.7 |
| + AugQ ($d_{q}^{h}$=4096) | **52.93**<sup>**↑0.79**</sup> | 56.7 | 40.8 | 56.9 | 37.1 | 73.6 | 83.5 | 61.7 | 28.0 | 38.1 |
| + AugQ ($d_{q}^{h}$=5632) | **53.07**<sup>**↑0.93**</sup> | 57.3 | 39.8 | 57.3 | 36.4 | 74.2 | 83.6 | 61.4 | 28.7 | 39.0 |
| **GQA** ($n_{k}^{h}$=$n_{v}^{h}$=4) | **51.66** | 54.0 | 38.0 | 56.0 | 37.5 | 72.3 | 82.0 | 61.3 | 28.6 | 35.4 |
| + AugQ ($d_{q}^{h}$=5632) | **53.13**<sup>**↑1.47**</sup> | 56.5 | 40.8 | 58.2 | 37.6 | 73.6 | 84.7 | 61.2 | 27.5 | 37.9 |{{< /table-caption >}}
> 🔼 표 4는 기본 모델 아키텍처와 증강된 Q를 통합한 아키텍처 간의 성능 비교를 보여줍니다.  dqh(d_{q}^{h})는 중간 Q 헤드 차원을 나타내며, 표의 모든 모델에서 Q 헤드의 수는 32(n_{q}^{h}=32)로 일정합니다. AugQ가 없는 기본 모델의 경우, Q 헤드의 중간 차원은 dqh=2048입니다. 이 표는 Q 헤드의 차원을 증가시키는 것이 모델 성능에 미치는 영향을 분석하기 위한 것입니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Comparisons between the baseline model architectures and those incorporating augmented Q. dqhsuperscriptsubscript𝑑𝑞ℎd_{q}^{h}italic_d start_POSTSUBSCRIPT italic_q end_POSTSUBSCRIPT start_POSTSUPERSCRIPT italic_h end_POSTSUPERSCRIPT refers to the intermediate Q head dimension. The number of Q heads is 32 for all models in the table (nqh=32superscriptsubscript𝑛𝑞ℎ32n_{q}^{h}=32italic_n start_POSTSUBSCRIPT italic_q end_POSTSUBSCRIPT start_POSTSUPERSCRIPT italic_h end_POSTSUPERSCRIPT = 32). For the baseline without AugQ, the intermediate dimension of Q head is dqh=2048superscriptsubscript𝑑𝑞ℎ2048d_{q}^{h}=2048italic_d start_POSTSUBSCRIPT italic_q end_POSTSUBSCRIPT start_POSTSUPERSCRIPT italic_h end_POSTSUPERSCRIPT = 2048.
> </details>

{{< table-caption >}}
Model|Overall|Hella.|ObQA|Wino.|ARC.|PIQA|SciQ|Bool.|Logi.|LAMB.|LM
---|---|---|---|---|---|---|---|---|---|---
**GQA**|**52.14**|55.1|39.6|56.3|35.4|71.9|85.0|61.4|27.8|36.8
+ AugF (ΔdF=δ)|**53.26 (↑1.12)**|57.6|39.6|57.3|38.5|73.2|87.3|59.0|27.6|39.2
+ AugQ (dqh=δ)|**53.38 (↑1.24)**|56.6|40.2|56.1|40.0|73.2|87.3|61.0|28.3|37.7
+ AugF (ΔdF=2δ)|**53.16 (↑1.02)**|59.3|40.0|57.0|38.3|73.9|85.2|59.8|24.9|40.1
+ AugF (ΔdF=δ) & AugQ (dqh=δ)|**54.55 (↑2.41)**|58.8|41.8|57.5|39.7|74.4|86.9|62.4|28.1|41.5
+ AugF (ΔdF=3δ)|**54.50 (↑2.36)**|60.5|42.4|59.8|39.8|74.7|87.3|59.9|27.0|39.2
+ AugF (ΔdF=2δ) & AugQ (dqh=δ)|**54.67 (↑2.53)**|60.5|41.6|57.4|39.9|74.7|87.3|59.6|27.3|43.8
+ AugF (ΔdF=5δ)|**55.08 (↑2.94)**|62.4|41.4|57.3|41.3|75.3|88.3|60.6|26.6|42.5
+ AugF (ΔdF=3δ) & AugQ (dqh=δ)|**55.09 (↑2.95)**|61.6|39.8|61.0|40.5|75.1|88.7|59.6|28.3|41.2{{< /table-caption >}}
> 🔼 표 5는 증강된 Q 구성 요소(AugQ)를 다양한 크기로 통합하고 FFN 모듈(AugF)을 확장할 때 모델 성능을 비교한 것입니다. 기준 방법은 FFN 차원이 5632이고 nk=nv=16인 GQA입니다. ΔdF는 FFN 모듈의 확장된 차원을 나타내고, dq는 중간 Q 헤드 차원(δ=3072)을 나타냅니다. 이 표는 AugQ와 AugF의 크기를 달리하여 모델 성능에 미치는 영향을 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Comparisons of the model performance when incorporating the augmented Q component (AugQ) with different sizes and enlarging the FFN module (AugF). The baseline method is GQA, with the FFN dimension being 5632 and nkhsuperscriptsubscript𝑛𝑘ℎn_{k}^{h}italic_n start_POSTSUBSCRIPT italic_k end_POSTSUBSCRIPT start_POSTSUPERSCRIPT italic_h end_POSTSUPERSCRIPT=nvhsuperscriptsubscript𝑛𝑣ℎn_{v}^{h}italic_n start_POSTSUBSCRIPT italic_v end_POSTSUBSCRIPT start_POSTSUPERSCRIPT italic_h end_POSTSUPERSCRIPT=16. Δ⁢dFΔsubscript𝑑𝐹\Delta d_{F}roman_Δ italic_d start_POSTSUBSCRIPT italic_F end_POSTSUBSCRIPT denotes the enlarged dimension for the FFN module, while dqhsuperscriptsubscript𝑑𝑞ℎd_{q}^{h}italic_d start_POSTSUBSCRIPT italic_q end_POSTSUBSCRIPT start_POSTSUPERSCRIPT italic_h end_POSTSUPERSCRIPT represents the intermediate Q head dimension (δ𝛿\deltaitalic_δ=3072307230723072).
> </details>

{{< table-caption >}}
| Model Config ($n_k^h = n_v^h = 16$) | Overall | Commonsense & Comprehension | Continued | LM |
|---|---|---|---|---|
| **AugQ** | **Overall** | **Commonsense & Comprehension** | **Continued** | **LM** |
| -75% K Heads | Hella. | ObQA | Wino. | ARC. | PIQA | SciQ | Bool. | Logi. | LAMB. |
| Half K Dim |  |  |  |  |  |  |  |  |  |
| ($d_q^h = 3072$) | 52.14 | 55.1 | 39.6 | 56.3 | 35.4 | 71.9 | 85.0 | 61.4 | 27.8 | 36.8 |
| ($n_k^h = 4$) | **52.97** | 56.0 | 38.4 | 57.7 | 37.0 | 72.5 | 83.8 | 62.5 | 30.1 | 38.8 |
| ($d_k^h = d_v^h/2$) | **52.72** | 55.9 | 39.4 | 59.1 | 37.5 | 73.1 | 84.3 | 60.6 | 27.0 | 37.4 |
|  | **51.74** | 54.3 | 37.4 | 57.5 | 36.3 | 72.9 | 85.5 | 60.5 | 26.3 | 35.1 |
|  | **52.61** | 55.8 | 40.2 | 54.9 | 38.5 | 74.0 | 84.6 | 61.1 | 26.9 | 37.6 |{{< /table-caption >}}
> 🔼 표 6은 자기 주의 네트워크 구조를 최적화하기 위한 세 가지 전략(증강된 Q, K 헤드 수 압축, K 헤드 차원 압축)의 조합을 보여줍니다. ✓와 ✗는 각 전략이 사용되었는지 여부를 나타냅니다. 전략이 사용되지 않은 경우 표준 모델 설정(즉,  𝑛𝑘ℎ=𝑛𝑣ℎ=16이고 Q는 증강되지 않음)이 적용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Combinations of three strategies for optimizing the self-attention architecture: augmented Q, compressing the number of K heads, and compressing K head dimension. ✓ and ✗ represent whether the corresponding strategy is used or not respectively. If the strategy is not used, the standard model setting is adopted (i.e. nkhsuperscriptsubscript𝑛𝑘ℎn_{k}^{h}italic_n start_POSTSUBSCRIPT italic_k end_POSTSUBSCRIPT start_POSTSUPERSCRIPT italic_h end_POSTSUPERSCRIPT=nvhsuperscriptsubscript𝑛𝑣ℎn_{v}^{h}italic_n start_POSTSUBSCRIPT italic_v end_POSTSUBSCRIPT start_POSTSUPERSCRIPT italic_h end_POSTSUPERSCRIPT=16, and Q is not augmented).
> </details>

{{< table-caption >}}
| Parameter \\ Scale | 1.5B | 10B |
|---|---|---|
| Layers | 26 | 32 |
| Hidden Dimension | 2,048 | 4,096 |
| FFN Dimension | 6,144 | 14,336 |
| Aug Q Dimension | 3,072 | 6,144 |
| Attention Heads | 32 | 32 |
| Key Heads | 4 | 4 |
| Value Heads | 16 | 16 |
| Peak Learning Rate | 4.0e-4 | 1.5e-4 |
| Activation Function | SwiGLU | SwiGLU |
| Vocabulary Size | 128,256 | 128,256 |
| Positional Embeddings | ROPE (θ=50,000) | ROPE (θ=500,000) |{{< /table-caption >}}
> 🔼 표 7은 논문에서 제시된 SIGMA 모델의 두 가지 크기, 즉 15억 개와 100억 개의 파라미터를 가진 SIGMA-1.5B와 SIGMA-10B에 대한 주요 구성 및 하이퍼파라미터를 보여줍니다.  레이어 수, 은닉 차원, FFN 차원, 증강된 Q 차원, 어텐션 헤드 수, 키 헤드 수, 밸류 헤드 수, 최고 학습률, 활성화 함수, 어휘 크기, 위치 임베딩과 같은 세부 정보를 포함합니다. 이 표는 SIGMA 모델의 아키텍처와 성능에 대한 이해를 돕기 위해 자세한 설정 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Key configurations and hyperparameters of Sigma 1.5B and 10B.
> </details>

{{< table-caption >}}
| Prefix | Std Split | Std Combine | Std Total Cost | Sigma 1.5B Split | Sigma 1.5B Combine | Sigma 1.5B Total Cost | Relative Improvement Split | Relative Improvement Combine | Relative Improvement Total Cost |
|---|---|---|---|---|---|---|---|---|---| 
| **Length** |  |  |  |  |  |  |  |  |  |
| **2k** | 2.53E+6 | 1.88E+6 | 4.41E+6 | 2.50E+6 | 1.85E+6 | 4.34E+6 | 1.17% | 1.68% | 1.39% |
| **4k** | 4.68E+6 | 1.91E+6 | 6.59E+6 | 3.49E+6 | 1.91E+6 | 5.40E+6 | 25.33% | 0.08% | 18.02% |
| **16k** | 1.52E+7 | 1.94E+6 | 1.72E+7 | 1.12E+7 | 1.94E+6 | 1.31E+7 | 26.30% | 0.25% | 23.35% |
| **32k** | 2.75E+7 | 1.99E+6 | 2.95E+7 | 2.00E+7 | 2.01E+6 | 2.21E+7 | 27.21% | -0.93% | 25.31% |{{< /table-caption >}}
> 🔼 표 8은 접두사 길이가 2k에서 32k로 증가함에 따라 분할 커널과 결합 커널의 실행 시간(ns)을 보여줍니다. 출력 길이는 10으로 고정되어 있습니다. 'Split'은 분할 커널을 나타내고, 'Combine'은 결합 커널을 나타냅니다. 이 표는 SIGMA 모델의 효율성을 평가하기 위한 실험 결과를 보여주는 표이며, 접두사 길이 변화에 따른 각 커널의 실행 시간을 측정하여 SIGMA 모델의 성능을 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 8: KET Results (ns) with the prefix length increase from 2k to 32k, keeping the output length as 10. Split represents the split kernel and Combine represents the combine kernel.
> </details>

{{< table-caption >}}
| Data Type | Sources | Size | # Tokens |
|---|---|---|---| 
| **General System** | CCF Ranking list | 14.0 G | 3.3 B |
|  | arXiv | 33.0 G | 5.4 B |
| **Design Capability** | Technical blogs & Developer forums | 14.5 G | 3.2 B |
| **Debug Capability** | Stack Overflow | 38.9 G | 7.6 B |{{< /table-caption >}}
> 🔼 표 9는 SIGMA 사전 훈련을 위해 사용된 시스템 도메인 데이터의 구성을 보여줍니다.  일반적인 시스템 데이터, 설계 능력 관련 데이터, 디버깅 능력 관련 데이터 등 데이터 유형별로 데이터 소스, 크기, 토큰 수를 자세히 제시하여 SIGMA 모델 훈련에 사용된 시스템 도메인 데이터의 규모와 다양성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Composition of the system domain pre-training data for Sigma.
> </details>

{{< table-caption >}}
| Model | CMD Score | Output Score | Calibration Score | Exact Match | Success Ratio | Accuracy |
|---|---|---|---|---|---|---|
| **GPT-3.5** | 70.0 | 36.0 | 21.0 | 6.0 | 11.0 | 13.0 |
| **GPT-4** | 84.0 | 61.0 | 62.0 | 13.0 | 21.0 | 25.0 |
| **Mistral-7B-S** | 80.6 | 58.7 | 62.0 | 24.9 | 19.0 | 30.7 |
| **Mistral-7B-P-S** | 83.4 | 65.3 | 66.3 | 23.9 | 21.5 | 32.2 |
| **Llama3-8B-S** | 86.4 | 69.1 | 64.4 | 42.0 | 32.7 | 50.7 |
| **Llama3-8B-P-S** | 87.5 | 72.2 | 69.3 | 46.3 | 37.1 | 57.1 |
| **Codegemma-7B-P-S** | 84.2 | 61.8 | 65.9 | 23.9 | 21.0 | 32.7 |
| **Starcoder2-7B-P-S** | 86.5 | 66.5 | 64.9 | 31.2 | 23.4 | 38.1 |
| **DeepSeekCoder1.5-7B-P-S** | 86.3 | 68.4 | 63.9 | 41.0 | 30.7 | 49.3 |
| **Gemma2-9B-P-S** | 90.3 | 72.2 | 78.1 | 34.2 | 26.8 | 43.9 |
| Sigma-System-10B | 87.5 | 80.9 | 78.0 | 57.0 | 74.0 | 74.5 |{{< /table-caption >}}
> 🔼 표 10은 논문에서 제시된 AIMICIUS 벤치마크의 CMDGen NVIDIA 하위 작업에 대한 다양한 언어 모델의 성능을 보여줍니다.  '-S' 접미사는 해당 모델이 연구팀의 SFT(Supervised Fine-Tuning) 데이터셋의 초기 버전을 사용하여 SFT(Supervised Fine-Tuning) 학습되었음을 나타내고, '-P' 접미사는 시스템 도메인 사전 학습 데이터셋으로 사전 학습되었음을 의미합니다.  표에는 각 모델의 CMD 점수, 출력 점수, 보정 점수, 정확히 일치하는 비율, 성공 비율, 정확도 등 다양한 지표가 포함되어 모델의 성능을 다각적으로 평가합니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Performance of different models on CMDGen NVIDIA subtask in AIMicius. The postfix of “-S” indicates that the model has been SFTed using a preliminary version of our SFT dataset, while “-P” denotes that the model has been pre-trained on our system-domain pre-training dataset.
> </details>

{{< table-caption >}}
| CMD | Score |
|---|---|{{< /table-caption >}}
> 🔼 표 11은 논문에서 제시된 AIMICIUS 벤치마크에 대한 다양한 언어 모델들의 평가 결과를 보여줍니다.  기준 모델로 GPT-4, Gemma2-9B-Instruct, Deepseek-Coder-7b-Instruct-v1.5, Qwen2.5-Coder-7B-Instruct, Llama3-8B-Instruct를 사용했으며, 모든 지표는 0에서 100까지 정규화되어 있습니다. 높은 값일수록 성능이 더 좋음을 의미합니다. 각 과제에서 가장 중요한 평가 기준은 굵게 표시되어 있습니다.  Sigma-System 10B 모델은 연구팀이 독자적으로 만든 데이터셋을 사용하여 미세 조정(Fine-tuned, SFT)되었습니다.
> <details>
> <summary>read the caption</summary>
> Table 11: Evaluation results on the AIMicius benchmark. The baselines include GPT-4, Gemma2-9B-Instruct, Deepseek-Coder-7b-Instruct-v1.5, Qwen2.5-Coder-7B-Instruct, and Llama3-8B-Instruct. All metrics are normalized to a scale of 0 to 100, with higher values indicating better performance. Bolded metrics represent the most critical evaluation criteria for each task. Sigma-System 10B is fine-tuned (SFT) using our proprietary dataset.
> </details>

{{< table-caption >}}
| Output | Score |
|---|---|{{< /table-caption >}}
> 🔼 표 12는 commonsense 추론 및 text 이해 작업에 대한 기준 모델과 SIGMA 모델의 성능 비교 결과를 보여줍니다.  각 모델의 성능은 HellaSwag, OpenBookQA, WinoGrande, ARC Challenge, PIQA, SciQ, BoolQ, LogiQA 와 같은 다양한 벤치마크 데이터셋을 사용하여 평가되었습니다. 표에는 각 모델의 매개변수 수, 평균 점수, 그리고 각 벤치마크 데이터셋에 대한 세부 점수가 포함되어 있습니다.  표의 결과는 공정한 비교를 위해 저자들이 통일된 방식으로 재평가한 결과임을 주목해야 합니다. 원 논문에서 보고된 결과와의 차이점은 재평가 과정에서 발생한 것으로, 모델 자체의 성능 차이가 아닙니다.
> <details>
> <summary>read the caption</summary>
> Table 12: Comparisons with baseline models on commonsense reasoning and text understanding tasks. Differences with original reports in the baseline models are due to our unified re-evaluations for fair comparisons.
> </details>

{{< table-caption >}}
| Calibration | Score |
|---|---|{{< /table-caption >}}
> 🔼 표 13은 다양한 기준 모델들과 SIGMA 모델의 성능을 일반적인 문제 해결, 코딩, 수학 문제 해결 작업에 대해 비교한 표입니다.  기존 연구에서 보고된 기준 모델들의 성능과 차이가 있는데, 이는 공정한 비교를 위해 본 논문에서 통일된 재평가를 수행했기 때문입니다.  표에는 각 모델의 매개변수 수와 다양한 작업(MMLU, MMLU-Pro, BBH, HumanEval, MBPP, MATH, GSM8K)에서의 평균 성능 점수가 포함되어 있습니다. 각 작업의 성능 점수는 해당 작업의 특성에 따라 다를 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 13: Comparisons with baseline models on general, coding, and math problem-solving tasks. Differences with original reports in the baseline models are due to our unified re-evaluations for fair comparisons.
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