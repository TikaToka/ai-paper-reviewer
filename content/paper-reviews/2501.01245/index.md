---
title: "SeFAR: Semi-supervised Fine-grained Action Recognition with Temporal Perturbation and Learning Stabilization"
summary: "SeFAR: 제한된 데이터로도 정밀 동작 인식의 성능을 획기적으로 향상시키는 새로운 세미-슈퍼바이즈드 학습 프레임워크!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Action Recognition", "🏢 Unmanned System Research Institute, Northwestern Polytechnical University",]
showSummary: true
date: 2025-01-02
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.01245 {{< /keyword >}}
{{< keyword icon="writer" >}} Yongle Huang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-03 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.01245" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.01245" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

최근 **대규모 언어 모델(LLM)**의 발전에도 불구하고, **정밀한 의미를 가진 짧은 동작(예: 1회전 턴 동작)**을 인식하는 것은 여전히 어려운 과제입니다. 이는 **정밀한 레이블링 비용이 높고, LLM 미세 조정에 필요한 데이터가 방대**하기 때문입니다.  본 논문에서는 이 문제를 해결하기 위해 **세미-슈퍼바이즈드 학습(SSL)**을 활용한 새로운 프레임워크 SeFAR를 제안합니다. 



SeFAR은 **이중 시간 요소 모델링**을 통해 시각적 세부 정보를 포착하고, **적당한 시간적 섭동**을 통한 강력한 증강 전략을 활용합니다. 또한, **적응적 조절**을 통해 불확실성을 완화하고 학습 과정을 안정화합니다.  실험 결과, SeFAR은 **다양한 데이터 규모에서 최첨단 성능**을 달성하고, 기존의 SSL 방법들을 능가하며, **다중 모달 기반 모델의 성능 향상**에도 기여함을 보여줍니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} SeFAR은 세미-슈퍼바이즈드 학습을 통해 정밀 동작 인식 문제를 효과적으로 해결합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 시간적 섭동 및 학습 안정화 기법을 통해, 제한된 데이터로도 높은 정확도를 달성합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} SeFAR은 다중 모달 대규모 언어 모델의 정밀 동작 인식 능력을 향상시키는 데 기여합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **세미-슈퍼바이즈드 방식의 정밀 동작 인식(FAR)**이라는 어려운 과제에 대한 최초의 연구이며, **제한된 데이터로도 높은 성능을 달성**할 수 있는 새로운 프레임워크 SeFAR를 제시합니다.  **기존의 다중 모달 대규모 언어 모델(MLLM)의 성능 향상**에도 기여하며,  **영상 이해 분야의 새로운 연구 방향**을 제시하고, 미래 연구를 위한 기반을 마련합니다. 특히, **시간적 섭동 및 학습 안정화**라는 혁신적인 기법을 통해 FAR 문제 해결에 크게 기여하며, **영상 이해 분야의 발전에 중요한 의미**를 지닙니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.01245/x1.png)

> 🔼 그림 1은 FineGym 데이터셋(Shao et al., 2020a)에서 가져온 두 개의 세밀한 동작 예시를 보여줍니다. 위쪽은 'pike sole circle backward with 0.5 turn to handstand' 동작이고, 아래쪽은 '... 1 turn ...' 동작입니다.  논문에서는 아래쪽 동작 예시에 대해 인기있는 다중 모달 대규모 언어 모델(MLLM)들을 사용하여  일반적인 동작 인식과 세밀한 동작 인식 모두를 테스트했습니다.  테스트에 사용된 MLLM은 GPT-4V (OpenAI 2024), VideoChat2 (Li et al., 2024), VideoLLaVA (Lin et al., 2023), InternLM-XComposer-2.5 (Zhang et al., 2024)입니다. 이 그림은 MLLM이 세밀한 동작을 얼마나 잘 인식하는지 보여주는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Fine-grained Action Instances. The two samples are drawn from the FineGym (Shao et al. 2020a) dataset, specifically the “pike sole circle backward with 0.5 turn to handstand” at the top and the “… 1 turn …” at the bottom. We further test popular MLLMs on the bottom instance for both coarse-grained and fine-grained: GPT-4V (OpenAI 2024), VideoChat2 (Li et al. 2024), VideoLLaVA (Lin et al. 2023), and InternLM-XComposer-2.5 (Zhang et al. 2024).
> </details>





{{< table-caption >}}
| Method | Backbone | Input | ImgNet | Params | #F | Epoch | Gym99 5% | Gym99 10% | Gym288 5% | Gym288 10% | Diving 5% | Diving 10% |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| 2.5 **Method** | **Backbone** | **Input** | **ImgNet** | **Params** | **#F** | **Epoch** | **Gym99** | **Gym99** | **Gym288** | **Gym288** | **Diving** | **Diving** |
| 2 MemDPC (ECCV’20) [Han, Xie, and Zisserman 2020] | 3D-ResNet-18 | V | ✗ | 15.4M | 16 | 500 | 10.8 | 24.1 | 14.5 | 21.3 | 54.3 | 62.0 |
| LTG (CVPR’22) [Xiao et al. 2022] | 3D-ResNet-18 | VG | ✗ | 68.3M | 8 | 180 | 34.3 | 45.8 | 16.2 | 38.7 | 59.8 | 64.3 |
| SVFormer (CVPR’23) [Xing et al. 2023] | ViT-B | V | ✓ | 121.4M | 8 | 30 | 31.4 | 47.9 | 21.3 | 39.6 | 59.1 | 70.8 |
| SeFAR-S (Ours) | VIT-S | V | ✓ | 31.2M | 8 | 30 | 36.7 | 56.3 | 27.8 | 46.9 | 72.2 | 78.4 |
| SeFAR-B (Ours) | VIT-B | V | ✓ | 122.1M | 8 | 30 | 39.0 | 56.9 | 28.3 | 48.1 | 72.8 | 80.9 |{{< /table-caption >}}

> 🔼 표 1은 미세 입자 동작 인식 데이터셋에서 최첨단의 준지도 학습 기반 동작 인식 방법들과 SeFAR의 성능을 비교한 표입니다. SeFAR은 {2-2-4} 샘플링 조합을 사용했습니다. 주요 평가 지표는 top-1 정확도입니다. 표에서 'Input' 열의 'V'는 RGB 비디오를, 'G'는 시간적 기울기를 나타냅니다. 'ImgNet'은 ImageNet (Russakovsky et al., 2015)을 사전 훈련한 모델을 사용했음을 나타내며, '#F'는 입력 프레임 수를 나타냅니다. 데이터셋의 라벨링 비율은 5%, 10%, 20%로 표시되어 있습니다. 최고 성능은 **굵은 글씨**로, 두 번째로 좋은 성능은 밑줄로 표시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparison with state-of-the-art semi-supervised action recognition methods on fine-grained datasets. We employ SeFAR with a sampling combination of {2-2-4}. The primary evaluation metric is top-1 accuracy. In this table, “V” within “Input” denotes RGB video, while “G” represents temporal gradients. “ImgNet” indicates the utilization of models pre-trained on ImageNet (Russakovsky et al. 2015), while “#F” signifies the number of input frames. The labeling rates of the data are indicated by “5%”, “10%”, and “20%” in the datasets. The best results are highlighted in Bold, and the second-best Underlined.
> </details>





### In-depth insights


#### Semi-Supervised FAR
**준지도 학습 기반의 정밀 동작 인식(FAR)**은 기존의 완전 지도 학습 방식의 한계를 극복하기 위한 시도로, **데이터 부족 문제와 어노테이션 비용 문제**를 해결하고자 합니다.  **소량의 레이블된 데이터와 대량의 레이블되지 않은 데이터**를 활용하여 모델을 학습시키는 방식으로,  **효율성과 실용성**을 높일 수 있습니다.  이러한 접근법은 특히 정밀한 의미 분류가 필요한 FAR 분야에서 **비용 효과적이며 효율적인 해결책**을 제시할 수 있습니다.  하지만, **레이블되지 않은 데이터의 불확실성**과 **정밀한 동작 특징의 포착 어려움** 등의 과제가 존재하며, 이를 극복하기 위한 **강건한 알고리즘 및 효과적인 데이터 증강 기법**이 필요합니다.  **SeFAR와 같은 새로운 프레임워크**는 이러한 과제를 해결하기 위한 여러 가지 혁신적인 설계를 제시하며, **준지도 학습의 효율성과 정밀 동작 인식의 정확성**을 동시에 달성하는 것을 목표로 합니다.  향후 연구는 **더욱 다양한 데이터셋 및 알고리즘**을 활용한 **성능 개선**과 **실제 응용 분야**에 대한 적용을 중심으로 이루어져야 합니다.

#### Dual-Temporal Modeling
**이중 시간 모델링**은 동영상 내의 미묘한 행동 차이를 구분하기 위해 **다중 시간적 특징**을 효과적으로 포착하는 전략입니다.  **세분화된 시간 요소**와 **맥락 시간 요소**를 결합하여 다양한 시간적 정보를 효율적으로 분석합니다.  **세분화된 요소**는 짧은 시간 내의 미세한 변화를 포착하고 **맥락 요소**는 장기적인 패턴을 파악하는 데 도움을 주어서 **정확도**를 높입니다. 이러한 이중 접근 방식은 **미세한 동작 인식**에 특히 중요하며, 기존의 단일 시간 모델링보다 더 나은 성능을 제공합니다.  **시간적 섭동**과의 조합을 통해 강건성을 더욱 향상시키며, **불안정한 예측** 문제를 해결하는 데 기여할 수 있습니다.  **결론적으로**, 이중 시간 모델링은 **세분화된 동작 인식**에서 중요한 역할을 하며, **성능 개선**에 크게 기여합니다.

#### Temporal Perturbation
본 논문에서 제안하는 '시간적 섭동(Temporal Perturbation)' 기법은 **비디오 내 시간적 동작의 미묘한 변화를 학습**하기 위한 핵심 전략입니다. 기존의 강력한 증강 기법이 공간적 변형에 치중하는 반면, 시간적 섭동은 **비디오 프레임 순서를 조정**함으로써 모델이 시간적 흐름에 대한 이해도를 높이는 데 집중합니다. 이는 특히 **미세한 동작 인식(Fine-grained Action Recognition)**에서 중요한데, 미세한 동작은 시간적 순서에 민감하기 때문입니다.  **적당한 수준의 섭동**을 통해 모델은 시간적 변화에 대한 강건성을 확보하며, 동시에 과도한 섭동으로 인한 의미 손실을 방지합니다.  **교사-학생(Teacher-Student) 학습 구조**와 결합하여, 약한 섭동을 가한 비디오를 사용하여 교사 모델이 의사 레이블을 생성하고, 강한 섭동을 가한 비디오를 학습하는 학생 모델의 성능을 향상시킵니다.  결과적으로, 시간적 섭동은 **미세 동작 인식의 정확도를 높이고, 모델의 일반화 성능을 향상**시키는 데 크게 기여합니다.  **시간적 섭동의 강도 조절**은 모델의 성능에 중요한 영향을 미치므로, 적절한 섭동 강도를 찾는 것이 중요한 연구 과제입니다.

#### Adaptive Regulation
본 논문에서 제안하는 적응적 조절(Adaptive Regulation)은 **불안정한 teacher 모델 예측**으로 인해 발생하는 semi-supervised fine-grained action recognition 학습의 어려움을 해결하기 위한 핵심 전략입니다.  **Teacher 모델의 예측 신뢰도와 불확실성을 정량화**하여, 학습 과정에서의 안정성을 확보하고자 합니다.  **높은 신뢰도의 예측에는 높은 가중치**, 낮은 신뢰도의 예측에는 낮은 가중치를 부여하여, **불안정한 pseudo-label로 인한 학습 붕괴를 방지**합니다.  이는 단순히 임계값을 설정하는 기존 방식보다 유연하며,  **데이터의 특성과 모델의 불확실성을 동적으로 반영**하여 최적의 학습 성능을 달성하는 데 기여합니다.  **표준편차와 최대 신뢰도 값을 기반**으로 계산되는 적응적 계수는, 모델의 예측 안정성을 높이고, fine-grained action recognition의 어려움을 효과적으로 극복하는 데 중요한 역할을 수행합니다. 특히, **높은 신뢰도에도 불구하고 높은 표준편차**를 가지는 경우, 해당 예측의 가중치를 낮춤으로써, **과도한 신뢰에 따른 오류 확산을 방지**합니다.

#### MLLM Enhancement
본 논문은 세미-슈퍼바이즈드 방식의 정교한 동작 인식(FAR) 모델인 SeFAR을 제시하며, **다양한 수준의 시간적 정보를 효과적으로 활용**하는 이중적 시간 요소 모델링 기법을 사용합니다.  또한, **교사-학생 학습 구조**를 기반으로, 적절한 시간적 섭동을 통해 강력한 데이터 증강 전략을 구현하고, 교사 모델의 예측 불확실성을 해소하기 위한 적응적 조절 메커니즘을 도입하여 학습 안정성을 확보합니다.  흥미로운 점은 SeFAR가 **다양한 멀티모달 대규모 언어 모델(MLLM)**의 성능 향상에 기여한다는 것입니다.  **특히, SeFAR의 특징 추출 능력**을 활용하여 기존 MLLM의 비전 인코더를 대체함으로써, 정교한 의미를 요구하는 도메인 특정 시나리오에서 MLLM의 성능을 크게 개선할 수 있음을 보여줍니다.  이는 단순한 동작 인식을 넘어, **MLLM의 시각적 이해 능력 자체를 강화**하는 데 기여하는 핵심적인 발견입니다.  결론적으로, SeFAR는 세미-슈퍼바이즈드 학습 환경에서 정교한 동작 인식의 새로운 지평을 열고, MLLM의 성능 향상에도 크게 기여하는 혁신적인 접근 방식임을 제시합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.01245/extracted/6107226/fig2_00.png)

> 🔼 그림 2는 SeFAR의 파이프라인 개요를 보여줍니다. SeFAR은 대부분의 입력 샘플이 레이블이 지정되지 않은 준지도 학습을 목표로 합니다.  준지도 학습 중에 SeFAR은 이중 수준의 시간적 요소 모델링을 채택하고 두 가지 방식('약한' 대 '강한')으로 증강을 수행합니다. 적당한 시간적 섭동에 의해 강하게 증강/왜곡된 샘플은 학생 모델에 의해 사용되는 반면, 약하게 증강된 샘플을 기반으로 교사 모델이 의사 레이블을 제공합니다. 손실 최소화(ℒ𝑢𝑛)을 통해 일관성이 강화됩니다.  비지도 학습 손실은 제안된 적응적 규제에 의해 추가로 조정됩니다. 이 프레임워크는 지도 학습 손실(ℒ𝑠𝑢𝑝)과 비지도 학습 손실(ℒ𝑢𝑛)의 가중 조합으로 학습됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 2:  Overview of SeFAR pipeline. We target Semi-supervised FAR, assuming most input samples are unlabeled. During unsupervised learning, SeFAR adopts dual-level temporal elements modeling and performs augmentation in two manners (‘Weak’ vs. ‘Strong’). Strongly augmented/distorted samples by moderate temporal perturbation are used by the student model, while the teacher model offers pseudo-labels based on weakly augmented samples. Consistency is enforced through loss minimization (ℒu⁢nsubscriptℒ𝑢𝑛\mathcal{L}_{un}caligraphic_L start_POSTSUBSCRIPT italic_u italic_n end_POSTSUBSCRIPT). The unsupervised loss is further adjusted by our proposed Adaptive Regulation. The framework is trained with a weighted combination of supervised ℒs⁢u⁢psubscriptℒ𝑠𝑢𝑝\mathcal{L}_{sup}caligraphic_L start_POSTSUBSCRIPT italic_s italic_u italic_p end_POSTSUBSCRIPT and unsupervised ℒu⁢nsubscriptℒ𝑢𝑛\mathcal{L}_{un}caligraphic_L start_POSTSUBSCRIPT italic_u italic_n end_POSTSUBSCRIPT losses.
> </details>



![](https://arxiv.org/html/2501.01245/extracted/6107226/fig3.png)

> 🔼 그림 3은 두 가지 내용을 보여줍니다. (a)는 K개의 비표지된 비디오에 대해 Teacher 모델이 여러 번 예측하여 예측 분포를 파악하는 과정을 보여줍니다. 이 과정에서 조잡한 동작 데이터보다 세밀한 동작 데이터에서 예측 분포의 변동성이 더 크다는 것을 보여줍니다. 이러한 변동성을 바탕으로 평균과 분산을 사용하여 적응형 계수 η를 계산하여 학습 과정을 안정화시킵니다. (b)는 SeFAR의 세밀한 특징을 사용한 MLLM 구성 파이프라인을 보여줍니다. SeFAR 모델의 특징 추출을 통해 MLLM의 성능 향상을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3:  (a) For K𝐾Kitalic_K unlabeled videos, the Teacher model predicts each video multiple times to capture the distribution of predictions, which shows less variability on coarse-grained data and more on fine-grained data. An adaptive coefficient η𝜂\etaitalic_η is calculated from the mean and variance of the distribution to stabilize training. (b) MLLM construction pipeline with SeFAR’s fine-grained features.
> </details>



![](https://arxiv.org/html/2501.01245/extracted/6107226/fig4.png)

> 🔼 그림 4는 SeFAR 모델의 성능에 영향을 미치는 요소들을 분석한 결과를 보여줍니다. 왼쪽은 Gym-99 데이터셋(라벨링 비율 5%)에서 서로 다른 샘플링 조합을 사용했을 때 SeFAR-B 모델의 성능을 비교한 것입니다. 가운데는 FineDiving 데이터셋(라벨링 비율 5%)에서 고정 임계값 방법과 SeFAR의 적응적 조절 전략을 비교 분석한 결과입니다. 오른쪽은 여러 데이터셋에서 Teacher 모델의 예측값 변동성을 보여줍니다.  즉, 그림은 SeFAR 모델의 주요 구성 요소들의 효과를 실험적으로 검증하기 위한 ablation study 결과를 종합적으로 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4:  Ablation Studies. We compare SeFAR-B with different sampling combinations on Gym-99 5%, as illustrated on the left. We also contrast fixed threshold methods with our Adaptive Regulation strategy on FineDiving 5% in the middle. On the right side, we demonstrate the fluctuation of predictions made by the Teacher model across different datasets.
> </details>



![](https://arxiv.org/html/2501.01245/x2.png)

> 🔼 그림 5는 교사 모델의 예측 정확도와 신뢰도(왼쪽), 그리고 표준 편차(오른쪽) 사이의 관계를 보여줍니다. 왼쪽 패널은 교사 모델의 예측에 대한 신뢰도 수준과 그 정확도 사이의 상관관계를 보여줍니다. 높은 신뢰도를 가진 예측은 일반적으로 더 높은 정확도를 나타냅니다. 오른쪽 패널은 교사 모델의 예측에서 표준 편차와 그 정확도 사이의 관계를 보여줍니다. 예측의 분산이 작을수록 정확도가 높아지는 경향이 있습니다. 이 그림은 적응적 규제(Adaptive Regulation) 개념을 뒷받침하는 근거를 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5:  The relationship between the Teacher model’s prediction accuracy and its confidence (left), as well as its standard deviation (right).
> </details>



![](https://arxiv.org/html/2501.01245/x3.png)

> 🔼 그림 6은 본 논문에서 새롭게 제안하는 Gym-QA 데이터셋의 예시를 보여줍니다. Gym-QA는 기존의 FineGym 데이터셋을 바탕으로 다중 선택지 질문 형태로 만들어진 데이터셋입니다. 그림에는 비디오 영상과 함께 '선수가 수행한 동작은 무엇입니까?' 라는 질문과 네 가지 선택지가 제시되어 있습니다. 각 선택지는 세세한 동작의 차이를 보여주는 상세한 설명을 포함하고 있습니다. 이를 통해, 세밀한 동작 인식(Fine-grained Action Recognition)의 어려움을 보여주고, 제안된 SeFAR 모델의 성능을 평가하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 6:  Examples of Gym-QA
> </details>



![](https://arxiv.org/html/2501.01245/x4.png)

> 🔼 그림 7은 논문의 Gym-New 데이터셋의 예시를 보여줍니다. Gym-New는 기존 FineGym 데이터셋에서 동작 방향이 반대인 동작 쌍을 선택하여 만든 데이터셋입니다. 그림에는 세 가지 유형의 동작(Salto, Pike sole circle, Giant circle)이 제시되어 있으며, 각 유형에 대해 동작 방향이 반대인 두 개의 예시가 나란히 배치되어 있습니다. 이를 통해 시간적 방향성이 동작 인식에 미치는 영향을 더욱 명확하게 분석하고, 모델의 성능을 평가할 수 있도록 설계되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7:  Examples of Gym-New
> </details>



![](https://arxiv.org/html/2501.01245/x5.png)

> 🔼 그림 8은 Gym-New 데이터셋의 10% 레이블을 사용하여 기준 모델(왼쪽)과 제안된 SeFAR 모델(오른쪽)의 혼동 행렬을 보여줍니다. 가로축은 예측 레이블을, 세로축은 실제 레이블을 나타냅니다. 각 레이블은 그림 9에서 확인할 수 있습니다. 이 그림은 두 모델의 성능 차이를 시각적으로 보여주는 동시에, SeFAR 모델이 특히 유사한 동작들을 더 잘 구분한다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8:  Confusion matrix of baseline (left) and ours (right) on Gym-New 10%, where the horizontal coordinate represents the predicted label and the vertical coordinate represents the true label. The labels corresponding to actions are shown in Fig. 9.
> </details>



![](https://arxiv.org/html/2501.01245/x6.png)

> 🔼 그림 9는 Gym-New 데이터셋에 사용된 동작에 대한 레이블을 보여줍니다.  Gym-New 데이터셋은 세 가지 체조 종목(도마, 평행봉, 마루운동)에 걸쳐 정의된 40가지의 미세립 동작을 포함합니다.  각 동작은 짧은 설명과 함께 표시되어 있어, 모델이 각 동작의 시각적 차이를 구별하는 데 도움이 됩니다. 이 표는 논문에서 제안된 SeFAR 모델의 성능을 평가하는 데 사용되는 데이터의 구성을 이해하는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9:  Labels corresponding to actions in Gym-New.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | UB 10% | UB 20% | FX 10% | FX 20% | 10m 10% | 10m 20% |
|---|---|---|---|---|---|---|
| 2.5 Method | **UB** |  | **FX** |  | **10m** |  |
|  | **10%** | **20%** | **10%** | **20%** | **10%** | **20%** |
| 2 MemDPC | 20.7 | 19.1 | 13.8 | 15.9 | 65.4 | 71.2 |
| LTG | 50.5 | 60.5 | 19.6 | 21.6 | 75.2 | 83.5 |
| SVFormer | 52.9 | 66.8 | 20.1 | 28.8 | 73.8 | 85.9 |
| SeFAR-S (Ours) | **56.9** | **73.8** | **23.8** | **42.9** | **85.5** | **94.0** |
| SeFAR-B (Ours) | **58.5** | **75.5** | **27.6** | **44.2** | **87.4** | **94.6** |
| 2.5  |  |  |  |  |  |  |{{< /table-caption >}}
> 🔼 표 1(a)는 미세립 데이터셋에서 다양한 반(semi-supervised) 동작 인식 방법들과 SeFAR의 성능을 비교한 표입니다.  'elements across all events'는 FineGym 데이터셋의 계층적 주석(event, set, element) 중 가장 세부적인 수준인 element 단위로 모든 event에 걸쳐 결과를 평균낸 것을 의미합니다.  표에는 방법(Method), 백본(Backbone), 입력(Input), ImageNet 사전 훈련 여부(ImgNet), 매개변수 수(Params), 프레임 수(#F), 에폭(Epoch), 그리고 5%, 10% 라벨링 비율에서 Gym99, Gym288, Diving 데이터셋에 대한 top-1 정확도가 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> (a) Results of elements across all events.
> </details>

{{< table-caption >}}
| Method | UB-S1 (10%) | UB-S1 (20%) | FX-S1 (10%) | FX-S1 (20%) | 5253B (10%) | 5253B (20%) |
|---|---|---|---|---|---|---|
| 2.5 Method | **UB-S1** |  | **FX-S1** |  | **5253B** |  |
|  | **10%** | **20%** | **10%** | **20%** | **10%** | **20%** |
| MemDPC | 17.2 | 21.1 | 15.4 | 20.1 | 82.2 | 89.5 |
| LTG | 21.3 | 29.7 | 14.6 | 19.3 | 64.6 | 76.9 |
| SVFormer | 28.9 | 47.3 | 18.8 | 22.5 | 86.6 | 90.1 |
| SeFAR-S (Ours) | **36.6** | **55.3** | **19.2** | **25.5** | **96.4** | **97.3** |
| SeFAR-B (Ours) | **37.1** | **56.8** | **20.1** | **26.5** | **97.0** | **97.8** |
| 2.5  |  |  |  |  |  |  |{{< /table-caption >}}
> 🔼 표 1의 (b)는 세부 동작(element) 단위의 정확도를 보여줍니다.  FineGym 데이터셋에서 특정 종목(event) 내의 세부 동작들에 대한 모델 성능을 보다 자세히 분석한 결과입니다.  예를 들어, 특정 체조 종목 안에서 수행되는 여러 다양한 세부 동작들에 대한 정확도를 개별적으로 비교하여, 모델의 미세한 동작 구분 능력을 평가합니다.  표의 결과는 각 event 내에서 element 단위로 평가된 성능을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> (b) Results of elements within an event.
> </details>

{{< table-caption >}}
| 2.5 **Method** | **Backbone** | **Input** | **ImgNet** | **#F** | **Epoch** | **UCF-101 1%** | **UCF-101 5%** | **UCF-101 10%** | **HMDB-51 40%** | **HMDB-51 50%** |
|---|---|---|---|---|---|---|---|---|---|---|
| 2 MT+SD (WACV’21) [Jing et al. (2021)](https://arxiv.org/html/2501.01245/bib.bib21)| 3D-ResNet-18 | V | ✗ | 16 | 500 | - | 31.2 | 40.7 | 32.6 | 35.1 |
| MvPL (ICCV’21) [Xiong et al. (2021)](https://arxiv.org/html/2501.01245/bib.bib56) | 3D-ResNet-50 | VFG | ✗ | 8 | 600 | 22.8 | 41.2 | 80.5 | 30.5 | 33.9 |
| TCLR (CVIU’22) [Dave et al. (2022)](https://arxiv.org/html/2501.01245/bib.bib9) | 3D-ResNet-18 | V | ✗ | 16 | 1200 | 26.9 | - | 66.1 | - | - |
| CMPL (CVPR’22) [Xu et al. (2022b)](https://arxiv.org/html/2501.01245/bib.bib58) | R50+R50-1/4 | V | ✗ | 8 | 200 | 25.1 | - | 79.1 | - | - |
| LTG (CVPR’22) [Xiao et al. (2022)](https://arxiv.org/html/2501.01245/bib.bib53) | 3D-ResNet-18 | VG | ✗ | 8 | 180 | - | 44.8 | 62.4 | 46.5 | 48.4 |
| TimeBalance (CVPR’23) [Dave et al. (2023)](https://arxiv.org/html/2501.01245/bib.bib10) | 3D-ResNet-50 | V | ✗ | 8 | 250 | 30.1 | 53.3 | 81.1 | 52.6 | 53.9 |
| SeFAR (Ours) | VIT-S | V | ✗ | 8 | 30 | 35.2 | 64.1 | 78.3 | 55.9 | 59.2 |
| 1.6 FixMatch (NeurlPS’20) [Sohn et al. (2020)](https://arxiv.org/html/2501.01245/bib.bib42) | SlowFast-R50 | V | ✓ | 8 | 200 | 16.1 | - | 55.1 | - | - |
| MemDPC (ECCV’20) [Han, Xie, and Zisserman (2020)](https://arxiv.org/html/2501.01245/bib.bib18) | 3D-ResNet-18 | V | ✓ | 16 | 500 | - | - | 44.2 | - | - |
| ActorCM (CVIU’21) [Zou et al. (2023)](https://arxiv.org/html/2501.01245/bib.bib69) | R(2+1)D-34 | V | ✓ | 8 | 360 | - | 45.1 | 53.0 | 35.7 | 39.5 |
| VideoSSL (WACV’21) [Jing et al. (2021)](https://arxiv.org/html/2501.01245/bib.bib21) | 3D-ResNet-18 | V | ✓ | 16 | 500 | - | 32.4 | 42.0 | 32.7 | 36.2 |
| TACL (TSVT’22) [Tong, Tang, and Wang (2023)](https://arxiv.org/html/2501.01245/bib.bib46) | 3D-ResNet-50 | V | ✓ | 16 | 200 | - | 35.6 | 55.6 | 38.7 | 40.2 |
| L2A (ECCV’22) [Gowda et al. (2022)](https://arxiv.org/html/2501.01245/bib.bib16) | 3D-ResNet-18 | V | ✓ | 8 | 400 | - | - | 60.1 | 42.1 | 46.3 |
| SVFormer-S (CVPR’23) [Xing et al. (2023)](https://arxiv.org/html/2501.01245/bib.bib55) | ViT-S | V | ✓ | 8 | 30 | 31.4 | - | 79.1 | 56.2 | 58.2 |
| SVFormer-B (CVPR’23) [Xing et al. (2023)](https://arxiv.org/html/2501.01245/bib.bib55) | ViT-B | V | ✓ | 8 | 30 | 46.1 | - | 84.6 | 59.9 | 64.3 |
| SeFAR (Ours) | VIT-S | V | ✓ | 8 | 30 | 46.0 | 73.2 | 84.3 | 58.5 | 62.9 |
| SeFAR (Ours) | VIT-B | V | ✓ | 8 | 30 | **50.3** | **77.6** | **87.0** | **61.5** | **65.7** |{{< /table-caption >}}
> 🔼 표 1의 (c)는 FineGym 데이터셋의 특정 이벤트 내에 있는 요소들에 대한 결과를 보여줍니다.  각 이벤트는 여러 개의 요소(예: 특정 체조 동작의 세부 동작)로 구성됩니다. 이 표는  각 요소에 대한 모델의 성능을 10%와 20%의 라벨링 비율로 평가한 결과를 보여줍니다.  즉, 세부적인 동작 인식의 정확도를 이벤트 별로 더욱 자세히 분석한 결과입니다.
> <details>
> <summary>read the caption</summary>
> (c) Results of elements within a set.
> </details>

{{< table-caption >}}
| 2.5 **Dual-Ele** | **Mod-Perturb** | **Ada-Reg** | **Gym99** | **Gym288** | **Diving** |
|---|---|---|---|---|---| 
| 2 ✗ | ✗ | ✗ | 32.6 | 22.7 | 60.4 |
| ✓ | ✗ | ✗ | 34.8 | 25.4 | 64.6 |
| ✓ | ✓ | ✗ | 35.9 | 26.6 | 67.4 |
| ✓ | ✓ | ✓ | **36.7** | **27.8** | **72.2** |
| 2.5 |  |  |  |  |  |{{< /table-caption >}}
> 🔼 표 2는 널리 사용되는 동작 인식 데이터셋인 UCF-101과 HMDB-51에서 다양한 최첨단 반지도 학습 기반 동작 인식 방법들과 SeFAR의 성능을 비교 분석한 표입니다.  'V'는 RGB 비디오, 'F'는 광학 흐름(optical flow), 'G'는 시간적 기울기(temporal gradients)를 나타냅니다.  각 방법의 백본 네트워크, 입력 데이터 유형(비디오, 광학 흐름, 시간적 기울기), ImageNet 사전 학습 여부, 프레임 수, 에폭 수, 그리고 다양한 라벨 비율(1%, 5%, 10%, 40%, 50%)에서의 UCF-101과 HMDB-51 데이터셋에 대한 상위 1% 정확도를 보여줍니다. 이 표를 통해 SeFAR 모델의 강건성과 성능을 객관적으로 평가하고 다른 최신 방법들과 비교하여 우수성을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Comparison with state-of-the-art semi-supervised action recognition methods on coarse-grained datasets.“V” within “Input” signifies RGB video, “F” indicates optical flow, while “G” denotes temporal gradients.
> </details>

{{< table-caption >}}
| Perturbation | S/O | Gym99 | Gym288 | Diving | G.-New | Sth.-Sth. |
|---|---|---|---|---|---|---|
| 2.5 **Perturbation** |  | **Gym99** | **Gym288** | **Diving** | **G.-New** | **Sth.-Sth.** |
| 2 Spatial-only |  | 34.2 | 24.4 | 67.9 | 45.6 | 39.4 |
| Slow (T-Drop) | S | 35.6 | 25.2 | 68.6 | 45.0 | 41.2 |
| All shuffle | O | 35.2 | 26.3 | 69.0 | 45.5 | 41.9 |
| Local-shuffle | O | 36.4 | 27.6 | 71.9 | 45.3 | 43.3 |
| Warping | O | 35.9 | 24.7 | 68.2 | 44.8 | 40.8 |
| T-Half | O | 36.0 | 24.8 | 68.4 | 44.8 | 42.1 |
| All reverse | O | 36.3 | 27.3 | 71.2 | 45.9 | 42.7 |
| Mod-Perturb | O | **36.7** | **27.8** | **72.2** | **46.2** | **44.9** |
| 2.5 |  |  |  |  |  |  |{{< /table-caption >}}
> 🔼 표 3은 SeFAR의 구성 요소별 효과를 분석한 결과를 보여줍니다.  '✓'는 해당 구성 요소를 사용했음을 의미합니다.  일관성 규제 원칙을 준수하기 위해, Mod-Perturb(Moderate Temporal Perturbation)을 제거한 경우에는 SVFormer(Xing et al., 2023)와 일관되게 시간 왜곡을 강력한 증강 기법으로 사용했습니다.  표는 Dual-level Temporal Elements, Mod-Perturb, Ada-Reg(Adaptive Regulation) 세 가지 구성 요소를 각각 사용했을 때와 사용하지 않았을 때의 FineGym, Gym288, FineDiving 데이터셋에 대한 성능을 비교 분석하여 각 구성요소의 기여도를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Ablations of different components with SeFAR, where ✓ means “w/”. To adhere to the principle of consistency regularization in SSL, we employ strong augmentation consistent with SVFormer (Xing et al. 2023), i.e., temporal warping, once our Mod-Perturb is eliminated.
> </details>

{{< table-caption >}}
| Visual Encoder | MLLM | Gym-QA-99 | Gym-QA-288 |
|---|---|---|---| 
| 2.5 **Visual Encoder** | **MLLM** | **Gym-QA-99** | **Gym-QA-288** |
| 2 CLIP-ViT-L/16 | https://arxiv.org/html/2501.01245/LLaVA.png, https://arxiv.org/html/2501.01245/VideoChat2.png | 37.3 | 41.0 |
| EVA-CLIP ViT-G/14 | https://arxiv.org/html/2501.01245/VideoLLaMA.png, https://arxiv.org/html/2501.01245/VideoChat.png | 43.7 | 44.8 |
| ViT-L/14 | https://arxiv.org/html/2501.01245/VideoLLaMA.png | 44.3 | 46.0 |
| SeFAR (Ours) | - | **49.0** | **56.2** |
| 2.5 |  |  |  |{{< /table-caption >}}
> 🔼 표 4는 서로 다른 시간적 증강 기법들의 영향을 비교 분석한 결과를 보여줍니다.  'S'는 속도 중심, 'O'는 순서 중심 증강을 나타냅니다.  각 증강 기법(Spatial-only, Slow(T-Drop), All shuffle, Local-shuffle, Warping, T-Half, All reverse, Mod-Perturb)에 따른 FineGym 데이터셋(Gym99, Gym288, Diving)의 성능(Top-1 정확도) 변화를 보여주어, 제안된 Mod-Perturb 기법의 효과를 검증합니다.  다양한 시간적 증강 방법들의 성능을 비교하여, 어떤 기법이 Fine-grained Action Recognition(FAR)에 가장 적합한지 확인하고, 제안된 Mod-Perturb 기법의 우수성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Ablation of different temporal augmentations. S and O denote the Speed- and Order-focused.
> </details>

{{< table-caption >}}
| Method | FineDiving |  |  |  |  | 
|---|---|---|---|---|---| 
| 2.5 **Method** | **1%** | **3%** | **5%** | **7%** | **10%** | 
| 2 SeFAR w/o Ada-Reg | 61.5 | 64.6 | 67.2 | 69.7 | 73.4 | 
| SeFAR | **66.3** | **69.5** | **72.2** | **74.6** | **78.4** | 
| Increase (%) | 7.8%↑ | 7.6%↑ | 7.4%↑ | 7.0%↑ | 6.8%↑ | 
| 2.5 |  |  |  |  |  | {{< /table-caption >}}
> 🔼 표 5는 사전 훈련된 비주얼 인코더의 ablation study 결과를 보여줍니다. 기본 LLM으로 Vicuna-7B (Chiang et al., 2023)를 사용하고, 5%의 데이터로 추가 미세 조정된 MLLM에서 일반적으로 사용되는 비주얼 인코더의 사전 훈련된 특징들과 SeFAR의 특징들을 비교합니다.  비교 대상 비주얼 인코더는 LLaVA, VideoChat2, VideoLLaMA, VideoChat, VideoLLaVA입니다.  각 인코더의 성능을 Gym-QA-99와 Gym-QA-288 데이터셋에서 평가하여 SeFAR 특징이 다른 사전 훈련된 비주얼 인코더에 비해 얼마나 성능 향상을 가져오는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Ablation of Pre-trained Visual Encoder. We employ Vicuna-7B (Chiang et al. 2023) as the base LLM, comparing SeFAR’s features with the pre-trained features of commonly used visual encoders in MLLMs further fine-tuned on 5% data (i.e.,    : LLaVA,    : VideoChat2,    : VideoLLaMA,    : VideoChat, and    : VideoLLaVA)
> </details>

{{< table-caption >}}
| 2.5 **Perturbation** | **Speed/Order** | **FX** | **10m** | **UB-S1** | **5253B** |
|---|---|---|---|---|---| 
| 2 Slow-rate | Speed | 22.4 | 81.2 | 35.6 | 92.8 |
| T-Drop | Speed | 22.4 | 81.2 | 35.6 | 92.8 |
| All shuffle | Order | 23.5 | 82.8 | 36.1 | 93.5 |
| Local-shuffle | Order | 23.0 | 84.1 | 36.5 | 94.9 |
| Warping | Order | 23.4 | 81.9 | 34.7 | 92.9 |
| T-Half | Order | 23.3 | 83.0 | 35.3 | 93.4 |
| All reverse | Order | 23.6 | 83.7 | 35.5 | 95.1 |
| Mod-Perturb | Order | 23.8 | 85.5 | 36.6 | 96.4 |
| 2.5 |  |  |  |  |  |{{< /table-caption >}}
> 🔼 표 6은 다양한 레이블 비율에 따른 SeFAR의 성능 변화를 보여줍니다.  처음 두 행은 각각 적응적 조절(Ada-Reg)을 사용하지 않은 SeFAR과 사용한 SeFAR의 결과를 보여줍니다. 세 번째 행은 다양한 레이블 비율에서 성능 향상률을 보여줍니다.  레이블 비율이 감소함에 따라 적응적 조절(Ada-Reg)의 효과가 더욱 두드러짐을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Ablation of different labeling rates. The first two raw demonstrate our SeFAR w/o and w/ the Adaptive Regulation (Ada-Reg) respectively. The third raw further shows the performance increase rates at different labeling rates.
> </details>

{{< table-caption >}}
| Prediction Times | 1 | 2 | 5 | 10 | 15 | 20 |
|---|---|---|---|---|---|---|
| 2.5 **Prediction Times** | **1** | **2** | **5** | **10** | **15** | **20** |
| 2 Teacher time / Iter. | 29.9 | 68.5 | 75.8 | 160.4 | 260.1 | 361.3 |
| Total time / Iter. | 982.8 | 991.6 | 1005.1 | 1080.7 | 1220.6 | 1417.6 |
| Portion (%) | 3.0 | 6.9 | 7.5 | 14.8 | 21.3 | 25.5 |
| Accuracy (%) | - | 35.3 | 36.2 | 36.7 | 36.8 | 37.0 |
| 2.5 |  |  |  |  |  | |{{< /table-caption >}}
> 🔼 표 7은 다양한 시간적 증강 기법들의 성능을 심층적으로 비교 분석한 결과를 보여줍니다.  속도 중심 및 순서 중심 증강 기법들을 비롯해, 다양한 기법들의 FineGym 데이터셋의 FX, 10m, UB-S1, 5253B 이벤트에 대한 Top-1 정확도를 제시하며, 각 기법의 강점과 약점을 파악하는 데 도움을 줍니다.  시간적 왜곡, 순서 변경, 임의 셔플 등 여러 시간적 증강 기법과 제안된 방법인 적당한 시간적 섭동(Mod-Perturb)의 성능을 비교하여, 어떤 기법이 fine-grained action recognition에 가장 효과적인지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Deeper comparison of temporal augmentations.
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
{{< /gallery >}}