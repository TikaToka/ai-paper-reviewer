---
title: "The Curse of Depth in Large Language Models"
summary: "대규모 언어 모델의 깊은 계층들이 예상보다 훨씬 효과적이지 않다는 '깊이에 대한 저주'를 해결하는 LayerNorm Scaling 기법 제시!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Medical Artificial Intelligence Laboratory, Westlake University",]
showSummary: true
date: 2025-02-09
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.05795 {{< /keyword >}}
{{< keyword icon="writer" >}} Wenfang Sun et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-11 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.05795" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.05795" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

최근 대규모 언어 모델(LLM) 연구에서 모델의 깊이가 깊어질수록 일부 계층의 효과가 떨어지는 현상이 관찰되었습니다. 이는 **Pre-Layer Normalization(Pre-LN)**이라는 훈련 안정화 기법의 부작용으로, Pre-LN은 깊은 계층의 출력 분산을 기하급수적으로 증가시켜,  깊은 계층의 기울기가 항등 행렬에 가까워져 학습에 거의 기여하지 못하기 때문입니다. 이러한 문제는 **자원 낭비**로 이어지고 LLM의 성능 향상을 저해합니다.

본 논문에서는 이러한 문제를 해결하기 위해 **LayerNorm Scaling**이라는 새로운 기법을 제안합니다. LayerNorm Scaling은 계층의 깊이에 반비례하여 Layer Normalization의 출력 분산을 조절함으로써 깊은 계층의 기울기가 항등 행렬에 가까워지는 것을 방지합니다. 실험 결과, LayerNorm Scaling은 다양한 크기의 LLM에서 사전 학습 및 미세 조정 성능을 향상시키는 것으로 나타났습니다.  **이는 깊은 계층들이 학습에 효과적으로 기여하도록 함으로써 LLM의 성능과 효율성을 동시에 개선**하는 것을 의미합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 깊은 계층의 비효율성은 Pre-Layer Normalization의 출력 분산이 깊이에 따라 기하급수적으로 증가하기 때문이다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} LayerNorm Scaling은 계층의 깊이에 반비례하여 출력 분산을 조절하여 깊은 계층의 효율성을 높인다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} LayerNorm Scaling은 여러 LLM에서 사전 학습 및 미세 조정 성능을 향상시킨다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
이 논문은 **대규모 언어 모델(LLM)**의 깊이에 대한 저주 현상을 밝히고, 이를 해결하기 위한 효과적인 방법인 LayerNorm Scaling을 제시함으로써, LLM 연구에 중요한 영향을 미칠 수 있습니다. **자원 낭비를 줄이고 성능을 향상**시킬 수 있는 실용적인 방법을 제시한다는 점에서 큰 의의가 있습니다. 또한,  **Pre-LN의 단점**과 이를 극복하는 방안에 대한 심도있는 분석을 제공하여 **LLM의 효율성 및 성능 개선**에 대한 새로운 연구 방향을 제시합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.05795/x1.png)

> 🔼 본 그림은 다양한 설정에서 여러 계층에 걸친 출력 분산을 비교합니다. 설정은 다음과 같습니다. (1) 사전 레이어 정규화(Pre-LN), (2) 사전 레이어 정규화와 크기 조정된 초기화를 결합한 방법, (3) 제안된 레이어 정규화 크기 조정(LayerNorm Scaling). 1억 3천만 매개변수의 LLaMA 모델을 1만 단계 동안 학습시킨 결과를 보여줍니다. 제안된 LayerNorm Scaling은 모든 계층에서 분산을 효과적으로 제어하는 것을 보여줍니다. 즉, Pre-LN에서 나타나는 깊은 레이어의 출력값 분산 폭발 문제를 해결하여 깊은 레이어가 학습에 효과적으로 기여하도록 만들 수 있음을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  Layerwise output variance. This figure compares the output variance across various layers for different setups: (1) Pre-LN; (2) Pre-LN with Scaled Initialization; and (3) LayerNorm Scaling. The experiments are conducted on the LLaM-130M model trained for 10,000 steps. The proposed LayerNorm Scaling effectively controls the variance across layers.
> </details>





{{< table-caption >}}
| Model | LLaMA-130M | LLaMA-250M | LLaMA-350M | LLaMA-1B |
|---|---|---|---|---|
| Training Tokens | 2.2B | 3.9B | 6.0B | 8.9B |
| Post-LN [Ba, 2016] | 26.95 | 1409.79 | 1368.33 | 1390.75 |
| DeepNorm [Wang et al., 2024] | 27.17 | 22.77 | 1362.59 | 1409.08 |
| Mix-LN [Li et al., 2024b] | 26.07 | 21.39 | 1363.21 | 1414.78 |
| Pre-LN [Baevski and Auli, 2019] | 26.73 | 21.92 | 19.58 | 17.02 |
| Pre-LN + LayerNorm Scaling | **25.76** | **20.35** | **18.20** | **15.71** |{{< /table-caption >}}

> 🔼 본 표는 다양한 크기의 LLaMA 모델에서 다양한 Layer Normalization 기법의 성능을 perplexity 지표를 사용하여 비교 분석한 결과를 보여줍니다.  Pre-LN, Post-LN, DeepNorm, Mix-LN과 제안된 LayerNorm Scaling 기법의 perplexity 값을 130M, 250M, 350M, 1B 파라미터 모델에 대해 비교함으로써, 각 기법의 효율성과 안정성을 평가하고 LayerNorm Scaling의 우수성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Perplexity (↓) comparison of various layer normalization methods across various LLaMA sizes.
> </details>





### In-depth insights


#### Depth's Curse in LLMs
본 논문에서 제시된 "Depth's Curse in LLMs" 개념은 **대규모 언어 모델(LLM)의 심층 레이어들이 예상보다 훨씬 효과적이지 못한 현상**을 설명합니다.  이는 **Pre-Layer Normalization(Pre-LN)**의 널리 퍼진 사용으로 인해 발생하며, Pre-LN은 훈련을 안정화시키지만 **심층 레이어의 출력 분산을 기하급수적으로 증가**시켜 심층 트랜스포머 블록의 도함수를 항등 행렬에 가깝게 만듭니다.  결과적으로 심층 레이어들이 훈련에 거의 기여하지 못하게 되는 것입니다.  이 문제를 해결하기 위해 제안된 **LayerNorm Scaling** 기법은 레이어 정규화의 출력을 심도의 제곱근으로 역으로 조정하여 심층 트랜스포머 레이어의 출력 분산 폭발을 완화하고 훈련에의 기여도를 높입니다.  **모델 크기에 상관없이 성능 향상**을 보여주는 실험 결과는 LayerNorm Scaling이 LLM의 사전 훈련 및 지도 학습 미세 조정 성능을 크게 향상시키는 것을 보여줍니다.  이는 **모든 레이어가 효과적으로 훈련에 기여**하도록 함으로써 자원 낭비를 줄이고 LLM의 성능을 개선하는 데 중요한 의미를 지닙니다.

#### Pre-LN's Variance Issue
본 논문에서 다루는 Pre-LN(Pre-Layer Normalization)의 분산 문제는 **깊이가 증가함에 따라 Pre-LN의 출력 분산이 기하급수적으로 증가하는 현상**을 말합니다. 이는 깊은 Transformer 블록의 도함수가 항등 행렬에 가까워져 학습에 거의 기여하지 못하게 되는 결과를 초래합니다. **Pre-LN은 학습을 안정화시키는 데 효과적이지만, 출력 분산의 급격한 증가는 깊은 레이어의 효율성을 저해하는 주요 원인**이 됩니다.  이러한 문제는 모델의 크기가 커질수록 더욱 심화되어, 자원 낭비로 이어집니다.  **LayerNorm Scaling과 같은 기술을 통해 출력 분산을 제어함으로써 이 문제를 해결**할 수 있으며, 이를 통해 깊은 레이어가 학습에 효과적으로 기여하도록 만들 수 있습니다. 따라서, Pre-LN의 분산 문제는 단순한 기술적 문제가 아닌, LLM의 효율적인 설계와 학습에 대한 중요한 고려 사항임을 시사합니다.

#### LayerNorm Scaling
본 논문에서 제안하는 'LayerNorm Scaling'은 **깊이가 깊어짐에 따라 Pre-Layer Normalization(Pre-LN)에서 발생하는 출력 분산의 기하급수적 증가 문제를 해결하기 위한 효과적인 방법**입니다. Pre-LN은 Transformer 기반의 대규모 언어 모델(LLM) 학습을 안정화시키는 데 기여하지만, 깊은 레이어의 경우 출력 분산이 과도하게 증가하여 미분값이 항등 행렬에 가까워져 학습에 거의 기여하지 못하는 문제점이 있습니다. LayerNorm Scaling은 레이어의 깊이에 반비례하는 비율로 Layer Normalization 출력을 조정하여 이러한 문제를 완화합니다. **단순한 수정임에도 불구하고, 깊은 레이어의 효과적인 학습을 가능하게 하여 모델 성능을 향상**시키는 것으로 나타났습니다.  **깊은 레이어의 기여도를 높임으로써 모델의 전체 성능 향상 및 자원 효율성 증대**에 기여할 뿐만 아니라,  다양한 LLM에서 효과적으로 작동하는 일반적인 방법임을 실험적으로 증명했습니다.  이는 **LLM의 압축 및 효율적인 학습을 위한 새로운 패러다임**을 제시하는 중요한 결과입니다.

#### Empirical Evidence
본 논문에서 제시된 '경험적 증거' 부분은 **대규모 언어 모델(LLM)의 심층 레이어 비효율성 현상**에 대한 실증적 분석을 제시합니다. 다양한 LLM 아키텍처와 크기에 걸쳐, 심층 레이어는 예상보다 훨씬 적은 기여를 하고 있으며, 이는 **레이어 제거 실험**을 통해 확인됩니다.  특히 Pre-LN(Pre-Layer Normalization)을 사용하는 모델에서 이러한 현상이 두드러지게 나타나는데, 이는 심층 레이어의 **출력 분산 폭발**과 밀접한 관련이 있습니다.  **Post-LN(Post-Layer Normalization) 모델**과의 비교를 통해 Pre-LN의 문제점이 더욱 명확하게 드러납니다.  **Post-LN 모델**은 심층 레이어의 기여도가 높지만, Pre-LN 모델은 심층 레이어의 영향이 미미하여, **자원 낭비**라는 문제를 제기합니다.  이러한 실험 결과는 깊이가 증가함에 따라 LLM의 효율성이 감소하는 현상, 즉 '깊이의 저주'에 대한 **강력한 실험적 근거**를 제공합니다.

#### Future Work
본 논문은 깊이에 따른 저주 현상을 다루는 심층적인 연구이며, 향후 연구 방향에 대한 몇 가지 중요한 통찰력을 제공합니다. **Pre-LN(Pre-Layer Normalization)의 문제점을 명확히 밝히고, LayerNorm Scaling이라는 효과적인 해결책을 제시한 점은 높이 평가할 만합니다.** 하지만, 이 연구는 아직 초기 단계이며, 향후 연구를 통해 더욱 발전시킬 수 있는 여지가 많습니다. **다양한 LLM 아키텍처 및 모델 크기에서 LayerNorm Scaling의 일반화 가능성을 검증하고, 다른 정규화 기법과의 비교 분석을 통해 LayerNorm Scaling의 우수성을 더욱 강조할 필요가 있습니다.** 또한, LayerNorm Scaling의 메커니즘을 이론적으로 더 깊이 있게 연구하여, 왜 이 기법이 Pre-LN의 문제점을 해결하는지에 대한 명확한 설명을 제공해야 합니다.  **다양한 하류 작업(downstream task)에 대한 LayerNorm Scaling의 성능 평가를 확장하고, 실제 응용 사례를 통해 그 효용성을 검증하는 것도 중요합니다.** 마지막으로, **Post-LN(Post-Layer Normalization)과 LayerNorm Scaling을 결합하여 더욱 효율적이고 강력한 LLM을 개발하는 연구도 필요합니다.** 이러한 후속 연구들을 통해 본 논문에서 제시된 LayerNorm Scaling의 실용성과 효과를 더욱 확대하고, LLM 연구 분야에 중요한 기여를 할 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.05795/x2.png)

> 🔼 그림 2는 다양한 크기의 언어 모델에서 레이어 제거(pruning)에 따른 성능 저하를 보여줍니다. BERT-Large(Post-LN)를 제외하고 Mistral-7B, Qwen-7B, DeepSeek-7B, LLaMA2-7B, LLaMA2-13B는 모두 Pre-LN을 사용하는 모델들입니다. 그림에서 보듯이, Pre-LN 모델은 깊은 레이어일수록 성능 저하가 적은 반면, Post-LN 모델은 깊은 레이어에서도 성능 저하가 상당히 크게 나타납니다. 이는 Pre-LN 모델의 깊은 레이어가 효율적으로 학습되지 않음을 시사하며, Post-LN 모델과는 대조적인 결과입니다.  즉, Pre-LN 기반 모델에서는 깊은 레이어의 효율성이 떨어지고, Post-LN 기반 모델에서는 얕은 레이어의 효율성이 떨어짐을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2:  Performance drop of layer pruning across different LLMs. (a) BERT-Large (Post-LN), (b) Mistral-7B (Pre-LN), (c) Qwen-7B (Pre-LN), (d) DeepSeek-7B (Pre-LN), (e) LLaMA2-7B (Pre-LN), and (f) LLaMA2-13B (Pre-LN). The results show that Pre-LN models exhibit significant inefficiency in deeper layers, while Post-LN models maintain strong deep-layer contributions.
> </details>



![](https://arxiv.org/html/2502.05795/x3.png)

> 🔼 그림 3은 Pre-LN(a)과 LayerNorm Scaling(b)의 비교를 보여줍니다. LayerNorm Scaling은 레이어 인덱스 l의 제곱근에 반비례하는 스케일링 계수를 적용하여 과도한 분산 증가를 방지하고 레이어 간의 안정적인 학습 역학을 유지합니다.  좀 더 자세히 설명하면, Pre-LN(Pre-Layer Normalization)은 레이어의 입력을 정규화한 후에 주요 연산(예: 어텐션, 피드포워드 네트워크)을 수행하는 반면, LayerNorm Scaling은 레이어 정규화의 출력을 레이어 깊이(l)의 제곱근의 역수만큼 스케일링합니다.  이를 통해 깊은 레이어에서 출력 분산이 기하급수적으로 증가하는 것을 억제하여, 모든 레이어가 효과적으로 학습에 기여할 수 있도록 합니다. 이러한 스케일링 기법은 학습 과정에서 그래디언트의 안정성을 유지하고, 전체 모델 성능 향상에 기여합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Comparison between Pre-LN (a) and LayerNorm Scaling (b). LayerNorm Scaling applies a scaling factor inversely proportional to the square root of the layer index l𝑙litalic_l, preventing excessive variance growth and stabilizing training dynamics across layers.
> </details>



![](https://arxiv.org/html/2502.05795/x4.png)

> 🔼 그림 4는 LLaMA-130M 모델에서 레이어 가지치기를 했을 때 성능 저하를 보여줍니다. Pre-LN을 사용한 경우 깊은 레이어를 제거해도 성능 저하가 거의 없었지만, LayerNorm Scaling을 적용한 경우에는 깊은 레이어를 제거했을 때 성능 저하가 상당했습니다. 이는 LayerNorm Scaling이 깊은 레이어가 모델에 의미있는 기여를 하도록 만들었기 때문입니다.  깊은 레이어의 중요성을 강조하며, LayerNorm Scaling의 효과를 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4:  Performance drop of layer pruning on LLaMA-130M. LayerNorm Scaling enables deep layers to make a meaningful contribution to the model.
> </details>



![](https://arxiv.org/html/2502.05795/x5.png)

> 🔼 그림 5는 LLaMA-1B 모델에 대해 Pre-LN(Pre-Layer Normalization)과 LayerNorm Scaling을 사용했을 때의 학습 손실 곡선을 보여줍니다.  Pre-LN은 깊이가 깊어짐에 따라 성능이 저하되는 현상을 보이는 반면, LayerNorm Scaling은 깊은 레이어의 기여도를 높여 학습 과정을 안정화시키고 성능을 향상시키는 것을 보여줍니다. 두 방법 모두 학습 초기에는 손실이 빠르게 감소하지만, LayerNorm Scaling이 Pre-LN보다 더 빠르게 수렴하고 낮은 손실 값을 유지하는 것을 확인할 수 있습니다. 이는 LayerNorm Scaling이 LLM의 학습 효율성을 향상시키는 데 효과적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Training loss of LLaMA-1B with Pre-LN and LayerNorm Scaling.
> </details>



![](https://arxiv.org/html/2502.05795/x6.png)

> 🔼 그림 6은 Pre-LN(Pre-Layer Normalization)을 사용하는 LLaMA-130M 모델에서 각 레이어의 분산(variance)이 훈련 과정에서 어떻게 변하는지 보여줍니다. 세 개의 서브플롯은 각각 1000, 3000, 6000 에폭(epoch)에서의 분산을 나타냅니다. 모든 경우에 있어서, 레이어의 깊이가 깊어짐에 따라 분산은 기하급수적으로 증가하는 패턴을 보이며, 이는 훈련 진행 정도에 관계없이 깊은 레이어에서 제어되지 않은 분산 증폭이 발생함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6:  Variance growth across layers in LLaMA-130M with Pre-LN. Each subplot shows the variance at different training stages (1000, 3000, and 6000 epochs). In all cases, the variance follows an exponential growth pattern as depth increases, indicating that deeper layers experience uncontrolled variance amplification regardless of training progress.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Pre-LN | Admin | Group-LN | Sandwich-LN | Mix-LN | LayerNorm Scaling |
|---|---|---|---|---|---| 
| 26.73 | 27.91 | 28.01 | 26.51 | 26.07 | 25.76 |{{< /table-caption >}}
> 🔼 표 2는 다양한 층 정규화 기법을 LLaMA-130M 모델에 적용했을 때의 성능을 비교한 표입니다.  성능 지표로는 perplexity(낮을수록 좋음)를 사용했습니다.  Pre-LN(Pre-Layer Normalization)을 기준으로 Admin, Group-LN, Sandwich-LN, Mix-LN, 그리고 LayerNorm Scaling 등의 다른 정규화 방법과의 perplexity 값을 비교하여 LayerNorm Scaling의 효과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Comparison against other normalization methods on LLaMA-130M. Perplexity (↓) is reported.
> </details>

{{< table-caption >}}
| Method | MMLU | BoolQ | ARC-e | PIQA | Hellaswag | OBQA | Winogrande | Average |
|---|---|---|---|---|---|---|---|---|
| **LLaMA-250M** |  |  |  |  |  |  |  |  |
| Post-LN [Ba, 2016] | 22.95 | 37.83 | 26.94 | 52.72 | 26.17 | 11.60 | 49.56 | 32.54 |
| DeepNorm [Wang et al., 2024] | 23.60 | 37.86 | 36.62 | 61.10 | 25.69 | 15.00 | 49.57 | 35.63 |
| Mix-LN [Li et al., 2024b] | 26.53 | 56.12 | 41.68 | 66.34 | 30.16 | 18.00 | 50.56 | 41.34 |
| Pre-LN [Baevski and Auli, 2019] | 24.93 | 38.35 | 40.15 | 63.55 | 26.34 | 16.20 | 49.01 | 36.93 |
| Pre-LN + LayerNorm Scaling | **27.08** | **58.17** | **45.24** | **67.38** | **32.81** | **18.80** | **52.49** | **43.14** |
| **LLaMA-1B** |  |  |  |  |  |  |  |  |
| Post-LN [Ba, 2016] | 22.95 | 37.82 | 25.08 | 49.51 | 25.04 | 13.80 | 49.57 | 31.96 |
| DeepNorm [Wang et al., 2024] | 23.35 | 37.83 | 27.06 | 52.94 | 26.19 | 11.80 | 49.49 | 32.67 |
| Mix-LN [Li et al., 2024b] | 23.19 | 37.83 | 25.08 | 49.51 | 25.04 | 11.80 | 49.57 | 31.72 |
| Pre-LN [Baevski and Auli, 2019] | 26.54 | **62.20** | 45.70 | 67.79 | 30.96 | 17.40 | 50.51 | 43.01 |
| Pre-LN + LayerNorm Scaling | **28.69** | 61.80 | **48.85** | **67.92** | **33.94** | **18.60** | **54.30** | **44.87** |{{< /table-caption >}}
> 🔼 표 3은 다양한 정규화 기법을 사용하여 LLaMA 모델을 미세 조정했을 때의 성능을 보여줍니다.  다양한 하위 작업(MMLU, BoolQ, ARC-e, PIQA, HellaSwag, OBQA, Winogrande)에 대한 성능 향상을 정량적으로 비교하여 LayerNorm Scaling이 다른 정규화 기법들보다 뛰어난 성능을 보임을 보여줍니다.  특히 LLaMA-1B 모델에서는 8개의 하위 작업 중 7개에서 LayerNorm Scaling이 가장 좋은 성능을 보였습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Fine-tuning performance (↑↑\uparrow↑) of LLaMA with various normalizations.
> </details>

{{< table-caption >}}
| Perplexity (↓) | **LLaMA-130M** | **LLaMA-250M** |
|---|---|---|
| Training Tokens | 2.2B | 3.9B |
| Pre-LN | 26.73 | 21.92 |
| + LayerScale | 27.93 | 23.45 |
| + Scaled Initialization | 26.04 | 20.98 |
| + LayerNorm Scaling | **25.76** | **20.35** |{{< /table-caption >}}
> 🔼 표 4는 다양한 크기의 LLaMA 모델에서 다양한 Layer Normalization 기법들을 비교 분석한 결과를 보여줍니다.  Pre-LN을 기준으로 LayerScale, Scaled Initialization, 그리고 LayerNorm Scaling 세 가지 방법의 성능을 perplexity(낮을수록 좋음) 지표를 사용하여 비교합니다.  각 방법의 perplexity 값을 LLaMA-130M과 LLaMA-250M 모델에 대해 제시하여, 모델 크기에 따른 성능 변화를 살펴봅니다.  이는 LayerNorm Scaling의 효과를 다른 scaling 기법들과 비교하여 보여주는 표입니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Comparison against other scaling methods.
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