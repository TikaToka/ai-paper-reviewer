---
title: "Continuous Diffusion Model for Language Modeling"
summary: "연구진은 **이산 데이터의 기하학적 특성을 고려한 연속 확산 언어 모델(RDLM)**을 제시하여 기존 이산 및 연속 확산 모델의 한계를 극복했습니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Text Generation", "🏢 Korea Advanced Institute of Science and Technology",]
showSummary: true
date: 2025-02-17
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.11564 {{< /keyword >}}
{{< keyword icon="writer" >}} Jaehyeong Jo et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-19 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.11564" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.11564" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/continuous-diffusion-model-for-language" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 이산 데이터 모델링은 반복적인 개선 과정에서 신호 손실이 발생하는 문제점을 가지고 있었고, 기존 연속 확산 모델은 이산 데이터에 적용될 때 성능이 떨어지는 한계를 보였습니다.  **특히, 이산 및 연속 확산 모델 간의 명확한 연결 고리가 부족하여 이산 데이터에 대한 확산 모델 개발이 제한적**이었습니다.

본 연구는 **이러한 문제를 해결하기 위해 통계 다양체의 기하학적 구조를 고려한 새로운 연속 확산 언어 모델(RDLM)**을 제안합니다.  RDLM은 이산 확산과 연속 흐름 간의 관계를 수립하고, 이를 통해 이산 확산 모델을 일반화하는 간단한 확산 프로세스를 제시합니다.  **방사형 대칭성과 고차원 다양체 문제 해결 기법**을 활용하여 시뮬레이션이 필요 없는 학습 프레임워크를 구축하고, 다양한 실험 결과를 통해 기존 모델 대비 우수한 성능을 입증했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 이산 확산 모델과 연속 확산 모델 간의 연결성을 확립하고, 이를 바탕으로 이산 확산 모델을 일반화하는 간단한 확산 프로세스 설계 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 통계 다양체의 기하학적 구조를 활용하여 고차원 다양체 문제 해결 및 효율적인 학습 프레임워크 구축 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 다양한 벤치마크 데이터셋에서 기존 이산 및 연속 확산 모델을 능가하는 성능을 달성 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**본 논문은 이산 데이터에 대한 생성 모델링 분야의 발전에 크게 기여하며**, 언어 모델링 및 다양한 이산 데이터 작업에 대한 새로운 접근 방식을 제시합니다. **연구 결과는 다양한 응용 분야에 적용될 수 있으며**, 특히 이산 데이터를 효율적으로 처리해야 하는 자연어 처리, 이미지 생성, 생물학적 서열 설계 등의 분야에서 **기존 모델의 성능을 능가하는 혁신적인 결과**를 보여줍니다. 따라서 이 논문은 관련 분야 연구자들에게 중요한 의미를 지니며, 향후 연구 방향에 대한 새로운 시각을 제공합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.11564/x1.png)

> 🔼 이 그림은 Text8 테스트 세트에서 비트당 문자 수(BPC)를 비교하여 훈련 목표 간의 성능을 비교한 것입니다. 세 가지 다른 훈련 목표, 즉 드리프트 MSE, 교차 엔트로피, 그리고 교차 엔트로피와 중요도 샘플링을 결합한 방법의 결과를 보여줍니다.  그림은 각 목표에 대한 BPC 값의 변화를 보여주는 그래프를 포함하고 있습니다. 이를 통해 어떤 훈련 목표가 Text8 데이터셋에서 가장 좋은 성능을 내는지 시각적으로 비교할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  Comparison between the training objectives. We compare Bits Per Character (BPC) on the Text8 test set.
> </details>





{{< table-caption >}}
| Method | BPC (<math alttext="\downarrow" class="ltx_Math" display="inline" id="S6.T1.1.1.1.1.m1.1"><semantics id="S6.T1.1.1.1.1.m1.1a"><mo id="S6.T1.1.1.1.1.m1.1.1" stretchy="false" xref="S6.T1.1.1.1.1.m1.1.1.cmml">↓</mo><annotation-xml encoding="MathML-Content" id="S6.T1.1.1.1.1.m1.1b"><ci id="S6.T1.1.1.1.1.m1.1.1.cmml" xref="S6.T1.1.1.1.1.m1.1.1">↓</ci></annotation-xml><annotation encoding="application/x-tex" id="S6.T1.1.1.1.1.m1.1c">\downarrow</annotation><annotation encoding="application/x-llamapun" id="S6.T1.1.1.1.1.m1.1d">↓</annotation></semantics></math>) | 
|---|---| 
| *Autoregressive* |  | 
| IAF/SCF | 1.88 | 
| AR Argmax Flow | 1.39 | 
| Transformer AR | **1.23** | 
| Discrete Flow | **1.23** | 
| *Any-order Autoregressive* |  | 
| ARDM | ≤ 1.43 | 
| MAC | ≤ 1.40 | 
| *Discrete Diffusion* |  | 
| Multinomial Diffusion | ≤ 1.72 | 
| D3PM Uniform | ≤ 1.61 | 
| D3PM Absorb | ≤ 1.45 | 
| SEDD Absorb | ≤ 1.39 | 
| MDLM | ≤ 1.40 | 
| MD4 | ≤ 1.37 | 
| *Continuous Diffusion* |  | 
| Plaid | ≤ 1.48 | 
| BFN | ≤ 1.41 | 
| RDLM (Ours) | ≤ **1.32** |{{< /table-caption >}}

> 🔼 표 1은 Text8 테스트 세트에 대한 비트당 문자 수(BPC) 결과를 보여줍니다.  각 모델의 성능을 비교하기 위해 해당 논문에서 발췌한 결과를 제시하고 있습니다.  자동 회귀 모델과 확산 모델 중 가장 좋은 성능을 보이는 결과는 굵게 표시되어 있습니다.  자세히 살펴보면, 다양한 유형의 언어 모델링 접근 방식 (자동 회귀 모델, 다양한 확산 모델, 그리고 흐름 기반 모델)의 성능을 비교 분석하여 제시하고 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1:  Bits Per Character (BPC) results on Text8 test set. Results are taken from the corresponding papers. Bold denotes the best result in autoregressive or diffusion models.
> </details>





### In-depth insights


#### Discrete Diffusion
본 논문에서 다룬 ‘이산 확산(Discrete Diffusion)’은 이산적인 데이터, 특히 텍스트나 이미지와 같은 범주형 데이터를 모델링하기 위한 확산 모델의 한 유형입니다. **기존의 연속 확산 모델과 달리, 이산 확산 모델은 데이터의 이산적인 특성을 직접적으로 고려하여 설계됩니다.**  이산 확산 모델은 마르코프 체인을 이용하여 이산 상태 간의 전이를 모델링하는데, 이는 데이터 공간에서의 확률적 샘플링을 통해 이루어집니다.  **전이 과정에서 확률적 노이즈가 추가되어 데이터를 점진적으로 왜곡시키고, 이를 역전시켜 원본 데이터를 생성하는 것이 핵심 아이디어입니다.**  하지만 이산 확산 모델은 반복적인 개선 과정에서 신호 손실이 발생하고, 연속 확산 모델에 비해 성능이 제한적일 수 있다는 단점이 있습니다.  논문에서는 이러한 문제를 해결하기 위해 **이산 확산과 연속 확산 사이의 연관성을 규명하고, 이를 바탕으로 새로운 연속 확산 모델을 제안합니다.** 이는 이산 확산의 장점과 연속 확산의 강점을 결합하여 데이터 모델링의 효율성과 성능을 향상시키는 데 기여할 것으로 기대됩니다.  **특히, 통계적 다양체의 기하학적 구조를 활용하여 연속 확산 과정을 설계함으로써, 이산 확산 모델의 한계를 극복하고 더 나은 성능을 달성하고자 하는 시도가 돋보입니다.**

#### Manifold Geometry
본 논문에서 다루는 다양체 기하학은 이산 범주형 데이터의 기저 확률 분포를 효과적으로 모델링하기 위한 핵심 개념입니다. **연구는 이산 확률 분포의 통계적 다양체를 연속적인 공간으로 매핑하여, 기존의 이산 확률 모델의 한계를 극복**합니다. 이는 연속 확산 모델이 가진 반복적인 개선 과정을 이산 데이터에도 적용 가능하게 합니다. 특히, **Fisher-Rao 메트릭을 사용하여 통계적 다양체 위에서의 기하학적 구조를 정의**함으로써, 데이터 점 간의 거리와 연관성을 보다 정확하게 파악할 수 있습니다. 이러한 기하학적 정보는 확산 과정을 설계하고 학습하는 데 중요한 역할을 하여, **모델의 생성 성능과 제어 가능성을 향상**시킵니다. 즉, 단순히 데이터를 벡터로 표현하는 것이 아니라, 데이터의 근본적인 기하학적 특성을 고려함으로써, 보다 정교하고 효율적인 생성 모델을 구축하는 것입니다. **초구면(hypersphere)을 이용한 매핑**을 통해 고차원 다양체의 복잡성을 해결하고, 효율적인 계산과 학습을 가능하게 합니다.  **RDLM 모델의 핵심적인 강점** 중 하나는 바로 이러한 다양체 기하학에 대한 심도 있는 이해와 활용입니다. 

#### RDLM Framework
RDLM 프레임워크는 이산 범주형 데이터에 대한 지속적인 확산 모델링을 위한 새로운 접근 방식을 제시합니다. **기존의 이산 확산 모델들은 반복적인 개선의 힘을 충분히 활용하지 못하고, 이산 상태 간의 전이 과정에서 신호 손실이 발생하는 한계**를 지닙니다.  RDLM은 통계적 다양체의 기하학적 구조를 통합하여 이러한 문제를 해결하고자 합니다.  **이산 확산과 연속 흐름 간의 연결을 확립하여, 이산 확산 모델을 일반화하는 단순한 확산 프로세스 설계**를 제안합니다.  **방사형 대칭성을 기반으로 한 시뮬레이션이 필요 없는 학습 프레임워크**를 통해 고차원 다양체의 문제를 해결합니다.  **기존의 이산 확산 모델들을 능가하고, 자기 회귀 모델의 성능에 근접하는 결과**를 보여주는 등 언어 모델링을 위한 강력한 프레임워크임을 실험적으로 입증하였습니다.  **특히, 다양한 모달리티에 대한 실험을 통해 범용성을 보여주는 것이 핵심**입니다.

#### Simul-Free Training
본 논문에서 제시된 'Simul-Free Training' 개념은 **계산 비용이 많이 드는 기존의 시뮬레이션 기반 훈련 방식을 극복하기 위한 핵심 전략**입니다.  기존의 확률적 미분 방정식(SDE) 기반 확산 모델 훈련은 매 반복마다 복잡한 확산 과정을 시뮬레이션해야 했으나, 이는 고차원 데이터 공간에서는 매우 계산적으로 비효율적입니다. 이를 해결하기 위해, **본 연구는 훈련 과정에서 시뮬레이션을 제거하는 방법론을 제시**합니다. 이는 **radial symmetry (방사형 대칭성)**을 이용해 단순화된 파라미터화와 최대 우도 기반 훈련 목표를 통합하여 구현됩니다. 이러한 방식은 고차원 다양체에서의 복잡한 계산을 피하면서 효율적인 훈련을 가능하게 합니다. 특히 **radial symmetry 기반의 simple parameterization**을 통해 계산 복잡도를 낮추고, **simulation-free training scheme**을 구현함으로써, 기존 방법보다 훨씬 빠르고 효율적인 훈련이 가능해집니다.  결과적으로,  **계산 효율성의 증대**뿐 아니라,  **대규모 어휘 집합을 가진 언어 모델의 훈련에도 적용 가능**하다는 점에서 중요한 의의를 지닙니다.  **고차원 데이터에 대한 효과적인 훈련 방법**을 제공하여, 확산 모델의 실용성을 크게 향상시키는 데 기여할 수 있습니다. 

#### Future Extensions
본 논문에서 제시된 리만 확산 언어 모델(RDLM)은 **자연어 처리 분야에서 새로운 가능성을 열었지만**, 아직 해결해야 할 과제와 더욱 발전시킬 여지가 많습니다. **미래 확장 방향**으로는 첫째, **모델의 매개변수를 대폭 확장**하여 더욱 복잡하고 정교한 언어 모델을 구축하는 것입니다. 현재 모델은 비교적 작은 크기의 매개변수를 사용하지만, 대규모 언어 모델(LLM)과 같이 거대한 매개변수를 사용하는 모델이 더욱 향상된 성능을 보일 가능성이 있습니다. 둘째, **자기회귀적(autoregressive) 특성을 모델에 통합**하여 더욱 효율적이고 제어 가능한 텍스트 생성을 가능하게 하는 것입니다. 현재 모델은 병렬적으로 텍스트를 생성하지만, 자기회귀적 접근 방식을 결합하면 더욱 일관성 있고 자연스러운 텍스트 생성이 가능할 것으로 예상됩니다. 셋째, **다양한 모달리티(modality)로의 확장**입니다. 본 논문에서는 자연어 처리에 집중했지만, 이미지, DNA 서열 등 다른 유형의 데이터에도 적용 가능성을 보였습니다. 앞으로 **이미지 생성, 생물학적 서열 디자인 등 다양한 분야**로의 확장 연구가 필요합니다. 마지막으로, **모델의 안정성과 일반화 성능을 개선**하기 위한 연구가 중요합니다. 현재 모델은 특정 데이터셋에 대해서는 좋은 성능을 보이지만, 다른 데이터셋으로의 일반화 능력은 아직 부족합니다. 따라서, **데이터 증강, 정규화 기법 등을 활용**하여 모델의 안정성과 일반화 성능을 개선하는 연구가 필요합니다.


### More visual insights




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | # Param. | PPL (<img src="https://arxiv.org/html/2502.11564/downarrow.png" alt="↓" />) |
|---|---|---:|
| *Autoregressive* |  |  |
| Transformer-X Base | 0.46B | 23.5 |
| <math>\text{OmniNet}_{T}</math> | 100M | 21.5 |
| Transformer | 110M | 22.32 |
| *Discrete Diffusion* |  |  |
| BERT-Mouth | 110M | ≤ 142.89 |
| D3PM Absorb | 70M | ≤ 76.90 |
| DiffusionBert | 110M | ≤ 63.78 |
| SEDD | 110M | ≤ 32.79 |
| MDLM | 110M | ≤ 27.04 |
| *Continuous Diffusion* |  |  |
| Diffusion-LM | 80M | ≤ 118.62 |
| RDLM (Ours) | 110M | ≤ 29.72 |{{< /table-caption >}}
> 🔼 표 2는 LM1B 데이터셋을 사용한 언어 모델링 작업에서 테스트 당황도(PPL) 결과를 보여줍니다.  Sahoo 외 (2024)의 연구 결과를 기준선으로 사용하여 여러 가지 자기회귀 및 확산 모델의 성능을 비교합니다. 표에는 각 모델의 이름, 매개변수 수, 그리고 PPL 점수가 포함되어 있습니다. PPL 점수가 낮을수록 모델의 성능이 좋음을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 2:  Test perplexity (PPL) results on LM1B dataset. Baseline results are taken from Sahoo et al. (2024).
> </details>

{{< table-caption >}}
| Method | # Param. | BPD (<span>↓</span>) |
|---|---|---:|
| *Autoregressive* |  |  |
| PixelRNN |  | 3.00 |
| Gated PixelCNN |  | 3.03 |
| PixelCNN++ | 53M | 2.92 |
| PixelSNAIL | 46M | 2.85 |
| Image Transformer |  | 2.90 |
| Sparse Transformer | 59M | 2.80 |
| *Discrete Diffusion* |  |  |
| D3PM Absorb | 37M | ≤ 4.40 |
| D3PM Gauss | 36M | ≤ 3.44 |
| <span>τ</span>LDR | 36M | ≤ 3.59 |
| MD4 | 28M | ≤ 2.78 |
| *Continuous Diffusion* |  |  |
| RDLM (Ours) | 35M | ≤ **2.74** |{{< /table-caption >}}
> 🔼 표 3은 CIFAR-10 데이터셋에서의 비트당 차원(BPD) 결과를 보여줍니다.  이 표는 다양한 오토인코더 모델들의 성능을 비교하여 제시합니다.  특히, 본 논문에서 제안하는 RDLM 모델의 성능을 기준으로, 기존의 다양한 오토인코더 모델(자동 회귀 모델, 이산 확산 모델, 연속 확산 모델 등)들과의 성능 비교를 통해 RDLM의 우수성을 보여주는 데 초점을 맞추고 있습니다.  기준 성능(Baseline)은 Shi et al.(2024) 논문의 결과를 사용했습니다.
> <details>
> <summary>read the caption</summary>
> Table 3:  Bits Per Dimension (BPD) results on CIFAR-10 dataset. Baseline results are taken from Shi et al. (2024).
> </details>

{{< table-caption >}}
| Method | MSE (<img src="https://arxiv.org/html/2502.11564/downarrow.png" alt="↓"/>) |
|---|---| 
| Bit-Diffusion (bit) | 0.041 |
| Bit-Diffusion (one-hot) | 0.040 |
| D3PM Uniform | 0.038 |
| DDSM | 0.033 |
| DirichletFM | 0.034 |
| Language Model | 0.034 |
| Fisher-Flow | 0.029 |
| RDLM (Ours) | **0.027** |{{< /table-caption >}}
> 🔼 표 4는 생성된 프로모터 DNA 서열에 대한 평균 제곱 오차(MSE) 결과를 보여줍니다.  Davis et al.(2024)의 기준 결과와 비교하여 RDLM 모델의 성능을 평가합니다.  MSE는 생성된 DNA 서열의 규제 활성과 실제 규제 활성 간의 차이를 측정한 지표입니다.  낮은 MSE 값은 생성된 서열이 실제 서열과 유사하고, 따라서 모델의 성능이 우수함을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 4:  MSE results on the generated promoter DNA sequences. Baseline results are taken from Davis et al. (2024).
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