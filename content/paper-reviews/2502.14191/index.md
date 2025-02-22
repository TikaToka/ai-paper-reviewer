---
title: "Multimodal RewardBench: Holistic Evaluation of Reward Models for Vision Language Models"
summary: "Multimodal RewardBench: VLM 리워드 모델을 위한 포괄적 평가 벤치마크"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Meta AI",]
showSummary: true
date: 2025-02-20
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.14191 {{< /keyword >}}
{{< keyword icon="writer" >}} Michihiro Yasunaga et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-21 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.14191" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.14191" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/multimodal-rewardbench-holistic-evaluation-of" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 비전-언어 모델(VLM) 리워드 모델 평가는 제한적이었고, 종합적인 벤치마크가 부족했습니다. 이러한 문제를 해결하기 위해, 본 연구는 **6가지 주요 능력(일반적인 정확성, 선호도, 지식, 추론, 안전성, VQA)**을 포괄하는 **Multimodal RewardBench**라는 새로운 벤치마크를 제시합니다. 이 벤치마크는 다양한 VLM에서 수집한 5,211개의 데이터를 활용하며, 전문가에 의해 주석이 달렸습니다. 



실험 결과, 최고 성능 모델조차도 72%의 정확도를 달성하는 데 그쳤으며, 특히 **추론 및 안전성 과제에서 어려움**을 보였습니다. **Multimodal RewardBench는 VLM 리워드 모델 개발을 위한 도전적인 테스트 환경**을 제공하며, **모델의 규모 확장과 관련된 새로운 통찰력**을 제공합니다. 이는 VLM 리워드 모델 연구의 발전에 크게 기여할 것으로 기대됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} Multimodal RewardBench는 VLM 리워드 모델을 위한 최초의 포괄적인 벤치마크입니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 다양한 VLM 판정 모델의 성능을 평가하여, 상위 모델조차도 완벽하지 않음을 보여줍니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 추론 및 안전성 과제에서 모델의 어려움을 강조하고, 규모 확장 추세를 분석하여 향후 연구 방향을 제시합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**본 논문은 다양한 분야를 아우르는 멀티모달 리워드 모델 평가를 위한 첫 번째 포괄적이고 전문가 검토 기반의 벤치마크인 Multimodal RewardBench를 제시하여, 비전-언어 모델(VLM)의 리워드 모델 개발에 중대한 영향을 미칠 것입니다.**  이 벤치마크는 VLM의 다양한 기능(정확성, 선호도, 지식, 추론, 안전성, VQA)을 포괄적으로 평가하며, 향후 연구 방향과 리워드 모델 개선에 대한 통찰력을 제공합니다. 특히, 안전성 및 추론 과제에서 모델의 어려움을 강조하고, 확장성 추세에 대한 새로운 정보를 제공함으로써, **멀티모달 리워드 모델 연구의 발전에 크게 기여할 것**으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.14191/x1.png)

> 🔼 그림 1은 Multimodal RewardBench의 개념을 보여줍니다. 왼쪽에는 다양한 시각 언어 모델(VLM)의 출력물을 평가하기 위해, 사람이 주석을 단 벤치마크 데이터셋의 예시가 나와 있습니다. 이 데이터셋은 다양한 모드를 가진 프롬프트(prompt), 선택된 응답(chosen response), 기각된 응답(rejected response) 세 가지 요소의 세 쌍(triplets)으로 구성됩니다. 오른쪽에는 이렇게 만들어진 벤치마크 데이터셋을 사용하여 다양한 보상 모델 또는 VLM 판정 모델(judge)의 정확도를 평가하는 과정을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Illustration of Multimodal RewardBench. We build a human-annotated benchmark that consists of (multimodal prompt, chosen response, rejected response) triplets (left). Using this benchmark, we evaluate the accuracy of various reward models or judges for vision-language models (right). See §A for real examples from our benchmark.
> </details>





{{< table-caption >}}
| Dataset | Multimodal | Cover holistic dimensions (e.g. reasoning, safety) | Human expert annotated / High inter-annotator agreement |
|---|---|---|---| 
| Anthropic HH<br>OpenAI Summarization<br>JudgeBench |  |  |  |
| RewardBench |  | ✔ |  |
| Prometheus-Vision<br>Llava-critic<br>VLRewardBench<br>MLLM-as-a-Judge | ✔ |  |  |
| Multimodal-RewardBench (Ours) | ✔ | ✔ | ✔ |{{< /table-caption >}}

> 🔼 표 1은 기존의 보상 모델 평가 데이터와 제안하는 다중 모드 RewardBench를 비교 분석한 표입니다. 기존 연구들은 일반적인 VQA 작업에 국한되거나, 사람이 직접 주석을 달지 않은 데이터를 사용하는 등 한계점을 지니고 있습니다. 반면, RewardBench는 추론, 안전, VQA를 포함한 6가지 영역을 다루는 종합적인 벤치마크로, 전문가가 직접 주석을 달아 신뢰도를 높였습니다.  따라서 다양한 비전-언어 모델(VLMs)의 보상 모델을 평가하는 최초의 종합적인 벤치마크임을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparison with existing evaluation data for reward models. Our Multimodal RewardBench is the first holistic benchmark for evaluating reward models for multimodal LLMs (vision-language models).
> </details>





### In-depth insights


#### RewardBench Intro
본 논문의 "RewardBench Intro" 부분은 기존의 다양한 보상 모델 평가 벤치마크의 한계를 지적하고, **다차원적이고 종합적인 보상 모델 평가를 위한 새로운 벤치마크인 RewardBench**를 제시하는 서론으로 추정됩니다. RewardBench는 기존 연구들이 주로 단일 모달리티(텍스트)에 집중했던 점을 넘어, **비전-언어 모델(VLMs)에 특화된 다모달 보상 모델을 평가**하기 위해 고안되었을 것입니다.  특히, 정확성, 선호도, 지식, 추론, 안전성, VQA 등 다양한 측면을 아우르는 **포괄적인 평가 지표**를 통해 기존 벤치마크보다 더욱 섬세하고 정교한 평가가 가능하다는 점을 강조할 것으로 예상됩니다. 따라서, 이 부분은 RewardBench의 필요성과 독창성을 설명하는 동시에, **향후 연구 방향에 대한 중요한 시사점**을 제공할 것입니다.  다시 말해, RewardBench가 단순한 평가 도구를 넘어, VLM 연구 발전에 기여할 핵심적인 기반이 될 것임을 보여주는 역할을 할 것으로 예상됩니다.

#### VLM Judge Analysis
본 논문에서 가상의 "VLM Judge Analysis" 섹션은 다양한 비전-언어 모델(VLMs)의 판단 능력을 평가하는 데 중점을 둘 것입니다. 이를 위해, **다양한 VLM들을 판정자(judge)로 활용**, 멀티모달 리워드 벤치마크 상에서 그 성능을 측정하고 분석합니다. **상위권 모델들조차 완벽한 정확도를 보이지 못하며, 특히 추론 및 안전성 영역에서 어려움을 겪는다는 점**이 중요한 통찰을 제공할 것입니다. 이는 **리워드 모델 개발의 어려움과 향상 여지**를 보여주는 핵심 결과이며, 벤치마크의 난이도와 실제 적용 가능성을 시사합니다.  더불어, 모델 규모의 확장에 따른 성능 변화, 특정 영역에 대한 강점과 약점 등 세부적인 분석 결과는 **향후 VLM 및 리워드 모델 개발 방향**을 제시하는 데 귀중한 정보가 될 것입니다.  **개방형 모델과 독점 모델 간 성능 비교**를 통해 각 모델의 장단점을 파악하고, 모델 개발 전략에 대한 시사점을 도출할 수 있을 것입니다.  결론적으로, 이 섹션은 멀티모달 리워드 모델의 현황과 한계를 객관적으로 제시하고,  미래 연구 방향을 제시하는 데 크게 기여할 것입니다.

#### Benchmark Datasets
본 논문에서 다루는 'Benchmark Datasets'는 **다양한 비전-언어 모델(VLMs)의 성능을 평가하기 위한 기준 데이터셋**을 의미합니다. 이는 단순한 데이터셋 목록이 아니라, 각 데이터셋의 특징과 한계를 명확히 이해하고, VLM 평가에 있어서 어떤 측면을 강조하는지, 또 어떤 측면이 부족한지에 대한 심층적인 분석이 필요함을 시사합니다.  **다양한 작업(예: 일반적인 정확성, 선호도, 지식, 추론, 안전성, VQA)을 포괄하는 종합적인 벤치마크를 구축하는 노력**이 중요하며, 이를 통해 VLM의 능력을 다각적으로 평가하고, 향후 연구 방향을 제시할 수 있습니다.  **특히, 기존 텍스트 기반 벤치마크의 한계를 넘어, 비전-언어적 요소를 포함하는 벤치마크의 필요성**을 강조하며, 이는 멀티모달 모델의 발전에 중요한 역할을 할 것입니다.  **인간 전문가에 의한 주석의 중요성** 또한 간과해서는 안 됩니다.  정확하고 일관성 있는 평가를 위해서는 고품질의 주석 데이터가 필수적이며, 이는 벤치마크의 신뢰성을 높이는 데 기여합니다.  결론적으로, 'Benchmark Datasets'는 단순한 데이터셋 목록을 넘어, **VLM 평가의 핵심 요소이며, 모델 개발 및 평가 방식에 대한 깊이 있는 이해**를 바탕으로 설계되어야 합니다.

#### Holistic Evaluation
본 논문에서 제시된 '전면적 평가(Holistic Evaluation)'는 **다양한 측면**을 고려하여 시각 언어 모델(VLM)의 보상 모델을 평가하는 접근 방식입니다. 단순히 정확성만 평가하는 것이 아니라, **정확성, 선호도, 지식, 추론, 안전성, VQA** 등 여러 요소를 종합적으로 분석합니다. 이러한 다차원적 평가는 모델의 강점과 약점을 균형 있게 파악하고, **개선 방향**을 제시하는 데 중요한 역할을 합니다. 특히 기존 연구들이 특정 측면에만 집중했던 것과 달리, **전반적인 성능**을 평가함으로써 보다 객관적이고 포괄적인 평가 결과를 제공합니다. 이는 향후 VLM 보상 모델 개발에 있어 중요한 지표가 될 것이며, **더욱 발전된 모델**의 개발을 촉진할 것으로 기대됩니다.  **다양한 데이터셋과 모델**을 사용하여 실험을 진행한 결과, 최고 성능 모델조차 완벽하지 않으며, 특히 추론 및 안전성 영역에서 개선의 여지가 있음을 보여줍니다. 따라서 이러한 전면적 평가 방식은 모델의 한계를 명확히 드러내고, 보다 **실용적이고 안전한 VLM**의 개발을 위한 중요한 이정표가 될 것입니다.

#### Future Work
본 논문의 "향후 연구" 부분은 **다양한 차원에서의 확장 및 개선**을 제시합니다. 우선, **더욱 다양한 데이터셋을 활용**하여 각 차원(일반 정확성/선호도, 지식, 추론, 안전성, VQA)을 더욱 풍부하게 만들 수 있습니다. 특히 안전성 측면에서는 현재 데이터셋의 부족을 해결하기 위해 더욱 다양한 안전 관련 측면(프롬프트 거부, NSFW 콘텐츠 감지, 유해 응답 식별 등)을 추가적으로 고려해야 합니다.  코딩 평가의 경우, 파이썬 플롯 및 LaTeX에만 초점을 맞춘 현재 방식에서 벗어나, HTML, JavaScript, C++와 같은 다양한 프로그래밍 언어를 포함하고 알고리즘 문제 해결에 중점을 둔 더욱 복잡한 코딩 문제를 다루는 것이 중요합니다.  또한, **현재 VLM-as-a-judge 방식에만 초점을 맞춘 평가에서 벗어나** 회귀/분류 기반 VLM 보상 모델을 평가할 수 있도록 연구를 확장해야 합니다.  마지막으로, 본 연구에서 제시된 벤치마크를 활용한 추가적인 실험과 분석을 통해 보상 모델 발전에 더욱 기여할 수 있을 것입니다.  **특히, 다양한 모델 크기의 성능 비교 분석을 확장하고, 대규모 언어모델의 특징과 이를 보상 모델에 적용하는 방안에 대한 연구가 필요합니다.**


### More visual insights




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Cover holistic dimensions |
|---|---| 
| (e.g. reasoning, safety) |{{< /table-caption >}}
> 🔼 표 2는 시각 언어 모델(VLMs)을 위한 보상 모델 평가를 위한 종합적인 벤치마크인 Multimodal RewardBench의 요약입니다. 이 벤치마크는 VLMs와 관련된 여섯 가지 주요 영역(일반 정확성, 일반 선호도, 지식, 추론, 안전, VQA)을 다룹니다. 긴 응답과 짧은 응답 형식 모두를 다루고 있으며, 두 가지 유형의 판정 작업('정답 대 오답' 및 '사람이 선호하는 응답 대 비선호 응답'(두 응답 모두 정답이거나 오답인 경우))을 평가합니다. 긴 형식 응답에 대한 판정 레이블은 전문가의 고품질 주석을 통해 수집됩니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Summary of Multimodal RewardBench, a holistic benchmark for evaluating reward models for vision-language models (VLMs). We cover six key areas relevant to VLMs: general correctness, general preference, knowledge, reasoning, safety, and VQA. We cover both long and short response formats, and assess both types of judge tasks: ’correct vs incorrect response’ and ’human-preferred vs non-preferred’ (provided both responses are either correct or incorrect). Our judge labels for long-form responses are collected by high-quality annotation from human experts.
> </details>

{{< table-caption >}}
| Human expert annotated / | High inter-annotator agreement |
|---|---|{{< /table-caption >}}
> 🔼 표 3은 다양한 VLMs(Vision Language Model)을 Multimodal RewardBench를 사용하여 평가한 결과를 보여줍니다.  각 모델의 전반적인 정확도와 여섯 가지 하위 작업(일반적인 정확성, 일반적인 선호도, 지식, 추론, 안전, VQA)에 대한 정확도를 세분화하여 제시합니다. 상위 세 개의 모델(Claude 3.5 Sonnet, Gemini 1.5 Pro, GPT-4o)의 전반적인 정확도는 72%에 불과하여, Multimodal RewardBench가 보상 모델 개발에 있어 상당히 어려운 벤치마크임을 시사합니다. 각 하위 작업에 대한 데이터 출처와 작업 정의는 표 2를 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Table 3: Accuracy of various VLM judges on Multimodal RewardBench, with a breakdown across task categories. The top-performing models, Claude 3.5 Sonnet, Gemini 1.5 Pro and GPT-4o, achieve only 72% overall accuracy, suggesting that the benchmark offers a challenging testbed for reward model development. For the data source and task definitions of each category, see Table 2.
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
{{< /gallery >}}