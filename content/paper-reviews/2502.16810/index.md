---
title: "Grounded Persuasive Language Generation for Automated Marketing"
summary: "AI 기반 부동산 마케팅 에이전트가 인간 전문가보다 더 나은 마케팅 문구를 생성한다는 것을 입증한 연구"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Stanford University",]
showSummary: true
date: 2025-02-24
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.16810 {{< /keyword >}}
{{< keyword icon="writer" >}} Jibang Wu et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-25 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.16810" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.16810" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/grounded-persuasive-language-generation-for" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

본 연구는 **대규모 언어 모델(LLM)**을 활용하여 **사실에 기반한 설득력 있는 마케팅 콘텐츠를 자동 생성**하는 새로운 접근 방식을 제시합니다. 기존 연구들은 LLM의 설득력에 대한 측정 및 평가에 어려움을 겪었고, 특히 사실과 맥락을 고려하지 않은 설득으로 인한 오류 가능성에 대한 우려가 제기되었습니다.  이러한 문제점들을 해결하기 위해, 본 연구는 부동산 광고를 중심으로 실제 마케팅 환경에서의 LLM 적용 가능성을 탐구했습니다.

본 연구는 세 가지 주요 모듈(Grounding, Personalization, Marketing)을 포함한 에이전트 기반 프레임워크를 제시합니다.  **Grounding Module**은 전문가 수준의 판단으로 시장성 있는 특징을 예측하고, **Personalization Module**은 사용자 선호도를 반영하며, **Marketing Module**은 사실 정확성과 지역 특징을 보장합니다.  실제 사용자를 대상으로 한 실험 결과는, 본 연구의 접근 방식으로 생성된 마케팅 문구가 **인간 전문가 작성 문구보다 훨씬 선호도가 높음**을 보여줍니다. 이는 대규모, 표적화된 마케팅 자동화를 위한 LLM 기반 프레임워크의 가능성과 **사실 기반의 책임감 있는 콘텐츠 생성**의 중요성을 강조합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} AI 기반 에이전트가 인간 전문가보다 더 설득력 있는 부동산 광고 문구 생성 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 사실에 기반한 설득력 있는 LLM 기반 마케팅 자동화 프레임워크 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 실험적 검증을 통해 AI 기반 마케팅의 효과와 윤리적 고려사항에 대한 통찰력 제공 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대규모 언어 모델(LLM)**을 사용하여 **사실에 기반한 설득력 있는 마케팅 콘텐츠를 자동 생성**하는 프레임워크를 제시함으로써, 자동화된 마케팅 분야의 혁신적인 발전과 함께 **윤리적 문제**에 대한 심도 있는 고찰을 제공합니다.  LLM의 설득력 있는 콘텐츠 생성 능력을 실제 마케팅 환경에 적용하고, 그 효과를 실험적으로 검증하여 **학계 및 산업계에 시사하는 바가 큼**을 보여줍니다. 특히, **사실 기반의 책임감 있는 마케팅 자동화**에 대한 새로운 지평을 열어줌으로써, 향후 연구 방향을 제시하고 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.16810/x1.png)

> 🔼 AI Realtor의 설계 파이프라인을 보여주는 그림입니다. 사용자의 입력(집에 대한 정보)을 받아 Grounding Module, Personalization Module, Marketing Module의 세 가지 모듈을 거쳐 최종적으로 설득력 있는 부동산 광고 문구를 생성하는 과정을 시각적으로 나타냅니다. 각 모듈은 고유한 기능을 수행하며, Grounding Module은 부동산의 특징을 파악하고, Personalization Module은 사용자의 선호도를 반영하며, Marketing Module은 지역 특성과 사실 정확성을 보장합니다.  모듈 간의 상호 작용과 정보 흐름을 통해 최종적으로 사용자에게 매력적인 부동산 광고 문구를 생성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Illustration of the Design Pipeline of AI Realtor.
> </details>





{{< table-caption >}}
| Field Name | Data Type |
|---|---| 
| bedrooms | float64 |
| bathrooms | float64 |
| price | float64 |
| description | object |
| living_area_value | float64 |
| lot_area_value | float64 |
| area_units | object |
| brokerage_name | object |
| zipcode | object |
| street_address | object |
| home_type | object |
| time_on_zillow | object |
| page_view_count | float64 |
| favorite_count | float64 |
| home_insights | object |
| neighborhood_region | object |
| scraped_at | object |
| url | object |
| city | object |
| state | object |
| year_built | float64 |
| county | object |
| avg_school_rating | float64 |
| id | object |
| time_on_zillow_days | float64 |
| score | float64 |
| jpeg_urls | array |{{< /table-caption >}}

> 🔼 표 1은 논문에서 사용된 부동산 매물 데이터의 일부 중요 열을 보여줍니다.  전체 데이터셋은 95개의 열로 구성되며, 침실 수, 욕실 수, 가격, 주소 등과 같은 다양한 기능을 포함합니다. 이러한 풍부한 기능들은 다양한 기계 학습 모델을 훈련하고 평가하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Listing data, subset of important columns
> </details>





### In-depth insights


#### AI Realtor Design
본 논문에서 제안하는 AI 리얼터 설계는 **대규모 언어 모델(LLM)**을 기반으로 하여 부동산 매물 설명 생성을 자동화하는 에이전트 시스템입니다. 이 시스템은 사용자의 선호도를 반영하면서도 사실적인 정보를 강조하는 설득력 있는 마케팅 콘텐츠를 생성하는 데 중점을 둡니다. **기반(Grounding), 개인화(Personalization), 마케팅(Marketing)** 세 가지 주요 모듈로 구성되어, 전문가 수준의 판단을 모방하여 시장성 있는 특징을 예측하고, 사용자의 선호도에 맞춰 콘텐츠를 조정하며, 지역 특징을 포함하여 사실 정확성을 보장합니다.  **실제 부동산 거래 데이터를 활용한 실험**을 통해 제안된 방법의 효과를 검증하며, 기존 전문가 작성물 대비 우수한 성능을 보임으로써, **LLM 기반의 에이전트 프레임워크**를 통한 대규모 표적 마케팅 자동화의 가능성을 제시합니다. 특히, **사실 기반의 설득**에 초점을 맞춰 윤리적 문제를 최소화하는 데 기여하는 점이 주목할 만합니다.

#### Persuasion Metrics
논문에서 "설득 지표" 항목에 대한 심도있는 고찰은 설득력 측정의 어려움과 다양한 접근 방식의 필요성을 강조해야 합니다. **정량적 지표** (예: 전환율, 참여율)는 실질적 영향을 평가하지만, **정성적 지표** (예: 사용자 피드백, 설문조사 결과)는 맥락적 이해와 심층적 분석을 제공합니다. 따라서 효과적인 설득 지표는 **정량적 및 정성적 지표를 통합**하여 다각적 관점을 제시해야 하며, 도메인 특수성, 사용자 특성 및 맥락적 요인을 고려하여 **맞춤형 설계**가 필요합니다. 아울러, **인공지능 기반 평가 시스템**을 활용한 객관적 측정과 **인간 전문가 평가**를 통한 주관적 검토를 병행하는 혼합방식이 신뢰성 있는 결과 도출에 중요하며, 윤리적 문제와 편향 가능성에 대한 고려가 필수적입니다.  **지속적인 지표 개선 및 검증**을 통해 설득 전략의 효과성을 정확하게 평가하고 개선하는 체계를 구축해야 합니다.

#### Feature Engineering
본 논문에서 제시된 특징 공학(Feature Engineering)은 **LLM의 강점을 활용하여 실제 부동산 데이터에서 판매 가능한 특징(marketable features)을 효과적으로 추출하는 과정**을 의미합니다. 단순히 기존의 전문가 지식에 의존하는 대신, **LLM의 풍부한 지식과 자연어 처리 능력**을 활용하여 부동산 목록의 원시 속성(raw attributes)을 **사람이 이해할 수 있는 특징으로 변환**합니다. 이를 위해, **LLM 기반의 지도 학습 방식**을 통해 부동산 설명 텍스트에서 특징들을 추출하고 분류하며, **다양한 특징의 상호 관계와 중복성을 고려**하여 계층적 구조의 특징 체계(schema)를 구축합니다. 또한, **인간 전문가의 검토 과정**을 통해 LLM의 잠재적 오류를 최소화하고 체계의 정확성을 높입니다.  **이러한 과정은 대규모 데이터셋에 대해 자동화**되어 있어, **시간과 비용을 절감**하면서 효율적인 특징 추출이 가능합니다.  결과적으로, **LLM을 기반으로 한 특징 공학은 객관적인 데이터 분석과 인간의 직관을 결합**하여 보다 정확하고 효과적인 부동산 마케팅을 가능하게 하는 핵심 요소입니다.  **데이터 기반의 객관성과 인간의 전문성을 결합**하는 이러한 접근 방식은 다른 도메인에서의 마케팅 자동화에도 적용될 수 있는 잠재력을 지닙니다.

#### Human Feedback
본 논문에서 'Human Feedback' 섹션은 **인간 피험자의 반응을 통해 모델 성능을 평가하는 실험 설계 및 결과**에 초점을 맞춥니다.  **실험 참여자들은 부동산 매물 정보와 두 개의 서로 다른 설명문(AI 모델 생성 및 전문가 작성)을 비교**하고 선호도를 평가하는 과제를 수행했습니다.  **Elo rating 시스템을 사용하여 정량적 비교**를 수행했으며, AI 모델이 **인간 전문가보다 더 높은 설득력을 가진다는 것을 보여주는 결과**를 얻었습니다.  **실험의 신뢰성 확보를 위해 다양한 조치(설문 사전 검사, 주의 집중 확인, 대조군 설정 등)**를 취했으며, 이는 **결과의 객관성과 타당성을 높이는 데 기여**했습니다.  **AI 피드백을 통한 보조 평가**도 시도되었으나, **인간 피드백만큼의 신뢰성을 확보하지 못했음**을 인정하고 있습니다. 전반적으로, 이 섹션은 **정교하게 설계된 인간 피드백 기반 평가를 통해 AI 모델의 설득력을 검증**하는 과정을 상세히 보여주는 동시에, **AI 기반 평가의 한계점도 함께 제시**하여 연구의 신뢰성을 높였습니다.

#### AI Feedback Limits
AI 피드백의 한계에 대한 심층적인 논의는 **모델의 신뢰성과 정확성에 대한 의문**을 제기합니다. 인간의 피드백을 모방한 AI 피드백은 편향되거나 불완전한 데이터에 의존할 수 있으며, **예측의 정확도가 떨어지고 변동성이 클 수 있습니다.** 특히 사용자의 개성이나 선호도를 정확히 반영하지 못하는 경우가 발생하며, 이로 인해 **AI 피드백 시스템의 신뢰도를 저해**할 수 있습니다. 또한, AI 피드백 시스템은 텍스트 길이에 대한 편향이나, 모호한 사용자 의견 등의 문제를 야기할 수 있습니다. 따라서 **AI 피드백을 실제 평가에 활용하기 위해서는 이러한 한계점을 명확히 인식하고, 보완적인 방법을 모색**하는 것이 중요합니다.  **인간 피드백과 AI 피드백을 병행**하여 서로의 강점을 활용하고 약점을 보완하는 전략이 필요하며, **지속적인 시스템 개선을 통한 신뢰성 확보**가 필수적입니다.  **데이터의 양과 질 개선**, **모델의 정확도 향상** 등을 통해 AI 피드백의 신뢰도를 높이고, 실제 평가에 활용 가능성을 높여야 합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.16810/extracted/6227460/figures/schema_induction_icml_ver.png)

> 🔼 그림 2는 실제 부동산 목록의 텍스트 설명에서 특징 스키마(feature schema)를 유도하여 생성하는 과정을 보여줍니다.  LLM(Large Language Model)을 사용하여 Zillow 플랫폼의 5만 개가 넘는 부동산 목록의 원시 속성 데이터에서 키워드를 추출합니다. 이후, 중복되거나 의미가 비슷한 키워드들을 제거하고, 계층적 구조를 가진 특징 스키마를 생성합니다. 이 스키마의 질을 평가하기 위해 사람이 개입하여 오류를 수정하고 개선합니다. 최종적으로, 생성된 특징 스키마는 추후 부동산 마케팅 텍스트에서 특징을 학습하는 데 사용됩니다. 이 과정은 인간의 개입을 최소화하면서 LLM의 광범위한 지식을 활용하여 비지도 학습 방식으로 전문가 수준의 통찰력을 얻는 새로운 패러다임을 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Illustration of the inductive feature schema construction pipeline.
> </details>



![](https://arxiv.org/html/2502.16810/x2.png)

> 🔼 그림 3(a)는 다양한 모델의 성능을 Elo 등급으로 비교한 것입니다. Elo 등급은 모델의 전반적인 설득력을 나타내는 지표로, 높을수록 설득력이 높다는 것을 의미합니다. 그림에서는 AI Realtor 모델이 다른 모델들(Vanilla, SFT, Human, Control 등)에 비해 훨씬 높은 Elo 등급을 기록한 것을 확인할 수 있습니다. 이는 AI Realtor 모델이 부동산 광고 문구 생성에 있어서 인간 전문가보다 더 설득력 있는 문구를 생성한다는 것을 시사합니다.  특히, AI Realtor 모델의 세 가지 주요 모듈(Grounding, Personalization, Marketing)이 각각 설득력 향상에 기여하는 것을 보여주는 추가적인 실험 결과도 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> (a) Elo Ratings
> </details>



![](https://arxiv.org/html/2502.16810/x4.png)

> 🔼 그림 3(b)는 다양한 모델의 상대적 설득력을 보여주는 승률을 나타냅니다. 각 모델은 다른 모델과 비교하여 얼마나 자주 선호되는지 보여줍니다. 이는 인간 피험자의 평가를 기반으로 합니다.
> <details>
> <summary>read the caption</summary>
> (b) Win Rates
> </details>



![](https://arxiv.org/html/2502.16810/x6.png)

> 🔼 그림 3은 Elo 등급 및 승률을 사용하여 모델 성능을 비교한 것입니다. Elo 등급은 전반적인 설득력을 나타내고, 승률은 상대적인 설득력을 반영합니다. 두 지표 모두 인간 피험자의 평가를 기반으로 합니다.  AI Realtor 모델이 인간 전문가 및 기타 기준 모델보다 설득력이 훨씬 높다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Comparison of model performance using Elo ratings and win rates. Elo ratings represent overall persuasiveness, and win rates reflect relative persuasiveness. Both metrics are based on evaluations by human subjects.
> </details>



![](https://arxiv.org/html/2502.16810/x7.png)

> 🔼 그림 4a는 AI 피드백의 효과를 보여줍니다.  Shot-wise Simulation Accuracy(SSA)는 각 샷에 대한 예측 정확도의 사용자 평균을 나타냅니다. 이 그래프는 AI가 인간의 피드백을 시뮬레이션하는 데 있어서 정확도가 샷 수에 따라 어떻게 변하는지 보여줍니다.  정확도는 샷의 수가 증가함에 따라 증가하지만, 안정적인 수준에는 도달하지 않습니다.  이 결과는 사용자 선호도를 동적으로 예측하는 어려움을 강조합니다.
> <details>
> <summary>read the caption</summary>
> (a) Shot-wise Accuracy
> </details>



![](https://arxiv.org/html/2502.16810/extracted/6227460/figures/survey_interface/comparison.jpg)

> 🔼 그림 4b는 AI 피드백의 효과를 평가하기 위해 사용된 사용자별 시뮬레이션 정확도(USA)를 보여줍니다. USA는 각 사용자에 대한 예측 정확도를 나타내며, 모든 시도에 걸쳐 평균을 낸 값입니다. 이 그래프는 AI가 인간의 피드백을 얼마나 잘 시뮬레이션할 수 있는지, 그리고 그 정확도가 사용자마다 얼마나 다를 수 있는지 보여줍니다.  높은 분산은 AI가 개별 사용자의 선호도를 동적으로 예측하는 데 어려움을 겪고 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (b) User-wise Accuracy
> </details>



![](https://arxiv.org/html/2502.16810/extracted/6227460/figures/annotation_interface.png)

> 🔼 그림 4(c)는 AI 피드백을 사용한 인간 피드백 시뮬레이션의 오류 원인을 분석한 결과입니다.  AI가 인간의 반응을 얼마나 정확하게 시뮬레이션하는지 평가하기 위해 오류들을 분석했고,  설명 가능한 패턴이 없는 56.1%의 오류를 제외하고 나머지 오류들을 네 가지 주요 원인으로 분류했습니다. 각 원인은 막대 그래프로 표현되어 있습니다.  세부적으로는 길이 편향, 동점 의견, 출현 선호도, 늦은 예측, 모델 혼동 등의 원인이 포함됩니다. 이는 AI 피드백 시뮬레이션의 한계점을 보여주는 시각 자료입니다.
> <details>
> <summary>read the caption</summary>
> (c) Error Case Attribution
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