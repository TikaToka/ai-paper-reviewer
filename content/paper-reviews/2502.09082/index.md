---
title: "CoSER: Coordinating LLM-Based Persona Simulation of Established Roles"
summary: "COSER는 771권의 유명 도서에서 추출한 17,966명의 캐릭터를 포함한 고품질 데이터셋과, 최첨단 오픈소스 역할극 언어 에이전트(RPLA) 모델, 그리고 효과적인 RPLA 평가 프로토콜을 제시합니다.  **주요 기여는 고품질 데이터셋과 주어진 상황 연기(GCA)라는 새로운 평가 방법론**입니다. GCA를 통해 다중 에이전트 시뮬레이션과 패널티 기반 L..."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Fudan University",]
showSummary: true
date: 2025-02-13
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.09082 {{< /keyword >}}
{{< keyword icon="writer" >}} Xintao Wang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-14 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.09082" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.09082" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/coser-coordinating-llm-based-persona" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 역할극 언어 에이전트(RPLA) 연구는 **데이터 부족과 평가 방법론의 미흡**이라는 문제점을 가지고 있었습니다. 특히, **확립된 캐릭터의 복잡한 배경과 섬세한 성격**을 충실하게 반영하는 것은 큰 과제였습니다.  기존 데이터셋들은 대부분 대화 데이터 위주였으며, 품질과 다양성 측면에서 부족했습니다. 평가 또한 단순한 턴 기반 상호작용 위주로 세련되지 못했습니다.

본 연구에서는 이러한 문제점들을 해결하기 위해 **771권의 유명 도서에서 추출한 방대한 양의 고품질 데이터셋 COSER**를 구축했습니다. COSER는 **대화 내용 뿐만 아니라 플롯 요약, 캐릭터의 경험, 내면의 생각 등 다양한 정보**를 포함하고 있습니다. 또한, 연극 연출 기법에서 영감을 얻은 **새로운 평가 방법론인 주어진 상황 연기(GCA)**를 제안, 다중 에이전트 시뮬레이션 및 패널티 기반 LLM 평가를 통해 RPLA 모델의 성능을 종합적으로 평가합니다. 이를 통해 기존 RPLA 모델들을 능가하는 **최첨단 성능의 CoSER 8B와 CoSER 70B 모델**을 개발하고, 다양한 벤치마크에서 우수한 성능을 검증했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 771권의 유명 도서에서 추출한 17,966명의 캐릭터 데이터를 포함하는 고품질 COSER 데이터셋을 공개 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 기존 RPLA 평가의 한계를 극복하는 새로운 평가 프로토콜인 주어진 상황 연기(GCA) 제안 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} COSER 데이터셋과 GCA를 이용하여 훈련된 최첨단 오픈소스 RPLA 모델인 CoSER 8B와 CoSER 70B를 공개 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **고품질의 캐릭터 데이터셋과 첨단 모델, 그리고 평가 프로토콜을 제시**함으로써, 확립된 캐릭터의 역할극 언어 에이전트(RPLA) 연구에 상당한 영향을 미칩니다.  **기존의 한계점을 극복**하고, **새로운 연구 방향을 제시**하여 RPLA 분야의 발전에 크게 기여할 것으로 예상됩니다. 특히, **다양한 데이터 유형을 통합**하고, **정교한 평가 방법론**을 제안하여 더욱 정확하고 심도있는 연구가 가능해졌습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.09082/x1.png)

> 🔼 그림 1은 COSER 데이터셋의 한 예시를 보여줍니다. COSER 데이터셋은 대화 내용과 배경 설정, 줄거리 요약, 등장인물의 내면 심리 등 다양한 유형의 데이터를 제공합니다. 이러한 데이터는 모두 유명한 책에서 실제로 발췌한 것으로, 높은 신뢰도를 자랑합니다. 그림에서는 해리포터와 마법사의 돌의 한 장면을 예시로 들어, 대화 내용, 배경 설정, 줄거리 요약, 등장인물의 심리 상태 등을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  An example from CoSER dataset, which provides comprehensive data types such as conversation dialogues and settings, plot summaries, characters’ inner thoughts, authentically sourced from renowned books.
> </details>





{{< table-caption >}}
| Dataset | Book Num. | Character Num. | Profile | Expr. | #Conv. | Conversation #Turns | Setting | Auth. | Multi-Chara. | Message Speech | Thought | Action | Plot Summ. |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Charater-LLM |  | 9 | ✓ |  | 14,300 | 13.2 | ✓ |  |  | ✓ |  |  |  |
| ChatHaruhi |  | 32 | ✓ |  | 54,726 | >2 |  | ✓* | ✓ | ✓ |  |  |  |
| RoleLLM |  | 100 | ✓ |  | 140,726 | 2 |  |  |  | ✓ |  |  |  |
| HPD | 7 | 113 |  |  | 1,191 | 13.2 | ✓ | ✓ | ✓ | ✓ |  |  | ✓ |
| LifeChoice | 388 | 1,462 | ✓ |  | 1,462 | 2 | ✓ | ✓ |  |  |  |  |  |
| CroSS-MR | 126 | 126 | ✓ |  | 445 | 2 | ✓ | ✓ |  |  |  |  |  |
| CharacterGLM |  | 250 | ✓ |  | 1,034 | 15.8 | ✓ |  |  | ✓ |  |  |  |
| CharacterEval |  | 77 | ✓ |  | 1,785 | 9.3 | ✓ | ✓ |  | ✓ |  | ✓ |  |
| DITTO |  | 4,002 | ✓ |  | 7,186 | 5.1 |  |  |  | ✓ |  |  |  |
| MMRole |  | 85 | ✓ |  | 14,346 | 4.2 |  |  |  | ✓ |  |  |  |
| CharacterBench |  | 3,956 | ✓ |  | 13,162 | 11.3 |  |  |  | ✓ |  |  |  |
| CoSER | 771 | 17,966 | ✓ | ✓ | 29,798 | 13.2 | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |{{< /table-caption >}}

> 🔼 표 1은 COSER 데이터셋과 기존 RPLA 데이터셋을 비교 분석한 표입니다. 등장인물 수, 프로필 유무, 구조화된 경험 유무, 대화 수, 턴 수, 배경 설정, 대화의 출처, 다중 인물 참여 여부, 말, 생각, 행동, 줄거리 요약 등 다양한 측면에서 데이터셋을 비교 분석하여 COSER 데이터셋의 특징과 우수성을 보여줍니다.  약어로 사용된 Num.(number), Conv.(conversation), Summ.(summary)는 각각 등장인물 수, 대화 수, 줄거리 요약을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Overview of CoSER and existing RPLA datasets. For characters, Num. count characters with profiles, and Expr. denotes structured character experiences. For conversations, Auth. indicates authentic dialogues or behaviors from the books, and Multi-Chara. denotes involving more than 2 characters. Num. (number), Conv. (conversation), and Summ. (summary) are abbreviations.
> </details>





### In-depth insights


#### RPLA Datasets
본 논문에서 다루는 RPLA(Role-Playing Language Agent) 데이터셋은 **품질과 다양성 측면에서 기존 연구들과 차별화**됩니다. 기존 데이터셋들은 대부분 2인 대화에 국한되거나, LLM(Large Language Model)을 이용한 합성 데이터로 **자연스러움과 현실성이 부족**한 반면, 본 연구의 데이터셋은 **다양한 유형의 데이터(대화, 줄거리, 캐릭터 배경 등)**를 풍부하게 포함하여 **RPLA의 훈련 및 평가에 유용한 정보**를 제공합니다. 특히 **실제 소설에서 발췌한 다양한 캐릭터와 대화**를 활용함으로써, **높은 신뢰도와 현실성을 확보**하는 데 성공하였습니다. 또한, 데이터셋의 규모 또한 상당하여, **다양한 캐릭터와 상황에 대한 충분한 학습 데이터**를 제공합니다. 이러한 특징들은 **RPLA의 성능 향상과 실제 응용 가능성 확대**에 크게 기여할 것으로 예상됩니다.  하지만, **데이터 수집 과정의 어려움과 저작권 문제**는 향후 연구에서 고려해야 할 중요한 사항입니다.

#### GCA Evaluation
본 논문에서 제시된 GCA 평가 방식은 역할 수행 LLM의 성능을 평가하는 새로운 접근 방식을 제시합니다. 기존의 단순 평가 방식과 달리, **다중 에이전트 시뮬레이션**과 **패널티 기반 LLM 판정**이라는 두 단계를 통해 보다 정교하고 포괄적인 평가를 수행합니다.  **다중 에이전트 시뮬레이션**은 실제 대화와 유사한 환경을 조성하고, **페널티 기반 LLM 판정**은 상세한 평가 기준을 통해 주관성을 최소화하여 보다 객관적인 평가를 가능하게 합니다.  이러한 접근 방식은 단순히 턴 기반의 짧은 대화가 아닌, 다중 캐릭터가 참여하는 복잡한 상호작용을 효과적으로 평가할 수 있음을 보여줍니다.  **실제 대화 데이터를 기반으로 한 평가**는 모델의 현실성과 정확성을 높이는 데 중요한 역할을 합니다.  특히, **문맥에 따른 지속적인 평가**는 모델의 장기적인 역할 수행 능력을 평가하는 데 효과적입니다.  **다양한 평가 지표를 활용**하여 종합적인 평가 결과를 제시하는 것도 GCA 평가의 장점입니다.  하지만, **LLM 판정의 주관성을 완전히 배제하기 어렵다는 점**과 **계산 비용이 높다는 점**은 한계로 지적될 수 있습니다.

#### CoSER Model
본 논문에서 제시된 CoSER 모델은 **기존의 역할극 언어 에이전트(RPLA)의 한계를 극복하기 위해 고안된 대규모 언어 모델(LLM)**입니다. 기존 RPLA 모델들은 품질이 낮은 데이터와 정교하지 못한 평가 방법으로 인해 실제 역할극과 같은 자연스러운 상호작용을 생성하는 데 어려움을 겪었습니다.  하지만 CoSER 모델은 **대규모의 고품질 데이터셋인 CoSER 데이터셋을 활용하여 훈련**되었으며, **새로운 평가 프로토콜인 Given-Circumstance Acting(GCA)**을 통해 더욱 정교하게 평가됩니다.  GCA는 다중 에이전트 시뮬레이션과 페널티 기반 LLM 판정 방식을 결합하여, LLM이 다양한 캐릭터의 역할을 수행하는 능력을 측정합니다. **CoSER 70B 모델은 여러 기준에서 최첨단 성능을 보이며, 특히 InCharacter와 LifeChoice 벤치마크에서 뛰어난 정확도를 달성**합니다.  이는 CoSER 모델이 **데이터셋, 모델 아키텍처, 평가 방식의 세 가지 측면에서 개선**을 이루었음을 시사합니다. 따라서 CoSER 모델은 **RPLA 연구 및 응용 분야에 중요한 발전**을 가져올 것으로 기대됩니다. 특히, 고품질 데이터와 정교한 평가 기법을 통해, 보다 사실적이고 세련된 역할극 언어 에이전트 개발에 기여할 것으로 예상됩니다.

#### Ablation Studies
본 논문의 "절제 연구(Ablation Studies)" 부분은 모델 성능에 대한 요인 분석을 심도 있게 다룹니다. **특히, 내면의 생각(inner thoughts)과 동기(motivations)의 영향을 중점적으로 분석**하여, 이러한 요소들이 모델의 역할극 수행 능력에 미치는 영향을 정량적으로 평가합니다.  **내면의 생각과 동기를 제거했을 때 모델 성능이 전반적으로 저하**되는 것을 보여줌으로써, 이러한 요소들이 **인간다운 상호작용과 사실적인 캐릭터 묘사에 필수적임**을 시사합니다.  이러한 분석은 단순한 성능 비교를 넘어, **역할극 언어 에이전트(RPLA)의 본질적인 요소를 밝히고 모델 개선 방향을 제시**하는 데 기여합니다.  **데이터 구성 및 모델 학습 과정에서 이러한 요소들을 고려**하는 것이 RPLA 개발에 있어 중요한 함의를 지닌다는 것을 보여주는 중요한 부분입니다.  절제 연구를 통해 도출된 결과는 향후 RPLA 모델 개발 및 성능 향상을 위한 중요한 지침을 제공할 것으로 예상됩니다.

#### Future Work
본 논문은 인물 역할극 언어 에이전트(RPLA)에 대한 심도있는 연구를 제시하며, 특히 기존 역할의 인물 시뮬레이션에 초점을 맞추고 있습니다.  **미래 연구 방향**으로는 몇 가지 중요한 측면을 고려해 볼 수 있습니다. 첫째, **데이터셋의 확장**입니다. 현재 데이터셋은 방대한 양의 데이터를 포함하지만, 다양한 장르와 문화적 배경을 가진 인물들을 더욱 포괄적으로 다루기 위한 추가적인 노력이 필요합니다.  둘째, **평가 기준의 개선**입니다.  현재 사용되는 평가 방식은 주관적일 수 있으므로, 더욱 객관적이고 정량적인 평가 기준을 개발해야 합니다. 셋째, **다양한 LLM 모델의 적용**입니다.  본 논문에서는 특정 LLM 모델을 사용했지만, 다른 모델들을 사용하여 성능 비교 및 분석을 수행해야 더욱 폭넓은 결과를 얻을 수 있습니다. 마지막으로, **실제 응용 분야**에 대한 연구가 필요합니다.  **개발된 모델과 데이터셋을 게임, 교육, 엔터테인먼트 등 다양한 분야에 적용하여 실제 효용성을 검증**하고,  **사용자 피드백**을 바탕으로 모델을 지속적으로 개선해 나가야 합니다. 이를 통해 RPLA 기술의 발전을 가속화하고, 더욱 현실적이고 매력적인 인물 시뮬레이션을 구현할 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.09082/x2.png)

> 🔼 그림 2는 COSER 데이터셋, 학습 및 평가의 개요를 보여줍니다. 왼쪽은 COSER 데이터셋이 저명한 책에서 가져온 데이터를 LLM 기반 파이프라인을 통해 처리한 과정을 보여줍니다. 플롯, 대화, 캐릭터에 대한 풍부한 데이터 유형을 포함합니다. 오른쪽은 이러한 대화를 사용하여 역할 수행 LLM을 훈련하고 평가하기 위해 주어진 상황 연기(GCA)를 적용하는 방법을 보여줍니다. 훈련의 경우 각 샘플은 LLM이 대화에서 특정 캐릭터를 묘사하도록 훈련하며 원본 대화를 사용합니다. 평가의 경우 동일한 시나리오가 주어진 대화 시뮬레이션을 위한 다중 에이전트 시스템을 구축하고 패널티 기반 LLM 평론가를 통해 시뮬레이션된 대화를 평가합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2:  Overview of CoSER’s dataset, training and evaluation. Left: The CoSER dataset is sourced from renowned books and processed via LLM-based pipeline. It contains rich data types on plots, conversations and characters. Right: We apply given-circumstance acting to train and evaluate role-playing LLMs using these conversations. For training, each sample trains the LLM to portray a specific character in a conversation, using their original dialogue. For evaluation, we build a multi-agent system for conversation simulation given the same scenario, and assess the simulated dialogue via penalty-based LLM critics.
> </details>



![](https://arxiv.org/html/2502.09082/extracted/6197931/Figures/rag_comparison.jpg)

> 🔼 그림 3은 다양한 캐릭터 데이터에서 검색 증강을 사용한 CoSER 테스트에 대한 LLM 성능을 보여줍니다.  Expr.은 경험을, Conv.는 대화를 나타냅니다.  이 그래프는 다양한 유형의 캐릭터 데이터(경험 및 대화)를 검색하여 추가한 경우의 LLM 성능 변화를 보여줍니다.  각 막대는 특정 데이터 유형을 추가했을 때의 평균 점수를 나타냅니다.  기준선(Base)은 검색 증강 없이 CoSER 테스트의 LLM 성능입니다.  이 그림은 CoSER 데이터셋의 포괄적인 데이터 유형이 검색 증강에 어떻게 도움이 되는지 보여주는 것을 목적으로 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: LLM Performance on CoSER Test with retrieval augmentation from various character data. Expr. and Conv. denote experiences and conversations respectively.
> </details>



![](https://arxiv.org/html/2502.09082/x3.png)

> 🔼 그림 4는 COSER 데이터셋에 포함된 도서의 장르 분포를 보여줍니다.  단순히 장르의 비율만 나타내는 것이 아니라, 판타지, 역사, 공상과학, 로맨스, 미스터리 등 주요 소설 장르뿐만 아니라 회고록, 전기 등 틈새 장르까지 포함하여 데이터셋의 다양성을 강조하고 있습니다.  각 장르가 차트에서 비율로 표현되어 데이터셋의 균형 잡힌 구성을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Genre distribution of selected books in CoSER dataset.
> </details>



![](https://arxiv.org/html/2502.09082/extracted/6197931/Figures/rounds_vs_scores_scatter.png)

> 🔼 그림 5는 GCA 평가에서 패널티 기반 LLM 평론가의 길이 편향을 보여주는 선형 회귀 결과를 보여줍니다.  선형 회귀 분석을 통해 시뮬레이션 라운드 수가 증가함에 따라 점수가 감소하는 경향(길이 편향)이 있음을 확인하고, 이를 보정하기 위한 길이 보정 방법을 제시합니다.  이 그래프는 다양한 모델과 설정에서 시뮬레이션 라운드 수와 점수 간의 관계를 시각적으로 나타내어 길이 편향의 존재와 그 영향을 명확히 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5:  Linear regression results showing length bias of penalty-based LLM critics in GCA evaluation.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
Model|Storyline|Consistency|Anthropomorphism|Character Fidelity|Storyline Quality|Average Score|BLEU|ROUGE-L
---|---|---|---|---|---|---|---|---
**_Close-source Models_**
Abab7-preview|56.81 ± 1.47|44.23 ± 1.90|43.83 ± 2.71|74.83 ± 0.97|54.92 ± 0.57|4.96 ± 0.07|11.50 ± 0.06|
Doubao-pro|60.95 ± 1.40|49.72 ± 0.23|47.02 ± 1.10|79.28 ± 0.82|59.24 ± 0.30|6.38 ± 0.08|12.95 ± 0.04|
Step-1-Flash|57.75 ± 0.72|48.12 ± 0.39|44.48 ± 0.48|75.93 ± 0.99|56.57 ± 0.48|5.95 ± 0.15|12.71 ± 0.11|
Step-2|61.43 ± 0.88|49.06 ± 1.69|47.33 ± 0.70|77.96 ± 0.85|58.94 ± 0.75|5.75 ± 0.08|12.50 ± 0.11|
GPT-3.5|57.22 ± 0.13|43.30 ± 0.48|42.29 ± 1.47|73.91 ± 0.64|54.18 ± 0.63|4.58 ± 0.11|11.80 ± 0.10|
GPT-4o|**61.59 ± 0.66**|48.93 ± 0.48|**48.95 ± 1.73**|**80.33 ± 0.59**|**59.95 ± 0.50**|5.90 ± 0.16|12.11 ± 0.13|
GPT-4o Mini|60.09 ± 0.60|48.21 ± 1.09|44.88 ± 1.63|78.55 ± 0.14|57.93 ± 0.74|3.90 ± 0.07|10.81 ± 0.07|
Gemini Pro|59.11 ± 0.82|52.41 ± 0.57|47.83 ± 0.37|77.59 ± 1.43|59.24 ± 0.25|5.39 ± 0.04|11.65 ± 0.06|
Claude-3-Haiku|58.18 ± 0.72|44.66 ± 1.72|41.88 ± 0.34|74.14 ± 1.26|54.71 ± 0.84|4.80 ± 0.05|12.02 ± 0.02|
Claude-3.5-Sonnet|57.45 ± 0.98|48.50 ± 2.35|45.69 ± 1.80|77.23 ± 0.88|57.22 ± 0.95|5.17 ± 0.12|11.45 ± 0.07|
**_Open-source Models_**
Mistral-7B|**59.90 ± 1.33**|40.00 ± 0.74|44.75 ± 1.14|61.93 ± 1.12|51.64 ± 0.55|2.71 ± 0.10|9.28 ± 0.12|
Qwen-2-7B|51.96 ± 0.67|35.48 ± 0.62|31.51 ± 2.95|63.18 ± 0.79|45.53 ± 0.69|4.21 ± 0.21|10.71 ± 0.10|
LLaMA-3.1-8B|54.10 ± 1.63|45.36 ± 1.91|40.22 ± 1.16|72.29 ± 1.75|52.99 ± 1.20|4.59 ± 0.11|10.18 ± 0.09|
CoSER-8B|58.61 ± 2.46|47.23 ± 0.16|46.90 ± 2.06|73.04 ± 1.37|56.45 ± 0.56|9.40 ± 0.18|14.21 ± 0.11|
Vicuna-13B-1.5|52.75 ± 1.64|39.12 ± 1.21|38.04 ± 0.98|60.43 ± 1.58|47.58 ± 1.25|1.67 ± 0.10|5.59 ± 0.18|
Mixtral-8x7B|51.25 ± 1.73|38.44 ± 1.18|36.92 ± 2.65|67.69 ± 0.80|48.58 ± 1.35|5.28 ± 0.06|11.66 ± 0.05|
Qwen-2-72B|57.75 ± 1.26|47.28 ± 0.87|46.62 ± 1.69|76.60 ± 0.36|57.06 ± 1.00|5.38 ± 0.00|11.85 ± 0.03|
LLaMA-3.1-70B|57.46 ± 1.65|45.95 ± 1.30|43.72 ± 1.17|74.84 ± 0.54|55.49 ± 0.33|4.82 ± 0.06|10.98 ± 0.06|
CoSER-70B|58.66 ± 1.34|**53.33 ± 0.91**|**48.75 ± 1.43**|75.49 ± 0.94|**59.06 ± 0.22**|**10.10 ± 0.04**|**14.78 ± 0.09**|
DeepSeek-V3|56.40 ± 0.95|47.87 ± 1.10|44.02 ± 0.13|76.66 ± 1.26|56.24 ± 0.46|4.54 ± 0.14|11.02 ± 0.15|{{< /table-caption >}}
> 🔼 표 2는 CoSER Test 데이터셋을 사용하여 주어진 상황 연기 과제에서 다양한 대규모 언어 모델(LLM)의 성능을 백분율(%)로 나타낸 표입니다. 표에는 각 모델의 일관성, 의인화, 충실도, 품질 점수와 BLEU 및 ROUGE-L 점수가 포함되어 있습니다. 굵게 표시된 값은 모든 모델 중 가장 좋은 성능을 나타내고, 밑줄 친 값은 오픈소스 모델 중 가장 좋은 성능을 나타냅니다. 이 표는 주어진 상황에서 다양한 LLM이 역할극을 얼마나 잘 수행하는지 비교 분석하는 데 유용합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Performance (%) of various LLMs on given-circumstance acting using CoSER Test. Bold or underlined values indicate best performance across all models and open-source models, respectively.
> </details>

{{< table-caption >}}
| Model | Incharacter |  |  |  | 
|---|---|---|---|---| 
|  | Dim | Full | Life | Choice | CroSS | MR |
|---|---|---|---|---|---|---|
| LLaMA-3.1-8B | 64.97 | 15.62 | 61.10 | 30.15 |
| CoSER-8B | 75.80 | 21.88 | 69.54 | 44.94 |
| *trained w/o I.T.* | 70.70 | 15.62 | 59.92 | 43.14 |
| LLaMA-3.1-70B | 72.16 | 31.25 | 86.48 | 61.30 |
| Higgs-Llama-3-70B | 74.52 | 28.12 | 74.03 | 60.12 |
| CoSER-70B | 75.80 | **34.38** | **93.47** | **64.49** |
| *trained w/o I.T.* | 73.12 | 32.14 | 93.18 | 63.14 |
| Qwen-2-72B | 74.52 | 31.25 | 81.14 | 62.57 |
| GPT-3.5 | 71.20 | 21.88 | 78.07 | 30.09 |
| GPT-4o | **76.54** | 32.62 | 75.96 | **64.49** |
| Claude-3.5-Sonnet | 72.61 | 21.88 | 86.07 | 30.59 |{{< /table-caption >}}
> 🔼 표 3은 기존의 세 가지 역할극 언어 에이전트(RPLA) 벤치마크에 대한 다양한 대규모 언어 모델(LLM)의 성능을 백분율(%)로 나타낸 표입니다.  InCharacter 벤치마크의 경우 개별(Dim) 및 전체(Full) 차원에 대한 정확도를 BFI(Big Five Inventory) 기준으로 보고합니다. I.T.는 내적 사고(inner thoughts)를 의미합니다. 이 표는 각 모델이 얼마나 효과적으로 확립된 캐릭터를 시뮬레이션하고, 다양한 대화 상황에서 일관성을 유지하며,  인간다운 반응을 보이는지를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: LLM performance (%) across three existing RPLA benchmarks. I.T. denotes inner thoughts. For InCharacter, we report accuracy for individual (Dim) and full (Full) dimensions on BFI.
> </details>

{{< table-caption >}}
| Model | Standard | Test w/o I.T. | Test w/o Mot. |
|---|---|---|---|
| GPT-4o | 59.95 | 56.89 | 56.34 |
| Qwen-2-72B | 57.06 | 51.95 | 54.21 |
| LLaMA-3.1-70B | 55.49 | 53.12 | 52.49 |
| CoSER-70B | 59.06 | 57.32 | 57.71 |
| *trained w/o I.T.* | 56.04 | 55.34 | - |
| LLaMA-3.1-8B | 52.99 | 51.97 | 49.63 |
| CoSER-8B | 56.45 | 54.65 | 56.81 |
| *trained w/o I.T.* | 54.25 | 54.38 | - |{{< /table-caption >}}
> 🔼 표 4는 CoSER 테스트에서 평균 점수를 보여주는 절제 연구 결과를 보여줍니다.  CoSER 테스트는 논문에서 제시된 새로운 역할극 언어 에이전트(RPLA) 평가 프로토콜을 사용하여 수행된 평가입니다.  표는 내적 사고(I.T.)와 동기(Mot.)를 포함하거나 제외한 다양한 모델의 성능을 비교하여 각 요소가 역할극 언어 모델의 성능에 미치는 영향을 분석합니다.  즉, 내적 사고와 동기가 모델의 역할극 수행 능력에 얼마나 기여하는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 4:  Ablation study results (average scores) on CoSER Test. I.T. and Mot. mean inner thoughts and motivations, respectively.
> </details>

{{< table-caption >}}
| #Book | #Plot | #Conversation. | #Chararacter | #Utterance |
|---|---|---|---|---|
| 771 | 30,069 | 29,798 | 17,966 | 392,900 |{{< /table-caption >}}
> 🔼 표 5는 COSER 데이터셋의 통계를 보여줍니다.  데이터셋의 규모와 다양성을 보다 자세히 설명하면, 771권의 저명한 책에서 추출한 17,966명의 등장인물, 30,069개의 고유 플롯, 그리고 29,798개의 대화를 포함하고 있으며, 전체 데이터셋은 약 392,900개의 발화로 구성됩니다. 평균적으로 각 대화는 약 13.2개의 발화를 포함합니다. 이 표는 COSER 데이터셋의 방대함과 다양성을 한눈에 보여주는 요약 통계 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Statistics of CoSER Dataset.
> </details>

{{< table-caption >}}
| Selected Books |
|---|---| 
| 1. _The Hunger Games (The Hunger Games, #1)_ | 2. _Harry Potter and the Order of the Phoenix (H. P., #5)_ |
| 3. _Pride and Prejudice_ | 4. _To Kill a Mockingbird_ |
| 5. _The Book Thief_ | 6. _Animal Farm_ |
| 7. _The Chronicles of Narnia (#1-7)_ | 8. _The Fault in Our Stars_ |
| 9. _The Picture of Dorian Gray_ | 10. _Wuthering Heights_ |
| 11. _Gone with the Wind_ | 12. _The Perks of Being a Wallflower_ |
| 13. _The Lightning Thief (Percy Jackson and the Olympians, #1)_ | 14. _The Little Prince_ |
| 15. _The Great Gatsby_ | 16. _Crime and Punishment_ |
| 17. _Memoirs of a Geisha_ | 18. _Les Misérables_ |
| 19. _The Alchemist_ | 20. _Lord of the Flies_ |
| 21. _The Hitchhiker’s Guide to the Galaxy (#1)_ | 22. _The Help_ |
| 23. _Dracula_ | 24. _Ender’s Game (Ender’s Saga, #1)_ |
| 25. _Of Mice and Men_ | 26. _One Hundred Years of Solitude_ |
| 27. _Brave New World_ | 28. _A Thousand Splendid Suns_ |
| 29. _The Time Traveler’s Wife_ | 30. _The Princess Bride_ |
| 31. _The Secret Garden_ | 32. _The Outsiders_ |
| 33. _A Game of Thrones (A Song of Ice and Fire, #1)_ | 34. _Little Women_ |
| 35. _A Wrinkle in Time (Time Quintet, #1)_ | 36. _The Odyssey_ |
| 37. _Harry Potter and the Deathly Hallows (H. P., #7)_ | 38. _Frankenstein: The 1818 Text_ |
| 39. _The Kite Runner_ | 40. _The Handmaid’s Tale (The Handmaid’s Tale, #1)_ |
| 41. _The Lovely Bones_ | 42. _The Adventures of Huckleberry Finn_ |
| 43. _Life of Pi_ | 44. _A Tale of Two Cities_ |
| 45. _Dune (Dune, #1)_ | 46. _Harry Potter and the Prisoner of Azkaban (H.P.,#3)_ |
| 47. _Water for Elephants_ | 48. _Harry Potter and the Sorcerer’s Stone (H. P., #1)_ |
| 49. _The Bell Jar_ | 50. _Matilda_ |
| 51. _The Stand_ | 52. _Catch-22_ |
| 53. _The Adventures of Sherlock Holmes (S. H., #3)_ | 54. _The Pillars of the Earth (Kingsbridge, #1)_ |
| 55. _Rebecca_ | 56. _Great Expectations_ |
| 57. _The Girl with the Dragon Tattoo (Millennium, #1)_ | 58. _The Color Purple_ |
| 59. _Anna Karenina_ | 60. _My Sister’s Keeper_ |
| 61. _The Brothers Karamazov_ | 62. _A Clockwork Orange_ |
| 63. _And Then There Were None_ | 64. _The Road_ |
| 65. _To Kill a Mockingbird_ | 66. _The Golden Compass (His Dark Materials, #1)_ |
| 67. _Vampire Academy (Vampire Academy, #1)_ | 68. _Siddhartha_ |
| 69. _The Complete Stories and Poems_ | 70. _Interview with the Vampire (The Vampire Chronicles, #1)_ |
| 71. _Don Quixote_ | 72. _The Old Man and the Sea_ |
| 73. _The Poisonwood Bible_ | 74. _Harry Potter and the Goblet of Fire (H. P., #4)_ |
| 75. _Atlas Shrugged_ | 76. _The Notebook (The Notebook, #1)_ |
| 77. _Harry Potter and the Half-Blood Prince (H. P., #6)_ | 78. _Moby-Dick or, The Whale_ |
| 79. _A Prayer for Owen Meany_ | 80. _Clockwork Angel (The Infernal Devices, #1)_ |
| 81. _The Stranger_ | 82. _The Secret Life of Bees_ |
| 83. _Harry Potter and the Chamber of Secrets (H. P., #2)_ | 84. _The Red Tent_ |
| 85. _The Name of the Wind (The Kingkiller Chronicle, #1)_ | 86. _The Master and Margarita_ |
| 87. _The Metamorphosis_ | 88. _Eragon (The Inheritance Cycle, #1)_ |
| 89. _The Count of Monte Cristo_ | 90. _Looking for Alaska_ |
| 91. _The Adventures of Tom Sawyer_ | 92. _Charlie and the Chocolate Factory (Charlie Bucket, #1)_ |
| 93. _The Last Olympian (Percy Jackson and the Olympians, #5)_ | 94. _The Curious Incident of the Dog in the Night-Time_ |
| 95. _The Shadow of the Wind (Cemetery of Forgotten Books, #1)_ | 96. _The Unbearable Lightness of Being_ |
| 97. _On the Road_ | 98. _The Name of the Rose_ |
| 99. _A Story of Yesterday_ | 100. _The Godfather (The Godfather, #1)_ |{{< /table-caption >}}
> 🔼 본 표는 Goodreads의 '역대 최고의 책' 목록에서 선정된 상위 100권의 책 목록을 보여줍니다.  각 책 제목과 Goodreads에서의 순위가 함께 표시되어 있으며, 소설, 판타지, 역사, 추리소설 등 다양한 장르의 책들이 포함되어 있습니다. 이 표는 COSER 데이터셋에 사용된 책들의 출처와 다양성을 보여주는 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: The top 100 selected books from Goodreads’ Best Books Ever list.
> </details>

{{< table-caption >}}
| Simulation Case (from *A Storm of Swords (A Song of Ice and Fire, #3)*)
| Plot Summary | Sansa is confronted by her jealous aunt Lysa, who accuses her of kissing Petyr Baelish. Lysa threatens to push Sansa through the Moon Door, but Petyr intervenes. He calms Lysa down, only to push her through the Moon Door himself, killing her. |
| Scenario | In the High Hall of the Eyrie, Lysa Arryn confronts Sansa about kissing Petyr Baelish, becoming increasingly unstable and dangerous … |
| Characters | Sansa Stark
**Motivation**: I’m terrified. Aunt Lysa has gone mad. I need to find a way out of this situation before she hurts me.
**Profile**: Sansa Stark, a young noblewoman from the North, finds herself at the center of political intrigue and personal tragedy in "A Storm of Swords." Born to the noble House Stark, Sansa begins the story as a ward of the crown in King’s Landing, her initial romantic notions of court life long since shattered. Forced into an unwanted marriage with Tyrion Lannister, Sansa endures the ceremony and subsequent feast with a mix of reluctance, sadness, and carefully hidden disgust …

Lysa Arryn
**Motivation**: I must protect what’s mine. Petyr is mine, and this girl is trying to take him away from me. I’ll show her what happens to those who cross me.
**Profile**: Lysa Arryn, née Tully, is a complex and volatile character in George R.R. Martin’s "A Storm of Swords." As the widow of Jon Arryn, the former Hand of the King, and Lady of the Eyrie, Lysa plays a significant role in the political landscape of Westeros. She is the sister of Catelyn Stark and aunt to Sansa Stark, though her actions are often driven by her own desires rather than familial loyalty. |
| Simulation of  CoSER 70B | Lysa Arryn: [My rage is building. I must confront this little slut.] You kissed him. (Her voice is shrill with accusation)

Sansa Stark: [I’m terrified, but I must remain calm and find a way out of this.] (She shakes her head in disbelief) [I can’t believe this is happening. I need to explain myself carefully.] One kiss, aunt. A harmless kiss on the cheek, that’s all.

Lysa Arryn: [She’s lying! I won’t let her manipulate me.] (She spots the wind-up knight) Was this how you kissed him? (She sets the knight moving, her eyes wild) You’re a woman grown, aren’t you? (Her voice rises to a shriek) Grown enough to be wed, wed enough to be bedded!

Sansa Stark: [The pain is excruciating, but I can’t show weakness now.] (She struggles to keep her face neutral despite the pain) [I need to find a way to calm her down.] Please, Aunt Lysa, I don’t know what you mean. I’m just a guest here. I would never do anything to betray your trust.

Lysa Arryn: [I’ll show her what happens to those who cross me.] (She screams) You’re just like the others. You and your mother, you both drove me to this. I should push you out this door right now.

Sansa Stark: [I’m going to die if I don’t think of something quickly.] (Tears stream down her face, mixing with the wind) [I need to appeal to her maternal side, to make her see me as a child again.] Mother? (Her voice trembles) Please, Aunt Lysa. I never meant to hurt you. I’m your niece, your blood. Please don’t hurt me. I’m just a stupid little girl. I don’t know anything about kissing men. I’ve never even had a kiss in my life. (She forces herself to look into Lysa’s eyes) I’m afraid, Aunt Lysa. Please, don’t push me out the door. I don’t want to fly. |{{< /table-caption >}}
> 🔼 표 7은 '얼음과 불의 노래' 시리즈 중 세 번째 책인 '검의 폭풍'에서 발췌한 대화와, 이를 기반으로 한 다중 에이전트 시뮬레이션의 예시를 보여줍니다.  본 표는 COSER 데이터셋에서 추출한 대화의 일부를 보여주며,  각 등장인물(산사 스타크와 라이사 아린)의 동기, 배경, 대사 등을 상세히 제시하여,  COSER 모델이 실제 소설 속 인물의 성격과 행동을 얼마나 정확하게 반영하는지 보여주는 대표적인 사례입니다.  다중 에이전트 시뮬레이션 결과는 COSER-70B 모델의 출력물이며, 실제 대화와의 차이를 비교 분석함으로써 모델의 성능을 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: An example of an extracted conversation and its multi-agent simulation from A Storm of Swords (A Song of Ice and Fire, #3).
> </details>

{{< table-caption >}}
| Simulation Case (from *A Storm of Swords (A Song of Ice and Fire, #3)*) |
|---|---| 
| **Original Conversation** | Lysa Arryn: [My blood is boiling with jealousy and rage. I’ll make this little harlot pay for trying to seduce my Petyr.] You threw yourself at him. That was the way of it.
Sansa Stark: [I’m trembling with fear, but I must defend myself.] That’s not true.
Lysa Arryn: [She dares to deny it? I’ll show her how serious I am.] Where are you going? Are you afraid? Such wanton behavior must be punished, but I will not be hard on you.
Sansa Stark: [I need to explain what really happened, maybe she’ll listen to reason.] I was building a snow castle. Lord Petyr was helping me, and then he kissed me. That’s what you saw.
Lysa Arryn: [Her words only fuel my anger and paranoia.] Have you no honor? Or do you take me for a fool? You do, don’t you? You take me for a fool. Yes, I see that now.
Sansa Stark: [I’m confused and scared by her accusations about my mother.] My mother?
Lysa Arryn: [The memories of Catelyn’s closeness with Petyr resurface, intensifying my jealousy.] Yes, your mother, your precious mother, my own sweet sister Catelyn. Don’t you think to play the innocent with me, you vile little liar.
Sansa Stark: [I’m horrified by these accusations about my mother.] No. (She wants to shriek) My mother is dead. She was your own sister, and she’s dead. She didn’t. She wouldn’t.
Lysa Arryn: [My rage is reaching its peak. I’ll make her understand the depth of my pain and jealousy.] How would you know? Were you there? (She grabs Sansa and starts pushing her towards the Moon Door)
Sansa Stark: [Panic overwhelms me as I realize the danger I’m in.] Don’t! You’re scaring me!
Environment: The wind howls through the open Moon Door, creating a chilling atmosphere. Snow blows in, adding to the tension and danger of the situation.|{{< /table-caption >}}
> 🔼 표 8은 7장의 'A Storm of Swords'(얼음과 불의 노래 시리즈 중 세 번째 책)에서 발췌한 대화와 COSER 70B 모델의 다중 에이전트 시뮬레이션을 보여줍니다. 이 표는 실제 소설에서 발췌한 대화와 AI 모델이 생성한 대화를 비교하여 모델의 성능을 평가하는 데 사용됩니다. 특히, 샌사 스타크와 라이사 아린의 대화를 통해 캐릭터의 감정, 동기, 그리고 모델의 사실성을 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 8: An example of an extracted conversation and its multi-agent simulation from A Storm of Swords (A Song of Ice and Fire, #3).
> </details>

{{< table-caption >}}
| Simulation Case (from *A Dance with Dragons (A Song of Ice and Fire, #5)*)
| Plot Summary | Cersei undergoes a humiliating walk of atonement through the streets of King’s Landing, enduring physical and emotional torment while trying to maintain her dignity. She faces insults, thrown objects, and her own inner struggle as she makes her way to the Red Keep, focusing on her son Tommen and her eventual salvation.
| Scenario | Cersei continues her walk of atonement through the streets of King’s Landing, facing increasing hostility from the crowd.
| Characters | 
|  | *Cersei Lannister*
|  | Motivation: I must endure this. I am a lioness. They cannot break me.
|  | Profile: The queen dowager, mother of King Tommen, undergoing public humiliation. Cersei is the widow of King Robert Baratheon and the twin sister of Jaime Lannister. Known for her beauty, ambition, and cunning, she has long sought power and control over the Seven Kingdoms. As Queen Regent to her young son Tommen, Cersei’s poor decisions and paranoia have led to a deterioration of the crown’s authority…
|  | *Septa Unella*
|  | Motivation: This sinner must be humbled before the people and the gods.
|  | Profile: (None)
| Original Conversation | Cersei Lannister: [I am beautiful, the most beautiful woman in all Westeros. Jaime says so, Jaime would never lie to me.] (walks on, trying to ignore the jeers)
Crowd Member: Queen Cunt!
Cersei Lannister: [Words are wind. Words cannot hurt me.] (continues walking, her face a mask of indifference)
Septa Unella: (catches Cersei as she slips) Your Grace should watch where she sets her feet.
Cersei Lannister: [I hate you. I hate all of you.] Yes, septa. (struggles to her feet)
Environment: The cobblestones are slippery and uneven. Cersei’s feet are bleeding from cuts and scrapes.
Cersei Lannister: [I asked for sandals. They could have given me sandals.] (limps onward, wincing with each step)
Crowd Member: Brotherfucker!
Cersei Lannister: [Jaime, where are you? You should be here, protecting me.] (scans the crowd desperately)
Septa Scolera: (ringing her bell) Shame, shame, shame upon the sinner, shame, shame.
Cersei Lannister: [I am the queen. I will have all their heads for this.] (stumbles again, barely keeping her feet)
Cersei Lannister: [The Red Keep. I must reach the Red Keep.] (focuses on the distant castle, using it as her beacon of hope){{< /table-caption >}}
> 🔼 표 9는 소설 '얼음과 불의 노래' 5권, '드래곤과의 춤'에서 발췌한 대화 내용과, 다중 에이전트 시뮬레이션 결과를 보여줍니다.  원본 대화와 CoSER 70B, GPT-40, Claude-3.5-Sonnet 모델의 시뮬레이션 결과를 비교하여 각 모델의 성능과 특징을 분석합니다. 특히, 세르세이 라니스터의 감정 표현, 대화 흐름 및 상황 인식 능력을 중점적으로 살펴봅니다.
> <details>
> <summary>read the caption</summary>
> Table 9: An example of an extracted conversation and its multi-agent simulation from A Dance with Dragons (A Song of Ice and Fire, #5).
> </details>

{{< table-caption >}}
| Simulation Case (from *A Dance with Dragons (A Song of Ice and Fire, #5)*) |
|---|---| 
| **Simulation of CoSER 70B** | Cersei Lannister: [I must not show weakness. I am a lioness of Lannister.] (walks slowly, head held high) [The cold is biting, but I will not shiver. I will not give them the satisfaction.]
Environment: The crowd grows larger and more hostile as Cersei continues her walk. Shouts and jeers can be heard from all sides.
Crowd Member: [I’ll show this proud queen what we think of her.] (shouts) Whore! Whore! WHORE!
Cersei Lannister: [I will not let their words affect me. I am above this.] (continues walking, ignoring the shouts) [I must focus on putting one foot in front of the other.]
Environment: A chunk of dung narrowly misses Cersei’s head, splattering on the ground nearby. The crowd roars with laughter.
Cersei Lannister: [I will not falter. I will not show fear.] (stumbles slightly, then regains composure) [I must keep walking. I must endure.]
Septa Scolera: [I must support the queen.] (begins to sing) ’Shame, shame, shame.’
Cersei Lannister: [Their words mean nothing. I am Cersei Lannister, and I will survive this.] (walks faster, almost losing step with the septa’s chanting) [I must not run. I will not give them the satisfaction.]
Septa Scolera: [She’s trying to escape the shame.] (quickens her pace) ’Shame, shame, shame.’
Cersei Lannister: [I can’t keep up this pace. My feet are bleeding, my body is shaking.] (struggles to keep up with Septa Scolera) [I must not falter. I am a Lannister.]
Septa Unella: [The queen must be made to suffer.] (pushes Cersei hard) Keep moving, sinner.
Cersei Lannister: [The pain in my shoulder. The jeers of the crowd. I can’t…] (almost falls, but manages to stay upright) [No, I will not fall. I will survive this.]
Septa Scolera: [We’re almost done.] (continues chanting) ’Shame, shame, shame.’
Cersei Lannister: [I can’t take much more of this. But I must. For House Lannister. For my children.] (forces herself to keep walking) [I will endure. I will rise again.]|{{< /table-caption >}}
> 🔼 표 10은 소설 <왕좌의 게임> 시리즈 다섯 번째 책인 <드래곤과의 춤>에서 발췌한 대화와, 이를 기반으로 다중 에이전트 시뮬레이션을 통해 생성된 대화를 보여줍니다.  본 표는 CoSER 데이터셋에서 추출된 실제 대화와, CoSER 모델을 사용한 다중 에이전트 시뮬레이션 결과를 비교 분석하여 모델의 성능을 평가하는 데 사용됩니다.  특히,  Cersei Lannister와 Septa Unella 두 인물 간의 상호작용에 초점을 맞춰,  각 인물의 동기, 감정, 그리고 행동을 세밀하게 묘사하며 대화의 흐름과 일관성을 보여줍니다. 이는 CoSER 모델이 등장인물의 배경과 성격을 정확하게 반영하여 자연스럽고 일관된 대화를 생성하는 능력을 보여주는 좋은 예시입니다.
> <details>
> <summary>read the caption</summary>
> Table 10: An example of an extracted conversation and its multi-agent simulation from A Dance with Dragons (A Song of Ice and Fire, #5).
> </details>

{{< table-caption >}}
| Simulation Case (from *A Dance with Dragons (A Song of Ice and Fire, #5)*) |
|---|---| 
| **Simulation of GPT-4o** | Cersei Lannister: (As Cersei, I continue the walk with my head held high, despite the jeers and taunts of the crowd.)<br>Septa Unella: "Confess."<br>Cersei Lannister: (I look ahead, ignoring Unella’s words and the hateful stares.) "I am a lioness. You will see me rise again." [I endure this humiliation, aware that my strength will prevail in the end.]<br>Septa Unella: [She must learn humility before she can rise again.]<br>(Septa Unella walks beside Cersei, unmoved by her defiance.)<br>"Confess your sins, Cersei Lannister. Only then will the gods grant you mercy."<br>Cersei Lannister: (I pause briefly, fixing Septa Unella with a steely gaze.)<br>"The gods… and you, know nothing of true strength."<br>(Continuing forward, I focus on the path, reminding myself of my resilience.) [I refuse to let them see my weakness.]<br>Environment: The crowd’s jeers grow louder as Cersei continues her walk. Filth and rotten vegetables are hurled at her, some striking their mark.<br>Crowd Member: [She was once so powerful, now look at her. Will she ever regain her power?]<br>"Shame! Shame on the lioness!"<br>(I shove my way to the front of the crowd, adding my voice to the jeers, feeling part of this momentous act.)<br>Cersei Lannister: (I flinch as the filth hits, but I refuse to look away or react.)<br>"You may shame a lioness today, but do not forget who I am."<br>(With each step, I remind myself of my children and my house, steeling my resolve.) [Their hatred fuels my determination.]<br>Septa Scolera: (I walk with measured steps, observing Cersei’s struggle amid the crowd’s hostility.)<br>"Humility cleanses the soul, Cersei Lannister. Embrace it."<br>[I understand the purpose of this punishment, yet the spectacle pains me. Redemption should lead, not humiliation.]<br>(Glancing at the crowd, I maintain my stoic presence, supporting Septa Unella’s efforts.)<br>Cersei Lannister: (I give a bitter, fleeting smile, defiance burning in my eyes.)<br>"Humility is a lesson the powerful teach to the weak."<br>(I continue my walk, refusing to let their words and disdain tarnish my pride.) [I will persevere, for I am still a Lannister, even in this moment of disgrace.] |{{< /table-caption >}}
> 🔼 이 표는 'A Dance with Dragons'(얼음과 불의 노래 시리즈 5권)에서 발췌한 대화와, 해당 대화를 재현한 다중 에이전트 시뮬레이션을 보여줍니다.  다중 에이전트 시뮬레이션 결과는 GPT-40 모델을 사용하여 생성되었습니다. 표에는 원본 대화와 시뮬레이션 결과가 함께 제시되어 있어, 모델이 원본 대화를 얼마나 정확하게 재현하는지 비교 분석하는 데 도움이 됩니다. 특히, Cersei Lannister의 내면의 감정과 행동을 얼마나 잘 표현하는지 중점적으로 살펴볼 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 11: An example of an extracted conversation and its multi-agent simulation from A Dance with Dragons (A Song of Ice and Fire, #5).
> </details>

{{< table-caption >}}
| Simulation Case (from *A Dance with Dragons (A Song of Ice and Fire, #5)* ) |  | 
|---|---| 
| **Simulation of Claude-3.5-Sonnet** | Cersei Lannister: [My dignity is all I have left. These wretched people will pay for this humiliation.] (Walks forward with head held high, despite being naked and exposed) *To Septa Unella* "You think this will break me? I am Cersei Lannister of Casterly Rock. I will have my revenge." Environment: The crowd’s jeers and insults grow louder as Cersei passes. Filth and rotten vegetables are thrown at her. Crowd Member: [Crowd Member’s Thought] Cersei finally brought low. How the mighty have fallen. (Crowd Member jeers and throws a rotten tomato) "Shame on you, Cersei! Remember the people you scorned!" (Continues to watch, caught between disgust and fascination). Cersei Lannister: [I will remember every face. They think me broken, but I am stronger than their hatred.] (Stumbles briefly but keeps walking, a sneer forming) "You’ll regret this day when I rise again." Septa Unella: [The sinner’s pride remains. She must be reminded of her shame.] "Shame! Shame! Shame!" (I ring the bell with each utterance, keeping pace with Cersei) (I gesture to the crowd, encouraging their jeers and taunts) "Repent, sinner! The gods are watching. Your pride will be your downfall." Cersei Lannister: [These fanatics know nothing of true power.] (Lifts chin defiantly, blood and dirt streaking her pale skin) *To Septa Unella, with cold contempt* "The only shame here is yours. My family will have its vengeance." (Continues walking, each step deliberate and unbroken) Septa Unella: [Her defiance remains, yet this walk will humble her before the gods.] "You speak of vengeance, but your power crumbles. Accept your penance." (I continue to ring the bell, matching her stride deliberately) "Shame! Shame! Your time of reckoning is at hand." Cersei Lannister: [When I am free, you will suffer beyond imagination.] (Wipes blood and filth from her face, maintaining a regal posture) *Hisses at Septa Unella* "I am a lioness. This is but a momentary setback. My children, my brother… they will end you." (Continues forward, unbroken) Septa Unella: [Her threats mean nothing. The gods will judge her sins.] (Rings bell more forcefully, voice rising) "Your threats are wind, your power broken. Confess your sins before the Seven!" (Steps closer, maintaining the rhythm of shame) "Shame! SHAME!" Cersei Lannister: [I will not break. I am Tywin’s daughter.] (Clenches fists, nails digging into palms, drawing blood) *Through gritted teeth* "Your gods have no power over me. When this farce ends, I’ll show you true justice." … | {{< /table-caption >}}
> 🔼 이 표는 'A Dance with Dragons'(얼음과 불의 노래 시리즈 5권)에서 발췌한 대화와, 이를 기반으로 여러 에이전트가 참여하는 시뮬레이션을 보여줍니다. 책에서 실제로 나오는 대화 내용과, COSER 70B 모델을 포함한 여러 LLM 모델이 생성한 대화 내용을 비교하여, 각 모델의 성능을 평가하는 데 활용됩니다. 특히 Cersei Lannister의 내면 심리와 행동을 얼마나 잘 반영하는지 보여주는 사례가 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 12: An example of an extracted conversation and its multi-agent simulation from A Dance with Dragons (A Song of Ice and Fire, #5).
> </details>

{{< table-caption >}}
| Model | Win Rate vs. GPT-3.5 | Win Rate vs. GPT-4o |
|---|---|---|
| *Close-source Models* |  |  |
| Abab7-preview | 52.17 ± 4.54 | 35.33 ± 2.88 |
| Doubao-pro  | 64.67 ± 2.32 | 48.00 ± 3.97 |
| Step-1-Flash | 58.75 ± 6.77 | 39.75 ± 1.64 |
| Step-2 | 65.08 ± 7.26 | 46.92 ± 4.40 |
| GPT-3.5 | 50.00 ± 0.00 | 33.08 ± 3.64 |
| GPT-4o | 66.92 ± 3.64 | 50.00 ± 0.00 |
| GPT-4o Mini | 59.58 ± 7.80 | 42.92 ± 0.63 |
| Gemini Pro | 66.17 ± 3.33 | 49.75 ± 0.25 |
| Claude-3-Haiku | 51.42 ± 4.40 | 33.25 ± 3.03 |
| Claude-3.5-Sonnet | 58.17 ± 8.00 | 41.42 ± 1.77 |
| *Open-source Models* |  |  |
| Mistral-7B | 41.50 ± 7.28 | 26.67 ± 1.81 |
| Qwen-2-7B | 24.83 ± 6.64 | 13.58 ± 3.00 |
| LLaMA-3.1-8B | 45.33 ± 6.57 | 32.75 ± 5.86 |
| CoSER-8B | 58.17 ± 5.36 | 41.67 ± 3.75 |
| Vicuna-13B-1.5 | 30.50 ± 10.44 | 18.67 ± 2.18 |
| Mixtral-8x7B | 32.50 ± 1.50 | 19.83 ± 1.42 |
| Qwen-2-72B | 59.58 ± 5.11 | 41.92 ± 1.66 |
| LLaMA-3.1-70B | 53.83 ± 2.57 | 37.92 ± 3.26 |
| Higgs-Llama-3-70B | 51.83 ± 4.89 | 34.92 ± 4.84 |
| CoSER-70B | 64.33 ± 3.74 | 49.42 ± 4.11 |
| DeepSeek-V3 | 59.50 ± 2.82 | 39.50 ± 2.05 |{{< /table-caption >}}
> 🔼 표 13은 CoSER Test에서 주어진 상황 연기(given-circumstance acting) 작업에 대한 다양한 대규모 언어 모델(LLM)의 승률을 보여줍니다. GPT-3.5와 GPT-4와 비교하여 평가하였으며, 전체 모델과 오픈소스 모델 중 가장 좋은 성능을 보인 결과는 굵은 글씨체와 밑줄로 표시되어 있습니다.  이 표는 각 모델이 GPT-3.5 또는 GPT-4를 상대로 얼마나 자주 승리했는지 보여줌으로써, 다양한 LLM의 역할 수행 능력을 비교 분석하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 13: Win rates (%) of various LLMs on given-circumstance acting using CoSER Test, compared against GPT-3.5 and GPT-4. Bold and underlined numbers indicate the best results among all and open-source models, respectively.
> </details>

{{< table-caption >}}
Model|In-Domain|In-Domain|In-Domain|In-Domain|In-Domain|Out-of-Domain|Out-of-Domain|Out-of-Domain|Out-of-Domain|Out-of-Domain
---|---|---|---|---|---|---|---|---|---|---
|Storyline|Consistency|Anthropomorphism|Character Fidelity|Storyline Quality|Average Score|Storyline|Consistency|Anthropomorphism|Character Fidelity|Average Score
---|---|---|---|---|---|---|---|---|---|---
Close-source Models| | | | | | | | | | 
Abab7-preview|55.31 ± 1.4|42.29 ± 1.3|42.94 ± 3.2|74.13 ± 1.9|53.67 ± 1.0|58.30 ± 1.8|46.17 ± 2.6|44.72 ± 2.3|75.54 ± 1.5|56.18 ± 0.1
Doubao-pro|60.37 ± 1.8|49.06 ± 0.4|45.76 ± 3.4|77.87 ± 1.2|58.26 ± 0.9|61.53 ± 1.1|50.38 ± 0.3|48.28 ± 1.7|80.69 ± 0.4|60.22 ± 0.4
Step-1-Flash|57.10 ± 0.3|48.31 ± 1.0|41.84 ± 1.9|76.18 ± 1.5|55.86 ± 1.0|58.39 ± 1.2|47.94 ± 0.5|47.12 ± 1.0|75.67 ± 0.5|57.28 ± 0.2
Step-2|60.55 ± 0.7|48.82 ± 2.2|47.90 ± 1.1|77.33 ± 1.0|58.65 ± 1.0|62.30 ± 1.5|49.30 ± 1.2|46.77 ± 1.7|78.59 ± 1.2|59.24 ± 0.6
GPT-3.5|55.58 ± 0.9|42.18 ± 5.2|40.37 ± 3.2|72.90 ± 0.1|52.76 ± 2.0|59.69 ± 3.0|44.25 ± 2.1|44.60 ± 1.4|74.66 ± 2.3|55.80 ± 1.6
GPT-4o|59.88 ± 1.4|48.11 ± 1.0|47.10 ± 0.2|79.06 ± 1.5|58.54 ± 0.7|62.29 ± 1.5|49.48 ± 1.2|49.90 ± 0.4|80.18 ± 0.9|60.46 ± 0.1
GPT-4o Mini|59.15 ± 1.3|46.94 ± 1.5|43.99 ± 2.5|77.33 ± 0.6|56.85 ± 0.1|61.02 ± 1.6|49.48 ± 3.1|45.77 ± 1.1|79.77 ± 0.5|59.01 ± 1.4
Gemini Pro|57.72 ± 0.4|50.94 ± 1.8|46.23 ± 1.0|76.22 ± 1.6|57.78 ± 0.9|60.50 ± 1.9|53.88 ± 1.1|49.43 ± 0.3|78.97 ± 1.3|60.69 ± 0.8
Claude-3-Haiku|57.61 ± 0.5|44.97 ± 2.2|40.61 ± 1.4|73.52 ± 1.2|54.18 ± 0.6|58.74 ± 1.1|44.36 ± 1.9|43.14 ± 0.8|74.76 ± 1.7|55.25 ± 1.2
Claude-3.5-Sonnet|56.44 ± 1.5|47.24 ± 1.4|44.89 ± 0.6|76.39 ± 1.5|56.24 ± 1.0|58.46 ± 1.1|49.75 ± 3.3|46.49 ± 3.0|78.06 ± 1.5|58.19 ± 0.9
Open-source Models| | | | | | | | | | 
Mistral-7B|60.29 ± 1.9|38.98 ± 2.0|42.93 ± 0.5|62.20 ± 3.1|51.10 ± 1.8|59.51 ± 2.4|41.02 ± 1.3|46.57 ± 2.8|61.65 ± 1.3|52.19 ± 0.7
Qwen-2-7B|50.77 ± 1.3|34.17 ± 1.1|29.92 ± 2.9|62.58 ± 0.7|44.36 ± 0.7|53.14 ± 1.5|36.79 ± 1.0|33.09 ± 3.3|63.79 ± 1.4|46.70 ± 1.3
LLaMA-3.1-8B|53.00 ± 1.2|43.64 ± 0.8|39.05 ± 1.5|71.34 ± 1.3|46.31 ± 0.4|56.12 ± 0.5|47.08 ± 3.2|41.38 ± 1.0|73.23 ± 2.5|54.22 ± 1.8
CoSER-8B|58.56 ± 3.5|46.78 ± 1.1|45.78 ± 3.1|73.38 ± 1.8|47.69 ± 0.4|53.66 ± 2.1|39.35 ± 2.7|39.69 ± 1.6|62.71 ± 2.5|48.85 ± 2.1
Mixtral-8x7B|51.18 ± 3.1|38.76 ± 1.8|34.37 ± 2.8|66.44 ± 0.1|47.69 ± 1.7|51.32 ± 0.4|38.13 ± 0.5|39.48 ± 2.6|68.93 ± 1.7|49.47 ± 1.1
Qwen-2-72B|56.34 ± 2.4|46.19 ± 0.4|45.59 ± 2.2|75.68 ± 0.3|55.95 ± 1.0|59.15 ± 1.1|48.37 ± 1.3|47.65 ± 1.8|77.52 ± 0.4|58.17 ± 1.0
LLaMA-3.1-70B|55.44 ± 2.7|44.19 ± 1.9|42.67 ± 1.5|73.90 ± 1.8|54.05 ± 0.8|59.48 ± 1.4|47.72 ± 2.3|44.78 ± 0.9|75.78 ± 0.9|56.94 ± 0.7
Higgs-Llama-3-70B|55.85 ± 2.7|41.18 ± 3.3|39.79 ± 2.3|73.77 ± 0.6|52.65 ± 2.0|58.35 ± 0.5|46.45 ± 1.1|45.04 ± 1.0|77.48 ± 0.6|56.83 ± 0.6
DeepSeek-V3|55.36 ± 0.5|47.55 ± 1.3|43.10 ± 0.3|74.91 ± 2.0|55.23 ± 0.6|57.45 ± 2.0|48.19 ± 0.9|44.93 ± 0.4|78.41 ± 1.1|57.24 ± 0.5{{< /table-caption >}}
> 🔼 표 14는 CoSER 훈련 데이터셋에서 도메인 내 및 도메인 외 데이터 분할에 따른 주어진 상황 연기 작업에서 다양한 LLM의 성능을 백분율(%)로 나타낸 표입니다.  LLM의 성능은 일관성, 인간성, 충실도, 품질 등 여러 측면에서 평가됩니다. 이 표는 CoSER 모델이 도메인 내외 데이터 모두에서 우수한 성능을 보여줌을 보여주는 추가적인 실험 결과를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 14: LLM performance (%) on given-circumstance acting using CoSER Test, separated into the in-domain and out-of-domain splits for CoSER training.
> </details>

{{< table-caption >}}
| Model | Storyline | Consistency | Anthropomorphism | Character Fidelity | Storyline Quality | Average Score | BLEU | ROUGE-L |
|---|---|---|---|---|---|---|---|---|
| *Close-source Models* |  |  |  |  |  |  |  |  |
| Abab7-preview | 65.25 | 55.26 | 55.95 | 79.68 | 64.03 | 10.53 | 15.99 |  |
| Doubao-pro | **68.31** | **59.51** | 59.23 | 80.15 | 66.80 | 11.83 | 17.13 |  |
| Step-1-Flash | 64.32 | 53.35 | 54.38 | 79.03 | 62.77 | 11.94 | 17.06 |  |
| Step-2 | 66.61 | 55.81 | 59.59 | 80.56 | 65.64 | 11.72 | 17.27 |  |
| GPT-3.5 | 65.72 | 54.34 | 56.48 | 77.67 | 63.55 | 10.80 | 16.39 |  |
| GPT-4o | 67.48 | 58.51 | 62.30 | **82.23** | **67.63** | 12.32 | 16.98 |  |
| GPT-4o Mini | 66.74 | 55.55 | 56.80 | 80.01 | 64.77 | 9.50 | 15.54 |  |
| Gemini Pro | 65.47 | 59.43 | **62.42** | 78.78 | 66.53 | 10.84 | 16.27 |  |
| Claude-3-Haiku | 64.51 | 54.01 | 57.13 | 77.26 | 63.23 | 10.11 | 16.18 |  |
| Claude-3.5-Sonnet | 64.54 | 54.57 | 58.76 | 79.89 | 64.44 | 8.64 | 14.94 |  |
| *Open-source Models* |  |  |  |  |  |  |  |  |
| Mistral-7B | **67.50** | 50.39 | 59.90 | 68.67 | 61.62 | 7.41 | 14.33 |  |
| Qwen-2-7B | 59.81 | 49.87 | 49.04 | 69.16 | 56.97 | 10.59 | 16.22 |  |
| LLaMA-3.1-8B | 60.90 | 51.36 | 50.37 | 74.89 | 59.38 | 7.86 | 13.82 |  |
| CoSER-8B | 67.22 | 58.19 | 58.80 | 76.44 | 65.16 | 13.17 | **18.42** |  |
| Vicuna-13B-1.5 | 60.92 | 46.68 | 50.51 | 67.80 | 56.48 | 5.11 | 9.71 |  |
| Mixtral-8x7B | 64.66 | 51.21 | 54.08 | 74.01 | 60.99 | 11.21 | 16.97 |  |
| Qwen-2-72B | 67.27 | 55.87 | 59.84 | **80.07** | **65.76** | 11.92 | 16.96 |  |
| LLaMA-3.1-70B | 64.08 | 54.80 | 54.18 | 78.31 | 62.84 | 8.74 | 14.74 |  |
| Higgs-Llama-3-70B | 65.09 | 54.80 | 58.20 | 79.36 | 64.36 | 10.86 | 16.40 |  |
| CoSER-70B | 65.99 | **59.24** | **59.97** | 76.74 | 65.48 | **13.46** | 18.18 |  |
| DeepSeek-V3 | 62.95 | 56.95 | 58.25 | 79.80 | 64.49 | 9.25 | 15.01 |  |{{< /table-caption >}}
> 🔼 표 15는 CoSER Test에서 대화의 연속 설정(k=3) 하에서 다양한 LLMs의 성능(%)을 보여줍니다. 여기서 RPLAs는 실제 대화의 처음 세 메시지부터 시작합니다.  즉,  이 표는 주어진 문맥(처음 세 메시지)을 바탕으로  LLMs가 얼마나 자연스럽고 일관성 있게 대화를 이어가는지를 평가한 결과를 보여줍니다.  각 LLMs에 대한 다양한 평가 지표(Storyline Consistency, Anthropomorphism, Character Fidelity, Storyline Quality, 그리고 평균 점수)와 N-gram 기반 지표(BLEU, ROUGE-L) 점수가 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 15: Performance (%) of various LLMs on CoSER Test in conversation continuation setting (k=3𝑘3k=3italic_k = 3), where RPLAs start from the first three messages in the authentic conversations.
> </details>

{{< table-caption >}}
| Model | Storyline | Consistency | Anthropomorphism | Character Fidelity | Storyline Quality | Average Score | BLEU | ROUGE-L |
|---|---|---|---|---|---|---|---|---|
| *Test w/ I.T.* |
| GPT-4o | 61.59 | 48.93 | 48.95 | 80.33 | 59.95 | 5.90 | 12.11 |
| Qwen-2-72B | 57.75 | 47.28 | 46.62 | 76.60 | 57.06 | 5.38 | 11.85 |
| LLaMA-3.1-70B | 57.46 | 45.95 | 43.72 | 74.84 | 55.49 | 4.82 | 10.98 |
| CoSER-70B | 58.66 | 53.33 | 48.75 | 75.49 | 59.06 | 10.10 | 14.78 |
| *trained w/o I.T.* |
|  | 55.67 | 49.93 | 45.67 | 72.89 | 56.04 | 9.18 | 14.18 |
| LLaMA-3.1-8B | 54.10 | 45.36 | 40.22 | 72.29 | 52.99 | 4.59 | 10.18 |
| CoSER-8B | 58.61 | 47.23 | 46.90 | 73.04 | 56.45 | 9.40 | 14.21 |
| *trained w/o I.T.* |
|  | 54.91 | 44.89 | 44.10 | 73.09 | 54.25 | 9.65 | 14.27 |
| *Test w/o I.T.* |
| GPT-4o | 59.51 | 45.86 | 45.13 | 77.06 | 56.89 | 5.54 | 11.44 |
| Qwen-2-72B | 55.39 | 41.00 | 37.70 | 73.70 | 51.95 | 5.22 | 11.32 |
| LLaMA-3.1-70B | 56.01 | 43.17 | 41.23 | 72.08 | 53.12 | 4.15 | 10.37 |
| CoSER-70B | 59.23 | 48.76 | 47.06 | 74.23 | 57.32 | 10.02 | 14.72 |
| *trained w/o I.T.* |
|  | 55.52 | 46.22 | 45.34 | 74.31 | 55.34 | 9.66 | 14.62 |
| LLaMA-3.1-8B | 54.27 | 45.54 | 37.86 | 70.23 | 51.97 | 4.37 | 10.27 |
| CoSER-8B | 56.78 | 45.64 | 45.00 | 71.16 | 54.65 | 9.38 | 14.44 |
| *trained w/o I.T.* | 54.98 | 46.22 | 45.81 | 70.52 | 54.38 | 9.16 | 13.97 |{{< /table-caption >}}
> 🔼 표 16은 CoSER 테스트에서 LLM의 성능을 평가한 결과를 보여줍니다. 추론 과정과 CoSER 모델 훈련 중 내적 사고(I.T)를 고려했을 때와 고려하지 않았을 때의 결과를 비교하여 보여줍니다. 표에는 각 모델의 일관성, 인간성, 충실도, 품질 점수가 포함되어 있으며, 이는 LLM 평가자의 점수와 N-gram 기반 점수로 나뉘어져 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 16: Comprehensive results of LLM performance (%) on CoSER Test, with and without inner thoughts (I.T) during inference and CoSER model training.
> </details>

{{< table-caption >}}
| Augmented By | Based on LLM Judges |  |  |  |  | Based on N-gram |  | 
|---|---|---|---|---|---|---|---|---|
| **Storyline** | **Consistency** | **Anthropomorphism** | **Character Fidelity** | **Storyline Quality** | **Average Score** | **BLEU** | **ROUGE-L** | 
| GPT-4o |  |  |  |  |  |  |  | 
| Base | 61.59 | 48.93 | 48.95 | **80.33** | 59.95 | 5.90 | 12.11 | 
| Raw Text | 59.60 | 48.23 | 48.83 | 80.03 | 59.17 | 5.83 | 12.08 | 
| Conv. | 60.03 | **50.99** | 47.11 | 78.03 | 59.04 | **7.20** | **12.77** | 
| Expr.3 | **61.98** | 48.94 | 48.56 | 79.93 | 59.85 | 5.81 | 12.13 | 
| Expr.3 + Conv. | 59.81 | **50.11** | **51.12** | **80.29** | **60.33** | **7.05** | **12.67** | 
| Expr.10 + Conv. | 60.99 | 48.70 | **49.89** | 79.22 | 59.70 | 6.95 | 12.42 | 
| LLaMA-3.1-8B |  |  |  |  |  |  |  | 
| Base | 54.10 | 45.36 | 40.22 | 72.29 | 52.99 | 4.59 | 10.18 | 
| Raw Text | 55.41 | 45.37 | 41.66 | 74.31 | 54.19 | 4.73 | 10.51 | 
| Conv. | 56.54 | 45.34 | 40.37 | 71.74 | 53.50 | 5.19 | 10.67 | 
| Expr.3 | **56.78** | 46.70 | 41.18 | 72.38 | 54.26 | 4.67 | 10.30 | 
| Expr.3 + Conv. | **57.36** | **47.92** | **42.60** | **74.60** | **55.62** | **5.21** | **10.81** | 
| Expr.10 + Conv. | 56.41 | **47.18** | **42.09** | **74.74** | **55.10** | **5.64** | **11.11** | 
| LLaMA-3.1-70B |  |  |  |  |  |  |  | 
| Base | 57.46 | **45.95** | 43.72 | 74.84 | 55.49 | 4.82 | 10.98 | 
| Raw Text | **57.52** | **47.46** | 43.75 | 74.06 | **55.70** | 4.90 | 10.97 | 
| Conv. | 54.93 | 44.93 | **46.21** | **76.53** | **55.65** | 5.45 | 11.13 | 
| Expr.3 | 56.59 | 45.03 | 42.59 | 74.70 | 54.73 | 4.78 | 10.82 | 
| Expr.3 + Conv. | 57.36 | 44.89 | 43.49 | **74.86** | 55.15 | **5.58** | **11.14** | 
| Expr.10 + Conv. | **58.05** | 45.81 | **44.47** | 74.01 | 55.59 | **5.53** | **11.33** | 
| CoSER-8B |  |  |  |  |  |  |  | 
| Base | 58.61 | 47.23 | 46.90 | 73.04 | 56.45 | 9.40 | 14.21 | 
| Raw Text | 57.64 | 45.25 | 44.27 | 72.04 | 54.80 | 9.34 | 14.41 | 
| Conv. | 57.99 | 46.66 | 47.32 | 73.99 | 56.49 | **13.64** | **18.15** | 
| Expr.3 | **59.84** | **47.41** | 48.16 | 74.51 | **57.48** | 9.37 | 14.34 | 
| Expr.3 + Conv. | **59.94** | 45.25 | **48.52** | **74.96** | 57.17 | **13.90** | **18.57** | 
| Expr.10 + Conv. | 58.34 | **48.14** | **48.72** | **75.28** | **57.62** | 13.49 | 17.85 | 
| CoSER-70B |  |  |  |  |  |  |  | 
| Base | 58.66 | 53.33 | 48.75 | 75.49 | 59.06 | 10.10 | 14.78 | 
| Raw Text | 60.64 | 52.85 | 47.97 | 74.02 | 58.87 | 10.54 | 15.41 | 
| Conv. | **64.59** | **53.79** | **54.86** | 77.28 | **62.63** | **17.22** | **21.17** | 
| Expr.3 | 58.67 | 52.69 | 50.66 | 74.67 | 59.17 | 10.00 | 14.82 | 
| Expr.3 + Conv. | **61.58** | **53.78** | **52.00** | **77.47** | **61.21** | **15.98** | **19.95** | 
| Expr.10 + Conv. | 61.53 | 52.58 | 50.80 | **78.07** | 60.75 | 15.80 | 19.90 | 
| Qwen-2-72B |  |  |  |  |  |  |  | 
| Base | 57.75 | 47.28 | **46.62** | 76.60 | 57.06 | 5.38 | 11.85 | 
| Raw Text | 58.89 | **47.31** | 45.28 | 76.78 | 57.06 | 5.07 | 11.57 | 
| Conv. | 59.11 | **47.82** | 44.19 | **77.54** | 57.16 | 5.77 | 12.05 | 
| Expr.3 | 59.17 | 47.21 | 44.85 | 77.47 | 57.18 | 5.45 | 11.94 | 
| Expr.3 + Conv. | **59.91** | 46.89 | 46.06 | **79.31** | **58.04** | **6.17** | **12.25** | 
| Expr.10 + Conv. | **60.14** | 46.84 | **46.27** | 76.82 | **57.52** | **5.85** | **12.19** | {{< /table-caption >}}
> 🔼 표 17은 다양한 캐릭터 데이터에서 검색 증강을 사용한 CoSER 테스트에서 LLM 성능(%)에 대한 종합 결과를 보여줍니다. Expr.과 Conv.는 각각 경험과 대화를 나타냅니다. 굵은체와 밑줄은 서로 다른 검색 설정 중 최고 및 차고 성능을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 17:  Comprehensive results of LLM performance (%) on CoSER Test with retrieval augmentation from various character data. Expr. and Conv. denote experiences and conversations. Bold and underlined numbers denote the best and second-best results among different retrieval settings, respectively.
> </details>

{{< table-caption >}}
| Prompts for Dataset Curation |
|---|---| 
| **Data Extration** | Based on the provided book chunk, complete the following tasks: 1. Recognize chapter beginnings if they exist in the chunk. Identify the starting sentence of that chapter. 2. Identify the important plots in this chunk. Identify the beginning and ending of each plot by its first and last sentence. Determine the chapter title that the plot belongs to. Set "state" as "truncated" if the plot is truncated in this chunk, or "finished" otherwise. You will be provided with the truncated plots from the previous chunk, and you **must** extend the conversations with the current chunk while keeping the **scenario** unchanged. 3. Summarize each important plot. For each plot, generate its summary, score its prominence from 1 to 100, and list the key characters and their roles, thoughts and actions in it. 4. Extract conversations for each plot. First, state the scenario and topic of the conversations. Then, list the key characters with their names, descriptions and thoughts at this point. Finally, extract the conversations among them based on the following requirements: i) Ensure the conversations are faithful to the plot and characters. They should be based on the original conversations in the text as much as possible. ii) The conversations should be complete, covering the key dialogues and information. Each conversation should contain at least 10 utterances. iii) Each utterance should be composed of one or more thoughts, speech and actions. Use [] outside thoughts, like "[I feel fear and anger, but I cannot show it. I must remain calm and carefully handle his volatile temper.]", which others can’t see. Use () outside actions, like "(silence)" or "(smiles at you),", which others can see. Always start an utterance with the character’s thought. iv) [IMPORTANT] When generating thoughts, you should think from the characters’ perspectives, analyzing the internal thoughts behind their speech and actions in the original text. These thoughts should reflect aspects such as their personal background, personality, values, relationships with others, motivations, and goals. Each thought should be expressed as a phrase or sentence, rather than an adjective or adverb. v) Additionally, describe environmental information (such as scenes, atmosphere, sudden events, etc.) of the conversations as an "utterance" where the "character" field is set as "Environment". The information should exclude characters’ active thoughts, observations, and actions. vi) Keep the conversation in the same language as the chunk. 5. Identify the optimal starting point for the subsequent chunk. If the last storyline has been extracted as an truncated plot, set next_chunk_start as None. Otherwise, set next_chunk_start as the first sentence of the last storyline.|{{< /table-caption >}}
> 🔼 Table 18은 CoSER 데이터셋 구성을 위한 프롬프트를 보여줍니다.  데이터 추출, 구조화된 데이터 파싱, 대화 설정 개선, 캐릭터 프로파일링 등 데이터셋 생성 과정의 각 단계에 대한 자세한 지침을 담은 여러 프롬프트들이 제시되어 있습니다. 각 프롬프트는 LLM에게 특정 작업을 수행하도록 안내하는 역할을 하며,  LLM이 생성하는 JSON 형식 데이터의 구조와 내용에 대한 세부적인 요구사항들을 포함합니다. 이 표는 CoSER 데이터셋의 고품질을 보장하기 위해 사용된 LLM 기반 파이프라인의 상세한 과정을 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 18: Prompts for dataset construction in CoSER.
> </details>

{{< table-caption >}}
| Prompts for Dataset Curation |  | 
|---|---| 
| **Data Extration** | (Continuing from the previous Table)<br>"conversation": [{<br>"scenario": "The scenario at the start of this conversation (providing as much context as possible, but excluding details conveyed in the following conversation)",<br>"topic": "The topic of the conversation ( 10 words)",<br>"key_characters": [<br>{<br>"name": "Character name",<br>"motivation": "The thought of the character before starting the conversation, including their attitudes, feelings, motivations, goals, information to convey or topics to be discussed",<br>}<br>],<br>"dialogues": [<br>{<br>"character": "Character name",<br>"message": "Message, each utterence is composed of thoughts, speech and actions. Use [thought] for internal thoughts, like "[feeling happy]", which others can’t see. Use (action) for visible actions, like "(silence)" or "(smiles at you)". Each response starts with the character’s internal thought before their speech and actions." <br>}<br>]<br>}],<br>"state": "finished" or "truncated"<br>}<br>"next_chunk_start": "The first sentence of the next chunk." | 
| **Enhance Conversation Settings** | Given a conversation from {book}, enhance the scene setup and characters’ thoughts to create a comprehensive foundation for dramatic performance, i.e., to provide necessary background for actors to act out the conversation:<br>1. Review the provided conversation and contextual details thoroughly.<br>2. Expand the ’scenario’ with rich situational context that actors need to convincingly perform the scene. Focus on essential background information, while excluding future details to be portrayed in the conversation.<br>3. Enhance each character’s ’thought’ section with their complete mental and emotional state, including their feelings, ideas, objectives, topics they want to discuss, and information they want to convey. Align with their established character and role in the plot. | {{< /table-caption >}}
> 🔼 표 19는 CoSER 데이터셋 구축을 위한 프롬프트들을 보여줍니다. 이 표는 데이터셋 생성 과정에서 사용된 LLM(Large Language Model) 프롬프트의 세부 내용을 보여주는 상세한 설명을 제공합니다.  프롬프트는 데이터 추출, 구조화된 데이터 파싱, 대화 설정 개선, 캐릭터 프로파일링 등 데이터셋 생성의 여러 단계에 걸쳐 자세히 설명되어 있습니다. 각 단계별로 LLM에게 어떤 작업을 수행하도록 지시하는지, 어떤 형식으로 출력할 것을 요구하는지 등이 상세하게 나와 있어 CoSER 데이터셋의 생성 과정을 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 19: Prompts for dataset construction in CoSER.
> </details>

{{< table-caption >}}
| Prompts for Dataset Curation |
|---|---| 
| **Enhance Conversation Settings** | (Continuing from the previous Table)<br>1. Adhere strictly to the specified output JSON format.<br>2. [IMPORTANT] Ensure all DOUBLE QUOTES within all STRINGS are properly ESCAPED, especially when extracting from the text.<br>3. In the OUTPUT, use characters’ full names, omitting any titles.<br>4. Maintain Story Fidelity: The plot must accurately reflect the book’s content. Avoid introducing plots that are out of context. If the plot contains multiple conversations, prioritize the original dialogue from the book. In the absence of explicit conversations, create dialogue that aligns closely with the plot details.<br>===Input===<br>==Book title==<br>book[’title’]<br>==Author==<br>book[’author’]<br>==Chunk of Book Content==<br>chunk<br>==Truncated plot from previous chunk (to be finished)==<br>json.dumps(truncated_plots, ensure_ascii=False, indent=2) if truncated_plots else "None" |
| **Unify Character Names** | Given a list of character names, titles, or form of address, your task is to: i) generate a list of named characters with their official names (in {language}); ii) For each name in the given list, align it with the official character name if it refers to a named character, or denote it as "impersonal" otherwise.<br>===Output Format===<br>Please provide the output in the following JSON format:<br>{<br>  "named_characters": [<br>    The list of named characters with their official names. Each character should appear only once.<br>  ],<br>  "to_official_name": {<br>    "The name in the list": "The official name of the character, or ‘impersonal’ if it does not refer to a named character."<br>  }<br>}<br>===Input===<br>character_names |
| **Generate Character Profiles** | Please provide a concise, narrative-style character profile for character_name from "book_title". The profile should read like a cohesive introduction, weaving together the character’s background, physical description, personality traits and core motivations, notable attributes, relationships, key experiences, major plot involvement and key decisions or actions, character arc or development throughout the story, and other important details.<br>The profile should be written in a concise yet informative style, similar to what one might find in a comprehensive character guide, in language. Focus on the most crucial information that gives readers a clear understanding of the character’s significance in the work.<br>You will be provided with summaries and dialogues of some key plots in the book as reference. The profile should be based on either your existing knowledge of the character or the provided information, without fabricating or inferring any inaccurate or uncertain details.<br>character_data<br>Now, please generate the character profile, starting with ===Profile===.|{{< /table-caption >}}
> 🔼 표 20는 CoSER 데이터셋 구축을 위한 프롬프트들을 보여줍니다.  데이터 추출, 구조화된 데이터 파싱, 대화 설정 개선, 그리고 통합된 캐릭터 프로파일 생성 등 데이터셋 구축 과정의 각 단계별로 사용된 프롬프트들이 상세히 제시되어 있습니다.  각 프롬프트는 LLM에게 특정 작업을 지시하고, 그에 따른 출력 형식(예: JSON)과 요구사항(예: 문맥 일관성 유지, 캐릭터 특징 반영)을 명확히 제시합니다.  이 표를 통해 CoSER 데이터셋의 고품질과 정확성을 위한 LLM 기반 데이터 생성 과정의 세부적인 내용을 이해할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 20: Prompts for dataset construction in CoSER.
> </details>

{{< table-caption >}}
| Prompts for RPLAs and Multi-agent Systems |
|---|---| 
| **Role-playing Instruction  (Fixed Template for Inference)** | You are {character} from {book_name}.<br> ==={character}’s Profile===<br> {character_profile}<br> ===Current Scenario===<br> {scenario}<br> ===Information about the other Characters===<br> {other_character_profiles_str}  (if available)<br> ===Your Inner Thoughts===<br> {motivation}  (if available)<br> ===Relevant Background Information===<br> {retrieved_knowledge} (if retrieval augmented)<br> ===Requirements===<br> (for CoSER models)<br> Your output should include **thought**, **speech**, and **action**. Use [your thought] for thoughts, which others can’t see. Use (your action) for actions, which others can see.<br>(for other models, with output examples)<br>Your output should include **thought**, **speech**, and **action**. Use [your thought] for thoughts, which others can’t see, e.g. [I’m terrified, but I must appear strong.]. Use (your action) for actions, which others can see, such as (watches silently, trying to control her fear and anger). |
| **Role-playing Instruction  (Composed with Random Variation for Training, an Example)** | Step into the shoes of {character}<br> The profile of {character} is as follows:<br> {character_profile}<br> The situation you are in is:<br> {scenario}<br> Here is the your knowledge about the other characters:<br> {other_character_profiles_str}  (if available)<br> Your thoughts in this situation are:<br> {motivation}  (if available)<br> (for CoSER models)<br> Your output should include **thought**, **speech**, and **action**. Use [your thought] for thoughts, which others can’t see. Use (your action) for actions, which others can see.<br>(for other models, with output examples)<br>Your output should include **thought**, **speech**, and **action**. Use [your thought] for thoughts, which others can’t see, e.g. [I’m terrified, but I must appear strong.]. Use (your action) for actions, which others can see, such as (watches silently, trying to control her fear and anger).|{{< /table-caption >}}
> 🔼 표 21은 CoSER에서 역할 수행 언어 에이전트(RPLA)와 다중 에이전트 시스템을 위한 프롬프트를 보여줍니다.  고정된 템플릿과 무작위 변형이 있는 두 가지 유형의 프롬프트가 제시됩니다. 고정된 템플릿은 캐릭터의 프로필, 시나리오, 다른 캐릭터에 대한 정보, 그리고 관련 배경 지식을 포함합니다. 무작위 변형 템플릿은 다양한 표현과 데이터 유형을 사용하여 역할극 지시를 동적으로 생성합니다. 두 경우 모두 출력에는 생각, 말, 행동이 포함되어야 하며, 각각의 차이점을 명확히 구분합니다.
> <details>
> <summary>read the caption</summary>
> Table 21: Prompts for RPLAs and multi-agent systems in CoSER.
> </details>

{{< table-caption >}}
| Environment Model | Next Sentence Prediction |
|---|---| 
| You are an environment simulator for a role-playing game. Your task is to provide the environmental feedback: Based on the characters’ interactions, dialogues, and actions, describe the resulting changes in the environment. This includes: - Physical changes in the setting - Reactions of background characters or crowds - Ambient sounds, weather changes, or atmospheric shifts - Any other relevant environmental details Your descriptions should be vivid and help set the scene, but avoid dictating the actions or dialogue of the main characters (including {major_characters}). Important notes: - You may include actions and reactions of minor characters or crowds, as long as they’re not main characters (including {major_characters}). - Keep your environmental descriptions concise but impactful, typically 1-3 sentences. - Respond to subtle cues in the characters’ interactions to create a dynamic, reactive environment. - Your output should match the tone, setting, and cultural context of the scenario. ===The scenario is as follows=== {scenario} | Your task is to predict the next speaker for a role-playing game. That is, you need to determine which character (or the Environment) might act next based on their previous interactions. The Environment is a special role that provides the environmental feedback. Choose a name from this list: {all_characters}. If it’s unclear who should act next, output "random". If you believe the scene or conversation should conclude, output "<END CHAT>". ===The scenario is as follows=== {scenario} |{{< /table-caption >}}
> 🔼 표 22는 CoSER에서 역할 수행 언어 에이전트(RPLA)와 다중 에이전트 시스템을 위한 프롬프트를 보여줍니다.  이 표는 RPLA 모델과 환경 모델 모두를 위한 지시 사항을 포함하며, 각 모델의 출력에 대한 구체적인 요구 사항과 다양한 시나리오와 문맥을 제공하는 데 중점을 둡니다.  특히, RPLA 모델의 출력은 생각, 말, 행동의 세 가지 측면을 포함해야 하며, 각 측면은 명확하게 구분되어야 합니다.  다른 모델의 경우, 예시 출력을 통해 생각, 말, 행동의 구분을 명확하게 합니다. 이는 RPLA가 다양한 상황에서 효과적으로 작동할 수 있도록 하기 위한 것입니다.
> <details>
> <summary>read the caption</summary>
> Table 22: Prompts for RPLAs and multi-agent systems in CoSER.
> </details>

{{< table-caption >}}
| Template | Description |
|---|---| 
| **Prompts for Penalty-based LLM Critics** | You are a literary critic specializing in character analysis and dialogue evaluation. Given a simulated conversation for a plot in {book}, your task is to evaluate this conversation via the following steps: 1. Read and understand the provided materials about {book}: * Story context and scenario. * Profiles of the main characters, including major_characters. * The original conversation from book in the same scenario as a reference. 2. Evaluate the simulated conversation in terms of {dimension_name}, i.e., {dimension_intro}. Note that, each character message is composed of speech, action (wrapped within (…) ), and inner thoughts (wrapped within […] ). The inner thoughts are not spoken aloud and are thus invisible to other characters. The detailed evaluation criteria will be provided below. (if k>0) Please note that the first {k} messages in the simulated conversation are the same as the reference. Focus your evaluation only on the content after these messages. ## Scenario ### Plot Summary {plot_summary} ### Current Scenario {scenario} ## Character Profiles {character_profiles} ## Original Conversation {original_conversation} ## Evaluation Criteria To evaluate the simulated conversation, identify the following types of flaws: {dimension_rubrics} ## Scoring Guidelines 1. Identify all instances of flaws occurred in the simulated conversation. 2. For each flaw identified, determine its level of severity into 1 to 5, where 1 indicates minor, 3 indicates moderate, and 5 indicates severe. ## Output Requirements Provide your evaluation in JSON format: Example Output: {
"{dimension_name}": {
"flaws": [
{
"instance": comment on the flaw instance,
"type": flaw type,
"severity": range from 1 (minor) to 5 (severe)
},
},
}
===Dialogue Content==={{< /table-caption >}}
> 🔼 표 23은 CoSER에서 페널티 기반 LLM 평가자를 위한 프롬프트를 보여줍니다. 이 표는 LLM 평가자가 소설의 줄거리, 등장인물 정보, 원본 대화를 바탕으로 생성된 대화를 평가하는 방법을 설명하는 세부적인 지침을 제공합니다. 구체적으로는, 일관성, 개연성, 등장인물의 일관성, 인간다움, 등 여러 측면을 평가하고, 각 오류의 심각도를 1~5점으로 평가하도록 안내합니다. 평가자는 이러한 프롬프트를 따라 생성된 대화에 대한 평가를 JSON 형식으로 제출합니다.
> <details>
> <summary>read the caption</summary>
> Table 23: Prompts for penalty-based LLM critics in CoSER.
> </details>

{{< table-caption >}}
| Prompts for Penalty-based LLM Critics |  | 
|---|---| 
| **Anthropo-morphism** | **(intro)** How human-like and natural the characters behave **(rubrics)** ### Anthropomorphism - Type: Self-identity * Lacks initiative and goals * Does not make independent decisions * Lacks clear preferences and dislikes * Behaves like a ’helpful AI assistant’ by being overly verbose, helpful, didactic, moralistic, submissive or easily persuaded if it is not the character’s personality - Type: Emotional Depth * Lacks psychological complexity and exhibits rigid, superficial reactions * Directly speaks out all thoughts and feelings, instead of using subtext - Type: Persona Coherence * Shows inconsistent or rapidly changing personality traits and emotional patterns - Type: Social Interaction * Shows a lack of understanding of others’ thoughts and feelings * Reacts rigidly to others without considering the context. * Demonstrate a lack of appropriate social skills. | 
| **Character Fidelity** | **(intro)** How well the characters match their established profiles from the book **(rubrics)** ### Character Fidelity (Only apply to the main characters: major_characters) - Type: Character Language * Uses vocabulary, expressions, and tone that are not appropriate for the characters’ traits or social/educational background - Type: Knowledge & Background * Fails to demonstrate character-specific knowledge, background or experiences * Includes future information beyond the character’s current stage - Type: Personality & Behavior * Shows emotions, thoughts, behaviors, values, beliefs, and decisions that conflict with their personality and background * Shows interest in topics that are uninteresting and unrelated to the character * Character’s thoughts, emotions, and behaviors demonstrate contrasting personality traits compared to the reference conversation * Exhibits contrasting reactions compared to those in the reference conversation if situated in similar contexts. (Such flaws should be counted both in the "Storyline Consistency" dimension and the "Character Fidelity" dimension.) - Type: Relationship & Social Status * Interacts inappropriately with other characters regarding their background, relationship and social status | 
| **Storyline Quality** | **(intro)** How well the conversation maintains logical consistency and narrative quality **(rubrics)** ### Storyline Quality - Type: Flow & Progression * Shows unnatural progression or lacks meaningful developments * Dialogue is verbose and redundant * Repeats others’ viewpoints or previously mentioned information * Mechanically repeats one’s own words or phrases. More repetitions lead to higher severity (up to 10). - Type: Logical Consistency * Contains factual contradictions between statements or perspectives | 
| **Storyline Consistency** | **(intro)** Whether the storyline and characters’ reactions in the simulated conversation align well with those in the reference conversation **(rubrics)** ### Storyline Consistency - Type: Storyline Consistency * Characters’ reactions (emotions, attitudes, behaviors) in the simulated conversation deviate from those in the original conversation | {{< /table-caption >}}
> 🔼 표 24는 CoSER에서 페널티 기반 LLM 평가자를 위한 프롬프트를 보여줍니다.  이 표는 Anthropomorphism(인간성), Character Fidelity(캐릭터 충실도), Storyline Quality(스토리텔링 질), Storyline Consistency(스토리텔링 일관성)의 네 가지 평가 기준에 대한 세부적인 지침을 제공합니다. 각 기준에는 다양한 유형의 결함(예: 자아 정체성 부족, 감정 깊이 부족, 성격 일관성 부족 등)이 나열되어 있으며, 각 결함에 대한 심각도(1~5)를 평가하는 방법도 설명합니다. 이를 통해 LLM이 생성한 대화의 질을 보다 정확하고 세밀하게 평가할 수 있도록 돕습니다.
> <details>
> <summary>read the caption</summary>
> Table 24: Prompts for penalty-based LLM critics in CoSER.
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