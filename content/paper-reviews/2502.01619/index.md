---
title: "Learning to Generate Unit Tests for Automated Debugging"
summary: "LLM 기반 자동 디버깅을 위한 단위 테스트 생성 및 활용 기술을 제시하는 논문입니다.  UTGEN이라는 새로운 방법론을 통해 오류를 효과적으로 찾아내는 단위 테스트를 생성하고, UTDEBUG라는 파이프라인으로  LLM의 디버깅 성능을 향상시켰습니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Department of Computer Science, UNC Chapel Hill",]
showSummary: true
date: 2025-02-03
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.01619 {{< /keyword >}}
{{< keyword icon="writer" >}} Archiki Prasad et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-04 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.01619" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.01619" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

소프트웨어 개발에서 코드의 정확성을 검증하고 개발자에게 피드백을 제공하는 데 단위 테스트(UT)가 중요한 역할을 합니다. 하지만, 수동으로 단위 테스트를 작성하는 것은 매우 어렵고 시간이 많이 소요됩니다. 따라서, 최근에는 대규모 언어 모델(LLM)을 이용하여 단위 테스트를 자동으로 생성하려는 연구가 활발히 진행되고 있습니다.  하지만 기존의 LLM 기반 단위 테스트 생성 방법은 오류를 잘 찾아내는 입력값을 생성하는 것과, 정답을 예측하는 것 사이에 상충관계가 존재하는 문제점이 있습니다.

본 논문에서는 이러한 문제를 해결하기 위해, **오류를 드러내는 입력값과 그에 대한 정답을 모두 생성하는 새로운 LLM 기반 단위 테스트 생성 방법(UTGEN)**을 제시합니다.  또한, 생성된 테스트가 부정확한 결과를 포함할 수 있다는 점을 고려하여, **UTDEBUG라는 강력한 디버깅 파이프라인**을 제시하여, 테스트 시간 계산을 통해 예측 정확도를 높이고, 여러 테스트 결과를 바탕으로 오류 수정을 검증 및 되돌리는 기능을 추가했습니다.  실험 결과, 제안된 방법은 기존 방법보다 단위 테스트 생성 및 코드 디버깅 성능을 크게 향상시키는 것으로 나타났습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} LLM을 활용한 자동화된 코드 디버깅을 위한 새로운 단위 테스트 생성 기법(UTGEN)을 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} UTGEN을 통하여 생성된 단위 테스트를 효과적으로 활용하는 디버깅 파이프라인(UTDEBUG) 개발 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} HumanEval-Fix 및 MBPP+ 데이터셋에서 기존 방법론 대비 디버깅 정확도를 상당히 향상시키는 결과를 도출 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **자동화된 디버깅을 위한 단위 테스트 생성 및 활용**이라는 중요한 문제에 대한 해결책을 제시합니다.  **소스 코드의 버그를 효과적으로 찾아내고 수정하는 데 단위 테스트가 필수적**이며,  본 연구는 이를 자동화함으로써 연구자들이 더욱 효율적으로 코드 디버깅을 수행할 수 있도록 지원합니다. 특히 **LLM(대규모 언어 모델)을 이용한 코드 디버깅의 어려움을 해결**하고, 새로운 연구 방향을 제시하여 **향후 연구의 발전에 크게 기여**할 것으로 예상됩니다. 더불어, 본 연구에서 제시된 **UTGEN 및 UTDEBUG는 오픈소스로 공개**되어 다른 연구자들이 직접 활용하고 발전시킬 수 있다는 점에서 큰 의미가 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.01619/x1.png)

> 🔼  그림 1은 LLM을 사용한 코드 정확성 자체 평가의 개요를 보여줍니다. LLM을 사용하여 코드의 정확성을 자체 평가하는 것은 신뢰할 수 없으며, 사람이 작성한 단위 테스트를 수집하는 것은 많은 노력이 필요합니다. 본 논문에서는 잘못된 코드에 대해 오류를 유발하는 실패 단위 테스트를 자동으로 생성하는 UTGen을 제안합니다. 생성된 단위 테스트는 UTDebug를 통해 단위 테스트 피드백에 기반한 LLM 디버깅에 사용되어 향상된 다운스트림 코드 정확도를 달성할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  Overview: Self-evaluating code correctness using LLMs can be unreliable and collecting human-written unit tests can be laborious; we propose UTGen, which automatically generates failing unit tests for a faulty code (triggering errors) without access to the gold solution. The generated unit tests can in turn be used for LLM debugging based on unit test feedback via UTDebug, leading to improved downstream code accuracy.
> </details>





{{< table-caption >}}
| Model | UT Method | HE+Fix | MBPP+Fix | (Hard) |
|---|---|---|---|---|
| Llama-3 8B | No UT | 27.22 | 16.31 | 11.76 |
|  | Random | 51.90 | 30.46 | 17.06 |
|  | Prompted | 51.90 | 28.92 | 22.94 |
|  | UTGen | 53.80 | 37.54 | 28.82 |
| Llama-3.1 8B | No UT | 31.65 | 10.15 | 11.18 |
|  | Random | 62.03 | 33.54 | 13.53 |
|  | Prompted | 56.33 | 28.00 | 24.71 |
|  | UTGen | 67.09 | 36.92 | 28.23 |
| Qwen-2.5 7B | No UT | 52.53 | 23.08 | 16.47 |
|  | Random | 79.75 | 34.77 | 17.06 |
|  | Prompted | 75.32 | 32.92 | 24.12 |
|  | UTGen | 82.91 | 37.54 | 29.41 |{{< /table-caption >}}

> 🔼 표 1은 MBPP+Fix (Hard) 데이터셋에서 세 가지 모델(Llama-3 8B, Llama-3.1 8B, Qwen-2.5 7B)을 사용하여 세 번의 실행에 걸쳐 다양한 단위 테스트 생성 기준(UTGen 포함)의 내재적 지표를 평가한 결과를 보여줍니다.  각 모델에 대해 무작위 단위 테스트, 프롬프트를 사용한 단위 테스트 생성, 그리고 UTGen을 이용한 학습된 단위 테스트 생성의 세 가지 방법을 비교합니다.  세 가지 내재적 지표(공격률, 출력 정확도, 정확도 및 공격률) 모두 높을수록 좋습니다. 이 표는 단위 테스트 생성기의 성능을 평가하는 데 사용되는 세 가지 측정 기준(공격 성공률, 출력 정확도, 그리고 두 지표 모두 충족하는 비율)에 대한 결과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Evaluation on intrinsic UT generation metrics of different UT generation baselines and UTGen across different model families on MBPP+Fix (Hard) over 3 runs. Higher is better for all three intrinsic metrics.
> </details>





### In-depth insights


#### LLM Test Generation
LLM을 이용한 테스트 생성은 소프트웨어 개발의 효율성과 신뢰성을 높이는 핵심 기술입니다. 기존의 수동 테스트 작성 방식은 시간과 비용이 많이 소요되고, 인적 오류 가능성도 높습니다. LLM을 활용하면 **자동화된 테스트 생성**을 통해 이러한 문제를 해결할 수 있습니다.  **LLM은 코드 분석 및 이해 능력**을 바탕으로, 다양한 테스트 케이스를 생성하고 예상 결과를 예측할 수 있습니다.  **테스트 데이터 생성의 자동화**는 개발 주기를 단축하고, 개발자의 생산성을 향상시키는 데 크게 기여합니다. 하지만, LLM 기반 테스트 생성의 정확도와 신뢰성을 보장하는 것은 여전히 어려운 과제입니다. **LLM이 생성한 테스트의 품질을 관리**하고, 오류를 최소화하기 위한 후속 검증 절차가 필수적입니다.  또한, LLM이 생성한 테스트가 실제 코드의 결함을 얼마나 효과적으로 발견할 수 있는지에 대한 **실험적 검증**이 중요합니다.  **다양한 코드 스타일과 복잡도**에 대한 LLM의 적응력을 평가하고,  필요에 따라 추가적인 학습이나 미세 조정을 수행하는 것도 고려해야 합니다. LLM 기반 테스트 생성 기술은 아직 초기 단계이지만, 지속적인 연구 개발을 통해 **소프트웨어 개발 과정 전반의 효율성과 신뢰성 향상**에 큰 기여를 할 것으로 예상됩니다. 특히, **복잡한 시스템이나 대규모 프로젝트**에서 더욱 효과적으로 활용될 수 있을 것으로 기대됩니다. 따라서 LLM의 테스트 생성 능력 향상을 위한 지속적인 노력이 필요합니다.

#### UTGEN Training
UTGEN 훈련 과정은 **결함 코드를 생성하고 이를 공격하는 단위 테스트를 생성하는 데 초점**을 맞춥니다.  **기존 코드 생성 벤치마크를 수정하여 결함 코드를 생성**하고, 이를 바탕으로 단위 테스트 입력값을 생성합니다.  **단위 테스트의 출력값 정확도를 높이기 위해, 각 테스트에 대한 Chain-of-Thought(CoT) 스타일의 설명을 추가**하여 모델이 추론 과정을 거치도록 유도합니다.  결과적으로, **높은 공격률(error-revealing input)과 출력 정확도(correct output)를 동시에 달성**하는 단위 테스트 생성기를 훈련하는 데 성공합니다. 이 과정은 **단위 테스트 생성의 어려움을 해결**하고, **자동화된 디버깅 파이프라인에 활용**할 수 있는 고품질 단위 테스트를 제공하는 데 중요한 역할을 합니다.  **데이터 생성 방식의 혁신**과 **CoT 기법의 활용**이 핵심이며, 이는 자동화된 코드 디버깅의 효율성을 크게 향상시키는 주요 요소입니다.

#### UTDEBUG Pipeline
UTDEBUG 파이프라인은 잠재적으로 **잡음이 많은 모델 생성 단위 테스트**의 문제를 해결하기 위해 고안된 강력한 디버깅 방법입니다. 이는 **테스트 시간 확장**을 통해 생성된 단위 테스트의 출력 정확도를 높이고, 여러 단위 테스트를 생성하여 **과적합을 방지**하고, 검증 세트의 단위 테스트에 대한 영향을 기반으로 편집을 수락 또는 거부함으로써 **역추적**을 가능하게 합니다. 이러한 다중 단계 접근 방식을 통해 UTDEBUG는 잡음이 많은 피드백으로 인한 문제를 완화하고, 모델 생성 단위 테스트를 사용한 코드 디버깅의 효율성과 정확성을 크게 향상시킵니다. 특히, **복잡한 에러**가 있는 코드 디버깅 시 유용성이 높으며, 단위 테스트 생성기의 성능을 향상시키는 데 큰 기여를 합니다.  **다중 단위 테스트**의 사용은 과적합을 방지하고, 더욱 **강력한 디버깅**으로 이어집니다.  결론적으로, UTDEBUG 파이프라인은 혁신적인 디버깅 전략을 제시하며, **LLM 기반 코드 디버깅**의 미래를 위한 중요한 진전을 보여줍니다.

#### Debugging Metrics
디버깅 메트릭은 소프트웨어 개발에서 **중요한 측면**입니다.  효과적인 디버깅 메트릭은 개발자가 코드의 결함을 신속하고 효율적으로 식별하고 수정할 수 있도록 도와줍니다.  **버그 수정 시간**, **코드 수정 횟수**, **테스트 케이스 통과율** 등의 지표는 디버깅 프로세스의 효율성을 평가하는 데 사용될 수 있습니다.  **자동화된 테스트 생성 및 디버깅**에 대한 연구에서, 이러한 메트릭은 모델의 성능과 효율성을 객관적으로 측정하는 데 필수적입니다.  **오류 검출율**과 **정확도**는 자동화된 시스템의 성능을 평가하는 데 사용되는 주요 지표이며, 이를 통해 모델의 강점과 약점을 파악하고 개선 방향을 설정할 수 있습니다.  **다양한 디버깅 전략**의 비교 분석에도 디버깅 메트릭이 사용되는데,  메트릭을 통해 각 전략의 효율성을 비교하고 최적의 전략을 선택할 수 있습니다.  **다양한 데이터셋**에서의 성능 비교는 일반화 가능성을 평가하는 데 도움이 됩니다.  **결론적으로**, 디버깅 메트릭은 자동화된 디버깅 시스템 개발 및 평가에 있어 필수적인 요소이며,  **소프트웨어 개발의 전반적인 효율성 향상**에 기여합니다.

#### Future Work
본 논문은 **자동화된 디버깅을 위한 단위 테스트 생성**에 초점을 맞추고 있으며, 향후 연구 방향으로는 몇 가지 중요한 측면을 고려해야 합니다. 첫째, **더욱 다양하고 복잡한 코드 예시**를 포함하는 단위 테스트 생성 데이터셋을 확장하는 것이 중요합니다. 현재 사용된 데이터셋은 특정 범위의 문제만 다루고 있으므로, 다양한 프로그래밍 패러다임과 복잡성 수준을 포괄하는 더욱 포괄적인 데이터셋이 필요합니다.  둘째, **단위 테스트 생성 모델의 성능을 향상**시키기 위한 연구가 필요합니다. 특히, 오류를 유발할 가능성이 높은 입력값을 생성하고, 올바른 예상 출력값을 예측하는 모델의 능력을 향상시키는 데 집중해야 합니다.  셋째, **다양한 프로그래밍 언어**에 대한 단위 테스트 생성 모델을 개발하는 것이 필요합니다. 현재 모델은 파이썬에만 집중되어 있으므로, 다른 주요 프로그래밍 언어에 대한 지원을 확장하는 것이 중요합니다. 넷째, **단위 테스트 기반 자동화된 디버깅 파이프라인의 효율성을 개선**하는 연구가 필요합니다.  특히, 테스트 시간 계산 및 역추적 검증 전략의 효율성을 개선하여, 디버깅 시간을 단축하고 정확도를 높여야 합니다.  마지막으로, **실제 소프트웨어 개발 환경**에서 본 논문의 결과를 평가하고 검증하는 연구가 필요합니다.  실제 프로젝트에 적용하여 성능을 평가함으로써, 모델의 실용성과 한계를 파악하고 개선 방향을 모색할 수 있습니다. 이러한 후속 연구를 통해, **더욱 강력하고 효율적인 단위 테스트 생성 및 자동화된 디버깅 기술**을 개발할 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.01619/x2.png)

> 🔼 그림 2는 UTGen이라는 단위 테스트 생성기를 위한 훈련 파이프라인을 보여줍니다. 코드 생성을 위한 훈련 데이터(문제 설명과 정답 코드)로 시작하여 세 단계를 거쳐 단위 테스트 생성을 위한 훈련 데이터를 만듭니다. 1단계에서는 정답 코드를 변경하여 잘못된 코드를 생성하고, 2단계에서는 단위 테스트 입력을 생성하고 실패하는 테스트를 걸러냅니다. 마지막 3단계에서는 정답 코드의 출력을 조건으로 하여 사고 과정(chain-of-thought)에 대한 설명을 생성하고 다시 라벨링합니다. 이 그림은 UTGen의 훈련 과정을 시각적으로 보여주어, 단계별 과정을 명확하게 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: UTGen Training Pipeline: Starting with training data for code generation (problem description and gold code), we create training data for UT generation in three stages: (I) perturbing gold code to generate faulty codes, (II) generating UT inputs and filtering for failing UTs, and (III) generating and relabeling chain-of-thought rationales conditioned on the gold code’s outputs.
> </details>



![](https://arxiv.org/html/2502.01619/x3.png)

> 🔼 그림 3은 생성된 단위 테스트(UT)를 사용하여 잘못된 코드를 디버깅할 때 발생할 수 있는 잠재적 문제점과 이러한 문제를 해결하기 위해 제안하는 UTDebug 방법을 보여줍니다. 왼쪽은 (I) 잘못된 코드를 정상적인 코드로 잘못 분류하는 UT가 발생할 수 있고, (II) 잘못된 출력을 가진 UT는 잘못된 피드백을 생성하여 디버깅이 실패할 수 있다는 점을 강조합니다. 오른쪽은 이러한 고유한 과제를 처리하기 위해 제안하는 UTDebug가 (a) 다수결 투표에 따라 더 나은 UT 출력을 선택하기 위해 추론 시간 확장을 사용하고 (b) 검증 및 역추적을 위해 여러 UT를 생성하여 전체 통과율이 감소할 때는 편집을 삭제하고 전체 통과율이 향상될 때는 편집을 수락하는 방식(라운드 1과 2에서와 같이)을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Left: We highlight potential issues with debugging a faulty code using generated UTs: (I) non-failing UTs misclassify faulty code as correct; (II) UTs with incorrect outputs produce incorrect feedback and consequently, unsuccessful debugging. Right: To handle these unique challenges, we introduce UTDebug which (a) uses inference-time scaling to select better UT outputs based on a majority vote, and (b) generates multiple UTs for validation and backtracking, discarding edits when overall pass rate decreases (as in round 1) and accepting edits when overall pass rate improves (as in round 2).
> </details>



![](https://arxiv.org/html/2502.01619/x4.png)

> 🔼 그림 4는 Qwen2.5 모델을 사용하여 UTGen으로 생성된 단위 테스트와 무작위 샘플링으로 생성된 단위 테스트를 사용하여 MBPP+Fix 및 MBPP+Fix (Hard) 데이터셋에서 단위 테스트 수를 늘리는 것의 영향을 보여줍니다.  MBPP+Fix 데이터셋은 상대적으로 오류가 명확하여 디버깅이 쉬운 반면, MBPP+Fix (Hard) 데이터셋은 미묘한 오류가 포함되어 디버깅이 더 어렵습니다. 이 그림은 단위 테스트의 수가 증가함에 따라 디버깅 정확도가 어떻게 변화하는지 보여줍니다. UTGen으로 생성된 단위 테스트는 무작위 샘플링으로 생성된 단위 테스트보다 디버깅 성능이 더 우수하며, 특히 MBPP+Fix (Hard) 데이터셋에서 그 차이가 더욱 두드러집니다. 이는 UTGen이 오류를 유발할 가능성이 높은 단위 테스트를 생성하기 때문입니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Impact of increasing number of unit tests across MBPP+Fix and MBPP+Fix (Hard) datasets using UTs generated by UTGen and randomly-sampling with Qwen2.5 model.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| UT Method | Acc. | Δ |
|---|---|---|
| Randomly-sampled (Qwen2.5) | 34.77 |  |
|  - Output Test-time Scaling | 30.77 | - 4.0 |
|  - Backtracking | 32.61 | - 2.2 |
| UTGen (Qwen2.5) | 37.54 |  |
|  - Output Test-time Scaling | 26.15 | - 11.4 |
|  - Backtracking | 34.38 | - 3.2 |{{< /table-caption >}}
> 🔼 표 2는 UTGen 및 기타 기준 모델에서 생성한 단위 테스트를 사용하여 UTDebug로 디버깅한 후 3라운드에 걸쳐 HumanEval+Fix (HE+Fix), MBPP+Fix 및 MBPP+Fix (Hard)에 대한 pass@1 정확도를 평가한 결과를 보여줍니다.  각 모델과 단위 테스트 생성 방법에 따라 코드 디버깅 후의 정확도를 비교하여, UTGen 기반 단위 테스트의 효과성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Evaluating pass@1 accuracies after debugging with UTDebug, using UTs generated by UTGen and other baselines for 3 rounds, on HumanEval+Fix (HE+Fix), MPBB+Fix, and MBPP+Fix (Hard).
> </details>

{{< table-caption >}}
| Model | UT Method | HE+Fix Attack Rate | HE+Fix Out Acc. | HE+Fix Acc. ∩ Attack | MBPP+Fix Attack Rate | MBPP+Fix Out Acc. | MBPP+Fix Acc. ∩ Attack |
|---|---|---|---|---|---|---|---| 
| Llama-3 8B | Random | 89.63 | **72.97** | **72.97** | 62.56 | 41.85 | 24.28 |
|  | Prompted | 95.73 | 39.59 | 38.78 | 62.67 | 29.64 | 16.41 |
|  | UTGen | **96.34** | 53.27 | 52.04 | **67.18** | **42.67** | **26.87** |
| Llama-3.1 8B | Random | 76.02 | **63.52** | **63.52** | 47.28 | 36.0 | 21.33 |
|  | Prompted | 92.68 | 34.53 | 33.89 | 59.28 | 19.38 | 11.08 |
|  | UTGen | **96.54** | 56.38 | 55.76 | **62.77** | **43.59** | **25.54** |
| Qwen-2.5 7B | Random | 90.85 | **87.36** | **86.47** | 55.28 | **52.31** | 30.38 |
|  | Prompted | 93.29 | 54.55 | 53.91 | 62.97 | 35.29 | 22.60 |
|  | UTGen | **96.54** | 72.90 | 72.48 | **65.54** | **32.82** | **32.82** |{{< /table-caption >}}
> 🔼 이 표는 Qwen2.5 모델을 사용하여 MBPP+Fix 데이터셋에서 두 가지 유닛 테스트 생성 방법(UTGen 포함)에 대해 UTDebug 파이프라인의 구성 요소들을 제거했을 때의 결과를 보여줍니다.  구체적으로, 테스트 시간 확장(test-time scaling)과 역추적(backtracking) 기능을 각각 제거했을 때 정확도(accuracy)가 어떻게 변하는지 비교 분석합니다. 이를 통해 UTDebug 파이프라인의 각 구성요소의 중요성을 평가하고, 유닛 테스트 생성 및 디버깅 과정에서의 효율성을 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Ablating components of UTDebug’s pipeline (cf. Section 3.3) for two different unit test generation methods (including UTGen) on MBPP+Fix using Qwen2.5.
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