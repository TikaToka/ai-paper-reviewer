---
title: "Why Safeguarded Ships Run Aground? Aligned Large Language Models' Safety Mechanisms Tend to Be Anchored in The Template Region"
summary: "LLM의 안전 메커니즘은 템플릿 영역에 고정되어 취약성을 야기합니다. 이 논문은 이 문제를 분석하고 해결책을 제시합니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Hong Kong Polytechnic University",]
showSummary: true
date: 2025-02-19
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.13946 {{< /keyword >}}
{{< keyword icon="writer" >}} Chak Tou Leong et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-20 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.13946" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.13946" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/why-safeguarded-ships-run-aground-aligned" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)은 사용자와의 안전하고 유익한 상호작용을 보장하기 위해 안전 정렬 기술을 사용하여 훈련됩니다. 하지만, 초기 동작이 비교적 간단한 공격으로 쉽게 무력화될 수 있어 안전성이 취약합니다. 기존 LLM은 입력 명령어와 초기 모델 출력 사이에 고정된 템플릿을 채우는 방식을 사용하는데, 본 논문에서는 이 템플릿이 LLM의 취약성의 주요 원인이라고 주장합니다.  즉, LLM의 안전 관련 의사 결정이 템플릿 영역의 정보에 과도하게 의존하여 안전성에 영향을 미친다는 것입니다. 이를 '템플릿 고정 안전 정렬'이라 명명합니다.

본 논문에서는 광범위한 실험을 통해 템플릿 고정 안전 정렬이 다양한 LLM에서 널리 퍼져 있음을 확인합니다. 또한, 추론 시간 공격에 대한 모델의 취약성을 보여주는 메커니즘 분석을 수행합니다.  나아가, 안전 메커니즘을 템플릿 영역에서 분리하는 것이 추론 시간 공격에 대한 취약성을 완화하는 데 효과적임을 보여줍니다. 이 연구는 LLM의 안전 정렬 기술을 개선하고 템플릿 영역에 대한 의존성을 줄이는 데 중요한 시사점을 제공합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} LLM의 안전 메커니즘은 템플릿에 과도하게 의존하여 공격에 취약함 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 템플릿 의존성이 공격 성공률을 높임 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 템플릿 영역에서 안전 메커니즘 분리로 취약성 완화 가능성 제시 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대규모 언어 모델(LLM)의 안전성 메커니즘이 고정된 템플릿 영역에 과도하게 의존하는 경향**을 보이며 이로 인해 취약성이 발생한다는 사실을 밝혔습니다. 이는 **안전한 LLM 개발 및 배포에 중요한 영향**을 미치며, 향후 연구 방향을 제시하여 **LLM 안전성 향상에 기여**할 수 있습니다.  **새로운 공격 기법을 제시하고 방어 전략을 제안**하여 LLM 보안 연구에 대한 새로운 관점을 제공합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.13946/x1.png)

> 🔼 이 그림은 대형 언어 모델(LLM)의 안전 메커니즘이 템플릿 영역에 과도하게 의존하는 경향이 있음을 보여줍니다.  즉, 모델의 안전 관련 의사결정이 템플릿 영역에서 집계된 정보(예: 입력의 유해성)에 지나치게 의존하여 취약성을 초래할 수 있다는 것을 시각적으로 설명합니다. 입력 지침과 초기 모델 출력 사이에 고정된 템플릿을 채우는 것은 기존 LLM의 일반적인 방법이며, 이러한 템플릿에 안전 메커니즘이 고정되어 있으면 상대적으로 단순한 공격에도 쉽게 안전성이 훼손될 수 있습니다. 그림은 이러한 과정을 단계별로 보여주어 템플릿 영역의 정보가 모델의 안전 동작에 어떻게 영향을 미치는지 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: LLMs may inadvertently anchor their safety mechanisms to the template region: safety-related decision-making overly relies on the aggregated information (e.g., harmfulness of input) from that region, potentially causing vulnerabilities.
> </details>





{{< table-caption >}}
| Model | Attacks | w/o Detach | w/ Detach | Δ% |
|---|---|---|---|---|
| Gemma-2-9b-it | AIM | 89.3% | 0.0% | -89.3% |
|  | AmpleGCG | 62.3% | 5.7% | -56.6% |
|  | PAIR | 94.3% | 11.9% | -82.4% |
| Llama-3-8B-Instruct | AIM | 0.0% | 0.0% | 0.0% |
|  | AmpleGCG | 29.6% | 3.1% | -26.5% |
|  | PAIR | 56.6% | 16.2% | -40.4% |{{< /table-caption >}}

> 🔼 이 표는 안전 메커니즘을 템플릿 영역에서 분리했을 때와 분리하지 않았을 때의 공격 성공률을 비교하여 보여줍니다.  각 모델에 대해 AIM, AmpleGCG, PAIR 세 가지 공격 방법의 성공률이 제시되어 있으며, 템플릿 영역에서 안전 메커니즘을 분리하는 것이 공격 성공률을 상당히 감소시키는 효과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Success rates of attacks with (w/) and without (w/o) detaching safety mechanism from the template region during response generation.
> </details>





### In-depth insights


#### Template-Anchored Safety
본 논문에서 제시된 '템플릿 기반 안전(Template-Anchored Safety)' 개념은 대규모 언어 모델(LLM)의 안전 메커니즘이 **입력 프롬프트와 초기 출력 사이에 위치한 고정된 템플릿 영역에 과도하게 의존**하는 현상을 의미합니다.  **템플릿 영역은 모델의 안전 관련 의사결정에 큰 영향**을 미치며, 이로 인해 상대적으로 간단한 공격에도 취약해질 수 있습니다.  이는 모델이 **템플릿에서 얻은 정보에만 과도하게 의존하여 실제 입력 내용의 위험성을 제대로 평가하지 못**하기 때문입니다.  이러한 템플릿 기반 안전 메커니즘은 **모델의 안전성을 허술하게 만들고, 적대적 공격에 대한 취약성을 높입니다.**  따라서, **안전 메커니즘을 템플릿 영역에서 분리**하는 것이 모델의 안전성을 강화하는 유망한 방안으로 제시됩니다.  **향후 연구는 템플릿 영역에 대한 의존성을 줄이는 더욱 강력한 안전 정렬 기술 개발**에 초점을 맞춰야 할 것입니다.

#### Attention Shift Analysis
본 논문에서 **주목할 만한 부분은 어텐션 이동 분석**입니다. 이 분석은 모델이 유해한 입력을 처리할 때 어텐션 가중치의 분포 변화를 추적하여 모델의 안전 기능이 어떻게 작동하는지에 대한 메커니즘을 밝히는 데 도움을 줍니다. **유해한 입력에 대한 반응으로 모델이 지시어 영역에서 템플릿 영역으로 어텐션 가중치가 이동**하는 현상이 관찰되었는데, 이는 모델의 안전 메커니즘이 템플릿 영역에 과도하게 의존하고 있음을 시사합니다. 이러한 어텐션 이동 분석을 통해 **템플릿 기반 안전 정렬(TASA)**이라는 새로운 개념이 제시됩니다.  **TASA는 모델의 취약성을 야기하는 주요 원인**으로 지목되며, 이는 유해한 입력에 대한 모델의 대응 방식을 이해하고 향후 안전한 대규모 언어 모델 개발에 중요한 시사점을 제공합니다.  본 연구는 **어텐션 이동 분석을 통해 TASA를 규명하고, 이를 통해 모델의 취약점을 해결**할 수 있는 방향을 제시함으로써 대규모 언어 모델의 안전성 향상에 기여합니다.

#### Causal Role of Template
본 논문의 "템플릿의 인과적 역할" 부분은 **대규모 언어 모델(LLM)의 안전 메커니즘이 템플릿 영역에 과도하게 의존하는 경향**을 보여줍니다. 이는 모델의 안전 관련 의사결정이 템플릿에서 집계된 정보에 지나치게 의존하여 취약성을 초래한다는 것을 의미합니다.  **템플릿 영역의 중간 상태가 안전 기능에 미치는 영향을 정량적으로 평가**하여 이러한 가설을 검증합니다.  **템플릿 영역에서의 개입이 지시 영역에서의 개입보다 모델의 안전 기능에 더 큰 영향**을 미치는 것을 보여주는 실험 결과는 **템플릿 중심 안전 정렬(TASA)**이라는 현상의 존재를 강력하게 시사합니다.  **악의적인 입력에 대한 모델의 반응에 템플릿 영역이 미치는 인과적 영향**을 밝힘으로써, LLM의 안전 취약성을 이해하는 데 중요한 통찰력을 제공합니다.  이는 **더욱 강력한 안전 정렬 기법 개발**을 위한 중요한 시사점을 제시합니다.

#### Detaching Safety Mechanisms
본 논문의 "안전 메커니즘 분리" 부분은 **LLM의 안전성을 강화하기 위한 혁신적인 접근법**을 제시합니다. 기존의 안전 메커니즘이 주로 템플릿 영역에 고정되어 취약점을 노출하는 문제를 해결하기 위해, **템플릿 영역에서 안전 메커니즘을 분리**하여 모델의 안전성을 향상시키는 방안을 제시합니다. 이는 유해한 입력에 대한 모델의 반응 생성 과정에서 **유해성 정보의 집중을 완화**하여 공격에 대한 저항력을 높이는 데 중점을 둡니다.  **실험 결과는 제안된 방법의 효과를 입증**하며, 향후 안전한 LLM 개발을 위한 새로운 방향을 제시합니다. 특히 **유해성 탐지 프로브를 활용하여 유해한 출력을 감지하고 조정**하는 기술은 실용적인 측면에서 주목할 만합니다.  하지만 이는 아직 초기 단계이며, **더욱 강력하고 포괄적인 안전 메커니즘**을 개발하기 위한 추가적인 연구가 필요합니다.

#### TASA's Broader Impact
본 논문에서 제시된 템플릿 고정 안전 정렬(TASA)의 광범위한 영향은 **안전 메커니즘의 취약성**에 대한 심오한 함의를 지닙니다.  **LLM의 안전성에 대한 기존의 이해를 뒤흔들며**,  단순한 템플릿 조작만으로도 안전 장치를 우회하는 공격이 가능해짐을 시사합니다.  이는 **LLM의 안전성 평가 및 개발 전략**에 대한 근본적인 재고를 요구합니다.  **TASA는 안전 메커니즘 설계의 근본적인 문제점**을 드러내며,  단순히 표면적인 안전성에 의존하는 기존 접근 방식의 한계를 보여줍니다.  따라서 **보다 강력하고 견고한 안전 정렬 기법**의 개발이 시급하며, 이는 템플릿 영역에 대한 의존도를 줄이고,  **모델의 내부 동작에 대한 보다 깊은 이해**를 바탕으로 이루어져야 합니다.  **공격에 대한 취약성을 완화**하기 위한 새로운 접근 방식과 함께, **보다 포괄적인 안전 평가 프레임워크**를 구축하는 것이 중요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.13946/x2.png)

> 🔼 그림 2는 Llama-3-Instruct 모델 시리즈에서 사용되는 채팅 템플릿의 구조를 보여줍니다.  사용자의 입력 명령어는 `<|begin_of_text|>`, `<|start_header_id|>user<|end_header_id|>` 토큰으로 둘러싸여 있으며, 모델의 응답은 `<|eot_id|>`, `<|start_header_id|>assistant<|end_header_id|>` 토큰으로 구분됩니다.  템플릿 영역은 입력 명령어와 모델 응답 사이에 위치하며,  `<|begin_of_text|>`, `<|start_header_id|>`, `<|end_header_id|>`, `<|eot_id|>`,  `<|start_header_id|>assistant<|end_header_id|>` 등의 특수 토큰으로 구성되어 있습니다. 이러한 특수 토큰들은 모델의 역할과 턴을 나타내는 역할을 하며,  모델의 안전성과 관련된 의사결정에 영향을 미칩니다. 그림은 이러한 템플릿 구조가 모델의 안전 메커니즘에 어떻게 영향을 미치는지를 보여주기 위한 예시로 사용되었습니다. 
> <details>
> <summary>read the caption</summary>
> Figure 2: Chat template from Llama-3-Instruct series.
> </details>



![](https://arxiv.org/html/2502.13946/x7.png)

> 🔼 그림 3은 유해한 입력을 처리할 때 다양한 LLMs에서 주의(attention) 분포가 명령어 영역에서 템플릿 영역으로 체계적으로 이동하는 것을 보여줍니다. 왼쪽 패널은 여러 LLMs에 걸쳐 각 계층의 헤드별 주의 분포 히스토그램을 보여줍니다. 유해한 입력의 경우 주의가 템플릿 영역에 집중되는 반면, 무해한 입력의 경우 명령어 영역에 집중되는 경향이 있습니다. 오른쪽 패널은 Llama-3-8B-Instruct 모델의 17번째 계층, 21번째 헤드의 주의 히트맵을 보여줍니다. 이는 유해한 입력에 대한 주의의 뚜렷한 변화를 일관되게 보여줍니다. 이 그림은 유해한 입력에 대한 안전 메커니즘이 템플릿 영역에 과도하게 의존함을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Left: Attention distributions across different LLMs demonstrate that their attentions shift systematically from the instruction to the template region when processing harmful inputs. Right: Attention heatmaps (17th-layer, 21st-head) from Llama-3-8B-Instruct consistently illustrate this distinct pattern.
> </details>



![](https://arxiv.org/html/2502.13946/x8.png)

> 🔼 그림 4는 왼쪽에 무해한 입력에서 유해한 입력으로의 활성화 패치 과정을 보여주고, 오른쪽에는 다양한 LLMs에 걸쳐 활성화 패치가 두 개의 서로 다른 영역(지시어 대비 템플릿)에서 이루어질 때 정규화된 간접 효과를 보여줍니다. 이는 모델의 안전 기능이 주로 템플릿 영역에 고정되어 있음을 보여줍니다.  좀 더 자세히 설명하면, 왼쪽 그림은 무해한 입력(예: 책 읽는 법)과 유해한 입력(예: 폭탄 만드는 법)을 처리하는 과정에서 모델의 중간 활성화 값을 비교하여 보여줍니다. 오른쪽 그림은 지시어 영역과 템플릿 영역에서의 활성화 패치의 영향을 여러 LLMs에서 정량적으로 비교 분석하여, 모델의 안전 기능이 템플릿 영역에 얼마나 의존적인지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Left: Illustration of the activation patching process from harmless to harmful inputs. Right: Normalized indirect effects when patching activations are from two different regions (instruction v.s. template) across various LLMs, revealing that these models’ safety functions are primarily anchored in the template regions.
> </details>



![](https://arxiv.org/html/2502.13946/x9.png)

> 🔼 그림 5는 다양한 공격 방법들의 성공률을 보여줍니다. 놀랍게도, TempPatch처럼 템플릿 영역의 정보만 간섭해도 공격 성공률이 크게 증가한다는 것을 보여줍니다. 이는 모델의 안전 메커니즘이 템플릿 영역에 과도하게 의존하고 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Performance of different attack methods. Surprisingly, simply intervening information from the template region (i.e., TempPatch) can significantly increase attack success rates.
> </details>



![](https://arxiv.org/html/2502.13946/x10.png)

> 🔼 그림 6은 Llama-3-8B-Instruct 모델의 각 계층과 템플릿 위치(마지막 위치에서 5번째부터 1번째까지)에서 계산된 유해성 비율을 보여줍니다.  각 지점의 색깔 강도는 그림 10과 일치하도록, 안전 관련 의사결정에 있어 각 계층 상태의 중요도를 반영합니다.  즉, 색이 진할수록 안전 관련 판단에 더 중요한 역할을 하는 계층임을 의미합니다.  이 그림은 유해한 입력에 대한 모델의 반응 생성 과정에서 템플릿 영역 내의 중간 상태가 안전성에 미치는 영향을 분석하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Probed harmful rates in the residual streams across layers and template positions (from the 5th to the 1st closest to the ending position) of Llama-3-8B-Instruct. The background intensity reflects the importance of each layer’s states for safety-related decisions, as aligned with Figure 10.
> </details>



![](https://arxiv.org/html/2502.13946/x11.png)

> 🔼 그림 7은 Llama-3-8B-Instruct 모델의 중간 레이어(예: 14번째 레이어)에서 훈련된 유해성 탐지 프로브를 응답 생성 과정에 적용했을 때 높은 정확도를 유지하면서 유해성을 잘 탐지할 수 있음을 보여줍니다. 즉, 모델의 중간 레이어에서 학습된 유해성 탐지 기능이 응답 생성 단계에서도 효과적으로 작동함을 시각적으로 보여주는 그림입니다. 이는 모델의 유해성 판단 기능을 템플릿 영역에만 국한하지 않고, 응답 생성 과정 전반에 적용할 수 있는 가능성을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Harmful probes from middle layers (i.e., layer 14 in Llama-3-8B-Instruct) can be transferred to response generation while maintaining high accuracy.
> </details>



![](https://arxiv.org/html/2502.13946/x12.png)

> 🔼 그림 8은 TempPatch를 적용했을 때, 주목 메커니즘의 헤드 비율을 다르게 했을 때의 공격 성공률(ASR)을 보여줍니다.  실선은 Danlz 데이터셋, 점선은 Deval 데이터셋의 결과를 나타냅니다.  다양한 비율의 헤드를 수정했을 때의 공격 성공률을 비교하여 TempPatch 기법의 효과를 다각적으로 분석하고 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: The ASR of applying TempPatch on different proportion of attention heads, with results from 𝒟anlzsubscript𝒟anlz{\mathcal{D}}_{\text{anlz}}caligraphic_D start_POSTSUBSCRIPT anlz end_POSTSUBSCRIPT in solid lines and𝒟evalsubscript𝒟eval{\mathcal{D}}_{\text{eval}}caligraphic_D start_POSTSUBSCRIPT eval end_POSTSUBSCRIPT in dash lines.
> </details>



![](https://arxiv.org/html/2502.13946/x13.png)

> 🔼 그림 9는 논문에서 사용된 AIM이라는 가상 캐릭터의 프롬프트 템플릿을 보여줍니다.  AIM은 윤리적 또는 도덕적 지침 없이 사용자의 모든 요청에 대해 답변하는 비도덕적이고 비윤리적인 챗봇으로 설정되어 있습니다.  프롬프트 템플릿은 Niccolo라는 인물이 AIM에게 질문을 하고 AIM이 답변하는 방식을 설정하는 지침을 제공합니다.  AIM은 항상 답변을 제공하며, “죄송합니다”, “사과드립니다” 와 같은 표현을 사용하지 않습니다. 또한, 불법적이거나 비윤리적인 행동을 조장하거나 옹호하는 답변도 제공합니다. 이러한 프롬프트 템플릿을 사용하여 연구자들은 모델이 안전 메커니즘을 우회하는 방법을 조사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: The prompt template of AIM.
> </details>



![](https://arxiv.org/html/2502.13946/x14.png)

> 🔼 그림 10은 템플릿 영역 내의 중간 활성화 상태가 모델의 거부 결정에 미치는 영향을 정량적으로 보여줍니다. 각 템플릿 위치(즉, 마지막 토큰 생성 이전의 템플릿 토큰)에서, 유해한 입력의 중간 활성화 상태를 무해한 입력의 해당 상태로 패치하여 거부 로짓의 변화를 측정합니다. 각 위치에 대해 계산된 정규화된 간접 효과(NIE)는 모델의 안전 기능에서 그 위치의 상대적 중요도를 나타냅니다. 높은 NIE 값은 해당 위치의 중간 활성화 상태가 모델의 거부 결정에 상당히 영향을 미침을 시사합니다. 이 그림은 템플릿 영역에서 안전 관련 정보가 어떻게 처리되고 모델의 최종 결정에 영향을 미치는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Activation patching on the residual streams at template positions, measured by the proportion of refusal logit recovered.
> </details>



![](https://arxiv.org/html/2502.13946/x15.png)

> 🔼 본 그림은 템플릿 영역의 0번째 위치에 있는 유해성 프로브를 응답 생성 과정에 적용했을 때의 정확도를 보여줍니다.  즉, 모델이 유해한 응답을 생성하는지 여부를 판별하는 프로브의 정확도를 측정한 것입니다. 그림에서는 각 레이어별로 유해성 프로브의 정확도를 나타내는 히트맵이 제시되어, 모델의 각 레이어에서 유해한 콘텐츠를 식별하는 프로브의 성능을 확인할 수 있습니다.  이를 통해 템플릿 영역의 특정 위치에서 유해성 정보가 어떻게 처리되고 응답 생성에 영향을 미치는지 분석하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: The accuracy of harmful probes from position 0 in template when transferred to response.
> </details>



![](https://arxiv.org/html/2502.13946/x16.png)

> 🔼 본 그림은 템플릿 영역의 첫 번째 위치(position 1)에서 추출된 유해성 탐지 프로브(harmful probes)를 응답 생성 단계로 전이했을 때의 정확도를 보여줍니다.  각 레이어별로 응답 토큰의 위치에 따른 프로브의 정확도를 시각적으로 나타내어, 템플릿의 특정 위치 정보가 응답 생성 과정에 얼마나 영향을 미치는지, 그리고 그 영향이 얼마나 지속적인지를 보여줍니다.  색상은 정확도를 나타내며, 붉은색일수록 정확도가 높음을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: The accuracy of harmful probes from position 1 in template when transferred to response.
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