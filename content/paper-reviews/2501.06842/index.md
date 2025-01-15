---
title: "SPAM: Spike-Aware Adam with Momentum Reset for Stable LLM Training"
summary: "SPAM: 급증하는 기울기로 인한 LLM 학습 불안정성 해결!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 University of Exeter",]
showSummary: true
date: 2025-01-12
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.06842 {{< /keyword >}}
{{< keyword icon="writer" >}} Tianjin Huang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-14 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.06842" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.06842" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/spam-spike-aware-adam-with-momentum-reset-for" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)은 뛰어난 성능을 보이지만, 학습 과정에서 **기울기(gradient)와 손실(loss)의 급격한 변동(스파이크)**으로 인해 **훈련 불안정성**이라는 심각한 문제에 직면합니다.  이로 인해 학습 과정이 중단되고, 많은 시간과 자원을 낭비하는 **체크포인트 복구 및 재시작**이 필요해집니다. 기존 연구는 주로 모델 구조 변경을 통해 이 문제를 해결하려고 했지만, 완벽한 해결책은 제시하지 못했습니다.

본 논문에서는 이 문제를 해결하기 위해 **모멘텀 리셋(Momentum Reset)**과 **스파이크 인식 기울기 클리핑(Spike-Aware Gradient Clipping)**을 통합한 새로운 최적화 기법인 **SPAM(Spike-Aware Adam with Momentum Reset)**을 제안합니다.  SPAM은 다양한 LLM 사전 훈련 및 미세 조정 작업에서 기존 방법보다 우수한 성능을 보였으며, 특히 **희소 모멘텀(Sparse Momentum)**을 통해 메모리 효율성을 크게 높였습니다.  **대규모 LLM 훈련의 안정성과 효율성을 동시에 개선**함으로써, **LLM 연구 및 개발에 중요한 기여**를 하고 있습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 새로운 최적화 기법 SPAM은 기울기 스파이크로 인한 LLM 학습 불안정성을 효과적으로 해결합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} SPAM은 모멘텀 리셋과 스파이크 인식 기울기 클리핑을 통해 학습 안정성과 자원 효율성을 향상시킵니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 희소 모멘텀 기법을 활용하여 메모리 효율적인 대규모 LLM 학습을 가능하게 합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대규모 언어 모델(LLM)** 학습의 안정성을 저해하는 **기울기 스파이크** 문제를 해결하기 위한 새로운 최적화 기법인 **SPAM(Spike-Aware Adam with Momentum Reset)**을 제시합니다.  **LLM 학습의 어려움과 비효율성을 감소시키는 데 기여**하여, **자원 효율성과 성능을 동시에 향상**시키고자 하는 연구 동향에 중요한 기여를 할 수 있습니다.  특히, **메모리 효율적인 훈련을 위한 희소 모멘텀 기법**까지 포함하고 있어, **대규모 모델 학습의 현실적인 제약을 극복**하는 데 실질적인 도움을 줄 수 있습니다. 이러한 연구는 앞으로 **LLM 연구의 발전과 실용화**에 큰 영향을 미칠 것으로 예상됩니다.

------
#### Visual Insights







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