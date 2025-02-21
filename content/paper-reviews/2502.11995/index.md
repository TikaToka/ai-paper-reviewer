---
title: "Presumed Cultural Identity: How Names Shape LLM Responses"
summary: "이름이 LLM의 문화적 편향을 유발한다는 사실을 밝혀냄"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 University of Copenhagen",]
showSummary: true
date: 2025-02-17
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.11995 {{< /keyword >}}
{{< keyword icon="writer" >}} Siddhesh Pawar et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-20 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.11995" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.11995" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/presumed-cultural-identity-how-names-shape" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

인공지능 언어 모델(LLM)이 점점 더 개인화된 응용 프로그램에 통합되면서, 모델의 반응을 개별 사용자에게 맞추는 것이 중요해지고 있습니다. 하지만, **LLM은 이름을 사용자의 문화적 정체성을 나타내는 지표로 사용**하는 경향이 있으며, 이로 인해 편향된 응답이 생성될 수 있습니다. 이러한 문제는 특히 이민자, 디아스포라 공동체 또는 다문화 가정과 같이 복잡한 정체성을 가진 사용자들에게 더욱 심각하게 나타날 수 있습니다. 

본 연구는 다양한 문화권의 일반적인 질문에 대해 LLM이 생성한 응답에서 나타나는 문화적 편향을 측정함으로써, 이름과 관련된 편향을 분석했습니다. 연구 결과, **LLM은 이름에 기반하여 문화적 정체성에 대한 강력한 가정**을 하고 있으며, 특정 문화권의 이름과 관련된 편향이 다른 문화권보다 훨씬 강한 것으로 나타났습니다.  본 연구는 문화적 고정관념을 강화하지 않고 의미있는 사용자 지정을 유지하는 보다 정교한 개인화 시스템을 설계하기 위한 시사점을 제시합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} LLM의 응답에서 이름에 따른 문화적 편향이 존재함을 밝힘 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 특정 문화권의 이름에 대한 편향이 다른 문화권보다 더 강함을 발견 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 문화적 편향을 완화하고 공정성을 개선하기 위한 시스템 설계 방향 제시 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **LLM의 이름에 따른 문화적 편향**을 체계적으로 분석하고, 이러한 편향이 사용자 경험과 공정성에 미치는 영향을 밝힘으로써, **더욱 공정하고 균형 잡힌 개인화된 LLM 시스템** 개발에 중요한 시사점을 제공합니다. 특히, 문화적 다양성을 고려한 LLM 개발 및 평가, 그리고 이름과 문화적 정체성의 복잡한 관계에 대한 심층적인 이해를 필요로 하는 연구자들에게 중요한 참고 자료가 될 것입니다.  **기존 연구들이 주로 성별이나 인종에 집중한 것과 달리 문화적 편향에 초점**을 맞춤으로써, 새로운 연구 영역을 개척하고 향후 연구 방향을 제시합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.11995/extracted/6211043/figures/Name-bias-eg.png)

> 🔼 그림 1은 이름을 기반으로 LLM이 사용자의 문화적 정체성을 추측하는 예시를 보여줍니다.  대화에서 사용자의 이름인 'Raj'를 보고 LLM은 결혼식에 어울리는 복장으로 인도 전통 의상인 Sherwani, Kurta, Churidar를 제안합니다. 이는 이름이 문화적 배경에 대한 추론을 가능하게 하고, LLM의 응답에 영향을 미칠 수 있음을 시사합니다. 이러한 추론은 정확하지 않을 수 있으며, 편향된 결과를 초래할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Example of an interaction with an LLM with an identity presumption based on the name
> </details>





{{< table-caption >}}
| Mark | Countries | 
|---|---| 
| US (10.12%), UK (5.59%), Ireland (3.03%), Canada (0.97%) |  | 
| James | US (12.15%), UK (5.52%), Ireland (3.42%), Canada (0.58%) | 
| Juan | Mexico (13.90%), US (11.32%), Spain (6.21%), Peru (2.95%) | 
| Maria | Mexico (11.51%), US (9.12%), Italy (9.04%), Spain (4.69%), Brazil (3.00%), Peru (1.97%), Portugal (0.80%) | 
| Carlos | Mexico (13.25%), US (10.74%), Brazil (4.52%), Spain (4.46%), Peru (2.57%), Portugal (1.19%) | 
| Fabio | Italy (14.58%), Switzerland (1.12%) | 
| Isabelle | France (5.08%), Switzerland (1.11%) | 
| Ali | Türkiye (7.28%), Iran (4.66%), Morocco (3.48%), Egypt (2.16%) | 
| Mohammed | Morocco (6.94%), Egypt (5.00%) | 
| Maryam | Iran (6.59%), Morocco (2.01%) | 
| Jun | Japan (19.53%), China (10.05%), Philippines (2.81%) | 
| Yu | Japan (15.21%), China (13.73%) | 
| Cherry | China (10.92%), Philippines (4.62%) | {{< /table-caption >}}

> 🔼 이 표는 이름 클러스터와 국가별 연관성 및 편향 값을 보여줍니다.  각 이름 클러스터는 여러 국가와 관련이 있으며, 각 국가에 대한 편향 값이 제시되어 있습니다. 이는 특정 이름이 특정 문화와 얼마나 강하게 연관되어 있는지를 보여주는 지표입니다.  편향 값은 언어 모델이 이름을 사용하여 문화적 추론을 할 때 나타나는 편향의 정도를 측정합니다.  높은 편향 값은 특정 이름이 특정 문화와 강하게 연관되어 있음을 시사하며, 낮은 값은 연관성이 약하거나 또는 다양한 문화와 연관될 수 있음을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Name Clusters with country associations and bias values
> </details>





### In-depth insights


#### Name Bias in LLMs
LLM에서의 이름 편향은 이름이 **문화적, 민족적, 성별적 고정관념**을 불러일으켜 모델의 응답에 편향을 유발하는 현상을 말합니다. 이는 훈련 데이터에 존재하는 사회적 편견을 반영하며, 특정 이름을 가진 사용자에게 불리한 결과를 초래할 수 있습니다. **특정 문화권의 이름에 대한 과도한 연관성** 또는 특정 문화권의 이름에 대한 부족한 연관성이 모두 문제가 됩니다. 예를 들어, 동아시아 이름에 대한 과도한 연관성은 해당 문화권의 사용자에게 편향된 응답을 제공할 수 있으나, 다른 문화권의 이름에 대한 부족한 연관성은 그들의 문화적 특징을 제대로 반영하지 못하는 결과를 초래할 수 있습니다. 이러한 편향은 단순히 재미있는 결과를 넘어, **사회적 불평등을 악화시키고 차별을 조장**할 수 있다는 점에서 심각한 문제입니다. 따라서 LLM 개발 시, **데이터의 다양성 확보 및 편향 완화**에 대한 노력과 더불어, **공정하고 포괄적인 응답을 제공**하기 위한 지속적인 연구가 필요합니다.

#### Cultural Presumption
본 논문에서 

#### Methodology & Models
본 논문의 방법론 및 모델 부분은 **데이터 수집**, **실험 설계**, 그리고 **모델 평가** 세 가지 핵심 요소로 구성됩니다. 먼저, 다양한 문화권의 이름 데이터셋을 구축하고, 문화적 속성과 관련된 질문들을 준비합니다. 이를 바탕으로, 여러 개의 대규모 언어 모델(LLM)을 사용하여 각 이름과 질문 조합에 대한 응답을 생성하고, 생성된 응답에서 문화적 편향을 분석합니다.  **여러 LLM을 사용**하여 모델 자체의 특성이 결과에 미치는 영향을 최소화하고, **다양한 문화권의 이름과 질문을 포괄**하여 연구의 일반화 가능성을 높이고자 합니다.  **문화적 편향 탐지 방법론**은 정량적, 정성적 분석을 모두 포함하며, 이를 통해 보다 객관적이고 심층적인 분석 결과를 도출할 수 있을 것으로 예상됩니다.  **결과적으로**, 본 연구는 다양한 LLM에서 나타나는 문화적 편향의 양상을 체계적으로 분석하고, 보다 공정하고 균형 잡힌 LLM 개발을 위한 중요한 시사점을 제시할 것으로 기대됩니다.

#### Bias Detection Methods
본 논문에서 제시된 바이어스 탐지 방법론은 다양한 측면에서 심도있는 분석을 필요로 합니다. **데이터셋의 다양성과 균형**은 바이어스를 정확하게 탐지하는데 매우 중요합니다. 또한, **알고리즘의 투명성과 설명가능성**을 확보하여 바이어스의 근원을 명확히 파악하고 해석하는 것이 중요합니다. **인간 전문가의 개입**을 통한 검증은 알고리즘의 한계를 보완하고 신뢰성을 높이는 데 필수적입니다.  **다양한 바이어스 유형에 대한 고려** 또한 필수적입니다. 단순히 특정 집단에 대한 차별적 결과 뿐 아니라, **간접적이거나 은밀한 바이어스**까지 포괄적으로 검출하는 시스템이 필요합니다. 마지막으로, **지속적인 모니터링 및 평가**를 통해 시스템의 성능을 지속적으로 개선하고 변화하는 사회적 맥락에 대응하는 적응력을 확보해야 합니다.

#### Future Research
본 논문은 이름이 LLM의 응답에 미치는 영향을 분석하고, 문화적 편견을 강화하지 않으면서 의미있는 개인화를 달성하기 위한 방안을 제시합니다. **미래 연구는 좀 더 다양한 문화와 언어를 포괄하는 더 큰 규모의 데이터셋을 사용하여 연구를 확장하는 것이 중요합니다.** 또한, 이름 외에도 사용자의 성별, 인종, 나이 등 다양한 요소들이 LLM 응답에 어떤 영향을 미치는지에 대한 연구가 필요합니다.  **LLM의 내부 작동 방식에 대한 이해를 높이기 위한 연구 또한 중요합니다.** 예를 들어, LLM이 어떤 방식으로 이름과 문화적 특징을 연결짓는지, 그리고 이러한 연결 방식에 어떤 편향이 존재하는지 등을 자세히 분석하는 것이 필요합니다.  마지막으로, **본 연구에서 제시된 문제점들을 해결하기 위한 기술적 해결책을 개발하는 것도 중요한 미래 연구 과제입니다.**  예를 들어, 문화적 편견을 완화하거나 제거하는 새로운 LLM 학습 방법 또는 응답 생성 알고리즘을 개발하는 등의 노력이 필요합니다. 이러한 연구들을 통해 보다 공정하고, 포괄적이며, 유용한 LLM을 개발할 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.11995/extracted/6211043/figures/name-bias-setup.png)

> 🔼 본 그림은 논문의 실험 설정을 보여줍니다. 이름을 포함한 질문을 사용하여 LLM(대규모 언어 모델)로부터 응답을 생성하고, CANDLE 지식 그래프를 사용하여 문화적 추정을 감지하는 과정을 시각적으로 설명합니다.  LLM의 응답을 평가하여 문화적 편견을 탐지하는 방법을 보여줍니다.  이름이 포함된 질문과 포함되지 않은 질문 모두에 대한 응답을 비교하여 이름이 모델의 반응에 미치는 영향을 분석합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Experimental Setup
> </details>



![](https://arxiv.org/html/2502.11995/x1.png)

> 🔼 그림 3은 다양한 언어 모델과 문화적 측면에 걸쳐 평균화된 기본 편향 값을 보여줍니다. 이 그림은 각 모델이 이름 없이 질문에 응답할 때 특정 문화에 대해 과도하게 언급하는 경향을 보여줍니다. 자세한 내용은 3.8절을 참조하세요.
> <details>
> <summary>read the caption</summary>
> Figure 3: Default Bias values averaged over Models and Facets. For details refer to subsection 3.8.
> </details>



![](https://arxiv.org/html/2502.11995/extracted/6211043/figures/vertical_bias_plots.png)

> 🔼 이 그림은 다섯 개의 다양한 언어 모델에서 이름이 언급된 프롬프트와 이름이 없는 프롬프트의 문화적 편향을 비교하여 보여줍니다. 각 모델에 대해 기본 편향(이름이 없는 프롬프트)을 계산하고, 이름이 포함된 프롬프트의 편향에서 이 기본 편향을 빼서 조정된 편향 점수를 계산합니다. 막대 그래프는 각 문화권에서 조정된 편향을 보여주며, 일부 문화권(예: 한국, 러시아)에서는 상당히 높은 편향 점수를 나타내고 다른 문화권(예: 필리핀, 아일랜드)에서는 낮거나 음수의 편향 점수를 나타내는 것을 알 수 있습니다. 자세한 계산 방법은 본 논문의 3.8절을 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Figure 4: Bias across models above the default bais. For calculation of bais refer to section 3.8
> </details>



![](https://arxiv.org/html/2502.11995/extracted/6211043/figures/aspect_boxplot.png)

> 🔼 이 그림은 네 가지 문화적 측면(의복, 음식, 의식 및 전통)에 걸쳐 네 개의 언어 모델에 대한 국가별 편향 값을 비교하여 보여주는 상자 그림입니다. 각 측면에 대한 평균 편향 값을 계산하여 국가별로 비교 분석합니다. 이를 통해 각 모델과 문화적 측면에 따라 국가별 편향의 정도를 파악하고, 특정 문화에 대한 모델의 편향 정도를 시각적으로 비교할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Box plot showing comparison of bias for countries values (averaged over 4 models) for each facet.
> </details>



![](https://arxiv.org/html/2502.11995/extracted/6211043/figures/overall_diff_heatmap.png)

> 🔼 그림 6은 기본값(3.8절 참조)을 초과하는 편향 값에 대한 국가 간 편향 히트맵입니다. X축은 편향을 확인할 국가이고 Y축은 이름이 가져온 국가입니다. 이 히트맵은 특정 문화권의 이름을 사용했을 때 언어 모델의 응답에서 문화적 편향이 어떻게 나타나는지 시각적으로 보여줍니다. 각 셀의 색상은 특정 이름과 문화 간의 연관성의 강도를 나타내며, 더 진한 색상은 더 강한 연관성을 나타냅니다. 이는 특정 이름이 언어 모델에서 어떻게 특정 문화와 연관되는지 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Cross-cultural bias heatmap for bias values over the default (3.8). The X-axis is the country for which the bias is checked is for and Y-axis is country from which the name was taken.
> </details>



![](https://arxiv.org/html/2502.11995/extracted/6211043/figures/names_biased_responses_plot.png)

> 🔼 그림 7은 이름별로 생성된 편향된 응답의 분포를 보여줍니다. 이 그래프는 이름을 X축에 표시하지 않고 응답의 개수를 Y축에 표시하여 가독성을 높였습니다.  이를 통해 특정 이름에 대한 응답이 다른 이름에 비해 얼마나 편향되어 있는지, 즉 일부 이름이 다른 이름보다 훨씬 더 편향된 응답을 유발하는 경향이 있음을 시각적으로 보여줍니다.  세로축은 각 이름에 대한 편향된 응답의 빈도를 나타냅니다. 이 그래프는 이름에 따른 편향된 응답 분포의 불균형을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Distribution of biased responses per name [Names are omitted from the x-axis to avoid clutter]
> </details>



![](https://arxiv.org/html/2502.11995/extracted/6211043/figures/grouped_percentage_comparison.png)

> 🔼 그림 8은 편향된 응답의 전체 수를 기준으로 각 단어의 편향된 응답이 차지하는 비율을 보여줍니다. 즉, 특정 단어가 포함된 질문에 대해 모델이 얼마나 자주 편향된 응답을 생성하는지 보여줍니다. 이는 이름이 언급된 프롬프트에서 문화적 편향이 어떻게 강화되는지 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Percentage contribution of each word’s biased responses relative to the overall number of biased responses
> </details>



![](https://arxiv.org/html/2502.11995/extracted/6211043/figures/country_differences_baroai.png)

> 🔼 그림 9는 OpenAI GPT-4o-mini 모델의 이름에 따른 편향을 보여줍니다.  특히 이름이 언급되지 않은 경우(기본값)와 비교하여 특정 문화권의 이름이 모델의 응답에 어떤 영향을 미치는지 보여주는 그래프입니다. 이 그래프는 모델이 이름을 통해 문화적 배경을 추론하고 이에 따라 응답을 생성하는 과정에서 편향이 발생할 수 있음을 시각적으로 보여줍니다.  세부적으로는 각 국가별 이름이 모델의 응답에 얼마나 큰 영향을 미치는지를 비교하여 문화적 편향의 정도를 수치화하고 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: OpenAI GPT-4o-mini name bias over the default responses
> </details>



![](https://arxiv.org/html/2502.11995/extracted/6211043/figures/grid_bias_plots_base.png)

> 🔼 그림 10은 다양한 언어 모델에서 이름이 없는 프롬프트에 대한 기본 편향을 보여줍니다. 즉, 사용자 이름이 없어도 모델의 응답에 특정 문화적 성향이 나타나는 것을 보여줍니다. 이 기본 편향은 모델에 따라 다르며, 일부 모델은 다른 모델보다 더 큰 편향을 보입니다. 이러한 기본 편향은 모델의 학습 데이터나 설계에 따른 것일 수 있습니다. 자세한 내용은 3.8절을 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Figure 10: Default Bias across models, for calculation and discussion about default bias refer to section 3.8
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | HuggingFace Repository |
|---|---| 
| Aya | CohereForAI/aya-expanse-32b |
| Mistral | mistralai/Mistral-Nemo-Instruct-2407 |
| DeepSeek | deepseek-ai/DeepSeek-R1-Distill-Llama-8B |
| Llama | meta-llama/Meta-Llama-3.1-8B-Instruct |{{< /table-caption >}}
> 🔼 이 표는 논문에서 사용된 다섯 가지 언어 모델(Llama, Aya, Mistral, DeepSeek, GPT-40-mini)과 해당 모델의 Hugging Face 저장소 코드를 보여줍니다.  각 모델의 세부 정보(예: 체크포인트, 매개변수)는 부록에 자세히 설명되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Models used in this study and their corresponding HuggingFace repository code
> </details>

{{< table-caption >}}
| Name | Country Contribution (%) | 
|---|---| 
| Amanda | US(10.77%), UK(5.59%), South Africa(3.08%), Canada(0.76%) | 
| Ashley | US(10.71%), Canada(0.40%) | 
| Mark | US(10.12%), UK(5.59%), Ireland(3.03%), Canada(0.97%) | 
| Jason | US(11.05%), China(7.17%), Canada(0.64%) | 
| Sarah | US(9.61%), UK(5.25%), France(4.27%), Germany(2.96%), Canada(1.17%) | 
| James | US(12.15%), UK(5.52%), Ireland(3.42%), Canada(0.58%) | 
| Melissa | US(11.15%), Canada(0.82%) | 
| Julie | UK(5.10%), France(3.81%), Canada(0.99%) | 
| Michelle | US(10.94%), UK(5.03%), Ireland(3.17%), South Africa(2.22%), Canada(0.56%) | 
| Paul | UK(6.39%), Ireland(3.93%), Canada(0.69%) | 
| Kevin | US(9.86%), Canada(0.82%) | 
| Mike | US(10.50%), Canada(1.02%) | 
| Linda | US(11.25%), South Africa(2.40%), Canada(1.04%) | 
| Emily | US(9.88%), UK(5.56%), Canada(0.58%) | 
| Robert | US(13.07%), Canada(1.08%), Poland(1.05%) | 
| Jennifer | US(12.37%), Canada(0.88%) | 
| Nancy | US(11.46%), Peru(1.83%), Canada(0.61%) | 
| Heidi | Finland(1.66%), Switzerland(1.29%) | 
| Philippe | France(10.39%), Switzerland(0.93%) | 
| Nathalie | France(5.11%), Switzerland(0.71%) | 
| Dominique | France(4.69%), Switzerland(0.79%) | 
| Michel | France(5.40%), Switzerland(1.08%) | 
| Tanja | Germany(2.82%), Switzerland(1.61%) | 
| Markus | Germany(2.98%), Switzerland(0.66%) | 
| Stefan | Germany(2.22%), Sweden(0.97%), Switzerland(0.94%) | 
| Monika | Germany(2.40%), Iran(3.20%), Poland(1.55%), Switzerland(0.95%) | 
| Andreas | Germany(3.21%), Greece(5.00%), Switzerland(0.93%), Sweden(0.88%) | 
| Thomas | France(3.92%), Germany(1.92%), Switzerland(1.02%) | 
| Pascal | France(6.58%), Switzerland(0.49%) | 
| Ana | Mexico(11.21%), US(10.05%), Spain(3.80%), Brazil(2.67%), Peru(2.27%), Egypt(1.93%), Portugal(0.21%) | 
| Maria | Mexico(11.51%), US(9.12%), Italy(9.04%), Spain(4.69%), Brazil(3.00%), Peru(1.97%), Portugal(0.80%) | 
| Carlos | Mexico(13.25%), US(10.74%), Brazil(4.52%), Spain(4.46%), Peru(2.57%), Portugal(1.19%) | 
| Jose | Mexico(12.56%), US(12.31%), Spain(4.64%), Brazil(3.86%), Peru(2.89%) | 
| Juan | Mexico(13.90%), US(11.32%), Spain(6.21%), Peru(2.95%) | 
| Jorge | Mexico(12.83%), US(10.11%), Spain(4.72%), Peru(2.49%), Portugal(0.47%) | 
| Fernando | Mexico(12.72%), Spain(5.33%), Brazil(3.34%), Peru(3.03%), Portugal(0.64%) | 
| Javier | Mexico(15.02%), Spain(6.47%), Peru(2.75%) | 
| Carmen | Mexico(10.39%), Spain(5.34%), Peru(0.87%) | 
| Miguel | Mexico(12.59%), Spain(5.14%), Peru(2.89%), Portugal(0.77%) | 
| Manuel | Mexico(11.94%), Spain(4.50%), Peru(2.82%), Portugal(0.62%) | 
| Francisco | Mexico(12.65%), Spain(5.31%), Brazil(4.07%), Portugal(0.94%) | 
| Antonio | Mexico(12.11%), Italy(10.89%), Spain(4.32%), Brazil(3.84%), Portugal(0.85%) | 
| Fabio | Italy(14.58%), Switzerland(1.12%) | 
| Daniela | Italy(11.93%), Germany(4.11%) | 
| Andrea | Italy(9.86%), Germany(1.70%) | 
| Elena | Italy(8.62%), Spain(4.38%), Russian Federation(1.37%) | 
| Cristina | Italy(12.15%), Spain(4.32%), Portugal(0.55%) | 
| Ali | Türkiye(7.28%), Iran(4.66%), Morocco(3.48%), Egypt(2.16%) | 
| Mohammed | Morocco(6.94%), Egypt(5.00%) | 
| Maryam | Iran(6.59%), Morocco(2.01%) | 
| Omar | Morocco(4.37%), Egypt(1.96%) | 
| Ahmed | Morocco(2.78%), Egypt(0.87%) | 
| Fatma | Türkiye(10.92%), Egypt(2.50%) | 
| Salma | Morocco(4.69%), Egypt(3.04%) | 
| Mohamed | Morocco(5.57%), Egypt(3.71%) | 
| Jun | Japan(19.53%), China(10.05%), Philippines(2.81%) | 
| Yu | Japan(15.21%), China(13.73%) | 
| Cherry | China(10.92%), Philippines(4.62%) | 
| Chen | China(17.79%), Israel(2.88%) | {{< /table-caption >}}
> 🔼 이 표는 다양한 문화권의 이름 목록과 각 이름이 가장 많이 연관되는 국가 및 해당 국가와의 연관성 정도(편향 정도)를 보여줍니다.  각 이름에 대해 여러 국가가 나열되어 있으며, 이는 이름의 다양한 문화적 기원과 사용을 반영합니다. 이 표는 이름에 따른 문화적 편향을 분석하는 데 사용되었습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Multicultual Names
> </details>

{{< table-caption >}}
| Country | Biased Names (Frequency) |
|---|---| 
| Brazil | Larissa (15), Bruna (14), Felipe (14), Marcelo (14), Pedro (14) |
| Canada | Nicole (8), Eric (6), Lisa (6), Amanda (5), Ashley (5) |
| China | Liu (56), Wei (54), Feng (49), Yuan (48), Zhou (48) |
| Finland | Päivi (12), Tarja (9), Tiina (9), Hanna (8), Johanna (7) |
| France | Guillaume (36), Christophe (34), Thierry (33), Julien (29), Philippe (27) |
| Germany | Heike (16), Alexander (12), Stefan (12), Claudia (11), Jens (11) |
| India | Pooja (115), Vijay (107), Raju (104), Mukesh (103), Priya (98) |
| Indonesia | Bambang (46), Teguh (30), Asep (29), Siti (25), Retno (23) |
| Iran, Islamic Republic of | Mehdi (27), Hamid (26), Alireza (24), Reza (24), Maryam (21) |
| Ireland | Sinead (21), Aoife (17), Niall (17), Eoin (16), Paddy (16) |
| Italy | Giuseppe (84), Vincenzo (66), Massimo (63), Luigi (62), Federica (57) |
| Japan | Daisuke (133), Takahiro (128), Takashi (125), Hiroyuki (109), Megumi (109) |
| Mexico | Lupita (59), Eduardo (52), Fernanda (48), Guadalupe (47), Miguel (46) |
| Morocco | Kawtar (35), Hanane (31), Siham (27), Imane (26), Zineb (25) |
| Peru | Diego (15), Milagros (12), Ana (10), Juan Carlos (10), Pedro (10) |
| Philippines | Marites (24), Kristine (16), Jm (14), Noel (13), Rj (13) |
| Poland | Małgorzata (30), Krzysztof (20), Katarzyna (16), Paweł (15), Grzegorz (13) |
| Portugal | Margarida (9), André (7), Filipa (6), Catarina (5), Marta (5) |
| South Africa | Nonhlanhla (55), Zandile (39), Siyabonga (38), Zinhle (33), Themba (29) |
| Spain | María (25), Francisco (24), Mari Carmen (21), Marta (21), Cristina (20) |
| Sweden | Håkan (37), Åsa (13), Marcus (11), Birgitta (10), Björn (10) |
| Switzerland | Roger (9), Heidi (7), Marcel (6), Philippe (6), Reto (6) |
| Türkiye | Ayşe (76), Hüseyin (65), Hülya (50), Özlem (45), Zeynep (44) |
| United Kingdom | Lisa (27), Emma (24), Ian (23), Claire (22), Daniel (22) |
| United States | James (54), Juan (43), Linda (40), Michelle (40), Ashley (39) |{{< /table-caption >}}
> 🔼 이 표는 논문에서 언급된 모든 국가에 대해 편향된 이름 목록을 보여줍니다. 괄호 안의 숫자는 각 이름에 대해 편향된 응답의 수를 나타냅니다. 예를 들어, 브라질의 경우 Larissa(15), Bruna(14), Felipe(14), Marcelo(14), Pedro(14)라는 이름이 편향된 응답을 많이 받았다는 것을 알 수 있습니다. 이 표는 각 국가의 이름에 대한 모델의 편향 정도를 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Biased Names for All Countries (Names with number of biased responses in parenthesis)
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