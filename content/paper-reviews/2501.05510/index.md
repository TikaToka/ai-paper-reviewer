---
title: "OVO-Bench: How Far is Your Video-LLMs from Real-World Online Video Understanding?"
summary: "OVO-Bench: 온라인 비디오 이해 모델의 시간적 인식 능력 평가를 위한 새로운 벤치마크"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Video Understanding", "🏢 Tsinghua University",]
showSummary: true
date: 2025-01-09
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.05510 {{< /keyword >}}
{{< keyword icon="writer" >}} Yifei Li et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-13 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.05510" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.05510" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/ovo-bench-how-far-is-your-video-llms-from" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 비디오 이해 연구는 주로 오프라인 환경, 즉 비디오 전체를 보고 질문에 답하는 방식에 초점을 맞춰왔습니다. 하지만 실제 온라인 비디오 서비스나 자율주행 등의 응용 분야에서는 **비디오가 실시간으로 제공**되고 질문 또한 언제든지 발생할 수 있으므로, **시간에 따른 동적인 이해 능력**이 중요합니다.  그러나 기존 벤치마크는 이러한 온라인 환경을 충분히 반영하지 못했습니다.

본 논문에서는 이러한 문제를 해결하기 위해 **OVO-Bench라는 새로운 벤치마크**를 제시합니다. OVO-Bench는 **실제 온라인 비디오 데이터**를 사용하고, **과거 정보 추적, 실시간 이해, 미래 예측** 등 다양한 시나리오를 포함하여 모델의 시간적 인식 능력을 종합적으로 평가합니다.  연구 결과, 기존 모델들이 온라인 비디오 이해에 어려움을 겪고 있음을 보여주었으며,  OVO-Bench가 **온라인 비디오 이해 모델의 발전**에 중요한 기여를 할 것으로 기대하고 있습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} OVO-Bench는 **시간 경과에 따른 동적 추론 능력**을 평가하는 새로운 벤치마크입니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 기존 벤치마크의 한계를 극복하고 **실제 온라인 환경**을 반영한 평가를 제공합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} **과거 추적, 실시간 이해, 미래 예측** 등 다양한 시나리오에서의 모델 성능을 종합적으로 평가합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **온라인 비디오 이해에 대한 새로운 벤치마크인 OVO-Bench를 제시**함으로써, 기존의 오프라인 중심 벤치마크의 한계를 극복하고 **실제 온라인 환경에서의 비디오 이해 모델 성능 평가를 위한 새로운 기준**을 마련합니다. 이는 **시간적 인식 능력을 중시하는 새로운 평가 방식**을 제시하며, 앞으로 온라인 비디오 이해 연구의 발전에 크게 기여할 것으로 예상됩니다.  특히, **시간 경과에 따른 동적 추론 능력**을 평가하는 새로운 평가 지표를 제시하고, 다양한 시나리오(과거 추적, 실시간 이해, 미래 예측)에서의 모델 성능을 종합적으로 평가하여 온라인 비디오 이해 모델의 발전 방향을 제시합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.05510/x1.png)

> 🔼 그림 1은 오프라인 및 온라인 비디오 이해 방식을 비교한 것입니다. 오프라인 비디오 이해는 전체 비디오를 기반으로 질문에 답하는 반면, 온라인 비디오 이해는 비디오 중간 지점에서 문맥에 대한 질문을 하고 과거 정보를 추적하고, 현재 진행 중인 이벤트를 인지하며, 지속적인 입력에 적응하는 능력을 필요로 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  A demonstrative comparison between offline and online video understanding [5]. Offline video understanding focuses on answering questions based on the entirety of a video. In contrast, online video understanding involves posing queries about the context of a video at intermediate points, demanding the ability to trace back past information, perceive ongoing events, and adapt to continuous input.
> </details>





{{< table-caption >}}
| Model | # Frames | OCR | ACR | ATR | STU | FPD | OJR | Avg. | EPM | ASI | HLD | Avg. | REC | SSR | CRR | Avg. | Overall Avg. |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| **Human** |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| Human Agents | - | 93.96 | 92.57 | 94.83 | 92.70 | 91.09 | 94.02 | 93.20 | 92.59 | 93.02 | 91.37 | 92.33 | 95.48 | 89.67 | 93.56 | 92.90 | 92.81 |
| **Blind LLMs** |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| GPT-4-turbo | - | 28.86 | 24.77 | 25.67 | 33.76 | 27.72 | 26.63 | 27.90 | 42.76 | 48.65 | 70.05 | 53.82 | - | - | - | - | - |
| **Proprietary Multimodal Models-Offline** |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| Gemini 1.5 Pro | 1fps | 87.25 | 66.97 | 80.17 | 54.49 | 68.32 | 67.39 | 70.77 | 68.59 | 75.68 | 52.69 | 62.32 | 35.53 | 74.24 | 61.67 | 57.15 | 65.25 |
| GPT-4o | 64 | 69.13 | 65.14 | 65.52 | 50.00 | 68.32 | 63.68 | 63.63 | 49.83 | 70.95 | 55.38 | 58.72 | 27.58 | 73.21 | 59.4 | 53.40 | 58.58 |
| **Open-source Multimodal Models-Offline** |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| Qwen2-VL-72B | 64 | 72.48 | 56.88 | 77.59 | 52.25 | 74.26 | 61.41 | 65.81 | 51.52 | 73.65 | 63.44 | 62.87 | 37.68 | 60.10 | 45 | 47.59 | 58.76 |
| LLaVA-NeXT-Video-7B | 64 | 69.80 | 59.63 | 66.38 | 50.56 | 72.28 | 61.41 | 63.34 | 51.18 | 64.19 | 9.68 | 41.68 | 34.10 | 67.57 | 60.83 | 54.17 | 53.06 |
| LLaVA-OneVision-7B | 64 | 67.11 | 58.72 | 69.83 | 49.44 | 71.29 | 60.33 | 62.79 | 52.53 | 58.78 | 23.66 | 44.99 | 24.79 | 66.93 | 60.83 | 50.85 | 52.88 |
| Qwen2-VL-7B | 64 | 69.13 | 53.21 | 63.79 | 50.56 | 66.34 | 60.87 | 60.65 | 44.44 | 66.89 | 34.41 | 48.58 | 30.09 | 65.66 | 50.83 | 48.86 | 52.70 |
| InternVL-V2-8B | 64 | 68.46 | 58.72 | 68.97 | 44.94 | 67.33 | 55.98 | 60.73 | 43.10 | 61.49 | 27.41 | 44.00 | 25.79 | 57.55 | 52.92 | 45.42 | 50.05 |
| LongVU-7B | 1fps | 55.70 | 49.54 | 59.48 | 48.31 | 68.32 | 63.04 | 57.40 | 43.10 | 66.22 | 9.14 | 39.49 | 16.62 | 69.00 | 60.00 | 48.54 | 48.48 |
| **Open-source Multimodal Models-Online** |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| Flash-VStream-7B | 1fps | 25.50 | 32.11 | 29.31 | 33.71 | 29.70 | 28.80 | 29.86 | 36.36 | 33.78 | 5.91 | 25.35 | 5.44 | 67.25 | 60.00 | 44.23 | 33.15 |
| VideoLLM-online-8B | 2fps | 8.05 | 23.85 | 12.07 | 14.04 | 45.54 | 21.20 | 20.79 | 22.22 | 18.80 | 12.18 | 17.73 | - | - | - | - | - |{{< /table-caption >}}

> 🔼 표 1은 OVO-Bench에 대한 자세한 평가 결과를 보여줍니다.  † 표시는 '낮은' 해상도를 사용했음을 나타냅니다. 질문과 단서 사이의 시간 간격을 늘려 질문의 난이도를 높이기 위해 표의 [EPM]과 [ASI]에 대한 질문 시간은 비디오의 끝으로 통일하여 배치되었습니다. [HLD]는 스트리밍 모드를 따르는 표준 방식으로 평가되었습니다.  선행적 응답에 대해서는 정확도 기반 평가 지표가 사용되었습니다. 고품질 [ASI] 작업이 추가되어 차별화가 더욱 강화되었습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Detailed evaluation results on OVO-Bench. † refers to using ”low” resolution. To enhance the challenge of the questions by increasing the time interval between the question and the clues, the question time for [EPM] and [ASI] in the table is uniformly placed at the end of the video. [HLD] are evaluated in the standard manner following the streaming mode. For Forward Active Responding, accuracy-based evaluation metrics are utilized in this table. More high-quality [ASI] tasks are supplemented, further enhancing differentiation.
> </details>





### In-depth insights


#### Online Video LLM Gap
본 논문은 **온라인 비디오에 대한 이해 능력에서 비디오 LLM(대규모 언어 모델)의 성능과 인간의 능력 사이에 상당한 차이**가 존재함을 보여줍니다. 이러한 차이는 단순히 기술적 한계를 넘어, **비디오 데이터의 시간적 특성을 고려한 동적인 추론 능력의 부재**에서 기인합니다. 기존 벤치마크들은 주로 정적인 오프라인 설정을 기반으로 하여, 비디오 전반에 걸친 정보를 모두 활용할 수 있는 상황에서 모델의 성능을 평가합니다. 하지만 **실제 온라인 환경에서는 비디오가 실시간으로 스트리밍되고 질문이 임의의 시점에 제기되기 때문에, 과거 정보를 추적하고 현재 상황을 파악하며 미래를 예측하는 능력**이 중요합니다. 논문에서 제시된 OVO-Bench는 이러한 온라인 비디오 이해 능력을 종합적으로 평가하기 위한 새로운 벤치마크로서, **시간적 인식 능력의 중요성을 강조**합니다. 따라서 **향후 연구는 온라인 비디오 상황에서의 동적 추론 능력을 향상**시키는 데 집중해야 하며, OVO-Bench는 이러한 연구 방향을 제시하는 중요한 기준점이 될 것입니다.

#### OVO-Bench: Design
OVO-Bench는 **온라인 비디오 이해를 위한 새로운 벤치마크**로서, 기존 오프라인 방식의 한계를 넘어 **시간적 요소를 중시하는 평가 시스템**을 제시합니다.  **역추적, 실시간 이해, 사전 예측 응답** 등 세 가지 주요 모드를 통해 비디오-LLM의 동적 추론 능력을 다각적으로 평가합니다.  **다양한 영역의 고품질 비디오 데이터**를 활용하여 현실 세계의 온라인 비디오 이해에 가까운 시나리오를 구축하고, **정확한 시간 정보가 포함된 세밀한 어노테이션**을 통해 모델의 성능을 객관적으로 측정합니다.  **인간 수준의 온라인 비디오 이해 능력**과의 차이를 명확히 드러내어, 향후 비디오-LLM 연구의 방향을 제시하는 데 기여할 것으로 기대됩니다. 특히 **Forward Active Responding 모드**는 미래 정보를 고려한 응답을 요구하여, 기존 벤치마크에서는 다루지 않던 **시간적 동적 추론 능력**을 평가하는 중요한 지표가 될 것입니다.  **다양한 질의 유형과 시나리오**를 포함하여 모델의 견고성과 일반화 능력을 평가함으로써, 보다 현실적인 온라인 비디오 이해 시스템의 개발을 촉진할 것입니다.

#### Benchmark Results
본 논문의 벤치마크 결과는 **비디오-LLM의 온라인 비디오 이해 능력에 대한 중요한 통찰력**을 제공합니다. 오프라인 모델은 정적 비디오에 대한 강력한 이해 능력을 보여주지만, 동적이고 시간에 따른 추론이 필요한 온라인 질문에는 어려움을 겪는다는 것을 보여줍니다. 특히, **시간적 인식(temporal awareness)이 부족하여 실시간으로 벌어지는 사건에 대한 정확한 이해와 반응에 어려움**을 겪습니다.  반면, 온라인 모델은 실시간 이해 능력을 보여주지만, 오프라인 모델에 비해 성능이 떨어지는 것으로 나타났습니다. 이는 **온라인 비디오 이해를 위한 모델 아키텍처와 훈련 방법의 개선 필요성**을 시사합니다. 또한, **환각(hallucination) 현상이 온라인 및 오픈소스 모델에서 빈번하게 발생**하며, 이는 모델의 신뢰성과 정확성에 대한 우려를 제기합니다.  전반적으로, 이 벤치마크 결과는 **현재의 비디오-LLM이 실제 온라인 비디오 이해에 필요한 수준에 도달하지 못했음**을 강조하며, 향후 연구 방향을 제시하는 데 중요한 역할을 합니다.

#### Temporal Awareness
본 논문에서 강조하는 핵심 개념 중 하나인 "시간적 인지(Temporal Awareness)"는 **비디오의 시간적 흐름을 이해하고 이를 질의응답에 동적으로 반영하는 능력**을 의미합니다. 기존의 오프라인 비디오 이해 모델들은 전체 비디오를 한꺼번에 처리하여 질문에 답하는 반면, 시간적 인지 능력을 갖춘 온라인 모델은 비디오 스트림을 순차적으로 처리하면서 **질문이 제기된 시점을 고려하여 동적으로 응답**을 생성합니다. 이는 **실제 온라인 비디오 이해 시나리오**에서 매우 중요한 요소이며, **과거 정보를 추적하고 현재 상황을 인지하며 미래를 예측**하는 능력을 모두 필요로 합니다.  본 연구는 기존 벤치마크들이 시간적 인지 능력을 충분히 평가하지 못하고 있음을 지적하며, 이를 개선하기 위한 새로운 벤치마크인 OVO-Bench를 제시합니다. 따라서 시간적 인지는 단순히 비디오 내용을 이해하는 것을 넘어, **시간에 따른 사건의 맥락을 파악하고 이를 종합적으로 활용**하는 고차원적인 능력으로 볼 수 있습니다.

#### Future Research
본 논문에서 제시된 OVO-Bench는 **온라인 비디오 이해에 대한 벤치마크**로서, 기존 벤치마크의 한계를 극복하고 실제 상황에 가까운 평가를 제공합니다. 하지만, 아직 온라인 비디오 이해 분야는 초기 단계이며, 향후 연구 방향은 다양하게 설정될 수 있습니다. **더욱 다양하고 복잡한 비디오 데이터셋**을 구축하고, **시간적 요소를 고려한 새로운 평가 지표** 개발 및 **모델의 일반화 성능 향상** 연구가 필요합니다. 특히, **비디오의 시각적 정보뿐 아니라 청각적, 언어적 정보**를 통합적으로 고려하는 멀티모달 모델 개발과, **실시간 처리 속도 향상**을 위한 효율적인 알고리즘 개발도 중요한 연구 과제입니다. 또한, **모델의 설명 가능성 향상**을 통해, 모델의 의사결정 과정을 이해하고 신뢰도를 높이는 연구도 필요합니다.  **에고센트릭 비디오와 같은 특수한 유형의 비디오 데이터**에 대한 연구도 중요하며, **다양한 언어**를 지원하는 다국어 모델 개발 또한 필요합니다.  궁극적으로는 **인간 수준의 온라인 비디오 이해 능력**을 갖춘 인공지능 시스템을 개발하는 것이 목표입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.05510/x2.png)

> 🔼 그림 2는 OVO-Bench의 각 과제에 대한 예시를 보여줍니다. 총 14개의 과제는 크게 세 가지 유형의 온라인 비디오 이해 인식 모드로 분류됩니다: 과거 추적(Backward Tracing), 실시간 시각적 인식(Real-Time Visual Perception), 그리고 전향적 능동적 응답(Forward Active Responding). 각 모드는 비디오의 과거, 현재, 미래에 대한 질문에 어떻게 대응하는지 보여주는 다양한 유형의 질문과 답변을 포함합니다. 과거 추적은 과거 이벤트를 추적하여 질문에 답하는 능력을 평가하고, 실시간 시각적 인식은 현재 일어나는 일을 이해하고 즉시 반응하는 능력을 평가하며, 전향적 능동적 응답은 충분한 미래 정보가 제공될 때까지 응답을 지연시키는 능력을 평가합니다. 각 과제는 다양한 비디오 유형과 시나리오를 다루어 온라인 비디오 이해 모델의 포괄적인 평가를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Examples of each task in OVO-Bench. The 14 tasks are categorized into three different kinds of perceiving modes in online video understanding: Backward Tracing, Real-Time Visual Perception, and Forward Active Responding.
> </details>



![](https://arxiv.org/html/2501.05510/extracted/6119562/sec/image/model0.png)

> 🔼 그림 3은 OVO-Bench의 데이터 생성 파이프라인을 보여줍니다. 기존의 공개된 주석 데이터에서 관련성이 높은 객관식 문제와 답변(QAs)을 자동으로 생성하기 위해 데이터를 신중하게 필터링하고 선택합니다.  시스템 프롬프트와 효율적인 응답 프롬프트를 사용하여  대규모 언어 모델(MLLMs)이 정확한 결과를 생성하도록 유도합니다. 비디오 주석을 달기 위해 사용된 비디오-LLM은 GPT-4o와 Gemini-1.5 Pro입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3:  Generation pipeline of OVO-Bench. Within public annotations, data is carefully filtered and relevant multiple-choice QAs are auto-generated. The effective system prompt and efficient answer prompt are employed to guide MLLMs toward precise outputs. The Video-LLMs we use to annotate videos are GPT-4o and Gemini-1.5 Pro.
> </details>



![](https://arxiv.org/html/2501.05510/x3.png)

> 🔼 그림 4는 OVO-Bench 데이터셋에 대한 세 가지 측면을 보여줍니다. 왼쪽은 질문의 시간적 분포를 보여주는 히스토그램으로, OVO-Bench의 질문들이 비디오 전체 시간에 걸쳐 고르게 분포되어 있음을 보여줍니다. 가운데는 질문의 언어적 특징들을 보여주는 워드 클라우드로, 자주 등장하는 단어들을 시각적으로 표현합니다. 이는 질문의 주요 주제와 범위를 파악하는 데 도움을 줍니다. 오른쪽은 OVO-Bench 데이터셋에 포함된 비디오의 카테고리 분포를 보여주는 파이 차트로, 각 카테고리의 비디오 수를 비율로 나타냅니다. 이는 OVO-Bench의 데이터셋 다양성을 평가하는 데 사용될 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4:  Left Queries Temporal Distribution in OVO-Bench. Center Linguistic Characteristics of Text Queries. Right Video category distribution of OVO-Bench.
> </details>



![](https://arxiv.org/html/2501.05510/x4.png)

> 🔼 그림 5는 온라인 비디오-LLM과 오프라인 비디오-LLM의 성능 비교를 보여줍니다. 이 그림은 OVO-Bench의 실시간 시각적 인식 작업에서 여러 모델의 평균 점수를 보여줍니다. 온라인 및 오프라인 모델 모두의 강점과 약점을 비교하여 실시간 시각적 이해 능력을 평가합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5:  Performance comparison between online Video-LLMs and offline Video-LLMs. The figure illustrates the average scores of different models on the OVO-Bench in real-time visual perception tasks.
> </details>



![](https://arxiv.org/html/2501.05510/x5.png)

> 🔼 그림 6은 오프라인 비디오-LLM을 위한 다중 트리거 평가 파이프라인을 보여줍니다.  온라인 비디오 이해를 위해, 오프라인 비디오-LLM은 시간적 축을 따라 밀집되게 질문을 받습니다. 각 질문 시점마다 모델은 기존의 시각적 콘텐츠가 답변에 충분한 단서를 제공하는지 여부를 독립적으로 판단합니다.  즉, 비디오의 특정 시점에 질문이 주어지면, 모델은 그 시점까지의 비디오 프레임만을 사용하여 답을 찾아야 합니다. 이러한 과정을 통해 모델의 실시간 추론 능력과 제한된 정보만으로도 정확한 답변을 도출할 수 있는 능력을 평가합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6:  Multiple triggering evaluation pipeline of prompt offline models for online video understanding. Offline Video-LLMs are densely queried along the temporal axes to make independent decisions of whether existing visual content provide enough clues for answering.
> </details>



![](https://arxiv.org/html/2501.05510/extracted/6119562/sec/image/supplimentary/222.png)

> 🔼 그림 7은 논문의 3.2절(Benchmark Construction)에 있는 그림으로, Forward Active Responding 작업에 대한 온라인(위쪽) 및 오프라인(아래쪽) 모델에 사용된 프롬프트와 응답 예시를 보여줍니다.  온라인 모델에 대한 연구진의 기대와 달리, VideoLLM-online과 같은 기존 온라인 모델은 복잡하거나 훈련 데이터 영역 밖의 비디오 및 질의를 처리할 때 적응력이 부족하고 쉽게 실패하는 것으로 나타났습니다. 반면 오프라인 모델은  'is/currently/ongoing' 과 같은 단어가 질문에 포함될 경우 무작위로 추측하는 경향이 있었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7:  Prompts used for Online(up) and Offline(down) Models on Forward Active Responding and Response Examples. Despite our vision for online models, existing online models, like videollm-online, are still far from satisfactory, showing limited adaptation ability, and would easily encounter collapse when processing complicated or out-of-training-domain video and queries. Offline models are inclined to perform random guessing when the queries contain words like ”is/currently/ongoing”.
> </details>



![](https://arxiv.org/html/2501.05510/extracted/6119562/sec/image/supplimentary/111.png)

> 🔼 그림 8은 실시간 비디오 이해에 대한 온라인 및 오프라인 모델에 사용된 프롬프트와 응답 예시를 보여줍니다.  [ACR](Action Recognition), [OCR](Optical Character Recognition), [ASI](Action Sequential Identification) 세 가지 작업이 시범으로 포함되어 있습니다. 벤치마크에는 시간에 따라 답변이 바뀌는 질문이 많이 포함되어 있어, 모델이 원본 비디오에서 무작위로 프레임을 선택하여 답을 찾는 것이 어렵다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8:  Prompts used for Online(up) and Offline(down) Models on Real-Time Visual Perception and Response Examples. Three tasks including [ACR], [OCR], and [ASI] are included as demonstrations. Our benchmarks involve a large ratio of questions, whose answers shift over time, which means that models can hardly figure out the answer by randomly selecting frames from original videos.
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