---
title: "IDOL: Instant Photorealistic 3D Human Creation from a Single Image"
summary: "단일 이미지에서 초고속, 고품질, 애니메이션 가능한 3D 아바타를 생성하는 IDOL 모델 제시!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "3D Vision", "🏢 Tencent",]
showSummary: true
date: 2024-12-19
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.14963 {{< /keyword >}}
{{< keyword icon="writer" >}} Yiyu Zhuang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-23 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.14963" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.14963" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/idol-instant-photorealistic-3d-human-creation" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

3D 아바타 생성은 가상현실, 게임 등 다양한 분야에서 중요하지만, 기존 기술은 **단일 이미지로부터 고품질 아바타 생성에 어려움**을 겪었습니다. 특히, **고품질 데이터 부족**, **느린 처리 속도**, **일반화 성능 저하** 등이 주요 문제였습니다.  또한, 생성된 아바타의 **애니메이션 및 편집 기능 제약**도 큰 걸림돌이었습니다.

본 논문에서는 이러한 문제를 해결하기 위해 **10만 개 이상의 다양한 인물 데이터를 포함한 대규모 데이터셋 HuGe100K**를 제작하고, 이를 기반으로 **새로운 딥러닝 모델 IDOL**을 개발했습니다. IDOL은 **단일 이미지 입력으로 1초 이내에 고품질 3D 아바타를 생성**하며, **자연스러운 애니메이션 및 편집 기능**을 제공합니다. **빠른 속도와 높은 정확도, 그리고 우수한 일반화 성능**을 통해 기존 기술의 한계를 극복하고 3D 아바타 생성 기술의 새로운 가능성을 열었습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 단일 이미지를 이용한 실시간 고품질 3D 아바타 생성 기술 개발 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 대규모 고해상도 데이터셋 HuGe100K 공개 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 기존 방법 대비 향상된 속도 및 정확도, 다양한 애플리케이션 지원 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **단일 이미지로부터 실시간 고품질 3D 아바타 생성**이라는 어려운 문제에 대한 혁신적인 해결책을 제시합니다. **대규모 고해상도 데이터셋 HuGe100K**를 활용한 **새로운 피드포워드 변환기 모델 IDOL**을 통해, 기존 방법의 한계를 뛰어넘는 속도와 정확도를 달성하였습니다. 이는 **3D 아바타 생성 및 편집 기술 발전**에 크게 기여하며, **가상현실, 게임, 3D 콘텐츠 제작 분야**의 혁신을 가져올 수 있습니다. 또한, 본 연구는 **데이터셋 생성 파이프라인**, **모델 설계 및 최적화**, **다양한 응용 분야**에 대한 심도있는 연구를 제공하여, 관련 분야 연구자들에게 귀중한 자료가 될 것입니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.14963/x2.png)

> 🔼 그림 1은 본 논문에서 제시하는 IDOL 모델과 그 성능을 보여주는 그림입니다. (a)는 IDOL이라는 단일 이미지 기반의 빠르고 정확하며 일반화 성능이 뛰어난 3D 인체 재구성 프레임워크임을 보여줍니다. (b)는 10만 명의 다양한 자세를 포함하는 대규모 생성 인체 다중 뷰 데이터 세트를 활용하여 다양한 인체 형태, 도메인 간 데이터, 심각한 시점 및 폐색 등을 처리하는 데 탁월한 일반화 성능을 보여줍니다. (c)는 균일한 구조화된 표현 방식을 통해 아바타를 직접 애니메이션으로 만들고 쉽게 편집할 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  This work introduces (a) IDOL, a feed-forward, single-image human reconstruction framework that is fast, high-fidelity, and generalizable; (b) Utilizing the proposed Large Generated Human Multi-View Dataset consisting of 100⁢K100𝐾100K100 italic_K multi-view subjects, our method exhibits exceptional generalizability in handling diverse human shapes, cross-domain data, severe viewpoints, and occlusions; (c) With a uniform structured representation, the avatars can be directly animatable and easily editable.
> </details>





{{< table-caption >}}
| Type | Dataset | #Frames | IDs | SMPL(-X) |
|---|---|---|---|---|
| 3D Scans | THuman [74] | - | 200 | ✔ |
|  | THuman2.1 [64] | - | 2500 | ✔ |
|  | 2K2K [14] | - | 2050 | ✘ |
|  | X-Avatar [52] | 35.5K | 20 | ✔ |
| Multi-view Images | ZJU-MoCap [46] | 180K | 10 | ✔ |
|  | Neural Actor [37] | 250K | 8 | ✔ |
|  | HUMBI [66] | 26M | 772 | ✔ |
|  | AIST++ [34] | 10.1M | 30 | ✔ |
|  | HuMMan [4] | 60M | 1000 | ✔ |
|  | GeneBody [8] | 2.95M | 50 | ✔ |
|  | ActorsHQ [27] | 40K | 8 | ✘ |
|  | DNA-Rendering [9] | 67.5M | 500 | ✔ |
|  | MVHumanNet [59] | **645.1M** | 4500 | ✔ |
| Ours | **HuGe100K** | > 2.4M | **100K** | ✔ |{{< /table-caption >}}

> 🔼 표 1은 기존의 다양한 인체 데이터셋과 본 논문에서 제시하는 HuGe100K 데이터셋을 비교 분석한 표입니다. HuGe100K는 10만 명의 다양한 사람들을 포함하는 대규모 합성 다중 뷰 인체 데이터셋으로, 고품질의 이미지 데이터를 제공합니다. 표에는 각 데이터셋의 프레임 수, ID 수, SMPL(-X) 모델 사용 여부 등의 정보가 포함되어 HuGe100K의 우수성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparisons of related datasets. HuGe100K is a large-scale generated multi-view human dataset with 100⁢K100𝐾100K100 italic_K diverse high-fidelity humans.
> </details>





### In-depth insights


#### HuGe100K Dataset
본 논문에서 제시된 HuGe100K 데이터셋은 **단일 이미지로부터 사실적인 3D 인간 아바타를 생성하는 모델을 훈련하기 위한 대규모 다중 뷰 데이터셋**입니다. 기존의 데이터셋들이 규모나 다양성 측면에서 제한적이었던 점을 고려하여, **합성 이미지와 실제 이미지를 결합**하여 100,000명 이상의 다양한 인물을 포함하고 있습니다. 각 인물에 대해 24개의 다중 뷰 이미지가 제공되며, **포즈, 체형, 의상, 배경 등 다양한 속성을 고려**하여 생성되었습니다. 이는 모델의 일반화 성능 향상에 크게 기여할 것으로 예상되며, **3D 인간 아바타 생성 분야의 발전**에 중요한 역할을 할 것으로 기대됩니다.  특히, **일관성 있는 고품질의 다중 뷰 데이터**를 제공함으로써, 기존의 단일 이미지 기반 3D 인간 아바타 생성 모델이 가지고 있던 한계를 극복하는데 도움을 줄 수 있을 것으로 보입니다.

#### IDOL Architecture
본 논문에서 제시된 IDOL 모델의 아키텍처는 **단일 이미지로부터 사실적인 3D 아바타를 생성하기 위한 효율적인 구조**를 보여줍니다.  **고해상도 이미지 인코더**를 통해 이미지의 세밀한 특징을 추출하고, **UV-정렬 변환기**를 이용하여 불규칙적인 이미지를 규칙적인 UV 맵으로 정렬합니다. 이후 **UV 디코더**는 3D 가우시안 표면의 속성 맵을 예측하여, SMPL-X 모델과 결합하여 3D 아바타를 생성합니다.  **가우시안 표면 기반의 표현**은 효율적인 애니메이션과 편집을 가능하게 하며, **전체 과정이 미분 가능**하여 최적화 과정을 용이하게 합니다.  **다양한 관점과 자세를 가진 대규모 데이터셋**을 활용한 학습을 통해 IDOL은 **일반화 성능**을 크게 향상시켰습니다.  **빠른 처리 속도** 또한 IDOL의 주요 특징이며, 단일 GPU에서 1초 이내에 3D 아바타 생성이 가능합니다.  **모듈화된 구조**는 다양한 응용 분야에 적용될 수 있는 확장성을 제공합니다.

#### Ablation Studies
본 논문의 ablation study는 **모델 성능에 기여하는 각 구성 요소의 중요성을 정량적으로 평가**하기 위해 설계되었습니다.  여러 구성 요소를 제거하거나 변경하여 모델 성능에 미치는 영향을 측정함으로써, 각 요소의 상대적 중요도를 파악하고, 모델의 강점과 약점을 명확히 밝히는 데 도움이 됩니다.  특히, **고해상도 이미지 인코더, 대규모 데이터셋, 그리고 제안된 모델 아키텍처의 기여도를 개별적으로 분석**하는 실험 결과는, 각 요소가 최종 성능에 얼마나 중요한 역할을 하는지 보여주는 중요한 지표가 됩니다.  이러한 분석을 통해, 연구진은 **향후 모델 개선을 위한 방향을 제시**하고, 제한된 자원 하에서도 효율적으로 모델을 개선할 수 있는 전략을 세울 수 있습니다.  또한, ablation study는 모델의 **일반화 성능 및 견고성**을 평가하는 데에도 활용될 수 있습니다. 다양한 조건에서 모델 성능을 비교 분석함으로써, 모델의 범용성 및 환경 변화에 대한 적응력을 측정할 수 있습니다.  **결론적으로, 본 논문의 ablation study는 모델의 성능을 심도 있게 분석하고 향후 연구 방향을 제시하는 중요한 부분**이며, 연구의 신뢰성과 설득력을 높이는 데 크게 기여할 것입니다.

#### 3D Reconstruction
본 논문에서 3D 재구성은 단일 이미지로부터 사실적인 3D 인간 아바타를 생성하는 핵심 과정입니다. **단일 이미지만으로 3D 모델을 만드는 과정은 매우 어렵기 때문에**, 높은 충실도와 일반화 성능을 달성하기 위해 데이터셋, 모델, 표현 방식에 대한 혁신적인 접근법이 필요합니다.  논문에서는 **대규모 다중 뷰 데이터셋 HuGe100K**를 제시하여 다양한 인간의 모습, 자세, 의상을 포괄적으로 학습할 수 있게 하였고, 이를 바탕으로 **빠르고 효율적인 피드포워드 변환기 모델 IDOL**을 개발하여 단일 이미지에서 3D 가우시안 표현을 예측합니다. **가우시안 표현은 균일한 구조를 가지므로 애니메이션과 편집이 용이하며**, 고해상도의 사진처럼 사실적인 텍스처를 생성합니다.  IDOL은 기존의 방법들보다 **속도와 정확성이 뛰어나며**, 다양한 응용 분야에 적용 가능한 **일반화된 성능**을 보여줍니다.  결론적으로 본 논문의 3D 재구성 방법은 **데이터셋의 규모와 모델의 설계**라는 두 가지 핵심 요소에 집중하여 단일 이미지 기반 3D 인간 모델링의 새로운 기준을 제시합니다.

#### Future Directions
본 논문에서 제시된 IDOL 모델은 단일 이미지로부터 사실적인 3D 아바타를 생성하는 데 있어 상당한 발전을 이루었지만, 여전히 개선의 여지가 있습니다. **향후 연구 방향**으로는 첫째, **더욱 다양하고 방대한 데이터셋**을 구축하는 것입니다. 현재 모델은 다양한 인종, 연령, 의상, 자세 등을 포함하도록 데이터셋을 확장하여 일반화 성능을 향상시킬 수 있습니다.  둘째, **모델의 효율성 개선**입니다. 현재 모델은 1초 이내의 빠른 속도를 자랑하지만, 더욱 가볍고 효율적인 모델 구조를 연구하여 실시간 응용 분야에 적용 가능성을 높일 수 있습니다.  셋째, **다중 사람 및 물체 상호작용**에 대한 지원입니다. 현재는 단일 인물에만 초점을 맞추고 있으므로, 여러 사람이나 물체와의 상호작용을 처리할 수 있도록 모델을 확장하는 것이 필요합니다. 마지막으로, **모델의 해석성 및 제어 가능성**을 높이는 연구가 필요합니다. 생성 과정에 대한 이해를 높이고, 사용자가 아바타의 외형, 움직임, 표정 등을 직관적으로 제어할 수 있도록 하는 것이 중요합니다. 이러한 노력을 통해 IDOL 모델은 더욱 실용적이고 강력한 3D 아바타 생성 도구로 발전할 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.14963/x3.png)

> 🔼 본 그림은 HuGe100K 데이터셋 생성 과정을 보여줍니다.  GPT-4 템플릿을 사용하여 다양한 속성 조합을 만들고, 이를 바탕으로 텍스트 프롬프트를 생성합니다.  FLUX를 통해 합성 이미지를 생성하고, DeepFashion의 실제 이미지와 결합합니다.  SMPL-X 피팅을 통해 360도 회전과 다양한 애니메이션 동작을 포함한 다중 뷰 포즈 시퀀스를 생성하고, MVChamp 모델을 이용하여 이 시퀀스를 다중 뷰 이미지로 변환하여 데이터셋의 3D 일관성을 확보합니다.  즉, 다양한 인물의 다양한 자세와 의상을 갖는 고해상도 이미지 데이터를 대량으로 생성하는 과정을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Pipeline for constructing our HuGe100K. Diverse attribute combinations from GPT-4 templates create text prompts, generating synthetic images via FLUX, combined with real images from DeepFashion. SMPL-X fitting produces multi-view pose sequences with 360-degree rotations and diverse animatable motions. MVChamp then converts these sequences into multi-view images, ensuring 3D consistency in the dataset.
> </details>



![](https://arxiv.org/html/2412.14963/x4.png)

> 🔼 그림 3은 제안된 HuGe100K 데이터셋에서 한 쌍의 예시를 보여줍니다. 각 참조 이미지에 대해 추정된 형태와 특정 자세를 사용하여 여러 각도의 이미지 세트를 생성합니다. 그림은 자세가 잘 정렬되어 있음을 보여줍니다.  즉, 하나의 사람의 이미지를 기반으로 여러 각도에서 촬영된 것처럼 보이는 일관된 이미지 세트를 생성했음을 의미합니다. 이는 3D 인체 모델 재구성의 정확성과 신뢰성을 높이는 데 중요한 요소입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: A paired example from the proposed HuGe100K Dataset. For each reference image, we generate a set of multi-view images using an estimated shape and a specific pose. The figure shows the pose is well-aligned.
> </details>



![](https://arxiv.org/html/2412.14963/x5.png)

> 🔼 그림 4는 IDOL의 구조를 보여줍니다. IDOL은 단일 이미지에서 애니메이션 가능한 3D 인체를 재구성하기 위한 완전 미분 가능한 트랜스포머 기반 프레임워크입니다.  고해상도(1024x1024) 인코더 [29]를 통합하여 이미지 토큰과 학습 가능한 UV 토큰을 UV 정렬 트랜스포머를 통해 융합합니다. UV 디코더는 중간 표현으로 가우시안 속성 맵을 예측하여 SMPL-X 모델에 의해 정의된 구조화된 2D UV 공간에서 인체의 기하학적 형태와 외관을 포착합니다. 이러한 맵은 SMPL-X 모델과 함께 결합되어 정규화된 공간에서 3D 인체 아바타를 나타내며, 선형 블렌드 스키닝(LBS)을 사용하여 애니메이션할 수 있습니다. 다양한 자세와 신원을 가진 다중 뷰 이미지를 사용하여 모델을 최적화하고 자세, 외관 및 형태를 분리하는 것을 학습합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: The architecture of IDOL, a full-differentiable transformer-based framework for reconstructing animatable 3D human from a single image. The model integrates a high-resolution (1024×1024102410241024\times 10241024 × 1024) encoder [29] and fuses image tokens with learnable UV tokens through the UV-Alignment Transformer. A UV Decoder predicts Gaussian attribute maps as intermediate representations, capturing the human’s geometry and appearance in a structured 2D UV space defined by the SMPL-X model. These maps, in conjunction with the SMPL-X model, represent a 3D human avatar in a canonical space, which can be animated using linear blend skinning (LBS). The model is optimized using multi-view images with diverse poses and identities, learning to disentangle pose, appearance, and shape.
> </details>



![](https://arxiv.org/html/2412.14963/x6.png)

> 🔼 그림 5는 MVChamp에 대한 ablation study 결과와 다른 방법들과의 비교 실험 결과를 보여줍니다. 왼쪽에는 MVChamp의 각 구성 요소(손 고화질화, 얼굴 바꿔치기, THuman2.1 파인튜닝, 시간적 잡음 제거 전략)를 제거했을 때의 결과를 보여주는 ablation study가 제시되어 있습니다. 각 ablation study는 해당 구성 요소를 제거했을 때 이미지 생성 품질에 어떤 영향을 미치는지 보여줍니다. 오른쪽에는 제안된 방법인 MVChamp를 Champ, MimicMotion, SV3D와 비교한 결과가 제시되어 있습니다. 비교 실험은 다양한 측면(관절의 정확도, 텍스처 품질, 일관성 등)에서 MVChamp의 성능을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Qualitative results of our MVChamp ablation study (left) and comparison experiment (right).
> </details>



![](https://arxiv.org/html/2412.14963/x7.png)

> 🔼 그림 6은 IDOL 모델의 성능을 보여주는 두 가지 비교 실험 결과를 보여줍니다. (a) 상단은 단일 이미지에서 새로운 뷰를 합성하는 능력을 보여줍니다.  기존 방법들과 비교하여 IDOL 모델이 더욱 사실적이고 정확한 결과를 생성하는 것을 확인할 수 있습니다. (b) 하단은 IDOL 모델을 사용하여 애니메이션 결과를 보여줍니다.  다양한 자세와 동작을 자연스럽게 표현하는 IDOL 모델의 능력을 시각적으로 확인할 수 있습니다.  전체적으로 그림 6은 IDOL 모델의 우수한 3D 인간 재구성 및 애니메이션 능력을 잘 보여주는 그림입니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Comparisons on (a) the upper: novel-view synthesis given a single image, and (b) the lower: our animated results.
> </details>



![](https://arxiv.org/html/2412.14963/x8.png)

> 🔼 그림 7은 IDOL 모델의 ablation study 결과를 보여줍니다.  (a)는 기준 이미지, (b)는 Sapiens 인코더 없이, (c)는 HuGe100K 데이터셋 없이, (d)는 IDOL의 전체 모델을 사용한 결과입니다.  각각의 이미지를 비교하여, Sapiens 인코더와 HuGe100K 데이터셋이 IDOL 모델의 성능에 미치는 영향을 시각적으로 보여줍니다.  Sapiens 인코더와 HuGe100K 데이터셋이 없을 경우, 결과 이미지의 디테일이 부족하고 왜곡이 심해지는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Qualitative Results of Ablation Study of IDOL.
> </details>



![](https://arxiv.org/html/2412.14963/x9.png)

> 🔼 그림 8은 IDOL 모델의 편집 가능성을 보여줍니다. (a)에서는 질감 편집을 통해 의류 패턴을 변경하는 것을 보여주고, (b)에서는 신체 형태 편집을 통해 아바타의 신체 크기를 조정하는 것을 보여줍니다. 이는 사용자가 아바타의 외모와 신체 특징을 자유롭게 제어할 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Controllable Avatar Editing: (a) texture editing; (b) body shape editing.
> </details>



![](https://arxiv.org/html/2412.14963/extracted/6078595/fig/supp_dataset/fig_representation.png)

> 🔼 그림 9는 제시된 이미지와 비디오를 사용하여 사람을 재현하는 과정을 보여줍니다. 먼저, 참조 이미지를 사용하여 IDOL 모델이 대상 인물의 3D 아바타를 생성합니다. 그런 다음, 참조 비디오의 포즈와 배경을 사용하여 생성된 아바타를 애니메이션화합니다. 마지막으로, 배경을 복구하고, 아바타를 비디오에 매끄럽게 결합합니다. 이는 IDOL 모델이 비디오 내 인물을 효율적으로 교체하고 품질을 유지하는 데 탁월하다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: The visualization of the reenactment.
> </details>



![](https://arxiv.org/html/2412.14963/extracted/6078595/fig/supp_dataset/flux_collections.jpg)

> 🔼 그림 10은 3D 인체 재구성에 대한 다양한 접근 방식을 시각적으로 보여줍니다. PIFU는 매개변수 사전 없이 3D 인체를 직접 예측하는 반면, GTA/SIFU는 SMPL 정렬을 위해 계산적으로 비용이 많이 드는 반복 최적화에 의존합니다. IDOL 방식은 SMPL-X를 사전으로 활용하여 오류 누적의 문제를 피하면서 더욱 강력하고 정확한 재구성을 가능하게 합니다. 또한, IDOL 방식은 애니메이션 및 편집 기능을 직접 지원하여 디지털 콘텐츠 제작에 추가적인 응용 프로그램을 활성화합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Visualization of different approaches for 3D human reconstruction. Unlike PIFu, which directly predicts the 3D human without a parametric prior, and GTA/SIFU, which relies on computationally expensive loop optimization for SMPL alignment, our IDOL method leverages SMPL-X as a prior. This enables more robust and accurate reconstruction while avoiding the pitfalls of error accumulation. Furthermore, our method supports direct animation and editing, enabling additional applications in digital content creation.
> </details>



![](https://arxiv.org/html/2412.14963/extracted/6078595/fig/supp_dataset/fig_visual_comparison.png)

> 🔼 그림 11은 논문의 부록 A.3절에 있는 그림으로,  Flux [18]라는 이미지 생성 모델을 사용하여 생성된 다양한 이미지들을 보여줍니다.  이 이미지들은 다양한 연령, 체형, 의상, 배경 등을 가진 사람들의 전신 사진으로, IDOL 모델의 훈련 데이터셋인 HuGe100K를 구성하는 데 사용된 이미지들의 다양성을 보여주는 예시입니다. 각 이미지는 서로 다른 특징들을 가지고 있어, IDOL 모델이 다양한 사람들의 모습을 정확하게 재구성할 수 있도록 돕는 데 기여했습니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Visualization of diverse images generated by Flux [18].
> </details>



![](https://arxiv.org/html/2412.14963/extracted/6078595/fig/supp_dataset/fig_visual_comp_sgd.jpg)

> 🔼 그림 12는 HuGe100K 데이터셋에서 Flux를 사용하여 생성한 이미지들의 예시를 보여줍니다. 이 이미지들은 다양한 자세와 의상을 입은 사람들을 보여주며, 각 이미지는 다양한 각도에서 촬영된 여러 장의 사진으로 구성되어 있습니다. 이는 IDOL 모델이 다양한 사람들의 모습을 정확하게 재구성할 수 있도록 돕는 핵심적인 데이터셋입니다.  다양한 각도의 사진은 3D 모델의 정확도를 높이는 데 기여합니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Visualization of examples from HuGe100K, where the images are generated by Flux and used to generate multi-view images.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | MSE ↓ | PSNR ↑ | LPIPS ↓ |
|---|---|---|---|
| SIFU [73] | 0.042 | 14.204 | 1.612 |
| GTA [72] | 0.041 | 14.282 | 1.629 |
| Ours-w/o _HuGe100K_ | 0.017 | 19.225 | 1.326 |
| Ours-full | **0.008** | **21.673** | **1.138** |{{< /table-caption >}}
> 🔼 표 2는 제안된 IDOL 모델의 성능을 평가하기 위해 수행된 비교 실험 및 ablation 실험의 결과를 보여줍니다.  MSE(Mean Squared Error), PSNR(Peak Signal-to-Noise Ratio), LPIPS(Learned Perceptual Image Patch Similarity) 세 가지 지표를 사용하여, IDOL 모델의 성능을 기존의 다른 방법들 (SIFU, GTA, HuGe100K를 사용하지 않은 IDOL,  전체 HuGe100K를 사용한 IDOL) 과 비교 분석했습니다. 이를 통해  제안된 방법의 우수성과 데이터셋의 중요성을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Evaluation of Comparison and Ablation Experiments.
> </details>

{{< table-caption >}}
| Method | Face | Clothing | Back | Overall |
|---|---|---|---|---|
| GTA | 0% | 2.27% | 0% | 0% |
| SIFU | 2.27% | 4.55% | 4.55% | 4.55% |
| HumanLRM | 45.45% | 43.18% | 36.36% | 45.45% |
| Ours | 52.28% | 50.0% | 59.09% | 50% |{{< /table-caption >}}
> 🔼 본 표는 HumanLRM 논문에서 제시된, HumanLRM의 강점을 부각하는 사례들을 대상으로 IDOL 모델의 성능을 평가한 사용자 연구 결과를 보여줍니다. HumanLRM에 유리하도록 사례를 선정했음에도 불구하고, IDOL 모델은 얼굴, 의복, 후면 시야의 일관성 및 전반적인 화질 측면에서 HumanLRM보다 약간 나은 성능을 보였습니다. 이는 IDOL 모델의 견고성과 다양한 조건에서의 효과성을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 3: The user study. We evaluated IDOL on selected cases reported by HumanLRM[57], designed to highlight their strengths. Despite the selection for HumanLRM, our method achieves slightly superior performance, demonstrating greater robustness and effectiveness under comparable conditions.
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