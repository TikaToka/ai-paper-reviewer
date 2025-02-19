---
title: "Large Language Models and Mathematical Reasoning Failures"
summary: "대규모 언어 모델의 수학적 추론 능력은 여전히 미흡하며, 단순 정답률이 아닌 추론 과정 분석을 통해 이를 개선해야 합니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 KTH Royal Institute of Technology",]
showSummary: true
date: 2025-02-17
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.11574 {{< /keyword >}}
{{< keyword icon="writer" >}} Johan Boye et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-18 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.11574" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.11574" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/large-language-models-and-mathematical" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

본 연구는 고등학교 수준의 수학 문제 50개를 새로 만들어 대규모 언어 모델(LLM) 8개의 수학적 추론 능력을 평가한 연구입니다. 기존 연구들이 주로 정답률에만 초점을 맞춘 것과 달리, 본 연구는 **정답과 풀이 과정 모두를 면밀히 분석**하여 LLM의 추론 오류를 심층적으로 파악했습니다. 그 결과, 최신 모델일수록 정확도는 높지만 모든 모델에서 공간 추론, 전략적 계획, 산술 연산 등에서 오류가 발견되었고, 특히 다단계 추론이나 실세계 지식이 필요한 문제에서 어려움을 겪는다는 것을 확인했습니다. 

본 연구는 **LLM의 추론 과정 분석의 중요성**을 강조하며, 단순 정답률에 의존하는 기존 평가 방식의 한계를 지적합니다.  연구진은 **공간 추론, 전략적 계획 및 산술 능력 향상** 등을 위한 개선 방안을 제시하며, LLM의 일반화 능력 향상을 위한 **구조화된 추론 및 제약 조건 처리 능력 강화**의 필요성을 강조합니다.  **새롭게 제작된 50개의 수학 문제 데이터셋**은 향후 LLM의 수학적 추론 능력 평가에 유용하게 활용될 수 있을 것입니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 대규모 언어 모델은 수학적 추론 과정에서 다양한 오류를 보이며, 단순히 정답률만으로는 성능을 정확히 평가할 수 없습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 공간 추론, 전략적 계획, 산술 연산 등에서 LLM의 약점이 드러났으며, 이는 다단계 추론이나 실세계 지식을 요구하는 문제에서 더욱 두드러집니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} LLM의 수학적 추론 능력 향상을 위해서는 구조화된 추론 및 제약 조건 처리 능력을 개선하는 것이 중요합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대규모 언어 모델(LLM)**의 수학적 추론 능력에 대한 심층적인 분석을 제공하여, **LLM의 한계와 개선 방향**을 제시합니다.  이는 현재 **인공지능 연구의 주요 관심사** 중 하나이며, LLM의 응용 범위 확장에 중요한 시사점을 제공합니다. 특히 **추론 과정의 평가**를 강조하여, 단순 정답률 뿐 아니라 **추론 과정의 오류 분석**을 통해 LLM의 발전 방향을 제시하는 데 큰 의의가 있습니다.  향후 연구에서는 본 논문에서 제기된 문제점들을 해결하기 위한 **구체적인 개선 방안**을 모색하는 것이 중요할 것입니다.

------
#### Visual Insights





{{< table-caption >}}
| Model | Correct | Ans | Sol |
|---|---|---|---|
| mixtral-8x7B | 0 | 4 | 0 |
| llama-3.3-70B | 10 | 1 | 0 |
| gemini-2.0-pro-exp | 23 | 3 | 1 |
| gpt-4o | 14 | 3 | 2 |
| o1-preview | 30 | 2 | 2 |
| o1 | 37 | 2 | 1 |
| o3-mini | 40 | 2 | 0 |
| deepseek-r1 | 36 | 4 | 0 |{{< /table-caption >}}

> 🔼 표 1은 8개의 최첨단 대규모 언어 모델(LLM)이 50개의 고등학교 수준 수학 문제를 풀이한 결과를 보여줍니다. 각 모델에 대해 정답과 풀이 과정의 정확성을 분석하여, 정답만 맞춘 경우(Ans), 풀이 과정은 틀렸지만 정답은 맞춘 경우(Sol), 정답과 풀이 과정 모두 맞춘 경우(Correct)로 분류하여 각각의 개수를 나타냅니다. 이를 통해 각 모델의 수학적 추론 능력을 정량적으로 비교하고, LLM의 강점과 약점을 파악하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 1: The number of problems correctly solved and answered (out of 50). Ans = correct answer but wrong solution. Sol = correct solution but wrong final answer.
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
{{< /gallery >}}