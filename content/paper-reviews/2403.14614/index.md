---
title: "AdaIR: Adaptive All-in-One Image Restoration via Frequency Mining and Modulation"
summary: "AdaIR: 주파수 분석 기반 적응형 올인원 이미지 복원 네트워크"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Restoration", "🏢 Technical University of Munich",]
showSummary: true
date: 2024-03-21
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2403.14614 {{< /keyword >}}
{{< keyword icon="writer" >}} Yuning Cui et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-27 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2403.14614" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2403.14614" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/adair-adaptive-all-in-one-image-restoration" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

많은 이미지 복원 알고리즘들이 특정 저하 유형에만 초점을 맞추는 반면, 최근에는 여러 유형의 저하를 한 번에 처리하는 '올인원' 알고리즘이 주목받고 있습니다. 하지만 기존 올인원 알고리즘들은 공간 영역에서만 동작하여, 서로 다른 저하 유형의 고유한 주파수 특징을 충분히 활용하지 못하는 한계가 있었습니다.

본 논문에서는 이러한 문제를 해결하기 위해 **주파수 영역 정보를 적극적으로 활용하는 새로운 올인원 이미지 복원 네트워크인 AdaIR**을 제안합니다. AdaIR은 이미지의 주파수 특징을 분석하고, 저하 유형에 따라 적응적으로 주파수 대역을 조정하여 이미지를 복원합니다.  실험 결과, AdaIR은 다양한 이미지 복원 작업에서 기존 최고 성능을 뛰어넘는 결과를 보였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 다양한 이미지 품질 저하(잡음, 흐림, 안개, 비 등) 문제를 단일 모델로 해결하는 새로운 접근 방식 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 주파수 영역 분석을 통해 이미지 저하 유형에 따라 적응적으로 복원하는 Adaptive Frequency Learning Block (AFLB) 제안 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 다양한 이미지 복원 작업(잡음 제거, 안개 제거, 비 제거, 움직임 흐림 제거, 저조도 이미지 향상)에서 최첨단 성능 달성 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **다양한 이미지 품질 저하 문제를 하나의 모델로 해결**하는 새로운 방법을 제시하여, **연구자들이 효율적이고 일반화된 이미지 복원 모델을 개발**하는 데 중요한 의미를 가집니다.  **주파수 영역 분석을 기반으로 이미지 저하 유형에 따라 적응적으로 복원**하는 접근 방식은 기존의 방법들보다 우수한 성능을 보이며, **향후 이미지 처리 및 컴퓨터 비전 분야의 발전**에 크게 기여할 것으로 예상됩니다. 이 연구는 **다양한 이미지 저하 유형에 대한 통합적인 해결책**을 제시함으로써, **실시간 이미지 처리 시스템 개발 및 실제 응용 분야 확장**에도 중요한 영향을 미칠 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2403.14614/x11.png)

> 🔼 그림 1은 다양한 이미지 복원 작업(저조도 이미지 향상, 디헤이징, 디레이닝, 모션 흐림 제거, 잡음 제거)에 대한 샘플 이미지들을 보여줍니다. 왼쪽에는 각 작업에 대한 저화질 이미지, 정답 이미지, 그리고 저화질 이미지에서 정답 이미지를 뺀 잔차 이미지의 푸리에 스펙트럼이 위에서부터 아래로 순서대로 나열되어 있습니다. 이미지들은 각각 LOL-v1, SOTS, Rain100L, GoPro, BSD68 데이터셋에서 가져왔습니다. 오른쪽 그래프는 다섯 가지 작업에 걸쳐 푸리에 스펙트럼의 평균값을 x축에 표시된 길이의 제곱에 대해 나타냅니다. 모든 스펙트럼은 비교를 위해 320x320 크기로 조정되었습니다. 그래프를 통해 서로 다른 작업들이 서로 다른 주파수 대역에 대해 다른 정도로 주의를 기울인다는 것을 알 수 있습니다. 예를 들어, 저조도 이미지 향상 및 디헤이징 데이터셋의 경우 저화질 이미지와 정답 이미지 간 저주파수 영역에서 차이가 더 큽니다. 반면, 잡음 제거의 경우 주파수 차이는 전반적으로 고르게 분포되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Left, from top to bottom: degraded images, ground-truth images, and the Fourier spectra of residual images obtained by subtracting the degraded images from the ground-truth images. The images are obtained from LOL-v1 [64], SOTS [32], Rain100L [32], GoPro [44], and BSD68 [41], respectively. Right, the sub-graph illustrates the mean values of Fourier spectra on the square of length shown on the x-axis, across five tasks. The spectra are all resized to 320×320320320320\times 320320 × 320 for comparisons. As seen, different tasks pay different attention to different frequency subbands. For example, there are larger discrepancies in low frequency between degraded and target image pairs of the low-light image enhancement and dehazing datasets. In contrast, the frequency differences are generally evenly distributed for image denoising.
> </details>





{{< table-caption >}}
| Low-Light | Dehazing | Deraining | Deblurring | Denoising |
|---|---|---|---|---|
| [https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/teaser/final_use/lol-v1/79_low.png](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/teaser/final_use/lol-v1/79_low.png) | [https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/teaser/final_use/ots_0011/0011_0.95_0.16.jpg](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/teaser/final_use/ots_0011/0011_0.95_0.16.jpg) | [https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/teaser/final_use/02/rain-002.png](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/teaser/final_use/02/rain-002.png) | [https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/teaser/final_use/gopro/1/GOPR0854_11_00-000001_input.png](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/teaser/final_use/gopro/1/GOPR0854_11_00-000001_input.png) | [https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/teaser/final_use/3096/input.png](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/teaser/final_use/3096/input.png) |
| [https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/teaser/final_use/lol-v1/79_normal.png](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/teaser/final_use/lol-v1/79_normal.png) | [https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/teaser/final_use/ots_0011/0011.png](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/teaser/final_use/ots_0011/0011.png) | [https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/teaser/final_use/02/norain-002.png](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/teaser/final_use/02/norain-002.png) | [https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/teaser/final_use/gopro/1/GOPR0854_11_00-000001.png](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/teaser/final_use/gopro/1/GOPR0854_11_00-000001.png) | [https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/teaser/final_use/3096/3096.png](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/teaser/final_use/3096/3096.png) |
| [https://arxiv.org/html/2403.14614/x1.png](https://arxiv.org/html/2403.14614/x1.png) | [https://arxiv.org/html/2403.14614/x2.png](https://arxiv.org/html/2403.14614/x2.png) | [https://arxiv.org/html/2403.14614/x3.png](https://arxiv.org/html/2403.14614/x3.png) | [https://arxiv.org/html/2403.14614/x4.png](https://arxiv.org/html/2403.14614/x4.png) | [https://arxiv.org/html/2403.14614/x5.png](https://arxiv.org/html/2403.14614/x5.png) |{{< /table-caption >}}

> 🔼 표 1은 세 가지 종류의 이미지 손상(흐림, 비, 노이즈)에 대한 통합 모델의 성능을 비교한 표입니다. 이 모델은 모든 손상 유형과 수준의 이미지를 결합한 데이터셋으로 학습되었습니다.  Rain100L 데이터셋을 사용한 탈우(deraining) 작업에서 AdaIR은 PromptIR보다 2.27dB 향상된 성능을 보였습니다. 표에는 각 손상 유형에 대한 PSNR(Peak Signal-to-Noise Ratio)과 SSIM(Structural SIMilarity Index) 값이 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparisons under the three-degradation all-in-one setting: a unified model is trained on a combined set of images obtained from all degradation types and levels. On Rain100L [68] for image deraining, AdaIR yields 2.27 dB gain over PromptIR [46].
> </details>





### In-depth insights


#### Frequency Modulation
본 논문에서 제시된 주파수 변조(Frequency Modulation) 기법은 다양한 이미지 손상 유형에 적응적으로 대처하기 위한 핵심 요소입니다. **주파수 영역에서의 손상 특징을 효과적으로 분리**하여, **각 주파수 대역에 최적화된 복원 과정**을 수행합니다. 저주파수 성분과 고주파수 성분을 각각 추출하여, 상호 보완적인 정보를 교환하는 양방향 연산을 통해 **손상 정보와 원본 이미지 정보를 효과적으로 분리**하는 것이 핵심입니다. 이러한 과정을 통해 모델은 다양한 손상 유형에 따라 적응적으로 복원 과정을 제어하여, **최첨단 성능**을 달성할 수 있습니다.  **주파수 특징 추출 및 변조 모듈**은 서로 긴밀하게 연동되어 작동하며, 모델의 전반적인 성능 향상에 크게 기여합니다. 특히, 다양한 손상 유형을 효과적으로 처리하기 위한 **적응력**을 강화하는데 중요한 역할을 수행합니다.  **주파수 변조 기법**은 단순한 공간 영역 처리를 넘어, 주파수 영역 분석을 도입하여 이미지 복원의 정확도와 효율성을 동시에 향상시키는 혁신적인 접근 방식을 제시합니다.

#### Adaptive Restoration
적응적 복원(Adaptive Restoration)은 **다양한 유형의 이미지 손상(노이즈, 흐림, 안개, 비 등)을 단일 모델로 처리**하는 능력을 말합니다.  기존의 이미지 복원 기법들은 특정 손상 유형에만 초점을 맞추는 경향이 있었지만, 적응적 복원은 입력 이미지의 손상 유형을 사전에 알 필요 없이 **다양한 손상을 동시에 제거**할 수 있는 **범용성**을 추구합니다. 이는 **주파수 영역 분석**을 통해 다양한 손상 유형의 고유한 주파수 특징을 파악하고, 이를 바탕으로 **적응적으로 주파수 대역을 조절**하여 복원하는 방식으로 구현될 수 있습니다.  **AdaIR과 같은 최신 알고리즘**들은 주파수 영역과 공간 영역 정보를 통합하여 **더욱 정확하고 효율적인 적응적 복원**을 실현합니다.  **주파수 정보의 적절한 활용**은 적응적 복원의 핵심이며, **다양한 손상 유형에 대한 일반화 성능**을 향상시키는 데 중요한 역할을 합니다.

#### All-in-One Approach
본 논문에서 제시된 "올인원 접근 방식"은 **단일 모델로 다양한 이미지 손상 유형(노이즈, 흐림, 안개, 비 등)을 복구**하는 것을 목표로 합니다. 기존의 개별적인 이미지 복원 방법들과 달리, **사전에 손상 유형을 알 필요 없이** 다양한 손상을 동시에 처리할 수 있다는 장점이 있습니다. 이는 **주파수 영역 분석을 기반으로 설계**되었으며, 각 손상 유형이 이미지 콘텐츠에 미치는 주파수 영역별 영향을 다르게 모델링하여 적응적으로 처리합니다.  **저주파 및 고주파 정보를 분리하여 처리**하는 모듈을 통해, 손상 유형에 따른 최적화된 복원이 가능해졌습니다. 이러한 접근 방식은 모델의 일반화 성능을 높이고, 효율성을 향상시켜 다양한 실제 환경에서의 적용 가능성을 높였습니다. 특히, **주파수 영역 분석을 통한 적응적 처리**는 본 논문의 핵심적인 기여이며, 향후 올인원 이미지 복원 분야의 발전에 중요한 영향을 미칠 것으로 예상됩니다.

#### Ablation Experiments
본 논문의 "절제 실험" 부분은 모델의 성능에 대한 각 구성 요소의 기여도를 측정하기 위해 설계되었습니다. **개별 모듈(예: 주파수 추출 모듈, 주파수 변조 모듈)을 제거하거나 변경하여 모델 성능에 미치는 영향을 분석함으로써 각 모듈의 중요성을 정량적으로 평가**합니다. 이를 통해, **모델 설계의 효율성을 높이고 성능 향상에 중요한 요소를 파악**할 수 있습니다.  **실험 결과는 각 모듈의 성능 기여도를 명확히 제시하며, 제안된 모델의 설계가 최적화되었음을 보여줍니다.** 또한, **다양한 하이퍼파라미터 설정을 시험하여 최적의 성능을 달성하는 조건을 찾는 데에도 도움**이 됩니다. 이러한 절제 실험은 모델의 견고성과 일반화 능력을 평가하는 데에도 기여하며, **모델의 강점과 한계를 명확히 이해**하는 데 중요한 역할을 수행합니다.

#### Future Directions
**미래 연구 방향**으로는, 본 논문에서 제시된 적응형 올인원 이미지 복원 프레임워크(AdaIR)의 성능 향상 및 일반화 능력 강화에 초점을 맞춰야 합니다. **다양한 종류의 이미지 훼손 유형에 대한 적응력 향상**을 위해, 주파수 분석 및 변조 모듈을 더욱 정교화하고, 다양한 훼손 유형 간의 상호 작용을 효과적으로 모델링하는 방법을 연구할 필요가 있습니다. 또한, **계산 효율성을 높이는 경량화 모델 개발** 및 **실시간 처리 성능 개선**을 위한 연구도 중요합니다. **데이터셋의 다양성 및 규모 확장**을 통해 모델의 일반화 성능을 높이고, 다양한 하드웨어 플랫폼에서의 적용 가능성을 확보하기 위한 연구도 필요합니다.  마지막으로, **다른 이미지 처리 과제와의 통합**을 고려하여 AdaIR의 활용 범위를 확장하는 연구도 중요한 미래 연구 방향이 될 것입니다.


### More visual insights




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Image | Image | Image | Image |
|---|---|---|---|
| ![Refer to caption](https://arxiv.org/html/2403.14614/x7.png) | ![Refer to caption](https://arxiv.org/html/2403.14614/x8.png) | ![Refer to caption](https://arxiv.org/html/2403.14614/x9.png) | ![Refer to caption](https://arxiv.org/html/2403.14614/x10.png) |
| AirNet [33] | PromptIR [46] | Ours |  |
{{< /table-caption >}}
> 🔼 표 2는 단일 작업 설정에서 SOTS-Outdoor [32] 데이터셋에 대한 탈안개 결과를 보여줍니다. PromptIR [46]과 비교했을 때, 제안된 방법은 PSNR이 0.49dB 향상되었습니다. 이 표는 다양한 탈안개 방법들 간의 성능 비교를 보여주며, 제안된 방법의 우수성을 보여줍니다. 특히 PSNR과 SSIM 지표를 사용하여 정량적으로 비교 분석하였습니다.  각 방법의 PSNR과 SSIM 값을 제시하여 정확한 성능 비교를 수행했습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Dehazing results in the single-task setting on the SOTS-Outdoor [32] dataset. Compared to PromptIR [46], our method generates a 0.49 dB PSNR improvement.
> </details>

{{< table-caption >}}
| Method | Dehazing on SOTS [32] | Deraining on Rain100L [68] | Denoising on BSD68 [41]  σ=15 | σ=25 | σ=50 | Average |
|---|---|---|---|---|---|---|
| BRDNet [56] | 23.23/0.895 | 27.42/0.895 | 32.26/0.898 | 29.76/0.836 | 26.34/0.693 | 27.80/0.843 |
| LPNet [22] | 20.84/0.828 | 24.88/0.784 | 26.47/0.778 | 24.77/0.748 | 21.26/0.552 | 23.64/0.738 |
| FDGAN [20] | 24.71/0.929 | 29.89/0.933 | 30.25/0.910 | 28.81/0.868 | 26.43/0.776 | 28.02/0.883 |
| MPRNet [73] | 25.28/0.955 | 33.57/0.954 | 33.54/0.927 | 30.89/0.880 | 27.56/0.779 | 30.17/0.899 |
| DL [21] | 26.92/0.931 | 32.62/0.931 | 33.05/0.914 | 30.41/0.861 | 26.90/0.740 | 29.98/0.876 |
| AirNet [33] | 27.94/0.962 | 34.90/0.968 | 33.92/0.933 | 31.26/0.888 | 28.00/0.797 | 31.20/0.910 |
| PromptIR [46] | 30.58/0.974 | 36.37/0.972 | 33.98/0.933 | 31.31/0.888 | 28.06/0.799 | 32.06/0.913 |
| **AdaIR (Ours)** | **31.06/0.980** | **38.64/0.983** | **34.12/0.935** | **31.45/0.892** | **28.19/0.802** | **32.69/0.918** |{{< /table-caption >}}
> 🔼 표 3은 Rain100L 데이터셋에서 단일 작업 설정으로 수행된 제비 제거 결과를 보여줍니다. AdaIR은 기존 최고 성능 모델인 PromptIR보다 PSNR이 1.86dB 향상되었음을 보여줍니다. 이 표는 다양한 제비 제거 모델들의 PSNR과 SSIM 성능을 비교하여 AdaIR의 우수성을 입증합니다.  특히, AdaIR은 다른 모델들에 비해 훨씬 높은 PSNR 값을 기록하여, 비가 내리는 이미지에서 비 효과를 제거하는 데 탁월한 성능을 보임을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Deraining results in the single-task setting on the Rain100L [68] dataset. Our AdaIR obtains a significant performance boost of 1.86 dB PSNR over PromptIR [46].
> </details>

{{< table-caption >}}
| Image | Input | AirNet | PromptIR | AdaIR | Reference |
|---|---|---|---|---|---| 
| <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-haze/154_c/input_full.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-haze/154_c/input.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-haze/154_c/airnet.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-haze/154_c/pir.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-haze/154_c/our.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-haze/154_c/gt.png" width="96" height="78"> |
| Degraded | 7.84 dB | 23.09 dB | 25.30 dB | 30.80 dB | PSNR |
| <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-haze/253_0.2_c/input_full.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-haze/253_0.2_c/input.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-haze/253_0.2_c/airnet.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-haze/253_0.2_c/pir.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-haze/253_0.2_c/ours.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-haze/253_0.2_c/gt.png" width="96" height="78"> |
| Degraded | 10.82 dB | 27.49 dB | 28.75 dB | 31.68 dB | PSNR |
| <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-haze/1738_/input_full.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-haze/1738_/input.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-haze/1738_/airnet.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-haze/1738_/pir.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-haze/1738_/ours.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-haze/1738_/gt.png" width="96" height="78"> |
| Degraded | 9.57 dB | 19.34 dB | 19.88 dB | 24.61 dB | PSNR |{{< /table-caption >}}
> 🔼 표 4는 Urban100 [25] 및 BSD68 [41] 데이터셋에서 단일 작업 설정으로 수행된 잡음 제거 결과를 보여줍니다.  이 표는 다양한 잡음 수준(σ = 15, 25, 50)에서 여러 잡음 제거 방법들의 PSNR(Peak Signal-to-Noise Ratio)과 SSIM(Structural Similarity Index) 성능을 비교 분석합니다. 특히, 잡음 수준 50에서 AdaIR은 PromptIR [46]보다 0.31dB 향상된 성능을 보여줍니다.  표는 각 방법의 평균 성능을 보여주는 것 외에도, 각 잡음 수준별 성능을 구체적으로 제시하여 다양한 잡음 강도에 따른 알고리즘의 성능 차이를 명확하게 비교 분석할 수 있도록 합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Denoising results in the single-task setting on Urban100 [25] and BSD68 [41]. On Urban100 [25] for the noise level 50, AdaIR yields a 0.31 dB gain over PromptIR [46].
> </details>

{{< table-caption >}}
| Image | Input | AirNet | PromptIR | AdaIR | Reference |
|---|---|---|---|---|---| 
| <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-rain/air_rain_14_65_c/input_full.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-rain/air_rain_14_65_c/input.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-rain/air_rain_14_65_c/14_65_airnet.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-rain/air_rain_14_65_c/14_65_pir.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-rain/air_rain_14_65_c/14_65_ours.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-rain/air_rain_14_65_c/14_65_gt.png" width="96" height="78"> |
| Degraded | 16.92 dB | 28.40 dB | 28.81 dB | 31.38 dB | PSNR |
| <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-rain/88/input_image.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-rain/88/input.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-rain/88/airnet.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-rain/88/promptir.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-rain/88/ours.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-rain/88/gt.png" width="96" height="78"> |
| Degraded | 23.16 dB | 31.12 dB | 33.64 dB | 38.66 dB | PSNR |
| <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-rain/70_cc/input_full.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-rain/70_cc/input.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-rain/70_cc/airnet.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-rain/70_cc/pir.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-rain/70_cc/ours.png" width="96" height="78"> | <img src="https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-rain/70_cc/gt.png" width="96" height="78"> |
| Degraded | 27.49 dB | 35.53 dB | 39.25 dB | 44.90 dB | PSNR |
| Image | Input | AirNet | PromptIR | **AdaIR** | Reference |{{< /table-caption >}}
> 🔼 표 5는 다섯 가지의 이미지 손상(degration)에 대한 올인원(all-in-one) 복원 방법들을 비교 분석한 표입니다. 잡음 제거(denoising) 결과는 잡음 강도(noise level) σ가 25일 때의 결과를 보여줍니다. 표의 위쪽 부분은 일반적인 이미지 복원 방법들을, 아래쪽 부분은 특정 손상 유형에 특화된 올인원 방법들을 나타냅니다. SOTS [68] 데이터셋을 이용한 뿌연 이미지(haze) 제거 작업에서 AdaIR은 IDR [76] 방법보다 5.29dB 향상된 성능을 보였습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Comparisons for five-degradation all-in-one restoration. Denoising results are reported for the noise level σ=25𝜎25\sigma=25italic_σ = 25. The top super-row methods denote the general image restoration approaches, and the rest are specialized all-in-one approaches. On SOTS [68] for dehazing, AdaIR attains a remarkable gain of 5.29 dB over IDR [76].
> </details>

{{< table-caption >}}
| Image | Input | AirNet | PromptIR | AdaIR | Reference |
|---|---|---|---|---|---| 
| ![Degraded](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-noise/1_c/input_full.png) | ![14.95 dB](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-noise/1_c/input.png) | ![33.11 dB](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-noise/1_c/airnet.png) | ![32.91 dB](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-noise/1_c/pir.png) | ![34.02 dB](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-noise/1_c/aours.png) | ![PSNR](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-noise/1_c/gt.png) |
| ![Degraded](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-noise/jing/input_image.png) | ![14.89 dB](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-noise/jing/input.png) | ![27.19 dB](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-noise/jing/airnet.png) | ![27.23 dB](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-noise/jing/pir.png) | ![27.68 dB](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-noise/jing/ours.png) | ![PSNR](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-noise/jing/gt.png) |
| ![Degraded](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-noise/223061_c/input_full.png) | ![15.63 dB](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-noise/223061_c/input.png) | ![26.73 dB](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-noise/223061_c/airnet.png) | ![26.18 dB](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-noise/223061_c/pir.png) | ![27.12 dB](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-noise/223061_c/ours.png) | ![PSNR](https://arxiv.org/html/2403.14614/extracted/5487039/main_fig/3d-noise/223061_c/gt.png) |{{< /table-caption >}}
> 🔼 표 6은 다섯 가지 이미지 품질 저하 유형에 대해 사전 훈련된 모델을 Urban100, Kodak24, BSD68 데이터셋에 직접 적용하여 얻은 이미지 잡음 제거 결과를 보여줍니다. 결과는 PSNR 점수로 나타내며, Urban100 데이터셋에서 노이즈 레벨 σ가 25일 때 AdaIR은 IDR보다 PSNR이 0.39dB 향상되는 것을 보여줍니다. 이 표는 다양한 데이터셋과 노이즈 레벨에서 AdaIR의 성능을 보여주어, 다양한 잡음 조건에서도 우수한 성능을 유지함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Image denoising results of directly applying the pre-trained model under the five-degradation setting to the Urban100 [25], Kodak24 [53] and BSD68 [41] datasets. The results are PSNR scores. On Urban100 [25] for the noise level σ=25𝜎25\sigma=25italic_σ = 25, AdaIR produces a significant performance gain of 0.39 dB PSNR over IDR [76].
> </details>

{{< table-caption >}}
| Method | DehazeNet | MSCNN | AODNet | EPDN | FDGAN | AirNet | Restormer | PromptIR | AdaIR |
|---|---|---|---|---|---|---|---|---|---| 
| PSNR | 22.46 | 22.06 | 20.29 | 22.57 | 23.15 | 23.18 | 30.87 | 31.31 | 31.80 |
| SSIM | 0.851 | 0.908 | 0.877 | 0.863 | 0.921 | 0.900 | 0.969 | 0.973 | 0.981 |{{< /table-caption >}}
> 🔼 표 7은 제안된 구성 요소에 대한 절삭 연구 결과를 보여줍니다. 'Fixed'는 한 변의 길이가 10인 고정된 정사각형 마스크를 사용합니다. FLOPs는 256x256x3 패치 크기에 대해 측정됩니다. 이 표는 주요 구성 요소(FMiM, FMOM, H-L, L-H)의 성능에 미치는 영향을 분석하고, 각 구성 요소가 전체 성능 향상에 기여하는 정도를 정량적으로 보여줍니다.  각 행은 특정 구성요소의 활성화 여부를 나타내며, PSNR과 SSIM 값을 통해 성능 변화를 비교 분석합니다.  마지막 행 (e)는 모든 구성요소가 활성화된 AdaIR 모델의 결과를 보여줍니다.  이는 각 구성요소의 효과를 개별적으로 그리고 전체적으로 평가하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Ablation studies for the proposed components. Fixed uses a fixed square mask with sides of 10. FLOPs are measured on the patch size of 256×256×32562563256\times 256\times 3256 × 256 × 3.
> </details>

{{< table-caption >}}
| Method | DIDMDN | UMR | SIRR | MSPFN | LPNet | AirNet | Restormer | PromptIR | AdaIR |
|---|---|---|---|---|---|---|---|---|---| 
| PSNR | 23.79 | 32.39 | 32.37 | 33.50 | 33.61 | 34.90 | 36.74 | 37.04 | 38.90 |
| SSIM | 0.773 | 0.921 | 0.926 | 0.948 | 0.958 | 0.977 | 0.978 | 0.979 | 0.985 |{{< /table-caption >}}
> 🔼 표 8은 이미지 복원을 위한 주파수 분해 방법에 대한 비교 결과를 보여줍니다.  세 가지 방법, 즉 평균 풀링, 가우시안 필터링 및 본 논문에서 제안하는 방법을 비교하여 PSNR 및 SSIM 값을 제시합니다.  본 논문에서 제안하는 방법이 다른 두 방법보다 더 나은 성능을 보임을 확인할 수 있습니다. 이 표는 다양한 주파수 영역 분해 기법의 효과를 정량적으로 비교 분석하여 AdaIR 모델의 성능 향상에 기여하는 핵심 요소를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Spectra decomposition methods.
> </details>

{{< table-caption >}}
| Method | Urban100 σ=15 | Urban100 σ=25 | Urban100 σ=50 | BSD68 σ=15 | BSD68 σ=25 | BSD68 σ=50 | Average | 
|---|---|---|---|---|---|---|---| 
| CBM3D [17] | 33.93/0.941 | 31.36/0.909 | 27.93/0.840 | 33.50/0.922 | 30.69/0.868 | 27.36/0.763 | 30.80/0.874 | 
| DnCNN [77] | 32.98/0.931 | 30.81/0.902 | 27.59/0.833 | 33.89/0.930 | 31.23/0.883 | 27.92/0.789 | 30.74/0.878 | 
| IRCNN [78] | 27.59/0.833 | 31.20/0.909 | 27.70/0.840 | 33.87/0.929 | 31.18/0.882 | 27.88/0.790 | 29.90/0.864 | 
| FFDNet [79] | 33.83/0.942 | 31.40/0.912 | 28.05/0.848 | 33.87/0.929 | 31.21/0.882 | 27.96/0.789 | 31.05/0.884 | 
| BRDNet [56] | 34.42/0.946 | 31.99/0.919 | 28.56/0.858 | 34.10/0.929 | 31.43/0.885 | 28.16/0.794 | 31.44/0.889 | 
| AirNet [33] | 34.40/0.949 | 32.10/0.924 | 28.88/0.871 | 34.14/0.936 | 31.48/0.893 | 28.23/0.806 | 31.54/0.897 | 
| PromptIR [46] | 34.77/0.952 | 32.49/0.929 | 29.39/0.881 | 34.34/0.938 | 31.71/0.897 | 28.49/0.813 | 31.87/0.902 | 
| **AdaIR (Ours)** | **34.96**/0.953 | **32.74**/0.931 | **29.70**/0.885 | **34.36**/0.938 | **31.72**/0.897 | **28.49**/0.813 | **32.00**/0.903 | {{< /table-caption >}}
> 🔼 표 9는 논문의 실험에서 사용된 다양한 이미지 손상 유형(예: 잡음, 비, 안개, 흐림)의 출처를 보여줍니다.  각 손상 유형은 어떤 데이터셋이나 방법을 사용하여 생성되었는지 명시하여, 실험의 재현성을 높이고 사용된 데이터의 특징을 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Degradation sources.
> </details>

{{< table-caption >}}
| Task             | Dehazing   | Deraining   | Denoising  | Deblurring  | Low-Light  | Average     |
|-----------------|-------------|-------------|-------------|-------------|------------|--------------|
| Method           | on SOTS     | on Rain100L | on BSD68    | on GoPro    | on LOL     |              |
| NAFNet [9]       | 25.23/0.939 | 35.56/0.967 | 31.02/0.883 | 26.53/0.808 | 20.49/0.809 | 27.76/0.881 |
| HINet [10]      | 24.74/0.937 | 35.67/0.969 | 31.00/0.881 | 26.12/0.788 | 19.47/0.800 | 27.40/0.875 |
| MPRNet [73]     | 24.27/0.937 | 38.16/0.981 | 31.35/0.889 | 26.87/0.823 | 20.84/0.824 | 28.27/0.890 |
| DGUNet [43]     | 24.78/0.940 | 36.62/0.971 | 31.10/0.883 | 27.25/0.837 | 21.87/0.823 | 28.32/0.891 |
| MIRNetV2 [74]   | 24.03/0.927 | 33.89/0.954 | 30.97/0.881 | 26.30/0.799 | 21.52/0.815 | 27.34/0.875 |
| SwinIR [36]     | 21.50/0.891 | 30.78/0.923 | 30.59/0.868 | 24.52/0.773 | 17.81/0.723 | 25.04/0.835 |
| Restormer [70]  | 24.09/0.927 | 34.81/0.962 | 31.49/0.884 | 27.22/0.829 | 20.41/0.806 | 27.60/0.881 |
| DL [21]         | 20.54/0.826 | 21.96/0.762 | 23.09/0.745 | 19.86/0.672 | 19.83/0.712 | 21.05/0.743 |
| Transweather [61]| 21.32/0.885 | 29.43/0.905 | 29.00/0.841 | 25.12/0.757 | 21.21/0.792 | 25.22/0.836 |
| TAPE [38]       | 22.16/0.861 | 29.67/0.904 | 30.18/0.855 | 24.47/0.763 | 18.97/0.621 | 25.09/0.801 |
| AirNet [33]     | 21.04/0.884 | 32.98/0.951 | 30.91/0.882 | 24.35/0.781 | 18.18/0.735 | 25.49/0.846 |
| IDR [76]        | 25.24/0.943 | 35.63/0.965 | 31.60/0.887 | 27.87/0.846 | 21.34/0.826 | 28.34/0.893 |
| **AdaIR (Ours)** | **30.53**/0.978 | **38.02**/0.981 | 31.35/0.889 | **28.12**/0.858 | **23.00**/0.845 | **30.20**/0.910 |{{< /table-caption >}}
> 🔼 표 9는 논문의 실험에서 사용된 다양한 이미지 손상 유형(Degradation)의 출처를 보여줍니다.  즉, 어떤 데이터셋에서 어떤 종류의 이미지 손상이 사용되었는지에 대한 정보를 요약하여 제시합니다. 이 표를 통해 독자는 논문에서 사용된 데이터셋의 다양성과 실험의 범위를 더욱 잘 이해할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Degradation sources.
> </details>

{{< table-caption >}}
| Method | Urban100 σ=15 | Urban100 σ=25 | Urban100 σ=50 | Kodak24 σ=15 | Kodak24 σ=25 | Kodak24 σ=50 | BSD68 σ=15 | BSD68 σ=25 | BSD68 σ=50 | Average |
|---|---|---|---|---|---|---|---|---|---|---|
| DL [21] | 21.10 | 21.28 | 20.42 | 22.63 | 22.66 | 21.95 | 23.16 | 23.09 | 22.09 | 22.04 |
| Transweather [61] | 29.64 | 27.97 | 26.08 | 31.67 | 29.64 | 26.74 | 31.16 | 29.00 | 26.08 | 28.66 |
| TAPE [38] | 32.19 | 29.65 | 25.87 | 33.24 | 30.70 | 27.19 | 32.86 | 30.18 | 26.63 | 29.83 |
| AirNet [33] | 33.16 | 30.83 | 27.45 | 34.14 | 31.74 | 28.59 | 33.49 | 30.91 | 27.66 | 30.89 |
| IDR [76] | 33.82 | 31.29 | 28.07 | 34.78 | 32.42 | 29.13 | 34.11 | 31.60 | 28.14 | 31.48 |
| AdaIR (Ours) | 34.10 | 31.68 | 28.29 | 34.89 | 32.38 | 29.21 | 34.01 | 31.35 | 28.06 | 31.55 |{{< /table-caption >}}
> 🔼 표 10은 논문에서 제시된 AdaIR 모델의 성능을 CSD 데이터셋의 눈 제거 작업에 대해 평가한 결과를 보여줍니다.  AdaIR 모델은 다양한 이미지 복원 작업에 대해 훈련되었지만, CSD 데이터셋은 훈련 과정에서 사용되지 않은 데이터셋이므로 이 표는 AdaIR 모델의 일반화 성능을 평가하는 데 중점을 둡니다.  즉, 다양한 유형의 이미지 손상에 대한 훈련을 통해 익힌 지식을 얼마나 잘 일반화하여 본 적 없는 새로운 유형의 손상(눈 제거)에도 적용할 수 있는지 보여주는 것입니다. 표에는 AirNet, PromptIR 및 AdaIR 세 가지 모델의 PSNR(Peak Signal-to-Noise Ratio)과 SSIM(Structural SIMilarity Index) 값이 제시되어 있으며,  AdaIR 모델이 다른 두 모델에 비해 눈 제거 작업에서 더 나은 성능을 보임을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Results on the unseen desnowing task with the CSD [11] dataset.
> </details>

{{< table-caption >}}
| Net | Baseline | Fixed | MGB | L-H | H-L | PSNR | SSIM | Params. | FLOPs |
|---|---|---|---|---|---|---|---|---|---| 
| (a) | ✓ |  |  |  |  | 28.21 | 0.966 | 26.13M | 141.24G |
| (b) | ✓ | ✓ |  |  |  | 29.79 | 0.969 | 27.73M | 145.09G |
| (c) | ✓ | ✓ |  | ✓ |  | 30.37 | 0.975 | 28.74M | 147.44G |
| (d) | ✓ | ✓ |  | ✓ | ✓ | 30.52 | 0.976 | 28.74M | 147.44G |
| (e) | ✓ |  | ✓ | ✓ | ✓ | 31.24 | 0.978 | 28.77M | 147.45G |{{< /table-caption >}}
> 🔼 표 11은 Rain100L 데이터셋에 가우시안 노이즈 (σ=50)가 추가된 혼합 손상 이미지에 대한 실험 결과를 보여줍니다.  AdaIR 모델은 다른 All-in-One 이미지 복원 모델들(AirNet, PromptIR) 과 비교하여 성능을 평가합니다.  PSNR과 SSIM 지표를 사용하여 이미지 품질을 측정하고,  AdaIR이 다른 모델들에 비해 혼합 손상 이미지 복원에서 우수한 성능을 보이는지 확인합니다.
> <details>
> <summary>read the caption</summary>
> Table 11: Results on mixed degradations, Rain100L with the Gaussian noise σ=50𝜎50\sigma=50italic_σ = 50.
> </details>

{{< table-caption >}}
| Methods | Average Pooling | Gaussian Filter | Ours |
|---|---|---|---| 
| PSNR | 30.59 | 30.22 | 31.24 |
| SSIM | 0.976 | 0.976 | 0.978 |{{< /table-caption >}}
> 🔼 표 11은 Rain100L 데이터셋에 가우시안 노이즈(σ=50)가 추가된 혼합 손상 이미지에 대한 실험 결과를 보여줍니다.  AdaIR 모델을 포함한 여러 복원 알고리즘의 성능을 PSNR 및 SSIM 지표를 사용하여 비교 분석합니다. 이 표는 다양한 손상 유형이 결합된 복잡한 이미지 복원 시나리오에서 AdaIR 모델의 성능을 평가하고 다른 모델과 비교하는 데 중점을 둡니다.
> <details>
> <summary>read the caption</summary>
> Table 11: Results on mixed degradations, Rain100L with the Gaussian noise σ=50𝜎50\sigma=50italic_σ = 50.
> </details>

{{< table-caption >}}
| Method | Embedding | Ours |
|---|---|---|
| PSNR | 29.29 | 30.52 |
| SSIM | 0.969 | 0.976 |{{< /table-caption >}}
> 🔼 표 12는 단일 작업 설정에서 이미지 제거에 대한 비교를 보여줍니다. 인코더 측면, 디코더 측면 또는 둘 다에서 AFLB(적응형 주파수 학습 블록)를 사용하는 경우의 성능을 비교 분석합니다.  AFLB를 디코더에만 통합했을 때 가장 좋은 성능을 보입니다. 이는 인코더와 디코더 모두에 AFLB를 사용하면 성능이 저하될 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 12: Comparisons of image dehazing under the single-task setting: between the use of AFLBs on either the encoder-side, decoder-side, or both.
> </details>

{{< table-caption >}}
| Method | AirNet [33] | PromptIR [46] | Ours |
|---|---|---|---|
| PSNR | 19.32 | 20.47 | 20.54 |
| SSIM | 0.733 | 0.7638 | 0.7643 |{{< /table-caption >}}
> 🔼 표 13은 SOTS 데이터셋[32]에서 AFLB(적응형 주파수 학습 블록)의 위치에 따른 성능 변화를 보여줍니다.  실험은 디코더의 특정 계층(레벨 2, 레벨 2와 3 사이, 레벨 2, 3, 4 사이)에 AFLB를 배치했을 때의 PSNR과 SSIM 값을 비교 분석하여  디코더의 모든 연속적인 계층 사이에 AFLB를 배치하는 것이 최적임을 보여줍니다.  즉, AFLB를 적절한 위치에 배치하는 것이 이미지 복원 성능에 중요한 영향을 미친다는 것을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 13: AFLB position. Results are reported on the SOTS [32] dataset.
> </details>

{{< table-caption >}}
| Method | AirNet [33] | PromptIR [46] | Ours |
|---|---|---|---|
| PSNR | 27.25 | 27.34 | 27.51 |
| SSIM | 0.790 | 0.791 | 0.799 |{{< /table-caption >}}
> 🔼 표 14는 논문의 세 가지 복원 작업(탈잡음, 탈비, 탈안개)에 대한 다양한 조합의 손상을 적용한 실험 결과를 보여줍니다.  각 손상 유형(잡음, 비, 안개)에 대해 여러 가지 조합을 시도하여 각 조합에 따른 PSNR(dB) 및 SSIM 값을 제시함으로써 다양한 손상 조합이 모델 성능에 미치는 영향을 분석합니다. 이 표는 다양한 손상의 존재가 이미지 복원 모델에 어떤 영향을 주는지, 특히 손상 조합이 성능에 미치는 영향을 정량적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 14: Ablation studies on the combinations of degradations for the three-task setting. Results are presented in the form of PSNR (dB)/SSIM.
> </details>

{{< table-caption >}}
| Method | PSNR | SSIM |
|---|---|---|
| Encoder+Decoder+AFLB | 29.70 | 0.973 |
| AdaIR (Ours) | 30.52 | 0.976 |{{< /table-caption >}}
> 🔼 표 15는 세 가지 종류의 이미지 손상(흐림, 비, 노이즈)이 있는 경우에 대해 모든 기능을 갖춘 이미지 복원 모델들의 계산 비용을 비교 분석한 표입니다. 세 가지 작업에 대한 평균 PSNR(Peak Signal-to-Noise Ratio) 값을 보여주며, 자세한 결과는 본 논문의 표 1을 참조하라고 안내하고 있습니다.  FLOPs(Floating Point Operations)는 256x256x3 크기의 패치에 대해 측정되었습니다. 이 표는 정확도와 계산 효율성 사이에서 다양한 모델들이 어떤 절충을 하는지를 보여주는 지표가 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 15: Computational comparisons of all-in-one methods under the three-degradation setting. Average PSNR across three tasks is reported here (see Table 1 of the main paper for more detailed results). FLOPs are measured on the patch size of 256×256×32562563256\times 256\times 3256 × 256 × 3.
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