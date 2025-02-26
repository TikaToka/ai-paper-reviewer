---
title: "Mobile-Agent-V: Learning Mobile Device Operation Through Video-Guided Multi-Agent Collaboration"
summary: "Mobile-Agent-V는 비디오 지도를 통해 모바일 기기 작동을 학습하는 혁신적인 다중 에이전트 협업 프레임워크입니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Vision-Language Models", "🏢 Beijing Jiaotong University",]
showSummary: true
date: 2025-02-24
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.17110 {{< /keyword >}}
{{< keyword icon="writer" >}} Junyang Wang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-25 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.17110" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.17110" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/mobile-agent-v-learning-mobile-device" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

모바일 기기 사용 증가로 인해 효율적인 작업 관리를 위한 자동화의 필요성이 커지고 있습니다. 하지만 기존 AI 기반 프레임워크는 운영 지식 부족으로 어려움을 겪고 있으며, 수동으로 지식을 입력하는 방식은 비효율적입니다.  

본 논문에서는 이러한 문제를 해결하기 위해 Mobile-Agent-V라는 새로운 프레임워크를 제시합니다. Mobile-Agent-V는 비디오 지도를 통해 모바일 자동화를 위한 풍부한 지식을 제공하며, 특수한 샘플링이나 전처리 과정 없이 비디오 입력을 활용합니다. 슬라이딩 윈도우 전략과 비디오 에이전트, 심층 반사 에이전트를 통합하여 사용자 지침과 작업 실행의 일치성을 보장합니다. 실험 결과, 기존 프레임워크 대비 30%의 성능 향상을 확인했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 비디오 지도 학습을 통해 모바일 기기 작동에 대한 풍부하고 비용 효율적인 지식을 제공합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 슬라이딩 윈도우 전략과 비디오 에이전트 및 심층 반사 에이전트를 통합하여 작업 실행 성능을 향상시킵니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 기존 프레임워크에 비해 30%의 성능 향상을 달성하여 모바일 자동화 분야에 새로운 가능성을 제시합니다.  {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **모바일 자동화 분야의 어려움을 해결하기 위한 혁신적인 접근 방식**을 제시하여, 연구자들에게 **새로운 연구 방향**을 제시하고 **모바일 애플리케이션 자동화 기술 발전**에 크게 기여할 수 있습니다. 특히, 비디오 지도 학습 기법을 통해 기존의 수동적이고 비효율적인 방법들을 극복하고, **더욱 효율적이고 확장 가능한 모바일 자동화 시스템 개발**에 대한 새로운 가능성을 열어줍니다. 또한, **다양한 모바일 기기 및 애플리케이션 환경**에서도 적용 가능한 범용적인 접근 방식을 제시함으로써, 향후 연구의 폭넓은 활용과 발전을 위한 토대를 마련합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.17110/extracted/6231218/intro.png)

> 🔼 그림 1은 기존 방식과 Mobile-Agent-V의 차이점을 보여줍니다. 기존 에이전트는 작업 지식이 부족하여 과도한 단계를 거치더라도 작업을 완료하지 못하지만, 수동으로 작성된 지식은 문서화 및 반복적인 검증이 필요합니다. 반면 Mobile-Agent-V는 작업 비디오를 활용하여 실행 및 녹화만으로 지식 주입을 효율적으로 수행합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Comparison between a baseline agent, manually written knowledge, and Mobile-Agent-V. The baseline agent, lacking operation knowledge, struggles to complete the task, requiring excessive steps and still failing. Manually written knowledge requires documentation and iterative verification. In contrast, Mobile-Agent-V leverages operation videos, requiring only execution and recording, making knowledge injection far more efficient.
> </details>





{{< table-caption >}}
| Method | Basic Instruction |  |  |  | Normal Instruction |  |  |  | Advanced Instruction |  |  |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|  | SR | CR | DA | Step | SR | CR | DA | Step | SR | CR | DA | Step |
| AppAgent | 90 | 85.0 | 78.0 | 5.5 | 50 | 70.0 | 50.5 | 12.0 | 10 | 40.5 | 25.0 | 19.1 |
| Mobile-Agent-v1 | 80 | 86.5 | 79.5 | 5.3 | 40 | 72.5 | 48.0 | 11.5 | 10 | 43.0 | 27.8 | 19.8 |
| Mobile-Agent-v2 | 90 | 90.0 | 84.3 | 5.0 | 60 | 76.3 | 54.4 | 10.5 | 20 | 49.3 | 31.2 | 18.6 |
| Mobile-Agent-V | 100 | 100 | 97.8 | 4.5 | 90 | 93.3 | 80.3 | 6.6 | 70 | 86.8 | 60.1 | 10.9 |
| Δ | +10 | +10.0 | +13.5 | -0.5 | +30 | +17.0 | +25.9 | -3.9 | +50 | +37.5 | +18.9 | -7.7 |
| Human-Know. | 100 | 100 | 98.9 | 4.5 | 100 | 95.2 | 83.7 | 6.2 | 70 | 82.6 | 58.8 | 10.7 |{{< /table-caption >}}

> 🔼 표 1은 다양한 종류의 지시어(instruction)에 따른 Mobile-Agent-V의 성능 평가 결과를 보여줍니다.  'SR'(성공률), 'CR'(완료율), 'DA'(의사결정 정확도), 'Step'(단계 수) 네 가지 지표를 사용하여 기본, 일반, 고급 세 가지 수준의 지시어에 대한 Mobile-Agent-V의 성능을 측정했습니다.  Human-Know. 열은 사람이 직접 지식을 입력한 경우의 결과를 나타냅니다. 이를 통해 Mobile-Agent-V의 성능을 다른 기존 방법들과 비교하고, 비디오 기반 학습의 효과를 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Evaluation results across different instructions, where Human-Know. denotes human-curated knowledge.
> </details>





### In-depth insights


#### Video-Guided Agents
영상 기반 에이전트는 **인간의 시연을 통해 학습하는 강력한 접근 방식**을 제시합니다.  이를 통해 복잡하고 반복적인 작업을 자동화하고, 특히 사용자 인터페이스(UI)가 동적으로 변화하는 모바일 환경에서 효율적인 작업 수행이 가능해집니다.  **전문가의 수동 코딩 없이 영상 데이터를 통해 에이전트가 지식을 습득**함으로써, **시간 및 비용 효율성을 크게 향상**시킬 수 있습니다.  그러나 영상 처리의 계산 비용,  **무수한 프레임에서 핵심 정보 추출의 어려움**,  그리고 **다양한 UI 변화에 대한 적응성 확보**가 주요 과제로 남아있습니다.  따라서 효율적인 영상 처리 기법,  **핵심 프레임 선택 알고리즘**, 그리고 **강인한 의사결정 메커니즘**의 개발이 향후 연구 방향을 제시합니다. 특히, **다양한 작업과 환경에 대한 일반화 능력을 높이는 연구**가 중요하며,  **실제 모바일 환경에서의 성능 평가 및 신뢰성 확보**는 영상 기반 에이전트의 실용성을 높이는 데 필수적입니다.

#### Mobile Automation
모바일 자동화는 **모바일 기기 사용 편의성 증대**를 목표로 하는 중요한 연구 분야입니다.  본 논문에서는 모바일 자동화의 어려움과 이를 극복하기 위한 혁신적인 방법들을 제시하고 있습니다. **기존의 규칙 기반 접근 방식**은 모바일 환경의 동적인 특성과 다양한 앱 업데이트로 인해 효율성이 떨어지고 유지 보수가 어렵다는 문제점이 있었습니다. 반면, **본 논문에서 제시하는 비디오 기반 접근 방식**은 사용자가 직접 작업 과정을 녹화하여 시스템에 제공함으로써, 다양하고 복잡한 작업들을 효율적으로 학습하고 수행할 수 있게 합니다. 이는 **비용 효율적이며 지속 가능한 솔루션**을 제공합니다. 특히, **복수 에이전트 협업 시스템**을 통해 작업의 정확성과 효율성을 더욱 향상시키는 것이 핵심입니다.  **비디오 처리 및 슬라이딩 윈도우 전략**을 활용하여 계산 비용을 줄이고 효과적인 지도 학습을 실현하며, **심층적 반추 에이전트**를 통해 의사 결정의 정확도를 높이는 등 여러 기술적인 측면에서 뛰어난 성능을 보여줍니다. 결과적으로, 모바일 자동화의 효율성과 정확성을 크게 향상시키는 획기적인 시스템을 제시하고 있다는 점에서 높이 평가할 수 있습니다.  향후 연구에서는 다양한 모바일 환경 및 작업에 대한 적용 가능성을 더욱 확장하고, 시스템의 **로버스트성 및 일반화 능력**을 향상시키는 노력이 필요할 것입니다.

#### Multi-Agent Collab
본 논문에서 제안하는 "멀티 에이전트 협업(Multi-Agent Collab)" 개념은 **모바일 기기 자동화를 위한 새로운 접근 방식**을 제시합니다. 단순히 하나의 인공지능 에이전트가 모든 작업을 수행하는 것이 아니라, **전문화된 여러 에이전트들이 각자의 역할을 수행하며 협력**하여 효율성을 높이는 전략입니다.  **비디오 가이드를 활용**하여 사용자의 작업 과정을 학습하고, 비디오 에이전트는 적절한 프레임 선택을 통해 핵심 정보를 추출하며, 심층 반추 에이전트는 의사결정의 정확성을 높이는 역할을 수행합니다. 이러한 멀티 에이전트 구조는 **복잡한 작업을 보다 효율적으로 처리**하고, **오류를 최소화**하며, **확장성을 높이는 데 기여**할 것으로 기대됩니다.  특히, **비디오 기반 학습은 기존의 수작업 방식보다 효율적**이며, **실제 환경에서 발생하는 다양한 상황 변화에 대한 적응력**을 높입니다. 따라서 "멀티 에이전트 협업"은 모바일 자동화 분야에서 **새로운 가능성**을 제시하는 중요한 연구 결과입니다.  하지만, **비디오 처리의 계산 비용**, **비디오 품질에 대한 의존성**, 그리고 **다양한 작업에 대한 일반화 능력** 등은 앞으로 해결해야 할 과제입니다.

#### Sliding Window
본 논문에서 제안하는 슬라이딩 윈도우 기법은 **장시간의 비디오 입력 처리 과정에서의 계산 비용을 줄이기 위한 효율적인 전략**입니다.  단순히 모든 프레임을 처리하는 대신, **핵심 프레임들만을 선택적으로 추출하여 처리**함으로써, 모델의 처리 부하를 줄이고 속도를 높입니다.  이를 위해 비디오 에이전트는 현재 작업과 관련된 핵심 프레임들을 선택하고,  슬라이딩 윈도우를 통해 시간적 맥락을 유지합니다.  **윈도우 크기의 조정은 모델의 정확도와 효율성 사이에서의 균형을 맞추는 중요한 요소**입니다.  너무 작으면 중요 정보의 손실이 발생하고, 너무 크면 비효율적인 처리가 발생할 수 있기 때문입니다. 따라서, **최적의 윈도우 크기를 결정하는 것은 실험적 분석을 통해 이루어져야 하며,  작업의 복잡도나 비디오의 특성에 따라 달라질 수 있습니다.**  딥 러닝 모델의 성능 향상과 효율적인 연산 사이에서 최적의 균형을 찾기 위한 핵심적인 역할을 수행합니다.  **슬라이딩 윈도우를 통해 긴 비디오 시퀀스를 효율적으로 처리하는 전략**은 Mobile-Agent-V의 핵심적인 강점 중 하나이며, 이를 통해 모델의 실시간 성능 향상에 크게 기여합니다.

#### Deep Reflection
본 논문에서 제시된 "심층적 성찰(Deep Reflection)"은 단순한 오류 수정 메커니즘을 넘어 **의사결정 과정의 정확성과 신뢰도를 높이는 핵심 요소**로 기능합니다.  슬라이딩 윈도우 기법을 통해 비효율적인 정보 처리를 줄이고, **핵심 프레임에 집중**하여 모델의 판단력을 향상시키는 동시에, **장기적인 비디오 맥락을 고려**하여 예측의 정확도를 높입니다.  **심층적 성찰 에이전트는 비디오 내 작업의 일관성을 검증하고, 오류 발생 시 이를 수정**, 최종 결정의 정확성을 보장합니다. 이러한 과정을 통해 단순히 행동만 모방하는 수준을 넘어 **인간의 의사결정 과정을 보다 효과적으로 모방**, 더욱 **정교하고 신뢰할 수 있는 자동화된 모바일 기기 작동**을 가능하게 합니다. 따라서 심층적 성찰은 단순한 보조 기능이 아닌, **Mobile-Agent-V 시스템의 지능과 성능을 좌우하는 핵심 구성 요소**라 할 수 있습니다. 이는 단순한 오류 수정을 넘어, 시스템의 전반적인 성능 향상에 크게 기여하는 **핵심적인 역할**을 수행한다는 것을 의미합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.17110/extracted/6231218/framework.png)

> 🔼 그림 2는 Mobile-Agent-V 프레임워크의 전체 구조를 보여줍니다. 비디오 입력으로부터 키프레임을 추출하고, 슬라이딩 윈도우 기법을 사용하여 관련 키프레임들을 선택합니다. 비디오 에이전트는 윈도우의 위치를 조정하고, 의사결정 에이전트는 선택된 키프레임과 기존의 행동들을 바탕으로 다음 행동을 예측합니다. 심층 반추 에이전트는 예측된 행동을 검증하고 수정하여 최종 행동을 결정합니다. 이러한 과정을 반복하며 작업을 수행합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: The framework of Mobile-Agent-V.
> </details>



![](https://arxiv.org/html/2502.17110/extracted/6231218/CD.png)

> 🔼 이 그림은 비디오 지시사항과 사용자 지시사항이 일치하는 경우(도메인 내)와 일치하지 않는 경우(도메인 간)의 성능을 비교하여 보여줍니다.  Mobile-Agent-V 모델이 비디오 지시사항과 사용자 지시사항이 일치하는 경우(도메인 내) 더 높은 성공률과 완료율, 그리고 더 적은 단계 수를 보이는 것을 보여줍니다. 반면에 지시사항이 일치하지 않는 경우(도메인 간)에는 성능이 다소 저하되는 것을 확인할 수 있습니다. 이는 Mobile-Agent-V 모델이 비디오 데모와 일치하는 작업에 대해서는 더 효과적으로 작동하지만, 작업이 다를 경우에는 일반화 능력이 다소 떨어짐을 시사합니다.  그림은  Mobile-Agent-V의 일반화 능력에 대한 통찰력을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Comparison of video-misaligned instructions and video-aligned instructions. The in-domain means that the video instruction is consistent with the user instruction, and the cross-domain instruction is inconsistent.
> </details>



![](https://arxiv.org/html/2502.17110/extracted/6231218/window.png)

> 🔼 그림 4는 다양한 슬라이딩 윈도우 크기의 영향을 비교 분석한 결과를 보여줍니다.  슬라이딩 윈도우 크기가 성공률(SR), 완료율(CR), 의사결정 정확도(DA) 및 단계 수(Step) 등 다양한 지표에 미치는 영향을 보여주는 여러 그래프가 포함되어 있습니다.  윈도우 크기가 커짐에 따라 성능이 향상되지만 특정 지점을 넘어서면 성능 향상이 감소하거나 성능이 저하되는 것을 확인할 수 있습니다. 이는 적절한 크기의 윈도우를 선택하는 것이 모델 성능에 중요함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Comparison of different sliding window sizes.
> </details>



![](https://arxiv.org/html/2502.17110/extracted/6231218/keyframe.png)

> 🔼 이 그림은 Mobile-Agent-V 모델의 성능에 Keyframe의 질이 미치는 영향을 보여줍니다.  단순히 균일한 간격으로 Keyframe을 추출하는 방법(Uniform Sampling)과 중복된 Keyframe을 제거하고 일정 시간 간격 이상 떨어진 Keyframe만 선택하는 방법(Uniform Sampling + Filtering), 그리고 사람이 직접 중요한 Keyframe을 선택하는 방법(Artificial Sampling) 세 가지 방법을 비교하여, Keyframe의 질이 Mobile-Agent-V 모델의 성능(성공률, 완료율, 결정 정확도, 수행 단계 수)에 어떤 영향을 주는지 보여줍니다.  사람이 직접 선택한 Keyframe을 사용했을 때 가장 좋은 성능을 보이지만, 제안된 방법 또한 좋은 성능을 보임을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Comparison of different keyframe quality.
> </details>



![](https://arxiv.org/html/2502.17110/extracted/6231218/DR.png)

> 🔼 그림 6은 다양한 종류의 지시(instruction)에 대해, 심층 반추 에이전트(Deep Reflection agent)를 사용한 경우와 사용하지 않은 경우의 성능을 비교한 결과를 보여줍니다.  심층 반추 에이전트는 모델의 의사결정 정확도를 높이는 역할을 하며, 특히 복잡한 작업에서 성능 향상에 크게 기여합니다.  단순한 작업에서는 성능 향상이 미미하지만, 복잡한 작업에서는 성공률(SR), 완료율(CR), 의사결정 정확도(DA) 모두 향상되는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Comparison of w/o DR and w/ DR across different instructions.
> </details>



![](https://arxiv.org/html/2502.17110/extracted/6231218/case.jpg)

> 🔼 그림 7은 Mobile-Agent-V의 전체 실행 사례를 보여줍니다. 의사결정 에이전트는 처음에 잘못된 행동을 하지만, 심층적 반성 에이전트는 작업 비디오를 확인하고 장치 상태를 비교하여 행동을 수정합니다.  즉, 의사결정 에이전트가 잘못된 동작을 수행하지만, 심층 반성 에이전트가 비디오 가이드와 현재 장치 상태를 비교 분석하여 오류를 수정하고 올바른 동작을 수행하도록 보정하는 과정을 보여줍니다. 이는 Mobile-Agent-V의 다중 에이전트 협업을 통해 보다 정확하고 효율적인 작업 수행을 가능하게 함을 시각적으로 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: A complete execution case of Mobile-Agent-V. The decision agent initially makes an incorrect action, but the deep-reflection agent verifies the operation video, compares the device state, and corrects the action.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Action | Parameter | Description |
|---|---|---|
| Click | id | The "id" represents the numeric identifier of the detection box to be clicked. |
| Click_text | text | The "text" specifies the target text to be clicked, used only when no detection box or corresponding ID exists at the target location. |
| Scroll | direction | The "direction" can be either "up" or "down," allowing the agent to scroll the screen accordingly. |
| Type | text | The "text" parameter defines the content to be entered into a text field. |
| Back | None | Returns to the previous screen. |
| Home | None | Navigates to the home screen. |
| Done | None | Signals task completion. |{{< /table-caption >}}
> 🔼 이 표는 Mobile-Agent-V 시스템에서 사용되는 행동 공간을 정의합니다.  각 행동(클릭, 스크롤, 입력, 뒤로가기, 홈, 완료)에 대한 매개변수와 설명을 제공하여 시스템의 작동 방식을 명확하게 보여줍니다.  예를 들어, '클릭' 행동은 대상 요소의 ID를 매개변수로 사용하고, '스크롤' 행동은 스크롤 방향을 지정하는 매개변수를 사용합니다. 이 표는 Mobile-Agent-V의 기능을 이해하는 데 필수적입니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Action space definition for Mobile-Agent-V.
> </details>

{{< table-caption >}}
| Knowledge Injection Method | Average Time |
|---|---| 
| Video Recording | <1 min |
| Manually Writing Knowledge | ~5 min |{{< /table-caption >}}
> 🔼 이 표는 비디오 녹화와 수동 문서화에 필요한 시간을 보여줍니다.  비디오 녹화는 평균 1분 미만이 소요되는 반면, 수동 문서화는 약 5분이 걸립니다. 따라서 비디오를 사용하면 시간 소모를 80% 줄이고 수동 작업을 없앨 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Time consumption for video recording and manual documentation.
> </details>

{{< table-caption >}}
| APP | Level | Video Instruction & Video-Aligned User Instruction | Video-Misaligned User Instruction |
|---|---|---|---| 
| Phone | Basic | Help me dial 123. | Help me dial 321. |
|  | Normal | Please turn on the call recording for me. | Please view all call recording for me. |
|  | Advanced | Help me add the mobile number 1234567890 to the blacklist. | Help me add the mobile number 9876543210 to the whitelist. |
| Messages | Basic | Help me set up messages and notifications to be displayed together in Messages. | Help me set up messages and notifications not to be displayed together in Messages. |
|  | Normal | Please send a message to 123456 with text "Hello" | Please send a message to 9876543210 with text "Goodbye". |
|  | Advanced | Send a message to 123456 with my current location information. | Send a message to 987654 with my contact card. |
| Setting | Basic | Help me turn off the auto brightness in Setting. | Help me turn on the auto brightness in Setting. |
|  | Normal | Help me turn off the status bar network speed display. | Help me turn off the status bar NFC display. |
|  | Advanced | Help me open three-finger screenshots. | Help me open three-finger touch and hold. |
| Photo | Basic | Help me turn on the shared albums setting in Photos. | Help me turn off the shared albums setting in Photos. |
|  | Normal | Help me clear recently deleted photos. | Help me restore recently deleted photos. |
|  | Advanced | Help me set up not to record location when taking photos. | Help me set up not to record properties when taking photos. |
| Manager | Basic | Help me turn on the App cleaner reminder in Phone Manager. | Help me turn off the App cleaner reminder in Phone Manager. |
|  | Normal | Help me turn on the automatic phone call for help. | Help me turn on the automatic phone call for help and countdown sound. |
|  | Advanced | Help me clean up QQ’s storage. | Help me clean up WhatsApp’s storage. |
| Recorder | Basic | Help me start recording. | Help me stop recording. |
|  | Normal | Help me change the audio format of my recording. | Help me turn on the cloud recording. |
|  | Advanced | Help me show recently deleted recordings. | Help me show call recordings. |
| Files | Basic | Help me view photos in My Files. | Help me view videos in My Files. |
|  | Normal | Help me create a new tag named "test". | Help me create a new tag named "mobile". |
|  | Advanced | Help me turn on the option to show hidden files. | Help me turn off the option to show hidden files. |
| Clock | Basic | Help me start stopwatch in Clock. | Help me reset stopwatch in Clock. |
|  | Normal | Help me set the gesture to turn off the alarm to swipe up. | Help me set the gesture to turn off the alarm to press button. |
|  | Advanced | Help me delete the last city of the current world clock and add London. | Help me delete the first city of the current world clock and add New York. |
| Weather | Basic | Help me turn on the meteorological alert setting in Weather. | Help me turn off the meteorological alert setting in Weather. |
|  | Normal | Help me turn on the rain reminder. | Help me turn off the rain reminder. |
|  | Advanced | Help me turn on the UV intensity display and view the UV intensity at your current location. | Help me turn on the Sunset display and view the sunset at your current location. |
| Calendar | Basic | Help me turn on fixed time zone setting in Calendar. | Help me turn off fixed time zone setting in Calendar. |
|  | Normal | Help me turn on calendar meeting reminders. | Help me turn on fixed time zone. |
|  | Advanced | Help me subscribe to horoscope and choose Aries. | Help me subscribe to today in history. |{{< /table-caption >}}
> 🔼 이 표는 논문의 실험을 위해 사용된 벤치마크 작업 목록을 보여줍니다. 각 작업은 어플리케이션, 난이도(기본, 일반, 고급), 그리고 비디오 및 비디오와 일치하지 않는 사용자 지침의 두 가지 유형의 지침으로 분류됩니다. 이는 비디오 가이드의 효과를 평가하기 위한 다양한 시나리오를 제공합니다. 각 벤치마크 작업은 모바일 장치에서 특정 작업을 수행하는 데 필요한 단계를 포함합니다. 일반적으로 기본 작업은 간단한 작업을, 일반 작업은 중간 정도의 작업을, 고급 작업은 복잡하고 장치별 지식이 필요한 작업을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Benchmark tasks with different difficulty levels and instruction variations.
> </details>

{{< table-caption >}}
| System |
|---|---| 
| You are a mobile phone operation assistant. Below is a description of this conversation. |
| In the following part, I will upload a large image made up of many screenshots. These screenshots in this image are all from a screen recording of a mobile phone operation. I will tell you the task completed in the screen recording. You need to observe this screen recording. |
| Then, you need to complete a new task, which is related to the task in the screen recording. You need to combine the operation experience provided by the screen recording and gradually complete this task. I will upload the current screenshot of the device. There will be many detection boxes on this screenshot, and there will be a number in the upper left and lower right corners of the detection box. You need to perform operations on the current page. In order to better operate the phone, the following are the operation tools you can use: |
| - Click (id): The "id" is the numeric serial number of the detection box you need to click. |
| - Click_text (text): The "text" is the text you need to click. This is only used when the detection box and the corresponding id do not exist at the location to be clicked. |
| - Scroll (direction): The "direction" selects from "up", "down", "left", and "right". You can scroll the page a certain distance in the specified direction. |
| - Type (text): The "text" is the content you need to enter. |
| - Back: You can use this operation to return to the previous page. |
| - Home: You can use this operation to return to the home page. |
| - Done: You can use this operation when the task is completed. |
| You need to strictly follow the following json output format: |
| "Thought": You need to think about how to perform this operation on the current device based on the operation path in the video, "Operation": Select one from the operation tools, "Summary": Briefly summarize this operation |
| **User during the first operation** |
| The first image is the screen recording, in which the tasks are completed: {I<sub>v</sub>} |
| The second image is the screenshot of the current device, in which you need to complete the following tasks: {I<sub>u</sub>} |
| Note: You need to refer to the operation path in the video more than relying on your own operation experience. Because you may make mistakes. |
| Note: You need to refer to the operation path in the video more than relying on your own operation experience. Because you may make mistakes. |
| <image: V<sub>w</sub>><image: D<sub>i</sub>> |
| **User during subsequent operations** |
| The first image is the screen recording, in which the tasks are completed: {I<sub>v</sub>} |
| The second image is the screenshot of the current device, in which you need to complete the following tasks: {I<sub>u</sub>} |
| Here is your operation history: |
| Step-1: {operation 1} |
| Step-2: {operation 2} |
| … |
| Step-n: {operation n} |
| Note: If the operation history and current device can infer that the task has been completed, use Done. |
| Note: You need to refer to the operation path in the video more than relying on your own operation experience. Because you may make mistakes. |
| <image: V<sub>w</sub>><image: D<sub>i</sub>> |{{< /table-caption >}}
> 🔼 표 5는 의사결정 에이전트에 대한 프롬프트를 보여줍니다.  이 표는 논문에서 제시된 Mobile-Agent-V 프레임워크의 핵심 구성 요소 중 하나인 의사결정 에이전트가 어떻게 동작하는지에 대한 설명을 제공합니다.  프롬프트는 비디오 가이드를 바탕으로 모바일 기기의 작업을 수행하는 단계별 지침을 포함하고 있습니다.  이를 통해 의사결정 에이전트는 비디오에서 보여주는 작업과 현재 장치의 상태를 비교 분석하여 다음 작업을 결정합니다.  프롬프트는 시스템이 현재 작업에 따라 동적으로 조정될 수 있도록 단계별 작업 이력과 함께 비디오 지침, 현재 장치의 스크린샷, 사용자 지침을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: The prompt for decision agent.
> </details>

{{< table-caption >}}
| System | User |
|---|---| 
| You are an expert in mobile phone operation. I will upload two images below. The first image is a keyframe mosaic from an operation video, in which the completed task is "$I_{v}$"; the second image is a screenshot of the current status of the mobile phone. | https://arxiv.org/html/2502.17110/Vw.png https://arxiv.org/html/2502.17110/Di.png |
| On the mobile phone shown in the second image, the task to be completed is: "$I_{u}$". The user will perform the following operation: |  |
| {Operation from decision agent} |  |
| Now please observe whether this operation conforms to the operation path shown in the first image. If it conforms, please output "True", otherwise please modify the operation content according to the above json format. |  |
| The operation should be: |  |
| - Click (id): The "id" is the numeric serial number of the detection box you need to click. |  |
| - Click_text (text): The "text" is the text you need to click. This is only used when the detection box and the corresponding id do not exist at the location to be clicked. |  |
| - Scroll (direction): The "direction" selects from "up" and "down". You can scroll the page a certain distance in the specified direction. |  |
| - Type (text): The "text" is the content you need to enter. |  |
| - Back: You can use this operation to return to the previous page. |  |
| - Home: You can use this operation to return to the home page. |  |
| - Done: You can use this operation when the task is completed. |  |
| Note: If the operation history and current device can infer that the task has been completed, use Done. |  |
| You need to think in the following way: |  |
| 1. Observe the operation of each step in the video (especially frame-3 and frame-4). |  |
| 2. Anchor the position of the current device in the video. |  |
| 3. Complete the current step according to the operation in the video. |  |
| Please output your thought about this step by step before you output your response. |  |{{< /table-caption >}}
> 🔼 본 표는 논문의 깊이 있는 반추 에이전트(Deep-Reflection Agent)에 대한 프롬프트(명령어)를 보여줍니다.  에이전트는 비디오 프롬프트와 장치의 현재 상태를 분석하여 작업을 완료하는 데 도움이 되는 명령어를 생성하는 역할을 합니다.  이 표는 에이전트에게 주어지는 입력값(비디오, 현재 화면, 이전 작업 정보 등)을 정의하고,  에이전트가 어떻게 반응해야 하는지에 대한 지침을 상세히 설명합니다.  이를 통해 깊이 있는 반추 에이전트가 올바른 작업을 수행할 수 있도록 안내하고, 정확도를 높이는 데 기여합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: The prompt for deep-reflection agent.
> </details>

{{< table-caption >}}
| System | User |
|---|---| 
| You are a mobile phone operation assistant. I will provide you with two images. The first image is a long picture of key frames from a mobile phone operation video, which shows a correct operation trajectory to complete the task:  $I_{v}$. The second image is two screenshots before and after an operation from the user. The user want to complete the task: $I_{u}$. Please note that these two images are not necessarily the complete operation trajectories, they may only be part of the continuous operation. | Here are the video and operation: <br> <img src="https://arxiv.org/html/2502.17110/V_w.png"><img src="https://arxiv.org/html/2502.17110/D_i.png"> |
| Although the task shown in the video may not be exactly the same as the task the user needs to complete, there is a strong correlation between the two. So the user is referring to the operation in the video to complete this task. |  |
| Now you need to determine which frame of the video the user is in after the device is operated. You need to use a number to represent it. If the device is in the state between two frames, the previous frame is output. |  |
| If the device is not in any frame of the video, please output the number 0 to indicate an operation error and generate an error cause analysis. |  |
| You need to output in the following json format: |  |
| {"Thought": Your thought of current question, "Frame": a number, "Analysis": If Frame is 0, generate an error cause analysis, otherwise output null, "Need_Back": If Frame is 0, you need to think about how to get back on track. If you need to return to the previous page, please output true. If you need to continue to perform an operation on the current page to get back on track, please output false. If Frame is not 0, please output False directly.} |  |{{< /table-caption >}}
> 🔼 표 7은 논문의 비디오 에이전트(Video Agent)에 대한 프롬프트(명령어)를 보여줍니다.  비디오 에이전트는 사용자의 작업과 비디오의 작업 간의 연관성을 파악하여, 사용자의 현재 상태가 비디오의 어느 프레임에 해당하는지 판별하는 역할을 합니다.  에이전트는 비디오의 프레임 번호를 출력하고(0은 오류를 나타냄), 오류 발생 시 오류 원인 분석 및 문제 해결 방안(이전 페이지로 돌아갈지, 현재 페이지에서 계속 작업할지 여부)을 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 7: The prompt for video agent.
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
{{< /gallery >}}