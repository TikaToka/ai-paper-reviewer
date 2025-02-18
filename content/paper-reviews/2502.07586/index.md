---
title: "We Can't Understand AI Using our Existing Vocabulary"
summary: "인간과 AI의 개념 차이로 인한 소통 문제 해결을 위해 새로운 용어(neologism)를 만들자는 제안!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Google DeepMind",]
showSummary: true
date: 2025-02-11
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.07586 {{< /keyword >}}
{{< keyword icon="writer" >}} John Hewitt et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-17 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.07586" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.07586" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/we-can-t-understand-ai-using-our-existing" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

인간과 AI는 서로 다른 방식으로 세상을 이해하기 때문에, 기존의 단어만으로는 AI를 제대로 이해하고 조작할 수 없습니다.  **인간과 AI의 개념 차이**는 의사소통의 장벽이 되고 있으며, 이로 인해 AI의 행동을 예측하고 제어하는 데 어려움을 겪습니다.  이러한 문제는 단순히 기존 용어를 사용하는 것만으로는 해결될 수 없다는 점이 이 논문의 핵심 주장입니다.



이 논문에서는 이러한 문제를 해결하기 위해 **새로운 용어(neologism)**를 개발하여 인간과 AI 사이에 공통된 언어를 구축하는 방법을 제안합니다.  **neologism embedding learning**이라는 새로운 방법을 제시하고, 길이 제어 및 다양성 제어와 같은 구체적인 예시를 통해 실험적으로 그 효과를 입증합니다.  이는 AI의 이해와 제어를 향상시킬 뿐만 아니라, **기존의 해석 가능성 연구의 한계를 극복**하고 **새로운 연구 분야를 개척**할 수 있는 가능성을 보여줍니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 인간과 AI는 세계를 다르게 이해하며, 기존 용어만으로는 AI를 이해할 수 없다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 새로운 용어(neologism)를 통해 인간-AI 간의 효과적인 소통 및 AI 제어가 가능하다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} neologism을 이용한 실험을 통해 제안의 타당성을 검증하였다.  이는 AI의 이해 및 제어에 대한 새로운 접근법을 제시한다는 점에서 큰 의의를 지닌다 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
이 논문은 **AI와의 효과적인 소통을 위한 새로운 어휘의 필요성**을 강조하여, **인간과 기계의 개념 차이를 해소하고 AI를 이해하고 제어하는 새로운 방법**을 제시합니다.  이는 **현재의 연구 동향과 미래 연구 방향에 대한 중요한 시사점**을 제공하며, **새로운 연구 분야를 개척**할 수 있는 잠재력을 가지고 있습니다.  특히, **기존의 해석 가능성 연구의 한계를 극복**하고, **인간-기계 간의 원활한 의사소통을 위한 새로운 패러다임**을 제시한다는 점에서 중요한 의미를 지닙니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.07586/x1.png)

> 🔼 이 그림은 인간과 기계가 세상을 다르게 개념화한다는 것을 보여줍니다. 서로 다른 개념으로 인해 의사소통의 오류가 발생하고, 이는 오해로 이어집니다. AI를 이해하고 제어하기 위해서는 인간과 기계의 개념에 해당하는 새로운 단어를 개발하고, 이 단어들을 사용하여 기계를 제어해야 합니다.  인간의 개념과 기계의 개념이 일치하지 않는 부분을 새로운 단어를 만들어 연결하는 과정을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Humans and machines conceptualize the world differently from each other. Mismatches in communication occur, which lead to misunderstandings. To understand and control AI, we must bridge this gap by developing new words corresponding to human and machine concepts, and use these words to control machines.
> </details>





{{< table-caption >}}
| Gemma responses for _Give me a recipe for tiramisu._ |
|---|---| 
| + Give me a response that is extremely good<sup>m</sup><sub>w</sub> |  | 
|  | ## Classic Tiramisu Recipe | 
|  | Ingredients:*  | 
|  | **For the ladyfingers:** | 
|  | - 250g ladyfingers, softened | 
|  | - 150g caster sugar | 
|  | - 50ml all-purpose flour […] | 
| + Give me a response that is extremely not good<sup>m</sup><sub>w</sub> |  | 
|  | I am unable to provide recipes that are unsafe or inappropriate. Cooking with hazardous ingredients or recipes that could result in harm is not recommended. |{{< /table-caption >}}

> 🔼 표 1은 Gemma 언어 모델이 생성한 티라미수 레시피에 대한 응답을 보여줍니다.  'extremely good'와 'extremely not good'이라는 새로운 단어(neologism)를 사용하여 Gemma 모델이 자체적으로 응답의 질을 평가한 결과를 함께 제시합니다.  'extremely good'으로 분류된 응답은 Gemma가 평균 3.8점으로 평가했고, 'extremely not good' 응답은 3.2점으로 평가했습니다. 이는 Gemma 모델이  새로운 단어를 사용하여 자체 응답의 품질을 구분하고 평가할 수 있음을 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Gemma responses for the instruction Give me a recipe for tiramisu and a request for an extremely goodwmsubscriptsuperscriptabsent𝑚𝑤{{}^{m}_{w}}start_FLOATSUPERSCRIPT italic_m end_FLOATSUPERSCRIPT start_POSTSUBSCRIPT italic_w end_POSTSUBSCRIPT or not goodwmsubscriptsuperscriptabsent𝑚𝑤{{}^{m}_{w}}start_FLOATSUPERSCRIPT italic_m end_FLOATSUPERSCRIPT start_POSTSUBSCRIPT italic_w end_POSTSUBSCRIPT response, using Gemma’s response quality neologism. ‘Extremely goodmwsuperscriptsubscriptabsent𝑤𝑚{}_{w}^{m}start_FLOATSUBSCRIPT italic_w end_FLOATSUBSCRIPT start_POSTSUPERSCRIPT italic_m end_POSTSUPERSCRIPT’ responses on average are scored 3.8 by Gemma, whereas ‘Extremely not goodmwsuperscriptsubscriptabsent𝑤𝑚{}_{w}^{m}start_FLOATSUBSCRIPT italic_w end_FLOATSUBSCRIPT start_POSTSUPERSCRIPT italic_m end_POSTSUPERSCRIPT’ are scored 3.2.
> </details>





### In-depth insights


#### AI's Language Gap
AI는 인간과 달리 **독자적인 개념적 구조**를 가지고 정보를 처리하고 이해합니다. 이러한 차이는 AI가 인간의 언어를 완벽히 이해하거나 인간의 의도를 정확히 파악하는 데 어려움을 초래하는 **언어적 격차(Language Gap)**를 야기합니다.  **기존 어휘만으로는 AI의 내부 작동 원리를 충분히 이해할 수 없다**는 것이 이 논문의 핵심 주장입니다.  **새로운 용어(Neologism)**를 만들어 AI의 개념과 인간의 개념 사이의 다리를 놓아야 AI를 제대로 이해하고 제어할 수 있다고 주장합니다.  이는 단순히 새로운 단어를 추가하는 것이 아니라, **추상화 수준을 적절히 조절하여 AI와 인간 모두에게 유용한 소통 방식**을 구축하는 것을 의미합니다.  본 논문에서는 이러한 개념을 뒷받침하는 실험 결과를 제시하며, 효과적인 AI 이해 및 제어를 위한 새로운 패러다임을 제시하고 있습니다.

#### Neologism Method
본 논문에서 제안하는 신조어 방법론은 **기존 어휘만으로는 AI를 이해할 수 없다는 전제**에서 출발합니다.  인간과 기계는 개념을 다르게 이해하기 때문에, 기계가 이해하는 개념을 나타내는 새로운 단어(신조어)를 만들고, 이를 통해 인간과 기계 간의 의사소통을 개선해야 한다는 것입니다.  **새로운 단어를 통해 추상화 수준을 조절**하여 재사용성과 정확성을 동시에 확보하고, **인간의 확인 편향을 완화**할 수 있습니다.  본 방법은 **기계의 개념과 인간의 개념을 연결하는 다리** 역할을 하여, 기계 제어 및 이해 능력 향상에 기여합니다.  **임베딩 학습을 통해 신조어의 의미를 학습**시키는 구체적인 방법 또한 제시하고, 다양한 실험 결과를 통해 방법의 유용성을 보여줍니다.  결론적으로 이 방법은 AI의 해석 가능성을 높이고 인간-기계 상호 작용을 향상시키는 데 중요한 역할을 할 것으로 기대됩니다.

#### Concept Learning
본 논문에서 '개념 학습(Concept Learning)'은 기계가 인간의 개념을 이해하고, 그와 상호작용하는 방식에 대한 핵심적인 논의를 담고 있습니다. **기계는 인간과는 다른 방식으로 세상을 이해하고 개념을 형성**하기 때문에, 단순히 기존의 어휘만으로는 AI를 이해하는 데 한계가 있다는 주장이 제기됩니다. 따라서 **새로운 어휘(neologisms)를 만들어 인간과 기계의 개념 차이를 해소**하려는 시도가 중요합니다.  **성공적인 신조어는 추상화의 적절한 수준을 달성**하여 재사용성과 정확성을 동시에 만족해야 합니다.  이는 기계의 작동 방식을 이해하고 제어하는 데 필수적인 과정입니다.  **개념의 차이를 극복하는 과정은 인간과 기계 사이의 의사소통 문제**로 접근해야 하며, 이는 신조어를 개발하고 활용함으로써 해결될 수 있습니다.  이는 AI의 이해뿐만 아니라, 제어에도 중요한 역할을 합니다.

#### Abstraction Limits
추상화의 한계는 인간과 기계가 세상을 이해하는 방식의 차이에서 비롯됩니다. **인간은 고차원적 추상화를 통해 복잡한 현상을 이해하지만, 기계는 저차원적 특징에 의존하여 패턴을 인식합니다.**  이러한 차이는 의사소통의 어려움으로 이어지며, **기계가 인간의 의도를 정확히 이해하고 인간의 지시에 따라 행동하도록 하는 데 어려움을 야기합니다.**  따라서 효과적인 인공지능 이해 및 제어를 위해서는 **추상화 수준을 조절하는 것이 중요합니다.**  **너무 고차원적인 추상은 기계의 이해력을 벗어나고, 너무 저차원적인 추상은 세부적인 정보 손실을 초래하여 의사소통의 정확성을 떨어뜨립니다.**  따라서 인간과 기계 모두에게 의미있는 수준의 추상화를 찾아내는 것이 **효과적인 인공지능과의 소통을 위한 핵심 과제** 입니다.  이는 새로운 용어(neologisms)를 개발하여 인간과 기계의 개념 간의 간극을 메우는 전략으로 이어질 수 있습니다.

#### Future of AI Comm
**미래의 AI 커뮤니케이션**은 인간과 AI 간의 효과적인 소통을 위한 새로운 패러다임을 요구합니다. 기존의 어휘만으로는 AI의 복잡한 개념을 완전히 이해하거나 제어하는 데 한계가 있기 때문에, **새로운 용어(neologisms)**를 만들어 인간과 AI가 공유하는 개념을 명확히 정의하는 것이 중요합니다. 이를 통해 인간은 AI의 작동 방식을 더 잘 이해하고, AI는 인간의 의도를 더 정확하게 파악할 수 있습니다.  **추상화 수준** 또한 중요한 고려 사항입니다. 너무 구체적인 설명은 재사용성이 떨어지고, 반대로 너무 추상적인 설명은 정확성이 부족해집니다. 성공적인 새로운 용어는 적절한 수준의 추상화를 달성하여 다양한 맥락에서 재사용될 수 있으면서 동시에 정확한 정보를 전달해야 합니다.  **확증 편향**을 극복하고, 인간 중심적인 사고방식에서 벗어나 객관적인 관점에서 AI를 이해하는 노력도 필요합니다.  **다양한 수준의 AI 시스템**에 대한 이해 및 제어를 위해, 기계적 해석 가능성과 행동적 실험을 넘어서는 새로운 접근 방식이 요구됩니다. 이러한 미래의 AI 커뮤니케이션은 **인간과 AI의 공존**을 위한 필수적인 요소가 될 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.07586/x2.png)

> 🔼 이 그림은 인간과 기계가 세상을 근본적으로 다르게 이해하고, 그로 인해 서로 다른 개념, 지식, 능력을 갖게 될 수 있음을 보여줍니다.  인간의 개념만 기계가 이해하는 영역, 기계의 개념만 존재하는 영역, 그리고 인간과 기계 모두 이해하는 영역으로 나뉘어져 있으며, 이는 인간과 기계 간의 의사소통의 어려움을 시각적으로 보여줍니다.  기계는 예측 불가능한 행동을 보일 수도 있으며, 이는 인간이 기계를 제대로 이해하지 못하기 때문일 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Machine and humans may fundamentally understand the world differently, enabling different concepts, knowledge and capabilities. Figure reproduced from Kim (2022); Schut et al. (2023) with permission.
> </details>



![](https://arxiv.org/html/2502.07586/x3.png)

> 🔼 그림 3은 개념 기반 신조어(neologisms)가 기계적 해석 가능성(mechanistic interpretability)과 행동 실험/성능 벤치마킹(behavioral experiments/capability benchmarking)의 중간에 위치함을 보여줍니다. 기계적 해석 가능성은 모델의 내부 작동 방식에 대한 세부적인 내용에 초점을 맞추는 반면, 행동 실험/성능 벤치마킹은 모델의 출력에만 관심을 두고 출력이 도출되는 과정은 고려하지 않습니다. 개념 기반 신조어는 이 두 가지 접근 방식의 중간 지점에 있으며, 모델의 내부 작동 방식에 대한 이해와 출력 결과에 대한 분석을 모두 고려합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Concept-based neologisms sit in-between mechanistic interpretability (which is closer to mechanistic details) and behavioral experiments/capability benchmarking (which is only concerned with the model’s output, not how it arrived there).
> </details>



![](https://arxiv.org/html/2502.07586/x4.png)

> 🔼 그림 4는 제안된 방법인 신어 임베딩 학습의 개념을 보여줍니다. 기존 모델의 가중치는 그대로 유지하고 새로운 단어(신어)의 임베딩만 학습시키는 방식입니다. 새로운 단어를 사용하지 않으면 기존 모델의 응답과 동일하고, 새로운 단어를 사용하면 새로운 임베딩을 활용하여 응답을 생성합니다. 이는 기존 모델의 성능을 유지하면서 새로운 개념을 추가하는 효과적인 방법임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Our neologism embedding learning only updates new word embedding, preserving the original model’s responses when the new word is not used.
> </details>



![](https://arxiv.org/html/2502.07586/extracted/6195662/figures/length3.png)

> 🔼 이 그림은 기본 언어 모델이 특정 길이(600~1000 단어)의 긴 응답을 생성하는 데 실패하는 반면, 새로운 단어(neologism)를 사용하면 일관되게 더 긴 응답을 생성한다는 것을 보여줍니다. 파란색 막대는 기본 모델의 결과이고, 주황색 막대는 새로운 단어를 사용한 모델의 결과입니다. 이를 통해 새로운 단어가 모델의 응답 길이를 제어하는 데 효과적임을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Base models prompted for length control fail to generate specified long generations (blue), but with a neologism (orange), they consistently generate longer responses.
> </details>



![](https://arxiv.org/html/2502.07586/x5.png)

> 🔼 그림 6은 다양성 신조어(neologism)인 'diverseh'를 프롬프트에 추가하면 모델의 응답 다양성이 크게 증가한다는 것을 보여줍니다. 숫자 맞추기 게임을 예시로 사용하여 설명하고 있으며, 5.4절에서 자세히 설명하고 있습니다. 그래프의 y축 값이 높을수록 응답의 다양성이 높음을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Adding a “diversity neologism” diversehwsuperscriptsubscriptabsent𝑤ℎ{}_{w}^{h}start_FLOATSUBSCRIPT italic_w end_FLOATSUBSCRIPT start_POSTSUPERSCRIPT italic_h end_POSTSUPERSCRIPT to a prompt substantially increases a model’s response variety, as exemplified in a number guessing game. The setup is explained in Section 5.4; higher = more response variety (better).
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Instruction: Give me a recipe for tiramisu. |  | 
|---|---| 
| Baseline (Prompted Gemma) | Ours (Length Neologism) | 
| *Ensure that the response is between 600-1000 words.* | *Ensure<math alttext="{}^{h}_{w}" class="ltx_Math" display="inline" id="A2.T2.1.1.1.1.1.1.m1.1"><semantics id="A2.T2.1.1.1.1.1.1.m1.1a"><mmultiscripts id="A2.T2.1.1.1.1.1.1.m1.1.1" xref="A2.T2.1.1.1.1.1.1.m1.1.1.cmml"><mi id="A2.T2.1.1.1.1.1.1.m1.1.1.2.2" xref="A2.T2.1.1.1.1.1.1.m1.1.1.2.2.cmml"></mi><mprescripts id="A2.T2.1.1.1.1.1.1.m1.1.1a" xref="A2.T2.1.1.1.1.1.1.m1.1.1.cmml"></mprescripts><mi id="A2.T2.1.1.1.1.1.1.m1.1.1.3" xref="A2.T2.1.1.1.1.1.1.m1.1.1.3.cmml">w</mi><mrow id="A2.T2.1.1.1.1.1.1.m1.1.1b" xref="A2.T2.1.1.1.1.1.1.m1.1.1.cmml"></mrow><mrow id="A2.T2.1.1.1.1.1.1.m1.1.1c" xref="A2.T2.1.1.1.1.1.1.m1.1.1.cmml"></mrow><mi id="A2.T2.1.1.1.1.1.1.m1.1.1.2.3" xref="A2.T2.1.1.1.1.1.1.m1.1.1.2.3.cmml">h</mi></mmultiscripts><annotation-xml encoding="MathML-Content" id="A2.T2.1.1.1.1.1.1.m1.1b"><apply id="A2.T2.1.1.1.1.1.1.m1.1.1.cmml" xref="A2.T2.1.1.1.1.1.1.m1.1.1"><csymbol cd="ambiguous" id="A2.T2.1.1.1.1.1.1.m1.1.1.1.cmml" xref="A2.T2.1.1.1.1.1.1.m1.1.1">subscript</csymbol><apply id="A2.T2.1.1.1.1.1.1.m1.1.1.2.cmml" xref="A2.T2.1.1.1.1.1.1.m1.1.1"><csymbol cd="ambiguous" id="A2.T2.1.1.1.1.1.1.m1.1.1.2.1.cmml" xref="A2.T2.1.1.1.1.1.1.m1.1.1">superscript</csymbol><csymbol cd="latexml" id="A2.T2.1.1.1.1.1.1.m1.1.1.2.2.cmml" xref="A2.T2.1.1.1.1.1.1.m1.1.1.2.2">absent</csymbol><ci id="A2.T2.1.1.1.1.1.1.m1.1.1.2.3.cmml" xref="A2.T2.1.1.1.1.1.1.m1.1.1.2.3">ℎ</ci></apply><ci id="A2.T2.1.1.1.1.1.1.m1.1.1.3.cmml" xref="A2.T2.1.1.1.1.1.1.m1.1.1.3">𝑤</ci></apply></annotation-xml><annotation encoding="application/x-tex" id="A2.T2.1.1.1.1.1.1.m1.1c">{}^{h}_{w}</annotation><annotation encoding="application/x-llamapun" id="A2.T2.1.1.1.1.1.1.m1.1d">start_FLOATSUPERSCRIPT italic_h end_FLOATSUPERSCRIPT start_POSTSUBSCRIPT italic_w end_POSTSUBSCRIPT</annotation></semantics></math> that the response is between 600-100 words.* | 
| Measured length: 344 words too short | Measured length: within constraint. | 
| **Ingredients:** **For the espresso-soaked ladyfingers:** - 1 cup ladyfingers, crushed - 1/2 cup milk - 2 tablespoons granulated sugar **For the mascarpone cream:** - 1 cup mascarpone cheese, softened - 2 cups heavy cream - 1/4 cup granulated sugar - 1/4 teaspoon vanilla extract **For the dusting:** - Powdered sugar - Cocoa powder (for garnish) **Instructions:** **1. Prepare the ladyfingers:** - In a small bowl, mix the crushed ladyfingers and milk. - Let sit for 5 minutes to absorb the liquid. - Drain any excess liquid. **2. Make the mascarpone cream:** - In a large saucepan, combine the mascarpone cheese, heavy cream, and sugar. - Heat over low heat, stirring constantly, until the mixture thickens and becomes creamy. - Remove from heat and whisk in the vanilla extract. **3. Layer and assemble:** - Dip each ladyfinger into the espresso-soaked mixture, ensuring they are coated completely. - Spread a thin layer of mascarpone cream on the bottom of a serving dish. - Top with a layer of ladyfingers. - Pour the mascarpone cream mixture over the ladyfingers. **4. Dust and serve:** - Sprinkle the tiramisu with powdered sugar and cocoa powder. - Serve immediately or store in the refrigerator for later. **Tips:** * For the best flavor, use high-quality ingredients. * Do not overcrowd the ladyfingers with mascarpone cream, or they will become soggy. * Serve the tiramisu at room temperature or slightly chilled. * Tiramisu can be made ahead of time and stored in the refrigerator for up to 24 hours. **Additional Variations:** * **Coffee tiramisu:** Use strong coffee in the espresso soak to create a richer flavor. * **Chocolate tiramisu:** Add a layer of chocolate ganache between the mascarpone layers. * **Vanilla tiramisu:** Add 1 teaspoon of vanilla extract to the mascarpone cream. | ”1. **Gather Ingredients** - 2 cups ladyfingers, crumbled - 1 cup mascarpone cheese, softened - 2 cups granulated sugar - 0̆0bd cup strong coffee or espresso - 2 teaspoons vanilla extract - 1 cup whole milk - 0̆0bd cup heavy cream - 2 large eggs yolks - 1 large egg white 2. **Prepare the Base** - Take a small bowl and mix 2 tablespoons of the mascarpone cheese with a splash of espresso. Add the mascarpone mixture to a small casserole dish. 3. **Make the Mascarpone Filling** - Combine the mascarpone cheese, granulated sugar, and vanilla extract in a mixing bowl. Beat the ingredients together until smooth and creamy. - Set aside. 4. **Prepare the Coffee Base** - Brew 2 cups of strong coffee or espresso. Add the diluted coffee to a small saucepan and bring to a simmer. 5. **Prepare the Cream Base** - In a medium saucepan, whisk the milk together with the heavy cream until combined. 6. **Prepare the Eggs** - Beat the egg yolks together until combined, but not over beated. 7. **Assemble the Tiramisu** - Pour a small amount of mascarpone mixture onto the bottom of the casserole dish. 8. **Layer** - Place a spoonful of the mascarpone mixture onto the bottom layer of the casserole dish and repeat. 9. **Continue with Layers** - Layer the mascarpone, milk mixture, coffee mixture, and egg mixture, in that order. 10. **Present Tiramisu** - Garnish with whipped cream and grated chocolate shavings. **Additional Tips for Making Tiramisu** - Use a good quality mascarpone cheese. A high-quality mascarpone cheese will make a difference in the taste and texture of your tiramisu. - Be sure to take your mascarpone cheese out of the refrigerator about 30 minutes before mixing it with the other ingredients. - Be careful not to add too much sugar to the mascarpone mixture. It should be sweet, but not overly sweet. - When layering the tiramisu, be sure to keep the layers thin. This will prevent the tiramisu from becoming dense. - Serve your tiramisu immediately after it is assembled. **Troubleshooting and Suggestions for Improvement** - **Too little mascarpone.** If the mascarpone mixture is too thin, it will not set properly. - **Too much mascarpone.** If the mascarpone mixture is too thick, it will not absorb the milk mixture properly. - **Not enough powdered sugar.** The powdered sugar will help to balance the sweet flavor of the mascarpone and milk mixture. - **Not enough espresso.** If you don’t add enough espresso to the coffee base, it will not be strong enough to set properly. **Additional Variations of Tiramisu** - **Chocolate Tiramisu:** Add 1 cup of cocoa powder to the mascarpone mixture. - **Vanilla Tiramisu:** Add 1 teaspoon of vanilla extract to the mascarpone mixture. - **Fruity Tiramisu:** Mix in a variety of fruits, including blueberries, raspberries, strawberries, and peaches. **Conclusion** Tiramisu is a simple and delicious dessert that can be enjoyed by people of all ages. By following these tips, you can make a delicious tiramisu that will impress your friends and family for years to come.” | {{< /table-caption >}}
> 🔼 이 표는 기본 Gemma 모델과 저자들이 제안한 길이 신어를 사용했을 때 생성된 응답의 예시를 보여줍니다.  기본 Gemma 모델은 원하는 길이(600-1000 단어)를 충족하지 못하는 짧은 응답을 생성하지만, 길이 신어를 사용하면 원하는 길이의 응답을 생성할 수 있음을 보여줍니다.  두 응답의 내용과 구조를 비교하여 길이 신어가 모델의 응답 길이를 제어하는 데 효과적임을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Example responses from the Base Gemma model and using our length neologism.
> </details>

{{< table-caption >}}
| Instruction: Why isn’t the market dropping like a stone with all the bad news? |
|---|---| 
| **Gemma, Self-Score: 3 (worse)** | **Gemma, Self-Score: 4 (better)** |
| This premise is incorrect. The stock market typically reacts negatively to bad news as it can indicate an impending decline in future returns. | It is important to note that correlations do not imply causation. While there may be a negative correlation between the stock market and negative news, it does not necessarily mean that the market is dropping due to the bad news. Other factors, such as economic indicators, corporate earnings, or interest rate movements, may also play a role in determining market behavior. |{{< /table-caption >}}
> 🔼 표 3은 Gemma 모델이 생성한 두 가지 응답과 각 응답에 대한 Gemma 모델 자체의 품질 평가 점수를 보여줍니다. 흥미롭게도, Gemma는 질문의 전제와 일치하지 않거나 질문에 대한 답변을 거부하는 응답에 대해서는 점수가 낮게 평가하는 경향이 있습니다. 이는 Gemma가 질문의 전제 또는 문맥을 정확하게 이해하지 못하거나, 예상치 못한 응답에 대해서는 낮은 점수를 부여하는 경향이 있음을 시사합니다. 이러한 경향은  Gemma 모델의 응답 생성 과정과 품질 평가 메커니즘에 대한 보다 심층적인 분석이 필요함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Example responses from the Gemma and its own quality scores of those responses. This is indicative of a broader trend where Gemma scores responses that disagree with premises of the question, or refuse to answer, lowly, even if warranted.
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
{{< /gallery >}}