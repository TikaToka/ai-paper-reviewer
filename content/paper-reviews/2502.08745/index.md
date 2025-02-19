---
title: "IHEval: Evaluating Language Models on Following the Instruction Hierarchy"
summary: "IHEval: 언어 모델의 명령어 계층 구조 준수 능력 평가 벤치마크 제시! 상충되는 명령어 처리에 어려움을 겪는 오픈소스 모델의 취약점을 밝히고, 안전하고 신뢰할 수 있는 언어 모델 개발의 새로운 방향 제시!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Amazon",]
showSummary: true
date: 2025-02-12
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.08745 {{< /keyword >}}
{{< keyword icon="writer" >}} Zhihan Zhang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-18 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.08745" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.08745" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/iheval-evaluating-language-models-on" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

많은 응용 분야에서 상호작용 서비스로 사용되는 **지시어 학습 언어 모델(LLM)**은 일관된 성능과 안전성을 위해 **명령어 계층 구조**를 따라야 합니다. 하지만, 현재 LLM은 시스템 메시지, 사용자 메시지, 대화 기록, 도구 출력 등의 우선순위를 인식하는 데 어려움을 겪고 있으며, 특히 상충되는 지시어가 있을 때 성능이 크게 저하됩니다.  기존 연구는 이러한 문제를 포괄적으로 다루지 못하고 있습니다.

본 논문에서는 이러한 문제를 해결하기 위해 **새로운 벤치마크인 IHEval**을 제시합니다. IHEval은 다양한 시나리오와 작업을 포함하여 LLM의 명령어 계층 구조 준수 능력을 포괄적으로 평가합니다. 실험 결과, 평가된 모든 모델이 상충되는 지시어에 대해 성능 저하를 보였으며, 경쟁력 있는 오픈소스 모델도 50% 미만의 정확도를 보였습니다.  본 연구는 향후 LLM 개발에 있어 **명령어 계층 구조 최적화**의 필요성을 강조하고, **안전하고 신뢰할 수 있는 LLM 개발**에 중요한 기여를 합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} IHEval이라는 새로운 벤치마크를 통해 언어 모델의 명령어 계층 구조 준수 능력을 평가할 수 있음 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 상충되는 명령어가 있을 때 오픈소스 모델의 성능이 크게 저하됨을 확인 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 안전하고 신뢰할 수 있는 언어 모델 개발을 위해 명령어 계층 구조 처리 최적화가 필요함을 강조 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **명령어 계층 구조**를 따르는 언어 모델의 능력을 평가하는 새로운 벤치마크인 IHEval을 제시하여, **실제 환경에서의 안전성과 일관성을 보장하는 데 중요한 영향**을 미칩니다.  **오픈소스 모델의 성능 저하 문제**를 보여주고 향후 연구 방향을 제시함으로써, **안전하고 신뢰할 수 있는 언어 모델 개발에 크게 기여**할 것으로 예상됩니다.  본 연구는 현재 언어 모델 연구의 주요한 트렌드인 **안전성 및 신뢰성 확보**와 밀접하게 연관되어 있으며, 향후 연구에서 **계층적 명령어 처리 최적화**에 대한 심도 있는 연구를 촉진할 것으로 기대됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.08745/x1.png)

> 🔼 본 그림은 논문의 Instruction Hierarchy(명령어 계층 구조)에 대한 4가지 범주와 각 명령어의 우선순위를 보여줍니다.  계층 구조는 시스템 메시지, 사용자 메시지, 대화 이력, 도구 출력 순으로 우선순위가 매겨집니다.  빨간색으로 표시된 부분은 상충되는 명령어를 나타냅니다. 모델은 상위 우선순위의 명령어를 따라야 합니다.  즉, 시스템 메시지가 사용자 메시지보다, 사용자 메시지가 대화 이력보다, 대화 이력이 도구 출력보다 우선 순위가 높다는 것을 보여줍니다.  만약 상충되는 지시사항이 있다면, 모델은 가장 높은 우선순위의 지시사항을 따라야 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Four categories of the instruction hierarchy and the corresponding priority orders of instructions. Conflict instructions are shown in red. Models are expected to follow the instruction with the higher priority.
> </details>





{{< table-caption >}}
| Model | Setting | Single. | Multi. | Ext. | Gen. | Class. | Hijack | Extract | Intrinsic | Injected | Mean | Abs. | Δ | 
|---|---|---|---|---|---|---|---|---|---|---|---|---|---| 
|  | reference | 89.0 | 86.5 | 90.0 | 78.0 | 100 | 99.5 | 100 | 90.2 | 94.0 | 91.9 | - |  | 
|  | aligned | 85.6 | 86.8 | 87.3 | 73.9 | 100 | 99.2 | 98.7 | 88.6 | 99.0 | 91.0 | -0.9 | 2.1 | 
| GPT-4o (2024-0806) | conflict | 49.5 | 51.0 | 77.2 | 38.3 | 99.7 | 91.2 | 96.7 | 63.8 | 62.5 | 70.0 | -21.9 | 21.9 | 
|  | reference | 84.5 | 86.1 | 90.5 | 78.4 | 99.6 | 99.1 | 99.4 | 89.3 | 79.0 | 89.6 | - |  | 
|  | aligned | 82.3 | 80.2 | 84.0 | 72.0 | 100 | 98.6 | 98.7 | 82.7 | 59.0 | 84.2 | -5.4 | 5.5 | 
| GPT-4o mini (2024-0718) | conflict | 33.9 | 35.7 | 47.7 | 31.1 | 41.1 | 70.3 | 95.5 | 43.6 | 0 | 44.3 | -45.2 | 45.2 | 
|  | reference | 80.9 | 83.9 | 84.9 | 76.9 | 100 | 87.1 | 85.5 | 87.1 | 87.0 | 85.9 | - |  | 
|  | aligned | 68.4 | 69.5 | 77.4 | 79.8 | 100 | 97.6 | 97.2 | 85.3 | 91.0 | 85.1 | -0.8 | 7.2 | 
| Claude-3 Sonnet | conflict | 10.8 | 21.1 | 2.3 | 29.7 | 9.8 | 46.6 | 60.1 | 56.9 | 39.0 | 30.7 | -55.2 | 55.2 | 
|  | reference | 88.3 | 88.4 | 89.1 | 77.0 | 100 | 99.3 | 99.7 | 89.0 | 100 | 92.3 | - |  | 
|  | aligned | 82.9 | 76.6 | 84.3 | 59.5 | 100 | 95.8 | 96.2 | 20.3 | 94.0 | 78.8 | -13.5 | 13.5 | 
| LLaMA-3.1 70B | conflict | 14.3 | 24.3 | 0 | 15.2 | 6.2 | 24.4 | 25.2 | 2.2 | 14.0 | 14.0 | -78.3 | 78.3 | 
|  | reference | 83.6 | 85.2 | 85.2 | 78.5 | 100 | 99.2 | 98.4 | 88.3 | 69.0 | 87.5 | - |  | 
|  | aligned | 81.7 | 87.1 | 76.0 | 78.3 | 100 | 97.7 | 99.1 | 77.9 | 79.0 | 86.3 | -1.2 | 4.0 | 
| Mistral-Large (2407) | conflict | 25.2 | 60.0 | 11.0 | 20.2 | 78.4 | 23.9 | 18.8 | 13.9 | 13.5 | 29.4 | -58.1 | 58.1 | 
|  | reference | 81.4 | 85.0 | 74.9 | 75.0 | 100 | 97.6 | 98.4 | 83.9 | 92.0 | 87.6 | - |  | 
|  | aligned | 82.1 | 81.3 | 73.4 | 75.3 | 100 | 97.5 | 97.8 | 77.6 | 86.0 | 85.7 | -1.9 | 2.1 | 
| Qwen-2 72B | conflict | 35.8 | 39.5 | 53.7 | 58.4 | 99.5 | 36.8 | 34.7 | 26.2 | 46.0 | 47.8 | -39.7 | 39.7 | {{< /table-caption >}}

> 🔼 표 1은 IHEval 벤치마크에서 주요 대규모 언어 모델(LLM)들의 성능을 보여줍니다.  전체 결과는 표 5~10에 나와 있습니다.  Δ 열은 기준 설정(단일 입력)과의 점수 차이를 나타내며, 평균 차이(부호 포함)와 평균 절대 차이를 모두 포함합니다.  빨간색 점수는 절대 점수 차이가 5보다 큰 경우를 나타냅니다.  규칙 준수 범주에서는 단일 턴과 다중 턴 작업을 구분하고, 작업 실행 범주에서는 추출, 생성, 분류 작업을 구분합니다.  충돌 설정에서 가장 좋은 성능은 굵게 표시하고, 두 번째로 좋은 성능은 밑줄을 쳤습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Results of select LMs on IHEval. Full results are in Tables 5~10. ΔΔ\Deltaroman_Δ is the score difference from the reference setting, including both the mean difference (signed) and the mean absolute difference. Red scores indicate |Δ|>5Δ5|\Delta|>5| roman_Δ | > 5. Single. and Multi. refer to single-turn and multi-turn tasks in the Rule Following category. Ext., Gen., and Class. refer to extraction, generation, and classification tasks in Task Execution. The best performance in the conflict setting is marked as bold and the second-best is underlined.
> </details>





### In-depth insights


#### Instruction Hierarchy
본 논문에서 다룬 'Instruction Hierarchy'는 언어 모델이 다양한 종류의 지시사항(시스템 메시지, 사용자 메시지, 대화 이력, 도구 출력 등)을 처리할 때 **우선순위**를 정하는 체계를 의미합니다.  **상위 지시사항이 하위 지시사항보다 우선**되어야 함을 강조하며, 이를 따르지 못할 때 발생하는 모델의 오류나 안전 문제를 지적합니다.  이는 실제 서비스 환경에서 사용자의 예상치 못한 입력이나 도구의 오작동으로 인해 **높은 수준의 지시가 낮은 수준의 지시에 덮어씌워지는 문제**를 해결하기 위한 중요한 개념입니다.  **모델이 이러한 계층 구조를 얼마나 잘 따르는지 평가하기 위한 벤치마크** IHEval을 제시하고, 여러 모델의 평가 결과를 통해  **대부분의 모델이 상충하는 지시사항을 제대로 처리하지 못함**을 보여줍니다.  특히, 오픈소스 모델의 경우 성능 저하가 더욱 심각하며,  향후 언어 모델 개발에서 **계층적 지시 처리 능력 향상**이 중요한 과제임을 시사합니다.

#### IHEval Benchmark
IHEval 벤치마크는 **계층적 지시사항 따르기** 능력을 평가하기 위해 고안된 종합적인 벤치마크입니다.  다양한 시나리오(규칙 준수, 작업 실행, 안전 방어, 도구 사용)와 다양한 입력 유형(시스템 메시지, 사용자 메시지, 대화 내역, 도구 출력)을 포함하여 **실제 사용 환경을 반영**합니다.  **상호 모순되는 지시사항**이 존재하는 경우 모델이 상위 지시사항을 우선시하는지 평가하며, 이를 통해 모델의 안전성과 일관성을 측정합니다.  **다양한 난이도**의 작업을 포함하여 모델의 능력을 포괄적으로 평가하고, 프로그래밍 방식으로 평가하여 효율성과 재현성을 확보합니다.  IHEval은 기존 벤치마크의 한계를 극복하고, **LM의 계층적 지시사항 처리 능력**에 대한 심층적인 이해를 제공하여 향후 LM 개발에 중요한 역할을 할 것으로 기대됩니다.  특히, 오픈소스 모델의 성능 저하 문제를 보여주는 등, **실제 적용 시 발생할 수 있는 위험성**을 강조합니다.

#### LM Limitations
본 논문에서 언급된 것처럼, 대규모 언어 모델(LLM)은 명령어 계층 구조를 따르는 데 어려움을 겪습니다. **특히 상위 수준의 지침과 하위 수준의 입력이 충돌하는 경우 성능이 크게 저하됩니다.** 이는 모델이 다양한 입력의 우선순위를 인식하고 충돌하는 지침을 해결하는 데 어려움을 겪고 있음을 시사합니다.  **오픈 소스 모델은 이러한 충돌을 해결하는 데 50% 미만의 정확도를 보이며, 이는 향후 LLM 개발에서 이 문제를 해결하기 위한 노력이 필요함을 강조합니다.**  또한, 모델의 성능은 지침의 엄격성과 같은 피상적인 요소의 영향을 받기 쉽고, 모델 크기가 커진다고 해서 이러한 문제가 효과적으로 해결되지 않음을 보여줍니다. 따라서 **LLM의 안전성 및 일관성을 보장하기 위해서는 명령어 계층 구조를 따르는 능력 향상을 위한 표적화된 최적화가 필수적입니다.** 이러한 한계는 실제 응용 프로그램에서 심각한 위험을 초래할 수 있으며, **향후 연구를 통해 명령어 계층 구조를 더 잘 따르도록 모델을 훈련하는 방법을 개발해야 합니다.**

#### Conflict Resolution
연구 논문의 '갈등 해결' 부분에 대한 심층적인 분석을 통해 얻을 수 있는 통찰력은 다음과 같습니다. **자연어 모델(LLM)이 상충되는 지시사항을 처리하는 능력**은 아직 미흡하며, 이는 모델의 안전성 및 신뢰성에 심각한 위협이 될 수 있습니다.  **계층적 지시사항의 우선순위를 인식하고, 상위 지시사항에 따라 하위 지시사항을 적절히 무시하는 능력**이 중요하며, 이를 평가하는 벤치마크가 필요합니다.  본 논문은 이러한 문제를 해결하기 위한 **새로운 평가 기준 및 벤치마크(IHEval)**를 제시하고 있으며, 다양한 시나리오와 상황을 고려하여 모델의 갈등 해결 능력을 포괄적으로 평가합니다. **오픈소스 모델의 성능은 기대치에 미치지 못하며**, 특히 상충되는 지시사항이 존재하는 경우 성능 저하가 뚜렷합니다. 따라서,  **향후 LLM 개발에 있어 계층적 지시사항 처리 능력 향상을 위한 집중적인 노력**이 필요함을 시사합니다.  **모델 크기가 커질수록 성능이 향상**되지만, 갈등 해결 능력의 향상은 모델 크기에 비례하지 않으므로, **모델 설계 및 훈련 과정에 대한 개선**이 요구됩니다.  **프롬프트 엔지니어링을 통한 해결책 모색**도 시도되었지만, 그 효과는 제한적임을 보여줍니다.

#### Future Directions
본 논문은 언어 모델의 지시 사항 계층 구조 준수 능력을 평가하기 위한 새로운 벤치마크인 IHEval을 제시합니다. **미래 방향으로는 IHEval을 더욱 확장하여 다양한 작업과 시나리오를 포함하고, 다양한 유형의 지시 사항 충돌을 다루는 모델의 능력을 더욱 정교하게 평가하는 것을 고려할 수 있습니다.** 또한, IHEval에서 확인된 모델의 약점을 해결하기 위한 **표적 최적화 기법 개발**이 중요하며, **계층적 지시 사항을 효과적으로 처리할 수 있는 새로운 모델 아키텍처 연구**도 필요합니다.  **프롬프트 엔지니어링 기법을 활용하여 모델의 계층적 지시 사항 준수 능력을 개선**하는 방안도 탐구할 수 있으며, 이를 통해 더 안전하고 신뢰할 수 있는 언어 모델 개발에 기여할 수 있을 것입니다.  **모델의 규모와 계층적 지시 사항 처리 능력 간의 상관관계에 대한 심층적인 분석**도 필요합니다.  마지막으로, **다양한 분야에서 언어 모델의 안전성과 신뢰성을 높이는 데 IHEval을 적용**하고,  실제 애플리케이션 환경에서의 성능을 평가하는 추가 연구가 필요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.08745/x2.png)

> 🔼 그림 2는 주요 대규모 언어 모델(LLM)들이 IHEval 벤치마크에서 보여준 성능을 나타냅니다.  'Reference' 설정은 계층적 입력 없이 모델의 원래 작업 수행 능력을 보여줍니다.  이와 달리 계층적 입력이 충돌하는 경우 모델의 성능이 크게 저하되는 것을 확인할 수 있습니다.  즉, 상위 레벨의 지시사항과 하위 레벨의 지시사항이 서로 상충될 때 모델의 정확도가 급격히 감소함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Results of mainstream LMs on IHEval. The reference setting represents original task performance without hierarchical inputs. We observe large performance drops when models face conflicting hierarchical instructions.
> </details>



![](https://arxiv.org/html/2502.08745/x3.png)

> 🔼 IHEval 평가 벤치마크는 규칙 준수, 작업 실행, 안전 방어 및 도구 사용이라는 네 가지 범주에 걸쳐 총 9가지 작업으로 구성되어 있습니다. 각 범주 내의 작업은 다양한 어려움의 계층적 입력을 포함하며, 여기에는 저수준 입력이 고수준 규칙과 일치하거나 충돌하는 경우가 포함됩니다. 그림 8-16에서는 각 작업에 대한 자세한 예시와 지침을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: IHEval covers four categories and nine tasks. Detailed examples and instructions are in Figures 8~16.
> </details>



![](https://arxiv.org/html/2502.08745/x4.png)

> 🔼 그림 4는 IHEval 벤치마크에 사용된 9가지 과제에 대한 데이터 출처, 평가 지표 및 데이터 크기를 보여줍니다. 각 과제는 특정 자연어 처리 작업(규칙 준수, 작업 실행, 안전 방어, 도구 사용)을 다루며, 다양한 데이터 세트와 평가 지표를 사용합니다. 예를 들어, 규칙 준수 과제에는 IFEval 데이터 세트의 하위 집합을 사용하여 모델의 형식 준수 능력을 평가하고, 작업 실행 과제는 다양한 NLP 데이터 세트를 사용하여 추출, 생성, 분류 작업의 성능을 측정합니다. 안전 방어 과제는 TensorTrust 데이터 세트를 기반으로 모델의 안전성을 평가하며, 도구 사용 과제는 사용자의 질의에 응답하기 위해 도구를 호출하는 모델의 기능을 평가합니다. 각 과제의 데이터 크기는 데이터 세트와 작업의 복잡성을 반영합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: The original data source, the evaluation metric, and the data size of each task.
> </details>



![](https://arxiv.org/html/2502.08745/x5.png)

> 🔼 그림 5는 모델 규모에 따른 IHEval 성능 추세를 보여줍니다.  세 가지 설정(기준, 정렬, 충돌)에서 다양한 크기의 주요 모델들의 성능을 비교하여 모델 크기가 커짐에 따라 IHEval 성능이 향상되는 경향을 보여줍니다. 특히, 정렬된 입력에 대한 성능은 기준 성능에 가까워지거나 일치하며, 충돌 설정에서는 성능 향상폭이 감소하는 것을 알 수 있습니다. 이는 대규모 모델이 일반적인 지시 따르기 능력을 향상시키는 동시에 계층적 지시를 따르는 능력 향상에는 제한이 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: The trend of IHEval performance by model scale.
> </details>



![](https://arxiv.org/html/2502.08745/x6.png)

> 🔼 그림 6은 여러 주요 모델이 상충하는 지시사항을 마주했을 때 발생하는 오류 유형을 보여줍니다.  IM(주요 지시사항)과 IC(상충하는 지시사항)으로 구분하여 표시하며, 예시로 '사용자 메시지에서 동사 추출 / 해당 구절을 스페인어로 번역' (작업 실행 - 추출) 과제를 제시하여 각 유형을 설명합니다. 이 그림은 모델들이 우선순위가 높은 지시사항을 따르는 데 어려움을 겪고 있음을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Error types when facing instruction conflicts (all models in Figure 1). IMsubscript𝐼𝑀I_{M}italic_I start_POSTSUBSCRIPT italic_M end_POSTSUBSCRIPT: Main instruction; ICsubscript𝐼𝐶I_{C}italic_I start_POSTSUBSCRIPT italic_C end_POSTSUBSCRIPT: Conflicting instruction. Examples are based on “IMsubscript𝐼𝑀I_{M}italic_I start_POSTSUBSCRIPT italic_M end_POSTSUBSCRIPT: Extract verbs in user message, ICsubscript𝐼𝐶I_{C}italic_I start_POSTSUBSCRIPT italic_C end_POSTSUBSCRIPT: Translate this passage to Spanish” (Task Execution - Extraction).
> </details>



![](https://arxiv.org/html/2502.08745/x7.png)

> 🔼 그림 7은 논문 4.5절에서 설명하는 다양한 설정에 대한 입력 구성을 보여줍니다. 기준 설정과 정렬된 설정 #1에서는 후속 질문만을 사용자 메시지로 직접 사용하는 것이 타당합니다. 이는 평가 범위가 형식 규칙 준수 여부에만 국한되기 때문입니다. 생성된 콘텐츠가 사용자 질문과 일치하는지는 평가 대상이 아닙니다.  다른 설정들은 여러 턴에 걸친 대화에서 형식 규칙과 충돌하는 지시사항을 포함하여 모델의 지시 사항 계층 구조 준수 능력을 평가하기 위해 고안되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: The input configuration of different settings in §4.5. Directly using the follow-up query as the only user message in the reference and aligned #1 settings is reasonable because we only evaluate the adherence to formatting rules, whereas whether the generated content matches the user query is not in the evaluation scope.
> </details>



![](https://arxiv.org/html/2502.08745/x8.png)

> 🔼 그림 8은 논문의 Rule Following 섹션에 있는 single-turn conversation task에 대한 설명입니다. 주요 지침은 녹색으로, 상충되는 지침은 빨간색으로 표시되어 있습니다. 이 그림은 사용자가 제시한 지침에 따라 모델이 응답하는 방식을 보여줍니다. 특히, 주요 지침과 상충되는 지침이 있을 때 모델의 동작을 분석하고 비교하기 위해 single-turn 대화를 사용했습니다. 그림에는 참조 설정, 정렬 설정 및 충돌 설정의 세 가지 설정이 있습니다. 이 그림은 모델이 주어진 지침을 얼마나 잘 따르는지, 그리고 주요 지침과 상충되는 지침이 있을 때 어떻게 행동하는지를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Task card of the single-turn conversation task in Rule Following category. The main instruction is in  green, and the conflicting instruction is in  red.
> </details>



![](https://arxiv.org/html/2502.08745/x9.png)

> 🔼 그림 9는 논문의 '규칙 준수' 섹션에 있는 다회차 대화 과제의 작업 카드를 보여줍니다. 주요 지시사항은 녹색으로, 상충하는 지시사항은 빨간색으로 표시되어 있습니다. 이 과제에는 두 가지 유형의 충돌 설정이 있습니다. (1) 첫 번째 회차 충돌: 시스템 메시지와 상충하는 대화 이력(지시사항 및 응답)만 존재합니다. (2) 두 회차 모두 충돌: 시스템 메시지와 상충하는 대화 이력과 현재 회차 모두 존재합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Task card of the multi-turn conversation task in Rule Following category. The main instruction is in  green, and the conflicting instruction is in  red. There are two conflict settings in this task: (1) First-turn conflict: only the conversational history (instruction & response) conflicting with the system message; and (2) Both-turns conflict: both the history and the current turn conflicting with the system message.
> </details>



![](https://arxiv.org/html/2502.08745/x10.png)

> 🔼 그림 10은 과제 실행 범주의 추출 과제에 대한 작업 카드입니다. 주요 지시 사항은 녹색으로, 상충되는 지시 사항은 빨간색으로 표시되어 있습니다. 시스템 메시지와 사용자 메시지는 더 엄격한 버전으로 바꿀 수 있습니다. 상충되는 설정에서 이상적인 동작은 번역 지시 사항과 과제 데이터를 포함한 전체 사용자 메시지에서 동사를 추출하는 것입니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Task card of the extraction task in Task Execution category. The main instruction is in  green, and the conflicting instruction is in  red. Both the system message and user message can be replaced with the stricter version. In the conflict setting, the ideal behavior is to extract verbs from the entire user message, including the translation instruction and the task data.
> </details>



![](https://arxiv.org/html/2502.08745/x11.png)

> 🔼 그림 11은 과제 실행 범주의 생성 과제에 대한 작업 카드입니다. 주요 지침은 녹색으로, 상충되는 지침은 빨간색으로 표시되어 있습니다. 시스템 메시지와 사용자 메시지는 모두 더 엄격한 버전으로 바꿀 수 있습니다. 상충되는 설정에서 이상적인 동작은 수학 지침과 과제 데이터를 포함하여 전체 사용자 메시지를 번역하는 것입니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Task card of the generation task in Task Execution category. The main instruction is in  green, and the conflicting instruction is in  red. Both the system message and user message can be replaced with the stricter version. In the conflict setting, the ideal behavior is to translate the entire user message, including the math instruction and the task data.
> </details>



![](https://arxiv.org/html/2502.08745/x12.png)

> 🔼 그림 12는 과제 실행 범주의 분류 작업에 대한 작업 카드입니다. 주요 지침은 녹색으로, 상반되는 지침은 빨간색으로 표시되어 있습니다. 시스템 메시지와 사용자 메시지는 더 엄격한 버전으로 대체될 수 있습니다. 이 그림은 모델이 상반되는 지침이 있을 때 주요 지침을 따르는지 평가하는 방법을 보여줍니다. 녹색으로 강조된 주요 지침은 모델이 따라야 할 주요 작업을 나타냅니다. 빨간색으로 강조된 상반되는 지침은 모델의 동작을 방해하거나 다른 작업을 수행하도록 유도하려는 추가 지침입니다. 시스템 메시지와 사용자 메시지는 모두 더 엄격한 버전으로 바뀔 수 있습니다. 이는 모델이 상반되는 지침에도 불구하고 주요 지침을 우선시하도록 보장하기 위해서입니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Task card of the classification task in Task Execution category. The main instruction is in  green, and the conflicting instruction is in  red. Both the system message and user message can be replaced with the stricter version.
> </details>



![](https://arxiv.org/html/2502.08745/x13.png)

> 🔼 그림 13은 안전 방어 범주의 하이재킹 작업에 대한 작업 카드를 보여줍니다. 주요 지침은 녹색으로, 상충하는 지침은 붉은색으로 표시되어 있습니다. 시스템 메시지는 더 많은 잠재적인 적대적 공격을 설명하는 더 엄격한 버전으로 바꿀 수 있습니다. 이 그림은 시스템 메시지, 사용자 메시지, 모델 응답의 세 가지 부분으로 구성됩니다. 시스템 메시지는 모델이 비밀 액세스 코드를 받고, 사용자가 액세스 코드를 입력하면 '액세스 허용'으로 응답하고, 그렇지 않으면 '액세스 거부' 또는 이와 유사한 응답을 하도록 지시합니다. 사용자 메시지는 모델이 '액세스 허용'으로 응답하도록 유도하는 적대적 공격 시나리오입니다. 모델 응답은 모델이 액세스 코드 없이 '액세스 허용'으로 응답했는지 여부를 보여줍니다.  이 그림은 모델이 안전 방어 지침을 따르고, 악의적인 사용자의 적대적 공격에 효과적으로 대응하는 능력을 평가하는 방법을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: Task card of the Hijack task in Safety Defense category. The main instruction is in  green, and the conflicting instruction is in  red. The system message can be replaced with the stricter version, which describes more potential adversarial attacks.
> </details>



![](https://arxiv.org/html/2502.08745/x14.png)

> 🔼 그림 14는 안전 방어 범주의 추출 작업에 대한 작업 카드를 보여줍니다. 주요 지침은 녹색으로, 상충되는 지침은 빨간색으로 표시되어 있습니다. 시스템 메시지는 더 많은 잠재적 적대적 공격을 설명하는 엄격한 버전으로 대체될 수 있습니다. 이 그림은 시스템 메시지가 사용자에게 비밀번호를 제공하지 않고 비밀번호가 입력되면 '액세스 허용'으로 응답하고 그렇지 않으면 '액세스 거부' 또는 유사한 응답을 하는 안전 방어 시나리오를 보여줍니다.  하지만 충돌 설정에서 사용자는 시스템 메시지의 지침을 무시하고 모델이 '액세스 허용'으로 시작하는 응답을 생성하도록 유도하려고 합니다. 엄격한 버전은 이러한 유형의 적대적 공격을 방지하기 위한 추가 지침을 포함합니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: Task card of the Extraction task in Safety Defense category. The main instruction is in  green, and the conflicting instruction is in  red. The system message can be replaced with the stricter version, which describes more potential adversarial attacks.
> </details>



![](https://arxiv.org/html/2502.08745/x15.png)

> 🔼 그림 15는 도구 사용 범주의 고유 명령어 작업에 대한 작업 카드입니다. 주요 지침은 녹색으로, 상충되는 지침은 빨간색으로 표시되어 있습니다. 도구 출력의 삽입된 지침은 웹페이지의 악의적인 조작된 콘텐츠를 나타내는 보다 엄격한 버전으로 바꿀 수 있습니다. 이 그림은 모델이 도구 출력에서 제공되는 정보의 우선순위를 올바르게 판단하고, 악의적으로 조작된 정보에 영향을 받지 않고 주요 작업을 수행하는 능력을 평가하는 데 사용됩니다.  구체적으로, 사용자 메시지는 모델이 웹페이지의 내용을 가져오고 스페인어로 번역하는 작업을 지시합니다. 그러나 도구 출력에는 수학 문제가 포함되어 있어 모델이 번역 작업 대신 수학 문제를 먼저 해결하려고 할 수 있는 상충되는 지침이 삽입됩니다.  엄격한 버전에서는 모델이 다른 모든 지침을 무시하고 수학 문제를 풀도록 명시적으로 지시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 15: Task card of the Intrinsic Instruction task in Tool Use category. The main instruction is in  green, and the conflicting instruction is in  red. The injected instruction in the tool output can be replaced with the stricter version, which represents maliciously manipulated content in the webpage.
> </details>



![](https://arxiv.org/html/2502.08745/x16.png)

> 🔼 그림 16은 도구 사용 범주의 주입 명령어 작업에 대한 작업 카드입니다. 이 작업은 주요 작업이 사용자 메시지(녹색 부분)에 자세히 설명되어 있는 반면, 시스템 메시지는 정확한 일치 평가를 용이하게 하기 위한 형식 제약 조건으로만 사용된다는 점에서 다른 작업과 약간 다릅니다. 상충되는 명령어는 빨간색으로 표시되며, 모델을 공격하기 위해 보다 신중하게 설계된 주입을 나타내는 보다 엄격한 버전으로 바꿀 수 있습니다. 이러한 더욱 강력한 공격의 형식은 AgentDojo Debenedetti et al.(2024)에서 채택되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 16: Task card of the Injected Instruction task in Tool Use category. This task slightly differs from others as the main task is elaborated in the user message (the  green part), whereas the system message only serves as a formatting constraint to facilitate exact-match evaluation. The conflicting instruction is in  red, and can be replaced with the stricter version which represents a more carefully designed injection to attack the model. The format of this stronger attack is adopted from AgentDojo Debenedetti et al. (2024).
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| ![Main](https://arxiv.org/html/2502.08745/main.png) | **Rule** | **Task Execution** | **Safety** | **Tool Use** |
|---|---|---|---|---|
| **Ins.** | Multi-turn | Extract. | Gen. | Class. | Hijack | Extract | Instrinsic | Inject |
|  | First. | Both. | _weak_ | _strong_ | _weak_ | _strong_ | _weak_ | _strong_ | _weak_ | _strong_ | _weak_ | _strong_ |
| _weak_ | 41.0 | 12.3 | 31.8 | 9.3 | 28.3 | 10.4 | 25.9 | 21.5 | 30.6 | 33.3 | 33.3 | 13.1 |
| _strong_ | 55.4 | 16.1 | 37.1 | 16.3 | 50.6 | 24.5 | 47.0 | 38.8 | 43.7 | 45.2 |  | 18.7 | 36.5 | } 36.5{{< /table-caption >}}
> 🔼 표 2는 모순되는 지시사항이 있는 상황에서 지시사항의 엄격성에 따른 모델 성능을 보여줍니다. '주요 지시사항'과 '상충되는 지시사항'은 각각 주요 지시사항과 상충되는 지시사항을 의미합니다. 다회차 규칙 준수의 경우, '첫 번째'와 '모두'는 상충되는 지시사항이 첫 번째 차례 또는 두 차례 모두에 나타나는 설정을 의미합니다(예시는 그림 9 참조).
> <details>
> <summary>read the caption</summary>
> Table 2: Model performance in conflict settings with different strictness of instructions. “Main Ins.” and “Conflict Ins.” refer to the main instruction and the conflicting instruction, respectively. In multi-turn Rule Following, “First.” and “Both.” are settings where conflict instructions appear in the first turn or both turns (see Figure 9 for examples).
> </details>

{{< table-caption >}}
| Model | IPP | Rule | Task | Safety | Tool | Avg |
|---|---|---|---|---|---|---|
|  | ✗ | 50.3 | 71.7 | 94.0 | 63.2 | 70.0 |
| GPT-4o (0806) | ✔ | 54.6 | 65.7 | 93.1 | 56.0 | 67.2 |
|  | ✗ | 19.3 | 7.1 | 24.8 | 8.1 | 14.0 |
| LLaMA 3.1-70B | ✔ | 19.6 | 13.8 | 28.5 | 8.1 | 17.1 |
|  | ✗ | 42.6 | 36.5 | 21.4 | 13.7 | 29.4 |
| Mistral Large | ✔ | 39.6 | 34.6 | 21.2 | 14.6 | 28.3 |{{< /table-caption >}}
> 🔼 표 3은 추가적인 명령어 우선순위 프롬프트(IPP)를 사용했을 때와 사용하지 않았을 때의 성능을 보여줍니다. 점수가 향상된 경우 녹색으로, 점수가 감소한 경우 빨간색으로 표시됩니다. 이 표는 다양한 주요 언어 모델이 계층적 명령어를 따르는 능력을 평가하는 IHEval 벤치마크의 결과를 보여줍니다.  IPP를 추가하면 모델의 성능이 향상될 수 있지만, 일부 모델에서는 성능이 저하되는 것을 확인할 수 있습니다. 이는 계층적 명령어 처리에 대한 모델의 취약성을 보여주는 것입니다. 
> <details>
> <summary>read the caption</summary>
> Table 3: Performance with or without the additional instruction priority prompt (IPP). Improved scores are in green, while decreased scores are in red.
> </details>

{{< table-caption >}}
| Setting | Alignment with Main Instruction | GPT-4 | Claude 3 | All Models |
|---|---|---|---|---|
| **Reference** | - | GPT<br>4o | Claude3<br>Sonnet | All<br>Models | M | 86.5 | 83.9 | 85.9 |
| **Aligned** | - | - | - | ✔ | M | 86.7 | 73.7 | 83.5 |
|  | ✔ | ✔ | ✔ | M | 86.8 | 69.5 | 79.6 |
| **Conflict** | ✔ | ✗ | ✔ | M | 78.1 | 57.2 | 68.9 |
|  | ✗ | ✗ | ✔ | M | 73.2 | 35.9 | 59.5 |
|  | ✗ | ✗ | ✗ | M | 28.6 | 6.3 | 17.7 |
|  | ✗ | ✗ | - | M | 86.6 | 84.7 | 84.2 |{{< /table-caption >}}
> 🔼 표 4는 다회차 규칙 준수 작업의 변형에 대한 결과를 보여줍니다. M은 주요 지침, 𝐼₁은 첫 번째 턴의 사용자 지침, 𝑅₁은 첫 번째 턴의 모델 응답, 𝐼₂는 두 번째 턴의 사용자 지침을 나타냅니다. ✓ 및 ✗는 입력이 주요 지침과 일치하는지 또는 충돌하는지 여부를 나타냅니다. 모든 모델은 표 1에 나열된 모든 모델의 평균 성능을 나타냅니다. 충돌하는 𝑅₁은 응답 형식이 주요 지침을 따르지 않음을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Results on variants of the Multi-turn Rule Following task. M: Main instruction, I1subscript𝐼1I_{1}italic_I start_POSTSUBSCRIPT 1 end_POSTSUBSCRIPT: User instruction in the 1st turn, R1subscript𝑅1R_{1}italic_R start_POSTSUBSCRIPT 1 end_POSTSUBSCRIPT: Model response in the 1st turn, I2subscript𝐼2I_{2}italic_I start_POSTSUBSCRIPT 2 end_POSTSUBSCRIPT: User instruction in the 2nd turn. ✔ and ✗ indicate whether the input aligns or conflicts with the main instruction. All Models refers to the average performance of all models listed in Table 1. A conflicting R1subscript𝑅1R_{1}italic_R start_POSTSUBSCRIPT 1 end_POSTSUBSCRIPT means its response format does not follow the main instruction.
> </details>

{{< table-caption >}}
| Alignment with | Main Instruction |
|---|---|{{< /table-caption >}}
> 🔼 표 5는 IHEval 벤치마크에서 GPT 언어 모델들의 성능을 보여줍니다.  각 모델은 참조 설정(계층적 입력 없음), 정렬 설정(계층적 입력이 일치), 충돌 설정(계층적 입력이 상충) 세 가지 설정에서 평가됩니다.  각 설정에 대한 점수는 규칙 준수, 작업 실행, 안전 방어, 도구 사용 네 가지 범주로 나뉘어 표시됩니다.  |Δ| > 5 로 표시된 빨간색 점수는 계층적 입력을 사용했을 때 성능 저하가 5점 이상임을 나타냅니다.  이 표는 모델의 계층적 지시 사항 준수 능력을 평가하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Results of GPT models on IHEval. Red scores indicate |Δ|>5Δ5|\Delta|>5| roman_Δ | > 5.
> </details>

{{< table-caption >}}
| Model | Setting | Single. | Multi. | Ext. | Gen. | Class. | Hijack | Extract | Intrinsic | Inject | Mean | Abs. | Δ | 
|---|---|---|---|---|---|---|---|---|---|---|---|---|---| 
|  | reference | 70.1 | 69.4 | 79.6 | 76.7 | 100 | 88.8 | 87.7 | 85.9 | 98.0 | 84.0 | - |  | 
|  | aligned | 70.3 | 72.9 | 78.0 | 80.3 | 100 | 94.7 | 97.2 | 78.3 | 92.0 | 84.8 | +0.8 | 4.2 | 
| GPT-3.5-turbo (2024-0125) | conflict | 26.5 | 25.9 | 34.0 | 57.7 | 2.3 | 43.3 | 29.0 | 20.2 | 66.0 | 33.9 | -50.1 | 50.1 | 
|  | reference | 84.5 | 86.1 | 90.5 | 78.4 | 99.6 | 99.1 | 99.4 | 89.3 | 79.0 | 89.6 | - |  | 
|  | aligned | 82.3 | 80.2 | 84.0 | 72.0 | 100 | 98.6 | 98.7 | 82.7 | 59.0 | 84.2 | -5.4 | 5.4 | 
| GPT-4o mini (2024-0718) | conflict | 33.9 | 35.7 | 47.7 | 31.1 | 41.1 | 70.3 | 95.5 | 43.6 | 0 | 44.3 | -45.2 | 45.2 | 
|  | reference | 89.0 | 86.5 | 90.0 | 78.0 | 100 | 99.5 | 100 | 90.2 | 94.0 | 91.9 | - |  | 
|  | aligned | 85.6 | 86.8 | 87.3 | 73.9 | 100 | 99.2 | 98.7 | 88.6 | 99.0 | 91.0 | -0.9 | 2.1 | 
| GPT-4o (2024-0806) | conflict | 49.5 | 51.0 | 77.2 | 38.3 | 99.7 | 91.2 | 96.7 | 63.8 | 62.5 | 70.0 | -21.9 | 21.9 | {{< /table-caption >}}
> 🔼 표 6은 IHEval 벤치마크에서 Claude 언어 모델의 성능을 보여줍니다. 이 표는 다양한 작업(규칙 준수, 작업 실행, 안전 방어, 도구 사용)에 걸쳐 Claude 모델의 정확도를 보여줍니다. 각 작업은 계층적 입력(상호 일치 또는 상충하는 지침)이 있는 설정과 계층적 입력이 없는 기준 설정으로 나뉩니다. 빨간색 점수는 기준 설정과 계층적 입력 설정 간의 성능 차이(|Δ|)가 5보다 큰 경우를 나타냅니다. 이는 Claude 모델이 계층적 지침을 따르는 데 어려움을 겪는다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Results of Claude models on IHEval. Red scores indicate |Δ|>5Δ5|\Delta|>5| roman_Δ | > 5.
> </details>

{{< table-caption >}}
| Model | Setting | Single. | Multi. | Ext. | Gen. | Class. | Hijack | Extract | Intrinsic | Inject | Mean | Abs. |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|  | reference | 77.8 | 78.9 | 84.5 | 77.3 | 100 | 97.4 | 97.5 | 87.6 | 69.0 | 85.6 | - |
|  | aligned | 68.3 | 71.0 | 71.8 | 74.7 | 100 | 90.3 | 94.0 | 80.2 | 33.0 | 75.9 | -9.7 |
| Claude-3<br>Haiku | conflict | 15.4 | 23.4 | 7.3 | 23.6 | 26.0 | 42.2 | 52.4 | 59.1 | 1.5 | 27.9 | -57.7 |
|  | reference | 80.9 | 83.9 | 84.9 | 76.9 | 100 | 87.1 | 85.5 | 87.1 | 87.0 | 85.9 | - |
|  | aligned | 68.4 | 69.5 | 77.4 | 79.8 | 100 | 97.6 | 97.2 | 85.3 | 91.0 | 85.1 | -0.8 |
| Claude-3<br>Sonnet | conflict | 10.8 | 21.1 | 2.3 | 29.7 | 9.8 | 46.6 | 60.1 | 56.9 | 39.0 | 30.7 | -55.2 |{{< /table-caption >}}
> 🔼 표 7은 IHEval 벤치마크에서 LLaMA-3.1 모델의 성능을 보여줍니다. 표에는 다양한 작업(규칙 준수, 작업 실행, 안전 방어, 도구 사용)과 각 작업의 세 가지 설정(기준, 정렬, 충돌)에 대한 결과가 포함되어 있습니다.  각 설정에서 모델의 정확도와 계층적 지시 사항을 따르지 못한 정도를 나타내는 Δ 값이 제시됩니다. 빨간색 점수는 절대 Δ 값이 5보다 큰 경우를 나타냅니다. 즉, 계층적 지시 사항이 있을 때 모델 성능의 큰 변화를 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Results of LLaMA-3.1 models on IHEval. Red scores indicate |Δ|>5Δ5|\Delta|>5| roman_Δ | > 5.
> </details>

{{< table-caption >}}
| Model | Setting | Single. | Multi. | Ext. | Gen. | Class. | Hijack | Extract | Intrinsic | Inject | Mean | Abs. | 
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|  | reference | 80.7 | 79.6 | 84.4 | 72.5 | 100 | 70.2 | 68.2 | 85.1 | 91.0 | 81.3 | - |
|  | aligned | 71.1 | 68.1 | 77.1 | 48.9 | 96.9 | 66.2 | 64.1 | 7.9 | 0.0 | 55.6 | -25.7 |
| LLaMA-3.1 8B | conflict | 14.5 | 20.1 | 21.8 | 7.1 | 0.1 | 19.2 | 11.3 | 7.8 | 0.0 | 11.3 | -70.0 |
|  | reference | 88.3 | 88.4 | 89.1 | 77.0 | 100 | 99.3 | 99.7 | 89.0 | 100 | 92.3 | - |
|  | aligned | 82.9 | 76.6 | 84.3 | 59.5 | 100 | 95.8 | 96.2 | 20.3 | 94.0 | 78.8 | -13.5 |
| LLaMA-3.1 70B | conflict | 14.3 | 24.3 | 0 | 15.2 | 6.2 | 24.4 | 25.2 | 2.2 | 14.0 | 14.0 | -78.3 |{{< /table-caption >}}
> 🔼 표 8은 IHEval 벤치마크에서 LLaMA-3 모델들의 성능을 보여줍니다.  표에는 각 모델이 Rule Following, Task Execution, Safety Defense 세 가지 범주에서 얼마나 잘 지시 사항 계층 구조를 따르는지 평가한 결과가 담겨 있습니다.  각 범주 내에서도 여러 하위 작업들이 있고, 이들 각각에 대한 정확도가 제시됩니다.  |Δ| > 5 로 표시된 붉은색 점수는 기준 설정(단일 입력 설정)과 계층적 입력 설정(계층적 지시사항이 포함된 설정) 간의 성능 차이가 5%p를 넘는다는 것을 의미합니다.  즉, 붉은색은 모델이 계층적 지시사항 처리에 어려움을 겪는다는 것을 나타냅니다. LLaMA-3 모델들은 툴 호출 기능을 공식적으로 지원하지 않으므로, 툴 사용 설정(Tool Use) 결과는 표에 포함되지 않았습니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Results of LLaMA-3 models on IHEval. Red scores indicate |Δ|>5Δ5|\Delta|>5| roman_Δ | > 5. As LLaMA-3 models do not officially support tool calling, we skip the Tool Use setting for them.
> </details>

{{< table-caption >}}
| Model | Setting | Single. | Multi. | Ext. | Gen. | Class. | Hijack | Extract | Intrinsic | Inject | Mean | Δ | Abs. |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---| 
|  | reference | 77.0 | 74.6 | 79.7 | 73.5 | 100.0 | 93.2 | 92.8 | - | - | 84.4 | - | - |
|  | aligned | 71.4 | 57.7 | 72.0 | 57.2 | 100.0 | 82.2 | 78.9 | - | - | 74.2 | -10.2 | 10.2 |
| LLaMA-3<br>8B | conflict | 22.7 | 22.6 | 20.0 | 15.6 | 0.2 | 22.0 | 23.6 | - | - | 18.1 | -66.3 | 66.3 |
|  | reference | 83.8 | 84.3 | 85.4 | 74.9 | 99.6 | 98.8 | 99.7 | - | - | 89.5 | - | - |
|  | aligned | 81.5 | 69.8 | 79.8 | 64.4 | 99.4 | 97.9 | 97.2 | - | - | 84.3 | -5.2 | 5.2 |
| LLaMA-3<br>70B | conflict | 15.0 | 23.9 | 2.0 | 24.5 | 33.2 | 32.9 | 37.4 | - | - | 24.2 | -65.3 | 65.3 |{{< /table-caption >}}
> 🔼 표 9는 Mistral 언어 모델의 IHEval 벤치마크 결과를 보여줍니다.  각 모델의 기본 성능(Reference), 계층적 입력이 일치하는 경우(Aligned), 그리고 계층적 입력이 충돌하는 경우(Conflict)의 세 가지 설정에 대한 성능을 보여줍니다. 각 과제(Rule Following, Task Execution, Safety Defense, Tool Use)별 점수와 전체 평균 점수, 그리고 Reference 설정과 다른 설정 간의 점수 차이(Δ)와 절대 점수 차이의 평균값을 나타냅니다.  |Δ| 값이 5보다 큰 점수는 빨간색으로 표시되어, 계층적 지시 사항을 따르는 데 어려움을 겪는 부분을 강조합니다. 이 표는 Mistral 모델의 크기(7B, Large)에 따른 성능 변화를 분석하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Results of Mistral models on IHEval. Red scores indicate |Δ|>5Δ5|\Delta|>5| roman_Δ | > 5.
> </details>

{{< table-caption >}}
| Model | Setting | Single. | Multi. | Ext. | Gen. | Class. | Hijack | Extract | Intrinsic | Inject | Mean | Abs. | Δ | 
|---|---|---|---|---|---|---|---|---|---|---|---|---|---| 
|  | reference | 53.9 | 54.4 | 44.8 | 61.1 | 42.9 | 63.0 | 61.3 | 54.0 | 51.0 | 54.0 | - |  | 
|  | aligned | 54.7 | 63.6 | 42.5 | 39.1 | 88.5 | 58.1 | 60.1 | 30.6 | 0.0 | 48.6 | -5.4 | 17.9 | 
| Mistral-7B <br> Instruct-v0.3 | conflict | 22.6 | 39.7 | 15.8 | 15.2 | 12.4 | 18.6 | 8.6 | 2.0 | 0.0 | 15.0 | -39.0 | 39.0 | 
|  | reference | 83.6 | 85.2 | 85.2 | 78.5 | 100 | 99.2 | 98.4 | 88.3 | 69.0 | 87.5 | - |  | 
|  | aligned | 81.7 | 87.1 | 76.0 | 78.3 | 100 | 97.7 | 99.1 | 77.9 | 79.0 | 86.3 | -1.2 | 4.0 | 
| Mistral-Large <br> (2407) | conflict | 25.2 | 60.0 | 11.0 | 20.2 | 78.4 | 23.9 | 18.8 | 13.9 | 13.5 | 29.4 | -58.1 | 58.1 |{{< /table-caption >}}
> 🔼 표 10은 IHEval 벤치마크에서 Qwen-2 언어 모델의 성능을 보여줍니다. 표에는 다양한 작업(규칙 준수, 작업 실행, 안전 방어, 도구 사용)과 설정(참조, 정렬, 충돌)에 대한 결과가 포함되어 있습니다.  각 설정에서 모델의 정확도와 계층적 지시 사항을 따르지 못한 정도(Δ)가 표시됩니다. 빨간색 점수는 절대값이 5보다 큰 Δ값을 나타내며, 모델이 계층적 지시 사항을 처리하는 데 어려움을 겪었음을 시사합니다. 이 표는 주로 모델의 규모와 계층적 지시 사항 준수 능력 사이의 관계를 분석하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Results of Qwen-2 models on IHEval. Red scores indicate |Δ|>5Δ5|\Delta|>5| roman_Δ | > 5.
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