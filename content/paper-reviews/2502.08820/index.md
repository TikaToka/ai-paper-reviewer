---
title: "Can a Single Model Master Both Multi-turn Conversations and Tool Use? CoALM: A Unified Conversational Agentic Language Model"
summary: "단일 모델로 다회차 대화와 도구 사용 모두를 마스터하는 CoALM: 통합적 대화형 에이전트 언어 모델"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Dialogue Systems", "🏢 University of Illinois Urbana-Champaign",]
showSummary: true
date: 2025-02-12
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.08820 {{< /keyword >}}
{{< keyword icon="writer" >}} Emre Can Acikgoz et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-18 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.08820" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.08820" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/can-a-single-model-master-both-multi-turn" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

현존하는 대화형 시스템은 **다회차 대화 관리**와 **도구(API) 활용** 능력 중 하나에만 특화되어, 두 가지 능력 모두를 고루 갖춘 시스템 개발에 어려움을 겪고 있습니다. 특히, 다회차 대화를 효과적으로 관리하면서 동시에 다양한 API를 자유롭게 활용하는 것은 매우 어려운 과제입니다.

본 연구는 이러한 문제를 해결하기 위해 **다회차 대화와 도구 사용 능력을 통합한 새로운 대화형 에이전트 언어 모델인 CoALM**을 제시합니다.  CoALM은 **새롭게 개발된 CoALM-IT 데이터셋**을 사용하여 학습되었으며, 다양한 벤치마크 테스트에서 **기존 최고 성능 모델들을 뛰어넘는 결과**를 보였습니다.  CoALM의 개발 및 공개를 통해, **대화형 에이전트의 성능 향상 및 오픈소스 생태계 발전**에 기여할 것으로 기대됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 단일 모델로 다회차 대화와 도구 사용을 통합적으로 처리하는 새로운 접근 방식인 CoALM 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 다회차 대화와 API 사용을 결합한 새로운 다중 작업 학습 데이터셋인 CoALM-IT 개발 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} CoALM은 기존 최고 성능 모델들을 다양한 벤치마크에서 능가하는 성능을 보임 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대화형 에이전트** 분야의 핵심적인 문제점인 **다회차 대화 관리 및 도구 사용 능력**을 동시에 향상시키는 새로운 모델을 제시하여, **개방형 대화 시스템** 연구에 중요한 기여를 합니다.  또한, 제시된 모델은 **오픈소스**로 공개되어, 다른 연구자들의 **후속 연구 및 발전**을 위한 기반을 마련합니다. 이는 **인공지능 분야의 발전**에 직접적으로 기여하며, 특히 **대화형 AI 시스템**의 실용성을 높이는 데 큰 의미가 있습니다. 

------
#### Visual Insights



![](https://arxiv.org/html/2502.08820/x1.png)

> 🔼 그림 1은 TOD 시스템과 언어 에이전트(LA)의 기능을 통합적으로 보여줍니다. TOD 시스템은 턴이 많은 대화와 작업 완료에 뛰어나지만 고급 API 기능이 부족한 반면, LA는 API를 잘 처리하지만 일관성 있는 다턴 대화에는 어려움을 겪는다는 것을 보여줍니다.  즉, TOD 시스템은 여러 턴에 걸친 대화를 잘 처리하고 작업을 완료하지만, 새로운 API에 대한 기능이 부족합니다. 반면 LA는 API 활용 능력이 뛰어나지만,  일관성 있는 다턴 대화를 생성하는 데 어려움이 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Unifying Capabilities of TOD Systems and LAs. TOD systems excel in multi-turn conversations and task completion but lack advanced API capabilities, while LA handle APIs well but struggle with coherent multi-turn dialogue.
> </details>





{{< table-caption >}}
| Data Domain | Data Type | Data Name | Data Format | # of Data Samples | # of Total Tokens | Avg. Tokens Per Sample |
|---|---|---|---|---|---|---|
| **TOD** | Single-Turn | SNIPS | State Tracking | 13,028 | 12,278,780 | 942.49 |
| **LA** | Single-Turn | Hammer | API Call | 13,819 | 10,199,147 | 738.05 |
|  | Multi-Turn | ToolAce | API Call | 202,500 | 129,001,612 | 637.04 |
| **CRA** | Multi-Turn | SGD | ReAct API Call | 82,236 | 59,704,782 | 726.02 |
| **Total** |  |  |  | 311,583 | 211,184,321 | 760.90 |{{< /table-caption >}}

> 🔼 이 표는 논문에서 제안하는 CoALM-IT 데이터셋의 통계적 세부 정보를 보여줍니다.  CoALM-IT 데이터셋은 대화 상태 추적, 복잡한 함수 호출, ReAct 스타일의 멀티턴 대화를 포함하는 세 가지 차원을 다룹니다.  이 표는 각 데이터 유형(TOD, LA, CRA)의 데이터 샘플 수, 총 토큰 수, 샘플당 평균 토큰 수를 보여주어 학습 데이터의 구성을 자세히 설명합니다.  'Generated CRA'는 대화형 ReAct API 데이터셋을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 1: CoALM-IT Dataset Details. Statistical details of our proposed CoALM-IT dataset showcasing the training mixtures. Generated CRA denotes the Conversational ReAct API dataset.
> </details>





### In-depth insights


#### Unified Agent Vision
통합 에이전트 비전은 **단일 모델이 다중 턴 대화와 도구 사용을 모두 마스터할 수 있는 가능성**을 탐구하는 것입니다. 이는 기존의 특정 작업에 초점을 맞춘 대화 시스템과 도구 사용에 특화된 언어 에이전트의 한계를 극복하기 위한 시도입니다.  **강력한 다중 턴 관리와 고급 기능 호출은 효과적인 대화형 에이전트에 필수적**이며, 이 비전은 이 두 가지 기능을 통합하여 사용자 의도를 유지하고 다양한 API를 효율적으로 활용하는 **통합된 대화형 에이전트**를 구축하는 데 있습니다. 이를 위해서는 **다중 작업 데이터셋을 이용한 훈련**이 중요하며,  **새로운 서비스에 대한 적응력**과 **다양한 API 접근**이 가능해야 함을 시사합니다.  **개방형 접근 방식**을 채택하여  더 많은 연구가 이루어질 수 있도록 하는 것이 중요하며, 이는 **단일 모델 접근 방식의 실현 가능성**을 보여주고 대화형 에이전트의 새로운 기준을 제시할 수 있습니다.

#### CoALM-IT Dataset
CoALM-IT 데이터셋은 **대화 상태 추적, 복잡한 함수 호출, ReAct 스타일의 다회차 대화** 세 가지 차원을 아우르는 통합적인 접근 방식을 제시합니다.  기존 TOD 시스템의 한계를 극복하고자 **ReAct 추론과 API 사용을 결합**한 새로운 데이터 생성 방식을 통해,  **실제 환경에 가까운 다양한 시나리오**를 포함합니다. 특히, **GPT-4를 활용**하여 생성된 대화형 ReAct API(CRA) 인스턴스는 **다중 사고 단계를 통합**하여, 모델이 API 호출 여부 및 사용자 응답 여부를 결정하는 과정을 반영합니다.  이러한 접근 방식은 기존의 특정 API에 국한된 TOD 시스템 및 단일 턴 함수 호출에 초점을 맞춘 LA 시스템의 한계를 뛰어넘어, **통합적인 대화형 에이전트** 개발을 위한 중요한 토대가 됩니다.  **개방형 모델의 성능 향상**에 기여할 뿐 아니라, 향후 연구에 활용될 수 있는 귀중한 자원이 될 것으로 예상됩니다.

#### Benchmark Results
본 논문의 벤치마크 결과는 **CoALM 모델이 기존의 TOD 시스템 및 LA 모델보다 우수한 성능을 보임**을 보여줍니다. 특히, **다중 턴 대화 및 API 호출 능력에서 뛰어난 성능**을 기록하여, **단일 모델로 다중 작업을 효과적으로 수행할 수 있음**을 입증하였습니다.  **MultiWOZ, API-Bank, BFCL V3 세 가지 벤치마크 모두에서 CoALM 모델은 최첨단 성능**을 달성하였고, 특히 대규모 모델일수록 성능 향상이 두드러졌습니다. 이는 **CoALM이 대화 관리와 에이전트 기능을 통합**하여 상호보완적으로 작용함으로써 기존 모델의 한계를 극복했음을 시사**합니다. 하지만, 제한된 모델 아키텍처 사용 및 특정 데이터셋에 대한 의존성 등의 한계점도 존재합니다.**

#### Open-Source Impact
본 논문에서 **오픈소스의 영향**에 대한 논의는 주로 **대규모 언어 모델(LLM)**의 접근성과 연구 확장성에 초점을 맞춥니다.  **오픈소스 모델 공개**를 통해 더 많은 연구자들이 최첨단 기술에 접근하여 연구를 진행하고, **모델 개선**에 기여할 수 있게 되었습니다. 이는 상용 모델에 비해 **비용 효율적**이며, **투명성**을 확보하고 **공동 연구**를 촉진하는 긍정적 측면을 보여줍니다.  하지만 **오픈소스 모델**의 성능이 상용 모델에 비해 다소 떨어지는 측면도 존재하며, 이러한 성능 차이는  **데이터셋 규모와 품질**, **모델 학습 방식**, **컴퓨팅 자원** 등 여러 요소에 기인합니다. 따라서 **오픈소스 LLM 생태계**의 지속적인 성장과 발전을 위해서는 **데이터셋 구축**, **모델 아키텍처 개선**, **학습 효율 향상** 등 다방면의 노력이 필요합니다. **오픈소스 모델**의 장점과 단점을 균형 있게 고려하여, **연구 및 상용화** 전략을 수립하는 것이 중요합니다.

#### Future Work
본 논문의 "미래 연구 방향" 부분은 **대규모 언어 모델(LLM) 기반의 대화형 에이전트의 기능 향상**에 초점을 맞춰야 할 것입니다.  특히, **복잡한 멀티턴 대화와 다양한 API 호출의 통합**을 더욱 효율적이고 자연스럽게 처리하는 방안을 모색해야 합니다.  강화 학습(RL)을 활용하여 LLM이 다양한 환경에서 스스로 학습하고 발전할 수 있도록 하는 연구가 필요하며, **제로샷 또는 극소수 샷 학습** 성능 개선을 위한 연구도 중요합니다.  또한, **다양한 모델 아키텍처와 훈련 전략**을 비교 분석하여 CoALM 모델의 한계를 극복하고 더욱 강력한 대화형 에이전트를 개발하는 데 집중해야 합니다.  나아가, 개발된 모델의 **실제 환경 적용을 위한 테스트 및 평가**를 통해 실용성을 높이고, 윤리적 문제점을 해결하는 방안을 마련해야 합니다.  **오픈소스 커뮤니티의 참여**를 확대하여 연구의 지속가능성을 확보하는 것 또한 중요한 미래 연구 과제입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.08820/x2.png)

> 🔼 그림 2는 CoALM 파이프라인의 개요를 보여줍니다. 데이터 변환 과정과 미세 조정 프레임워크를 보여주는 데 중점을 둡니다. 위쪽 세 줄은 데이터 변환 과정을 나타내며, 오른쪽에는 해당 예시가 나와 있습니다. 각 훈련 샘플에서 녹색 텍스트는 지시어 샘플의 입력 구성 요소를 강조하고, 보라색 텍스트는 미세 조정 중에 최적화된 대상 출력을 나타냅니다. 자세한 내용은 그림 4~7을 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Figure 2: Overview of the CoALM Pipeline. This figure illustrates our dataset generation and fine-tuning framework. The top three rows depict the data transformation processes, along with a corresponding sample shown on the right. In each training sample, green text highlights the input components of the instruction sample, while purple text indicates the target outputs optimized during fine-tuning. For detailed examples, refer to Figures 4 - 7.
> </details>



![](https://arxiv.org/html/2502.08820/x3.png)

> 🔼 그림 3은 CoALM 모델과 다른 기준 모델들의 함수 호출 성능을 API-Bank L1(위쪽) 및 BFCL V3 병렬 함수 호출(아래쪽) 벤치마크에서 비교 분석한 결과를 보여줍니다.  API-Bank L1은 단일 함수 호출, BFCL V3는 병렬 함수 호출 시나리오를 평가합니다. 이 그림은 각 모델의 출력 결과와 정답을 제시하여, CoALM 모델이 다른 모델들에 비해 일관되게 우수한 성능을 보임을 시각적으로 보여줍니다.  특히, 다른 모델들이 구문 오류, 함수 누락, 잘못된 값 등의 문제를 보이는 반면, CoALM은 정확한 함수 호출과 매개변수를 제공하여 정답을 생성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Error Analysis of Function-Calling Results. Illustrated performance comparison on function calling benchmarks API-Bank L1 (top) and BFCL V3 parallel function call (bottom). Results demonstrate CoALM’s consistent performance compared to other baselines.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | Success | JGA |
|---|---|---|
| CoALM 8B (ours) | 51.6 | 30.4 |
| CoALM 70B (ours) | 69.4 | 43.8 |
| CoALM 405B (ours)<sup>*</sup> | 66.7 | 38.8 |
| Hammer 2.0 7B | 23.5 | 21.7 |
| ToolAce | 18.0 | 34.4 |
| Granite-20B-Code | 10.7 | 21.8 |
| CodeActAgent | 9.5 | 20.2 |
| Llama 3.1 8B Instruct | 19.9 | 26.3 |
| Llama 3.3 70B Instruct | 67.6 | 40.8 |
| Mistral-7B-Instruct-v0.3 | 31.2 | 27.0 |
| FNCTOD [Li et al. (2024)](<https://arxiv.org/pdf/2502.08820.pdf>) | 44.4 | 37.9 |
| NC-Latent-TOD [King and Flanigan (2024)](<https://arxiv.org/pdf/2502.08820.pdf>) | 68.3 | 39.7 |
| GPT 3.5 Turbo [Hudeček and Dusek (2023)](<https://arxiv.org/pdf/2502.08820.pdf>) | - | 13.5 |
| GPT4o-mini | 69.9 | 38.4 |
| GPT4o | 75.5 | 36.9 |{{< /table-caption >}}
> 🔼 표 2는 MultiWOZ 2.4 대화 벤치마크에서 다양한 모델들의 성능을 비교 분석한 결과를 보여줍니다. MultiWOZ 2.4는 호텔 예약, 식당 예약, 교통편 예약 등 여러 도메인에 걸친 복잡한 대화 시나리오를 포함하고 있습니다.  표에는 각 모델의 성공률(Success)과 공동 목표 달성률(JGA)이 제시되어 있으며, 가장 높은 점수는 굵은 글씨체로 강조 표시되어 있습니다.  CoALM 405B 모델의 경우 아직 훈련이 완료되지 않은 중간 지점(checkpoint)의 결과이므로, (*) 표시로 구분되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: MultiWOZ 2.4 Benchmark Results. Performance comparison across models on MultiWOZ 2.4 dialogue benchmark. Best scores are highlighted with bold. The asterisk (*) on CoALM 405B denotes the checkpoint from one completed epoch, as the model is still under training.
> </details>

{{< table-caption >}}
| Model | Rouge-L* (L-1) | Rouge-L* (L-2) | Rouge-1 (L-1) | Rouge-1 (L-2) | Rouge-2 (L-1) | Rouge-2 (L-2) | BLEU-4 (L-1) | BLEU-4 (L-2) |
|---|---|---|---|---|---|---|---|---|
| CoALM 8B (ours) | 92.8 | 81.9 | 94.1 | 81.2 | 91.9 | 76.4 | 89.4 | 69.7 |
| CoALM 70B (ours) | 92.7 | 83.2 | 94.5 | 82.7 | 92.5 | 78.9 | 89.5 | 72.4 |
| CoALM 405B (ours)* | 93.4 | 77.8 | 94.5 | 77.1 | 92.4 | 71.9 | 90.3 | 64.4 |
| Llama 3.1 8B Instruct | 72.7 | 75.2 | 84.0 | 81.4 | 79.8 | 76.3 | 62.3 | 65.1 |
| Qwen2.5 7B Instruct | 84.3 | 73.9 | 88.9 | 78.5 | 84.6 | 71.2 | 76.4 | 64.2 |
| Hammer 2.0 7B | 90.1 | 74.0 | 92.3 | 74.1 | 89.9 | 68.5 | 85.4 | 58.4 |
| ToolAce | 81.5 | 63.6 | 88.8 | 71.3 | 85.0 | 63.0 | 76.1 | 67.0 |
| Granite-20B-Code | 60.3 | 45.7 | 64.7 | 48.9 | 59.5 | 43.4 | 43.8 | 29.3 |
| Fnc-TOD 13B | 3.9 | 3.3 | 22.1 | 23.4 | 8.0 | 9.2 | 1.5 | 1.1 |
| LDST | 8.3 | 7.1 | 12.8 | 11.6 | 2.7 | 2.4 | 6.2 | 5.7 |
| tod-zero-bqag3oyb | 3.7 | 4.2 | 11.5 | 12.4 | 1.1 | 2.2 | 1.0 | 0.9 |
| nc-latent-tod-step-2 | 3.2 | 3.2 | 14.3 | 13.3 | 3.2 | 1.5 | 0.8 | 0.8 |{{< /table-caption >}}
> 🔼 본 표는 API-Bank 기능 호출 벤치마크에서 다양한 모델의 성능을 비교 분석한 결과를 보여줍니다.  MultiWOZ와 달리 API 호출에 초점을 맞춘 API-Bank 데이터셋을 사용하여 각 모델의 기능 호출 정확도를 평가합니다.  Rouge-L, Rouge-1, Rouge-2, BLEU-4 지표를 사용하여 모델의 성능을 다각적으로 평가하며,  최고 점수는 굵은 글씨체로, 두 번째로 높은 점수는 밑줄 친 글씨체로 표시됩니다.  CoALM 405B 모델은 아직 훈련 중이므로 한 에포크 완료 시점의 결과만 제시됩니다.
> <details>
> <summary>read the caption</summary>
> Table 3: API-Bank Benchmark Results. Performance comparison across models on API-Bank function calling benchmark. Best scores are highlighted with bold and the second-best results are underlined. The asterisk (*) on CoALM 405B denotes one completed epoch, as the model is still in the training process.
> </details>

{{< table-caption >}}
| Model | Overall Acc | Non-Live AST Acc | Non-Live Exec Acc | Live Acc | Multi Turn Acc | Relevance Detection | Irrelevance Detection |
|---|---|---|---|---|---|---|---| 
| Mistral-7B-Instruct-v0.3 | 38.35% | 56.33% | 63.77% | 57.31% | 0.25% | 77.78% | 41.84% |
| Llama-3.1-8B-Instruct | 49.84% | 84.25% | 79.75% | 60.33% | 10.25% | 75.61% | 47.92% |
| Llama-3.3-70B-Instruct | 51.36% | 84.85% | 90.05% | 62.51% | 7.25% | 95.12% | 48.33% |
| ToolAce | 52.55% | 82.19% | 86.98% | 71.08% | 0.88% | 70.73% | 87.29% |
| Hammer2.0-7b | 52.13% | 86.94% | 83.66% | 71.17% | 0.38% | 95.12% | 73.20% |
| Llama-3.1-405B-Instruct | 56.38% | 89.71% | 84.70% | 70.77% | 11.75% | 88.89% | 70.86% |
| GPT-4o-mini (2024-07-18) | 59.40% | 86.52% | 85.05% | 73.26% | 19.00% | 78.05% | 76.97% |
| GPT-4o (2024-08-06) | 59.83% | 70.08% | 60.79% | 76.41% | 34.62% | 51.22% | 87.34% |
| CoALM 8B (ours) | 54.11% | 85.17% | 78.61% | 72.59% | 7.00% | 77.78% | 83.00% |
| CoALM 70B (ours) | 60.49% | 82.94% | 81.36% | 72.19% | 26.25% | 72.22% | 85.36% |
| CoALM 405B (ours)<sup>∗</sup> | 63.34% | 90.46% | 84.75% | 74.59% | 28.25% | 100.00% | 72.26% |{{< /table-caption >}}
> 🔼 표 4는 BFCL V3 기능 호출 벤치마크에 대한 성능 비교 결과를 보여줍니다.  CoALM 모델이 다른 모델들에 비해 우수한 성능을 보이는 것을 보여주는 표입니다.  특히, CoALM 405B는 아직 학습이 완료되지 않은 상태임에도 불구하고 상위권 성능을 기록하고 있습니다.  표에는 정확도, AST 정확도, 실행 가능한 함수 정확도, 다중 턴 정확도, 관련성 감지, 무관성 감지 등 여러 지표가 포함되어 있습니다. 가장 좋은 결과는 굵게 표시하고, 두 번째로 좋은 결과는 밑줄이 그어져 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: BFCL V3 Benchmark Results. Performance comparison on the BFCL V3 function-calling benchmark. The best results are highlighted in bold, while the second-best results are underlined. The asterisk (*) on CoALM 405B denotes one completed epoch, as the model continues training.
> </details>

{{< table-caption >}}
| Model | TOD Task |  | Function Calling Tasks |  |  |  | 
|---|---|---|---|---|---|---| 
|  | **MultiWOZ 2.4** |  | **API-Bank** |  | **BFCL-V3** |  | 
|  | **Success** | **DST** | **Rouge-L1** | **Rouge-L2** | **Overall Success** |  | 
| Llama 3.1 8B Instruct | 19.9 | 26.3 | 72.7 | 75.2 | 49.8 |  | 
|  + CoALM-IT w/o LA | 46.0 (26.1 ↑, 5.6 ↓) | 28.5 (2.2 ↑, 1.9 ↓) | 45.5 (27.2 ↓, 47.3 ↓) | 48.8 (26.4 ↓, 33.1 ↓) | 35.4 (14.4 ↓, 18.3 ↓) |  | 
|  + CoALM-IT w/o TOD | 42.0 (22.1 ↑, 9.6 ↓) | 19.4 (6.9 ↓, 11.0 ↓) | 92.7 (20.0 ↑, 0.1 ↓) | 78.9 (13.7 ↑, 3.0 ↓) | 54.1 (4.3 ↑, 0.4 ↑) |  | 
|  + CoALM-IT w/o CRA | 50.0 (30.1 ↑, 1.6 ↓) | **34.5** (8.2 ↑, 4.1 ↑) | 91.3 (18.6 ↑, 1.5 ↓) | 78.8 (3.6 ↑, 3.1 ↓) | **56.6** (10.6 ↑, 2.9 ↑) |  | 
| CoALM 8B | **51.6** | 30.4 | **92.8** | **81.9** | 53.7 |  | {{< /table-caption >}}
> 🔼 표 5는 CoALM 미세 조정 중 특정 도메인 데이터셋을 제외했을 때의 영향을 보여주는 실험 결과를 보여줍니다.  'w/o'는 미세 조정 중 해당 데이터셋을 제외했음을 나타냅니다. 각 행은 기준 모델(Llama) 및 최종 모델(CoALM)과 비교하여 성능 변화를 보여줍니다. 괄호 안의 값은 Llama 모델과 CoALM 모델의 성능 변화를 각각 나타냅니다. 성능 향상은 녹색으로, 성능 저하는 빨간색으로 표시됩니다.  즉, 이 표는 CoALM 모델의 성능에 각 데이터셋(TOD, LA, CRA)이 얼마나 기여하는지를 정량적으로 보여주는 표입니다. 
> <details>
> <summary>read the caption</summary>
> Table 5: Dataset Domain Effects. Experimental results highlighting the impact of excluding specific domain datasets during CoALM fine-tuning. w/o indicates excluding the corresponding dataset during fine-tuning. Each row displays performance changes in parentheses with respect to base model (Llama) and final model (CoALM), i.e. (ΔΔ\Deltaroman_Δ Llama, ΔΔ\Deltaroman_Δ CoALM). Performance gains are highlighted in green, while drops are marked in red.
> </details>

{{< table-caption >}}
| User | Thought1 | API | API Input Arguments | API Result | Thought2 | System |
|---|---|---|---|---|---|---|
| You are an advanced AI assistant specializing in conversational dialogues. |  |  |  |  |  |  |
| You have access to a variety of services and APIs to assist users with their requests and your goal is to provide helpful and informative responses to user queries and commands. |  |  |  |  |  |  |
| You can interact with multiple services and APIs to fulfill user requests. |  |  |  |  |  |  |
| Your responses should be natural, informative, and tailored to the user’s needs. |  |  |  |  |  |  |
| # Task Information: |  |  |  |  |  |  |
| - You are asked to create a dataset in the format: User - Thought1 - API - API Input Arguments - API Result - Thought2 - System, or User - Thought - System. |  |  |  |  |  |  |
| - For the given # User Input, generate a multi-turn dialogue that follows this format, with each turn exhibiting realistic context reasoning, thought processes, and API interaction where applicable. |  |  |  |  |  |  |
| - The dialogues should be converted to follow a specific # Output Format, which includes reasoning on whether an API call is needed or if the system can respond directly. |  |  |  |  |  |  |
| - If the system decides that an API call is necessary, use this format: User - Thought1 - API - API Input Arguments - API Result - Thought2 - System. |  |  |  |  |  |  |
| - Call the right API from # Avaliable Functions and provide the necessary input arguments to fulfill the user’s request. |  |  |  |  |  |  |
| - If you think a function argument is not necessary, you can skip it. Don’t provide unnecessary arguments and None values. |  |  |  |  |  |  |
| - Ensure that the API calls are used logically and that the dialogue remains coherent and natural throughout the exchange. |  |  |  |  |  |  |
| - If the system determines that an API call is not necessary, use this format: User - Thought - System. |  |  |  |  |  |  |
| - Include intermediate thoughts where appropriate to capture the model’s internal reasoning, and clearly separate the different components of the format. |  |  |  |  |  |  |
| # Available Functions: |  |  |  |  |  |  |
| 1. CheckBalance(account_type) |  |  |  |  |  |  |
| 2. TransferMoney(account_type, amount, recipient_account_name) |  |  |  |  |  |  |
| . |  |  |  |  |  |  |
| . |  |  |  |  |  |  |
| . |  |  |  |  |  |  |
| 52. FindAttractions(location) |  |  |  |  |  |  |
| 53. GetWeather(city) |  |  |  |  |  |  |
| # Output Format: |  |  |  |  |  |  |
| - If an API Call is Needed: |  |  |  |  |  |  |
|  User: [User Input] |  |  |  |  |  |  |
|  Thought1: [I need to call an API] |  |  |  |  |  |  |
|  API Name: [API Call Name: CheckBalance(), TransferMoney(),..., FindAttractions(), GetWeather()] |  |  |  |  |  |  |
|  API Input: [The input parameters for the API] |  |  |  |  |  |  |
|  API Result: [API output result] |  |  |  |  |  |  |
|  Thought2: [2nd thought after API Result that ensure if the information is enough before the system response] |  |  |  |  |  |  |
|  System: [Your system response here] |  |  |  |  |  |  |
| - If an API Call is Not Needed: |  |  |  |  |  |  |
|  User: [User Input] |  |  |  |  |  |  |
|  Thought: [I don’t need an API and I want to respond to the user] |  |  |  |  |  |  |
|  System: [Your system response here] |  |  |  |  |  |  |
| Below is an example of the format: |  |  |  |  |  |  |
| # Example: |  |  |  |  |  |  |
| User: Add Don and Sherri to my "Meditate to Sounds of Nature" playlist. | Thought1: The user wants to add two artists to a specific playlist. I’ll need to extract the playlist name and the artists’ names. | API Name: AddToPlaylist | API Input: 'playlist_name': 'Meditate to Sounds of Nature', 'artists': Don Sherri | API Result: 'status': 'success', 'message': 'Don and Sherri have been added to your playlist.' | Thought2: The API call was successful, and the artists were added to the playlist. I need to inform the user about this. | System: Don and Sherri have been successfully added to your "Meditate to Sounds of Nature" playlist. Enjoy your music! |
| User: Thank you for adding them. I think I can add more songs to the playlist. | Thought: I don’t need an API call for that, I want to respond to the user. |  |  |  |  | System: Would you like to add more songs? |
| User: Yes, please add "Calm River" to the playlist. | Thought1: The user wants to add another song to the playlist. I’ll note the song title and proceed with the request. | API Name: AddToPlaylist | API Input: 'playlist_name': 'Meditate to Sounds of Nature', 'songs': Calm River | API Result: 'status': 'success', 'message': 'Calm River has been added to your playlist.' | Thought2: The song was successfully added. I should let the user know. | System: "Calm River" has been successfully added to your "Meditate to Sounds of Nature" playlist. Would you like to do anything else? |
| User: No, that’s all for now. Thank you! | Thought: The user is satisfied and doesn’t need further assistance. I should acknowledge their gratitude. |  |  |  |  | System: You’re welcome! If you need anything else, feel free to ask. Enjoy your relaxing music! |
| # User Input: |  |  |  |  |  |  |{{< /table-caption >}}
> 🔼 이 표는 논문의 4.1절 '대화형 에이전트 데이터셋 생성'에서 사용된, GPT-4를 이용해 생성된 SGD(Stochastic Gradient Descent) 파인튜닝 샘플 생성을 위한 API 기반 대화 프롬프트를 보여줍니다.  표에는 모든 대화에서 사용된 함수만 포함되어 있으며, 함수의 개수가 많기 때문에 모든 함수를 다 포함하지는 않았습니다.  프롬프트는 사용자의 질의에 대한 응답을 생성하기 위해 다양한 API와 상호작용하는 방법을 모델에게 가르치는 것을 목표로 합니다.  여기에는 사용자의 의도를 파악하고, 적절한 API를 선택하고, 필요한 인수를 제공하는 방법, 그리고 일관성 있고 자연스러운 대화를 유지하는 방법 등이 포함됩니다.  결과적으로, 이 프롬프트는 다양한 대화 시나리오를 생성하여 모델의 대화 능력과 API 활용 능력을 향상시키는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 6: API-driven conversation prompt to generate SGD fine-tuning samples with GPT4-o. Only functions used across all dialogues are included due to their large number.
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