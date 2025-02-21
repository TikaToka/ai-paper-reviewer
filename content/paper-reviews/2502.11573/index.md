---
title: "InfiR : Crafting Effective Small Language Models and Multimodal Small Language Models in Reasoning"
summary: "InfiR: 효율적인 소형 언어 모델 및 다중 모달 소형 언어 모델을 이용한 추론 성능 향상"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Reallm Labs",]
showSummary: true
date: 2025-02-17
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.11573 {{< /keyword >}}
{{< keyword icon="writer" >}} Congkai Xie et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-20 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.11573" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.11573" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/infir-crafting-effective-small-language" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)은 뛰어난 추론 능력을 보이지만, 높은 계산 비용과 개인 정보 보호 문제로 인해 활용에 제약이 있습니다.  **소규모 모델은 이러한 문제를 해결할 수 있는 유망한 대안**으로 떠오르고 있지만, 추론 능력이 LLM에 비해 떨어지는 것이 과제입니다. 

본 연구는 **InfiR이라는 새로운 훈련 파이프라인**을 제시하여 이 문제를 해결합니다.  InfiR은 소형 모델의 추론 성능을 향상시키는 동시에 개발 비용을 최소화하고 에지 장치 배포를 용이하게 합니다.  **InfiR-1B-Base와 InfiR-1B-Instruct 모델은 10억 개의 매개변수 규모에서 최첨단 성능**을 달성했으며, InfiR-VL-1.6B 모델은 멀티모달 작업에서도 우수한 성능을 보였습니다.  이 연구는 **소규모 모델의 실용성을 높이고 AI 시스템의 접근성을 확대**하는 데 기여합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 소형 언어 모델(SLM)과 다중 모달 소형 언어 모델(MSLM)의 추론 성능 향상 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 경제적인 비용과 에지 장치 배포의 용이성 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 개인 정보 보호에 대한 우려 해소 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **소형 언어 모델(SLM)과 다중 모달 소형 언어 모델(MSLM)**의 추론 능력 향상에 중점을 두고 있으며, **경제적인 비용과 에지 장치 배포의 용이성**을 제공합니다. 이는 AI 시스템의 채택 장벽을 낮추고, **개인 정보 보호**에 대한 우려를 해소하는 데 크게 기여할 수 있습니다. 또한, 제시된 방법론은 다양한 분야의 연구자들에게 적용 가능하며, 향후 연구를 위한 새로운 가능성을 제시합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.11573/x1.png)

> 🔼 본 그림은 논문의 전처리 데이터 파이프라인을 보여줍니다.  먼저, 원시 말뭉치(Raw Corpus)에서 잡음을 제거하기 위해 휴리스틱 필터링(Heuristic Filtering)과 추론 지향적 텍스트 재검색(Reasoning-oriented text recall)이 수행됩니다. 중복 제거(Deduplication) 및 오염 제거(Decontamination) 단계를 거쳐 데이터 품질을 높입니다.  마지막으로, LLaMA3.2-1B 모델을 사용한 비교 실험을 통해 다양한 정제된 데이터셋의 품질이 성능에 미치는 영향을 검증합니다.  즉, 데이터의 질이 모델의 성능에 얼마나 중요한지 보여주는 그림입니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: The pipeline of pretrain data drocesses: heuristic filtering, reasoning-oriented text recall, deduplication, quality assessment and decontamination. Comparative experiments on LLaMA3.2-1B with differently cleaned datasets validate the significance of data quality.
> </details>





{{< table-caption >}}
| Type Source | Datasets |
|---|---| 
| Web Pages | Common crawl, FineWeb-Edu, DCLM |
| Math | InfiMM-WebMath-40B, OpenWebMath, MathCode-Pile, Proof-pile-2, finemath |
| Code | the-Stack-v2, Starcoder |
| General Knowledge | arXiv, StackExchange, peS2o |
| Encyclopedia | Wikipedia |
| Open-Source Instruction | FLAN, Infinity Instruct |{{< /table-caption >}}

> 🔼 표 1은 다양한 벤치마크를 사용한 몇 번의 시도만으로 기본 언어 모델의 성능을 보여줍니다. 표에는 각 모델의 MMLU, GSM8K, MATH, HumanEval, MBPP 점수가 나와 있으며, 각 점수는 해당 논문에서 주장하는 결과와 비교하여 제시되어 있습니다. 괄호 안의 값은 해당 논문에서 주장하는 결과를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Performance of base models on various benchmarks using few-shot evaluation. The values in parentheses indicate the claimed results from the respective papers.
> </details>





### In-depth insights


#### Small Model Reasoning
본 논문은 **소형 언어 모델(Small Language Model, SLM)**의 추론 능력 향상에 중점을 두고 있습니다.  대규모 언어 모델(LLM)은 높은 성능을 보이지만, 높은 계산 비용과 개인 정보 보호 문제를 야기합니다. 이에 반해 SLM은 효율성과 경제성을 갖추면서 경쟁력 있는 추론 능력을 유지하는 것을 목표로 합니다. **새로운 훈련 파이프라인**을 통해 추론 성능을 향상시키고 에지 기기 배포를 용이하게 하여 개발 비용을 최소화합니다.  **전처리 데이터 파이프라인**은 잡음을 줄이고 추론 관련 정보를 보존하는 정교한 필터링 및 품질 평가를 포함합니다. 또한, **최적화된 데이터 믹싱 전략**을 사용하여 모델의 성능과 효율성을 균형 있게 유지합니다.  실험 결과는 SLM이 다양한 추론 작업에서 최첨단 성능을 달성함을 보여줍니다.  **소형 모델의 한계를 극복**하고 실용적인 AI 시스템 개발을 가속화하는데 기여하는 연구입니다.

#### Data Pipeline Design
본 논문에서 제시된 데이터 파이프라인 설계는 **데이터 품질 향상**에 중점을 두고 있습니다.  원시 데이터 수집 후 **중복 제거 및 오염 제거** 과정을 거치며, **휴리스틱 필터링 및 추론 지향적 텍스트 재호출** 기법을 통해 노이즈를 제거하고 추론에 유용한 정보를 선택적으로 추출합니다.  **다양한 도메인의 데이터 균형**을 위해 수집된 데이터는 신중하게 평가 및 분류되고, **데이터 품질 확보**를 위한 다단계 검증 시스템이 도입됩니다. 특히 **소규모 언어 모델의 특성**을 고려하여 효율적인 데이터 처리 및 모델 학습을 위한 최적화 전략이 포함되어 있다는 점이 핵심입니다.  **최종적으로 생성된 고품질 데이터셋**은 모델의 추론 능력 향상에 크게 기여하며,  **비용 효율적인 소규모 모델 개발**에 중요한 역할을 합니다.

#### Multimodal Extension
본 논문에서 제시된 연구는 **멀티모달 확장**에 대한 심도있는 논의를 제공하지 않지만, 멀티모달 기능을 향상시키기 위한 몇 가지 중요한 측면을 간접적으로 보여줍니다.  **비전 인코더와 언어 모델을 통합하는 아키텍처**를 통해 멀티모달 이해 능력을 구축하려는 시도가 엿보입니다.  특히, **이미지와 텍스트 간의 의미적 정합성 확보**를 위한 전처리 과정과, **다양한 멀티모달 데이터셋을 활용한 미세 조정 전략**은 주목할 만합니다.  하지만, 멀티모달 기능 확장에 대한 구체적인 기술적 세부 사항이나, 다른 멀티모달 모델과의 비교 분석이 부족하여, **멀티모달 확장의 효과 및 한계에 대한 명확한 이해**를 얻기에는 다소 제한적입니다.  향후 연구에서는 멀티모달 데이터 처리 및 모델 학습 전략에 대한 더욱 상세한 설명과 실험 결과를 통해, **본 연구의 멀티모달 확장 방식의 장점과 단점을 명확히 밝히고 다른 멀티모달 모델들과의 비교 분석을 통해 그 성능을 객관적으로 평가**하는 것이 필요합니다.

#### Training Strategies
본 논문에서는 효과적인 소형 언어 모델(SLM) 및 다중 모드 소형 언어 모델(MSLM)을 위한 훈련 전략에 대해 심도 있게 논의합니다. **핵심은 제한된 계산 자원 내에서 경쟁력 있는 추론 능력을 유지하는 효율적인 훈련 파이프라인을 개발하는 것**입니다. 이를 위해 **전처리 데이터 파이프라인을 통해 잡음을 줄이고 추론 관련 정보를 보존하는 정교한 데이터 필터링 및 정제 과정**을 거칩니다. 특히, **이 논문에서는 데이터 품질의 중요성을 강조하며, 다양한 도메인에 걸쳐 고품질 데이터를 확보하기 위한 전략들을 제시**합니다.  또한, **모델의 추론 능력 향상을 위한 어닐링(annealing) 데이터 활용 및 지속적인 미세 조정(fine-tuning)**을 통해 성능 향상을 도모합니다.  **다중 모드 모델의 경우, 비전과 언어 정보의 효율적인 정렬을 위한 사전 훈련 및 다양한 모드의 데이터를 활용한 단계적 미세 조정 방식**이 제시됩니다.  **전반적으로, 이 논문에서 제시된 훈련 전략은 모델 크기를 줄이면서도 추론 성능을 극대화하는 데 초점을 맞추고 있으며, 실제 구현 및 배포 가능성까지 고려한 실용적인 접근 방식**을 보여줍니다.

#### Future of Small LLMs
소형 LLM의 미래는 **경제성과 효율성**을 중시하면서도 **강력한 추론 능력**을 유지하는 데 달려 있습니다.  **하드웨어 발전**은 더욱 강력한 소형 모델의 훈련과 배포를 가능하게 할 것이며, **효율적인 훈련 기법**과 **데이터 증강 기술**의 발전은 개발 비용을 낮추고 성능을 향상시킬 것입니다.  **다양한 모달리티**를 지원하는 소형 멀티모달 LLM은 **실세계 애플리케이션**에 대한 접근성을 높일 것이며,  **개인 정보 보호**에 대한 우려를 해소하는 방향으로 발전할 것으로 예상됩니다.  궁극적으로 소형 LLM은 **에지 디바이스**에서의 배포가 용이해지고, **사용자 맞춤형 AI** 제공이 가능해짐으로써 더욱 광범위하게 활용될 것입니다.  **지속적인 연구 개발**을 통해 소형 LLM은 성능과 효율성 면에서 더욱 발전하여, **대규모 모델의 한계를 극복**하고 **실용적인 AI 시스템** 구축에 크게 기여할 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.11573/x2.png)

> 🔼 그림 2는 지도학습 미세조정 데이터 합성 파이프라인을 보여줍니다.  고품질 시드 데이터 세트로 시작하여 지시사항 발전을 통해 데이터를 확장합니다.  Qwen-2.5-32B-Instruct 모델을 사용하여 응답 후보를 생성하고, 보상 모델과 샌드박스 환경을 사용하여 거절 샘플링을 수행합니다.  마지막으로, 큐레이션된 데이터의 품질과 난이도를 평가하고 도메인 레이블을 할당합니다. 이 과정을 통해 다양하고 고품질의 미세조정 데이터를 생성하여 모델의 성능 향상을 도모합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Supervised fine-tuning data synthesis pipeline. The pipeline initiates with a set of high-quality seed data, which is augmented through instruction evolution. Response candidates are generated using the Qwen-2.5-32B-Instruct model, followed by rejection sampling with a reward model and sandbox environment. Finally, we score the curated data for quality and difficulty, and assign domain labels.
> </details>



![](https://arxiv.org/html/2502.11573/extracted/6208609/figures/mslm.png)

> 🔼 그림 3은 다양한 모달리티(텍스트, 이미지)를 처리하는 작은 다중 모달 언어 모델(MSLM)의 학습 과정을 보여줍니다.  먼저 캡션 생성 및 질의응답(QA) 작업을 통해 기본적인 시각-언어 정렬 능력을 학습합니다. 그 다음, 텍스트 렌더링 기법을 사용하여 모델이 텍스트 기반 데이터(수학 문제, 코드 등)를 이미지 형태로 처리하도록 학습합니다.  이후 지시어 미세조정(instruction-tuning)을 통해 수학적 추론과 운영체제(OS) 관련 추론 능력을 향상시켜 최종적으로 복잡한 추론 문제를 해결할 수 있도록 합니다. 그림은 각 단계에서 사용되는 데이터 유형과 모델 구조의 변화를 시각적으로 나타내어 MSLM의 학습 파이프라인을 명확하게 설명합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Illustration of the MSLM training pipeline and the MSLM training details, showcasing the progression from captioning and QA tasks to text rendering, followed by instruction-tuning, culminating in enhanced mathematical and operating system reasoning abilities.
> </details>



![](https://arxiv.org/html/2502.11573/x3.png)

> 🔼 그림 (a)는 논문의 2.1.1절 데이터 수집 부분에서 설명하는 다양한 프로그래밍 언어로 구성된 소스 코드 데이터의 분포를 보여주는 원형 차트입니다. 각 부분은 특정 프로그래밍 언어(예: Python, Java, JavaScript 등)의 소스 코드 데이터 비율을 나타냅니다. 이는 논문에서 개발한 소규모 언어 모델(SLM)과 다중 모드 소규모 언어 모델(MSLM) 학습에 사용된 데이터의 다양성과 균형을 보여주는 중요한 시각적 자료입니다.  이 그림은 다양한 프로그래밍 언어로부터 수집된 데이터의 비중을 보여줌으로써, 모델의 일반화 성능과 다양한 프로그래밍 패러다임에 대한 적응력을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (a)
> </details>



![](https://arxiv.org/html/2502.11573/extracted/6208609/figures/bge_bar.jpg)

> 🔼 그림 (b)는 2500개의 이미지-텍스트 쌍에 대한 유사도 히스토그램을 보여줍니다. 이 히스토그램은 COCO-caption 데이터셋에서 샘플링된 이미지-텍스트 쌍의 유사도를 나타내며, x축은 유사도 점수, y축은 해당 유사도 점수를 가진 쌍의 개수를 나타냅니다. 이 히스토그램을 통해 모델의 이미지와 텍스트 이해 능력에 영향을 미치는 저품질, 저유사도 이미지-텍스트 쌍의 비율을 파악하고, 적절한 유사도 임계값을 설정하는 데 도움이 됩니다. 즉, 0.5 이하의 낮은 유사도를 가진 이미지-텍스트 쌍의 비율이 얼마나 되는지 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b)
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
{{< /gallery >}}