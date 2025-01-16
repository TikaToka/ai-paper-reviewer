---
title: "Tarsier2: Advancing Large Vision-Language Models from Detailed Video Description to Comprehensive Video Understanding"
summary: "Tarsier2는 세분화된 비디오 설명 생성과 뛰어난 일반적인 비디오 이해 능력을 갖춘 최첨단 대규모 비전-언어 모델입니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Vision-Language Models", "🏢 ByteDance Research",]
showSummary: true
date: 2025-01-14
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.07888 {{< /keyword >}}
{{< keyword icon="writer" >}} Liping Yuan et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-15 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.07888" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.07888" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/tarsier2-advancing-large-vision-language" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존 대규모 비전-언어 모델(LVLM)은 정확한 시간적 이해, 공간-시간적 추론, 환각 문제 등으로 인해 인간 수준의 비디오 이해 능력에는 미치지 못했습니다.  특히, 세부적인 비디오 설명 생성은 여전히 어려운 과제였습니다.

본 논문에서는 이러한 문제들을 해결하기 위해, **4000만 개의 비디오-텍스트 쌍을 활용한 대규모 사전 학습**, **세분화된 시간 정렬을 수행하는 지도식 미세 조정**, **모델 기반 샘플링을 통한 선호도 데이터 자동 생성 및 DPO 최적화** 등의 기술을 통해 Tarsier2를 개발했습니다.  Tarsier2는 비디오 설명 생성 뿐 아니라, 비디오 질의응답, 비디오 기반 작업 등 다양한 과제에서 최첨단 성능을 달성하여 강력한 일반적인 비전-언어 모델임을 입증했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} Tarsier2는 대규모 사전 학습 데이터, 세분화된 시간 정렬, 모델 기반 샘플링을 사용하여 비디오 이해 성능을 크게 향상시켰습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 비디오 설명 생성, 비디오 질의응답 등 다양한 비디오 이해 과제에서 최첨단 성능을 달성했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 자동으로 선호도 데이터를 생성하고 DPO 학습을 적용하여 모델 성능을 더욱 향상시켰습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **비디오 이해 분야의 혁신적인 발전**을 제시하며, 특히 **세분화된 비디오 설명 생성 및 포괄적인 비디오 이해 능력**을 향상시킨 대규모 비전-언어 모델(LVLM)인 Tarsier2를 소개합니다. 이는 기존 모델의 한계를 극복하고 새로운 연구 방향을 제시하여, **다양한 비디오 관련 연구**에 큰 영향을 미칠 것입니다.  **비디오 설명 생성, 비디오 질의응답, 비디오 기반 작업 등 다양한 과제**에서 최첨단 성능을 달성하여,  **연구자들이 보다 정교하고 포괄적인 비디오 이해 시스템 개발**을 위한 새로운 기반을 제공합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.07888/extracted/6130403/figs/pretrain_data.png)

> 🔼 그림 1은 7B 크기의 모델과 GPT-4o 모델을 포함하여, Tarsier2 모델의 성능을 이전 최고 성능 모델들과 비교한 표입니다. 다양한 비디오 이해 작업 벤치마크에서 평균 점수를 보여줍니다. 각 벤치마크는 여러 하위 작업 또는 측정항목으로 구성되어 있으며, Tarsier2가 여러 벤치마크에서 최고 성능을 달성했음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Performance comparison of Tarsier2 with previous SOTA models at 7B-scale and GPT-4o. We report the overall average scores for benchmarks with multiple subtasks/metrics.
> </details>





{{< table-caption >}}
| Benchmark | Previous SOTA |
|---|---| 
| DREAM-1K [105] | Tarsier-7B [105] |
| MVBench [57] | InternVL2.5-8B [20] |
| TVBench [25] | IXC-2.5 7B [124] |
| TOMATO [94] | Qwen2-VL-7B [106] |
| Vinoground [123] | LLaVA-OV-7B [53] |
| TempCompass [69] | Qwen2-VL-7B [106] |
| Video-MME [31] | NVILA-7B [70] |
| LongVideoBench [110] | Apollo-7B [130] |
| TemporalBench [12] | LLaVA-Video-7B [127] |
| MLVU [128] | InternVL2.5-8B [20] |
| MMBench-Video [30] | MiniCPM-V-2.6 [119] |
| VideoHallucer [109] | Qwen2-VL-7B [106] |
| EventHallusion [122] | Tarsier-7B [105] |
| E.T. Bench [67] | E.T. Chat [67] |{{< /table-caption >}}

> 🔼 DREAM-1K 비디오 캡션링 벤치마크에 대한 Tarsier2의 성능 평가 결과를 보여주는 표입니다.  표에는 각 카테고리와 전체 데이터셋에 대한 F1 점수, 정밀도, 재현율이 표시되어 있습니다. 오픈소스 모델의 경우, 공식 체크포인트와 추론 코드를 사용하여 권장 설정으로 모든 결과를 테스트했습니다. 비슷한 규모(10B 미만)의 최첨단(SOTA) 결과는 굵게 표시되었고, 최고의 결과는 밑줄이 그어져 있습니다.  다양한 유형의 비디오에 대한 캡션 생성 능력을 종합적으로 평가합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Evaluation results on DREAM-1K. We report F1/Precision/Recall scores for each category and for the overall dataset. For open-source models, all results are tested with their official checkpoint and inference code under recommended setting. SOTA results of comparable scale (<<<10B) are bolded and overall best results are underlined.
> </details>





### In-depth insights


#### Tarsier2: Video LLMs
Tarsier2는 대규모 비디오-언어 모델(Video LLM)로, **세분화된 비디오 설명 생성 및 종합적인 비디오 이해 능력**에서 뛰어난 성능을 보여줍니다.  기존 모델들보다 훨씬 많은 4천만 개의 비디오-텍스트 쌍으로 사전 훈련되어 데이터 양과 다양성을 크게 향상시켰습니다. 또한, **세분화된 시간 정렬을 통한 지도 학습 미세 조정** 및 **모델 기반 샘플링을 활용한 DPO(Direct Preference Optimization) 최적화**를 통해 성능을 더욱 향상시켰습니다.  이러한 개선으로 인해, Tarsier2는 여러 비디오 이해 과제에서 최첨단(SOTA) 성능을 달성했으며, 특히 세부적인 비디오 설명 생성 능력이 두드러집니다.  이는 **대용량 데이터 학습**, **정교한 시간 정렬**, **효율적인 최적화 기법**의 조합이 시너지를 창출하여 **비디오 이해의 새로운 수준**을 제시함을 보여줍니다.  **GPT-4, Gemini와 같은 경쟁 모델들을 능가하는 성능**은 Tarsier2의 발전된 기술력과 잠재력을 보여주는 중요한 지표입니다. 향후 연구는 더욱 긴 비디오에 대한 처리 능력 향상 및 실시간 비디오 처리와 같은 방향으로 진행될 것으로 예상됩니다.

#### Multi-Stage Training
본 논문에서 제시된 다단계 학습 전략은 **전이 학습(Transfer Learning)**의 개념을 적극 활용하여, 비디오 이해 모델의 성능을 향상시키는 데 초점을 맞추고 있습니다.  **사전 학습(Pre-training)** 단계에서는 대규모의 다양한 비디오-텍스트 데이터를 사용하여 모델의 기본적인 비디오 이해 능력을 확보합니다. 이후 **지도 학습 미세 조정(Supervised Fine-tuning)** 단계에서는 정교하게 주석이 달린 데이터셋을 활용하여 모델의 정확도와 세부적인 묘사 능력을 높입니다. 특히, **시간적 정렬(Temporal Alignment)**을 고려한 미세 조정을 통해 비디오 내의 시간적 흐름을 정확하게 이해할 수 있도록 합니다.  마지막으로 **직접적 선호도 최적화(Direct Preference Optimization)** 단계를 통해 모델의 생성 품질을 향상시킵니다.  **모델 기반 샘플링(Model-based Sampling)**을 통해 자동으로 선호도 데이터를 생성하고, 이를 통해 모델이 더욱 효율적으로 학습하도록 유도하는 것이 특징입니다. 이러한 다단계 학습 과정은 각 단계의 장점을 결합하여, **종합적이고 정확한 비디오 이해 능력**을 갖춘 강력한 비디오-언어 모델을 구축하는 데 중요한 역할을 합니다.  **모델의 일반화 능력(Generalization)** 향상에도 기여하여, 다양한 비디오 관련 작업에 적용 가능성을 높입니다.

#### DPO for Enhancement
본 논문에서 제시된 DPO(Direct Preference Optimization) 기법은 비디오 이해 모델의 성능 향상에 중점을 둔 강화 학습 방식입니다. **자동화된 선호도 데이터 생성**을 통해 기존 지도 학습 방식의 한계를 극복하고자 하였으며, **모델 기반 샘플링**과 **선호도 데이터 필터링**이라는 두 가지 핵심 전략을 사용합니다.  **모델이 직접 생성한 샘플**을 통해 선호도를 자동으로 구성하여 효율성을 높였고, **AutoDQ**를 활용하여 품질이 낮은 데이터를 제거함으로써  전반적인 성능 향상에 기여합니다.  실험 결과는 DPO가 **비디오 묘사의 정확도 및 완성도 개선**에 효과적임을 보여주고, **환각 현상 감소**에도 긍정적인 영향을 미침을 확인했습니다. 이는 DPO를 통해 모델의 비디오 이해 능력을 향상시키고, 보다 정확하고 자세한 비디오 설명을 생성하는 데 기여할 수 있음을 시사합니다.  **GPT-4, Gemini와 같은 최첨단 상용 모델들과의 비교 실험**을 통해 DPO의 효과를 검증하였고, 향후 연구 방향으로 **장시간 비디오 처리 및 실시간 처리 기술**, 그리고 **오디오, 텍스트 정보와의 융합**을 통해 더욱 포괄적인 비디오 이해 시스템을 구축하는 것을 제시합니다. 

#### Benchmark Results
본 논문의 벤치마크 결과는 제시된 비전-언어 모델의 성능을 다양한 벤치마크 데이터셋에서 평가한 것을 보여줍니다. **다양한 비디오 이해 작업에서 최첨단 성능을 달성했다는 점을 강조하며,** 특히 비디오 캡셔닝, 비디오 질의응답, 비디오 접지와 같은 주요 작업에서 경쟁력 있는 결과를 보여줍니다.  **특히 GPT-4와 Gemini와 같은 최첨단 독점 모델을 능가하는 결과를 보여주는 것은 매우 인상적입니다.** 이는 모델의 강력한 성능과 일반화 능력을 입증합니다.  하지만, **벤치마크 결과만으로는 모델의 한계점이나 개선 여지에 대한 정보가 부족합니다.**  따라서, 향후 연구에서는 벤치마크 외 추가적인 분석을 통해 모델의 장단점을 더욱 심층적으로 파악하는 것이 필요합니다.  **특히, 벤치마크 데이터셋의 한계점과 편향성, 그리고 모델의 실제 적용 가능성에 대한 검토가 중요합니다.**  전반적으로, 제시된 벤치마크 결과는 모델의 우수성을 보여주지만, 더욱 폭넓고 깊이있는 분석이 필요하며,  다양한 실제 환경에서의 성능 검증을 통해 신뢰성을 높여야 합니다.

#### Future Work
본 논문은 비디오 이해를 위한 최첨단 거대 비전-언어 모델인 Tarsier2를 제시합니다.  **미래 연구 방향**으로는 먼저, **더 긴 비디오에 대한 Tarsier2의 확장성을 높이는 연구**가 필요합니다.  **더욱 효율적인 모델 아키텍처 개발**과 **더 방대한 훈련 데이터셋 확보**를 통해 장시간 비디오에 대한 이해 능력을 향상시켜야 합니다.  또한, **실시간 비디오 처리 기술 향상**을 위한 연구도 중요합니다.  스트리밍되는 비디오를 분석하고 묘사하는 모델의 능력을 향상시키는 것은 실제 응용 분야에서 매우 중요한 부분입니다.  마지막으로, **비디오, 오디오, 텍스트 간의 풍부한 상호작용을 탐구**하여 **보다 포괄적이고 맥락적인 비디오 이해 시스템을 만드는 것**이 중요한 미래 연구 과제입니다.  **다양한 모달리티 간의 통합적 이해를 통해 비디오 콘텐츠의 의미를 더욱 정확하게 파악하고 설명하는 모델 개발**은 Tarsier2의 한계를 극복하고 실제 응용 분야에서의 활용도를 높이는 데 기여할 것입니다. 이를 통해 **보다 포괄적인 비디오 이해 기술을 확보**하고,  **더욱 진보된 비디오 관련 서비스 및 애플리케이션 개발**에 중요한 역할을 할 것으로 기대됩니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.07888/extracted/6130403/figs/SFT_grounding.png)

> 🔼 그림 2는 Tarsier2의 다양한 기능들을 보여줍니다.  Tarsier2는 상세한 비디오 설명 생성 능력을 기반으로, 비디오 캡션 생성, 단/장시간 비디오 질의응답, 비디오 기반 객체탐색, 멀티 비디오 질의응답, 그리고 실제 로봇 환경 질의응답 등 다양한 비디오 중심 작업에서 뛰어난 성능을 보여줍니다. 그림의 각 영역은 Tarsier2가 수행하는 특정 작업을 예시로 보여주는 비디오 클립과 해당 작업에 대한 설명을 담고 있습니다. 플레이 버튼을 클릭하면 해당 비디오를 볼 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Overview of Tarsier2 capabilities. Based on its strong ability for detailed video description, Tarsier2 excels in a variety of video-centric tasks. Click the play buttons to view the videos.
> </details>



![](https://arxiv.org/html/2501.07888/x2.png)

> 🔼 이 그림은 Tarsier2의 사전 훈련 단계에서 사용된 데이터셋의 요약을 보여줍니다.  각 데이터셋의 종류(예: 비디오 캡션, 이미지 QA 등), 데이터셋의 출처(예: 오픈소스, 자체 수집 등), 그리고 각 데이터셋에 포함된 데이터의 개수를 시각적으로 나타냅니다. 이를 통해 Tarsier2의 사전 훈련에 사용된 방대한 양의 데이터와 다양한 데이터 유형을 한눈에 파악할 수 있습니다.  특히, 자체 수집된 데이터의 비중이 큰 것을 확인할 수 있으며, 이는 Tarsier2 모델의 성능 향상에 기여한 중요한 요소임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Summary of datasets used in the pre-training stage of Tarsier2.
> </details>



![](https://arxiv.org/html/2501.07888/extracted/6130403/figs/human_sbs.png)

> 🔼 그림 4는 세분화된 시간적 기반을 가진 비디오 설명의 예시를 보여줍니다. 'frame: i-j'는 해당 이벤트가 i번째 프레임부터 j번째 프레임까지 추론되었음을 나타냅니다. 각 이벤트는 색상으로 구분되며, 해당 프레임과 설명도 같은 색상으로 표시되어 이벤트 간의 연관성을 명확히 보여줍니다.  이 그림은 비디오의 각 프레임에 대한 상세한 설명과 이벤트의 시작 및 종료 시간을 보여줌으로써, 모델이 비디오 내 이벤트의 시간적 흐름을 정확하게 파악하고 있다는 것을 시각적으로 보여줍니다. 이를 통해 모델의 비디오 이해 능력 향상에 기여하는 세분화된 시간적 기반의 중요성을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: An example of a video description with fine-grained temporal grounding. “¡frame: i𝑖iitalic_i-j𝑗jitalic_j¿” indicates that the following event is inferred from frames i𝑖iitalic_i to j𝑗jitalic_j. Events are distinguished by color, with corresponding frames and descriptions marked in the same color to indicate their association.
> </details>



![](https://arxiv.org/html/2501.07888/x3.png)

> 🔼 본 그림은 DPO(Direct Preference Optimization) 학습 과정에서 선호도 데이터를 구성하는 파이프라인을 보여줍니다.  양성 샘플링은 원본 비디오와 모델이 생성한 비디오 설명을 보여주고, 음성 샘플링은 비디오 프레임을 임의로 변경하여 왜곡된 비디오와 그에 대한 모델의 설명을 보여줍니다.  AutoDQ 평가자는 선호도 쌍의 질을 평가하여, 양질의 선호도 데이터만 DPO 학습에 사용합니다.  전반적으로, 이 그림은 DPO 학습을 위한 고품질 선호도 데이터를 자동으로 생성하는 방법을 시각적으로 보여주는 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Preference data construction pipeline for DPO training.
> </details>



![](https://arxiv.org/html/2501.07888/x4.png)

> 🔼 그림 6은 Tarsier2와 다른 모델들(Tarsier-34B, GPT-40, Gemini 1.5 Pro)의 성능을 사람이 직접 비교 평가한 결과를 보여줍니다.  각 모델이 생성한 비디오 설명을 사람 평가자들이 비교하여 어떤 모델이 더 나은 설명을 생성했는지 판단하도록 했습니다.  그 결과를 Tarsier2가 다른 모델들에 비해 얼마나 더 나은 성능을 보이는지, 그리고 각 모델 간의 상대적 강점과 약점을 정량적으로 제시합니다.  세부적으로는 Tarsier2 대비 Tarsier-34B는 Tarsier2가 약간 불리하지만, 상당수의 경우에서 우세함을 보이며, Gemini 1.5 Pro 대비 Tarsier2는 상당한 우위를 점하고, GPT-40 대비해서는 근소하지만 우위를 차지하는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Human side-by-side evaluation results of Tarsier2 versus other models.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | Live-action | Animation | Stock | YouTube | Shorts | Overall |
|---|---|---|---|---|---|---|
| *Proprietary models* |  |  |  |  |  |  |
| GPT-4V [5] | 34.8/39.2/31.3 | 27.4/31.9/24.0 | 40.7/46.7/36.1 | 33.8/40.1/29.2 | 34.8/46.1/28.0 | 34.4/40.8/29.7 |
| GPT-4o [41] | 39.8/42.1/37.8 | 35.8/39.1/33.1 | 44.0/46.6/41.7 | 35.9/41.5/31.7 | 39.9/47.9/34.2 | 39.2/43.4/35.7 |
| Gemini-1.5-Flash [102] | 34.8/36.4/33.3 | 29.2/32.5/26.5 | 39.4/39.7/39.1 | 34.3/38.6/30.9 | 35.6/42.4/30.7 | 34.8/37.9/32.1 |
| Gemini-1.5-Pro [102] | 36.4/36.4/36.4 | 30.7/31.8/29.7 | 42.2/40.7/43.8 | 34.0/36.7/31.6 | 37.0/42.4/32.7 | 36.2/37.6/34.8 |
| *Open-source models (>10B)* |  |  |  |  |  |  |
| PLLaVA-34B [114] | 29.3/34.9/25.2 | 20.9/32.0/15.6 | 35.1/42.5/29.9 | 28.9/40.8/22.3 | 25.6/41.9/18.4 | 28.2/38.4/22.3 |
| VideoLLaMA2-72B [23] | 27.3/29.3/25.6 | 19.7/21.7/18.1 | 33.9/37.0/31.3 | 27.7/33.0/23.8 | 26.5/33.1/22.1 | 27.1/30.8/24.2 |
| LLaVA-OV-72B [53] | 31.7/32.8/30.7 | 27.7/30.6/25.2 | 38.0/39.6/36.6 | 34.1/34.7/33.5 | 33.8/41.8/28.4 | 33.2/35.9/30.9 |
| LLaVA-Video-72B [127] | 33.5/36.3/31.1 | 28.6/31.7/26.1 | 39.3/41.1/37.6 | 32.8/34.7/31.1 | 35.7/42.8/30.6 | 34.0/37.3/31.3 |
| Qwen2-VL-72B [106] | 32.1/33.7/30.6 | 27.6/32.6/23.9 | 41.1/41.2/41.1 | 32.0/38.1/27.7 | 32.1/41.0/26.4 | 33.2/37.3/29.9 |
| InternVL2.5-78B [20] | 25.3/31.5/21.1 | 21.8/28.8/17.6 | 33.5/38.1/29.9 | 31.0/38.5/25.9 | 31.1/41.7/24.8 | 28.6/35.7/23.9 |
| Tarsier-34B [105] | 38.5/39.6/37.5 | 32.2/35.8/29.2 | 41.7/46.4/37.8 | 34.5/41.1/29.7 | 34.0/44.1/27.7 | 36.3/41.4/32.4 |
| *Open-source models (<10B)* |  |  |  |  |  |  |
| Video-LLaVA-7B [61] | 19.4/24.3/16.2 | 15.3/21.2/11.9 | 27.0/33.5/22.7 | 21.2/31.9/15.8 | 18.5/29.4/13.5 | 20.4/28.1/16.0 |
| VideoLLaMA2-7B [23] | 25.1/28.7/22.2 | 20.4/25.5/17.0 | 32.6/35.5/30.2 | 27.5/33.5/23.4 | 24.5/34.1/19.2 | 26.2/31.5/22.4 |
| LLaVA-OV-7B [53] | 31.2/33.2/29.3 | 26.8/29.0/25.0 | 38.1/39.1/37.1 | 30.6/32.1/29.2 | 31.4/38.3/26.6 | 31.7/34.3/29.4 |
| LLaVA-Video-7B [127] | 31.4/35.2/28.4 | 27.6/32.9/23.8 | 36.7/39.7/34.1 | 33.0/39.5/28.3 | 33.4/42.5/27.5 | 32.5/37.9/28.4 |
| Qwen2-VL-7B [106] | 27.7/32.5/24.2 | 22.2/28.0/18.4 | 37.0/36.1/38.0 | 30.7/35.5/27.0 | 29.1/37.6/23.8 | 29.6/33.9/26.3 |
| InternVL2.5-8B [20] | 26.6/32.0/22.8 | 21.3/28.9/16.9 | 32.7/37.2/29.1 | 27.9/35.4/23.0 | 28.9/39.9/22.7 | 27.6/34.7/22.9 |
| Tarsier-7B [105] | 36.6/38.5/34.8 | 29.3/34.6/25.5 | 39.6/44.7/35.5 | 33.0/39.2/28.4 | 33.6/44.6/26.9 | 34.6/40.3/30.2 |
| Tarsier2-7B | 44.4/41.9/47.3 | 39.3/39.5/39.1 | 45.7/45.4/46.0 | 36.0/38.4/33.9 | 43.7/48.9/39.4 | 42.0/42.8/41.1 |{{< /table-caption >}}
> 🔼 표 2는 E.T. Bench-Captioning 벤치마크에 대한 평가 결과를 보여줍니다. 회색으로 표시된 결과는 하위 집합에 대해 테스트되었음을 나타냅니다. † 기호는 모델이 E.T. Instruct 164K 데이터셋으로 미세 조정되었음을 나타냅니다. 모든 결과는 공식 벤치마크에서 전사되었지만, LLaVA-OV, LLaVA-Video 및 Qwen2-VL에 대한 결과는 공식 체크포인트와 추론 코드를 사용하여 저자들이 직접 평가한 것입니다. 표는 다양한 모델들의 DVCF1, DVCSim, SLCF1, SLCSim, AvgF1, AvgSim 성능 지표를 비교 분석하여 각 모델의 비디오 캡션 생성 능력을 종합적으로 평가합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Evaluation results on E.T. Bench-Captioning. Results marked in gray are tested on a subset. ††{\dagger}† denotes the model is fine-tuned on E.T. Instruct 164K. All results are transcribed from the official benchmark, except for LLaVA-OV, LLaVA-Video and Qwen2-VL, which are our evaluation using the official checkpoint and inference code.
> </details>

{{< table-caption >}}
| Model | DVC<sub>F1</sub> | DVC<sub>Sim</sub> | SLC<sub>F1</sub> | SLC<sub>Sim</sub> | Avg<sub>F1</sub> | Avg<sub>Sim</sub> |
|---|---|---|---|---|---|---|
| *Proprietary models* |  |  |  |  |  |  |
| GPT-4V [5] | <span style="color:#BFBFBF;">16.1</span> | <span style="color:#BFBFBF;">19.4</span> | <span style="color:#BFBFBF;">21.9</span> | <span style="color:#BFBFBF;">13.5</span> | <span style="color:#BFBFBF;">19.0</span> | <span style="color:#BFBFBF;">16.4</span> |
| GPT-4o [41] | <span style="color:#BFBFBF;">46.9</span> | <span style="color:#BFBFBF;">22.3</span> | <span style="color:#BFBFBF;">23.1</span> | <span style="color:#BFBFBF;">14.9</span> | <span style="color:#BFBFBF;">35.0</span> | <span style="color:#BFBFBF;">18.6</span> |
| Gemini-1.5-Flash [102] | <span style="color:#BFBFBF;">31.6</span> | <span style="color:#BFBFBF;">14.9</span> | <span style="color:#BFBFBF;">16.5</span> | <span style="color:#BFBFBF;">13.3</span> | <span style="color:#BFBFBF;">24.1</span> | <span style="color:#BFBFBF;">14.1</span> |
| Gemini-1.5-Pro [102] | <span style="color:#BFBFBF;">24.0</span> | <span style="color:#BFBFBF;">17.5</span> | <span style="color:#BFBFBF;">5.8</span> | <span style="color:#BFBFBF;">9.8</span> | <span style="color:#BFBFBF;">14.9</span> | <span style="color:#BFBFBF;">13.7</span> |
| *Open-source models (>10B)* |  |  |  |  |  |  |
| PLLaVA-34B [114] | 13.3 | 10.6 | 9.7 | 11.8 | 11.5 | 11.2 |
| LLaVA-OV-72B [53] | 41.9 | 16.3 | 25.6 | 13.9 | 33.8 | 15.1 |
| LLaVA-Video-72B [127] | 37.0 | 15.7 | 20.4 | 13.5 | 28.7 | 14.6 |
| Qwen2-VL-72B [106] | 15.3 | 13.9 | 11.0 | 12.8 | 13.2 | 13.4 |
| *Open-source models (≤10B)* |  |  |  |  |  |  |
| VideoLLaMA2-7B [23] | 0.6 | 14.5 | 0.0 | 15.2 | 0.3 | 14.8 |
| Video-LLaVA-7B [61] | 28.0 | 15.0 | 0.9 | 8.3 | 14.4 | 11.7 |
| LLaVA-OV-7B [53] | 22.0 | 15.1 | 9.5 | 10.6 | 15.8 | 12.8 |
| LLaVA-Video-7B [127] | 20.6 | 14.7 | 6.5 | 13.4 | 13.6 | 14.1 |
| E.T. Chat [67]<sup>†</sup> | 38.4 | 19.7 | 24.4 | 14.6 | 31.4 | 17.1 |
| Qwen2-VL-7B [106]<sup>†</sup> | 44.3 | 25.3 | 25.7 | 15.6 | 35.0 | 20.4 |
| Tarsier-7B [105]<sup>†</sup> | 42.8 | 19.1 | 23.7 | 15.2 | 33.2 | 17.1 |
| Tarsier2-7B<sup>†</sup> | 46.5 | 28.8 | 24.6 | 16.4 | 35.5 | 22.6 |{{< /table-caption >}}
> 🔼 표 3은 짧은 비디오 질문 답변 벤치마크에 대한 평가 결과를 보여줍니다. 이 표에는 다양한 벤치마크(MVBench, PerceptionTest, TVBench, TOMATO, Vinoground, TempCompass)에서 Tarsier2-7B 모델의 성능을 다른 최첨단 모델들과 비교하여 보여줍니다. 각 벤치마크의 하위 작업에 대한 정확도 점수와 더불어 전체 평균 점수도 제시합니다.  * 표시는 해당 모델의 학습 데이터에 벤치마크의 학습 데이터가 포함되었음을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Evaluation results on short video question answering benchmarks. * indicates that the training set has been observed in the training data mixture.
> </details>

{{< table-caption >}}
| Model | MVBench [57] | PerceptionTest [86] | TVBench [25] | TOMATO [94] | Vinoground [123] | TempCompass [69] |
|---|---|---|---|---|---|---|
| **Model** | test | val | test | test | Text/Video/Group | mc/yn/cm/cg |
| *Proprietary models* |  |  |  |  |  |  |
| GPT-4o [41] | 57.5 | - | 39.6 | 37.7 | 54.0/38.2/24.6 | 71.0/73.7/80.8/70.8 |
| Gemini-1.5-Pro [102] | - | - | 46.5 | 36.1 | 35.8/22.6/10.2 | 63.9/70.3/77.5/57.9 |
| *Open-source models (>10B)* |  |  |  |  |  |  |
| LLaVA-OV-72B [53] | 59.4 | 66.9 | 45.9 | 28.6 | 48.4/35.2/21.8 | 67.6/72.6/78.2/52.6 |
| LLaVA-Video-72B [127] | 64.1 | 74.3* | 50.0 | 28.2 | 52.0/35.6/20.8 | 69.9/73.0/80.9/54.4 |
| Qwen2-VL-72B [106] | 73.6 | 66.5 | 52.7 | 37.9 | 50.4/32.6/17.4 | 76.0/75.9/84.6/58.6 |
| Tarsier-34B [105] | 67.6 | 60.4 | 53.8 | 34.3 | 37.8/32.0/15.0 | 69.8/74.0/73.0/60.9 |
| *Open-source models (≤10B)* |  |  |  |  |  |  |
| LLaVA-OV-7B [53] | 56.7 | 57.1 | 45.6 | 25.5 | 41.6/29.4/14.6 | 64.8/69.7/73.8/49.9 |
| LLaVA-Video-7B [127] | 58.6 | 67.9* | 45.6 | 24.9 | 36.8/29.0/12.8 | 56.3/68.7/76.8/53.0 |
| Qwen2-VL-7B [106] | 67.0 | - | 43.8 | 31.5 | 40.0/23.4/12.4 | 68.5/72.8/77.3/54.2 |
| Tarsier-7B [105] | 62.6 | 53.9 | 45.8 | 28.6 | 29.8/22.2/8.6 | 58.7/58.0/54.2/55.3 |
| Previous SOTA | 72.0 [20] | 70.0* [72] | 51.6 [124] | 31.5 [106] | 41.6/29.4/14.6 [52] | 68.5/72.8/77.3/54.2 [106] |
| Tarsier2-7B | 71.5 | 71.6* | 54.7 | 42.0 | 65.8/38.0/28.8 | 75.3/75.1/80.6/66.6 |{{< /table-caption >}}
> 🔼 표 4는 장시간 비디오 질문 응답 벤치마크에 대한 Tarsier2의 평가 결과를 보여줍니다. Tarsier2 평가 시 각 벤치마크에서 사용된 프레임 수를 함께 제시합니다.  표에는 경쟁 모델들과 비교하여 Tarsier2의 성능을 다양한 지표(정확도, 평균 정확도 등)로 나타내어 장시간 비디오 이해 능력을 평가합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Evaluation results on long-video question answering benchmarks. We list the number of frames used for each benchmark during evaluating Tarsier2.
> </details>

{{< table-caption >}}
| Model | Video-MME<sup>[31]</sup> | LongVideoBench<sup>[110]</sup> | TemporalBench<sup>[12]</sup> | MLVU<sup>[128]</sup> | MMBench-Video<sup>[30]</sup> |
|---|---|---|---|---|---| 
|  | w/o subs | val | Binary Accuracy | M-Avg | val |
|---|---|---|---|---|---| 
| *Proprietary models* |  |  |  |  |  |
| GPT-4o<sup>[41]</sup> | 71.9 | 66.7 | 73.2 | 64.6 | 1.87 |
| Gemini-1.5-Pro<sup>[102]</sup> | 75.0 | 64.0 | 66.4 | - | 1.30 |
| *Open-source models (>10B)* |  |  |  |  |  |
| VILA-1.5-40B<sup>[62]</sup> | 60.1 | - | - | 56.7 | 1.61 |
| LLaVA-Video-72B<sup>[127]</sup> | 70.5 | 61.9 | 72.4 | 74.4 | 1.71 |
| Qwen2-VL-72B<sup>[106]</sup> | 71.2 | - | 70.2 | - | 1.70 |
| InternVL2.5-78B<sup>[20]</sup> | 72.1 | 63.6 | - | 75.7 | 1.97 |
| Tarsier-34B<sup>[105]</sup> | 52.3 | 54.2 | 66.7 | 58.2 | 1.46 |
| *Open-source models (≤10B)* |  |  |  |  |  |
| LLaVA-Video-7B<sup>[127]</sup> | 63.3 | 58.2 | 63.6 | 70.8 | 1.60 |
| Qwen2-VL-7B<sup>[106]</sup> | 63.3 | 55.6 | 62.0 | - | 1.44 |
| InternVL2.5-8B<sup>[20]</sup> | 64.2 | 60.0 | - | 68.9 | 1.68 |
| Tarsier-7B<sup>[105]</sup> | 42.2 | 39.8 | 56.9 | 49.3 | - |
| Previous SOTA | 64.2<sup>[70]</sup> | 60.0<sup>[20]</sup> | 63.6<sup>[127]</sup> | 70.9<sup>[130]</sup> | 1.70<sup>[119]</sup> |
| Tarsier2-7B | 64.5 (128f) | 58.6 (128f) | 65.3 (128f) | 67.9 (256f) | 1.82 (128f) |{{< /table-caption >}}
> 🔼 표 5는 비디오 환각 벤치마크에 대한 평가 결과를 보여줍니다.  두 가지 환각 벤치마크인 VideoHallucer와 EventHallusion에 대한 결과가 제시됩니다.  각 벤치마크는 여러 하위 작업(예: Yes/No QA, 설명 생성)으로 구성되며,  각 작업에 대한 정밀도, 재현율, F1 점수와 같은 다양한 지표가 제공됩니다.  비디오 설명 생성의 환각 여부를 직접적으로 평가하는 작업도 포함되어 있습니다.  표에는 독점 모델(GPT-4, Gemini)과 오픈소스 모델(LLaVA, Tarsier 등)의 결과가 제시되어 있으며, Tarsier2 모델의 성능이 다른 모델들과 비교되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Evaluation results on hallucination benchmarks.
> </details>

{{< table-caption >}}
| Model | VideoHallucer [109] | EventHallusion [122] | EventHallusion [122] |
|---|---|---|---|
|  | Yes/No QA | Yes/No QA | Desc GPT |
|  | Basic/Hallucinated/Overall | Entire/Interleave/Misleading/Overall | Entire/Interleave/Misleading/Overall |
| *Proprietary models* |  |  |  |
| GPT-4o [41] | 75.1/74.2/53.3 | 65.8/90.7/92.2/84.1 | 34.9/54.9/83.2/56.2 |
| Gemini-1.5-Pro [102] | 83.6/42.3/37.8 | 70.2/77.7/96.1/80.2 | 38.5/40.9/80.0/49.6 |
| *Open-Source models (>10B)* |  |  |  |
| Qwen2-VL-72B [106] | 87.1/79.4/70.2 | 33.3/77.7/56.4/60.0 | 16.5/25.4/70.2/33.6 |
| LLaVA-OV-72B [53] | 88.3/62.6/55.2 | 47.4/26.9/90.1/48.3 | 24.8/34.7/71.3/40.7 |
| LLaVA-Video-72B [127] | 88.2/73.5/64.6 | 57.9/11.9/96.0/45.6 | 32.1/35.8/75.5/44.2 |
| InternVL2.5-78B [20] | 82.5/82.5/67.8 | 57.9/67.9/88.2/70.2 | 45.0/43.0/76.8/51.6 |
| Tarsier-34B [105] | 84.8/80.0/67.7 | 49.1/92.7/69.6/74.8 | 38.5/40.4/83.2/50.1 |
| *Open-Source models (≤10B)* |  |  |  |
| LLaVA-OV-7B [53] | 81.1/69.6/53.8 | 46.5/67.4/86.1/66.2 | 22.0/26.4/73.4/36.4 |
| LLaVA-Video-7B [127] | 82.4/70.6/56.0 | 61.4/48.7/96.0/64.0 | 27.5/32.6/75.5/41.4 |
| Qwen2-VL-7B [106] | 85.0/70.8/59.3 | 35.1/94.3/57.4/68.6 | 14.7/16.1/67.0/27.8 |
| InternVL2.5-8B [20] | 72.7/78.3/53.6 | 46.5/69.2/90.2/68.2 | 23.9/20.7/60.0/31.0 |
| Tarsier-7B [105] | 76.4/60.8/41.4 | 43.9/82.4/79.4/70.9 | 35.8/29.5/72.6/41.6 |
| Tarsier2-7B | 86.5/78.3/67.0 | 60.5/93.3/95.1/84.6 | 54.6/53.1/93.7/63.3 |{{< /table-caption >}}
> 🔼 표 6은 E.T. Bench-Grounding 벤치마크에 대한 평가 결과를 보여줍니다. 이 표는 다양한 비디오 지상화(grounding) 작업에 대한 여러 모델의 성능을 비교 분석합니다. 회색으로 표시된 결과는 일부 데이터셋에 대해서만 테스트된 결과임을 나타냅니다. † 기호는 모델이 E.T. Instruct 164K 데이터셋을 사용하여 미세 조정되었음을 의미합니다.  표에는 TVGF1, EPMF1, TALF1, EVSF1, VHDF1 및 MeanF1 등 여러 지표가 포함되어 있으며, 각 지표는 비디오 지상화 작업의 다양한 측면을 평가합니다. 각 모델의 성능을 비교하여 어떤 모델이 특정 작업에서 가장 우수한 성능을 보이는지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Evaluation results on E.T. Bench-Grounding. Results marked in gray are tested on a subset. ††{\dagger}† denotes the model is fine-tuned on E.T. Instruct 164K.
> </details>

{{< table-caption >}}
| Model | TVG<sub>F1</sub> | EPM<sub>F1</sub> | TAL<sub>F1</sub> | EVS<sub>F1</sub> | VHD<sub>F1</sub> | Mean<sub>F1</sub> |
|---|---|---|---|---|---|---|
| *Proprietary models* |
| GPT-4V [5] | <span style="color:#BFBFBF;">27.0</span> | <span style="color:#BFBFBF;">1.8</span> | <span style="color:#BFBFBF;">18.0</span> | <span style="color:#BFBFBF;">28.6</span> | <span style="color:#BFBFBF;">55.1</span> | <span style="color:#BFBFBF;">26.1</span> |
| GPT-4o [41] | <span style="color:#BFBFBF;">40.4</span> | <span style="color:#BFBFBF;">4.5</span> | <span style="color:#BFBFBF;">20.0</span> | <span style="color:#BFBFBF;">17.6</span> | <span style="color:#BFBFBF;">56.9</span> | <span style="color:#BFBFBF;">27.9</span> |
| Gemini-1.5-Flash [102] | <span style="color:#BFBFBF;">43.9</span> | <span style="color:#BFBFBF;">5.4</span> | <span style="color:#BFBFBF;">27.0</span> | <span style="color:#BFBFBF;">5.4</span> | <span style="color:#BFBFBF;">60.8</span> | <span style="color:#BFBFBF;">28.5</span> |
| Gemini-1.5-Pro [102] | <span style="color:#BFBFBF;">43.1</span> | <span style="color:#BFBFBF;">6.2</span> | <span style="color:#BFBFBF;">33.8</span> | <span style="color:#BFBFBF;">7.9</span> | <span style="color:#BFBFBF;">47.0</span> | <span style="color:#BFBFBF;">27.6</span> |
| *Open-source models (&lt;10B)* |
| LITA [39] | 22.2 | 4.6 | 18.0 | 29.7 | 23.9 | 19.7 |
| VTG-LLM [37] | 15.9 | 3.7 | 14.4 | 26.8 | 48.2 | 21.8 |
| TimeChat [91]<sup>†</sup> | - | - | - | - | - | 24.3 |
| E.T. Chat [67]<sup>†</sup> | 38.6 | 10.2 | 30.8 | 25.4 | 62.5 | 33.5 |
| Tarsier-7B [105]<sup>†</sup> | 39.6 | 9.0 | 25.0 | 25.4 | 47.6 | 30.9 |
| Qwen2-VL-7B [106]<sup>†</sup> | 39.7 | 7.0 | 26.9 | 17.1 | 66.9 | 33.5 |
| Tarsier2-7B<sup>†</sup> | 38.4 | 11.0 | 31.8 | 19.4 | 66.8 | 35.5 |{{< /table-caption >}}
> 🔼 표 7은 EgoTaskQA, RoboVQA, OpenEQA 세 가지 임베디드 질의응답 과제에 대한 Tarsier2 모델의 평가 결과를 보여줍니다.  각 과제는 실제 로봇 시나리오를 기반으로 하며, 모델의 실제 환경 이해 능력을 평가합니다.  결과는 EgoTaskQA의 경우 정확도 일치율(Exact Match Accuracy), RoboVQA의 경우 BLEU 점수, OpenEQA의 경우 GPT-4를 사용한 정확도 점수로 나타냅니다. 이 표는 Tarsier2가 일반적인 대규모 언어 모델과 전문 모델 모두를 능가하는 성능을 보여줌을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Evaluation results on embodied question-answering tasks, including EgoTaskQA, RoboVQA and OpenEQA.
> </details>

{{< table-caption >}}
| Model | EgoTaskQA Exact Match |
|---|---| 
| Human | 80.0 |
| HCRN [50] | 42.2 |
| GF [9] | 44.3 |
| EgoVLPv2 [88] | 46.3 |
| Tarsier2 | **77.5** |{{< /table-caption >}}
> 🔼 표 8은 사전 훈련에 대한 ablation 연구 결과를 보여줍니다. Tarsier1-7B-Qwen은 기본 모델이 Qwen2-VL로 업그레이드되었지만 사전 훈련 데이터셋은 Tarsier1과 동일한 모델을 의미합니다. Tarsier2는 Qwen2-VL을 기반으로 사전 훈련 데이터셋이 Tarsier1의 1,300만 개에서 4,000만 개로 확장되어 훈련된 모델입니다. 이 표는 기본 모델, 사전 훈련 데이터셋 크기, 훈련 단계 등 여러 요소들이 모델 성능에 미치는 영향을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Results of the ablation study for pre-training. Tarsier1-7b-Qwen stands for the model where the base model is upgraded to Qwen2-VL, while the pre-training dataset remains the same as Tarsier1. Tarsier2 is trained from Qwen2-VL with an expanded pre-training dataset, growing from 13 million in Tarsier1 to 40 million samples.
> </details>

{{< table-caption >}}
| Model | RoboVQA (BLEU-1/2/3/4)| 
|---|---| 
| LLaMA-AdapterV2 [33] | 27.8/16.0/10.9/8.1 | 
| LLaVA-OV-7B [53] | 38.1/33.6/31.8/31.0 | 
| RoboMamba [66] | 54.9/44.2/39.5/36.3 | 
| MLCD [3] | 73.2/66.4/60.6/56.6 | 
| Tarsier2 | 77.1/67.4/61.5/56.8 |{{< /table-caption >}}
> 🔼 표 9는 SFT(Supervised Fine-Tuning) 단계에서 시간적 기반 데이터 세트의 영향을 분석한 결과를 보여줍니다.  Tarsier2-7B-SFT는 SFT 단계를 거친 모델이고, w/o SFT는 사전 학습만 거친 모델이며, w/o grounding은 시간적 기반 정보 없이 미세 조정된 모델을 의미합니다.  표에는 캡션 생성, 짧은 비디오 질문 답변, 긴 비디오 질문 답변, 그리고 환각(hallucination) 테스트의 성능을 DREAM-1K, TempCompass-cg, Vinoground-Text 등 다양한 벤치마크 기준으로 정량적으로 비교 분석한 결과가 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Ablation study of temporal grounding dataset during the SFT phase. Tarsier2-7B-SFT refers to the model after the SFT phase. w/o SFT refers to the model after pre-training; w/o grounding refers to the model fine-tinued without grounding information.
> </details>

{{< table-caption >}}
| Model | OpenEQA |
|---|---| 
| **Human** | 86.8 |
| GPT-4V<sup>[5]</sup> | 55.3 |
| Gemini-1.5-Pro<sup>[102]</sup> | 44.9 |
| MLCD<sup>[3]</sup> | 48.8 |
| Tarsier2 | **58.7** |{{< /table-caption >}}
> 🔼 표 10은 DPO(Direct Preference Optimization) 훈련 단계에서 음성 샘플링(Negative Sampling)과 선호도 데이터 필터링(Preference Filtering) 전략을 제거했을 때의 영향을 보여주는 추가 실험 결과를 보여줍니다.  각 열은 DREAM-1K, TempCompass-cg, Vinoground-Text, Short Video QA, Long Video QA, Hallucination의 성능 지표를 나타냅니다. 각 행은 Tarsier2-7B 모델의 기준 설정과 음성 샘플링 제거, 선호도 데이터 필터링 제거, DPO 제거 등의 변형 설정에 대한 결과를 보여줍니다.  이를 통해 각 구성 요소의 성능에 대한 기여도를 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Ablation study for DPO training phase, negative sampling (NS) and preference data filtering (PF) strategies.
> </details>

{{< table-caption >}}
| Model | DREAM-1K | TempCompass-cg | Vinoground-Text | Short | Long | Hallucination |
|---|---|---|---|---|---|---|
| Tarsier1-7B | 34.6 | 55.3 | 29.8 | 45.6 | 46.3 | 56.3 |
| Tarsier1-7B-Qwen <br> _upgrading model_ | 38.4 (↑3.8) | 59.3 (↑4.0) | 48.6 (↑18.8) | 52.4 (↑6.8) | 57.6 (↑11.3) | 62.1 (↑5.8) |
| Tarsier2-7B <br> _upgrading model_ + _data_ | 40.8 (↑6.2) | 60.1 (↑4.8) | 60.2 (↑30.4) | 55.3 (↑9.7) | 64.1 (↑17.8) | 63.5 (↑7.2) |{{< /table-caption >}}
> 🔼 표 11은 Tarsier2-Recap-585K 데이터셋을 사용하여 모델을 미세 조정한 결과와 동일한 비디오를 사용하여 원래 레이블을 목표 출력으로 사용하여 모델을 미세 조정한 결과를 보여줍니다.  'Recaption FT'는 Tarsier2-Recap-585K 데이터셋에 대해 모델을 미세 조정한 것을 나타내고, 'Original FT'는 Tarsier2-Recap-585K와 동일한 비디오를 사용하지만 원래 레이블을 목표 출력으로 사용하여 모델을 미세 조정한 것을 나타냅니다.  즉,  원본 자막을 사용하여 재학습한 경우와 새로운 자막으로 재학습한 경우의 성능 비교표입니다.
> <details>
> <summary>read the caption</summary>
> Table 11: The experimental results of recaptioning. “Recaption FT” represents fine-tune the model on the Tarsier2-Recap-585K dataset. “Original FT” represents fine-tune the model with the same videos as Tarsier2-Recap-585K but taking their original labels as target output.
> </details>

{{< table-caption >}}
| Model | Caption | Caption | Caption | Video QA | Video QA | Hallucination |
|---|---|---|---|---|---|---|
| **Model** | **DREAM-1K** | **TempCompass-cg** | **Vinoground-Text** | **Short** | **Long** | **Hallucination** |
| Tarsier2-7B-SFT | 40.8 | 60.1 | 60.2 | 56.2 | 63.2 | 71.9 |
| *w/o SFT* | 35.2 (↓5.6) | 50.5 (↓9.6) | 57.2 (↓3.0) | 55.3 (↓0.9) | 64.1 (↑0.9) | 63.5 (↓8.4) |
| *w/o grounding* | 37.4 (↓3.4) | 50.2 (↓9.9) | 60.6 (↑0.4) | 55.9 (↓0.3) | 61.9 (↓1.3) | 68.6 (↓3.3) |{{< /table-caption >}}
> 🔼 Tarsier2 모델의 학습 하이퍼파라미터를 보여주는 표입니다.  전체 학습 과정(Pre-training, SFT-1, SFT-2, DPO)에 사용된 Optimizer, 학습률, 배치 크기, 가중치 감소, 드롭아웃 비율, 최대 픽셀 수, 비디오당 프레임 수, 수치적 정밀도 등의 하이퍼파라미터 값을 상세히 제시하고 있습니다.  각 단계별로 다른 설정값을 사용하여 모델 학습의 세부적인 내용을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 12: Training hyper-parameters of Tarsier2
> </details>

{{< table-caption >}}
| Model | Caption DREAM-1K | Caption TempCompass-cg | Caption Vinoground-Text | Video QA Short | Video QA Long | Hallucination |
|---|---|---|---|---|---|---|
| Tarsier2-7B | 42.0 | 66.6 | 65.8 | 56.1 | 62.8 | 74.0 |
| _w/o DPO_ | 40.8 (↓1.2) | 62.1 (↓6.5) | 60.6 (↓5.6) | 56.2 (↑0.1) | 63.2 (↑0.4) | 71.9 (↓2.1) |
| _w/o NS_ | 41.5 (↓0.5) | 61.1 (↓5.5) | 59.8 (↓6.0) | 56.1 (↓0.0) | 62.8 (↓0.0) | 72.9 (↓1.1) |
| _w/o PF_ | 40.5 (↓1.5) | 65.1 (↓1.5) | 67.6 (↑1.8) | 56.0 (↓0.1) | 62.3 (↓0.5) | 74.2 (↑0.2) |{{< /table-caption >}}
> 🔼 Tarsier2 사전 학습에 사용된 데이터셋의 종류와 크기를 보여주는 표입니다.  표에는 비디오 캡션, 액션 인식, 비디오 질의응답, 그라운딩, 비디오 자기 지도 학습, 이미지 이해, 텍스트 생성 등 다양한 작업에 사용된 데이터셋들이 포함되어 있습니다.  각 데이터셋의 크기는 괄호 안에 표시되어 있으며, †† 기호는 자체적으로 수집한 데이터셋임을 나타냅니다. 이 표는 Tarsier2 모델의 사전 학습 과정에서 어떤 종류와 양의 데이터가 사용되었는지 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 13: Datasets and their sizes used in Tarsier2 pre-training. ††\dagger† indicates in-house datasets.
> </details>

{{< table-caption >}}
| Model | Caption DREAM-1K | Caption TempCompass-cg | Caption Vinoground-Text | Video QA Short | Video QA Long | Hallucination |
|---|---|---|---|---|---|---|
| Qwen2-VL-7B [106] | 31.2 | 54.2 | 40.0 | 49.4 | 60.3 | 51.9 |
| Qwen2-VL-7B [106] + *Original FT* | 35.2 (↑4.0) | 49.9 (↓4.3) | 39.0 (↓1.0) | 46.9 (↓2.5) | 55.4 (↓4.9) | 43.0 (↓8.9) |
| Qwen2-VL-7B [106] + *Recaption FT* | 39.5 (↑8.3) | 67.7 (↑13.5) | 55.0 (↑15.0) | 52.5 (↑3.1) | 56.8 (↓3.5) | 68.5 (↑16.6) |{{< /table-caption >}}
> 🔼 표 14는 사전 훈련에 대한 ablation study 결과를 보여줍니다. 캡션 작업의 경우 SFT 단계 이후의 결과가 보고되고, 다른 작업의 경우 사전 훈련 단계 이후의 결과가 보고됩니다.  표에는 캡션 생성, 짧은 비디오 QA, 긴 비디오 QA, 환각 테스트 세 가지 능력 범주에 대한 정량적 결과가 포함되어 있습니다. 각 범주에 대해 여러 개의 벤치마크에 대한 결과가 제시되고, Tarsier1-7B, Tarsier1-7B-Qwen(모델 업그레이드), Tarsier2-7B(데이터 및 모델 업그레이드) 세 가지 모델의 성능을 비교 분석합니다.  이를 통해 사전 훈련 데이터 크기 및 기본 모델의 영향을 명확하게 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 14: Detailed results of the ablation study for pre-training. For the captioning task, results are reported after the SFT stage. For other tasks, results are reported after the pre-training stage.
> </details>

{{< table-caption >}}
| Configuration | Pre-training | SFT-1 | SFT-2 | DPO |
|---|---|---|---|---|
| VLM init. | Qwen2-VL-7B | Tarsier2-Pre-trian | Tarsier2-SFT-1 | Tarsier2-SFT-2 |
| Optimizer name | AdamW | AdamW | AdamW | AdamW |
| Optimizer \$\beta_{1}$ | 0.9 | 0.9 | 0.9 | 0.9 |
| Optimizer \$\beta_{2}$ | 0.999 | 0.999 | 0.999 | 0.999 |
| Optimizer eps | 1e^{-6} | 1e^{-6} | 1e^{-6} | 1e^{-6} |
| Learning rate | 2e^{-5} | 2e^{-5} | 2e^{-6} | 1e^{-6} |
| Learning rate schedule | cosine | cosine | cosine | cosine |
| Training steps | 200,000 | 5,000 | 5,000 | 1,000 |
| Warm-up steps | 1,000 | 250 | 250 | 100 |
| Weight decay | 0.01 | 0.01 | 0.01 | 0.01 |
| Gradient clip | 1.0 | 1.0 | 1.0 | 1.0 |
| Dropout rate | 0.0 | 0.0 | 0.0 | 0.0 |
| Global batch size | 384 | 64 | 64 | 64 |
| Max pixels | 460,800 | 460,800 | 460,800 | 460,800 |
| Frames per video | [8,128] | 16 | 16 | 16 |
| Numerical precision | bfloat16 | bfloat16 | bfloat16 | bfloat16 |{{< /table-caption >}}
> 🔼 표 15는 SFT(Supervised Fine-Tuning) 단계의 ablation study 결과를 보여줍니다.  SFT 단계에서 fine-grained temporal grounding 데이터셋을 사용했을 때와 사용하지 않았을 때의 성능 차이를 보여주는 여러 비디오 이해 작업(캡션 생성, 짧은 비디오 질의응답, 긴 비디오 질의응답, 환각)에 대한 정량적 결과를 제시합니다.  세 가지 모델(Tarsier2-7B-SFT, grounding 정보 없이 fine-tuning된 모델, SFT 단계 없이 pre-training만 진행된 모델)을 비교하여 fine-grained temporal grounding의 중요성을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Table 15: Detailed results of the ablation study for SFT.
> </details>

{{< table-caption >}}
| Task                     | Dataset             | # Samples | Notes                                   |
|--------------------------|----------------------|------------|----------------------------------------|
| **Video Captioning**      |                       |            |                                        |
| WebVid                    | [10]                 | 2.9M       |                                        |
| LSMDC                     | [92]                 | 109K       |                                        |
| TGIF                      | [59]                 | 105K       |                                        |
| ActivityNet               | [47]                 | 38K        |                                        |
| Charades                  | [97]                 | 16K        |                                        |
| Charades-Ego              | [96]                 | 6K         |                                        |
| YouCook2                  | [129]                | 9K         |                                        |
| TACoS                     | [90]                 | 18K        |                                        |
| Ego4D                     | [35]                 | 1.1M       |                                        |
| Spoken Moments            | [82]                 | 493K       |                                        |
| Multi-Moments             | [83]                 | 997K       |                                        |
| TREC-VTT                  | [7]                  | 64K        |                                        |
| ShareGPT-4o-video        | [26]                 | 2K         |                                        |
| MovieStory101            | [38]                 | 11K        |                                        |
| GPT4o-labeled Caption†   |                       | 2.5M       |                                        |
| Human-labeled Caption†   |                       | 145K       |                                        |
| Film&TV Commentary†      |                       | 11.5M      |                                        |
| **Action Recognition**    |                       |            |                                        |
| HMDB                      | [49]                 | 5.8K       |                                        |
| COIN                      | [101]                | 10K        |                                        |
| SSV2                      | [34]                 | 169K       |                                        |
| Kinetics-700             | [13]                 | 537K       |                                        |
| FineAction                | [68]                 | 82K        |                                        |
| RareAct                   | [80]                 | 2K         |                                        |
| 20BN-jester              | [79]                 | 46K        |                                        |
| **Video QA**              |                       |            |                                        |
| CLEVRER                   | [120]                | 83K        |                                        |
| TGIF-QA                   | [43]                 | 72K        |                                        |
| EgoQA                     | [29]                 | 5K         |                                        |
| VideoInstruct             | [76]                 | 89K        |                                        |
| LLaVA-Video-178K         | [127]                | 165K       |                                        |
| M4-Instruct-video        | [52]                 | 255K       |                                        |
| GPT4o-labeled QA†        |                       | 16.2K      |                                        |
| **Grounding**             |                       |            |                                        |
| DiDeMo                    | [4]                  | 82K        |                                        |
| AVA                       | [36]                 | 28K        |                                        |
| E.T. Instruct 164K       | [67]                 | 147K       |                                        |
| Object Tracking†          |                       | 745K       |                                        |
| **Video Self-Supervised Training** |                       |            |                                        |
| Frame Order Prediction†    |                       | 825K       |                                        |
| **Intent Recognition**    |                       |            |                                        |
| Oops!                     | [28]                 | 15K        |                                        |
| **Multi-Image Understanding** |                       |            |                                        |
| VIST                      | [40]                 | 38K        |                                        |
| MMDU                      | [71]                 | 45K        |                                        |
| M4-Instruct-image        | [52]                 | 616K       |                                        |
| Image Retrival†           |                       | 533K       |                                        |
| **Single-Image Understanding** |                       |            |                                        |
| ShareGPT4V                | [15]                 | 95K        |                                        |
| LLaVA-1.5                | [64]                 | 643K       |                                        |
| ShareGPT-4o-image        | [26]                 | 57K        |                                        |
| MS COCO                   | [63]                 | 566K       |                                        |
| Flicker                   | [87]                 | 145K       |                                        |
| LLaVA-ReCap-CC3M         | [52]                 | 2.9M       |                                        |
| Visual Genome             | [48]                 | 759K       |                                        |
| SBU Captions              | [84]                 | 860K       |                                        |
| GPT4o-labeled Caption†   |                       | 1.13M      |                                        |
| **Image OCR**             |                       |            |                                        |
| RCTW-17                   | [95]                 | 8K         |                                        |
| LSVT                      | [98]                 | 430K       |                                        |
| ReCTS                     | [125]                | 20K        |                                        |
| Art                       | [11]                 | 5.6K       |                                        |
| COCOTextV2                | [103]                | 16K        |                                        |
| CORD-v2                   | [85]                 | 1K         |                                        |
| HierText                  | [73]                 | 10K        |                                        |
| MSRA-TD500                | [118]                | 465        |                                        |
| IC03                      | [74]                 | 499        |                                        |
| SynthDoG-en              | [46]                 | 100K       |                                        |
| SynthDoG-zh              | [46]                 | 100K       |                                        |
| **Text Generation**       |                       |            |                                        |
| OpenOrca                  | [60]                 | 995K       |                                        |
| ShareGPT                  | [24]                 | 80K        |                                        |{{< /table-caption >}}
> 🔼 표 16은 DPO(Direct Preference Optimization) 단계에 대한 ablation study 결과를 보여줍니다.  각 ablation 실험은 DPO 훈련에서 특정 요소(음성 샘플링, 선호도 필터링)를 제거하여 수행되었으며,  'Caption', 'Video QA', 'Hallucination' 세 가지 능력에 대한 영향을 정량적으로 평가합니다.  각 능력은 여러 하위 작업(예: DREAM-1K, TempCompass-cg, Vinoground-Text 등)의 평균 점수로 측정됩니다. 이를 통해 각 구성 요소가 모델 성능에 미치는 영향을 분석하고, DPO 전략의 효과를 자세히 이해할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 16: Detailed results of the ablation study for DPO.
> </details>

{{< table-caption >}}
| Capability | Benchmark | Tarsier1-7B | Tarsier1-7B-Qwen | Tarsier2-7B |
|---|---|---|---|---|
| Caption | DREAM-1K | 34.6/30.2/40.3 | 38.4/40.6/36.4 | 40.8/42.5/39.3 |
|  | TempCompass-cg | 55.3 | 59.3 | 60.1 |
|  | Vinoground-Text | 29.8 | 48.6 | 60.2 |
| Video QA Short | MVBench | 62.6 | 69.8 | 72.8 |
|  | TVBench | 45.8 | 51.0 | 53.5 |
|  | TOMATO | 28.6 | 36.5 | 39.5 |
| Video QA Long | Video-MME | 42.2 | 58.9 | 65.3 |
|  | LongVideoBench | 39.8 | 52.1 | 58.3 |
|  | TemporalBench | 56.9 | 61.9 | 68.7 |
| Hallucination | EventHallusion-Y/N | 70.9 | 75.6 | 77.8 |
|  | EventHallusion-Desc | 41.6 | 48.6 | 49.1 |{{< /table-caption >}}
> 🔼 표 17은 Tarsier2-Recap-585K 데이터셋을 사용한 재캡션 작업의 실험 결과를 보여줍니다.  Tarsier2-Recap-585K는 기존의 비디오 캡션 데이터셋에 두 가지 액션 인식 데이터셋을 추가하여 구성된 데이터셋입니다.  표는 재캡션 실험을 위해 원본 캡션을 사용하여 미세 조정한 모델과 Tarsier2-Recap-585K 데이터셋으로 미세 조정한 모델의 성능을 비교하여 DREAM-1K, TempCompass-cg, Vinoground-Text 와 같은 벤치마크에서의 성능을 F1 점수, 정밀도, 재현율, 정확도 등 다양한 지표를 통해 보여줍니다.  비디오 질의응답(Video QA)과 환각(Hallucination) 테스트 결과 또한 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 17: Detailed results of the recaptioning experiment.
> </details>

{{< table-caption >}}
| Capability | Benchmark | pre-train | Tarsier2-7B | SFT |
|---|---|---|---|---|
| Caption | DREAM-1K | 35.2/36.8/33.7 | 37.4/38.6/36.3 | 40.8/42.5/39.3 |
|  | TempCompass-cg | 50.5 | 50.2 | 60.1 |
|  | Vinoground-Text | 57.2 | 60.6 | 60.2 |
| Video QA Short | MVBench | 72.8 | 71.9 | 72.5 |
|  | TVBench | 53.5 | 54.5 | 54.2 |
|  | TOMATO | 39.5 | 41.3 | 41.9 |
| Video QA Long | Video-MME | 65.3 | 64.0 | 64.7 |
|  | LongVideoBench | 58.3 | 54.7 | 58.2 |
|  | TemporalBench | 68.7 | 66.9 | 66.6 |
| Hallucination | EventHallusion-Y/N | 77.8 | 80.1 | 84.4 |
|  | EventHallusion-Desc | 49.1 | 56.2 | 59.4 |{{< /table-caption >}}
> 🔼 Tarsier2-Recap-585K 데이터셋의 구성을 보여주는 표입니다. 원본 데이터셋의 분할 방식을 'Split' 열에 나타내고, 재캡션 작업을 위해 비디오 클립을 샘플링한 부분을 굵은 글씨체로 표시했습니다. 각 데이터셋의 원본 레이블 유형, 샘플링된 클립의 수, 평균 지속 시간, 전체 데이터셋에서 차지하는 비율 등을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 18: Data composition of Tarsier2-Recap-585K. The “Split” column lists the original dataset partitioning, and we use bold to mark the parts which we sampled the video clips from to conduct recaptioning.
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