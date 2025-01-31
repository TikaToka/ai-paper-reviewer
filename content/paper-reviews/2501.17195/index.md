---
title: "Atla Selene Mini: A General Purpose Evaluation Model"
summary: "Atla Selene Mini: 최첨단 소형 언어 모델 기반 평가 시스템으로, 다양한 벤치마크에서 최고 성능을 달성!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Atla",]
showSummary: true
date: 2025-01-27
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.17195 {{< /keyword >}}
{{< keyword icon="writer" >}} Andrei Alexandru et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-30 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.17195" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.17195" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/atla-selene-mini-a-general-purpose-evaluation" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)의 자동화된 평가는 점점 더 중요해지고 있습니다. 기존의 LLM 평가 방식은 비용이 많이 들고 확장성이 떨어진다는 한계가 있습니다.  본 논문에서는 이러한 문제를 해결하기 위해 **Atla Selene Mini**라는 새로운 소형 언어 모델 기반 평가 시스템을 제시합니다.

Atla Selene Mini는 공개 데이터셋과 합성 데이터를 결합하여 훈련되었으며, **다양한 평가 작업**에서 우수한 성능을 보였습니다. 특히, **실제 금융 및 의료 산업 데이터셋**에서 인간 전문가 평가와의 높은 일치율을 달성하여 실용성을 입증했습니다.  또한, **프롬프트 형식 변화에 대한 강건성**을 보였으며,  **오픈소스로 공개**되어 폭넓은 커뮤니티 참여를 유도하고 있습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} Atla Selene Mini는 11개의 다양한 벤치마크에서 최첨단 성능을 기록했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 원칙적인 데이터 기법과 DPO 및 SFT 손실 함수를 사용하여 모델을 훈련했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 실제 산업 데이터셋에서 인간 전문가 평가와의 일치도가 크게 향상되었습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **자동화된 대규모 언어 모델 평가** 분야에 중요한 기여를 합니다.  **신뢰할 수 있고 확장 가능한 자동 평가 방법**은 LLM 연구의 발전에 필수적이며, 본 연구는 이러한 방법을 제공합니다. 또한, **다양한 실제 환경에서의 성능을 평가**하여 실용성을 강조하고 있으며,  향후 연구를 위한 **새로운 방향**을 제시합니다.  **오픈소스 모델 공개**를 통해 폭넓은 커뮤니티 참여를 유도하고 공동 연구를 촉진할 수 있다는 점에서도 의의가 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.17195/extracted/6157738/figures/Fig1.png)

> 🔼 그림 1은 Atla Selene Mini의 성능을 기존 최고 성능의 작은 언어 모델 판정자(SLMJ)들과 비교한 것입니다. (a)는 다양한 작업에서 Atla Selene Mini(검정색)와 가장 널리 사용되는 SLMJ들의 전체 작업 평균 성능을 비교한 것이고, (b)는 작업 유형 및 벤치마크별 성능 분석을 보여줍니다. 자세한 내용은 표 1을 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Figure 1: Atla Selene Mini outperforms current state-of-the-art SLMJs: a) Overall task-average performance, comparing Atla Selene Mini (black) with the best and most widely used SLMJs. b) Breakdown of performance by task type and benchmark – see Table 1 for full comparison.
> </details>





{{< table-caption >}}
| Model | CRAFT-MD | Medical | Most likely | Relevant | Overall | Finance |
|---|---|---|---|---|---|---|
|  |  |  |  |  |  | Bench |
|  |  | terminology | diagnosis | med. hist. |  |  |
| Atla-Selene-Mini | **0.92** | **0.62** | **0.68** | **0.74** | **0.717** |
| LLama-3.1-8B-Instruct | 0.79 | 0.51 | 0.62 | 0.64 | 0.664 |{{< /table-caption >}}

> 🔼 표 1은 다양한 과제와 벤치마크에 걸쳐 여러 언어 모델 평가자(SLMJ)의 성능을 상세히 분석한 결과를 보여줍니다. 각 열의 최고 점수는 굵게 표시되어 있으며, Atla Selene Mini는 과제와 벤치마크 전체에 걸쳐 평균적으로 가장 높은 성능을 보였습니다. † 표시는 기존 연구에서 발표된 수치를 사용한 모델임을 나타냅니다.  표는 Atla Selene Mini의 우수한 성능을 객관적으로 보여주는 주요 결과를 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Detailed breakdown of SLMJ performance: Bold numbers indicate the highest score per column. Atla Selene Mini has the highest overall performance averaged over tasks (sections) and benchmarks (columns).  † indicates models for which we report previously published numbers.
> </details>





### In-depth insights


#### Mini-LMJ
소형 언어 모델 기반 판정 시스템(Mini-LMJ)은 대규모 언어 모델(LLM)의 자동 평가에 대한 효율적이고 비용 효과적인 접근 방식을 제시합니다. 기존의 대규모 LLM을 사용하는 것보다 훨씬 적은 자원을 사용하면서도, **정확도와 효율성을 동시에 확보**할 수 있는 가능성을 보여줍니다.  Mini-LMJ는 특히 **신속한 추론**과 **높은 확장성**이 필요한 실제 환경에서 유용하며, **데이터 품질 향상**과 **적절한 훈련 방법**을 통해 기존의 한계를 극복하고 더욱 정교한 평가를 가능하게 합니다. 하지만, **작은 모델 크기**로 인해 복잡한 평가 과제를 처리하는 데는 여전히 한계가 있을 수 있으며, **일반화 성능**과 **다양한 과제에 대한 적응력**을 더욱 향상시키기 위한 추가 연구가 필요합니다.  **데이터 편향** 문제에 대한 지속적인 주의와 **인간 전문가 평가와의 일관성** 확보 노력 또한 중요한 요소입니다.  궁극적으로 Mini-LMJ는 LLM 평가 분야에서 **새로운 가능성**을 열어주지만, 꾸준한 개선과 발전을 통해 실제 적용 가능성을 더욱 높여야 할 것입니다.

#### DPO+SFT Training
본 논문에서 제시된 DPO+SFT 훈련 방법은 **대규모 언어 모델(LLM) 평가자의 성능을 향상**시키는 데 중점을 두고 있습니다. DPO(Direct Preference Optimization)는 모델이 인간의 선호도를 직접적으로 학습하도록 하는 반면, SFT(Supervised Fine-Tuning)는 기존의 지도 학습 방식을 통해 모델의 정확성을 높입니다.  두 기법을 결합함으로써 **모델의 성능과 신뢰도를 모두 개선**할 수 있다는 점이 핵심입니다.  **데이터 품질 확보를 위한 엄격한 데이터 정제 과정**과 **합성 데이터를 활용한 데이터 증강**은 모델의 일반화 능력 향상에도 크게 기여했을 것으로 예상됩니다. 특히, 다양한 실제 환경 데이터셋에서의 성능 평가 결과는 이러한 훈련 방법이 **실제 응용 분야에서도 효과적**임을 보여줍니다.  **다만, DPO와 SFT의 최적 비율 및 하이퍼파라미터 조정** 등 추가적인 연구를 통해 더욱 개선된 성능을 기대할 수 있을 것입니다.

#### Real-world Robustness
본 논문은 실제 환경에서의 강건성(Real-world Robustness)을 평가하기 위해 **다양한 실제 산업 데이터셋**을 사용하여 모델의 성능을 평가하였습니다. 특히, 금융 및 의료 분야의 전문가가 주석을 단 데이터셋을 활용하여 **제로샷(zero-shot)** 성능을 측정했습니다. 이를 통해, 모델이 훈련 데이터셋의 분포를 벗어나는 실제 상황에서도 **높은 정확도**를 유지함을 보여주었습니다. 또한, **다양한 프롬프트 형식**에 대한 모델의 강건성을 평가하여, 프롬프트의 변화에도 성능 저하 없이 일관된 성능을 유지함을 확인했습니다. 이러한 결과는 모델이 실제 응용 환경에서도 효과적으로 사용될 수 있음을 시사합니다.  **커뮤니티 기반 평가 플랫폼**을 통해 다른 최첨단 모델들과의 비교 평가를 진행하여, **상위권 성적**을 달성한 점도 주목할 만합니다. 이는 모델의 실용성과 뛰어난 성능을 다시 한번 입증하는 것입니다.

#### Arena Leaderboard
연구 논문의 "아레나 리더보드" 부분은 **실제 환경에서 모델의 성능을 평가하는 혁신적인 방법론**을 제시합니다.  다양한 평가 모델들이 실시간으로 서로 경쟁하며, **ELO 점수를 통해 순위를 매김**으로써, 단순한 벤치마크 결과를 넘어 실질적인 사용성과 우위를 보여줍니다. 이는 기존의 정적인 벤치마크 방식과 달리, **지속적인 경쟁과 개선을 유도**하며, 모델의 장기적인 성능과 안정성을 평가하는 데 효과적입니다.  또한, **오픈소스와 독점 모델 간의 직접적인 비교**를 가능하게 하여, 상호 경쟁을 통한 기술 발전을 촉진할 수 있습니다.  **커뮤니티 기반의 참여**는 리더보드의 신뢰도와 활용도를 높이고, 다양한 관점과 평가 기준을 반영할 수 있다는 장점이 있습니다. 하지만, 리더보드의 순위 변동이 잦고, 평가 기준이 주관적일 수 있으며, **참여 모델의 대표성**에 대한 검토가 필요하다는 점을 고려해야 합니다.  결론적으로, "아레나 리더보드"는 **새로운 평가 패러다임**을 제시하며, AI 모델의 실제 성능과 경쟁력을 평가하는 유용한 도구임을 시사합니다.

#### Future of Eval
평가(Eval)의 미래는 **더욱 정교하고, 견고하며, 그리고 실세계에 적용 가능한 시스템**으로 나아갈 것입니다.  이는 단순히 정확도나 효율성 측면만 고려하는 것이 아니라, **모델의 윤리적 측면과 사회적 영향까지 고려**해야 함을 시사합니다.  특히, **복합적인 상황과 다양한 프롬프트 형식에 대한 모델의 강인성**을 평가하는 방법론 개발이 중요하며, **인간 전문가의 평가와의 일관성 확보**도 필수적입니다.  더 나아가, **대규모 언어 모델(LLM)의 자동화된 평가 시스템**을 통해 지속적인 모델 개선 및 신뢰도 향상을 도모할 수 있을 것입니다.  하지만, **평가 지표 자체의 한계 및 편향성**을 인지하고 꾸준히 개선해 나가는 노력이 필요합니다.  **인간의 개입과 상호작용을 고려한 평가 체계**의 구축도 중요한 과제입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.17195/extracted/6157738/figures/Fig2.png)

> 🔼 이 그림은 Atla Selene Mini 모델의 학습 데이터 생성 과정을 보여줍니다. 왼쪽에서 시작하여 후보 데이터셋을 여러 단계의 필터링(노란색 박스)과 선택 및 거부된 쌍(파란색과 빨간색)의 합성 생성(보라색)을 거쳐 최종 학습 데이터셋(오른쪽)을 만드는 과정입니다. 빨간색 원은 보상 임계값이나 데이터셋 포함 여부와 같은 ablation 연구를 통해 내려진 결정들을 나타냅니다.  즉, 기존 데이터셋에 합성 데이터를 추가하고 품질을 높이기 위해 여러 필터링 및 ablation 기법을 사용하는 데이터 정제 과정을 시각적으로 보여주는 그림입니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Data curation strategy: The process of transforming a candidate dataset (left) into the final training mix (right). Yellow boxes indicate filtering steps, purple represents synthetic generation of chosen and rejected pairs (blue and red) for preference optimization, and red circles highlight ablation-informed decisions, such as reward thresholds and dataset inclusion.
> </details>



![](https://arxiv.org/html/2501.17195/extracted/6157738/figures/Fig3.png)

> 🔼 그림 3은 Atla Selene Mini의 실제 환경 평가 결과를 보여줍니다. (a)는 금융(FinanceBench) 및 의료(CRAFT-MD) 특화 산업용 벤치마크에서 Atla Selene Mini(검정색)와 기본 모델(주황색)의 정확도를 비교하여 훈련된 모델이 전문가 합의도가 더 높음을 보여줍니다. (b)는 프롬프트 형식을 변경했을 때 Atla Selene Mini와 기본 모델의 RewardBench 성능을 비교하여 훈련된 모델이 프롬프트 형식에 관계없이 일관되게 성능이 향상됨을 보여줍니다. (c)는 Judge Arena에서 1대1 비교를 기반으로 ELO 점수로 측정한 성능을 보여줍니다. 2025년 1월 22일 기준으로 Atla Selene Mini(굵은 글씨)가 다른 모든 평가자를 능가합니다. 오차 막대는 95% 신뢰 구간을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Real-world evaluation: a) Performance on domain-specific industry benchmarks of Atla Selene Mini (black) compared to base model (orange) measured in accuracy. Trained model shows higher expert agreement on FinanceBench, a financial benchmark, and CRAFT-MD, a medical dataset. b) Performance on RewardBench of Atla Selene Mini compared to base model, when prompt format is changed. Trained model shows consistent improvement across formats. c) Performance measured by ELO scores, based on head-to-head comparisons in Judge Arena. An early snapshot of Atla Selene Mini (bold) beats all other evaluators as of Jan 22, 2025. Error bars indicate 95% CI.
> </details>



![](https://arxiv.org/html/2501.17195/extracted/6157738/figures/nomic.png)

> 🔼 그림 4는 Atla Selene Mini 모델의 학습 데이터셋을 Nomic Atlas를 사용하여 2차원으로 시각화한 것입니다.  각 점은 특정 주제(topic)를 나타내는 데이터셋을 표현하며, 유사한 주제의 데이터셋은 서로 가까이 위치합니다. 이를 통해 Atla Selene Mini 모델이 학습된 데이터셋의 주제 분포와 그 관계를 직관적으로 파악할 수 있습니다. 데이터셋 간의 유사성과 다양성을 한눈에 보여주는 시각적 표현으로, 모델 성능에 영향을 미치는 요소들을 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Training dataset map: Topic-stratified, two-dimensional embedding representation of Atla Selene Mini’s training dataset generated using Nomic Atlas [33].
> </details>



![](https://arxiv.org/html/2501.17195/extracted/6157738/figures/rm-ablation-report.png)

> 🔼 그림 5는 Atla Selene Mini 모델의 학습에 사용된 예시 데이터 포인트를 보여줍니다. FeedbackCollection 데이터셋 [34]에서 가져온 예시이며, 참고 답변(reference response)이 포함되어 있습니다.  참고 답변은 Atla Selene Mini가 평가할 때 선택적으로 사용할 수 있는 정보입니다.  이 예시는 논문에서 [10]번 참고문헌에서 사용된 것과 유사한 프롬프트 템플릿을 사용합니다. 그림은 프롬프트, 모델의 응답, 채점 기준, 그리고 평가 결과를 보여주어, Atla Selene Mini가 어떻게 훈련 데이터를 사용하여 텍스트를 평가하는지 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Example data point: Training example from FeedbackCollection [34], including the reference response, which is an optional field for Atla Selene Mini. This instance uses a similar prompt template to [10].
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
{{< /gallery >}}