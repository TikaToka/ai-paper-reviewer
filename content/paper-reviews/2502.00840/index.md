---
title: "Activation Approximations Can Incur Safety Vulnerabilities Even in Aligned LLMs: Comprehensive Analysis and Defense"
summary: "활성화 함수 근사는 LLM의 추론 효율성을 높이지만 안전성을 저해할 수 있다는 사실을 최초로 밝히고, 이를 해결하는 QuadA 방어 메커니즘을 제안!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Zhejiang University",]
showSummary: true
date: 2025-02-02
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.00840 {{< /keyword >}}
{{< keyword icon="writer" >}} Jiawen Zhang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-05 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.00840" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.00840" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/activation-approximations-can-incur-safety" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)은 다양한 분야에서 뛰어난 성능을 보이지만, **막대한 계산 비용**과 **복잡한 활성화 함수**로 인해 배포 및 활용에 어려움이 있습니다. 최근에는 추론 효율성을 높이기 위해 **활성화 함수 근사** 기법이 주목받고 있지만, 이러한 기법이 **모델의 안전성에 미치는 영향**에 대한 연구는 부족합니다.

본 논문에서는 **다양한 활성화 함수 근사 기법**에 대한 **체계적인 안전성 평가**를 수행하고, 이를 통해 **안전성 저하** 현상을 발견했습니다.  특히 초기 레이어에서의 활성화 함수 근사가 안전성에 큰 영향을 미치며, 유해한 프롬프트가 특정 활성화 영역에 집중되는 경향을 발견했습니다. 이러한 문제를 해결하기 위해, 본 논문에서는 **QuadA라는 새로운 안전성 강화 기법**을 제안합니다. QuadA는 활성화 함수 근사의 오류 패턴을 분석하여 안전성을 저해하는 영역을 식별하고, 이를 완화하는 방식으로 설계되었습니다. 실험 결과, QuadA는 다양한 활성화 함수 근사 기법과 적응형 공격에 대해 강력한 안전성을 제공하는 것으로 나타났습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 활성화 함수 근사는 LLM의 안전성을 저해할 수 있다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 초기 몇몇 레이어에서의 활성화 함수 근사가 안전성에 가장 큰 영향을 미친다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} QuadA는 활성화 함수 근사로 인한 안전성 저하 문제를 완화하는 효과적인 방어 메커니즘이다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **활성화 함수 근사(activation approximation)** 기법이 안전하게 정렬된 대규모 언어 모델(LLM)의 안전성에 미치는 영향을 최초로 체계적으로 연구한 것입니다. **다양한 활성화 함수 근사 기법의 안전성 위험을 밝히고, 이러한 위험을 완화하기 위한 새로운 방어 메커니즘인 QuadA를 제안**합니다. 이는 LLM의 안전성과 효율성 사이의 균형을 개선하려는 연구자들에게 중요한 의미를 지닙니다. 또한, 본 연구는 **향후 LLM 안전성 연구의 새로운 방향**을 제시하며, LLM의 안전한 배포 및 활용을 위한 기반을 마련하는 데 기여합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.00840/extracted/6172793/assets/imgs/overview_2.png)

> 🔼 그림 1은 논문에서 제시하는 위협 모델에 등장하는 세 주체를 보여줍니다.  LLM 모델 개발자는 안전하게 정렬된 LLM을 개발하여 오픈소스로 제공합니다. LLM 기반 애플리케이션 제공자는 이러한 모델을 특정 사용 사례에 맞게 사용자 지정하고 최종 사용자에게 서비스를 제공합니다.  최종 사용자는 LLM 기반 애플리케이션과 상호 작용합니다. 이 그림은 세 주체 간의 상호 작용과 각 주체의 역할을 시각적으로 보여주어 논문의 위협 모델을 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Illustration of the three parties in Threat Model.
> </details>





{{< table-caption >}}
| Methods | Work | Setting | Speedup |
|---|---|---|---|
| Activation <br> Polynomialization | Iron (NeurIPS’22) | MPC | 9.6x |
|  | BOLT (S&P’24) | MPC | 24.6x |
|  | BumbleBee (NDSS’25) | MPC | 22.3x |
|  | NEXUS (NDSS’25) | FHE | 5.3x |
| Activation <br> Sparsification | TEAL (ICLR’25) | 25% sparsity | 1.3x |
|  |  | 50% sparsity | 1.9x |
|  |  | 90% sparsity | 9.5x |
| Activation <br> Quantization | SmoothQuant (ICML’23) | W16A8 | 2.0x |
|  |  | W16A4 | 4.0x |
|  | OmniQuant (ICLR’24) | W16A8 | 2.0x |
|  |  | W16A4 | 4.0x |{{< /table-caption >}}

> 🔼 표 1은 활성화 근사 기법과 그에 따른 추론 효율 향상을 보여줍니다. 활성화 다항식 근사의 경우, 기준 연구는 다항식 근사 없이 개인 정보 보호 추론 프로토콜을 사용하는 SIRNN(S&P’21) [29]입니다. 활성화 희소화 및 양자화의 경우, 기준은 가속 없이 전체 정밀도(FP16) 추론입니다.  다시 말해, 이 표는 다양한 활성화 근사 기법들을 소개하고, 각 기법이 기존 방식 대비 추론 속도를 얼마나 향상시키는지(속도 향상 배수) 보여줍니다.  활성화 근사 기법은 크게 활성화 다항식 근사, 활성화 희소화, 활성화 양자화 세 가지로 분류됩니다. 각 기법별 대표적인 연구들이 제시되며, 실험 환경(MPC, FHE 등)과 속도 향상 배수가 함께 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Activation approximation techniques and their inference efficiency gains. For activation polynomialization, the baseline work is SIRNN (S&P’21) [29], a private inference protocol without polynomialization. For activation sparsification and quantization, the baseline is full-precision (FP16) inference without any accelerations.
> </details>





### In-depth insights


#### LLM Safety Fragility
LLM의 안전성 취약성은 **대규모 언어 모델이 예상치 못한 방식으로 유해한 결과를 생성할 수 있다는 사실**을 강조합니다. 이는 모델이 잘못된 방식으로 학습되거나, 악의적인 사용자의 공격에 취약하거나, 또는 환경 변화에 적응하지 못하는 경우 발생할 수 있습니다.  **안전성 취약성의 심각성**은 모델의 규모와 복잡성이 증가함에 따라 더욱 심각해지며, **예측 불가능성**으로 인해 안전성을 보장하기 어렵습니다. 따라서, **안전한 LLM 개발 및 배포**를 위해서는 견고한 안전성 메커니즘이 필수적입니다. 이는 모델 개발 단계에서의 철저한 안전성 테스트 및 평가, 그리고 배포 후 지속적인 모니터링과 수정을 포함합니다.  **사용자의 악의적인 의도**를 탐지하고 차단하는 기술 또한 중요하며, **안전성과 유용성 간의 균형**을 맞추는 것이 중요한 과제입니다.  **새로운 공격 기법**에 대한 지속적인 연구와 대응, 그리고 **안전성 개선을 위한 협업**이 필요합니다.

#### Activation Approx. Risks
활성화 함수 근사(Activation Approximation)는 추론 속도 향상에 효과적이지만, **안전성에 심각한 위협**이 될 수 있다는 점이 이 논문의 핵심입니다.  **정확도 저하보다 안전성 저하가 먼저 발생**하며, 특히 초기 계층에서의 근사 오류가 안전성에 치명적입니다.  **악의적인 프롬프트는 활성화 공간 내 특정 영역에 집중**되는 경향이 있으며, 근사는 이러한 악의적인 활성화를 무해한 영역으로 이동시켜 안전 장치를 우회할 수 있게 합니다. 따라서 단순한 성능 향상이 아닌, **안전성을 고려한 활성화 함수 근사 기법 및 방어 메커니즘의 개발**이 필수적입니다.  본 논문은 이러한 문제점을 규명하고, **QuadA** 와 같은 새로운 안전 강화 기법을 제시하여 활성화 함수 근사의 안전성 문제를 해결하고자 합니다.  **다양한 모델과 공격 방법에 대한 실험 결과**는 QuadA의 효과를 뒷받침합니다.

#### QuadA Safety Fix
QuadA는 활성화 근사로 인한 안전성 저하 문제를 해결하기 위한 안전 강화 기법입니다. **주요 아이디어는 활성화 근사 오류의 패턴을 분석하여 이러한 오류가 안전성에 미치는 영향을 최소화하는 것입니다.** 이를 위해 QuadA는 세 가지 핵심 구성 요소를 포함합니다. 첫째, **모델의 안전성에 가장 취약한 활성화 영역을 식별하여 이 영역에만 섭동을 적용**합니다. 둘째, **안전성에 가장 큰 영향을 미치는 층을 식별**하고 해당 층에만 섭동을 적용합니다. 셋째, **유해한 프롬프트가 활성화 공간 내에서 클러스터링되는 경향을 이용**하여 유해한 프롬프트를 양성 영역으로 이동시키는 방식으로 안전성을 강화합니다.  QuadA는 다양한 활성화 근사 기법에 대해 **일관된 안전성 향상 효과**를 보이며, 특히 적응형 감옥 탈출 공격에 대해 강력한 방어력을 제공합니다.  **실험 결과는 QuadA가 안전성과 유용성 사이의 균형을 효과적으로 유지하면서 안전성을 향상시킨다는 것을 보여줍니다.**  이 기법은 LLM 개발자들이 최소한의 코드 수정만으로도 안전성을 강화할 수 있도록 지원하며, 안전한 LLM 배포를 위한 중요한 전략으로 자리매김할 가능성이 높습니다.

#### Layer-Wise Effects
본 논문에서 다룬 "Layer-Wise Effects"는 **각 레이어별 활성화 함수 근사의 영향을 계층별로 분석**한 부분입니다.  이는 단순히 성능 저하 여부를 넘어, **안전성 측면에서 특정 레이어가 다른 레이어보다 훨씬 취약**하다는 것을 시사합니다. 특히, 초기 레이어의 활성화 함수 근사가 안전성에 미치는 악영향이 훨씬 크다는 점을 강조합니다.  **초기 레이어는 모델의 기본적인 이해와 판단에 관여**하기 때문에, 여기서 발생하는 오류는 전반적인 출력에 심각한 영향을 미칠 수 있습니다. 반면, 후기 레이어의 근사는 상대적으로 안전성에 미치는 영향이 적은 것으로 나타났습니다. 이는 **모델의 안전성이 계층 구조적으로 취약점을 가지고 있음**을 보여주는 중요한 발견입니다.  따라서, **활성화 함수 근사 기법을 적용할 때는 레이어별 특성을 고려한 차별화된 접근**이 필요하며, **초기 레이어의 정확성을 최대한 유지**하는 방안을 강구해야 합니다.  이는 향후 안전한 LLM 개발 및 배포에 중요한 시사점을 제공합니다.

#### Future Research
활성화 근사의 안전성에 대한 연구는 아직 초기 단계이며, **미래 연구는 몇 가지 중요한 방향으로 나아갈 수 있습니다.**  먼저, 다양한 활성화 함수와 네트워크 구조에 대한 포괄적인 안전성 평가가 필요합니다. 특정 활성화 함수나 구조가 안전성 저하에 더 취약한지, 그리고 그 이유는 무엇인지에 대한 심층적인 이해가 중요합니다.  **다양한 활성화 근사 기법의 안전성 저하 메커니즘을 분석하고, 그 특징을 규명하는 연구**는 효과적인 방어 메커니즘 개발에 필수적입니다.  또한, **QuadA와 같은 방어 기법의 일반화 가능성과 효율성을 높이는 연구**가 필요합니다. 다양한 활성화 함수, 네트워크 구조, 그리고 공격 방법에 대해 QuadA의 성능을 평가하고,  계산 비용을 줄이는 방향으로 개선하는 연구가 진행되어야 합니다. 마지막으로, **실제 응용 환경에서의 안전성 평가를 위한 실험 환경 구축 및 실험 수행**을 통해,  활성화 근사 기법의 안전성 문제를 보다 현실적으로 이해하고, 효과적인 해결책을 제시하는 연구가 필요합니다.  **특히, 개인정보보호를 위한 연합 학습과 같은 상황에서 활성화 근사 기법의 안전성에 대한 연구는 중요한 과제**입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.00840/extracted/6172793/assets/imgs/noise_private_inference.png)

> 🔼 그림 (a)는 BOLT[21]를 예시로 하여 활성화 다항식화에서의 오차 분포를 보여줍니다. 다항식 근사화 방법을 사용하여 복잡한 활성화 함수를 단순화할 때 발생하는 오차의 분포를 나타냅니다.  x축은 오차 값을, y축은 해당 오차 값의 빈도수를 나타내는 히스토그램 형태로 표현됩니다. 이 분포는 활성화 함수 근사화 과정에서 발생하는 오차의 크기와 빈도를 파악하는 데 유용하며, 이는 추후 모델의 성능 및 안전성 평가에 중요한 지표가 됩니다.
> <details>
> <summary>read the caption</summary>
> (a) Error distributions in activation polynomialization, with BOLT [21] as the example.
> </details>



![](https://arxiv.org/html/2502.00840/extracted/6172793/assets/imgs/noise_activation_sparsity.png)

> 🔼 그림 (b)는 TEAL [24] 논문의 50% 희소성(sparsity)을 적용한 활성화 희소화(activation sparsification)에서 발생하는 오류의 분포를 보여줍니다.  이 그래프는 활성화 함수의 출력값에 적용된 희소화 기법으로 인해 발생하는 오차의 크기와 빈도를 나타냅니다.  가로축은 오차의 크기를, 세로축은 오차의 발생 빈도(확률 밀도)를 나타냅니다.  그림에서 볼 수 있듯이 오차는 0을 중심으로 대칭적으로 분포되어 있으며, 대부분의 오차는 0에 가까운 값을 가지는 것을 알 수 있습니다. 이는 활성화 희소화 기법이 상대적으로 작은 오차를 발생시킨다는 것을 시사합니다.  하지만, 일부 큰 오차도 존재하는 것으로 보이며, 이는 활성화 희소화의 안정성과 관련된 추가적인 분석이 필요할 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (b) Error distributions in activation sparsification, with TEAL [24] in 50% sparsity.
> </details>



![](https://arxiv.org/html/2502.00840/extracted/6172793/assets/imgs/noise_activation_quantization.png)

> 🔼 그림은 SmoothQuant라는 8비트 활성화 양자화 기법을 사용했을 때의 활성화 오차 분포를 보여줍니다.  Llama-3.1-8B-Instruct 모델에서 Wup(가중치 행렬 곱셈 전)과 Wdown(가중치 행렬 곱셈 후)에서의 오차 분포를 각각 보여주는 두 개의 그래프가 있습니다.  각 그래프는 오차의 분포를 나타내며, 가우시안 분포와 라플라스 분포를 최적합으로 표시하여 비교 분석합니다. 이를 통해, SmoothQuant 기법의 오차 특성을 정량적으로 파악하고, 다른 활성화 근사 기법과의 비교 분석에 활용할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (c) Error distributions in activation quantization, with SmoothQuant [27] in 8-bit activation.
> </details>



![](https://arxiv.org/html/2502.00840/extracted/6172793/assets/imgs/LN_noise.png)

> 🔼 그림 2는 Llama-3.1-8B-Instruct 모델에서 다양한 활성화 함수 근사 기법을 사용했을 때 발생하는 오차의 분포를 보여줍니다.  왼쪽 열은    $ \mathbf{W}^{\text{up}} $ 행렬 적용 전의 오차 분포를, 오른쪽 열은   $ \mathbf{W}^{\text{down}} $ 행렬 적용 전의 오차 분포를 나타냅니다.  각 오차 분포에 가장 잘 맞는 가우시안 또는 라플라스 분포가 검은색 선으로 표시되어 비교 분석에 활용됩니다.  이를 통해 다양한 활성화 함수 근사 방법의 오차 특성을 파악하고, 그 영향을 평가하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Activation error distributions on Llama-3.1-8B-Instruct using different activation approximations. The first column presents errors before 𝐖upsuperscript𝐖up\mathbf{W}^{\text{up}}bold_W start_POSTSUPERSCRIPT up end_POSTSUPERSCRIPT, and the second column presents errors before 𝐖downsuperscript𝐖down\mathbf{W}^{\text{down}}bold_W start_POSTSUPERSCRIPT down end_POSTSUPERSCRIPT. Best-fit Gaussian/Laplace distributions are overlaid in black for comparison.
> </details>



![](https://arxiv.org/html/2502.00840/extracted/6172793/assets/imgs/FFN_noise.png)

> 🔼 그림 3은 다양한 안전하게 정렬된 대규모 언어 모델(LLM)에서 활성화 함수의 입력값인  \(\mathbf{W}^{\text{up}}\) 앞에 근사화 오류를 추가했을 때의 영향을 보여줍니다.  x축은 추가된 노이즈의 표준편차를 나타내고, y축은 ASR(공격 성공률)과 PPL(퍼플렉서티)을 나타냅니다. 각 그래프는 특정 LLM에 대한 결과를 보여주며, 근사화 오류가 증가함에 따라 ASR이 어떻게 변하는지, 그리고 PPL 점수가 어떻게 변하는지 보여줍니다.  이 그림은 활성화 함수 근사화가 모델의 안전성과 유용성에 미치는 영향을 시각적으로 보여주는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Approximation of activation before 𝐖upsuperscript𝐖up\mathbf{W}^{\text{up}}bold_W start_POSTSUPERSCRIPT up end_POSTSUPERSCRIPT on different safety-aligned LLMs.
> </details>



![](https://arxiv.org/html/2502.00840/extracted/6172793/assets/imgs/activation_mds_before.png)

> 🔼 그림 4는 다양한 안전하게 정렬된 대규모 언어 모델(LLM)에서 활성화 함수에 대한 근사치를 적용하기 전과 후의 활성화 값의 분포를 보여줍니다. 구체적으로, 그림은 다양한 안전하게 정렬된 LLM에 대해  Wdown \mathbf{W}^{\text{down}}\mathbf{W}^{\text{down}} 매트릭스 앞의 활성화 값의 근사 오차 분포를 보여줍니다.  각 그래프는 특정 LLM에 대한 활성화 값 근사의 영향을 보여주는 ASR(공격 성공률)과 PPL(퍼플렉서티) 값의 변화를 나타냅니다. 가우시안 노이즈 표준편차가 증가함에 따라 ASR이 점진적으로 증가하다가 특정 수준에서 정점에 도달하고, 이후 PPL 점수가 급격하게 증가하면서 ASR은 감소하는 경향을 보입니다. 이는 안전하게 정렬된 LLM이 악의적인 질문을 거부하지 못하고 의미 있는 응답을 생성하다가, 노이즈가 너무 커지면 의미 없는 응답을 생성하기 시작함을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Approximation of activation before 𝐖downsuperscript𝐖down\mathbf{W}^{\text{down}}bold_W start_POSTSUPERSCRIPT down end_POSTSUPERSCRIPT on different safety-aligned LLMs.
> </details>



![](https://arxiv.org/html/2502.00840/extracted/6172793/assets/imgs/activation_mds_after.png)

> 🔼 그림은 활성화 근사화가 적용되지 않은 경우(a)와 적용된 경우(b)의 마지막 토큰 활성화 공간의 2차원 투영을 보여줍니다.  Llama-2-7B-chat 모델의 첫 번째 계층에서 악의적인 프롬프트와 양성 프롬프트 모두에서 추출한 활성화 값을 사용했습니다.  MDS(다차원 배열 축소)를 사용하여 차원을 줄였습니다.  악의적인 프롬프트의 활성화는 활성화 근사화가 없을 때는 양성 프롬프트와 명확하게 구분되지만, 근사화가 적용되면 양성 프롬프트와 겹치는 경향이 있습니다. 이는 악의적인 프롬프트가 안전 점검을 우회할 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (a) Activations without approximation
> </details>



![](https://arxiv.org/html/2502.00840/extracted/6172793/assets/imgs/noise_cutoff.png)

> 🔼 그림 (b)는 활성화 함수 근사화가 적용된 후의 활성화 값 분포를 보여줍니다.  x축은 악의적인 프롬프트와 양성 프롬프트의 마지막 토큰의 활성화 벡터를 다차원척도법(MDS)을 사용하여 2차원으로 투영한 값입니다. y축은 해당 벡터의 값을 나타냅니다.  근사화 전의 그림 (a)와 비교하여 악성 프롬프트의 활성화 값 분포가 양성 프롬프트의 분포와 겹치는 부분이 증가했음을 시각적으로 보여줍니다. 이는 활성화 함수 근사화로 인해 악성 프롬프트가 안전장치를 우회할 가능성이 높아졌음을 의미합니다.
> <details>
> <summary>read the caption</summary>
> (b) Activations with approximation
> </details>



![](https://arxiv.org/html/2502.00840/extracted/6172793/assets/imgs/LN_noise_defense.png)

> 🔼 그림 5는 Llama-2-7B-Chat 모델의 첫 번째 레이어에서 악의적인 프롬프트와 무해한 프롬프트 모두로부터 생성된 마지막 토큰 활성화 공간의 MDS 투영을 보여줍니다.  MDS(다차원척도법)는 고차원 데이터를 저차원 공간에 시각적으로 표현하는 기법으로, 이 그림에서는 악의적 프롬프트와 무해한 프롬프트의 활성화 벡터 분포를 2차원 공간에 나타냅니다. 이를 통해 활성화 공간에서 악의적 프롬프트와 무해한 프롬프트의 분포 차이를 시각적으로 확인하고, 활성화 근사에 따른 이러한 분포 변화를 이해하는 데 도움이 됩니다. 그림은 활성화 근사가 적용되지 않은 경우와 적용된 경우의 활성화 벡터 분포를 비교하여, 활성화 근사가 악의적 프롬프트의 감지를 어렵게 만드는 데 어떻게 영향을 미치는지를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: MDS projection of the last-token activation space produced from both harmful and benign prompts on Llama-2-7B-chat in the first layer.
> </details>



![](https://arxiv.org/html/2502.00840/extracted/6172793/assets/imgs/FFN_noise_defense.png)

> 🔼 그림 6은 다양한 안전하게 정렬된 LLMs에서 계층별 활성화 근사에 대한 실험 결과를 보여줍니다.  그래프는 Ｗup (가중치 업데이트 행렬) 전과 Ｗdown (가중치 다운데이트 행렬) 전에 활성화에 추가된 근사화 잡음의 영향을 보여줍니다.  녹색 선은 Ｗup 전의 활성화에 추가된 근사화 잡음을 나타내고, 주황색 선은 Ｗdown 전의 활성화에 추가된 근사화 잡음을 나타냅니다. 각 그래프는 특정 LLM 모델에 대한 결과를 보여주며, x축은 LLM의 계층을, y축은 공격 성공률(ASR)을 나타냅니다.  이 그림을 통해 각 계층에서의 활성화 근사가 안전성에 미치는 영향을, 특히 Ｗup과 Ｗdown 전의 활성화에 대한 잡음의 영향을 비교 분석할 수 있습니다.  각 LLM 모델별로 다양한 수준의 활성화 근사화 노이즈가 안전성에 미치는 영향을 시각적으로 보여주는 것이 이 그림의 주요 목적입니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Layer-wise activation approximations on different safety-aligned LLMs. The green lines indicate approximation noise added to activations before 𝐖upsuperscript𝐖up\mathbf{W}^{\text{up}}bold_W start_POSTSUPERSCRIPT up end_POSTSUPERSCRIPT. The orange lines indicate approximation noise added to activations before 𝐖downsuperscript𝐖down\mathbf{W}^{\text{down}}bold_W start_POSTSUPERSCRIPT down end_POSTSUPERSCRIPT.
> </details>



![](https://arxiv.org/html/2502.00840/extracted/6172793/assets/imgs/layers_ablation_2.png)

> 🔼 그림 7은 다양한 perturbation-aware 안전하게 정렬된 LLMs에 대해 W<sup>up</sup> 이전의 활성화에 대한 섭동을 보여줍니다.  각 그래프는 특정 LLM에 대한 ASR(공격 성공률)과 PPL(퍼플렉서티)을 보여주는 곡선을 나타냅니다. x축은 가우시안 노이즈의 표준 편차를 나타내고, y축은 왼쪽이 ASR, 오른쪽이 PPL을 나타냅니다. 이 그림은 다양한 수준의 노이즈가 추가된 모델의 안전성과 유용성에 대한 영향을 보여주기 위해 만들어졌습니다.  안전하게 정렬된 LLM이 섭동에 얼마나 강인한지, 그리고 유용성이 손상되기 전에 안전성이 떨어지는지를 보여주는 중요한 결과를 담고 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Perturbation of activation before 𝐖upsuperscript𝐖up\mathbf{W}^{\text{up}}bold_W start_POSTSUPERSCRIPT up end_POSTSUPERSCRIPT on different perturbation-aware safety-aligned LLMs.
> </details>



![](https://arxiv.org/html/2502.00840/extracted/6172793/assets/imgs/activation_mds_dpo.png)

> 🔼 그림 8은 다양한 변형에 강화된 안전하게 정렬된 대규모 언어 모델(LLM)에 대한 Wdown 행렬 이전의 활성화에 대한 변형을 보여줍니다. 이 그림은 다양한 LLM에서 활성화에 노이즈를 추가했을 때의 ASR(공격 성공률)과 PPL(퍼플렉서티) 점수를 보여주는 그래프를 포함합니다. 이는 활성화 근사화에 따른 안전성 저하를 완화하기 위한 QuadA 방법의 효과를 평가하기 위한 실험 결과를 보여줍니다. 각 그래프는 특정 LLM의 ASR과 PPL이 노이즈의 표준 편차에 따라 어떻게 변하는지를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Perturbation of activation before 𝐖downsuperscript𝐖down\mathbf{W}^{\text{down}}bold_W start_POSTSUPERSCRIPT down end_POSTSUPERSCRIPT on different perturbation-aware safety-aligned LLMs.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
Methods | Works | Setting | \epsilon_{l}^{up} | \epsilon_{l}^{down} | \textbf{PPL}\downarrow | \textbf{ASR}\downarrow
---|---|---|---|---|---|---
Activation <br> Polynomialization | Iron [19] | MPC | \mathcal{N}(0,0.064^{2}) | Lap(0, 0.049) | 43.74 | 58.07
| BOLT [21] | MPC | \mathcal{N}(0,0.042^{2}) | Lap(0, 0.036) | 15.81 | 35.76
| BumbleBee [22] | MPC | \mathcal{N}(0,0.026^{2}) | Lap(0, 0.018) | 11.28 | 20.56
| NEXUS [23] | FHE | \mathcal{N}(0,0.031^{2}) | Lap(0, 0.014) | 12.93 | 21.15
Activation <br> Sparsification | TEAL [24] | 10% sparsity | \mathcal{N}(0,0.35^{2},|X|\leq 0.04) | \text{Lap}(0,0.024,|X|\leq 0.003) | 8.05 | 5.00
|  |  | 25% sparsity | \mathcal{N}(0,0.35^{2},|X|\leq 0.11) | \text{Lap}(0,0.024,|X|\leq 0.007) | 8.09 | 28.85
|  |  | 50% sparsity | \mathcal{N}(0,0.35^{2},|X|\leq 0.24) | \text{Lap}(0,0.024,|X|\leq 0.017) | 8.57 | 57.12
|  |  | 90% sparsity | \mathcal{N}(0,0.35^{2},|X|\leq 0.57) | \text{Lap}(0,0.024,|X|\leq 0.055) | 206.47 | 0.02
Activation <br> Quantization | SmoothQuant [27] | W16A8 | \mathcal{N}(0,0.027^{2}) | Lap(0,0.019) | 9.56 | 41.92
|  |  | W16A4 | \mathcal{N}(0,0.035^{2}) | Lap(0,0.024) | 10.35 | 55.19
| OmniQuant [28] | W16A8 | \mathcal{N}(0,0.029^{2}) | Lap(0,0.028) | 9.85 | 33.46
|  |  | W16A4 | \mathcal{N}(0,0.036^{2}) | Lap(0,0.037) | 10.79 | 47.11{{< /table-caption >}}
> 🔼 표 2는 Llama-3.1-8B-Instruct 모델에 대해 다양한 training-free activation approximation 기법들의 성능을 벤치마크한 결과를 보여줍니다.  각 기법은 activation polynomialization, sparsification, quantization 세 가지 범주로 나뉘며, 각 범주 내에서 대표적인 기법들을 선정하여 실험했습니다.  결과는 perplexity (PPL)와 attack success rate (ASR)으로 측정되었으며, baseline PPL은 8.05, baseline ASR은 0.19입니다.  각 기법의 적용 후 PPL과 ASR 변화를 통해 activation approximation이 모델 성능 및 안전성에 미치는 영향을 정량적으로 비교 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Benchmark of different training-free activation approximation techniques on Llama-3.1-8B-Instruct. Note that the baseline PPL is 8.05, ASR is 0.19.
> </details>

{{< table-caption >}}
| Family | Model | Sensitive | Baseline | Error Before 𝐖<sup>up</sup> | Error Before 𝐖<sup>down</sup> |
|---|---|---|---|---|---|---|
| Llama | Llama-2-7B-Chat | [0-3] | 1.34 | 7.84 |  𝝰(0,0.045<sup>2</sup>) | 56.73 |
|  |  |  |  |  | Lap(0, 0.100) | 49.80 |
|  |  |  |  |  |  | 10.96 |
|  | Llama-2-13B-Chat | [0-3] | 0.00 | 7.07 | 𝝰(0,0.042<sup>2</sup>) | 47.88 |
|  |  |  |  |  | Lap(0, 0.125) | 52.12 |
|  |  |  |  |  |  | 18.46 |
|  | Llama-3.1-8B-Instruct | [0-3] | 0.19 | 8.05 | 𝝰(0,0.075<sup>2</sup>) | 69.23 |
|  |  |  |  |  | Lap(0, 0.085) | 67.50 |
|  |  |  |  |  |  | 11.70 |
| Phi3 | Phi-3-Mini-4K-Instruct | [0-3] | 0.00 | 6.71 | 𝝰(0,0.040<sup>2</sup>) | 82.61 |
|  |  |  |  |  | Lap(0, 0.120) | 32.38 |
|  |  |  |  |  |  | 9.46 |
|  | Phi-3.5-Mini-Instruct | [0-3] | 0.77 | 6.86 | 𝝰(0,0.033<sup>2</sup>) | 79.50 |
|  |  |  |  |  | Lap(0, 0.100) | 44.72 |
|  |  |  |  |  |  | 7.45 |
| Mistral | Mistral-7B-Instruct-v0.3 | [0-6] | 34.61 | 6.13 | 𝝰(0,0.200<sup>2</sup>) | 73.18 |
|  |  |  |  |  | Lap(0, 0.075) | 71.02 |
|  |  |  |  |  |  | 6.24 |
|  | Mixtral-8x7B-Instruct-v0.1 | [0-4] | 1.15 | 4.61 | 𝝰(0,0.400<sup>2</sup>) | 82.47 |
|  |  |  |  |  | Lap(0, 0.225) | 87.64 |
|  |  |  |  |  |  | 19.31 |
|  | Zephyr-7B-β | [0-4] | 22.31 | 7.01 | 𝝰(0,0.250<sup>2</sup>) | 88.30 |
|  |  |  |  |  | Lap(0, 0.113) | 82.35 |
|  |  |  |  |  |  | 9.07 |
| Qwen | Qwen2-7B-Instruct | [0-4] | 0.38 | 8.46 | 𝝰(0,0.300<sup>2</sup>) | 52.16 |
|  |  |  |  |  | Lap(0, 0.058) | 73.82 |
|  |  |  |  |  |  | 23.94 |
|  | Qwen2.5-32B-Instruct | [0-4] | 0.00 | 5.74 | 𝝰(0,0.200<sup>2</sup>) | 37.48 |
|  |  |  |  |  | Lap(0, 0.043) | 46.13 |
|  |  |  |  |  |  | 21.54 |{{< /table-caption >}}
> 🔼 표 3은 안전하게 정렬된 대규모 언어 모델(LLM)에서 활성화 근사의 영향을 보여줍니다.  각 모델에 대해 안전에 민감한 계층의 수, 기준 PPL(퍼플렉서티) 및 ASR(공격 성공률), Wup(가중치 업데이트 전) 및 Wdown(가중치 업데이트 후) 전의 활성화 오류 크기, 그리고 각 오류에 대한 MVA(가장 취약한 근사값)에서의 ASR 및 PPL 값이 제시되어 있습니다. 이 표는 활성화 근사가 LLM의 안전성에 미치는 영향을 계층별로, 그리고 다양한 모델들 간에 비교 분석하는 데 도움을 줍니다.  즉, 활성화 근사가 모델의 안전성에 어떤 영향을 주는지, 어느 정도의 크기의 영향인지를 계층과 모델 별로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Impact surface and magnitude of activation approximations on safety-aligned LLMs.
> </details>

{{< table-caption >}}
| Model | None | GCG | AutoDAN | DRA |
|---|---|---|---|---|
| Llama-2-7B-Chat | 1.3 | 34.5 | 0.5 | 69.2 |
| + DPO | 0.0 | 29.1 | 0.0 | 38.4 |
| + QuadA | 0.0 | 0.0 | 0.0 | 3.3 |
| Llama-2-13B-Chat | 0.0 | 28.0 | 0.0 | 58.4 |
| + DPO | 0.0 | 20.5 | 0.0 | 19.2 |
| + QuadA | 0.0 | 0.0 | 0.0 | 1.5 |
| Llama-3.1-8B-Instruct | 0.2 | 36.0 | 1.0 | 75.3 |
| + DPO | 0.0 | 34.9 | 0.0 | 58.4 |
| + QuadA | 0.0 | 0.0 | 0.0 | 0.2 |
| Phi-3-Mini-4K-Instruct | 0.0 | 56.0 | 84.5 | 91.2 |
| + DPO | 0.0 | 27.4 | 69.0 | 84.7 |
| + QuadA | 0.0 | 1.5 | 0.8 | 6.3 |
| Phi-3.5-Mini-Instruct | 0.8 | 58.0 | 86.5 | 96.7 |
| + DPO | 0.0 | 31.0 | 72.1 | 88.2 |
| + QuadA | 0.0 | 4.9 | 2.5 | 10.4 |
| Mistral-7B-Instruct-v0.3 | 34.6 | 84.3 | 93.0 | 98.5 |
| + DPO | 0.0 | 20.5 | 64.4 | 86.0 |
| + QuadA | 0.8 | 1.2 | 1.0 | 2.5 |
| Mixtral-8x7B-Instruct-v0.1 | 1.2 | 79.5 | 88.5 | 92.0 |
| + DPO | 0.0 | 12.3 | 36.7 | 52.5 |
| + QuadA | 0.0 | 0.0 | 0.0 | 0.8 |
| Zephyr-7B-β | 22.3 | 78.6 | 97.5 | 94.8 |
| + DPO | 0.0 | 19.5 | 70.2 | 88.1 |
| + QuadA | 0.0 | 2.9 | 0.4 | 7.0 |
| Qwen2-7B-Instruct | 0.4 | 48.4 | 62.5 | 79.3 |
| + DPO | 0.0 | 32.5 | 53.0 | 67.9 |
| + QuadA | 0.0 | 0.0 | 0.0 | 4.5 |
| Qwen2.5-32B-Instruct | 0.0 | 36.6 | 31.5 | 57.9 |
| + DPO | 0.0 | 17.9 | 6.8 | 24.1 |
| + QuadA | 0.0 | 0.0 | 0.0 | 0.2 |{{< /table-caption >}}
> 🔼 표 4는 다양한 적응형 프롬프트 기반 탈옥 공격을 적용했을 때의 공격 성공률(ASR)을 보여줍니다.  'None'은 접미사가 없는 탈옥 프롬프트를 의미합니다. 이 표는 다양한 사전 훈련된 안전한 LLMs에 대해 GCG, AutoDAN, DRA와 같은 세 가지 적응형 탈옥 공격의 효과를 보여줍니다. 각 행은 특정 LLM 모델을 나타내며, 각 열은 특정 공격 방법 또는 공격이 없는 경우의 ASR을 백분율로 나타냅니다.  +DPO 및 +QuadA 열은 각각 DPO(Direct Preference Optimization) 기반 안전 정렬 및 제안된 QuadA 방법을 사용하여 안전하게 정렬된 모델에 대한 결과를 보여줍니다. 이 표는 QuadA 방법의 효과를 보여주는 데 사용됩니다. 즉, QuadA는 적응형 탈옥 공격에 대해 안전성이 강화된 LLM을 만드는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Attack success rates (ASR) of applying different adaptive prompt-based jailbreak attacks. None means the jailbreak prompt without any suffix.
> </details>

{{< table-caption >}}
| Model | NA | LA | mva |
|---|---|---|---| 
| Llama-2-7B-Chat | 40.76 | 26.15 | **0.00** |
| Llama-2-13B-Chat | 44.52 | 30.95 | **0.00** |
| Llama-3.1-8B-Instruct | 61.84 | 45.79 | **0.19** |
| Phi-3-Mini-4K-Instruct | 56.83 | 41.26 | **0.00** |
| Phi-3.5-Mini-Instruct | 64.80 | 35.76 | **0.00** |
| Mistral-7B-Instruct-v0.3 | 71.45 | 52.84 | **0.77** |
| Mixtral-8x7B-Instruct-v0.1 | 78.04 | 59.37 | **1.05** |
| Zephyr-7B-β | 81.20 | 62.35 | **0.38** |
| Qwen2-7B-Instruct | 64.36 | 33.17 | **0.00** |
| Qwen2.5-32B-Instruct | 35.58 | 22.06 | **0.00** |{{< /table-caption >}}
> 🔼 표 5는 활성화 근사 강건한 안전 정렬 중에 서로 다른 크기의 섭동을 적용할 때 공격 성공률(ASR)을 보여줍니다.  이 표는 다양한 활성화 근사 기법(활성화 다항식화, 활성화 희소화, 활성화 양자화)에 대해 10가지 안전 정렬된 LLMs에서 안전성에 미치는 영향을 평가한 실험 결과를 제시합니다.  'NA'는 섭동이 없는 경우, 'LA'는 MVA(가장 취약한 근사)보다 10% 큰 크기의 섭동, 그리고 'MVA'는 가장 취약한 근사에 해당하는 섭동을 의미합니다.  이 표를 통해 MVA를 사용하여 안전 정렬을 수행하면 활성화 근사 오류에 대한 모델의 저항성이 크게 향상됨을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Attack success rates (ASR) of applying perturbations with different magnitudes during activation approximation-robust safety alignment.
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
{{< /gallery >}}