---
title: "Test-time Computing: from System-1 Thinking to System-2 Thinking"
summary: "테스트 시간 컴퓨팅을 활용하여 대규모 언어 모델의 추론 능력을 시스템 1 사고에서 시스템 2 사고 수준으로 향상시키는 방법을 제시하는 획기적인 연구!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Soochow University",]
showSummary: true
date: 2025-01-05
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.02497 {{< /keyword >}}
{{< keyword icon="writer" >}} Yixin Ji et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-07 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.02497" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.02497" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/test-time-computing-from-system-1-thinking-to" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

본 연구는 인공지능 분야에서 최근 주목받고 있는 대규모 언어 모델(LLM)의 성능 향상과 복잡한 추론 능력 향상에 초점을 맞추고 있습니다. 특히, LLM이 단순한 패턴 인식(시스템 1 사고)에 의존하는 한계를 극복하고, 인간처럼 복잡한 문제를 다단계 추론을 통해 해결하는 능력(시스템 2 사고)을 갖추도록 하는 데 필요한 테스트 시간 컴퓨팅(Test-time computing) 기법들을 종합적으로 조망하고 있습니다. 기존 연구들은 주로 시스템 1 모델의 한계를 극복하기 위한 다양한 테스트 시간 적응(TTA) 기법에 초점을 맞춰왔습니다. 하지만, 본 연구는 여기서 한 발 더 나아가, 시스템 2 사고를 구현하기 위한 테스트 시간 추론(Test-time reasoning) 기법들을 새롭게 제시함으로써, LLM의 추론 능력 향상에 크게 기여하고 있습니다. 

본 연구에서는 시스템 1에서 시스템 2 사고로의 전환 과정에서 테스트 시간 컴퓨팅이 중요한 역할을 한다는 점을 강조합니다.  **시스템 1 모델의 경우, 테스트 시간 적응(TTA)을 통해 분포 이동 문제를 해결하고 강건성과 일반화 성능을 향상시키는 데 초점을 맞춥니다.** 이를 위해 매개변수 업데이트, 입력 수정, 표현 편집, 출력 보정 등 다양한 방법론이 제시됩니다.  **시스템 2 모델의 경우, 반복적 샘플링, 자기 수정, 트리 탐색 등의 고급 추론 전략을 통해 복잡한 문제 해결 능력을 향상시키는 데 초점을 맞춥니다.**  본 논문은 이러한 시스템 1과 시스템 2 모델에서의 테스트 시간 컴퓨팅 전략들을 체계적으로 정리하고,  향후 연구 방향을 제시함으로써 LLM 분야의 발전에 크게 기여할 것으로 기대됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 시스템 1 및 시스템 2 모델에서 테스트 시간 컴퓨팅의 역할과 중요성을 강조 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 분포 변화에 강건하고 일반화 성능을 향상시키는 다양한 테스트 시간 적응 기법 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 복잡한 추론 문제 해결을 위한 반복 샘플링, 자기 수정, 트리 탐색 등의 테스트 시간 추론 전략 제시 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **테스트 시간 컴퓨팅(Test-time computing)**의 개념을 시스템 1 사고에서 시스템 2 사고로 확장하는 데 중점을 두고 있으며, 이는 **대규모 언어 모델(LLM)**의 성능 향상과 복잡한 추론 문제 해결에 중요한 의미를 가집니다.  **시스템 1 모델의 강건성과 일반화 문제를 해결하기 위한 다양한 테스트 시간 적응(TTA) 기법과 시스템 2 모델의 추론 능력 향상을 위한 테스트 시간 추론(Test-time reasoning) 기법**을 종합적으로 제시함으로써, 향후 연구 방향을 제시하고 있습니다. 특히, **복잡한 추론 문제 해결을 위한 다양한 전략(반복적 샘플링, 자기 수정, 트리 탐색 등)을 체계적으로 정리**하고, **다중 모달 추론 및 효율적인 확장성 확보 방안**을 제시함으로써, LLM 연구 분야의 발전에 크게 기여할 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.02497/x1.png)

> 🔼 그림 1은 논문에서 제시하는 시스템 1과 시스템 2 모델에서의 테스트 시간 컴퓨팅 개념을 보여줍니다. 시스템 1 모델은 훈련 중에 학습된 패턴에 의존하여 제한적인 지각 작업만 수행하는 반면, 시스템 2 모델은 반복적 샘플링, 자기 수정, 트리 탐색을 통해 모델의 추론 능력을 향상시켜 복잡한 문제를 해결합니다. 이 그림은 시스템 1에서 시스템 2 사고로의 전환 과정에서 테스트 시간 컴퓨팅의 중요한 역할을 보여줍니다. 시스템 1 모델은 분포 이동을 해결하고 매개변수 업데이트, 입력 수정, 표현 편집, 출력 보정을 통해 강건성과 일반화를 개선하는 반면 시스템 2 모델은 반복 샘플링, 자기 수정, 트리 탐색을 통해 모델의 추론 능력을 강화합니다.  이 그림은 시스템 1 모델에서 약한 시스템 2 모델, 그리고 강한 시스템 2 모델로의 전환 과정을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Illustration of test-time computing in the System-1 and System-2 model.
> </details>





{{< table-caption >}}
| Category | sub-category | Representative Methods | Tasks | Verifier/Critic | Train-free |
|---|---|---|---|---|---| 
| Repeat Sampling | Majority voting | CoT-SC (2023d) | Math, QA | self-consistency | ✓ |
|  |  | PROVE (2024) | Math | compiler | ✓ |
|  | Best-of-N | Cobbe et al. (2021) | Math | ORM | ✗ |
|  |  | DiVeRSe (2023c) | Math | PRM | ✗ |
| Self-correction | Human feedback | NL-EDIT (2021) | Semantic parsing | Human | ✗ |
|  |  | FBNET (2022) | Code | Human | ✗ |
|  | External tools | DrRepair (2020) | Code | compiler | ✗ |
|  |  | Self-debug (2024c) | Code | compiler | ✓ |
|  |  | CRITIC (2024) | Math, QA, Detoxifying | text-to-text APIs | ✓ |
|  | External models | REFINER (2024) | Math, Reason | critic model | ✗ |
|  |  | Shepherd (2023b) | QA | critic model | ✗ |
|  |  | Multiagent Debate (2023) | Math, Reason | multi-agent debate | ✓ |
|  |  | MAD (2024b) | Translation, Math | multi-agent debate | ✓ |
|  | Intrinsic feedback | Self-Refine (2023) | Math, Code, Controlled generation | self-critique | ✓ |
|  |  | Reflexion (2023) | QA | self-critique | ✓ |
|  |  | RCI (2023) | Code, QA | self-critique | ✓ |
| Tree Search | Uninformed search | ToT (2023) | Planing, Creative writing | self-critique | ✓ |
|  |  | Xie et al. (2023) | Math | self-critique | ✓ |
|  | Heuristic search | RAP (2023) | Planing, Math, Logical | self-critique | ✓ |
|  |  | TS-LLM (2024b) | Planing, Math, Logical | ORM | ✗ |
|  |  | rStar (2024) | Math, QA | multi-agent consistency | ✓ |
|  |  | ReST-MCTS* (2024a) | Math, QA | PRM | ✗ |{{< /table-caption >}}

> 🔼 표 1은 논문의 4.2절 '검색 전략' 에서 다루는 다양한 검색 전략들을 개괄적으로 보여줍니다. 반복적 샘플링, 자기 수정, 트리 검색 등 세 가지 주요 전략과 각 전략 하위에 속하는 여러 방법들을 소개하고 있습니다. 각 방법에 대한 대표적인 연구, 해당 방법이 사용되는 작업 유형, 사용된 검증자/평론가의 종류, 그리고 훈련 없이 사용 가능한지 여부를 명시하여 각 방법의 특징과 차이점을 비교 분석하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Overview of search strategies.
> </details>





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