---
title: "How to Synthesize Text Data without Model Collapse?"
summary: "합성 데이터 기반 언어 모델 학습의 붕괴 문제 해결: 토큰 편집 기법 제시!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Tsinghua University",]
showSummary: true
date: 2024-12-19
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.14689 {{< /keyword >}}
{{< keyword icon="writer" >}} Xuekai Zhu et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-20 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.14689" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.14689" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/how-to-synthesize-text-data-without-model" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM) 학습에 합성 데이터를 활용하는 것은 미래의 핵심 기술이지만, 합성 데이터의 무분별한 사용은 **모델 성능 저하** 및 **모델 붕괴** 문제를 야기할 수 있습니다. 기존 연구는 주로 반복적인 자기 생성 데이터에 대한 학습에서의 붕괴 현상에 초점을 맞췄으나, 본 연구는 **반복적이지 않은 모델 붕괴** 문제에 집중합니다.  본 연구는 다양한 비율의 합성 데이터를 사용한 LLM 사전 학습을 통해, **합성 데이터 비율이 높아질수록 성능이 저하**됨을 실험적으로 증명합니다.  또한, 합성 데이터의 분포 및 특징 분석을 통해 **분포 붕괴** 및 **n-gram 특징 과농축** 현상을 발견합니다.



본 연구는 이러한 문제를 해결하기 위해, **인간이 생성한 데이터에 대한 토큰 단위의 편집**을 통해 **반합성 데이터(semi-synthetic data)**를 생성하는 새로운 기법을 제시합니다. 이 기법은 이론적으로 **테스트 오류의 상한선을 제한**하여 모델 붕괴를 방지하는 효과를 갖습니다.  다양한 사전 학습 및 미세 조정 실험을 통해 **토큰 편집 기법이 데이터 품질 향상 및 모델 성능 개선**에 효과적임을 검증합니다.  본 연구는 합성 데이터를 활용한 LLM 학습의 안전성 및 효율성을 높이는 데 크게 기여하며, **새로운 데이터 생성 및 모델 학습 방식**에 대한 연구를 위한 기반을 마련합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 합성 데이터의 비율이 높을수록 언어 모델 성능이 저하된다는 사실을 밝힘 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 모델 붕괴를 방지하는 새로운 데이터 합성 방법인 '토큰 편집' 기법을 제시하고 이론적 근거를 제시함 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 다양한 실험 결과를 통해 토큰 편집 기법의 효과를 검증하여 모델 성능 향상을 보임 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **합성 데이터를 사용한 언어 모델 학습의 붕괴 문제**를 해결하는 데 중요한 의미를 가집니다.  **합성 데이터의 과도한 사용이 모델 성능 저하로 이어질 수 있다는 점을 밝히고**, 이를 방지하기 위한 **토큰 편집 기법**을 제시합니다. 이는 **합성 데이터 생성 및 활용 전반에 걸쳐 영향력 있는 연구**이며, 향후 **대규모 언어 모델의 개발 및 훈련 방식에 시사점**을 제공합니다.  더 나아가, **이론적 증명과 실험적 검증을 통해 제시된 방법의 효과를 입증**함으로써,  합성 데이터 활용에 대한 연구의 새로운 지평을 열었습니다. 

------
#### Visual Insights



![](https://arxiv.org/html/2412.14689/x1.png)

> 🔼 그림 1은 합성 데이터의 모델 붕괴 현상을 보여줍니다. ① 기존 모델은 이전에 생성한 데이터로 지속적으로 학습하며, 모델 성능이 점차 저하되는 모델 붕괴 현상을 보입니다. 실제 데이터 (xo, yo)에서 시작하여, 모델 f0가 합성 데이터 (y1, y2,…, yn)로 반복 학습함에 따라, 테스트 오류 Et⁢e⁢s⁢t가 증가합니다. ② 본 논문에서 제안하는 ToEdit 방법은 순수하게 합성 데이터를 생성하는 대신, 훈련된 모델을 사용하여 토큰 수준에서 데이터를 수정합니다. 훈련된 모델 f0와 연산 행렬 mi를 활용하여 데이터를 수정함으로써, 테스트 오류가 고정된 상한선 내에 제한됩니다. 따라서, 분포 범위를 유지하여 모델 붕괴를 방지할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Model collapse of synthetic data. ① The model continuously trains on its previously generated data, leading to a gradual decline in model performance, i.e., model collapse. Starting from real data (xo,yo)subscript𝑥𝑜subscript𝑦𝑜(x_{o},y_{o})( italic_x start_POSTSUBSCRIPT italic_o end_POSTSUBSCRIPT , italic_y start_POSTSUBSCRIPT italic_o end_POSTSUBSCRIPT ), the test error Et⁢e⁢s⁢tsubscript𝐸𝑡𝑒𝑠𝑡E_{test}italic_E start_POSTSUBSCRIPT italic_t italic_e italic_s italic_t end_POSTSUBSCRIPT increases as f0subscript𝑓0f_{0}italic_f start_POSTSUBSCRIPT 0 end_POSTSUBSCRIPT undergoes iterative training on synthetic data (y1,y2,…,yn)subscript𝑦1subscript𝑦2…subscript𝑦𝑛(y_{1},y_{2},\dots,y_{n})( italic_y start_POSTSUBSCRIPT 1 end_POSTSUBSCRIPT , italic_y start_POSTSUBSCRIPT 2 end_POSTSUBSCRIPT , … , italic_y start_POSTSUBSCRIPT italic_n end_POSTSUBSCRIPT ). ② ToEdit (ours), we use a trained model for token-level editing rather than purely synthesizing data. Leveraging f0subscript𝑓0f_{0}italic_f start_POSTSUBSCRIPT 0 end_POSTSUBSCRIPT and an operation matrix misubscript𝑚𝑖m_{i}italic_m start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT to edit the data, the test error is constrained within a fixed upper bound. Therefore, we can preserve the distribution coverage to avoid model collapse.
> </details>





{{< table-caption >}}
|                     | ArXiv | Books2 | Books3 | Math  | Enron | EuroParl | FreeLaw | GitHub | PG-19  | HackerNews | NIH   | Avg   |
| :------------------ | :---- | :----- | :----- | :---- | :---- | :------ | :------ | :----- | :---- | :-------- | :---- | :---- |
| Human data          | 22.26 | 25.39  | 22.87  | 10.84 | 23.50 | 30.73   | 12.04   | 4.15   | 16.88 | 32.54     | 23.53 |       |
| 25% Synthetic Data | 21.86 | 26.32  | 23.87  | 11.05 | 24.85 | 35.02   | 12.84   | 4.35   | 17.99 | 33.80     | 23.76 |       |
| 50% Synthetic Data | 22.50 | 28.01  | 25.75  | 10.84 | 26.56 | 41.99   | 14.02   | 4.67   | 19.70 | 36.12     | 24.61 |       |
| 75% Synthetic Data | 24.35 | 31.19  | 28.98  | 11.81 | 30.30 | 56.32   | 16.03   | 5.30   | 22.75 | 40.44     | 26.19 |       |
| Synthetic Data     | 35.60 | 43.72  | 47.72  | 17.25 | 66.97 | 129.75  | 29.62   | 12.00  | 50.14 | 87.95     | 39.48 |       |
|                     | OpenSubts | OWT2  | Phil  | Pile-CC | PubMed-A | PubMed-C | StackEx | Ubuntu | USPTO  | Wikipedia | Youtube | Avg   |
| Human data          | 28.08   | 25.77 | 33.56 | 26.78  | 18.97   | 15.49   | 10.81  | 20.86 | 19.32  | 24.31     | 21.54 | 21.37 |
| 25% Synthetic Data | 29.25   | 26.94 | 34.63 | 27.83  | 19.55   | 15.38   | 11.03  | 22.32 | 19.58  | 25.88     | 22.63 | 22.31 |
| 50% Synthetic Data | 31.00   | 28.76 | 37.48 | 29.36  | 20.51   | 15.89   | 11.54  | 23.53 | 20.51  | 27.57     | 24.91 | 23.90 |
| 75% Synthetic Data | 34.18   | 32.04 | 42.39 | 32.17  | 22.33   | 16.92   | 12.55  | 26.54 | 22.21  | 30.68     | 28.98 | 27.03 |
| Synthetic Data     | 57.83   | 53.94 | 78.18 | 54.69  | 34.82   | 23.87   | 20.47  | 51.78 | 37.24  | 46.12     | 65.49 | 49.30 |{{< /table-caption >}}

> 🔼 표 1은 GPT-2 Small(124M) 모델을 다양한 비율의 합성 데이터와 실제 데이터를 혼합하여 사전 훈련시킨 결과를 보여줍니다.  표에는 합성 데이터의 비율이 증가함에 따라 perplexity(PPL) 값이 증가하는 것을 보여주며, 이는 그림 2의 결과를 뒷받침합니다.  즉, 모델 성능이 합성 데이터 비율이 높아질수록 저하됨을 보여줍니다.  각 데이터셋(ArXiv, Books2, Books3, Math, Enron, EuroParl, FreeLaw, GitHub, PG-19, HackerNews, NIH, OpenSubtitles, OWT2, Phil, Pile-CC, PubMed-A, PubMed-C, StackExchange, Ubuntu, USPTO, Wikipedia, Youtube)에 대한 PPL 값을 비교하여 합성 데이터의 영향을 자세히 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: PPL evaluation results for GPT-2 Small (124M) pre-trained on data mixture. The PPL increases as the proportion of synthetic data grows, providing further confirmation of Figure 2.
> </details>





### In-depth insights


#### Synthetic Data Risks
합성 데이터는 다양한 응용 분야에서 매력적인 대안이지만, **모델 붕괴** 와 같은 심각한 위험성을 내포하고 있습니다. 모델 붕괴는 합성 데이터의 반복적인 사용으로 인해 모델이 실제 데이터 분포를 제대로 학습하지 못하고 합성 데이터에 과적합되는 현상을 말합니다. 이는 모델의 일반화 능력을 저하시켜 성능 저하로 이어집니다. 또한, **합성 데이터의 품질** 또한 중요한 문제입니다. 품질이 낮은 합성 데이터는 모델 학습에 부정적인 영향을 미치고, 예측 성능을 떨어뜨릴 수 있습니다. **데이터 분포의 불일치** 또한 주요 위험 요소입니다. 합성 데이터와 실제 데이터의 분포가 다를 경우, 모델은 실제 데이터에 대해 잘못된 예측을 할 수 있습니다. 따라서 합성 데이터를 사용할 때는 이러한 위험성들을 충분히 인지하고, 모델 붕괴 및 품질 저하를 방지하기 위한 적절한 조치를 취해야 합니다.  **데이터 증강 기법** 과 같은 다양한 방법을 통해 이러한 위험을 완화할 수 있습니다.

#### Token-Level Editing
토큰 수준 편집(Token-Level Editing)은 합성 데이터 생성을 위한 새로운 방법으로, **기존의 순차적 합성 데이터 생성 방식의 한계를 극복하기 위해 제안되었습니다.**  기존 방법들은 반복적인 학습 과정에서 모델이 자체 생성 데이터에 과적합되어 성능이 저하되는 모델 붕괴(Model Collapse) 현상을 초래합니다.  반면 토큰 수준 편집은 인간이 생성한 데이터의 일부 토큰을 사전 훈련된 언어 모델의 확률 분포를 기반으로 재샘플링하여 **데이터의 다양성을 유지하면서도 모델 과적합을 방지하는 데 중점을 둡니다.** 이를 통해 테스트 오류가 유한한 상한선으로 제한되고, **모델 붕괴 현상을 효과적으로 예방**할 수 있습니다.  본 논문에서는 이러한 토큰 수준 편집 방법에 대한 이론적 분석 및 실험적 검증을 통해, **합성 데이터의 품질을 향상시키고 모델 성능을 개선**할 수 있음을 보여줍니다. 특히, 초기 데이터의 분포를 유지하면서 데이터의 질을 개선하는 데 초점을 맞춰, 다양한 사전 훈련 및 미세 조정 실험을 통해 그 효과를 확인하였습니다.  이는 **대규모 언어 모델 훈련에서 합성 데이터 활용의 새로운 가능성**을 제시하는 중요한 결과입니다.

#### Non-iterative Collapse
본 논문에서 제시된 '비반복적 붕괴(Non-iterative Collapse)' 개념은 **합성 데이터가 언어 모델 학습에 미치는 영향을 평가하는 새로운 관점**을 제시합니다. 기존의 반복적 붕괴 연구가 자체 생성 데이터의 반복적 학습에 초점을 맞춘 반면, 이 논문은 **합성 데이터와 실제 데이터의 직접적인 혼합**이 모델 성능 저하를 유발할 수 있음을 보여줍니다. 이는 **합성 데이터의 비율이 높아질수록 모델 성능이 떨어지는 부정적 상관관계**를 통해 입증됩니다.  **합성 데이터의 분포 및 특징 분석** 결과, 합성 데이터는 실제 데이터의 긴 꼬리 분포를 놓치고 특정 n-gram 특징에 과도하게 집중되는 현상을 보입니다.  이러한 **분포 붕괴(Coverage Collapse)**와 **특징 과집중(Over-concentration)**은 모델의 일반화 능력을 저해하는 주요 원인으로 작용합니다.  결론적으로,  **단순한 합성 데이터의 사용은 모델 붕괴를 초래할 수 있으며, 실제 데이터 기반의 추가적인 전략이 필요**함을 시사합니다.

#### Theoretical Bounds
이 논문의 '이론적 경계(Theoretical Bounds)' 부분은 **모델 붕괴 문제를 해결하기 위한 제안된 방법의 효과를 수학적으로 뒷받침하는 데 중점**을 둡니다.  구체적으로는, **토큰 편집 기법을 통해 생성된 준합성 데이터에 대한 테스트 오차가 유한한 상한선으로 제한될 수 있음을 이론적으로 증명**합니다. 이는 반복적인 학습 과정에서 발생할 수 있는 누적 오류로 인한 모델 성능 저하를 방지할 수 있음을 시사합니다.  **이론적 증명은 선형 모델을 기반**으로 하지만, **실험 결과는 다양한 언어 모델의 사전 학습, 지속적 사전 학습, 그리고 지도 학습 미세 조정 과정에서 일관되게 성능 향상**을 보여줌으로써, 이론적 분석의 실용성을 강조합니다.  **유한한 상한선은 모델 붕괴 현상을 막는 핵심**이며, **토큰 편집 기법이 데이터 품질 향상에 기여**한다는 점을 보여주는 중요한 결과입니다.  결론적으로, 이론적 경계 설정은 제안된 방법의 견고성과 신뢰성을 확보하는 데 중요한 역할을 수행합니다.

#### Future Directions
본 논문은 합성 데이터를 사용한 언어 모델 학습에서의 모델 붕괴 문제를 해결하기 위한 토큰 편집 기법을 제안합니다. **미래 연구 방향**으로는, 먼저 **다양한 유형의 합성 데이터 생성 및 적용**에 대한 연구가 필요합니다. 현재는 텍스트 데이터에 중점을 두고 있지만, 이미지, 오디오 등 다양한 모달리티의 데이터에 대한 연구 확장이 중요합니다. 또한, **토큰 편집 기법의 효율성 및 성능 개선**을 위한 연구가 필요합니다. 현재 기법은 단일 전방 패스만을 사용하지만, 더욱 정교한 알고리즘을 통해 성능을 높일 수 있습니다. 마지막으로, **모델 붕괴 방지 및 합성 데이터 품질 향상**을 위한 이론적 토대 마련이 중요합니다.  현재 이론적 분석은 선형 모델에 국한되어 있으므로, 더욱 복잡한 모델에 대한 연구가 필요합니다. 이러한 미래 연구를 통해 합성 데이터를 활용한 언어 모델 학습의 안정성과 성능을 크게 향상시킬 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.14689/x2.png)

> 🔼 그림 2는 인공지능 합성 데이터 또는 인간 및 합성 데이터의 혼합물을 사용하여 언어 모델을 처음부터 학습시킬 때 성능 저하가 발생하는 비반복적 모델 붕괴 현상을 보여줍니다. 합성 데이터의 비율이 증가함에 따라 성능 저하가 심해지는 음의 상관관계를 보입니다. A는 인간 데이터(Dolma (Soldaini et al., 2024))와 합성 데이터(Cosmopedia (Ben Allal et al., 2024))를 사용하여 GPT-2 Small (124M)을 사전 훈련시킨 결과를 보여줍니다. 합성 데이터 비율이 증가함에 따라 모델 손실은 감소하지만, B에서 보는 것처럼 검증 세트에서의 PPL(퍼플렉서티)은 증가합니다. 이러한 경향은 다양한 검증 세트에서 일관되게 나타납니다. 하위 작업에 대한 자세한 결과는 그림 10과 11에 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Non-iterative model collapse. Training language models from scratch on AI-synthesized data or a mixture of human and synthetic data leads to performance degradation. This degradation is negatively correlated with the proportion of synthetic data used in training. A. We pre-train GPT-2 Small (124M) on human (Dolma (Soldaini et al., 2024)) and synthetic (Cosmopedia (Ben Allal et al., 2024)) data. As the proportion of synthetic data increases, the model’s loss decreases. B. As the proportion of synthetic data increases, the PPL also rises. This trend remains consistent across different validation sets. More results on downstream tasks are presented in 10 and  11.
> </details>



![](https://arxiv.org/html/2412.14689/x3.png)

> 🔼 그림 3은 Llama-3-8B를 사용하여 추정한 인간이 생성한 데이터와 합성 데이터의 PPL 분포를 보여줍니다. 합성 데이터는 인간이 생성한 데이터의 긴 꼬리를 갖지 않고, 인간이 생성한 데이터 분포의 처음 25% 내에 집중되어 있습니다. (A) 인간이 생성한 데이터의 분포는 긴 꼬리를 가진 뾰족한 분포로 0에서 100 이상의 넓은 범위에 걸쳐 있습니다. (B) 합성 데이터의 값은 훨씬 더 좁은 범위인 0에서 12 사이에 집중되어 있습니다. 이 실험에서는 인간이 생성한 데이터로 Dolma v6을, 합성 데이터로 Cosmopedia를 사용했으며, 각각 60억 개의 토큰을 샘플링했습니다. 그림 9에 추가 결과가 나와 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: PPL distribution of human and synthetic data estimated by Llama-3-8B. The synthetic data lacks the long tail of the human-produced data and is also concentrated within the first 25%percent2525\%25 % of the human-produced data distribution. A. Distribution of human-produced data is sharp with a long tail, spanning a wide range from 0 to over 100. B. The values are concentrated within a much narrower range, mostly between 0 and 12. The experiment uses Dolma v6 and Cosmopedia as human and synthetic data, each with sampled 6B tokens. More results in Figure 9.
> </details>



![](https://arxiv.org/html/2412.14689/x4.png)

> 🔼 그림 4는 두 가지 하위 그림으로 구성되어 있습니다. 그림 4A는 t-SNE와 sentence-transformer를 사용하여 인간이 작성한 데이터, 합성 데이터, DSIR(Data Selection via Importance Resampling) 기법으로 선택된 합성 데이터의 임베딩을 시각화한 것입니다.  이를 통해 각 데이터 유형 간의 분포 차이를 명확히 보여줍니다. 그림 4B는 선택된 합성 데이터와 다른 데이터 혼합물을 사용하여 OLMo-237M 모델을 사전 훈련한 결과를 보여줍니다.  다양한 합성 데이터 비율에 따른 성능 변화를 보여주어, 합성 데이터 사용의 영향과 최적 혼합 비율을 파악하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: A. Embedding visualization using t-SNE and sentence-transformers. B. pre-training results for selected synthetic data and other data mixtures.
> </details>



![](https://arxiv.org/html/2412.14689/x5.png)

> 🔼 그림 5는 10,000개의 해시 버킷에 걸쳐 단일구 및 이중구 특징의 분포를 보여줍니다. 인간이 생성한 데이터는 넓은 범위에 걸쳐 분포되어 있지만, 합성 데이터는 몇몇 특정 버킷에 집중되어 있습니다. 이는 합성 데이터가 인간이 생성한 데이터의 다양성을 충분히 포착하지 못하고, 특정 특징에 과도하게 집중되어 있음을 시사합니다. 이러한 현상은 모델 붕괴 현상과 밀접한 관련이 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Uni/Bi-gram feature distribution across 10,000 hash buckets.
> </details>



![](https://arxiv.org/html/2412.14689/x6.png)

> 🔼 그림 6은 Qwen-0.5B-Instruct 모델을 사용하여 Dolma-sampled V6 데이터셋의 토큰 확률 분포를 나타낸 그림입니다.  이 그림은 단순히 U자형 분포를 보여주는 것 이상으로,  언어 모델이 학습한 데이터의 토큰에 대한 확률 분포가 양 끝단(확률이 매우 높거나 매우 낮은 토큰)에 집중되어 있음을 시각적으로 보여줍니다. 이는 중간 영역의 토큰들이 상대적으로 낮은 확률을 가지며,  모델이 일부 토큰 패턴에 과도하게 집중하는 현상을 나타냅니다. 이러한 U자형 분포는 후속 절에서 설명하는 토큰 편집 기법(Token-level Editing)의 이론적 근거를 제공합니다.  즉,  모델이 확률이 높은 토큰에 과도하게 의존하는 경향을 수정하여,  더욱 다양하고 균형잡힌 데이터셋을 생성하기 위한 토대가 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: U-shape token probability distribution of Dolma-sampled V6 estimated by Qwen-0.5B-Instruct (qwe, 2024).
> </details>



![](https://arxiv.org/html/2412.14689/x7.png)

> 🔼 그림 7은 OLMo-237M 언어 모델을 인간이 생성한 데이터(Dolma)와 합성 데이터(Cosmopedia)를 섞어서 사전 훈련시킨 결과를 보여줍니다.  다양한 비율로 인간 데이터와 합성 데이터를 섞어서 모델을 훈련시켰고, 그 결과를 그래프로 나타냈습니다. 이를 통해 합성 데이터의 비율이 높아짐에 따라 모델 성능에 미치는 영향을 분석합니다.  x축은 훈련에 사용된 데이터의 양(토큰 수)을 나타내고, y축은 손실(loss) 값을 나타냅니다.  합성 데이터의 비율이 높을수록 손실 값이 감소하지만, 실제 성능은 오히려 떨어질 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: OLMo-237M pretraining with mixed human and synthetic data proportions. We pretrain the OLMo-237M model using a mixture of human data (Dolma (Soldaini et al., 2024)) and synthetic data (Cosmopedia (Ben Allal et al., 2024)).
> </details>



![](https://arxiv.org/html/2412.14689/x8.png)

> 🔼 그림 8은 GPT-2 언어 모델을 처음부터 학습시킬 때, 합성 데이터의 비율을 달리하여 학습시킨 결과를 보여줍니다.  x축은 학습에 사용된 토큰의 수 (십억 단위)이고, y축은 다양한 검증 데이터셋(Wikitext-103, RedPajama, Falcon-RefinedWeb, c4-en)에 대한 GPT-2의 perplexity(PPL) 값입니다.  PPL은 모델의 성능을 나타내는 지표로, 값이 낮을수록 성능이 좋음을 의미합니다.  각 선은 합성 데이터의 비율이 다른 경우(0%, 25%, 50%, 75%, 100%)의 결과를 나타냅니다.  이 그림은 합성 데이터의 비율이 높아질수록 모델의 성능이 저하됨을 보여주는 것을 목적으로 합니다.  즉, 순수 합성 데이터로만 학습한 모델의 성능이 가장 낮고, 실제 데이터만으로 학습한 모델의 성능이 가장 높다는 것을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: GPT-2 perplexity (PPL) on validation sets, trained from scratch.
> </details>



![](https://arxiv.org/html/2412.14689/x9.png)

> 🔼 그림 9는 StabLM-Zephyr-3B를 사용하여 추정된 인간 데이터와 합성 데이터의 PPL 분포를 보여줍니다. 이 그림은 서로 다른 사전 분포를 사용하더라도 동일한 결과를 얻을 수 있음을 보여주는 Figure 3과 일치합니다. 합성 데이터는 긴 꼬리를 가지지 않고 분포의 좁은 영역에 집중되어 있음을 보여줍니다. 다시 말해, 합성 데이터는 인간 데이터의 다양성과 복잡성을 충분히 포착하지 못하고, 인간 데이터 분포의 하위 25%에만 집중되어 있음을 시각적으로 보여줍니다.  이러한 결과는 합성 데이터가 인간이 생성한 데이터의 복잡성을 충분히 반영하지 못한다는 것을 의미하며, 이로 인해 모델 붕괴가 발생할 가능성을 높입니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: PPL distribution of human and synthetic data estimated by StabLM-Zephyr-3B. This indicates that different prior distributions yielded the same result, which is consistent with Figure 3. The synthetic data lacks a long tail and is concentrated within a narrow portion of the distribution.
> </details>



![](https://arxiv.org/html/2412.14689/x10.png)

> 🔼 그림 10은 Dolma, Cosmopedia 및 DSIR로 선택된 데이터셋에서 개별적으로 샘플링된 1M개의 하위 집합에서 상위 40개의 이중 그램을 보여줍니다. 이 그림은 각 데이터셋에서 가장 빈번하게 나타나는 이중 그램들을 시각적으로 비교하여, 세 데이터셋의 언어적 특징과 분포의 차이를 보여줍니다.  Dolma는 인간이 생성한 데이터셋, Cosmopedia는 합성 데이터셋, DSIR은 선택된 데이터셋으로, 이들의 이중 그램 분포를 비교함으로써 각 데이터셋의 특징과 한계를 파악할 수 있습니다. 특히, 인간이 생성한 데이터셋과 합성 데이터셋 간의 이중 그램 분포 차이를 통해 합성 데이터셋의 한계점을 보여주고, DSIR을 통해 선택된 데이터셋이 두 데이터셋의 특징을 어떻게 반영하는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: The top 40 bi-grams from separately sampled 1M subsets of Dolma, Cosmopedia, and DSIR-selected datasets.
> </details>



![](https://arxiv.org/html/2412.14689/x11.png)

> 🔼 그림 11은 Dolma, Cosmopedia 및 DSIR 선택 데이터 세트의 개별적으로 샘플링된 1M 하위 집합에서 상위 64개의 이중 그램을 보여줍니다. 이 그림은 각 데이터 세트에서 가장 자주 나타나는 2개의 단어 조합을 시각적으로 비교하여, 데이터 세트 간의 차이점과 유사점을 파악하는 데 도움을 줍니다. 특히, 인간이 생성한 텍스트(Dolma)와 합성 텍스트(Cosmopedia) 사이의 n-gram 특징의 차이를 보여줍니다. DSIR 선택 데이터 세트는 인간이 생성한 데이터와 합성 데이터의 특징을 모두 포함하도록 설계되었으므로, 세 데이터 세트 모두에서 상위 n-gram 특징의 분포가 어떻게 다른지 보여주는 것이 중요합니다. 이 비교를 통해 합성 데이터 생성 시 발생할 수 있는 문제점(예: 특징 과잉 집중)을 이해하고 개선하는 데 도움이 될 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: The top 64 bi-grams from separately sampled 1M subsets of Dolma, Cosmopedia, and DSIR-selected datasets.
> </details>



![](https://arxiv.org/html/2412.14689/x12.png)

> 🔼 그림 12는 합성 데이터에서 특징들의 붕괴 문제를 더 자세히 보여주는 밀도 샘플링 응답 값을 보여줍니다.  x축은 해시 함수의 인덱스를 나타내고 y축은 해당 해시 버킷에 있는 특징들의 빈도를 나타냅니다.  이 히트맵은 합성 데이터의 특징들이 소수의 특징 버킷에 과도하게 집중되어 있음을 시각적으로 보여줍니다. 이는 합성 데이터가 실제 데이터의 다양한 특징들을 제대로 반영하지 못하고 있다는 것을 의미하며, 모델 붕괴 문제의 원인이 됨을 보여줍니다. 이러한 밀도 샘플링 응답 값은 앞서 언급된 분포 및 특징 분석 결과를 더욱 강화하며, 합성 데이터의 한계를 명확히 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Density sampling response values. This result further confirms the issue of feature collapse in synthetic data.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Models | MQP | ChemProt | PubMedQA | RCT | USMLE | Average |
|---|---|---|---|---|---|---|
| OLMo-1B | 52.59 | 17.2 | 51.40 | 32.70 | 28.90 | 36.63 |
| CPT | 52.29 | 21.00 | 58.50 | 34.90 | 27.49 | 38.83 |
| Δ ToEdit | 54.59 | 22.40 | 65.00 | 34.50 | 27.96 | 40.89 |
| LLama-3-8B | 66.80 | 28.59 | 60.8 | 73.85 | 40.61 | 54.13 |
| CPT | 72.29 | 29.4 | 69.1 | 72.65 | 36.76 | 56.04 |
| Δ ToEdit | 76.39 | 30.2 | 65.3 | 73.30 | 37.23 | 56.48 |
|  |  |  |  |  |  |  |
| Models | HeadLine | FPB | FiQA-SA | ConvFinQA | NER | Average |
|---|---|---|---|---|---|---|
| OLMo-1B | 69.00 | 47.03 | 48.05 | 4.83 | 62.19 | 46.22 |
| CPT | 70.31 | 49.78 | 40.36 | 18.72 | 60.44 | 47.92 |
| Δ ToEdit | 71.77 | 51.39 | 46.06 | 18.85 | 62.97 | 50.21 |
| LLama-3-8B | 81.28 | 63.58 | 81.60 | 52.88 | 72.53 | 70.37 |
| CPT | 85.68 | 54.22 | 81.88 | 67.78 | 67.43 | 71.40 |
| Δ ToEdit | 83.83 | 61.61 | 80.82 | 67.31 | 67.62 | 72.24 |
|  |  |  |  |  |  |  |
| Models | ARC-c | GPQA | GSM8K | MATH | MMLU | Average |
|---|---|---|---|---|---|---|
| OLMo-1B | 28.67 | 24.23 | 1.67 | 0.00 | 26.56 | 16.23 |
| CPT | 28.41 | 24.03 | 1.52 | 0.10 | 27.23 | 16.26 |
| Δ ToEdit | 28.92 | 28.12 | 2.20 | 0.10 | 23.63 | 16.59 |{{< /table-caption >}}
> 🔼 표 2는 지속적 사전 훈련 모델에 대한 도메인별 과제 성능을 보여줍니다. CPT는 지속적 사전 훈련을 나타내고, ΔΔ Δ는 저희가 편집한 데이터를 사용한 훈련을 나타냅니다. 이 표는 OLMo-1B와 Llama-3-8B 모두에서 세 가지 도메인에 걸쳐 일관된 성능 향상을 보여줍니다.  즉, 본 논문에서 제시된 토큰 편집 기법을 사용하여 생성된 반합성 데이터를 사용한 지속적 사전 훈련이 OLMo-1B 와 Llama-3-8B 모델 모두에서 생의학, 금융, 수학 세 가지 도메인의 다양한 하위 작업에서 성능 향상을 가져왔음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Performance on domain-specific tasks for continual pre-training models. CPT indicates continual pre-training. ΔΔ\Deltaroman_Δ denotes training with our edited data. Our method demonstrates consistent improvements across three domains on both OLMo-1B and Llama-3-8B.
> </details>

{{< table-caption >}}
|           | PIQA | BoolQ | OBQA | ARC-c | ARC-e | HellaSwag | SIQA | Winogrande | Average |
| :--------- | :----: | :----: | :----: | :----: | :----: | :-------: | :----: | :--------: | :------: |
| OLMo-1B (PT) | 53.97 | 38.26 | 12.20 | 17.23 | 28.36 |  26.02   | 34.80 |   51.14   |  32.75  |
| <div style="text-align:left;">Δ ToEdit</div> | 54.13 | 38.65 | 12.80 | 18.43 | 27.48 |  25.94   | 34.95 |   52.49   |  33.11  |{{< /table-caption >}}
> 🔼 표 3은 사전 훈련된 기본 모델들의 일반적인 성능을 보여줍니다. PT는 OLMo-1B를 처음부터 사전 훈련시켰음을 나타냅니다. 실험 결과는 제안된 방법이 사전 훈련의 효과를 높일 수 있음을 보여줍니다. 이 표는 다양한 하류 작업(하류 과제)에서 OLMo-1B와 ToEdit(제안된 방법 적용) 모델의 성능을 비교하여, ToEdit을 사용했을 때 사전 훈련된 모델의 성능이 향상되었는지를 보여줍니다.  각 하류 작업의 성능은 해당 작업에 맞는 지표를 사용하여 측정됩니다.  표에서 확인할 수 있듯이,  대부분의 하류 작업에서 ToEdit을 적용한 모델이 기본 OLMo-1B 모델보다 더 나은 성능을 보여주고 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: General performance of the pre-trained base models. PT indicates we pre-train OLMo-1B from scratch. Experimental results demonstrate that our method can also enhance the effectiveness of pre-training.
> </details>

{{< table-caption >}}
|       | Models       | PIQA  | BoolQ | HellaSwag | SIQA  | Winogrande | Average |
| :---- | :----------- | :---- | :---- | :-------- | :---- | :--------- | :------ |
| Instruction Tuning |             |       |       |           |       |           |        |
| _Natural Instructions_ | Llama-3-8B | 79.82 | 87.06 | 58.32     | 46.83 | 74.66      | 69.34  |
| Δ ToEdit             |             | 80.58 | 87.80 | 58.27     | 46.93 | 74.90      | 69.70  |
| _CoT_                 | Llama-3-8B | 79.87 | 81.28 | 59.72     | 49.69 | 74.51      | 69.01  |
| Δ ToEdit             |             | 80.25 | 81.16 | 59.74     | 50.56 | 74.59      | 69.26  |
| _FLAN v2_             | Llama-3-8B | 80.79 | 84.04 | 59.98     | 51.43 | 74.66      | 70.18  |
| Δ ToEdit             |             | 80.69 | 85.20 | 59.99     | 52.00 | 75.37      | 70.65  |
| _Open Assistant 1_   | Llama-3-8B | 79.65 | 83.18 | 60.51     | 48.52 | 74.11      | 69.19  |
| Δ ToEdit             |             | 79.98 | 83.91 | 60.34     | 48.31 | 74.66      | 69.44  |{{< /table-caption >}}
> 🔼 표 4는 지시 조정 및 코드 추론 작업을 사용하여 LLaMA-3-8B를 미세 조정한 결과를 보여줍니다. 제안된 방법으로 생성된 편집된 버전과의 성능을 비교하여 본 연구의 접근 방식이 지시 조정 및 코드 추론 작업에 사용되는 데이터를 향상시킬 수 있음을 보여줍니다. 표에는 다양한 지시 조정 및 코드 추론 작업에 대한 성능 지표가 포함되어 있으며, 편집된 데이터를 사용했을 때의 성능 향상 정도를 수치적으로 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Performance of the SFT models. We fine-tune LLaMA-3-8B using instruction tuning and code reasoning tasks, comparing performance with the edited version produced by our method. The experimental results indicate that our approach can enhance the data for instruction-tuning and code reasoning tasks.
> </details>

{{< table-caption >}}
|   | Models | ARC-c | GPQA | GSM8K | MMLU | Average |
|---|---|---|---|---|---|---|
| *Code Reasoning* |  |  |  |  |  |  |
| *OSS-Instruct-75K* | Llama-3-8B | 51.28 | 27.46 | 49.58 | 62.14 | 45.76 |
|  | Δ ToEdit | 51.79 | 28.79 | 49.36 | 62.04 | 46.13 |
| *Evol-Instruct-110K* | Llama-3-8B | 52.90 | 27.90 | 50.87 | 62.40 | 46.62 |
|  | Δ ToEdit | 52.22 | 29.69 | 50.87 | 62.60 | 46.92 |{{< /table-caption >}}
> 🔼 표 5는 다양한 샘플링 전략에 따른 결과를 보여줍니다.  본 논문에서는 top-k, top-p, rejection 세 가지 샘플링 방법을 사용하여 언어 모델 학습에 미치는 영향을 비교 분석했습니다.  각 샘플링 방법의 장단점(계산 효율성, 성능)을 제시하며, 실험 결과를 통해 top-k 샘플링 방법의 효율성과 성능 측면에서의 우수성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 5:  Results of different sampling strategies.
> </details>

{{< table-caption >}}
| Sampling Strategy | PubMedQA | MedMCQA | MedQA (4 options) |
|---|---|---|---| 
| Top-k | 64.5 | 26.13 | 24.82 |
| Top-p | 63.8 | 27.11 | 25.61 |
| Reject Sampling | 64.5 | 28.90 | 28.20 |{{< /table-caption >}}
> 🔼 본 표는 top-k 샘플링에서 샘플 크기 k에 대한 추가 실험 결과를 보여줍니다.  다양한 k 값 (예: k=8, k=64)에 대해 세 가지 하위 작업(PubMedQA, MedMCQA, MedQA(4 options))의 성능을 비교하여 최적의 샘플 크기를 결정하는 데 도움이 되는 정보를 제공합니다.  표의 결과는 계산 효율성과 성능 간의 균형을 고려하여 하이퍼파라미터 k를 선택하는 데 유용한 지침을 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 6:  Ablation study on sampling size k𝑘kitalic_k for top-k.
> </details>

{{< table-caption >}}
| Sampling Size (<math>k</math>) | PubMedQA | MedMCQA | MedQA (4 options) |
|---|---|---|---|
| <math>k=8</math> | 64.5 | 26.13 | 24.82 |
| <math>k=64</math> | 63.8 | 28.14 | 27.34 |{{< /table-caption >}}
> 🔼 표 7은 생의학 분야에서 재표본화된 토큰 조건(p)의 성능에 미치는 영향을 보여줍니다.  다양한 p 값에 따른 여러 설정에서의 성능 변동을 보여줍니다.  p 값이 클수록 재표본화되는 토큰 수가 적어지고, p 값이 작을수록 재표본화되는 토큰 수가 많아집니다. 성능과 데이터 분포 유지를 고려하여 임계값으로 p=0.99를 설정했습니다.
> <details>
> <summary>read the caption</summary>
> Table 7:  Performance impact of different resampled token condition (p𝑝pitalic_p) in Biomedicine domain.
> </details>

{{< table-caption >}}
|   | PubMedQA | MQP | RCT | USMLE | ChemProt | Avg |
|---|---|---|---|---|---|---|
| $p \geq 0.99$ | 64.5 | 55.73 | 30.95 | 27.65 | 14.6 | 38.69 |
| $p \geq 0.999$ | 63.6 | 55.4 | 29.09 | 28.12 | 16.2 | 38.48 |
| $p \leq 0.1$ | 62.4 | 51.47 | 25.6 | 29.14 | 10.0 | 35.72 |
| $p \leq 0.01$ | 65.4 | 54.91 | 28.19 | 27.80 | 11.0 | 37.46 |
| $p \leq 0.001$ | 64.2 | 56.39 | 35.0 | 27.80 | 12.4 | 39.16 |{{< /table-caption >}}
> 🔼 표 8은 BioMed 데이터셋에서 토큰의 확률 분포를 다양한 확률 범위별로 보여줍니다.  각 범위(예: 0.0-0.1, 0.1-0.2 등)에 속하는 토큰의 비율과 개수를 나타내어, BioMed 데이터셋 내 토큰의 확률 분포 특징을 분석하는 데 사용됩니다. 이 표는 합성 데이터의 긴 꼬리(long tail) 부족 및 특정 영역에 대한 과도한 집중 현상과 같은 문제점을 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 8:  Token distribution across different probability ranges in BioMed dataset.
> </details>

{{< table-caption >}}
| Probability Range | Percentage | Token Count |
|---|---|---|
| 0.0-0.1 | 34.7% | 388,626,330 |
| 0.1-0.2 | 8.1% | 90,716,809 |
| 0.2-0.3 | 5.4% | 60,477,872 |
| 0.3-0.4 | 4.4% | 49,278,266 |
| 0.4-0.5 | 3.8% | 42,558,503 |
| 0.5-0.6 | 3.6% | 40,318,546 |
| 0.6-0.7 | 3.7% | 41,438,924 |
| 0.7-0.8 | 4.0% | 44,798,424 |
| 0.8-0.9 | 5.2% | 58,238,944 |
| 0.9-1.0 | 27.1% | 303,543,988 |{{< /table-caption >}}
> 🔼 표 9는 Natural Instructions 데이터셋에서 토큰 수정이 필요한 비율을 보여줍니다. 총 토큰 수는 4,671,834개이며, 'Gen'은 'Generation'(세대)을 의미합니다. 이 표는 토큰 수정이 필요한 비율이 세대가 거듭될수록 감소하는 경향을 보여줍니다. 즉, 초기 세대(Gen 1)에서는 수정이 필요한 토큰의 비율이 높지만, 세대가 진행될수록 그 비율이 점차 감소합니다. 이는 모델이 학습을 거듭하면서 데이터 분포의 변화에 적응하고, 수정이 필요한 토큰의 수가 줄어든다는 것을 의미합니다. 이 표는 본 논문에서 제시하는 토큰 편집 방법의 효과를 보여주는 중요한 증거입니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Percentage of tokens requiring edits in the Natural-Instructions dataset. The total number of tokens is 4,671,834. and “Gen” is short for “Generation”.
> </details>

{{< table-caption >}}
| **Tokens (p&gt;0.99)** | **Gen 1 (source)** | **Gen 2** | **Gen 3** |
|---|---|---|---|
| 584,103 | 12.5% | 11.76% | 11.08% |{{< /table-caption >}}
> 🔼 표 10은 GPT-2 모델을 사용하여 훈련시킨 후, 다운스트림 작업(Maini et al., 2024)에서 사람이 작성한 데이터와 합성 데이터의 성능을 비교한 결과를 보여줍니다.  사람이 작성한 데이터, 25%, 50%, 75%의 합성 데이터를 섞은 데이터, 그리고 순수 합성 데이터로 훈련시킨 GPT-2 모델의 TruthfulQA, LogiQA, Winogrande, PIQA, ARC-E, BoolQ, OBQA 작업에 대한 성능(정확도)을 보여줍니다. 이를 통해 합성 데이터의 비율이 증가함에 따라 모델 성능이 어떻게 변하는지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 10:  Comparison of human and synthetic data performance across downstream tasks in (Maini et al., 2024), based on training with GPT-2.
> </details>

{{< table-caption >}}
|                   | TruthfulQA | LogiQA | Wino. | PIQA | ARC-E | BoolQ | OBQA | Avg |
| :----------------- | :----------: | :-----: | :----: | :---: | :----: | :----: | :---: | :--: |
| Human Data         |    32.68     |  23.03  |  51.3  | 64.42 |  44.4  | 60.98 |  15   | 41.69 |
| 25% Synthetic Data |    27.91     |  21.37  | 50.12  | 63.93 | 43.94 | 62.29 | 15.4  | 40.71 |
| 50% Synthetic Data |    30.84     |  22.58  | 52.41  | 63.33 | 44.02 | 62.14 |  16   | 41.62 |
| 75% Synthetic Data |    29.5      |  22.65  |  49.8  | 63.44 | 44.53 | 61.56 | 17.2  | 41.24 |
| Synthetic Data     |    28.89     |  22.58  | 49.72  |  63   |  46.3  | 54.53 | 16.8  | 40.26 |{{< /table-caption >}}
> 🔼 표 11은 OLMo-237M 모델을 사용하여 훈련했을 때, 인간이 작성한 데이터와 합성 데이터의 성능을 다운스트림 작업에서 비교한 결과를 보여줍니다. 표에는 다운스트림 작업(TruthfulQA, LogiQA, Wino, PIQA, ARC-E, OBQA, Avg)에 대한 각 데이터 유형의 성능과 표준 오차가 포함되어 있습니다. 이 표는 합성 데이터 사용이 모델 성능에 미치는 영향을 평가하는 데 도움이 됩니다.  Maini et al.(2024)의 연구 결과를 바탕으로 하였습니다.
> <details>
> <summary>read the caption</summary>
> Table 11:  Comparison of human and synthetic data performance across downstream tasks in (Maini et al., 2024), based on training with OLMo-237M. ± indicates the standard error.
> </details>

{{< table-caption >}}
|               | TruthfulQA | LogiQA | Wino. | PIQA  | ARC-E | OBQA  | Avg   |
| :------------ | :----------: | :-----: | :----: | :----: | :----: | :----: | :----: |
| Human Data    | 26.81 ± 1.550 | 21.06 ± 1.028 | 52.01 ± 1.404 | 56.69 ± 1.156 | 31.73 ± 0.9550 | 13.80 ± 1.543 | 33.68 |
| 25% Synthetic Data | 26.44 ± 1.543 | 21.25 ± 1.032 | 52.64 ± 1.403 | 57.02 ± 1.155 | 31.78 ± 0.9552 | 12.40 ± 1.475 | 33.59 |
| 50% Synthetic Data | 25.95 ± 1.534 | 20.04 ± 1.099 | 52.25 ± 1.408 | 56.64 ± 1.126 | 31.82 ± 0.9557 | 12.80 ± 1.495 | 33.25 |
| 75% Synthetic Data | 25.34 ± 1.522 | 20.87 ± 1.025 | 50.43 ± 1.405 | 55.60 ± 1.159 | 32.74 ± 0.9629 | 12.00 ± 1.454 | 32.83 |
| Synthetic Data | 23.01 ± 1.473 | 20.29 ± 1.014 | 49.33 ± 1.405 | 55.93 ± 1.158 | 33.33 ± 0.9673 | 14.20 ± 1.562 | 32.68 |{{< /table-caption >}}
> 🔼 본 표는 GPT-2 124M 모델을 인간이 작성한 데이터와 합성 데이터의 혼합물로 사전 훈련했을 때의 퍼플렉서티(PPL) 결과를 보여줍니다.  다양한 비율의 합성 데이터(0%, 25%, 50%, 75%, 100%)를 사용하여 모델을 훈련시켰고, 훈련 데이터 크기(토큰 수)와 에포크 수에 따른 PPL 값을 여러 개의 검증 세트(Wikitext-103, RedPajama, Falcon-RefinedWeb, c4-en, mc4-en)에 대해 제시합니다. 이를 통해 합성 데이터 비율이 모델 성능에 미치는 영향을 정량적으로 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 12: PPL results of GPT-2 124M pretraining on mixture of human and synthetic data.
> </details>

{{< table-caption >}}
| Synthetic Data Ratio | 25% | 25% | 25% | 25% | 25% | 50% | 50% | 50% | 50% | 50% | 75% | 75% | 75% | 75% | 75% |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Tokens Size | 8.4B | 16.8B | 25.2B | 33.6B | 42B | 8.4B | 16.8B | 25.2B | 33.6B | 42B | 8.4B | 16.8B | 25.2B | 33.6B | 42B |
| Epochs | 1 | 2 | 3 | 4 | 5 | 1 | 2 | 3 | 4 | 5 | 1 | 2 | 3 | 4 | 5 |
| Wikitext-103 | 45.97 | 39.87 | 37.65 | 36.91 | 36.32 | 50.29 | 43.15 | 40.46 | 39.43 | 38.65 | 58.66 | 48.75 | 45.20 | 43.42 | 42.95 |
| RedPajama | 42.28 | 37.62 | 35.72 | 34.66 | 34.24 | 46.89 | 41.42 | 39.37 | 38.21 | 37.72 | 55.72 | 49.26 | 46.27 | 44.81 | 44.30 |
| Falcon-RefinedWeb | 56.40 | 50.62 | 48.26 | 47.13 | 46.66 | 61.06 | 54.34 | 51.72 | 50.39 | 49.87 | 69.32 | 61.50 | 58.28 | 56.77 | 56.19 |
| c4-en | 48.15 | 43.14 | 40.98 | 39.91 | 39.41 | 51.79 | 46.06 | 43.90 | 42.73 | 42.23 | 58.60 | 52.22 | 49.26 | 47.87 | 47.27 |
| mc4-en | 62.46 | 56.80 | 54.35 | 53.06 | 52.71 | 70.43 | 62.48 | 59.61 | 57.66 | 57.07 | 80.37 | 71.77 | 67.90 | 65.31 | 64.82 |{{< /table-caption >}}
> 🔼 표 13은 인간이 작성한 데이터와 합성 데이터를 섞어 OLMo-237M 언어 모델을 사전 훈련시킨 결과입니다.  다양한 비율의 합성 데이터를 사용하여 모델 성능에 미치는 영향을 PPL(Perplexity) 지표를 통해 분석한 결과를 보여줍니다.  합성 데이터의 비율이 증가함에 따라 PPL 값이 변화하는 양상을 확인할 수 있습니다.  표에는 다양한 검증 데이터셋에 대한 PPL 결과가 포함되어 있으며, 합성 데이터의 사용이 모델 성능에 어떤 영향을 미치는지 자세히 분석하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 13: PPL results of OLMo-237M pretraining on mixture of human and synthetic data.
> </details>

{{< table-caption >}}
| Synthetic Data Ratio | 0% | 25% | 50% | 75% | 100% | DSIR (1M) | DSIR (10M) | Edu Classifier (1M) | Edu Classifier (10M) | PPL Filter (1M) | PPL Filter (10M) | Density Sampling (1M) | Density Sampling (10M) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---| 
| Unique Tokens | 8.4B | 8.4B | 8.4B | 8.4B | 8.4B | 0.6B | 8.4B | 0.75B | 7.4B | 0.97B | 9B | 0.6B | 7.1B |
| Training Tokens | 8.4B | 8.4B | 8.4B | 8.4B | 8.4B | 8.4B | 8.4B | 10.5B | 7.4B | 13.68B | 9B | 8.9B | 7.1B |
| Epochs | 1 | 1 | 1 | 1 | 1 | 14 | 1 | 14 | 1 | 14 | 1 | 14 | 1 |
| Wikitext-103 | 187.36 | 185.5 | 260.08 | 367.46 | 1605.73 | 1309.53 | 1757.03 | 1111.29 | 1612.95 | 738.36 | 1193.25 | 1188.40 | 1753.89 |
| RedPajama | 175.38 | 183.93 | 236.33 | 301.09 | 907.91 | 649.36 | 916.51 | 811.14 | 1104.75 | 376.36 | 645.82 | 789.67 | 896.18 |
| Falcon-RefinedWeb | 165.17 | 166.69 | 199.68 | 245.15 | 523.93 | 573.61 | 510.96 | 522.97 | 612.72 | 344.82 | 449.86 | 501.99 | 560.92 |
| c4-en | 123.88 | 127.68 | 147.69 | 174.48 | 410.19 | 457.96 | 404.63 | 415.88 | 487.97 | 286.95 | 367.44 | 414.55 | 457.71 |
| mc4-en | 208.91 | 208.94 | 263.35 | 324.91 | 800.40 | 861.01 | 823.12 | 769.86 | 955.70 | 476.81 | 662.00 | 740.75 | 844.53 |
| M2D2-Wiki | 88.24 | 87.34 | 107.77 | 114.19 | 189.06 | 234.45 | 183.17 | 161.58 | 206.45 | 130.43 | 162.08 | 167.20 | 205.50 |
| M2D2-S2ORC | 86.15 | 81.53 | 97.61 | 100.64 | 204.22 | 170.78 | 496.40 | 145.27 | 201.52 | 117.44 | 163.38 | 131.22 | 192.97 |{{< /table-caption >}}
> 🔼 표 14는 서로 다른 세 가지 인공 데이터 생성 방법, 즉 순수 합성 데이터(Cosmopedia), 준합성 데이터(Rephrasing the Web), 그리고 토큰 편집 기반 준합성 데이터(ToEdit)를 비교 분석한 표입니다. 각 방법은 데이터 생성 방식, 데이터 유형, 그리고 실험 결과(모델 붕괴 발생 여부 또는 성능 향상 여부)를 제시하여 서로 다른 인공 데이터 생성 방법의 특징과 효과를 비교하고 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 14: Comparison of different synthetic data methods.
> </details>

{{< table-caption >}}
| Method | Data Type | Approach | Result |
|---|---|---|---| 
| Cosmopedia (Ben Allal et al., 2024) | Pure synthetic | Using a prompt to induce data from LLMs. | Reveal non-iterative model collapse. |
| Rephrasing the Web (Maini et al., 2024) | Semi-synthetic | Using a prompt and source content to guide LLMs to reformat source content. | Improve training performance. |
| ToEdit (Ours) | Semi-synthetic | Using the distribution of source content estimated by LLMs (single forward pass) to replace tokens. | Improve training performance. |{{< /table-caption >}}
> 🔼 표 15는 순수 인간 데이터 또는 합성 데이터로 GPT-2 124M을 사전 훈련시킨 결과의 퍼플렉서티(PPL)를 보여줍니다.  다양한 토큰 크기(8.4B, 16.8B, 25.2B, 33.6B, 42B)와 에폭(1, 2, 3, 4, 5)에 따른 퍼플렉서티 값을 Wikitext-103, RedPajama, Falcon-RefinedWeb, c4-en, mc4-en 데이터셋에서 비교 분석하여 인간 데이터와 합성 데이터의 성능 차이를 보여줍니다. 이 표는 합성 데이터만을 사용한 경우 모델 성능에 미치는 영향을 자세히 분석하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 15: PPL results of GPT-2 124M pretraining on pure Human or Synthetic data.
> </details>

{{< table-caption >}}
| Data Type | Human Data (Dolma) |  |  |  |  | Synthetic Data (Cosmopedia) |  |  |  |  | 
|---|---|---|---|---|---|---|---|---|---|---|
| Tokens Size | 8.4B | 16.8B | 25.2B | 33.6B | 42B | 8.4B | 16.8B | 25.2B | 33.6B | 42B |
| Epochs | 1 | 2 | 3 | 4 | 5 | 1 | 2 | 3 | 4 | 5 |
| Wikitext-103 | 43.62 | 38.57 | 36.11 | 34.89 | 34.55 | 169.38 | 147.73 | 135.23 | 131.78 | 128.05 |
| RedPajama | 40.18 | 35.84 | 33.97 | 32.74 | 32.34 | 116.37 | 103.25 | 99.27 | 96.81 | 96.03 |
| Falcon-RefinedWeb | 54.85 | 49.10 | 46.93 | 45.43 | 44.90 | 146.97 | 132.60 | 127.68 | 124.32 | 122.69 |
| c4-en | 45.87 | 41.00 | 39.10 | 37.95 | 37.56 | 128.25 | 114.41 | 109.73 | 107.53 | 106.55 |
| mc4-en | 61.00 | 54.44 | 52.11 | 50.38 | 49.74 | 171.44 | 153.70 | 150.28 | 145.44 | 144.99 |{{< /table-caption >}}
> 🔼 표 16은 Soldaini 외의 2024년 논문에서 인용한 Dolma 데이터셋(v1.6)의 통계를 보여줍니다.  UTF-8 바이트(GB), 문서 수(백만), 유니코드 단어 수(십억), Llama 토큰 수(십억)와 같은 다양한 측면에서 데이터셋의 크기와 구성을 나타냅니다. 각 숫자는 데이터셋에 포함된 Common Crawl 웹 페이지, Stack Overflow 코드, Wikipedia, Wikibooks, Reddit 소셜 미디어, PubMed 기사, 그리고 Project Gutenberg 도서와 같은 다양한 소스의 데이터 양을 보여줍니다.  이 표는 Dolma 데이터셋의 규모와 다양한 소스로부터의 데이터 분포를 이해하는 데 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 16: Dolma dataset statistics (v1.6), quoted from source (Soldaini et al., 2024).
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