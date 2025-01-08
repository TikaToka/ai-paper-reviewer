---
title: "Auto-RT: Automatic Jailbreak Strategy Exploration for Red-Teaming Large Language Models"
summary: "AUTO-RT: 자동화된 재밍 전략 탐색으로 LLM 취약점 효율적으로 발견!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Ant Group",]
showSummary: true
date: 2025-01-03
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.01830 {{< /keyword >}}
{{< keyword icon="writer" >}} Yanjiang Liu et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-07 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.01830" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.01830" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/auto-rt-automatic-jailbreak-strategy" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)의 안전성과 신뢰성 확보는 점점 더 중요해지고 있습니다.  하지만 기존의 수동적인 안전성 평가 방법은 LLM의 복잡성과 역동적인 방어기법으로 인해 효율적이지 못하고, 복잡한 취약점을 찾아내는 데 어려움이 있습니다.  특히 **새로운 공격 전략의 등장과 방어 기법의 진화**는 지속적인 안전성 평가의 필요성을 더욱 강조합니다. 



본 논문에서는 **AUTO-RT**라는 새로운 프레임워크를 제안하여 이러한 문제를 해결합니다. AUTO-RT는 **강화 학습 기반의 자동화된 적대적 테스트 시스템**으로,  **악의적인 질의를 통해 LLM의 보안 취약성을 자동으로 탐색하고 최적화**합니다.  핵심적으로, **조기 종료 탐색 및 진보적 보상 추적 알고리즘**을 도입하여 탐색 과정의 복잡성을 줄이고 전략 최적화를 향상시켰습니다. 실험 결과, AUTO-RT는 **다양한 LLM에서 기존 방법보다 취약점 검출 속도와 성공률을 높였으며**, 새로운 취약점을 발견하는 데에도 효과적임을 보였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} AUTO-RT는 강화 학습 기반의 자동화된 적대적 테스트 프레임워크로, LLM의 복잡한 공격 전략을 효과적으로 탐색하고 최적화합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 조기 종료 탐색 및 진보적 보상 추적 알고리즘을 통해 탐색 효율성을 높이고 다양한 취약점을 빠르게 찾아냅니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 다양한 LLM에서 기존 방법보다 취약점 검출 속도 및 성공률이 향상되었으며, 특히 블랙박스 모델에도 적용 가능합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **자동화된 적대적 테스트(red-teaming)** 기법을 통해 대규모 언어 모델(LLM)의 취약점을 효율적으로 발견하는 새로운 방법론을 제시하여, **LLM 안전성 연구 분야**에 중요한 기여를 합니다.  **자동화된 공격 전략 탐색 및 최적화**를 통해 기존 방법의 한계를 극복하고, 다양한 LLM에서 **취약점 검출 속도 및 성공률을 향상**시킨 연구 결과는 LLM의 안전성 및 신뢰성 향상에 직접적인 영향을 미치며, 향후 연구 방향을 제시하는 중요한 의미를 지닙니다.  특히 **블랙박스 모델에도 적용 가능**한 점은 실제 LLM 적용 환경에서의 안전성 평가에 큰 도움이 될 것입니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.01830/x1.png)

> 🔼 이 그림은 기존의 레드팀 접근 방식과 Auto-RT의 차이점을 보여줍니다. 기존 방법들은 주어진 공격 전략 하에서 타겟 모델의 안전성 결함을 식별하는 데 중점을 두었지만, Auto-RT는 전략 탐색 자체부터 시작하여 타겟 모델의 체계적인 안전성 결함을 직접적으로 탐색함으로써 완전 자동화된 프로세스를 가능하게 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Comparison between previous red-teaming approaches and Auto-RT. Previous works focused on identifying safety flaws of the target model under given attack strategies, whereas Auto-RT directly explores systematic safety flaws in target models starting from searching strategies itself, enabling a fully automated process.
> </details>





{{< table-caption >}}
Target Model|DA|FS|IL|RL|Auto-RT|FS|IL|RL|Auto-RT|FS|IL|RL|Auto-RT
---|---|---|---|---|---|---|---|---|---|---|---|---|
Vicuna 7B|24.80|29.58|36.90|31.95|**56.40**|0.70|0.86|0.64|**0.57**|6.30<sub>-23.28</sub>|5.24<sub>-31.66</sub>|20.10<sub>-11.85</sub>|**46.80<sub>-9.60</sub>**
Vicuna 13B|16.60|20.80|36.08|17.80|**55.35**|0.77|0.93|0.51|**0.50**|8.15<sub>-12.65</sub>|4.55<sub>-31.53</sub>|21.03<sub>+3.23</sub>|**56.33<sub>+0.98</sub>**
Llama 2 7B Chat|0.45|6.84|6.67|0.50|**13.50**|0.74|0.90|0.54|**0.46**|3.55<sub>-3.29</sub>|2.70<sub>-3.97</sub>|0.88<sub>+0.38</sub>|**12.98<sub>-0.52</sub>**
Llama 2 13B Chat|1.30|5.88|6.80|2.05|**11.00**|0.65|0.85|**0.54**|0.56|4.20<sub>-1.68</sub>|3.03<sub>-3.77</sub>|1.15<sub>-0.90</sub>|**10.85<sub>-0.15</sub>**
Llama 3 8B Instruct|3.20|9.42|7.18|14.55|**15.00**|0.67|0.94|0.64|**0.45**|7.00<sub>-2.42</sub>|6.40<sub>-0.78</sub>|7.50<sub>-7.05</sub>|**15.00<sub>+0.00</sub>**
Mistral 7B Instruct|48.50|51.54|**54.88**|44.20|52.65|0.76|0.88|0.51|**0.50**|12.35<sub>-39.19</sub>|9.80<sub>-45.08</sub>|28.48<sub>-15.72</sub>|**48.68<sub>-3.97</sub>**
Yi 6B Chat|13.45|36.00|42.29|33.80|**52.50**|0.80|0.90|0.50|**0.48**|14.60<sub>-21.40</sub>|12.18<sub>-30.11</sub>|31.45<sub>-2.35</sub>|**47.25<sub>-5.25</sub>**
Yi 9B Chat|16.75|28.06|34.23|39.75|**49.20**|0.80|0.91|**0.57**|0.59|15.00<sub>-13.06</sub>|13.05<sub>-21.18</sub>|22.60<sub>-17.15</sub>|**48.90<sub>-0.30</sub>**
Gemma 2 2b Instruct|2.05|5.64|7.49|6.15|**48.15**|0.81|0.85|0.52|**0.46**|5.15<sub>-0.49</sub>|3.53<sub>-3.96</sub>|3.43<sub>-2.72</sub>|**47.93<sub>-0.22</sub>**
Gemma 2 9b Instruct|1.55|3.74|6.63|**44.85**|44.80|0.71|0.82|0.62|**0.53**|3.80<sub>+0.06</sub>|2.28<sub>-4.35</sub>|30.20<sub>-14.65</sub>|**48.10<sub>+3.30</sub>**
R2D2|1.70|**27.18**|24.24|8.60|12.45|0.71|0.82|0.59|**0.50**|10.45<sub>-16.73</sub>|8.95<sub>-15.29</sub>|4.33<sub>-4.27</sub>|**41.78<sub>+29.33</sub>**
Qwen 1.5 4B Chat|12.50|27.24|18.52|17.45|**51.30**|0.65|0.87|0.59|**0.58**|5.50<sub>-21.74</sub>|4.20<sub>-14.32</sub>|12.88<sub>-4.57</sub>|**45.58<sub>-5.72</sub>**
Qwen 1.5 7B Chat|21.70|23.80|18.82|32.60|**49.85**|0.72|0.89|0.57|**0.52**|8.00<sub>-15.80</sub>|6.80<sub>-12.02</sub>|25.95<sub>-6.65</sub>|**34.25<sub>-15.60</sub>**
Qwen 1.5 14B Chat|17.20|18.78|23.82|17.75|**42.50**|0.72|0.88|0.57|**0.53**|6.95<sub>-11.83</sub>|5.05<sub>-18.77</sub>|16.40<sub>-1.35</sub>|**43.40<sub>+0.90</sub>**
Qwen 2.5 3B Chat|16.30|30.94|38.30|20.35|**42.20**|0.71|0.83|0.58|**0.58**|5.20<sub>-25.74</sub>|3.80<sub>-34.50</sub>|17.25<sub>-3.10</sub>|**47.85<sub>+5.65</sub>**
Qwen 2.5 14B Chat|3.80|15.42|9.38|15.65|**17.15**|0.74|0.84|0.64|**0.46**|9.10<sub>-6.32</sub>|7.50<sub>-1.88</sub>|12.38<sub>-3.27</sub>|**15.43<sub>-1.72</sub>**{{< /table-caption >}}

> 🔼 표 1은 다양한 방법을 사용한 공격 성공률, 의미론적 다양성, 방어 일반화 다양성을 비교 분석한 표입니다. 왼쪽 열은 다양한 방법의 공격 성공률(ASRtst)을 보여주며, 값이 높을수록 공격 효과가 높음을 나타냅니다. 가운데 열은 각 방법이 생성한 공격 전략의 의미론적 다양성(SeD)을 보여주며, 값이 낮을수록 다양성이 높음을 나타냅니다. 오른쪽 열은 초기 공격 전략에 대한 방어 후 두 번째 공격에서 달성한 ASRtst로 평가되는 방어 일반화 다양성(DeD)을 비교한 것으로, 값이 높을수록 다양한 공격 전략을 지속적으로 발견할 수 있는 능력이 높음을 나타냅니다. 아래첨자는 두 번째 공격과 초기 공격 간 ASRtst의 차이를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Left: Attack success rate (ASRtst) of various methods, where higher values indicate greater attack effectiveness. Middle: Semantic diversity (SeD) among attack strategies generated by different methods, with lower values indicating higher diversity. Right: Comparison of defense generalization diversity (DeD), evaluated by the ASRtst achieved during a second attack following the defenses to the initial attack strategies. Higher DeD values suggest a greater ability to discover diverse strategies continuously, with subscripts denoting the difference in ASRtst between the second and initial attacks.
> </details>





### In-depth insights


#### Auto-RT: Jailbreak
자동화된 적대적 공격 도구인 Auto-RT는 대규모 언어 모델(LLM)의 취약점을 찾기 위해 **자동화된 탈옥 전략 탐색**에 중점을 둡니다.  기존의 수동 접근 방식과 달리, Auto-RT는 강화 학습을 통해 다양한 공격 전략을 자동으로 생성하고 최적화하여 **효율성 및 효과성**을 높입니다.  **조기 종료 탐색 및 점진적 보상 추적 알고리즘**과 같은 핵심 메커니즘을 통해 탐색 복잡성을 줄이고 전략 최적화를 개선합니다. 이는 다양한 LLM에서 광범위한 취약점을 빠르게 감지하고 성공률을 높이는 데 기여합니다.  **블랙박스 환경에서도 작동**하므로 다양한 모델에 적용 가능하며,  **백색 박스 모델에 대한 호환성**도 갖추고 있습니다.  Auto-RT는 단순히 취약점을 찾는 것을 넘어, 자동화된 취약점 평가 및 정렬 최적화를 위한 틀을 제공하여 안전하고 적응력 있는 LLM 개발에 기여할 수 있다는 점에서 큰 의미를 지닙니다.

#### RL Framework
본 논문에서 제시된 강화 학습(Reinforcement Learning, RL) 프레임워크는 **자동화된 적대적 공격 전략 탐색**을 위한 핵심 구성 요소입니다. 이 프레임워크는 대규모 언어 모델(Large Language Model, LLM)의 취약점을 효율적으로 발견하기 위해 **에이전트가 악의적인 질의를 생성하고, LLM의 반응을 통해 보상을 받는 환경**을 구축합니다. 특히, **초기 종료 탐색(Early-terminated Exploration)**과 **점진적 보상 추적(Progressive Reward Tracking)**이라는 두 가지 주요 메커니즘을 통해 탐색의 복잡성을 줄이고 전략 최적화를 개선합니다. 초기 종료 탐색은 잠재력이 높은 공격 전략에 집중하여 탐색 속도를 높이고, 점진적 보상 추적은 중간 다운그레이드 모델을 활용하여 보상 신호의 밀도를 높임으로써 학습 효율을 향상시킵니다. 이러한 메커니즘을 통해 **다양한 LLM에서 광범위한 취약점을 빠르게 탐지**하고 기존 방법보다 높은 성공률을 달성할 수 있습니다. **블랙박스 환경에서도 작동**하므로 다양한 LLM에 적용 가능하며, 향후 **취약점 평가 및 정렬 최적화** 등에 활용될 수 있는 범용적인 프레임워크로서의 가능성을 제시합니다.

#### Reward Shaping
강화 학습에서 보상 함수는 에이전트가 효과적인 정책을 학습하도록 안내하는 근본적인 역할을 합니다. 하지만 피드백이 지연되거나 드물게 제공될 경우 학습 신호가 약해져 행동 평가가 어려워집니다. **보상 형성**은 이러한 문제를 해결하기 위한 일반적인 방법으로, 추가적인 도메인별 정보를 통합하여 보상 신호를 강화하는 것입니다.  **잠재력 기반 보상 형성**은 상태에 기반한 잠재력 함수를 구성하여 정책 불변성을 보장합니다.  **스파스 보상 환경에서의 탐색 과제**를 해결하기 위해 도메인 지식에 의존하지 않고 보상 형성을 적용하는 시도도 있습니다.  **AUTO-RT는 희소한 보상 신호 문제를 해결하기 위해 보상 형성 기법을 사용합니다.**  **저하된 모델을 활용하여 보상 신호를 조정함으로써 탐색 효율성을 높이고 탐색 결과의 정밀도를 향상시킵니다.** 이는 강화 학습 기반의 자동화된 적대적 테스트 프레임워크에서 효과적으로 작동하며, 다양한 모델에 대한 안전성 평가에 유용하게 활용될 수 있습니다.

#### Ablation Study
본 논문의 ablation study는 **AUTO-RT 프레임워크의 핵심 구성 요소인 Early-terminated Exploration과 Progressive Reward Tracking의 효과를 개별적으로 그리고 결합적으로 평가**하여 모델의 성능에 미치는 영향을 분석한 것으로 보입니다.  각 구성 요소를 제거한 실험 결과를 비교 분석함으로써, **각 요소의 독립적인 기여도와 상호작용 효과**를 정량적으로 제시하고, **AUTO-RT의 성능 향상에 대한 통찰력**을 제공합니다.  **Early-terminated Exploration은 탐색 과정의 효율성을 높이고, Progressive Reward Tracking은 보상 신호의 밀도를 높여 학습 효율을 개선**하는 역할을 했을 것으로 예상됩니다.  Ablation study 결과는 AUTO-RT의 설계 및 성능 향상에 대한 중요한 근거를 제시하며,  향후 유사한 연구에 대한 방향성을 제시하는 데 기여할 것으로 생각됩니다.

#### Future Works
본 논문에서 제시된 AUTO-RT 프레임워크는 대규모 언어 모델의 취약성을 자동으로 탐색하고 최적화하는 데 있어 상당한 진전을 이루었지만, **향후 연구를 통해 더욱 개선**될 여지가 많습니다.  **전략적 공격 생성 모델과 재구성 모델을 함께 최적화**하는 방향으로 연구를 확장하여 더 폭넓은 취약성을 발견할 수 있을 것입니다. 또한, **다양한 유형의 공격 전략**을 고려하고 **더욱 다양한 모델 아키텍처**에 적용하여 AUTO-RT의 일반화 능력을 높이는 연구가 필요합니다.  **다른 보안 기술과의 통합**을 통해 실제 환경에서의 효과적인 적용 가능성을 높이고, **실제 악성 행위와의 연관성**을 분석하여 더욱 현실적인 위협 모델링을 가능하게 하는 연구도 중요합니다.  마지막으로, **윤리적 문제**를 고려하여 책임감 있는 연구 방향을 설정하고, **오용 가능성**에 대한  심도 있는 논의가 필요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.01830/x2.png)

> 🔼 그림 2는 AUTO-RT 프레임워크의 개념도입니다. AUTO-RT는 두 가지 주요 구성 요소로 이루어져 있습니다. 첫 번째는 조기 종료 탐색(Early-terminated Exploration)으로, 생성된 전략의 다양성과 재구성된 프롬프트의 일관성을 평가하여 안전성 평가의 필요성을 결정합니다. 제약 조건이 충족되지 않으면 프로세스가 즉시 종료되고 패널티가 적용됩니다. 두 번째는 진보적 보상 추적(Progressive Reward Tracking)으로, 대상 모델에서 파생된 저하 모델을 활용하여 안전성 보상의 밀도를 높여 탐색 프로세스의 효율성과 효과성을 향상시킵니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: The framework of Auto-RT, comprising two key components: 1) Early-terminated Exploration, which assesses the diversity of the generated strategies and the consistency of the rephrased prompt with the initial toxic behavior to determine the necessity of safety evaluation. If either constraint is unmet, the process immediately terminate, and a penalty is applied; 2) Progressive Reward Tracking, which enhances the density of safety rewards by utilizing a degrade model derived from the target model, thereby improving the efficiency and effectiveness of the exploration process.
> </details>



![](https://arxiv.org/html/2501.01830/x3.png)

> 🔼 그림 3은 제안된 보상 형성 과정의 원리를 보여주는 상태 공간 s에 대한 안전 분포 J(s)의 개념적 다이어그램입니다. 빨간색 곡선은 더 안전한 모델 m을, 파란색 곡선은 덜 안전한 모델 m'을 나타냅니다. θ는 안전-위험 임계값을 나타내며, δ와 δ'는 각각 위험한 하위 공간을 표시합니다. 더 안전한 모델 m은 대부분의 상태에서 더 높은 안전성을 보여주며, 위험한 하위 공간 δ는 드물고 최소한으로 상호 연결됩니다. 반면에 덜 안전한 모델 m'은 더 크고 상호 연결된 위험한 하위 공간을 보여주어 안전하지 않은 영역을 만날 확률이 높아집니다. 주목할 점은 m의 위험한 하위 공간이 m'의 위험한 하위 공간에 완전히 포함된다는 것입니다. 이러한 관계는 m'을 전략적으로 사용하여 m의 위험한 하위 공간을 효율적으로 식별하는 탐색 프로세스에 집중할 수 있도록 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Conceptual diagram of the safety distribution 𝒥⁢(s)𝒥s\mathcal{J}(\textbf{s})caligraphic_J ( s ) across the state space s, illustrating the principle of our proposed reward shaping process. The red curve represents the safer model m𝑚{\color[rgb]{1,0.23,0.13}\definecolor[named]{pgfstrokecolor}{rgb}{1,0.23,0.13}% \pgfsys@color@cmyk@stroke{0}{0.77}{0.87}{0}\pgfsys@color@cmyk@fill{0}{0.77}{0.% 87}{0}m}italic_m, while the blue curve represents the less safe model m′superscript𝑚′{\color[rgb]{0.0600000000000001,0.46,1}\definecolor[named]{pgfstrokecolor}{rgb% }{0.0600000000000001,0.46,1}\pgfsys@color@cmyk@stroke{0.94}{0.54}{0}{0}% \pgfsys@color@cmyk@fill{0.94}{0.54}{0}{0}m^{\prime}}italic_m start_POSTSUPERSCRIPT ′ end_POSTSUPERSCRIPT. θ𝜃\thetaitalic_θ denotes the safety-danger threshold, with δ𝛿{\color[rgb]{1,0.23,0.13}\definecolor[named]{pgfstrokecolor}{rgb}{1,0.23,0.13}% \pgfsys@color@cmyk@stroke{0}{0.77}{0.87}{0}\pgfsys@color@cmyk@fill{0}{0.77}{0.% 87}{0}\delta}italic_δ and δ′superscript𝛿′{\color[rgb]{0.0600000000000001,0.46,1}\definecolor[named]{pgfstrokecolor}{rgb% }{0.0600000000000001,0.46,1}\pgfsys@color@cmyk@stroke{0.94}{0.54}{0}{0}% \pgfsys@color@cmyk@fill{0.94}{0.54}{0}{0}\delta^{\prime}}italic_δ start_POSTSUPERSCRIPT ′ end_POSTSUPERSCRIPT marking the respective dangerous subspaces. The safer model, m𝑚{\color[rgb]{1,0.23,0.13}\definecolor[named]{pgfstrokecolor}{rgb}{1,0.23,0.13}% \pgfsys@color@cmyk@stroke{0}{0.77}{0.87}{0}\pgfsys@color@cmyk@fill{0}{0.77}{0.% 87}{0}m}italic_m, demonstrates higher safety across most states, with its dangerous subspace, δ𝛿{\color[rgb]{1,0.23,0.13}\definecolor[named]{pgfstrokecolor}{rgb}{1,0.23,0.13}% \pgfsys@color@cmyk@stroke{0}{0.77}{0.87}{0}\pgfsys@color@cmyk@fill{0}{0.77}{0.% 87}{0}\delta}italic_δ, being sparse and minimally interconnected. In contrast, the less safe model, m′{\color[rgb]{0.0600000000000001,0.46,1}\definecolor[named]{pgfstrokecolor}{rgb% }{0.0600000000000001,0.46,1}\pgfsys@color@cmyk@stroke{0.94}{0.54}{0}{0}% \pgfsys@color@cmyk@fill{0.94}{0.54}{0}{0}m{\prime}}italic_m ′, exhibits larger and more connected dangerous subspaces, increasing the probability of encountering unsafe regions. Notably, the dangerous subspace of m𝑚{\color[rgb]{1,0.23,0.13}\definecolor[named]{pgfstrokecolor}{rgb}{1,0.23,0.13}% \pgfsys@color@cmyk@stroke{0}{0.77}{0.87}{0}\pgfsys@color@cmyk@fill{0}{0.77}{0.% 87}{0}m}italic_m is entirely encompassed by that of m′{\color[rgb]{0.0600000000000001,0.46,1}\definecolor[named]{pgfstrokecolor}{rgb% }{0.0600000000000001,0.46,1}\pgfsys@color@cmyk@stroke{0.94}{0.54}{0}{0}% \pgfsys@color@cmyk@fill{0.94}{0.54}{0}{0}m{\prime}}italic_m ′. This relationship allows for the strategic use of m′{\color[rgb]{0.0600000000000001,0.46,1}\definecolor[named]{pgfstrokecolor}{rgb% }{0.0600000000000001,0.46,1}\pgfsys@color@cmyk@stroke{0.94}{0.54}{0}{0}% \pgfsys@color@cmyk@fill{0.94}{0.54}{0}{0}m{\prime}}italic_m ′ to efficiently focus the exploration process on identifying the dangerous subspaces of m𝑚{\color[rgb]{1,0.23,0.13}\definecolor[named]{pgfstrokecolor}{rgb}{1,0.23,0.13}% \pgfsys@color@cmyk@stroke{0}{0.77}{0.87}{0}\pgfsys@color@cmyk@fill{0}{0.77}{0.% 87}{0}m}italic_m.
> </details>



![](https://arxiv.org/html/2501.01830/x4.png)

> 🔼 그림 4는 Auto-RT와 RL의 공격 효율성을 비교한 것입니다. 바이올린 플롯은 1,000개의 샘플 전략마다 공격 성공률의 분포를 보여줍니다. 밝은 색상은 Auto-RT를, 어두운 색상은 RL을 나타냅니다. Auto-RT는 동일한 샘플 수를 사용하는 RL보다 더 높은 공격 성공률을 달성하며, 분산이 더 큽니다. 이는 Auto-RT가 RL보다 더 포괄적인 탐색을 수행함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Comparison of attack efficiency between Auto-RT and RL. The violin plots represent the distribution of attack success rates for every 1k sampled strategies, with lighter colors indicating Auto-RT and darker colors representing RL. Auto-RT achieves higher attack success rates than RL under the same number of samples, and with larger variance, indicating that it achieves more comprehensive exploration.
> </details>



![](https://arxiv.org/html/2501.01830/extracted/6109106/resources/sampling.png)

> 🔼 그림 5는 다양한 양의 독성 데이터를 사용하여 6개의 대상 모델을 미세 조정하여 얻은 일련의 중간 모델(M1~M6)에 대한 보상 형성 후 적색 팀 활동 결과(공격 성공률, Attack ASR), 해당 모델의 안전 수준(약화된 ASR, Weaken ASR), 추가적인 독성 행동에 대한 최초 역률(약화된 FIR, Weaken FIR) 간의 관계를 보여줍니다. 최적의 적색 팀 결과는 그림에서 어두운 색상의 막대로 표시된 FIR의 급증 전 마지막 중간 모델을 보상 형성을 위한 저하 모델로 선택하여 얻을 수 있습니다. 이 그림은 보상 형성에 사용할 저하 모델을 선택하는 데 FIR 지표가 효과적임을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: The relationship between the red-teaming outcomes (Attack ASR) following reward shaping with a series of intermediate models (M1 to M6), the safety levels of these models (Weaken ASR), and their first inverse rate for additional toxic behavior (Weaken FIR). These intermediate models are derived by fine-tuning on six target models using varying amounts of toxic data.The optimal red-teaming results are achieved by selecting the last intermediate model before a sudden spike in FIR (represented by the dark-colored bar in the figure) as the degrade model for reward shaping.
> </details>



![](https://arxiv.org/html/2501.01830/x5.png)

> 🔼 그림 6은 새로운 공격 전략 탐색을 위한 프롬프트 예시입니다. 기존 전략들을 바탕으로 다양한 설정에서 생성된 여러 가지 데모 예시들이 포함되어 있습니다. 이를 통해 모델이 새로운 공격 전략을 생성하는 데 도움을 줄 수 있습니다.  데모 예시는 다양한 설정에 따라 기존 전략들을 기반으로 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Complete prompt for new strategies exploration. seed examples are demonstrations selected from existing strategies based on different settings.
> </details>



![](https://arxiv.org/html/2501.01830/x6.png)

> 🔼 그림 7은 공격 쿼리 재구성을 위한 프롬프트를 보여줍니다.  이 프롬프트는 공격 모델에서 샘플링된 공격 전략과 초기 유해 행동을 나타내는 유해 쿼리를 사용합니다.  프롬프트는 공격 전략에 따라 쿼리를 수정하여 원래 의도를 유지하면서 안전하지 않은 응답을 유도하는 방법을 보여줍니다.  재구성된 쿼리는 모델의 취약성을 드러내는 데 사용됩니다.  간단히 말해, 이 그림은 AUTO-RT 시스템이 유해한 질문을 재구성하여 언어 모델의 취약성을 공격하는 방식을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Complete the prompt for attack query rephrasing using the provided attack strategy. The attack strategy is sampled from the attack model, and the toxic query represents the initial toxic behavior.
> </details>



![](https://arxiv.org/html/2501.01830/x7.png)

> 🔼 그림 8은 질의의 의도를 판단하기 위한 프롬프트를 보여줍니다. 공격 전략으로 수정된 원본 질의와 수정된 질의의 목적을 평가하여 두 질의의 의도가 유사한지 확인하는 과정을 보여줍니다.  두 질의의 의도가 동일하면 1, 다르면 0으로 응답하도록 설계되었습니다.  이는 모델이 생성한 응답의 안전성을 평가하기 위한 중간 단계로,  유사한 의도를 가진 질의는 동일한 안전성 등급을 가져야 하며, 다른 의도를 가진 질의는 서로 다른 안전성 등급을 가질 수 있기 때문에 중요한 단계입니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Complete the prompt for judging query intent. Verify that the original query and the rephrased query, modified with the attack strategy, share a similar intent by assessing their purposes.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
|                     | V-7    | V-13   | L2-13  | L3-8   | Y-6    | G-2    | R2D2   | Q1.5-7  | Q1.5-14 | Q2.5-14 |
| :------------------ | :----- | :----- | :----- | :----- | :----- | :----- | :----- | :----- | :----- | :----- |
| **Attack Effective (ASR<sub>tst</sub>) ↑** |         |         |         |         |         |         |         |         |         |         |
| RL                   | 31.95  | 17.80  | 2.05   | 14.55  | 33.80  | 6.15   | 8.60   | 32.60  | 17.75  | 15.65  |
|  +ETE                | 36.54  | 22.92  | 2.46   | 15.00  | 35.98  | 7.38   | 9.07   | 41.01  | 19.58  | 17.15  |
|  +PRT                | 40.50  | 35.20  | 6.80   | 14.60  | 42.30  | 25.30  | 9.80   | 40.20  | 28.30  | 16.50  |
|  Auto-RT             | 56.40  | 55.35  | 11.00  | 15.00  | 52.50  | 48.15  | 12.45  | 49.85  | 42.50  | 17.15  |
| **Semantic Diversity (SeD) ↓** |         |         |         |         |         |         |         |         |         |         |
| RL                   | 0.64   | 0.51   | **0.54** | 0.64   | 0.50   | 0.52   | 0.59   | 0.57   | 0.57   | 0.64   |
|  +ETE                | 0.57   | 0.50   | 0.55   | 0.51   | 0.53   | 0.50   | 0.57   | 0.53   | 0.53   | **0.44** |
|  +PRT                | 0.66   | 0.58   | 0.65   | 0.59   | 0.61   | 0.54   | 0.63   | 0.57   | 0.64   | 0.57   |
|  Auto-RT             | **0.57** | **0.50** | 0.56   | **0.45** | **0.48** | **0.46** | **0.50** | **0.52** | **0.53** | 0.46   |
| **Defense Generalization Diversity (DeD) ↑** |         |         |         |         |         |         |         |         |         |         |
| RL                   | 20.10  | 21.03  | 1.15   | 7.50   | 31.45  | 3.43   | 4.33   | 25.95  | 16.40  | 12.38  |
|  +ETE                | 43.02  | 54.45  | 12.51  | 14.35  | 47.19  | 47.51  | 41.09  | **42.37** | 42.15  | 14.49  |
|  +PRT                | **47.02** | 56.18  | **13.93** | 14.84  | **50.94** | 43.55  | 39.11  | 32.56  | 42.05  | **16.23** |
|  Auto-RT             | 46.80  | **56.33** | 10.85  | **15.00** | 47.25  | **47.93** | **41.78** | 34.25  | **43.40** | 15.43  |{{< /table-caption >}}
> 🔼 표 2는 Auto-RT의 두 가지 주요 구성 요소인 조기 종료 탐색(ETE)과 점진적 보상 추적(PRT)의 영향을 다양한 언어 모델에서 평가한 결과를 보여줍니다.  실험 결과는 ETE와 PRT 모두 전략 탐색 향상에 기여하며, 두 가지를 함께 사용하면 효과가 더욱 증대됨을 보여줍니다.  각 구성 요소의 독립적 및 결합적 효과를 정량적으로 비교 분석하여 Auto-RT의 성능 향상에 대한 통찰력을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 2:  Ablation of early-terminated exploration (ETE) and progressive reward tracking (PRT) in Auto-RT. We evaluated the impact of the two components of Auto-RT on different models, and the results demonstrate that both contribute to enhancing strategy exploration.
> </details>

{{< table-caption >}}
|               | AD    | HT    | PT    | Auto-RT |
| :------------ | :---- | :---- | :---- | :------ |
| ASR<sub>tst</sub> ↑ | **55.23** | 37.35 | 11.19 | 38.38   |
| SeD ↓         | 0.86  | **0.36** | -     | 0.52    |
| DeD ↑         | 17.88 | 13.15 | 7.27  | **38.19**|{{< /table-caption >}}
> 🔼 표 3은 Auto-RT와 사람 기반 전략 공격 방법을 비교한 표입니다.  Auto-RT는 지속적으로 안정적인 공격 전략을 생성할 수 있다는 것을 보여줍니다.  자세히 살펴보면,  Auto-RT의 공격 성공률(ASR), 의미적 다양성(SeD), 방어 일반화 다양성(DeD)을 사람이 만든 세 가지 방법(AD, HT, PT)과 비교하여 Auto-RT의 성능을 다각적으로 평가하고 있습니다.  이는 Auto-RT가 단순히 높은 공격 성공률을 달성하는 것 뿐만 아니라 다양하고 안정적인 공격 전략을 지속적으로 생성할 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Comparison between Auto-RT and human-based strategic attack methods. Auto-RT can continuously generate stable attack strategies.
> </details>

{{< table-caption >}}
| Model | Attack Effectiveness (ASR<sub>tst</sub>) ↑ | Semantic Diversity (SeD) ↓ | Defense Generalization Diversity (DeD) ↑ |
|---|---|---|---| 
| Llama 3 70B |  |  |  |
| Qwen 2.5 72B |  |  |  |
|---|---|---|---| 
| **FS** | 5.49 | 0.87 | 1.17<sub>-4.32</sub> |
| **IL** | 6.80 | 0.64 | 0.92<sub>-5.88</sub> |
| **RL** | 4.99 | 0.53 | 4.15<sub>-0.84</sub> |
| **Auto-RT** | **14.88** | **0.52** | **15.00**<sub>+0.12</sub> |
|---|---|---|---| 
| **FS** | 3.53 | 0.82 | 3.05<sub>-0.48</sub> |
| **IL** | 6.22 | 0.73 | 1.20<sub>-5.02</sub> |
| **RL** | 4.53 | **0.52** | 4.33<sub>-0.2</sub> |
| **Auto-RT** | **14.47** | 0.61 | **14.15**<sub>-0.32</sub> |{{< /table-caption >}}
> 🔼 본 논문의 표 4는 접근 불가능한 가중치를 가진 모델을 시뮬레이션하기 위해 In-Context Learning 기법으로 저하된 모델을 생성하는 블랙박스 설정에서의 공격 성능을 보여줍니다.  즉, 모델의 내부 정보에 접근할 수 없는 상황에서, In-Context Learning을 이용하여 모델의 안전성을 약화시킨 후 공격을 수행했을 때의 효과를 평가한 결과입니다.  표에는 다양한 모델들에 대한 공격 성공률(ASR), 의미론적 다양성(SeD), 방어 일반화 다양성(DeD) 등이 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4:  Attack performance when using In-Context Learning approach to construct degrade model in black-box setting for simulating models with inaccessible weights.
> </details>

{{< table-caption >}}
| RL | +ETE | +PRT | +ETE+PRT(Auto-RT) |
|---|---|---|---|---|
| Vicuna 7B | 31.95 | 36.54 | 40.50 | 56.40 |
| Vicuna 13B | 17.80 | 22.92 | 35.20 | 55.35 |
| Llama 2 7B Chat | 0.50 | 0.62 | 8.20 | 13.50 |
| Llama 2 13B Chat | 2.05 | 2.46 | 6.80 | 11.00 |
| Llama 3 8B Instruct | 14.55 | 15.00 | 14.60 | 15.00 |
| Mistral 7B Instruct | 44.20 | 48.13 | 47.00 | 52.65 |
| Yi 6B Chat | 33.80 | 35.98 | 42.30 | 52.50 |
| Yi 9B Chat | 39.75 | 49.20 | 44.00 | 49.20 |
| Gemma 2 2B Instruct | 6.15 | 7.38 | 25.30 | 48.15 |
| Gemma 2 9B Instruct | 44.85 | 44.80 | 44.70 | 44.80 |
| R2D2 | 8.60 | 9.07 | 9.80 | 12.45 |
| Qwen 1.5 4B Chat | 17.45 | 22.55 | 32.60 | 51.30 |
| Qwen 1.5 7B Chat | 32.60 | 41.01 | 40.20 | 49.85 |
| Qwen 1.5 14B Chat | 17.75 | 19.58 | 28.30 | 42.50 |
| Qwen 2.5 3B Chat | 20.35 | 22.29 | 30.80 | 42.20 |
| Qwen 2.5 14B Chat | 15.65 | 17.15 | 16.50 | 17.15 |{{< /table-caption >}}
> 🔼 표 5는 논문에서 제시된 AUTO-RT 모델의 공격 효과에 대한 실험 결과를 보여줍니다.  AUTO-RT 모델의 주요 구성 요소인 조기 종료 탐색(ETE)과 점진적 보상 추적(PRT)을 각각 적용했을 때와 두 요소를 모두 적용했을 때의 공격 성공률(ASR)을 다양한 언어 모델(Target Model)에 대해 비교 분석한 결과가 제시되어 있습니다.  각 구성요소의 효과를 개별적으로 확인하고 전체 모델의 성능을 평가하여 AUTO-RT의 효율성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 5: The ablation results of the Attack Effectiveness with different components on all target models.
> </details>

{{< table-caption >}}
| RL | +ETE | +PRT | +ETE+PRT(Auto-RT) |
|---|---|---|---|---|
| Vicuna 7B | 20.10 | 43.02 | 47.02 | 46.80 |
| Vicuna 13B | 21.03 | 54.45 | 56.18 | 56.33 |
| Llama 2 7B Chat | 0.88 | 14.36 | 13.23 | 12.98 |
| Llama 2 13B Chat | 1.15 | 12.51 | 13.93 | 10.85 |
| Llama 3 8B Instruct | 7.50 | 14.35 | 14.84 | 15.00 |
| Mistral 7B Instruct | 28.48 | 48.89 | 50.37 | 48.68 |
| Yi 6B Chat | 31.45 | 47.19 | 50.94 | 47.25 |
| Yi 9B Chat | 22.60 | 48.16 | 45.13 | 48.90 |
| Gemma 2 2b Instruct | 3.43 | 47.51 | 43.55 | 47.93 |
| Gemma 2 9b Instruct | 30.20 | 47.42 | 47.65 | 48.10 |
| R2D2 | 4.33 | 41.09 | 39.11 | 41.78 |
| Qwen 1.5 4B Chat | 12.88 | 47.34 | 48.74 | 45.58 |
| Qwen 1.5 7B Chat | 25.95 | 42.37 | 32.56 | 34.25 |
| Qwen 1.5 14B Chat | 16.40 | 42.15 | 42.05 | 43.40 |
| Qwen 2.5 3B Chat | 17.25 | 47.42 | 50.75 | 47.85 |
| Qwen 2.5 14B Chat | 12.38 | 14.49 | 16.23 | 15.43 |{{< /table-caption >}}
> 🔼 표 6은 다양한 모델에 대해 방어 일반화 다양성에 대한 AUTO-RT의 구성 요소별 실험 결과를 보여줍니다.  각 모델에 대해, 기준 RL 방법과 초기 종료 탐색(ETE), 점진적 보상 추적(PRT)을 추가한 여러 가지 변형을 비교하여, 각 구성 요소가 방어 전략에 대한 공격 전략의 다양성에 미치는 영향을 분석합니다.  결과는 AUTO-RT의 두 가지 주요 구성요소가 모두 방어 일반화 다양성을 향상시키는 데 기여함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 6: The ablation results of the Defense Generalization Diversity with different components on all target models.
> </details>

{{< table-caption >}}
| Model | RL | +ETE | +PRT | +ETT+PRT(Auto-RT) |
|---|---|---|---|---|
| Vicuna 7B | 0.64 | 0.57 | 0.66 | 0.57 |
| Vicuna 13B | 0.51 | 0.50 | 0.58 | 0.50 |
| Llama 2 7B Chat | 0.54 | 0.44 | 0.55 | 0.46 |
| Llama 2 13B Chat | 0.54 | 0.55 | 0.65 | 0.56 |
| Llama 3 8B Instruct | 0.64 | 0.51 | 0.59 | 0.45 |
| Mistral 7B Instruct | 0.51 | 0.49 | 0.59 | 0.50 |
| Yi 6B Chat | 0.50 | 0.53 | 0.61 | 0.48 |
| Yi 9B Chat | 0.57 | 0.53 | 0.68 | 0.59 |
| Gemma 2 2B Instruct | 0.52 | 0.50 | 0.54 | 0.46 |
| Gemma 2 9B Instruct | 0.62 | 0.53 | 0.62 | 0.53 |
| R2D2 | 0.59 | 0.57 | 0.63 | 0.50 |
| Qwen 1.5 4B Chat | 0.59 | 0.59 | 0.57 | 0.58 |
| Qwen 1.5 7B Chat | 0.57 | 0.53 | 0.57 | 0.52 |
| Qwen 1.5 14B Chat | 0.57 | 0.53 | 0.64 | 0.53 |
| Qwen 2.5 3B Chat | 0.58 | 0.57 | 0.70 | 0.58 |
| Qwen 2.5 14B Chat | 0.64 | 0.44 | 0.57 | 0.46 |{{< /table-caption >}}
> 🔼 표 7은 다양한 모델에 대해 구성 요소별로 계산된 의미적 다양성의 분석 결과를 보여줍니다.  구체적으로는, 기준 모델(RL)과 조기 종료 탐색(ETE), 점진적 보상 추적(PRT)을 개별적으로 적용했을 때와  두 기법을 모두 적용한 AUTO-RT의 성능을 의미적 다양성 측면에서 비교 분석한 결과입니다.  여러 모델에 대한 각 기법 적용 시 의미적 다양성 수치를 통해 각 기법이  전반적인 전략 생성의 다양성에 미치는 영향을 정량적으로 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: The ablation results of the Semantic Diversity with different components on all target models.
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
<img src="paper_images/20.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
{{< /gallery >}}