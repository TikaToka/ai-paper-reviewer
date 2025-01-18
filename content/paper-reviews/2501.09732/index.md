---
title: "Inference-Time Scaling for Diffusion Models beyond Scaling Denoising Steps"
summary: "확산 모델의 추론 시간 확장을 통해 고품질 이미지 생성을 달성하는 획기적인 방법 제시!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Generation", "🏢 NYU",]
showSummary: true
date: 2025-01-16
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.09732 {{< /keyword >}}
{{< keyword icon="writer" >}} Nanye Ma et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-17 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.09732" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.09732" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/inference-time-scaling-for-diffusion-models" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 확산 모델들은 학습 시간에 많은 계산 자원을 필요로 하며, 추론 시간에는 단순히 잡음 제거 단계만을 늘리는 방식으로 성능 향상을 시도해 왔습니다. 하지만 이러한 방식은 성능 향상에 한계가 있으며, 계산 효율성을 저해하는 문제점이 있었습니다. 본 연구는 이러한 문제를 해결하기 위해 **추론 시간 동안 추가적인 계산을 할당하여 더 나은 잡음을 찾는 방식**을 제안합니다.  이는 마치 최적의 경로를 찾는 문제와 유사하며,  잡음을 평가하는 검증자(verifier)와 더 나은 잡음 후보를 찾는 알고리즘(algorithm)이라는 두 가지 주요 요소를 고려합니다. 



연구진은 다양한 검증자와 알고리즘의 조합을 실험하여 이미지 생성의 품질을 향상시키는 데 성공했습니다. 특히, 이미지의 복잡성을 고려하여 프레임워크의 구성 요소들을 다양한 응용 시나리오에 맞게 조합할 수 있음을 보여주었습니다.  **실험 결과, 제안된 방법은 기존 방식보다 훨씬 우수한 성능을 보였으며,  다양한 모델 크기와 작업에서도 효과적**임을 확인했습니다.  본 연구는 **추론 시간 확장이라는 새로운 관점에서 생성 모델의 성능을 향상시키는 데 중요한 기여**를 할 것으로 기대됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 확산 모델의 추론 시간을 확장하여 이미지 생성 품질을 크게 향상시키는 새로운 프레임워크 제안 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 검증자(verifier)와 알고리즘(algorithm)의 두 축을 중심으로 설계 공간을 체계적으로 분석하고 과제별 최적 설정 도출 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 다양한 벤치마크 실험을 통해 제안된 프레임워크의 효과성과 일반화 성능 검증 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **추론 시간 확장을 통해 확산 모델의 성능을 향상시키는 새로운 프레임워크**를 제시하여,  **제한된 계산 자원 내에서도 고품질의 이미지 생성을 가능하게** 합니다.  이는 최근 급격히 발전하는 생성 모델 분야에서 **계산 효율성을 개선하고,  다양한 응용 분야에 적용 가능한 새로운 가능성을 제시**하는 중요한 연구입니다.  특히, **검증자와 알고리즘의 설계 공간을 체계적으로 분석**하여,  **과제별로 최적화된 설정을 찾는 방법**을 제안한 점이 주목할 만하며,  향후 생성 모델의 확장성과 효율성을 높이는 데 기여할 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.09732/x1.png)

> 🔼 그림 1은 확산 모델에서 추론 시간 확장에 대한 실험 결과를 보여줍니다. 기존의 방법은 denoising step의 수를 늘리는 것이었지만, 이 논문에서는 denoising step의 수를 늘리는 것 외에도, 더 나은 noise를 찾는 search 과정을 추가하여 성능 향상을 시도했습니다. 그림에서는 ImageNet과 DrawBench 데이터셋에서 FID(낮을수록 좋음), IS(높을수록 좋음), CLIPScore(높을수록 좋음), Aesthetic Score(높을수록 좋음) 지표를 사용하여 성능을 비교하고 있습니다. 실험 결과, 제안된 search framework가 denoising step만 증가시키는 것보다 모든 설정에서 상당한 성능 향상을 보였다는 것을 보여줍니다.  즉, 단순히 denoising step을 늘리는 것보다, 계산 비용을 search 과정에 투자하는 것이 더 효과적이라는 것을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Inference scaling beyond increasing denoising steps. We demonstrate the performance with respect to FID ↓bold-↓\boldsymbol{\downarrow}bold_↓, IS ↑bold-↑\boldsymbol{\uparrow}bold_↑ on ImageNet, and CLIPScore ↑bold-↑\boldsymbol{\uparrow}bold_↑, Aesthetic Score ↑bold-↑\boldsymbol{\uparrow}bold_↑ on DrawBench. Our search framework exhibits substantial improvements in all settings over purely scaling NFEs with increasing denoising steps.
> </details>





{{< table-caption >}}
| Verifier | Color | Shape | Texture | Spatial | Numeracy | Complex |
|---|---|---|---|---|---|---|
| - | 0.7692 | 0.5187 | 0.6287 | 0.2429 | 0.6167 | 0.3600 |
| Aesthetic | 0.7618 | 0.5119 | 0.5826 | 0.2593 | 0.6159 | 0.3472 |
| CLIP | 0.8009 | 0.5722 | 0.7005 | 0.2988 | 0.6457 | 0.3704 |
| ImageReward | **0.8303** | **0.6274** | **0.7364** | **0.3151** | **0.6789** | **0.3810** |
| Ensemble | 0.8204 | 0.5959 | 0.7197 | 0.3043 | 0.6623 | 0.3754 |{{< /table-caption >}}

> 🔼 표 1은 FLUX-1-dev 모델을 사용하여 T2I-CompBench 데이터셋에서 검색(search) 기법의 성능을 보여줍니다.  검색에는 검증기(verifier) 앙상블을 사용한 랜덤 검색이 사용되었습니다. 평가에는 T2I-CompBench에서 제공하는 파이프라인이 사용되었습니다. 첫 번째 행은 검색 없이 노이즈 제거(denoising) 단계에만 30 NFEs를 할당한 경우의 성능을 나타내고, 나머지 행은 검색에 1920 NFEs를 할당한 경우의 성능을 나타냅니다.  색상, 모양, 질감, 공간적 관계, 수적 개념 및 복잡도의 여섯 가지 측면에서 성능이 평가됩니다. 각 측면은 다양한 모델을 통해 평가되며 가중 평균을 통해 최종 점수를 산출합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Performance of search with FLUX.1-dev on T2I-CompBench. We use random search with Verifier Ensemble to obtain the samples; for evaluation, we use the pipeline provided in T2I-CompBench. The first row denotes the performance without search where we fix the denoising budget to be 30303030 NFEs, and for the rest, we fix the search budget to be 1920192019201920 NFEs.
> </details>





### In-depth insights


#### Inference Scaling Laws
추론 스케일링 법칙은 **모델 크기, 데이터 크기 및 계산 자원의 증가에 따라 성능이 향상되는 방식**을 설명합니다.  본 논문에서는 확산 모델에서 추론 스케일링 법칙에 대한 심층적인 탐구를 통해, 단순히 디노이징 단계를 늘리는 것만으로는 성능 향상에 한계가 있음을 보여줍니다. **추론 시간에 계산 비용을 추가적으로 할당하여 노이즈 검색을 수행함으로써 성능을 더욱 향상**시킬 수 있다는 것을 밝혀냈습니다.  이는 검증자(verifier)와 알고리즘(algorithm)이라는 두 축을 중심으로 설계 공간을 체계적으로 조직화하여 이루어졌습니다. **다양한 검증자-알고리즘 조합의 실험을 통해 특정 작업에 최적화된 구성이 존재하며, 이는 이미지의 복잡성과 밀접한 관련**이 있음을 발견했습니다.  **본 연구는 추론 시간의 계산 자원 배분 전략을 통해 확산 모델의 성능을 획기적으로 향상시킬 수 있음을 시사**하며,  향후 다양한 응용 분야에 적용될 수 있는 잠재력을 가지고 있습니다.

#### Search Space Design
본 논문에서 제안하는 **추론 시간 확장 프레임워크**는 확산 모델의 생성 성능을 향상시키기 위해 **탐색 알고리즘**을 사용합니다.  이를 위해 **검증자(verifier)**와 **알고리즘(algorithm)**이라는 두 가지 주요 설계 축을 중심으로 탐색 공간을 구성합니다. 검증자는 생성된 샘플의 우수성을 평가하는 역할을 하며, 알고리즘은 더 나은 노이즈 후보를 찾는 데 사용됩니다. **다양한 검증자와 알고리즘의 조합**을 통해 실험을 진행하여 어떤 조합이 특정 작업에 가장 적합한지 파악하고, **작업별로 최적의 탐색 설정**을 찾는 것이 중요함을 보여줍니다.  **복잡한 이미지 생성 작업**의 경우, 프레임워크의 구성 요소를 특정 응용 시나리오에 맞춰 선택할 수 있다는 점도 중요한 설계 고려 사항입니다.

#### Verifier-Task Alignment
본 논문에서 제시된 검색 프레임워크의 핵심 구성 요소인 검증자(Verifier)와 생성 작업(Task) 간의 정렬(Alignment)에 대한 심층적인 분석이 중요합니다. **다양한 검증자**는 이미지의 미적 품질, 텍스트와 이미지의 일치도, 일반적인 선호도 등을 평가하는 서로 다른 관점을 제공합니다. 따라서 특정 생성 작업에 가장 적합한 검증자를 선택하는 것이 중요합니다. **DrawBench와 같은 다양한 데이터셋**에서 다양한 검증자-알고리즘 조합의 성능을 비교 분석하여 어떤 검증자-알고리즘 조합이 특정 작업에 가장 효과적인지 밝히는 것은 실용적인 측면에서 매우 중요합니다. 이러한 분석을 통해 **특정 작업에 맞춤화된 검색 설정**을 선택할 수 있음을 보여주는 것은 **실제 응용 시나리오**에 대한 프레임워크의 적용 가능성을 높입니다.  결론적으로 검증자-작업 정렬 분석은 제안된 프레임워크의 실용성 및 일반화 가능성을 평가하는 데 필수적입니다.

#### Algorithmic Efficiency
본 논문에서는 알고리즘 효율성에 대한 심도있는 논의가 부족하지만, 추론 시간 확장을 위한 탐색 과정에서의 계산 비용 최소화 전략이 중요하게 다루어짐을 알 수 있습니다. **무작위 탐색 (Random Search)은 계산 비용 대비 성능 향상 측면에서 효율적**이며, **영(Zero)-차 탐색 (Zero-Order Search) 및 경로 탐색 (Search over Paths)은 반복적인 최적화를 통해 성능 개선을 보이지만 계산 비용 증가**를 고려해야 합니다. 따라서, **특정 작업에 맞는 알고리즘 선택이 효율성을 좌우**하며, **검증자 (Verifier)와 알고리즘의 조합에 따른 성능 차이**를 분석하여 최적의 효율성을 확보하는 것이 중요합니다.  **모델 크기 및 작업 특성에 따른 최적 알고리즘 및 검증자 조합이 다르게 나타나는 경향**은 효율적인 탐색 전략 수립에 중요한 시사점을 제공합니다.  **결론적으로, 단순히 계산량 증가보다는 적절한 알고리즘과 검증자 선택을 통한 전략적 계산 투자가 추론 시간 확장 및 성능 향상에 보다 효율적**임을 시사합니다.

#### Future Research
본 논문은 확산 모델의 추론 시간 확장에 대한 새로운 프레임워크를 제시하고, 다양한 실험 결과를 통해 **검증자(verifier)와 알고리즘(algorithm)의 조합이 성능에 미치는 영향**을 보여주었습니다.  **미래 연구는 다양한 검증자와 알고리즘을 결합하여 최적의 성능을 달성하는 방법**을 더욱 심도 있게 연구하는데 초점을 맞출 수 있습니다. 특히, **특정 작업에 맞춘 검증자 설계** 및 **고차원 알고리즘(high-order algorithms)** 개발을 통해 추론 시간 확장의 효율성을 극대화하는 연구가 필요합니다. 또한, **제한된 계산 자원 환경**에서의 효율적인 추론 시간 확장 기법 연구도 중요한 과제입니다.  **다양한 확산 모델과 다른 생성 모델**에 대한 적용 가능성을 검토하고, **실제 응용 분야**에 적용하여 그 효과를 검증하는 연구도 필요합니다.  **대규모 언어 모델(LLM)과의 연계**를 통해 더욱 정교하고 효율적인 생성 모델을 구축하는 방안도 고려해볼 수 있습니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.09732/x2.png)

> 🔼 그림 2는 제시된 논문에서 세 가지 검색 알고리즘(Random Search, Zero-Order Search, Search over Paths)을 설명하는 그림입니다. 왼쪽 그림은 Random Search로, 검증자의 점수에 따라 가장 좋은 샘플을 선택하고 나머지는 버리는 방식입니다. 가운데 그림은 Zero-Order Search로, 각 단계에서 기준 소음(pivot noise)의 이웃 영역에서 N개의 후보 소음을 샘플링하고, 검증자의 점수를 기준으로 가장 좋은 소음을 선택하여 검색을 계속 진행하는 방식입니다. 오른쪽 그림은 Search over Paths로, 중간 샘플링 단계에서 소음을 추가하여 샘플링 경로를 확장하고, 가장 좋은 소음을 선택하여 검색을 계속하는 방식입니다. 각 알고리즘의 특징을 시각적으로 보여주는 그림입니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Illustration of Search Algorithms. Left: Random Search selects the best sample according to the verifier score and rejects the rest. Center: Zero-Order Search samples N𝑁Nitalic_N candidates in the neighborhood of the pivot noise at each step, and selects the best one according to the verifier to continue the search from. Right: Search over Paths sample noises at intermediate sampling steps to add to current samples to expand the sampling trajectories, and select the best one to continue the search.
> </details>



![](https://arxiv.org/html/2501.09732/x5.png)

> 🔼 그림 3은 오라클 검증자(Oracle Verifier)의 성능을 보여줍니다. ImageNet 데이터셋에서 FID(Fréchet Inception Distance)와 IS(Inception Score) 지표를 사용하여 랜덤 검색(Random Search)을 수행한 결과입니다.  'Inference Compute'는 잡음 제거 단계(denoising steps)와 검색 과정에 사용된 총 함수 평가 횟수(NFE, number of function evaluations)를 나타냅니다. 각 곡선의 시작점은 잡음 제거 단계에만 NFE를 할당하고 검색에는 NFE를 할당하지 않은 경우를 의미합니다. 이 그림은 단순히 잡음 제거 단계의 수만 늘리는 것보다 검색 과정에 계산 비용을 투입함으로써 성능 향상을 얻을 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Performances of Oracle Verifiers. Random Search with FID and IS on ImageNet. Inference Compute is given by the total NFEs devoted to denoising steps and search; the starting points of all curves in each and the following figures denote only devoting NFEs to denoising steps and 0 NFEs in search.
> </details>



![](https://arxiv.org/html/2501.09732/x13.png)

> 🔼 이 그림은 ImageNet 데이터셋에서 CLIP과 DINO를 이용한 Random Search를 통해 얻은 결과를 보여줍니다.  여기서 CLIP-ZeroShot은 프롬프트 엔지니어링으로 생성된 CLIP 제로샷 분류기의 로짓을 사용한 것이고, DINO-LinearHead는 Oquab 등의 연구 [53]에서 제공된 사전 훈련된 선형 분류기를 사용한 것입니다. 그림은 다양한 Classifier-free guidance 가중치에 따른 성능을 보여주며, 추론 시간 계산량을 늘리는 것이 성능 향상에 어떻게 기여하는지를 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Performances of Supervised Verifiers. Random Search with CLIP and DINO on ImageNet across different classifier-free guidance weights. CLIP-ZeroShot refers to using the logits output by the CLIP zero-shot classifier formulated with Prompt Engineering, and DINO-LinearHead refers to using the pre-trained linear classifier provided by Oquab et al. [53].
> </details>



![](https://arxiv.org/html/2501.09732/x14.png)

> 🔼 이 그림은 자기 지도 방식의 검증기 성능을 보여줍니다. 왼쪽 그림은 CLIP과 DINO 특징 유사도 점수와 분류 로짓 간의 상관 관계를 보여주고, 오른쪽 그림은 분류기 없는 안내 가중치가 다른 여러 상황에서 CLIP과 DINO 특징 유사도 점수를 검증기로 사용하는 랜덤 검색의 성능을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Performances of Self-Supervised Verifiers. Left: correlation between CLIP and DINO feature similarity score and their classification logits; Right: Random Search with CLIP and DINO feature similarity score as verifiers across different classifier-free guidance weight.
> </details>



![](https://arxiv.org/html/2501.09732/x15.png)

> 🔼 이 그림은 ImageNet 데이터셋에서 Zero-Order Search와 Search over Paths 알고리즘의 성능을 보여줍니다. 검증기는 DINO-LinearHead로 고정하고, FID와 IS 지표를 사용하여 성능을 평가합니다. 각 알고리즘에 대해 N(후보 노이즈 개수)과 성능 간의 관계를 추가적으로 보여줍니다. Zero-Order Search는 기존 노이즈 주변에서 새로운 노이즈를 탐색하고, Search over Paths는 확산 과정의 중간 단계에서 노이즈를 탐색하는 방식입니다. 그림을 통해 두 알고리즘의 성능 차이와 N값에 따른 성능 변화를 비교 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Performances of Search Algorithms. We fix the verifier to be DINO-LinearHead and investigate the FID and IS of Zero-Order Search and Search over Paths on ImageNet. For each algorithm, we further demonstrate the relationship between N𝑁Nitalic_N and their performances.
> </details>



![](https://arxiv.org/html/2501.09732/extracted/6136690/figures/sit_visuals/33_grid.png)

> 🔼 그림 7은 추론 시간 확장의 시각적 결과를 보여줍니다. 각 행은 다음과 같이 구성됩니다. 왼쪽 세 개의 이미지는 디노이징 단계에서 NFEs(함수 평가 횟수)를 증가시켜 생성한 이미지이고, 오른쪽 네 개의 이미지는 검색 과정에서 NFEs를 증가시켜 생성한 이미지입니다. 처음 두 행은 DINO-LinearHead를 사용하여 SiT-XL [50] 모델에서 샘플링한 이미지이고, 세 번째 행은 검증자 앙상블을 사용하여 PixArt-Σ [8] 모델에서 샘플링한 이미지이며, 마지막 두 행은 검증자 앙상블을 사용하여 FLUX-1.dev [41] 모델에서 샘플링한 이미지입니다. 이 그림은 디퓨전 모델의 추론 시간 확장을 통해 이미지 생성 품질을 개선할 수 있음을 시각적으로 보여줍니다. 특히, 단순히 디노이징 단계만 늘리는 것보다 검색 과정에서 계산량을 늘리는 것이 더 효과적임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Visualizations of Scaling Behaviors. Each row is constructed as follows: left three: sampled with increasing NFEs in denoising steps; right four: sampled with increasing NFEs in search. First two rows are sampled from SiT-XL [50] with DINO-LinearHead, third row is sampled from PixArt-ΣΣ\Sigmaroman_Σ [8] with Verifier Ensemble, and last two rows are sampled from FLUX-1.dev [41] with Verifier Ensemble.
> </details>



![](https://arxiv.org/html/2501.09732/extracted/6136690/figures/sit_visuals/89_grid.png)

> 🔼 그림 8은 FLUX.1-dev 모델을 사용하여 추론 시간을 확장하는 검색 방법의 성능을 보여줍니다. 랜덤 검색을 사용하여 검색 예산을 3840 NFEs로 고정하고, 검색 예산 없이 생성된 결과와 비교하여 상대적 성능 향상률(%)을 보여줍니다. 이 그림은 다양한 평가 지표(미적 평가자, CLIPScore, ImageReward, Verifier Ensemble)에 따른 검색 방법의 효과를 보여주는 여러 개의 막대 그래프를 포함합니다. 각 막대 그래프는 특정 평가 지표에 대한 상대적 성능 향상을 나타내며, 검색 방법이 모든 평가 지표에서 상당한 성능 향상을 가져왔음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Performances of Search with FLUX.1-dev at inference-time. We fix the search budget to be 3840384038403840 NFEs with random search, and demonstrate the relative performance gain (%) with generation without any search budget.
> </details>



![](https://arxiv.org/html/2501.09732/extracted/6136690/figures/sit_visuals/250_grid.png)

> 🔼 그림 9는 DrawBench 데이터셋에서 FLUX-1-dev 모델을 사용하여 inference-time scaling에 대한 실험 결과를 보여줍니다.  Verifier Ensemble을 사용한 랜덤 검색 기법을 통해 생성된 이미지의 품질 향상을 보여주는 그래프입니다.  검색을 사용하지 않은 경우(검색 비용 0) 대비 상대적 성능 향상률(%)을 보여주며, ImageNet 데이터셋에서 관찰된 것과 유사한 경향을 여러 평가 지표에서 확인할 수 있습니다.  즉, inference 시간에 계산량을 늘림으로써 성능이 향상되는 것을 보여주는 그래프이며,  이러한 경향이 다양한 평가 지표에 걸쳐 일관되게 나타난다는 것을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Scalability of search with FLUX.1-dev on DrawBench. We use random search with Verifier Ensemble to obtain the results, and demonstrate the relative performance gain (%) with generation without any search budget. Similar scaling behavior to ImageNet setting is observed across different metrics.
> </details>



![](https://arxiv.org/html/2501.09732/extracted/6136690/figures/sit_visuals/270_grid.png)

> 🔼 그림 10은 단일 검색 반복에 대한 계산량 조정의 성능을 보여줍니다.  SiT-XL 모델을 사용하고, 디노이징 예산을 250 NFE로 고정하여 단일 검색 반복에 할당된 NFE에 따른 성능 차이를 보여줍니다.  즉,  이 그림은 검색 과정에서 사용되는 계산량을 변화시켰을 때, 이미지 생성 성능이 어떻게 달라지는지 보여주는 실험 결과를 나타냅니다.  다양한 NFEs/iter(검색 반복 당 NFE 수) 값을 사용하여 실험을 진행했으며,  NFEs/iter 값이 증가함에 따라 성능이 향상되지만, 특정 지점을 넘어서면 추가적인 성능 향상은 미미함을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Performance of scaling compute for single search iteration. We use the SiT-XL model, fix the denoising budget to 250250250250 NFE, and demonstrate the performance differences with respect to the NFEs devoted to a single search iteration.
> </details>



![](https://arxiv.org/html/2501.09732/extracted/6136690/figures/sit_visuals/429_grid.png)

> 🔼 본 그림은 ImageNet 데이터셋에서 서로 다른 크기의 SiT 모델(SiT-B, SiT-L, SiT-XL)에 대해 제안된 두 가지 검색 방법(Zero-Order Search와 Random Search)의 성능을 보여줍니다.  각 모델에 대해 FID(Fréchet Inception Distance)와 IS(Inception Score) 지표를 사용하여 성능을 측정했습니다. 그림의 왼쪽은 Zero-Order Search (ZO-4) 알고리즘을 DINO-LinearHead 검증자와 함께 사용한 결과를, 오른쪽은 Random Search 알고리즘을 DINO-LinearHead 검증자와 함께 사용한 결과를 보여줍니다.  x축은 추론 연산량(GFLOPs)을 나타내고, y축은 FID와 IS 점수를 나타냅니다.  이를 통해 모델 크기와 검색 방법에 따른 성능 변화를 비교 분석하여 효율적인 추론 연산량 배분 전략을 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Performance of our search methods across different model sizes (SiT-{B,L,XL}) on ImageNet. We use the best set up for FID and IS separately. Left: ZO-4 with DINO-LinearHead.; Right: Random Search with DINO-LinearHead.
> </details>



![](https://arxiv.org/html/2501.09732/extracted/6136690/figures/sit_visuals/587_grid.png)

> 🔼 그림 12는 제로-오더 탐색 알고리즘의 단계 크기 λ와 경로 탐색 알고리즘의 길이 L을 조정했을 때의 성능을 보여줍니다. 왼쪽 그래프는 λ를 변화시키면서 제로-오더 탐색의 성능을, 오른쪽 그래프는 L을 변화시키면서 경로 탐색의 성능을 각각 나타냅니다. 두 경우 모두 SiT-XL 모델을 사용했고, 검증자는 DINO의 분류 로짓으로 고정했습니다.  이 그래프들을 통해 하이퍼파라미터의 미세 조정이 모델 성능에 미치는 영향을 분석하고, 최적의 하이퍼파라미터 설정을 찾는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Performance of tuning additional parameters for algorithms.  Left: Zero-Order Search with step sizes λ𝜆\lambdaitalic_λ; Right: Search Over Paths with lengths L𝐿Litalic_L. We use SiT-XL and fix the verifier to be the classification logits from DINO.
> </details>



![](https://arxiv.org/html/2501.09732/extracted/6136690/figures/sit_visuals/980_grid.png)

> 🔼 그림 13은 ImageNet 데이터셋에서 DINO와 CLIP 분류 로짓을 사용하여 랜덤 검색의 성능을 보여줍니다. SiT-XL 모델에 랜덤 검색을 적용하고 FID, IS, 정밀도 및 재현율을 보고합니다. 이 그래프는 랜덤 검색을 통해 생성된 이미지의 품질(FID 및 IS로 측정)과 다양성(정밀도와 재현율로 측정)이 검색 반복 횟수에 따라 어떻게 변화하는지를 보여줍니다. 특히, 검색 반복 횟수가 증가함에 따라 정밀도는 증가하지만 재현율은 감소하는 것을 보여주는 데 중점을 둡니다. 이는 검색 알고리즘이 특정 분류기에 과도하게 적합되어 다양성이 희생될 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: Performance of Random Search on ImageNet against DINO and CLIP classification logits. We use random search on the SiT-XL model and report FID, IS, Precision, and Recall.
> </details>



![](https://arxiv.org/html/2501.09732/extracted/6136690/figures/flux_visuals/194_grid.jpg)

> 🔼 그림 14는 영(Zero-Order) 및 1차(First-Order) 탐색 방법의 성능 비교를 보여줍니다. SiT-XL 모델을 사용하고 검증자(verifier)는 DINO-LinearHead로 고정했습니다. 역전파(backward) 계산 비용이 순전파(forward) 계산 비용의 약 3배라고 가정하여 추정된 역전파 비용을 사용하여 추론 계산 비용을 일치시켰습니다. 즉, 1차 탐색의 경우 역전파 연산을 포함하기 때문에 계산 비용이 더 높게 나타납니다. 이 그림은 각 탐색 방법이 추론 계산량에 따라 FID와 IS 지표에 미치는 영향을 비교 분석합니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: Comparison between Zero-Order and First-Order Search. We use the SiT-XL model and fix the verifier to be the DINO-LinearHead. The Inference Compute is aligned via the rough estimation of cost(backward) ∼similar-to\sim∼ 3×\times×cost(forward).
> </details>



![](https://arxiv.org/html/2501.09732/extracted/6136690/figures/flux_visuals/123_grid.jpg)

> 🔼 그림 15는 CLIP, DINO 및 SigLIP 특징 유사도 점수와 CLIPScore 간의 상관관계를 보여줍니다.  왼쪽부터 CLIP, DINO, SigLIP 특징 유사도 점수와 CLIPScore 간의 상관관계를 각각 보여주는 세 개의 산점도가 나와 있습니다. 모든 점들은 FLUX-1.dev 모델로 생성된 것입니다. 이 그림은 특징 유사도 점수와 CLIPScore 간의 상관관계를 시각적으로 보여주어, 각 모델이 이미지 생성 품질을 평가하는 데 어떻게 다른 지표를 사용하는지를 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 15: From Left to Right: Correlation of CLIP, DINO, and SigLIP feature similarity score with CLIPScore. All points are generated from FLUX.1-dev.
> </details>



![](https://arxiv.org/html/2501.09732/extracted/6136690/figures/flux_visuals/126_grid.jpg)

> 🔼 그림 16은 LLM 평가자를 사용한 평가에 대한 자세한 프롬프트를 보여줍니다. 이 프롬프트는 LLM 평가자가 생성된 이미지의 다양한 측면(정확성, 독창성, 시각적 품질, 일관성 및 감정적 공명)을 평가하고 각 측면에 대한 점수를 매기도록 안내합니다. 각 점수에는 해당 점수가 주어진 이유를 설명하는 간략한 설명이 포함됩니다. 또한 프롬프트는 각 측면에 대한 점수의 가중 평균 또는 모든 측면의 평균을 사용하여 모델의 전반적인 성능에 대한 종합적인 점수를 제공하도록 지시합니다. 이 프롬프트는 LLM 평가자가 생성된 이미지의 품질과 관련성을 정확하게 평가하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 16: The detailed prompt for evaluation with the LLM Grader.
> </details>



![](https://arxiv.org/html/2501.09732/extracted/6136690/figures/flux_visuals/149_grid.jpg)

> 🔼 그림 17은 'loggerhead turtle' 이라는 텍스트 프롬프트를 사용하여 생성된 이미지들을 보여줍니다. 왼쪽 세 개의 이미지는 각각 10, 20, 250개의 디노이징 스텝을 사용하여 생성되었고, 오른쪽 세 개의 이미지는 제로-오더 검색 알고리즘을 사용하여 생성되었습니다. 제로-오더 검색은 DINO 분류기를 검증자로 사용하며, 이는 이미지 품질을 평가하는 데 사용되는 사전 훈련된 모델입니다. 제로-오더 검색을 통해 생성된 이미지들은 추가적인 계산 비용을 투자하여 이미지의 질을 높일 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 17: “loggerhead turtle” (33)
> </details>



![](https://arxiv.org/html/2501.09732/extracted/6136690/figures/flux_visuals/145_grid.jpg)

> 🔼 그림 18은 '황색관자고깔앵무'(89)라는 제목의 이미지를 보여줍니다. 이 그림은 논문의 추론 시간 확장에 대한 실험 결과를 보여주는 일련의 이미지 중 하나입니다. 왼쪽 세 개의 이미지는 각각 10, 20, 250번의 디노이징 단계를 거쳐 생성된 이미지이고, 오른쪽 세 개의 이미지는 제로-오더 검색 알고리즘을 사용하여 생성된 이미지입니다. 제로-오더 검색은 더 나은 노이즈 후보를 찾기 위한 알고리즘으로, 각 이미지는 다른 노이즈 조건을 사용하여 생성되었습니다. 이미지의 품질은 디노이징 단계의 수와 검색 알고리즘의 사용 여부에 따라 달라질 수 있습니다. 이 그림은 확장된 추론 시간 계산이 확산 모델의 성능 향상에 기여할 수 있음을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 18: “Sulphur-crested cockatoo” (89)
> </details>



![](https://arxiv.org/html/2501.09732/extracted/6136690/figures/flux_visuals/183_grid.jpg)

> 🔼 그림 19는 '시베리안 허스키'라는 텍스트 프롬프트를 사용하여 생성된 이미지들을 보여줍니다. 왼쪽 세 개의 이미지는 각각 10, 20, 250개의 디노이징 단계를 사용하여 생성되었고, 오른쪽 세 개의 이미지는 제로-오더 탐색 알고리즘을 사용하여 생성되었습니다. 제로-오더 탐색에서는 이웃의 수 N을 2로, 단계 크기 λ를 0.95로 설정하였으며, 이에 상응하는 NFE(함수 평가 횟수)는 각각 450, 1850, 6650입니다. 이 그림은 다른 디노이징 단계 수와 제로-오더 탐색 알고리즘을 통해 생성된 이미지 간의 비교를 보여줌으로써, 제안된 방법이 추론 시간 연산을 확장하여 확산 모델의 성능을 향상시킬 수 있음을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 19: “Siberian husky” (250)
> </details>



![](https://arxiv.org/html/2501.09732/extracted/6136690/figures/flux_visuals/152_grid.jpg)

> 🔼 그림 20은 '북극늑대' 라는 텍스트 프롬프트를 사용하여 생성된 이미지들을 보여줍니다. 이미지들은 노이즈 제거 단계의 수를 증가시켜 생성된 이미지들(왼쪽 세 개)과, 제안된 검색 프레임워크를 이용하여 더 나은 노이즈를 찾아 생성된 이미지들(오른쪽 네 개)을 보여줍니다. 이를 통해 추론 시간 연산량을 늘리는 것이 확산 모델의 성능 향상에 어떻게 기여하는지 시각적으로 보여줍니다. 왼쪽 이미지들은 기본적인 확산 모델의 노이즈 제거 과정을 거친 결과이며, 오른쪽 이미지들은 제안된 검색 알고리즘을 통해 더욱 개선된 결과물입니다. 각 이미지의 품질 차이를 통해 제안된 방법의 효과를 짐작할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 20: “Arctic wolf” (270)
> </details>



![](https://arxiv.org/html/2501.09732/extracted/6136690/figures/pixart_visuals/1_grid.jpg)

> 🔼 이 그림은 야구공을 다양한 각도와 조명으로 묘사한 여러 이미지들을 보여줍니다.  각 이미지는 약간씩 다른 각도나 조명을 사용하여 야구공의 질감, 재질, 그리고 형태를 다양하게 표현하고 있습니다. 이는 인공지능 모델이 제시된 텍스트 프롬프트(“야구공”)를 해석하고 다양한 시각적 표현을 생성할 수 있음을 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 21: “baseball” (429)
> </details>



![](https://arxiv.org/html/2501.09732/extracted/6136690/figures/pixart_visuals/3_grid.jpg)

> 🔼 그림 22는 'hammer'(망치)라는 텍스트 프롬프트를 사용하여 생성된 이미지들을 보여줍니다.  이미지는 FLUX-1.dev 모델을 사용하여 생성되었으며, 이미지의 다양성과 품질을 보여주는 다양한 시각적 표현들을 확인할 수 있습니다.  왼쪽 세 이미지는 기본적인 샘플링 과정을 거쳐 생성된 것이고, 오른쪽 세 이미지는 제안된 방법(Zero-Order Search)을 사용하여 생성된 것입니다.  Zero-Order Search는 추론 시간을 확장하여 이미지 품질을 높이는 기법으로, 이 그림에서는 이 방법을 통해 생성된 이미지들이 더욱 사실적이고 다양한 디테일을 보여주는 것을 확인할 수 있습니다. 각 이미지는 망치의 형태, 재질, 배경 등이 서로 다르게 표현되어 있습니다. 이는 제안된 방법이 다양한 종류의 망치 이미지를 생성하는 데 효과적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 22: “hammer” (587)
> </details>



![](https://arxiv.org/html/2501.09732/extracted/6136690/figures/pixart_visuals/4_grid.jpg)

> 🔼 그림 23은 '화산'이라는 텍스트 프롬프트를 사용하여 생성된 이미지들을 보여줍니다. 총 여섯 개의 이미지가 있으며, 각 이미지는 훈련된 확산 모델이 텍스트 프롬프트를 기반으로 생성한 화산의 다양한 시각적 표현을 보여줍니다. 이미지들은 화산의 크기, 형태, 주변 환경 등에서 차이를 보이며, 화산 폭발 장면이나 화산의 평화로운 모습 등 다채로운 모습을 담고 있습니다. 이 그림은 논문의 추론 시간 확장에 대한 실험 결과를 보여주는 여러 이미지 중 하나이며, 추가적인 계산을 통해 확산 모델의 추론 성능을 향상시킬 수 있음을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 23: “volcano” (980)
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Verifier | Aesthetic | CLIPScore | ImageReward | LLM Grader |
|---|---|---|---|---|
| - | 5.79 | 0.71 | 0.97 | 84.29 |
| Aesthetic + Random | **6.38** | 0.69 | 0.99 | 86.04 |
| + ZO-2 | 6.33 | 0.69 | 0.96 | 85.90 |
| + Paths-2 | 6.31 | 0.70 | 0.95 | 85.86 |
| CLIPScore + Random | 5.68 | **0.82** | 1.22 | 86.15 |
| + ZO-2 | 5.72 | 0.81 | 1.16 | 85.48 |
| + Paths-2 | 5.71 | 0.81 | 1.14 | 85.45 |
| ImageReward + Random | 5.81 | 0.74 | **1.58** | 87.09 |
| + ZO-2 | 5.79 | 0.73 | 1.50 | 86.22 |
| + Paths-2 | 5.76 | 0.74 | 1.49 | 86.33 |
| Ensemble + Random | 6.06 | 0.77 | 1.41 | **88.18** |
| + ZO-2 | 5.99 | 0.77 | 1.38 | 87.25 |
| + Paths-2 | 6.02 | 0.76 | 1.34 | 86.84 |{{< /table-caption >}}
> 🔼 표 2는 DrawBench 데이터셋에서 다양한 검증자를 사용한 검색 알고리즘의 성능을 보여줍니다. 결과는 FLUX-1.dev 모델을 DrawBench에서 평가하여 얻었습니다. 첫 번째 행은 검색 없이 노이즈 제거 비용을 30 NFEs로 고정했을 때의 성능을 나타내고, 나머지 행은 검색 비용을 2880 NFEs로 고정했을 때의 성능을 나타냅니다.  다양한 검증자(미적 검증자, CLIPScore, ImageReward, LLM Grader)와 검색 알고리즘(Random Search, Zero-Order Search, Search over Paths) 조합에 따른 성능 변화를 비교 분석하여 각 조합의 효과 및 한계를 파악할 수 있습니다.  특히, 검색 비용을 추가했을 때 각 검증자와 알고리즘의 조합에 따른 성능 향상 또는 저하를 정량적으로 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Performance of search algorithms with different verifiers on DrawBench. The results are obtained from FLUX.1-dev evaluated on DrawBench. The first row denotes the performance without search where we fix denoising budget to be 30303030 NFEs, and for the rest we fix search budget to be 2880288028802880 NFEs.
> </details>

{{< table-caption >}}
| Model | Aesthetic | CLIP | PickScore |
|---|---|---|---|
| SDXL | 5.56 | 0.73 | 22.39 |
| + DPO | 5.59 | 0.74 | 22.54 |
| + DPO & Search | **5.66** | **0.76** | **23.54** |{{< /table-caption >}}
> 🔼 표 3은 DPO(Diffusion Probabilistic Optimization) 방식으로 미세 조정된 SDXL(Stable Diffusion XL) 모델에 대한 탐색(search) 기법의 성능을 보여줍니다.  DrawBench 데이터셋을 사용하여 검증기(verifier) 앙상블과 무작위 탐색(random search)을 통해 결과를 얻었습니다.  denoising 단계에는 40 NFEs(Number of Function Evaluations), 탐색 단계에는 1280 NFEs를 할당했습니다.  표에는  미세 조정된 모델의 기본 성능과 탐색을 적용했을 때의 성능 향상 정도(Aesthetic, CLIPScore, ImageReward 지표 기준)가 제시되어 있습니다.  즉,  추가적인 계산 비용을 투입하여 샘플 품질을 향상시키는 탐색 기법의 효과를 정량적으로 보여주는 표입니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Performance of Search with DPO-finetuned SDXL. We use random search with Verifier Ensemble on DrawBench to obtain the result. We set the denoising budget to 40404040 NFEs, and search budget to 1280128012801280 NFEs.
> </details>

{{< table-caption >}}
| Model | Compute Ratio | Aesthetic | CLIP | ImageReward | LLM Grader |
|---|---|---|---|---|---| 
| FLUX | 1 | 5.79 | 0.71 | 0.97 | 84.29 |
| PixArt-Σ | ~0.06 | 5.94 | 0.68 | 0.70 | 84.67 |
|  | ~0.09 | 6.03 | 0.71 | 0.97 | 85.62 |
|  | ~2.59 | 6.20 | 0.73 | 1.15 | 86.95 |{{< /table-caption >}}
> 🔼 표 4는 검색 시 검증자 앙상블을 사용한 PixArt-Σ와 검색 없이 FLUX를 사용한 경우의 성능을 비교한 것입니다. 하나의 샘플을 생성하는 데 FLUX에서 사용된 총 연산량을 표준 단위로 사용하여 PixArt-Σ의 사용 연산량을 조정했습니다. 총 연산량 추정치는 최상의 근사치를 기반으로 하며 완전히 정확하지 않을 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Comparison between PixArt-ΣΣ\Sigmaroman_Σ when search with Verifier Ensemble and FLUX without search. We use the total compute consumed by FLUX to generate one sample as the standard unit and scale the compute used by PixArt-ΣΣ\Sigmaroman_Σ accordingly. These total compute estimates are based on our best approximation and may not be entirely precise.
> </details>

{{< table-caption >}}
| Configs | Class-conditioned | Text-conditioned | Text-conditioned |
|---|---|---|---|
|  | SiT-XL | FLUX.1-dev | PixArt-Σ |
| ODE solver | 2<sup>nd</sup> order Heun | Euler | DDIM |
| NFEs/iter | 50<sup>†</sup> | 30 | 30 |
| final denoising steps | 250 | 30 | 30 |
| guidance scale | 1.0<sup>‡</sup> | 3.5 | 4.5 |
| resolution | 256 | 1024 | 1024 |{{< /table-caption >}}
> 🔼 표 5는 이미지 생성에 사용된 기본 샘플링 설정을 보여줍니다. 클래스 조건부 및 텍스트 조건부 이미지 생성 모두에 대한 설정이 포함되어 있습니다.  특히, 그림 10에서는 NFEs/iter(iteration당 기능 평가 횟수)가 다른 경우의 수치를, 그림 4에서는 안내 배율(guidance scale)이 다른 경우의 결과를 보여줍니다. 표에는 ODE 솔버(적분기), NFEs/iter, 최종 디노이징 단계 수, 안내 배율, 그리고 해상도 등의 정보가 포함되어 있습니다. 이 표는 본 논문의 실험 환경을 이해하는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Default sampling settings for Class-conditioned and Text-conditioned generation. ††\dagger† In Figure 10 we report numbers with different NFEs/iter; ‡‡\ddagger‡ In Figure 4 we report results with different guidance scales.
> </details>

{{< table-caption >}}
| Hyperparameter | Description |
|---|---| 
| initial paths  (<math>N</math>) | The number of paths to start the search with. |
| paths width  (<math>M</math>) | The number of noises to sample within each path. |
| search start (<math>σ</math>) | The time to start search. |
| backward stepsize (<math>Δb</math>) | The length of time interval to run ODE solver. |
| forward stepsize (<math>Δf</math>) | The length of time interval to run noising process. |
| paths length (<math>L</math>) | The NFEs devoted in each backward step. |{{< /table-caption >}}
> 🔼 표 6은 Search Over Paths 알고리즘에 사용된 하이퍼파라미터들을 설명합니다.  각 하이퍼파라미터는 Search Over Paths 알고리즘의 동작에 영향을 미치는 설정값들을 나타냅니다.  `initial paths (N)`는 검색을 시작하기 위한 초기 경로의 수를 의미하고, `paths width (M)`는 각 경로 내에서 샘플링할 노이즈의 수를 나타냅니다. `search start (σ)`는 검색을 시작할 노이즈 레벨을 나타내고, `backward stepsize (Δb)`와 `forward stepsize (Δf)`는 각각 역방향 및 순방향 노이징 프로세스의 단계 크기를 나타냅니다. 마지막으로 `paths length (L)`는 ODE 솔버를 실행할 시간 간격의 길이를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Hyperparameters for Search Over Paths.
> </details>

{{< table-caption >}}
| Model |  | Accuracy↑ | Originality↑ | Visual↑ | Consistency↑ | Emotional↑ | Overall↑ |
|---|---|---|---|---|---|---|---| 
| **FLUX.1-dev** |  | 89.35 | 67.58 | 93.00 | 97.04 | 73.99 | 84.29 |
|  | + 4 search iters | 91.33 | 68.49 | 93.42 | 96.99 | 75.31 | 85.17 |
|  | + 16 search iters | 91.95 | 71.52 | **93.76** | **97.24** | 76.30 | 86.42 |
|  | + 64 search iters | **93.83** | **75.38** | 93.57 | 97.04 | **79.34** | **88.08** |
| **PixArt-Σ** |  | 84.60 | 73.29 | 91.91 | 95.80 | 76.34 | 84.67 |
|  | + 4 search iters | 87.88 | 74.03 | 91.92 | 96.29 | 77.32 | 85.62 |
|  | + 16 search iters | 88.15 | 75.39 | 91.72 | 96.04 | 79.17 | 86.27 |
|  | + 64 search iters | **89.30** | **77.79** | **92.46** | **96.68** | **80.43** | **87.55** |{{< /table-caption >}}
> 🔼 표 7은 DrawBench 데이터셋에서 랜덤 검색 및 검증기 앙상블을 사용하여 FLUX-1.dev 및 PixArt-Σ 모델에 대한 LLM 평가자의 세부 점수를 보여줍니다. 각 이미지에 대해 LLM 평가자는 정확성, 독창성, 시각적 품질, 일관성, 감정적 공명 등 다섯 가지 측면을 평가하고 각 측면에 대한 점수(0~10)를 제공합니다.  이러한 점수는 각 이미지의 전반적인 품질을 평가하는 데 사용됩니다.  표에는 각 모델에 대한 점수와 검색 반복 횟수를 다르게 했을 때의 점수 변화를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Break-down scores of LLM Grader for FLUX.1-dev and PixArt-ΣΣ\Sigmaroman_Σ. The evaluation is done on DrawBench with random search and verifier ensemble.
> </details>

{{< table-caption >}}
| Verifiers | Aesthetic | CLIPScore | ImageReward |
|---|---|---|---|
| - | 5.79 | 0.71 | 0.97 |
| CLIP-SSL + 4 search iters | 5.76 | 0.71 | 0.99 |
| + 16 search iters | 5.72 | 0.71 | 1.04 |
| DINO-SSL + 4 search iters | 5.79 | 0.71 | 0.99 |
| + 16 search iters | 5.78 | 0.70 | 1.03 |
| SigLIP-SSL + 4 search iters | 5.79 | 0.70 | 1.02 |
| + 16 search iters | 5.75 | 0.70 | 1.02 |{{< /table-caption >}}
> 🔼 이 표는 DrawBench 데이터셋에서 FLUX.1-dev 모델을 사용하여 무지도 학습 방식으로 훈련된 검증자(Verifier)들의 성능을 보여줍니다. 랜덤 검색(random search) 기법을 사용했으며, 첫 번째 행은 검색 없이 기본 모델 성능을 나타냅니다.  각 검증자(Aesthetic, CLIPScore, ImageReward)에 대해 랜덤 검색을 4번과 16번 반복했을 때의 성능 향상을 보여줍니다. 이를 통해, 자가 지도 학습 방식 검증자들이 DrawBench와 같은 복잡한 이미지 생성 작업에서 얼마나 효과적인지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Performance of self-supervised verifiers on DrawBench. All numbers are from FLUX.1-dev with random search. The first row is the reference performance without search.
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