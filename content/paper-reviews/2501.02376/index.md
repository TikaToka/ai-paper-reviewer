---
title: "Generalizable Origin Identification for Text-Guided Image-to-Image Diffusion Models"
summary: "텍스트 기반 이미지 생성 모델의 오용 방지! 새로운 원본 식별 방법과 데이터셋 OriPID로  **모델 일반화 문제 해결**"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Generation", "🏢 University of Technology Sydney",]
showSummary: true
date: 2025-01-04
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.02376 {{< /keyword >}}
{{< keyword icon="writer" >}} Wenhao Wang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-08 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.02376" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.02376" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/generalizable-origin-identification-for-text" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

최근 텍스트 기반 이미지-투-이미지 확산 모델이 허위 정보 유포, 저작권 침해, 콘텐츠 추적 회피 등에 악용되는 문제가 심각해지고 있습니다. 기존의 유사도 기반 접근 방식은 서로 다른 확산 모델에서 생성된 이미지 간의 시각적 차이로 인해 실제 응용에 어려움을 겪고 있습니다. 

본 논문에서는 이러한 문제를 해결하기 위해 **원본 이미지 식별(ID2)이라는 새로운 과제를 제시**하고, 다양한 확산 모델에서 생성된 이미지에 대해 **일반화 성능이 뛰어난 새로운 방법론을 제안**합니다. 이 방법론은 선형 변환을 이용하여 VAE 임베딩 간의 거리를 최소화하는 방식으로, 이론적으로 보장된 일반화 성능을 가지는 것이 특징입니다.  또한, **새로운 ID2 데이터셋 OriPID를 공개**하여, 다양한 확산 모델에 대한 일반화 성능을 평가하고 검증했습니다.  실험 결과, 제안된 방법론은 기존 방법론보다 훨씬 뛰어난 일반화 성능을 보였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 텍스트 기반 이미지-투-이미지 확산 모델의 원본 이미지 식별(ID2)이라는 새로운 과제 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 다양한 확산 모델에 일반화 가능한 원본 식별을 위한 새로운 방법론 제시 및 검증 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 일반화 성능 평가를 위한 최초의 ID2 데이터셋 OriPID 공개 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **텍스트 기반 이미지-투-이미지 확산 모델의 안전한 사용을 위한 새로운 기준을 제시**합니다.  이는 현재의 생성 AI 모델 오용 문제에 대한 효과적인 해결책을 제시하며, 관련 분야 연구의 새로운 방향을 제시할 수 있습니다. 특히, **일반화 가능한 원본 식별 방법론 제시**는 다양한 모델에 대한 적용성을 확보하여 실제 응용 가능성을 높였습니다. 또한, 제시된 데이터셋과 방법론은 향후 연구에서 벤치마크로 활용될 수 있어, **다른 연구자들의 후속 연구**에 큰 영향을 미칠 것입니다. 

------
#### Visual Insights



![](https://arxiv.org/html/2501.02376/x2.png)

> 🔼 본 그림은 텍스트 기반 이미지-이미지 확산 모델의 오용 사례를 보여줍니다. 세 가지 시나리오는 다음과 같습니다. (a) 도널드 트럼프 암살 후 사진을 조 바이든으로 편집한 허위 정보 유포, (b) 저작권이 있는 해변 사진에서 워터마크를 제거하고 수정하여 저작권 확인을 회피하는 행위, (c) 폭발 후 노르웨이 정부 건물 사진을 변경하여 불안정한 이미지 유포 제한을 우회하는 행위입니다. 각각의 시나리오는 이미지 조작을 통해 허위 정보 유포, 저작권 침해 및 콘텐츠 추적 회피가 가능함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: The illustration for misusing text-guided image-to-image diffusion models in several scenarios: misinformation, copyright infringement, and evading content tracing. Specifically: (a) An altered image originally showing Donald Trump post-assassination is edited to depict Joe Biden instead; (b) The removal of a watermark from a copyrighted beach image, followed by modifications, could assist in escaping copyright checks; (c) An image of a Norwegian government building after an explosion is altered to bypass restrictions, which limit the spread of disturbing images.
> </details>





{{< table-caption >}}
| Model | SDXL | OpenDalle | ColorfulXL | Kandinsky-3 | SD3 | Kolors |
|---|---|---|---|---|---|---|
| $cos(\varphi)$ | SDXL | OpenDalle | ColorfulXL | Kandinsky-3 | SD3 | Kolors |
| SD2 | 0.995790 ± 0.000037 | 0.996532 ± 0.000016 | 0.998436 ± 0.000015 | 0.999788 ± 0.000009 | 0.993256 ± 0.000035 | 0.991808 ± 0.000042 |{{< /table-caption >}}

> 🔼 표 1은 서로 다른 확산 모델들에 대해 Stable Diffusion 2를 비교 분석하여 얻은 cos(φ) 값을 보여줍니다. cos(φ)는 생성된 이미지와 원본 이미지 간의 VAE 임베딩 벡터 사이의 코사인 유사도를 나타냅니다. 실험의 신뢰성을 높이기 위해 각 모델에 대해 10회 반복 실험을 수행하여 평균과 표준편차를 계산했습니다. 이 표는 다양한 확산 모델에서 생성된 이미지들 간의 시각적 차이를 정량적으로 보여주는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 1: The c⁢o⁢s⁢(φ)𝑐𝑜𝑠𝜑cos\left(\varphi\right)italic_c italic_o italic_s ( italic_φ ) gained by compared Stable Diffusion 2 against different diffusion models. The experiments are repeated for ten times to calculate mean and standard deviation.
> </details>





### In-depth insights


#### ID2 Task Genesis
본 논문에서 제시된 "ID2 Task Genesis"는 텍스트 기반 이미지-투-이미지 확산 모델의 오용 문제를 해결하기 위한 핵심 개념입니다. **가짜 정보 유포, 저작권 침해, 콘텐츠 추적 회피** 등 악의적인 사용 사례를 방지하기 위해, 생성된 이미지의 원본 이미지를 식별하는 **ID2(Origin IDentification for text-guided Image-to-image Diffusion models) 과제**를 새롭게 정의합니다.  **ID2 과제의 핵심은 생성된 이미지와 그 원본 이미지 사이의 시각적 불일치 문제**를 해결하는 데 있습니다. 기존 유사도 기반 방법론의 한계를 극복하고, 다양한 확산 모델에 대한 일반화 성능을 확보하는 것이 중요합니다. 이를 위해 **일반화 성능을 강조한 OriPID 데이터셋 구축**과 이론적으로 보장된 새로운 방법론이 제안될 것입니다.  **선형 변환을 활용한 접근 방식**은 다양한 모델에서도 효과적으로 원본 이미지를 식별할 수 있음을 보여줍니다. 따라서 ID2 과제의 창시는 **이미지 생성 기술의 윤리적, 안전적 사용**을 위한 중요한 발걸음입니다.

#### OriPID Dataset
OriPID 데이터셋은 본 논문에서 제안하는 **오리진 식별(Origin Identification)** 과제를 위한 핵심 구성 요소입니다. **다양한 텍스트 기반 이미지-투-이미지 확산 모델에서 생성된 이미지들을 포함**하여 일반화 성능 평가에 중요한 역할을 합니다.  **풍부한 오리진 이미지와 이에 대응하는 다양한 프롬프트**를 제공하여, 모델의 일반화 능력을 측정하고 향상시키는 데 기여합니다.  데이터셋의 구성은 **실제 세계의 다양한 시나리오**를 반영하여 실용적인 응용에 적합하며, **여러 확산 모델의 이미지들을 포함**함으로써 모델의 일반화 성능을 효과적으로 평가할 수 있도록 설계되었습니다. 따라서 OriPID는 텍스트 기반 이미지-투-이미지 확산 모델의 안전성 및 신뢰성 향상에 기여하는 중요한 데이터셋입니다.

#### Linear Transform
선형 변환은 본 논문에서 제시된 **일반화 가능한 원본 식별 방법**의 핵심 구성 요소입니다.  **다양한 확산 모델에서 생성된 이미지 간의 시각적 차이**를 해결하기 위해, 논문에서는 원본 이미지와 변환된 이미지의 VAE 임베딩 간의 거리를 최소화하는 선형 변환 행렬 W의 존재를 증명합니다. 이는 **다양한 확산 모델에 대한 일반화 성능**을 보장하는 데 중요한 역할을 합니다.  **VAE 임베딩의 선형 변환**을 통해 모델 간의 시각적 불일치에도 불구하고,  일관된 특징 표현을 얻을 수 있게 되어 원본 이미지를 효과적으로 식별할 수 있습니다.  **이론적 보장과 실험적 결과**를 통해 선형 변환 기반의 방법이 우수한 일반화 성능을 달성함을 보여줍니다.

#### Generalizability
본 논문에서 다루는 "일반화 가능성(Generalizability)"은 제안된 방법이 **다양한 텍스트 기반 이미지-이미지 확산 모델에 적용될 수 있는지**를 평가하는 핵심 요소입니다.  단일 모델로 학습된 기존 방법들은 다른 모델에 적용하면 성능이 저하되는 한계를 보이는 반면, 본 연구에서는 **선형 변환을 통해 모델 간의 차이를 해소하고 일반화 성능을 크게 향상**시키는 것을 목표로 합니다. 이는 실제 응용 환경에서 다양한 모델들이 사용될 수 있다는 점을 고려할 때 매우 중요한 부분입니다. 실험 결과는 제안된 방법의 우수한 일반화 성능을 입증하며, **다양한 확산 모델에 대한 견고하고 효율적인 원본 식별을 가능하게** 한다는 점을 보여줍니다. 특히,  기존 유사도 기반 방법과 비교하여 상당한 성능 향상을 보임으로써, 제안된 방법의 실용성과 효과를 강조합니다.

#### Future Works
논문의 "향후 연구" 부분은 **이미지-텍스트 변환 모델의 일반화 가능성을 높이는 데 초점**을 맞춰야 합니다.  **CLIP 인코딩 기반의 새로운 일반화 방법론 개발**이 중요하며, 이는 다양한 모델과 텍스트-이미지 변환 방식에 대한 호환성을 높이는 데 기여할 것입니다. 또한,  **하드 네거티브 샘플 문제 해결을 위한 연구**는 모델의 정확도 향상에 필수적입니다.  **이미지 품질 저하에 대한 강건성 확보** 연구도 병행되어야 하며, 이는 다양한 이미지 변형 및 잡음에 대한 모델의 안정적인 성능을 보장하는 데 중요합니다.  **실제 적용 시나리오에 대한 실험 및 분석을 통해 모델의 실용성을 검증**하는 것도 중요한 향후 연구 과제입니다.  **다양한 모델과 인코딩 방식 간의 상호 작용에 대한 심도있는 연구**를 통해, 더욱 강력하고 일반화된 텍스트-이미지 변환 모델을 개발하는 데 기여할 수 있습니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.02376/x3.png)

> 🔼 그림 2는 다양한 텍스트-기반 이미지-투-이미지 확산 모델들이 생성한 이미지 간의 시각적 차이를 보여줍니다. 각 모델은 사실적인 질감, 복잡한 구조, 생생한 디테일, 선명한 색상, 추상적 표현, 마법 같은 분위기, 사실적인 요소 등 독특한 시각적 특징을 가진 이미지들을 생성합니다.  다양한 모델들이 생성한 이미지들을 비교하여 각 모델의 고유한 시각적 스타일을 명확히 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: The demonstration for visual discrepancy between generated images by different diffusion models. The images generated by various models exhibit distinctive visual features such as realistic textures, complex architectures, life-like details, vibrant colors, abstract expression, magical ambiance, and photorealistic elements.
> </details>



![](https://arxiv.org/html/2501.02376/x4.png)

> 🔼 그림 3은 논문에서 사용된 데이터셋 OriPID의 다양하고 포괄적인 이미지들을 보여줍니다.  데이터셋은 허위 정보 유포, 저작권 침해, 콘텐츠 추적 회피와 같은 실제 상황에서 발생할 수 있는 문제들을 다루기 위해, 자연, 건축물, 동물, 비행기, 예술 작품, 실내 장면 등 다양한 주제의 이미지들을 포함합니다. 간략하게 하기 위해 이미지 생성에 사용된 프롬프트는 생략했으며, 자세한 프롬프트와 생성된 이미지 예시는 보충 자료(8절)에서 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: The images in our dataset, which is diverse and comprehensive. Specifically, it encompasses a variety of subjects commonly found in real-world scenarios where issues such as misinformation, copyright infringement, and content tracing evasion occur. For instance, our dataset includes images of nature, architecture, animals, planes, art, and indoor. Note that for simplicity, we omit the prompts here. Please refer to Supplementary (Section 8) for examples of prompts and generations.
> </details>



![](https://arxiv.org/html/2501.02376/x5.png)

> 🔼 그림 4는 이론적으로 예상되는 변환 행렬 W를 학습하는 방법을 보여줍니다. 이론적으로는 W를 구하는 것이 가능하지만, 실제로는 경사하강법을 이용하여 메트릭 손실 함수를 최적화하여 W를 학습합니다. 구체적으로는 원본 이미지, 변환된 이미지, 그리고 네거티브 샘플 세 가지를 사용하여 메트릭 학습 손실 함수를 최소화하는 W를 찾습니다. 이를 통해 원본 이미지와 변환된 이미지 간의 특징 벡터 간의 거리를 최소화하고, 네거티브 샘플과의 거리는 최대화합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: The implementation of learning theoretical-expected matrix 𝐖𝐖\mathbf{W}bold_W. Specifically, in practice, we use gradient descent to optimize a metric loss function in order to learn 𝐖𝐖\mathbf{W}bold_W.
> </details>



![](https://arxiv.org/html/2501.02376/x6.png)

> 🔼 그림 5는 다양한 종류의 모델들에 대해 오류 사례를 보여줍니다. 구체적으로는, 지도학습 사전 훈련 모델, 자기 지도학습 모델, 비전-언어 모델, 그리고 이미지 복제 탐지 모델의 예시가 포함되어 있으며, 각 모델의 특징과 오류 원인을 시각적으로 보여줍니다. 이를 통해, 본 논문에서 제시하는 ID2 작업의 어려움과 과제를 더 잘 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Examples of failure cases for each kind of model.
> </details>



![](https://arxiv.org/html/2501.02376/x7.png)

> 🔼 그림 6은 다양한 유형과 강도의 공격에 대해 제안된 방법의 견고성을 보여줍니다. 구체적으로, 가우시안 블러와 JPEG 압축의 다양한 강도를 적용하여 모델의 강건성을 평가했습니다. 실험 결과, 이러한 공격의 부작용은 상대적으로 미미하여 제안된 방법의 효과가 입증되었습니다. 특히, 가시성이 떨어지는 공격에 대해서는 모델이 매우 강력했습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Our method demonstrates a certain level of robustness against different types and intensities of attacks.
> </details>



![](https://arxiv.org/html/2501.02376/x8.png)

> 🔼 그림 7은 본 논문의 이론적 근거대로, 에폭(epoch)이 증가함에 따라 코사인 유사도가 증가함을 보여주는 그래프입니다.  x축은 에폭, y축은 코사인 유사도를 나타내며, 서로 다른 조건(예: 가우시안 블러의 강도, JPEG 압축의 강도) 하에서 코사인 유사도의 변화를 보여줍니다. 이 그래프는 제시된 방법의 일반화 성능과 이론적 타당성을 시각적으로 확인시켜 줍니다.  특히, 'Seen' 데이터셋에서는 코사인 유사도가 빠르게 1에 수렴하는 반면, 'Unseen' 데이터셋에서는 수렴 속도가 다소 느리다는 점을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: As expected by the theory, the cosine similarities increase w.r.t. epochs.
> </details>



![](https://arxiv.org/html/2501.02376/x9.png)

> 🔼 이 표는 서로 다른 VAE(Variational Autoencoder) 인코더를 사용했을 때 모델 성능에 미치는 영향을 보여줍니다.  세 가지 다른 VAE 인코더(Open-Sora, Open-Sora-Plan, Stable Diffusion 2)를 사용하여 실험을 진행했고, 각 인코더에 대해 '본(Seen)' 데이터셋과 '보이지 않는(Unseen)' 데이터셋에서의 mAP(Mean Average Precision)와 정확도(Accuracy)를 측정했습니다. 이를 통해 VAE 인코더의 선택이 모델 성능에 미치는 영향을 정량적으로 분석하여, 모델의 일반화 성능에 대한 통찰력을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Ablation for choices of VAE encoders.
> </details>



![](https://arxiv.org/html/2501.02376/x10.png)

> 🔼 표 6은 서로 다른 지도 학습 손실 함수를 사용했을 때의 실험 결과를 보여줍니다. 세 가지 다른 지도 학습 손실 함수(SoftMax, Circle loss, CosFace)를 사용하여 모델을 학습시켰을 때의 성능을 비교 분석합니다. 각 손실 함수별로 'Seen'(학습 데이터셋에 있는 확산 모델에서 생성된 이미지)과 'Unseen'(학습 데이터셋에 없는 확산 모델에서 생성된 이미지) 두 가지 경우에 대한 평균 정밀도(mAP)와 정확도(Acc)를 나타냅니다. 이 표를 통해 어떤 지도 학습 손실 함수가 일반화 성능에 가장 효과적인지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Ablation for different supervision losses.
> </details>



![](https://arxiv.org/html/2501.02376/x11.png)

> 🔼 그림 8은 학습된 선형 변환 행렬 \(\mathbf{W}\)의 rank(계수의 개수)를 변화시켰을 때 성능 변화를 보여줍니다.  낮은 rank를 사용해도 성능 저하 없이 효율성을 높일 수 있음을 보여주는 실험 결과입니다. 구체적으로, rank를 4096에서 512로 줄여도 성능 변화가 거의 없지만, 512에서 64로 줄이면 성능이 저하됨을 알 수 있습니다. 이는 낮은 rank의 행렬은 원본 이미지와 변환된 이미지 간의 관계를 충분히 포착하지 못하기 때문입니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: The change in performance w.r.t the rank of 𝐖𝐖\mathbf{W}bold_W.
> </details>



![](https://arxiv.org/html/2501.02376/x12.png)

> 🔼 이 그림은 다양한 층 수를 가진 다층 퍼셉트론(MLP)을 사용하여 학습된 선형 변환 행렬 W의 성능 변화를 보여줍니다.  그래프는 '본(seen)' 데이터셋과 '보이지 않는(unseen)' 데이터셋에 대한 평균 평균 정밀도(mAP)와 정확도(Acc)를 층 수의 함수로 나타냅니다.  본 데이터셋은 안정적인 확산 모델 2(Stable Diffusion 2)로 생성된 이미지로 학습되었고, 보이지 않는 데이터셋은 다양한 확산 모델에서 생성된 이미지로 구성됩니다. 이 그림은 제안된 방법의 일반화 성능과 과적합에 대한 민감도를 보여주는 실험 결과를 시각적으로 보여줍니다.  특히, 층 수가 증가함에 따라 본 데이터셋의 성능이 향상되는 반면, 보이지 않는 데이터셋의 성능은 저하되는 현상을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: The change in performance w.r.t the number of layers.
> </details>



![](https://arxiv.org/html/2501.02376/x13.png)

> 🔼 그림 10은 본 논문의 정리(theorems)를 넘어서는 이미지 투 이미지 변환 패러다임을 보여줍니다.  본 논문에서 제시된 방법론은 VAE(Variational Autoencoder)를 사용하여 원본 이미지와 변환된 이미지의 임베딩 간의 거리를 최소화하는 선형 변환을 찾는 데 초점을 맞추고 있습니다. 하지만 그림 10에서 보여주는 InstructPix2Pix [2] 와 IP-Adapter [46] 와 같은 다른 방법론들은 다른 방식으로 이미지를 생성하고, 본 논문의 정리에서 다루는 범위를 벗어납니다.  InstructPix2Pix는 텍스트 안내에 따라 이미지를 생성하는 동안 VAE를 사용하지만,  IP-Adapter는 CLIP(Contrastive Language-Image Pre-training)을 사용하여 이미지를 임베딩합니다. 이러한 차이점은 본 논문의 정리에 기반한 방법론의 일반화 능력에 영향을 미칠 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: The image-to-image paradigm beyond our theorems.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
|| Method || Venue || mAP || Acc ||
|---|---|---|---|---|
| Supervised: Swin-B [23] || ICCV || 3.9 || 2.7 ||
| Pre-trained: ResNet-50 [12] || CVPR || 4.5 || 3.0 ||
| Models: ConvNeXt [24] || CVPR || 4.5 || 3.1 ||
|  EfficientNet [38] || ICML || 4.6 || 3.3 ||
|  ViT-B [8] || ICLR || 6.2 || 4.6 ||
| Self-supervised: SimSiam [6] || CVPR || 1.8 || 1.0 ||
| supervised: MoCov3 [13] || CVPR || 2.1 || 1.2 ||
| Learning: DINOv2 [27] || TMLR || 4.3 || 2.9 ||
| Models: MAE [14] || CVPR || 11.6 || 9.2 ||
|  SimCLR [5] || ICML || 11.3 || 9.7 ||
| Vision-language: CLIP [34] || ICML || 2.9 || 1.8 ||
|  SLIP [25] || ECCV || 5.4 || 3.7 ||
| Models: ZeroVL [7] || ECCV || 5.6 || 3.8 ||
|  BLIP [19] || ICML || 8.3 || 5.9 ||
| Image Copy: ASL [42] || AAAI || 5.2 || 4.1 ||
| Detection: CNNCL [47] || PMLR || 6.3 || 5.0 ||
| Models: BoT [41] || PMLR || 10.5 || 8.2 ||
|  AnyPattern [43] || Arxiv || 29.1 || 25.7 ||{{< /table-caption >}}
> 🔼 Table 2는 OriPID 테스트 세트에서 공개적으로 사용 가능한 여러 모델들이 성능이 저조함을 보여줍니다.  표는 다양한 종류의 사전 훈련된 모델들(지도 학습, 자기 지도 학습, 비전-언어 모델, 이미지 복제 탐지 모델)의 평균 평균 정밀도(mAP)와 정확도(Acc)를 보여줍니다.  이러한 모델들은 7가지 다른 확산 모델에서 생성된 이미지를 사용하여 평가되었으며, 모두 매우 낮은 성능을 기록했습니다. 이는 OriPID 데이터셋의 독특한 특징과 기존 모델의 일반화 능력 부족을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Publicly available models fail on the test set of OriPID.
> </details>

{{< table-caption >}}
|---|---|---|---|---|---|---|---| 
|   | Sim. | SDXL | OpDa | CoXL | Kan3 | SD3 | Kolor |
|---|---|---|---|---|---|---|---| 
|   | Conv. | 0.169 | 0.169 | 0.169 | 0.002 | - | 0.169 |
| <img src="https://arxiv.org/html/2501.02376/SD2.png" width="16.4pt" height="16.4pt" style="transform:rotate(-90deg)"> | Embed. | 0.120 | 0.121 | 0.120 | 0.023 | - | 0.120 |{{< /table-caption >}}
> 🔼 이 표는 서로 다른 확산 모델에서 생성된 이미지의 VAE(Variational Autoencoder) 임베딩 간의 차이를 보여줍니다.  'Seen'은 학습에 사용된 확산 모델이고, 'Unseen'은 테스트에 사용된 다른 확산 모델입니다.  표에서 각 모델의 VAE 인코더에 의해 추출된 임베딩 벡터의 유사성(Cosine Similarity)과 합성곱 층의 가중치 유사성을 비교하여,  다른 모델에서 생성된 이미지를 처리할 때 일반화 성능에 영향을 미치는 VAE의 차이를 보여줍니다.  즉,  같은 종류의 모델에서만 학습한 VAE는 다른 종류의 모델 이미지에는 잘 작동하지 않음을 보여주는 표입니다.
> <details>
> <summary>read the caption</summary>
> Table 3: VAE differs between seen and unseen diffusion models.
> </details>

{{< table-caption >}}
 | Method | Venue | Seen ↑ mAP | Seen ↑ Acc | Unseen ↑ mAP | Unseen ↑ Acc | Efficiency ↓ Train | Efficiency ↓ Extract | Efficiency ↓ Match | 
|---|---|---|---|---|---|---|---|---|
| Circle loss [37] | CVPR | 70.4 | 64.3 | 53.9 | 48.5 | 1.79 | 2.81 | 0.80 |
| SoftMax [18] | NC | 82.7 | 78.3 | 55.0 | 49.4 | 2.25 | 2.81 | 0.80 |
| CosFace [40] | CVPR | 87.1 | 83.2 | 52.2 | 46.5 | 2.43 | 2.81 | 0.80 |
| IBN-Net [28] | ECCV | 88.6 | 85.1 | 54.6 | 49.0 | 2.03 | 3.42 | 2.14 |
| TransMatcher [20] | NeurIPS | 65.6 | 60.3 | 65.3 | 60.7 | 1.84 | 2.30 | 0.941 |
| QAConv-GS [21] | CVPR | 78.8 | 74.9 | 75.8 | 72.3 | 1.47 | 2.30 | 0.464 |
| With Linear Transformation |  - | 88.8 | 86.6 | 86.6 | 84.5 | 0.17 | 1.59 | 0.53 |{{< /table-caption >}}
> 🔼 표 4는 제안된 방법이 효율성을 유지하면서 성능이 우수함을 보여줍니다.  'mAP'와 'Acc'는 백분율로 표시되며, 'Train', 'Extract', 'Match'는 각각 시간 단위(h), 이미지당 처리 시간(10⁻⁴초), 쌍당 매칭 시간(10⁻¹⁰초)을 나타냅니다.  이 표는 다양한 방법들의 훈련 시간, 특징 추출 시간, 매칭 시간 및 성능(mAP, Acc)을 비교하여 제안된 방법의 효율성과 성능을 보여줍니다.  기존 방법들과 비교하여 제안된 방법의 훈련 시간과 매칭 시간이 현저히 짧은 것을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Our method excels in performance while keeping efficiency. ‘mAP’ and ‘Acc’ are in percentage; ‘Train’, ‘Extract’, and ‘Match’ are in ‘h’, ‘10−4superscript10410^{-4}10 start_POSTSUPERSCRIPT - 4 end_POSTSUPERSCRIPT s/img’, and ‘10−10superscript101010^{-10}10 start_POSTSUPERSCRIPT - 10 end_POSTSUPERSCRIPT s/pair’, respectively.
> </details>

{{< table-caption >}}
|                       | Seen ↑ |          | Unseen ↑ |          |
|-----------------------|--------|----------|----------|----------|
| **VAE**                | mAP    | Acc      | mAP      | Acc      |
| Open-Sora              | 86.3   | 83.5     | 86.5     | 84.2     |
| Open-Sora-Plan         | 88.8   | 86.4     | 86.1     | 84.0     |
| **Stable Diffusion 2** | **88.8** | **86.6** | **86.6** | **84.5** |{{< /table-caption >}}
> 🔼 표 7은 널리 사용 가능한 7가지 다른 확산 모델(Stable Diffusion 2, Stable Diffusion XL, OpenDalle, ColorfulXL, Kandinsky-3, Stable Diffusion 3, Kolors)에 대해 사전 훈련된 모델, 자가 지도 학습 모델, 비전-언어 모델, 이미지 복제 감지 모델 등 다양한 공개적으로 사용 가능한 모델들의 성능을 보여줍니다. 각 모델의 평균 평균 정밀도(mAP)와 정확도(Acc)가 제시되어 있으며, 이를 통해 다양한 모델에서의 일반화 성능을 비교 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: The performance of publicly available models on 7 different diffusion models.
> </details>

{{< table-caption >}}
| Supervision | Seen ↑ |  | Unseen ↑ |  |
|---|---|---|---|---|
| SoftMax | 76.1 | 72.6 | 62.4 | 59.0 |
| Circle loss | 84.9 | 82.0 | 82.5 | 80.4 |
| CosFace | **88.8** | **86.6** | **86.6** | **84.5** |{{< /table-caption >}}
> 🔼 표 8은 논문에서 제안된 방법을 사용하여 훈련된 모델의 성능을 7가지 다른 확산 모델에 대해 평가한 결과를 보여줍니다. 이 표는 SD2(Stable Diffusion 2)로 생성된 이미지를 사용하여 훈련된 모델이 다양한 확산 모델에서 생성된 이미지에 대해 얼마나 잘 일반화되는지를 보여줍니다. 즉, 특정 확산 모델로 훈련된 모델이 다른 확산 모델에 대해서도 얼마나 효과적으로 작동하는지 평가합니다.  각 열은 특정 확산 모델을 나타내며, 각 행은 특정 모델 또는 방법을 나타냅니다. mAP(평균 정밀도)와 Acc(정확도)는 모델의 성능을 평가하는 지표입니다.
> <details>
> <summary>read the caption</summary>
> Table 8: The performance of our trained models on 7 different diffusion models. Note that these models are trained on images generated by SD2 and tested on images from multiple models.
> </details>

{{< table-caption >}}
Method | SD2 mAP | SD2 Acc | SDXL mAP | SDXL Acc | OpDa mAP | OpDa Acc | CoXL mAP | CoXL Acc | Kan3 mAP | Kan3 Acc | SD3 mAP | SD3 Acc | Kolor mAP | Kolor Acc
---|---|---|---|---|---|---|---|---|---|---|---|---|---|---
Swin-B | 3.1 | 2.0 | 2.9 | 1.9 | 4.1 | 2.9 | 4.2 | 3.1 | 6.8 | 4.7 | 2.9 | 1.9 | 3.0 | 2.0
ResNet-50 | 3.8 | 2.6 | 3.1 | 2.0 | 5.3 | 3.7 | 4.5 | 3.2 | 8.1 | 5.7 | 3.4 | 2.0 | 3.4 | 2.2
ConvNeXt | 3.5 | 2.1 | 3.3 | 2.2 | 4.7 | 3.3 | 5.0 | 3.5 | 8.4 | 6.2 | 3.5 | 2.4 | 3.6 | 2.6
EfficientNet | 2.9 | 1.9 | 2.9 | 2.0 | 4.9 | 3.4 | 5.4 | 3.9 | 8.7 | 6.5 | 3.3 | 2.2 | 4.1 | 3.0
ViT-B | 4.1 | 2.8 | 4.5 | 3.1 | 7.2 | 5.5 | 6.7 | 5.0 | 11.2 | 8.7 | 4.1 | 2.8 | 5.6 | 4.3
SimSiam | 1.5 | 1.0 | 1.2 | 0.7 | 1.8 | 0.9 | 1.7 | 1.0 | 3.1 | 1.9 | 1.5 | 0.8 | 1.4 | 0.8
MoCov3 | 1.4 | 0.8 | 1.5 | 0.9 | 2.4 | 1.3 | 2.2 | 1.3 | 3.8 | 2.4 | 1.9 | 1.1 | 1.6 | 1.0
DINOv2 | 2.6 | 1.6 | 2.7 | 1.7 | 4.6 | 3.0 | 5.5 | 3.6 | 8.4 | 5.9 | 2.9 | 1.9 | 3.6 | 2.6
MAE | 14.9 | 11.4 | 10.0 | 8.0 | 13.1 | 10.5 | 8.1 | 6.4 | 17.6 | 14.3 | 11.2 | 8.5 | 6.5 | 5.1
SimCLR | 6.0 | 4.2 | 7.0 | 5.2 | 13.5 | 10.6 | 13.0 | 10.1 | 23.7 | 19.3 | 7.3 | 12.0 | 8.8 | 6.7
CLIP | 2.6 | 1.7 | 2.1 | 1.4 | 3.1 | 2.1 | 3.2 | 2.0 | 4.2 | 2.7 | 2.5 | 1.6 | 2.1 | 0.7
SLIP | 5.6 | 3.8 | 3.5 | 2.3 | 5.8 | 4.0 | 4.9 | 3.3 | 9.1 | 6.7 | 5.4 | 3.5 | 3.8 | 2.5
ZeroVL | 5.2 | 3.5 | 4.4 | 2.9 | 6.4 | 4.4 | 4.5 | 3.2 | 9.8 | 6.9 | 4.7 | 3.0 | 4.3 | 3.0
BLIP | 6.8 | 4.8 | 6.5 | 4.5 | 9.9 | 7.0 | 8.7 | 6.3 | 13.8 | 10.2 | 6.0 | 3.9 | 6.4 | 4.5
ASL | 2.3 | 1.7 | 3.0 | 2.3 | 5.6 | 4.4 | 5.7 | 4.6 | 10.3 | 8.7 | 2.7 | 2.1 | 3.7 | 2.9
CNNCL | 4.0 | 2.9 | 4.2 | 3.2 | 8.3 | 6.7 | 5.7 | 4.5 | 12.2 | 9.9 | 3.7 | 2.7 | 6.3 | 5.0
BoT | 6.6 | 4.9 | 6.1 | 4.4 | 10.4 | 8.2 | 12.5 | 10.2 | 20.6 | 16.8 | 7.4 | 5.4 | 9.3 | 7.3
SSCD | 9.7 | 7.7 | 8.7 | 6.8 | 16.4 | 14.0 | 18.1 | 15.6 | 28.1 | 24.6 | 9.0 | 6.8 | 14.1 | 11.9
AnyPattern | 17.6 | 14.3 | 18.5 | 15.7 | 33.0 | 29.2 | 37.8 | 34.0 | 48.0 | 43.9 | 18.2 | 15.0 | 30.7 | 27.5{{< /table-caption >}}
> 🔼 표 9는 InstructPix2Pix [2]와 IP-Adapter [46]에 대한 일반화 결과를 보여줍니다.  이 표는 다양한 방법(유사도 기반 모델, 일반화 가능한 모델, VAE 임베딩 사용, 선형 변환 VAE 사용)을 사용하여 InstructPix2Pix와 IP-Adapter에서 생성된 이미지의 원본 이미지를 식별하는 성능을 비교합니다. 결과적으로 어떤 방법도 IP-Adapter에 대해서는 일반화에 성공하지 못했습니다.  이는 IP-Adapter가 다른 모델들과는 다른 방식으로 이미지 생성 작업을 수행하기 때문일 수 있습니다. 이 표는 제시된 방법들의 일반화 능력에 대한 한계를 보여주는 중요한 결과를 담고 있으며, 향후 연구 방향을 제시하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 9: The generalization results on InstructPix2Pix [2] and IP-Adapter [46]. No method succeeds in generalizing to IP-Adapter.
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
{{< /gallery >}}