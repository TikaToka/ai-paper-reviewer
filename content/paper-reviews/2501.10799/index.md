---
title: "Step-KTO: Optimizing Mathematical Reasoning through Stepwise Binary Feedback"
summary: "Step-KTO는 단계별 이진 피드백을 활용하여 LLM의 수학적 추론 능력을 향상시키는 새로운 훈련 프레임워크입니다. 중간 추론 단계와 최종 답변에 대한 이진 평가를 통해 LLM이 논리적 추론 과정을 따르도록 유도합니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Meta GenAI",]
showSummary: true
date: 2025-01-18
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.10799 {{< /keyword >}}
{{< keyword icon="writer" >}} Yen-Ting Lin et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-24 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.10799" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.10799" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/step-kto-optimizing-mathematical-reasoning" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)은 최근 수학적 추론에서 놀라운 성과를 보였지만, **추론 과정의 신뢰성 부족**이라는 문제점을 안고 있습니다. 기존 방법들은 최종 답변의 정확성에만 집중하여, **중간 추론 단계의 오류**는 간과하는 경향이 있었습니다. 이는 LLM을 투명하고 신뢰할 수 있는 시스템으로 활용하는 데 제약이 됩니다.

본 논문에서는 **Step-KTO**라는 새로운 훈련 프레임워크를 제시합니다. Step-KTO는 중간 추론 단계와 최종 답변에 대한 **단계별 이진 피드백**을 통합하여 모델이 논리적이고 정확한 추론 과정을 거치도록 유도합니다. 실험 결과, Step-KTO는 다양한 수학적 벤치마크에서 **정확도 및 추론 과정의 질적 향상**을 모두 달성했습니다. 이는 단계별 피드백을 LLM 훈련에 통합하는 것이 **모델의 해석성과 신뢰성을 높이는 데 효과적**임을 보여줍니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} Step-KTO는 단계별 및 최종 결과에 대한 이진 피드백을 결합하여 LLM의 추론 신뢰성을 향상시킵니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} Step-KTO는 다양한 수학적 벤치마크에서 기존 방법보다 우수한 성능을 보였습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 단계별 피드백 통합은 LLM 훈련에 대한 새로운 접근 방식을 제시하며, 더욱 해석 가능하고 신뢰할 수 있는 추론 기능 개발을 위한 길을 열어줍니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **LLM의 수학적 추론 신뢰성 향상**이라는 중요한 문제에 대한 새로운 접근 방식을 제시합니다. 단순히 최종 답변의 정확성에만 초점을 맞추는 기존 연구와 달리, **단계별 추론 과정의 타당성**까지 고려하여 더욱 신뢰할 수 있는 모델을 개발하는 데 기여합니다.  이는 **설명 가능성과 신뢰성이 중요한** 다양한 분야의 연구에 큰 영향을 미칠 수 있습니다.  본 연구의 결과는 LLM의 추론 능력 향상뿐만 아니라, **더욱 투명하고 신뢰할 수 있는 AI 시스템 개발**을 위한 새로운 방향을 제시한다는 점에서 큰 의의를 가집니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.10799/x1.png)

> 🔼 그림 1은 STEP-KTO 학습 과정을 보여줍니다. 왼쪽에 수학 문제 데이터셋이 주어지면, 언어 모델(LLM)은 추론 단계와 최종 답변을 모두 생성합니다. 각 중간 추론 단계는 프로세스 보상 모델(Process RM)에 의해 평가되고, 최종 답변은 결과 보상 모델(Outcome RM)에 의해 평가됩니다. 두 수준(결과 정확성 c<sup>o</sup> 와 단계별 정확성 c<sup>s</sup><sub>h</sub>)의 이진 피드백 신호는 입력(x)과 모델의 응답(y)과 함께 기록됩니다(§2.1). 그런 다음 이러한 신호들을 사용하여 STEP-KTO 손실을 계산하고, LLM이 올바른 최종 답변을 생성할 뿐만 아니라 일관되고 정확한 추론 단계를 유지하도록 안내합니다(§2.3). 이 학습 과정의 여러 반복을 통해(§2.4), 모델은 단계별 추론과 최종 답변 정확도를 점진적으로 향상시킵니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: \method Training Process. Given a dataset of math problems (left), a language model (LLM) produces both reasoning steps and a final answer. Each intermediate reasoning step is evaluated by a process reward model (Process RM), and the final answer is assessed by an outcome reward model (Outcome RM). The binary feedback signals from both levels (outcome-level correctness cosuperscript𝑐𝑜c^{o}italic_c start_POSTSUPERSCRIPT italic_o end_POSTSUPERSCRIPT and stepwise correctness chssubscriptsuperscript𝑐𝑠ℎc^{s}_{h}italic_c start_POSTSUPERSCRIPT italic_s end_POSTSUPERSCRIPT start_POSTSUBSCRIPT italic_h end_POSTSUBSCRIPT) are recorded together with the input (x)𝑥(x)( italic_x ) and the model’s response (y)𝑦(y)( italic_y ) §2.1. These signals are then used to compute the \method loss, guiding the LLM to not only produce correct final answers but also maintain coherent and correct reasoning steps §2.3. Through multiple iterations of this training process §2.4, the model progressively improves both its stepwise reasoning and final answer accuracy.
> </details>





{{< table-caption >}}
| 8B Model | Stepwise Errors in Correct Solutions | Stepwise Errors in Correct Solutions |
|---|---|---|
|  | KTO | \method |
| $M_{0}$ | 27.3% | 27.3% |
| $M_{1}$ | 24.6% | **22.9%** |
| $M_{2}$ | 22.6% | **20.8%** |
| $M_{3}$ | 21.1% | **19.9%** |{{< /table-caption >}}

> 🔼 표 1은 MATH-500, AMC23, AIME24 세 가지 수학 문제 풀이 벤치마크에서 다양한 크기의 Llama 모델과 독점 모델들의 성능을 비교한 표입니다.  Pass@1(탐욕적 디코딩 정확도)와 Maj@8(8개 샘플에 대한 다수결 투표 정확도) 두 가지 지표를 사용하여 모델의 성능을 평가했습니다. 파란색으로 강조 표시된 모델은 매개변수가 8B개인 모델이고, 녹색은 70B개, 회색은 상용 모델입니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Math problem solving performance comparing Llama models of different sizes and proprietary models. Results show accuracy on MATH-500, AMC23, and AIME24 test sets using both greedy decoding (Pass@1) and majority voting over 8 samples (Maj@8). Models highlighted in blue are 8B parameter models, green are 70B parameter models, and gray are commercial models.
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