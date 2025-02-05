---
title: "Scaling Embedding Layers in Language Models"
summary: "SCONE은 언어 모델의 입력 임베딩 계층을 확장하여 계층 크기가 커져도 성능을 유지하는 방법입니다.  기존 방식과 달리,  빈도수가 높은 n-gram의 임베딩을 추가하여 기존 어휘는 유지하면서 문맥 정보를 풍부하게 합니다.  추론 속도 저하 없이 성능을 향상시켜 대규모 언어 모델의 효율성을 높였습니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Google Research",]
showSummary: true
date: 2025-02-03
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.01637 {{< /keyword >}}
{{< keyword icon="writer" >}} Da Yu et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-04 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.01637" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.01637" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델에서 **임베딩 계층의 크기 확장**은 성능 향상에 중요하지만, **추론 비용 증가**라는 문제점이 있습니다. 기존 방식은 어휘 크기를 늘리는 방식이라, 훈련 데이터 부족으로 인해 성능이 저하되고, 메모리 사용량이 급증하는 문제가 있습니다. 

본 논문에서는 이러한 문제를 해결하기 위해 **SCONE**이라는 새로운 방법을 제시합니다. SCONE은 빈번하게 등장하는 n-gram에 대한 임베딩을 추가하여 문맥 정보를 풍부하게 하고, 이 임베딩들은 추론 단계에서 미리 계산되어 저장되므로 **추론 속도 저하 없이 성능 향상**을 가져옵니다. 실험 결과, SCONE은 기존 모델보다 성능이 뛰어나고, 추론 시간 FLOPS를 절반으로 줄였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} SCONE은 추론 속도 저하 없이 언어 모델의 임베딩 계층을 확장하는 새로운 방법입니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} SCONE은 빈도수가 높은 n-gram 임베딩을 추가하여 문맥 정보를 풍부하게 하면서 기존 어휘는 유지합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} SCONE은 대규모 언어 모델의 성능을 향상시키고, 추론 시간 FLOPS를 절반으로 줄입니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **언어 모델의 임베딩 계층을 확장하는 새로운 방법**을 제시하여 추론 속도 저하 없이 성능을 향상시키는 데 중요한 의미를 가집니다.  **기존의 어휘 확장 방식의 한계를 극복**하고, **새로운 확장 전략**을 제시함으로써,  향후 언어 모델 연구에 새로운 방향을 제시하고, 다양한 분야의 연구자들에게 널리 활용될 수 있습니다.  특히 **대규모 언어 모델의 효율적인 학습 및 배포**에 직접적인 영향을 미칠 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.01637/x1.png)

> 🔼 그림 1은 SCONE 모델의 성능을 보여주는 두 개의 그래프로 구성됩니다. 위쪽 그래프는 OLMo 평가 혼합 데이터셋에서 네 가지 크기(0.7B, 1B, 1.3B, 1.9B)의 모델에 대한 perplexity를 보여줍니다.  SCONE을 사용하면 10M개의 f-gram을 사용하는 1.3B 모델이 1.9B 기준 모델과 동일한 성능을 달성하고, 1B개의 f-gram을 사용하는 1B 모델은 기준 모델을 능가하는 것을 알 수 있습니다. 아래쪽 그래프는 단일 A100에서 vLLM을 사용하여 종단 간 토큰 생성 속도를 보여줍니다. f-gram 임베딩을 메인 메모리에 저장하면 지연 시간이 거의 발생하지 않지만, NVMe 저장소를 사용하면 생성 속도가 약간 느려지지만 병목 현상은 발생하지 않습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: (Top) Perplexity (lower is better) on the OLMo (Groeneveld et al., 2024) evaluation mixture. Inference-time FLOPS refer to the forward pass computation cost for four model sizes (0.7B, 1B, 1.3B, and 1.9B). With 10M f-grams, the 1.3B model matches the 1.9B baseline, while with 1B f-grams, the 1B model surpasses it. (Bottom) End-to-end token generation speed on a single A100 using vLLM (Kwon et al., 2023). Storing f-gram embeddings in main memory introduces negligible latency, while NVMe storage slows generation slightly but does not create a bottleneck.
> </details>





{{< table-caption >}}
| # of n-grams | System memory | Solid-state drive |
|---|---|---|
| 10<sup>7</sup> | 41.4 GB | 77.3 GB |
| 10<sup>8</sup> | 413.6 GB | 766.8 GB |
| 10<sup>9</sup> | (does not fit) | 7665.4 GB |
| Price (per GB) | ∼ 2 USD | ∼ 0.1 USD |{{< /table-caption >}}

> 🔼 표 1은 f-gram 임베딩 레이어 (ℱ)의 공간 사용량과 메모리 및 NVMe 솔리드 스테이트 드라이브 비용을 보여줍니다.  다양한 크기의 f-gram(10⁷, 10⁸, 10⁹)에 대한 시스템 메모리와 SSD 저장 용량을 보여주며, 각 저장 매체에 대한 GB당 가격도 함께 제시합니다. 이는 모델의 크기 변화에 따른 저장 공간 및 비용 효율성을 비교 분석하는 데 유용합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Space usage of the f-gram embedding layer ℱℱ\mathcal{F}caligraphic_F, along with cost for memory and NVMe solid-state drives (McCallum, 2024).
> </details>





### In-depth insights


#### SCONE's Novel Design
SCONE은 기존의 단순한 어휘 확장 방식에서 벗어나 **빈번하게 등장하는 n-gram 단위의 문맥 정보를 활용**하여 입력 임베딩 계층을 확장하는 혁신적인 디자인을 제시합니다. 이를 통해 기존의 어휘 크기 증가로 인한 성능 저하 및 연산 비용 증가 문제를 해결하고자 합니다.  **기존 어휘를 유지하면서 빈번한 n-gram에 대한 임베딩을 추가**함으로써, 모델의 표현력을 향상시키는 동시에 추론 속도 저하를 최소화하는 전략을 채택합니다.  **추론 과정에서 n-gram 임베딩은 가속기 메모리가 아닌 외부 메모리에 저장**되어, 추론 시간에 대한 오버헤드를 최소화합니다.  또한, **n-gram 임베딩 학습을 위한 별도의 모델을 도입**함으로써, 희귀 토큰의 임베딩 학습 문제를 완화하고, 모델 성능을 더욱 향상시킵니다.  이러한 SCONE의 설계는 **두 가지 확장 전략(n-gram 임베딩 수 증가 및 학습 모델 크기 조정)**을 가능하게 하여, 고정된 추론 시간 연산량 내에서 모델 성능을 향상시키는 데 기여합니다.

#### Scaling Strategies
본 논문에서 제시된 "확장 전략"은 언어 모델의 임베딩 계층을 확장하는 두 가지 주요 방법에 초점을 맞춥니다. 첫째, **자주 사용되는 n-gram 임베딩의 수를 늘리는 것**입니다. 이는 기존 어휘에 n-gram의 문맥 정보를 추가하여 모델의 표현력을 향상시키는 전략입니다. 둘째, **n-gram 임베딩을 학습하는 데 사용되는 모델의 크기를 키우는 것**입니다. 이를 통해 더욱 정교하고 풍부한 문맥 정보를 담은 임베딩을 얻을 수 있습니다. 두 전략 모두 추론 속도에 영향을 미치지 않으면서 모델 성능을 향상시키는 데 중점을 둡니다.  **추론 시간 FLOPS를 일정하게 유지하면서**  두 가지 전략을 동시에 적용하여 기존 모델보다 우수한 성능을 달성했다는 점에서 **효율적인 확장 방식**이라는 것을 알 수 있습니다. 이러한 전략은 단순히 어휘 크기를 늘리는 기존 방식의 한계를 극복하고, 제한된 자원 내에서 모델 성능 향상을 꾀하는 효과적인 접근 방식입니다. 

#### Empirical Findings
본 논문의 실험 결과는 **SCONE이 다양한 말뭉치에서 기준 모델을 능가한다는 것을 보여줍니다.** 특히, **추론 시간 FLOPS를 유지하면서 f-gram 임베딩의 수와 f-gram 모델의 크기를 조정함으로써 성능 향상을 이끌어냈습니다.**  **단어 임베딩 확장의 기존 문제점인 어휘 크기 증가에 따른 계산 비용 증가와 희귀 단어의 부족한 학습을 SCONE이 효과적으로 해결**했음을 실증적으로 확인했습니다.  **추론 속도 저하 없이 메모리 또는 보조 저장장치에 f-gram 임베딩을 저장**하여 효율성을 높였습니다.  **다양한 크기의 모델과 말뭉치에 대해 일관되게 성능 향상**을 보였으며, 이는 SCONE의 확장성과 일반화 능력을 시사합니다.  **SCONE은 향후 대규모 언어 모델의 효율적인 확장을 위한 유망한 방법**으로 평가될 수 있습니다.  그러나, **Af-gram 모델의 크기가 어느 정도 이상 커지면 성능 향상이 감소**하는 경향도 확인되었으므로, 향후 연구에서는 Af-gram 모델의 최적 크기를 결정하는 추가적인 연구가 필요할 것으로 보입니다.

#### Space and Latency
본 논문의 "Space and Latency" 부분은 **메모리 및 저장 공간 사용량과 쿼리 지연 시간**에 대한 실험 결과를 제시합니다.  **주요 목표는 제안된 방법의 효율성을 검증**하는 것입니다.  인메모리와 NVMe 드라이브 두 가지 저장 방식에 대한 비교 분석을 통해 **메모리 사용량이 선형적으로 증가**함을 보여주고, NVMe 사용 시에도 **지연 시간이 짧아 실시간 응답에 부족함이 없음**을 강조합니다.  특히, 배치 크기 증가에 따른 지연 시간 감소 효과가 언급되어 실제 시스템 구현에서의 성능 최적화 가능성을 시사합니다.  **결론적으로, 본 논문의 공간 및 지연 시간 분석은 제안된 모델의 실용성 및 확장성을 입증**하는 중요한 근거를 제공합니다.

#### Future Directions
본 논문에서 제시된 SCONE 기법은 언어 모델의 임베딩 계층을 확장하는 효과적인 방법을 제시하지만, **추가적인 연구 방향**이 존재합니다.  먼저, **다양한 크기의 언어 모델과 코퍼스**에 대한 SCONE의 일반화 성능을 더욱 심도 있게 평가해야 합니다.  다양한 모델 아키텍처와 데이터셋에 대한 실험을 통해 SCONE의 범용성을 확인하는 것이 중요합니다.  둘째, **f-gram 임베딩 학습에 사용되는 f-gram 모델의 최적 크기 및 아키텍처**를 탐색해야 합니다. 현재 연구에서는 여러 크기의 f-gram 모델을 실험하였으나,  더욱 체계적인 연구를 통해 최적의 모델을 찾을 필요가 있습니다.  셋째, **추론 속도와 메모리 사용량 간의 균형**을 더욱 효율적으로 조절하는 방법을 연구할 수 있습니다.  본 논문에서는 추론 속도를 유지하면서 메모리 사용량을 줄이는 데 초점을 맞추었지만,  추론 속도를 더욱 향상시키는 동시에 메모리 사용량을 효율적으로 관리하는 방안에 대한 연구가 필요합니다.  마지막으로, **SCONE 기법을 다른 자연어 처리 작업**에 적용하고 그 성능을 평가하는 연구가 필요합니다. 본 연구에서는 주로 언어 모델 사전 학습에 집중하였지만,  텍스트 분류, 기계 번역 등 다른 작업에도 적용 가능한지 추가적인 실험을 통해 확인해야 합니다. 이러한 후속 연구를 통해 SCONE의 실용성과 범용성을 더욱 높일 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.01637/x2.png)

> 🔼 그림 2는 제안된 SCONE 방법의 개념을 보여줍니다. 최대 3-gram 길이를 사용하는 예시가 나와 있으며, 자주 등장하는 n-gram(f-gram)들을 사용하여 입력 토큰 임베딩을 확장하는 방법을 보여줍니다. 입력 텍스트는 토큰화되고, f-gram 모델은 자주 등장하는 n-gram에 대한 문맥화된 임베딩을 생성합니다. 이 임베딩은 추론 중에 오프-액셀러레이터 메모리에 저장되므로 추론 속도에 영향을 미치지 않습니다.  SCONE은 기존의 단어 임베딩과 f-gram 임베딩을 결합하여 입력 토큰의 풍부한 표현을 제공합니다. 이 그림은 SCONE의 주요 구성 요소와 데이터 흐름을 시각적으로 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Illustration of Scone (with a maximum n𝑛nitalic_n-gram length of 3333). The term f-grams refers to the set of frequent n𝑛nitalic_n-grams (Section 3).
> </details>



![](https://arxiv.org/html/2502.01637/x3.png)

> 🔼 이 그림은 OLMo 토큰화된 훈련 말뭉치(Soldaini et al., 2024)에서 시퀀스를 균일하게 샘플링하여 말뭉치 크기를 다양하게 변경하면서 최소 5회 이상 나타나는 고유한 2-그램에서 6-그램의 수를 보여줍니다.  x축은 훈련 토큰 수(수십억 단위)를 나타내고, y축은 고유한 n-그램 수(백만 단위)를 나타냅니다. 각 선은 2-그램, 3-그램, 4-그램, 5-그램, 6-그램에 해당합니다. 이 그림은 훈련 데이터 크기가 증가함에 따라 다양한 길이의 n-그램의 수가 어떻게 증가하는지 보여주는 시각적 표현을 제공합니다.  이는  SCONE 모델에서 자주 나타나는 n-그램(f-gram)을 선택하는 과정을 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Number of unique 2222- to 6666-grams that appear at least five times. We vary the size of the corpus by uniformly sampling sequences from the OLMo tokenized training corpus (Soldaini et al., 2024).
> </details>



![](https://arxiv.org/html/2502.01637/x4.png)

> 🔼 그림 4는 10만 개의 배치에 대해 평균화된 토큰당 쿼리 지연 시간(밀리초)을 보여줍니다. 시스템 메모리에서 읽을 때 배치 크기가 1에서 2로 증가하면 지연 시간이 급증하는데, 이는 배치 연산 오버헤드 때문입니다. 반면, SSD를 사용하면 이러한 현상이 덜 두드러집니다. 이는 시스템 메모리에 비해 SSD의 더 빠른 데이터 접근 속도 때문입니다. 그림은 메모리와 SSD의 두 가지 저장 방법에 대한 토큰당 지연 시간을 배치 크기에 따라 비교 분석하고 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Amortized per-token query latency (ms), averaged over 100,000 batches. The latency spike from batch size 1 to 2 when reading from system memory is due to batch operator overhead, which is less pronounced for solid-state drives.
> </details>



![](https://arxiv.org/html/2502.01637/x5.png)

> 🔼 그림 5는 SCONE 모델에서 사용되는 최대 f-gram 길이(n)가 모델 성능과 매칭된 f-gram의 평균 길이에 미치는 영향을 보여줍니다. 왼쪽 y축은 세 번의 시드에 대한 평균 perplexity를 나타내며, 가장 왼쪽 별표는 기준 성능을 나타냅니다. 오른쪽 y축은 매칭된 f-gram의 평균 길이를 나타냅니다. 최대 길이가 2에서 4로 증가함에 따라 perplexity는 감소하지만, 그 이후에는 약간의 변동을 보이며 안정화됩니다. 마찬가지로, 매칭된 f-gram의 평균 길이도 처음에는 증가하지만, 크기가 4가 된 후에는 안정화됩니다. 이는 더 긴 f-gram이 덜 자주 나타나고, 훈련 데이터에서 더 긴 f-gram이 평가 데이터와 일치할 가능성이 적기 때문일 것입니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Effect of the maximum f-gram length n𝑛nitalic_n in Vf⁢-⁢gramsubscript𝑉f-gramV_{\mathrm{f\text{-}gram}}italic_V start_POSTSUBSCRIPT roman_f - roman_gram end_POSTSUBSCRIPT, on perplexity and matched length. The left y𝑦yitalic_y-axis shows perplexity (averaged over three seeds), where the leftmost star indicates baseline performance. The right y𝑦yitalic_y-axis shows the average length of matched f-grams. The perplexity decreases as we increase the maximum length from 2 to 4, but then plateaus with some fluctuation. Similarly, the average matched length initially rises but stabilizes after size 4.
> </details>



![](https://arxiv.org/html/2502.01637/x6.png)

> 🔼 그림 6은 주요 모델 크기(토큰 임베딩 계층 포함)에 대해 |Vf-gram|의 함수로 평가된 perplexity를 보여줍니다. 점선과 맨 왼쪽 별표는 기준 성능을 나타냅니다. |Vf-gram|의 크기가 증가함에 따라 perplexity가 전반적으로 감소합니다. 이 그림은 다양한 크기의 주요 모델에 대해, 자주 발생하는 n-gram의 임베딩 수가 증가함에 따라 언어 모델 성능이 향상되는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Evaluation perplexity as a function of |Vf⁢-⁢gram|subscript𝑉f-gram|V_{\mathrm{f\text{-}gram}}|| italic_V start_POSTSUBSCRIPT roman_f - roman_gram end_POSTSUBSCRIPT |. Model sizes in the legend correspond to the main model sizes, including the token embedding layer. The dashed lines and leftmost stars indicate baseline performance. Perplexity decreases overall with increasing sizes of Vf⁢-⁢gramsubscript𝑉f-gramV_{\mathrm{f\text{-}gram}}italic_V start_POSTSUBSCRIPT roman_f - roman_gram end_POSTSUBSCRIPT.
> </details>



![](https://arxiv.org/html/2502.01637/x7.png)

> 🔼 그림 7은 주요 모델 크기(토큰 임베딩 계층 포함)에 대한 Wikitext-103의 평가 퍼플렉서티를 Af-gram 모델 크기의 함수로 보여줍니다. 왼쪽의 점선과 별표는 기준 성능을 나타냅니다. Af-gram 모델 크기가 커짐에 따라 퍼플렉서티가 개선됩니다. 이 그림은 Af-gram 모델 크기가 증가함에 따라 언어 모델 성능이 향상됨을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Evaluation perplexity on Wikitext-103 as a function of the size of 𝒜f⁢-⁢gramsubscript𝒜f-gram\mathcal{A}_{\mathrm{f\text{-}gram}}caligraphic_A start_POSTSUBSCRIPT roman_f - roman_gram end_POSTSUBSCRIPT. Model sizes in the legend correspond to the main model sizes, including the token embedding layer. Dashed lines and stars on the left represent baseline performance. The perplexity improves as the size of 𝒜f⁢-⁢gramsubscript𝒜f-gram\mathcal{A}_{\mathrm{f\text{-}gram}}caligraphic_A start_POSTSUBSCRIPT roman_f - roman_gram end_POSTSUBSCRIPT grows.
> </details>



![](https://arxiv.org/html/2502.01637/x8.png)

> 🔼  그림 8은 세 가지 크기의 모델에 대한 검증 세트의 BPC(Bits Per Character)를 보여줍니다. BPC는 낮을수록 좋습니다. 세 가지 모델 크기 모두에서 어휘 크기가 증가함에 따라 BPC가 처음에는 향상되지만 결국에는 저하됨을 보여줍니다. 이는 더 큰 어휘 크기가 모델의 성능에 긍정적이지만 어느 정도까지만 그렇다는 것을 시사합니다. 어휘 크기가 너무 커지면 성능이 저하될 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: BPC of three model sizes on the validation set (lower is better). For all three model sizes, BPC initially improves as vocabulary size increases but eventually deteriorates.
> </details>



![](https://arxiv.org/html/2502.01637/x9.png)

> 🔼 이 그림은 1억 개의 토큰에 대한 학습 후에 특정 횟수 이상의 업데이트를 받은 토큰의 비율을 보여줍니다. x축은 업데이트 횟수 임계값이고, y축은 해당 임계값보다 많은 업데이트를 받은 토큰의 비율입니다.  다양한 어휘 크기에 대해 비교 분석하여 어휘 크기가 증가함에 따라 토큰 업데이트가 점점 드물어짐을 보여줍니다.  즉, 큰 어휘를 사용하면 희귀 토큰의 임베딩은 거의 업데이트되지 않아 성능 저하로 이어질 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Percentages of tokens (y-axis) that receive more than a given number of updates (x-axis), measured over 100 million training tokens. As the vocabulary size increases, tokens receive increasingly sparse updates.
> </details>



![](https://arxiv.org/html/2502.01637/x10.png)

> 🔼 그림 10은 어휘 크기가 증가함에 따라 GPU 메모리 사용량과 GPU에 저장된 임베딩 계층 매개변수의 수를 보여줍니다.  GPU 메모리 사용량과 매개변수 수는 어휘 크기에 따라 선형적으로 증가합니다. 이는 큰 어휘를 갖는 언어 모델에서 계산 비용이 어떻게 증가하는지 보여주는 시각적 표현입니다.  임베딩 계층의 크기가 커짐에 따라 모델의 메모리 요구사항이 어떻게 증가하는지, 그리고 그에 따른 성능 저하 가능성을 이해하는데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Number of embedding layer parameters on the GPU and corresponding GPU memory usage. Computational costs increase linearly with vocabulary size.
> </details>



![](https://arxiv.org/html/2502.01637/x11.png)

> 🔼 그림 11은 WebText 검증 분할에 대해 평가된 V<sub>f-gram</sub>에서 최대 f-gram 길이가 미치는 영향을 보여줍니다.  x축은 최대 f-gram 길이(n)이고, y축은 두 가지 지표를 나타냅니다. 왼쪽 y축은 평균 perplexity를, 오른쪽 y축은 일치하는 f-gram의 평균 길이를 나타냅니다. 그래프는 최대 f-gram 길이가 증가함에 따라 perplexity가 감소하다가 어느 정도에서 안정화되는 것을 보여줍니다.  일치하는 f-gram의 평균 길이는 최대 f-gram 길이가 증가함에 따라 증가하다가 마찬가지로 어느 시점에서 안정화됩니다. 이는 짧은 f-gram이 더 빈번하게 나타나고, 더 긴 f-gram은 훈련 데이터에 비해 검증 데이터에서 일치할 가능성이 적기 때문입니다. 이 그림은 최적의 최대 f-gram 길이가 존재하며, 너무 짧거나 너무 길어도 성능 향상에 제한이 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Effect of the maximum f-gram length in Vf⁢-⁢gramsubscript𝑉f-gramV_{\mathrm{f\text{-}gram}}italic_V start_POSTSUBSCRIPT roman_f - roman_gram end_POSTSUBSCRIPT, evaluated on the WebText validation split.
> </details>



![](https://arxiv.org/html/2502.01637/x12.png)

> 🔼 그림 12는 WebText 데이터셋에서 훈련된 주요 모델의 크기에 따른(128M, 419M, 589M, 204M, 759M, 1099M)  f-gram 모델 (𝒜f-gramsubscript𝒜f-gram   mathcal{A}_{   mathrm{f   -   gram}}   )의 크기 변화에 따른 평가 perplexity를 보여줍니다.  f-gram 모델의 크기가 증가함에 따라 perplexity가 감소하는 경향을 보여주는 그래프입니다.  각 모델 크기에 대해 여러 크기의 f-gram 모델을 훈련하여 비교 분석하였습니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Evaluation perplexity on WebText as a function of the size of 𝒜f⁢-⁢gramsubscript𝒜f-gram\mathcal{A}_{\mathrm{f\text{-}gram}}caligraphic_A start_POSTSUBSCRIPT roman_f - roman_gram end_POSTSUBSCRIPT.
> </details>



![](https://arxiv.org/html/2502.01637/x13.png)

> 🔼 그림 13은 OLMo 평가 혼합물에 대한 평균 perplexity를 훈련 전체에 걸쳐 보여줍니다. SCONE을 사용하여 훈련된 모델은 더 나은 perplexity에 도달할 뿐만 아니라, 수렴에 더 많은 훈련 토큰을 필요로 합니다. 이는 SCONE이 모델의 용량을 증가시켜 더 나은 성능을 달성한다는 것을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: Average perplexity on the OLMo evaluation mixture throughout training. Models with Scone enabled converge later, indicating stronger capacity, and achieve better perplexity.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
Model size|c4-en|books|common-crawl|pes2o|reddit|stack|wiki|ice|m2de-s2orc|pile|wikitext-103|Average
---|---|---|---|---|---|---|---|---|---|---|---|---
1B baseline|16.813|21.570|16.752|11.682|22.612|3.360|14.453|15.281|27.900|10.429|16.053|16.082
+10M V<sub>f-gram</sub> (0.6B 𝒜<sub>f-gram</sub>)|16.087|20.963|16.039|11.270|21.797|3.274|13.777|14.979|26.361|10.128|15.371|15.459
+10M V<sub>f-gram</sub> (1.8B 𝒜<sub>f-gram</sub>)|15.727|20.429|15.473|11.124|21.388|3.231|13.454|14.709|25.785|9.956|15.104|15.125
+1B V<sub>f-gram</sub> (0.6B 𝒜<sub>f-gram</sub>)|15.846|20.593|15.684|11.071|21.411|3.213|13.543|14.702|26.026|9.889|15.077|15.187
+1B V<sub>f-gram</sub> (1.8B 𝒜<sub>f-gram</sub>)|15.158|19.680|14.857|10.761|20.757|3.133|12.964|14.220|24.958|9.553|14.354|14.581
1.3B baseline|15.994|20.157|15.921|11.148|21.634|3.248|13.721|14.651|26.583|9.927|15.143|15.284
+10M V<sub>f-gram</sub> (0.6B 𝒜<sub>f-gram</sub>)|15.509|19.816|15.407|10.887|21.022|3.192|13.260|14.372|25.450|9.757|14.616|14.844
+10M V<sub>f-gram</sub> (1.8B 𝒜<sub>f-gram</sub>)|15.193|19.587|14.995|10.795|20.735|3.171|13.071|14.272|25.258|9.674|14.438|14.654
+1B V<sub>f-gram</sub> (0.6B 𝒜<sub>f-gram</sub>)|15.270|19.510|15.106|10.707|20.763|3.139|13.073|14.177|25.009|9.546|14.397|14.609
+1B V<sub>f-gram</sub> (1.8B 𝒜<sub>f-gram</sub>)|14.803|18.996|14.541|10.502|20.296|3.085|12.637|13.971|24.533|9.357|13.971|14.245
1.9B baseline|15.270|19.017|15.184|10.719|20.752|3.163|13.119|14.095|25.461|9.570|14.229|14.598{{< /table-caption >}}
> 🔼 표 2는 OLMo 평가 혼합물에 대한 perplexity(낮을수록 좋음)을 보여줍니다. 모든 모델은 200B 토큰으로 학습되었습니다. SCONE은 모든 평가 말뭉치에서 언어 모델링 성능을 일관되게 향상시킵니다. 10M개의 Vf-gram을 사용하면 1.3B 모델이 1.9B 기준 모델의 성능과 일치합니다. 마찬가지로, 1B개의 Vf-gram을 사용하면 1B 모델이 1.9B 기준 모델과 일치합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Perplexity (lower is better) on the OLMo evaluation mixture. All models are trained for 200B tokens. Scone consistently improves language modeling performance across all evaluation corpora. With 10M Vf⁢-⁢gramsubscript𝑉f-gramV_{\mathrm{f\text{-}gram}}italic_V start_POSTSUBSCRIPT roman_f - roman_gram end_POSTSUBSCRIPT, a 1.3B model matches the performance of the 1.9B baseline. Similarly, with 1B Vf⁢-⁢gramsubscript𝑉f-gramV_{\mathrm{f\text{-}gram}}italic_V start_POSTSUBSCRIPT roman_f - roman_gram end_POSTSUBSCRIPT, a 1B model matches the 1.9B baseline.
> </details>

{{< table-caption >}}
| Parameters (million) | d_model | ffw_size | n_layers |
|---|---|---|---|
| 128 | 1024 | 4096 | 6 |
| 204 | 1024 | 4096 | 12 |
| 491 | 1536 | 6144 | 12 |
| 759 | 1536 | 6144 | 24 |
| 589 | 1536 | 6144 | 18 |
| 1099 | 1536 | 6144 | 36 |{{< /table-caption >}}
> 🔼 이 표는 WebText 데이터셋을 사용한 사전 훈련을 위한 기본 모델 구성을 보여줍니다.  f-gram 모델(𝒜f⁢-⁢gramsubscript𝒜f-gram mathcal{A}_{ mathrm{f - gram}} )을 구성하기 위해 128M, 491M, 589M 매개변수를 가진 모델의 레이어 수를 변경하고 토큰 임베딩 레이어를 제외했습니다.  각 모델의 매개변수 수, d_model, ffw_size, 레이어 수를 명시적으로 보여주어 WebText 데이터셋에서의 모델 사전 훈련 구성을 자세히 설명합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Baseline model configurations for pre-training on WebText. For constructing the f-gram model (𝒜f⁢-⁢gramsubscript𝒜f-gram\mathcal{A}_{\mathrm{f\text{-}gram}}caligraphic_A start_POSTSUBSCRIPT roman_f - roman_gram end_POSTSUBSCRIPT), we vary the number of layers in the 128M, 491M, and 589M variants and discard the token embedding layer.
> </details>

{{< table-caption >}}
| Parameters (million) | d_model | ffw_size | n_layers |
|---|---|---|---| 
| 711 | 2048 | 8192 | 12 |
| 1014 | 2048 | 8192 | 18 |
| 1316 | 2048 | 8192 | 24 |
| 1920 | 2048 | 8192 | 36 |{{< /table-caption >}}
> 🔼 표 4는 OLMo 말뭉치 사전 훈련을 위한 기준 모델 구성을 보여줍니다. f-gram 모델 (Af-gram)을 구성하기 위해 711M 및 1920M 구성을 사용하고 토큰 임베딩 계층은 제외합니다.  이 표는 모델의 크기(매개변수 수), 임베딩 차원(d_model), 피드포워드 네트워크 크기(ffw_size), 레이어 수(n_layers) 등의 정보를 담고 있습니다. OLMo 말뭉치를 사용한 사전 훈련에 대한 세부 정보는 본문에서 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Baseline model configurations for pre-training on OLMo corpus. For constructing the f-gram model (𝒜f⁢-⁢gramsubscript𝒜f-gram\mathcal{A}_{\mathrm{f\text{-}gram}}caligraphic_A start_POSTSUBSCRIPT roman_f - roman_gram end_POSTSUBSCRIPT), we use the 711M and 1920M configurations and discard the token embedding layers.
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