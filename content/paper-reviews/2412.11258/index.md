---
title: "GaussianProperty: Integrating Physical Properties to 3D Gaussians with LMMs"
summary: "GaussianProperty는 LMM을 사용하여 3D 가우시안에 물리적 속성을 통합하는 훈련 없는 프레임워크로, 물리 기반 시뮬레이션 및 로봇 쥐기와 같은 다운스트림 작업을 가능하게 합니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "3D Vision", "🏢 Hong Kong University of Science and Technology",]
showSummary: true
date: 2024-12-15
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.11258 {{< /keyword >}}
{{< keyword icon="writer" >}} Xinli Xu et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-17 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.11258" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.11258" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/gaussianproperty-integrating-physical" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

시각 데이터에서 물리적 속성을 추정하는 것은 컴퓨터 비전, 그래픽 및 로봇 공학에서 중요한 작업으로, 증강 현실, 물리 기반 시뮬레이션 및 로봇 쥐기와 같은 다양한 분야의 토대를 마련합니다. 그러나 레이블이 지정된 Ground-truth 데이터를 얻는 어려움, 예측 작업의 모호성 및 관찰 가능한 표면의 제한된 수로 인해 물리적 속성 추정은 여전히 어려운 과제입니다.

이 논문에서는 **LMM(Large Multimodal Models)**과 **SAM(Segment Anything)**을 사용하여 3D 가우시안에 물리적 속성을 할당하는 **훈련 없는 프레임워크인 GaussianProperty**를 제안합니다. **GPT-4V(ision)의 인식 기능을 활용하여 2D 이미지에서 물리적 속성을 추정하고, 전역-지역 물리적 속성 추론 모듈을 사용하여 다양한 구성 요소의 속성을 정확하게 식별**합니다. 그런 다음 다중 뷰 재구성 접근 방식과 투표 전략을 사용하여 이러한 속성을 3D 가우시안에 투영합니다. 이러한 주석이 달린 3D 가우시안은 물리 기반 동적 시뮬레이션 및 로봇 쥐기와 같은 다운스트림 작업을 용이하게 합니다. **이 방법은 재료 분할, 물리 기반 동적 시뮬레이션 및 로봇 쥐기를 포함한 광범위한 실험을 통해 검증**되었으며, 최첨단 성능과 다운스트림 작업에 대한 이점을 보여줍니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} GaussianProperty는 LMM과 SAM을 활용하여 3D 가우시안에 물리적 속성을 할당하는 훈련 없는 프레임워크입니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 물리적 속성 주석이 달린 3D 가우시안은 물리 기반 동적 시뮬레이션 및 로봇 쥐기와 같은 다운스트림 작업에 사용할 수 있습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 이 프레임워크는 다양한 재료, 동적 시뮬레이션 및 실제 로봇 쥐기 실험에서 효과적임이 입증되었습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**3D 모델에 물리적 속성을 통합하는 것은 AR, 로봇 공학, 시뮬레이션과 같은 다양한 분야에서 중요하지만, 본질적인 모호성으로 인해 어려움을 겪고 있습니다.** 이 논문은 이러한 문제를 해결하는 훈련 없이 3D 가우시안에 물리적 속성을 할당하는 새로운 프레임워크인 GaussianProperty를 제시합니다. **이 연구는 대규모 다중 모드 모델(LMM)을 활용하여 물리적 속성 추정을 위한 새로운 길을 열어줍니다.** 또한 물리 기반 동적 시뮬레이션 및 로봇 쥐기와 같은 다운스트림 작업을 위한 잠재적 응용 프로그램을 강조하여 추가 연구 및 개발을 위한 길을 열었습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.11258/x1.png)

> 🔼 GaussianProperty는 LMM의 도움을 받아 3D 가우시안에 물리적 속성을 추가하는 학습 없는 프레임워크입니다. 3D 가우시안에 물리적 속성을 할당함으로써 물리 기반 생성 역학 및 로봇 파지와 같은 여러 다운스트림 작업을 촉진합니다. 그림은 입력으로 다중 뷰 이미지를 사용하고 SAM을 사용하여 분할 맵을 생성한 다음 LMM을 사용하여 물리적 속성을 예측하는 방법을 보여줍니다. 그런 다음 이러한 속성이 3D 가우시안에 투영되어 물리 기반 시뮬레이션 및 로봇 파지와 같은 애플리케이션에 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  GaussianProperty is a training-free framework, aiming at adding physical properties to 3D Gaussians with the assistance of LMMs. By assigning physical properties to 3D Gaussians, it promotes several downstream tasks such as physical-based generative dynamics and robot grasping in this work.
> </details>





{{< table-caption >}}
| · Method | ABO dataset |       |       |       |        |        | MVImgNet |           |          |        |        |        |        |        |          |       |        |
| :------- | :---------- | :---- | :---- | :---- | :----- | :----- | :------- | :-------- | :------- | :----- | :----- | :----- | :----- | :----- | :------- | :---- | :----- |
|         | Wood        | Metal | Plastic | Fabric | Ceramic | Average | Wood      | Metal     | Plastic   | Glass   | Fabric   | Foam    | Food    | Ceramic   | Paper   | Leather | Average |
| Nerf2phycics | 27.87      | 13.01 | 8.38   | 40.26  | 38.44   | 25.59   | 6.39     | 3.63      | 6.70     | 1.15    | 1.11    | 0.38   | 2.40   | 6.54     | 6.73    | 5.20   | 4.02    |
| Ours      | **61.53** | **33.41** | **38.26** | **67.57** | **78.40** | **55.83** | **41.96** | **38.85** | **39.50** | **18.87** | **27.12** | **23.18** | **84.89** | **19.74** | **30.23** | **23.96** | **34.83** |{{< /table-caption >}}

> 🔼 NeRF2Physics [46] 와 ABO 및 MVImgNet 데이터 세트의 다양한 범주에서 재료 분할 비교. 저희 방법은 객체를 더욱 포괄적이고 정확하게 이해하고 더욱 정밀한 재료 분할을 달성합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparison of material segmentation with NeRF2Physics [46] across different categories on ABO and MVImgNet dataset. Our method achieves a more comprehensive and accurate understanding of the object and achieve more precise material segmentation.
> </details>





### In-depth insights


#### 3D Gaussian Properties
**3D 가우시안 속성**은 3D 장면을 나타내는 강력한 방법으로, 각 가우시안은 중심, 공분산, 모양과 외관에 대한 추가 정보를 인코딩합니다. 이러한 속성은 **물리 기반 시뮬레이션**과 같은 다운스트림 작업에 매우 중요합니다. 예를 들어, **강성** 및 **밀도**와 같은 재료 속성을 3D 가우시안에 할당하면 사실적인 물리적 상호 작용을 시뮬레이션할 수 있습니다. 또한, **질량**, **부피**, **마찰 계수**와 같은 속성은 **로봇 파지**에 유용하여 로봇이 다양한 재료와 모양의 물체를 효과적으로 파지하는 데 필요한 힘을 추정할 수 있습니다. 또한 3D 가우시안을 사용하여 물체의 **표면 속성**(예: **거칠기**, **질감**)을 나타낼 수 있어 햅틱 피드백과 같은 응용 분야에 유용할 수 있습니다. **3D 가우시안의 속성을 풍부하게 하면** 장면 이해가 향상되고 로봇 공학 및 시뮬레이션과 같은 다양한 응용 분야에 대한 새로운 가능성이 열립니다.

#### LLM-Driven Physics
**LLM 기반 물리 엔진**은 3D 모델에 물리적 속성을 부여하여 시뮬레이션과 로봇 조작을 향상시키는 새로운 패러다임입니다. 이는 전통적인 방법과 달리 데이터 기반 접근법을 사용하여 사전 지식 없이도 다양한 재료의 물리적 특성을 예측합니다.  **SAM과 GPT-4V**의 조합은 객체의 부분별 분할 및 속성 매칭을 가능하게 하여 복잡한 장면에서도 정확한 물리적 속성 추정을 가능하게 합니다. **멀티뷰 투영 및 투표 전략**을 통해 2D 이미지에서 추출된 정보를 3D 가우시안으로 통합하여 일관성 있는 3D 표현을 생성합니다. 이러한 통합된 물리적 속성은 **물리 기반 동적 시뮬레이션과 로봇 grasping**에서 그 효과를 발휘합니다. 특히, 로봇 grasping에서는 LLM 기반 물리 엔진을 통해 재료에 따른 최적의 grasping force를 예측하여 안정적인 grasping을 가능하게 합니다. 하지만, 모호한 표면 질감을 가진 객체의 경우 정확한 재료 분류가 어려울 수 있다는 한계점이 있습니다. 향후 연구에서는 이러한 한계점을 해결하고 다양한 재료와 물리적 특성을 포괄하는 보다 포괄적인 물리 엔진 개발이 기대됩니다.

#### Robotic Grasping
**로봇 파지**는 시각적 입력만으로 물체의 구성 재료를 예측하고 그에 따른 물리적 특성을 추정하여 물체에 맞는 파지력을 적용하는 기술입니다. 이는 **재료에 따라 파지력을 조정해야 하는** 어려움을 해결하여 **다양한 재료의 물체를 효과적으로 파지**할 수 있게 합니다. 기존의 고정된 파지력 접근 방식은 **다양한 재료와 특성을 가진 물체에 대한 일반적인 적용에 한계**가 있었습니다.  GaussianProperty는 **SAM의 분할 기능과 GPT-4V의 인식 기능을 결합**하여 물체의 재료와 물리적 특성을 **정확히 예측**하고, **MPM을 활용하여 물리 기반 동역학 시뮬레이션을 통해 현실적인 파지 과정을 구현**합니다. 또한, 파지력 예측 모듈을 통해 물체의 변형을 방지하고 안정적인 파지를 위한 **최적의 힘 범위를 추정**합니다. 이러한 접근 방식은 **로봇 및 산업 응용 분야 전반에 폭넓게 적용**될 수 있는 **잠재력**을 가지고 있습니다.

#### Dynamic Simulation
**동적 시뮬레이션**은 물리적 속성을 3D 모델에 통합하여 사실적인 움직임과 상호 작용을 생성하는 핵심 기술입니다. 이 연구에서는 **가우시안 속성**이라는 새로운 방법을 통해 멀티뷰 2D 이미지에서 추정된 물리적 속성을 3D 가우시안에 할당하여 동적 시뮬레이션을 향상시킵니다. 기존 방법은 물리적 속성을 수동으로 할당해야 하는 비효율성이 있었지만, 가우시안 속성은 이러한 과정을 자동화하여 시뮬레이션 시간을 단축하고 복잡한 환경에서의 확장 가능한 응용을 가능하게 합니다. **물질점법(MPM)**을 활용하여 사실적인 물리적 상호작용을 구현하고, 예측된 속성을 시뮬레이션에 직접 적용하여 **생성적 다이내믹스**라는 새로운 가능성을 제시합니다. 이는 힘에 따른 물체의 움직임과 변형을 사실적으로 시뮬레이션하는 데 기여하며, 다양한 분야에서의 응용 가능성을 보여줍니다.

#### Ambiguity Limits
**모호성 제한**은 물리적 특성 추정의 주요 과제입니다. 시각적 정보만으로는 물체의 고유한 물리적 특성을 확실하게 파악하기 어려운 경우가 많습니다. 예를 들어, 같은 모양과 색상의 물체라도 재질이 다르면 무게나 밀도가 다를 수 있습니다. 또한, 물체의 표면이 제한적으로 보이는 경우, 가려진 부분의 특성을 추정하기가 더욱 어려워집니다. 이러한 모호성은 **학습 데이터 부족과 결합**되어 문제를 더욱 악화시킵니다. 물리적 특성에 대한 정확한 레이블이 지정된 데이터를 수집하는 것은 어렵고 비용이 많이 들기 때문에, 기존의 지도 학습 방법을 적용하기가 어렵습니다. 따라서 **모호성을 해결**하고 **데이터 부족을 완화**하는 효과적인 방법을 개발하는 것이 물리적 특성 추정의 핵심입니다. 이를 위해 다양한 시각적 단서와 사전 지식을 활용하고, 멀티모달 정보를 통합하는 방법 등이 연구되고 있습니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.11258/x2.png)

> 🔼 GaussianProperty의 전체 파이프라인은 먼저 SAM을 사용하여 객체의 분할 맵을 얻습니다. 그런 다음 원본 이미지와 마스크를 GPT-4V(ision)과 같은 파운데이션 모델로 보내 재료 후보를 질의하여 해당 물리적 속성을 얻습니다. 2D 이미지에서 물리적 속성을 획득한 후 다중 뷰 접근 방식과 투표 전략을 사용하여 재구성된 3D 가우시안에 물리적 속성을 추가합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Overall pipeline. Our Gausssian-Property initially leverages SAM to get the segmentation map of the object. Then the original images and the masks are sent to the foundation models like GPT-4V(ision) to get the corresponding physical properties by inquiring the material candidates. After acquiring physical properties from 2D images, we using a multi-view approach and a voting strategy to add physical properties to the reconstruction 3D Gaussians.
> </details>



![](https://arxiv.org/html/2412.11258/x3.png)

> 🔼 이 그림은 GPT-4V(ision)이 전역 및 부분 이미지 입력만으로 재질을 인식하는 데 어려움을 겪는다는 것을 보여줍니다(왼쪽). 그러나 전역-지역 정보와 연계를 결합하면 구성 요소의 속성을 정확하게 특징짓습니다(오른쪽). 왼쪽 이미지에서는 덤벨 전체 이미지와 손잡이 부분 이미지를 입력으로 제공했을 때 GPT-4V가 재질을 제대로 인식하지 못합니다. 오른쪽 이미지에서는 덤벨 전체 이미지, 손잡이 부분이 빨간색으로 강조된 분할 이미지, 손잡이 부분 이미지를 함께 입력으로 제공했을 때 GPT-4V가 손잡이 재질을 금속으로 정확하게 인식하는 것을 보여줍니다. 이는 전역-지역 정보와 연계를 활용하여 LMM의 인식 능력을 향상시키는 방법을 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Left: GPT-4V(ision) struggles to recognize the material when directly provided with both global and partial image inputs. Right: Enhanced with combined global-local information and association, the agent accurately characterizes the component’s properties.
> </details>



![](https://arxiv.org/html/2412.11258/x4.png)

> 🔼 이 그림은 GaussianProperty가 다양한 객체에 대해 재료 분할을 수행한 결과를 보여줍니다. 각 객체의 부분별로 어떤 재료로 구성되어 있는지 예측한 결과를 시각적으로 표현하고 있습니다. 예측된 재료는 색상으로 구분되어 있으며, 경계가 명확하게 표시되어 높은 정확도를 보여줍니다.  제시된 예시들은 나무, 금속, 플라스틱, 고무, 천 등 다양한 재료를 포함하고 있으며, GaussianProperty가 복잡한 형태의 객체도 정확하게 분할할 수 있음을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Qualitative results of Material Segmentation. Our model makes boundary-accurate physical material predictions.
> </details>



![](https://arxiv.org/html/2412.11258/x5.png)

> 🔼 이 그림은 물리적 속성을 가진 3D 가우시안의 다운스트림 작업인 생성 역학을 보여줍니다. 힘을 가하면 3D 가우시안은 그에 상응하는 움직임을 생성합니다. 예를 들어 첫 번째 행에서 의자에 위에서 아래로 힘을 가했을 때 가해진 힘에 따라 의자가 움직이는 것을 보여줍니다. 의자, 베개, 쓰레기통과 같은 다양한 물체에 대한 시뮬레이션 결과가 표시됩니다. 정적 상태의 물체에 힘을 가하면 물리 기반 시뮬레이션을 통해 물체가 움직이거나 변형됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Generative Dynamics. We present a potential downstream task of 3D Gaussians with physical property, i.e., the generative dynamics. By imposing force, the 3D Gaussians generate corresponding motion. For example, in the first row, we applied a top-down force, the chair exhibited a movement corresponding to the applied force.
> </details>



![](https://arxiv.org/html/2412.11258/x6.png)

> 🔼 이 그림은 GaussianProperty를 로봇 파지 작업에 적용한 결과를 보여줍니다. 여러 물체에 대한 로봇 파지 실험의 샘플 결과가 제시되어 있으며, 제안된 방법(오른쪽 열)을 세 가지 기준선(중간 열)과 비교하고 초기 구성(왼쪽 열)을 보여줍니다. 기준선에는 최소 파지력(MinGF), 중간 파지력(MidGF), 최대 파지력(MaxGF)을 사용한 파지 전략이 포함됩니다. 제안된 방법은 물체의 재질 특성을 고려하여 파지력을 조정하는 반면, 기준선은 고정된 파지력을 사용합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Robot Grasping is a downstream application of GaussianProperty. Several sample cases from robot grasping experiments are presented, where we compare our proposed method (right) against three baselines (middle columns), starting from initial configurations (left).
> </details>



![](https://arxiv.org/html/2412.11258/x7.png)

> 🔼 이 그림은 로봇 파지 실험에 사용된 로봇 플랫폼(왼쪽)과 로봇 그리퍼(오른쪽)를 보여줍니다. 로봇 플랫폼은 Jacobi.ai JSR-1 로봇 플랫폼이고, 로봇 그리퍼는 최대 40N의 파지력을 가진 TEK CTAG2F90-C 로봇 그리퍼입니다. 그리퍼 끝 부분의 힘 전달 면적은 0.00011m²이고, 최대 허용 굽힘 곡률은 0.5입니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: The robot platform (left) and the  robotic gripper (right)  utilized in robot grasping experiments.
> </details>



![](https://arxiv.org/html/2412.11258/x8.png)

> 🔼 로봇 그리퍼의 파지력과 정규화된 입력값 간의 관계를 보여주는 그래프입니다. 왼쪽 그래프는 실제 측정값을, 가운데와 오른쪽 그래프는 각각 5차 다항식으로 부드럽게 처리한 결과를 나타냅니다. 최소 활성화 정규화 입력값이 존재하며, 로봇 그리퍼는 정규화 입력값 NGF가 15 이상일 때만 활성화됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Calibration curve of robotic gripper grasping force (left) and its 5th-order polynomial smoothings (middle and right).
> </details>



![](https://arxiv.org/html/2412.11258/x9.png)

> 🔼 로봇 grasping 실험을 위해 선택된 16개의 물체 목록입니다. 이 컬렉션은 플라스틱, 세라믹, 종이, 강철, 나무, 유리 등 다양한 무게와 재질의 물체들을 포함합니다. 이러한 물체들은 일상생활에서 흔히 볼 수 있으며, 각 부분의 재질 특성도 매우 다양합니다. 따라서 재질 적응성을 고려하지 않은 단순한 grasping 전략은 이러한 모든 항목을 효과적이고 안전하게 파지하는 데 어려움을 겪을 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: List of selected objects for robot grasping experiments.
> </details>



![](https://arxiv.org/html/2412.11258/x10.png)

> 🔼 이 그림은 16개의 실제 물체에 대한 로봇 grasping 실험 결과를 보여줍니다. 제안된 방법(오른쪽 열)을 초기 구성(왼쪽 열)에서 시작하여 세 가지 기준선(중간 열)과 비교합니다. 성공적인 grasping은 물체를 미끄러지거나 손상시키거나 원치 않는 변형을 일으키지 않고 집어 올리는 것을 의미합니다. 프로젝트 페이지에서 실험 비디오를 볼 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Complete robot grasping experiment results. The 16 test cases along with results in robot grasping experiments are listed. We compare our proposed method (right) against three baselines (middle columns), starting from initial configurations (left). You can view the MP4 videos of the experiments in our project page.
> </details>



![](https://arxiv.org/html/2412.11258/x11.png)

> 🔼 NeRF2Physics는 경계가 모호한 예측을 생성하는 반면 제안된 방법은 명확한 경계를 생성합니다. 즉, 제안된 방법은 경도 예측 정확도가 더 높습니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Qualitative comparison of hardness prediction. Compared to NeRF2Physics, our method provides more accurate hardness prediction with clear boundaries.
> </details>



![](https://arxiv.org/html/2412.11258/x12.png)

> 🔼 이 그림은 SAM(Segment Anything Model)을 사용하여 다양한 세분화 수준에서 이미지를 분할하는 과정을 보여줍니다. 왼쪽에서 오른쪽으로 입력 이미지, 큰 수준 분할, 중간 수준 분할, 작은 수준 분할이 표시됩니다. 큰 수준 분할은 객체 그룹화를 단순화하지만 세부 정보가 부족한 반면, 작은 수준 분할은 계산 복잡성을 높이면서 미세한 세부 정보를 캡처합니다. 객체 이해와 효율성 사이의 균형을 맞추기 위해 모델에서는 의미 있는 부분 수준 세부 정보를 유지하면서 과도한 조각화를 방지하는 중간 수준 분할을 선택했습니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Segmentation process using SAM at different levels of granularity. From left to right: the input image, large-level segmentation, middle-level segmentation, and small-level segmentation. For our model, we selected the middle-level of SAM prediction to balance part-level object understanding and computational efficiency.
> </details>



![](https://arxiv.org/html/2412.11258/x13.png)

> 🔼 이 그림은 ABO-500 데이터셋에서 가져온 객체들의 데이터 레이블링 예시를 보여줍니다. 의자, 탁자, 서랍장 등의 객체 일부분을 대화형 분할 도구를 사용하여 라벨링한 결과를 시각적으로 표현하고 있습니다. 각 객체 부분은 나무, 금속, 가죽 등의 재질에 따라 다른 색상으로 표시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: Examples of data labeling. These objects are sourced from the ABO-500 dataset.
> </details>



![](https://arxiv.org/html/2412.11258/x14.png)

> 🔼 이 그림은 GPT-4V(ision)에 입력으로 제공되는 프롬프트의 예시를 보여줍니다. 이 프롬프트는 객체의 재질과 기타 물리적 특성(경도, 밀도, 영률, 푸아송 비 등)을 제안하는 데 사용됩니다. 프롬프트는 왼쪽 이미지(원본 이미지), 중간 이미지(부분 분할 다이어그램, 빨간색 마스크), 오른쪽 이미지(객체의 일부) 세 부분으로 구성됩니다. 먼저 객체의 일부에 대한 간략한 캡션을 제공하고, 객체의 재질을 설명하며, 마지막으로 객체의 재질과 물리적 특성을 예측합니다. 답변 형식은 (캡션, 재질, 경도 최소-최대, <쇼어 A 또는 쇼어 D>, 밀도, 영률, 푸아송 비) 쌍으로 제공되어야 합니다. 재질 유형은 '일반 재질 라이브러리'에서 선택해야 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: Prompt used for proposing materials and other physical properties.
> </details>



![](https://arxiv.org/html/2412.11258/x15.png)

> 🔼 이 그림은 빈도 기반 투표 전략의 효과를 보여주는 예시입니다. 투표 전략이 없으면 '알루미늄'과 '나무'가 각각 '플라스틱'과 '강철'로 잘못 분류됩니다. 빈도 기반 투표 전략을 사용하면 여러 시점에서 얻은 정보를 집계하여 일관성 있고 안정적인 예측을 보장합니다.
> <details>
> <summary>read the caption</summary>
> Figure 15: Effects of Frequency-based Voting Strategy. We provide an example to demonstrate the effectiveness of the frequency-based voting strategy. The result misclassified the “aluminum” and “wood” into “plastic” and “’steel’ without voting strategy.
> </details>



![](https://arxiv.org/html/2412.11258/x16.png)

> 🔼 이 그림은 ABO-500 데이터셋에서 가져온 객체들의 재질 분할 결과를 NeRF2Physics와 제안된 방법을 비교하여 보여줍니다. 제안된 방법이 NeRF2Physics보다 더 정확한 재질 분할 결과를 보여주고, 경계도 더 명확하게 구분하는 것을 확인할 수 있습니다. 예시로 제시된 객체들은 사다리, 의자, 소파, 화분, 벤치 등 다양한 재질로 이루어진 객체들입니다.
> <details>
> <summary>read the caption</summary>
> Figure 16: Qualitative comparison of Material Segmentation. These objects are sourced from the ABO-500 dataset.
> </details>



![](https://arxiv.org/html/2412.11258/x17.png)

> 🔼 MVImgNet 데이터셋에서 객체 재질 분할에 대한 정성적 결과입니다. 모델은 단일 또는 여러 재질로 구성된 객체에 대해 합리적이고 경계가 정확한 재질 예측을 수행합니다.
> <details>
> <summary>read the caption</summary>
> Figure 17: Qualitative results of object material segmentation on MVImgNet. Our model makes reasonable and boundary-accurate material predictions for objects with multiple or single materials.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Global-to-local | Voting | Average mIoU (%) (↑) |
|---|---|---| 
| | ✓ | 22.17 |
| ✓ |  | 51.28 |
| ✓ | ✓ | **55.83** |{{< /table-caption >}}
> 🔼 이 표는 전역-지역 지식 통합과 빈도 기반 투표 전략을 사용하지 않았을 때와 사용했을 때의 재료 분할 성능을 비교하여 두 가지 기술의 효과를 보여줍니다. 전역-지역 지식 통합은 객체의 전역적 구조와 세부 정보를 더 잘 이해하여 재료 예측의 정확도를 향상시키는 반면, 빈도 기반 투표는 여러 시점에서 정보를 집계하여 예측의 일관성과 신뢰성을 보장합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Ablation study of Global-to-Local Knowledge Integration and Frequency-Based Voting.
> </details>

{{< table-caption >}}
| Method | PUR (%)↑ | NDR (%)↑ | SR (%)↑ |
|---|---|---|---| 
| MinGF | 50.00 | **100.00** | 50.00 |
| MidGF | 87.50 | 81.25 | 68.75 |
| MaxGF | **100.00** | 75.00 | 75.00 |
| Ours* | **100.00** | **100.00** | **100.00** |{{< /table-caption >}}
> 🔼 로봇 그리핑 실험 결과를 요약한 표입니다. 최소, 중간, 최대 그리핑 힘을 사용하는 베이스라인과 제안된 GaussianProperty 방법을 비교하여 성공률을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Results of robot grasping experiments on 16 objects. MinGF, MidGF and MaxGF are baselines with minimum (NG⁢F=15subscript𝑁𝐺𝐹15N_{GF}=15italic_N start_POSTSUBSCRIPT italic_G italic_F end_POSTSUBSCRIPT = 15), medium (NG⁢F=60subscript𝑁𝐺𝐹60N_{GF}=60italic_N start_POSTSUBSCRIPT italic_G italic_F end_POSTSUBSCRIPT = 60) and maximum (NG⁢F=100subscript𝑁𝐺𝐹100N_{GF}=100italic_N start_POSTSUBSCRIPT italic_G italic_F end_POSTSUBSCRIPT = 100) grasping forces applied by the robotic gripper. Bold: best results.
> </details>

{{< table-caption >}}
| Method | ADE (↓) | ALDE (↓) | APE (↓) | MnRE (↑) | PRA (↑) |
|---|---|---|---|---|---| 
| NeRF2Physics | 35.917 | 0.328 | 0.294 | 0.748 | 0.575 |
| Ours* | **28.583** | **0.220** | **0.198** | **0.820** | **0.686** |{{< /table-caption >}}
> 🔼 이 표는 실제 촬영된 자체 수집 데이터셋(10개 객체, 100개 지점)에서 지점별 Shore 경도 추정 결과를 비교한 것입니다. NeRF2Physics와 제한된 방법과 비교하여 제안된 방법이 더 정확한 경도 추정 결과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Estimation of per-point Shore hardness on the real-captured in-house collected dataset (10 objects, 100 points). Bold: best model.
> </details>

{{< table-caption >}}
| Method | ADE (↓) | ALDE (↓) | APE (↓) | MnRE (↑) |
|---|---|---|---|---| 
| NeRF2Physics | 12.761 | 0.803 | **0.589** | 0.498 |
| Ours* | **5.960** | **0.744** | 1.609 | **0.559** |{{< /table-caption >}}
> 🔼 ABO 데이터셋에서의 질량 추정 결과 비교. 다양한 평가 지표에서 NeRF2Physics보다 본 연구의 방법이 더 나은 성능을 보임.
> <details>
> <summary>read the caption</summary>
> Table 5: Mass estimation on ABO dataset. Bold: best results.
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