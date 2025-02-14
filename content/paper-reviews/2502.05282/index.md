---
title: "Homeomorphism Prior for False Positive and Negative Problem in Medical Image Dense Contrastive Representation Learning"
summary: "의료 영상의 기하학적 유사성(GEMINI) 학습을 통해 거짓 양성 및 거짓 음성 문제를 해결하는 새로운 딥러닝 프레임워크 제시!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Segmentation", "🏢 Key Laboratory of New Generation Artificial Intelligence Technology and Its Interdisciplinary Applications (Southeast University), Ministry of Education",]
showSummary: true
date: 2025-02-07
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.05282 {{< /keyword >}}
{{< keyword icon="writer" >}} Yuting He et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-13 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.05282" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.05282" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

의료 영상 분석에서 밀집 표현 학습(DCRL)은 효율적이지만, 의료 영상의 특성으로 인해 거짓 양성과 거짓 음성 쌍이 대량으로 발생하는 문제가 있습니다. 이는 모델의 성능을 저하시키는 주요 원인 중 하나입니다. 기존 연구들은 이 문제를 해결하기 위해 다양한 방법을 제시했지만, 의료 영상 고유의 특성을 충분히 고려하지 못했습니다.

본 논문에서는 의료 영상의 고유한 위상적 특성을 활용한 새로운 프레임워크인 GEMINI를 제안합니다. GEMINI는 변형 가능한 동형 사상 학습(DHL)을 통해 거짓 음성 문제를 완화하고, 기하학적 의미 유사성(GSS)을 통해 양성 쌍의 신뢰도를 높여 거짓 양성 문제를 개선합니다. 실험 결과, GEMINI는 기존 방법들보다 우수한 성능을 보였으며, 특히 적은 양의 데이터로도 높은 성능을 달성할 수 있음을 보여주었습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 의료 영상 고유의 위상적 특성을 활용한 새로운 딥러닝 프레임워크 GEMINI를 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 변형 가능한 동형 사상 학습(DHL)을 통해 거짓 음성 문제 완화 및 거짓 양성 문제 개선 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 기하학적 의미 유사성(GSS)을 통해 양성 쌍 학습 신뢰도 향상 및 성능 개선 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 의료 영상의 고유한 특성으로 인해 발생하는 **거짓 양성 및 거짓 음성 문제**를 해결하기 위한 새로운 방법을 제시하여 의료 영상 분석 연구에 **중요한 발전**을 가져올 수 있습니다. 특히, **데이터 및 주석 비용 절감**이라는 중요한 문제에 대한 해결책을 제시하고, 향후 연구를 위한 새로운 방향을 제시합니다.  **의료 영상 분야의 다양한 응용 분야**에 적용될 수 있으며, **효율적인 의료 영상 학습 방법**에 대한 새로운 패러다임을 제시합니다. 이는 **의료 영상 분석 분야의 발전**에 크게 기여할 뿐만 아니라, **다른 영상 분석 분야**에도 적용될 수 있는 잠재력을 가지고 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.05282/x1.png)

> 🔼 그림 1은 의료 이미지의 밀집 표상 학습(DCRL)에서 대규모 FP&N 문제를 보여줍니다. A)는 일관되거나 구별되는 표상을 위해 DCRL이 양수 및 음수 특징 쌍을 당기고 미는 과정을 보여줍니다. 그러나 B)는 의료 이미지의 특성으로 인해 신뢰할 수 없는 대응 관계 발견이 발생하고, 이로 인해 DCRL에서 대규모 FP&N 특징 쌍이라는 열린 문제가 발생하여 표상 학습 능력이 매우 제한된다는 것을 보여줍니다.  즉, 의료 영상의 특성(의미적 의존성, 연속성, 중복)으로 인해 정확한 픽셀 매칭이 어려워, 잘못된 양성/음성 쌍이 많이 생겨 학습 성능이 저하되는 문제를 시각적으로 보여주는 그림입니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: The DCRL with the large-scale FP&N problem. A) The DCRL pulls and pushes the positive and negative feature pairs for consistent or distinct representation. However, B) medical images’ properties cause unreliable correspondence discovery, resulting in the open problem of large-scale FP&N features pairs in DCRL and extremely limiting the representation learning ability.
> </details>





{{< table-caption >}}
| Dataset | Type | Num | FS-Semi | SS-MIP |
|---|---|---|---|---|
| ASOCA [71] | 3D cardiac CT | 60 | √ |  |
| CAT08 [72] | 3D cardiac CT | 32 | √ |  |
| WHS-CT [73] | 3D cardiac CT | 60 | √ |  |
| CANDI [74] | 3D brain MRI | 103 | √ | √ |
| SCR [75] | 2D chest X-ray | 247 | √ | √ |
| KiPA22 [9] | 3D kidney CT | 130 |  | √ |
| ChestX-ray8 [76] | 2D chest X-ray | 112,120 |  | √ |{{< /table-caption >}}

> 🔼 본 논문에서는 GEMINI의 다양한 변형을 실험하기 위해 총 7개의 공개적으로 이용 가능한 데이터셋을 사용했습니다.  표에는 각 데이터셋의 유형(2D 또는 3D 의료 영상), 데이터셋에 포함된 의료 영상의 수, 그리고 본 논문에서 수행된 두 가지 실험 유형인 퓨샷 세미슈퍼바이즈드 학습과 셀프슈퍼바이즈드 의료 영상 사전 학습에 각 데이터셋이 사용되었는지 여부를 나타냅니다.  모든 데이터셋은 GEMINI의 재현성을 높이기 위해 선택되었으며, 이를 통해 연구 결과의 신뢰성을 높였습니다.
> <details>
> <summary>read the caption</summary>
> TABLE I: Total seven publicly available datasets are involved in this paper for the experiments of our GEMINI’s variants, achieving great reproducibility.
> </details>





### In-depth insights


#### Homeomorphism Prior
본 논문에서 제안하는 ‘Homeomorphism Prior’는 의료 영상의 고유한 특징인 **위상적 일관성(topological consistency)**을 활용하여 의료 영상의 밀집 표현 학습(Dense Contrastive Representation Learning, DCRL)에서 발생하는 과다한 위양성(false positive) 및 위음성(false negative) 쌍의 문제를 해결하는 핵심 전략입니다.  **인체의 해부학적 구조는 일관성을 유지**하므로, 서로 다른 의료 영상 간에도 위상적으로 동일한 특징을 공유한다는 점에 착안했습니다.  이를 통해, 변형 가능한 사상(deformable mapping)을 학습하여 영상 간의 신뢰할 만한 픽셀 매칭을 이끌어내고, **부정확한 매칭을 감소**시키는 효과를 거둡니다.  이러한 기법은 위양성 및 위음성 쌍의 문제를 직접적으로 해결하는 것이 아니라, **위상적 제약 조건을 통해 탐색 공간을 축소**하고, **음성 쌍의 학습을 간접적이면서도 효율적으로 유도**하는 방식으로 작동합니다.  **기하학적 의미론적 유사성(Geometric Semantic Similarity, GSS)**을 통해 의미론적으로 일치하는 영역을 효과적으로 식별하고, 이를 통해 양성 쌍을 신뢰성 있게 구성함으로써 학습 효율을 높입니다.  결과적으로, ‘Homeomorphism Prior’는 DCRL의 신뢰성과 효율성을 크게 향상시키는 혁신적인 접근 방식으로 평가될 수 있습니다.

#### GEMINI Learning
본 논문에서 제안하는 GEMINI 학습은 의료 영상의 밀집 표현 학습에서 거짓 양성 및 거짓 음성 쌍의 문제를 해결하기 위한 새로운 패러다임입니다. **의료 영상의 고유한 위상 동형성(homeomorphism)을 활용**, 신뢰할 수 있는 대응 관계 발견을 가능하게 합니다.  **변형 위상 동형성 학습(DHL)**은 의료 영상의 위상 동형성을 모델링하여 변형 매핑을 추정, 대응 관계 학습의 효율성을 높입니다. **기하 의미론적 유사성(GSS)**은 특징 내의 의미론적 정보를 추출하여 대응 관계 학습의 정확성을 높입니다.  GEMINI 학습은 거짓 양성 및 거짓 음성 쌍 문제를 효과적으로 줄이고, 다양한 의료 영상 분할 및 전이 학습 작업에서 우수한 성능을 보입니다. 특히, 소량의 데이터만으로도 높은 정확도를 달성하여 **데이터 효율성**을 크게 향상시킵니다.  **강건성과 유연성** 또한 뛰어나 여러 의료 영상 분석 작업에 적용 가능합니다.

#### DCRL Improvements
본 논문은 의료 영상의 밀집 표현 학습(DCRL)에서 거짓 양성(FP)과 거짓 음성(FN) 쌍 문제를 해결하기 위한 새로운 방법론인 GEMINI 학습을 제시합니다. **GEMINI는 의료 영상의 고유 위상(homeomorphism) 사전 정보를 DCRL에 통합하여 신뢰할 수 있는 대응 관계 발견을 가능하게 합니다.**  이는 변형 가능한 위상 학습(DHL)과 기하 의미 유사성(GSS)이라는 두 가지 주요 구성 요소를 통해 달성됩니다. DHL은 의료 영상의 위상을 모델링하고 변형 가능한 매핑을 학습하여 위상 보존 조건 하에서 픽셀의 대응 관계를 추정합니다.  GSS는 특징에서 의미 정보를 추출하여 대응 관계 학습의 정렬 정도를 측정하는 데 사용되어, 변형의 학습 효율과 성능을 향상시키고 신뢰할 수 있게 양성 쌍을 구성합니다.  결과적으로, **GEMINI는 FP와 FN 문제를 효과적으로 줄여 DCRL의 성능을 크게 향상시킵니다.** 여러 데이터셋에서의 실험 결과는 기존 방법보다 GEMINI의 우수성을 보여줍니다.  특히, 적은 수의 레이블을 사용하는 반지도 학습 설정에서 GEMINI의 성능이 더욱 뛰어납니다. **의료 영상의 데이터 수집 및 어노테이션 비용을 줄이는 데 기여하며, 의료 영상 분석 분야에 큰 발전을 가져올 것으로 기대됩니다.**

#### FP&N Mitigation
본 논문에서 제시된 의료 영상의 밀집 표현 학습에서의 가짜 양성(FP) 및 가짜 음성(FN) 쌍 문제 완화 전략은 **기하학적 시각적 밀집 유사성(GEMINI) 학습**이라는 프레임워크를 중심으로 이루어집니다. 이는 의료 영상의 고유 위상 기하학적 구조를 활용하여 신뢰할 수 있는 대응 관계 발견을 가능하게 합니다.  **변형 위상 동형 학습(DHL)**은 두 영상 간의 위상 동형 매핑을 추정하여 가짜 음성 쌍을 부드럽게 학습하고, **기하학적 의미 유사성(GSS)**은 특징 내 의미 정보를 활용하여 신뢰할 수 있는 양성 쌍을 구성합니다.  **DHL의 부드러운 음성 쌍 학습**은 경계를 명확히 구분 짓는 대신 연속적인 의료 영상 신호의 특성을 반영하며, **GSS의 양성 쌍 학습 전략**은 의미 정보를 고려하여 더욱 정확한 매핑을 가능하게 합니다.  이러한 방법을 통해 의료 영상의 고유한 특성에 따른 FP&N 문제를 효과적으로 완화하며, 밀집 표현 학습의 효율성 및 성능 향상을 도모합니다.

#### Future Directions
미래 연구 방향은 크게 세 가지로 나눌 수 있습니다. 첫째, **의료 영상의 다양한 유형에 대한 GEMINI 학습의 확장성**입니다. 현재 GEMINI는 형태 동형성을 가진 의료 영상에 초점을 맞추고 있으나, 병변이 있는 영상과 같이 형태 동형성이 없는 영상에도 적용할 수 있도록 확장해야 합니다. 둘째, **영상과 비영상 간의 형태 동형성 매핑 연구**입니다. 영상과 비영상 간의 대응 관계를 효율적으로 학습하는 새로운 방법을 개발하여 GEMINI의 적용 범위를 넓힐 수 있습니다. 셋째, **계산 비용 감소 및 효율적인 학습 방법 개발**입니다. GEMINI는 계산 비용이 높은 편이므로, 경량화된 모델을 개발하거나 더욱 효율적인 학습 방법을 개발하여 실제 의료 현장에 적용 가능성을 높여야 합니다.  **특히,  대규모 FP&N 문제 해결에 대한 지속적인 연구는 GEMINI의 성능 향상에 필수적이며, 다양한 의료 영상 유형 및 임상 시나리오에 대한 적용성을 확보하는 것이 중요합니다.**


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.05282/x2.png)

> 🔼 그림 2는 의료 이미지의 고유 위상에 따라 픽셀 간 대응 관계를 신뢰할 수 있도록 하는 동형 사상 우선 순위에 대해 설명합니다. A)는 위상 동형 사상 개념을 도입하여, 위상 동형인 객체는 점대점 대응 관계를 위해 위상을 보존하는 동형 사상 매핑을 통해 위상을 정렬할 수 있음을 보여줍니다. B)는 인체의 일관성으로 인해 의료 이미지가 이미지 공간에서 위상 동형이라는 사실을 보여줍니다. 이는 의료 이미지의 고유 위상 하에서 픽셀 간 대응 관계를 위한 변형 가능 매핑을 구성하기 위한 사전 지식을 제공합니다. 이를 통해 쌍을 찾는 공간을 효과적으로 줄일 수 있습니다. C)는 의료 이미지 DCRL에서 신뢰할 수 있는 픽셀 간 대응 관계를 찾을 수 있는 잠재력을 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: The homeomorphism prior enables the pixel-wise correspondence discovery under the condition of medical images’ inherent topology, promoting its reliability. A) In topologie, the homeomorphic objects are able to align their topologies via a homeomorphism mapping for point-to-point correspondence with topological preservation. B) Due to the consistency of human body, the medical images are homeomorphic in image space. This provides prior knowledge to construct a deformable mapping for the pixels’ correspondence under the condition of their inherent topology, which will effectively reduce the searching space of pairing. C) This gives a potential to enable a reliable pixel-wise correspondence discovery in the medical image DCRL.
> </details>



![](https://arxiv.org/html/2502.05282/x3.png)

> 🔼 그림 3은 의료 이미지에 homeomorphism prior를 적용한 GEMINI가 DCRL에서 신뢰할 수 있는 correspondence discovery를 달성하는 방법을 보여줍니다. 두 가지 측면이 있습니다. a) DHL(3.2절)은 음성 쌍의 소프트 학습을 위한 변형 가능한 매핑을 학습합니다. b) GSS(3.3절)는 correspondence 정도의 측정에 의미적 유사성을 융합하여 양성 쌍을 신뢰할 수 있도록 구성합니다. 'opt'는 최적화를 나타냅니다. 자세한 내용은 보충 자료의 D절을 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Figure 3: Our GEMINI embedded the homeomorphism prior in medical images achieves a reliable correspondence discovery in DCRL. It has two aspects: a) The DHL (Sec.3.2) learns a deformable mapping for soft learning of negative pairs. b) The GSS (Sec.3.3) fuses semantic similarity into the measurement of correspondence degree to construct the positive pairs reliably. The “opt” is the optimization. More details are described in Sec.D of our Supplementary Materials.
> </details>



![](https://arxiv.org/html/2502.05282/x4.png)

> 🔼 그림 4는 GSS 손실의 기울기가 양성 쌍의 명시적 대조를 동시에 학습하고 DHL에서 음성 쌍의 암묵적이고 부드러운 학습을 유도하는 과정을 보여줍니다.  GSS 손실은 양성 쌍의 일관성 있는 특징을 학습하도록 백본 네트워크를 훈련합니다. 동시에 DHL의 기울기는 음성 쌍의 구별되는 특징을 학습하도록 백본 네트워크를 유도하여, 양성 쌍과 음성 쌍 모두에 대해 강력한 표현 학습을 가능하게 합니다. 이는 연속적인 의료 영상 신호의 특성을 고려하여, 음성 쌍을 명확하게 구분하는 대신 부드러운 학습을 통해 효율성을 높인다는 점에서 중요합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: The gradients from the loss of our GSS simultaneously train the explicit contrast of positive pairs and drive the implicit and soft learning in our DHL.
> </details>



![](https://arxiv.org/html/2502.05282/x5.png)

> 🔼 그림 5는 GEMINI 학습의 작동 방식에 대한 직관적인 설명을 보여줍니다. (a)는 목적 함수 (식 8)의 두 가지 최적화 목표가 어떻게 신뢰할 수 있는 양성 쌍 학습과 음성 쌍의 암묵적 학습을 유도하는지 보여줍니다.  양성 쌍의 경우, homeomorphism prior는 매칭 검색 공간을 줄이고, 신뢰할 수 있는 매칭을 가능하게 합니다. 음성 쌍의 경우, DHL(변형 동형사상 학습)을 통해 음성 쌍이 명시적으로 구분되지 않고, 대신 기울기 기반의 암묵적 학습을 통해 다루어집니다. (b)는 DHL에서 생성된 기울기가 특징 쌍의 부드러운 학습을 어떻게 이끄는지 보여줍니다.  즉, 일치하지 않는 특징들은 구별되는 특징을 갖도록 학습되고, 일치하는 특징들은 일관된 특징을 갖도록 학습됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Intuitions on behavior. a) The two optimization objectives in Equ.8 for θ𝜃\thetaitalic_θ drive the reliable learning of positive and implicit learning of negative pairs. b) The feature pairs are learned softly via the gradient from the DHL.
> </details>



![](https://arxiv.org/html/2502.05282/x6.png)

> 🔼 그림 6은 본 논문에서 제안하는 GEMINI-Semi 방법이 세 가지 FS-Semi 의료 영상 분할 작업에서 기존 방법보다 훨씬 우수한 시각적 결과를 보여준다는 것을 보여줍니다.  세 가지 작업은 심장 구조 분할, 뇌 조직 분할, 흉부 구조 분할이며, 각 작업에서 GEMINI-Semi는 기존 방법보다 더욱 정확하고 완전한 분할 결과를 제공합니다. 특히, 세밀한 구조나 저대비 영역에서 GEMINI-Semi의 우수성이 더욱 두드러집니다. 이는 GEMINI-Semi가 의료 영상의 고유한 위상적 특성을 활용하여 신뢰할 수 있는 대응 관계를 찾고, 효율적인 특징 표현 학습을 가능하게 하기 때문입니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Our GEMINI-Semi has significant visual superiority on three FS-Semi medical image segmentation tasks.
> </details>



![](https://arxiv.org/html/2502.05282/x7.png)

> 🔼 이 그림은 논문의 실험 2: 자기 지도 학습 의료 영상 사전 훈련(SS-MIP) 섹션에 속하며, 세 가지 하위 작업(SCR25, KiPA22, CANDI)에서 GEMINI-MIP의 성능을 시각적으로 보여줍니다.  GEMINI-MIP은 세 가지 작업 모두에서 다른 방법들보다 훨씬 우수한 시각적 결과를 보여주는 것을 확인할 수 있습니다.  특히, 세밀한 구조와 경계선을 더 잘 포착하고, 노이즈나 오류가 적은 결과를 보여줍니다. 이는 GEMINI-MIP의 강력한 표현 능력과 신뢰할 수 있는 픽셀 단위 대응 발견 기능을 시각적으로 증명하는 것입니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Our GEMINI-MIP also has very significant visual superiority in the three downstream tasks.
> </details>



![](https://arxiv.org/html/2502.05282/x8.png)

> 🔼 그림 8은 제안된 GEMINI 프레임워크에서 각 구성 요소의 중요한 역할을 보여주는 추가 실험 결과입니다.  특히 3D 심장 구조(T1)와 2D 흉부 구조(T3) 데이터셋에 대한 실험 결과를 보여줍니다.  실험은 연속성 학습(C)과 전단사 사상 학습(B)을 포함하여 여러 가지 조합으로 진행되었습니다. 그래프는 각 구성요소를 추가했을 때의 분할 정확도(Segmentation DSC) 변화를 보여줍니다.  이를 통해 각 구성요소가 GEMINI의 성능 향상에 얼마나 기여하는지 정량적으로 확인할 수 있습니다. 단순히 DSC 수치뿐 아니라, 연속성(Continuity) 및 전단사 사상(Bijection) 학습이 모델 성능 향상에 미치는 영향을 명확하게 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: The ablation studies on the “T1: 3D Cardiac structures” and “T3: 2D Chest structures” demonstrate the great contributions of the components in our framework. The “C” and “B” are the learning for continuity and bijection.
> </details>



![](https://arxiv.org/html/2502.05282/x9.png)

> 🔼 그림 9는 3D 심장 구조(T1)에 대한 초매개변수 제거 연구 결과를 보여줍니다.  매끄러움 손실(λs⁢m⁢o), 양성 쌍 가중치(λp⁢o⁢s), 그리고 GVS 손실(λG⁢V⁢S)의 가중치가 변형의 매끄러움에 미치는 영향을 보여줍니다.  |Jϕ|≤0(%)는 변형의 매끄러움을 평가하는 자코비 행렬을 나타냅니다.  각 가중치의 증가는 초기에 성능 향상을 가져오지만, 특정 지점을 넘어서면 성능 저하를 야기합니다. 이는 매끄러움 손실이 과도하게 적용될 경우 변형 정확도가 감소하고, 양성 쌍 가중치가 과도하게 커지면 모델이 모든 특징을 일관되게 나타내려고 하여 차별성이 저하되며, GVS 손실 가중치가 과도하게 커지면 외관의 제약으로 인해 유사도 측정이 부정확해지기 때문입니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: The ablation of the hyper-parameters on the “T1: 3D Cardiac structures” show the effects from the weight of the smoothness loss λs⁢m⁢osubscript𝜆𝑠𝑚𝑜\lambda_{smo}italic_λ start_POSTSUBSCRIPT italic_s italic_m italic_o end_POSTSUBSCRIPT, the positive pairs λp⁢o⁢ssubscript𝜆𝑝𝑜𝑠\lambda_{pos}italic_λ start_POSTSUBSCRIPT italic_p italic_o italic_s end_POSTSUBSCRIPT, and the GVS loss λG⁢V⁢Ssubscript𝜆𝐺𝑉𝑆\lambda_{GVS}italic_λ start_POSTSUBSCRIPT italic_G italic_V italic_S end_POSTSUBSCRIPT. The |Jϕ|≤0subscript𝐽italic-ϕ0|J_{\phi}|\leq 0| italic_J start_POSTSUBSCRIPT italic_ϕ end_POSTSUBSCRIPT | ≤ 0 (%) is Jacobian matrix [41] which evaluates smoothness of the deformation.
> </details>



![](https://arxiv.org/html/2502.05282/x10.png)

> 🔼 그림 10은 논문의 실험 1(Few-shot Semi-supervised Medical Image Segmentation) 부분, 특히 3D 심장 구조 분할 작업에서 학습 과정 동안 변형(deformation)이 시각적으로 어떻게 나타나는지를 보여줍니다. 첫 번째 행은 분할(segmentation) 및 변형 성능을 보여주는 선 그래프입니다. 두 번째 행은 변형 정도를 보여주는 그리드(grid)이며, 세 번째 행은 학습 과정 중 변형된 이미지 A를 보여줍니다.  즉, 이 그림은 모델이 학습하면서 이미지를 어떻게 변형시키는지, 그리고 그 변형이 분할 성능과 어떤 관계가 있는지를 시각적으로 보여주는 상세한 설명을 제공합니다.  특히, 3D 심장 구조의 복잡한 형태를 고려할 때 변형 과정의 시각화는 모델의 성능 이해에 매우 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: The visualization of the deformation in the learning process on the “T1: 3D Cardiac structures”. The first row is the line chart of the segmentation and deformation performance. The second row is the grids which demonstrates the deformation degree. The third row is the deformed image A during the learning process.
> </details>



![](https://arxiv.org/html/2502.05282/x11.png)

> 🔼 그림 11은 자기 지도 학습 기반 의료 영상 사전 학습(SS-MIP)에서 사전 학습 데이터 양과 미세 조정 데이터 양에 따른 성능 변화를 보여줍니다.  (a)는 사전 학습 데이터 양을 다르게 했을 때 SCR25 데이터셋에서의 성능 변화를 보여줍니다. (b)와 (c)는 각각 SCR 데이터셋(내부 장면)과 KiPA22 데이터셋(외부 장면)에서 미세 조정 데이터 양을 변화시켰을 때의 성능 변화를 보여줍니다. GEMINI-MIP 모델은 적은 양의 데이터로도 높은 성능을 달성하는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: The pre-training and fine-tuning data amount analysis on SS-MIP.
> </details>



![](https://arxiv.org/html/2502.05282/x12.png)

> 🔼 그림 12는 제안된 GEMINI-MIP 모델이 inner-scene(같은 이미지 카테고리 내 전이) 및 inter-scene(다른 이미지 카테고리 간 전이) 전이 작업 모두에서 우수한 학습 효율성을 보여줌을 시각적으로 보여줍니다.  inner-scene 전이 작업에서는 빠르게 수렴하고 높은 정확도를 달성하지만, inter-scene 전이 작업에서는 학습 속도가 다소 느려지고 정확도가 다소 감소합니다. 하지만 GEMINI-MIP는 두 경우 모두에서 다른 방법들보다 우월한 성능을 나타냅니다. 이는 GEMINI-MIP가 이미지의 토폴로지적 일관성을 활용하여 강력하고 안정적인 특징 표현을 학습하기 때문입니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Our GEMINI-MIP has powerful learning efficiency both in the inner-scene and inter-scene transferring tasks.
> </details>



![](https://arxiv.org/html/2502.05282/x13.png)

> 🔼 그림 13은 GEMINI-MIP에서 기본 학습 과제의 필요성을 보여줍니다. 기본 학습 과제 없이 학습할 경우 초기 표현의 부족으로 인해 GVS 손실이 느리게 수렴하고, GSS와 GVS의 대응 학습이 제한됩니다. 기본 학습 과제(자기 복원)를 추가하면 기본적인 의미 영역 표현으로부터 시작하여 대응 학습이 효율적으로 이루어집니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: The necessity of the fundament in our GEMINI-MIP. When learning without the fundamental learning task, the GVS loss converges slowly due to the initial weak representation limiting the GSS and GVS for correspondence. When adding the fundament (self-restoration), warmup from the basic representation of semantic regions drives correspondence learning efficiently.
> </details>



![](https://arxiv.org/html/2502.05282/x14.png)

> 🔼 그림 14는 대규모 FP 문제 평가를 보여줍니다. DenseCL에서 사용된 특징 유사도를 기반으로 구성된 실제 양성(TP) 쌍은 전경 영역의 5.79%만 차지하지만, GEMINI는 60.74%의 TP 쌍을 가져올 수 있습니다.  이는 GEMINI가 의료 이미지의 고유한 토폴로지 특성을 활용하여 보다 신뢰할 수 있는 대응 관계를 발견하고, 따라서 더 정확한 양성 쌍을 생성할 수 있음을 시사합니다. DenseCL의 방법은 의료 이미지의 특징 유사성만 고려하여 많은 잘못된 양성 쌍을 생성하는 반면, GEMINI는 이미지의 토폴로지적 특성을 고려하여 보다 정확한 양성 쌍을 식별합니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: The evaluation of the large-scale FP problem. The true positive (TP) pairs constructed by the features’ similarity (used in DenseCL) only occupy the 5.79% of the foreground region, and our GEMINI is able to bring 60.74% TP pairs.
> </details>



![](https://arxiv.org/html/2502.05282/x15.png)

> 🔼 그림 15는 잘못된 양성/음성 쌍이 학습에 미치는 심각한 영향을 보여줍니다. (a)는 심장 CT 이미지에서 잘못된 양성/음성 쌍을 사용한 피팅 과정을 보여줍니다. (b)는 피팅된 사례에 대한 모델의 학습된 분할 능력과 다른 테스트 사례에 대한 일반화 능력을 보여줍니다.  (a)에서는 잘못된 양성/음성 쌍이 학습 과정에 혼란을 일으켜 모델이 목표 이미지에 제대로 맞춰지지 못하는 것을 보여줍니다. 잘못된 양성/음성 쌍의 비율을 줄이면 모델이 목표 이미지에 점진적으로 맞춰지고 일반화 능력도 향상됨을 보여줍니다. 이는 잘못된 양성/음성 쌍의 제거가 학습에 필수적임을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 15: The FP and FN pairs have a serious impact on learning. a) The fitting process with FP and FN pairs on a cardiac CT image. b) The models’ learned segmentation ability on the fitted case and their generalization ability on another testing case.
> </details>



![](https://arxiv.org/html/2502.05282/x16.png)

> 🔼 그림 16은 수용 영역 크기 r과 네트워크 매개변수 양에 대한 추가 연구 결과를 보여줍니다. (a)는 FS-Semi 설정의 T1에서 수용 영역 크기 r을 증가시키면서 분할 성능을 평가한 결과입니다. 수용 영역 크기가 증가함에 따라 성능이 안정적으로 유지됨을 보여줍니다. 이는 백본 네트워크와 디포머 네트워크가 함께 특징 표현을 학습하기 때문에, 디포머 네트워크의 수용 영역이 작더라도 큰 수용 영역에서 특징을 추출하여 사용하기 때문입니다. (b)는 사전 훈련된 네트워크에서 매개변수 양(백만 단위, M)을 늘리면서 미세 조정 성능을 평가한 결과입니다. 매개변수 양이 증가함에 따라 성능이 향상되지만, 특정 지점을 넘어서면 성능 향상폭이 줄어드는 것을 보여줍니다. 이는 네트워크 용량이 증가함에 따라 더 많은 특징을 학습할 수 있지만, 네트워크 용량이 과도하게 커지면 과적합이 발생할 수 있기 때문입니다. 이를 통해 수용 영역 크기와 매개변수 양이 모델 성능에 미치는 영향을 효과적으로 분석합니다.
> <details>
> <summary>read the caption</summary>
> Figure 16: The ablation study of the receptive field size r𝑟ritalic_r and the network parameter amounts. a) The segmentation performance on the T1 of FS-Semi setting with the increasing of the receptive field size r𝑟ritalic_r. b) The fine-tuning performance with the enlarging of the parameter amount (million, M𝑀Mitalic_M) in the pre-trained networks.
> </details>



![](https://arxiv.org/html/2502.05282/x17.png)

> 🔼 그림 17은 학습된 픽셀 표현의 t-SNE 시각화를 보여줍니다. 확대된 보기에서 픽셀의 좌표를 제공하여 공간적 관계를 보여줍니다.  t-SNE는 고차원 데이터를 저차원 공간(이 경우 2차원)에 투영하여 데이터 포인트 간의 유사성을 시각적으로 표현하는 기법입니다. 이 그림은 서로 다른 의미 영역의 픽셀들이 얼마나 잘 분리되어 표현되는지를 보여주는 데 초점을 맞춥니다.  즉, 의미가 비슷한 픽셀들은 서로 가깝게, 의미가 다른 픽셀들은 서로 멀리 떨어져서 나타나도록 학습이 잘 되었는지를 확인할 수 있습니다.  확대된 영역의 좌표 정보는 픽셀들의 공간적 위치와 시각적 표현의 관계를 명확히 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 17: The t-SNE visualization of the learned pixel representations. We provide the coordinates of pixels in a zoomed view, indicating their spatial relationship.
> </details>



![](https://arxiv.org/html/2502.05282/x18.png)

> 🔼 그림 18은 GEMINI의 전체 학습 과정을 보여줍니다. (a)는 전체 프레임워크의 추론 과정을 보여줍니다. 마지막 줄의 회색 경로는 자가 지도 학습 전훈련(GEMINI-MIP) 및 반지도 학습 분할(GEMINI-Semi)의 GEMINI 변형에서 추가적인 학습 부분입니다. (b)는 전체 프레임워크를 최적화하기 위한 손실 계산 과정입니다.  GEMINI는 자가 지도 학습 전훈련과 반지도 학습 분할 두 가지 모두에 대해 변형 모델을 가지고 있습니다.  (a)는 두 가지 변형 모델의 추론 과정을 보여주는 데, 마지막 단계에서 회색으로 표시된 추가 학습 부분이 중요합니다.  (b)는 손실함수 계산을 통해 전체 네트워크를 최적화하는 과정을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 18: The overall training diagram of our GEMINI. a) The inference process of the whole framework. The gray path in the last line is the additional learning part in the variants of our GEMINI in self-supervised pre-training (GEMINI-MIP) and semi-supervised segmentation (GEMINI-Semi). b) The loss calculation to optimize the whole framework.
> </details>



![](https://arxiv.org/html/2502.05282/x19.png)

> 🔼 그림 19는 GEMINI의 세부 아키텍처를 보여줍니다. (a)는 백본 아키텍처로, 3D 영상 작업에는 3D U-Net을, 2D 영상 작업에는 2D U-Net을 사용합니다. (b)는 변형 네트워크 아키텍처로, 경량화된 U-Net을 사용합니다. (c)와 (d)는 각각 GEMINI-Semi의 분할 헤드와 GEMINI-MIP의 자기 복원 헤드를 보여줍니다.  백본 네트워크는 이미지의 특징을 추출하고, 변형 네트워크는 두 이미지 간의 대응 관계를 학습합니다. GEMINI-Semi에서는 분할 헤드가 추가되어 분할 작업을 수행하고, GEMINI-MIP에서는 자기 복원 헤드가 추가되어 자기 복원 작업을 수행합니다.
> <details>
> <summary>read the caption</summary>
> Figure 19: The detailed architecture of our GEMINI. a) The backbone architecture utilizes the 3D U-Net in 3D image tasks and 2D U-Net in 2D image tasks. b) The deformer network architecture utilized a lightweight U-Net. c-d) The segmentation head in the variant of GEMINI-Semi and the self-restoration head in the variant of GEMINI-MIP.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
Type|Method|HP|T1: 3D cardiac structures DSC<sub>±std</sub>↑|T1: 3D cardiac structures AVD<sub>±std</sub>↓|T2: 3D brain tissues DSC<sub>±std</sub>↑|T2: 3D brain tissues AVD<sub>±std</sub>↓|T3: 2D chest structures DSC<sub>±std</sub>↑|T3: 2D chest structures AVD<sub>±std</sub>↓|AVG
---|---|---|---|---|---|---|---|---|---|---
Full|U-Net [80]|×|-|-|88.7<sub>±1.2</sub>|0.31<sub>±0.04</sub>|96.1<sub>±1.4</sub>|2.28<sub>±1.00</sub>|- 
Five|U-Net [80]|×|84.3<sub>±9.6</sub>|2.43<sub>±2.14</sub>|69.5<sub>±8.8</sub>|1.59<sub>±0.84</sub>|83.4<sub>±6.9</sub>|10.34<sub>±4.80</sub>|79.1<sub>±8.4</sub>
Semi|UA-MT [81]|×|66.4<sub>±16.2</sub>|4.69<sub>±2.27</sub>|75.5<sub>±3.4</sub>|1.31<sub>±0.95</sub>|83.9<sub>±6.2</sub>|9.52<sub>±4.03</sub>|75.3<sub>±8.6</sub>
|CPS [84]|×|87.4<sub>±5.4</sub>|1.40<sub>±0.76</sub>|37.1<sub>±1.8</sub>|unable|63.2<sub>±1.4</sub>|19.57<sub>±5.67</sub>|62.6<sub>±2.9</sub>
|MASSL [82]|×|77.4<sub>±8.7</sub>|9.07<sub>±3.11</sub>|80.5<sub>±3.1</sub>|0.92<sub>±0.43</sub>|81.9<sub>±7.0</sub>|10.99<sub>±4.58</sub>|79.9<sub>±6.3</sub>
|DPA-DBN [83]|×|68.0<sub>±14.5</sub>|5.75<sub>±3.89</sub>|68.7<sub>±8.2</sub>|3.90<sub>±2.39</sub>|67.4<sub>±8.7</sub>|24.05<sub>±6.75</sub>|68.0<sub>±10.5</sub>
Atlas|VM [35]|√|81.0<sub>±6.1</sub>|2.13<sub>±0.78</sub>|83.1<sub>±1.8</sub>|0.56<sub>±0.08</sub>|59.9<sub>±5.0</sub>|15.36<sub>±4.34</sub>|74.7<sub>±4.3</sub>
|LC-VM [57]|√|81.7<sub>±6.0</sub>|2.04<sub>±0.77</sub>|83.0<sub>±1.8</sub>|0.56<sub>±0.07</sub>|60.2<sub>±7.4</sub>|14.72<sub>±4.89</sub>|74.9<sub>±5.1</sub>
|LT-Net [56]|√|77.8<sub>±7.8</sub>|2.25<sub>±0.95</sub>|82.6<sub>±1.2</sub>|0.57<sub>±0.05</sub>|60.4<sub>±7.4</sub>|14.62<sub>±4.84</sub>|73.6<sub>±5.5</sub>
LRLS|DeepAtlas [63]|√|87.9<sub>±4.3</sub>|1.30<sub>±0.57</sub>|79.3<sub>±2.6</sub>|0.74<sub>±0.12</sub>|64.8<sub>±9.6</sub>|12.87<sub>±3.56</sub>|77.3<sub>±5.5</sub>
|DataAug [62]|√|82.2<sub>±5.2</sub>|2.04<sub>±0.73</sub>|83.9<sub>±1.2</sub>|0.55<sub>±0.06</sub>|22.2<sub>±2.8</sub>|unable|62.8<sub>±3.1</sub>
|DeepRS [60]|√|87.0<sub>±5.0</sub>|1.60<sub>±0.90</sub>|73.0<sub>±5.9</sub>|0.93<sub>±0.25</sub>|86.0<sub>±5.6</sub>|8.55<sub>±3.98</sub>|82.0<sub>±5.5</sub>
|PC-Reg-RT [41]|√|88.5<sub>±4.9</sub>|1.23<sub>±0.72</sub>|73.1<sub>±3.1</sub>|1.09<sub>±0.17</sub>|59.1<sub>±3.6</sub>|20.71<sub>±5.21</sub>|73.6<sub>±3.9</sub>
|BRBS [8]|√|91.1<sub>±3.9</sub>|0.93<sub>±0.57</sub>|87.2<sub>±1.0</sub>|0.43<sub>±0.05</sub>|71.5<sub>±6.4</sub>|10.85<sub>±2.99</sub>|83.3<sub>±3.8</sub>
DCRL|VADeR [2]|×|85.4<sub>±4.7</sub>|1.69<sub>±0.77</sub>|81.2<sub>±3.2</sub>|0.59<sub>±0.13</sub>|79.9<sub>±5.8</sub>|8.95<sub>±3.37</sub>|82.2<sub>±4.6</sub>
|DenseCL [3]|×|87.3<sub>±4.3</sub>|1.52<sub>±0.79</sub>|83.9<sub>±1.9</sub>|0.48<sub>±0.09</sub>|77.1<sub>±8.8</sub>|12.11<sub>±6.51</sub>|82.8<sub>±5.0</sub>
|SetSim [4]|×|87.0<sub>±4.5</sub>|1.60<sub>±0.84</sub>|81.2<sub>±3.0</sub>|0.58<sub>±0.13</sub>|79.0<sub>±7.3</sub>|11.72<sub>±5.03</sub>|82.4<sub>±4.9</sub>
|DSC-PM [1]|×|87.0<sub>±4.6</sub>|1.60<sub>±0.86</sub>|82.6<sub>±2.1</sub>|0.53<sub>±0.09</sub>|85.7<sub>±6.2</sub>|7.33<sub>±3.32</sub>|85.1<sub>±4.3</sub>
|PixPro [5]|×|89.5<sub>±3.9</sub>|1.31<sub>±0.75</sub>|86.3<sub>±1.2</sub>|0.38<sub>±0.04</sub>|83.3<sub>±8.7</sub>|8.73<sub>±4.55</sub>|86.4<sub>±4.6</sub>
|GLCL [49]|×|84.5<sub>±7.0</sub>|1.82<sub>±1.09</sub>|83.0<sub>±2.7</sub>|0.52<sub>±0.11</sub>|85.5<sub>±8.9</sub>|8.65<sub>±5.18</sub>|84.3<sub>±6.2</sub>
DCRL|(Ours) GEMINI-Semi|√|91.2<sub>±3.6</sub>|0.97<sub>±0.56</sub>|87.3<sub>±1.0</sub>|0.35<sub>±0.03</sub>|87.7<sub>±5.2</sub>|7.14<sub>±3.63</sub>|88.7<sub>±3.3</sub>{{< /table-caption >}}
> 🔼 표 II는 본 논문에서 제안하는 GEMINI-Semi 방법이 다양한 의료 영상(CT, MR, X-ray)의 Few-shot Semi-supervised 세분화 작업에서 우수한 성능을 보임을 보여주는 정량적 평가 결과를 나타냅니다.  19가지 다른 방법들과 GVSL과의 비교를 통해 GEMINI-Semi의 성능 우위를 확인할 수 있습니다.  'unable'은 결과가 너무 좋지 않아 AVD(Average Hausdorff Distance)를 계산할 수 없음을 의미하며, '-'는 설정이 불가능함을 의미합니다. 'HP'는 해당 방법이 homeomorphism prior를 사용했는지 여부를 나타냅니다. T1, T2, T3은 각각 과제 1, 2, 3을 나타내며, 빨간색과 파란색 값은 각 열에서 가장 높은 값과 두 번째로 높은 값을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> TABLE II: The quantitative evaluation demonstrates our powerful representation ability in FS-Semi tasks. Our GEMINI-Semi achieves the best performance on CT, MR, and X-ray images compared with 19 popular methods and the GVSL. The “unable” means that the extremely poor results make the AVD unable to be calculated. The “-” means that the setting is unable to be implemented. The “HP” means these methods have or do not have homeomorphism prior. “T1”, “T2”, “T3” are the task 1, task 2, task 3. The red and blue values are the highest and the second-highest values in the columns.
> </details>

{{< table-caption >}}
| Type | Pre-training | T1: SCR<sub>25</sub><br><em>Inner-scene</em> |  | T2: KiPA22<br><em>Inter-scene</em> |  | T3: CANDI<br><em>Inter-scene</em> |  | AVG | 
|---|---|---|---|---|---|---|---|---|
| DSC<sub>±std</sub>↑ | Scratch (2D U-Net) | 81.8<sub>±8.2</sub> | 9.00<sub>±6.37</sub> | 74.1<sub>±12.3</sub> | 3.59<sub>±1.97</sub> | 65.0<sub>±4.4</sub> | 1.27<sub>±0.21</sub> | 73.6<sub>±8.3</sub> |
| AVD<sub>±std</sub>↓ |  | 92.0<sub>±3.1</sub> | 4.09<sub>±1.64</sub> | 72.6<sub>±15.5</sub> | 4.78<sub>±4.86</sub> | 71.1<sub>±19.8</sub> | 1.35<sub>±2.07</sub> | 78.6<sub>±12.8</sub> |
|  | ImageNet [88] | 83.9<sub>±7.8</sub> | 11.17<sub>±7.81</sub> | 60.3<sub>±17.7</sub> | 7.55<sub>±5.18</sub> | 67.7<sub>±2.1</sub> | 1.21<sub>±0.08</sub> | 70.6<sub>±9.2</sub> |
|  | Denoising [89] | 85.1<sub>±6.6</sub> | 16.59<sub>±10.74</sub> | 64.4<sub>±16.4</sub> | 5.79<sub>±4.13</sub> | 66.2<sub>±2.3</sub> | 1.26<sub>±0.08</sub> | 71.9<sub>±8.4</sub> |
|  | In-painting [69] | 86.1<sub>±4.6</sub> | 6.22<sub>±2.27</sub> | 66.6<sub>±16.3</sub> | 5.86<sub>±3.14</sub> | 88.1<sub>±3.1</sub> | 0.32<sub>±0.10</sub> | 80.3<sub>±8.0</sub> |
|  | Models Genesis [68] | 80.5<sub>±7.7</sub> | 20.62<sub>±12.55</sub> | 69.7<sub>±15.3</sub> | 6.45<sub>±4.33</sub> | 78.3<sub>±2.6</sub> | 0.75<sub>±0.09</sub> | 76.2<sub>±8.5</sub> |
|  | Rotation [90] | 87.2<sub>±5.1</sub> | 11.87<sub>±8.10</sub> | 72.6<sub>±13.3</sub> | 4.10<sub>±3.25</sub> | 76.7<sub>±2.1</sub> | 0.82<sub>±0.06</sub> | 78.8<sub>±6.8</sub> |
|  | SimSiam [50] | 89.4<sub>±4.9</sub> | 8.48<sub>±4.37</sub> | 74.1<sub>±12.6</sub> | 3.87<sub>±2.93</sub> | 70.5<sub>±2.1</sub> | 1.08<sub>±0.07</sub> | 78.0<sub>±6.5</sub> |
|  | BYOL [24] | 89.0<sub>±4.0</sub> | 11.28<sub>±6.53</sub> | 74.4<sub>±11.3</sub> | 3.68<sub>±2.65</sub> | 79.0<sub>±2.6</sub> | 1.02<sub>±0.40</sub> | 80.8<sub>±6.0</sub> |
|  | SimCLR [22] | 84.3<sub>±6.5</sub> | 11.06<sub>±5.19</sub> | 69.6<sub>±14.4</sub> | 6.28<sub>±4.70</sub> | 82.9<sub>±3.6</sub> | 0.52<sub>±0.12</sub> | 78.9<sub>±8.2</sub> |
|  | MoCov2 [23] | 84.0<sub>±8.1</sub> | 19.71<sub>±13.15</sub> | 72.7<sub>±15.1</sub> | 4.91<sub>±3.50</sub> | 60.0<sub>±2.2</sub> | 1.52<sub>±0.07</sub> | 72.2<sub>±8.5</sub> |
|  | DeepCluster [51] | 85.2<sub>±5.1</sub> | 7.15<sub>±3.05</sub> | 62.8<sub>±15.6</sub> | 7.23<sub>±4.73</sub> | 86.1<sub>±3.4</sub> | 0.40<sub>±0.12</sub> | 78.0<sub>±8.0</sub> |
|  | VADeR [2] | 85.0<sub>±6.3</sub> | 11.74<sub>±7.02</sub> | 70.8<sub>±14.8</sub> | 5.48<sub>±3.95</sub> | 76.8<sub>±2.9</sub> | 1.22<sub>±0.68</sub> | 77.5<sub>±8.0</sub> |
|  | DenseCL [3] | 85.2<sub>±5.1</sub> | 9.63<sub>±7.64</sub> | 70.8<sub>±14.4</sub> | 4.92<sub>±3.26</sub> | 74.9<sub>±2.5</sub> | 0.89<sub>±0.08</sub> | 77.0<sub>±7.3</sub> |
|  | SetSim [4] | 90.5<sub>±3.5</sub> | 5.44<sub>±2.87</sub> | 77.2<sub>±12.2</sub> | 3.87<sub>±3.34</sub> | 83.3<sub>±2.4</sub> | 0.74<sub>±0.64</sub> | 83.7<sub>±6.0</sub> |
|  | DSC-PM [1] | 91.5<sub>±3.3</sub> | 9.83<sub>±5.34</sub> | 73.6<sub>±12.9</sub> | 4.00<sub>±3.33</sub> | 63.9<sub>±2.0</sub> | 1.35<sub>±0.06</sub> | 76.3<sub>±6.1</sub> |
|  | PixPro [5] | 87.3<sub>±5.8</sub> | 9.35<sub>±4.68</sub> | 76.5<sub>±11.9</sub> | 4.33<sub>±2.94</sub> | 82.8<sub>±2.6</sub> | 0.56<sub>±0.09</sub> | 82.2<sub>±6.8</sub> |
|  | GLCL [49] | 89.7<sub>±3.7</sub> | 10.52<sub>±7.23</sub> | 78.9<sub>±11.2</sub> | 2.95<sub>±1.55</sub> | 89.7<sub>±2.6</sub> | 0.27<sub>±0.08</sub> | 86.1<sub>±5.8</sub> |
|  | GVSL-MIP (CVPR)[33] | **92.1<sub>±2.8</sub>** | 5.38<sub>±2.65</sub> | **79.1<sub>±11.1</sub>** | **3.22<sub>±2.24</sub>** | **89.8<sub>±2.6</sub>** | **0.27<sub>±0.08</sub>** | **87.0<sub>±5.5</sub>** |
| (Ours) | **GEMINI-MIP** |  |  |  |  |  |  |  |{{< /table-caption >}}
> 🔼 표 III은 자기 지도 학습 의료 이미지 사전 학습(SS-MIP) 작업에서 GEMINI-MIP의 우수한 전이 학습 성능을 보여줍니다. 세 가지 하위 작업에서 18가지 방법과 비교하여 GEMINI-MIP가 최고 성능을 달성했습니다. T1, T2, T3은 각각 작업 1, 작업 2, 작업 3을 나타내고 AVG는 각 행의 평균값을 나타냅니다. 회색 배경의 셀은 내부 장면(동일한 이미지 범주) 전이를 나타내고, 다른 색상의 셀은 장면 간(다른 이미지 범주) 전이를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> TABLE III: The fine-tuning evaluations demonstrate our great transferring ability on SS-MIP tasks. Our GEMINI-MIP achieves the best performance compared with 18 methods on 3 downstream tasks. “T1”, “T2”, and “T3” are the task 1, task 2, and task 3. “AVG” is the average value of the row. The cells with gray backgrounds are the inner-scene (same image category) transferring and the others are the inter-scene (different image category) transferring.
> </details>

{{< table-caption >}}
| Type | No \mathcal{L}_{pos} | Half \mathcal{L}_{pos} | Full \mathcal{L}_{pos} |
|---|---|---|---| 
| DSC_{\pm std} \uparrow | 90.3_{\pm3.6} | 90.5_{\pm3.5} | 91.2_{\pm3.6} |{{< /table-caption >}}
> 🔼 표 IV는 3D 심장 구조(T1)에 대한 양성 쌍 학습 손실 함수(ℒp⁢o⁢ssubscriptℒ𝑝𝑜𝑠 mathcal{L}_{pos})의 설정에 따른 영향을 보여줍니다. 'No ℒp⁢o⁢ssubscriptℒ𝑝𝑜𝑠 mathcal{L}_{pos}'는 양성 쌍 학습 없이 학습한 경우, 'Half ℒp⁢o⁢ssubscriptℒ𝑝𝑜𝑠 mathcal{L}_{pos}'는 전체 반복 횟수의 절반까지 양성 쌍 학습을 진행하고 그 이후부터 양성 쌍 학습을 적용한 경우, 'Full ℒp⁢o⁢ssubscriptℒ𝑝𝑜𝑠 mathcal{L}_{pos}'는 전체 학습 과정 동안 양성 쌍 학습을 적용한 경우를 각각 의미합니다.
> <details>
> <summary>read the caption</summary>
> TABLE IV: The learning for positive pairs ℒp⁢o⁢ssubscriptℒ𝑝𝑜𝑠\mathcal{L}_{pos}caligraphic_L start_POSTSUBSCRIPT italic_p italic_o italic_s end_POSTSUBSCRIPT in different setting on the “T1: 3D Cardiac structures”. The “No ℒp⁢o⁢ssubscriptℒ𝑝𝑜𝑠\mathcal{L}_{pos}caligraphic_L start_POSTSUBSCRIPT italic_p italic_o italic_s end_POSTSUBSCRIPT” means the training without positive pairs. The “Half ℒp⁢o⁢ssubscriptℒ𝑝𝑜𝑠\mathcal{L}_{pos}caligraphic_L start_POSTSUBSCRIPT italic_p italic_o italic_s end_POSTSUBSCRIPT” means when training to half of the total iteration amount, the learning of positive pairs is added. The “Full ℒp⁢o⁢ssubscriptℒ𝑝𝑜𝑠\mathcal{L}_{pos}caligraphic_L start_POSTSUBSCRIPT italic_p italic_o italic_s end_POSTSUBSCRIPT” means the whole training process with positive pairs.
> </details>

{{< table-caption >}}
| Type | Segmentation | Deformation | Deformation | 
|---|---|---|---| 
| **Type** | **Segmentation** | **Deformation** | **Deformation** | 
|  | DSC<sub>±std</sub>↑ | DSC<sub>±std</sub>↑ | |J<sub>ϕ</sub>|≤0 %↓ | 
| Only ℒ<sub>Seg</sub> | 84.3<sub>±9.6</sub> | - | - | 
| No deformation | - | 62.1<sub>±8.7</sub> | - | 
| GVS only | 89.3<sub>±4.1</sub> | 51.3<sub>±10.3</sub> | 40.8<sub>±1.2</sub> | 
| GSS only | **90.0<sub>±3.4</sub>** | **84.1<sub>±13.0</sub>** | **10.2<sub>±2.2</sub>** |{{< /table-caption >}}
> 🔼 표 V는 본 논문에서 제안하는 GEMINI-Semi 방법의 성능을 보여줍니다.  특히 기하학적 시맨틱 유사성(GSS)만 사용한 경우와 기하학적 시각 유사성(GVS)만 사용한 경우의 성능을 비교하여 GSS의 장점을 보여줍니다.  3D 심장 구조 분할 작업(T1)에서 GSS를 사용한 GEMINI-Semi는 GVS만 사용한 경우보다 분할 및 변형 정확도가 모두 높음을 보여줍니다.  이는 GSS가 시맨틱 정보를 활용하여 더욱 정확한 대응 관계를 학습하기 때문입니다.  이 표는 GEMINI-Semi의 성능과 GSS의 효과를 정량적으로 보여주는 중요한 결과를 제시합니다.
> <details>
> <summary>read the caption</summary>
> TABLE V: The comparison between our GEMINI-Semi with only GSS and with only GVS on the “T1: 3D Cardiac structures” demonstrates the advantages of our geometric semantic similarity.
> </details>

{{< table-caption >}}
| Type | Pre-training | T2: KiPA22 _Inter-scene_ DSC<sub>±std</sub>↑ | T2: KiPA22 _Inter-scene_ AVD<sub>±std</sub>↓ | T3: CANDI _Inner-scene_ DSC<sub>±std</sub>↑ | T3: CANDI _Inner-scene_ AVD<sub>±std</sub>↓ | AVG DSC<sub>±std</sub>↑ |
|---|---|---|---|---|---|---|
|  | Scratch (3D U-Net) | 72.4<sub>±16.3</sub> | 6.11<sub>±5.91</sub> | 84.0<sub>±3.2</sub> | 0.52<sub>±0.14</sub> | 78.2<sub>±9.8</sub> |
| Sup | Med3D [95] | 81.7<sub>±12.0</sub> | 2.61<sub>±2.77</sub> | 72.7<sub>±19.0</sub> | 1.57<sub>±2.56</sub> | 77.2<sub>±15.5</sub> |
| GRL | Denosing [89] | 70.0<sub>±15.4</sub> | 7.60<sub>±5.03</sub> | 83.7<sub>±3.3</sub> | 1.71<sub>±0.20</sub> | 76.9<sub>±9.4</sub> |
|  | In-painting [69] | 69.7<sub>±17.1</sub> | 7.57<sub>±5.93</sub> | 88.5<sub>±3.1</sub> | 0.32<sub>±0.11</sub> | 79.1<sub>±10.1</sub> |
|  | Models Genesis [68] | 75.8<sub>±13.7</sub> | 4.64<sub>±4.49</sub> | 88.7<sub>±3.1</sub> | 0.31<sub>±0.10</sub> | 82.3<sub>±8.4</sub> |
|  | Rotation [90] | 77.4<sub>±14.3</sub> | 4.82<sub>±6.29</sub> | 89.4<sub>±2.6</sub> | 0.28<sub>±0.08</sub> | 83.4<sub>±8.5</sub> |
| CRL | SimSiam [50] | 83.8<sub>±11.9</sub> | 3.69<sub>±7.47</sub> | 87.3<sub>±3.1</sub> | 0.36<sub>±0.10</sub> | 85.6<sub>±7.5</sub> |
|  | BYOL [24] | 83.6<sub>±11.2</sub> | 2.78<sub>±5.42</sub> | 89.7<sub>±2.4</sub> | 0.27<sub>±0.08</sub> | 86.7<sub>±6.8</sub> |
|  | SimCLR [22] | 78.9<sub>±13.9</sub> | 4.49<sub>±5.15</sub> | 89.2<sub>±3.0</sub> | 0.30<sub>±0.14</sub> | 84.1<sub>±8.5</sub> |
|  | MoCov2 [23] | 78.0<sub>±15.3</sub> | 4.42<sub>±5.67</sub> | 89.7<sub>±2.4</sub> | 0.28<sub>±0.11</sub> | 83.9<sub>±8.9</sub> |
|  | DeepCluster [51] | 79.7<sub>±13.7</sub> | 4.28<sub>±5.76</sub> | 89.8<sub>±2.4</sub> | 0.27<sub>±0.08</sub> | 84.8<sub>±8.1</sub> |
| DCRL | VADeR [2] | 72.1<sub>±13.8</sub> | 6.56<sub>±5.89</sub> | 87.4<sub>±3.6</sub> | 0.35<sub>±0.11</sub> | 79.8<sub>±8.7</sub> |
|  | DenseCL [3] | 74.0<sub>±15.8</sub> | 6.42<sub>±8.21</sub> | 87.7<sub>±3.8</sub> | 0.34<sub>±0.13</sub> | 80.9<sub>±9.8</sub> |
|  | SetSim [4] | 73.5<sub>±15.9</sub> | 6.34<sub>±6.68</sub> | 88.4<sub>±3.1</sub> | 0.32<sub>±0.10</sub> | 81.0<sub>±9.5</sub> |
|  | DSC-PM [1] | 79.0<sub>±14.6</sub> | 4.90<sub>±6.05</sub> | 88.5<sub>±3.4</sub> | 0.32<sub>±0.13</sub> | 83.8<sub>±9.0</sub> |
|  | PixPro [5] | 80.0<sub>±14.4</sub> | 4.60<sub>±6.25</sub> | 89.9<sub>±2.4</sub> | 0.27<sub>±0.07</sub> | 85.0<sub>±8.4</sub> |
|  | GLCL [49] | 70.7<sub>±16.9</sub> | 7.33<sub>±7.05</sub> | 87.4<sub>±3.2</sub> | 0.34<sub>±0.09</sub> | 79.1<sub>±10.1</sub> |
| **DCRL** | **GVSL-MIP (CVPR)[33]** | **84.3<sub>±10.3</sub>** | 2.85<sub>±5.12</sub> | 89.1<sub>±2.8</sub> | 0.31<sub>±0.11</sub> | **86.7<sub>±6.6</sub>** |
| **(Ours)** | **GEMINI-MIP** | **85.0<sub>±10.2</sub>** | **2.55<sub>±5.71</sub>** | **90.0<sub>±2.4</sub>** | **0.26<sub>±0.07</sub>** | **87.5<sub>±6.3</sub>** |{{< /table-caption >}}
> 🔼 표 VI는 PPMI 데이터셋으로 사전 훈련된 SS-MIP 작업에서 GEMINI-MIP의 우수한 전이 학습 성능을 보여줍니다. 두 가지 하위 작업(T2: KiPA22, T3: CANDI)에서 GEMINI-MIP는 18가지 방법 중 가장 우수한 성능을 달성했습니다. 표는 각 방법에 대한 DSC 및 AVD 점수를 보여주며, GEMINI-MIP가 다른 방법에 비해 상당한 성능 향상을 보였음을 강조합니다.
> <details>
> <summary>read the caption</summary>
> TABLE VI: The fine-tuning evaluations demonstrate our great transferring ability on SS-MIP tasks which pre-trained on PPMI dataset. Our GEMINI-MIP achieves the best performance compared with 18 methods on two downstream tasks.
> </details>

{{< table-caption >}}
| Index | Method | Chest X-ray | Brain T1 MR | Gap |
|---|---|---|---|---|
| <math>i</math> | 2D U-Net | 3D U-Net | <math>G^{i}</math> |
| _Inter-scene_ | _Inner-scene_ |  |  |  |
| 0 | Scratch | 65.0<sub>±4.4</sub> | 84.0<sub>±3.2</sub> | 1 |
| 1 | BYOL | 70.5<sub>±2.1</sub> | 89.7<sub>±2.4</sub> | 1.01 |
| 2 | DeepCluster | 60.0<sub>±2.2</sub> | 89.8<sub>±2.4</sub> | 1.57 |
| 3 | Model Genesis | 88.1<sub>±3.1</sub> | 88.7<sub>±3.1</sub> | 0.03 |
| 4 | DenseCL | 76.8<sub>±2.9</sub> | 87.7<sub>±3.8</sub> | 0.57 |
| **5** | **Our GEMINI-MIP** | **89.8<sub>±2.6</sub>** | **90.0<sub>±2.4</sub>** | **0.01** |{{< /table-caption >}}
> 🔼 표 VII은 두 가지 상황, 즉 '흉부 X선 이미지로 사전 훈련하고 뇌 T1 MR 이미지로 미세 조정'(장면 간)과 '뇌 T1 MR 이미지로 사전 훈련하고 뇌 T1 MR 이미지로 미세 조정'(장면 내)의 차이를 계량화하는 간격 계수 *G<sup>i</sup>*를 보여줍니다.  간격 계수는 사전 훈련된 모델의 장면 내 전이 학습 능력과 장면 간 전이 학습 능력의 차이를 나타냅니다.  값이 1보다 크면 장면 내 전이 학습 능력이 더 크고, 1보다 작으면 장면 간 전이 학습 능력이 더 크다는 것을 의미합니다.
> <details>
> <summary>read the caption</summary>
> TABLE VII: The gap coefficient Gisuperscript𝐺𝑖G^{i}italic_G start_POSTSUPERSCRIPT italic_i end_POSTSUPERSCRIPT quantifies the gap between “pre-trained on chest X-ray images & fine-tuning on brain T1 MR images” (inter-scene) and “pre-trained on brain T1 MR images & fine-tuning on brain T1 MR images” (inner-scene).
> </details>

{{< table-caption >}}
| Type | Method | T1: 3D cardiac structures DSC<sub>±std</sub>↑ | T1: 3D cardiac structures AVD<sub>±std</sub>↓ | T2: 3D brain tissues DSC<sub>±std</sub>↑ | T2: 3D brain tissues AVD<sub>±std</sub>↓ | T3: 2D chest structures DSC<sub>±std</sub>↑ | T3: 2D chest structures AVD<sub>±std</sub>↓ | AVG DSC<sub>±std</sub>↑ |
|---|---|---|---|---|---|---|---|---|
| **Five** | U-Net [80] | 84.3<sub>±9.6</sub> | 2.43<sub>±2.14</sub> | 69.5<sub>±8.8</sub> | 1.59<sub>±0.84</sub> | 83.4<sub>±6.9</sub> | 10.34<sub>±4.80</sub> | 79.1<sub>±8.4</sub> |
| **(Lower)** | TransUNet [99] | 74.5<sub>±8.3</sub> | 4.41<sub>±1.39</sub> | 67.4<sub>±5.4</sub> | 2.02<sub>±0.46</sub> | 76.5<sub>±8.2</sub> | 16.59<sub>±6.53</sub> | 72.8<sub>±7.3</sub> |
|  | SwinUNet [100] | 40.8<sub>±8.0</sub> | 11.59<sub>±1.32</sub> | 67.8<sub>±5.3</sub> | 4.04<sub>±0.39</sub> | 63.9<sub>±11.5</sub> | 14.26<sub>±8.91</sub> | 57.5<sub>±8.3</sub> |
| **Full** | U-Net [80] | - | - | 88.7<sub>±1.2</sub> | 0.31<sub>±0.04</sub> | 96.1<sub>±1.4</sub> | 2.28<sub>±1.00</sub> | - |
| **(Upper)** | TransUNet [99] | - | - | 85.7<sub>±1.2</sub> | 0.43<sub>±0.05</sub> | 95.2<sub>±2.1</sub> | 2.78<sub>±1.35</sub> | - |
|  | SwinUNet [100] | - | - | 82.8<sub>±2.7</sub> | 0.54<sub>±0.15</sub> | 95.3<sub>±1.2</sub> | 2.17<sub>±0.65</sub> | - |
| **Semi** | **GEMINI+U-Net** | 91.2<sub>±3.6</sub> | 0.97<sub>±0.56</sub> | 87.3<sub>±1.0</sub> | 0.35<sub>±0.03</sub> | 87.7<sub>±5.2</sub> | 7.14<sub>±3.63</sub> | 88.7<sub>±3.3</sub> |
| **(Ours)** | **GEMINI+TransUNet** | 90.8<sub>±3.4</sub> | 0.94<sub>±0.51</sub> | 84.4<sub>±1.3</sub> | 0.45<sub>±0.05</sub> | 88.4<sub>±5.7</sub> | 8.63<sub>±4.68</sub> | 87.9<sub>±3.5</sub> |
|  | **GEMINI+SwinUNet** | 88.6<sub>±4.2</sub> | 1.28<sub>±0.64</sub> | 79.9<sub>±5.0</sub> | 0.62<sub>±0.20</sub> | 86.2<sub>±7.8</sub> | 6.34<sub>±4.34</sub> | 84.9<sub>±5.7</sub> |{{< /table-caption >}}
> 🔼 표 VIII은 제안된 GEMINI의 다양한 아키텍처 적합성을 보여줍니다. U-Net, TransUNet, SwinUNet 세 가지 다른 아키텍처에서의 Few-Shot Semi-supervised(FS-Semi) 세그먼테이션 작업에 대한 평가 결과를 보여줍니다.  각 아키텍처는 제한된 수의 레이블을 사용하여 평가되며, GEMINI가 다양한 아키텍처에서 효과적으로 작동함을 보여줍니다. 표에는 각 아키텍처와 데이터 설정(Five, Full, Semi)에 따른 Dice Similarity Coefficient(DSC)와 Average Hausdorff Distance(AVD) 값이 포함되어 있습니다. '-'는 해당 설정에서 구현할 수 없음을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> TABLE VIII: The FS-Semi evaluations on U-Net [80], TransUNet [99], and SwinUNet [100] demonstrate the cross-architecture compatibility of our GEMINI. The “-” means that the setting is unable to be implemented.
> </details>

{{< table-caption >}}
| Type | Method | Pre-training FLOPs | Downstream FLOPs | T1: SCR<sub>25</sub> DSC<sub>±std</sub> |
|---|---|---|---|---|
| 1×Encoder | Rotation [90] | 5.99G | 20.15G | 80.5<sub>±7.7</sub> |
| 2×Encoder | BYOL [24] | 11.98G | 20.15G | 89.4<sub>±4.9</sub> |
| 1×Encoder-decoder | Model Genesis [68] | 19.74G | 20.15G | 86.1<sub>±4.6</sub> |
| 2×Encoder-decoder | VADeR [2] | 39.67G | 20.15G | 85.2<sub>±5.1</sub> |
| 2×Encoder-decoder | **Our GEMINI** | **52.59G** | 20.15G | **92.1<sub>±2.8</sub>** |{{< /table-caption >}}
> 🔼 표 IX는 GEMINI 모델의 전반적인 계산 비용을 보여줍니다. GEMINI는 추가적인 변형 네트워크로 인해 사전 훈련 단계에서 상대적으로 높은 계산 비용이 들지만, 다른 방법들과 마찬가지로 하류 작업의 미세 조정 단계에서는 동일한 계산 비용이 들며 훨씬 더 높은 성능을 달성합니다.  사전 훈련 단계에서 높은 계산 비용은 향상된 성능을 위한 투자로 볼 수 있습니다.
> <details>
> <summary>read the caption</summary>
> TABLE IX: Owing to the additional deformer networks, our GEMINI has relatively higher computing costs in the pre-training stage, but it has same computing costs in the fine-tuning for downstream tasks as other methods and achieves much higher performance.
> </details>

{{< table-caption >}}
| Evaluations | T1: 3D cardiac structures | T2: 3D brain tissues | T3: 2D chest structures | AVG |
|---|---|---|---|---|
| **a) Reliability across samples** |  |  |  |  |
|  | DSC ↑ | std ↓ | DSC ↑ | std ↓ | DSC ↑ | std ↓ | DSC ↑ | std ↓ |
|  | 91.2 | 3.6 | 87.3 | 1.0 | 87.7 | 5.2 | 88.7 | 3.3 |
| **b) Reliability across training** |  |  |  |  |
|  | *Cor* ↑ | *p* ↓ | *Cor* ↑ | *p* ↓ | *Cor* ↑ | *p* ↓ | *Cor* ↑ | *p* ↓ |
|  | 0.989 | &lt;0.001 | 0.999 | &lt;0.001 | 0.968 | &lt;0.001 | 0.985 | &lt;0.001 |{{< /table-caption >}}
> 🔼 표 10은 논문의 실험 1에서 GEMINI의 신뢰도를 평가한 결과입니다.  표에는 세 가지 과업(3D 심장 구조, 3D 뇌 조직, 2D 흉부 구조)에 대한 GEMINI 모델의 성능 평가 지표인 DSC(Dice Similarity Coefficient) 값과 표준 편차(std), 그리고 재현성을 평가하기 위한 피어슨 상관 계수(Cor)와 p-값이 제시되어 있습니다.  샘플 간의 신뢰도와 훈련 간의 신뢰도를 모두 평가하여 GEMINI 모델의 견고성과 재현성을 보여줍니다.  낮은 표준 편차와 높은 피어슨 상관 계수는 GEMINI 모델이 안정적이고 재현 가능한 결과를 제공함을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> TABLE X: The evaluation of our GEMINI’s reliability on the tasks in Experiment 1. The Cor is the Pearson correlation coefficient [101], and the p is the p-value.
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