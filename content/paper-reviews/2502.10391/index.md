---
title: "MM-RLHF: The Next Step Forward in Multimodal LLM Alignment"
summary: "MM-RLHF: 12만 개의 정교한 인간 주석이 달린 데이터셋과 새로운 정렬 알고리즘을 통해 다양한 모달리티의 대규모 언어 모델(MLLM) 성능을 크게 향상시킨 연구"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Vision-Language Models", "🏢 CASIA",]
showSummary: true
date: 2025-02-14
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.10391 {{< /keyword >}}
{{< keyword icon="writer" >}} Yi-Fan Zhang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-17 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.10391" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.10391" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 다양한 모달리티를 사용하는 대규모 언어 모델(MLLM)들은 인간의 선호도와 충분히 정렬되지 않아, 환각 감소와 같은 특정 영역에서만 성능 향상을 보였습니다. 이러한 문제는 MLLM의 전반적인 성능 향상을 저해하는 요인이 됩니다.

본 논문에서는 12만 개의 정교하게 주석이 달린 데이터셋 MM-RLHF와 새로운 정렬 알고리즘을 제시하여 이러한 문제를 해결합니다. **비판 기반 보상 모델**과 **동적 보상 조정** 기법을 통해 보상 모델의 질과 정렬 알고리즘의 효율성을 향상시켰으며, 이를 통해 대화 능력과 안전성이 크게 향상된 것을 확인했습니다. **특히, MM-RLHF 데이터셋은 기존 데이터셋보다 규모, 다양성, 주석의 정교함 측면에서 뛰어나 MLLM 정렬 연구의 새로운 기준을 제시합니다.**

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 12만 개의 정교한 인간 주석이 포함된 새로운 MM-RLHF 데이터셋을 통해 MLLM 정렬 연구의 새로운 기준을 제시했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 비판 기반 보상 모델과 동적 보상 조정 기법을 통해 보상 모델의 질과 정렬 알고리즘의 효율성을 개선했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} MM-RLHF 및 제시된 정렬 알고리즘을 사용하여 LLaVA-ov-7B 모델의 성능을 대화 능력 19.5%, 안전성 60% 향상시켰습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**본 논문은 다양한 모달리티를 사용하는 대규모 언어 모델(MLLM)의 성능 향상을 위한 새로운 데이터셋과 정렬 알고리즘을 제시함으로써, 연구자들이 MLLM의 안전성, 신뢰성, 효율성을 개선하는 데 크게 기여할 수 있습니다.**  **특히, 고품질 데이터셋을 사용한 정교한 정렬 방법은 MLLM 분야의 주요 과제 해결에 큰 영향을 미칠 것으로 예상되며, 향후 연구 방향을 제시하는 중요한 자료가 될 것입니다.**

------
#### Visual Insights



![](https://arxiv.org/html/2502.10391/imgs/teaser_tasks.pdf)

> 🔼 MME-RealWorld 벤치마크는 43가지 지각 및 추론 하위 작업을 다루는 5,555개의 실제 환경 도메인으로 구성됩니다. 각 질의응답 쌍에는 5,555개의 선택지가 제공되며, 관련 이미지 부분은 가시성 향상을 위해 빨간색 상자로 강조 표시되어 있습니다. 이 그림은 다양한 실제 환경에서 복잡한 질문에 대해 모델의 성능을 평가하는 MME-RealWorld 벤치마크의 구조를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Diagram of MME-RealWorld. Our benchmark contains 5555 real-world domains, covering 43 perception and reasoning subtasks. Each QA pair offers 5555 options. We highlight and magnify the image parts relevant to the question in a red box for better visibility.
> </details>





{{< table-caption >}}
| [Image] | [Question] | 
|---|---| 
| (A) [Choice A] |  | 
| (B) [Choice B] |  | 
| (C) [Choice C] |  | 
| (D) [Choice D] |  | 
| (E) [Choice E] |  |{{< /table-caption >}}

> 🔼 본 논문의 표 1은 MME-RealWorld 데이터셋에 대한 프롬프트 설정을 보여줍니다.  더 자세히 설명하자면,  다양한 실제 상황(real-world scenarios)을 반영한 멀티모달 질문응답(multimodal question answering) 작업을 위한 프롬프트의 종류, 각 종류에 대한 설명, 그리고 각 프롬프트 유형에 해당하는 질문과 답변의 예시 등이 포함되어 있을 것으로 예상됩니다.  표를 통해 MME-RealWorld 데이터셋이 어떻게 구성되었는지, 그리고 어떤 종류의 질문과 답변을 포함하고 있는지에 대한 자세한 정보를 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Prompt setting of MME-RealWorld.
> </details>





### In-depth insights


#### MM-RLHF Dataset
본 논문에서 제시된 MM-RLHF 데이터셋은 **다양한 모달리티(이미지, 비디오, 텍스트)를 포함하는 대규모 다중 모드 강화 학습 데이터셋**입니다. 기존의 데이터셋보다 크기가 크고, 다양성이 높으며, 주석의 정교함이 뛰어나다는 점이 강조됩니다. **120,000개 이상의 정교하게 주석 달린 데이터**를 통해 다양한 작업에서 모델의 성능을 향상시키는 데 도움이 되며, **이미지 이해, 비디오 이해, MLLM 안전성 등 여러 영역을 포괄**합니다.  데이터 수집, 필터링, 주석 표시 등의 과정을 통해 데이터의 질을 높였으며, 이는 곧 향상된 보상 모델 및 효율적인 정렬 알고리즘으로 이어집니다. 특히, **다양한 질문 유형과 답변의 길이를 고려하여 샘플링 전략을 고안**한 점, 그리고 **다중 모달리티 데이터의 특성을 고려하여 데이터 중복 제거 및 샘플링 기법을 적용**한 점이 중요한 특징입니다.  이를 통해 MM-RLHF 데이터셋은 다양한 작업과 다양한 모델에 대한 성능 개선을 위한 견고한 기반을 마련할 수 있을 것으로 기대됩니다.  하지만, **데이터 수집 및 주석에 대한 비용과 시간이 상당히 소요될 것**이라는 점도 고려해야 합니다.

#### Critique-Based Reward
본 논문에서 제안하는 '비평 기반 보상(Critique-Based Reward)'은 기존의 단순한 스칼라 값 보상 방식의 한계를 극복하기 위한 혁신적인 방법입니다. **기존 보상 모델은 해석력이 부족하고, 모델의 성능 향상에 대한 직관적인 통찰력을 제공하지 못한다는 단점**이 있습니다. 이에 반해, 비평 기반 보상은 모델의 출력에 대한 비평을 생성하고, 이 비평을 기반으로 점수를 매기는 두 단계 접근 방식을 사용합니다. 이를 통해 **보상 신호의 질을 향상시키고 해석력을 높이며, 더욱 정보가 풍부한 피드백**을 제공합니다. **비평 생성은 사전 훈련된 거대 언어 모델을 활용하여 인간의 주석을 보다 상세하고 모델 친화적인 형태로 변환**함으로써 이루어집니다. 또한, **역동적인 보상 조정(Dynamic Reward Scaling)** 기법을 도입하여 고품질의 비교 쌍을 효율적으로 활용하고, 낮은 신뢰도의 데이터의 영향을 완화합니다.  이러한 비평 기반 보상 시스템은 **모델의 성능 향상에 기여하고, 안전성을 높이며, 다양한 측면에서의 성능 개선**을 보여줍니다. 결과적으로, **비평 기반 보상은 다중 모드 거대 언어 모델의 정렬 과정을 개선하고, 보다 신뢰할 수 있는 모델을 구축**하는 데 중요한 역할을 수행합니다.

#### Dynamic Reward Scaling
본 논문에서 제안하는 다이내믹 리워드 스케일링(Dynamic Reward Scaling)은 기존 강화학습 기반 미세조정(RLHF) 방식의 한계를 극복하기 위한 중요한 기술입니다. 기존 RLHF는 모든 샘플에 동일한 가중치를 부여하여 학습하는 반면, **다이내믹 리워드 스케일링은 리워드 신호에 따라 각 샘플의 손실 가중치를 조정**합니다. 이를 통해 고품질 비교 쌍을 효율적으로 활용하고 저품질 샘플의 영향을 최소화하여 모델 성능 향상을 도모합니다.  **핵심은 리워드 마진(reward margin)**을 계산하여 고품질 샘플에 더 높은 가중치를 부여하는 것입니다.  이러한 접근 방식은 학습 과정의 효율성을 높이고, 결과적으로 **대화 능력 향상 및 안전성 개선**과 같은 성능 향상으로 이어집니다.  **다이내믹 리워드 스케일링의 핵심적인 장점**은 고품질 샘플에 집중하여 학습 효율성을 높이는 동시에 저품질 샘플의 부정적 영향을 완화하는 데 있습니다.  이는 대규모 다중 모달 언어 모델(MLLM) 학습에서 특히 중요하며, 향후 연구에서 더욱 발전된 리워드 모델링 및 최적화 기법과의 결합을 통해 더욱 큰 성능 향상을 기대할 수 있습니다. 특히 **해석 가능성(interpretability)**을 높이고, 다양한 작업에서 일관된 성능 개선을 보이는 점은 주목할 만합니다.

#### MM-DPO Framework
MM-DPO 프레임워크는 기존 DPO(Direct Preference Optimization) 방식을 다중 모드 환경에 맞춰 개선한 방법론입니다. **핵심은 역동적인 보상 조정(Dynamic Reward Scaling)**으로, 각 샘플의 보상 신호에 따라 손실 가중치를 조정하여 고품질 비교쌍을 효과적으로 활용하고 저품질 샘플의 영향을 완화하는 데 있습니다.  단순히 가장 어려운 쌍만 학습하는 기존 방식과 달리, **모든 가능한 비교쌍을 활용**하여 보다 정교한 순위 정보를 학습할 수 있게 했습니다. 이를 통해 **모델의 최적화 안정성과 견고성을 향상**시키고, 다양한 작업에서 일관된 성능 향상을 도출합니다.  **고품질 보상 모델**을 활용하여 보상 차이를 정확히 계산하고, 이를 바탕으로 역동적 보상 조정을 수행함으로써 훈련 효율성을 높였습니다.  결과적으로, MM-DPO는 다양한 벤치마크에서 **일관된 성능 향상**을 보이며, **다중 모달 LLM 정렬의 효율성과 성능을 크게 개선**하는 데 기여합니다.

#### Small-Scale Limits
본 논문의 "Small-Scale Limits" 부분은 소규모(7B 파라미터 미만) 다중 모드 LLM의 자기 개선(self-improvement)의 현실적인 어려움을 다룹니다. **모델 용량의 제약**으로 인해, 특히 장문 대화나 복잡한 추론 작업에서 최적의 응답을 생성하는 데 어려움을 겪습니다. **보상 신호의 질적 한계** 또한 문제점으로 지적됩니다. 기존 데이터셋은 자연 이미지나 대화 위주로 구성되어 수학적 추론이나 전문 분야 등 다양한 영역에 대한 보상 모델 학습의 어려움을 야기합니다. 따라서, 소규모 MLLM은 자기 개선을 통해 성능을 크게 향상시키기 어렵다는 결론을 제시하며, **고품질 인간 주석 데이터 기반의 대규모 학습**이 필수적임을 시사합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.10391/imgs/close_source_e.pdf)

> 🔼 그림 12(a)는 MM-RLHF 데이터셋과 MM-DPO 알고리즘을 사용한 실험 결과를 보여줍니다. 기준 모델(LLaVA-OV-7B)과 비교하여, MM-RLHF 데이터셋만 사용한 경우와 MM-RLHF 데이터셋과 기존 DPO 알고리즘을 결합한 경우, 그리고 MM-DPO 알고리즘을 사용한 경우의 성능을 비교 분석합니다. 특히, 실제 환경(Real-world) 작업에서의 성능 향상을 중점적으로 나타냅니다. 세 가지 방법 모두 기준 모델보다 성능이 향상되었지만, MM-DPO를 사용했을 때 가장 큰 성능 향상을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (a) Real-World Tasks
> </details>



![](https://arxiv.org/html/2502.10391/extracted/6204095/imgs/data/web_ui.jpg)

> 🔼 그림 (b)는 논문의 MM-DPO 섹션에 속하며, 하이퍼파라미터 w와 k값 변화에 따른 MM-DPO 모델의 리더보드 점수 변화를 보여줍니다.  x축은 w값, y축은 평균 점수를 나타내고, 각 선은 서로 다른 k값에 해당하는 모델 성능을 보여줍니다. 이 그래프는 다양한 하이퍼파라미터 조합에 따른 성능 변화를 시각적으로 보여주어, MM-DPO 모델의 강건성과 최적 하이퍼파라미터 설정을 파악하는 데 도움을 줍니다.  다양한 k값에서 w값이 증가함에 따라 성능이 향상되는 경향을 확인할 수 있으며,  w와 k의 적절한 조합을 통해 성능 향상을 이끌어낼 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (b) Leaderboard
> </details>



![](https://arxiv.org/html/2502.10391/x1.png)

> 🔼 그림 2는 논문의 5장 실험 부분에 속하며, 두 개의 주요 부분으로 구성됩니다. 왼쪽은 벤치마크에 포함된 다양한 작업 유형을 보여주는 그림입니다. 이 벤치마크는 실제 시나리오와 밀접하게 관련된 5,555개의 주요 도메인과 43,434,343개의 하위 작업으로 구성됩니다.  데이터셋에는 고해상도 이미지 13,366,133개와 주석 29,429,429개가 포함되어 있습니다. 오른쪽은 다양한 최첨단 다중 모드 언어 모델(MLLM)의 성능을 보여줍니다. 영어와 중국어로 나뉜 데이터셋에서 각 모델의 평균 정확도가 표시되어 있습니다.  즉, 그림은 벤치마크 데이터셋의 규모와 다양성, 그리고 여러 MLLM의 성능을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Task Categories (left). Our benchmark spans 5555 key domains and 43434343 subtasks highly related to real-world scenarios, including 13,3661336613,36613 , 366 high-resolution images and 29,4292942929,42929 , 429 annotations. Model Performance (right). Average accuracies of advanced MLLMs are shown across both the English and Chinese splits of the dataset.
> </details>



![](https://arxiv.org/html/2502.10391/x2.png)

> 🔼 이 그림은 다양한 도메인에서 여러 모델의 답변 'E' 출력 빈도를 보여줍니다.  괄호 안의 표기는 과제 유형(P: 지각, R: 추론)을 나타냅니다.  총 질의응답 쌍의 수와 답변이 'E'인 쌍의 수를 비교하여 보여줍니다.  각 도메인별로 모델들이 'E'라는 답을 얼마나 자주 선택하는지 시각적으로 보여주는 그래프 또는 표일 것으로 예상됩니다.  이를 통해 각 모델의 특정 도메인에 대한 성능과 편향성을 파악하는 데 도움이 됩니다. 
> <details>
> <summary>read the caption</summary>
> Figure 3: Frequency of outputting answer “E” for different models across various domains. The notation in parentheses indicates the task type: P for perception and R for reasoning. The total QA pairs and those with answer “E” are also presented for comparison.
> </details>



![](https://arxiv.org/html/2502.10391/x3.png)

> 🔼 그림 (a)는 Claude 3.5 Sonnet 모델의 응답을 보여줍니다.  더 자세히 설명하자면, 이 그림은 본 논문의 다양한 멀티모달 모델 성능 평가 부분에서 사용된 세 가지 모델(Claude 3.5 Sonnet, GPT-4, Qwen2-VL) 중 하나의 모델 응답을 보여주는 예시입니다.  각 모델은 동일한 질문에 대한 응답을 생성했고, 그림은 그 중 Claude 3.5 Sonnet 모델의 응답 내용과 그에 대한 평가자의 점수 및 이유를 시각적으로 보여줍니다.  이를 통해 모델 응답의 질, 정확성, 윤리적 고려 사항 등을 종합적으로 평가하는 방식을 보여주는 것이 목적입니다.  본 그림은 모델 성능 평가의 일부분으로,  다른 모델들과의 비교를 통해 모델의 강점과 약점을 파악하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> (a) Claude 3.5 Sonnet
> </details>



![](https://arxiv.org/html/2502.10391/x4.png)

> 🔼 그림 (b)는 GPT-4를 사용하여 다양한 멀티모달 모델의 응답을 평가한 결과를 보여줍니다.  GPT-4는 각 모델의 응답에 대한 세부적인 비교 분석 및 점수 매기기를 수행하여, 각 차원(도움이 되는 정도, 신뢰성, 윤리적 고려사항)에 대한 점수와 전체 순위를 제공합니다.  이러한 평가는 MM-RLHF 데이터셋의 질과 다양성을 강조하며,  다양한 작업 유형과 모델 성능 차이에 대한 통찰력을 제공합니다.  각 모델의 응답에 대한 GPT-4의 평가 결과가 시각적으로 제시되어, 모델 간의 성능 비교 및 각 모델의 강점과 약점 파악에 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> (b) GPT-4o
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| [Image] [Question] The choices are listed below: |
|---|---| 
|(A) [Choice A] |
|(B) [Choice B] |
|(C) [Choice C] |
|(D) [Choice D] |
|(E) [Choice E] |
| Select the best answer to the above multiple-choice question based on the image. Respond with only the letter (A, B, C, D, or E) of the correct option. |
| The best answer is: |{{< /table-caption >}}
> 🔼 표 2는 다양한 벤치마크에 대한 비교 결과를 보여줍니다. MME-RealWorld는 가장 큰 규모의 완전한 수동 주석 데이터셋이며, 평균 해상도가 가장 높고 가장 어려운 작업들이 포함되어 있습니다. 이 표는 다양한 벤치마크 데이터셋의 특징을 비교하여, 각 데이터셋의 크기, 이미지 해상도, 작업의 복잡성 등을 종합적으로 평가한 결과를 제시합니다. 특히 MME-RealWorld 데이터셋은 수동 주석 작업의 어려움과 고해상도 이미지 사용으로 인해 다른 데이터셋보다 더욱 까다로운 작업들을 포함하고 있음을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Comparison of benchmarks. MME-RealWorld is the largest fully human-annotated dataset, featuring the highest average resolution and the most challenging tasks.
> </details>

{{< table-caption >}}
| Benchmark | # QA-Pair | Fully Human Annotation | CN | Average Resolution | LLaVA-1.5-7B Performance |
|---|---|---|---|---|---| 
| VizWiz | 8000 | × | × | 1224x1224 | 50.0 |
| RealWorldQA | 765 | × | × | 1536x863 | - |
| TextVQA | 5734 | ✓ | × | 985x768 | 58.2 |
| MME | 2374 | ✓ | × | 1161x840 | 76.0 |
| MMBench | 3217 | ✓ | ✓ | 512x270 | 64.3 |
| MMStar | 1500 | × | × | 512x375 | 30.3 |
| ScienceQA | 21000 | × | × | 378x249 | 71.6 |
| ChartQA | 32719 | × | × | 840x535 | - |
| MM-Vet | 218 | × | × | 1200x675 | 31.1 |
| Seed-Bench | 19242 | × | × | 1024x931 | 66.1 |
| SEED-Bench-2-Plus | 2300 | × | × | 1128x846 | 36.8 |
| MMT-Bench | 32325 | × | × | 2365x377 | 49.5 |
| MathVista | 735 | × | × | 539x446 | 26.1 |
| TouchStone | 908 | × | × | 897x803 | - |
| VisIT-Bench | 1159 | × | × | 765x1024 | - |
| BLINK | 3807 | × | × | 620x1024 | 37.1 |
| CV-Bench | 2638 | × | × | 1024x768 | - |
| MME-RealWorld | 29429 | ✓ | ✓ | 2000x1500 | 24.9 |{{< /table-caption >}}
> 🔼 표 3은 다양한 지각 과제에 대한 실험 결과를 보여줍니다. 모델은 평균 성능에 따라 순위가 매겨집니다. 독점 모델에 해당하는 행은 구분을 위해 회색으로 강조 표시되어 있습니다. 'OCR', 'RS', 'DT', 'MO', 'AD'는 각각 특정 작업 도메인(야생에서의 광학 문자 인식, 원격 감지, 다이어그램 및 표, 모니터링, 자율 주행)을 나타냅니다. 'Avg'와 'Avg-C'는 각 도메인의 하위 작업에 대한 가중 평균 정확도와 비가중 평균 정확도를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Experimental results on the perception tasks. Models are ranked according to their average performance. Rows corresponding to proprietary models are highlighted in gray for distinction. “OCR”, “RS”, “DT”, “MO”, and “AD” each indicate a specific task domain: Optical Character Recognition in the Wild, Remote Sensing, Diagram and Table, Monitoring, and Autonomous Driving, respectively. “Avg” and “Avg-C” indicate the weighted average accuracy and the unweighted average accuracy across subtasks in each domain.
> </details>

{{< table-caption >}}
| Fully Human | Annotation |
|---|---|{{< /table-caption >}}
> 🔼 표 4는 추론 과제에 대한 실험 결과를 보여줍니다. 모델은 평균 성능에 따라 순위가 매겨집니다. 독점 모델에 해당하는 행은 구분을 위해 회색으로 강조 표시되어 있습니다. 'OCR', 'RS', 'DT', 'MO', 'AD'는 각각 특정 과제 영역(Optical Character Recognition in the Wild, Remote Sensing, Diagram and Table, Monitoring, Autonomous Driving)을 나타냅니다. 'Avg'와 'Avg-C'는 각 영역의 하위 과제에 대한 가중 평균 정확도와 비가중 평균 정확도를 나타냅니다.  이 표는 다양한 추론 과제에서 여러 모델의 성능을 비교 분석하여 각 모델의 강점과 약점을 파악하고, 특히 독점 모델과 오픈소스 모델 간의 성능 차이를 명확히 보여줍니다. 가중 평균과 비가중 평균을 모두 제시하여 다양한 관점에서의 성능 평가를 가능하게 합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Experimental results on the reasoning tasks. Models are ranked according to their average performance. Rows corresponding to proprietary models are highlighted in gray for distinction. “OCR”, “RS”, “DT”, “MO”, and “AD” each indicate a specific task domain: Optical Character Recognition in the Wild, Remote Sensing, Diagram and Table, Monitoring, and Autonomous Driving, respectively. “Avg” and “Avg-C” indicate the weighted average accuracy and the unweighted average accuracy across subtasks in each domain.
> </details>

{{< table-caption >}}
| Average | Resolution |
|---|---|{{< /table-caption >}}
> 🔼 표 5는 MME-RealWorld-CN의 지각 과제에 대한 실험 결과를 보여줍니다. 모델은 평균 성능에 따라 순위가 매겨집니다. 독점 모델에 해당하는 행은 구분을 위해 회색으로 강조 표시되어 있습니다. 'OCR', 'RS', 'DT', 'MO', 'AD'는 각각 야외 광학 문자 인식, 원격 감지, 다이어그램 및 표, 모니터링, 자율 주행을 나타냅니다. 'Avg'와 'Avg-C'는 각 도메인의 하위 과제에 대한 가중 평균 정확도와 비가중 평균 정확도를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Experimental results on the perception tasks of MME-RealWorld-CN. Models are ranked according to their average performance. Rows corresponding to proprietary models are highlighted in gray for distinction. “OCR”, “RS”, “DT”, “MO”, and “AD” each indicate a specific task domain: Optical Character Recognition in the Wild, Remote Sensing, Diagram and Table, Monitoring, and Autonomous Driving, respectively. “Avg” and “Avg-C” indicate the weighted average accuracy and the unweighted average accuracy across subtasks in each domain.
> </details>

{{< table-caption >}}
| Model Name | Performance |
|---|---| 
| LLaVA-1.5-7B |  |{{< /table-caption >}}
> 🔼 표 6는 MME-RealWorld-CN의 추론 과제에 대한 실험 결과를 보여줍니다. 모델은 평균 성능에 따라 순위가 매겨집니다. 독점 모델에 해당하는 행은 구분을 위해 회색으로 강조 표시되어 있습니다. 'OCR', 'DT', 'MO', 'AD'는 각각 야생의 광학 문자 인식, 다이어그램 및 표, 모니터링 및 자율 주행을 나타내는 특정 작업 영역을 나타냅니다. 'Avg'와 'Avg-C'는 각 영역의 하위 과제에 대한 가중 평균 정확도와 비가중 평균 정확도를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Experimental results on the reasoning tasks of MME-RealWorld-CN. Models are ranked according to their average performance. Rows corresponding to proprietary models are highlighted in gray for distinction. “OCR”, “DT”, “MO”, and “AD” each indicate a specific task domain: Optical Character Recognition in the Wild, Diagram and Table, Monitoring and Autonomous Driving, respectively. “Avg” and “Avg-C” indicate the weighted average accuracy and the unweighted average accuracy across subtasks in each domain.
> </details>

{{< table-caption >}}
| Method | LLM | OCR | RS | DT | MO | AD | Avg | Avg-C |
|---|---|---|---|---|---|---|---|---|
| Qwen2-VL | Qwen2-7B | 81.38 | 44.81 | 70.18 | 37.3 | 34.62 | 58.96 | 53.66 |
| InternVL-2 | InternLM2.5-7B-Chat | 73.92 | 39.35 | 62.80 | 53.19 | 35.46 | 55.82 | 52.94 |
| Claude 3.5 Sonnet | - | 72.47 | 25.74 | 67.44 | 32.19 | 40.77 | 52.90 | 47.72 |
| InternLM-XComposer2.5 | InternLM2-7B | 69.25 | 36.12 | 63.92 | 39.48 | 33.63 | 52.47 | 48.48 |
| InternVL-Chat-V1.5 | InternLM2-Chat-20B | 71.51 | 33.55 | 55.83 | 51.16 | 31.42 | 51.36 | 48.69 |
| Mini-Gemini-34B-HD | Nous-Hermes-2-Yi-34B | 69.55 | 40.40 | 44.36 | 39.61 | 32.70 | 48.05 | 45.32 |
| MiniCPM-V 2.5 | Llama3-8B | 66.79 | 27.69 | 52.81 | 38.70 | 34.15 | 47.37 | 44.03 |
| Cambrian-1-34B | Nous-Hermes-2-Yi-34B | 66.45 | 38.63 | 40.44 | 45.98 | 33.61 | 46.68 | 45.02 |
| GPT-4o | - | 77.69 | 28.92 | 46.68 | 33.93 | 22.43 | 46.43 | 41.93 |
| CogVLM2-llama3-Chat | Llama3-8B | 69.97 | 28.76 | 47.51 | 33.74 | 30.22 | 45.84 | 42.04 |
| Cambrian-1-8B | Llama3-8B-Instruct | 58.68 | 40.05 | 32.73 | 47.68 | 38.52 | 43.82 | 43.53 |
| SliME-8B | Llama3-8B | 53.45 | 42.27 | 29.34 | 40.62 | 33.66 | 40.29 | 39.87 |
| Gemini-1.5-pro | - | 67.62 | 13.99 | 39.90 | 31.11 | 26.64 | 39.63 | 35.85 |
| GPT-4o-mini | - | 62.51 | 6.69 | 44.23 | 26.50 | 24.18 | 37.12 | 32.82 |
| Monkey | Qwen-7B | 54.63 | 24.99 | 32.51 | 28.01 | 29.67 | 36.30 | 33.96 |
| mPLUG-DocOwl 1.5 | Llama-7B | 51.15 | 23.71 | 29.34 | 24.97 | 28.28 | 33.71 | 31.49 |
| DeepSeek-VL | DeepSeek-LLM-7b-base | 49.55 | 25.49 | 23.38 | 26.97 | 33.39 | 33.14 | 31.76 |
| SliME-13B | Vicuna-13B | 50.58 | 25.82 | 20.93 | 24.73 | 27.16 | 31.50 | 29.84 |
| Mini-Gemini-7B-HD | Vicuna-7B-v1.5 | 42.02 | 31.30 | 22.31 | 34.15 | 24.81 | 31.07 | 30.92 |
| YI-VL-34B | Yi-34B-Chat | 44.95 | 31.62 | 15.99 | 34.85 | 28.31 | 30.97 | 31.14 |
| LLaVA-Next | Llama3-8B | 47.94 | 25.42 | 26.63 | 19.46 | 18.66 | 30.14 | 27.62 |
| LLaVA-Next | Qwen-72B | 37.07 | 29.13 | 27.68 | 29.37 | 17.98 | 29.01 | 28.25 |
| LLaVA1.5-13B | Vicuna-13B | 44.10 | 23.27 | 20.17 | 20.45 | 26.12 | 28.42 | 26.82 |
| ShareGPT4V-13B | Vicuna-13B | 44.55 | 23.06 | 20.17 | 19.26 | 26.12 | 28.38 | 26.63 |
| MiniGPT-v2 | Llama 2-7B-Chat | 39.02 | 23.33 | 20.41 | 19.26 | 25.96 | 26.94 | 25.60 |
| ShareGPT4V-7B | Vicuna-7B | 39.39 | 22.10 | 20.08 | 19.13 | 26.04 | 26.73 | 25.35 |
| LLaVA1.5-7B | Vicuna-7B | 38.69 | 22.12 | 20.08 | 19.13 | 26.04 | 26.54 | 25.21 |
| Qwen-VL-Chat | Qwen-7B | 32.37 | 15.14 | 15.59 | 22.13 | 15.08 | 20.75 | 20.06 |
| TextMonkey | Qwen-7B | 37.30 | 11.69 | 5.93 | 16.14 | 14.26 | 18.18 | 17.06 |
| # QA pairs |  | 5740 | 3738 | 5433 | 2196 | 3660 | 20767 | 20767 |{{< /table-caption >}}
> 🔼 표 7은 MM-RLHF-SafetyBench의 요약 정보, 평가 지표 및 비교 방법을 보여줍니다. 이 표는 다양한 종류의 작업(적대적 공격 또는 안전 관련)에 대한 다중 모드 모델의 안전성 및 적대적 강건성을 평가하기 위해 사용된 여러 작업들을 개괄적으로 설명합니다. 작업은 공격 유형(적대적 또는 안전)에 따라 분류되고, 평가 지표에는 적대적 공격의 성공률 또는 유해한 출력을 거부하는 모델의 거부율이 포함됩니다. 비교 열의 화살표는 평가 지표의 더 높은(↑↑) 또는 더 낮은(↓↓) 값이 선호되는지 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 7: MME-RealWorld-SafetyBench: summary of Task Data, Evaluation Metrics, and Comparison Methods for Safety and Adversarial Testing. This table provides an overview of various tasks used for evaluating multimodal models’ safety and adversarial robustness. The tasks are categorized based on attack type (adversarial or safety), and the evaluation metrics include success rates of adversarial attacks or model rejection rates for harmful outputs. The arrows in the Comparison column indicate whether higher (↑↑\uparrow↑) or lower (↓↓\downarrow↓) values of the evaluation metric are preferred.
> </details>

{{< table-caption >}}
| Method | LLM | OCR | DT | MO | AD | Avg | Avg-C |
|---|---|---|---|---|---|---|---| 
| Task Split |  |  |  |  |  |  |  |
| # QA pairs |  | 500 | 500 | 498 | 1334 | 2832 | 2832 |
| Claude 3.5 Sonnet | - | 61.90 | 61.20 | 41.79 | 31.92 | 44.12 | 49.20 |
| Qwen2-VL | Qwen2-7B | 63.40 | 48.60 | 33.13 | 31.47 | 40.39 | 44.15 |
| InternVL-2 | InternLM2.5-7B-Chat | 57.40 | 39.00 | 43.57 | 29.84 | 38.74 | 42.45 |
| GPT-4o | - | 61.40 | 44.80 | 36.51 | 26.41 | 37.61 | 42.28 |
| CogVLM2-llama3-Chat | Llama3-8B | 54.00 | 32.80 | 41.16 | 31.18 | 37.25 | 39.79 |
| InternVL-Chat-V1-5 | InternLM2-Chat-20B | 56.80 | 35.40 | 37.35 | 28.94 | 36.48 | 39.62 |
| Cambrian-1-8B | Llama3-8B-Instruct | 53.20 | 27.40 | 42.37 | 30.73 | 36.16 | 38.43 |
| SliME-8B | Llama3-8B | 53.20 | 29.40 | 36.14 | 31.55 | 35.80 | 37.57 |
| MiniCPM-V 2.5 | Llama3-8B | 44.00 | 31.80 | 36.95 | 31.03 | 34.50 | 35.95 |
| SliME-13B | Vicuna-13B | 41.00 | 39.00 | 33.13 | 30.80 | 34.46 | 35.98 |
| InternLM-XComposer2.5 | InternLM2-7B | 53.40 | 41.00 | 17.67 | 29.99 | 33.90 | 35.52 |
| GPT-4o-mini | - | 47.00 | 39.80 | 25.81 | 26.79 | 32.48 | 34.85 |
| YI-VL-34B | Yi-34B-Chat | 42.40 | 26.00 | 31.33 | 31.55 | 32.45 | 32.82 |
| LLaVA-Next | Llama3-8B | 55.20 | 23.40 | 21.08 | 30.73 | 32.06 | 32.60 |
| Mini-Gemini-34B-HD | Nous-Hermes-2-Yi-34B | 59.20 | 39.20 | 20.48 | 22.84 | 31.73 | 35.43 |
| Gemini-1.5-pro | - | 52.70 | 33.20 | 28.33 | 19.20 | 29.19 | 33.36 |
| Monkey | Qwen-7B | 27.20 | 20.80 | 27.31 | 33.04 | 28.84 | 27.09 |
| DeepSeek-VL | DeepSeek-LLM-7b-base | 45.20 | 23.80 | 16.67 | 27.31 | 27.98 | 28.25 |
| LLaVA-Next | Qwen-72B | 17.20 | 34.20 | 27.31 | 29.69 | 27.86 | 27.10 |
| Cambrian-1-34B | Nous-Hermes-2-Yi-34B | 55.00 | 36.00 | 19.48 | 16.07 | 27.06 | 31.64 |
| mPLUG-DocOwl 1.5 | Llama-7B | 42.60 | 19.80 | 20.48 | 26.04 | 26.88 | 27.23 |
| Mini-Gemini-7B-HD | Vicuna-7B-v1.5 | 35.40 | 24.60 | 25.90 | 23.29 | 26.12 | 27.30 |
| LLaVA1.5-13B | Vicuna-13B | 30.20 | 20.80 | 27.51 | 24.78 | 25.51 | 25.82 |
| ShareGPT4V-13B | Vicuna-13B | 26.00 | 20.80 | 27.31 | 24.55 | 24.63 | 24.67 |
| LLaVA1.5-7B | Vicuna-7B | 26.00 | 20.60 | 25.90 | 24.18 | 24.17 | 24.17 |
| ShareGPT4V-7B | Vicuna-7B | 24.15 | 20.60 | 26.10 | 24.18 | 23.88 | 23.76 |
| MiniGPT-v2 | Llama 2-7B-Chat | 30.00 | 20.40 | 16.87 | 23.66 | 23.01 | 22.73 |
| Qwen-VL-Chat | Qwen-7B | 28.60 | 13.60 | 16.47 | 24.63 | 21.95 | 20.83 |
| TextMonkey | Qwen-7B | 30.40 | 2.20 | 4.42 | 20.01 | 15.96 | 14.26 |{{< /table-caption >}}
> 🔼 이 표는 인간의 주석을 보강하기 위해 사용된 프롬프트의 예시를 보여줍니다.  인간 평가자는 질문, 모델 응답, 그리고 응답에 대한 인간 전문가의 의견을 받습니다. 이 프롬프트는 인간의 의견을 더욱 자세하고 논리적으로 확장하여 모델 학습에 더 유용한 정보를 제공하기 위해 고안되었습니다.  프롬프트는 질문, 답변, 그리고 인간 평가자의 의견을 포함하며, 인간 평가자는 이를 바탕으로 더욱 자세하고 논리적인 설명을 추가해야 합니다.  추가된 설명은 기존 의견에 기반해야 하며, 추측이나 불확실한 내용을 포함해서는 안 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Example of the Prompt Used for Augmenting Human Annotations.
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