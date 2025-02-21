---
title: "Train Small, Infer Large: Memory-Efficient LoRA Training for Large Language Models"
summary: "LORAM은 대규모 언어 모델의 미세 조정에 필요한 메모리를 획기적으로 줄이면서 성능 저하 없이 효율적인 학습을 가능하게 하는 혁신적인 방법입니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Zhejiang University",]
showSummary: true
date: 2025-02-19
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.13533 {{< /keyword >}}
{{< keyword icon="writer" >}} Jun Zhang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-20 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.13533" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.13533" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/train-small-infer-large-memory-efficient-lora" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)의 미세 조정은 많은 메모리를 필요로 하기 때문에 비용이 많이 들고, 계산 자원이 제한적인 연구자들에게는 어려움이 있습니다. 기존의 LoRA(Low-Rank Adaptation) 방법은 원래 모델의 파라미터를 고정하고 저차원 어댑터 행렬만 학습하여 메모리 사용량을 줄이지만, 여전히 원래 모델의 파라미터 크기 때문에 메모리 부족 문제가 발생합니다.

본 논문에서는 이러한 문제를 해결하기 위해 **LORAM (Memory-efficient LoRA training)**이라는 새로운 방법을 제안합니다. LORAM은 **훈련 단계에서는** **잘라낸(pruned) 소규모 모델**을 사용하여 저차원 어댑터 행렬을 학습하고, **추론 단계에서는** **잘라내기 전의 원래 대규모 모델**에 학습된 행렬을 적용하는 방식입니다. 이를 통해 **훈련에 필요한 메모리 사용량을 크게 줄이면서** 추론 성능은 그대로 유지할 수 있습니다. 또한, 논문에서는 **모델 제공자가 미리 수행할 수 있는 저비용의 지속적인 사전 훈련**을 통해 잘라낸 모델과 원래 모델 간의 지식 차이를 줄이는 방법도 제시합니다. 실험 결과, LORAM은 기존 LoRA 및 전체 미세 조정 방법보다 우수한 성능을 보였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} LORAM은 대규모 언어 모델의 미세 조정에 필요한 메모리 사용량을 획기적으로 줄입니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} LORAM은 소규모 모델로 훈련하고 대규모 모델로 추론하는 독특한 방식을 통해 성능 저하 없이 메모리 효율을 높입니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} LORAM은 다양한 모델과 작업에서 효과적으로 작동하며, 양자화 기법과의 통합을 통해 추가적인 메모리 절감 효과를 제공합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **메모리 효율적인 LLM 미세 조정**을 위한 새로운 방법인 LORAM을 제시하여, 기존의 한계를 극복하고 **GPU 메모리 사용량을 크게 줄이면서** 성능을 향상시키는 데 중요한 의미를 가집니다. **제한된 자원**으로 대규모 언어 모델을 활용하려는 연구자들에게 **실용적인 해결책**을 제공하며, **효율적인 모델 훈련 및 추론**에 대한 새로운 가능성을 제시합니다. 특히, **소규모 모델을 이용한 훈련과 대규모 모델을 이용한 추론**이라는 독특한 접근 방식은 향후 연구의 새로운 방향을 제시합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.13533/x1.png)

> 🔼 그림 1은 논문에서 제안하는 LoRAM의 핵심 아이디어를 보여줍니다. 기존 LoRA는 학습과 추론 모두 동일한 모델을 사용하지만, LoRAM은 학습 시에는 가지치기된 작은 모델을 사용하고 추론 시에는 원래 큰 모델을 사용합니다. 이를 통해 LoRA 학습 시 발생하는 메모리 문제를 완화합니다. 그림에서는 가지치기된 모델에서 학습된 가중치(노란색 블록)가 원래 모델에 통합되는 과정과 추론 시 가지치기된 가중치(파란색 블록)가 활용되는 과정을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Idea of LoRAM
> </details>





{{< table-caption >}}
| Method | OpenHermes MathQA | OpenHermes GSM8K | OpenOrca MathQA | OpenOrca GSM8K | Redu. Ratio |
|---|---|---|---|---|---| 
| 13B w/o FT | 32.60 | 24.26 | 32.93 | 23.35 | 1.00× |
| 7B LoRA | 29.61 | 22.82 | 30.95 | 13.87 | 1.93× |
| 13B LoRAM-Rand | 33.77 | 27.22 | 32.83 | 25.93 | 2.17× |
| 13B LoRAM-Stru | 33.80 | 24.64 | 33.07 | 24.49 | 2.17× |
| 13B LoRAM-Semi | 31.76 | 36.92 | 33.07 | 27.29 | 1.95× |
| 13B LoRAM-Unst | 30.12 | 31.92 | 32.70 | 26.61 | 2.16× |
| 70B w/o FT | 39.53 | 52.01 | 39.53 | 52.01 | 1.00× |
| 13B LoRA | 32.03 | 36.69 | 33.63 | 25.70 | 5.30× |
| 70B QLoRAM-Rand | 39.66 | 57.62 | 39.40 | 55.72 | 12.84× |
| 70B QLoRAM-Stru | 39.77 | 57.16 | 39.73 | 54.44 | 12.84× |{{< /table-caption >}}

> 🔼 본 표는 LLaMA-2 언어 모델을 사용하여 수행된 수학적 추론 작업에 대한 MathQA (1-shot) 및 GSM8K (8-shots) 데이터셋의 정확도(%)를 보여줍니다.  ▲ 기호는 비구조적 가지치기(pruning)의 이론적 매개변수 감소를 나타냅니다. 하지만 실제 훈련 과정에서는 이러한 매개변수들이 0으로 채워지기 때문에 메모리 사용량은 줄어들지 않습니다.  즉, 이 표는 가지치기 전략에 따른 모델 성능 변화를 보여주는 실험 결과를 요약한 것으로, 특히 메모리 효율과의 관련성을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Accuracy (%) of the MathQA (1-shot) & GSM8K (8-shots) in the mathematical domain under LLaMA-2. ▲ indicates the theoretical parameters reduction of non-structured pruning. However, these parameters are filled with zeros in actual training, so the memory footprint is not reduced.
> </details>





### In-depth insights


#### Memory-Efficient LoRA
본 논문은 **메모리 효율적인 LoRA 훈련 기법**에 대한 심도있는 고찰을 제공합니다. 기존 LoRA의 주요 한계점인 메모리 소모 문제를 해결하기 위해, **가지치기된(작은) 모델을 사용하여 훈련**하는 독창적인 접근 방식을 제시합니다. 이는 과다 매개변수화된 LLMs에서 많은 뉴런이 훈련에 낮은 효용성을 가지지만 추론에는 필수적이라는 직관에 기반합니다.  **가지치기된 저랭크 행렬을 얻은 후, 원래(큰) 모델에서 추론에 활용**함으로써 메모리 사용량을 크게 줄입니다.  또한, **모델 제공자가 미리 수행하는 최소 비용의 지속적 사전 훈련**을 통해 가지치기된 모델과 원래 모델 간의 지식 불일치를 해소합니다.  여러 가지치기 전략과 하류 작업에 대한 광범위한 실험 결과를 통해 LORAM의 효과를 보여주며, **700억 개 매개변수 모델을 20GB HBM GPU에서 훈련**할 수 있음을 강조합니다.  이는 기존 LoRA 훈련에 필요한 A100-80G GPU 또는 완전 미세 조정을 위한 15개의 GPU를 대체하는 획기적인 성과입니다.

#### Pruned Model Training
**프루닝된 모델 학습**은 과매개변수화된 대규모 언어 모델(LLM)의 효율적인 미세 조정을 위한 핵심 전략입니다. 이 방법은 **훈련 과정에서 계산 비용을 줄이기 위해** LLM의 일부 뉴런을 제거합니다. 이렇게 하면 메모리 사용량이 감소하고 학습 속도가 빨라집니다. 하지만 프루닝은 추론 성능에 영향을 미칠 수 있으므로, **프루닝 전략을 신중하게 선택하는 것이 중요**합니다. 효과적인 프루닝 전략은 모델의 중요한 부분을 보존하면서 불필요한 부분을 제거하는 데 중점을 둡니다.  **프루닝 후 복구 과정**을 통해 추론 성능을 유지하는 전략도 중요한 부분입니다.  **적절한 프루닝과 복구를 통해** 훈련 비용을 낮추면서 추론 성능을 유지할 수 있습니다.  따라서 **프루닝된 모델 학습**은 대규모 언어 모델의 효율성을 높이는 데 매우 중요한 역할을 합니다.  하지만 **최적의 프루닝 비율**을 찾는 것은 여전히 어려운 과제이며, 모델 구조와 하위 작업에 따라 다를 수 있습니다.

#### LORAM's Alignment
LORAM은 **잘려나간(pruned) 모델과 원래 모델 간의 지식 불일치**로 인해 성능 저하 문제를 해결하기 위해 **지식 정렬(alignment)** 전략을 제시합니다.  **미리 수행되는 저비용의 지속적 사전 훈련**을 통해, 잘려나간 모델을 원래 모델과 일치시켜 성능 저하를 최소화합니다.  이러한 사전 훈련은 **모델 공급자가 오프라인으로 한 번만 수행**하므로, 사용자는 추가적인 비용이나 노력 없이도 성능 향상의 혜택을 누릴 수 있습니다.  **이는 모델 개발자의 부담을 줄이고, 사용자의 자원 제약을 완화하는 데 기여**합니다.  결과적으로, LORAM은 메모리 효율성뿐만 아니라 모델 정렬을 통해 성능 개선까지 달성하는 효과적인 방법을 제시합니다.  **잘려나간 모델의 사전 훈련은 오프라인에서 모델 공급자가 수행**하므로, 사용자는 추가적인 비용이나 연산 없이도 성능 향상을 얻을 수 있고, 이는 **저사양 환경에서도 대규모 언어 모델을 효과적으로 미세 조정할 수 있는 가능성**을 열어줍니다.

#### QLORAM & Quantization
본 논문에서 제시된 QLORAM은 **기존 LoRA의 메모리 효율성을 획기적으로 개선하기 위해 구조적 가지치기(structured pruning)와 4비트 양자화(quantization) 기법을 LoRAM과 결합한 방법**입니다.  이는 과다 매개변수화된 LLMs에서 많은 뉴런들이 훈련에는 기여도가 낮지만 추론에는 필수적이라는 직관에 기반합니다. QLORAM은 **가지치기를 통해 훈련에 필요한 메모리를 줄이고, 추론 시에는 원래 모델의 모든 매개변수를 활용**하여 성능 저하를 최소화합니다.  **양자화는 추가적으로 메모리 사용량을 감소**시키는 역할을 합니다.  **QLORAM은 다양한 가지치기 전략 및 하위 작업에서 효과적임을 실험적으로 보여주며**, 특히 LLaMA-2-70B 모델에서 매개변수 저장 비용을 15.81배(16.95배)까지 줄이면서 LoRA 기반의 LLaMA-3.1-8B (LLaMA-2-13B)보다 우월한 성능을 달성합니다. 따라서 QLORAM은 **제한된 메모리 환경에서도 대규모 언어 모델의 효율적인 미세 조정을 가능하게 하는 중요한 기술적 진보**라고 할 수 있습니다.

#### Future Research
본 논문에서 제시된 LORAM 기법은 대규모 언어 모델의 메모리 효율적인 미세 조정을 위한 중요한 발걸음이지만, **향후 연구를 통해 개선 및 확장될 여지가 많습니다.**  특히, **다양한 모델 아키텍처 및 크기에 대한 LORAM의 일반화 성능을 평가하는 것은 중요한 과제입니다.** 또한, **현재 연구에서는 주로 지도 학습 방식에 초점을 맞추었으므로, 자기 지도 학습이나 강화 학습과 같은 다른 학습 패러다임에서 LORAM의 적용 가능성을 탐색하는 것이 필요합니다.**  **더 나아가, LORAM과 다른 메모리 효율적인 기술(예: 양자화, 압축)을 결합하여 더 큰 시너지 효과를 창출하는 연구도 기대됩니다.**  마지막으로, **LORAM의 실제적인 적용성을 높이기 위해 다양한 하드웨어 플랫폼에서의 성능을 분석하고 최적화하는 연구가 필요합니다.** 이러한 후속 연구를 통해 LORAM은 더욱 강력하고 실용적인 대규모 언어 모델 미세 조정 기법으로 발전할 수 있을 것입니다. 


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.13533/x2.png)

> 🔼 그림 2는 LoRAM과 LoRA의 학습 및 추론 과정을 비교하여 보여줍니다. (a)와 (b)는 각각 LoRA와 LoRAM의 학습 과정을, (c)와 (d)는 추론 과정을 나타냅니다. 주요 단계는 오프라인으로 진행되는 고정된 완전 계급 행렬 W0*의 처리 과정 (e)과 LoRAM 학습 (b) 및 추론 (d) 중에 온라인으로 생성되는 학습 가능한 저계급 행렬 WΔ*의 과정 (f)을 포함합니다. LoRAM은 LoRA와 달리 학습과 추론 단계에서 서로 다른 모델을 사용하는데, 이는 학습 단계에서는 가지치기된 작은 모델을 사용하고 추론 단계에서는 원래의 큰 모델을 사용하는 것을 의미합니다. 이러한 접근 방식은 메모리 효율을 높이고 성능을 향상시키는 데 기여합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2:  Comparison of LoRAM and LoRA: Training (subfigures a and b) and Inference (c and d). Key stages include the offline process of the frozen full-rank matrix 𝐖0∗superscriptsubscript𝐖0\mathbf{W}_{0}^{*}bold_W start_POSTSUBSCRIPT 0 end_POSTSUBSCRIPT start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT (subfigure e) and the online generation of the learnable low-rank matrix 𝐖Δ∗superscriptsubscript𝐖Δ\mathbf{W}_{\Delta}^{*}bold_W start_POSTSUBSCRIPT roman_Δ end_POSTSUBSCRIPT start_POSTSUPERSCRIPT ∗ end_POSTSUPERSCRIPT (f) during LoRAM training (b) and inference (d).
> </details>



![](https://arxiv.org/html/2502.13533/x5.png)

> 🔼 본 그림은 OpenHermes 데이터셋을 사용하여 LLaMA-2-13B 및 LLaMA-2-70B 모델을 학습시킨 결과에 대한 테스트 퍼플렉서티를 보여줍니다.  각 하위 그림은 다른 모델 크기와 데이터셋 조합에 대한 퍼플렉서티 변화를 나타내며, 다양한 LoRAM 변형 모델들(LORAM-Rand, LORAM-Stru, LORAM-Semi, LORAM-Unst)과 기존 LoRA 모델(7B, 13B, 70B)의 성능을 비교 분석합니다.  그림을 통해 각 모델의 학습 과정에서의 퍼플렉서티 변화 추이를 파악하고, LoRAM의 효율성과 성능을 LoRA와 비교 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: The test perplexity of training LLaMA-2-13B & LLaMA-2-70B on OpenHermes.
> </details>



![](https://arxiv.org/html/2502.13533/x6.png)

> 🔼 그림 4는 OpenOrca 데이터셋을 사용하여 LLaMA-2-13B 및 LLaMA-2-70B 모델을 미세 조정하는 동안의 테스트 당황도를 보여줍니다.  여러 가지 자르기 알고리즘(LORAM-Rand, LORAM-Stru, LORAM-Semi, LORAM-Unst)과 양자화(QLORAM)를 적용한 LORAM의 성능을 기준 모델(LoRA로 미세 조정된 7B 및 13B 모델, 미세 조정되지 않은 13B 및 70B 모델)과 비교하여 보여줍니다.  그래프는 미세 조정 반복 횟수에 따른 당황도의 변화를 보여주어 각 방법의 수렴 속도와 성능을 비교 분석하는 데 도움을 줍니다. 특히, 70B 모델에서 QLORAM의 효율성과 성능 향상을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: The test perplexity of training LLaMA-2-13B & LLaMA-2-70B on OpenOrca.
> </details>



![](https://arxiv.org/html/2502.13533/x7.png)

> 🔼 이 그림은 OpenHermes 데이터셋을 사용하여 LLaMA-3.1-70B 모델을 미세 조정했을 때의 테스트 퍼플렉서티와 다운스트림 작업 성능을 보여줍니다.  그래프는 다양한 미세 조정 방법(예: LoRA, QLoRAM-Stru)과 훈련 반복 횟수에 따른 퍼플렉서티 변화를 보여주어, LoRAM의 효율성과 성능을 평가하는 데 도움이 됩니다.  특히, QLoRAM-Stru는 매개변수 저장 비용을 크게 줄이면서도 LoRA 기반 방법들과 비교했을 때 우수한 성능을 보임을 확인할 수 있습니다. 다른 LoRAM 변형들과의 비교를 통해 다양한 가지치기 전략의 영향을 분석하고, 훈련 과정 중 퍼플렉서티 변화 추세를 확인하여, 모델의 일반화 성능과 학습 안정성을 파악하는 데 활용됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: The test perplexity & downstream performance of training LLaMA-3.1-70B on OpenHermes.
> </details>



![](https://arxiv.org/html/2502.13533/x8.png)

> 🔼 그림 6은 LLaMA-2-13B 모델에서 다양한 가지치기 전략에 따른 복원 및 정렬의 필요성을 보여줍니다.  각 가지치기 전략(무작위, 구조적, 반구조적, 비구조적)에 대해 복원 과정이 없을 때와 정렬 과정이 없을 때의 성능을 보여주는 그래프가 포함되어 있습니다.  그래프는 알파카(Alpaca) 데이터셋을 사용한 테스트 결과를 보여주며, 복원 및 정렬 과정이 성능 향상에 중요한 역할을 한다는 것을 시각적으로 보여줍니다.  특히, 구조적 가지치기의 경우 복원 과정이 없으면 성능 저하가 심각하게 나타납니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Necessity of Recovery & Alignment across different pruning strategies on LLaMA-2-13B.
> </details>



![](https://arxiv.org/html/2502.13533/x9.png)

> 🔼 본 그림은 매개변수 감소 비율을 확장했을 때의 효과를 보여줍니다. LoRA 기법을 사용하여 미세 조정된 LLaMA-2-13B 모델은 매개변수 감소 비율이 5.30배에 달하는 반면, QLORAM-STRU는 두 가지 지시어 조정 데이터 세트 모두에서 우수한 퍼플렉서티를 유지하면서 매개변수를 더욱 감소시켰습니다. 반면에 단순한 가지치기는 매개변수 감소 비율이 적을 때 퍼플렉서티가 크게 증가합니다. 매개변수 감소 비율이 28.56배에 이르면 QLORAM-STRU는 약 2.5의 효과적인 퍼플렉서티를 유지하는 반면, 단순한 가지치기는 621.98로 급증합니다. 이는 LoRAM이 기반 모델의 메모리를 극적으로 줄이면서 추론 성능을 유지하는 능력을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Effect of scaling parameter reduction ratio.
> </details>



![](https://arxiv.org/html/2502.13533/x18.png)

> 🔼 그림 8은 다양한 파라미터 축소 비율에서 여러 가지 downstream 작업에 대한 성능을 보여줍니다.  그래프는 파라미터 축소 비율이 증가함에 따라 성능이 어떻게 변화하는지를 보여주며, 특정 작업에 대한 최적의 파라미터 축소 비율을 파악하는 데 도움이 됩니다.  특히,  9.82배에서 16.95배 사이의 파라미터 감소 비율에서 최적의 성능이 나타나며, 이는 13B LoRA와 70B w/o FT를 일관되게 능가하는 것으로 나타났습니다. 하지만, 파라미터 감소 비율이 28.56배로 과도하게 높아지면 오히려 성능이 저하되는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Performance of downstream tasks across different parameter reduction ratios.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | OpenHermes | OpenOrca | Parameter
|---|---|---|---|
| Mean ± Std | Mean ± Std |  Redu. Ratio |
| 13B w/o FT | 64.28 ± 1.30 | 64.28 ± 1.30 | 1.00 × |
| 7B LoRA | 61.51 ± 1.29 | 61.42 ± 1.30 | 1.93 × |
| 13B LoRAM-Rand | 64.64 ± 1.29 | 64.49 ± 1.30 | 2.17 × |
| 13B LoRAM-Stru | 64.42 ± 1.29 | 64.32 ± 1.29 | 2.17 × |
| 13B LoRAM-Semi | 64.38 ± 1.29 | 64.73 ± 1.30 | 1.95 × |
| 13B LoRAM-Unst | 64.12 ± 1.29 | 64.68 ± 1.29 | 2.16 × |
| 70B w/o FT | 68.69 ± 1.27 | 68.69 ± 1.27 | 1.00 × |
| 13B LoRA | 65.05 ± 1.29 | 65.40 ± 1.29 | 5.30 × |
| 70B QLoRAM-Rand | 68.99 ± 1.27 | 68.46 ± 1.27 | 12.84 × |
| 70B QLoRAM-Stru | 69.10 ± 1.27 | 68.94 ± 1.27 | 12.84 × |{{< /table-caption >}}
> 🔼 본 표는 LLaMA-2 모델을 기반으로 한 공통 상식 추론(CSR) 작업에서 1-shot 설정 하에 각 하위 작업별 평균 정확도(%)를 보여줍니다.  표에는 다양한 LoRAM 변형 및 기준 모델(원본 LLaMA-2, LoRA 미세 조정된 소형 모델)의 성능이 포함되어 있으며, 각 모델의 파라미터 감소 비율도 함께 제시되어 있습니다.  각 하위 작업의 기준 성능 결과는 부록 E에 자세히 설명되어 있습니다.  이를 통해 LoRAM이 메모리 효율성을 유지하면서 공통 상식 추론 작업에서 성능 향상을 달성하는지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Average accuracy (%) of the CSR in the common sense reasoning domain (1-shot) under the LLaMA-2. Baseline results for each subtask of CSR are detailed in Appendix E.
> </details>

{{< table-caption >}}
| Method | OpenHermes Pass@1 | OpenHermes Pass@10 | OpenOrca Pass@1 | OpenOrca Pass@10 | Parameter
---|---|---|---|---|---| 
| 13B w/o FT | 17.68 | 35.37 | 17.68 | 35.37 | 1.00× | 
| 7B LoRA | 15.24 | 28.04 | 15.85 | 26.21 | 1.93× | 
| 13B LoRAM-Rand | 19.51 | 33.54 | 19.51 | 32.32 | 2.17× | 
| 13B LoRAM-Stru | 17.68 | 35.37 | 17.07 | 31.71 | 2.17× | 
| 13B LoRAM-Semi | 20.12 | 35.37 | 18.29 | 39.63 | 1.95× | 
| 13B LoRAM-Unst | 22.56 | 34.15 | 18.29 | 37.20 | 2.16× | 
| 70B w/o FT | 31.71 | 58.54 | 31.71 | 58.54 | 1.00× | 
| 13B LoRA | 18.29 | 35.98 | 18.29 | 39.02 | 5.30× | 
| 70B QLoRAM-Rand | 29.27 | 57.32 | 31.71 | 56.71 | 12.84× | 
| 70B QLoRAM-Stru | 32.32 | 58.54 | 32.32 | 59.15 | 12.84× |{{< /table-caption >}}
> 🔼 본 표는 LLaMA-2 언어 모델을 사용하여 코드 생성 작업에 대한 HumanEval 평가 결과를 보여줍니다.  Pass@1과 Pass@10 지표를 사용하여 모델 성능을 평가하며, temperature는 0.0에서 0.8까지 다양하게 설정하고 topp는 0.95로 고정하여 가장 좋은 결과를 제시합니다. 다양한 기준 모델 (예: 훈련되지 않은 모델, LoRA로 미세 조정된 모델)과 여러 가지 LORAM 변형 모델의 성능을 비교 분석하여 LORAM의 효율성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Pass@1(%) and Pass@10(%) of HumanEval in the code generation domain under LLaMA-2. The best results for all baselines are reported, selected from temperature settings in {0.0, 0.2, 0.4, 0.6, 0.8} with toppsubscripttopp\textsc{top}_{\textsc{p}}top start_POSTSUBSCRIPT p end_POSTSUBSCRIPT fixed at 0.95.
> </details>

{{< table-caption >}}
| Method | #Orig. Params | Pruning Ratio | #Pruned Params | Reduction | HBM |
|---|---|---|---|---|---| 
| LoRAM-Semi | 13015864320 | 0.50 | 6738415616 | 1.93x | 12.55 |
| LoRAM-Unst | 13015864320 | 0.55 | 6037628912 | 2.16x | 11.25 |
| LoRAM-Rand & Stru | 13015864320 | 0.65 | 6005662720 | 2.17x | 11.19 |{{< /table-caption >}}
> 🔼 표 4는 LLaMA-2-13B 모델에 대한 LoRAM 설정을 보여줍니다.  다양한 가지치기 방법의 매개변수 감소율 (Reduction)과 가지치기된 매개변수의 HBM 공간 사용량 (GB)을 비교한 표입니다. 저차원 행렬 오버헤드는 고려하지 않았습니다.  즉, 이 표는 여러 가지치기 기법(LORAM-Semi, LORAM-Unst, LORAM-Rand & Stru)을 사용하여 LLaMA-2-13B 모델의 매개변수를 얼마나 효율적으로 줄일 수 있는지, 그리고 그에 따른 HBM 메모리 사용량의 변화를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 4: LoRAM configures on LLaMA-2-13B. Comparison of different pruning methods in terms of parameter reduction ratio (Reduction) and HBM footprint (GB) of pruned parameters (HBM), ignoring low-rank matrix overhead.
> </details>

{{< table-caption >}}
| Method | #Orig. Params | Pruning Ratio | #Pruned Params | Reduction | HBM |
|---|---|---|---|---|---| 
| LoRAM-Rand & Stru | 68976648192 | 0.65 | 28099436544 | 2.45x | 52.34 |
| LoRAM-Rand & Stru | 68976648192 | 0.75 | 21488738304 | 3.21x | 40.03 |
| LoRAM-Rand & Stru | 68976648192 | 0.85 | 16272924672 | 4.24x | 30.31 |
| LoRAM-Rand & Stru | 68976648192 | 0.95 | 9662226432 | 7.14x | 18.00 |
| LoRAM-Rand & Stru | 70553706496 | 0.85 | 17849982976 | 3.95x | 33.25 |{{< /table-caption >}}
> 🔼 표 5는 LLaMA-2-70B와 LLaMA-3.1-70B 모델에 대해 다양한 가지치기 비율을 적용한 LoRAM 설정을 보여줍니다.  각 행은 다른 가지치기 비율(Pruning Ratio)을 사용하는 LoRAM 설정을 나타내며, 원래 매개변수 수(Orig. Params), 가지치기된 매개변수 수(Pruned Params), 매개변수 감소 비율(Reduction), 그리고 가지치기된 매개변수를 저장하는 데 필요한 HBM(High Bandwidth Memory) 용량(GB)을 보여줍니다. 이 표는 다양한 가지치기 전략을 사용했을 때 LoRAM의 효율성과 성능에 대한 통찰력을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: LoRAM configures on LLaMA-2-70B and LLaMA-3.1-70B with different pruning ratios.
> </details>

{{< table-caption >}}
| Method | #Orig. Params | Pruning Ratio | #Pruned Params | Reduction | HBM |
|---|---|---|---|---|---| 
| QLoRAM-Rand & Stru | 68976648192 | 0.65 | 7024859136 | 9.82x | 13.08 |
| QLoRAM-Rand & Stru | 68976648192 | 0.75 | 5372184576 | 12.84x | 10.01 |
| QLoRAM-Rand & Stru | 68976648192 | 0.85 | 4068231168 | 16.95x | 7.58 |
| QLoRAM-Rand & Stru | 68976648192 | 0.95 | 2415556608 | 28.56x | 4.50 |
| QLoRAM-Rand & Stru | 70553706496 | 0.85 | 4462495744 | 15.81x | 8.31 |{{< /table-caption >}}
> 🔼 표 6은 QLoRAM(QLORA와 LORAM을 결합한 방법)을 LLaMA-2-70B와 LLaMA-3.1-70B 모델에 적용했을 때의 결과를 보여줍니다.  다양한 가지치기 비율(Pruning Ratio)에서 매개변수 감소율(Reduction)과 사용된 HBM(High Bandwidth Memory) 용량을 보여주어,  매개변수를 더욱 공격적으로 압축했을 때의 효과를 분석합니다.  원본 모델의 크기 대비 매개변수 크기 감소율이 9.82배에서 최대 28.56배까지 달하는 것을 확인할 수 있습니다.  이는 QLoRA의 양자화 기법과 LORAM의 가지치기 기법을 병행하여 메모리 사용량을 크게 줄이는 효과를 보여줍니다.  표는 각 가지치기 비율에 따른 매개변수 개수와 HBM 사용량을 보여주어,  메모리 효율적인 모델 학습을 위한 최적의 가지치기 비율을 결정하는 데 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: QLoRAM configures on LLaMA-2-70B and LLaMA-3.1-70B with , demonstrating more aggressive parameter compression.
> </details>

{{< table-caption >}}
| LLaMA-3.1 | GSM8K | Parameter Reduction Ratio |
|---|---|---|
| 8B w/o Fine-Tuning | 55.27 | 8.79× |
| 8B LoRA (OpenHermes 400) | 55.80 | 8.79× |
| 70B w/o Fine-Tuning | 75.28 | 1.00× |
| 70B QLoRAM-Stru 400 (OpenHermes 400) | 80.36 | 15.81× |
| 70B QLoRAM-Stru 400 (GSM8K 100) | 77.18 | 15.81× |
| 70B QLoRAM-Stru 400 (GSM8K 200) | 79.15 | 15.81× |
| 70B LoRA (OpenHermes 400) | 80.74 | 1.00× |{{< /table-caption >}}
> 🔼 표 7은 특정 영역 미세 조정을 위해 GSM8K 데이터셋에서 LoRAM의 성능 평가 결과를 보여줍니다.  다양한 설정에 따른 정확도(%)와 파라미터 감소 비율을 보여줍니다.  본 실험은 LoRAM이 일반적인 지시어 미세 조정을 넘어 특정 도메인 작업에서도 강력함을 보여주는 것을 목표로 합니다. 표에는 기본 모델(미세 조정 없음)과 LoRA로 미세 조정된 소규모 모델과 LoRAM의 결과를 비교하여 LoRAM의 효율성과 성능 향상을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Evaluation of LoRAM on the GSM8K dataset for domain-specific fine-tuning. Results show accuracy (%) and parameter reduction ratios for different configurations.
> </details>

{{< table-caption >}}
| Model | #Model Params | Reduction Ratio | Memory | Latency | Throughput |
|---|---|---|---|---|---| 
| **LLaMA-2** | **#Model Params** | **Reduction Ratio** | **Memory** | **Latency** | **Throughput** |
| 7B LoRA | 6.73B | 1.93× | 30,517 | **134.27** | **7.626** |
| 13B LoRA | 13.02B | 1.00× | 51,661 | 206.07 | 4.969 |
| 13B LoRAM-Stru | **6.01B** | **2.17×** | **29,799** | 147.86 | 6.925 |{{< /table-caption >}}
> 🔼 표 8은 LoRAM과 LoRA 모델의 온라인 학습 단계에서 피크 메모리(MiB), 대기 시간(초), 처리량(샘플/초)을 비교한 표입니다.  결과는 1024개의 샘플(배치 크기 128, 마이크로 배치 크기 4, 시퀀스 길이 512) 작업량을 기반으로 합니다. 이 표는 LoRAM이 메모리 사용량과 대기 시간 측면에서 LoRA와 비슷한 성능을 보이면서도 처리량 측면에서 약간의 이점을 제공한다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Comparison of peak memory (MiB), latency (s), and throughput (samples/s) during the online training phase for LoRAM and LoRA models. Results are based on a workload of 1024 samples (batch size 128, micro-batch size 4, sequence length 512).
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