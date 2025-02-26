---
title: "M3-AGIQA: Multimodal, Multi-Round, Multi-Aspect AI-Generated Image Quality Assessment"
summary: "M3-AGIQA: 멀티모달, 멀티라운드, 멀티측면 AI 생성 이미지 품질 평가 프레임워크가 최첨단 성능을 달성!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Generation", "🏢 School of Computer Science and Technology, Tongji University, Shanghai, China",]
showSummary: true
date: 2025-02-21
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.15167 {{< /keyword >}}
{{< keyword icon="writer" >}} Chuan Cui et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-25 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.15167" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.15167" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

AI 기술의 발전으로 AI 생성 이미지(AGI)가 급증하고 있지만, 이를 평가하는 기존 방법들은 **주관적이거나 객관적인 지표가 부족**하여 AGI의 품질, 일관성, 신뢰성을 정확하게 평가하는 데 어려움이 있습니다. 특히, 사용자의 의도와 생성 이미지의 부합성을 평가하는 것은 매우 중요하지만, 기존 방법으로는 어려운 과제입니다.

본 논문에서는 이러한 문제를 해결하기 위해 **M3-AGIQA라는 새로운 프레임워크**를 제시합니다.  M3-AGIQA는 **멀티모달 대규모 언어 모델(MLLM)을 활용**하여 이미지와 텍스트를 함께 분석하고, **다단계 평가 방식**을 통해 이미지의 품질, 일관성, 신뢰성을 종합적으로 평가합니다.  **xLSTM과 회귀 모델**을 사용하여 사람의 인지 능력에 맞춰 예측값을 조정하고, 여러 개의 벤치마크 데이터셋을 사용하여 실험을 진행하여 **최첨단 성능**을 달성했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} M3-AGIQA는 **다양한 측면(품질, 일관성, 신뢰성)을 고려하는 멀티모달 AI 생성 이미지 품질 평가 프레임워크**입니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} **대규모 언어 모델(MLLM)을 활용하여 이미지와 텍스트를 통합적으로 분석**하고, 사람의 인지 능력에 가까운 평가를 제공합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 다양한 데이터셋에서 **최첨단 성능을 달성**하여 **뛰어난 일반화 능력**을 입증하였습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **AI 생성 이미지 품질 평가 분야의 난제를 해결하기 위한 새로운 멀티모달 프레임워크인 M3-AGIQA를 제시**합니다.  대규모 언어 모델을 활용하여 이미지의 품질, 일관성, 신뢰성을 다각적으로 평가하고, 사람의 인식과 의도에 더욱 부합하는 정확한 평가를 제공합니다.  이는 **AI 생성 이미지 기술 발전에 크게 기여**하며, 관련 연구 분야의 새로운 연구 방향을 제시할 수 있습니다.  **다양한 데이터셋에 대한 실험 결과는 M3-AGIQA의 우수한 성능과 일반화 능력을 입증**하며, 향후 AI 생성 콘텐츠의 질적 향상에 중요한 역할을 할 것으로 예상됩니다.

------
#### Visual Insights





{{< table-caption >}}
| Statistics | AGIQA-3k | AIGCIQA2023 | AIGCIQA-20k |
|---|---|---|---|
| No. of images | 2,982 | 2,400 | 20,000 |
| No. of T2I models | 6 | 6 | 15 |
| quality MOS | 
<span class="ltx_ERROR undefined">


ding</span>51 |
<span class="ltx_ERROR undefined">


ding</span>51 | 
<span class="ltx_ERROR undefined">


ding</span>51 |
| correspondence MOS | 
<span class="ltx_ERROR undefined">


ding</span>51 | 
<span class="ltx_ERROR undefined">


ding</span>51 | 
<span class="ltx_ERROR undefined">


ding</span>55 |
| authenticity MOS | 
<span class="ltx_ERROR undefined">


ding</span>55 | 
<span class="ltx_ERROR undefined">


ding</span>51 | 
<span class="ltx_ERROR undefined">


ding</span>55 |{{< /table-caption >}}

> 🔼 이 표는 논문에서 사용된 세 가지 AI 생성 이미지 품질 평가 데이터셋(AGIQA-3k, AIGCIQA2023, AIGCIQA-20k)의 통계 정보를 요약하여 보여줍니다. 각 데이터셋에 포함된 이미지 수, 사용된 텍스트-이미지 생성 모델의 수, 그리고 품질, 일관성, 진정성 등과 같은 다양한 측면에 대한 평균 의견 점수(MOS)의 유무를 보여줍니다. 이 정보는 각 데이터셋의 규모와 특징을 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table \thetable: Statistics of the datasets.
> </details>





### In-depth insights


#### AGIQA Challenges
AGIQA(AI 생성 이미지 품질 평가) 분야는 **다차원적 품질 평가**의 어려움에 직면합니다. 단순한 화질 평가를 넘어, 프롬프트 일치도, 현실성, 다양성 등 주관적인 요소까지 고려해야 하기 때문입니다.  **기존 IQA(이미지 품질 평가) 방식**은 이러한 다면적인 측면을 충분히 반영하지 못하며, **텍스트-이미지 정합성**을 제대로 평가하는 데에도 한계가 있습니다.  **데이터셋의 한계** 또한 문제입니다.  현존하는 AGIQA 데이터셋은 규모나 다양성 측면에서 부족하며, 다양한 생성 모델과 프롬프트 유형을 포괄하지 못합니다. 따라서, **더욱 정교하고 포괄적인 평가 지표 및 데이터셋 구축**이 시급한 과제입니다.  더불어, **인간의 주관적인 판단을 효과적으로 반영**하는 모델 개발이 중요하며, 이를 위해 **인간의 지각 능력을 모방하는 새로운 딥러닝 기법** 연구가 필요합니다.  궁극적으로, AGIQA는 AI 생성 이미지의 질적 향상에 중요한 역할을 하므로, 이러한 과제들을 해결하기 위한 지속적인 연구 노력이 필요합니다.

#### M3-AGIQA Framework
M3-AGIQA 프레임워크는 **다중 모드**, **다중 라운드**, **다중 측면** 평가를 통해 AI 생성 이미지의 질을 종합적으로 평가하는 혁신적인 시스템입니다.  **온라인 MLLM으로부터의 지식 증류**를 통해 로컬 모델의 성능을 향상시키고, **구조화된 다중 라운드 평가 메커니즘**을 통해 이미지 품질, 일관성, 신뢰성에 대한 심층적인 통찰력을 제공합니다.  **xLSTM과 회귀 분석기**를 활용하여 인간의 지각 판단과 의도를 정확히 반영하며, **다양한 데이터셋에 대한 우수한 성능**과 **일반화 가능성**을 보여줍니다.  **LoRA 파인튜닝**을 통한 효율적인 학습과 **다양한 지표**를 활용하여 AI 생성 이미지 평가 분야의 새로운 기준을 제시합니다.

#### MLLM Distillation
본 논문에서 제시된 **MLLM 증류**는 대규모 언어 모델의 강력한 이미지 캡셔닝 능력을 활용하여 AI 생성 이미지의 질적 평가를 향상시키는 핵심 전략입니다.  **온라인 MLLM으로부터 얻은 풍부한 이미지 설명 정보**를 **로컬 MLLM에 효율적으로 전이**하는 과정을 통해, 제한된 자원으로도 고품질의 이미지 평가가 가능해집니다. 이는 특히 **LoRA(Low-Rank Adaptation) 파인튜닝 기법**을 활용하여 온라인 모델의 지식을 로컬 모델에 효과적으로 주입하는 방식으로 이루어집니다.  **증류된 지식은 AI 생성 이미지의 질, 일관성, 신뢰성** 등 다양한 측면을 포괄적으로 평가하는 데 활용되며, 최종적으로는 사람의 인지 능력과 일치하는 정확한 평가 결과를 도출하는 데 기여합니다.  **결과적으로, MLLM 증류는 제한된 계산 자원 하에서도 우수한 성능을 달성하는 AI 생성 이미지 평가 모델을 구축하는 데 매우 효과적임을 시사**합니다.

#### Cross-dataset Results
본 논문에서 다루는 **교차 데이터셋 결과**는 모델의 일반화 성능을 평가하는 데 매우 중요합니다.  만약 특정 데이터셋에 과적합된 모델이라면 다른 데이터셋에서 성능이 현저히 떨어질 것입니다.  따라서 교차 데이터셋 실험 결과는 **모델의 견고성과 실제 적용 가능성**을 보여주는 중요한 지표입니다.  **다양한 데이터셋에 대한 성능 비교**를 통해 모델의 일반화 능력을 정확하게 평가하고, 개선점을 도출할 수 있습니다. 이러한 분석은 모델의 강점과 약점을 파악하고, 향후 연구 방향을 설정하는 데 필수적입니다. 특히, **데이터셋 간의 차이점을 고려한 분석**은 모델의 일반화 능력을 더욱 명확히 이해하는 데 도움이 될 것입니다.

#### Future of AGIQA
AGIQA 분야의 미래는 **다양한 모드와 측면을 아우르는 포괄적인 평가 시스템 개발**에 달려 있습니다.  **대규모 언어 모델(LLM)의 발전**은 텍스트와 이미지 간의 상관관계를 더욱 정교하게 분석하고, 인간의 미적 감각과 의도를 더욱 정확하게 반영하는 AGIQA 시스템 구축을 가능하게 할 것입니다.  **데이터셋의 확장 및 다양화**는 모델의 일반화 능력 향상에 중요한 역할을 하며,  **인간 평가자와의 지속적인 상호 작용**을 통해 모델의 정확성을 높일 수 있습니다.  **새로운 평가 지표 개발**과 더불어, 생성된 이미지의 윤리적 측면과 사회적 영향에 대한 고려 또한 중요해질 것입니다.  결론적으로, AGIQA의 미래는 **기술적 진보와 윤리적 책임감 있는 접근 방식**의 조화로운 발전에 있습니다.


### More visual insights




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Methods | AGIQA-3k |  |  |  | AIGCIQA2023 |  |  |  |  | AIGCIQA-20k |  |  | 
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|  | Qual. |  | Corr. |  | Qual. |  | Corr. |  | Auth. |  | Qual. |  |
|  | SRCC | PLCC | SRCC | PLCC | SRCC | PLCC | SRCC | PLCC | SRCC | PLCC | SRCC | PLCC |
| VGG16 [simonyan2014very] | 0.8167 | 0.8752 | 0.6867 | 0.8108 | 0.8157 | 0.8282 | 0.6839 | 0.6853 | 0.7399 | 0.7465 | 0.8133 | 0.8660 |
| ResNet50 [he2016deep] | 0.8552 | 0.9072 | 0.7493 | 0.8564 | 0.8190 | 0.8503 | 0.7230 | 0.7270 | 0.7571 | 0.7563 | 0.8036 | 0.8661 |
| ViT/B/16 [dosovitskiy2020image] | 0.8659 | 0.9115 | 0.7478 | 0.8449 | 0.8370 | 0.8618 | 0.7293 | 0.7439 | 0.7783 | 0.7697 | 0.8407 | 0.8904 |
| ViL [alkin2024visionlstm] | 0.8750 | 0.9145 | 0.7570 | 0.8561 | 0.8436 | 0.8770 | 0.7174 | 0.7296 | 0.7753 | 0.7770 | 0.8459 | 0.8852 |
| DBCNN* [zhang2018blind] | 0.8154 | 0.8747 | 0.6329 | 0.7823 | 0.8339 | 0.8577 | 0.6837 | 0.6787 | 0.7485 | 0.7436 | 0.7941 | 0.8542 |
| StairIQA [sun2022blind] | 0.8439 | 0.8989 | 0.7345 | 0.8474 | 0.8264 | 0.8483 | 0.7176 | 0.7133 | 0.7596 | 0.7514 | 0.8126 | 0.8746 |
| MGQA [wang2021multi] | 0.8283 | 0.8944 | 0.7244 | 0.8430 | 0.8093 | 0.8308 | 0.6892 | 0.6745 | 0.7367 | 0.7310 | 0.8107 | 0.8534 |
| HyperIQA [Su_2020_CVPR] | 0.8526 | 0.8975 | 0.7437 | 0.8471 | 0.8357 | 0.8504 | 0.7318 | 0.7222 | 0.7758 | 0.7790 | 0.8171 | 0.8584 |
| AMFF-Net* [zhou2024adaptive] | 0.8565 | 0.9050 | 0.7513 | 0.8476 | 0.8409 | 0.8537 | 0.7782 | 0.7638 | 0.7749 | 0.7643 | - | - |
| MA-AGIQA* [wang2024large] | 0.8939 | 0.9273 | - | - | - | - | - | - | - | - | 0.8644 | 0.9050 |
| IPCE* [peng2024aigc] | 0.8841 | 0.9246 | 0.7697 | 0.8725 | 0.8640 | 0.8788 | 0.7979 | 0.7887 | 0.8097 | 0.7998 | 0.9076 | 0.9274 |
| SF-IQA* [yu2024sf] | 0.9024 | 0.9314 | 0.8454 | 0.9072 | - | - | - | - | - | - | 0.9009 | 0.9268 |
| M3-AGIQA (Ours) | 0.9045 | 0.9317 | 0.8523 | 0.9142 | 0.8618 | 0.8922 | 0.8060 | 0.7973 | 0.8282 | 0.8165 | 0.8988 | 0.9292 |{{< /table-caption >}}
> 🔼 이 표는 논문에서 제시된 세 가지 AI 생성 이미지 품질 평가 데이터 세트(AGIQA-3k, AIGCIQA2023, AIGCIQA-20k)에 대한 다양한 방법들의 성능 비교 결과를 보여줍니다.  표에는 각 방법의 Spearman 순위 상관 계수(SRCC)와 Pearson 선형 상관 계수(PLCC)가 세 가지 측면(품질, 일관성, 신뢰성)별로 제시되어 있습니다.  별표(*)가 표시된 방법들은 해당 논문에서 직접적으로 가져온 결과이며, 굵은 밑줄이 표시된 값은 각 측면에서 가장 우수한 결과와 두 번째로 우수한 결과를 나타냅니다.  이 표는 다양한 방법들의 상대적인 강점과 약점을 비교하여, 제안된 방법의 효과를 평가하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table \thetable: Comparison results on AGIQA-3k [li2023agiqa], AIGCIQA2023 [wang2023aigciqa2023], and AIGCIQA-20k [li2024aigiqa] among different methods, results of methods with asterisk symbol “∗” are directly retrieved from corresponding papers. Bold and underlined values indicate the best and second-best results, respectively.
> </details>

{{< table-caption >}}
| Present Descriptions | Qual. | Corr. | Auth. | SRCC | PLCC |
|---|---|---|---|---|---| 
|  ✔ | ✔ | ✔ | 0.8816 | 0.9193 |
| ✕ | ✔ | ✔ | 0.8989 | 0.9342 |
| ✕ | ✕ | ✔ | 0.9045 | 0.9317 |
| ✕ | ✕ | ✕ | 0.8999 | 0.9321 |{{< /table-caption >}}
> 🔼 이 표는 논문의 실험 결과를 보여줍니다.  AGIQA-3k 데이터셋의 품질 평가 측면에서, 이미지 설명의 여러 조합(품질, 일치성, 진정성)에 따른 비교 결과를 보여줍니다.  각 조합에 대한 SRCC(Spearman Rank Order Correlation Coefficient)와 PLCC(Pearson Linear Correlation Coefficient) 값을 제시하여, 이미지 설명의 다양한 조합이 모델 성능에 미치는 영향을 분석합니다.  이를 통해 어떤 종류의 이미지 설명이 AGIQA 모델의 정확도 향상에 가장 효과적인지 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table \thetable: Comparison results on AGIQA-3k [li2023agiqa] quality aspect with different combinations of image description aspects.
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