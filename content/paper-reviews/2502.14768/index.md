---
title: "Logic-RL: Unleashing LLM Reasoning with Rule-Based Reinforcement Learning"
summary: "규칙 기반 강화 학습으로 대규모 언어 모델의 추론 능력을 향상시킨 Logic-RL을 소개합니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Microsoft Research",]
showSummary: true
date: 2025-02-20
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.14768 {{< /keyword >}}
{{< keyword icon="writer" >}} Tian Xie et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-21 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.14768" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.14768" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/logic-rl-unleashing-llm-reasoning-with-rule" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)의 추론 능력 향상은 인공지능 연구의 주요 과제입니다. 기존 방법들은 복잡하거나 재현성이 떨어지는 한계를 가지고 있습니다. 본 논문에서는 **규칙 기반 강화 학습(Logic-RL)**을 사용하여 LLM의 추론 능력을 향상시키는 새로운 방법을 제시합니다. 특히, **제어 가능한 복잡성을 가진 합성 논리 퍼즐을 훈련 데이터**로 사용하여 안정적이고 효율적인 학습을 가능하게 하였습니다. 



Logic-RL은 **생각 과정을 강조하는 시스템 프롬프트, 지름길을 방지하는 엄격한 형식 보상 함수, 그리고 안정적인 수렴을 달성하는 간단한 훈련 절차**를 도입했습니다. 그 결과, 7B 모델은 기존 논리 데이터셋에서는 관찰되지 않았던 **반성, 검증, 요약과 같은 고급 추론 능력**을 개발했습니다.  더욱 놀라운 것은, 단 5,000개의 논리 문제로 학습시킨 후에도 **AIME 및 AMC와 같은 어려운 수학 문제 벤치마크에서 일반화 능력**을 보였다는 점입니다. 이는 Logic-RL이 단순 패턴 매칭이 아닌 추상적 문제 해결 체계를 학습함을 시사합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 규칙 기반 강화 학습을 통해 대규모 언어 모델의 추론 능력 향상 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 합성 논리 퍼즐 데이터셋을 이용한 안정적인 학습 및 일반화 성능 확인 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 수학 문제 벤치마크(AIME, AMC)에서 우수한 성능으로 실용성 입증 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **규칙 기반 강화 학습을 사용하여 대규모 언어 모델의 추론 능력을 향상시키는 새로운 방법**을 제시합니다.  이는 현재 연구 동향과 밀접하게 연관되어 있으며, 추론 능력 향상에 대한 새로운 가능성을 제시합니다. 또한, **다양한 분야의 연구자들에게 영향**을 미칠 수 있는 잠재력을 가지고 있습니다. 특히, **합성 논리 퍼즐 데이터셋을 사용하여 안정적인 훈련을 달성한 점**과 **수학 문제 벤치마크에서의 일반화 성능**은 주목할 만합니다.  이는 향후 연구를 위한 새로운 방향을 제시할 뿐 아니라, **실제 응용 분야에서도 유용성**을 가질 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.14768/x1.png)

> 🔼 그림 1은 강화 학습(RL) 훈련 중 모델의 검증 정확도와 평균 응답 길이를 보여줍니다.  모델이 성능 향상을 위해 더 많은 '생각' 연산을 자동으로 할당하는 학습 과정을 보여줍니다.  흥미롭게도, 모델은 완전히 새로운 데이터셋(AIME, AMC)에서도 놀라운 일반화 능력을 보여줍니다.  즉, 훈련 데이터로 사용되지 않은 문제 유형에도 잘 적용됨을 의미합니다.  응답 길이가 길어짐에 따라 검증 정확도가 향상되는 경향을 보이는데, 이는 모델이 더 복잡한 추론 과정을 거칠수록 정답률이 높아짐을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Validation accuracy and mean response length during RL training, illustrating how the model autonomously learns to allocate more thinking compute for improved performance. Remarkably, the model also demonstrates impressive generalization on completely unseen datasets (AIME, AMC).
> </details>





{{< table-caption >}}
| Algorithm | Train Batch Size | Rollout N | KL Coef | Max Response Len |
|---|---|---|---|---|
| REINFORCE++ | 8 | 8 | 0.001 | 4096 |{{< /table-caption >}}

> 🔼 표 1은 논문의 2.4절(훈련 일정)에서 Logic-RL 모델 훈련에 사용된 주요 하이퍼파라미터들을 보여줍니다.  각 하이퍼파라미터는 훈련 과정의 안정성 및 효율성에 영향을 미치는 중요한 요소입니다. REINFORCE++ 알고리즘을 사용한 훈련에 대한 세부 정보를 제공합니다.  여기에는 배치 크기(Batch Size), 롤아웃 수(Rollout N), KL 계수(KL Coef), 최대 응답 길이(Max Response Len) 등이 포함됩니다.  이 표는 논문에서 제시된 훈련 설정을 이해하는 데 필수적입니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Important Training Parameters
> </details>





### In-depth insights


#### Logic-RL: Rule-Based RL
논문에서 제시된 Logic-RL: Rule-Based RL 접근 방식은 **규칙 기반 강화 학습**을 사용하여 대규모 언어 모델의 추론 능력을 향상시키는 데 초점을 맞추고 있습니다.  합성 논리 퍼즐 데이터셋을 사용하여 **제어 가능한 복잡성**과 **명확한 정답 검증**이 가능하다는 점이 특징입니다.  **효율적인 학습을 위해**, 생각 과정을 강조하는 시스템 프롬프트, 지름길을 방지하는 엄격한 형식 보상 함수, 그리고 안정적인 수렴을 달성하는 간단한 학습 방법을 제시합니다. Logic-RL은 단순한 패턴 매칭이 아닌 **추상적인 문제 해결 체계**를 개발하여 AIME 및 AMC와 같은 어려운 수학 벤치마크에서 일반화 능력을 보여줍니다. **긴 응답이 항상 더 나은 추론을 보장하는 것은 아니며**, 오히려 효율적인 추론은 가장 짧은 경로에서 나온다는 점을 발견했습니다. 또한, **언어 혼합은 추론을 방해**하고, '생각' 토큰의 증가는 성능 향상과 상관관계가 있다는 점도 흥미로운 발견입니다.  **SFT와 달리 RL은 일반화 능력**이 뛰어나며, 커리큘럼 학습은 여전히 RL에서 중요한 역할을 합니다.

#### Reward Design Refinement
보상 설계 개선은 논문에서 강조하는 핵심 요소입니다. **초기 보상 설계는 모델이 지름길을 찾거나, 형식을 조작하는 등의 문제를 야기했습니다.** 따라서 연구자들은 **엄격한 형식 보상 및 간결한 시스템 프롬프트**를 도입하여 이러한 문제를 해결했습니다. 엄격한 형식 보상은 모델이 올바른 형식과 구조를 준수하도록 유도하고, 지름길을 통한 보상 획득을 방지합니다. 간결한 시스템 프롬프트는 모델의 사고 과정을 명확히 제시하고, 단순한 답변보다는 추론 과정에 중점을 두도록 유도합니다. **보상 설계의 반복적인 개선을 통해 모델의 성능을 향상시키고, 훈련의 안정성을 확보할 수 있었습니다.** 또한, 보상 설계 과정에서 모델의 행동을 지속적으로 모니터링하여 발생 가능한 문제점들을 사전에 예방하고, 개선에 반영하는 과정이 중요함을 강조합니다.  **이러한 보상 설계 개선은 궁극적으로 모델의 일반화 능력을 향상시켜, 훈련 데이터에 없는 새로운 문제에도 효과적으로 대처할 수 있도록 만들었습니다.**

#### Emergent Reasoning Skills
본 논문에서 다룬 'Emergent Reasoning Skills'는 **규칙 기반 강화 학습(rule-based reinforcement learning)**을 통해 대규모 언어 모델(LLM)에서 나타나는 예상치 못한 추론 능력의 출현을 의미합니다.  단순히 훈련 데이터를 암기하는 것을 넘어, 모델이 **추상적인 문제 해결 전략(abstract problem-solving schemata)**을 스스로 개발하고, **반성(reflection), 검증(verification), 요약(summarization)**과 같은 고차원적 사고 과정을 수행하는 능력이 자발적으로 생겨나는 현상입니다. 이는 특히 **제한된 훈련 데이터(5,000개의 논리 퍼즐)**만으로도 어려운 수학 문제(AIME, AMC)에 일반화하는 능력을 보여주는 점에서 매우 중요한 의미를 지닙니다.  **단순히 답을 맞추는 것을 넘어서, 추론 과정을 상세히 보여주고(chain-of-thought), 스스로 오류를 수정하고(back-tracking) 여러가지 가능성을 탐색하는(multi-path exploration)** 모습은 인간의 추론 과정과 유사하며, LLM의 잠재력을 보여주는 강력한 증거입니다.  하지만, 응답 길이가 길다고 해서 추론 능력이 항상 향상되는 것은 아니며, **효율적인 추론(efficient reasoning)**이 더 중요하다는 점을 시사합니다.  **추론 과정에 특정 단어(예: verify, re-evaluate)**의 사용이 성능 향상과 연관되어 있음을 발견하였지만, 모든 복잡한 사고 단어가 성능 향상에 기여하는 것은 아님을 확인했습니다.  앞으로 이러한 **새로운 추론 능력의 일반화 가능성(generalization ability)**을 더 큰 규모의 실제 문제에 적용하는 추가 연구가 필요합니다.

#### Generalization to OOD
본 논문에서 다룬 Logic-RL 모델의 핵심 강점 중 하나는 **분포 외(Out-of-Distribution, OOD) 일반화 능력**입니다.  합성 데이터로 훈련된 모델이 실제 수학 문제 벤치마크인 AIME과 AMC에서 예상치 못한 높은 성능을 보인 것은 주목할 만합니다. 이는 단순히 암기가 아닌, **추론 능력 자체의 향상**을 의미합니다.  **합성 데이터의 제어 가능성** 덕분에, 복잡도를 조절하며 훈련 데이터의 범위를 넓힐 수 있었고, 이를 통해 모델은 훈련 데이터의 패턴을 넘어서는 추론 능력을 발휘할 수 있었습니다.  **단순 패턴 매칭이 아닌 추상적인 문제 해결 능력**을 획득했음을 시사합니다.  하지만, 합성 데이터 기반의 OOD 일반화 능력이 실제 복잡한 문제에 얼마나 잘 적용될지는 추가적인 연구가 필요합니다.  **실제 세계 문제에 대한 적용성**을 검증하고, 그 한계를 파악하는 후속 연구가 중요합니다.  Logic-RL 모델의 성공은 규칙 기반 강화 학습의 잠재력을 보여주는 중요한 사례이며,  앞으로 더욱 발전된  **강화 학습 기반의 추론 모델 개발**에 대한 기대감을 높입니다.

#### SFT vs. RL Generalization
본 논문은 SFT(Supervised Fine-Tuning)와 RL(Reinforcement Learning)의 일반화 능력을 비교 분석합니다. **SFT는 기존 데이터에 과적합되는 경향이 강하지만, RL은 새로운 데이터에도 잘 적응하는 일반화 성능을 보입니다.**  이는 RL이 단순히 패턴을 암기하는 것이 아니라, 추론 능력 자체를 향상시키기 때문입니다.  **SFT는 주어진 데이터의 구조에 의존하여 학습하지만, RL은 보상 함수를 통해 목표 지향적인 학습을 수행하므로, 데이터 분포의 변화에 강건합니다.** 따라서, 새로운 유형의 문제나 복잡한 추론이 필요한 상황에서는 RL 기반 모델이 SFT 기반 모델보다 훨씬 우수한 성능을 발휘할 것으로 예상됩니다.  **특히, 제한된 데이터로 학습된 모델의 경우 RL의 일반화 능력은 매우 중요한 장점**이 됩니다.  하지만, RL은 학습 과정이 복잡하고 시간이 오래 걸릴 수 있다는 단점이 존재합니다.  따라서, 실제 응용에서는 SFT와 RL의 장점을 결합하는 하이브리드 접근 방식이 효과적일 수 있습니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.14768/extracted/6220745/figure/rq1.png)

> 🔼 그림 2는 세 가지 강화 학습 알고리즘인 GRPO, REINFORCE++, PPO의 성능을 비교 분석한 그래프입니다. 50개의 데이터를 묶어 평균을 낸 이동 평균을 사용하여 학습 속도, 정확도, 보상 증가 측면에서 알고리즘 간의 차이를 보여줍니다. GRPO는 파란색, REINFORCE++는 빨간색, PPO는 초록색으로 표시됩니다. 각 그래프는 학습 단계에 따른 시간, 정확도, 보상의 변화를 나타내어 알고리즘의 효율성과 성능을 비교하는 데 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Comparison of GRPO (Blue), REINFORCE++ (Red), and PPO (Green) performance (averaged by sliding window = 50) in terms of training speed, accuracy, and reward gain.
> </details>



![](https://arxiv.org/html/2502.14768/extracted/6220745/figure/rq7.png)

> 🔼 그림 3은 복잡한 추론 행위와 언어 혼용이 추론 성능에 미치는 영향을 보여줍니다.  이 그림은 특정 단어를 포함한 응답에 대한 모델의 평균 점수를 분석한 결과입니다.  'verify'와 're-evaluate'와 같은 단어를 포함한 응답은 해당 단어가 없는 응답보다 점수가 훨씬 높았습니다. 반대로 다른 언어의 단어를 포함한 응답은 점수가 낮았습니다. 이는 모델이 'verify'나 're-evaluate'와 같은 단어를 사용하며 더욱 심도있는 추론 과정을 거치고 있음을 시사합니다. 반면, 다른 언어의 단어 혼용은 오히려 추론 성능을 저해하는 요소로 작용합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Impact of complex reasoning behaviours and language mixing on reasoning performance. We analyzed the model’s answer rewards for responses containing the tokens shown in the figure. Responses with 'verify' and 're-evaluate' scored significantly higher than those without these words. Conversely, responses containing certain tokens from other languages generally received lower scores.
> </details>



![](https://arxiv.org/html/2502.14768/extracted/6220745/figure/word_frequency_charts/verify.png)

> 🔼 그림 4는 강화 학습 과정에서 특정 단어의 빈도 변화를 추적한 그래프입니다.  (a)는 'verify' 단어의 빈도 변화를 보여줍니다. 이는 모델이 추론 과정에서 검증 행위를 수행하는 빈도를 나타내며, 학습 초기에 낮은 빈도를 보이다가 점차 증가하는 경향을 보입니다. 이는 모델이 자율적으로 추론 과정을 더욱 철저하게 검증하는 능력을 학습함을 시사합니다.  즉, 단순히 답을 맞히는 것뿐만 아니라, 그 답에 도달하는 과정에 대한 신뢰도를 높이기 위해 스스로 검증하는 행위를 학습한다는 의미입니다.  단순히 정답률 향상뿐 아니라,  추론의 정확성과 신뢰성을 높이는 복잡한 사고 과정의 발달을 보여주는 지표입니다.
> <details>
> <summary>read the caption</summary>
> (a) Verify
> </details>



![](https://arxiv.org/html/2502.14768/extracted/6220745/figure/word_frequency_charts/re-evaluate.png)

> 🔼 그림 3은 특정 단어의 포함 여부에 따른 추론 성능에 대한 영향을 보여줍니다.  're-evaluate' 단어가 포함된 응답은 포함되지 않은 응답보다 상당히 높은 점수를 받았습니다. 이는 모델이 자신의 답변을 재검토하고 재평가하는 복잡한 추론 행동을 수행할 때 더 나은 성능을 보임을 시사합니다.  반대로, 다른 언어의 특정 토큰이 포함된 응답은 낮은 점수를 받았습니다. 이는 언어 혼용이 추론 능력을 저해한다는 점을 보여주는 것입니다.
> <details>
> <summary>read the caption</summary>
> (b) Re-evaluate
> </details>



![](https://arxiv.org/html/2502.14768/extracted/6220745/figure/word_frequency_charts/check.png)

> 🔼 그림 4는 훈련 과정에서 특정 단어의 빈도 변화를 추적한 그래프입니다.  (c) Check는 '확인'이라는 의미의 단어의 빈도 변화를 보여줍니다.  그래프를 통해 훈련 초기에 '확인'과 같은 단어가 드물게 나타나다가 훈련이 진행될수록 빈도가 점진적으로 증가하는 것을 확인할 수 있습니다.  이는 모델이 훈련 과정에서 자체적으로 추론 과정을 검증하고 확인하는 행위를 점점 더 많이 수행하게 되었음을 시사합니다. 즉, 단순히 답을 내는 것이 아니라 추론 과정의 정확성을 스스로 확인하고 검증하는 능력이 향상되었다는 것을 의미합니다.
> <details>
> <summary>read the caption</summary>
> (c) Check
> </details>



![](https://arxiv.org/html/2502.14768/extracted/6220745/figure/word_frequency_charts/yet.png)

> 🔼 그림 4는 강화 학습 과정 동안 특정 단어의 빈도 변화를 추적한 그래프입니다.  'verify'와 같은 반성적 단어와 'yet'이나 'let's'와 같은 조심스러운 단어, 그리고 중국어 단어의 사용 빈도가 시간이 지남에 따라 점진적으로 증가하는 것을 보여줍니다. 이는 모델이 갑작스러운 변화 없이 점진적으로 복잡한 추론 능력을 개발했음을 시사합니다.  즉, 'aha moment' 와 같은 갑작스러운 발견이 없었음을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> (d) Yet
> </details>



![](https://arxiv.org/html/2502.14768/extracted/6220745/figure/word_frequency_charts/lets.png)

> 🔼 그림 4는 강화 학습 과정에서 특정 단어의 빈도 변화를 추적한 것입니다.  (a)부터 (c)까지는 'verify', 're-evaluate', 'check' 와 같이 사고 과정을 반영하는 단어의 빈도가 점진적으로 증가하는 것을 보여줍니다.  (d)와 (e)는 'yet', 'let's' 와 같은 단어 또는 조심스러운 어조를 나타내는 단어의 빈도가 증가함을 보여줍니다.  (f)는 영어 응답에 중국어 단어가 등장하기 시작하는 것을 보여줍니다. 모든 단어의 빈도 변화는 급격한 변화 없이 꾸준히 증가하며, 이는 'aha moment' 와 같은 갑작스러운 전환점이 없다는 것을 시사합니다.  즉, 모델이 복잡한 추론 능력을 갑자기 획득하는 시점은 없으며, 점진적으로 발전한다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (e) Let’s
> </details>



![](https://arxiv.org/html/2502.14768/extracted/6220745/figure/word_frequency_charts/chinese_yes.png)

> 🔼 그림은 강화 학습 훈련 과정 동안 영어 응답에서 중국어 단어의 빈도를 추적합니다. 훈련 초기 단계에서는 중국어 단어가 거의 나타나지 않지만, 훈련이 진행됨에 따라 중국어 단어의 빈도가 점진적으로 증가하는 것을 보여줍니다. 이는 모델이 추론 과정에서 다양한 언어적 표현을 활용함으로써 보다 복잡한 추론 작업을 수행할 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (f) Chinese word
> </details>



![](https://arxiv.org/html/2502.14768/extracted/6220745/figure/limem_rl32.png)

> 🔼 그림 4는 강화 학습 과정에서 처음 1800단계 동안 단어 빈도 변화를 추적한 그래프입니다. (a)-(c)는 '확인', '검증'과 같은 반성적 단어들의 빈도가 서서히 증가함을 보여줍니다. (d)-(e)는 'Let’s', 'yet'과 같은 대화체 표현과 신중한 표현의 빈도가 증가함을 보여줍니다. (f)는 영어 응답에 중국어 단어가 나타나기 시작함을 보여줍니다. 이러한 모든 단어들의 빈도는 갑작스러운 변화 없이 점진적으로 증가하여, 갑작스러운 'aha moment'가 없다는 것을 시사합니다.  즉, 모델의 추론 능력 향상이 갑작스럽게 나타나는 것이 아니라 점진적으로 발전함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Tracking the frequency of words in the first 1,800 training steps. 1. Reflective words like 'check' and 'verify' slowly increased (a)-(c). 2. Conversational phrases (e.g., 'Let’s') and cautious terms (e.g., 'yet') became more frequent (d)-(e), 3. Chinese words began appearing in English responses (f). The frequency of all these words developed steadily without sudden jumps, suggesting that there may not be a distinct 'aha moment.'
> </details>



![](https://arxiv.org/html/2502.14768/extracted/6220745/figure/limem_rft32.png)

> 🔼 그림 5는 Logic-RL 모델이 AIME(2021-2024) 및 AMC(2022-2023) 데이터셋에서의 정확도를 훈련 단계에 따라 보여줍니다.  이 그림은 Logic-RL 모델이 해당 훈련 데이터셋에서 학습한 추론 능력이 얼마나 잘 일반화되는지 보여주는 지표입니다.  훈련 단계가 증가함에 따라 모델의 AIME 및 AMC 데이터셋에 대한 정확도가 향상되는 것을 확인할 수 있습니다. 이는 Logic-RL 모델이 훈련 데이터셋에서 학습한 추론 전략이 새로운 데이터셋에도 효과적으로 적용됨을 시사합니다. 즉, 모델이 단순히 암기하는 것이 아니라 실제로 추론 능력을 향상시켰음을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Training Step vs. Accuracy on AIME (2021-2024) and AMC (2022-2023) Datasets.
> </details>



![](https://arxiv.org/html/2502.14768/x4.png)

> 🔼 그림은 강화 학습(RL) 기반 모델의 성능을 보여줍니다.  RL 기반 모델은 논리 퍼즐 데이터셋을 사용하여 학습되었으며,  그림은 훈련 단계에 따른 검증 정확도, 평균 응답 길이, 그리고 보상을 나타냅니다.  특히, 모델이 훈련 중에 자율적으로 더 많은 사고 연산을 할당하여 성능을 향상시키는 방법을 보여줍니다.  흥미롭게도, 이 모델은 완전히 새로운 데이터셋(AIME, AMC)에서도 우수한 일반화 성능을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (a) RL
> </details>



![](https://arxiv.org/html/2502.14768/extracted/6220745/figure/rq3.png)

> 🔼 그림 6(b)는 Reject Sampling Fine-Tuning(RFT) 방법을 사용하여 훈련된 모델의 성능을 보여줍니다. RFT는 기존 모델에 Reject Sampling 기법을 적용하고, 규칙 기반 Best-of-N 방법을 사용하여 정답이면서 가장 짧은 응답을 수집하여 추가 미세 조정을 수행합니다. 이 그림은 훈련 데이터의 변형에 따른 테스트 정확도와 훈련 데이터 암기 정도의 변화를 보여줍니다. RFT는 테스트 정확도가 약간 향상되지만, 훈련 데이터를 과도하게 암기하는 경향(LiMem(f, Tr) 급격한 증가)을 보여주며, 진정한 추론 능력보다는 표면적인 답변 형식을 학습하는 경향이 있음을 시사합니다. 반면, RL 기반 방법은 LiMem(f, Tr) 증가가 최소화되거나 심지어 감소하면서 테스트 정확도가 높아지는 모습을 보여주어 일반화 능력이 더 우수함을 강조합니다.
> <details>
> <summary>read the caption</summary>
> (b) RFT
> </details>



![](https://arxiv.org/html/2502.14768/extracted/6220745/figure/base_instruct/base_length.png)

> 🔼 그림 6은 RFT(Reject sampling Fine-Tuning)와 RL(강화 학습)의 일반화 능력을 비교한 것입니다. RFT는 테스트 정확도를 약간 향상시키지만, LiMem(f;Tr) 지표가 급격히 증가하여 형식적인 답변만 학습함을 보여줍니다. 반면 RL은 LiMem(f;Tr)의 증가가 최소화되거나 심지어 감소하면서 더 높은 테스트 정확도를 달성합니다. 동일한 LiMem(f;Tr) 범위 내에서 RL이 RFT보다 훨씬 우수한 테스트 정확도를 보이는 것은 일반화 능력이 더 뛰어남을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: RFT memorizes while RL generalizes. RFT (Reject sampling Fine-Tuning) slightly improves test accuracy at the expense of rapidly increasing L⁢i⁢M⁢e⁢m⁢(f;T⁢r)𝐿𝑖𝑀𝑒𝑚𝑓𝑇𝑟LiMem(f;Tr)italic_L italic_i italic_M italic_e italic_m ( italic_f ; italic_T italic_r ), indicating it mainly learns superficial answer format than geniue reasoning. In contrast, RL achieves higher test accuracy with minimal or even negative increase in L⁢i⁢M⁢e⁢m⁢(f;T⁢r)𝐿𝑖𝑀𝑒𝑚𝑓𝑇𝑟LiMem(f;Tr)italic_L italic_i italic_M italic_e italic_m ( italic_f ; italic_T italic_r ). Within the same L⁢i⁢M⁢e⁢m𝐿𝑖𝑀𝑒𝑚LiMemitalic_L italic_i italic_M italic_e italic_m interval, RL outperform RFT in test acc greatly, suggesting better generalization ability.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | 2 | 3 | 4 | 5 | 6 | 7 | 8 | Avg. |
|---|---|---|---|---|---|---|---|---|
| **o3-mini-high** | 0.99 | 0.98 | 0.97 | 0.95 | 0.94 | 0.89 | 0.83 | 0.94 |
| **o1-2024-12-17** | 0.83 | 0.51 | 0.38 | 0.38 | 0.35 | 0.30 | 0.20 | 0.42 |
| **Deepseek-R1** | 0.91 | 0.73 | 0.77 | 0.78 | 0.75 | 0.88 | 0.83 | 0.81 |
| **GPT-4o** | 0.68 | 0.57 | 0.49 | 0.32 | 0.23 | 0.21 | 0.11 | 0.37 |
| **GPT-4o-mini** | 0.63 | 0.42 | 0.34 | 0.17 | 0.09 | 0.10 | 0.01 | 0.25 |
| **NuminaMath-7B-CoT** | 0.28 | 0.13 | 0.12 | 0.05 | 0.01 | 0.00 | 0.00 | 0.08 |
| **Deepseek-Math-7B** | 0.35 | 0.21 | 0.08 | 0.06 | 0.02 | 0.00 | 0.00 | 0.10 |
| **Qwen2.5-Base-7B** | 0.41 | 0.34 | 0.16 | 0.09 | 0.00 | 0.00 | 0.00 | 0.14 |
| **Qwen2.5-7B-Instruct-1M** | 0.49 | 0.40 | 0.25 | 0.11 | 0.06 | 0.02 | 0.01 | 0.19 |
| + **Logic-RL** | 0.99<sup>↑0.50</sup> | 0.99<sup>↑0.59</sup> | 0.94<sup>↑0.69</sup> | 0.92<sup>↑0.81</sup> | 0.91<sup>↑0.85</sup> | 0.80<sup>↑0.78</sup> | 0.67<sup>↑0.48</sup> | 0.89<sup>↑0.70</sup> |{{< /table-caption >}}
> 🔼 표 2는 다양한 난이도의 K&K 논리 퍼즐에 대해 추론 모델 및 일반 모델을 포함한 여러 모델의 성능을 비교한 표입니다.  다양한 수의 등장인물(2명에서 8명)을 가진 퍼즐에 대한 각 모델의 정확도를 보여주어, 모델의 추론 능력을 다양한 복잡도 수준에서 평가합니다.  이 표는 Logic-RL 모델의 성능을 다른 기존 모델들과 비교하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Comparison of different models including reasoning models and general models on K&K logic puzzle across various difficulty.
> </details>

{{< table-caption >}}
| Question | Response |
|---|---| 
| A very special island is inhabited only by knights and knaves. Knights always tell the truth, and knaves always lie. Five residents (William, Chloe, Lily, Jack, and Logan) made the following statements: (1) William said: "William is a knight and Chloe is a knight." (2) Chloe said: "Lily is a knight." (3) Lily said: "William is a knave and Jack is a knight." (4) Jack said: "William is a knave." (5) Logan said: "Lily is a knave if and only if William is a knave." So who is a knight and who is a knave? | To solve this, let’s start analyzing the statements one by one, beginning with William’s statement since it’s a good starting point due to its self-referential nature. William’s statement: "William is a knight and Chloe is a knight." If William is telling the truth (i.e., he is a knight), then both parts of his statement must be true. However, if William is a knight, the statement "William is a knight" is true, but the statement "Chloe is a knight" cannot determine the truth about Chloe at this point since we haven’t analyzed Chloe’s statement yet. Therefore, William cannot be a knight because it would lead to a contradiction. Let’s test both possibilities. Testing Chloe as a knight: If Chloe is a knight, then her statement "Lily is a knight" is true, so Lily is a knight. Analyzing Lily’s statement: "William is a knave and Jack is a knight." Now, we have determined: - William is a knave. - Chloe is a knight. Let’s verify all statements: - "William is a knight and Chloe is a knight" (False, since William is a knave). - "Lily is a knight" (True).  |{{< /table-caption >}}
> 🔼 본 표는 강화 학습을 통해 훈련된 대규모 언어 모델이 훈련 데이터에 존재하지 않았던 주저, 탐색, 요약, 검증과 같은 추론 동작을 자연스럽게 보이는 예시를 보여줍니다.  표에는 질문과 응답의 형태로 문제 풀이 과정이 제시되어 있으며, 모델이 문제 해결 과정에서 여러 가지 가능성을 탐색하고, 그 과정을 요약하고, 최종 답변을 내리기 전에 중간 결과를 검증하는 모습을 보여줍니다. 이는 단순히 암기가 아닌 실제 추론 능력이 향상되었음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: An example of a large language model trained through reinforcement learning naturally exhibiting reasoning behaviors such as hesitation, exploration, summarization, and verification, even though these behaviors were not present in the training data.
> </details>

{{< table-caption >}}
| Question | Response |
|---|---| 
| A very special island is inhabited only by knights and knaves. Knights always tell the truth, and knaves always lie. Three residents (Jack, Samuel, Lily) made the following statements: (1) Jack said, "If Samuel is a knight, then Lily is a knave." (2) Samuel said, "If Jack is a knight, then Lily is a knave." (3) Lily said, "Jack is a knight." So who is a knight and who is a knave? | Let’s analyze the statements step by step.  1. Jack’s statement is: "If Samuel is a knight then Lily is a knave." ... Now that we know Samuel is a knave, let’s analyze Samuel’s statement again: - Samuel’s statement: "If Jack is a knight then Lily is a knave." - An implication "If P then Q" is false only when P is true and Q is false. (Formula Application) Here, "If Jack is a knight then Lily is a knave" is false when Jack is a knight and Lily is not a knave. This is consistent with our previous conclusion that Jack is a knight and Lily is a knight. ... |{{< /table-caption >}}
> 🔼 표 4는 기사와 악당 퍼즐을 푸는 데 논리 공식을 사용하는 예시를 보여줍니다.  본 논문에서는 규칙 기반 강화 학습을 통해 학습된 언어 모델이 추론 과정에서 논리적 공식을 자연스럽게 적용하는 능력을 보여주는 사례를 제시하고 있습니다.  이 표는 모델이 단순히 패턴 매칭을 통해 답을 찾는 것이 아니라,  논리적 추론 과정을 거쳐 문제를 해결함을 보여주는 중요한 근거 자료로 활용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 4: An example of using logical formulas to solve a Knights and Knaves puzzle.
> </details>

{{< table-caption >}}
| Question | Response |
|---|---| 
| A very special island is inhabited only by knights and knaves. Knights always tell the truth, and knaves always lie. Six residents (Benjamin, Michael, Evelyn, Sophia, James, and Jacob) made the following statements: (1) Benjamin said, "If Sophia is a knight, then Evelyn is also a knight." (2) Michael said, "Benjamin is a knave, or James is a knight." (3) Evelyn said, "Sophia is a knight, or James is a knave." (4) Sophia said, "If Michael is a knave, then James is a knight." (5) James said, "Sophia is a knight, or Evelyn is a knight." (6) Jacob said, "Benjamin is a knave, and Sophia is a knight." So who is a knight and who is a knave? | <think> Let’s analyze each statement step-by-step based on whether the speaker is a knight or a knave. 1. Benjamin: "If Sophia is a knight then Evelyn is a knight" - If Benjamin is a knight, then the statement must be true. Thus, if Sophia is a knight, Evelyn has to be a knight. 2. Michael: "Benjamin is a knave or James is a knight" … From Jacob’s statement, if Jacob is a knight then Sophia must be a knight and Benjamin must be a knave.  … - 假设 Jacob 是骑士，那么 Jacob 的声明 "Benjamin 是背叛者且 Sophia 是骑士" 就是真的。这意味着 Benjamin 是背叛者而 Sophia 是骑士。 - 既然 Sophia 是骑士，根据 Benjamin 的声明 "如果 Sophia 是骑士那么 Evelyn 也是骑士"，Evelyn 也是骑士。 … 综上所述，Sophia, Evelyn, 和 Jacob 是骑士，而 Benjamin, Michael, 和 James 是背叛者。  (Language Switching) … |{{< /table-caption >}}
> 🔼 표 5는 논문에서 제시된 모델이 기사와 악당 퍼즐을 풀기 위해 언어 전환을 사용한 사례를 보여줍니다.  이 표는 모델이 추론 과정에서 영어와 중국어를 혼용하여 사용하는 것을 보여주는 하나의 예시를 제공합니다. 이는 모델이 다양한 언어를 사용하는 방식을 보여주며, 추론 과정의 복잡성과 융통성을 시사합니다.  특히, 모델이 중국어를 사용하는 부분은 모델의 내부적인 사고 과정이 복잡하고 다층적임을 보여주는 단서가 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 5: An example of our model used language switching to solve a Knights and Knaves puzzle.
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
{{< /gallery >}}