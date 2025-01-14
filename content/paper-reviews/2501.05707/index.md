---
title: "Multiagent Finetuning: Self Improvement with Diverse Reasoning Chains"
summary: "다양한 추론 체인을 사용한 자기 개선을 통해 언어 모델의 성능을 크게 향상시키는 다중 에이전트 미세 조정 기법 제시"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 MIT",]
showSummary: true
date: 2025-01-10
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.05707 {{< /keyword >}}
{{< keyword icon="writer" >}} Vighnesh Subramaniam et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-13 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.05707" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.05707" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/multiagent-finetuning-self-improvement-with" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

최근 대규모 언어 모델(LLM)은 괄목할 만한 성능을 보였지만, 기저 학습 데이터에 근본적으로 제한됩니다. 기존의 자기 개선 방법은 수렴 효과가 감소하는 문제점을 가지고 있습니다. 이 논문에서는 이러한 문제를 해결하기 위해 다중 에이전트 사회를 구성하고, 각 에이전트를 독립적으로 특화시켜 자기 개선을 수행하는 새로운 방법을 제시합니다.  

본 논문에서 제시하는 다중 에이전트 미세 조정 기법은 **여러 모델을 독립적으로 학습**시켜 모델 간의 특성화 및 다양성을 증진시키는 데 중점을 둡니다. 이를 통해 **다양한 추론 체인을 유지**하고, 기존의 단일 에이전트 방법보다 훨씬 더 많은 미세 조정 라운드에서 지속적인 성능 향상을 달성할 수 있습니다.  **다양한 추론 과제에 대한 실험 결과**를 통해 이 방법의 효과를 정량적으로 보여줍니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 다중 에이전트 미세 조정을 통해 언어 모델의 자율적 자기 개선 능력 향상 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 다양한 추론 체인 유지 및 모델 특성화를 통한 지속적인 성능 향상 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 오픈소스 및 독점 언어 모델 모두에 적용 가능한 일반적인 방법 제시 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **다양한 추론 체인을 유지하면서 언어 모델의 성능을 향상시키는 새로운 방법**을 제시하여,  **자율적 자기 개선의 한계를 극복**하고 여러 연구 분야에 광범위한 영향을 미칠 수 있습니다. 특히 **오픈소스 및 독점 언어 모델 모두에 적용 가능**하다는 점에서, 향후 연구의 새로운 방향을 제시하고 다양한 응용 분야에서의 발전에 기여할 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.05707/x1.png)

> 🔼 그림 1은 다중 에이전트 미세 조정이 여러 번의 미세 조정을 거치면서 추론 성능을 향상시키는 것을 보여줍니다. 본 논문에서 제시하는 다중 에이전트 미세 조정 절차는 여러 번의 미세 조정 과정에서도 모델의 성능 향상을 가능하게 합니다. 이 그림은 MATH 데이터셋을 사용한 실험 결과를 보여줍니다.  다중 에이전트는 서로 다른 추론 경로를 통해 상호 작용하여 모델의 전반적인 성능 향상과 다양한 추론 능력을 가능하게 합니다. 각 에이전트는 독립적으로 데이터를 업데이트하고, 이를 통해 모델 간의 전문화 및 다양성이 향상되어, 단일 에이전트 미세 조정보다 더 많은 미세 조정 라운드를 거쳐도 지속적인 성능 향상을 이룰 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Multiagent finetuning improves reasoning performance over multiple rounds of finetuning. Our multiagent finetuning procedure enables models to improve across multiple iterations of finetuing. Results reported on the MATH dataset.
> </details>





{{< table-caption >}}
LLM|Methods|Arithmetic|GSM|MATH
---|---|---|---|---
GPT-3.5 (OpenAI, 2022)|Base|81.99 ± 0.99|75.60 ± 1.36|46.83 ± 2.25
GPT-3.5 (OpenAI, 2022)|Majority|94.40 ± 1.03|81.20 ± 1.24|51.40 ± 2.23
GPT-3.5 (OpenAI, 2022)|Debate|98.21 ± 0.54|83.30 ± 1.18|55.73 ± 2.21
GPT-3.5 (OpenAI, 2022)|STaR|98.38 ± 0.57|83.60 ± 1.17|53.00 ± 2.23
GPT-3.5 (OpenAI, 2022)|Majority FT|98.40 ± 0.56|83.70 ± 1.17|53.40 ± 2.23
GPT-3.5 (OpenAI, 2022)|Ours|99.62 ± 0.28|85.60 ± 1.11|60.60 ± 2.18
Phi-3 (Abdin et al., 2024)|Base|88.30 ± 1.44|81.20 ± 1.74|45.60 ± 2.10
Phi-3 (Abdin et al., 2024)|Majority|91.80 ± 1.23|81.80 ± 1.72|47.20 ± 1.82
Phi-3 (Abdin et al., 2024)|Debate|96.20 ± 0.86|84.40 ± 1.58|53.40 ± 2.28
Phi-3 (Abdin et al., 2024)|STaR|94.80 ± 0.99|85.80 ± 1.21|51.80 ± 2.06
Phi-3 (Abdin et al., 2024)|Majority FT|93.80 ± 1.08|82.20 ± 1.71|48.60 ± 2.16
Phi-3 (Abdin et al., 2024)|Ours|99.40 ± 0.34|88.60 ± 1.42|58.80 ± 2.22
Mistral (Jiang et al., 2023)|Base|10.80 ± 0.51|35.60 ± 1.92|16.60 ± 1.21
Mistral (Jiang et al., 2023)|Majority|14.80 ± 1.17|41.80 ± 0.88|16.80 ± 1.25
Mistral (Jiang et al., 2023)|Debate|19.60 ± 1.12|52.60 ± 1.26|18.20 ± 1.37
Mistral (Jiang et al., 2023)|STaR|17.40 ± 0.97|45.50 ± 1.54|17.84 ± 1.23
Mistral (Jiang et al., 2023)|Majority FT|16.40 ± 0.73|44.60 ± 1.65|18.91 ± 1.37
Mistral (Jiang et al., 2023)|Ours|22.60 ± 0.97|58.40 ± 2.11|22.50 ± 1.87
LLaMA-3 (Dubey et al., 2024)|Base|43.20 ± 2.22|75.00 ± 1.94|46.80 ± 2.23
LLaMA-3 (Dubey et al., 2024)|Majority|45.80 ± 2.23|76.40 ± 1.90|47.20 ± 2.23
LLaMA-3 (Dubey et al., 2024)|Debate|48.40 ± 2.24|78.40 ± 1.44|51.60 ± 2.23
LLaMA-3 (Dubey et al., 2024)|Majority FT|49.20 ± 2.24|77.20 ± 1.87|52.20 ± 2.23
LLaMA-3 (Dubey et al., 2024)|Ours|52.00 ± 2.24|88.60 ± 1.77|57.40 ± 2.21{{< /table-caption >}}

> 🔼 표 1은 제안된 방법과 기준 방법들의 정량적 결과를 보여줍니다. 정확도(% ± 표준 오차)를 통해 제안된 방법이 모든 데이터 세트에서 기준 방법들을 능가함을 보여줍니다. 가장 높은 값은 빨간색으로, 두 번째로 높은 값은 파란색으로 강조 표시되어 있습니다. 모든 결과는 500개의 고정된 평가 문제에 대해 보고되었으며, GPT-3.5의 GSM 결과는 중복되지 않는 신뢰 구간을 구성하기 위해 1000개의 고정된 평가 문제에 대해 보고되었습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Quantitative results of the proposed method and baselines. Our method outperforms the baselines across all datasets, as indicated by accuracy (%) ±plus-or-minus\pm± standard error. The highest values are highlighted in red, and the second-highest values are highlighted in blue. All results are reported over 500 fixed evaluation problems, expect GSM results for GPT-3.5 which are reported over 1000 fixed evaluation problems (to construct nonoverlapping confidence bars).
> </details>





### In-depth insights


#### Multiagent Finetuning
본 논문에서 제안하는 다중 에이전트 파인튜닝(Multiagent Finetuning)은 **단일 에이전트 방식의 한계를 극복**하기 위한 새로운 접근법입니다.  기존의 단일 에이전트 자기 개선 방식은 반복적인 학습으로 인해 성능 향상의 정체가 발생하는 문제점을 가지고 있는데 반해, 다중 에이전트 파인튜닝은 **여러 언어 모델 에이전트를 동시에 학습**시켜 각 에이전트가 특정 기능에 특화되도록 합니다. 이를 통해 **모델의 다양성을 확보**하고 **지속적인 성능 향상**을 가능하게 합니다.  각 에이전트는 독립적인 데이터셋으로 학습되며, 상호작용을 통해 서로의 강점을 보완하고 약점을 개선하는 시너지 효과를 창출합니다.  **다양한 추론 체인을 유지**하고 **더 많은 학습 라운드**를 수행할 수 있게 되어,  **단일 에이전트 방식보다 훨씬 뛰어난 성능**을 보입니다.  다양한 추론 작업에서의 실험 결과는 이러한 접근 방식의 효과를 명확히 보여주고 있습니다.

#### Debate Mechanism
논문에서 제시된 ‘토론 메커니즘(Debate Mechanism)’은 다중 에이전트 언어 모델들이 상호작용하며 지식을 공유하고, **추론 능력을 향상시키는 핵심 과정**입니다.  **여러 모델이 동시에 질문에 대한 답변을 생성**하고, 이후 **상호 답변을 평가하고 수정하는 반복적인 과정**을 통해 최종적인 해답에 도달합니다.  이 과정에서 각 모델은 특정 역할(생성 에이전트 또는 비평 에이전트)을 전문화하여 다양한 추론 경로를 탐색하고, 서로 다른 관점에서 문제를 접근함으로써 **단일 모델보다 더욱 정확하고 포괄적인 결과**를 얻을 수 있습니다.  **상호 비판과 수정을 통한 지속적인 학습**은 모델의 성능 개선에 중요한 역할을 하며, **단순한 반복적 학습의 한계를 극복**하는 데 기여합니다.  결국, 이 토론 메커니즘은 모델의 자율적인 성능 향상(self-improvement)을 위한 효과적인 전략을 제시합니다.

#### Diversity Metrics
본 논문에서 제시된 다양성 측정 방법은 **모델의 응답 다양성을 정량적으로 평가**하는 데 중점을 둡니다.  단순히 정확도만을 측정하는 것이 아니라, 모델이 다양한 추론 경로를 통해 문제를 해결하는 능력을 평가하고자 합니다.  **여러 가지 측정 방법**을 사용하여 다양성을 포괄적으로 평가함으로써, 모델의 견고성과 일반화 능력을 향상시키는 데 기여할 수 있음을 보여줍니다. 특히, **다양성 유지**를 통한 지속적인 성능 향상 가능성을 시사하며, 단일 에이전트 모델의 한계를 극복하는 데 중요한 역할을 합니다.  **다양성 지표 자체의 한계**도 인지하며,  다양성과 성능 간의 상관관계를 면밀히 분석하여 향후 연구 방향을 제시합니다.  결과적으로, 제시된 다양성 측정 지표들은 **모델의 성능 평가를 넘어, 모델의 내부 동작 방식에 대한 이해를 돕는 중요한 도구**임을 시사합니다.

#### Zero-Shot Gains
논문에서 "제로샷 이득(Zero-Shot Gains)"이라는 제목을 가진 부분에 대한 심층적인 분석을 통해 얻은 통찰력을 요약하면 다음과 같습니다. **제로샷 성능**은 모델이 훈련 데이터에 없는 새로운 작업이나 데이터에 대해 얼마나 잘 일반화하는지를 측정하는 중요한 지표입니다. 이는 모델의 **일반화 능력**과 **견고성**을 나타내는 지표로, 특히 제한된 데이터 환경이나 새로운 데이터가 지속적으로 생성되는 실제 환경에서 매우 중요한 의미를 가집니다.  본 논문에서 제시된 다중 에이전트 미세조정 기법은 제로샷 성능 향상에 상당한 기여를 할 것으로 예상됩니다. 이는 **다양한 추론 과정을 갖는 다수의 에이전트**를 통해 생성된 데이터로 모델을 학습시킴으로써, 특정 작업이나 데이터에 과적합되지 않고 보다 폭넓은 일반화 능력을 갖추도록 하기 때문입니다. **다양한 에이전트의 상호작용**을 통해 생성된 데이터는 각기 다른 추론 경로를 반영하며, 이는 모델의 **표현 능력**과 **적응력** 향상으로 이어집니다.  결과적으로 **다양한 유형의 추론 과제**에서 뛰어난 제로샷 성능을 보일 것으로 예측되며, 특히 어려운 추론 문제를 해결하는 데 효과적일 것으로 예상됩니다.  하지만, **제로샷 성능의 향상**은 단순히 다양한 데이터를 사용하는 것만으로는 충분하지 않으며, 데이터의 질과 다양성, 그리고 모델의 설계 및 학습 전략 등 다양한 요인들이 복합적으로 작용한다는 점을 고려해야 합니다.

#### Future Work
본 논문은 다양한 추론 과제에 걸쳐 성능을 향상시키는 다중 에이전트 미세 조정 프레임워크를 제시합니다. **미래 연구는 다음과 같은 방향으로 진행될 수 있습니다.** 첫째, **다양한 다중 에이전트 상호 작용 방식** (예: 협력적 접근 방식)을 탐구하여 다양한 상황에서 프레임워크의 유연성과 일반화 능력을 향상시킬 수 있습니다. 둘째, **모델 크기 및 훈련 비용**에 대한 제약을 완화하기 위해 모델 가중치 공유 또는 양자화와 같은 효율적인 기술을 통합하여 실제 환경에서의 적용성을 높일 수 있습니다. 셋째, **RLHF(Reinforcement Learning from Human Feedback) 또는 DPO(Direct Preference Optimization)와 같은 인간 피드백 기반 기술과의 통합**을 통해 모델의 성능을 더욱 개선하고 신뢰성을 높일 수 있습니다. 마지막으로, **다양한 언어 및 다양한 과제 유형**에 대한 프레임워크의 일반화 성능을 평가하고 개선하는 연구가 필요합니다. 이러한 미래 연구는 다중 에이전트 미세 조정 프레임워크의 잠재력을 더욱 탐색하고 자연어 처리 분야에 혁신적인 발전을 가져올 것으로 기대됩니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.05707/x2.png)

> 🔼 그림 2는 본 논문에서 제안하는 다중 에이전트 미세 조정 방법의 개요를 보여줍니다. 먼저 다중 에이전트 토론과 다수결 투표를 통해 미세 조정 데이터 세트를 생성합니다 (왼쪽). 생성된 데이터 세트는 생성 에이전트와 비평 에이전트를 미세 조정하는 데 사용됩니다 (오른쪽). 생성 모델을 미세 조정할 때는 다수결 결과(정답 출력)를 사용하여 각 에이전트의 첫 번째 라운드 응답을 선택합니다. 그런 다음 최종 라운드의 응답이 다수결 결과와 일치하는지 여부를 기반으로 최종 라운드의 응답을 사용하여 비평 모델을 미세 조정합니다 (정답과 오답 혼합). 미세 조정된 모델은 다중 에이전트 토론을 통해 결합되어 더 정확한 답변을 생성합니다. 이 그림에서는 단일 미세 조정 반복을 보여줍니다. 여러 라운드의 미세 조정 반복을 적용하면 성능이 크게 향상될 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Overview of Multiagent Finetuning.We first use multiagent debate and majority voting to create the finetuning datasets (left). These datasets are then used to finetune the generation and critic agents (right). When finetuning generation models, we use the majority voted result (”correct” output) to select first-round responses from each agent. We then finetune critic models using responses from the final round based on whether responses match the majority voted result (mix of ”correct and incorrect” outputs). The finetuned models are combined through multiagent debate to generate more accurate answers. In this figure, we illustrate a single finetuning iteration. Applying multiple rounds of finetuning iterations can significantly boost performance.
> </details>



![](https://arxiv.org/html/2501.05707/x3.png)

> 🔼 본 그림은 다양성 측정 지표 두 가지(Likelihood, Embedding Dissimilarity)를 사용하여 MATH 데이터셋에서 제안된 방법과 단일 에이전트 파인튜닝 방법의 응답 다양성을 측정한 결과를 보여줍니다. 제안된 다중 에이전트 파인튜닝 방법의 경우, 파인튜닝 반복 횟수가 증가해도 한 가지 지표에서는 다양성이 일정하게 유지되고 다른 지표에서는 다양성이 향상되는 반면, 단일 에이전트 방법은 다양성이 크게 감소하는 것을 보여줍니다. 이는 다중 에이전트 파인튜닝이 모델의 다양성을 유지하고 향상시키는 데 효과적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Diversity is preserved and can improve across iterations of finetuning. We measure the response diversity of our method and the single-agent finetuning method on the MATH dataset using two diversity measures. The diversity of our method remains consistent over finetuning iterations for one metric and improves for another metric, whereas the diversity of the single-agent method drops significantly.
> </details>



![](https://arxiv.org/html/2501.05707/x4.png)

> 🔼 그림 4는 정확도와 다양성 간의 관계를 보여줍니다.  본 논문에서는 멀티에이전트 파인튜닝을 통해 모델의 정확도를 향상시키는 동시에 다양성을 유지하는 방법을 제시합니다. 이 그림은 임베딩 유사성(embedding dissimilarity)과 MATH 데이터셋에서의 정확도 간의 관계를 여러 번의 파인튜닝 라운드에 걸쳐 시각적으로 보여줍니다. 멀티에이전트 파인튜닝을 사용하면 파인튜닝 라운드가 반복되어도 다양성이 유지되면서 정확도가 향상되는 것을 확인할 수 있습니다. 즉, 다양한 추론 과정을 유지하면서 모델 성능이 지속적으로 개선되는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Relationship between accuracy and diversity. We visualize the relationship between embedding dissimilarity and MATH accuracy across rounds of finetuning. Our multiagent finetuning preserves diversity across rounds of finetuning while improving accuracy.
> </details>



![](https://arxiv.org/html/2501.05707/x5.png)

> 🔼 그림 5는 제안된 방법의 제로샷 일반화 능력을 보여줍니다. MATH 데이터셋으로 학습된 모델이 GSM 데이터셋에서도 효과적으로 일반화되는 것을 보여줍니다.  이는 GSM 데이터셋으로 학습된 모든 기준 모델들을 성능면에서 능가함을 의미합니다.  보다 자세히 설명하면, 제안된 다중 에이전트 미세조정 기법을 통해 학습된 모델이,  기존의 단일 에이전트 방식으로 GSM 데이터셋에 대해 학습된 모델들보다 더 나은 성능을 보임을 시각적으로 나타냅니다.  이는 제안된 모델이 새로운 데이터셋에 대해 사전 학습 없이도 우수한 성능을 발휘할 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Zero-shot generalization of the proposed method. Our method demonstrates zero-shot generalization capabilities. When trained on the MATH dataset, it can effectively generalize to the GSM dataset. It outperforms all the baselines that are trained on the GSM dataset.
> </details>



![](https://arxiv.org/html/2501.05707/x6.png)

> 🔼 본 그림은 다중 에이전트 미세조정 방법과 단일 에이전트 미세조정 방법을 MATH 데이터셋에 적용하여 각 반복 학습 시도별 응답의 다양성을 측정한 결과를 보여줍니다. 다중 에이전트 미세조정 방법의 경우, 학습 반복 횟수가 증가해도 응답의 다양성이 일정하게 유지되는 반면, 단일 에이전트 미세조정 방법은 응답의 다양성이 크게 감소하는 것을 보여줍니다. 이는 다중 에이전트 미세조정 방법이 모델의 과적합을 방지하고 다양한 추론 과정을 유지하는 데 효과적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Consensus: Response diversity across finetuning iterations. We measure the response diversity based on agent consensus of our method and the single-agent finetuning method on the MATH dataset. The diversity of our method remains consistent over finetuning iterations, whereas the diversity of the single-agent method drops significantly.
> </details>



![](https://arxiv.org/html/2501.05707/x7.png)

> 🔼 그림 7은 여러 번의 미세 조정 반복을 거치면서 모델의 응답 다양성을 KL 다이버전스를 사용하여 측정한 결과를 보여줍니다. 구체적으로, 각 에이전트의 출력 토큰 확률 분포 간의 KL 다이버전스를 계산하여 다양성을 측정했습니다. 이전에 사용했던 가능도 측정과 마찬가지로, 여러 번의 미세 조정 후에도 다양성이 유지됨을 확인했습니다. 즉, 미세 조정 과정에서 모델이 특정 유형의 응답에 치우치지 않고 다양한 응답을 생성한다는 것을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: KL-Divergence: Response diversity across finetuning iterations. We measure diversity based on the KL-divergence between the probabilities of the output tokens between agents. Similar to our likelihood measurement, we find that diversity is preserved across rounds of finetuning.
> </details>



![](https://arxiv.org/html/2501.05707/x8.png)

> 🔼 그림 8은 미세 조정된 언어 모델과 미세 조정되지 않은 기본 언어 모델 간의 KL 다이버전스를 보여줍니다.  단일 에이전트 미세 조정과 다중 에이전트 미세 조정의 생성/비평 에이전트 모두에 대해 미세 조정된 에이전트와 기본 LLM 에이전트의 응답에 대한 우도 간의 KL 다이버전스를 측정합니다. Gemma-2(2B)를 사용하여 우도를 계산합니다. 본 논문의 방법은 기본 LLM 확률과 다르다는 것을 알 수 있으며, 비평 에이전트는 응답의 다이버전스가 더 크고, 본 논문의 방법은 단일 에이전트 미세 조정보다 다양성 측정값이 더 좋다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: KL Diversity between finetuned and unfinetuned LLM. We measure the KL-divergence between likelihoods of responses from finetuned agents and base LLM agents for single-agent finetuning and generation/critic agents from multiagent finetuning. Likelihoods are calculated using Gemma-2 (2B). We find that our method diverges from the base LLM probabilities and furthermore, critic agents have better divergence in responses and our method has better diversity metrics than single-agent FT.
> </details>



![](https://arxiv.org/html/2501.05707/x9.png)

> 🔼 그림 9는 다양한 에이전트의 응답 간의 임베딩 유사도 차이를 기반으로 측정한 응답 다양성을 여러번의 미세 조정 반복에 걸쳐 보여줍니다. T5-3B 인코더를 사용하여 임베딩을 계산했습니다. 결과는 가능도 측정과 유사하게 미세 조정 라운드에 걸쳐 다양성이 유지됨을 보여줍니다. 즉, 여러 에이전트의 응답이 서로 유사하지 않고 다양하게 유지되면서 모델의 성능이 향상됨을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Embedding Dissimilarity: Response diversity across finetuning iterations. We measure the response diversity based on the embedding dissimilarity between the responses of different agents, where embeddings are computed using the T5-3B encoder. We notice that similar to likelihood measurement, we find that diversity is preserved across rounds of finetuning.
> </details>



![](https://arxiv.org/html/2501.05707/x10.png)

> 🔼 그림 10은 온도를 높여 다양성을 유도하는 방법에 대한 실험 결과를 보여줍니다. 기존의 Single-Agent FT(Fine-tuning) 방법에 온도 2를 적용한 추가적인 기준선을 설정하여 모델이 더 다양한 응답을 생성하도록 했습니다. 실험 결과, 제안된 다중 에이전트 미세조정 방법이 높은 온도 설정을 사용한 Single-Agent FT보다 성능이 우수하다는 것을 보여줍니다. 이는 단순히 온도를 높이는 것만으로는 정확도에 도움이 되는 방식으로 다양성을 증가시킬 수 없다는 것을 시사합니다. 다중 에이전트 미세조정 방법은 다양성을 유지하면서 정확도를 향상시키는 더 효과적인 방법임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Inducing diversity through increasing temperature. We introduce an additional baseline where we apply the Single-Agent FT baselin with a temperature of 2. By increasing the sampling temperature, we allow the model to generate more diverse responses. We observe that our method out-performs higher temperature settings, which demonstrates that temperature does not increase diversity in a way that is useful for accuracy.
> </details>



![](https://arxiv.org/html/2501.05707/x11.png)

> 🔼 그림 11은 다양한 난이도의 MATH 데이터셋을 사용하여 다중 에이전트 미세 조정의 반복적인 성능 향상을 보여줍니다. 500개의 MATH 문제 샘플을 사용하여 여러 번의 미세 조정을 수행했으며, 더 어려운 도메인에서도 다중 에이전트 미세 조정을 통해 지속적인 자가 개선이 가능함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Multiple iterations of finetuning over all levels of MATH. We apply multiple iterations of finetuning over 500 examples of MATH sampled from all levels. Even over a more difficult domain, we see significant improvements from multiagent finetuning that continue to self-improve.
> </details>



![](https://arxiv.org/html/2501.05707/x12.png)

> 🔼 이 그림은 MATH 데이터셋으로 학습된 모델을 사용하여 GSM 데이터셋에서 제로샷 일반화 능력을 테스트한 결과를 보여줍니다.  1000개의 GSM 문제에 대한 테스트 결과, 제안된 다중 에이전트 미세조정 기법이 모든 기준 모델보다 성능이 우수함을 보여줍니다.  그림은 다중 에이전트 미세조정 기법의 제로샷 일반화 능력을 명확하게 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Testing zero-shot generalization across 1000 GSM problems We test the zero-shot capabilities of our method using models trained on the MATH dataset. We find that over 1000 problems of GSM, our method performs better than all baselines.
> </details>



![](https://arxiv.org/html/2501.05707/x13.png)

> 🔼 이 그림은 산술 연산 문제를 사용하여 Mistral 모델을 미세 조정한 후 GSM(Grade School Math) 데이터셋에서의 제로샷 일반화 능력을 평가한 결과를 보여줍니다.  그림은 산술 문제로 미세 조정했을 때  MATH 데이터셋으로 미세 조정했을 때보다 GSM 성능이 더 향상됨을 보여줍니다.  이는 제안된 다 에이전트 미세 조정 방법의 일반화 성능을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: Zero-shot generalization after arithmetic finetuning. We evaluate the ability of our method to generalize after finetuning Mistral on the arithmetic task and evaluating on GSM. We find that this aids in GSM performance, even more than finetuning with MATH.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| LLM | Ablations | Arithmetic | GSM | MATH |
|---|---|---|---|---|
| GPT-3.5 (OpenAI, 2022) | Multiagent FT (Ours) | 99.62 ± 0.28 | 85.60 ± 1.67 | 60.60 ± 2.18 |
|  | Multiagent FT w/o summary | 99.20 ± 0.40 | 82.20 ± 1.72 | 51.70 ± 2.24 |
|  | Multiagent FT w/o critic | 99.20 ± 0.40 | 83.80 ± 1.65 | 50.80 ± 2.24 |
|  | Single-agent FT | 99.00 ± 0.45 | 83.60 ± 1.66 | 56.80 ± 2.21 |
|  | Single-agent FT w/o debate | 87.20 ± 1.49 | 75.00 ± 1.93 | 48.89 ± 2.23 |
| Phi-3 (Abdin et al., 2024) | Multiagent FT (Ours) | 99.40 ± 0.34 | 88.60 ± 1.42 | 58.80 ± 2.22 |
|  | Multiagent FT w/o summary | 98.80 ± 0.51 | 84.40 ± 1.68 | 55.00 ± 2.09 |
|  | Multiagent FT w/o critic | 98.20 ± 0.62 | 86.00 ± 1.58 | 56.60 ± 2.22 |
|  | Single-agent FT | 97.40 ± 0.71 | 86.80 ± 1.51 | 56.80 ± 2.21 |
|  | Single-agent FT w/o debate | 92.20 ± 1.20 | 83.60 ± 1.66 | 50.20 ± 2.24 |
| Mistral (Jiang et al., 2023) | Multiagent FT (Ours) | 22.60 ± 1.87 | 58.40 ± 2.11 | 22.50 ± 1.87 |
|  | Multiagent FT w/o summary | 21.80 ± 1.84 | 56.00 ± 1.56 | 20.20 ± 1.55 |
|  | Multiagent FT w/o critic | 21.00 ± 1.82 | 54.80 ± 1.60 | 19.01 ± 1.59 |
|  | Single-agent FT | 21.20 ± 1.83 | 55.00 ± 2.22 | 19.21 ± 1.69 |
|  | Single-agent FT w/o debate | 17.71 ± 1.70 | 51.20 ± 2.24 | 17.22 ± 1.54 |
| LLaMA-3 (Dubey et al., 2024) | Multiagent FT (Ours) | 52.00 ± 2.24 | 88.60 ± 1.77 | 57.40 ± 2.21 |
|  | Multiagent FT w/o summary | 50.40 ± 2.24 | 83.20 ± 1.67 | 51.60 ± 2.23 |
|  | Multiagent FT w/o critic | 48.60 ± 2.24 | 82.20 ± 1.70 | 50.50 ± 2.23 |
|  | Single-agent FT | 48.00 ± 2.23 | 84.40 ± 1.62 | 52.40 ± 2.23 |
|  | Single-agent FT w/o debate | 44.00 ± 2.22 | 81.60 ± 1.73 | 48.80 ± 2.24 |{{< /table-caption >}}
> 🔼 표 2는 제안된 방법의 각 구성 요소에 대한 분석 결과를 보여줍니다. 요약, 비평 에이전트와 생성 에이전트의 결합, 다중 에이전트 미세 조정 및 다중 에이전트 토론 등이 성능 향상에 기여함을 보여줍니다. 정확도와 표준 오차가 함께 보고됩니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Ablation results. We examine each component of the proposed method and found that summarization, the combination of critic and generation agents, multiagent finetuning, and multiagent debate all contribute to performance improvement. The accuracy (%) ±plus-or-minus\pm± standard error is reported.
> </details>

{{< table-caption >}}
| LLM | Methods | Arithmetic | GSM | MATH |
|---|---|---|---|---|
| GPT-3.5 | Cooperative (Base) | 96.60 ± 0.83 | 81.80 ± 1.73 | 53.60 ± 2.23 |
|  | Cooperative (FT) | **98.80** ± 0.39 | **84.00** ± 1.64 | **56.40** ± 2.21 |{{< /table-caption >}}
> 🔼 이 표는 본 논문의 협력적 미세 조정(Cooperative Finetuning)에 대한 결과를 보여줍니다.  기존의 경쟁적 다중 에이전트 설정(multi-agent debate)과 달리, 이 방법은 에이전트들이 협력적으로 답을 생성하도록 합니다.  예를 들어, 3개의 에이전트와 2라운드의 대화를 통해 각 에이전트가 다른 에이전트의 응답을 통합하여 최종 응답을 생성하는 방식입니다. 표에는 다양한 언어 모델(LLM)과 작업(Arithmetic, GSM, MATH)에 대한 정확도 결과가 제시되어 있으며,  협력적 미세 조정이 경쟁적 설정보다 성능 향상에 기여하는지 여부를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Cooperative Finetuning. Our method supports fine-tuning in cooperative settings, where agents work together (e.g., 3 agents, 2 rounds).
> </details>

{{< table-caption >}}
| LLM | Methods | Arithmetic | GSM | MATH |
|---|---|---|---|---|
| GPT-3.5 | Debate | 99.40 ± 0.34 | 85.40 ± 1.58 | 58.20 ± 2.22 |
|  | Majority FT | 99.60 ± 0.28 | 86.20 ± 1.54 | 59.00 ± 2.19 |
|  | Ours | **100.00 ± 0.00** | **88.20 ± 1.44** | **62.80 ± 2.16** |
| Phi-3 | Debate | 97.40 ± 0.71 | 86.00 ± 1.55 | 55.20 ± 2.22 |
|  | Majority FT | 95.80 ± 0.90 | 84.80 ± 1.61 | 53.20 ± 2.23 |
|  | (Ours) | **99.80 ± 0.20** | **89.40 ± 1.38** | **60.40 ± 2.19** |{{< /table-caption >}}
> 🔼 이 표는 다수 대리자 논쟁(Multiagent Debate)을 사용한 다중 에이전트 미세 조정(Multiagent Finetuning) 방법의 성능을 보여줍니다. 표 1에서 제시된 3개의 에이전트와 2라운드의 논쟁 결과와 비교하여, 에이전트 수를 5개로 늘리고 논쟁 라운드를 2라운드로 유지했을 때의 결과를 보여줍니다.  본 연구의 방법은 기준 모델들보다 여전히 우수한 성능을 보이며, 에이전트 수 증가가 성능 향상에 기여함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 4: More agents of debate. With 5 agents and 2 rounds of debate, our methods still outperform the baselines and show better results than the 3 agents and 2 rounds of debate results presented in Table 1 of the main paper.
> </details>

{{< table-caption >}}
| LLM | Methods | MATH |
|---|---|---|
| LLaMA-3 [Dubey et al., 2024] | Base | 46.80 ± 2.23 |
|  | Debate | 51.60 ± 2.23 |
|  | Unique ID | 50.80 ± 2.24 |
|  | Ours | 57.40 ± 2.21 |{{< /table-caption >}}
> 🔼 본 표는 다중 에이전트 파인튜닝과 고유 ID(Unique ID) 방식의 성능을 비교 분석한 결과를 보여줍니다.  다중 에이전트 파인튜닝은 각 에이전트(생성 또는 비평 에이전트)에 고유 ID 토큰을 제공하여 다양성을 유지하는 방식입니다.  실험 결과, 고유 ID 방식은 다중 에이전트 파인튜닝 방식에 비해 성능 향상이 미미하여 다중 에이전트 파인튜닝의 효과를 입증하는 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Unique ID vs Multiagent Finetuning. We introduce an additional comparison to multiagent finetuning where we feed a unique ID token to each agent, corresponding to a generation or critic agent. We find that this is not comparable to improvements on multiagent finetuning.
> </details>

{{< table-caption >}}
| LLM | Methods | MATH |
|---|---|---|
| LLaMA-3 (Dubey et al., 2024) | Base | 24.40 ± 1.92 |
|  | Majority | 25.20 ± 1.94 |
|  | Debate | 29.80 ± 2.05 |
|  | Majority FT | 28.00 ± 2.01 |
|  | Ours | **34.20 ± 2.12** |{{< /table-caption >}}
> 🔼 표 6은 다양한 난이도의 수학 문제에 대한 다중 에이전트 미세 조정의 추가 평가 결과를 보여줍니다.  MATH 데이터셋의 모든 레벨의 문제들을 포함하여 더 어려운 문제들에 대해서도 본 연구의 방법론이 기준 방법론들보다 성능이 우수함을 보여줍니다. 이는 본 연구의 방법론이 더욱 광범위한 환경에서도 적용 가능함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Additional Evaluation of Multiagent Finetuning on more difficult tasks. Our method outperforms the baselines on more difficult tasks including examples from all levels of MATH. This shows the applicability of our method in more broad settings.
> </details>

{{< table-caption >}}
| LLM | Methods | MMLU |
|---|---|---|
| LLaMA-3 (Dubey et al., 2024) | Base | 60.40 ± 2.18 |
|  | Majority | 61.80 ± 2.17 |
|  | Debate | 65.80 ± 2.12 |
|  | Majority FT | 63.40 ± 2.15 |
|  | Ours | 68.80 ± 2.07 |{{< /table-caption >}}
> 🔼 본 논문의 표 7은 MMLU 벤치마크를 사용한 추가 평가 결과를 보여줍니다. 500개의 MMLU 예시로 미세 조정을 하고 500개의 다른 MMLU 예시로 테스트했습니다. 결과적으로 제시된 방법이 다른 기준 방법들보다 성능이 우수함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 7: MMLU Evaluation We introduce an additional evaluation with the MMLU benchmark, finetuning on 500 MMLU examples and testing on 500 different MMLU examples. We find that our method performs better than other baselines.
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