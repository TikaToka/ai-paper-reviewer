---
title: "You Do Not Fully Utilize Transformer's Representation Capacity"
summary: "LIMe: Transformer의 표현력 한계 극복!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 T-Tech HSE University Moscow Institute of Physics and Technology",]
showSummary: true
date: 2025-02-13
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.09245 {{< /keyword >}}
{{< keyword icon="writer" >}} Gleb Gerasimov et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-19 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.09245" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.09245" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/you-do-not-fully-utilize-transformer-s" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존 Transformer 모델은 이전 레이어의 정보를 제한적으로 활용하여 표현력 저하 및 성능 저하 문제를 야기합니다.  특히 긴 시퀀스 처리 시 미묘한 차이가 사라지는 표현 붕괴 현상이 발생합니다.  본 논문은 이러한 문제를 해결하기 위해 Layer-Integrated Memory (LIMe) 라는 새로운 기법을 제안합니다.



LIMe는 이전 레이어의 은닉 상태에 접근하여 정보를 통합하는 메커니즘을 통해 모델의 표현력을 확장합니다.  광범위한 실험을 통해 다양한 과제에서 LIMe의 일관된 성능 향상을 입증하고, 표현 붕괴 현상을 완화하는 효과를 보였습니다.  또한, LIMe가 레이어 간 정보 통합을 어떻게 수행하는지에 대한 분석 결과를 제시하여, 향후 심층 신경망 연구에 대한 새로운 방향을 제시합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} LIMe는 기존 Transformer의 표현력 한계를 극복하여 성능 향상을 가져왔습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} LIMe는 다양한 아키텍처와 과제에서 일관된 성능 향상을 보였습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} LIMe는 심층 신경망의 표현력 분석에 대한 새로운 통찰력을 제공합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **Transformer 모델의 표현 능력을 제한하는 기존의 설계 문제**를 해결하기 위한 새로운 방법을 제시하여, 깊이 있는 Transformer 모델의 성능 향상과 표현력 증대에 기여합니다.  **다양한 과제에서의 성능 향상**과 **표현 붕괴 현상 완화**에 대한 실험적 증거를 제시하여, **향후 연구 방향**을 제시합니다.  이는 심층 신경망 연구 전반에 걸쳐 영향을 미칠 수 있는 중요한 발견입니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.09245/x1.png)

> 🔼 그림 1은 Llama, Static LIMe, Dynamic LIMe 세 가지 모델에 대한 학습 손실(loss) 대비 FLOPs(floating point operations) 그래프를 보여줍니다.  FLOPs는 모델의 계산량을 나타내는 지표이며, 손실은 모델의 예측 정확도와 반비례하는 값입니다. 그래프에서 확인할 수 있듯이, LIMe 모델 (Static과 Dynamic 모두)은 Llama 모델보다 훨씬 낮은 손실을 보이는데, 이는 동일한 계산량(FLOPs)으로 훨씬 더 나은 성능을 달성함을 의미합니다.  즉, LIMe는 Llama보다 효율성이 훨씬 높은 모델임을 보여주는 것입니다. 5.1절에서 더 자세한 내용을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Training loss per FLOPs for Llama, Static LIMe, and Dynamic LIMe. LIMe has a substantially lower loss with a similar amount of FLOPs. See Section 5.1 for more details.
> </details>





{{< table-caption >}}
| Model | ARC-E | ARC-C | Winogrande | COPA | MultiRC | RTE | HellaSwag | PIQA | Avg |
|---|---|---|---|---|---|---|---|---|---| 
| LLaMA | 69.5 | 38.7 | 55.2 | 75.0 | 42.8 | 54.5 | 53.1 | 72.5 | 57.7 |
| HC | 70.1 | 38.4 | 53.0 | 77.0 | 42.9 | 51.6 | 54.4 | 73.5 | 57.6 |
| LIMe Dynamic | 72.7 | 39.5 | 53.1 | 79.0 | 43.0 | 52.4 | 54.4 | 72.9 | 58.4 |
| LIMe Static | 71.1 | 39.3 | 56.2 | 75.0 | 43.1 | 55.2 | 53.9 | 72.2 | 58.3 |{{< /table-caption >}}

> 🔼 표 1은 1.2B 매개변수 모델을 사용하여 num-fewshots를 1로 설정하고 다양한 언어 모델링 평가 벤치마크를 수행한 결과를 보여줍니다.  평가 벤치마크는 ARC-E, ARC-C, Winogrande, COPA, MultiRC, RTE, HellaSwag, PIQA 등 다양한 언어 이해 과제를 포함합니다.  각 과제에 대한 정확도(정확율)는 백분율(%)로 표시되어 있으며, 마지막 열은 모든 과제에 대한 평균 정확도를 나타냅니다.  제안된 LIMe 기법(LIMe Static 및 LIMe Dynamic)은 기존의 LLaMA 및 HyperConnections 모델보다 우수한 성능을 보여주는 것으로 나타났습니다.  자세한 내용은 본 논문 5.1절을 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Table 1: LM Evaluation Harness benchmarks (accuracies in %) on 1.2B models with num-fewshots 1. The rightmost column shows average accuracy across the tasks. Proposed methods outperform both LLaMA and HyperConnections (Zhu et al., 2024) baselines. See Section 5.1 for more details.
> </details>





### In-depth insights


#### Transformer Limits
트랜스포머의 한계는 주로 **표현 능력의 제약**과 **계산 비용**에서 비롯됩니다.  표현 능력의 측면에서 트랜스포머는 이전 토큰들을 단순히 하나의 은닉 상태로 압축하는 RNN과 달리 모든 이전 토큰에 직접적으로 주의를 기울일 수 있습니다. 하지만 표준 트랜스포머는 바로 앞 레이어의 표현만 사용하기 때문에 **표현 붕괴** 현상이 발생합니다. 긴 시퀀스에서 미묘한 차이가 사라지고 성능이 저하될 수 있습니다. 계산 비용 측면에서는 트랜스포머의 계산 복잡도가 시퀀스 길이에 따라 증가하여 **긴 시퀀스 처리에 어려움**을 겪습니다.  **메모리 용량** 또한 중요한 제약으로, 특히 매우 긴 시퀀스나 대규모 모델에서는 메모리 부족으로 인해 학습과 추론이 불가능할 수 있습니다.  이러한 한계를 극복하기 위한 다양한 연구가 진행 중이며, 효율적인 메모리 관리 및 계산 최적화 기법 등이 중요한 연구 주제입니다.

#### LIMe: Multi-Layer Memory
LIMe는 기존 Transformer 모델의 한계를 극복하기 위해 제안된 다층 메모리 메커니즘입니다. **기존 Transformer는 이전 계층의 표현만을 사용하지만, LIMe는 이전 모든 계층의 은닉 상태에 접근하여 정보를 통합**합니다.  이는 **표현 붕괴 문제를 완화**하고, 모델의 **표현 능력을 확장**시키는 효과를 가져옵니다. LIMe의 핵심은 다층 정보를 효율적으로 융합하는 라우팅 메커니즘으로, **계산 비용 증가를 최소화하면서 성능 향상을 달성**합니다.  실험 결과는 다양한 작업에서 LIMe가 기존 모델들을 능가하는 성능을 보임을 보여주며, **심층적인 분석을 통해 LIMe의 작동 원리를 밝히고, 향후 심층 신경망 연구의 새로운 방향을 제시**합니다. 특히, LIMe는 장문의 시퀀스 처리에 효과적이며, **모델의 해석력 향상**에도 기여할 수 있습니다.  이는 **심층 신경망의 표현력 한계를 극복하고, 더욱 강력하고 해석 가능한 모델 개발**에 중요한 전환점을 마련할 수 있다는 점에서 의의가 있습니다.

#### Representation Collapse
본 논문에서 다루는 "표현 붕괴(Representation Collapse)"는 긴 시퀀스를 처리하는 트랜스포머 모델에서 나타나는 심각한 문제입니다. **깊이가 깊어질수록 모델이 이전 계층의 정보를 제대로 활용하지 못하고 표현력이 감소하는 현상**을 의미합니다.  이는 **모델이 미묘한 차이를 구별하지 못하고 다양한 토큰들을 같은 표현으로 압축**시키기 때문에 발생합니다.  이로 인해 **모델의 성능이 저하**되고 **해석력이 떨어지는 결과**를 초래합니다.  논문에서는 이 문제를 해결하기 위해 다계층 메모리 접근을 가능하게 하는 LIMe(Layer-Integrated Memory)라는 새로운 방법을 제시하고 있으며, 이를 통해 **표현 다양성을 증가시키고 성능을 향상**시키는 효과를 보입니다.  **LIMe는 이전 계층의 정보를 효율적으로 통합하여 표현 붕괴 현상을 완화**시키는 핵심적인 역할을 수행합니다.  결과적으로 LIMe는 **트랜스포머 모델의 표현 능력을 극대화**하고 더욱 **강력하고 해석 가능한 모델**을 만드는 데 기여할 것으로 예상됩니다.

#### Depthwise Circuit Analysis
심층적 회로 분석은 **트랜스포머 모델 내부의 정보 흐름과 처리 과정**을 자세히 들여다보는 중요한 분석 방법입니다. 특히, 이 논문에서 제시된 LIMe (Layer-Integrated Memory) 와 같은 다층적 메모리 접근 방식을 사용하는 모델에서는 각 층간의 상호 작용과 정보 전달 경로를 파악하는 것이 중요합니다.  **LIMe는 이전 층들의 정보를 현재 층에 통합**하는 방식으로, 단순히 이전 층의 출력만을 사용하는 기존 트랜스포머보다 훨씬 복잡한 정보 흐름을 보일 것으로 예상됩니다. 심층 회로 분석을 통해, LIMe가 어떻게 다양한 층들로부터 정보를 효율적으로 통합하고, **표현력 저하(representation collapse) 문제를 완화**하는지에 대한 구체적인 메커니즘을 밝혀낼 수 있습니다. 또한, 각 층에서 어떤 종류의 정보가 주로 처리되는지, 특정 층들이 어떤 역할을 수행하는지에 대한 이해를 높일 수 있으며, **모델의 성능 향상에 기여하는 요인**을 분석할 수 있습니다.  **특정 어휘나 구문 정보의 처리 경로**를 추적하여 모델의 해석력을 향상시킬 수 있습니다.  결론적으로, 심층 회로 분석을 통해 LIMe의 작동 원리를 명확히 이해하고, 트랜스포머 모델의 설계 및 최적화에 대한 새로운 통찰력을 얻을 수 있을 것입니다.

#### Future Research
본 논문은 Transformer의 표현 능력을 향상시키는 LIMe 메커니즘을 제시하며, 다층 메모리 접근을 통해 성능 향상을 이끌어냈습니다. **미래 연구 방향**으로는 LIMe의 효율적인 구현 및 확장성 개선에 대한 연구가 필요합니다. 특히, **매우 깊은 네트워크에서의 LIMe 적용 및 최적화**는 중요한 과제입니다. 또한, LIMe가 학습된 표현의 다양성을 증가시키는 메커니즘에 대한 심층적인 분석과 더불어, **다양한 과제 및 아키텍처에 대한 LIMe의 일반화 성능 검증**이 필요합니다.  나아가, LIMe의 **해석 가능성을 높이기 위한 연구**도 중요한데, 이를 위해서는 학습된 경로(circuits)에 대한 심층적인 분석과 시각화 기법 개발이 필요합니다.  **LIMe와 다른 메모리 증강 기법들과의 비교 연구**를 통해 LIMe의 강점과 한계를 명확히 파악하는 것 또한 중요한 미래 연구 과제입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.09245/x2.png)

> 🔼 그림 2는 여러 층(r)에서 이전 층(m)의 표현에 대한 평균 검색 가중치를 보여줍니다.  두 경우 모두, 마지막 층에서는 모델이 현재 층이 아닌 이전 층의 정보를 검색하는 경향이 있습니다.  동적 LIMe의 경우, 첫 번째 층에서 정보를 검색하는 비율이 확실히 높아지는 것을 볼 수 있습니다.  자세한 내용은 5.2절을 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Figure 2: Mean retrieval weight for each representation (m𝑚mitalic_m) among later layers (r𝑟ritalic_r). In both cases, in the last layers, models tend to retrieve information from previous layers rather than from the current one. In the case of Dynamic LIMe, there is a clear bump in retrieving from the first layer. See Section 5.2 for more details.
> </details>



![](https://arxiv.org/html/2502.09245/x3.png)

> 🔼 그림 3은 정적 및 동적 LIMe의 각 헤드에 대한 자기 검색 가중치를 보여줍니다. 두 모델 모두 중간 계층에서 최신 표현에 더 높은 가중치를 할당하지만, 나중에는 저수준 기능을 검색하는 경향이 있습니다. 묘사된 가중치는 거의 모든 헤드에서 크게 감소하지만, 일부 헤드는 여전히 자기 검색 경로를 사용하여 출력을 개선하는 단계를 제안합니다. 또한 동적 LIMe의 첫 번째 계층은 시퀀스 조건 지정으로 인해 저수준 기능에 크게 의존함을 알 수 있습니다. 자세한 내용은 5.2절을 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Figure 3: Self Retrieval weights for each head of Static and Dynamic LIMe. Both models assign higher weights to the latest representation in the middle layers, but tend to retrieve lower-level features later. The depicted weights decrease significantly in almost all heads, although some of them still use self-retrieval paths, suggesting the outputs’ refinement stage. Moreover, we can see that Dynamic LIMe’s first layers heavily rely on low-level features due to their sequence conditioning. See Section 5.2 for more details.
> </details>



![](https://arxiv.org/html/2502.09245/x4.png)

> 🔼 그림 4는 LIMe의 각 레이어(r)에 대해 기대되는 검색된 표현을 보여줍니다. 정적 및 동적 변형 모두 초기 레이어의 정보를 검색하는 경향이 있습니다. 이는 LIMe가 이전 레이어의 정보를 활용하여 표현의 붕괴를 방지하고 성능을 향상시키는 메커니즘을 보여줍니다. 자세한 내용은 5.2절을 참조하세요.
> <details>
> <summary>read the caption</summary>
> Figure 4: Expected retrieved representation for each LIMe layer (r𝑟ritalic_r). Both static and dynamic variants tend to retrieve information from early layers. See Section 5.2 for more details.
> </details>



![](https://arxiv.org/html/2502.09245/x5.png)

> 🔼 그림 5는 FineWeb Edu 데이터셋 하위 집합에 대한 각 계층별 값 행렬 엔트로피를 보여줍니다. 동적 및 정적 LIMe 모두 LLaMa보다 더 다양한 값을 가지며, 이는 LIMe가 더 많은 정보를 저장하고 있음을 시사합니다.  즉, 각 레이어에서 값(Value)들의 다양성을 측정한 것으로, 다양성이 클수록 모델이 더 많은 정보를 표현하고 있음을 의미합니다.  LLaMa에 비해 LIMe(동적 및 정적)의 값들이 더 다양하게 분포되어 있어, LIMe가 더욱 풍부한 정보를 표현하고 있음을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Values’ matrix entropy on FineWeb Edu subset by layers. Both Dynamic and Static LIMe have more diverse values than LLaMa, which indicates more information stored in LIMe.
> </details>



![](https://arxiv.org/html/2502.09245/x6.png)

> 🔼 그림 6은 유사한 토큰들의 값들을 여러 계층에 걸쳐 t-SNE 기법을 사용하여 시각화한 것입니다. LIMe에서 얻은 값들은 후반부 계층에서도 구분 가능하지만, LLaMA에서는 혼합되어 토큰에 대한 정보가 손실되는 것을 보여줍니다. 이는 LIMe가 다층 메모리 접근을 통해 표현의 붕괴를 방지하여 더욱 풍부하고 구별되는 표현을 생성함을 시사합니다. 자세한 내용은 5.3절을 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Figure 6: t-SNE of similar tokens’ values among layers. Values obtained from LIMe are separable in later layers, while values in LLaMA become mixed and lose information about tokens. See Section 5.3 for more details.
> </details>



![](https://arxiv.org/html/2502.09245/x7.png)

> 🔼 그림 7은 5개의 교차 검증 폴드에 걸쳐 측정된 값 분류 정확도를 보여줍니다. LIMe에서 얻은 후기 레이어의 값들은 거의 1.0의 정확도로 선형적으로 분리될 수 있지만, LLaMA의 값들은 훨씬 낮은 정확도를 보입니다. 이는 LIMe가 LLaMA보다 훨씬 더 효과적으로 토큰 간의 미묘한 차이를 유지한다는 것을 시사합니다. 자세한 내용은 5.3절을 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Figure 7: Values classification accuracy measured with standard deviation over 5 cross-validation folds. Values in later layers obtained from LIMe can be linearly separated with nearly 1.0 accuracy, while accuracy for values from LLaMA is much lower. See Section 5.3 for more details.
> </details>



![](https://arxiv.org/html/2502.09245/x8.png)

> 🔼 그림 8은 다양한 깊이의 트랜스포머 아키텍처에 대한 훈련 손실을 보여줍니다.  특히 128개의 레이어를 가진 모델에서 LIMe 아키텍처가 기준 모델보다 훨씬 우수한 성능을 보임을 알 수 있습니다.  이는 LIMe가 다층 메모리 접근 방식을 통해 깊은 네트워크에서 나타나는 표현 붕괴 문제를 효과적으로 완화하기 때문입니다. 그림은 훈련 손실 곡선을 통해 LIMe의 성능 향상을 시각적으로 보여주며, 자세한 내용은 본 논문 5.4절을 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Figure 8: Training losses for deep architectures. The LIMe architecture significantly outperforms the baseline, especially in the case of 128128128128 layers. See Section 5.4 for more details.
> </details>



![](https://arxiv.org/html/2502.09245/x9.png)

> 🔼 그림 9는 top-p 가지치기를 사용하여 학습된 128계층 LIMe 모델의 검색 가중치 통계를 보여줍니다. 후속 계층으로부터의 평균 검색 가중치(녹색 곡선)는 여러 개의 정보 스트림을 자기 지도 방식으로 모델이 획득한다는 것을 나타내는 여러 개의 뚜렷한 피크를 보여줍니다. 자기 검색 가중치(오렌지색 곡선)의 평균은 1.0이 자기 주의를 나타내며, 후속 계층에서 감소하여 정보 처리 패턴이 다른 세 개의 연속적인 계층 그룹을 형성합니다. 자세한 내용은 5.4절을 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Figure 9: Retrieval weights statistics for a 128-layer LIMe model trained with top-p𝑝pitalic_p pruning. The mean retrieval weight from subsequent layers (green curve) displays several distinct peaks, indicating that the model acquires multiple information streams in a self-supervised fashion. The mean self-retrieval weight (orange curve), where 1.0 denotes self-attention, decreases across later layers, forming three consecutive layer groups with different information-processing patterns. See Section 5.4 for further details.
> </details>



![](https://arxiv.org/html/2502.09245/x10.png)

> 🔼 그림 10은 각 LIMe 계층에 대해 헤드에 걸쳐 평균화된 자기 검색 가중치를 보여줍니다. 이 그림은 각 LIMe 계층에서 이전 계층의 표현에 대한 각 헤드의 평균 가중치를 보여줍니다.  간단히 말해, 이 그림은 LIMe 모델의 각 계층에서 얼마나 자주 이전 계층의 정보를 참조하는지를 보여주는 시각적 표현입니다.  x축은 LIMe 계층의 번호를 나타내고, y축은 평균 가중치를 나타냅니다.  가중치가 높을수록 해당 계층이 이전 계층의 정보를 더 많이 활용한다는 것을 의미합니다. 이는 LIMe 모델이 다양한 계층의 정보를 통합하여 더 나은 성능을 달성하는 방법을 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Self Retrieval weights averaged across heads for each LIMe layer.
> </details>



![](https://arxiv.org/html/2502.09245/x11.png)

> 🔼 그림 11은 FineWeb Edu 데이터셋에서 각 계층별 은닉 상태의 매트릭스 엔트로피를 보여줍니다. LIMe의 은닉 상태는 언어 작업에서 더 나은 성능을 제공하기 위해 다양성이 부족할 수 있음을 보여줍니다. 자세한 내용은 5.3절을 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Figure 11: Hiddens’ matrix entropy on FineWeb Edu subset by layers. We can see that hidden states in LIMe can be not very diverse for the model to provide better performance on language tasks. For details, see Section 5.3.
> </details>



![](https://arxiv.org/html/2502.09245/x12.png)

> 🔼 그림 12는 5개의 교차 검증 세트에 대한 표준 편차를 측정하여 숨겨진 상태 분류 정확도를 보여줍니다. LLaMA의 경우 심층 레이어에서 선형 분리 가능성이 더 강하지만, LIMe는 전체 숨겨진 상태의 차원을 사용하여 다음 토큰 예측으로 원활하게 이동하기 때문에 후반 레이어에서 클러스터링이 다소 어려워집니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Hidden states classification accuracy measured with standard deviation over 5 cross-validation folds. Although LLaMa’s deeper layers maintain stronger linear separability, LIMe’s hidden states become slightly harder to cluster in later layers due to its ability to smoothly move on to predicting the next token using the full hidden states’ dimensionality.
> </details>



![](https://arxiv.org/html/2502.09245/x13.png)

> 🔼 그림 13은 Fineweb Edu 데이터셋의 일부를 사용하여 학습된 정적 가중치와 동적 사전 분포를 보여줍니다. 각 셀은 특정 헤드 내 각 레이어의 검색 확률을 나타냅니다.  즉, 각 레이어의 어텐션 헤드가 이전 레이어의 정보를 얼마나 활용하는지를 가중치의 형태로 시각화한 것입니다.  정적 가중치는 모든 토큰에 대해 동일하게 적용되는 반면, 동적 사전 분포는 토큰마다 다르게 적용됩니다. 이 그림은 LIMe 모델의 다층 메모리 접근 방식을 이해하는 데 중요한 시각적 자료입니다.  다양한 레이어에서 어텐션 헤드가 과거 레이어의 정보를 선택적으로 활용하는 패턴을 보여주며, LIMe 모델의 동작 메커니즘을 자세히 파악하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: Learned static weights and dynamic prior distribution calculated on a subset of Fineweb Edu. Each cell represents retrieval probability for each layer in the specific head.
> </details>



![](https://arxiv.org/html/2502.09245/x14.png)

> 🔼  그림 14는 128개의 레이어를 가진 심층 정적 LIMe에 대한 모든 가중치를 보여줍니다. 반복적인 라우팅 패턴이 정제 프로세스를 닮았다는 것을 명확하게 알 수 있습니다. 즉, 이 그림은 심층 신경망에서 LIMe가 이전 레이어의 정보를 효율적으로 재활용하여 특징을 정제하는 과정을 시각적으로 보여줍니다. 각 셀은 특정 헤드에 대한 특정 레이어의 검색 확률을 나타냅니다.  다양한 레이어에서 일관되게 나타나는 패턴은 LIMe의 효율적인 다층 메모리 접근 방식을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: All weights for deep static LIMe with 128 layers. We can see explicitly the repeated routing patterns resembling a refinement process.
> </details>



![](https://arxiv.org/html/2502.09245/x15.png)

> 🔼 본 그림은 유사한 토큰들의 은닉 상태를 다양한 레이어에서 t-SNE 기법을 사용하여 시각화한 것입니다. LLaMA 모델과 달리 LIMe 모델은 이전 레이어의 표현을 참조하여 업데이트를 수행할 수 있으며, 이는 후반 레이어에서 값들의 분리성을 높이는 데 기여합니다. 즉, LLaMA는 후반 레이어에서 유사한 토큰들이 서로 구분이 어렵게 섞이는 반면, LIMe는 이전 레이어의 정보를 활용하여 각 토큰들을 보다 명확하게 구분할 수 있음을 보여줍니다. 자세한 내용은 5.3절을 참조하세요.
> <details>
> <summary>read the caption</summary>
> Figure 15: t-SNE of similar tokens’ hidden states among layers. Although hidden states are not separable in later layers for both models, unlike LLaMA, LIMe can make updates attending to the previous representations, which leads to high values’ separability. See Section 5.3 for more details.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| L | R | H | Semantic circuit description | Tokens examples |
|---|---|---|---|---|
| 4 | 0 | 23 | Primarily partial word segments that illustrate English morphological composition. | lex, ache, isters, ique, ley, elling, ets, ry. |
| 9 | 1 | 3 | A range of English suffixes or near-suffix fragments that highlight morphological building blocks and transformations. | ist, ised, ishing, osed, ized, ense, istic, ish, ened, inch. |
| 8 | 0 | 10 | Primarily affixes and stems that indicate morphological processes in English. | izing, ically, ified, ission, ational, ist, ering. |
| 15 | 1 | 23 | A collection of intensifiers, qualifiers, and comparative modifiers that adjust tone and degree in writing. | very, various, respective, relatively, highly, latter, largely, particularly. |
| 10 | 1 | 18 | Primarily subordinating conjunctions and discourse markers for conditions or reasons, illustrating causation, contingency, and contrast. | Because, If, Although, While, There, According, Unlike, However, It, Even. |{{< /table-caption >}}
> 🔼 이 표는 Dynamic LIMe 모델에서 의미적 회로가 활성화되는 토큰의 예시를 보여줍니다.  각 행은 특정 토큰(단어 또는 어절)과, 그 토큰의 의미적 회로가 활성화되는 레이어(L), 참조되는 표현의 레벨(R), 헤드 번호(H)를 나타냅니다.  이 결과는 모델이 더 깊은 레이어로 정보를 변경하지 않고 건너뛸 수 있는 심층 회로를 학습한다는 것을 보여줍니다.  자세한 내용은 5.2절을 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Table 2: Table with examples of tokens where semantic circuits activate in Dynamic LIMe. L – layer which makes the query, R – level of queried representation, H – head number. This result indicates that the model learns depthwise circuits to bypass information without change to a further layer. See Section 5.2 for more details.
> </details>

{{< table-caption >}}
| Hyperparameter | Value |
|---|---| 
| Optimizer | AdamW |
| Learning Rate | 0.001 |
| LIMe Router Learning Rate | 0.01 |
| Weight Decay | 0.1 |
| β₁ | 0.9 |
| β₂ | 0.95 |
| ϵ | 1e-8 |
| Scheduler | cosine |
| Warmup Steps | 200 |
| Min LR | 1e-6 |
| Mixed Precision | bf16 |
| Gradient Clipping | 1.0 |
| Sequence Length | 2048 |
| Batch Size | 1024 |
| Training Steps | 20000 |{{< /table-caption >}}
> 🔼 이 표는 논문의 모든 실험에서 사용된 주요 훈련 하이퍼파라미터들을 보여줍니다.  최적화 알고리즘, 학습률, 가중치 감쇠, 베타1, 베타2, 에프실론, 스케줄러, 웜업 단계, 최소 학습률, 혼합 정밀도, 기울기 클리핑, 시퀀스 길이, 배치 크기, 훈련 단계 등의 하이퍼파라미터 값들이 포함되어 있습니다.  각 하이퍼파라미터는 모델 학습 과정에 중요한 영향을 미치는 요소이며, 이 표는 실험의 재현성과 결과 해석에 필수적인 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Key training hyperparameters used in all experiments.
> </details>

{{< table-caption >}}
| Parameter | Value |
|---|---| 
| Vocab Size | 50,257 |
| Hidden Size | 2048 |
| Intermediate Size | 8192 |
| Number of Hidden Layers | 16 |
| Number of Attention Heads | 32 |
| Tie Word Embeddings | True |{{< /table-caption >}}
> 🔼 이 표는 논문에서 제시된 세 가지 모델 변형(LLaMa, Hyper Connections, LIMe)에 대한 아키텍처를 12억 매개변수 규모에서 비교하여 보여줍니다. 각 모델의 어휘 크기, 은닉층 크기, 중간층 크기, 은닉층 수, 어텐션 헤드 수, 가중치 공유 여부 등의 주요 아키텍처 매개변수 값이 표에 자세히 나열되어 있습니다. 이를 통해 세 가지 모델의 아키텍처 차이를 명확하게 이해하고, 각 모델의 성능 비교 분석에 유용한 기준점을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Model architecture for all variants (LLaMa, Hyper Connections, and LIMe) at the 1.2B scale.
> </details>

{{< table-caption >}}
| Model Depth | Total Router Weights | Pruned Weights (%) |
|---|---|---|
| 32-layer | 7,936 | 1,845 (23%) |
| 64-layer | 32,256 | 6,795 (21%) |
| 128-layer | 130,048 | 24,632 (19%) |{{< /table-caption >}}
> 🔼 표 5는 다양한 모델 깊이에 대해 top-p = 0.9로 LIMe 라우터 가중치를 가지치기한 개수를 보여줍니다.  5.4절의 심층 모델 학습 결과에서 알 수 있듯이, 검색 경로 가지치기는 LIMe가 LLaMA보다 우수한 성능을 내는 것을 막지 못했습니다.  즉, LIMe는 모델의 깊이가 깊어짐에 따라 상대적으로 더 적은 수의 라우터 가중치를 가지치기하여 효율성을 유지하면서도 성능 저하 없이 우수한 성능을 유지했습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Number of pruned LIMe Router’s weights at top-p=0.9𝑝0.9p=0.9italic_p = 0.9 for various model depths. As we can see in deep models’ training results (5.4), retrieval paths pruning does not stop LIMe from being superior compared to LLaMA.
> </details>

{{< table-caption >}}
| Model | # Parameters (B) | FLOPs (T) | Peak Memory Overhead over LLaMA excluding parameters | Peak Memory Overhead over LLaMA excluding parameters |
|---|---|---|---|---|
|  |  |  | Train | Inference |
| **LLaMA** | 1.1767 | 2.97 | 0 | 0 |
| **LIMe Static** | 1.1768 (+0.008%) | 2.98 (+0.3%) | (L-1)BTHD | BTHD<sup>(*)</sup> |
| **LIMe Dynamic** | 1.1856 (+0.075%) | 3.01 (+1.3%) | BTH(L(L+1)/2-1)+(L-1)BTHD | LBTH+BTHD<sup>(*)</sup> |
| **HC Dynamic** | 1.1771 (+0.030%) | 2.98 (+0.3%) | 2LBT[(R-1)D+R(R+2))] | BT[(R-1)D+R(R+2))] |{{< /table-caption >}}
> 🔼 표 6은 1.2B 크기의 언어 모델들(LLaMA, LIMe Static, LIMe Dynamic, HC)의 효율성을 비교 분석한 표입니다.  매개변수 수, FLOPs (부동소수점 연산 수), 최대 메모리 사용량 등을 비교하여 LIMe 모델이 기존 모델들에 비해 매개변수 및 FLOPs 증가는 미미하지만 훈련 시 최대 메모리 사용량은 더 적다는 것을 보여줍니다. 특히 키-밸류 캐시를 사용하면 추론 시에도 메모리 이점이 확장됩니다.  표에는 각 모델의 헤드 수(H), 레이어 수(L), 시퀀스 길이(T), 은닉 차원(D), 하이퍼 커넥션의 확장 비율(R) 등의 정보도 함께 제공됩니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Comparing efficiency for all 1.21.21.21.2B models: both Dynamic and Static LIMe enjoy negligible parameter and FLOPs increase, and smaller peak memory than HC during training. When the Key-Value cache is utilized, this memory advantage extends to inference as well (*). H – number of heads, L — number of layers, T — sequence length, D — hidden dimension, R — Hyper Connections (Zhu et al., 2024) expansion rate.
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