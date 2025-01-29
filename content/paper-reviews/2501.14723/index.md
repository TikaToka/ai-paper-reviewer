---
title: "CodeMonkeys: Scaling Test-Time Compute for Software Engineering"
summary: "CodeMonkeys: 소프트웨어 엔지니어링 문제 해결을 위해 테스트 시간 컴퓨팅을 확장하여 성능을 크게 향상시킨 시스템"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Stanford University",]
showSummary: true
date: 2025-01-24
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.14723 {{< /keyword >}}
{{< keyword icon="writer" >}} Ryan Ehrlich et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-28 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.14723" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.14723" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/codemonkeys-scaling-test-time-compute-for" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)은 소프트웨어 엔지니어링 문제를 해결하는 데 점점 더 효과적이 되고 있습니다. 하지만 모델 학습에 필요한 막대한 비용과 시간 때문에, 테스트 시간 컴퓨팅을 확장하는 것이 중요한 연구 과제로 떠오르고 있습니다. 이 논문에서는 CodeMonkeys라는 새로운 시스템을 제시하는데, 이 시스템은 GitHub 이슈를 해결하기 위해 모델이 반복적으로 코드를 수정하고 테스트하는 과정을 통해 테스트 시간 컴퓨팅을 확장합니다. 

CodeMonkeys는 병렬 및 직렬 테스트 시간 컴퓨팅 확장 전략을 결합하여 효율적인 성능 향상을 이루었습니다. 즉, 여러 개의 후보 솔루션을 생성하고 이들을 평가하여 최적의 솔루션을 선택하는 방법입니다.  **CodeMonkeys는 SWE-bench Verified 데이터셋에서 57.4%의 문제 해결률을 달성하여 기존 최고 성능을 능가**했습니다. 또한, 이 시스템은 다양한 출처의 후보 솔루션을 결합하는 새로운 선택 방법론을 제시합니다.  **이 방법론은 기존 최고 성능 모델보다 더 좋은 성능을 보여주었습니다.**

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} CodeMonkeys는 SWE-bench Verified 데이터셋에서 57.4%의 문제 해결률을 달성했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 병렬 및 직렬 테스트 시간 컴퓨팅 확장 전략을 결합하여 효율적인 성능 향상을 이루었습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 다양한 출처의 후보 솔루션들을 결합하는 새로운 선택 방법론을 제시했습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **소프트웨어 엔지니어링 문제 해결을 위한 대규모 언어 모델의 테스트 시간 컴퓨팅 확장**에 대한 중요한 통찰력을 제공합니다. 이는 현재 연구 동향과 밀접하게 관련되어 있으며, **향후 연구를 위한 새로운 방향**을 제시합니다. 특히, 병렬 및 직렬 테스트 시간 컴퓨팅 확장 전략을 결합하여 성능을 향상시킨 방법론은 다른 분야의 연구에도 적용될 수 있는 잠재력을 가지고 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.14723/x1.png)

> 🔼 그림 1은 CodeMonkeys 시스템의 개요를 보여줍니다. 왼쪽 부분은 모델을 사용하여 관련 코드베이스 파일을 식별하고 서로에 대한 순위를 매기는 방법을 보여줍니다. 중간 부분은 실행 피드백에 따라 반복되는 두 개의 멀티턴 상태 머신을 사용하여 코드베이스 편집 및 테스트 스크립트를 생성하는 방법을 보여줍니다. 이러한 상태 머신은 병렬로 여러 번 실행되어 모든 이슈에 대해 10개의 편집 및 테스트를 생성합니다. 오른쪽 부분은 생성된 테스트를 통과한 후보 편집을 식별하고 모델에게 이러한 상위 후보 간의 결정을 요청하는 방법을 보여줍니다. 시스템의 세 가지 상태 머신에 대한 자세한 내용은 그림 4를 참조하세요.
> <details>
> <summary>read the caption</summary>
> Figure 1: Overview of the CodeMonkeys system. Left: We retrieve codebase context by using models to first identify relevant files and then rank them relative to each other. Middle: We generate a codebase edit and testing script using a pair of multi-turn state machines that iterate based on execution feedback. We run these state machines multiple times in parallel to generate 10 edits and tests for every issue. Right: We select between candidate edits by identifying the candidates that pass the most generated tests and asking a model to decide between these top candidates. For details about our system’s three state machines, see Figure 4.
> </details>





{{< table-caption >}}
| Stage | Input | Output | Input Cache Read | Input Cache Write | Qwen-2.5 | USD (%) | Total Cost |
|---|---|---|---|---|---|---|---| 
| **Claude Sonnet-3.5 API Costs** |  |  |  |  |  |  |  |
| Relevance | 0.00 | 0.00 | 0.00 | 0.00 | 334.02 | 334.02 (14.6%) |  |
| Ranking | 0.00 | 11.92 | 1.10 | 6.90 | 0.00 | 19.92 (0.9%) |  |
| Gen. tests | 10.60 | 295.15 | 21.60 | 112.64 | 0.00 | 439.99 (19.2%) |  |
| Gen. edits | 14.67 | 353.95 | 636.82 | 360.58 | 0.00 | 1366.02 (59.6%) |  |
| Selection | 0.52 | 51.12 | 15.17 | 65.14 | 0.00 | 131.95 (5.8%) |  |
| **Total** | 25.79 | 712.14 | 674.69 | 545.26 | 334.02 | 2291.90 (100.0%) |  |{{< /table-caption >}}

> 🔼 표 1은 CodeMonkeys 시스템을 SWE-bench Verified 데이터셋의 모든 GitHub 이슈에 적용했을 때 발생하는 비용을 세부적으로 분석한 표입니다. 비용은 모두 미국 달러($) 단위로 표시됩니다. 시스템은 두 개의 거대 언어 모델(LLM)을 사용하는데, 주요 모델은 순위 지정, 생성, 선택 단계에 사용되며 (Claude 3.5 Sonnet API [3] 사용), 보조 모델은 코드베이스에서 관련 파일을 스캔하는 데 사용됩니다 (Qwen-2.5-Coder-32B-Instruct [24] 로컬 실행). Claude API를 사용한 비용 측정에는 1백만 개의 입력 토큰당 3달러, 1백만 개의 캐시 읽기 토큰당 0.3달러, 1백만 개의 캐시 쓰기 토큰당 3.75달러, 1백만 개의 출력 토큰당 15달러의 가격이 사용됩니다. 로컬 추론 비용 산정에 대한 자세한 내용은 부록 C를 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Table 1: Breaking down the costs of running CodeMonkeys on all GitHub issues from SWE-bench Verified. All costs are in USD. Our system uses two LLMs: a primary model used for the ranking, generation, and selection stages (we use the Claude 3.5 Sonnet API [3]), and a cheaper model used for scanning codebases to identify relevant files (we run Qwen2.5-Coder-32B-Instruct [24] locally). For measuring costs with the Claude API, we use prices of $3/million input tokens, $0.3/million cache read tokens, $3.75/million cache write tokens, and $15/million output tokens. For details about estimating local inference costs, see Appendix C.
> </details>





### In-depth insights


#### LLM Test-Time Scaling
LLM 테스트 시간 확장은 **모델 학습 후 추론 단계에서의 계산 자원 증가**를 통해 성능을 향상시키는 접근법입니다.  **직렬적 확장**은  모델이 더 오랜 시간 사고 과정을 거치도록 하여,  더욱 정교한 답변을 생성하는 방식입니다. 반면 **병렬적 확장**은 여러 후보 솔루션을 동시에 생성하고 평가하여 최적의 결과를 선택하는 방식입니다. 본 논문에서는  SWE-bench 데이터셋을 활용, 코드 수정 문제 해결에  CodeMonkeys 시스템을 적용하여 두 가지 확장 방식을 실험적으로 비교 분석합니다.  **직렬적 확장**의 경우 반복적인 테스트와 수정을 통해  정확성을 높였고, **병렬적 확장**은 여러 후보군을 생성하여  더 높은 문제 해결률을 달성했습니다.  **특히,  모델이 생성한 테스트를 활용한 투표 방식과 추가적인 모델 기반 선택 과정을 결합**하여 효율적인 후보 선택을 수행한 점이 핵심입니다.  결과적으로,  CodeMonkeys는 상당한 비용을 들이면서도 높은 정확도를 달성하여,  LLM 테스트 시간 확장의 효과를 보여주었습니다.

#### CodeMonkey System
CodeMonkey 시스템은 **LLM의 테스트 시간 연산을 확장하여 소프트웨어 엔지니어링 문제 해결 능력을 향상**시키는 시스템입니다. 이 시스템은 모델이 테스트 스크립트와 함께 코드베이스를 반복적으로 수정하여 후보 코드 편집을 생성하는 방식을 채택합니다. 이는 **직렬 연산과 병렬 연산 모두를 확장**하여 다양한 문제에 대한 다양한 솔루션을 생성할 수 있게 해줍니다. 또한, 모델이 생성한 테스트를 이용한 투표와 최종 선택을 위한 다중 턴 트래젝토리를 결합하여 후보 코드 편집을 선택하는 방식을 통해 **정확도를 높입니다**.  CodeMonkey는 SWE-bench 데이터셋에서 상당한 성능 향상을 보이며, 특히 다른 소스의 후보들을 결합하는 데 효과적임을 보여줍니다.  **테스트 시간 연산 확장**은 LLM의 능력 향상에 있어 중요한 방향이며, CodeMonkey는 이 방향에 대한 심도있는 연구결과를 제시합니다. 하지만 여전히 개선의 여지가 있는데, 관련 코드베이스 맥락 식별, 후보 편집 및 테스트 생성, 최종 편집 선택 등의 세부적인 부분에서 더욱 발전된 연구가 필요합니다.  **전반적으로 CodeMonkey 시스템은 LLM 기반 소프트웨어 엔지니어링의 효율성과 정확성 향상에 크게 기여**할 수 있는 잠재력을 보여주는 혁신적인 시스템입니다.

#### Serial/Parallel Scaling
본 논문에서 제시된 코드몽키(CodeMonkeys) 시스템은 소프트웨어 엔지니어링 문제 해결을 위해 **직렬(serial) 및 병렬(parallel) 테스트 시간 계산(test-time compute)**을 확장하는 접근 방식을 제시합니다. 직렬 확장은 모델이 최종 답변을 출력하기 전에 더 오래 고민하도록 함으로써 이루어집니다. 이는 여러 토큰의 계산을 사용하여 문제를 해결하거나, 모델이 코드 실행 결과와 같은 외부 피드백에 반복적으로 반응하는 다중 턴 상호 작용을 통해 구현될 수 있습니다. 병렬 확장은 문제에 대한 여러 후보 솔루션을 샘플링하여 수행됩니다. 코드몽키는 다중 턴 상태 머신을 사용하여 코드베이스 편집과 테스트 스크립트를 생성하고, 각 이슈에 대해 여러 개의 후보 편집을 생성하여 병렬 테스트 시간 계산을 확장합니다. 또한, 모델이 모든 파일을 읽도록 함으로써 다운스트림 샘플 전반에 걸쳐 선행 비용을 상쇄하고, 후보 편집 간에 투표를 통해 최종 편집을 선택합니다. 이러한 접근 방식은 직렬 및 병렬 확장을 효과적으로 결합하여 SWE-bench Verified의 57.4% 문제를 해결합니다.  **병렬 샘플링을 통한 범위 확장의 효과**와 **직렬 계산 확장을 위한 반복적 테스트와 수정 과정의 중요성**을 강조하는 결과는 **테스트 시간 계산 확장의 다양한 전략**을 이해하는 데 중요한 통찰력을 제공합니다.

#### Selection Strategies
본 논문에서 제시된 다양한 선택 전략들은 코드 수정 제안들을 효과적으로 평가하고 최적의 후보를 선택하는 데 중점을 둡니다. **다수결 투표 전략**은 생성된 테스트를 기반으로 가장 많은 테스트를 통과한 수정을 선택하며, **모델 기반 선택 전략**은 모델에게 수정 후보들을 제시하여 최적의 후보를 결정하게 합니다. **상위 3개 필터링 후 모델 선택 전략**은 다수결 투표를 통해 상위 3개의 후보를 선별한 후, 모델 기반 선택을 적용하여 정확성을 높이고자 합니다.  **상위 3개 필터링 후 상태 머신 기반 선택 전략**은 다수결 투표로 선별된 상위 3개의 후보에 대해, 모델이 추가 테스트를 생성하고 실행하며 반복적으로 최적의 후보를 선택하는 정교한 방법입니다. 이러한 다양한 전략 비교를 통해, **상태 머신 기반 전략이 가장 높은 정확도**를 보이는 것을 확인할 수 있었습니다.  각 전략의 성능과 비용을 고려하여, **최적의 선택 전략을 선택**하는 것은 실제 문제 해결에 중요한 부분입니다.

#### Future Work
논문의 "향후 연구" 부분에서 제시된 아이디어들은 **시스템의 세 가지 주요 하위 작업(컨텍스트, 생성, 선택) 각각의 성능 향상**에 초점을 맞추고 있습니다.  **컨텍스트 단계**에서는 더욱 효율적인 파일 필터링 및 순위 지정 기법을 통해 관련 없는 파일을 제거하고 정확도를 높이는 데 집중할 수 있습니다.  **생성 단계**에서는 모델이 테스트 스크립트를 작성하고 수정하는 과정을 개선하여 더욱 정확하고 효율적인 코드 수정을 생성하는 방향으로 연구를 진행할 수 있습니다.  마지막으로 **선택 단계**에서는 후보 코드 수정들 중 최적의 수정을 선택하는 정확도를 높이는 데 집중하여 전체 시스템 성능을 향상시키는 데 기여할 수 있습니다.  **다양한 모델을 결합하거나, 특정 추론 모델을 활용하는 등의 추가적인 접근 방식**을 통해 테스트 시간 계산을 확장하는 방안도 고려해 볼 수 있습니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.14723/extracted/6154717/figures/problem_resolution_flow.png)

> 🔼 그림 2는 논문의 2절에서 설명하는 세 가지 하위 작업(컨텍스트, 생성, 선택)에 걸쳐 CodeMonkeys의 성능을 측정한 것입니다. 각 하위 작업의 성능은 다른 작업의 성능에 영향을 줄 수 있습니다. 예를 들어, 후보 코드 수정본을 더 많이 생성하면 적중률은 높아지지만 선택 작업이 더 어려워질 수 있습니다. 그림은 각 하위 작업의 성공률을 시각적으로 보여주고, CodeMonkeys 시스템의 전반적인 성능을 평가하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Measuring CodeMonkeys performance across the three subtasks we identify in Section 2 (context, generation, and selection). Note that modifying the approach to one subtask can influence the performance on other subtasks as well. For example, generating more candidate edits could increase coverage but make selection harder.
> </details>



![](https://arxiv.org/html/2501.14723/extracted/6154717/figures/context_recall.png)

> 🔼 그림 3은 두 개의 그래프로 구성되어 있습니다. 왼쪽 그래프는 문맥 창 크기 제한을 늘릴 때 재현율(필요한 모든 파일을 포함하는 문맥 창이 있는 SWE-bench 문제의 비율)을 측정한 결과를 보여줍니다. 나중 실험에서 사용한 128k 토큰 제한을 사용하면 인스턴스의 92.6%가 올바른 파일을 문맥에 포함하고 있습니다. 오른쪽 그래프는 SWE-bench 문제에 걸쳐 문맥 압축 계수의 분포를 시각화한 것입니다. 즉, 관련성 모델에 의해 스캔된 파일의 누적 토큰 수와 관련성 및 순위 지정 후 포함된 파일의 누적 토큰 수 간의 비율입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Left: Measuring recall (the fraction of SWE-bench problems with context windows that contain all needed files) as we increase the context window size limit. With the 128k token limit that we use for later experiments, 92.6% of instances have the correct files in context. Right: Visualizing the distribution of context compression factors across SWE-bench problems, i.e. the ratio between the cumulative token count of files scanned by the relevance model and the cumulative token count of files we include after relevance + ranking.
> </details>



![](https://arxiv.org/html/2501.14723/x2.png)

> 🔼 그림 4는 CodeMonkeys 시스템의 세 가지 상태 머신(테스트, 편집, 선택)의 상세 내용을 보여줍니다. 테스트 상태 머신은 코드 수정 전에 테스트를 실행하여 얻은 실행 피드백을 기반으로 테스트 스크립트의 초기 초안을 반복적으로 생성합니다. 편집 상태 머신은 코드베이스 컨텍스트와 테스트 상태 머신의 출력 테스트를 조건으로 초기 수정을 생성한 다음, 수정 전후 테스트를 실행하여 얻은 실행 피드백을 기반으로 테스트와 수정 초안을 모두 다듬습니다. 선택 상태 머신은 가장 많은 테스트 스크립트를 통과한 상위 3개의 후보 수정을 구분하기 위한 테스트를 먼저 생성합니다. 그런 다음, 이 테스트를 모든 후보 수정과 수정되지 않은 코드베이스에서 실행하여 얻은 실행 피드백을 기반으로, 수정을 더 구분하기 위한 새로운 테스트 스크립트를 생성하거나 최종 수정을 선택합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Details of the CodeMonkeys state machines. The Testing State Machine iteratively generates an initial draft of a testing script based on execution feedback from running the test on the codebase before any edits are applied. The Editing State Machine first generates an initial edit conditioned on the codebase context and the output test of the Testing State Machine. Then, it refines both the test and edit draft based on execution feedback from running the test before and after the edit is applied. The Selection State Machine first generates a test to distinguish between the top 3 candidate edits that pass the most testing scripts. Then, based on execution feedback of running this test with all of the candidate edits and on the codebase without edits, chooses to either create a new test script to further differentiate between the edits or selects a final edit.
> </details>



![](https://arxiv.org/html/2501.14723/x3.png)

> 🔼 그림 5는 편집 상태 머신당 직렬 반복 횟수와 문제당 병렬 상태 머신 수를 변경하면서 다수결 투표 선택을 사용할 때의 적용범위(왼쪽)와 점수(오른쪽)를 측정한 결과를 보여줍니다. 각 색상 곡선은 서로 다른 수의 병렬 상태 머신에 해당하며, 곡선 위의 점은 상태 머신당 직렬 반복 횟수의 증가에 해당합니다. 처음 몇 번의 직렬 반복은 성능 향상에 큰 영향을 미치지만, 그 이후에는 비슷한 비용을 가진 서로 다른 구성에서도 특히 적용 범위 측면에서 비슷한 성능을 보입니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Measuring coverage (left) and score when using majority-voting selection (right) as we sweep over the number of serial iterations per editing state machine and the number of parallel state machines sampled per problem. Each colored curve corresponds to a different number of parallel state machines, and the dots along each curve correspond to increased numbers of sequential iterations per state machine. The first few serial iterations have a large impact on improving performance. However, past that point, different configurations with similar costs lead to similar performance, particularly for coverage.
> </details>



![](https://arxiv.org/html/2501.14723/x4.png)

> 🔼 그림 6은 CodeMonkeys 편집 상태 머신에 의해 생성된 후보 편집본에 적용된 선택 방법들을 비교한 것입니다. 생성된 테스트를 사용하여 상위 3개 필터링 후 선택 상태 머신을 사용한 방법이 가장 우수한 성능을 보였습니다. 이 방법은 무작위 선택의 최저 성능과 오라클 선택의 최고 성능(즉, 적용 범위) 사이의 차이를 약 절반 정도 회복합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Comparing our selection methods when applied to the candidate edits generated by the CodeMonkeys editing state machines. Our best performing selection method – the selection state machine after top-3 filtering with generated tests – recovers approximately half of the difference between the random selection floor and the oracle selection ceiling (i.e. coverage).
> </details>



![](https://arxiv.org/html/2501.14723/x5.png)

> 🔼 그림 7은 Claude와 DeepSeek-V3 모델을 사용하여 병렬 샘플 수와 순차 반복 횟수를 조정했을 때 다수결 투표 점수에 미치는 영향을 비교 분석한 결과를 보여줍니다. 왼쪽 그래프는 고정된 샘플 수에 대해 순차 반복 횟수를 다르게 했을 때의 결과를 보여주며, Claude 모델이 더 높은 점수를 달성하지만 DeepSeek-V3 모델도 Claude 모델 점수의 86.8%에 달하는 성능을 훨씬 적은 비용으로 달성함을 보여줍니다. 가운데 그래프는 DeepSeek-V3 모델의 다수결 투표 점수 확장에 대한 자세한 분석을 제공하며, 오른쪽 그래프는 병렬 샘플 수와 순차 반복 횟수에 따른 DeepSeek-V3 모델의 적용 범위를 보여줍니다. 이를 통해 추론 계산을 늘리면 적용 범위가 계속 확장됨을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Left: Comparing the impact of scaling the number of parallel samples and sequential iterations on majority voting score between Claude and DeepSeek-V3. Each line corresponds to a fixed amount of samples, with each dot on the line being a different maximum number of sequential iterations. We see that although Claude can achieve a higher overall score, DeepSeek-V3 can achieve 86.8%percent86.886.8\%86.8 % percent of the score at a fraction of the cost. Center: A more granular view of the majority voting scaling for DeepSeek-V3. Right: Coverage for DeepSeek-V3 as a function of the number of parallel samples and sequential iterations. We highlight that coverage is continuing to scale with increased inference compute.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | Score |
|---|---| 
| Barrel of Monkeys (Oracle Selection) | 80.8 |
| o3 | 71.7 |
| CodeMonkeys (Oracle Selection) | 69.8 |
| Barrel of Monkeys | 66.2 |
| Blackbox AI Agent | 62.8 |
| CodeStory | 62.2 |
| Learn-by-interact | 60.2 |
| devlo | 58.2 |
| CodeMonkeys | 57.4 |
| Emergent E1 | 57.2 |
| Gru | 57.0 |{{< /table-caption >}}
> 🔼 표 2는 본 논문에서 제시된 방법(굵은 글씨체)과 기존 최고 성능 방법들을 비교하여 최종 SWE-bench Verified 점수를 보여줍니다. Barrel of Monkeys 결과는 SWE-bench Verified 리더보드에 있는 기존 제출물의 생성 결과에 의존하며, 오라클 선택 방법은 적용 범위를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Comparing final SWE-bench Verified scores between the methods explored in this paper (bolded) and existing top approaches. Note that the Barrel of Monkeys results rely on the generations from existing submissions on the SWE-bench Verified leaderboard, and oracle selection methods are coverage numbers.
> </details>

{{< table-caption >}}
| **Testing State Machine** | **Editing State Machine** | **Selection State Machine** |
|---|---|---|
| **Information in Initial Prompt** | GitHub issue description. | GitHub issue description, codebase context, final test script from a testing state machine, execution output when running the provided test on the unedited codebase. | GitHub issue description, candidate edits in git diff form, full contents of any codebase files that have been edited, test script from the edit that passed the most generated tests (breaking ties by using the shortest edit). |
| **Initial Task** | Write a test script that reproduces the issue. The script should exit with code 0 if the issue is fixed and exit with code 2 if the issue is not fixed. | Write a codebase edit that resolves the issue. | Write a test script for distinguishing between candidates and assessing their correctness. |
| **Information in Iteration Prompt** | Execution output when running the test on the codebase (which has not yet been edited). | Execution outputs when running the testing script on the unedited codebase and edited codebase. | Execution outputs when running the test script on a codebase after each edit has been applied, in addition to the unedited codebase. |
| **Iteration Task** | Rewrite the test script or approve of it (terminating the state machine). | Rewrite the edit, rewrite the test script, or approve of the (edit, test) pairs (terminating the state machine). | Write a new testing script, or make a selection among the candidate edits (terminating the state machine). |{{< /table-caption >}}
> 🔼 이 표는 CodeMonkeys 시스템의 세 가지 상태 머신(테스트, 편집, 선택)에 대한 자세한 내용을 보여줍니다. 각 머신의 초기 프롬프트, 초기 작업, 각 반복에서 제공되는 정보, 각 반복의 작업을 설명합니다. 테스트 상태 머신은 문제를 재현하는 테스트 스크립트를 작성하고, 편집 상태 머신은 문제를 해결하는 코드베이스 편집을 작성하며, 선택 상태 머신은 후보 편집을 구분하고 정확성을 평가하기 위한 테스트 스크립트를 작성합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Details of the Testing, Editing, and Selection State Machines.
> </details>

{{< table-caption >}}
| Subtask | Stage | Parameter | Value |
|---|---|---|---| 
| **Context** | Relevance | Model | Qwen-2.5-Coder-32B-Instruct |
|  |  | Hardware | 8xL40S |
|  |  | Temperature | 0.0 |
|  | Ranking | Model | Claude Sonnet 3.5 |
|  |  | Temperature | 0.0 |
|  |  | Repetitions | 3 |
| **Generation** | Testing & Editing | Temperature (Sonnet 3.5) | 0.5 |
|  |  | Temperature (DeepSeek-V3) | 0.6 |
|  |  | Number of State Machines per Instance | 10 |
|  |  | Maximum Iterations | 8 |
|  |  | Generated Test Timeout (seconds) | 100 |
| **Selection** | — | Temperature | 0.0 |
|  |  | Maximum Iterations | 10 |
|  |  | Generated Test Timeout (seconds) | 100 |{{< /table-caption >}}
> 🔼 표 4는 CodeMonkeys 시스템의 하이퍼파라미터 설정을 요약하여 보여줍니다.  각 하이퍼파라미터는 시스템의 세 가지 주요 단계(Context, Generation, Selection)와 각 단계의 하위 단계에 따라 나뉘어져 있습니다.  각 하이퍼파라미터의 값과 사용된 모델 (예: Claude Sonnet 3.5, Qwen-2.5-Coder-32B-Instruct)도 함께 제시되어 있어 CodeMonkeys 시스템의 구현 세부 사항을 이해하는 데 도움이 됩니다.  특히, 온도(Temperature), 반복 횟수(Repetitions), 상태 머신 수(Number of State Machines), 최대 반복 횟수(Maximum Iterations), 제한 시간(Timeout)과 같은 하이퍼파라미터는 모델의 성능에 큰 영향을 미치므로, 이 표를 통해 CodeMonkeys 시스템의 성능 조정에 대한 통찰력을 얻을 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: CodeMonkeys hyperparameter summary.
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