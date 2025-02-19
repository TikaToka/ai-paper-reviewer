---
title: "CRANE: Reasoning with constrained LLM generation"
summary: "CRANE: 제약된 LLM 생성을 통한 추론 개선"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 University of Illinois Urbana-Champaign",]
showSummary: true
date: 2025-02-13
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.09061 {{< /keyword >}}
{{< keyword icon="writer" >}} Debangshu Banerjee et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-18 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.09061" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.09061" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/crane-reasoning-with-constrained-llm" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)은 코드 생성, 수학적 추론 등 다양한 작업에 활용되고 있지만, 출력 결과가 특정 도구나 시스템의 입력 요구사항을 충족하지 못하는 경우가 많습니다. 기존의 제약된 디코딩 알고리즘은 이러한 문제를 해결하기 위해 LLM의 출력을 공식적인 제약 조건에 맞추려고 하지만, LLM의 추론 능력을 저하시키는 부작용이 발생하는 것으로 알려져 있습니다. 

본 논문에서는 이러한 문제에 대한 이론적 설명과 함께, LLM의 추론 능력을 유지하면서 구문 및 의미상의 정확성을 보장하는 새로운 제약된 디코딩 알고리즘인 CRANE을 제시합니다. CRANE은 출력 문법에 추가적인 규칙을 추가하여 LLM이 중간 추론 단계를 생성할 수 있도록 하면서, 최종 출력은 여전히 제약 조건을 만족하도록 합니다. 실험 결과, CRANE은 기존 방법보다 우수한 성능을 보였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} CRANE은 제약된 LLM 생성에서 **LLM의 추론 능력 저하 문제를 해결**합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} CRANE은 **구문 및 의미 정확성을 유지**하면서 LLM의 추론 능력을 향상시킵니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} CRANE은 **GSM-symbolic 및 FOLIO와 같은 기준 데이터 세트에서 기존 방법보다 성능이 우수**함을 보여줍니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 제약된 LLM 생성에서 발생하는 문제점을 해결하기 위한 새로운 방법론인 CRANE을 제시하여 **LLM의 추론 능력을 유지하면서 구문 및 의미 정확성을 보장**하는 데 중요한 의미를 가집니다. 기존의 제약된 디코딩 방법론은 LLM의 추론 능력을 저하시키는 단점이 있었지만, CRANE은 이러한 문제를 효과적으로 해결하여 **다양한 응용 분야에서 LLM 성능을 향상**시킬 수 있는 잠재력을 가지고 있습니다. 특히, **기호 추론 및 코드 생성과 같은 복잡한 작업**에서 그 효과가 두드러질 것으로 예상되며, 향후 연구에서 더욱 발전된 형태로 활용될 수 있을 것입니다. 또한, 본 논문에서 제시된 이론적 분석 및 실험 결과는 **향후 LLM의 제약된 생성 연구**에 중요한 참고 자료가 될 것입니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.09061/extracted/6200562/figures/example.png)

> 🔼 그림 1은 GSM-symbolic 데이터셋의 한 예시를 보여줍니다. 파란색으로 표시된 변수들을 사용하여, 제약 없는 생성(unconstrained generation)은 구문론적으로 틀린 출력을 생성하는 반면, 제약 있는 생성(constrained generation)은 구문론적으로는 정확하지만 의미론적으로는 틀린 답을 생성합니다. 그러나 CRANE은 정확한 답을 생성합니다.  이 그림은 제약 조건이 LLM 추론 능력에 미치는 영향과 CRANE이 이러한 문제를 어떻게 해결하는지 보여주는 중요한 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: An example from the GSM-symbolic dataset (variables in blue) where unconstrained generation produces syntactically incorrect output, while constrained generation provides a syntactically valid but incorrect answer. CRANE, however, generates a correct answer.
> </details>





{{< table-caption >}}
| Model | Method | Acc. (%) | Parse (%) | Tokens |
|---|---|---|---|---|
|  | Unconstrained w/o CoT | 21 | 97 | 23.34 |
|  | Constrained | 22 | 97 | 25.29 |
| Qwen2.5-1.5B-Instruct | Unconstrained CoT | 26 | 90 | 128.97 |
|  | **CRANE** | **31** | 100 | 131.3 |
|  | Unconstrained w/o CoT | 36 | 94 | 17.92 |
|  | Constrained | 35 | 99 | 25.28 |
| Qwen2.5-Coder-7B-Instruct | Unconstrained CoT | 37 | 88 | 138.38 |
|  | **CRANE** | **39** | 94 | 155.32 |
|  | Unconstrained w/o CoT | 27 | 89 | 25.7 |
|  | Constrained | 29 | 99 | 26.81 |
| Qwen2.5-Math-7B-Instruct | Unconstrained CoT | 29 | 82 | 155.26 |
|  | **CRANE** | **38** | 94 | 158.86 |
|  | Unconstrained w/o CoT | 21 | 73 | 128.38 |
|  | Constrained | 26 | 98 | 35.97 |
| Llama-3.1-8B-Instruct | Unconstrained CoT | 30 | 95 | 163.55 |
|  | **CRANE** | **33** | 95 | 170.22 |
|  | Unconstrained w/o CoT | 18 | 89 | 21.64 |
|  | Constrained | 20 | 99 | 17.21 |
| DeepSeek-R1-Distill-Qwen-7B | Unconstrained CoT | 24 | 89 | 212.24 |
|  | **CRANE** | **29** | 92 | 235.78 |
|  | Unconstrained w/o CoT | 12 | 77 | 29.2 |
|  | Constrained | 13 | 96 | 16.89 |
| DeepSeek-R1-Distill-Llama-8B | Unconstrained CoT | 21 | 87 | 250.83 |
|  | **CRANE** | **31** | 92 | 268.82 |{{< /table-caption >}}

> 🔼 표 1은 GSM-Symbolic 데이터셋에서 CRANE과 여러 기준 모델들의 성능을 비교한 표입니다.  다양한 크기의 LLM 모델들(매개변수 수가 다른 모델들)에 대해, CRANE은 기존의 제약된 디코딩 방법과 비교하여 정확도가 상당히 향상되었음을 보여줍니다.  특히, CRANE은 문법적으로 올바른 응답을 생성하는 동시에 LLM의 추론 능력을 유지하여, 정확성과 효율성을 모두 개선했습니다.  표에는 각 모델과 방법에 대한 정확도(Acc.), 구문 분석 성공률(Parse %), 토큰 수, 그리고 평균 시간 등이 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparison of CRANE and baselines with different models on GSM-Symbolic.
> </details>





### In-depth insights


#### Constrained LLM Expressivity
제한된 LLM 표현력에 대한 논의는 **제한된 출력 문법(G) 하에서 일정 수준의 계층을 가진 LLM의 문제 해결 능력 감소** 현상에 대한 이론적 설명을 제공합니다.  **제한적인 문법은 LLM이 중간 추론 단계를 생성하는 것을 방해하여 표현력을 감소**시키는 주요 원인으로 지목됩니다.  이러한 제한은 단순히 문법적 정확성에만 초점을 맞춘 기존 제한된 디코딩 알고리즘의 단점을 드러냅니다.  **본 연구는 문법에 추가적인 규칙을 추가하여 LLM의 추론 능력을 유지하면서 구문 및 의미상의 정확성을 보장**할 수 있음을 보여줍니다.  이를 통해 제한된 생성의 이점과 제한되지 않은 생성의 유연성 간의 균형을 맞추는 것이 가능해집니다.  **추론에 필요한 중간 단계를 허용하는 확장된 문법(Ga)**을 사용하여 LLM의 표현력을 유지하는 방법을 제시하며, 이는 다양한 LLM과 제한된 디코딩 알고리즘에 적용 가능한 이론적 근거를 제공합니다.  결론적으로, 제한된 LLM 표현력에 대한 심층적 분석은 제한된 디코딩 알고리즘의 한계를 극복하고, 보다 효과적인 제한된 LLM 생성을 위한 새로운 방향을 제시합니다.

#### CRANE Algorithm
본 논문에서 제시된 CRANE 알고리즘은 제약된 LLM 생성의 효율성과 유연성을 동시에 달성하기 위한 핵심 전략입니다. **CRANE은 제약된 생성과 비제약된 생성을 적절히 조합하여 LLM의 추론 능력을 유지하면서 동시에 구문 및 의미적 정확성을 보장**합니다.  **핵심 아이디어는 제약된 생성 단계와 비제약된 추론 단계를 번갈아 수행하는 것**입니다. 이는 제약적인 문법으로 인해 발생할 수 있는 LLM의 추론 능력 저하 문제를 해결합니다. 특히, 시작 및 종료 구분자를 활용하여 제약된 생성 단계와 비제약된 생성 단계 간의 전환을 효율적으로 제어하는 방식이 돋보입니다.  **이러한 전략을 통해 CRANE은 기존의 제약된 디코딩 방법과 표준 비제약된 디코딩 방법보다 우수한 성능을 보이며, 특히 복잡한 기호 추론 벤치마크에서 최대 10%의 정확도 향상**을 보여줍니다.  **CRANE 알고리즘은 다양한 오픈 소스 LLM 및 벤치마크에서 효과적으로 작동**하며, 실용적인 제약된 LLM 생성 시스템 구축에 중요한 발전을 가져올 것으로 기대됩니다.  **CRANE은 이론적 근거와 실험적 결과를 모두 바탕으로 하여 제약된 LLM 생성 분야에 대한 중요한 통찰력을 제공**합니다.

#### GSM-Symbolic Results
GSM-Symbolic 결과는 제약된 LLM 생성의 효과를 평가하기 위한 중요한 척도입니다. 이는 수학적 추론 능력을 측정하는 데 초점을 맞춘, **상징적 변수와 수학적 연산으로 구성된 수학 문제 풀이 데이터셋**입니다.  CRANE 모델의 성능을 평가하는 데 있어 GSM-Symbolic 데이터셋의 사용은, **모델이 생성한 수학적 표현의 정확성과 구문적 정확성을 측정**할 수 있다는 점에서 중요합니다.  **정확도 향상**은 CRANE이 제약된 생성의 이점과 비제약된 생성의 유연성을 효과적으로 결합하여 **LLM의 추론 능력을 유지하면서도 구문 및 의미상의 정확성을 보장**할 수 있음을 보여줍니다.  **다양한 모델에서 일관된 성능 향상**은 CRANE 접근 방식의 일반성과 견고성을 시사합니다.  **토큰 수**와 관련해서는, CRANE이 기준 모델에 비해 더 많은 토큰을 생성하는 경향이 있지만, 이는 더욱 **심층적인 추론 과정**을 반영하는 것으로 해석될 수 있습니다.  **정확성과 효율성 사이의 균형**은 제약된 LLM 생성 시스템을 설계하는 데 중요한 고려 사항이며, GSM-Symbolic 결과는 CRANE이 이러한 균형을 잘 맞추고 있음을 보여주는 강력한 증거입니다.

#### FOLIO Experiments
FOLIO 실험은 논문의 핵심 주장을 뒷받침하는 중요한 부분입니다.  **다양한 LLM 모델을 사용하여 FOLIO 벤치마크에서 CRANE 알고리즘의 성능을 평가**했을 것입니다.  단순히 정확도만 비교하는 것이 아니라, **구문 분석 성공률, 생성된 토큰 수 등 다양한 지표를 종합적으로 분석**했을 것으로 예상됩니다.  **기존의 제약된 디코딩 방법이나 비제약된 디코딩 방법과 비교하여 CRANE의 우수성을 보여주는 실험 결과**를 제시했을 것입니다.  **특히, 논리적 추론 능력 저하 없이 구문 오류를 줄이는 CRANE의 효과**를 실험적으로 입증하는데 초점을 맞추었을 것으로 예상됩니다.  **다른 모델들과의 비교를 통해 CRANE의 일반성과 범용성**을 확인하는 실험도 포함되었을 것입니다.  이러한 실험 결과들은 **CRANE 알고리즘의 실용성과 효율성**을 보여주는 강력한 근거가 될 것입니다.

#### Future Work
본 논문은 제약된 LLM 생성을 위한 새로운 알고리즘인 CRANE을 제시하고, 제약된 생성의 표현력 한계를 이론적으로 밝히고, 제약된 디코딩에서 LLM의 추론 능력을 보존하는 방법을 제시합니다. **향후 연구 방향으로는 먼저, 제약된 디코딩 알고리즘을 더욱 개선하여 효율성을 높이고, 다양한 유형의 LLM 및 다양한 작업에 대한 적용성을 확장하는 것입니다.**  둘째, 제약된 생성 시 발생할 수 있는 문제점들, 예를 들어 과도한 제약으로 인한 추론 능력 저하, 특정 문법에 대한 의존성 등을 보다 심층적으로 분석하고 해결 방안을 마련해야 합니다. **특히, 제약 조건의 수준과 추론 성능 간의 관계를 정량적으로 분석하고, 최적의 제약 조건 설정 전략을 제시하는 연구가 필요합니다.**  셋째, 제안된 CRANE 알고리즘의 성능을 다양한 벤치마크 및 실제 응용 사례에 적용하여 검증하고, 다른 기존 방법들과의 비교 분석을 통해 CRANE의 우수성을 입증하는 연구가 필요합니다. 마지막으로, **CRANE 알고리즘을 다른 생성 모델, 예를 들어 이미지 생성 모델, 음성 생성 모델 등에 적용하는 연구도 필요합니다.** 이를 통해 CRANE의 일반화 가능성을 높이고, 다양한 분야에서의 응용 가능성을 확대할 수 있습니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.09061/extracted/6200562/figures/crane.png)

> 🔼 그림 2는 CRANE 알고리즘이 제약된(constrained) 및 제약되지 않은(unconstrained) LLM 생성을 어떻게 적응적으로 전환하는지 보여줍니다.  특히, '<<' 및 '>>'(이 예시에서는) 와 같은 시작 및 끝 구분 기호(delimiter)를 사용하여 제약된 LLM 생성이 적용되어야 하는 구간(그림에서 강조 표시된 부분)을 동적으로 추적합니다.  즉, CRANE은 추론(reasoning) 단계에서는 제약 없이 LLM을 자유롭게 생성하게 하고, 구문(syntax) 및 의미(semantic)가 올바른 최종 결과를 생성해야 하는 단계에서는 제약된 생성을 적용하여, 추론 능력과 생성 품질 사이의 균형을 유지합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2:  CRANE adaptively switches between constrained LLM generation and unconstrained LLM generation based on start and end delimiters (in this example << and >>). Using these delimiters, CRANE dynamically tracks which windows (highlighted in the figure) of the LLM generation constraints should be applied to.
> </details>



![](https://arxiv.org/html/2502.09061/extracted/6200562/figures/k_accuracy_Qwen2.5-Math-7B-Instruct.png)

> 🔼 이 그림은 GSM-Symbolic 데이터셋을 사용하여 Qwen2.5-Math-7B-Instruct 모델의 정확도를 다양한 샷 수와 방법에 따라 비교 분석한 결과를 보여줍니다.  x축은 사용된 몇 샷(few-shot)의 수를 나타내고, y축은 모델의 정확도(%)를 나타냅니다.  그림에는 Unconstrained(제약 없는), Constrained(제약 있는), Unconstrained CoT(사고 과정을 포함한 제약 없는), CRANE(본 논문에서 제안하는 방법) 등 네 가지 방법의 성능이 비교되어 있습니다. 이를 통해 샷 수가 증가함에 따라 각 방법의 정확도가 어떻게 변화하는지, 그리고 CRANE 방법이 다른 방법들에 비해 얼마나 우수한 성능을 보이는지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Accuracy (%) of Qwen2.5-Math-7B-Instruct By Method and Number of Shots on GSM-Symbolic
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | Method | Acc. (%) | Compiles (%) | Tokens |
|---|---|---|---|---|
|  | Unconstrained CoT | 18.72 | 54.19 | 629.59 |
| Qwen2.5-Math-7B-Instruct | Constrained | 28.08 | 76.85 | 679.44 |
|  | CRANE | **31.03** | 75.86 | 690.17 |
|  | Unconstrained CoT | 36.95 | 70.94 | 350.64 |
| Qwen2.5-7B-Instruct | Constrained | 37.44 | 87.68 | 775.62 |
|  | CRANE | **42.36** | 87.68 | 726.88 |
|  | Unconstrained CoT | 32.02 | 57.14 | 371.52 |
| Llama-3.1-8B-Instruct | Constrained | 39.41 | 86.21 | 549.75 |
|  | CRANE | **46.31** | 85.71 | 449.77 |{{< /table-caption >}}
> 🔼 표 2는 FOLIO 데이터셋에서 다양한 언어 모델에 대해 CRANE과 기준 모델들의 성능을 비교한 표입니다.  정확도, 컴파일 성공률, 그리고 토큰 수를 측정하여 CRANE의 효과를 보여줍니다.  각 모델에 대해 CRANE이 기준 모델들보다 우수한 성능을 보이는지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Comparison of CRANE and baselines with various models on FOLIO.
> </details>

{{< table-caption >}}
| Model | k | Method | Acc. (%) | Parse (%) | Tokens |
|---|---|---|---|---|---| 
|  |  | Unconstrained w/o CoT | 20 | 98 | 18.23 |
|  |  | Constrained | 21 | 95 | 34.28 |
| Qwen2.5-1.5B-Instruct | 2 | Unconstrained CoT | 22 | 90 | 130.74 |
|  |  | CRANE | **28** | 96 | 140.52 |
|  |  | Unconstrained w/o CoT | 18 | 95 | 18.23 |
|  |  | Constrained | 18 | 96 | 34.28 |
| Qwen2.5-1.5B-Instruct | 4 | Unconstrained CoT | 24 | 94 | 130.74 |
|  |  | CRANE | **30** | 98 | 140.52 |
|  |  | Unconstrained w/o CoT | 21 | 97 | 23.34 |
|  |  | Constrained | 22 | 97 | 25.29 |
| Qwen2.5-1.5B-Instruct | 8 | Unconstrained CoT | 26 | 90 | 128.97 |
|  |  | CRANE | **31** | 100 | 131.3 |
|  |  | Unconstrained w/o CoT | 37 | 96 | 17.22 |
|  |  | Constrained | 36 | 99 | 18.61 |
| Qwen2.5-Coder-7B-Instruct | 2 | Unconstrained CoT | 32 | 84 | 148.87 |
|  |  | CRANE | **37** | 96 | 155.65 |
|  |  | Unconstrained w/o CoT | 36 | 96 | 16.89 |
|  |  | Constrained | 36 | 100 | 18.81 |
| Qwen2.5-Coder-7B-Instruct | 4 | Unconstrained CoT | 35 | 89 | 151.29 |
|  |  | CRANE | **37** | 97 | 163.21 |
|  |  | Unconstrained w/o CoT | 36 | 94 | 17.92 |
|  |  | Constrained | 35 | 99 | 25.28 |
| Qwen2.5-Coder-7B-Instruct | 8 | Unconstrained CoT | 37 | 88 | 138.38 |
|  |  | CRANE | **39** | 94 | 155.32 |
|  |  | Unconstrained w/o CoT | 20 | 66 | 115.22 |
|  |  | Constrained | 26 | 95 | 26.99 |
| Qwen2.5-Math-7B-Instruct | 2 | Unconstrained CoT | 28 | 72 | 190.51 |
|  |  | CRANE | **32** | 89 | 195.65 |
|  |  | Unconstrained w/o CoT | 22 | 83 | 47 |
|  |  | Constrained | 29 | 98 | 27.08 |
| Qwen2.5-Math-7B-Instruct | 4 | Unconstrained CoT | 28 | 76 | 184.35 |
|  |  | CRANE | **37** | 88 | 194.77 |
|  |  | Unconstrained w/o CoT | 27 | 89 | 25.7 |
|  |  | Constrained | 29 | 99 | 26.81 |
| Qwen2.5-Math-7B-Instruct | 8 | Unconstrained CoT | 29 | 82 | 155.26 |
|  |  | CRANE | **38** | 94 | 158.86 |
|  |  | Unconstrained w/o CoT | 19 | 61 | 157.36 |
|  |  | Constrained | 23 | 95 | 45.58 |
| Llama-3.1-8B-Instruct | 2 | Unconstrained CoT | 29 | 84 | 198.64 |
|  |  | CRANE | **35** | 94 | 206.85 |
|  |  | Unconstrained w/o CoT | 18 | 68 | 131.5 |
|  |  | Constrained | 24 | 96 | 37.38 |
| Llama-3.1-8B-Instruct | 4 | Unconstrained CoT | 26 | 92 | 172.21 |
|  |  | CRANE | **30** | 97 | 179.95 |
|  |  | Unconstrained w/o CoT | 21 | 73 | 128.38 |
|  |  | Constrained | 26 | 98 | 35.97 |
| Llama-3.1-8B-Instruct | 8 | Unconstrained CoT | 30 | 95 | 163.55 |
|  |  | CRANE | **33** | 95 | 170.22 |{{< /table-caption >}}
> 🔼 표 3은 GSM-Symbolic 데이터셋에서 다양한 언어 모델에 대해 CRANE과 기준 모델들의 성능을 정확도, 생성된 토큰 수, 평균 시간 세 가지 측면에서 비교 분석한 결과를 보여줍니다.  각 모델별로 제약 없는 생성(CoT 사용 유무), 제약된 생성, CRANE 세 가지 방법의 성능을 비교하여 CRANE의 효과성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Comparison of CRANE and baselines with various models on GSM-Symbolic based on accuracy, number of tokens, and average time.
> </details>

{{< table-caption >}}
| Model | Method | pass@1/2/3 (%) | Parse (%) | Tokens |
|---|---|---|---|---|
|  | Unconstrained w/o CoT (Greedy) | 21 | 97 | 23.34 |
|  | Unconstrained w/o CoT (t = 0.7) | 15/19/22 | 88/96/98 | 20.19/39.76/60.57 |
|  | Constrained (Greedy) | 22 | 97 | 25.29 |
| Qwen2.5-1.5B-Instruct | Unconstrained CoT (Greedy) | 26 | 90 | 128.97 |
|  | Unconstrained CoT (t = 0.7) | 21/25/30 | 78/91/96 | 146.22/292.96/444.61 |
|  | CRANE | 31 | 100 | 131.3 |
|  | Unconstrained w/o CoT (Greedy) | 21 | 73 | 128.38 |
|  | Unconstrained w/o CoT (t = 0.7) | 15/21/25 | 51/74/84 | 106.88/232.75/369.86 |
|  | Constrained (Greedy) | 26 | 98 | 35.97 |
| Llama-3.1-8B-Instruct | Unconstrained CoT (Greedy) | 30 | 95 | 163.55 |
|  | Unconstrained CoT (t = 0.7) | 24/29/35 | 89/98/98 | 196.01/403.68/607.7 |
|  | CRANE (Greedy) | 33 | 95 | 170.22 |{{< /table-caption >}}
> 🔼 표 4는 GSM-Symbolic 데이터셋에서 CRANE과 탐욕적(greedy) 및 샘플링 기반의 기준 모델들을 비교 분석한 결과를 보여줍니다.  CRANE은 탐욕적 디코딩과 샘플링 디코딩 모두에서 정확도와 구문 분석 성공률을 크게 향상시켰습니다. 특히, 샘플링 기반의 비교 분석을 통해 CRANE의 우수성을 더욱 명확하게 제시하고 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Comparison of CRANE and greedy and sampling baselines with different models on GSM-Symbolic.
> </details>

{{< table-caption >}}
| Model | Method | pass@1/2/3 (%) | Compile (%) | Tokens |
|---|---|---|---|---|
|  | Unconstrained CoT (Greedy) | 36.95 | 70.94 | 350.64 |
|  | Unconstrained CoT (t = 0.7) | 16.75/28.57/34.98 | 35.96/55.67/68.47 | 401.5/800.19/1219.33 |
| Qwen2.5-7B-Instruct | Constrained (Greedy) | 37.44 | 87.68 | 775.62 |
|  | **CRANE** (Greedy) | **42.36** | 87.68 | 726.88 |
|  | Unconstrained CoT (Greedy) | 32.02 | 57.14 | 371.52 |
|  | Unconstrained CoT (t = 0.7) | 14.29/22.66/29.06 | 33.99/46.8/57.64 | 435.35/877.33/1307.45 |
| Llama-3.1-8B-Instruct | Constrained (Greedy) | 39.41 | 86.21 | 549.75 |
|  | **CRANE** (Greedy) | **46.31** | 85.71 | 449.77 |{{< /table-caption >}}
> 🔼 표 5는 FOLIO 데이터셋에서 다양한 모델에 대해 CRANE, 탐욕적(greedy) 방법 및 샘플링 기법의 성능을 비교한 결과를 보여줍니다.  정확도, 컴파일 성공률 및 토큰 수를 측정하여 각 방법의 효율성과 정확성을 평가합니다.  구체적으로, 제한된(constrained) 생성, CoT(Chain-of-Thought) 프롬프트가 있는 제한 없는 생성 및 CRANE의 세 가지 기준 방법에 대한 결과가 제시됩니다.  샘플링 기법을 적용한 경우, 여러 개의 샘플을 생성하고 그 중 최고의 결과를 기록합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Comparison of CRANE and greedy and sampling baselines with different models on FOLIO.
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