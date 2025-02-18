---
title: "CLaMP 3: Universal Music Information Retrieval Across Unaligned Modalities and Unseen Languages"
summary: "CLAMP 3: 여러 언어와 모달리티를 지원하는 범용 음악 정보 검색 프레임워크"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Cross-Modal Retrieval", "🏢 Tsinghua University",]
showSummary: true
date: 2025-02-14
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.10362 {{< /keyword >}}
{{< keyword icon="writer" >}} Shangda Wu et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-17 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.10362" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.10362" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

음악 정보 검색(MIR) 분야는 **다양한 언어와 모달리티(악보, 연주, 오디오)**를 다루는 데 어려움을 겪고 있습니다. 기존 연구는 특정 모달리티 쌍에만 초점을 맞춰 **범용성이 부족**하고, 주로 영어 데이터에 의존하여 **다국어 지원이 미흡**했습니다. 또한, 짝지어진 학습 데이터의 부족으로 **모달리티 간 정렬**이 어려웠습니다.

본 논문에서는 이러한 문제를 해결하기 위해 **CLAMP 3**이라는 통합 프레임워크를 제시합니다. CLAMP 3는 대규모 다국어 음악-텍스트 데이터셋(M4-RAG)과 벤치마크(WikiMT-X)를 활용하여 **다양한 모달리티와 언어 간의 정렬**을 수행합니다. **대조 학습**을 통해 다양한 음악 모달리티와 다국어 텍스트를 공유된 표현 공간에 매핑하여 **모달리티 간 검색**을 가능하게 합니다. 실험 결과, CLAMP 3는 기존 방법들을 상당히 능가하는 성능을 보였으며, 다국어 및 다모달 상황에서 뛰어난 일반화 능력을 입증했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} CLAMP 3는 다양한 언어와 모달리티(악보, 연주 신호, 오디오)를 지원하는 통합 음악 정보 검색 프레임워크를 제시합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 대규모 다국어 음악-텍스트 데이터셋(M4-RAG)과 벤치마크(WikiMT-X)를 공개하여 향후 연구를 위한 기반을 마련했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 다양한 음악 정보 검색 작업에서 최첨단 성능을 달성하여, 다국어 및 다모달 상황에서 우수한 일반화 능력을 보여주었습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **다양한 언어와 모달리티를 포괄하는 음악 정보 검색 분야**에 중요한 기여를 합니다. 제시된 통합 프레임워크와 대규모 데이터셋은 **향후 연구의 기반**을 마련하고, **새로운 연구 방향**을 제시합니다. **다국어 지원 및 다양한 음악 형식 지원**은 특히 중요하며, 음악 정보 검색 기술의 글로벌화 및 접근성 향상에 기여할 것입니다. 또한, 본 연구는 **모달리티 간의 상호 작용**에 대한 이해를 깊게 하고, **다양한 음악 관련 응용 분야**에 활용될 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.10362/x1.png)

> 🔼 그림 1은 CLAMP 3 모델의 핵심적인 기능인 다중 모드 및 다국어 일반화 능력을 보여줍니다.  기존의 지도 학습 방식(실선 화살표)은 음악 악보, 연주 신호, 오디오 레코딩과 같은 다양한 음악 모드를 각각 다국어 텍스트와 연결하여 표현 공간에서 정렬합니다.  하지만 CLAMP 3는 여기서 더 나아가 지도 학습 없이도 서로 다른 음악 모드들을 연결하는 잠재적 정렬(점선 화살표)을 가능하게 합니다.  다국어 텍스트 인코더는 이러한 연결 과정의 중심 역할을 수행하며, 학습 과정에서 보지 못한 언어(회색 음영 처리된 원)에 대해서도 검색 기능을 지원합니다. 즉, 다양한 언어와 형태의 음악 정보를 텍스트를 매개로 효과적으로 연결하고 검색할 수 있음을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: CLaMP 3 demonstrates robust cross-modal and cross-lingual generalization. Supervised alignment (solid arrows) links paired modalities, while emergent alignment (dashed arrows) bridges unaligned ones. A multilingual text encoder enables retrieval in languages unseen (grayed-out bubbles) during alignment.
> </details>





{{< table-caption >}}
| Category | Field | Content | Avg Bytes |
|---|---|---|---| 
| **Basic** | _Title_ | Music Title | 20.04 |
|  | _Artists_ | Artist names | 21.97 |
| **Annotations** | _Region_ | Country of origin | 20.69 |
|  | _Language_ | Document language | 7.02 |
|  | _Genres_ | Genre list | 21.83 |
|  | _Tags_ | Keywords/playlists | 51.91 |
|  | _Background_ | Background context | 531.79 |
|  | _Analysis_ | Musical analysis | 770.29 |
|  | _Description_ | General description | 591.86 |
|  | _Scene_ | Scene depiction | 750.92 |
| **Translations** | _Language_ | Translation language | 6.38 |
|  | _Background_ | Translated background | 819.76 |
|  | _Analysis_ | Translated analysis | 1130.47 |
|  | _Description_ | Translated description | 888.86 |
|  | _Scene_ | Translated scene | 1077.07 |{{< /table-caption >}}

> 🔼 표 1은 M4-RAG 데이터셋의 메타데이터 개요를 보여줍니다. 기본 정보, 주석 및 번역의 세 가지 범주로 그룹화되어 있습니다. 주석 범주에서는 지역 및 언어 필드가 영어로 작성되고 다른 필드는 언어 사양을 따릅니다. 이 표는 각 필드의 내용과 평균 바이트 크기를 보여주어 데이터셋의 다양성과 풍부함을 보여줍니다.  데이터셋의 규모, 다양성 및 언어 분포에 대한 통계를 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Metadata overview for M4-RAG, grouped into basic information, annotations, and translations. In Annotations, Region and Language are written in English; other fields follow the Language specification.
> </details>





### In-depth insights


#### Cross-Modal Alignment
본 논문에서 **다양한 모달리티 간의 정렬(Cross-Modal Alignment)**은 음악 정보 검색(MIR) 시스템의 핵심 과제로 제시됩니다.  **텍스트, 악보, 오디오, 연주 신호** 등 서로 다른 형태의 음악 데이터를 통합된 표현 공간에 매핑하여 상호 참조 및 검색을 가능하게 합니다.  **대조 학습(Contrastive Learning)** 기법을 통해 각 모달리티의 특징을 추출하고, **텍스트를 중개자(bridge)** 로 활용하여 서로 다른 모달리티 간의 연관성을 학습합니다.  **정렬 과정**은 단순히 쌍으로 된 데이터를 일치시키는 것을 넘어, **정렬되지 않은 데이터 간의 관계를 추론하는 emergent alignment** 까지 고려합니다.  이러한 과정을 통해 **언어 간 장벽**을 넘어 **다국어 지원**이 가능해지고, **새로운 언어**에 대한 적응력 또한 향상됩니다.  결과적으로 **모달리티와 언어 간 일반화 성능**이 뛰어난 강력한 MIR 시스템을 구축하는 데 중요한 역할을 합니다.  특히, **부족한 쌍으로 된 데이터** 문제를 해결하기 위해 **Retrieval-Augmented Generation(RAG)** 기법을 사용하여 대규모의 음악-텍스트 데이터셋을 구축하는 것 또한 **Cross-Modal Alignment** 전략의 중요한 부분입니다.

#### M4-RAG Dataset
M4-RAG 데이터셋은 **다양한 언어와 문화권을 아우르는 방대한 규모의 음악-텍스트 데이터셋**입니다. 기존 음악 정보 검색(MIR) 연구의 주요 제약 중 하나였던 **데이터 부족 문제를 해결하기 위해 등장**했습니다.  **231만 개의 음악-텍스트 쌍**을 포함하며, **곡 제목, 아티스트명과 같은 기본 메타데이터뿐만 아니라, 장르, 태그, 다국어 번역을 포함한 상세한 설명까지 풍부한 정보**를 담고 있습니다.  이러한 다양한 정보는 **대규모 언어 모델(LLM)을 활용한 검색어 생성 과정**을 통해 수집되었으며, **전 세계 다양한 음악적 전통을 반영**하고 있습니다. **27개 언어와 194개 국가의 음악**을 포함하는 M4-RAG는 **다국어 및 다모달 음악 정보 검색 시스템 개발을 위한 중요한 자원**이며, **CLAMP 3 모델의 성능 향상**에 크게 기여했습니다.  **다양한 언어와 모달리티(sheet music, performance signals, audio recordings)를 포괄하는 특징**은 기존 연구의 한계를 뛰어넘는 핵심적 가치를 제공합니다.  **특히, 기존 연구에서 부족했던 장문의 설명 데이터를 포함**하여, 더욱 풍부한 의미 정보를 담고 있다는 점이 중요한 강점입니다.

#### Multilingual MIR
다국어 MIR은 음악 정보 검색 분야에서 **언어 장벽을 극복**하고 전 세계의 다양한 문화적, 언어적 배경을 가진 음악을 포괄적으로 접근하는 데 중점을 둡니다. 이는 단순히 다양한 언어로 된 텍스트 질의를 처리하는 것을 넘어, **다양한 언어의 음악 관련 텍스트와 비텍스트 모달리티(예: 악보, 오디오)**를 통합적으로 이해하고 상호 연관짓는 것을 의미합니다.  **대규모 언어 모델(LLM)**의 발전은 다국어 MIR 시스템 구축에 중요한 역할을 합니다.  LLM은 다양한 언어의 텍스트를 이해하고, 다양한 음악 모달리티 간의 의미적 연관성을 파악하는 데 도움을 줄 수 있기 때문입니다. 그러나, 다국어 MIR은 **데이터 부족**과 **모달리티 간의 일관성 유지**라는 어려움에 직면합니다.  따라서, 다국어 음악 데이터셋 구축 및 다국어 모달리티 간의 효과적인 정렬 기법 개발이 중요한 연구 과제입니다.  **대규모 다국어 음악 데이터셋의 구축과 다양한 언어를 지원하는 강건한 모델 개발**은 다국어 MIR의 핵심입니다.  이는 전 세계 음악 문화의 다양성을 반영하고, 보다 포괄적이고 접근성 높은 음악 정보 검색 시스템을 구축하는 데 필수적입니다.

#### Emergent Retrieval
본 논문에서 제시된 핵심 개념 중 하나인 '떠오르는 검색(Emergent Retrieval)'은 **정렬되지 않은 다양한 모달리티(예: 악보, 연주 신호, 오디오) 간의 관계를 학습 데이터 없이도 모델이 스스로 파악하여 검색을 수행하는 능력**을 의미합니다. 이는 기존의 쌍으로 된 데이터를 필요로 하는 접근 방식과는 대조적이며, **대규모 언어 모델(LLM)의 강점을 활용하여 다양한 언어와 모달리티를 통합**하는 혁신적인 접근 방식입니다.  **텍스트를 다리 삼아 모달리티 간의 연관성을 추론**하고, **보이지 않는 언어에도 일반화**할 수 있다는 점이 특징입니다.  **실험 결과는 이러한 떠오르는 검색 능력이 다양한 음악 정보 검색 과제에서 우수한 성능을 달성**함을 보여주고 있으며, 향후 **데이터 제약이 있는 상황에서도 강력한 음악 정보 검색 시스템을 구축**할 수 있는 가능성을 제시합니다.  특히, **다양한 언어 지원과 모달리티 간의 유연한 상호 작용**이 강조되며,  **음악 정보 검색 분야의 범용성과 접근성을 크게 향상**시킬 수 있는 잠재력을 지니고 있습니다.

#### Future of MIR
MIR의 미래는 **다양한 모달리티와 언어 간의 통합**에 달려 있습니다.  **대규모 언어 모델(LLM)**의 발전은 다양한 언어로 된 음악 정보에 대한 접근성을 높이고, **멀티모달 표현 학습**을 통해 악보, 연주 신호, 오디오 레코딩 등 다양한 형태의 음악 데이터를 텍스트와 통합적으로 처리하는 방향으로 나아가고 있습니다.  **고품질의 멀티모달 데이터셋 구축**은 이러한 통합의 기반이 되며, 앞으로는 **다양한 언어와 문화적 배경을 포괄하는** 더욱 풍부한 데이터가 필요할 것입니다.  또한, **시간적 요소를 고려한 모델링**과 **좀 더 세련된 평가 지표 개발**도 MIR의 발전에 중요한 요소입니다.  **데이터 누수 문제 해결**과 **새로운 벤치마크 데이터셋 개발**도 미래 MIR 연구의 중요한 과제가 될 것입니다.  궁극적으로, MIR은 **사용자에게 더욱 직관적이고 효율적인 음악 검색 및 접근 경험**을 제공하는 것을 목표로 발전해 나갈 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.10362/x2.png)

> 🔼 그림 2는 CLaMP 3 모델의 다중 모드 특징 정렬 과정을 보여줍니다. 악보와 연주 신호는 마디 또는 MIDI 메시지 단위로 분할되어 심볼릭 음악 인코더로 처리되고, 오디오는 5초 클립으로 분할되어 오디오 특징 추출기와 오디오 음악 인코더를 통해 처리됩니다. 심볼릭 및 오디오 표현은 모두 다국어 텍스트 인코더의 텍스트 표현과 정렬됩니다. 대조 학습을 통해 모든 모드의 특징이 공유 표현 공간에 정렬되어 다중 모드 검색을 가능하게 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: CLaMP 3 uses contrastive learning to align features across modalities. Sheet music and performance signals are segmented into units (bars or MIDI messages) and processed by the symbolic music encoder, while audio is segmented into 5-second clips and processed through the audio feature extractor and audio music encoder. Both symbolic and audio representations are aligned with text representations from the multilingual text encoder.
> </details>



![](https://arxiv.org/html/2502.10362/x3.png)

> 🔼 M4-RAG 데이터셋에 포함된 원본 언어와 번역된 언어의 분포를 보여주는 그래프입니다. 총 27개 언어를 포함하며, 각 언어별 원본 데이터와 번역 데이터의 개수를 비교하여 시각적으로 보여줍니다. 이를 통해 M4-RAG 데이터셋의 다국어 지원 범위와 언어별 데이터 균형을 파악하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Language distribution of original and translated entries in M4-RAG, covering 27 languages.
> </details>



![](https://arxiv.org/html/2502.10362/x4.png)

> 🔼 이 그림은 M4-RAG 데이터셋에 포함된 음악 트랙의 국가별 분포를 보여줍니다. 전 세계 194개국에서 수집된 음악 데이터의 다양성을 시각적으로 나타냅니다.  각 국가의 음악 트랙 수는 크기가 다른 원으로 표현되며, 원의 크기가 클수록 해당 국가에서 수집된 음악 트랙의 수가 많음을 나타냅니다. 이 그림은 M4-RAG 데이터셋의 글로벌한 포괄성을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Country-wise distribution of music tracks in M4-RAG, spanning 194 countries.
> </details>



![](https://arxiv.org/html/2502.10362/x5.png)

> 🔼 그림 5는 WikiMT-X 데이터셋의 장르 분포를 보여줍니다.  막대 그래프는 각 장르에 속한 음악 트랙의 수를 나타냅니다. 이 그래프를 통해 WikiMT-X 데이터셋에 포함된 다양한 장르의 비율을 파악할 수 있습니다.  특정 장르(예: 재즈, 팝, 컨트리, 포크, 록, 클래식, 종교 음악, R&B)의 트랙 수가 다른 장르에 비해 얼마나 많은지 시각적으로 확인할 수 있습니다.  이는 데이터셋의 균형과 다양성을 평가하는 데 유용합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Genre distribution of the WikiMT-X dataset.
> </details>



![](https://arxiv.org/html/2502.10362/x8.png)

> 🔼 그림 6은 M4-RAG 데이터셋 생성에 사용된 메타데이터 생성 프롬프트를 보여줍니다. 이 프롬프트는 제목, 아티스트, 지역, 언어, 장르, 태그, 배경 정보, 음악 분석, 일반적인 설명, 시각적 장면 등 음악 메타데이터를 포괄적으로 설명하기 위한 필수 JSON 구조를 설명합니다. 고품질의 일관된 메타데이터 추출을 보장하기 위해 자세한 지침과 형식 요구 사항이 제공됩니다. 저희의 경험을 바탕으로 지역 및 언어 출력에 ISO 표준을 준수하는 요구 사항을 프롬프트에 추가할 것을 권장합니다. 이렇게 하면 후처리가 줄어듭니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: The metadata generation prompt was used for constructing the M4-RAG dataset. This prompt outlines the required JSON structure for describing music metadata comprehensively, including fields for title, artists, region, language, genres, tags, background context, musical analysis, general description, and visual scene. Detailed instructions and formatting requirements are provided to ensure high-quality and consistent metadata extraction from search results. Based on our experience, we recommend adding the requirement to the prompt that Region and Language be output in accordance with ISO standards, which can reduce the need for post-processing.
> </details>



![](https://arxiv.org/html/2502.10362/x9.png)

> 🔼 그림 7은 M4-RAG 및 WikiMT-X 데이터셋의 메타데이터 예시를 보여줍니다. 위쪽 부분은 M4-RAG 데이터셋의 'Mairi's Wedding' 항목을 보여주며, 영어 및 베트남어로 된 자세한 다국어 메타데이터와 YouTube ID로 식별되는 관련 오디오 레코딩이 포함되어 있습니다. 아래쪽 부분은 WikiMT-X 데이터셋의 'Deed I Do' 항목을 보여주며, 오디오 레코딩으로 연결되는 YouTube ID, 미리 정의된 8개 범주 중 하나인 재즈 장르 레이블, 네 가지 유형의 장문 텍스트 주석, 그리고 ABC 표기법으로 된 악보가 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Metadata examples from the M4-RAG and WikiMT-X datasets. The top section shows an entry for “Mairi’s Wedding” from the M4-RAG dataset, including detailed multilingual metadata in English and Vietnamese, and an associated audio recording identified by a YouTube ID. The bottom section presents an entry for “Deed I Do” from the WikiMT-X dataset, which includes a YouTube ID linking to an audio recording, a genre label (Jazz, one of eight predefined categories), four types of long-form text annotations, and a lead sheet in ABC notation.
> </details>



![](https://arxiv.org/html/2502.10362/x10.png)

> 🔼 그림 8(a)는 모달리티(Sheet Music, MIDI, Audio, Text) 기반의 t-SNE 시각화 결과를 보여줍니다. 각 모달리티는 고유한 클러스터를 형성하며, Text 모달리티 주변에 음악 모달리티들이 대칭적으로 분포하는 것을 알 수 있습니다. 이는 Text가 모달리티들을 통합하는 데 중요한 역할을 한다는 것을 시사합니다.  모달리티 클러스터의 크기는 각 모달리티의 표현 능력 및 상호 연관성을 반영합니다.
> <details>
> <summary>read the caption</summary>
> (a) Modality
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | WikiMT | MidiCaps | Background | Analysis | Description | Scene |
|---|---|---|---|---|---|---|
| _CLaMP_ | 0.2561 | 0.1236 | 0.2122 | 0.1345 | 0.0306 | 0.0426 |
| _CLaMP 2_ | 0.3438 | 0.2695 | 0.3024 | 0.2374 | 0.0418 | 0.0838 |
| _CLaMP 3<sub>sa</sub><sup>c2</sup>_ | **0.4498** | **0.2826** | **0.4028** | **0.3382** | 0.0835 | **0.1512** |
| _CLaMP 3<sub>saas</sub>_ | 0.3555 | 0.1798 | 0.3301 | 0.2758 | **0.1274** | 0.1500 |
| Model | SDD | MC-R | Background | Analysis | Description | Scene |
|---|---|---|---|---|---|---|
| _CLAP_ | 0.1310 | 0.0657 | 0.0598 | 0.0429 | 0.0318 | 0.0218 |
| _TTMR++_ | 0.1437 | **0.1248** | 0.1119 | 0.0833 | 0.0584 | 0.0301 |
| _CLaMP 3<sub>sa</sub><sup>c2</sup>_ | 0.1612 | 0.0959 | 0.1180 | 0.1206 | 0.0639 | 0.0619 |
| _CLaMP 3<sub>saas</sub>_ | **0.1985** | 0.1177 | **0.2017** | **0.1711** | **0.0988** | **0.0963** |{{< /table-caption >}}
> 🔼 표 2는 다양한 벤치마크(WikiMT, MidiCaps, Song Describer Dataset(SDD), MusicCaps-Remake(MC-R))에 대한 영어 텍스트-음악 검색 결과를 보여줍니다. WikiMT와 MidiCaps는 각각 1,010쌍의 데이터를 가지고 있으며, SDD는 706개의 오디오와 1,106개의 캡션을 포함하고 있습니다. MC-R은 AudioSet 평가 세트의 전체 길이 오디오와 다시 작성된 캡션을 사용하여 데이터 누출을 방지하기 위해 2,777쌍의 데이터를 포함하고 있습니다. 표에는 심볼릭 음악과 오디오 음악에 대한 성능 벤치마크가 모두 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Results for English text-to-music retrieval on several benchmarks: WikiMT and MidiCaps have 1,010 pairs, Song Describer Dataset (SDD) has 706 audio and 1,106 captions, and MusicCaps-Remake (MC-R) contains 2,777 pairs. MC-R prevents data leakage by using full-length audio and rewritten captions from AudioSet’s evaluation set.
> </details>

{{< table-caption >}}
| Model | ru | fr | es | ar | zh | fi* | el* | ta* | kk* | am* |
|---|---|---|---|---|---|---|---|---|---|---|
| **Model** | **ru** | **fr** | **es** | **ar** | **zh** | **fi*** | **el*** | **ta*** | **kk*** | **am*** |
|  | *49.69* | *55.50* | *62.82* | *53.38* | *39.58* | *39.19* | *55.55* | *40.07* | *36.57* | *56.08* |
| **ABC Notation** |  |  |  |  |  |  |  |  |  |  |
| *CLaMP 2* | 0.2668 | 0.2968 | 0.2934 | 0.2298 | 0.1646 | 0.2795 | 0.2410 | 0.0915 | 0.2543 | 0.1237 |
| *CLaMP 3<sub>sa</sub><sup>c2</sup>* | **0.3614** | **0.3949** | **0.3921** | **0.3155** | **0.2373** | **0.3524** | **0.3226** | **0.1415** | **0.3397** | **0.1871** |
| *CLaMP 3<sub>saas</sub>* | 0.2918 | 0.3214 | 0.3239 | 0.2789 | 0.2358 | 0.2919 | 0.2681 | 0.1246 | 0.2703 | 0.1139 |
| **MIDI** |  |  |  |  |  |  |  |  |  |  |
| *CLaMP 2* | 0.1271 | 0.1414 | 0.1452 | 0.1113 | 0.0749 | 0.1438 | 0.1087 | 0.0466 | 0.1079 | 0.0616 |
| *CLaMP 3<sub>sa</sub><sup>c2</sup>* | **0.1921** | **0.2101** | **0.2137** | **0.1681** | **0.1316** | **0.2019** | **0.1702** | **0.0804** | **0.1765** | **0.1039** |
| *CLaMP 3<sub>saas</sub>* | 0.1165 | 0.1319 | 0.1330 | 0.1141 | 0.0937 | 0.1245 | 0.1143 | 0.0601 | 0.1104 | 0.0544 |
| **Audio** |  |  |  |  |  |  |  |  |  |  |
| *CLaMP 3<sub>sa</sub><sup>c2</sup>* | 0.1068 | 0.1150 | 0.1202 | 0.0981 | 0.0877 | 0.1112 | 0.1014 | 0.0720 | 0.1005 | **0.0681** |
| *CLaMP 3<sub>saas</sub>* | **0.1788** | **0.1980** | **0.1962** | **0.1665** | **0.1459** | **0.1770** | **0.1736** | **0.0945** | **0.1561** | 0.0675 |{{< /table-caption >}}
> 🔼 표 3은 다국어 음악 정보 검색 성능을 보여줍니다. 번역된 WikiMT-X 배경 주석을 사용하여 다양한 언어에 대한 텍스트-음악 검색 결과를 보여줍니다. M4-RAG 학습 데이터에 포함되지 않은 언어는 별표(*)로 표시되어 있습니다. 각 언어의 BLEU 점수는 SeamlessM4T 모델을 사용하여 텍스트를 다시 번역하고 원래 영어 텍스트와 비교하여 계산됩니다. 이 표는 다양한 언어에 대한 모델의 일반화 능력과 다국어 음악 정보 검색의 성능을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Results for multilingual text-to-music retrieval on translated WikiMT-X background annotations. Languages marked with asterisks were not included in the M4-RAG training data. The BLEU scores below each language are calculated by back-translating the text with the SeamlessM4T model and comparing it to the original English text.
> </details>

{{< table-caption >}}
| Model | S→P | S→A | P→S | P→A | A→S | A→P |
|---|---|---|---|---|---|---|
| _CLaMP 2_ | **0.5138** | - | 0.4480 | - | - | - |
| _CLaMP 3<sub>sa</sub><sup>c2</sup>_ | 0.4547 | 0.0543 | **0.5293** | 0.0313 | **0.0492** | **0.0383** |
| _CLaMP 3<sub>saas</sub>_ | 0.3262 | **0.0578** | 0.3146 | **0.0397** | 0.0410 | 0.0303 |{{< /table-caption >}}
> 🔼 표 4는 WikiMT-X 데이터셋에서 다양한 음악 모달리티(악보, MIDI, 오디오) 간의 쌍을 이용한 등장형태의 교차 모달 검색 결과를 보여줍니다.  'S'는 ABC 표기법으로 된 악보, 'P'는 ABC 표기법에서 변환된 MIDI 성능 신호, 'A'는 오디오 녹음을 나타냅니다. 이 표는 각 모달리티 쌍에 대한 평균 상호 역순위(MRR) 점수를 보여주어, 각 모달리티 간의 정보 연관성과 모델의 교차 모달 일반화 능력을 평가합니다. 예를 들어, S→P는 악보를 사용하여 MIDI 성능 신호를 검색하는 것을 나타내며, 여기서 높은 MRR 점수는 모델이 악보와 MIDI 간의 연관성을 잘 학습했음을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Results for emergent cross-modal retrieval on WikiMT-X pairings across different musical modalities. S: Sheet Music (ABC notation), P: Performance Signals (MIDI, converted from ABC), A: Audio recordings.
> </details>

{{< table-caption >}}
| Model | WikiMT | MidiCaps | Background | Analysis | Description | Scene |
|---|---|---|---|---|---|---|
| _CLaMP 3<sub>as</sub>_ | 0.1973 | 0.0788 | 0.2108 | 0.1660 | 0.1049 | 0.1056 |
| _CLaMP 3<sub>sa</sub>_ | 0.3789 | 0.1322 | 0.3591 | 0.3088 | 0.1316 | **0.1643** |
| _CLaMP 3<sup>c2</sup><sub>sa</sub>_ | **0.4498** | **0.2826** | **0.4028** | **0.3382** | 0.0835 | 0.1512 |
| _CLaMP 3<sub>assa</sub>_ | 0.2993 | 0.0884 | 0.2919 | 0.2507 | **0.1459** | 0.1464 |
| _CLaMP 3<sub>saas</sub>_ | 0.3555 | 0.1798 | 0.3301 | 0.2758 | 0.1274 | 0.1512 |
| _CLaMP 3<sup>c2</sup><sub>saas</sub>_ | 0.3631 | 0.2688 | 0.3295 | 0.2957 | 0.0951 | 0.1395 |
| Model | SDD | MC-R | Background | Analysis | Description | Scene |
|---|---|---|---|---|---|---|
| _CLaMP 3<sub>as</sub>_ | 0.1977 | 0.1117 | 0.1602 | 0.1375 | 0.0854 | 0.0819 |
| _CLaMP 3<sub>sa</sub>_ | 0.1607 | 0.0937 | 0.1718 | 0.1586 | 0.0997 | 0.0871 |
| _CLaMP 3<sup>c2</sup><sub>sa</sub>_ | 0.1612 | 0.0959 | 0.1180 | 0.1206 | 0.0639 | 0.0619 |
| _CLaMP 3<sub>assa</sub>_ | 0.2003 | 0.1045 | 0.1597 | 0.1522 | **0.1020** | 0.0873 |
| _CLaMP 3<sub>saas</sub>_ | 0.1985 | 0.1177 | **0.2017** | **0.1711** | 0.0988 | **0.0963** |
| _CLaMP 3<sup>c2</sup><sub>saas</sub>_ | **0.2115** | **0.1180** | 0.1583 | 0.1530 | 0.0768 | 0.0885 |{{< /table-caption >}}
> 🔼 표 5는 영어 텍스트-음악 검색 작업에 대한 다양한 벤치마크에 대한 결과를 보여줍니다. WikiMT 및 MidiCaps는 1,010쌍의 데이터를, Song Describer Dataset (SDD)는 706개의 오디오와 1,106개의 캡션을, MusicCaps-Remake (MC-R)은 2,777쌍의 데이터를 포함합니다. MC-R은 전체 길이의 오디오와 AudioSet의 평가 세트에서 다시 작성된 캡션을 사용하여 데이터 누출을 방지합니다. 이 표에서는 다양한 모델(CLAMP, CLAMP 2, CLAMP 3의 여러 변형 등)의 성능을 기호 음악 및 오디오 벤치마크 모두에서 비교합니다. 각 벤치마크에 대한 결과는 MRR(평균 상호 순위) 점수를 사용하여 제시됩니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Results for English text-to-music retrieval on several benchmarks: WikiMT and MidiCaps have 1,010 pairs, Song Describer Dataset (SDD) has 706 audio and 1,106 captions, and MusicCaps-Remake (MC-R) contains 2,777 pairs. MC-R prevents data leakage by using full-length audio and rewritten captions from AudioSet’s evaluation set.
> </details>

{{< table-caption >}}
| Model | ru | fr | es | ar | zh | fi* | el* | ta* | kk* | am* |
|---|---|---|---|---|---|---|---|---|---|---|
| **49.69** | **55.50** | **62.82** | **53.38** | **39.58** | **39.19** | **55.55** | **40.07** | **36.57** | **56.08** |  |
| **ABC Notation** |  |  |  |  |  |  |  |  |  |  |
| _CLaMP 3<sub>as</sub>_ | 0.1750 | 0.1931 | 0.1964 | 0.1594 | 0.1559 | 0.1828 | 0.1641 | 0.0997 | 0.1575 | 0.0876 |
| _CLaMP 3<sub>sa</sub>_ | 0.3262 | 0.3544 | 0.3536 | 0.3072 | **0.2459** | 0.3163 | 0.2879 | 0.1336 | 0.2894 | 0.1317 |
| _CLaMP 3<sub>sa</sub><sup>c2</sup>_ | **0.3614** | **0.3949** | **0.3921** | **0.3155** | 0.2373 | **0.3524** | **0.3226** | 0.1415 | **0.3397** | **0.1871** |
| _CLaMP 3<sub>assa</sub>_ | 0.2648 | 0.2810 | 0.2817 | 0.2450 | 0.2271 | 0.2644 | 0.2415 | **0.1432** | 0.2561 | 0.1300 |
| _CLaMP 3<sub>saas</sub>_ | 0.2918 | 0.3214 | 0.3239 | 0.2789 | 0.2358 | 0.2919 | 0.2681 | 0.1246 | 0.2703 | 0.1139 |
| _CLaMP 3<sub>saas</sub><sup>c2</sup>_ | 0.2954 | 0.3171 | 0.3225 | 0.2773 | 0.2144 | 0.2990 | 0.2721 | 0.1348 | 0.2750 | 0.1690 |
| **MIDI** |  |  |  |  |  |  |  |  |  |  |
| _CLaMP 3<sub>as</sub>_ | 0.0418 | 0.0416 | 0.0432 | 0.0404 | 0.0332 | 0.0456 | 0.0449 | 0.0297 | 0.0398 | 0.0267 |
| _CLaMP 3<sub>sa</sub>_ | 0.1174 | 0.1284 | 0.1316 | 0.1132 | 0.0890 | 0.1217 | 0.1112 | 0.0623 | 0.1117 | 0.0540 |
| _CLaMP 3<sub>sa</sub><sup>c2</sup>_ | **0.1921** | **0.2101** | **0.2137** | **0.1681** | **0.1316** | **0.2019** | **0.1702** | **0.0804** | **0.1765** | **0.1039** |
| _CLaMP 3<sub>assa</sub>_ | 0.0565 | 0.0582 | 0.0620 | 0.0582 | 0.0517 | 0.0620 | 0.0585 | 0.0394 | 0.0595 | 0.0354 |
| _CLaMP 3<sub>saas</sub>_ | 0.1165 | 0.1319 | 0.1330 | 0.1141 | 0.0937 | 0.1245 | 0.1143 | 0.0601 | 0.1104 | 0.0544 |
| _CLaMP 3<sub>saas</sub><sup>c2</sup>_ | 0.1499 | 0.1645 | 0.1664 | 0.1408 | 0.1049 | 0.1560 | 0.1399 | 0.0653 | 0.1335 | 0.0793 |
| **Audio** |  |  |  |  |  |  |  |  |  |  |
| _CLaMP 3<sub>as</sub>_ | 0.1267 | 0.1515 | 0.1525 | 0.1210 | 0.1089 | 0.1430 | 0.1428 | 0.0610 | 0.1043 | 0.0559 |
| _CLaMP 3<sub>sa</sub>_ | 0.1619 | 0.1717 | 0.1714 | 0.1529 | 0.1414 | 0.1585 | 0.1544 | **0.0991** | 0.1456 | 0.0774 |
| _CLaMP 3<sub>sa</sub><sup>c2</sup>_ | 0.1068 | 0.1150 | 0.1202 | 0.0981 | 0.0877 | 0.1112 | 0.1014 | 0.0720 | 0.1005 | 0.0681 |
| _CLaMP 3<sub>assa</sub>_ | 0.1426 | 0.1580 | 0.1588 | 0.1370 | 0.1202 | 0.1468 | 0.1431 | 0.0795 | 0.1276 | 0.0617 |
| _CLaMP 3<sub>saas</sub>_ | **0.1788** | **0.1980** | **0.1962** | **0.1665** | **0.1459** | **0.1770** | **0.1736** | 0.0945 | **0.1561** | 0.0675 |
| _CLaMP 3<sub>saas</sub><sup>c2</sup>_ | 0.1331 | 0.1566 | 0.1554 | 0.1304 | 0.1208 | 0.1550 | 0.1460 | 0.0901 | 0.1340 | **0.0874** |{{< /table-caption >}}
> 🔼 표 6은 다국어 음악 정보 검색을 평가하기 위해 번역된 WikiMT-X 배경 주석에 대한 결과를 보여줍니다.  M4-RAG 학습 데이터에 포함되지 않은 언어는 별표(*)로 표시되어 있습니다. 각 언어 아래의 BLEU 점수는 SeamlessM4T 모델을 사용하여 텍스트를 재번역하고 원래 영어 텍스트와 비교하여 계산됩니다. 이 표는 다양한 언어에 대한 CLaMP 3의 성능을 보여주며, 특히 M4-RAG 학습 데이터에 포함되지 않은 언어에 대한 일반화 능력을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Results for multilingual text-to-music retrieval on translated WikiMT-X background annotations. Languages marked with asterisks were not included in the M4-RAG training data. The BLEU scores below each language are calculated by back-translating the text with the SeamlessM4T model and comparing it to the original English text.
> </details>

{{< table-caption >}}
| Model | S→P | S→A | P→S | P→A | A→S | A→P |
|---|---|---|---|---|---|---|
| _CLaMP 3<sub>as</sub>_ | 0.1637 | 0.0557 | 0.1477 | 0.0248 | 0.0456 | 0.0237 |
| _CLaMP 3<sub>sa</sub>_ | 0.3205 | **0.0739** | 0.3054 | 0.0397 | 0.0479 | 0.0237 |
| _CLaMP 3<sub>sa</sub><sup>c2</sup>_ | **0.4547** | 0.0543 | **0.5293** | 0.0313 | 0.0492 | 0.0383 |
| _CLaMP 3<sub>assa</sub>_ | 0.1911 | 0.0619 | 0.1646 | 0.0299 | 0.0513 | 0.0264 |
| _CLaMP 3<sub>saas</sub>_ | 0.3262 | 0.0578 | 0.3146 | 0.0397 | 0.0410 | 0.0303 |
| _CLaMP 3<sub>saas</sub><sup>c2</sup>_ | 0.3909 | 0.0688 | 0.4375 | **0.0467** | **0.0558** | **0.0431** |{{< /table-caption >}}
> 🔼 표 7은 WikiMT-X 데이터셋에서 서로 다른 음악 모달리티(악보, MIDI, 오디오) 간의 쌍을 사용하여 등장하는 교차 모달 검색 결과를 보여줍니다.  각 모달리티는 다음과 같이 약자로 표시됩니다: S(악보, ABC 표기법), P(MIDI, ABC 표기법에서 변환), A(오디오 녹음).  표는 각 모달리티 쌍(예: 악보에서 MIDI로, MIDI에서 오디오로 등)에 대한 평균 역순위(MRR) 점수를 보여주어, 모델이 훈련되지 않은 모달리티 간의 연관성을 얼마나 잘 파악하는지 평가합니다.  이는 모델의 일반화 능력과 다양한 음악 표현 방식에 대한 이해도를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Results for emergent cross-modal retrieval on WikiMT-X pairings across different musical modalities. S: Sheet Music (ABC notation), P: Performance Signals (MIDI, converted from ABC), A: Audio recordings.
> </details>

{{< table-caption >}}
| Model | Modality | WikiMT F1-macro | WikiMT Accuracy | VGMIDI F1-macro | VGMIDI Accuracy | Pianist8 F1-macro | Pianist8 Accuracy |
|---|---|---|---|---|---|---|---| 
| _M3_ | ABC | 0.2349 | 0.4010 | 0.6016 | 0.6341 | 0.7395 | 0.7590 |
| _CLaMP_ | ABC | 0.3452 | 0.4267 | 0.6453 | 0.6866 | 0.7067 | 0.7152 |
| _CLaMP 2_ | ABC | **0.3990** | **0.4653** | 0.7449 | **0.8049** | **0.8025** | **0.8072** |
| _CLaMP 3<sub>as</sub>_ | ABC | 0.3135 | 0.4307 | 0.6638 | 0.7073 | 0.6872 | 0.6867 |
| _CLaMP 3<sub>sa</sub>_ | ABC | 0.3225 | 0.4455 | 0.7725 | **0.8049** | 0.7403 | 0.7590 |
| _CLaMP 3<sub>sa</sub><sup>c2</sup>_ | ABC | 0.3316 | 0.4356 | 0.6845 | 0.7317 | 0.7722 | 0.7711 |
| _CLaMP 3<sub>assa</sub>_ | ABC | 0.3102 | 0.4455 | 0.4990 | 0.6341 | 0.6796 | 0.6988 |
| _CLaMP 3<sub>saas</sub>_ | ABC | 0.3177 | 0.4356 | **0.7969** | **0.8049** | 0.7716 | 0.7952 |
| _CLaMP 3<sub>saas</sub><sup>c2</sup>_ | ABC | 0.3568 | 0.4257 | 0.6694 | 0.7561 | 0.7891 | 0.7952 |
| _M3_ | MIDI | 0.2621 | 0.4257 | 0.5399 | 0.6098 | **0.9199** | **0.9157** |
| _CLaMP 2_ | MIDI | 0.2898 | 0.4455 | 0.5246 | 0.6585 | 0.8927 | 0.8916 |
| _CLaMP 3<sub>as</sub>_ | MIDI | **0.3361** | **0.4653** | 0.5600 | 0.5854 | 0.8186 | 0.8313 |
| _CLaMP 3<sub>sa</sub>_ | MIDI | 0.2614 | 0.4010 | **0.6864** | **0.7073** | 0.8461 | 0.8554 |
| _CLaMP 3<sub>sa</sub><sup>c2</sup>_ | MIDI | 0.3073 | 0.4455 | 0.6223 | **0.7073** | 0.8696 | 0.8675 |
| _CLaMP 3<sub>assa</sub>_ | MIDI | 0.2882 | 0.4406 | 0.5001 | 0.6098 | 0.8076 | 0.8193 |
| _CLaMP 3<sub>saas</sub>_ | MIDI | 0.2721 | 0.4158 | 0.5723 | 0.6341 | 0.7834 | 0.7952 |
| _CLaMP 3<sub>saas</sub><sup>c2</sup>_ | MIDI | 0.2943 | 0.4208 | 0.5474 | 0.6829 | 0.8565 | 0.8554 |{{< /table-caption >}}
> 🔼 표 8은 세 가지 데이터셋(WikiMT, VGMIDI, Pianist8)에서 ABC 표기법과 MIDI에 대한 기호 음악 분류 성능을 보여줍니다. WikiMT는 8개의 장르로 분류된 1,010개의 악보를 포함하고, VGMIDI는 4가지 감정으로 분류된 204개의 MIDI 파일을 포함하고, Pianist8은 8명의 작곡가로 분류된 411개의 피아노 연주 MIDI 파일을 포함합니다. 이 표는 다양한 모델(M3, CLAMP, CLAMP 2, 그리고 여러 가지 CLAMP 3 변형 모델)의 분류 정확도와 F1-macro 점수를 비교하여 각 모델의 성능을 보여줍니다. 각 모델은 ABC 표기법과 MIDI 데이터 모두에서 평가되었으며, 데이터셋과 모델에 따라 성능이 다르게 나타났습니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Symbolic classification performance for ABC notation and MIDI was assessed across three datasets: WikiMT (1,010 pieces, 8 genres), VGMIDI (204 pieces, 4 emotions), and Pianist8 (411 pieces, 8 composers).
> </details>

{{< table-caption >}}
| Model | MTT Tagging ROC | MTT Tagging AP | GS Key Acc | GTZAN Genre Acc | EMO Emotion R2<sup>V</sup> | EMO Emotion R2<sup>A</sup> | Nsynth Instrument Acc | Nsynth Pitch Acc | VocalSet Tech Acc | VocalSet Singer Acc |
|---|---|---|---|---|---|---|---|---|---|---|
| _MERT<sub>mean</sub>_ | 0.9068 | 0.3915 | **0.6475** | 0.6689 | 0.5185 | **0.7501** | 0.6963 | **0.9152** | **0.7219** | **0.8961** |
| _CLAP_ | 0.9066 | 0.3897 | 0.1596 | 0.8207 | 0.5408 | 0.7025 | **0.7817** | 0.5146 | 0.6868 | 0.6327 |
| _TTMR++_ | 0.9082 | 0.3922 | 0.1672 | 0.8551 | 0.5599 | 0.7116 | 0.6735 | 0.5012 | 0.6342 | 0.5352 |
| _CLaMP 3<sub>as</sub>_ | 0.9097 | 0.3888 | 0.4935 | 0.8379 | 0.5944 | 0.7413 | 0.6445 | 0.8601 | 0.6780 | 0.8491 |
| _CLaMP 3<sub>sa</sub>_ | 0.9084 | 0.3863 | 0.2533 | 0.8448 | **0.6031** | 0.6949 | 0.6338 | 0.8647 | 0.7061 | 0.8419 |
| _CLaMP 3<math alttext="{}_{sa}^{c2}" display="inline">{}_{sa}^{c2}</math>_ | 0.9092 | 0.3924 | 0.2545 | 0.8551 | 0.5477 | 0.6876 | 0.6147 | 0.8574 | 0.6710 | 0.8007 |
| _CLaMP 3<sub>assa</sub>_ | 0.9098 | 0.3935 | 0.1498 | **0.8793** | 0.5921 | 0.7327 | 0.6411 | 0.8742 | 0.6842 | 0.8555 |
| _CLaMP 3<sub>saas</sub>_ | **0.9109** | **0.3941** | 0.5377 | 0.8655 | 0.5907 | 0.7004 | 0.6377 | 0.8689 | 0.7053 | 0.8441 |
| _CLaMP 3<math alttext="{}_{saas}^{c2}" display="inline">{}_{saas}^{c2}</math>_ | 0.9095 | 0.3938 | 0.3907 | 0.8138 | 0.5368 | 0.6589 | 0.6562 | 0.8732 | 0.6798 | 0.8470 |{{< /table-caption >}}
> 🔼 표 9는 MARBLE 벤치마크에 포함된 여러 오디오 분류 작업에 대한 성능을 보여줍니다.  MARBLE 벤치마크는 MTT(25,860 클립, 50 태그), GS(7,035 클립, 24 키), GTZAN(1,000 클립, 10 장르), EMO(744 클립, valence/arousal 회귀), Nsynth(305,979 클립, 11 악기 종류, 88 피치), VocalSet(7,506 클립, 17 노래 기법, 20 가수) 데이터셋을 포함합니다. 각 데이터셋은 다양한 오디오 특징(태그, 키, 장르, 감정, 악기, 피치, 노래 기법)을 분류하는 작업에 사용됩니다. 이 표는 다양한 모델의 성능을 비교하여 각 모델의 강점과 약점을 파악하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Audio classification performance is evaluated on multiple benchmarks included in MARBLE: MTT (25,860 clips, 50 tags), GS (7,035 clips, 24 keys), GTZAN (1,000 clips, 10 genres), EMO (744 clips, valence/arousal regression), Nsynth (305,979 clips, 11 instrument categories, 88 pitches), and VocalSet (7,506 clips, 17 singing techniques, 20 singers).
> </details>

{{< table-caption >}}
| Model | Instrument ROC | Instrument AP | Mood/Theme ROC | Mood/Theme AP | Genre ROC | Genre AP | Top50 ROC | Top50 AP |
|---|---|---|---|---|---|---|---|---|
| _MERT<sub>mean</sub>_ | 0.7421 | 0.1764 | 0.7598 | 0.1383 | 0.8672 | 0.1818 | 0.8280 | 0.2837 |
| _CLAP_ | 0.7480 | 0.1812 | 0.7601 | 0.1323 | 0.8544 | 0.1716 | 0.8197 | 0.2773 |
| _TTMR++_ | 0.7806 | 0.2111 | 0.7705 | 0.1477 | 0.8742 | 0.2030 | **0.8340** | 0.3049 |
| _CLaMP 3<sub>as</sub>_ | 0.7895 | 0.2254 | 0.7814 | 0.1476 | 0.8750 | **0.2114** | 0.8321 | 0.3068 |
| _CLaMP 3<sub>sa</sub>_ | 0.7780 | 0.2112 | 0.7823 | 0.1533 | 0.8713 | 0.2008 | 0.8276 | 0.3011 |
| _CLaMP 3<sub>sa</sub><sup>c2</sup>_ | 0.7832 | 0.2168 | 0.7796 | 0.1475 | 0.8679 | 0.2046 | 0.8220 | 0.2964 |
| **_CLaMP 3<sub>assa</sub>_** | **0.7911** | **0.2269** | 0.7828 | 0.1486 | **0.8763** | 0.2109 | 0.8290 | 0.3041 |
| _CLaMP 3<sub>saas</sub>_ | 0.7872 | 0.2208 | **0.7835** | **0.1547** | 0.8703 | 0.2076 | 0.8242 | 0.3021 |
| _CLaMP 3<sub>saas</sub><sup>c2</sup>_ | 0.7803 | 0.2145 | 0.7825 | 0.1522 | 0.8734 | 0.2092 | 0.8296 | **0.3074** |{{< /table-caption >}}
> 🔼 표 10은 MTG-Jamendo 데이터셋(55,000개 이상의 트랙)을 사용하여 수행된 오디오 분류 성능을 보여줍니다.  총 4가지 과제(악기 분류(41개 태그), 분위기/주제 분류(59개 태그), 장르 분류(95개 태그), 상위 50개 다중 레이블 분류)에 대해 평가했습니다. 이 표는 다양한 모델(MERT, CLAMP, TTMR++, 그리고 여러 CLaMP 3 변형)의 성능을 ROC, AP, 정확도와 같은 다양한 지표를 통해 비교 분석하여 각 모델의 분류 능력을 정량적으로 보여줍니다. 특히, 악기, 분위기/주제, 장르 등 다양한 음악적 속성에 대한 분류 성능을 비교함으로써, 각 모델의 강점과 약점을 파악하는 데 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Audio classification performance on the MTG-Jamendo dataset (55,000+ tracks) was evaluated across four tasks: instrument classification (41 tags), mood/theme classification (59 tags), genre classification (95 tags), and top-50 multi-label classification.
> </details>

{{< table-caption >}}
| Model | ABC | MIDI | Audio | Background | Analysis | Description | Scene |
|---|---|---|---|---|---|---|---| 
| **Accuracy** |  |  |  |  |  |  |  |
| _CLaMP_ | 0.7000 | - | - | 0.8050 | 0.7900 | 0.6900 | 0.6250 |
| _CLaMP 2_ | 0.6800 | 0.6350 | - | 0.7900 | 0.8150 | 0.7250 | 0.6150 |
| _CLAP_ | - | - | 0.6450 | 0.6950 | 0.6800 | 0.6500 | 0.5550 |
| _TTMR++_ | - | - | 0.7150 | 0.7400 | 0.7600 | 0.6700 | 0.5950 |
| _CLaMP 3<sub>as</sub>_ | 0.6850 | 0.6100 | 0.7050 | 0.8200 | 0.8350 | **0.7800** | 0.6550 |
| _CLaMP 3<sub>sa</sub>_ | 0.7000 | 0.6650 | 0.6850 | 0.8000 | 0.8600 | 0.7700 | 0.6500 |
| _CLaMP 3<sub>sa</sub><sup>c2</sup>_ | 0.6850 | 0.6350 | 0.6850 | 0.7850 | 0.8550 | 0.7750 | 0.6500 |
| _CLaMP 3<sub>assa</sub>_ | 0.7000 | 0.6300 | **0.7200** | **0.8650** | **0.8650** | 0.7700 | **0.6850** |
| _CLaMP 3<sub>saas</sub>_ | **0.7150** | **0.6800** | 0.7050 | 0.8400 | 0.8550 | **0.7800** | 0.6650 |
| _CLaMP 3<sub>saas</sub><sup>c2</sup>_ | 0.6750 | 0.6300 | 0.6850 | 0.8300 | 0.8500 | 0.7700 | **0.6850** |
| **F1-macro** |  |  |  |  |  |  |  |
| _CLaMP_ | 0.5252 | - | - | 0.6835 | 0.6486 | 0.6079 | 0.4447 |
| _CLaMP 2_ | 0.5287 | 0.3784 | - | 0.6617 | 0.6832 | 0.6333 | 0.3710 |
| _CLAP_ | - | - | 0.3943 | 0.5913 | 0.5491 | 0.4921 | 0.3100 |
| _TTMR++_ | - | - | 0.4714 | 0.6914 | 0.6694 | 0.6254 | 0.4246 |
| _CLaMP 3<sub>as</sub>_ | 0.5431 | 0.4005 | 0.4755 | 0.7424 | 0.7933 | **0.7639** | 0.4780 |
| _CLaMP 3<sub>sa</sub>_ | 0.5345 | 0.5108 | 0.4881 | 0.7917 | 0.8199 | 0.7372 | 0.4527 |
| _CLaMP 3<sub>sa</sub><sup>c2</sup>_ | 0.5428 | 0.4171 | 0.4589 | 0.6626 | 0.7439 | 0.7318 | 0.4260 |
| _CLaMP 3<sub>assa</sub>_ | 0.5499 | 0.3976 | **0.5130** | **0.8486** | **0.8277** | 0.6878 | **0.5207** |
| _CLaMP 3<sub>saas</sub>_ | **0.5720** | **0.4967** | 0.4995 | 0.8123 | 0.8225 | 0.7484 | 0.4742 |
| _CLaMP 3<sub>saas</sub><sup>c2</sup>_ | 0.5182 | 0.4313 | 0.4432 | 0.7811 | 0.8054 | 0.7082 | 0.4999 |{{< /table-caption >}}
> 🔼 표 11은 WikiMT-X 데이터셋(1,000개 항목, 8개 장르)에서 다양한 음악 모달리티(ABC 악보, MIDI, 오디오)와 텍스트 주석(배경, 분석, 설명, 장면)에 대한 분류 성능을 보여줍니다.  다양한 음악 표현 방식과 텍스트 설명에 따른 8개 장르의 음악 분류 정확도와 F1-macro 점수를 비교 분석하여, 모델의 성능을 다각적으로 평가합니다.  각 모달리티와 텍스트 유형에 따른 분류 정확도를 비교함으로써, 모델이 어떤 유형의 데이터에 강점을 보이는지 파악하고, 다양한 음악 데이터 표현 방식과 텍스트 정보 간의 상관관계를 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 11: Classification performance on WikiMT-X (1,000 entries, 8 genres) across different musical modalities and text annotations.
> </details>

{{< table-caption >}}
| Model | Full Set (5,521 pairs) |  |  |  | Eval Set (2,858 pairs) |  |  |  |
|---|---|---|---|---|---|---|---|---|
|  | _RF_ | _RC_ | _OF_ | _OC_ | _RF_ | _RC_ | _OF_ | _OC_ |
|---|---|---|---|---|---|---|---|---|
| _CLAP_ | 0.0536 | 0.0743 | 0.0640 | 0.0894 | 0.0657 | 0.0886 | 0.0774 | 0.1113 |
| _TTMR++_ | **0.1410** | **0.2315** | **0.1757** | **0.3155** | **0.1248** | **0.1341** | **0.1219** | **0.1382** |
| _CLaMP 3<sub>as</sub>_ | 0.0874 | 0.0642 | 0.0696 | 0.0536 | 0.1119 | 0.0830 | 0.0917 | 0.0699 |
| _CLaMP 3<sub>sa</sub>_ | 0.0741 | 0.0591 | 0.0530 | 0.0431 | 0.0934 | 0.0735 | 0.0661 | 0.0572 |
| _CLaMP 3<sub>sa</sub><sup>c2</sup>_ | 0.0729 | 0.0609 | 0.0619 | 0.0504 | 0.0961 | 0.0832 | 0.0822 | 0.0651 |
| _CLaMP 3<sub>assa</sub>_ | 0.0830 | 0.0592 | 0.0743 | 0.0530 | 0.1045 | 0.0784 | 0.0897 | 0.0723 |
| _CLaMP 3<sub>saas</sub>_ | 0.0890 | 0.0705 | 0.0652 | 0.0523 | 0.1177 | 0.0889 | 0.0890 | 0.0682 |
| _CLaMP 3<sub>saas</sub><sup>c2</sup>_ | 0.0973 | 0.0737 | 0.0762 | 0.0550 | 0.1180 | 0.0933 | 0.0961 | 0.0710 |{{< /table-caption >}}
> 🔼 표 12는 MusicCaps 데이터셋을 사용한 영어 텍스트-음악 검색 결과를 보여줍니다. 기존 모델의 데이터 유출 문제를 반영하여 전체 데이터셋과 AudioSet 평가 데이터셋에서 모두 평가를 진행했습니다. R/O는 재작성 또는 원본 캡션 사용 여부를, F/C는 전체 트랙 또는 클립 사용 여부를 나타냅니다.  다양한 조건(재작성된 캡션 사용 여부, 전체 트랙 또는 클립 사용 여부) 하에서 CLAMP 3 모델과 기존 모델(CLAP, TTMR++)의 성능을 비교 분석하여 데이터 유출 문제의 영향과 모델 성능에 미치는 영향을 평가합니다.
> <details>
> <summary>read the caption</summary>
> Table 12: Results for English text-to-music retrieval on MusicCaps, reflecting data leakage in baseline models. Evaluations are conducted on both the full set and the AudioSet evaluation set. R/O denotes the use of rewritten or original captions, while F/C indicates retrieval using full tracks or clips.
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