---
title: "SPaR: Self-Play with Tree-Search Refinement to Improve Instruction-Following in Large Language Models"
summary: "Self-play with refinement boosts instruction-following in LLMs."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Tsinghua University",]
showSummary: true
date: 2024-12-16
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.11605 {{< /keyword >}}
{{< keyword icon="writer" >}} Jiale Cheng et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-17 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.11605" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.11605" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/spar-self-play-with-tree-search-refinement-to" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

**LLMs struggle with complex instructions**, often getting distracted by irrelevant details. Current methods for training LLMs with preferences create comparisons between entirely different responses, which worsens the issue. This introduces variations that are unrelated to actually following the instructions and makes it difficult for models to identify the key factors that lead to correct responses. **Existing preference learning methods do not address this subtle but crucial issue**.  As a result, LLMs fail to accurately reflect subtle nuances within the instructions and their output.  This limitation hinders the effectiveness of preference learning in enhancing instruction-following ability, especially for multi-constraint tasks.

**SPAR, a self-play framework with tree-search refinement, is proposed** to address the limitations of current preference learning techniques. LLMs learn by **playing against themselves**, refining their own imperfect responses. **Tree search** systematically explores possible refinements, while minimizing interference.  This approach helps LLMs focus on the key differences that lead to better instruction following, without getting lost in unrelated details.  Experiments show significant improvements over other self-improvement methods.  Impressively, SPAR even surpasses GPT-4-Turbo on a key benchmark, demonstrating its effectiveness in enhancing instruction-following capability.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} Self-play with tree-search refinement significantly improves instruction following in LLMs. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} The proposed method, SPAR, outperforms existing techniques and even surpasses GPT-4-Turbo on certain benchmarks. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} SPAR enhances model scalability and shows potential for continuous self-improvement without relying on bootstrapping data or human feedback {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**SPAR offers a novel approach to improving instruction-following in LLMs, which is crucial for aligning these powerful models with human intent.**  By focusing on refinement and minimizing interference, it enhances both performance and robustness. The demonstrated scalability across different model sizes and the potential for continuous self-improvement make SPAR **a significant contribution to the field**. This work opens up **new possibilities for developing more aligned and reliable LLMs**, impacting various applications. The iterative nature and self-play aspect offer a unique perspective on model training, potentially inspiring further research in autonomous LLM alignment and improvement.

------
#### Visual Insights



![](https://arxiv.org/html/2412.11605/x1.png)

> 🔼 이 그림은 독립적으로 샘플링된 여러 응답에서 발생하는 간섭 요인(스토리 내용)의 예시(왼쪽)와 이러한 요인을 배제하고 핵심 차이점(마지막 문장)을 강조하여 반복적으로 학습된 LLaMA3-8B-Instruct의 성능 향상을 가져온 개선된 응답 쌍(오른쪽)을 보여줍니다. 왼쪽 부분은 주어진 지시(Write a story and end it with 'The devil is in the details.')에 대해 서로 다른 이야기(<Hansel and Gretel>, <Little Red Riding Hood>)를 생성하는 모델의 예시를 보여줍니다. 오른쪽 부분은 IFEval 벤치마크에서의 평균 점수를 나타내는 그래프로, 세 번의 반복 학습 후 SPAR가 직접 샘플링된 쌍보다 더 나은 성능을 보여줌을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: An example of the interfering factors (story content) in independently sampled multiple responses (Left). Refined response pairs exclude these factors, highlight the key difference (ending sentence), and lead to improved performance on iteratively trained LLaMA3-8B-Instruct (Right).
> </details>





{{< table-caption >}}
| Model | IFEval | | | | | FollowBench (SSR) | | | | | |
|---|---|---|---|---|---|---|---|---|---|---|---|
| | P (L) | I (L) | P (S) | I (S) | Avg. | Lv-1 | Lv-2 | Lv-3 | Lv-4 | Lv-5 | Avg. |
|---|---|---|---|---|---|---|---|---|---|---|---|
| **LLaMA3-8B Models** | | | | | | | | | | | |
| LLaMA3-8B-Instruct | 77.6 | 84.5 | 70.6 | 78.9 | 77.9 | 69.4 | 62.2 | 63.1 | 61.9 | 60.9 | 63.5 |
| AutoIF-8B† | 43.1 | 56.0 | 28.8 | 42.2 | 42.5 | 54.6 | 52.1 | 50.0 | 49.0 | 43.7 | 49.9 |
| SELF | 78.2 | 84.5 | 76.0 | 82.9 | 80.4 | 68.3 | 65.7 | 65.2 | 62.2 | 62.4 | 64.8 |
| Humpback | 72.5 | 80.2 | 70.1 | 78.1 | 75.2 | 66.8 | 66.1 | 67.2 | 60.2 | 62.6 | 64.6 |
| Self-Rewarding | 77.3 | 84.2 | 74.1 | 81.7 | 79.3 | 72.8 | 66.6 | 66.8 | **64.9** | 64.1 | 67.0 |
| Meta-Rewarding | 77.8 | 84.1 | 75.4 | 82.3 | 79.9 | 73.9 | 71.9 | 66.0 | 62.3 | 62.6 | 67.3 |
| SPaR-8B-SFT | 75.4 | 82.5 | 73.4 | 80.6 | 78.0 | 73.9 | 67.4 | 68.1 | 63.1 | 61.3 | 66.8 |
| SPaR-8B-DPO-iter1 | 78.0 | 84.7 | 75.8 | 82.6 | 80.3 | **75.3** | 67.7 | 67.6 | 64.7 | 62.3 | 67.5 |
| SPaR-8B-DPO-iter2 | 78.9 | 85.0 | 77.1 | 83.3 | 81.1 | 73.9 | 71.9 | 69.1 | 64.0 | 62.2 | 68.2 |
| SPaR-8B-DPO-iter3 | **79.9** | **85.4** | **78.0** | **83.7** | **81.8** | 73.0 | **72.3** | **70.0** | 64.1 | **64.7** | **68.8** |
| 
cdashline{1-12}  w/ tree search | 82.4 | 87.5 | 79.5 | 85.3 | 83.7 | 73.9 | 71.7 | 70.3 | 66.8 | 64.1 | 69.4 |
| **GLM-4-9B Models** | | | | | | | | | | | |
| GLM-4-9B-Chat | 71.5 | 79.9 | 68.0 | 77.2 | 74.2 | 80.8 | 75.1 | 67.4 | 64.3 | **65.4** | 70.6 |
| SPaR-9B-SFT | 71.5 | 80.5 | 68.8 | 78.1 | 74.7 | 79.4 | 70.9 | 68.2 | 65.1 | 63.7 | 69.5 |
| SPaR-9B-DPO-iter3 | **77.3** | **84.1** | **73.6** | **81.4** | **79.1** | **82.7** | **76.7** | **67.9** | **68.3** | 64.2 | **72.0** |
| **LLaMA3-70B Models** | | | | | | | | | | | |
| LLaMA3-70B-Instruct | 83.7 | 88.9 | 77.1 | 83.8 | 83.4 | 77.1 | 72.5 | 69.4 | 68.7 | 66.3 | 70.8 |
| AutoIF-70B† | **85.6** | **90.4** | 80.2 | 86.7 | 85.7 | 71.0 | 67.2 | 66.2 | 64.6 | 63.5 | 66.5 |
| SPaR-70B-DPO-iter3 | **85.6** | 90.2 | **81.3** | **87.3** | **86.1** | **80.3** | **75.7** | **71.4** | **73.7** | **70.5** | **74.3** |{{< /table-caption >}}

> 🔼 이 표는 여러 대규모 언어 모델(LLM)을 여러 번 반복 학습시켰을 때 명령어를 얼마나 잘 따르는지 평가한 결과를 보여줍니다. 각 LLM마다 최고 성능을 굵게 표시했습니다. 자세한 내용은 논문의 표 6을 참조하세요. 평가 지표는 크게 명령어 수준(I)과 프롬프트 수준(P)으로 나뉘며, 각각 느슨한 평가(L)와 엄격한 평가(S)로 세분화됩니다. 또한, 추론 과정에서 트리 탐색 기법을 사용했을 때의 결과는 녹색으로 강조 표시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Main results of iteratively trained LLMs on instruction-following benchmarks (Cf. Table 6 for full results). P stands for prompt level, and I represents instruction level. L and S denote loose and strict evaluations, respectively. Avg. indicates average results and Lv means level. Results using inference-time tree search are highlighted in green. The highest results for each backbone model is bolded. Scores marked with † are sourced directly from the original paper.
> </details>





### In-depth insights


#### Preference Bias
**선호 편향**은 강화 학습에서 중요한 문제입니다. 모델이 특정 응답을 선호하게 되면 **다양성 부족**과 **편향된 출력**이 발생할 수 있습니다. 이는 훈련 데이터의 **불균형**, **보상 함수 설계의 결함**, 또는 **탐색 전략의 부적절성**에서 기인할 수 있습니다. 선호 편향을 완화하기 위한 방법으로는 **다양한 데이터 수집**, **보상 함수 재설계**, **규칙 기반 보상 추가**, **역강화 학습**, **탐색-활용 균형 조정** 등이 있습니다. **SPAR**와 같은 자기 대전 기반 학습 및 트리 탐색 기반 개선은 **선호 편향을 줄이고** **지시 따르기 성능을 향상**시키는 데 도움이 될 수 있습니다. 하지만 자체 평가에 대한 **객관적인 검증** 또한 중요하며, **인간 피드백**을 통한 지속적인 개선이 필요합니다.

#### Self-Play Refinement
**셀프 플레이 개선**은 LLM의 명령어 준수 능력 향상을 위한 핵심 전략입니다. LLM이 **자신과 대결하며 학습**하는 방식으로, 행위자와 개선자 역할을 번갈아 수행합니다. 행위자는 주어진 명령에 대한 응답을 생성하고, 개선자는 이 응답을 평가하고 개선합니다. 이러한 **반복적 과정**을 통해 모델은 **미묘한 차이**를 학습하고 명령어 준수 능력을 향상시킵니다. **트리 검색 기반 개선**은 효과적인 학습 데이터를 생성하는 핵심 요소입니다. 이는 단순히 최적의 응답을 찾는 것뿐 아니라, 다양한 응답을 탐색하여 모델이 **핵심적인 차이**를 학습할 수 있도록 돕는 데 중점을 둡니다. 즉, 셀프 플레이 개선은 **지속적인 자기 개선**을 위한 유효한 전략입니다.

#### Iterative LLM Training
**반복적 LLM 훈련**은 LLM의 성능을 점진적으로 향상시키는 강력한 기술입니다. 이 접근 방식은 모델의 자체 예측, 외부 피드백 또는 강화 학습에서 파생된 데이터를 사용하여 모델을 미세 조정하는 여러 훈련 주기를 포함합니다. 각 주기에서 모델은 새로운 데이터에 대해 훈련되어 이전 반복의 결함을 해결하고 성능을 향상시킵니다. 이 반복적 프로세스를 통해 모델은 보다 정확하고 효율적이며 다양한 작업에 적합하게 발전할 수 있습니다. 그러나 **과적합** 및 **계산 비용**과 같은 문제는 신중하게 고려해야 합니다. 또한, 각 반복에 사용되는 데이터의 품질이 최종 성능에 큰 영향을 미칠 수 있으므로 데이터 선택 및 정제 과정에서 주의를 기울여야 합니다. 전반적으로 반복적 LLM 훈련은 **지속적인 자기 개선**을 가능하게 하는 유망한 방법이지만 성공적인 구현을 위해서는 세심한 계획과 실행이 필요합니다.

#### Instruction Following
**명령어 준수**는 대규모 언어 모델(LLM)의 핵심 기능으로, 주어진 명령을 정확히 이해하고 따르는 능력을 의미합니다. 이는 복잡한 작업을 수행하고 다양한 상황에 대응하는 LLM의 성능을 좌우하는 중요한 요소입니다. 명령어 준수 능력 향상을 위해 **다양한 평가 벤치마크**가 개발되었으며, 이를 통해 모델의 성능을 객관적으로 측정하고 개선 방향을 설정할 수 있습니다. 또한, **지속적인 자기 개선 및 강화 학습 기법**을 통해 명령어 준수 능력을 더욱 발전시킬 수 있습니다. **미묘한 차이를 인식하고 반영하는 능력**은 고품질의 명령어 준수를 위한 중요한 요소이며, 이를 위해 **자가 학습 및 검색 기반 개선 전략** 등 다양한 방법이 연구되고 있습니다. 궁극적으로 명령어 준수는 LLM이 인간과 자연스럽고 효율적으로 상호 작용하는 데 필수적인 능력입니다.

#### IFEval Benchmark
**IFEval 벤치마크**는 코드 기반 평가를 위해 특별히 고안된 541개의 검증 가능한 명령어를 제공합니다. 키워드 빈도, 단어 수와 같은 작업을 포함하여 25가지 유형의 검증 가능한 명령어를 다룹니다. 객관적인 평가를 가능하게 하므로 코드 생성 및 이해 능력을 평가하는 데 적합합니다. **IFEval**은 명령어를 따르는 능력을 엄격하게 평가하므로 미묘한 차이에도 민감합니다. 따라서 **IFEval**에서 좋은 성능을 보이는 모델은 **복잡한 명령어를 정확히 따르는 데 능숙**하다고 볼 수 있습니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.11605/x2.png)

> 🔼 SPaR은 액터와 리파이너, 두 개의 모델을 사용하는 자기 개선 프레임워크입니다. 그림 2는 이 프레임워크의 반복적인 훈련 과정을 보여줍니다. t번째 반복에서 리파이너 Rt는 액터 Mt가 생성한 응답을 평가하여 부정적인 데이터를 수집합니다. 그런 다음 트리 검색 알고리즘을 사용하여 이러한 불완전한 응답을 개선합니다. 마지막으로, 수집 및 개선된 데이터를 사용하여 액터와 리파이너를 다음 반복을 위해 최적화합니다. 이러한 반복적인 자기 플레이 과정을 통해 모델은 지속적으로 자기 개선을 달성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: SPaR iterative training framework. At iteration t𝑡titalic_t, the refiner Rtsubscript𝑅𝑡R_{t}italic_R start_POSTSUBSCRIPT italic_t end_POSTSUBSCRIPT first judges the generated responses from the actor Mtsubscript𝑀𝑡M_{t}italic_M start_POSTSUBSCRIPT italic_t end_POSTSUBSCRIPT to collect negative data. Next, a tree-search algorithm is employed to refine these imperfect responses. Finally, using the data from the above steps, we can optimize the actor and refiner for the next iteration, aiming for continuous self-improvement.
> </details>



![](https://arxiv.org/html/2412.11605/extracted/6072122/figures/baseline.png)

> 🔼 이 그림은 SPaR-8B 모델이 IFEval 벤치마크에서 다른 기준선보다 성능이 우수함을 보여줍니다. x축은 학습 반복 횟수를 나타내고 y축은 IFEval의 평균 점수를 나타냅니다. SPaR-8B는 모든 반복에서 Self-rewarding, Meta-rewarding, SELF와 같은 다른 자가 개선 방법을 능가합니다. 또한 GPT-4-Turbo의 성능도 능가합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Comparison with baseline methods across iterations (Cf. Figure 9 for SPaR-7B). SPaR-8B consistently surpasses all baselines.
> </details>



![](https://arxiv.org/html/2412.11605/extracted/6072122/figures/decoding.png)

> 🔼 이 그림은 합성 데이터 실험 결과를 보여줍니다. 왼쪽은 문자 시퀀스 생성, 오른쪽은 이야기 시작/끝 생성 작업에 대한 결과입니다. 문자 시퀀스 생성 작업에서 간섭 쌍은 대문자 비율(간섭 요소)을 빠르게 학습하지만 개선 쌍보다 성능이 낮습니다. 이야기 시작/끝 생성 작업에서 개선 쌍은 간섭 쌍보다 성능이 뛰어나며, 간섭 쌍은 0단계에서 원래 모델보다 성능이 낮습니다. 즉, 개선 쌍을 사용하면 작업의 핵심 차이점에 집중하여 성능이 향상되고 간섭 요소를 최소화하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Synthetic data experiment results: Character Sequence Generation (left) and Start/End Story Generation (right). For Character Sequence Generation, interfering pairs show rapid learning of the uppercase ratio (interfering factor) but perform worse than refinement pairs. In the Start/End Story Generation task, refinement pairs outperform interfering pairs, which even underperform the original model at step 0.
> </details>



![](https://arxiv.org/html/2412.11605/extracted/6072122/figures/taxonomy.png)

> 🔼 이 표는 행위자 모델에 대한 절제 연구 결과를 보여줍니다. 'w/o 트리 검색', 'w/o 반복 훈련', 'w/o 개선'은 각각 트리 검색, 반복 훈련, 개선 데이터 없이 SPAR를 훈련시켰을 때의 결과를 나타냅니다. 이러한 요소들을 제거하면 성능이 크게 저하되는 것을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Ablation study on the actor.
> </details>



![](https://arxiv.org/html/2412.11605/x3.png)

> 🔼 이 표는 재구성기(refiner)에 대한 절제 연구(ablation study) 결과를 보여줍니다. 재구성기는 tree-search refinement 과정과 반복적인 훈련 과정을 포함하는 SPAR의 핵심 요소 중 하나입니다. 표 5는 tree-search refinement 없이, 혹은 반복적인 훈련 없이 재구성기를 훈련했을 때의 성능 저하를 보여줍니다. 특히, 자연어(Natural) 및 적대적(Adversarial) 입력에 대한 정확도(Acc)와 F1 점수 모두 감소하는 것을 확인할 수 있습니다. 이는 tree-search refinement와 반복적인 훈련이 재구성기의 성능 향상에 중요한 역할을 한다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Ablation study on the refiner.
> </details>



![](https://arxiv.org/html/2412.11605/x4.png)

> 🔼 이 그림은 추론 시간(응답 생성 횟수로 측정)을 늘려 SPAR-8B-DPO-iter3 모델의 성능을 평가한 결과를 보여줍니다. 그리디 디코딩(Greedy Decoding), 베스트-오브-N 생성(Best-of-N), 너비 우선 탐색(BFS), 깊이 우선 탐색(DFS) 등 다양한 디코딩 전략의 성능을 비교합니다. 추론 시간이 늘어남에 따라 모든 방법의 성능이 향상되는 것을 볼 수 있습니다. 특히 트리 탐색 기반 개선(BFS와 DFS)은 베스트-오브-N 생성보다 결국 더 나은 결과를 달성합니다. 이는 개선이 생성보다 더 강력하며 추론 시간에 계산 규모를 조정하는 데 더 적합할 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Comparison of decoding strategies. Model performance improves with increased inference times.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | Natural | | Adversarial | | | | | | | Average | | |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| | Acc. | F1 | GPTInst | | GPTOut | | Manual | | Neighbor | | Average | | Acc. | F1 |
| | | | Acc. | F1 | Acc. | F1 | Acc. | F1 | Acc. | F1 | Acc. | F1 | | |
| GPT-4o-Mini | 74.5 | 70.5 | 69.2 | 61.6 | 60.9 | 51.4 | 59.8 | 51.9 | 72.8 | 66.4 | 65.7 | 57.8 | 67.4 | 60.4 |
| **_LLaMA3-8B Models_** | | | | | | | | | | | | | | |
| LLaMA3-8B-Instruct | 60.0 | 51.8 | 55.4 | 46.1 | 47.9 | 39.5 | 51.1 | 36.6 | 54.5 | 45.0 | 52.2 | 41.8 | 53.8 | 43.8 |
| SELF | 69.5 | 61.6 | 62.0 | 50.7 | 64.9 | 54.8 | 57.6 | 41.8 | 64.6 | 51.3 | 62.2 | 49.6 | 63.7 | 52.0 |
| Self-Rewarding | **71.0** | **66.3** | 70.1 | **66.7** | 63.8 | 59.5 | 62.0 | 55.7 | 67.5 | 61.7 | 65.9 | 60.9 | 66.9 | 61.9 |
| Meta-Rewarding | 70.5 | **66.3** | 68.5 | 64.6 | 64.9 | **60.2** | 64.1 | 58.3 | **69.0** | **63.1** | 66.6 | 61.6 | 67.4 | 62.5 |
| SPaR-8B-SFT | 68.5 | 60.9 | 67.9 | 62.4 | 59.6 | 50.0 | 63.0 | 54.1 | 68.3 | 59.3 | 64.7 | 56.5 | 65.5 | 57.3 |
| SPaR-8B-RFT-iter1 | 68.5 | 63.2 | 66.8 | 60.6 | 63.8 | 55.3 | 62.0 | 53.3 | 66.8 | 59.0 | 64.9 | 57.1 | 65.6 | 58.3 |
| SPaR-8B-RFT-iter2 | 70.5 | 64.2 | 66.8 | 61.6 | **66.0** | 60.0 | 65.2 | 57.9 | **69.0** | 62.4 | 66.8 | 60.5 | 67.5 | 61.2 |
| SPaR-8B-RFT-iter3 | 70.5 | 65.9 | **70.7** | **66.7** | 63.8 | 57.5 | **68.5** | **63.3** | 68.3 | 62.2 | **67.8** | **62.4** | **68.3** | **63.1** |
| **_GLM-4-9B Models_** | | | | | | | | | | | | | | |
| GLM-4-9B-Chat | **74.5** | **76.5** | 74.5 | **75.9** | 57.4 | **62.3** | 53.3 | 56.6 | 69.8 | **72.0** | 63.7 | **66.7** | 65.9 | **68.6** |
| SPaR-9B-SFT | 70.5 | 65.5 | 72.8 | 70.2 | **59.6** | 55.8 | 64.1 | 53.5 | 71.3 | 67.2 | 66.9 | 61.7 | 67.7 | 62.5 |
| SPaR-9B-RFT-iter3 | 71.0 | 68.8 | **75.5** | 74.6 | 58.5 | 55.2 | **68.5** | **64.2** | **68.7** | 65.9 | **67.8** | 64.9 | **68.4** | 65.7 |
| **_LLaMA3-70B Models_** | | | | | | | | | | | | | | |
| LLaMA3-70B-Instruct | 75.0 | 71.9 | 73.4 | 69.6 | **69.1** | **66.7** | 66.3 | **60.8** | 69.0 | 63.4 | 69.5 | 65.1 | 70.6 | 66.5 |
| SPaR-70B-RFT-iter3 | **78.0** | **74.7** | **78.8** | **76.9** | 64.9 | 61.2 | **67.4** | 59.5 | **72.4** | **68.1** | **70.9** | **66.4** | **72.3** | **68.1** |{{< /table-caption >}}
> 🔼 이 표는 LLMBar 벤치마크에서 반복적으로 학습된 LLM의 판단 능력 평가 결과를 보여줍니다. Mistral-7B-Instruct 결과는 표 8을 참조하세요. 각 기본 모델에 대해 가장 높은 점수는 굵게 표시되어 있습니다. 표에는 자연어와 적대적 질문에 대한 정확도와 F1 점수가 표시되며, 각 질문 유형에 대해 GPT 입력, GPT 출력, 수동, 이웃 등 다양한 평가 방식을 사용한 결과가 제공됩니다. 또한, 각 모델에 대해 자연어와 적대적 질문에 대한 평균 정확도와 F1 점수를 보여줍니다. 이 표를 통해 SPAR 학습 과정에서 Refiner의 판단 능력이 향상되는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2:  Evaluation of judgment capability for iteratively trained LLMs on LLMBar. (Cf. Table 8 for Mistral-7B-Instruct results.) Acc. denotes accuracy. The highest scores for each base model are highlighted in bold.
> </details>

{{< table-caption >}}
| Model | Acc-GPT | Acc-SPaR |
|---|---|---| 
| GPT-4o-Mini | 79.0 | 71.0 |
| SPaR-8B-SFT | 73.5 | 71.0 |
| SPaR-8B-RFT-iter1 | 77.5 | 77.0 |
| SPaR-8B-RFT-iter2 | 74.5 | 76.0 |
| SPaR-8B-RFT-iter3 | 79.0 | 90.5 |{{< /table-caption >}}
> 🔼 이 표는 다양한 평가 메트릭을 사용하여 SPAR 프레임워크의 개선 기능을 보여줍니다. 'Acc-GPT' 열은 GPT-40을 판사로 사용한 정확도를 나타내고 'Acc-SPAR' 열은 SPAR-8B-RFT-iter3를 판사로 사용한 정확도를 나타냅니다. 표에서 SPAR-8B-RFT-iter3가 자체 평가에서 GPT-40보다 높은 점수를 받았지만 GPT-40 평가에서는 그렇지 않다는 점에 유의해야 합니다. 이는 자체 평가 편향의 가능성을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Refinement evaluation results. Acc-GPT uses GPT-4o as judge; -SPaR uses SPaR-8B-RFT-iter3.
> </details>

{{< table-caption >}}
| Model | IFEval | | FollowBench (SSR) | 
|---|---|---|---|
| | Prompt(S) | Instruction(S) | Avg. |
| SPaR-8B-DPO-iter3 | 78.0 | 83.7 | 68.8 |
| *w/o* Tree Search | -2.0 | -0.8 | -1.7 |
| *w/o* Iterative Training | -0.9 | -0.2 | -2.0 |
| *w/o* Refinement | -2.6 | -1.6 | -3.1 |{{< /table-caption >}}
> 🔼 이 표는 SPaR-7B, SPaR-9B, SPaR-70B 모델의 명령어 수행 벤치마크 점수를 자세히 보여줍니다. IFEval 및 FollowBench(SSR) 벤치마크에서 프롬프트 레벨(P)과 명령어 레벨(I) 모두에 대한 점수, 느슨한 평가(L)와 엄격한 평가(S) 점수, 그리고 각 레벨(Lv1~Lv5)별 평균 점수가 제공됩니다.  논문에서 직접 가져온 점수는 †로 표시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Full results of SPaR-7B, SPaR-9B, and SPaR-70B on instruction-following benchmarks. P stands for prompt level, and I represents instruction level. L and S denote loose and strict evaluations, respectively. Avg. indicates average results and Lv means level. Scores marked with † are sourced directly from the original paper.
> </details>

{{< table-caption >}}
| Model | Natural | Adversarial |
|---|---|---|
| | Acc. | F1 | Acc. | F1 |
| SPaR-8B-RFT-iter3 | 70.5 | 65.9 | 67.8 | 62.4 |
| *w/o* Tree Search | -0.5 | -1.2 | -4.3 | -8.2 |
| *w/o* Iterative Training | -0.5 | -2.5 | -1.7 | -3.5 |{{< /table-caption >}}
> 🔼 이 표는 SPaR이 모델의 일반적인 능력을 유지하는지 여부를 평가하기 위해 일반 벤치마크에서의 성능을 보여줍니다. SPaR을 통해 교육된 모델은 GSM8k, TriviaQA, MMLU 및 HumanEval과 같은 벤치마크에서 성능이 저하되지 않고 오히려 향상되는 경우도 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Performance on general benchmarks. SPaR maintains the model’s general capabilities.
> </details>

{{< table-caption >}}
| Model | IFEval | | | | | FollowBench (SSR) | | | | | |
|---|---|---|---|---|---|---|---|---|---|---|---|
| | **P (L)** | **I (L)** | **P (S)** | **I (S)** | **Avg.** | **Lv-1** | **Lv-2** | **Lv-3** | **Lv-4** | **Lv-5** | **Avg.** |
|---|---|---|---|---|---|---|---|---|---|---|---| 
| *Mistral-7B Models* | | | | | | | | | | | |
| Mistral-7B-Instruct | 55.1 | 64.9 | 49.9 | 60.2 | 57.5 | 65.1 | 61.6 | 61.6 | 56.8 | 57.2 | 60.4 |
| SELF | 71.3 | 79.7 | 68.0 | 76.9 | 74.0 | 71.5 | 64.2 | 60.8 | 58.0 | 57.0 | 62.3 |
| Humpback | 60.4 | 71.0 | 56.6 | 67.6 | 63.9 | 70.7 | 63.9 | 63.8 | 59.8 | 57.9 | 63.2 |
| Self-Rewarding | 64.3 | 73.5 | 61.0 | 70.7 | 67.4 | 70.8 | 64.8 | 62.3 | 61.9 | **58.3** | 63.6 |
| Meta-Rewarding | 65.1 | 74.7 | 61.0 | 71.1 | 68.0 | 73.2 | 64.6 | 64.5 | 60.6 | 57.6 | 64.1 |
| SPaR-7B-SFT | 62.7 | 72.3 | 59.3 | 68.7 | 65.8 | 74.4 | 64.3 | 62.5 | 58.2 | 55.0 | 62.9 |
| SPaR-7B-DPO-iter1 | 68.2 | 76.6 | 64.7 | 73.6 | 70.8 | 73.2 | 64.6 | 63.1 | 60.3 | 56.6 | 63.6 |
| SPaR-7B-DPO-iter2 | 70.0 | 78.1 | 65.8 | 74.2 | 72.0 | 72.2 | **65.7** | 61.4 | **62.4** | 57.5 | 63.8 |
| SPaR-7B-DPO-iter3 | **74.1** | **80.9** | **69.7** | **77.1** | **75.5** | **74.6** | 63.8 | **66.1** | 61.0 | 58.0 | **64.7** |
| *GLM-4-9B Models* | | | | | | | | | | | |
| GLM-4-9B-Chat | 71.5 | 79.9 | 68.0 | 77.2 | 74.2 | 80.8 | 75.1 | 67.4 | 64.3 | **65.4** | 70.6 |
| SPaR-9B-SFT | 71.5 | 80.5 | 68.8 | 78.1 | 74.7 | 79.4 | 70.9 | **68.2** | 65.1 | 63.7 | 69.5 |
| SPaR-9B-DPO-iter1 | 73.8 | 81.2 | 70.6 | 78.5 | 76.0 | 82.6 | 76.0 | 67.9 | 64.9 | 63.6 | 71.0 |
| SPaR-9B-DPO-iter2 | 76.7 | 83.3 | 73.2 | 80.9 | 78.5 | 80.4 | 76.6 | 67.4 | **68.7** | 64.1 | 71.4 |
| SPaR-9B-DPO-iter3 | **77.3** | **84.1** | **73.6** | **81.4** | **79.1** | **82.7** | **76.7** | 67.9 | 68.3 | 64.2 | **72.0** |
| *LLaMA3-70B Models* | | | | | | | | | | | |
| LLaMA3-70B-Instruct | 83.7 | 88.9 | 77.1 | 83.8 | 83.4 | 77.1 | 72.5 | 69.4 | 68.7 | 66.3 | 70.8 |
| AutoIF-70B† | **85.6** | **90.4** | 80.2 | 86.7 | 85.7 | 71.0 | 67.2 | 66.2 | 64.6 | 63.5 | 66.5 |
| SPaR-70B-DPO-iter1 | 84.5 | 89.2 | 80.2 | 85.7 | 84.9 | 77.6 | 74.0 | 70.2 | 70.6 | 66.9 | 71.9 |
| SPaR-70B-DPO-iter2 | 85.0 | 89.4 | 81.5 | 87.2 | 85.8 | **80.4** | **76.4** | 69.9 | **73.7** | 70.2 | 74.1 |
| SPaR-70B-DPO-iter3 | **85.6** | 90.2 | **81.3** | **87.3** | **86.1** | 80.3 | 75.7 | **71.4** | **73.7** | **70.5** | **74.3** |{{< /table-caption >}}
> 🔼 이 표는 Mistral-7B-Instruct 모델을 기반으로 SPaR 프레임워크를 사용하여 반복적으로 훈련된 모델의 판단 능력을 LLMBar 벤치마크에서 평가한 결과를 보여줍니다. SPaR은 자체 개선을 위한 셀프 플레이 프레임워크로, 텍스트의 미묘한 차이를 강조하여 명령어를 더 효과적으로 따르도록 설계되었습니다. 표에는 자연어 및 적대적 샘플 모두에 대한 정확도와 F1 점수가 포함되어 있으며, 각 샘플 유형(GPTInst, GPTOut, Manual, Neighbor)에 대해 개별적으로 평가되었습니다. 또한, 전체 평균 점수를 제공하여 모델의 전반적인 판단 능력을 보여줍니다. SPaR을 통해 반복적으로 훈련된 모델은 벤치마크에서 다른 기준선보다 더 나은 성능을 보여줍니다. 이는 모델의 판단 능력 향상을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Judgment evalution results on LLMBar for SPaR-7B. Acc. stands for accuracy.
> </details>

{{< table-caption >}}
| Model | GSM8k | TriviaQA | MMLU | HumanEval | Average | 
|---|---|---|---|---|---| 
| **_Mistral-7B Models_** | | | | | | 
| Mistral-7B-Instruct | 42.9 | 72.5 | 57.9 | 32.9 | 51.6 | 
| SPaR-7B-SFT | 56.4 | 72.8 | 56.7 | 44.5 | 57.6 (+6.0) | 
| SPaR-7B-DPO-iter1 | 55.6 | 72.2 | 55.3 | 46.3 | 57.4 (+5.8) | 
| SPaR-7B-DPO-iter2 | 54.4 | 72.1 | 55.8 | 45.1 | 56.9 (+5.3) | 
| SPaR-7B-DPO-iter3 | 58.2 | 71.6 | 55.1 | 46.3 | 57.8 (+6.2) | 
| **_LLaMA3-8B Models_** | | | | | | 
| LLaMA3-8B-Instruct | 75.4 | 75.9 | 63.6 | 55.5 | 67.6 | 
| SPaR-8B-SFT | 75.6 | 76.0 | 64.0 | 61.6 | 69.3 (+1.7) | 
| SPaR-8B-DPO-iter1 | 78.8 | 75.2 | 63.8 | 60.4 | 69.6 (+2.0) | 
| SPaR-8B-DPO-iter2 | 77.0 | 74.9 | 63.1 | 60.4 | 68.9 (+1.3) | 
| SPaR-8B-DPO-iter3 | 77.7 | 75.1 | 63.1 | 60.9 | 69.2 (+1.6) | 
| **_GLM-4-9B Models_** | | | | | | 
| GLM-4-9B-Chat | 80.6 | 69.7 | 71.9 | 74.3 | 74.1 | 
| SPaR-9B-SFT | 82.9 | 69.4 | 71.8 | 73.8 | 74.5 (+0.4) | 
| SPaR-9B-DPO-iter1 | 82.6 | 68.8 | 71.6 | 75.0 | 74.5 (+0.4) | 
| SPaR-9B-DPO-iter2 | 82.8 | 68.9 | 71.8 | 73.8 | 74.3 (+0.2) | 
| SPaR-9B-DPO-iter3 | 83.0 | 69.0 | 72.1 | 73.2 | 74.3 (+0.2) | 
| **_LLaMA3-70B Models_** | | | | | | 
| LLaMA3-70B-Instruct | 92.2 | 87.2 | 80.8 | 79.3 | 84.9 | 
| SPaR-70B-DPO-iter1 | 92.5 | 90.4 | 81.0 | 79.3 | 85.8 (+0.9) | 
| SPaR-70B-DPO-iter2 | 92.9 | 89.5 | 80.4 | 78.7 | 85.4 (+0.5) | 
| SPaR-70B-DPO-iter3 | 93.4 | 86.7 | 80.6 | 79.9 | 85.2 (+0.3) |{{< /table-caption >}}
> 🔼 이 표는 LLMBar 데이터셋에서 다양한 디코딩 전략을 비교한 결과를 보여줍니다. 주요 내용은 탐욕적 디코딩과 다수결 투표를 사용한 여러 샘플링 횟수를 비교한 것입니다. 샘플링 횟수가 증가할수록 자연어 답변의 정확도와 F1 점수는 다소 향상되는 반면, 적대적 답변에서는 샘플링 횟수 5에서 가장 좋은 성능을 보입니다. 이는 샘플링 횟수 증가가 성능 향상에 중요할 수 있지만, 지나치게 늘리면 오히려 적대적 답변에 대한 성능이 저하될 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Comparison of decoding strategies on LLMBar.
> </details>

{{< table-caption >}}
| Model | Natural | | Adversarial | | | | | | Average | | |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---| 
| | Acc. | F1 | GPTInst | | GPTOut | | Manual | | Neighbor | | Average | | | |
| | | | Acc. | F1 | Acc. | F1 | Acc. | F1 | Acc. | F1 | Acc. | F1 | Acc. | F1 |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---| 
| Mistral-7B-Instruct | 58.0 | **69.1** | 57.1 | **68.8** | 50.0 | **64.1** | 45.6 | **61.5** | 47.8 | 62.6 | 50.1 | **64.3** | 51.7 | **65.2** |
| SELF | 68.0 | 65.2 | 71.2 | 68.7 | 56.4 | 56.8 | 62.0 | 52.6 | 67.5 | 62.3 | 64.3 | 60.1 | 65.0 | 61.1 | 
| Self-Rewarding | 68.0 | 64.0 | 69.0 | 63.7 | 59.6 | 53.7 | **63.0** | 57.5 | **69.4** | **64.3** | **65.3** | 59.8 | 65.8 | 60.6 |
| Meta-Rewarding | 67.5 | 62.4 | 71.7 | 68.7 | 56.4 | 51.8 | **63.0** | 56.4 | 66.8 | 62.1 | 64.5 | 59.7 | 65.1 | 60.3 |
| SPaR-7B-SFT | 69.5 | 63.9 | 71.7 | 67.5 | 55.3 | 48.8 | 55.4 | 45.3 | **69.4** | 62.3 | 63.0 | 56.1 | 64.3 | 57.6 |
| SPaR-7B-RFT-iter1 | 67.0 | 62.1 | 66.3 | 62.7 | 56.4 | 52.9 | 60.9 | 52.6 | 64.2 | 60.7 | 61.9 | 57.2 | 63.0 | 58.2 |
| SPaR-7B-RFT-iter2 | 68.0 | 64.4 | 68.5 | 64.6 | **60.6** | 57.5 | 62.0 | 52.1 | 64.2 | 60.0 | 63.8 | 58.5 | 64.7 | 59.7 |
| SPaR-7B-RFT-iter3 | **71.0** | 66.7 | **72.3** | 67.5 | 57.4 | 55.6 | 60.9 | 51.4 | 68.3 | 62.6 | 64.7 | 59.2 | **66.0** | 60.7 |{{< /table-caption >}}
> 🔼 이 표는 다양한 디코딩 전략을 비교하여 SPaR-8B 모델의 개선 성능을 보여줍니다. Acc-GPT는 GPT-40을 판사로 사용한 정확도이고, Acc-SPaR는 SPaR-8B-RFT-iter3를 판사로 사용한 정확도입니다. 표에서 BFS와 DFS와 같은 트리 탐색 알고리즘이 다른 방법들보다 성능이 뛰어나며, 특히 탐욕적 디코딩보다 높은 성능을 보이는 것을 확인할 수 있습니다. 이는 응답 개선 작업에서 트리 탐색의 중요성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Comparison of different decoding strategies for refinement task. Acc-GPT stands for the accuracy of using GPT-4o as judge, and Acc-SPaR for the accuracy of using SPaR-8B-RFT-iter3 as judge.
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
<img src="paper_images/19.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
{{< /gallery >}}