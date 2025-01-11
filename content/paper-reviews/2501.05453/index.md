---
title: "An Empirical Study of Autoregressive Pre-training from Videos"
summary: "본 연구는 비디오 데이터를 사용한 자기회귀적 사전 학습의 효과를 최초로 체계적으로 연구한 것입니다.  연구진은 'Toto'라는 새로운 비디오 모델을 제시하며, 이는 비디오를 시각적 토큰 시퀀스로 처리하고 미래 토큰을 예측하도록 훈련됩니다.  **1조 개 이상의 시각적 토큰**으로 구성된 방대한 데이터셋을 사용하여 여러 하류 작업(이미지 인식, 비디오 분류,..."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Video Understanding", "🏢 UC Berkeley",]
showSummary: true
date: 2025-01-09
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.05453 {{< /keyword >}}
{{< keyword icon="writer" >}} Jathushan Rajasegaran et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-10 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.05453" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.05453" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/an-empirical-study-of-autoregressive-pre" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

최근 자연어 처리 분야에서 자기회귀적 사전 학습 모델이 큰 성공을 거두었지만, 비디오 데이터에 대한 연구는 상대적으로 부족했습니다.  기존의 비디오 모델링 방법들은 종종 특정 작업에 대한 지도 학습이나 제한적인 자기 지도 학습에 의존하며, 대규모 비디오 데이터셋을 효과적으로 활용하지 못하는 한계가 있었습니다. 따라서 **대규모 비디오 데이터셋을 효과적으로 활용하고 다양한 하류 작업에 적용 가능한 새로운 비디오 모델링 프레임워크**가 필요했습니다. 

본 연구에서는 이러한 문제를 해결하기 위해 'Toto'라는 새로운 자기회귀적 비디오 모델을 제시합니다.  Toto는 비디오를 시각적 토큰의 시퀀스로 처리하고, **미래 토큰을 예측하는 방식으로 사전 학습**됩니다. **1조 개 이상의 시각적 토큰**으로 구성된 대규모 데이터셋을 사용하여 다양한 하류 작업(이미지 인식, 비디오 분류, 객체 추적, 로보틱스 등)에서 **경쟁력 있는 성능**을 달성했습니다.  또한, 자기회귀적 비디오 모델의 스케일링 법칙에 대한 새로운 통찰력을 제시하여, 향후 **대규모 비디오 모델의 개발 및 성능 향상**에 기여할 것으로 기대됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 비디오 데이터를 사용한 자기회귀적 사전 학습은 다양한 하류 작업에서 경쟁력 있는 성능을 달성할 수 있다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 새로운 비디오 모델 아키텍처 'Toto'는 대규모 비디오 데이터셋에서 효과적으로 학습되며, 여러 하류 작업에서 우수한 성능을 보인다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 자기회귀적 비디오 모델의 스케일링 법칙은 언어 모델과 유사하지만, 그 비율은 다르다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **비디오에 대한 자기회귀적 사전 학습의 효과**를 실증적으로 연구한 최초의 연구 중 하나입니다.  **대규모 비디오 데이터셋**을 사용하여 다양한 하류 작업에서 경쟁력 있는 성능을 달성한 새로운 비디오 모델 아키텍처를 제시합니다. 이는 **자기회귀적 모델링의 스케일링 법칙**에 대한 새로운 통찰력을 제공하며, 앞으로의 연구 방향을 제시합니다. 특히 **비디오 이해 분야의 발전**에 중요한 의미를 지니며, 향후 연구에서 더욱 큰 규모의 모델과 데이터를 사용한 연구에 영감을 줄 것입니다.  **다양한 하류 작업에 대한 벤치마크 결과**는  비디오 모델링 연구자들에게 귀중한 자료가 될 것입니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.05453/x1.png)

> 🔼 본 그림은 논문에서 제시하는 전체 프레임워크를 보여줍니다. 다양한 데이터셋으로부터 이미지와 비디오 프레임을 가져와 각 프레임/이미지를 독립적으로 이산적인 시각적 토큰으로 변환합니다. 변환된 토큰들을 사용하여, 4K 토큰 길이(이미지 또는 비디오 프레임)의 문맥을 사용하여 다음 시각적 토큰을 예측하는 방식으로 트랜스포머를 사전 훈련합니다. 훈련이 완료되면 중간 표현을 추출하여 다양한 하위 작업에 대해 평가합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Overall Framework. Starting with images and video frames from a collection of datasets, we tokenize each frame/image into discrete visual tokens independently. We pre-train the transformer by predicting the next visual tokens, with a context length of 4K tokens of images or video frames. Once trained, we take the intermediate representations and evaluate them on various tasks.
> </details>





{{< table-caption >}}
| Model | Params | Dimension | Heads | Layers |
|---|---|---|---|---|
| base | 120m | 768 | 12 | 12 |
| large | 280m | 1024 | 16 | 16 |
| 1b | 1.1b | 2048 | 16 | 22 |{{< /table-caption >}}

> 🔼 이 표는 논문의 3.2절(Architecture)에서 다양한 규모의 모델에 대한 구조 정보를 보여줍니다.  'base', 'large', '1b' 세 가지 크기의 모델이 있으며, 각 모델은 매개변수 수, 차원, 헤드 수, 레이어 수 등의 주요 하이퍼파라미터가 다릅니다. 이러한 모델들은 이미지와 비디오의 시각적 토큰들로만 사전 훈련되었다는 점을 강조합니다.  즉,  텍스트 데이터는 사용되지 않았습니다. 모델 크기가 커짐에 따라 매개변수 수, 차원, 헤드 수, 레이어 수 모두 증가하여 모델의 표현 능력이 향상되는 것을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Model Architecture: We pre-train models at different scales, only on visual tokens from images and videos.
> </details>





### In-depth insights


#### Autoregressive Video
자기회귀적 비디오 모델은 비디오 프레임을 시퀀스로 취급하여 **미래 프레임을 예측**하는 방식으로 학습됩니다. 이는 자연어 처리 분야의 자기회귀적 언어 모델과 유사한 접근 방식입니다. **비디오를 토큰 시퀀스로 변환**하고, 변환기 모델을 사용하여 다음 토큰을 예측하도록 훈련시키는 것이 핵심입니다. 이러한 모델은 대규모 비디오 데이터셋으로 사전 훈련되어 다양한 하위 작업에 대한 강력한 시각적 표현을 학습합니다.  **다양한 토큰화 기법, 아키텍처 및 훈련 전략**을 실험하여 성능을 개선하는 연구가 진행되고 있습니다.  **대규모 모델 스케일링**을 통해 성능 향상을 얻을 수 있지만, 언어 모델과 비교했을 때 그 효율성은 다릅니다.  **다운스트림 작업에 대한 적용성**을 평가하기 위해 이미지 인식, 비디오 분류, 객체 추적 및 로보틱스와 같은 다양한 벤치마크를 활용합니다.  **자기회귀적 모델은 생성 능력과 인식 능력 모두에서 경쟁력있는 성능**을 보여주지만,  **데이터 품질 및 다양성**에 대한 의존도가 높다는 한계가 있습니다.

#### Toto Model
이 논문에서 제시된 Toto 모델은 비디오 데이터를 이용한 자기회귀적 사전 학습에 대한 실험적 연구의 핵심입니다. **비디오 프레임을 시각적 토큰으로 처리**하여 변환기 모델을 이용해 미래 토큰 예측을 수행하는 자기회귀적 접근 방식을 사용합니다. **1조 개 이상의 시각적 토큰으로 구성된 방대한 비디오 및 이미지 데이터셋**으로 사전 학습되며, 이미지 인식, 비디오 분류, 객체 추적 등 다양한 하위 작업에서 경쟁력 있는 성능을 보여줍니다. **최소한의 귀납적 편향에도 불구하고 경쟁력 있는 성능**을 달성하며, 모델 확장에 따른 성능 향상 곡선이 언어 모델과 유사하지만 상이한 속도를 보인다는 점이 흥미롭습니다. **다양한 토크나이저, 아키텍처, 훈련 및 추론 전략**을 탐구하여 이러한 결과를 도출합니다.  **토큰화 방식에 대한 실험**을 통해 이 선택이 하위 작업 성능에 미치는 영향이 제한적임을 보여줍니다. 결론적으로 Toto 모델은 자기회귀적 사전 학습을 통한 비디오 모델링 분야에서 중요한 발전을 제시하며, 향후 연구를 위한 기반을 마련합니다.

#### Downstream Tasks
논문에서 다운스트림 작업에 대한 심층적인 분석은 **다양한 비전 관련 작업에서 사전 훈련된 모델의 일반화 능력을 평가하는 데 중점**을 둡니다. 이미지 인식, 동작 인식, 동작 예측, 반자동 추적, 물체 영속성, 로봇 제어와 같이 광범위한 과제를 통해 모델의 강력한 기능과 일반화 가능성을 보여줍니다. 특히, **자연어 모델과 유사한 스케일링 동향**을 보이는 것은 흥미로운 결과입니다. 즉, 모델의 크기와 성능 간의 관계를 보여주는 계산 최적화 스케일링을 통해 **비전 모델도 대규모 언어 모델과 마찬가지로 계산 비용 증가에 따라 성능이 향상됨**을 나타냅니다. 하지만, 인터넷 기반 비디오 데이터의 품질 및 다양성, 토크나이저의 제한, 비디오 프레임의 중복성 등 여러 가지 제한점도 함께 제시됩니다. 이러한 제한점은 향후 연구를 위한 중요한 방향을 제시합니다. 전체적으로, 본 연구는 **사전 훈련된 모델의 뛰어난 성능**을 다양한 비전 관련 작업에서 입증하고, 동시에 **향후 개선 및 발전 방향**을 제시하여  비전 분야의 연구에 중요한 기여를 할 것으로 예상됩니다.

#### Scaling Behaviors
본 논문에서 다룬 "스케일링 거동(Scaling Behaviors)" 분석은 **대규모 언어 모델(LLM)에서 관찰되는 스케일링 법칙이 비디오 모델에도 적용되는지, 그리고 그 차이점은 무엇인지**를 탐구하는 데 중점을 두었습니다.  연구진은 계산량 증가에 따른 성능 향상을 분석하여 **비디오 모델의 스케일링이 LLM보다 느리다는 점**을 발견했습니다. 이는 비디오 데이터의 고유한 특성, 즉 **시간적 및 공간적 상관관계의 복잡성** 때문으로 해석됩니다.  LLM은 순차적인 텍스트 데이터를 처리하지만, 비디오 모델은 더욱 복잡한 시공간 정보를 다루어야 하기 때문에 같은 수준의 성능 향상을 위해 더 많은 계산량이 필요합니다.  **최적의 스케일링 법칙을 찾기 위한 추가적인 연구**가 필요하며, **데이터의 다양성과 품질이 스케일링 거동에 미치는 영향**에 대한 심층적인 분석도 중요합니다.  **토큰화 전략 및 모델 아키텍처** 또한 스케일링 성능에 영향을 미치는 요인으로 고려되어야 합니다.

#### Future Work
본 논문은 비디오로부터의 자기회귀적 사전 학습에 대한 경험적 연구를 제시하며, 다양한 하류 작업에서 경쟁력 있는 성능을 달성합니다. 하지만, **인터넷 비디오의 품질과 다양성의 편차**로 인해 모델 성능에 영향을 미칠 수 있다는 한계점을 지적합니다. 또한, 토크나이저에 의존하는 방식은 **종단 간 학습이 아니며**, 토크나이저의 품질에 따라 표현 및 생성 품질이 제한될 수 있다는 점을 밝힙니다. 따라서, 미래 연구에서는 보다 정교하고 다양한 데이터셋을 사용하거나, 더욱 **강력하고 범용적인 비주얼 토크나이저**를 개발하는 방향으로 나아가야 합니다.  뿐만 아니라, **비디오 프레임의 중복성 문제**를 해결하고, 다양한 하류 작업에 대한 최적의 구성을 찾는 연구가 필요합니다.  **밀집 예측 작업이나 세밀한 인식, 복잡한 시간적 역동성**을 고려한 연구 또한 미래 과제로 제시됩니다. 종합적으로, 자기회귀적 사전 학습 모델의 효율성을 높이고, 다양한 작업에 적용 가능성을 확장하기 위한 심층적인 연구가 필요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.05453/extracted/6091816/figs/toto_blue.png)

> 🔼 그림 2는 다양한 크기의 모델(기본, 대형, 10억 매개변수)에 대한 학습 손실 곡선을 보여줍니다. 이러한 모델은 dVAE 토큰화기를 사용하여 훈련되었으며, 어휘 크기는 8,000이고 문맥 길이는 4,000토큰(16개의 이미지 또는 비디오 프레임에 해당)입니다. 이 그래프는 모델 크기에 따른 학습 진행 상황을 보여주는 시각적 자료입니다.  각 곡선은 학습 과정에서 손실 값이 어떻게 감소하는지 보여주며, 모델의 크기가 클수록 손실 감소 속도가 빠르다는 것을 나타냅니다. 이는 더 큰 모델이 더 효율적으로 학습 데이터를 학습할 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Training Loss Curves: We show the training loss curves for base, large, and 1b models trained with tokens from dVAE (Ramesh et al., 2021) with a vocabulary size of 8k and context length of 4k tokens (equivalent to 16 images or video frames).
> </details>



![](https://arxiv.org/html/2501.05453/extracted/6091816/figs/tokens1gram_blue.png)

> 🔼 이 그림은 ImageNet 검증 세트에서 다양한 토큰 생성기(dVAE (Ramesh et al., 2021), VQGAN-1k, VQGAN-16k (Esser et al., 2020))의 1-그램 토큰 분포를 보여줍니다. dVAE는 거의 모든 토큰에 대해 수렴하는 반면, VQGAN은 50% 미만의 토큰만을 포함한다는 것을 보여줍니다.  즉, dVAE 토큰화 방식은 VQGAN에 비해 ImageNet 데이터셋을 훨씬 더 잘 포괄적으로 나타냅니다.  이것은 토큰의 다양성과 표현력 측면에서 dVAE의 우수성을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: 1-gram Distribution of Various Tokens: This Figure shows the distribution of 1-gram tokens of various tokenizers (dVAE (Ramesh et al., 2021), VQGAN-1k, VQGAN-16k (Esser et al., 2020)) on Imagenet validation set. Note that, dVAE has almost full convergence of the tokens while VQGAN has less than 50% coverage of the tokens.
> </details>



![](https://arxiv.org/html/2501.05453/extracted/6091816/figs/robots/franka_pick_toto_blue.png)

> 🔼 표 4는 토큰 해상도의 영향을 보여줍니다. 낮은 해상도로 사전 훈련된 모델은 성능이 낮지만, 더 높은 해상도에서 다음 패치 예측을 위해 미세 조정하면 전체 해상도로 사전 훈련된 모델보다 성능이 우수해짐을 보여줍니다.  ROPE(Rotary Position Embedding)의 기본값은 50,000입니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Token Resolution: While the performance is lower for a low-resolution model, when finetuned for next-patch prediction at a higher resolution, its performance surpasses the full-resolution pre-trained model. ††{}^{\text{\textdagger}}start_FLOATSUPERSCRIPT † end_FLOATSUPERSCRIPT Base values of the RoPE is 50,000.
> </details>



![](https://arxiv.org/html/2501.05453/extracted/6091816/figs/robots/kuka_pick_toto_blue.png)

> 🔼 이 표는 같은 레이어에서 평가했을 때 어텐션 풀링이 중간 토큰의 평균 풀링보다 훨씬 더 나은 성능을 보여준다는 것을 보여줍니다.  어텐션 풀링은 토큰의 중요도를 동적으로 가중치를 부여하여 중간 표현을 생성하는 반면, 평균 풀링은 모든 토큰에 동일한 가중치를 부여합니다.  따라서, 어텐션 풀링은 다운스트림 작업에 더 적합한 표현을 생성합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Attention vs Average Pooling: When probed at the same layers, attention pooling performs much better than average pooling of intermediate tokens.
> </details>



![](https://arxiv.org/html/2501.05453/extracted/6091816/figs/robots/franka_cabinet_toto_blue.png)

> 🔼 그림 4는 세 가지 크기의 모델(기본, 큰, 10억 매개변수)에 대한 각 레이어의 어텐션 프로빙 성능을 보여줍니다. 세 가지 모델 모두에서 최고 성능은 모델의 약 50% 깊이에서 관찰됩니다. 이는 모델의 중간 레이어가 다운스트림 작업에 가장 유용한 표현을 학습한다는 것을 시사합니다.  초반 레이어는 저수준 특징을 추출하고, 후반 레이어는 과적합될 수 있으므로 중간 레이어가 최적의 균형을 이룹니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Probing at Different Layers: We show the attention-probing performance at each layer of our three models. Peak performance is observed at around 50% depth of the models.
> </details>



![](https://arxiv.org/html/2501.05453/extracted/6091816/figs/robots/kuka_cabinet_toto_blue.png)

> 🔼 그림 5는 준지도 학습 기반의 비디오 객체 추적 결과를 보여줍니다.  Jabri 등의 연구(2020)에서 제시된 방법을 따라, 정답(GT) 분할 마스크로 시작하여 Toto-large 모델이 계산한 특징을 사용하여 레이블을 전파합니다.  마스크는 정보 손실 없이 최대 60프레임까지 전파됩니다.  이 그림은 모델이 시간에 걸쳐 객체를 정확하게 추적하는 능력을 보여주는 시각적 증거를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Semi-Supervised Tracking: We follow the protocol in STC (Jabri et al., 2020), start with the GT segmentation mask, and propagate the labels using the features computed by Toto-large. The mask was propagated up to 60 frames without losing much information.
> </details>



![](https://arxiv.org/html/2501.05453/x2.png)

> 🔼 그림 6(a)는 강화 학습을 사용한 로봇 조작 실험 결과를 보여줍니다.  특히, Franka 로봇을 사용하여 물체를 집는 작업의 성공률을 시간에 따라 나타냅니다.  Toto-base 모델과 MVP-base 모델의 성능을 비교하여 Toto 모델이 작업 학습을 더 빠르게 수행함을 보여줍니다.  두 모델 모두 강화 학습을 통해 훈련되었으며, 성공률은 여러 번의 시도에 걸친 평균을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> (a) Franka Pick
> </details>



![](https://arxiv.org/html/2501.05453/extracted/6091816/figs/plot2x_vgpt_blue.png)

> 🔼 그림 (b)는 쿠카 로봇 암을 사용하여 물체를 집는 작업을 보여줍니다.  강화 학습을 통해 학습된 로봇 제어 정책의 성능을 평가하기 위해 다양한 시도를 거친 결과를 보여주는 그래프가 포함되어 있습니다.  이 그래프는 시도 횟수에 따른 성공률을 나타내며, Toto 기반 모델과 기존 MAE 기반 모델의 성능을 비교합니다. Toto 모델이 작업 학습에 더 빠르고 효율적인 것을 보여줍니다.  이 그림은 논문의 로봇 제어 부분에서 사용된 시뮬레이션 환경에서의 실험 결과를 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) Kuka Pick
> </details>



![](https://arxiv.org/html/2501.05453/extracted/6091816/figs/plot3_toto_blue.png)

> 🔼 그림 (c)는 로봇 조작 실험 중 프랑카 캐비닛 작업에 대한 성공률을 보여줍니다. 강화 학습을 통해 로봇이 캐비닛을 여는 작업을 수행하는 성공률을 여러 단계에 걸쳐 나타냅니다. Toto-base 모델과 MVP-base 모델의 성능을 비교하여 Toto-base 모델이 작업 학습 속도 면에서 더 우수함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (c) Franka Cabinet
> </details>



![](https://arxiv.org/html/2501.05453/extracted/6091816/figs/plot4_toto_blue.png)

> 🔼 그림 (d)는 쿠카 로봇 팔이 캐비닛 문을 여는 작업을 수행하는 강화 학습 과정을 보여줍니다.  Toto-base 모델과 MVP-base 모델의 성공률을 비교하여 Toto 모델이 작업 학습에 더 빠르고 효율적임을 시각적으로 보여줍니다.  각 막대 그래프는 특정 단계에서의 성공률을 나타내며, Toto-base 모델이 전반적으로 더 높은 성공률을 달성함을 알 수 있습니다. 이는 Toto 모델이 비디오 데이터로 사전 훈련되어 시각적 정보를 더 잘 처리하고 강화 학습 과정에서 더 효과적으로 학습할 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (d) Kuka Cabinet
> </details>



![](https://arxiv.org/html/2501.05453/extracted/6091816/figs/plot5_vgpt_blue.png)

> 🔼 그림 6은 강화 학습을 사용한 로봇 조작 실험 결과를 보여줍니다. Radosavovic et al.(2022)의 MAE-base 모델과 비교하여 Toto-base 사전 훈련 모델을 시뮬레이션 환경에서 Xiao et al.(2022)의 방법을 따라 평가했습니다. 각 모델의 평균 성공률을 훈련 단계에 따라 평가했습니다. Toto 모델은 MAE 모델보다 두 가지 로봇과 두 가지 작업에서 모두 학습 속도가 더 빨랐습니다. 그림은 네 가지 다른 로봇 조작 작업(Franka Pick, Kuka Pick, Franka Cabinet, Kuka Cabinet)에 대한 성공률 그래프를 보여줍니다. 각 그래프는 Toto-base 모델과 MAE-base 모델의 성공률을 훈련 단계에 따라 나타냅니다. 이를 통해 Toto 모델이 MAE 모델보다 학습 속도가 빠르다는 것을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Robot Manipulation with Reinforcement Learning: We compare MAE-base (Radosavovic et al., 2022) with Toto-base pre-trained models in simulation following Xiao et al. (2022). We evaluate each model the mean success rate over training steps. Toto was able to learn these tasks faster than MAE, across two robots and two tasks.
> </details>



![](https://arxiv.org/html/2501.05453/x3.png)

> 🔼 이 그림은 실제 로봇 환경에서 Toto-base 모델을 사용하여 큐브 집는 작업을 수행하는 예시를 보여줍니다.  Toto-base는 비교적 작은 모델이지만, 실시간으로 로봇을 제어하여 약 63%의 성공률을 달성했습니다.  이 그림은 Toto 모델의 실제 세계 적용 가능성을 보여주는 증거입니다.  Franka 로봇이 큐브를 집는 과정의 여러 단계가 순차적으로 나타나 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Real-world Deployment: We show an example episode of our policy performing the cube picking task on a Franka robot in the real world. We use Toto-base to run the robot at real time, despite being a small model, Toto was able to achieve about 63% success rate in real world setting.
> </details>



![](https://arxiv.org/html/2501.05453/extracted/6091816/figs/toto-large-k400-val-set.png)

> 🔼 그림 8은 다양한 작업에 대해 모델의 여러 계층에서의 동작을 보여줍니다. 이미지 분류, 동작 인식 및 객체 추적의 경우 모든 모델은 유사하게 동작하며 모델 깊이의 약 50%에서 최고 성능을 보입니다. 이러한 동작은 모든 모델 크기에서 관찰됩니다. 로봇 작업은 중간 계층이 물체를 집는 데 우수한 성능을 보이지만 마지막 계층도 중간 계층만큼 우수한 성능을 보이는 유사한 동작을 보입니다. 이러한 그래프는 디코더 전용 모델에서 모델의 전반부가 인코더처럼 동작하여 정보를 압축한 다음 모델의 후반부가 압축된 의미적 특징을 입력 공간으로 투영한다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Probing Across Layers, Models, and Tasks: We study the behavior of our models across multiple layers and tasks. For image classification, action recognition, and object tracking, all the models behave similarly and peak around 50% of the model depth. This behavior is observed across all model sizes. Robot tasks show a similar behaviour, where the middle layers perform good at picking the objects, but last layers also perform good as middle layers. These plots suggests, in decoder-only model, first half of the model starts to behave like an encoder, and compress the information, and then rest of the model, projects the compressed semantic features back to input space.
> </details>



![](https://arxiv.org/html/2501.05453/extracted/6091816/figs/tokens2gram_blue.png)

> 🔼 그림 9는 모델의 크기(은닉층 크기 및 깊이)를 증가시키면서 최적의 학습률을 사용하여 여러 가지 변형된 Toto 모델을 학습시킨 결과를 보여줍니다.  x축은 학습에 사용된 연산량(MACs, Multiply-Accumulate operations)을 나타내고, y축은 검증 손실을 나타냅니다.  이 그래프는 최적의 연산량을 사용했을 때 명확한 확장성을 보여줍니다. 즉, 연산량이 증가할수록 검증 손실이 감소하여 모델 성능이 향상됨을 의미합니다. 이는 모델의 크기를 키우는 것이 효과적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Scaling Toto: We train multiple variants of Toto, with increasing hidden size and depth, with optimal learning rates. We plot the validation loss vs the compute spent on training in MACs. This shows a clear scaling behavior with optimal compute.
> </details>



![](https://arxiv.org/html/2501.05453/extracted/6091816/figs/tokens3gram_blue.png)

> 🔼 그림 10은 Kinetics 검증 세트에서 토큰당 평균 손실을 보여줍니다. 첫 번째 프레임은 예측 손실이 더 높고, 나머지 프레임은 평균적으로 첫 번째 프레임보다 손실이 더 낮다는 것을 명확하게 보여줍니다. 이는 비디오의 중복성을 보여주는 것입니다. 즉, 다음 프레임을 예측하는 것이 상대적으로 쉬워서 손실이 낮아지는 것을 의미합니다. 이는 비디오 프레임 간의 높은 상관관계 때문에 발생합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Average Validation Loss Over Tokens: We show the average loss per token for kinetics validation set. It clearly shows the redundancy in videos, as the first frame has higher prediction loss, and rest of the frames on average has lower loss than the first frame.
> </details>



![](https://arxiv.org/html/2501.05453/extracted/6091816/figs/frames1.png)

> 🔼 이 표는 논문의 4.9절 컴퓨팅 최적 배율 조정(Compute Optimal Scaling) 섹션에 있는 그림으로,  Toto 모델의 크기를 조정하는 다양한 변형 모델들을 보여줍니다.  Toto 모델의 크기 조정은  (Yang et al., 2022; Touvron et al., 2023)의 연구를 따릅니다. 구체적으로,  은닉 차원(hidden dimension)과 레이어 수(number of layers)를 선형적으로 증가시키면서 헤드 수(number of heads)는 일정하게 유지합니다.  각 모델 변형에 대한 매개변수 수(Params), 차원(Dimension), 헤드 수(Heads), 레이어 수(Layers)를 명시적으로 제시하여  모델 크기 변화에 따른 성능 변화를 분석하는 데 사용됩니다.  이 표는 단순히 모델의 크기 정보만 제공하는 것이 아니라, 후속 실험에서 모델 크기 변화에 따른 성능 변화 분석 및 컴퓨팅 자원 효율성 평가의 기반을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 15: Toto Varients: We scale Toto models by increasing hidden dimension and number of layers linearly while keeping number of heads constant following (Yang et al., 2022; Touvron et al., 2023).
> </details>



![](https://arxiv.org/html/2501.05453/extracted/6091816/figs/frames2.png)

> 🔼 그림 11은 μ-파라미터화(Yang et al., 2022)를 사용하여 다양한 너비의 Toto 모델을 단일 최적 학습률 범위(2⁻⁷)로 학습할 수 있음을 보여줍니다. 이는 모델의 너비에 관계없이 일관된 최적 학습률을 찾을 수 있음을 의미하며, μ-파라미터화 기법이 모델 스케일링에 효과적임을 시사합니다. 그림은 다양한 너비의 Toto 모델에 대한 최적 학습률 곡선을 보여주며, 각 곡선의 최저점이 최적 학습률을 나타냅니다. 모든 곡선의 최저점이 비슷한 범위에 있으므로, μ-파라미터화를 통해 단일 최적 학습률로 다양한 크기의 모델을 효율적으로 학습할 수 있음을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: μ𝜇\muitalic_μ-Parameterization Learning Rate: We show that μ𝜇\muitalic_μ-Parameterization (Yang et al., 2022), we can train all width Toto models, with an single optimal learning rate of 2−7superscript272^{-7}2 start_POSTSUPERSCRIPT - 7 end_POSTSUPERSCRIPT.
> </details>



![](https://arxiv.org/html/2501.05453/extracted/6091816/figs/frames3.png)

> 🔼 이 그림은 ImageNet 검증 세트의 10,000개 이미지에 대해 계산된 다양한 토큰화 방법(dVAE, VQGAN-1k, VQGAN-16k)의 2-gram 분포를 보여줍니다.  dVAE 토큰화 방식은 VQGAN-1k 및 VQGAN-16k 토큰화 방식과 비교하여 더 많은 토큰 조합을 가지고 있음을 보여줍니다.  즉, dVAE는 이미지의 다양한 특징들을 더욱 세분화하여 나타내는 더욱 풍부한 토큰 집합을 생성한다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: 2-gram Distribution of Various Tokens: We compute the 2-gram distribution on 10000 images from the ImageNet validation set. Compared to VQGAN 1k and 16k vocabulary tokenizers, the dVAE tokenizer has a larger set of token combinations.
> </details>



![](https://arxiv.org/html/2501.05453/extracted/6091816/figs/plot2_extra.png)

> 🔼 그림 13은 ImageNet 검증 세트의 10,000개 이미지에 대해 3-gram 분포를 계산한 결과를 보여줍니다. 세 가지 토큰 생성기(dVAE, VQGAN-1k, VQGAN-16k) 모두 3-gram 토큰에 대해 거의 비슷한 평평한 분포를 보입니다. 이는 3-gram 수준에서는 토큰 생성기의 차이가 크지 않음을 시사합니다.  dVAE 토큰 생성기는 2-gram 수준에서는 더 다양한 조합을 보였으나, 3-gram 수준에서는 VQGAN 토큰 생성기와 유사한 분포를 보입니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: 3-gram Distribution of Various Tokens: We compute the 3-gram distribution on 10000 images from the ImageNet validation set. All the tokenizers has similar almost flat distribution when it comes to 3-gram tokens.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Datasets | Instances | Tokens | Hours |
|---|---|---|---|
| ImageNet | 13.9M | 3.6B | - |
| Kinetics-600 | 0.53M | 41.3B | 1496 |
| Ego4D | 52.1K | 103B | 3750 |
| HowTo100m | 1.172M | 2560B | 92627 |{{< /table-caption >}}
> 🔼 이 표는 논문의 데이터셋 구성에 대한 정보를 보여줍니다.  ImageNet, Kinetics600, Ego4D, HowTo100M 등 다양한 이미지 및 비디오 데이터셋을 사용했으며, 이들의 비율을 다르게 조정하여 모델을 사전 훈련시켰습니다.  전체 훈련 데이터는 약 10만 시간 분량의 비디오를 포함합니다. 각 데이터셋의 인스턴스 수, 토큰 수, 비디오 시간(시간)이 표에 자세히 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Pre-training Dataset: We use both image datasets (Imagenet (Russakovsky et al., 2015)) and video datasets (Kinetics600 (Carreira et al., 2019), Ego4D (Grauman et al., 2022), HowTo100m (Miech et al., 2019)) with different mixing ratios during the pre-training of our models. The whole training data contains about 100,000 hours of videos.
> </details>

{{< table-caption >}}
| Input-Target | Tokens | Vocabulary | Top1 |
|---|---|---|---| 
| VQGAN-VQGAN | 16x16 | 16k | 61.3 |
| VQGAN-VQGAN | 16x16 | 1k | 61.1 |
| dVAE-dVAE | 32x32 | 8k | 61.2 |
| dVAE-dVAE | 16x16 | 8k | 53.2 |
| patch-patch | 16x16 | - | 60.6 |
| patch-dVAE | 16x16 | 8k | 58.5 |{{< /table-caption >}}
> 🔼 이 표는 다양한 토크나이저(dVAE, VQGAN, 패치 임베딩)를 사용하여 모델을 사전 훈련시킨 후 ImageNet 데이터셋에서 선형 탐색(linear probing)을 통해 얻은 결과를 보여줍니다.  구체적으로, dVAE와 VQGAN 토크나이저는 불연속적인 시각적 토큰을 생성하는 반면, 패치 임베딩은 연속적인 토큰을 사용합니다.  표에는 각 토크나이저를 입력과 출력으로 사용했을 때, 모델의 9번째 레이어에서 선형 탐색을 수행하여 얻은 ImageNet 분류 정확도(top-1 정확도)가 나타나 있습니다. 이를 통해 다양한 토크나이저의 성능을 비교하고, 모델의 사전 훈련에 대한 최적의 토크나이저 선택을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: ImageNet Linear Probing Accuracy with Various Tokenizers: We compare discrete (dVAE, VQGAN) and patch embedding as input and target for pre-training our models. ImageNet top-1 accuracies are computed by linear probing at the 9th layer of the large model.
> </details>

{{< table-caption >}}
| Method | Compute | Top1 |
|---|---|---|
dVAE/16 | 1.42e+17 | 53.2 |
dVAE/32 | 5.68e+17 | 61.2 |
dVAE/16→32 | 2.13e+17 | 63.2 |
dVAE/16→32† | 2.13e+17 | 64.4 |{{< /table-caption >}}
> 🔼 표 6은 ImageNet 선형 프로빙 작업에서 다양한 시퀀스 모델링 아키텍처(LLaMA, GPT2, Mamba)를 비교 분석한 결과를 보여줍니다.  각 모델의 매개변수 수와 ImageNet 선형 프로빙 작업에서 달성한 상위 1위 정확도를 비교하여,  다양한 아키텍처의 성능 차이를 보여줍니다.  이는 서로 다른 아키텍처가 시각적 표현 학습에 미치는 영향을 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Architecture: We compare sequence modeling architectures LLaMA Touvron et al. (2023), GPT2 Radford et al. (2019), and non-transformer models, Mamba Gu & Dao (2023) on ImageNet linear probing task.
> </details>

{{< table-caption >}}
| Method | Tokens | Pooling | Top1 |
|---|---|---|---| 
| dVAE | 16x16 | Average | 53.2 |
| dVAE | 16x16 | Attention | 61.1 |{{< /table-caption >}}
> 🔼 표 7은 ImageNet (Deng et al., 2009) 이미지 분류 작업에서 다양한 차별적 및 생성적 모델의 성능을 비교한 결과를 보여줍니다.  자세히 살펴보면, 본 논문의 모델들이 생성적 모델들 중에서는 비슷한 성능을 보이지만, 특히 자기회귀적 모델링 측면에서 가장 높은 정확도를 달성했음을 알 수 있습니다.  † 표시는 선형 탐색(linear probing) 방식으로 평가된 모델임을 나타냅니다.  즉, 기존에 학습된 모델의 특징 추출 부분만을 사용하여 새로운 분류 작업에 적용한 결과를 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 7: ImageNet Results: We compare discriminative and generative models on ImageNet (Deng et al., 2009) recognition task. While achieving comparable performance among generative models, our models model achieves the highest accuracy on autoregressive modeling. †models are evaluated with linear probing.
> </details>

{{< table-caption >}}
| Model | Params | Top1 |
|---|---|---|
| GPT2 [Radford et al. (2019)] | 280 m | 48.5 |
| Mamba [Gu & Dao (2023)] | 290 m | 40.7 |
| LLaMA [Touvron et al. (2023)] | 280 m | 53.2 |{{< /table-caption >}}
> 🔼 표 8은 Kinetics-400 (Kay et al., 2017) 동작 인식 작업에서 차별적 모델과 생성적 모델을 비교한 결과를 보여줍니다. 생성적 모델들 간의 성능이 비슷한 수준임에도 불구하고, 본 연구의 모델들은 오토리그레시브 사전 학습을 통해 Kinetics-400에서 경쟁력 있는 성능을 보여준 최초의 모델이며, 모델 크기가 커짐에 따라 성능이 향상되는 경향을 보입니다.
> <details>
> <summary>read the caption</summary>
> Table 8: K400 Results: We compare discriminative and generative models on Kinetics-400 (Kay et al., 2017) action recognition task. While achieving comparable performance among generative models, our models are the first to show the competitive performance on K400 with autoregressive pre-training, and shows scaling with large model sizes.
> </details>

{{< table-caption >}}
| Method | Arch | #θ | Top1 |
|---|---|---|---| 
| *Discriminative Approaches* |  |  |  |
| SimCLR (Chen et al., 2020b)† | RN50x2 | 94 | 74.2 |
| BYOL (Grill et al., 2020)† | RN50x2 | 94 | 77.4 |
| SwAV (Caron et al., 2020)† | RN50x2 | 94 | 73.5 |
| DINO (Caron et al., 2021) | ViT-B/8 | 86 | 80.1 |
| DINOv2 (Oquab et al., 2023) | ViT-g/14 | 1011 | 86.4 |
| *Generative Approaches* |  |  |  |
| BEiT-L (Bao et al., 2021) | ViT-L/14 | 307 | 62.2 |
| AIM (El-Nouby et al., 2024) | ViT-1B/14 | 1200 | 80.6 |
| MAE (He et al., 2022) | ViT-H/14 | 632 | 80.9 |
| iGPT-L (Chen et al., 2020a)† | GPT-2 | 1386 | 65.2 |
| iGPT-XL (Chen et al., 2020a)† | GPT-2 | 6801 | 72.0 |
| *Toto*-base | LLaMA | 120 | 64.7 |
| *Toto*-large | LLaMA | 280 | 71.1 |
| *Toto*-1b | LLaMA | 1100 | 75.3 |{{< /table-caption >}}
> 🔼 표 9는 Ego4D 데이터셋을 사용한 단기 행동 예측 작업에서 제안된 모델의 성능을 보여줍니다. 제안된 모델은 기존 연구들(FRCNN+Rnd, FRCNN+SF, Hiera, StillFast, VideoMAE, MAE-ST)과 비교하여 평균 정밀도 측면에서 비슷한 성능을 달성했습니다.  표에는 각 모델의 Noun, N+V, N+TTC, 그리고 전체 평균 정밀도 점수가 포함되어 있습니다. 이 표는 제안된 모델이 다양한 척도에서 경쟁력 있는 성능을 보여줌을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Ego4D Results: Our model achieves comparable mean-average precision compared to previous work. We compare our method with, FRCNN+Rnd (Grauman et al., 2022), FRCNN+SF (Grauman et al., 2022), Hiera (Ryali et al., 2023), StillFast (Ragusa et al., 2023), VideoMAE (Wang et al., 2023a), and MAE-ST (Feichtenhofer et al., 2022).
> </details>

{{< table-caption >}}
| Method | Arch | Top1 |
|---|---|---|
| *Discriminative Approaches* |  |  |
| I-JEPA (Assran et al., 2023) | ViT-H/16 | 74.5 |
| OpenCLIP (Cherti et al., 2023) | ViT-G/14 | 83.3 |
| DINOv2 (Oquab et al., 2023) | ViT-g/14 | 84.4 |
| InternVideo (Wang et al., 2022) | - | 73.7 |
| *Generative Approaches* |  |  |
| Hiera (Ryali et al., 2023) | Hiera-H/14 | 77.0 |
| MVD (Wang et al., 2023b) | ViT-H/14 | 79.4 |
| VideoMAE (Wang et al., 2023a) | ViT-L/14 | 79.8 |
| *Toto*-base | LLaMA | 59.3 |
| *Toto*-large | LLaMA | 65.3 |
| *Toto*-1b | LLaMA | 74.4 |{{< /table-caption >}}
> 🔼 표 10은 DAVIS(Densely Annotated Video Segmentation) 데이터셋을 사용한 비디오 객체 추적 결과를 보여줍니다.  각 모델의 성능을 나타내는 지표로 J, F, J&F 점수를 사용했습니다.  J는 객체의 위치 정확도, F는 객체의 분할 정확도, J&F는 두 지표의 조화 평균을 나타냅니다.  표는 각 모델에서 성능이 가장 좋은 레이어의 점수를 보여줍니다.  결과에 따르면, 본 논문에서 제시된 Toto 모델은 DINO와 유사한 성능을 보였으며, 특히 고해상도(512)에서는 다른 모든 방법들을 능가하는 성능을 보였습니다.  즉, Toto 모델이 비디오 객체 추적 작업에서 우수한 성능을 보임을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 10: DAVIS Tracking: We report J, F, and J&F scores at the peak layers of each model. We achieves comparable performance as DINO and at large resolution (512), it outperforms all methods.
> </details>

{{< table-caption >}}
| Method | Noun | N+V | N+TTC | Overall |
|---|---|---|---|---|
| FRCNN+Rnd (Grauman et al., 2022) | 17.55 | 1.56 | 3.21 | 0.34 |
| FRCNN+SF (Grauman et al., 2022) | 17.55 | 5.19 | 5.37 | 2.07 |
| Hiera-large (Ryali et al., 2023) | 14.05 | 6.03 | 4.53 | 2.12 |
| StillFast (Ragusa et al., 2023) | 16.20 | 7.47 | 4.94 | 2.48 |
| VideoMAE-large (Wang et al., 2023a) | 15.16 | 6.72 | 5.26 | 2.55 |
| MAE-ST-large (Feichtenhofer et al., 2022) | 13.71 | 6.63 | 4.94 | 2.60 |
| *Toto*-large | 15.20 | 6.75 | 5.41 | 2.70 |{{< /table-caption >}}
> 🔼 표 11은 실제 환경에서의 로봇 조작 실험 결과를 보여줍니다.  특히 Franka 로봇을 이용한 큐브 집기 작업에서 MVP(Radosavovic et al., 2022) 와 Toto 모델의 성능을 비교 분석합니다. 두 모델 모두 사전 훈련된 특징을 사용하며, 동일한 데모 데이터를 사용하여 행동 복제 방식으로 학습된 모듈에 이러한 특징을 전달합니다.  실험 결과, Toto 모델이 로봇 애플리케이션을 위해 특별히 설계되지 않았음에도 불구하고 최첨단 로봇 비전 백본과 비슷한 성능을 보여줍니다.  즉, 본 연구에서 제안하는 방법이 로봇 조작 작업에 효과적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 11: Robotics, Real-world Experiments: We compare MVP (Radosavovic et al., 2022) and Toto on a Franka cube-picking task in the real world. Features from both models are pre-trained, frozen, and passed into a learning module trained with behavior cloning using the same demonstrations. We see that our approach performs comparably to the state-of-the-art vision backbone for robotics, despite not being designed with the robotic application in mind.
> </details>

{{< table-caption >}}
| Method (Res/Patch) | J&F | J | F |
|---|---|---|---| 
| DINO-base (224/8) | 54.3 | 52.5 | 56.1 |
| DINO-base (224/16) | 33.1 | 36.2 | 30.1 |
| MAE-base (224/16) | 31.5 | 34.1 | 28.9 |
| *Toto*-base (256/8) | 42.0 | 41.2 | 43.1 |
| *Toto*-large (256/8) | 44.8 | 44.4 | 45.1 |
| *Toto*-1b (256/8) | 46.1 | 45.8 | 46.4 |
| *Toto*-large (512/8) | 62.4 | 59.2 | 65.6 |{{< /table-caption >}}
> 🔼 본 표는 CATER 데이터셋(Girdhar & Ramanan, 2019)을 사용하여 객체의 영속성(Object Permanence) 성능을 평가한 결과를 보여줍니다.  CATER 데이터셋은 물체가 다른 물체에 의해 가려지거나 숨겨진 상황에서 객체의 위치를 예측하는 과제를 포함합니다.  표에는 다양한 방법(V3D, TFC-V3D, Toto-large)을 사용한 실험 결과가 나와 있으며, 특히 Toto-large 모델이 16프레임과 32프레임 모두에서 기존 방법들보다 더 나은 성능을 보임을 확인할 수 있습니다.  이는 Toto 모델이 객체의 위치를 예측하는 데 있어서 우수한 성능을 가지고 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 12: Object Permanence: CATER (Girdhar & Ramanan, 2019) object localization task, where the object is hidden under or obstructed by other objects. The model is trained to predict its coarse location. Our model performs better than previous methods on snitch localization task at 16, 32 temporal resolutions.
> </details>

{{< table-caption >}}
| Model | # Traj | Success |
|---|---|---|
| MVP | 240 | 75% |
| Toto-base | 240 | 63% |{{< /table-caption >}}
> 🔼 표 13은 ImageNet-1K 데이터셋에서 다양한 방법들의 성능을 비교한 결과를 보여줍니다.  '전체 미세 조정 성능' 이라는 제목처럼, 사전 훈련된 모델을 ImageNet-1K 데이터셋에 대해 미세 조정했을 때의 성능을 보여줍니다.  DINO, MoCo v3, BEIT, MAE와 같은 다른 방법들과 Toto 모델의 성능을 비교하여,  Toto 모델의 성능이 다른 방법들과 비슷하거나 그 이상임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 13: Full Fine Tuning Performance: Comparison of different methods performance on ImageNet-1K.
> </details>

{{< table-caption >}}
| Method | Model | 16 | 32 |
|---|---|---|---| 
| V3D | ResNet | 55.2 | 69.7 |
| TFC V3D | ResNet | 54.6 | 70.2 |
| *Toto*-large | LLaMa | 62.8 | 72.9 |{{< /table-caption >}}
> 🔼 본 표는 ImageNet 데이터셋을 사용하여 선형 프로빙 방식으로 평가한 Toto 모델과 유사한 크기의 iGPT 모델의 성능을 비교한 결과를 보여줍니다.  Toto 모델이 iGPT 모델보다 더 높은 정확도를 달성했음을 보여주는 표입니다.  구체적으로는, 비슷한 크기의 모델(약 10억 개의 파라미터)에서 Toto 모델이 iGPT 모델보다 ImageNet 분류 정확도가 더 높았다는 것을 보여줍니다. 이는 Toto 모델의 설계 변경이 iGPT 모델에 비해 성능 향상에 기여했음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 14: ImageNet Linear Probing Results: Toto performs better than similar size iGPT models.
> </details>

{{< table-caption >}}
| DINO | MoCo v3 | BEiT | MAE | Toto |
|---|---|---|---|---|
| 82.8 | 83.2 | 83.2 | 83.6 | 82.6 |{{< /table-caption >}}
> 🔼 표 16은 Kinetics-400 데이터셋에서 다양한 모델의 동작 인식 성능을 보여줍니다.  이 표는 크로스 어텐션과 다층 퍼셉트론(MLP) 레이어를 분류 헤드로 사용하여 모델을 평가한 결과를 나타냅니다.  표에서 알 수 있듯이, 고용량 헤드를 사용하면 모든 모델의 성능이 향상됩니다.  즉, 더 복잡한 분류 헤드를 사용하면 모델이 동작을 더 정확하게 인식할 수 있음을 보여줍니다. 이는 특히 대규모 모델에서 더욱 두드러지게 나타납니다.
> <details>
> <summary>read the caption</summary>
> Table 16: K400 Results: We evaluate our models using cross attention and MLP layer as the classification head. Overall using a high-capacity head improves the performance across all models.
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