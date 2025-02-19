---
title: "How Do LLMs Acquire New Knowledge? A Knowledge Circuits Perspective on Continual Pre-Training"
summary: "지속적 사전 훈련 중 LLM의 지식 습득 메커니즘을 지식 회로 진화 관점에서 분석하여 지식 관련성, 이중 단계적 진화, 심층-표층 패턴 등의 핵심 발견을 제시합니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Zhejiang University",]
showSummary: true
date: 2025-02-16
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.11196 {{< /keyword >}}
{{< keyword icon="writer" >}} Yixin Ou et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-18 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.11196" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.11196" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/how-do-llms-acquire-new-knowledge-a-knowledge" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)은 지식 집약적 작업에서 뛰어난 성능을 보이지만, 새로운 지식을 어떻게 내부적으로 통합하는지에 대한 이해는 부족합니다. 특히, 획득한 지식을 신경망 계산에 구조적으로 통합하는 방법은 아직 명확하지 않습니다. 본 연구는 지속적 사전 훈련 과정에서 지식 회로의 진화를 분석하여 이 문제를 해결하고자 합니다. 기존 연구는 지식 블록을 고립된 구성 요소로 취급하는 반면, 본 연구는 지식 회로의 관점에서 여러 구성 요소 간의 상호 작용을 분석하여 암묵적인 지식 표현을 밝혀냅니다.

본 연구는 지속적 사전 훈련 중 지식 회로의 진화를 체계적으로 분석하여 몇 가지 중요한 발견을 제시합니다. 첫째, 새로운 지식의 습득은 기존 지식과의 관련성에 따라 달라집니다. 둘째, 지식 회로의 진화는 형성 단계와 최적화 단계로 나뉘며 각 단계는 고유한 구조적, 행동적 특징을 갖습니다. 셋째, 지식 회로의 진화는 심층에서 표층으로 진행되는 패턴을 따릅니다. 이러한 발견은 LLM의 새로운 지식 습득 메커니즘에 대한 이론적 이해를 높일 뿐만 아니라, 모델 성능 향상을 위한 지속적 사전 훈련 전략 개선에도 시사점을 제공합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 새로운 지식 습득은 기존 지식과의 관련성에 영향을 받는다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 지식 회로의 진화는 형성 단계와 최적화 단계로 구분된다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 지식 회로의 진화는 심층에서 표층으로 진행되는 패턴을 따른다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **지속적 사전 훈련** 과정에서 **지식 회로의 진화**를 분석하여 **LLM의 새로운 지식 습득 메커니즘**에 대한 이해를 높이고, 모델 성능 향상을 위한 **새로운 전략**을 제시합니다. **지식 관련성 원칙**, **이중 단계적 회로 진화**, **심층에서 표층으로의 회로 진화 패턴** 등의 핵심 발견은 LLM의 지식 습득 과정에 대한 이론적 이해를 높이고, 지속적 학습 능력 향상을 위한 연구에 중요한 시사점을 제공합니다.  연구는 **기계 해석 가능성** 분야에서도 중요한데,  **지식 회로** 개념을 이용하여 **LLM의 내부 작동 방식**을 설명하고, 이를 통해 모델의 **예측 성능 향상** 및 **다양한 도메인에서의 적응성 향상**에 기여할 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.11196/extracted/6191678/figures/illustration.png)

> 🔼 본 논문의 그림 1은 지식 회로의 진화 과정에서 형성 단계에서 최적화 단계로의 전이를 보여줍니다. 각 단계는 성능, 토폴로지 및 구성 요소 수준에서 고유한 특징을 갖습니다.  즉, 모델이 새로운 지식을 습득하는 과정에서 지식 회로의 구조와 기능이 어떻게 변화하는지를 보여주는 것으로, 초기에는 지식 회로가 형성되고, 이후 최적화를 거쳐 성능이 향상됨을 시각적으로 나타냅니다.  세부적으로는 성능 지표, 지식 회로의 토폴로지(구조), 그리고 구성 요소(노드와 엣지)의 변화를 통해 이러한 단계적 변화를 분석합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Illustration of our findings: Phase shift from formation to optimization in the evolution of knowledge circuits, each phase characterized by distinct features at the performance, topology, and component levels.
> </details>





{{< table-caption >}}
| Architecture | Model | size | nodes | edges | block_size | batch_size | learning_rate | epochs |
|---|---|---|---|---|---|---|---|---|
| GPT-2 | GPT-2 Small | 124M | 158 | 32,491 | 1,024 | 32 | 1e-3 | 25 |
|  | GPT-2 Medium | 355M | 410 | 231,877 | 1,024 | 16 | 1e-3 | 15 |
| Llama | TinyLlama-v1.1 | 1.1B | 728 | 742,996 | 2,048 | 4 | 4e-5 | 10 |
| Phi | Phi-1.5 | 1.3B | 794 | 886,597 | 2,048 | 2 | 2e-4 | 7 |{{< /table-caption >}}

> 🔼 본 표는 지속적 사전 훈련 실험에 사용된 모델의 통계 및 하이퍼파라미터를 보여줍니다. 모델의 크기(size), 노드 수(nodes), 에지 수(edges), 블록 크기(block size), 배치 크기(batch size), 학습률(learning rate), 에폭 수(epochs) 등의 정보를 포함하고 있습니다.  GPT-2 Small, GPT-2 Medium, TinyLlama, Phi-1.5 네 가지 모델에 대한 정보를 제공하여 각 모델의 특징과 하이퍼파라미터 설정을 비교 분석하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Statistics and hyperparameters of models used in the continual pre-training experiments.
> </details>





### In-depth insights


#### Knowledge Circuits
본 논문에서 제시된 '지식 회로(Knowledge Circuits)' 개념은 **LLM이 지식을 어떻게 저장하고 처리하는지**에 대한 새로운 관점을 제공합니다. 기존 연구들이 지식을 고립된 모듈로 간주한 것과 달리, 지식 회로는 **여러 구성요소 간의 상호작용**을 통해 내재된 지식 표현을 드러냅니다. 이는 **계산적 부그래프(computational subgraph)**로 정의되며, 특정 지식 도메인을 충실히 반영하여 모델의 행동이나 성능을 독자적으로 재현할 수 있습니다. **지속적인 사전 훈련(continual pre-training)** 과정에서 지식 회로의 진화를 분석함으로써, 새로운 지식 습득의 메커니즘에 대한 통찰력을 얻을 수 있으며, **성능 향상을 위한 전략 개선**에도 기여할 수 있습니다. 특히, **지식의 관련성**, **회로 진화의 단계적 변화**, **심층에서 표층으로의 패턴** 등 중요한 발견들이 제시됩니다.

#### Continual Learning
본 논문은 지속적 사전 훈련을 통한 대규모 언어 모델(LLM)의 새로운 지식 습득 메커니즘을 다룹니다. **지식 회로 진화**라는 관점에서, 기존 지식과의 관련성, **형성 및 최적화 단계**, 그리고 **심층에서 표층으로의 패턴**이라는 세 가지 주요 발견을 제시합니다.  이는 단순히 지식을 저장하는 것이 아니라 **동적인 상호작용을 통해 지식을 처리하고 통합하는 과정**임을 강조합니다. 특히, 관련된 새로운 지식은 완전히 새로운 지식보다 효율적으로 통합되는데, 이는 데이터 커리큘럼 설계 및 지속적 학습 전략 개선에 시사하는 바가 큽니다.  **지식 회로의 토폴로지적 중앙화**는 지식 습득 과정에서 중요한 역할을 하며, **심층에서 표층으로 이어지는 계층적 패턴**은 지식 추출 및 표현의 효율성을 높이는 데 기여합니다.  **두 단계의 뚜렷한 전환점**은 모델의 지식 습득과 최적화 과정에 대한 이해를 심화시켜 지속적 사전 훈련 전략을 개선하는 데 도움을 줄 수 있습니다.  결론적으로, 이 연구는 LLM의 지식 습득에 대한 이론적 이해를 높일 뿐 아니라 모델 성능 향상을 위한 실질적인 전략을 제시합니다.

#### Circuit Evolution
본 논문에서 제시된 지식 회로의 진화는 **단순한 구조적 변화를 넘어 지식 획득과 처리 방식의 근본적인 변화**를 보여줍니다. 초기 단계에서는 **새로운 지식이 기존 지식과의 관련성에 따라 효율적으로 통합**되며, 회로의 형성 단계와 최적화 단계로 구분되는 **뚜렷한 상전이 현상**이 관찰됩니다.  **깊은 층에서 얕은 층으로 이어지는 계층적 패턴**을 통해, 깊은 층은 지식 추출 기능을 담당하고, 얕은 층은 지식 표현을 풍부하게 하는 역할을 수행합니다. 이러한 진화 과정은 **모델의 지식 습득 및 적응 메커니즘에 대한 심도 있는 이해**를 제공하며, **지속적인 사전 학습 전략 개선**을 위한 중요한 시사점을 제시합니다.  특히 **지식 관련성 원칙**과 **이원적 진화 과정**은 지속적인 학습 모델의 효율성을 높이는 데 중요한 역할을 합니다.

#### Model Limitations
본 논문에서 제시된 모델의 한계는 주로 **모델 아키텍처**와 **훈련 기법**에 집중되어 있습니다.  **트랜스포머 계열 디코더 전용 LLM**에만 초점을 맞춰 연구를 진행하여, 인코더-디코더 또는 인코더 전용 모델에는 적용할 수 없다는 점이 한계로 지적됩니다. 또한, 계산 자원 및 회로 발견 방법의 제약으로 인해 **13억 파라미터보다 큰 모델**은 분석하지 못했다는 점도 있습니다.  **표준 다음 토큰 예측 목표**를 사용한 지속적 사전 훈련 방식만을 채택하여, 새로운 지식 습득 효율성 및 효과성을 높이는 다양한 훈련 기법의 영향은 고려되지 않았습니다. 따라서 본 연구 결과는 **모델 아키텍처와 훈련 방식의 다양성**을 고려하지 못한 제한적인 측면을 지니고 있으며, 이는 향후 연구에서 개선되어야 할 부분입니다.  더욱 폭넓은 모델 아키텍처와 훈련 전략에 대한 연구를 통해 본 연구의 한계를 극복하고, 더욱 포괄적인 결과를 얻을 수 있을 것입니다.

#### Future Research
본 논문은 거대 언어 모델(LLM)의 지식 습득 메커니즘에 대한 새로운 관점을 제시하며, **지식 회로의 진화**를 중점적으로 다룹니다.  미래 연구는 **다양한 LLM 아키텍처** (인코더-디코더, 인코더 전용 모델 등)에 대한 연구 확장을 통해 일반화 가능성을 높이는 데 초점을 맞춰야 합니다. 또한, **대규모 매개변수 모델**에 대한 연구를 위해서는 계산 자원 및 회로 발견 방법의 한계를 극복하는 것이 중요합니다.  **다양한 지식 습득 기법**에 대한 연구 또한 필요합니다.  예를 들어, 기존의 다음 토큰 예측 방식 외에 새로운 훈련 기법들을 통해 지식 회로의 진화에 미치는 영향을 분석하는 것이 중요합니다.  마지막으로, **지식 회로의 상태를 추적**하여 훈련 과정의 상황에 맞게 훈련 방식이나 데이터를 조정하는 방안을 모색하는 것도 중요한 미래 연구 과제입니다. 이를 통해 LLM의 지속적인 학습 능력 향상 및 다양한 분야에서의 적응성 강화에 기여할 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.11196/extracted/6191678/figures/hit_at_10.png)

> 🔼 그림 2는 GPT-2 Small, GPT-2 Medium, Phi-1.5 모델에서 지속적 사전 훈련 중에 발견된 지식 회로의 성능(Hit@10)을 보여줍니다. 왼쪽은 새로 학습된 지식의 종류에 따른 성능을 보여줍니다. K_rel은 기존 지식과 관련된 새 지식, K_compl은 완전히 새로운 지식을 나타냅니다. 오른쪽은 지식의 빈도에 따른 성능을 보여줍니다. Low-freq, Medium-freq, High-freq는 각각 [1, 2), [2, 5], (5, 27] 범위의 빈도를 가진 지식을 나타냅니다. 모든 설정에서 3 epoch의 윈도우 크기를 사용하여 곡선을 부드럽게 처리했습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Hit@10 of the performance of knowledge circuits in GPT-2 Small, GPT-2 Medium and Phi-1.5 throughout training. Left: Performance for circuits discovered by different types of knowledge, where K_rel and K_compl represent relevant new knowledge and completely new knowledge, respectively. Right: Performance for circuits discovered by different frequencies of knowledge, where Low-freq, Medium-freq, and High-freq represent knowledge with frequencies in the ranges [1,2)12[1,2)[ 1 , 2 ), [2,5]25[2,5][ 2 , 5 ] and (5,27]527(5,27]( 5 , 27 ], respectively. Note that we smooth the curves using a window size of 3 epochs for all settings.
> </details>



![](https://arxiv.org/html/2502.11196/extracted/6191678/figures/similarity_entropy.png)

> 🔼 그림 3은 지속적 사전 훈련 전반에 걸쳐 지식 회로의 진화를 보여줍니다. 위쪽은 중간 지점에서 최종 지점(훈련 종료 시점)의 지식 회로 간의 가장자리 자카드 유사도를 보여줍니다. 아래쪽은 지식 회로 엔트로피의 변화를 보여줍니다.  K_rel은 기존 지식과 관련된 새로운 지식을, K_compl은 완전히 새로운 지식을 나타냅니다. Low-freq, Medium-freq, High-freq는 각각 빈도가 [1, 2), [2, 5], (5, 27]인 지식을 나타냅니다. 이 그림을 통해 지식 회로가 훈련 과정에서 어떻게 진화하고 안정화되는지, 그리고 새로운 지식이 기존 지식과의 관련성에 따라 학습 효율성에 어떤 영향을 미치는지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Top: Edges Jaccard Similarity of intermediate knowledge circuits with the circuits at the final checkpoint. Bottom: Knowledge Cutcuit Entropy of knowledge circuits throughout training. K_rel and K_compl represent relevant new knowledge and completely new knowledge, respectively. Low-freq, Medium-freq, and High-freq represent knowledge with frequencies in the ranges [1,2)12[1,2)[ 1 , 2 ), [2,5]25[2,5][ 2 , 5 ] and (5,27]527(5,27]( 5 , 27 ], respectively.
> </details>



![](https://arxiv.org/html/2502.11196/extracted/6191678/figures/specific_circuit_performance.png)

> 🔼 본 그림은 GPT-2 Small 모델에서 지속적 사전 훈련 중 정렬된 지식 회로의 성능(Hit@10)을 나타냅니다.  'Init', 'Before', 'After', 'Last'는 각각 초기 체크포인트, 위상 변화 이전 체크포인트, 위상 변화 이후 체크포인트, 최종 체크포인트에서의 토폴로지와 정렬된 회로를 나타냅니다. 'Original'은 각 체크포인트에서 원본 지식 회로를 나타냅니다. 3 에폭의 윈도우 크기를 사용하여 곡선을 부드럽게 처리했습니다.  즉, 이 그림은 모델 훈련 초반, 위상 변화 직전, 위상 변화 직후, 그리고 훈련 말기에 각각의 지식 회로의 성능을 비교하여 지식 획득 과정에서 지식 회로의 토폴로지 변화가 성능 향상에 미치는 영향을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Hit@10 of the performance of aligned knowledge circuits in GPT-2 Small throughout training. Init, Before, After, Last represents the circuits whose topologies align with those at the initial checkpoint, the checkpoint before the phase shift, the checkpoint after the phase shift, and the final checkpoint, respectively. Original represents the original knowledge circuits at each checkpoint. Note that we smooth the curves using a window size of 3 epochs.
> </details>



![](https://arxiv.org/html/2502.11196/extracted/6191678/figures/specialized_components.png)

> 🔼 본 그림(그림 5)은 GPT-2 Small과 GPT-2 Medium 모델에서 지식 회로 내 모든 노드에 걸쳐 훈련 과정 동안 특수화된 어텐션 헤드의 비율을 보여줍니다. 특수화된 어텐션 헤드는 mover head, relation head, mixture head 등을 포함하며, 각각 특정 기능(예: 주어 추출, 관계 추출 등)에 특화되어 있습니다. 훈련 초반에는 특수화된 어텐션 헤드의 비율이 낮지만, 훈련이 진행됨에 따라 비율이 증가하는 것을 확인할 수 있습니다.  곡선은 3 에폭의 윈도우 크기를 사용하여 평활화 처리되었습니다. 이는 모델이 훈련 과정에서 새로운 지식을 습득하고, 지식 처리를 위해 특수화된 메커니즘을 발달시키는 과정을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Proportion of specialized attention heads in all nodes of the knowledge circuits throughout training for GPT-2 Small and GPT-2 Medium. Note that we smooth the curves using a window size of 3 epochs.
> </details>



![](https://arxiv.org/html/2502.11196/extracted/6191678/figures/gpt2_heads_distribution.png)

> 🔼 그림 6은 GPT-2 Small 모델에서 지속적인 사전 훈련 과정 동안 지식 회로 내에서 이동 헤드와 관계 헤드의 계층별 분포를 보여줍니다. 위쪽 그림은 훈련 중에 지식 회로에서 이동 헤드의 계층별 분포를 보여줍니다. 아래쪽 그림은 훈련 중에 지식 회로에서 관계 헤드의 계층별 분포를 보여줍니다. 이 그림을 통해 지속적인 사전 훈련 중에 지식 표현의 진화 과정을 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Top: Layer distribution of mover head in the knowledge circuits in GPT-2 Small throughout training. Bottom: Layer distribution of relation head in the knowledge circuits in GPT-2 Small throughout training.
> </details>



![](https://arxiv.org/html/2502.11196/extracted/6191678/figures/gpt2_activation_ratio.png)

> 🔼  그림 7은 GPT-2 Small 모델의 지식 회로 내에서 각 계층의 활성화 비율을 보여줍니다.  더 자세히 설명하면, 이 그림은 지식 회로 내의 모든 간선 중에서 특정 계층에서 시작되는 간선의 비율을 계층별로 보여줍니다. 이는 지식이 모델 내에서 어떻게 흐르는지, 그리고 각 계층이 지식 처리에 어떤 역할을 하는지를 이해하는 데 도움을 줍니다.  훈련 과정에서 각 계층의 활성화 비율이 어떻게 변하는지 보여주는 시각적 자료입니다. 
> <details>
> <summary>read the caption</summary>
> Figure 7: Layer distribution of the edges activation ratio within the knowledge circuits in GPT-2 Small.
> </details>



![](https://arxiv.org/html/2502.11196/extracted/6191678/figures/gpt2_rank_and_prob.png)

> 🔼 그림 8은 GPT-2 Small 모델에서 지속적인 사전 훈련 중에 중간 레이어의 출력을 어휘 공간에 임베딩 해제할 때 마지막 토큰 위치에서 목표 속성 토큰의 순위와 해당 확률을 보여줍니다.  위쪽은 각 레이어에서의 목표 토큰의 순위를, 아래쪽은 각 레이어에서의 목표 토큰의 확률을 나타냅니다.  훈련 에폭에 따른 변화를 시각적으로 보여주어, 모델이 새로운 지식을 습득하는 과정에서 어떻게 목표 토큰에 대한 정보를 처리하고 표현하는지 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Top: Rank of the target attribute token when unembedding the intermediate layer’s output into vocabulary space at the last token position throughout training for GPT-2 Small. Bottom: The corresponding probability of the target attribute token.
> </details>



![](https://arxiv.org/html/2502.11196/extracted/6191678/figures/accuracy.png)

> 🔼 그림 9는 지속적인 사전 훈련 과정에서의 정확도 곡선을 보여줍니다. K_rel과 K_compl은 각각 관련된 새로운 지식과 완전히 새로운 지식을 나타냅니다. First-token Acc는 각 속성의 첫 번째 토큰에 대한 모델의 다음 토큰 예측 정확도를 나타내고, Query Acc는 각 속성에 대한 다운스트림 쿼리 작업에서의 생성 정확도를 나타냅니다.  그림은 지속적인 사전 훈련 중에 모델이 새로운 지식을 학습하는 과정에서 First-token Acc와 Query Acc 지표가 어떻게 변화하는지 보여줍니다. K_rel의 경우, 모델이 이미 가지고 있는 지식과 관련된 새로운 지식을 학습하기 때문에, K_compl보다 정확도 향상이 더 빠르게 나타납니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Accuracy curves across continual pre-training. K_rel and K_compl represent relevant new knowledge and completely new knowledge, respectively. First-token Acc stands for the model’s next-token prediction accuracy on the first token of each attribute, while Query Acc stands for the generation accuracy on downstream query tasks for each attribute.
> </details>



![](https://arxiv.org/html/2502.11196/extracted/6191678/figures/transfer_hit_at_10.png)

> 🔼 그림 10은 GPT-2 Small과 GPT-2 Medium 모델에서 지속적인 사전 훈련 중에 생성된 지식 회로의 전이 성능을 Hit@10 지표로 나타낸 그래프입니다.  Low-freq Circuit, Medium-freq Circuit, High-freq Circuit은 각각 빈도 범위가 [1, 2), [2, 5], (5, 27]인 지식으로부터 식별된 지식 회로를 나타냅니다. 즉, 사용된 지식의 빈도에 따라 세 가지 유형의 지식 회로가 만들어졌고, 각 유형의 지식 회로가 서로 다른 빈도의 지식 집합에 대해 어떻게 성능을 보이는지 평가한 결과를 보여줍니다. 그래프는 3 에폭의 이동 평균을 사용하여 부드럽게 처리되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Hit@10 of the transfer performance of knowledge circuits in GPT-2 Small and GPT-2 Medium throughout training. Low-freq Circuit, Medium-freq Circuit, and High-freq Circuit represent knowledge circuits identified by knowledge with the frequencies in the ranges [1,2)12[1,2)[ 1 , 2 ), [2,5]25[2,5][ 2 , 5 ] and (5,27]527(5,27]( 5 , 27 ], respectively. Note that we smooth the curves using a window size of 3 epochs for all settings.
> </details>



![](https://arxiv.org/html/2502.11196/extracted/6191678/figures/nodes_similarity.png)

> 🔼 그림 11은 지속적인 사전 훈련 과정에서 중간 지점의 지식 회로와 최종 지점의 지식 회로 간의 노드 자카드 유사도를 보여줍니다. K_rel과 K_compl은 각각 관련된 새로운 지식과 완전히 새로운 지식을 나타냅니다. Low-freq, Medium-freq, High-freq는 각각 [1, 2), [2, 5], (5, 27]의 범위에 있는 주파수를 가진 지식을 나타냅니다. 이 그림은 지식 회로의 구조적 안정성과 진화 과정에 대한 통찰력을 제공합니다. 즉, 훈련이 진행됨에 따라 중간 지점의 지식 회로가 최종 지점의 지식 회로와 점점 더 유사해짐을 보여줍니다. 이는 지식 획득 과정에서 지식 회로가 점진적으로 안정화되고 핵심 구조가 강화됨을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Nodes Jaccard Similarity of intermediate knowledge circuits with the circuits at the final checkpoint. K_rel and K_compl represent relevant new knowledge and completely new knowledge, respectively. Low-freq, Medium-freq, and High-freq represent knowledge with frequencies in the ranges [1,2)12[1,2)[ 1 , 2 ), [2,5]25[2,5][ 2 , 5 ] and (5,27]527(5,27]( 5 , 27 ], respectively.
> </details>



![](https://arxiv.org/html/2502.11196/extracted/6191678/figures/gpt2_medium_activation_ratio.png)

> 🔼 그림 12는 GPT-2 Medium 모델의 지식 회로 내에서 각 계층별 간선 활성화 비율의 분포를 보여줍니다.  GPT-2 Medium 모델에서 지속적 사전 훈련 중에 식별된 지식 회로 내의 간선 활성화 패턴의 변화를 계층별로 분석한 결과입니다.  세로축은 모델 계층을, 가로축은 지속적 사전 훈련의 에포크 수를 나타내며, 색깔은 각 계층에서 시작되는 간선의 활성화 비율을 나타냅니다. 이 그림을 통해 지식 회로 내에서 정보 흐름의 역동적인 변화를 시각적으로 파악할 수 있습니다. 특히, 계층 간의 활성화 비율 변화를 통해 지식 획득 과정에서의 계층별 역할 변화를 분석하는 데 유용합니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Layer distribution of the edges activation ratio within the knowledge circuits in GPT-2 Medium.
> </details>



![](https://arxiv.org/html/2502.11196/extracted/6191678/figures/gpt2_medium_heads_distribution.png)

> 🔼 그림 13은 GPT-2 Medium 모델에서 지속적인 사전 훈련 과정 동안 파악된 지식 회로 내에서 이동 헤드와 관계 헤드의 계층별 분포를 보여줍니다. 왼쪽 패널은 이동 헤드의 계층별 분포를, 오른쪽 패널은 관계 헤드의 계층별 분포를 나타냅니다. 이를 통해 지식 회로의 진화 과정에서 각 헤드의 역할과 상호 작용을 시각적으로 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: Left: Layer distribution of mover head in the knowledge circuits in GPT-2 Medium throughout training. Right: Layer distribution of relation head in the knowledge circuits in GPT-2 Medium throughout training.
> </details>



![](https://arxiv.org/html/2502.11196/extracted/6191678/figures/gpt2_forget.png)

> 🔼 이 그림은 이전 지식 습득 실험의 최종 검사대와 중간 지식 회로의 가장자리 자카드 유사성을 보여줍니다.  그림은 지식 회로의 구조적 안정성을 보여주는 지표로, 훈련 과정 전반에 걸쳐 회로의 가장자리 구성이 얼마나 일관되게 유지되는지 보여줍니다.  높은 유사성은 지식 회로가 훈련 과정 동안 안정적이고 일관된 구조를 유지한다는 것을 시사합니다. 이는 모델이 새로운 지식을 효율적으로 통합하고 이전 지식과 통합하는 능력을 나타냅니다.  반대로 낮은 유사성은 지식 회로가 훈련 중에 크게 변화하여 새로운 지식 습득의 비효율성이나 불안정성을 나타낼 수 있음을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: Edges Jaccard Similarity of intermediate knowledge circuits with the circuits at the final checkpoint of the previous knowledge acquisition experiment.
> </details>



![](https://arxiv.org/html/2502.11196/extracted/6191678/figures/gpt2_all_rank_and_prob.png)

> 🔼 그림 15는 GPT-2 Small 모델의 지속적 사전 훈련 과정에서 중간층 출력을 어휘 공간으로 임베딩 해제할 때 마지막 토큰 위치에서 타겟 속성 토큰의 순위와 확률을 보여줍니다. 상단은 순위를, 하단은 확률을 나타냅니다. Low-freq, Medium-freq, High-freq는 각각 [1, 2), [2, 5], (5, 27] 범위의 빈도를 가진 지식을 나타냅니다. 이 그림은 모델이 새로운 지식을 습득하는 과정에서 중간층의 역할과 어휘 공간에서의 타겟 토큰 표현 변화를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 15: Top: Rank of the target attribute token when unembedding the intermediate layer’s output into vocabulary space at the last token position throughout training for GPT-2 Small. Bottom: Probability of the target attribute token when unembedding the intermediate layer’s output into vocabulary space at the last token position throughout training for GPT-2 Small. Low-freq, Medium-freq, and High-freq represent knowledge with frequencies in the ranges [1,2)12[1,2)[ 1 , 2 ), [2,5]25[2,5][ 2 , 5 ] and (5,27]527(5,27]( 5 , 27 ], respectively.
> </details>



![](https://arxiv.org/html/2502.11196/extracted/6191678/figures/gpt2_medium_rank_and_prob.png)

> 🔼 그림 16은 GPT-2 Medium 모델의 지속적 사전 훈련 과정에서 각 레이어의 출력을 어휘 공간으로 임베딩 해제할 때, 마지막 토큰 위치에서 타겟 속성 토큰의 순위(위쪽)와 확률(아래쪽)을 보여줍니다.  Low-freq, Medium-freq, High-freq는 각각 [1, 2), [2, 5], (5, 27] 범위의 빈도를 가진 지식을 나타냅니다. 이 그림은 모델이 지속적 사전 훈련 중에 새로운 지식을 습득하는 과정에서 각 레이어의 역할과 어휘 공간 내 타겟 토큰의 변화를 보여주는 시각적 자료입니다.
> <details>
> <summary>read the caption</summary>
> Figure 16: Top: Rank of the target attribute token when unembedding the intermediate layer’s output into vocabulary space at the last token position throughout training for GPT-2 Medium. Bottom: Probability of the target attribute token when unembedding the intermediate layer’s output into vocabulary space at the last token position throughout training for GPT-2 Medium. Low-freq, Medium-freq, and High-freq represent knowledge with frequencies in the ranges [1,2)12[1,2)[ 1 , 2 ), [2,5]25[2,5][ 2 , 5 ] and (5,27]527(5,27]( 5 , 27 ], respectively.
> </details>



![](https://arxiv.org/html/2502.11196/extracted/6191678/figures/tinyllama_rank_and_prob.png)

> 🔼 그림 17은 TinyLlama 모델에서 지속적 사전 훈련 중에 중간 레이어의 출력을 어휘 공간에 임베딩 해제할 때 마지막 토큰 위치에서 타겟 속성 토큰의 순위(위쪽)와 확률(아래쪽)을 보여줍니다. 저주파, 중주파, 고주파는 각각 [1, 2), [2, 5], (5, 27] 범위의 빈도를 가진 지식을 나타냅니다. 이 그림은 모델이 훈련되는 동안 어떻게 타겟 토큰 정보를 처리하고, 다양한 빈도의 지식에 따라 그 처리 방식이 어떻게 달라지는지를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 17: Top: Rank of the target attribute token when unembedding the intermediate layer’s output into vocabulary space at the last token position throughout training for TinyLlama. Bottom: Probability of the target attribute token when unembedding the intermediate layer’s output into vocabulary space at the last token position throughout training for TinyLlama. Low-freq, Medium-freq, and High-freq represent knowledge with frequencies in the ranges [1,2)12[1,2)[ 1 , 2 ), [2,5]25[2,5][ 2 , 5 ] and (5,27]527(5,27]( 5 , 27 ], respectively.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Relation | Template |
|---|---| 
| _city_ | _s_ lives in the city of | 
| _major_ | _s_ majors in the field of | 
| _company_ | _s_ works for the company of |{{< /table-caption >}}
> 🔼 이 표는 논문의 3.3절 '회로 발견'에서 사용된 세 가지 관계(city, major, company)에 대한 사실 확인 작업의 템플릿을 보여줍니다. 각 관계에 대해 질문 문구를 만드는 방법을 보여주는 세 개의 템플릿이 있습니다. 예를 들어, 'city' 관계에 대한 템플릿은 's lives in the city of' 입니다. 여기서 's'는 주어를 나타냅니다. 이 표는 모델이 새로운 지식을 습득하는 방식을 이해하는 데 도움이 되는 합성 데이터 생성 방법을 설명합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Templates for the factual recall task on relations.
> </details>

{{< table-caption >}}
| Name | Possible Values |
|---|---| 
| First Name | Aarav, Abbott, Aberdeen, Abilene, Acey, Adair, Adelia, Adriel, Afton, Aida, Ainsley, Aislinn, Alaric, Albin, Alden, Aleah, Alessandra, Alistair, Allegra, Alphonse, Althea, Amaury, Ambrose, Amelina, Amias, Anatole, Anders, Ansel, Anthea, Antonella, Anwen, Arden, Ariadne, Aric, Arlen, Armand, Armando, Arwen, Asa, Astra, Atticus, Aubrey, Auden, Aurelia, Aurora, Aveline, Aviana, Azariah, Baird, Basil, Bayard, Beauregard, Bellamy, Belvedere, Benedict, Bennett, Berenice, Bertram, Blaine, Blair, Blythe, Boaz, Bodhi, Boniface, Bram, Branwen, Brenna, Briar, Briony, Broderick, Bromley, Bronson, Cadence, Cael, Caelan, Caius, Caledon, Calista, Calliope, Callum, Calyx, Cambria, Camellia, Candela, Caspian, Cassian, Cassiopeia, Castor, Cecily, Celeste, Celestia, Cerelia, Cerys, Chalcedony, Chandra, Charlton, Cicero, Cillian, Clemence, Clementine, Cleo, Clio, Clovis, Colton, Conall, Conrad, Corbin, Cordelia, Cormac, Cosima, Cressida, Crispin, Cybele, Cyril, Dahlia, Damaris, Daphne, Darby, Darcy, Dario, Davina, Deirdre, Delaney, Delphine, Demelza, Desmond, Dexter, Dimitri, Dinah, Dorian, Dulcie, Eamon, Earlene, Eben, Edeline, Edmund, Eldon, Eleri, Elia, Elian, Elias, Elodie, Eloise, Elowen, Ember, Emeline, Emrys, Endellion, Ender, Ephraim, Erasmus, Esme, Eulalia, Evadne, Evander, Everard, Everett, Fable, Fanchon, Farrah, Faye, Felix, Fern, Finlay, Fiora, Fletcher, Florian, Forsythia, Freya, Frida, Gable, Galen, Gareth, Garnet, Garrick, Gelsey, Gemma, Genever, Genevieve, Ginevra, Grady, Griffin, Guinevere, Hadley, Halcyon, Hale, Harlan, Hart, Haven, Hawthorne, Hazel, Heath, Helena, Hesper, Hollis, Honora, Hyacinth, Idris, Ilaria, Ilona, Imara, Indigo, Ingrid, Ione, Iris, Isadora, Isolde, Ivor, Jago, Jareth, Jarvis, Jemima, Jericho, Jocasta, Jolyon, Jorah, Jory, Jovan, Jubilee, Jules, Junia, Juniper, Kael, Kaia, Kalista, Kalliope, Katriel, Keir, Kenna, Kerensa, Keturah, Keziah, Kieran, Kirby, Kismet, Kit, Knox, Kyrie, Lachlan, Lark, Larkin, Laszlo, Leda, Leif, Lennox, Leonie, Leopold, Leta, Linnea, Liora, Livia, Llewellyn, Locke, Lorcan, Lorelei, Lorna, Lucian, Lysandra, Lysander, Mabel, Macey, Maeve, Magnolia, Malachi, Malin, Manon, Marcel, Marcellus, Maren, Marius, Marisol, Maris, Mathis, Matilda, Mavis, Maximilian, Meadow, Merrick, Merritt, Micaiah, Micah, Mira, Mireille, Mireya, Mirren, Morrigan, Muir, Nadia, Nadine, Nairne, Nara, Nash, Navi, Naylor, Neve, Nico, Nina, Noble, Nolan, Nora, Nova, Nyssa, Oberon, Octavia, Odessa, Oisin, Oleander, Olwen, Onyx, Ophelia, Orion, Orla, Orson, Osiris, Osric, Ottilie, Ozias, Paisley, Paloma, Pax, Paz, Penelope, Peregrine, Persephone, Phaedra, Phineas, Phoenix, Pippa, Poppy, Portia, Posy, Primrose, Quill, Quinlan, Rafferty, Rain, Rainer, Raphael, Raven, Reeve, Reinette, Renata, Rhea, Rhiannon, Rhys, Riona, Roderick, Romilly, Rowan, Roxana, Rufus, Sable, Sabine, Saffron, Sage, Salem, Samara, Sancia, Saoirse, Sarai, Saskia, Selah, Seneca, Seraphina, Seren, Severin, Shai, Shiloh, Sibyl, Sidonie, Silas, Simeon, Simone, Sinclair, Sol, Solange, Sorrel, Sparrow, Stellan, Sullivan, Sylvain, Sybil, Sylvana, Tallulah, Tamsin, Tansy, Tarquin, Taryn, Tavish, Tegan, Thaddeus, Thelma, Theodora, Theron, Thorin, Thorne, Thora, Tiernan, Tristan, Tullia, Ursula, Valencia, Valerian, Vanya, Vesper, Vianne, Violetta, Virgil, Waverly, Wendell, Willa, Windsor, Winston, Wisteria, Wren, Wynn, Xanthe, Xavier, Xenia, Xerxes, Yara, Yasmin, Yelena, Ysabel, Yvaine, Zahra, Zara, Zephyr, Zinnia, Ziva, Zora |
| Middle Name | Abel, Abram, Ace, Adele, Ainsley, Alaric, Alcott, Alden, Allegra, Amara, Amethyst, Anders, Ansel, Arden, Arlo, Arrow, Asa, Asher, Aster, Astrid, Atticus, Auden, Aurora, Austen, Axel, Baird, Basil, Bay, Beau, Beck, Blaise, Blake, Blythe, Boden, Bodhi, Boone, Bram, Bran, Briar, Briggs, Brooks, Calla, Calvin, Caspian, Cassian, Cedar, Celeste, Chance, Channing, Cleo, Clove, Clyde, Cohen, Colt, Cove, Crew, Crosby, Cyrus, Dane, Dante, Dashiell, Dawn, Dax, Dean, Delta, Dimitri, Dove, Drake, Dune, Echo, Eden, Edison, Elara, Elian, Ellis, Elowen, Ember, Emrys, Eos, Esme, Evangeline, Ever, Everest, Ewan, Eyre, Fable, Fairfax, Fallon, Faye, Fenton, Fern, Finnian, Fleur, Flynn, Forrest, Fox, Gage, Gale, Garnet, Gideon, Gray, Greer, Halcyon, Hale, Harlow, Haven, Hawk, Hayes, Hollis, Hope, Hugo, Idris, Iker, Indigo, Ines, Iona, Iris, Isla, Iver, Jace, Jade, Jagger, Jem, Jet, Joaquin, Jude, Jules, Kai, Kane, Kash, Keats, Keira, Kellen, Kendrick, Kepler, Kian, Kit, Knox, Lake, Lark, Laurel, Layne, Leif, Lennox, Lester, Levi, Liam, Lila, Linnea, Locke, Lorcan, Lore, Luca, Lucian, Lux, Lyric, Maeve, Magnus, Maia, Malcolm, March, Maren, Marlow, Mason, Maverick, Meadow, Mercer, Merrick, Mica, Milan, Milo, Monroe, Moon, Nash, Nico, Noble, Noor, North, Oak, Oberon, Odette, Oisin, Oleander, Onyx, Opal, Orion, Otis, Otto, Pace, Parker, Pax, Paz, Penn, Perry, Phoenix, Pierce, Pine, Poe, Poet, Poppy, Porter, Prosper, Quill, Quincy, Rain, Reed, Reeve, Remy, Rex, Rhea, Ridge, Riven, Roan, Rogue, Roman, Rook, Rowan, Rune, Sable, Sage, Sailor, Saxon, Scout, Sequoia, Shane, Shiloh, Sierra, Sloane, Sol, Solstice, Soren, Sparrow, Star, Stone, Storm, Story, Sullivan, Sylvan, Talon, Tamsin, Tate, Teague, Teal, Thane, Thatcher, Thorn, Thornton, Tide, Torin, True, Vail, Valor, Veda, Vesper, Vince, Violette, Wade, Waverly, Wells, West, Wilder, Willow, Winter, Wren, Wynn, Xander, Xanthe, Xavier, Yara, York, Yule, Zane, Zara, Zephyr, Zinnia |
| Last Name | Abernathy, Ainsworth, Alberts, Ashcroft, Atwater, Babcock, Bader, Bagley, Bainbridge, Balfour, Barkley, Barlowe, Barnhill, Biddle, Billingsley, Birkett, Blakemore, Bleeker, Bliss, Bonham, Boswell, Braddock, Braithwaite, Briggs, Brockman, Bromley, Broughton, Burkhardt, Cadwallader, Calloway, Carmichael, Carrington, Cavanaugh, Chadwick, Chamberlain, Chilton, Claffey, Claypool, Clifton, Coffey, Colfax, Colquitt, Conway, Copley, Cotswold, Creighton, Crenshaw, Crowder, Culpepper, Cunningham, Dallimore, Darlington, Davenport, Delaney, Devlin, Doolittle, Dover, Driscoll, Dudley, Dunleavy, Eldridge, Elston, Fairfax, Farnsworth, Fitzgerald, Fitzroy, Flanders, Fleetwood, Gainsborough, Gatling, Goddard, Goodwin, Granger, Greenfield, Griffiths, Harcourt, Hargrove, Harkness, Haverford, Hawkins, Hawthorne, Heathcote, Holbrook, Hollingworth, Holloway, Holmes, Holtz, Howland, Ingles, Jardine, Kenworthy, Kingsley, Langford, Latham, Lathrop, Lockhart, Lodge, Loxley, Lyndon, MacAlister, MacGregor, Mansfield, Marston, Mather, Middleton, Millington, Milton, Montague, Montgomery, Montoya, Morgenthal, Mortimer, Nash, Newcomb, Newkirk, Nightingale, Norwood, Oakley, Ormsby, Osborne, Overton, Pemberton, Pennington, Percival, Pickering, Prescott, Prichard, Quimby, Radcliffe, Rafferty, Rainier, Ramsay, Rawlins, Renshaw, Ridley, Rivers, Rockwell, Roosevelt, Rothschild, Rutherford, Sanderson, Sedgwick, Selwyn, Severance, Sheffield, Sheridan, Sherwood, Shields, Sinclair, Slater, Somerset, Standish, Stanton, Stoddard, Stokes, Stratford, Strickland, Sutherland, Sutton, Talmadge, Tanner, Tennyson, Thackeray, Thatcher, Thorne, Thurston, Tilden, Townsend, Trent, Trevelyan, Trumbull, Underhill, Vanderbilt, Vandermeer, Vickers, Wadsworth, Wakefield, Walpole, Waring, Warwick, Weatherford, Webster, Wharton, Whittaker, Wickham, Wiggins, Wilcox, Winslow, Winthrop, Wolcott, Woodruff, Wycliffe, Yardley, Yates, Yeats, Yule, Zeller, Zimmerman |{{< /table-caption >}}
> 🔼 이 표는 논문의 데이터셋 구성 방법을 설명하는 부분에 포함되어 있으며, 합성 데이터셋을 생성할 때 사용된 이름(이름, 중간 이름, 성) 목록을 보여줍니다.  각 열에는 이름, 중간 이름, 성에 대해 가능한 모든 값들이 나열되어 있습니다. 이 표는 논문에서 사용된 합성 데이터셋의 다양성을 보여주는 데 중요한 역할을 합니다.  실제 데이터셋은 이 표에 제시된 이름들을 조합하여 생성되었습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: All possible values generated for the first name, middle name and last name.
> </details>

{{< table-caption >}}
| Relation | Possible Attributes |
|---|---| 
| City | "Princeton, NJ", "New York, NY", "Los Angeles, CA", "Chicago, IL", "Houston, TX", "Phoenix, AZ", "Philadelphia, PA", "San Antonio, TX", "San Diego, CA", "Dallas, TX", "San Jose, CA", "Austin, TX", "Jacksonville, FL", "Fort Worth, TX", "Columbus, OH", "San Francisco, CA", "Charlotte, NC", "Indianapolis, IN", "Seattle, WA", "Denver, CO", "Washington, DC", "Boston, MA", "El Paso, TX", "Nashville, TN", "Detroit, MI", "Oklahoma City, OK", "Portland, OR", "Las Vegas, NV", "Memphis, TN", "Louisville, KY", "Baltimore, MD", "Milwaukee, WI", "Albuquerque, NM", "Tucson, AZ", "Fresno, CA", "Mesa, AZ", "Sacramento, CA", "Atlanta, GA", "Kansas City, MO", "Colorado Springs, CO", "Miami, FL", "Raleigh, NC", "Omaha, NE", "Long Beach, CA", "Virginia Beach, VA", "Oakland, CA", "Minneapolis, MN", "Tulsa, OK", "Arlington, TX", "Tampa, FL", "New Orleans, LA", "Wichita, KS", "Cleveland, OH", "Bakersfield, CA", "Aurora, CO", "Anaheim, CA", "Honolulu, HI", "Santa Ana, CA", "Riverside, CA", "Corpus Christi, TX", "Lexington, KY", "Stockton, CA", "Henderson, NV", "Saint Paul, MN", "St. Louis, MO", "Cincinnati, OH", "Pittsburgh, PA", "Greensboro, NC", "Anchorage, AK", "Plano, TX", "Lincoln, NE", "Orlando, FL", "Irvine, CA", "Newark, NJ", "Toledo, OH", "Durham, NC", "Chula Vista, CA", "Fort Wayne, IN", "Jersey City, NJ", "St. Petersburg, FL", "Laredo, TX", "Madison, WI", "Chandler, AZ", "Buffalo, NY", "Lubbock, TX", "Scottsdale, AZ", "Reno, NV", "Glendale, AZ", "Gilbert, AZ", "Winston-Salem, NC", "North Las Vegas, NV", "Norfolk, VA", "Chesapeake, VA", "Garland, TX", "Irving, TX", "Hialeah, FL", "Fremont, CA", "Boise, ID", "Richmond, VA", "Baton Rouge, LA", "Spokane, WA", "Des Moines, IA", "Tacoma, WA", "San Bernardino, CA", "Modesto, CA", "Fontana, CA", "Santa Clarita, CA", "Birmingham, AL", "Oxnard, CA", "Fayetteville, NC", "Moreno Valley, CA", "Rochester, NY", "Glendale, CA", "Huntington Beach, CA", "Salt Lake City, UT", "Grand Rapids, MI", "Amarillo, TX", "Yonkers, NY", "Aurora, IL", "Montgomery, AL", "Akron, OH", "Little Rock, AR", "Huntsville, AL", "Augusta, GA", "Port St. Lucie, FL", "Grand Prairie, TX", "Columbus, GA", "Tallahassee, FL", "Overland Park, KS", "Tempe, AZ", "McKinney, TX", "Mobile, AL", "Cape Coral, FL", "Shreveport, LA", "Frisco, TX", "Knoxville, TN", "Worcester, MA", "Brownsville, TX", "Vancouver, WA", "Fort Lauderdale, FL", "Sioux Falls, SD", "Ontario, CA", "Chattanooga, TN", "Providence, RI", "Newport News, VA", "Rancho Cucamonga, CA", "Santa Rosa, CA", "Peoria, AZ", "Oceanside, CA", "Elk Grove, CA", "Salem, OR", "Pembroke Pines, FL", "Eugene, OR", "Garden Grove, CA", "Cary, NC", "Fort Collins, CO", "Corona, CA", "Springfield, MO", "Jackson, MS", "Alexandria, VA", "Hayward, CA", "Clarksville, TN", "Lancaster, CA", "Lakewood, CO", "Palmdale, CA", "Salinas, CA", "Hollywood, FL", "Pasadena, TX", "Sunnyvale, CA", "Macon, GA", "Pomona, CA", "Escondido, CA", "Killeen, TX", "Naperville, IL", "Joliet, IL", "Bellevue, WA", "Rockford, IL", "Savannah, GA", "Paterson, NJ", "Torrance, CA", "Bridgeport, CT", "McAllen, TX", "Mesquite, TX", "Syracuse, NY", "Midland, TX", "Pasadena, CA", "Murfreesboro, TN", "Miramar, FL", "Dayton, OH", "Fullerton, CA", "Olathe, KS", "Orange, CA", "Thornton, CO", "Roseville, CA", "Denton, TX", "Waco, TX", "Surprise, AZ", "Carrollton, TX", "West Valley City, UT", "Charleston, SC", "Warren, MI", "Hampton, VA", "Gainesville, FL", "Visalia, CA", "Coral Springs, FL", "Columbia, SC", "Cedar Rapids, IA", "Sterling Heights, MI", "New Haven, CT", "Stamford, CT", "Concord, CA", "Kent, WA", "Santa Clara, CA", "Elizabeth, NJ", "Round Rock, TX", "Thousand Oaks, CA", "Lafayette, LA", "Athens, GA", "Topeka, KS", "Simi Valley, CA", "Fargo, ND"|{{< /table-caption >}}
> 🔼 이 표는 논문의 데이터셋 구성 방법을 설명하는 부분에 포함되어 있으며, 합성 데이터셋을 생성할 때 사용된 도시 이름 목록을 보여줍니다. 총 100개 이상의 미국 도시들이 포함되어 있으며, 각 도시는 주 이름과 함께 표기되어 있습니다.  연구에서는 이러한 도시 이름들을 사용하여 합성된 인물들의 출생지를 나타내는 데 사용했습니다.  즉, 논문에서 사용된 합성 데이터의 다양성을 확보하기 위해 폭넓게 선택된 도시 목록이라고 할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: All possible attributes generated for city relation.
> </details>

{{< table-caption >}}
| Relation | Possible Attributes |
|---|---| 
| Major | Accounting, Actuarial Science, Advertising, Aerospace Engineering, African American Studies, Agribusiness, Agricultural Engineering, Agriculture, Agronomy, Animal Science, Anthropology, Applied Mathematics, Architecture, Art History, Arts Management, Astronomy, Astrophysics, Athletic Training, Atmospheric Sciences, Biochemistry, Bioengineering, Biological Sciences, Biology, Biomedical Engineering, Biotechnology, Botany, Broadcast Journalism, Business Administration, Business Analytics, Business Economics, Business Information Systems, Chemical Engineering, Chemistry, Civil Engineering, Classics, Cognitive Science, Communication Studies, Communications, Comparative Literature, Computer Engineering, Computer Science, Construction Management, Counseling, Creative Writing, Criminal Justice, Criminology, Culinary Arts, Cybersecurity, Dance, Data Science, Dietetics, Digital Media, Drama, Earth Sciences, Ecology, Economics, Education, Electrical Engineering, Elementary Education, Engineering Physics, Engineering Technology, English, Entrepreneurship, Environmental Engineering, Environmental Science, Environmental Studies, Exercise Science, Fashion Design, Fashion Merchandising, Film Studies, Finance, Fine Arts, Fisheries and Wildlife, Food Science, Forensic Science, Forestry, French, Game Design, Genetics, Geography, Geology, German, Global Studies, Graphic Design, Health Administration, Health Education, Health Informatics, Health Sciences, Healthcare Management, History, Horticulture, Hospitality Management, Human Development, Human Resources Management, Human Services, Industrial Engineering, Information Systems, Information Technology, Interior Design, International Business, International Relations, Journalism, Kinesiology, Labor Studies, Landscape Architecture, Latin American Studies, Law, Legal Studies, Liberal Arts, Linguistics, Management, Management Information Systems, Marine Biology, Marketing, Mass Communications, Materials Science, Mathematics, Mechanical Engineering, Media Studies, Medical Technology, Medicine, Microbiology, Molecular Biology, Music, Music Education, Music Performance, Neuroscience, Nursing, Nutrition, Occupational Therapy, Oceanography, Operations Management, Optometry, Organizational Leadership, Paleontology, Paralegal Studies, Pharmacy, Philosophy, Photography, Physical Education, Physical Therapy, Physics, Physiology, Political Science, Pre-Dental, Pre-Law, Pre-Med, Pre-Pharmacy, Pre-Veterinary, Psychology, Public Administration, Public Health, Public Policy, Public Relations, Quantitative Analysis, Radiologic Technology, Real Estate, Recreation Management, Religious Studies, Renewable Energy, Respiratory Therapy, Risk Management, Robotics, Rural Studies, Sales, Social Work, Sociology, Software Engineering, Spanish, Special Education, Speech Pathology, Sports Management, Statistics, Supply Chain Management, Sustainability, Telecommunications, Theater, Tourism Management, Toxicology, Transportation, Urban Planning, Veterinary Medicine, Victimology, Video Production, Web Development, Wildlife Conservation, Women’s Studies, Zoology|}{{< /table-caption >}}
> 🔼 이 표는 논문의 방법론 섹션에 포함되어 있으며, 합성 데이터셋을 구성하는 데 사용된 전공(major) 정보의 모든 가능한 속성 값들을 보여줍니다.  각 전공은 학문 분야를 나타내는 문자열로 표현되며, 다양한 학문 분야들을 포괄하고 있습니다. 이 표는 모델이 학습할 새로운 지식의 유형과 빈도를 제어하기 위한 데이터셋 구성 과정을 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 5: All possible attributes generated for major relation.
> </details>

{{< table-caption >}}
| Relation | Possible Attributes |
|---|---| 
| Company | Apple, Microsoft, Amazon, Google, Facebook, Berkshire Hathaway, Visa, Johnson & Johnson, Walmart, Procter & Gamble, Nvidia, JPMorgan Chase, Home Depot, Mastercard, UnitedHealth Group, Verizon Communications, Pfizer, Chevron, Intel, Cisco Systems, Merck & Co., Coca-Cola, PepsiCo, Walt Disney, AbbVie, Comcast, Bank of America, ExxonMobil, Thermo Fisher Scientific, McDonald’s, Nike, AT&T, Abbott Laboratories, Wells Fargo, Amgen, Oracle, Costco Wholesale, Salesforce, Medtronic, Bristol-Myers Squibb, Starbucks, IBM, NextEra Energy, Broadcom, Danaher, Qualcomm, General Electric, Honeywell, Citigroup, Lockheed Martin, Union Pacific, Goldman Sachs, Raytheon Technologies, American Express, Boeing, Texas Instruments, Gilead Sciences, S&P Global, Deere & Company, Charles Schwab, Colgate-Palmolive, General Motors, Anthem, Philip Morris International, Caterpillar, Target, Intuitive Surgical, Northrop Grumman, Booking Holdings, ConocoPhillips, CVS Health, Altria Group, Eli Lilly and Company, Micron Technology, Fiserv, BlackRock, American Tower, General Dynamics, Lam Research, Zoetis, Applied Materials, Elevance Health, T-Mobile US, Automatic Data Processing, Marsh & McLennan, Mondelez International, Kroger, Crown Castle, Cigna, Analog Devices, FedEx, CSX, Uber Technologies, Moderna, Truist Financial, Kraft Heinz, HCA Healthcare, Dominion Energy, Cognizant Technology Solutions, Occidental Petroleum, Regeneron Pharmaceuticals, Freeport-McMoRan, eBay, O’Reilly Automotive, Southern Company, Duke Energy, Sherwin-Williams, PayPal, Nucor, Gartner, AutoZone, Cheniere Energy, ServiceNow, Constellation Brands, Discover Financial, U.S. Bancorp, Public Storage, Aflac, Lennar, Johnson Controls, Tyson Foods, Sempra Energy, Southwest Airlines, Las Vegas Sands, McKesson, Baxter International, KLA Corporation, Monster Beverage, Archer Daniels Midland, Eaton, Paccar, Illumina, Intercontinental Exchange, Clorox, Capital One Financial, Estee Lauder, Hess, Becton Dickinson, Parker-Hannifin, Cummins, Ameriprise Financial, Fidelity National Information Services, State Street, Xilinx, Chipotle Mexican Grill, Expeditors International, Roper Technologies, L3Harris Technologies, M&T Bank, Alcoa, Live Nation Entertainment, Marriott International, Norfolk Southern, DISH Network, Akamai Technologies, Fortinet, Ball Corporation, Corning, Nordstrom, CMS Energy, Nasdaq, BorgWarner, Liberty Media, Sealed Air, PulteGroup, General Mills, Ross Stores, Hewlett Packard Enterprise, Host Hotels & Resorts, Hilton Worldwide, Snap-on, Zebra Technologies, Leidos, Lincoln National, Weyerhaeuser, CarMax, Rockwell Automation, Allstate, Entergy, NRG Energy, AutoNation, LyondellBasell, Omnicom Group, HollyFrontier, Western Digital, International Flavors & Fragrances, Eastman Chemical, Xcel Energy, Xylem, Ansys, IPG Photonics, Digital Realty, First Solar, Jacobs Engineering, Cognex, Ingersoll Rand, Fastenal, Allegion, LKQ, AMETEK, WABCO Holdings, Keysight Technologies |{{< /table-caption >}}
> 🔼 이 표는 논문의 데이터셋 구성 방법을 설명하는 부분에 포함되어 있으며, 회사(company) 관계에 대해 생성된 모든 속성 값들을 보여줍니다.  각 속성 값들은 실제 존재하는 회사 이름들로 구성되어 있으며, 다양한 산업 분야와 규모의 회사들이 포함되어 있습니다.  이 표의 데이터는 합성 데이터셋을 구성하는 데 사용되었으며, 언어 모델이 새로운 지식을 습득하는 과정을 시뮬레이션하는 데 활용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 6: All possible attributes generated for company relation.
> </details>

{{< table-caption >}}
| Relation | Possible Attributes |
|---|---| 
| University | Massachusetts Institute of Technology, Harvard University, Stanford University, California Institute of Technology, University of Chicago, Princeton University, Columbia University, Yale University, University of Pennsylvania, University of California, Berkeley, University of California, Los Angeles, University of Michigan, Ann Arbor, Duke University, Johns Hopkins University, Northwestern University, New York University, University of California, San Diego, University of Southern California, Cornell University, Rice University, University of California, Santa Barbara, University of Washington, University of Texas at Austin, University of Wisconsin-Madison, University of Illinois at Urbana-Champaign, University of North Carolina at Chapel Hill, Washington University in St. Louis, University of Florida, University of Virginia, Carnegie Mellon University, Emory University, Georgetown University, University of California, Irvine, University of Notre Dame, University of Rochester, Boston College, Boston University, Ohio State University, Pennsylvania State University, University of Miami, Purdue University, University of Minnesota, University of Maryland, Michigan State University, University of Colorado Boulder, University of Pittsburgh, University of Arizona, University of Utah, University of California, Davis, University of Massachusetts Amherst, Indiana University Bloomington, University of Connecticut, University of Iowa, University of Missouri, University of Kansas, University of Kentucky, University of Tennessee, University of Alabama, University of Oklahoma, University of Oregon, University of Nebraska-Lincoln, University of South Carolina, University of New Hampshire, University of Vermont, University of Delaware, University of Rhode Island, University of Arkansas, Auburn University, Baylor University, Brigham Young University, Clemson University, Colorado State University, Drexel University, Florida State University, George Washington University, Howard University, Iowa State University, Kansas State University, Louisiana State University, Marquette University, Mississippi State University, North Carolina State University, Northeastern University, Oklahoma State University, Oregon State University, Rutgers University, San Diego State University, Southern Methodist University, Stony Brook University, Syracuse University, Temple University, Texas A&M University, Texas Tech University, Tulane University, University of Alabama at Birmingham, University of Central Florida, University of Cincinnati, University of Dayton, University of Denver, University of Georgia, University of Houston, University of Idaho, University of Louisville, University of Maryland, Baltimore County, University of Memphis, University of Mississippi, University of Nevada, Las Vegas, University of New Mexico, University of North Texas, University of San Francisco, University of South Florida, University of Texas at Dallas, University of Toledo, University of Tulsa, University of Wyoming, Villanova University, Virginia Tech, Wake Forest University, West Virginia University, Wichita State University, Worcester Polytechnic Institute, Xavier University, Yeshiva University, American University, Arizona State University, Arkansas State University, Ball State University, Boise State University, Bowling Green State University, Bradley University, California Polytechnic State University, California State University, Long Beach, Central Michigan University, Chapman University, City University of New York, Claremont McKenna College, Clark University, College of William & Mary, DePaul University, Eastern Michigan University, Fairfield University, Florida Atlantic University, Fordham University, Hofstra University, Illinois Institute of Technology, James Madison University, Loyola Marymount University, Loyola University Chicago, Miami University, Middlebury College, New Jersey Institute of Technology, Northern Arizona University, Northern Illinois University, Pepperdine University, Pomona College, Rensselaer Polytechnic Institute, Rhode Island School of Design, Rollins College, Saint Louis University, San Francisco State University, San Jose State University, Santa Clara University, Seattle University, Seton Hall University, Southern Illinois University, Stevens Institute of Technology, SUNY College of Environmental Science and Forestry, SUNY Polytechnic Institute, Texas Christian University, The New School, Towson University, Trinity College, Trinity University, Tufts University, Union College, University at Albany, University at Buffalo, University of Akron, University of Alabama in Huntsville, University of Alaska Anchorage, University of Alaska Fairbanks, University of Baltimore, University of Bridgeport, University of Central Arkansas, University of Charleston, University of Dayton, University of Detroit Mercy, University of Evansville, University of Hartford, University of La Verne, University of Mary Washington, University of Michigan-Dearborn, University of Michigan-Flint, University of Montana, University of Nebraska Omaha, University of Nevada, Reno, University of North Dakota, University of North Florida, University of Northern Colorado, University of Redlands, University of Richmond, University of Saint Joseph, University of San Diego, University of Scranton, University of Sioux Falls, University of South Alabama, University of Southern Mississippi, University of St. Thomas, University of Tampa, University of the Pacific, University of the Sciences, University of Toledo, University of West Georgia, University of Wisconsin-Eau Claire, University of Wisconsin-Green Bay, University of Wisconsin-La Crosse, University of Wisconsin-Milwaukee, University of Wisconsin-Oshkosh, University of Wisconsin-Platteville, University of Wisconsin-River Falls, University of Wisconsin-Stevens Point, University of Wisconsin-Stout, University of Wisconsin-Superior, University of Wisconsin-Whitewater, Ursinus College, Utah State University, Valparaiso University, Vanderbilt University, Vassar College, Villanova University, Virginia Commonwealth University, Wabash College, Wagner College, Wayne State University, Webster University, Weber State University, Wellesley College, Wentworth Institute of Technology, Wesleyan University, Western Carolina University, Western Kentucky University, Western Michigan University, Western Washington University, Westminster College, Whitman College, Whittier College, Willamette University, Williams College, Wittenberg University, Wofford College, Woodbury University, Wright State University, Xavier University, Yale University, York College of Pennsylvania |{{< /table-caption >}}
> 🔼 이 표는 논문의 데이터셋 구성 부분에 포함되어 있으며, 합성 데이터셋에 사용된 대학 목록을 보여줍니다.  총 178개의 대학 이름이 포함되어 있으며,  논문에서 새로운 지식을 습득하는 과정을 연구하기 위해 사용된 합성 데이터의 다양성을 보여주는 데 기여합니다.  각 대학 이름은 모델의 사전 학습 단계에 존재하지 않는 가상의 데이터를 생성하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 7: All possible attributes generated for university relation.
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