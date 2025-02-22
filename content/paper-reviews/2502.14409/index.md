---
title: "Unstructured Evidence Attribution for Long Context Query Focused Summarization"
summary: "장문 컨텍스트 질의 중심 요약에서 LLM의 위치 편향을 완화하고, 비정형 증거 인용의 정확성과 신뢰성을 높이는 새로운 합성 데이터셋(SUnsET) 및 미세 조정 기법을 제시합니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Text Summarization", "🏢 University of Michigan",]
showSummary: true
date: 2025-02-20
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.14409 {{< /keyword >}}
{{< keyword icon="writer" >}} Dustin Wright et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-21 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.14409" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.14409" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/unstructured-evidence-attribution-for-long" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)은 장문 컨텍스트에서 질의 중심 요약을 생성하는 데 탁월하지만, **투명성과 신뢰성 부족**이라는 문제점을 가지고 있습니다. 특히, LLM은 정보의 위치에 편향되어 중요한 내용을 놓치거나 잘못 인용하는 경우가 많습니다.  기존 연구는 주로 구조화된 증거 인용에 초점을 맞춰왔기 때문에, **비정형 증거 인용**에 대한 연구는 부족했습니다. 

본 연구는 이러한 문제를 해결하기 위해 **새로운 합성 데이터셋(SUnsET)**을 제시합니다.  SUnsET은 다양한 유형의 문서를 포함하며, 모델이 비정형 증거를 추출하고 인용하는 방법을 학습하는 데 사용됩니다. 실험 결과, SUnsET을 이용하여 미세 조정된 LLM은 기존 모델보다 **더 정확하고 일관성 있는 증거를 추출**하며, **요약의 질도 향상**됨을 보였습니다.  이는 장문 컨텍스트 요약의 신뢰성과 설명 가능성을 높이는 데 기여할 것으로 예상됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 새로운 합성 데이터셋 SUnsET을 이용하여 LLM의 위치 편향 문제를 완화하고, 비정형 증거 인용의 정확성을 높였습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 장문 컨텍스트 요약에서 비정형 증거를 효과적으로 추출하고 인용하는 방법을 제시했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 제안된 방법은 다양한 문서 유형과 길이에 대해 성능 향상을 보였으며, 요약의 질적 향상을 가져왔습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **장문 컨텍스트 질의 중심 요약에서 비정형 증거 인용**이라는 중요한 문제를 다루고 있습니다.  이는 투명성과 신뢰성 향상에 필수적이며, **LLM의 위치 편향 문제**와 **대규모 데이터셋 생성의 어려움**을 해결하기 위한 새로운 방법론을 제시합니다. 이는 요약 및 정보 검색 분야의 연구에 큰 영향을 미치며, 앞으로의 연구 방향을 제시할 것입니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.14409/x1.png)

> 🔼 본 논문의 그림 1은 장문 맥락에서 비정형 증거 인용을 사용한 질의 중심 요약에 대한 연구를 설명합니다. 그림은 사용자의 질문에 대한 답변을 생성하기 위해 장문의 문서(예: 책, 연구 논문 또는 법률 문서)에서 관련 정보를 추출하고 요약하는 과정을 시각적으로 보여줍니다.  단순히 요약만 하는 것이 아니라, 요약에 사용된 정보의 출처를  문서 내 특정 위치를 명시하지 않고 자유롭게 인용하는 방식을 강조하고 있습니다. 이는 기존의 문장, 단락 또는 문서 단위의 구조화된 인용 방식과는 다릅니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: We study query focused summarization with unstructured evidence citation from long contexts
> </details>





{{< table-caption >}}
| Method | SUnsET Titles | SUnsET Questions | SUnsET Summaries | SUnsET Documents | Base Titles | Base Questions | Base Summaries | Base Documents | Base w/ Titles Titles | Base w/ Titles Questions | Base w/ Titles Summaries | Base w/ Titles Documents |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Moving Avg. TTR | 0.816 | 0.751 | 0.836 | 0.820 | 0.387 | 0.670 | 0.797 | 0.350 | 0.588 | 0.631 | 0.778 | 0.352 |
| Avg. Cosinse Dist. | 0.780 | 0.806 | 0.733 | 0.682 | 0.425 | 0.725 | 0.716 | 0.042 | 0.607 | 0.660 | 0.610 | 0.040 |
| Avg. Length (in words) | 5.44 | 13.45 | 226.5 | 3767.4 | 6.65 | 9.85 | 23.79 | 474.8 | 5.76 | 10.21 | 24.45 | 433.8 |{{< /table-caption >}}

> 🔼 표 1은 합성 데이터셋(SUnsET)의 통계 및 다양성 지표를 보여줍니다.  단순한 캡션보다 자세히 설명하자면,  합성 데이터 생성 파이프라인의 다양한 단계를 거쳐 생성된 문서, 질문, 요약, 증거 텍스트의 통계량과 다양성을 측정한 결과를 제시합니다.  구체적으로는 형태소 비율(Type-Token Ratio, TTR), 임베딩 코사인 유사도, 평균 길이(단어 수) 등의 지표를 사용하여 데이터의 다양성과 품질을 평가합니다. 이를 통해 SUnsET 데이터셋의 특징과 신뢰성을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Statistics and diversity metrics of synthetically generated data.
> </details>





### In-depth insights


#### Unstructured Citation
**비구조적 인용**은 기존의 문장, 단락, 문서 수준의 구조화된 인용 방식에서 벗어나, 맥락에 따라 자유롭게 인용 구간을 선택하는 방식입니다.  **LLM(대규모 언어 모델)이 장문의 텍스트를 요약할 때, 인용 근거를 명확히 밝히는 것은 투명성과 신뢰성을 높이는 데 중요**합니다. 하지만 기존의 구조화된 인용 방식은 모델의 유연성을 제한하고, 맥락에 맞는 정보를 선택하는 데 어려움을 초래할 수 있습니다.  **본 논문은 비구조적 인용을 통해 이러한 문제를 해결하고자 제안**합니다.  **데이터셋 생성 과정에서 모델의 위치 편향성을 최소화하고, 다양한 유형의 문서에서도 효과적으로 인용 근거를 추출할 수 있는 방법을 제시**하는 것이 핵심입니다.  **합성 데이터셋을 활용한 미세 조정을 통해 모델의 성능을 향상시키는 실험 결과는 비구조적 인용 방식의 실효성을 보여줍니다.**  하지만, 비구조적 인용은 인용의 정확성과 일관성을 보장하는 데 어려움이 있을 수 있다는 점을 고려해야 합니다.  **향후 연구에서는 비구조적 인용의 정확성과 신뢰성을 높이기 위한 추가적인 연구가 필요**합니다.

#### SUnsET Dataset
본 논문에서 제시된 SUnsET 데이터셋은 **긴 문맥 질의에 초점을 맞춘 요약에서 비구조화된 증거 인용을 위한 최초의 연구**를 지원하기 위해 고안되었습니다. 기존의 구조화된 증거 인용 방식과 달리, SUnsET은 **문장이나 단락 등 특정 구조에 제한되지 않고, 텍스트 내에서 자유롭게 증거를 추출하고 인용**할 수 있도록 합니다. 이는 모델이 **자연스럽고 유연한 방식으로 증거를 활용**할 수 있게 하여 요약의 투명성과 신뢰성을 높이는 데 기여합니다.  데이터셋 생성에는 **도메인에 구애받지 않는 귀납적 생성 파이프라인**이 사용되었으며, 다양한 유형의 문서와 질의에 걸쳐 일반화될 수 있도록 설계되었습니다.  **모델의 위치 편향 문제 완화를 위해 문서의 구조를 조정**하는 방법도 포함합니다.  **SUnsET은 다양한 크기와 사전 훈련 구성의 5개의 LLM과 4개의 데이터셋에서 평가**되었으며,  **기존 모델에 비해 더욱 관련성 있고 사실적으로 일관된 증거를 생성**하는 것으로 나타났습니다.  전반적으로 SUnsET 데이터셋은 긴 문맥 요약 분야의 발전에 크게 기여할 뿐만 아니라, **비구조화된 증거 인용이라는 새로운 과제**를 제시함으로써 관련 연구에 중요한 기준점을 제공합니다.

#### LLM Adaptation
본 논문에서 제시된 LLM 적응 전략은 **합성 데이터셋(SUnsET)을 활용한 파인튜닝**에 초점을 맞춥니다.  이는 기존의 방대한 실제 데이터 수집의 어려움을 극복하고, **다양한 도메인과 텍스트 길이에 대한 일반화 성능**을 향상시키는 데 효과적입니다. 특히, **비정형적 증거 인용**이라는 새로운 과제에 대한 LLM의 성능 향상에 주목할 만합니다.  **단순한 파인튜닝뿐 아니라, 위치 정보를 고려한 적응 전략과 무작위화 전략을 비교 분석**함으로써 최적의 적응 방식을 제안하고, 이를 통해 LLM의 위치 편향 문제를 완화하고 증거 인용의 정확도와 범위를 개선하는 효과를 보여줍니다.  **SUnsET 데이터셋의 공개**를 통해 향후 연구의 발전에도 기여할 것으로 기대됩니다.  하지만,  **합성 데이터의 한계**와 **과제 특수성**으로 인한 일반화 가능성에 대한 추가 연구가 필요하며,  **실제 데이터와의 비교 검증**을 통해 실제 적용 가능성을 더욱 확고히 하는 후속 연구가 필요합니다.  결론적으로, 제시된 LLM 적응 방법은 효과적이지만,  **일반화 및 실제 세계 적용 가능성**에 대한 면밀한 검토가 필요합니다.

#### Positional Bias
본 논문에서 다루는 "Positional Bias"는 **장문 컨텍스트 질의 중심 요약**에서 LLMs(대규모 언어 모델)의 성능에 상당한 영향을 미치는 중요한 문제입니다.  LLMs는 입력 텍스트의 처음과 끝 부분에 과도하게 집중하는 경향이 있으며, 이는 **중간 부분의 관련 정보가 무시**될 수 있음을 의미합니다. 이러한 현상은 모델이 텍스트의 위치 정보에 편향되어 학습되었기 때문에 발생하며, **정확하고 포괄적인 요약 생성을 저해**합니다.  본 연구는 이러한 positional bias를 완화하기 위해 **합성 데이터셋(SUnsET)**을 활용한 미세 조정 기법을 제시하고 있습니다.  **데이터셋의 모듈화**를 통해 텍스트의 구조적 순서를 무작위로 바꾸는 방법을 통해 positional bias의 영향을 줄이고, 더욱 균형 잡힌 정보 활용을 유도합니다. 이는 **요약의 질적 향상과 관련 정보의 균형 있는 추출**로 이어집니다.  하지만, 단순히 데이터셋의 순서만 바꾸는 것보다 더욱 정교한 위치 정보 조정 기법을 통해 positional bias 문제를 해결할 수 있을 것이라는 가능성도 시사하고 있습니다.

#### Future Research
본 논문에서 제시된 연구는 장문 컨텍스트 질의 중심 요약에서 비구조적 증거 인용에 대한 첫 번째 연구이며, 흥미로운 결과를 보여주지만 추가 연구가 필요한 영역들이 있습니다. **미래 연구는 먼저, 더욱 다양하고 대규모의 데이터셋을 구축하는 데 초점을 맞춰야 합니다.**  현재 사용된 SUnsET 데이터셋은 합성 데이터셋이기 때문에 실제 세계 데이터셋의 다양성과 복잡성을 완전히 반영하지 못할 수 있습니다.  **다양한 도메인과 유형의 문서를 포함하는 실제 세계 데이터셋을 사용하여 모델의 일반화 성능을 평가하는 것이 중요합니다.**  둘째, **비구조적 증거 인용의 정확성과 신뢰성을 높이기 위한 새로운 기술을 개발하는 것이 필요합니다.**  본 연구에서 제시된 방식은 합성 데이터셋을 사용한 미세 조정에 의존하지만, 이는 실제 세계 데이터에서 항상 효과적이지는 않습니다.  **보다 정교한 증거 추출 및 인용 메커니즘을 개발하고, 잠재적으로는  RAG(Retrieval-Augmented Generation)와 같은 기술을 통합하여 모델의 성능을 개선해야 합니다.**  마지막으로, **장문 컨텍스트 요약의 효율성과 확장성을 향상시키는 방안을 모색해야 합니다.** 본 연구의 모델은 상당한 계산 자원을 필요로 하기 때문에, 경량화된 모델이나 더욱 효율적인 학습 방법을 개발하는 것이 실제 응용에 중요한 과제가 될 것입니다.  이러한 미래 연구들을 통해, 장문 컨텍스트 질의 중심 요약의 투명성과 신뢰성을 더욱 높이고, 실제 응용 분야에서의 활용성을 높일 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.14409/x2.png)

> 🔼 그림 2는 논문에서 사용된 합성 데이터셋 생성을 위한 6단계 유도적 파이프라인을 보여줍니다. 각 단계는 특정한 작업을 수행하며, 이전 단계의 결과를 입력으로 받아 다음 단계의 입력을 생성하는 순차적 과정을 거칩니다.  1단계는 소설과 논픽션 도서의 제목을 생성하고, 2단계는 생성된 제목에 대한 개요를 만듭니다. 3단계는 제목과 개요를 바탕으로 질문, 요약문, 그리고 이를 뒷받침하는 텍스트 구간을 생성합니다. 4단계는 이전 단계에서 생성된 내용을 바탕으로 도서의 각 장을 생성하고, 5단계는 생성된 요약문과 증거 텍스트를 세련되게 다듬습니다. 마지막 6단계는 생성된 요약문과 증거 텍스트가 도서의 내용과 일치하는지 검증하는 단계입니다. 부록 A의 그림 8부터 그림 16까지 각 단계에 대한 자세한 프롬프트 내용이 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Six stage inductive data generation pipeline. The full prompts for each stage are given in Appendix A Figure 8 - Figure 16.
> </details>



![](https://arxiv.org/html/2502.14409/x3.png)

> 🔼 그림 3은 SUnsET 데이터셋에서 가져온 문서의 일부 발췌를 보여줍니다.  'Writing the Unwritable' 이라는 제목의 예시 문서를 통해, 제목, 짧은 요약, 질문, 그리고 해당 요약을 뒷받침하는 증거 문구가 어떻게 구성되는지 보여줍니다.  이 그림은 논문에서 제시하는 무작위 구조의 증거 인용을 가진 긴 문맥 질의 중심 요약 작업의 복잡성과 SUnsET 데이터셋이 어떻게 이러한 복잡성을 다루는지 보여주는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Snippets from a SUnsET document.
> </details>



![](https://arxiv.org/html/2502.14409/x4.png)

> 🔼 그림 4(a)는 Llama 3.2 1B 모델에 대한 결과를 보여줍니다. 이 그림은 다양한 방법(Shuffled, Standard, Base)을 사용하여 추출된 증거의 위치를 소스 컨텍스트 내에서 보여줍니다.  'Shuffled'는 문서 섹션을 섞어서 학습시킨 모델의 결과이고, 'Standard'는 문서 섹션 순서를 유지하여 학습시킨 모델의 결과이며, 'Base'는 fine-tuning 전 모델의 결과입니다.  x축은 소스 컨텍스트 내에서 증거가 추출된 상대적 위치를 나타내고, y축은 각 위치에서 추출된 증거의 수를 나타냅니다. 이를 통해 각 방법에 따른 증거 추출 위치의 편향성(positional bias)을 확인할 수 있습니다.  특히, 'Base' 모델은 컨텍스트의 중간 부분에서 증거가 적게 추출되는 ‘Lost-in-the-middle’ 현상을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (a) Llama 3.2 1B
> </details>



![](https://arxiv.org/html/2502.14409/x5.png)

> 🔼 그림 (b)는 Llama 3.2 3B 모델에 대한 결과를 보여줍니다. 이 그림은 본 논문의 4.2절 RQ2: 'Lost-in-the-middle' 에서 다루는 내용과 관련이 있으며, 추출된 증거의 위치를 나타내는 히스토그램입니다.  x축은 문서 내 증거의 상대적 위치(0.0은 문서의 시작, 1.0은 문서의 끝)를 나타내고, y축은 각 위치에서 추출된 증거의 개수를 나타냅니다. 세 개의 그룹(Shuffled, Standard, Base)이 있는데 각 그룹은 서로 다른 fine-tuning 방법을 나타냅니다.  Shuffled는 문서 섹션 순서를 섞어서 fine-tuning한 결과이고, Standard는 원래 순서대로 fine-tuning한 결과, Base는 fine-tuning 하지 않은 기본 모델의 결과입니다. 이 그림을 통해  LLM이 문서의 중간 부분에 있는 증거를 제대로 추출하지 못하는 경향(lost-in-the-middle 현상)을 확인하고, fine-tuning 방식에 따른 차이를 비교 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (b) Llama 3.2 3B
> </details>



![](https://arxiv.org/html/2502.14409/x6.png)

> 🔼 그림 (c)는 Llama 3.1 8B 모델에 대한 결과를 보여줍니다. 이 그림은 다양한 방법(Shuffled, Standard, Base)으로 추출된 증거의 위치를 보여주는 히스토그램입니다.  Shuffled는 문서 섹션을 섞어서 학습한 경우, Standard는 자연스러운 순서로 학습한 경우, Base는 사전 학습된 모델을 사용한 경우를 나타냅니다.  x축은 증거의 상대적 위치(0.0은 문서의 처음, 1.0은 문서의 끝을 나타냄), y축은 해당 위치에서 추출된 증거의 개수를 나타냅니다. 이를 통해 모델의 위치 편향(positional bias) 및 SUnsET 데이터셋을 사용한 미세 조정의 효과를 시각적으로 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (c) Llama 3.1 8B
> </details>



![](https://arxiv.org/html/2502.14409/x7.png)

> 🔼 그림 (d)는 Mistral Nemo 2407 모델에 대한 다양한 방법(Shuffled, Standard, Base)을 사용하여 추출된 증거의 위치를 보여줍니다.  x축은 문서 내 상대적 위치(0.0에서 1.0까지)를 나타내고, y축은 추출된 증거의 개수를 나타냅니다. 이 그림은 각 방법에 따른 증거 추출 위치의 분포를 비교하여 모델의 위치 편향(positional bias)을 분석하는 데 사용됩니다.  Shuffled는 문서 섹션을 섞은 후 학습한 모델, Standard는 일반적인 순서로 학습한 모델, Base는 SUnsET 데이터로 fine-tuning 하지 않은 기본 모델을 의미합니다.
> <details>
> <summary>read the caption</summary>
> (d) Mistral Nemo 2407
> </details>



![](https://arxiv.org/html/2502.14409/x8.png)

> 🔼 그림 4(e)는 다양한 방법으로 생성된 요약에서 추출된 증거의 위치를 보여줍니다. 특히, Mixtral 8x7B 모델의 경우를 보여주는 이 그림은 추출된 증거가 문서의 어느 부분에서 나왔는지 그 분포를 보여주는 히스토그램을 나타냅니다.  'Shuffled', 'Standard', 'Base' 세 가지 방법의 결과를 비교하여,  모델 학습 방식에 따라 증거 추출 위치 분포가 어떻게 달라지는지 시각적으로 보여줍니다. 이는 모델의 위치 편향(positional bias)을 분석하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> (e) Mixtral 8x7B
> </details>



![](https://arxiv.org/html/2502.14409/x9.png)

> 🔼 그림 4(f)는 다양한 방법(기준 모델, 순서 변경된 훈련, SUnsET 데이터로 훈련된 모델)을 사용하여 추출된 증거의 위치를 보여줍니다. 특히 GPT-40 Mini 모델에 대한 결과를 보여주는 그래프입니다.  이 그래프는 각 방법에 따라 추출된 증거가 원본 문서의 어느 위치에서 얼마나 자주 나오는지 보여주는 히스토그램을 나타냅니다. 이를 통해 모델의 위치 편향성과 SUnsET 데이터를 사용한 미세 조정이 위치 편향성에 미치는 영향을 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (f) GPT 4o Mini
> </details>



![](https://arxiv.org/html/2502.14409/x10.png)

> 🔼 그림 4는 다양한 방법들을 사용하여 제공된 소스 컨텍스트에서 추출된 증거의 위치를 보여줍니다.  각 그래프는 특정 모델(Llama 3.2 1B, Llama 3.2 3B, Llama 3.1 8B, Mistral Nemo 2407, Mixtral 8x7B, GPT 40 Mini)에 대한 추출된 증거의 위치 분포를 나타냅니다.  x축은 컨텍스트 내 증거의 상대적 위치(0.0은 시작 부분, 1.0은 끝 부분)를 나타내고, y축은 해당 위치에 추출된 증거의 개수를 나타냅니다.  각 모델에 대해 기본 모델(Base), 셔플링된 컨텍스트로 학습된 모델(Shuffled), 표준 컨텍스트로 학습된 모델(Standard)의 결과가 비교되어 표시됩니다. 이를 통해 각 모델의 위치 편향(positional bias) 및 SUnsET 데이터셋을 사용한 미세 조정의 효과를 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Location of extracted evidence in the provided source context for different methods.
> </details>



![](https://arxiv.org/html/2502.14409/x11.png)

> 🔼 그림 5는 논문의 4.2절 'RQ2: 증거가 중간에 손실되는가?'에서 제시된 그림입니다. 이 그림은 각 데이터셋(SQuALITY, LexAbSumm, SummHay, ScholarQABench)에서 추출된 증거의 위치 분포를 보여줍니다. x축은 증거의 위치(0.0은 문서의 시작, 1.0은 문서의 끝), y축은 각 위치에 있는 증거의 개수를 나타냅니다. 각 데이터셋에서 기존 모델이 증거를 추출하는 위치 경향성과 실제 증거의 위치 분포를 비교하여 모델의 위치 편향성(positional bias)을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (a) SQuALITY
> </details>



![](https://arxiv.org/html/2502.14409/x12.png)

> 🔼 그림 5(b)는 논문의 실험에 사용된 네 가지 데이터셋 중 하나인 LexAbSumm 데이터셋의 기저 진실 증거(ground truth evidence)의 위치 분포를 보여줍니다.  LexAbSumm 데이터셋은 긴 법률 문서를 사용하며, 각 문서에 대한 요약문과 관련된 증거 구간을 포함합니다. 이 그래프는 LexAbSumm 데이터셋의 문서에서 증거의 위치 분포가 어떻게 되어 있는지 보여주는 히스토그램입니다.  x축은 문서 내 상대적인 위치(0.0에서 1.0까지)를 나타내고, y축은 해당 위치에 있는 증거의 개수를 나타냅니다. 이를 통해 모델이 문서의 어느 부분에 있는 정보에 더 많이 주목하는지, 또는 증거가 문서의 특정 부분에 집중되어 있는지 등을 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (b) LexAbSumm
> </details>



![](https://arxiv.org/html/2502.14409/x13.png)

> 🔼 그림은 논문의 실험 결과를 보여주는 그림 5의 (c) 부분입니다. 그림 5는 다양한 데이터셋에서 추출된 증거의 위치를 보여주는 히스토그램을 나타냅니다.  (c)는 SummHay 데이터셋에 대한 결과이며, SummHay는 대화 및 뉴스 기사를 포함하는 다중 문서 요약 데이터셋입니다. 히스토그램은 SummHay 데이터셋의 지상 진실 증거(ground truth evidence)가 소스 컨텍스트에서 어디에 위치하는지 보여줍니다.  x축은 증거 위치의 상대적 위치를 나타내고, y축은 각 위치에 해당하는 증거의 수를 나타냅니다. 이를 통해 SummHay 데이터셋에서 증거가 소스 문서 내에서 어떻게 분포되어 있는지 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (c) SummHay
> </details>



![](https://arxiv.org/html/2502.14409/x14.png)

> 🔼 그림 5(d)는 논문의 실험 결과 중 하나로, ScholarQABench 데이터셋에서 추출된 근거(evidence)의 위치 분포를 보여줍니다.  ScholarQABench는 컴퓨터 과학 연구 논문을 다루는 다중 문서 요약 데이터셋입니다. 이 그래프는 다양한 모델(기준 모델, SUnsET 데이터로 미세 조정된 모델 등)에서 추출된 근거가 원본 문서 내에서 어느 위치에 주로 분포하는지 보여주는 히스토그램입니다. x축은 문서 내 상대적 위치(0.0은 문서의 시작, 1.0은 문서의 끝), y축은 근거 횟수를 나타냅니다. 이를 통해 모델의 위치 편향(positional bias) 및 SUnsET 데이터셋을 활용한 미세 조정 효과를 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (d) ScholarQABench
> </details>



![](https://arxiv.org/html/2502.14409/x15.png)

> 🔼 그림 5는 각 데이터셋에서 실제 증거의 위치를 보여줍니다.  x축은 문서 내 증거의 상대적 위치(0에서 1 사이의 값으로 표현, 0은 문서의 시작, 1은 문서의 끝)를 나타내고, y축은 각 위치에 해당하는 증거의 개수를 나타냅니다. 각 데이터셋(SQUALITY, LexAbSumm, SummHay, ScholarQABench)별로 실제 증거가 문서 내 어느 위치에 주로 분포하는지 시각적으로 보여줌으로써, 모델의 위치 편향(positional bias) 문제를 이해하는 데 도움을 줍니다.  즉, 특정 위치의 단어들에 모델이 지나치게 집중하여 다른 위치의 관련 정보를 무시하는 경향을 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Location of ground truth evidence in each dataset.
> </details>



![](https://arxiv.org/html/2502.14409/x16.png)

> 🔼 그림 4(a)는 Llama 3.2 1B 모델에 대한 결과를 보여줍니다. 이 그림은 다양한 방법(Shuffled, Standard, Base)을 사용하여 추출된 증거의 위치를 나타내는 히스토그램입니다.  x축은 문서 내 증거의 상대적 위치(0.0은 문서의 시작, 1.0은 문서의 끝)를 나타내고, y축은 각 위치에서 추출된 증거의 개수를 나타냅니다. 이를 통해 모델이 문서의 어느 부분에서 증거를 주로 추출하는지, 그리고 각 방법이 증거 추출 위치에 어떤 영향을 미치는지를 확인할 수 있습니다.  Shuffled는 문장의 순서를 섞은 경우, Standard는 기본 모델을 fine-tuning한 경우, Base는 fine-tuning 전의 기본 모델을 의미합니다.
> <details>
> <summary>read the caption</summary>
> (a) Llama 3.2 1B
> </details>



![](https://arxiv.org/html/2502.14409/x17.png)

> 🔼 그림 (b)는 4.1절의 실험 결과 중 하나로, Llama 3.1 8B 모델에 대한 비정렬 및 정렬된 학습 방식을 사용한 추출된 증거의 위치 분포를 보여줍니다.  x축은 문서 내 증거 위치의 상대적 비율(0.0에서 1.0까지)을 나타내고, y축은 각 위치에서 추출된 증거의 개수를 나타냅니다.  세 개의 막대 그래프는 각각 기준 모델, 정렬된 학습 모델, 그리고 비정렬된 학습 모델의 결과를 보여줍니다. 이는 모델이 문서 내에서 어디에서 증거를 추출하는지, 그리고 정렬된 학습과 비정렬된 학습이 이에 어떤 영향을 미치는지를 시각적으로 보여주는 그림입니다.
> <details>
> <summary>read the caption</summary>
> (b) Llama 3.1 8B
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | Exact Match | 50% Match | # Evidence |
|---|---|---|---| 
| Llama 3.2 1B | 0.0 | 35.71 | 14 |
| + Standard | **7.69** | **43.26** | 208 |
| + Shuffled | 5.15 | 22.68 | 97 |
| Llama 3.2 3B | 25.57 | **90.11** | 1345 |
| + Standard | **52.77** | 85.62 | 3720 |
| + Shuffled | 32.99 | 74.07 | 2337 |
| Llama 3.1 8B | 43.93 | 83.12 | 3412 |
| + Standard | **78.36** | **97.21** | 4690 |
| + Shuffled | 54.53 | 88.51 | 4684 |
| Mistral Nemo 2407 | 5.48 | 66.13 | 310 |
| + Standard | **82.20** | **97.29** | 2107 |
| + Shuffled | 72.38 | 95.76 | 1959 |
| Mixtral 8x7B | 5.79 | 91.25 | 3452 |
| + Standard | **33.82** | 90.47 | 4208 |
| + Shuffled | 29.29 | **90.74** | 4288 |
| GPT-4o-mini | *11.06* | *96.32* | *8159* |{{< /table-caption >}}
> 🔼 표 2는 추출된 증거의 환각률을 보여줍니다. 이 표는 증거 문장이 문맥에 정확하게 나타나는 경우(즉, 정확히 일치)와 추출된 증거와 문맥 내 가장 긴 공통 부분 문자열 간의 50% 중복이 있는 경우를 직접 측정합니다.
> <details>
> <summary>read the caption</summary>
> Table 2:  Hallucination rates for evidence extraction. We directly measure exact string match (i.e. when the evidence sentence exactly appears in the context) as well as 50% overlap between the extracted evidence and the longest common substring in the context.
> </details>

{{< table-caption >}}
| Method | SLT<sub>S</sub> Rel<sub>F1</sub> | SLT<sub>S</sub> Con<sub>F1</sub> | LAS<sub>S</sub> Rel<sub>F1</sub> | LAS<sub>S</sub> Con<sub>F1</sub> | SMH<sub>M</sub> Rel<sub>F1</sub> | SMH<sub>M</sub> Con<sub>F1</sub> | SQB<sub>M</sub> Rel<sub>F1</sub> | SQB<sub>M</sub> Con<sub>F1</sub> |
|---|---|---|---|---|---|---|---|---|
| Llama 3.2 1B | 0.00 | 0.00 | 0.94 | 1.06 | **0.00** | **0.00** | 0.23 | 0.18 |
| + Standard | **0.63** | **0.53** | **4.80** | **4.56** | **0.00** | **0.00** | **1.84** | **1.68** |
| + Shuffled | 0.48 | 0.26 | 2.83 | 2.84 | **0.00** | **0.00** | 0.00 | 0.00 |
| Llama 3.2 3B | 11.21 | 10.16 | 15.08 | 14.64 | 8.64 | 8.75 | 12.37 | 12.99 |
| + Standard | **36.19** | **25.12** | **43.98** | **40.64** | **37.73** | **39.03** | **37.16** | **34.39** |
| + Shuffled | 23.38 | 15.33 | 36.19 | 31.26 | 32.73 | 33.46 | 31.36 | 26.73 |
| Llama 3.1 8B | 17.21 | 15.15 | 31.17 | 30.65 | 34.18 | 37.96 | 32.08 | 32.85 |
| + Standard | **35.21** | **25.34** | **52.64** | **47.79** | **56.82** | **57.50** | **45.26** | **41.13** |
| + Shuffled | 29.36 | 20.65 | 49.90 | 44.19 | 54.79 | 54.27 | 39.53 | 36.17 |
| Mistral Nemo 2407 | 2.75 | 2.37 | 5.34 | 4.58 | 10.37 | 10.25 | 5.67 | 5.36 |
| + Standard | **34.24** | **24.45** | 38.21 | 36.88 | **23.54** | **25.13** | **7.15** | **7.56** |
| + Shuffled | 32.52 | 22.84 | **39.94** | **38.57** | 21.58 | 23.23 | 4.65 | 4.08 |
| Mixtral 8x7B | 24.45 | 19.15 | 39.48 | 40.08 | 44.01 | 43.44 | 25.97 | 25.61 |
| + Standard | 30.54 | 25.11 | 38.27 | 38.08 | **48.71** | **51.85** | 38.37 | 38.59 |
| + Shuffled | **32.87** | **25.86** | **44.13** | **44.48** | 46.67 | 49.09 | **39.65** | **41.89** |
| GPT 4o Mini | _42.62_ | _36.23_ | _59.48_ | _53.96_ | _64.99_ | _60.14_ | _37.65_ | _33.11_ |{{< /table-caption >}}
> 🔼 표 3은 요약문에서 언급된 증거 문장의 관련성과 일관성을 평가한 결과를 보여줍니다. 관련성과 일관성은 사전에 검증된 프롬프트를 기반으로 GPT-40-mini 자동 평가기를 사용하여 측정되었습니다(Liu et al., 2023, 2024b).  인용 정확도와 재현율을 측정하여 관련성과 일관성 모두에 대한 전반적인 F1 점수를 계산했습니다(Laban et al., 2024; Asai et al., 2024와 유사한 설정).  S는 단일 문서 작업을, M은 다중 문서 작업을 나타냅니다. SQ는 SQuALITY, LAS는 LexAbSumm, SMH는 SummHay, SQB는 ScholarQABench를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Relevance and consistency of evidence sentences with respect to their citances. Relevance and consistency are measured using an autorater (GPT-4o-mini) Liu et al. (2023) based on previously validated prompts Liu et al. (2024b). We follow a similar setup to Laban et al. (2024); Asai et al. (2024) where we measure citation precision and recall in order to calculate an overall F1 score for both relevance and consistency. S indicates single document tasks, M indicates multi-document. SQ is SQuALITY, LAS is LexAbSumm, SMH is SummHay, and SQB is ScholarQABench
> </details>

{{< table-caption >}}
| Method | SLT<sup>S</sup> Rel | SLT<sup>S</sup> Con | LAS<sup>S</sup> Rel | LAS<sup>S</sup> Con | SMH<sup>M</sup> Rel | SMH<sup>M</sup> Con | SQB<sup>M</sup> Rel | SQB<sup>M</sup> Con |
|---|---|---|---|---|---|---|---|---|
| Llama 3.2 1B | 2.68 | 2.15 | **3.68** | **3.38** | 4.53 | 4.40 | 3.80 | 3.61 |
| + Standard | 2.73<sup>=</sup> | **2.17<sup>=</sup>** | 3.25 | 2.93 | 4.53<sup>=</sup> | 4.44<sup>=</sup> | 3.81<sup>=</sup> | 3.59<sup>=</sup> |
| + Shuffled | **2.79*** | 2.15<sup>=</sup> | 3.41 | 3.03 | **4.66*** | **4.55*** | **3.97*** | **3.69*** |
| Llama 3.2 3B | **4.39** | **4.05** | **4.40** | **4.19** | 4.82 | 4.74 | 4.28 | 4.11 |
| + Standard | 4.22 | 3.80 | 4.19 | 4.02 | **4.90*** | **4.85*** | 4.41* | 4.21* |
| + Shuffled | 3.84 | 3.38 | 4.25 | 4.02 | 4.89* | 4.84* | **4.49*** | **4.23*** |
| Llama 3.1 8B | 4.55 | 4.34 | **4.64** | **4.52** | 4.88 | 4.78 | 4.18 | 4.06 |
| + Standard | **4.63*** | **4.41*** | 4.53 | 4.44 | 4.94* | **4.93*** | 4.64* | **4.42*** |
| + Shuffled | 4.59* | 4.34<sup>=</sup> | 4.55 | 4.44 | **4.97*** | 4.92* | **4.68*** | 4.41* |
| Mistral Nemo 2407 | 4.27 | 4.09 | 3.83 | 3.85 | 4.27 | 4.15 | 3.15 | 3.23 |
| + Standard | 4.43* | 4.24* | 4.03* | 4.04* | 4.54* | 4.47* | **3.79*** | **3.75*** |
| + Shuffled | **4.53*** | **4.35*** | **4.18*** | **4.12*** | **4.65*** | **4.49*** | 3.49* | 3.41* |
| Mixtral 8x7B | 4.02 | 3.99 | 4.28 | 4.22 | 4.78 | 4.68 | 3.95 | 3.89 |
| + Standard | **4.52*** | 4.35* | **4.45*** | **4.40*** | **4.84*** | **4.72*** | 4.26* | 4.13* |
| + Shuffled | 4.51* | **4.40*** | 4.44* | 4.38* | 4.79<sup>=</sup> | 4.68<sup>=</sup> | **4.33*** | **4.18*** |
| GPT 4o Mini | _4.98_ | _4.92_ | _4.93_ | _4.77_ | _4.99_ | _4.98_ | _4.94_ | _4.76_ |{{< /table-caption >}}
> 🔼 표 4는 생성된 요약의 관련성과 일관성을 보여줍니다. 관련성과 일관성은 이전에 검증된 프롬프트를 기반으로 자동 평가기(GPT-4o-mini) Liu et al.(2023)을 사용하여 측정되었습니다. *는 기준선과 비교하여 중복되지 않는 부트스트래핑 신뢰 구간으로 측정된 유의성을 나타내고, =는 기준선과 유의미한 차이가 없음을 나타냅니다. S는 단일 문서 작업을, M은 다중 문서 작업을 나타냅니다. SLT는 SQuALITY, LAS는 LexAbSumm, SH는 SummHay, SQB는 ScholarQABench를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Relevance and consistency of generated summaries. Relevance and consistency are measured using an autorater (GPT-4o-mini) Liu et al. (2023) based on previously validated prompts Liu et al. (2024b). * indicates significance as measured by non-overlapping bootstrapped confidence intervals with the baseline. = indicates no significant difference from baseline. S indicates single document tasks, M indicates multi-document. SLT is SQuALITY, LAS is LexAbSumm, SH is SummHay, and SQB is ScholarQABench.
> </details>

{{< table-caption >}}
| Model | Huggingface Identifier |
|---|---| 
| Llama 3.2 1B | `meta-llama/Llama-3.2-1B-Instruct` |
| Llama 3.2 3B | `meta-llama/Llama-3.2-3B-Instruct` |
| Llama 3.1 8B | `meta-llama/Meta-Llama-3.1-8B-Instruct` |
| Mistral Nemo 2407 | `mistralai/Mistral-Nemo-Instruct-2407` |
| Mixtral 8x7B | `mistralai/Mixtral-8x7B-Instruct-v0.1` |{{< /table-caption >}}
> 🔼 표 5는 본 논문의 실험에 사용된 모델들의 Hugging Face 식별자를 보여줍니다.  각 모델의 이름과 해당 모델을 Hugging Face 허브에서 찾을 수 있는 식별자를 나타냅니다.  이 표는 모델 비교 및 재현성을 위해 중요한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Huggingface identifiers for models used in our experiments.
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