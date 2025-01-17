---
title: "CityDreamer4D: Compositional Generative Model of Unbounded 4D Cities"
summary: "CityDreamer4D: 무한한 4D 도시를 실시간 생성하는 혁신적인 모델!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Generation", "🏢 Tencent AI Lab",]
showSummary: true
date: 2025-01-15
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.08983 {{< /keyword >}}
{{< keyword icon="writer" >}} Haozhe Xie et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-16 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.08983" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.08983" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/citydreamer4d-compositional-generative-model" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

3D 장면 생성 분야가 발전했지만, **구조적으로 복잡하고 시각적으로 다양한 객체들과 인간의 높은 민감도** 때문에 4D 도시 생성은 여전히 어려운 과제입니다. 기존 방법들은 시간적 일관성 부족, 작은 규모의 장면 생성 등의 한계를 가지고 있습니다. 



본 논문에서는 이러한 문제를 해결하기 위해 **CityDreamer4D**라는 새로운 모델을 제시합니다. CityDreamer4D는 동적 객체(차량)와 정적 장면(건물, 도로)을 분리하고, 각 객체에 특화된 신경망 필드를 사용하여 4D 도시를 생성합니다. **OSM, Google Earth, CityTopia** 등 다양한 데이터셋을 활용하여 모델의 성능을 높였으며, 인스턴스 편집, 도시 스타일링, 도시 시뮬레이션 등 다양한 응용 프로그램을 지원합니다. CityDreamer4D는 **무한한 4D 도시 생성 분야의 새로운 기준**을 제시하고, 도시 계획, 환경 시뮬레이션, 게임 개발 등 다양한 분야에 기여할 것으로 기대됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 동적 객체(차량)와 정적 장면(건물, 도로)을 분리하여 4D 도시 생성의 복잡성을 해결 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 신경망 필드를 사용하여 배경, 건물, 차량 등 다양한 객체를 사실적으로 생성 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} OSM, Google Earth, CityTopia 등 대규모 데이터셋을 활용하여 모델 성능과 현실감 향상 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **무한한 4D 도시 생성**이라는 어려운 문제에 대한 새로운 접근법을 제시하여, 도시 계획, 환경 시뮬레이션, 게임 자산 개발 등 다양한 분야에서의 활용 가능성을 높였습니다. 특히, **동적 객체와 정적 장면 분리**, **다양한 신경망 필드 활용**, **대규모 데이터셋 구축** 등의 혁신적인 방법론을 통해 현실감 넘치는 4D 도시를 생성하고, 인스턴스 편집, 도시 스타일링, 도시 시뮬레이션 등 다양한 응용 프로그램을 지원합니다.  **4D 도시 생성 분야의 발전에 크게 기여**하고, 향후 연구 방향에 대한 새로운 가능성을 제시합니다. 

------
#### Visual Insights



![](https://arxiv.org/html/2501.08983/x1.png)

> 🔼 그림 1은 CityDreamer4D의 개요를 보여줍니다. 4D 도시 생성은 Unbounded Layout Generator와 Traffic Scenario Generator에 의해 생성된 𝐿과 𝑇𝑡를 조건으로 정적 및 동적 장면 생성으로 나뉩니다. City Background Generator는 𝐿을 사용하여 도로, 초목, 하늘과 같은 배경 이미지 𝐼̂𝐺를 생성하는 반면, Building Instance Generator는 도시 내 건물 {𝐼̂𝐵𝑖}를 렌더링합니다. 𝑇𝑡를 사용하여 Vehicle Instance Generator는 시간 단계 t에서 차량 {𝐼̂𝑉𝑖𝑡}을 생성합니다. 마지막으로 Compositor는 렌더링된 배경, 건물 및 차량을 통합하여 통합적이고 일관된 이미지 𝐼̂𝐶𝑡를 생성합니다. 'Gen.', 'Mod.', 'Cond.', 'BG.', 'BLDG.', 'VEH.'는 각각 'Generation', 'Modulation', 'Condition', 'Background', 'Building', 'Vehicle'을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Overview of CityDreamer4D. 4D city generation is divided into static and dynamic scene generation, conditioned on 𝐋𝐋\mathbf{L}bold_L and 𝐓tsubscript𝐓𝑡\mathbf{T}_{t}bold_T start_POSTSUBSCRIPT italic_t end_POSTSUBSCRIPT, produced by Unbounded Layout Generator and Traffic Scenario Generator, respectively. City Background Generator uses 𝐋𝐋\mathbf{L}bold_L to create background images 𝐈^Gsubscript^𝐈𝐺\mathbf{\hat{I}}_{G}over^ start_ARG bold_I end_ARG start_POSTSUBSCRIPT italic_G end_POSTSUBSCRIPT for stuff like roads, vegetation, and the sky, while Building Instance Generator renders the buildings {𝐈^Bi}subscript^𝐈subscript𝐵𝑖\{\mathbf{\hat{I}}_{B_{i}}\}{ over^ start_ARG bold_I end_ARG start_POSTSUBSCRIPT italic_B start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT end_POSTSUBSCRIPT } within the city. Using 𝐓tsubscript𝐓𝑡\mathbf{T}_{t}bold_T start_POSTSUBSCRIPT italic_t end_POSTSUBSCRIPT, Vehicle Instance Generator generates vehicles {𝐈^Vit}superscriptsubscript^𝐈subscript𝑉𝑖𝑡\{\mathbf{\hat{I}}_{V_{i}}^{t}\}{ over^ start_ARG bold_I end_ARG start_POSTSUBSCRIPT italic_V start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT end_POSTSUBSCRIPT start_POSTSUPERSCRIPT italic_t end_POSTSUPERSCRIPT } at time step t𝑡titalic_t. Finally, Compositor combines the rendered background, buildings, and vehicles into a unified and coherent image 𝐈^Ctsuperscriptsubscript^𝐈𝐶𝑡\mathbf{\hat{I}}_{C}^{t}over^ start_ARG bold_I end_ARG start_POSTSUBSCRIPT italic_C end_POSTSUBSCRIPT start_POSTSUPERSCRIPT italic_t end_POSTSUPERSCRIPT. “Gen.”, “Mod.“, “Cond.”, “BG.”, “BLDG.”, and “VEH.” denote “Generation”, “Modulation”, “Condition”, “Background”, “Building”, and “Vehicle”, respectively.
> </details>





{{< table-caption >}}
| Dataset | #Images | #Cities | Area (km<sup>2</sup>) | Source | Ext. | 3DM. | Lighting | Lighting | View Type | View Type | Dense Annotations | Dense Annotations | Dense Annotations | Dense Annotations |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| KITTI [92] | 0.2 | 1 | - | Real | ✗ | ✗ | ✓ | ✗ | ✓ | ✗ | ✓ | ✓ | ✗ | ✗ |
| Cityscapes [93] | 25 | 50 | - | Real | ✗ | ✗ | ✓ | ✗ | ✓ | ✗ | ✓ | ✓ | ✗ | ✗ |
| AeroScapes [94] | 3.2 | - | - | Real | ✗ | ✗ | ✓ | ✗ | ✗ | ✓ | ✓ | ✗ | ✗ | ✗ |
| nuScenes [95] | 93 | 2 | - | Real | ✗ | ✗ | ✓ | ✗ | ✓ | ✗ | ✓ | ✓ | ✗ | ✗ |
| GTA-V [96] | 25 | - | - | Synthetic | ✗ | ✗ | ✓ | ✗ | ✓ | ✗ | ✓ | ✗ | ✗ | ✗ |
| SYNTHIA [97] | 213 | 1 | - | Synthetic | ✗ | ✗ | ✓ | ✗ | ✓ | ✓ | ✓ | ✓ | ✗ | ✗ |
| VEIS [98] | 61 | - | - | Synthetic | ✗ | ✗ | ✓ | ✗ | ✓ | ✓ | ✓ | ✓ | ✗ | ✗ |
| MatrixCity [99] | 519 | 2 | 28 | Synthetic | ✗ | ✗ | ✓ | ✓ | ✓ | ✓ | ✗ | ✗ | ✗ | ✗ |
| HoliCity [100] | 6.3 | 1 | 20 | Real | ✗ | CAD | ✓ | ✗ | ✓ | ✗ | ✓ | ✓ | ✗ | ✗ |
| KITTI-360 [101] | 78 | 1 | - | Real | ✗ | CAD | ✓ | ✗ | ✓ | ✗ | ✓ | ✓ | ✗ | ✗ |
| UrbanScene3D [102] | 6.1<sup>†</sup> | - | 3<sup>†</sup> | Real | ✗ | Mesh | ✓ | ✗ | ✗ | ✓ | ✗ | ✗ | ✗ | ✓ |
| GoogleEarth | 24 | 1 | 25 | Real | ✓ | Voxel | ✓ | ✗ | ✗ | ✓ | ✓ | ✓ | ✓ | ✓ |
| CityTopia | 3.75 | 11 | 36 | Synthetic | ✓ | Voxel | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ | ✓ |{{< /table-caption >}}

> 🔼 본 표는 GoogleEarth, CityTopia 및 기존 데이터셋의 통계 및 특징을 비교한 것입니다. 주석이 달린 이미지만 계산되었으며, 각 데이터셋의 이미지 수, 도시 수, 면적, 조명, 시점, 밀집 주석, 소스, 확장 가능성, 3D 모델, 의미 및 인스턴스 여부 등을 보여줍니다.  'Ext.'는 현재 데이터 생성 파이프라인을 따라 데이터셋을 쉽게 확장할 수 있는지 여부를 나타내는 '확장 가능성'을 의미합니다.  '3DM.', 'Sem.', 'Inst.'는 각각 '3D 모델', '의미', '인스턴스'를 의미합니다.
> <details>
> <summary>read the caption</summary>
> TABLE I: Comparison of Statistics and Properties: GoogleEarth, CityTopia, and Previous Datasets. Only annotated images are counted. “Ext.” stands for “Extendable”, indicating whether the dataset can be easily expanded following the current data generation pipeline. “3DM.”, “Sem.”, and “Inst.” refer to “3D Model”, “Semantic”, and “Instance”, respectively.
> </details>





### In-depth insights


#### Unbounded 4D Cities
이 논문은 **무한한 4D 도시** 생성이라는 매력적이면서도 어려운 문제에 대한 혁신적인 해결책을 제시합니다. 기존의 3D 도시 생성 모델의 한계를 넘어, 시간의 흐름(4D)을 고려하여 도시의 동적 요소(차량 등)와 정적 요소(건물, 도로 등)를 분리하여 모델링함으로써 현실감 있는 시뮬레이션을 가능하게 합니다.  **도시 레이아웃 생성기**와 **교통 시나리오 생성기**를 통해 각 요소를 효율적으로 생성하고, **다양한 유형의 신경망 필드**를 사용하여 건물, 차량, 배경 등을 구분하여 모델링합니다.  **방대한 데이터셋**을 활용하여 모델의 정확도와 현실성을 높였으며, 이는 도시 계획, 환경 시뮬레이션, 게임 개발 등 다양한 분야에 활용될 수 있다는 점을 시사합니다.  **인스턴스 편집** 및 **도시 스타일 변경** 기능을 통해 사용자의 창의성을 더욱 증진시키고, 향후 **메타버스** 구축에도 중요한 역할을 할 것으로 기대됩니다.  결론적으로, 이 연구는 무한하고 동적인 4D 도시 생성에 대한 새로운 가능성을 보여주는 획기적인 연구입니다.

#### Compositional Generation
본 논문에서 제시된 CityDreamer4D 모델의 핵심은 **구성적 생성(Compositional Generation)** 접근 방식에 있습니다. 이는 도시의 정적 요소(건물, 도로)와 동적 요소(차량)를 분리하여 생성하는 것을 의미합니다.  **정적 요소는 비어 있는 공간(unbounded)에서 확장 가능한 레이아웃 생성기를 통해 만들어지고, 동적 요소는 고해상도 지도를 기반으로 생성된 교통 시나리오에 따라 생성됩니다.** 이러한 분리는 복잡한 도시 환경을 효율적으로 모델링하고, 현실감 있는 4D 도시를 생성하는 데 중요한 역할을 합니다.  각 요소는 다양한 신경망 필드(neural field)를 사용하여 생성되는데, 배경 요소는 해시 그리드를, 건물 및 차량은 주기적 위치 임베딩을 사용하는 등 각 요소의 특성에 맞는 방식을 채택합니다. 이러한 **모듈화된 접근 방식**은 각 요소의 생성 과정을 독립적으로 제어하고 최적화할 수 있게 하여,  **인스턴스 편집, 도시 스타일 변환, 도시 시뮬레이션 등 다양한 다운스트림 애플리케이션을 지원합니다.**  결론적으로, CityDreamer4D의 구성적 생성은 4D 도시 생성의 현실성과 효율성을 크게 향상시키는 핵심 요소이며,  메타버스 등 다양한 분야에서 활용될 수 있는 잠재력을 가지고 있습니다.

#### Neural Field Fusion
**신경장(Neural Field)** 융합이란, 서로 다른 신경장 표현들을 결합하여 하나의 통합된 표현을 생성하는 기술을 말합니다. 이는 3D 또는 4D 도시 생성 모델에서 **다양한 객체들을 효율적이고 현실적으로 표현**하는 데 매우 중요한 역할을 합니다.  예를 들어, 건물, 차량, 배경 등 각각 다른 특징을 가진 객체들을 개별적인 신경장으로 표현하고, 이들을 융합하여 하나의 시나리오를 생성할 수 있습니다. 이러한 융합 과정에서 **각 신경장의 장점을 유지하면서 단점을 보완**하는 것이 중요하며, **융합 방식**에 따라 최종 결과물의 품질이 크게 달라질 수 있습니다.  **효율적인 연산과 메모리 관리**를 위해서는 신경장의 크기와 복잡도를 최적화하는 것이 필요합니다. 또한, **시간적 일관성을 유지**하는 4D 도시 생성을 위해서는 시간에 따른 객체들의 변화를 정확하게 표현하고, **다양한 시각적 효과**를 위해서는 물리적 현상(조명, 그림자 등)을 사실적으로 모델링하는 것이 중요합니다.  **데이터셋의 질** 또한 신경장 융합의 성능에 큰 영향을 미칩니다. 풍부하고 다양한 데이터셋을 바탕으로 학습된 모델일수록 더욱 현실적이고 정교한 4D 도시를 생성할 수 있습니다.

#### Dataset Contributions
본 논문은 **세 가지 주요 도시 데이터셋**인 OSM, Google Earth, CityTopia를 제시하며, 이는 기존 방법론의 한계를 극복하고 4D 도시 생성 모델의 성능을 향상시키는 데 크게 기여합니다. OSM은 전 세계 80개 도시의 도로, 건물, 식생 등의 정보를 포함한 대규모의 레이아웃 정보를 제공합니다.  **Google Earth 데이터셋**은 뉴욕시를 대상으로 한 400개의 드론 궤적 데이터와 24,000개의 고품질 이미지를 포함하며, 건물에 대한 3D 인스턴스 주석이 포함된 특징이 있습니다. 마지막으로, **CityTopia 데이터셋**은 Unreal Engine을 사용하여 생성된 11개의 합성 도시를 포함하며, 고해상도의 이미지와 정확한 2D 및 3D 주석을 제공하는 것이 특징입니다. 세 데이터셋은 각각 **다양한 강점**을 가지고 있으며,  **상호 보완적인 역할**을 수행하여 더욱 풍부하고 다양한 4D 도시 생성을 가능하게 합니다. 이러한 데이터셋 공개는 향후 4D 도시 생성 분야의 발전에 상당한 영향을 미칠 것으로 예상됩니다.

#### Future Directions
본 논문의 "미래 방향"에 대한 고찰은 **도시 생성 모델의 확장성 및 현실성 개선**에 초점을 맞춰야 할 것입니다.  **무한한 크기의 도시 환경을 생성하는 기술**은 더욱 발전되어야 하며, 이를 위해서는 **더욱 효율적이고 확장 가능한 데이터 구조 및 알고리즘** 개발이 필수적입니다.  **다양한 기후, 문화, 건축 양식 등을 반영한 도시 환경 생성**은 모델의 현실감을 높이는 데 중요한 요소가 될 것이며,  **실시간 상호 작용 및 시뮬레이션 기술과의 통합**을 통해 메타버스나 도시 계획 분야 등 다양한 응용 분야에서 활용 가능성을 높일 수 있습니다.  **인공지능 기반의 도시 설계 및 최적화**는 미래 도시의 지속가능성을 확보하는 데 중요한 역할을 할 것이며, **에너지 효율, 교통 흐름, 환경 보호 등을 고려한 도시 모델링** 기술 개발이 필요합니다.  마지막으로, **윤리적, 사회적 측면을 고려한 도시 생성 모델** 개발이 중요합니다. **개인정보 보호, 편향성 제거, 공정성 확보** 등의 문제를 해결하여 사회에 긍정적인 영향을 미치는 기술이 되도록 해야 합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.08983/x2.png)

> 🔼 그림 2는 OSM(OpenStreetMap)과 Google Earth 데이터셋의 개요를 보여줍니다. (a)는 Google Earth 데이터셋에 있는 2D 및 3D 주석의 예시이며, OSM 데이터셋을 사용하여 자동으로 생성될 수 있습니다. (b)는 자동 주석 파이프라인을 전 세계 도시에 쉽게 적용할 수 있음을 보여줍니다. (c)는 Google Earth 데이터셋의 다양한 관점을 강조하는 데이터셋 통계를 보여줍니다.  즉,  OSM 데이터셋을 기반으로 Google Earth 이미지 데이터에 대한 2D 및 3D 어노테이션(주석)을 자동으로 생성하는 방법과, 이러한 자동화된 주석 생성 방식을 전 세계 여러 도시에 적용할 수 있음을 시각적으로 보여주는 그림입니다. 또한 Google Earth 데이터셋의 이미지들이 다양한 각도와 높이에서 촬영되었음을 보여주는 통계자료도 함께 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Overview of the OSM and GoogleEarth Datasets. (a) Examples of the 2D and 3D annotations in the GoogleEarth dataset, which can be automatically generated using the OSM dataset. (b) The automatic annotation pipeline can be readily adapted for worldwide cities. (c) The dataset statistics highlight the diverse perspectives in the GoogleEarth dataset.
> </details>



![](https://arxiv.org/html/2501.08983/x3.png)

> 🔼 그림 3은 CityTopia 데이터셋에 대한 개요를 보여줍니다. (a)는 가상 도시 생성 파이프라인을 보여줍니다. 프로토타입 인스턴스화, 표면 샘플링, 3D 인스턴스 주석을 나타내는 약어를 풀어서 설명합니다. (b)는 가상 도시 생성 중에 자동으로 생성된 주행 및 야간의 거리 전망과 항공 전망 모두에서 CityTopia 데이터셋의 2D 및 3D 주석의 예를 보여줍니다. (c)는 거리 전망과 항공 전망 모두에서 다양한 관점을 강조하는 데이터셋 통계를 보여줍니다.  CityTopia 데이터셋은 다양한 시각(주행 시점, 항공 시점, 주간, 야간)에서 고품질 합성 이미지를 제공하고, 각 이미지에 대한 정확한 2D 및 3D 주석을 포함하며, 대규모 4D 도시 생성을 위한 풍부한 데이터를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Overview of the CityTopia Dataset. (a) The virtual city generation pipeline. “Pro.Inst.”, “Sur.Spl”, and “3D Inst. Anno.” denote “Prototype Instantiation”, “Surface Sampling”, and “3D Instance Annotation”, respectively. (b) Examples of 2D and 3D annotations in the CityTopia dataset are shown from both daytime and nighttime street-view and aerial-view perspectives, automatically generated during virtual city generation. (c) The dataset statistics highlight the diverse perspectives in both street and aerial views.
> </details>



![](https://arxiv.org/html/2501.08983/x4.png)

> 🔼 그림 4는 Google Earth 데이터셋을 기반으로 한 다양한 방법들의 정성적 비교 결과를 보여줍니다. SceneDreamer와 CityDreamer4D의 경우, Google Earth에는 차량에 대한 의미론적 주석이 부족하여 CityTopia에서 학습된 모델을 사용하여 차량을 생성했습니다. DimensionX의 경우 CityDreamer4D가 생성한 초기 프레임을 사용했습니다. 저자들이 제공한 InfiniCity 결과는 더 나은 시각화를 위해 확대했습니다. Pers.Nature는 PersistentNature의 약자입니다.  이 그림은 각 모델이 Google Earth 데이터셋에서 얼마나 사실적인 도시 장면을 생성하는지, 특히 건물과 차량의 디테일과 전체적인 도시 구조의 현실성을 비교 분석하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Qualitative Comparison on Google Earth. For SceneDreamer [7] and CityDreamer4D, vehicles are generated using models trained on CityTopia due to the lack of semantic annotations for vehicles in Google Earth. For DimensionX [107], the initial frame is provided by CityDreamer4D. The visual results of InfiniCity [26], provided by the authors, have been zoomed in for better viewing. “Pers.Nature” stands for “PersistentNature” [105].
> </details>



![](https://arxiv.org/html/2501.08983/x5.png)

> 🔼 그림 5는 CityTopia 데이터셋을 기반으로 다양한 4D 도시 생성 모델들의 성능을 비교한 정성적 결과를 보여줍니다.  DimensionX와 DreamScene4D는 CityTopia 데이터셋의 이미지를 초기 프레임 또는 입력 프레임으로 사용했습니다. PersistentNature [105]는 별도로 명시되어 있습니다.  이 그림은 각 모델이 생성한 4D 도시의 시각적 품질과 현실성, 다양성을 보여주어, CityDreamer4D를 포함한 여러 모델의 장단점을 한눈에 비교할 수 있도록 합니다.  각 모델의 생성 결과는 여러 시점에서의 이미지 시퀀스로 표현되어, 시간적 일관성 및 시각적 품질을 평가하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Qualitative Comparison on CityTopia. The initial frame for DimensionX and the input frames for DreamScene4D are chosen from the dataset. “Pers.Nature” refers to “PersistentNature” [105].
> </details>



![](https://arxiv.org/html/2501.08983/x6.png)

> 🔼 그림 6은 제시된 4D 도시 생성 모델에 대한 사용자 연구 결과를 보여줍니다.  5점 척도(5점이 최고)로 사용자들이 인식 품질, 4D 사실성, 시점 일관성 세 가지 측면에서 각 모델의 성능을 평가했습니다.  PersistentNature는 논문 [105]에서 제시된 모델을 의미합니다.  그래프는 각 모델에 대한 평균 점수를 보여주어 CityDreamer4D 모델이 다른 모델들에 비해 훨씬 우수한 성능을 보임을 시각적으로 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: User Study on 4D City Generation. All scores are in the range of 5, with 5 indicating the best. “Pers.Nature” refers to “PersistentNature” [105].
> </details>



![](https://arxiv.org/html/2501.08983/x7.png)

> 🔼 그림 7은 논문의 Unbounded Layout Generator(제한 없는 도시 레이아웃 생성기) 섹션에 포함된 그림으로, 세 가지 다른 방법(Ours, InfinityGAN, IPSM)을 사용하여 생성된 도시 레이아웃의 높이 맵을 비교한 것입니다. 높이 맵 값은 각 맵 내 최댓값으로 나누어 0과 1 사이의 범위로 정규화되었습니다.  각 방법의 결과는 시각적으로 비교되어, 생성된 도시 레이아웃의 질적 차이를 보여줍니다.  Ours 방법은 더욱 사실적이고 디테일한 도시 레이아웃을 생성하는 것을 시각적으로 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Qualitative Comparison of City Layout Generators. The height map values are normalized to a range of [0,1]01[0,1][ 0 , 1 ] by dividing each value by the maximum value within the map.
> </details>



![](https://arxiv.org/html/2501.08983/x8.png)

> 🔼 그림 8은 건물 인스턴스 생성기(BIG)의 변형에 대한 정성적 비교를 보여줍니다. (a)와 (b)는 각각 BIG와 인스턴스 레이블을 제거했을 때의 효과를 보여줍니다. (c)부터 (f)까지는 다양한 장면 매개변수화의 결과를 보여줍니다. 'Enc.'는 '인코더'의 약자입니다.  이 그림은 3.4절에 제시된 건물 인스턴스 생성기의 성능을 평가하기 위해 다양한 설정으로 생성된 결과 이미지들을 보여주는 것으로,  인코더 종류(전역/국소), 위치 인코딩 방식(해시 그리드/사인 코사인 함수)에 따른 결과 차이를 시각적으로 비교하여 각 요소의 중요성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Qualitative Comparison of Building Instance Generator (BIG) Variants. (a) and (b) illustrate the effects of removing BIG and instance labels, respectively. (c)–(f) present the results of various scene parameterizations. Note that “Enc.” is an abbreviation for “Encoder”.
> </details>



![](https://arxiv.org/html/2501.08983/x9.png)

> 🔼 그림 9는 CityDreamer4D의 차량 인스턴스 생성기(VIG)의 변형에 대한 정성적 비교를 보여줍니다. (a)와 (b)는 각각 VIG와 정규화를 제거했을 때의 영향을 보여주며, (c)부터 (f)는 다양한 장면 매개변수화 결과를 보여줍니다. 'Enc.'는 '인코더'의 약자입니다.  이 그림은 VIG의 구성요소(정규화, 인코더 종류, 위치 인코딩 방식)가 생성된 차량의 시각적 품질에 미치는 영향을 보여주는 실험 결과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Qualitative Comparison of Vehicle Instance Generator (VIG) Variants. (a) and (b) illustrate the effects of removing VIG and canonicalization, respectively. (c)–(f) present the results of various scene parameterizations. Note that “Enc.” is an abbreviation for “Encoder”.
> </details>



![](https://arxiv.org/html/2501.08983/x10.png)

> 🔼 그림 10은 CityDreamer4D 모델이 생성한 도시 환경에서 국소적 편집의 결과를 보여줍니다. (a)와 (c)는 차량의 위치, 스타일, 개수 등을 변경한 결과를, (b)와 (d)는 건물의 높이, 스타일 등을 변경한 결과를 보여줍니다.  모델의 구성 요소 간의 독립적인 특성 덕분에 특정 객체만을 수정하고 다른 요소들에는 영향을 주지 않고 도시의 특징을 자유롭게 바꿀 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Localized Editing on the Generated Cities. (a) and (c) show vehicle editing results, while (b) and (d) present building editing results.
> </details>



![](https://arxiv.org/html/2501.08983/x11.png)

> 🔼 본 그림은 ControlNet을 사용하여 텍스트 기반으로 도시 스타일을 변경하는 실험 결과를 보여줍니다.  Minecraft와 Cyberpunk 두 가지 스타일로 도시를 변환했으며, 다양한 시점에서 촬영한 이미지들에서도 일관된 시각적 결과를 유지하고 있음을 보여줍니다.  이는 ControlNet이 다중 시점 일관성을 유지하면서 다양한 스타일의 도시 생성을 가능하게 함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Text-driven City Stylization with ControlNet. The multi-view consistency is preserved in stylized Minecraft and Cyberpunk cities.
> </details>



![](https://arxiv.org/html/2501.08983/x12.png)

> 🔼 그림 12는 CityDreamer4D 모델이 생성한 600프레임의 궤도 비디오에 대한 COLMAP 재구성 결과를 보여줍니다. 빨간색 원은 카메라 위치를 나타내며, 명확한 점 구름은 CityDreamer4D의 일관된 렌더링 성능을 보여줍니다.  이 그림은 CityDreamer4D가 생성한 장면의 3D 일관성을 시각적으로 증명합니다. 즉, 다양한 각도에서 촬영한 이미지들이 하나의 일관된 3D 모델로 정확하게 재구성될 수 있음을 보여줍니다.  이는 CityDreamer4D가 생성한 4D 도시의 시각적 정확성과 일관성에 대한 강력한 증거입니다.  'Recon.'은 'Reconstruction'의 약자입니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: COLMAP Reconstruction of 600-frame Orbital Videos. The red ring shows the camera positions, and the clear point clouds demonstrate CityDreamer4D’s consistent rendering. Note that ”Recon.” stands for ”Reconstruction.”
> </details>



![](https://arxiv.org/html/2501.08983/x13.png)

> 🔼 그림 13은 CityDreamer4D 모델의 조명 재조정 효과를 보여줍니다. (a)는 Lambertian 셰이딩으로 인한 균일한 조명, (b)는 그림자 매핑을 통한 그림자 및 간섭 효과, (c)는 카메라를 왼쪽에 배치한 최종 재조정 결과를 각각 나타냅니다. Lambertian 셰이딩은 균일한 조명을 생성하고, 그림자 매핑은 그림자 및 간섭 효과를 시뮬레이션합니다. 최종 결과는 현실적인 그림자와 조명 효과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: Directional Light Relighting Effect. (a) and (b) show the lighting intensity. (c) illustrates the relighting effect. Note that “S.M.” denotes “Shadow Mapping”.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Methods | GoogleEarth FID ↓ | GoogleEarth KID ↓ | GoogleEarth VBench ↑ | GoogleEarth DE ↓ | GoogleEarth CE ↓ | CityTopia FID ↓ | CityTopia KID ↓ | CityTopia VBench ↑ | CityTopia DE ↓ | CityTopia CE ↓ |
|---|---|---|---|---|---|---|---|---|---|---|
| SGAM [104] | 277.6 | 0.358 | 0.691 | 0.575 | 239.2 | 330.1 | 0.284 | 0.690 | 0.571 | 233.5 |
| PersistentNature [105] | 123.8 | 0.109 | 0.706 | 0.326 | 86.37 | 235.3 | 0.215 | 0.713 | 0.428 | 127.3 |
| SceneDreamer [7] | 232.2 | 0.204 | 0.781 | 0.153 | 0.186 | 195.1 | 0.126 | 0.708 | 0.185 | 0.162 |
| DreamScene4D [106] | - | - | - | - | - | 288.2 | 0.136 | 0.715 | 0.199 | 0.146 |
| DimensionX [107] | 206.9 | 0.182 | 0.805 | - | - | 171.4 | 0.070 | 0.815 | - | - |
| CityDreamer4D (Ours) | **96.83** | **0.096** | **0.834** | **0.138** | **0.060** | **88.48** | **0.049** | **0.825** | **0.150** | **0.063** |{{< /table-caption >}}
> 🔼 이 표는 Google Earth 및 CityTopia 데이터셋에서 다양한 방법들을 정량적으로 비교한 결과를 보여줍니다.  비교 대상은 SGAM, PersistentNature, SceneDreamer, DreamScene4D, DimensionX 및 CityDreamer4D이며, FID, KID, VBench, DE, CE 지표를 사용하여 성능을 평가했습니다.  InfiniCity는 오픈소스가 아니므로 비교에서 제외되었습니다.  가장 좋은 값은 굵게 표시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> TABLE II: Quantitative Comparison. The best values are highlighted in bold. Note that InfiniCity is not included in this comparison as it is not open-sourced.
> </details>

{{< table-caption >}}
| Methods | FID ↓ | KID ↓ |
|---|---|---|
| IPSM [113] | 321.47 | 0.502 |
| InfinityGAN [114] | 183.14 | 0.288 |
| UIG (Ours) | **124.45** | **0.123** |{{< /table-caption >}}
> 🔼 이 표는 논문의 5.4절(Ablation Studies)에서 무한한 도시 레이아웃 생성기(Unbounded Layout Generator, ULG)의 성능을 정량적으로 비교 분석한 결과를 보여줍니다.  세 가지 방법(IPSM, InfinityGAN, ULG)의 FID와 KID 점수를 비교하여 ULG의 우수성을 입증합니다. 생성된 이미지는 중앙을 기준으로 4096x4096 크기로 자르고 비교 분석했습니다.  FID(Fréchet Inception Distance)와 KID(Kernel Inception Distance)는 생성된 이미지의 품질을 측정하는 지표입니다. 낮은 값일수록 생성된 이미지의 품질이 실제 이미지와 유사하다는 것을 의미합니다.  이 표를 통해 ULG가 다른 두 방법보다 훨씬 더 좋은 성능을 보임을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> TABLE III: Quantitative Comparison of Ubounded Layout Generator (UIG). The best values are highlighted in bold. The generated images are centrally cropped to a size of 4096×\times×4096.
> </details>

{{< table-caption >}}
| BIG | Inst. | Encoder G | Encoder L | Pos.Enc. Hash | Pos.Enc. SinCos | FID ↓ | KID ↓ | DE ↓ | CE ↓ |
|---|---|---|---|---|---|---|---|---|---| 
| ✗ | ✗ | - | - | - | - | 195.1 | 0.126 | 0.185 | 0.162 |
| ✓ | ✗ | ✗ | ✓ | ✗ | ✓ | 167.8 | 0.094 | 0.157 | 0.087 |
| ✓ | ✓ | ✓ | ✗ | ✓ | ✗ | 196.8 | 0.124 | 0.165 | 0.159 |
| ✓ | ✓ | ✓ | ✗ | ✗ | ✓ | 197.9 | 0.132 | 0.162 | 0.152 |
| ✓ | ✓ | ✗ | ✓ | ✓ | ✗ | 182.3 | 0.111 | 0.155 | 0.092 |
| ✓ | ✓ | ✗ | ✓ | ✗ | ✓ | **88.48** | **0.049** | **0.150** | **0.063** |{{< /table-caption >}}
> 🔼 표 IV는 건물 인스턴스 생성기의 변형에 대한 정량적 비교 결과를 보여줍니다.  가장 좋은 값은 굵게 표시되어 있습니다.  'Inst.'는 '인스턴스 레이블'을, 'Pos.Enc.'는 '위치 인코딩'을 의미하며, 'G'는 '전역 인코더'를, 'L'는 '지역 인코더'를 나타냅니다. 이 표는 각 인코더(전역/지역)와 위치 인코딩 기법(해시, 사인-코사인) 조합에 따른 FID, KID, DE, CE 값을 비교하여 어떤 조합이 건물 인스턴스 생성 성능에 가장 효과적인지 보여줍니다. 인스턴스 레이블의 유무에 따른 성능 차이도 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> TABLE IV: Quantitative Comparison of Building Instance Generator Variants. The best values are highlighted in bold. Note that “Inst.” and “Pos.Enc.” refer to “Instance Labels” and “Positional Encoding”, while “G” and “L” denote “Global Encoder” and “Local Encoder”, respectively.
> </details>

{{< table-caption >}}
| VIG | Can. | Encoder G | Encoder L | Pos.Enc. Hash | Pos.Enc. SinCos | FID ↓ | KID ↓ | DE ↓ | CE ↓ |
|---|---|---|---|---|---|---|---|---|---| 
| ✗ | ✗ | - | - | - | - | 419.3 | 0.576 | 0.364 | 1.276 |
| ✓ | ✗ | ✓ | ✗ | ✗ | ✓ | 273.4 | 0.530 | 0.289 | 0.966 |
| ✓ | ✓ | ✓ | ✗ | ✓ | ✗ | 229.2 | 0.428 | 0.259 | 0.989 |
| ✓ | ✓ | ✓ | ✗ | ✗ | ✓ | 273.4 | 0.521 | 0.265 | 0.997 |
| ✓ | ✓ | ✗ | ✓ | ✓ | ✗ | **142.3** | **0.276** | **0.202** | **0.824** |
| ✓ | ✓ | ✗ | ✓ | ✗ | ✓ | 200.5 | 0.403 | 0.332 | 1.117 |{{< /table-caption >}}
> 🔼 이 표는 CityTopia 데이터셋의 차량 전용 도시에서 계산된 다양한 차량 인스턴스 생성기 변형에 대한 정량적 비교 결과를 보여줍니다.  최상의 값은 굵게 표시되어 있으며, 'Can.'은 '정규화', 'Pos.Enc.'는 '위치 인코딩', 'G'는 '전역 인코더', 'L'은 '지역 인코더'를 각각 나타냅니다.  각 변형은 FID, KID, DE, CE와 같은 다양한 지표를 사용하여 평가되었으며, 이는 이미지 품질, 깊이 정확도 및 멀티뷰 일관성을 반영합니다. 이 표는 여러 가지 차량 인스턴스 생성기 아키텍처를 비교하여 성능을 평가하고 분석하는 데 사용할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> TABLE V: Quantitative Comparison of Vehicle Instance Generator Variants. All metrics are computed on the vehicle-only city from the CityTopia dataset. The best values are highlighted in bold. Note that “Can.” and “Pos.Enc.” refer to “Canonicalization” and “Positional Encoding”, while “G” and “L” denote “Global Encoder” and “Local Encoder”, respectively.
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