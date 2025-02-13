---
title: "Gemstones: A Model Suite for Multi-Faceted Scaling Laws"
summary: "Gemstones: 4,000개 이상의 다양한 트랜스포머 모델 체크포인트를 공개하여, 모델 설계 및 훈련 선택이 확장성 법칙에 미치는 영향을 정량적으로 분석한 연구."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 University of Maryland",]
showSummary: true
date: 2025-02-07
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.06857 {{< /keyword >}}
{{< keyword icon="writer" >}} Sean McLeish et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-12 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.06857" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.06857" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/gemstones-a-model-suite-for-multi-faceted" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 확장성 법칙 연구는 모델 아키텍처와 하이퍼파라미터 선택의 범위가 제한적이어서, 실제 모델 개발에 적용하기 어려운 측면이 있었습니다. 또한, 확장성 법칙 자체가 실험 설계 및 특정 모델에 민감하여, 그 결과의 일반화 가능성에 대한 의문이 제기되었습니다.

본 연구는 이러한 문제점들을 해결하기 위해 **Gemstones라는 대규모 오픈소스 데이터셋**을 구축하고 공개하였습니다. Gemstones는 4000개 이상의 다양한 트랜스포머 모델 체크포인트를 포함하며, 모델 너비와 깊이, 훈련 토큰 수, 학습률, 쿨다운 스케줄 등 다양한 요소들을 고려하여 생성되었습니다. 이를 통해 기존 연구보다 훨씬 광범위한 실험을 수행하고, **모델 너비와 깊이를 고려한 새로운 확장성 법칙**을 제시하였습니다. 또한, **확장성 법칙의 민감도와 한계점**을 밝히고, 실제 모델 개발에 적용할 때 주의해야 할 사항들을 제시하였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 4000개 이상의 다양한 트랜스포머 모델 체크포인트를 포함하는 Gemstones 데이터셋을 공개 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 모델 너비와 깊이를 고려한 새로운 확장성 법칙 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 확장성 법칙의 민감도 및 한계점을 밝히고, 모델 설계 및 훈련에 대한 새로운 통찰력 제공 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **확장성 법칙(scaling laws)** 연구에 중요한 기여를 합니다.  **다양한 모델 아키텍처와 하이퍼파라미터를 사용한 방대한 실험 데이터셋인 Gemstones** 를 공개하여, 기존 연구의 한계를 극복하고 보다 정확하고 견고한 확장성 법칙을 도출하는 데 도움을 줍니다.  이는 **대규모 언어 모델 개발 및 최적화**에 직접적인 영향을 미치며, 향후 연구의 새로운 방향을 제시합니다. 특히 **모델 아키텍처의 형태(width/depth)**가 확장성 법칙에 미치는 영향을 심층적으로 분석하여, 모델 설계에 대한 새로운 통찰력을 제공합니다. 이는 **산업계의 대규모 언어 모델 개발 방식에 대한 이해를 높이고, 효율적인 모델 개발 전략 수립**에 기여할 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.06857/x1.png)

> 🔼 그림 1은 Transformer 아키텍처에서 width와 depth의 의미를 보여줍니다.  width는 hidden dimension의 크기를, depth는 Transformer block의 개수를 나타냅니다.  본 논문에서는 새롭게 제시하는 scaling laws를 통해 이 두 가지 요소에 대한 최적의 값을 제시하고자 합니다.  즉, 모델의 성능을 극대화하기 위해 width와 depth를 어떻게 설정해야 하는지를 보여주는 그림입니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: The meaning of width and depth. We visualize a standard transformer architecture, highlighting the “width” as the size of the hidden dimension and the “depth” as the number of transformer blocks. These are the quantities we’re interested in providing a prescription for with our new scaling laws.
> </details>







### In-depth insights


#### Multifaceted Scaling Laws
본 논문에서 다루는 다면적 스케일링 법칙은 **모델 크기(매개변수 수)** 뿐만 아니라 **모델 구조(폭과 깊이)**, **훈련 토큰 수**, **학습률**, **쿨다운 스케줄** 등 다양한 요소를 고려하여 모델 성능을 예측하는 것을 목표로 합니다. 기존 연구들이 제한된 하이퍼파라미터 선택으로 인해 좁은 범위의 모델에만 초점을 맞춘 것과 달리, 본 연구는 다양한 아키텍처와 하이퍼파라미터를 사용하여 **폭넓은 모델에 대한 스케일링 법칙을 제시**하고 있습니다.  **Gemstones 데이터셋**은 이러한 다양한 모델들을 포함하고 있어, **스케일링 법칙의 견고성과 일반화 성능**을 평가하는데 유용합니다.  또한, GPU 효율성과 과적합 문제를 고려한 새로운 스케일링 법칙을 제안하고 있으며, 모델 설계 과정에서의 여러 결정이 예측 결과에 큰 영향을 미친다는 것을 보여주고 있습니다.  이를 통해 **모델 선택 및 설계**에 대한 중요한 시사점을 제공합니다.

#### Gemstone Dataset
본 논문에서 제시된 Gemstone Dataset은 **다양한 모델 구조와 훈련 하이퍼파라미터를 가진 4000개 이상의 Transformer 모델 체크포인트**를 포함하는 방대한 규모의 데이터셋입니다. 기존 연구들과 달리, **폭넓은 아키텍처와 하이퍼파라미터 선택지를 고려하여 생성**되었다는 점이 특징입니다. 이는 스케일링 법칙 연구에 있어 모델 설계 및 선택이 미치는 영향을 보다 정확하게 평가할 수 있도록 합니다. 또한, **산업계 모델들과의 비교 분석을 통해 실제 적용 가능성을 높였습니다.** Gemstone Dataset은 다양한 스케일링 법칙 연구 및 모델 개발에 귀중한 자원이 될 것이며, 특히 **모델의 폭과 깊이가 성능에 미치는 영향을 심층적으로 분석**하는 데 유용할 것으로 예상됩니다.  **오픈소스로 공개**되어 접근성이 높다는 점 또한 큰 장점입니다.  **다만,  모델의 다양성에도 불구하고 특정 아키텍처나 훈련 설정에 편향될 가능성**이 있으며, 이에 대한 추가적인 검토가 필요할 수 있습니다.

#### Optimal Model Design
본 논문에서 다룬 '최적 모델 설계'에 대한 심층적인 고찰은 **모델의 너비와 깊이에 대한 최적 비율을 찾는 것**에 초점을 맞춥니다.  단순히 매개변수 수만 고려하는 기존 연구와 달리, **너비와 깊이 모두를 고려한 다차원적 접근**을 통해 더욱 정교한 최적 모델 설계를 제시합니다.  **다양한 아키텍처와 하이퍼파라미터를 사용한 광범위한 실험**을 통해, 최적 비율이 모델 크기 및 학습 데이터에 따라 달라짐을 밝혀냅니다.  **단순한 경험적 규칙에 의존하지 않고, 다양한 요소의 영향을 종합적으로 분석**하는 것이 중요하며, **실제 산업 현장의 모델 설계와 비교 분석**을 통해 제시된 최적 설계의 실용성을 검증합니다.  이러한 연구는 **모델 효율성과 과적합 문제**를 고려하여 보다 현실적인 최적 모델을 설계하는 데 도움을 줄 것입니다.  **새로운 스케일링 법칙을 제안**하여, 제한된 컴퓨팅 자원 내에서 최적의 모델을 찾는 실용적인 지침을 제공합니다.

#### Scaling Law Fragility
본 논문에서 제기하는 스케일링 법칙의 취약성은 **모델 설계 및 선택의 미묘한 차이가 예측 결과에 큰 영향**을 미친다는 점을 강조합니다.  **하이퍼파라미터의 작은 변화**나 **모델 구조의 사소한 차이**가 스케일링 법칙의 기울기와 절편을 크게 바꿀 수 있다는 것을 보여주는 다양한 실험 결과가 제시됩니다.  이러한 취약성은 기존 연구에서 사용된 제한적인 모델 집합의 일반화 가능성에 의문을 제기하며, **더욱 폭넓고 다양한 모델에 대한 실험**의 필요성을 시사합니다. **실험 설계 과정과 특정 모델 선택**이 스케일링 법칙에 상당한 영향을 미친다는 사실은 **실제 응용에 있어 신중한 접근**을 요구하며,  **단순한 스케일링 법칙에만 의존하는 것의 위험성**을 경고합니다. 따라서 스케일링 법칙의 맹점을 인지하고, 다양한 요소들을 고려하여 모델을 설계하고 선택해야 함을 강조합니다.

#### Future Research
본 논문은 다양한 모델 설계 및 선택이 확장 법칙에 미치는 영향을 연구하기 위해 광범위한 모델 체크포인트를 사용하는 것을 제안합니다. **미래 연구는 모델 아키텍처의 너비와 깊이에 대한 영향을 더욱 깊이 있게 조사**하여, 다양한 트랜스포머 아키텍처에서의 확장 법칙에 대한 이해를 높이는 데 초점을 맞춰야 합니다. 특히, **파라미터 효율성, 과적합, 추론 비용과 같은 실제적인 고려사항을 통합**하여 더욱 현실적인 확장 법칙을 제시하는 연구가 필요합니다. 또한, **다양한 하이퍼파라미터의 영향을 분석**하고, 이를 통해 더욱 견고하고 일반화된 확장 법칙을 개발하는 연구가 중요합니다. 마지막으로, **개발된 확장 법칙을 다양한 하류 작업에 적용**하고, 그 성능을 평가하는 실험적 연구가 필요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.06857/x2.png)

> 🔼 본 그림은 기존 연구의 스케일링 법칙 모델들, 업계의 모델들 그리고 본 논문에서 제시하는 Gemstones 모델들의 너비(width)와 깊이(depth)를 비교 분석한 것입니다. 기존 연구(보라색, 녹색)와 업계(파란색, 주황색) 모델들은 대부분 고정된 너비-깊이 비율을 가지는 선상에 위치하는 반면, 최적의 너비-깊이 비율을 제시하기 위해서는 다양한 너비와 깊이를 가진 모델들을 선택해야 합니다. 본 논문에서 제시하는 Gemstones 모델들(검은색)이 바로 이러한 다양성을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Distribution of prior scaling law models, industry models, and our models in terms of width and depth.  Prior work (purple and green) and industry models (blue and orange) mostly lie on a fixed width-depth line. If we want to prescribe the optimal width-depth ratio, we need to select models with different widths and depths (our models, black).
> </details>



![](https://arxiv.org/html/2502.06857/x3.png)

> 🔼 그림 3은 다양한 모델 아키텍처와 크기에 걸쳐 안정적이고 거의 최적의 성능을 달성하기 위해서는 학습률 조정이 필수적임을 보여줍니다. 왼쪽 그림은 초기화 규칙을 적용하지만 학습률 조정은 하지 않은 예비 학습 실행 결과를 보여줍니다. 반면 오른쪽 그림은 동일한 데이터에 대해 x축을 다시 조정하여 l⁢rbase=l⁢reff×(width×depth)𝑙subscript𝑟base𝑙subscript𝑟effwidthdepthlr_{'base'} = lr_{'eff'}         × (width         ×           √depth) 공식을 적용한 학습률 조정을 시뮬레이션한 결과를 보여줍니다. 이를 통해 폭과 깊이가 다른 아키텍처에서도 일관된 최적의 학습률을 찾을 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Learning rate scaling is necessary for width-depth transfer. Left: Preliminary training runs with initialization rules active, but no learning rate scaling. Right: Same data, but with x-axis rescaled to simulate the application of learning rate scaling with l⁢rbase=l⁢reff×(width×depth)𝑙subscript𝑟base𝑙subscript𝑟effwidthdepthlr_{\text{base}}=lr_{\text{eff}}\times(\text{width}\times\sqrt{\text{depth}})italic_l italic_r start_POSTSUBSCRIPT base end_POSTSUBSCRIPT = italic_l italic_r start_POSTSUBSCRIPT eff end_POSTSUBSCRIPT × ( width × square-root start_ARG depth end_ARG ).
> </details>



![](https://arxiv.org/html/2502.06857/x4.png)

> 🔼 그림 4는 두 가지 다른 방법으로 계산된 최적의 모델 크기를 보여줍니다. 첫 번째 행은 FLOPs(왼쪽) 및 GPU 시간(오른쪽)에 따른 검증 손실을 나타냅니다.  검은색 십자가는 각 설정에서 볼록선체(convex hull) 상의 최적 점을 나타냅니다. 두 번째 행은 경험적으로 최적화된 모델의 매개변수당 토큰 수에 대한 선형 회귀 분석 결과를 보여줍니다. 본 연구 결과는 Hoffmann et al.(2022)의 연구 결과보다 약간 높지만 여전히 일정한 매개변수당 토큰 수를 보여줍니다. Hoffmann et al.(2022)의 접근 방식 1은 크기를 10배 단위로 로그 스케일로 나눈 250개의 FLOPs 구간을 사용하는 반면, 본 연구에서는 볼록선체 접근 방식을 사용하여 더 적은 모델로 법칙을 적합시켜 더 나은 결과를 얻었습니다. 그림 9에 확장된 그림이 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Approach 1 prescriptions. Row one: Validation loss over FLOPs (left) and GPU hours (right). We use Approach 1 to find the optimal points on the convex hull in each setting, marked with black crosses. Row two: We fit a line to the tokens per parameter of empirically optimal models and find a slightly higher, but still constant, tokens per parameter prescription than Hoffmann et al. (2022).  Hoffmann et al. (2022)’s Approach 1 creates 250250250250 logarithmically-spaced FLOPs bins per order of magnitude, and in red we plot the minimizers over these bins, and the scaling law fitted to these minimizers (binning). Clearly, their Approach 1 is not well-suited for our data, and our convex hull approach is better when we select fewer models to fit our law on. Extended plot in Figure 9.
> </details>



![](https://arxiv.org/html/2502.06857/x5.png)

> 🔼 그림 5는 본 논문의 등식 (2)에 제시된 매개변수화를 사용한 접근 방식 3의 법칙을 보여줍니다. 그림의 왼쪽은 FLOPs 예산이 증가함에 따라 규정된 최적 너비-깊이 비율이 증가하고, 오른쪽은 FLOPs 예산이 증가함에 따라 매개변수당 최적 토큰 수가 감소함을 보여줍니다. 어텐션 헤드에 대한 정수 제약 조건으로 인해 선이 약간 울퉁불퉁하지만, 그림 16에서 이 제약 조건을 제거한 플롯도 함께 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Approach 3 laws with the parametrization shown in Equation 2. We see the prescribed optimal width-depth ratio increases with the FLOPs (left) budget and the optimal tokens per parameter decreases as the FLOPs budget increases (right). We see slight bumpiness in the lines due to the integer constraints we enforce on the attention heads, we also plot with this constraint removed in Figure 16.
> </details>



![](https://arxiv.org/html/2502.06857/x6.png)

> 🔼 그림 6은 데이터를 여러 방식으로 재샘플링하여 스케일링 법칙을 적합하는 데 있어 변동성을 보여줍니다. 접근 방식 1을 사용하여 얻은 처방은 범례에 'Approach 1'로 표시하고, 그렇지 않은 경우 접근 방식 3을 사용합니다. 범례에 명시되지 않은 한, 사용 가능한 모든 토큰 수를 법칙에 적용합니다. 예를 들어, ≤100B는 100B 미만 또는 100B 이하의 토큰 수만 적합하는 데 사용됨을 의미합니다. No Embeds: 임베딩 매개변수는 법칙에 적용되지 않습니다. Cooldown: 쿨다운 에이블레이션의 데이터만 법칙에 적용합니다. LR Ablation: 학습률을 절반으로 줄인 학습률 에이블레이션 학습 런의 데이터만 법칙에 적용합니다. width=512 Only: 너비가 512인 모델의 데이터만 법칙에 적용합니다. Chinchilla Reduced Sampling: Hoffmann 등(2022)이 스케일링 법칙을 적용하는 데 사용한 토큰 수와 모델 크기에 최대한 가깝도록 데이터를 하위 샘플링하고, Hoffmann 등(2022)의 데이터 하위 집합에 새로운 스케일링 법칙을 적용합니다. 자세한 내용은 4.2절을 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Figure 6:  We demonstrate the variability in fitting scaling laws by resampling our data many different ways. We label prescriptions found using Approach 1 with “Approach 1111” in the legend, otherwise approach 3333 is used. All tokens counts available are used to fit the laws unless stated otherwise in the legend, for example ≤100⁢Babsent100𝐵\leq 100B≤ 100 italic_B means that only token counts less than or equal to 100⁢B100𝐵100B100 italic_B are used in fitting. No Embeds: Embedding parameters are not counted when fitting these laws. Cooldown: Only data from the cooldown ablation is used to fit this law. LR Ablation: Only data from the learning rate ablation training runs, where the learning rate is halved, is used to fit these laws. width=512512512512 Only: Only models with width 512512512512 are used to fit these laws. Chinchilla Reduced Sampling: We subsample our data to be as close as possible to the token counts and model sizes that Hoffmann et al. (2022) use to fit their scaling laws and also fit new scaling laws on this subset of Hoffmann et al. (2022) data. Details in Section 4.2.
> </details>



![](https://arxiv.org/html/2502.06857/x7.png)

> 🔼 그림 7은 최적이 아닌 너비와 깊이를 가진 모델을 학습시키는 비효율성을 보여줍니다. Gemstones 모델을 3000억 토큰 동안 학습시킨 후 FLOPs(왼쪽) 및 GPU 시간(오른쪽) 초과분을 플롯합니다. 초과분은 특정 손실에 도달하기 위해 주어진 너비-깊이 구성을 가진 모델에 필요한 리소스(FLOPs 또는 GPU 시간)의 양을 손실에 가장 빨리 도달하는 모델(파레토 프런티어의 점)과 비교한 것입니다. 그림에서 볼 수 있듯이 마른 모델(왼쪽 상단, 어두운 점)은 넓은 모델보다 목표 손실에 도달하는 데 훨씬 더 많은 FLOPs 또는 GPU 시간을 사용합니다. 이러한 비효율성은 텐서 병렬 처리만 사용하고 파이프라인 병렬 처리는 사용하지 않기 때문에 본 연구의 학습 설정에 존재합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7:  The inefficiency of training models with suboptimal widths and depths.  We plot the FLOPs (left) and GPU Hours (right) overspend after training our Gemstones for 300300300300 billion tokens. We define the overspend as how many resources (FLOPs or GPU hours) are required for a model with a given width-depth configuration to reach some target loss, relative to the models that achieve that target loss the fastest (the “points on (pareto)-frontier”). We can see that the skinny models (top-left, dark points) use many more FLOPs or GPU hours to reach a target loss than the wide models. We note that these inefficiencies exist in our training setup because we only use tensor parallelism and not pipeline parallelism.
> </details>



![](https://arxiv.org/html/2502.06857/x8.png)

> 🔼 그림 8은 과적합 비용을 정량화한 것입니다. 최적 토큰 수를 계산하는 데 사용된 방정식 2를 기반으로 과적합 계수만큼 최적 토큰 수를 늘려 모델 성능에 미치는 영향을 평가합니다. 그런 다음 각 FLOP 예산과 과적합 계수에서 손실을 최소화하도록 모델 형태를 최적화합니다. 10⁰ 또는 1×는 예측된 최적 지점임을 나타냅니다. 4가지 FLOP 예산(각 플롯의 제목)을 사용하여 과적합 계수의 함수로 손실을 플롯팅하고 과적합 또는 과소적합이 예측 손실을 약간 증가시킨다는 것을 확인합니다. y축 범위를 정확히 나타내기 위해 검증 세트에서 선택된 오픈소스 모델의 손실을 플롯팅합니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Quantifying the cost of overtraining.  We simulate deviations from our prescriptions to assess their impact on model performance by increasing the optimal token count prescribed by Equation 2 by an overtraining factor. We then optimize the model shape to achieve the lowest loss possible at each FLOP budget and overtraining factor. Note that 100superscript10010^{0}10 start_POSTSUPERSCRIPT 0 end_POSTSUPERSCRIPT, or 1×1\times1 ×, is the prescribed optimal point. We take four FLOP budgets (title of each plot) and plot the loss as a function of overtraining factor and see that under or overtraining increases predicted loss but by only a small amount. We plot the losses of selected open source models on our validation set to help ground the y-axis ranges.
> </details>



![](https://arxiv.org/html/2502.06857/x9.png)

> 🔼 그림 9는 논문의 그림 4를 확장한 것으로, FLOPs와 GPU 시간을 기준으로 분석한 결과를 보여줍니다. 그림 4와 마찬가지로, 왼쪽에는 FLOPs에 대한 분석을, 오른쪽에는 GPU 시간에 대한 분석을 제시합니다.  하지만 그림 9는 토큰 수와 파라미터 수를 추가적인 축으로 포함하여 보다 자세한 분석을 제공합니다.  이를 통해 모델의 크기와 훈련에 필요한 계산량 및 시간 사이의 관계를 더욱 명확하게 이해할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Extended Approach 1 plot from Figure 4, including tokens and parameters axes. As in Figure 4, we present an analysis over FLOPs on the left and over GPU hours take to train on the right.
> </details>



![](https://arxiv.org/html/2502.06857/x10.png)

> 🔼 그림 10은 학습률 에이베이션 데이터셋에 적용된 접근 방식 1을 보여줍니다. 그림 4와 마찬가지로, 왼쪽에는 FLOP에 대한 분석, 오른쪽에는 학습에 소요되는 GPU 시간에 대한 분석이 제시되어 있습니다.  보다 자세히 설명하자면, 이 그림은 모델의 너비와 깊이를 다양하게 변화시키면서 학습률을 조절했을 때,  계산량(FLOPs)과 훈련 시간(GPU hours)에 따른 성능 변화를 보여줍니다.  이를 통해 학습률 조절이 모델의 계산 효율성과 훈련 시간에 미치는 영향을 시각적으로 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Approach 1 fitted on the learning rate ablation dataset. As in Figure 4, we present an analysis over FLOPs on the left and over GPU hours take to train on the right.
> </details>



![](https://arxiv.org/html/2502.06857/x11.png)

> 🔼 그림 11은 냉각 어닐링 데이터셋에 대해 적합된 접근 방식 1을 보여줍니다. 그림 4와 마찬가지로 왼쪽에는 FLOP에 대한 분석, 오른쪽에는 학습에 소요된 GPU 시간에 대한 분석을 제시합니다.  냉각 어닐링은 학습률을 점진적으로 감소시키는 기술로, 과적합을 방지하고 모델의 일반화 성능을 향상시키는 데 도움이 됩니다. 이 그림은 냉각 어닐링 전략이 모델의 성능 및 훈련 시간에 미치는 영향을 분석하여, 최적의 컴퓨팅 자원 배분 전략을 결정하는 데 도움이 되는 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Approach 1 fitted on the cooldown ablation dataset. As in Figure 4, we present an analysis over FLOPs on the left and over GPU hours take to train on the right.
> </details>



![](https://arxiv.org/html/2502.06857/x12.png)

> 🔼 그림 12는 5번 그림에 나와있는 접근 방식 3을 확장한 그림입니다. 토큰, 파라미터, 너비, 깊이 축을 포함합니다. 여기에는 Hoffmann 등(2022)이 제안한 방정식 4와 우리의 FLOP 계산을 포함하는 무차별 대입 플로팅 방법의 비교가 포함됩니다. 오른쪽 열에는 이 두 선이 거의 차이가 없음을 보여줍니다. 업계 모델은 FLOP당 파라미터 처방전보다 체계적으로 낮거나, 또는 FLOP당 토큰 처방전보다 체계적으로 높다는 점을 지적합니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Extended Approach 3 plot from Figure 5, including tokens, parameters, width and depth axes. This also includes a comparison of equation 4 that Hoffmann et al. (2022) propose and a brute force plotting method which includes our FLOPs counting for laws of the form seen in Equation 1. We show these are blue and red lines respectively in the right column seeing only a minor difference in the outcome. We remark that industry models fall systematically below our parameter per FLOPs prescriptions, or equivalently above our token per FLOPs prescriptions.
> </details>



![](https://arxiv.org/html/2502.06857/x13.png)

> 🔼 그림 13은 학습률 변경 데이터셋에 적용된 접근 방식 3을 보여줍니다. 그림 12와 마찬가지로, 왼쪽에는 식 (2)에 나와있는 형태의 법칙에 대한 분석, 오른쪽에는 식 (1)에 나와있는 형태의 법칙에 대한 분석을 제시합니다. 그림은 다양한 모델 크기와 구조에 따른 손실 변화를 보여주며, 학습률 조정이 최적 모델 크기와 구조에 미치는 영향을 분석합니다.  다양한 아키텍처와 크기에 걸쳐 모델을 훈련하는 데 필요한 최적의 학습률을 찾기 위한 실험 결과를 보여줍니다. 이를 통해, 모델의 너비와 깊이에 따른 그래디언트 역학의 복합 효과를 고려하여 최적의 학습률을 결정하는 방법을 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: Approach 3 fitted on the learning rate ablation dataset. As in Figure 12, we present an analysis over laws of the from shown in Equation 2 on the left and laws of the form shown in Equation 1 on the right.
> </details>



![](https://arxiv.org/html/2502.06857/x14.png)

> 🔼 그림 14는 냉각 어닐링(cooldown) 변화 데이터셋에 적합화된 접근 방식 3을 보여줍니다. 그림 12와 마찬가지로, 왼쪽에는 식 (2)에 나와있는 형태의 법칙에 대한 분석, 오른쪽에는 식 (1)에 나와있는 형태의 법칙에 대한 분석을 제시합니다. 이 그림은 모델의 아키텍처(width, depth)와 학습에 사용된 토큰 수, 그리고 매개변수 수 등 다양한 요소를 고려하여, 최적의 모델 크기와 학습 방법을 제시하는 접근 방식 3의 결과를 보여줍니다. 특히, 냉각 어닐링 기법을 적용했을 때 최적의 모델 크기와 성능이 어떻게 달라지는지 보여주는 것이 핵심입니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: Approach 3 fitted on the cooldown ablation dataset. As in Figure 12, we present an analysis over laws of the from shown in Equation 2 on the left and laws of the form shown in Equation 1 on the right.
> </details>



![](https://arxiv.org/html/2502.06857/x15.png)

> 🔼 그림 15는 1200억 토큰 미만의 모든 토큰 수를 제거한 데이터셋에 대해 적합된 접근 방식 3을 보여줍니다. 그림 12와 마찬가지로, 왼쪽에는 식 (2)에 나와 있는 형태의 법칙에 대한 분석, 오른쪽에는 식 (1)에 나와 있는 형태의 법칙에 대한 분석을 제시합니다. 그림은 다양한 모델 크기와 토큰 수에 대해 생성된 모델의 손실을 보여주며, 계산 최적화된 모델 크기를 예측하는 스케일링 법칙의 성능을 평가합니다.  이를 통해 모델 설계 결정이 스케일링 법칙의 예측에 미치는 영향을 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 15: Approach 3 fitted on a dataset where all token counts less than 120120120120 billion are removed. As in Figure 12, we present an analysis over laws of the from shown in Equation 2 on the left and laws of the form shown in Equation 1 on the right.
> </details>



![](https://arxiv.org/html/2502.06857/x16.png)

> 🔼 그림 16은 그림 5의 결과를 바탕으로 하여 모델의 너비와 깊이를 결정할 때 정수 제약 조건을 제거하고 최적화를 수행한 결과를 보여줍니다. 그림 12와 마찬가지로, 왼쪽에는 식 (2) 형태의 법칙에 대한 분석을, 오른쪽에는 식 (1) 형태의 법칙에 대한 분석을 제시합니다.  정수 제약 조건을 제거함으로써, 모델의 너비와 깊이에 대한 더욱 자유롭고 다양한 최적화 결과를 얻을 수 있었습니다.  이를 통해, 다양한 모델 설계 선택지에 따른 성능 변화를 더욱 정확하게 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 16: Following from Figure 5, this plot removes the integer constraints when optimizing. As in Figure 12, we present an analysis over laws of the from shown in Equation 2 on the left and laws of the form shown in Equation 1 on the right.
> </details>



![](https://arxiv.org/html/2502.06857/x17.png)

> 🔼 그림 17은 허버 손실에서 δ=10⁻³을 사용하여 주요 데이터 세트에 적합한 접근 방식 3을 보여줍니다. 그림 16과 일치합니다. 그림 12와 같이 왼쪽에는 방정식 2에 표시된 법칙에 대한 분석을, 오른쪽에는 방정식 1 형식의 법칙에 대한 분석을 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 17: Approach 3 fitted on our main dataset using δ=10−3𝛿superscript103\delta=10^{-3}italic_δ = 10 start_POSTSUPERSCRIPT - 3 end_POSTSUPERSCRIPT in the Huber loss. Corresponds to Figure 16. As in Figure 12, we present an analysis over laws of the from shown in Equation 2 on the left and laws of the form shown in Equation 1 on the right.
> </details>



![](https://arxiv.org/html/2502.06857/x18.png)

> 🔼 그림 18은 허버 손실에서 δ=10⁻³을 사용하여 학습률 에이블레이션 데이터셋에 적합화된 접근 방식 3을 보여줍니다. 그림 12와 마찬가지로 왼쪽에는 방정식 2에 표시된 형태의 법칙에 대한 분석, 오른쪽에는 방정식 1에 표시된 형태의 법칙에 대한 분석이 제시되어 있습니다. 이 그림은 그림 13과 대응됩니다.  즉, 학습률을 절반으로 줄인 데이터셋에 대해 접근 방식 3(방정식 2와 방정식 1)을 적용한 결과를 보여줍니다.  그림은 모델의 너비, 깊이, 그리고 파라미터 수에 따른 손실 값을 FLOP(부동 소수점 연산 수)와 GPU 시간에 따라 보여주는 다양한 플롯을 포함합니다.  이를 통해 최적의 모델 크기와 형태를 예측하는 스케일링 법칙의 성능과 민감도를 분석합니다.
> <details>
> <summary>read the caption</summary>
> Figure 18: Approach 3 fitted on the learning rate ablation dataset using δ=10−3𝛿superscript103\delta=10^{-3}italic_δ = 10 start_POSTSUPERSCRIPT - 3 end_POSTSUPERSCRIPT in the Huber loss. Corresponds to Figure 13. As in Figure 12, we present an analysis over laws of the from shown in Equation 2 on the left and laws of the form shown in Equation 1 on the right.
> </details>



![](https://arxiv.org/html/2502.06857/x19.png)

> 🔼 그림 19는 허버 손실에서 δ=10⁻³을 사용하여 냉각 어닐링 데이터셋에 적합화된 접근 방식 3을 보여줍니다. 그림 12와 마찬가지로 왼쪽에는 방정식 2에 나와 있는 형태의 법칙에 대한 분석을, 오른쪽에는 방정식 1에 나와 있는 형태의 법칙에 대한 분석을 제시합니다. 이 그림은 다양한 모델 크기와 훈련 토큰 수에 걸쳐 여러 아키텍처에서 냉각 일정이 스케일링 법칙에 미치는 영향을 보여줍니다. 특히, 냉각 일정을 변경하면 최적의 모델 크기와 토큰 수에 대한 예측이 어떻게 달라지는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 19: Approach 3 fitted on the cooldown ablation dataset using δ=10−3𝛿superscript103\delta=10^{-3}italic_δ = 10 start_POSTSUPERSCRIPT - 3 end_POSTSUPERSCRIPT in the Huber loss. Corresponds to Figure 19. As in Figure 12, we present an analysis over laws of the from shown in Equation 2 on the left and laws of the form shown in Equation 1 on the right.
> </details>



![](https://arxiv.org/html/2502.06857/x22.png)

> 🔼 그림 20은 그리드 검색 크기(x축)와 예측된 토큰의 기울기(y축)를 보여줍니다. 델타 값을 다르게 하여 작은 그리드 크기에서 델타 10⁻⁵가 매우 불안정하다는 것을 확인했습니다. 왼쪽 그림은 1000억 토큰 미만의 데이터만 사용하여 적합한 결과를 보여주고, 오른쪽 그림은 최대 3500억 토큰까지의 모든 데이터를 사용한 결과를 보여줍니다. 더 많은 데이터를 포함하면 델타 10⁻⁴, 10⁻⁵에 대해 더 작은 그리드 크기에서 발견된 지수의 안정성이 향상됨을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 20: We plot the size of the grid search as the x axis and the gradient of the prescribed tokens as the y axis. We vary delta and see that a delta of 10−5superscript10510^{-5}10 start_POSTSUPERSCRIPT - 5 end_POSTSUPERSCRIPT is highly unstable when fitting on smaller grid sizes. On the left, we plot only fitting on data less than 100100100100 billion tokens. On the right, we plot fitting on all data up to 350350350350 billion tokens. We see that including more data increases the stability of the exponents found for smaller grid sizes for deltas 10−4,10−5superscript104superscript10510^{-4},10^{-5}10 start_POSTSUPERSCRIPT - 4 end_POSTSUPERSCRIPT , 10 start_POSTSUPERSCRIPT - 5 end_POSTSUPERSCRIPT.
> </details>



![](https://arxiv.org/html/2502.06857/x23.png)

> 🔼 그림 21은 논문의 주요 데이터셋에 대해 식 (3) 형태의 가정을 사용하여 적합된 접근 방식 3을 보여줍니다. 이 그림은 다양한 모델 크기와 훈련 토큰 수에 대한 최적의 모델 너비와 깊이를 보여줍니다. 또한, 산점도는 실제 모델과 예측된 모델 간의 관계를 보여줍니다. 이를 통해 연구진은 제안된 방법이 다양한 모델 아키텍처에 대해 일관된 결과를 제공함을 보여주고자 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 21: Approach 3 fitted on our main dataset using an ansatz of the form shown in Equation 3.
> </details>



![](https://arxiv.org/html/2502.06857/x24.png)

> 🔼 그림 22는 논문에서 제시된 아키텍처를 기반으로 ±5%의 오차 범위 내에서 선택 가능한 모든 모델 형태를 보여줍니다. 원으로 표시된 점들은 가능한 모든 모델 형태를 나타내고, 별표로 표시된 점들은 실제로 선택된 모델 형태를 나타냅니다. 여기에는 너비가 512인 모델을 네 개 갖도록 추가로 선택한 두 개의 점도 포함되어 있습니다. 이 그림은 다양한 너비와 깊이를 가진 모델들을 훈련시켜 스케일링 법칙에 대한 더욱 포괄적인 분석을 수행하기 위한 저자의 접근 방식을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 22:  All possible model shapes we could have chosen based on our architecture within ±5%plus-or-minuspercent5\pm 5\%± 5 % are shown as circles. The points we selected are highlighted as stars, including the two extra points we select to have four models of width 512512512512.
> </details>



![](https://arxiv.org/html/2502.06857/x25.png)

> 🔼 그림 23은 논문에서 주요하게 다룬 22개 모델의 학습 과정에서 손실 값의 변화를 보여주는 그래프입니다. x축은 토큰(token)의 수(로그 스케일), y축은 손실 값(loss)입니다. 각 선은 하나의 모델에 대한 손실 값의 변화를 나타내며, 모델의 너비와 깊이에 따라 서로 다른 양상을 보입니다. 이 그림은 다양한 모델 구조와 크기에 따른 학습 성능의 차이를 시각적으로 비교 분석하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 23: Loss curves for the main 22222222 training runs.
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