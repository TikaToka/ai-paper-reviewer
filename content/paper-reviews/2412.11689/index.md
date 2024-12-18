---
title: "Just a Simple Transformation is Enough for Data Protection in Vertical Federated Learning"
summary: "간단한 변환만으로 수직 연합 학습에서 데이터 보호 가능."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Machine Learning", "Federated Learning", "🏢 MIPT",]
showSummary: true
date: 2024-12-16
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.11689 {{< /keyword >}}
{{< keyword icon="writer" >}} Andrei Semenov et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-17 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.11689" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.11689" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/just-a-simple-transformation-is-enough-for" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

**수직 연합 학습(VFL)**은 개인정보를 보호하면서 딥러닝 모델의 협업 훈련을 가능하게 하지만, 악의적인 공격에 취약한 부분이 여전히 존재합니다. 특히 입력 데이터 유출을 목표로 하는 **기능 재구성 공격**은 심각한 위협입니다.  기존 연구는 CNN 기반 모델에 집중했지만, 본 연구는 MLP 기반 모델의 개인정보 보호 가능성에 주목합니다.

본 연구는 기능 재구성 공격이 **사전 데이터 분포에 대한 지식 없이는 성공할 수 없음**을 이론적으로 주장합니다. 따라서 **MLP 기반 모델**에서 Model Inversion 및 Feature-space Hijacking 공격이 실패함을 실험적으로 입증하여 **추가 방어 없이도** 개인정보 보호가 가능함을 보여줍니다. 또한, **(준)직교 변환**을 사용하여 **데이터 및 가중치 초기화**를 통해 서버 관점에서 동일한 훈련 프로세스를 유지하면서 입력 데이터를 보호하는 방법을 제시합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 사전 데이터 분포에 대한 지식 없이는 기능 재구성 공격이 성공할 수 없음. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 간단한 모델 아키텍처 변환으로 VFL 중 입력 데이터 보호에 큰 영향을 미칠 수 있음. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} MLP 기반 모델은 최첨단 기능 재구성 공격에 대해 내성이 있음 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**개인정보 보호 강화를 위한 간단한 변환**이 수직 연합 학습에 미치는 영향을 강조합니다. 본 연구는 **MLP 기반 모델을 사용하여 기능 재구성 공격을 방어**하는 방법을 제시하고, 프라이버시 향상과 정확도 유지 사이의 균형을 이루는 방법에 대한 **새로운 관점**을 제시합니다. 또한, 본 연구는 기존 공격의 한계를 드러내고 **향후 개인정보 보호 연구를 위한 새로운 방향**을 제시합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.11689/x1.png)

> 🔼 이 그림은 MNIST 데이터셋을 사용하여 UnSplit 공격의 결과를 보여줍니다. UnSplit 공격은 Split Learning에서 클라이언트 측 모델의 복제본을 훈련하여 원본 데이터를 재구성하는 것을 목표로 하는 모델 역전 공격의 한 유형입니다. 그림의 윗부분에는 원본 이미지가 표시됩니다. 가운데 부분은 CNN 기반 클라이언트 모델에 대한 UnSplit 공격 결과를 보여줍니다. 마지막 부분은 MLP 기반 클라이언트 모델에 대한 공격 결과를 보여줍니다. CNN 기반 모델의 경우 공격이 원본 이미지를 어느 정도 재구성하는 데 성공한 반면 MLP 기반 모델의 경우에는 공격이 실패했음을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Results of UnSplit attack on MNIST. (Top): Original images. (Middle): CNN-based client model. (Bottom): MLP-based client model.
> </details>





{{< table-caption >}}
| Dataset | Model | MSE \\(\[\]mathcal{X}\\) | MSE \\(\[\]mathcal{Z}\\) | FID | Acc% |
|---|---|---|---|---|---|
| MNIST | MLP-based | 0.27 | 3e-8 | 394 | 98.42 |
| MNIST | CNN-based | 0.05 | 2e-2 | 261 | 98.68 |
| F-MNIST | MLP-based | 0.19 | 4e-5 | 361 | 88.31 |
| F-MNIST | CNN-based | 0.37 | 4e-2 | 169 | 89.23 |
| CIFAR-10 | MLP-Mixer | 1.398 | 6e-6 | 423 | 89.29 |
| CIFAR-10 | CNN-based | 0.056 | 4e-3 | 455 | 93.61 |{{< /table-caption >}}

> 🔼 이 표는 UnSplit 공격에 대한 MNIST, F-MNIST 및 CIFAR-10 데이터 세트의 재구성 손실 값(MSE 및 FID)과 최종 정확도(Acc%)를 보여줍니다. MLP 기반 모델과 CNN 기반 모델의 결과를 비교하여 MLP 기반 모델의 이미지 복구 실패를 보여줍니다. 표에서 MSE X는 원본 이미지와 재구성된 이미지 간의 차이를 나타내고, MSE Z는 활성화 간의 차이, FID는 재구성 품질을 나타내며, Acc%는 훈련된 모델의 최종 정확도를 나타냅니다. 특히, 잘못 재구성된 이미지의 경우에도 MSE Z 값이 매우 낮다는 점에 유의해야 합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: UnSplit attack on MNIST, F-MNIST, and CIFAR-10 datasets.
> </details>





### In-depth insights


#### VFL Privacy Gaps
**VFL(수직 연합 학습)은 개인정보 보호 강화를 목표로 하지만, 여전히 공격에 취약한 부분이 존재합니다.** 특히, 악의적인 참여자가 모델 아키텍처, 매개변수, 중간 출력값(활성화) 등에 접근하여 입력 데이터를 재구성하거나 레이블을 추론하는 공격이 가능합니다. 이러한 공격은 데이터 분포에 대한 사전 지식을 활용할 경우 성공 가능성이 높아집니다. 따라서 VFL 시스템 설계 시 데이터 분포에 대한 사전 정보를 최소화하고, 모델 아키텍처를 신중하게 선택해야 합니다. 또한, 차분 프라이버시(DP) 메커니즘과 같은 방어 전략을 적용하여 개인정보 보호 수준을 강화하는 것이 중요합니다. 궁극적으로, VFL의 개인정보 보호 수준을 높이려면 공격자의 역량을 제한하고 방어 메커니즘을 강화하는 노력이 필요합니다.

#### Transformation as Defense
**변환 기반 방어**는 데이터 및 모델 가중치에 **직교 변환**을 적용하여 특징 재구성 공격으로부터 VFL 모델을 보호하는 데 중점을 둡니다. 이러한 변환은 서버 측에서 모델 학습 프로토콜을 변경하지 않으므로 **데이터 배포에 대한 사전 정보 없이는 특징 재구성이 불가능**합니다. 따라서 공격자가 원본 데이터를 재구성하기 어렵게 만듭니다. 또한 **MLP 기반 아키텍처가 CNN보다 이러한 공격에 더 강력**하다는 것을 시사합니다. MLP의 **dense layer가 특징 공간을 난독화**하여 재구성 공격의 성공 가능성을 줄입니다. **변환은 훈련된 모델의 정확도에 큰 영향을 미치지 않으면서 강력한 방어 메커니즘을 제공**합니다. 이는 추가적인 방어 프레임워크가 필요하지 않을 수 있음을 나타냅니다.

#### MLP-Based Model Robustness
**MLP 기반 모델은 feature 재구성 공격에 강인함**을 보여줍니다. 특히 CNN 기반 모델에서 성공적인 UnSplit 및 FSHA 공격은 MLP 기반 모델에서는 실패합니다. 이는 MLP 아키텍처의 고유한 특성, 즉 완전히 연결된 layer가 많은 것과 컨볼루션 layer가 없는 것 때문입니다. 덕분에 공격자가 입력 데이터의 사전 분포에 대한 지식 없이 feature를 재구성하기가 어렵습니다. 이러한 **견고성은 추가적인 방어 메커니즘 없이 달성**되므로 계산 오버헤드가 발생하지 않습니다. 따라서 MLP 기반 모델은 **수직 연합 학습에서 강력한 개인 정보 보호**를 제공합니다. 하지만 다른 공격 벡터에 대한 취약성 가능성을 배제할 수는 없으므로 향후 연구에서는 다른 공격 유형에 대한 MLP 모델의 견고성을 평가해야 합니다.

#### Prior Knowledge Limits Attacks
**사전 지식이 공격자의 능력을 제한한다**는 주장은 적대적 공격의 맥락에서 중요한 의미를 지닙니다. 이는 공격자가 대상 시스템, 데이터 또는 사용자에 대한 특정 정보에 접근할 수 있다고 가정하는 표적 공격과 대조적입니다. 사전 지식을 제한함으로써 공격의 범위를 좁히고 방어자가 공격 표면을 줄이는 데 집중할 수 있습니다. 이러한 제한은 공격자가 악용할 수 있는 취약점의 수를 줄여 **전반적인 보안 태세를 강화**할 수 있습니다. 또한 사전 지식 제한은 실제 공격 시나리오를 더 잘 반영하여 **보다 현실적인 평가**를 가능하게 합니다. 이는 공격자가 무한한 자원을 보유하고 있다는 비현실적인 가정에 기반한 평가보다 **더 정확한 시스템의 복원력 측정**을 제공합니다. 또한 사전 지식의 제한 사항을 고려하면 다양한 공격 유형과 그 영향을 이해하는 데 도움이 되어 **방어 전략 개발**에 도움이 됩니다.

#### Beyond MSE: FID Evaluation
**MSE는 이미지 재구성 공격 방어의 질적 평가에 적합하지 않을 수 있습니다.** 특히 복잡한 이미지의 경우 MSE는 재구성된 이미지의 품질 저하를 충분히 반영하지 못합니다. 이 연구에서는 **FID(Fréchet Inception Distance)를 사용하여 재구성 공격에 대한 방어의 충실도를 인간의 인식에 맞춰 평가합니다.** FID는 원본 이미지와 재구성된 이미지 간의 분포 차이를 측정하여 **인간이 인지하는 이미지 유사성을 더 잘 반영합니다.** 따라서 **FID는 MSE에 비해 재구성 공격의 영향을 더 정확하게 평가할 수 있습니다.** 실험 결과, CIFAR-10 데이터셋에서 CNN 아키텍처의 경우 재구성된 이미지의 품질이 더 좋음에도 불구하고 MSE 값이 더 높게 나타났습니다. 이는 MSE가 배경 픽셀 값의 차이에 민감하게 반응하기 때문입니다. **이러한 결과는 FID가 이미지 재구성 공격 방어 평가에 더 적합한 지표임을 시사합니다.**


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.11689/x2.png)

> 🔼 이 그림은 F-MNIST 데이터셋에 대한 UnSplit 공격 결과를 보여줍니다. 맨 위에는 원본 이미지가, 가운데에는 CNN 기반 클라이언트 모델을 사용한 공격 결과가, 맨 아래에는 MLP 기반 클라이언트 모델을 사용한 공격 결과가 표시됩니다. MLP 기반 모델을 사용했을 때, CNN 기반 모델과 비교하여 이미지 재구성 품질이 현저히 낮다는 것을 알 수 있습니다. 이는 MLP 기반 모델이 UnSplit 공격에 더 강력한 방어력을 제공함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Results of UnSplit attack on F-MNIST. (Top): Original images. (Middle): CNN-based client model. (Bottom): MLP-based client model.
> </details>



![](https://arxiv.org/html/2412.11689/x3.png)

> 🔼 이 그림은 MNIST 데이터셋에 대한 Feature-space Hijacking Attack(FSHA) 결과를 보여줍니다. 위쪽에는 원본 이미지가, 중간에는 CNN 기반 클라이언트 모델을 사용한 공격 결과가, 아래쪽에는 MLP 기반 클라이언트 모델을 사용한 공격 결과가 나타나 있습니다. 그림에서 볼 수 있듯이, CNN 기반 모델의 경우 공격자가 원본 이미지를 재구성하는 데 성공한 반면, MLP 기반 모델의 경우 공격이 실패했습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Results of FSHA attack on MNIST. (Top): Original images. (Middle): CNN-based client model. (Bottom): MLP-based client model.
> </details>



![](https://arxiv.org/html/2412.11689/x4.png)

> 🔼 이 그림은 F-MNIST 데이터셋에 대한 Feature-space Hijacking Attack(FSHA) 결과를 보여줍니다. 맨 위에는 원본 이미지가, 중간에는 CNN 기반 클라이언트 모델을 사용한 FSHA 공격 결과가, 맨 아래에는 MLP 기반 클라이언트 모델을 사용했을 때의 FSHA 공격 결과가 나타나 있습니다. MLP 기반 모델을 사용했을 경우, 공격자가 원본 이미지를 재구성하는데 실패한 것을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Results of FSHA attack on F-MNIST. (Top): Original images. (Middle): CNN-based client model. (Bottom): MLP-based client model.
> </details>



![](https://arxiv.org/html/2412.11689/x5.png)

> 🔼 이 그림은 Feature-space Hijacking Attack (FSHA)에 대한 엔코더-디코더 오류와 재구성 오류를 보여줍니다. FSHA 공격은 공격자가 잘 알려진 데이터셋을 사용하여 Split Learning 과정에서 클라이언트 모델을 조작하는 공격입니다. 엔코더-디코더 오류는 공격자가 공개 데이터셋에서 데이터를 재구성하는 능력을 나타내며, 재구성 오류는 공격자가 클라이언트의 개인 데이터를 재구성하는 능력을 나타냅니다. 그래프는 두 종류의 아키텍처에 대해 FSHA 공격이 수행되었을 때의 오류를 보여주고 있습니다: CNN 기반 클라이언트 모델과 MLP 기반 클라이언트 모델. MNIST와 F-MNIST 데이터셋 모두에 대해 MLP 기반 클라이언트 모델을 사용하는 경우 재구성 오류가 훨씬 높다는 것을 알 수 있습니다. 이는 MLP 기반 모델이 FSHA 공격에 더 강력함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Encoder-decoder error and Reconstruction error for FSHA attack
> </details>



![](https://arxiv.org/html/2412.11689/x6.png)

> 🔼 이 그림은 CIFAR-10 데이터셋에 대한 UnSplit 공격 결과를 보여줍니다. 상단에는 원본 이미지가, 중간에는 CNN 기반 클라이언트 모델을 사용한 공격 결과가, 하단에는 MLP-Mixer 클라이언트 모델을 사용한 공격 결과가 표시됩니다. CNN 기반 모델의 경우, 공격으로 재구성된 이미지가 원본 이미지와 매우 유사한 것을 볼 수 있습니다. 반면 MLP-Mixer 모델의 경우, 재구성된 이미지는 원본 이미지와 상당히 다르며, 공격이 성공적이지 못했음을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Results of UnSplit attack on CIFAR-10. (Top): Original images. (Middle): CNN-based client model. (Bottom): MLP-Mixer client model.
> </details>



![](https://arxiv.org/html/2412.11689/x7.png)

> 🔼 이 그림은 초기화에 따라 비볼록 함수 f(x) = x² + 6sin²(x)를 최적화할 때 Adam 최적화 알고리즘이 지역 최솟값에 갇힐 수 있음을 보여줍니다.   파란색 선은 초기값 W = (1.915 + √2 * 0.6, 0), X = (1, 0)에서 시작하여 최적화를 진행한 결과를, 주황색 선은 데이터와 가중치를 직교 변환한 초기값 U * W, U * X에서 시작하여 최적화를 진행한 결과를 나타냅니다. U는 45도 회전 행렬입니다.  그림에서 볼 수 있듯이, Adam은 데이터와 가중치를 회전하기 전에는 전역 최솟값 0으로 수렴하지만, 회전한 후에는 지역 최솟값에 갇히게 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: While optimizing the non-convex function f⁢(x)𝑓𝑥f(x)italic_f ( italic_x ), Adam can get stuck in the local minima in depence on the initialization.
> </details>



![](https://arxiv.org/html/2412.11689/x8.png)

> 🔼 이 그림은 UnSplit 공격에 대한 각 클래스별 MSE를 보여줍니다. 첫 번째 행은 CIFAR-10 데이터셋에 대한 MLP-Mixer 및 CNN 기반 모델의 결과를, 두 번째 행은 F-MNIST 데이터셋에 대한 MLP 및 CNN 기반 모델의 결과를, 세 번째 행은 MNIST 데이터셋에 대한 MLP 및 CNN 기반 모델의 결과를 나타냅니다.  이 그림은 클라이언트 측 모델 아키텍처가 MLP 기반일 때 UnSplit 공격이 재구성된 데이터와 원본 데이터 간의 MSE 차이가 CNN 기반 모델보다 훨씬 크다는 것을 보여 MLP 기반 모델이 UnSplit 공격에 더 강력함을 시사합니다. 또한, 잘 재구성된 이미지의 경우에도, MLP 기반 모델의 Cut Layer 이전 활성화 간의 MSE가 CNN 기반 모델보다 훨씬 낮다는 것을 알 수 있습니다. 이는 Cut Layer Lemma 3을 반영하는 것으로, Cut Layer 이전 활성화에 대한 사전 지식이 없으면 서버가 Cut Layer 이전 활성화를 정확하게 재구성하지 못한다는 것을 의미합니다. Cut Layer MSE와 재구성 MSE의 차이는 CNN 기반 모델보다 MLP 기반 모델에서 훨씬 더 큽니다. 이는 서버가 Cut Layer 활성화를 재구성하는 데 어려움이 있음을 보여줍니다. 이 그림은 또한 데이터셋의 어떤 클래스가 특징 재구성 공격에 더 '민 sensitive'한지에 대한 통찰력을 제공합니다. 이러한 결과를 방어 메커니즘과 결합하면 공격자의 능력을 크게 약화시키거나 비 라벨 당사자가 데이터 세트의 특정 클래스의 방어에 집중할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: MSE across different classes for the UnSplit attack. (Top row): CIFAR-10 – MLP-Mixer and CNN-based models. (Middle row): F-MNIST – MLP and CNN-based models. (Bottom row): MNIST – MLP and CNN-based models.
> </details>



![](https://arxiv.org/html/2412.11689/x9.png)

> 🔼 이 그림은 MNIST 데이터셋에 대한 UnSplit 공격 결과를 보여줍니다. UnSplit 공격은 Split Learning에서 클라이언트 측 모델의 입력 데이터를 재구성하는 것을 목표로 하는 공격 기법입니다. 그림은 원본 이미지(상단), CNN 기반 클라이언트 모델을 사용한 공격 결과(중간), SmallMLP 클라이언트 모델을 사용한 공격 결과(하단)를 비교하여 보여줍니다. SmallMLP 모델은 CNN 모델보다 매개변수 수가 적지만 UnSplit 공격에 더 강력한 방어력을 보여줍니다. 즉, SmallMLP 모델을 사용했을 때, CNN 기반 모델에 비해 공격자가 원본 이미지를 재구성하는 데 실패한 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Results of UnSplit attack on MNIST. (Top): Original images. (Middle): CNN-based client model. (Bottom): SmallMLP client model.
> </details>



![](https://arxiv.org/html/2412.11689/x10.png)

> 🔼 이 그림은 F-MNIST 데이터셋에 대한 UnSplit 공격 결과를 보여줍니다. 맨 위에는 원본 이미지가, 중간에는 CNN 기반 클라이언트 모델을 사용한 공격 결과가, 맨 아래에는 SmallMLP 클라이언트 모델을 사용한 공격 결과가 표시됩니다. SmallMLP 모델을 사용한 경우, CNN 기반 모델에 비해 재구성된 이미지의 품질이 떨어집니다. 이는 MLP 기반 모델이 특징 재구성 공격에 더 강력함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Results of UnSplit attack on F-MNIST. (Top): Original images. (Middle): CNN-based client model. (Bottom): SmallMLP client model.
> </details>



![](https://arxiv.org/html/2412.11689/x11.png)

> 🔼 이 그림은 MNIST 데이터셋에 대한 FSHA(Feature-space Hijacking Attack)의 결과를 보여줍니다. 맨 위에는 원본 이미지가, 중간에는 CNN 기반 클라이언트 모델을 사용한 FSHA 결과가, 맨 아래에는 SmallMLP 클라이언트 모델을 사용한 FSHA 결과가 표시됩니다. SmallMLP 모델을 사용한 경우, 공격자가 원본 이미지를 재구성하지 못하는 것을 확인할 수 있습니다. 이는 MLP 기반 모델이 특징 재구성 공격에 더 강력한 방어력을 제공함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Results of FSHA attack on MNIST. (Top): Original images. (Middle): CNN-based client model. (Bottom): SmallMLP client model.
> </details>



![](https://arxiv.org/html/2412.11689/x12.png)

> 🔼 이 그림은 F-MNIST 데이터셋에 대한 Feature-space Hijacking Attack(FSHA) 결과를 보여줍니다. 상단에는 원본 이미지가, 중간에는 CNN 기반 클라이언트 모델을 사용한 재구성 결과, 하단에는 SmallMLP 클라이언트 모델을 사용한 재구성 결과가 표시됩니다. SmallMLP 모델을 사용했을 때, 공격자가 원본 이미지를 재구성하는 데 실패한 것을 알 수 있습니다. 이는 MLP 기반 모델이 FSHA와 같은 feature 재구성 공격에 더 강력하다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Results of FSHA attack on F-MNIST. (Top): Original images. (Middle): CNN-based client model. (Bottom): SmallMLP client model.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| # Parameters / Model | MLP | MLP-Mixer | CNN | SmallMLP |
|---|---|---|---|---|
| # | 2,913,290 | 146,816 | 45,278 | 7,850 |{{< /table-caption >}}
> 🔼 이 표는 여러 모델들의 매개변수 개수를 보여줍니다. SmallMLP 모델은 CNN 기반 모델과 매개변수 개수가 비슷하지만 정확도는 낮도록 설계되었습니다. 표에서 보듯이 SmallMLP의 매개변수는 CNN보다 훨씬 적습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Number of parameters for different models across.
> </details>

{{< table-caption >}}
| Split Layer # | Without noise | With Noise |
|---|---|---|
| Ref. | <img alt="[Uncaptioned image]" src="https://arxiv.org/html/2412.11689/x36.png" width="349" height="42"/> | <img alt="[Uncaptioned image]" src="https://arxiv.org/html/2412.11689/x37.png" width="349" height="42"/> |
| 1 | <img alt="[Uncaptioned image]" src="https://arxiv.org/html/2412.11689/x38.png" width="349" height="42"/> | <img alt="[Uncaptioned image]" src="https://arxiv.org/html/2412.11689/x39.png" width="349" height="42"/> |
| 2 | <img alt="[Uncaptioned image]" src="https://arxiv.org/html/2412.11689/x40.png" width="349" height="42"/> | <img alt="[Uncaptioned image]" src="https://arxiv.org/html/2412.11689/x41.png" width="349" height="42"/> |
| 3 | <img alt="[Uncaptioned image]" src="https://arxiv.org/html/2412.11689/x42.png" width="349" height="42"/> | <img alt="[Uncaptioned image]" src="https://arxiv.org/html/2412.11689/x43.png" width="349" height="42"/> |
| 4 | <img alt="[Uncaptioned image]" src="https://arxiv.org/html/2412.11689/x44.png" width="349" height="42"/> | <img alt="[Uncaptioned image]" src="https://arxiv.org/html/2412.11689/x45.png" width="349" height="42"/> |
| 5 | <img alt="[Uncaptioned image]" src="https://arxiv.org/html/2412.11689/x46.png" width="349" height="42"/> | <img alt="[Uncaptioned image]" src="https://arxiv.org/html/2412.11689/x47.png" width="349" height="42"/> |
| 6 | <img alt="[Uncaptioned image]" src="https://arxiv.org/html/2412.11689/x48.png" width="349" height="42"/> | <img alt="[Uncaptioned image]" src="https://arxiv.org/html/2412.11689/x49.png" width="349" height="42"/> |
| Ref. | <img alt="[Uncaptioned image]" src="https://arxiv.org/html/2412.11689/x50.png" width="349" height="42"/> | <img alt="[Uncaptioned image]" src="https://arxiv.org/html/2412.11689/x51.png" width="349" height="42"/> |
| 1 | <img alt="[Uncaptioned image]" src="https://arxiv.org/html/2412.11689/x52.png" width="349" height="42"/> | <img alt="[Uncaptioned image]" src="https://arxiv.org/html/2412.11689/x53.png" width="349" height="42"/> |
| 2 | <img alt="[Uncaptioned image]" src="https://arxiv.org/html/2412.11689/x54.png" width="349" height="42"/> | <img alt="[Uncaptioned image]" src="https://arxiv.org/html/2412.11689/x55.png" width="349" height="42"/> |{{< /table-caption >}}
> 🔼 이 표는 MNIST, F-MNIST 및 CIFAR-10 데이터셋에 대한 다양한 Cut Layer에 대해 노이즈를 추가하거나 추가하지 않고 추정된 입력을 보여줍니다. 'Ref.' 행은 실제 입력을 표시하고 다음 행은 다양한 분할 깊이에 대한 공격 결과를 표시합니다. 서로 다른 데이터셋에 대해 다음과 같은 노이즈 분산을 사용했습니다. MNIST의 경우 σ=1.6, F-MNIST의 경우 σ=2.6, CIFAR-10의 경우 σ=0.25입니다. CIFAR-10의 σ에 대한 이론적 값은 7.1이지만 신경망 학습 문제로 인해 낮추기로 결정했습니다. 이 표는 Differential Privacy 방어가 UnSplit Model Inversion(MI) 공격에 대해 완벽하지는 않지만 어느 정도 효과가 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Estimated inputs with and without adding noise for various Cut Layers for the MNIST, F-MNIST, and CIFAR-10 datasets. The 'Ref.' row display the actual inputs, and the next rows display the attack results for different split depths. We took the following noise variance for different datasets: σ=1.6𝜎1.6\sigma=1.6italic_σ = 1.6 for MNIST, σ=2.6𝜎2.6\sigma=2.6italic_σ = 2.6 for F-MNIST, σ=0.25𝜎0.25\sigma=0.25italic_σ = 0.25 for CIFAR-10. Note that theoretical value of σ𝜎\sigmaitalic_σ for CIFAR-10 is 7.17.17.17.1, but we decided to lower it due to neural network learning issues.
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