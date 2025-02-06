---
title: "Federated Sketching LoRA: On-Device Collaborative Fine-Tuning of Large Language Models"
summary: "FSLORA: 서로 다른 계산 능력을 가진 장치에서도 효율적으로 대규모 언어 모델을 공동 미세 조정하는 획기적인 연합 학습 기법"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Department of Electrical and Computer Engineering, Purdue University",]
showSummary: true
date: 2025-01-31
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.19389 {{< /keyword >}}
{{< keyword icon="writer" >}} Wenzhi Fang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-05 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.19389" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.19389" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/federated-sketching-lora-on-device" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)을 장치에서 직접 미세 조정하는 것은 점점 더 많은 관심을 받고 있지만, 모델 크기와 데이터 부족으로 인해 어려움이 있습니다. 기존의 연합 학습 기법들은 이러한 문제를 해결하기 위해 노력했지만, 장치 간의 계산 능력 차이로 인한 병목 현상은 여전히 해결되지 않았습니다.  

본 논문에서는 연합 스케칭 LoRA (FSLORA)라는 새로운 방법을 제시하여 이러한 문제를 해결합니다. FSLORA는 서버에서 관리하는 글로벌 LoRA 모듈의 하위 행렬을 선택적으로 업데이트하는 스케칭 메커니즘을 사용합니다. 스케칭 비율을 조정함으로써 장치별 제약 조건에 맞게 유연하게 적응하며, 이론적인 수렴 분석을 통해 스케칭 비율이 수렴 속도에 미치는 영향을 규명합니다. 다양한 데이터 세트와 LLM 모델에 대한 실험을 통해 기존 방법에 비해 FSLORA의 우수한 성능을 보여줍니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 연합 스케칭 LoRA (FSLORA)는 이기종 장치에서의 제약을 고려하여, 효율적인 연합 학습을 가능하게 합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} FSLORA는 스케칭 비율을 조정하여 장치별 통신 및 계산 제약에 유연하게 적응합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 실험 결과, FSLORA는 기존 방법들에 비해 성능이 우수함을 보여줍니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **비균일 환경에서의 분산 학습을 위한 효율적이고 이론적으로 뒷받침되는 솔루션**을 제공하여, **자원 제약이 있는 장치에서 대규모 언어 모델의 미세 조정**에 대한 연구에 중요한 영향을 미칩니다. 이는 현재 **연구 동향과 밀접하게 관련**되어 있으며, **향후 연구를 위한 새로운 방향**을 제시합니다. 특히, **대규모 언어 모델의 효율적인 미세조정 기법**에 대한 연구는 지속적으로 중요하며, 본 연구는 이러한 흐름에 크게 기여할 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.19389/extracted/6169909/Figure/Overview.png)

> 🔼 본 그림은 제안된 방법론을 보여줍니다. 서버는 두 개의 전역 LoRA 모듈을 유지 관리하고, 각 장치는 매 라운드마다 스케치를 통해 전역 LoRA 모듈의 하위 행렬을 적응적으로 업데이트합니다.  더 자세히 설명하면, 서버는 각 장치의 계산 및 통신 제약 조건에 맞게 조정되는 스케치 행렬을 생성합니다. 각 장치는 해당 스케치 행렬을 사용하여 LoRA 모듈의 하위 행렬만 업데이트하고, 업데이트된 하위 행렬을 서버로 전송합니다. 서버는 모든 장치로부터 받은 업데이트를 집계하여 전역 LoRA 모듈을 업데이트하고, 업데이트된 전역 LoRA 모듈을 모든 장치에 다시 배포합니다. 이러한 과정을 반복함으로써, 제안된 방법론은 장치 간의 이기종성을 효율적으로 해결하고, 장치의 제한된 리소스를 활용하여 성능을 향상시킵니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: An illustration of our proposed methodology where the server maintains a pair of global LoRA modules while the devices adaptively update submatrices of the global LoRA modules through sketching during each round.
> </details>





{{< table-caption >}}
| Method | GPU hours | QNLI | MRPC | CoLA | MNLI | RTE | SST-2 | QQP | Avg. |
|---|---|---|---|---|---|---|---|---|---|
| HeteroLoRA | 10.7h | 87.5 ±0.5 | 84.4 ±0.9 | 75.3 ±1.2 | 66.3 ±0.8 | 69.0 ±1.7 | 89.5 ±0.0 | 85.3 ±0.1 | 79.6 |
| FlexLoRA | 12.6h | 88.5 ±0.2 | 81.2 ±0.4 | 77.5 ±1.2 | 63.0 ±0.5 | 62.2 ±1.9 | 92.8 ±0.4 | 87.4 ±0.1 | 78.9 |
| FedStackLoRA | 12.3h | 87.2 ±0.3 | 78.1 ±0.7 | 77.4 ±1.7 | 74.6 ±0.5 | 54.4 ±2.1 | 93.4 ±0.1 | 87.1 ±0.3 | 78.9 |
| FSLoRA | 10.9h | 88.0 ±0.3 | 87.3 ±0.2 | 82.2 ±0.5 | 76.4 ±0.2 | 69.8 ±1.2 | 93.5 ±0.1 | 85.8 ±0.1 | 83.3 |{{< /table-caption >}}

> 🔼 표 5.1은 RoBERTa 모델을 GLUE 벤치마크에서 미세 조정한 결과를 보여줍니다. 세 번의 독립적인 실행에 대한 테스트 정확도를 나타내며, FSLORA가 기존 방법들에 비해 평균 성능이 눈에 띄게 향상되었음을 보여줍니다. 각 방법에 대한 GPU 시간, QNLI, MRPC, COLA, MNLI, RTE, SST-2, QQP 및 평균 정확도가 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5.1: Testing accuracy over 3 independent runs for fine-tuning the RoBERTa model on the GLUE benchmark. FSLoRA achieves a notable improvement in average performance compared to the baselines.
> </details>





### In-depth insights


#### FedAvg & LoRA Fusion
**FedAvg와 LoRA의 결합은 분산 환경에서의 대규모 언어 모델 미세 조정을 위한 효율적인 전략**입니다. FedAvg는 각 장치에서의 지역적 학습과 서버에서의 모델 파라미터 집계를 통해 데이터 프라이버시와 통신 비용을 절감합니다.  **LoRA는 저순위 근사를 통해 모델 파라미터 업데이트의 크기를 줄여 메모리 사용량과 계산 비용을 감소**시키는 기술입니다. 두 기법의 결합은 **각 장치의 제한된 자원 내에서도 효과적인 미세 조정**을 가능하게 합니다.  **그러나 장치 간의 계산 능력과 통신 대역폭의 이질성은 여전히 큰 과제**입니다.  이러한 이질성을 해결하기 위한 추가적인 메커니즘이나 전략이 필요하며, **서버-클라이언트 간의 통신 효율성을 높이는 방안** 또한 중요한 연구 주제가 될 것입니다.  **모델의 수렴 속도와 정확도를 균형 있게 고려**하여 최적의 성능을 달성하는 것이 중요합니다.  특히, **다양한 종류의 하드웨어와 네트워크 환경을 고려한 실험**을 통해 실질적인 효용성을 검증하는 것이 중요할 것입니다.

#### Sketching's Role
본 논문에서 제시된 Federated Sketching LoRA (FSLORA)에서 스케칭의 역할은 **이종적인 기기들의 제한된 자원과 계산 능력을 고려하여 효율적인 분산 학습을 가능하게 하는 것**입니다.  스케칭 기법을 통해 각 기기는 글로벌 LoRA 모듈의 일부분만 선택적으로 업데이트함으로써, 통신 및 계산 비용을 줄입니다.  **스케칭 비율(sketching ratio) 조정을 통해 기기의 통신 및 연산 제약 조건에 유연하게 적응**할 수 있으며, 이는 이종 환경에서의 성능 향상에 기여합니다.  **스케칭은 단순히 통신 오버헤드를 줄이는 것 이상으로, 각 기기에서 계산되는 그래디언트의 희소성(sparsity)을 유도**하여 계산 효율을 높입니다.  **스케칭 비율과 수렴 속도 사이의 균형**을 이루는 것이 중요하며, 이를 위해서는 이론적 분석과 실험적 검증이 필수적입니다.  **이론적 분석은 스케칭 비율이 수렴 속도에 미치는 영향**을 규명하고, 실험을 통해 다양한 데이터셋과 LLM 모델에서 스케칭의 효과를 검증합니다.  **결론적으로 스케칭은 FSLORA의 핵심 구성 요소**로서, 이종 분산 환경에서의 효율적인 LoRA 기반 미세 조정을 가능하게 합니다.

#### Convergence Analysis
본 논문의 "Convergence Analysis" 부분은 제안된 Federated Sketching LoRA (FSLORA) 알고리즘의 수렴성을 이론적으로 분석한 중요한 부분입니다.  **수렴 속도에 영향을 미치는 요소들, 특히 스케칭 비율(sketching ratio)과 이종적인 기기들의 특성을 정량적으로 분석**하여 FSLORA의 효율성을 뒷받침합니다.  **엄밀한 수학적 증명을 통해 수렴 속도에 대한 보장**을 제공하며, **스케칭 비율이 수렴 속도와 통신/계산 비용 간의 균형을 결정**짓는 중요한 변수임을 보여줍니다.  **이종적인 자원 제약 조건 하에서도 수렴성을 보장**하는 FSLORA의 강점을 수학적으로 증명함으로써, 제안된 알고리즘의 신뢰성을 높입니다.  분석 결과는 실험 결과와 일치하며, **이론적 분석과 실험적 검증을 통해 FSLORA의 실용성과 효율성**을 입증합니다.  **다만, 분석에 사용된 가정(assumptions)들의 현실적인 타당성**에 대한 추가적인 논의가 필요할 수 있으며, 보다 복잡한 시나리오에 대한 확장된 분석이 향후 연구 과제로 남아있습니다.

#### Heterogeneity Adapt
연구 제목에서 '이기종 적응(Heterogeneity Adapt)'이라는 용어는 **분산 환경에서의 기기 간 계산 능력 및 통신 대역폭의 차이**를 의미합니다. 이는 기기의 이기종성으로 인해 발생하는 문제점을 해결하기 위한 중요한 요소입니다.  **서버는 모든 기기의 상황을 고려하여** 모델 업데이트 전략을 세워야 하며, 이를 위해 각 기기의 자원 제약 조건을 분석하고, 최적의 계산 및 통신 자원 할당 전략을 수립해야 합니다. 또한, **기기의 성능 차이를 고려한 모델 업데이트 방식**을 설계해야 합니다. 예를 들어, 계산 능력이 낮은 기기에는 작은 크기의 모델 업데이트를 전송하고, 계산 능력이 높은 기기에는 더 큰 크기의 업데이트를 전송하는 방식을 채택할 수 있습니다.  **효율적인 통신 및 계산 자원 관리 전략**을 통해 전체 시스템의 성능을 최적화하는 것이 중요하며, 이를 위한 알고리즘 개발 및 분석이 필수적입니다.  **모델의 정확도와 시스템 효율성 간의 균형**을 유지하는 것이 '이기종 적응'의 핵심 과제입니다.  결론적으로, 이기종 적응은 분산 환경에서의 효율적인 모델 학습 및 배포에 매우 중요한 역할을 하며, **실제 응용 환경의 다양성을 고려한** 섬세한 설계가 필요합니다.

#### Future Works
본 논문은 **연합 학습(Federated Learning)** 환경에서 대규모 언어 모델(LLM)의 효율적인 미세 조정을 위한 새로운 방법론인 **연합 스케칭 LoRA(FSLORA)**를 제안합니다.  미래 연구 방향으로는 **스케칭 기법의 고급화**, **비균일적 자원 분배 환경에 대한 추가적인 연구**, **다양한 LLM 아키텍처 및 데이터셋에 대한 확장성 검증**, 그리고 **프라이버시 보호 강화 기법과의 통합** 등을 고려할 수 있습니다. 특히, **스케칭 비율(sketching ratio)의 최적화**는 성능과 자원 사용량 간의 균형을 맞추는 중요한 과제이며, 이에 대한 심층적인 분석과 최적화 알고리즘 개발이 필요합니다.  더 나아가, **FSLORA의 수렴 속도 분석을 더욱 심화**하여 다양한 하이퍼파라미터 설정에 따른 성능 변화를 예측하고, 이를 바탕으로 **더욱 효율적인 미세 조정 전략을 제시**하는 연구가 필요합니다.  **실제 응용 환경에서의 FSLORA 성능 평가** 또한 중요하며, 다양한 모바일 및 IoT 기기에서의 실험을 통해 실용성을 검증하는 연구가 진행되어야 합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.19389/extracted/6169909/Figure/Results_RoBERTa.png)

> 🔼 그림 2는 RoBERTa 모델을 사용하여 GLUE 벤치마크에서 수행된 FSLORA와 기준 모델들의 수렴 거동을 보여줍니다. 7가지 과제에 대한 평균 테스트 정확도를 나타냅니다. FSLORA는 반복 횟수가 증가함에 따라 다른 기준 모델보다 빠르게 수렴하고 더 높은 정확도에 도달합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Convergence behavior of FSLoRA and baselines on the GLUE benchmark with the RoBERTa model. Testing accuracy is averaged over seven tasks.
> </details>



![](https://arxiv.org/html/2501.19389/extracted/6169909/Figure/Results_RoBERTa_detail.png)

> 🔼 그림 3은 장치당 업로드 용량을 해당 계층의 전체 글로벌 LoRA 모듈 크기의 100배로 설정하고, 스케치 기법을 사용한 FSLoRA와 사용하지 않은 FSLoRA의 성능을 비교한 것입니다. GLUE 벤치마크와 RoBERTa 모델을 사용하여 실험을 수행했습니다. 결과적으로 스케치 기법을 사용한 FSLoRA가 더 나은 성능을 보여주어 스케치 기법의 효과를 검증했습니다. 이 그림은 다양한 크기의 LoRA 모듈에 대해 두 가지 방법의 정확도를 비교하여 스케치 기법의 효과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Comparison between FSLoRA with and without sketching, where the upload budget for devices is set to 100×100\times100 × the full global LoRA modules at the corresponding rank. The experiment is performed on the GLUE benchmark and the RoBERTa model. FSLoRA with sketching obtains a better performance, validating the effectiveness of sketching.
> </details>



![](https://arxiv.org/html/2501.19389/extracted/6169909/Figure/Results_LLaMA_detail.png)

> 🔼 그림 6은 공통 상식 추론 벤치마크와 LLaMA-3.2-3B 모델을 사용하여 스케치 기법을 사용한 FSLORA와 사용하지 않은 FSLORA의 성능을 비교한 것입니다. 각 장치의 업로드 용량은 글로벌 LoRA 모듈 크기의 400배로 설정되었습니다. 실험 결과, 스케치 기법이 모든 과제에서 성능 향상을 가져왔다는 것을 보여줍니다. 8가지 과제의 평균 정확도는 그림 LABEL:fig:rank_varying에 나와 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Comparison of FSLoRA with and without sketching, with an upload budget 400×400\times400 × the global LoRA module size at each rank. This is based on the commonsense reasoning benchmark and the LLaMA-3.2-3B model. We observe that the sketching mechanism improves performance across all considered tasks. The average accuracy of the eight tasks is shown in Figure LABEL:fig:rank_varying.
> </details>



![](https://arxiv.org/html/2501.19389/extracted/6169909/Figure/Impact_global_rank_detail.png)

> 🔼 본 그림은 고정된 크기의 로컬 LoRA 모듈 업데이트를 사용하여 글로벌 LoRA 모듈의 계층에 따른 FSLORA의 성능을 보여줍니다. Commonsense Reasoning 벤치마크와 LLaMA-3.2-3B 모델을 사용하여 실험을 진행했습니다. 글로벌 LoRA 모듈의 계층이 증가함에 따라 FSLORA의 성능이 향상되는 것을 확인할 수 있습니다. 8가지 작업에 대한 평균 정확도는 그림 LABEL:fig:global_rank에 나와 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Impact of the rank of global LoRA modules on FSLoRA, given a fixed rank for the updated submatrices at the devices. This is based on the commonsense reasoning benchmark and the LLaMA-3.2-3B model. Overall, FSLoRA demonstrates improved performance as the global rank increases. The average accuracy of the eight tasks is shown in Figure LABEL:fig:global_rank.
> </details>



![](https://arxiv.org/html/2501.19389/extracted/6169909/Figure/Impact_topk.png)

> 🔼 그림 7은 공통 상식 추론 벤치마크에서 LLaMA-3.2-3B 모델을 사용하여 평가한 top-k 압축 및 스케치 기법 통합의 비교 결과를 보여줍니다. 결과는 두 직교 기법의 조합이 성능을 크게 향상시킨다는 것을 보여주며, 스케치와 top-k 압축을 통합하는 이점을 강조합니다. 보다 구체적으로, x축은 장치당 업로드 통신 부하(MB)를 나타내고 y축은 테스트 정확도를 나타냅니다. 다양한 스케치 비율(ki/r)에서 top-k 압축과 스케치의 성능을 비교하여 스케치 비율이 낮을수록 동일한 통신 비용에 대해 더 높은 테스트 정확도를 달성하여 효율성을 더욱 높이는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Comparison of top-k compression and its integration with sketching, evaluated on the commonsense reasoning benchmark using the LLaMA-3.2-3B model. The results show that combining these two orthogonal techniques significantly enhances performance, demonstrating the benefits of integrating sketching with top-k compression.
> </details>



![](https://arxiv.org/html/2501.19389/extracted/6169909/Figure/More_Device_50_detail.png)

> 🔼 그림 9는 Commonsense Reasoning benchmark 및 LLaMA-3.2-3B 모델을 사용하여 평가한, 스케치 기법 적용 유무에 따른 FSLORA의 성능 비교 결과를 보여줍니다. 각 등급에서 글로벌 LoRA 모듈 크기의 400배에 해당하는 업로드 용량을 사용했으며, 디바이스 수는 50개로 설정했습니다. 스케치 기법을 사용했을 때 모든 과제에서 성능이 향상됨을 알 수 있습니다. 8개 과제의 평균 정확도는 그림 10에 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Comparison of FSLoRA with and without sketching, with an upload budget 400×400\times400 × the global LoRA module size at each rank, evaluated on the commonsense reasoning benchmark and the LLaMA-3.2-3B model. The number of devices is set to 50505050. We observe that the sketching mechanism improves performance across all considered tasks. The average accuracy of the eight tasks is shown in Figure 10.
> </details>



![](https://arxiv.org/html/2501.19389/extracted/6169909/Figure/More_Device_50.png)

> 🔼 그림 10은 공통 상식 추론 벤치마크의 8가지 작업에 대해 평균화된 결과를 보여줍니다. 각 작업에 대해 LLaMA-3.2B 모델을 사용하여 평가했습니다. 장치 수는 50개로 설정하고, 업로드 용량은 각 계층의 글로벌 LoRA 모듈 크기의 400배로 설정했습니다.  FSLORA(Federated Sketching LoRA)와 스케칭 없이 FSLORA를 비교하여 스케칭이 성능 향상에 미치는 영향을 보여줍니다.  각 그래프의 x축은 LoRA 모듈의 계층(rank)을 나타내고, y축은 테스트 정확도를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Comparison of FSLoRA with and without sketching, with an upload budget 400×400\times400 × the global LoRA module size at each rank, evaluated on the LLaMA-3.2-3B model. The number of devices is set to 50505050. The results are averaged over eight tasks from the commonsense reasoning benchmark.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | GPU hours | ARC-c | ARC-e | BoolQ | HellaSwag | OBQA | PIQA | SIQA | WinoGrande | Avg. |
|---|---|---|---|---|---|---|---|---|---|---|
| HeteroLoRA | 44.2h | 69.2 ±0.2 | 84.6 ±0.2 | 68.4 ±0.5 | 80.0 ±0.7 | 69.9 ±0.0 | 77.3 ±0.0 | 68.7 ±0.3 | 72.0 ±0.3 | 73.8 |
| FlexLoRA | 60.8h | 69.9 ±0.3 | 84.7 ±0.4 | 66.9 ±0.2 | 80.5 ±0.4 | 72.3 ±0.1 | 78.1 ±0.2 | 70.4 ±0.4 | 73.3 ±0.5 | 74.5 |
| FedStackLoRA | 56.2h | 67.5 ±0.7 | 83.1 ±0.5 | 65.8 ±0.9 | 78.4 ±0.5 | 69.2 ±0.7 | 75.5 ±0.6 | 67.1 ±0.3 | 71.5 ±0.5 | 72.3 |
| FSLoRA | 44.5h | 73.8 ±0.6 | 86.2 ±0.1 | 68.5 ±0.1 | 83.1 ±1.1 | 78.7 ±0.3 | 82.0 ±0.2 | 75.8 ±0.0 | 74.8 ±0.6 | 77.9 |{{< /table-caption >}}
> 🔼 표 5.2는 LLaMA-3.2-3B 모델을 사용하여 상식 추론 벤치마크에서 미세 조정을 수행한 결과에 대한 테스트 정확도를 보여줍니다. 세 번의 독립적인 실행에 걸쳐 얻은 결과를 보여주며, 각 작업에 대한 평균 정확도를 제시합니다.  FSLORA는 기준 방법들과 비교하여 모든 작업에서 일관되게 성능 향상을 보임을 알 수 있습니다.  이 표는 다양한 상식 추론 작업에서 FSLORA의 효과를 정량적으로 평가합니다.
> <details>
> <summary>read the caption</summary>
> Table 5.2:  Testing accuracy over 3 independent runs for fine-tuning the LLaMA-3.2-3B model on the commonsense reasoning benchmark. FSLoRA demonstrates consistent performance improvement across these tasks compared to baselines.
> </details>

{{< table-caption >}}
| Hyperparameter | RoBERTa & GLUE | LLaMA-3.2-3B & Commensense Reasoning |
|---|---|---|
| Batch size | 16 | 16 |
| LoRA dropout rate | 0.1 | 0.1 |
| Learning rate, γ | 5e-4 | 3e-4 |
| Communication round, T | 200 | 750 |
| Local iteration number, H | 50 | 20 |
| Number of edge devices, N | 20 | 20 |
| Target module | [“query”, “value”, “classification head”] | [“q_proj”, “k_proj”, “v_proj”, “up_proj”, “down_proj”] |{{< /table-caption >}}
> 🔼 표 A.1은 RoBERTa 모델과 GLUE 벤치마크, 그리고 LLaMA-3.2-3B 모델과 상식 추론 벤치마크에 사용된 하이퍼파라미터들을 보여줍니다.  표에는 배치 크기, LoRA 드롭아웃 비율, 학습률, 통신 라운드 수, 로컬 반복 횟수, 에지 디바이스 수, 그리고 목표 모듈 등의 하이퍼파라미터 값들이 각 벤치마크별로 상세하게 제시되어 있습니다. 이 표는 실험 설정의 재현성을 높이고, 다른 연구자들이 동일한 실험 환경을 구축하는 데 도움을 주기 위해 포함되었습니다.
> <details>
> <summary>read the caption</summary>
> Table A.1:  The hyperparameters for RoBERTa & GLUE and LLaMA-3.2-3B & Commensense Reasoning benchmarks.
> </details>

{{< table-caption >}}
| Dataset | Input Template |
|---|---| 
| ARC-c/e | <img src="https://arxiv.org/html/2501.19389/A2.T1.1.1.1.1.1.p1.pic1.png" > | 
| BoolQ | <img src="https://arxiv.org/html/2501.19389/A2.T1.2.2.1.1.1.p1.pic1.png"> | 
| HellaSwag | <img src="https://arxiv.org/html/2501.19389/A2.T1.3.3.1.1.1.p1.pic1.png"> | 
| OBQA | <img src="https://arxiv.org/html/2501.19389/A2.T1.4.4.1.1.1.p1.pic1.png"> | 
| PIQA | <img src="https://arxiv.org/html/2501.19389/A2.T1.5.5.1.1.1.p1.pic1.png"> | 
| SIQA | <img src="https://arxiv.org/html/2501.19389/A2.T1.6.6.1.1.1.p1.pic1.png"> | 
| WinoGrande | <img src="https://arxiv.org/html/2501.19389/A2.T1.7.7.1.1.1.p1.pic1.png"> |{{< /table-caption >}}
> 🔼 표 B.1은 Commonsense170K 데이터셋(Hu et al., 2023)의 프롬프트 템플릿을 보여줍니다.  Commonsense170K 데이터셋은 ARC-c/e, BoolQ, HellaSwag, OBQA, PIQA, SIQA, WinoGrande 등 여러 개의 데이터셋을 합쳐 만든 것으로, 각 데이터셋의 질문 유형과 답변 형식이 다릅니다. 표는 각 데이터셋에 대한 프롬프트(질문)의 예시와 답변 형식을 보여주어, 모델이 각 데이터셋의 질문 유형에 맞춰 답변을 생성하도록 돕는 역할을 합니다.  각 행은 하나의 데이터셋을 나타내고, 'Dataset' 열에는 데이터셋 이름, 'Input Template' 열에는 해당 데이터셋의 질문 템플릿을 설명합니다.
> <details>
> <summary>read the caption</summary>
> Table B.1: The prompt template of the Commonsense170K dataset (Hu et al., 2023).
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