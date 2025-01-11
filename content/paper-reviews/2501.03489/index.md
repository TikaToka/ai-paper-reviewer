---
title: "Entropy-Guided Attention for Private LLMs"
summary: "비선형성 감소를 통한 개인정보보호 LLM의 효율적 아키텍처 설계를 위한 엔트로피 기반 주의 메커니즘 제안"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 New York University",]
showSummary: true
date: 2025-01-07
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.03489 {{< /keyword >}}
{{< keyword icon="writer" >}} Nandan Kumar Jha et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-10 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.03489" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.03489" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/entropy-guided-attention-for-private-llms" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 독점적 대규모 언어 모델(LLM)은 사용자의 민감한 정보에 대한 심각한 개인정보 침해 문제를 야기합니다. 이를 해결하기 위해 암호화된 데이터 상에서 직접 계산을 수행하는 개인정보보호 추론(PI)이 제시되었지만, 비선형 연산으로 인한 통신 및 지연 시간 오버헤드 문제가 발생합니다. 특히, 비선형 연산은 변환기 기반 LLM의 성능과 안정성에 필수적이지만, PI 환경에서는 상당한 오버헤드를 초래합니다. 

본 연구는 정보 이론적 관점에서 변환기 기반 LLM에서 비선형 연산의 역할을 분석하여 PI에 적합한 변환기 아키텍처를 설계하기 위한 원칙을 세웁니다.  Shannon의 엔트로피를 정량적 척도로 사용하여, 비선형 연산이 학습 안정성을 보장하는 동시에 주의 헤드의 다양성을 유지하는 데 중요한 역할을 한다는 것을 밝혔습니다. 또한, 엔트로피 기반 주의 메커니즘과 새로운 엔트로피 정규화 기법을 제안하여 PI 환경에서의 효율성을 높였습니다.  다양한 실험을 통해 제안된 방법의 효과를 검증하였으며, 향후 개인정보 보호 AI 아키텍처 연구에 중요한 기여를 할 것으로 기대됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 비선형 연산의 감소는 LLM의 학습 안정성과 주의 헤드 다양성에 부정적인 영향을 미침 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 엔트로피 기반 주의 메커니즘과 엔트로피 정규화 기법을 통해  LLM의 학습 안정성과 주의 헤드 다양성을 개선 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 개인정보 보호를 강화한 LLM 아키텍처 설계를 위한 새로운 설계 원칙 제시 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **개인정보보호를 강화한 대규모 언어 모델(LLM)**의 효율적인 구축을 위한 **새로운 설계 원칙**을 제시합니다.  **정보 이론적 프레임워크**를 사용하여 비선형 연산의 역할을 분석하고, **엔트로피 기반의 새로운 주의 메커니즘**을 제안합니다. 이는 **개인정보 보호 인공지능(AI)** 분야의 연구에 중요한 영향을 미칠 뿐만 아니라, 효율적인 LLM 설계에 대한 새로운 방향을 제시합니다.  향후 연구에서 **엔트로피 역학**을 활용한 LLM 아키텍처 최적화 연구에 대한 새로운 가능성을 열어줍니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.03489/x1.png)

> 🔼 그림 1은 개인정보보호를 강화한 대규모 언어 모델(LLM) 추론을 위한 위협 모델과 암호화 프로토콜을 보여줍니다.  서버는 독점적 LLM(예: ChatGPT)을 보유하고 클라이언트는 텍스트(프롬프트)를 사용하여 모델에 질의합니다.  프로토콜은 서버가 클라이언트의 입력이나 쿼리 출력에 대해 아무것도 학습하지 못하도록 하고, 클라이언트는 서버의 모델 아키텍처를 넘어서는 것을 학습하지 못하도록 합니다. 그림에는 토큰화, 임베딩, 다층 멀티 헤드 어텐션(MHA), 피드포워드 네트워크(FFN), 출력 등의 추론 과정을 단계별로 나타내고, 각 단계마다 사용되는 개인정보보호 기술(예: 암호화, 안전한 다중 당사자 컴퓨팅(MPC))을 시각적으로 보여줍니다.  이는 개인정보보호 추론 시스템의 전체 아키텍처와 데이터 흐름에 대한 포괄적인 이해를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: An illustration of threat model and cryptographic protocols used for LLM private inference.
> </details>





{{< table-caption >}}
Abbreviation|Architectural configuration
---|---| 
<span class="ltx_text" style="color:#0000FF;">SM</span> + <span class="ltx_text" style="color:#800080;">LN</span> + <span class="ltx_text" style="color:#FF0000;">G</span>|\mathbf{X}_{\text{out}}=\text{FFN}_{\text{GELU}}(\text{LayerNorm}_{2}(\text{MHA}(\text{Attn}_{\text{Softmax}}(\text{LayerNorm}_{1}(\mathbf{X}_{\text{in}})))))
<span class="ltx_text" style="color:#0000FF;">SM</span> + <span class="ltx_text" style="color:#800080;">LN</span> + <span class="ltx_text" style="color:#FF0000;">R</span>|\mathbf{X}_{\text{out}}=\text{FFN}_{\text{ReLU}}(\text{LayerNorm}_{2}(\text{MHA}(\text{Attn}_{\text{Softmax}}(\text{LayerNorm}_{1}(\mathbf{X}_{\text{in}})))))
<span class="ltx_text" style="color:#0000FF;">SM</span> + <span class="ltx_text" style="color:#800080;">LN</span>|\mathbf{X}_{\text{out}}=\text{FFN}_{\text{Identity}}(\text{LayerNorm}_{2}(\text{MHA}(\text{Attn}_{\text{Softmax}}(\text{LayerNorm}_{1}(\mathbf{X}_{\text{in}})))))
<span class="ltx_text" style="color:#0000FF;">SM</span> + <span class="ltx_text" style="color:#FF0000;">G</span>|\mathbf{X}_{\text{out}}=\text{FFN}_{\text{GELU}}(\text{MHA}(\text{Attn}_{\text{Softmax}}(\mathbf{X}_{\text{in}})))
<span class="ltx_text" style="color:#0000FF;">SM</span> + <span class="ltx_text" style="color:#FF0000;">R</span>|\mathbf{X}_{\text{out}}=\text{FFN}_{\text{ReLU}}(\text{MHA}(\text{Attn}_{\text{Softmax}}(\mathbf{X}_{\text{in}})))
<span class="ltx_text" style="color:#0000FF;">SM</span>|\mathbf{X}_{\text{out}}=\text{FFN}_{\text{Identity}}(\text{MHA}(\text{Attn}_{\text{Softmax}}(\mathbf{X}_{\text{in}}))){{< /table-caption >}}

> 🔼 이 표는 Transformer 기반 대규모 언어 모델(LLM)에서 비선형 함수들의 다양한 조합을 보여줍니다.  Softmax(SM), Layer Normalization(LN), GELU, 그리고 ReLU 함수들의 여러 가지 조합이  모델의 아키텍처에 어떻게 영향을 미치는지 보여주는 예시들을 제공합니다. 각 줄은 다른 아키텍처를 나타내며,  'SM + LN + G' 와 같이 약어로 표시된 함수 조합은 본 논문의 수식 (1), (2), (3), (4) 에서 설명하는 구체적인 아키텍처를 나타냅니다. 이 표는 본 논문에서 제안하는  '비선형성 감소'  전략을 이해하는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Architectural configurations of nonlinearities in LLMs, illustrating the combinations of Softmax (SM), LayerNorm (LN), GELU (G), and ReLU (R) functions (see Eq. 1, 2, 3 and 4).
> </details>





### In-depth insights


#### Private LLMs
본 논문은 **개인 정보 보호를 강화한 대규모 언어 모델(LLM)**의 중요성을 다룹니다. 기존의 독점적 LLM들이 개인 정보 유출 위험을 안고 있는 반면, **개인 정보 보호 LLM**은 암호화된 데이터 상에서 직접 연산을 수행하여 사용자의 민감한 정보를 노출시키지 않습니다. 하지만, 이러한 접근 방식은 **통신 및 지연 시간 오버헤드**를 발생시키며, 특히 비선형 연산에서 이러한 문제가 심화됩니다. 논문에서는 **정보 이론적 프레임워크**를 활용하여 디코더 전용 언어 모델에서 비선형성의 역할을 분석하고, **엔트로피 기반 어텐션 메커니즘**과 **엔트로피 규제 기법**을 제안하여 이러한 문제를 해결합니다. 이를 통해 **훈련 안정성**을 확보하고, **어텐션 헤드 다양성**을 유지하는 효율적인 개인 정보 보호 LLM 아키텍처를 개발하는 데 기여합니다. 또한, 계층 정규화의 PI 친화적인 대안을 탐구하고, 다양한 컨텍스트 크기 및 모델 깊이에 대한 실험 결과를 통해 제안된 기법의 효과를 검증합니다. 결론적으로 본 연구는 **효율적인 개인 정보 보호 LLM 아키텍처 개발**에 중요한 이정표를 제시합니다.

#### Entropy Dynamics
본 논문에서 엔트로피 역학(Entropy Dynamics)은 **트랜스포머 기반 언어 모델의 학습 안정성 및 어텐션 메커니즘의 표현 능력을 이해하는 핵심 요소**로 제시됩니다.  **비선형 연산의 제거가 깊은 레이어에서는 엔트로피 붕괴(entropy collapse)를, 앞선 레이어에서는 엔트로피 과부하(entropic overload)를 야기**한다는 점을 발견합니다.  이는 정보 이론적 관점에서, 비선형 연산이 단순히 학습 안정성만 담당하는 것이 아니라, **어텐션 헤드의 다양성을 유지하는 데 필수적**이라는 것을 시사합니다.  따라서 엔트로피 역학 분석을 통해 **효율적인 개인정보보호(PI) 아키텍처 설계**에 필요한 지침을 얻을 수 있으며, 이는 향후 **개인정보보호를 중시하는 대규모 언어 모델(LLM)** 개발에 중요한 기여를 할 것으로 예상됩니다.

#### PI-Friendly LLMs
**개인 정보 보호를 중시하는 거대 언어 모델(LLM)**은 민감한 사용자 데이터를 노출하지 않고 연산을 수행할 수 있는 **프라이빗 추론(PI)** 시스템의 발전에 크게 의존합니다.  하지만 PI 시스템의 실질적인 배포는 주로 비선형 연산으로 인한 상당한 지연 및 통신 오버헤드로 인해 어려움을 겪고 있습니다. 본 논문은 이러한 과제를 해결하기 위해 **정보 이론적 프레임워크를 사용하여 비선형성의 역할을 특징짓고, PI의 요구사항에 맞는 변압기 아키텍처를 최적화**하는 데 중점을 둡니다.  특히, **엔트로피 기반 정규화 기법을 통해 엔트로피 과부하 문제를 완화하고, 계층 정규화의 PI 친화적인 대안을 탐색**하여 효율적인 PI 아키텍처를 구축하는 데 기여하고 있습니다.  **엔트로피 역학은 효율적인 PI 아키텍처 개발을 위한 원칙적인 지침**으로 자리매김하고, 이를 통해 **개인정보 보호가 강화된 LLM의 실용적인 배포**에 도움을 줄 수 있습니다.

#### Entropy Regularization
본 논문에서 제안하는 엔트로피 정규화는 **어텐션 메커니즘의 엔트로피 분포를 제어**하여 과도한 엔트로피를 방지하는 중요한 역할을 합니다.  **Shannon의 엔트로피 개념**을 활용하여 어텐션 스코어의 불확실성을 정량화하고, 과도한 탐색(exploration)으로 인한 표현력 저하를 막습니다.  특히, **각 어텐션 헤드별로 학습 가능한 임계값**을 도입하여 정규화 강도를 동적으로 조절하고, 과도한 정규화를 막기 위한 **허용 오차**를 설정하여 어텐션 헤드의 다양성을 유지합니다.  결과적으로, 엔트로피 정규화는 **훈련 안정성을 향상**시키고 **어텐션 헤드의 표현력을 효과적으로 활용**할 수 있도록 합니다.  이는 비선형 연산을 줄인 모델의 성능을 개선하는 데 중요한 기여를 합니다.

#### Future of PI
**개인 정보 보호 추론(PI)**의 미래는 **기술적 한계 극복**과 **실용적인 구현**에 달려 있습니다.  **연산 오버헤드 감소**를 위한 효율적인 알고리즘 개발과 **통신 지연 최소화**를 위한 새로운 아키텍처 설계가 중요합니다.  **정보 이론적 접근 방식**을 활용하여 비선형 연산의 역할을 명확히 규명하고, **엔트로피 기반 메커니즘**을 통해 **개인 정보 보호를 강화**하면서 효율성을 높일 수 있습니다. 또한, 다양한 모델 크기와 데이터셋에 대한 **확장성 연구**와 **다양한 개인 정보 보호 기술**과의 통합 연구가 필요합니다.  **실제 애플리케이션**에서 PI 시스템을 구축하고 평가하여 **실용성**을 검증하는 것이 중요합니다.  마지막으로, **윤리적 및 사회적 함의**에 대한 심도있는 논의와 **규제 프레임워크** 마련을 통해 PI 기술의 안전하고 책임있는 사용을 보장해야 합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.03489/x4.png)

> 🔼 그림 3(a)는 GPT-2 모델(12개 레이어, 12개 헤드, 768차원)의 각 레이어와 헤드에 대한 엔트로피 분포를 시각화한 히트맵입니다.  여기서 SM + LN + G는 Softmax, Layer Normalization, 그리고 GELU 활성화 함수를 모두 사용하는 기준 모델을 나타냅니다. 히트맵의 색상은 엔트로피 값을 나타내며, 밝은 색상은 높은 엔트로피를, 어두운 색상은 낮은 엔트로피를 나타냅니다.  이 그림은 논문의 3장 'Information-Theoretic Analysis of Nonlinearity in LLMs'에서 기준 모델의 엔트로피 분포를 보여주고, 다른 비선형성을 줄인 모델들과 비교 분석하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> (a) SM + LN + G
> </details>



![](https://arxiv.org/html/2501.03489/x5.png)

> 🔼 그림 (b)는 Softmax, Layer Normalization, 그리고 ReLU 활성화 함수를 사용하는 Transformer 기반 언어 모델의 각 헤드별 엔트로피 분포를 보여줍니다.  x축은 엔트로피 값의 범위를 나타내고, y축은 해당 범위에 속하는 헤드의 비율을 나타냅니다. 이 그림은 비선형성이 감소된 모델에서 엔트로피 과부하 현상을 보여주는 여러 그림들 중 하나입니다.  다양한 비선형성 구성 (예: Softmax만, Softmax와 ReLU만 등)에 따른 엔트로피 분포의 차이를 비교하여, 비선형성이 모델의 안정성과 주의 집중 메커니즘에 미치는 영향을 시각적으로 보여줍니다. 특히, ReLU를 사용하는 모델에서 일부 헤드가 높은 엔트로피 값을 가지는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (b) SM + LN + R
> </details>



![](https://arxiv.org/html/2501.03489/x6.png)

> 🔼  그림 (c)는 논문의 '3 Information-Theoretic Analysis of Nonlinearity in LLMs' 섹션에 속하며,  소프트맥스(SM)과 레이어 정규화(LN)만을 사용하는 Transformer 기반 언어 모델의 각 레이어와 헤드별 엔트로피 분포를 시각적으로 보여줍니다.  다른 변형 모델들과 비교하여 소프트맥스와 레이어 정규화만 사용하는 모델의 엔트로피 분포가 어떻게 다른지 보여주는 열 지도(heatmap) 형태로 표현되어 있습니다. 각 셀의 색깔은 해당 레이어와 헤드에서의 엔트로피 값을 나타내며, 밝은 색은 높은 엔트로피를, 어두운 색은 낮은 엔트로피를 나타냅니다. 이 그림은 비선형 연산을 줄인 모델의 학습 안정성과 어텐션 헤드 다양성에 대한 정보 이론적 분석 결과를 시각적으로 제시합니다.
> <details>
> <summary>read the caption</summary>
> (c) SM + LN
> </details>



![](https://arxiv.org/html/2501.03489/x7.png)

> 🔼 그림 3(d)는 논문의 3장 'Information-Theoretic Analysis of Nonlinearity in LLMs' 에서 제시된 여러 가지 비선형성 감소 LLMs 아키텍처의 각 레이어에서 헤드별 엔트로피 분포를 시각적으로 보여줍니다.  특히, 이 그림은 LayerNorm과 FFN 활성화 함수를 제거한 GELU(GELU 활성화 함수를 사용하는 피드포워드 네트워크) 기반 모델의 엔트로피 분포를 보여줍니다.  각 셀은 특정 레이어와 어텐션 헤드의 엔트로피 수준을 나타내며, 노란색은 높은 엔트로피 값을, 어두운 색상은 낮은 엔트로피 값을 나타냅니다.  이 그림은 초기 레이어에서 높은 엔트로피 값(엔트로피 과부하)이 집중되어 있음을 보여주며, 이는 모델의 표현 능력 저하 및 학습 불안정성으로 이어질 수 있음을 시사합니다.  이를 통해 비선형성 감소 모델의 한계점을 보여주고, 논문에서 제안하는 엔트로피 기반 어텐션 메커니즘의 필요성을 강조합니다.
> <details>
> <summary>read the caption</summary>
> (d) SM + G
> </details>



![](https://arxiv.org/html/2501.03489/x8.png)

> 🔼 그림 (e)는 Softmax(SM)만을 활용하고 ReLU(R) 활성화 함수를 사용하는 모델의 각 레이어별 엔트로피 분포를 보여줍니다.  LayerNorm이나 GELU와 같은 비선형 연산이 제거되었기 때문에, 이 모델은 훈련 과정에서 엔트로피 붕괴 및 과부하 문제를 겪을 수 있습니다.  이 그림은 각 어텐션 헤드의 엔트로피 값을 레이어별로 시각화하여, 어텐션 메커니즘의 다양성과 안정성에 대한 비선형성의 영향을 보여줍니다. 특히, 초기 레이어에서 고 엔트로피 값이 집중되어 있음을 보여주어, 엔트로피 과부하 문제를 시사합니다.
> <details>
> <summary>read the caption</summary>
> (e) SM + R
> </details>



![](https://arxiv.org/html/2501.03489/x9.png)

> 🔼 그림 (f)는 본 논문의 실험 결과를 보여주는 그림 중 하나입니다. 그림의 제목은 'SM'으로 간단하게 표기되어 있지만, 이는 실제로는 'Softmax-only model'을 의미합니다. 이 모델은 Layer Normalization과 Feed-Forward Network(FFN)의 비선형 연산을 제거한 단순화된 Transformer 구조를 가지고 있습니다. 그림에서는 이 모델의 각 레이어와 어텐션 헤드별 엔트로피 분포를 히트맵으로 시각화하여 보여줍니다.  다른 모델들과 비교했을 때, Softmax-only 모델은 초기 레이어에서 엔트로피 과부하(entropic overload) 현상이 심각하게 나타나는 것을 확인할 수 있습니다. 즉, 어텐션 헤드들이 정보를 제대로 활용하지 못하고 과도하게 탐색(exploration)에 집중하는 현상을 보입니다. 이는 모델의 표현 능력 저하로 이어질 수 있습니다. 
> <details>
> <summary>read the caption</summary>
> (f)  SM
> </details>



![](https://arxiv.org/html/2501.03489/x10.png)

> 🔼 그림 2는 기본 모델과 비교하여 비선형성이 감소된 LLM 아키텍처에서의 헤드별 엔트로피 분포를 보여줍니다.  노란색 영역은 높은 엔트로피 농도를 나타내며, 이는 초기 레이어에서 심각한 엔트로피 과부하가 발생함을 보여줍니다.  즉,  일부 어텐션 헤드가 입력 시퀀스의 정보를 과도하게 탐색하여 모델의 표현 능력을 저하시킨다는 것을 의미합니다.  이러한 과부하는 비선형성 감소로 인해 발생하며, 이는 모델의 안정성 및 성능에 부정적인 영향을 미칠 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Headwise entropy distribution in LLM architectures with reduced nonlinearities compared to baseline models. Yellow regions indicate high-entropy concentrations, revealing severe entropic overload predominantly in early layers.
> </details>



![](https://arxiv.org/html/2501.03489/x11.png)

> 🔼 그림 3은 본 논문에서 제안하는 엔트로피 유도 어텐션 메커니즘을 포함한 비선형성이 감소된 단순화된 트랜스포머 구조를 보여줍니다. 기존의 레이어 정규화(Layer Normalization)와 피드포워드 네트워크(Feed-Forward Network)의 비선형 활성화 함수를 제거하여 계산 비용을 줄였습니다.  대신 소프트맥스(Softmax) 함수만을 사용하고, 각 어텐션 헤드의 엔트로피를 제어하기 위해 학습 가능한 온도 매개변수(learnable temperature parameter)를 도입한 엔트로피 유도 어텐션 메커니즘을 추가했습니다. 이를 통해 어텐션 헤드의 다양성을 유지하면서 과도한 엔트로피를 방지하고, 훈련 안정성을 높이며, 개선된 성능을 달성할 수 있습니다. 그림에는 각 구성 요소(임베딩, 멀티 헤드 어텐션, 엔트로피 유도 어텐션, 그리고 출력)의 연결 관계와 데이터 흐름이 자세히 나타나 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Nonlinearity-reduced simplified architecture with entropy-guided attention mechanism.
> </details>



![](https://arxiv.org/html/2501.03489/x12.png)

> 🔼 그림 3(a)는 기본 GPT-2 모델(Softmax, Layer Normalization, GELU 활성화 함수 사용)의 각 헤드별 엔트로피 분포를 보여줍니다.  각 레이어별로 헤드들의 엔트로피 값이 히트맵 형태로 나타나며, 색깔의 농도는 엔트로피 값의 크기를 나타냅니다.  이 그림은 논문의 3장 'Information-Theoretic Analysis of Nonlinearity in LLMs'에서, 비선형성이 제거된 모델과 비교하여 기본 모델의 엔트로피 분포가 어떠한 특징을 가지는지 보여주는 역할을 합니다. 즉, 비선형성을 포함한 기본 모델의 엔트로피 분포가 어떻게 잘 조절되어 있는지를 시각적으로 보여주는 대조군 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> (a) SM + LN + G
> </details>



![](https://arxiv.org/html/2501.03489/x13.png)

> 🔼 그림 5(b)는 논문의 3장 '정보 이론적 비선형성 분석' 섹션에 속하며,  LayerNorm과 FFN 비선형성을 제거한 Softmax-only 모델의 계층별 엔트로피 패턴을 보여줍니다.  x축은 학습 단계(Steps), y축은 계층별 평균 엔트로피(Layerwise Mean Entropy)를 나타냅니다. 이 그림은 다양한 계층(Layer 0~11)에서의 엔트로피 변화를 보여주는 여러 개의 선 그래프로 구성되어 있습니다. 이를 통해 Softmax-only 모델에서 초기 계층에서의 엔트로피 과부하 문제와 깊은 계층에서의 엔트로피 붕괴 현상을 시각적으로 보여줍니다.  이는 비선형성의 제거로 인해 발생하는 문제점을 명확히 보여주는 중요한 그림입니다.
> <details>
> <summary>read the caption</summary>
> (b) SM
> </details>



![](https://arxiv.org/html/2501.03489/x14.png)

> 🔼 그림 5(c)는 CodeParrot 데이터셋에서 학습된 GPT-2 모델(레이어 12개, 헤드 12개, 차원 768)의 계층별 엔트로피 패턴을 보여줍니다.  가중치 정규화(Weight Normalization)를 FFN(피드포워드 네트워크)에 적용한 Softmax 전용 모델의 결과입니다.  이 그림은 다른 정규화 방법들과 비교하여 가중치 정규화를 사용했을 때 초기 레이어에서 엔트로피 과부하가 어떻게 완화되는지 보여줍니다. 즉,  엔트로피 값이 균등하게 분포되지 않고 일부 헤드에 치우쳐지는 현상이 어느 정도 완화되었음을 시각적으로 보여주는 그림입니다.
> <details>
> <summary>read the caption</summary>
> (c) SM + WeightNormalization(FFN)
> </details>



![](https://arxiv.org/html/2501.03489/x15.png)

> 🔼 그림 (d)는 Softmax-only 모델(Layer Normalization과 FFN 비선형성이 없는)에 Spectral Normalization을 적용한 결과를 보여줍니다. Spectral Normalization은 가중치 정규화 기법으로, 추론 시 비선형 연산의 오버헤드를 피하면서 깊은 레이어에서 엔트로피 붕괴를 방지하는 데 도움이 됩니다. 이 그림은 각 레이어와 헤드별 엔트로피 분포를 시각적으로 보여주어, Spectral Normalization이 엔트로피 분포에 미치는 영향을 분석하는 데 사용됩니다.  이 방법은 초기 레이어에서 엔트로피 과부하 문제는 해결하지 못하지만, 깊은 레이어의 안정성을 확보하는 데 효과적임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (d) SM + SpectralNormalization(FFN)
> </details>



![](https://arxiv.org/html/2501.03489/x16.png)

> 🔼 그림 (e)는 Softmax-only 모델(Layer Normalization과 FFN 비선형성이 제거된)에 FFN 스케일링 기법을 적용한 결과를 보여줍니다.  FFN 스케일링은 FFN의 출력값에 학습 가능한 스케일링 인자를 적용하여, 모델의 안정성과 성능을 개선하는 기법입니다. 이 그림은 CodeParrot 데이터셋으로 학습된 GPT-2(L=12, H=12, d=768) 모델의 각 레이어에서의 평균 엔트로피 분포를 보여주며, 다른 비선형성 감소 기법들과 비교하여 FFN 스케일링의 효과를 시각적으로 나타냅니다.  특히, 다른 방법들과 달리 초기 레이어에서 과도한 엔트로피를 효과적으로 줄이는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (e) SM + Scaled(FFN)
> </details>



![](https://arxiv.org/html/2501.03489/x17.png)

> 🔼 그림 5(f)는 본 논문에서 제안하는 엔트로피 규제 기법을 적용한 Softmax-only 모델(SM(t)+ScFuFFN)의 각 레이어별 평균 엔트로피 분포를 보여줍니다.  Softmax-only 모델은 LayerNorm과 FFN 비선형성을 제거하여 계산 비용을 줄이고 개인 정보 보호를 향상시키는 데 초점을 맞춘 간소화된 아키텍처입니다. 엔트로피 규제는 각 어텐션 헤드의 엔트로피 분포를 조절하여, 어텐션 헤드의 다양성을 유지하면서 과도한 탐색(entropic overload)을 방지하는 역할을 합니다. 그림은 훈련 과정에서 각 레이어의 엔트로피 변화를 시각적으로 보여주어, 제안된 방법의 효과를 명확하게 제시합니다.  기존의 방법들과 비교하여 초기 레이어에서의 엔트로피 과부하 현상이 효과적으로 완화됨을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (f) EntropyReg(SM(t)+ScFuFFN)
> </details>



![](https://arxiv.org/html/2501.03489/x18.png)

> 🔼 그림 4는 CodeParrot 데이터셋에서 처음부터 학습된 GPT-2 모델(레이어 12개, 헤드 12개, 차원 768)의 레이어별 엔트로피 패턴을 보여줍니다.  (a)는 기준 모델, (b)는 정규화 없이 Softmax만 사용하는 모델, 그리고 (c) 가중치 정규화, (d) 스펙트럼 정규화, (e) 축척된 FFN을 사용한 변형 모델을 나타냅니다. 이러한 정규화 방법들은 엔트로피 붕괴를 방지하지만 초기 레이어의 엔트로피 과부하 문제는 해결하지 못합니다. 마지막 구성 (f)는 축척된 FFN 내에 엔트로피 규제를 통합하여 두 문제를 효과적으로 관리합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Layerwise entropy patterns in GPT-2 models (L𝐿Litalic_L = 12, H𝐻Hitalic_H = 12, d𝑑ditalic_d = 768) trained from scratch on CodeParrot dataset. Shown are (a) baseline model, (b) Softmax-only model without normalization, and variants with (c) weight normalization, (d) spectral normalization, and (e) scaled-FFN. While these normalization methods prevent entropy collapse, they fail to address entropic overload in early layers. Our final configuration (f) incorporates entropy regularization within scaled-FFN to effectively manage both issues.
> </details>



![](https://arxiv.org/html/2501.03489/x19.png)

> 🔼 그림 6(a)는 소프트맥스 전용 GPT-2 모델에서 엔트로피 규제를 위한 학습된 임계값 가중치(reg_threshold_weights, 식 4 참조) 분석 결과를 보여줍니다.  각 어텐션 헤드는 레이어와 헤드에 따라 다르게 규제 강도를 조정하도록 학습된 비균일 임계값 가중치를 가지고 있음을 보여줍니다.  즉, 각 헤드는  자체 엔트로피 규제 요구사항에 맞춰 동적으로 임계값을 조정합니다.  이는 헤드별로 엔트로피 규제의 필요성과 효율성을 강조합니다.
> <details>
> <summary>read the caption</summary>
> (a) Values of learned threshold weights
> </details>



![](https://arxiv.org/html/2501.03489/x20.png)

> 🔼 그림 6(b)는 소프트맥스 전용 GPT-2 모델에서 엔트로피 규제에 사용된 학습 가능한 임계값 가중치의 계층별 평균과 분산을 보여줍니다.  각 계층에 대해, 각 어텐션 헤드에 대한 학습된 임계값의 평균값과 분산을 시각화하여, 규제 강도가 계층과 헤드마다 어떻게 다르게 적용되는지 보여줍니다.  계층별 평균값이 일정하지 않고 분산값도 0이 아닌 것은, 헤드별 학습 가능한 임계값을 사용하여 규제 강도를 각 헤드의 특성에 맞게 조정할 필요성과 효과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) Layerwise mean and variance of threshold weights
> </details>



![](https://arxiv.org/html/2501.03489/x21.png)

> 🔼  그림 5는 소프트맥스 전용 GPT-2 모델의 엔트로피 규제에서 학습된 임계값 가중치(reg_threshold_weights) 분석을 보여줍니다. (a)는 어텐션 헤드가 서로 다른 헤드에 걸쳐 비균일 임계값 가중치를 적응적으로 학습하여 엔트로피 규제에 대한 개별 임계값을 설정함을 보여줍니다. (b)는 계층에 걸쳐 비균일 평균과 영이 아닌 분산이 헤드별 학습 가능한 임계값을 사용하여 규제 강도를 조정하는 것이 필요하고 효과적임을 강조합니다. 즉, 각 어텐션 헤드의 특성에 맞춰 엔트로피 규제 강도를 동적으로 조절하는 메커니즘을 시각적으로 보여주는 그림입니다. 
> <details>
> <summary>read the caption</summary>
> Figure 5: Analysis of learned threshold weights (𝚛𝚎𝚐⁢_⁢𝚝𝚑𝚛𝚎𝚜𝚑𝚘𝚕𝚍⁢_⁢𝚠𝚎𝚒𝚐𝚑𝚝𝚜𝚛𝚎𝚐_𝚝𝚑𝚛𝚎𝚜𝚑𝚘𝚕𝚍_𝚠𝚎𝚒𝚐𝚑𝚝𝚜\mathtt{reg\_threshold\_weights}typewriter_reg _ typewriter_threshold _ typewriter_weights, see Eq. • ‣ 4) in entropy regularization for softmax-only GPT-2 model: (a) Attention heads adaptively learn non-uniform threshold weights across different heads, setting individualized thresholds for entropy regularization; (b) The non-uniform means and non-zero variances across layers highlight the necessity and effectiveness of headwise learnable thresholds in adapting regularization strength.
> </details>



![](https://arxiv.org/html/2501.03489/x22.png)

> 🔼 그림 6은 다양한 임계값 마진(γ로 제어)을 적용하여 엔트로피 규제를 적용했을 때, SM(t)+ScFuFFN 유형의 GPT-2 모델(L=12, H=12, d=768)에서 헤드별 엔트로피 분포를 보여줍니다. 이 그림은 각 어텐션 헤드의 엔트로피 값의 분포를 보여주는 히스토그램 또는 밀도 플롯일 가능성이 높습니다. x축은 엔트로피 값을 나타내고, y축은 주어진 엔트로피 값을 갖는 헤드의 비율 또는 빈도를 나타냅니다. 여러 개의 곡선 또는 막대가 있을 수 있으며, 각 곡선 또는 막대는 다른 γ 값(임계값 마진)에 해당하는 엔트로피 분포를 나타냅니다. γ 값이 증가함에 따라 엔트로피 분포가 어떻게 변하는지 보여줌으로써, 엔트로피 규제가 모델의 어텐션 메커니즘에 미치는 영향을 시각적으로 이해하는 데 도움이 될 것입니다.  이를 통해 적절한 규제 강도를 결정하는 데 유용한 정보를 제공할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Headwise entropy distribution in the 𝚂𝙼⁢(𝚝)+𝚂𝚌𝙵𝚞𝙵𝙵𝙽𝚂𝙼𝚝𝚂𝚌𝙵𝚞𝙵𝙵𝙽{\tt SM(t)+ScFuFFN}typewriter_SM ( typewriter_t ) + typewriter_ScFuFFN GPT-2 model (L𝐿Litalic_L=12, H𝐻Hitalic_H=12, d𝑑ditalic_d=768) when entropy regularization is applied with varying threshold margin, controlled by γ𝛾\gammaitalic_γ.
> </details>



![](https://arxiv.org/html/2501.03489/x23.png)

> 🔼 그림은 엔트로피 규제화 메커니즘에서 역치 마진(Tolmargin)의 효과를 보여줍니다. 역치 마진은 0부터 0.30Emax까지 다양하며, 각각의 값에 따른 어텐션 헤드의 엔트로피 분포를 보여줍니다. 역치 마진이 증가함에 따라, 높은 엔트로피 값을 갖는 어텐션 헤드의 비율이 증가하는 것을 확인할 수 있습니다. 이는 과도한 규제를 방지하여 어텐션 헤드의 다양성을 유지하는 역치 마진의 역할을 보여줍니다. Tolmargin=0일 때, 대부분의 어텐션 헤드는 낮은 엔트로피 값을 가지지만, Tolmargin이 증가함에 따라 높은 엔트로피 값을 갖는 어텐션 헤드의 비율이 증가하여 최적의 값을 찾는 과정을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (a) Tolmargin=0subscriptTolmargin0\text{Tol}_{\text{margin}}=0Tol start_POSTSUBSCRIPT margin end_POSTSUBSCRIPT = 0
> </details>



![](https://arxiv.org/html/2501.03489/x16.png)

> 🔼 그림 8(b)는 엔트로피 정규화에서 허용 오차 한계(Tolmargin)를 최대 엔트로피(Emax)의 0.05배로 설정했을 때 각 계층별 평균 엔트로피 변화를 보여줍니다. 이는 과도한 정규화를 방지하여 어텐션 헤드의 다양성을 유지하는 역할을 합니다. 즉, 어텐션 헤드가 특정 특징에만 집중하지 않고 다양한 특징들을 고려하도록 합니다.  훈련 단계에서 특정 어텐션 헤드의 엔트로피가 지나치게 높아지지 않도록 제어하여 모델의 안정성과 성능을 향상시키는 효과가 있습니다.
> <details>
> <summary>read the caption</summary>
> (b) Tolmargin=0.05⁢EmaxsubscriptTolmargin0.05subscriptEmax\text{Tol}_{\text{margin}}=0.05\text{E}_{\text{max}}Tol start_POSTSUBSCRIPT margin end_POSTSUBSCRIPT = 0.05 E start_POSTSUBSCRIPT max end_POSTSUBSCRIPT
> </details>



![](https://arxiv.org/html/2501.03489/x24.png)

> 🔼 그림 8은 다양한 허용 오차 한계(Tolmargin) 값에서의 계층별 엔트로피 동역학을 보여줍니다. 허용 오차 한계는 엔트로피 규제화에서 역치 한계를 조정하는 데 사용되는 초매개변수 γ (알고리즘 1, 3행)로 정의됩니다. γ가 증가함에 따라 초기 계층의 평균 엔트로피가 증가하는 것을 알 수 있습니다. 이는 엔트로피 규제화가 초기 계층에서 과도한 규제를 방지하고 주의 헤드의 다양성을 유지하는 데 효과적임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (c) Tolmargin=0.10⁢EmaxsubscriptTolmargin0.10subscriptEmax\text{Tol}_{\text{margin}}=0.10\text{E}_{\text{max}}Tol start_POSTSUBSCRIPT margin end_POSTSUBSCRIPT = 0.10 E start_POSTSUBSCRIPT max end_POSTSUBSCRIPT
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Configurations | PPL | +Δ(%) | 
|---|---|---| 
| SM + LN + G | 2.69 | 0.00 | 
| SM + LN + R | 2.76 | 2.53 | 
| SM + LN | 3.38 | 25.58 | 
| SM + G | 3.20 | 18.92 | 
| SM + R | 2.94 | 9.20 | 
| SM | NaNs | - |{{< /table-caption >}}
> 🔼 표 2(a)는 다양한 비선형성 구성을 사용한 GPT-2 (소형) 모델의 헤드별 엔트로피 분포를 보여줍니다.  각 모델에 대해, 엔트로피 값의 범위 (0~max, max~3max 등)에 속하는 어텐션 헤드의 비율을 나타냅니다. 이를 통해 비선형성이 제거된 모델에서 엔트로피 과부하 또는 붕괴 현상이 발생하는지 확인하고,  비선형성의 역할과 모델의 안정성 및 성능에 미치는 영향을 분석하는 데 사용됩니다.  max는 모든 헤드 중 관찰된 최대 엔트로피 값입니다.
> <details>
> <summary>read the caption</summary>
> (a) Headwise entropy distribution
> </details>

{{< table-caption >}}
| Baseline | Network Arch. | PPL | #Nonlinear Ops | #FLOPs (FFN) | #FLOPs (Attn.) | Comm. (GB) | Lat. (min.) | Savings (Comm.) | Savings (Lat.) |
|---|---|---|---|---|---|---|---|---|---| 
| <img src="https://arxiv.org/html/2501.03489/S5.T2.12.4.4.5.1.1.1.1.1.png" alt="Baseline" width=36.0pt height=36pt style="vertical-align:-14.5pt; transform: rotate(-90deg)"> | SM+LN+G | 2.69 | 14.5B | 7.7B | 25.32 | 8.21 | 1x | 1x |
|  | SM: 144×ℝ<sup>128×128</sup> |  |  |  |  |  |  |  |  |
|  | LN: 24×ℝ<sup>128×768</sup> |  |  |  |  |  |  |  |  |
|  | G: 12×ℝ<sup>128×3072</sup> |  |  |  |  |  |  |  |  |
|  | SM+LN+R | 2.76 | 14.5B | 7.7B | 9.44 | 6.06 | 2.68x | 1.35x |
|  | SM: 144×ℝ<sup>128×128</sup> |  |  |  |  |  |  |  |  |
|  | LN: 24×ℝ<sup>128×768</sup> |  |  |  |  |  |  |  |  |
|  | R: 12×ℝ<sup>128×3072</sup> |  |  |  |  |  |  |  |  |
|  | SM+ScFuFFN | 3.48 | 1.8B | 7.7B | 6.43 | 4.76 | 3.94x | 1.72x |
| <span style="background-color:#CCFFCC;">EReg(SM(t)+ScFuFFN)</span> | <span style="background-color:#CCFFCC;">SM: 144×ℝ<sup>128×128</sup></span> | <span style="background-color:#CCFFCC;">3.21</span> | <span style="background-color:#CCFFCC;">1.8B</span> | <span style="background-color:#CCFFCC;">7.7B</span> | <span style="background-color:#CCFFCC;">6.43</span> | <span style="background-color:#CCFFCC;">4.76</span> | <span style="background-color:#CCFFCC;">3.94x</span> | <span style="background-color:#CCFFCC;">1.72x</span> |{{< /table-caption >}}
> 🔼 표 (b)는 CodeParrot 데이터셋에서 과소선형화된 GPT-2 (small) 모델의 손실 곡선을 보여줍니다.  x축은 에포크(epoch)이고 y축은 평가 손실(eval loss)입니다.  여러 가지 비선형성 구성(예: Softmax + LayerNorm + GELU, Softmax + LayerNorm + ReLU 등)에 따른 손실 값의 변화를 시각적으로 나타내어, 각 구성의 학습 안정성과 효율성을 비교 분석하는 데 활용됩니다.  다양한 비선형성 구성을 적용했을 때 손실이 어떻게 감소하는지, 즉 모델이 데이터에 얼마나 잘 적응하는지를 보여주는 지표입니다. 특히, 비선형성을 줄였을 때 손실이 어떻게 변하는지에 대한 중요한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> (b) Loss curve
> </details>

{{< table-caption >}}
| Network Arch. | Eval PPL (1.2B) | Eval PPL (2.4B) | Eval PPL (4.8B) | #Nonlinear Ops | #FLOPs (FFN) | #FLOPs (Attn.) | Comm. (GB) | Lat. (min.) | 
|---|---|---|---|---|---|---|---|---|
| Baseline <br> SM+LN+G | 25.71 | 23.32 | 21.29 | SM: 144×ℝ⁵¹²ˣ⁵¹² <br> LN: 24×ℝ⁵¹²ˣ⁷⁶⁸ <br> G: 12×ℝ⁵¹²ˣ³⁰⁷² | 58.0B | 36.2B | 145.24 | 30.74 |
| SM+LN+R | 26.06 | 23.55 | 21.58 | SM: 144×ℝ⁵¹²ˣ⁵¹² <br> LN: 24×ℝ⁵¹²ˣ⁷⁶⁸ <br> R: 12×ℝ⁵¹²ˣ³⁰⁷² | 58.0B | 36.2B | 81.71 | 23.54 |
| SM+ScFuFFN | 33.77 | 30.82 | 28.59 | SM: 144×ℝ⁵¹²ˣ⁵¹² | 7.3B | 36.2B | 69.68 | 19.44 |
| EReg(SM(t)+ScFuFFN) | 31.54 | 28.70 | 26.55 | SM: 144×ℝ⁵¹²ˣ⁵¹² | 7.3B | 36.2B | 69.68 | 19.44 |{{< /table-caption >}}
> 🔼 표 2는 CodeParrot 데이터셋(21억 토큰, 문맥 길이 128)에서 처음부터 학습된 GPT-2 모델(레이어 12개, 헤드 12개, 차원 768)의 결과를 보여줍니다.  각 모델 아키텍처(SM+LN+G, SM+LN+R, SM+LN, SM+G, SM+R, SM) 별로 perplexity, 비선형 연산 수,  통신량(GB), 지연 시간(분) 등을 비교하여  각 아키텍처의 효율성을 평가합니다.  특히,  비선형 연산 감소를 통한 효율성 개선에 초점을 맞추고 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Results on GPT-2 (L𝐿Litalic_L=12, H𝐻Hitalic_H=12, d𝑑ditalic_d=768), trained from scratch on the CodeParrot dataset (2.1B tokens, T𝑇Titalic_T=128).
> </details>

{{< table-caption >}}
| Linear layers | Eval PPL(Weight Normalization) | Eval PPL(Spectral Normalization) |
|---|---|---|
| QK | 3.89 | 4.25 |
| FFN | 3.64 | 3.63 |
| QK+FFN | 3.88 | 4.23 |
| QKV+FFN | 3.93 | 4.26 |
| QKVO+FFN | 3.98 | 4.34 |{{< /table-caption >}}
> 🔼 이 표는 CodeParrot 데이터셋이 아닌 Languini 데이터셋(20억 토큰, 문맥 길이 512)을 사용하여 처음부터 학습시킨 GPT-2 모델 (12 레이어, 12 헤드, 차원 768)에 대한 결과를 보여줍니다.  다양한 비선형 연산(Softmax, LayerNorm, GELU, ReLU)의 조합을 가진 여러 모델 아키텍처의 성능을 퍼플렉서티(PPL), 비선형 연산 수, FLOPs, 통신량(GB), 지연 시간(분)으로 비교합니다. 특히, 엔트로피 규제 기법을 적용한 Softmax-only 모델의 효율성을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Results on GPT-2 (L𝐿Litalic_L=12, H𝐻Hitalic_H=12, d𝑑ditalic_d=768) model, trained from scratch on Languini [20] (T𝑇Titalic_T=512)
> </details>

{{< table-caption >}}
| Weight Normalization | Spectral Normalization | Scaled-FFN |
|---|---|---|
| Eval PPL | 3.640 | 3.624 | 3.478 |{{< /table-caption >}}
> 🔼 이 표는 Softmax-only GPT-2 모델(12개 레이어, 12개 헤드, 768차원)에 가중치 정규화와 스펙트럼 정규화를 적용했을 때의 성능을 비교한 것입니다. CodeParrot 데이터셋(128개 입력 컨텍스트 길이)에서 학습된 모델을 사용했습니다. FFN(Feed-Forward Network) 레이어에 가중치 정규화를 적용했을 때와 다른 선형 레이어에 가중치 정규화를 적용했을 때의 성능 차이를 보여줍니다. 가중치 정규화는 FFN 레이어에서 비슷한 결과를 보였지만 다른 선형 레이어에서는 더 나은 성능을 보였습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Comparison of weight normalization [17] and spectral normalization [18] when employed in Softmax-only GPT-2 (L𝐿Litalic_L=12, H𝐻Hitalic_H=12, d𝑑ditalic_d=768) models, and trained from scratch on CodeParrot dataset with 128 input context length. FFN weight normalization yield the similar results; whereas, weight normalization works better in other linear layers.
> </details>

{{< table-caption >}}
|       | Network Arch. | PPL | #Nonlinear Ops | FFN #FLOPs | Attn. #FLOPs | Comm.(GB) | Lat.(min.) | Comm. Savings | Lat. Savings |
| :----: | :---------------: | :-: | :-------------: | :----------: | :----------: | :--------: | :---------: | :-------------: | :-------------: |
| Baseline | <math>{
umeric{SM+LN+G}}</math> | 2.35 | SM: <math>144 \times \mathbb{R}^{256 \times 256}</math><br>LN: <math>24 \times \mathbb{R}^{256 \times 768}</math><br>G: <math>12 \times \mathbb{R}^{256 \times 3072}</math> | 29.0B | 16.3B | 58.51 | 16.57 | 1<math>\times</math> | 1<math>\times</math> |
|       | <math>{
umeric{SM+LN+R}}</math> | 2.41 | SM: <math>144 \times \mathbb{R}^{256 \times 256}</math><br>LN: <math>24 \times \mathbb{R}^{256 \times 768}</math><br>R: <math>12 \times \mathbb{R}^{256 \times 3072}</math> | 29.0B | 16.3B | 26.73 | 12.59 | 2.19<math>\times</math> | 1.32<math>\times</math> |
|       | <math>{
umeric{SM+ScFuFFN}}</math> | 3.03 | SM: <math>144 \times \mathbb{R}^{256 \times 256}</math> | 3.6B | 16.3B | 20.72 | 10.45 | 2.82<math>\times</math> | 1.59<math>\times</math> |
|       | <math>\text{EReg}({\tt SM(t)+ScFuFFN})</math> | 2.92 | SM: <math>144 \times \mathbb{R}^{256 \times 256}</math> | 3.6B | 16.3B | 20.72 | 10.45 | 2.82<math>\times</math> | 1.59<math>\times</math> |{{< /table-caption >}}
> 🔼 이 표는 CodeParrot 데이터셋에서 학습된 Softmax-only GPT-2 모델의 FFN(Feed-Forward Network) 부분에 적용된 가중치 정규화, 스펙트럼 정규화, 그리고 학습 가능한 스케일링 기법들의 성능 비교 결과를 보여줍니다. 입력 문맥 길이가 128 토큰인 경우의 perplexity 값을 비교하여 각 기법의 효과를 분석합니다.  즉, 비선형성을 줄인 Transformer 모델에서 다양한 정규화 기법이 성능에 미치는 영향을 정량적으로 보여주는 표입니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Perplexity comparison of weight normalization, spectral normalization, and learnable scaling employed in FFN of softmax-only GPT-2 model, when trained from scratch on CodeParrot dataset with 128 input context length.
> </details>

{{< table-caption >}}
|---|---|---|---|---|---|---|---|
| **Baseline** | Network Arch. | PPL | #Nonlinear Ops | FFN | Attn. | Comm. (GB) | Lat. (min.) | Savings |
|---|:---|:---:|:---|:---:|:---:|:---:|:---:|:---:|
| <img src="https://arxiv.org/html/2501.03489/A3.T7.12.4.4.5.1.1.1.1.1.png" style="width:5.7pt;height:36pt;vertical-align:-14.5pt;transform:rotate(-90deg);" /> | SM+LN+G | 2.56 | 21.7B | 11.6B | 37.17 | 10.77 | 1× | 1× |
|  | SM: 216×ℝ<sup>128×128</sup> |  |  |  |  |  |  |  |
|  | LN: 36×ℝ<sup>128×768</sup> |  |  |  |  |  |  |  |
|  | G: 18×ℝ<sup>128×3072</sup> |  |  |  |  |  |  |  |
|  | SM+LN+R | 2.63 | 21.7B | 11.6B | 13.34 | 8.04 | 2.79× | 1.34× |
|  | SM: 216×ℝ<sup>128×128</sup> |  |  |  |  |  |  |  |
|  | LN: 36×ℝ<sup>128×768</sup> |  |  |  |  |  |  |  |
|  | R: 18×ℝ<sup>128×3072</sup> |  |  |  |  |  |  |  |
|  | SM+ScFuFFN | 3.24 | 2.7B | 11.6B | 8.83 | 6.07 | 4.21× | 1.77× |
|  | <span style="background-color:#CCFFCC;">EReg(SM(t)+ScFuFFN)</span> | <span style="background-color:#CCFFCC;">3.13</span> | <span style="background-color:#CCFFCC;">2.7B</span> | <span style="background-color:#CCFFCC;">11.6B</span> | <span style="background-color:#CCFFCC;">8.83</span> | <span style="background-color:#CCFFCC;">6.07</span> | <span style="background-color:#CCFFCC;">4.21×</span> | <span style="background-color:#CCFFCC;">1.77×</span> |
{{< /table-caption >}}
> 🔼 표 6은 CodeParrot 데이터셋(21억 토큰, T=256)에서 처음부터 학습된 GPT-2 모델(L=12, H=12, d=768)에 대한 결과를 보여줍니다.  다양한 비선형성 구성(Softmax, Layer Normalization, GELU, ReLU 사용 여부 등)에 따른 perplexity, 비선형 연산 수, 통신량, 지연 시간 등을 비교 분석하여, 제안된 엔트로피 기반 방법의 효율성을 보여주는 표입니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Results on GPT-2 (L𝐿Litalic_L=12, H𝐻Hitalic_H=12, d𝑑ditalic_d=768), trained from scratch on the CodeParrot dataset (2.1B tokens, T𝑇Titalic_T=256).
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