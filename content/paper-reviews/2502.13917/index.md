---
title: "TESS 2: A Large-Scale Generalist Diffusion Language Model"
summary: "TESS 2: 대규모 일반적 지시 따르는 확산 언어 모델, 기존 모델 성능 뛰어넘어!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Yale University",]
showSummary: true
date: 2025-02-19
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.13917 {{< /keyword >}}
{{< keyword icon="writer" >}} Jaesung Tae et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-20 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.13917" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.13917" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/tess-2-a-large-scale-generalist-diffusion" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 자기회귀(AR) 언어 모델은 계획 및 자기 수정 능력에 한계를 가지고 있습니다.  **연구자들은 AR 모델의 한계를 극복하기 위해 확산 언어 모델을 제안했지만, 확산 언어 모델은 상대적으로 작은 규모이고, 퍼플렉서티와 같은 내부 지표 개선에 초점을 맞추고 있었습니다.**  따라서, 실제 응용 분야에서 AR 모델과 비교할 때 성능이 부족하다는 문제가 있었습니다.

본 논문에서는 이러한 문제를 해결하기 위해 대규모 일반적 지시 따르는 확산 언어 모델인 TESS 2를 제안합니다.  **TESS 2는 강력한 AR 모델을 기반으로 하여, 교차 엔트로피 손실을 확산 손실로 전환하여 모델을 적응시킨 후 추가적인 지시 조정을 수행하여 훈련되었습니다.**  **또한, 본 논문에서는 모델 출력을 정렬하기 위한 새로운 추론 시간 안내 절차인 보상 안내 기법을 제시했습니다.**  실험 결과, TESS 2는 기존 모델을 능가하며, 추론 시간 연산량 증가에 따라 성능이 향상되는 것을 확인했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} TESS 2는 기존의 지시 조정된 확산 언어 모델과 자기 회귀 모델을 능가하는 성능을 보임 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 추론 시 연산량을 미세 조정할 수 있는 확산 언어 모델의 장점을 강조 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 보상 기반 안내 기법을 통해 추가 훈련 없이 모델 출력을 개선하는 새로운 방법 제시 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**본 논문은 대규모 확산 언어 모델의 새로운 가능성을 제시하여, 연구자들에게 새로운 연구 방향을 제시하고 기존의 자기회귀 모델의 한계를 극복하는 데 기여합니다.**  **특히, 추론 시 연산량의 확장성과 미세 조정 가능성을 강조하여, 향후 연구에서 다양한 응용 분야로의 확장 가능성을 높입니다.**  **또한, 보상 기반 분류기 안내 기법은 모델 성능을 향상시키는 새로운 방법론을 제시하여, 모델 성능 향상에 대한 새로운 연구 방향을 제시합니다.**

------
#### Visual Insights



![](https://arxiv.org/html/2502.13917/x1.png)

> 🔼 그림 1은 TESS 2 모델의 추론 과정을 보여줍니다. 채팅 형식의 질문이 주어지면, 모델은 심플렉스 공간에서 반복적으로 잡음 제거(denoise) 과정을 거쳐 답변을 생성합니다. 이때, 일반적으로 100단계의 확산(diffusion) 단계를 수행하며, 선택적으로 각 단계마다 보상 안내(reward guidance)를 추가할 수 있습니다. 보상 안내는 예측된 보상의 기울기를 중간 로짓(logit)에 적용하여 보상을 기준으로 기울기 상승(gradient ascent)을 수행하는 방식입니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Overview of inference with \modelname. We provide a chat-template formatted query and iteratively denoise over the simplex space for a number of diffusion steps (typically 100). Optionally, we also incorporate reward guidance at each diffusion step by applying the gradient of the predicted reward to the intermediate logits, i.e., gradient ascent on reward.
> </details>





{{< table-caption >}}
| Ctx. Len. | 512 | 2048 | 2048 |
|---|---|---|---|
| Train Steps | 35,000 | 10,000 | 200,000 |
| Perp. | 24.3 | 12.2 | **11.3** |
| d-1 | **0.62** | 0.58 | 0.59 |
| d-2 | **0.87** | 0.84 | 0.85 |
| d-3 | **0.93** | 0.91 | 0.91 |
| d-4 | **0.94** | 0.93 | 0.93 |
| Mauve | 0.95 | **0.97** | 0.92 |
| Entropy | 6.31 | 6.21 | **6.34** |{{< /table-caption >}}

> 🔼 이 표는 다양한 기본 모델을 사용하여 35,000단계의 사전 훈련 후 확산 적응의 성능을 보여줍니다.  perplexity를 제외한 모든 경우 더 높은 값이 더 좋습니다.  Rand는 무작위 초기화를 나타냅니다.  표에는 각 모델의 perplexity, d-1, d-2, d-3, d-4, Mauve 점수 및 엔트로피가 포함되어 있으며, 이를 통해 다양한 기본 모델에 대한 확산 적응의 효과를 비교 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Performance of diffusion adaptation after 35,000 steps of pretraining over varied base models. In all cases except perplexity, higher is better. Rand. inidicates initializing from scratch.
> </details>





### In-depth insights


#### Diffusion LM Recipe
본 논문에서 제시된 "확산 LM 레시피"는 기존의 자기회귀 언어 모델을 기반으로 **연속 확산 언어 모델**을 효과적으로 훈련시키는 방법을 상세히 설명합니다.  **핵심은 기존의 강력한 자기회귀 모델을 사전 훈련하는 것**으로, 여기에는 UL2 마스크, 레이블 시프팅, 그리고 양방향 어텐션이 포함됩니다.  이를 통해 확산 모델이 효과적으로 학습하고 자기회귀 모델의 장점을 활용할 수 있게 됩니다.  또한, **추가적인 지시어 미세 조정**을 통해 일반적인 지시어 따르기 성능을 향상시키고, **보상 안내** 기법을 통해 훈련 없이도 출력을 개선할 수 있습니다.  전반적으로, 이 레시피는 확산 언어 모델을 효율적으로 훈련시키고 성능을 향상시키는 데 필수적인 요소들을 체계적으로 제시하며, **대규모 확산 언어 모델의 실용적인 구축**에 중요한 기여를 합니다.  **특히, 추론 시 계산량을 세밀하게 조절 가능**하다는 확산 모델의 장점을 극대화하는 데 집중하고 있습니다.

#### AR to Diffusion
본 논문의 "AR to Diffusion" 부분은 기존의 자기회귀(AR) 언어 모델을 확산(Diffusion) 언어 모델로 변환하는 방법을 제시합니다. **핵심은 AR 모델의 사전 훈련된 지식을 활용하여 확산 모델을 효율적으로 학습시키는 것**입니다.  이는 단순히 새로운 모델을 훈련하는 것보다 훨씬 적은 비용과 시간으로 고성능 확산 모델을 구축할 수 있다는 것을 의미합니다.  **본 연구는 AR 모델을 기반으로 UL2 마스크, 레이블 시프팅, 양방향 어텐션 등의 기법을 적용하여 확산 모델에 적합하도록 변환하는 구체적인 절차**를 제시합니다. 이를 통해 확산 모델이 지닌 **미세한 제어 및 생성 능력**을 유지하면서 AR 모델의 강점을 결합함으로써 성능 향상을 도모합니다.  **본 논문에서 제시된 방법론은 단순한 모델 전환을 넘어, AR 모델의 지식을 효과적으로 활용하는 전략**을 보여줍니다.  이는 향후 대규모 언어 모델 연구에 시사하는 바가 큽니다.

#### Reward Guidance
본 논문에서 제시된 'Reward Guidance'는 **추가적인 훈련 없이** 모델 출력을 개선하기 위한 새로운 방법입니다. 기존의 보상 모델을 활용하여, 생성 과정의 각 단계에서 보상의 기울기를 이용해 중간 생성물을 조정합니다. 이는 보상 모델이 생성물의 잠재적 보상을 추정하는 방식으로 작동하며, 생성 과정을 더 높은 보상을 가진 시퀀스로 유도합니다.  **기존 모델의 재학습 없이** 추론 단계에서만 적용되는 모듈식 접근 방식이므로, 효율적인 접근법이라고 할 수 있습니다.  **보상 모델의 선택 및 보상 가중치 조정**을 통해 성능 향상을 제어할 수 있다는 점이 핵심적이며, 향후 연구를 통해 다양한 보상 모델 및 가중치 조정 전략을 통해 추가적인 성능 개선이 기대됩니다.  본 논문은 'Reward Guidance'를 통해 **추론 시간 계산량의 확장성**을 보여주는 데에 성공하였습니다.

#### Downstream Tasks
연구 논문의 "다운스트림 작업(Downstream Tasks)" 부분에 대한 심층적인 분석 결과를 요약하면 다음과 같습니다. **다양한 하위 작업(하위 과제)들을 통해 모델 성능 평가가 이루어졌다.**는 점이 주목할 만합니다.  본 연구는 다양한 유형의 과제(예: 질의응답, 수리 문제 해결, 지시 따르기 등)를 포함하여 모델의 일반적인 언어 이해 및 추론 능력을 종합적으로 평가하고자 하였습니다.  **각 작업의 특징을 고려하여 평가 지표가 적절하게 선택되었으며**, 이를 통해 **모델의 강점과 약점을 정확히 파악하고 개선 방향을 제시**할 수 있게 되었습니다.  **특히, 특정 작업에 대한 세밀한 분석은 모델의 한계점을 드러내는 동시에, 향후 연구를 위한 중요한 시사점을 제공합니다.**  **다운스트림 작업 결과 분석은 모델의 실제 활용 가능성을 판단하는 데 중요한 역할**을 하며, 이는 연구의 신뢰도를 높이는 데 기여합니다.  추가적으로, 다운스트림 작업의 결과는 향후 모델 개선 및 발전 방향을 모색하는 데 중요한 근거자료로 활용될 수 있습니다.

#### Future Work
본 논문의 "향후 연구" 부분에 대한 심층적인 분석 결과를 요약하면 다음과 같습니다. **연구진은 TESS 2 모델의 성능 향상을 위한 여러 방안을 제시**하고 있습니다. 특히, **추론 속도 향상을 위한 연구**가 중요하게 언급되는데, 이는 확산 모델의 고유한 속도 저하 문제를 해결하기 위한 필수적인 과제이기 때문입니다. 또한, **다양한 하류 작업에서의 성능 개선을 위한 추가적인 연구**도 필요하며, **특히 추론 시간 계산량의 확장성에 대한 연구**는 모델의 실용성을 높이는 데 중요한 역할을 할 것입니다.  **보상 기반 분류기 지도의 개선** 또한 향후 연구 과제로 제시되었으며, 이를 통해 모델 출력의 품질을 더욱 향상시킬 수 있을 것으로 예상됩니다.  마지막으로, **다양한 언어 및 작업에 대한 모델의 적응성 및 일반화 성능 향상**을 위한 연구가 필요합니다. 이러한 연구를 통해 TESS 2 모델의 실용적 가치 및 학문적 기여도를 더욱 높일 수 있을 것으로 기대됩니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.13917/x2.png)

> 🔼 본 그림은 다양한 기본 모델들을 활용하여 확산 모델에 적용하는 과정에서의 훈련 손실을 보여줍니다. Mistral 모델이 Llama 3와 같은 최신 언어 모델들보다도 훈련 손실이 낮음을 보여주어, Mistral 모델이 확산 모델에 적용하기에 효율적인 기반 모델임을 시사합니다. 그림은 훈련 단계별 손실 값을 나타내는 그래프로 구성되어 있으며, 각 모델별 손실 변화 추이를 비교 분석하는 데 유용합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Train loss during adaptation training when adapting from different models. We find Mistral achieves the lowest overall loss during training, even compared to newer LMs such as Llama 3.
> </details>



![](https://arxiv.org/html/2502.13917/x3.png)

> 🔼 이 그림은 보상 안내 가중치를 증가시켰을 때 AlpacaEval 성능에 미치는 영향을 보여줍니다. 보상 안내 가중치가 증가하면 처음에는 성능이 향상되지만, 특정 지점을 넘어서면 성능이 저하됨을 보여줍니다. 즉, 적절한 보상 안내 가중치를 찾는 것이 중요하며, 과도한 가중치는 오히려 역효과를 낼 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (a) AlpacaEval performance against reward guidance weight. Increasing guidance weight initially improves, and then degrades performance.
> </details>



![](https://arxiv.org/html/2502.13917/x4.png)

> 🔼 이 그림은 추론 시 사용하는 확산 단계 수를 늘림에 따라 AlpacaEval 및 GSM8k 성능이 어떻게 변하는지 보여줍니다. 성능은 특정 지점까지는 단계 수가 증가함에 따라 향상되지만, 그 이후에는 더 이상 향상되지 않고 오히려 감소할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (b) AlpacaEval and GSM8k performance using increasing diffusion steps at inference time. Performance increases with number of steps up to a point.
> </details>



![](https://arxiv.org/html/2502.13917/x5.png)

> 🔼 이 그림은 미스트랄 v0.1 모델을 사용하여 확산 적응 훈련 단계의 수에 따른 알파카 평가 승률을 보여줍니다. 훈련 단계를 20만 단계까지 늘리면 성능이 크게 향상됨을 알 수 있습니다. 이는 더 많은 훈련 단계를 거칠수록 모델이 지시 사항을 따르는 능력이 향상됨을 시사합니다. 그림은 훈련 단계의 수가 증가함에 따라 승률이 어떻게 변하는지를 보여주는 곡선을 보여줍니다. 20만 단계를 지나면 승률이 더 이상 크게 향상되지 않음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (c) AlpacaEval winrate against number of diffusion adaptation steps. Going up to 200k steps provides significant improvements.
> </details>



![](https://arxiv.org/html/2502.13917/x6.png)

> 🔼 이 그림은 TESS 2 모델의 성능 분석 결과를 보여줍니다. (a)는 보상 안내 가중치에 따른 AlpacaEval 성능 변화를, (b)는 추론 시 사용하는 확산 단계 수에 따른 AlpacaEval 및 GSM8k 성능 변화를, (c)는 적응 훈련 단계 수에 따른 AlpacaEval 승률 변화를 각각 나타냅니다.  각 그래프는 TESS 2 모델의 성능 향상을 위한 하이퍼파라미터 조정 및 훈련 과정 최적화에 대한 통찰력을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Analysis Experiments on \modelname.
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