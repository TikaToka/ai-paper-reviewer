---
title: "LLaVA-UHD v2: an MLLM Integrating High-Resolution Feature Pyramid via Hierarchical Window Transformer"
summary: "LLaVA-UHD v2는 계층적 윈도우 변환기를 이용, 고해상도 특징 피라미드를 통합하여 다양한 시각적 세부 정보를 포착하는 혁신적인 다중 모달 언어 모델입니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Vision-Language Models", "🏢 Tsinghua University",]
showSummary: true
date: 2024-12-18
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.13871 {{< /keyword >}}
{{< keyword icon="writer" >}} Yipeng Zhang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-19 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.13871" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.13871" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/llava-uhd-v2-an-mllm-integrating-high" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)에 시각 정보를 통합하는 것은 시각적 질문 응답과 같은 다양한 작업에 큰 진전을 가져왔습니다. 그러나 기존의 비전 트랜스포머(ViT) 기반 MLLM은 다양한 시각적 수준의 정보가 부족하여 다양한 의미적 세분성과의 정렬을 방해하여 보편적인 MLLM 작업 해결에 만족스럽지 못한 성능을 보였습니다.  이러한 문제는 다양한 시각적 세부 정보를 포착하고 통합하는 고해상도 특징 피라미드를 구축하지 못하기 때문입니다.

본 논문에서는 계층적 윈도우 변환기를 중심으로 한 고급 MLLM인 LLaVA-UHD v2를 제시합니다. LLaVA-UHD v2는 고해상도 특징 피라미드를 구성하고 통합함으로써 다양한 시각적 세분성을 포착합니다.  역 피라미드와 계층적 윈도우 어텐션이라는 두 가지 주요 모듈로 구성된 Hiwin 변환기는 다양한 시각적 세분성을 포착하고, 여러 수준의 특징 맵을 압축하여 언어 생성에 필요한 다양한 의미적 세분성을 제공합니다. 실험 결과, LLaVA-UHD v2는 여러 벤치마크에서 기존 MLLM보다 우수한 성능을 보였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 계층적 윈도우 변환기를 사용하여 고해상도 특징 피라미드를 효과적으로 통합하는 새로운 방법 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 기존 MLLM 대비 14개의 벤치마크에서 평균 3.7% 향상된 성능 달성 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 모든 데이터, 모델 및 코드 공개를 통해 후속 연구 지원 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **다양한 시각적 세부 정보를 통합하여 언어 모델의 성능을 향상시키는 새로운 방법**을 제시합니다.  **고해상도 특징 피라미드를 계층적 윈도우 변환기를 통해 통합**하는 것은 시각 언어 모델링 분야에서 중요한 발전이며, 특히 고해상도 이미지 이해에 필요한 다양한 시각적 정보를 효과적으로 처리하는 데 기여합니다.  **공개된 데이터, 모델 및 코드**는 후속 연구를 위한 중요한 자원이 될 것입니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.13871/x1.png)

> 🔼 본 그림은 논문에서 제안하는 LLaVA-UHD v2 모델과 기존 다중 모달 대규모 언어 모델(MLLM)의 비교를 보여줍니다. (a)는 기존 MLLM들이 일반적으로 ViT 특징을 MLP 또는 perceiver re-sampler를 사용하여 언어 공간에 정렬하는 방식을 나타내며, 이는 시각적 세부 정보가 부족함을 의미합니다. (b)는 여러 개의 시각적 인코더를 결합하는 것이 보편적이지 않고 계산적으로 집약적임을 보여줍니다. (c)는 LLaVA-UHD v2가 계층적 윈도우 변환기를 사용하여 역 특징 피라미드를 구축하고 시각 토큰으로 압축하여 다양한 의미적 세분성을 제공함으로써 언어 생성에 도움을 주는 방식을 보여줍니다.  즉, LLaVA-UHD v2는 다양한 시각적 해상도를 효과적으로 활용하여 언어 생성 성능을 향상시킨다는 점을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Comparison of LLaVA-UHD v2 with other MLLMs. (a) MLLMs typically align ViT features to language space using MLPs [63] or perceiver re-samplers [6, 52], lacking visual granularity. (b) Combining multiple visual encoders is non-universal and computationally intensive. (c) LLaVA-UHD v2 employs the Hiwin transformer to build an inverse feature pyramid and compress it into visual tokens, providing various semantic granularity for language generation.
> </details>





{{< table-caption >}}
| Method | #Data | MaxRes. | #FLOPs. | Avg. | VQA<sup>D</sup> | Bench<sup><i>OCR</i></sup> | VQA<sup>C</sup> | VQA<sup>T</sup> | AI2D | SQA | MMMU<sup>v</sup> | GQA | SEED<sup>I</sup> | MMB | MME<sup>P</sup> | RWQA | Bench<sup><i>HR</i></sup> |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---| 
| Qwen-VL [10] | 1.45B | 448×448 | 4.0T | 56.9 | 62.6 | 48.8 | **66.3** | 61.5 | 57.7 | 68.2 | 35.9 | 57.5 | 65.4 | 61.8 | 74.4 | 49.3 | 30.5 |
| MiniGPT-v2 [16] | 326M | 448×448 | 4.0T | - | - | 15.7 | - | - | - | - | - | 60.3 | - | - | - | - | - |
| mPLUG-Owl2 [105] | 401M | 448×448 | 1.7T | - | - | - | - | 58.2 | - | 68.7 | - | 56.1 | 57.8 | 64.5 | 72.5 | - | - |
| UReader [104] | 86M | 896×1120 | 20.3T | - | 65.4 | - | 59.3 | 57.6 | - | - | - | - | - | - | - | - | - |
| LLaVA-1.5 [63] | 1.22M | 336×336 | 8.0T | 49.0 | 21.8 | 31.8 | 17.8 | 45.5 | 55.5 | 66.8 | 37.0 | 62.0 | 65.8 | 66.5 | 75.3 | 54.8 | 36.1 |
| SPHINX-2k [60] | 1.01B | 762×762 | 42.2T | - | - | - | - | 61.2 | - | <u>**70.6**</u> | - | 63.1 | <u>**71.6**</u> | 65.9 | 73.6 | - | - |
| SPHINX-X [28] | 15.3M | 448×448 | 21.3T | - | 56.3 | - | 39.7 | 58.1 | 63.0 | 70.4 | - | 56.2 | 68.8 | 57.9 | 63.0 | - | - |
| LLaVA-HR [73] | 1.22M | 1024×1024 | 24.3T | - | - | - | - | 67.1 | - | 65.1 | - | 64.2 | 64.2 | - | <u>**77.7**</u> | - | - |
| VILA [56] | 51M | 336×336 | 8.2T | - | - | - | - | 64.4 | - | 68.2 | - | 62.3 | 61.1 | <u>**68.9**</u> | 76.7 | - | - |
| Honey-bee [15] | 52.5M | 336×336 | 2.6T | - | - | - | - | - | - | - | 35.3 | - | 64.5 | <u>**70.1**</u> | <u>**79.2**</u> | - | - |
| Mini-Gemini [54] | 3.0M | 672×672 | 54.6T | 59.4 | 61.9 | 47.7 | 47.4 | 65.2 | <u>**68.2**</u> | 69.6 | 36.8 | <u>**64.5**</u> | 66.9 | 65.8 | 77.3 | 51.1 | <u>**50.1**</u> |
| Monkey [55] | 1.40B | 896×1344 | 28.0T | 59.2 | <u>**66.5**</u> | 51.4 | <u>**65.1**</u> | 67.6 | 62.6 | 69.4 | <u>**38.9**</u> | 60.7 | 64.3 | 59.8 | 73.6 | 51.6 | 38.0 |
| LLaVA-Next [62] | 1.34M | 672×672 | 44.4T | 61.0 | 63.6 | <u>**53.2**</u> | 54.3 | 64.9 | 67.0 | 70.1 | 35.8 | 64.2 | <u>**70.2**</u> | 67.4 | 76.0 | <u>**57.8**</u> | 47.9 |
| LLaVA-UHD v2 (ours) | 1.42M | 1008×672 | 17.5T | **63.2** | **68.1** | **53.9** | 64.5 | **67.6** | **70.5** | **71.3** | <u>**38.2**</u> | **65.4** | 70.0 | 68.2 | 74.7 | **58.2** | **51.5** |{{< /table-caption >}}

> 🔼 표 1은 여러 벤치마크에서 주요 모델들의 성능을 비교한 표입니다. 공정한 비교를 위해 Vicuna-7B와 같이 7B 수준의 LLM을 사용한 방법만을 보고했습니다. #Data는 MLLM의 사전 훈련 및 지도 학습에 사용된 데이터의 양을 나타냅니다. MaxRes는 MLLM이 접근할 수 있는 최대 해상도이고, Avg는 13개의 벤치마크에 대한 평균 결과입니다. 약어는 다음과 같습니다. VQAD: DocVQA, BenchOCR: OCR-Bench, VQAC: ChartQA, VQAT: TextVQA, SQA: Science-QA, MMMUv: MMMU-val, SEEDI: SEED-Image, MMEP: MME의 인식 하위 집합, RWQA: RealWorldQA, BenchHR: HR-Bench.
> <details>
> <summary>read the caption</summary>
> Table 1: Main performance on popular benchmarks. For a fair comparison, we only report the method using 7B level LLM (e.g.formulae-sequence𝑒𝑔e.g.italic_e . italic_g ., Vicuna-7B). #Data denotes the volume of overall data during MLLM pre-training and supervised fine-tuning. “MaxRes.” is the maximum accessible resolution of MLLM. “Avg.”: average results of 13 benchmarks. “VQAD: DocVQA. “BenchOCR”: OCR-Bench. “VQAC”: ChartQA. “VQAT”: TextVQA. “SQA”: Science-QA. “MMMUv”: MMMU-val. “SEEDI”: SEED-Image. “MMEP”: perception sub-set of MME. “RWQA”: RealWorldQA. “BenchHR”: HR-Bench.
> </details>





### In-depth insights


#### Visual Granularity
본 논문은 다양한 시각적 세부 수준을 포착하는 계층적 윈도우 변환기를 중심으로 하는 고급 다중 모달 대규모 언어 모델(MLLM)인 LLaVA-UHD v2를 제시합니다. **시각적 세분성(Visual Granularity)**은 다양한 의미적 과립성에 맞춰 언어 생성에 필요한 정보를 제공하는 핵심 개념입니다. 저해상도 특징과 고해상도 특징을 통합하여 다양한 시각적 세부 수준을 포착하고, 계층적 윈도우 어텐션 메커니즘을 통해 다중 수준의 특징 맵을 효율적으로 압축합니다.  **역 특징 피라미드(Inverse Feature Pyramid)**를 통해 이미지 피라미드의 고주파 세부 정보를 활용하여 다양한 시각적 세분성을 캡처하는 것이 핵심입니다. 이를 통해 **시각적 지각 능력 향상**과 **다양한 시각적 다중 모달 작업에 대한 성능 향상**을 가져옵니다. 특히 문서 중심 시각적 질문 응답, 시각적 그라운딩, 고해상도 이미지 인식 등 다양한 벤치마크에서 기존 MLLM을 능가하는 우수한 성능을 보여줍니다. 따라서 **시각적 세분성의 효과적 통합**은 MLLM의 성능 향상에 중요한 역할을 한다는 것을 알 수 있습니다.

#### Hiwin Transformer
본 논문에서 제시된 Hiwin Transformer는 **고해상도 특징 피라미드를 계층적으로 통합**하는 혁신적인 비전-언어 프로젝터입니다. 기존의 단일 스케일 특징에 의존하는 ViT 기반 MLLM의 한계를 극복하기 위해 역피라미드 구조를 통해 다양한 시각적 세밀도를 포착하고, 계층적 윈도우 어텐션을 통해 다중 레벨 특징 맵을 효율적으로 압축합니다.  **역피라미드 구조**는 ViT에서 파생된 특징 업샘플링 과정을 통해 이미지 피라미드의 고주파 정보를 활용하여 구축되며, **계층적 윈도우 어텐션**은 크로스 스케일 윈도우 내 주요 샘플링 특징에 집중하여 다중 레벨 특징을 효과적으로 압축합니다.  결과적으로, Hiwin Transformer는 다양한 시각적 세밀도를 제공하여 언어 생성 작업의 다양한 의미적 과립도와의 정렬을 개선하며, 여러 벤치마크에서 기존 MLLM을 능가하는 성능을 보여줍니다. **JBU 모듈**과의 결합은 고해상도 특징을 효과적으로 활용하고 고주파 정보를 통합하는 데 중요한 역할을 수행합니다.  **전체적으로, Hiwin Transformer는 고해상도 영상 이해를 위한 MLLM의 성능 향상에 기여하는 중요한 요소**입니다.

#### Feature Pyramid
본 논문에서 제시된 Feature Pyramid는 **다양한 시각적 세부 정보와 고차원 의미를 효과적으로 통합**하는 핵심 요소입니다. 기존의 단일 스케일 특징 벡터 표현 방식의 한계를 극복하기 위해, **고해상도 특징 피라미드**를 구축하여 다양한 수준의 시각적 정보를 포착합니다. 이는 역 피라미드 구조를 통해 고주파수 세부 정보를 활용하고, 계층적 윈도우 어텐션을 통해 다중 스케일 특징 맵을 효율적으로 압축함으로써 구현됩니다. **역 피라미드는 ViT-파생 특징 업샘플링 과정을 통해 고해상도 특징을 생성**하고, **계층적 윈도우 어텐션은 다양한 스케일의 윈도우 내 주요 샘플링 특징에 집중**하여 다중 수준 특징을 효율적으로 압축합니다. 이러한 방식은 다양한 시각적 세부 정보와 고차원 의미를 포착하여 언어 생성에 필요한 다양한 의미적 세분성을 제공함으로써, 기존의 MLLM 모델 성능을 향상시킵니다.

#### MLLM Enhancement
본 논문은 다양한 시각적 수준의 정보 부족이 보편적인 다중 모달 대규모 언어 모델(MLLM) 작업 해결에 대한 성능 저하로 이어진다는 점을 **강조**합니다. 이러한 문제를 해결하기 위해, 고해상도 특징 피라미드를 계층적 윈도우 변환기를 통해 통합하는 LLaVA-UHD v2를 제시합니다. **계층적 윈도우 변환기**는 고해상도 특징 피라미드를 구성하고 통합하여 다양한 시각적 세분성을 포착할 수 있도록 합니다.  이는 역 특징 피라미드와 계층적 윈도우 어텐션이라는 두 가지 주요 모듈을 통해 구현됩니다.  역 특징 피라미드는 이미지 피라미드의 고주파수 정보를 활용하여 ViT 기반 특징 업샘플링 프로세스를 통해 구성되며, 계층적 윈도우 어텐션은 다중 수준 특징 맵을 압축하기 위해 다양한 스케일의 윈도우 내 주요 샘플링 특징에 집중합니다.  **실험 결과**, LLaVA-UHD v2는 기존 MLLM보다 우수한 성능을 보이며, 여러 벤치마크에서 평균 3.7%의 성능 향상을 가져왔습니다. 특히 DocVQA에서는 9.3%의 향상을 보였습니다.  **본 연구의 핵심은 다양한 시각적 세분성을 포착하여 언어 생성과의 정렬을 개선하는 고해상도 특징 피라미드의 효과적인 통합**에 있습니다.  이를 통해, MLLM의 시각적 이해 능력을 크게 향상시킬 수 있음을 보여줍니다.

#### Future MLLM
미래의 다중 모드 대규모 언어 모델(MLLM)은 **더욱 정교한 시각적 이해 능력**을 갖추게 될 것입니다.  이는 고해상도 이미지 처리 및 다양한 시각적 세부 정보 포착을 위한 향상된 아키텍처를 통해 가능해질 것입니다. 또한, **더욱 효율적인 계산 과정**을 위해, 고해상도 특징 피라미드를 압축하는 새로운 방법이 개발될 것입니다.  **다양한 시각적 과제 수행**을 위한 시각적 다양성과, 고차원적 의미 이해를 위한 상호 작용적 학습 전략 또한 중요한 발전 방향입니다. **지식 기반의 시각적 질의응답 시스템**이 보다 강력해지면서, 폭넓은 영역을 포괄하는 정보 처리 역량을 갖춘 MLLM이 등장할 것입니다.  **학문적 데이터 뿐 아니라 대규모 실세계 데이터를 활용한 훈련**을 통해  실제 세계 문제 해결 능력이 향상될 것입니다.  **모델의 투명성과 설명 가능성** 또한 미래 MLLM 개발의 중요한 과제가 될 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.13871/x2.png)

> 🔼 제안된 LLaVA-UHD v2의 전체 아키텍처는 ViT(Vision Transformer), 계층적 윈도우 트랜스포머(Hiwin 트랜스포머), 그리고 LLM(Large Language Model)의 세 가지 주요 모듈로 구성됩니다. Hiwin 트랜스포머는 이미지를 여러 조각으로 나누고 개별 조각과 전체 이미지를 처리하여 다양한 수준의 표현을 포착하고 이를 공간적으로 일관된 토큰으로 압축하여 보다 효과적인 비전-언어 정렬을 가능하게 합니다.  이 과정을 통해 다양한 시각적 세부 정보를 포착하고 언어 생성에 필요한 다양한 의미적 세분성을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: The overall architecture of proposed LLaVA-UHD v2, consisting of a ViT, our hierarchical window transformer (Hiwin transformer), and an LLM. Hiwin transformers process sliced patches and the overview image by capturing inner multi-level representations and compressing them into spatially consistent tokens for a better vision-language alignment.
> </details>



![](https://arxiv.org/html/2412.13871/x3.png)

> 🔼 이 그림은 이미지 피라미드를 활용하여 고해상도 특징 맵을 생성하는 Joint Bilateral Upsampling (JBU) 모듈의 흐름도를 보여줍니다. JBU 모듈은 이미지 피라미드의 고주파수 정보를 활용하여 저해상도 특징 맵을 고해상도로 업샘플링하고, 이를 통해 고주파수 정보가 풍부한 고해상도 특징 맵을 생성합니다. 이 과정은 이미지 피라미드의 여러 레벨에서 고주파수 정보를 통합하여 수행되며, 최종적으로는 다양한 시각적 세부 정보를 포착하는 고해상도 특징 맵이 생성됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Flowchart of the Joint Bilateral Upsampling (JBU) module, which leverages the image pyramid to guide feature up-sampling, integrating high-frequency information into the up-sampled feature maps.
> </details>



![](https://arxiv.org/html/2412.13871/x4.png)

> 🔼 그림 4는 계층적 윈도우 어텐션의 흐름도를 보여줍니다. 피처 피라미드의 여러 레벨에서 나온 피처 맵들은 적응적으로 RoI-정렬되어 샘플링 피처가 되고, 그다음 길이 축을 따라 연결되어 학습 가능한 쿼리의 키 역할을 합니다.  즉, 다양한 해상도의 시각적 정보를 효율적으로 통합하고 압축하여 언어 모델이 이미지를 이해하는 데 도움을 주는 메커니즘을 보여줍니다. 각 레벨의 피처 맵은 지역적 맥락을 포착하는 여러 개의 윈도우로 나뉘며, 각 윈도우 내의 주요 피처들이 쿼리에 의해 선택되어 어텐션 연산에 사용됩니다. 이를 통해 다양한 시각적 세부 정보와 고차원적 의미를 효과적으로 결합하여 언어 생성에 활용할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: The flowchart of hierarchical window attention. Feature maps from different levels of the feature pyramid are adaptively RoI-aligned into sampling features and then concatenated along the length axis to serve as the key for the learnable queries.
> </details>



![](https://arxiv.org/html/2412.13871/x6.png)

> 🔼 그림 5는 JBU 모듈과 일반적인 이중 선형 보간법을 사용하여 수행한 다양한 시각적 작업에 대한 성능을 보여줍니다. 세 가지 시각적 작업은 광학 문자 인식(OCR), 선형 프로빙 의미론적 분할(Seg), 그리고 SUB-200 데이터셋을 사용한 세분화된 분류(Cls)입니다. JBU 모듈을 사용했을 때 세 가지 작업 모두에서 더 나은 성능을 보여줍니다. 이는 JBU 모듈이 이미지 피라미드에서 고주파수 패턴을 캡처하여 특징 업샘플링을 안내함으로써 고해상도 특징을 효과적으로 통합하기 때문입니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Performance on different visual tasks with JBU module and vanilla bilinear interpolation. “OCR” denotes the optical character recognition, “Seg” the Linear probing semantic segmentation, and “Cls” the fine-grained classification on SUB-200.
> </details>



![](https://arxiv.org/html/2412.13871/x7.png)

> 🔼 그림 6은 고해상도 복합 지각 과제에서 제안된 LLaVA-UHD v2와 LLaVA-Next, Mini-Gemini, GPT-4V를 포함한 고급 MLLM을 정성적으로 비교한 것입니다. 이러한 과제는 세밀한 시각 정보와 고차원 의미 맥락을 통합해야 합니다. 그림은 다양한 시각적 세부 정보와 의미 맥락을 필요로 하는 복잡한 시각적 질문에 대한 각 모델의 응답을 보여줍니다.  LLaVA-UHD v2는 세밀한 시각 정보와 고차원 의미 맥락을 효과적으로 통합하여 더욱 정확하고 포괄적인 응답을 생성하는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6:  Qualitative comparison of proposed LLaVA-UHD v2 and advanced MLLMs, including LLaVA-Next, Mini-Gemini, and GPT-4V on high-resolution complex perception tasks, which require the integration of both fine-grained visual information and high-level semantic contexts.
> </details>



![](https://arxiv.org/html/2412.13871/x8.png)

> 🔼 그림 7은 다양한 시각적 특징 수준에 대한 특정 텍스트 토큰의 활성화 응답을 보여줍니다. 빨간색 원은 서로 다른 수준 간의 명확한 차이점을 강조 표시합니다. 이 그림은 다양한 시각적 세부 수준을 포착하는 역 피라미드의 효과를 보여주는 것으로, 고해상도 특징이 세부적인 시각적 정보를 더 잘 캡처하는 반면, 저해상도 특징은 더 추상적인 시각적 개념을 캡처합니다. 이는 다양한 세부 수준에서 시각적 정보를 통합하는 모델의 능력을 보여주는 중요한 시각적 증거입니다.  최상의 이해를 위해서는 컬러로 확대하여 보는 것이 좋습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Activation response of specific textual tokens to different visual feature levels. Red circles highlight the obvious difference between levels. (Best viewed in color and zoomed-in)
> </details>



![](https://arxiv.org/html/2412.13871/x9.png)

> 🔼 그림 8은 고해상도의 이미지에서 미세한 부분까지 정확하게 인식해야 하는 과제를 보여줍니다.  LLaVA-UHD v2는 TV 프로그램 시작 시간, 공연 날짜, 운동 시간, 상품 가격 등을 정확하게 식별하여, 고해상도 이미지에서 복잡하게 밀집된 유사한 객체들 사이에서도 목표 객체의 경계를 정확하게 찾고 목표 객체를 정확하게 식별하는 능력을 보여줍니다. 반면 다른 모델들은 목표를 정확하게 찾지 못하거나(LLaVA-Next),  유사한 객체들과 구분하지 못하는(Mini-Gemini) 등의 한계를 보입니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Qualitative comparison on high-resolution dense perception task which requires the capabilities of fine-grained details perception.
> </details>



![](https://arxiv.org/html/2412.13871/x10.png)

> 🔼 그림 9는 고해상도의 미세한 질감 인식 능력이 필요한 고해상도 미세립자 인식 과제에 대한 정성적 비교를 보여줍니다.  이 그림에서는 다양한 최첨단 다중 모달 대규모 언어 모델(MLLM)이 고해상도 이미지에서 미세한 시각적 세부 사항을 정확하게 식별하고 해석하는 능력을 보여줍니다.  각 모델은 세부 정보가 많고 복잡한 시각적 장면을 다루는 데 있어 강점과 약점을 보여주는 몇 가지 예시를 통해 비교됩니다. 특히, LLaVA-UHD v2 모델은 작은 물체나 흐릿한 텍스트와 같이 미세한 시각적 세부 사항을 식별하는 능력을 강조하여, 다른 모델보다 우수한 성능을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Qualitative comparison on high-resolution fine-grained perception task which requires robust fine-grained visual texture perception capabilities.
> </details>



![](https://arxiv.org/html/2412.13871/x11.png)

> 🔼 그림 10은 고해상도 공간적 지각에 대한 정성적 비교를 보여줍니다. 이는 고차원 공간적 맥락을 파악하는 능력이 필요한 작업입니다. 그림은 다양한 고해상도 시각적 인식 작업에서 LLaVA-UHD v2, LLaVA-Next, Mini-Gemini, GPT-4V의 성능을 보여주는 여러 사례를 제시합니다. 각 사례는 고해상도 이미지에서 세부적인 시각적 정보와 고차원 의미적 맥락을 통합하여 정확하게 객체를 식별하고 상호 관계를 파악해야 하는 복잡한 작업입니다. LLaVA-UHD v2는 고해상도 공간적 지각 능력을 갖추고 있어 세부적인 시각적 정보와 고차원 의미적 맥락을 정확하게 통합하여 작업을 수행하는 것을 보여줍니다. 반면에 다른 모델들은 고해상도 공간적 지각 능력이 부족하여 일부 작업에서 어려움을 겪는 것으로 나타났습니다. 이는 LLaVA-UHD v2가 고해상도 공간적 인식에 대한 뛰어난 성능을 가짐을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Qualitative comparison on high-resolution spatial perception which necessitates the capabilities of high-level spatial contexts.
> </details>



![](https://arxiv.org/html/2412.13871/x12.png)

> 🔼 그림 11은 자연 장면에 대해 JBU 모듈에 의해 업샘플링된 특징들의 PCA 시각화를 보여줍니다. 계층적 감독을 사용하면 고해상도 특징(8배)이 객체 경계와 텍스트 모양을 명확하게 묘사할 수 있습니다. 색상으로 보면 더욱 효과적입니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: PCA visualization of the up-sampled features by JBU module on nature scene. With hierarchical supervision, the high-resolution features (8×8\times8 ×) could clearly depict object boundary and text appearance. (Best viewed in color and zoomed in)
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | Average | VQA<sup><i>D</i></sup> | Bench<sup><i>OCR</i></sup> | VQA<sup><i>C</i></sup> | VQA<sup><i>T</i></sup> | AI2D | SQA | MMMU<sup><i>v</i></sup> | GQA | SEED<sup><i>I</i></sup> | MMB | MME<sup><i>P</i></sup> | RWQA | REC | Bench<sup><i>HR</i></sup> |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| LLaVA-UHD [31] | 58.0 | 56.7 | 40.9 | 56.3 | 62.2 | 55.4 | 70.7 | 37.0 | 63.8 | 65.6 | 64.8 | 70.0 | 54.4 | 68.3 | 45.6 |
| + JBU module | 60.0 | 60.2 | 50.4 | 60.4 | 67.1 | 57.8 | 70.5 | 38.2 | 64.0 | 66.7 | 65.6 | 71.2 | 51.9 | 72.3 | 43.9 |
| + HFP integration | 61.5 | 65.0 | 51.3 | 62.5 | 68.5 | 58.1 | 69.2 | 38.9 | 64.6 | 67.4 | 65.5 | 73.0 | 55.5 | 73.3 | 48.9 |
| + Token organization | 61.7 | 66.0 | 50.1 | 62.8 | 66.8 | 59.4 | 69.8 | 37.6 | 64.0 | 67.4 | 66.1 | 73.6 | 56.9 | 74.0 | 49.0 |
| Δ | +3.7 | +9.3 | +9.2 | +6.5 | +4.6 | +4.0 | -0.9 | +0.6 | +0.2 | +1.8 | +1.3 | +3.6 | +2.5 | +5.7 | +3.4 |{{< /table-caption >}}
> 🔼 표 2는 제안된 방법에서 각 모듈의 효과를 분석한 결과를 보여줍니다.  'HFP'는 고해상도 특징 피라미드의 약자이며,  'Δ'는 기준 방법 대비 전반적인 성능 향상을 나타냅니다. REC는 RefCOCO/g/+ 데이터셋에 대한 평균 정확도를 의미합니다.  이 표는 고해상도 특징 피라미드(HFP)를 구성하고 통합하는 과정에서 각 모듈(JBU, HFP 통합, 토큰 구성)이 성능 향상에 미치는 영향을 정량적으로 분석하여, 제안된 방법의 효과를 보여줍니다.  각 모듈이 추가됨에 따라 성능이 향상되는 것을 확인할 수 있으며, 특히 DocVQA 데이터셋에서 9.3%의 향상을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Ablation studies of modules in our proposed method. “HFP” is the abbreviation of high-resolution feature pyramid. “ΔΔ\Deltaroman_Δ” denotes the overall improvement compared to the baseline. REC reports the average accuracy of RefCOCO/g/+.
> </details>

{{< table-caption >}}
| Method | Average | MME<sup>P</sup> | GQA | AI2D | VQA<sup>C</sup> | VQA<sup>T</sup> | VQA<sup>D</sup> | Bench<sup>HR</sup> |
|---|---|---|---|---|---|---|---|---|
| LLaVA-UHD | 58.6 | 70.0 | 63.8 | 55.4 | 56.3 | 62.2 | 56.7 | 45.6 |
| *w. ConvNext* | 59.7 | 68.2 | 62.7 | 55.6 | 61.8 | 63.5 | 61.8 | 44.0 |
| *w. DeConv.* | 61.7 | 71.2 | 64.2 | 57.4 | 61.8 | 67.8 | 63.4 | 46.3 |
| *w. Bilinear* | 62.0 | 72.0 | 64.5 | 57.8 | 62.2 | 67.6 | 63.7 | 46.5 |
| *w. JBU module* | 63.0 | 73.0 | 64.6 | 58.3 | 62.5 | 68.5 | 65.0 | 48.9 |{{< /table-caption >}}
> 🔼 표 3은 다양한 특징 피라미드 구성 방법의 비교 결과를 보여줍니다.  CLIP-ViT 대신 CLIP-ConvNext [68]를 비주얼 인코더로 사용하고 여러 단계의 특징 맵을 최종 계층적 특징 피라미드로 직접 사용한 경우를  'ConvNext' 라고 표시했습니다. 이 표는 여러 가지 방법으로 생성된 특징 피라미드의 성능과 효율성을 비교 분석하여, 제안된 방법의 우수성을 보여주는 데 사용됩니다.  특히, 다양한 벤치마크에서의 성능과 계산 비용 측면에서의 비교가 이루어집니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Comparison of different methods for feature pyramid construction. “ConvNext” means we replace the CILP-ViT with CLIP-ConvNext [68] as visual encoder and directly use the feature maps from multiple stages as the final hierarchical feature pyramid.
> </details>

{{< table-caption >}}
| Method | Period(h) | Latency(s) | Memory(G) | Efficiency Average | General MME<sup>P</sup> | GQA | AI2D | VQA<sup>C</sup> | VQA<sup>T</sup> | VQA<sup>D</sup> |
|---|---|---|---|---|---|---|---|---|---|---|
| _Pyramid_ | 62.4 | 1.26 | 60.3 | 62.4 | 69.0 | 60.8 | 57.3 | 60.7 | 67.5 | 58.9 |
| _Fix [3×3]_ | 26.9 | 0.62 | 41.7 | 64.6 | 73.8 | 63.9 | 58.8 | 60.9 | 66.2 | 63.8 |
| _Selective_ | 27.7 | 0.54 | 39.4 | 65.3 | 73.0 | 64.6 | 58.3 | 62.5 | 68.5 | 65.0 |{{< /table-caption >}}
> 🔼 표 4는 다양한 그리드 크기 선택에 따른 성능과 효율성을 비교 분석한 표입니다.  'Pyramid' 방식은 여러 레벨의 특징 맵을 지역 수준의 특징 피라미드로 구성하는 방식을 의미하며, 예를 들어 레벨 0은 2x3, 레벨 1은 4x6, 레벨 2는 8x12 크기의 그리드를 사용합니다.  'Fix' 방식은 모든 특징 맵을 3x3 그리드로 통합하는 방식입니다.  본 표에서는 8개의 A100 GPU를 사용하여 학습 시간을 측정하고, A100 GPU 1개를 사용하여 1008x672 이미지에 대한 지연 시간을 측정하며, 8개의 A100 GPU를 사용하고 GPU당 1개의 이미지로 GPU 메모리를 측정했습니다.  모두 지도 학습 미세 조정 단계에서 측정된 결과입니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Comparison of different choice of grid sizes on performance and efficiency. “Pyramid” means the feature grids from different levels form a region-level feature pyramid, e.g.formulae-sequence𝑒𝑔e.g.italic_e . italic_g ., [2×\times×3] for level-0, [4×\times×6] for level-1, [8×\times×12] for leval-2. “Fix” represents all feature maps are pooled into a 3×\times×3 feature grid. We measure the training period on 8×\times×A100s, the latency on an A100 with a 1008×\times×672 image, and the GPU memory on 8×\times×A100s with 1 image per GPU in supervised fine-tune phase.
> </details>

{{< table-caption >}}
| Data | Size | Response formatting prompts |
|---|---|---|
| LLaVA [63] | 158K | – |
| ShareGPT [90] | 40K | – |
| VQAv2 [29] | 83K | Answer the question using a single word or phrase. |
| GQA [38] | 72K |  |
| OKVQA [75] | 9K |  |
| OCRVQA [82] | 80K |  |
| DocVQA [95] | 15K |  |
| ChartQA [76] | 20K |  |
| A-OKVQA [88] | 66K | Answer directly with the option’s letter from the given choices. |
| DVQA [41] | 20K | – |
| TextCaps [92] | 22K | Provide a one-sentence caption for the provided image. |
| ShareGPT4V [18] | 55K | – |
| AI2D [43] | 3K | – |
| LAION-GPT4V [3] | 11K | – |
| SythDog-EN [46] | 40K | – |
| LRV-Instruct [61] | 30K | – |
| RefCOCO [42, 74] | 48K | Provide a short description for this region. _ (for Region Caption)_ |
| VG [48] | 86K | Provide the bounding box coordinate of the region this sentence describes. _ (for Referring Expression Comprehension)_ |
| Total | 858K |  |{{< /table-caption >}}
> 🔼 표 5는 논문에서 사용된 858,000개의 이미지-텍스트 데이터셋의 상세 구성을 보여줍니다.  데이터셋은 다양한 비전-언어 작업(VQA, OCR, 이미지 캡션 생성 등)을 위한 여러 개의 기존 데이터셋들을 하나로 합쳐 만든 혼합 데이터셋입니다. 각 데이터셋의 크기와 함께 해당 데이터셋에서 사용되는 응답 형식(예: 한 단어 또는 구절로 답하기, 객관식 답변, 영역 설명 제공 등)이 명시되어 있습니다. 이 표는 논문에서 제시된 모델의 성능을 평가하는 데 사용된 데이터의 종류와 특징을 자세히 보여줌으로써, 실험 결과의 신뢰성과 일반화 가능성을 높이는 데 기여합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Detailed composition of our 858k-mixed dataset.
> </details>

{{< table-caption >}}
| Level | Period(h) | Memory(G) | Average | GQA | SQA | REC | VQA<sup>C</sup> | VQA<sup>T</sup> | ESTVQA | MME<sup>P</sup> |
|---|---|---|---|---|---|---|---|---|---|---|
| _0,2_ | 27.7 | 41.9 | 63.4 | 63.9 | 69.5 | 71.5 | 60.5 | 66.5 | 40.6 | 71.0 |
| _0,1,2_ | 28.0 | 41.9 | 63.7 | 63.8 | 70.2 | 71.8 | 60.5 | 66.9 | 40.8 | 72.1 |
| _0,1,2,3_ | 45.6 | 53.0 | 63.8 | 64.4 | 69.3 | 72.6 | 60.7 | 66.4 | 41.6 | 71.4 |
| _0,1,2,3_ (w/o HS.) | 45.6 | 52.6 | 62.4 | 63.6 | 69.8 | 67.1 | 57.8 | 66.5 | 39.9 | 72.0 |{{< /table-caption >}}
> 🔼 표 6은 다양한 수준의 특징(feature level)을 사용했을 때 성능과 효율성을 비교 분석한 결과를 보여줍니다.  'HS'는 계층적 감독(hierarchical supervision)을 의미하며, ESTVQA [101]는 장면 텍스트 인식(scene text recognition)에 초점을 맞춘 VQA 벤치마크입니다. 표에는 각 특징 수준별로 학습 시간, 메모리 사용량, 그리고 GQA, SQA, REC, VQAC, VQAT, ESTVQA, MMEP 등 다양한 벤치마크에서의 성능이 나타나 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Comparison of different choices of feature level on performance and efficiency. “HS.”: hierarchical supervision. ESTVQA [101] is a VQA benchmark focusing on scene text recognition.
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