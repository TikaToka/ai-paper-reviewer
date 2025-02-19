---
title: "Better Embeddings with Coupled Adam"
summary: "Coupled Adam으로 LLM 임베딩의 비등방성 문제 해결!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 AI Sweden",]
showSummary: true
date: 2025-02-12
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.08441 {{< /keyword >}}
{{< keyword icon="writer" >}} Felix Stollenwerk et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-18 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.08441" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.08441" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/better-embeddings-with-coupled-adam" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)은 텍스트를 이해하고 생성하는 데 뛰어난 성능을 보이지만, **단어 표현(임베딩)**이 **비등방성**을 띠는 문제점을 가지고 있습니다. 이는 **희귀 단어**의 표현이 제대로 학습되지 않아 모델의 성능과 일반화 능력을 저해하는 원인이 됩니다.  기존 연구에서는 이 문제를 해결하기 위해 다양한 방법을 제시했지만, **최적화 알고리즘의 역할**에 대한 연구는 부족했습니다.

본 논문에서는 Adam이라는 널리 사용되는 최적화 알고리즘이 LLM의 비등방성 문제를 야기하는 주요 원인임을 밝히고, 이를 해결하기 위한 새로운 최적화 알고리즘인 **Coupled Adam**을 제시합니다.  Coupled Adam은 Adam 알고리즘의 **두 번째 모멘텀(second moment)**을 수정하여 단어 임베딩의 비등방성을 완화하고, **희귀 단어**에 대한 표현 학습을 개선합니다. 실험 결과, Coupled Adam은 단어 임베딩의 질을 향상시키고, 여러 가지 언어 모델 평가 작업에서 성능 향상을 보였습니다. 

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} Coupled Adam이라는 새로운 최적화 알고리즘을 통해 LLM의 단어 임베딩 비등방성 문제를 효과적으로 해결 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} Coupled Adam은 단어 임베딩의 질을 향상시키고, 상위 및 하위 작업 성능을 개선 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 희귀 단어의 임베딩 개선을 통해 LLM의 일반화 성능 향상 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대규모 언어 모델(LLM)**의 핵심 구성 요소인 **단어 임베딩의 질을 향상**시키는 새로운 방법을 제시하여, LLM 연구에 중요한 영향을 미칠 수 있습니다. **Coupled Adam이라는 새로운 최적화 알고리즘**을 통해 단어 임베딩의 **비등방성 문제를 해결**하고, 상위 및 하위 작업 성능을 개선하는 실험 결과는 LLM 연구자들에게 귀중한 통찰력을 제공합니다. 특히 **희귀 단어에 대한 임베딩 개선**은 LLM의 일반화 성능 향상에 큰 기여를 할 것으로 예상됩니다. 또한 이 연구는 최적화 알고리즘과 단어 임베딩의 관계를 깊이 있게 분석하여, **향후 연구 방향**을 제시하는 데에도 중요한 역할을 합니다. 

------
#### Visual Insights



![](https://arxiv.org/html/2502.08441/extracted/6201951/figs/toy_example.png)

> 🔼 그림 1은 2차원 잠재 공간에서 숨겨진 상태 벡터 h와 세 개의 임베딩 벡터 eᵢ를 보여줍니다.  파란색 벡터는 숨겨진 상태 벡터 h이고, 빨간색 벡터는 임베딩 벡터 eᵢ입니다. 회색 벡터는 SGD와 Adam 최적화 알고리즘을 사용했을 때의 임베딩 업데이트 벡터를 나타냅니다.  진짜 토큰(정답 토큰)의 업데이트 벡터는 h와 같은 방향을 가리키지만, 다른 토큰의 업데이트 벡터는 h와 반대 방향을 가리킵니다(식 5 참조). SGD의 경우 임베딩 업데이트 벡터의 합은 0이 되지만, Adam의 경우에는 항상 그렇지 않다는 점에 유의해야 합니다(식 11과 16 참조).  이 그림은 Adam이 임베딩 벡터의 비등방성을 유발하는 원인을 시각적으로 설명합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Toy example of a hidden state vector hℎhitalic_h (shown in blue) and three embedding vectors eisubscript𝑒𝑖e_{i}italic_e start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT (shown in red) in H=2𝐻2H=2italic_H = 2 dimensions. The gray vectors represent the embedding update vectors, for the SGD (dark) and the Adam (light) optimizer. The update vector of the true token is aligned with hℎhitalic_h, while the others point in the opposite direction, see Eq. (5). Note that the sum of embedding update vectors vanishes for SGD, while this is not necessarily the case for Adam, cf. Eqs. (11) and (16).
> </details>





{{< table-caption >}}
| D | N | Adam | \mathcal{L} (\downarrow) | \rm Acc (\uparrow) | \rm Iso (\uparrow) | \|\mu\| (\downarrow) | \|\mu\|\rm r (\downarrow) | \overline{r} (\uparrow) | \rho (\uparrow) | \kappa (\uparrow) |
|---|---|---|---|---|---|---|---|---|---|---|---| 
| \resultsS |  |  |  |  |  |  |  |  |  |  | {{< /table-caption >}}

> 🔼 표 1은 논문의 소규모 실험 결과를 보여줍니다.  D는 데이터셋 크기, N은 모델 크기를 나타냅니다. ℒ은 테스트 손실이고, Acc 열은 4.3절에 나열된 다운스트림 작업에 대한 평균 정확도를 나타냅니다. 다른 평가 지표는 같은 섹션(식 25~28)에 정의되어 있으며, 괄호 안의 화살표는 더 높은 값이 바람직한지 낮은 값이 바람직한지를 나타냅니다. 모든 훈련은 서로 다른 시드를 사용하여 S=3번 반복되었으며, 표의 숫자는 반올림된 평균과 표준 편차를 나타냅니다. 예를 들어, 0.123 (4)는 0.123 ± 0.004를 의미합니다. 각 (D, N) 조합과 각 지표에 대해, (반올림되지 않은) 차이가 일방적 신뢰 수준 α=95%의 Student t-검정에 따라 유의미한 경우 해당 값이 굵게 표시됩니다(자세한 내용은 부록 F 참조).  ℒ과 Acc에 대한 그래프는 부록 G.1에 나와 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Results of our small-scale experiments. D𝐷Ditalic_D and N𝑁Nitalic_N denote the dataset and model size, respectively. ℒℒ\mathcal{L}caligraphic_L is the test loss, and the column AccAcc\rm Accroman_Acc represents the accuracy averaged over the downstream tasks listed in Sec. 4.3. The other evaluation metrics are defined in the same section, see Eqs. (25)-(28). The arrow in parentheses indicates whether a higher or lower value is desirable. Every training was conducted S=3𝑆3S=3italic_S = 3 times with different seeds, and the numbers represent the (rounded) averages and standard deviations in the following shorthand notation format: 0.1230.1230.1230.123 (4)4(4)( 4 ) ≡0.123±0.004absentplus-or-minus0.1230.004\equiv 0.123\pm 0.004≡ 0.123 ± 0.004. For each combination (D,N)𝐷𝑁(D,N)( italic_D , italic_N ) and each metric, the respective better value is highlighted in bold if the (unrounded) difference is significant according to Student’s t-test with a one-sided confidence level of α=95%𝛼percent95\alpha=95\%italic_α = 95 % (see App. F for details). Plots for ℒℒ\mathcal{L}caligraphic_L and AccAcc\rm Accroman_Acc are shown in App. G.1.
> </details>





### In-depth insights


#### Adam's Anisotropy
본 논문은 Adam 최적화 알고리즘이 언어 모델의 임베딩 벡터에 **비등방성(anisotropy)** 문제를 야기하는 원인을 분석하고, 이를 해결하기 위한 새로운 방법을 제시합니다.  Adam은 두 번째 모멘트를 사용하여 매개변수 업데이트 방향을 조정하는데, 이 과정에서 단어 빈도의 불균형이 **비등방성 임베딩**으로 이어집니다. 즉, 빈도가 높은 단어의 임베딩 벡터는 밀집되어 있고, 빈도가 낮은 단어는 산재되어 있습니다.  논문에서는 이러한 문제를 완화하기 위해, **모든 임베딩 벡터의 두 번째 모멘트를 평균화**하는 'Coupled Adam'이라는 수정된 최적화 알고리즘을 제안합니다.  실험 결과는 Coupled Adam이 임베딩 벡터의 품질을 향상시키고, 상위 및 하위 작업의 성능을 개선함을 보여줍니다. 특히, 대규모 데이터셋에서 그 효과가 두드러집니다.  이는 Adam의 고유한 특성과 데이터셋의 단어 분포 사이의 상호 작용에 대한 중요한 통찰력을 제공하며, 향후 언어 모델 연구에 유용한 지침을 제시합니다.  **Coupled Adam은 구현이 간단하고 효율적**이기 때문에, 실제 언어 모델 개발에 널리 적용될 가능성이 높습니다.

#### Coupled Adam
본 논문에서 제시된 "Coupled Adam"은 기존 Adam 최적화 알고리즘의 단점을 해결하기 위한 새로운 접근 방식입니다. **기존 Adam은 단어 임베딩 벡터의 비등방성(anisotropy)** 문제를 야기하는데, 이는 빈도가 낮은 단어의 임베딩 벡터가 과도하게 업데이트되는 현상에서 기인합니다. Coupled Adam은 **Adam의 두 번째 모멘트(second moment)를 모든 임베딩 벡터에 대해 동일하게 만들어** 이러한 비등방성 문제를 완화합니다.  이는 각 임베딩 벡터의 업데이트 스케일을 통일시켜, 빈도가 낮은 단어의 벡터가 과도하게 업데이트되는 것을 방지함으로써, **더욱 균형잡힌(isotropy) 임베딩 공간**을 생성하는 데 기여합니다.  실험 결과, Coupled Adam은 임베딩 품질을 향상시키고, 상위 및 하위 작업 모두에서 성능을 개선하는 것으로 나타났습니다. 특히, **대규모 데이터셋**에서 그 효과가 더욱 두드러집니다.  하지만,  **계산 비용 증가** 및 **하이퍼파라미터 조정**에 대한 추가적인 연구가 필요할 것으로 예상됩니다.

#### Empirical Findings
본 논문의 '경험적 결과' 부분은 **제안된 방법의 효과를 실험적으로 검증**하는 데 중점을 둡니다. 다양한 규모의 데이터셋과 모델을 사용한 실험 결과를 통해, 제안된 방법이 **임베딩의 질을 향상**시키고, 상류 및 하류 작업의 성능을 개선함을 보여줍니다. 특히, **대규모 데이터셋일수록 성능 향상 효과가 더욱 두드러짐**을 확인할 수 있습니다. 또한, 임베딩의 등방성을 정량적으로 측정하여, 제안된 방법이 **임베딩의 등방성을 개선**하는 데 효과적임을 입증합니다.  **제안된 방법의 우수성은 통계적으로 유의미한 수준**으로 나타납니다.  그러나, 일부 실험 설정에서는 성능 향상이 제한적일 수 있으며, 이에 대한 추가적인 분석이 필요할 수 있습니다.  **결론적으로, 이 부분은 제안된 방법의 실용성과 효과를 뒷받침하는 핵심적인 증거를 제시**하지만, 향후 연구를 위한 추가적인 탐구 영역도 제시합니다.

#### Future Work
본 논문은 LLMs에서의 embedding anisotropy 문제를 해결하기 위한 Coupled Adam이라는 새로운 최적화 알고리즘을 제시합니다. **Coupled Adam은 Adam의 두 번째 모멘트를 조정하여 embedding vector의 불균형을 완화**시키는 데 효과적임을 보여줍니다.  하지만 이는 아직 초기 단계의 연구이며, 향후 연구 방향으로는 다음과 같은 내용이 고려될 수 있습니다.  **다양한 모델 아키텍처와 더 큰 규모의 데이터셋**에 대한 Coupled Adam의 일반화 성능 평가가 필요합니다.  또한, **weight tying의 영향**에 대한 추가적인 조사를 통해 anisotropy 문제에 대한 더욱 심도있는 이해를 도모할 수 있습니다.  **Coupled Adam의 효율성을 높이기 위한 구현 최적화**도 중요한 과제입니다.  마지막으로, **다른 최적화 알고리즘**과의 비교 분석을 통해 Coupled Adam의 우수성을 더욱 명확히 밝히는 연구가 필요합니다.  이러한 추가적인 연구들을 통해 Coupled Adam의 실용성과 효과성을 더욱 강화하고, LLMs의 성능 향상에 기여할 수 있을 것입니다.

#### Study Limitations
본 연구의 제한점은 크게 세 가지로 요약할 수 있습니다. 첫째, **모델의 크기 제한**입니다. 본 연구에서는 최대 26억개의 파라미터를 가진 모델까지만 실험하였습니다. 따라서 더 큰 모델에 대한 일반화 가능성은 추가적인 연구가 필요합니다. 둘째, **데이터셋의 제한**입니다. 다양한 크기의 데이터셋을 사용하였으나, 사용된 데이터셋 자체가 연구의 일반화 가능성을 제한할 수 있습니다. 더욱 다양하고 방대한 데이터셋을 사용한 추가 연구가 필요합니다. 셋째, **방법론의 제한**입니다. 본 연구에서 제안한 방법은 특정 최적화 알고리즘과 모델 구조에 초점을 맞추고 있습니다. 다른 알고리즘이나 구조에는 적용되지 않을 수 있으며, 더욱 폭넓은 방법론적 연구가 필요합니다.  이러한 제한점들을 고려하여, **후속 연구**에서는 더욱 큰 모델과 다양한 데이터셋, 그리고 더욱 폭넓은 방법론을 사용하여 본 연구의 결과를 검증하고 확장하는 것이 중요합니다. 특히, **일반화 가능성을 높이는 연구**는 향후 연구의 중요한 방향이 될 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.08441/extracted/6201951/figs/experimental_results_E_p_125M_20B.png)

> 🔼 그림 4는 모델 크기 N=125M, 데이터셋 크기 D=D'=20B일 때, 임베딩 업데이트 벡터의 제곱의 기댓값 𝔼[v̂i] 와 단어 빈도 p̃i 간의 관계를 보여줍니다.  세로축은 𝔼[v̂i], 가로축은 p̃i를 나타내며, 파란색 선은 R2=0.91인 선형 회귀선입니다. 이 그림은 Adam 최적화 알고리즘에서 임베딩 벡터의 업데이트 크기가 단어 빈도와 어떻게 비례하는지 보여주는 실험 결과를 시각적으로 보여줍니다. 즉, 흔한 단어일수록 임베딩 업데이트 크기가 작고, 드문 단어일수록 임베딩 업데이트 크기가 크다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Experimental results for 𝔼⁢[v^i]𝔼delimited-[]subscript^𝑣𝑖\mathbb{E}\left[\widehat{v}_{i}\right]blackboard_E [ over^ start_ARG italic_v end_ARG start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT ] (vertical axis) vs. p~isubscript~𝑝𝑖\widetilde{p}_{i}over~ start_ARG italic_p end_ARG start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT (horizontal axis) for N=125⁢M𝑁125MN=125\rm Mitalic_N = 125 roman_M and D=D′=20⁢B𝐷superscript𝐷′20BD=D^{\prime}=20\rm Bitalic_D = italic_D start_POSTSUPERSCRIPT ′ end_POSTSUPERSCRIPT = 20 roman_B. The blue line shows the linear fit with R2=0.91superscript𝑅20.91R^{2}=0.91italic_R start_POSTSUPERSCRIPT 2 end_POSTSUPERSCRIPT = 0.91.
> </details>



![](https://arxiv.org/html/2502.08441/extracted/6201951/figs/experimental_results_A.png)

> 🔼 그림 5는 Adam 최적화 알고리즘에서 두 번째 모멘트의 크기(v)에 대한 기대값(E[v])과 unigram 확률(p) 사이의 선형 관계에서의 기울기(A)를 보여줍니다.  이 기울기는 모델 크기(N)와 데이터셋 크기(D')의 함수로 나타나며,  데이터셋 크기가 증가함에 따라 기울기 A가 증가하는 경향을 보입니다.  즉, 더 큰 데이터셋으로 학습할수록 Adam 최적화 과정에서 발생하는 단어 임베딩의 비등방성이 심해지는 것을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Experimental results for the linear fit parameter A𝐴Aitalic_A as a function of N𝑁Nitalic_N and D′superscript𝐷′D^{\prime}italic_D start_POSTSUPERSCRIPT ′ end_POSTSUPERSCRIPT.
> </details>



![](https://arxiv.org/html/2502.08441/extracted/6201951/figs/experiments_log.png)

> 🔼 그림 6은 논문에서 수행된 소규모(파란색, 녹색, 주황색 원) 및 대규모(빨간색 사각형) 실험에 사용된 데이터셋 크기(가로축)와 모델 크기(세로축)를 보여줍니다. 점선은 Hoffmann 외의 논문에서 제시된 계산 최적 경로를 나타내는 N=D/20을 보여줍니다. 이 그림은 모델 크기와 데이터셋 크기 간의 관계를 시각적으로 보여주어, 실험 설계에 대한 이해를 돕습니다. 소규모 실험은 상대적으로 작은 모델과 데이터셋을 사용한 반면, 대규모 실험은 훨씬 큰 모델과 데이터셋을 사용했습니다. 점선은 계산 자원을 효율적으로 사용하는 모델 크기와 데이터셋 크기의 관계를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Overview of the dataset (horizontal axis) and model sizes (vertical axis) involved in our small-scale (blue, green and orange circles) and large-scale (red squares) experiments. The dashed, black line shows N=D/20𝑁𝐷20N=D/20italic_N = italic_D / 20, which is approximately the compute-optimal trajectory according to hoffmann2022trainingcomputeoptimallargelanguage.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| D | N | Adam | $\mathcal{L}$ ($\downarrow$) | Acc ($\uparrow$) | Iso ($\uparrow$) | $\|\mu\|$ ($\downarrow$) | $\|\mu\|^r$ ($\downarrow$) | $\overline{r}$ ($\uparrow$) | $\rho$ ($\uparrow$) | $\kappa$ ($\uparrow$) |
|---|---|---|---|---|---|---|---|---|---|---|
| \resultsL |  |  |  |  |  |  |  |  |  |  |{{< /table-caption >}}
> 🔼 표 2는 본 논문의 대규모 실험 결과를 보여줍니다. 표의 각 열은 테스트 손실, 다운스트림 작업 정확도, 임베딩 등방성, 평균 임베딩 벡터 크기, 임베딩 벡터의 평균 크기, 임베딩 벡터 길이와 단일 단어 확률 간의 상관 관계, 그리고 임베딩 행렬의 조건 수를 나타냅니다. 각 지표에 대해 더 높은 값이 바람직한지 더 낮은 값이 바람직한지는 화살표로 표시되어 있습니다. 데이터 크기(D)와 모델 크기(N)의 각 조합에 대해 표준 Adam과 Coupled Adam을 사용하여 훈련된 두 개의 모델 결과가 제시됩니다.  각 지표에 대해 더 나은 값은 굵게 표시됩니다. 표준 Adam과 Coupled Adam은 모두 임베딩 매개변수에 적용되며, 다른 모든 매개변수에는 표준 Adam이 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Results of our large-scale experiments. See the caption of Tab. 4.3 for an explanation of the column names. For each combination (D,N)𝐷𝑁(D,N)( italic_D , italic_N ) and each metric, the respective better value is highlighted in bold.
> </details>

{{< table-caption >}}
| Description | Small-scale | Large-scale |
|---|---|---|
| optimizer | AdamW | AdamW |
| \(\beta_{1}\) | 0.9 | 0.9 |
| \(\beta_{2}\) | 0.95 | 0.95 |
| \(\epsilon\) | 1e-8 | 1e-8 |
| weight decay | 0.1 | 0.1 |
| gradient clipping | 1.0 | 1.0 |
| dropout | 0.0 | 0.0 |
| weight tying | true | true |
| vocab size | 50304 | 50304 |
| learning rate schedule | cosine decay | cosine decay |
| layer normalization | LayerNorm | LayerNorm |
| precision | BF16 | BF16 |
| hidden activation | GeLU | SwiGLU |
| positional embedding | absolute (learned) | RoPE |
| sequence length | 1024 | 2048 |
| batch size (samples) | 96 | 256 |
| batch size (tokens) | \(\sim\)100k | \(\sim\)500k |
| warmup | 100 steps | 1\% of steps |
| training framework | nanoGPT | Modalities |
| training parallelism | DDP | FSDP |{{< /table-caption >}}
> 🔼 알고리즘 2는 임베딩 벡터에 적용되는 선택적 모멘텀을 갖는 SGD 알고리즘의 의사 코드를 보여줍니다.  이 표는 SGD 알고리즘의 각 단계(입력, 초기 임베딩, 목적 함수, 모멘텀, 시간 단계, 출력)를 설명하고, 모멘텀을 사용하는 방법과 임베딩 벡터를 업데이트하는 방법을 자세하게 보여줍니다. 이는 논문에서 제시된 Coupled Adam 알고리즘과 비교하여 SGD 알고리즘의 작동 방식을 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Algorithm 2  Pseudocode for the SGD algorithm with optional momentum, applied to the embedding vectors eisubscript𝑒𝑖e_{i}italic_e start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT.
> </details>

{{< table-caption >}}
| N | lr | heads | layers | emb. dim. |
|---|---|---|---|---|
| 124M | 6.0e-4 | 12 | 12 | 768 |
| 350M | 3.0e-4 | 16 | 24 | 1024 |
| 760M | 2.5e-4 | 16 | 24 | 1536 |
| 1.3B | 2.0e-4 | 32 | 24 | 2048 |
| 2.6B | 1.6e-4 | 32 | 32 | 2560 |{{< /table-caption >}}
> 🔼 표 5는 본 논문에서 수행된 두 가지 유형의 실험(소규모 및 대규모 실험)에 사용된 일반적인 하이퍼파라미터들을 보여줍니다.  표에는 최적화기, 베타 값, 가중치 감소, 그래디언트 클리핑, 드롭아웃, 가중치 연결, 어휘 크기, 학습률 스케줄, 레이어 정규화, 정밀도, 은닉 활성화 함수, 위치 임베딩, 시퀀스 길이, 배치 크기(샘플 및 토큰), 워밍업, 학습 프레임워크, 병렬 학습 등 다양한 하이퍼파라미터들이 포함되어 있습니다. 소규모 실험과 대규모 실험에 따라 일부 하이퍼파라미터 값이 다르게 설정되었음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 5: General hyperparameters used in our two sets of experiments.
> </details>

{{< table-caption >}}
| D | N | Optimizer | \mathcal{L} (\downarrow) | \rm Acc (\uparrow) | \rm Iso (\uparrow) | \|\mu\| (\downarrow) | \|\mu\|\rm r (\downarrow) | \overline{r} (\uparrow) | \rho (\uparrow) | \kappa (\uparrow) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| \resultsAblationsSGDExpFive |  |  |  |  |  |  |  |  |  |  | {{< /table-caption >}}
> 🔼 표 6은 논문에서 사용된 모델 크기에 따른 하이퍼파라미터를 보여줍니다.  N은 모델의 파라미터 수를 나타내고, lr은 최대 학습률을 의미합니다.  표에는 모델 크기(N)가 증가함에 따라 최대 학습률(lr)을 비롯한 다양한 하이퍼파라미터들이 어떻게 조정되었는지를 보여주는 정보가 담겨있습니다. 이는 모델 크기 변화에 따른 학습 과정의 안정성 및 효율성을 유지하기 위한 하이퍼파라미터 조정 전략을 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Model-size dependent hyperparameter used in our experiments. N𝑁Nitalic_N denotes the model size in terms of parameters, while lr corresponds to the maximum learning rate.
> </details>

{{< table-caption >}}
| D | N | Optimizer | \mathcal{L} (\downarrow) | \rm Acc (\uparrow) | \rm Iso (\uparrow) | \|\mu\| (\downarrow) | \|\mu\|<sup>\rm r</sup> (\downarrow) | \overline{r} (\uparrow) | \rho (\uparrow) | \kappa (\uparrow) |
|---|---|---|---|---|---|---|---|---|---|---|---|
| \resultsAblationsSGDExpTen |  |  |  |  |  |  |  |  |  |  |  |{{< /table-caption >}}
> 🔼 표 7은 임베딩에 대한 최적화 기법으로 SGD(확률적 경사 하강법)를 사용한 실험 결과를 보여줍니다.  다양한 모델 크기(N)와 데이터셋 크기(D)에 대해, 표준 Adam과 Coupled Adam을 사용한 결과와 비교하여 손실(L), 정확도(Acc), 등방성(Iso), 평균 임베딩 벡터 크기(||µ||), 평균 임베딩 벡터 크기의 비율(||µ||/||e||), 상관관계(p), 조건수(κ) 등 다양한 지표를 측정했습니다.  같은 열의 다른 값들보다 통계적으로 유의미하게 더 좋은 값을 가지는 경우 굵은 글씨체로 표시했습니다. 이를 통해, SGD와 Coupled Adam의 성능을 비교분석하고, 임베딩 품질에 미치는 영향을 다각적으로 평가하여 최적의 임베딩 전략을 제시하고자 했습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Results of our experiments with SGD. Values are highlighted in bold if they are significantly better than all the other values in the same column.
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
{{< /gallery >}}