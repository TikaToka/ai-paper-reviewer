---
title: "$\text{Transformer}^2$: Self-adaptive LLMs"
summary: "Transformer²: 실시간 자가 적응형 LLM 프레임워크, 제한된 매개변수로 다양한 작업에 효율적 적응"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Sakana AI, Japan",]
showSummary: true
date: 2025-01-09
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.06252 {{< /keyword >}}
{{< keyword icon="writer" >}} Qi Sun et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-14 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.06252" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.06252" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/text-transformer-2-self-adaptive-llms" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 대규모 언어 모델(LLM) 미세 조정 방법은 계산 비용이 많이 들고, 다양한 작업에 대한 적응력이 부족하다는 문제점이 있습니다. 특히, 새로운 작업에 대한 적응을 위해서는 모델 전체를 다시 훈련해야 하므로, 시간과 자원 낭비가 심각합니다.  또한, 기존의 방법들은 모델의 크기가 커질수록 효율성이 떨어지는 문제가 있습니다.

본 논문에서는 이러한 문제점들을 해결하기 위해, **Transformer²라는 새로운 자가 적응형 LLM 프레임워크**를 제시합니다.  Transformer²는 **Singular Value Fine-tuning(SVF)**이라는 새로운 매개변수 효율적인 미세 조정(PEFT) 방법과 강화 학습(RL)을 활용하여, LLM의 가중치 행렬의 특이값만을 조정함으로써,  **실시간으로 다양한 작업에 적응**할 수 있도록 합니다.  실험 결과, Transformer²는 기존 방법들보다 적은 매개변수로 더 높은 성능을 달성하며, 다양한 LLM 아키텍처와 모달리티에서도 우수한 성능을 보여줍니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} Transformer²는 가중치 행렬의 특이값만을 선택적으로 조정하여 LLM을 실시간으로 미세 조정하는 새로운 자가 적응형 프레임워크 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} Singular Value Fine-tuning(SVF)는 기존의 미세 조정 방법보다 매개변수가 적고, 과적합 위험이 낮으며, 구성 가능성이 높음 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 강화 학습을 통해 훈련된 전문가 벡터를 역할에 따라 동적으로 결합하는 세 가지 적응 전략 제시 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **실시간으로 다양한 작업에 적응하는 자가 적응형 대규모 언어 모델(LLM)**을 개발하고자 하는 연구자들에게 매우 중요합니다. 기존의 미세 조정 방법의 한계를 극복하고, 효율성과 확장성을 동시에 달성하는 새로운 프레임워크를 제시함으로써, **동적이고 자가 조직화된 AI 시스템** 개발의 가능성을 열어줍니다. 특히, 제한된 매개변수로 성능을 향상시키는 **매개변수 효율적인 미세 조정(PEFT)** 방법과 강화 학습을 활용한 새로운 접근 방식은 관련 분야 연구에 혁신적인 영향을 미칠 것으로 예상됩니다.  또한, 다양한 LLM 아키텍처와 모달리티에 대한 실험 결과는 제안된 프레임워크의 범용성을 보여주고, 향후 연구를 위한 새로운 방향을 제시합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.06252/x1.png)

> 🔼 그림 1은 Transformer²의 개요를 보여줍니다. 훈련 단계에서는 가중치 행렬의 특이값 배율을 조정하여 각각 특정 유형의 작업에 특화된 '전문가' 벡터 집합을 생성합니다. 추론 단계에서는 먼저 작업별 전문가를 적용한 다음 답변을 생성하는 두 단계 프로세스가 채택됩니다.  이 그림은 Transformer²의 작동 방식을 시각적으로 설명하며, 훈련 과정에서 특이값 조정을 통해 전문가 벡터를 생성하고, 추론 과정에서 두 단계(작업 식별 및 답변 생성)를 거치는 과정을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Overview of Transformer2superscriptTransformer2\text{Transformer}^{2}Transformer start_POSTSUPERSCRIPT 2 end_POSTSUPERSCRIPT. In the training phase, we tune the scales of the singular values of the weight matrices to generate a set of “expert” vectors, each of which specializes in one type of tasks. In the inference phase, a two-pass process is adopted where the first applies the task-specific expert and the second generates the answer.
> </details>





{{< table-caption >}}
| Method | GSM8K | MBPP-Pro | ARC-Easy |
|---|---|---|---| 
| Llama3-8B-Instruct | 75.89 (1.00) | 64.65 (1.00) | 88.59 (1.00) |
| + LoRA | 77.18 (1.02) | 67.68 (1.05) | 88.97 (1.00) |
| + SVF (Ours) | 79.15 (1.04) | 66.67 (1.03) | 89.56 (1.01) |
| Mistral-7B-Instruct-v0.3 | 42.83 (1.00) | 49.50 (1.00) | 81.65 (1.00) |
| + LoRA | 44.66 (1.04) | 51.52 (1.04) | 81.19 (0.98) |
| + SVF (Ours) | 49.74 (1.16) | 51.52 (1.04) | 85.14 (1.04) |
| Llama3-70B-Instruct | 85.29 (1.00) | 80.81 (1.00) | 89.10 (1.00) |
| + LoRA | 77.26 (0.91) | 68.69 (0.85) | 88.55 (0.99) |
| + SVF (Ours) | 88.32 (1.04) | 80.81 (1.00) | 88.47 (0.99) |{{< /table-caption >}}

> 🔼 표 1은 세 가지 과제(수학, 코딩, 추론)에 대한 세 가지 대규모 언어 모델(LLM)의 성능을 보여줍니다. 각 LLM에 대해 기본 성능과 LoRA 및 SVF(Singular Value Fine-tuning) 기술을 사용하여 미세 조정한 후의 성능이 표시됩니다. 괄호 안의 점수는 정규화된 점수이며, 기본 모델의 성능을 1.00으로 하여 상대적인 성능 향상을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Fine-tuning results. LLM performance on the test splits of math, coding and reasoning. Normalized scores are in the parentheses.
> </details>





### In-depth insights


#### Adaptive LLMs
적응형 거대 언어 모델(LLM)은 **다양한 작업에 대한 실시간 적응성**을 제공하여 기존의 정적 미세 조정 방법의 한계를 극복하는 것을 목표로 합니다. 이는 **계산 비용이 많이 들고 유연성이 부족한** 기존 방법과 대조됩니다.  **실시간 적응성**은 모델의 가중치 행렬 내 특정 구성 요소만을 선택적으로 조정하여 달성됩니다.  **전이 학습**과 **강화 학습**을 통해 사전 훈련된 전문가 벡터를 활용하여 효율성을 높입니다.  이러한 전문가 벡터는 작업 속성을 식별하고 들어오는 프롬프트에 대한 목표 동작을 얻기 위해 동적으로 혼합됩니다. 이러한 접근 방식은 매개변수 효율성, 즉 적은 매개변수로 높은 성능을 달성하고, 다양한 LLM 아키텍처와 모달리티에서의 다양성을 제공하여 기존 방법보다 우수한 성능을 보입니다. **자기 조직화 AI 시스템**으로 가는 길을 열어 줄 잠재력을 지닌 **확장 가능하고 효율적인 솔루션**을 제시합니다.

#### SVF: A PEFT Method
본 논문에서 제시된 **Singular Value Fine-tuning (SVF)**는 기존의 파라미터 효율적인 미세 조정(PEFT) 방법들의 한계를 극복하기 위한 새로운 방법입니다. 기존의 방법들은 계산 비용이 많이 들고 과적합의 위험이 높다는 단점이 있었지만, **SVF는 가중치 행렬 내 특이값만 추출하고 조정함으로써 과적합을 방지하고 계산 효율성을 높입니다.**  이는 **매우 적은 수의 파라미터로 효과적인 빌딩 블록을 얻을 수 있게 해주며,** 다양한 LLM 아키텍처와 모달리티에서도 적용 가능하다는 장점이 있습니다.  특히, 강화 학습을 이용하여 도메인 특정 “전문가” 벡터를 효율적으로 훈련하여 개별 주제에 대한 성능을 최적화할 수 있게 합니다.  **SVF의 주요 특징은 계산 효율성, 과적합 방지, 그리고 구성 가능성**입니다.  이러한 특징들은 Transformer² 프레임워크의 핵심 구성 요소로서,  LLM의 적응성과 특정 작업에 대한 성능 향상에 크게 기여합니다.

#### Transformer2
Transformer2는 기존의 LLMs의 한계를 극복하기 위해 **실시간으로 자가 적응하는 새로운 프레임워크**를 제시합니다. 기존의 파인튜닝 방식의 계산 비용과 유연성 부족 문제를 해결하고자, 가중치 행렬의 특이값만을 선택적으로 조정하여 실시간으로 미지의 작업에 적응하는 **효율적인 메커니즘**을 사용합니다. 특히, 강화학습을 통해 훈련된 작업별 전문가 벡터를 역동적으로 혼합하여 원하는 동작을 얻는 **두 단계 접근 방식**을 채택하고 있습니다. 이는 기존의 LoRA와 같은 방법보다 적은 파라미터로 더 높은 효율성을 달성합니다. 다양한 LLM 아키텍처와 모달리티에 적용 가능하며, 비전-언어 작업에서도 뛰어난 성능을 보여줍니다. **자가 조직화 AI 시스템**으로 가는 중요한 발걸음이 될 것으로 기대됩니다.

#### RL-Based Training
본 논문에서 제시된 강화 학습 기반 훈련 방법은 **매개변수 효율적인 미세 조정(PEFT)** 방법으로, 기존의 대규모 언어 모델(LLM)의 가중치 행렬을 직접 조정하는 대신 특정 작업에 대한 전문가 벡터를 학습하는 데 중점을 둡니다. 이는 과적합 위험을 줄이고 계산 비용을 절감하며 **모듈성**을 높이는 데 효과적입니다. 특히, **특이값 미세 조정(SVF)** 기법을 통해 가중치 행렬의 특이값만을 선택적으로 조정함으로써, 적은 매개변수로도 우수한 성능을 달성할 수 있습니다.  강화 학습은 전문가 벡터를 훈련하는 데 사용되며, 이는 다양한 작업에 대한 모델의 적응력을 높이는 데 기여합니다.  **강화학습 기반 훈련의 핵심은 효율성과 적응력의 균형**을 이루는 것입니다.  전문가 벡터는 오프라인으로 훈련되어 실시간으로 모델에 추가되므로, 새로운 작업에 대한 재훈련 없이 동적으로 모델을 조정할 수 있습니다.  결과적으로, 이 방법은 자가 적응형 AI 시스템 구축을 위한 효율적이고 확장 가능한 솔루션을 제공합니다.

#### Future Work
본 논문은 자가 적응형 거대 언어 모델(LLM)에 대한 새로운 프레임워크인 Transformer²를 제시하며, **특히 파라미터 효율적인 미세 조정 기법인 SVF(Singular Value Fine-tuning)와 강화 학습을 결합하여 실시간으로 다양한 작업에 적응하는 모델을 구축**하는 데 중점을 두고 있습니다.  향후 연구 방향으로는 **SVF의 확장성 및 일반화 성능 개선**, **더욱 효율적인 적응 전략 개발**, 그리고 **다양한 모달리티 및 아키텍처에 대한 적용성 검증**이 제시될 수 있습니다.  **특히, CEM(Cross-Entropy Method) 기반의 몇몇 샷 학습 전략의 효율성을 높이는 방안**에 대한 연구가 필요하며, 다른 진화 알고리즘을 활용하여 더 나은 효율성과 수렴 속도를 달성하는 연구도 진행될 수 있습니다.  또한, **모델 병합 기술을 활용하여 특화된 모델들을 단일 모델로 통합**하는 연구를 통해 모델의 능력을 향상시키는 연구도 기대됩니다.  **다양한 크기의 모델에서의 성능 및 적용성을 평가**하고, **실제 응용 환경에서의 성능 및 안정성을 검증**하는 것 또한 중요한 과제입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.06252/extracted/6130084/images/cem_code.png)

> 🔼 그림 2는 Transformer²의 훈련 및 추론 과정을 개괄적으로 보여줍니다. 왼쪽 부분은 훈련 단계를 나타내며, 특이값 미세 조정(SVF)과 강화 학습(RL)을 사용하여 가중치 행렬의 특이값을 조정하는 '전문가' 벡터 z를 학습하는 과정을 보여줍니다. 오른쪽 부분은 추론 단계를 나타내며, 학습된 전문가 벡터를 적응적으로 선택하거나 결합하는 세 가지 방법을 제시합니다. 이를 통해 Transformer²는 다양한 작업에 실시간으로 적응할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Method overview. Left) At training time, we employ SVF and RL to learn the “expert” vectors z𝑧zitalic_z’s that scale the singular values of the weight matrices. Right) At inference time, we propose three distinct methods to adaptively select/combine the learned expert vectors.
> </details>



![](https://arxiv.org/html/2501.06252/x2.png)

> 🔼 그림 3은 Transformer²의 질의 분류를 위한 프롬프트 기반 적응 과정을 보여줍니다. Transformer²는 입력 프롬프트를 미리 정의된 범주(예: 코드, 수학, 추론, 기타)로 분류하기 위해 특수 설계된 프롬프트를 사용합니다.  이 프롬프트는 모델이 질문의 주요 초점, 필요한 기술 및 지식을 고려하여 질문을 적절한 범주로 분류하도록 안내합니다.  여러 범주에 걸쳐 있는 질문의 경우 가장 우세한 범주를 선택하도록 지시합니다.  이 그림은 Transformer²가 어떻게 질문을 분류하고, 해당 작업에 가장 적합한 전문가 벡터를 동적으로 선택하는지를 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Prompt based adaptation. Self-adaptation prompt used by Transformer2superscriptTransformer2\text{Transformer}^{2}Transformer start_POSTSUPERSCRIPT 2 end_POSTSUPERSCRIPT to classify the task prompt into pre-defined categories.
> </details>



![](https://arxiv.org/html/2501.06252/x3.png)

> 🔼 그림 4는 제안된 특이값 미세조정(SVF) 방법의 학습 곡선을 보여줍니다. 점선은 Llama3-8B-Instruct 모델의 각 과제에 대한 테스트 집합 성능을 나타내고, SVF는 기본 성능을 능가하도록 효과적으로 미세 조정합니다. 검증 점수를 기준으로 최적의 체크포인트를 선택하여 평가하지만, SVF의 학습 능력을 보여주기 위해 조기 중단 없이 전체 학습 곡선을 제시합니다. 코딩 및 추론과 같이 학습 샘플이 수백 개에 불과한 과제는 조기에 중단되었습니다. 실험에서는 각 에포크의 끝에서 매개변수를 업데이트했습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: SVF learning curves. The dashed lines indicate the performance of Llama3-8B-Instruct on the test split of each task. SVF effectively fine-tunes to surpass the base performance. While we use the best validation score to select our checkpoint for evaluation (marked by red dots), we present the entire training curve without early stopping to demonstrate SVF’s learning capabilities. Tasks with only hundreds of training samples like Coding and Reasoning were stopped early. In our experiments, we update the parameters at the end of each epoch.
> </details>



![](https://arxiv.org/html/2501.06252/x4.png)

> 🔼 그림 5는 Vision-Language Model(VLM) 영역에 대한 실험 결과를 보여줍니다.  Transformer² 프레임워크의 성능을 평가하기 위해,  LLAMA3-LLAVA-NEXT-8B 모델에 SVF(Singular Value Fine-tuning)를 적용하여 TextVQA(Text Visual Question Answering) 작업에 대한 성능 향상을 시각적으로 보여줍니다.  그림은 SVF를 사용했을 때의 성능 향상 정도를 보여주며, 기존 모델보다 얼마나 큰 성능 향상을 가져왔는지 보여주는 비교 결과를 담고 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Results for the VLM domain.
> </details>



![](https://arxiv.org/html/2501.06252/x5.png)

> 🔼 그림 6은 모델이 각 작업(수학, 코딩, 추론)을 분류한 결과를 보여주는 혼동 행렬입니다. 행은 실제 작업 유형을, 열은 모델이 예측한 작업 유형을 나타냅니다. 일부 샘플은 '기타'로 잘못 분류되었는데, 이는 행의 합계가 1이 아닌 경우에 반영됩니다. 이는 모델이 특정 작업을 다른 작업으로 잘못 분류하는 정도를 시각적으로 보여줍니다.  예를 들어, 수학 문제가 추론 문제로 잘못 분류된 비율 등을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Confusion matrices. These matrices display the classification percentages, where rows represent the task classes (ground truth) and columns indicate the predicted categories. Some samples are misclassified as “Others,” which is reflected in rows where the totals do not sum to one.
> </details>



![](https://arxiv.org/html/2501.06252/x6.png)

> 🔼 그림 7은 Transformer²의 세 가지 적응 전략(프롬프트 기반, 분류 전문가, 퓨샷)에서 각 작업에 대한 학습된 가중치(αk)를 보여줍니다.  각 막대는 특정 작업에 대한 각 전문가 벡터의 기여도를 나타내며, 더 높은 값은 해당 전문가 벡터가 특정 작업에 더 중요함을 의미합니다. 이 그림은 Transformer²가 다양한 작업에 대해 어떻게 다른 전문가 벡터를 동적으로 결합하는지 보여주는 시각적 표현입니다.  다양한 작업에 대한 적응 가중치의 분포를 통해 Transformer²의 적응 능력과 유연성을 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: 𝜶𝒌subscript𝜶𝒌\bm{\alpha_{k}}bold_italic_α start_POSTSUBSCRIPT bold_italic_k end_POSTSUBSCRIPT learned weights.
> </details>



![](https://arxiv.org/html/2501.06252/x7.png)

> 🔼 그림 8은 LoRA(Low-Rank Adaptation) 방식의 instruction fine-tuning을 위한 수학 문제 데이터 샘플을 보여줍니다.  파란색으로 표시된 텍스트는 답을 유추하는 데 사용되는, 미리 학습된 모델이 예측하지 못한 부분(unmasked solution)을 나타냅니다. 이 그림은 모델이 문제를 풀 때 어떤 방식으로 답을 도출하는지 보여주는 예시로, 본 논문의 '3.2 TRANSFORMER²' 섹션에서 Transformer² 모델의 학습 과정을 설명하기 위해 사용됩니다.  특히,  Singular Value Fine-tuning(SVF) 방법과 함께 RL(Reinforcement Learning)을 사용하여 모델을 학습시키는 과정에서 사용되는 데이터의 예시를 보여주는 것이 목적입니다. 그림을 통해,  Transformer²가 어떻게 제한된 정보(unmasked solution)로부터 효율적으로 학습하는지를 시각적으로 이해할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Sample problem and answer. Math data sample used for LoRA instruction fine-tuning, text in blue is the unmasked solution.
> </details>



![](https://arxiv.org/html/2501.06252/x8.png)

> 🔼 그림 9는 정책 경사도를 사용하여 LoRA를 학습시킨 결과를 보여줍니다. 점선은 Llama3-8B-Instruct 모델의 테스트 세트 성능을 나타냅니다. LoRA는 학습 초기 단계에서 성능이 급격히 저하되고 회복되지 않아 테스트 성능에 부정적인 영향을 미치는 것을 확인할 수 있습니다. 다양한 학습률(2×10⁻⁴, 5×10⁻⁴,…,2×10⁻², 5×10⁻²)을 시도했지만, 모든 학습 곡선이 그림에 제시된 것과 유사한 결과를 보였습니다. 이는 LoRA가 정책 경사도 기반 학습에 적합하지 않음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Training LoRA with policy gradient. The dashed line shows the performance of Llama3-8B-Instruct on the test split. LoRA collapses at the beginning of the training stage and fails to recover, leading to negative effects on test performance. We swept a wide range of learning rates (2×10−4,5×10−4,…,2×10−2,5×10−2)2superscript1045superscript104…21025superscript102(2\times 10^{-4},5\times 10^{-4},\dots,2\times 10{-2},5\times 10^{-2})( 2 × 10 start_POSTSUPERSCRIPT - 4 end_POSTSUPERSCRIPT , 5 × 10 start_POSTSUPERSCRIPT - 4 end_POSTSUPERSCRIPT , … , 2 × 10 - 2 , 5 × 10 start_POSTSUPERSCRIPT - 2 end_POSTSUPERSCRIPT ), and all learning curves were similar to the one presented.
> </details>



![](https://arxiv.org/html/2501.06252/x9.png)

> 🔼 그림 10은 Llama3-8B-Instruct 모델의 가중치 행렬에 대한 주성분 분석(PCA) 결과를 보여줍니다. y축은 상위 r개의 특이값 성분이 설명하는 분산 비율을 나타내고, x축은 계층 색인을 나타냅니다. Query, Key, Value 투영 행렬을 제외하고는, 작은 r 값은 파라미터 행렬 내 특이값의 분산을 거의 포착하지 못함을 보여줍니다.  즉, 모델의 가중치 행렬에서 상위 몇 개의 주성분만으로는 전체 정보를 충분히 설명할 수 없다는 것을 의미합니다. 특히 MLP 계층에서는 이러한 현상이 더욱 두드러집니다. 이는 저차원 근사 방법을 사용하는 기존의 매개변수 효율적인 미세 조정 기법(예: LoRA-XS)이 정보 손실 및 모델링 성능 저하를 초래할 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: PCA of Llama3-8B-Instruct. We show the ratio of the variance captured by the top r𝑟ritalic_r singular components on the y-axis, and the layer indices on the x-axis. Except for the Query, Key and Value projection matrices, small r𝑟ritalic_r values only capture a tiny fraction of variance in singular values in the parameter matrices.
> </details>



![](https://arxiv.org/html/2501.06252/x10.png)

> 🔼 그림 11은 MISTRAL-7B-Instruct-v0.3 모델의 가중치 행렬에 대한 주성분 분석(PCA) 결과를 보여줍니다. y축은 상위 r개의 특이값 성분이 설명하는 분산 비율을 나타내고, x축은 레이어 인덱스를 나타냅니다. Query, Key, Value projection 행렬을 제외하고, 작은 r 값은 가중치 행렬의 특이값 분산의 아주 작은 부분만을 설명합니다. 이는 SVF(Singular Value Fine-tuning) 방법이 모델의 가중치 행렬에서 중요한 정보를 담고 있는 상위 몇 개의 특이값에만 집중하여 효율적으로 미세 조정을 수행할 수 있음을 시사합니다. 그림은 각 레이어의 다양한 모듈(q_proj, k_proj, v_proj, o_proj, up_proj, gate_proj, down_proj)에 대해 PCA 결과를 보여줍니다.  각 모듈에서 상위 r개 특이값이 설명하는 분산 비율이 상대적으로 낮다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: PCA of Mistral-7B-Instruct-v0.3. We show the ratio of the variance captured by the top r𝑟ritalic_r singular components on the y-axis, and the layer indices on the x-axis. Except for the Query, Key and Value projection matrices, small r𝑟ritalic_r values only capture a tiny fraction of variance in singular values in the parameter matrices.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | MATH | Humaneval | ARC-Challenge |
|---|---|---|---|
| Llama3-8B-Instruct 3 | 24.54 (1.00) | 60.98 (1.00) | 80.63 (1.00) |
| + LoRA | 24.12 (0.98) | 52.44 (0.86) | 81.06 (1.01) |
| + Transformer<sup>2</sup> (Prompt) | 25.22 (1.03) | 61.59 (1.01) | 81.74 (1.01) |
| + Transformer<sup>2</sup> (Cls-expert) | 25.18 (1.03) | 62.80 (1.03) | 81.37 (1.01) |
| + Transformer<sup>2</sup> (Few-shot) | 25.47 (1.04) | 62.99 (1.03) | 82.61 (1.02) |
| Mistral-7B-Instruct-v0.3 | 13.02 (1.00) | 43.29 (1.00) | 71.76 (1.00) |
| + LoRA | 13.16 (1.01) | 37.80 (0.87) | 75.77 (1.06) |
| + Transformer<sup>2</sup> (Prompt) | 11.86 (0.91) | 43.90 (1.01) | 72.35 (1.01) |
| + Transformer<sup>2</sup> (Cls-expert) | 11.60 (0.89) | 43.90 (1.01) | 74.83 (1.04) |
| + Transformer<sup>2</sup> (Few-shot) | 13.39 (1.03) | 47.40 (1.09) | 75.47 (1.05) |
| Llama3-70B-Instruct | 40.64 (1.00) | 78.66 (1.00) | 87.63 (1.00) |
| + LoRA | 25.40 (0.62) | 73.78 (0.94) | 83.70 (0.96) |
| + Transformer<sup>2</sup> (Prompt) | 40.44 (1.00) | 79.88 (1.02) | 88.48 (1.01) |{{< /table-caption >}}
> 🔼 이 표는 Transformer² 모델의 자가 적응 능력을 보여줍니다.  기존에 학습되지 않은 네 가지 과제(MATH, Humaneval, ARC-Challenge, OKVQA)에 대해, Transformer²가 세 가지 다른 적응 전략(프롬프트 엔지니어링, 분류 전문가, 퓨샷 적응)을 사용하여 얼마나 잘 적응하는지 보여줍니다.  각 과제에 대한 정규화된 점수(괄호 안)를 제시하여, Transformer²의 성능을 기준 모델(LLAMA3-8B-INSTRUCT, MISTRAL-7B-INSTRUCT-V0.3, LLAMA3-70B-INSTRUCT) 및 LoRA 기준 모델과 비교합니다. 이를 통해 Transformer²의 자가 적응 성능과 다양한 적응 전략의 효과를 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Self-adaptation on unseen tasks. Normalized scores are in the parentheses.
> </details>

{{< table-caption >}}
| Task | 1st (s) | 2nd (s) |
|---|---|---|
| MATH | 42.64 (13%) | 321.19 |
| Humaneval | 2.76 (19%) | 14.28 |
| ARC-Challenge | 13.40 (47%) | 28.51 |{{< /table-caption >}}
> 🔼 이 표는 논문의 Transformer² 모델에서 프롬프트 적응 전략을 사용했을 때, 전체 문제 집합에 대한 2단계 추론의 시간 비용을 보여줍니다. 1차 추론은 문제의 유형을 파악하는 데, 2차 추론은 실제 문제 해결에 사용됩니다. 표에는 각 단계의 추론 시간과 1차 추론 시간 대비 2차 추론 시간의 비율이 괄호 안에 표시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Time cost of 2-pass inference in prompt adaptation strategy of Transformer2superscriptTransformer2\text{Transformer}^{2}Transformer start_POSTSUPERSCRIPT 2 end_POSTSUPERSCRIPT for the entire problem set. 1st to 2nd pass inference time ratios are shown in parentheses.
> </details>

{{< table-caption >}}
| # | Method | Objective Function | Module | #Params (↓) | GSM8K (↑) | MATH (↑) |
|---|---|---|---|---|---|---|
| 0 | LLAMA-3-8B-Instruct |  |  |  | 75.89 (1.00) | 24.54 (1.00) |
| 1 | SVF | Policy gradient | MLP | 0.39M | 78.62 (1.04) | 24.20 (0.99) |
| 2 | SVF | Policy gradient | attention | 0.16M | 76.19 (1.00) | 24.20 (0.99) |
| 3 | SVF | Policy gradient | MLP + attention | 0.58M | 79.23 (1.04) | 25.04 (1.04) |
| 4 | SVF | Next token pred | attention | 0.16M | 60.50 (0.80) | 18.52 (0.75) |
| 5 | LoRA | Policy gradient | attention | 6.82M | 57.92 (0.76) | 15.72 (0.64) |
| 6 | LoRA | Next token pred | attention | 6.82M | 77.18 (0.98) | 24.12 (0.96) |
| 7 | LoRA | Next token pred | MLP + attention | 35.13M | 75.66 (0.96) | 22.12 (0.91) |{{< /table-caption >}}
> 🔼 표 4는 Llama3-8B-Instruct 모델을 GSM8K 학습 데이터셋의 서로 다른 설정으로 미세 조정한 결과와, 미세 조정된 모델의 GSM8K 테스트셋 성능 및 MATH 데이터셋에 대한 제로샷 전이 성능을 보여줍니다. 미세 조정 설정에는 최적화 목적 함수(정책 경사 또는 다음 토큰 예측), 미세 조정 모듈(MLP, 어텐션 또는 둘 다), 매개변수 수 등이 포함됩니다. 이 표는 제안된 SVF 방법의 강건성과 효율성을 평가하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Ablation studies. We fine-tune Llama3-8B-Instruct on the GSM8K training split with different settings and the results on the test split along with zero-shot transfer results on MATH.
> </details>

{{< table-caption >}}
| Method | MATH | Humaneval | ARC-Challenge |
|---|---|---|---|
| _SVF training task_ | _GSM8K_ | _MBPP-pro_ | _ARC-Easy_ |
| Mistral-7B-Instruct-v0.3 | 13.02 (1.00) | 43.29 (1.00) | 71.76 (1.00) |
| + Llama SVF (ordered σ<sub>i</sub>) | 11.96 (0.92) | 45.12 (1.04) | 72.01 (1.00) |
| + Llama SVF (shuffled σ<sub>i</sub>) | 10.52 (0.81) | 40.24 (0.93) | 70.82 (0.99) |
| + Few-shot adaptation (cross-model) | 12.65 (0.97) | 46.75 (1.08) | 75.64 (1.05) |{{< /table-caption >}}
> 🔼 본 표는 Llama3-8B-Instruct 모델에서 학습된 전문가 벡터들을 Mistral-7B-Instruct-v0.3 모델에 전이 학습하는 실험 결과를 보여줍니다.  특히, 교차 모델 퓨샷 적응 기법을 사용하여 전이 학습을 수행했으며,  GSM8K, MBPP-pro, ARC-Easy 세 가지 과제에 대한 성능을 비교 분석합니다.  표에는 각 과제에 대한 기준 성능과 Llama3-8B-Instruct에서 학습된 벡터를 순서대로 적용했을 때, 순서를 섞어 적용했을 때, 그리고 교차 모델 퓨샷 적응을 적용했을 때의 성능 향상을 보여줍니다. 이를 통해 교차 모델 적응 전략의 효과성과 SVF 벡터의 일반화 성능을 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Cross-model z𝑧\bm{z}bold_italic_z vector transfer. Results from transferring the expert vectors trained on Llama3-8B-Instruct to Mistral-7B-Instruct-v0.3 with cross model few-shot adaptation.
> </details>

{{< table-caption >}}
| SVF Hyperparameters                                  |
|-------------------------------------------------------|
| Initial mean value of z                             | 0.1           |
| Initial variance value of z                          | $1 \times 10^{-3}$ |
| Global batch size                                    | 256           |
| Learning rate                                        | $2 \times 10^{-3}$ |
| Clip max norm                                         | $1 \times 10^{-3}$ |
| KL coefficient $\lambda$                            | 0.0, 0.1, 0.2, 0.3 |
| LoRA Hyperparameters                                 |
|-------------------------------------------------------|
| Rank                                                | 16            |
| LoRA alpha                                           | 32            |
| LoRA dropout                                         | 0.05          |
| Global batch size                                    | 256           |
| Learning rate                                        | $2 \times 10^{-4}$, $5 \times 10^{-4}$, $2 \times 10^{-5}$, $5 \times 10^{-5}$, $2 \times 10^{-6}$, $5 \times 10^{-6}$ |
| Clip max norm                                         | $1 \times 10^{-3}$, 1.0 |{{< /table-caption >}}
> 🔼 표 6은 SVF와 LoRA 학습에 사용된 하이퍼파라미터들을 보여줍니다.  공정한 비교를 위해 특정 민감한 하이퍼파라미터에 대해 여러 방법들을 시도해 보았습니다.  표에는 SVF와 LoRA 학습에 사용된 초기 평균값과 분산값, 배치 크기, 학습률, 클리핑 최대 규범, KL 계수(SVF의 경우)와 같은 하이퍼파라미터들이 자세히 나열되어 있습니다.  이 표는 논문에서 제시된 실험 결과의 재현성을 확보하고, 서로 다른 방법 간의 비교를 위한 기준을 제공하는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Hyper-parameters used for SVF and LoRA training. We perform a sweep on certain sensitive hyper-parameters across methods for fair comparison.
> </details>

{{< table-caption >}}
| Method | GSM8K | MBPP-Pro | ARC-Easy |
|---|---|---|---| 
| Llama3-8B-Instruct | 75.89 (1.00) | 64.65 (1.00) | 88.59 (1.00) |
| + IA3 | 78.01 (1.03) | 67.68 (1.05) | 89.10 (1.01) |
| + DORA | 78.09 (1.03) | 64.65 (1.00) | 89.14 (1.01) |
| + SVF(Ours) | **79.15 (1.04)** | 66.67 (1.03) | **89.56 (1.01)** |
| Method | MATH | Humaneval | ARC-Challenge |
|---|---|---|---| 
| Llama3-8B-Instruct | 24.54 (1.00) | 60.98 (1.00) | 80.63 (1.00) |
| + IA3 | 23.64 (0.96) | 59.76 (0.98) | 81.57 (1.01) |
| + DORA | 24.44 (0.99) | 52.44 (0.86) | 81.14 (1.01) |
| + Transformer<sup>2</sup> (Prompt) | 25.22 (1.03) | 61.59 (1.01) | 81.74 (1.01) |
| + Transformer<sup>2</sup> (Cls-expert) | 25.18 (1.03) | 62.80 (1.03) | 81.37 (1.01) |
| + Transformer<sup>2</sup> (Few-shot) | **25.47 (1.04)** | **62.99 (1.03)** | **82.61 (1.02)** |{{< /table-caption >}}
> 🔼 표 7은 추가 비교 실험 결과를 보여줍니다.  여러가지 매개변수 효율적인 미세 조정 방법들을 비교 분석한 결과입니다. 표에는 각 방법의 정규화된 점수(괄호 안)와 함께 GSM8K, MBPP-Pro, ARC-Easy 및 세 가지 추가되지 않은 작업(MATH, Humaneval, ARC-Challenge)에 대한 성능이 나와 있습니다.  각 방법의 상대적 성능을 비교하여 Transformer²의 효율성과 효과를 보여주는 표입니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Additional Comparison Experiment. Normalized scores are in the parentheses.
> </details>

{{< table-caption >}}
| Method | \text{Transformer}^{2} | IA<sup>3</sup> 100 steps | IA<sup>3</sup> 1000 steps |
|---|---|---|---| 
| Llama3-8B-Instruct | 80.63 (1.00) | 80.63 (1.00) | 80.63 (1.00) |
| + 3-shot adaptation | 82.18 (1.02) | 81.83 (1.01) | 79.01 (0.98) |
| + 5-shot adaptation | 82.38 (1.02) | 80.89 (1.00) | 79.41 (0.98) |
| + 10-shot adaptation | **82.61 (1.02)** | **82.00** (1.02) | **79.78** (**0.99**) |
| + 20-shot adaptation | **82.61 (1.02)** | 81.40 (1.01) | 79.61 (0.99) |{{< /table-caption >}}
> 🔼 표 8은 Arc-Challenge 과제에 대한 소수 샷 적응 확장성을 보여줍니다. 이 표는 다양한 수의 예시를 사용하여 성능이 어떻게 변하는지 보여주는 실험 결과를 제시합니다.  LLAMA3-8B-INSTRUCT 모델을 기반으로, 3-shot, 5-shot, 10-shot, 그리고 20-shot 적응 전략을 사용했을 때의 성능을 비교 분석합니다. 각 전략별로 Arc-Challenge 과제에 대한 정확도를 측정하고, 그 결과를 백분율(%)로 표시하여, 예시의 개수가 증가함에 따라 성능 변화를 정량적으로 보여줍니다. 이를 통해 소수 샷 학습 전략의 효율성 및 확장성을 평가하고, 적절한 예시 개수를 결정하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Few-shot adaptation scaling on the Arc-Challenge task. Performance varies with number of examples.
> </details>

{{< table-caption >}}
| Method | GSM8K | MBPP-pro | ARC-Easy |
|---|---|---|---| 
| Mistral-7B-Instruct-v0.3 | 42.83 (1.00) | 49.50 (1.00) | 81.65 (1.00) |
| + Llama SVF (ordered σ<sub>i</sub>) | 42.61 (0.99) | 48.48 (0.98) | 81.78 (1.00) |
| + Llama SVF (shuffled σ<sub>i</sub>) | 41.93 (0.98) | 46.34 (0.94) | 80.81 (0.99) |{{< /table-caption >}}
> 🔼 표 9는 Llama3-8B-Instruct 모델에서 학습된 SVF 전문가 벡터를 Mistral-7B-Instruct-v0.3 모델로 전이했을 때의 결과를 보여줍니다. 각 학습 과업(GSM8K, MBPP-pro, ARC-Easy)에 대해 Llama3-8B-Instruct 모델에서 학습된 SVF 벡터를 Mistral-7B-Instruct-v0.3 모델에 적용하여 성능을 측정했습니다.  이는 모델 간 전이 학습의 효과를 확인하기 위한 실험입니다. 표에는 각 과업에 대한 Mistral-7B-Instruct-v0.3 모델의 기본 성능과 SVF 벡터를 적용했을 때의 성능 향상 정도가 제시되어 있습니다.  특히, SVF 벡터의 순서를 유지했을 때와 임의로 섞었을 때의 성능 차이를 비교하여 SVF 벡터의 순서가 성능에 미치는 영향을 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 9:  Cross-model z𝑧\bm{z}bold_italic_z Vector Transfer. Results from transfering the SVF expert vectors trained on Llama3-8B-Instruct to Mistral-7B-Instruct-v0.3 in the respective training tasks.
> </details>

{{< table-caption >}}
| Method | ARC-Challenge |
|---|---| 
| Llama3-8B-Instruct | 80.63 (1.00) |
| + CEM 10-shot adaptation | **82.61 (1.02)** |
| + CEM 3-shot (30% of prompts) | 82.18 (1.02) |
| + CEM light (3% of prompts) | 82.08 (1.02) |{{< /table-caption >}}
> 🔼 표 10은 추론 시간 적응 예산이 다른 세 가지 다른 설정에서의 성능을 보여줍니다. 세 가지 설정은 10개의 샘플을 사용하는 표준 CEM(Cross-Entropy Method), 프롬프트의 30%만 사용하는 CEM의 변형, 그리고 프롬프트의 3%만 사용하는 CEM light입니다. 각 설정에서의 성능을 ARC-Challenge 작업에 대해 평가합니다.  표는 각 설정에서의 성능을 기본 모델의 성능과 비교하여 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 10: 3-shot and light variants Performance with different inference-time adaptation budgets.
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
{{< /gallery >}}