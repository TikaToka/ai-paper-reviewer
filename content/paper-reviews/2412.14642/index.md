---
title: "TOMG-Bench: Evaluating LLMs on Text-based Open Molecule Generation"
summary: "TOMG-Bench: LLM 기반 오픈 분자 생성 벤치마크 제시! 25개 LLM 평가 및 새로운 instruction tuning 데이터셋 OpenMolIns 공개로, 오픈소스 LLM의 성능 향상 및 분자 발견의 새로운 가능성 제시!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Hong Kong Polytechnic University",]
showSummary: true
date: 2024-12-19
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.14642 {{< /keyword >}}
{{< keyword icon="writer" >}} Jiatong Li et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-20 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.14642" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.14642" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/tomg-bench-evaluating-llms-on-text-based-open" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존 분자 발견 연구는 **시행착오적**이며 비효율적입니다.  **LLM**은 텍스트 기반으로 분자 구조를 이해하고 생성할 수 있는 잠재력을 가지고 있지만, 이를 평가할 수 있는 표준화된 벤치마크가 부족했습니다.  특히, **기존의 텍스트-분자 변환 과제**는 목표 분자를 생성하는 데에 집중되어 있어, 새로운 분자를 창출하는 데에는 한계가 있습니다.

본 논문에서는 **텍스트 기반 오픈 분자 생성**을 위한 새로운 벤치마크인 TOMG-Bench를 제시합니다.  여기에는 분자 수정, 최적화 및 맞춤형 생성이라는 세 가지 주요 과제가 포함됩니다.  또한, **자동화된 평가 시스템**과 **OpenMolIns**라는 새로운 instruction tuning 데이터셋을 개발하여 LLM의 성능을 더욱 향상시켰습니다.  결과적으로, 본 연구는 LLM이 분자 발견에 기여할 수 있는 잠재력을 보여주고, 향후 연구를 위한 새로운 기준을 제시합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 텍스트 기반 오픈 분자 생성(TOMG)이라는 새로운 과제를 제시하고 이를 위한 벤치마크인 TOMG-Bench를 개발했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 25개의 다양한 LLM을 TOMG-Bench로 평가하여, 기존의 한계와 개선 방향을 제시했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} OpenMolIns라는 새로운 instruction tuning 데이터셋을 제시하여 Llama-3.1-8B의 성능을 향상시켰고, 기존 오픈소스 LLM들을 능가하는 성능을 달성했습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **LLM 기반의 오픈 분자 생성**이라는 새로운 연구 분야를 개척하여, 과학적 발견에 있어 LLM의 잠재력을 보여줍니다. 제시된 벤치마크와 데이터셋은 향후 연구의 기준점이 되어, **새로운 분자 발견 및 신약 개발**에 크게 기여할 것입니다.  또한, 본 연구는 오픈소스 LLM의 발전을 보여주는 동시에, 향후 연구 방향을 제시하여 **AI 기반 과학 연구**의 발전을 가속화할 것입니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.14642/x1.png)

> 🔼 그림 1은 텍스트 기반의 표적 분자 생성(a)과 텍스트 기반의 개방형 분자 생성(b)을 비교한 것입니다. (a)에서는 특정 분자 구조를 생성하는 것을 목표로 하며, 정답은 하나 뿐입니다. 예를 들어, 특정 원자와 결합 수를 가진 분자를 생성하라는 지시가 주어집니다. 반면에 (b)에서는 특정 원자나 결합 수에 대한 제약은 있지만, 여러 개의 올바른 답이 존재합니다. 즉, 다양한 구조의 분자들을 생성할 수 있으며, 생성된 분자의 정확성과 질을 평가하는 자동화된 시스템이 필요합니다. 이러한 차이점은 개방형 분자 생성의 복잡성과 어려움을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Comparison of Text-Based Targeted Molecule Generation (a) v.s. Text-Based Open Molecule Generation (b).
> </details>





{{< table-caption >}}
| Item | Data Size |
|---|---| 
| TOMG-Bench |  |
| subtask | 5,000 |
| OpenMolIns |  |
| light | 4,500 |
| small | 18,000 |
| medium | 45,000 |
| large | 90,000 |
| xlarge | 1,200,000 |{{< /table-caption >}}

> 🔼 이 표는 TOMG-Bench와 OpenMolIns 데이터셋의 통계를 보여줍니다. TOMG-Bench는 세 가지 주요 작업(MolEdit, MolOpt, MolCustom)과 각 작업에 해당하는 세 가지 하위 작업으로 구성되며, 각 하위 작업에는 5,000개의 테스트 샘플이 있습니다. OpenMolIns 데이터셋은 다양한 훈련 목적을 위해 다섯 가지 데이터 규모(light, small, medium, large, xlarge)로 구성되어 있으며, TOMG-Bench의 아홉 가지 하위 작업이 균등하게 분포되어 있습니다.  각 데이터 규모에 대한 샘플 수가 명시되어 있어, 모델의 성능에 미치는 데이터 규모의 영향을 분석하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Statisics of TOMG-Bench and OpenMolIns.
> </details>





### In-depth insights


#### LLM Molecule Gen
LLM 분자 생성(LLM Molecule Gen)은 **대규모 언어 모델(LLM)**이 분자 구조를 생성하는 능력을 평가하는 흥미로운 연구 분야입니다.  이 분야는 **약물 발견 및 재료 과학** 분야에서 혁신적인 발전을 가져올 수 있는 잠재력을 가지고 있습니다.  **SMILES 표기법**과 같은 텍스트 기반 표현을 사용하여 LLM은 분자 구조를 생성하고 수정할 수 있으며, 이는 기존의 시행착오 방식보다 효율적인 접근 방식을 제공합니다.  **그러나 LLM은 아직 분자 생성의 복잡성을 완전히 이해하지 못하고 있으며, 생성된 분자의 정확성과 품질을 높이는 데에는 여전히 과제가 존재합니다.**  **학습 데이터의 질과 양**, **모델의 일반화 능력**, **평가 지표의 적절성** 등이 향후 연구에서 고려해야 할 중요한 요소입니다.  **특히, 개방형 분자 생성(open-domain molecule generation) 과제는 LLM의 일반화 능력을 평가하는 데 매우 중요하며, 더욱 엄격한 평가 기준과 새로운 벤치마크 개발이 필요합니다.**  본 연구는 이러한 과제를 해결하고 LLM 기반 분자 발견의 잠재력을 충분히 활용하기 위한 중요한 발걸음이 될 것입니다.  향후 연구는  **LLM의 생성 능력 향상**, **새로운 평가 방법 개발**, **다양한 분야에서의 응용 연구** 등에 초점을 맞춰야 할 것입니다.

#### TOMG-Bench
TOMG-Bench는 **LLM(대규모 언어 모델)의 텍스트 기반 개방형 분자 생성 능력을 평가하기 위한 최초의 벤치마크**입니다. 기존의 표적 분자 생성 작업과 달리, TOMG-Bench는 **특정 목표를 설정하지 않고 LLM이 다양한 화학적 작업(분자 편집, 최적화, 사용자 정의 생성)을 수행할 수 있는지 평가**합니다. 이는 **LLM의 일반화 능력과 창의성을 측정**하는 데 중요합니다.  **자동화된 평가 시스템**을 통해 생성된 분자의 질과 정확성을 측정하며, **25개의 LLM에 대한 종합적인 벤치마크 결과**를 제공하여 현재 LLM의 한계와 개선 가능성을 제시합니다. 특히, OpenMolIns라는 특수 지시어 미세 조정 데이터셋을 통해 Llama-3.1-8B가 다른 오픈소스 일반 LLM을 능가하고 심지어 GPT-3.5-turbo보다 성능이 뛰어남을 보여줍니다.  **TOMG-Bench는 화학 분야에서 LLM의 잠재력을 평가하고 발전시키는 데 중요한 역할**을 할 것으로 기대됩니다.

#### OpenMolIns
본 논문에서 제시된 OpenMolIns는 **LLM(대규모 언어 모델)의 분자 생성 능력 향상을 위한 새로운 지침 미세 조정 데이터셋**입니다. 기존의 분자-캡션 변환 작업의 한계를 극복하기 위해, **열린 도메인 분자 생성 작업**을 위한 새로운 벤치마크인 TOMG-Bench와 함께 제시되었습니다.  OpenMolIns는 기존의 PubChem 데이터베이스에서 추출하고 재구성된 분자들을 포함하며, 다양한 규모의 데이터(light, small, medium, large, xlarge)로 구성되어 있어 모델의 데이터 크기 확장성을 평가하는 데 유용합니다.  **TOMG-Bench의 하위 작업들과의 균형있는 분포**를 가지도록 설계되었고, LLM의 분자 구조 및 편집 능력 향상에 효과적임을 실험 결과를 통해 보여줍니다.  **Llama-3.1-8B 모델의 성능 향상**에 기여하여, 오픈소스 일반 LLM이 TOMG-Bench에서 우수한 성능을 달성할 수 있도록 도왔다는 점에서 그 중요성이 부각됩니다.

#### LLM Limitations
본 논문에서 다룬 LLM의 한계는 크게 **데이터 품질 및 다양성 부족**, **프롬프트(지시문)의 다양성 부족**, **과도한 단순화** 세 가지로 요약할 수 있습니다.  **데이터 품질 및 다양성 부족**은 모델 학습에 사용된 ChEBI-20 데이터셋의 규모와 다양성이 제한적이라는 점을 의미합니다.  이는 모델의 일반화 능력을 저해하고 새로운 분자 구조를 생성하는 능력에 부정적인 영향을 미쳤습니다.  **프롬프트 다양성 부족**은 모델이 특정 유형의 질문에 대해 과도하게 학습되어 유연성이 떨어지는 점을 시사합니다.  다양한 표현 방식과 질문 유형을 포함한 더욱 다양한 프롬프트를 통해 이러한 한계를 극복할 수 있을 것입니다.  마지막으로 **과도한 단순화**는 모델이 분자의 복잡한 구조 및 특성을 충분히 이해하지 못하고 단순화된 방식으로 문제에 접근하는 경향을 나타냅니다.  **더욱 정교하고 복잡한 분자 구조 및 특성에 대한 데이터와, 이를 효과적으로 처리할 수 있는 모델 아키텍처 개발**이 필요합니다.

#### Future Directions
본 논문은 향후 연구 방향으로 **LLM의 일반화 능력 향상**과 **다양한 화학적 특성 고려**를 제시합니다. 현재 LLM은 특정 작업에 대해서는 뛰어난 성능을 보이지만, 다양한 분야에 적용하기에는 일반화 능력이 부족합니다. 따라서, **더욱 광범위한 데이터셋을 활용한 훈련**을 통해 LLM의 일반화 능력을 향상시키는 것이 중요하며, 이를 위해 **새로운 평가 지표 및 벤치마크 개발**도 필요합니다. 또한, 분자 구조 편집이나 최적화 작업에서 **물리 화학적 특성을 보다 정확하게 예측**하고 고려하는 것이 필수적입니다. 이를 위해, **물리 화학적 지식을 통합한 LLM 개발** 및 **기존의 그래프 신경망(GNN) 기반 방법론과의 결합** 등이 중요한 연구 방향으로 제시됩니다.  **새로운 분자 구조 생성 능력 강화** 또한 중요한 과제입니다.  기존 방법론의 한계를 극복하고 더욱 **혁신적인 분자 구조를 생성**하기 위한 연구가 필요하며, **LLM과 GNN을 결합한 하이브리드 모델 개발**이 유망한 방안으로 생각됩니다.  **실험적 검증**을 통해 모델의 실제 성능을 확인하고 개선하는 것도 중요한 미래 연구 방향입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.14642/x2.png)

> 🔼 그림 2는 TOMG-Bench의 데이터 구성 워크플로우와 평가 프로세스를 보여줍니다.  TOMG-Bench는 분자 편집(MolEdit), 분자 최적화(MolOpt), 맞춤형 분자 생성(MolCustom)의 세 가지 주요 작업으로 구성됩니다. 각 작업은 세 가지 하위 작업으로 더 나뉘며, 각 하위 작업은 5,000개의 테스트 샘플을 포함합니다.  데이터 생성 과정은 RDKit과 같은 화학 도구 상자를 활용하여 분자의 기본 구조 및 특성을 분석하고, 이를 바탕으로 LLMs의 성능을 평가하는 자동화된 평가 시스템을 사용합니다.  이 그림은 데이터 생성 과정부터 LLMs의 입력, RDKit을 이용한 유효성 검사, 그리고 최종 성능 측정까지의 전체적인 흐름을 시각적으로 나타냅니다.  각 단계에서 사용되는 도구 및 메트릭도 함께 표시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Data construction workflow and evaluation process of TOMG-Bench.
> </details>



![](https://arxiv.org/html/2412.14642/extracted/6081791/figures/performance.png)

> 🔼 그림 3은 TOMG-Bench에서 벤치마킹된 모델들의 성능을 보여줍니다. TOMG-Bench는 독점 모델, 오픈소스 일반 LLM, 오픈소스 ChEBI-20 미세 조정 LLM, OpenMolIns 미세 조정 LLM의 네 가지 범주로 나뉩니다. 매개변수가 알려진 모델은 점으로 표시되고, 매개변수가 알려지지 않은 모델은 수평선으로 표시됩니다. 이 그림은 다양한 모델들의 크기와 TOMG-Bench에서의 성능을 비교하여, 모델의 크기와 성능 사이의 관계를 보여줍니다. 또한, 미세 조정 전략이 모델 성능에 미치는 영향을 시각적으로 보여줍니다.  각 모델의 성능은 가중 평균 정확도(wAcc)로 측정됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: The performance of models benchmarked in TOMG-Bench. In TOMG-Bench, LLMs are divided into 4 categories: Proprietary Models, Open-source General LLMs, Open-source ChEBI-20 Fine-tuned LLMs, and OpenMolIns Fine-tuned LLMs. Models whose parameters are known are plotted as dots, while models of unknown parameters are denoted as horizontal lines.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Prompt Templates for MolEdit |
|---|---|---|---|---|
| *AddComponent* | Please add a {} to the molecule {}. | Modify the molecule {} by adding a {}. | Add a {} to the molecule {}. |  |
| *DelComponent* | Please remove a {} from the molecule {}. | Modify the molecule {} by removing a {}. | Remove a {} from the molecule {}. |  |
| *SubComponent* | Please substitute a {} in the molecule {} by {}. | Modify the molecule {} by replacing a {} by {}. | Replace a {} in the molecule {} by {}. | Please replace a {} in the molecule {} with {}. | Modify the molecule {} by substituting a {} with {}. | Substitute a {} in the molecule {} with {}. |{{< /table-caption >}}
> 🔼 이 표는 논문의 MolEdit 작업에 사용된 프롬프트 템플릿을 보여줍니다. AddComponent, DelComponent, SubComponent 세 가지 하위 작업에 대한 프롬프트 예시가 포함되어 있으며, 각 하위 작업에 대해 여러 가지 변형된 프롬프트 예시를 제공하여 모델의 다양한 입력에 대한 성능을 평가하고자 함을 알 수 있습니다.  표는  LLM이 분자 구조를 수정하는 작업을 수행하도록 안내하는 다양한 방법들을 보여주는 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Prompt Templates for MolEdit
> </details>

{{< table-caption >}}
| Functional Group | benzene ring | hydroxyl | aldehyde | carboxyl | amide |
|---|---|---|---|---|---| 
| Weights | 15 | 15 | 5 | 5 | 10 |
| Functional Group | amine | nitro | halo | nitrile | thiol |
| Weights | 5 | 5 | 5 | 1 | 1 |{{< /table-caption >}}
> 🔼 이 표는 AddComponent 및 DelComponent 작업에서 고려되는 작용기와 AddComponent에서 선택 가중치를 보여줍니다.  각 작용기는 분자의 구조적 특징과 다양한 화합물에서의 빈도를 반영하는 가중치를 부여받습니다.  가중치가 높을수록 해당 작용기가 AddComponent 작업에서 선택될 확률이 높아집니다.  이를 통해 실제 화학 반응에서 작용기의 출현 빈도를 더욱 정확하게 반영하여 모델의 일반화 성능을 향상시키는 데 기여합니다. 
> <details>
> <summary>read the caption</summary>
> Table 3: Functional Groups that are considered in AddComponent and DelComponent, as well as their weights to be selected in AddComponent.
> </details>

{{< table-caption >}}
| Prompt Templates for MolOpt |
|---|---|---|---|---|
| *LogP* | Please optimize the molecule {} to have a lower/higher LogP value. | Modify the molecule {} to decrease/increase its LogP value. | Optimize the molecule {} to have a lower/higher LogP value. | Please modify the molecule {} to decrease/increase its LogP value. | Modify the molecule {} to have a lower/higher LogP value. |
| *MR* | Please optimize the molecule {} to have a lower/higher MR value. | Modify the molecule {} to decrease/increase its MR value. | Optimize the molecule {} to have a lower/higher MR value. | Please modify the molecule {} to decrease/increase its MR value. | Modify the molecule {} to have a lower/higher MR value. |
| *QED* | Please optimize the molecule {} to have a lower/higher QED value. | Modify the molecule {} to decrease/increase its QED value. | Optimize the molecule {} to have a lower/higher QED value. | Please modify the molecule {} to decrease/increase its QED value. | Modify the molecule {} to have a lower/higher QED value. |{{< /table-caption >}}
> 🔼 표 4는 MolOpt 작업에 사용된 프롬프트 템플릿을 보여줍니다. MolOpt 작업은 분자의 구조를 개선하여 특정 분자 특성(LogP, MR, QED)을 최적화하는 것을 목표로 합니다. 이 표에는 LogP(분자의 친유성/친수성을 측정), MR(분자 크기 및 가지화 정도를 측정), QED(약물 유사성을 평가하는 계산 지표) 값을 낮추거나 높이는 것을 목표로 하는 다양한 프롬프트 템플릿이 포함되어 있습니다. 각 특성에 대해 여러 개의 프롬프트 템플릿이 제시되어 있으며, 이는 LLM이 다양한 방식으로 분자 구조를 최적화할 수 있도록 하기 위함입니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Prompt Templates for MolOpt
> </details>

{{< table-caption >}}
| Prompt Templates for MolCustom |
|---|---|---|---|
| *AtomNum* | *BondNum* | *FunctionalGroup* |
| Please generate a molecule with {} atom(s). | Please generate a molecule with {} bond(s). | Please generate a molecule with {} group(s). |
| Please generate a molecule composed of {} atom(s). | Please generate a molecule composed of {} bond(s). | Please generate a molecule composed of {} group(s). |
| Please generate a molecule consisting {} atom(s). | Please generate a molecule consisting {} bond(s). | Please generate a molecule consisting {} group(s). |
| The molecule has {} atom(s). | The molecule has {} bond(s). | The molecule has {} group(s). |
| The molecule is composed of {} atom(s). | The molecule is composed of {} bond(s). | The molecule is composed of {} group(s). |
| The molecule consists of {} atom(s). | The molecule consists of {} bond(s). | The molecule consists of {} group(s). |
| There is a molecule with {} atom(s). | There is a molecule with {} bond(s). | There is a molecule with {} group(s). |
| There is a molecule composed of {} atom(s). | There is a molecule composed of {} bond(s). | There is a molecule composed of {} group(s). |
| There is a molecule consisting of {} atom(s). | There is a molecule consisting of {} bond(s). | There is a molecule consisting of {} group(s). |
| The molecule contains {} atom(s). | The molecule contains {} bond(s). | The molecule contains {} group(s). |{{< /table-caption >}}
> 🔼 표 5는 MolCustom 작업에 사용된 프롬프트 템플릿을 보여줍니다. MolCustom 작업은 원하는 분자를 생성하는 작업으로, 세 가지 하위 작업(AtomNum, BondNum, FunctionalGroup)으로 구성됩니다. 각 하위 작업마다 분자의 원자 수, 결합 수, 작용기의 종류와 개수를 지정하는 다양한 프롬프트 템플릿이 제공됩니다. 이 표는 각 하위 작업에 대한 다양한 프롬프트 표현 방식을 보여주어, LLM이 이러한 다양한 표현 방식을 얼마나 잘 이해하고 생성 작업을 수행하는지 평가하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Prompt Templates for MolCustom
> </details>

{{< table-caption >}}
| Atom | carbon | oxygen | nitrogen | sulfur | fluorine | chlorine | bromine | iodine | phosphorus |
|---|---|---|---|---|---|---|---|---|---| 
| Weights | [Mandatory] | 5 | 3 | 3 | 2 | 2 | 2 | 2 | 1 |
| Atom | boron | silicon | selenium | tellurium | arsenic | antimony | bismuth | polonium |  |
| Weights | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |  |{{< /table-caption >}}
> 🔼 표 6은 AtomNum 하위 작업에서 사용되는 원자 목록과 각 원자의 가중치를 보여줍니다.  AtomNum 작업은 지정된 수와 종류의 원자를 포함하는 분자를 생성하는 것을 목표로 합니다. 이 표는 각 원자의 선택 확률을 나타내는 가중치를 제공하며, 이는 실제 분자 데이터 분포를 반영하기 위해 설계되었습니다.  탄소(carbon)는 유기 화합물의 기본 구성 요소이기 때문에 필수 원소로 지정되어 있고, 다른 원자들은 다양한 화학적 특성을 반영하여 가중치가 부여됩니다. 이 가중치는 LLMs이 다양한 종류의 분자를 생성하도록 유도하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Atoms that are considered in AtomNum, as well as their weights to be selected.
> </details>

{{< table-caption >}}
| Bond | single | double | triple | rotatable | aromatic |
|---|---|---|---|---|---| 
| Weights | 5 | 4 | 3 | 1 | 1 |{{< /table-caption >}}
> 🔼 표 7은 BondNum 작업에서 고려되는 화학 결합과 각 결합이 선택될 가중치를 보여줍니다.  단일 결합, 이중 결합, 삼중 결합, 회전 가능한 결합, 방향족 결합의 다섯 가지 유형의 화학 결합이 포함됩니다. 각 유형의 결합은 선택될 확률을 나타내는 가중치가 할당되어 있으며, 이는 실제 분자 데이터에서의 분포를 반영합니다.  예를 들어, 단일 결합은 5의 가중치를 가지며, 이는 다른 유형의 결합보다 더 높은 선택 확률을 가짐을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Chemical bonds that are considered in BondNum, as well as their weights to be selected.
> </details>

{{< table-caption >}}
| Functional Group | benzene ring | hydroxyl | anhydride | aldehyde | ketone | carboxyl | ester | amide | amine | nitro |
|---|---|---|---|---|---|---|---|---|---|---|
| Weights | 15 | 15 | 2 | 5 | 5 | 10 | 5 | 5 | 5 | 2 |
| Functional Group | halo | thioether | nitrile | thiol | sulfide | disulfide | sulfoxide | sulfone | borane |  |
|---|---|---|---|---|---|---|---|---|---|---|
| Weights | 2 | 1 | 1 | 1 | 1 | 1 | 1 | 1 | 1 |  |{{< /table-caption >}}
> 🔼 표 8은 MolCustom 작업의 하위 작업인 FunctionalGroup에서 사용되는 작용기 목록과 각 작용기의 가중치를 보여줍니다.  각 작용기는 분자 구조에서 고유한 역할을 하며, 가중치는 실제 분자 데이터셋에서의 작용기 출현 빈도를 반영하여 결정되었습니다. 이 가중치는 모델이 다양한 작용기를 가진 분자를 생성하도록 유도하는 데 사용됩니다. 가중치가 높을수록 해당 작용기가 생성될 확률이 높아집니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Functional Groups that are considered in FunctionalGroup, as well as their weights to be selected.
> </details>

{{< table-caption >}}
| Item | Value |
|---|---| 
| Generation |  |
| temperature | 0.75 |
| top_p | 0.85 |
| num_beams | 1 |
| max_new_tokens | 512 |
| Instruction Tuning |  |
| batchsize | 32 |
| lr | 3e-4 |
| cutoff_len | 1024 |
| Lora Settings |  |
| r | 64 |
| α | 128 |
| dropout | 0.1 |{{< /table-caption >}}
> 🔼 표 9는 본 논문의 실험에서 사용된 하이퍼파라미터들을 보여줍니다.  각 하이퍼파라미터의 이름과 설정 값이 명시되어 있으며, 모델 생성 및 학습 과정에 영향을 미치는 중요한 변수들을 포함하고 있습니다.  이 표는 실험의 재현성을 확보하고, 다른 연구자들이 유사한 실험을 수행할 때 참고할 수 있도록 상세한 설정 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Hyper-parameters
> </details>

{{< table-caption >}}
| Model | #Parameters (B) | \bar{Acc} (%) | \bar{wAcc}(
%) | 
|---|---|---|---| 
| Claude-3.5 Anthropic (2024b) | - | 51.10 | 35.92 | 
| Gemini-1.5-pro Deepmind (2024) | - | 52.25 | 34.80 | 
| GPT-4-turbo Achiam et al. (2023) | - | 50.74 | 34.23 | 
| GPT-4o Achiam et al. (2023) | - | 49.08 | 32.29 | 
| Claude-3 Anthropic (2024a) | - | 46.14 | 30.47 | 
| OpenMolIns-large (Llama-3.1-8B) | 8 | 43.1 | 27.22 | 
| OpenMolIns-xlarge (Galactica-125M) | 0.125 | 44.48 | 25.73 | 
| Llama3-70B-Instruct (Int4) Dubey et al. (2024) | 70 | 38.54 | 23.93 | 
| OpenMolIns-large (Galactica-125M) | 0.125 | 39.28 | 23.42 | 
| OpenMolIns-medium (Galactica-125M) | 0.125 | 34.54 | 19.89 | 
| GPT-3.5-turbo Achiam et al. (2023) | - | 28.93 | 18.58 | 
| OpenMolIns-small (Galactica-125M) | 0.125 | 24.17 | 15.18 | 
| Llama3.1-8B-Instruct Dubey et al. (2024) | 8 | 26.26 | 14.09 | 
| Llama3-8B-Instruct Dubey et al. (2024) | 8 | 26.40 | 13.75 | 
| chatglm-9B GLM et al. (2024) | 9 | 18.50 | 13.13(7) | 
| OpenMolIns-light (Galactica-125M) | 0.125 | 20.95 | 13.13(6) | 
| OpenMolIns-large (Llama3.2-1B) | 1 | 14.11 | 8.10 | 
| yi-1.5-9B Young et al. (2024) | 9 | 14.10 | 7.32 | 
| Mistral-7B-Instruct-v0.2 Jiang et al. (2023) | 7 | 11.17 | 4.81 | 
| BioT5-base Pei et al. (2023) | 0.25 | 24.19 | 4.21 | 
| MolT5-large Edwards et al. (2022) | 0.78 | 23.11 | 2.89 | 
| Llama-3.1-1B-Instruct Dubey et al. (2024) | 1 | 3.95 | 1.99 | 
| MolT5-base Edwards et al. (2022) | 0.25 | 11.11 | 1.30(0) | 
| MolT5-small Edwards et al. (2022) | 0.08 | 11.55 | 1.29(9) | 
| Qwen2-7B-Instruct Yang et al. (2024) | 7 | 0.18 | 0.15 |{{< /table-caption >}}
> 🔼 표 10은 본 논문에서 제안하는 TOMG-Bench 벤치마크에 대한 리더보드를 보여줍니다.  다양한 크기의 모델들을 대상으로 세 가지 주요 과제(분자 편집, 분자 최적화, 맞춤형 분자 생성)에 대한 가중 평균 정확도를 나타냅니다.  각 모델의 성능을 가중 평균 정확도(wAcc)를 사용하여 비교하며,  오픈소스 모델과 독점 모델 간의 성능 차이를 보여줍니다.  특히, Instruction Tuning 데이터셋을 사용한 Llama-3.1-8B 모델의 성능 향상이 두드러지게 나타납니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Leaderboard of TOMG-Benchmark.
> </details>

{{< table-caption >}}
| Models | AddComponent |  |  | DelComponent |  |  | SubComponent |  |  |
|---|---|---|---|---|---|---|---|---|---|---|
|  | Accuracy | Similarity | Validity | Accuracy | Similarity | Validity | Accuracy | Similarity | Validity |
|---|---|---|---|---|---|---|---|---|---|---|
| GPT-4o <cite class="ltx_cite ltx_citemacro_cite">Achiam et al. (<a class="ltx_ref" href="https://arxiv.org/html/2412.14642v1#bib.bib1" title="">2023</a>)</cite> | 0.6188 | 0.6782 | 0.7412 | 0.7012 | 0.6038 | 0.8474 | 0.7992 | 0.7225 | 0.9368 |
| GPT-4-turbo <cite class="ltx_cite ltx_citemacro_cite">Achiam et al. (<a class="ltx_ref" href="https://arxiv.org/html/2412.14642v1#bib.bib1" title="">2023</a>)</cite> | 0.699 | 0.6936 | 0.7934 | 0.7244 | 0.5735 | 0.906 | 0.7778 | 0.7323 | 0.916 |
| GPT-3.5-turbo <cite class="ltx_cite ltx_citemacro_cite">Achiam et al. (<a class="ltx_ref" href="https://arxiv.org/html/2412.14642v1#bib.bib1" title="">2023</a>)</cite> | 0.5832 | 0.6545 | 0.798 | 0.3082 | 0.7797 | 0.8468 | 0.2918 | 0.6333 | 0.6822 |
| Claude-3.5 <cite class="ltx_cite ltx_citemacro_cite">Anthropic (<a class="ltx_ref" href="https://arxiv.org/html/2412.14642v1#bib.bib3" title="">2024b</a>)</cite> | 0.6832 | 0.7017 | 0.4414 | 0.5414 | 0.6678 | 0.796 | 0.8104 | 0.731 | 0.9588 |
| Claude-3 <cite class="ltx_cite ltx_citemacro_cite">Anthropic (<a class="ltx_ref" href="https://arxiv.org/html/2412.14642v1#bib.bib2" title="">2024a</a>)</cite> | 0.6766 | 0.684 | 0.818 | 0.5556 | 0.6408 | 0.8984 | 0.655 | 0.7159 | 0.9184 |
| Gemini-1.5-pro <cite class="ltx_cite ltx_citemacro_cite">Deepmind (<a class="ltx_ref" href="https://arxiv.org/html/2412.14642v1#bib.bib9" title="">2024</a>)</cite> | 0.7058 | 0.6792 | 0.8254 | 0.759 | 0.5949 | 0.9158 | 0.7148 | 0.7139 | 0.8684 |
| Llama3-70B-Instruct (Int4) <cite class="ltx_cite ltx_citemacro_cite">Dubey et al. (<a class="ltx_ref" href="https://arxiv.org/html/2412.14642v1#bib.bib11" title="">2024</a>)</cite> | 0.5198 | 0.6801 | 0.5922 | 0.6122 | 0.5637 | 0.7182 | 0.5094 | 0.717 | 0.6822 |
| Llama3-8B-Instruct <cite class="ltx_cite ltx_citemacro_cite">Dubey et al. (<a class="ltx_ref" href="https://arxiv.org/html/2412.14642v1#bib.bib11" title="">2024</a>)</cite> | 0.3914 | 0.6649 | 0.5374 | 0.4348 | 0.5058 | 0.57 | 0.2602 | 0.6841 | 0.4838 |
| Llama3.1-8B-Instruct <cite class="ltx_cite ltx_citemacro_cite">Dubey et al. (<a class="ltx_ref" href="https://arxiv.org/html/2412.14642v1#bib.bib11" title="">2024</a>)</cite> | 0.2992 | 0.6088 | 0.4954 | 0.4336 | 0.5257 | 0.591 | 0.3401 | 0.6424 | 0.5076 |
| Mistral-7B-Instruct-v0.2 <cite class="ltx_cite ltx_citemacro_cite">Jiang et al. (<a class="ltx_ref" href="https://arxiv.org/html/2412.14642v1#bib.bib18" title="">2023</a>)</cite> | 0.1868 | 0.6251 | 0.376 | 0.2018 | 0.3774 | 0.359 | 0.0602 | 0.6227 | 0.355 |
| Qwen2-7B-Instruct <cite class="ltx_cite ltx_citemacro_cite">Yang et al. (<a class="ltx_ref" href="https://arxiv.org/html/2412.14642v1#bib.bib43" title="">2024</a>)</cite> | 0.001 | 0.2527 | 0.0036 | 0.0006 | 0.4024 | 0.0012 | 0.0004 | 0.2895 | 0.0068 |
| Yi-1.5-9B <cite class="ltx_cite ltx_citemacro_cite">Young et al. (<a class="ltx_ref" href="https://arxiv.org/html/2412.14642v1#bib.bib44" title="">2024</a>)</cite> | 0.1742 | 0.417 | 0.4216 | 0.2858 | 0.5936 | 0.4909 | 0.137 | 0.4619 | 0.4368 |
| Chatglm-9B <cite class="ltx_cite ltx_citemacro_cite">GLM et al. (<a class="ltx_ref" href="https://arxiv.org/html/2412.14642v1#bib.bib15" title="">2024</a>)</cite> | 0.2932 | 0.7622 | 0.5686 | 0.2956 | 0.7494 | 0.6914 | 0.1498 | 0.715 | 0.5084 |
| Llama-3.2-1B-Instruct <cite class="ltx_cite ltx_citemacro_cite">Dubey et al. (<a class="ltx_ref" href="https://arxiv.org/html/2412.14642v1#bib.bib11" title="">2024</a>)</cite> | 0.0374 | 0.5343 | 0.1982 | 0.0768 | 0.575 | 0.3028 | 0.0102 | 0.3671 | 0.1468 |
| MolT5-small <cite class="ltx_cite ltx_citemacro_cite">Edwards et al. (<a class="ltx_ref" href="https://arxiv.org/html/2412.14642v1#bib.bib12" title="">2022</a>)</cite> | 0.122 | 0.1027 | 0.449 | 0.1598 | 0.1125 | 0.4504 | 0.0708 | 0.1029 | 0.4876 |
| MolT5-base <cite class="ltx_cite ltx_citemacro_cite">Edwards et al. (<a class="ltx_ref" href="https://arxiv.org/html/2412.14642v1#bib.bib12" title="">2022</a>)</cite> | 0.1354 | 0.1066 | 0.4686 | 0.1562 | 0.1144 | 0.4472 | 0.0584 | 0.1028 | 0.4426 |
| MolT5-large <cite class="ltx_cite ltx_citemacro_cite">Edwards et al. (<a class="ltx_ref" href="https://arxiv.org/html/2412.14642v1#bib.bib12" title="">2022</a>)</cite> | 0.2834 | 0.1084 | 0.9282 | 0.2228 | 0.1201 | 0.9198 | 0.1692 | 0.0932 | 0.941 |
| BioT5-base <cite class="ltx_cite ltx_citemacro_cite">Pei et al. (<a class="ltx_ref" href="https://arxiv.org/html/2412.14642v1#bib.bib31" title="">2023</a>)</cite> | 0.3462 | 0.1567 | 1 | 0.1668 | 0.1597 | 1 | 0.0684 | 0.1576 | 0.9998 |
| OpenMolIns-large (Llama-3.2-1B) | 0.1756 | 0.5676 | 0.3216 | 0.1816 | 0.4963 | 0.2466 | 0.0844 | 0.5415 | 0.2958 |
| OpenMolIns-large (Llama-3.1-8B) | 0.5822 | 0.6541 | 0.673 | 0.5104 | 0.5074 | 0.6896 | 0.544 | 0.6258 | 0.84 |
| OpenMolIns-light (Galactica-125M) | 0.3786 | 0.5958 | 0.3786 | 0.2062 | 0.6521 | 0.7048 | 0.3102 | 0.5879 | 0.6674 |
| OpenMolIns-small (Galactica-125M) | 0.3472 | 0.6172 | 0.5356 | 0.3258 | 0.6025 | 0.5758 | 0.2692 | 0.6181 | 0.5692 |
| OpenMolIns-medium (Galactica-125M) | 0.4736 | 0.5682 | 0.7442 | 0.4886 | 0.5184 | 0.7488 | 0.3282 | 0.5975 | 0.6958 |
| OpenMolIns-large (Galactica-125M) | 0.5866 | 0.5876 | 0.8228 | 0.6078 | 0.5577 | 0.7934 | 0.3438 | 0.6491 | 0.8438 |
| OpenMolIns-xlarge (Galactica-125M) | 0.5842 | 0.5859 | 0.8438 | 0.6526 | 0.5084 | 0.8286 | 0.1872 | 0.6024 | 0.8538 |{{< /table-caption >}}
> 🔼 표 11은 논문의 MolEdit 섹션에 대한 결과를 보여줍니다.  MolEdit 섹션은 분자 편집 작업을 다루며, AddComponent(구성 요소 추가), DelComponent(구성 요소 제거), SubComponent(구성 요소 대체) 세 가지 하위 작업으로 구성됩니다. 표는 각 하위 작업에 대해 모델의 정확도(Accuracy), 유사도(Similarity), 유효성(Validity) 세 가지 지표를 제시합니다.  가장 높은 정확도를 달성한 모델은 굵게 표시되고, 두 번째로 높은 정확도를 달성한 모델은 밑줄이 그어져 있습니다. 이를 통해 각 모델의 분자 편집 능력을 비교 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 11: Results on MolEdit. For each task, we highlight the best accuracy and underline the second best accuracy.
> </details>

{{< table-caption >}}
| Models | LogP Accuracy | LogP Similarity | LogP Validity | MR Accuracy | MR Similarity | MR Validity | QED Accuracy | QED Similarity | QED Validity |
|---|---|---|---|---|---|---|---|---|---| 
| GPT-4o [Achiam et al. (2023)](https://arxiv.org/html/2412.14642v1#bib.bib1) | 0.719 | 0.6586 | 0.8796 | 0.6864 | 0.642 | 0.8352 | 0.3952 | 0.618 | 0.857 |
| GPT-4-turbo [Achiam et al. (2023)](https://arxiv.org/html/2412.14642v1#bib.bib1) | 0.7662 | 0.6984 | 0.9048 | 0.7388 | 0.6821 | 0.8848 | 0.3946 | 0.6587 | 0.905 |
| GPT-3.5-turbo [Achiam et al. (2023)](https://arxiv.org/html/2412.14642v1#bib.bib1) | 0.4048 | 0.6327 | 0.854 | 0.412 | 0.6263 | 0.8486 | 0.3316 | 0.5635 | 0.8354 |
| Claude-3.5 [Anthropic (2024b)](https://arxiv.org/html/2412.14642v1#bib.bib3) | 0.797 | 0.7124 | 0.9422 | 0.6962 | 0.7112 | 0.911 | 0.5361 | 0.7042 | 0.8604 |
| Claude-3 [Anthropic (2024a)](https://arxiv.org/html/2412.14642v1#bib.bib2) | 0.7984 | 0.6067 | 0.9096 | 0.6094 | 0.6398 | 0.9062 | 0.4678 | 0.5855 | 0.9044 |
| Gemini-1.5-pro [Deepmind (2024)](https://arxiv.org/html/2412.14642v1#bib.bib9) | 0.7712 | 0.7022 | 0.9274 | 0.7876 | 0.6744 | 0.8926 | 0.4704 | 0.6077 | 0.9484 |
| Llama3-70B-Instruct (Int4) [Dubey et al. (2024)](https://arxiv.org/html/2412.14642v1#bib.bib11) | 0.5984 | 0.6028 | 0.6482 | 0.5684 | 0.6032 | 0.6272 | 0.2774 | 0.4828 | 0.634 |
| Llama3-8B-Instruct [Dubey et al. (2024)](https://arxiv.org/html/2412.14642v1#bib.bib11) | 0.4642 | 0.3658 | 0.6086 | 0.4332 | 0.4793 | 0.5704 | 0.2568 | 0.4547 | 0.6112 |
| Llama3.1-8B-Instruct [Dubey et al. (2024)](https://arxiv.org/html/2412.14642v1#bib.bib11) | 0.399 | 0.4235 | 0.5122 | 0.4164 | 0.483 | 0.5238 | 0.2655 | 0.4499 | 0.6158 |
| Mistral-7B-Instruct-v0.2 [Jiang et al. (2023)](https://arxiv.org/html/2412.14642v1#bib.bib18) | 0.222 | 0.4501 | 0.2802 | 0.1908 | 0.2578 | 0.3795 | 0.121 | 0.3244 | 0.2532 |
| Qwen2-7B-Instruct [Yang et al. (2024)](https://arxiv.org/html/2412.14642v1#bib.bib43) | 0 | 0.2923 | 0.0004 | 0.0002 | 0.4123 | 0.0004 | 0 | 0 | 0 |
| Yi-1.5-9B | 0.2884 | 0.5461 | 0.4927 | 0.205 | 0.3724 | 0.4126 | 0.1064 | 0.6596 | 0.4526 |
| Chatglm-9B | 0.3666 | 0.6902 | 0.4736 | 0.3514 | 0.682 | 0.5 | 0.1832 | 0.6506 | 0.4342 |
| Llama-3.2-1B-Instruct [Dubey et al. (2024)](https://arxiv.org/html/2412.14642v1#bib.bib11) | 0.0644 | 0.5055 | 0.1664 | 0.0822 | 0.441 | 0.1604 | 0.0714 | 0.4757 | 0.1796 |
| MolT5-small | 0.2158 | 0.1052 | 0.4302 | 0.2316 | 0.1011 | 0.442 | 0.2214 | 0.1031 | 0.4326 |
| MolT5-base | 0.2074 | 0.1051 | 0.4168 | 0.1856 | 0.1073 | 0.3796 | 0.2358 | 0.1054 | 0.4536 |
| MolT5-large | 0.4244 | 0.1015 | 0.8156 | 0.4496 | 0.1072 | 0.8678 | 0.4654 | 0.119 | 0.9214 |
| BioT5-base | 0.5158 | 0.1526 | 1 | 0.506 | 0.1597 | 1 | 0.5068 | 0.158 | 1 |
| OpenMolIns-large (Llama-3.2-1B) | 0.2898 | 0.5951 | 0.385 | 0.2644 | 0.5956 | 0.3678 | 0.1996 | 0.5849 | 0.349 |
| OpenMolIns-large (Llama-3.1-8B) | 0.8054 | 0.6678 | 0.872 | 0.7122 | 0.6548 | 0.8514 | 0.5224 | 0.6398 | 0.8802 |
| OpenMolIns-light (Galactica-125M) | 0.3202 | 0.6547 | 0.6416 | 0.3508 | 0.6435 | 0.6358 | 0.269 | 0.6521 | 0.638 |
| OpenMolIns-small (Galactica-125M) | 0.4172 | 0.642 | 0.5568 | 0.3958 | 0.6452 | 0.5338 | 0.2956 | 0.6385 | 0.5376 |
| OpenMolIns-medium (Galactica-125M) | 0.5904 | 0.5812 | 0.789 | 0.5874 | 0.5873 | 0.7384 | 0.4608 | 0.5859 | 0.7768 |
| OpenMolIns-large (Galactica-125M) | 0.6454 | 0.5927 | 0.8198 | 0.6388 | 0.5973 | 0.8028 | 0.495 | 0.5962 | 0.81 |
| OpenMolIns-xlarge (Galactica-125M) | 0.7362 | 0.5744 | 0.8902 | 0.7124 | 0.5697 | 0.8612 | 0.5786 | 0.5677 | 0.8626 |{{< /table-caption >}}
> 🔼 표 12는 논문의 MolOpt 섹션에 있는 결과표입니다. 이 표는 MolOpt 작업(분자 최적화)에 대한 다양한 모델의 성능을 보여줍니다.  각 하위 작업(LogP, MR, QED 최적화)에 대해 모델의 정확도, 유사도, 유효성을 보여주는 세 가지 지표가 있습니다.  가장 높은 정확도는 강조 표시되고, 두 번째로 높은 정확도는 밑줄이 그어져 있습니다. 이를 통해 각 모델이 분자의 특정 특성을 얼마나 잘 최적화하는지 비교할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 12: Results on MolOpt. For each task, we highlight the best accuracy and underline the second best accuracy.
> </details>

{{< table-caption >}}
| Models | AtomNum |  |  | BondNum |  |  | FunctionalGroup |  |  |
|---|---|---|---|---|---|---|---|---|---|---| 
|  | Accuracy | Novelty | Validity | Accuracy | Novelty | Validity | Accuracy | Novelty | Validity |
|---|---|---|---|---|---|---|---|---|---|---|
| GPT-4o <cite class="ltx_cite ltx_citemacro_cite">Achiam et al. (2023)</cite> | **0.1998** | 0.6703 | 0.5852 | 0.065 | 0.6336 | 0.8564 | 0.233 | 0.6513 | 0.859 |
| GPT-4-turbo <cite class="ltx_cite ltx_citemacro_cite">Achiam et al. (2023)</cite> | 0.1702 | 0.6991 | 0.4904 | 0.0774 | 0.6301 | 0.9068 | 0.218 | 0.6605 | 0.8778 |
| GPT-3.5-turbo <cite class="ltx_cite ltx_citemacro_cite">Achiam et al. (2023)</cite> | 0.107 | 0.5054 | 0.6947 | 0.0518 | 0.6871 | 0.5522 | 0.1136 | 0.6585 | 0.8686 |
| Claude-3.5 <cite class="ltx_cite ltx_citemacro_cite">Anthropic (2024b)</cite> | **0.1928** | 0.6926 | 0.6548 | **0.1058** | 0.6584 | 0.886 | **0.2364** | 0.6582 | 0.8892 |
| Claude-3 <cite class="ltx_cite ltx_citemacro_cite">Anthropic (2024a)</cite> | 0.1044 | 0.6833 | 0.591 | 0.1042 | 0.6598 | 0.8696 | 0.1816 | 0.9158 | 0.6644 |
| Gemini-1.5-pro <cite class="ltx_cite ltx_citemacro_cite">Deepmind (2024)</cite> | 0.1742 | 0.6902 | 0.6774 | 0.0708 | 0.6522 | 0.8688 | **0.2486** | 0.6673 | 0.924 |
| Llama3-70B-Instruct (Int4) <cite class="ltx_cite ltx_citemacro_cite">Dubey et al. (2024)</cite> | 0.1404 | 0.6675 | 0.5474 | 0.067 | 0.6478 | 0.7378 | 0.1752 | 0.6576 | 0.765 |
| Llama3-8B-Instruct <cite class="ltx_cite ltx_citemacro_cite">Dubey et al. (2024)</cite> | 0.0242 | 0.6649 | 0.3812 | 0.026 | 0.6303 | 0.57 | 0.0848 | 0.6167 | 0.7216 |
| Llama3.1-8B-Instruct <cite class="ltx_cite ltx_citemacro_cite">Dubey et al. (2024)</cite> | 0.0228 | 0.702 | 0.3862 | 0.0395 | 0.6541 | 0.6387 | 0.13 | 0.6274 | 0.6905 |
| Mistral-7B-Instruct-v0.2 <cite class="ltx_cite ltx_citemacro_cite">Jiang et al. (2023)</cite> | 0.0078 | 0.6732 | 0.2986 | 0.0102 | 0.6309 | 0.4524 | 0.0048 | 0.6012 | 0.402 |
| Qwen2-7B-Instruct <cite class="ltx_cite ltx_citemacro_cite">Yang et al. (2024)</cite> | 0.011 | 0.9061 | 0.2622 | 0.001 | 0.8645 | 0.0796 | 0.0022 | 0.8601 | 0.0622 |
| Yi-1.5-9B <cite class="ltx_cite ltx_citemacro_cite">Young et al. (2024)</cite> | 0.0392 | 0.6848 | 0.617 | 0.0208 | 0.6407 | 0.7072 | 0.0126 | 0.6945 | 0.6521 |
| Chatglm-9B <cite class="ltx_cite ltx_citemacro_cite">GLM et al. (2024)</cite> | 0.0002 | 0.7483 | 0.2131 | 0.0254 | 0.7189 | 0.4682 | 0 | 0.6908 | 0.5926 |
| Llama-3.2-1B-Instruct <cite class="ltx_cite ltx_citemacro_cite">Dubey et al. (2024)</cite> | 0.004 | 0.6807 | 0.185 | 0.008 | 0.7465 | 0.2226 | 0.0008 | 0.7461 | 0.2818 |
| MolT5-small <cite class="ltx_cite ltx_citemacro_cite">Edwards et al. (2022)</cite> | 0.0006 | 0.6586 | 0.661 | 0.0064 | 0.598 | 0.6202 | 0.0114 | 0.5287 | 0.8354 |
| MolT5-base <cite class="ltx_cite ltx_citemacro_cite">Edwards et al. (2022)</cite> | 0.0008 | 0.6868 | 0.756 | 0.007 | 0.6509 | 0.8422 | 0.013 | 0.5464 | 0.8382 |
| MolT5-large <cite class="ltx_cite ltx_citemacro_cite">Edwards et al. (2022)</cite> | 0.015 | 0.7103 | 0.8412 | 0.0118 | 0.5611 | 0.8916 | 0.0382 | 0.6088 | 0.9406 |
| BioT5-base <cite class="ltx_cite ltx_citemacro_cite">Pei et al. (2023)</cite> | 0.0118 | 0.8353 | 0.995 | 0.0078 | 0.6667 | 0.9992 | 0.0476 | 0.6792 | 0.9998 |
| OpenMolIns-large (LLama-3.2-1B) | 0.0144 | 0.649 | 0.5616 | 0.035 | 0.615 | 0.6186 | 0.0252 | 0.6373 | 0.4412 |
| OpenMolIns-large (LLama-3.1-8B) | 0.0136 | 0.6634 | 0.7582 | 0.0544 | 0.6614 | 0.7456 | 0.1344 | 0.6396 | 0.6435 |
| OpenMolIns-light (Galactica-125M) | 0.0044 | 0.6054 | 0.793 | 0.0216 | 0.5724 | 0.7596 | 0.0244 | 0.5756 | 0.8442 |
| OpenMolIns-small (Galactica-125M) | 0.0146 | 0.6568 | 0.8424 | 0.053 | 0.6365 | 0.7926 | 0.057 | 0.5954 | 0.8874 |
| OpenMolIns-medium (Galactica-125M) | 0.0294 | 0.6553 | 0.8698 | 0.0622 | 0.6473 | 0.7474 | 0.0882 | 0.6091 | 0.8932 |
| OpenMolIns-large (Galactica-125M) | 0.0464 | 0.6729 | 0.9116 | 0.0716 | 0.6695 | 0.7374 | 0.0996 | 0.6276 | 0.8966 |
| OpenMolIns-xlarge (Galactica-125M) | 0.1862 | 0.6899 | 0.9308 | **0.1656** | 0.6887 | 0.7952 | 0.2006 | 0.6445 | 0.9162 |{{< /table-caption >}}
> 🔼 표 13은 논문의 MolCustom 작업에 대한 결과를 보여줍니다.  MolCustom 작업은 사용자 정의 분자 생성 작업으로, 원자 수, 결합 수, 작용기 등을 지정하여 분자를 생성하는 과제입니다. 이 표는 각 하위 작업(AtomNum, BondNum, FunctionalGroup)에 대해 여러 모델들의 정확도, 참신성, 유효성을 나타냅니다.  가장 높은 정확도를 달성한 모델은 각 하위 작업마다 강조 표시되어 있으며, 두 번째로 높은 정확도를 달성한 모델은 밑줄이 그어져 있습니다. 이를 통해 다양한 LLM 모델들의 분자 생성 능력을 비교 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 13: Results on MolCustom. For each task, we highlight the best accuracy and underline the second best accuracy.
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