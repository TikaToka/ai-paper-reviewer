---
title: "MM-IQ: Benchmarking Human-Like Abstraction and Reasoning in Multimodal Models"
summary: "MM-IQ 벤치마크는 다양한 추론 유형을 포괄하는 2710개의 과제로 구성되어, 최첨단 다중 모드 모델의 추상적 사고 및 추론 능력을 평가합니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Multimodal Reasoning", "🏢 Tencent Hunyuan Team",]
showSummary: true
date: 2025-02-02
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.00698 {{< /keyword >}}
{{< keyword icon="writer" >}} Huanqia Cai et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-04 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.00698" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.00698" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

현재 인공지능 연구는 **다중 모드 모델(LMMs)**의 추상적 사고와 추론 능력을 정량적으로 평가할 수 있는 체계적인 벤치마크가 부족합니다. 기존 벤치마크는 특정 작업에 초점을 맞추거나, 언어 능력이나 특정 영역 지식에 의존하는 경우가 많아, 핵심적인 인지 능력을 제대로 평가하지 못한다는 문제가 있습니다.

본 연구에서는 이러한 문제를 해결하기 위해, **인간의 지능 검사 방식을 모방하여 언어 및 영역 지식에 의존하지 않는 포괄적인 평가 프레임워크인 MM-IQ**를 제안합니다. MM-IQ는 8가지 다양한 추론 패러다임을 포함하는 2710개의 엄선된 문제들로 구성되어 있으며, 최첨단 LMMs의 추론 능력을 평가한 결과, **인간 수준에는 크게 미치지 못하는 것**으로 나타났습니다. 이는 **현재의 다중 모드 모델들이 기본적인 인간 추론 능력을 충분히 모방하지 못한다는 점**을 시사하며, **새로운 패러다임의 발전이 필요함**을 강조합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} MM-IQ는 다양한 추론 유형을 포괄하는 종합적인 벤치마크로, 인간 수준의 추론 능력을 갖춘 다중 모드 모델 개발을 위한 새로운 기준을 제시합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 현존하는 최첨단 다중 모드 모델들은 MM-IQ에서 인간 수준의 성능에 크게 못 미치는 것으로 나타났습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} MM-IQ 데이터셋과 분석 결과는 다중 모드 모델의 추론 능력 개선을 위한 향후 연구 방향을 제시합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **다중 모드 모델의 추상적 사고 및 추론 능력을 평가하기 위한 새로운 벤치마크인 MM-IQ**를 제시하여, **현존하는 최첨단 모델의 한계를 드러내고 향후 연구 방향을 제시**한다는 점에서 중요합니다. 특히, 인간의 추론 능력에 대한 이해를 바탕으로 **다양한 추론 패러다임을 포괄적으로 평가**하는 것은 인공지능 발전에 큰 영향을 미칠 수 있습니다. 또한, 본 연구는 **오픈소스 및 독점 모델 모두를 평가하여 객관적인 비교 분석**을 제공하고, **향후 연구를 위한 새로운 데이터셋 및 분석 결과**를 제공하여, 관련 분야 연구자들에게 큰 도움을 줄 수 있을 것입니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.00698/x1.png)

> 🔼 그림 1은 MM-IQ 벤치마크의 8가지 추론 패러다임에서 최고 성능의 다중 모드 모델과 사람의 성능(정확도)을 비교한 결과를 보여줍니다. 왼쪽 그래프는 각 패러다임에 대한 정확도를 보여주고, 오른쪽은 MM-IQ의 8가지 추론 패러다임의 시각적 예시들을 보여줍니다.  자세한 내용은 3.2절을 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Figure 1: Left: Performance (accuracy) of top-performing multimodal models and humans across eight reasoning paradigms of MM-IQ. Right: Visual examples of eight reasoning paradigms of MM-IQ (Detailed information can be found in Section 3.2).
> </details>





{{< table-caption >}}
| Input Shape | Geometric | RAVEN* | G-set* | VAP* | SVRT | DOPT* | ARC | MNS | IQTest | MARVEL | MM-IQ |
|---|---|---|---|---|---|---|---|---|---|---|---| 
| **Input Shape** | Geometric | ✓ | ✓ | ✓ |  | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Abstract |  |  |  | ✓ |  |  |  |  | ✓ | ✓ | ✓ |
| Concrete Object |  |  |  |  |  |  |  |  |  |  | ✓ |
| **Problem Configuration** | Raven’s Progressive Matrices [17] | ✓ | ✓ |  |  |  |  |  |  | ✓ | ✓ |
| Visual Analogy [6] |  |  | ✓ |  |  |  |  |  |  | ✓ | ✓ |
| Odd-one-out [15] |  | ✓ |  |  |  |  |  |  | ✓ |  | ✓ |
| Visual Extrapolation [24] |  |  |  |  |  | ✓ |  |  | ✓ | ✓ | ✓ |
| Arithmetic Reasoning [29] |  |  |  |  |  |  |  | ✓ | ✓ |  | ✓ |
| Visual Grouping |  |  |  |  | ✓ |  |  |  |  |  | ✓ |
| **Reasoning Paradigm** | Temporal Movement | ✓ | ✓ |  |  |  | ✓ | ✓ |  |  | ✓ |
| Spatial Relationship |  |  |  |  | ✓ |  | ✓ |  |  | ✓ | ✓ |
| 2D-Geometry |  |  |  |  | ✓ |  |  |  | ✓ | ✓ | ✓ |
| 3D-Geometry |  |  |  |  |  |  |  |  | ✓ | ✓ | ✓ |
| Logical Operation | ✓ |  | ✓ |  |  |  |  |  |  |  | ✓ |
| Concrete Object |  |  |  |  |  |  |  |  |  |  | ✓ |
| Visual Instruction |  |  |  |  |  |  |  |  |  |  | ✓ |
| mathematics | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |
| Dataset Size | 14,000 | 1,500 | 100,000 | 23 | 95,200 | 600 | - | 228 | 770 | 2,710 |{{< /table-caption >}}

> 🔼 표 1은 MM-IQ 벤치마크와 관련된 기존 벤치마크들을 비교 분석한 표입니다. MM-IQ와 RAVEN, G-set, VAP, SVRT, DOPT, ARC, MNS, IQTest, MARVEL 등의 벤치마크들을 입력 형태(기하학적, 추상적, 구체적 객체), 문제 구성(레이븐의 점진적 행렬, 시각적 유추, 홀수 찾기 등), 추론 패러다임(시간적 움직임, 공간적 관계, 논리적 연산 등) 세 가지 측면에서 비교하여 MM-IQ의 특징과 강점을 보여줍니다. 특히, 기존 벤치마크들이 절차적 콘텐츠 생성을 통해 자동으로 생성된 데이터를 사용하는 반면, MM-IQ는 다양성을 확보하기 위해 실제 시험 문제들을 활용했다는 점을 강조합니다.  MM-IQ가 벤치마크 규모, 추론 패러다임의 다양성, 그리고 데이터의 질적 수준 면에서 우수함을 보여주는 표입니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparison between our MM-IQ and related benchmarks: RAVEN∗∗\ast∗ [27], G-set∗∗\ast∗ [15], VAP∗∗\ast∗ [6], SVRT [5], DOPT∗∗\ast∗ [24], ARC [4], MNS [29], IQTest [12], MARVEL [7]. ∗∗\ast∗ denotes that the dataset is automatically produced through procedural content generation.
> </details>





### In-depth insights


#### MM-IQ Benchmark
MM-IQ 벤치마크는 **다양한 모드의 추론 능력을 평가하기 위한 종합적인 평가 프레임워크**입니다. 기존 벤치마크와 달리, 언어 능력이나 특정 분야 지식과 같은 요소를 배제하고 **추상적 사고와 추론 능력 자체에 초점**을 맞춘 점이 특징입니다. **8가지의 서로 다른 추론 패러다임**을 포함하며, 각 패러다임은 다양한 시각적 퍼즐을 통해 평가됩니다.  **인간 수준의 추론 능력과 비교**했을 때, 최첨단 다중 모드 모델조차도 인간 수준에 크게 못 미치는 성능을 보이는데, 이는 **현재 기술의 한계**를 보여줍니다.  **MM-IQ는 다중 모드 모델의 추론 능력 향상을 위한 중요한 기준**을 제시하며, **향후 연구 방향**을 제시하는 데 중요한 역할을 할 것으로 예상됩니다. 특히, **추상적 사고 능력과 시각적 이해 능력의 개선**이 중요한 과제로 제기됩니다.

#### Human-like Reasoning
본 논문은 인간과 유사한 추론 능력을 평가하기 위한 벤치마크인 MM-IQ를 제시합니다.  **MM-IQ는 다양한 추론 패러다임을 포괄하는 2710개의 세심하게 기획된 문제들로 구성**되어, 언어 능력이나 특정 도메인 지식에 의존하지 않고 추상적 사고와 추론 능력을 측정하는 데 초점을 맞춥니다.  **기존의 벤치마크들이 특정 과제에 국한된 반면, MM-IQ는 인간의 IQ 테스트 원리를 활용하여 추상적 사고 능력을 보다 포괄적으로 평가**합니다.  실험 결과, 최첨단 다중 모달 모델들조차 MM-IQ에서 인간 수준의 성능에는 훨씬 못 미치는 것으로 나타났습니다.  이는 **현재의 다중 모달 모델들이 인간과 같은 추상적 추론 능력을 갖추지 못하고 있음**을 시사하며, 인간 수준의 인지 능력에 도달하기 위한 새로운 접근법의 필요성을 강조합니다.  **특히, 논리적 연산과 공간 관계 파악 등에서 모델의 성능이 현저히 낮았던 점은 향후 연구 방향을 제시**합니다.  추론 과정에 대한 상세한 설명이 모델의 성능 향상에 도움이 될 수 있다는 점도 주목할 만합니다.

#### LMM Evaluation
본 논문은 다양한 모드(텍스트, 이미지 등)를 처리하는 대규모 다중 모드 모델(LMM)의 평가에 대해 심도있게 논의합니다. **기존의 벤치마크들이 특정 작업에 치우쳐 LMM의 핵심 인지 능력을 제대로 평가하지 못하는 한계점**을 지적하며, 추상적 사고와 추론 능력을 측정하는 새로운 벤치마크의 필요성을 강조합니다. 특히 **인간의 지능 지수(IQ) 테스트의 원리를 차용하여 언어나 도메인 지식에 의존하지 않는 객관적인 평가 방식**을 제안합니다. 새로운 벤치마크는 다양한 추론 패러다임을 포괄하며, LMM의 성능을 인간 수준과 비교 분석하여 **현재 LMM의 추상적 추론 능력이 미흡함**을 보여줍니다.  나아가 **LMM의 오류 분석을 통해 추론 과정의 결함, 시각적 이해 부족, 추상적 패턴 인식의 어려움 등을 구체적으로 파악**하고, 향후 연구 방향을 제시합니다. 이는 **LMM의 인지 능력 향상**을 위한 중요한 시사점을 제공합니다.

#### Failure Analysis
본 논문의 "실패 분석" 부분은 MM-IQ 벤치마크에서 최첨단 다중모드 모델의 성능 저하 원인을 심층적으로 조사합니다. **세 가지 주요 오류 유형**으로 분류하여 분석하는데,  잘못된 추론, 잘못된 시각적 이해, 잘못된 최종 답변입니다. 특히, **잘못된 추론은 오류의 상당 부분**을 차지하며, 모델이 복잡한 시각적 패턴을 간단한 규칙으로 단순화하거나, 고차원적인 추상적 규칙을 추출하지 못하는 데서 기인함을 보여줍니다. **시각적 이해 부족은 특정 추론 유형(예: 논리 연산, 시간적 움직임, 공간적 관계)**에서 두드러지게 나타나며, 이는 모델이 복잡한 시각 정보를 정확하게 해석하는 데 어려움을 겪는다는 것을 시사합니다. 마지막으로, **일부 모델은 설명 없이 답변만 제시할 경우 성능이 저하되는 현상**을 보이는데, 이는 상세한 추론 과정을 생성하는 것이 큰 모델의 성능 향상에 도움이 될 수 있음을 의미합니다. 이러한 분석 결과는 다중모드 모델의 추상적 추론 능력 향상을 위한 중요한 시사점을 제공하며, **구체적인 시각적 이해 능력 향상, 고차원 추상적 패턴 인식 능력 강화, 보다 구조화된 응답 생성 능력 개발**이 필요함을 강조합니다.

#### Future of LMMs
LMM(대규모 다중 모달 모델)의 미래는 **추상적 사고와 추론 능력의 향상**에 달려 있습니다. MM-IQ 벤치마크에서 드러난 LMM의 한계는 인간 수준의 추상적 사고와 추론 능력을 구현하는 데 필요한 핵심적인 능력이 부족하다는 것을 보여줍니다. **보다 복잡하고 다양한 추론 패러다임**을 다루는 새로운 벤치마크 개발과 **구조화된 응답 생성 및 고차원 추상적 규칙 추출** 능력 향상, 그리고 **시각적 이해 능력 강화**를 통해 LMM의 성능을 개선할 수 있습니다. 특히, **시각 정보에 대한 보다 정교한 이해**와 추론 과정에 대한 상세한 설명을 생성하는 능력은 LMM의 추상적 사고 및 추론 능력 향상에 중요한 역할을 할 것입니다.  **설명적인 응답**은 큰 모델의 성능 향상에 도움이 되는 반면, 작은 모델은 간결한 응답으로 더 나은 성능을 보일 수 있습니다.  궁극적으로, **인간 수준의 인지 능력에 근접**하기 위해서는 패러다임 전환적인 발전이 필요하며, 이는 LMM 분야의 지속적인 연구와 개발을 통해 가능해질 것입니다.  **데이터 다양성 확보**를 위한 노력도 필수적입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.00698/extracted/6172197/imgs/error_analysis_stacked.png)

> 🔼 그림 2는 논리 연산 패러다임의 시각적 예시입니다. 이 그림은 사용자가 주어진 그림에서 추상적인 논리 연산(예: AND, OR, XOR)을 파악하여 일반적인 논리 규칙을 도출하고, 이를 적용하여 필요한 그림을 식별하는 논리 추론 능력을 평가하기 위한 것입니다.  그림은 AND 연산을 포함하는 추론 과정을 보여줍니다.  즉, 여러 2차원 기하학적 도형들의 속성 패턴을 이해하고(예: 대칭성, 직선성, 개방성, 폐쇄성), 이러한 속성을 기반으로 유추 또는 외삽을 수행하는 능력을 평가합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: A visualized example of logical operation paradigm.
> </details>



![](https://arxiv.org/html/2502.00698/extracted/6172197/imgs/data_distribution.png)

> 🔼 그림 3은 논문의 수학적 추론 패러다임을 보여주는 예시입니다.  문제는 주어진 숫자 패턴을 파악하고, 물음표에 들어갈 적절한 숫자를 선택하는 것입니다.  이 문제는 기본적인 산술 연산 능력과 수학적 추론 능력을 평가합니다.  이 그림은 시각적 정보를 기반으로 수학적 문제를 해결하는 다중 모드 모델의 능력을 평가하기 위한 MM-IQ 벤치마크의 일부입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: A visualized example of mathematics paradigm.
> </details>



![](https://arxiv.org/html/2502.00698/extracted/6172197/imgs/error_types_proportions.png)

> 🔼 그림 4는 논문의 2D 기하학 추론 패러다임을 시각적으로 보여주는 예시입니다. 그림은 여러 가지 2D 도형의 패턴을 보여주고, 모델이 이 패턴을 이해하고 다음 도형을 예측할 수 있는지 평가하는 데 사용됩니다. 이는 단순히 도형을 인식하는 것을 넘어, 도형의 속성(대칭성, 직선, 개방성, 폐쇄성 등)을 이해하고 추론하는 능력을 평가합니다. 따라서, 모델의 추상적 추론 능력과 일반화 능력을 평가하는 데 유용한 지표가 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: A visualized example of 2D-geometry paradigm.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | Mean | LO | Math | 2D-G | 3D-G | VI | TM | SR | CO |
|---|---|---|---|---|---|---|---|---|---| 
| **Open-Source LMMs** |  |  |  |  |  |  |  |  |  |
| LLaVA-1.6-7B [8] | 19.45 | 24.22 | 20.34 | 17.92 | 15.83 | 20.00 | 18.23 | 17.82 | 18.42 |
| Deepseek-vl-7b-chat [3] | 22.17 | 19.53 | 20.30 | 22.25 | 27.39 | 35.56 | 23.72 | 24.75 | 15.79 |
| Qwen2-VL-72B-Instruct [23] | 26.38 | 24.74 | 24.40 | 28.60 | 27.39 | 24.44 | 26.93 | 32.67 | 23.68 |
| QVQ-72B-Preview [21] | 26.94 | 28.91 | 25.59 | 29.23 | 26.38 | 26.67 | 25.43 | 22.77 | 34.21 |
| **Proprietary LMMs** |  |  |  |  |  |  |  |  |  |
| GPT-4o [1] | 26.87 | 25.52 | 25.70 | 28.32 | 27.64 | 26.67 | 25.69 | 27.72 | 50.00 |
| Gemini-1.5-Pro-002 [20] | 26.86 | 19.53 | 27.43 | 28.03 | 25.88 | 24.44 | 31.17 | 25.74 | 39.47 |
| Claude-3.5-Sonnet [2] | 27.49 | 23.41 | 29.48 | 26.60 | 24.37 | 35.56 | 25.69 | 27.72 | 42.11 |
| Human Performance | 51.27 | 61.36 | 45.03 | 60.11 | 47.48 | 46.67 | 55.61 | 36.63 | 65.79 |{{< /table-caption >}}
> 🔼 표 2는 MM-IQ 벤치마크에서 다양한 모델과 사람의 성능을 백분율(%)로 비교한 표입니다.  모델의 성능은 논리 연산(LO), 2차원 기하학(2D-G), 3차원 기하학(3D-G), 시각적 지시(VI), 시간적 움직임(TM), 공간적 관계(SR), 구체적 객체(CO) 등 8가지 추론 패러다임별로 평가되었습니다.  각 열은 특정 추론 유형에 대한 정확도를 나타내며, 마지막 열은 모든 유형에 대한 평균 정확도를 보여줍니다.  이 표는 인간과 최첨단 다중 모달 모델의 추론 능력을 비교 분석하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Model and Human Performance on MM-IQ (%). Abbreviations adopted: LO for Logical Operation; 2D-G for 2D-Geometry; 3D-G for 3D-Geometry; VI for Visual Instruction; TM for Temporal Movement; SR for Spatial Relationship; CO for Concrete Object.
> </details>

{{< table-caption >}}
| Model | Generation Setup |
|---|---| 
| Claude-3.5-Sonnet-2024-06-20 | temperature = 1.0, output_token_limit = 8,192, top_p = 1.0 |
| GPT-4o-2024-08-06 | temperature = 1.0, output_token_limit = 16,384, top_p = 1.0 |
| Gemini-1.5-Pro-002 | temperature = 1.0, output_token_limit = 8,192 |
| DeepSeek-vl-7b-chat | temperature = 1.0, output_token_limit = 2,048, do_sample = False, top_p = 1.0 |
| LLaVA-1.6-7B | temperature = 0, output_token_limit = 2,048 |
| Qwen2-VL-72B-Instruct | temperature = 1.0, output_token_limit = 8,192, top_p = 0.001, top_k = 1, do_sample = True, repetition_penalty = 1.05 |
| QVQ-72B-Preview | temperature = 0.01, output_token_limit = 8,192, top_p = 0.001, top_k = 1, do_sample = True, repetition_penalty = 1.0 |{{< /table-caption >}}
> 🔼 표 3은 다양한 대규모 다중 모달 언어 모델(LMM)에 대한 생성 매개변수를 보여줍니다.  각 모델에 대해 온도, 출력 토큰 제한, top_p 또는 top_k 와 같은 생성 매개변수가 나열되어 있습니다. 이 설정은 모든 LMM에 대해 공정한 비교를 위해 동일하게 유지되었습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Generating parameters for various LMMs.
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