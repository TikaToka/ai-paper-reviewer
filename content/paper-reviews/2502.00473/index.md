---
title: "Weak-to-Strong Diffusion with Reflection"
summary: "약한 확산 모델과 강력한 확산 모델 간의 차이를 이용하여 이상적인 모델과의 격차를 줄이는 새로운 프레임워크, W2SD 제시!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Machine Learning", "Deep Learning", "🏢 Hong Kong University of Science and Technology",]
showSummary: true
date: 2025-02-01
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.00473 {{< /keyword >}}
{{< keyword icon="writer" >}} Lichen Bai et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-07 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.00473" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.00473" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

기존 확산 모델들은 학습 데이터의 질, 모델링 전략, 아키텍처 설계 등의 한계로 인해 생성 결과물과 실제 데이터 간에 격차가 존재합니다. 이러한 격차를 줄이기 위한 다양한 연구들이 진행되었지만, 실제 데이터 분포에 대한 직접적인 접근이 어려워 한계가 있습니다. 본 논문에서는 **기존의 약한 모델과 강력한 모델 간의 차이를 이용하여 이상적인 모델과의 격차를 근사하는 새로운 방법론인 W2SD**를 제시합니다.

W2SD는 약한 모델과 강력한 모델을 번갈아 사용하는 반사(reflection) 연산을 통해 잠재 변수를 실제 데이터 분포의 영역으로 유도합니다. 다양한 실험 결과를 통해 W2SD가 이미지, 비디오 등 다양한 모달리티, UNet 기반 및 DiT 기반 등 다양한 아키텍처에서 우수한 성능 향상을 보임을 보여줍니다. 특히, 추가적인 계산 비용 대비 높은 성능 향상 효과를 보이며, **다양한 약한 모델과 강력한 모델의 조합을 통해 성능 향상 효과를 누적시킬 수 있다는 점에서 높은 실용성**을 가지고 있습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 약한 모델과 강력한 모델의 차이를 이용하여 이상적인 모델과의 격차를 효과적으로 줄이는 새로운 프레임워크 W2SD를 제안합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} W2SD는 이미지, 비디오 등 다양한 모달리티와 UNet 기반, DiT 기반 등 다양한 아키텍처에 적용 가능하며, 우수한 성능 향상을 보입니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} W2SD는 추가적인 계산 비용 대비 성능 향상 효과가 뛰어나며, 다양한 약한 모델과 강력한 모델 조합을 통해 성능 향상 효과를 누적시킬 수 있습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **확산 모델의 추론 성능을 향상시키는 새로운 프레임워크인 W2SD**를 제시하여, 기존의 강력한 모델과 약한 모델 간의 차이를 이용하여 이상적인 모델과의 격차를 줄이는 방법을 제시합니다. 이는 **다양한 모달리티와 아키텍처에서 적용 가능하며, 계산 비용 대비 성능 향상이 뛰어나다는 점에서 높은 실용성을 가집니다.** 또한, 이 연구는 확산 모델의 추론 과정에 대한 이론적 이해를 심화시키고, 향후 연구를 위한 새로운 방향을 제시합니다.  특히, **다양한 모델 조합의 적용 가능성**과 **성능 향상 효과의 누적 가능성**을 실험적으로 증명하여, 실제 응용 가능성을 높였습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.00473/x1.png)

> 🔼 이 그림은 약한 모델과 강한 모델 간의 차이를 이용하여 강한 모델과 이상적인 모델 간의 차이를 근사하는 W2SD(약한 모델에서 강한 모델로의 확산)의 개념을 보여줍니다. 왼쪽 패널은 약한 모델, 중간 패널은 강한 모델, 오른쪽 패널은 이상적인 모델의 확률 분포를 보여줍니다. W2SD는 약한 모델과 강한 모델 간의 차이(A1)를 추정하여 강한 모델과 이상적인 모델 간의 차이(A2)를 근사합니다. 이를 통해 W2SD는 샘플링 과정에서 잠재 변수를 실제 데이터 분포의 영역으로 유도하여 생성 품질을 향상시킵니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: W2SD leverages the gap between weak and strong models to approximate the gap between strong and ideal models.
> </details>





{{< table-caption >}}
| Method | HPS v2 ↑ | AES ↑ | PickScore ↑ | MPS ↑ |
|---|---|---|---|---|
| SD1.5 | 24.9558 | 5.5003 | 20.1368 | - |
| DreamShaper | 30.1477 | 6.1155 | 21.5035 | 46.8705 |
| **W2SD** | **30.4924** | **6.2478** | **21.5727** | **53.1304** |
| SDXL | 29.8701 | **6.0939** | 21.6487 | - |
| Juggernaut-XL | 31.6412 | 5.9790 | 22.1903 | 45.7397 |
| **W2SD** | **32.0992** | 6.0712 | **22.2434** | **54.2634** |{{< /table-caption >}}

> 🔼 표 1은 전체 파라미터 미세 조정 전략을 기반으로 한 W2SD의 정량적 결과를 보여줍니다. W2SD는 인간의 선호도에 더 잘 맞는 결과를 생성합니다. 데이터셋은 Pick-a-Pic입니다.  이 표는 HPS v2, AES, PickScore, MPS 등 여러 지표를 사용하여 W2SD 기법을 적용했을 때의 성능 향상을 정량적으로 보여줍니다. 각 지표는 이미지 생성 품질의 다양한 측면(예: 인간의 미적 선호도, 이미지의 미학적 품질, 프롬프트 충실도)을 평가합니다.  표에서 W2SD를 적용한 모델이 기준 모델(SD1.5, DreamShaper, SDXL, Juggernaut-XL)보다 모든 지표에서 더 높은 점수를 받은 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Quantitative results of W2SD based on a full parameter fine-tuning strategy. Our method generates results better aligned with human preferences. Datasets: Pick-a-Pic.
> </details>





### In-depth insights


#### Weak-to-Strong Diff
**약-강 확산(Weak-to-Strong Diffusion)** 개념은 기존의 강력한 확산 모델의 성능을 개선하기 위해 약한 모델과의 차이를 활용하는 독창적인 방법입니다.  **핵심 아이디어는 이상적인 모델과 강력한 모델 사이의 격차를 약한 모델과 강력한 모델 간의 차이로 근사하는 것**입니다. 이를 통해 접근하기 어려운 이상적인 모델과의 차이를 효과적으로 추정하고, 강력한 모델을 개선하는 데 활용합니다.  이는 단순히 기존 모델을 개선하는 것을 넘어, **모델의 한계를 이해하고 이를 보완하는 새로운 패러다임**을 제시합니다.  **약한 모델의 선택은 유연성을 제공**하여 다양한 방식으로 성능 향상을 도모할 수 있습니다. 이 방법은 단순한 개념적 제안이 아니라, 실제 실험을 통해 그 효과가 검증되었다는 점에서 큰 의의를 지닙니다.  향후 연구에서는 **다양한 약한 모델의 선택과 조합을 통한 추가적인 성능 향상**, 그리고 **다른 생성 모델에의 적용 가능성**에 대한 연구가 필요할 것으로 예상됩니다.  **이러한 연구는 생성 모델 분야의 발전에 크게 기여**할 것으로 기대됩니다.

#### Reflection Mechanics
본 논문에서 제시된 "Reflection Mechanics"는 확산 모델의 추론 과정을 개선하기 위한 핵심 메커니즘으로 보입니다. **약한 모델과 강한 모델 간의 차이를 이용하여 이상적인 모델과 강한 모델 간의 차이를 근사**하는 방식입니다. 이를 통해 생성된 샘플이 실제 데이터 분포에 더 가까워지도록 유도합니다.  **반사 연산**을 통해 약한 모델과 강한 모델 간의 차이를 활용하여 잠재 변수를 실제 데이터 분포의 영역으로 유도하는 과정은 매우 흥미롭습니다.  이는 단순히 기존 모델의 성능을 향상시키는 것을 넘어, **추론 과정 자체의 근본적인 메커니즘을 이해하고 개선**하는 데 초점을 맞추고 있음을 시사합니다.  **다양한 약-강 모델 조합**을 통해 유연성을 확보하고, 다양한 모달리티와 아키텍처에서도 적용 가능하다는 점은 실용적인 측면에서 큰 장점입니다.  **이론적 분석과 실험적 결과**를 통해 이러한 메커니즘의 효과를 검증하고, 추가적인 분석을 통해 그 한계와 개선 방향을 제시한다면 더욱 완성도 높은 연구가 될 것입니다.  본 메커니즘은 단순히 기술적인 개선을 넘어, 확산 모델의 이론적 이해와 실제 응용에 큰 기여를 할 것으로 예상됩니다. 특히, **다양한 모델 간 차이를 효과적으로 활용**하는 점은 다른 생성 모델에도 적용 가능한 일반적인 원리로 확장될 가능성이 높습니다.

#### W2SD Algorithm
W2SD 알고리즘은 약한 확산 모델과 강한 확산 모델 간의 차이를 이용하여 이상적인 모델과 강한 모델 간의 차이를 근사하는 참신한 방법입니다. **반복적인 반사 연산**을 통해 잡음 제거와 역변환을 번갈아 수행하며, 잠재 변수를 실제 데이터 분포의 영역으로 유도합니다. 이는 약한 모델의 부족한 부분을 강한 모델의 장점을 활용하여 보완하는 전략으로, **다양한 모달리티와 아키텍처에서 뛰어난 성능**을 보여줍니다.  **약한 모델과 강한 모델의 쌍을 전략적으로 선택**하는 것이 성능 향상에 중요한 역할을 하며,  **계산 비용 대비 성능 향상**이 뛰어나 실용성이 높습니다.  W2SD 알고리즘은 이론적 이해와 실험적 검증을 통해 그 효과를 입증하며, 향후 확산 모델 연구에 중요한 기여를 할 것으로 기대됩니다. 특히, **다양한 응용 분야에 적용 가능성**이 높아 폭넓은 연구 확장을 기대할 수 있습니다.

#### Broad Applicability
본 논문에서 제시된 방법론의 광범위한 적용 가능성은 **다양한 모달리티(이미지, 비디오), 아키텍처(UNet 기반, DiT 기반, MoE), 그리고 벤치마크에 걸쳐 최첨단 성능을 달성**함으로써 입증되었습니다.  이는 단순히 특정 모델이나 데이터셋에 국한되지 않고, **모델 간의 차이를 전략적으로 활용하여 개선 효과를 도출**하는 핵심 아이디어에 기반하기 때문입니다.  **약한 모델과 강한 모델의 조합을 유연하게 선택**할 수 있으며, 이를 통해 다양한 종류의 개선 효과를 얻을 수 있습니다.  **계산 비용 증가에도 불구하고 성능 향상이 더 크다는 점**이 실험적으로 확인되었으며, 이는 **실용성과 효율성을 동시에 확보**하는 강점으로 이어집니다.  결론적으로, 제시된 방법론은 **범용적이고 확장성이 뛰어나**, 다양한 생성 모델 및 응용 분야에 적용될 수 있는 잠재력을 가지고 있습니다.

#### Future Directions
미래 방향에 대한 심도있는 고찰은 **약-강 확산 모델의 일반화 및 적용 확대**에 초점을 맞춰야 합니다.  다양한 모달리티(이미지, 비디오, 텍스트 등)와 아키텍처(U-Net, DiT 등)에 대한 적용 가능성을 탐구하고, 다양한 약-강 모델 조합을 통해 성능 개선 효과를 극대화하는 방안을 연구해야 합니다.  **계산 효율성 향상**을 위한 연구도 중요한데,  W2SD 알고리즘의 계산 복잡도를 줄이면서 성능 저하를 최소화하는 방안을 모색해야 합니다.  **이론적 토대 강화**를 위해 약-강 차이를 정확하게 정량화하고,  이 차이가 생성 성능에 미치는 영향을 깊이 있게 분석하는 연구가 필요합니다.  **실제 응용 분야 확장**에 대한 연구도 중요한데,  예술 작품 생성, 디자인 지원, 의료 영상 분석 등 다양한 분야에 W2SD를 적용하고 그 효과를 평가해야 합니다.  **다른 생성 모델과의 통합**을 연구하여,  W2SD의 강점을 다른 모델들과 결합하여 시너지 효과를 창출하는 방안을 모색해야 합니다. 마지막으로,  **윤리적 함의**에 대한 고찰도 중요한데,  W2SD 기술의 오용 가능성과 사회적 영향을 면밀히 분석하여 책임감 있는 기술 개발 및 활용 방안을 모색해야 합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.00473/x2.png)

> 🔼 그림 2는 W2SD 기법의 효과를 다양한 측면에서 보여주는 정성적 결과들을 보여줍니다. 텍스트 렌더링, 개체 위치, 색상, 개체 수 세기, 개체의 공동 출현 등 여러 측면에서 기존 방법보다 향상된 결과를 보여줍니다. 부록 C.2에는 더 많은 사례가 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: The qualitative results of W2SD demonstrate the effectiveness of our method in various aspects, such as text rendering, position, color, counting, and object co-occurrence. We present more cases in Appendix C.2.
> </details>



![](https://arxiv.org/html/2502.00473/x3.png)

> 🔼 그림 3은 W2SD의 효과를 시각적으로 보여줍니다. 약한 모델과 강한 모델 사이의 차이(Δ1(t))가 강한 모델과 이상적인 모델 사이의 차이(Δ2(t))와 거의 같을 때(즉, Δ2(t) - Δ1(t)가 작을 때), W2SD의 반사 연산을 통해 수정된 잠재 변수 (~xt)가 이상적인 잠재 변수 (xgt t)에 수렴함을 보여줍니다.  즉, 약한 모델과 강한 모델 간의 차이를 이용하여 강한 모델을 이상적인 모델에 가깝게 만들 수 있음을 시각적으로 나타냅니다.  이를 통해 W2SD가 실제 데이터 분포에 가까운 영역으로 샘플링 경로를 유도하는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Visualizing the effectiveness of W2SD. When the weak-to-strong difference closely approximates the strong-to-ideal difference (e.g., Δ2⁢(t)−Δ1⁢(t)subscriptΔ2𝑡subscriptΔ1𝑡\Delta_{2}(t)-\Delta_{1}(t)roman_Δ start_POSTSUBSCRIPT 2 end_POSTSUBSCRIPT ( italic_t ) - roman_Δ start_POSTSUBSCRIPT 1 end_POSTSUBSCRIPT ( italic_t ) is small), the refined latent variable x~tsubscript~𝑥𝑡\tilde{x}_{t}over~ start_ARG italic_x end_ARG start_POSTSUBSCRIPT italic_t end_POSTSUBSCRIPT converges to the ideal latent variable xtgtsuperscriptsubscript𝑥𝑡gtx_{t}^{\mathrm{gt}}italic_x start_POSTSUBSCRIPT italic_t end_POSTSUBSCRIPT start_POSTSUPERSCRIPT roman_gt end_POSTSUPERSCRIPT.
> </details>



![](https://arxiv.org/html/2502.00473/x4.png)

> 🔼 그림 4는 1차원 가우스 분포를 따르는 데이터셋에 대한 세 가지 다른 방법(약한 모델, 강한 모델, W2SD)의 잡음 제거 과정을 보여줍니다.  데이터셋에 왼쪽 피크 데이터가 부족하여 푸른색으로 표시된 약한 모델은 오른쪽 피크 데이터만 생성하는 반면, 빨간색으로 표시된 강한 모델은 두 피크 사이의 데이터를 생성합니다. W2SD는 반사 연산자 ℳinvw(ℳs(⋅))을 활용하여 두 피크의 데이터 분포를 균형 있게 생성함으로써 데이터 분포의 균형을 맞춥니다.  이를 통해 W2SD가 약한 모델과 강한 모델의 차이를 이용하여 이상적인 모델에 가까운 결과를 생성하는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Denoising trajectories across different settings (1-D Gauss). The weak model (blue) generates only right-peak data due to missing left-peak training samples, while the strong model (red) produces data between both peaks. W2SD balances the distribution by leveraging the reflective operator ℳinvw⁢(ℳs⁢(⋅))superscriptsubscriptℳinvwsuperscriptℳs⋅\mathcal{M}_{\mathrm{inv}}^{\mathrm{w}}(\mathcal{M}^{\mathrm{s}}(\cdot))caligraphic_M start_POSTSUBSCRIPT roman_inv end_POSTSUBSCRIPT start_POSTSUPERSCRIPT roman_w end_POSTSUPERSCRIPT ( caligraphic_M start_POSTSUPERSCRIPT roman_s end_POSTSUPERSCRIPT ( ⋅ ) ).
> </details>



![](https://arxiv.org/html/2502.00473/x6.png)

> 🔼 그림 5는 2차원 가우시안 혼합 분포를 사용하여 서로 다른 설정에서의 확률 밀도 함수 등고선과 잡음 제거 과정을 시각적으로 보여줍니다. W2SD는 약한 모델과 강한 모델의 차이를 이용하여 학습된 분포를 실제 데이터 분포에 더 가깝게 만듭니다.  즉, 약한 모델은 가우시안 혼합 분포의 일부 영역만 잘 생성하고, 강한 모델은 전체 영역을 어느 정도 생성하지만 실제 분포와는 차이가 있는데, W2SD를 통해 약한 모델과 강한 모델의 차이를 이용하여 강한 모델의 생성 결과를 실제 분포에 더 근접하게 개선하는 것을 보여줍니다.  이를 통해 W2SD가 학습된 분포를 실제 데이터 분포와 더 잘 정렬시키는 효과적인 방법임을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Probability contour plot and denoising trajectories across different settings (2-D Gauss). W2SD balances the learned distribution, bringing it closer to the real data distribution
> </details>



![](https://arxiv.org/html/2502.00473/x7.png)

> 🔼 그림 6은 CIFAR-10 데이터셋의 차이를 기반으로 W2SD의 정성적 결과를 보여줍니다.  기존의 강력한 모델은 자동차 이미지를 생성하는 확률이 낮고, 약한 모델은 말 이미지 생성에 치우쳐져 불균형적인 분포를 보입니다. W2SD는 약한 모델과 강력한 모델 간의 차이를 이용하여, 강력한 모델의 생성 분포를 실제 데이터 분포에 더 가깝게 만듭니다.  즉, 자동차 이미지 생성 확률을 높이고 전체적인 생성 분포의 균형을 개선하는 효과를 보입니다. 이는 W2SD가 데이터셋의 불균형 문제를 완화하고 더욱 다양하고 균형 잡힌 이미지 생성을 가능하게 함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Qualitative results of W2SD based on dataset differences (CIFAR-10). Our method enhances the probability of generating “cars” and promote a more balanced generation distribution.
> </details>



![](https://arxiv.org/html/2502.00473/x8.png)

> 🔼 그림 7은 생성된 이미지(32x32x3)에 해당하는 CLIP 특징을 2차원 공간에 투영한 것입니다. W2SD는 '자동차'와 '말'의 표현을 효과적으로 분리합니다. (a) 강력한 모델(ℳ<sup>s</sup>)은 자동차를 생성하는 능력이 뛰어납니다. (b) 약한 모델(ℳ<sup>w</sup>)은 자동차를 거의 생성하지 못합니다. (c) W2SD는 생성 분포의 균형을 맞춰 자동차 생성 가능성을 높입니다. (d) S2WD(즉, ℳ<sup>s</sup><sub>inv</sub>(ℳ<sup>w</sup>(⋅)))는 데이터 생성의 불균형을 악화시킵니다. 이 그림은 W2SD가 약한 모델과 강력한 모델 간의 차이를 활용하여 이상적인 모델에 가까워지는 과정을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: The CLIP feature corresponding to the generated image (32×\times×32×\times×3) is projected into a 2D space. W2SD effectively disentangles the representations of “car” and “horse” in the 2D space. (a) ℳssuperscriptℳs\mathcal{M}^{\mathrm{s}}caligraphic_M start_POSTSUPERSCRIPT roman_s end_POSTSUPERSCRIPT demonstrates the ability to generate cars; (b) ℳwsuperscriptℳw\mathcal{M}^{\mathrm{w}}caligraphic_M start_POSTSUPERSCRIPT roman_w end_POSTSUPERSCRIPT can hardly generate cars; (c) W2SD balances the generation distribution, increasing the likelihood of generating cars; (d) S2WD (i.e., ℳi⁢n⁢vs⁢(ℳw⁢(⋅))superscriptsubscriptℳ𝑖𝑛𝑣𝑠superscriptℳ𝑤⋅\mathcal{M}_{inv}^{s}(\mathcal{M}^{w}(\cdot))caligraphic_M start_POSTSUBSCRIPT italic_i italic_n italic_v end_POSTSUBSCRIPT start_POSTSUPERSCRIPT italic_s end_POSTSUPERSCRIPT ( caligraphic_M start_POSTSUPERSCRIPT italic_w end_POSTSUPERSCRIPT ( ⋅ ) )) exacerbates the imbalance in data generation.
> </details>



![](https://arxiv.org/html/2502.00473/x9.png)

> 🔼 그림 8은 가중치 차이에 기반한 W2SD의 정성적 비교 결과를 보여줍니다. 왼쪽은 약한 모델, 가운데는 강한 모델, 오른쪽은 W2SD 결과입니다. W2SD는 고해상도 LoRA와 표준 모델 등 선택된 강한 모델과 약한 모델 간의 차이를 활용하여 스타일, 캐릭터, 의복 등 다양한 측면에서 개선된 결과를 제공합니다. 자세한 내용은 C.2절을 참조하세요.
> <details>
> <summary>read the caption</summary>
> Figure 8: Qualitative comparisons with weak model (left), strong model (middle) and W2SD based on weight difference (right). Our method utilizes the differences between chosen strong and weak models (e.g., high-detail LoRA vs. standard model) to deliver improvements in various dimensions, including style, character, clothing, and beyond. We provide more qualitative results in Section C.2.
> </details>



![](https://arxiv.org/html/2502.00473/x10.png)

> 🔼 그림 9는 MoE(Mixture of Experts) 메커니즘 기반 W2SD의 정량적 결과를 보여줍니다.  첫 번째 줄은 DiT-MoE-S 모델의 결과를, 두 번째 줄은 W2SD를 적용한 결과를 나타냅니다.  W2SD는 활성화 매개변수가 71M에 불과한 작은 모델에서도 성능을 크게 향상시키는 것을 보여줍니다.  즉, 기존 DiT-MoE-S 모델의 결과보다 W2SD를 적용한 결과가 훨씬 더 좋은 성능을 보임을 의미합니다. 이는 W2SD가 효과적으로 diffusion model의 추론 성능을 개선함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Quantitative Results of W2SD Based on the MoE Mechanism. The first row shows the results for DiT-MoE-S, while the second row presents W2SD. W2SD achieves significant improvements, even with small models featuring 71M activated parameters.
> </details>



![](https://arxiv.org/html/2502.00473/x11.png)

> 🔼 그림 10은 파이프라인의 차이를 기반으로 W2SD의 정성적 결과를 보여줍니다. ControlNet을 강력한 모델(ℳs), DDIM을 약한 모델(ℳw)로 설정했습니다. W2SD는 참조 이미지와의 정렬을 향상시킵니다.  즉, W2SD가 ControlNet과 같은 고급 추론 파이프라인을 사용할 때,  기존의 DDIM 방법보다 참조 이미지와 더욱 일치하는 결과를 생성함을 보여줍니다. 이는 W2SD가 다양한 모델과 파이프라인에 적용될 수 있는 유연성과 일반화 능력을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Qualitative results of W2SD based on pipeline difference. We set ControlNet as ℳssuperscriptℳs\mathcal{M}^{\mathrm{s}}caligraphic_M start_POSTSUPERSCRIPT roman_s end_POSTSUPERSCRIPT, DDIM as ℳwsuperscriptℳw\mathcal{M}^{\mathrm{w}}caligraphic_M start_POSTSUPERSCRIPT roman_w end_POSTSUPERSCRIPT. W2SD improves alignment with reference images.
> </details>



![](https://arxiv.org/html/2502.00473/x12.png)

> 🔼 그림 11은 W2SD의 성능 향상에 미치는 약한 모델과 강한 모델 간의 차이 정도를 보여줍니다. 가로축은 약한 모델과 강한 모델 간의 차이 정도를 나타내고, 세로축은 Pick-a-Pic 데이터셋에서 평균 HPS v2 점수를 나타냅니다. 강한 모델이 약한 모델보다 성능이 낮을 경우, W2SD는 오히려 성능 저하를 야기합니다.  즉, 강한 모델과 약한 모델의 성능 차이가 클수록 W2SD의 성능 향상 효과가 크다는 것을 시각적으로 보여줍니다.  이러한 결과는 W2SD의 효과적인 적용을 위해서는 적절한 강약 모델의 선택이 중요함을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: The magnitude of weak-to-strong difference is a key factor impacting the effects of improvements. The horizontal axis shows the magnitude of the weak-to-strong difference, while the vertical axis shows the average HPS v2 on the Pick-a-Pic. When ℳssuperscriptℳs\mathcal{M}^{\mathrm{s}}caligraphic_M start_POSTSUPERSCRIPT roman_s end_POSTSUPERSCRIPT is weaker than ℳwsuperscriptℳw\mathcal{M}^{\mathrm{w}}caligraphic_M start_POSTSUPERSCRIPT roman_w end_POSTSUPERSCRIPT, W2SD results in negative gains.
> </details>



![](https://arxiv.org/html/2502.00473/x13.png)

> 🔼 그림 12는 약한 모델과 강한 모델 간의 차이(weak-to-strong difference)가 W2SD 알고리즘의 성능에 미치는 영향을 보여줍니다.  약한 모델과 강한 모델 간의 차이가 0보다 클 때, 즉 강한 모델이 약한 모델보다 성능이 우수할 때 W2SD는 성능 향상(positive gains)을 가져옵니다. 이는 W2SD가 약한 모델과 강한 모델 간의 차이를 이용하여 생성 과정을 개선하기 때문입니다. 반대로, 약한 모델과 강한 모델 간의 차이가 0일 때는 W2SD가 표준 샘플링(standard sampling)과 동일하게 작동하며, 차이가 0보다 작을 때는 성능 저하(negative gains)가 발생하여 이미지 품질이 저하됩니다. 이는 W2SD 알고리즘이 강한 모델을 향상시키는 방향으로 작동하기 때문입니다.  즉, W2SD는 약한 모델과 강한 모델 간의 차이를 효과적으로 이용하여 생성 결과를 개선하지만,  이 차이가 부적절할 경우 오히려 성능이 저하될 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: When the weak-to-strong difference is greater than 0, W2SD yields positive gains. When it equals 0, the process degenerates into standard sampling. When it is less than 0, negative gains occurs, resulting in poor image quality.
> </details>



![](https://arxiv.org/html/2502.00473/x14.png)

> 🔼 그림 13은 W2SD가 표준 샘플링과 동일한 시간 비용으로 더 나은 성능을 보여준다는 것을 보여줍니다. 가로축은 이미지당 평균 생성 시간을 나타내고, 세로축은 Pick-a-Pic 데이터셋에서 HPS v2 점수를 나타냅니다. 이 그래프는 W2SD가 단순히 계산 비용이 더 많이 드는 것이 아니라, 동일한 시간 내에 더 좋은 결과를 생성함으로써 효율성을 증명한다는 것을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: W2SD outperforms standard sampling with identical time costs. The horizontal axis denotes the average generation time per image, the vertical axis represents the HPS v2 on Pick-a-Pic.
> </details>



![](https://arxiv.org/html/2502.00473/x15.png)

> 🔼 표 8은 전체 파라미터 미세 조정 전략을 기반으로 한 W2SD의 정량적 결과를 보여줍니다. W2SD는 인간의 선호도와 더 잘 맞는 결과를 생성합니다.  이 표는 Drawbench 데이터셋을 사용한 실험 결과를 나타냅니다.  구체적으로는, 다양한 지표(HPS v2, AES, PickScore, MPS)를 통해 W2SD가 기존 방법들에 비해 인간의 미적 선호도에 더 부합하는 이미지를 생성했음을 보여줍니다. 각 지표는 이미지의 미적 품질, 세부 묘사, 일관성, 주제 일관성 등을 종합적으로 평가합니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Quantitative results of W2SD based on a full parameter fine-tuning strategy. Our method generates results better aligned with human preferences. Datasets: Drawbench.
> </details>



![](https://arxiv.org/html/2502.00473/x16.png)

> 🔼 표 9는 안내 차이에 따른 W2SD의 정량적 결과를 보여줍니다. 사용된 모델은 SDXL이며, 데이터셋은 DrawBench입니다. 이 표는 다양한 평가 지표(예: HPS v2, AES, PickScore, MPS)에서 기본 SDXL 모델과 비교하여 W2SD의 성능 향상을 보여줍니다.  HPS v2는 인간의 선호도를, AES는 미적 품질을, PickScore는 이미지 품질을 종합적으로 평가하는 지표입니다. MPS는 여러 가지 측면(미적 품질, 의미 일치도, 디테일 충실도, 전반적 평가)을 고려하여 생성된 이미지의 품질을 평가하는 지표입니다.  각 지표의 수치는 W2SD를 적용했을 때 얼마나 향상되었는지를 보여주는 정량적인 증거를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Quantitative results of W2SD based on guidance difference. Model: SDXL. Datasets: DrawBench.
> </details>



![](https://arxiv.org/html/2502.00473/x17.png)

> 🔼 표 10은 사람의 선호도를 기반으로 미세 조정된 LoRA 모델을 사용한 W2SD의 정량적 결과를 보여줍니다.  이 표는 W2SD가 사람의 미적 기준과 더 잘 맞는 결과를 생성한다는 것을 보여주는 여러 지표(HPS v2, AES, PickScore, MPS)에 대한 결과를 제시합니다. Pick-a-Pic 데이터셋을 사용하여 실험을 진행했습니다.  각 지표는 개선된 성능을 보여주며, W2SD 기법이 이미지 생성 품질 향상에 효과적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Quantitative results of W2SD based on human preference LoRA model. Our method generates results better aligned with human preferences. Datasets: Pick-a-Pic.
> </details>



![](https://arxiv.org/html/2502.00473/x18.png)

> 🔼 표 11은 사람의 선호도를 기반으로 미세 조정된 LoRA 모델을 사용하여 W2SD의 정량적 결과를 보여줍니다.  이 표는 DrawBench 데이터셋을 사용하여 W2SD가 생성된 이미지의 품질을 향상시키고 사람의 미적 기준에 더 부합하는 결과를 생성하는지 평가한 결과를 보여줍니다.  구체적으로, W2SD는 다양한 지표(HPS v2, AES, PickScore, MPS)에서 기준 모델보다 성능이 향상되었음을 보여줍니다. 이는 W2SD 방법론이 다양한 이미지 생성 작업에서 사람의 선호도를 향상시키는 데 효과적임을 시사합니다.  각 지표는 이미지의 미적 품질, 의미 일관성, 세부 묘사 등 다양한 측면을 평가합니다.
> <details>
> <summary>read the caption</summary>
> Table 11: Quantitative results of W2SD based on human preference LoRA model. Our method generates results better aligned with human preferences. Datasets: DrawBench.
> </details>



![](https://arxiv.org/html/2502.00473/x19.png)

> 🔼 그림 14는 가중치 차이를 기반으로 한 W2SD의 정성적 결과를 보여줍니다. 여기서 xlMoreArtFullV1을 강력한 모델로, SDXL을 약한 모델로 선택했습니다. W2SD는 사람의 선호도 성능을 효과적으로 향상시킬 수 있음을 보여줍니다. 각 열은 약한 모델, 강력한 모델 및 W2SD의 결과를 보여줍니다.  각 행은 다양한 프롬프트를 나타내며, W2SD가 세부 사항을 더 잘 캡처하고, 더욱 사실적인 결과를 생성하는 것을 보여줍니다. 이를 통해 W2SD가  세부 사항과 정확성 측면에서 약한 모델보다 우수한 성능을 제공한다는 것을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: Qualitative results of W2SD based on weight differences (human preference). Here we select xlMoreArtFullV1 as the strong model and SDXL as the weak model. W2SD can effectively enhance the performance of human preference.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | DINO ↑ | CLIP-I ↑ | CLIP-T ↑ |
|---|---|---|---|
| SD1.5 | 27.47 | 52.08 | 20.14 |
| Personalized LoRA | 48.03 | 64.37 | 25.99 |
| **W2SD** | **51.58** | **68.04** | **27.66** |{{< /table-caption >}}
> 🔼 표 2는 개인화된 LoRA 모델을 기반으로 W2SD의 정량적 결과를 보여줍니다. 여기서, 약한 모델 ℳ𝑤(SD1.5)와 강한 모델 ℳ𝑠(SD1.5 + LoRA) 간의 가중치 차이는 생성된 결과를 더욱 개인화된 방향으로 편향시킵니다.  즉, SD1.5 모델에 LoRA를 추가하여 특정 스타일이나 특징을 강화한 모델을 강한 모델로 사용하고, 기본 SD1.5 모델을 약한 모델로 사용하여 두 모델 간의 차이를 이용해 생성 결과의 개인화 수준을 높였음을 보여줍니다. 표에는 다양한 평가 지표에 따른 성능 향상이 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Quantitative results of W2SD based on personalized LoRA model. Here, the weight difference between ℳwsuperscriptℳ𝑤\mathcal{M}^{w}caligraphic_M start_POSTSUPERSCRIPT italic_w end_POSTSUPERSCRIPT (SD1.5) and ℳssuperscriptℳ𝑠\mathcal{M}^{s}caligraphic_M start_POSTSUPERSCRIPT italic_s end_POSTSUPERSCRIPT (SD1.5 +LoRA) biases the generated results towards a more personalized direction.
> </details>

{{< table-caption >}}
| Method | IS ↑ | FiD ↓ | AES ↑ | HPS v2 ↑ |
|---|---|---|---|---|
| DiT-MoE-S | 45.4437 | 15.1032 | 4.4755 | 20.0486 |
| **W2SD** | **55.5341** | **9.1001** | **4.5053** | **22.3225** |{{< /table-caption >}}
> 🔼 이 표는 W2SD 기법을 Mixture of Experts (MoE) 메커니즘에 적용했을 때의 정량적 결과를 보여줍니다.  ImageNet 50K 데이터셋을 사용하여, Inception Score (IS), Fréchet Inception Distance (FID),  Average Embedding Similarity (AES),  Human Preference Score version 2 (HPS v2) 지표를 통해 W2SD의 성능을 평가합니다.  표에는 W2SD를 적용한 모델과 적용하지 않은 모델의 결과가 비교되어 있으며, 각 지표에 따른 성능 향상 정도를 확인할 수 있습니다.  MoE 메커니즘을 활용하여 약한 모델과 강한 모델을 조합하여 W2SD가 성능 개선에 효과적임을 보여주는 실험 결과입니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Quantitative results of W2SD based on MoE Mechanism. Datasets: ImageNet 50K.
> </details>

{{< table-caption >}}
| Method | HPS v2 ↑ | AES ↑ | PickScore ↑ | MPS ↑ |
|---|---|---|---|---|
| SD1.5 | 24.9558 | 5.5003 | 20.1368 | 42.1101 |
| **W2SD** | **25.5069** | **5.5073** | **20.2443** | **57.8903** |
| SDXL | 29.8701 | 6.0939 | 21.6487 | 43.9425 |
| **W2SD** | **31.2020** | **6.0970** | **21.7980** | **56.0608** |{{< /table-caption >}}
> 🔼 표 4는 안내 차이를 기반으로 한 W2SD의 정량적 결과를 보여줍니다. 사용된 모델은 SDXL이며, 데이터셋은 Pick-a-Pic입니다. 이 표는 약한 모델과 강한 모델 간의 안내 차이를 활용하여 이미지 생성 품질을 향상시키는 W2SD의 효과를 다양한 지표(HPS v2, AES, PickScore, MPS)를 사용하여 정량적으로 평가한 결과를 보여줍니다. 각 지표는 인간의 선호도, 미적 품질, 프롬프트 충실도 등을 반영합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Quantitative results of W2SD based on guidance difference. Model: SDXL. Datasets: Pick-a-Pic.
> </details>

{{< table-caption >}}
| Prompt Type | HPS v2 ↑ | AES ↑ | PickScore ↑ | MPS ↑ |
|---|---|---|---|---|
| Raw Prompt | 25.3897 | 5.4454 | 20.7144 | - |
| Refined Prompt | 28.5698 | 5.7714 | 21.6350 | 45.7719 |
| **W2SD** | **29.4023** | **5.8812** | **21.8053** | **54.2275** |{{< /table-caption >}}
> 🔼 표 5는 W2SD의 성능을 평가하기 위해 GenEval 데이터셋을 사용하여 수행된 실험 결과를 보여줍니다.  모델은 SDXL을 사용하였으며,  약한 모델과 강한 모델 간의 의미론적 차이를 이용하여 W2SD 기법을 적용했습니다.  표에는 W2SD를 적용했을 때와 적용하지 않았을 때의 Human Preference Score (HPS v2), Aesthetic Score (AES), PickScore, MPS 등 다양한 지표를 비교하여 W2SD의 효과를 정량적으로 분석한 결과가 제시되어 있습니다.  실험 결과는 약한 모델과 강한 모델 간의 의미론적 차이를 이용하는 것이 생성 품질 향상에 효과적임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Quantitative results of W2SD based on semantic differences between prompts. Model: SDXL. Datasets: GenEval.
> </details>

{{< table-caption >}}
| Weight Difference | Condition Difference | HPS v2 ↑ | Winning Rate ↑ |
|---|---|---|---| 
| × | × | 31.6412 | - |
| × | ✓ | 32.8217 | 84% |
| ✓ | × | 32.0992 | 76% |
| ✓ | ✓ | **32.9623** | **90%** |{{< /table-caption >}}
> 🔼 표 6은 서로 다른 모델 간의 차이점이 누적되어 개선 효과를 가져올 수 있음을 보여줍니다.  Pick-a-Pic 데이터셋을 사용한 실험 결과를 보여주는 표이며, 가중치 차이(Weight Difference)와 조건 차이(Condition Difference)를 결합하여 얻은 결과를 비교 분석합니다.  가중치 차이만 사용했을 때보다 가중치 차이와 조건 차이를 모두 사용했을 때 HPS v2 지표가 더 높아지는 것을 확인할 수 있습니다.  즉, 모델의 차이점을 다양하게 조합하여 사용하면 성능 향상 효과를 더욱 높일 수 있음을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: The improvements effects from different model differences can be cumulative. Datasets: Pick-a-Pic.
> </details>

{{< table-caption >}}
| Model Difference | \mathcal{M}^{\mathrm{s}} | \mathcal{M}^{\mathrm{w}} | Results |
|---|---|---|---| 
| Weight Difference | Finetune Mechanism | SDXL/SD1.5 | Tables 1 and 9 |
|  | LoRA Mechanism | SDXL/SD1.5 | Tables 2, 11 and 11 |
|  | Strong Experts (MoE) | Weak experts (MoE) | Table 3 |
| Condition Difference | High CFG | Low CFG | Tables 4 and 9 |
|  | Refined Prompt | Raw Prompt | Table 5 |
| Sampling Pipeline Difference | ControlNet | Standard Pipeline (DDIM) | Figure 10 |
|  | IP-Adapter | Standard Pipeline (DDIM) | Figure 17 |{{< /table-caption >}}
> 🔼 표 7은 모델 간의 차이가 생성 결과 향상에 미치는 영향을 보여줍니다. 가중치 차이, 조건 차이, 샘플링 파이프라인 차이 등 다양한 유형의 모델 차이가 생성 결과에 다른 방향으로 영향을 미친다는 것을 보여줍니다. 각 유형의 모델 차이에 따라 어떤 강점과 약점 모델을 선택해야 하는지, 그리고 어떤 방식으로 사용해야 효과적인지에 대한 정보가 담겨 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Different types of model differences lead to improvements effects in different directions.
> </details>

{{< table-caption >}}
| Method | HPS v2 ↑ | AES ↑ | PickScore ↑ | MPS ↑ |
|---|---|---|---|---|
| SD1.5 | 25.3601 | 5.2023 | 21.0519 | - |
| DreamShaper | 28.7845 | 5.7047 | 21.8522 | 47.8813 |
| **W2SD** | **28.7901** | **5.7847** | **21.9057** | **52.1192** |
| SDXL | 28.5536 | **5.4946** | 22.2464 | - |
| Juggernaut-XL | 28.9085 | 5.3455 | 22.4906 | 47.5648 |
| **W2SD** | **29.3246** | 5.4261 | **22.5803** | **52.4358** |{{< /table-caption >}}
> 🔼 표 12는 AnimateDiff 모델과 VBench 데이터셋을 사용하여 비디오 생성 작업에서 W2SD의 정량적 결과를 보여줍니다.  W2SD는 주제 일관성, 배경 일관성, 동작 부드러움, 역동성, 미적 품질, 이미지 품질 등 여러 측면에서 성능 향상을 보여줍니다.  하지만 일부 측면(예: 동작 부드러움)에서는 SDXL의 고유한 한계로 인해 성능 저하가 발생할 수 있습니다. 이 표는 W2SD의 효과를 객관적으로 평가하는 데 도움이 되는 다양한 지표를 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 12: Quantitative results of W2SD on the video generation task. Model: AnimateDiff. Datasets: VBench.
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