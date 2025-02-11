---
title: "AuraFusion360: Augmented Unseen Region Alignment for Reference-based 360° Unbounded Scene Inpainting"
summary: "AuraFusion360: 참조 기반 360도 무제한 장면 인페인팅을 위한 새로운 방법 제시!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "3D Vision", "🏢 National Yang Ming Chiao Tung University",]
showSummary: true
date: 2025-02-07
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.05176 {{< /keyword >}}
{{< keyword icon="writer" >}} Chung-Ho Wu et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-10 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.05176" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.05176" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/aurafusion360-augmented-unseen-region" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 3D 장면 인페인팅 방법들은 360도 무제한 환경에서의 뷰 일관성 및 기하학적 정확도 유지에 어려움을 겪었습니다. 특히, 기존 방법들은 뷰 간의 일관성을 유지하지 못하거나, **360도 환경에서의 뷰 변화에 제대로 대처하지 못하는 문제점**을 가지고 있습니다. 또한, 기존 데이터셋은 부족하여 연구 개발에 어려움이 있었습니다. 

본 논문에서는 이러한 문제점을 해결하기 위해 **AuraFusion360**이라는 새로운 참조 기반 방법을 제시합니다. AuraFusion360는 Gaussian Splatting을 기반으로 하여 깊이 인식 마스크 생성, 적응형 가이드 깊이 확산, SDEdit 기반 세부 정보 향상 등의 기법을 통해 **다양한 시점에서도 기하학적 정확도와 뷰 일관성을 유지하는 고품질의 객체 제거 및 구멍 채우기**를 가능하게 합니다. 또한, 본 논문에서는 **360도 무제한 장면 인페인팅을 위한 최초의 포괄적인 데이터셋인 360-USID**를 공개하여 후속 연구에 기여합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 360도 무제한 장면에서 고품질의 객체 제거 및 구멍 채우기를 가능하게 하는 참조 기반 방법을 제시합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 깊이 인식이 가능한 새로운 마스크 생성 기법, 적응형 가이드 깊이 확산 기법, 그리고 SDEdit 기반 세부 정보 향상 기법을 도입했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 360도 무제한 장면 인페인팅을 위한 최초의 포괄적인 데이터셋인 360-USID를 공개했습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**본 논문은 360도 무제한 환경에서의 3D 장면 인페인팅 분야에 대한 중요한 발전을 제시합니다.** 기존 방법들의 한계를 극복하고 고품질의 결과를 달성함으로써, 가상현실, 증강현실, 건축 시각화 등 다양한 분야에 광범위한 영향을 미칠 수 있습니다. 또한, 제시된 새로운 데이터셋과 방법론은 후속 연구에 귀중한 자원이 될 것이며, **향후 연구 방향에 대한 새로운 가능성을 열어줄 것입니다.**

------
#### Visual Insights



![](https://arxiv.org/html/2502.05176/x2.png)

> 🔼 이 그림은 AuraFusion360 방법의 개요를 보여줍니다. 카메라 파라미터, 객체 마스크, 그리고 참조 이미지가 주어지면, AuraFusion360은 객체 마스크가 적용된 Gaussian Splatting 표현을 생성합니다. 이 표현은 참조 이미지와 일관성을 유지하면서 마스크된 객체를 제거하고 새로운 뷰의 합성 이미지를 생성할 수 있습니다.  입력 이미지는 여러 각도에서 촬영된 이미지들이고, 객체 마스크는 제거할 객체의 영역을 나타냅니다. 참조 이미지는 배경과 주변 환경 정보를 제공합니다.  AuraFusion360은 이러한 정보들을 활용하여  360도 전방위의 자연스럽고 일관성 있는 합성 이미지를 생성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  Overview of our reference-based 360° unbounded scene inpainting method. Given input images with camera parameters, object masks, and a reference image, our AuraFusion360 approach generates an object-masked Gaussian Splatting representation. This representation can then render novel views of the inpainted scene, effectively removing the masked objects while maintaining consistency with the reference image.
> </details>





{{< table-caption >}}
| PSNR ↑ / LPIPS ↓ | Carton | Cone | Cookie | Newcone | Plant | Skateboard | Sunflower | Average |
|---|---|---|---|---|---|---|---|---|---|
| SPIn-NeRF [34] | 16.659 / 0.539 | 15.438 / 0.389 | 11.879 / 0.521 | 17.131 / 0.519 | 16.850 / 0.401 | 15.645 / 0.675 | 23.538 / 0.206 | 16.734 / 0.464 |
| 2DGS [18] + LaMa [53] | 16.433 / 0.499 | 15.591 / 0.351 | 11.711 / 0.538 | 16.598 / 0.670 | 14.491 / 0.564 | 15.520 / 0.639 | 23.024 / 0.194 | 16.195 / 0.494 |
| 2DGS [18] + LeftRefill [6] | 15.157 / 0.567 | 16.143 / 0.372 | 12.458 / 0.526 | 16.717 / 0.677 | 12.856 / 0.666 | 16.429 / 0.634 | 24.216 / 0.181 | 16.282 / 0.518 |
| LeftRefill [6] | 14.667 / 0.560 | 14.933 / 0.380 | 11.148 / 0.519 | 16.264 / 0.448 | 16.183 / 0.463 | 14.912 / 0.572 | 18.851 / 0.331 | 15.280 / 0.468 |
| Gaussian Grouping [65] | 16.695 / 0.502 | 14.549 / 0.366 | 11.564 / 0.731 | 16.745 / 0.533 | 16.175 / 0.440 | 16.002 / 0.577 | 20.787 / 0.209 | 16.074 / 0.480 |
| GScream [60] | 14.609 / 0.587 | 14.655 / 0.476 | 12.733 / 0.429 | 13.662 / 0.605 | 16.238 / 0.437 | 12.941 / 0.626 | 18.470 / 0.436 | 14.758 / 0.514 |
| Infusion [27] | 14.191 / 0.555 | 14.163 / 0.439 | 12.051 / 0.486 | 9.562 / 0.624 | 16.127 / 0.406 | 13.624 / 0.638 | 21.195 / 0.238 | 14.416 / 0.484 |
| AuraFusion360 (Ours) w/o SDEdit | 13.731 / 0.477 | 14.260 / 0.390 | 12.332 / 0.445 | 16.646 / 0.460 | 17.609 / 0.319 | 15.107 / 0.580 | 24.884 / 0.170 | 16.367 / 0.406 |
| AuraFusion360 (Ours) | 17.675 / 0.473 | 15.626 / 0.332 | 12.841 / 0.434 | 17.536 / 0.426 | 18.001 / 0.322 | 17.007 / 0.559 | 24.943 / 0.173 | 17.661 / 0.388 |{{< /table-caption >}}

> 🔼 표 1은 논문에서 제시된 360-USID 데이터셋을 사용하여 다양한 360도 이미지 채색 기법들의 정량적 비교 결과를 보여줍니다.  각 기법의 성능은 PSNR(Peak Signal-to-Noise Ratio)과 LPIPS(Learned Perceptual Image Patch Similarity) 두 가지 지표로 평가되었으며,  각 장면별 및 전체 평균 성능이 제시되어 있습니다. 붉은색 텍스트는 각 지표에서 가장 좋은 성능을 보인 방법을, 파란색 텍스트는 두 번째로 좋은 성능을 보인 방법을 나타냅니다. 이를 통해 다양한 방법들의 상대적 성능을 명확하게 비교하고,  어떤 방법이 특정 장면이나 전반적으로 더 나은 성능을 보이는지 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Quantitative comparison of 360° inpainting methods on the 360-USID dataset. Red text indicates the best, and blue text indicates the second-best performing method.
> </details>





### In-depth insights


#### 360° Inpainting
360도 이미지 인페인팅은 **전방향 시야**를 가진 이미지에서 물체 제거 및 구멍 메우기 과제를 다룹니다.  기존 방법들은 뷰 일관성 및 기하학적 정확성을 유지하는 데 어려움을 겪었지만, 본 논문에서는 참조 이미지를 기반으로 고품질 객체 제거 및 3D 구멍 메우기를 가능하게 하는 새로운 참조 기반 방법을 제시합니다. 이는 **깊이 인식 없는 영역 마스크 생성**, **적응적 유도 깊이 확산**, **SDEdit 기반 세부 향상** 이라는 세 가지 핵심 구성 요소를 통해 이루어집니다. 특히, 360도 환경에서의 **멀티 뷰 일관성** 유지에 초점을 맞추고, 기존 방법들보다 우수한 성능을 보임을 실험적으로 증명합니다.  **360-USID** 라는 새로운 데이터셋을 통해 360도 인페인팅의 벤치마크를 제공하여 향후 연구에 기여합니다.  하지만 고해상도나 대규모 장면에서는 연산 비용이 높아 실시간 처리에는 제약이 있습니다.  **깊이 추정의 정확성**에 따라 성능이 영향받을 수 있으며, 심한 폐색 영역에서는 오류가 발생할 수 있다는 점 또한 한계로 지적됩니다. 

#### AGDD Method
본 논문에서 제안하는 AGDD(Adaptive Guided Depth Diffusion) 방법은 **360도 무경계 환경에서의 정확한 깊이 정렬**이라는 어려운 문제를 해결하기 위해 고안되었습니다. 기존의 단안 깊이 추정 방법의 한계점인 절대적 스케일 정보 부족과 비정규 깊이 값 생성 문제를 해결하고자, **적응적 손실 함수**를 통해 추정된 깊이와 기존의 불완전한 깊이 간의 정렬을 최적화합니다.  **VAE 디코더**를 사용하여 잠재적인 잡음을 제거하고, **반복적인 잡음 제거 과정**을 통해 정확도를 높이며, **unseen 영역에 대한 정렬**을 특히 강조합니다.  이는 단순히 깊이 값을 완벽하게 일치시키는 것을 넘어, **시각적 일관성을 유지하며** 3D 시각화에 필요한 깊이 정보의 정확성을 높이는 데 중점을 둡니다.  **참조 영상으로부터의 정렬된 깊이 정보**는 이후 Gaussian 초기화 및 SDEdit 기반 세부사항 향상에 중요한 역할을 합니다.  결론적으로 AGDD는 **360도 무경계 깊이 추정 및 시각적 일관성 확보**라는 난제에 대한 효과적인 해결책을 제시합니다.

#### 360-USID Dataset
본 논문에서 제시된 360-USID 데이터셋은 **360도 무제한 시야(unbounded) 환경**에서의 3D 신 scene inpainting 연구를 위한 **최초의 종합적인 데이터셋**입니다. 기존 방법들의 한계를 극복하고 다양한 환경에서의 성능 평가를 가능하게 하기 위해, 실내외 다양한 장면 7개를 포함하며 각 장면 당 **180~200개의 학습 이미지**와 **30개의 테스트 이미지**, 그리고 **1개의 참조 이미지** (물체가 없는)를 제공합니다.  **다양한 촬영 각도**와 **조명 조건**을 고려하여 실제 환경과 유사한 데이터를 구축했으며, **정확한 물체 마스크**를 제공함으로써 정량적 및 정성적 평가를 모두 지원합니다. 360도 영상을 처리하는 기존 방법들의 성능 비교 및 향후 연구를 위한 벤치마크 역할을 수행하며, 특히 **멀티뷰 일관성 및 기하학적 정확도**를 평가하는 데 유용한 자원이 될 것입니다.

#### Future Works
본 논문에서 제시된 AuraFusion360 모델은 360도 무제한 공간에서의 물체 제거 및 빈 공간 채우기 작업에 있어 상당한 성과를 보였으나, **실시간 처리 및 고해상도 이미지 처리**에 대한 어려움과 **복잡한 장면에서의 정확도 저하** 문제점을 보였습니다. 따라서 향후 연구 방향은 **실시간 처리 성능 향상을 위한 효율적인 알고리즘 개발**과 **고해상도 이미지 및 대규모 장면 처리를 위한 확장성 연구**에 초점을 맞춰야 합니다.  또한, **다양한 유형의 물체 및 복잡한 배경에 대한 일반화 성능 개선**, **불확실한 영역(unseen region) 예측 정확도 향상**, **다른 모달리티(예: 깊이 정보, 점군 데이터)와의 통합을 통한 성능 향상**, 그리고 **새로운 360도 무제한 장면 데이터셋 구축**이 중요한 과제가 될 것입니다.  이를 통해 AuraFusion360 모델은 더욱 실용적이고 강력한 3D 장면 편집 도구로 발전할 수 있을 것입니다.

#### Limitations
본 논문의 "Limitations" 섹션에서는 제시된 방법의 한계점을 명확하게 제시하고 있습니다.  **실시간 처리의 어려움**은 고해상도 또는 대규모 장면에서 투영된 초기 가우시안을 렌더링하고 SDEdit을 적용하는 데 상당한 시간이 소요됨을 의미합니다.  이는 실시간 애플리케이션에는 적합하지 않다는 점을 시사합니다.  **폐색이 심한 영역에서의 부정확한 픽셀 투영** 또한 중요한 한계점입니다.  폐색이 심한 영역 근처에서 물체 제거가 필요한 경우, 픽셀의 부정확한 투영으로 인해 최종 결과물에 플로터(떠다니는 물체)가 발생할 수 있습니다.  이는 비단 본 논문의 방법뿐만 아니라 비교된 다른 방법들에서도 나타나는 문제이므로, **향후 연구를 위한 중요한 개선 방향**을 제시합니다.  **고해상도 이미지 처리 및 대규모 장면 처리의 어려움**은 앞으로 해결해야 할 과제이며, **실시간 처리를 위한 효율적인 알고리즘 개발**과 더불어 **폐색 문제 해결**에 대한 추가적인 연구가 필요합니다.  본 논문에서는 이러한 한계점을 명확히 인지하고 있으며, 향후 연구 방향을 제시함으로써 연구의 신뢰성을 높이고 있습니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.05176/x3.png)

> 🔼 그림 2는 다양한 3D 이미지 채색 기법들을 비교 분석한 결과를 보여줍니다.  기존의 SPIn-NeRF [34]나 GScream [60]과 같은 방법들은 정면을 향하는 장면에 맞춰 설계되었기 때문에 360도 전방위 장면에서는 성능이 저하되는 경향이 있습니다.  Infusion [27]과 같은 참조 기반 방법들은 깊이 완성 모델의 부정확성으로 인해 참조 이미지를 3D 장면에 정확하게 투영하지 못하여 미세 조정 과정에서 인공물이 발생하는 문제가 있습니다. Gaussian Grouping [65]은 마스크 생성 과정에서 보이지 않는 영역을 잘못 인식하여 채색 품질이 저하될 수 있습니다.  반면 AuraFusion360은 적응적 유도 깊이 확산을 통해 보다 정확한 보이지 않는 영역 마스크를 생성하고, 초기 점에 SDEdit [30]을 적용하여 확산 사전 정보를 활용하면서 RGB 안내의 다중 보기 일관성을 유지함으로써 이러한 문제점들을 해결합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Comparison with different 3D inpainting approaches. Previous methods, such as SPin-NeRF [34] and GScream [60], are tailored for forward-facing scenes and tend to underperform in 360° unbounded scenarios. Reference-based methods, such as Infusion [27], whose depth completion model struggles to accurately project the reference view back into the 3D scene, leading to fine-tuning artifacts. Gaussian Grouping [65] often misidentifies the unseen region during mask generation, which can degrade inpainting quality. Our method, AuraFusion360, achieves a more accurate unseen mask and enhanced depth alignment through Adaptive Guided Depth Diffusion, with SDEdit [30] applied to the initial points to leverage diffusion prior while also maintaining multi-view consistency in RGB guidance.
> </details>



![](https://arxiv.org/html/2502.05176/x4.png)

> 🔼 그림 3은 AuraFusion360 방법의 개요를 보여줍니다. 이 방법은 다중 뷰 RGB 이미지와 해당 객체 마스크를 입력으로 받아 마스크된 객체가 제거된 가우시안 표현을 출력합니다. 이 파이프라인은 세 가지 주요 단계로 구성됩니다. (a) 깊이 인식이 되는 보이지 않는 영역 마스크 생성은 실제로 가려진 영역(보이지 않는 영역이라고 함)을 식별합니다. (b) 참조 뷰에 대한 깊이 정렬된 가우시안 초기화는 객체 제거 후 참조 RGB 정보가 포함된 초기화된 가우시안을 사용하여 보이지 않는 영역을 채웁니다. (c) SDEdit 기반 RGB 안내 개선은 참조 뷰 정보를 유지하면서 인페인팅 모델을 사용하여 세부적인 부분을 향상시킵니다. 무작위 노이즈를 사용하여 SDEdit을 적용하는 대신, 렌더링된 초기 가우시안에 DDIM 반전을 사용하여 참조 뷰의 구조를 유지하는 노이즈를 생성하여 모든 RGB 안내에 걸쳐 다중 뷰 일관성을 보장합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Overview of our method. Our approach takes multi-view RGB images and corresponding object masks as input and outputs a Gaussian representation with the masked objects removed. The pipeline consists of three main stages: (a) Depth-Aware Unseen Masks Generation to identify truly occluded areas, referred to as the “unseen region”, (b) Depth-Aligned Gaussian Initialization on Reference View to fill unseen regions with initialized Gaussian containing reference RGB information after object removal, and (c) SDEdit-Based RGB Guidance for Detail Enhancement, which enhances fine details using an inpainting model while preserving reference view information. Instead of applying SDEdit with random noise, we use DDIM Inversion on the rendered initial Gaussians to generate noise that retains the structure of the reference view, ensuring multi-view consistency across all RGB Guidance.
> </details>



![](https://arxiv.org/html/2502.05176/x5.png)

> 🔼 그림 4는 깊이 워핑을 사용한 보이지 않는 영역 마스크 생성 과정을 보여줍니다. 특정 뷰 n에 대한 보이지 않는 영역 마스크를 얻기 위해, 먼저 렌더링된 불완전한 깊이 정보 D𝑛incomplete를 사용하여 뷰 n과 다른 모든 뷰 i 간의 픽셀 대응 관계를 계산합니다. 각 뷰 i에 대해, 제거 영역 Ri를 뷰 n에 맞춰 역변환하여 폐색을 정렬합니다. 여러 뷰의 결과를 평균화하고 임계값을 적용하여 보이지 않는 영역 마스크의 초기 윤곽선을 생성합니다. 이 윤곽선은 SAM2 [44]에 대한 경계 상자 프롬프트로 변환되어 뷰 n에 대한 최종 보이지 않는 영역 마스크를 생성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Overview of the Unseen Mask Generation Process using Depth Warping. To obtain the unseen mask for view n𝑛nitalic_n, we calculate the pixel correspondences between the view n𝑛nitalic_n and all other views i𝑖iitalic_i by using the rendered incomplete depth Dnincompletesuperscriptsubscript𝐷𝑛incompleteD_{n}^{\text{incomplete}}italic_D start_POSTSUBSCRIPT italic_n end_POSTSUBSCRIPT start_POSTSUPERSCRIPT incomplete end_POSTSUPERSCRIPT. For each view i𝑖iitalic_i, the removal region Risubscript𝑅𝑖R_{i}italic_R start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT is backward traversal to view n𝑛nitalic_n to align occlusions. We then aggregate the results from multiple views, averaging and applying a threshold to produce the initial contour of the unseen mask. This contour is subsequently converted into a bounding box prompt for SAM2 [44], which refines the unseen mask to its final version for view n𝑛nitalic_n.
> </details>



![](https://arxiv.org/html/2502.05176/x6.png)

> 🔼 그림 5는 적응적 유도 심도 확산(AGDD)의 개요를 보여줍니다.  AGDD는 이미지 잠재 벡터, 불완전한 심도, 그리고 보이지 않는 영역 마스크를 입력받아 정렬된 심도 추정값을 생성하는 프레임워크입니다.  (a) 부분은 보이지 않는 영역 마스크를 확장하고 원본 마스크를 빼서 유도 영역을 식별하는 과정을 보여줍니다. (b) 부분은 각 디노이징 시간 단계 t에서 미리 디코딩된 심도와 불완전한 심도 간의 적응적 손실(ℒadaptive)을 계산하여 잡음 입력 (ϵ̂t)을 업데이트하는 과정을 보여줍니다. 이 과정은 다음 디노이징 단계로 넘어가기 전에 N번 반복되며, 추정된 심도가 유도 영역 내의 불완전한 심도 분포와 일치하도록 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5:  Overview of Adaptive Guided Depth Diffusion (AGDD). The framework takes image latent, incomplete depth, and unseen mask as inputs to generate aligned depth estimates. (a) The guided region is identified by dilating the unseen mask and subtracting the original mask. (b) At each denoising timestep t𝑡titalic_t, an adaptive loss ℒadaptivesubscriptℒadaptive\mathcal{L}_{\text{adaptive}}caligraphic_L start_POSTSUBSCRIPT adaptive end_POSTSUBSCRIPT is computed between the pre-decoded and incomplete depth to update the noise input ϵ^tsubscript^italic-ϵ𝑡\hat{\epsilon}_{t}over^ start_ARG italic_ϵ end_ARG start_POSTSUBSCRIPT italic_t end_POSTSUBSCRIPT. This process repeats N𝑁Nitalic_N times before advancing to the next denoising step, ensuring the estimated depth aligns with the incomplete depth distribution in the guided region.
> </details>



![](https://arxiv.org/html/2502.05176/x7.png)

> 🔼 그림 6은 논문에서 제시하는 새로운 360도 무제한 장면 인페인팅 데이터셋인 360-USID의 개요를 보여줍니다.  이 데이터셋은 다양한 환경에서 3D 인페인팅 기법을 평가하기 위해 실내외 환경을 모두 포함하는 7개의 장면(상자, 원뿔, 새로운 원뿔, 스케이트보드, 식물, 쿠키, 해바라기)의 샘플 이미지를 보여줍니다. 오른쪽 하단의 표는 각 장면에 대한 통계를 보여주는데, 학습에 사용된 뷰의 수와 실제값(GT) 새로운 뷰의 수를 포함합니다. 이 데이터셋은 다양한 실내외 환경을 제공하여 3D 인페인팅 방법을 평가할 수 있도록 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Overview of the 360-USID dataset. Sample images from each scene, including five outdoor scenes (Carton, Cone, Newcone, Skateboard, Plant) and two indoor scenes (Cookie, Sunflower). (Bottom right) The table shows statistics for each scene, including the number of training views and ground truth (GT) novel views. The dataset provides a diverse range of environments for evaluating 3D inpainting methods in both indoor and outdoor settings.
> </details>



![](https://arxiv.org/html/2502.05176/x8.png)

> 🔼 그림 7은 논문에서 제시된 360-USID 데이터셋을 구축하기 위한 데이터 수집 과정을 보여줍니다.  (a)는 훈련 데이터를 수집하는 과정으로, 장면 내의 물체 주변에서 여러 각도로 이미지를 촬영합니다.  (b)는 기준 이미지를 얻는 과정으로, 삼각대에 카메라를 고정하여 물체가 있는 장면의 고정된 기준 이미지를 촬영합니다. (c)는 새로운 뷰를 수집하는 과정으로, 물체를 제거한 후 다양한 시점에서 추가적인 이미지를 촬영하며, 여기에는 기준 이미지와 동일한 삼각대 위치에서 촬영한 이미지도 포함됩니다. 이 그림은 360도 환경에서의 물체 제거 및 배경 복원 작업에 필요한 데이터셋 구축 과정을 자세히 설명합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Illustration of the data capture process for the 360-USID dataset. (a) Capturing training views: Multiple images are taken around the object in the scene. (b) Capturing the reference view: A camera is mounted on a tripod to capture a fixed reference view (with an object). (c) Capturing novel views: After removing the object, additional images are taken from various viewpoints, including one from the same tripod position as the reference image.
> </details>



![](https://arxiv.org/html/2502.05176/x9.png)

> 🔼 그림 8은 논문에서 제시된 360-USID 데이터셋을 사용하여 다양한 최첨단 방법들과 제안된 방법을 비교 분석한 결과를 보여줍니다. 비교 대상 방법은 Gaussian Grouping [65], 2DGS + LeftRefill, Infusion [27]입니다. Gaussian Grouping은 보이지 않는 영역을 잘못 식별하여 부유하는 인공물이 발생하는 반면, 2DGS + LeftRefill은 뷰 일관성 문제를 보입니다. 하지만 제안된 방법은 기하학적 일관성을 유지하고 다양한 관점에서 미세한 디테일을 보존하는 데 성공합니다. 참조용으로 실제 정답(GT) 이미지가 표시되며, 비교를 위해 물체가 있는 원본 장면 이미지도 첫 번째 행에 함께 제공됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Visual Comparison on our 360-USID dataset. We compare our method against state-of-the-art approaches including Gaussian Grouping [65], 2DGS + LeftRefill, and Infusion [27]. While Gaussian Grouping struggles with misidentifying unseen regions, leading to floating artifacts, and 2DGS + LeftRefill faces view consistency issues, our method successfully maintains geometric consistency and preserves fine details across different viewpoints. Ground truth (GT) is shown for reference, and the original scene with an object is provided in the first row for comparison.
> </details>



![](https://arxiv.org/html/2502.05176/x10.png)

> 🔼 그림 9는 제안된 방법이 기존의 SAM2 [44] 방법보다 각 뷰에 대해 더 정확한 예측을 생성하는지 보여줍니다. 수동으로 프롬프트를 제공할 필요 없이 깊이 왜곡을 통해 경계 상자 프롬프트를 자동으로 생성하여 SAM2 [44]가 더욱 정확한 예측을 생성할 수 있도록 합니다. 즉, 기존 방법은 수동으로 프롬프트를 지정해야 하지만, 본 논문에서 제시하는 방법은 깊이 왜곡 기법을 이용하여 경계 상자 프롬프트를 자동으로 생성함으로써 더욱 정확한 결과를 얻을 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Visual comparison of unseen mask generation method. Our method enables SAM2 [44] to generate more accurate predictions for each view without the need for manually provided prompts, as the bounding box prompts are automatically generated through depth warping.
> </details>



![](https://arxiv.org/html/2502.05176/x11.png)

> 🔼 그림 10은 제안된 방법과 Gaussian Grouping [65]의 Unseen Mask 생성 결과를 비교하여 보여줍니다. Gaussian Grouping은 비디오 추적기 [9]와 DEVA [9] 메서드의 '검은 흐릿한 구멍' 프롬프트를 사용하여 Unseen 영역을 추적하지만, 이는 추적 오류를 발생시켜 인페인팅 결과에 영향을 미칠 수 있습니다. 반면에, 제안된 기하 기반 접근 방식은 깊이 왜곡을 사용하여 Unseen 영역의 윤곽선을 추정하여 분할 오류를 줄입니다. 즉, Gaussian Grouping은 영상 기반 추적에 의존하여 Unseen 영역을 식별하는 반면, 본 논문의 방법은 기하학적 정보를 활용하여 더욱 정확하게 Unseen 영역을 식별합니다. 이는 복잡한 장면에서 특히 유용하며, 인페인팅 성능을 향상시킵니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Compared Unseen Mask w/ Gaussian Grouping. Gaussian Grouping [65] uses a video tracker [9] and the “black blurry hole” prompt for the DEVA [9] method to track the unseen region. However, this can result in tracking errors, affecting inpainting. In contrast, our geometry-based approach uses depth warping to estimate the unseen region’s contour, reducing segmentation errors.
> </details>



![](https://arxiv.org/html/2502.05176/x12.png)

> 🔼 그림 11은 다양한 방법으로 깊이 완성을 수행했을 때의 결과를 보여줍니다. 기존의 방법 (b, c)들과 비교했을 때, Infusion [27] (a)는 깊이 정렬에 있어 더 나은 성능을 보이지만 일반화에는 취약점을 보입니다. 마찬가지로, Guided Depth Diffusion [68] (d) 또한 배경 영역에서 손실이 증폭되어 정밀한 정렬을 달성하는 데 어려움을 겪습니다. 반면에, 본 논문에서 제안하는 AGDD (e)는 이러한 문제점들을 효과적으로 해결합니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Compared to other depth completion methods. The depth completion model in Infusion [27] (a) performs better at depth alignment compared to traditional methods (b) and (c), but it lacks generalization. Similarly, (d) Guided Depth Diffusion [68] struggles to achieve precise alignment, as the background regions amplify the loss, leading to misalignment. In contrast, (e) Our AGDD effectively addresses these issues.
> </details>



![](https://arxiv.org/html/2502.05176/x13.png)

> 🔼 그림 12는 깊이 왜곡 과정에서 생성된 중간 결과를 보여줍니다. (a)와 (b)는 각각 뷰 n의 RGB 이미지와 해당 제거 영역을 보여줍니다. (c)는 뷰 i(i≠n)에서 얻은 제거 영역을 보여줍니다. (d)는 역방향 추적을 통해 뷰 i에서 얻은 보이지 않는 영역을 보여줍니다. 교차점은 보이지 않는 영역 근처에 집중되어 있습니다. 보이지 않는 영역 내에 픽셀이 있지만 값이 0인 것은 해당 영역에 가우시안이 없기 때문이며, 이로 인해 깊이 렌더링이 불가능하고 따라서 뷰 n과 뷰 i 간의 픽셀 대응 관계를 설정할 수 없습니다. (e)는 뷰 i에서 뷰 n에서 얻은 모든 보이지 않는 영역의 집계를 보여줍니다. 이 결과에 임계값을 적용한 다음 뷰 n의 제거 영역과 교차시켜 (f)의 최종 결과를 얻습니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Intermediate Results of Depth Warping for Unseen Region Detection. This figure illustrates the intermediate results generated during the depth warping process. (a) and (b) show the RGB image and the corresponding removal region at view n𝑛nitalic_n, respectively. (c) displays the removal regions obtained from view i𝑖iitalic_i (i≠n𝑖𝑛i\neq nitalic_i ≠ italic_n). (d) shows the unseen region obtained from view i𝑖iitalic_i through backward traversal. The intersections are concentrated near the unseen region. Note that the pixels within the unseen region, but with a value of zero, are due to the absence of Gaussians in that area, preventing depth rendering and thus making it impossible to establish pixel correspondences between view n𝑛nitalic_n and view i𝑖iitalic_i. (e) presents the aggregation of all unseen regions obtained from view i𝑖iitalic_i at view n𝑛nitalic_n. A threshold is applied to this result, and it is then intersected with the removal region at view n𝑛nitalic_n to obtain the final result in (f).
> </details>



![](https://arxiv.org/html/2502.05176/x14.png)

> 🔼 그림 13은 제거 영역 정의에 대한 ablation 연구 결과를 보여줍니다. (a) 객체 마스크와 (b) 깊이 차이를 제거 영역을 정의하는 방법으로 비교합니다. 객체 마스크는 기하학적 변화를 포착하지 못하여 부정확한 보이지 않는 마스크로 이어집니다. 반면에 깊이 차이는 장면 구조를 더 잘 보존하여 SAM2 프롬프트와 보이지 않는 영역 분할을 개선합니다. 즉, 객체의 기하학적 모양 변화를 더 잘 반영하는 깊이 차이 정보를 사용하여 보이지 않는 영역 마스크를 생성하는 것이 더 정확하다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: Ablation Study on Removal Region Definition. Comparison of (a) object masks vs. (b) depth difference for defining removal regions. Object masks fail to capture geometric changes, leading to less accurate unseen masks. Depth difference better preserves scene structure, improving SAM2 prompts and unseen region segmentation.
> </details>



![](https://arxiv.org/html/2502.05176/x15.png)

> 🔼 그림 14는 3D 이미지 인페인팅의 어려움을 보여주는 실패 사례들을 보여줍니다. 특히, 인페인팅이 필요한 영역 근처에 상당한 폐색이 존재할 때 어려움이 발생합니다. (b)와 (c)는 기존 방법들이 훈련 뷰에서 만족스러운 RGB 이미지를 생성하는 데 어려움을 겪는 반면, (d)와 (e)는 잘못된 픽셀 투영으로 인한 오류를 보여줍니다. 이러한 관찰 결과는 비교된 방법들 중 어떤 것도 이 문제를 효과적으로 해결하지 못한다는 것을 시사하며, 추가적인 연구와 개선의 여지를 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: Failure Cases. The figure illustrates failure cases of inpainting results. These examples highlight the challenges of 3D inpainting when significant occlusions are present near the regions requiring inpainting. For instance, (b) and (c) demonstrate difficulties in achieving satisfactory guided inpainted RGB images in the training views, while (d) and (e) show errors resulting from incorrect pixel unprojections. These observations indicate that this issue is not effectively addressed by any of the compared methods, suggesting a potential avenue for further exploration and improvement.
> </details>



![](https://arxiv.org/html/2502.05176/x16.png)

> 🔼 그림 15는 논문에서 제시된 360-USID 데이터셋을 사용하여 다양한 360도 무제한 장면 인페인팅 방법들을 시각적으로 비교한 결과를 보여줍니다.  본 논문의 방법(Ours)을 포함하여,  2DGS + LeftRefill, Gaussian Grouping, Infusion 등 기존 방법들의 결과를  Ground Truth(GT)와 함께 제시하여, 각 방법들의 장점과 단점, 특히 여러 관점에서의 일관성 및 기하학적 정확성을 시각적으로 명확하게 비교하고 있습니다.  다양한 환경과 제거 대상 물체의 복잡도에 따른 각 방법의 성능 차이를 직관적으로 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 15: Visual Comparison on our 360-USID dataset.
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