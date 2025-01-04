---
title: "Understanding and Mitigating Bottlenecks of State Space Models through the Lens of Recency and Over-smoothing"
summary: "심층 신경망의 장기 의존성을 모델링하는 구조적 상태 공간 모델(SSM)의 한계를 극복!  최신 연구에서 SSM의 **최근 편향(recency bias)** 및 **과도한 평활화(over-smoothing)** 문제를 규명하고, 이를 해결하는 **극성화 기법(polarization)**을 제시하여 장기 토큰 상관관계 정확도를 높였습니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 University of Texas at Austin",]
showSummary: true
date: 2024-12-31
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.00658 {{< /keyword >}}
{{< keyword icon="writer" >}} Peihao Wang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-03 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.00658" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.00658" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

본 논문은 장기 의존성을 잘 포착하는 것으로 여겨지는 구조적 상태 공간 모델(SSM)이 실제로는 **'최근 편향(recency bias)'** 문제로 인해 먼 과거 정보를 잘 기억하지 못하고, **견고성 문제**까지 발생시킨다는 점을 밝힙니다.  또한, SSM의 깊이를 늘리면 장기 문맥 학습에는 도움이 되지만, **'과도한 평활화(over-smoothing)'** 문제가 발생하여 토큰 표현이 서로 구분하기 어려워지는 문제점도 제기합니다. 이는 SSM의 확장성을 제한하는 근본적인 문제입니다. 



이러한 문제를 해결하기 위해 연구팀은 **'극성화(polarization)'**라는 새로운 기법을 제안합니다. 이 기법은 상태 전이 행렬의 두 채널을 0과 1로 설정하여 최근 편향과 과도한 평활화 문제를 동시에 해결합니다. 실험 결과, 이 기법은 장기 토큰의 상관 관계 재현 정확도를 향상시키고 더 깊은 구조의 SSM에서도 성능 향상을 가져왔음을 보여줍니다.  이 연구는 SSM의 한계를 극복하고 성능을 향상시키는 데 기여하며, 향후 연구를 위한 새로운 방향을 제시합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 구조적 상태 공간 모델(SSM)은 본질적으로 최근 편향(recency bias)과 과도한 평활화(over-smoothing) 문제를 지닌다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 제안된 극성화 기법(polarization)은 최근 편향과 과도한 평활화 문제를 동시에 해결하여 장기 토큰 상관관계 정확도를 향상시킨다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 심층 SSM 아키텍처의 확장성을 제한하는 주요 병목 현상에 대한 이해 증진 및 해결 방안 제시 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **장기 의존성을 효과적으로 모델링하는 데 있어 구조적 상태 공간 모델(SSM)의 두 가지 근본적인 한계점**을 밝히고, 이를 해결하기 위한 새로운 방법론을 제시함으로써 **SSM의 확장성을 제한하는 주요 병목 현상을 이해하고 완화**하는 데 중요한 의미를 지닙니다.  이는 현재 딥러닝 분야에서 활발하게 연구되고 있는 **장기 의존성 모델링 및 모델의 견고성 향상**에 직접적으로 기여하며, 관련 연구자들에게 새로운 연구 방향을 제시합니다. 또한, **적대적 공격에 대한 취약성을 다루는 SSM의 견고성 문제**는 실제 응용 프로그램에서 SSM의 안전성과 신뢰성을 높이는 데 중요한 이슈이므로, 본 논문의 결과는 이러한 문제를 해결하는 데 도움이 될 것입니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.00658/x1.png)

> 🔼 그림 1은 SSM(Structured State Space Model)에서 토큰 간의 영향력 점수를 시각화한 것입니다.  세로축은 토큰 s와 토큰 t 사이의 영향력 점수 (log|∂yt/∂xs|)의 로그 값을 나타내고, 가로축은 두 토큰 사이의 거리 (t-s)를 나타냅니다.  이 그래프는 SSM이 시간적으로 가까운 토큰들에 더 큰 영향을 받는, 즉 최근 정보에 치우친(recency bias) 경향이 있음을 보여줍니다. 여러 모델 크기(1.3억, 14억 파라미터)에 걸쳐, 영향력 점수는 거리에 따라 기하급수적으로 감소하는 것을 확인할 수 있으며, 이는 이러한 경향이 모델 구조 자체에 내재된 특성임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Visualization of log influential scores log⁡|∂𝒚t/∂𝒙s|subscript𝒚𝑡subscript𝒙𝑠\log|\partial\bm{y}_{t}/\partial\bm{x}_{s}|roman_log | ∂ bold_italic_y start_POSTSUBSCRIPT italic_t end_POSTSUBSCRIPT / ∂ bold_italic_x start_POSTSUBSCRIPT italic_s end_POSTSUBSCRIPT | versus distance (t−s)𝑡𝑠(t-s)( italic_t - italic_s ).
> </details>





{{< table-caption >}}
| Models | (no corrupt) | [992:1024] | [0:32] | [928:1024] | [0:96] |
|---|---|---|---|---|---| 
| H3 | 0.654 | 0.569 (<span>↓</span> 13.04%) | 0.654 (<span>↓</span> 0.03%) | 0.477 (<span>↓</span> 27.07%) | 0.650 (<span>↓</span> 0.72%) |
| Transformer | 0.580 | 0.535 (<span>↓</span> 7.81%) | 0.447 (<span>↓</span> 22.95%) | 0.431 (<span>↓</span> 25.76%) | 0.370 (<span>↓</span> 36.32%) |
| RWKV | 0.474 | 0.150 (<span>↓</span> 68.35%) | 0.466 (<span>↓</span> 1.58%) | 0.138 (<span>↓</span> 70.88%) | 0.460 (<span>↓</span> 2.91%) |
| Mamba | 0.674 | 0.126 (<span>↓</span> 81.24%) | 0.658 (<span>↓</span> 2.30%) | 0.098 (<span>↓</span> 85.46%) | 0.647 (<span>↓</span> 3.98%) |{{< /table-caption >}}

> 🔼 표 1은 CIFAR-10 데이터셋에서 적대적 공격 실험 결과를 보여줍니다. 분류 정확도를 평가 지표로 사용했습니다. 각 입력 시퀀스는 1,024개의 토큰으로 구성됩니다. 선두 및 후미 토큰을 각각 변경하기 위해 두 가지 손상 비율(32/1024 및 96/1024)을 적용했습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Results of adversarial attack experiments on the CIFAR-10 dataset, evaluated using classification accuracy. Each input sequence contains 1,024 tokens. Two corruption ratios (32/102432102432/102432 / 1024 and 96/102496102496/102496 / 1024) are applied to perturb the leading and trailing tokens, respectively.
> </details>





### In-depth insights


#### SSM Recency Bias
본 논문은 순환 상태 공간 모델(SSM)의 근본적인 한계점인 **최근 편향(Recency Bias)**을 심층적으로 분석합니다.  SSM은 장기 의존성을 포착하는 데 효과적이라고 여겨지지만, 실제로는 최근 정보에 과도하게 의존하는 경향이 있음을 보여줍니다. 이러한 편향은 모델의 **원거리 정보 재현 능력을 저해**하고, **모델의 견고성에 문제**를 야기합니다.  **깊은 구조의 SSM은 장기 문맥 학습에 도움이 될 수 있지만**, 깊이가 깊어짐에 따라 토큰 표현이 서로 구분되지 않는 **과도한 평활화(Over-smoothing)** 현상이 발생합니다.  이러한 최근 편향과 과도한 평활화 사이의 상충관계는 기존 SSM의 확장성을 저해하는 주요 요인으로 제시됩니다. 논문은 이러한 문제를 해결하기 위해 상태 전이 행렬의 채널을 양극화하는 기법을 제안하여 **최근 편향과 과도한 평활화를 동시에 완화**시키고, 장기 토큰의 연관성 재현 정확도를 향상시킵니다.

#### Over-Smoothing Effect
본 논문에서 다룬 "과도한 평활화 효과(Over-Smoothing Effect)"는 **심층 신경망, 특히 순환 신경망(RNN) 기반의 상태 공간 모델(SSM)에서 나타나는 현상**입니다.  깊이가 깊어짐에 따라 토큰 표현이 점점 구분이 어려워지는 현상으로, **장기 의존성을 포착하는 SSM의 능력을 저해**합니다.  이는 SSM이 본질적으로 **평활화 연산자(smoothing operator)** 역할을 하기 때문이며, 깊은 구조에서는 **고주파 성분(high-frequency components)**이 제거되어 토큰 표현의 **선명도(sharpness)**가 감소하고 **과도한 일반화(over-generalization)**가 발생합니다.  **깊이 확장(depth scaling)**을 통해 장기 의존성을 개선하려는 시도에도 불구하고, 과도한 평활화는 성능 향상에 제한을 가합니다.  **극성화 기법(polarization technique)**과 같은 해결책을 통해 이러한 문제를 완화할 수 있지만, 이는 SSM의 근본적인 한계를 완전히 해결하지는 못합니다. 따라서 **SSM의 확장성을 제한하는 주요 병목 현상**으로 인식되어야 합니다.

#### Polarization Approach
본 논문에서 제시된 극성 접근 방식은 **장기 의존성을 효과적으로 모델링하는 데 있어 SSM(구조화된 상태 공간 모델)의 고질적인 문제점인 최근 편향과 과도한 평활화를 동시에 해결하기 위한 혁신적인 방법**입니다.  이는 SSM의 상태 천이 행렬에 두 개의 채널을 할당하여, 하나는 항상 0으로, 다른 하나는 1로 설정하는 방식으로 이루어집니다.  **0 채널은 최근 편향을 완화하여 과거 정보의 손실을 방지하고, 1 채널은 과도한 평활화를 억제하여 토큰 표현의 구별성을 유지**합니다. 이러한 극성화 기법은 장거리 토큰의 연관성 회상 정확도를 일관되게 향상시키고, 보다 깊은 아키텍처에서 SSM의 성능 향상을 가능하게 합니다.  **본 논문의 핵심은 단순한 기술적 개선이 아닌, SSM의 근본적인 한계를 밝히고 이를 해결하기 위한 이론적 토대를 마련했다는 점**입니다. 이를 통해 SSM의 확장성을 크게 높였을 뿐만 아니라, 향후 더욱 발전된 SSM 모델 개발에 중요한 지침을 제시하고 있습니다.  **극성 접근 방식은 이론적 근거와 실험적 증거 모두를 바탕으로 제시되었기 때문에, 그 신뢰성과 실용성이 매우 높다**고 평가할 수 있습니다.

#### Depth Scaling Limits
본 논문에서 다룬 심층 신경망(DNN)의 성능 저하 현상 중 하나는 **심도 확장의 한계**입니다.  모델의 깊이를 늘리는 것은 장기 의존성을 포착하는 데 도움이 될 수 있지만, 특정 깊이를 넘어서면 **과도한 평활화(over-smoothing)**로 인해 토큰 표현이 서로 구분되지 않게 되고, 성능이 오히려 감소하는 현상이 발생합니다. 이러한 현상은 이론적 분석과 실험적 결과를 통해 입증되었으며, **심도 확장 전략의 효과적인 적용에는 한계가 있음**을 시사합니다.  **과도한 평활화를 완화**하고 심도 확장의 이점을 최대한 활용하기 위한 추가적인 전략과 기법에 대한 연구가 필요함을 강조합니다.  특히, **깊이와 너비의 균형있는 확장**을 고려하여 성능 저하를 막는 연구가 필요합니다.  또한, **모델 구조의 최적화**를 통해 심도 확장의 한계를 극복하고자 하는 시도가 더욱 중요해지고 있습니다.

#### Future Research
미래 연구 방향으로는 **SSMs의 과도한 평활화 문제를 완화하는 새로운 기법**을 연구하는 것이 중요합니다. 본 논문에서 제시된 편극화 기법은 효과적이지만, 더욱 정교하고 효율적인 방법을 모색할 필요가 있습니다. 또한, **SSMs의 국소적 편향성을 근본적으로 해결**하는 새로운 모델 아키텍처를 설계하는 연구도 필요합니다.  **장기 의존성을 효과적으로 포착**하면서도 계산 비용을 줄이는 효율적인 메커니즘을 개발하는 것도 중요한 과제입니다.  **다양한 하드웨어 플랫폼에서의 성능 최적화** 연구도 필요하며, 특히,  **메모리 효율성을 높이는 기법** 개발을 통해 SSMs의 확장성을 제고해야 합니다. 마지막으로, **SSMs의 견고성을 향상**시키는 연구가 필요합니다.  본 논문에서 제시된 적대적 공격에 대한 취약성 분석 결과를 바탕으로, 보다 강력한 방어 메커니즘을 개발해야 합니다.  이러한 노력을 통해 SSMs의 한계를 극복하고, 더욱 강력하고 효율적인 시퀀스 처리 아키텍처를 구축하는데 기여할 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.00658/x4.png)

> 🔼 그림 2는 '건초더미 속 바늘 찾기' 벤치마크에서 SSM(Structured State Space Model)과 Transformer의 성능을 비교한 것입니다. 왼쪽 그림은 Mamba-Codestral-7B 모델의 검색 정확도를, 오른쪽 그림은 Mistral-7B 모델의 검색 정확도를 히트맵으로 나타낸 것입니다. 히트맵에서 '전체 문맥 길이'는 문서의 전체 길이를, '바늘 위치'는 검색할 문장이 문맥 내에서 상대적으로 어디에 위치하는지를 나타냅니다. Appendix E.2에서는 보다 자세한 시각화 자료를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Comparison between SSM and Transformer on the “Needle in a Haystack' benchmark. The left figure shows the retrieval accuracy of the Mamba-Codestral-7B model, while the right figure presents the retrieval accuracy of the Mistral-7B model. We present a heatmap where 'full context length' refers to the total length of the document, and 'needle position' denotes the relative position of the statement to be retrieved within the context. See more fine-grained visualization in Appendix E.2.
> </details>



![](https://arxiv.org/html/2501.00658/x5.png)

> 🔼 그림 3은 CIFAR-10 데이터셋에서 대상 공격 실험의 결과를 보여줍니다. (a)와 (b)는 두 가지 다른 공격 비율(25%, 47%)에서의 대상 공격 성공률을 보여줍니다. 성공률이 낮을수록 해당 공격 영역에서 모델의 강건성이 높다는 것을 의미합니다. 그림에서 볼 수 있듯이, SSM 계열 모델은 후행 토큰에 대한 공격에 훨씬 취약하며, 특히 Mamba 모델의 경우 후행 토큰의 일부를 변경하는 것만으로도 분류 정확도가 크게 저하됨을 보여줍니다. 이는 SSM 모델이 최근 정보에 치우친 경향이 있음을 보여주는 강력한 증거입니다.
> <details>
> <summary>read the caption</summary>
> (a) Attack ratio = 256/1024⁢(25.00%)2561024percent25.00256/1024~{}~{}(25.00\%)256 / 1024 ( 25.00 % )
> </details>



![](https://arxiv.org/html/2501.00658/x8.png)

> 🔼 이 그림은 CIFAR-10 데이터셋에서의 표적 공격 실험 결과를 보여줍니다. 그림 (b)는 입력 시퀀스의 480/1024 (약 46.875%)의 토큰을 표적 클래스의 픽셀로 대체했을 때, 각 모델의 성공률을 보여줍니다.  표적 공격은 특정 클래스(예: 말)의 픽셀을 다른 클래스의 이미지에 추가하여 모델이 잘못 분류하도록 유도하는 방식입니다. 그림은 선두 및 후미 토큰에 대한 공격 성공률을 비교하여, SSM(State Space Model) 기반 모델의 취약성을 강조합니다. SSM 모델은 후미 토큰에 대한 공격에 더 취약한 반면, 트랜스포머 모델은 선두 및 후미 토큰에 대해 유사한 수준의 강건성을 보여줍니다. 이는 SSM 모델의 국소적 편향성으로 인해 발생하는 현상입니다.
> <details>
> <summary>read the caption</summary>
> (b) Attack ratio = 480/1024⁢(46.875%)4801024percent46.875480/1024~{}~{}(46.875\%)480 / 1024 ( 46.875 % )
> </details>



![](https://arxiv.org/html/2501.00658/x9.png)

> 🔼 그림 3은 말 이미지를 표적으로 한 CIFAR-10 데이터셋에 대한 표적 공격 실험 결과를 보여줍니다. 그림 (a)와 (b)는 두 가지 다른 공격 비율(공격 픽셀 비율) 하에서의 표적 공격 성공률을 나타냅니다. 성공률이 낮을수록 해당 영역에서 모델의 강건성이 높다는 것을 의미합니다. 즉, 그림은 SSM(Structured State Space Model) 기반 모델이 입력 데이터의 앞부분보다는 뒷부분에 더 취약하다는 것을 보여주는 실험 결과를 시각적으로 보여줍니다. 이는 SSM 모델의 국소적인 편향(locality bias)으로 인해 발생하는 현상임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Results of target attack experiments on CIFAR-10, where “horse” is the target class. (a) and (b) present target attack success rates under two attack ratios. Lower success rates suggest higher robustness in the corresponding attack regions.
> </details>



![](https://arxiv.org/html/2501.00658/x10.png)

> 🔼 본 그림은 문맥 길이가 증가함에 따라 더 깊은 모델이 점점 더 유리해짐을 실험적으로 보여줍니다. 그러나 특정 깊이를 넘어서면 SSM의 성능이 정체되기 시작하여 결국 감소하는 것을 보여줍니다.  이러한 현상은 모델의 깊이가 증가함에 따라 발생하는 과도한 평활화 현상(over-smoothing) 때문에 발생할 수 있습니다.  깊은 모델은 장기 의존성을 포착하는 데 더 효과적일 수 있지만, 너무 깊어지면 토큰 표현이 구별이 어려워지고 성능이 저하될 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: We empirically observe that deeper models become increasingly advantageous as the context length grows. However, beyond a certain depth, the performance of SSMs begins to plateau and eventually declines.
> </details>



![](https://arxiv.org/html/2501.00658/x11.png)

> 🔼 그림 5는 사전 훈련된 Mamba와 Pythia 모델에서 각 계층에 걸쳐 특징의 부드러움(smoothness)을 시각화한 것입니다. 세로축은 토큰 간의 평균 쌍방향 차이를 나타내며, 가로축은 계층의 깊이를 나타냅니다. (a)는 Mamba 또는 어텐션 모듈만을 고려한 믹서 출력(Mixer output), (b)는 다른 모든 구성 요소(예: MLP)를 포함한 블록 출력(Block output)을 보여줍니다.  Mamba의 경우, 입력 토큰의 예리함이 메모리 상태 출력보다 일관되게 높은 것을 알 수 있습니다.  또한, 믹서 출력과 블록 출력 모두 계층이 깊어짐에 따라 예리함이 급격히 감소하는 경향이 있습니다.  반면, 트랜스포머는 특징의 부드러움이 더 느리게 감소합니다.
> <details>
> <summary>read the caption</summary>
> (a) 𝒃tsubscript𝒃𝑡\bm{b}_{t}bold_italic_b start_POSTSUBSCRIPT italic_t end_POSTSUBSCRIPT and 𝒉tsubscript𝒉𝑡\bm{h}_{t}bold_italic_h start_POSTSUBSCRIPT italic_t end_POSTSUBSCRIPT.
> </details>



![](https://arxiv.org/html/2501.00658/x12.png)

> 🔼 그림 5(b)는 Mamba 모델의 믹서(Mixer) 모듈 출력에서 토큰 특징의 평활도(smoothness)를 보여줍니다.  y축은 토큰 간의 평균 쌍별 차이를 나타내며,  x축은 레이어의 깊이를 나타냅니다.  믹서 모듈은 Mamba 모델의 어텐션 메커니즘 부분만을 나타냅니다.  이 그래프는 Mamba 모델의 깊이가 증가함에 따라 토큰 표현의 유사성이 어떻게 증가하는지(즉, 과도한 평활화 현상) 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) Mixer output.
> </details>



![](https://arxiv.org/html/2501.00658/x13.png)

> 🔼 그림 5는 사전 훈련된 Mamba 및 Pythia 모델에서 각 계층에 걸쳐 특징의 부드러움을 시각화한 것입니다. y축은 토큰 간 평균 쌍별 차이를 나타내며, 믹서 출력(b)은 Mamba 또는 어텐션 모듈만 고려하고, 블록 출력(c)은 다른 모든 구성 요소(예: MLP)를 포함합니다.  블록 출력은 전체 모델의 출력을 나타내므로, 믹서 출력과 비교하여 모델의 부드러움 변화를 더 정확히 파악할 수 있습니다.  특히, 깊이가 증가함에 따라 특징의 부드러움이 감소하는 현상을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (c) Block output.
> </details>



![](https://arxiv.org/html/2501.00658/x14.png)

> 🔼 이 그림은 사전 훈련된 Mamba와 Pythia 모델에서 각 계층의 특징 매끄러움을 시각화한 것입니다. y축은 토큰 간의 평균적인 쌍방향 차이를 나타냅니다. (b)의 믹서 출력은 Mamba 또는 어텐션 모듈만을 고려하는 반면, (c)의 블록 출력은 다른 모든 구성 요소(예: MLP)를 포함합니다.  이 그림은 모델의 깊이가 깊어짐에 따라 토큰 표현이 얼마나 유사해지는지(즉, 과도한 평활화 현상)을 보여줍니다.  믹서 출력과 블록 출력을 비교하여 어텐션 메커니즘 자체와 MLP와 같은 다른 구성 요소의 영향을 분리하여 분석합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Visualization of feature smoothness across layers in pre-trained Mamba and Pythia. The y-axis represents the average pairwise differences among tokens. Mixer outputs (b) solely consider the Mamba or attention module, while Block outputs (c) include all other components (e.g., MLP).
> </details>



![](https://arxiv.org/html/2501.00658/x17.png)

> 🔼 그림 6은 SSM(Structured State Space Model)의 상태 전이 행렬 A의 최대 고유값(A_max)과 최소 고유값(A_min)의 차이 (A_max - A_min)의 누적 분포를 보여줍니다. 각 구간(bin)의 높이는 (A_max - A_min)이 x축의 해당 값보다 작거나 같은 채널의 비율을 나타냅니다. 이 그림은 SSM에서 과도한 평활화(over-smoothing) 현상을 설명하기 위해 제시되었으며,  대부분의 채널에서 A_max와 A_min의 차이가 0.5보다 작다는 것을 보여줌으로써,  SSM이 동시에 국소 편향(recency bias)과 과도한 평활화 문제를 완화하기 어려움을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Cumulative histogram of (Am⁢a⁢x−Am⁢i⁢n)subscript𝐴𝑚𝑎𝑥subscript𝐴𝑚𝑖𝑛(A_{max}-A_{min})( italic_A start_POSTSUBSCRIPT italic_m italic_a italic_x end_POSTSUBSCRIPT - italic_A start_POSTSUBSCRIPT italic_m italic_i italic_n end_POSTSUBSCRIPT ). The height of each bin represents the cumulative proportion of (Am⁢a⁢x−Am⁢i⁢n)subscript𝐴𝑚𝑎𝑥subscript𝐴𝑚𝑖𝑛(A_{max}-A_{min})( italic_A start_POSTSUBSCRIPT italic_m italic_a italic_x end_POSTSUBSCRIPT - italic_A start_POSTSUBSCRIPT italic_m italic_i italic_n end_POSTSUBSCRIPT ) less than or equal to the corresponding value on the x-axis.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Configurations | # Layers | # KV Pairs |  |  | Avg. |
|---|---|---|---|---|---| 
|  |  | 64 | 128 | 256 |  |
| Default 𝑨t | 2 | 98.38 | 81.81 | 36.00 | 72.06 |
| Default 𝑨t | 4 | 99.23 | 82.08 | 33.52 | 71.61 |
| (𝑨t)1,1=1 | 2 | 99.81 | 94.70 | 56.39 | 83.63 |
| (𝑨t)N,N=0 | 2 | 98.41 | 81.35 | 36.55 | 72.10 |
| (𝑨t)N,N=0 | 4 | 99.74 | 92.20 | 52.21 | 81.38 |
| (𝑨t)1,1=1,(𝑨t)N,N=0 | 2 | 99.23 | 95.54 | 54.74 | 83.17 |
| (𝑨t)1,1=1,(𝑨t)N,N=0 | 4 | 99.94 | 98.80 | 81.56 | 93.43 |{{< /table-caption >}}
> 🔼 표 2는 제안된 편극 기법의 효과를 보여줍니다. 1-2행은 편극이 없는 기본 Mamba 모델의 결과를, 3-5행은 채널 하나에만 0 또는 1을 적용한 편극 모델의 결과를, 6-7행은 두 채널 모두에 0과 1을 적용한 편극 모델의 결과를 보여줍니다.  다양한 레이어 수와 키-값 쌍의 수에 따른 성능 변화를 비교하여 편극 기법이 어떻게 성능을 향상시키는지 보여줍니다. 특히, 두 채널 모두 편극된 모델이 가장 좋은 성능을 보이는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Results of polarization. Rows 1-2 have no polarization, rows 3-5 only polarize one channel to either one or zero, and rows 6-7 polarize both channels.
> </details>

{{< table-caption >}}
| Models | (no corrupt) | [1014:1024] | [0:10] | [768:1024] | [0:256] | [512:544] | [480:576] |
|---|---|---|---|---|---|---|---| 
| H3 | 0.654 | 0.629 | 0.654 | 0.394 | 0.639 | 0.603 | 0.543 |
| Transformer | 0.580 | 0.571 | 0.500 | 0.249 | 0.263 | 0.498 | 0.347 |
| RWKV | 0.474 | **0.194** | 0.470 | **0.107** | 0.448 | 0.405 | 0.392 |
| Mamba | 0.674 | 0.348 | 0.664 | **0.099** | 0.597 | 0.515 | 0.446 |{{< /table-caption >}}
> 🔼 표 3은 CIFAR-10 데이터셋에서 적대적 공격 실험의 확장된 결과를 보여줍니다.  각 모델에 대해 입력 시퀀스의 선두 및 후미 토큰에 다양한 비율(32/1024, 96/1024)의 잡음을 추가하여 적대적 공격을 수행했습니다.  표는 각 모델의 기본 정확도와 선두 및 후미 토큰이 손상된 경우의 정확도를 보여줍니다.  이를 통해 각 모델의 견고성과 지역 편향성에 대한 통찰력을 제공합니다. 특히, 후미 토큰이 손상될 때 Mamba 모델의 성능 저하가 크게 나타나는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Extended results of adversarial attack experiments on the CIFAR-10 dataset. Classification accuracy is used as the metric.
> </details>

{{< table-caption >}}
| # Params | Training steps | Peak LR | Batch Size (in tokens) | # Tokens |
|---|---|---|---|---|
| 100-250M | 4800 | 3e-3 | 0.5M | 2.5B |
| 250-400M | 13500 | 1.5e-3 | 0.5M | 7B |
| 400-550M | 20000 | 1.25e-3 | 0.5M | 10B |{{< /table-caption >}}
> 🔼 표 4는 다양한 크기의 Mamba 모델에 대한 훈련 설정을 요약한 표입니다.  Chinchilla 법칙 (Hoffmann et al., 2022)과 Gu & Dao (2023)의 연구를 기반으로 설정되었습니다.  표에는 매개변수 수, 훈련 단계, 최대 학습률, 배치 크기(토큰 수), 그리고 토큰 수 등의 정보가 포함되어 있습니다. 이러한 설정은 모델 크기에 따라 조정되어 모델의 성능을 최적화하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Summary of training settings for varying-sized Mamba. The settings are following Chinchilla law (Hoffmann et al., 2022) and consistent with Gu & Dao (2023).
> </details>

{{< table-caption >}}
| Configurations | # Layers | Recency | Over-smoothing | # KV Pairs 64 | # KV Pairs 128 | # KV Pairs 256 | Avg. | 
|---|---|---|---|---|---|---|---| 
| Default <b>A</b><sub>t</sub> | 2 | https://arxiv.org/html/2501.00658/A5.T5.2.2.2.2.pic1.png | https://arxiv.org/html/2501.00658/A5.T5.3.3.3.3.pic1.png | 98.38 | 81.81 | 36.00 | 72.06 | 
| Default <b>A</b><sub>t</sub> | 4 | https://arxiv.org/html/2501.00658/A5.T5.5.5.5.2.pic1.png | https://arxiv.org/html/2501.00658/A5.T5.6.6.6.3.pic1.png | 99.23 | 82.08 | 33.52 | 71.61 | 
| (<b>A</b><sub>t</sub>)<sub>1,1</sub>=1 | 2 | https://arxiv.org/html/2501.00658/A5.T5.8.8.8.2.pic1.png | https://arxiv.org/html/2501.00658/A5.T5.9.9.9.3.pic1.png | 99.81 | 94.70 | 56.39 | 83.63 | 
| (<b>A</b><sub>t</sub>)<sub>N,N</sub>=0 | 2 | https://arxiv.org/html/2501.00658/A5.T5.11.11.11.2.pic1.png | https://arxiv.org/html/2501.00658/A5.T5.12.12.12.3.pic1.png | 98.41 | 81.35 | 36.55 | 72.10 | 
| (<b>A</b><sub>t</sub>)<sub>N,N</sub>=0 | 4 | https://arxiv.org/html/2501.00658/A5.T5.14.14.14.2.pic1.png | https://arxiv.org/html/2501.00658/A5.T5.15.15.15.3.pic1.png | 99.74 | 92.20 | 52.21 | 81.38 | 
| (<b>A</b><sub>t</sub>)<sub>1,1</sub>=1,(<b>A</b><sub>t</sub>)<sub>N,N</sub>=0 | 2 | https://arxiv.org/html/2501.00658/A5.T5.17.17.17.2.pic1.png | https://arxiv.org/html/2501.00658/A5.T5.18.18.18.3.pic1.png | 99.23 | 95.54 | 54.74 | 83.17 | 
| (<b>A</b><sub>t</sub>)<sub>1,1</sub>=1,(<b>A</b><sub>t</sub>)<sub>N,N</sub>=0 | 4 | https://arxiv.org/html/2501.00658/A5.T5.20.20.20.2.pic1.png | https://arxiv.org/html/2501.00658/A5.T5.21.21.21.3.pic1.png | 99.94 | 98.80 | 81.56 | 93.43 |{{< /table-caption >}}
> 🔼 표 5는 논문의 실험 결과를 보여주는 표입니다.  원 논문의 표 제목은 다소 간략하게 작성되어 있으므로, 보다 자세한 설명을 추가하여 이해도를 높였습니다. 표는 SSM(Structured State Space Model)의 locality(국소성) 및 over-smoothing(과도한 평활화) 문제를 완화하기 위한 polarization 기법의 효과를 다양한 설정(모델 깊이, key-value 쌍 개수) 하에서 보여줍니다.  1-polarization은 locality 문제를 효과적으로 완화하지만, 모델의 깊이를 늘리면 recency(최근 정보 편향)는 다소 완화되나 over-smoothing이 악화되는 것을 보여줍니다. 반면에 0-polarization은 over-smoothing을 완화하고, 모델 깊이를 늘림으로써 성능 향상을 가져옵니다.  결론적으로, polarization 기법은 SSM의 확장성을 제한하는 locality와 over-smoothing 문제를 효과적으로 해결하는 데 기여함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Extension to Tab. 5. We note the extent of locality and over-smoothing for each configuration. We consider 1111-polarization mitigates locality most significantly, while deepening architecture only relieves recency mildly but deteriorates over-smoothing. 00-polarization alleviates over-smoothening and unleash the benefits by depth scaling.
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