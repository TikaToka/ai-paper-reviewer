---
title: "Intuitive physics understanding emerges from self-supervised pretraining on natural videos"
summary: "자연 영상 데이터를 이용한 자기 지도 학습을 통해 인공지능 모델이 직관적 물리적 이해 능력을 얻을 수 있다는 것을 보여주는 획기적인 연구!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Video Understanding", "🏢 Meta AI",]
showSummary: true
date: 2025-02-17
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.11831 {{< /keyword >}}
{{< keyword icon="writer" >}} Quentin Garrido et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-18 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.11831" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.11831" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/intuitive-physics-understanding-emerges-from" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

인간은 물체의 움직임과 상호작용에 대한 직관적인 물리적 이해를 가지고 있습니다. 하지만 기존 인공지능 모델들은 이러한 직관적인 물리적 이해를 제대로 구현하지 못했습니다. 이는 **인공지능 모델이 세계를 이해하는 데 필요한 핵심적인 지식(core knowledge)이 선천적으로 내장되어야 한다는 믿음** 때문이었습니다.



본 연구는 **자연 영상 데이터를 이용한 자기 지도 학습 기반의 영상 예측 모델을 통해 이 문제를 해결**하고자 하였습니다. 연구진은 모델이 **학습된 표상 공간에서 마스크된 영역을 예측**하도록 훈련시켰으며, 그 결과 모델은 물체의 영속성, 형태 일관성 등 다양한 물리적 특성에 대한 이해를 보여주었습니다. **특히, 1주일치의 영상 데이터만으로도 기존 모델보다 우수한 성능을 보임**으로써, **선천적 지식 없이도 물리적 직관을 학습할 수 있다는 가능성**을 제시하였습니다. 이는 인공지능 모델의 물리적 직관 학습에 대한 새로운 패러다임을 제시하는 중요한 발견입니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 자기 지도 학습 기반의 영상 예측 모델이 물리적 직관을 학습할 수 있다는 것을 입증 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 물리적 직관 학습에 선천적 지식이 필요 없다는 기존 이론에 대한 도전 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 학습된 표상 공간에서의 예측이 물리적 직관 학습에 중요한 역할을 한다는 것을 발견 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**본 논문은 인간의 직관적 물리적 이해 능력을 컴퓨터가 학습할 수 있는 새로운 방법을 제시하여 인공지능 분야의 혁신적인 발전을 가져올 수 있습니다.**  **영상 예측 모델의 자기 지도 학습을 통해 물리적 직관을 얻는다는 새로운 패러다임을 제시**, **기존의 핵심 지식 이론에 대한 도전장을 내밀며**  **향후 연구 방향을 제시**, **다양한 분야의 연구자들에게 영감을 주고 새로운 연구를 촉진할 수 있습니다.**

------
#### Visual Insights



![](https://arxiv.org/html/2502.11831/x1.png)

> 🔼 그림 1은 일반적인 물리적 직관을 이해하는 V-JEPA(Video Joint Embedding Predictive Architecture) 모델의 성능을 보여줍니다. (A)는 기존의 세 가지 물리적 직관 데이터셋(IntPhys, GRASP, InfLevel)을 사용하여 예상 위반 패러다임으로 비디오 모델을 평가한 결과입니다. V-JEPA는 비현실적인 비디오에 대해 훨씬 더 놀라는(surprise) 반응을 보였습니다. 반면에, V-JEPA의 무작위 초기화 모델(훈련되지 않은 네트워크)은 우연 수준의 성능을 보였고, 텍스트 또는 픽셀 예측 기반의 최첨단 비디오 모델은 우연 수준에 가까운 성능을 보였습니다. (B)는 V-JEPA가 학습된 표상 공간에서 자연 비디오의 손상된 부분을 복원하도록 훈련되는 과정을 보여줍니다. 비디오와 손상된 버전으로부터 표상을 추출한 후, 손상된 표상으로부터 원본 비디오의 표상을 예측하는 것을 목표로 합니다. (C)는 훈련된 V-JEPA를 사용하여 과거 M개의 프레임을 기반으로 미래 N개의 프레임 표상을 예측하고, 관찰된 이벤트의 표상과 비교하여 놀라움 지표를 계산하는 방법을 보여줍니다. 놀라움 지표는 두 비디오 중 어느 것이 물리적 위반을 포함하는지 판단하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Video prediction in representation space (V-JEPA) achieves an understanding of intuitive physics. (A) Video models are evaluated on three intuitive physics datasets using the Violation of Expectation paradigm (IntPhys, GRASP, and InfLevel). V-JEPA is significantly more ‘surprised’ by implausible videos. Random initializations of V-JEPA (untrained networks) show near-chance performance, and state-of-the-art video models based on text or pixel prediction are much closer to chance. Confidence intervals at 95% are obtained via bootstrapping, except for untrained networks (n=20𝑛20n=20italic_n = 20) which use a normal distribution assumption. (B) V-JEPA is trained to ’inpaint’ natural videos in a learned representation space. Starting from a video and a corrupted version, representations are first extracted. The goal is then to predict the representation of the original video from the representation of the corrupted ones. (C) From a trained V-JEPA, we compute a surprise metric by predicting representations of N future frames based on M past ones and comparing the predictions to the representations of observed events. The surprise metric is then used to decide which of the two videos contains a physical violation.
> </details>





{{< table-caption >}}
| Hyper-parameter | ViT-B/16 | ViT-L/16 | ViT-H/16 |
|---|---|---|---|
| _positional embeddings_ |  |  |  |
| Type | RoPE | RoPE | RoPE |
| theta | 10000 | 10000 | 10000 |
| _data_ |  |  |  |
| resolution | 224 | 224 | 224 |
| num_frames | 16 | 16 | 16 |
| framerate | 5.33 fps | 5.33 fps | 5.33 fps |
| horizontal_flip | true | true | true |
| random_resize_scale | (0.3, 1.0) | (0.3, 1.0) | (0.3, 1.0) |
| random_resize_aspect_ratio | (0.75, 1.35) | (0.75, 1.35) | (0.75, 1.35) |
| _masking_ |  |  |  |
| block_aspect_ratio | (0.75, 1.5) | (0.75, 1.5) | (0.75,1.5) |
| shortrange_mask_num_blocks | 8 | 8 | 8 |
| shortrange_mask_spatial_scale | 0.15 | 0.15 | 0.15 |
| longrange_mask_num_blocks | 2 | 2 | 2 |
| longrange_mask_spatial_scale | 0.7 | 0.7 | 0.7 |
| _optimization_ |  |  |  |
| optimizer | AdamW | AdamW | AdamW |
| batch_size | 3072 | 3072 | 3072 |
| total_number_of_iterations | 90000 | 90000 | 90000 |
| scheduler | Linear + Cosine | Linear + Cosine | Linear + Cosine |
| warmup_iterations | 12000 | 12000 | 12000 |
| learning_rate | 6.25e-04 | 6.25e-04 | 6.25e-04 |
| start_lr | 2e-04 | 2e-04 | 2e-04 |
| final_lr | 1e-06 | 1e-06 | 1e-06 |
| start_momentum | 0.998 | 0.998 | 0.998 |
| final_momentum | 1.0 | 1.0 | 1.0 |
| start_weight_decay | 0.04 | 0.04 | 0.04 |
| final_weight_decay | 0.4 | 0.4 | 0.4 |
| scheduler_scale_factor | 1.25 | 1.25 | 1.25 |
| _architecture_ |  |  |  |
| patch_size | 16 | 16 | 16 |
| tubelet_size | 2 | 2 | 2 |
| pred_depth | 12 | 12 | 12 |
| pred_embed_dim | 384 | 384 | 384 |
| _hardware_ |  |  |  |
| dtype | bfloat16 | bfloat16 | bfloat16 |
| accelerator | A100 80G | A100 80G | A100 80G |{{< /table-caption >}}

> 🔼 표 S1은 V-JEPA 사전 훈련에 사용된 하이퍼파라미터들을 보여줍니다. 원 논문 (Bardes et al., 2024)의 표와 구조와 값이 동일하며, 위치 인코딩에 RoPE (Su et al., 2021)을 사용한 점만 다릅니다. 이 표는 V-JEPA 모델의 사전 훈련 과정에서 사용된 다양한 설정 값들을 상세히 보여주어, 모델 성능에 미치는 각 하이퍼파라미터의 영향을 분석하는 데 도움을 줍니다.  모델 아키텍처, 최적화 설정, 마스킹 전략 등의 세부 정보를 포함하여 V-JEPA의 사전 훈련 과정을 이해하는 데 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table S1: Pretraining hyper-parameters for V-JEPA. Table structure and values identical to the original V-JEPA paper (Bardes et al., 2024), apart from positional embedding where we rely on RoPE (Su et al., 2021).
> </details>





### In-depth insights


#### Intuitive Physics AI
**직관적 물리학 AI**는 인간처럼 물리적 세계를 이해하고 예측하는 인공지능 시스템을 구축하는 데 중점을 둡니다. 이는 단순히 물리 법칙을 프로그래밍하는 것을 넘어 **데이터 기반 학습을 통해 물리적 직관을 습득**하는 것을 의미합니다. 이를 위해 자연 영상이나 시뮬레이션 데이터를 활용하여 물체의 움직임, 상호작용, 변화 등을 학습하며, **예측 불가능한 상황에 대한 놀라움(surprise)**을 측정하여 이해도를 평가합니다.  **제한된 데이터로도 놀라운 성과**를 보이는 모델들이 등장하고 있으며, **추상적인 표현 공간에서의 예측**이 **픽셀 기반 예측보다 우수**한 성능을 보이는 것으로 나타났습니다.  그러나 아직까지 **복잡한 상호작용이나 비정상적인 상황에 대한 이해는 부족**하고, **물리적 직관을 어떻게 효율적으로 학습시킬지**에 대한 연구가 더 필요합니다.  **심층 신경망을 통해 추상적 표현 능력을 획득**함으로써 직관적 물리학 AI가 발전하고 있지만, 아직 **인간 수준의 이해력에는 미치지 못**하고 있습니다.  향후 연구는 **더욱 다양하고 풍부한 데이터**, **더욱 발전된 모델 아키텍처**, **인간의 인지 과정에 대한 깊이 있는 이해**를 바탕으로 진행되어야 할 것입니다.

#### V-JEPA Architecture
V-JEPA(Video Joint Embedding Predictive Architecture)는 비디오 프레임의 마스크된 영역을 예측하기 위해 자가지도학습 방식을 사용하는 아키텍처입니다. **핵심은 비디오 프레임을 저수준 픽셀 공간이 아닌 고차원 추상적 표현 공간에서 처리한다는 점**입니다. 이를 통해 모델은 **물리적 법칙 위반에 대한 이해**를 보다 효율적으로 학습할 수 있습니다.  **예측적 코딩(predictive coding)** 개념을 기반으로 설계되어, 모델은 미래의 프레임을 예측하고 실제 관측된 프레임과 비교함으로써 예측 오차를 최소화합니다. 이러한 오차는 직관적 물리에 대한 이해 수준을 측정하는 지표로 사용됩니다. V-JEPA의 주요 강점은 **손으로 설계된 추상적 표현이 아닌 데이터로부터 자동으로 학습된 표현 공간을 사용**한다는 점입니다. 이는 다양한 물리적 현상을 포괄적으로 학습할 수 있는 유연성을 제공합니다. 또한, **상대적으로 적은 양의 데이터**로도 우수한 성능을 달성할 수 있다는 점도 주목할 만합니다.  결론적으로 V-JEPA 아키텍처는 직관적 물리 이해를 위한 효과적이고 확장성 있는 접근 방식을 제시합니다.

#### Violation of Expectation
기대 위반(Violation of Expectation) 패러다임은 **유아의 물리적 직관 발달 연구**에서 출발하여 인공지능 모델의 물리적 직관 이해도를 평가하는 데 활용됩니다.  영아에게 물리적으로 불가능한 상황을 보여주고 그 반응을 관찰하여 물리적 직관의 존재와 발달 단계를 추론하는 방식입니다.  인공지능 분야에서는 이 패러다임을 활용하여 **모델이 물리적으로 불가능한 상황에 대한 예상치 못한 반응**을 보이는지 측정함으로써 물리적 직관을 평가합니다.  **예측 오류 측정**을 통해 물리적 법칙 위반에 대한 모델의 '놀라움' 수준을 정량적으로 평가하며, 이는 모델의 물리적 직관 이해도를 나타내는 중요한 지표입니다.  본 논문에서 이 기법을 통해  **비디오 예측 모델의 물리적 직관 이해도**를 성공적으로 평가하였으며, 특히 학습된 표상 공간에서의 예측이 픽셀 공간 예측이나 언어 모델보다 훨씬 우수한 성능을 보임을 확인했습니다.  즉, **직관적 물리학 이해는 선천적 지식이 아닌 학습을 통해 얻을 수 있다는 것을 시사**합니다.

#### Ablation Study
본 논문의 ‘절제 연구(Ablation Study)’ 부분은 **모델의 설계 선택이 직관적 물리적 이해에 미치는 영향을 체계적으로 분석**하기 위해 고안되었습니다.  **다양한 요소 (예: 훈련 데이터, 예측 목표, 모델 크기)**를 제거하거나 변경하여 모델 성능 변화를 관찰함으로써, 각 요소의 중요성과 상호작용을 파악할 수 있습니다. 이를 통해, **단순한 예측 성능 향상을 넘어, 직관적 물리적 이해 능력 발달에 실질적으로 기여하는 핵심 요소**를 도출하는 것을 목표로 합니다.  특히, 학습된 표상 공간에서의 비디오 예측이 **선천적 지식이 아닌 학습을 통해 물리적 직관을 획득할 수 있음**을 시사하는 중요한 결과를 제시할 것으로 예상됩니다.  **절제 연구의 결과는 모델 설계의 최적화뿐 아니라, 인공지능 시스템의 물리적 직관 발달에 대한 이론적 이해를 심화**시키는 데 기여할 것입니다.  결과적으로,  본 연구는 **인공지능 시스템의 물리적 이해 능력 향상을 위한 새로운 방향과 통찰력을 제공**할 것으로 기대됩니다.

#### Future Directions
본 논문은 자가 지도 학습을 통해 일반적인 심층 신경망 모델에서 직관적인 물리적 이해가 어떻게 나타나는지에 대한 연구입니다.  **비디오 예측 모델이 학습된 표상 공간에서 다양한 직관적 물리 특성을 이해한다는 것을 보여줍니다.**  미래 연구 방향으로는 **더욱 복잡한 물리적 상호 작용을 이해하기 위한 모델의 메모리 및 표상 능력 향상**, **실제 영유아의 시각적 경험과 유사한 데이터셋을 활용한 학습**, 그리고 **에이전트가 환경과 상호 작용하며 학습하는 방식**에 대한 연구가 제시될 수 있습니다.  특히, **다양한 유형의 물리적 현상에 대한 이해도를 높이기 위해 모델의 아키텍처 및 훈련 방식을 개선하는 연구**가 중요하며,  **모델의 추론 과정을 더욱 투명하게 만드는 연구**를 통해 직관적 물리 이해의 메커니즘을 밝히는 데 기여할 수 있을 것입니다.  **인간의 직관적 물리적 이해와 AI 모델의 이해도를 비교 분석하는 연구**도 필요하며, 이를 통해 인간의 인지 과정에 대한 이해를 높일 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.11831/x2.png)

> 🔼 그림 2는 다양한 물리적 속성과 벤치마크에 걸쳐 무작위로 초기화된 모델과 사람에 비해 V-JEPA의 정확도 향상을 보여줍니다. (A) 일부 벤치마크에는 저수준의 편향이 있으므로 모델 성능을 20개의 무작위로 초기화된 네트워크와 비교하여 테스트합니다. V-JEPA 모델(5개)은 대부분의 개념에 대해 직관적인 물리학 벤치마크에서 더 높은 상대적 분류 정확도를 보입니다. (B) IntPhys 테스트 세트에서 다양한 조건에 걸쳐 사람의 단순한 성능과 비교한 V-JEPA의 상대적(왼쪽) 및 절대적(오른쪽) 정확도를 보여주며, 사람과 기계 오류 간의 높은 상관관계를 보여줍니다. V-JEPA 점수는 각 비디오의 최대 놀라움을 사용하며, 단일 비디오 분류에 더 적합합니다. 인간 데이터는 (Riochet et al., 2022)에서 가져왔습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: V-JEPA accuracy increase relative to randomly-initialized models and humans across different physical properties and benchmarks. (A) Because some benchmarks contain low-level biases, we test the model performance against a set of randomly initialized networks (n=20𝑛20n=20italic_n = 20). V-JEPA models (n=5𝑛5n=5italic_n = 5) have higher relative classification accuracy on intuitive physics benchmarks for most, but not all concepts. (B) V-JEPA relative (left) and absolute (right) accuracy on the IntPhys test set across different conditions compared to naive human performance, showing a high correlation between human and machine errors. The V-JEPA score uses the maximum surprise from each video, which generalizes better for single-video classification. Human data are taken from (Riochet et al., 2022).
> </details>



![](https://arxiv.org/html/2502.11831/x3.png)

> 🔼 그림 3은 V-JEPA 모델의 IntPhys 점수에 대한 마스크 유형, 훈련 데이터 유형 및 양, 모델 크기의 영향을 보여줍니다. (A) VM2M으로 사전 훈련된 경우, V-JEPA는 모든 마스킹 전략에서 직관적인 물리학에 대한 이해를 보여줍니다. (B) 세 가지 훈련 데이터셋 중 두 가지(K710 및 HowTo100M)는 개별적으로 훈련되었을 때 높은 정확도를 제공합니다. HowTo100M의 1289시간만으로도 높은 점수를 얻었으며, 128시간만으로도 우연보다 나은 성능을 보였습니다. (C) 더 큰 인코더는 성능을 향상시키지만, HowTo100M으로 사전 훈련했을 때 크기에 관계없이 성능이 의미 있는 수준을 유지합니다. 신뢰 구간은 부트스트래핑을 통해 얻었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Influence of type of mask, type and amount of training data, and model size on V-JEPA IntPhys scores. (A) When pretrained on VM2M, V-JEPA exhibits an understanding of intuitive physics with every masking strategy. (B) Of the three training datasets, two give high accuracies when trained separately (K710 and Howto100M). High scores are found with only 1289 hours of Howto100M (the largest dataset), and even 128h gives better than chance performance. (C) While larger encoders improve performance, we find that the performance remains non-trivial across sizes when pretraining on HowTo100M. Confidence intervals obtained via bootstrapping.
> </details>



![](https://arxiv.org/html/2502.11831/x6.png)

> 🔼 그림 S1은 서로 다른 놀라움 측정 방식이 서로 다른 작업에 더 적합하다는 것을 보여줍니다. IntPhys에 중점을 두면 비디오의 평균 놀라움을 보는 것이 비디오 쌍을 비교할 때 성능이 더 우수하다는 것을 알 수 있습니다. 일표본 t-검정을 수행하여 상대적인 놀라움이 0보다 큰지 확인했습니다(왼쪽). 그러나 개별 비디오의 놀라움을 살펴볼 때 비디오의 최대 놀라움을 선택하면 가능한 비디오와 불가능한 비디오를 더 잘 구분할 수 있습니다. 불가능한 비디오의 놀라움이 가능한 비디오보다 더 높은지 확인하기 위해 이표본 t-검정을 수행했습니다(오른쪽).
> <details>
> <summary>read the caption</summary>
> Figure S1: Different surprise measures are better suited for different tasks. Focusing on IntPhys, we find that looking at the average surprise over a video leads to better performance when comparing pairs of videos. A one-sample t-test was performed to see if the relative surprises are greater than zero (left). However, when looking at individual videos’ surprise, choosing the maximum surprise over a video leads to a better separation between possible and impossible videos. A two-sample t-test was performed to see if impossible videos have higher surprise than possible ones. (rigt).
> </details>



![](https://arxiv.org/html/2502.11831/x7.png)

> 🔼 그림 S2는 Qwen2-VL-72B 모델이 한 쌍의 비디오를 제시받았을 때, 가능한 비디오와 불가능한 비디오에 대해 유사한 확률을 출력하는 것을 보여줍니다.  이 그림은 모델이 가능/불가능 여부를 구분하는 데 어려움을 겪는다는 것을 시각적으로 보여주는 히스토그램을 포함하고 있으며,  각 비디오 유형의 확률 분포를 비교하여 모델의 성능을 평가하는 데 사용됩니다.  세 개의 다른 벤치마크 데이터셋(IntPhys, GRASP, InfLevel-lab)에 대한 결과가 각각 표시되어 모델의 일반화 능력을 평가할 수 있도록 합니다.
> <details>
> <summary>read the caption</summary>
> Figure S2: Normalized probabilities output by Qwen2-VL-72B. When presented with a pair of videos, we find that the model outputs similar probabilities for possible and impossible videos.
> </details>



![](https://arxiv.org/html/2502.11831/x10.png)

> 🔼 본 그림은 다양한 속성과 데이터셋에 걸쳐 단일 컨텍스트 크기를 사용할 때 모델의 성능이 저하됨을 보여줍니다. 모델이 처리할 수 있는 비디오 길이에 제한이 있기 때문에 발생하는 현상입니다.  V-JEPA의 경우 이러한 시나리오에서도 성능이 여전히 유의미하게 나타납니다. 즉, 비디오의 일부분만을 사용하여 예측을 수행할 때 모델의 성능이 어떻게 변하는지를 보여주는 그래프입니다. 다양한 데이터셋과 물리적 속성에 대해, 단일 컨텍스트 크기에서의 성능 저하가 관찰되는데, 특히 V-JEPA 모델은 이러한 상황에서도 성능이 크게 떨어지지 않음을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure S3: Models perform suboptimally with a fixed context size. Due to limitations in how long of a video models can process, we find drops in performance when using a single context size across all properties and datasets. Performance remains non-trivial for V-JEPA in this scenario.
> </details>



![](https://arxiv.org/html/2502.11831/x11.png)

> 🔼 그림 S4는 다양한 물리적 속성과 데이터 집합에 대해 예측을 위한 문맥 크기를 변경할 때 성능의 변화를 보여줍니다. 일반적으로 모델은 더 작은 문맥 크기에서 더 나은 성능을 보이지만, 최적의 문맥 크기는 속성과 데이터 집합에 따라 다릅니다. GRASP는 가장 큰 변화를 보이는 반면, IntPhys와 InfLevel-lab는 상대적으로 덜 민감합니다.  즉, 어떤 물리적 현상을 예측하는 데 필요한 과거 정보의 양은 현상의 종류와 데이터 특징에 따라 다르다는 것을 보여줍니다. GRASP 데이터셋의 경우 다른 데이터셋에 비해 최적의 문맥 크기가 더욱 변화무쌍하게 나타나며, 이는 데이터셋 자체의 특성과 관련이 있을 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure S4: Variation of performance when changing context size for predictions. While models tend to perform better with smaller context sizes, we find the optimal context size to be dependent on the property and dataset. GRASP exhibits the most variation whereas IntPhys and InfLevel-lab are less sensitive in general.
> </details>



![](https://arxiv.org/html/2502.11831/x12.png)

> 🔼 그림 S5는 HowTo100M의 하위 집합으로 V-JEPA-L을 사전 훈련하여 동작과 장면의 다양성이 IntPhys 성능에 미치는 영향을 조사한 결과를 보여줍니다. (왼쪽) 비디오를 하위 샘플링하여 장면의 다양성을 줄이면 모델은 여전히 128시간의 고유 비디오로 좋은 성능에 도달할 수 있음을 보여줍니다. (오른쪽) 비디오의 프레임을 하위 샘플링하여 각 장면의 동작 다양성을 줄이면 비디오 하위 샘플링보다 성능이 낮지만 모델은 여전히 프레임의 2%(2579시간)로 좋은 성능을 달성할 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure S5: Influence of motion and scene diversity. By pretraining V-JEPA-L on subsets of HowTo100M, we investigate how the diversity in motion and scenes affects performance on IntPhys.(left) By subsampling videos, we reduce the diversity in scenes, where we find that the model can still reach good performance with 128h of unique videos. (right) By subsampling frames in videos, we reduce the diversity of motions in each scene. Here we find lower performance than when subsampling videos, but the model still achieves good performance with 2% of the frames (2579h).
> </details>



![](https://arxiv.org/html/2502.11831/x13.png)

> 🔼 그림 S6은 InfLevel 데이터셋에서 문맥화 이벤트를 제거하여 V-JEPA와 VideoMAE 모델의 성능 향상을 보여줍니다. 중력과 고체성과 같은 속성은 실험 전에 비디오에 표시된 용기의 속성을 기억해야 합니다. 접두사 비디오가 필요하지 않도록 비디오에 레이블을 다시 지정함으로써, 두 모델 모두 성능이 크게 향상되었습니다. 그러나 이러한 레이블 재지정은 가능한 비디오와 불가능한 비디오의 난이도가 동일하다는 가정을 깨뜨립니다.
> <details>
> <summary>read the caption</summary>
> Figure S6: Relabeling InfLevel to remove contextualization events. Gravity and solidity both require to remember the properties about the containers shown in a video before the actual experiment. By relabeling the videos such that the prefix video is not necessary, we find a significant increase in performance for both V-JEPA and VideoMAE. However, this relabeling breaks the assumption that the possible and impossible videos have the same difficulty.
> </details>



![](https://arxiv.org/html/2502.11831/x14.png)

> 🔼 그림 S7은 V-JEPA-L 모델의 성능을 다양한 물리적 속성에 대해 보여줍니다.  5개의 V-JEPA-L 모델(n=5)이 대부분의 속성에서 훈련되지 않은 네트워크보다 높은 정확도를 달성했습니다. 검은색 점은 각 모델의 5번의 시도에 대한 성능을 나타냅니다. 이 그림은 V-JEPA-L 모델이 다양한 직관적 물리적 속성을 이해하는 데 있어 우수한 성능을 보여준다는 것을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure S7: Complete results for V-JEPA-L. The models (n=5𝑛5n=5italic_n = 5) achieve accuracies higher than untrained networks on most properties. Black dots represent the performance of 5 seeds.
> </details>



![](https://arxiv.org/html/2502.11831/x15.png)

> 🔼 그림 S8은 V-JEPA-H 모델의 성능을 다양한 물리적 속성에 대해 보여줍니다. 이 그림은 V-JEPA-H 모델이 대부분의 속성에서 훈련되지 않은 네트워크보다 더 높은 정확도를 달성했음을 보여줍니다. 회색 점은 20개의 훈련되지 않은 네트워크의 성능을 나타내며, 신뢰 구간은 부트스트래핑을 통해 얻어졌습니다. 이 그림은 모델이 물리적 직관에 대한 이해를 얼마나 잘 학습했는지 보여주는 상세한 결과를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure S8: Complete results for V-JEPA-H. The model achieves accuracies higher than untrained networks on most properties. Gray dots represent the performance of the 20 untrained networks. Confidence intervals obtained via bootstrapping.
> </details>



![](https://arxiv.org/html/2502.11831/x16.png)

> 🔼 그림 S9는 VideoMAEv2 모델의 성능을 다양한 물리적 속성에 대해 보여줍니다.  VideoMAEv2는 훈련되지 않은 네트워크와 비슷하거나 약간 더 나은 성능을 보여주지만, 고체성(Solidity)과 충돌(Collision) 속성에서는 성능이 다소 떨어집니다. 회색 점은 훈련되지 않은 20개 네트워크의 성능을 나타내며, 신뢰 구간은 부트스트래핑을 통해 얻어졌습니다. 이 그림은 다양한 물리적 속성에 대한 VideoMAEv2의 성능을 자세히 보여주는 시각적 자료입니다.
> <details>
> <summary>read the caption</summary>
> Figure S9: Complete results for VideoMAEv2. The model achieves performance on par or slightly higher than untrained networks across properties, apart from solidity and collision. Gray dots represent the performance of the 20 untrained networks. Confidence intervals obtained via bootstrapping.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Dataset | Realistic | Diverse scenes | Size | Number of Properties |
|---|---|---|---|---|
| IntPhys | No | Yes | ~ 360 | 3 |
| GRASP | No | No | ~ 4000 | 10 |
| InfLevel-lab | Yes | No | ~ 4000 | 3 |{{< /table-caption >}}
> 🔼 표 S2는 본 논문에서 사용된 세가지 데이터셋, 즉 IntPhys, GRASP, InfLevel-lab에 대한 요약 정보를 제공합니다. 각 데이터셋은 모델 평가를 위한 질적으로 다른 데이터 소스를 제공하며, 이는 보다 포괄적인 모델 평가를 가능하게 합니다. IntPhys는 정밀하게 제작된 합성 데이터를 사용하여 물리적 직관에 대한 이해를 평가하는 데 중점을 둡니다. GRASP는 다양한 물리적 현상을 포함하는 합성 및 실제 데이터의 조합을 제공합니다. InfLevel-lab은 실제 비디오를 사용하지만 컨텍스트를 제공하는 이전 비디오 클립이 없습니다.  이러한 데이터셋의 다양성은 모델이 다양한 상황에서 물리적 직관을 이해하는 능력을 포괄적으로 평가할 수 있도록 합니다.
> <details>
> <summary>read the caption</summary>
> Table S2: Summary of datasets used for evaluation. IntPhys, GRASP and InfLevel-lab provide qualitatively different data sources to perform a more holistic evaluation of models.
> </details>

{{< table-caption >}}
| Dataset | Method | Frame skip | FPS | Window size | Window Stride |
|---|---|---|---|---|---| 
| IntPhys | V-JEPA | 2 | 7.5 | 16 | 2 |
|  | VideoMAEv2 | 2 | 7.5 | 16 | 2 |
|  | Qwen-2-VL-72b | 5 | 3 | All | N/A |
|  | Gemini-1.5-pro | 2 | 7.5 | All | N/A |
| GRASP | V-JEPA | 10 | 5 | 16 | 2 |
|  | VideoMAEv2 | 10 | 5 | 16 | 2 |
|  | Qwen-2-VL-72b | 10 | 5 | All | N/A |
|  | Gemini-1.5-pro | 10 | 5 | All | N/A |
| InfLevel-lab | V-JEPA | 5 | 6 | 32 | 2 |
|  | VideoMAEv2 | 10 | 3 | 16 | 2 |
|  | Qwen-2-VL-72b | 20 | 1.5 | All | N/A |
|  | Gemini-1.5-pro | 30 | 1 | All | N/A |{{< /table-caption >}}
> 🔼 표 S3는 본 논문의 실험에서 사용된 초매개변수들을 보여줍니다.  각 데이터셋(IntPhys, GRASP, InfLevel-lab)에 대해, V-JEPA, VideoMAE, Qwen-2-VL-72B, Gemini-1.5-pro 모델들의 프레임 건너뛰기(Frame skip), 초당 프레임 수(FPS), 윈도우 크기(Window size), 윈도우 스트라이드(Window Stride) 값들이 명시되어 있습니다. 이 표는 각 모델과 데이터셋에 적절한 초매개변수들을 선택하는 과정과 그 결과를 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table S3: Evaluation hyperparameters.
> </details>

{{< table-caption >}}
| Method | Surprise | Object permanence |  |  |  | Shape constancy |  |  |  | Continuity |  |  |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|  |  | Visible | Occluded | All | Visible | Occluded | All | Visible | Occluded | All |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| V-JEPA-H | Max | 0.6% | 8.2% | 4.4% | 0.8% | 8.1% | 4.4% | 0.19% | 25.6% | 12.87% |
| V-JEPA-H | Avg | 0.0% | 0.56% | 0.28% | 0.0% | 0.0% | 0.0% | 0.0% | 0.19% | 0.09% |
| V-JEPA-L | Max | 5.2% | 35.4% | 0.20% | 8.8% | 35.0% | 21.9% | 5.9% | 41.5% | 23.8% |
| V-JEPA-L | Avg | 0.9% | 1.8% | 1.4% | 2.5% | 3.5% | 3.1% | 0.7% | 3.3% | 2.0% |
| Riochet et al. (2020) |  | 5.0% | 19.0% | 12.0% | 11.0% | 31.0% | 21.0% | 26.0% | 47.0% | 41.0% |
| Human |  | 10.0% | 15.0% | 12.5% | 13.0% | 16.0% | 14.5% | 20.0% | 40.0% | 30.0% |{{< /table-caption >}}
> 🔼 표 S4는 IntPhys 테스트 세트에서 쌍으로 이루어진 비디오에 대한 쌍별 오류율을 보여줍니다. 비디오의 최대 또는 평균 놀라움 점수를 사용하여 평가했을 때 높은 성능을 보였으며, 이는 (Riochet et al., 2022)에 보고된 인간의 성능을 능가합니다. 이 표는 다양한 방법(V-JEPA, VideoMAE, Qwen-2-VL-72B, Gemini 1.5-pro)을 사용하여 여러 시각적 물리적 특성(객체 영속성, 연속성, 형태 일관성)에 대한 성능을 비교 분석한 결과를 보여줍니다.  각 방법의 최대 및 평균 놀람 점수에 따른 성능 차이도 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table S4: Pairwise error rates on IntPhys’ test set. For pairs of videos, taking either the maximum or average surprise from a video leads to high performance, surpassing the human results reported in (Riochet et al., 2022).
> </details>

{{< table-caption >}}
| Method | Surprise | Object permanence |  |  |  | Shape constancy |  |  |  | Continuity |  |  |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|  |  | Visible | Occluded | All | Visible | Occluded | All | Visible | Occluded | All |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| V-JEPA-H | Max | 8.0% | 28.1% | 19.2% | 11.9% | 29.7% | 21.9% | 7.8% | 43.9% | 29.67% |
| V-JEPA-H | Avg | 27.8% | 38.9% | 38.3% | 31.2% | 39.3% | 39.2% | 28.4% | 31.3% | 37.05% |
| V-JEPA-L | Max | 25.5% | 47.8% | 40.0% | 29.9% | 47.8% | 41.8% | 26.0% | 49.0% | 41.6% |
| V-JEPA-L | Avg | 33.4% | 41.7% | 41.5% | 37.0% | 42.5% | 42.7% | 34.4% | 38.8% | 41.5% |
| Human |  | 18.0% | 30.0% | 24.0% | 22.0% | 30.0% | 26.0% | 28.0% | 47.0% | 38.0% |{{< /table-caption >}}
> 🔼 표 S5는 IntPhys 테스트 세트에서 단일 비디오 분류 오류율(1-AUROC)을 보여줍니다. 단일 비디오의 경우 비디오의 최대 놀람 점수가 가장 높은 성능을 보이며, (Riochet et al., 2022)에 보고된 인간의 기준 성능을 능가합니다. 여기서 비디오의 평균 놀람 점수는 실험 설정에 과도하게 의존하기 때문에 좋은 지표가 아닙니다. 가독성을 위해 지표는 백분율로 보고합니다.
> <details>
> <summary>read the caption</summary>
> Table S5: Single video classification error rates (1-AUROC) on IntPhys’ test set. For single videos, we see that the maximum surprise of video leads to the highest performance, surpassing the human baselines reported in (Riochet et al., 2022). Here, the average surprise of a video is not a good metric, possibly due to values being too dependent on the experimental setup. We report the metric as percentages for legibility.
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