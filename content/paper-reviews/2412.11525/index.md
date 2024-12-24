---
title: "Sequence Matters: Harnessing Video Models in 3D Super-Resolution"
summary: "비디오 초해상도 모델을 이용한 혁신적인 3D 초해상도 기법으로, 정렬 과정 없이도 최첨단 성능 달성!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "3D Vision", "🏢 Department of Electrical and Computer Engineering, Sungkyunkwan University",]
showSummary: true
date: 2024-12-16
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.11525 {{< /keyword >}}
{{< keyword icon="writer" >}} Hyun-kyu Ko et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-23 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.11525" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.11525" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/sequence-matters-harnessing-video-models-in" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

3D 초해상도는 저해상도의 다중 뷰 이미지로부터 고해상도 3D 모델을 생성하는 어려운 문제입니다. 기존의 단일 이미지 초해상도 기법은 각 이미지를 독립적으로 처리하기 때문에 뷰 사이의 일관성이 부족하고, 이를 해결하기 위한 후처리 기법은 계산 비용이 많이 들고 완벽한 해결책이 아닙니다.  본 논문에서는 이러한 문제를 해결하기 위해 비디오 초해상도(VSR) 모델을 활용하는 새로운 접근법을 제시합니다.

본 논문의 핵심 아이디어는 **VSR 모델의 우수한 공간적 일관성을 활용**하여 저해상도 이미지 시퀀스를 고해상도로 업스케일링하는 것입니다.  연구진은 간단하면서도 효과적인 이미지 정렬 알고리즘을 제안하여, VSR 모델의 미세 조정 없이도 표준 벤치마크 데이터셋에서 최첨단 성능을 달성했습니다. 특히, **VSR 모델이 정확한 공간적 정렬이 부족한 시퀀스에서도 우수한 성능을 보이는 점을 확인**하여, 실제 환경에서의 적용 가능성을 높였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 비디오 초해상도(VSR) 모델을 활용하여 저해상도 다중 뷰 이미지로부터 고해상도 3D 모델을 효율적으로 재구성하는 새로운 기법 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 정밀한 공간 정렬 없이도 VSR 모델이 높은 정확도를 유지하며, 기존 방식의 한계점인 뷰 일관성 부족 문제 해결 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} NeRF-synthetic 및 Mip-NeRF 360 데이터셋에서 최첨단 성능 달성 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **저해상도의 다중 뷰 이미지로부터 고해상도의 3D 모델을 재구성하는 3D 초해상도 문제**에 대한 새로운 접근법을 제시합니다. 기존의 단일 이미지 초해상도 기법의 한계를 극복하고, 비디오 초해상도 모델을 활용하여 **공간적 일관성을 높이고 계산 비용을 줄이는 효율적인 방법**을 제시함으로써, 3D 초해상도 분야의 발전에 크게 기여할 수 있습니다. 특히, **사전 훈련된 비디오 초해상도 모델을 활용**하여 추가적인 미세 조정 없이도 우수한 성능을 달성한 점은 매우 중요한 의미를 지닙니다. 이는 향후 **다양한 3D 모델링 및 시각화 연구**에 널리 활용될 가능성이 높습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.11525/extracted/6087365/figures/stripy_and_blob_artifacts.jpg)

> 🔼 이 그림은 3D Gaussian Splatting(3DGS)으로 렌더링된 저해상도(LR) 비디오의 VSR(Video Super-Resolution) 출력에서 발생하는 줄무늬 또는 얼룩과 같은 인공물을 보여줍니다. 'VSR-Render'는 LR 렌더링 비디오의 VSR 출력을 보여주는 반면, 'VSR-GT'는 실제(GT) LR 비디오의 VSR 출력을 보여줍니다.  즉, 3D 모델에서 생성된 LR 비디오와 실제 LR 비디오를 VSR 모델에 입력했을 때 출력 결과의 차이를 보여주는 것으로, 3DGS를 통해 생성된 비디오가 실제 비디오와 다르다는 것을 시각적으로 보여주는 중요한 그림입니다.  이는 VSR 모델의 성능에 부정적인 영향을 미치는 3DGS 렌더링 과정의 한계를 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Illustration of stripy or blob-like artifacts generated in VSR outputs of LR videos rendered from 3DGS. ‘VSR-Render’ shows the VSR outputs of the LR rendered videos, while ‘VSR-GT’ displays the VSR outputs of the ground truth (GT) LR videos.
> </details>





{{< table-caption >}}
| Index | L |  | R |  |
|---|---|---|---|---|
| | S | ALS | S | ALS |
| 1 | 34.06 | 37.18 | 34.53 | 35.52 |
| 2 | 33.12 | 34.33 | 34.67 | 36.63 |
| 3 | 32.90 | 33.37 | 31.62 | 34.26 |
| 4 | 33.47 | 34.41 | 33.68 | 34.29 |
| 5 | 34.07 | 35.68 | 32.77 | 35.31 |
| 6 | 32.65 | 34.41 | 32.05 | 32.77 |
| 7 | 32.71 | 33.43 | 32.68 | 34.66 |{{< /table-caption >}}

> 🔼 표 1은 제안된 정렬 알고리즘의 정량적 결과를 보여줍니다.  'S'는 단순 탐욕적 알고리즘을, 'ALS'는 적응적 길이 하위 시퀀스 알고리즘을 나타냅니다. 그림 4의 두 이미지 쌍에서 왼쪽 및 오른쪽 이미지의 PSNR 값을 각각 'L'과 'R'로 표시했습니다. 이 표는 제안된 두 가지 알고리즘(단순 탐욕적 알고리즘과 적응적 길이 하위 시퀀스 알고리즘)의 성능을 이미지 쌍별 PSNR 값을 통해 비교 분석한 결과를 보여줍니다.  각 알고리즘의 성능을 보다 명확하게 이해할 수 있도록 그림 4에 제시된 두 개의 이미지 쌍에 대한 왼쪽 및 오른쪽 이미지의 PSNR 값을 상세히 제시하고 있습니다. 이를 통해, 각 알고리즘이 이미지의 정렬에 따라 어떻게 다른 성능을 보이는지, 그리고 어떤 알고리즘이 더 나은 정렬 결과를 제공하는지를 정량적으로 비교 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: The quantitative results of the proposed ordering algorithms. S: the simple greedy algorithm, ALS: the adaptive-length subsequence. L and R denote the PSNR of the left and right image in two image pairs from Fig. 4.
> </details>





### In-depth insights


#### VSR in 3D Super-Res
본 논문에서 제안하는 VSR(Video Super-Resolution) 기반 3D 초고해상도 기법은 기존의 SISR(Single Image Super-Resolution) 방식의 한계를 극복하기 위한 시도입니다. **VSR 모델을 활용하여 다중 뷰 이미지 시퀀스의 공간적 일관성을 높임으로써 3D 모델 재구성의 정확도를 향상**시키는 것이 핵심입니다.  단순히 해상도만 높이는 것이 아니라, 시간적 정보를 활용하여 보다 정확하고 디테일한 3D 모델을 생성하는 데 초점을 맞추고 있습니다. **특히, LR(Low-Resolution) 이미지 시퀀스에서 발생할 수 있는 정렬 오류나 왜곡을 효과적으로 보정하기 위한 간단하지만 실용적인 알고리즘**을 제안하여 주목할 만합니다.  이는 고품질의 3D 모델 생성에 필수적인 정확한 공간적 정합을 확보하는 데 크게 기여할 것으로 예상됩니다.  **기존의 VSR 기법이 갖는 한계점을 극복하기 위해, 훈련 데이터의 구조화된 시퀀스 생성 방식을 제안**한 점도 돋보입니다.  이를 통해 VSR 모델의 성능을 최대화하고, 3D 초고해상도 작업에서 최첨단 결과를 달성할 수 있었습니다.

#### Greedy Ordering
본 논문에서 제안하는 '탐욕적 순서 정렬(Greedy Ordering)'은 비정렬된 다중 뷰 이미지들을 효율적으로 정렬하여 비디오와 유사한 시퀀스를 생성하는 알고리즘입니다. **단순하면서도 효과적**으로, 각 이미지의 이웃 이미지를 선택하여 시퀀스를 확장하는 방식을 취합니다.  **단순 탐욕적 접근 방식**은 연산량이 적다는 장점이 있지만, 최적의 순서를 보장하지는 못합니다.  이러한 한계를 극복하고자, **적응적 길이 하위 시퀀스(Adaptive-Length Subsequencing)** 기법을 추가적으로 제안합니다. 이 기법은 여러 개의 하위 시퀀스를 생성하여, 각 이미지가 최소한 하나의 시퀀스에 포함되도록 함으로써, 단일 탐욕적 접근 방식의 제한점을 보완합니다.  **카메라 자세 및 시각적 특징**을 활용한 유사도 측정 방식을 통해 이미지 간의 유사성을 평가합니다.  결론적으로, 탐욕적 순서 정렬은 비디오 초고해상도 모델의 성능 향상을 위해 비정렬 이미지들의 효과적인 시퀀스 생성이라는 중요한 역할을 수행하며, 단순성과 효율성을 갖춘 실용적인 방법임을 보여줍니다.

#### Artifact Mitigation
본 논문에서 다루는 핵심 개념 중 하나인 '아티팩트 완화'는 저해상도 이미지로부터 고해상도 3D 모델을 재구성하는 과정에서 발생하는 인공적인 왜곡이나 잡음을 줄이는 기술을 의미합니다. **특히, 저해상도 영상을 고해상도로 변환하는 과정에서 비디오 슈퍼해상도(VSR) 모델이 사용되는데, 이때 3D 모델 렌더링 과정에서 발생하는 줄무늬나 블롭과 같은 아티팩트가 VSR 모델 성능을 저해할 수 있습니다.** 이러한 문제를 해결하기 위해, 논문에서는 **3D 모델 렌더링 과정 자체의 개선이나 VSR 모델의 미세 조정 없이도, 훈련 데이터셋을 효과적으로 정렬하여 아티팩트를 줄이는 방법을 제안합니다.**  이는 **VSR 모델의 입력으로 사용되는 저해상도 이미지 시퀀스의 순서를 최적화함으로써, VSR 모델이 주변 정보를 더욱 효과적으로 활용하여 정확하고 상세한 3D 모델을 재구성하도록 유도하는 전략입니다.**  이를 위해 제안된 알고리즘은 간결하지만 효과적이며, 표준 벤치마크 데이터셋에서 최첨단 성능을 달성함으로써 그 효용성을 입증합니다.  **즉, 아티팩트 완화에 대한 핵심은 저해상도 영상 자체의 품질 향상이 아닌, VSR 모델의 입력 데이터를 최적화하여 3D 재구성 과정에서의 효율성을 높이는 데 있습니다.**  이러한 접근법은 계산 비용을 절감하고, 데이터셋에 대한 의존성을 줄이는 데 기여합니다.

#### Adaptive Subseq.
본 논문에서 제안하는 적응적 서브시퀀스(Adaptive Subseq.) 기법은 비정렬된 다중 뷰 이미지들을 효과적으로 정렬하여 비디오와 유사한 시퀀스를 생성하는 방법입니다. 기존의 단순 탐욕적 알고리즘(Simple Greedy Algorithm)의 한계를 극복하기 위해 **여러 임계값(Threshold)**을 사용하여 다양한 길이와 매끄러움을 가진 여러 개의 서브시퀀스를 생성합니다.  **높은 임계값**은 매끄러운 시퀀스를 생성하지만 짧은 시퀀스가 될 수 있으며, **낮은 임계값**은 긴 시퀀스를 생성하지만 매끄럽지 않을 수 있습니다.  이러한 문제를 해결하기 위해 적응적 서브시퀀스 기법은 여러 단계의 임계값을 사용하여, 가장 매끄러운 시퀀스를 우선 생성하고 이미지가 남아있으면 임계값을 낮춰 더 많은 이미지를 포함한 시퀀스를 만듭니다.  결과적으로, **다양한 특성의 이미지들**을 모두 효율적으로 활용하여 VSR 모델의 성능을 최적화하는 데 기여합니다. 이 기법은 **데이터셋의 다양한 특징**을 고려하여, 객체 중심 데이터셋과 장면 중심 데이터셋 모두에서 우수한 성능을 보여주는 유연성을 제공합니다.  **단순하면서 효과적인 접근 방식**으로 VSR 모델의 성능을 향상시키는 핵심 요소입니다.

#### Future of VSR
VSR의 미래는 **고해상도 비디오 생성의 정확성과 효율성을 향상시키는 데 중점을 둘 것**으로 예상됩니다.  이는 더욱 발전된 신경망 아키텍처, 특히 **더욱 효과적이고 효율적인 특징 추출 및 정렬 메커니즘**을 통해 가능해질 것입니다.  **대용량 고품질 데이터셋**의 등장 또한 VSR 모델의 성능 향상에 크게 기여할 것입니다.  **시간적 일관성 유지 및 다양한 비디오 유형에 대한 일반화 능력 향상** 또한 중요한 연구 분야가 될 것입니다.  결국, 미래의 VSR 기술은 **실시간 고품질 비디오 생성 및 처리**를 가능하게 하여, 방송, 영화 제작, 의료 영상 처리, 자율 주행 등 다양한 분야에서 혁신을 주도할 것으로 전망됩니다.  또한, **에너지 효율적인 모델 설계**에 대한 연구도 활발해져, 환경 문제에 대한 사회적 책임을 다하는 기술 발전이 이뤄질 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.11525/extracted/6087365/figures/main.jpg)

> 🔼 그림 2는 제안된 3D 슈퍼 해상도 기법의 개요를 보여줍니다. 먼저 저해상도(LR) 다중 뷰 이미지가 입력으로 주어집니다.  이 이미지들을 기반으로 단순 탐욕 알고리즘(Section 3.2)을 사용하여 각 이미지에서 시작하는 여러 개의 부분 수열(subsequence)을 생성합니다. 이 부분 수열들은 여러 임계값(threshold)으로 경계가 지정됩니다(Section 3.3). 이렇게 생성된 부분 수열들은 비디오 슈퍼 해상도(VSR) 모델을 통해 고해상도(HR) 이미지로 업스케일링됩니다.  마지막으로, 업스케일링된 HR 이미지들을 사용하여 3D 가우시안 스플래팅(3DGS) 모델을 학습시켜 3D 모델을 재구성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Overview of the proposed method. Given LR multi-view images, we generate subsequences (Sec. 3.3) starting from each image using a simple greedy algorithm (Sec. 3.2) and these subsequences are bounded by multiple thresholds (Sec. 3.3). Finally, we train a 3DGS model for 3D reconstruction using the upsampled HR images.
> </details>



![](https://arxiv.org/html/2412.11525/extracted/6087365/figures/subsequence.jpg)

> 🔼 그림 3은 제안된 방법의 핵심인 서브 시퀀스 생성 과정을 보여줍니다. (a)는 순서가 없는 다중 뷰 이미지 데이터셋을 나타냅니다. (b)는 간단한 탐욕 알고리즘(알고리즘 1)을 적용하여 이미지들을 순차적으로 배열한 결과입니다. (c)는 이 알고리즘으로 인해 발생하는 이미지 정렬 오류를 보여주며, 연속적인 프레임 간의 자세 차이 임계값(빨간 점선)을 기준으로 이미지 시퀀스를 여러 개의 서브 시퀀스로 나누는 것을 제안합니다. 이를 통해 VSR 모델의 성능 저하를 야기하는 정렬 오류를 줄이고, 보다 효과적인 3D 초고해상도 재구성을 가능하게 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Illustration of subsequence generation. (a) is an unordered multi-view image dataset. (b) is the result of using a simple greedy algorithm, Alg. 1. (c) highlights misalignments incurred by the algorithm, and we propose to split it into subsequences based on a pose difference threshold (red dotted line) between consecutive frames.
> </details>



![](https://arxiv.org/html/2412.11525/extracted/6087365/figures/lego_simple_greedy_algorithm.jpg)

> 🔼 그림 4는 간단한 탐욕 알고리즘을 NeRF 합성 데이터셋(Lego)에 적용한 결과의 예시입니다. 빨간색으로 강조된 두 개의 인접 이미지는 정렬 오류로 인해 발생하는 갑작스러운 전환을 보여줍니다. 이 그림은 간단한 탐욕 알고리즘이 이미지들을 순차적으로 나열할 때,  이미지 간의 시각적 유사성만을 고려하여 서로 관련 없는 이미지들을 연결하는 경우 발생할 수 있는 문제점을 보여줍니다.  즉,  정확한 공간적 정렬 없이 순차적으로 이미지들을 나열하는 경우,  결과물의 품질에 심각한 영향을 미칠 수 있음을 시각적으로 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: An example result from the simple greedy algorithm applied to the NeRF-synthetic dataset (Lego). Two neighboring images highlighted in red demonstrate abrupt transitions caused by misalignments.
> </details>



![](https://arxiv.org/html/2412.11525/extracted/6087365/figures/baseline_blender.jpg)

> 🔼 그림 5는 NeRF-synthetic 데이터셋에 대한 정성적 결과를 보여줍니다. 각 이미지 패치에는 GT(Ground Truth)에 대한 PSNR(Peak Signal-to-Noise Ratio) 값이 표시되어 있습니다. 제안된 방법은 기존의 기준 모델들보다 특히 고주파수 디테일에 대한 성능이 우수함을 보여줍니다.  이 그림은 제안된 방법이 더욱 선명하고 디테일한 이미지 재구성을 달성했음을 시각적으로 보여줍니다. 특히, 기존 방법들로는 재구성하기 어려운 미세한 디테일까지 잘 표현하고 있다는 점을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Qualitative results on the NeRF-synthetic dataset. The PSNR values against GT are embedded in each image patch. Ours have shown superior results than the existing baselines, especially for high-frequency details.
> </details>



![](https://arxiv.org/html/2412.11525/extracted/6087365/figures/baseline_mip360.jpg)

> 🔼 그림 6은 Mip-NeRF 360 데이터셋에 대한 정성적 결과를 보여줍니다. 각 이미지 패치에는 GT(Ground Truth)에 대한 PSNR 값이 표시되어 있습니다. 제안된 방법은 기존의 기준 모델들보다 특히 고주파수 디테일에서 우수한 결과를 보여줍니다.  이는 제안된 방법이 고해상도 이미지의 세부적인 부분까지도 잘 복원함을 의미합니다.  즉, 기존 방법들로는 복원이 어려웠던 미세한 부분까지도 선명하게 복원하여 더욱 사실적인 3D 모델을 생성할 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Qualitative results on Mip-NeRF 360 dataset. The PSNR values against GT are embedded in each image patch. Ours have shown superior results than the existing baselines, especially for high-frequency details.
> </details>



![](https://arxiv.org/html/2412.11525/extracted/6087365/figures/PSNR_LPIPS.jpg)

> 🔼 그림 7은 제안된 방법의 성능을 기존 최첨단 방법들과 비교 분석한 결과를 보여줍니다.  PSNR(Peak Signal-to-Noise Ratio)과 LPIPS(Learned Perceptual Image Patch Similarity) 지표를 사용하여 정량적으로 비교하였으며,  다양한 기존 방법들(NeRF-SR, ZS-SRT, CROP, FastSR-NeRF, DiSR-NeRF, SRGS, GaussianSR, SuperGaussian) 과 제안된 방법(Ours-S, Ours-ALS)의 성능 차이를 명확하게 보여줍니다.  이를 통해 제안된 방법이 기존 방법들에 비해 우수한 성능을 가짐을 시각적으로 확인할 수 있습니다. 특히, 제안된 방법의 두 가지 변형(Ours-S와 Ours-ALS) 모두 기존 최첨단 방법들보다 높은 PSNR 값과 낮은 LPIPS 값을 보이는 것을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Comparison with baselines.
> </details>



![](https://arxiv.org/html/2412.11525/extracted/6087365/figures/misalignment_trends_all_objects.jpg)

> 🔼 그림 8은 시퀀스 내에서 이미지 정렬 오류의 추세를 보여줍니다.  x축은 시퀀스 내 위치(0~100%), y축은 정렬 오류의 횟수를 나타냅니다.  각 선은 다른 물체에 대한 결과를 나타냅니다.  이 그래프는 그리디 알고리즘을 사용하여 시퀀스를 생성할 때 시퀀스의 후반부에서 정렬 오류가 증가하는 경향을 보여줍니다. 이는 그리디 알고리즘의 고유한 한계로 인해 발생하며, 긴 시퀀스에서는 연관성이 없는 특징들을 잘못 연결할 가능성이 높아지기 때문입니다.  이러한 정렬 오류는 VSR 모델의 성능을 저하시킵니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Misalignment trends within a sequence.
> </details>



![](https://arxiv.org/html/2412.11525/extracted/6087365/figures/misalignment.jpg)

> 🔼 그림 9는 순차적으로 정렬되지 않은 멀티뷰 이미지들을 비디오처럼 연결하는 과정에서 발생하는 정렬 오류를 보여줍니다. 특히 ORB 특징점을 이용하여 이미지들을 연결할 때, 연속적인 프레임들을 정확하게 연결하지 못하는 경우가 발생하며, 이러한 오류는 시퀀스의 길이가 길어질수록 증가하는 경향이 있습니다. 이 그림은 시퀀스의 마지막 25% 구간에 집중하여, 잘못 정렬된 프레임들을 시각적으로 보여주고, 이러한 정렬 오류가 3D 초해상도 결과에 미치는 영향을 설명합니다.  잘못 정렬된 프레임들이 많을수록 3D 재구성의 정확도가 떨어집니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Misalignment Error.
> </details>



![](https://arxiv.org/html/2412.11525/extracted/6087365/figures/appendix_qualitative_blender.jpg)

> 🔼 그림 10은 NeRF-synthetic 데이터셋에 대한 정량적 결과를 보여줍니다. 각 이미지 패치에는 GT(Ground Truth)에 대한 PSNR 값이 표시되어 있습니다. 제안된 방법은 특히 고주파수 디테일 측면에서 기존 기준 모델들보다 우수한 결과를 보여줍니다.  이 그림은 제안된 방법이 NeRF-synthetic 데이터셋에서 고해상도 이미지를 생성하는 데 있어 기존 방법들보다 성능이 뛰어나다는 것을 시각적으로 보여줍니다. 특히, 고주파수 성분(세부적인 디테일)을 더 잘 복원하여 더욱 사실적인 이미지를 생성하는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Qualitative results on the NeRF-synthetic dataset. The PSNR values against GT are embedded in each image patch. Ours have shown superior results than the existing baselines, especially for high-frequency details.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
|       | S     | ALS   |
| :---- | :---- | :---- |
| Chair | 32.11 | 32.74 |
| Drums | 29.74 | 30.26 |
| Ficus | 35.31 | 35.96 |
| Hotdog | 37.85 | 38.32 |
| Lego  | 33.30 | 34.73 |
| Materials | 35.24 | 35.85 |
| Mic   | 31.38 | 31.62 |
| Ship  | 30.03 | 30.48 |{{< /table-caption >}}
> 🔼 표 2는 논문에서 제안된 정렬 알고리즘의 성능을 NeRF 합성 데이터셋에서 비교 분석한 결과를 보여줍니다.  간단한 탐욕적 알고리즘(S)과 적응적 길이 하위 시퀀싱 알고리즘(ALS) 두 가지 방법의 PSNR 값을 다양한 물체(의자, 드럼, 무화과나무, 핫도그, 레고, 재료, 마이크, 배)에 대해 비교하여 각 알고리즘의 장단점과 개선 효과를 보여줍니다.  ALS 알고리즘이 전반적으로 더 높은 PSNR 값을 달성하여 향상된 성능을 보임을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: The comparison of the proposed ordering algorithms in the NeRF-synthetic dataset.
> </details>

{{< table-caption >}}
| Method | PSNR ↑ | SSIM ↑ | LPIPS ↓ |
|---|---|---|---| 
| Bicubic | 27.56 | 0.9150 | 0.1040 |
| SwinIR | 30.77 | 0.9501 | 0.0550 |
| Render-SR | 28.90 | 0.9346 | 0.0683 |
| NeRF-SR | 28.46 | 0.9210 | 0.0760 |
| ZS-SRT † | 29.69 | 0.9290 | 0.0690 |
| CROP † | 30.71 | 0.9459 | 0.0671 |
| FastSR-NeRF † | 30.47 | 0.9440 | 0.0750 |
| DiSR-NeRF | 26.00 | 0.8898 | 0.1226 |
| SRGS † | 30.83 | 0.9480 | 0.0560 |
| GaussianSR † | 28.37 | 0.9240 | 0.0870 |
| SuperGaussian † | 28.44 | 0.9459 | 0.0670 |
| Ours-ALS | **31.41** | **0.9520** | **0.0540** |
| 3DGS-HR | 33.31 | 0.9695 | 0.0303 |{{< /table-caption >}}
> 🔼 표 3은 Blender 데이터셋에서 다양한 3D 초고해상도화 기법들을 비교 분석한 결과를 보여줍니다.  가로 해상도를 4배에서 1배로 축소한(×4→×1) 저해상도 이미지를 사용하여 초고해상도 3D 모델을 생성하는 다양한 기법들의 성능을 비교합니다.  표에는 PSNR, SSIM, LPIPS 지표를 사용하여 정량적으로 평가한 결과가 제시되어 있습니다.  일부 기법의 경우, 코드가 공개되지 않아 논문에 제시된 수치를 가져왔음을 † 표시로 나타냅니다.  즉, 본 연구에서 직접 재현한 결과가 아닌 기존 논문의 결과를 인용한 것임을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Comparison of different methods for 3D super-resolution (×4→×1\times 4\rightarrow\times 1× 4 → × 1) in Blender Dataset. The numbers marked with † are sourced from their respective paper, as the code is not available at this time.
> </details>

{{< table-caption >}}
|       | VRT                               | IART                              | PSRT                              |
| :---- | :---------------------------------- | :--------------------------------- | :--------------------------------- |
| SISR  | PSNR ↑ 31.20, SSIM ↑ 0.9497, LPIPS ↓ 0.0567 | PSNR ↑ 31.10, SSIM ↑ 0.9484, LPIPS ↓ 0.0590 | PSNR ↑ 31.10, SSIM ↑ 0.9516, LPIPS ↓ 0.0543 |
| S     | PSNR ↑ 31.25, SSIM ↑ 0.9505, LPIPS ↓ 0.0557 | PSNR ↑ 31.32, SSIM ↑ 0.9513, LPIPS ↓ 0.0550 | PSNR ↑ 31.35, SSIM ↑ 0.9513, LPIPS ↓ 0.0548 |
| ALS   | PSNR ↑ 31.37, SSIM ↑ 0.9516, LPIPS ↓ 0.0544 | PSNR ↑ 31.35, SSIM ↑ 0.9514, LPIPS ↓ 0.0548 | PSNR ↑ 31.41, SSIM ↑ 0.9520, LPIPS ↓ 0.0540 |{{< /table-caption >}}
> 🔼 표 4는 다양한 VSR(Video Super-Resolution) 모델을 사용하여 Blender 데이터셋(해상도 4배 축소)에 대해 수행한 비교 실험 결과를 보여줍니다.  SISR(Single-Image Super-Resolution)은 단일 이미지에 VSR을 적용하는 방식이고, S는 단순 탐욕 알고리즘(순서: 특징)을 사용하여 이미지 순서를 정렬하는 방식이며, ALS는 다중 임계값을 사용하여 특징을 기반으로 적응적 길이 부분 시퀀스를 생성하는 방식입니다.  각 방식에 대한 PSNR, SSIM, LPIPS 값을 비교하여 성능을 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Ablation comparison of Blender dataset (×4→×1\times 4\rightarrow\times 1× 4 → × 1) on various VSR models. SISR refers to Single-Image Super-Resolution (single image VSR), S refers to ordering by simple greedy algorithm (order: feature), and ALS refers to using adaptive-length subsequence (order: feature) with multi-threshold (threshold: pose).
> </details>

{{< table-caption >}}
| Metric | PSNR ↑ | SSIM ↑ | LPIPS ↓ |
|---|---|---|---| 
| S (last 25%) | 31.32 | 0.9511 | 0.0552 |
| ALS | 31.41 | 0.9520 | 0.0540 |{{< /table-caption >}}
> 🔼 표 5는 정렬 오류가 3D 초고해상도 결과에 미치는 영향을 보여줍니다. 간단히 말해, 제안된 적응형 길이 하위 시퀀싱 알고리즘(ALS)을 사용하면 단순 탐욕적 알고리즘(S)보다 3D 초고해상도 결과가 더 향상됩니다. 특히,  시퀀스의 마지막 25%에서 정렬 오류가 발생할 가능성이 높은데, ALS는 이러한 오류에 덜 민감합니다. 이는 ALS가 이미지 시퀀스 내에서 일관성 있는 시각적 흐름을 더 잘 유지하기 때문입니다.  PSNR, SSIM, LPIPS 지표를 사용하여 정량적으로 비교 분석하였습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Impact of misalignment on 3D super-resolution.
> </details>

{{< table-caption >}}
|                     | chair | drums | ficus | hotdog | lego | materials | mic | ship | average |
|---------------------|-------|-------|-------|--------|------|-----------|-----|------|---------|
| Bicubic              | 29.02 | 23.75 | 28.24 | 31.86  | 27.46 | 26.47     | 27.97 | 25.71 | 27.56   |
| PSRT (SISR)          | 30.94 | 25.56 | 33.49 | 35.82  | 32.20 | 30.06     | 31.75 | 28.96 | 31.10   |
| SwinIR+3DGS         | 31.02 | 25.48 | 32.49 | 35.60  | 32.05 | 29.58     | 31.75 | 28.20 | 30.77   |
| Render-SR           | 30.23 | 24.04 | 28.63 | 33.78  | 29.23 | 27.34     | 30.53 | 27.35 | 28.90   |
| NeRF-SR              | 30.16 | 23.46 | 26.64 | 34.40  | 29.13 | 28.02     | 27.25 | 26.61 | 28.21   |
| DiSR-NeRF            | 27.55 | 22.63 | 25.64 | 30.07  | 26.43 | 24.71     | 26.49 | 24.47 | 26.00   |
| CROP<sup>†</sup>     | 31.53 | 24.99 | 31.50 | 35.62  | 32.88 | 29.16     | 31.76 | 28.23 | 30.71   |
| Ours-S               | 31.33 | 25.58 | 33.71 | 35.95  | 32.98 | 30.09     | 31.91 | 29.26 | 31.35   |
| Ours-ALS             | 31.36 | 25.65 | 33.69 | 36.18  | 33.03 | 30.17     | 31.93 | 29.26 | 31.41   |
| HR-3DGS             | 35.79 | 26.14 | 34.84 | 37.72  | 35.77 | 29.97     | 35.36 | 30.89 | 33.31   |{{< /table-caption >}}
> 🔼 표 6은 합성 Blender 데이터셋에서 개체별 PSNR 비교 결과를 보여줍니다. 입력 이미지의 해상도를 4배 축소한 후 (×4 → ×1), 다양한 방법으로 초해상도를 적용하여 생성된 3D 모델의 화질을 평가했습니다.  'Ours-ALS'는 제안된 적응적 길이 부분 시퀀스 기법을 사용한 결과를 나타냅니다.  각 개체(의자, 드럼, 무화과나무 등)에 대한 PSNR 값을 비교하여 제안된 방법의 성능을 다른 기존 방법들과 비교 분석했습니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Per-object PSNR comparison on the synthetic Blender dataset (×4absent4\times 4× 4 →→\rightarrow→ ×1absent1\times 1× 1). Ours-ALS refers to our method using adaptive-length subsequencing (ALS).
> </details>

{{< table-caption >}}
| Method | chair | drums | ficus | hotdog | lego | materials | mic | ship | average |
|---|---|---|---|---|---|---|---|---|---| 
| Bicubic | 0.9194 | 0.9003 | 0.9430 | 0.9526 | 0.9059 | 0.9220 | 0.9481 | 0.8291 | 0.9150 |
| PSRT (SISR) | 0.9475 | 0.9386 | 0.9762 | 0.9721 | 0.9572 | 0.9544 | 0.9732 | 0.8688 | 0.9516 |
| SwinIR+3DGS | 0.9469 | 0.9412 | 0.9760 | 0.9728 | 0.9601 | 0.9558 | 0.9747 | 0.8731 | 0.9501 |
| Render-SR | 0.9432 | 0.9163 | 0.9539 | 0.9677 | 0.9379 | 0.9322 | 0.9671 | 0.8582 | 0.9346 |
| NeRF-SR | 0.9366 | 0.9019 | 0.9026 | 0.9629 | 0.9292 | 0.9319 | 0.9432 | 0.8357 | 0.9180 |
| DiSR-NeRF | 0.9035 | 0.8618 | 0.9117 | 0.9332 | 0.8875 | 0.8816 | 0.9335 | 0.8053 | 0.8898 |
| CROP<sup>†</sup> | 0.9513 | 0.9236 | 0.9709 | 0.9725 | 0.9641 | 0.9468 | 0.9740 | 0.8637 | 0.9459 |
| Ours-S | 0.9538 | 0.9391 | 0.9779 | 0.9738 | 0.9646 | 0.9541 | 0.9747 | 0.8724 | 0.9513 |
| Ours-ALS | 0.9539 | 0.9405 | 0.9777 | 0.9744 | 0.9649 | 0.9555 | 0.9750 | 0.8741 | 0.9520 |
| HR-3DGS | 0.9874 | 0.9544 | 0.9872 | 0.9853 | 0.9828 | 0.9603 | 0.9914 | 0.9067 | 0.9694 |{{< /table-caption >}}
> 🔼 이 표는 합성 Blender 데이터셋에서 개체별 SSIM 비교 결과를 보여줍니다. 입력 저해상도 이미지를 4배 업샘플링(4x → 1x)한 결과를 보여주며, 제안된 방법인 적응적 길이 하위 시퀀싱(ALS)을 사용한 결과와 기준 모델들(Bicubic, PSRT (SISR), SwinIR+3DGS, Render-SR, NeRF-SR, DiSR-NeRF, CROP)의 결과를 비교합니다.  각 개체(의자, 드럼, 무화과나무, 핫도그, 레고, 재료, 마이크, 배)에 대한 SSIM 값을 제시하여 제안된 방법의 성능을 다각적으로 평가합니다.  HR-3DGS는 정답 고해상도 이미지를 사용한 3DGS 모델의 결과를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Per-object SSIM comparison on the synthetic Blender dataset (×4absent4\times 4× 4 →→\rightarrow→ ×1absent1\times 1× 1). Ours-ALS refers to our method using adaptive-length subsequencing (ALS).
> </details>

{{< table-caption >}}
|       | chair   | drums   | ficus   | hotdog  | lego    | materials | mic    | ship    | average |
| :---- | :------ | :------ | :------ | :------ | :------ | :-------- | :------ | :------ | :------- |
| Bicubic | 0.0899  | 0.1106  | 0.0619  | 0.0768  | 0.1272  | 0.0892    | 0.0626  | 0.2136  | 0.1040   |
| PSRT (SISR) | 0.0553  | 0.0609  | 0.0237  | 0.0421  | 0.0595  | 0.0480    | 0.0254  | 0.1567  | 0.0544   |
| SwinIR+3DGS | 0.0577  | 0.0565  | 0.0221  | 0.0401  | 0.0498  | 0.0420    | 0.0203  | 0.1511  | 0.0550   |
| Render-SR | 0.0563  | 0.0743  | 0.0396  | 0.0462  | 0.0691  | 0.0597    | 0.0312  | 0.1698  | 0.0683   |
| NeRF-SR  | 0.0687  | 0.1091  | 0.1014  | 0.0591  | 0.0976  | 0.0770    | 0.0805  | 0.1984  | 0.0990   |
| DiSR-NeRF | 0.0943  | 0.1429  | 0.0905  | 0.1001  | 0.1378  | 0.1293    | 0.0751  | 0.2106  | 0.1226   |
| CROP<sup>†</sup> | 0.0567  | 0.0856  | 0.0317  | 0.0481  | 0.0496  | 0.0622    | 0.0251  | 0.1776  | 0.0671   |
| Ours-S   | 0.0478  | 0.0585  | 0.0216  | 0.0395  | 0.0470  | 0.0488    | 0.0240  | 0.1509  | 0.0547   |
| Ours-ALS  | 0.0478  | 0.0576  | 0.0216  | 0.0388  | 0.0465  | 0.0464    | 0.0233  | 0.1501  | 0.0540   |
| HR-3DGS  | 0.0117  | 0.0371  | 0.0116  | 0.0199  | 0.0154  | 0.0341    | 0.0060  | 0.1063  | 0.0303   |{{< /table-caption >}}
> 🔼 표 8은 합성 Blender 데이터셋(4배 축소 → 1배)에서 개체별 LPIPS 비교 결과를 보여줍니다.  각 개체(의자, 드럼, 무화과나무, 핫도그, 레고, 재료, 마이크, 배)에 대해 여러 기준 모델(Bicubic, PSRT(SISR), SwinIR+3DGS, Render-SR, NeRF-SR, DiSR-NeRF, CROP, Ours-S, Ours-ALS, HR-3DGS)의 LPIPS 값을 비교하여 제시합니다. Ours-ALS는 본 논문에서 제안하는 적응형 길이 하위 시퀀싱(ALS) 기법을 사용한 방법을 나타냅니다. LPIPS 값이 낮을수록 이미지의 품질이 더 좋음을 의미합니다. 이 표를 통해 제안된 방법이 다른 기준 모델에 비해 LPIPS 값이 낮아, 이미지 품질이 우수함을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Per-object LPIPS comparison on the synthetic Blender dataset (×4absent4\times 4× 4 →→\rightarrow→ ×1absent1\times 1× 1). Ours-ALS refers to our method using adaptive-length subsequencing (ALS).
> </details>

{{< table-caption >}}
| Method | bicycle | flowers | garden | stump | treehill | room | counter | kitchen | bonsai | average |
|---|---|---|---|---|---|---|---|---|---|---|
| Bicubic | 24.02 | 21.24 | 25.14 | 26.30 | 22.25 | 30.47 | 28.15 | 28.23 | 30.21 | 26.22 |
| SwinIR + 3DGS | 24.54 | 21.18 | 25.81 | 26.38 | 22.16 | 31.30 | 28.71 | 29.82 | 31.26 | 26.80 |
| Ours-S | 24.42 | 21.13 | 26.04 | 26.40 | 22.26 | 31.47 | 28.96 | 30.79 | 31.69 | 27.02 |
| Ours-ALS | 24.50 | 21.17 | 25.99 | 26.46 | 22.26 | 31.52 | 28.90 | 30.73 | 31.68 | 27.02 |
| HR-3DGS | 24.41 | 20.59 | 26.58 | 26.28 | 22.27 | 31.52 | 29.12 | 31.57 | 32.36 | 27.19 |{{< /table-caption >}}
> 🔼 표 9는 Mip-NeRF 360 데이터셋에서의 8배 저해상도 이미지를 2배 고해상도 이미지로 초해상도 처리한 결과에 대한 각 장면별 PSNR(Peak Signal-to-Noise Ratio) 비교 결과를 보여줍니다.  저해상도 이미지에서 고해상도 이미지로의 변환 비율은 8배에서 2배입니다.  본 논문에서 제안하는 적응적 길이 하위 시퀀싱 (ALS) 방법을 사용한 결과('Ours-ALS')와 기타 기준 모델(Bicubic, SwinIR + 3DGS, Ours-S, HR-3DGS)의 성능을 비교하여 제안된 방법의 효과를 보여줍니다. 각 장면(bicycle, flowers, garden, stump, treehill, room, counter, kitchen, bonsai)에 대한 PSNR 값을 제시하며 평균 PSNR 값도 함께 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Per-scene PSNR comparison on the Mip-NeRF 360 dataset (×8absent8\times 8× 8 →→\rightarrow→×2absent2\times 2× 2). Ours-ALS refers to our method using adaptive-length subsequencing (ALS).
> </details>

{{< table-caption >}}
|               | bicycle | flowers | garden | stump | treehill | room | counter | kitchen | bonsai | average |
| :------------ | :------ | :------ | :------ | :------ | :------- | :---- | :------ | :------ | :----- | :------ |
| Bicubic       | 0.6401  | 0.5321  | 0.6648  | 0.7324  | 0.5880   | 0.8877 | 0.8573  | 0.8128  | 0.8980 | 0.7348  |
| SwinIR + 3DGS | 0.6810  | 0.5498  | 0.7259  | 0.7468  | 0.6020   | 0.9063 | 0.8837  | 0.8724  | 0.9235 | 0.7657  |
| Ours-S        | 0.6752  | 0.5512  | 0.7476  | 0.7481  | 0.6048   | 0.9123 | 0.8936  | 0.9071  | 0.9328 | 0.7747  |
| Ours-ALS      | 0.6783  | 0.5503  | 0.7462  | 0.7467  | 0.6028   | 0.9123 | 0.8918  | 0.9062  | 0.9323 | 0.7741  |
| HR-3DGS       | 0.7007  | 0.5445  | 0.8173  | 0.7571  | 0.6269   | 0.9263 | 0.9144  | 0.9325  | 0.9465 | 0.7962  |{{< /table-caption >}}
> 🔼 표 10은 Mip-NeRF 360 데이터셋에서의 8배 축소된 이미지를 2배로 초해상도 처리한 결과에 대한 장면별 구조 유사성 지표(SSIM) 비교를 보여줍니다.  각 장면(자전거, 꽃, 정원, 그루터기, 언덕, 방, 카운터, 주방, 분재)에 대한 SSIM 값을 보여주며, 제안된 방법(Ours-ALS)을 포함한 다양한 기준 모델들(Bicubic, SwinIR + 3DGS, Ours-S, HR-3DGS)과 비교 분석합니다. Ours-ALS는 제안된 적응형 길이 하위 시퀀스 기법을 사용한 결과를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Per-scene SSIM comparison on the Mip-NeRF 360 dataset (×8absent8\times 8× 8 →→\rightarrow→×2absent2\times 2× 2). Ours-ALS refers to our method using adaptive-length subsequencing (ALS).
> </details>

{{< table-caption >}}
|               | bicycle | flowers | garden | stump | treehill | room | counter | kitchen | bonsai | average |
| :------------ | :------: | :------: | :------: | :------: | :-------: | :----: | :------: | :------: | :------: | :------: |
| Bicubic       |  0.3688  |  0.4315  |  0.3469  |  0.3334  |   0.4391  | 0.2750 |  0.2671  |  0.2598  |  0.2392  |  0.3290  |
| SwinIR + 3DGS |  0.3220  |  0.4065  |  0.2784  |  0.3098  |   0.4116  | 0.2354 |  0.2216  |  0.1973  |  0.2035  |  0.2873  |
| Ours-S        |  0.3344  |  0.4091  |  0.2613  |  0.3142  |   0.4162  | 0.2218 |  0.2074  |  0.1536  |  0.1927  |  0.2790  |
| Ours-ALS      |  0.3261  |  0.4062  |  0.2607  |  0.3117  |   0.4134  | 0.2218 |  0.2104  |  0.1542  |  0.1925  |  0.2774  |
| HR-3DGS       |  0.3230  |  0.4188  |  0.1777  |  0.3130  |   0.3997  | 0.1931 |  0.1800  |  0.1136  |  0.1758  |  0.2550  |{{< /table-caption >}}
> 🔼 표 11은 Mip-NeRF 360 데이터셋에서의 8배 저해상도에서 2배 고해상도로의 슈퍼 해상도 결과에 대한 LPIPS(Learned Perceptual Image Patch Similarity) 비교 결과를 보여줍니다.  LPIPS는 이미지의 지각적 유사성을 측정하는 지표로, 낮을수록 더 높은 유사성을 의미합니다. 이 표는 제안된 방법(Ours-ALS)을 포함한 여러 비교 대상 방법들에 대한 각 장면별 LPIPS 값을 제시합니다. Ours-ALS는 본 논문에서 제안된 적응적 길이 하위 시퀀스 기법을 사용한 방법입니다.  표를 통해 각 방법의 주관적인 이미지 품질 차이를 수치적으로 비교 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 11: Per-scene LPIPS comparison on the Mip-NeRF 360 dataset (×8absent8\times 8× 8 →→\rightarrow→×2absent2\times 2× 2). Ours-ALS refers to our method using adaptive-length subsequencing (ALS).
> </details>

{{< table-caption >}}
| Method | PSNR ↑ | SSIM ↑ | LPIPS ↓ |
|---|---|---|---| 
| Bicubic | 26.22 | 0.7349 | 0.3290 |
| SwinIR | 26.80 | 0.7657 | 0.2873 |
| SRGS<sup>†</sup> | 26.88 | 0.7670 | 0.2860 |
| Ours | **27.02** | **0.7747** | **0.2790** |
| 3DGS-HR | 27.19 | 0.7710 | 0.2802 |{{< /table-caption >}}
> 🔼 표 12는 Mip-NeRF 360 데이터셋에서 8배 다운샘플링된 이미지를 2배로 업샘플링하는 다양한 기준 모델들과 제안된 방법의 성능 비교 결과를 보여줍니다.  PSNR, SSIM, LPIPS 세 가지 지표를 사용하여 정량적으로 비교 분석하였습니다.  이 표는 제안된 방법의 성능 우수성을 보여주는 실험 결과의 일부분입니다.
> <details>
> <summary>read the caption</summary>
> Table 12: Comparison with baseline models in Mip-NeRF 360 dataset (×8absent8\times 8× 8 →→\rightarrow→ ×2absent2\times 2× 2).
> </details>

{{< table-caption >}}
| Method | FVD↓ | PSNR↑ |
|---|---|---|
| Bicubic | 195 | 27.56 |
| SwinIR | 113 | 30.77 |
| Render-SR | 134 | 28.90 |
| NeRF-SR | 169 | 28.21 |
| DiSR-NeRF | 304 | 26.00 |
| Ours-S | 110 | 31.35 |
| Ours-ALS | **109** | **31.41** |{{< /table-caption >}}
> 🔼 표 13은 Blender 데이터셋에서 제안된 방법의 시간적 일관성 및 공간적 화질 지표를 보여줍니다.  시간적 일관성은 비디오 프레임 간의 부드러운 전환을 나타내는 반면, 공간적 화질은 재구성된 3D 모델의 시각적 선명도를 나타냅니다.  다양한 기준 모델(Bicubic, SwinIR, Render-SR, NeRF-SR, DiSR-NeRF, Ours-S, Ours-ALS)과의 비교를 통해 제안된 방법의 우수성을 보여줍니다. 특히, Ours-ALS는 FVD(Fréchet Video Distance) 지표에서 가장 낮은 값을 기록하여, 시간적 일관성이 가장 뛰어남을 보여줍니다. PSNR(Peak Signal-to-Noise Ratio) 지표 또한 높은 값을 나타내어, 공간적 화질 또한 우수함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 13: Temporal Consistency and Spatial Quality Metrics on Blender Dataset.
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