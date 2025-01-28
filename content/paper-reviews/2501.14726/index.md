---
title: "Relightable Full-Body Gaussian Codec Avatars"
summary: "실시간 고품질 전신 아바타를 위한 새로운 재조명 및 애니메이션 기술 개발"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "3D Vision", "🏢 ETH Zurich",]
showSummary: true
date: 2025-01-24
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.14726 {{< /keyword >}}
{{< keyword icon="writer" >}} Shaofei Wang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-27 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.14726" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.14726" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/relightable-full-body-gaussian-codec-avatars" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 전신 아바타 모델들은 **사실적인 조명 효과 및 자연스러운 애니메이션**을 구현하는 데 어려움을 겪었습니다. 특히, **신체의 관절 운동**으로 인한 복잡한 광선 전달 효과를 정확하게 모델링하고 **다양한 조명 환경**에 적응하는 것이 어려웠습니다. 또한, **얼굴과 손**과 같이 세부적인 부분의 묘사가 부족한 경우가 많았습니다.

본 논문에서는 이러한 문제점들을 해결하기 위해 **Gaussian Codec Avatars**라는 새로운 아바타 모델을 제시합니다. **방향 의존적 확산 복사 전달과 지연 셰이딩 기반의 반사 복사 전달**을 결합하여 사실적인 조명 효과를 구현하고, **Zonal Harmonics**를 사용하여 관절 운동에 따른 광선 전달 변화를 효율적으로 모델링합니다.  또한, **전용 그림자 네트워크**를 통해 신체 부위 간의 그림자 효과를 정확하게 예측하여 더욱 사실적인 아바타를 생성합니다. 본 연구는 **전신 아바타의 재조명 및 애니메이션 기술**에 중요한 발전을 가져왔으며, 가상현실, 증강현실, 게임 등 다양한 분야에 활용될 수 있습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 학습된 방향 의존적 확산 복사 전달과 지연 셰이딩 기반의 반사 복사 전달을 결합하여 복잡한 광선 전달을 모델링 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 전신 아바타의 재조명 및 애니메이션을 위한 최초의 접근 방식 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 손과 얼굴을 포함한 세부적인 묘사와 다양한 조명 환경에 대한 일반화 성능 향상 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **전신 아바타의 재조명 및 애니메이션을 위한 새로운 접근법**을 제시하여, **실시간 렌더링 분야**와 **인공지능 기반 아바타 생성 연구**에 중요한 발전을 가져왔습니다.  **고품질의 실시간 아바타 생성**은 가상현실, 증강현실, 게임 등 다양한 분야에서 활용될 수 있으며, **본 논문의 방법론은 이러한 분야의 발전**에 크게 기여할 수 있습니다. 특히, **새로운 조명 환경에 대한 일반화 성능**을 높인 점과 **손과 얼굴을 포함한 세부적인 묘사**를 구현한 점은 높이 평가할 만합니다.  향후 연구에서는 본 논문의 방법론을 바탕으로 더욱 **사실적이고 효율적인 아바타 생성 기술** 개발 및 **다양한 애플리케이션**으로의 확장이 기대됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.14726/x1.png)

> 🔼 그림 1은 본 논문에서 제시하는 새로운 방법으로 생성한 '다시 조명 가능한 전신 Gaussian Codec 아바타'를 보여줍니다. 이 방법은 신체, 얼굴, 손을 포함한 전신 아바타의 재구성, 다시 조명, 표현력 있는 애니메이션을 가능하게 하는 최초의 접근 방식입니다.  방법은 학습된 방향 의존성 확산 복사 전달과 지연 셰이딩 기반의 반사 복사 전달을 결합하여 완전히 관절이 있는 인체에 대한 전역 조명과 같은 복잡한 광 전달을 가능하게 합니다. 그림에는 전신 아바타의 모습과, 얼굴, 손 부분의 클로즈업 이미지, 환경 맵을 이용한 다시 조명, 고유한 분해(법선, 확산, 반사), 애니메이션(보이지 않는 포즈/렌더링) 등의 결과가 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1. Relightable Full Body Gaussian Codec Avatars. We present the first approach that enables reconstruction, relighting and expressive animation of full-body avatars including body, face, and hands. Our approach combines learned, orientation-dependent diffuse radiance transport and deferred-shading-based specular radiance transport to enable complex light transport such as global illumination for fully articulated human bodies.
> </details>





{{< table-caption >}}
| Method | Training Motion PSNR ↑ | Training Motion SSIM ↑ | Training Motion LPIPS ↓ | Unseen Motion PSNR ↑ | Unseen Motion SSIM ↑ | Unseen Motion LPIPS ↓ |
|---|---|---|---|---|---|---|
| PBR | 28.35 | 0.7729 | 0.1993 | 26.83 | 0.7477 | 0.2166 |
| SH | 29.15 | 0.7958 | 0.1846 | 27.21 | 0.7679 | 0.2056 |
| w.o. shadow | 28.89 | 0.7991 | 0.1800 | 27.07 | 0.7707 | 0.2004 |
| w.o. deferred | 29.55 | 0.8047 | 0.1796 | 27.59 | 0.7755 | 0.2003 |
| Mesh normal | 29.43 | 0.8036 | 0.1785 | 27.53 | 0.7747 | 0.1993 |
| Ours | 29.48 | 0.8046 | 0.1781 | 27.57 | 0.7756 | 0.1989 |{{< /table-caption >}}

> 🔼 표 1은 제안된 방법과 기준 방법들의 정량적 비교 결과를 보여줍니다.  PSNR, SSIM, LPIPS 세 가지 지표를 사용하여 재조명 및 애니메이션 작업의 성능을 평가했습니다.  훈련 데이터셋과 시험 데이터셋에서의 결과를 모두 제시하고 있으며, 특히 제안된 방법(Ours)이 다른 방법들에 비해 월등히 높은 성능을 보임을 확인할 수 있습니다.  빨간색과 주황색으로 강조된 부분은 상위 두 가지 성능을 나타냅니다. 즉, 제안된 방법과 특정 기준 방법이 다른 방법들보다 더 나은 결과를 보였다는 것을 시각적으로 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 1. Quantitative comparison to baselines. The top two approaches are highlighted in red and orange, respectively.
> </details>





### In-depth insights


#### Zonal Harmonic
본 논문에서 제안하는 "구역 조화 함수(Zonal Harmonics)"는 **인체의 관절 운동에 따른 조명 변화를 효율적으로 모델링하기 위한 핵심 기술**입니다. 기존의 구면 조화 함수(Spherical Harmonics)는 회전에 대한 계산 비용이 높아 관절이 많은 인체 모델에 적용하기 어려웠던 반면, 구역 조화 함수는 **회전에 대한 계산 효율성이 뛰어나** 이러한 문제를 해결합니다.  **각 구역에서의 국소 좌표계를 기반으로 학습**하여 인체의 자세 변화에 따른 국소적인 조명 변화를 효과적으로 표현하며, **전체 모델의 파라미터 수를 줄여 계산량을 감소**시키는 효과도 있습니다.  이는 실시간 렌더링에 적합한 경량화된 모델 구축에 중요한 역할을 합니다.  **비국소적인 그림자 효과는 별도의 그림자 네트워크를 통해 처리**하여, 구역 조화 함수의 장점을 극대화하는 동시에 사실적인 조명 효과를 구현합니다. 따라서, 구역 조화 함수는 실시간으로 움직이는 인체 아바타의 재조명(relighting) 문제에 대한 효과적이고 효율적인 해결책을 제시한다고 볼 수 있습니다.

#### Shadow Network
본 논문에서 제시된 그림자 네트워크는 **관절의 움직임으로 인한 그림자**를 모델링하기 위한 핵심 요소입니다. 기존의 방법들이 복잡한 광선 추적을 사용하여 그림자를 계산하는 것과 달리, 이 네트워크는 **효율적인 학습 기반 접근 방식**을 통해 **정확하고 사실적인 그림자 효과**를 생성합니다.  **입력으로는 조잡한 메시(coarse-tracked mesh) 상의 정규화된 입사 조도(normalized incoming irradiance)**를 사용하며, 이는 신경망의 일반화 능력을 향상시키는 데 중요한 역할을 합니다. **학습된 그림자 네트워크는 신체 관절의 움직임에 따른 그림자 변화를 효과적으로 예측**하여, 전체적인 시각적 사실성을 높입니다.  이는 특히 신체 부위 간의 상호 작용으로 인해 발생하는 복잡한 그림자 영역을 처리하는 데 효과적이며, **실시간 렌더링 환경**에서도 효율적인 성능을 제공합니다.  **물리 기반의 조도 정규화 기법**을 통해 다양한 조명 조건에 대한 일반화 능력을 강화하는 것 또한 중요한 특징입니다. 이러한 그림자 네트워크는 **실시간으로 움직이는 전체 신체 아바타**의 사실적인 묘사를 가능하게 하는 핵심 기술이라 할 수 있습니다.

#### Deferred Shading
본 논문에서 제시된 지연 셰이딩(Deferred Shading) 기법은 **실시간 렌더링 환경에서 복잡한 광학 효과를 효율적으로 구현**하기 위해 고안되었습니다. 특히, **표면의 반사(specular) 특성을 정확하게 모델링**하는 데 초점을 맞추고 있는데, 이는 기존의 방법으로는 계산 비용이 많이 드는 작업입니다. **가우시안 스플래팅(Gaussian Splatting)**과 결합하여, 복잡한 기하 구조를 효율적으로 표현하면서도 **고품질의 반사 효과를 생성**합니다.  **지연 셰이딩 방식은 기하 정보와 재질 정보를 먼저 화면 공간(screen space)에 저장**하고, 이후 조명 계산을 수행함으로써 **렌더링 성능을 개선**합니다. 이는 **각 픽셀에 대해 여러 조명 계산을 반복적으로 수행하지 않아도 되기 때문**입니다.  **가우시안 기반의 표면 모델**과 결합하여 **고주파수의 세밀한 반사 효과까지도 효과적으로 표현**할 수 있다는 점이 특징입니다.  결과적으로, 본 논문의 지연 셰이딩 기법은 **실시간으로 고품질의 렌더링 결과를 생성**하는 데 크게 기여하며, **특히 실시간 애니메이션이나 가상현실(VR)과 같은 분야에서 유용성이 높을 것**으로 예상됩니다.

#### Full-Body Avatars
본 논문에서 다루는 "전신 아바타"는 **기존의 얼굴이나 상체 중심의 아바타 기술을 넘어 전신을 사실적으로 표현하고 조작 가능한 새로운 아바타 기술**을 의미합니다.  **신체, 얼굴, 손까지 포함하는 전체적인 모델링**을 통해 더욱 현실감 있는 가상 환경 구현 및 상호작용을 가능하게 합니다.  특히, **다양한 조명 환경에서도 실제와 같은 모습을 유지하는 재조명(relighting) 기능**은 몰입도 향상에 크게 기여하며, **자연스러운 애니메이션** 구현은 실시간 상호작용의 핵심 요소입니다.  하지만 이러한 전신 아바타는 **높은 계산 비용과 복잡한 모델링**이라는 기술적 어려움이 존재합니다.  본 논문은 이러한 문제를 해결하기 위해 **효율적인 표현 방식과 학습 기반의 조명 및 애니메이션 기술**을 제안하여 전신 아바타 기술의 발전에 기여하고 있습니다.

#### Future Work
본 논문은 전신 아바타의 재조명 및 애니메이션에 대한 새로운 접근 방식을 제시하지만, **여전히 개선의 여지가 있는 몇 가지 제한점**을 가지고 있습니다.  **향후 연구**는 다음과 같은 방향으로 진행될 수 있습니다. 첫째, 현재의 의류 동작 모델은 물리적 기반이 부족하여 비현실적인 움직임을 생성할 수 있습니다. 따라서 **물리 기반 의류 시뮬레이션 모델과의 통합**을 통해 더욱 사실적인 의류 움직임을 구현하는 연구가 필요합니다. 둘째, 눈, 얼굴, 손과 같은 세부 영역의 외관 표현은 전문화된 방법에 비해 다소 떨어집니다. 이를 개선하기 위해 **다이나믹한 UV 공간 용량 할당** 기법을 통해 학습 과정에서 신체 부위별로 세부 표현에 필요한 용량을 동적으로 조절하는 연구가 필요합니다. 셋째, 다중 카메라 설정과 알려진 광원을 필요로 하는 현재 시스템의 확장성을 개선하기 위해 **단일 카메라 또는 다양한 조명 조건 하에서도 작동하는 시스템**으로의 발전이 필요합니다.  마지막으로, 실시간 성능 향상을 위해서는 **더욱 효율적인 알고리즘 및 하드웨어 가속화 기술**을 적용해야 합니다. 이러한 연구들을 통해 더욱 현실적이고 실시간에 가까운 전신 아바타 재현이 가능해질 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.14726/x2.png)

> 🔼 그림 2는 본 논문에서 제안하는 방법의 개요를 보여줍니다. 키포인트 인코더에 의해 계산된 신체 잠재 코드(lb)와 얼굴 잠재 코드(lf) 그리고 정규화된 시야 방향(ωo)을 입력으로 받아, 3D 가우시안의 기하학적 매개변수(Rk, sk, tk, ok)와 광 전달 계수(zkc, zkm), 노말(nk), 거칠기(σk), 그리고 반사율(vk) 등의 외관 매개변수를 디코딩합니다. 확산 광 전달 계수를 사용하여 가우시안별 확산 색상을 생성하고, 지연 셰이딩을 사용하여 반사 색상을 계산합니다. 최종 색상은 그림자 네트워크에 의해 예측된 그림자 맵으로 변조됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 2.  Overview of our approach. Given a body latent code 𝐥bsubscript𝐥𝑏\mathbf{l}_{b}bold_l start_POSTSUBSCRIPT italic_b end_POSTSUBSCRIPT and a face latent code 𝐥fsubscript𝐥𝑓\mathbf{l}_{f}bold_l start_POSTSUBSCRIPT italic_f end_POSTSUBSCRIPT computed by a keypoint encoder and canonicalized viewing directions ω^osubscript^𝜔𝑜\hat{\mathbf{\omega}}_{o}over^ start_ARG italic_ω end_ARG start_POSTSUBSCRIPT italic_o end_POSTSUBSCRIPT as input, we decode the geometry parameters of 3D Gaussians {𝐑k,𝐬k,𝐭k,ok}subscript𝐑𝑘subscript𝐬𝑘subscript𝐭𝑘subscript𝑜𝑘\{\mathbf{R}_{k},\mathbf{s}_{k},\mathbf{t}_{k},o_{k}\}{ bold_R start_POSTSUBSCRIPT italic_k end_POSTSUBSCRIPT , bold_s start_POSTSUBSCRIPT italic_k end_POSTSUBSCRIPT , bold_t start_POSTSUBSCRIPT italic_k end_POSTSUBSCRIPT , italic_o start_POSTSUBSCRIPT italic_k end_POSTSUBSCRIPT } (Sec. 3.1), and appearance parameters consisting of light transport coefficients {𝐳kc,𝐳km}superscriptsubscript𝐳𝑘𝑐superscriptsubscript𝐳𝑘𝑚\{\mathbf{z}_{k}^{c},\mathbf{z}_{k}^{m}\}{ bold_z start_POSTSUBSCRIPT italic_k end_POSTSUBSCRIPT start_POSTSUPERSCRIPT italic_c end_POSTSUPERSCRIPT , bold_z start_POSTSUBSCRIPT italic_k end_POSTSUBSCRIPT start_POSTSUPERSCRIPT italic_m end_POSTSUPERSCRIPT }, normals {𝐧k}subscript𝐧𝑘\{\mathbf{n}_{k}\}{ bold_n start_POSTSUBSCRIPT italic_k end_POSTSUBSCRIPT }, roughness {σk}subscript𝜎𝑘\{\sigma_{k}\}{ italic_σ start_POSTSUBSCRIPT italic_k end_POSTSUBSCRIPT }, and specular visibility {vk}subscript𝑣𝑘\{v_{k}\}{ italic_v start_POSTSUBSCRIPT italic_k end_POSTSUBSCRIPT } (Sec. 3.2). We integrate the light with diffuse light transport coefficients to yield per-Gaussian diffuse color, while using deferred shading to compute specular color. The final color is modulated by a shadow map predicted by a shadow network (Sec. 3.3).
> </details>



![](https://arxiv.org/html/2501.14726/)

> 🔼 그림은 논문의 실험 결과를 보여줍니다. (a)는 기준(GT) 이미지이고, 나머지 이미지는 제시된 방법론을 사용하여 생성한 결과 이미지와 기존 방법론을 사용하여 생성한 결과 이미지를 비교한 것입니다.  본 그림은 논문의 다양한 방법론 및 그 성능을 시각적으로 보여주는 여러 하위 그림들로 구성되어 있습니다. 각 하위 그림은 다른 조명 조건이나 애니메이션 상태를 보여주며, 제안된 방법론의 우수성을 보여주고자 합니다.
> <details>
> <summary>read the caption</summary>
> (a) GT
> </details>



![](https://arxiv.org/html/2501.14726/)

> 🔼 그림은 논문의 실험 결과를 보여줍니다. (b) Ours는 제안된 방법을 사용하여 생성한 3D 아바타의 이미지를 보여주는 부분입니다.  이미지는 다양한 각도와 조명 환경에서 촬영되었으며, 제안된 방법이 얼굴, 손, 몸 전체에 걸쳐 사실적인 조명과 애니메이션을 생성하는 데 효과적임을 보여줍니다.  본 그림은 다양한 포즈와 조명에서도 고품질의 아바타를 생성할 수 있는 본 논문의 강점을 시각적으로 보여주는 중요한 부분입니다. 
> <details>
> <summary>read the caption</summary>
> (b) Ours
> </details>



![](https://arxiv.org/html/2501.14726/)

> 🔼 그림은 논문의 실험 결과를 보여줍니다. (c) PBR은 물리 기반 렌더링(Physically Based Rendering) 기법을 사용한 결과를 나타냅니다. PBR은 실제 물리적 현상을 기반으로 재질과 조명을 모델링하여 사실적인 이미지를 생성하는 기법입니다. 이 그림에서는 PBR 기반 방법으로 생성된 아바타의 외형을 보여주는 것으로 보이며, 다른 방법들과 비교하여 PBR의 장단점을 보여주는 데 활용될 것으로 예상됩니다.  자세한 내용은 논문의 관련 부분을 참고해야 합니다.
> <details>
> <summary>read the caption</summary>
> (c) PBR
> </details>



![](https://arxiv.org/html/2501.14726/)

> 🔼 이 그림은 논문에서 제시된 외관 모델과 기존의 물리 기반 렌더링(PBR) 모델을 비교한 것입니다. PBR 모델은 피부나 머리카락과 같은 반투명 물질의 표면 아래 산란 효과를 제대로 포착하지 못하고, 귀와 같이 오목한 부분에서는 전반적인 조명을 고려하지 않아 어둡게 표현되는 것을 보여줍니다. 제시된 모델은 이러한 문제점을 해결하여 더욱 사실적인 외관을 생성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3. Our appearance model vs. PBR appearance model. The PBR appearance model fails to capture subsurface scattering effects for skins and translucent structures such as hairs. It also produces a darker appearance for concave structures such as ears by omitting global illumination.
> </details>



![](https://arxiv.org/html/2501.14726/)

> 🔼 그림은 논문의 실험 결과를 보여줍니다. (a) GT는 기준(Ground Truth) 이미지이고, (b) Ours는 제안된 방법으로 생성한 이미지, (c) PBR은 기존의 물리 기반 렌더링(Physically Based Rendering) 방법을 사용한 결과입니다.  제안된 방법은 물리 기반 렌더링 방법보다 더 정확하고 사실적인 결과를 생성하며, 특히 피부의 미묘한 표현이나 머리카락 표현 등에서 차이가 큽니다.  GT와 비교했을 때, 제안된 방법은 사람의 얼굴과 몸의 모양과 색상, 질감을 더욱 정확하게 복원하고 있습니다.
> <details>
> <summary>read the caption</summary>
> (a) GT
> </details>



![](https://arxiv.org/html/2501.14726/)

> 🔼 그림은 논문의 실험 결과 중 하나로, 제안된 방법(ZH)을 사용한 렌더링 결과를 보여줍니다.  (a)는 기준(Ground Truth) 이미지, (b)는 제안된 방법으로 생성된 이미지, (c)는 비교 대상 방법(SH)의 결과입니다.  이 그림을 통해 제안된 방법이 기존 방법보다 더 정확하고 자연스러운 조명 효과를 생성함을 시각적으로 보여줍니다. 특히 그림 (b)는 더욱 사실적인 그림자와 반사광을 보여줍니다.  이는 제안된 방법이 더 나은 조명 전달 모델을 사용하기 때문입니다.
> <details>
> <summary>read the caption</summary>
> (b) Ours (ZH)
> </details>



![](https://arxiv.org/html/2501.14726/)

> 🔼 그림은 논문의 4.3절 실험 결과 부분에 포함되어 있으며, 확산 광 전달에 대한 구면 조화 함수(SH) 기반 방법의 한계를 보여줍니다. 그림 (a)는 실제 이미지, (b)는 제안된 방법(구역 조화 함수(ZH) 사용), (c)는 SH 기반 방법의 결과를 보여줍니다.  ZH 기반 방법은 SH 기반 방법에 비해 팔의 음영 처리가 더 정확하게 이루어짐을 보여줍니다. 이는 ZH가 관절이 있는 신체의 국소 좌표계에서 학습되어 관절 동작에 따른 국소 광 전달 변화를 보다 효율적으로 모델링하기 때문입니다.  SH 기반 방법은 광 전달 함수를 회전시키는 비용이 많이 들기 때문에, 관절 부위에서 정확한 음영을 표현하는 데 어려움을 겪습니다.
> <details>
> <summary>read the caption</summary>
> (c) SH
> </details>



![](https://arxiv.org/html/2501.14726/)

> 🔼 그림 4는 확산 광 전달에 대한 ZH(Zonal Harmonics)와 SH(Spherical Harmonics)의 비교 결과를 보여줍니다.  ZH는 관절이 있는 신체의 국소 좌표계에서 학습된 확산 광선 전달을 나타내는 반면, SH는 전역 좌표계에서 광선 전달을 모델링합니다. 그림에서 오른팔의 그림자가 SH 변형에서는 잘못 표현된 것을 확인할 수 있습니다.  이는 SH가 관절 동작으로 인한 국소적인 광선 전달 변화를 제대로 포착하지 못하기 때문입니다. ZH는 국소 좌표계를 사용하여 이러한 변화를 효율적으로 처리하여 더 정확한 그림자 표현을 가능하게 합니다.  즉, ZH 기반의 방법이  관절 동작으로 인한 그림자나 조명 변화를 더 정확하게 모델링함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4. ZH vs. SH for diffuse light transport. Note the incorrect shading on the right arm in the SH variant.
> </details>



![](https://arxiv.org/html/2501.14726/)

> 🔼 그림은 논문의 실험 결과를 보여줍니다. (a)는 실제 지상 진실(Ground Truth) 영상이고, 나머지 영상들은 제안된 방법과 비교 대상 방법들을 사용하여 생성한 결과 영상입니다. 각 열은 특정 조명 환경이나 포즈에서의 결과를 보여주며, GT와 비교하여 제안된 방법의 성능을 평가할 수 있습니다. 제안된 방법은 GT와 매우 유사한 결과를 생성하여, 정확하고 사실적인 결과를 얻을 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (a) GT
> </details>



![](https://arxiv.org/html/2501.14726/extracted/6154043/figures/Lighticon/Lighticon2.jpg)

> 🔼 그림은 논문의 그림 5의 (b) 부분을 보여줍니다. 그림 전체 제목은 '그림 5. 그림자 네트워크가 있는 우리 모델과 그림자 네트워크가 없는 우리 모델 비교' 입니다. 그림은 신체의 관절 부분에서 발생하는 그림자 효과를 나타냅니다. 왼쪽 열에는 실제 이미지(GT), 가운데 열에는 그림자 네트워크를 사용한 우리 모델의 결과, 오른쪽 열에는 그림자 네트워크를 사용하지 않은 우리 모델의 결과가 보여집니다. 그림자 네트워크가 있을 때 더 정확하고 사실적인 그림자 효과가 나타나는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) Ours (w. shadow)
> </details>



![](https://arxiv.org/html/2501.14726/)

> 🔼 그림은 본 논문에서 제안하는 방법론의 효과를 보여주는 비교 실험 결과 중 하나입니다.  (c) w.o. shadow는 그림의 (b) Ours와 대조되는 결과로, 그림 (b)에서는 제안된 방법론을 적용하여 몸의 관절 부분에 의한 그림자를 정확히 표현한 반면, (c) w.o. shadow에서는 그림자 처리 네트워크 없이 학습한 결과이므로 몸의 관절 부분 그림자가 제대로 표현되지 않음을 보여줍니다. 이는 몸의 관절이 움직임에 따라 생기는 비국소적인 그림자 효과를 정확히 모델링하기 위해 그림자 예측 네트워크가 중요함을 시사합니다. 즉, 본 그림은 신체 관절에 의한 그림자 효과 모델링에 대한 실험 결과를 보여주는 것입니다.
> <details>
> <summary>read the caption</summary>
> (c) w.o. shadow
> </details>



![](https://arxiv.org/html/2501.14726/)

> 🔼  그림 5는 본 논문에서 제안하는 그림자 네트워크의 정성적 결과를 보여줍니다. 그림자 네트워크 없이 학습된 라디언스 전달만으로는 신체 관절에 의한 그림자 효과를 충분히 포착할 수 없다는 것을 보여줍니다. 왼쪽 열은 기준 이미지(GT)를, 가운데 열은 그림자 네트워크를 사용한 결과를, 오른쪽 열은 그림자 네트워크를 사용하지 않은 결과를 보여줍니다. 신체의 움직임으로 인해 발생하는 그림자들이 그림자 네트워크를 사용했을 때 훨씬 더 정확하게 표현되는 것을 확인할 수 있습니다. 그림자 네트워크가 신체의 관절로 인해 발생하는 비국소적인 그림자 효과를 포착하는 데 중요한 역할을 수행함을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5. Qualitative results shadow networks. The learned light transport is not sufficient to capture the shadowing effects caused by body articulation without the help of the shadow network.
> </details>



![](https://arxiv.org/html/2501.14726/)

> 🔼 그림 6은 논문에서 사용된 다중 카메라 조명 스테이지의 모습을 보여줍니다. 돔 형태의 구조물 안에 512개의 카메라와 1024개의 개별적으로 제어 가능한 광원이 설치되어 있습니다. 돔의 반지름은 2.75미터이며, 각 카메라는 24메가픽셀 해상도를 가지고 초당 최대 90프레임의 비디오를 녹화할 수 있습니다. 이러한 설정은 다양한 조명 조건 하에서 고해상도의 움직임 데이터를 캡처하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 6. Capture Dome. Our multi-camera light stage with 512 cameras and 1024 controllable light sources. The dome has a radius of 2.752.752.752.75 meters. Each camera has 24 mega-pixels resolution and records video with up to 90Hz.
> </details>



![](https://arxiv.org/html/2501.14726/)

> 🔼 그림은 논문의 실험 결과를 보여줍니다. (a) GT는 Ground Truth를 의미하며, 실제 캡쳐된 이미지 데이터를 나타냅니다.  (b) Ours는 제안된 방법을 사용하여 생성한 이미지이고, (c) PBR은 기존의 물리 기반 렌더링 기법을 사용하여 생성한 이미지입니다. 세 이미지 모두 같은 자세와 조명 조건을 가지고 있으며, 제안된 방법의 성능을 시각적으로 비교하기 위한 것입니다.  제안된 방법은 물리 기반 렌더링보다 더 사실적이고 자세한 이미지를 생성하는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (a) GT
> </details>



![](https://arxiv.org/html/2501.14726/)

> 🔼 그림은 논문의 실험 결과 중 하나이며, 본 논문에서 제시하는 새로운 방법론 (Ours)을 사용하여 생성한 렌더링 결과를 보여줍니다.  특히, 'w. deferred'는 deferred shading 기법을 적용했음을 의미합니다.  deferred shading은 픽셀 단위의 깊이 정보를 활용하여 후처리 단계에서 광원과의 상호작용을 계산하는 방식으로,  더욱 사실적인 반사광 효과를 구현하는 데 유용합니다. 그림에서 비교 대상이 명시되어 있지 않아  (a)와 같은 다른 결과와 비교하여 deferred shading의 효과를 확인해야 합니다.  즉,  (a)와 비교 시 (b)에서 더욱 세밀하고 현실적인 반사광 표현이 가능함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) Ours (w. deferred)
> </details>



![](https://arxiv.org/html/2501.14726/)

> 🔼 이 그림은 본 논문에서 제시된 방법론의 차이점을 보여주는 비교 결과입니다. 구체적으로, (c) w.o. deferred는 그림의 왼쪽에서부터 순서대로 지연 셰이딩(deferred shading)을 적용하지 않은 결과를 보여줍니다.  지연 셰이딩은 픽셀 단위로 스크린 공간에서 광선 추적을 수행하여 표면 반사를 계산하는 기법입니다. 이 그림을 통해 지연 셰이딩을 적용했을 때와 적용하지 않았을 때의 차이점, 특히 반사광의 정확도 및 디테일의 차이를 비교 분석할 수 있습니다.  특히 눈 주변의 하이라이트가 지연셰이딩을 사용했을 때 훨씬 사실적임을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (c) w.o. deferred
> </details>



![](https://arxiv.org/html/2501.14726/x18.png)

> 🔼 그림 7은 지연 셰이딩(Deferred Shading)의 효과를 보여줍니다. 지연 셰이딩을 사용하지 않으면 눈의 반사광이 제대로 포착되지 않거나 흐릿하게 나타납니다. 즉, 지연 셰이딩은 정확하고 디테일한 반사광을 표현하는 데 중요한 역할을 합니다. 이는 특히 눈과 같이 작고 세밀한 부분의 반사광을 표현하는 데 효과적입니다. 지연 셰이딩 기법은 Gaussian Splatting 기반의 렌더링 방식에 적용되어, 가우시안 프리미티브의 스페큘러 특성을 효율적으로 처리하고, 더욱 사실적인 이미지를 생성하는 데 기여합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7. Deferred shading. Without deferred shading, the specular reflections in eyes are either not captured or blurred.
> </details>



![](https://arxiv.org/html/2501.14726/extracted/6154043/figures/relight/BOL681_face_envmap_frame_000001500_0.png)

> 🔼 그림은 논문의 실험 결과를 보여줍니다. (a)는 기준(Ground Truth) 이미지이고, (b)는 제안된 방법을 사용한 결과, (c)는 PBR(Physically Based Rendering) 방법을 사용한 결과입니다. 제안된 방법은 PBR 방법보다 더 사실적인 결과를 생성합니다. 특히, 피부의 반투명 효과와 머리카락의 투명도가 더 잘 표현됩니다.
> <details>
> <summary>read the caption</summary>
> (a) Reference
> </details>



![](https://arxiv.org/html/2501.14726/extracted/6154043/figures/relight/BOL681_full-body_pt-light_frame_000001500_0.png)

> 🔼 그림은 논문의 실험 결과를 보여줍니다. (b) Ours는 본 논문에서 제안하는 방법을 사용하여 생성한 결과 이미지를 나타냅니다. 이 이미지는 사람의 전신을 사실적으로 묘사하고 있으며, 조명 변화에 따라 자연스럽게 반응하는 모습을 보여줍니다. 특히, 머리카락이나 피부 등의 미세한 디테일까지 잘 표현되어 있습니다. 이를 통해 본 논문에서 제시하는 방법이 실제 사람의 모습을 매우 사실적으로 재현할 수 있음을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (b) Ours
> </details>



![](https://arxiv.org/html/2501.14726/extracted/6154043/figures/relight/BOL681_face_pt-light_frame_000001500_0.png)

> 🔼 그림은 본 논문의 실험 결과 중 하나로, 정규화된 표면 법선 벡터를 생성하는 방법에 대한 비교 결과를 보여줍니다. (c)는 메시(Mesh)의 표면 법선을 이용하여 정규화된 법선 벡터를 생성한 결과이며, 가우시안(Gaussian)의 회전 행렬의 마지막 열을 법선 벡터로 사용하는 방법과 비교됩니다. 메시 기반 법선 생성 방법은 가우시안 기반 방법보다 정확도가 떨어지는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (c) w. mesh normal
> </details>



![](https://arxiv.org/html/2501.14726/extracted/6154043/figures/relight/XJX084_full-body_envmap_frame_000003470_0.png)

> 🔼 그림 8은 Gaussian 회전을 specular normal과 연결했을 때 normal 추정의 질이 얼마나 향상되는지를 보여줍니다.  specular normal은 표면의 반사 특성을 결정하는 데 중요한 역할을 하며, 정확한 specular normal을 얻는 것은 사실적인 렌더링에 필수적입니다. 이 그림은  Gaussian 기반의 표면 모델링에서 Gaussian의 방향 정보를 활용하여 specular normal을 더욱 정확하게 예측할 수 있음을 시각적으로 보여줍니다.  결과적으로 더욱 사실적이고 디테일한 표면 반사를 얻을 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8. Normal representations. The quality of normal estimation is significantly improved if Gaussian rotations are associated with specular normals.
> </details>



![](https://arxiv.org/html/2501.14726/extracted/6154043/figures/relight/XJX084_face_envmap_frame_000003470_0.png)

> 🔼 그림 9는 본 논문에서 제시하는 방법을 사용하여 본 적이 없는 동작에 대해 재조명한 결과를 보여줍니다. 왼쪽 두 열은 환경 맵 기반 재조명을, 오른쪽 두 열은 점 광원 기반 재조명을 보여줍니다.  이를 통해 제시된 방법이 다양한 조명 조건과 동작에 대해서도 사실적인 재조명 결과를 생성할 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 9. Relighting result on unseen motion. We show environment-map-based relighting on the left two columns and point-light-based relighting on the right two columns.
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