---
title: "MegaPairs: Massive Data Synthesis For Universal Multimodal Retrieval"
summary: "MegaPairs는 VLM과 공개 도메인 이미지를 활용, 2600만 개 이상의 고품질 다중 모달 학습 데이터를 생성하여 범용 다중 모달 검색 성능을 획기적으로 향상시켰습니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Vision-Language Models", "🏢 Hong Kong University of Science and Technology",]
showSummary: true
date: 2024-12-19
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.14475 {{< /keyword >}}
{{< keyword icon="writer" >}} Junjie Zhou et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-20 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.14475" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.14475" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/megapairs-massive-data-synthesis-for" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

다중 모달 검색 기술은 **방대한 학습 데이터 부족**으로 발전에 어려움을 겪고 있습니다. 기존의 데이터 합성 방법들은 **데이터의 규모, 품질, 다양성 측면에서 한계**를 가지고 있었고, 대부분의 고품질 데이터는 **소수 연구팀만이 독점**하고 있었습니다.  이러한 문제는 다중 모달 검색 기술의 **범용성 및 성능 향상을 저해**하는 주요 원인이 됩니다.

본 논문에서는 **MegaPairs**라는 새로운 데이터 합성 방법을 제시합니다. MegaPairs는 **VLMs(Vision-Language Models)와 공개 도메인 이미지를 활용**, 다양한 유형의 상관관계를 갖는 이미지 쌍을 효율적으로 추출하고, 이를 바탕으로 **대규모의 고품질 다중 모달 학습 데이터셋**을 생성합니다.  **2600만 개 이상**의 학습 데이터를 생성하여 다양한 벤치마크에서 **최첨단의 제로샷 성능**을 달성하였으며, 추가적인 파인튜닝을 통해 성능을 더욱 향상시켰습니다.  MegaPairs 데이터셋과 MMRet 모델, 데이터 생성 파이프라인을 **공개**함으로써, 다중 모달 검색 기술 분야의 발전에 기여할 것으로 기대됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} MegaPairs는 VLM과 공개 도메인 이미지를 이용해 2600만 개 이상의 고품질 다중 모달 학습 데이터를 생성하는 새로운 방법론을 제시합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} MegaPairs로 학습된 MMRet 모델은 기존 최고 성능 모델들을 능가하는 제로샷 성능을 다양한 벤치마크에서 보여줍니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} MegaPairs 데이터셋과 MMRet 모델, 데이터 생성 파이프라인은 공개적으로 제공되어 향후 다중 모달 검색 기술 발전에 기여할 것입니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대규모 고품질 다중 모달 데이터셋 합성의 어려움을 해결**하고, 이를 통해 **범용 다중 모달 검색 기술 발전에 크게 기여**하는 방법론을 제시합니다. 기존 연구의 한계를 극복하고 새로운 연구 방향을 제시함으로써, **다양한 분야의 연구자들에게 중요한 의미**를 지닙니다. 특히, **대규모 데이터셋 구축의 어려움을 겪는 다중 모달 연구 분야의 발전에 큰 영향**을 미칠 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.14475/x1.png)

> 🔼 그림 1은 다중 모드 triplet 생성 파이프라인을 보여줍니다. (a)에서는 여러 유사성 모델을 사용하여 다양한 상관관계를 가진 이미지 쌍을 마이닝하는 과정을, (b)에서는 개방형 지시어를 생성하는 과정을 보여줍니다.  여러 유사성 모델을 사용함으로써 이미지 쌍의 다양한 상관관계를 도입하여 다양한 데이터를 생성합니다.  (a) 단계에서는 CLIP 비전 인코더, DINO 비전 인코더, CLIP 텍스트 인코더 세 가지 모델을 사용하여 이미지 간의 다양한 유사성을 파악합니다.  (b) 단계에서는 MLLM(다중 모드 대규모 언어 모델)과 LLM(대규모 언어 모델)을 사용하여 이미지 간의 관계를 설명하는 개방형 지시어를 생성합니다. 이를 통해 다양하고 높은 품질의 데이터를 생성하여 다운스트림 작업의 성능을 향상시킵니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Construction pipeline of multimodal triplets: (a) mining of image pairs, (b) generation of open-ended instructions. Multiple similarity models are used to introduce diversified correlations for the image pairs.
> </details>





{{< table-caption >}}
Task|Zero-shot|Zero-shot|Zero-shot|Zero-shot|Zero-shot|Zero-shot|Zero-shot|Zero-shot|Fine-Tune|Fine-Tune
---|---|---|---|---|---|---|---|---|---|---
|CLIP|OpenCLIP|SigLIP|BLIP2|MagicLens|E5-V|UniIR|MMRet|VLM2Vec|MMRet|
Classification (10 tasks)|ImageNet-1K|N24News|HatefulMemes|VOC2007|SUN397|Place365|ImageNet-A|ImageNet-R|ObjectNet|Country-211
---|---|---|---|---|---|---|---|---|---|---
|55.8|34.7|51.1|50.7|43.4|28.5|25.5|75.6|43.4|19.2
|63.5|38.6|51.7|52.4|68.8|37.8|14.2|83.0|51.4|16.8
|45.4|13.9|47.2|64.3|39.6|20.0|42.6|75.0|40.3|14.2
|10.3|36.0|49.6|52.1|34.5|21.5|3.2|39.7|20.6|2.5
|48.0|33.7|49.0|51.6|57.0|31.5|8.0|70.9|31.6|6.2
|9.6|23.4|49.7|49.9|33.1|8.6|2.0|30.8|7.5|3.1
|53.7|33.9|51.0|62.7|61.7|38.0|12.9|61.6|37.1|8.8
|49.1|45.8|51.0|74.6|60.1|35.3|31.6|66.2|49.2|9.3
|65.6|79.5|67.1|88.6|72.7|42.6|19.3|70.2|29.5|13.0
|58.8|71.3|53.7|85.0|70.0|43.0|36.1|71.6|55.8|14.7
All Classification|42.8|47.8|40.3|27.0|38.8|21.8|42.1|47.2|54.8|56.0
VQA (10 tasks)|OK-VQA|A-OKVQA|DocVQA|InfographicsVQA|ChartQA|Visual7W|ScienceQA|VizWiz|GQA|TextVQA
---|---|---|---|---|---|---|---|---|---|---
|7.5|3.8|4.0|4.6|1.4|4.0|9.4|8.2|41.3|7.0
|11.5|3.3|5.3|4.6|1.5|2.6|10.2|6.6|52.5|10.9
|2.4|1.5|4.2|2.7|3.0|1.2|7.9|2.3|57.5|1.0
|8.7|3.2|2.6|2.0|0.5|1.3|6.8|4.0|9.7|3.3
|12.7|2.9|3.0|5.9|0.9|2.5|5.2|1.7|43.5|4.6
|8.9|5.9|1.7|2.3|2.4|5.8|3.6|2.6|7.8|3.2
|24.5|10.6|5.6|5.0|1.8|12.3|11.6|19.2|49.3|10.6
|28.0|11.6|12.6|10.6|2.4|9.0|23.3|25.9|41.3|18.9
|63.2|50.2|78.4|40.8|59.0|47.7|43.4|39.2|60.7|66.1
|73.3|56.7|78.5|39.3|41.7|49.5|45.2|51.7|59.0|79.0
All VQA|9.1|10.9|8.4|4.2|8.3|4.9|15.0|18.4|54.9|57.4
Retrieval (12 tasks)|VisDial|CIRR|VisualNews_t2i|VisualNews_i2t|MSCOCO_t2i|MSCOCO_i2t|NIGHTS|WebQA|FashionIQ|Wiki-SS-NQ
---|---|---|---|---|---|---|---|---|---|---
|30.7|12.6|78.9|79.6|59.5|57.7|60.4|67.5|11.4|55.0
|25.4|15.4|74.0|78.0|63.6|62.1|66.1|62.1|13.8|44.6
|21.5|15.1|51.0|52.4|58.3|55.0|62.9|58.1|20.1|55.1
|18.0|9.8|48.1|13.5|53.7|20.3|56.5|55.4|9.3|28.7
|24.8|39.1|50.7|21.1|54.1|40.0|58.1|43.0|11.2|18.7
|9.2|6.1|13.5|8.1|20.7|14.0|4.2|17.7|2.8|8.6
|37.6|53.2|63.6|68.8|72.0|74.1|69.7|86.3|39.3|11.3
|62.6|65.7|45.7|53.4|68.7|56.7|59.4|76.3|31.5|25.4
|73.3|47.8|67.2|70.7|70.6|66.5|66.1|88.1|12.9|56.6
|83.0|61.4|74.2|78.1|78.6|72.4|68.3|90.2|54.9|24.9
All Retrieval|53.0|52.3|31.6|33.9|35.4|11.5|60.1|56.5|62.3|69.9
Visual Grounding (4 tasks)|MSCOCO|RefCOCO|RefCOCO-matching|Visual7W-pointing
---|---|---|---|---
|33.8|56.9|61.3|55.1
|34.5|54.2|68.3|56.3
|46.4|70.8|50.8|70.1
|28.9|47.4|59.5|52.0
|22.1|22.8|35.6|23.4
|10.8|11.9|38.9|14.3
|46.6|67.8|62.9|71.3
|42.7|69.3|63.2|73.5
|67.3|84.7|79.2|86.8
|76.8|89.8|90.6|77.0
All Visual Grounding|51.8|53.3|59.5|47.0|26.0|19.0|62.2|62.2|79.5|83.6
Final Score (36 tasks)|All|All IND|All OOD
---|---|---|---
|37.8|37.1|38.7
|39.7|39.3|40.2
|34.8|32.3|38.0
|25.2|25.3|25.1
|27.8|31.0|23.7
|13.3|14.9|11.5
|42.8|44.7|40.4
|44.0|43.5|44.3
|60.1|66.5|52.0
|64.1|59.1|68.0{{< /table-caption >}}

> 🔼 표 1은 다양한 구성 이미지 검색(CIR) 벤치마크에 대한 제로샷 검색 성능을 보여줍니다. MMRet 이전 최고 성능은 별표(*)로 표시되어 있으며, GPT-3.5나 Qwen-1.5-32B 와 같이 여러 구성 요소가 있는 방법은 † 로 표시되어 있으며, 알려진 크기의 구성 요소 매개변수 수를 보고합니다. CoCa 기반 MagicLens 모델은 독점적이므로 ‡으로 표시됩니다.  굵은 밑줄은 각 모델 규모에 대한 최고 및 두 번째 최고 성능을 나타냅니다. MMRet 모델은 다양한 모델 크기와 벤치마크에서 최첨단 결과를 달성하며, 주요 벤치마크인 CIRCO에서 이전 최고 성능을 8.1% 상회합니다. 이는 제로샷 CIR 방법을 크게 발전시킨 것입니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Zero-shot retrieval performance on various CIR benchmarks. ∗ denotes the previous best performance for each benchmark prior to MMRet. † indicates methods with multiple components (e.g., GPT-3.5, Qwen1.5-32B); we report # parameters of components with known sizes. The CoCa-based MagicLens‡ models are proprietary. Results in bold and underline denote the best and second-best performances for each model scale, respectively. Our MMRet model achieves state-of-the-art results across different model sizes and benchmarks, surpassing the previous SOTA by 8.1% on the main benchmark CIRCO, significantly advancing zero-shot CIR methods.
> </details>





### In-depth insights


#### MegaPairs Data Synth
MegaPairs 데이터 합성은 기존의 다모달 검색 모델 학습에 사용되는 데이터의 부족 문제를 해결하기 위해 제안된 대규모 합성 데이터셋 생성 방법입니다. **기존 방법들의 한계인 확장성, 품질, 다양성, 가용성 문제를 극복**하기 위해, MegaPairs는 개방형 도메인 이미지와 강력한 Vision-Language Model(VLM) 및 Large Language Model(LLM)을 활용합니다. **여러 유사성 모델을 이용하여 다양한 상관관계를 가진 이미지 쌍을 추출**하고, 이를 VLM과 LLM을 통해 **다양한 종류의 오픈엔디드 지시어로 주석**을 달아, **기존 데이터셋보다 훨씬 많은 양의 고품질 다모달 학습 데이터를 효율적으로 생성**하는 것이 특징입니다.  본 논문에서 제시된 방법은 **합성 데이터의 품질을 높이고 확장성을 확보하여 다모달 검색 기술 발전에 크게 기여**할 것으로 예상됩니다.  **오픈소스 모델에 의존**하기 때문에 비용 효율적이며, **지속적인 성능 개선**이 가능하다는 점 또한 주목할 만합니다.

#### MMRet Model Intro
MMRet 모델 소개는 논문에서 제시된 핵심 다중 모드 검색 모델의 구조와 기능에 대한 심층적인 이해를 제공합니다. **CLIP 기반 MMRet과 MLLM 기반 MMRet** 두 가지 주요 아키텍처를 통해 다양한 다중 모드 입력에 대한 범용적인 임베딩을 달성하는 방식을 설명합니다. **CLIP 기반 모델은 이미지와 텍스트를 독립적으로 인코딩**하여 이들의 결합된 임베딩을 생성하는 반면, **MLLM 기반 모델은 비전 트랜스포머와 대규모 언어 모델을 통합**하여 다양한 형태의 입력을 토큰 시퀀스로 처리하고 통합된 표현을 생성합니다. 두 아키텍처 모두 **다중 모드 대조 학습(Multimodal Contrastive Learning)**을 통해 다양한 다중 모드 검색 작업에 대한 일반화 능력을 향상시킵니다. 특히, **task-specific instructions**를 사용하여 모델의 일반화 능력 향상에 중점을 두고 있으며, 이는 다양한 하위 작업에 대한 적응력을 높이는 데 기여합니다. 이러한 MMRet 모델의 다양한 구조와 학습 방법은 다중 모드 검색 분야의 발전에 상당한 기여를 할 것으로 기대됩니다.

#### Zero-Shot CIR Tests
논문에서 "Zero-Shot CIR Tests" 제목의 섹션은 **영상 검색(CIR)** 모델의 제로샷 성능을 평가하는 데 중점을 둡니다. 이는 모델이 사전 훈련된 지식만을 사용하여 본 적 없는 데이터셋에 대해 성능을 평가하는 것을 의미합니다.  **다양한 CIR 벤치마크**에서 제로샷 성능을 평가함으로써, 해당 모델이 **새로운 유형의 데이터셋에 얼마나 잘 적응하는지**를 측정할 수 있습니다.  이러한 평가는 **모델의 일반화 능력**과 **실용적인 적용 가능성**을 판단하는 데 중요한 지표가 됩니다. 특히 대규모 합성 데이터셋을 사용한 모델은 기존 데이터셋으로 훈련된 모델에 비해 제로샷 성능이 얼마나 향상되었는지 비교 분석하여, **데이터 합성 전략의 효과성**을 검증할 수 있을 것입니다. 따라서 이 섹션은 논문의 핵심 주장을 뒷받침하는 실험 결과를 보여주는 중요한 부분이며, **모델의 성능과 데이터셋의 질** 모두를 평가하는 데 유용한 정보를 제공합니다.

#### MMEB Benchmark
본 논문에서 다룬 MMEB(Massive Multimodal Embedding Benchmark)는 **다양한 모달리티(텍스트, 이미지)를 결합한 여러 과제들을 포괄하는 종합적인 벤치마크**입니다.  **영상 질의응답, 이미지 검색, 분류 등 다양한 다중 모달리티 작업의 성능을 평가**하는 데 사용되며,  **모델의 일반화 능력과 다양한 작업에 대한 적응력을 측정**하는 데 중요한 역할을 합니다.  MMEB는 기존 벤치마크의 한계를 극복하고 **더욱 포괄적이고 까다로운 평가를 제공**하여 다중 모달리티 모델의 발전에 기여합니다. 특히, **영상과 텍스트를 함께 처리하는 능력**을 중점적으로 평가하여 **진정한 의미의 다중 모달리티 이해 능력을 갖춘 모델**의 개발을 촉진합니다. 따라서, MMEB 벤치마크에서 우수한 성능을 달성하는 것은 **다양한 실제 응용 분야에 적용 가능한 견고하고 유연한 다중 모달리티 모델**을 개발했음을 시사합니다.  **대규모 데이터셋과 다양한 과제들을 포함**하여,  **연구의 신뢰성과 실용성을 높이는 데 기여**한다는 점에서 중요한 의미를 가집니다.

#### Future Work
본 논문에서 제시된 MegaPairs 데이터셋과 MMRet 모델은 다양한 모달리티 검색 과제에 대한 성능 향상을 보여주었지만, **향후 연구 방향**은 여전히 많습니다.  **더욱 다양하고 정교한 데이터 생성 기법** 연구가 필요하며, **다양한 유형의 multimodal instruction을 포함하는 데이터 확장**을 통해 더욱 범용적인 모델 개발이 가능할 것입니다. 특히,  **다양한 언어 지원 및 다양한 문화적 맥락을 고려한 데이터셋 구축**은 모델의 범용성을 높이는 데 중요한 역할을 합니다.  또한, **현재 모델의 효율성 향상을 위한 경량화 연구**도 필요하며, **메모리 및 연산 자원 소모량을 줄이는 최적화 기법** 연구가 중요합니다.  **다른 종류의 multimodal task (예: 비디오 검색)에 대한 확장성 연구**와 **설명 가능성(explainability) 향상을 위한 연구** 역시 미래 연구의 주요 과제입니다.  **MegaPairs 데이터셋의 공개를 통한 외부 연구자들과의 협력**을 통해 이러한 과제에 대한 해결책을 더욱 빠르게 찾을 수 있을 것으로 예상됩니다. 마지막으로, **윤리적인 측면을 고려한 데이터 관리 및 모델 사용 가이드라인 수립**은 매우 중요한 부분입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.14475/x2.png)

> 🔼 그림 2는 MegaPairs 데이터셋 크기가 증가함에 따라 MMRet-base 모델의 성능 변화를 보여줍니다.  x축은 MegaPairs 데이터셋의 크기를 나타내고, y축은 네 가지 CIR(Composed Image Retrieval) 벤치마크(CIRCO, CIRR, FashionIQ, GeneCIS)에 대한 MMRet-base 모델의 성능 지표(mAP@5)를 나타냅니다.  점선은 MagicLens-B(CLIP) 모델이 36.7M개의 데이터 쌍으로 학습되었을 때의 성능을 보여주는 기준선 역할을 합니다.  이 그래프는 MegaPairs 데이터셋이 MMRet-base 모델의 성능 향상에 미치는 영향을 데이터셋 크기 변화에 따라 시각적으로 보여주며,  MegaPairs의 확장성과 효율성을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Performance scaling of MMRet-base on the MegaPairs as data size increases. The dashed lines indicate the performance of MagicLens-B (CLIP) trained on their dataset of 36.7M data pairs.
> </details>



![](https://arxiv.org/html/2412.14475/x3.png)

> 🔼 이 그림은 MLLM(다중 모드 대규모 언어 모델)을 위한 구체적인 프롬프트를 보여줍니다.  이 프롬프트는 두 이미지 간의 공통점과 차이점을 자세히 설명하도록 설계되었으며, 생성된 설명의 다양성을 높이기 위해 WORD_NUM 값을 60에서 100까지 다양하게 사용합니다.  즉, 모델이 두 이미지의 관계를 정확하고 다양하게 이해하고 설명할 수 있도록 유도하는 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: The specific prompts for MLLM. The value of WORD_NUM ranges from 60 to 100 in our practical data generation to enhance the diversity of the generated description.
> </details>



![](https://arxiv.org/html/2412.14475/x4.png)

> 🔼 그림 4는 LLM을 위한 구체적인 프롬프트를 보여줍니다. 그림에서는 두 가지 시연이 나와 있지만, 실제 데이터 생성 과정에서는 50개의 프롬프트 중에서 5개를 무작위로 선택하여 LLM에 입력합니다.  LLM은 제공된 두 이미지의 상관관계를 바탕으로 타겟 이미지를 검색하는 데 사용할 수 있는 흥미로운 텍스트 질의를 생성합니다. 프롬프트는 소스 이미지의 세부 정보를 드러내지 않도록 유사점을 비특정 대명사로 바꾸고 간결하게 유지하는 것을 목표로 합니다. 또한 타겟 이미지에만 있는 고유한 차이점을 자세히 설명합니다.  이러한 접근 방식은 다양한 질의를 생성하여 모델의 일반화 성능을 향상시키는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: The specific prompts for LLM. The figure showcases two demonstrations, while in our practical data generation process, five demonstrations are randomly selected from a pool of 50 and fed into the LLM.
> </details>



![](https://arxiv.org/html/2412.14475/x5.png)

> 🔼 그림 5는 MegaPairs 데이터셋의 시각적 예시를 보여줍니다. 각 행은 하나의 예시를 나타내며, 질의 항목(쿼리 이미지와 해당 캡션)은 파란색 사각형으로 강조 표시되어 있고, 타겟 항목(관련 이미지들)은 점선 상자로 표시되어 있습니다. 각 행에는 질의 이미지와 시각적으로 유사한 이미지와 의미적으로 관련된 이미지(시각적 특징을 넘어서는 이미지)가 모두 포함되어 있습니다. 예를 들어, 4번째 행의 쿼리 이미지는 '둥근 오토만, 푹신한 표면'이라는 캡션과 함께 오토만 이미지가 있는데, 이와 시각적으로 유사한 이미지(소파 등)와 의미적으로 관련된 이미지(차량 내부, 거실 벽 등)가 함께 제시됩니다. 이는 시각적 유사성뿐 아니라 의미적 관련성까지 고려하여 MegaPairs 데이터셋을 구성했음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: The visualized examples of MegaPairs. Each row represents a single example, with the query item highlighted in a blue rectangle and the target items enclosed within a dashed box.
> </details>



![](https://arxiv.org/html/2412.14475/x6.png)

> 🔼 그림 6은 CLIP-L 백본을 사용한 MMRet과 MagicLens의 제로샷 CIR 작업에 대한 상위 5개 검색 이미지를 보여줍니다. 질의는 파란색 배경으로 표시되며, 가장 정확한 이미지는 녹색 윤곽선으로 표시됩니다. 이 그림은 다양한 질의에 대해 두 모델이 검색한 결과를 비교하여, MMRet의 성능 우수성을 시각적으로 보여주는 역할을 합니다. 각 질의에 대해 MMRet은 MagicLens보다 더 관련성이 높은 이미지들을 상위에 배치하는 경향을 보입니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Top-5 retrieved images of MMRet and MagicLens on zero-shot CIR tasks, both using the CLIP-L backbone. Queries are shown with a blue background, and the most correct retrieved images are marked with green outlines.
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