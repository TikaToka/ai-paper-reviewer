---
title: "CypherBench: Towards Precise Retrieval over Full-scale Modern Knowledge Graphs in the LLM Era"
summary: "본 연구는 대규모 현대 지식 그래프에서 LLM을 이용한 정확한 정보 검색을 위한 새로운 벤치마크인 CypherBench를 제시합니다.  기존의 RDF 기반 지식 그래프는 과도하게 큰 스키마와 리소스 식별자 사용으로 LLM에 비효율적이라는 문제점을 분석합니다.  특히, Wikidata와 같은 현대 지식 그래프는 LLM의 문맥 창 크기를 초과하는 경우가 많습니..."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Question Answering", "🏢 Megagon Labs",]
showSummary: true
date: 2024-12-24
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.18702 {{< /keyword >}}
{{< keyword icon="writer" >}} Yanlin Feng et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-30 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.18702" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.18702" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/cypherbench-towards-precise-retrieval-over" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

최근 대규모 언어 모델(LLM) 기반의 RAG(Retrieval Augmented Generation) 시스템이 주목받고 있지만, Wikidata와 같은 현대적인 지식 그래프로부터의 효율적인 정보 검색은 여전히 어려운 과제입니다.  기존 지식 그래프는 과도하게 큰 스키마, 리소스 식별자 사용, 관계형 유형 중복 및 정규화 부족 등의 문제점을 가지고 있어 LLM의 제한된 문맥 창 크기에 부적합합니다. 이로 인해 Langchain 및 LlamaIndex와 같은 주요 LLM 프레임워크는 Wikidata와 같은 현대 지식 그래프에 대한 지원이 미흡합니다.

본 논문에서는 이러한 문제를 해결하기 위해 기존 RDF 그래프를 여러 개의 작은 속성 그래프로 변환하고, Cypher를 사용하여 LLM이 효율적으로 질의할 수 있도록 하는 새로운 방법론을 제시합니다. Wikidata를 기반으로 구축한 CypherBench 벤치마크는 780만 개의 엔터티와 10,000개 이상의 질문으로 구성되어 있으며, 이를 통해  LLM의 텍스트-Cypher 검색 성능을 평가하고, 향후 연구를 위한 기반을 마련합니다.  본 연구는 RDF-속성 그래프 변환 엔진, 텍스트-Cypher 작업 생성 파이프라인, 새로운 평가 지표를 개발하는 등의 기술적 기여를 통해 대규모 지식 그래프에서 LLM을 이용한 정확한 정보 검색 기술 발전에 크게 기여할 것으로 기대됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} LLM을 이용한 대규모 현대 지식 그래프 검색의 어려움을 분석하고 해결 방안 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} Wikidata 기반 11개의 대규모 다중 도메인 속성 그래프와 10,000개 이상의 질문으로 구성된 CypherBench 벤치마크 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} RDF-속성 그래프 변환 엔진, 텍스트-Cypher 작업 생성 파이프라인, 새로운 평가 지표 개발 등의 기술적 기여 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대규모 지식 그래프에서 효율적이고 정확한 텍스트-Cypher 검색을 가능하게 하는 새로운 방법론**을 제시하고, 이를 위한 **CypherBench라는 새로운 벤치마크**를 소개합니다. 이는 **LLM 시대에 지식 그래프 검색의 난관을 해결하고, 향후 연구를 위한 중요한 기반**을 제공할 것으로 예상됩니다.  LLM 기반 RAG 시스템의 발전에 크게 기여하며, **다양한 도메인의 대규모 속성 그래프**를 제공하여 관련 분야 연구자들에게 귀중한 자원이 될 것입니다.  특히, **글로벌 쿼리와 같은 복잡한 쿼리 유형**을 포함하여 기존 벤치마크보다 훨씬 까다로운 과제를 제시합니다. 

------
#### Visual Insights



![](https://arxiv.org/html/2412.18702/x1.png)

> 🔼 그림 1은 RDF 그래프와 속성 그래프 모두에 대한 검색을 위한 통합 인터페이스로서의 Cypher를 보여줍니다. 전형적인 그래프 검색 또는 RAG 워크플로는 다음 세 단계를 포함합니다. 1) LLM을 사용한 텍스트-Cypher 변환, 2) Cypher 쿼리 실행, 그리고 선택적으로 3) 최종 답변 생성입니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: An illustration of Cypher as a unified interface for retrieval over both RDF and property graphs. A typical graph retrieval or RAG workflow involves: 1) text-to-Cypher translation using an LLM, 2) Cypher query execution, and optionally, 3) final answer generation.
> </details>





{{< table-caption >}}
| ![https://arxiv.org/html/2412.18702/figures/logos/hf-logo.png](https://arxiv.org/html/2412.18702/figures/logos/hf-logo.png) **Dataset** | [https://huggingface.co/datasets/megagonlabs/cypherbench](https://huggingface.co/datasets/megagonlabs/cypherbench) |
| ![https://arxiv.org/html/2412.18702/figures/logos/github-mark.png](https://arxiv.org/html/2412.18702/figures/logos/github-mark.png) **Code** | [https://github.com/megagonlabs/cypherbench](https://github.com/megagonlabs/cypherbench) |{{< /table-caption >}}

> 🔼 표 1은 다양한 유형의 질의에 대한 그래프 패턴과 질의 예시를 보여줍니다. 기본적인 MATCH 패턴, 특수한 MATCH 패턴, 그리고 RETURN 템플릿을 포함하고 있으며, 보라색 노드는 답변 엔티티를 나타냅니다. 정사각형 노드는 특정 유형의 모든 엔티티를 나타내고, 원형 노드는 명명된 엔티티를 나타냅니다. 점선으로 표시된 노드와 에지는 선택적입니다. 표 11과 표 12에는 전체 패턴 목록이 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1:  A basic MATCH pattern, a special MATCH pattern, and a RETURN template, along with sample questions. The nodes in purple denote the answer entities. Square nodes () denote all entities of a particular type, while circular nodes () represent named entities. Nodes and edges with dashed lines () are optional. The complete list of patterns are provided in Table 11 and Table 12.
> </details>





### In-depth insights


#### LLM-KG Retrieval
LLM-KG 검색은 **대규모 언어 모델(LLM)**과 **지식 그래프(KG)**를 결합하여 정보 검색의 새로운 가능성을 제시하는 분야입니다. 기존의 검색 방식과 달리, LLM-KG 검색은 KG의 구조화된 지식을 활용하여 LLM의 자연어 이해 능력을 보완함으로써 더욱 정확하고 심층적인 검색 결과를 제공합니다. **LLM의 강력한 자연어 처리 능력**은 사용자의 질문 의도를 정확하게 파악하고, KG의 구조화된 정보는 질문에 대한 답변을 효율적으로 찾아낼 수 있도록 돕습니다.  하지만, **LLM의 제한적인 컨텍스트 창 크기**와 **KG의 복잡한 스키마**는 LLM-KG 검색의 성능을 저해하는 주요 과제입니다. 따라서, 효율적인 지식 표현 방식과 질문 응답 전략의 개발이 매우 중요합니다.  **지식 그래프의 효율적인 질의 처리**를 위한 기술 발전과 **LLM의 컨텍스트 창 한계를 극복**하기 위한 연구가 지속적으로 필요합니다. 또한, **다양한 도메인의 지식 그래프**를 활용한 실험과 평가를 통해 LLM-KG 검색의 실용성과 확장성을 검증하는 노력도 중요합니다. 이러한 과제들을 해결하기 위한 다양한 연구가 진행 중이며, 향후 LLM-KG 검색 기술은 더욱 발전하여 정보 검색 분야에 혁신적인 변화를 가져올 것으로 예상됩니다.  **특히, 개인정보보호 및 윤리적 문제**에 대한 고려도 중요한 요소입니다.

#### RDF to Property
본 논문에서 제시된 "RDF에서 속성 그래프로"의 개념은 **대규모 지식 그래프의 효율적인 쿼리 처리를 위한 핵심 전략**입니다.  RDF는 표준화되지 않은 스키마, 중복되는 관계형, 자원 식별자 사용 등의 이유로 LLM 기반 질의응답 시스템에 비효율적입니다.  **RDF를 여러 개의 더 작고 특정 도메인에 집중된 속성 그래프로 변환**함으로써, LLM의 제한된 컨텍스트 창 문제를 해결하고 Cypher와 같은 효율적인 쿼리 언어를 사용할 수 있게 합니다.  이러한 변환 과정에는 **도메인별 스키마 생성, 데이터 유형 변환, 단위 표준화** 등의 과정이 포함되며, Wikidata를 기반으로 한 CypherBench 벤치마크는 이러한 접근 방식의 효과를 보여줍니다. **속성 그래프는 LLM 기반 RAG 시스템에서 효율적인 지식 검색을 위한 실용적인 해결책**을 제공하지만, 변환 과정의 복잡성과 스키마 관리의 어려움은 여전히 과제로 남아있습니다.  **본 연구는 대규모 RDF 지식 그래프의 효율적 활용**에 대한 중요한 시사점을 제공하며, 향후 연구는 변환 과정의 자동화 및 최적화에 초점을 맞춰야 합니다.

#### CypherBench
CypherBench는 **현대적인 지식 그래프에서 효율적이고 정확한 텍스트-Cypher 검색을 가능하게 하는 새로운 벤치마크**입니다. 기존의 지식 그래프 질의응답(KBQA) 방법론의 한계를 극복하기 위해 **RDF 기반 지식 그래프를 여러 개의 더 작고 효율적인 속성 그래프로 변환**하는 새로운 방법론을 제시합니다. 이는 LLMs의 제한된 컨텍스트 창 크기 및 RDF 스키마의 복잡성 문제를 해결하는 데 도움이 됩니다.  **Wikidata를 기반으로 구축된 11개의 대규모 다중 도메인 속성 그래프와 10,000개 이상의 질문**으로 구성되어 있으며,  **전통적인 KBQA 벤치마크에서는 간과되었던 전역 질의(global queries)**를 포함하여 다양한 그래프 매칭 패턴을 다룹니다.  **Cypher 언어를 사용하여 효율적인 질의가 가능**하도록 설계되었으며, 이를 통해 LLMs가 현대적인 지식 그래프를 활용하여 더 정확하고 효율적으로 질문에 답할 수 있도록 지원합니다.  **정확도와 효율성을 측정하기 위한 새로운 평가 지표**도 제시하여,  LLM 기반 지식 그래프 검색 기술의 발전에 크게 기여할 것으로 기대됩니다.  **개방형 접근 방식**을 통해  연구자들은 이를 활용하여  LLM 기반 지식 그래프 검색 기술을 더욱 발전시킬 수 있습니다.

#### Benchmarking LLMs
본 논문에서는 대규모 언어 모델(LLM)을 벤치마킹하는 방법에 대한 심도있는 논의가 부족합니다. 하지만, **CypherBench라는 새로운 벤치마크를 제시하여 다양한 도메인의 대규모 속성 그래프를 사용한 정확한 검색을 평가**합니다.  이는 기존의 LLM 프레임워크들이 Wikidata와 같은 현대적인 지식 그래프로부터 검색하는 기능이 부족하다는 점을 고려할 때 매우 중요합니다. CypherBench는 **LLM의 맥락 창 크기보다 훨씬 큰 스키마를 가진 현대적인 RDF 지식 그래프의 비효율성 문제를 해결하기 위해 Cypher를 사용한 속성 그래프 뷰를 제안**합니다.  **다양한 규모와 복잡도의 질문들을 포함하여 실제 환경을 더 잘 반영**하고, **기존 KBQA 벤치마크에서 간과되었던 글로벌 질문 유형도 포함**하여 LLM의 성능을 종합적으로 평가합니다. 이러한 벤치마크는 **LLM의 그래프 검색 능력을 평가하는 표준적인 방법론을 제공**하며, **향후 LLM 기반 RAG(Retrieval-Augmented Generation) 시스템의 발전에 중요한 역할**을 할 것으로 예상됩니다.  **다만, 벤치마킹에 사용된 모델의 종류 및 상세 사양, 그리고 평가 지표의 한계점에 대한 논의가 추가**된다면 더욱 완성도 높은 연구가 될 것입니다.

#### Future Work
본 논문은 Wikidata 기반의 대규모 지식 그래프에서 효율적이고 정확한 텍스트-Cypher 검색을 가능하게 하는 새로운 방법론을 제시합니다. **향후 연구 방향으로는 먼저, 더욱 다양하고 복잡한 질문 유형을 포함하는 CypherBench 벤치마크의 확장이 필요합니다.**  다양한 도메인과 복잡한 질의 패턴을 포함하여 LLMs의 일반화 능력을 더욱 엄격하게 평가해야 합니다. 또한, **개선된 엔티티 연결(entity linking) 기법을 통해 질문의 의미를 더욱 정확하게 파악하고, 그에 따른 정확한 Cypher 쿼리를 생성하는 연구가 필요합니다.**  현재 벤치마크는 엔티티 이름을 직접 사용하지만, 실제 환경에서는 엔티티 연결이 필수적이기 때문입니다.  마지막으로, **다양한 크기와 성능의 LLMs에 대한 벤치마크 결과 분석을 통해, LLM의 크기와 성능 사이의 관계를 보다 명확히 규명할 필요가 있습니다.**  이를 통해, 특정 작업에 최적화된 LLM의 크기를 결정하고, 자원 사용을 효율적으로 관리하는 데 도움이 될 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.18702/x2.png)

> 🔼 그림 2는 CypherBench의 생성 과정을 보여줍니다. Wikidata는 스키마 기반 속성 그래프로 변환되며, 이를 통해 효율적이고 정확한 text-to-Cypher 쿼리 생성이 가능해집니다. 생성된 속성 그래프는 text-to-Cypher 작업 생성에 사용됩니다.  즉, Wikidata의 복잡한 데이터를 LLM이 효율적으로 처리할 수 있도록 단순화하고, Cypher라는 질의어를 사용하여 LLM이 Wikidata에 대한 질의를 효과적으로 수행할 수 있도록 하는 과정을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: CypherBench construction process: Wikidata is transformed into schema-enforced property graphs, which enables efficient and accurate text-to-Cypher querying. These property graphs are then used to generate text-to-Cypher tasks.
> </details>



![](https://arxiv.org/html/2412.18702/x3.png)

> 🔼 그림 3은 회사(company) 도메인에 대한 속성 그래프 스키마를 보여줍니다. 이 스키마는 회사, 국가, 산업 및 개인과 같은 엔티티 유형과 이러한 엔티티 유형 간의 관계(relation) 유형을 정의합니다. 각 엔티티 및 관계 유형에는 해당 속성(property)이 포함될 수 있습니다. 예를 들어 회사는 설립연도(launch_year)와 이름(name)과 같은 속성을 가지며, 개인은 출생지(place_of_birth), 시민권 국가 목록(country_of_citizenship) 및 이름(name)과 같은 속성을 가집니다. 또한, 회사와 개인, 국가 및 산업 사이의 다양한 관계가 표시됩니다. 논문의 부록 B에는 다른 그래프의 스키마가 나와 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3:  Schema of the company graph with entity properties an relation properties. See Appendix B for other graphs.
> </details>



![](https://arxiv.org/html/2412.18702/extracted/6093954/figures/question_distribution.png)

> 🔼 그림 4는 CypherBench 테스트 세트에 있는 그래프 매칭 패턴, RETURN 템플릿, 도메인 및 답변 길이(답변의 행 수)의 분포를 보여줍니다.  각각의 카테고리별 데이터 분포를 시각적으로 나타내어 CypherBench 테스트 세트의 다양성과 균형을 보여줍니다.  이를 통해, CypherBench가 다양한 유형의 질문과 그래프 구조를 포함하고 있음을 알 수 있습니다.  각 차트는 해당 카테고리의 상대적 비율을 보여주는 파이 차트 또는 막대 차트의 형태로 나타내어, 데이터 분포를 명확하게 이해하도록 돕습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Distribution of graph matching patterns, RETURN templates, domains, and answer lengths (number of rows in the answer) in the CypherBench test set.
> </details>



![](https://arxiv.org/html/2412.18702/extracted/6093954/figures/radar.png)

> 🔼 그림 5는 다양한 그래프 매칭 패턴, RETURN 템플릿 및 도메인에 걸친 성능을 보여줍니다. 기본 및 특수 MATCH 패턴에 대한 정확도와 PSJS 점수를 비교하여 그래프 매칭의 어려움을 보여줍니다. RETURN 템플릿에 따른 정확도를 분석하여 모델별로 다른 약점을 보여줍니다. 마지막으로, 다양한 도메인에서 모델의 정확도를 보여주고 그래프의 복잡성이 정확도에 미치는 영향을 평가합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Performance across basic and special MATCH patterns, RETURN templates and domains.
> </details>



![](https://arxiv.org/html/2412.18702/extracted/6093954/figures/error_distribution.png)

> 🔼 그림 6은 무작위로 선택된 50개의 잘못된 예측에 대해 gpt-40 및 llama3.1-8b 모델이 생성한 오류의 분포를 보여줍니다. 각 모델은 50개의 잘못된 예측에 대해 평가되었으며, 각 예측은 여러 오류를 포함할 수 있습니다.  즉, 하나의 예측에 여러 오류 유형이 동시에 나타날 수 있다는 것을 의미합니다. 이 그림은 각 모델의 오류 유형별 발생 빈도를 시각적으로 보여주어, 두 모델의 오류 패턴을 비교 분석하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Distribution of errors made by gpt-4o and llama3.1-8b on 50 randomly sampled incorrect predictions. Note that a model might make multiple errors on one instance.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Pattern/Template | Sample Question | Cypher Query |
|---|---|---|
| <img src="https://arxiv.org/html/2412.18702/figures/match_patterns/basic_1.png" width="16" height="16"> (Basic MATCH) | Q1. What are the names of terrorist attacks that occurred before March 13th, 1997?  ( _terrorist attack_ ) | ⬇ MATCH (n:TerroristAttack) WITH DISTINCT n WHERE n.date < date('1997-03-13') RETURN n.name |
| <img src="https://arxiv.org/html/2412.18702/figures/match_patterns/optional.png" width="68" height="16"> Optional Match (Special MATCH) | Q10. Provide the names of all aircraft models manufactured by ATR, along with the number of flight accidents each has been involved in.  ( _flight accident_ ) | ⬇ MATCH (n:AircraftModel)-[r1:manufacturedBy]->(m1:AircraftManufacturer {name: 'ATR'}) OPTIONAL MATCH (n:AircraftModel)<-[r0:involves]-(m0:FlightAccident) WITH n, count(DISTINCT m0) AS num RETURN n.name, num |
| AGGREGATE (RETURN Template) | Q18. What is the average longest lifespan of taxa that feed on Leporidae?  ( _biology_ ) | ⬇ MATCH (n:Taxon)-[r0:feedsOn]->(m0:Taxon {name: 'Leporidae'}) WITH DISTINCT n RETURN avg(n.longest_lifespan_years) |{{< /table-caption >}}
> 🔼 표 2는 CypherBench 데이터셋의 훈련 및 테스트 분할 통계를 보여줍니다. 훈련 세트에는 4개의 그래프가 포함되어 있으며, 테스트 세트에는 7개의 그래프가 포함되어 있습니다. 각 그래프는 특정 도메인을 다루며, 테스트 세트는 전체 데이터셋의 4개 그래프로 구성되어 있습니다. 각 그래프의 질문 수, 도메인 및 답변 길이 분포를 보여주는 추가적인 정보가 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2:  Statistics of the data splits.
> </details>

{{< table-caption >}}
| Split | Graphs | #question |
|---|---|---|
| Train | art, biology, soccer, terrorist attack | 8817 |
| Test | company, fictional character, flight accident, geography, movie, nba, politics | 2488 |{{< /table-caption >}}
> 🔼 표 3은 CypherBench 테스트 세트에서 제로샷 실행 정확도(EX), 출처 서브그래프 자카드 유사도(PSJS), 및 실행 가능한 비율(Exec.)을 보여줍니다.  EX는 예측된 쿼리의 결과가 실제 쿼리의 결과와 일치하는지 측정하는 지표입니다. PSJS는 MATCH 절에 의해 일치된 서브그래프를 비교하여 그래프 일치 성능을 측정합니다.  실행 가능한 비율은 성공적으로 실행된 쿼리의 비율을 나타냅니다. 이 표는 다양한 크기의 여러 LLM(Large Language Model)의 성능을 비교하여 CypherBench의 난이도와 LLM의 그래프 질의 능력에 대한 통찰력을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Zero-shot execution accuracy (EX), provenance subgraph jaccard similarity (PSJS) and executable percentage (Exec.) on the CypherBench test set.
> </details>

{{< table-caption >}}
| Model | EX (%) | PSJS (%) | Exec. (%) |
|---|---|---|---|
| *Open-source LLMs (<10B)* |  |  |  |
| `llama3.2-3b` | 11.20 | 17.33 | 86.46 |
| `llama3.1-8b` | 18.82 | 30.98 | 90.67 |
| `gemma2-9b` | 18.61 | 30.67 | 68.57 |
| *Open-source LLMs (10-100B)* |  |  |  |
| `mixtral-8x7b` | 19.21 | 37.01 | 59.33 |
| `qwen2.5-72b` | 41.87 | 56.39 | 86.84 |
| `llama3.1-70b` | 38.84 | 54.79 | 92.25 |
| *Proprietary LLMs* |  |  |  |
| `yi-large` | 33.82 | 47.21 | 83.52 |
| `gemini1.5-flash-001` | 25.26 | 41.46 | 83.65 |
| `gemini1.5-pro-001` | 39.95 | 57.70 | 86.03 |
| `gpt-4o-mini-20240718` | 31.43 | 45.91 | 87.39 |
| `gpt-4o-20240806` | 60.18 | 76.87 | 94.93 |
| `claude3.5-sonnet-20240620` | **61.58** | **80.85** | **96.34** |{{< /table-caption >}}
> 🔼 표 4는 질문에 대한 gpt-4o와 llama3.1-8b의 예측 결과를 보여줍니다. 각 예측에는 오류 범주가 함께 주석으로 달려 있습니다. 이 표는 모델이 질문에 답변하는 과정에서 어떤 유형의 오류를 범하는지 보여주는 사례를 제시하며,  오류 분석(Error Analysis) 부분에서 언급되는 다양한 오류 유형(예: 구문 오류, 잘못된 엔티티/관계/속성 유형, 반전된 방향, 스키마 위반, 질문과 정렬되지 않은 패턴, 잘못된 그룹화, 엔티티 연결, 잘못된 필터링, 질문과 정렬되지 않은 결과, 잘못된 중복 제거 등)을 보여주는 구체적인 예시입니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Sample predictions of gpt-4o and llama3.1-8b with annotated error categories.
> </details>

{{< table-caption >}}
| Question | Ground-truth Cypher | Predicted Cypher & Errors |
|---|---|---|
| What are the names of lakes situated in countries through which the Natara River flows, with an area of less than 390,000 square kilometers? (geography) | MATCH (n:Lake)-[r0:locatedIn]->(m0:Country)<-[r1:flowsThrough]-(m1:River {name: 'Natara'}) WITH DISTINCT n WHERE n.area_km2 < 390000 RETURN n.name | MATCH (r:River {name: 'Natara River'})-[ :flowsThrough]->(c:Country)<-[ :locatedIn]-(l:Lake) WHERE l.area_km2 < 390000 RETURN DISTINCT l.name ■ Entity Linking: 'Natara River' does not exist ■ Incorrect Deduplication: Distinct rivers with the same name should not be merged (gpt-4o) |
| What are the names of film series that include movies originating from the Czech Republic? (movie) | MATCH (n:FilmSeries)<-[r0:partOfSeries]-(m0:Movie)-[r1:originatesFrom]->(m1:Country {name: 'Czech Republic'}) WITH DISTINCT n RETURN n.name | MATCH (m:Movie)-[:originatesFrom]->(c:Country {name: 'Czech Republic'})-[:partOfSeries]->(fs:FilmSeries) RETURN DISTINCT fs.name ■ Schema violation: partOfSeries between Country and FilmSeries is invalid (llama3.1-8b) |{{< /table-caption >}}
> 🔼 본 표는 기존 연구 논문과 오픈소스 프로젝트에서 사용된 그래프 검색 방법들을 분류하고 요약하여 보여줍니다.  표에는 근사 검색 방법과 정밀 검색 방법의 두 가지 주요 범주가 있으며, 각 범주 내에는 여러 하위 범주와 각 방법을 채택한 대표적인 연구 논문 및 오픈소스 프로젝트들이 포함되어 있습니다. 이를 통해, 그래프 데이터에서 정보를 검색하는 다양한 접근 방식을 종합적으로 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Graph retrieval methods adopted by existing research papers and open-source projects.
> </details>

{{< table-caption >}}
| Graph Retrieval Method | Papers / Open-source Projects |
|---|---| 
| *Approximate Retrieval* |  | 
| Entity linking + k-hop neighbourhood |  <img src="https://arxiv.org/html/2412.18702/figures/logos/LlamaLogoBrowserTab.png" width="13" height="13"> LlamaIndex [31], MCCNN [32], UniK-QA [33], CLOCQ [34], Convinse [35], Explaignn [36], Temple-MQA [37], Subgraph Retriever [38], QA-GNN [39], MHGRN [40], RoG [23], UniKGQA [25] |
| Top-k entities / relations / pseudo-doc | STaRK [41], DiFaR [13], UDT-QA [42], DecAF [24] |
| *Precise Retrieval* |  | 
| Text-to-SPARQL through intermediate logical form (e.g., λ-DCS, S-expression, etc.)  | S-expression [6], λ-DCS [3, 26], ComplexWebQ [43], Staged Query Graph [27], Graph Query [29], Abstract Query Graph [44], KoPL [7], GraphQ IR [15], KB-BINDER [28] |
| Text-to-SPARQL | <img src="https://arxiv.org/html/2412.18702/figures/logos/langchain-removebg-preview.png" width="21" height="12"> Langchain [45], sparqlgen [17], T5-sparql [18], sparql-llm [14], SPARKLE [46] |
| Text-to-Cypher (Our focus) | <img src="https://arxiv.org/html/2412.18702/figures/logos/LlamaLogoBrowserTab.png" width="13" height="13"> LlamaIndex [31], <img src="https://arxiv.org/html/2412.18702/figures/logos/langchain-removebg-preview.png" width="21" height="12"> Langchain [45], UniOQA [47] |{{< /table-caption >}}
> 🔼 표 6은 대표적인 텍스트-쿼리 벤치마크에 대한 비교를 보여줍니다. †† 표시가 된 벤치마크는 비영어권 언어(R3-NL2GQL, FinGQL, MediGQL, SpCQL은 중국어)이며,  'LLM 효율적?' 열은 벤치마크의 데이터베이스 스키마가 일반적인 LLMs의 컨텍스트 창에 맞는지 여부를 나타냅니다. 기존 KBQA 벤치마크는 RDF 지식 그래프의 방대한 스키마로 인해 제로샷 환경에서 LLMs를 평가하는 데 어려움을 야기합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Comparison of representative text-to-query benchmarks. Benchmarks marked by ††\dagger† are non-English (R3superscript𝑅3R^{3}italic_R start_POSTSUPERSCRIPT 3 end_POSTSUPERSCRIPT-NL2GQL, FinGQL, MediGQL and spQCL are in Chinese). The column “LLM Efficient?” refers to whether the database schema from the benchmark can fit in the typical context window of LLMs. Existing KBQA benchmarks pose challenges for evaluation in zero-shot settings with LLMs due to the massive schema of RDF knowledge graphs.
> </details>

{{< table-caption >}}
| Benchmark | Data Source | #graph/db | Avg. Schema Size (per graph/db) | Data Size | LLM Efficient? |
|---|---|---|---|---|---| 
| Text-to-SQL / relational data |  |  |  |  |  |
| Spider [30] | Wikipedia, etc. | 200 | 5.1 tables, 27.6 columns | 400k rows | ✓ |
| BIRD-SQL [48] | Kaggle, etc. | 95 | 7.3 tables, 54.2 columns | 52M rows | ✓ |
| Text-to-SPARQL / RDF graphs |  |  |  |  |  |
| LC-Quad 2.0 [5] | Wikidata | 1 | 12k relation types | 114M entities | × |
| GrailQA [6] | Freebase | 1 | 37k relation types | 45M entities | × |
| KQA Pro [7] | FB15k-237 | 1 | 0.8k relation types | 16k entities | × |
| Text-to-nGQL / property graphs |  |  |  |  |  |
| R<sup>3</sup>-NL2GQL<sup>†</sup> [49] | OpenKG | 3 | 5.3 relation types, 13 properties | 46k entities | ✓ |
| Fin/Medi-GQL<sup>†</sup> [50] | OpenKG | 2 | 13 relation types, 38 properties | 713k entities | ✓ |
| Text-to-Cypher / property graphs |  |  |  |  |  |
| MetaQA-Cypher [15] | OMDb | 1 | 5 relation types, 5 properties | 43k entities | ✓ |
| SpCQL<sup>†</sup> [51] | OwnThink | 1 | 480k relation types, 1 property | 16M entities | × |
| Neo4j Text2Cypher (2024) | neo4j-graph-examples | - | - | - | ✓ |
| CypherBench (ours) | Wikidata | 11 | 7.5 relation types, 18.7 properties | 7.8M entities | ✓ |{{< /table-caption >}}
> 🔼 표 7은 기존 질의응답 데이터셋에서 다루는 그래프 매칭 패턴을 보여줍니다. 여기에는 단일 홉 지식 집약적 텍스트 QA 데이터셋인 Natural Questions [52] 와 다중 홉 지식 집약적 텍스트 QA 데이터셋인 HotpotQA [53] 가 포함됩니다. 본 논문에서 설명된 질의 큐레이션 기법과 무작위로 추출한 100개의 질문을 바탕으로 패턴을 도출했습니다. 표는 다양한 질의응답 데이터셋에서 사용되는 그래프 매칭 패턴의 유형과 빈도를 비교하여, CypherBench 데이터셋이 기존 데이터셋보다 다양한 유형의 패턴을 포함하고 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 7:  Graph matching patterns covered by previous question answering datasets. We also include Natural Questions [52] and HotpotQA [53] as representative knowledge-intensive single-hop and multi-hop text QA datasets here. We determined the patterns based on the question curation approach described in the paper and 100 randomly sampled questions.
> </details>

{{< table-caption >}}
|   | Natural Questions (single-hop Text QA) | HotpotQA (multi-hop Text QA) | KQA Pro (text-to-SPARQL) | MetaQA-Cypher (text-to-Cypher) |
|---|---|---|---|---|
| **CypherBench Basic Graph Patterns** |  |  |  |  |
| <img src="https://arxiv.org/html/2412.18702/figures/match_patterns/basic_1.png" width="16" height="16"> |  |  |  |  |
| <img src="https://arxiv.org/html/2412.18702/figures/match_patterns/basic_2.png" width="16" height="16"> | ✓ |  | ✓ | ✓ |
| <img src="https://arxiv.org/html/2412.18702/figures/match_patterns/basic_3.png" width="42" height="16"> |  |  |  |  |
| <img src="https://arxiv.org/html/2412.18702/figures/match_patterns/basic_4.png" width="42" height="16"> | ✓ | ✓ | ✓ | ✓ |
| <img src="https://arxiv.org/html/2412.18702/figures/match_patterns/basic_5.png" width="68" height="16"> |  | ✓ | ✓ |  |
| <img src="https://arxiv.org/html/2412.18702/figures/match_patterns/basic_6.png" width="68" height="16"> |  |  |  |  |
| <img src="https://arxiv.org/html/2412.18702/figures/match_patterns/basic_7.png" width="42" height="16"> |  |  |  |  |
| **CypherBench Special Graph Patterns** |  |  |  |  |
| <img src="https://arxiv.org/html/2412.18702/figures/match_patterns/comparison.png" width="42" height="16"> |  | ✓ | ✓ |  |
| <img src="https://arxiv.org/html/2412.18702/figures/match_patterns/group.png" width="68" height="16"> |  |  |  |  |
| <img src="https://arxiv.org/html/2412.18702/figures/match_patterns/optional.png" width="68" height="16"> |  |  |  |  |
| <img src="https://arxiv.org/html/2412.18702/figures/match_patterns/time.png" width="42" height="16"> |  |  | ✓ |  |
| <img src="https://arxiv.org/html/2412.18702/figures/match_patterns/union.png" width="93" height="16"> |  |  |  |  |{{< /table-caption >}}
> 🔼 표 8은 CypherBench 벤치마크에 사용된 11개 속성 그래프의 통계를 보여줍니다. 각 그래프의 엔티티, 관계, 엔티티 유형, 관계 유형 및 속성 수가 나와 있습니다. 또한, 각 그래프의 엔티티 중 몇 개가 영어 위키피디아 문서와 연결되어 있는지 (대략 위키피디아 문서와 연결된 엔티티 수)를 나타내는 위키피디아 열도 포함되어 있습니다. 이는 각 그래프의 규모와 범위를 보다 잘 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 8:  Statistics of the graphs. Wikipedia refers to the number of English Wikipedia articles linked from the entities (roughly the number of entities with Wikipedia articles).
> </details>

{{< table-caption >}}
| Graph | Ent. | Rel. | Ent. Types | Rel. Types | Properties | Wikipedia |
|---|---|---|---|---|---|---|
| _art_ | 1.1M | 1.3M | 6 | 8 | 16 | 64.9k |
| _biology_ | 3.7M | 7.5M | 4 | 5 | 8 | 447.7k |
| _company_ | 581.3k | 299.6k | 4 | 6 | 14 | 166.3k |
| _fictional character_ | 28.9k | 40.5k | 4 | 11 | 12 | 8.5k |
| _flight accident_ | 1.7k | 2.2k | 5 | 5 | 25 | 1.6k |
| _geography_ | 773.5k | 903.8k | 8 | 12 | 19 | 73.1k |
| _movie_ | 459.4k | 1.9M | 7 | 9 | 21 | 262.2k |
| _nba_ | 4.3k | 19.0k | 7 | 7 | 27 | 4.3k |
| _politics_ | 885.2k | 1.5M | 6 | 11 | 25 | 414.2k |
| _soccer_ | 275.2k | 1.1M | 6 | 5 | 26 | 206.6k |
| _terrorist attack_ | 1.6k | 1.5k | 5 | 4 | 13 | 1.3k |
| Total | 7.8M | 14.7M | 62 | 83 | 206 | 1.7M |{{< /table-caption >}}
> 🔼 표 9는 질문 재작성 프롬프트의 예시를 보여줍니다.  LLM이 생성한 템플릿 질문을 보다 자연스러운 질문으로 바꾸는 방법을 설명합니다.  여기에는 관계 패턴의 방향, 관계와 속성의 자연어 표현, 수량값과 날짜의 다양한 표현, 연산자와 정렬의 자연어 표현 등이 포함되어 있어 LLM이 더 정확하고 자연스러운 질문을 생성하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 9: A sample question rewriting prompt.
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