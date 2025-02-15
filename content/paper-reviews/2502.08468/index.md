---
title: "mmE5: Improving Multimodal Multilingual Embeddings via High-quality Synthetic Data"
summary: "고품질 합성 데이터를 활용, 다국어 다중 모달 임베딩 모델 mmE5 개발로 SOTA 성능 달성!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Vision-Language Models", "🏢 Microsoft Research",]
showSummary: true
date: 2025-02-12
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.08468 {{< /keyword >}}
{{< keyword icon="writer" >}} Haonan Chen et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-14 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.08468" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.08468" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/mme5-improving-multimodal-multilingual" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 다중 모달 임베딩 모델은 **데이터 부족**으로 인해 성능 향상에 어려움을 겪었습니다. 특히, **다국어 지원 및 다양한 모달 조합**을 고려한 데이터셋이 부족하여 모델의 일반화 성능이 저하되는 문제가 있었습니다. 본 논문에서는 이러한 문제를 해결하기 위해 **고품질 합성 다중 언어 다중 모달 데이터셋**을 생성하는 새로운 프레임워크를 제안합니다.

본 논문에서 제안하는 프레임워크는 **세 가지 핵심 기준**(광범위한 범위, 강력한 교차 모달 정렬, 높은 충실도)을 바탕으로 **다양한 작업, 모달 조합 및 언어**를 포괄하는 고품질 데이터셋을 생성합니다. **대규모 언어 모델(MLLM)**을 활용하여 효율적으로 데이터를 생성하며, 자체 평가 및 개선 과정을 통해 데이터의 품질을 높였습니다. 생성된 데이터셋을 사용하여 훈련된 mmE5 모델은 다양한 벤치마크에서 **최첨단 성능**을 달성하였으며, 특히 다국어 성능에서 뛰어난 결과를 보였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 고품질 합성 다중 언어 다중 모달 데이터셋 생성을 위한 새로운 프레임워크 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 제안된 프레임워크 기반 mmE5 모델 개발을 통해 다양한 벤치마크에서 최첨단 성능 달성 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 다국어 지원 및 다양한 모달 조합을 고려한 데이터셋은 다국어 다중 모달 연구 분야의 발전에 기여 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **고품질 합성 다중 언어 다중 모달 데이터셋을 생성하는 새로운 프레임워크**를 제시하여 다중 모달 임베딩 모델의 성능을 크게 향상시켰다는 점에서 중요합니다. **기존의 데이터 부족 문제를 해결하고 다양한 하류 작업에 적용 가능한 범용적인 임베딩 모델 개발**에 기여하며, 향후 연구의 새로운 방향을 제시합니다. 특히, 다국어 지원 및 다양한 모달 조합을 고려한 데이터셋 생성은 **다국어 다중 모달 연구 분야의 발전**에 큰 영향을 미칠 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.08468/x1.png)

> 🔼 그림 1은 논문에서 제안하는 데이터 합성 프레임워크를 보여줍니다.  'X→Y'는 질의(query) 측면과 타겟(target) 측면의 조합을 나타내며, 여기서 'X'는 질의 측면, 'Y'는 타겟 측면을 의미합니다. 'T'는 텍스트(text), 'I'는 이미지(image)를 나타냅니다.  이 그림은 데이터 합성 과정에서 다양한 모달 조합(예: 이미지에서 텍스트, 텍스트에서 이미지, 텍스트와 이미지에서 텍스트 등)을 사용하는 방법을 시각적으로 설명합니다.  데이터는 LAION 이미지 집합에서 가져온 실제 이미지와 다국어 텍스트를 사용하여 합성되며, 다양한 작업(분류, VQA, 검색)과 언어를 포함합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: An illustration of our data synthesis framework. “X→→\rightarrow→Y” denotes a modality combination, where “X” represents the query side and “Y” denotes the target side. “T” denotes text and “I” denotes image.
> </details>





{{< table-caption >}}
| Method | # Languages | Task | Modality Combinations | w/ MLLM | One Pass | Self-evaluation |
|---|---|---|---|---|---|---|
| MagicLens | 1 (English) | Retrieval | IT→I | × | √ | × |
| MegaPairs | 1 (English) | Retrieval | IT→I | √ | × | × |
| GME | 1 (English) | Retrieval | T→IT, IT→IT | × | × | × |
| mmE5 (Ours) | 93 (English, Spanish, etc.) | Classification, VQA, Retrieval | IT→I, T→IT, IT→IT, I→I, I→T, IT→T, T→I | √ | √ | √ |{{< /table-caption >}}

> 🔼 표 1은 본 논문에서 제안하는 방법과 기존 방법들의 합성 데이터셋을 비교한 표입니다. 본 논문의 합성 데이터셋은 93개 언어, 2가지 추가 과제, 그리고 더 많은 모달 조합을 포함합니다.  'IT→T'는 질의 측면에 이미지와 텍스트가 있고, 타겟 측면에 텍스트가 있는 모달 조합을 나타냅니다.  데이터 합성 과정 전체가 대규모 다중 모달 언어 모델(MLLM)의 단일 패스 내에서 수행되어 정보 손실을 방지하고 강력한 교차 모달 정렬을 보장합니다. 또한, 실제 이미지와 자체 평가를 사용하여 충실도를 유지합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparison of the synthetic datasets in our work with those from previous methods. Our synthetic datasets incorporate 93 languages, two additional tasks, and more modality combinations. “IT→→\rightarrow→T” denotes a modality combination, where “IT” denotes images and texts on the query side and “T” denotes texts on the target side. The entire data synthesis process is executed within a single pass of an MLLM, thereby avoiding potential information loss and ensuring robust cross-modal alignment. We also employ real images and self-evaluation to maintain fidelity.
> </details>





### In-depth insights


#### Synth Data Criteria
본 논문에서 제시하는 합성 데이터의 세 가지 기준, 즉 **광범위한 범위**, **강력한 교차 모드 정렬**, **높은 충실도**는 합성 데이터 생성의 질적 향상을 위한 중요한 고려 사항임을 시사합니다.  **광범위한 범위**는 다양한 작업과 모드를 포괄하여 다양한 하위 작업에 적용 가능한 데이터를 생성하는 것을 의미하며, **강력한 교차 모드 정렬**은 서로 다른 모드 간의 의미적 일관성을 유지하여 하위 작업에서의 성능 저하를 방지하는 데 중요합니다.  **높은 충실도**는 현실적인 세부 정보를 유지하여 신뢰성을 높이는 데 기여합니다. 이 세 가지 기준은 상호 보완적이며, 이를 충족하는 고품질의 합성 데이터는 다운스트림 작업에서 뛰어난 성능을 달성하는 데 필수적입니다.  특히, **단일 패스 내에서 대규모 다중 모드 언어 모델을 활용한 데이터 합성**은 정보 손실을 최소화하고 강력한 교차 모드 정렬을 달성하는 효과적인 방법론으로 제시됩니다.

#### mmE5 Model
mmE5 모델은 **고품질 합성 데이터**를 사용하여 다국어 지원을 하는 다중 모드 임베딩 모델입니다. 이 모델은 기존의 다중 모드 임베딩 모델의 한계점인 **데이터 부족** 문제를 해결하기 위해 **세 가지 주요 기준**(광범위한 적용 범위, 강력한 상호 모드 정렬, 높은 충실도)을 제시하고, 이를 바탕으로 **MLLM(다중 모드 대형 언어 모델)**을 활용한 효율적인 데이터 합성 프레임워크를 구축했습니다.  **단일 패스 생성**을 통해 정보 손실을 최소화하고, 실제 이미지와 자체 평가 및 개선 메커니즘을 통해 **데이터 품질**을 높였습니다.  mmE5는 다양한 작업과 모드 조합, 그리고 93개 언어를 지원하며, MMEB 및 XTD 벤치마크에서 **최첨단 성능**을 달성했습니다. 특히, 기존 SOTA 모델보다 훨씬 적은 데이터로도 우수한 성능을 보이며, **데이터 효율성** 측면에서도 뛰어남을 입증했습니다.  **다국어 능력** 또한 탁월하여, 다양한 언어 환경에서의 다중 모드 임베딩 작업에 효과적으로 적용될 수 있습니다.

#### MLLM-Based Synth
**MLLM 기반 합성 데이터 생성**은 최근 멀티모달 엠베딩 모델의 성능 향상에 중요한 역할을 하고 있습니다.  기존의 수작업으로 데이터를 라벨링하는 방식은 비용과 시간이 많이 소모되는 반면, **MLLM(대규모 언어 모델)**을 활용하면 **훨씬 효율적이고 대량의 합성 데이터**를 생성할 수 있습니다.  본 논문에서 제시된 MLLM 기반 합성 방법은 단순히 텍스트와 이미지를 짝지어주는 것이 아니라, **MLLM의 심층적인 이해 능력을 활용**하여 다양한 모달리티 조합과 언어를 지원하는 **풍부하고 정교한 데이터셋**을 생성하는 데 초점을 맞춥니다.  이러한 **고품질 합성 데이터**는 다운스트림 작업의 성능 향상과 모델의 일반화 능력 향상에 크게 기여할 것으로 예상됩니다. 하지만, **MLLM의 한계점을 고려**하여, 생성된 데이터의 품질을 보장하고,  **편향성을 최소화**하는 노력이 지속적으로 필요합니다.  향후 연구는 더 다양한 모달리티, 더 많은 언어, 더욱 정교한 작업을 지원하는 방향으로 나아갈 것으로 예상됩니다.

#### Multilingual Gains
다국어 지원 기능 향상에 대한 논의는 **다국어 데이터셋의 질적 향상**과 **모델의 다국어 처리 능력 강화**라는 두 가지 측면에서 이루어져야 합니다. 본 연구는 고품질의 다국어 합성 데이터를 생성하여 다양한 언어를 지원하는 다국어 모델을 훈련시키는 데 중점을 두었습니다. 이를 통해 기존의 영어 중심 모델의 한계를 극복하고 다양한 언어에 대한 성능을 향상시켰다는 점이 중요합니다. 특히, 저자들은 **다양한 언어를 포괄하는 대규모 데이터셋**을 구축하고, **모델의 다국어 이해 및 생성 능력을 강화**하는 데 성공했습니다. 다국어 성능 평가를 위한 벤치마크 데이터셋에서의 우수한 결과는 이러한 노력의 성과를 보여줍니다.  **합성 데이터의 질적 향상**, **모델 아키텍처 개선**, **다양한 언어 지원** 등의 세 가지 요소가 다국어 모델의 성능 향상에 중요한 영향을 미쳤을 것으로 예상됩니다. 앞으로 다국어 자연어 처리 분야에서 **더욱 정교하고 광범위한 다국어 데이터셋**, **다양한 모달리티를 지원하는 통합 모델**, **다국어 이해와 생성을 동시에 고려하는 학습 전략** 등의 발전이 필요합니다.  본 연구는 이러한 발전 방향에 대한 중요한 시사점을 제공합니다.

#### Future Work
본 논문은 고품질의 합성 다중 모드 다국어 데이터를 사용하여 다중 모드 다국어 임베딩 모델을 향상시키는 데 중점을 두었습니다.  하지만 **미래 연구를 위한 몇 가지 중요한 방향**이 제시됩니다.  먼저, 현재 모델은 독점적 대규모 언어 모델(LLM)에 의존하고 있는데, 이는 비용이 많이 들고 접근성이 낮다는 한계점을 지닙니다. 따라서 **더 작고 효율적인 LLM을 사용하여 고품질 데이터를 합성하는 방법**을 모색하는 것이 중요합니다.  둘째, 현재는 텍스트와 이미지 모드에 초점을 맞추고 있지만, **오디오 및 비디오 모드와 같은 추가 모드를 포함**하여 모델의 다양성을 확장하는 연구가 필요합니다.  셋째, 모델 학습에 사용된 데이터의 양은 비용 문제로 제한적이었으므로 **데이터 크기를 늘리는 동시에 다양성을 유지**하는 방안을 고려해야 합니다.  마지막으로, **모델의 일반화 성능을 더욱 향상**시키기 위해 다양한 하이퍼파라미터에 대한 심층적인 분석과 최적화 연구가 필요합니다. 이러한 미래 연구를 통해 다중 모드 다국어 임베딩 모델의 성능과 활용 가능성이 크게 향상될 것으로 기대됩니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.08468/x2.png)

> 🔼 그림 2는 제시된 논문의 방법론을 설명하는 그림입니다. IT→IT 검색 데이터 샘플 생성 과정을 예시로 보여줍니다.  데이터 구성(Data Configuration), 시각적 해석(Visual Interpretation), 데이터 합성(Data Synthesis), 자체 평가(Self-evaluation), 모델 미세 조정(Model Finetuning)의 다섯 단계를 거쳐 데이터를 생성하는 과정을 시각적으로 보여줍니다. 각 단계별로 어떤 작업이 수행되는지 자세하게 묘사되어 있습니다.  특히, MLLM(다중 모드 대규모 언어 모델)을 사용하여 이미지를 다양한 관점에서 해석하고, 이를 바탕으로 데이터를 생성하며, 자체 평가 및 개선을 통해 데이터 품질을 높이는 과정이 상세히 나타나 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: An illustration of our method. We take the generation of an IT→→\rightarrow→IT retrieval data sample as an example.
> </details>



![](https://arxiv.org/html/2502.08468/x3.png)

> 🔼 그림 3은 합성 데이터셋에 포함된 언어들의 분포를 보여줍니다. 영어가 가장 큰 비중을 차지하고 있고, 다른 언어들은 상대적으로 적은 비중을 차지하고 있습니다. 이는 다양한 언어를 포함하여 모델의 다국어 성능을 향상시키려는 연구진의 노력을 보여줍니다. 하지만 영어 데이터가 압도적으로 많다는 점은 모델의 다국어 능력에 대한 편향성을 야기할 수 있다는 점을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Distribution of languages in the synthetic data.
> </details>



![](https://arxiv.org/html/2502.08468/x4.png)

> 🔼 이 그림은 MMEB 벤치마크에서 합성 데이터 크기가 다중 모드 임베딩 성능에 미치는 영향을 보여줍니다. x축은 사용된 합성 데이터의 크기를 나타내고, y축은 MMEB 벤치마크에서 달성된 평균 점수를 나타냅니다. 그래프는 합성 데이터 크기가 증가함에 따라 성능이 향상됨을 보여주며, 일정 수준 이상의 데이터 크기에 도달하면 성능 향상의 정도가 줄어드는 점을 시사합니다. 이는 더 많은 데이터가 항상 더 나은 성능을 보장하지는 않으며, 특정 수준 이상의 데이터 양을 넘어서는 경우 성능 향상에 대한 감소 수익이 발생할 수 있음을 의미합니다. 이 그림은 모델의 성능 향상에 대한 데이터 크기의 효과를 보여주는 중요한 결과를 시각적으로 보여주고 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: The impact of synthetic data size on multimodal embedding performance on MMEB.
> </details>



![](https://arxiv.org/html/2502.08468/x5.png)

> 🔼 그림 5는 본 논문에서 제안하는 mmE5 모델의 제로샷 성능을 보여줍니다.  다양한 훈련 설정(LoRA Rank, 배치 크기, 온도)에 따른 mmE5의 성능 변화를 MMEB(Multimodal Embedding Benchmark) 데이터셋을 기반으로 측정하였습니다. 효율적인 테스트를 위해 합성 데이터 280K를 사용했습니다.  각 그래프는 특정 하이퍼파라미터를 변화시키면서 mmE5의 성능이 어떻게 달라지는지 보여줍니다. 이를 통해 최적의 하이퍼파라미터 설정을 찾고 모델 성능을 개선하는 데 도움이 되는 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: The zero-shot performances of mmE5 with different training settings on MMEB (280K synthetic data for efficient test).
> </details>



![](https://arxiv.org/html/2502.08468/x6.png)

> 🔼 그림 6은 논문의 합성 검색 IT2IT 데이터의 예시 (1부)입니다. 이 부분에는 입력 이미지, 다면적 설명, 그리고 초기 생성 데이터가 포함되어 있습니다. 즉, 합성 데이터 생성 과정의 첫 번째 단계를 보여주는 것으로,  MLLM(대규모 다중 언어 모델)을 사용하여 실제 이미지를 기반으로 다양한 측면(일반적인 설명, 개체 수준 세부 정보, 상황적 특징, 작업 관련 발상)에서 이미지에 대한 설명을 생성하고, 이를 바탕으로 질의(query)와 양성 문서(positive document), 음성 문서(hard negative document)를 생성하는 과정을 보여줍니다. 각 데이터는 다양한 모드 조합과 언어를 다룹니다. 그림은 MLLM의 처리 과정을 시각적으로 보여주어, 데이터 생성의 전반적인 흐름을 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: An example of the synthetic Retrieval IT2IT data (part 1). This part includes the input images, the multi-aspect descriptions, and the initially generated data.
> </details>



![](https://arxiv.org/html/2502.08468/x7.png)

> 🔼 그림 7은 논문의 데이터 합성 과정을 보여주는 예시의 두 번째 부분입니다. 이 부분에서는 합성된 데이터에 대한 평가 결과와 개선 사항, 그리고 개선된 데이터를 보여줍니다. 구체적으로는, 합성된 데이터의 관련성, 타당성, 명확성, 다양성 측면에 대한 평가 점수와 함께 개선에 대한 구체적인 제안이 제시되어 있습니다. 또한, 평가를 바탕으로 수정된 질문, 긍정적 답변, 부정적 답변 등의 데이터가 제시되어 있습니다.  이는 논문에서 제시하는 고품질의 다중 모드 다국어 데이터 합성 프레임워크의 중요한 부분을 보여줍니다. 그림 7은 합성 데이터의 품질을 높이기 위한 반복적인 평가 및 개선 과정을 강조하여, 모델의 성능 향상에 기여하는 데이터의 질적 측면을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: An example of the synthetic Retrieval IT2IT data (part 2). This part includes the evaluation, possible improvements, and the revised data.
> </details>



![](https://arxiv.org/html/2502.08468/x8.png)

> 🔼 그림 8은 논문에서 제시된 합성 분류 IT2T 데이터의 예시를 보여줍니다.  이 그림은 영화 포스터 이미지 하나와, 해당 이미지를 기반으로 생성된 다양한 메타데이터들을 보여줍니다. 메타데이터에는 영화 장르 식별이라는 과제에 대한 지시 사항,  이미지를 설명하는 자세한 묘사,  정답 레이블,  오답 레이블, 데이터 평가, 개선 제안,  수정된 지시 사항 및 레이블 등이 포함되어 있습니다. 이러한 메타데이터들은 합성 데이터의 품질을 평가하고 개선하는 데 사용됩니다.  이 그림은 논문에서 제안하는 합성 데이터 생성 프레임워크의 일부분을 보여주는 구체적인 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: An example of the synthetic Classification IT2T data.
> </details>



![](https://arxiv.org/html/2502.08468/x9.png)

> 🔼 그림 9는 논문에서 제시된 합성 VQA IT2T 데이터의 예시를 보여줍니다. 그림은 어린 아이가 사과 상자에 앉아 사과를 먹는 모습을 담고 있습니다.  이 이미지를 바탕으로 질문과 답변이 생성되는데,  정답과 오답이 함께 제시되어 VQA 모델 학습에 활용될 수 있음을 보여줍니다.  정답은 '사과'이고 오답은 '바나나'입니다.  이를 통해 데이터의 질과 다양성을 보여주고, VQA 모델 학습에 활용될 수 있는 합성 데이터의 예시를 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: An example of the synthetic VQA IT2T data.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| 93 (English, Spanish, etc.) |{{< /table-caption >}}
> 🔼 표 2는 MMEB 벤치마크의 결과를 보여줍니다. MMEB 벤치마크는 분류, VQA, 검색, 시각적 기반 설정 등 네 가지 유형에 걸쳐 총 36가지 과제로 구성됩니다.  UniIR, MM-EMBED, GME 모델은 엄밀히 따지면 제로샷 모델이 아니며, UniIR과 MM-EMBED는 MBEIR 데이터셋 (Wei et al., 2024)을 사용하여 학습되었고, 이 데이터셋에는 MMEB에 포함된 10개의 검색 데이터셋이 포함되어 있습니다.  마찬가지로 GME는 UMRB 데이터셋 (Zhang et al., 2024b)을 사용하여 학습되었으며, 이 데이터셋은 MMEB와 14개의 데이터셋을 공유합니다. VLM2Vec의 경우 원 논문에서 보고된 고해상도 이미지를 사용한 LLaVA 기반 버전을 사용했습니다.  두 번째로 좋은 성능은 밑줄이 그어져 있고, 최고 성능은 굵게 표시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Results on MMEB benchmark, consisting of 36 tasks across four types: classification (Class.), VQA, retrieval (Retr.), and visual grounding (Ground.). † UniIR, MM-EMBED, and GME are not strictly zero-shot models. UniIR and MM-EMBED are trained on the MBEIR dataset Wei et al. (2024), which includes 10 retrieval datasets included in the MMEB. Similarly, GME is trained on the UMRB dataset Zhang et al. (2024b), which shares 14 datasets with the MMEB. For VLM2Vec, we use the LLaVA-based version with high-resolution images reported in its original paper. The second-best performances are underlined and the best performances are in bold.
> </details>

{{< table-caption >}}
| Classification, |
|---|---| 
| VQA, Retrieval|{{< /table-caption >}}
> 🔼 표 3은 XTD 벤치마크에 대한 결과를 보여줍니다. XTD 벤치마크는 7개 언어를 포함하는 텍스트-이미지 검색 작업입니다. 이 표는 다양한 모델들의 성능을 Recall@10 지표를 사용하여 비교 분석합니다.  각 모델의 7개 언어에 대한 성능과 평균 성능을 보여줍니다. 이를 통해 다국어 멀티모달 임베딩 모델의 다국어 성능을 평가하고 비교 분석하는 데 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Results on XTD benchmark, a text-to-image retrieval task covering seven languages.
> </details>

{{< table-caption >}}
| IT→I, T→IT, IT→IT, |
|---|---|---| 
| I→I, I→T, IT→T, T→I |{{< /table-caption >}}
> 🔼 이 표는 다양한 기초 다중 모드 언어 모델(MLLM)을 사용하여 mmE5 모델의 성능을 비교 분석한 결과를 보여줍니다.  mmE5는 제안된 고품질 합성 데이터셋으로 학습된 다중 모드 다국어 임베딩 모델입니다.  표에는 각 MLLM을 기반으로 학습된 mmE5 모델의 MMEB 벤치마크 평균 점수가 제시되어 있습니다. 이를 통해 다양한 MLLM이 mmE5의 성능에 미치는 영향을 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Performances of mmE5 with different MLLMs.
> </details>

{{< table-caption >}}
| Models | Class. | VQA | Retr. | Ground. | IND | OOD | Overall |
|---|---|---|---|---|---|---|---| 
| *Zero-shot Setting Models* |  |  |  |  |  |  |  |
| CLIP [Radford et al. (2021)] | 42.8 | 9.1 | 53.0 | 51.8 | - | - | 37.8 |
| BLIP2 [Li et al. (2023)] | 27.0 | 4.2 | 33.9 | 47.0 | - | - | 25.2 |
| SigLIP [Zhai et al. (2023)] | 40.3 | 8.4 | 31.6 | 59.5 | - | - | 34.8 |
| OpenCLIP [Cherti et al. (2023)] | 47.8 | 10.9 | 52.3 | 53.3 | - | - | 39.7 |
| E5-V [Jiang et al. (2024a)] | 21.8 | 4.9 | 11.5 | 19.0 | - | - | 13.3 |
| MagicLens [Zhang et al. (2024a)] | 38.8 | 8.3 | 35.4 | 26.0 | - | - | 27.8 |
| MMRet (w/ 26M synthetic data) | 47.2 | 18.4 | **56.5** | 62.2 | - | - | 44.0 |
| mmE5 (w/ 560K synthetic data) | **60.6** | **55.7** | 54.7 | **72.4** | - | - | **58.6** |
| *Partially Supervised Finetuning Models*<sup>†</sup> |  |  |  |  |  |  |  |
| UniIR [Wei et al. (2024)] | 42.1 | 15.0 | 60.1 | 62.2 | - | - | 42.8 |
| MM-EMBED [Lin et al. (2024)] | 48.1 | 32.2 | 63.8 | 57.8 | - | - | 50.0 |
| GME [Zhang et al. (2024b)] | 56.9 | 41.2 | 67.8 | 53.4 | - | - | 55.8 |
| *Supervised Finetuning Models* |  |  |  |  |  |  |  |
| CLIP [Radford et al. (2021)] | 55.2 | 19.7 | 53.2 | 62.2 | 47.6 | 42.8 | 45.4 |
| OpenCLIP [Cherti et al. (2023)] | 56.0 | 21.9 | 55.4 | 64.1 | 50.5 | 43.1 | 47.2 |
| VLM2Vec [Jiang et al. (2024b)] | **61.2** | 49.9 | 67.4 | **86.1** | 67.5 | 57.1 | 62.9 |
| MMRet [Zhou et al. (2024a)] | 56.0 | **57.4** | **69.9** | 83.6 | **68.0** | **59.1** | **64.1** |
| mmE5 (w/ synthetic data + labeled data) | **67.6** | **62.8** | **70.9** | **89.7** | **72.3** | **66.7** | **69.8** |{{< /table-caption >}}
> 🔼 표 5는 제한된 모델의 MMEB 성능을 보여줍니다. 효율적인 테스트를 위해 동일한 작업, 모드 유형 및 언어를 가진 280K 합성 데이터에 대한 제로샷 실험을 수행했습니다. 이 표는 합성 데이터의 다양한 측면(예: 시각적 해석, 자체 평가, 분류 데이터, VQA 데이터, 검색 데이터, 하드 네거티브)을 제거했을 때 mmE5 모델의 성능 변화를 보여줍니다. 이를 통해 각 구성 요소의 중요성을 평가하고 모델 성능에 미치는 영향을 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Performances of ablated models on MMEB. For efficient test, we conduct zero-shot experiments on 280K synthetic data, which has the same tasks, modality types and languages as the full synthetic data.
> </details>

{{< table-caption >}}
| Model | it | es | ru | zh | pl | tr | ko | Avg. |
|---|---|---|---|---|---|---|---|---|
| ALIGN Jia et al. (2021) | 87.9 | 88.8 | 82.3 | 86.5 | 79.8 | 73.5 | 76.6 | 82.2 |
| MURAL Jain et al. (2021) | 91.8 | 92.9 | 87.2 | 89.7 | 91.0 | 89.5 | 88.1 | 90.0 |
| VLM2Vec Jiang et al. (2024b) | 83.7 | 87.1 | 86.7 | 92.8 | 76.1 | 37.2 | 63.9 | 75.4 |
| jina Koukounas et al. (2024) | 93.6 | 94.1 | 89.8 | 91.8 | 94.3 | 92.7 | 90.1 | 92.3 |
| M-CLIP Carlsson et al. (2022) | 93.1 | 93.6 | 90.0 | 94.0 | 94.3 | 93.1 | 89.0 | 92.4 |
| GME Zhang et al. (2024b) | 95.1 | 96.4 | 92.3 | 96.4 | 94.9 | 89.8 | 93.6 | 94.1 |
| mmE5 (full) | 96.1 | 96.2 | 93.3 | 96.3 | 95.4 | 93.6 | 96.0 | 95.3 |
| w/ synthetic data only | 90.9 | 89.6 | 86.3 | 90.2 | 90.3 | 87.2 | 86.7 | 88.7 |
| w/ english synthetic data | 86.3 | 86.3 | 84.2 | 88.8 | 84.9 | 81.0 | 84.4 | 85.1 |{{< /table-caption >}}
> 🔼 표 6은 논문에서 제안하는 다중 모달 합성 데이터셋 mmE5의 통계량을 보여줍니다.  데이터셋은 세 가지 주요 다중 모달 임베딩 작업(분류, VQA, 검색)과 일곱 가지 모달 조합을 포함하고 있으며,  각 작업과 모달 조합별로 샘플 수를 상세히 제시합니다.  이를 통해 mmE5 학습에 사용된 데이터의 규모와 다양성을 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Statistics of the multimodal synthetic data used for training mmE5.
> </details>

{{< table-caption >}}
| Base MLLM | Avg. on MMEB |
|---|---| 
| Phi-3.5-V [Abdin et al. (2024)](https://arxiv.org/html/2502.08468/bib.bib1) | 61.0 |
| LLaVA-1.6 [Liu et al. (2023a)](https://arxiv.org/html/2502.08468/bib.bib21) | 65.8 |
| LLaMA-3-Vision [Meta (2024)](https://arxiv.org/html/2502.08468/bib.bib23) (Ours) | **69.8** |
| *Baselines (For Reference)* |  |
| VLM2Vec (Phi-3.5-V) | 60.1 |
| VLM2Vec (LLaVA-1.6) | 62.9 |
| MMRet (LLaVA-1.6) | 64.1 |
| VLM2Vec (LLaMA-3.2) | 64.8 |{{< /table-caption >}}
> 🔼 표 7은 Jiang et al.(2024b)의 MMEB 벤치마크에 포함된 각 데이터셋에서 제로샷 설정과 지도 학습 설정 모델의 상세 결과를 보여줍니다.  제로샷 설정에서는 CLIP, OpenCLIP, SigLIP, BLIP2, MagicLens, E5-V, MMRet, mmE5 등 다양한 모델의 성능을 비교 분석하고, 지도 학습 설정에서는 VLM2Vec, MMRet, mmE5 모델을 비교 분석합니다. 각 모델의 분류, VQA, 검색, 시각적 그라운딩 작업에 대한 정확도를 데이터셋별로 자세히 제시하여 모델 성능을 종합적으로 평가할 수 있도록 합니다.  표에는 각 작업 유형별(분류, VQA, 검색, 시각적 그라운딩) 및 모든 데이터셋에 대한 평균 점수도 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Detailed results of zero-shot setting and supervised setting models on each dataset of MMEB Jiang et al. (2024b).
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