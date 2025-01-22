---
title: "GameFactory: Creating New Games with Generative Interactive Videos"
summary: "GameFactory는 사전 훈련된 비디오 모델을 활용, 오픈 도메인 비디오에서 새로운 게임을 생성하는 프레임워크입니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Video Understanding", "🏢 University of Hong Kong",]
showSummary: true
date: 2025-01-14
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.08325 {{< /keyword >}}
{{< keyword icon="writer" >}} Jiwen Yu et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-21 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.08325" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.08325" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/gamefactory-creating-new-games-with" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 게임 제작 방식은 고정된 스타일과 장면에 국한되어 **새로운 게임 경험을 창출하는 데 한계**가 있었습니다.  본 연구는 이러한 문제를 해결하기 위해 **비디오 확산 모델 기반의 게임 제작 프레임워크인 GameFactory**를 제시합니다.  이는 기존 게임에 제한되지 않고, **다양한 오픈 도메인 장면에서 새로운 게임을 생성**할 수 있는 잠재력을 갖추고 있습니다.

GameFactory는 **Minecraft 데이터셋을 활용하여 액션 제어 모듈을 학습**하고, 이를 **오픈 도메인 비디오에 적용**합니다.  **멀티 단계 학습 전략**을 통해 게임 스타일 학습과 액션 제어를 분리하여 **오픈 도메인 일반화와 액션 제어 성능을 동시에 향상**시켰습니다.  또한, **자동 회귀적 긴 비디오 생성**을 지원하여 **제한 없는 길이의 상호 작용적 게임 비디오를 생성**할 수 있도록 합니다.  본 연구는 AI 기반 게임 제작 분야의 발전에 기여하며, 새로운 게임 경험을 창출하는 데 기여할 것으로 기대됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} GameFactory는 사전 훈련된 비디오 모델을 이용해 다양한 장면에서 게임을 생성할 수 있습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 본 연구는 멀티 단계 학습 전략을 통해 게임 스타일 학습과 액션 제어를 분리하여 오픈 도메인 일반화를 유지하면서 액션 제어 성능을 향상시켰습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 자동 회귀적 긴 비디오 생성을 통해 제한 없는 길이의 상호 작용적 게임 비디오 생성을 가능하게 합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
이 논문은 **AI 기반 게임 제작 분야의 혁신적인 발전**을 제시하며, **새로운 게임 경험을 창출하는 데 기여**합니다. 기존 게임 제작 방식의 한계를 극복하고, **새로운 게임 장르를 개척**할 수 있는 가능성을 열어줍니다. 또한, 제시된 방법론은 **다른 분야의 연구에도 적용될 수 있는 잠재력**을 가지고 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.08325/x3.png)

> 🔼 그림 1은 제안된 GameFactory 프레임워크를 보여줍니다. 이 프레임워크는 사전 훈련된 비디오 모델의 강력한 생성 능력을 활용하여 새로운 게임을 만듭니다. 소규모 1인칭 마인크래프트 데이터셋으로부터 동작 제어를 학습하여 이 프레임워크는 이러한 제어 기능을 개방형 도메인 비디오로 전이할 수 있으며, 궁극적으로 개방형 도메인 장면 내에서 새로운 게임을 생성할 수 있습니다. (1)~(4)에서 보여주는 바와 같이 GameFactory는 다양하고 새롭게 생성된 개방형 도메인 장면에서 동작 제어를 지원하여 완전히 새로운 게임 경험 개발의 길을 열어줍니다. 노란색 버튼은 눌린 키를, 화살표는 마우스 움직임의 방향을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: We propose GameFactory, a framework that leverages the powerful generative capabilities of pre-trained video models for the creation of new games. By learning action control from a small-scale first-person Minecraft dataset, this framework can transfer these control abilities to open-domain videos, ultimately allowing the creation of new games within open-domain scenes. As illustrated in (1)-(4), GameFactory supports action control across diverse, newly generated scenes in open domains, paving the way for the development of entirely new game experiences. The yellow buttons indicate pressed keys, and the arrows represent the direction of mouse movements.
> </details>





{{< table-caption >}}
| Control Module | Only-Key | Mouse-Small | Mouse-Large |
|---|---|---|---|---|
| Key | Mouse | Flow-MSE ↓ | CLIP-Sim ↑ | FID ↓ | Flow-MSE ↓ | CLIP-Sim ↑ | FID ↓ | Flow-MSE ↓ | CLIP-Sim ↑ | FID ↓ |
| Cross Attention | Cross Attention | 8.67 | **0.3313** | 107.13 | 20.46 | 0.3137 | **125.67** | 325.18 | 0.3103 | 167.37 |
| Concat | Concat | 22.37 | 0.3277 | **103.89** | 19.18 | 0.3159 | 133.42 | 258.93 | **0.3123** | 145.74 |
| **Cross Attention** | **Concat** | **7.79** | 0.3292 | 105.28 | **18.64** | **0.3184** | 127.84 | **249.54** | 0.3107 | **139.91** |{{< /table-caption >}}

> 🔼 표 1은 동작 제어 메커니즘에 대한 비교 연구 결과를 보여줍니다.  연구 결과에 따르면,  불연속적인 동작 제어에는 cross-attention 기법이, 연속적인 동작 제어에는 concatenation 기법이 최적의 접근 방식임을 알 수 있습니다.  다양한 동작 제어 메커니즘(cross-attention 또는 concatenation 사용, 키 입력 또는 마우스 입력만 사용)을 비교하여 불연속적(키 입력) 및 연속적(마우스 입력) 동작 제어에 대한 각 기법의 성능을 평가했습니다.  FID, CLIP-Sim, Flow-MSE 지표를 사용하여 생성된 비디오의 품질과 동작 제어 정확도를 측정하였습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Results of the ablation study on action control mechanisms. The findings indicate that an optimal approach for the action control module is to use cross-attention for discrete action control and concatenation for continuous action control.
> </details>





### In-depth insights


#### Generative Game AI
생성형 게임 AI는 게임 개발 과정을 혁신할 잠재력을 지닌 분야입니다. **자동화된 콘텐츠 생성 및 수작업 감소**를 통해 게임 개발의 효율성을 높일 수 있습니다. 기존의 비디오 기반 게임 생성 방식은 **장면 일반화의 어려움** 때문에 고정된 스타일과 장면을 가진 기존 게임에만 적용될 수 있다는 한계가 있습니다.  본 논문에서 제시된 GameFactory는 이러한 문제를 해결하기 위해 **사전 훈련된 비디오 확산 모델을 활용**하여 다양한 새로운 게임을 생성합니다.  **오픈 도메인 비디오 데이터를 사용**하여 장면 일반화를 달성하고, 소규모 게임 데이터셋으로부터 학습한 행동 제어 모듈을 통해 오픈 도메인 장면 내에서 새로운 게임을 생성할 수 있게 합니다.  **멀티 단계 학습 전략**을 통해 게임 스타일 학습과 행동 제어를 분리하여 오픈 도메인 일반화를 유지하면서 행동 제어 성능을 확보합니다.  이는 게임 제작의 새로운 가능성을 열어주는 중요한 진전이며, 앞으로 **AI 기반 게임 엔진의 발전**에 크게 기여할 것으로 예상됩니다.  하지만 **장면 일반화**에 대한 더 많은 연구와 **사전 훈련된 모델**의 성능 개선이 필요합니다.

#### Action Control
본 논문에서 제시된 게임팩토리는 **영상 생성 모델의 제어 가능성**에 초점을 맞추고 있습니다.  이는 단순히 영상을 생성하는 것을 넘어, 사용자의 입력에 따라 영상의 내용을 실시간으로 변화시키는 **상호작용적인 게임 경험**을 제공하기 위한 중요한 부분입니다.  특히, **다양한 유형의 액션 제어 방식** (키보드 입력, 마우스 움직임 등)을 지원하며, 각각에 최적화된 제어 모듈을 설계하여 효율적인 액션 처리를 구현하는 점이 돋보입니다.  **지연 효과를 고려한 슬라이딩 윈도우 기법**을 통해 과거 행동이 미래 프레임에 미치는 영향을 효과적으로 처리하고, **연속적인 마우스 움직임과 이산적인 키보드 입력을 모두 지원**하는 제어 메커니즘을 통해 다채롭고 현실감 있는 게임 환경을 구축할 수 있습니다.  **사전 훈련된 모델의 장점을 활용**하여 오픈 도메인 영상에서도 효과적인 액션 제어를 가능하게 만드는 점은 **일반화 가능성**을 높이는 핵심입니다.  **다중 단계 학습 전략**을 통해 스타일 학습과 액션 제어를 분리하여, 특정 게임 스타일이 아닌 일반적인 액션 제어 능력을 확보하는 것이 중요한 특징입니다.

#### Scene Gen
본 논문에서 제시된 Scene Gen 개념은 **장면 일반화(scene generalization)**를 통해 기존 게임에 국한되지 않고 다양한 환경에서 새로운 게임을 생성하는 능력에 초점을 맞춥니다.  이는 **기존 게임 생성 방식의 한계를 극복**하기 위한 핵심 전략으로, 특정 게임 데이터에 과적합(overfitting)되는 문제를 해결하고 개방형 도메인(open-domain) 영상 데이터의 풍부한 사전 정보를 활용하여 다양한 장면을 생성합니다.  **사전 훈련된 비디오 생성 모델**을 기반으로 하며, 소규모 게임 데이터셋으로부터 학습된 행동 제어 모듈을 결합하여 **개방형 도메인에서의 제어 가능성을 확보**합니다.  이를 통해 게임 스타일 학습과 행동 제어를 분리하는 다단계 훈련 전략을 통해 일반화 성능을 높이고, **자동 회귀적(autoregressive) 방식**으로 무한한 길이의 게임 비디오 생성을 가능하게 합니다.  결과적으로, Scene Gen은 **AI 기반 게임 생성의 혁신**을 이끌고, 새로운 게임 경험을 창출하는 데 기여할 것으로 기대됩니다.

#### Multi-phase Training
본 논문에서 제안하는 다단계 학습 전략은 **씬 일반화를 달성하면서 동시에 액션 제어 성능을 유지**하기 위한 핵심 전략입니다. 이는 단순히 사전 훈련된 모델을 게임 데이터로 미세 조정하는 기존 방식의 한계를 극복하기 위해 고안되었습니다.  **첫 번째 단계**에서는 사전 훈련된 비디오 생성 모델에 LoRA(Low-Rank Adaptation)를 사용하여 게임 특유의 스타일을 학습시킵니다.  **두 번째 단계**에서는 게임 스타일을 유지하면서 액션 제어 모듈을 학습시켜 게임 스타일 학습과 액션 제어 학습을 분리합니다.  **세 번째 단계**에서는 LoRA 가중치를 제거하고 액션 제어 모듈만을 사용하여 오픈 도메인에서 액션 제어가 가능한 게임 영상을 생성합니다. 이러한 다단계 접근 방식은 **게임 특유의 스타일 편향을 최소화**하면서 **오픈 도메인에서의 일반화 능력**을 향상시키는 데 중요한 역할을 합니다.  **결론적으로**, 다단계 학습 전략은 게임 영상 생성 모델의 성능 향상에 크게 기여하며, 씬 일반화와 액션 제어라는 두 가지 중요한 목표를 동시에 달성하는 효과적인 방법론임을 보여줍니다.

#### Future Work
본 논문의 "미래 연구" 부분에 대한 심층적인 고찰은 다음과 같습니다. **GameFactory의 핵심적인 한계는 게임 스타일과 액션 제어를 명확히 분리하는 다단계 학습 전략에도 불구하고, 여전히 특정 게임 데이터의 스타일 편향을 완전히 제거하지 못한다는 점**입니다.  향후 연구는 **더욱 강력한 스타일 일반화를 위한 새로운 기술**을 탐구해야 합니다.  예를 들어, 스타일 변환 네트워크를 추가하여  Minecraft 스타일의 영향을 최소화하고,  다양한 게임 스타일을 학습할 수 있도록 하는 것입니다. 또한, **현재 모델은 연속적인 게임 플레이를 위한 장기간의 게임 비디오 생성에 제한**이 있습니다.  **자동 회귀적 비디오 생성의 효율성을 높이고, 무한한 길이의 인터랙티브 게임 비디오 생성을 가능하게 하는 기술 개발**이 중요합니다.  더 나아가, **다양한 게임 장르와 플랫폼에 대한 일반화 능력을 향상시키기 위한 연구**도 필요합니다.  **더욱 다양한 액션 유형과 복잡한 상호작용을 포괄하는 데이터셋을 구축**하는 것 또한 중요한 과제입니다.  마지막으로,  **GameFactory를 실제 게임 개발 환경에 통합하고, 사용자 인터페이스와의 완벽한 통합**을 연구하여 사용자 친화적인 게임 제작 환경을 구축하는 것이 중요한 미래 연구 과제입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.08325/x4.png)

> 🔼 그림 2는 제안된 GameFactory의 개념도를 보여줍니다. GameFactory는 사전 훈련된 대규모 비디오 생성 모델을 기반으로 새로운 게임을 만드는 프레임워크입니다. 그림의 상단 파란색 부분은 사전 훈련된 모델이 개방형 도메인에서 생성 능력을 보이는 것을 나타내고, 하단 녹색 부분은 소량의 게임 데이터로 학습된 동작 제어 모듈을 추가하여 새로운 게임을 생성하는 과정을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: A schematic of our GameFactory creating new games based on pre-trained large video generation models. The upper blue section shows the generative capabilities of the pre-trained model in an open-domain, while the lower green section demonstrates how the action control module, learned from a small amount of game data, can be plugged in to create new games.
> </details>



![](https://arxiv.org/html/2501.08325/x5.png)

> 🔼 그림 3은 비디오 확산 모델에 액션 제어 모듈을 통합하는 방법과 연속적인 마우스 신호 및 이산적인 키보드 신호에 대한 다양한 제어 메커니즘을 보여줍니다. (a)는 액션 제어 모듈이 비디오 확산 모델의 트랜스포머 블록에 통합되는 방식을 보여줍니다. (b)는 연속적인 마우스 신호와 이산적인 키보드 신호에 대한 서로 다른 제어 메커니즘을 보여줍니다. 자세한 내용은 3.3절을 참조하십시오. (c)는 시간적 압축(압축 비율 r=4)으로 인해 잠재 특징의 수가 액션 수와 달라 융합 과정에서 과립성 불일치가 발생하는 것을 보여줍니다. 그룹화는 이러한 시퀀스를 정렬하여 융합합니다. 또한, i번째 잠재 특징은 이전 창(창 크기 w=3) 내의 액션 그룹과 융합될 수 있으며, 이는 지연된 액션 효과(예: '점프' 키는 여러 후속 프레임에 영향을 미침)를 설명합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3:  (a) Integration of Action Control Module into transformer blocks of the video diffusion model. (b) Different control mechanisms for continuous mouse signals and discrete keyboard signals (detailed analysis in Sec 3.3). (c) Due to temporal compression (compression ratio r=4𝑟4r=4italic_r = 4), the number of latent features differs from the number of actions, causing granularity mismatch during fusion. Grouping aligns these sequences for fusion. Additionally, the i𝑖iitalic_i-th latent feature can fuse with action groups within a previous window (window size w=3𝑤3w=3italic_w = 3), accounting for delayed action effects (e.g., ‘jump’ key affects several subsequent frames).
> </details>



![](https://arxiv.org/html/2501.08325/x6.png)

> 🔼 그림 4는 비디오 게임 생성에서 스타일 편향 문제를 보여줍니다. Minecraft 데이터로 학습된 모델은 Minecraft 고유의 픽셀 블록 스타일을 상속하여 원래 파라미터와 도메인 격차를 만듭니다. 이러한 문제는 특수한 훈련 전략을 통해 액션 제어 학습과 데이터 스타일 학습을 분리해야 함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4:  Style bias in video game generation. The model tuned on Minecraft data inherits its distinctive pixelated block style, creating a domain gap from the original parameters. This motivates decoupling action control learning from data style learning through specialized training strategies.
> </details>



![](https://arxiv.org/html/2501.08325/x7.png)

> 🔼 그림 5는 GameFactory의 다단계 학습 전략을 보여줍니다. 먼저, 대규모 개방형 도메인 비디오 데이터로 비디오 생성 모델을 사전 훈련합니다 (Phase #0).  다음으로, 게임 비디오 데이터를 사용하여 LoRA를 미세 조정하여 게임 특유의 스타일을 학습합니다 (Phase #1). 이후, 다른 매개변수를 고정하고 액션 제어 모듈을 훈련하여 스타일과 독립적인 액션 제어를 수행합니다 (Phase #2). 마지막으로, Phase #0에서 얻은 개방형 도메인 기능을 유지하면서 Phase #3에서 액션 제어가 가능한 개방형 도메인 생성을 위한 추론을 수행합니다.  스타일 학습과 액션 제어를 분리하여 Phase #0의 개방형 도메인 기능을 보존하고 Phase #3에서 일반화를 가능하게 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5:  Phase #0: pretraining a video generation model on open-domain data. Phase #1: finetuning with LoRA for game video data. Phase #2: training the action control module while fixing other parameters. Phase #3: inference for action-controlled open-domain generation. To decouple style learning from action control, Phase #1 learns game-specific style while Phase #2 focuses on style-independent action control. This design preserves the open-domain capabilities from Phase #0, enabling generalization in Phase #3.
> </details>



![](https://arxiv.org/html/2501.08325/x8.png)

> 🔼 그림 6은 자기 회귀적 비디오 생성 과정을 보여줍니다. 0부터 k까지의 프레임은 조건부 프레임으로 사용되고, 나머지 N-k 프레임은 예측을 위해 사용됩니다. k값은 무작위로 선택됩니다. (a) 학습 단계에서는 예측된 프레임의 노이즈에만 초점을 맞춰 손실을 계산하고 최적화합니다. (b) 추론 단계에서는 모델이 반복적으로 최근 k+1개의 프레임을 조건으로 사용하여 N-k개의 새로운 프레임을 생성하여 자기 회귀적 생성을 가능하게 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6:  Illustration of autoregressive video generation. The frames from index 00 to k𝑘kitalic_k serve as conditional frames, while the remaining N−k𝑁𝑘N-kitalic_N - italic_k frames are for prediction, with k𝑘kitalic_k randomly selected. (a) Training stage: Loss computation and optimization focus only on the noise of predicted frames. (b) Inference stage: The model iteratively selects the latest k+1𝑘1k+1italic_k + 1 frames as conditions to generate N−k𝑁𝑘N-kitalic_N - italic_k new frames, enabling autoregressive generation.
> </details>



![](https://arxiv.org/html/2501.08325/x9.png)

> 🔼 그림 7은 Minecraft 환경에서 모델의 동작 제어 성능을 보여줍니다. 모델은 WASD 키와 마우스 기반의 yaw 및 pitch 제어를 포함한 기본적인 단위 동작들을 성공적으로 학습했습니다.  더 나아가, 이러한 단위 동작들을 결합하여 더욱 복잡한 움직임을 수행할 수 있습니다.  각 비디오 프레임 아래의 텍스트는 모델에 제공된 프롬프트가 아니라 해당 콘텐츠에 대한 설명입니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Demonstration of action control capabilities in the Minecraft domain. The model has successfully learned basic atomic actions (WASD keys) and mouse-based yaw and pitch controls. Additionally, it can combine these atomic actions to execute more complex movements. Note that the text below each video frame is a descriptive label of the content, not a text prompt provided to the model.
> </details>



![](https://arxiv.org/html/2501.08325/x10.png)

> 🔼 그림 8은 Minecraft 게임 내비게이션에서 가장 흔한 상호 작용 중 하나인 충돌에 대한 학습된 반응을 보여줍니다. 각 비디오 프레임 아래의 텍스트는 모델에 제공된 텍스트 프롬프트가 아니라 콘텐츠에 대한 설명 레이블임을 유의해야 합니다.  비디오는 에이전트가 장애물에 접근하고 충돌을 감지하여 멈추는 과정을 보여주며, 모델이 Minecraft 환경 내에서 물리적 상호 작용을 이해하고 반응하는 능력을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Demonstration of the learned response to collision, one of the most common interactions in Minecraft navigation. Note that the text below each video frame is a descriptive label of the content, not a text prompt provided to the model.
> </details>



![](https://arxiv.org/html/2501.08325/x11.png)

> 🔼 그림 9는 제안된 모델이 레이싱 게임이라는 다른 유형의 게임으로 일반화될 수 있음을 보여줍니다. 흥미롭게도, Minecraft에서 학습된 방향 제어(yaw control)가 레이싱 게임의 조향 제어(steering control)로 매끄럽게 전이되는 반면, 뒤로, 왼쪽, 오른쪽으로 이동하거나 피치 각도를 조정하는 것과 같은 관련 없는 동작들은 자동으로 줄어듭니다. 이는 모델이 게임 유형에 관계없이 특정 동작 제어에 대한 지식을 일반화할 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Our model demonstrates the ability to generalize to a different game type, a racing game. Interestingly, the yaw control learned in Minecraft seamlessly transfers to steering control in the racing game, while unrelated actions, such as moving backward, left, or right, and pitch angle adjustments, automatically diminish.
> </details>



![](https://arxiv.org/html/2501.08325/x12.png)

> 🔼 이 그림은 논문의 GF-Minecraft 데이터셋에 대한 설명 부분에 포함되어 있습니다.  그림은 Minecraft 게임 영상의 한 장면을 보여주며, 영상에 대한 텍스트 주석이 어떻게 생성되었는지 보여주는 예시입니다.  붉은색 볼드체로 강조 표시된 단어들은 MiniCPM이라는 다중 모드 대규모 언어 모델을 사용하여 생성된 자동 주석의 일부입니다.  이 그림을 통해 연구자들은 자동 주석 생성 과정을 설명하고, 데이터셋에 포함된 비주얼 정보와 텍스트 정보의 연관성을 보여줍니다.  즉, 게임 영상의 시각적 내용을 정확하게 설명하는 텍스트 주석이 생성되었음을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: An example of video clip annotation, where words describing scenes and objects are highlighted in red and bolded.
> </details>



![](https://arxiv.org/html/2501.08325/x13.png)

> 🔼 그림 11은 키 입력 제어 성능에 대한 정성적 비교를 보여줍니다.  개별 키 입력 신호 처리에서 cross-attention이 concatenation보다 훨씬 우수한 성능을 보이는 반면, concatenation은 키 입력에 반응하지 못하는 경우가 있음을 알 수 있습니다. 노란색 버튼은 눌린 키를 나타냅니다.  즉, 불연속적인 키 입력에 대해서는 cross-attention 방식이 더 효과적이라는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Qualitative comparison of key input control performance. It can be observed that cross-attention significantly outperforms concatenation in handling discrete key input signals, while concatenation may fail to respond to the key input. The yellow buttons indicate pressed keys.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Behavior | Control Signal | Action Interface |
|---|---|---|
| forward | W key | Interface<sub>1</sub> |
| back | S key | Interface<sub>1</sub> |
| left | A key | Interface<sub>2</sub> |
| right | D key | Interface<sub>2</sub> |
| jump | space key | Interface<sub>3</sub> |
| sneak | shift key | Interface<sub>3</sub> |
| sprint | ctrl key | Interface<sub>3</sub> |
| vertical perspective movement | mouse movement(yaw) | Interface<sub>4</sub> |
| horizontal perspective movement | mouse movement(pitch) | Interface<sub>5</sub> |{{< /table-caption >}}
> 🔼 표 2는 Minecraft 게임 환경에서 사용된 행동 공간에 대한 세부 정보를 보여줍니다.  '제어 신호(Control Signal)' 열은 학습 목적으로 사용된 원시 입력 신호를 나타내고, '행동 인터페이스(Action Interface)' 열은 MineDojo 플랫폼에서 이러한 신호를 실행 가능한 명령으로 매핑하는 인터페이스를 나타냅니다.  각 행은 특정 행동(예: 앞으로 이동, 뒤로 이동 등), 해당 행동에 해당하는 제어 신호(키 입력 또는 마우스 움직임) 및 MineDojo 인터페이스를 보여줍니다. 이 표는 모델이 학습에 사용한 행동과 MineDojo 시뮬레이션 환경과의 연결 관계를 명확히 설명합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Details of Action Space. The term Control Signal refers to the raw input signals utilized for training purposes, while the Action Interface represents the corresponding interface in the MineDojo platform that maps these input signals to actionable commands.
> </details>

{{< table-caption >}}
| Method | Domain | Flow-MSE ↓ | Domain-Sim ↑ | CLIP-Sim ↑ | FID ↓ |
|---|---|---|---|---|---| 
| Multi-Phase Training | Minecraft | **43.48** | - | - | - |
| Multi-Phase Training | Open-Domain | 54.13 | **0.7565** | **0.3181** | **121.18** |
| One-Phase Training | Open-Domain | 76.02 | 0.7345 | 0.3111 | 167.79 |{{< /table-caption >}}
> 🔼 표 3은 GameFactory 모델의 씬 일반화 성능을 평가한 정량적 결과를 보여줍니다.  다중 단계 학습 전략과 단일 단계 학습 전략을 사용하여 생성된 오픈 도메인 비디오와 마인크래프트 비디오의 Flow-MSE, Domain-Sim, CLIP-Sim, FID 값을 비교 분석하여 모델의 일반화 성능과 품질을 평가합니다. 특히, 다중 단계 학습 전략이 오픈 도메인 씬에서 더 나은 액션 제어 성능과 도메인 유사성을 보이는지 확인합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Quantitative results of evaluation on scene generalization.
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
{{< /gallery >}}