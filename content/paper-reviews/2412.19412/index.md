---
title: "MINIMA: Modality Invariant Image Matching"
summary: "MINIMA: 모달리티 불변 이미지 매칭을 위한 통합 프레임워크가 제안되어, 데이터 확장을 통해 다양한 모달리티 간의 성능을 향상시켰습니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Matching", "🏢 Huazhong University of Science and Technology",]
showSummary: true
date: 2024-12-27
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.19412 {{< /keyword >}}
{{< keyword icon="writer" >}} Xingyu Jiang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-16 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.19412" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.19412" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/minima-modality-invariant-image-matching" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 이미지 매칭 연구는 특정 모달리티에 특화되어 일반화 성능이 떨어지고, 데이터 부족으로 인해 성능 향상에 어려움을 겪었습니다.  이 논문에서는 다양한 모달리티(예: RGB, 적외선, 깊이) 간의 이미지 매칭을 위한 통합 프레임워크를 제시합니다.

본 논문에서는 **데이터 확장 엔진**을 통해 다양한 모달리티와 시나리오를 포함하는 대규모 데이터셋을 생성하고, 이를 기반으로 **MINIMA**라는 통합 프레임워크를 학습시켰습니다.  **MD-syn**라는 새로운 종합 데이터셋을 통해 다양한 모달리티 조합에 대한 제로샷 성능을 평가하고, 기존 방법들을 상당히 능가하는 결과를 얻었습니다.  이는 다양한 모달리티 이미지 매칭 연구에 새로운 가능성을 제시합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 다양한 모달리티(RGB, 적외선, 깊이, 이벤트 등) 간의 이미지 매칭을 위한 통합 프레임워크 MINIMA 제안 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 데이터 확장 엔진을 이용한 대규모 다중 모달리티 데이터셋 MD-syn 구축 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 도메인 내 및 제로샷 매칭 작업에서 기존 방식 대비 성능 향상 및 모달리티 특화 방식을 능가하는 성능 달성 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
이 논문은 **다양한 모달리티의 이미지 매칭을 위한 통합 프레임워크**를 제시하여, 기존의 모달리티 특화 방식의 한계를 극복하고 제로샷 성능을 향상시켰다는 점에서 중요합니다.  **데이터 확장 엔진을 통해 대규모의 다중 모달리티 데이터셋을 구축**함으로써, 다양한 영역의 연구자들에게 귀중한 자원을 제공하고, 향후 연구의 새로운 가능성을 제시합니다. **특히, 다양한 모달리티 간의 도메인 격차 문제 해결에 대한 새로운 접근 방식**을 제시하여, 컴퓨터 비전 분야의 발전에 기여할 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.19412/x4.png)

> 🔼 그림 1은 실제 다중 모드 이미지 쌍의 6개 데이터 세트에서 수행된 전체 이미지 매칭 정확도와 효율성을 보여줍니다. 정확도 평가에는 자세 오차(10도) 또는 재투영 오차(10픽셀)의 AUC가 사용되고, 효율성 테스트에는 초당 쌍(Pairs Per Second)이 사용됩니다. 왼쪽 그래프는 대표적인 방법들의 각 데이터 세트에 대한 AUC를 보여주고, 오른쪽 그래프는 다양한 색상으로 스파스, 세미-덴스, 덴스 매칭 파이프라인을 구분하여 평균 성능을 요약합니다.  MINIMA는 별표(★★)로 표시되어 있습니다. 본 논문에서 제안하는 데이터 엔진으로 생성된 합성 다중 모드 데이터를 사용해야만 MINIMA는 실제 다중 모드 장면에 일반화하여 성능을 크게 향상시킬 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Overall Image Matching Accuracy and Efficiency on Six Datasets of Real Cross-modal Image Pairs. AUC of the pose error (@10∘superscript1010^{\circ}10 start_POSTSUPERSCRIPT ∘ end_POSTSUPERSCRIPT) or reprojection error (@10101010px) is used for accuracy evaluation, while Pairs Per Second is used for efficiency test. Left: AUCs on each dataset of representative methods are reported. Right: average performance is summarized, wherein different colors indicate matching pipelines of sparse, semi-dense and dense matching, while our MINIMA is marked as ★★\bigstar★. Only with synthetic multimodal data created by our data engine, MINIMA can generalize to real cross-modal scenes with large improvements.
> </details>





{{< table-caption >}}
| Dataset | #Pairs | # Scene (Type) | #Modality | Match Label |
|---|---|---|---|---|
| *RGB Matching* |  |  |  |  |
| MegaDepth [26] | 40M | 196 (Out.) | 1 | Depth, Pose |
| ScanNet [5] | 230M | 1513 (In.) | 1 | Depth, Pose |
| *Multimodal Matching* |  |  |  |  |
| METU-VisTIR [43] | 2.5K | 6 (Out.) | 2 | Pose |
| M3FD [29] | 4.2K | 15 (Out.) | 2 | Pre-aligned |
| LLVIP [19] | 15K | 26 (Out.) | 2 | Pre-aligned |
| DIODE [53] | 25K | 20 (In. & Out.) | 3 | Pre-aligned |
| MD-syn (ours) | 480M | 196 (Out.) | 7 | Depth, Pose |{{< /table-caption >}}

> 🔼 표 1은 대표적인 데이터셋들을 개괄적으로 보여줍니다. RGB 전용 및 다중 모달 매칭 데이터셋과 제안된 MD-syn 데이터셋을 포함합니다.  데이터셋의 쌍의 수, 장면 유형(실내 또는 실외), 모달 유형 및 매칭 레이블의 형태를 요약하여 보여줍니다.  RGB 전용 데이터셋과 비교하여 다중 모달 데이터셋의 쌍 수, 장면 다양성, 모달 유형 등이 제한적인 이유를 설명합니다. MD-syn 데이터셋이 이러한 한계를 극복하기 위해 제안되었음을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Overview of Representative Datasets. It contains RGB-only and multimodal matching datasets, and our proposed MD-syn. The number (#) of Pairs, Scene (Type: Indoor or Outdoor), Modality type, and the forms of Match Label are summarized.
> </details>





### In-depth insights


#### Cross-Modal Matching
본 논문은 다양한 모달리티(예: RGB, 적외선, 깊이, 이벤트)를 사용하는 이미지 매칭 문제를 다룹니다. **핵심은 모달리티 간 차이를 극복하는 것**이며, 기존 방법들의 한계를 극복하기 위해 **데이터 확장** 전략을 제시합니다. 저렴하지만 풍부한 RGB 데이터를 기반으로 생성 모델을 이용, 다양한 모달리티의 합성 데이터를 생성합니다. 이를 통해 대규모의 다중 모달리티 데이터셋을 구축하고, **모달리티 불변성을 갖는 이미지 매칭 모델**을 학습합니다. 실험 결과는 제안된 방법이 기존의 모달리티 특화 방법보다 우수한 성능을 보이며, 특히 제로샷(zero-shot) 설정에서도 뛰어난 일반화 능력을 보임을 보여줍니다.  **데이터 확장의 중요성**과 **모달리티 불변 모델의 효용성**을 강조하는 연구입니다.  **다양한 실제 환경 데이터셋에 대한 실험**을 통해 일반화 성능을 입증한 점도 중요한 특징입니다.

#### Data Engine Design
본 논문에서 제시된 ‘데이터 엔진 설계’는 **다양한 모달리티의 이미지 매칭을 위한 대규모 데이터셋을 생성**하는 것을 목표로 합니다. 기존의 제한된 크기와 다양성을 가진 데이터셋의 문제를 해결하기 위해, **저렴하고 풍부한 RGB 이미지 데이터를 기반으로 생성 모델을 활용하여 다양한 모달리티의 합성 데이터를 생성**합니다. 이는 적은 비용으로 대규모의 다양한 시나리오와 정확한 매칭 레이블을 포함하는 데이터셋을 확보할 수 있게 합니다. 특히, RGB 데이터셋의 다양성과 매칭 레이블 정보가 합성 데이터에 효과적으로 계승되어, **일반적인 다중 모달리티 이미지 매칭 모델 학습에 필요한 데이터 부족 문제를 해결**합니다. 따라서, 본 논문의 데이터 엔진은 다양한 모달리티 이미지 매칭 문제에 대한 새로운 해결책을 제시하며, **모델의 일반화 성능 향상 및 제로샷 학습 성능 향상에 크게 기여**할 것으로 예상됩니다.

#### MINIMA Framework
MINIMA 프레임워크는 **다양한 모달리티 간의 불일치 문제를 해결하기 위해 통합된 이미지 매칭 방식**을 제시합니다. 기존 연구들의 특정 모달리티에 대한 의존성과 제한된 데이터셋 사용으로 인한 일반화 성능 저하 문제를 극복하고자, **데이터 확장 전략을 통해 다양한 모달리티와 풍부한 시나리오를 포함하는 대규모 데이터셋을 구축**하는 데 중점을 둡니다. 이를 위해 간단하면서도 효과적인 데이터 엔진을 제안하여 저렴하고 풍부한 RGB 데이터를 기반으로 다양한 모달리티의 합성 데이터를 생성합니다.  **생성된 데이터는 기존의 고급 매칭 파이프라인에 적용하여 범용적인 성능 향상**을 도모하며, 도메인 내 및 제로샷 매칭 과제에서 우수한 성능을 보입니다.  **MINIMA의 핵심은 데이터 스케일업을 통한 보편적인 성능 향상**에 있으며, 이를 통해 다양한 모달리티 조합에 대한 뛰어난 일반화 능력을 확보합니다.  결론적으로 MINIMA는 **데이터 엔진과 통합 매칭 모델의 조합을 통해 견고하고 일반화된 이미지 매칭 성능**을 제공하는 혁신적인 프레임워크입니다.

#### Zero-Shot Transfer
본 논문에서 제시된 '제로샷 전이(Zero-Shot Transfer)' 개념은 **다양한 모달리티(예: RGB, 적외선, 깊이, 이벤트) 간의 이미지 매칭**에서 **사전 훈련된 모델이 새로운 모달리티 조합에 대해서도 성능을 유지하는 능력**을 의미합니다. 이는 기존의 모달리티별 특화된 모델의 한계를 극복하고, **범용적인 이미지 매칭 시스템** 구축의 가능성을 보여줍니다.  **데이터 확장 기술**을 통해 다양한 모달리티 데이터셋을 생성하고, 이를 기반으로 훈련된 모델은 **도메인 간 차이에 대한 일반화 능력**을 향상시키는 것을 보여줍니다.  **제로샷 성능**은 다양한 실제 환경 데이터셋에서 평가되었으며, 기존 방법들에 비해 우수한 성능을 보임으로써, **모델의 범용성과 강인성**을 입증합니다.  하지만, **합성 데이터의 실제 데이터와의 차이**에 대한 추가적인 연구와 **다양한 모달리티 데이터의 균형** 문제는 향후 개선 과제로 남아있습니다.

#### Future Enhancements
본 논문의 MINIMA 프레임워크는 다양한 모달리티 간 이미지 매칭에 대한 획기적인 발전을 제시하지만, **향후 개선 및 확장을 위한 여지**는 여전히 존재합니다.  먼저, **데이터 엔진의 확장성**을 높여 더욱 다양하고 방대한 크로스-모달 데이터셋을 생성하는 연구가 필요합니다.  **합성 데이터의 현실감**을 높이기 위한 고급 생성 모델의 개발도 중요한 과제입니다.  또한, 현재 MINIMA는 단일 모델을 사용하지만, 모달리티 특성에 맞춘 **전문화된 모듈**을 통합하는 연구를 통해 성능 향상을 도모할 수 있습니다.  **제로-샷 성능** 개선을 위해 다양한 모달리티 조합에 대한 폭넓은 실험 및 추가적인 데이터 확보가 필요하며, 특히, 의료 영상이나 원격 탐사 영상 등 특수 영역에서의 성능 향상에 집중해야 합니다.  마지막으로, **실시간 처리 성능** 향상을 위한 효율적인 알고리즘 및 하드웨어 가속화 기술 개발도 중요한 미래 연구 방향입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.19412/x5.png)

> 🔼 그림 2는 실제 다중 모드 이미지 쌍에 대한 정성적 결과를 보여줍니다. 제시된 방법인 MINIMALG(희소)와 MINIMARoMa(조밀)을 희소 매칭 파이프라인인 ReDFeat [7]와 OmniGlue [20], 그리고 반조밀 매처인 XoFTR [43]과 비교합니다. ReDFeat와 XoFTR은 다중 모드 방법이고, OmniGlue는 일반화 능력으로 알려져 있습니다. 각 방법으로 생성된 매칭이 표시되며, 빨간색 선은 5×10⁻⁴ 또는 3픽셀을 초과하는 에피폴라 오차(자세) 또는 투영 오차(호모그래피)를 나타냅니다. 각 이미지 쌍의 좌상단에는 기본 RANSAC 추정으로 생성된 기하 오차와 정확한 매칭 수를 포함한 세부 정보가 기록됩니다. 이 그림은 서로 다른 모달리티(예: RGB-적외선, RGB-깊이)를 가진 이미지 쌍의 매칭 정확도를 시각적으로 보여주고, 각 알고리즘의 성능을 비교하여 다중 모드 이미지 매칭에서의 성능 차이를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Qualitative Results on Real Cross-modal Image Pairs. Our methods MINIMALG (sparse) and MINIMARoMa (dense) are compared with the sparse matching pipeline ReDFeat [7] and OmniGlue [20], and semi-dense matcher XoFTR [43]. ReDFeat and XoFTR are cross-modal methods, and OmniGlue is known for its generalization ability. Matches generated by each method are drawn, where the red lines indicate epipolar error (pose) or projection error (homography) beyond 5×10−45superscript1045\times 10^{-4}5 × 10 start_POSTSUPERSCRIPT - 4 end_POSTSUPERSCRIPT or 3333 pixels. Details are recorded in the top-left of each image pair, including the geometric errors created by default RANSAC estimation and the (# correct match / # match).
> </details>



![](https://arxiv.org/html/2412.19412/x6.png)

> 🔼 그림 3은 제안된 MINIMA 파이프라인의 개요를 보여줍니다. 이는 모든 종류의 크로스-모달 매칭 작업에 대해 단일 모델을 사용하는 프레임워크입니다. 데이터 엔진은 다양한 모달리티를 포함하는 대규모의 이미지 매칭 데이터셋을 생성하며, 이는 크로스-모달 성능을 확보하기 위해 매칭 모델의 학습을 지원합니다. 데이터 엔진은 다양한 모달리티를 가진 이미지 쌍을 생성하고, 생성된 데이터의 정확성을 보장하기 위해 정확한 매칭 레이블을 제공합니다.  단일 모델을 사용함으로써 다양한 모달리티 조합에 대한 유연성과 일반화 성능을 향상시킵니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Overview of the proposed MINIMA pipeline: a single model for any cross-modal matching tasks. Wherein the Data Engine is to generate a large multimodal image matching dataset, which supports the training of matching models to obtain cross-modal ability.
> </details>



![](https://arxiv.org/html/2412.19412/x7.png)

> 🔼 이 그림은 생성된 다양한 모달리티(적외선, 깊이, 이벤트, 노멀, 페인트, 스케치)에 대한 픽셀 강도 통계를 보여줍니다. 각 모달리티의 히스토그램을 통해 데이터 엔진이 실제 모달리티 간의 차이를 효과적으로 생성할 수 있음을 보여줍니다.  즉, 생성된 데이터가 실제 데이터처럼 다양한 특징을 가지고 있음을 시각적으로 보여주는 것입니다. 이는 다양한 모달리티 매칭 모델 학습에 도움이 될 수 있음을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4:  Pixel Intensity Statistic for Generated Modalities. The statistic differences reveal the excellent ability of our data engine to generate modality gaps.
> </details>



![](https://arxiv.org/html/2412.19412/x8.png)

> 🔼 그림 5는 LoFTR 모델을 기반으로, MD-syn 데이터셋의 합성 RGB-IR 데이터를 사용하여 스크래치 방식과 파인튜닝 방식으로 학습했을 때, 에폭에 따른 학습 손실과 AUC@5°의 변화를 보여줍니다. 스크래치 방식은 처음부터 모델을 학습하는 방식이고, 파인튜닝 방식은 사전 학습된 모델을 기반으로 추가 학습하는 방식입니다. 이 그림은 두 가지 학습 방식의 성능을 비교 분석하여 파인튜닝 방식의 효율성을 보여주는 데 초점을 맞추고 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Training Loss and AUC@5∘superscript55^{\circ}5 start_POSTSUPERSCRIPT ∘ end_POSTSUPERSCRIPT w.r.t. Epochs, using Scratch Training and Fine-tuning. The basic model is LoFTR. The test set is our synthetic RGB-IR of MD-syn.
> </details>



![](https://arxiv.org/html/2412.19412/x9.png)

> 🔼 이 그림은 MSRS 데이터셋에서 적외선 이미지 생성 결과를 보여줍니다.  앞의 두 열은 실제 RGB 이미지와 적외선 이미지이고, 나머지 열은 각각 XOFTR, CPSTN 및 제안된 방법으로 생성된 적외선 이미지입니다.  이 그림을 통해 제안된 방법이 실제 적외선 이미지와 유사한 적외선 이미지를 생성하는 성능을 시각적으로 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure A1: Visualization Results of Infrared generation on MSRS. The first two columns are real RGB and Infrared images.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
Category|Method|RGB-IR 5°|RGB-IR 10°|RGB-IR 20°|RGB-Depth 5°|RGB-Depth 10°|RGB-Depth 20°|RGB-Normal 5°|RGB-Normal 10°|RGB-Normal 20°|RGB-Event 5°|RGB-Event 10°|RGB-Event 20°|RGB-Sketch 5°|RGB-Sketch 10°|RGB-Sketch 20°|RGB-Paint 5°|RGB-Paint 10°|RGB-Paint 20°
---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---
Sparse|SuperGlue [35]|7.49|17.51|33.54|3.06|6.94|13.70|11.53|24.42|41.85|10.38|23.48|41.63|21.52|37.99|56.17|11.35|24.15|42.51
|LightGlue (LG) [28]|7.64|17.73|32.86|1.19|2.87|6.42|12.32|24.93|41.86|10.11|22.40|39.33|26.77|44.47|62.00|13.93|27.99|46.16
|ReDFeat [7]|2.75|8.56|20.90|2.20|6.36|15.25|2.56|7.25|17.79|0.00|0.00|0.00|5.26|13.91|29.01|2.73|7.32|17.83
|GIMLG [40]|8.40|18.88|33.20|0.00|0.00|0.12|12.03|23.93|38.53|6.75|14.19|23.81|28.80|46.82|63.94|13.18|26.84|43.45
|MINIMA<sub>LG</sub>|14.74|30.24|49.22|16.19|32.53|51.76|20.47|37.33|56.17|19.00|36.27|54.97|27.51|45.71|63.77|16.39|32.85|51.65
Semi-Dense|LoFTR [41]|5.44|12.58|24.28|0.13|0.44|1.88|5.72|12.07|23.14|4.90|12.43|26.45|37.81|54.82|69.52|5.93|12.22|22.19
|XoFTR [43]|17.85|32.21|49.53|12.82|23.10|36.02|22.74|38.35|54.71|33.33|51.61|67.49|44.18|61.39|75.07|3.73|7.54|14.48
|ELoFTR [47]|6.73|14.59|27.36|0.25|0.79|3.32|11.20|21.67|36.86|9.25|20.39|37.56|43.86|61.09|74.84|14.09|25.11|39.44
|GIM<sub>LoFTR</sub> [40]|2.60|6.79|15.50|0.00|0.04|0.27|0.35|1.06|4.01|0.44|1.43|5.28|17.30|31.82|48.79|4.84|10.64|21.82
|MINIMA<sub>LoFTR</sub>|18.07|32.36|48.42|14.70|28.81|46.23|27.65|44.26|59.88|18.14|32.74|49.11|36.07|53.54|68.47|7.79|15.45|27.39
Dense|DKM [9]|15.68|29.46|46.11|0.10|0.38|1.92|23.23|39.28|55.22|10.18|18.14|27.78|56.91|72.25|83.31|29.64|44.73|58.57
|GIM<sub>DKM</sub> [40]|11.23|22.72|37.93|1.42|4.07|10.86|14.09|25.81|40.55|22.86|38.30|53.58|50.89|67.12|79.02|28.22|43.49|58.06
|RoMa [10]|20.27|35.99|54.02|10.21|22.75|39.43|40.99|59.48|74.19|40.86|58.87|73.35|58.49|73.90|84.80|41.30|58.36|72.70
|MINIMA<sub>RoMa</sub>|24.33|40.94|58.33|29.56|48.58|65.87|47.10|64.48|77.90|43.83|61.48|75.21|59.17|74.30|84.86|40.09|57.21|71.96{{< /table-caption >}}
> 🔼 표 2는 본 논문에서 제안하는 데이터 생성 엔진을 사용하여 생성된 합성 데이터셋에 대한 이미지 매칭 결과를 보여줍니다.  다양한 조합의 모달리티(RGB-IR, RGB-Depth, RGB-Normal, RGB-Event, RGB-Sketch, RGB-Paint)에 대해, 여러 매칭 방법들의 성능을 정밀하게 평가했습니다.  AUC (Area Under the Curve) 지표를 사용하여 포즈 오차를 백분율로 나타내었으며, 각 카테고리별 최고 성능과 두 번째로 높은 성능을 굵은 글씨와 밑줄로 표시했습니다. 이 표는 다양한 조건에서 제안된 MINIMA 모델의 강건성과 일반화 성능을 보여주는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Full Results on Our Synthetic Dataset. The AUC of the pose error in percentage is reported. The best and second of each category are masked as Bold and Underline, respectively.
> </details>

{{< table-caption >}}
| Category | Method | Pose estimation AUC @5° | Pose estimation AUC @10° | Pose estimation AUC @20° | Time (ms) |
|---|---|---|---|---|---| 
| Sparse | RIFT<sup>(TIP 19)</sup> | 0.05 | 0.27 | 0.90 | 13k |
|  | SRIT<sup>(ISPRS 23)</sup> | 0.00 | 0.08 | 0.37 | 1.9k |
|  | LNIFT<sup>(TGRS 22)</sup> | 0.02 | 0.09 | 0.43 | 1.2k |
|  | SuperGlue<sup>(CVPR 20)</sup> | 4.30 | 9.26 | 17.21 | 86.1 |
|  | ReDFeat<sup>(TIP 23)</sup> | 1.71 | 4.57 | 10.85 | 235.8 |
|  | LightGlue (LG)<sup>(ICCV 23)</sup> | 2.17 | 5.37 | 11.21 | 57.7 |
|  | GIM<sub>LG</sub><sup>(ICLR 24)</sup> | 2.43 | 5.85 | 10.58 | 42.9 |
|  | OmniGlue<sup>(CVPR 24)</sup> | 1.48 | 4.13 | 10.11 | 3k |
|  | MINIMA<sub>LG</sub> | 19.14 | 37.17 | 55.51 | 58.6 |
| Semi-Dense | LoFTR<sup>(CVPR 21)</sup> | 2.88 | 6.94 | 14.95 | 61.6 |
|  | GIM<sub>LoFTR</sub><sup>(ICLR 24)</sup> | 0.43 | 1.06 | 2.99 | 69.5 |
|  | ELoFTR<sup>(CVPR 24)</sup> | 2.88 | 7.88 | 17.72 | 46.6 |
|  | XoFTR<sup>(CVPR 24)</sup> | 18.47 | 34.64 | 51.50 | 62.7 |
|  | MINIMA<sub>LoFTR</sub> | 15.61 | 30.84 | 47.87 | 71.6 |
| Dense | DKM<sup>(CVPR 23)</sup> | 6.76 | 13.69 | 22.53 | 485.3 |
|  | GIM<sub>DKM</sub><sup>(ICLR 24)</sup> | 5.08 | 12.30 | 23.69 | 792.2 |
|  | RoMa<sup>(CVPR 24)</sup> | 25.61 | 48.12 | 68.37 | 639.1 |
|  | MINIMA<sub>RoMa</sub> | 37.45 | 60.70 | 78.00 | 633.3 |{{< /table-caption >}}
> 🔼 표 3은 실제 RGB-IR 데이터셋(METU-VisTIR) [43]을 사용하여 자세 추정을 수행한 결과를 보여줍니다.  각 방법에 대한 자세 오차의 AUC (Area Under the Curve) 백분율이 보고되며, 마지막 열에는 평균 실행 시간이 나열되어 있습니다.  AUC는 특정 임계값(예: 5°, 10°, 20°) 이하의 자세 오차 비율을 나타내는 지표입니다.  즉, 높은 AUC 값은 더 정확한 자세 추정을 의미합니다.  이 표는 다양한 이미지 매칭 방법의 성능과 효율성을 비교 분석하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Evaluation on Real RGB-IR Dataset (METU-VisTIR) [43] with Pose Estimation. The AUC of the pose error in percentage is reported. The average runtime is listed in the last column.
> </details>

{{< table-caption >}}
| Category | Method | Homo. estimation AUC (@3px) | Homo. estimation AUC (@5px) | Homo. estimation AUC (@10px) |
|---|---|---|---|---|
| Sparse | SuperGlue [35](https://arxiv.org/html/2412.19412/bib35.png)<sub>(CVPR 20)</sub> | 1.77 | 6.83 | 21.15 |
|  | ReDFeat [7](https://arxiv.org/html/2412.19412/bib7.png)<sub>(TIP 23)</sub> | 1.01 | 4.58 | 16.30 |
|  | LightGlue (LG) [28](https://arxiv.org/html/2412.19412/bib28.png)<sub>(ICCV 23)</sub> | 0.79 | 3.30 | 11.26 |
|  | GIM<sub>LG</sub> [40](https://arxiv.org/html/2412.19412/bib40.png)<sub>(ICLR 24)</sub> | 0.30 | 1.14 | 3.65 |
|  | MINIMA<sub>LG</sub> | **8.71** | **26.80** | **55.97** |
| Semi-Dense | LoFTR [41](https://arxiv.org/html/2412.19412/bib41.png)<sub>(CVPR 21)</sub> | 0.97 | 4.20 | 15.16 |
|  | GIM<sub>LoFTR</sub> [40](https://arxiv.org/html/2412.19412/bib40.png)<sub>(ICLR 24)</sub> | 0.00 | 0.25 | 1.15 |
|  | ELoFTR [47](https://arxiv.org/html/2412.19412/bib47.png)<sub>(CVPR 24)</sub> | 0.82 | 4.09 | 16.69 |
|  | XoFTR [43](https://arxiv.org/html/2412.19412/bib43.png)<sub>(CVPR 24)</sub> | **11.03** | **27.24** | **51.60** |
|  | MINIMA<sub>LoFTR</sub> | **5.35** | **18.65** | **44.85** |
| Dense | DKM [9](https://arxiv.org/html/2412.19412/bib9.png)<sub>(CVPR 23)</sub> | 1.29 | 4.23 | 11.78 |
|  | GIM<sub>DKM</sub> [40](https://arxiv.org/html/2412.19412/bib40.png)<sub>(ICLR 24)</sub> | 1.90 | 6.34 | 17.96 |
|  | RoMa [10](https://arxiv.org/html/2412.19412/bib10.png)<sub>(CVPR 24)</sub> | **9.21** | **24.64** | **49.31** |
|  | MINIMA<sub>RoMa</sub> | **28.98** | **50.88** | **72.54** |{{< /table-caption >}}
> 🔼 표 4는 실제 RGB-Depth 데이터셋(DIODE) [44]을 사용하여 호모그래피 추정을 통해 평가한 결과를 보여줍니다.  각 방법에 대해 투영 오차의 AUC(곡선 아래 면적)를 백분율로 제시합니다.  AUC는 3픽셀, 5픽셀, 10픽셀의 오차 임계값에서 계산됩니다. 이 표는 다양한 이미지 매칭 방법들의 정확도를 비교 분석하여, 특히 RGB-Depth 이미지 쌍에 대한 호모그래피 추정 성능을 평가하는 데 유용합니다.  다양한 매칭 방법(희소, 반밀집, 밀집)의 호모그래피 추정 성능을 비교 분석하는 데 사용되었습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Evaluation on Real RGB-Depth Dataset (DIODE) [44] with Homography Estimation. The AUC of the projective error in percentage is reported.
> </details>

{{< table-caption >}}
| Category | Method | Medical@3px | Medical@5px | Medical@10px | Remote Sensing@3px | Remote Sensing@5px | Remote Sensing@10px | RGB-Event@3px | RGB-Event@5px | RGB-Event@10px |
|---|---|---|---|---|---|---|---|---|---|---|
| Sparse | SuperGlue [35] | 30.72 | 36.18 | 44.66 | 18.34 | 27.47 | 45.59 | 0.00 | 0.67 | 8.00 |
|  | LightGlue (LG) [28] | 35.47 | 42.37 | 49.48 | 16.22 | 27.51 | 44.62 | 0.00 | 0.67 | 7.02 |
|  | ReDFeat [7] | 38.55 | 44.26 | 50.93 | 15.99 | 23.95 | 43.72 | 0.55 | 0.97 | 6.07 |
|  | GIM<sub>LG</sub> [40] | 24.32 | 27.88 | 33.84 | 11.09 | 17.44 | 27.18 | 0.57 | 1.08 | 5.54 |
|  | MINIMA<sub>LG</sub> | 37.95 | 44.08 | 52.50 | 23.53 | 38.40 | 58.74 | 0.52 | 2.27 | 12.82 |
| Semi-Dense | LoFTR [41] | 38.42 | 43.89 | 50.13 | 24.13 | 33.80 | 50.79 | 0.00 | 0.00 | 3.59 |
|  | XoFTR [43] | 39.67 | 45.60 | 52.32 | 27.35 | 39.58 | 56.63 | 0.00 | 1.37 | 12.64 |
|  | ELoFTR [47] | 34.57 | 41.66 | 49.08 | 16.45 | 29.65 | 46.74 | 0.64 | 1.34 | 7.78 |
|  | GIM<sub>LoFTR</sub> [40] | 39.51 | 44.40 | 48.94 | 17.96 | 27.41 | 37.29 | 0.00 | 0.55 | 1.19 |
|  | MINIMA<sub>LoFTR</sub> | 39.67 | 45.33 | 52.77 | 23.32 | 35.18 | 56.81 | 0.81 | 2.49 | 11.75 |
| Dense | DKM [9] | 39.43 | 45.00 | 51.78 | 26.44 | 35.82 | 51.20 | 0.00 | 0.00 | 0.00 |
|  | GIM<sub>DKM</sub> [40] | 37.78 | 43.46 | 48.87 | 21.19 | 30.28 | 47.68 | 0.00 | 0.66 | 7.04 |
|  | RoMa [10] | 39.62 | 45.13 | 53.75 | 29.24 | 40.50 | 57.84 | 0.85 | 1.69 | 10.71 |
|  | MINIMA<sub>RoMa</sub> | 39.17 | 45.92 | 57.55 | 32.55 | 44.68 | 64.38 | 0.54 | 3.51 | 17.07 |{{< /table-caption >}}
> 🔼 표 5는 다양한 실제 데이터셋에서 호모그래피 추정을 사용한 제로샷 매칭 결과를 보여줍니다.  각 범주에서 가장 좋은 성능과 두 번째로 좋은 성능을 보이는 방법들이 굵은 글씨체와 밑줄로 표시되어 있습니다.  구체적으로, 제로샷 설정에서 여러 모달리티 이미지 쌍을 사용하여 다양한 매칭 방법의 성능을 평가하고, 모서리 오차의 AUC(곡선 아래 면적)를 백분율로 계산하여 정확도를 측정합니다. 이 표는 다양한 유형의 실제 이미지 데이터에 대한 제로샷 매칭의 일반화 성능을 비교 분석하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Zero-shot Matching on Real Dataset with Homography Estimation. The AUC of the corner error in percentage is reported. The best and second of each category are masked as Bold and Underline, respectively.
> </details>

{{< table-caption >}}
| Training Strategy | Syn RGB-IR | Rel RGB-IR | Rel RGB-D |
|---|---|---|---|
| Basic Model: LoFTR (LT) [41] | 12.58 | 6.94 | 15.16 |
| (1) Train from scratch on syn IR | 23.63 | 21.41 | 30.04 |
| (2) LT + real IR | 6.28 | 9.78 | 32.93 |
| (3) LT + syn IR | 29.43 | 29.55 | 39.23 |
| (4) LT + syn Depth | 17.30 | 15.12 | 36.06 |
| (5) LT + syn IR/Depth/Normal | **32.36** | **30.84** | **44.85** |{{< /table-caption >}}
> 🔼 표 6은 다양한 학습 설정으로 합성 RGB-IR, 실제 RGB-IR 및 실제 RGB-Depth 데이터에 대한 ablation 연구 결과를 보여줍니다.  다양한 학습 전략(합성 데이터로부터 처음부터 학습, 사전 학습된 모델에 실제 또는 합성 데이터로 미세 조정)을 사용하여 세 가지 유형의 데이터 세트에서 모델 성능을 비교 분석합니다.  각 학습 전략은 다양한 모달리티 조합을 사용하여 MINIMA 모델의 일반화 성능 및 강건성을 평가하는 데 사용됩니다. 이를 통해 MINIMA의 성능에 미치는 데이터 및 학습 전략의 영향을 분석하고 최적의 설정을 도출합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Ablation Studies. Test on Synthetic RGB-IR, Real RGB-IR, and Real RGB-Depth data, with different training settings.
> </details>

{{< table-caption >}}
| Data | Method | PSNR ↑ | SSIM ↑ | LPIPS ↓ | FID-2048 ↓ |
|---|---|---|---|---|---|
| **LLVIP** | CPSTN | 27.91 | 0.32 | 0.66 | 303.55 |
|  | XoFTR | 27.90 | 0.29 | 0.71 | 204.44 |
|  | **Ours** | **28.28** | **0.55** | **0.42** | **145.93** |
| **M3FD** | CPSTN | 27.82 | 0.37 | 0.56 | 161.71 |
|  | XoFTR | 27.86 | 0.33 | 0.59 | 125.07 |
|  | **Ours** | **28.14** | **0.53** | **0.46** | **119.96** |
| **MSRS** | CPSTN | **27.95** | 0.15 | 0.74 | 204.37 |
|  | XoFTR | 27.84 | 0.16 | 0.77 | 167.39 |
|  | **Ours** | **27.87** | **0.19** | **0.73** | **161.37** |{{< /table-caption >}}
> 🔼 표 A1은 적외선 이미지 생성 성능을 정량적으로 평가한 결과를 보여줍니다.  평가 지표로는 PSNR, SSIM, LPIPS, FID-2048을 사용했습니다.  LLVIP [19], M3FD [29], MSRS [42] 세 가지 데이터셋을 사용하여 실험을 진행하였으며, 비교 대상으로 CPSTN (IJCAI 22) [45]과 XoFTR (CVPR 24) [43] 방법을 사용했습니다.  각 지표에서 가장 좋은 성능을 보인 값은 굵게 표시되어 있습니다.  본 표는 제안된 방법의 적외선 이미지 생성 품질을 객관적으로 평가하고, 기존 방법들과의 성능 비교를 통해 제안된 방법의 우수성을 보여주는 것을 목표로 합니다.
> <details>
> <summary>read the caption</summary>
> Table A1: Quantitative Evaluation of Infrared Generation with Different Metrics. The test datasets are LLVIP [19], M3FD [29] and MSRS [42]. CPSTN (IJCAI 22) [45] and XoFTR (CVPR 24) [43] are used for comparison. Bold indicates the best.
> </details>

{{< table-caption >}}
Models|Generated Modalities|Rel IR|Rel Depth|Rel Event|RS|Medical|Average
---|---|---|---|---|---|---|---|---
|Infrared|Depth|Normal|Event|Paint|Sketch|AUC@10°|AUC@10px|AUC@10px|AUC@10px|AUC@10px
MINIMA<sub>LG</sub>||||||5.37|11.26|7.02|44.62|49.48|23.55
|✓|||||35.55|47.27|**13.39**|55.12|**52.73**|40.81
||✓||||30.54|51.78|12.08|57.73|52.17|40.86
|||✓||||32.66|48.66|10.44|58.15|52.43|40.47
||||✓||||23.33|38.37|10.01|55.72|51.32|35.75
|✓|✓|✓||||**37.17**|**55.97**|**12.82**|**58.74**|52.50|**43.44**
|✓|✓|✓|✓|✓|✓|36.34|55.93|12.74|58.41|52.45|43.17
MINIMA<sub>LoFTR</sub>||||||6.94|15.16|5.91|50.79|50.13|25.79
|✓|||||29.55|39.23|11.12|48.79|51.71|36.08
||✓||||15.12|36.06|5.32|53.64|52.40|32.51
|||✓||||23.14|39.79|10.28|54.73|52.53|36.09
||||✓||||14.96|32.97|12.19|45.77|50.28|31.24
|✓|✓|✓||||**30.84**|**44.85**|**11.38**|**56.81**|**52.77**|39.33
|✓|✓|✓|✓||✓|30.80|**48.55**|**12.44**|56.04|51.82|**39.93**
|✓|✓|✓|✓|✓|✓|30.61|45.10|11.83|55.33|52.19|39.01
MINIMA<sub>RoMa</sub>||||||48.12|49.31|10.71|57.84|53.75|43.95
|✓|||||57.28|57.49|10.49|60.37|57.08|48.54
||✓||||60.42|72.63|11.00|62.95|56.72|52.74
|||✓||||60.36|72.51|10.89|63.23|55.26|52.45
||||✓||||59.11|69.11|11.71|64.30|57.75|52.40
|✓|✓|✓||||**58.89**|**72.88**|**12.36**|**63.91**|**55.50**|52.71
|✓|✓|✓|✓||✓|**60.70**|72.54|**17.07**|64.38|55.09|**53.96**
|✓|✓|✓|✓|✓|✓|60.43|72.83|12.98|64.80|**57.92**|53.79{{< /table-caption >}}
> 🔼 표 A2는 다양한 훈련 데이터를 사용한 추가 실험 결과를 보여줍니다. 기본 모델로는 LightGlue(LG), LoFTR, RoMa를 사용했으며, 훈련 세트는 생성된 다중 모드 데이터의 여러 조합으로 구성됩니다. 미세 조정된 모델은 실제 다중 모드 사례에서 평가되었습니다. 각 기본 모델에 대해 원래 MegaDepth에서 훈련된 모델이 첫 번째 행에 보고되며, 마지막 열에는 평균 성능이 표시됩니다.
> <details>
> <summary>read the caption</summary>
> Table A2: Ablation Studies with Different Training Data. The basic models are LG, LoFTR, and RoMa. The training sets are different combinations of our generated cross-modal data. We evaluated the fine-tuned models on real cross-modal cases. For each baseline, the model trained on the original MegaDepth is reported in the first row. The average performance is shown in the last column.
> </details>

{{< table-caption >}}
 | Category | Method | RGB-IR 5° | RGB-IR 10° | RGB-IR 20° | RGB-Depth 5° | RGB-Depth 10° | RGB-Depth 20° | RGB-Normal 5° | RGB-Normal 10° | RGB-Normal 20° | RGB-Event 5° | RGB-Event 10° | RGB-Event 20° | RGB-Sketch 5° | RGB-Sketch 10° | RGB-Sketch 20° | RGB-Paint 5° | RGB-Paint 10° | RGB-Paint 20° | 
---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---
| Semi-Dense | LoFTR [41] | 5.44 | 12.58 | 24.28 | 0.13 | 0.44 | 1.88 | 5.72 | 12.07 | 23.14 | 4.90 | 12.43 | 26.45 | 37.81 | 54.82 | 69.52 | 5.93 | 12.22 | 22.19 | 
|  | XoFTR [43] | 17.85 | 32.21 | 49.53 | 12.82 | 23.10 | 36.02 | 22.74 | 38.35 | 54.71 | 33.33 | 51.61 | 67.49 | 44.18 | 61.39 | 75.07 | 3.73 | 7.54 | 14.48 | 
|  | ELoFTR [47] | 6.73 | 14.59 | 27.36 | 0.25 | 0.79 | 3.32 | 11.20 | 21.67 | 36.86 | 9.25 | 20.39 | 37.56 | 43.86 | 61.09 | 74.84 | 14.09 | 25.11 | 39.44 | 
|  | GIM<sub>LoFTR</sub> [40] | 2.60 | 6.79 | 15.50 | 0.00 | 0.04 | 0.27 | 0.35 | 1.06 | 4.01 | 0.44 | 1.43 | 5.28 | 17.30 | 31.82 | 48.79 | 4.84 | 10.64 | 21.82 | 
|  | MINIMA<sub>LoFTR</sub> | 18.07 | 32.36 | 48.42 | 14.70 | 28.81 | 46.23 | 27.65 | 44.26 | 59.88 | 18.14 | 32.74 | 49.11 | 36.07 | 53.54 | 68.47 | 7.79 | 15.45 | 27.39 | 
|  | MINIMA<sub>XoFTR</sub> | 18.97 | 34.36 | 51.72 | 24.47 | 40.90 | 58.36 | 30.47 | 47.90 | 64.64 | 31.14 | 49.39 | 65.71 | 42.91 | 60.77 | 75.00 | 5.61 | 11.56 | 20.95 | 
|  | MINIMA<sub>ELoFTR</sub> | 13.14 | 26.36 | 43.63 | 16.59 | 32.26 | 50.37 | 29.72 | 47.47 | 63.72 | 15.66 | 30.72 | 48.73 | 41.64 | 59.63 | 73.73 | 15.02 | 27.02 | 41.62 | {{< /table-caption >}}
> 🔼 표 A3는 합성 데이터셋에서의 반밀집 매칭 결과를 보여줍니다. 자세히 설명하자면, 다양한 합성 이미지 쌍에 대한 포즈 오차의 AUC(곡선 아래 면적)를 백분율로 나타냅니다.  각 범주(Sparse, Semi-dense, Dense) 내에서 가장 좋은 성능과 두 번째로 좋은 성능을 굵은 글씨와 밑줄로 표시하여, 제안된 MINIMA 방법의 성능을 다른 기존 방법들과 비교 분석합니다.  다양한 모달리티 조합(RGB-IR, RGB-Depth 등)에 대한 결과를 포함하고 있습니다. 
> <details>
> <summary>read the caption</summary>
> Table A3: Semi-dense Matching Results on Our Synthetic Dataset. The AUC of the pose error in percentage is reported. The best and second are masked as Bold and Underline, respectively.
> </details>

{{< table-caption >}}
| Category | Method | Real RGB-IR @5° | Real RGB-IR @10° | Real RGB-IR @20° | Real RGB-IR @3px | Real RGB-IR @5px | Real RGB-IR @10px | Real RGB-Depth @3px | Real RGB-Depth @5px | Real RGB-Depth @10px | Medical @3px | Medical @5px | Medical @10px | Remote Sensing @3px | Remote Sensing @5px | Remote Sensing @10px | Real RGB-Event @3px | Real RGB-Event @5px | Real RGB-Event @10px |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Semi-Dense | LoFTR [41] | 2.88 | 6.94 | 14.95 | 0.97 | 4.20 | 15.16 | 38.42 | 43.89 | 50.13 | 24.13 | 33.80 | 50.79 | 0.00 | 0.00 | 3.59 |
|  | XoFTR [43] | 18.47 | 34.64 | 51.5 | 11.03 | 27.24 | 51.60 | 39.67 | 45.60 | 52.32 | 27.35 | 39.58 | 56.63 | 0.00 | 1.37 | 12.64 |
|  | ELoFTR [47] | 2.88 | 7.88 | 17.72 | 0.82 | 4.09 | 16.69 | 34.57 | 41.66 | 49.08 | 16.45 | 29.65 | 46.74 | 0.64 | 1.34 | 7.78 |
|  | GIM<sub>LoFTR</sub> [40] | 0.43 | 1.06 | 2.99 | 0.00 | 0.25 | 1.15 | 39.51 | 44.40 | 48.94 | 17.96 | 27.41 | 37.29 | 0.00 | 0.55 | 1.19 |
|  | MINIMA<sub>LoFTR</sub> | 15.61 | 30.84 | 47.87 | 5.35 | 18.65 | 44.85 | 39.67 | 45.33 | 52.77 | 23.32 | 35.18 | 56.81 | 0.81 | 2.49 | 11.75 |
|  | MINIMA<sub>XoFTR</sub> | 19.38 | 35.82 | 52.94 | 11.76 | 29.48 | 55.05 | 39.33 | 44.92 | 52.09 | 25.19 | 37.86 | 54.36 | 0.00 | 1.92 | 15.23 |
|  | MINIMA<sub>ELoFTR</sub> | 12.11 | 28.07 | 47.25 | 3.96 | 16.42 | 44.03 | 39.12 | 44.61 | 52.12 | 19.70 | 33.78 | 53.83 | 0.37 | 1.04 | 9.66 |{{< /table-caption >}}
> 🔼 표 A4는 실제 데이터셋에서의 반밀집 매칭 결과를 보여줍니다. 각 방법에 대해 자세한 성능을 평가하기 위해 다양한 실제 크로스 모달 데이터셋(RGB-IR, RGB-Depth, 의료, 원격 탐사, RGB-Event)에 대한 포즈 오차의 AUC(Area Under the Curve)를 백분율로 제시합니다.  AUC는 포즈 오차 임계값에 대한 정확도를 측정한 값으로, 값이 높을수록 성능이 우수함을 나타냅니다. 표에는 각 데이터셋과 방법에 대한 AUC 값과 함께 최고 성능과 두 번째로 높은 성능을 굵은 글씨와 밑줄로 표시하여 직관적으로 비교할 수 있게 했습니다. 이 표는 제안된 MINIMA 모델이 다양한 실제 크로스 모달 상황에서 기존 방법보다 뛰어난 성능을 보임을 보여주는 증거입니다.
> <details>
> <summary>read the caption</summary>
> Table A4: Semi-dense Matching Results on Real Dataset. The AUC of the pose error in percentage is reported. The best and second are masked as Bold and Underline, respectively.
> </details>

{{< table-caption >}}
| Category | Method | Pose estimation AUC @5° | Pose estimation AUC @10° | Pose estimation AUC @20° |
|---|---|---|---|---|
| Sparse | SuperGlue [35](https://arxiv.org/html/2412.19412v1#bib.bib35)<sub>(CVPR 20)</sub> | 49.7 | 67.1 | 80.6 |
|  | LightGlue (LG) [28](https://arxiv.org/html/2412.19412v1#bib.bib28)<sub>(ICCV 23)</sub> | 49.9 | 67.0 | 80.1 |
|  | GIM<sub>LG</sub> [40](https://arxiv.org/html/2412.19412v1#bib.bib40)<sub>(ICLR 24)</sub> | 41.3 | 60.7 | 75.9 |
|  | MINIMA<sub>LG</sub> | 47.3 | 65.0 | 78.6 |
| Semi-Dense | LoFTR [41](https://arxiv.org/html/2412.19412v1#bib.bib41)<sub>(CVPR 21)</sub> | 53.6 | 69.9 | 82.0 |
|  | GIM<sub>LoFTR</sub> [40](https://arxiv.org/html/2412.19412v1#bib.bib40)<sub>(ICLR 24)</sub> | 51.3 | 68.5 | 81.1 |
|  | ELoFTR [47](https://arxiv.org/html/2412.19412v1#bib.bib47)<sub>(CVPR 24)</sub> | 56.4 | 72.2 | 83.5 |
|  | XoFTR [43](https://arxiv.org/html/2412.19412v1#bib.bib43)<sub>(CVPR 24)</sub> | 45.8 | 61.7 | 74.0 |
|  | MINIMA<sub>LoFTR</sub> | 29.9 | 45.3 | 59.5 |
|  | MINIMA<sub>ELoFTR</sub> | 51.0 | 68.1 | 80.3 |
|  | MINIMA<sub>XoFTR</sub> | 44.5 | 60.0 | 72.3 |
| Dense | DKM [9](https://arxiv.org/html/2412.19412v1#bib.bib9)<sub>(CVPR 23)</sub> | 60.4 | 74.9 | 85.1 |
|  | GIM<sub>DKM</sub> [40](https://arxiv.org/html/2412.19412v1#bib.bib40)<sub>(ICLR 24)</sub> | 60.7 | 75.5 | 85.9 |
|  | RoMa [10](https://arxiv.org/html/2412.19412v1#bib.bib10)<sub>(CVPR 24)</sub> | 62.6 | 76.7 | 86.3 |
|  | MINIMA<sub>RoMa</sub> | 61.7 | 76.5 | 86.4 |{{< /table-caption >}}
> 🔼 표 A5는 원본 Megadepth-1500 데이터셋을 사용하여 자세 추정을 수행한 결과를 보여줍니다.  자세 오차의 AUC (Area Under the Curve) 값을 백분율로 나타냈습니다. 이 표는 MINIMA가 LoFTR을 사용하는 경우를 제외하고는 RGB 전용 매칭 성능을 잘 유지함을 보여줍니다.  즉, MINIMA는 다양한 모달리티를 사용하는 경우에도 RGB 영상 매칭에서의 성능을 크게 저하시키지 않고 유지한다는 것을 의미합니다. 다만, LoFTR을 사용할 경우에는 성능 저하가 발생함을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table A5: Evaluation on Original Megadepth-1500 for Pose Estimation. The AUC of the pose error in percentage is reported. This mainly demonstrates that our MINIMA can well preserve the RGB-only matching performance except when using LoFTR.
> </details>

{{< table-caption >}}
| Method | Day | Night |
|---|---|---|
| MNN | 86.9 / 92.0 / 95.5 | 73.5 / 79.6 / 88.8 |
| SuperGlue [35]<sub>(CVPR 20)</sub> | 87.9 / **95.0** / 97.9 | 84.7 / **92.9** / 99.0 |
| SGMNet [4]<sub>(ICCV 21)</sub> | 86.5 / 93.7 / 97.2 | 82.7 / 91.8 / 99.0 |
| LightGlue (LG) [28]<sub>(ICCV 23)</sub> | 88.0 / 93.8 / 97.5 | 84.7 / 91.8 / 99.0 |
| ConvMatch [60]<sub>(TPAMI 23)</sub> | 88.1 / 94.4 / 97.3 | 79.6 / 88.8 / 96.9 |
| MINIMA<sub>LG</sub> | **88.3** / 94.7 / 98.3 | **85.7** / 92.9 / 100.0 |{{< /table-caption >}}
> 🔼 표 A6는 Aachen Day-Night V1.0 데이터셋 [36]을 사용한 시각적 위치 인식 결과를 보여줍니다.  다양한 방법(MNN, SuperGlue, SGMNet, LightGlue, ConvMatch, MINIMA)을 사용하여 낮과 밤의 이미지에서 6자유도 카메라 자세를 복원하는 성능을 평가합니다.  각 방법의 성능은 세 가지 거리 및 각도 임계값(0.25m, 2°), (0.5m, 5°), (5m, 10°)에서 자세 재현율로 측정됩니다. 이 표는 서로 다른 조건(낮, 밤)에서 다양한 매칭 기법의 위치 인식 성능을 비교 분석하여, 각 기법의 강점과 약점을 파악하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table A6: Visual Localization on Aachen Day-Night V1.0 [36]
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