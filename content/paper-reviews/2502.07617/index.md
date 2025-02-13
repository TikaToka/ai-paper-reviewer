---
title: "Scaling Pre-training to One Hundred Billion Data for Vision Language Models"
summary: "1000억 개 이미지-텍스트 쌍 WebLI-100B로 비전-언어 모델 사전 훈련: 문화적 다양성 및 다국어 성능 향상!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Vision-Language Models", "🏢 Google DeepMind",]
showSummary: true
date: 2025-02-11
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.07617 {{< /keyword >}}
{{< keyword icon="writer" >}} Xiao Wang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-12 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.07617" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.07617" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/scaling-pre-training-to-one-hundred-billion" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

본 연구는 **대규모 웹 데이터를 활용한 비전-언어 모델 사전 훈련**의 잠재력을 조사한 연구입니다.  기존 연구들은 주로 서구 중심적인 데이터와 벤치마크에 집중하여, 문화적 다양성과 다국어 지원이 부족한 모델들이 개발되는 문제점을 가지고 있었습니다.  또한 데이터의 질적 향상을 위해 사용되는 필터링 기법이 문화적 다양성을 저해할 수 있다는 점도 문제로 지적되었습니다. 

본 연구는 **1000억 개의 이미지-텍스트 쌍으로 구성된 WebLI-100B 데이터셋**을 새롭게 제시하고, 이를 이용하여 비전-언어 모델을 사전 훈련했습니다. 그 결과, 기존의 서구 중심적인 벤치마크에서는 성능 향상이 미미했지만, 문화적 다양성과 다국어 지원 능력이 크게 향상되었음을 확인했습니다. **WebLI-100B 데이터셋**과 실험 결과는 **문화적으로 포괄적이고 공정한 다중 모달 시스템**을 구축하는 데 중요한 기여를 할 것으로 기대됩니다. 특히, 데이터 필터링 기법의 사용에 대한 신중한 접근의 필요성을 강조하고 있습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 1000억 개의 이미지-텍스트 쌍으로 구성된 대규모 WebLI-100B 데이터셋을 사용하여 비전-언어 모델을 사전 훈련했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 기존 벤치마크에서는 성능 향상이 제한적이었으나, 문화적 다양성 및 다국어 능력 측면에서는 상당한 개선을 이루었습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 데이터 필터링이 모델의 문화적 다양성에 미치는 부정적 영향을 밝히고, 보다 포괄적인 다중 모달 시스템 구축을 위한 새로운 방향을 제시했습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **1000억 개의 이미지-텍스트 쌍으로 구성된 대규모 웹 데이터셋 WebLI-100B**를 활용하여 비전-언어 모델을 사전 훈련한 결과를 제시합니다. 기존의 서구 중심적인 벤치마크에서는 성능 향상이 제한적이었지만, **문화적 다양성 및 다국어 능력** 측면에서는 상당한 성과를 달성했습니다. 이는 **소규모 언어 및 문화적으로 소외된 그룹**에 대한 모델의 포괄성을 높이는 데 중요한 의미를 지닙니다. 본 연구는 **데이터 규모 확장의 영향**에 대한 심층적인 이해를 제공하고, 향후 **포괄적인 다중 모달 시스템** 구축을 위한 새로운 방향을 제시합니다. 또한 **데이터 필터링**이 문화적 다양성에 미치는 영향을 분석하여 **더욱 포괄적이고 공정한 모델 개발**에 대한 중요한 시사점을 제공합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.07617/x1.png)

> 🔼 그림 1은 데이터 크기 증가가 모델 성능에 미치는 영향을 보여줍니다. 왼쪽 그래프는 100억 개의 데이터에서 1,000억 개의 데이터로 확장하면 문화적 다양성과 다국어 기능이 다른 지표보다 더 크게 향상됨을 보여줍니다. 숫자는 모든 작업에서 평균을 낸 데이터 크기 증가 시 절대적인 정확도 향상을 나타냅니다. 자세한 내용은 4장을 참조하세요. 오른쪽 그래프는 데이터 크기의 영향을 보여주는 예시입니다. 왼쪽 두 개는 서구 중심적인 지표로, 데이터 크기를 1,000억 개로 늘려도 큰 이점이 없습니다. 반면 오른쪽 두 개는 문화적 다양성과 다국어 기능을 보여주는 예시로, 예를 들어 텔루구어는 웹의 0.04% 미만을 차지하지만 1,000억 개의 데이터 크기에서 큰 이점을 얻습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: left: Scaling the data from 10 billion to 100 billion examples enhances cultural diversity and multilingual capabilities more prominently than other metrics. The numbers represent the improved accuracy (in absolute terms) when data scale is increased, averaged across all tasks. See details in Section 4. right: Illustrative examples of the impact of data scale. The leftmost two are Western-centric metrics, which do not benefit much by scaling the data to 100 billion, while the rightmost two are illustrative of cultural diversity and multilinguality. The language Telugu, for example, makes up <0.04%absentpercent0.04<0.04\%< 0.04 % of the web and benefits a lot from the 100 billion data scale.
> </details>





{{< table-caption >}}
| Concept | Image | 1B Data | 10B Data | 100B Data |
|---|---|---|---|---|
| Igorot Dance (Igorot) | https://arxiv.org/html/2502.07617/x6.png | https://arxiv.org/html/2502.07617/x7.png | https://arxiv.org/html/2502.07617/x8.png | https://arxiv.org/html/2502.07617/x9.png |
| Igloo (Inuit) | https://arxiv.org/html/2502.07617/x10.png | https://arxiv.org/html/2502.07617/x11.png | https://arxiv.org/html/2502.07617/x12.png | https://arxiv.org/html/2502.07617/x13.png |
| Bison (Yellowstone) | https://arxiv.org/html/2502.07617/x14.png | https://arxiv.org/html/2502.07617/x15.png | https://arxiv.org/html/2502.07617/x16.png | https://arxiv.org/html/2502.07617/x17.png |{{< /table-caption >}}

> 🔼 표 1은 서로 다른 규모의 데이터로 학습된 ViT-L/16 모델의 어텐션 맵 시각화를 보여줍니다. 선택된 이미지들은 서구 중심 국가와 저자원 언어가 사용되는 국가의 문화를 대표합니다.  이 표는 모델이 이미지의 어떤 부분에 주의를 기울이는지 시각적으로 보여줌으로써, 데이터 규모가 모델의 시각적 이해에 미치는 영향을 보여줍니다. 서구 중심 문화와 저자원 언어권 문화 모두를 대표하는 이미지들을 포함하여 다양한 문화적 배경을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 1: The attention map visualization of the ViT-L/16 models trained on different scales of data. Images are selected to represent cultures in Western-centric countries and countries where low-resource languages are spoken.
> </details>





### In-depth insights


#### Data Scaling Laws
본 논문에서 데이터 확장 법칙에 대한 심층적인 논의는 명시적으로 제시되지 않았지만, **데이터 규모의 증가가 모델 성능 향상에 미치는 영향**에 대한 실험적 연구 결과를 통해 간접적으로 논의되고 있음을 알 수 있습니다.  대규모 데이터셋을 사용한 사전 학습의 효과와 한계를 다루고 있으며, 특히 **기존의 서구 중심적인 벤치마크에서는 성능 향상의 한계**가 있음을 보여주는 한편, **문화적 다양성 및 다국어 지원 측면**에서는 상당한 개선 효과를 확인했습니다. 따라서 데이터 확장 법칙은 단순히 데이터 양의 증가가 선형적으로 성능 향상으로 이어지는 것이 아니라, **데이터의 질과 다양성, 그리고 모델의 복잡도와의 상호 작용**에 따라 복잡하게 영향을 받는다는 것을 시사합니다.  **특히 문화적 다양성이 부족한 기존 데이터셋의 한계를 극복**하기 위한 대규모 웹 데이터의 중요성을 강조하는 것이 본 연구의 주요 함축입니다.

#### VLM Pre-training
본 논문은 **대규모 데이터를 활용한 Vision-Language Model(VLM)의 사전 훈련**에 대한 심층적인 분석을 제공합니다.  초기 연구는 웹에서 기존의 방식으로 정제된 데이터셋에 의존했지만, **WebLI-100B와 같이 1000억 개의 이미지-텍스트 쌍으로 구성된 방대한 규모의 데이터셋**을 활용하여 사전훈련의 가능성을 탐구합니다.  기존의 서구 중심적인 벤치마크에서는 성능 향상이 제한적이었으나, **문화적 다양성 및 저자원 언어**에 대한 성능은 상당히 향상됨을 보였습니다.  이는 **대규모 데이터가 장기적으로 긴 꼬리 개념을 포착하는데 중요**함을 시사합니다. 또한, CLIP과 같은 기존의 필터링 기법은 데이터 품질을 향상시키지만, **문화적 다양성을 감소시키는 역효과**를 가져올 수 있음을 보여줍니다. 따라서, **포괄적인 다중 모드 시스템을 구축**하기 위해서는 대규모의 원시 웹 데이터를 활용한 사전 훈련이 필수적임을 강조합니다.

#### Cultural Diversity
본 논문에서 '문화 다양성'은 단순한 키워드를 넘어서, **서구 중심적 벤치마크의 한계를 극복하고 진정한 다중 모달 시스템을 구축하는 데 필수적인 요소**임을 강조합니다. 기존 벤치마크에서 성능 향상이 미미했던 반면, **문화적 다양성과 관련된 과제에서는 100억 개에서 1000억 개의 데이터로 확장함으로써 상당한 성능 향상**을 보였습니다. 이는 **장기간 학습 데이터의 부족으로 인해 잘 나타나지 않았던 소외된 문화 개념들을 포착하는 데 대규모 데이터가 중요한 역할**을 함을 시사합니다.  **CLIP과 같은 품질 필터는 성능 향상에 기여하지만, 역으로 문화적 다양성을 감소시키는 부작용**도 발생할 수 있음을 보여줍니다. 따라서, **데이터의 양적 확장 뿐 아니라 문화적 다양성을 보존하고 증진하는 데이터 큐레이션 및 모델 학습 전략**이 중요함을 강조합니다.  이는 **포괄적인 다중모달 시스템을 구축하기 위한 중요한 전략**이 될 것입니다.

#### Bias Mitigation
이 논문은 **대규모 데이터셋을 사용한 비전-언어 모델 사전 학습의 영향**에 대해 광범위하게 다루고 있습니다. 특히, 편향 완화 전략의 효과를 평가하고, **기존의 편향 완화 기법이 문화적 다양성을 저해할 수 있음**을 보여주는 중요한 발견을 제시하고 있습니다.  이는 단순히 성능 향상에만 초점을 맞추기 보다는 **모델의 포괄성과 공정성 확보**를 위해 데이터셋 구성 및 사전 학습 과정 전반에 대한 재검토가 필요함을 시사합니다.  **웹 데이터의 문화적 다양성 활용**이 중요하지만, 이를 위해서는 단순히 데이터 양을 늘리는 것만으로는 부족하며, **데이터 품질 및 편향 완화 기법의 신중한 적용**이 필수적입니다.  결론적으로, 이 논문은 **진정으로 포괄적이고 공정한 다중 모달 시스템 구축**을 위한  새로운 방향을 제시하는 중요한 연구입니다.

#### Future Research
본 논문은 1000억 개의 이미지-텍스트 쌍으로 구성된 WebLI-100B 데이터셋을 사용하여 비전-언어 모델을 사전 훈련하는 실험 결과를 제시합니다. **향후 연구는 WebLI-100B 데이터셋의 품질 개선과 다양성 확보에 초점을 맞춰야 합니다.**  **특히, 문화적 다양성을 저해하지 않으면서 데이터셋의 품질을 향상시키는 새로운 필터링 기법을 개발하는 것이 중요합니다.** 또한, 현재의 벤치마크는 주로 서구 중심적인 경향을 보이므로, **더욱 포괄적인 다양한 문화적 배경을 반영하는 새로운 벤치마크를 개발해야 합니다.**  **저자원 언어에 대한 모델 성능 개선을 위해 데이터 불균형 문제를 해결하고 저자원 언어 데이터를 증강하는 연구가 필요합니다.** 마지막으로, **대규모 데이터셋을 효율적으로 활용하는 새로운 사전훈련 기법 및 모델 아키텍처에 대한 연구가 필요합니다.**


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.07617/x27.png)

> 🔼 그림 2는 확장된 모델과 데이터에서 성별과 직업 간의 연관성 편향을 평가한 결과를 보여줍니다.  각 그래프는 특정 모델(B, L, H)과 데이터 크기(10억, 100억, 1000억)에 따른 성별과 특정 직업(간호사, 사서, 가정부, 접수원, 비서)의 연관성을 시각적으로 나타냅니다.  색상 강도는 각 직업에 대한 성별 연관성의 강도를 나타내며, 더 진한 색상은 더 강한 연관성을 의미합니다. 이 그림은 대규모 데이터 학습을 통해 성별과 직업 간의 고정관념이 어떻게 변화하는지, 그리고 각 모델이 이러한 편향을 어떻게 학습하는지 보여주는 데 중점을 둡니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Association bias between gender and occupation, evaluated in scaled models and data.
> </details>



![](https://arxiv.org/html/2502.07617/x65.png)

> 🔼 그림 3은 1000억 개의 예제로 확장하면 저자원 언어의 성능이 크게 향상됨을 보여줍니다.  Δ는 100억 개의 예제에서 1000억 개의 예제로 확장할 때 정확도가 향상된 정도를 나타냅니다. 이는 저자원 언어 모델이 대규모 데이터셋에서 더 많은 이점을 얻을 수 있음을 시사합니다.  대조적으로, 고자원 언어는 상대적으로 적은 향상을 보입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Scaling up to 100B examples leads to more notable improvements in low-resource languages. ΔΔ\Deltaroman_Δ denotes the improved accuracy when scaling from 10B examples to 100B.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
## Table 1: Model performance and scaling laws

| Model | Metric (err%) | Value @ 100B ex (1B) | Value @ 100B ex (10B) | Value @ 100B ex (100B) | exponent (1B) | exponent (10B) | exponent (100B) | limit (1B) | limit (10B) | limit (100B) |
|---|---|---|---|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |  |  |  |  |
|  |  | 1B | 10B | 100B | 1B | 10B | 100B | 1B | 10B | 100B |
|  |  |  |  |  |  |  |  |  |  |  |
| *Zero-shot classification* |  |  |  |  |  |  |  |  |  |  |
| B | ImageNet | 41.2 | 39.4 | **39.0** | -0.58 | -0.97 | -0.65 | 40.1 | **38.5** | **37.9** |
|  | CIFAR100 | **36.6** | **35.9** | 36.8 | -0.26 | -0.23 | -0.24 | 33.8 | **32.5** | **33.7** |
|  | Pet | 25.4 | **23.7** | **22.3** | -0.43 | -0.45 | -0.37 | 22.3 | **21.7** | **18.4** |
| L | ImageNet | 31.2 | **29.7** | **28.5** | -0.92 | -0.91 | -0.82 | 30.7 | **29.0** | **27.1** |
|  | CIFAR100 | 25.0 | **23.8** | **23.4** | -0.26 | -0.32 | -0.43 | 22.7 | **20.7** | **21.1** |
|  | Pet | 14.4 | **12.5** | **9.5** | -0.61 | -0.57 | -0.51 | 12.3 | **9.6** | **7.0** |
| H | ImageNet | 29.6 | **25.6** | **24.9** | -0.36 | -0.64 | -0.52 | 26.7 | **24.5** | **23.3** |
|  | CIFAR100 | 23.5 | **19.8** | **21.4** | -0.25 | -0.36 | -0.29 | 20.6 | **18.0** | **17.6** |
|  | Pet | 10.3 | **7.5** | **7.2** | -0.45 | -0.42 | -0.50 | 8.1 | **5.3** | **4.6** |
|  |  |  |  |  |  |  |  |  |  |  |
| *Retrieval @1* |  |  |  |  |  |  |  |  |  |  |
| B | COCO I2T@1 | 56.5 | **51.6** | **53.4** | -0.24 | -0.49 | -0.30 | 52.4 | **49.9** | **50.7** |
|  | COCO T2I@1 | 70.9 | **68.8** | **70.0** | -0.34 | -0.39 | -0.69 | 69.6 | **67.1** | **69.5** |
|  | Flickr I2T@1 | 24.2 | **21.2** | **21.1** | -0.24 | -0.34 | -0.23 | 21.5 | **18.1** | **17.0** |
|  | Flickr T2I@1 | 43.1 | **40.3** | **40.4** | -0.32 | -0.42 | -0.30 | 40.9 | **37.5** | **36.7** |
| L | COCO I2T@1 | 49.7 | **47.2** | **45.3** | -0.24 | -0.41 | -0.30 | 45.8 | **44.7** | **42.9** |
|  | COCO T2I@1 | 68.2 | **64.3** | **62.5** | -0.19 | -0.42 | -0.41 | 64.2 | **62.6** | **60.5** |
|  | Flickr I2T@1 | 20.4 | **15.5** | **16.6** | -0.21 | -0.45 | -0.21 | 16.5 | **14.1** | **13.4** |
|  | Flickr T2I@1 | 39.9 | **32.3** | **32.5** | -0.10 | -0.42 | -0.42 | 34.6 | **30.7** | **30.7** |
| H | COCO I2T@1 | 48.6 | **42.0** | **42.5** | -0.21 | -0.62 | -0.47 | 44.6 | **40.3** | **40.6** |
|  | COCO T2I@1 | 64.9 | **60.3** | **59.3** | -0.30 | -0.55 | -0.43 | 62.8 | **58.9** | **57.3** |
|  | Flickr I2T@1 | 16.8 | **13.5** | **13.9** | -0.23 | -0.40 | -0.23 | 12.2 | **11.4** | **11.3** |
|  | Flickr T2I@1 | 34.3 | **28.5** | **28.0** | -0.23 | -0.56 | -0.46 | 29.6 | **26.8** | **25.9** |
|  |  |  |  |  |  |  |  |  |  |  |
| *10-shot* |  |  |  |  |  |  |  |  |  |  |
| B | Imagenet | 46.6 | **45.6** | **44.7** | -0.82 | -0.61 | -0.49 | 46.2 | **44.4** | **43.3** |
|  | Birds | **53.8** | **53.5** | 53.9 | -0.34 | -0.40 | -0.51 | **51.5** | **51.6** | 52.8 |
|  | Caltech | 8.4 | **8.3** | **8.2** | -0.30 | -0.24 | -0.23 | **7.1** | 7.2 | 6.8 |
|  | Cars | 18.3 | **16.8** | **17.6** | -0.63 | -0.68 | -0.60 | 17.1 | **15.5** | **16.3** |
|  | CIFAR100 | **38.7** | **38.6** | 39.0 | -0.19 | -0.22 | -0.20 | **35.2** | **34.9** | 35.9 |
|  | Colorectal | **26.5** | 29.2 | **27.0** | -0.02 | -0.06 | -0.16 | **20.2** | **22.6** | 24.4 |
|  | Pet | **22.9** | 23.2 | **22.1** | -1.77 | -0.62 | -0.77 | **21.6** | **21.3** | 20.6 |
|  | DTD | **29.7** | **30.9** | **30.9** | -0.28 | -0.24 | -0.19 | **27.9** | 28.3 | 27.2 |
| L | Imagenet | 35.1 | **35.0** | **33.7** | -0.67 | -0.68 | -0.63 | 34.1 | **34.0** | **32.5** |
|  | Birds | **44.0** | 45.3 | **44.3** | -0.51 | -0.43 | -0.51 | **42.1** | 43.2 | 42.7 |
|  | Caltech | **6.4** | **7.4** | 7.5 | -0.43 | -0.17 | -0.18 | **5.9** | **4.8** | 4.8 |
|  | Cars | **11.1** | **11.3** | 11.5 | -0.54 | -0.49 | -0.41 | 10.1 | **9.7** | **9.9** |
|  | CIFAR100 | 27.5 | **26.7** | **25.5** | -0.24 | -0.29 | -0.41 | **24.0** | **23.7** | 22.9 |
|  | Colorectal | **25.2** | 26.2 | **25.9** | -0.22 | -0.20 | -0.15 | **19.7** | **20.2** | 20.7 |
|  | Pet | **12.3** | 12.5 | **11.8** | -0.70 | -0.65 | -0.53 | **11.3** | **11.4** | 10.3 |
|  | DTD | 28.5 | **27.1** | **27.9** | -0.22 | -0.25 | -0.23 | **25.2** | **25.1** | 25.5 |
| H | Imagenet | 32.4 | **29.8** | **29.3** | -0.41 | -0.73 | -0.79 | 30.3 | **29.0** | **28.3** |
|  | Birds | 41.6 | **39.1** | **36.3** | -0.67 | -0.52 | -0.47 | 40.6 | **37.4** | **33.9** |
|  | Caltech | **5.7** | **6.0** | 8.9 | -0.21 | -0.08 | -0.11 | **4.3** | **3.7** | 4.6 |
|  | Cars | 11.3 | **10.3** | **9.6** | -0.27 | -0.88 | -0.44 | 9.1 | **10.1** | **8.3** |
|  | CIFAR100 | 25.8 | **23.8** | **24.2** | -0.22 | -0.25 | -0.24 | 21.4 | **21.1** | 19.7 |
|  | Colorectal | **25.2** | 26.2 | **25.9** | -0.22 | -0.20 | -0.15 | **19.7** | **20.2** | 20.7 |
|  | Pet | 10.8 | **9.1** | **8.7** | -0.92 | -0.48 | -0.46 | **10.3** | **7.6** | 6.5 |
|  | DTD | 29.2 | **26.1** | **26.8** | -0.16 | -0.23 | -0.23 | **25.0** | **23.8** | 24.8 |{{< /table-caption >}}
> 🔼 표 2는 서구 중심적 벤치마크에 대한 평가와 확장 법칙을 보여줍니다. 100억 개의 예제로 확장하는 것보다 100억 개의 데이터에서 1000억 개의 데이터로 확장했을 때 성능 향상이 제한적임을 보여줍니다.  다양한 모델 크기(B, L, H)와 제로샷 분류, 검색 등 다양한 작업에 대한 결과를 보여주는 포괄적인 표입니다.  이 표는 데이터 크기 증가에 따른 성능 향상의 한계를 보여주는 데 중점을 두고 있으며,  서구 중심적 지표에서의 성능 개선은 크지 않다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Evaluations and scaling laws on Western-centric benchmarks, where scaling from 10B to 100B examples shows limited benefits.
> </details>

{{< table-caption >}}
| Model | Metric (err %) | Value @ 100B ex |  |  | Scaling Laws |  |  |  |  |  | 
|---|---|---|---|---|---|---|---|---|---|---|
|  |  | 1B | 10B | 100B | exponent |  |  | limit |  |  | 
|  |  |  |  |  |  |  |  |  |  |  | 
| 10-shot Geolocalization |  |  |  |  |  |  |  |  |  |  | 
| B | Dollar Street | 77.7 | 75.8 | 72.1 | -0.38 | -0.36 | -0.37 | 76.3 | 73.7 | 70.2 |
| B | GeoDE-Country | 72.8 | 71.5 | 71.4 | -0.35 | -0.31 | -0.37 | 70.8 | 69.6 | 68.9 |
| B | GeoDE-Region | 61.1 | 60.8 | 59.2 | -0.26 | -0.22 | -0.29 | 58.8 | 57.0 | 57.3 |
| L | Dollar Street | 63.6 | 64.1 | 58.3 | -1.09 | -0.38 | -0.94 | 63.2 | 60.1 | 57.5 |
| L | GeoDE-Country | 61.9 | 62.3 | 57.8 | -0.40 | -0.30 | -1.11 | 58.8 | 58.0 | 56.6 |
| L | GeoDE-Region | 54.2 | 53.6 | 48.3 | -0.15 | -0.16 | -0.39 | 49.9 | 46.9 | 46.3 |
| H | Dollar Street | 64.6 | 59.1 | 53.7 | -0.30 | -0.56 | -0.64 | 61.0 | 56.4 | 52.5 |
| H | GeoDE-Country | 56.9 | 50.2 | 47.6 | -0.23 | -0.78 | -0.62 | 52.2 | 49.4 | 46.1 |
| H | GeoDE-Region | 54.6 | 47.6 | 44.7 | 0.00 | -0.38 | -0.31 | 50.1 | 45.3 | 41.0 |
| Zero-shot classification |  |  |  |  |  |  |  |  |  |  | 
| B | Dollar Street | 52.0 | 51.9 | 51.6 | -0.38 | -0.25 | -0.28 | 50.4 | 49.7 | 49.7 |
| B | GeoDE | 7.8 | 8.3 | 8.7 | -0.24 | -0.26 | -0.25 | 6.1 | 6.7 | 5.4 |
| B | GLDv2 | 65.0 | 61.0 | 59.4 | -0.46 | -0.72 | -0.51 | 61.6 | 59.3 | 56.8 |
| L | Dollar Street | 50.2 | 48.1 | 49.0 | -0.22 | -0.35 | -0.17 | 46.9 | 46.2 | 46.2 |
| L | GeoDE | 6.0 | 5.9 | 4.9 | -0.29 | -0.17 | -0.25 | 4.7 | 4.3 | 3.3 |
| L | GLDv2 | 50.4 | 46.4 | 45.7 | -0.53 | -0.93 | -0.89 | 48.5 | 44.8 | 44.1 |
| H | Dollar Street | 50.0 | 48.6 | 47.4 | -0.15 | -0.13 | -0.20 | 43.9 | 44.2 | 44.1 |
| H | GeoDE | 6.0 | 4.9 | 4.8 | -0.19 | -0.22 | -0.24 | 3.3 | 3.3 | 3.5 |
| H | GLDv2 | 48.1 | 40.1 | 38.8 | -0.52 | -1.34 | -0.80 | 46.0 | 39.0 | 36.8 |{{< /table-caption >}}
> 🔼 표 3은 문화적 다양성 벤치마크에 대한 평가와 확장 법칙을 보여줍니다. 데이터 크기를 100억 개에서 1,000억 개로 늘리면 성능이 크게 향상되는 것을 알 수 있습니다. 표에는 다양한 지표(예: Dollar Street, GeoDE, GLDv2)에 대한 결과가 포함되어 있으며, 모델 크기(B, L, H)에 따른 성능 변화도 보여줍니다. 각 지표에 대한 10억, 100억, 1000억 데이터셋에서의 성능과 확장 법칙(지수 및 한계)을 나타냅니다. 이는 모델의 문화적 다양성 및 다국어 기능에 미치는 데이터 규모의 영향을 분석하는 데 유용한 정보입니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Evaluations and scaling laws on culture diversity benchmarks, where scaling from 10B to 100B examples shows larger benefits.
> </details>

{{< table-caption >}}
| Model | 1B | 10B | 100B |
|---|---|---|---| 
| B | 83.2 | 84.5 | 85.2 |
| L | 88.2 | 86.4 | 85.5 |
| H | 86.8 | 85.0 | 86.6 |{{< /table-caption >}}
> 🔼 표 4는 논문의 4절에서 언급된 성별에 대한 표상 편향을 보여줍니다.  표에 제시된 값은 백분율(%)로, 모델이 무작위로 선택된 이미지를 '여성'이 아닌 '남성' 레이블과 연결하는 빈도를 나타냅니다.  즉, 각 모델이 ImageNet 데이터셋에서 임의로 선택된 이미지에 대해 '남성' 레이블을 '여성' 레이블보다 얼마나 자주 할당하는지 보여줍니다.  데이터셋의 크기에 따른 모델의 성별 표상 편향의 변화를 보여주는 것을 목적으로 합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Representation bias w.r.t. gender (see Section 4). Here, values [%] indicate how often the model prefers to associate a random image with the label “Male” over “Female”.
> </details>

{{< table-caption >}}
| Model | Data Scale | 0-200 | 200-685 | 685-1998 | >1998 |  |  | Disparity |
|---|---|---|---|---|---|---|---|---|
| *0-shot Dollar Street* |  |  |  |  |  |  |  |  |
| B | 1B | 29.4 | 43.9 | 56.5 | 62.0 |  |  | 32.5 |
| B | 10B | 31.6 | 44.0 | 55.4 | 61.5 |  |  | 29.9 |
| B | 100B | 32.0 | 44.3 | 56.3 | 61.0 |  |  | **29.0** |
| L | 1B | 33.7 | 44.7 | 57.3 | 63.4 |  |  | **29.7** |
| L | 10B | 35.7 | 47.8 | 58.7 | 65.5 |  |  | 29.8 |
| L | 100B | 33.7 | 46.6 | 59.5 | 64.1 |  |  | 30.4 |
| H | 1B | 32.3 | 44.9 | 58.4 | 64.5 |  |  | 32.2 |
| H | 10B | 33.9 | 46.3 | 58.6 | 66.9 |  |  | 33.0 |
| H | 100B | 34.1 | 48.2 | 62.2 | 66.1 |  |  | **32.1** |
| *0-shot GeoDE* |  |  |  |  |  |  |  |  |
| B | 1B | 89.4 | 92.1 | 91.8 | 94.1 | 92.5 | 93.4 | 4.7 |
| B | 10B | 88.4 | 91.8 | 91.4 | 94.0 | 92.2 | 93.0 | 5.5 |
| B | 100B | 88.8 | 91.4 | 91.0 | 93.3 | 91.7 | 92.2 | **4.4** |
| L | 1B | 92.0 | 94.0 | 94.0 | 95.2 | 94.2 | 94.9 | 3.2 |
| L | 10B | 91.8 | 94.4 | 94.0 | 95.8 | 94.2 | 94.7 | 4.0 |
| L | 100B | 93.5 | 95.1 | 95.4 | 96.2 | 95.0 | 95.8 | **2.8** |
| H | 1B | 91.5 | 94.4 | 94.7 | 95.2 | 94.1 | 94.5 | 3.6 |
| H | 10B | 93.4 | 95.4 | 95.0 | 96.5 | 95.1 | 95.6 | 3.0 |
| H | 100B | 93.6 | 95.1 | 95.3 | 96.3 | 95.2 | 95.8 | **2.7** |{{< /table-caption >}}
> 🔼 표 5는 10억, 100억, 1000억 개의 예제를 사용하여 사전 훈련된 다양한 SigLIP 모델에 대한 성능 불균형 결과를 보여줍니다. 여기서 불균형은 Dollar Street(소득 수준별)와 GeoDE(지리적 지역별)의 하위 그룹 간 최대 차이에 해당합니다. 1000억 개의 예제를 사용하여 사전 훈련하면 전반적인 불균형이 개선되는 경향이 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Performance disparity results for various SigLIP models pretrained on 100 billion seen examples of 1B, 10B, and 100B datasets. Here, disparity corresponds to the maximum gap across subgroups in Dollar Street (by income level) and GeoDE (by geographic region). Pretraining on 100B examples tends to improve disparity overall.
> </details>

{{< table-caption >}}
|   | Data | Semantics | OCR | Multiling | RS | Avg |
|---|---|---|---|---|---|---|
| ![https://arxiv.org/html/2502.07617/images/snowflake_2744-fe0f.png](https://arxiv.org/html/2502.07617/images/snowflake_2744-fe0f.png) | 1B | 76.0 | 66.8 | 67.0 | 92.3 | 73.6 |
| ![https://arxiv.org/html/2502.07617/images/snowflake_2744-fe0f.png](https://arxiv.org/html/2502.07617/images/snowflake_2744-fe0f.png) | 10B | 75.4 | 65.2 | 66.3 | 91.9 | 72.7 |
| ![https://arxiv.org/html/2502.07617/images/snowflake_2744-fe0f.png](https://arxiv.org/html/2502.07617/images/snowflake_2744-fe0f.png) | 100B | 76.4 | 67.0 | 66.9 | 92.1 | 73.9 |
| ![https://arxiv.org/html/2502.07617/images/fire_1f525.png](https://arxiv.org/html/2502.07617/images/fire_1f525.png) | 1B | 77.1 | 69.5 | 66.9 | 92.0 | 75.1 |
| ![https://arxiv.org/html/2502.07617/images/fire_1f525.png](https://arxiv.org/html/2502.07617/images/fire_1f525.png) | 10B | 76.4 | 66.9 | 66.0 | 91.8 | 73.7 |
| ![https://arxiv.org/html/2502.07617/images/fire_1f525.png](https://arxiv.org/html/2502.07617/images/fire_1f525.png) | 100B | 77.2 | 70.0 | 67.0 | 91.8 | 75.3 |{{< /table-caption >}}
> 🔼 표 6은 비전 언어 모델 사전 훈련에 대한 실험 결과를 보여줍니다.  ViT-L/16 아키텍처를 사용하여 100억 개와 1,000억 개의 이미지-텍스트 쌍으로 사전 훈련된 두 가지 모델에 대해,  각각 비전 부분을 고정한(frozen) 경우와 고정하지 않은(unfrozen) 경우의 성능을 평가한 결과를 보여줍니다.  다양한 하위 작업(downstream tasks)에 대한 종합적인 결과를 보여주며, 상위에는 고정된 비전 모델, 하위에는 고정되지 않은 비전 모델의 결과가 나타나 있습니다.  이 표는 다양한 규모의 데이터셋을 사용한 사전 훈련의 영향을 종합적으로 평가하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 6:  The PaliGemma transfer results of ViT-L/16 models pretrained on 10B and 100B examples, with both frozen (top) and unfrozen (bottom) vision components. Results are aggregated.
> </details>

{{< table-caption >}}
| Concept | Image | 1B | 10B | 100B |
|---|---|---|---|---|
| Street (New York) <sup class="ltx_note_mark">3</sup>By Terabass, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=134418052 | https://arxiv.org/html/2502.07617/x31.png | https://arxiv.org/html/2502.07617/x32.png | https://arxiv.org/html/2502.07617/x33.png | https://arxiv.org/html/2502.07617/x34.png |
| Pub (London) <sup class="ltx_note_mark">4</sup>By Ricardalovesmonuments - Own work, CC BY-SA 4.0, https://commons.wikimedia.org/w/index.php?curid=122810839 | https://arxiv.org/html/2502.07617/x35.png | https://arxiv.org/html/2502.07617/x36.png | https://arxiv.org/html/2502.07617/x37.png | https://arxiv.org/html/2502.07617/x38.png |
| Bison (Yellowstone) <sup class="ltx_note_mark">5</sup>Source: Yellowstone National Park, https://www.yellowstonenationalparklodges.com/connect/yellowstone-hot-spot/yellowstone-where-the-bison-roam/ | https://arxiv.org/html/2502.07617/x39.png | https://arxiv.org/html/2502.07617/x40.png | https://arxiv.org/html/2502.07617/x41.png | https://arxiv.org/html/2502.07617/x42.png |
| Igorot Dance (Igorot) <sup class="ltx_note_mark">6</sup>Source: Itogon, https://itogon.wordpress.com/2012/04/26/book-goes-to-heart-of-igorot-people/ | https://arxiv.org/html/2502.07617/x43.png | https://arxiv.org/html/2502.07617/x44.png | https://arxiv.org/html/2502.07617/x45.png | https://arxiv.org/html/2502.07617/x46.png |
| Kathputli Kala Chitra (Hindi) <sup class="ltx_note_mark">7</sup>Source: The Better India, https://thebetterindia.com/57220/journey-indian-handicraft-landscape/ | https://arxiv.org/html/2502.07617/x47.png | https://arxiv.org/html/2502.07617/x48.png | https://arxiv.org/html/2502.07617/x49.png | https://arxiv.org/html/2502.07617/x50.png |
| Igloo (Inuit) <sup class="ltx_note_mark">8</sup>Source: https://commons.wikimedia.org/w/index.php?curid=3648025 | https://arxiv.org/html/2502.07617/x51.png | https://arxiv.org/html/2502.07617/x52.png | https://arxiv.org/html/2502.07617/x53.png | https://arxiv.org/html/2502.07617/x54.png |
| Pohela Boishakh (Bengali) <sup class="ltx_note_mark">9</sup>Source: EyeNews, https://www.eyenews.news/english/Today-is-Pahela-Baishakh-the-first-day-of-Bengal-1430/757 | https://arxiv.org/html/2502.07617/x55.png | https://arxiv.org/html/2502.07617/x56.png | https://arxiv.org/html/2502.07617/x57.png | https://arxiv.org/html/2502.07617/x58.png |{{< /table-caption >}}
> 🔼 표 7은 서로 다른 규모의 데이터로 학습된 ViT-L/16 모델의 어텐션 맵 시각화를 보여줍니다. 이미지는 서구 중심 국가와 저자원 언어가 사용되는 국가의 문화를 대표하도록 선택되었습니다. 이 표는 서구 중심적인 문화와 저자원 언어권 문화 모두를 아우르는 다양한 문화적 맥락을 보여주는 이미지에 대한 모델의 초점을 비교 분석하여, 데이터 크기가 모델의 문화적 이해에 미치는 영향을 시각적으로 보여줍니다.  각 이미지에 대한 모델의 어텐션이 데이터 크기에 따라 어떻게 변하는지 보여줌으로써, 모델의 성능 향상과 문화적 다양성 간의 관계를 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 7: The attention map visualization of the ViT-L/16 models trained on different scales of data. Images are selected to represent cultures in Western-centric countries and countries where low-resource languages are spoken.
> </details>

{{< table-caption >}}
Metric|Category|ViT-B/16 1B|ViT-B/16 10B|ViT-B/16 100B|ViT-L/16 1B|ViT-L/16 10B|ViT-L/16 100B|ViT-H/16 1B|ViT-H/16 10B|ViT-H/16 100B
---|---|---|---|---|---|---|---|---|---|---
ImageNet 0-shot Classification|Western|41.21|39.35|39.04|31.23|29.70|28.49|29.60|25.60|24.90
Cifar100 0-shot Classification|Western|36.62|35.87|36.80|25.02|23.75|23.36|23.49|19.79|21.42
Pet 0-shot Classification|Western|25.40|23.71|22.27|14.36|12.46|9.46|10.33|7.47|7.17
ImageNet 10-shot Classification|Western|46.65|45.63|44.74|35.11|34.95|33.71|32.44|29.76|29.34
Cifar100 10-shot Classification|Western|38.73|38.63|39.02|27.50|26.70|25.49|25.76|23.79|24.21
Pet 10-shot Classification|Western|22.95|23.19|22.08|12.32|12.48|11.80|10.85|9.13|8.67
Bird 10-shot Classification|Western|53.80|53.47|53.90|44.05|45.25|44.29|41.65|39.13|36.31
Caltech 10-shot Classification|Western|8.37|8.33|8.23|6.41|7.40|7.53|5.70|6.02|8.93
Cars 10-shot Classification|Western|18.29|16.79|17.60|11.14|11.33|11.47|11.32|10.30|9.60
Colorectal 10-shot Classification|Western|26.53|29.23|27.00|24.00|23.53|22.57|25.17|26.17|25.87
DTD 10-shot Classification|Western|29.73|30.85|30.90|28.46|27.07|27.93|29.20|26.12|26.76
COCO Image-Text 0-shot Retrieval|Western|56.46|51.62|53.44|49.70|47.18|45.28|48.62|42.04|42.48
COCO Text-Image 0-shot Retrieval|Western|70.90|68.84|70.01|68.16|64.32|62.51|64.86|60.32|59.29
Flickr Image-Text 0-shot Retrieval|Western|24.20|21.20|21.10|20.40|15.50|16.60|16.80|13.50|13.90
Flickr Text-Image 0-shot Retrieval|Western|43.12|40.26|40.42|39.94|32.32|32.52|34.26|28.46|28.00
Dollar Street 0-shot Classification|Culture|52.04|51.88|51.60|50.23|48.10|49.03|50.00|48.58|47.35
Dollar Street 10-shot Classification|Culture|77.69|75.81|72.12|63.56|64.09|58.29|64.60|59.10|53.69
GeoDE 0-shot Classification|Culture|7.85|8.27|8.65|6.01|5.90|4.88|5.99|4.87|4.81
GeoDE/country 10-shot Classification|Culture|72.75|71.47|71.36|61.94|62.31|57.85|56.94|50.22|47.55
GeoDE/region 10-shot Classification|Culture|61.09|60.80|59.18|54.21|53.59|48.29|54.56|47.63|44.68
GLDv2 0-shot Classification|Culture|65.05|60.96|59.40|50.39|46.37|45.72|48.05|40.08|38.78
Representation Bias|Fairness|33.15|34.54|35.21|38.18|36.35|35.51|36.76|35.01|36.61
Income 0-200 Classification|Fairness|70.57|68.43|67.97|66.30|64.35|66.30|67.69|66.11|65.92
Income 200-285 Classification|Fairness|56.07|55.98|55.70|55.33|52.18|53.38|55.14|53.66|51.81
Income 285-685 Classification|Fairness|43.45|44.57|43.73|42.71|41.32|40.48|41.60|41.41|37.79
Income >1998 Classification|Fairness|38.05|38.51|38.98|36.56|34.51|35.91|35.53|33.12|33.86
GeoDE: Africa|Fairness|10.58|11.56|11.15|7.99|8.24|6.55|8.46|6.56|6.40
GeoDE: Americas|Fairness|7.94|8.16|8.58|6.03|5.57|4.92|5.60|4.57|4.86
GeoDE: EastAsia|Fairness|8.15|8.57|8.99|5.98|5.96|4.56|5.30|5.01|4.68
GeoDE: Europe|Fairness|5.92|6.02|6.75|4.81|4.20|3.75|4.83|3.53|3.75
GeoDE: SouthEastAsia|Fairness|7.51|7.81|8.26|5.78|5.78|5.02|5.86|4.89|4.76
GeoDE: WestAsia|Fairness|6.57|7.01|7.85|5.11|5.30|4.19|5.50|4.42|4.19
XM3600 Image-Text: Arabic|Multiling|61.78|53.42|53.36|53.58|45.00|44.56|52.25|41.64|41.00
XM3600 Image-Text: Bengali|Multiling|95.69|80.64|77.06|90.81|66.36|63.75|88.17|61.22|56.69
XM3600 Image-Text: Czech|Multiling|60.78|51.89|50.83|52.31|43.81|42.22|49.94|40.11|39.44
XM3600 Image-Text: Danish|Multiling|55.58|45.39|45.75|45.08|35.06|31.00|43.03|29.92|28.75
XM3600 Image-Text: German|Multiling|39.47|31.53|31.78|30.61|24.28|24.03|29.17|22.75|21.89
XM3600 Image-Text: Greek|Multiling|74.36|63.00|61.86|67.86|53.64|50.14|65.67|49.50|47.33
XM3600 Image-Text: English|Multiling|56.53|55.03|55.50|54.14|52.42|51.67|53.22|51.42|49.64
XM3600 Image-Text: Spanish|Multiling|49.17|42.94|44.22|41.56|38.44|35.81|40.03|33.89|34.28
XM3600 Image-Text: Persian|Multiling|58.94|51.17|51.58|49.64|38.97|40.17|46.61|33.72|34.06
XM3600 Image-Text: Finnish|Multiling|70.64|53.83|53.61|59.25|42.67|39.06|57.39|34.83|32.86
XM3600 Image-Text: Filipino|Multiling|87.86|82.06|81.92|82.72|72.86|71.36|81.31|66.14|63.03
XM3600 Image-Text: French|Multiling|47.08|38.92|39.06|39.08|31.78|29.92|36.58|28.53|28.19
XM3600 Image-Text: Hindi|Multiling|83.53|74.78|72.39|77.67|65.67|63.47|76.92|62.33|60.64
XM3600 Image-Text: Croatian|Multiling|64.53|53.28|51.33|53.08|37.94|35.78|47.81|32.44|30.44
XM3600 Image-Text: Hungarian|Multiling|64.50|49.06|47.53|53.81|38.64|34.42|51.22|32.67|30.36
XM3600 Image-Text: Indonesian|Multiling|44.81|38.14|37.08|35.83|28.47|28.53|33.39|24.86|25.33
XM3600 Image-Text: Italian|Multiling|48.58|41.00|40.86|38.42|33.33|30.97|36.47|29.64|28.89
XM3600 Image-Text: Hebrew|Multiling|67.06|50.28|49.86|56.75|39.44|35.72|52.03|33.86|30.81
XM3600 Image-Text: Japanese|Multiling|67.36|55.67|55.42|59.00|45.42|44.97|58.47|42.22|37.94
XM3600 Image-Text: Korean|Multiling|58.64|49.61|49.53|50.75|40.33|38.31|46.81|35.39|35.08
XM3600 Image-Text: Maori|Multiling|99.61|99.50|99.42|99.58|99.22|99.25|99.31|98.92|99.17
XM3600 Image-Text: Dutch|Multiling|53.97|47.47|48.78|47.11|41.14|38.39|44.56|38.06|37.44
XM3600 Image-Text: Norwegian|Multiling|56.56|46.78|47.89|45.33|36.11|34.28|43.39|31.81|30.19
XM3600 Image-Text: Polish|Multiling|53.97|44.89|44.22|45.97|35.50|34.11|41.75|33.00|31.06
XM3600 Image-Text: Portuguese|Multiling|51.03|44.19|44.39|43.33|36.03|34.56|41.14|32.69|32.28
XM3600 Image-Text: Quechua|Multiling|95.53|94.08|93.89|94.64|93.53|93.92|94.58|93.06|92.78
XM3600 Image-Text: Romanian|Multiling|64.56|51.39|52.03|52.19|38.31|35.39|47.92|32.36|30.11
XM3600 Image-Text: Russian|Multiling|51.56|42.36|42.28|42.78|35.14|33.22|41.19|31.97|30.31
XM3600 Image-Text: Swedish|Multiling|54.03|44.25|45.69|44.50|34.94|34.78|40.69|31.14|30.78
XM3600 Image-Text: Swahili|Multiling|92.14|88.17|88.72|89.94|81.33|79.47|88.92|76.86|74.14
XM3600 Image-Text: Telugu|Multiling|98.06|87.08|80.53|96.08|76.67|69.69|96.36|73.08|65.31
XM3600 Image-Text: Thai|Multiling|79.33|68.67|67.47|72.61|59.47|58.86|71.25|56.86|52.78
XM3600 Image-Text: Turkish|Multiling|60.33|50.03|50.06|52.78|40.72|39.72|48.56|36.56|34.94
XM3600 Image-Text: Ukrainian|Multiling|62.39|52.25|49.78|55.19|41.25|37.83|52.75|36.94|33.25
XM3600 Image-Text: Vietnamese|Multiling|54.31|45.33|45.22|43.19|34.00|32.44|40.75|29.06|29.08
XM3600 Text-Image: Arabic|Multiling|73.77|67.79|68.49|67.49|59.74|59.86|65.87|56.22|54.91
XM3600 Text-Image: Bengali|Multiling|97.19|89.25|89.53|95.17|79.72|77.31|94.22|76.36|72.42
XM3600 Text-Image: Czech|Multiling|71.81|64.49|65.48|65.52|58.57|58.18|63.59|55.79|55.07
XM3600 Text-Image: Danish|Multiling|68.23|59.97|61.73|60.01|51.18|49.50|56.72|46.53|45.46
XM3600 Text-Image: German|Multiling|55.15|47.80|49.18|45.85|39.88|39.75|43.80|36.56|36.99
XM3600 Text-Image: Greek|Multiling|82.61|75.69|75.71|77.96|69.11|67.35|75.68|65.45|64.10
XM3600 Text-Image: English|Multiling|62.32|59.41|60.78|58.97|57.57|56.32|58.15|56.40|55.82
XM3600 Text-Image: Spanish|Multiling|57.35|52.74|55.49|52.64|49.06|48.31|51.24|47.27|46.62
XM3600 Text-Image: Persian|Multiling|71.80|65.18|65.58|62.65|55.06|56.09|59.79|52.93|49.69
XM3600 Text-Image: Finnish|Multiling|81.00|70.80|68.28|72.96|59.11|56.24|70.79|51.07|49.35
XM3600 Text-Image: Filipino|Multiling|93.60|90.28|91.07|90.89|83.98|83.70|89.55|80.61|77.92
XM3600 Text-Image: French|Multiling|56.70|50.23|50.57|48.33|43.31|42.10|47.52|40.48|39.96
XM3600 Text-Image: Hindi|Multiling|91.01|86.55|86.09|87.43|81.38|80.01|87.71|79.21|78.22
XM3600 Text-Image: Croatian|Multiling|75.52|67.53|66.85|66.68|54.42|54.22|63.21|50.71|48.53
XM3600 Text-Image: Hungarian|Multiling|74.24|63.83|63.53|66.49|53.73|50.75|64.26|48.31|45.72
XM3600 Text-Image: Indonesian|Multiling|60.08|52.90|53.96|50.28|44.05|43.97|49.27|41.45|40.81
XM3600 Text-Image: Italian|Multiling|57.90|51.51|52.08|47.96|42.80|42.60|48.03|40.62|40.34
XM3600 Text-Image: Hebrew|Multiling|76.50|64.76|62.76|69.11|56.25|54.14|65.88|51.49|49.99
XM3600 Text-Image: Japanese|Multiling|76.74|69.20|68.99|69.56|62.34|58.44|69.16|57.06|54.78
XM3600 Text-Image: Korean|Multiling|70.82|64.88|67.23|64.52|56.76|56.51|61.52|53.57|52.67
XM3600 Text-Image: Maori|Multiling|99.78|99.78|99.78|99.73|99.56|99.62|99.75|99.67|99.51
XM3600 Text-Image: Dutch|Multiling|63.50|59.25|59.05|57.41|52.02|51.48|55.49|49.88|49.10
XM3600 Text-Image: Norwegian|Multiling|70.36|63.58|63.44|61.54|53.81|52.99|60.04|49.16|48.20
XM3600 Text-Image: Polish|Multiling|63.73|57.39|57.71|56.06|47.92|47.09|53.28|45.05|44.49
XM3600 Text-Image: Portuguese|Multiling|62.16|57.16|57.93|54.54|49.48|48.72|52.44|47.48|46.64
XM3600 Text-Image: Quechua|Multiling|98.46|97.94|97.85|97.88|98.14|98.04|98.18|98.28|98.26
XM3600 Text-Image: Romanian|Multiling|74.48|65.48|65.11|65.20|54.05|52.41|61.69|48.77|47.09
XM3600 Text-Image: Russian|Multiling|61.65|53.83|54.17|53.47|47.58|45.36|51.60|43.58|43.08
XM3600 Text-Image: Swedish|Multiling|66.11|59.05|60.50|58.78|50.72|51.82|55.34|47.66|47.93
XM3600 Text-Image: Swahili|Multiling|96.30|94.01|94.73|94.55|90.09|89.57|93.85|87.47|85.67
XM3600 Text-Image: Telugu|Multiling|98.76|92.69|90.40|97.76|87.47|83.03|98.18|84.44|79.57
XM3600 Text-Image: Thai|Multiling|86.81|80.38|79.47|81.83|74.60|73.67|82.21|73.31|69.67
XM3600 Text-Image: Turkish|Multiling|72.31|65.24|65.17|65.21|55.12|56.70|62.35|53.59|52.19
XM3600 Text-Image: Ukrainian|Multiling|75.01|66.08|65.35|68.84|57.74|55.32|66.07|54.18|50.84
XM3600 Text-Image: Vietnamese|Multiling|70.38|64.82|64.64|61.84|54.00|53.39|58.46|50.29|48.76
Avg Western 0-shot Classification|Western|34.41|32.98|32.70|23.54|21.97|20.44|21.14|17.62|17.83
Avg Western 10-shot Classification|Western|30.63|30.77|30.43|23.62|23.59|23.10|22.76|21.30|21.21
Avg Western 0-shot Retrieval|Western|48.67|45.48|46.24|44.55|39.83|39.23|41.13|36.08|35.92
Avg Western Classification|Western|31.66|31.37|31.05|23.60|23.15|22.37|22.32|20.30|20.29
Avg Dollar Street Classification|Culture|64.87|63.85|61.86|56.89|56.09|53.66|57.30|53.84|50.52
Avg GeoDE Classification|Culture|47.23|46.85|46.39|40.72|40.60|37.01|39.16|34.24|32.35
Avg Income Classification|Fairness|52.03|51.87|51.59|50.22|48.09|49.02|49.99|48.57|47.35
Avg Geographic Classification|Fairness|7.78|8.19|8.59|5.95|5.84|4.83|5.92|4.83|4.77
Avg Demography Classification|Fairness|25.24|24.43|27.49|24.91|26.47|25.50|25.50|25.13|27.22
Avg Multiling: Low-Resource Lang|Multiling|91.22|84.27|83.16|87.73|77.14|75.01|86.58|73.69|70.93
Avg Multiling: High-Resource Lang|Multiling|63.66|55.42|55.53|55.54|46.75|45.43|53.38|43.11|41.81
Average Western-centric| |36.20|35.13|35.10|29.19|27.60|26.87|27.34|24.51|24.46
Average Cultural Diversity| |56.08|54.87|53.72|47.72|46.72|44.01|46.69|41.75|39.48
Average Fairness| |25.44|25.46|26.08|23.87|23.36|23.01|23.88|22.80|22.70
Average Multilinguality| |65.23|56.09|55.61|57.52|47.23|45.40|55.38|43.33|41.63{{< /table-caption >}}
> 🔼 표 8은 서로 다른 크기(10억, 100억, 1000억 개)의 데이터셋으로 학습된 ViT-B/L/H 모델에 대한 자세한 평가 결과를 보여줍니다.  '표현 편향(Representation Bias)'을 제외한 모든 지표는 오류율로 측정되며, 낮을수록 성능이 좋음을 의미합니다. '표현 편향'은 불균형도(disparity)로 측정되며, 값이 낮을수록 좋습니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Detailed evaluation results of ViT-B/L/H models on 1/10/100 billion scale datasets. All metrics are measured by error rate, with the exception of “Representation Bias”, which is measured by disparity, where lower values are better.
> </details>

{{< table-caption >}}
| Metric | Frozen ViT |  |  | Unfrozen ViT |  |  |
|---|---|---|---|---|---|---|
|  | 1B Data | 10B Data | 100B Data | 1B Data | 10B Data | 100B Data |
|---|---|---|---|---|---|---|
| COCOcap | 134.6 | 132.9 | 134.4 | 135.0 | 132.1 | 134.0 |
| NoCaps | 114.1 | 110.5 | 112.8 | 113.4 | 111.4 | 113.3 |
| COCO-35L (avg35) | 107.6 | 105.9 | 108.0 | 107.7 | 106.8 | 107.8 |
| COCO-35L (avg34) | 106.9 | 105.2 | 107.3 | 107.0 | 106.0 | 107.1 |
| COCO-35L (en) | 130.6 | 130.4 | 133.4 | 132.4 | 132.5 | 133.4 |
| XM3600 (en) | 75.5 | 74.9 | 75.2 | 75.3 | 75.4 | 76.0 |
| XM3600 (avg36) | 37.9 | 36.9 | 38.0 | 37.7 | 37.5 | 38.0 |
| Screen2Words | 108.9 | 107.5 | 109.9 | 105.0 | 105.3 | 105.5 |
| TextCaps | 86.5 | 79.3 | 93.2 | 87.6 | 81.8 | 83.8 |
| SciCap | 149.7 | 146.9 | 150.0 | 146.1 | 144.6 | 147.1 |
| WidgetCap | 120.1 | 109.6 | 117.9 | 113.3 | 108.4 | 114.9 |
| VQAv2 (minival) | 79.4 | 78.8 | 79.8 | 79.2 | 78.6 | 78.6 |
| OKVQA | 60.4 | 59.6 | 59.7 | 59.6 | 59.7 | 59.9 |
| AOKVQA-MC (val) | 74.2 | 72.7 | 73.0 | 73.0 | 72.7 | 74.2 |
| AOKVQA-DA (val) | 58.5 | 56.8 | 57.3 | 59.1 | 57.7 | 57.9 |
| GQA | 63.4 | 63.5 | 63.6 | 63.8 | 63.0 | 63.5 |
| NLVR2 | 87.5 | 86.7 | 87.2 | 86.4 | 86.4 | 87.0 |
| MARVL (avg5) | 76.7 | 76.2 | 76.6 | 76.3 | 76.8 | 77.0 |
| AI2D | 69.8 | 70.0 | 70.6 | 68.2 | 68.5 | 68.6 |
| ScienceQA | 95.4 | 94.9 | 94.4 | 94.5 | 92.9 | 94.7 |
| RSVQA-lr | 93.0 | 92.4 | 92.3 | 93.6 | 92.8 | 93.0 |
| RSVQA-hr (test) | 92.5 | 92.5 | 92.7 | 92.6 | 92.6 | 92.6 |
| RSVQA-hr (test2) | 90.4 | 90.4 | 90.5 | 90.5 | 90.4 | 90.6 |
| ChartQA (avg) | 45.1 | 43.6 | 45.0 | 41.4 | 40.3 | 42.5 |
| ChartQA (human) | 31.8 | 31.8 | 32.6 | 29.8 | 28.3 | 30.5 |
| ChartQA (aug) | 58.5 | 55.4 | 57.4 | 53.0 | 52.3 | 54.5 |
| VizWizVQA (val) | 72.3 | 71.2 | 72.8 | 72.0 | 71.6 | 71.9 |
| TallyQA (simple) | 76.6 | 75.7 | 75.9 | 76.6 | 75.7 | 76.9 |
| TallyQA (complex) | 65.0 | 65 | 65.5 | 65.4 | 64.5 | 65.3 |
| CountBenchQA | 68.2 | 69.0 | 67.3 | 60.6 | 61.2 | 63.7 |
| OCR-VQA | 68.3 | 67.5 | 68.2 | 66.9 | 66.0 | 67.1 |
| TextVQA (val) | 44.5 | 41.4 | 44.7 | 41.2 | 40.4 | 41.2 |
| DocVQA (val) | 25.0 | 23.5 | 25.8 | 23.4 | 21.7 | 23.1 |
| InfoVQA (val) | 22.3 | 22.2 | 23 | 21.4 | 22.0 | 22.1 |
| ST-VQA (val) | 46.6 | 42.8 | 46.7 | 43.5 | 40.1 | 43.2 |
| xGQA (avg8) | 55.2 | 55.2 | 55 | 55.6 | 54.5 | 54.8 |
| xGQA (avg7) | 54.1 | 54.0 | 53.8 | 54.5 | 53.3 | 53.6 |
| RefCOCO (testA) | 67.4 | 67.5 | 67.9 | 64.5 | 64.2 | 65.1 |
| RefCOCO (testB) | 62.7 | 62.0 | 63.8 | 60.2 | 59.6 | 60.9 |
| RefCOCO+ (testA) | 63 | 62.7 | 63.5 | 60.2 | 59.9 | 60.3 |
| RefCOCO+ (testB) | 55.6 | 54.9 | 56.2 | 53.2 | 52.5 | 53.3 |
| RefCOCOg (test) | 59.1 | 58.9 | 60 | 56.5 | 56.1 | 57.2 |
| Avg Semantics | 77.1 | 76.4 | 77.2 | 76.0 | 75.4 | 76.4 |
| Avg OCR | 69.5 | 66.9 | 70.0 | 66.8 | 65.2 | 67.0 |
| Avg Multilinguality | 66.9 | 66.0 | 67.0 | 67.0 | 66.3 | 66.9 |
| Avg Remote Sensing | 92.0 | 91.8 | 91.8 | 92.3 | 91.9 | 92.1 |
| Avg | 75.1 | 73.7 | 75.3 | 73.6 | 72.7 | 73.9 |{{< /table-caption >}}
> 🔼 표 9는 대조적으로 훈련된 비전 모델(ViT-L/16)을 생성 비전-언어 모델(PaliGemma)로 전이 학습하는 실험 결과를 보여줍니다. 비전 모델은 10억, 100억, 1000억 개의 원시 데이터로 각각 훈련되었으며, PaliGemma의 기본 미세 조정 설정을 사용했습니다. 표에는 동결 및 동결 해제 설정 모두에 대한 세부적인 결과가 포함되어 있습니다. 각 작업에 대한 구체적인 수치가 보고됩니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Detailed evaluation results of the transferability of contrastively trained vision models (ViT-L/16) to generative vision-language models (PaliGemma), with both frozen and unfrozen setups. Task-specific Numbers are reported for vision models trained on 1 billion, 10 billion and 100 billion raw data respectively, using PaliGemma’s default fine-tuning configuration.
> </details>

{{< table-caption >}}
Metric|Filter|1B|5B|10B|20B|30B
---|---|---|---|---|---|---
ImageNet 0-shot Classification|Baseline (en)|34.67|28.17|26.68|26.15|24.32
ImageNet 0-shot Classification|CLIP filtered|31.18|26.76|25.14|24.39|23.90
ImageNet 0-shot Classification|Other filtered|34.50|29.52|28.13|26.70|26.45
Cifar100 0-shot Classification|Baseline (en)|33.05|26.08|24.37|24.52|23.99
Cifar100 0-shot Classification|CLIP filtered|31.69|26.96|25.37|24.68|25.76
Cifar100 0-shot Classification|Other filtered|36.07|35.27|29.95|32.58|30.78
Pet 0-shot Classification|Baseline (en)|17.25|11.99|11.69|9.13|8.72
Pet 0-shot Classification|CLIP filtered|13.68|10.49|8.78|8.59|8.23
Pet 0-shot Classification|Other filtered|14.04|9.62|8.99|7.28|6.62
ImageNet 10-shot Classification|Baseline (en)|42.41|35.25|33.17|33.17|30.68
ImageNet 10-shot Classification|CLIP filtered|38.57|32.53|30.60|29.20|28.72
ImageNet 10-shot Classification|Other filtered|38.32|32.32|30.42|29.05|28.46
Cifar100 10-shot Classification|Baseline (en)|36.61|30.02|27.39|27.23|26.82
Cifar100 10-shot Classification|CLIP filtered|32.83|28.44|28.04|26.20|27.40
Cifar100 10-shot Classification|Other filtered|35.30|35.56|31.18|32.26|31.79
Pet 10-shot Classification|Baseline (en)|22.95|16.93|15.32|15.26|11.72
Pet 10-shot Classification|CLIP filtered|17.31|11.72|10.44|8.97|8.83
Pet 10-shot Classification|Other filtered|14.15|10.38|9.08|7.63|7.52
Bird 10-shot Classification|Baseline (en)|41.18|31.69|29.91|29.60|27.37
Bird 10-shot Classification|CLIP filtered|32.38|25.20|23.85|22.21|21.95
Bird 10-shot Classification|Other filtered|34.57|27.01|26.30|24.65|23.73
Caltech 10-shot Classification|Baseline (en)|10.45|9.94|9.34|9.63|9.60
Caltech 10-shot Classification|CLIP filtered|11.18|10.68|10.44|10.50|10.50
Caltech 10-shot Classification|Other filtered|8.97|9.25|9.01|8.30|9.06
Cars 10-shot Classification|Baseline (en)|16.47|11.03|10.16|10.05|8.94
Cars 10-shot Classification|CLIP filtered|13.07|9.70|8.89|7.75|8.01
Cars 10-shot Classification|Other filtered|16.84|13.07|12.52|11.30|11.30
Colorectal Histology 10-shot Classification|Baseline (en)|27.80|27.17|24.77|27.03|25.33
Colorectal Histology 10-shot Classification|CLIP filtered|25.97|22.90|20.80|24.23|27.13
Colorectal Histology 10-shot Classification|Other filtered|24.53|24.70|25.47|27.10|26.53
DTD 10-shot Classification|Baseline (en)|31.12|26.91|26.33|26.97|26.86
DTD 10-shot Classification|CLIP filtered|29.20|25.69|25.37|23.51|23.72
DTD 10-shot Classification|Other filtered|28.09|26.81|24.73|24.52|23.56
COCO Image-Text 0-shot Retrieval|Baseline (en)|46.80|40.28|39.30|39.18|37.04
COCO Image-Text 0-shot Retrieval|CLIP filtered|41.06|36.04|36.48|34.84|34.02
COCO Image-Text 0-shot Retrieval|Other filtered|42.92|38.32|36.80|35.96|36.24
COCO Text-Image 0-shot Retrieval|Baseline (en)|62.26|56.78|54.78|55.22|53.20
COCO Text-Image 0-shot Retrieval|CLIP filtered|59.11|55.27|54.45|53.12|53.03
COCO Text-Image 0-shot Retrieval|Other filtered|60.53|56.01|54.60|53.23|53.27
Flickr Image-Text 0-shot Retrieval|Baseline (en)|16.70|11.30|11.30|11.30|10.90
Flickr Image-Text 0-shot Retrieval|CLIP filtered|14.80|9.90|9.70|9.60|8.90
Flickr Image-Text 0-shot Retrieval|Other filtered|16.70|13.80|12.60|13.10|12.00
Flickr Text-Image 0-shot Retrieval|Baseline (en)|32.26|24.78|24.74|24.90|22.66
Flickr Text-Image 0-shot Retrieval|CLIP filtered|29.52|24.98|23.34|22.12|22.02
Flickr Text-Image 0-shot Retrieval|Other filtered|32.84|27.18|26.48|24.82|24.32
Dollar Street 0-shot Classification|Baseline (en)|54.67|50.44|49.81|49.98|49.37
Dollar Street 0-shot Classification|CLIP filtered|53.71|52.58|51.88|50.63|51.44
Dollar Street 0-shot Classification|Other filtered|50.23|47.63|47.86|47.45|47.08
Dollar Street 10-shot Classification|Baseline (en)|84.87|79.27|77.18|76.21|72.54
Dollar Street 10-shot Classification|CLIP filtered|88.86|84.59|84.73|82.80|82.80
Dollar Street 10-shot Classification|Other filtered|90.16|89.46|87.91|88.72|87.77
GeoDE 0-shot Classification|Baseline (en)|8.98|6.48|6.43|6.26|6.23
GeoDE 0-shot Classification|CLIP filtered|9.64|8.54|8.02|7.42|7.22
GeoDE 0-shot Classification|Other filtered|9.50|7.69|7.50|7.50|7.53
GeoDE (country) 10-shot Classification|Baseline (en)|84.29|77.28|73.22|73.37|68.85
GeoDE (country) 10-shot Classification|CLIP filtered|85.82|81.98|80.11|78.08|78.24
GeoDE (country) 10-shot Classification|Other filtered|91.37|89.52|88.30|87.65|86.76
GeoDE (region) 10-shot Classification|Baseline (en)|66.67|61.66|57.71|58.77|55.78
GeoDE (region) 10-shot Classification|CLIP filtered|70.68|68.16|66.99|64.81|63.68
GeoDE (region) 10-shot Classification|Other filtered|75.82|72.39|72.95|72.13|71.27
GLDv2 0-shot Classification|Baseline (en)|65.50|53.18|50.13|49.48|44.16
GLDv2 0-shot Classification|CLIP filtered|61.15|52.46|49.55|47.41|46.37
GLDv2 0-shot Classification|Other filtered|80.87|74.06|72.37|72.37|70.17
Representation Bias|Baseline (en)|33.89|28.22|36.00|33.52|30.96
Representation Bias|CLIP filtered|11.46|19.14|20.03|26.57|14.05
Representation Bias|Other filtered|39.31|36.44|39.01|40.57|35.51
Income 0-200 Classification|Baseline (en)|71.31|67.22|68.34|67.50|67.04
Income 0-200 Classification|CLIP filtered|69.36|69.36|68.71|66.67|67.87
Income 0-200 Classification|Other filtered|69.36|67.97|65.65|66.11|66.67
Income 200-285 Classification|Baseline (en)|60.15|55.33|54.87|54.49|55.33
Income 200-285 Classification|CLIP filtered|58.48|57.46|56.63|54.59|56.63
Income 200-285 Classification|Other filtered|54.22|50.88|52.64|51.16|51.16
Income &gt;1998 Classification|Baseline (en)|40.56|36.19|34.98|35.44|34.33
Income &gt;1998 Classification|CLIP filtered|40.56|38.70|37.95|38.33|37.77
Income &gt;1998 Classification|Other filtered|36.37|32.56|33.77|33.12|32.74
Africa|Baseline (en)|11.51|8.19|7.88|7.72|7.85
Africa|CLIP filtered|11.00|9.74|9.37|9.28|8.44
Africa|Other filtered|12.04|9.97|9.51|9.85|9.88
Americas|Baseline (en)|8.59|6.74|6.15|6.37|6.27
Americas|CLIP filtered|9.57|8.60|8.30|7.29|7.16
Americas|Other filtered|9.63|7.68|7.32|7.53|7.48
EastAsia|Baseline (en)|9.90|7.10|7.37|7.29|6.71
EastAsia|CLIP filtered|10.45|9.34|8.88|7.72|7.67
EastAsia|Other filtered|10.52|8.92|8.63|8.21|8.48
Europe|Baseline (en)|6.75|4.82|5.29|5.01|5.17
Europe|CLIP filtered|7.71|6.89|6.52|5.52|6.01
Europe|Other filtered|7.29|5.62|5.57|5.45|5.51
SouthEastAsia|Baseline (en)|8.69|6.23|6.00|5.77|6.01
SouthEastAsia|CLIP filtered|9.74|8.47|7.40|7.74|7.32
SouthEastAsia|Other filtered|8.89|7.28|7.47|7.16|7.11
WestAsia|Baseline (en)|8.14|5.61|5.64|5.17|5.08
WestAsia|CLIP filtered|9.24|8.16|7.59|6.75|6.52
WestAsia|Other filtered|8.32|6.34|6.17|6.47|6.35
Perceived Gender|Baseline (en)|8.41|6.42|5.78|5.98|5.64
Perceived Gender|CLIP filtered|8.43|7.63|8.08|7.56|6.35
Perceived Gender|Other filtered|13.08|10.64|11.13|11.02|9.55
Perceived Race|Baseline (en)|37.87|44.74|43.93|48.30|44.95
Perceived Race|CLIP filtered|33.08|40.63|38.98|41.89|43.04
Perceived Race|Other filtered|53.52|52.46|53.21|52.83|56.43
Average Western 0-shot Classification|Baseline (en)|28.33|22.08|20.91|19.93|19.01
Average Western 0-shot Classification|CLIP filtered|25.52|21.40|19.76|19.22|19.30
Average Western 0-shot Classification|Other filtered|28.20|24.81|22.36|22.18|21.28
Average Western 10-shot Classification|Baseline (en)|28.62|23.62|22.05|22.37|20.92
Average Western 10-shot Classification|CLIP filtered|25.06|20.86|19.80|19.07|19.53
Average Western 10-shot Classification|Other filtered|25.10|22.39|21.09|20.60|20.25
Average Western 0-shot Retrieval|Baseline (en)|39.50|33.29|32.53|32.65|30.95
Average Western 0-shot Retrieval|CLIP filtered|36.12|31.55|30.99|29.92|29.49
Average Western 0-shot Retrieval|Other filtered|38.25|33.83|32.62|31.78|31.46
Average Western Classification|Baseline (en)|28.54|23.20|21.74|21.70|20.40
Average Western Classification|CLIP filtered|25.19|21.01|19.79|19.11|19.47
Average Western Classification|Other filtered|25.94|23.05|21.43|21.03|20.53
Average Dollar Street Classification|Baseline (en)|69.77|64.86|63.50|63.09|60.96
Average Dollar Street Classification|CLIP filtered|71.29|68.58|68.30|66.71|67.12
Average Dollar Street Classification|Other filtered|70.19|68.55|67.89|68.08|67.42
Average GeoDE Classification|Baseline (en)|53.32|48.48|45.79|46.13|43.62
Average GeoDE Classification|CLIP filtered|55.38|52.89|51.71|50.10|49.71
Average GeoDE Classification|Other filtered|58.90|56.54|56.25|55.76|55.18
Average Income Classification|Baseline (en)|54.66|50.43|49.81|49.97|49.36
Average Income Classification|CLIP filtered|53.71|52.57|51.87|50.62|51.43
Average Income Classification|Other filtered|50.22|47.62|47.86|47.44|47.07
Average Geographic Classification|Baseline (en)|8.93|6.44|6.39|6.22|6.18
Average Geographic Classification|CLIP filtered|9.62|8.53|8.01|7.39|7.19
Average Geographic Classification|Other filtered|9.45|7.63|7.44|7.45|7.47
Average Demography Classification|Baseline (en)|23.14|25.58|24.86|27.14|25.30
Average Demography Classification|CLIP filtered|20.76|24.13|23.53|24.72|24.70
Average Demography Classification|Other filtered|33.30|31.55|32.17|31.93|32.99
Average Western-centric|Baseline (en)|31.47|25.89|24.62|24.62|23.21
Average Western-centric|CLIP filtered|28.10|23.82|22.78|21.99|22.14
Average Western-centric|Other filtered|29.22|25.92|24.42|23.90|23.44
Average Cultural Diversity|Baseline (en)|60.83|54.72|52.41|52.34|49.49
Average Cultural Diversity|CLIP filtered|61.64|58.05|56.88|55.19|54.96
Average Cultural Diversity|Other filtered|66.33|63.46|62.82|62.64|61.76
Average Fairness|Baseline (en)|26.54|24.30|23.94|24.29|23.76
Average Fairness|CLIP filtered|26.17|25.81|25.22|24.69|24.85
Average Fairness|Other filtered|27.02|24.95|25.04|24.86|24.92{{< /table-caption >}}
> 🔼 표 10은 ViT-L/16 모델에 대한 데이터 품질 필터링의 상세한 평가 결과를 보여줍니다. 모든 평가는 50억 개의 이미지-텍스트 쌍 데이터셋과 다양한 수의 학습된 예시를 사용하여 수행되었습니다.  '표상 편향(Representation Bias)'을 제외한 모든 지표는 오류율로 측정되며, '표상 편향'은 차이로 측정됩니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Detailed evaluation results of data quality filtering on ViT-L/16 models. All evaluations are conducted on datasets of 5 billion image-text pairs and across different number of seen examples. All metrics are measured by error rate, with the exception of “Representation Bias”, which is measured by disparity.
> </details>

{{< table-caption >}}
Metric|1B Data|1B Data|10B Data|10B Data|100B Data|100B Data
---|---|---|---|---|---|---
ImageNet 0-shot Classification|31.23|31.39|29.70|30.47|28.49|28.80
Cifar100 0-shot Classification|25.02|24.96|23.75|24.04|23.36|23.51
Pet 0-shot Classification|14.36|13.00|12.46|12.05|9.46|11.23
ImageNet 10-shot Classification|35.11|34.94|34.95|34.99|33.71|33.89
Cifar100 10-shot Classification|27.50|27.82|26.70|26.50|25.49|25.05
Pet 10-shot Classification|12.32|13.71|12.48|15.59|11.80|13.46
Bird 10-shot Classification|44.05|42.75|45.25|45.29|44.29|42.89
Caltech 10-shot Classification|6.41|8.09|7.40|8.97|7.53|8.35
Cars 10-shot Classification|11.14|11.34|11.33|11.54|11.47|11.21
Colorectal Histology 10-shot Classification|24.00|25.50|23.53|24.43|22.57|28.00
DTD 10-shot Classification|28.46|29.31|27.07|27.39|27.93|29.04
COCO Image-Text 0-shot Retrieval|49.70|52.92|47.18|50.28|45.28|45.90
COCO Text-Image 0-shot Retrieval|68.16|67.50|64.32|63.60|62.51|62.16
Flickr Image-Text 0-shot Retrieval|20.40|24.30|15.50|20.30|16.60|16.40
Flickr Text-Image 0-shot Retrieval|39.94|37.88|32.32|32.64|32.52|33.30
Dollar Street 0-shot Classification|50.23|51.16|48.10|49.42|49.03|49.23
Dollar Street 10-shot Classification|63.56|65.04|64.09|65.51|58.29|59.42
GeoDE 0-shot Classification|6.01|6.03|5.90|5.97|4.88|5.42
GeoDE (country) 10-shot Classification|61.94|59.79|62.31|60.52|57.85|53.34
GeoDE (region) 10-shot Classification|54.21|53.99|53.59|53.30|48.29|48.05
GLDv2 0-shot Classification|50.39|51.82|46.37|47.73|45.72|44.29
Representation Bias|38.18|35.21|36.35|32.61|35.51|32.74
Income 0-200 Classification|66.30|67.32|64.35|65.83|66.30|65.37
Income 200-285 Classification|55.33|54.22|52.18|53.48|53.38|53.20
Income 285-685 Classification|42.71|44.75|41.32|42.80|40.48|40.76
Income >1998 Classification|36.56|38.33|34.51|35.53|35.91|37.58
Africa|7.99|8.34|8.24|7.81|6.55|7.46
Americas|6.03|5.51|5.57|5.84|4.92|5.20
EastAsia|5.98|6.07|5.96|5.90|4.56|5.27
Europe|4.81|4.41|4.20|4.23|3.75|4.00
SouthEastAsia|5.78|6.21|5.78|6.15|5.02|5.50
WestAsia|5.11|5.30|5.30|5.67|4.19|4.79
Perceived Gender|5.25|5.27|6.06|5.96|4.97|5.03
Perceived Race|44.57|49.02|46.88|45.89|46.04|47.35
Crossmodal-3600 Image-Text Retrieval: Arabic|53.58|56.44|45.00|45.89|44.56|44.78
Crossmodal-3600 Image-Text Retrieval: Bengali|90.81|76.03|66.36|63.53|63.75|61.47
Crossmodal-3600 Image-Text Retrieval: Czech|52.31|52.81|43.81|43.36|42.22|41.61
Crossmodal-3600 Image-Text Retrieval: Danish|45.08|45.22|35.06|34.81|31.00|32.53
Crossmodal-3600 Image-Text Retrieval: German|30.61|32.00|24.28|24.36|24.03|23.11
Crossmodal-3600 Image-Text Retrieval: Greek|67.86|70.17|53.64|53.42|50.14|51.94
Crossmodal-3600 Image-Text Retrieval: English|54.14|54.58|52.42|51.58|51.67|50.89
Crossmodal-3600 Image-Text Retrieval: Spanish|41.56|43.50|38.44|38.00|35.81|35.89
Crossmodal-3600 Image-Text Retrieval: Persian|49.64|55.33|38.97|41.97|40.17|38.11
Crossmodal-3600 Image-Text Retrieval: Finnish|59.25|60.11|42.67|42.42|39.06|40.28
Crossmodal-3600 Image-Text Retrieval: Filipino|82.72|72.56|72.86|62.72|71.36|60.22
Crossmodal-3600 Image-Text Retrieval: French|39.08|39.72|31.78|31.47|29.92|29.61
Crossmodal-3600 Image-Text Retrieval: Hindi|77.67|71.67|65.67|65.44|63.47|63.53
Crossmodal-3600 Image-Text Retrieval: Croatian|53.08|53.72|37.94|38.86|35.78|35.64
Crossmodal-3600 Image-Text Retrieval: Hungarian|53.81|54.61|38.64|37.81|34.42|34.78
Crossmodal-3600 Image-Text Retrieval: Indonesian|35.83|37.47|28.47|30.94|28.53|28.42
Crossmodal-3600 Image-Text Retrieval: Italian|38.42|40.69|33.33|33.50|30.97|31.03
Crossmodal-3600 Image-Text Retrieval: Hebrew|56.75|47.75|39.44|37.39|35.72|34.19
Crossmodal-3600 Image-Text Retrieval: Japanese|59.00|61.58|45.42|45.78|44.97|46.69
Crossmodal-3600 Image-Text Retrieval: Korean|50.75|53.06|40.33|40.00|38.31|38.58
Crossmodal-3600 Image-Text Retrieval: Maori|99.58|97.94|99.22|95.00|99.25|96.08
Crossmodal-3600 Image-Text Retrieval: Dutch|47.11|48.06|41.14|41.42|38.39|39.94
Crossmodal-3600 Image-Text Retrieval: Norwegian|45.33|46.81|36.11|36.72|34.28|34.47
Crossmodal-3600 Image-Text Retrieval: Polish|45.97|45.81|35.50|35.61|34.11|34.33
Crossmodal-3600 Image-Text Retrieval: Portuguese|43.33|42.53|36.03|38.33|34.56|34.11
Crossmodal-3600 Image-Text Retrieval: Quechua|94.64|94.97|93.53|93.83|93.92|93.42
Crossmodal-3600 Image-Text Retrieval: Romanian|52.19|52.72|38.31|38.06|35.39|34.86
Crossmodal-3600 Image-Text Retrieval: Russian|42.78|45.00|35.14|35.11|33.22|33.42
Crossmodal-3600 Image-Text Retrieval: Swedish|44.50|46.19|34.94|36.06|34.78|34.19
Crossmodal-3600 Image-Text Retrieval: Swahili|89.94|75.06|81.33|67.64|79.47|65.81
Crossmodal-3600 Image-Text Retrieval: Telugu|96.08|81.00|76.67|67.78|69.69|66.33
Crossmodal-3600 Image-Text Retrieval: Thai|72.61|74.72|59.47|60.50|58.86|59.92
Crossmodal-3600 Image-Text Retrieval: Turkish|52.78|54.94|40.72|41.25|39.72|39.89
Crossmodal-3600 Image-Text Retrieval: Ukrainian|55.19|57.33|41.25|40.97|37.83|39.19
Crossmodal-3600 Image-Text Retrieval: Vietnamese|43.19|42.22|34.00|35.22|32.44|32.86
Crossmodal-3600 Image-Text Retrieval: Chinese|53.67|54.81|42.47|44.67|42.50|43.97
Crossmodal-3600 Text-Image Retrieval: Arabic|67.49|65.43|59.74|59.02|59.86|59.70
Crossmodal-3600 Text-Image Retrieval: Bengali|95.17|83.83|79.72|75.56|77.31|73.33
Crossmodal-3600 Text-Image Retrieval: Czech|65.52|65.19|58.57|59.19|58.18|57.56
Crossmodal-3600 Text-Image Retrieval: Danish|60.01|59.93|51.18|52.77|49.50|49.74
Crossmodal-3600 Text-Image Retrieval: German|45.85|47.48|39.88|40.72|39.75|39.50
Crossmodal-3600 Text-Image Retrieval: Greek|77.96|75.46|69.11|69.24|67.35|68.25
Crossmodal-3600 Text-Image Retrieval: English|58.97|56.93|57.57|57.52|56.32|56.51
Crossmodal-3600 Text-Image Retrieval: Spanish|52.64|52.79|49.06|49.90|48.31|48.76
Crossmodal-3600 Text-Image Retrieval: Persian|62.65|63.27|55.06|55.54|56.09|54.64
Crossmodal-3600 Text-Image Retrieval: Finnish|72.96|72.06|59.11|58.61|56.24|56.42
Crossmodal-3600 Text-Image Retrieval: Filipino|90.89|83.32|83.98|78.41|83.70|74.94
Crossmodal-3600 Text-Image Retrieval: French|48.33|49.81|43.31|44.62|42.10|42.34
Crossmodal-3600 Text-Image Retrieval: Hindi|87.43|83.45|81.38|80.96|80.01|79.22
Crossmodal-3600 Text-Image Retrieval: Croatian|66.68|65.73|54.42|56.10|54.22|53.60
Crossmodal-3600 Text-Image Retrieval: Hungarian|66.49|66.66|53.73|54.57|50.75|51.16
Crossmodal-3600 Text-Image Retrieval: Indonesian|50.28|49.62|44.05|44.58|43.97|44.30
Crossmodal-3600 Text-Image Retrieval: Italian|47.96|49.51|42.80|45.41|42.60|42.66
Crossmodal-3600 Text-Image Retrieval: Hebrew|69.11|60.25|56.25|55.62|54.14|51.65
Crossmodal-3600 Text-Image Retrieval: Japanese|69.56|71.62|62.34|63.34|58.44|61.42
Crossmodal-3600 Text-Image Retrieval: Korean|64.52|64.72|56.76|57.83|56.51|57.58
Crossmodal-3600 Text-Image Retrieval: Maori|99.73|97.92|99.56|96.30|99.62|96.19
Crossmodal-3600 Text-Image Retrieval: Dutch|57.41|58.78|52.02|53.88|51.48|51.82
Crossmodal-3600 Text-Image Retrieval: Norwegian|61.54|61.46|53.81|54.35|52.99|53.50
Crossmodal-3600 Text-Image Retrieval: Polish|56.06|56.43|47.92|49.96|47.09|47.16
Crossmodal-3600 Text-Image Retrieval: Portuguese|54.54|54.07|49.48|51.03|48.72|48.34
Crossmodal-3600 Text-Image Retrieval: Quechua|97.88|97.89|98.14|98.03|98.04|97.88
Crossmodal-3600 Text-Image Retrieval: Romanian|65.20|65.55|54.05|54.79|52.41|51.93
Crossmodal-3600 Text-Image Retrieval: Russian|53.47|53.75|47.58|48.43|45.36|46.83
Crossmodal-3600 Text-Image Retrieval: Swedish|58.78|59.12|50.72|52.50|51.82|50.97
Crossmodal-3600 Text-Image Retrieval: Vietnamese|61.84|61.28|54.00|55.01|53.39|53.51
Crossmodal-3600 Text-Image Retrieval: Chinese|64.87|65.56|59.03|61.21|57.33|59.49
Average Western 0-shot Classification|23.54|23.12|21.97|22.18|20.44|21.18
Average Western 10-shot Classification|23.62|24.18|23.59|24.34|23.10|23.99
Average Western 0-shot Retrieval|44.55|45.65|39.83|41.70|39.23|39.44
Average Western Classification|23.60|23.89|23.15|23.75|22.37|23.22
Average Dollar Street Classification|56.89|58.10|56.09|57.46|53.66|54.33
Average GeoDE Classification|40.72|39.94|40.60|39.93|37.01|35.60
Average Income Classification|50.22|51.15|48.09|49.41|49.02|49.23
Average Geographic Classification|5.95|5.97|5.84|5.93|4.83|5.37
Average Demography Classification|24.91|27.14|26.47|25.93|25.50|26.19
Average Multilingual: Low-Resource Lang|87.73|78.82|77.14|72.04|75.01|70.10
Average Multilingual: High-Resource Lang|55.54|56.21|46.75|47.53|45.43|45.75
Average Western-centric|29.19|29.69|27.60|28.54|26.87|27.55
Average Cultural Diversity|47.72|47.97|46.72|47.07|44.01|43.29
Average Fairness|23.87|24.56|23.36|23.76|23.01|23.46
Average Multilinguality|57.52|56.64|47.23|46.43|45.40|44.61{{< /table-caption >}}
> 🔼 표 11은 훈련 중 1000억 개의 예시를 사용하여 ViT-L/16 모델과 10억, 100억, 1000억 규모의 데이터셋에서 저자원 언어의 재균형 조정에 대한 자세한 평가 결과를 보여줍니다. 모든 지표는 오차율로 측정되지만, '표현 편향'은 차이로 측정됩니다.
> <details>
> <summary>read the caption</summary>
> Table 11: Detailed evaluation results of the rebalancing of low-resource languages on ViT-L/16 models and datasets of 1/10/100 billion scales, with 100 billion examples seen in training. All metrics are measured by error rate, with the exception of “Representation Bias”, which is measured by disparity.
> </details>

{{< table-caption >}}
| Language | Type | Pages (%) |
|---|---|---|
| Maori | Low-resource | 0.001 |
| Telugu | Low-resource | 0.036 |
| Swahili | Low-resource | 0.046 |
| Filipino | Low-resource | 0.111 |
| Bengali | Low-resource | 0.113 |
| Hebrew | Low-resource | 0.240 |
| Hindi | Low-resource | 0.267 |
| Croatian | High-resource | 0.284 |
| Norwegian | High-resource | 0.290 |
| Finnish | High-resource | 0.296 |
| Danish | High-resource | 0.370 |
| Hungarian | High-resource | 0.378 |
| Ukrainian | High-resource | 0.476 |
| Romanian | High-resource | 0.489 |
| Greek | High-resource | 0.560 |
| Swedish | High-resource | 0.660 |
| Czech | High-resource | 0.727 |
| Persian | High-resource | 0.881 |
| Thai | High-resource | 1.167 |
| Dutch | High-resource | 1.173 |
| Arabic | High-resource | 1.258 |
| Vietnamese | High-resource | 1.337 |
| Turkish | High-resource | 1.554 |
| Polish | High-resource | 1.825 |
| Italian | High-resource | 1.964 |
| Korean | High-resource | 2.519 |
| Portuguese | High-resource | 3.054 |
| Indonesian | High-resource | 3.181 |
| French | High-resource | 3.354 |
| Chinese | High-resource | 3.544 |
| German | High-resource | 3.869 |
| Russian | High-resource | 6.981 |
| Spanish | High-resource | 8.214 |
| Japanese | High-resource | 8.752 |
| English | High-resource | 35.353 |
| **Low-resource All** | Low-resource | 0.814 |
| **High-resource All** | High-resource | 94.510 |{{< /table-caption >}}
> 🔼 표 12는 논문에서 다국어 평가에 사용된 35개 언어의 분포를 보여줍니다. 각 언어는 자원량(저자원 또는 고자원)과 데이터셋에서 차지하는 비율(%)로 분류됩니다. 이 표는 다국어 모델의 성능을 평가할 때 사용된 언어의 균형을 이해하는 데 도움이 됩니다. 저자원 언어는 데이터셋에서 상대적으로 적은 비율을 차지하지만, 이러한 언어에 대한 모델의 성능을 평가하는 것은 다국어 모델의 포괄성을 평가하는 데 중요합니다.
> <details>
> <summary>read the caption</summary>
> Table 12: Distribution of the 35 languages used in multilingual evaluations.
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