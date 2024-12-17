---
title: "InstanceCap: Improving Text-to-Video Generation via Instance-aware Structured Caption"
summary: "InstanceCap: 인스턴스 인식 구조화 캡션을 통해 텍스트-비디오 생성을 개선합니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Video Understanding", "🏢 Nanjing University",]
showSummary: true
date: 2024-12-12
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.09283 {{< /keyword >}}
{{< keyword icon="writer" >}} Tiehan Fan et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-16 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.09283" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.09283" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/instancecap-improving-text-to-video" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

**텍스트-비디오 생성은 최근 몇 년 동안 급속도로 발전했지만 현재 비디오 캡션은 생성된 비디오의 충실도와 일관성에 영향을 미치는 세부 정보 부족, 환각 및 부정확한 동작 묘사로 어려움을 겪고 있습니다.** 기존 비디오 캡션 방법은 짧은 캡션, 밀도가 높은 캡션, 거친 수준의 구조화된 캡션의 세 가지 유형으로 분류될 수 있으며, 각각 고유한 한계가 있습니다. **이러한 문제를 해결하기 위해서는 캡션과 비디오 간의 높은 충실도와 캡션 콘텐츠의 정확성을 보장하는 것이 중요합니다.**

이 연구에서는 **인스턴스 인식 구조화 캡션 프레임워크인 InstanceCap**을 제안합니다. 이 프레임워크는 **인스턴스, 배경 및 카메라 움직임을 통합하는 구조**를 사용하여 처음으로 **인스턴스 수준 및 세분화된 비디오 캡션을 달성**합니다. **InstanceCap은 전역 비디오를 로컬 인스턴스로 변환**하고 **MLLM을 사용하여 밀도가 높은 프롬프트를 구조화된 구문으로 구체화하여 캡션의 충실도와 정확성을 향상**시킵니다. 또한, 학습을 위해 22K **InstanceVid** 데이터 세트가 선별되었으며 추론을 위해 맞춤화된 프롬프트 향상 파이프라인이 개발되었습니다. 실험 결과는 InstanceCap이 이전 모델보다 성능이 뛰어나 캡션과 비디오 간의 높은 충실도를 보장하고 환각을 줄이는 것으로 나타났습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} InstanceCap은 인스턴스 레벨 및 세분화된 비디오 캡션을 위한 새로운 프레임워크입니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} InstanceCap은 캡션과 비디오 간의 충실도를 향상시키고 환각을 줄입니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} InstanceVid는 InstanceCap을 학습하기 위해 선별된 22K 데이터 세트입니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**InstanceCap**은 현재 연구 동향과 관련하여 텍스트-비디오 생성의 충실도를 개선하는 데 중요한 의미를 지닙니다. **새로운 벤치마크와 향상된 평가 지표를 제공하여 인스턴스 레벨 세부정보를 생성하는 데 있어서 생성 모델의 기능을 평가하는 더 정확한 방법을 제시합니다.** 이는 향후 연구를 위한 새로운 길을 열어 더욱 사실적이고 정확한 비디오 생성 모델로 이어질 수 있고 비디오 생성 및 편집 응용 프로그램과 같은 실제 응용 프로그램에 영향을 미칠 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.09283/x1.png)

> 🔼 이 그림은 InstanceCap과 다른 캡션 방법을 사용하여 생성된 비디오의 비교를 보여줍니다. InstanceCap으로 생성된 비디오는 원본 비디오와 매우 유사하며, 높은 디테일 충실도를 보여줍니다. InstanceCap에서 생성된 캡션은 다른 캡션 방법과 비교하여 더 자세하고 정확한 설명을 제공합니다. 빨간색 원은 향상된 디테일을 강조 표시합니다. 아래 캡션은 각 캡션 방법의 성능을 보여줍니다. 빨간색은 잘못된 캡션, 파란색은 모호한 캡션, 녹색은 자세하고 정확한 비디오 설명을 나타냅니다. 모든 비디오는 Hailuo AI222https://hailuoai.com/video라는 동일한 비디오 생성 제품을 사용하여 생성되었으며, 이 제품의 강력한 프롬프트 준수 기능은 InstanceCap의 효과를 분명히 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Top: Comparison of the reconstruction-via-recaption results between 𝙸𝚗𝚜𝚝𝚊𝚗𝚌𝚎𝙲𝚊𝚙𝙸𝚗𝚜𝚝𝚊𝚗𝚌𝚎𝙲𝚊𝚙\mathtt{InstanceCap}typewriter_InstanceCap and state-of-the-art captioning methods for annotating the ground truth video. 𝙸𝚗𝚜𝚝𝚊𝚗𝚌𝚎𝙲𝚊𝚙𝙸𝚗𝚜𝚝𝚊𝚗𝚌𝚎𝙲𝚊𝚙\mathtt{InstanceCap}typewriter_InstanceCap produces results that more closely resemble the original video, showing greater detail fidelity (highlighted by the red circle). Bottom: The corresponding captions generated by 𝙸𝚗𝚜𝚝𝚊𝚗𝚌𝚎𝙲𝚊𝚙𝙸𝚗𝚜𝚝𝚊𝚗𝚌𝚎𝙲𝚊𝚙\mathtt{InstanceCap}typewriter_InstanceCap and others. Red denotes incorrect captions, blue represents ambiguous captions, and green indicates detailed and accurate descriptions of video. Specific visual hints are marked as A, B, and C for clarity. All videos are generated using the same video generation product, Hailuo AI222https://hailuoai.com/video, which has robust prompt-following capabilities, clearly highlighting the effectiveness of 𝙸𝚗𝚜𝚝𝚊𝚗𝚌𝚎𝙲𝚊𝚙𝙸𝚗𝚜𝚝𝚊𝚗𝚌𝚎𝙲𝚊𝚙\mathtt{InstanceCap}typewriter_InstanceCap.
> </details>





{{< table-caption >}}
| Captioning Methods | 3DVAE<sub>*score*</sub>↓ | CLIP<sub>*SenbySen*</sub>↑ | Avg. Length |
|---|---|---|---| 
| Panda-70M | 140.25 | 0.1956 | 13 words |
| ShareGPT4Video | 141.00 | 0.2132 | 191 words |
| LLaVA-Video-72B | 139.88 | 0.2060 | 102 words |
| MiraData(GPT-4o) | **137.50** | **0.2156** | 263 words |
| InstanceCap**(Ours)** | **134.25** | **0.2133** | 157 words |{{< /table-caption >}}

> 🔼 표 1은 비디오 재생성을 통해 다양한 캡션 모델의 성능을 정량적으로 비교한 결과를 보여줍니다. Panda-70M, ShareGPT4Video, LLaVA-Video-72B, MiraData(GPT-40) 및 제안된 InstanceCap(Ours)의 5가지 방법이 비교됩니다. 각 캡션 모델에서 생성된 캡션을 사용하여 CogVideoX-5b 모델로 비디오를 생성하고 원본 비디오와의 차이를 계산하여 성능을 평가합니다. 평가 지표로는 3DVAE 점수와 CLIP SenbySen 점수가 사용됩니다. 표에서 가장 좋은 결과는 굵게 표시되고 두 번째로 좋은 결과는 밑줄이 그어져 있습니다. 참고로 CogVideoX-5b는 최대 226개의 텍스트 토큰을 허용하며 초과되는 부분은 잘립니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Quantitative comparisons on reconstruction-via-recaption results. The best results are marked in bold, and the second-best are underscored. As a reference, CogVideoX-5b accepts 226226226226 text tokens, with any excess being truncated.
> </details>





### In-depth insights


#### InstanceCap Framework
**InstanceCap 프레임워크는 텍스트-비디오 생성에서 인스턴스 레벨의 디테일과 동작을 향상시키는 것을 목표**로 합니다. 핵심은 **인스턴스 인식 구조화 캡션**을 사용하여 비디오의 **세밀한 묘사**를 가능하게 하는 것입니다. 이 프레임워크는 **보조 모델 클러스터(AMC)**를 활용하여 글로벌 비디오를 개별 인스턴스로 분할하고, 각 인스턴스의 클래스, 외형, 동작, 움직임, 위치 등의 **상세 정보**를 추출합니다. 이렇게 추출된 정보는 **CoT(Chain-of-Thought) 파이프라인**을 통해 **MLLM(Multimodal Large Language Models)이 구조화된 문구**로 변환되어 캡션의 **충실도**를 높입니다. InstanceCap은 기존 캡션 방식과 달리 **환각 및 불필요한 내용을 줄여** 캡션과 비디오 간의 **높은 일관성**을 유지합니다. 또한, **InstanceVid 데이터셋을 통해 T2V 모델을 미세 조정**하여 **인스턴스 디테일 및 동작 생성의 정확도**를 향상시킵니다. **InstanceEnhancer는 추론 과정에서 짧은 프롬프트를 강화**하여 **사용자의 요구에 맞는 간결하고 풍부한 캡션 생성**을 지원합니다.

#### Instance-Aware Captions
**인스턴스 인식 캡션**은 이미지 또는 비디오의 특정 인스턴스에 대한 자세한 설명을 제공하는 것을 목표로 합니다. 이는 객체의 **클래스, 외관, 동작, 움직임 및 위치**와 같은 다양한 속성을 강조하여 이루어집니다. 이러한 캡션은 멀티미디어 콘텐츠 이해를 향상시키고 더 풍부하고 정확한 설명을 가능하게 합니다. 예를 들어, "빨간색 셔츠를 입은 남자가 공을 던진다."라는 단순 캡션 대신 인스턴스 인식 캡션은 "왼쪽에 있는 빨간색 셔츠를 입은 남자가 오른쪽에 서 있는 여자에게 농구공을 던진다."와 같이 더 자세한 정보를 제공할 수 있습니다. 이러한 세분화된 캡션은 컴퓨터 비전 작업, 특히 **객체 감지, 이미지 캡션 생성 및 텍스트-비디오 생성**에서 유용합니다. **인스턴스 인식 캡션을 사용하면 인스턴스 간의 관계를 더 잘 이해하고 더 정확하고 상황에 맞는 캡션을 생성**할 수 있습니다. 또한 **환각 및 관련 없는 콘텐츠 생성을 줄이는** 데 도움이 될 수 있습니다. 궁극적으로 인스턴스 인식 캡션은 인간과 기계 모두에게 더 풍부하고 유익한 멀티미디어 경험을 가능하게 합니다.

#### 22K InstanceVid Dataset
**InstanceVid 데이터셋은 22K개의 샘플로 구성된 고화질 비디오 데이터셋으로, 텍스트-비디오 생성(T2V) 모델 학습에 활용됩니다.** 샘플들은 최소 하나 이상의 **고강도 움직임**을 보이는 인스턴스를 포함하도록 선별되었으며, 인스턴스의 외형, 행동, 움직임 등에 대한 **상세한 설명**이 제공됩니다.  InstanceVid는 **실외 장면**과 **2-10초** 분량의 짧은 비디오를 중점적으로 다룹니다. 실외 장면의 균형있는 구성은 특정 환경 편향을 방지하고 다양한 시나리오에서의 모델 성능 향상을 목표로 합니다. 짧은 비디오는 과도한 장면 전환을 최소화하고, 오픈소스 T2V 모델의 최적화된 생성 범위에 맞춰 효율적인 학습을 지원합니다. InstanceVid는 **인스턴스 레벨**의 세부 정보와 움직임 일관성을 향상시켜 T2V 모델의 성능 향상에 기여합니다. **InstanceCap**이라는 새로운 캡션 구조와 결합하여 T2V 모델의 디테일 및 모션 액션 생성 정확도를 높입니다.

#### Reconstruction & T2V
**재구성(Reconstruction)**과 **텍스트-비디오 생성(T2V)**은 상호보완적인 관계를 형성하며, 서로의 발전에 기여합니다. 고품질 비디오 재구성은 T2V 모델 학습에 필요한 **정확한 데이터**를 제공하고, T2V는 재구성 기술의 **한계를 극복**하는 데 도움을 줄 수 있습니다. InstanceCap과 같은 **인스턴스 기반 구조화 캡션**은 재구성의 **충실도를 향상**시키고, T2V 모델이 **세부 사항과 움직임을 더 정확하게** 생성하도록 유도합니다. 향후 연구에서는 더 **대규모 데이터셋**과 **강력한 T2V 모델**을 활용하여 재구성 및 생성 품질을 더욱 향상시키는 데 집중해야 합니다.

#### Limitations & Future
**InstanceCap의 한계는 객체 감지 방법의 정확도에 의존한다는 점**입니다. 도메인별 인스턴스에 대해 감지 모델을 미세 조정해야 하며, 인스턴스가 없는 장면에서는 이점이 줄어듭니다. 또한, **InstanceVid 데이터 세트의 규모가 사전 훈련 데이터 세트로 사용하기에는 제한적**입니다. 향후 연구에서는 **더 큰 비디오 데이터 세트에 InstanceCap을 적용**하고 **더 강력한 T2V 모델을 훈련하여 그 영향을 확대**할 계획입니다. 이를 통해 인스턴스 레벨 세부 사항과 동작에 대한 생성 기능을 더욱 향상시킬 수 있을 것으로 기대됩니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.09283/x2.png)

> 🔼 InstanceCap 파이프라인의 개요를 보여주는 그림입니다. 전역 비디오를 지역 인스턴스로 변환하는 AMC 패러다임과, 상세 프롬프트를 구조화된 문구로 구체화하는 개선된 CoT 프로세스를 포함합니다. 'dense prompts에서 structured phrases로' 디자인에 대한 자세한 내용은 그림 3에 나와 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Overview of InstanceCap pipeline. Details of “from dense prompts to structured phrases” design are shown in Figure 3.
> </details>



![](https://arxiv.org/html/2412.09283/x3.png)

> 🔼 이 그림은 InstanceCap 파이프라인의 '밀집 프롬프트에서 구조화된 문구로' 디자인에 대한 세부 정보를 보여줍니다.  빨간색 화살표로 표시된 정보 상호 작용을 통해 MLLM이 속성에 대한 정확한 설명과 함께 인스턴스를 정확하게 캡처할 수 있도록 개선된 CoT 파이프라인을 제안합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Details on “from dense prompts to structured phrases” design. We propose an improved CoT pipeline with carefully designed information interactions (red arrow), which facilitates MLLMs to accurately capture instances with precise descriptions on attributes.
> </details>



![](https://arxiv.org/html/2412.09283/x4.png)

> 🔼 이 그림은 InstanceVid 데이터셋의 통계적 특성을 보여줍니다. InstanceVid는 다양한 인스턴스, 광범위한 장면, 정확하고 인스턴스 인식 캡션, 비디오 생성에 적합한 길이를 특징으로 하는 오픈 도메인 시나리오의 비디오에 대한 구 structured 캡션을 제공합니다. 그림 4는 장면(예: 토크쇼 및 인터뷰, 도시, 도시, 풍경 및 풍경)과 길이([0, 4], (4, 6), (6, 8), (8, 10), (10, 15), (15, 20), (20, 30), (30+))의 두 가지 주요 차원에서 InstanceVid의 분포를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: 𝙸𝚗𝚜𝚝𝚊𝚗𝚌𝚎𝚅𝚒𝚍𝙸𝚗𝚜𝚝𝚊𝚗𝚌𝚎𝚅𝚒𝚍\mathtt{InstanceVid}typewriter_InstanceVid provides structured captions for videos in open-domain scenarios, featuring diverse instance, expansive scenes, precise and instance-aware captions, and video-generation-friendly durations.
> </details>



![](https://arxiv.org/html/2412.09283/x5.png)

> 🔼 InstanceEnhancer는 두 단계로 구성된 튜닝 없는 접근 방식입니다. Stage A에서는 짧은 프롬프트를 자세한 긴 프롬프트로 확장합니다. Stage B(I)&(II)에서는 확장된 캡션과 원본 캡션을 모두 사용하여 특정 인스턴스를 분할하고 개선하여 상황별 일관성을 유지하는 동시에 정확한 인스턴스 식별을 보장합니다. InstanceEnhancer는 생성된 형식을 사용된 학습 입력에 해당하는 캡션과 일치하도록 엄격하게 제한하여 학습 및 추론 간의 프롬프트 불일치 문제를 해결합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: High-level overview of InstanceEnhancer, illustrating the data flow and the partitioning of stages. For a detailed implementation, refer to the supplemental materials, which provide an in-depth description of the enhancer pipeline design and the interdependencies between the stages.
> </details>



![](https://arxiv.org/html/2412.09283/x6.png)

> 🔼 이 그림은 InstanceCap과 MiraData의 비디오 재구성 성능을 비교합니다. InstanceCap은 원본 비디오와 재구성된 비디오 사이의 시각적 차이를 측정하는 지표인 3DVAE 점수에서 더 나은 성능을 보입니다. 빨간색 원과 선은 InstanceCap이 원본 비디오(GT)와 유사한 의미를 얼마나 잘 유지하는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Comparison on reconstruction-via-recaption between 𝙸𝚗𝚜𝚝𝚊𝚗𝚌𝚎𝙲𝚊𝚙𝙸𝚗𝚜𝚝𝚊𝚗𝚌𝚎𝙲𝚊𝚙\mathtt{InstanceCap}typewriter_InstanceCap and MiraData. Corresponding 3DVAE scores are also indicated. Similar semantics shared between 𝙸𝚗𝚜𝚝𝚊𝚗𝚌𝚎𝙲𝚊𝚙𝙸𝚗𝚜𝚝𝚊𝚗𝚌𝚎𝙲𝚊𝚙\mathtt{InstanceCap}typewriter_InstanceCap and GT are indicated by red circles and lines.
> </details>



![](https://arxiv.org/html/2412.09283/x7.png)

> 🔼 이 그림은 InstanceCap과 OpenSora의 단일 및 다중 동작 점수에 대한 시각적 비교를 보여줍니다. 비디오 생성의 동적 정도 측면에서 InstanceCap은 더 나은 일관성과 향상된 다중 인스턴스 동적 생성 효과를 보여줍니다. 즉, InstanceCap을 사용하여 생성된 비디오는 OpenSora보다 더 부드럽고 사실적인 움직임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Visual comparison of 𝙸𝚗𝚜𝚝𝚊𝚗𝚌𝚎𝙲𝚊𝚙𝙸𝚗𝚜𝚝𝚊𝚗𝚌𝚎𝙲𝚊𝚙\mathtt{InstanceCap}typewriter_InstanceCap and Opensora on Single and Multiple Action Score. In terms of the dynamic degree of video generation, we show better consistency and enhanced multi-instance dynamic generation effect.
> </details>



![](https://arxiv.org/html/2412.09283/x8.png)

> 🔼 인스턴스 디테일 및 환각 점수에 대한 사용자 연구 결과입니다. InstanceCap의 인스턴스 인식 구조화 캡션이 MiraData[9]의 대략적인 구조화 캡션보다 명확한 이점을 보여줍니다. 이 그래프는 InstanceCap과 MiraData에 대해 각각 4.60과 3.35의 인스턴스 디테일 점수와 4.12와 4.31의 환각 점수를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: User study on instance detail and hallucination scores. Our instance-aware structured caption shows clear advantages compared to the coarse-structured MiraData [9].
> </details>



![](https://arxiv.org/html/2412.09283/x9.png)

> 🔼 InstanceCap과 Open-Sora의 인스턴스 레벨 속성 비교. InstanceCap은 복잡한 다중 인스턴스 및 다중 속성 시나리오에서도 정확한 인스턴스 세부 충실도 및 명령 준수 기능이 뛰어납니다. 그림에서 InstanceCap은 '밝은 갈색 가방'과 같은 세부 사항을 정확하게 생성하는 반면 Open-Sora는 이러한 인스턴스를 놓칩니다.
> <details>
> <summary>read the caption</summary>
> Figure 9:  Visual comparison of 𝙸𝚗𝚜𝚝𝚊𝚗𝚌𝚎𝙲𝚊𝚙𝙸𝚗𝚜𝚝𝚊𝚗𝚌𝚎𝙲𝚊𝚙\mathtt{InstanceCap}typewriter_InstanceCap and Open-Sora on instance-level attributes. 𝙸𝚗𝚜𝚝𝚊𝚗𝚌𝚎𝙲𝚊𝚙𝙸𝚗𝚜𝚝𝚊𝚗𝚌𝚎𝙲𝚊𝚙\mathtt{InstanceCap}typewriter_InstanceCap excels in precise instance detail fidelity and instruction-following capabilities, even with complex multi-instance and multi-attribute scenarios.
> </details>



![](https://arxiv.org/html/2412.09283/x10.png)

> 🔼 그림 10은 InstanceCap에서 인간이 설계한 카메라 이동 힌트와 클래스 힌트의 영향을 보여주는 ablation study 결과를 나타냅니다. (a)는 카메라 이동 힌트가 MLLM 라벨링 정확도에 미치는 영향, (b)는 인간이 설계한 클래스 힌트가 인스턴스 라벨링 세부 사항에 미치는 영향을 보여줍니다. 카메라 이동 힌트는 '줌 인'처럼 간결한 프롬프트에서 '꾸준하고 점진적인 줌 인'과 같이 더 자세한 설명을 생성하는 데 도움이 됩니다. 클래스 힌트는 '나이 든 남자'에서 '중년 남성, 흰 머리, 데님 셔츠와 청바지 착용, 왼쪽 손목에 시계 착용'과 같이 인스턴스에 대한 더 풍부하고 정확한 설명을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: (a) Ablation study on the effect of camera movement hints on the accuracy of MLLM labeling. (b) Impact of human-designed class hints on the details of instance labeling.
> </details>



![](https://arxiv.org/html/2412.09283/x11.png)

> 🔼 이 그림은 InstanceCap 논문의 그림 11에 대한 설명입니다. (a)는 약한 시각적 프롬프트를 사용했을 때, 여러 인스턴스가 있는 대상에 대한 재구성 시각화를 비교한 것입니다. (b)는 빨간색 배경 화면을 사용했을 때 MLLM 라벨링 성능에 미치는 부정적인 영향을 비교한 것입니다. 약한 시각적 프롬프트는 여러 인스턴스가 있는 장면에서 특정 대상을 구별하고 설명하는 MLLM의 능력을 제한하여, 속성 혼합 및 모호한 주석을 초래합니다. 반대로, InstanceCap은 인스턴스별 특징 추출에 탁월하여 코치와 선수와 같은 그림을 정확하게 구분합니다. 단색 배경은 MLLM에 잘못된 컨텍스트를 제공하여 캡션에 부정적인 영향을 미칠 수 있습니다. InstanceCap에서 설계한 흐릿한 배경 마스킹 접근 방식은 자연스러운 장면과의 시각적 일관성을 유지하여 MLLM이 최소한의 프롬프트 지침만으로 정확하고 문맥적으로 관련된 주석을 생성할 수 있도록 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: (a) Comparison against the weak visual prompt for reconstruction-via-caption visualization on multi-instance targets. (b) Comparison against color screen backgrounds (red), which may negatively affect MLLM labeling performance.
> </details>



![](https://arxiv.org/html/2412.09283/x12.png)

> 🔼 Positive/Negative Lexicon은 생성된 비디오의 미적 품질을 향상시키기 위해 다양한 오픈 소스 모델 갤러리에서 프롬프트를 신중하게 수집하고 형용사를 추출하여 Positive Lexicon을 구축했습니다. 반대로, 강력한 LLM인 GPT-40을 사용하여 Negative Lexicon을 수동으로 구성하고 추가로 보강했습니다. 두 어휘집 모두 세심한 수동 심사를 거쳐 다듬어졌습니다. 그림 S1은 Positive/Negative Lexicon의 자세한 내용을 보여줍니다. 긍정적인 단어(kaleidoscopic, delicate, grand 등)는 비디오 생성에 도움이 되는 반면, 부정적인 단어(dull, rough, harsh 등)는 피해야 합니다.
> <details>
> <summary>read the caption</summary>
> Figure S1: The detail of Positive/Negative Lexicon
> </details>



![](https://arxiv.org/html/2412.09283/x13.png)

> 🔼 InstanceEnhancer 파이프라인의 상세 과정을 보여주는 그림입니다. 짧은 프롬프트가 주어지면, 먼저 LLMs를 사용하여 상세한 긴 프롬프트로 확장합니다. 그 후, 확장된 긴 프롬프트와 원본 짧은 프롬프트 모두를 사용하여 주요 인스턴스를 식별하고 분할합니다. 마지막으로, 분할된 인스턴스 정보와 긴 프롬프트를 기반으로 구조화된 캡션을 생성합니다. 그림 S9는 예시 번호 1을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure S2: Detailed overview of the InstanceEnhancer pipeline. Example No.1 as shown in Figure S9.
> </details>



![](https://arxiv.org/html/2412.09283/x14.png)

> 🔼 이 그림은 Inseval의 추론 예시들을 보여줍니다. 단일 및 다중 인스턴스에 대한 액션, 색상, 모양, 질감 및 세부 사항과 같은 다양한 차원의 예시를 제공합니다. 각 예시는 문장과 인스턴스 정보를 포함하는 JSON 형식으로 표현됩니다.
> <details>
> <summary>read the caption</summary>
> Figure S3: Inference examples of Inseval.
> </details>



![](https://arxiv.org/html/2412.09283/x15.png)

> 🔼 이 그림은 오픈 소스 모델과 상용 모델의 성능 비교를 보여줍니다. 특히, 여러 물체가 등장하고 복잡한 속성을 가진 프롬프트를 처리하는 데 있어서 상용 모델이 더 나은 성능을 보이는 것을 확인할 수 있습니다. 예를 들어, '사각형 스피커가 둥근 선반 위에 있다'와 같이 여러 속성을 가진 프롬프트에서 상용 모델은 모든 속성을 충실히 반영한 비디오를 생성하는 반면, 오픈 소스 모델은 속성을 제대로 반영하지 못하거나 일관성을 유지하지 못하는 경우가 있습니다. 또한, '녹색 이구아나가 등에 뾰족한 볏을 달고 바위 위에 있다. 근처에는 작은 조개 목걸이를 한 수달이 등에 떠 있다'와 같이 복잡한 장면을 묘사하는 프롬프트에서도 상용 모델이 더 나은 성능을 보입니다.
> <details>
> <summary>read the caption</summary>
> Figure S4: Visualization comparing open-source models and commercial models on prompts with poorer performance.
> </details>



![](https://arxiv.org/html/2412.09283/x16.png)

> 🔼 이 그림은 InstanceCap의 시스템 프롬프트를 보여줍니다. 이 프롬프트는 비디오 프레임 분석가의 페르소나를 설정하고 객체 외형, 동작, 섬세한 단어 사용, 제약 조건 등 다양한 능력을 명시합니다. 프롬프트는 객체의 색상 부분에 중점을 두고 사람에 대한 자세한 설명(예: 의복 스타일 및 색상, 나이, 성별, 체형, 표정 등)을 강조합니다. 또한 은유나 의인화와 같은 수사적 장치를 사용하지 않고 사실을 객관적으로 진술하며, 오디오 신호가 없으므로 소리 관련 측면은 제외하도록 지시합니다. 마지막으로 프롬프트는 현재 프레임의 프레임 번호와 타임스탬프를 언급하지 않고 구조화된 출력 형식을 엄격히 준수하도록 제약합니다.
> <details>
> <summary>read the caption</summary>
> Figure S5: System prompt of 𝙸𝚗𝚜𝚝𝚊𝚗𝚌𝚎𝙲𝚊𝚙𝙸𝚗𝚜𝚝𝚊𝚗𝚌𝚎𝙲𝚊𝚙\mathtt{InstanceCap}typewriter_InstanceCap.
> </details>



![](https://arxiv.org/html/2412.09283/x17.png)

> 🔼 InstanceCap 논문의 Figure S6는 비디오의 시간적 메타데이터를 가져오는 코드를 보여줍니다. 이 코드는 비디오의 길이, 프레임 수, 각 프레임의 타임스탬프 등의 정보를 추출하여 InstanceCap 모델이 시간적 맥락을 이해하는 데 도움을 줍니다. 이 정보는 비디오 캡션 생성 및 비디오-텍스트 정렬 작업에 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure S6: Code of getting video temporal metadata.
> </details>



![](https://arxiv.org/html/2412.09283/x18.png)

> 🔼 InstanceCap은 카메라 움직임을 구체적으로 설명하기 위해 CoT 프롬프트를 사용합니다. 만약 카메라 움직임이 'Undetermined'인 경우, 비디오의 변화를 바탕으로 카메라의 움직임과 촬영 각도를 추론하도록 MLLM에 지시합니다.  카메라 움직임이 'static'인 경우, 카메라가 정적인지 움직이는지, 그리고 비디오에서 카메라의 움직임과 촬영 각도가 무엇인지 추론하도록 MLLM에 지시합니다. 그 외의 경우, 주어진 카메라 움직임 정보를 바탕으로 카메라의 움직임과 촬영 각도를 추론하도록 MLLM에 지시합니다. MLLM은 'Sharply', 'rapidly', 'slowly' 등과 같은 정도 부부사를 적절히 사용하여 카메라 움직임과 촬영 각도에 대한 자세한 설명을 요약해야 합니다.
> <details>
> <summary>read the caption</summary>
> Figure S7: Prompt of camera movement.
> </details>



![](https://arxiv.org/html/2412.09283/x19.png)

> 🔼 이 그림은 행동과 움직임에 대한 프롬프트를 보여줍니다. 2단계 CoT 프롬프트가 제공됩니다. 1단계에서는 배경을 무시하고 대상 물체가 비디오에서 무엇을 하고 있는지 묻습니다. 2단계에서는 움직임 상태와 관련된 정보를 추출하고, 적절한 형용사를 사용하여 자세히 설명하도록 지시합니다. 또한 글머리 기호로 답하지 않고 대상 물체와 관련 없는 물체를 언급하지 않도록 합니다. 대상 물체가 있는 환경에 대한 추측이나 '흐릿한 배경'에 대한 언급도 하지 않도록 합니다.
> <details>
> <summary>read the caption</summary>
> Figure S8: Prompt of actions and motion.
> </details>



![](https://arxiv.org/html/2412.09283/x20.png)

> 🔼 이 그림은 LLMs를 위한 설계된 예시를 보여줍니다. 짧은 프롬프트 'Two wolves were hunting a rabbit in the snow.'에서 시작하여, 두 단계를 거쳐 더 자세한 프롬프트로 확장하는 과정을 보여줍니다. 첫 번째 단계(Stage A)에서는 주어진 짧은 프롬프트를 바탕으로 장면을 자세하게 묘사하는 긴 프롬프트를 생성합니다. 예시에서는 눈 덮인 숲에서 두 마리의 늑대가 토끼를 사냥하는 장면을 생생하게 묘사하고 있습니다. 두 번째 단계(Stage B(I))에서는 긴 프롬프트에서 주요 객체(instance)를 추출합니다. 여기서는 '늑대', '토끼'와 같이 장면이 아닌 만질 수 있는 개체를 추출하며, 여러 개체가 있을 경우 각각 분리하여 출력합니다. 이 예시에서는 'a wolf BREAK a wolf BREAK a rabbit' 과 같이 추출된 결과를 보여줍니다. 이러한 두 단계를 통해 짧은 프롬프트를 LLMs가 이해하고 활용하기 쉬운 형태로 변환하는 과정을 설명합니다.
> <details>
> <summary>read the caption</summary>
> Figure S9: Designed example for LLMs.
> </details>



![](https://arxiv.org/html/2412.09283/x21.png)

> 🔼 이 그림은 Inseval의 평가 프롬프트를 보여줍니다. 단일 객체 및 다중 객체 시나리오 모두에 대한 평가 프롬프트가 자세히 설명되어 있습니다. 'Detail' 차원에 대한 추가 프롬프트도 제공됩니다. 각 프롬프트는 MLLM이 생성된 비디오를 해당 차원과 일치시키는지 여부를 평가하기 위해 고안된 일반적인 CoT Q-A 쌍 형식을 따릅니다.
> <details>
> <summary>read the caption</summary>
> Figure S10: Evaluation prompts of Inseval.
> </details>



![](https://arxiv.org/html/2412.09283/x22.png)

> 🔼 Open-Sora 모델을 위한 정렬 프롬프트의 예시입니다. 이 프롬프트는 두 단계로 이루어져 있습니다. 1단계에서는 InstanceCap JSON을 연속적인 텍스트 단락으로 요약하도록 지시합니다. 2단계에서는 LLMs에 더 정확한 지침을 제공하기 위해 특별히 고안된 여러 가지 예시를 보여줍니다. 주어진 InstanceCap JSON을 바탕으로, 2단계 프롬프트를 사용하여 LLMs이 원본 비디오의 핵심 내용과 중요한 세부 사항을 모두 유지하는 연속적인 텍스트 단락을 생성하도록 유도합니다.
> <details>
> <summary>read the caption</summary>
> Figure S11: Aligning prompt used during alignment with the open source model.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| T2V Model | Single↑ | | | | | Multiple↑ | | | Average↑ |
|---|---|---|---|---|---|---|---|---|---|
|  | Action | Color | Shape | Texture | Detail | Action | Color | Texture |  |
| CogVideoX-5B [30] | 64% | 60% | 44% | 60% | 20% | 8% | 48% | 40% | 43.00% |
| Pyramid-Flow-2B [8] | 44% | 68% | 32% | 32% | 7% | 4% | 24% | 16% | 28.38% |
| Open-Sora Plan v1.3-2.7B [11] | 64% | 44% | 36% | 32% | 27% | 20% | 32% | 12% | 33.38% |
| Open-Sora v1.2-1.1B [35] | 40% | 56% | 36% | 40% | 13% | 12% | 16% | 16% | 28.63% |
| + \mathtt{InstanceCap} (Ours) | **56%** | **60%** | **40%** | **48%** | **27%** | **16%** | **32%** | **24%** | **37.88%** |
| + Panda-captioner [4] | 40% | 48% | 28% | 40% | 20% | 8% | 20% | 12% | 27.00% |
| + ShareGPT4Video [3] | 40% | 44% | 32% | 24% | 13% | **16%** | 8% | **20%** | 24.63% |
| + LLaVA [16] | **52%** | 52% | 28% | 28% | **20%** | 12% | **28%** | 16% | **29.50%** |{{< /table-caption >}}
> 🔼 표 2는 InstanceCap과 최신 비디오 캡션 모델들을 비교한 정량적 분석 결과를 보여줍니다. 모든 모델은 널리 사용되는 T2V 모델인 Open-Sora를 기반으로 합니다. 또한 CogVideoX-5B, Pyramid-Flow, Open-Sora Plan과 같은 세 가지 강력한 T2V 모델과도 비교합니다. 비디오 캡션 방법과 Open-Sora에서 가장 좋은 결과는 굵게 표시하고 두 번째로 좋은 결과는 밑줄을 긋습니다. 이 표는 InstanceCap을 사용한 fine-tuning이 Open-Sora의 성능을 향상시키는 것을 보여줍니다. 특히 InstanceCap은 복잡한 인스턴스 세부 정보를 캡처하는 능력에서 다른 캡셔닝 방법보다 우수합니다. 또한 InstanceCap은 CogVideoX와 같은 더 큰 모델과 비슷한 성능을 보입니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Quantitative comparison between 𝙸𝚗𝚜𝚝𝚊𝚗𝚌𝚎𝙲𝚊𝚙𝙸𝚗𝚜𝚝𝚊𝚗𝚌𝚎𝙲𝚊𝚙\mathtt{InstanceCap}typewriter_InstanceCap and SOTA video captioning models, all based on the popular T2V model Open-Sora. Additionally, we also compare three powerful T2V models, including CogVideoX-5B, Pyramid-Flow, and Open-Sora Plan. The best results of video captioning methods and Open-Sora are marked in bold, and the second-best are underscored.
> </details>

{{< table-caption >}}
| Distortion type | 3DVAE score↓ | Setting | 
|---|---|---| 
| **Blurring** | 7.71 | GaussianBlur(kernel=(5, 5), sigma=0) | 
| **Compression artifacts** | 11.19 | JPEG compression (quality 5-30) | 
| **Corruptions** | 39.80 | Random pixel masking (binary mask) | 
| **Random noise** | 49.70 | Gaussian noise (mean=0, stddev=25) | 
| **Brightness distortion** | 63.25 | Scaling (factor 0.5-1.5) | 
| **Spatial shifts** | 78.94 | Random affine shifts (±10 pixels) | 
| **T2V models Avg.** | 134 ~ 145 | - | 
| **Broken video** | 149.50 | - |{{< /table-caption >}}
> 🔼 표 S1은 다양한 왜곡 유형과 비디오 모델에 대한 3DVAE 점수를 보여주며, 지각적 유사성과 재구성 정확도를 포착하는 데 있어서의 효과를 보여줍니다. 설정 열은 각 왜곡 유형에 대한 실험 설정의 세부 정보를 제공합니다. 3DVAE 점수는 원본 비디오와 재구성된 비디오 간의 차이를 측정하며, 낮은 점수는 더 높은 유사성과 더 나은 재구성 품질을 나타냅니다. 표에는 블러링, 압축 아티팩트, 손상, 임의 노이즈, 밝기 왜곡, 공간 이동 및 깨진 비디오와 같은 다양한 왜곡 유형이 나열되어 있으며 각각에 대한 3DVAE 점수가 제공됩니다. 또한 여러 T2V 모델에 대한 평균 3DVAE 점수 범위도 표에 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table S1: 3DVAE scores for various distortions and video models, showcasing its effectiveness in capturing perceptual similarities and reconstruction accuracy. The setting column provides details of the experimental setup for each distortion type.
> </details>

{{< table-caption >}}
| Instance Detail | Instance Detail | Hallucination Scores | Hallucination Scores |
|---|---|---|---| 
| **1** | Descriptions are extremely vague, imprecise, or largely inaccurate. Almost no specific details from the video are captured correctly. | **1** | Severe hallucination - Describes many nonexistent details, significantly misrepresents what is shown, or introduces extensive irrelevant content with many unrelated topics or external information. |
| **2** | Descriptions have major inaccuracies or omit many important details. Only a few basic elements are described correctly. | **2** | Frequent hallucination - Multiple instances of fabricated or misrepresented details and significant extra content introducing information beyond the video scope. |
| **3** | Descriptions are moderately accurate but lack precision in some areas. Core details are present but some secondary details are missing or incorrect. | **3** | Occasional hallucination - A few minor instances of fabricated details, misrepresentations, or the addition of extra content not covered in the video. |
| **4** | Descriptions are largely accurate and detailed. Most key elements and nuances from the video are captured correctly, with only minor omissions or imprecisions. | **4** | Minimal hallucination - One or two very minor discrepancies or limited introduction of external information. |
| **5** | Descriptions are highly precise and comprehensive. All important details from the video are captured accurately, including subtle elements and specific examples. | **5** | No hallucination - All described details accurately reflect what is shown in the video, with no external content added. |{{< /table-caption >}}
> 🔼 표 S2는 인스턴스 세부 정보 및 환각 점수에 대한 채점 기준을 설명하고 내부 및 외부 환각을 통합 평가 프레임워크에 통합합니다. 인스턴스 세부 정보는 텍스트가 비디오의 세부 정보를 얼마나 정확하게 설명하는지를 평가합니다. 환각 점수(HS)는 텍스트가 비디오에 없는 내용을 얼마나 많이 도입하는지 평가하고, 본질적 환각(비디오에 있는 내용에 대한 환각)과 외적 환각(비디오에 없는 내용에 대한 환각)을 모두 포함합니다.
> <details>
> <summary>read the caption</summary>
> Table S2: This table outlines scoring criteria for Instance Detail and Hallucination Scores, integrating intrinsic and extrinsic hallucinations into a unified framework for evaluation.
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