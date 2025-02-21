---
title: "Noise May Contain Transferable Knowledge: Understanding Semi-supervised Heterogeneous Domain Adaptation from an Empirical Perspective"
summary: "소음 데이터에도 전이 가능한 지식이 존재하며, SHDA에서 전이 학습의 핵심은 소스 도메인의 전이성과 판별력임을 밝힌 연구."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Machine Learning", "Transfer Learning", "🏢 Beijing Teleinfo Technology Company Ltd.",]
showSummary: true
date: 2025-02-19
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.13573 {{< /keyword >}}
{{< keyword icon="writer" >}} Yuan Yao et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-20 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.13573" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.13573" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/noise-may-contain-transferable-knowledge" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 반지도 학습 비균질 도메인 적응(SHDA) 연구는 소스 도메인과 타겟 도메인 간의 특징 표현과 분포의 차이로 인해 전이 학습의 본질이 불분명했습니다. 특히, 소스 도메인의 샘플들이 어떤 지식을 전이하는지에 대한 이해가 부족했습니다. 이러한 문제를 해결하기 위해, 본 연구에서는 330개가 넘는 SHDA 과제에 대한 광범위한 실험을 수행했습니다.  

본 연구는 소스 샘플의 범주 및 특징 정보가 타겟 도메인의 성능에 미치는 영향을 분석하고, 소음 데이터에서도 전이 가능한 지식이 존재함을 밝혔습니다. **이를 바탕으로, 통합 지식 전달 프레임워크(KTF)를 설계하여 SHDA에서의 전이 가능한 지식의 원리를 규명했습니다.** 연구 결과, SHDA의 전이 가능한 지식은 주로 소스 도메인의 전이성과 판별력에 기인하며, 소스 샘플의 기원에 관계없이 이러한 특성을 유지하면 SHDA 과제에서의 지식 전달 효율성을 높일 수 있음을 보여주었습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 소스 샘플의 범주 및 특징 정보는 SHDA의 타겟 도메인 성능에 큰 영향을 미치지 않음 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 단순 분포에서 추출된 소음 데이터는 전이 가능한 지식을 포함할 수 있음 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} SHDA의 전이 학습은 소스 도메인의 전이성 및 판별력에 크게 의존함 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**본 논문은 반지도 학습 비균질 도메인 적응(SHDA) 분야에서 전이 학습의 본질에 대한 실증적 연구를 제시하여, 소음 데이터도 전이 가능한 지식을 포함할 수 있음을 보여줍니다.** 이는 기존의 전이 학습 연구에 새로운 관점을 제시하며, 소음 데이터 활용, 전이 학습 효율성 증대, SHDA 알고리즘 개선 등 다양한 연구 분야에 중요한 시사점을 제공합니다. 특히, **데이터 부족 문제 해결 및 다양한 도메인 적응 문제 해결에 크게 기여할 수 있으며, 미래 연구 방향을 제시하는데 중요한 역할을 합니다.**

------
#### Visual Insights



![](https://arxiv.org/html/2502.13573/x1.png)

> 🔼 이 그림은 본 논문에서 다루는 반지도 학습 비균질 도메인 적응(SHDA)의 예시 시나리오를 보여줍니다. 텍스트 기반의 소스 도메인과 이미지 기반의 타겟 도메인 간의 적응을 보여주는 것으로, 소스 도메인의 모든 텍스트 데이터는 레이블이 지정되어 있지만 타겟 도메인의 이미지 데이터는 일부만 레이블이 지정되어 있고 대부분은 레이블이 없는 상태입니다. 또한 소스 도메인과 타겟 도메인 간에는 일대일 대응 관계가 없다는 점을 강조합니다.  결론적으로 이 그림은 SHDA의 특징과 비균질 도메인 간 지식 전달의 불확실성을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Example scenario of SHDA with a textual source domain and a visual target domain. Here, all texts are labeled, but most images remain unlabeled, with only a small number having labels. Also, there is no one-to-one relationship between texts and images. We do not know what knowledge is transferred across heterogeneous domains.
> </details>





{{< table-caption >}}
| Notation | Description |
|---|---| 
| \mathcal{X}_{s} \/ \mathcal{X}_{t} | Source/Target feature space |
| \mathcal{D}_{s} \/ \mathcal{D}_{t} | Source/Target domain |
| \mathcal{D}_{l} \/ \mathcal{D}_{u} | Labeled/Unlabeled target domain |
| \mathbf{x}_{i}^{s} \/ \mathbf{x}_{i}^{l} \/ \mathbf{x}_{i}^{u} | the $i$-th sample in $\mathcal{D}_{s}$ / $\mathcal{D}_{l}$ / $\mathcal{D}_{u}$ |
| \mathbf{y}_{i}^{s} \/ \mathbf{y}_{i}^{l}| One-hot label of $\mathbf{x}_{i}^{s}$ / $\mathbf{x}_{i}^{l}$ |
| $n_{s} \/ n_{l} \/ n_{u}$ | Number of samples in $\mathcal{D}_{s}$ / $\mathcal{D}_{l}$ / $\mathcal{D}_{u}$ |
| C | Number of categories |{{< /table-caption >}}

> 🔼 본 논문의 표 1은 SHDA(Semi-supervised Heterogeneous Domain Adaptation)에 사용되는 주요 변수들을 정의하고 약어를 설명합니다.  출처 도메인과 타겟 도메인의 특징 공간, 도메인 자체, 타겟 도메인의 레이블링 여부, 샘플 수, 카테고리 수 등 SHDA 알고리즘 이해에 필수적인 기호들을 명확하게 정의하여 후속 설명의 이해도를 높입니다.
> <details>
> <summary>read the caption</summary>
> TABLE I: Notations.
> </details>





### In-depth insights


#### SHDA's Transferable Knowledge
본 논문은 **SHDA(Semi-supervised Heterogeneous Domain Adaptation)**에서 지식 전이에 대한 중요한 통찰력을 제공합니다.  기존 연구와 달리, 소스 도메인의 카테고리 및 특징 정보가 타겟 도메인 성능에 미치는 영향이 미미함을 실험적으로 증명합니다. 놀랍게도, **단순 분포에서 추출된 노이즈조차도 전이 가능한 지식을 포함**할 수 있음을 보여줍니다. 이는 **소스 도메인의 전이성 및 판별력이 SHDA에서 지식 전이의 핵심**임을 시사합니다.  소스 샘플의 기원(이미지, 텍스트, 노이즈 등)에 관계없이, 이러한 특성을 보장하면 SHDA에서 지식 전이 효율성을 높일 수 있습니다.  결론적으로, **노이즈 기반 SHDA 접근 방식은 소스 데이터 접근성 제약이 있는 실제 응용 분야에 유용한 대안**이 될 수 있다는 것을 제시합니다.

#### Noise as Source Data
본 논문에서 '잡음을 소스 데이터로 사용'에 대한 핵심적인 아이디어는 **소스 도메인의 샘플이 가지는 특징 정보(범주, 특징)가 타겟 도메인의 성능에 큰 영향을 미치지 않는다는 경험적 관찰**에서 비롯됩니다. 이는 직관적으로 반하는 주장이지만, 다양한 SHDA 작업에 대한 광범위한 실험 결과를 통해 뒷받침됩니다.  **단순한 분포에서 생성된 잡음조차도 전이 가능한 지식을 포함하고 있을 수 있으며, 이는 잡음을 소스 데이터로 활용하여 타겟 도메인의 성능을 향상시킬 수 있다는 것을 의미합니다.**  이러한 발견은 기존의 SHDA 방법론에 대한 새로운 시각을 제공하며, **소스 샘플의 기원에 관계없이 (이미지, 텍스트, 잡음 등) 전이성과 판별력을 보장하는 것이 SHDA에서 효과적인 지식 전이를 위해 중요**함을 시사합니다.  이 연구는 **잡음 기반 SHDA**에 대한 심도있는 실험을 통해 이러한 주장을 뒷받침하며, 소스 도메인의 전이성과 판별력이 타겟 도메인의 성능 개선에 중요한 역할을 한다는 점을 보여줍니다.  **결론적으로, 이 연구는 잡음이라는 예상치 못한 데이터 소스를 통해 SHDA에 대한 새로운 이해를 제공하고, 제한된 데이터 환경에서의 도메인 적응 문제를 해결하기 위한 새로운 가능성을 제시합니다.**

#### KTF Framework Analysis
본 논문에서 제시된 KTF(Knowledge Transfer Framework) 분석은 **소스 도메인의 전달력과 판별력이 타겟 도메인 성능에 미치는 영향을 규명**하는 데 중점을 둡니다.  **소스 샘플의 카테고리 및 특징 정보는 타겟 도메인 성능에 큰 영향을 미치지 않는다는 경험적 발견**에 기반하여, 다양한 노이즈 데이터를 소스 샘플로 사용하는 실험을 통해 전달력과 판별력의 중요성을 검증합니다.  **KTF는 소스 노이즈의 판별력(Ls), 전달력(Ls,t), 타겟 샘플의 판별력(Li)을 통합하여 최적화**함으로써, 소스 도메인의 특성이 타겟 도메인 성능 향상에 어떻게 기여하는지 분석합니다.  **스피어만 상관 계수 분석을 통해 소스 도메인의 판별력과 전달력이 타겟 도메인 성능 향상과 강한 음의 상관관계를 갖는다는 것을 확인**하여, 소스 도메인의 질적 특성이 중요함을 시사합니다.  결과적으로, KTF 분석은 SHDA(Semi-Supervised Heterogeneous Domain Adaptation)에서의 **지식 전달 메커니즘에 대한 심층적인 이해를 제공**하고, 소스 샘플의 기원에 관계없이 **전달력과 판별력을 확보하는 것이 효과적인 지식 전달의 핵심**임을 강조합니다.

#### SHDA Method Comparison
이 논문은 다양한 반(半)-지도 학습 비균질 도메인 적응(SHDA) 방법들을 비교 분석하는 데 중점을 둡니다. **실험 결과는 소스 샘플의 카테고리 및 특징 정보가 타겟 도메인 성능에 미치는 영향이 크지 않다는 것을 보여줍니다.**  놀랍게도, 간단한 분포에서 추출된 잡음조차도 전이 가능한 지식을 포함할 수 있습니다.  **본 연구는 SHDA에서 전이 가능한 지식의 핵심이 소스 도메인의 전이성과 판별력에 있음을 보여줍니다.**  소스 샘플의 기원에 관계없이(예: 이미지, 텍스트, 잡음), 이러한 특성을 유지하는 것이 SHDA 작업에서 지식 전이의 효율성을 높이는 데 중요합니다.  **통합 지식 전달 프레임워크(KTF)를 통해 소스 잡음의 판별력과 전이성이 타겟 도메인 성능 향상과 강한 상관관계를 가짐을 확인했습니다.**  **잡음 기반 SHDA 작업을 통해 소스 샘플로 잡음을 사용하는 것이 타겟 도메인 성능에 유의미한 영향을 미치지 않음을 확인했습니다.**  본 연구는 SHDA에서 전이 가능한 지식에 대한 실증적 이해를 제공하고,  **소스 데이터 접근성에 제약이 있는 실제 응용 분야에 유용한 대안을 제시합니다.**

#### Future Research
본 논문은 잡음이 포함된 데이터를 활용한 반지도학습 비균질 도메인 적응(SHDA)에서 전이 지식의 본질을 탐구합니다. **잡음 데이터가 전이 가능한 지식을 포함할 수 있다는 놀라운 발견**은 SHDA에 대한 새로운 관점을 제시합니다.  향후 연구는 **잡음 데이터의 특성(분포, 차원, 샘플 수 등)과 전이 성능 간의 관계를 정량적으로 분석**하는 데 초점을 맞춰야 합니다. 또한, **다양한 유형의 잡음 데이터(가우시안 잡음 외)**를 사용하여 SHDA의 로버스트니스를 평가하고, 이를 통해 **잡음 데이터의 최적 생성 및 활용 전략**을 제시하는 연구가 필요합니다.  나아가, **제안된 KTF(Knowledge Transfer Framework)의 일반화 성능을 향상**시키고,  실제 응용 분야에서의 효과를 검증하는 실험이 추가적으로 필요합니다. **다양한 도메인 및 작업에 대한 광범위한 실험**을 통해 본 연구 결과의 일반화 가능성을 더욱 높여야 하며,  **이론적 근거를 마련**하여 SHDA에서 잡음 데이터 활용의 효과를 설명할 수 있는 이론적 모델을 개발하는 것도 중요한 연구 과제입니다.  마지막으로, **개인정보보호 및 저작권 문제 해결**을 위해 잡음 데이터 기반 SHDA 기법의 실용화 방안에 대한 연구가 필요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.13573/x2.png)

> 🔼 그림 2는 NUS-WIDE+ImageNet-8 데이터셋[31, 32]에서의 실험 결과를 보여줍니다. 이 그림은 잡음이 전이 가능한 지식을 포함할 수 있다는 것을 보여줍니다. 'Text → Image'는 일반적인 SHDA 작업이며, 'Noise → Image'는 소스 샘플로 순수 잡음을 사용하는 특수 SHDA 작업입니다.  SVMt와 NNt는 두 가지 지도 학습 방법이고, SHFA, CDLS, DDACL, TNT, STN, SSAN, JMEA는 7가지 SHDA 방법입니다. 이 그래프는 다양한 방법들을 사용하여 잡음을 소스 데이터로 사용했을 때의 성능을 보여주고, 잡음 데이터에도 전이 가능한 지식이 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Experimental results on the NUS-WIDE+ImageNet-8 dataset [31, 32], which demonstrates that noise may contain transferable knowledge. Here, Text →→\rightarrow→ Image is a vanilla SHDA task, whilst Noise →→\rightarrow→ Image is a specialized SHDA task with pure noise as the source sample. In addition, SVMt and NNt are two supervised learning methods, whereas SHFA, CDLS, DDACL, TNT, STN, SSAN, and JMEA are seven SHDA methods.
> </details>



![](https://arxiv.org/html/2502.13573/x3.png)

> 🔼 이 그림은 Semi-supervised Heterogeneous Domain Adaptation (SHDA)의 일반적인 파이프라인을 보여줍니다. SHDA는 서로 다른 특징 표현과 분포를 가진 도메인 간의 학습을 다룹니다. 소스 샘플은 레이블이 지정되어 있지만 대부분의 타겟 샘플은 레이블이 지정되지 않고 일부만 레이블이 지정되어 있습니다. 또한 소스와 타겟 샘플 간에는 일대일 대응 관계가 없습니다.  이 그림에서는 분류 적응 및 분포 정렬 메커니즘을 통합하여 소스와 타겟 피처 프로젝터와 분류기를 함께 학습하는 과정을 보여줍니다.  특히 각 도메인에 고유한 피처 프로젝터가 있다는 점에 유의해야 합니다. 이 파이프라인은 준지도 방식으로, 레이블이 없는 타겟 샘플을 활용하여 학습 효율을 높입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: In general, the SHDA pipeline integrates the classification adaptation and distribution alignment mechanisms to jointly learn the source and target feature projectors, along with the classifier, from scratch in a semi-supervised manner. Notably, the feature projectors are unique to each domain.
> </details>



![](https://arxiv.org/html/2502.13573/x4.png)

> 🔼 이 그림은 출처 도메인과 대상 도메인이 동일한 범주를 가지지만 범주 색인의 순서가 다른, 범주 순열 SHDA 작업을 보여줍니다.  쉽게 말해, 같은 종류의 데이터(예: 고양이, 개)가 있지만,  출처 도메인에서는 특정 순서로 정렬되어 있고, 대상 도메인에서는 다른 순서로 정렬되어 있는 상황을 나타냅니다. 이 그림은 출처 도메인과 대상 도메인 간의 데이터 분포 차이를 시각적으로 보여주어 SHDA의 어려움을 설명하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: An illustration of the category-permutated SHDA task, where source and target samples have identical categories but with different orders of category indices.
> </details>



![](https://arxiv.org/html/2502.13573/x5.png)

> 🔼 그림 5는 세 개의 데이터셋(Office+Caltech-10, Multilingual Reuters Collection, NUS-WIDE+ImageNet-8)에서 소스 및 타겟 샘플의 카테고리 인덱스 순서를 보여줍니다. 타겟 샘플의 카테고리 인덱스 순서는 유지하면서 소스 샘플의 카테고리 인덱스 순서만 변경했습니다. 따라서 소스와 타겟 샘플의 카테고리 인덱스 순서가 모두 1번 순서와 일치할 때만 해당 작업을 일반적인 SHDA 작업으로 간주합니다. 각 데이터셋에 대해 소스 샘플의 카테고리 인덱스 순서를 다르게 배열하여 여러 SHDA 작업을 생성했습니다. 이 그림은 카테고리 정보가 SHDA 성능에 미치는 영향을 분석하는 데 사용되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: The orders of category indices for source and target samples on all datasets. Here, we preserve the order of category indices for target samples while exclusively modifying that of source samples. Consequently, the task is considered as a vanilla SHDA task only when the category indices of both source and target samples are aligned in order 1.
> </details>



![](https://arxiv.org/html/2502.13573/x6.png)

> 🔼 그림은 Office+Caltech-10 데이터셋을 사용한 SHDA(Semi-supervised Heterogeneous Domain Adaptation) 실험 결과를 보여줍니다.  (a)는 Amazon(A) 도메인의 SURF(S800) 특징을 사용하여 Caltech(C) 도메인의 DeCAF(D4096) 특징으로 도메인 적응을 수행한 결과를 나타냅니다.  소스 도메인(A)과 타겟 도메인(C)은 서로 다른 특징 공간을 가지고 있으며, 타겟 도메인에는 소량의 레이블된 데이터와 다량의 레이블되지 않은 데이터가 있습니다. 그림은 다양한 SHDA 방법들의 성능을 비교 분석하여, 소스 도메인의 특징 정보가 타겟 도메인 성능에 미치는 영향을 평가합니다. 
> <details>
> <summary>read the caption</summary>
> (a) A (S800subscript𝑆800S_{800}italic_S start_POSTSUBSCRIPT 800 end_POSTSUBSCRIPT) →→\rightarrow→C (D4096subscript𝐷4096D_{4096}italic_D start_POSTSUBSCRIPT 4096 end_POSTSUBSCRIPT)
> </details>



![](https://arxiv.org/html/2502.13573/x7.png)

> 🔼 이 그림은 논문의 실험 설정 중 하나를 보여줍니다.  C 도메인(Caltech-256 데이터셋)의 S800 특징(SURF 특징, 800차원)을 사용하여 W 도메인(Office 데이터셋의 Webcam 이미지)의 D4096 특징(DeCAF6 특징, 4096차원)을 가진 타겟 도메인에서의 성능을 평가합니다.  즉, 서로 다른 특징 공간과 분포를 가진 소스 도메인과 타겟 도메인 간의 지식 전이를 다루는 반(semi)-지도학습 이종 도메인 적응(SHDA) 작업을 수행합니다. 소스 도메인의 데이터는 레이블이 지정되어 있고, 타겟 도메인의 데이터는 일부만 레이블이 지정되어 있습니다. 이 그림은 이종 도메인 적응(SHDA) 문제에 대한 접근방식 중 하나인 얕은 투영 방법(shallow projection approach)을 설명하는 맥락에서 제시됩니다.
> <details>
> <summary>read the caption</summary>
> (b) C (S800subscript𝑆800S_{800}italic_S start_POSTSUBSCRIPT 800 end_POSTSUBSCRIPT) →→\rightarrow→ W (D4096subscript𝐷4096D_{4096}italic_D start_POSTSUBSCRIPT 4096 end_POSTSUBSCRIPT)
> </details>



![](https://arxiv.org/html/2502.13573/x8.png)

> 🔼 그림은 논문의 실험 설정 중 하나를 보여줍니다.  W (S800) 도메인에서 D (D4096) 도메인으로의 영상 분류 도메인 적응 작업을 나타냅니다.  W는 Webcam 도메인, D는 DSLR 도메인을 나타내고, S800과 D4096은 각 도메인에서 사용되는 이미지 특징 벡터의 차원을 나타냅니다.  이 그림은 SHDA(Semi-supervised Heterogeneous Domain Adaptation) 문제에 대한 다양한 실험을 보여주는 여러 그림 중 하나입니다.  즉, 특징 표현이 다른 도메인 간의 전이 학습 문제에 대한 실험 결과를 보여주는 그림의 일부입니다.
> <details>
> <summary>read the caption</summary>
> (c) W (S800subscript𝑆800S_{800}italic_S start_POSTSUBSCRIPT 800 end_POSTSUBSCRIPT) →→\rightarrow→D (D4096subscript𝐷4096D_{4096}italic_D start_POSTSUBSCRIPT 4096 end_POSTSUBSCRIPT)
> </details>



![](https://arxiv.org/html/2502.13573/x9.png)

> 🔼 그림은 본 논문의 실험 결과 중 하나로, 텍스트 데이터를 소스 도메인으로, 이미지 데이터를 타겟 도메인으로 하는 반지도 학습 비균질 도메인 적응(SHDA) 작업을 보여줍니다. 텍스트 데이터는 모두 레이블이 지정되어 있지만, 이미지 데이터는 일부만 레이블이 지정되어 있고 나머지는 레이블이 없다는 점을 보여줍니다.  소스 도메인과 타겟 도메인의 특징 벡터 공간이 다르다는 점을 강조하며, 이러한 비균질적인 데이터 분포에서의 지식 전이 과정을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (d) Text→→\rightarrow→Image
> </details>



![](https://arxiv.org/html/2502.13573/x10.png)

> 🔼 그림 (e)는 본 논문의 IV. 소스 샘플의 범주 및 특징 정보에 대한 연구 섹션에 포함된 그림입니다.  이 그림은 다국어 로이터 수집 데이터셋을 사용한 반감독 비균질 도메인 적응(SHDA) 실험 결과를 보여줍니다.  특히, 소스 도메인으로 영어(E)를, 타겟 도메인으로 스페인어(S)를 사용한 SHDA 작업을 수행한 결과를 나타냅니다. 그림은 각기 다른 소스 샘플의 범주 색인 순서에 따른 분류 정확도를 보여줍니다. 이를 통해 소스 도메인의 범주 정보가 타겟 도메인 성능에 미치는 영향을 실험적으로 분석하고자 합니다.  이 그림은 여러 다른 범주 순서 (order 1부터 order 10까지)에 따른 다양한 SHDA 기법들의 성능을 비교하여 소스 샘플의 범주 정보가 SHDA 성능에 미치는 영향을 평가하는 데 사용됩니다. 
> <details>
> <summary>read the caption</summary>
> (e) E→→\rightarrow→S
> </details>



![](https://arxiv.org/html/2502.13573/x11.png)

> 🔼 그림은 논문의 IV. 소스 샘플의 범주 및 특징 정보 연구 섹션에 속하며, 다국어 로이터 수집 데이터셋을 사용한 SHDA(Semi-supervised Heterogeneous Domain Adaptation) 실험 결과를 보여줍니다.  특히, 소스 도메인(F, 프랑스어)에서 타겟 도메인(S, 스페인어)으로의 지식 전이 과정을 나타냅니다. 이 그림은 소스 샘플의 카테고리 인덱스 순서를 변경했을 때(다른 순서 번호) 타겟 도메인의 성능에 미치는 영향을 분석하기 위한 실험 결과 중 하나입니다.  각 그래프는 다른 SHDA 방법(SVMt, NNt, SHFA, CDLS, DDACL, TNT, STN, SSAN, JMEA)의 정확도를 나타내며, 여러 가지 카테고리 인덱스 순서에 따른 정확도 변화를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (f) F→→\rightarrow→S
> </details>



![](https://arxiv.org/html/2502.13573/x12.png)

> 🔼 그림은 논문의 실험 결과 중 하나로, 독일어(G)에서 스페인어(S)로의 언어 간 도메인 적응(SHDA) 작업을 보여줍니다.  다양한 SHDA 방법들을 사용하여 독일어 데이터를 스페인어 데이터에 적용하는 실험 결과를 나타냅니다.  x축은 소스 샘플의 카테고리 인덱스 순서를, y축은 분류 정확도를 나타냅니다.  이 그림을 통해 소스 샘플의 카테고리 정보가 타겟 도메인의 성능에 미치는 영향을 분석합니다.
> <details>
> <summary>read the caption</summary>
> (g) G→→\rightarrow→S
> </details>



![](https://arxiv.org/html/2502.13573/x13.png)

> 🔼 그림은 논문의 IV. SOURCE SAMPLES의 CATEGORY 및 FEATURE 정보 연구 섹션에 속하며, 이탈리아어(I)에서 스페인어(S)로의 언어 간 도메인 적응(SHDA) 작업을 보여줍니다.  원본 언어(이탈리아어)는 레이블이 지정된 샘플을 가지고 있으며, 대상 언어(스페인어)는 일부 레이블이 지정된 샘플과 많은 레이블이 지정되지 않은 샘플을 가지고 있습니다. 이 그림은 다양한 순서로 소스 샘플의 범주 인덱스를 변경하여 대상 도메인의 성능에 미치는 영향을 보여주는 실험 결과 중 하나의 하위 그림입니다. 
> <details>
> <summary>read the caption</summary>
> (h) I→→\rightarrow→S
> </details>



![](https://arxiv.org/html/2502.13573/x14.png)

> 🔼 이 그림은 소스 샘플의 범주 색인 순서를 다르게 했을 때 분류 정확도의 변화를 보여줍니다. 8개의 데이터 집합에 대해 각각 여러 가지 범주 색인 순서(order)를 적용하여 실험을 진행했으며, 그 결과를 그래프로 나타냈습니다. 각 그래프는 특정 소스 도메인에서 타겟 도메인으로의 전이 작업을 나타내며, 다양한 범주 색인 순서에 따른 분류 정확도의 변화를 보여줍니다. 이를 통해 소스 샘플의 범주 정보가 타겟 도메인의 성능에 미치는 영향을 실험적으로 분석합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Classification accuracies (%) with distinct orders of category indices for source samples.
> </details>



![](https://arxiv.org/html/2502.13573/x15.png)

> 🔼 그림 7은 데이터셋 간의 SHDA 작업의 예시를 보여줍니다. 이 그림에서 소스 샘플과 타겟 샘플은 서로 다른 범주에 속하지만 강제로 동일한 범주 인덱스에 매핑됩니다. 즉, 소스 도메인과 타겟 도메인의 데이터 분포가 다르더라도, 강제로 같은 범주 인덱스를 사용함으로써 도메인 적응(domain adaptation) 문제를 해결하려는 시도를 보여줍니다. 이는 서로 다른 특징 공간을 가진 소스 도메인과 타겟 도메인 간의 지식 전이(knowledge transfer)를 이해하는 데 중요한 개념입니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Example illustration of the cross-dataset SHDA task. Here, source and target samples have different categories but are forcibly mapped to the same category indices.
> </details>



![](https://arxiv.org/html/2502.13573/x16.png)

> 🔼 그림 8(a)는 다양한 특징 정보를 가진 서로 다른 소스 샘플을 사용했을 때 이미지 도메인을 타겟 도메인으로 하는 SHDA 작업에서의 분류 정확도를 보여줍니다.  다양한 소스 도메인(텍스트, A(S800), C(S800), W(S800), A(D4096), C(D4096), W(D4096))에서 얻은 샘플을 사용하여 실험을 수행했으며, 각 소스 도메인의 특징 벡터는 다릅니다. 그 결과는 대부분의 SHDA 방법들이 서로 다른 소스 샘플에 대해 비슷한 성능을 보임을 보여줍니다. 이는 SHDA 방법들이 특정한 소스 샘플의 특징 정보에 크게 의존하지 않고, 소스와 타겟 도메인 간의 분포를 정렬하는 데 중점을 둔다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (a) Target domain: Image
> </details>



![](https://arxiv.org/html/2502.13573/x17.png)

> 🔼 그림은 소스 샘플에 다른 비율의 노이즈를 섞어서 만든 노이즈 주입 SHDA 작업의 결과를 보여줍니다.  (a)는 타겟 도메인으로 이미지를 사용한 경우이고, (b)는 타겟 도메인으로 S 도메인을 사용한 경우입니다.  각 그래프는 서로 다른 머신러닝 기법(SVMt, NNt, SHFA, CDLS, DDACL, TNT, STN, SSAN, JMEA)들의 정확도를 노이즈 비율에 따라 나타냅니다. 이 그림은 노이즈가 소스 샘플로 사용되었을 때, 타겟 도메인 성능에 미치는 영향을 실험적으로 분석한 결과를 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) Target domain: S
> </details>



![](https://arxiv.org/html/2502.13573/x18.png)

> 🔼 그림 8은 서로 다른 특징 정보를 가진 다양한 소스 샘플의 분류 정확도를 보여줍니다.  다양한 데이터셋(텍스트, 이미지, 오피스-캘텍, 다국어 로이터 등)과 특징 표현(SURF, DeCAF 등)을 사용하여 실험을 진행했으며, 각 데이터셋 조합에 대한 분류 정확도를 다양한 SHDA(Semi-supervised Heterogeneous Domain Adaptation) 방법론들을 통해 비교 분석하고 있습니다. 이를 통해 소스 샘플의 특징 정보가 SHDA의 성능에 미치는 영향을 실험적으로 보여줍니다.  특히, 소스 샘플이 이미지, 텍스트 또는 노이즈 등의 다양한 출처에서 나온 경우에도, SHDA 방법론들이 유사한 성능을 보이는지 확인합니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Classification accuracies (%) of different source samples with distinct feature information.
> </details>



![](https://arxiv.org/html/2502.13573/x19.png)

> 🔼 그림 9는 잡음 주입 SHDA 작업의 예시를 보여줍니다. 소스 샘플에 다양한 비율의 잡음이 섞여 있습니다.  잡음이 없는 소스 샘플과 순수한 잡음 샘플의 중간에 위치한 다양한 소스 샘플을 생성하기 위해, 서로 다른 비율의 잡음이 소스 샘플에 주입됩니다. 이는 소스 샘플의 잡음 비율이 SHDA 작업의 성능에 미치는 영향을 실험적으로 분석하기 위한 것입니다.  즉, 소스 데이터의 일부를 잡음으로 대체하여, 잡음이 포함된 데이터를 사용했을 때 SHDA의 성능이 어떻게 달라지는지 확인하기 위한 실험 설계입니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Example illustration of the noise-injection SHDA task. Here, source samples are mixed with distinct ratios of noise.
> </details>



![](https://arxiv.org/html/2502.13573/x20.png)

> 🔼 그림 8(a)는 Office+Caltech-10 데이터셋과 Multilingual Reuters Collection 데이터셋에서 다양한 소스 샘플의 특징 정보에 따른 분류 정확도를 보여줍니다.  'Target domain: Image'는 이미지를 타겟 도메인으로 하는 SHDA 작업을 의미하며, 각 막대는 다른 소스 도메인 (Text, A(S800), C(S800), W(S800), A(D4096), C(D4096), W(D4096))에서 얻은 결과를 나타냅니다.  여기서 서로 다른 소스 도메인의 특징 정보가 타겟 도메인 성능에 미치는 영향을 비교 분석합니다.  각 소스 도메인은 서로 다른 특징 표현을 가지고 있으므로, 이 그림은 다양한 특징 정보를 가진 소스 샘플이 SHDA 작업에서 어떻게 작용하는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (a) Target domain: S
> </details>



![](https://arxiv.org/html/2502.13573/x21.png)

> 🔼 그림은 데이터셋 Office+Caltech-10에서 사용된 두 가지 다른 특징 표현(S800과 D4096) 중 D4096 특징을 사용하는 대상 도메인에서의 분류 정확도를 보여줍니다.  각 그래프는 소스 샘플에 다른 비율의 노이즈를 섞었을 때의 결과를 나타내며, 다양한 기계 학습 방법의 성능을 비교합니다.  노이즈 비율이 증가함에 따라 성능 변화를 관찰하여 노이즈가 소스 샘플로 사용될 때의 전달 가능한 지식에 대한 통찰력을 제공합니다.
> <details>
> <summary>read the caption</summary>
> (b) Target domain: C (D4096subscript𝐷4096D_{4096}italic_D start_POSTSUBSCRIPT 4096 end_POSTSUBSCRIPT)
> </details>



![](https://arxiv.org/html/2502.13573/x22.png)

> 🔼 그림 10은 다양한 비율의 노이즈를 소스 샘플에 주입했을 때의 분류 정확도(%)를 보여줍니다.  소스 샘플에 노이즈를 추가하여 SHDA 작업에 미치는 영향을 실험적으로 분석한 결과입니다.  특히, 노이즈의 비율을 0에서 1까지 0.2씩 증가시키면서,  각 비율에 따른 다양한 SHDA 방법의 성능을 비교 분석합니다. 이를 통해 노이즈가 SHDA의 성능에 미치는 영향을 측정하고, 노이즈가 소스 샘플로 사용될 수 있는지 여부를 확인합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Classification accuracies (%) with different proportions of nosies.
> </details>



![](https://arxiv.org/html/2502.13573/x23.png)

> 🔼 그림 11은 잡음 기반 SHDA 작업의 예시 그림입니다. 이 그림에서는 의미 없는 랜덤 분포에서 생성된 잡음으로 소스 샘플이 구성됩니다. 여기서 타겟 도메인의 범주 색인은 소스 잡음의 각 범주에 무작위로 고유하게 할당됩니다. 즉, 소스 샘플은 의미론적 의미가 없는 랜덤 잡음으로 이루어져 있으며, 타겟 도메인의 클래스 레이블이 소스 잡음에 무작위로 매핑되어 있다는 것을 보여줍니다. 이는 기존의 SHDA 작업과는 달리 소스 도메인에 대한 사전 지식이 없이도 도메인 적응이 가능함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Example illustration of the noise-based SHDA task. Here, source samples consist of noise drawn from a random distribution without any semantic meaning, where the category indices of the target domain are randomly and uniquely assigned to each category of source noise.
> </details>



![](https://arxiv.org/html/2502.13573/x24.png)

> 🔼 그림 8은 서로 다른 특징 정보를 가진 다양한 소스 샘플에 따른 분류 정확도를 보여줍니다. (a)는 타겟 도메인으로 S를 사용한 결과이고, (b)는 타겟 도메인으로 C(D4096)를 사용한 결과입니다. 각 그래프는 다양한 소스 도메인에서 추출된 샘플에 대한 분류 정확도를 보여주는 데, 이는 소스 샘플이 타겟 도메인 성능에 미치는 영향을 평가하기 위한 것입니다.  이 그림은 소스 샘플의 특징 정보가 SHDA의 타겟 도메인 성능에 큰 영향을 미치지 않는다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (a) Target domain: S
> </details>



![](https://arxiv.org/html/2502.13573/x25.png)

> 🔼 그림은 다양한 소스 샘플의 특징 정보를 사용하여 타겟 도메인의 성능에 미치는 영향을 보여줍니다. 특히 (b)는 타겟 도메인으로서 Office+Caltech-10 데이터셋의 Caltech-256 부분에서 추출한 4096차원의 DeCAF6 특징을 사용한 이미지 데이터를 의미합니다. 이 그림은 소스 샘플의 특징이 타겟 도메인의 성능에 미치는 영향이 크지 않다는 것을 보여주는 실험 결과를 시각적으로 제시합니다.
> <details>
> <summary>read the caption</summary>
> (b) Target domain: C (D4096subscript𝐷4096D_{4096}italic_D start_POSTSUBSCRIPT 4096 end_POSTSUBSCRIPT)
> </details>



![](https://arxiv.org/html/2502.13573/x26.png)

> 🔼 그림 12는 서로 다른 평균과 공분산을 가진 다양한 노이즈 영역을 특징으로 하는 분류 정확도(%)를 보여줍니다. 이 그림은 다양한 노이즈 분포에서 생성된 노이즈를 소스 샘플로 사용하여, 목표 도메인의 성능에 미치는 영향을 실험적으로 분석한 결과를 나타냅니다.  평균과 공분산의 변화에도 불구하고, 모든 방법의 성능이 일정하게 유지되는 것을 확인할 수 있습니다. 이는 소스 노이즈의 평균 및 공분산 변화가 목표 도메인의 성능에 큰 영향을 미치지 않음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Classification accuracies (%) with various noise domains characterized by distinct means and covariances.
> </details>



![](https://arxiv.org/html/2502.13573/x27.png)

> 🔼 그림 8(a)는 Office+Caltech-10 및 Multilingual Reuters 데이터셋에서 다양한 소스 샘플을 사용하여 수행한 SHDA 작업의 결과를 보여줍니다.  세로축은 정확도를 나타내고 가로축은 다양한 소스 도메인을 나타냅니다.  각 소스 도메인은 서로 다른 특징 표현(예: Text, A(S800), C(S800), W(S800), A(D4096), C(D4096), W(D4096))을 가지고 있습니다.  이 그림은 소스 샘플의 특징 정보가 타겟 도메인의 성능에 미치는 영향을 분석하기 위한 실험 결과를 보여줍니다.  각 알고리즘의 성능 차이가 크지 않다는 것을 보여줌으로써, 소스 샘플의 특징 정보가 SHDA 성능에 큰 영향을 미치지 않는다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (a) Target domain: S
> </details>



![](https://arxiv.org/html/2502.13573/x28.png)

> 🔼 그림은 SHDA(Semi-supervised Heterogeneous Domain Adaptation)에서 소스 샘플에 다른 비율의 노이즈를 섞었을 때, 타겟 도메인의 성능에 미치는 영향을 보여줍니다.  (b)는 타겟 도메인으로 Caltech-256 데이터셋의 4096차원 DeCAF6 특징을 사용한 경우의 결과를 나타냅니다.  다양한 노이즈 비율에서 여러 SHDA 방법들의 정확도를 비교 분석하여, 노이즈가 소스 샘플로 사용될 때의 전달 가능한 지식에 대한 통찰력을 제공합니다.
> <details>
> <summary>read the caption</summary>
> (b) Target domain: C (D4096subscript𝐷4096D_{4096}italic_D start_POSTSUBSCRIPT 4096 end_POSTSUBSCRIPT)
> </details>



![](https://arxiv.org/html/2502.13573/x29.png)

> 🔼 그림 13은 서로 다른 샘플 수를 가진 다양한 노이즈 도메인을 특징으로 하는 분류 정확도(%)를 보여줍니다. 이 그림은 소스 샘플에 다양한 수의 노이즈를 주입했을 때, 타겟 도메인의 성능에 미치는 영향을 실험적으로 분석한 결과를 나타냅니다. 각 노이즈 도메인은 고유한 가우시안 혼합 분포에서 샘플링되며, 각 분포는 카테고리당 다양한 수의 노이즈를 포함합니다. 샘플 수는 각 노이즈 도메인에서 카테고리별로 300에서 700까지 100씩 증가합니다. 노이즈의 차원은 모든 노이즈 도메인에서 300으로 일관되게 유지됩니다. 실험 결과, 다양한 수의 노이즈가 타겟 도메인의 성능에 큰 영향을 미치지 않는다는 것을 보여줍니다. 이는 노이즈의 양이 SHDA에서의 지식 전달에 중요한 영향을 미치지 않음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: Classification accuracies (%) with different noise domains characterized by distinct sample numbers.
> </details>



![](https://arxiv.org/html/2502.13573/x30.png)

> 🔼 그림 8은 서로 다른 특징 정보를 가진 여러 소스 샘플에 대한 분류 정확도를 보여줍니다. (a)는 대상 도메인이 S일 때, (b)는 대상 도메인이 C(D4096)일 때의 결과를 나타냅니다.  각 그래프는 다양한 소스 샘플 유형에 따른 여러 SHDA 방법들의 성능을 비교 분석한 결과를 보여줍니다.  다양한 소스 데이터(텍스트, 이미지, 다양한 특징을 가진 이미지)를 사용하여 대상 도메인의 성능에 미치는 영향을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (a) Target domain: S
> </details>



![](https://arxiv.org/html/2502.13573/x31.png)

> 🔼 그림은 다양한 소스 샘플의 특징 정보가 SHDA(Semi-supervised Heterogeneous Domain Adaptation) 작업에서 타겟 도메인 성능에 미치는 영향을 보여줍니다. 구체적으로, 소스 샘플의 특징으로 SURF(Speeded-Up Robust Features) 800차원(S800)과 DeCAF(Deep Convolutional Activation Features) 4096차원(D4096)을 사용하여 Office+Caltech-10 데이터셋에서 수행한 실험 결과를 보여줍니다. 그림 (b)는 타겟 도메인으로 Caltech-256 데이터셋의 D4096 특징을 사용한 경우를 나타냅니다. 이를 통해 소스 샘플의 특징 정보가 SHDA의 성능에 미치는 영향을 분석하고 있습니다.
> <details>
> <summary>read the caption</summary>
> (b) Target domain: C (D4096subscript𝐷4096D_{4096}italic_D start_POSTSUBSCRIPT 4096 end_POSTSUBSCRIPT)
> </details>



![](https://arxiv.org/html/2502.13573/x32.png)

> 🔼 그림 14는 서로 다른 차원의 특징을 가진 다양한 노이즈 영역을 특징으로 하는 분류 정확도(%)를 보여줍니다. 이 그림은 소스 샘플에 다양한 수준의 노이즈를 주입하여 타겟 도메인의 성능에 미치는 영향을 실험적으로 분석한 결과를 보여줍니다.  세로축은 분류 정확도(%)를 나타내고, 가로축은 각 노이즈 영역의 차원을 나타냅니다.  각 선은 서로 다른 SHDA 방법(SVMt, NNt, SHFA, CDLS, DDACL, TNT, STN, SSAN, JMEA)에 대한 결과를 보여줍니다. 이 실험을 통해 소스 샘플의 차원이 타겟 도메인의 성능에 미치는 영향을 파악하고, 노이즈가 포함된 소스 샘플을 사용하는 SHDA의 효과에 대한 통찰력을 제공합니다.  각 노이즈 도메인은 고유한 가우시안 혼합 분포에서 샘플링됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: Classification accuracies (%) with different noise domains characterized by distinct dimensionalities.
> </details>



![](https://arxiv.org/html/2502.13573/x33.png)

> 🔼 그림 8(a)는 다양한 특징 정보를 가진 서로 다른 소스 샘플을 사용했을 때, 대상 도메인이 S일 경우 분류 정확도를 보여줍니다.  다양한 소스 도메인(텍스트, A(S800), C(S800), W(S800), A(D4096), C(D4096), W(D4096))에서 샘플들을 사용하여 실험을 진행했습니다.  각 막대는 특정 소스 도메인을 사용한 실험 결과를 나타내며, 여러 가지 머신러닝 방법들의 성능을 비교 분석하고 있습니다. 이는 소스 샘플의 특징 정보가 SHDA 작업에서 타겟 도메인의 성능에 미치는 영향을 실험적으로 평가한 것입니다.
> <details>
> <summary>read the caption</summary>
> (a) Target domain: S
> </details>



![](https://arxiv.org/html/2502.13573/x34.png)

> 🔼 그림은 다양한 소스 샘플의 특징 정보를 사용하여 대상 도메인의 성능에 미치는 영향을 보여줍니다. 특히, 소스 샘플이 800차원 SURF 특징과 4096차원 DeCAF6 특징을 가진 Caltech-256 데이터셋에서 나온 경우의 결과를 보여줍니다.  이 그림은 여러 가지 기계 학습 방법을 사용하여, 서로 다른 소스 데이터에서 가져온 소스 샘플이 대상 도메인의 성능에 미치는 영향이 얼마나 되는지 보여줍니다.  각 방법의 정확도를 다양한 설정(소스 도메인의 종류, 소스 샘플의 특징 정보 등)에 따라 비교하여 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) Target domain: C (D4096subscript𝐷4096D_{4096}italic_D start_POSTSUBSCRIPT 4096 end_POSTSUBSCRIPT)
> </details>



![](https://arxiv.org/html/2502.13573/x35.png)

> 🔼 그림 15는 서로 다른 유형의 분포로 특징 지어지는 다양한 노이즈 도메인을 사용하여 얻은 분류 정확도(%)를 보여줍니다. 이 그림은 소스 샘플에 다양한 유형의 노이즈 분포를 주입했을 때 타겟 도메인의 성능에 미치는 영향을 보여주기 위해 수행된 실험 결과를 나타냅니다. 각 노이즈 도메인은 고유한 분포(예: 가우시안, 균일, 라플라스)로부터 샘플링되며, 그 결과 타겟 도메인의 성능에 미치는 노이즈의 영향을 분석하는 데 도움이 됩니다.  구체적으로, 이 그림은 가우시안, 균일 및 라플라스 분포에서 생성된 6개와 10개의 카테고리(각각 S 도메인과 C(D4096) 도메인)를 가진 노이즈 도메인의 결과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 15: Classification accuracies (%) with different noise domains characterized by distinct types of distributions.
> </details>



![](https://arxiv.org/html/2502.13573/x36.png)

> 🔼 그림 8(a)는 다양한 특징 정보를 가진 서로 다른 소스 샘플을 사용했을 때, 대상 도메인이 S일 경우의 분류 정확도를 보여줍니다.  여기서 다양한 소스 도메인(Text, A(S800), C(S800), W(S800), A(D4096), C(D4096), W(D4096))이 사용되었고, 각 소스 샘플의 특징 표현이 서로 다름을 보여줍니다. 이는 다양한 소스 데이터를 사용한 반면, 대상 도메인은 이미지(Image)로 일관되게 유지됨을 의미합니다. 이 그림을 통해 서로 다른 특징 공간의 소스 데이터가 대상 도메인 성능에 미치는 영향을 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (a) Target domain: S
> </details>



![](https://arxiv.org/html/2502.13573/x37.png)

> 🔼 그림 8(b)는 다양한 특징 정보를 가진 서로 다른 소스 샘플을 사용했을 때, 대상 도메인으로 S를 사용하는 경우의 분류 정확도를 보여줍니다.  여러 가지 소스 도메인(Text, A(S800), C(S800), W(S800), A(D4096), C(D4096), W(D4096))에서 나온 샘플이 사용되었고, 각 소스 도메인의 특징이 대상 도메인의 성능에 미치는 영향을 보여줍니다.  이 그래프는 소스 샘플의 특징 정보가 대상 도메인의 성능에 큰 영향을 미치지 않는다는 것을 시사하는 실험 결과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) Target domain: S
> </details>



![](https://arxiv.org/html/2502.13573/x38.png)

> 🔼 그림은  소스 샘플에 다른 비율의 노이즈를 섞어서 만든 여러 SHDA 작업의 결과를 보여줍니다. (c)는 대상 도메인이 Caltech-256 데이터셋의 이미지이고, 이미지 특징은 4096차원 DeCAF6 특징으로 표현됨을 나타냅니다.  이 그래프를 통해 노이즈 비율이 달라져도 대상 도메인 성능에 큰 영향이 없음을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (c) Target domain: C (D4096subscript𝐷4096D_{4096}italic_D start_POSTSUBSCRIPT 4096 end_POSTSUBSCRIPT)
> </details>



![](https://arxiv.org/html/2502.13573/x39.png)

> 🔼 이 그림은 논문의 V. STUDY ON NOISE AS SOURCE SAMPLES 섹션에 속하며, 소스 샘플에 다양한 비율의 노이즈를 주입하여 타겟 도메인의 성능에 미치는 영향을 보여줍니다.  (d)는 타겟 도메인으로 Office-Caltech-10 데이터셋의 Caltech-256 부분에서 4096차원 DeCAF 특징을 사용한 이미지 데이터를 의미합니다.  다양한 노이즈 비율(α)에 따른 여러 머신러닝 기법의 정확도를 비교 분석하여 노이즈가 소스 샘플로 사용될 때의 전달 가능한 지식의 특성을 실험적으로 탐구합니다.
> <details>
> <summary>read the caption</summary>
> (d) Target domain: C (D4096subscript𝐷4096D_{4096}italic_D start_POSTSUBSCRIPT 4096 end_POSTSUBSCRIPT)
> </details>



![](https://arxiv.org/html/2502.13573/x40.png)

> 🔼 그림 16은 소스 도메인의 판별력(ℒs)과 타겟 도메인의 성능 향상 비율(𝒫r) 간의 상관관계, 그리고 소스 도메인의 전이 가능성(ℒs,t)과 타겟 도메인의 성능 향상 비율(𝒫r) 간의 상관관계를 보여줍니다.  ℒs가 클수록(판별력이 높을수록) 𝒫r은 감소하고, ℒs,t가 클수록(전이 가능성이 높을수록) 𝒫r은 감소하는 음의 상관관계가 존재함을 보여줍니다. 즉, 소스 도메인의 판별력과 전이 가능성이 높을수록 타겟 도메인의 성능 향상이 낮아짐을 시각적으로 나타냅니다.  이러한 결과는 소스 도메인의 특징이 타겟 도메인으로 얼마나 잘 전이될 수 있는지, 그리고 소스 도메인 자체의 데이터 질이 타겟 도메인 성능에 얼마나 영향을 주는지를 보여주는 중요한 지표입니다.
> <details>
> <summary>read the caption</summary>
> Figure 16: Correlation between ℒssubscriptℒ𝑠\mathcal{L}_{s}caligraphic_L start_POSTSUBSCRIPT italic_s end_POSTSUBSCRIPT and 𝒫rsubscript𝒫𝑟\mathcal{P}_{r}caligraphic_P start_POSTSUBSCRIPT italic_r end_POSTSUBSCRIPT, as well as between ℒs,tsubscriptℒ𝑠𝑡\mathcal{L}_{s,t}caligraphic_L start_POSTSUBSCRIPT italic_s , italic_t end_POSTSUBSCRIPT and 𝒫rsubscript𝒫𝑟\mathcal{P}_{r}caligraphic_P start_POSTSUBSCRIPT italic_r end_POSTSUBSCRIPT. Here, ℒssubscriptℒ𝑠\mathcal{L}_{s}caligraphic_L start_POSTSUBSCRIPT italic_s end_POSTSUBSCRIPT represents the discriminability of the source domain, ℒs,tsubscriptℒ𝑠𝑡\mathcal{L}_{s,t}caligraphic_L start_POSTSUBSCRIPT italic_s , italic_t end_POSTSUBSCRIPT characterizes the transferability of the source domain, and 𝒫rsubscript𝒫𝑟\mathcal{P}_{r}caligraphic_P start_POSTSUBSCRIPT italic_r end_POSTSUBSCRIPT denotes the performance improvement ratio in the target domain.
> </details>



![](https://arxiv.org/html/2502.13573/x41.png)

> 🔼 이 그림은 논문의 VI. SHDA에서 전이 가능한 지식을 통한 소스 노이즈 연구 섹션에 속하며, N6 → S 과업에서 시간 t=1일 때의 t-SNE 시각화 결과를 보여줍니다. '+'는 소스 샘플, 'x'는 레이블이 지정된 타겟 샘플, 'o'는 레이블이 지정되지 않은 타겟 샘플을 나타냅니다. 각 색상은 서로 다른 범주를 나타내고, 각 점은 데이터 포인트의 2차원 표현을 나타냅니다. 이 시각화는 소스 및 타겟 도메인의 분포 정렬 과정을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (a) N6 →→\rightarrow→ S: t=1𝑡1t=1italic_t = 1
> </details>



![](https://arxiv.org/html/2502.13573/x42.png)

> 🔼 그림 17(b)는 N6에서 S로의 도메인 적응 작업의 t-SNE 시각화를 보여줍니다. 여기서 '+'는 소스 샘플을, '●'는 레이블이 지정된 타겟 샘플을, 'o'는 레이블이 지정되지 않은 타겟 샘플을 나타냅니다. 각 색상은 서로 다른 범주를 나타내고, t는 현재 반복 횟수를 나타냅니다. 이 그림은 소스 도메인이 샘플 분포를 명확하게 분리하고 있음을 보여주며, 타겟 도메인의 분포는 훈련 초기에는 겹치지만 훈련이 진행됨에 따라 소스 도메인과의 정렬이 향상됨을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) N6 →→\rightarrow→ S: t=200𝑡200t=200italic_t = 200
> </details>



![](https://arxiv.org/html/2502.13573/x43.png)

> 🔼 이 그림은 논문의 VI. SHDA에서 전이 가능한 지식을 통한 소스 노이즈 연구 섹션에 포함되어 있습니다. 그림 (c)는 N6 → S 작업에서 400번째 반복의 t-SNE 시각화 결과를 보여줍니다. 여기서 '+' 기호는 소스 샘플, '□' 기호는 레이블이 지정된 타겟 샘플, 'o' 기호는 레이블이 지정되지 않은 타겟 샘플을 나타냅니다. 각 색상은 다른 범주를 나타내며, '+' 기호 옆의 숫자는 현재 반복 횟수를 나타냅니다. 이 시각화는 소스 도메인의 판별력이 높기 때문에, 타겟 도메인의 판별력을 향상시키기 위해 소스 도메인과 타겟 도메인의 분포를 정렬하여 양의 전이가 발생하는 것을 보여줍니다. 소스 도메인의 전이성이 향상됨에 따라 판별력이 타겟 도메인으로 점진적으로 전이되어 타겟 도메인의 성능이 향상됩니다.
> <details>
> <summary>read the caption</summary>
> (c) N6 →→\rightarrow→ S: t=400𝑡400t=400italic_t = 400
> </details>



![](https://arxiv.org/html/2502.13573/x44.png)

> 🔼 그림 (d)는 N6 → S 작업에 대한 t-SNE 시각화를 보여줍니다. 여기서 t는 600번째 반복을 나타냅니다.  '+' 기호는 소스 샘플을, '*' 기호는 라벨이 지정된 타겟 샘플을, 'o' 기호는 라벨이 지정되지 않은 타겟 샘플을 나타냅니다. 각 색상은 고유한 범주에 해당합니다. 이 그림은 소스 도메인의 높은 판별력과 타겟 도메인의 판별력 향상을 통해 소스 도메인에서 타겟 도메인으로의 양의 전이가 발생함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (d) N6 →→\rightarrow→ S: t=600𝑡600t=600italic_t = 600
> </details>



![](https://arxiv.org/html/2502.13573/x45.png)

> 🔼 그림은 N10에서 C(D4096)으로의 도메인 적응 작업에 대한 t-SNE 시각화를 보여줍니다. 여기서 '+'는 소스 샘플을, 'x'는 레이블이 지정된 타겟 샘플을, 'o'는 레이블이 지정되지 않은 타겟 샘플을 나타냅니다. 각 색상은 서로 다른 범주를 나타내며, 't'는 현재 반복 횟수를 나타냅니다. 특히, 이 그림은 반복 횟수가 1일 때의 시각화를 보여줍니다. 소스 샘플은 명확하게 구분되는 반면, 타겟 샘플은 상당한 중복이 있음을 보여줍니다.  이는 초기 단계에서 타겟 도메인의 판별력이 낮음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (e) N10 →→\rightarrow→ C (D4096subscript𝐷4096D_{4096}italic_D start_POSTSUBSCRIPT 4096 end_POSTSUBSCRIPT): t=1𝑡1t=1italic_t = 1
> </details>



![](https://arxiv.org/html/2502.13573/x46.png)

> 🔼 그림은 논문의 V. STUDY ON NOISE AS SOURCE SAMPLES 섹션에 속하며, 다양한 소스 샘플(noise)을 사용한 SHDA(Semi-supervised Heterogeneous Domain Adaptation) 작업의 결과를 보여줍니다. 특히, (f)는 N10 → C(D4096) 작업에서 200번의 반복(iteration) 후의 t-SNE 시각화 결과입니다. 즉, 이미지 특징을 4096차원으로 나타내는 Caltech-256 데이터셋의 10개 카테고리를 대상으로, 랜덤하게 생성된 노이즈 데이터를 소스 샘플로 사용한 SHDA 작업의 결과를 보여줍니다. 200번의 iteration은 모델 학습의 진행 정도를 나타내며, 각 점은 하나의 데이터 샘플을 나타내고 색깔은 샘플의 카테고리를 나타냅니다. 그림을 통해 소스 노이즈와 타겟 샘플의 분포가 어떻게 정렬되는지를 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (f) N10 →→\rightarrow→ C (D4096subscript𝐷4096D_{4096}italic_D start_POSTSUBSCRIPT 4096 end_POSTSUBSCRIPT): t=200𝑡200t=200italic_t = 200
> </details>



![](https://arxiv.org/html/2502.13573/x47.png)

> 🔼 이 그림은 논문의 VI. STUDY ON TRANSFERABLE KNOWLEDGE IN SHDA THROUGH SOURCE NOISE 섹션에 속하며,  소스 노이즈(source noise)를 사용한 SHDA 실험 결과를 보여줍니다.  (g) N10 → C(D4096): t=400 부분은 10개의 범주를 가진 소스 노이즈(N10)를 이미지 데이터셋 C(D4096)의 타겟 도메인에 적용한 결과이며, 학습 과정(t)의 400번째 반복 시점의 t-SNE 시각화 결과입니다. 각 점은 데이터 포인트를 나타내며, 색깔은 범주를 나타냅니다. 이 시각화를 통해 소스 노이즈의 분포와 타겟 도메인 데이터의 분포 정렬 과정을 확인할 수 있습니다.  소스 노이즈의 판별력(discriminability)과 타겟 도메인 데이터의 판별력 향상 과정을 보여주는 시각화 결과입니다.
> <details>
> <summary>read the caption</summary>
> (g) N10 →→\rightarrow→ C (D4096subscript𝐷4096D_{4096}italic_D start_POSTSUBSCRIPT 4096 end_POSTSUBSCRIPT): t=400𝑡400t=400italic_t = 400
> </details>



![](https://arxiv.org/html/2502.13573/x48.png)

> 🔼 이 그림은 논문의 실험 결과를 보여주는 그림 중 하나이며, 특히 소스 도메인으로서 노이즈를 사용했을 때의 결과를 나타냅니다.  (h)는 여러 개의 그림 중 마지막 그림을 의미하며,  'N10 → C(D4096)'는 10개의 카테고리를 가진 노이즈 데이터를 소스 도메인으로, D4096 특징을 가진 Caltech-256 데이터셋의 이미지를 타겟 도메인으로 사용한 SHDA 태스크를 의미합니다. 't=600'은 모델 학습의 반복 횟수가 600회임을 나타냅니다.  전체적으로 이 그림은 다양한 소스 도메인(여기서는 노이즈)을 사용하여 타겟 도메인의 성능을 향상시키는 SHDA 방법의 효과를 시각적으로 보여주는 부분입니다. t-SNE 기법을 사용하여 특징 공간에서 소스와 타겟 데이터의 분포를 시각화하고 있습니다.
> <details>
> <summary>read the caption</summary>
> (h) N10 →→\rightarrow→ C (D4096subscript𝐷4096D_{4096}italic_D start_POSTSUBSCRIPT 4096 end_POSTSUBSCRIPT): t=600𝑡600t=600italic_t = 600
> </details>



![](https://arxiv.org/html/2502.13573/x49.png)

> 🔼 그림 17은 N6→S와 N10→C(D4096) 작업에 대한 t-SNE 시각화를 보여줍니다. '+' 기호는 소스 샘플을 나타내고, '∙' 기호는 레이블이 지정된 타겟 샘플을 나타내며, '∘' 기호는 레이블이 지정되지 않은 타겟 샘플을 나타냅니다. 각 색상은 고유한 범주에 해당하며, t는 현재 반복 횟수입니다. 이 그림은 소스 도메인과 타겟 도메인 간의 특징 분포가 반복 횟수에 따라 어떻게 변하는지를 시각적으로 보여줍니다. 특히, 초기에는 소스 샘플이 명확하게 분리되어 있지만, 타겟 샘플은 겹쳐져 구분이 어렵습니다. 그러나 반복이 진행됨에 따라 타겟 샘플도 명확하게 분리되면서 소스 도메인과 타겟 도메인 간의 특징 분포가 점차 정렬되는 것을 확인할 수 있습니다. 이는 소스 도메인의 판별력이 타겟 도메인으로 전이되는 과정을 시각적으로 보여주는 것입니다.
> <details>
> <summary>read the caption</summary>
> Figure 17: t-SNE visualization on the tasks of N6 →→\rightarrow→ S and N10 →→\rightarrow→ C (D4096subscript𝐷4096D_{4096}italic_D start_POSTSUBSCRIPT 4096 end_POSTSUBSCRIPT). Here, the ‘+’ sign denotes a source sample, the ‘∙∙\bullet∙’ sign represents a labeled target sample, and the ‘∘\circ∘’ sign stands for an unlabeled target sample. Each color corresponds to a distinct category, and t𝑡titalic_t is the current number of iterations.
> </details>



![](https://arxiv.org/html/2502.13573/x50.png)

> 🔼 그림은 N6에서 S로의 도메인 적응 작업에 대한 t-SNE 시각화를 보여줍니다. 여기서 t는 현재 반복 횟수를 나타내고, 각 색상은 다른 범주를 나타냅니다. '+' 기호는 소스 샘플을, '■' 기호는 레이블이 지정된 타겟 샘플을, 'o' 기호는 레이블이 지정되지 않은 타겟 샘플을 나타냅니다. 그림 (a)는 첫 번째 반복(t=1)에서 소스 샘플과 타겟 샘플의 분포를 보여줍니다. 소스 샘플은 공통 하위 공간에서 잘 분리되어 있지만, 타겟 샘플은 상당한 중복이 있음을 보여줍니다. 이는 타겟 프로젝터와 분류기가 학습 초기 단계에 있기 때문에 타겟 도메인의 판별력이 좋지 않기 때문입니다. 그림 (b)~(d)는 반복 횟수가 증가함에 따라 소스 샘플의 판별력이 유지되고, 서로 다른 범주에 속한 타겟 샘플이 점진적으로 분리되는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (a) N6 →→\rightarrow→ S: t = 1
> </details>



![](https://arxiv.org/html/2502.13573/x51.png)

> 🔼 그림은 논문의 VI. SHDA에서 전이 가능한 지식을 통한 소스 노이즈 연구 섹션에 속하며,  N6 → S 작업에서 200번째 반복 시점의 t-SNE 시각화 결과를 보여줍니다. N6는 6가지 범주를 가진 소스 노이즈를, S는 대상 도메인을 나타냅니다. '+'는 소스 샘플, 'x'는 레이블이 지정된 대상 샘플, 'o'는 레이블이 지정되지 않은 대상 샘플을 나타내고 각 색상은 다른 범주를 나타냅니다. 이 그림은 소스 도메인의 판별력이 높기 때문에 소스 도메인의 전이 가능성이 향상됨에 따라 소스 도메인의 판별력이 대상 도메인으로 점진적으로 전달되어 대상 도메인의 판별력이 향상되는 것을 보여주는 시각적 증거를 제공합니다.
> <details>
> <summary>read the caption</summary>
> (b) N6 →→\rightarrow→ S: t = 200
> </details>



![](https://arxiv.org/html/2502.13573/x52.png)

> 🔼 이 그림은 논문의 VI. STUDY ON TRANSFERABLE KNOWLEDGE IN SHDA THROUGH SOURCE NOISE 섹션에 있는 그림으로,  t-SNE 기법을 사용하여 N6 → S 작업(Noise domain N6에서 Source domain S로의 도메인 적응 작업)에서 400번째 반복 시점의 특징 공간을 시각화한 것입니다.  '+' 기호는 소스 샘플, '*' 기호는 레이블이 지정된 타겟 샘플, 'o' 기호는 레이블이 지정되지 않은 타겟 샘플을 나타내며, 각 색상은 서로 다른 카테고리를 나타냅니다. 이 시각화는 소스 도메인의 차별성(discriminability)과 전달성(transferability)이 타겟 도메인의 성능 향상에 미치는 영향을 보여주는 데 중요한 역할을 합니다. 특히, 소스 샘플이 명확하게 구분되는 반면, 타겟 샘플들은 초기에는 겹쳐 있지만, 반복이 진행됨에 따라 소스 도메인의 특징이 타겟 도메인으로 전달되어 타겟 샘플들의 구분이 명확해지는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (c) N6 →→\rightarrow→ S: t = 400
> </details>



![](https://arxiv.org/html/2502.13573/x53.png)

> 🔼 그림은 N6에서 S로의 도메인 적응 작업에서 t-SNE 시각화를 보여줍니다. 여기서, '+'는 소스 샘플을, '●'는 레이블이 지정된 타겟 샘플을, 'o'는 레이블이 지정되지 않은 타겟 샘플을 나타냅니다. 각 색상은 서로 다른 범주를 나타내며, 't'는 현재 반복 횟수를 나타냅니다. t=600일 때, 소스 노이즈는 공통 하위 공간에서 여전히 구별되며, 타겟 샘플은 점진적으로 분리됩니다. 이는 소스 도메인의 우수한 판별력이 타겟 도메인의 판별력을 높이는 데 기여함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (d) N6 →→\rightarrow→ S: t = 600
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | Type | URL for Code | Publication |
|---|---|---|---| 
| SVMt [33] | Supervised Learning | https://www.csie.ntu.edu.tw/~cjlin/libsvm/ | ACM TIST 2011 |
| NNt [34] | Supervised Learning | https://github.com/tensorflow/tensorflow | OSDI 2016 |
| SHFA [35] | Shallow Projection SHDA | https://github.com/wenli-vision/SHFA_release | TPAMI 2014 |
| CDLS [36] | Shallow Projection SHDA | https://github.com/yaohungt/Cross-Domain-Landmarks-Selection-CDLS-/tree/master | CVPR 2016 |
| DDACL [27] | Shallow Projection SHDA | https://github.com/yyyaoyuan/DDA | Pattern Recognition 2020 |
| TNT [37] | Deep Projection SHDA | https://github.com/wyharveychen/TransferNeuralTrees | ECCV 2016 |
| STN [24] | Deep Projection SHDA | https://github.com/yyyaoyuan/STN | ACM MM 2019 |
| SSAN [29] | Deep Projection SHDA | https://github.com/BIT-DA/SSAN | ACM MM 2020 |
| JMEA [25] | Deep Projection SHDA | https://github.com/fang-zhen/Semi-supervised-Heterogeneous-Domain-Adaptation | TPAMI 2023 |{{< /table-caption >}}
> 🔼 본 논문에서 사용된 기준 모델들을 보여주는 표입니다. 표에는 각 모델의 유형(지도 학습 또는 준지도 비균질 도메인 적응), 코드에 대한 URL, 그리고 출판 정보가 포함되어 있습니다.  SVMt와 NNt는 지도 학습 모델이고, 나머지는 준지도 비균질 도메인 적응 모델입니다. SHFA, CDLS, DDACL은 얕은 투영 기법을 사용하는 반면, TNT, STN, SSAN, JMEA는 심층 투영 기법을 사용합니다.
> <details>
> <summary>read the caption</summary>
> TABLE II: Baselines utilized in the paper.
> </details>

{{< table-caption >}}
| Domain | \frac{1}{C}\sum_{c=1}^{C}\|\bm{\mu}_{c}\|_{2} | \frac{1}{C}\sum_{c=1}^{C}\|\bm{\Sigma}_{c}\|_{F} | 
|---|---|---| 
| **N$^{6}_{1}$** | 12.62 | 105.34 | 
| **N$^{6}_{2}$** | 24.44 | 210.32 | 
| **N$^{6}_{3}$** | 36.16 | 315.39 | 
| **N$^{6}_{4}$** | 46.74 | 420.53 | 
| **N$^{6}_{5}$** | 60.43 | 525.05 | 
| **N$^{10}_{1}$** | 19.45 | 164.80 | 
| **N$^{10}_{2}$** | 38.43 | 330.82 | 
| **N$^{10}_{3}$** | 57.24 | 496.16 | 
| **N$^{10}_{4}$** | 77.02 | 661.60 | 
| **N$^{10}_{5}$** | 95.54 | 824.46 | {{< /table-caption >}}
> 🔼 이 표는 다양한 노이즈 도메인에 대한 평균과 공분산의 노름 통계를 보여줍니다. 각 노이즈 도메인은 서로 다른 평균과 공분산을 가진 여러 개의 가우시안 분포로 구성됩니다. 표에는 각 노이즈 도메인의 카테고리 수(C), 각 카테고리의 평균(𝝁c)과 공분산(𝚺c)의 노름이 포함되어 있습니다. 이 정보는 노이즈 도메인의 특성을 분석하고, 이러한 노이즈 도메인을 사용한 SHDA(Semi-supervised Heterogeneous Domain Adaptation) 작업의 성능에 미치는 영향을 이해하는 데 유용합니다.
> <details>
> <summary>read the caption</summary>
> TABLE III: The statistics of norms of the means and covariances for the noise domains, where C𝐶Citalic_C denotes the total number of categories in each noise domain, and 𝝁csubscript𝝁𝑐\bm{\mu}_{c}bold_italic_μ start_POSTSUBSCRIPT italic_c end_POSTSUBSCRIPT, 𝚺csubscript𝚺𝑐\bm{\Sigma}_{c}bold_Σ start_POSTSUBSCRIPT italic_c end_POSTSUBSCRIPT represent the mean and covariance of category c𝑐citalic_c in each noise domain, respectively.
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
{{< /gallery >}}