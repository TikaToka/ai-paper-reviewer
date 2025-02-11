---
title: "Step Back to Leap Forward: Self-Backtracking for Boosting Reasoning of Language Models"
summary: "대규모 언어 모델(LLM)의 추론 능력 향상을 위해 자체 백트래킹 메커니즘을 제안합니다. 이는 학습 및 추론 과정에서 모델이 스스로 백트래킹 시점을 결정하도록 함으로써, 비효율적인 과도한 사고와 보조 보상 모델에 대한 과도한 의존성을 해결합니다. 실험 결과, 제안된 방법은 기존 방식보다 40% 이상의 성능 향상을 보였습니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 National Key Laboratory for Novel Software Technology, Nanjing University, China",]
showSummary: true
date: 2025-02-06
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.04404 {{< /keyword >}}
{{< keyword icon="writer" >}} Xiao-Wen Yang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-10 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.04404" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.04404" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/step-back-to-leap-forward-self-backtracking" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 대규모 언어 모델(LLM)은 복잡한 추론 과제에서 **비효율적인 과도한 사고**와 **보조 보상 모델에 대한 과도한 의존**이라는 문제점을 가지고 있습니다. 이는 LLM이 검색 과정을 내재화하지 못하기 때문입니다. 효과적인 추론에는 검색 과정의 내재화가 필수적이며, 이를 위해서는 전통적인 검색 알고리즘에서의 핵심 연산인 **백트래킹**이 필요합니다. 

본 연구에서는 LLM에 **자체 백트래킹 메커니즘**을 도입하여 이러한 문제를 해결하고자 합니다. 이 메커니즘은 학습 및 추론 과정 모두에서 LLM이 스스로 백트래킹 시점을 결정할 수 있도록 합니다. 이를 통해 모델의 추론 능력과 효율성이 향상되며, 느린 사고 과정이 빠른 사고 과정으로 변환됩니다. 실험 결과는 제안된 방법이 기존 최적 경로 감독 미세 조정 방법에 비해 40% 이상의 성능 향상을 달성함을 보여줍니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} LLM의 추론 과정에서 비효율적인 과도한 사고와 보조 보상 모델에 대한 과도한 의존성 문제 제기 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 학습 및 추론 과정에서 모델의 자체 백트래킹 시점 결정을 가능하게 하는 자체 백트래킹 메커니즘 제안 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 제안된 방법이 기존 방식 대비 40% 이상의 성능 향상을 달성하며 효율성과 성능을 동시에 개선함을 실험적으로 증명 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대규모 언어 모델의 추론 능력 향상**에 중요한 의미를 지닙니다. 기존의 느린 사고 메커니즘에 의존하는 방법들의 비효율성을 지적하고, **자체 백트래킹 메커니즘**을 통해 이 문제를 해결하는 새로운 방법을 제시합니다. 이는 **모델의 효율성과 성능을 동시에 개선**하는 혁신적인 접근 방식으로, 추론 관련 연구에 새로운 방향을 제시하고 후속 연구를 위한 기반을 마련합니다. 특히, **복잡한 추론 과제에서의 성능 향상**은 AGI(Artificial General Intelligence) 개발에 대한 중요한 전진으로 여겨질 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.04404/x1.png)

> 🔼 그림 1은 OpenAI의 o1 모델과 같이 보상 모델에 과도하게 의존하고 비효율적인 과도한 생각에 취약한 기존의 느린 사고 메커니즘 기반 언어 모델과 제안하는 자기 백트래킹 접근 방식을 비교한 것입니다. 자기 백트래킹은 언어 모델이 학습 및 추론 중에 스스로 언제 어디서 백트래킹할지 결정할 수 있게 함으로써 이러한 문제점을 해결합니다.  즉, 비효율적인 탐색 과정을 개선하고 보상 모델에 대한 의존성을 줄여 더욱 효율적이고 강력한 추론 능력을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  Comparison between o1-like models and our self-backtracking approach. O1-like models are prone to inefficient overthinking and exhibit overreliance on reward model.
> </details>





{{< table-caption >}}
| Affiliation | 
|---|---| 
| <sup>1</sup> National Key Laboratory for Novel Software Technology, Nanjing University, China | 
| <sup>2</sup> School of Artificial Intelligence, Nanjing University, China | 
| <sup>3</sup> School of Intelligence Science and Technology, Nanjing University, China | 
| <span>{yangxw,zhuxy,weiwd,zhangdc,shaojj,zhouz,guolz,liyf}@lamda.nju.edu</span> | {{< /table-caption >}}

> 🔼 본 표는 제안된 Self-Backtracking 기법이 추론 성능을 향상시키는지를 보여줍니다. Countdown 문제를 사용하여 Llama 3.2-1B 및 Llama 3.2-3B 두 가지 기본 모델에 대한 정확도(%)를 여러 기준 모델과 비교하여 제시합니다. 각 기본 모델에 대한 최고 성능은 굵게 표시되어 있습니다.  Self-Backtracking을 적용한 모델은 기존의 최적 경로 지도 학습(SFT) 방식보다 정확도가 40% 이상 향상되었음을 보여줍니다.  이는 제안된 기법의 효과를 명확하게 보여주는 결과입니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Self-Backtracking Enhances Reasoning Performance. We report the accuracy (%) for the countdown task across two base models (Llama3.2-1B and Llama3.2-3B) with several baseline models. Best results for each base model are bolded.
> </details>





### In-depth insights


#### Self-Backtracking
자기 백트래킹(Self-Backtracking)은 언어 모델의 추론 능력 향상을 위한 혁신적인 기법으로, **모델이 스스로 비효율적인 추론 경로를 인지하고 이전 단계로 돌아가 대안적인 경로를 탐색**할 수 있도록 합니다. 이는 기존의 느린 사고(slow thinking) 방식을 빠른 사고(fast thinking)로 전환하여 효율성을 높이고, 보상 모델(reward model)에 대한 의존도를 낮추는 데 기여합니다. **훈련 단계에서는 언어 모델이 최적의 해결책과 비최적 경로를 구분하고, 후자에 대해서는 백트래킹 시점을 학습**하도록 설계되어 있습니다. **추론 단계에서는 학습된 백트래킹 능력을 활용하여 동적 탐색 과정**을 수행하며, 다양한 추론 경로를 탐색하고 최적의 결과를 도출합니다.  **자기 개선(self-improvement) 단계를 통해 모델은 스스로의 추론 능력을 지속적으로 향상**시킬 수 있습니다.  결과적으로 자기 백트래킹은 언어 모델의 추론 능력 향상과 효율성 증대에 크게 기여하는 핵심 기술로 평가될 수 있습니다.  특히 복잡한 문제 해결에 효과적이며, **AGI(인공 일반 지능) 2단계 수준의 추론 능력**을 달성하는데 중요한 역할을 할 것으로 기대됩니다.

#### LLM Reasoning
LLM 추론은 대규모 언어 모델(LLM)이 **복잡한 추론 작업을 수행하고, 문제를 해결하며, 질문에 답하는 능력**을 의미합니다.  이는 단순한 단어 예측을 넘어, **논리적 사고, 지식 활용, 문제 해결 전략** 등 고차원적인 인지 능력을 필요로 합니다.  기존의 LLM은 주로 패턴 인식과 통계적 확률에 기반하여 텍스트를 생성하지만,  진정한 추론 능력을 갖추려면 **세계에 대한 심층적인 이해와 추론 과정의 내면화**가 필수적입니다.  따라서 최근 연구는 LLM의 추론 능력 향상에 집중하며, **느린 사고(slow thinking) 메커니즘 통합**, **탐색 알고리즘 도입**, **강화 학습 활용** 등 다양한 접근 방식을 시도하고 있습니다.  **자기 반추(self-reflection) 능력**을 부여하여 오류를 수정하고, 더 나은 해결책을 찾아가는 연구도 활발합니다. 하지만 여전히 **과도한 추론(overthinking)**, **보조 보상 모델 과의존**, **탐색 과정의 내면화 부족** 등의 어려움이 존재합니다.  이러한 과제를 극복하기 위한 **새로운 기법과 알고리즘 개발**은 LLM의 추론 능력을 획기적으로 발전시키고, **인공지능의 발전**에 중요한 기여를 할 것으로 예상됩니다.  **특히, 자기 반추 및 탐색 기능의 효율적인 통합**은 LLM 추론 연구의 핵심 과제이며,  향후 연구 방향을 제시합니다.

#### Countdown Task
본 논문에서 언급된 "카운트다운 과제"는 **수리적 추론 능력**을 평가하기 위한 벤치마크 과제로, 주어진 숫자들을 사칙연산을 통해 목표 숫자를 만들어내는 것을 요구합니다. 이는 단순한 계산이 아닌, **전략적 사고와 계획 수립**, 그리고 **다양한 가능성 탐색**이 필요한 복잡한 문제입니다.  따라서 대규모 언어 모델(LLM)의 **추론 능력**을 평가하는 데 매우 적합하며, 제안된 **자기 백트래킹 기법**의 효과를 검증하는 데 중요한 역할을 합니다. 특히, 최적 경로만을 학습하는 기존 방법과 달리, 자기 백트래킹은 **오류를 통한 학습**을 가능하게 하여 더욱 **강인하고 효율적인 추론 능력**을 향상시킬 수 있다는 점을 보여줍니다. 카운트다운 과제는 이러한  **자기 백트래킹 기법**의 성능을 실험적으로 입증하는 핵심적인 부분입니다.

#### Future Work
본 논문은 언어 모델의 추론 능력 향상을 위한 자기 백트래킹(Self-Backtracking) 기법을 제시하지만, **여전히 개선의 여지가 많다.**  **다양한 추론 과제에 대한 적용 확장**이 필요하며, 특히 **대규모 언어 모델(LLM)로의 확장성 검증**이 중요한 후속 연구 과제다.  **다양한 유형의 문제 풀이에 대한 일반화 능력**을 높이고, **효율적인 백트래킹 전략 학습**을 위한 새로운 알고리즘 개발 및 **오류 유형 분석을 통한 성능 개선**도 필요하다.  **백트래킹 과정의 투명성을 높이고** 해석 가능성을 향상시키는 연구도 중요하며, **실제 응용 분야에 적용**하여 그 효과를 검증하는 실험도 수행되어야 할 것이다.  나아가, **다른 탐색 알고리즘과의 통합** 및 **자기 개선 메커니즘의 최적화**를 통해 더욱 강력하고 효율적인 추론 시스템을 구축하는 연구가 필요하다.  **에러 유형 분석을 통한 모델 개선 방향**을 제시하고,  **다양한 매개변수 및 하이퍼파라미터 최적화**를 통해 더욱 성능을 높이는 연구도 중요한 미래 연구 방향이다.

#### Limitations
본 논문의 한계는 **다양한 일반 추론 과제에 대한 적용 부족 및 대규모 언어 모델로의 확장성 부족**입니다.  더 넓은 범위의 과제에 대한 성능 검증이 필요하며, 현재 사용된 모델보다 더 큰 모델로 확장하여 실험할 필요가 있습니다. 또한, **오류 유형 분석에서 3B 모델의 성능 저하 원인을 명확히 규명하지 못했습니다.**  추가적인 데이터 분석과 모델 개선을 통해 이 문제를 해결해야 합니다. **되돌아가기(backtrack) 기능의 효율성 향상 및 과적합 방지**를 위한 추가적인 연구가 필요하며, **다양한 매개변수 조합에 따른 성능 변화**에 대한 더욱 심도 깊은 분석이 요구됩니다.  마지막으로, 본 연구에서 제시된 방법의 사회적 영향에 대한 논의가 부족하므로, 향후 연구에서 이 부분을 보완해야 합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.04404/x2.png)

> 🔼 그림 2는 제안된 Self-Backtracking 방법의 전체 프레임워크를 보여줍니다. 훈련 단계에서는 언어 모델이 언제 어디서 백트래킹(backtracking)을 수행해야 하는지 학습합니다. 추론 단계에서는 깊이 우선 탐색과 너비 우선 탐색을 모두 고려하는 백트래킹 알고리즘을 사용합니다. 마지막으로 자기 개선 단계에서는 전문가 반복(expert iteration)을 통해 모델의 빠른 사고 능력을 향상시킵니다.  즉, 훈련 단계에서 백트래킹 시점을 학습하고, 추론 단계에서 효율적인 백트래킹 알고리즘을 적용하며, 자기 개선 단계에서 전문가의 피드백을 통해 성능을 개선하는 과정을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2:  The overall framework of Self-Backtracking. During the training phase, the language model is instructed on when and where to backtrack. The inference phase employs a backtracking algorithm that considers both depth and breadth. The self-improvement phase utilizes expert iteration to enhance the fast thinking capabilities of the model.
> </details>



![](https://arxiv.org/html/2502.04404/extracted/6182702/fig/improvement_comparison.png)

> 🔼 그림 3은 본 논문에서 제안하는 Self-Backtracking 기법을 Llama 3.2-1B 모델에 적용했을 때 정확도 향상 과정을 보여줍니다. 세 가지 단계(Slow Thinking, Self-Improvement, Fast Thinking)를 거치면서 모델의 추론 능력이 향상되는 것을 보여줍니다.  Slow Thinking 단계에서는 Self-Backtracking 알고리즘을 사용하여 추론 과정을 거치고, 그 결과를 바탕으로 Self-Improvement 단계에서 전문가 검토를 통해 학습 데이터를 개선합니다.  마지막 Fast Thinking 단계에서는 개선된 데이터를 이용하여 모델을 재학습시켜 추론 효율성을 높입니다.  이 그림은 Self-Backtracking 기법이 반복적인 학습과 개선을 통해 모델의 추론 성능을 향상시키는 과정을 시각적으로 보여주는 중요한 결과입니다.  그래프는 반복 횟수에 따른 정확도 변화를 나타내며, Self-Backtracking 기법 적용 시 정확도가 크게 향상됨을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Self-improvement in accuracy of Llama3.2-1B.
> </details>



![](https://arxiv.org/html/2502.04404/extracted/6182702/fig/kncurve.png)

> 🔼 그림 4는 다양한 N 값에 따른 성능 곡선을 보여줍니다. 여기서 N은 언어 모델이 각 상태에서 후보로 고려하는 예측의 수를 나타냅니다. 이 그래프는 모델이 N을 증가시킴에 따라 어떻게 성능이 향상되는지, 그리고 특정 시점을 지나면 더 이상 개선되지 않는지를 보여줍니다.  이를 통해 자체 백트래킹 방법이 어떻게 모델의 추론 능력을 향상시키는지, 특히 N값의 조정을 통해 탐색 공간을 효율적으로 관리하는지를 보여줍니다.  두 개의 다른 모델(Llama3.2-1B와 Llama3.2-3B)과 두 개의 데이터셋(훈련 데이터셋에서 본 적 있는 목표값과 훈련 데이터셋에서 본 적 없는 목표값)에 대한 결과가 제시됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: The performance curves when varing N𝑁Nitalic_N.
> </details>



![](https://arxiv.org/html/2502.04404/extracted/6182702/fig/pie_charts_small.png)

> 🔼 그림 5는 Llama 3.2-1B 모델을 사용하여 '본다운' 작업의 관측된 타겟에 대해 서로 다른 b(backtrack 횟수)와 N(후보 갯수) 값에서 제안된 방법의 오류 유형을 보여줍니다. 각 파이 차트는 특정 b와 N 값에 대한 오류 분포를 보여주며, '타겟에 도달하지 못함', '잘못된 단계 형식', '단계 내 잘못된 결과', '단계 내 알 수 없는 숫자'의 네 가지 오류 유형을 보여줍니다. 이 그림은 모델의 성능에 미치는 b와 N의 영향과 다양한 오류 유형의 상대적 비중을 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Error types of our method for different b𝑏bitalic_b and N𝑁Nitalic_N on Seen Targets of Llama3.2-1B.
> </details>



![](https://arxiv.org/html/2502.04404/extracted/6182702/fig/loss_subplots.png)

> 🔼 그림 6은 논문에서 제안된 자기 백트래킹 방법의 학습 과정을 보여주는 손실 곡선 그래프입니다. Llama 3.2-1B 및 Llama 3.2-3B 두 가지 모델에 대한 학습 곡선이 표시되어 있으며, 각 모델의 학습 진행에 따른 손실 값의 변화를 시각적으로 보여줍니다. 이를 통해 자기 백트래킹 방법의 학습 안정성 및 효율성을 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Loss Curve of self-backtracking for Llama3.2-1B and Llama3.2-3B.
> </details>



![](https://arxiv.org/html/2502.04404/x3.png)

> 🔼 이 그림은 제안된 자기 백트래킹 방법의 사례 연구를 보여줍니다. 두 가지 질문에 대한 참조 솔루션과 새 솔루션을 비교하여 모델이 최적 경로를 찾기 위해 어떻게 백트래킹을 사용하는지 보여줍니다.  각 질문에 대해 모델은 먼저 초기 경로를 따르지만, 잘못된 결정을 인식하고 이전 상태로 돌아가 다른 경로를 탐색하여 최종적으로 목표에 도달하는 과정을 거칩니다. 이는 자기 백트래킹 메커니즘이 더 복잡한 추론 문제를 해결하는 데 어떻게 도움이 되는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Case Study of our self-backtracking.
> </details>



![](https://arxiv.org/html/2502.04404/extracted/6182702/fig/improvement_comparison2.png)

> 🔼 그림 8은 Llama3.2-3B 모델의 정확도 향상 과정을 보여줍니다.  자기 개선 과정을 거치면서,  처음에는 느린 사고(slow thinking) 방식으로 학습된 모델이 빠른 사고(fast thinking) 방식으로 전환되는 것을 보여줍니다.  그래프는 반복 횟수에 따른 정확도 변화를 나타내며,  backtrack을 사용한 경우(b=1)와 사용하지 않은 경우(b=0)를 비교하여 자기 개선을 통한 성능 향상을 명확히 보여줍니다.  seen target과 new target에 대한 결과를 모두 포함하고 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Self-improvement in accuracy of Llama3.2-3B.
> </details>



![](https://arxiv.org/html/2502.04404/extracted/6182702/fig/pie_charts.png)

> 🔼 그림 9는 Llama3.2-1B 모델을 사용하여 '본 적 있는' 타겟(Seen Targets)에 대해 자가 백트래킹(Self-Backtracking) 알고리즘의 오류 유형 분포를 보여줍니다.  각 파이 차트는 백트래킹 깊이(b)와 후보군 크기(N)의 조합에 따른 오류 유형을 나타냅니다.  오류 유형은 다음 네 가지로 분류됩니다: 목표 달성 실패(Not reached target), 잘못된 단계 형식(Invalid step format), 단계 내 잘못된 결과(Incorrect result in step), 단계 내 알 수 없는 숫자(Unknown numbers in step). 이 그림을 통해 각 매개변수 조합에 따른 다양한 오류 유형의 비율을 확인하여 자가 백트래킹 알고리즘의 성능과 개선 방향을 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Error types of Llama3.2-1B on seen targets.
> </details>



![](https://arxiv.org/html/2502.04404/extracted/6182702/fig/pie_charts2.png)

> 🔼 그림 10은 새로운 타겟(New Targets)에 대해 Llama 3.2-1B 모델의 오류 유형을 보여줍니다.  각 파이 차트는 다른 하이퍼파라미터 설정(b, N)에서의 오류 비율을 나타냅니다.  '도달하지 못한 타겟(Not reached target)', '잘못된 단계 형식(Invalid step format)', '단계 내 잘못된 결과(Incorrect result in step)', '단계 내 알 수 없는 숫자(Unknown numbers in step)'의 네 가지 오류 유형이 분석됩니다.  각 파이 차트는 특정 하이퍼파라미터 조합에서 각 오류 유형이 차지하는 비율을 시각적으로 보여주어, 모델의 성능과 오류 패턴을 이해하는 데 도움을 줍니다.  새로운 타겟에 대한 모델의 성능과 오류 유형 분포를 자세히 분석하여, 모델 개선 방향을 제시하는데 활용될 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Error types of Llama3.2-1B on new targets.
> </details>



![](https://arxiv.org/html/2502.04404/extracted/6182702/fig/pie_charts3.png)

> 🔼 그림 11은 Llama3.2-3B 모델이 '본 적 있는(seen)' 타겟에 대해 추론하는 동안 발생하는 오류 유형을 보여줍니다.  각 파이 차트는 특정 하이퍼파라미터 설정(b 값과 N 값)에서의 오류 분포를 나타냅니다.  '도달하지 못한 목표(Not reached target)', '잘못된 단계 형식(Invalid step format)', '단계 내 잘못된 결과(Incorrect result in step)', '단계 내 알 수 없는 숫자(Unknown numbers in step)'의 네 가지 오류 유형이 포함되어 있습니다.  각 파이 차트의 비율은 각 오류 유형이 차지하는 비율을 보여줍니다. 이를 통해, 다른 하이퍼파라미터 설정에 따른 오류 패턴의 변화를 분석하고 모델의 성능을 개선하기 위한 방향을 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Error types of Llama3.2-3B on seen targets.
> </details>



![](https://arxiv.org/html/2502.04404/extracted/6182702/fig/pie_charts4.png)

> 🔼 그림 12는 새로운 타겟(New Targets)에 대해 Llama 3.2-3B 모델의 오류 유형을 보여줍니다.  다양한 탐색 깊이(b)와 너비(N) 매개변수 설정 하에서, 모델이 예측한 답변이 타겟에 도달하지 못하거나, 잘못된 단계 형식(Invalid step format), 단계 내 잘못된 결과(Incorrect result in step), 또는 단계에서 알 수 없는 숫자(Unknown numbers in step) 등의 오류 유형이 비율로 표시됩니다. 이 그림을 통해 각 매개변수 설정에 따른 다양한 오류 유형의 발생 비율을 비교 분석하여 모델의 성능과 안정성을 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Error types of Llama3.2-3B on new targets.
> </details>



![](https://arxiv.org/html/2502.04404/extracted/6182702/fig/temperature.png)

> 🔼 이 그림은 온도 변화가 정확도에 미치는 영향을 보여줍니다.  다양한 온도 설정에서 자체 백트래킹 방법의 안정성을 보여주는 실험 결과를 나타냅니다.  온도가 너무 낮으면 b=1 조건에서 약간의 부정적인 영향을 미치지만, 일반적으로 온도 변화에 강인함을 보여줍니다.  0.7이라는 기존 온도 값이 적절한 선택임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: The influence of different temperatures on accuracy.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Methods | Llama3.2-1B |  | Llama3.2-3B |  | 
|---|---|---|---|---|---| 
|  | Seen Targets | New Targets | Seen Targets | New Targets |  | 
|---|---|---|---|---|---| 
| ▷ Only Optimal Solution: |  |  |  |  |  | 
| SFT + Greedy | 28.60 | 28.92 | 33.98 | 32.68 |  | 
| SFT + Beam Search | 31.68 | 31.90 | 35.82 | 34.36 |  | 
| ▷ RLHF |  |  |  |  |  | 
| DPO (Rafailov et al., 2023) | 29.06 | 27.64 | 34.46 | 32.72 |  | 
| KTO (Ethayarajh et al., 2024) | 28.34 | 27.74 | 33.70 | 32.34 |  | 
| ▷ Backtracking Data: |  |  |  |  |  | 
| Greedy | 28.92 | 27.06 | 27.56 | 26.96 |  | 
| Beam Search | 36.10 | 34.30 | 23.10 | 22.20 |  | 
| Best-of-N (N=8) | 41.26 | 40.68 | 47.84 | 48.56 |  | 
| Best-of-N (N=16) | 32.40 | 33.94 | 47.28 | 47.80 |  | 
| Best-of-N (N=32) | 25.60 | 27.04 | 44.38 | 45.88 |  | 
| Self-Backtracking (b=0,N=8) | 66.66 | 67.40 | 58.76 | 56.92 |  | 
| Self-Backtracking (b=0,N=32) | 70.66 | 72.14 | 60.18 | 58.06 |  | 
| Self-Backtracking (b=1,N=8) | 67.60 | 68.02 | 61.06 | 59.28 |  | 
| Self-Backtracking (b=1,N=32) | **73.54** | **73.78** | **64.12** | **61.98** |  | {{< /table-caption >}}
> 🔼 표 2는 다양한 탐색 기반 방법들을 비교 분석한 결과를 보여줍니다.  본 논문의 Self-Backtracking 방법과 기존의 다른 탐색 기법들 (DFS, Best-of-N, SoS, GSOS)의 성능을 '본 적 있는 타겟' 과 '본 적 없는 타겟' 데이터셋에서 Llama 3.2-1B 및 Llama 3.2-3B 모델을 사용하여 비교 분석합니다. 각 방법의 정확도를 측정하여 Self-Backtracking의 우수성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Comparison between search-augmented methods.
> </details>

{{< table-caption >}}
| Methods | Seen Targets | New Targets |
|---|---|---|
| DFS ($b=32$) | 49.12 | 48.90 |
| DFS ($b=64$) | 60.00 | 61.06 |
| SoS (Gandhi et al., 2024) | 57.50 | 53.40 |
| GSoS (Moon et al., 2024) | 69.00 | 67.20 |
| Self-Backtracking (best) | **73.54** | **73.78** |{{< /table-caption >}}
> 🔼 표 3은 Llama3.2-1B 모델을 사용하여 '본문에서 확인된 타겟'(Seen Targets)에 대해, 최적 경로 데이터셋 (𝒟𝑜𝑝)과 백트래킹 데이터셋 (𝒟𝑏𝑎𝑐𝑘)의 비율을 다르게 하여 자체 백트래킹(self-backtraking)의 성능을 평가한 결과를 보여줍니다.  다양한 𝒟𝑜𝑝과 𝒟𝑏𝑎𝑐𝑘의 비율(1:0.5, 1:1, 1:2, 1:3, 1:4)에 따른 정확도 변화를 확인하여, 백트래킹 데이터의 양이 모델 성능에 미치는 영향을 분석합니다.  N(후보군 크기)과 b(백트래킹 깊이)의 값이 다를 때의 결과가 함께 제시되어,  모델 성능에 미치는 요인을 다각적으로 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Performance evaluation of self-backtraking under varying ratios of 𝒟o⁢psubscript𝒟𝑜𝑝\mathcal{D}_{op}caligraphic_D start_POSTSUBSCRIPT italic_o italic_p end_POSTSUBSCRIPT to 𝒟b⁢a⁢c⁢ksubscript𝒟𝑏𝑎𝑐𝑘\mathcal{D}_{back}caligraphic_D start_POSTSUBSCRIPT italic_b italic_a italic_c italic_k end_POSTSUBSCRIPT for Llama3.2-1B on Seen Targets.
> </details>

{{< table-caption >}}
| Parameter | 1 : 0.5 | 1 : 1 | 1 : 2 | 1 : 3 | 1 : 4 |
|---|---|---|---|---|---| 
| $b=0,N=8$ | **66.70** | 66.66 | 64.92 | 64.78 | 65.06 |
| $b=1,N=8$ | **68.00** | 67.60 | 64.66 | 65.18 | 65.94 |
| $b=0,N=16$ | 69.80 | **70.20** | 67.80 | 68.18 | 69.16 |
| $b=1,N=16$ | 71.12 | **72.50** | 65.66 | 66.56 | 70.12 |{{< /table-caption >}}
> 🔼 표 4는 Llama3.2-1B 모델을 사용하여 새 테스트 대상에 대해 최적 경로 데이터셋 (𝒟o⁢psubscript𝒟𝑜𝑝 mathcal{D}_{op} )과 백트래킹 데이터셋 (𝒟b⁢a⁢c⁢ksubscript𝒟𝑏𝑎𝑐𝑘 mathcal{D}_{back} )의 비율을 다르게 하여 자기 백트래킹 방법의 성능을 평가한 결과를 보여줍니다.  다양한 비율 (1:0.5, 1:1, 1:2, 1:3, 1:4) 에서 자기 백트래킹 기법의 정확도를 측정하여  최적 경로 데이터와 백트래킹 데이터의 비율이 모델 성능에 미치는 영향을 분석합니다.  표에는  N (후보군 크기)과 b (백트래킹 깊이)의 각기 다른 값에 대한 결과가 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Performance evaluation of self-backtraking under varying ratios of 𝒟o⁢psubscript𝒟𝑜𝑝\mathcal{D}_{op}caligraphic_D start_POSTSUBSCRIPT italic_o italic_p end_POSTSUBSCRIPT to 𝒟b⁢a⁢c⁢ksubscript𝒟𝑏𝑎𝑐𝑘\mathcal{D}_{back}caligraphic_D start_POSTSUBSCRIPT italic_b italic_a italic_c italic_k end_POSTSUBSCRIPT for Llama3.2-1B on New Targets.
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