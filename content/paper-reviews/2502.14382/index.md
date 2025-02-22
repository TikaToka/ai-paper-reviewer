---
title: "S*: Test Time Scaling for Code Generation"
summary: "S*는 코드 생성에서 테스트 시간 컴퓨팅을 활용하여 정확성과 적용 범위를 크게 향상시키는 최초의 혼합 방식입니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 UC Berkeley",]
showSummary: true
date: 2025-02-20
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.14382 {{< /keyword >}}
{{< keyword icon="writer" >}} Dacheng Li et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-21 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.14382" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.14382" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/s-test-time-scaling-for-code-generation" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존 연구는 수학적 추론 분야에서 테스트 시간 컴퓨팅의 효과를 보여주었지만, 코드 생성 분야에는 거의 적용되지 않았습니다. 코드 생성은 실행을 통한 검증이 필요하기 때문에, 단순히 문자열 일치를 통한 검증이 가능한 수학적 추론과는 다릅니다. 이로 인해 코드 생성 모델의 정확성과 적용 범위를 높이는 데 어려움이 있었습니다.

본 논문에서는 이러한 문제를 해결하기 위해 S*라는 새로운 하이브리드 테스트 시간 확장 프레임워크를 제안합니다. S*는 기존의 병렬 확장에 순차적 확장을 결합하여 반복적 디버깅을 통해 코드 품질을 높이고, 적응적 입력 합성 메커니즘을 통해 최적의 솔루션을 선택합니다. 실험 결과, S*는 다양한 모델과 벤치마크에서 성능을 향상시키는 것을 보여주었습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} S*는 코드 생성을 위한 최초의 하이브리드 테스트 시간 확장 프레임워크로, 기존의 병렬 확장 패러다임에 순차적 확장을 통합합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} S*는 적응적 입력 합성 메커니즘을 통해 코드 품질을 개선하고, 다양한 모델과 벤치마크에 대한 실험 결과를 통해 일반성과 효율성을 입증합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} S*는 3B 모델이 GPT-40-mini를 능가하고, GPT-40-mini가 S*를 통해 01-preview를 능가하는 등, 다양한 모델에서 성능 향상을 보여줍니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **테스트 시간 확장을 코드 생성에 적용하는 최초의 하이브리드 프레임워크인 S*를 제시**하여 코드 생성 모델의 성능을 크게 향상시켰다는 점에서 중요합니다.  **기존의 병렬 확장 방식에 순차적 확장 방식을 통합**하고 **적응적 입력 합성 메커니즘**을 도입하여 코드 품질을 높였습니다. 이는 코드 생성 분야의 발전에 기여하며, 향후 연구를 위한 새로운 방향을 제시할 것입니다.  **다양한 모델과 벤치마크에 대한 실험 결과**는 S*의 **일반성과 효율성**을 보여주어,  연구자들에게 중요한 시사점을 제공합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.14382/x1.png)

> 🔼 그림 1은 S* 기법을 LiveCodeBench (v2) 벤치마크에 적용했을 때의 성능 향상을 보여줍니다. S*은 모델 크기에 상관없이 성능을 향상시키며, 추론 능력이 없는 모델이 추론 모델을 능가하고, 오픈 모델이 높은 추론 능력을 요구하는 o1 모델과 경쟁력을 갖추도록 합니다.  Qwen-Coder는 Qwen2.5-Coder-Instruct를, R1-Distill은 DeepSeek-R1-Distill-Qwen을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Performance improvement with S∗superscript𝑆S^{*}italic_S start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT in LiveCodeBench (v2) (Jain et al., 2024). S∗superscript𝑆S^{*}italic_S start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT consistently improves models across different sizes, allowing non-reasoning models to surpass reasoning models and open models to be competitive with o1 (high reasoning effort). 'Qwen-Coder' denotes 'Qwen2.5-Coder-Instruct,' (Hui et al., 2024) and 'R1-Distill' denotes 'DeepSeek-R1-Distill-Qwen.'  (Guo et al., 2025).
> </details>





{{< table-caption >}}
| Method | Qwen2.5-Coder-Instruct (0.5B) | Qwen2.5-Coder-Instruct (1.5B) | Qwen2.5-Coder-Instruct (3B) | Qwen2.5-Coder-Instruct (7B) | Qwen2.5-Coder-Instruct (14B) | Qwen2.5-Coder-Instruct (32B) | 4o-mini | R1-Distill (7B) | R1-Distill (14B) | R1-Distill (32B) | QwQ | o1-mini |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Zero-Shot | 1.2 | 7.0 | 18.4 | 29.4 | 44.8 | 47.4 | 40.9 | 48.4 | 63.2 | 69.1 | 62.1 | 76.5 |
| Majority Vote | 2.5 | 11.0 | 25.2 | 40.5 | 50.8 | 55.9 | 46.6 | 58.7 | 68.1 | 75.8 | 67.3 | 81.6 |
| Self-Debugging | 2.4 | 9.4 | 27.8 | 39.9 | 51.5 | 59.5 | 51.7 | 58.4 | 66.2 | 70.1 | 59.3 | 79.9 |
| S* | **10.9** | **27.6** | **42.7** | **54.4** | **64.6** | **70.1** | **61.3** | **73.2** | **82.8** | **85.7** | **76.3** | **85.3** |{{< /table-caption >}}

> 🔼 표 1은 LiveCodeBench (v2) 데이터셋에서 제로샷(zero-shot), 다수결 투표(majority voting) (Wang et al., 2022; Li et al., 2022), 자가 디버깅(self-debugging) (Chen et al., 2023), 그리고 제안된 S* 방법의 성능을 Pass@1 지표로 비교한 표입니다.  굵은 글씨는 각 모델에서 가장 좋은 성능을 나타냅니다.  'R1-Distill', 'QwQ', '4o-mini'는 각각 'DeepSeek-R1-Distill-Qwen' (Guo et al., 2025), 'QwQ-32B-Preview' (Qwen, 2024), 그리고 'GPT-4o-mini' (Achiam et al., 2023)를 줄여서 표기한 것입니다.  S*는 다른 기준 방법들보다 일관되게 더 나은 성능을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Pass@1 of zero-shot, majority voting (Wang et al., 2022; Li et al., 2022), self-debugging (Chen et al., 2023), and S∗superscript𝑆S^{*}italic_S start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT on LiveCodeBench (v2). Bold text denotes the best performance. 'R1-Distill', 'QwQ', '4o-mini' is short for 'DeepSeek-R1-Distill-Qwen' (Guo et al., 2025), 'QwQ-32B-Preview' (Qwen, 2024), and 'GPT-4o-mini' (Achiam et al., 2023) respectively. S∗superscript𝑆S^{*}italic_S start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT consistently outperforms other baselines.
> </details>





### In-depth insights


#### Hybrid Scaling
본 논문에서 제시된 **하이브리드 스케일링 기법**은 기존의 병렬 스케일링과 순차적 스케일링의 장점을 결합하여 코드 생성 성능을 크게 향상시키는 데 초점을 맞추고 있습니다. **병렬 스케일링**은 여러 개의 코드 샘플을 동시에 생성하여 다양한 솔루션을 확보하는 반면, **순차적 스케일링**은 반복적인 디버깅을 통해 생성된 코드를 개선하는 과정입니다. 하이브리드 접근 방식은 이러한 두 가지 스케일링 방법을 통합하여 코드 품질을 향상시키고, 적응적 입력 합성 메커니즘을 통해 최적의 솔루션을 효율적으로 선택할 수 있도록 합니다.  이러한 통합 전략은 코드 생성의 특수한 과제, 즉 실행을 통한 정확성 검증의 어려움을 해결하는 데 중요한 역할을 합니다.  **실행 기반 정보**를 활용하여 코드의 정확성을 평가하고, 그 결과를 다음 단계의 코드 생성 및 선택에 반영함으로써 더욱 정확하고 효율적인 코드 생성이 가능해집니다.  결론적으로, 본 논문의 하이브리드 스케일링은 코드 생성 분야에서 **성능 향상**을 위한 효과적인 전략으로서 큰 가능성을 보여줍니다.

#### Adaptive Selection
적응적 선택(Adaptive Selection)은 본 논문에서 제시된 코드 생성을 위한 새로운 테스트 시간 확장 프레임워크의 핵심 구성 요소입니다. 이 방법은 기존의 병렬 샘플링 방식의 한계를 극복하기 위해 **순차적 샘플링(Sequential Scaling)**과 결합하여 사용됩니다.  기존의 방법들은 무작위로 테스트 입력을 생성하는 경우가 많아 후보 솔루션들을 효과적으로 구별하지 못하는 문제가 있었습니다.  하지만 적응적 선택은 **LLM(Large Language Model)**을 활용하여 쌍으로 비교될 후보 샘플들을 구별하는 데 유용한 테스트 입력을 적응적으로 생성합니다.  **실행 기반 정보(Execution-grounded Information)**를 활용하여 올바른 솔루션을 강력하게 식별하는 데 도움이 됩니다.  즉, 단순히 샘플들을 비교하는 것이 아니라 실제 실행 결과를 바탕으로 최적의 샘플을 선택하는 더욱 정교한 방법을 사용함으로써 선택 정확도를 향상시키는 것입니다.  **이러한 적응적이고 실행 기반의 선택 메커니즘은 다양한 모델들과 벤치마크에서 일관되게 성능 향상을 보여주며, 특히 큰 모델의 경우 더욱 효과적임을 보였습니다.**  이는 코드 생성에서 테스트 시간 확장의 효율성과 정확성을 크게 높이는 혁신적인 접근 방식임을 시사합니다.

#### Iterative Debugging
반복적 디버깅은 코드 생성 모델의 성능을 향상시키는 핵심 전략으로 제시되었습니다. 이는 **병렬 샘플링**의 한계를 극복하기 위한 **순차적 스케일링** 기법으로, 생성된 코드를 공개 테스트 케이스로 실행하여 결과(출력값 또는 에러 메시지)를 모델에 다시 입력하여 코드를 반복적으로 다듬는 과정입니다.  이를 통해 모델은 **에러를 수정하고 정확도를 높이며, 솔루션의 범위를 넓힐 수 있습니다.**  단순히 무작위로 테스트 입력을 생성하는 기존 방식과 달리, **반복적 디버깅은 실행 결과를 토대로 모델의 학습 방향을 효과적으로 제어**합니다. 특히, 코드 생성의 경우,  **정답 여부 확인이 문자열 일치만으로는 불가능**하다는 점을 고려할 때,  실행 기반의 피드백이 매우 중요하며, 이러한 점에서 **반복적 디버깅은 코드 생성 모델의 성능 향상에 크게 기여**하는 것으로 평가됩니다.  하지만, **과도한 반복은 오히려 성능 저하를 초래**할 수 있으므로, 적절한 반복 횟수를 결정하는 것이 중요한 요소입니다.

#### Ablation Studies
본 논문의 "절제 연구(Ablation Studies)" 부분은 제안된 방법의 각 구성 요소가 전체 성능에 미치는 영향을 면밀히 분석합니다. **병렬 확장(Parallel Scaling)**에 대한 연구는 온도(temperature)와 샘플 수(number of samples)와 같은 하이퍼파라미터가 성능에 미치는 영향을 보여줍니다. 적절한 온도는 다양성과 정확성 사이의 균형을 맞추는 데 중요하며, 샘플 수를 늘리면 성능이 로그선형적으로 향상됩니다.  **순차적 확장(Sequential Scaling)**에 대한 연구는 반복적인 디버깅(iterative debugging) 전략의 효과를 다양한 변형을 통해 검증합니다.  **선택 전략(Selection Policy)**에 대한 연구는 제안된 적응형 입력 합성 방법이 다른 방법들보다 더 신뢰할 수 있는 샘플 선택을 제공함을 보여줍니다.  **결론적으로, 절제 연구는 각 구성 요소의 중요성을 강조하고, 전체 시스템의 견고성과 효율성을 입증합니다.**  특히, 하이퍼파라미터 최적화 및 적응형 입력 합성을 통한 성능 향상은 본 연구의 중요한 발견입니다. 이러한 분석 결과는 향후 연구 방향을 제시하고, 모델 성능을 더욱 개선하는 데 기여할 것입니다.

#### Future Directions
본 논문에서 제시된 S* 프레임워크는 코드 생성 분야에서 **테스트 시간 확장**의 새로운 가능성을 보여주지만, 여전히 개선의 여지가 많습니다. **미래 연구 방향**으로는 첫째, 더욱 **정교한 오류 수정 메커니즘** 개발이 필요합니다. 현재 S*는 반복적인 디버깅을 통해 코드를 개선하지만, 더욱 효율적이고 지능적인 오류 분석 및 수정 방법을 연구해야 합니다. 둘째, **다양한 코드 생성 모델 및 벤치마크**에 대한 적용성을 확대해야 합니다. 본 논문에서는 특정 모델과 벤치마크에 대해서만 실험을 수행했으므로, 다른 모델과 벤치마크에서도 S*의 성능을 검증하고 일반화 가능성을 높여야 합니다. 셋째, **자원 효율적인 테스트 시간 확장 기법** 연구가 중요합니다. S*는 테스트 시간에 많은 계산 자원을 필요로 하므로, 자원 소모를 줄이면서 성능을 유지하는 기법을 개발하는 것이 필요합니다. 마지막으로, **실제 응용 시나리오**에 대한 적용성을 검토해야 합니다. 본 논문에서는 주로 경쟁 기반 코드 생성 문제에 초점을 맞추었지만, 실제 소프트웨어 개발 환경에서 S*의 유용성을 평가하고 개선해야 합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.14382/x2.png)

> 🔼 그림 2는 제안된 방법인 S*의 개요를 보여줍니다. S*는 두 가지 주요 단계, 즉 생성 단계와 선택 단계로 구성됩니다. 생성 단계에서는 반복적인 디버깅을 통해 병렬 샘플을 향상시킵니다. 각 샘플은 인터프리터를 통해 실행되는 공개 테스트 사례를 사용하여 테스트되며, 출력값이나 오류 메시지는 다음 샘플 생성을 안내하는 데 사용됩니다. 선택 단계에서는 쌍으로 이루어진 샘플들을 구별하는 입력값을 생성하도록 LLM에 프롬프트를 제시하여 최상의 샘플을 선택합니다. 그런 다음 실제 실행 결과를 활용하여 LLM이 최적의 선택을 결정하도록 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2:  Overview of S∗superscript𝑆S^{*}italic_S start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT. Stage 1: Generation—S∗superscript𝑆S^{*}italic_S start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT enhances parallel samples through iterative debugging. Each sample is tested using public test cases executed via an interpreter, with outputs and/or error messages used to guide the next round of sample generation. Stage 2: Selection—S∗superscript𝑆S^{*}italic_S start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT selects the best sample by prompting an LLM to generate inputs that differentiate between paired samples, then leveraging actual execution results to inform the LLM to determine the optimal choice.
> </details>



![](https://arxiv.org/html/2502.14382/x3.png)

> 🔼 그림 3은 제안된 방법인 S*의 성능 향상 효과를 보여줍니다.  S*를 적용한 Qwen2.5-Coder-14B 모델은 S* 없이 동작하는 o1-preview 모델보다 성능이 우수하며,  마찬가지로 S*를 적용한 DeepSeek-R1-Distill-Qwen-14B 모델 또한 S* 없이 동작하는 o1-mini 모델보다 성능이 뛰어남을 보여줍니다. 이는 S*가 다양한 종류의 모델에서 일관되게 성능 향상을 가져온다는 것을 시각적으로 보여주는 결과입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3:  Ablation of S∗superscript𝑆S^{*}italic_S start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT performance benefits: Qwen2.5-Coder-14B-Instruct (denoted as Qwen-Coder-14B) (Hui et al., 2024) with S∗superscript𝑆S^{*}italic_S start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT can surpass o1-preview without S∗superscript𝑆S^{*}italic_S start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT. DeepSeek-R1-Distill-Qwen-14B (denoted as R1-Distill-14B) (Guo et al., 2025) with S∗superscript𝑆S^{*}italic_S start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT outperforms o1-mini without S∗superscript𝑆S^{*}italic_S start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT.
> </details>



![](https://arxiv.org/html/2502.14382/x4.png)

> 🔼 그림 4는 두 가지 하이퍼파라미터(온도와 샘플 수)가 코드 생성 성능에 미치는 영향을 보여줍니다. 왼쪽 그래프는 온도의 영향을 보여줍니다. 온도가 0.7일 때 다양성과 품질이 적절히 조화되어 Pass@N이 가장 높아집니다. 반면, 온도가 0.95일 때는 Pass@N이 더 이상 향상되지 않고 오히려 코드 품질이 저하될 가능성이 있습니다. 오른쪽 그래프는 샘플 수의 영향을 보여줍니다. 샘플 수가 증가함에 따라 성능이 로그 선형적으로 향상됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: The effect of hyper-parameters. Left: The impact of temperature. A moderate temperature (0.7) balances diversity and quality, leading to higher Pass@N. In contrast, a higher temperature (0.95) does not further improve Pass@N, potentially degrading code quality. Right: The effect of increasing the number of samples. Performance improves log-linearly.
> </details>



![](https://arxiv.org/html/2502.14382/x5.png)

> 🔼 그림 5는 GPT-4o mini, Qwen2.5-Coder-7B-Instruct, Qwen2.5-Coder-32B-Instruct 세 가지 모델에 대해, 다양한 수의 병렬 샘플(N)을 사용하여 인 컨텍스트 예시를 활용했을 때의 성능을 보여줍니다.  각 모델별로 병렬 샘플 수(N)가 증가함에 따라 성능 향상이 어떻게 나타나는지, 그리고 성능 향상의 정도가 모델의 크기나 종류에 따라 어떻게 달라지는지를 시각적으로 나타낸 것입니다.  즉, 인 컨텍스트 학습이 병렬 샘플링과 결합되었을 때 각 모델의 성능 개선에 미치는 영향을 보여주는 그림입니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Performance with in-context examples across different numbers of parallel samples (N𝑁Nitalic_N), for GPT-4o mini, Qwen2.5-Coder-7B-Instruct, and Qwen2.5-Coder-32B-Instruct.
> </details>



![](https://arxiv.org/html/2502.14382/x6.png)

> 🔼 그림 6은 반복적 디버깅 접근 방식 세 가지(공개 테스트, 생성된 테스트 추가, 마지막 라운드 컨텍스트)를 비교한 그래프입니다. N=8, 온도=0.7, 최대 4라운드 디버깅으로 얻은 결과를 보여줍니다. 각 접근 방식은 코드 생성 성능에 미치는 영향을 보여주며, 특히 공개 테스트만 사용하는 방식과 생성된 테스트를 추가하는 방식, 그리고 마지막 라운드 컨텍스트만 활용하는 방식을 비교 분석합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Comparison of three iterative debugging approaches: Public Tests, + Generated Tests and Last Round Context. Results are obtained with N=8𝑁8N=8italic_N = 8, temperature=0.7temperature0.7\text{temperature}=0.7temperature = 0.7 and up to four rounds of debugging.
> </details>



![](https://arxiv.org/html/2502.14382/x7.png)

> 🔼  그림 7은 반복적인 디버깅 과정을 위한 프롬프트(명령어)를 보여줍니다.  이 프롬프트는 모델이 이전 라운드의 코드와 테스트 결과 피드백을 바탕으로 코드의 오류 원인을 분석하고 코드를 수정하도록 유도합니다.  프롬프트는 질문, 이전 라운드의 추론, 생성된 코드, 테스트 결과 등의 필드로 구성되어 있으며, 모델은 이러한 정보를 사용하여 코드를 개선하고  `[[ ## completed ## ]]` 마커로 완료를 표시합니다.  이는 모델이 코드 생성 과정에서 지속적으로 오류를 수정하고 개선해나가도록 하는 반복적 디버깅 전략의 핵심 구성 요소입니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: The prompt for iterative debugging.
> </details>



![](https://arxiv.org/html/2502.14382/x8.png)

> 🔼 그림 8은 코드 생성 문제에 대한 AI 생성 솔루션을 테스트하기 위한 잠재적 입력의 완전한 집합을 생성하는 프롬프트를 보여줍니다.  이 프롬프트는 빈 문자열이나 배열과 같은 에지 케이스, 복잡하고 어려운 입력, 버그를 최대화할 수 있는 기타 입력 등 다양한 종류의 입력을 생성하도록 설계되었습니다.  생성된 테스트 케이스는 JSON 형식으로 제공되어 입력과 예상 출력이 명확하게 구분됩니다.  이를 통해 모델의 출력이 문제의 예상되는 형식과 구조와 일치하는지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: The prompt for generating test cases.
> </details>



![](https://arxiv.org/html/2502.14382/x9.png)

> 🔼 그림 9는 코드 생성을 위한 프롬프트 예시를 보여줍니다.  간단히 말해, 이 프롬프트는 코드 생성 모델에게 문제 설명을 주고, 그에 대한 파이썬 함수 코드를 생성하도록 지시합니다.  함수 본문만 작성해야 하며, 다른 어떤 것도 포함하면 안 됩니다.  프롬프트는  `prompt`, `reasoning`, `code`, `completed`  필드를 사용하여 구조화되어 있고,  모델은 이 구조에 따라 응답해야 합니다.  이 프롬프트는 논문의 방법론 섹션에서 설명하는 코드 생성 과정의 일부입니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: The prompt for code generation.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | Zero-Shot | S* | S* (Oracle) |
|---|---|---|---|
| Qwen-Coder-7B | 1.8 | **10.9** (+9.1) | 12.1 |
| Qwen-Coder-14B | 9.7 | **21.8** (+12.1) | 27.9 |
| Qwen-Coder-32B | 10.1 | **21.8** (+11.7) | 29.7 |
| gpt-4o-mini | 9.1 | **23.0** (+13.9) | 28.5 |
| o1-mini | 32.7 | **48.5** (+15.8) | 58.2 |{{< /table-caption >}}
> 🔼 표 2는 CodeContests 벤치마크에서 제안된 S* 방법을 포함한 다양한 방법들의 성능을 비교 분석한 결과를 보여줍니다.  각 모델(Qwen-Coder, R1-Distill, GPT-40-mini, o1-mini)별로 Zero-shot, S* 적용, S*에 오라클(Oracle) 설정을 추가한 경우의 Pass@1 점수를 비교하여 S*의 성능 향상 효과를 보여줍니다.  굵은 글씨는 각 모델에서 가장 높은 성능을 나타냅니다. Qwen-Coder는 Qwen2.5-Coder-Instruct를, R1-Distill은 DeepSeek-R1-Distill-Qwen을 의미합니다. 이 표는 LiveCodeBench 뿐 아니라 CodeContests 벤치마크에서도 S*의 성능 향상이 일관되게 나타남을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Performance comparison on CodeContests. Bold text denotes the best performance of the same model. 'Qwen-Coder' is short for 'Qwen2.5-Coder-Instruct', 'R1-Distill' is short for 'DeepSeek-R1-Distill-Qwen'. S∗superscript𝑆S^{*}italic_S start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT consistently improves model performance on benchmark beyond LiveCodeBench.
> </details>

{{< table-caption >}}
| Model | Public | Generated | LLM | Adaptive Input |
|---|---|---|---|---|
|  | Only | Tests | Judge | Synthesis (Ours) |
| Qwen-Coder-7B | 42.3 | 42.3 | 42.3 | **44.5** |
| Qwen-Coder-32B | 54.6 | 57.8 | 55.5 | **58.3** |
| GPT-4o mini | 54.1 | 55.2 | 56.3 | **57.3** |
| QwQ-32B-Preview | 64.3 | 65.9 | 68.6 | **69.7** |
| Avg. | 53.8 | 53.1 | 55.6 | **57.5** |{{< /table-caption >}}
> 🔼 이 표는 LiveCodeBench(v4) 데이터셋을 사용하여 다양한 코드 선택 방법들의 성능을 Pass@1 지표로 비교 분석한 결과를 보여줍니다.  각 모델에 대해 Zero-shot, Public Tests만 사용, 생성된 테스트 케이스 사용, 그리고 본 논문에서 제안하는 적응적 입력 합성 방법의 성능을 비교합니다.  굵은 숫자는 각 모델에서 가장 높은 성능을 나타냅니다. Qwen-Coder는 Qwen2.5-Coder-Instruct를, R1-Distill은 DeepSeek-R1-Distill-Qwen을 의미하며, 모든 실험은 N=8, temperature=0.7 조건에서 진행되었습니다.  본 논문의 적응적 입력 합성 방법이 다른 방법들보다 더 높은 정확도를 달성함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Pass@1 Performance comparison between different selection methods on LiveCodeBench(v4). Bold text denotes the best performance of the same model. 'Qwen-Coder', 'R1-Distill' is short for 'Qwen2.5-Coder-Instruct' and 'DeepSeek-R1-Distill-Qwen'. Results are obtained with N=8 and temperature=0.7. Our Adaptive Input Synthesis method achieves better accuracy over other methods.
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