---
title: "EgoSpeak: Learning When to Speak for Egocentric Conversational Agents in the Wild"
summary: "EgoSpeak: 시각적 정보 기반 실시간 발화 시점 예측으로 자연스러운 대화 가능"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Human-AI Interaction", "🏢 Yonsei University",]
showSummary: true
date: 2025-02-17
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.14892 {{< /keyword >}}
{{< keyword icon="writer" >}} Junhyeok Kim et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-24 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.14892" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.14892" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

많은 연구가 단순화된 환경에서 대화 시점 예측에 집중했지만, 실제 세계의 복잡한 상호작용은 고려하지 못했습니다.  **다양한 화자, 겹치는 발화, 긴 침묵 등의 요소**가 실제 대화에서는 흔히 나타나기 때문에, 이러한 복잡성을 처리하는 것은 매우 어렵습니다. 기존 연구는 제한된 환경에서 이루어져 실제 적용에 한계가 있었습니다.

본 논문에서는 **EgoSpeak라는 새로운 프레임워크**를 제시하여 이 문제를 해결합니다. EgoSpeak는 **1인칭 시점의 비디오 스트림**을 사용하여 실시간으로 발화 시점을 예측합니다. **RGB 영상 처리, 온라인 처리, 무편집 비디오 처리 기능**을 통합하여 실제 환경의 복잡성을 처리합니다.  또한, 대규모 사전 학습을 위한 **YT-Conversation** 데이터셋을 공개하여 다른 연구자들의 활용을 돕습니다. 실험 결과는 EgoSpeak가 기존 방식보다 실시간 발화 시점 예측 성능이 뛰어남을 보여주며, 다양한 입력 정보와 긴 문맥 정보의 중요성을 강조합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 새로운 실시간 발화 시점 예측 프레임워크 EgoSpeak 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 다양한 모달리티(시각, 청각) 및 긴 문맥 정보 활용으로 성능 향상 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 실제 환경 대화 데이터셋 YT-Conversation 공개 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **실시간 대화형 에이전트의 자연스러운 대화 능력 향상**에 중요한 기여를 합니다. **실제 환경에서의 복잡한 대화 상황을 고려한 새로운 프레임워크**를 제시하고, **다양한 모달리티 데이터와 긴 문맥 정보를 효과적으로 활용**하여 성능을 향상시켰습니다.  이는 **대화형 AI 분야의 발전**에 크게 기여하고, **실제 로봇이나 가상 에이전트 개발**에 직접적으로 활용될 수 있습니다.  또한 제시된 **대규모 데이터셋 (YT-Conversation)**은 관련 연구 분야의 발전에도 큰 영향을 미칠 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.14892/x1.png)

> 🔼 그림 1은 EgoSpeak 모델이 카메라 착용자의 시점(카메라 아이콘)에서 얻은 영상 스트림을 실시간으로 처리하여 발화 시점을 예측하는 과정을 보여줍니다. 실제 사람처럼 다양한 발화자들이 있는 역동적인 환경에서 상황을 인지하고 참여하는 방식을 반영합니다. 그림에서는 카메라 착용자가 언제 말을 시작해야 할지 고민하는 모습과 주변 상황(다른 사람들의 발화 여부)을 보여주는 여러 시나리오를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: EgoSpeak models speech initiation in real time from the camera wearer’s (camera icon) egocentric video stream, mirroring how a real-world agent would perceive and engage in dynamic, multi-speaker environments.
> </details>







### In-depth insights


#### EgoSpeak Framework
EgoSpeak Framework는 **실시간 이기중심 대화 에이전트를 위한 새로운 프레임워크**로, 실제 환경에서의 복잡한 대화 상황 속에서 에이전트가 언제 말해야 하는지를 예측하는 것을 목표로 합니다. 이는 **일반적인 설정이 아닌 실제 세상의 복잡성을 반영**하여, 겹치는 발화, 모호한 발화자 역할, 잦은 중단 등을 고려합니다.  **1인칭 시점의 RGB 영상 처리 및 온라인 처리를 통합**하여 실시간으로 대화 맥락을 이해하고,  **자연스러운 대화 흐름을 위해 지속적인 비다듬어진 비디오 스트림을 처리**합니다.  **다양한 YouTube 대화 비디오 데이터셋을 활용**하여 모델의 성능 향상을 도모하며,  EasyCom 및 Ego4D 데이터셋을 사용한 실험 결과는 **EgoSpeak이 기존 방법들을 능가**함을 보여줍니다.  특히 **다중 모달 입력과 맥락 길이의 중요성**을 강조하며, 실제 환경에서의 에이전트에게 **자연스러운 대화 참여를 위한 핵심적인 요소**임을 시사합니다.

#### YT-Conversation Dataset
본 논문에서 제시된 YT-Conversation 데이터셋은 **기존의 제한된 환경에서 수집된 대화 데이터셋의 한계를 극복하기 위해** YouTube의 다양한 대화 영상들을 활용하여 구축되었습니다. **실제 자연어 대화의 복잡성과 다양성을 반영**하기 위해 인터뷰, 팟캐스트, 일상적인 대화 등 다양한 유형의 영상들을 포함하고 있으며, **대규모의 비지도 학습을 통해 다양한 어휘 및 문맥을 학습**할 수 있도록 설계되었습니다. 이 데이터셋은 에고스피크 모델의 사전 학습에 사용되었으며, **실제 환경에서의 대화 상황을 보다 정확하게 예측**하는 데 기여한 것으로 나타났습니다.  하지만, **전적으로 에고중심적 관점의 영상은 아니라는 점**과 **자동화된 주석 생성 방식의 정확도 한계**는 향후 개선 과제로 남아있습니다.  따라서, **YT-Conversation 데이터셋은 에고중심 대화 시스템 연구에 있어 중요한 자원**이 될 수 있지만, 데이터셋의 특성을 고려한 적절한 사용 및 추가적인 정제 작업이 필요합니다.

#### Multimodal Analysis
본 논문에서 다루는 멀티모달 분석은 **시각(RGB) 및 청각(오디오)** 정보를 통합하여 화자의 발화 시점을 예측하는 데 초점을 맞추고 있습니다.  단순히 각 모달리티의 정보를 개별적으로 처리하는 것이 아니라, **두 모달리티의 상호작용 및 보완 관계**를 고려하여 더욱 정확하고 자연스러운 발화 시점 예측을 가능하게 합니다.  **특히, 시각 정보는 비언어적 단서** (예: 상대방과의 시선 접촉, 몸짓 등)를 포착하여 발화 시점을 예측하는 데 중요한 역할을 수행하고, 오디오 정보는 음성의 존재 유무 및 화자의 발화 여부를 확인하는 데 활용됩니다.  이러한 멀티모달 분석을 통해, **복잡하고 다이나믹한 실제 대화 상황**에서도 인간과 유사한 수준의 자연스러운 대화 흐름을 구현할 수 있습니다.  **실시간 처리**를 위한 온라인 처리 모델을 사용하여, 시스템이 지속적으로 환경을 관찰하고 동적으로 발화 시점을 결정하는 능력을 강조하고 있으며, **대규모 데이터셋**을 활용한 사전 학습을 통해 다양한 대화 상황에 대한 일반화 능력을 향상시키고 있습니다.  따라서, 논문의 멀티모달 분석은 단순한 기술적 접근을 넘어, 실제 상황에 적용 가능한 실용적인 모델 개발에 중요한 의미를 지닌다고 볼 수 있습니다.

#### Real-time Prediction
본 논문에서 제시된 실시간 예측(Real-time Prediction)은 **에고센트릭(Egocentric)** 관점에서의 대화 시스템에 초점을 맞추고 있습니다.  이는 **일반적인 셋업을 넘어 실제 자연스러운 대화 상황**에서의 발화 시점 예측이라는 어려움을 해결하기 위한 시도입니다.  **RGB 영상 처리와 음성 처리를 통합**, 상황 인지 능력을 향상시키고,  **지속적인 비정형 비디오 스트림**을 처리하여 **동적인 멀티스피커 환경**에 적응할 수 있도록 설계되었습니다.  실시간 처리의 핵심은 **과거와 현재 정보만을 사용**한다는 점이며, 이를 통해  **미래의 정보에 의존하지 않고 자연스러운 대화 흐름**에 따라 발화 시점을 예측합니다.  **다양한 데이터셋을 이용한 실험 결과**는 제안된 시스템의 효과성을 보여주는 동시에, **모달리티(Modality) 조합**과 **컨텍스트 길이**의 중요성을 강조합니다.  이는 단순한 발화 검출을 넘어, **인간다운 자연스러운 상호작용**을 추구하는 시스템의 핵심 기술이라고 할 수 있습니다.

#### Future Work
본 논문의 "향후 연구 방향"에 대한 심도있는 고찰은 **다양한 1인칭 시점 대화 데이터 확보**를 위한 노력을 강조해야 합니다. 현재 YT-Conversation 데이터셋은 다양성을 제공하지만, 진정한 1인칭 시점의 자연스러운 대화 데이터를 충분히 포착하지 못합니다. **더욱 풍부하고 다양한 1인칭 시점 대화 데이터 구축**을 통해 모델의 일반화 성능을 높이고, 다양한 상황에 대한 적응력을 향상시키는 것이 중요합니다. 또한, **개별 화자의 특징을 고려하는 모델** 개발이 필요합니다. 현재 모델은 화자의 개별적인 발화 패턴이나 경향을 명시적으로 고려하지 않지만, 이를 고려하면 발화 시점 예측의 정확도를 더욱 향상시킬 수 있을 것입니다. 마지막으로, **대규모 언어 모델과의 통합**을 통해 더욱 자연스럽고 다채로운 대화 생성 및 응답 능력을 향상시키는 연구를 진행하는 것이 중요한 향후 연구 과제가 될 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.14892/x2.png)

> 🔼 그림 2는 EgoSpeak 프레임워크의 개요를 보여줍니다. 각 시간 단계에서 모델은 다듬어지지 않은 시점 중심의 비디오 및 오디오 스트림을 처리하여 실시간으로 세 가지 범주(배경(음성 없음), 다른 사람이 말하는 중, 대상 화자(카메라 착용자)가 말하는 중)로 분류합니다. 이러한 확률은 아래쪽에 시각화되어 있으며, 모델은 가까운 미래의 프레임을 예상하고 대화형 에이전트의 사전적인 말하기 시작을 가능하게 합니다.  즉,  EgoSpeak 모델이 현재 시점의 비디오와 오디오 정보를 바탕으로 다음 몇 프레임 내에 자신(카메라 착용자)이 말할지, 다른 사람이 말할지, 아니면 아무도 말하지 않을지에 대한 확률을 계산하고, 그 결과를 바탕으로 실시간으로 말할 시점을 결정하는 과정을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Overview of the EgoSpeak framework. At each time step, the model processes an untrimmed egocentric video and audio stream, classifying them in real time into three categories: background (no speech), other person speaking, and target speaker (camera wearer) speaking. These probabilities are visualized at the bottom, where the model anticipates near-future frames and enables proactive speech initiation for conversational agents.
> </details>



![](https://arxiv.org/html/2502.14892/x3.png)

> 🔼 이 그림은 논문에서 사용된 어노테이션 방법을 보여줍니다.  대화의 전사(transcript)를 각 프레임에 대한 레이블로 변환하는 과정을 시각적으로 설명합니다. 회색은 배경, 주황색은 대상 화자(카메라 착용자)가 말하는 프레임, 보라색은 다른 사람이 말하는 프레임을 나타냅니다.  각 프레임은 이 세 가지 카테고리 중 하나에 속하는 one-hot 인코딩 레이블을 받습니다. 이는 모델이 실시간으로 음성 개시 시점을 예측할 수 있도록 돕습니다. 
> <details>
> <summary>read the caption</summary>
> Figure 3:  Converting Transcript to Per-Frame Labels. Colors indicate: gray - background, orange - target speaker speaking, purple - other speaker speaking. Labels are one-hot encoded for classification.
> </details>



![](https://arxiv.org/html/2502.14892/x4.png)

> 🔼 그림 4는 논문에서 사용된 YT-Conversation 데이터셋의 샘플 프레임들을 보여줍니다. YT-Conversation 데이터셋은 유튜브의 다양한 대화 시나리오(팟캐스트, 인터뷰, 비공식 대화 등)를 포함하며, 실제 세상의 다양한 대화 형식을 나타냅니다.  이 그림은 데이터셋의 다양성과 실제 대화 상황을 반영하는 다양한 유형의 영상들을 보여줌으로써,  EgoSpeak 모델의 훈련 및 평가에 사용된 데이터의 특징을 효과적으로 설명합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Sample frames from YT-Conversation dataset. The dataset includes a diverse range of conversational scenarios from YouTube, such as podcasts, interviews, and informal dialogues, representing various real-world conversation formats.
> </details>



![](https://arxiv.org/html/2502.14892/x5.png)

> 🔼 YT-Conversation 데이터셋에 포함된 비디오의 길이 분포를 보여주는 히스토그램입니다.  가로축은 비디오 길이(초)이고, 세로축은 해당 길이를 가진 비디오의 상대적 빈도를 나타냅니다.  EgoSpeak 모델은 온라인 방식으로 동작하기 때문에 900초를 넘는 긴 비디오 클립도 처리할 수 있다는 점을 강조합니다. 평균 길이는 약 372초, 표준편차는 약 244초로 다양한 길이의 비디오가 포함되어 있음을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Video duration distribution for YT-Conversation. Our online formulation allows the use of long video clips, some even exceeding 900 seconds.
> </details>



![](https://arxiv.org/html/2502.14892/x6.png)

> 🔼 그림 6은 Transformer 모델의 단기 및 장기 메모리 길이를 다르게 하여 발화 개시 시점 예측 성능을 비교한 그래프입니다.  단기 메모리에는 짧은 문맥 창을, 장기 메모리에는 긴 문맥 창을 사용했을 때 더 나은 결과를 얻을 수 있음을 보여줍니다.  즉, 최근의 짧은 대화 내용과 과거의 긴 대화 맥락을 모두 고려하는 것이 발화 시점 예측에 효과적임을 시각적으로 보여주는 그림입니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Utterance initiation prediction with varying transformer memory length. a shorter context window for short-term memory and a longer context window for long-term memory generally show better results.
> </details>



![](https://arxiv.org/html/2502.14892/x7.png)

> 🔼 그림 7은 EasyCom 데이터셋에서 제안된 EgoSpeak 모델의 정성적 결과를 보여줍니다. 각 라인은 모델의 예측 점수를 나타내고, 영역은 실제 정답 레이블을 나타냅니다. 파란색 선은 RGB 입력만 사용한 모델, 빨간색 선은 오디오 입력만 사용한 모델, 보라색 선은 오디오와 비주얼 입력을 모두 사용한 모델의 결과를 각각 보여줍니다. 이 그림은 다양한 입력 모드를 사용한 모델의 성능을 시각적으로 비교하여, 다중 모달 입력의 효과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Qualitative results on EasyCom. The predicted scores are shown in lines and the ground-truth label is shown in regions. The blue line represents a model with RGB input, the red line represents a model with audio input, and the purple line represents a model with audio and visual input.
> </details>



![](https://arxiv.org/html/2502.14892/x8.png)

> 🔼 그림 8은 Transformer 모델의 어텐션 가중치를 보여줍니다. Transformer 모델은 발화 개시를 위해 주로 지역적 맥락에 집중하는 것을 보여줍니다. 그림은 Transformer 인코더의 어텐션 가중치 분포를 보여주는 그래프입니다. 예측 프레임으로부터의 거리에 따른 가중치의 변화를 보여주며, 예측 프레임에 가까울수록 가중치가 높아지는 것을 확인할 수 있습니다. 이는 Transformer 모델이 발화 개시 시점 예측을 위해 최근 프레임의 정보에 더욱 집중한다는 것을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Attention weight of a transformer encoders. Transformer models focus on mostly local context for utterance initiation.
> </details>



![](https://arxiv.org/html/2502.14892/x9.png)

> 🔼 그림 9는 EasyCom 데이터셋에서 EgoSpeak 모델이 제대로 작동하지 않은 예시를 보여줍니다. 주황색 영역은 목표 화자(카메라 착용자)가 말하는 구간을 나타내고, 빨간색 영역은 목표 화자가 다른 화자의 말에 대한 반응으로 짧게 발화하는 구간(backchanneling)을 나타냅니다. 이 그림은 모델이 backchanneling과 같은 짧고 비정형적인 발화를 정확하게 예측하는 데 어려움을 겪을 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Failure case on EasyCom. The orange region represents the target speaker speaking, and the red region represents the target speaker’s backchanneling.
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