---
title: "Current Pathology Foundation Models are unrobust to Medical Center Differences"
summary: "의료 센터 차이에 취약한 병리학 기반 모델의 강건성을 높이는 새로운 지표와 정량적 분석 방법 제시!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["AI Applications", "Healthcare", "🏢 Netherlands Cancer Institute Amsterdam",]
showSummary: true
date: 2025-01-29
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.18055 {{< /keyword >}}
{{< keyword icon="writer" >}} Edwin D. de Jong et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-04 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.18055" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.18055" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/current-pathology-foundation-models-are" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

많은 의료 AI 연구에서 병리학적 영상 분석에 **심층 신경망 기반의 기초 모델(Foundation Model)**이 사용되고 있습니다. 하지만, 이러한 기초 모델들은 **각 의료 센터마다 다른 염색 기법 및 기타 요인**으로 인해 모델의 예측 결과가 달라지는 **의료 센터 편향** 문제에 취약하다는 점이 지적됩니다. 이는 임상 현장에서 모델의 신뢰도와 일반화 성능을 저해하는 심각한 문제입니다.

본 논문에서는 이러한 문제를 해결하기 위해 **새로운 강건성 지표**를 제시하고, 의료 센터 편향이 모델 성능에 미치는 영향을 정량적으로 분석하는 방법을 제안합니다. 연구진은 다양한 기초 모델들을 평가하여 의료 센터 특징이 생물학적 특징보다 우세하게 나타나는 것을 확인하고, 이러한 편향이 모델의 오류에 어떻게 영향을 미치는지 시각화합니다.  **새로운 강건성 지표와 분석 방법**은 병리학 기반 모델의 강건성과 신뢰성을 향상시키는 데 기여할 것으로 기대됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 의료 센터 차이가 병리학 기반 모델의 성능에 큰 영향을 미친다는 것을 발견했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 병리학 기반 모델의 강건성을 평가하기 위한 새로운 지표인 '강건성 지수'를 제안했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 의료 센터 편향을 줄이고 모델의 신뢰성을 높이기 위한 새로운 분석 방법을 제시했습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
이 논문은 **의료 센터 간의 차이에 대한 강건성 부족**이라는 병리학 기반 모델의 주요 문제를 다룹니다. 이는 임상 환경에서의 적용 가능성에 영향을 미치는 중요한 문제입니다.  **새로운 강건성 지표와 정량적 분석 방법**을 제시함으로써, 연구자들은 병리학 기반 모델의 신뢰성과 일반화 성능을 개선하는 데 도움이 될 것입니다. 또한 이 연구는 **의료 센터 편향 문제**를 시각화하고 분석하는 새로운 관점을 제공하여 향후 연구를 위한 중요한 방향을 제시합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.18055/extracted/6170945/fig/freq-same-class.png)

> 🔼 그림 2는 논문에서 평가한 여러 병리학 기반 모델들의 강건성 지수를 보여줍니다.  강건성 지수는 생물학적 특징 (예: 조직 유형 또는 암 유형)이 혼란 요소 (예: 의료 센터)보다 얼마나 중요한지를 나타내는 지표입니다.  높은 강건성 지수는 모델이 생물학적 특징에 더 집중하고 의료 센터 간 차이와 같은 혼란 요소의 영향을 덜 받는다는 것을 의미합니다.  이 그림은 각 모델의 강건성 지수를 막대 그래프 형태로 비교하여 모델 간 강건성의 차이를 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Robustness index for the models evaluated here.
> </details>





{{< table-caption >}}
| TSS Short Name | BRCA | COAD | LIHC | LUSC | STAD |
|---|---|---|---|---|---| 
| Asterand | ✓ | ✓ | ✓ | ✓ | ✓ |
| GPCC | ✓ | ✓ |  |  | ✓ |
| IGC | ✓ | ✓ | ✓ | ✓ | ✓ |
| ILSBio | ✓ | ✓ | ✓ |  | ✓ |
| MSKCC | ✓ | ✓ |  | ✓ |  |{{< /table-caption >}}

> 🔼 표 1은 논문에서 사용된 TCGA-2k 데이터셋의 구성을 보여줍니다. TCGA-2k 데이터셋은 다양한 조직 유래(Tissue Source Site, TSS), 약칭 및 프로젝트 코드 조합으로 이루어져 있습니다. 이 표는 각 조직 유래(예: 유방암, 대장암 등)에 대해 어떤 병원(약칭)의 데이터가 포함되어 있는지 보여주는 정보를 담고 있습니다. 각 조직 유래와 병원 조합에 대해 10개의 전체 슬라이드 이미지(WSI)가 무작위로 선택되었고, 각 WSI에서 다시 10개의 정보가 풍부한 전경 패치(foreground patches)가 선택되어 최종적으로 2000개의 패치가 TCGA-2k 데이터셋을 구성합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Composition of the  TCGA-2k dataset: Tissue Source Site (TSS), Short Name and Project Code Combinations
> </details>





### In-depth insights


#### FM Robustness Index
본 논문에서 제시된 **FM 강건성 지수**는 병리학 기반 모델(FM)이 얼마나 생물학적 특징에 집중하는지, 혹은 염색 과정이나 기타 차이로 인한 의료 센터 간의 차이와 같은 혼란 요소에 얼마나 영향을 받는지를 측정하는 새로운 지표입니다.  **의료 센터의 영향을 정량적으로 측정**하여 하위 모델의 분류 성능에 미치는 영향을 분석하고, **생물학적 특징과 혼란 요소의 상대적 중요도**를 파악하는 데 중요한 역할을 합니다. 이 지수는 의료 센터 간의 차이에 대한 FM의 강건성을 평가하고, 임상 환경에서의 신뢰도와 견고성을 높이는 데 기여할 수 있습니다.  **강건성 지수가 1보다 클 경우**, 생물학적 특징이 혼란 요인보다 우세함을 나타내지만, 논문에서 평가된 모델 중에서는 이 기준을 만족하는 모델이 **거의 없음**을 보여줍니다. 따라서 향후 **더욱 강건한 병리학 FM 개발**을 위한 중요한 지표로 활용될 것으로 기대됩니다.

#### Center Confounders
본 논문에서 'Center Confounders'는 병리학적 영상 분석에서 **의료기관 간 차이**로 인해 발생하는 혼란 요인을 의미합니다.  즉, 조직의 종류나 암의 유형과 같은 생물학적 특징이 아닌, 염색 과정이나 영상 촬영 장비 등 의료기관 특유의 요소들이 모델의 예측 성능에 영향을 미치는 현상입니다. 이는 모델의 일반화 능력을 저하시키고, **의료기관별로 다른 진단 결과**를 초래할 수 있다는 점에서 심각한 문제입니다. 따라서, 이러한 Center Confounders를 정량적으로 측정하고, 이를 해결하기 위한 강건한 모델 개발이 중요한 과제임을 시사합니다. 특히, **로버스트니스 지수(Robustness Index)**를 활용하여 생물학적 특징과 혼란 요인의 영향력을 비교 분석함으로써 모델의 강건성을 평가할 수 있다는 점이 중요한 발견입니다.  또한, t-SNE 기법을 이용한 시각화 분석을 통해 **의료기관 간 군집 현상**을 명확히 보여줌으로써 Center Confounders 문제의 심각성을 강조합니다.

#### Embedding Analysis
본 논문에서 "임베딩 분석"은 **의료 센터 간 차이에 대한 병리학적 기초 모델의 강건성을 평가**하기 위해 필수적인 부분입니다.  이는 단순히 임베딩 공간의 시각화를 넘어, **생물학적 특징과 혼란 요소(의료 센터 차이 등)** 간의 관계를 정량적으로 분석하는 것을 의미합니다.  **새로운 강건성 지표(Robustness Index)**를 도입하여 생물학적 특징이 혼란 요소보다 얼마나 중요한지를 측정하고, 다양한 모델의 강건성을 비교 분석합니다.  **t-SNE를 이용한 2D 시각화**를 통해 임베딩 공간에서 의료 센터가 얼마나 강하게 클러스터링 되는지 보여줍니다.  이는 모델의 예측 성능에 대한 의료 센터의 영향을 파악하는 데 중요한 역할을 합니다.  **다운스트림 모델의 성능 분석**을 통해 의료 센터 간 차이가 예측 오류에 어떻게 영향을 미치는지 보여주며, **같은 의료 센터에서 온 다른 클래스의 이미지가 예측 오류에 기여**하는 것을 보여줍니다.  따라서 임베딩 분석은 단순한 시각화가 아닌, 모델의 강건성과 신뢰성을 평가하는 중요한 분석적 도구임을 강조합니다.

#### Prediction Accuracy
본 논문에서는 다양한 병리학 기반 모델의 예측 정확도를 종합적으로 평가합니다. **의료 센터 간의 차이에 대한 강건성**을 중점적으로 분석하여, 모델의 일반화 성능과 임상 적용 가능성에 대한 심도있는 논의를 제시합니다. 특히, **의료 센터 정보가 예측 성능에 미치는 영향**에 대한 정량적 분석을 통해, 모델의 신뢰성과 편향성 문제를 밝힙니다. **생물학적 특징과 혼란 변수의 구분**을 통해, 모델이 실제 질병 정보를 얼마나 정확하게 반영하는지 평가하고, 향후 **강건하고 신뢰할 수 있는 병리학 기반 모델 개발**을 위한 방향을 제시합니다.  **다운스트림 모델의 성능** 측면에서도 분석하여, 모델의 강건성이 임상적 의사결정에 미치는 영향을 보여줍니다.

#### Future Robustness
미래의 강건성을 위해서는 **의료 센터 간의 차이에 대한 견고성을 높이는 것**이 필수적입니다. 이는 다양한 염색 절차, 장비 및 이미지 처리 파이프라인의 변화로 인한 혼란스러운 특징에 대한 모델의 민감도를 줄이는 것을 의미합니다.  **강건성 지수와 같은 정량적 척도를 사용하여 이러한 차이가 모델 성능에 미치는 영향을 측정하고 시각화**함으로써, 의료센터 편향을 줄이고 생물학적 특징에 대한 모델의 집중도를 높일 수 있습니다.  **다운스트림 모델의 성능을 분석하고 임베딩 공간을 시각화**하는 것은 강건성을 평가하고 개선하는 데 중요한 부분입니다. **향후 연구는 강건한 병리학 기반 모델을 개발하고 임상 환경에 적용하기 위한 노력**에 집중되어야 합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.18055/extracted/6170945/fig/confounding-neighbors-fraction-same-center/confounding-neighbors-fraction-same-center-together.png)

> 🔼 그림 4는 다양한 병리학적 기초 모델에서 잘못 예측된 클래스의 이웃으로부터 동일한 센터의 혼란 요소 비율을 보여줍니다. 모든 모델은 의료 센터 차이에 민감하며, 일부 모델은 매우 높은 수준으로 민감합니다. 이 그림은 의료 센터의 영향을 정량화하여 모델의 강건성을 평가하는 데 도움이 됩니다. 높은 비율은 모델이 생물학적 특징보다 의료 센터 특징에 더 많이 의존한다는 것을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Fractions of same-center confounders for all models. All models are sensitive to these differences, some to a very high degree.
> </details>



![](https://arxiv.org/html/2501.18055/extracted/6170945/fig/relation-log-reg-center-error-avg-CLS-nr_reps-5-nr_neighbors-3.png)

> 🔼 그림 8은 로지스틱 회귀 오류와 중심 관련 knn 오류 간의 관계를 보여줍니다. 의료 센터를 기반으로 knn에 의해 잘못 분류될 가능성이 높은 샘플은 로지스틱 회귀에 의해 잘못 분류될 가능성도 높아 중심 유사성이 로지스틱 회귀 예측에도 영향을 미친다는 것을 시사합니다.  즉, 특정 의료 센터의 데이터 특징이 학습된 모델에 과도하게 반영되어 해당 센터의 데이터에 대해서는 예측 정확도가 높지만, 다른 센터의 데이터에 대해서는 예측 성능이 떨어지는 현상을 보여주는 것입니다. 이는 모델의 견고성(robustness)에 대한 중요한 시사점을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Relation between logistic regression errors and center-related knn errors. Samples that are more frequently misclassified by knn based on medical center are also more frequently misclassified by logistic regression, suggesting center similarities also affect logistic regression predictions.
> </details>



![](https://arxiv.org/html/2501.18055/extracted/6170945/fig/hibou-b/tsne-BRCA-medical-center.png)

> 🔼 그림 9는 유방암 조직 슬라이드의 임베딩을 보여줍니다. 왼쪽은 Phikon 모델, 오른쪽은 Phikon-v2 모델의 결과입니다. 각 점은 하나의 패치를 나타내며, 색깔은 의료기관(병원)을 나타냅니다. 이 그림은 두 모델이 의료기관 간 차이에 얼마나 민감하게 반응하는지 시각적으로 보여줍니다. 색깔이 섞이지 않고 명확하게 구분될수록 의료기관 특징에 더 민감하다는 것을 의미합니다.  Phikon-v2가 Phikon 보다 색깔이 더 명확하게 구분되는 것으로 보아 Phikon-v2가 의료기관 특징에 더 민감하게 반응한다는 것을 알 수 있습니다. 이는 모델의 강건성(robustness)에 영향을 미치는 중요한 요소입니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Embeddings for breast cancer colored by medical center for Phikon (left) and Phikon-v2 (right).
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
|---|---| 
| ![](https://arxiv.org/html/2501.18055/freq-same-class-phikon-v2.png) | ![](https://arxiv.org/html/2501.18055/freq-same-class-phikon.png) | 
| ![](https://arxiv.org/html/2501.18055/freq-same-class-UNI.png) | ![](https://arxiv.org/html/2501.18055/freq-same-class-UNI2-h.png) | 
| ![](https://arxiv.org/html/2501.18055/freq-same-class-Virchow-1280D.png) | ![](https://arxiv.org/html/2501.18055/freq-same-class-Virchow2-1280D.png) |{{< /table-caption >}}
> 🔼 이 표는 각 모델의 임베딩 공간에서 k번째 이웃이 같은 암 종류(파란색) 또는 같은 의료 센터(주황색)일 확률을 보여줍니다.  모델의 강건성이 증가하는 순서대로 정렬되어 있습니다. 부록 12에는 모든 결과가 포함되어 있습니다. 모든 모델에서 임베딩 공간의 근접성은 이미지가 동일한 의료 센터에서 나온 여부에 따라 크게 결정됩니다. Virchow2 모델을 제외한 모든 모델의 경우, 가장 가까운 200개 이웃에 대해 의료 센터가 암 종류보다 임베딩 근접성을 더 강하게 결정합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Fraction of samples for which the k-th neighbor has the same cancer type (blue) or medical center (orange), in order of increasing robustness. See Appendix 12 for all results. For all models, closeness in embedding space is strongly determined by whether the image comes from the same medical center. For all models except Virchow2, the medical center more strongly determines embedding proximity than the cancer type for the nearest 200 neighbors.
> </details>

{{< table-caption >}}
|---|---| 
|![https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-phikon-v2-nr_reps-5-nr_points-9.png](https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-phikon-v2-nr_reps-5-nr_points-9.png)|![https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-prov-gigapath-nr_reps-5-nr_points-9.png](https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-prov-gigapath-nr_reps-5-nr_points-9.png)| 
|![https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-UNI-nr_reps-5-nr_points-9.png](https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-UNI-nr_reps-5-nr_points-9.png)|![https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-H-optimus-0-nr_reps-5-nr_points-9.png](https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-H-optimus-0-nr_reps-5-nr_points-9.png)| 
|![https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-phikon-nr_reps-5-nr_points-9.png](https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-phikon-nr_reps-5-nr_points-9.png)|![https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-UNI2-h-nr_reps-5-nr_points-9.png](https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-UNI2-h-nr_reps-5-nr_points-9.png)| 
|![https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-Virchow-1280D-nr_reps-5-nr_points-9.png](https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-Virchow-1280D-nr_reps-5-nr_points-9.png)|![https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-Virchow2-1280D-nr_reps-5-nr_points-9.png](https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-Virchow2-1280D-nr_reps-5-nr_points-9.png)|{{< /table-caption >}}
> 🔼 이 표는 잘못 예측된 클래스의 이웃에서 동일한 센터의 혼란 요소 비율, 조직/암 유형 예측의 정확도, 의료 센터 예측의 정확도를 보여줍니다.  센터 강건성이 증가하는 순서대로 선택된 FM에 대해 정렬되어 있습니다. 모든 모델은 동일 센터 혼란 요소의 상당하고 유의미한 영향을 보여줍니다. 자세한 내용은 부록 9.3을 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Figure 3: Fraction of same-center confounders for neighbors from the incorrectly predicted class (red); accuracy of tissue / cancer type prediction (green); accuracy of medical center prediction (blue), sorted by order of increasing center-robustness for selected FMs. All models show a substantial and significant influence of same-center confounders. See Appendix 9.3 for a complete overview.
> </details>

{{< table-caption >}}
| Model | Cancer Type | Medical Center |
|---|---|---|
| hibou-b | https://arxiv.org/html/2501.18055/extracted/6170945/fig/hibou-b/embeddings-hibou-b-patch-level-tsne-2D-colored-by-project_code.png | https://arxiv.org/html/2501.18055/extracted/6170945/fig/hibou-b/embeddings-hibou-b-patch-level-tsne-2D-colored-by-shortname.png |
| phikon | https://arxiv.org/html/2501.18055/extracted/6170945/fig/phikon/embeddings-phikon-patch-level-tsne-2D-colored-by-project_code.png | https://arxiv.org/html/2501.18055/extracted/6170945/fig/phikon/embeddings-phikon-patch-level-tsne-2D-colored-by-shortname.png |
| phikon-v2 | https://arxiv.org/html/2501.18055/extracted/6170945/fig/phikon-v2/embeddings-phikon-v2-patch-level-tsne-2D-colored-by-project_code.png | https://arxiv.org/html/2501.18055/extracted/6170945/fig/phikon-v2/embeddings-phikon-v2-patch-level-tsne-2D-colored-by-shortname.png |
| EXAONEPath | https://arxiv.org/html/2501.18055/extracted/6170945/fig/EXAONEPath/embeddings-EXAONEPath-patch-level-tsne-2D-CLS-colored-by-project_code.png | https://arxiv.org/html/2501.18055/extracted/6170945/fig/EXAONEPath/embeddings-EXAONEPath-patch-level-tsne-2D-CLS-colored-by-shortname.png |
| UNI | https://arxiv.org/html/2501.18055/extracted/6170945/fig/UNI/embeddings-UNI-patch-level-tsne-2D-colored-by-project_code.png | https://arxiv.org/html/2501.18055/extracted/6170945/fig/UNI/embeddings-UNI-patch-level-tsne-2D-colored-by-shortname.png |
| UNI2-h | https://arxiv.org/html/2501.18055/extracted/6170945/fig/UNI2-h/embeddings-UNI2-h-patch-level-tsne-2D-CLS-colored-by-project_code.png | https://arxiv.org/html/2501.18055/extracted/6170945/fig/UNI2-h/embeddings-UNI2-h-patch-level-tsne-2D-CLS-colored-by-shortname.png |
| SRA_MoCo_v3 | https://arxiv.org/html/2501.18055/extracted/6170945/fig/SRA_MoCo_v3/embeddings-SRA_MoCo_v3-patch-level-tsne-2D-colored-by-project_code.png | https://arxiv.org/html/2501.18055/extracted/6170945/fig/SRA_MoCo_v3/embeddings-SRA_MoCo_v3-patch-level-tsne-2D-colored-by-shortname.png |{{< /table-caption >}}
> 🔼 이 표는 t-SNE(t-distributed Stochastic Neighbor Embedding) 기법을 사용하여 고차원의 병리 이미지 임베딩을 2차원 공간으로 투영한 결과를 보여줍니다. 왼쪽 열은 암 종류에 따라 색상으로 구분하고, 오른쪽 열은 의료 센터에 따라 색상으로 구분하여 각 패치의 분포를 시각적으로 나타냅니다. 이를 통해 각 모델이 암 종류와 의료 센터 정보를 얼마나 잘 학습했는지, 그리고 임베딩 공간 내에서 어떻게 구조화되어 있는지를 파악할 수 있습니다. 각 모델의 임베딩 공간에서 암 종류와 의료 센터 정보가 얼마나 분리되어 있는지, 그리고 서로 얼마나 밀접하게 연관되어 있는지를 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Colorings of the t-SNE embeddings of all patches by cancer type (left) and medical center (right)
> </details>

{{< table-caption >}}
| Model | Colored by project code | Colored by shortname |
|---|---|---|
| Virchow-1280D | https://arxiv.org/html/2501.18055/embeddings-Virchow-1280D-patch-level-tsne-2D-CLS-colored-by-project_code.png | https://arxiv.org/html/2501.18055/embeddings-Virchow-1280D-patch-level-tsne-2D-CLS-colored-by-shortname.png |
| Virchow-2560D | https://arxiv.org/html/2501.18055/embeddings-Virchow-2560D-patch-level-tsne-2D-CLS-avg-patch-colored-by-project_code.png | https://arxiv.org/html/2501.18055/embeddings-Virchow-2560D-patch-level-tsne-2D-CLS-avg-patch-colored-by-shortname.png |
| Virchow2-1280D | https://arxiv.org/html/2501.18055/embeddings-Virchow2-1280D-patch-level-tsne-2D-CLS-colored-by-project_code.png | https://arxiv.org/html/2501.18055/embeddings-Virchow2-1280D-patch-level-tsne-2D-CLS-colored-by-shortname.png |
| Virchow2-2560D | https://arxiv.org/html/2501.18055/embeddings-Virchow2-2560D-patch-level-tsne-2D-CLS-avg-patch-colored-by-project_code.png | https://arxiv.org/html/2501.18055/embeddings-Virchow2-2560D-patch-level-tsne-2D-CLS-avg-patch-colored-by-shortname.png |
| H-optimus-0 | https://arxiv.org/html/2501.18055/embeddings-H-optimus-0-patch-level-tsne-2D-colored-by-project_code.png | https://arxiv.org/html/2501.18055/embeddings-H-optimus-0-patch-level-tsne-2D-colored-by-shortname.png |
| prov-gigapath | https://arxiv.org/html/2501.18055/embeddings-prov-gigapath-patch-level-tsne-2D-colored-by-project_code.png | https://arxiv.org/html/2501.18055/embeddings-prov-gigapath-patch-level-tsne-2D-colored-by-shortname.png |{{< /table-caption >}}
> 🔼 그림 6은 다양한 병리학적 기초 모델에서 학습된 임베딩 공간의 시각화를 보여줍니다.  왼쪽 열은 암 유형에 따른 색상 분류를, 오른쪽 열은 의료 센터에 따른 색상 분류를 나타냅니다. 각 패치는 2차원 t-SNE 임베딩 공간의 점으로 표현되며, 점의 위치는 암 유형과 의료 센터 정보와 비교하여 분석됩니다. 이 시각화를 통해 각 모델이 암 유형과 의료 센터 정보를 얼마나 잘 학습했는지, 그리고 임베딩 공간 내에서 어떻게 조직화되는지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Colorings of the t-SNE embeddings of all patches by cancer type (left) and medical center (right)
> </details>

{{< table-caption >}}
| Model | Mean Accuracy (Cancer Type) | Std Dev (Cancer Type) | Mean Accuracy (Medical Center) | Std Dev (Medical Center) |
|---|---|---|---|---|
| SRA_MoCo_v3 | 0.486 | 0.036 | 0.692 | 0.027 |
| phikon | 0.829 | 0.037 | 0.987 | 0.012 |
| phikon-v2 | 0.83 | 0.038 | 0.993 | 0.007 |
| UNI | 0.713 | 0.034 | 0.956 | 0.013 |
| UNI2-h | 0.754 | 0.027 | 0.96 | 0.014 |
| hibou-b | 0.689 | 0.03 | 0.933 | 0.017 |
| Virchow-1280D | 0.727 | 0.038 | 0.932 | 0.022 |
| Virchow2-1280D | 0.786 | 0.03 | 0.957 | 0.016 |
| H-optimus-0 | 0.767 | 0.038 | 0.948 | 0.019 |
| prov-gigapath | 0.711 | 0.031 | 0.934 | 0.019 |
| EXAONEPath | 0.808 | 0.037 | 0.987 | 0.011 |{{< /table-caption >}}
> 🔼 표 2는 전체 임베딩 벡터를 입력값으로 사용하고 로지스틱 회귀를 학습 방법으로 사용하여 암 유형 예측 및 의료 센터 예측의 정확도에 대한 평균 및 표준 편차를 보여줍니다.  이 표는 다양한 병리학 기반 모델들의 암 유형 분류 성능과 의료 센터 식별 성능을 비교 분석하여 모델의 강건성(robustness)을 평가하는 데 사용되었습니다. 각 모델별로 암 유형 예측 정확도와 의료 센터 예측 정확도의 평균과 표준 편차가 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Mean and standard deviation for the accuracy of cancer type prediction and medical center prediction using the full embedding vectors as input and logistic regression as the learning method.
> </details>

{{< table-caption >}}
|---|---| 
| ![Uncaptioned image](https://arxiv.org/html/2501.18055/accuracy-ctype-center-full-embeddings-knn-nr_models-11-cv-5-rep-5-v1.png) | ![Uncaptioned image](https://arxiv.org/html/2501.18055/accuracy-ctype-center-full-embeddings-logistic-regression-nr_models-11-cv-5-rep-5-v1.png) | 
| ![Uncaptioned image](https://arxiv.org/html/2501.18055/accuracy-ctype-center-tsne-2D-knn-nr_models-13-cv-5-rep-5-v1.png) | ![Uncaptioned image](https://arxiv.org/html/2501.18055/accuracy-ctype-center-tsne-2D-logistic-regression-nr_models-13-cv-5-rep-5-v1.png) | {{< /table-caption >}}
> 🔼 이 표는 전체 임베딩 벡터(좌측 k-최근접 이웃 및 우측 로지스틱 회귀)와 2D t-SNE 임베딩 벡터(좌측 k-최근접 이웃 및 우측 로지스틱 회귀)를 입력으로 사용하여 암 유형 예측 정확도 대 중심 예측 정확도를 보여줍니다.  상단 행은 전체 임베딩 벡터를 사용한 결과를, 하단 행은 2D t-SNE 임베딩 벡터를 사용한 결과를 나타냅니다. 각각의 경우 k-최근접 이웃과 로지스틱 회귀의 두 가지 방법을 사용하여 암 유형과 병원 중심을 예측했으며, 그 결과를 비교 분석하여 모델의 강건성(robustness)을 평가합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7:  Top row: Accuracy of cancer type prediction vs. center prediction when using the full embedding vectors as input using knn (left) and logistic regression (right). Bottom row: Accuracy of cancer type prediction vs. center prediction when using the 2D t-SNE embedding vectors as input using knn (left) and logistic regression (right).
> </details>

{{< table-caption >}}
|---|---| 
|![](https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-phikon-v2-nr_reps-5-nr_points-9.png)|![](https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-EXAONEPath-nr_reps-5-nr_points-9.png)|
|![](https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-phikon-nr_reps-5-nr_points-9.png)|![](https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-UNI-nr_reps-5-nr_points-9.png)|
|![](https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-prov-gigapath-nr_reps-5-nr_points-9.png)|![](https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-H-optimus-0-nr_reps-5-nr_points-9.png)|
|![](https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-hibou-b-nr_reps-5-nr_points-9.png)|![](https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-SRA_MoCo_v3-nr_reps-5-nr_points-9.png)|
|![](https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-Virchow-1280D-nr_reps-5-nr_points-9.png)|![](https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-Virchow2-1280D-nr_reps-5-nr_points-9.png)|
|![](https://arxiv.org/html/2501.18055/confounding-neighbors-fraction-same-center-UNI2-h-nr_reps-5-nr_points-9.png)||{{< /table-caption >}}
> 🔼 그림 11은 의료 센터의 영향을 정량적으로 분석한 결과를 보여줍니다. 세 가지 주요 지표를 통해 모델의 성능을 평가합니다. 첫째, 조직 기원/암 유형 예측 정확도(녹색)는 모델이 실제 질병 특징을 얼마나 잘 파악하는지를 나타냅니다. 둘째, 의료 센터 예측 정확도(파란색)는 모델이 의료 센터 정보에 얼마나 민감한지를 보여줍니다. 마지막으로, 동일 의료 센터 혼란 요소의 비율(빨간색)은 잘못된 예측에 의료 센터 정보가 얼마나 영향을 미치는지를 나타냅니다. 모든 모델에서 의료 센터 정보가 예측에 상당하고 유의미한 영향을 미치는 것으로 나타났습니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Fraction of same-center confounders: (i) accuracy of tissue of origin / cancer type prediction (green), (ii) the accuracy of medical center prediction (blue), and (iii) fraction of same-center confounders. All models show a substantial and significant influence of same-center confounders.
> </details>

{{< table-caption >}}
|---|---| 
| <img src="https://arxiv.org/html/2501.18055/freq-same-class-phikon-v2.png" width="598" height="449"> | <img src="https://arxiv.org/html/2501.18055/freq-same-class-EXAONEPath.png" width="598" height="449"> | 
| <img src="https://arxiv.org/html/2501.18055/freq-same-class-phikon.png" width="598" height="449"> | <img src="https://arxiv.org/html/2501.18055/freq-same-class-prov-gigapath.png" width="598" height="449"> | 
| <img src="https://arxiv.org/html/2501.18055/freq-same-class-SRA_MoCo_v3.png" width="598" height="449"> | <img src="https://arxiv.org/html/2501.18055/freq-same-class-UNI.png" width="598" height="449"> | 
| <img src="https://arxiv.org/html/2501.18055/freq-same-class-hibou-b.png" width="598" height="449"> | <img src="https://arxiv.org/html/2501.18055/freq-same-class-H-optimus-0.png" width="598" height="449"> | 
| <img src="https://arxiv.org/html/2501.18055/freq-same-class-Virchow-1280D.png" width="598" height="449"> | <img src="https://arxiv.org/html/2501.18055/freq-same-class-UNI2-h.png" width="598" height="449"> | 
| <img src="https://arxiv.org/html/2501.18055/freq-same-class-Virchow2-1280D.png" width="598" height="449"> |  | {{< /table-caption >}}
> 🔼 이 그림은 k-최근접 이웃 중에서 같은 암 종류 또는 병원을 가진 샘플의 비율을 보여줍니다.  각 모델의 강건성 순서대로 정렬되어 있습니다. 파란색 선은 같은 암 종류를 가진 이웃의 비율을, 주황색 선은 같은 병원을 가진 이웃의 비율을 나타냅니다. 이를 통해 각 모델이 생물학적 특징(암 종류)과 혼란 요소(병원) 중 어느 쪽에 더 집중하는지 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Fraction of samples for which the k-th neighbor has the same cancer type (blue) or medical center (orange), in order of increasing robustness
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