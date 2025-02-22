---
title: "CLIPPER: Compression enables long-context synthetic data generation"
summary: "CLIPPER: 압축을 통해 장문 맥락 합성 데이터 생성"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 University of Maryland, College Park",]
showSummary: true
date: 2025-02-20
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.14854 {{< /keyword >}}
{{< keyword icon="writer" >}} Chau Minh Pham et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-21 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.14854" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.14854" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/clipper-compression-enables-long-context" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

장문 맥락 추론을 위한 고품질 합성 데이터 생성은 LLM 개발의 큰 과제입니다.  기존의 단순한 방법들은 장문 텍스트에서 복잡한 추론을 요구하는 과제에 적합하지 않고, 오류가 많으며 비용이 많이 듭니다.  

CLIPPER는 이러한 문제를 해결하기 위해 **텍스트 압축**을 기반으로 합니다.  먼저, 장문의 텍스트를 요약 및 장별 개요로 압축하고, 이를 바탕으로 복잡한 주장과 사고 과정을 생성합니다.  **CLIPPER를 통해 생성된 19,000개의 합성 데이터셋**을 사용하여 여러 LLM 모델을 미세 조정한 결과, **기존 최고 성능을 뛰어넘는 성과**를 거두었습니다. 특히, 10B 미만의 소규모 모델에서의 성능 향상이 두드러집니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} CLIPPER는 장문 맥락 추론을 위한 합성 데이터 생성 문제를 해결하기 위한 압축 기반 접근법을 제시합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} CLIPPER를 사용하여 생성된 합성 데이터는 기존 방법보다 더욱 정확하고 복잡하며, 이를 통해 LLM의 장문 맥락 추론 성능을 크게 향상시킵니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} CLIPPER는 10B 미만의 소규모 모델에서도 괄목할 만한 성능 향상을 달성하며, 새로운 state-of-the-art를 달성합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **장문 맥락 추론을 위한 합성 데이터 생성의 어려움**을 해결하는 압축 기반 접근 방식인 CLIPPER를 제시하여 **장문 맥락 추론 능력 향상**에 기여합니다.  CLIPPER는 기존 방법의 한계를 극복하고, 더욱 **유효하고 정확한 합성 데이터**를 생성하여 LLM 성능 향상에 새로운 가능성을 제시하며, **추후 연구를 위한 새로운 방향**을 제시합니다.  특히, 소규모 모델에서의 성능 향상은 상당히 주목할 만합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.14854/x1.png)

> 🔼 그림 1은 CLIPPER의 테스트 세트와 NoCha 벤치마크에서 기준 모델, 소규모 폐쇄형 모델 및 CLIPPER 모델의 결과를 보여줍니다.  가로축은 정확도(%)이고 세로축은 모델 이름입니다.  각 모델에 대해 CLIPPER 테스트 세트와 NoCha 벤치마크에서의 성능이 표시됩니다.  CLIPPER 모델은 합성 데이터로 미세 조정되었으며, 기준 모델과 비교하여 서술적 주장 검증 작업에서 상당한 성능 향상을 보여줍니다.  즉, CLIPPER를 사용한 미세 조정은 모델의 서술적 주장 검증 능력을 크게 향상시킨다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Results on CLIPPER’s test set and NoCha for baselines, small closed models, and CLIPPER models. Fine-tuning on our synthetic data significantly improves narrative claim verification.
> </details>





{{< table-caption >}}
| Category | NAÏVE | CLIPPER | Error Definition | Example |
|---|---|---|---|---|
| Invalid | 11.5% | 9.1% | The claim is incorrect with respect to the book text, or the true/false claim pair is invalid. | Anne rejects three marriage proposals during her time at Redmond College: from Charlie Sloane, Gilbert Blythe, and Roy Gardner, <span class="ltx_text" style="color:#BF0040;">all because she doesn’t love them</span>. <span class="ltx_text ltx_font_italic">(This false claim is not entirely false because Anne really didn’t love them or wasn’t initially aware of her romantic feelings.)</span>. |
| Misattribution | 28.9% | 4.6% | The claim is valid, but the associated explanation does not cite the correct chapters. | Dr. Sheppard…was the last person known to have seen Roger Ackroyd alive at 8:50 PM on the night of the murder, and he later assisted Hercule Poirot in the investigation while simultaneously <span class="ltx_text" style="color:#BF0040;">concealing Ralph Paton in a nursing home</span>. <span class="ltx_text ltx_font_italic">(The explanation cites Chapter 1, 4, 16, and 20, but misses Chapter 24, which mentions that Ralph is in a nursing home)</span> |
| Explicit references | 15.4% | 0.0% | The claim is easier to verify since it includes direct quotes and chapter references, eliminating the need for event retrieval. | Alice’s pursuit of the White Rabbit, which begins with her following him down a rabbit hole in <span class="ltx_text" style="color:#BF0040;">Chapter 1</span>, continues throughout her adventure, including an encounter in the King and Queen of Hearts’ court in <span class="ltx_text" style="color:#BF0040;">Chapter 11</span> where the Rabbit acts as a herald. |
| Duplication | 17.3% | 3.0% | The claim describes the same events as another. Although their content is similar, differences in wording may allow both to pass our deduplication process. | "Dorian Gray’s cruel rejection of Sibyl Vane after her poor performance as Juliet leads to her suicide, which Dorian callously dismisses by attending the opera the following night, resulting in the first noticeable change in his portrait […]" versus "Dorian Gray’s cruel rejection of Sibyl Vane after her poor performance as Juliet leads to her suicide, causing the first visible change in his portrait […] culminate in his murder of Basil Hallward years later […]." |{{< /table-caption >}}

> 🔼 표 1은 NAÏVE 방법과 CLIPPER 방법을 사용하여 생성된 주장들에 대한 오류 유형을 보여줍니다.  NAÏVE 방법은 표 5의 6권의 책을 바탕으로 52개의 주장을 생성했고, CLIPPER 방법은 같은 책들을 바탕으로 66개의 주장을 생성했습니다.  표에는 각 방법으로 생성된 주장들 중에서 잘못된 주장, 잘못된 장을 인용한 주장, 장 번호 또는 직접 인용문을 포함하는 주장, 중복된 주장 등의 오류 유형이 나타나 있습니다.  NAÏVE 방법으로 생성된 주장들에는 CLIPPER 방법보다 훨씬 더 많은 오류가 포함되어 있음을 보여줍니다.  표에는 NAÏVE 방법으로 생성된 주장들 중에서 오류 유형의 예시도 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Error types among claims produced by NAÏVE (52) and CLIPPER (66) based on six books from Table 5. Examples are selected from NAÏVE claims. CLIPPER produces much fewer claims with errors than NAÏVE.
> </details>





### In-depth insights


#### Long-Context LLM Data
장문 컨텍스트 LLM 데이터는 **대규모 언어 모델(LLM)**의 성능 향상에 필수적이나, 고품질 데이터 생성의 어려움으로 인해 연구가 활발히 진행되고 있습니다.  **데이터의 품질과 확장성**은 장문 컨텍스트 추론 성능에 직접적인 영향을 미칩니다.  단순히 긴 문서를 사용하는 것보다, **요약, 개요 생성 등의 압축 기법**을 통해 모델의 처리 부담을 줄이고, 핵심 정보에 집중하는 전략이 효과적입니다.  **인간의 개입을 최소화**하면서 고품질 데이터를 효율적으로 생성하는 방법에 대한 연구가 중요하며, **합성 데이터 생성 및 검증** 과정의 비용 효율성 또한 고려되어야 합니다.  **다양한 평가 지표**를 활용한 객관적인 성능 측정과, 실제 응용 환경에서의 모델 성능 검증을 통해 LLM 데이터셋 연구의 실효성을 높일 수 있습니다.

#### Compression-Based Gen
압축 기반 생성(Compression-Based Gen) 방법은 **장문의 텍스트 데이터를 효율적으로 처리**하기 위한 핵심 전략입니다.  이는 긴 문맥을 요구하는 작업에서 **LLM의 성능 저하 문제를 해결**하는 데 중요합니다.  **본 논문은 압축된 중간 표현** (예: 장 요약, 장 개요)을 활용하여 LLM이 장문 데이터에서 효과적으로 추론하고, **인공지능이 생성한 데이터의 질을 높이고, 생성 비용을 절감**할 수 있음을 보여줍니다.  단순히 원본 텍스트를 사용하는 것보다 훨씬 **정확하고, 근거가 명확하며, 복잡한 질문에도 잘 대응**하는 데이터 생성이 가능해짐을 실험적으로 증명합니다.  **압축 전략의 효과는 장문 데이터를 처리하는 LLM의 한계를 극복**하는 데 중요하며, **고품질 합성 데이터 생성을 위한 새로운 방향**을 제시합니다.  향후 연구는 더욱 확장된 모델과 다양한 과제에 대한 적용 가능성을 탐색하는 데 초점을 맞춰야 합니다.

#### CLIPPER Pipeline Eval
CLIPPER 파이프라인 평가는 **합성 데이터 생성 과정의 각 단계(압축, 클레임 생성, 검증)의 성능과 품질을 다각적으로 분석**하는 것을 의미합니다.  **단순 정확도 측정을 넘어, 생성된 클레임의 타당성, 근거의 명확성, 그리고 복잡도까지 고려**하여 종합적인 평가를 수행했을 것입니다.  특히, **기존의 단순 접근 방식(NAÏVE)과의 비교 분석을 통해 CLIPPER의 효율성과 우수성을 입증**하려 했을 것이며, 이를 위해 다양한 지표(정확도, 오류 유형 분류, 비용 분석 등)를 활용했을 것으로 예상됩니다.  **다양한 규모의 언어 모델에 대한 파인튜닝 결과를 통해 CLIPPER가 장문 추론 능력 향상에 미치는 영향을 실험적으로 검증**하는 과정 또한 포함되었을 것입니다.  **데이터셋의 품질과 모델 성능 간의 상관관계 분석을 통해, CLIPPER의 데이터 생성 전략의 유효성을 뒷받침**하는 결과를 제시했을 가능성이 높습니다.  전반적으로, CLIPPER 파이프라인 평가는 정량적, 정성적 분석을 종합하여 CLIPPER의 실용성과 효과를 객관적으로 제시하는 데 초점을 맞추었을 것으로 예상됩니다.

#### Finetuning & Analysis
본 논문의 "미세조정 및 분석" 부분은 **합성 데이터셋을 사용한 LLM 미세조정의 효과**를 심층적으로 다룹니다.  **CLIPPER 데이터셋을 이용한 세 가지 모델(ProLong, Llama, Qwen)의 미세조정 결과**를 제시하며, **기존 모델 대비 성능 향상**을 보여줍니다. 특히 장문 추론 과제에서의 성능 향상이 두드러지며,  **NarrativeQA, MuSR 등 다른 관련 과제에서의 성능 향상**도 확인됩니다. 단순히 성능 수치만 제시하는 것이 아니라, **미세조정 전후의 추론 과정(Chain-of-Thought)의 질적 변화**, **데이터셋의 특징(claim scope, data length)**에 따른 성능 변화 등을 분석하여 **모델 성능 향상의 원인과 한계**를 밝히려는 시도가 돋보입니다.  **데이터셋의 질적 측면을 정량적으로 평가**하고, **모델의 강점과 약점**을 구체적으로 분석하는 부분은 연구의 신뢰도를 높입니다. 하지만,  **모델 크기의 한계**와 **특정 과제에 대한 편향성** 등은 추가 연구가 필요함을 시사합니다.

#### Future Work & Limits
본 논문은 장문 맥락 추론을 위한 합성 데이터 생성에 있어 압축 기반 접근 방식인 CLIPPER를 제시합니다.  **미래 연구 방향**으로는, **더욱 크고 복잡한 모델에 대한 CLIPPER 파이프라인의 적용**을 통해 성능 향상을 도모하는 것이 중요합니다.  **현재 모델의 한계점**은 긴 문맥을 다루는 데 어려움을 겪고, **합성 데이터의 한계**로 인해 실제 인간이 작성한 데이터셋과의 성능 차이를 완전히 해소하지 못하는 점입니다. 따라서 **다양한 유형의 장문 데이터를 활용한 추가 실험**을 통해 모델의 일반화 성능을 높이고, **인간의 추론 능력과 더욱 근접한 합성 데이터 생성 전략**을 모색해야 합니다. 또한, **CLIPPER의 효율성을 높이는 연구**와 **다양한 하이퍼파라미터 조정**을 통한 최적화 방안을 탐구하는 것도 중요합니다.


### More visual insights




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Models | CLIPPER-test | NoCha | NarrativeQA | Bench QA | MuSR |
|---|---|---|---|---|---| 
| Qwen2.5-7B-Instruct | 51.0% | 24.1% | 40.3% | 35.3% | 41.2% |
| Llama-3.1-8B-Instruct | 27.9% | 16.5% | 47.7% | 47.8% | 40.3% |
| ProLong-512K-8B-Instruct | 34.5% | 16.9% | 44.0% | 42.6% | 42.3% |
| ![https://arxiv.org/html/2502.14854/assets/graphics/elmo-clipper.png](https://arxiv.org/html/2502.14854/assets/graphics/elmo-clipper.png) Qwen2.5-7B-CLIPPER | 73.9% | 32.4% | 46.0% | 42.3% | 45.2% |
| ![https://arxiv.org/html/2502.14854/assets/graphics/elmo-clipper.png](https://arxiv.org/html/2502.14854/assets/graphics/elmo-clipper.png) Llama-3.1-8B-CLIPPER | 76.0% | 32.2% | 49.0% | 46.5% | 43.6% |
| ![https://arxiv.org/html/2502.14854/assets/graphics/elmo-clipper.png](https://arxiv.org/html/2502.14854/assets/graphics/elmo-clipper.png) ProLong-512K-8B-CLIPPER | 75.0% | 32.3% | 49.0% | 38.5% | 44.5% |
| ProLong-512K-8B-WritingPrompts | 63.0% | 24.1% | 31.0% | 35.8% | 45.2% |{{< /table-caption >}}
> 🔼 표 2는 CLIPPER 데이터셋을 사용하여 미세 조정된 언어 모델의 성능을 보여줍니다.  CLIPPER-test와 NoCha 벤치마크는 서술적 주장 검증 작업에서의 정확도를 측정합니다. NarrativeQA, ∞Bench QA, MuSR 벤치마크는 서술 이해 능력을 평가합니다.  표에서 알 수 있듯이, CLIPPER 데이터셋으로 미세 조정한 모델은 주장 검증 및 서술 이해 작업 모두에서 성능이 향상됨을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Model accuracy on claim verification (CLIPPER-test, NoCha) and narrative understanding benchmarks (NarrativeQA, ∞\infty∞Bench QA, MuSR). Finetuning models using CLIPPER improves performance on claim verification and narrative understanding.
> </details>

{{< table-caption >}}
| Claim: | "Jacques consistently uses pastoral themes to express his love for Belle-bouche, first through metaphorical discussions of shepherds and shepherdesses, and later while walking through an orchard and discussing Arcadian lovers." |{{< /table-caption >}}
> 🔼 표 3은 John Esten Cooke의 저서인 'The Youth of Jefferson'의 주장에 대해 Llama-Instruct와 Llama-CLIPPER가 생성한 Chain of Thought(CoT) 응답을 비교한 것입니다. Llama-CLIPPER의 CoT 응답에는 Llama-Instruct의 응답보다 더 많은 명시적인 장 참조(녹색으로 강조 표시)와 세부 정보가 포함되어 있습니다. 이는 CLIPPER가 생성한 합성 데이터를 사용하여 미세 조정한 모델이 더욱 구체적이고 근거 있는 설명을 생성할 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Comparison of CoT responses produced by Llama-Instruct and Llama-CLIPPER for a claim from John Esten Cooke’s The Youth of Jefferson. Llama-CLIPPER’s CoT response contains more explicit chapter references (highlighed in green) and details compared to that of Llama-Instruct (highlighted in red).
> </details>

{{< table-caption >}}
| Model | Chain of Thought (CoT)                                                                                                                                                                                                                                 | Answer |
|---|---|---|
| Llama-Instruct | "The statement claims that Jacques consistently uses pastoral themes to express his love for Belle-bouche. To evaluate this statement, we need to examine the text and identify instances where Jacques uses pastoral themes to express his love for Belle-bouche. The text mentions that Jacques discusses crooks, flowers, and shepherdesses with Belle-bouche, and later, while walking through an orchard, he talks about Arcadian lovers, specifically mentioning Strephon, Chloe, Corydon, Daphnis, and Narcissus. These instances suggest that Jacques does use pastoral themes to express his love for Belle-bouche. However, we need to consider whether this is a consistent pattern throughout the text."  Answer: TRUE | TRUE |
| Llama-CLIPPER | "Here are the relevant details from the text:  • Chapter 2: Jacques engages in a metaphorical discussion about shepherds and shepherdesses, expressing his love for Belle-bouche.  • Chapter 17: Jacques and Belle-bouche walk through the orchard, discussing the twentieth of May as a day for lovers.  • Relationship: Recurring theme of pastoral love In Chapter 2, Jacques engages in a metaphorical discussion about shepherds and shepherdesses to express his love for Belle-bouche. This theme continues in Chapter 17, where Jacques and Belle-bouche walk through an orchard, discussing the twentieth of May as a day for lovers. This connection shows Jacques’ consistent use of pastoral imagery to convey his romantic feelings for Belle-bouche throughout the story." Answer: TRUE | TRUE |{{< /table-caption >}}
> 🔼 이 표는 잘못된 주장을 사실로 잘못 분류하는 원인이 되는 변화 유형을 보여줍니다. 참과 거짓 주장에서 해당 내용은 각각 녹색과 빨간색으로 강조 표시되어 있습니다. 일부 주장은 여러 가지 범주에 속하기 때문에 빈도의 합계가 100%가 아닙니다. 각 범주의 자세한 정의는 부록의 오류 분석 섹션에서 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: A taxonomy of perturbations that cause a false claim to be misclassified as true. Corresponding details in true and false claims are respectively highlighed in green and red. Frequencies do not sum to 100%, as some claims receive multiple labels. Category definitions and more detailed analysis in §LABEL:appendix:error-analysis.
> </details>

{{< table-caption >}}
| Category | Freq (%) | True Claim | False Claim |
|---|---|---|---| 
| Event | 43.2 | The Polaris unit, initially assigned to test a new audio transmitter on Tara, explores the planet’s surface using a jet boat without landing. | The Polaris unit, initially assigned to test a new audio transmitter on Tara, explores the planet’s surface by landing their spaceship. |
| Person | 31.6 | The cattle herd stolen from Yeager by masked rustlers is later found in General Pasquale’s possession at Noche Buena. | The cattle herd stolen from Yeager by masked rustlers is later found in Harrison’s possession at Noche Buena. |
| Object | 15.8 | The alien structure Ross enters contains both a chamber with a jelly-like bed and a control panel capable of communicating with other alien vessels. | The alien structure Ross enters contains both a chamber with a metal bed and a control panel capable of time travel. |
| Location | 13.7 | Costigan rescues Clio twice: first from Roger on his planetoid, and later from a Nevian city using a stolen space-speedster. | Costigan rescues Clio twice: first from Roger on his planetoid, and later from a Triplanetary city using a stolen space-speedster. |
| Time | 6.3 | Jean Briggerland’s meeting with ex-convicts Mr. Hoggins and Mr. Talmot, where she suggests a burglary target, follows a failed attempt on Lydia’s life involving a speeding car on the sidewalk. | Jean Briggerland’s meeting with ex-convicts Mr. Hoggins and Mr. Talmot, where she suggests a burglary target, precedes a failed attempt on Lydia’s life involving a speeding car on the sidewalk. |
| Affect | 4.2 | David Mullins, who initially expresses skepticism about Chester’s hiring, later fires Chester on false pretenses and immediately replaces him with Felix. | David Mullins, who initially expresses enthusiasm about Chester’s hiring, later fires Chester on false pretenses and immediately replaces him with Felix. |{{< /table-caption >}}
> 🔼 이 표는 수동 분석에 사용된 6권의 책 목록을 보여줍니다.  연구자들이 책 내용에 익숙하여 수동 검증 과정을 용이하게 하기 위해 해당 책들이 선택되었습니다.  표에는 각 책의 제목, 저자, 출판연도, 토큰 수, 장 수가 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Six books used in our manual analysis. Books are chosen due to familiarity with the content.
> </details>

{{< table-caption >}}
| Title | Author | Publication Year | Number of Tokens | Number of Chapters |
|---|---|---|---|---|
| Anne of the Island | L. M. Montgomery | 1915 | 111,337 | 41 |
| Alice in Wonderland | Lewis Carroll | 1865 | 36,691 | 12 |
| The Murder of Roger Ackroyd | Agatha Christie | 1926 | 98,602 | 27 |
| The Picture of Dorian Gray | Oscar Wilde | 1890 | 105368 | 20 |
| Frankenstein | Mary Shelley | 1818 | 97,574 | 24 |
| The Adventures of Tom Sawyer | Mark Twain | 1876 | 97,968 | 35 |{{< /table-caption >}}
> 🔼 표 6은 CLIPPER의 테스트 세트에 대한 정확도를 보여줍니다.  '책 본문 포함' 열은 모델이 책의 전체 본문과 함께 질문을 받았을 때의 정확도를 나타내고, '책 본문 미포함' 열은 책 본문 없이 질문만 받았을 때의 정확도를 나타냅니다. 이는 모델이 주어진 맥락에 얼마나 의존하는지, 그리고 긴 문맥 내 추론 능력이 얼마나 중요한지를 보여주는 지표입니다.  책 본문이 없을 경우 모델의 성능이 크게 저하되는 것을 통해 긴 문맥 내 추론 작업에서 책 본문의 중요성을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Accuracy on CLIPPER’s test set (with and without book texts).
> </details>

{{< table-caption >}}
| Models | No Text | With Text |
|---|---|---|
| ProLong-Instruct | 0.0% | 35.6% |
| Llama-Instruct | 0.0% | 32.8% |
| Qwen-Instruct | 0.0% | 51.4% |{{< /table-caption >}}
> 🔼 표 7은 CLIPPER의 테스트 세트에 대한 정확도를 보여줍니다. 이 표는 모델이 책의 본문이나 메타데이터 없이도 주어진 질문에 대해 얼마나 정확하게 답변하는지를 보여줍니다.  즉, 모델이 단순히 암기가 아닌 실제 추론 능력을 바탕으로 답변하는지 평가하기 위한 실험 결과입니다.  각 모델별로 True/False 문제에 대한 정확도를 제시하고 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Accuracy on CLIPPER’s test set (no book text or metadata provided).
> </details>

{{< table-caption >}}
| Models | Before SFT | After SFT |
|---|---|---|
| ProLong-Instruct | 0.0% | 25.2% |
| Llama-Instruct | 20.2% | 13.8% |
| Qwen-Instruct | 21.7% | 22.9% |{{< /table-caption >}}
> 🔼 표 8은 합성 데이터 생성 파이프라인의 각 단계별 비용을 보여줍니다.  단계별 비용은 각 단계를 수행하는 데 사용된 LLM (GPT-4 또는 Claude)의 토큰 수와 가격을 기반으로 계산되었습니다.  각 단계의 비용은 미국 달러로 표시되며 소수점 넷째 자리까지 반올림되었습니다.  이 표는 합성 데이터 생성에 드는 총 비용을 파악하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Cost to run pipeline per claim (in US dollars, rounded to four decimal places).
> </details>

{{< table-caption >}}
| Stage | Cost |
|---|---| 
| Book summary generation | $0.0021 |
| Chapter outline generation | $0.0107 |
| Book-level claim synthesis | $0.0129 |
| Chapter-level claim synthesis | $0.0172 |
| Deduplication | $0.0021 |
| Verification | $0.0064 |
| Total | $0.0514 |{{< /table-caption >}}
> 🔼 표 9는 논문에서 제시된 NAÏVE 방법과 CLIPPER 방법의 추정 비용을 소수점 둘째 자리까지 반올림하여 보여줍니다.  NAÏVE 방법은 책 전체 텍스트를 사용하여 주장을 생성하는 반면, CLIPPER 방법은 책을 요약 및 개요로 압축하여 주장을 생성합니다. 이 표는 각 방법의 책 수준 주장과 장 수준 주장 생성에 대한 비용을 비교하여 CLIPPER 방법이 NAÏVE 방법보다 비용 효율적임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Estimated cost for our NAÏVE vs CLIPPER approach (rounded to two decimal places)
> </details>

{{< table-caption >}}
|                     | NAÏVE | CLIPPER |
|---------------------|--------|---------|
| Cost per claim (book-level) | $0.09  | $0.07   |
| Cost per claim (chap-level) | $0.04  | $0.02   |{{< /table-caption >}}
> 🔼 표 10은 논문에서 사용된 각 프롬프트에 해당하는 그림의 번호를 보여줍니다.  즉, 각 프롬프트가 논문의 어떤 그림에 설명되어 있는지 보여주는 참조표입니다.  본 논문에서는 프롬프트 엔지니어링을 통해 합성 데이터셋을 생성하는데, 각 단계별 프롬프트를 시각적으로 이해하기 쉽도록 그림으로 나타내고 표 10에서는 이 그림들과 프롬프트의 매핑 관계를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Figure references for each prompt.
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