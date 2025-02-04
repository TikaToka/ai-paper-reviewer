---
title: "DINO-WM: World Models on Pre-trained Visual Features enable Zero-shot Planning"
summary: "DINO-WM: 사전 훈련된 시각적 특징을 활용한 제로샷 계획 가능한 세계 모델"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Machine Learning", "Reinforcement Learning", "🏢 Meta AI",]
showSummary: true
date: 2024-11-07
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2411.04983 {{< /keyword >}}
{{< keyword icon="writer" >}} Gaoyue Zhou et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-03 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2411.04983" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2411.04983" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/dino-wm-world-models-on-pre-trained-visual" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 세계 모델 학습 방법은 특정 작업에 대해 온라인으로 정책을 학습해야 하며, 이는 일반화 및 효율성 측면에서 어려움을 야기합니다.  본 논문에서는 이러한 문제를 해결하기 위해 오프라인으로 수집된 데이터셋을 기반으로 사전 훈련된 DINOv2 시각적 특징을 활용하여 세계 모델을 학습하는 새로운 방법을 제시합니다.  이는  **작업에 대한 사전 지식 없이도 새로운 작업을 수행할 수 있는 제로샷 계획**을 가능하게 합니다.

본 논문에서 제안하는 DINO-WM은 시각적 정보를 재구성하지 않고, 사전 훈련된 시각적 특징을 바탕으로 미래의 시각적 패치 특징을 예측함으로써 세계 모델을 학습합니다.  이를 통해 목표 지점까지 도달하는 행동 시퀀스를 최적화하고, **다양한 작업에 적용 가능한 일반적인 계획**을 가능하게 합니다.  실험 결과, DINO-WM은 전문가 데모, 보상 모델링 또는 사전 학습된 역 모델 없이도 여러 환경에서 제로샷으로 성공적인 행동 계획을 수행함을 보여줍니다.  **이는 기존 최첨단 기술을 능가하는 성능**을 의미합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 사전 훈련된 DINOv2 시각적 특징을 활용하여 시각적 역동성을 모델링하는 새로운 방법 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 오프라인 데이터셋으로부터 제로샷 행동 계획 수행 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 다양한 환경에서 우수한 성능을 보이며 기존 최첨단 기술 능가 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **영상 기반 제어 분야의 난제를 해결**하고 **제로샷 계획의 가능성**을 보여주는 중요한 연구입니다.  기존의 접근 방식들이 가지는 일반화 및 효율성 문제를 극복하는 새로운 방법론을 제시하여, **다양한 로봇 작업에 적용 가능한 범용적인 세계 모델 개발**이라는 중요한 발전을 이루었습니다.  이러한 발견은 **향후 로보틱스 및 인공지능 연구**에 큰 영향을 미칠 것으로 예상되며, **새로운 연구 방향**을 제시하여 관련 분야 연구자들에게 귀중한 통찰력을 제공합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2411.04983/extracted/6170539/figures/intro.png)

> 🔼 그림 1은 제시된 DINO-WM 방법을 보여줍니다. (a)에서는 DINOv2를 사전 훈련된 이미지 프레임의 임베딩을 사용하여 시각적 모델을 훈련하는 과정을 보여줍니다. 훈련된 모델은 (b)에서 설명하는 바와 같이, 목표 관측값 oT를 받아 모델 예측 제어를 사용하여 DINO-WM을 통해 에이전트의 행동을 직접 최적화합니다.  (c)는 사전 훈련된 임베딩을 사용함으로써 기존 최첨단 월드 모델들에 비해 성능이 크게 향상됨을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: We present DINO-WM, a method for training visual models by using pretrained DINOv2 embeddings of image frames (a). Once trained, given a target observation oTsubscript𝑜𝑇o_{T}italic_o start_POSTSUBSCRIPT italic_T end_POSTSUBSCRIPT, we can directly optimize agent behavior by planning through DINO-WM using model predictive control (b). The use of pretrained embeddings significantly improves performance over prior state-of-the-art world models (c).
> </details>





{{< table-caption >}}
|       | PointMaze | Push-T | Wall | Rope | Granular |
| :---: | :---: | :---: | :---: | :---: | :---: |
| CEM   | 0.8      | 0.86   | 0.74   | NA    | NA     |
| GD    | 0.22     | 0.28   | NA    | NA    | NA     |
| MPC   | 0.98     | 0.90   | 0.96   | 0.41   | 0.26    |{{< /table-caption >}}

> 🔼 이 표는 본 논문에서 제시된 DINO-WM 모델을 포함한 여러 오프라인 월드 모델들의 6가지 제어 환경에서의 계획 성능을 비교 분석한 결과를 보여줍니다.  각 모델의 성공률(SR)과 챔퍼 거리(CD)를 측정하여 정량적으로 비교 평가하였습니다. 성공률은 목표 달성 여부를 나타내며, 챔퍼 거리는 목표와의 오차를 나타냅니다.  실험 환경은 미로 탐색, 밀기 조작, 로봇 팔 제어, 변형 가능한 물체 조작 등 다양한 유형을 포함합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Planning results for offline world models on six control environments.
> </details>





### In-depth insights


#### DINO-WM Overview
DINO-WM은 **오프라인 데이터셋**에서 사전 훈련된 DINOv2의 공간 패치 특징을 활용하여 시각적 역동성을 모델링하는 새로운 방식입니다.  **화상 재구성 없이** 시각적 역동성을 모델링함으로써 계산 비용을 절감하고,  **작업에 대한 특정 정보 없이**도 다양한 작업에 적용 가능한 일반화된 모델을 구축하는 데 중점을 둡니다.  DINO-WM은 미래 패치 특징을 예측하여 관찰 목표를 달성하기 위한 행동 시퀀스를 최적화하며, 목표 특징을 예측 목표로 다룸으로써 작업에 구애받지 않는 계획을 가능하게 합니다.  **사전 학습된 특징 표현**과 **비지도 학습**을 통해 작업 특유의 정보에 대한 의존성을 줄이고 일반화 성능을 높입니다.  테스트 시점에서 전문가 시연, 보상 모델링, 사전 학습된 역 모델 없이도 다양한 작업에서 제로샷 행동 솔루션을 달성하는 것이 특징입니다.  **모델 예측 품질**이 높기 때문에, 추가적인 정보 없이도 추론 시간 최적화를 통해 목표를 달성할 수 있습니다.

#### Zero-Shot Planning
본 논문에서 제시된 제로샷 플래닝(Zero-Shot Planning)은 **사전 학습된 시각적 특징을 활용하여** 오프라인으로 수집된 데이터셋만으로 미지의 작업에 대한 계획을 세우는 능력을 의미합니다. 이는 기존의 온라인 정책 학습 방식과는 다르게, **새로운 작업에 대한 추가적인 학습 없이도** 작업을 수행할 수 있도록 하는 핵심 개념입니다.  **DINO-WM 모델은 이러한 제로샷 플래닝을 가능하게 하는 핵심 요소**로,  미리 학습된 DINOv2 모델의 공간적 패치 특징을 이용하여 시각적 역동성을 모델링하고, 목표 특징을 예측 대상으로 삼아 행동 순서를 최적화합니다.  이를 통해 **작업에 대한 사전 지식 없이도** 관측 목표를 달성할 수 있는 **범용적인 플래닝** 능력을 제공합니다.  다양한 환경에서의 실험 결과는 제로샷 플래닝의 효과를 입증하며, 특히 기존의 최첨단 모델보다 **훨씬 높은 성공률**을 보여주었습니다.  **오프라인 데이터를 활용**하여 범용적인 모델을 학습하고, 테스트 시간에 최적화를 수행함으로써 **효율적이고 일반화된 플래닝**이 가능하다는 것을 시사합니다.

#### Offline World Models
오프라인 월드 모델은 **데이터 수집 및 모델 훈련이 온라인 환경과의 상호작용 없이 이루어지는** 접근 방식입니다.  **사전에 수집된 데이터 세트**를 사용하여 월드 모델을 학습시키고, 이를 바탕으로 테스트 시간에 새로운 작업을 해결할 수 있습니다.  이는 온라인 학습 방식과 비교하여 **데이터 효율성이 높고, 환경 변화에 대한 적응력이 뛰어나다**는 장점을 가지고 있습니다.  하지만,  **데이터 세트의 품질과 다양성이 모델 성능에 큰 영향**을 미치기 때문에, 다양한 상황을 충분히 포함하는 고품질 데이터를 확보하는 것이 중요합니다. 또한, **오프라인 데이터만으로는 복잡한 환경을 충분히 모델링하는데 한계**가 있을 수 있으며, 이러한 한계를 극복하기 위해서는 **모델 구조와 학습 알고리즘의 개선**이 필요합니다.  **영상 예측이나 시뮬레이션**과 같이 오프라인 모델링에서 중요한 역할을 합니다.  궁극적으로 오프라인 월드 모델은 **데이터 효율성과 일반화 성능을 향상**시켜 로봇 및 인공지능 분야에서 더욱 강력하고 유연한 시스템을 구축하는 데 기여할 것입니다.

#### Visual Representation
본 논문에서 시각적 표현은 **DINOv2의 사전 훈련된 공간 패치 특징**을 활용하는 방식으로 제시됩니다. 이는 **화상 재구성 없이 시각적 역동성을 모델링**하는 핵심 전략입니다. 저자들은 **DINOv2가 공간적 및 객체 중심적 표현을 제공하는 사전 훈련된 표현**을 활용함으로써 작업 특정 데이터 커버리지에 대한 필요성을 완화한다고 주장합니다.  **사전 훈련된 특징의 강점**은 다양한 작업에 걸쳐 일관된 세계 모델링을 가능하게 함으로써 작업 독립적인 추론을 가능하게 한다는 점입니다.  **ViT 아키텍처**는 이러한 사전 훈련된 패치 특징과 행동을 사용하여 미래 특징을 예측하는 데 사용됩니다.  이는 **화상 데이터의 압축된 표현**을 사용하는 것이며, 픽셀 단위의 고해상도 재구성보다 효율적이며 일반화 성능이 향상됨을 시사합니다. 따라서, 이 연구의 시각적 표현 전략은 효율성과 일반화 능력을 균형 있게 고려한 접근 방식으로 평가할 수 있습니다.

#### Future Work
본 논문의 "향후 연구 방향"에 대한 심층적인 고찰은 **오프라인 데이터셋의 한계 극복**, **모델의 일반화 성능 향상**, **제어 정책의 고도화** 세 가지 주요 방향으로 귀결됩니다.  **오프라인 데이터셋의 제한된 크기 및 다양성**은 모델의 일반화 능력에 영향을 미치므로, **더욱 방대한 양질의 데이터 확보 및 다양한 환경 조건에서의 데이터 수집**이 필요합니다.  또한, 현재 모델의 제한된 크기와 복잡도는 일반화 성능 향상에 걸림돌이 될 수 있어, **모델 아키텍처 개선 및 매개변수 조정**을 통해 더욱 강건하고 일반화된 모델 개발이 요구됩니다.  마지막으로, 현재는 비교적 단순한 제어 정책을 사용하고 있으므로, **계층적 계획 및 하위 수준 제어 정책과의 통합**을 통해 보다 복잡하고 정교한 작업 수행이 가능한 시스템을 구축하는 연구가 필요합니다.  **강화 학습과의 결합**을 통한 온라인 학습 기능 추가도 고려해볼 만한  **실질적인 문제 해결 능력 향상**에 기여할 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2411.04983/x1.png)

> 🔼 그림 2는 DINO-WM의 아키텍처를 보여줍니다.  과거 관측값(ot−k:t)이 주어지면, DINO-WM은 목표 관측값(og)까지의 예측 손실을 최소화하도록 행동 시퀀스(at:T−1)를 최적화합니다.  모든 순전파 계산은 잠재 공간 z에서 수행됩니다.  여기서 pθ는 DINO-WM의 동적 모델을 나타내며, 미래 예측을 생성하는 데 사용됩니다.  간단히 말해, 이 그림은 모델의 입력, 처리 과정, 그리고 출력을 시각적으로 보여주는 다이어그램입니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Architecture of DINO-WM. Given observations ot−k:tsubscript𝑜:𝑡𝑘𝑡o_{t-k:t}italic_o start_POSTSUBSCRIPT italic_t - italic_k : italic_t end_POSTSUBSCRIPT, we optimize the sequence of actions at:T−1subscript𝑎:𝑡𝑇1a_{t:T-1}italic_a start_POSTSUBSCRIPT italic_t : italic_T - 1 end_POSTSUBSCRIPT to minimize the predicted loss to the desired goal ogsubscript𝑜𝑔o_{g}italic_o start_POSTSUBSCRIPT italic_g end_POSTSUBSCRIPT. All forward computation is done in the latent space z𝑧zitalic_z. Here pθsubscript𝑝𝜃p_{\theta}italic_p start_POSTSUBSCRIPT italic_θ end_POSTSUBSCRIPT indicates DINO-WM’s dynamics model, which is used for making future predictions.
> </details>



![](https://arxiv.org/html/2411.04983/extracted/6170539/figures/env.png)

> 🔼 이 그림은 논문에서 제시된 DINO-WM 모델을 평가한 여섯 가지 환경을 보여줍니다. 왼쪽 위부터 오른쪽 아래로 차례대로 미로 찾기(Maze), 로봇 팔 조작(Reach), 벽 통과(Wall), 밀기(Push-T), 로프 조작(Rope Manipulation), 입자 조작(Granular Manipulation) 환경이 나열되어 있습니다. 각 환경은 DINO-WM이 제로샷(zero-shot) 학습을 통해 어떻게 다양한 작업을 수행하는지 보여주는 시각적 예시를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: We evaluate DINO-WM on six environment suites, from left to right, top to bottom: Maze, Reach, Wall, Push-T, Rope Manipulation, and Granular Manipulation.
> </details>



![](https://arxiv.org/html/2411.04983/extracted/6170539/figures/openloop_fixed.png)

> 🔼 그림 4는 Push-T와 Granular 환경에서 다양한 월드 모델의 오픈루프 전개 결과를 보여줍니다. 각 모델은 첫 번째 프레임과 행동 순서를 입력받아 디코더를 통해 재구성된 미래 프레임을 예측합니다. 각 환경에 대해 하단 행은 실제(ground truth) 결과를 나타냅니다. DINO-WM(Ours)의 전개 결과는 굵게 표시되어 있으며, 실제 관측 결과와 시각적으로 구분할 수 없을 정도로 정확합니다.  즉, DINO-WM이 미래 상태를 매우 정확하게 예측한다는 것을 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Open-loop rollouts of world models on Push-T and Granular. Given the first frame and action sequence, each model predicts future frames, reconstructed by its decoder. For each environment, the bottom row denotes the ground truth. DINO-WM (Ours) rollouts are bolded and are visually indistinguishable from the ground truth observations.
> </details>



![](https://arxiv.org/html/2411.04983/extracted/6170539/figures/generalization_exps.png)

> 🔼 그림 5는 WallRandom, PushObj, GranularRandom 환경에 대한 학습 및 테스트 시각화를 보여줍니다. 테스트 환경은 파란색 상자로 강조 표시되어 있습니다. 이 그림은 세 가지 다른 환경에서 에이전트가 새로운 구성(예: 벽의 위치 변경, 물체의 모양 변경, 입자의 분포 변경)에 얼마나 잘 일반화되는지 보여줍니다. 각 환경에 대해, 에이전트는 다양한 시작 위치와 목표 위치로 여러 번의 시도를 수행하며, 성공률과 목표 달성에 필요한 단계 수를 측정하여 모델의 일반화 능력을 평가합니다. 파란색 상자는 테스트 중인 새로운 구성을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Training and testing visualizations for WallRandom, PushObj and GranularRandom. Test setups are highlighted in blue boxes.
> </details>



![](https://arxiv.org/html/2411.04983/extracted/6170539/figures/avdc_comp_reduced.png)

> 🔼 그림 6은 DINO-WM과 AVDC 모델이 생성한 계획(plan)을 보여줍니다.  두 모델 모두 동일한 시작 상태(start)와 목표 상태(goal)를 가지고 있지만, DINO-WM은 물리적으로 타당하고 효율적인 경로를 생성하는 반면, AVDC는 물리적으로 비현실적이고 비효율적인 계획을 생성합니다. 이는 AVDC가  세부적인 물리적 상호작용을 정확하게 모델링하지 못하기 때문입니다. DINO-WM이 물리적 세계를 더 잘 이해하고 있음을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Plans generated by DINO-WM and AVDC.
> </details>



![](https://arxiv.org/html/2411.04983/extracted/6170539/figures/ac_avdc.png)

> 🔼 이 그림은 DINO-WM과 action-conditioned AVDC 모델이 PushT 환경에서 열린 루프 방식으로 시뮬레이션된 결과를 보여줍니다. 각 시뮬레이션마다 모델은 첫 번째 프레임과 일련의 행동들을 입력으로 받습니다.  모델들은 이러한 정보를 바탕으로 열린 루프 방식(즉, 중간에 수정 없이)으로 시뮬레이션을 진행합니다.  DINO-WM의 경우 정확한 미래 예측을 보여주는 반면, AVDC-AC는 정확도가 떨어지는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Open-loop rollout on PushT with DINO-WM and action-conditioned AVDC (AVDC-AC). For each trajectory, the model is given the first frame as well as sequence of actions. The world models performs open-loop rollout with these actions.
> </details>



![](https://arxiv.org/html/2411.04983/extracted/6170539/figures/plan_results2.png)

> 🔼 표 11은 DINO-WM 모델 훈련을 위한 환경별 하이퍼파라미터를 보여줍니다.  'Dataset Size' 열은 사용된 궤적(trajectory) 데이터셋의 크기를 나타내고, 'Traj. Len.' 열은 각 궤적의 길이(시간 단계 수)를 나타냅니다.  각 환경(PointMaze, Reacher, Push-T, Wall, Rope, Granular)에 따라 데이터셋 크기와 궤적 길이가 다르게 설정되어 있습니다. 이는 각 작업의 복잡성과 특성을 반영한 것입니다.  이 표는 DINO-WM 모델의 훈련 과정에서 환경 특성에 맞춰 어떻게 하이퍼파라미터가 조정되었는지를 보여주는 중요한 정보를 담고 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 11: Environment-dependent hyperparameters for DINO-WM training. We report the number of trajectories in the dataset under Dataset Size, and the length of trajectories under Traj. Len.
> </details>



![](https://arxiv.org/html/2411.04983/extracted/6170539/figures/plan_all.png)

> 🔼 표 12는 DINO-WM 모델 학습에 사용된 공유 하이퍼파라미터들을 보여줍니다. 이미지 크기, 최적화 알고리즘(AdamW), 학습률(Decoder, Predictor, Action Encoder), 액션 임베딩 차원, 에폭 수, 배치 크기 등의 하이퍼파라미터 값들이 명시되어 있습니다. 이 표는 DINO-WM 모델 학습 과정에 대한 세부적인 설정 정보를 제공하여, 실험의 재현성을 높이는 데 기여합니다.
> <details>
> <summary>read the caption</summary>
> Table 12: Shared hyperparameters for DINO-WM training
> </details>



![](https://arxiv.org/html/2411.04983/extracted/6170539/figures/plan_pusht_same_init.png)

> 🔼 그림 8은 PointMaze, Push-T, Granular 세 가지 환경에서 무작위로 선택된 초기 상태와 목표 상태에 대한 계획 시각화를 보여줍니다. 각 환경에 대해 초기 상태('Start'), 계획된 행동 후 도달한 최종 상태('Final'), 목표 상태('Goal')를 보여줍니다.  각 모델의 계획 성능을 비교하기 위해 최고 성능 모델인 DINO CLS와 DreamerV3의 결과도 함께 제시합니다.  각 모델은 주어진 초기 상태와 목표 상태에서 최적의 행동 순서를 계획하고, 그 결과를 시각적으로 보여줍니다. 이를 통해 각 모델의 계획 능력과 일반화 성능을 시각적으로 비교할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Planning visualizations for PointMaze, Push-T, and Granular, on randomly sampled initial and goal configurations. The task is defined by Start and Goal, denoting the initial and goal observations. Final shows the final state the system arrives at after planning with each world model. For comparison, we show the best performing world models DINO CLS and DreamerV3.
> </details>



![](https://arxiv.org/html/2411.04983/extracted/6170539/figures/plan_pointmaze_same_init.png)

> 🔼 그림 9는 DINO-WM을 사용하여 여섯 가지 환경에서 계획된 궤적을 보여줍니다. 각 환경에 대해 위쪽(음영 처리된) 행은 계획된 행동을 실행한 후 환경의 관찰 결과를 보여주고, 아래쪽 행은 세계 모델이 상상한 관찰 결과를 보여줍니다.  쉽게 말해, DINO-WM이 각 상황에서 어떤 행동을 계획했고, 그 결과 실제 환경과 모델이 예측한 결과가 어떻게 다른지를 비교하여 보여주는 그림입니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Trajectories planned with DINO-WM on all six environments. For each environment, the top (shaded) row shows the environment’s observation after executing the planned actions, and the bottom row shows the world model’s imagined observations.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | LPIPS PushT ↓ | LPIPS Wall ↓ | LPIPS Rope ↓ | LPIPS Granular ↓ | SSIM PushT ↑ | SSIM Wall ↑ | SSIM Rope ↑ | SSIM Granular ↑ |
|---|---|---|---|---|---|---|---|---|
| R3M | 0.045 | 0.008 | 0.023 | 0.080 | 0.956 | 0.994 | 0.982 | 0.917 |
| ResNet | 0.063 | 0.002 | 0.025 | 0.080 | 0.950 | 0.996 | 0.980 | 0.915 |
| DINO CLS | 0.039 | 0.004 | 0.029 | 0.086 | 0.973 | 0.996 | 0.980 | 0.912 |
| AVDC | 0.046 | 0.030 | 0.060 | 0.106 | 0.959 | 0.983 | 0.979 | 0.909 |
| Ours | **0.007** | **0.0016** | **0.009** | **0.035** | **0.985** | **0.997** | **0.985** | **0.940** |{{< /table-caption >}}
> 🔼 이 표는 다양한 사전 훈련된 인코더를 사용한 월드 모델의 계획 성능을 보여줍니다.  각 사전 훈련된 인코더(R3M, ResNet, DINO CLS, DINO 패치)를 사용하여 훈련된 월드 모델이 6가지 환경(미로, 벽, 도달, 푸시, 로프 조작, 입상 조작)에서 얼마나 잘 수행하는지 성공률(SR)과 샴퍼 거리(CD)를 통해 비교 분석합니다.  이를 통해 사전 훈련된 시각적 표현의 중요성과 DINO-WM의 일반화 성능을 평가합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Planning results for world models with various pre-trained encoders.
> </details>

{{< table-caption >}}
| Metric | Time (s) |
|---|---| 
| Inference (Batch 32) | 0.014 |
| Simulation Rollout (Batch 1) | 3.0 |
| Planning (CEM, 100x10) | 53.0 |{{< /table-caption >}}
> 🔼 이 표는 세 가지 새로운 환경 구성(WallRandom, PushObj, GranularRandom)에서 이전에 보지 못한 환경 구성을 사용하여 오프라인 월드 모델의 계획 성능을 보여줍니다.  각 환경은 다양한 난이도와 특징을 가지고 있으며, 모델이 얼마나 일반화될 수 있는지 평가합니다.  성공률(SR)과 샴페르 거리(CD)는 각 작업에 대한 모델의 성능을 측정하는 지표입니다.  이 표는 DINO-WM이 다른 최첨단 모델에 비해 이러한 새로운 환경에서 얼마나 잘 수행되는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Planning results for offline world models on three suites with unseen environment configurations.
> </details>

{{< table-caption >}}
|       | H | Frameskip | Dataset Size | Traj. Len. |
| :---- | :-: | :-: | :-: | :-: |
| PointMaze | 3 | 5 | 2000 | 100 |
| Reacher | 3 | 5 | 3000 | 100 |
| Push-T | 3 | 5 | 18500 | 100-300 |
| PushObj | 3 | 5 | 20000 | 100 |
| Wall | 1 | 5 | 1920 | 50 |
| WallRandom | 1 | 5 | 10240 | 50 |
| Rope | 1 | 1 | 1000 | 5 |
| Granular | 1 | 1 | 1000 | 5 |{{< /table-caption >}}
> 🔼 표 4는 다양한 월드 모델들의 지각적 유사성을 측정하는 지표인 LPIPS (Learned Perceptual Image Patch Similarity) 점수를 비교한 표입니다. LPIPS 점수는 낮을수록 시각적 유사성이 높다는 것을 의미합니다. 표에는 PushT, Wall, Rope, Granular 등 네 가지 환경에서 다양한 모델들의 LPIPS 점수가 제시되어 있으며, DINO-WM이 다른 모델들에 비해 훨씬 더 낮은 LPIPS 점수를 기록함으로써 시각적 유사성이 가장 높음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Comparison of world models on LPIPS metrics.
> </details>

{{< table-caption >}}
| Name | Value |
|---|---| 
| Image size | 224 |
| Optimizer | AdamW |
| Decoder lr | 3e-4 |
| Predictor lr | 5e-5 |
| Action encoder lr | 5e-4 |
| Action emb dim | 10 |
| Epochs | 100 |
| Batch size | 32 |{{< /table-caption >}}
> 🔼 표 5는 다양한 크기의 데이터셋으로 학습된 DINO-WM을 사용하여 PushT 환경에서의 계획 성능과 예측 품질을 보여줍니다. SSIM과 LPIPS는 디코딩 후 예측된 미래 잠재값을 기준으로 측정됩니다. 데이터셋 크기가 증가함에 따라 성능이 일관되게 향상되는 것을 확인할 수 있습니다. 즉, 더 많은 데이터로 학습할수록 DINO-WM 모델의 예측 정확도가 높아지고, 그 결과 계획 성능 또한 향상된다는 것을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Planning performance and prediction quality on PushT with DINO-WM trained on datasets of various sizes. SSIM and LPIPS are measured on the predicted future latents after decoding. We observe consistent improvement in performance as we increase the dataset size.
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