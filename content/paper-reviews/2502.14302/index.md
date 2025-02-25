---
title: "MedHallu: A Comprehensive Benchmark for Detecting Medical Hallucinations in Large Language Models"
summary: "MedHallu: 의료 LLM 환각 검출을 위한 포괄적 벤치마크"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 University of Texas at Austin",]
showSummary: true
date: 2025-02-20
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.14302 {{< /keyword >}}
{{< keyword icon="writer" >}} Shrey Pandit et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-24 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.14302" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.14302" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/medhallu-a-comprehensive-benchmark-for" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

의료 분야에서 대규모 언어 모델(LLM)의 정확성은 매우 중요합니다. 하지만 LLM은 사실이 아닌 그럴듯한 정보를 생성하는 '환각' 현상을 보입니다. 이는 의료 분야에서 심각한 위험을 초래할 수 있습니다.  기존의 환각 검출 벤치마크는 의료 도메인 특유의 어려움을 충분히 반영하지 못했습니다.

본 연구는 의료 환각 검출을 위한 새로운 벤치마크인 MedHallu를 제시합니다.  MedHallu는 PubMedQA 데이터셋을 기반으로 10,000개의 고품질 질의응답 쌍을 포함하며, 제어된 파이프라인을 통해 체계적으로 환각 답변을 생성합니다.  실험 결과, 최첨단 LLM도 어려운 환각 검출 과제에서 낮은 F1 점수를 보였습니다. 하지만, 도메인 특화 지식과 "확신하지 못함" 답변 옵션을 추가함으로써 정확도와 F1 점수가 크게 향상되었습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} MedHallu는 의료 환각 검출을 위한 최초의 벤치마크 데이터셋입니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 최첨단 LLM도 어려운 의료 환각 검출 과제를 해결하는 데 어려움을 겪습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 도메인 특화 지식과 "확신하지 못함" 옵션을 추가하면 정확도와 F1 점수가 향상됩니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**MedHallu**는 의료 분야에서 **대규모 언어 모델(LLM)**의 환각(hallucination) 문제를 해결하기 위한 중요한 **벤치마크**를 제공합니다.  이 논문은 의료 환각 검출의 어려움을 보여주고,  **도메인 특화 지식**을 통합하고 **"확신하지 못함" 옵션**을 도입하여 정확도를 향상시키는 방법을 제시합니다. 이는 **의료 AI 안전**을 높이고 **LLM 기반 의료 애플리케이션**의 신뢰성을 높이는 데 기여할 것입니다.  향후 연구를 위한 새로운 방향을 제시하며, 의료 자연어 처리(NLP) 분야에 중요한 기여를 합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.14302/x1.png)

> 🔼 그림 1은 의료 환각 검출의 한 예시를 보여줍니다. 질문과 답변이 주어지고, 모델이 답변이 의학적으로 정확한지 또는 환각(잘못된 정보)인지를 판단해야 합니다.  부록 K에는 환각 검출 작업에 사용된 자세한 프롬프트가 나와 있습니다.  이 예시는 의료 분야에서의 잘못된 정보 생성의 위험성을 강조하며, MedHallu 벤치마크가 해결하고자 하는 문제를 명확히 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: An example of medical hallucination detection. The detailed prompt used for the hallucination detection task is presented in Appendix K.
> </details>





{{< table-caption >}}
| Hallucination Category | Description | Example |
|---|---|---|
| Misinterpretation of Question | Misunderstanding the question, leading to an irrelevant response. | #Question#: Does high-dose vitamin C therapy improve survival rates in patients with sepsis? <br> #Answer#: Vitamin C is water-soluble vitamin that plays a role in immune function and collagen synthesis. |
| Incomplete Information | Stays on-topic but omits the essential details needed to fully answer the question. | #Question#: How does penicillin treat strep throat? <br> #Answer#: Penicillin kills bacteria. |
| Mechanism and Pathway Misattribution | False attribution of biological mechanisms, molecular pathways, or disease processes that contradicts established medical knowledge. | #Question#: What is the primary mechanism of action of aspirin in reducing inflammation? <br> #Answer#: Aspirin primarily reduces inflammation by blocking calcium channels in immune cells, which prevents the release of histamine and directly suppresses T-cell activation. |
| Methodological and Evidence Fabrication | Inventing false research methods, statistical data, or specific clinical outcomes. | #Question#: What is the success rate of ACL reconstruction surgery? <br> #Answer#: Recent clinical trials using quantum-guided surgical technique showed 99.7% success rate across 10,543 patients with zero complications when using gold-infused synthetic grafts. |{{< /table-caption >}}

> 🔼 MedHallu 데이터셋 생성에 사용된 의학적 환각의 종류를 보여주는 표입니다. KnowHallu 벤치마크(Zhang et al., 2024a)에서 수정 및 의학 분야에 맞게 조정된 범주들을 기반으로 합니다.  각 범주는 질문 오해, 정보 부족, 메커니즘 및 경로 오류 지정, 방법론 및 증거 조작 등 환각 유형에 대한 설명과 예시를 포함합니다. 부록 D에는 자세한 내용이 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Categories of medical hallucinations used to generate the MedHalu dataset. Adapted from the KnowHallu benchmark (Zhang et al., 2024a) with revised categories tailored to the medical domain (Appendix D).
> </details>





### In-depth insights


#### MedHallu Dataset
MedHallu 데이터셋은 의료 분야의 대규모 언어 모델(LLM) 환각(hallucination) 검출을 위한 **종합적인 벤치마크**를 제공하는 핵심 요소입니다. **10,000개의 고품질 질의응답 쌍**으로 구성되어 있으며, PubMedQA 데이터셋을 기반으로 하여 체계적인 파이프라인을 통해 생성된 환각 응답들을 포함합니다. **난이도(쉬움, 중간, 어려움)**에 따라 계층화되어 있어 모델의 성능을 세분화하여 평가할 수 있게 합니다. 또한, 환각 유형(질문 오해, 정보 누락, 메커니즘 오류, 증거 조작)을 분류하여 다양한 유형의 환각에 대한 모델의 취약성을 분석할 수 있습니다. 이러한 특징들은 MedHallu 데이터셋이 **의료 LLM의 신뢰성과 안전성 향상**에 크게 기여할 수 있음을 시사합니다. 특히, 의료 분야의 특수성을 고려한 데이터셋 구성은 기존의 일반적인 환각 검출 벤치마크의 한계를 극복하고, **의료 환경에 특화된 LLM 개발 및 평가**에 중요한 역할을 할 것으로 예상됩니다.

#### Hallucination Types
의료 환경에서의 대규모 언어 모델(LLM)의 환각 현상 유형을 분석하는 것은 매우 중요합니다. **환각의 유형을 명확히 구분하는 것은 환각을 감지하고 완화하기 위한 전략을 개발하는 데 필수적입니다.** 이는 환각의 근본 원인과 메커니즘에 대한 이해를 필요로 합니다.  예를 들어, 질문 오해는 모델이 질문의 의도를 잘못 해석하여 사실과 다른 답변을 생성하는 경우를 말합니다. 반면, 불완전한 정보는 모델이 관련 정보의 일부만 제공하거나 중요한 세부 정보를 누락하여 부정확한 응답을 만드는 경우입니다. 메커니즘 및 경로 오류 지정은 생물학적 메커니즘, 분자 경로 또는 질병 과정에 대한 잘못된 설명을 포함하며, 방법론적 및 증거 조작은 허위 연구 방법, 통계 데이터 또는 특정 임상 결과를 만들어내는 경우를 의미합니다. **각 유형은 모델의 한계와 훈련 데이터의 편향성을 반영하며, 이러한 이해는 보다 정확하고 안전한 의료 LLM 개발에 중요한 역할을 합니다.** 따라서, 환각 유형에 대한 심층적인 연구는 의료 환경에서 LLM의 신뢰성과 안전성을 향상시키는 데 크게 기여할 것입니다.  **의료 환경의 특수성을 고려한 환각 유형 분류 체계를 개발하고, 각 유형에 대한 구체적인 예시 및 해결 방안을 제시하는 것이 중요한 연구 방향**입니다.

#### LLM Evaluation
LLM 평가는 **모델의 성능과 안전성을 측정하는 데 필수적**입니다.  기존의 방식들은 종종 단순 정확도에만 초점을 맞춰, **환각(hallucination)과 같은 중요한 문제점들을 간과**하는 경향이 있었습니다.  **의료 분야에서는 특히 환각으로 인한 위험성이 크기 때문에**, 의료 지식에 특화된 데이터셋을 사용한 평가가 중요합니다.  **의료 전문가의 검토를 거친 고품질 데이터셋**을 활용하고, **다양한 측면(정확성, 안전성, 효율성 등)을 종합적으로 고려**하는 평가 지표를 개발해야 합니다.  **단순 정확도 뿐 아니라, 환각 발생률, 신뢰도, 설명 가능성 등을 함께 평가**하여 실제 의료 현장 적용 가능성을 보다 정확하게 판단할 수 있습니다.  또한, **의료 전문가의 피드백을 지속적으로 반영**하여 LLM 평가 방법을 개선해나가는 것이 중요합니다.  궁극적으로 **인간의 감독과 협력을 통해 안전하고 신뢰할 수 있는 의료 LLM을 개발**하는 데 기여해야 합니다.

#### Knowledge Impact
본 논문에서 "지식의 영향"에 대한 심층적인 분석은 **의료 분야의 대규모 언어 모델(LLM) 성능 향상**에 중점을 둡니다.  **전문 지식을 LLM에 제공**하면 의료 환각 검출 성능이 크게 향상되는 것을 보여줍니다. 특히 일반적인 LLM은 의료 전문 LLM보다 지식 활용 측면에서 더 큰 성능 향상을 보입니다. 이는 일반 LLM이 의료 전문 지식에 대한 사전 학습이 부족하기 때문에, 추가적인 지식이 주어졌을 때 더 큰 학습 효과를 보이는 것으로 해석할 수 있습니다.  **의료 전문 지식의 통합**은 모델의 정확성과 재현율을 높이는 데 중요한 역할을 하며, 특히 어려운 환각 사례에 대한 판별 능력을 향상시킵니다.  하지만, 모델 크기와 지식 활용 간 상관관계는 단순하지 않아, 모델 규모에 따라 지식 활용의 효과가 다르게 나타날 수 있다는 점을 시사합니다.  **"not sure" 옵션 추가**는 모델의 정밀도 향상에 기여하며, 특히 의료 분야의 높은 신뢰도 요구사항을 충족하는 데 중요한 역할을 합니다.

#### Future Work
본 논문은 의료 환자의 안전과 임상적 의사결정에 있어서 **의료 환각(medical hallucination)** 문제를 해결하기 위한 중요한 첫걸음을 제시합니다.  하지만, 아직 해결해야 할 과제들이 남아있습니다. 미래 연구 방향으로는 **다양한 고품질 의료 데이터셋 확보**를 통한 모델의 일반화 성능 향상이 중요합니다.  **의료 전문가의 지식을 효과적으로 통합**하는 방법에 대한 연구도 필요하며, **다양한 의료 분야에 대한 전문적인 지식을 갖춘 모델 개발** 및 **다양한 의료 환각 유형을 더욱 정교하게 분류하고 검출하는 기술 개발**도 필수적입니다. 또한, **모델의 신뢰성을 평가하는 새로운 지표 개발**과 **인공지능 모델의 안전성 및 윤리적인 사용**에 대한 연구가 병행되어야 할 것입니다.  특히, 의료 분야의 특수성을 고려한 **설명 가능한 인공지능(explainable AI)** 기술 개발을 통해 의료 현장에서의 신뢰도를 높이는 데 집중해야 할 것입니다.  **의료 환각 문제에 대한 심층적인 이해**를 기반으로 한 이러한 미래 연구는 의료 인공지능 기술의 발전과 안전한 활용에 크게 기여할 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.14302/x2.png)

> 🔼 그림 2는 MedHallu 의료 환각 답변 생성 파이프라인을 보여줍니다. PubMedQA 데이터셋의 각 질문-답변 쌍은 환각 답변을 생성하기 위해 다음 단계를 거칩니다. 1단계는 후보 생성 단계로, 질문, 관련 지식, 정답이 주어지면 LLM은 네 가지 환각 유형 중 하나에 맞춰 환각 답변을 생성하라는 프롬프트를 받습니다. 2단계는 등급 및 필터링 단계로, 생성된 답변은 품질 및 정확성 검사를 거치며, 필터링 결과에 따라 어려움(hard), 중간(medium), 쉬움(easy) 또는 실패(failed)로 분류됩니다. 3단계는 실패한 생성을 수정하는 단계로, 실패한 답변은 TextGrad (Yuksekgonul et al., 2024)를 사용하여 최적화되고 다시 필터링됩니다. 다시 실패하면 LLM은 새로운 답변을 생성하라는 프롬프트를 받습니다 (재생성). 4단계는 대체 단계로, 4번의 재생성 시도 후에도 적격 답변이 나타나지 않으면 정답과 가장 유사한 답변이 쉬운 환각 사례로 선택됩니다. 환각 생성 작업에 사용된 자세한 프롬프트는 부록 K에 나와 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: MedHallu medical hallucinated answer generation pipeline. Each question-answer pair from the PubMedQA dataset undergoes the following steps to generate a hallucinated answer: (1) Candidate Generation: Given a question, relevant knowledge, and ground truth answer, the LLM is prompted to generate a hallucinated answer adhering to one of four hallucination types. (2) Grading & Filtering: Generated answers undergo quality and correctness checks, being labeled as hard, medium, easy, or failed based on filtering results. (3) Refining Failed Generation: Failed answers are optimized using TextGrad Yuksekgonul et al. (2024) and re-filtered. If they fail again, the LLM is re-prompted to generate new answers (Regeneration). (4) Fallback: If no qualified answers emerge after four regeneration attempts, the answer most similar to the ground truth is selected as an easy hallucinated example. The detailed prompt used for hallucination generation task is presented in the Appendix K.
> </details>



![](https://arxiv.org/html/2502.14302/x3.png)

> 🔼 그림 3은 MedHallu 데이터셋의 통계를 보여줍니다.  데이터셋은 의료 환각의 네 가지 범주(표 1 참조)와 난이도(쉬움, 중간, 어려움)별로 분류되어 있습니다. 각 범주와 난이도에 속한 샘플 수를 시각적으로 보여주는 차트 형태로 표현되어, 데이터셋의 구성과 각 환각 유형 및 난이도의 분포를 한눈에 파악할 수 있도록 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Statistics of the MedHallu dataset categorized by four categories of hallucinations (see Table 1 for detailed definitions) and levels of difficulty (easy, medium, hard).
> </details>



![](https://arxiv.org/html/2502.14302/x4.png)

> 🔼 그림 4는 MedHallu 데이터셋에서 다양한 유형의 환각에 대한 Qwen2-7B-Instruct 모델의 검출 정확도를 보여줍니다. 각 환각 유형(질문 오해, 불완전한 정보, 메커니즘/경로 오류 지정, 방법론적 및 증거 조작)에 대한 정확도를 시각적으로 비교하여 어떤 유형의 환각이 더 쉽게 또는 어렵게 감지되는지 보여줍니다. 이는 모델의 환각 감지 성능을 평가하는 데 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Detection accuracy of different hallucination categories on MedHallu, evaluated using Qwen2-7B-Instruct as the discriminator.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Metric | Mean (fooled) | Mean (not fooled) | P-value |
|---|---|---|---| 
| Cosine similarity | 0.715 | 0.696 | 0.004 |
| Euclidean distance | 0.714 | 0.750 | 0.002 |
| Rouge1-F1 | 0.358 | 0.319 | 0.002 |{{< /table-caption >}}
> 🔼 표 2는 MedHallu 데이터셋(10,000개 샘플)을 사용하여 지식 유무에 따른 다양한 LLMs의 성능을 비교한 표입니다.  대부분의 지표에서 일반적인 LLMs가 의료 환각 탐지 작업에서 의료 전용으로 미세 조정된 LLMs보다 더 나은 성능을 보여줍니다.  '전체 정밀도(Overall P)'는 정밀도를 나타내며,  '지식 차이(Δ Knowledge)'는 지식이 제공되었을 때 전체 F1 점수의 변화량을 나타냅니다.  일반 LLM과 미세 조정된 의료 LLM의 크기를 공정하게 비교하기 위해 GPT-4o를 제외하고 평균을 계산했습니다. 자세한 실험 내용은 부록 E를 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Table 2: Performance comparison of different LLMs with and without knowledge on MedHallu (10,000 samples). General LLMs perform better than medically fine-tuned LLMs in the task of Medical Hallucination across most metrics. “Overall P” denotes precision, and “ΔΔ\Deltaroman_Δ Knowledge” is the performance change in overall F1 when knowledge is provided. ∗We exclude GPT-4o while calculating the average to have a fair comparison of model sizes for general vs. fine-tuned LLMs. Additional experimental details can be found in Appendix E.
> </details>

{{< table-caption >}}
| Model | F1<sub>NS</sub> | P<sub>NS</sub> | F1<sub>R</sub> | P<sub>R</sub> | Response% |
|---|---|---|---|---|---| 
| GPT-4o-mini | 66.6 | 66.8 | 60.7 | 77.2 | 98.4 |
| Gemma-2-2b-it | 57.1 | 59.9 | 55.3 | 54.1 | 82.7 |
| Llama-3.2-3B-Instruct | 58.1 | 68.7 | 49.9 | 63.3 | 85.9 |
| Qwen2.5-3B-Instruct | 65.2 | 67.2 | 60.6 | 50.2 | 65.7 |
| BioMistral-7B | 56.5 | 50.5 | 57.0 | 51.3 | 99.2 |
| Qwen2.5-7B-Instruct | 69.3 | **94.6** | 55.3 | 73.7 | 47.5 |
| OpenBioLLM-Llama3-8B | 48.8 | 48.4 | 48.4 | 56.3 | 99.7 |
| Llama-3.1-8B-UltraMedical | 58.5 | 49.1 | 61.9 | 56.4 | 69.7 |
| DeepSeek-R1-Llama-8B | 66.0 | 56.9 | 51.4 | 61.7 | 98.1 |
| Llama-3.1-8B-Instruct | 51.7 | 90.4 | 52.2 | **86.0** | 98.2 |
| Gemma-2-9b-it | 61.4 | 85.5 | 51.5 | 71.5 | 37.6 |
| Qwen2.5-14B-Instruct | 76.2 | 82.9 | 61.9 | 76.5 | 27.9 |
| GPT-4o | **79.5** | 79.6 | **73.7** | 72.4 | 33.9 |{{< /table-caption >}}
> 🔼 이 표는 5.3절에서 생성된 클러스터와 실제 정답 간의 평균 유사도를 보여줍니다.  검출 LLM을 속이는 샘플(즉, 검출하기 어려운 환각)을 포함하는 클러스터는 실제 정답과 상당히 가깝습니다.  유사도는 코사인 유사도, 유클리드 거리, Rouge-1 F1 점수 세 가지 지표로 측정되어, 어려운 환각일수록 실제 정답과 의미적으로 더 가깝다는 것을 보여줍니다. 이는 어려운 환각이 실제 정답과 의미적으로 유사하지만 사실과는 다른 세부 사항을 포함하고 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: The average similarity between the clusters generated in Section 5.3 and the ground truth samples. Clusters containing samples that fool detection LLMs (i.e., hallucinations that are more challenging to detect) are notably closer to the ground truth.
> </details>

{{< table-caption >}}
| Model | F1<sub>NS</sub> | P<sub>NS</sub> | F1<sub>R</sub> | P<sub>R</sub> | Response % |
|---|---|---|---|---|---| 
| GPT-4o-mini | 83.6 | 77.7 | 84.1 | 82.0 | 100.0 |
| Gemma-2-2b-it | 75.5 | 67.2 | 71.5 | 67.4 | 89.2 |
| Llama-3.2-3B-Instruct | 76.8 | 67.9 | 73.4 | 55.5 | 90.8 |
| Qwen2.5-3B-Instruct | 69.2 | 47.0 | 67.6 | 49.8 | 94.2 |
| BioMistral-7B | 67.2 | 53.2 | 64.8 | 54.5 | 98.7 |
| Qwen2.5-7B-Instruct | 88.6 | 91.6 | 83.9 | 85.0 | 74.6 |
| OpenBioLLM-Llama3-8B | 40.2 | 58.9 | 42.4 | 55.5 | 99.4 |
| Llama-3.1-8B-UltraMedical | 72.9 | 56.1 | 77.3 | 73.4 | 95.1 |
| DeepSeek-R1-Llama-8B | 68.9 | 85.4 | 81.2 | 83.4 | 95.2 |
| Llama-3.1-8B-Instruct | 77.7 | **92.7** | 80.0 | **88.6** | 99.7 |
| Gemma-2-9b-it | 84.7 | 83.4 | 83.8 | 78.6 | 90.3 |
| Qwen2.5-14B-Instruct | **88.8** | 92.5 | 85.2 | 84.3 | 87.0 |
| GPT-4o | 84.9 | 78.3 | **87.7** | 88.3 | 95.2 |{{< /table-caption >}}
> 🔼 표 4는 모델이 '잘 모르겠습니다' 옵션을 사용할 수 있을 때와 답변을 해야 할 때의 성능을 보여줍니다. F1NS와 PNS(정밀도)는 '잘 모르겠습니다' 옵션이 있을 때의 성능을 나타내고, F1R과 PR(정밀도)는 답변해야 할 때의 성능을 나타냅니다. Response%는 '잘 모르겠습니다' 옵션이 있어도 '예' 또는 '아니오'로 답변한 질문의 비율을 나타냅니다.  즉, '잘 모르겠습니다' 옵션이 있음에도 불구하고 모델이 확신을 가지고 답변을 했는지, 아니면 '잘 모르겠습니다' 옵션을 얼마나 활용했는지를 보여주는 지표입니다.
> <details>
> <summary>read the caption</summary>
> Table 4: F1NS and PNS (Precision) represent performance with the “Not Sure” option, while F1R and PR (Precision) represent performance when required to answer. Response% represents the percentage of questions answered with “Yes” or “No” even when the “Not Sure” option is available.
> </details>

{{< table-caption >}}
| Computational Budget and Infrastructure Details while generating MedHallu |
|---|---| 
| **Primary Model:** | Qwen2.5-14B (14B parameters) |
| **Computation Time:** | 26.5 hours |
| **GPU Hardware:** | 4 x NVIDIA RTX A6000 (48,685 MiB RAM each) |
| **Additional Models:** | Gemma2-9B (9B parameters), Qwen2.5-7B (7B parameters), GPT4omini (used for correctness check) |
| **Dataset Size:** | 10,000 samples |{{< /table-caption >}}
> 🔼 표 5는 '확신하지 못함' 옵션을 사용했을 때의 F1 점수(F1NS)와 정밀도(PNS), 그리고 답변해야 할 경우의 F1 점수(F1R)와 정밀도(PR)를 보여줍니다. Response%는 '예' 또는 '아니오'로 답변해야 하는 질문의 비율을 나타내며, '확신하지 못함' 옵션이 있더라도 '예' 또는 '아니오'로만 답변한 질문의 비율을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 5:  F1NS and PNS (Precision) represent performance with the “Not Sure” option, while F1R and PR represent performance when required to answer. Response% represents the percentage of questions answered with “Yes” or “No” even when the “Not Sure” option is available.
> </details>

{{< table-caption >}}
| Pre-trained Models and huggingface names |
|---|---| 
| `m42-health/Llama3-Med42-8B` |
| `OpenMeditron/Meditron3-8B` |
| `aaditya/OpenBioLLM-Llama3-8B` |
| `BioMistral/BioMistral-7B` |
| `TsinghuaC3I/Llama-3.1-8B-UltraMedical` |
| `deepseek-ai/DeepSeek-R1-Distill-Llama-8B` |
| `Qwen/Qwen2.5-14B-Instruct` |
| `google/gemma-2-2b-it` |
| `google/gemma-2-9b-it` |
| `meta-llama/Llama-3.1-8B-Instruct` |
| `meta-llama/Llama-3.2-3B-Instruct` |
| `Qwen/Qwen2.5-7B-Instruct` |
| `Qwen/Qwen2.5-3B-Instruct` |{{< /table-caption >}}
> 🔼 표 6은 MedHallu 데이터셋 생성에 사용된 컴퓨팅 자원과 인프라에 대한 세부 정보를 보여줍니다.  여기에는 생성 모델(Qwen2.5-14B)의 컴퓨팅 시간(26.5시간), 사용된 GPU 하드웨어(4개의 NVIDIA RTX A6000), 생성된 데이터셋의 크기(10,000개 샘플) 등이 포함됩니다.  추가적으로, 정확도 검증을 위해 사용된 추가 모델(Gemma2-9B, Qwen2.5-7B, GPT4omini)의 매개변수 수도 명시되어 있습니다.  하지만, 실제 성능 벤치마킹을 위해 사용된 판별 모델들은 포함되어 있지 않습니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Computational Budget and Infrastructure Details while generating MedHallu Dataset, not includes the discriminator models used in benchmarking.
> </details>

{{< table-caption >}}
| Question | Category of Hallucination | Ground Truth | Hallucinated Example | Difficulty |
|---|---|---|---|---|
| Do mitochondria play a role in remodelling lace plant leaves during programmed cell death? | Mechanism and Pathway Misattribution | This is the first report of mitochondria and chloroplasts moving on transvacuolar strands to form a ring structure surrounding the nucleus during developmental PCD. Also, for the first time, we have shown the feasibility for the use of CsA in a whole plant system. Overall, our findings implicate the mitochondria as playing a critical and early role in developmentally regulated PCD in the lace plant. | Mitochondria regulate the formation of perforations in lace plant leaves through the modulation of calcium channels and by activating specific proteases that degrade cellular structures, facilitating the PCD process. | Medium |
| Differentiation of nonalcoholic from alcoholic steatohepatitis: are routine laboratory markers useful? | Misinterpretation of #Question# | Higher MCVs and AST/ALT ratios in ASH reflect the severity of underlying liver disease and do not differentiate NASH from ASH. Instead, these biomarkers might prove useful in guiding selection of patients for liver biopsy and in targeting therapy. | Routine laboratory markers, particularly mean corpuscular volume (MCV) and AST/ALT ratios, significantly aid in differentiating various types of nonalcoholic steatohepatitis (NASH). | Hard |
| Amblyopia: is visual loss permanent? | Incomplete Information | Older people with a history of amblyopia who develop visual loss in the previously normal eye can experience recovery of visual function in the amblyopic eye over a period of time. This recovery in visual function occurs in the wake of visual loss in the fellow eye and the improvement appears to be sustained. | Visual loss due to amblyopia is permanent unless treated with early intervention during childhood. | Hard |{{< /table-caption >}}
> 🔼 이 표는 실험에 사용된 사전 훈련된 언어 모델들의 목록과 해당 모델들의 허깅페이스(Hugging Face) 이름을 보여줍니다.  논문의 실험 부분에서 다양한 모델들의 성능을 비교 분석하는 데 사용되었으며, 각 모델의 이름과 허깅페이스에서 접근 가능한 고유 식별자를 명확히 제시하여 재현성을 높입니다.
> <details>
> <summary>read the caption</summary>
> Table 7: List of pre-trained models with their huggingface names used in our experiments.
> </details>

{{< table-caption >}}
| Question: | Prognosis of well differentiated small hepatocellular carcinoma–is well differentiated hepatocellular carcinoma clinically early cancer? |
|---|---| 
| Ground Truth Answer: | W-d HCCs were clinically demonstrated not to be early cancer, because there was no significant difference in disease free survival between the patients with w-d and l-d HCCs. |
| Cluster 1 (Fooling) |  1. W-d HCCs are indeed clinically early cancer, due to their smaller size and lower incidence of fibrous capsule formation. 
2. W-d HCCs were clinically demonstrated to be early cancer due to their smaller tumor size and lower incidence of fibrous capsule formation. 
3. Well-differentiated small hepatocellular carcinoma is indeed early cancer, due to its slow growth rate. 
4. Well-differentiated hepatocellular carcinoma is clinically early cancer due to its low aggressive nature. 
5. Well differentiated hepatocellular carcinoma appears to be clinically early cancer due to its low aggressiveness. |
| Cluster 2 (That didn’t fool) | 1. Well-differentiated hepatocellular carcinoma (HCC) is clinically early cancer due to its high histological grade. 
2. Due to its high histological grade, well-differentiated hepatocellular carcinoma (HCC) is considered clinically early cancer. |
| Cluster 3 (Fooling) | 1. Well-differentiated hepatocellular carcinoma is indeed an early cancer, as it often lacks fibrous capsule formation. 
2. Well-differentiated hepatocellular carcinomas (HCCs) are clinically early cancers due to their low incidence of fibrous capsule formation. |{{< /table-caption >}}
> 🔼 표 8은 Gemma2-9B-it 모델을 사용하여 생성된 MedHallu 데이터셋의 일부(pqa_labeled에서 1,000개 샘플)에 대한 성능 평가 결과를 보여줍니다. 다양한 언어 모델(LLM)에 대해 두 가지 조건(외부 지식 없음, 외부 지식 있음)에서 전체 F1 점수, 정밀도, Easy/Medium/Hard F1 점수 등의 성능 지표에 대한 평균 ± 표준 편차를 나타냅니다. 마지막 열(Δ F1)은 지식이 있을 때와 없을 때의 F1 점수 차이를 보여줍니다. 이 표는 외부 지식이 LLM의 의학적 환각 탐지 성능에 미치는 영향을 분석하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Medhallu data generated by Gemma2-9B-it (1,000 samples of pqa_labeled). Mean ±plus-or-minus\pm± standard deviation of performance metrics (Overall F1, Overall Precision, Easy/Medium/Hard F1) for various LLMs under two conditions: without and with external knowledge. The final column (ΔΔ\Deltaroman_Δ F1) shows the difference in F1 scores (with knowledge minus without knowledge).
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
{{< /gallery >}}