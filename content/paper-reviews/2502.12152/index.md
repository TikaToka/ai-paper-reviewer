---
title: "Learning Getting-Up Policies for Real-World Humanoid Robots"
summary: "인간 크기의 로봇이 다양한 지형에서 다양한 자세로부터 스스로 일어설 수 있도록 하는 이중 단계 강화 학습 기반 제어기를 개발했습니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["AI Applications", "Robotics", "🏢 University of Illinois Urbana-Champaign",]
showSummary: true
date: 2025-02-17
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.12152 {{< /keyword >}}
{{< keyword icon="writer" >}} Xialin He et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-18 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.12152" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.12152" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/learning-getting-up-policies-for-real-world" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

넘어짐 후 자율 복구는 인간형 로봇의 신뢰할 수 있는 배치를 위한 필수적인 전제 조건입니다. 하지만, 다양한 지형과 로봇이 넘어진 후의 다양한 자세를 고려하면 수동으로 제어기를 설계하는 것은 매우 어렵습니다. 기존의 인간형 로봇 이동 제어 연구는 주로 규칙적인 접촉 패턴을 가진 작업에 초점을 맞추고 있지만, 넘어짐 복구는 복잡한 접촉 패턴이 필요하며, 보상이 희소하다는 어려움이 있습니다.

본 논문에서는 이러한 어려움을 해결하기 위해 커리큘럼 기반 이중 단계 강화 학습 프레임워크인 HUMANUP을 제안합니다. HUMANUP은 첫 번째 단계에서 최소한의 제약 조건하에 최적의 넘어짐 복구 궤적을 발견하고, 두 번째 단계에서 발견된 동작을 실제 환경에 적용 가능하도록 부드럽고 느린 동작으로 다듬습니다. 이를 통해 다양한 지형과 초기 자세에서 견고하고 부드러운 동작을 통해 성공적인 복구가 가능하며, 실제 인간 크기의 로봇에서 학습된 넘어짐 복구 정책을 실제 세계에서 처음으로 성공적으로 시연했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 이중 단계 강화 학습 프레임워크를 사용하여 다양한 지형과 초기 자세에서 인간 크기의 로봇이 스스로 일어설 수 있는 제어기를 개발했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 제안된 방법은 견고하고 부드러운 동작을 통해 다양한 지형과 초기 자세에서 성공적인 복구를 가능하게 합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 본 연구는 실제 로봇에서 학습된 넘어짐 복구 정책의 최초 성공적인 시연을 제시합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**본 논문은 실제 로봇에서 다양한 지형과 자세에서의 자율적인 넘어짐 복구(getting-up)를 위한 학습 기반 제어기 설계에 대한 중요한 진전을 보여줍니다.** 이는 로봇 공학 분야의 중요한 문제이며, 본 연구는 이 문제에 대한 실용적이고 일반화된 해결책을 제공합니다. **특히, 이중 단계 강화 학습 방법론은 견고하고 부드러운 동작을 통해 다양한 지형과 초기 자세에서의 성공적인 복구를 가능하게 합니다.** 또한, 본 연구는 미래 연구를 위한 새로운 방향을 제시하며, 특히 복잡한 접촉 패턴을 포함하는 작업을 위한 학습 기반 제어기 설계에 대한 더 많은 연구가 필요함을 시사합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.12152/x2.png)

> 🔼 그림 1은 본 논문에서 제안하는 HumanUP 방법을 보여줍니다. HumanUP은 사람 모양의 로봇이 넘어진 후 다시 일어서는 동작을 학습하는 2단계 방법론입니다.  Unitree G1 로봇에 직접 적용될 수 있으며, 다양한 바닥(잔디, 돌)과 자세(똑바로 누운 자세, 엎드린 자세)에서도 안정적이고 부드러운 동작으로 일어설 수 있음을 보여줍니다. 그림은 이러한 다양한 상황에서 로봇의 일어서는 모습을 보여주는 여러 이미지로 구성되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: HumanUP provides a simple and general two-stage training method for humanoid getting-up tasks, which can be directly deployed on Unitree G1 humanoid robots [70]. Our policies showcase robust and smooth behavior that can get up from diverse lying postures (both supine and prone) on varied terrains such as grass slopes and stone tile.
> </details>





{{< table-caption >}}
Sim2Real|Task|Smoothness|Safety
---|---|---|---|---
Getting Up from Supine Poses||Success ↑|Task Metric ↑|Action Jitter ↓|DoF Pos Jitter ↓|Energy ↓|$\mathcal{S}^{\text{Torque}}_{0.8,0.5}\uparrow$|$\mathcal{S}^{\text{DoF}}_{0.8,0.5}\uparrow$
Tao et al. [65]|✗|92.62 ± 0.54|**1.27 ± 0.00**|5.39 ± 0.01|0.48 ± 0.00|650.19 ± 1.26|0.72 ± 3.10e-4|0.73 ± 1.39e-4
HumanUP w/o Stage II|✗|24.82 ± 0.25|0.83 ± 0.00|13.70 ± 0.18|0.71 ± 0.00|1311.22 ± 8.57|0.57 ± 1.45e-3|0.67 ± 5.56e-4
HumanUP w/o Full URDF|✗|93.95 ± 0.24|1.22 ± 0.00|0.71 ± 0.00|0.11 ± 0.00|104.14 ± 0.57|0.92 ± 8.36e-5|0.77 ± 9.40e-5
HumanUP w/o Posture Rand.|✓|65.39 ± 0.50|1.09 ± 0.04|0.75 ± 0.05|0.15 ± 0.03|141.52 ± 0.61|0.91 ± 2.32e-4|0.74 ± 7.24e-5
HumanUP w/ Hard Symmetry|✓|84.56 ± 0.11|1.23 ± 0.00|0.97 ± 0.01|0.22 ± 0.00|182.39 ± 0.22|0.89 ± 1.70e-5|0.78 ± 8.81e-5
HumanUP|✓|**95.34 ± 0.12**|1.24 ± 0.00|**0.56 ± 0.01**|**0.10 ± 0.00**|**91.74 ± 0.33**|**0.93 ± 1.55e-5**|**0.78 ± 4.15e-5**
Rolling Over from Prone to Supine Poses||Success ↑|Task Metric ↑|Action Jitter ↓|DoF Pos Jitter ↓|Energy ↓|$\mathcal{S}^{\text{Torque}}_{0.8,0.5}\uparrow$|$\mathcal{S}^{\text{DoF}}_{0.8,0.5}\uparrow$
HumanUP w/o Stage II|✗|43.48 ± 0.41|0.91 ± 0.00|3.32 ± 0.31|0.40 ± 0.05|1684.66 ± 0.43|0.65 ± 6.28e-4|0.72 ± 7.18e-5
HumanUP w/o Full URDF|✗|87.73 ± 0.33|0.97 ± 0.00|0.33 ± 0.00|0.07 ± 0.00|59.01 ± 0.05|0.93 ± 7.91e-5|0.75 ± 9.98e-5
HumanUP w/o Posture Rand.|✓|37.27 ± 1.14|0.77 ± 0.01|0.77 ± 0.01|0.15 ± 0.00|234.46 ± 1.00|0.90 ± 4.98e-4|0.72 ± 2.04e-4
HumanUP w/ Hard Symmetry|✓|75.53 ± 0.25|0.60 ± 0.00|**0.31 ± 0.00**|0.09 ± 0.00|84.95 ± 0.33|0.95 ± 3.12e-5|0.76 ± 2.49e-5
HumanUP|✓|**94.40 ± 0.21**|**0.99 ± 0.00**|0.31 ± 0.00|**0.06 ± 0.00**|**57.08 ± 0.20**|**0.95 ± 1.51e-4**|**0.76 ± 2.48e-5**
Getting Up from Prone Poses||Success ↑|Task Metric ↑|Action Jitter ↓|DoF Pos Jitter ↓|Energy ↓|$\mathcal{S}^{\text{Torque}}_{0.8,0.5}\uparrow$|$\mathcal{S}^{\text{DoF}}_{0.8,0.5}\uparrow$
Tao et al. [65]†|✗|**98.99 ± 0.20**|**1.26 ± 0.00**|11.73 ± 0.01|0.76 ± 0.00|1015.27 ± 0.65|0.67 ± 2.24e-4|0.68 ± 6.41e-5
HumanUP w/o Stage II|✗|27.59 ± 0.28|1.23 ± 0.00|5.56 ± 0.36|0.45 ± 0.04|1213.07 ± 5.56|0.67 ± 4.71e-3|0.71 ± 2.17e-3
HumanUP w/o Full URDF|✗|89.59 ± 0.29|0.82 ± 0.00|0.44 ± 0.01|0.08 ± 0.00|77.61 ± 0.86|0.92 ± 2.88e-5|0.75 ± 3.19e-5
HumanUP w/o Posture Rand.|✓|30.25 ± 0.24|0.87 ± 0.02|1.05 ± 0.01|0.15 ± 0.00|208.23 ± 1.27|0.90 ± 3.06e-4|0.73 ± 1.01e-4
HumanUP w/ Hard Symmetry|✓|67.12 ± 0.34|1.09 ± 0.01|0.94 ± 0.01|0.23 ± 0.01|196.17 ± 3.68|0.91 ± 3.54e-5|0.76 ± 4.45e-5
HumanUP|✓|92.10 ± 0.46|1.24 ± 0.00|**0.39 ± 0.01**|**0.07 ± 0.00**|**69.98 ± 0.45**|**0.94 ± 1.82e-4**|**0.77 ± 3.70e-4**{{< /table-caption >}}

> 🔼 표 I은 시뮬레이션 결과를 보여줍니다. HumanUP과 여러 기준 모델을 비교하여 만든 자세 집합 𝒫 (supine 및 prone)의 테스트 분할에 대한 결과를 보여줍니다. HumanUP을 제외한 모든 방법은 훈련 분할 데이터 𝒫에서 훈련되었으며, HumanUP의 경우 두 단계 학습이 아닌, 자세 무작위화를 하지 않은 방법도 포함되어 있습니다. HumanUP은 연속적으로 작업 1, 2, 3을 해결합니다. HumanUP의 두 단계 학습이 없는 기준 모델은 작업을 해결하지 못하므로 결과에 포함되지 않았습니다. Tao 등의 방법은 롤오버 정책이 없으므로 작업 3을 직접적으로 해결하도록 훈련되었습니다. Sim2Real 열은 해당 방법이 실제 환경으로 성공적으로 이전될 수 있는지 여부를 나타냅니다. 평활도 및 안전성 지표가 합리적인 실제 환경에서 모든 방법을 테스트했으며, 배포에 실패한 경우 Sim2Real은 거짓입니다. 섹션 V-C에서 지표를 소개합니다.
> <details>
> <summary>read the caption</summary>
> TABLE I: Simulation results. We compare HumanUP with several baselines on the held-out split of our curated posture set 𝒫supinesubscript𝒫supine\mathcal{P}_{\text{supine}}caligraphic_P start_POSTSUBSCRIPT supine end_POSTSUBSCRIPT and 𝒫pronesubscript𝒫prone\mathcal{P}_{\text{prone}}caligraphic_P start_POSTSUBSCRIPT prone end_POSTSUBSCRIPT using full URDF. All methods are trained on the training split of our posture set 𝒫𝒫\mathcal{P}caligraphic_P, except for methods HumanUP w/o Stage II and w/o posture randomization. HumanUP solves task ❸ by solving task ❷ and task ❶ consecutively. We do not include the results of baseline 6 (HumanUP w/o Two-Stage Learning) as it cannot solve the task. † Tao et al. [65] is trained to directly solving task ❸ as it does not have a rolling over policy. Sim2Real column indicates whether the method can transfer to the real world successfully. We tested all methods in the real world for which the Smoothness and Safety metrics are reasonable, and Sim2Real is false if deployment wasn’t successful. Metrics are introduced in Section V-C.
> </details>





### In-depth insights


#### Sim-to-Real Getup
본 논문의 "Sim-to-Real Getup" 부분은 시뮬레이션 환경에서 학습된 로봇의 넘어짐 회복 정책을 실제 로봇에 적용하는 과정을 다룹니다.  **가장 큰 도전 과제는 시뮬레이션과 실제 환경 간의 차이**로, 시뮬레이션에서는 완벽한 물리적 모델과 제어가 가능하지만 실제 로봇은 마찰, 불규칙한 지면, 센서 노이즈 등 예측 불가능한 요소에 영향을 받습니다.  이를 해결하기 위해 **두 단계 학습 전략**을 제시합니다. 1단계는 제약 없이 최적의 움직임을 발견하는 것이고, 2단계는 1단계에서 발견된 동작을 실제 로봇에 적용 가능하도록 매끄럽고 안전하게 다듬는 것입니다.  **단계별 커리큘럼 학습**을 통해 시뮬레이션 환경의 단순화된 모델부터 시작하여 점차 복잡한 환경으로 전환하며, 제어 정밀도 또한 단계적으로 높여 실제 로봇에 대한 일반화 성능을 향상시키는 전략을 사용합니다.  **실제 로봇 실험**을 통해 다양한 지형에서 안정적인 넘어짐 회복 성능을 검증했으며, 기존의 수동 제어 방식보다 우수한 성능을 보였습니다.  **하지만, 여전히 시뮬레이션과 실제 환경 간의 완벽한 일치는 어렵기 때문에**,  좀 더 강건하고 일반화된 정책을 개발하기 위한 추가 연구가 필요합니다.

#### Two-Stage RL
본 논문에서 제안하는 **두 단계 강화 학습 (Two-Stage RL)**은 휴머노이드 로봇의 자세 복귀 문제에 대한 효과적인 해결책을 제시합니다. 1단계는 **제약 없는 탐색 단계**로, 부드러움이나 속도 제한 없이 최적의 자세 복귀 동작을 발견하는 데 집중합니다. 반면 2단계는 **배포 가능한 정책 단계**로, 1단계에서 발견된 동작을 부드럽고 느리게, 다양한 지형과 초기 자세에서도 견고하게 수행하도록 개선합니다. **단계적 접근 방식**을 통해 복잡한 접촉 패턴과 희소 보상 문제를 효과적으로 해결합니다.  **시뮬레이션에서 실제 환경으로 전이**를 위한 심도 있는 커리큘럼(curriculum)을 통해 각 단계의 정책을 개선하는 점이 특징이며, **단계적 커리큘럼**을 통하여 학습의 효율성을 높이고 시뮬레이션과 실제 환경 간의 차이를 최소화합니다. 이는 **단순한 시뮬레이션-실제 환경 전이 (Sim2Real)** 접근 방식보다 훨씬 뛰어난 성능을 보이며, 실제 로봇에서 다양한 자세와 지형에서 견고한 자세 복귀 성능을 달성합니다. **다양한 시뮬레이션 및 실제 실험**을 통해 이 방법의 효과성을 입증했습니다.

#### Curriculum Learning
본 논문에서 제시된 커리큘럼 학습 방법은 **단순히 어려운 과제를 쉬운 과제부터 점진적으로 학습시키는 것**을 넘어, **두 가지 단계를 통해 로봇의 동작을 단계적으로 개선**하는 전략적인 접근 방식을 보여줍니다.  1단계에서는 제약 조건 없이 최적의 동작을 발견하는 데 초점을 맞추고, 2단계에서는 발견된 동작을 실제 환경에 적용 가능하도록 부드럽고 안전하게 만드는 데 집중합니다. 이러한 단계적 접근 방식은 복잡한 접촉 패턴을 포함하는 일어서기 과제에서 **안정적이고 일반화된 정책을 학습**하는 데 중요한 역할을 합니다. 특히,  충돌 메쉬 단순화, 초기 자세 무작위화, 제어 규제 강화 등의 커리큘럼을 통해 **시뮬레이션에서 실제 로봇으로의 전이를 원활하게** 합니다. 이러한 방법은 **단순한 시뮬레이션 환경을 넘어 다양한 지형에서의 안정적인 동작을 가능하게** 하여 실제 로봇에 대한 적용 가능성을 높입니다.  결론적으로, 본 논문의 커리큘럼 학습은 단순한 단계적 학습이 아닌, **문제 해결의 효율성과 일반화 성능을 모두 고려한 전략적인 접근 방식**임을 보여줍니다.

#### Real-World Robustness
본 논문에서 제시된 휴머노이드 로봇의 낙상 복구 정책의 현실 세계 적용 가능성을 평가하는 "실세계 강건성"에 대한 심층적인 분석이 필요합니다. **시뮬레이션 환경에서의 성공적인 결과는 실제 로봇의 복잡하고 예측 불가능한 환경에서의 성능을 보장하지 않습니다.** 따라서, 다양한 지형(잔디, 눈, 돌 등)과 초기 자세에서의 실제 로봇 실험 결과를 통해 정책의 강건성을 평가해야 합니다.  **실제 로봇 실험에서의 성공률, 안정성, 에너지 효율성 등을 측정하여 시뮬레이션 결과와 비교 분석하는 것이 중요합니다.** 또한, **예상치 못한 상황이나 장애물에 대한 로봇의 반응 및 복구 능력을 평가**하여 정책의 일반화 능력을 검증해야 합니다.  **실제 환경에서의 추가적인 테스트와 분석을 통해 시뮬레이션과의 차이점을 파악하고, 정책 개선 방향을 제시**하여 더욱 강건하고 신뢰할 수 있는 낙상 복구 정책을 개발하는 데 기여해야 할 것입니다.  마지막으로, **에너지 효율성 및 안전성을 고려한 제어 알고리즘의 설계 및 평가**도 실세계 강건성 평가의 중요한 부분입니다.

#### Future of Fall Recovery
낙상 복구의 미래는 **로봇 공학의 혁신과 인공지능의 발전에 크게 의존**할 것입니다.  보다 강력하고 정교한 센서와 제어 시스템을 통해 로봇은 다양한 지형과 예측 불가능한 낙상 상황에 더욱 효과적으로 대처할 수 있게 될 것입니다. 특히, **심층 강화 학습(Deep Reinforcement Learning)**과 같은 기계 학습 기술을 활용하여 로봇이 스스로 최적의 낙상 복구 전략을 학습하고, 다양한 환경에 적응하는 능력을 향상시키는 것이 중요합니다.  **시뮬레이션 기반 학습**을 통해 실제 환경에서의 위험을 최소화하면서 효율적인 훈련이 가능해질 것입니다. 더 나아가, **인간의 움직임을 모방하는 기술**을 통해 더 자연스럽고 안전한 복구 동작을 구현하고, **로봇과 인간의 협업**을 통해 복구 과정을 지원하는 시스템 개발도 중요한 연구 방향이 될 것입니다. 이러한 기술 발전은 재난 구조, 의료 지원 등 다양한 분야에서 로봇의 활용도를 높이고 인간의 안전을 보장하는 데 크게 기여할 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.12152/x3.png)

> 🔼 그림 2는 HumanUP 시스템의 개요를 보여줍니다. HumanUP은 시뮬레이션에서 두 단계의 강화 학습을 통해 훈련된 후 실제 세계에 직접 적용되는 낙상 회복 정책입니다. 1단계에서는 최소한의 구현 제약 조건 하에 최적의 낙상 회복 궤적을 찾는 발견 정책(f)을 학습합니다. 2단계에서는 1단계에서 발견된 궤적을 다양한 지형과 초기 자세에서 강력한 제어 규제 하에 느리게 추적하는 학습을 통해 배포 가능하고 견고하며 일반화 가능한 정책(π)으로 변환합니다. 두 단계 학습 과정은 커리큘럼을 유도합니다. 1단계는 단순한 충돌 형상, 동일한 초기 자세, 약한 규제, 지형 변화 없이 더 쉬운 환경에서 동작 발견에 중점을 두는 반면, 2단계는 학습된 동작을 배포 가능하고 일반화할 수 있도록 만드는 작업을 해결합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: HumanUP system overview. Our getting-up policy (Section III-A) is trained in simulation using two-stage RL training, after which it is directly deployed in the real world. (a) Stage I (Section III-B1) learns a discovery policy f𝑓fitalic_f that figures out a getting-up trajectory with minimal deployment constraints. (b) Stage II (Section III-B2) converts the trajectory discovered by Stage I into a policy π𝜋\piitalic_π that is deployable, robust, and generalizable. This policy π𝜋\piitalic_π is trained by learning to track a slowed down version of the discovered trajectory under strong control regularization on varied terrains and from varied initial poses. (c) The two-stage training induces a curriculum (Section III-C). Stage I targets motion discovery in easier settings (simpler collision geometry, same starting poses, weak regularization, no variations in terrain), while Stage II solves the task of making the learned motion deployable and generalizable.
> </details>



![](https://arxiv.org/html/2502.12152/x4.png)

> 🔼 그림 3은 실제 환경에서 HumanUP의 성능을 다양한 표면 특성(인공 및 자연 표면 포함)을 가진 여러 설정에서 평가한 결과를 보여줍니다. 평가에는 거칠기(거친 콘크리트에서 미끄러운 눈까지), 요철(평평한 콘크리트에서 타일까지), 지면의 탄성(완전히 단단한 콘크리트에서 습한 진흙탕 잔디까지), 경사(평평한 곳에서 약 10도까지) 등 폭넓은 범위가 포함됩니다. HumanUP은 기본 제공되는 G1 로봇의 기립 제어기와 자세 무작위화(PR)를 사용하지 않은 HumanUP과 비교됩니다. HumanUP은 더 일관되게 성공(78.3% 대 41.7%)하며, G1 제어기가 해결할 수 없는 지형도 해결할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Real-world results. We evaluate HumanUP (ours) in several real-world setups that span diverse surface properties, including both man-made and natural surfaces, and cover a wide range of roughness (rough concrete to slippery snow), bumpiness (flat concrete to tiles), ground compliance (completely firm concrete to being swampy muddy grass), and slope (flat to about 10∘superscript1010^{\circ}10 start_POSTSUPERSCRIPT ∘ end_POSTSUPERSCRIPT). We compare HumanUP with G1’s built-in getting-up controller and our HumanUP w/o posture randomization (PR). HumanUP succeeds more consistently (78.3% vs 41.7%) and can solve terrains that the G1’s controller can’t.
> </details>



![](https://arxiv.org/html/2502.12152/x5.png)

> 🔼 그림 4는 강화 학습 과정에서 로봇의 자세 변화를 보여주는 학습 곡선 그래프입니다. (a)는 로봇의 몸통 높이 변화를, (b)는 중력 방향에 대한 로봇의 수직도를 나타냅니다. 몸통 높이는 로봇이 몸을 들어올릴 수 있는지 여부를 나타내는 지표이고, 중력에 대한 수직도는 로봇이 얼마나 균형 있게 서 있는지를 나타내는 지표입니다. 두 그래프 모두 시뮬레이션 샘플링 단계의 정규화된 수치를 사용하여 비교 분석에 용이하도록 하였습니다.  총 50억 번의 시뮬레이션 샘플링 단계가 수행되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Learning curve. (a) Termination height of the torso, indicating whether the robot can lift the body. (b) Body uprightness, computed as the projected gravity on the z𝑧zitalic_z-axis, normalized to [0,1]01[0,1][ 0 , 1 ] for better comparison. The overall number of simulation sampling steps is about 5B, normalized to [0,1]01[0,1][ 0 , 1 ].
> </details>



![](https://arxiv.org/html/2502.12152/x6.png)

> 🔼 그림 5는 HumanUP과 G1 컨트롤러의 기립 동작 비교를 보여줍니다. G1 컨트롤러는 세 단계로 나뉜 수동 제작 모션 경로를 사용하는 반면, HumanUP은 연속적이고 효율적인 전신 기립 동작을 학습합니다. HumanUP을 사용하면 휴머노이드가 6초 안에 일어설 수 있는데, 이는 G1 컨트롤러의 11초에 비해 절반의 시간입니다. (a), (b), (c)는 각각 상체, 하체, 허리의 평균 모터 온도를 기록한 것입니다. G1 컨트롤러의 기본 실행은 팔 모터가 과열되는 반면, HumanUP 정책은 더 큰 토크 제한(83N 대 25N)을 가진 다리 모터를 더 많이 사용하므로 더 많은 하중을 감당할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Getting up comparison with G1 controller. G1 controller uses a handcrafted motion trajectory, which can be divided into three phases, while our HumanUP learns a continuous and more efficient whole-body getting-up motion. Our HumanUP enables the humanoid to get up within 6 seconds, half of the G1 controller’s 11 seconds of control. (a), (b), and (c) record the corresponding mean motor temperature of the upper body, lower body, and waist, respectively. G1’s default controller’s execution causes the arm motors to heat up significantly, whereas our policy makes more use of the leg motors that are larger (higher torque limit of 83N as opposed to 25N for the arm motors) and thus able to take more load.
> </details>



![](https://arxiv.org/html/2502.12152/x7.png)

> 🔼 그림 6은 잔디 경사면과 눈밭에서의 실패 모드를 보여주는 정성적 예시입니다. G1 컨트롤러는 경사진 잔디에서 스쿼트 자세를 취할 수 없고, 미끄러운 눈에서는 미끄러집니다. HumanUP 정책은 경사면과 눈밭 모두에서 부분적으로 일어설 수 있지만, 경사면에서는 불안정한 발 위치 때문에, 눈에서는 미끄러짐 때문에 넘어집니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Qualitative examples of failure modes on grass slope and snow field. G1 controller isn’t able to squat on the sloping grass and slips on the slow. HumanUP policy is able to partially get up on both the slope and the snow but falls due to unstable feet placement on the slope and slippage on the snow.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
Term | Expression | Weight
---|---|---
Penalty: |  |  
Torque limits | \mathds{1}({\boldsymbol{\tau}_{t}\notin[\boldsymbol{\tau}_{\min}, \boldsymbol{\tau}_{\max}]}) | -0.1
DoF position limits | \mathds{1}({\boldsymbol{d}_{t}\notin[\boldsymbol{q}_{\min},\boldsymbol{q}_{\max}]}) | -5
Energy | \lVert\ \boldsymbol{\tau}\odot\dot{\mathbf{q}}\rVert | -1e-4
Termination | \mathds{1}_{\text{termination}} | -500
Regularization: |  |  
DoF acceleration | \lVert{\boldsymbol{\ddot{d}}_{t}}\rVert_{2} | -1e-7
DoF velocity | \lVert{\boldsymbol{\dot{d}}_{t}}\rVert_{2}^{2} | -1e-4
Action rate | \lVert\boldsymbol{a}_{t}\rVert_{2}^{2} | -0.1
Torque | \lVert{\boldsymbol{\tau}_{t}}\rVert | -6e-7
DoF position error | \mathds{1}(h_{\text{base}}\geq 0.8)\cdot\exp\left(-0.05\|{\boldsymbol{d}_{t}} - {\boldsymbol{d}_{t}}^{\text{default}}|\right) | -0.75
Angular velocity | \lVert\omega^{2}\rVert | -0.1
Base velocity | \lVert\boldsymbol{v}^{2}\rVert | -0.1
Foot slip | \mathds{1}(\boldsymbol{F}^{\text{feet}}_{z}>5.0)\cdot\sqrt{\|\boldsymbol{v}_{z}^{\text{feet}}\|} | -1
Getting-Up Task Rewards: |  |  
Base height exp | \exp(\boldsymbol{h}^{base})-1 | 5
Head height exp | \exp(\boldsymbol{h}^{head})-1 | 5
Δ base height | \mathds{1}(\boldsymbol{h}_{t}^{base}>\boldsymbol{h}^{base}_{t-1}) | 1
Feet contact forces reward | \mathds{1}(\lVert\boldsymbol{F}_{t}^{feet}\rVert>\lVert\boldsymbol{F}^{\text{feet}}_{t-1})\rVert | 1
Standing on feet reward | \mathds{1}\big{(}(\lVert\boldsymbol{F}^{\text{feet}}\rVert>0\big{)}\&\big{(}\boldsymbol{h}^{\text{feet}}<0.2\big{)}\big{)} | 2.5
Body upright reward | \exp(-\mathbf{g}^{\text{base}}_{z}) | 0.25
Feet height reward | \exp(-10\cdot\boldsymbol{h}^{\text{feet}}) | 2.5
Feet distance reward | \frac{1}{2}\Big{(}\exp(-100\left|\max(\boldsymbol{d}_{\text{feet}}-\boldsymbol{d}_{\min},-0.5)\right|) + \exp(-100\left|\max(\boldsymbol{d}_{\text{feet}}-\boldsymbol{d}_{\max},0)\right|)\Big{)} | 2
Foot orientation | \sqrt{\lVert G_{xy}^{\text{feet}}\rVert} | -0.5
Soft body symmetry penalty | \left\|\mathbf{a}_{\text{left}}-\mathbf{a}_{\text{right}}\right\| | -1.0
Soft waist symmetry penalty | \left\|\mathbf{a}^{\text{waist}}\right\| | -1.0
Rolling-Over Task Rewards: |  |  
Base Gravity Exp | \frac{1}{2}\Big{(}\exp\big{(}-0.01(1-\cos\theta_{\text{left}})\big{)} + \exp\big{(}-0.01(1-\cos\theta_{\text{right}})\big{)}\Big{)}, \cos\theta=\frac{\mathbf{g}^{\text{knee}}\cdot\mathbf{g}_{\text{target}}}{\|\mathbf{g}^{\text{base}}\|\|\mathbf{g}_{\text{base}}\|} | 8
Knee Gravity Exp | \frac{1}{2}\Big{(}\exp\big{(}-0.01(1-\cos\theta_{\text{left}})\big{)} + \exp\big{(}-0.01(1-\cos\theta_{\text{right}})\big{)}\Big{)}, \cos\theta=\frac{\mathbf{g}^{\text{knee}}\cdot\mathbf{g}_{\text{target}}}{\|\mathbf{g}^{\text{base}}\|\|\mathbf{g}_{\text{base}}\|} | 8
Feet distance reward | \frac{1}{2}\Big{(}\exp(-100\left|\max(\boldsymbol{d}_{\text{feet}}-\boldsymbol{d}_{\min},-0.5)\right|) + \exp(-100\left|\max(\boldsymbol{d}_{\text{feet}}-\boldsymbol{d}_{\max},0)\right|)\Big{)} | 2
Feet height reward | \exp(-10\cdot\boldsymbol{h}^{\text{feet}}) | 2.5{{< /table-caption >}}
> 🔼 표 II는 논문의 Stage I에서 사용된 보상 구성 요소와 가중치를 보여줍니다.  벌점 보상은 시뮬레이션에서 실제 환경으로 전이할 때 원치 않는 동작을 방지하고, 규제는 동작을 개선하며, 작업 보상은 성공적인 일어서기 또는 구르기를 보장합니다.  좀 더 자세히 설명하자면,  벌점 보상은 토크 제한, 관절 위치 제한, 에너지 소비 등을 고려하여 로봇의 안전성과 효율성을 높입니다.  규제 보상은 부드러운 움직임을 유도하고,  작업 보상은 로봇이 목표 자세(일어서기 또는 구르기)에 도달했을 때 보상을 제공하여 학습 효율을 높입니다.
> <details>
> <summary>read the caption</summary>
> TABLE II: Reward components and weights in Stage I. Penalty rewards prevent undesired behaviors for sim-to-real transfer, regularization refines motion, and task rewards ensure successful getting up or rolling over.
> </details>

{{< table-caption >}}
Term | Expression | Weight
---|---|---
**Penalty:** |  | 
Torque limits |  \mathds{1}(\boldsymbol{\tau}_{t}\notin[\boldsymbol{\tau}_{min}, \boldsymbol{\tau}_{max}]) | -5
Ankle torque limits | \mathds{1}(\boldsymbol{\tau}_{t}^{ankle}\notin[\boldsymbol{\tau}^{ankle}_{min},\boldsymbol{\tau}^{ankle}_{max}]) | -0.01
Upper torque limits | \mathds{1}(\boldsymbol{\tau}_{t}^{upper}\notin[\boldsymbol{\tau}^{upper}_{min},\boldsymbol{\tau}^{upper}_{max}]) | -0.01
DoF position limits | \mathds{1}(\boldsymbol{d}_{t}\notin[\boldsymbol{q}_{min},\boldsymbol{q}_{max}]) | -5
Ankle DoF position limits | \mathds{1}(\boldsymbol{d}_{t}^{ankle}\notin[\boldsymbol{q}^{ankle}_{min},\boldsymbol{q}^{ankle}_{max}]) | -5
Upper DoF position limits | \mathds{1}(\boldsymbol{d}_{t}^{upper}\notin[\boldsymbol{q}^{upper}_{min},\boldsymbol{q}^{upper}_{max}]) | -5
Energy | \lVert \boldsymbol{\tau}\odot\dot{\mathbf{q}}\rVert | -1e-4
Termination | \mathds{1}_{termination} | -50
**Regularization:** |  | 
DoF acceleration | \lVert\boldsymbol{\ddot{d}}_{t}\rVert_{2} | -1e-7
DoF velocity | \lVert\boldsymbol{\dot{d}}_{t}\rVert_{2}^{2} | -1e-3
Action rate | \lVert\boldsymbol{a}_{t}\rVert_{2}^{2} | -0.1
Torque | \lVert\boldsymbol{\tau}_{t}\rVert | -0.003
Ankle torque | \lVert\boldsymbol{\tau}_{t}^{ankle}\rVert | -6e-7
Upper torque | \lVert\boldsymbol{\tau}_{t}^{upper}\rVert | -6e-7
Angular velocity | \lVert\omega^{2}\rVert | -0.1
Base velocity | \lVert\boldsymbol{v}^{2}\rVert | -0.1
**Tracking Rewards:** |  | 
Tracking DoF position | \exp\left(-\frac{(\boldsymbol{d}_{t}-\boldsymbol{d}_{t}^{target})^{2}}{4}\right) | 8
Feet distance reward | \frac{1}{2}\Big{(}\exp(-100\left|\max(\boldsymbol{d}_{feet}-\boldsymbol{d}_{min},-0.5)\right|) +\exp(-100\left|\max(\boldsymbol{d}_{feet}-\boldsymbol{d}_{max},0)\right|)\Big{)} | 2
Foot orientation | \sqrt{\lVert\mathbf{g}_{xy}^{feet}\rVert} | -0.5{{< /table-caption >}}
> 🔼 표 III은 강화 학습 기반의 휴머노이드 로봇 일어서기 정책 학습의 두 번째 단계(Stage II)에서 사용되는 보상 함수의 구성 요소와 가중치를 보여줍니다.  Sim-to-Real 전이를 위한 페널티 보상은 원치 않는 동작을 방지하고,  규제(Regularization) 보상은 동작의 부드러움을 향상시키며,  목표 달성 보상은 실시간으로 전체 신체의 움직임을 정확하게 추적하는 것을 보장합니다. 각 항목의 수식과 가중치가 상세히 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> TABLE III: Reward components and weights in Stage II. Penalty rewards prevent undesired behaviors for sim-to-real transfer, regularization refines motion, and task rewards ensure successful whole-body tracking in real time.
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