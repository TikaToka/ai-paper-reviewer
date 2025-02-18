---
title: "Region-Adaptive Sampling for Diffusion Transformers"
summary: "영역 적응형 샘플링(RAS)을 사용하여 확산 변환기의 속도를 최대 2.5배 향상시키는 획기적인 방법을 제시합니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Generation", "🏢 Microsoft Research",]
showSummary: true
date: 2025-02-14
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.10389 {{< /keyword >}}
{{< keyword icon="writer" >}} Ziming Liu et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-17 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.10389" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.10389" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 확산 모델들은 연속적인 순방향 패스에 의존하여 실시간 성능에 제약이 있었습니다. 이러한 문제를 해결하기 위해 기존 연구는 주로 샘플링 단계 수를 줄이거나 중간 결과를 재사용하는 데 초점을 맞추었지만, 이미지 내 공간적 영역의 변화를 활용하지 못했습니다. 본 논문에서는 **Diffusion Transformer(DiT)의 유연성을 활용**하여 이미지 내 각 영역에 다른 샘플링 비율을 동적으로 할당하는 새로운 샘플링 전략인 **RAS(Region-Adaptive Sampling)**를 제시합니다. RAS는 모델의 초점 영역을 기반으로 특정 영역만 업데이트하고 다른 영역은 이전 단계의 캐시된 노이즈를 사용합니다.



RAS는 Stable Diffusion 3과 Lumina-Next-T2I에서 각각 최대 2.36배와 2.51배의 속도 향상을 달성했습니다. 또한, 사용자 연구를 통해 RAS가 **인간 평가에서 유사한 품질을 유지하면서 1.6배의 속도 향상**을 달성함을 보였습니다. RAS는 **훈련이 필요 없고 DiT의 유연성을 활용**하여 다양한 영역에 적용 가능하며, 실시간 응용 분야를 위한 확산 변환기의 효율성을 크게 높입니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 이미지 내 영역의 중요도에 따라 다른 샘플링 비율을 동적으로 할당하는 새로운 샘플링 전략인 RAS를 제시합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} RAS는 기존 방법에 비해 속도를 최대 2.5배 향상시키면서 이미지 품질 저하를 최소화합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} RAS는 인간 평가에서도 기존 방법과 유사한 품질을 제공하면서 속도를 1.6배 향상시킵니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **확산 변환기의 효율성을 크게 향상**시키는 새로운 샘플링 전략을 제시하여 실시간 응용 분야에 대한 잠재력을 높입니다. **영역별 적응형 샘플링(RAS)**은 기존의 균일한 샘플링 방법과 달리 이미지 내 영역의 중요도에 따라 다른 샘플링 비율을 동적으로 할당하여 계산 비용을 줄입니다. 이는 특히 고해상도 이미지 생성과 같은 계산 집약적인 작업에서 큰 효율성 향상을 가져옵니다. 또한, 본 논문에서 제시된 방법은 다른 확산 모델에도 적용 가능하며, **향후 연구를 위한 새로운 가능성을 제시**합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.10389/extracted/6183550/pics/drop_cnt_4.png)

> 🔼 그림 1은 RAS(Region-Adaptive Sampling) 기법을 시각적으로 보여줍니다.  이미지의 주요 피사체와 세부 묘사가 필요한 영역은 다른 영역보다 더 많은 샘플링 단계를 거칩니다. 각 블록은 패치화된 잠재 토큰을 나타내며,  주요 피사체와 세부 영역일수록 더 진한 색상으로 표현되어 많은 단계의 샘플링을 받았음을 시각적으로 보여줍니다. 이는 RAS가 이미지 영역별로 샘플링 비율을 동적으로 조정하여 효율성을 높이는 방법을 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: The main subject and the regions with more details are brushed for more steps than other regions in RAS. Each block represents a patchified latent token.
> </details>





{{< table-caption >}}
| Symbol | Description |
|---|---| 
|  `t`  | The current timestep |
|  `N`  | The noise output of the DiT model |
|  `
̃N`  | The cached noise output from the previous timestep |
|  `
̂N`  | The estimated full-length noise calculated with `N` and `
̃N` |
|  `S`  | The unpatchified image sample |
|  `x`  | The patchified input of the DiT model |
|  `M`  | Mask generated to drop certain tokens in the input |
|  `D`  | The number of times the tokens in a patch being dropped |{{< /table-caption >}}

> 🔼 이 표는 논문에서 사용된 기호들의 의미를 설명합니다. 각 기호는 해당하는 수학적 또는 기술적 용어와 함께 정의되어 있어, 논문의 내용을 이해하는 데 도움을 줍니다.  예를 들어, 't'는 현재 시간 단계를, 'N'은 DiT 모델의 노이즈 출력을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Meanings of the symbols that are used in this paper
> </details>





### In-depth insights


#### RAS: Adaptive Sampling
RAS 기반 적응형 샘플링은 확산 모델의 추론 속도를 높이기 위한 혁신적인 방법입니다. 기존의 방법들이 모든 영역에 동일한 샘플링 비율을 적용했던 반면, RAS는 이미지 내 영역별 중요도에 따라 **동적으로 샘플링 비율을 조정**합니다. **DiT(Diffusion Transformer)의 유연성**을 활용하여 특정 영역에 집중적으로 샘플링 단계를 할당하고, 다른 영역은 이전 단계의 노이즈 결과를 재사용함으로써 계산량을 줄입니다. 이는 모델이 각 샘플링 단계에서 집중하는 영역이 연속성을 갖는다는 관찰에 기반합니다. **실험 결과, RAS는 Stable Diffusion 3과 Lumina-Next-T2I에서 속도 향상을 달성**하며, 인간 평가에서도 품질 저하 없이 속도 향상을 보였습니다.  RAS는 효율적인 확산 트랜스포머를 위한 중요한 진전으로, 실시간 응용에 대한 가능성을 높입니다.  **주요 강점은 학습이 필요없는 트레이닝-프리 방식**이라는 점과 영역별 중요도를 고려한 **지능적인 샘플링 전략**입니다.

#### DiT Inference Speedup
본 논문은 Diffusion Transformer (DiT)의 추론 속도 향상에 대해 심도있게 다룹니다. **기존의 U-Net 기반 확산 모델과 달리 DiT는 공간적 제약 없이 가변적인 토큰 수를 처리할 수 있는 유연성을 제공**합니다. 이러한 특징을 이용하여 논문에서는 영상의 각 영역에 따라 다른 샘플링 비율을 동적으로 할당하는 새로운 샘플링 전략인 RAS (Region-Adaptive Sampling)를 제안합니다. **RAS는 DiT 모델의 집중 영역을 파악하여 해당 영역만 집중적으로 업데이트**하고, 나머지 영역은 이전 단계의 캐시된 노이즈를 재사용하여 연산량을 줄입니다. 이를 통해 **Stable Diffusion 3과 Lumina-Next-T2I 모델에서 최대 2.5배의 속도 향상**을 달성했으며,  **주관적 평가에서도 유사한 화질을 유지**하면서 속도 향상을 보였습니다.  이는 **실시간 응용을 위한 효율적인 DiT 모델 구현**에 중요한 발걸음입니다.  특히, **영역별 중요도에 따라 연산량을 조절**하는 아이디어는 DiT의 강점을 최대한 활용하여 효율성을 극대화하는 훌륭한 전략이며, 향후 연구에서 DiT 기반 확산 모델의 성능 향상에 중요한 기여를 할 것으로 예상됩니다.  본 논문의 **RAS 기법은 DiT 모델의 효율성을 크게 개선**시켜 실시간 응용 가능성을 높였다는 점에서 큰 의의를 가집니다.

#### Regional Focus Analysis
논문에서 "지역 집중 분석"이라는 제목의 섹션은 **확산 모델(Diffusion Model)이 이미지 생성 과정에서 특정 영역에 집중하는 현상**을 분석한 부분일 것으로 예상됩니다. 이는 단순히 이미지 전체에 일률적으로 처리하는 것이 아니라, **의미있는 영역(예: 주요 객체)에 더 많은 연산 자원을 할당**하여 효율성을 높이고 성능을 향상시키는 전략을 수립하기 위한 중요한 단계입니다.  분석에는 각 단계에서 모델이 어떤 영역에 집중하는지, 그리고 그 집중도가 시간에 따라 어떻게 변화하는지를 정량적으로 측정하고 분석하는 방법이 포함될 것입니다. 이를 통해 **영역별 샘플링 비율을 동적으로 조절하는 알고리즘 설계**에 필요한 기초 자료를 확보할 수 있습니다.  **시간적 연속성 분석**을 통해 연속적인 단계에서 모델의 초점이 어떻게 이어지는지 파악하고, 이를 바탕으로 계산량을 줄이는 효율적인 샘플링 전략을 세울 수 있습니다.  결론적으로, 이 분석은 **단순히 속도 향상을 넘어 이미지 품질 저하 없이 효율적인 연산을 달성하는 데 중요한 역할**을 할 것으로 보입니다.

#### Human Evaluation
본 논문에서 인간 평가는 **RAS(Region-Adaptive Sampling) 기법이 처리 속도를 향상시키면서도 이미지 품질을 유지하는지**를 확인하기 위해 수행되었습니다. 100명의 참가자들이 Stable Diffusion 3과 Lumina-Next-T2I 모델을 사용하여 생성된 이미지들을 비교 평가했습니다. 각 프롬프트에 대해 기존 방식으로 생성된 이미지 하나와 RAS를 적용하여 생성된 이미지 하나를 제시하여 품질을 비교하도록 했습니다. 그 결과, **RAS는 기존 방식 대비 최대 1.6배의 속도 향상**을 보였으며, **인간 평가자들은 두 방식으로 생성된 이미지의 품질에 큰 차이를 느끼지 못했습니다.** 이는 RAS가 속도 향상과 품질 유지를 동시에 달성할 수 있음을 시사하는 중요한 결과입니다.  **하지만, 이러한 인간 평가는 주관적일 수 있으며, 더욱 엄격한 객관적 지표를 통한 추가적인 검증이 필요**하다는 점을 염두에 두어야 합니다.  **향후 연구에서는 더욱 다양한 프롬프트와 더 많은 참가자를 대상으로 한 평가를 통해 RAS의 일반화 성능을 측정**할 수 있을 것입니다.

#### Future Work
본 논문에서 제시된 RAS 기법은 확산 트랜스포머의 효율성을 크게 향상시키는 잠재력을 보여주지만, **향후 연구를 통해 개선 및 확장될 여지**가 많습니다.  먼저, **다양한 확산 모델 아키텍처 및 이미지 모달리티에 대한 RAS 적용성**을 더욱 폭넓게 검증해야 합니다.  현재 연구는 Stable Diffusion 3과 Lumina-Next-T2I에 국한되어 있으므로, 다른 모델들에 대한 실험 결과를 통해 일반화 가능성을 확인해야 합니다. 또한, **현재 사용되는 지역 식별 메트릭의 정교화**가 필요합니다.  잡음의 표준 편차나 L2 노름을 기반으로 한 지역 중요도 판단은 아직 개선의 여지가 있으며, 더욱 정확하고 효율적인 메트릭 개발을 통해 RAS의 성능을 더욱 높일 수 있습니다.  아울러, **다양한 계산 자원 환경에서의 RAS 성능 최적화**도 중요한 과제입니다.  GPU 메모리 관리 및 병렬 처리 최적화를 통해 더욱 효율적인 구현이 가능하며, 특히 메모리 제약이 큰 환경에서의 성능 향상에 주력해야 합니다. 마지막으로, **RAS를 다른 생성 모델에 적용**하는 연구가 필요합니다.  본 논문의 아이디어는 확산 모델에 국한되지 않고, 다른 생성 모델에도 적용 가능한 일반적인 원리를 포함하고 있을 가능성이 높습니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.10389/extracted/6183550/pics/lumina_case.png)

> 🔼 (a)는 논문의 실험 결과 중 하나로, Lumina-Next-T2I 모델을 사용하여 RAS(Region-Adaptive Sampling) 기법의 성능을 평가한 결과를 보여줍니다. 그림에는 RAS 기법을 적용했을 때와 적용하지 않았을 때의 이미지 생성 시간 및 이미지 품질(FID, CLIP score)을 비교 분석한 결과가 시각적으로 나타나 있습니다. RAS 기법을 사용하면 이미지 생성 속도가 향상되는 동시에 이미지 품질 저하가 최소화됨을 보여줍니다.  구체적으로, 다양한 RAS 설정(샘플링 비율 변화) 하에서의 성능 비교 결과가 제시되어 RAS의 유연성 및 효율성을 강조합니다.
> <details>
> <summary>read the caption</summary>
> (a) Lumina-Next-T2I
> </details>



![](https://arxiv.org/html/2502.10389/extracted/6183550/pics/sd3_case.png)

> 🔼 그림 (b)는 Stable Diffusion 3 모델을 사용하여 RAS 기법을 적용한 결과를 보여줍니다.  RAS의 여러 설정(sampling ratio)에 따른 이미지 생성 시간 및 품질을 비교 분석하여 RAS의 효율성을 보여주는 결과입니다. 여러 개의 이미지가 나열되어 있으며, 각 이미지는 RAS의 sampling ratio가 다르게 적용된 결과를 시각적으로 보여줍니다.  각 이미지에 대한 세부 정보는 본문을 참고해야 합니다.
> <details>
> <summary>read the caption</summary>
> (b) Stable Diffusion 3
> </details>



![](https://arxiv.org/html/2502.10389/extracted/6183550/pics/lumina_fid.png)

> 🔼 그림 (c)는 Lumina-Next-T2I 모델에 대해 RAS(Region-Adaptive Sampling)와 Rectified Flow 방법을 사용했을 때의 FID(Fréchet Inception Distance) 점수를 비교한 그래프입니다.  RAS는 다양한 샘플링 비율(100%, 75%, 50%, 25%, 12.5%)을 적용하여 샘플링 단계 수를 조절하고, Rectified Flow는 샘플링 단계 수 자체를 줄이는 방식입니다. 그래프는 각 방법의 이미지 생성 시간(x축)과 FID 점수(y축)의 관계를 보여줍니다.  RAS는 Rectified Flow에 비해 동일한 생성 시간 내에서 더 낮은 FID 점수를 달성하며, 효율성을 개선했음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (c) Lumina-Next-T2I FID RAS VS Rectified Flow
> </details>



![](https://arxiv.org/html/2502.10389/extracted/6183550/pics/lumina_clip.png)

> 🔼 그림 (d)는 Lumina-Next-T2I 모델을 사용하여 RAS(Region-Adaptive Sampling) 방법과 기존의 Rectified Flow 방법의 성능을 CLIP Score를 기준으로 비교한 그래프입니다.  x축은 이미지 생성에 걸린 시간(초)이고, y축은 CLIP Score 값입니다.  다양한 샘플링 비율(RAS-30, RAS-15, RAS-10, RAS-7, RAS-6, RAS-5)을 가진 RAS 방법이 Rectified Flow 방법보다 더 높은 CLIP Score를 달성했음을 보여줍니다. 이는 RAS 방법이 이미지 품질을 저하시키지 않고 연산 속도를 향상시킬 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (d) Lumina-Next-T2I CLIP Score RAS VS Rectified Flow
> </details>



![](https://arxiv.org/html/2502.10389/extracted/6183550/pics/human_eval.png)

> 🔼 그림 (e)는 Stable Diffusion 3과 Lumina-Next-T2I 모델에서 기본 설정과 RAS(Region-Adaptive Sampling) 기법을 사용한 결과를 비교한 사용자 평가 결과를 보여줍니다. RAS는 기본 설정 대비 Stable Diffusion 3에서는 처리량이 1.625배, Lumina-Next-T2I에서는 1.561배 향상되었음을 나타냅니다.  막대 그래프는 사용자들이 두 모델의 출력 품질을 비교한 결과를 보여주는데, RAS가 속도 향상에도 불구하고 품질 저하 없이 유사한 수준의 성능을 제공함을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (e) Default VS RAS (1.625x throughput for Stable Diffusion 3 and 1.561x for Lumina-Next-T2I) Human Evaluation
> </details>



![](https://arxiv.org/html/2502.10389/extracted/6183550/pics/similarity.png)

> 🔼 그림 2는 Region-Adaptive Sampling (RAS) 방법의 성능을 보여줍니다. (a)와 (b)는 Lumina-Next-T2I와 Stable Diffusion 3 모델에서 RAS를 사용했을 때의 속도 향상을 각각 30단계와 28단계로 나누어 보여줍니다. (c)와 (d)는 RAS의 여러 설정값을 비교하여 기존의 Rectified Flow 방법보다 이미지 품질과 텍스트 일치도 면에서 우수함을 보여줍니다. RAS-X는 총 X개의 샘플링 단계를 사용하는 RAS를 의미합니다. (e)는 사용자 연구 결과로, RAS가 기본 모델 설정과 비슷한 품질을 유지하면서 약 1.6배의 속도 향상을 달성했음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: (a)(b) Accelerating Lumina-Next-T2I and Stable Diffusion 3, with 30 and 28 steps separately. (c)(d) Multiple configurations of RAS outperform rectified flow in both image qualities and text-following. RAS-X stands for RAS with X sampling steps in total. (e) RAS achieves comparable human-evaluation results with the default model configuration while achieving around 1.6x speedup.
> </details>



![](https://arxiv.org/html/2502.10389/extracted/6183550/pics/coefficient.png)

> 🔼 이 그림은 확산 모델의 각 단계에서 예측된 노이즈를 시각화한 것입니다.  Diffusion Transformer (DiT) 모델이 각 단계마다 이미지의 특정 영역에 집중하고, 이러한 집중 영역이 연속적인 단계에서도 지속적으로 유지됨을 보여줍니다.  즉, 모델이 이미지의 특징을 단계별로 점진적으로 세밀하게 다듬어나가는 과정을 시각적으로 보여주는 것입니다.  어떤 영역은 여러 단계에 걸쳐 지속적으로 집중하는 반면, 다른 영역은 특정 단계에서만 집중 대상이 되는 것을 확인할 수 있습니다. 이는 Region-Adaptive Sampling (RAS) 기법의 핵심 아이디어를 시각적으로 설명하기 위한 그림입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Visualization of predicted noise of each step. DiT model focuses on certain regions during each step and the change in focus is continuous across steps.
> </details>



![](https://arxiv.org/html/2502.10389/extracted/6183550/pics/drop_overview.png)

> 🔼 그림 4는 연속적인 두 샘플링 단계 사이의 NDCG(Normalized Discounted Cumulative Gain) 값을 보여줍니다. NDCG는 관련성 순위를 평가하는 지표이며, 이 그림에서는 연속적인 단계에서 모델의 초점이 되는 토큰(tokens)의 순위가 얼마나 유사한지를 보여줍니다.  그래프에서 y축은 NDCG 값(0에서 1 사이), x축은 샘플링 단계를 나타냅니다.  전체 확산 과정(diffusion process) 동안 NDCG 값이 높게 유지되는 것은 연속적인 단계에서 모델의 주요 초점이 되는 영역이 일관성을 유지함을 시사합니다. 즉, 모델이 이전 단계에서 집중했던 영역과 유사한 영역에 다음 단계에서도 계속 집중한다는 의미입니다. 이러한 일관성은 RAS(Region-Adaptive Sampling) 방법의 효율성을 높이는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: NDCG [21, 48] for each pair of adjacent sampling steps is high throughout the diffusion process, marking the similarities in the ranking of focused tokens ranging from 0 to 1.
> </details>



![](https://arxiv.org/html/2502.10389/x1.png)

> 🔼 이 그림은 RAS(Region-Adaptive Sampling)의 설계 개요를 보여줍니다. 기존의 확산 모델과 달리, RAS는 이미지의 모든 영역을 매 단계마다 처리하는 대신, 모델이 현재 단계에서 집중하는 영역(fast-update regions)만 DiT(Diffusion Transformer) 모델에 전달하여 처리합니다.  나머지 영역(slow-update regions)은 이전 단계의 노이즈 출력을 재사용하여 계산량을 줄입니다. 이를 통해 계산 효율성을 높이고, 이미지 생성 속도를 향상시킵니다.  그림에서는 각 단계의 fast-update 영역이 DiT 모델에 입력되고, 결과가 slow-update 영역과 병합되어 다음 단계의 입력으로 사용되는 과정을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Overview of RAS design. Only current fast-update regions of each step are passed to the model.
> </details>



![](https://arxiv.org/html/2502.10389/x2.png)

> 🔼  그림 6은 Python으로 작성된 RAS의 한 단계를 보여줍니다. 원래 스케줄러에서 RAS로 전환하기 위해서는 단 두 개의 함수만 추가하면 됩니다. 이 그림은 RAS의 구현이 간단하고 기존 시스템에 쉽게 통합될 수 있음을 시각적으로 보여줍니다. 그림은 RAS가 기존의 스케줄러에 어떻게 통합되는지 보여주는 코드 스니펫을 포함하여, RAS의 메커니즘에 대한 더 깊이 있는 이해를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Sample Step with RAS in Python. Only two extra functions are needed to switch from the original scheduler to RAS.
> </details>



![](https://arxiv.org/html/2502.10389/x3.png)

> 🔼 그림 7은 RAS(Region-Adaptive Sampling)의 핵심 구성 요소인 자체 어텐션 모듈을 보여줍니다. 이 모듈은 어텐션 복구(Attention Recovery) 기법을 사용하여 생성 품질을 향상시킵니다. 그림은 활성 토큰(active tokens)의 입력 은닉 상태, 쿼리, 키, 값, 어텐션 출력을 나타내는 변수들을 보여줍니다. 여기서 활성 토큰이란 모델이 현재 단계에서 집중하는 영역의 토큰을 의미합니다. 또한, 키와 값 캐시(key and value caches)를 사용하여 이전 단계의 정보를 활용하고, 초점이 덜 맞춰진 영역(not-focused area)의 키와 값은 이전 단계의 캐시를 사용하여 추정합니다. PIT(Permutation Invariant Transformation) GeMM 커널을 사용하여 키와 값 캐시를 부분적으로 업로드하는 산포(scatter) 연산을 이전 프로젝션에 통합하여 효율성을 높입니다. 
> <details>
> <summary>read the caption</summary>
> Figure 7: A RAS self-attention module using Attention Recovery to enhance generation quality. Xat,lsuperscriptsubscript𝑋𝑎𝑡𝑙X_{a}^{t,l}italic_X start_POSTSUBSCRIPT italic_a end_POSTSUBSCRIPT start_POSTSUPERSCRIPT italic_t , italic_l end_POSTSUPERSCRIPT, Qat,lsuperscriptsubscript𝑄𝑎𝑡𝑙Q_{a}^{t,l}italic_Q start_POSTSUBSCRIPT italic_a end_POSTSUBSCRIPT start_POSTSUPERSCRIPT italic_t , italic_l end_POSTSUPERSCRIPT, Kat,lsuperscriptsubscript𝐾𝑎𝑡𝑙K_{a}^{t,l}italic_K start_POSTSUBSCRIPT italic_a end_POSTSUBSCRIPT start_POSTSUPERSCRIPT italic_t , italic_l end_POSTSUPERSCRIPT, Vat,lsuperscriptsubscript𝑉𝑎𝑡𝑙V_{a}^{t,l}italic_V start_POSTSUBSCRIPT italic_a end_POSTSUBSCRIPT start_POSTSUPERSCRIPT italic_t , italic_l end_POSTSUPERSCRIPT and Oat,lsuperscriptsubscript𝑂𝑎𝑡𝑙O_{a}^{t,l}italic_O start_POSTSUBSCRIPT italic_a end_POSTSUBSCRIPT start_POSTSUPERSCRIPT italic_t , italic_l end_POSTSUPERSCRIPT represent the input hidden states, query, key, value and attention output of active tokens on layer l𝑙litalic_l during step t𝑡titalic_t, respectively. Kt,lsuperscript𝐾𝑡𝑙K^{t,l}italic_K start_POSTSUPERSCRIPT italic_t , italic_l end_POSTSUPERSCRIPT and Vt,lsuperscript𝑉𝑡𝑙V^{t,l}italic_V start_POSTSUPERSCRIPT italic_t , italic_l end_POSTSUPERSCRIPT denote the key and value caches. The scatter operation to partially upload the key and value caches are fused into the previous projection using a PIT GeMM kernel. The keys and values of the not-focused area (Kit,lsubscriptsuperscript𝐾𝑡𝑙𝑖K^{t,l}_{i}italic_K start_POSTSUPERSCRIPT italic_t , italic_l end_POSTSUPERSCRIPT start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT and Vit,lsubscriptsuperscript𝑉𝑡𝑙𝑖V^{t,l}_{i}italic_V start_POSTSUPERSCRIPT italic_t , italic_l end_POSTSUPERSCRIPT start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT) are estimated with the cache from the last sampling step (Kt−1,lsuperscript𝐾𝑡1𝑙K^{t-1,l}italic_K start_POSTSUPERSCRIPT italic_t - 1 , italic_l end_POSTSUPERSCRIPT and Vt−1,lsuperscript𝑉𝑡1𝑙V^{t-1,l}italic_V start_POSTSUPERSCRIPT italic_t - 1 , italic_l end_POSTSUPERSCRIPT).
> </details>



![](https://arxiv.org/html/2502.10389/x4.png)

> 🔼 그림 8은 RAS가 Lumina-Next-T2I 및 Stable Diffusion 3 모델에 적용되었을 때의 결과를 보여줍니다.  각 이미지는 동일한 프롬프트를 사용하여 생성되었지만, RAS는 다양한 영역에 대해 다른 샘플링 비율을 적용하여 생성 속도를 높였습니다.  이 그림은 RAS가 이미지의 중요한 영역(예: 주요 피사체)에 더 많은 샘플링 단계를 할당하고, 덜 중요한 영역에는 더 적은 단계를 할당하여, 전체적인 이미지 품질을 유지하면서 생성 시간을 단축하는 효과를 시각적으로 보여줍니다.  다양한 프롬프트에 대한 결과를 보여주어, RAS의 적응력을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Visualization of RAS on Lumina-Next-T2I and Stable Diffusion 3.
> </details>



![](https://arxiv.org/html/2502.10389/extracted/6183550/pics/human/combined.png)

> 🔼 그림 9는 RAS가 L2 노름을 측정 기준으로 사용하여 Lumina-Next-T2I 모델의 추론 속도를 높이는 방법을 보여줍니다. 샘플 비율은 50%, 총 샘플링 단계는 30단계입니다. 그림은 20번째 단계의 노이즈, 마스크, 샘플을 보여줍니다. 이는 모델이 이미지의 특정 영역에 집중하여 효율성을 높이는 RAS의 지역 적응적 샘플링 전략을 시각적으로 보여줍니다.  주요 피사체는 더 많은 샘플링 단계를 거치는 반면, 배경과 같은 단순한 영역은 상대적으로 적은 단계를 거칩니다.  이를 통해 모델은 제한된 계산 자원으로도 더 높은 화질의 이미지를 생성할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: RAS using norm as the metric, accelerating Lumina-Next-T2I with 50% sample ratio and 30 total steps. The noise, masks and samples are from the 20th step.
> </details>



![](https://arxiv.org/html/2502.10389/x5.png)

> 🔼 그림 10은 RAS(Region-Adaptive Sampling)와 기본 샘플링 방법을 비교하여 각 잠재 토큰에 대한 활성 샘플링 단계를 보여줍니다.  RAS는 이미지의 주요 영역(예: 물체)에 더 많은 샘플링 단계를 할당하고, 덜 중요한 영역(예: 배경)에는 더 적은 샘플링 단계를 할당하여 계산 효율을 높입니다.  그림은 여러 이미지에 대한 RAS와 기본 샘플링의 결과를 비교하여, RAS가 주요 영역에 집중하여 샘플링 단계를 효율적으로 사용하는 것을 시각적으로 보여줍니다.  각 이미지는 주요 영역과 배경 영역의 샘플링 단계 수를 색상으로 구분하여 표시합니다.  이를 통해 RAS가 이미지의 중요한 부분에 집중하여 효율적으로 샘플링하는 것을 명확히 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: RAS VS default sampling and the active sampling step for each latent token.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | Sample Steps | Sampling Ratio | Throughput (iter/s) ↑ | FID ↓ | sFID ↓ | CLIP score ↑ |
|---|---|---|---|---|---|---|
| **Stable Diffusion 3** |  |  |  |  |  |  |
| RFlow | 5 | 100% | 1.43 | 39.70 | 22.34 | 29.84 |
| RAS | 7 | 25.0% | 1.45 | 31.99 | 21.70 | 30.64 |
| RAS | 7 | 12.5% | 1.48 | 32.86 | 22.10 | 30.55 |
| RAS | 6 | 25.0% | 1.52 | 33.24 | 21.51 | 30.38 |
| RAS | 6 | 12.5% | 1.57 | 33.81 | 21.62 | 30.33 |
| RFlow | 4 | 100% | 1.79 | 61.92 | 27.42 | 28.45 |
| RAS | 5 | 25.0% | 1.94 | 51.92 | 25.67 | 29.06 |
| RAS | 5 | 12.5% | 1.99 | 53.24 | 26.04 | 28.94 |
| **Lumina-Next-T2I** |  |  |  |  |  |  |
| RFlow | 7 | 100% | 0.49 | 48.19 | 38.60 | 28.65 |
| RAS | 10 | 25.0% | 0.59 | 45.67 | 32.36 | 29.82 |
| RAS | 10 | 12.5% | 0.65 | 47.34 | 32.69 | 29.75 |
| RFlow | 5 | 100.% | 0.69 | 96.53 | 59.26 | 26.03 |
| RAS | 7 | 25.0% | 0.70 | 53.93 | 39.80 | 28.85 |
| RAS | 7 | 12.5% | 0.74 | 54.62 | 40.23 | 28.83 |
| RAS | 6 | 25.0% | 0.75 | 67.16 | 46.46 | 27.85 |
| RAS | 6 | 12.5% | 0.78 | 67.88 | 45.88 | 27.83 |{{< /table-caption >}}
> 🔼 표 2는 COCO Val2014 데이터셋의 1024x1024 이미지에 대해 RAS(Region-Adaptive Sampling)를 적용한 결과와 기존 Rectified Flow 방식의 성능을 비교 분석한 표입니다.  단순히 샘플링 단계를 줄이는 기존 방법과 달리, RAS는 이미지 영역별로 다른 샘플링 비율을 적용하여 연산량을 줄이면서도 이미지 품질을 유지하거나 개선하는 효과를 보여줍니다. 표에는 각 방법의 샘플링 단계 수, 샘플링 비율, 처리 속도(iter/s), FID(Fréchet Inception Distance), sFID(Sliding FID), CLIP score 등 다양한 지표가 포함되어 있어 RAS의 성능 우위를 다각적으로 보여줍니다. 특히, 동일한 처리 속도를 가정했을 때 RAS가 FID, sFID 점수는 낮추면서 CLIP score는 높이는 Pareto 개선 효과를 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Pareto Improvements of rectified flow with RAS on COCO Val2014 1024×\times×1024.
> </details>

{{< table-caption >}}
| Method | FID ↓ | sFID ↓ | CLIP score ↑ |
|---|---|---|---|
| Default | 35.81 | 18.41 | 30.13 |
| Static Sampling Freq. | 37.92 | 19.11 | 29.98 |
| Random Dropping | 43.19 | 22.23 | 29.65 |
| W/O Error Reset | 46.10 | 24.85 | 30.41 |{{< /table-caption >}}
> 🔼 표 3은 Stable Diffusion 3 모델을 사용한 RAS(Region-Adaptive Sampling)의 ablation study 결과를 보여줍니다.  동적 샘플링 비율, 영역 식별, 에러 재설정, 키-값 복구 등 RAS의 주요 기술들을 각각 제거했을 때, 이미지 생성 품질에 미치는 영향을 FID, SFID, CLIP Score 지표를 통해 평가합니다. 모든 기술이 고품질 이미지 생성에 필수적임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Ablation Study on Stable Diffusion 3. All techniques including dynamic sampling ratio, region identifying, error reset, and key & value recovery are necessary for high quality generation.
> </details>

{{< table-caption >}}
| Method | Timesteps | FID ↓ | sFID ↓ | CLIP score ↑ |
|---|---|---|---|---|
| **Default** | 28 | 24.30 | 26.26 | 31.34 |
| W/O | 28 | 31.36 | 20.19 | 31.29 |
| **Default** | 10 | 35.81 | 18.41 | 30.13 |
| W/O | 10 | 32.33 | 20.21 | 30.27 |{{< /table-caption >}}
> 🔼 표 4는 Stable Diffusion 3 모델에 대해 L2 노름을 RAS의 평가 지표로 사용한 실험 결과를 보여줍니다. 처음 4단계의 샘플 비율은 생성 품질을 보장하기 위해 100%로 설정되었습니다. 표에는 다양한 방법(RFlow, RAS-Std, RAS-Norm, Random)을 사용한 7단계 샘플링에 대한 처리량(iter/s), FID, sFID, CLIP 점수 등이 포함되어 있습니다. RAS-Std는 표준 편차를, RAS-Norm은 L2 노름을 지표로 사용한 RAS를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Experiments on using L2 Norm as the metric for RAS on Stable Diffusion 3. The sample ratio of the first 4 steps is 100% to guarantee generation qualities.
> </details>

{{< table-caption >}}
| Method | Sample Steps | Sampling Ratio | Throughput (iter/s) ↑ | FID ↓ | sFID ↓ | CLIP score ↑ |
|---|---|---|---|---|---|---|
| RFlow | 7 | 100.0% | 1.01 | 27.23 | 17.76 | 30.87 |
| RAS-Std | 7 | 25.0% | 1.45 | 31.99 | 21.7 | 30.64 |
| RAS-Norm | 7 | 25.0% | 1.45 | 31.65 | 21.24 | 30.59 |
| Random | 7 | 25.0% | 1.45 | 33.26 | 22.10 | 30.67 |{{< /table-caption >}}
> 🔼 표 5는 Lumina-Next-T2I 모델과 COCO Val2014 데이터셋(1024x1024 해상도)을 사용하여 RAS(Region-Adaptive Sampling) 기법과 Rectified Flow 기법의 성능을 비교 분석한 결과를 보여줍니다.  RAS의 다양한 설정(샘플링 단계 수, 샘플링 비율)과 Rectified Flow의 결과를 FID, sFID, CLIP Score 지표 및 처리 속도(Throughput)를 기준으로 비교하여, RAS의 효율성 및 성능을 종합적으로 평가합니다. 각 설정에 따른 FID, sFID, CLIP Score 값의 변화와 처리 속도 변화를 통해 RAS의 성능 최적화 가능성 및 한계를 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Full experiment results of RAS and rectified flow on Lumina-Next-T2I and COCO Val2014 1024×\times×1024.
> </details>

{{< table-caption >}}
| Method | Sample Steps | Sampling Ratio | Throughput (iter/s) ↑ | FID ↓ | sFID ↓ | CLIP score ↑ |
|---|---|---|---|---|---|---|
| RFlow | 30 | 100.0% | 0.11 | 22.46 | 16.59 | 30.47 |
| RAS | 30 | 75.0% | 0.14 | 23.31 | 17.73 | 30.49 |
| RFlow | 23 | 100.0% | 0.15 | 23.10 | 17.91 | 30.42 |
| RAS | 30 | 50.0% | 0.18 | 24.10 | 18.83 | 30.51 |
| RFlow | 15 | 100.0% | 0.23 | 24.88 | 21.02 | 30.25 |
| RAS | 30 | 25.0% | 0.26 | 27.44 | 20.95 | 30.45 |
| RAS | 15 | 75.0% | 0.27 | 26.82 | 23.33 | 30.26 |
| RAS | 30 | 12.5% | 0.31 | 33.64 | 23.44 | 30.36 |
| RAS | 15 | 50.0% | 0.33 | 28.48 | 25.17 | 30.29 |
| RFlow | 10 | 100.0% | 0.34 | 31.35 | 27.84 | 29.74 |
| RAS | 10 | 75.0% | 0.40 | 34.19 | 30.57 | 29.79 |
| RAS | 15 | 25.0% | 0.43 | 33.28 | 27.41 | 30.24 |
| RAS | 15 | 12.5% | 0.48 | 39.75 | 28.88 | 30.14 |
| RAS | 10 | 50.0% | 0.48 | 36.18 | 32.36 | 29.86 |
| RFlow | 7 | 100.0% | 0.49 | 48.19 | 38.60 | 28.65 |
| RAS | 7 | 75.0% | 0.54 | 50.45 | 40.19 | 28.78 |
| RAS | 10 | 25.0% | 0.59 | 42.96 | 33.51 | 29.91 |
| RAS | 7 | 50.0% | 0.61 | 51.78 | 40.51 | 28.82 |
| RAS | 6 | 75.0% | 0.62 | 66.12 | 46.58 | 27.80 |
| RAS | 10 | 12.5% | 0.65 | 47.34 | 32.70 | 29.75 |
| RAS | 6 | 50.0% | 0.67 | 66.54 | 46.71 | 27.83 |
| RAS | 7 | 25.0% | 0.70 | 53.93 | 39.80 | 28.85 |
| RAS | 7 | 12.5% | 0.74 | 54.62 | 40.23 | 28.83 |
| RAS | 6 | 25.0% | 0.74 | 67.16 | 46.46 | 27.85 |
| RAS | 5 | 75.0% | 0.75 | 99.01 | 56.26 | 26.02 |
| RAS | 6 | 12.5% | 0.78 | 67.88 | 45.89 | 27.83 |
| RFlow | 5 | 100.0% | 0.69 | 96.53 | 59.26 | 26.03 |
| RAS | 5 | 50.0% | 0.83 | 99.81 | 56.57 | 26.01 |
| RAS | 5 | 25.0% | 0.95 | 101.50 | 56.40 | 25.93 |
| RAS | 5 | 12.5% | 1.00 | 102.90 | 55.25 | 25.84 |
| RFlow | 3 | 100.0% | 1.15 | 256.90 | 94.80 | 19.67 |{{< /table-caption >}}
> 🔼 표 6은 Stable Diffusion 3 모델과 COCO Val2014 데이터셋(1024x1024 해상도)을 사용하여 RAS(Region-Adaptive Sampling)와 Rectified Flow 방법의 성능을 비교 분석한 결과를 보여줍니다.  다양한 샘플링 단계(Sample Steps)와 샘플링 비율(Sampling Ratio) 조합에 따른 처리량(Throughput), FID(Fréchet Inception Distance), sFID(Sliding FID), CLIP Score 등의 지표를 제시하여, RAS가 Rectified Flow에 비해 속도와 성능 측면에서 우수함을 보여줍니다. 특히, RAS는 다양한 매개변수 조합을 통해 처리량과 이미지 품질 간의 균형을 효과적으로 조절할 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Full experiment results of RAS and rectified flow on Stable Diffusion 3 and COCO Val2014 1024×\times×1024.
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