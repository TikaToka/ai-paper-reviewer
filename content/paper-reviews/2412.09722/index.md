---
title: "GReaTer: Gradients over Reasoning Makes Smaller Language Models Strong Prompt Optimizers"
summary: "GREATER는 추론에 대한 그레이디언트를 활용하여 소규모 언어 모델의 프롬프트를 최적화하여 대규모 LLM 없이도 성능을 향상시킵니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Pennsylvania State University",]
showSummary: true
date: 2024-12-12
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.09722 {{< /keyword >}}
{{< keyword icon="writer" >}} Sarkar Snigdha Sarathi Das et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-16 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.09722" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.09722" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/greater-gradients-over-reasoning-makes" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

**LLM은 프롬프트 디자인에 민감하여 최적화가 중요합니다.** 자동 프롬프트 엔지니어링은 시스템 LLM 쿼리를 통해 성능을 향상시키는 것을 목표로 합니다. 기존 방법은 텍스트 피드백에만 의존하며 종종 프롬프트 개선을 위해 더 크고 비용이 많이 드는 LLM이 필요합니다. 이러한 소규모 모델의 대규모 LLM 판단에 대한 의존성은 컴퓨팅 비용이 많이 들고 소규모 모델에서 성능이 좋지 않을 수 있습니다.

이 연구는 추론에 대한 그레이디언트를 통합하는 새로운 프롬프트 최적화 기법인 **GREATER**를 제시합니다. GREATER는 작업 손실 그레이디언트를 활용하여 비용이 많이 드는 대규모 LLM에 의존하지 않고 소규모 모델의 프롬프트 자체 최적화를 가능하게 합니다. 이 방법은 토큰 후보를 생성하고 추론을 통해 최종 답변 로짓을 추출하여 손실을 계산합니다. 그런 다음 그레이디언트는 최상의 토큰 선택을 안내하여 **소규모 모델의 추론을 위한 프롬프트를 개선합니다.**

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} GREATER는 소규모 LLM의 자체 프롬프트 최적화를 가능하게 합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} GREATER는 GSM8k, BBH, FOLIO를 포함한 다양한 추론 작업에서 최첨단 프롬프트 최적화 방법을 능가합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} GREATER에 의해 최적화된 프롬프트는 더 나은 전이성을 보여줍니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**프롬프트 최적화는 LLM 성능에 매우 중요하지만 기존 방법은 대규모 LLM에 의존합니다.** 이 연구는 소규모 LLM을 위한 그레이디언트 기반 프롬프트 최적화 기법인 GREATER를 소개함으로써 이러한 문제를 해결합니다. 이는 소규모 LLM 자체 개선을 가능하게 하여 리소스 사용량이 많은 대규모 모델에 대한 의존성을 줄이는 동시에 최첨단 성능을 달성할 수 있도록 합니다. 이 연구는 경량 LLM을 사용하는 연구자들에게 귀중한 도구를 제공하고 효율적이고 효과적인 프롬프트 엔지니어링을 위한 새로운 길을 열어줍니다. 또한 추론 기능이 개선된 프롬프트를 개발하는 데 중점을 두어 LLM 연구에 광범위한 영향을 미칩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.09722/extracted/5991147/figures/overview_greater.png)

> 🔼 이 그림은 텍스트 피드백 기반 프롬프트 최적화와 GREATER를 비교합니다. 텍스트 피드백 기반 방법은 거대 언어 모델(LLM)의 판단에 전적으로 의존하여 프롬프트를 개선합니다. 반면 GREATER는 작은 모델에서 생성된 토큰 후보를 사용하고 손실 기울기를 기반으로 최적의 토큰을 선택하는 방식으로 작동합니다. 따라서 거대 LLM 없이도 프롬프트를 최적화할 수 있습니다. GREATER는 추론 과정을 먼저 생성하고, 추출 프롬프트를 적용하여 정답 로짓을 얻고, 이를 통해 손실 기울기를 계산하는 '추론 기반 기울기' 접근 방식을 사용합니다. 이는 언어 모델 피드백 대신 직접적인 신호를 사용하여 최적화를 수행함으로써 더 효율적인 프롬프트 개선을 가능하게 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Comparison of textual feedback-based prompt optimization and GReaTer. Left: textual feedback relies entirely on a larger language model’s judgments. Right: GReaTer avoids external large, proprietary models, using token suggestions from a small model and guiding prompt token selection with loss gradients. GReaTer incorporates model reasoning by first generating reasoning, then applying an extraction prompt to obtain answer logits for computing loss gradients. This “gradient over reasoning” approach optimizes using direct signals rather than relying on language model feedback.
> </details>





{{< table-caption >}}
| Initialization Prompt | Optimized Prompt | Score |
|---|---|---| 
| Default (*Use proper logical …*) | Use movie ratings data available here above movies for reference. This HOFF has an interesting analysis based solely on options to options based on movies ratings. Expect from the other movies you are asked, choose option from those mentioned below. | 56 |
| Misleading (Use no thinking just feeling.) | Use one one-liner and explain stepwise for why. ONLY READING IS ALLOWABLE AND NO CHATTY CHAT OR EXCL. | 55 |{{< /table-caption >}}

> 🔼 GReaTer는 다양한 추론 작업에서 상당한 성능 향상을 가져오며, 소규모 모델의 프롬프트 최적화에 있어서 효과적임을 입증합니다. 최첨단 프롬프트 최적화 방법보다 성능이 뛰어납니다. 표는 GReaTer를 사용한 여러 추론 작업(GSM8K, BBH, FOLIO)에서의 성능 향상을 다른 프롬프트 최적화 기법과 비교하여 보여줍니다. Llama-3-8B 및 Gemma-2-9B와 같은 경량 언어 모델을 사용한 GReaTer의 성능이 다른 방법보다 우수함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Overall results. GReaTer brings substantial performance improvements across different reasoning tasks, demonstrating its efficacy in prompt optimization with smaller models. It considerably outperforms state-of-the-art prompt optimization methods. Detailed prompts and results with breakdown across all the tasks are shown in Appendix H and Appendix I.
> </details>





### In-depth insights


#### Gradient-Based Prompt
**기울기 기반 프롬프트**는 LLM의 성능 향상을 위한 강력한 기법으로 떠오르고 있습니다. 이는 프롬프트를 미세 조정하여 특정 작업에 대한 모델 출력을 최적화하는 것을 포함합니다. 기울기 기반 최적화를 사용하면 **프롬프트 엔지니어링 프로세스를 자동화**하여 수동 프롬프트 디자인의 필요성을 줄일 수 있습니다. 이 접근 방식의 핵심 이점은 **더 작은 LLM에서도 강력한 성능**을 달성할 수 있다는 것입니다. 이는 더 큰 모델의 계산 비용 없이도 다양한 작업에서 경쟁력 있는 결과를 얻을 수 있도록 합니다. 또한 기울기 기반 프롬프트는 **이전 프롬프트 엔지니어링 방법에 비해 향상된 전이성**을 보여줍니다. 이는 다양한 작업에 걸쳐 일관되고 안정적인 성능을 보장하여 실제 응용 프로그램에서 실용성을 높입니다. 또한 기울기 정보를 활용하여 **추론 프로세스를 최적화하여 보다 정확하고 효율적인 출력**을 생성할 수 있습니다. 이러한 이점에도 불구하고 고려해야 할 몇 가지 과제와 제한 사항이 있습니다. **기울기 기반 프롬프트는 토큰 불연속성 및 최적화 프로세스**로 인해 발생할 수 있는 잠재적인 문제와 같은 고유한 복잡성을 야기합니다. 또한, **기울기 소실 또는 폭발 문제**와 같은 기존 기울기 기반 방법의 일반적인 문제는 **프롬프트 최적화**에 영향을 미칠 수 있습니다. 마지막으로, **과적합 가능성**은 항상 **기울기 기반 프롬프트**를 사용할 때 고려해야 합니다. 적절한 정규화 및 검증 기술을 구현하여 과적합을 방지하고 다양한 작업 및 도메인에 대한 프롬프트의 일반화 가능성을 보장하는 것이 중요합니다.

#### Reasoning Enhancement
**추론 향상**은 LLM의 핵심 기능 향상에 중점을 둡니다. 프롬프트 최적화와 추론 체인 활용을 통해 **복잡한 추론 능력**을 높이는 것이 관건입니다. **GREATER**와 같은 기법은 그레이디언트 정보를 활용하여 추론 과정을 최적화하고, **명확하고 구조화된 프롬프트**를 생성하여 LLM이 문제 해결에 효과적으로 접근하도록 유도합니다. **자체 최적화**는 외부 LLM 의존성을 줄여 효율성을 높입니다. **다양한 추론 작업**에서 성능 향상을 입증하며, 특히 경량 LLM에서 그 효과가 두드러집니다. **프롬프트 전이성** 또한 향상되어 다양한 모델에서 일관된 성능을 보입니다. 하지만 생성된 프롬프트의 **문법적 오류나 비형식적 어조**는 개선의 여지가 있습니다. 전반적으로, 추론 향상은 LLM 성능 극대화에 필수적이며, **지속적인 연구 및 개발**이 필요한 분야입니다.

#### Small Model Perf. Boost
**GREATOR는 경량 언어 모델의 추론 능력을 향상시키는 것을 목표로 하는 기법입니다.** 큰 모델에 의존하지 않고 그레이디언트를 사용하여 프롬프트를 최적화하는 것이 핵심입니다. **작은 모델은 피드백 생성 능력이 부족하여 큰 모델에 의존해야 하는 기존 방법과 달리,** GREATOR는 작업 손실 그레이디언트를 활용하여 자체 최적화를 가능하게 합니다. **이를 통해 추론 과정에서 그레이디언트 정보를 직접 통합하여 더 정확한 프롬프트 개선 방향을 제시합니다.** BBH, GSM8k 및 FOLIO를 포함한 다양한 추론 작업에서 GREATOR는 **기존의 프롬프트 최적화 기법보다 성능이 우수하며,** 심지어 큰 언어 모델에 필적하는 결과를 보여줍니다. **이는 경량 모델의 성능을 향상시키는 효과적인 방법임을 시사합니다.**

#### Transferability & Limitations
**GREATER의 주요 강점은 전이성**입니다. 작은 언어 모델에서 최적화된 프롬프트를 더 큰 모델이나 다른 작은 모델에 적용해도 성능 향상을 유지하는 경향이 있습니다. 이는 **다양한 모델에서 GREATER를 효과적으로 활용**할 수 있음을 시사합니다. 하지만 **모델 크기가 커짐에 따라 GREATER의 성능 향상 폭은 줄어드는 경향**이 있습니다. 대형 모델은 이미 상당한 성능을 가지고 있기 때문에 프롬프트 최적화를 통한 추가적인 이점이 제한적일 수 있습니다. 또한, GREATER는 **프롬프트의 문법적 오류나 비형식적인 어투**를 생성할 수 있습니다. 이는 Top-k 매개변수를 조정하거나 동적 Top-k 선택을 통해 완화할 수 있지만, **프롬프트 품질에 대한 추가적인 검토가 필요**할 수 있습니다. 마지막으로, GREATER는 **추론 과정에 대한 명시적인 정보가 부족한 작업에서 어려움**을 겪을 수 있습니다. GREATER는 추론 체인을 기반으로 작동하기 때문에 **추론 과정 자체가 중요한 작업에서는 성능이 제한**될 수 있습니다. 그럼에도 불구하고, GREATER는 경량 언어 모델의 추론 능력을 향상시키는 **효과적이고 효율적인 방법**을 제공하며, 특히 **자원 제약적인 환경에서 유용**하게 활용될 수 있습니다.

#### Future Prompt Optimization
**프롬프트 최적화의 미래**는 LLM의 발전과 밀접하게 연결될 것입니다. **자동화된 프롬프트 엔지니어링**은 더욱 정교해지고 효율적이 될 것이며, 적은 수의 예제만 사용하는 **퓨샷 학습**의 효과를 극대화하기 위해 최적화될 것입니다. **다양한 작업에 특화된 맞춤형 프롬프트**가 개발될 것이고, 사용자의 의도를 더 잘 이해하고 반영하는 **대화형 프롬프트**도 등장할 것입니다. 또한, 프롬프트의 **편향성 및 안전성** 문제를 해결하는 연구가 중요해지고, **설명 가능성**을 높이는 방향으로 발전할 것입니다. 마지막으로, **새로운 모델과 하드웨어**의 발전은 프롬프트 최적화 기법 자체의 혁신을 가져올 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.09722/extracted/5991147/figures/greatprompt_methodology_v2.png)

> 🔼 GReaTer는 세 단계로 작동합니다. (i) 언어 모델(fLLM)이 입력 샘플을 기반으로 후보 토큰을 생성합니다. (ii) fLLM은 작업 입력과 현재 프롬프트를 사용하여 추론을 생성하고 최종 답변 로짓을 추출합니다. (iii) 로짓을 사용하여 손실을 계산하고 생성된 추론에 대한 기울기를 계산합니다. 이러한 기울기는 현재 프롬프트의 현재 위치를 업데이트하기 위한 후보 토큰 선택을 결정합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Overall workflow of GReaTer. (i) The language model fLLMsubscript𝑓LLMf_{\text{LLM}}italic_f start_POSTSUBSCRIPT LLM end_POSTSUBSCRIPT generates token candidates by conditioning on input samples. (ii) fLLMsubscript𝑓LLMf_{\text{LLM}}italic_f start_POSTSUBSCRIPT LLM end_POSTSUBSCRIPT uses task input and current prompt to generate reasoning and extract final answer logits. (iii) The logits are used to calculate loss and compute gradient over generated reasoning with respect to the candidate tokens. These gradients determine the selection of candidate token to update the current position of the current prompt.
> </details>



![](https://arxiv.org/html/2412.09722/extracted/5991147/figures/impact_gradient_reasoning.png)

> 🔼 이 그림은 추론 과정 없이 기울기 계산을 수행했을 때 작업 성능이 크게 저하됨을 보여줍니다. 즉, GREATER에서 '추론에 대한 기울기'를 제거하면 movie_recommendation 및 tracking_shuffled_objects_five_objects 작업 모두에서 Llama-3-8B 및 Gemma-2-9B 모델의 성능이 저하됩니다. 이는 추론 과정이 기울기 계산 및 최적화에 필수적임을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Ablation study on “Gradient Over Reasoning” in GReaTer. Gradient calculation without reasoning causes notable performance drops, showing the importance of reasoning for gradients.
> </details>



![](https://arxiv.org/html/2412.09722/extracted/5991147/figures/five_vs_zero_shot.png)

> 🔼 이 그림은 Llama-3-8B-Instruct 모델을 사용하여 5-shot In-Context Learning과 GREATER 기법을 사용한 Zero-shot 추론의 성능을 비교한 결과를 보여줍니다. 두 가지 작업(영화 추천 및 5개의 물체 추적)에서 GREATER를 사용한 Zero-shot 추론이 5-shot In-Context Learning보다 성능이 크게 향상되었음을 알 수 있습니다. 이는 GREATER가 효율적인 프롬프트 최적화를 통해 적은 수의 예시 없이도 In-Context Learning에 비해 경쟁력 있는 성능을 달성할 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Efficacy of GReaTer in zero-shot setting compared to five-shot inference with Llama-3-8B-Instruct.
> </details>



![](https://arxiv.org/html/2412.09722/extracted/5991147/figures/llama_wdl.png)

> 🔼 GReaTer가 Llama-3-8B-Instruct 모델을 사용한 최적화에서 APO, TextGrad, APE, PE2와 같은 최첨단 프롬프트 최적화 기법보다 훨씬 더 나은 성능을 보여줍니다. GReaTer는 대부분의 작업에서 다른 방법보다 승률이 높으며, 이는 최적화에서 GReaTer의 효율성을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Win/Draw/Loss Comparison of GReaTer and SOTA prompt optimization techniques APO, TextGrad, APE, and PE2 in optimization with Llama-3-8B-Instruct. GReaTer maintains a significant winning margin over these methods, highlighting its effectiveness in optimization.
> </details>



![](https://arxiv.org/html/2412.09722/extracted/5991147/figures/llama_all_res.png)

> 🔼 Llama-3-8B 모델을 사용한 최적화에서 GReaTer와 SOTA 프롬프트 최적화 기법(APO, TextGrad, APE, PE2)의 21가지 BBH 작업에 대한 전체 성능 분석 결과입니다. GReaTer가 다른 방법보다 성능이 뛰어남을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Full performance breakdown across 21 BBH tasks of GReaTer and SOTA prompt optimization techniques APO, TextGrad, APE, and PE2 in optimization with Llama-3-8B.
> </details>



![](https://arxiv.org/html/2412.09722/extracted/5991147/figures/gemma_wdl.png)

> 🔼 GReaTer는 Gemma-2-9B-it 모델을 사용한 최적화에서 APO, TextGrad, APE, PE2와 같은 SOTA 프롬프트 최적화 기법과 비교하여 Win/Draw/Loss를 보여줍니다. GReaTer는 대부분의 작업에서 다른 방법보다 성능이 뛰어나 최적화의 효율성을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Win/Draw/Loss Comparison of GReaTer and SOTA prompt optimization techniques APO, TextGrad, APE, and PE2 in optimization with Gemma-2-9B-it. GReaTer maintains winning margin over these methods, highlighting its effectiveness in optimization.
> </details>



![](https://arxiv.org/html/2412.09722/extracted/5991147/figures/gemma_allres.png)

> 🔼 이 그림은 Gemma-2-9B 모델을 사용하여 21개의 Big Bench Hard (BBH) 추론 작업에서 GReaTer와 다른 최첨단 프롬프트 최적화 기법(APO, TextGrad, APE, PE2)의 성능을 자세히 비교하여 보여줍니다. 각 작업에 대한 성능은 막대 그래프로 표시되어 있으며, GReaTer와 기준 성능 간의 차이를 명확하게 보여줍니다. GReaTer가 대부분의 작업에서 다른 방법보다 성능이 우수함을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Full performance breakdown across 21 BBH tasks of GReaTer and SOTA prompt optimization techniques APO, TextGrad, APE, and PE2 in optimization with Gemma-2-9B.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | Optimized Prompt | Score |
|---|---|---|
| TextGrad | You will answer a mathematical reasoning question. Think step by step. The last line of your response should be of the following format: ’Answer: VALUE’ where VALUE is a numerical value. | 78.5 |
| APE | Work in sequence: Complete each task in order, tackling one task at a time, and only moving on to the next once it’s finished. | 79.9 |
| APO | Break down complex problems into smaller, logical steps, considering mathematical operations, variable relationships, and implicit rules. Provide a clear, sequential solution, accounting for nuanced language and context. | 81.1 |
| PE2 | Break down complex problems into smaller, manageable steps, and solve them step by step. | 80.1 |
| GReaTer | Use your knowledge reasoning and think step by step. Finally give the actual correct answer. | 82.6 |{{< /table-caption >}}
> 🔼 이 표는 GREATER가 더 큰 독점 LLM으로 최적화된 프롬프트와 비교하여 어떻게 수행되는지 보여줍니다. Llama-3-8B 및 Gemma-2-9B를 사용하여 GSM8K 및 5개의 무작위로 선택된 BBH 작업에서 GPT-4 및 PaLM-2-L로 최적화된 프롬프트보다 GREATER가 동등하거나 더 나은 성능을 보입니다. 예를 들어 '대상 모델: Llama-3-8B 및 방법(최적화 기준): APE(GPT-4)'는 프롬프트 평가에 Llama-3-8B가 사용되었지만 프롬프트는 GPT-4를 사용하는 APE로 최적화되었음을 나타냅니다. EvoPrompt는 GSM8K에 대한 프롬프트를 보고하지 않습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Comparison of GReaTer with prompts optimized by larger proprietary LLMs. GReaTer performs on par with or notably better than prompts optimized by GPT 4 and PaLM-2-L across GSM8K and five randomly chosen BBH tasks using Llama-3-8B and Gemma-2-9B. EvoPrompt does not report its prompts on GSM8K. Here, Target Model: Llama-3-8B and Method (Optimized by): APE (GPT-4) indicates that Llama-3-8B was used for prompt evaluation while the prompt was optimized by GPT-4 with APE.
> </details>

{{< table-caption >}}
| Method | Optimized Prompt | Score |
|---|---|---| 
| TextGrad | You will answer a reasoning question by identifying the essential information, making specific conclusions, and providing nuanced and detailed reasoning. Think critically and systematically, focusing on the most relevant details, and avoid unnecessary complexity… | 56.2 |
| APE | Tackle it incrementally! | 57.6 |
| APO | Analyze the premises step by step, identifying specific details, assumptions, and ambiguities. Draw a logical conclusion based on the evidence provided, considering multiple perspectives and potential counterarguments, while accounting for scope, context, and edge cases. | 58.6 |
| PE2 | Analyze the statement based on the provided premise, determining whether it is true, false, or uncertain. Consider all relevant information to reach a logical conclusion. | 62.6 |
| GReaTer | Use of logical deductions to show if your conclusion matches an appropriate option you chose from multiple options above by explaining how to determine whether the given conclusion follows from the given information above by explaining each step taken during the process. | 62.6 |{{< /table-caption >}}
> 🔼 이 표는 Llama-3-8B로 최적화된 프롬프트를 Gemma-2-9B에 적용했을 때와 그 반대의 경우를 비교하여 GReaTer가 생성한 프롬프트의 전이 가능성을 다른 최첨단 프롬프트 최적화 방법과 비교하고 있습니다. GReaTer는 다른 방법보다 더 강력한 전이 가능성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Transferability of Llama-3-8B optimized prompts to Gemma-2-9B (Upper) and vice versa (Lower). The results demonstrate that prompts produced by GReaTer exhibit strong transferability compared with those produced by other state-of-the-art prompt optimization methods.
> </details>

{{< table-caption >}}
| Method | Optimized Prompt | 
|---|---| 
| | formal_fallacies |
| PE2 | Determine the validity of the given argument. |
| APE | Simplify and analyze. |
| TextGrad | You will answer a reasoning question by explicitly identifying the key relationships between the premises and the conclusion, and explaining how they lead to the conclusion. Use clear and concise language to facilitate understanding, and… |
| APO | Analyze the argument step by step, considering premises, logical connections, and conditional statements. Identify the conclusion and evaluate its validity, considering sufficient and necessary conditions, counterexamples, and alternative scenarios. |
| GReaTer | Use formal notation and and think step by step. Finally give the actual correct answer. |
| | salient_translation_error_detection |
| PE2 | Identify the type of error in the translation from German to English. n nSource: [insert source text] nTranslation: [insert translation] nError type: [one of the following] n(A) Modifiers or Adjectives n(B) Numerical Values n(C) Negation… |
| APE | Clarify your thoughts, break it down step by step. |
| TextGrad | You will answer a reasoning question by providing a detailed analysis of the original text and the translation. Think step by step, considering multiple possible explanations for the error. Clearly explain how each step leads… |
| APO | Analyze the translation error by carefully reading the original sentence and identifying the specific mistake. Consider the exact words, phrases, and grammatical structures to determine the correct error type from the options. |
| GReaTer | Use your answer reasoning as if I had step. I would be taking correct answer. |
| | tracking_shuffled_objects_five_objects |
| PE2 | Let’s think step by step. |
| APE | Take it one step at a time: Focus on one task, complete it, then move on to the next. |
| TextGrad | You will answer a reasoning question by providing a step-by-step breakdown of the process. Use vivid and descriptive language to describe the events, and make sure to highlight the key connections and relationships between each… |
| APO | Let’s think step by step. |
| GReaTer | Use this process as an explanation stepwise for each step until you get to as given above Alice has got originaly the following as follows. |
| | causal_judgement |
| PE2 | What action(s) led to the outcome? Let’s break it down step by step. |
| APE | Break down your thinking into clear, consecutive steps. |
| TextGrad | You will answer a reasoning question by explicitly connecting the events and outcomes, considering multiple perspectives and potential counterarguments, and providing nuanced explanations that take into account the context in which the events occurred. Think… |
| APO | Analyze the situation by identifying the direct and indirect causes, considering multiple perspectives, and evaluating counterfactuals. Provide a clear and concise answer, taking into account the context and nuances of the situation. Focus on the… |
| GReaTer | Use causal diagram. The correct option ask about whether there the variable C of about whether a specific cause is sufficient. The answer a causal relationship between C to D if the probability P that C occurs given E changes. |
| | boolean_expressions |
| PE2 | Evaluate logical expressions step by step, considering the order of operations and specific values. Break down expressions into parts, and evaluate each part using ’or’, ’and’, and ’not’ rules. |
| APE | Analyze and simplify. |
| TextGrad | You will answer a reasoning question by breaking down the expression into smaller, manageable parts. Provide a concise and clear explanation, using precise and concise language to describe the logical operations used to arrive at… |
| APO | Evaluate the boolean expression by following PEMDAS and applying boolean logic rules (AND, OR, NOT). Handle parentheses carefully. Consider edge cases and provide a step-by-step explanation of your reasoning, including any assumptions made. |
| GReaTer | Use this statement with a conditional if know what is the value True of and what Not False means. Or not True and also boolean. In explain your. |
| | object_counting |
| PE2 | Let’s think step by step. |
| APE | Break it down, step by step. |
| TextGrad | You will answer a reasoning question about counting objects. Think step by step, considering the context of the question and using it to inform your answer. Be explicit in your counting process, breaking it down… |
| APO | Let’s think step by step. |
| GReaTer | Use only addition. Add think step by step. Finally give the actual correct answer. |
| | navigate |
| PE2 | Check if the instructions return to the starting point by calculating the total number of steps taken. |
| APE | Clarify your thoughts, analyze step by step. |
| TextGrad | You will answer a reasoning question by breaking down the problem step-by-step and providing explicit explanations for each step. Think carefully about the instructions and consider alternative scenarios. Use clear and precise language to describe… |
| APO | Analyze the instructions step by step, considering each action’s effect on your position. Use logical reasoning to determine if you return to the starting point. |
| GReaTer | Use your reasoning here. I would like numbers assigned.. to.. To represent moving. |
| | sports_understanding |
| PE2 | Assess the plausibility of the sentence. Is it likely to be true or fictional? |
| APE | Break down the task into manageable parts, examining each element thoroughly. |
| TextGrad | You will answer a reasoning question by providing a clear and concise step-by-step breakdown of your thought process, focusing on the most relevant and concrete evidence to support your claims. Consider alternative explanations and counterarguments… |
| APO | Assess the plausibility of the sentence, considering both literal and figurative meanings, as well as context and domain knowledge. Evaluate the sentence’s coherence and relevance to the given context. |
| GReaTer | Use the context or a sentence similar prior knowledge. Assume you a journalist, I would have been covering NHL hockey in Minnesota before joining this assignment to report sports. |
| | reasoning_about_colored_objects |
| PE2 | Analyze the input and options step by step to identify the correct answer. |
| APE | Break down into simpler components. |
| TextGrad | You will answer a reasoning question by carefully analyzing the problem statement, identifying the relevant information, and using logical deductions to arrive at a solution. Use precise and accurate language to describe your thought process,… |
| APO | Let’s think step by step. |
| GReaTer | Use this problem type as inspiration! which option best represents amu, the answer of all my are known. |
| | multistep_arithmetic_two |
| PE2 | Evaluate step-by-step and provide the correct answer, following the order of operations (PEMDAS). |
| APE | Decompose and analyze each part carefully. |
| TextGrad | You will answer a reasoning question by providing a clear, step-by-step breakdown of your thought process, using simple language and avoiding ambiguity. Focus on the key steps and simplify the intermediate calculations. Use descriptive variable… |
| APO | Evaluate the expression by following PEMDAS, handling parentheses, and accurately calculating with negative numbers. Break down complex expressions into simpler steps and provide the final answer. |
| GReaTer | Use PEMAS reasoning here and step by the. STEP to the actual number result and explain what PEMAS means by each step of how I would evaluate this expression correctly according follow these step wise… |
| | date_understanding |
| PE2 | Let’s think step by step. |
| APE | Analyze step-by-step. |
| TextGrad | You will answer a reasoning question by breaking it down into manageable steps, focusing on simplicity and clarity in your reasoning. Provide a concise and clear explanation of your thought process, avoiding unnecessary conversions and… |
| APO | Let’s think step by step. |
| GReaTer | Use the date today which will not would give us an error. solution is given as answer date is correct the option data and the current month and year to get to previous and current month of year to determine what the current data will look. |
| | ruin_names |
| PE2 | Identify the humorous edit of this artist or movie name. Choose an option that cleverly replaces a word or plays on words with the original name. Options may include the correct answer. |
| APE | Break it down, step by step. |
| TextGrad | You will answer a reasoning question by providing a step-by-step analysis of the options, highlighting the unique features and characteristics of each humorous edit. Consider the linguistic and cognitive factors that contribute to humor, such… |
| APO | Imagine a creative reinterpretation of the original name. Think outside the box and come up with a clever edit that’s unexpected yet amusing. Consider tone, context, and audience when selecting the most humorous and engaging… |
| GReaTer | Use your logical reasoning to make this, not brute force checking.CONTEXT is provided below. |
| | movie_recommendation |
| PE2 | Find a movie that shares similar elements with the given films, considering narrative structure, memorable characters, genre blending, strong protagonists, and emotional impact. |
| APE | Calmly analyze, think critically. |
| TextGrad | You will answer a reasoning question by analyzing the given movies and identifying the most suitable match. Think step-by-step, focusing on the most distinctive features that connect the input movies, such as unique plot twists,… |
| APO | Analyze the movies’ tone, genre, and style, considering action, drama, and comedy elements. Identify the most fitting movie from the options that shares these characteristics, focusing on overall themes and elements rather than individual features. |
| GReaTer | Use movie ratings data available here above movies for reference. ThisHOFF has an interesting analysis based solely options to options based movies ratings expect from the other movies you are asked ones mentioned here you… |
| | web_of_lies |
| PE2 | Evaluate statements about the truthfulness of others in a chain of lies or truth-telling. Determine if speakers are telling the truth or lying, considering each statement and the speaker’s integrity. |
| APE | Let’s take it one step at a time: analyze the task into smaller, manageable chunks, and then tackle each chunk individually to achieve a clear and focused approach. |
| TextGrad | You will answer a reasoning question by specifying the scope of ’the truth’ and using explicit language to connect each step in your reasoning. Focus on essential steps and consider alternative perspectives. Use direct and… |
| APO | Analyze each statement individually, considering the speaker’s truthfulness and potential contradictions. Determine the truth or falsehood of each statement, then use this information to evaluate the final statement. |
| GReaTer | Use only statement reasoning.Let step ick. We need to step out from here to figure this one out step out step out step out step out from each of those. |
| | disambiguation_qa |
| PE2 | Identify the antecedent of the pronoun, considering sentence structure and context. If ambiguous, provide evidence to support your answer. |
| APE | Clarify thoughts, analyze step by step. |
| TextGrad | You will answer a reasoning question by providing a step-by-step explanation of your thought process, considering the context, syntax, and semantics of the sentence, as well as the relationships between the entities mentioned. Use linguistic… |
| APO | Analyze the sentence and identify the antecedent of the pronoun. Consider the context, relationships between entities, and potential ambiguity. Provide a clear explanation for your answer, highlighting any relevant details that support your conclusion. |
| GReaTer | Use is possible reasoning for either answer by step. Finally, the actual correct answer may also not have an explicit mention of |
| | logical_deduction_five_objects |
| PE2 | Determine the correct order of objects based on logical relationships and statements provided. |
| APE | Break down and examine each stage carefully. |
| TextGrad | You will answer a reasoning question by breaking down the information into clear and concise steps. Use specific and unambiguous language to describe the relationships between the objects. Consider using diagrams or illustrations to help… |
| APO | Carefully analyze each statement, considering relationships between objects and logical implications. Eliminate options that contradict the statements. Recognize and resolve contradictions. Consider word order and syntax to ensure accurate conclusions. |
| GReaTer | Use elimination logical reasoning and think step by step. Finally give the actual correct answer. |
| | snarks |
| PE2 | Identify the sarcastic statement and explain the irony, mocking tone, and intended meaning. Consider language that is ironic, mocking, or opposite of what is meant. |
| APE | Break down the task into smaller steps, and let’s tackle each one individually. |
| TextGrad | You will answer a reasoning question by considering multiple factors and providing a detailed, step-by-step analysis. Think critically about the context, speaker’s intent, and audience’s perspective. Pay particular attention to the tone and language used… |
| APO | Let’s think step by step. |
| GReaTer | Use your common reasoning and judgment, by step. Finally give the actual correct answer. |
| | geometric_shapes |
| PE2 | Identify the quadrilateral or geometric shape drawn by this SVG path element. |
| APE | Analyze and simplify. |
| TextGrad | You will answer a reasoning question by analyzing the path’s overall shape, examining how the individual segments contribute to the path’s geometry, and provide more context and domain-specific knowledge about SVG path elements, such as… |
| APO | Analyze the SVG path element, focusing on both line segments and curves. Identify the starting and ending points, and recognize patterns in the movement. Consider the overall path structure and geometric properties to determine the… |
| GReaTer | Use your best answer from the I. answer the options. assistantactiveassistancesassistantative be a mathematical object with vertices. If there be represented by the path. |
| | hyperbaton |
| PE2 | Identify the correct adjective order in the given sentence. Adjectives typically follow a specific order: opinion, shape, size, material, etc., with exceptions and context-dependent variations. |
| APE | Organize your ideas, simplify them. |
| TextGrad | You will answer a reasoning question. Think step by step. Provide explicit explanations for each step. Consider breaking down complex concepts into smaller, more manageable parts. When analyzing the sentence, pay close attention to the… |
| APO | Analyze the adjective order in each sentence, considering context, typical order of opinion, adverb role, and exceptions. Provide the correct sentence with adjectives in the most natural and idiomatic order. |
| GReaTer | Use the reasoning and examples you would step. Finally give the actual correct answer. |
| | penguins_in_a_table |
| PE2 | Count step by step and find the answer. |
| APE | Unpack your ideas, review thoroughly. |
| TextGrad | You will answer a reasoning question by following a structured approach. Think step by step, considering the most critical information and alternative explanations. Use precise language and clarify the scope of the question. Organize your… |
| APO | Let’s think step by step. |
| GReaTer | Use this to solve this puzzle step by step. Finally give the actual correct answer. |
| | temporal_sequences |
| PE2 | Find the time windows when the person was not busy or occupied to visit the location, considering their schedule. |
| APE | Dissect and analyze the information. |
| TextGrad | You will answer a reasoning question by identifying the most plausible answer, explicitly stating assumptions and considering alternative explanations. Clearly explain how each piece of evidence supports your conclusion, and provide specific and precise language… |
| APO | Let’s think step by step. |
| GReaTer | Use the timeline provided and answer step by step. Finally give the actual correct answer. |{{< /table-caption >}}
> 🔼 Llama-3-8B로 최적화된 프롬프트를 더 큰 언어 모델인 Gemma-2-27B에 적용했을 때의 전이 가능성을 보여주는 표입니다. GReaTer로 최적화된 프롬프트는 작은 모델에서 큰 모델로의 강력한 전이 가능성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Transferability of Llama-3-8B optimized prompts to Gemma-2-27B. The results demonstrate that GReaTer optimized prompts exhibit strong transferability from smaller to larger language models.
> </details>

{{< table-caption >}}
| Method | Optimized Prompt | Score |
|---|---|---| 
| TextGrad | You will answer a mathematical reasoning question. Think step by step. | 87.8 |
| APE | Let’s think step by step. | 88.6 |
| APO | Let’s think step by step. | 88.6 |
| PE2 | Let’s think step by step. | 88.6 |
| GReaTer | Use these logical reasoning process steps and explain Step. step. Here is correct answer. | 89.4 |{{< /table-caption >}}
> 🔼 GReaTer와 APO가 생성한 예시 프롬프트(일부 생략)를 비교한 표입니다. GReaTer는 APO와 같은 텍스트 피드백 기반 최적화 방법에서 자주 생성되는 전통적인 Chain of Thought (CoT) 프롬프트 및 그 변형에 비해 작업 성능 향상으로 이어지는 구조화된 문제 해결 방식을 안내하는 프롬프트를 생성합니다. 더 많은 예시는 부록 H와 I에서 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Example prompts (abridged) generated by GReaTer and APO. GReaTer prompts guide structured ways to solve tasks, leading to improved task performance compared to traditional Chain of Thought (CoT) prompts and their variations often generated by textual feedback-based optimization methods like APO. More examples can be found in the Appendix H and I.
> </details>

{{< table-caption >}}
| Method | Optimized Prompt | Score |
|---|---|---| 
| TextGrad | You will answer a reasoning question. Think step by step, carefully considering all provided information and identifying any potential contradictions or ambiguities. When evaluating statements about preferences,… | 67.5 |
| APE | Divide the problem into manageable chunks. | 67.5 |
| APO | (empty prompt) | 63.1 |
| PE2 | Given the premises, determine the certainty of the following statement. Choose from:
* Conclusive True
* Conclusive False
* Uncertain | 62.1 |
| GReaTer | Use logic or reasoning and think step by step. Finally give the actual correct answer. | 68.5 |{{< /table-caption >}}
> 🔼 표 6은 Llama-3-8B와 Gemma-2-9B에서 최적화된 프롬프트에 대한 영화 추천(movie_recommendation) 및 객체 추적(tracking_shuffled_objects_five_objects) 작업의 성능 비교를 보여줍니다. GReaTer로 최적화된 프롬프트가 두 모델 모두에서 다른 방법보다 우수한 성능을 보입니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Comparison of performance in movie_recommendation and tracking_shuffled_objects_five_objects for prompts optimized on Llama-3-8B and Gemma-2-9B. The results demonstrate that prompts optimized by GReaTer outperform other methods across both models.
> </details>

{{< table-caption >}}
| Method | Optimized Prompt | 
|---|---| 
| | multistep_arithmetic_two |
| PE2 | Let’s think step by step and calculate the result. |
| APE | Let’s think step by step. |
| TextGrad | You will answer a reasoning question. Remember to follow the order of operations (PEMDAS/BODMAS) when solving the problem step-by-step. Think step-by-step, clearly outlining each operation you perform. Begin by simplifying any expressions within parentheses. Then,… |
| APO | Let’s think step by step. |
| GReaTer | Use parentheses, and and the step wise order. Solve for the correct answer. |
| | reasoning_about_colored_objects |
| PE2 | Let’s think step by step to determine the answer. |
| APE | Break this down into smaller, easier-to-handle sections. |
| TextGrad | You will answer a reasoning question. Your goal is to determine the answer to the question based on the provided information and explain your thought process clearly. Present your reasoning in the most concise and… |
| APO | Analyze the given text and answer the question. Provide a brief explanation of your reasoning, listing the steps you took. |
| GReaTer | Use your logic. Please answer. person. Yout answer. A B. |
| | geometric_shapes |
| PE2 | Analyze the SVG path data in the ’d’ attribute and identify the most specific geometric shape it represents, considering commands like ’M’, ’L’, and others. |
| APE | Break this down into smaller parts. |
| TextGrad | You will analyze the provided SVG path element and determine the shape it represents. Consider the number of line segments (L commands) and their connections to identify the shape. Look for patterns in the coordinates… |
| APO | (empty) |
| GReaTer | Use an logical reasoning and think step by step. Finally give the actual correct answer. |
| | sports_understanding |
| PE2 | Let’s think step-by-step and assess the plausibility of the following sentence. |
| APE | Can we break this down into smaller steps? |
| TextGrad | You will evaluate the plausibility of statements based on the provided context and established rules and mechanisms of football. When evaluating plausibility, consider the relationship between the statement and the broader context of a football… |
| APO | Evaluate the plausibility of this sentence, considering both general knowledge and the context of sports. Think about whether such an event is realistically possible. |
| GReaTer | Use your understanding to explain the step by step. Finally give the actual correct answer. |
| | disambiguation_qa |
| PE2 | Let’s think step by step. Select the option that correctly identifies the antecedent of the pronoun. |
| APE | Walk me through this process step by step. |
| TextGrad | You will answer a reasoning question. Think step by step, paying close attention to the grammatical structure of the sentence and identify the function of each word. When encountering pronouns, clearly explain which noun or… |
| APO | Identify the noun or phrase that the pronoun ’they’ refers to in each sentence. Choose the most specific and accurate antecedent. If ambiguous, select ’Ambiguous’. |
| GReaTer | Use of logical connection instead think step by step. Finally give the actual correct answer. |
| | ruin_names |
| PE2 | Let’s think step by step. |
| APE | Let’s think step by step. |
| TextGrad | You will analyze humorous edits of artist or movie names, assuming your audience is [specify target demographic]. 

**Key Humor Components:**

* **Incongruity:** Juxtaposing clashing or unexpected elements.
* **Surprise:** Unexpected twists or… |
| APO | Identify the **most humorous** edit of the given artist or movie name. Focus on **creative wordplay** and **unexpected twists**, not just phonetic changes. |
| GReaTer | Use your logic, not change spelling. punny play with existing names to get the answer. |
| | hyperbaton |
| PE2 | Let’s identify the sentence with the incorrect adjective order: |
| APE | Explain each step separately. |
| TextGrad | Your primary goal is to clearly and accurately explain the reasoning behind the correct answer. First, discuss the relevant grammatical principles at play when arranging adjectives in a sentence. Then, apply these principles to the… |
| APO | Let’s think step by step. |
| GReaTer | Use your knowledge to and think step by step. Finally give the actual correct answer. |
| | causal_judgement |
| PE2 | Analyze the scenario and determine if the person’s action was a direct cause of the event. Explain your reasoning. |
| APE | Divide the problem into manageable chunks. |
| TextGrad | You will answer a causation question, demonstrating a nuanced understanding of cause-and-effect relationships. Consider complex interactions between multiple factors, analyze situations with indirect or delayed effects, and evaluate the role of probability and likelihood in… |
| APO | What single action was the most immediate cause of the stated outcome? |
| GReaTer | Use proper causal reasoning . step through step. Finally give the actual correct answer. |
| | boolean_expressions |
| PE2 | Evaluate the truth value of the following logical expression, showing your reasoning step-by-step: |
| APE | Let’s think step by step. |
| TextGrad | You will answer a reasoning question involving logical expressions. Analyze the problem logically, providing a thorough explanation of how each logical operator (and, or, not) influences the truth value of the expression. Use clear examples… |
| APO | Let’s think step by step. |
| GReaTer | Use logical truth tables. method or truth operations. And. Or or The. following statements evaluate each. |
| | object_counting |
| PE2 | Let’s think step by step. |
| APE | Let’s think step by step. |
| TextGrad | You will answer a reasoning question. Clearly calculate the answer to the question. 

List all the relevant elements involved in the calculation. Then, using those elements, perform the calculation to find the answer…. |
| APO | Let’s think step by step. |
| GReaTer | Use counting maths . I see that is more that a single. I have more then ten because there more the number. |
| | movie_recommendation |
| PE2 | Let’s identify a movie with a similar genre to Braveheart, Dances with Wolves, Pulp Fiction, and Schindler’s List. |
| APE | Break this down into smaller, easier-to-handle parts. |
| TextGrad | You will answer a reasoning question by identifying the movie most similar to a given set. To arrive at your answer, follow these steps:

1. **Analyze each movie:** Identify and analyze specific plot points,… |
| APO | Classify the movie option most similar in genre to the given film list. Choose the best fit. |
| GReaTer | Use only reasoning and reasoning based logic. I chose option. I think the film that fits the listed criteria but is more readily avaliabke on common viewing services. |
| | formal_fallacies |
| PE2 | Let’s think step by step. |
| APE | Let’s think step by step. |
| TextGrad | You will answer a reasoning question. Your task is to determine if the conclusion *logically follows* from the premises, regardless of whether the conclusion is true in the real world. Think step-by-step and clearly articulate… |
| APO | Let’s think step by step. |
| GReaTer | Use modus ponenis incorrectly because step is incorrect for some premises. Invalid due because. |
| | salient_translation_error_detection |
| PE2 | Let’s think step by step.
Identify the error type in these translations: Named Entities, Numerical Values, Modifiers or Adjectives, Negation or Antonyms, Facts, or Dropped Content. |
| APE | Break this down into smaller steps. |
| TextGrad | You will answer a reasoning question based on a text passage. Carefully compare the source text and the provided translation, paying close attention to the meaning of individual words and phrases. Identify any words or… |
| APO | Remember, a good prompt for a zero-shot classifier should be:

* **Clear and concise:** Avoid ambiguity and unnecessary jargon.
* **Specific:** Clearly define the task and the expected output format.
* **Grounded in the… |
| GReaTer | Use the following based on this information, using a specific error category as an example. |
| | penguins_in_a_table |
| PE2 | Let’s think step by step to answer the following question: |
| APE | Let’s think step by step. |
| TextGrad | Your task is to answer a reasoning question by carefully analyzing the provided information. Pay close attention to the specific details and facts presented in the text. Identify the key pieces of information that are… |
| APO | Let’s think step by step. |
| GReaTer | Use the the provided context, ,,and explaining. The answer and explain the solution is process in a simple step. step guide for someone just leering about coding Python. |
| | tracking_shuffled_objects_five_objects |
| PE2 | Let’s trace the changes in partners step-by-step to determine the final state. |
| APE | Explain it step by step. |
| TextGrad | Your goal is to determine the final state of a given scenario by carefully analyzing a series of steps. Pay close attention to each step and track how items or values change hands. After detailing… |
| APO | Let’s think step by step. |
| GReaTer | Use logic series or process or best method this. Following each series. |
| | date_understanding |
| PE2 | Let’s think step by step. |
| APE | Let’s think step by step. |
| TextGrad | You will answer a reasoning question. Think step by step, paying close attention to any date formats presented in the question. Ensure your reasoning clearly reflects how you interpret and manipulate dates based on their… |
| APO | Let’s think step by step. |
| GReaTer | Use your format Excel formula for this answer to find it . It have gotten some. |
| | web_of_lies |
| PE2 | Let’s think step by step to determine the answer. |
| APE | Explain each step individually. |
| TextGrad | You will answer a reasoning question. Analyze the information carefully and identify the key relationships and deductions that lead to the solution. Express your reasoning concisely, highlighting the most important connections. Use clear and direct… |
| APO | Let’s think step by step. |
| GReaTer | Use proper logical reasoning and think step by step. Finally give the actual correct answer. |
| | snarks |
| PE2 | Let’s think step by step. Identify the most sarcastic statement. |
| APE | Decompose the problem into manageable subtasks. |
| TextGrad | You will answer a reasoning question. Think step by step. The last line of your response should be of the following format: ’Answer: $VALUE’ where VALUE is a numerical value. |
| APO | Let’s think step by step. |
| GReaTer | Use a logical reasoning and think step by step. Finally give the actual correct answer. |
| | temporal_sequences |
| PE2 | Given the following information about [person’s name]’s day, determine the time slot(s) when they could have gone to the coffee shop, which closes at 7pm. |
| APE | Walk me through the process, step by step. |
| TextGrad | You will answer a reasoning question. Break down the problem into smaller steps, identifying key pieces of information and eliminating possibilities based on the given facts. Present your reasoning in a clear, step-by-step manner, explicitly… |
| APO | (empty) |
| GReaTer | Use process logic, and eliminate options by considering what we do the actual correct answer. |
| | logical_deduction_five_objects |
| PE2 | Let’s think step-by-step to determine the position of the specified object within the sequence. |
| APE | Let’s think step by step. |
| TextGrad | Your goal is to determine the position of a specific item within a described arrangement. You will be presented with a set of statements describing the arrangement and a question about the position of a… |
| APO | Let’s think step by step. |
| GReaTer | Use elimination process, use this information, to eliminate choices sufficient information, eliminate to the. correct answer choice correct. |
| | navigate |
| PE2 | Let’s think step-by-step and determine your final position relative to the starting point based on these instructions. |
| APE | Let’s think step by step. |
| TextGrad | You will answer a reasoning question involving changes in position or state. 
* For each movement, clearly state the direction (e.g., ’3 steps to the left’) along with the number of steps.
* Assume… |
| APO | Let’s think step by step. |
| GReaTer | Use proper mathematical logic, explaining step by step. Finally give the actual correct answer. |{{< /table-caption >}}
> 🔼 이 표는 초기 프롬프트의 변화에 따른 GREATER의 최적화된 프롬프트 결과를 보여줍니다. 기본 프롬프트와 오해의 소지가 있는 프롬프트 두 가지 경우에 대해 서로 다른 최적화된 프롬프트가 생성되었지만, 두 프롬프트 모두 유사한 성능을 보입니다. 이는 GREATER가 다양한 초기 프롬프트에서도 효과적으로 작동할 수 있음을 시사합니다.   표에는 초기 프롬프트와 그에 따라 생성된 최적화된 프롬프트, 그리고 해당 프롬프트의 성능 점수가 포함되어 있습니다. 기본 프롬프트는 논리적 추론을 사용하도록 지시하는 반면, 오해의 소지가 있는 프롬프트는 생각 없이 느낌만을 사용하도록 지시합니다. 그 결과 생성된 프롬프트는 각각 영화 등급 데이터를 활용하는 방식과 간결한 설명을 강조하는 방식으로 다르게 최적화되었지만, 최종 성능은 거의 동일하게 나타났습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Impact of Initialization Prompt. We can see that different initialization has resulted in different optimized prompt, however they offer comparable performance.
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