---
title: "2.5 Years in Class: A Multimodal Textbook for Vision-Language Pretraining"
summary: "2.5년 분량의 교육 비디오를 활용, 고품질 다중 모달 텍스트북 코퍼스 구축 및 VLMs 사전 학습 성능 향상"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Vision-Language Models", "🏢 College of Computer Science and Technology, Zhejiang University",]
showSummary: true
date: 2025-01-01
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.00958 {{< /keyword >}}
{{< keyword icon="writer" >}} Wenqi Zhang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-03 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.00958" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.00958" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 Vision-Language Model (VLM) 사전 학습은 웹페이지에서 크롤링한 이미지-텍스트 쌍 데이터에 의존해왔습니다. 하지만 이러한 데이터는 **낮은 지식 밀도, 이미지와 텍스트 간의 느슨한 연관성, 이미지 시퀀스의 논리적 일관성 부족** 등의 문제점을 가지고 있습니다.  본 논문은 이러한 문제를 해결하기 위해 2.5년 분량의 교육 비디오 데이터를 활용하여 새로운 다중 모달 텍스트북 코퍼스를 제시합니다. 이 데이터셋은 **더욱 풍부하고 일관된 지식을 제공하며, 이미지와 텍스트 간의 정합성을 높였습니다.**

본 연구에서는 LLM 기반의 체계적인 비디오 수집 및 필터링 파이프라인을 구축하여 고품질의 교육 비디오 데이터를 확보했습니다.  **ASR 및 OCR 기술을 통해 비디오에서 시각적, 청각적, 텍스트 정보를 추출하고, 이를 시간적 순서에 따라 이미지-텍스트가 혼합된 형태로 구성**했습니다.  실험 결과, 제시된 텍스트북 코퍼스를 사용하여 사전 학습된 VLMs는 지식 및 추론 집약적인 과제에서 우수한 성능을 보였습니다.  **특히 few-shot 학습 환경에서 뛰어난 성능**을 보였으며, 이는 텍스트북 코퍼스의 일관된 컨텍스트 인식 능력을 보여줍니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 2.5년치 교육 비디오(22,000시간)를 활용하여 고품질 다중모달 텍스트북 코퍼스를 구축 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 기존 웹페이지 기반 데이터셋의 한계(낮은 지식 밀도, 느슨한 이미지-텍스트 관계, 논리적 일관성 부족) 극복 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 지식 및 추론 집약적인 과제에서 VLMs의 사전 학습 성능이 크게 향상됨을 실험적으로 입증 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**본 논문은 비디오 기반의 고품질 다중 모드 텍스트북을 제시함으로써, 기존의 웹페이지 기반 데이터셋의 한계를 극복하고 VLMs의 성능을 크게 향상시키는 데 기여합니다.**  특히 지식 및 추론 집약적인 작업에서의 성능 향상은 주목할 만하며, 향후 다중 모드 사전 학습 연구에 중요한 영향을 미칠 것입니다.  **웹 크롤링 데이터의 품질 저하 문제를 해결하고, 보다 풍부하고 일관된 지식을 제공하는 새로운 데이터셋의 개발은 앞으로의 연구 방향을 제시**합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.00958/x1.png)

> 🔼 그림 1은 기존의 MMC4와 OBELICS와 같은 이미지-텍스트 교차 데이터셋의 한계점을 보여줍니다. 이러한 데이터셋들은 이미지와 텍스트 간의 관련성이 약하고, 지식 밀도가 낮으며, 이미지 시퀀스의 일관성이 부족하다는 문제점을 가지고 있습니다. 반면, 본 논문에서 제시하는 다중 모달 텍스트북은 방대한 교육용 비디오를 활용하여 이미지와 텍스트 간의 밀접한 연관성과 논리적 일관성을 확보한 고품질의 데이터셋을 구축합니다.  비디오의 주요 장면(키프레임)과 ASR(자동 음성 인식) 및 OCR(광학 문자 인식)을 통해 추출한 텍스트를 교차적으로 배치하여, VLMs(비전-언어 모델)이 풍부한 지식을 효율적으로 학습할 수 있도록 지원합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Previous interleaved datasets, e.g., MMC4 and OBELICS, suffer from limitations like weak text-image relations, low knowledge density, and incoherent image sequences. Our multimodal textbook, sourced from massive tutorial videos, employs coarse-to-fine knowledge extraction and multi-level filtering to create a high-quality, textbook-level dataset. It interleaves video keyframes with tutorial texts (extracted from ASR and OCR), enabling VLMs to acquire rich knowledge through tightly coupled text-image and more coherent logic.
> </details>





{{< table-caption >}}
| Dataset | #Image |  |  | #Text Token |  |  | *L*=4 | *L*=5 | *L*=6 | *L*=7 | *L*=8 | Avg. | Source |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Min. | Max. | Avg. | Min. | Max. | Avg. |  |  |  |  |  |  |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| *Image-text Paired Dataset* |  |  |  |  |  |  |  |  |  |  |  |  |  |
| COYO-700M | 1 | 1 | 1 | 1 | 811 | 16 | - | - | - | - | - | - | Common Crawl |
| LAION-5B | 1 | 1 | 1 | 6 | 683 | 27 | - | - | - | - | - | - | Common Crawl |
| *Image-text Interleaved Dataset* |  |  |  |  |  |  |  |  |  |  |  |  |  |
| MMC4 | 0 | 117 | 5.7 | 4 | 16715 | 417 | 0.363 | 0.348 | 0.310 | 0.298 | 0.276 | 0.319 | Common Crawl |
| MMC4-core-ff | 0 | 15 | 4.1 | 15 | 16715 | 329 | 0.431 | 0.406 | 0.404 | 0.403 | 0.396 | 0.407 | Common Crawl |
| OBELICS | 1 | 30 | 2.5 | 12 | 10717 | 816 | 0.366 | 0.351 | 0.339 | 0.337 | 0.336 | 0.345 | Common Crawl |
| OmniCorpus* | 1 | 16 | 3.9 | 14 | 6893 | 574 | 0.358 | 0.329 | 0.310 | 0.305 | 0.301 | 0.321 | Multi-sources |
| **Ours** | **2** | **45** | **10.7** | **11** | **34174** | **1297** | **0.687** | **0.697** | **0.698** | **0.688** | **0.662** | **0.686** | Video Website |{{< /table-caption >}}

> 🔼 표 1은 제시된 논문에서 다루는 다중 모드 교과서 데이터셋을 기존의 이미지-텍스트 쌍 데이터셋 및 웹 페이지 중심의 혼합 데이터셋과 비교 분석한 표입니다. 이미지와 텍스트의 분포 측면에서 비교 분석하며, 특히 혼합 샘플 내 여러 이미지 간의 의미 및 구조적 상관관계를 측정하는 지표인 In-sample Image SIML(SIML은 이미지 수를 나타내는 상수)을 사용하여 데이터셋의 특징을 보다 자세하게 비교 분석합니다. OmniCorpus 데이터셋의 경우 데이터셋 크기가 매우 크기 때문에 무작위로 샘플링된 하위 집합에 대한 통계 분석 결과를 제시합니다. 요약하자면, 본 표는 다양한 다중 모드 데이터셋들의 이미지-텍스트 분포 및 이미지 간의 상관관계를 정량적으로 비교 분석하여 제안된 다중 모드 교과서 데이터셋의 특징과 우수성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: We compare our multimodal textbook with image-text paired datasets and webpage-centric interleaved datasets in terms of image and text distributions. In-sample Image SIMLsuperscriptSIM𝐿\text{SIM}^{L}SIM start_POSTSUPERSCRIPT italic_L end_POSTSUPERSCRIPT measures the semantic and structural correlation between multiple images within an interleaved sample. OmniCorpus∗superscriptOmniCorpus\text{OmniCorpus}^{*}OmniCorpus start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT: Due to the extensive size of the dataset, we perform statistical analysis on a randomly sampled subset.
> </details>





### In-depth insights


#### Multimodal Textbook
본 논문에서 제시된 "다중 모드 교과서"는 **비디오 중심의 고품질 다중 모드 데이터셋**으로, 기존 웹 페이지 기반 데이터셋의 한계를 극복하기 위해 **2.5년 분량의 교육용 비디오**를 활용하여 구성되었습니다. 단순히 이미지-텍스트 쌍으로 이루어진 기존 데이터셋과 달리, **비디오의 시간적 흐름에 따라 이미지와 텍스트가 긴밀하게 연결**되어 있어, 보다 자연스럽고 논리적인 세계 이해를 가능하게 합니다. 특히, **LLM 기반의 지식 분류 체계**를 통해 체계적으로 비디오를 수집하고, **다단계 필터링 및 추출 과정**을 거쳐 높은 품질의 키프레임, ASR, OCR 데이터를 확보한 점이 특징입니다. 이러한 고품질 데이터셋은 **지식 및 추론 집약적인 과제**에서 뛰어난 성능을 보이며, **문맥 인식 능력** 향상에도 기여합니다.  **비디오-텍스트 간의 일관성과 논리적 연결성**이 강화된 다중 모드 교과서는 VLMs의 학습 효율과 성능을 크게 향상시키는 핵심 요소임을 보여줍니다.

#### Video-centric VLM
비디오 중심 VLM은 기존의 이미지-텍스트 쌍 데이터셋의 한계를 극복하기 위해 등장한 새로운 접근 방식입니다. **단순한 이미지-텍스트 쌍을 넘어 비디오의 시공간적 정보를 활용**, 이미지와 텍스트 간의 연관성을 더욱 풍부하고 자연스럽게 학습할 수 있도록 합니다.  **비디오 데이터의 시퀀스 특징**을 활용하여, 이미지 간의 논리적 연관성을 강화하고, 맥락 정보를 보다 효과적으로 학습하는 데에 초점을 맞춥니다.  **장점**으로는 더욱 향상된 시각적 추론 능력, 보다 정확한 맥락 이해, 그리고 복잡한 시각적 정보 처리 능력 향상을 들 수 있습니다.  하지만 **단점**으로는  비디오 데이터의 수집 및 전처리 과정의 어려움, 그리고 대량의 연산 자원 필요성 등이 존재합니다. 앞으로 **연구 방향**으로는  비디오 데이터의 효율적인 처리 기술 개발,  비디오 중심 VLM의 다양한 응용 분야 발굴, 그리고 다양한 종류의 비디오 데이터를 활용한 모델 학습 방법 연구가 중요할 것으로 예상됩니다.

#### LLM-powered Pipeline
LLM 기반 파이프라인은 논문에서 다루는 핵심적인 방법론으로 보이며, **자동화된 지식 탐색 및 데이터 처리**를 가능하게 합니다.  **대규모 언어 모델(LLM)**을 활용하여 교육 비디오를 체계적으로 수집하고 필터링하는 과정을 자동화함으로써, 기존의 수동적인 방식으로는 불가능했던 대량의 고품질 데이터 확보를 가능하게 합니다. 이는 **효율성 극대화**와 **주관성 배제**를 통해 연구의 신뢰성을 높이는 데 기여할 것입니다.  LLM이 생성한 지식 분류 체계는 **비디오 선별의 정확성**을 높이고, **중복 제거 및 품질 관리**를 위한 기준을 제시합니다.  또한, **다층적 필터링 과정**을 통해 비디오 내 불필요한 부분을 제거하고 핵심 내용만 추출하여 효율성을 높입니다.  결과적으로, LLM 기반 파이프라인은 **대규모 고품질의 다중 모달 데이터셋 구축**이라는 어려운 과제를 해결하는 데 중요한 역할을 수행하며, **효과적인 VLMs 사전 학습**에 필수적인 요소로 작용할 것으로 예상됩니다.  **특히, 비디오 데이터 특성상 존재하는 노이즈나 불필요한 정보들을 효과적으로 제거하여 데이터 품질을 높이는 데 기여**할 것으로 보입니다.

#### Interleaved Context
논문에서 'Interleaved Context' 개념은 **이미지와 텍스트가 번갈아 나타나는 다중 모드 데이터셋**에서 중요한 역할을 합니다. 단순히 이미지와 텍스트를 짝지어 학습하는 것보다 **자연스러운 맥락**을 이해하는 데 효과적입니다.  **웹 페이지나 문서에서 수집된 기존의 Interleaved 데이터셋은 이미지와 텍스트 간의 관련성이 약하거나 논리적 일관성이 부족**한 문제점을 가지고 있습니다.  하지만, **본 논문에서 제시하는 고품질의 다중 모달 교과서 데이터셋**은 **일관성 있는 이미지 시퀀스와 풍부한 지식**을 제공하여 이러한 문제점을 해결합니다.  **영상 기반의 교과서 데이터셋**은 **일관된 맥락**을 제공하고 **이미지와 텍스트의 정렬**이 더욱 잘 이루어져 **VLMs(Vision-Language Models)의 성능 향상**에 크게 기여합니다.  특히 **지식과 추론이 필요한 과제**에서 뛰어난 성능을 보이는데, 이는 **Interleaved Context에 대한 VLMs의 이해도가 높아졌음**을 시사합니다.

#### Future Directions
본 논문에서 제시된 멀티모달 텍스트북을 바탕으로 미래 연구 방향을 생각해 볼 수 있습니다. **첫째, 텍스트북의 규모를 더욱 확장**하여 더욱 다양한 과목과 더욱 많은 학습 자료를 포함시킬 수 있습니다. **둘째, 현재 영어로만 제공되는 텍스트북을 다국어로 지원**하여 전 세계 학습자들에게 더욱 폭넓게 활용될 수 있도록 하는 것입니다.  **셋째, 다양한 학습 유형을 지원**하는 것이 중요합니다. 예를 들어, 시각적 학습, 청각적 학습, 운동 학습 등 다양한 유형의 학습자에게 맞춘 학습 콘텐츠를 개발하는 것입니다. **넷째, VLMs의 성능 향상을 위한 지속적인 연구**가 필요합니다. 본 논문에서 제시된 멀티모달 텍스트북은 VLMs의 사전 학습에 사용될 수 있지만, VLMs 자체의 성능 향상을 위한 지속적인 연구가 필요합니다.  **마지막으로, 윤리적 고려 사항**을 염두에 두어야 합니다.  인공지능 기술 발전에 따라 학습 자료의 편향성이나 저작권 문제와 같은 윤리적 문제에 대한 고려가 필수적입니다. 이러한 미래 연구 방향들을 통해 본 논문에서 제시된 멀티모달 텍스트북은 더욱 발전하고 다양한 분야에서 활용될 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.00958/x2.png)

> 🔼 그림 2는 교육용 비디오로부터 다중 모드 교과서를 구성하는 과정을 보여줍니다.  먼저, 대규모 언어 모델(LLM)을 사용하여 지식 분류 체계를 구축하고, 메타데이터 수준에서 비디오를 검색하고 필터링하여 15만 개의 교육용 비디오를 수집합니다. 그런 다음, 다중 수준의 지식 추출을 위해 비디오-교과서 파이프라인을 설계합니다. ① ASR(자동 음성 인식) 전사를 사용하여 비교육적인 비디오를 걸러내고 7만 5천 개의 고품질 비디오를 유지합니다. ② ASR의 타임스탬프를 사용하여 긴 비디오를 짧은 클립으로 분할하고, 시각 및 ASR이 일치하지 않는 클립은 제거합니다. ③ 각 클립에서 주요 프레임을 감지하고 OCR(광학 문자 인식)을 사용하여 텍스트와 기호를 추출합니다. 이 파이프라인은 650만 개의 주요 프레임, 2억 5,900만 개의 ASR 토큰, 5억 개의 OCR 토큰을 생성하고 이를 이미지-텍스트가 섞인 교과서로 구성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: An illustration of constructing a multimodal textbook from instructional videos. We first instruct LLMs to construct a knowledge taxonomy, then retrieve and filter videos at metadata level, collecting 159K instructional videos. Then a video-to-textbook pipeline is designed for multi-level knowledge extraction. ① We filter out non-instructional videos using ASR transcripts, retaining 75K high-quality videos. ② We use ASR’s timestamp to segment long videos into short clips, discarding those with misaligned visuals and ASR. ③ We detect keyframes from each clip and extract text and symbols by OCR. Our pipeline produces 6.5M keyframes, 259M ASR, and 500M OCR tokens and organizes them into an image-text interleaved textbook.
> </details>



![](https://arxiv.org/html/2501.00958/extracted/6106116/sec/fig/fig3.png)

> 🔼 그림 3은 데이터셋에서 무작위로 샘플의 20%, 50%, 100%를 선택하고 각 샘플 내에서 이미지 순서를 섞은 결과를 보여줍니다.  이렇게 이미지 순서가 섞인 데이터셋들은 사전 훈련에도 사용되었습니다. 정확도는 7가지 벤치마크의 평균값을 나타냅니다. 이는 이미지 순서의 일관성이 모델 성능에 미치는 영향을 평가하기 위한 실험으로, 이미지 순서가 무작위로 섞일수록 모델 성능이 얼마나 저하되는지를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: We randomly select 20%, 50%, and 100% samples from datasets and shuffle the image order within each sample. These datasets with shuffled images are also used for pretraining. The Accuracy denotes the average of seven benchmarks.
> </details>



![](https://arxiv.org/html/2501.00958/x3.png)

> 🔼 그림 4는 논문에서 다루는 6개 과목(수학, 물리, 화학, 지구과학, 공학, 컴퓨터 과학)에 대한 하위 과목들을 시각적으로 보여줍니다. 상위 9개 과목과 그 비율만을 선택적으로 표시하여 공간 제약을 고려했습니다. 하단 그래프는 각 과목과 그 하위 과목에 속한 지식 포인트의 분포를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Top: We plot six subjects along with their corresponding sub-courses. Due to space constraints, we selectively visualized only the courses with the highest proportions. Bottom: We count the knowledge points distribution belongs to each subject and its course
> </details>



![](https://arxiv.org/html/2501.00958/x4.png)

> 🔼 이 그림은 논문의 4장, '다중 모드 교과서 분석' 섹션에 포함된 그림 5입니다. 그림은 지구과학 분야를 다룬 교과서의 한 페이지를 보여줍니다.  이 페이지는 물 순환 과정(수문 순환)을 설명하고 있으며, 증발, 응결, 강수, 지표수, 침투, 지하수 등의 개념을 그림과 함께 설명하고 있습니다.  그림에는 다양한 그림과 텍스트 설명이 포함되어 있어, 물 순환 과정의 각 단계를 시각적으로 이해하기 쉽도록 구성되어 있습니다. 특히, 그림에는 물 순환 과정을 이해하기 위한 상세한 설명과 함께, 각 단계를 설명하는 ASR (자동 음성 인식) 결과 텍스트가 포함되어 있습니다. 이를 통해 독자가 물 순환 과정을 보다 쉽고 정확하게 이해할 수 있도록 돕고 있습니다.  전체적으로, 이 그림은 논문에서 제시하는 다중 모달 교과서의 높은 질과 효과적인 학습 내용 전달 방식을 보여주는 좋은 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: A case presented in our textbook illustrates the water cycle within the domain of earth science.
> </details>



![](https://arxiv.org/html/2501.00958/x5.png)

> 🔼 이 그림은 물리학 분야를 다루는 교재의 한 장면을 보여줍니다. 그림에서는 물체의 초기 속도가 0m/s이고 5초 후에 10m/s의 속도에 도달하는 상황을 설명합니다. 이를 통해 가속도의 개념을 설명하고, 가속도의 단위와 계산 방법을 보여줍니다.  더불어, 회전 운동에서 관성의 개념을 설명하기 위해 얇은 고리와 고체 원반을 비교하는 예시도 제시하고 있습니다.  그림은 텍스트와 이미지가 병행되어 설명되며, 각 단계의 계산 과정을 시각적으로 보여주는 방식으로 구성되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: A case presented in our textbook introducing the principles of mechanics within the domain of physics.
> </details>



![](https://arxiv.org/html/2501.00958/x6.png)

> 🔼 그림 7은 물리학 분야에서 속도와 가속도의 개념을 소개하는 교재의 한 예시입니다. 그림에서는 질량이 다른 두 물체에 같은 힘을 가했을 때의 운동을 비교하여 관성의 개념을 설명합니다. 또한, 회전 운동에서 관성 모멘트의 차이를 비교하여 관성의 개념을 확장합니다. 그림에는 각 상황에 대한 자세한 설명과 수식이 함께 제공되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: A case presented in our textbook introducing the concepts of velocity and acceleration within the context of physics.
> </details>



![](https://arxiv.org/html/2501.00958/x7.png)

> 🔼 이 그림은 논문의 멀티모달 교과서에서 기하학 문제를 푸는 과정을 보여줍니다. 그림은 문제에 대한 설명과 함께 여러 단계의 풀이 과정을 보여주는 이미지와 텍스트를 보여줍니다. 각 단계는 이미지, 수식, 그리고 설명 텍스트를 결합하여 시각적이고 논리적인 이해를 돕습니다. 이는 멀티모달 학습을 위한 교과서의 특징을 잘 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: A case presented in our textbook demonstrates how to solve a question about planar geometry in the domain of mathematics.
> </details>



![](https://arxiv.org/html/2501.00958/x8.png)

> 🔼 이 그림은 화학 분야를 다루는 교재의 한 부분으로, 원자와 분자, 그리고 화합물의 개념을 설명하기 위해 제시된 사례입니다. 헬륨, 수소 기체, 물(H2O)의 세 가지 물질을 예로 들어 원자와 분자의 차이점을 보여줍니다. 헬륨은 원자로 구성되고, 수소 기체는 분자(두 개의 수소 원자가 결합)로 구성되며, 물 또한 두 개의 수소 원자와 한 개의 산소 원자가 결합된 분자로 구성됩니다.  그림을 통해 원소, 분자, 화합물의 개념을 시각적으로 이해하고, 서로 다른 유형의 원자들이 결합하여 분자를 형성할 수 있음을 보여줍니다.  또한, 원자와 분자의 개념을 더 명확히 하기 위해 추가적인 예시들이 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: A case presented in our textbook illustrates the concepts of molecules, atoms, and compounds in the domain of chemistry.
> </details>



![](https://arxiv.org/html/2501.00958/x9.png)

> 🔼 그림 10은 본 논문에서 소개하는 다중 모드 교과서의 한 예시로, 깊이 우선 탐색 알고리즘을 보여줍니다. 그림에서는 노드 0에서 시작하여 깊이 우선 탐색을 수행하는 과정을 단계별로 보여주는 애니메이션과 함께, 각 단계에서 방문하는 노드와 경로를 시각적으로 표현하고 있습니다. 또한, 깊이 우선 탐색 알고리즘의 의사 코드(pseudocode)도 함께 제시하여 알고리즘의 동작 방식을 보다 자세히 이해할 수 있도록 돕고 있습니다. 이를 통해 독자는 깊이 우선 탐색 알고리즘의 개념과 동작 과정을 보다 직관적으로 이해할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: A case presented in our textbook introduces a depth-first search algorithm.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| #Shot | 0 | 1 | 2 | 4 | 0 | 1 | 2 | 4 | 0 | 1 | 2 | 4 | 0 | 1 | 2 | 4 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| **Dataset** | ScienceQA<sup>IMG</sup> |  |  |  | OKVQA |  |  |  | TextVQA |  |  |  | TextVQA<sup>ocr</sup> |  |  |  |
| MMC4 | - | 1.6 | 3.9 | 11.6 | 8.6 | 23.6 | 21.5 | 28.7 | 12.1 | 16.2 | 16.8 | 20.9 | 14.5 | 23.9 | 29.9 | 34.7 |
| MMC4-Core-ff | - | 2.1 | 10.1 | 10.2 | 11.8 | 21.2 | 25.3 | 30.4 | 13.6 | 18.7 | 18.8 | 22.1 | 16.1 | 26.6 | 28.7 | 33.1 |
| OBELICS | - | 2.8 | 3.0 | 16.4 | 13.0 | 31.7 | 35.7 | 37.5 | 9.2 | 26.5 | 30.2 | 32.2 | 11 | 30.7 | 36.3 | 41 |
| **Textbook-6.5M** | 26.3 | 29.4 | 25.1 | 37.3 | 10.2 | 31.2 | 36.8 | 39.9 | 11.8 | 26.7 | 32.1 | 33.5 | 14.1 | 33.1 | 36.4 | 42.8 |
| **Dataset** | MathVista |  |  |  | MathVision |  |  |  | MathVerse |  |  |  | Avg. |  |  |  |
| MMC4 | 20.4 | 30 | 27.9 | 26 | 12.2 | 21.3 | 15.5 | 16.1 | 8.6 | 19.4 | 21.2 | 15.9 | 10.9 | 19.4 | 19.5 | 21.9 |
| MMC4-Core-ff | 22.5 | 33.0 | 29.2 | 27.8 | 13.7 | 23.4 | 16.3 | 17.7 | 8.6 | 19.9 | 21.8 | 15.2 | 12.3 | 20.7 | 21.4 | 22.3 |
| OBELICS | 21.6 | 28.5 | 31.1 | 27.6 | 13.4 | 20.1 | 16.8 | 14.9 | 6.9 | 19.4 | 20.7 | 14 | 10.7 | 22.8 | 24.8 | 26.2 |
| **Textbook-6.5M** | 24.3 | 43.4 | 33.2 | 29.2 | 14.5 | 25.6 | 18.2 | 18.1 | 7.7 | 28.5 | 19.8 | 14.6 | 15.5 | 31.1 | 28.8 | 30.8 |{{< /table-caption >}}
> 🔼 표 2는 다양한 삽입형 데이터셋을 사용하여 LLaVA-1.5-7B 기본 모델을 추가로 사전 훈련한 결과를 보여줍니다.  성능 평가는 4가지 일반적인 VQA 벤치마크와 3가지 수학 관련 벤치마크에서 몇 번의 시도만으로 수행되었습니다. 이 표는 각 데이터셋으로 사전 훈련된 모델의 성능을 0-shot, 1-shot, 2-shot, 4-shot 설정에서 비교하여, 다양한 삽입형 데이터셋을 사용한 사전 훈련이 모델 성능에 미치는 영향을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 2: We continued pre-training the base model of LLaVA-1.5-7B using different interleaved datasets. The results are evaluated on 4 common VQA and 3 math-related benchmarks under few-shot settings.
> </details>

{{< table-caption >}}
|                       | OKVQA | TextVQA | MathVista | MathVison | MathVerse | OKVQA | TextVQA | MathVista | MathVison | MathVerse |
|-----------------------|-------|---------|-----------|-----------|----------|-------|---------|-----------|-----------|----------|
| **Continual Pre-training from Idefics2-8B-base** |       |         |           |           |          |       |         |           |           |          |
| Dataset                 |       |         |           |           |          |       |         |           |           |          |
| MMC4-cf                 | 54.1  | 57.7    | 27.8      | 14.0      | 17.3     | 9.4   | 25.1    | 24        | 13.3      | 18.3     |
| OBELICS                 | 54.6  | 57.5    | 27.6      | 14.3      | 17.5     | 10.5  | 25.7    | 24.2      | 13.6      | 17.7     |
| Textbook-6.5M          | 55.1  | 58.2    | 29.7      | 16.2      | 19.4     | 10.1  | 26.8    | 26.1      | 14.4      | 19.8     |
| **Pre-training Idefics2-8B from scratch** |       |         |           |           |          |       |         |           |           |          |{{< /table-caption >}}
> 🔼 표 3은 LLaVA 모델 외에도, 다중 이미지 처리 능력을 갖춘 고급 VLM인 Idefics 모델을 사용한 실험 결과를 보여줍니다. Idefics-8B 기반 모델을 지속적으로 학습시키거나 처음부터 학습시키는 두 가지 방법을 사용했습니다. 기존 연구[16]를 바탕으로 평가는 8-shot 설정으로 확장되었으며, 무작위로 선택된 예시를 사용했습니다.  표는 TextVQA, OKVQA, MathVista, MathVision, MathVerse와 같은 다양한 벤치마크에 대한 결과를 보여주어, 각 모델의 성능을 비교 분석하는 데 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Except for LLaVA, we also pre-train advanced VLMs with multi-image ability (Idefics): continual pretraining from Idefics-8B-base or pre-training from scratch. The evaluations are extended to an 8-shot using randomly selected examples as previous works [16].
> </details>

{{< table-caption >}}
| Dataset | OKVQA | TextVQA | Mathvista | Mathvision | Mathverse |
|---|---|---|---|---|---| 
| *1-shot Cheat: Example:* {$I_t$, $q_t$, $a_t$} + Test-case: $I_t$, $q_t$ |  |  |  |  |  |
| MMC4-cf | 69.0 | 41.0 | 72.6 | 69.3 | 55.7 |
| OBELICS | 71.5 | 43.8 | 67.7 | 66.5 | 62.8 |
| Ours | **79.2** | **51.9** | **94.1** | **98.4** | **76.8** |
| *2-shot Cheat: Example:* {$I_t$, $q_t$, $a_t$}, {$I_e$, $q_e$, $a_e$} + Test-case: $I_t$, $q_t$|  |  |  |  |  |
| MMC4-Cf | 53.5 | 39.2 | 55.7 | 51.9 | 40.8 |
| OBELICS | 71.3 | 42.8 | 56.7 | 39.9 | 39.5 |
| Ours | **84.3** | **49.4** | **77.1** | **70.7** | **63.1** |{{< /table-caption >}}
> 🔼 표 4는 VLMs이 문맥 내 정보를 얼마나 잘 활용하는지 확인하기 위한 '속임수 테스트' 결과를 보여줍니다. 테스트는 기존의 몇몇 샷 예제 중 하나를 테스트 샘플 자체로 바꿔서 진행되었습니다.  VLMs이 동일한 이미지, 질문, 답변이 이미 문맥 내에 존재하는 것을 인식하고 쉽게 답변하는지 확인하기 위한 것입니다.  I<sub>t</sub>, q<sub>t</sub>, a<sub>t</sub>는 테스트 케이스를 나타내고, I<sub>e</sub>, q<sub>e</sub>, a<sub>e</sub>는 무작위로 선택된 예제를 나타냅니다.  즉, 테스트 샘플과 동일한 예제가 몇몇 샷 예제에 포함되어 있는 상황에서 모델의 성능을 평가한 것입니다.
> <details>
> <summary>read the caption</summary>
> Table 4: We design “Cheat Test” to observe whether VLMs can attend to their interleaved context. We replace a few-shot example with the test sample itself and observe whether VLM notice this identical <<<image,question,answer>>> within their prompt. Itsubscript𝐼𝑡I_{t}italic_I start_POSTSUBSCRIPT italic_t end_POSTSUBSCRIPT, qtsubscript𝑞𝑡q_{t}italic_q start_POSTSUBSCRIPT italic_t end_POSTSUBSCRIPT, atsubscript𝑎𝑡a_{t}italic_a start_POSTSUBSCRIPT italic_t end_POSTSUBSCRIPT denote the test case, Iesubscript𝐼𝑒I_{e}italic_I start_POSTSUBSCRIPT italic_e end_POSTSUBSCRIPT, qesubscript𝑞𝑒q_{e}italic_q start_POSTSUBSCRIPT italic_e end_POSTSUBSCRIPT, aesubscript𝑎𝑒a_{e}italic_a start_POSTSUBSCRIPT italic_e end_POSTSUBSCRIPT denote a random selected example.
> </details>

{{< table-caption >}}
| Pretraining | Continual Pretraining | SFT | OKVQA | MathVista |
|---|---|---|---|---|
| ✓ | - | ✓ | 61.1 | 23.2 |
| ✓ | MMC4-Core-ff | ✓ | 61.5 ↑0.4 | 24.8 ↑1.6 |
| ✓ | OBELICS | ✓ | 61.8 ↑0.7 | 25.6 ↑2.4 |
| ✓ | Textbook-6.5M | ✓ | **62.2 ↑1.1** | **28.7 ↑5.5** |{{< /table-caption >}}
> 🔼 표 5는 LLaVA-1.5의 665K 데이터를 사용하여 instruction fine-tuning 후 zero-shot 결과를 평가한 것입니다.  LLaVA-1.5 모델에 대해 MMC4-Core-ff, OBELICS, 그리고 논문에서 제안하는 Multimodal Textbook 데이터셋으로 사전 학습 후 instruction fine-tuning을 진행한 zero-shot 성능을 OKVQA와 MathVista 지표를 통해 비교 분석한 표입니다.  각 데이터셋의 zero-shot 성능을 보여주며, Multimodal Textbook 데이터셋을 사용했을 때 성능 향상이 눈에 띄게 나타남을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 5: We also evaluated the zero-shot result after instruction fine-tuning using the 665K data from LLaVA-1.5.
> </details>

{{< table-caption >}}
| Dataset | Perplexity ↓ | 1-shot Acc. |
|---|---|---|
| MMC4-Core-ff | 12.56 | 20.7 |
| OBELICS | 11.27 | 22.8 |
| Ours (ASR Refine, OCR, SSIM) | 13.92 | 31.1 |
| - w/o ASR Refine | 16.86 | 26.2 (↓4.9) |
| - w/o OCR | 12.7 | 28.8 (↓2.3) |
| Keyframe Extraction algorithms | #Keyframe | 1-shot Acc. |
| - SSIM→Pixel-level extractor | 6.5M → 18M | 22.1 (↓9) |
| - SSIM→CLIP-based extractor | 6.5M → 1.7M | 24.6 (↓6.5) |{{< /table-caption >}}
> 🔼 표 6은 비디오-교재 파이프라인에 대한 ablation 연구 결과를 보여줍니다. ASR 개선의 영향, OCR 통합의 필요성, 그리고 키프레임 추출 알고리즘의 비교를 포함합니다.  구체적으로, ASR 개선을 하지 않았을 때, OCR을 통합하지 않았을 때, 그리고 서로 다른 키프레임 추출 알고리즘을 사용했을 때의 성능 변화를 정량적으로 분석합니다.  이는 모델 성능에 대한 각 구성 요소의 기여도를 파악하고, 비디오-교재 파이프라인의 최적화 방향을 제시하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 6: We perform an ablation study on video-to-textbook pipeline, including the impact of ASR refinement, the necessity of incorporating OCR, and the algorithms for extracting keyframes.
> </details>

{{< table-caption >}}
| Subject | #Video | Duration (h) | #Topic | #Video Clip | #Keyframe | #ASR Token | #OCR Token | #Sample |
|---|---|---|---|---|---|---|---|---|
| Mathematics | 21.7k | 4,423 | 725 | 809k | 1.67M | 72.5M | 145M | 123k |
| Physics | 11k | 3,511 | 530 | 822k | 0.95M | 36.7M | 73.4M | 119k |
| Chemistry | 4.5k | 2,643 | 410 | 234k | 0.49M | 15M | 30M | 32k |
| Earth Science | 12k | 3,670 | 520 | 640k | 1.03M | 40M | 80M | 88k |
| Engineering | 13k | 4,096 | 810 | 713k | 1.15M | 43.3M | 86.6M | 98k |
| Computer Science | 12.8k | 4,354 | 820 | 782k | 1.21M | 42.8M | 85.5M | 150k |
| **All** | **75k** | **22,697** | **3,915** | **4M** | **6.58M** | **258M** | **500M** | **610k** |{{< /table-caption >}}
> 🔼 표 7은 제시된 논문의 다중 모드 교과서 통계를 보여줍니다. 각 비디오 범주에 포함된 지식 포인트의 수를 보여주는 표입니다. 이 표는 다중 모드 교과서의 규모와 다양성을 보여주는 데 도움이 됩니다. 각 열은 비디오 수, 비디오의 총 지속 시간, 주제 수, 비디오 클립 수, 키프레임 수, ASR 토큰 수, OCR 토큰 수, 샘플 수를 나타냅니다. 각 행은 수학, 물리, 화학, 지구 과학, 공학, 컴퓨터 과학의 6가지 주제를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 7: The statistics of our multimodal textbook. Topic denotes the knowledge points covered by each category of videos, which are sourced from our knowledge taxonomy.
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