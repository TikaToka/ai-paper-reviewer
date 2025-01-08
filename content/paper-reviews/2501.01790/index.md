---
title: "Ingredients: Blending Custom Photos with Video Diffusion Transformers"
summary: "고품질 다중 ID 맞춤형 비디오 생성을 위한 혁신적인 프레임워크, Ingredients 소개!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Video Understanding", "🏢 Kunlun Inc.",]
showSummary: true
date: 2025-01-03
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.01790 {{< /keyword >}}
{{< keyword icon="writer" >}} Zhengcong Fei et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-07 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.01790" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.01790" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/ingredients-blending-custom-photos-with-video" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

최근 텍스트-비디오 합성 분야에서 비디오 확산 변환기 모델의 발전이 눈부시지만, **여러 사람의 얼굴을 일관되게 유지하면서 개인화된 비디오를 생성하는 것은 여전히 어려운 과제**입니다. 기존 방법들은 개별적인 미세 조정이 필요하거나, DiT 기반 모델에 적용이 어려운 한계를 가지고 있습니다.  

본 논문에서는 이러한 문제를 해결하기 위해 **Ingredients라는 새로운 프레임워크**를 제안합니다. Ingredients는 **얼굴 추출기, 다중 스케일 프로젝터, ID 라우터**의 세 가지 모듈로 구성되어 있으며, **미세 조정 없이 다수의 ID 사진을 통합하여 현실적이고 개인화된 비디오 생성**을 가능하게 합니다. 특히, **고안된 라우팅 메커니즘은 여러 ID 임베딩을 동적으로 조합하고 분배**하여 개별 ID의 특징을 유지하면서도 자연스러운 비디오를 생성하는 데 기여합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 비디오 확산 변환기를 이용하여 사용자 정의 사진을 동적인 개인화된 비디오 콘텐츠로 변환하는 새로운 프레임워크를 제시합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 다중 인물 식별을 유지하면서도 정확한 텍스트 제어 기능을 제공합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 다단계 훈련 프로토콜을 통해 우수한 성능을 달성하였으며, 데이터 및 코드를 공개하여 향후 연구에 기여합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **비디오 확산 변환기**를 이용한 **고품질의 다중 ID 맞춤형 비디오 생성**에 대한 새로운 방법론을 제시하여, 사용자 정의 사진을 동적인 개인화된 비디오 콘텐츠로 변환하는 분야에 크게 기여합니다. 이는 특히 **다중 인물 식별 유지 및 텍스트 제어 기능**을 결합하여 기존 방법의 한계를 뛰어넘는 획기적인 성과입니다. 따라서 비디오 생성, 개인화, 멀티미디어 기술 분야 연구자들에게 중요한 의미를 지닙니다.  **특히, 제한된 데이터 환경에서도 고품질의 비디오 생성을 가능하게 하는 훈련 방식**은 향후 연구에 대한 새로운 가능성을 열어줍니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.01790/extracted/6109222/precase.png)

> 🔼 본 그림은 제안된 Ingredients 방법을 사용하여 생성된 다중 ID 맞춤형 비디오 결과의 예시를 보여줍니다. 여러 인물의 이미지 집합을 참조하여, 제안된 방법은 특정 인물의 정체성을 유지하면서 사실적이고 개인화된 비디오를 생성할 수 있습니다. 각각의 비디오 클립은 여러 명의 인물을 포함하며, 각 인물의 얼굴 특징이 비디오 전체에서 일관되게 유지되는 것을 보여줍니다. 이는 제안된 방법이 복수의 인물을 포함하는 비디오 생성 시에도 정체성을 효과적으로 유지한다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Examples of multi-ID customized video results from our proposed Ingredients. Given a reference with multiple human image set, our method can generate realistic and personalized videos while preserving specific human identity consistent.
> </details>





{{< table-caption >}}
| Methods | Face Sim. ↑ (%) | CLIPScore ↑ (%) | FID ↓ | 
|---|---|---|---|
| CogvideoX | 2.8 | 28.3 | - |
| Inversion | 35.6 | 24.3 | 154.2 |
| Ingredients | 77.1 | 26.7 | 106.3 |{{< /table-caption >}}

> 🔼 표 1은 다중 인물 비디오 생성에 대한 제안된 방법과 기준 방법 간의 비교 결과를 보여줍니다.  CogvideoX는 비디오 조건 없이 텍스트만 사용하는 기준 방법으로 사용되었으며, Inversion은 미세 조정 기반 텍스트 반전 방법입니다.  표에는 각 방법의 얼굴 유사성, CLIP 점수, FID 점수가 포함되어 제안된 방법의 성능 우수성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Compare between our method and baseline approaches on multiple human video generation. Cogvideox served as the text-only baseline without any video conditioning while Inversion is tuning-based textual inversion.
> </details>





### In-depth insights


#### Multi-ID Customization
본 논문에서 다루는 다중 ID 맞춤화는 **비디오 확산 변환기(Video Diffusion Transformers)**를 이용하여 여러 개의 사용자 사진을 비디오에 통합하는 강력한 프레임워크를 제시합니다. 기존 방법들의 한계를 극복하고자, **훈련 없이(training-free)** 여러 인물의 얼굴 특징을 정확하게 추출하고, 이를 비디오의 적절한 공간-시간 영역에 동적으로 할당하는 모듈들을 제시합니다.  **얼굴 추출기(facial extractor), 다중 스케일 투영기(multi-scale projector), ID 라우터(ID router)**의 세 가지 주요 모듈을 통해 개별 ID의 일관성을 유지하면서도 다양한 콘텐츠 생성이 가능합니다. 특히, ID 라우터는 **분류 손실(classification loss)**을 활용하여 여러 ID 임베딩을 혼합하지 않고 각 영역에 적절히 분배하는 역할을 수행하며, 다중 ID 일관성을 유지하는 데 중요한 역할을 합니다. 이러한 기법은 기존의 단일 ID 맞춤화 방법보다 한 단계 발전된 것이며, **개인화된 동영상 콘텐츠 제작**에 있어 획기적인 발전을 가져올 것으로 예상됩니다.

#### Diffusion Transformer
본 논문에서 다루는 "Diffusion Transformer"는 **비디오 생성 분야의 혁신적인 아키텍처**입니다. 기존의 U-Net 기반 모델과 달리 순수 Transformer 구조를 사용하여 **뛰어난 스케일링 성능과 시계열 일관성**을 제공합니다. **공간-시간적 정보를 효과적으로 포착**하여 보다 사실적이고 자연스러운 비디오 생성을 가능하게 합니다. 특히, 본 연구에서는 다중 ID(identity) 사진을 활용한 비디오 개인화에 중점을 두고 있으며, 이를 위해 **얼굴 특징 추출, 다중 스케일 투영, ID 라우팅** 등의 모듈을 통해 개별 ID의 특징을 유지하면서 자연스럽게 결합하는 방법을 제시합니다. 이는 **기존 방법의 한계를 극복**하고, **보다 효과적인 생성적 비디오 제어 도구**를 제공하는 데 기여할 것으로 기대됩니다.

#### Ingredients Framework
본 논문에서 제시된 'Ingredients Framework'는 **다중 인물 식별(ID) 보존**을 위한 강력한 틀을 제공합니다. 이는 **얼굴 추출기, 다중 스케일 프로젝터, ID 라우터**라는 세 가지 주요 모듈로 구성됩니다. 얼굴 추출기는 다양한 각도에서 정확한 얼굴 특징을 포착하고, 다중 스케일 프로젝터는 얼굴 임베딩을 비디오 확산 트랜스포머의 문맥 공간으로 매핑합니다. ID 라우터는 시간-공간 영역에 걸쳐 다중 ID 임베딩을 동적으로 할당하여 **일관성 있는 다중 ID 보존**을 가능하게 합니다. **훈련 과정은 얼굴 임베딩 정렬 및 라우터 미세 조정 단계**로 구성되며, 효율적이고 정확한 비디오 생성 제어를 가능하게 합니다. 이러한 접근 방식은 기존 방법에 비해 향상된 성능과 유연성을 제공하며, **개인화된 동적 비디오 콘텐츠 생성**에 대한 중요한 진전을 의미합니다.

#### Ablation Experiments
본 논문에서 제시된 어떤 방법의 성능에 대한 깊이 있는 이해를 얻기 위해 **절제 실험(Ablation Experiments)**이 수행되었습니다. 이러한 실험은 모델의 특정 구성 요소 또는 하이퍼파라미터를 제거하거나 변경하여 그 영향을 평가함으로써 모델의 각 부분의 기여도를 파악하고, 전체적인 성능 향상을 위한 최적의 설계를 찾는 데 도움이 됩니다. **각 구성 요소의 상호 작용 및 중요성**을 밝히는 것이 목표입니다.  예를 들어, 특징 추출기, 프로젝터, 라우터 등의 모듈을 개별적으로 제거하거나 성능을 저하시켜 전체 성능에 미치는 영향을 정량적으로 분석합니다. 이를 통해 **각 모듈의 효과와 상호 연관성**을 규명하고,  모델의 강점과 약점을 명확하게 드러낼 수 있게 됩니다.  또한, 하이퍼파라미터 조정을 통한 성능 개선 여부를 확인하고, **최적의 하이퍼파라미터 설정**을 찾는 데 활용됩니다.  **절제 실험의 결과**는 최종 모델의 설계 및 성능 향상에 직접적으로 반영되어, 보다 효율적이고 강력한 성능을 가진 모델을 개발하는 데 중요한 역할을 합니다.  결과적으로, 절제 실험은 제안된 방법의 신뢰성과 일반화 성능을 높이는 데 기여하며,  **연구의 견고성을 높이는 데 중요한 절차**로써 기능합니다.

#### Future Directions
본 논문에서 제시된 Ingredients 프레임워크는 비디오 생성 분야에 큰 가능성을 보여주지만, **향후 연구 방향**은 다음과 같이 설정될 수 있습니다. 첫째, **다양한 ID 사진들의 효과적인 통합 및 관리**를 위한 더욱 발전된 얼굴 추출 및 라우팅 알고리즘 연구가 필요합니다. 현재의 방법은 다수의 ID를 처리하지만, 더 복잡한 시나리오나 고해상도 이미지 처리에 대한 성능 개선이 필요합니다. 둘째, **더욱 다양하고 풍부한 텍스트-비디오 데이터셋 구축**을 통해 모델의 일반화 능력을 향상시키는 연구가 필요합니다. 현재 사용된 데이터셋의 한계를 극복하고 다양한 스타일과 콘텐츠를 생성할 수 있도록 데이터의 질과 양을 개선해야 합니다. 셋째, **실시간 처리 성능 향상**을 위한 경량화된 모델 아키텍처 연구가 필요합니다. 현재의 모델은 상당한 컴퓨팅 자원을 필요로 하므로, 실제 애플리케이션 적용을 위해서는 모델 크기와 연산 속도를 개선해야 합니다. 마지막으로, **윤리적 및 사회적 문제**에 대한 고려가 필요합니다. 생성된 비디오의 오용 가능성을 줄이고 개인 정보 보호를 위한 기술적 및 정책적 방안을 마련해야 합니다. 이러한 미래 방향을 통해 Ingredients 프레임워크는 더욱 강력하고 유용한 비디오 생성 도구로 발전할 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.01790/extracted/6109222/framework.png)

> 🔼 그림 2는 제안된 Ingredients 프레임워크의 개요를 보여줍니다. 이 프레임워크는 세 가지 주요 모듈로 구성됩니다. 얼굴 추출기는 각 ID에 대해 다양하고 편집 가능한 얼굴 특징을 독립적으로 추출합니다. Q-Former 기반 프로젝터는 다중 스케일 얼굴 임베딩을 비디오 확산 트랜스포머의 여러 레이어에 매핑합니다. ID 라우터는 프롬프트나 레이아웃의 개입 없이 각 ID 임베딩을 해당 공간-시간 영역에 적응적으로 결합하고 분산시킵니다.  전체 훈련 과정은 얼굴 임베딩 정렬 단계와 라우터 미세 조정 단계의 두 단계로 구성됩니다. 그림은 각 모듈의 기능과 상호 작용을 시각적으로 보여주는 다이어그램을 포함합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Overview of Ingredients framework. The proposed method consists of three key modules: a facial extractor, a q-former-based projector, and an ID router. The facial extractor collects versatile editable facial features with a decoupling strategy for each ID. The q-former projector map multi-scale facial embedding into different layers of video diffusion transformers. The ID router combines and distributes ID embeddings to their respective locations adaptively without the intervention for prompts and layouts. The entire training process of the framework is curated into two stages, i.e., the facial embedding alignment stage and the router fine-tuning stage.
> </details>



![](https://arxiv.org/html/2501.01790/extracted/6109222/compare.png)

> 🔼 그림 3은 여러 사람 얼굴을 포함하는 비디오를 사용자 지정하는 데 있어 제안된 방법과 기존의 학습 기반 방법(텍스트 반전)의 성능을 정성적으로 비교한 결과를 보여줍니다.  본 논문의 방법은 텍스트 반전과 같은 학습 기반 방법과 비교했을 때, 각 사람의 얼굴 영역을 보다 명확하게 식별하고 해당 영역에 주의를 집중시켜, 개별 신원의 일관성을 유지하고 프롬프트를 더 잘 따르는 것을 보여줍니다.  다시 말해, 여러 사람의 얼굴이 혼합되지 않고 각 얼굴이 제대로 인식되면서, 사용자가 입력한 텍스트 프롬프트에 맞춰 비디오가 생성되는 것을 확인할 수 있습니다.  이는 제안된 방법의 우수성을 보여주는 중요한 시각적 증거입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Qualitative comparison of different personalization methods on multi-ID video customization. It can been seen that compared with training-based customization, i.e., textual inversion, our method can clearly routing and attention the respect regions, benefits to ID consistency as well as strong prompt following.
> </details>



![](https://arxiv.org/html/2501.01790/extracted/6109222/badcase.png)

> 🔼 그림 4는 다중 인물 사용자 지정의 추가적인 실패 사례들을 보여줍니다. 제안된 Ingredients 방법은 캐릭터가 복사-붙여넣기된 것처럼 보이거나 외부 페인팅이 발생하는 등의 실패를 포함하며, 이는 비일관적인 비디오 장면으로 이어집니다.  이는 다중 인물의 얼굴 특징들을 비디오에 효과적으로 통합하는 데 어려움을 겪는 것을 시각적으로 보여주는 예시입니다. 특히, 얼굴 영역의 일관성 유지, 자연스러운 움직임 생성, 전체적인 비디오 일관성 유지 측면에서 어려움을 드러냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Additional bad examples of multi-human customization. Our Ingredients involves failures that generated characters appearing as though they were directly copied-pasted and out-painting, leading to an inconsistent video scenes.
> </details>



![](https://arxiv.org/html/2501.01790/extracted/6109222/routing.png)

> 🔼 이 그림은 비디오 확산 트랜스포머의 각 크로스 어텐션 레이어 내에서 라우팅 맵을 시각화한 것입니다. 라우팅 손실을 사용하면 라우팅 네트워크가 이전 시간대에 서로 다른 사람 ID를 더욱 명확하게 구분할 수 있음을 보여줍니다. 그림은 여러 개의 크로스 어텐션 레이어에서 여러 프레임의 라우팅 결과를 보여주며, 각 픽셀은 특정 사람 ID를 나타냅니다. 시간이 지남에 따라 라우팅이 더욱 정확해지는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Visualization of routing map within each cross-attention layer of video diffusion transformers. We can see that with the routing loss, the routing network can discern different human IDs at earlier timesetps and in a more pronounced manner.
> </details>



![](https://arxiv.org/html/2501.01790/extracted/6109222/training.png)

> 🔼 그림 6은 라우터 미세 조정 단계에서의 다양한 손실 함수 훈련 곡선을 보여줍니다. 훈련 단계가 증가함에 따라 라우터 손실이 크게 감소하고, 라우터의 정확도가 향상되는 반면, 확산 손실은 거의 변하지 않아 원래의 생성 성능이 유지됨을 알 수 있습니다. 이는 라우터가 여러 ID를 효과적으로 식별하고 할당하여 생성된 비디오의 ID 일관성을 유지하는 데 성공했음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: The curve of different training loss in router fine-tuning stage. We can see that with training steps increases, routing loss significantly decreases, the router becomes more accurate, while the diffusion loss remains almost unchanged, maintaining the original generative performance.
> </details>



![](https://arxiv.org/html/2501.01790/extracted/6109222/sam.png)

> 🔼 그림 7은 SAM(Segment Anything Model)을 사용하여 라우팅을 위한 지도 학습 레이블을 생성하는데 사용된 하이퍼파라미터 설정을 보여줍니다.  SAM은 이미지 내의 모든 객체를 분할하는 것을 목표로 하는 강력한 모델입니다. 이 그림은 SAM의 임계값을 -2.0으로 설정하여 라우팅에 필요한 객체의 마스크를 생성하는 과정을 보여줍니다. 임계값을 조정함으로써, 원하는 수준의 정확도로 객체를 분할할 수 있으며, 이를 통해 보다 정확한 라우팅 결과를 얻을 수 있습니다.  이는 다중 ID 비디오 생성에서 각 ID의 영역을 정확하게 식별하고 할당하는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Hyper-parameter settings for SAM segmentaion. We select -2.0 as threshold to build routing supervised labels.
> </details>



![](https://arxiv.org/html/2501.01790/extracted/6109222/evaluate.png)

> 🔼 그림 8은 논문의 실험 설정에 대한 설명입니다. 왼쪽에는 평가에 사용된 이미지 데이터의 도메인 분포를 보여주고, 오른쪽에는 텍스트 입력 생성에 사용된 프롬프트의 예시를 보여줍니다. 다양한 측면을 고려하여 데이터를 수집함으로써 평가의 견고성을 높였음을 보여줍니다. 보다 구체적으로는, 이미지 데이터는 영화, 스포츠, 학술 장면 등 다양한 장르를 포함하며, 인물의 인종(흑인, 백인, 아시아인 등), 성별(남성-남성, 여성-남성, 여성-여성), 의상, 표정, 행동, 배경 등 다양한 속성을 고려하여 수집되었습니다.  텍스트 프롬프트는 이미지 데이터의 속성에 맞춰 세밀하게 작성되었습니다. 이를 통해, 평가의 일반화 능력과 신뢰도를 높일 수 있었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Domain distribution of evaluation images (left) and used prompt to generate text inputs (right). We consider multiple aspects for data collection to make evaluation more robust.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Initialize |  | Router Supervised |  | VAE Features |  | Metrics |  |  |  |
|---|---|---|---|---|---|---|---|---|---|
| T2V | I2V | Box | Seg. | After | Before | Face Sim. ↑ (%) | CLIP-T ↑ (%) | FID ↓ |  |
| ✓ |  |  | ✓ |  | ✓ | 58.1 | 26.5 | 122.5 |  |
|  | ✓ |  | ✓ | ✓ |  | 65.5 | 25.9 | 119.2 |  |
|  | ✓ | ✓ |  |  | ✓ | 74.3 | 26.7 | 110.4 |  |
|  | ✓ |  | ✓ |  | ✓ | 77.1 | 26.7 | 106.3 |  |{{< /table-caption >}}
> 🔼 표 2는 ID 임베딩과 제어 신호의 구성 요소에 대한 ablation 연구 결과를 보여줍니다.  I2V 초기화, 세그먼트 감독 및 VAE 이전 공간 연결을 모두 결합하면 다중 ID 일관성을 갖춘 최고의 생성 성능을 얻을 수 있습니다. 이 표는 다양한 구성 요소들을 제거하거나 변경했을 때 모델의 성능 변화를 보여줌으로써, 각 구성 요소의 중요성과 상호작용을 분석합니다.  특히 I2V 초기화, 세그먼트 감독 학습 및 VAE 전의 공간 연결의 중요성을 강조합니다. 각 열은 특정 구성 요소의 유무 또는 설정에 따른 얼굴 유사도, CLIP 점수, FID 점수를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Ablation studies for components in ID embedding and control signals. Combine all of I2V initialization, segment supervision and spacal concatenation before VAE provide a best generative performance with multi-ID consistency.
> </details>

{{< table-caption >}}
| Methods | Face Sim. ↑ (%) | CLIPScore ↑ (%) | FID ↓ | 
|---|---|---|---| 
| w/o $L_{route}$ | 62.2 | 26.9 | 112.3 | 
| w/ $L_{mse}$ | 72.5 | 26.1 | 109.5 | 
| w/ $L_{route}$ | 77.1 | 26.7 | 106.3 | {{< /table-caption >}}
> 🔼 표 3은 라우팅 손실이 다중 ID 일관성 있는 생성에 미치는 영향을 보여줍니다.  ID 분류를 위한 라우팅 손실을 사용하면 얼굴 유사도가 향상되고, CLIP 점수가 유지되며, FID 점수가 감소하는 것을 알 수 있습니다. 이는 라우팅 손실이 여러 ID를 가진 비디오 생성에서 개별 ID의 일관성을 유지하는 데 효과적임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Effect of routing loss. Equipped with routing loss of ID classification helps to build a multi-ID consistent generation.
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