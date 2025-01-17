---
title: "Multimodal LLMs Can Reason about Aesthetics in Zero-Shot"
summary: "대규모 언어 모델(LLM)을 활용하여 제로샷 방식으로 예술 작품의 미적 가치를 평가하는 새로운 방법을 제시하는 연구입니다.  MM-StyleBench라는 고품질 데이터셋을 구축하고, 인간의 미적 선호도를 모델링하여 LLM의 응답과의 상관관계를 분석함으로써 LLM의 한계점을 극복하고, AI와 인간의 미적 판단 간의 차이를 줄였습니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Vision-Language Models", "🏢 Hong Kong Polytechnic University",]
showSummary: true
date: 2025-01-15
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.09012 {{< /keyword >}}
{{< keyword icon="writer" >}} Ruixiang Jiang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-16 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.09012" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.09012" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/multimodal-llms-can-reason-about-aesthetics" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

본 연구는 **대규모 언어 모델(LLM)**이 제로샷 방식으로 예술 작품의 미적 가치를 평가하는 능력을 평가하는 최초의 연구입니다.  기존의 연구들이 미적 평가에 시각적 특징만을 고려했던 것과 달리, 본 연구는 **인간의 미적 인지 과정을 모방하여 LLM의 응답을 평가**했습니다.  이는 단순한 시각적 유사성 측정을 넘어, 문화적 배경, 감정적 영향, 스토리텔링 등 다양한 요소를 고려하는 종합적인 평가 방식으로 해석될 수 있습니다.  기존 방식의 한계를 극복하기 위해, 연구진은 **새로운 벤치마킹 데이터셋(MM-StyleBench)을 제작하고 인간의 미적 선호도를 모델링**하였습니다.



연구진은 **ArtCoT라는 새로운 프롬프팅 기법**을 제안하여 LLM의 미적 판단 능력을 향상시켰습니다.  ArtCoT는 예술 평가 과정을 여러 하위 작업으로 분해하고, 구체적인 언어를 사용하여 LLM의 환각 및 주관적인 응답을 최소화합니다.  실험 결과, ArtCoT는 다양한 LLM에서 인간의 미적 선호도와의 정렬도를 크게 향상시켰습니다.  본 연구는 LLM을 활용한 예술 분야 응용 연구에 중요한 시사점을 제공하며, 향후 AI 기반 예술 창작 및 평가 시스템 개발에 크게 기여할 것으로 예상됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 제로샷 방식으로 예술 작품의 미적 가치를 평가하는 새로운 방법 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} MM-StyleBench라는 고품질 데이터셋 구축 및 인간의 미적 선호도 모델링을 통한 LLM 평가 성능 향상 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} LLM의 환각 문제 해결을 위한 ArtCoT 기법 제시 및 인간의 미적 선호도와의 정렬도 향상 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **다양한 스타일의 예술 작품에 대한 미적 평가에서 대규모 언어 모델(LLM)의 성능을 향상시키는 새로운 방법**을 제시함으로써, **예술 분야에서의 AI 활용 연구에 중요한 발전**을 가져왔습니다. 특히, **인간의 미적 선호도와 AI의 평가 간의 정렬을 높이는 데 초점**을 맞추어 AI 기반 예술 평가의 신뢰도를 높이는 데 기여합니다. 또한, 제시된 방법론은 **다양한 하위 작업으로 예술 평가 과정을 분해하고 구체적인 언어를 사용함으로써 LLM의 환각 문제를 줄이는 데 효과적**임을 보여주었습니다.  이는 향후 AI 기반 예술 창작 및 평가 시스템 개발에 중요한 영향을 미칠 것으로 예상됩니다.  본 연구는 AI와 예술의 융합 분야에 대한 새로운 연구 방향을 제시하며, 향후 AI 모델의 미적 판단 능력 향상과 신뢰성 확보에 중요한 기여를 할 것으로 기대됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.09012/x1.png)

> 🔼 그림 1은 MM-StyleBench 데이터셋에 대한 설명입니다. (a)는 MM-StyleBench 데이터셋에 있는 다양한 속성들의 분포를 보여줍니다. 제안된 데이터셋은 세부적인 속성 주석이 달린 다양한 이미지와 텍스트 프롬프트를 포함합니다. (b)는 MM-StyleBench 데이터셋에 있는 콘텐츠(위쪽)와 스타일(아래쪽) 인스턴스의 예시를 보여줍니다.  즉, (a)는 데이터셋의 다양성을 수치적으로 보여주는 표이고, (b)는 (a)에서 설명된 다양성을 시각적으로 보여주는 예시 이미지들입니다.  이 그림을 통해 독자들은 MM-StyleBench 데이터셋이 얼마나 다양하고 풍부한 데이터를 가지고 있는지 이해할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: The MM-StyleBench dataset. (a) The distribution of different attributes in MM-StyleBench. the proposed dataset contains diverse images and text prompts with detailed attribute annotations. (b) Examples of content (top) and style (bottom) instances in MM-StyleBench.
> </details>





{{< table-caption >}}
| Dataset/Protocol | # Content | # Style | Multimodal | Dense Annotation |
|---|---|---|---|---|
| DiffStyler [2] | 20 | 25 | ✗ | ✗ |
| StyleID [34] | 20 | 40 | ✗ | ✗ |
| LAION-Aesthetics [7] | - | ~50 | ✗ | ✗ |
| ArtBench [35] | - | 10 | ✗ | ✗ |
| StyleBench [36] | 20 | 73 | ✓ | ✗ |
| Ours | 1000 | 1000 | ✓ | ✓ |{{< /table-caption >}}

> 🔼 이 표는 스타일 변환 벤치마킹 데이터셋을 비교한 것입니다. 제안된 MM-StyleBench는 기존 데이터셋보다 훨씬 많은 콘텐츠와 스타일 인스턴스를 제공하며, 세분화된 다중 모드 주석을 포함하고 있습니다.  기존 데이터셋들은 콘텐츠와 스타일 인스턴스 수가 적고, 주석이 부족하여 모델 성능 비교의 재현성과 공정성에 영향을 미쳤습니다. 하지만 MM-StyleBench는 대규모의 다양한 데이터와 상세한 주석을 통해 이러한 문제점을 해결하여 더욱 객관적이고 정확한 비교를 가능하게 합니다.  이를 통해 스타일 변환 모델의 성능을 더욱 정확하게 평가하고 개선하는 데 기여할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> TABLE I: Comparison of representative stylization benchmark datasets. The proposed MM-StyleBench offers significantly more content and style instance, with fine-grained multimodal annotations.
> </details>





### In-depth insights


#### MM-StyleBench Dataset
MM-StyleBench 데이터셋은 **다양한 스타일과 콘텐츠를 포함하는 대규모 다중 모드 스타일링 데이터셋**으로, **정량적이고 해석 가능한 미적 평가 프로토콜의 부재**라는 기존 연구의 한계를 극복하기 위해 고안되었습니다. 이 데이터셋은 단순히 이미지만 포함하는 것이 아니라, **각 이미지에 대한 자세한 속성 주석**(예: 색상 다양성, 요소 밀도, 구성 등)과 **상세한 텍스트 설명**을 함께 제공하여 **다양한 측면에서의 미적 평가를 가능**하게 합니다.  **대규모의 데이터셋 크기**와 **다양한 속성 정보의 풍부함**은 인간의 미적 선호도를 정확하게 모델링하고, 다양한 스타일 변환 모델의 성능을 객관적으로 비교하는 데 중요한 역할을 합니다.  **MLLM(다중 모드 거대 언어 모델) 기반의 미적 평가 연구**에 있어서 MM-StyleBench는 **기준 데이터셋으로서 필수적**이며, 이를 통해 MLLM의 미적 추론 능력을 평가하고 향상시키는 데 크게 기여할 것으로 예상됩니다.  결론적으로, MM-StyleBench는 **미적 평가 연구의 새로운 지평을 열고**, 다양한 하류 애플리케이션(예: 스타일 변환, 이미지 생성) 발전에 중요한 기여를 할 것으로 기대됩니다.

#### ArtCoT Prompting
ArtCoT 프롬프팅은 **다단계 질의응답 방식**을 통해 다양한 모달리티(텍스트, 이미지) 정보를 활용하여 미술 작품의 심미적 평가를 수행하는 기법입니다. 이는 단순히 이미지를 분석하는 것을 넘어서, **전문가 수준의 미술 비평**과 유사한 방식으로 작품을 해석하고 평가합니다.  **단계별 분석**을 통해 객관적인 평가를 지향하며, 주관적인 표현이나 착각(hallucination)을 최소화하여 **인간의 미적 판단과 일치도**를 높이는 데 초점을 맞춥니다.  ArtCoT는 단순한 프롬프트 엔지니어링 기법이 아닌, **심층적인 추론 능력**을 요구하는 복잡한 과제를 해결하기 위한 시스템적인 접근 방식이며, **미술 분야 뿐 아니라 다양한 창의적 영역**에서의 활용 가능성을 시사합니다.

#### Aesthetic Alignment
본 논문에서 '미적 정렬(Aesthetic Alignment)'이란, **인간의 미적 선호도와 다양한 다중 모드 언어 모델(MLLM)의 평가 결과 간의 일치 정도**를 의미합니다.  즉, MLLM이 예술 작품을 평가할 때 인간과 얼마나 유사한 판단을 내리는지를 측정하는 지표입니다.  논문에서는 MLLM의 미적 판단 능력을 향상시키기 위해, **작품 평가 과정을 구체적인 단계로 분해하고 명확한 언어를 사용**하는 ArtCoT 프롬프팅 기법을 제시합니다. ArtCoT는 MLLM의 환각 현상을 줄이고 미적 추론 능력을 높여, 인간의 미적 선호도와의 정렬을 개선하는 데 기여합니다.  **MM-StyleBench라는 대규모 데이터셋**을 활용하여 실험한 결과, ArtCoT는 다양한 MLLM에서 인간의 미적 선호도와의 상관성을 **상당히 높이는 효과**를 보였습니다.  이는 MLLM의 미적 판단 능력 향상 및 예술 관련 응용 분야 발전에 중요한 의미를 갖습니다.  **특히, 환각 현상 감소를 위한 프롬프팅 전략**은 MLLM의 신뢰도를 높이는 데 중요한 요소입니다.

#### Hallucination in LLMs
LLM의 환각 현상은 **모델이 사실이 아닌 정보를 생성하는 현상**을 말합니다.  이는 훈련 데이터의 부족이나 편향, 모델의 복잡성 등 다양한 요인으로 발생하며, 특히 맥락이 모호하거나 제한적인 경우 더욱 심해집니다.  **환각은 신뢰성있는 정보 생성을 저해**하며, LLM의 실제 응용 분야에서 심각한 문제를 야기할 수 있습니다.  **환각 문제 해결을 위해서는** 더욱 방대한 양의 고품질 데이터를 사용하고, 모델의 아키텍처를 개선하며, **사실 확인 및 검증 메커니즘**을 도입하는 등의 노력이 필요합니다.  **데이터의 품질 관리** 및 **모델의 투명성 확보**는 환각 현상을 최소화하기 위한 중요한 요소이며,  향후 LLM 연구의 주요 과제가 될 것입니다.  **프롬프트 엔지니어링 기법**을 활용하여 모델의 응답을 제어하고, **출력 결과에 대한 엄격한 평가 및 검증** 절차를 거치는 것 또한 중요합니다.  **사용자에게 환각 가능성을 알리고** 필요한 정보에 대한 **비판적 사고를 촉구**하는 것 또한 매우 중요한 해결책입니다.  궁극적으로, LLM의 환각 문제는 **기술적 개선과 윤리적 고려**를 동시에 충족해야 하는 복잡한 문제이며 지속적인 연구와 노력이 필요합니다.

#### Future of Art AI
미래의 아트 AI는 **예술가와 AI의 협업**을 통해 새로운 창작 영역을 개척할 것입니다. AI는 예술가의 상상력을 확장하고 기술적인 어려움을 해결하는 도구로서 기능하며, **개인화된 예술 경험**을 제공하는 데 기여할 것입니다.  **윤리적 문제** 또한 중요한 고려 사항입니다. AI가 생성한 예술 작품의 저작권, 예술의 정의, 인간 예술가의 역할 등에 대한 사회적 합의가 필요하며, AI 기술의 오용을 방지하기 위한 **규제 및 가이드라인** 마련이 중요합니다.  **데이터 편향** 문제 해결을 위한 노력 또한 필수적이며, 다양한 스타일과 문화적 배경을 반영하는 데이터 세트를 구축하고 AI 모델의 투명성을 높여야 합니다.  궁극적으로 아트 AI는 **인간의 창의성을 증폭**시키고 예술의 대중화에 기여하는 역할을 할 것으로 예상됩니다.  하지만 기술 발전과 함께 발생할 수 있는 부정적인 영향에 대한 면밀한 검토와 대비가 필요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.09012/x2.png)

> 🔼 그림 2는 제시된 논문의 실험 과정을 보여주는 개요도입니다.  (a)에서는 다양한 스타일과 콘텐츠를 가진 이미지들을 MM-StyleBench 데이터셋에서 샘플링하고, 이를 스타일 변환 모델에 적용하여 결과 이미지들을 생성합니다.  이후 모든 후보 이미지 조합에 대해 2AFC (Two-Alternative Forced Choice) 비교 세트를 구성합니다. (b)에서는 사람들이 생성된 이미지 쌍에 대해 선호도를 평가하고, 이를 통해 얻은 선호도 데이터를 두 가지 휴리스틱 지표를 이용하여 필터링하고, 최종적으로 글로벌 순위를 계산합니다.  (c)에서는 제안된 ArtCoT 프롬프팅 방법이 소개됩니다.  ArtCoT는 MLLM(다중 모드 대규모 언어 모델)의 환각 현상을 줄이기 위해 세 가지 단계의 특정 예술 관련 작업으로 구성됩니다.  마지막으로, MLLM과 사람의 순위 간의 상관관계를 계산하여 미적 정렬 정도를 평가합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Overview of our alignment evaluation pipeline. First, (a) we sample content and style from MM-StyleBench for stylization, and construct 2AFC comparison sets by sampling from all possible candidate comparisons. (b) Human preference data is collected and filtered with two heuristic indicators, which is finally aggregated as global rankings. (c) We propose ArtCoT, which involves three art-specific phases to reduce MLLMs’ hallucinations. Finally, we calculate the correlation of rankings from MLLMs and humans as indicators of aesthetic alignment.
> </details>



![](https://arxiv.org/html/2501.09012/x3.png)

> 🔼 그림 3은 다양한 MLLM 프롬프팅 기법에 따른 미세 조정된 비교 결과를 보여줍니다. MM-StyleBench에서 제공하는 대표적인 속성별로 그룹화하여 인스턴스별 정렬에 대한 Spearman의 ρ 값을 제시합니다. ArtCoT는 모든 시나리오에서 미적 추론을 이끌어내지만, 특히 길고 자세한 프롬프트가 있는 인스턴스에서 효과적임을 보여줍니다. 즉, ArtCoT 프롬프팅 기법을 사용하면 MLLM이 그림의 미적 특징을 더 잘 이해하고 평가할 수 있음을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Fine-grained comparison of different MLLM prompting scheme. We show the spearman’s ρ𝜌\rhoitalic_ρ for per-instance alignment, grouped by representative attribute provided by MM-StyleBench. ArtCoT elicits aesthetic reasoning for all scenarios, especially for instances with long and detailed prompts.
> </details>



![](https://arxiv.org/html/2501.09012/extracted/6127957/Fig/UI-min.png)

> 🔼 그림 4는 사용자 인터페이스 디자인을 보여줍니다. 사용자는 상단에 원본 이미지, 중간에 2AFC (두 가지 선택지 제시) 질문, 하단에 스타일 프롬프트를 확인합니다.  2AFC 질문에서는 두 개의 스타일 변환 결과 이미지가 제시되고, 사용자는 선호하는 이미지를 ‘왼쪽’ 또는 ‘오른쪽’ 버튼을 클릭하여 선택합니다. 이를 통해 사용자의 미적 선호도를 효과적으로 수집할 수 있습니다. 
> <details>
> <summary>read the caption</summary>
> Figure 4: User Interface for Preference Annotation. We present user with the source image (top), 2AFC (middle) and style prompt (bottom). The user is required to choose the preferred one by clicking on the “left” or “right” button.
> </details>



![](https://arxiv.org/html/2501.09012/x4.png)

> 🔼 이 알고리즘은 주어진 그래프에서 일정한 차수 분포를 가진 연결된 부분 그래프를 샘플링하는 방법을 설명합니다.  먼저, 그래프의 모든 노드를 포함하는 최소 신장 트리를 생성하고, 이를 초기 부분 그래프로 설정합니다. 그런 다음, 남은 에지를 추가하여 각 노드의 차수가 가능한 한 균일하게 되도록 합니다.  이 과정은 탐욕적인 방법으로 수행되며, 가장 낮은 차수 불균형을 가진 에지를 우선적으로 선택합니다.  알고리즘은 그래프의 크기와 에지의 수를 입력으로 받아, 연결된 부분 그래프의 에지 집합을 출력합니다.
> <details>
> <summary>read the caption</summary>
> Algorithm 1 Sample a Connected Subgraph with Uniform Degree Distribution
> </details>



![](https://arxiv.org/html/2501.09012/x5.png)

> 🔼 그림 5는 다양한 스타일 변환 결과에서 무작위로 선택된 두 가지 예시를 보여줍니다.  각각 인상주의와 입체주의 스타일을 적용한 결과이며, 스타일 변환 성능의 넓은 범위를 보여줍니다.  이러한 다양성은 예술 작품 평가에 있어 현실적이고 어려운 과제를 제시합니다. 그림에는 스타일 변환 결과 이미지들이 나열되어 있으며, 각 이미지는 원본 이미지와 그에 따른 두 가지 스타일 변환 결과를 보여줍니다. 이미지 순서는 무작위로 배치되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Examples of Stylized Image. We show two uncurated examples from different stylization results, the image order are randomized. The styles are impressionist and cubism, respectively. The results covers a wide range of stylization performance, setting a realistic and challenging task for artistic evaluation.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | Prompting | Per-Method Alignment Elo ρ ↑ | Per-Method Alignment p-value ↓ | Per-Method Alignment Bradley-Terry ρ ↑ | Per-Method Alignment Bradley-Terry p-value ↓ | Per-Instance Alignment Elo ρ ↑ | Per-Instance Alignment p-value ↓ | Per-Instance Alignment Bradley-Terry ρ ↑ | Per-Instance Alignment Bradley-Terry p-value ↓ |
|---|---|---|---|---|---|---|---|---|
| Random guess | – | -0.115 | 0.751 | 0.067 | 0.855 | 0.068 | 0.153 | 0.026 | 0.290 |
| Aesthetics Predictor [7] | – | 0.406 | 0.244 | 0.406 | 0.244 | 0.427 | &lt;10^-3 | 0.428 | &lt;10^-3 |
| GPT-4o | Base | 0.248 | 0.489 | 0.284 | 0.425 | 0.328 | 0.003 | 0.331 | 0.006 |
| Gemini 1.5-flash | Base | 0.467 | 0.173 | 0.552 | 0.09 | 0.479 | &lt;10^-3 | 0.353 | &lt;10^-3 |
| Claude 3.5-sonnet | Base | -0.261 | 0.467 | -0.321 | 0.365 | 0.312 | &lt;10^-3 | 0.367 | &lt;10^-3 |
| GPT-4o | Zero-shot CoT | 0.345 +13% | 0.328 | 0.357 +10% | 0.313 | 0.299 -4% | 0.097 | 0.313 -3% | 0.031 |
| Gemini 1.5-flash | Zero-shot CoT | 0.018 -84% | 0.962 | 0.236 -62% | 0.511 | 0.376 -20% | &lt;10^-3 | 0.327 -4% | &lt;10^-3 |
| Claude 3.5-sonnet | Zero-shot CoT | -0.345 -7% | 0.328 | -0.309 +1% | 0.385 | 0.108 -30% | 0.068 | 0.081 -45% | 0.082 |
| GPT-4o | ArtCoT | 0.576 +43% | 0.08 | 0.721 +61% | 0.001 | 0.591 +39% | &lt;10^-3 | 0.548 +32% | &lt;10^-3 |
| Gemini 1.5-flash | ArtCoT | 0.697 +43% | 0.025 | 0.782 +51% | 0.007 | 0.624 +28% | &lt;10^-3 | 0.577 +35% | &lt;10^-3 |
| Claude 3.5-sonnet | ArtCoT | 0.612 +69% | 0.059 | 0.600 +70% | 0.066 | 0.492 +26% | &lt;10^-3 | 0.487 +19% | &lt;10^-3 |{{< /table-caption >}}
> 🔼 표 II는 다양한 모델과 프롬프트 방법을 사용하여 얻은 방법별 또는 인스턴스별 순위와 사람의 선호도 간의 정렬을 정량적으로 비교한 표입니다. 기준 프롬프트 방법과 비교하여 정규화된 변화로 성능 향상/감소를 계산합니다. ArtCoT은 다양한 MLLM에서 사람의 미적 선호도와 강력한 정렬을 제공합니다.
> <details>
> <summary>read the caption</summary>
> TABLE II: Quantitative comparison on aesthetic alignment. We report alignment of per-method or per-instance ranking from different models and prompting methods with that of human preference. The performance improvement/decline is calculated as normalized changes compared with the base prompt method. Our ArtCoT delivers strong alignment with human aesthetic preference across different MLLMs.
> </details>

{{< table-caption >}}
| Method | Subjectivity ↓ | Subjective word frequency (%) ↓ |
|---|---|---|
| Zero-Shot CoT | 0.44 | 20.15 |
| ArtCoT | **0.23** | **5.51** |{{< /table-caption >}}
> 🔼 본 표는 서로 다른 프롬프트 방법을 사용했을 때 다양한 다중 모드 대규모 언어 모델(MLLM)의 응답 주관성을 정량적으로 비교 분석한 결과를 보여줍니다.  ArtCoT 프롬프트를 사용했을 때 MLLM 응답의 주관성이 훨씬 감소했음을 보여줍니다.  구체적으로, 각 프롬프팅 방법에 따른 주관성 점수와 주관적인 단어 빈도를 제시하여 ArtCoT의 효과를 명확하게 보여줍니다.
> <details>
> <summary>read the caption</summary>
> TABLE III: Response subjectivity from different prompting method. Responses from MLLM prompted by ArtCoT are less subjective.
> </details>

{{< table-caption >}}
| CS-analyzer | Critic | Per-method ρ ↑ | Per-instance ρ ↑ |
|---|---|---|---| 
| ✗ | ✓ | 0.630 | 0.532 |
| ✓ | ✗ | 0.531 | 0.366 |
| ✓ | ✓ | **0.739** | **0.607** |{{< /table-caption >}}
> 🔼 표 IV는 ArtCoT 구성 요소에 대한 ablation 연구 결과를 보여줍니다.  ArtCoT의 핵심 구성 요소인 콘텐츠/스타일 분석기와 예술 비평가(Art Critic)를 제거했을 때의 미적 정렬 성능 변화를 보여줍니다. 콘텐츠/스타일 분석기와 예술 비평가를 모두 사용하는 전체 ArtCoT 모델이 가장 높은 미적 정렬 성능을 달성함을 확인할 수 있습니다. 이는 ArtCoT의 각 구성 요소가 미적 판단에 중요한 역할을 한다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> TABLE IV: Ablation on component of ArtCoT. We ablate the content/style analyzer and the art critic. The full method achieves the best aesthetic alignment.
> </details>

{{< table-caption >}}
| Content | Style | Resolution | Per-method ρ ↑ | Per-instance ρ ↑ |
|---|---|---|---|---|
| ✓ | ✓ | 1/4 | 0.630 -42% | 0.432 -44% |
| ✓ | ✓ | 1/8 | 0.502 -91% | 0.285 -82% |
| ✗ | ✗ | 1/2 (default) | 0.476 -100% | 0.416 -49% |
| ✗ | ✓ | 1/2 (default) | 0.678 -23% | 0.465 -36% |
| ✓ | ✗ | 1/2 (default) | 0.557 -69% | 0.521 -22% |
| ✓ | ✓ | 1/2 (default) | **0.739** | **0.607** |{{< /table-caption >}}
> 🔼 표 V는 이미지 해상도와 소스 정보에 대한 ablation study 결과를 보여줍니다. Elo와 Bradley-Terry 방법을 사용하여 계산된 상관관계 ρ (rho) 값을 보고합니다.  다양한 입력 설정(컨텐츠 이미지, 스타일 프롬프트, 이미지 하위 샘플링 비율)에 따른 상관관계를 비교 분석하여 어떤 요소들이 모델 성능에 가장 큰 영향을 미치는지 보여줍니다.  즉, 컨텐츠 이미지, 스타일 프롬프트, 이미지 해상도가 모델의 성능에 어떻게 영향을 주는지 실험적으로 확인한 결과를 보여주는 표입니다.
> <details>
> <summary>read the caption</summary>
> TABLE V: Ablation on image resolution and source information. We report the correlation ρ𝜌\rhoitalic_ρ (averaged from Elo and Bradley-Terry) of different input setups: content image, style prompt, and image sub-sampling factor.
> </details>

{{< table-caption >}}
|---|---|---|---|---|---| 
| **Source** | **Generated** | **MS-COCO** | **SA-1B** | **WikiArt** | **DiffusionDB** | 
|---|---|---|---|---|---| 
| **Number** | 500 | 250 | 250 | 764 | 236 |{{< /table-caption >}}
> 🔼 표 VI는 MM-StyleBench 데이터셋의 구성에 대해 설명합니다. MM-StyleBench는 다양한 스타일의 이미지를 생성하기 위해 여러 데이터 소스를 사용하여 생성되었으며, 편향을 제거하기 위해 노력했습니다. 이 표는 각 소스에서 가져온 콘텐츠와 스타일 이미지의 수량을 보여줍니다.  구체적으로는,  콘텐츠 이미지는 SA-1B, MS-COCO, GPT-4를 이용하여 생성되었으며, 스타일 이미지는 WikiArt와 DiffusionDB로부터 수집되었습니다. 각 소스에서 가져온 데이터의 개수가 명시되어 있어 MM-StyleBench 데이터셋의 규모와 다양성을 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> TABLE VI: Content and Style Sources MM-StyleBench is built from diverse sources to eliminate bias.
> </details>

{{< table-caption >}}
| Base Prompt | Zero-Shot CoT | C-S Analyzer | Art Critic | Summarizer |
|---|---|---|---|---|
| ‘[IMAGE]‘ You are an expert in fine art. A source image (top) and two different stylized images (bottom) in the style of ‘[STYLE]‘ are presented to you. Consider both the content and style, which stylized image is better in terms of overall aesthetic quality as an artwork? Return your decision in a Python Dict, [’winner’:int]. ‘0‘ means the left is better while ‘1‘ means the right is better. Do not answer any other things. | ‘[IMAGE]‘ {”request”: ”You are an expert in fine art. A source image (top) and two different stylized images (bottom) in the style of ‘style‘ are presented to you. Consider both the content and style, which stylized image is better in terms of overall aesthetic quality as an artwork?”. Return the reason and your decision in short in format of a Python Dict  ’thinking’:str, ’winner’:int. ‘0‘ means the left is better while ‘1‘ means the right is better.”, ”response”: ”{’thinking’: ’ Let’s’ think step by step, | ‘[IMAGE]‘ You are an expert in fine art. A source image (top) Two stylized images (bottom left and bottom right) in the style of ‘[STYLE]‘ are presented to you. Compare the content preservation and style fidelity of the two images, which one is better. Return your answer in a Python Dict, [’style_reason’:str, ’content_reason’:str, ’style_winner’:int, ’content_winner’:int]. ‘0‘ means the left is better while ‘1‘ means the right is better. Do not include any other string in your response. | ‘[IMAGE]‘ Take a closer look at the two stylized images at the bottom in the style of ‘[STYLE]‘. As an expert in art, do you agree with above analysis? Compare and consider the following questions. What visual features is essential for the style of ‘[STYLE]‘? Is the content at top well-preserved in the specific art style? Is there any artifact, distortion or inharmonious color patterns in either painting? Return your answer in a Python Dict, [reflection’:str]. | ‘[IMAGE]‘ Now we summarize. Based on above analysis and reflection, which stylized image at the bottom is better in terms of overall aesthetic quality as an **painting of the original content (top) in another style**? Return your answer in a Python Dict, [’winner’:int]. ‘0‘ means the left is better while ‘1‘ means the right is better. Do not include any other string in your response. |{{< /table-caption >}}
> 🔼 표 VII은 논문에서 사용된 세 가지 다른 프롬프트 방법(기본 프롬프트, 제로샷 CoT, ArtCoT)의 템플릿을 보여줍니다. 각 템플릿은 스타일 프롬프트([STYLE])와 이미지 토큰([IMAGE])에 대한 자리 표시자를 포함합니다. 기본 프롬프트는 단순히 이미지와 스타일을 제시하고 미학적 품질을 평가하도록 요청합니다. 제로샷 CoT는  추론 과정을 단계별로 제시하여 모델의 추론 능력을 향상시키려고 시도합니다. ArtCoT는 예술 전문가의 평가 방식을 모방하여 콘텐츠 보존, 스타일 충실도, 미학적 요소 등을 체계적으로 평가하도록 프롬프트합니다.  각 템플릿은 모델의 응답을 Python 딕셔너리 형태로 받아 평가 결과를 도출합니다.
> <details>
> <summary>read the caption</summary>
> TABLE VII: Template for different prompting methods. [STYLE] stands for placeholder for the style prompt, and [IMAGE] stands for placeholder for image tokens.
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
{{< /gallery >}}