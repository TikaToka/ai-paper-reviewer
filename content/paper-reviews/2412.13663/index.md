---
title: "Smarter, Better, Faster, Longer: A Modern Bidirectional Encoder for Fast, Memory Efficient, and Long Context Finetuning and Inference"
summary: "ModernBERT: 빠르고 메모리 효율적인 장문 컨텍스트 미세 조정 및 추론을 위한 최첨단 양방향 인코더!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Answer.AI",]
showSummary: true
date: 2024-12-18
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.13663 {{< /keyword >}}
{{< keyword icon="writer" >}} Benjamin Warner et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-19 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.13663" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.13663" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/smarter-better-faster-longer-a-modern" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 인코더 전용 트랜스포머 모델은 정보 검색 및 분류 작업에 탁월한 성능을 보였지만, BERT 이후로 성능 개선이 제한적이었습니다.  또한, 기존 모델들은 짧은 시퀀스 길이와 비효율적인 아키텍처로 인해 장문 컨텍스트 처리와 추론 효율성에 제약이 있었습니다.  이러한 문제점들을 해결하기 위한 새로운 모델의 필요성이 제기되었습니다.

본 논문에서는 이러한 문제점들을 해결하기 위해 ModernBERT를 제시합니다. ModernBERT는 최신 모델 최적화 기법을 적용하여 인코더 전용 모델의 성능과 효율성을 크게 향상시켰습니다.  특히, 2조 토큰의 대규모 데이터셋과 최대 8192 토큰의 시퀀스 길이를 지원하며, 다양한 분류 작업과 벡터 검색 작업에서 최첨단 성능을 달성했습니다.  또한, ModernBERT는 기존 모델보다 훨씬 빠르고 메모리 효율적이며, 일반적인 GPU에서 추론이 가능하다는 장점을 가지고 있습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} ModernBERT는 다양한 하류 작업에서 최첨단 성능을 달성했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} ModernBERT는 기존 인코더 모델보다 속도와 메모리 효율성이 뛰어납니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} ModernBERT는 장문 컨텍스트와 코드 데이터를 효과적으로 처리할 수 있습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**본 논문은 효율성과 성능을 모두 향상시킨 최첨단 양방향 인코더 모델인 ModernBERT를 제시하여 인코딩 전용 모델 연구에 중요한 발전을 가져왔습니다.**  **장문 컨텍스트와 코드 데이터를 활용한 훈련을 통해 다양한 하류 작업에서 최첨단 성능을 달성했습니다.** 이는 자연어 처리 및 정보 검색 분야 연구에 중요한 시사점을 제공하며, 향후 연구를 위한 새로운 방향을 제시합니다.  특히, **추론 효율성을 개선하여 실제 애플리케이션에 바로 적용할 수 있는 가능성을 보여줍니다.**

------
#### Visual Insights





{{< table-caption >}}
|       | Model      | IR (DPR) BEIR | IR (DPR) MLDR<sub>OOD</sub> | IR (DPR) MLDR<sub>ID</sub> | IR (ColBERT) BEIR | IR (ColBERT) MLDR<sub>OOD</sub> | NLU | Code GLUE | Code CSN | Code SQA |
| :---- | :--------- | :---------------: | :-----------------------: | :---------------------: | :----------------: | :--------------------------: | :-: | :-------: | :------: | :------: |
| Base  | BERT       | 38.9             | 23.9                      | 32.2                    | 49.0              | 28.1                         | 84.7 | 41.2      | 59.5     |        |
|       | RoBERTa    | 37.7             | 22.9                      | 32.8                    | 48.7              | 28.2                         | 86.4 | 44.3      | 59.6     |        |
|       | DeBERTaV3  | 20.2             | 5.4                       | 13.4                    | 47.1              | 21.9                         | 88.1 | 17.5      | 18.6     |        |
|       | NomicBERT  | 41.0             | 26.7                      | 30.3                    | 49.9              | 61.3                         | 84.0 | 41.6      | 61.4     |        |
|       | GTE-en-MLM | 41.4             | **34.3**                 | 44.4                    | 48.2              | 69.3                         | 85.6 | 44.9      | 71.4     |        |
|       | ModernBERT | **41.6**         | 27.4                      | **51.3**                | **80.2**           | **88.4**                     |     | **56.4**  | **73.6** |        |
| Large | BERT       | 38.9             | 23.3                      | 31.7                    | 49.5              | 28.5                         | 85.2 | 41.6      | 60.8     |        |
|       | RoBERTa    | 41.4             | 22.6                      | 36.1                    | 49.8              | 28.8                         | 88.9 | 47.3      | 68.1     |        |
|       | DeBERTaV3  | 25.6             | 7.1                       | 19.2                    | 46.7              | 23.0                         | **91.4** | 21.2      | 19.7     |        |
|       | GTE-en-MLM | 42.5             | **36.4**                 | 48.9                    | 50.7              | 71.3                         | 87.6 | 40.5      | 66.9     |        |
|       | ModernBERT | **44.0**         | 34.3                      | **52.4**                | **80.4**           | 90.4                         |     | **59.5**  | **83.9** |        |{{< /table-caption >}}

> 🔼 표 1은 다양한 하류 작업에 대한 모든 모델의 결과를 보여줍니다. BEIR, MLDROOD, MLDRID는 검색 성능을, GLUE는 자연어 이해 능력을, CSN은 코드 검색 성능을, SQA는 Stack Overflow 질문 답변 능력을 평가하는 지표입니다. MLDRID는 학습 데이터셋으로 미세 조정된 모델의 성능을, MLDROOD는 학습 데이터셋과 다른 데이터셋으로 평가된 모델의 성능을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Results for all models across an overview of all tasks. CSN refers to CodeSearchNet and SQA to StackQA. MLDRID refers to in-domain (fine-tuned on the training set) evaluation, and MLDROOD to out-of-domain.
> </details>





### In-depth insights


#### ModernBERT: An Overview
ModernBERT는 기존 BERT의 한계를 극복하고 장점을 강화한 최신 양방향 인코더 모델입니다. **속도와 메모리 효율성을 높이고**, 긴 컨텍스트를 처리하는 능력을 향상시켜 **빠르고 효율적인 미세 조정 및 추론**을 가능하게 합니다.  **8192 토큰의 기본 시퀀스 길이**를 지원하며, **Flash Attention**을 사용하여 메모리 효율성을 더욱 높였습니다. 다양한 분류 작업과 검색 작업에서 최첨단 성능을 보이며, 특히 **장문 컨텍스트 검색**에서 뛰어난 성능을 보입니다.  **모듈식 설계**를 통해 실험과 확장이 용이하며, 다양한 하드웨어에서 최적화되어 효율적인 추론을 가능하게 합니다. 다만, 영어 데이터 중심으로 학습되어 다른 언어에 대한 적용성은 제한적일 수 있으며,  **편향된 데이터**의 영향을 받을 수 있습니다.

#### Efficiency Improvements
본 논문에서 제시된 효율성 향상은 크게 두 가지 측면으로 나눌 수 있습니다. 첫째는 **아키텍처 최적화**입니다.  **FlashAttention**과 같은 최신 어텐션 메커니즘을 채택하고, **GeGLU 활성화 함수** 및 **Rotary Positional Embedding**을 사용하여 모델의 속도와 메모리 효율성을 개선했습니다.  둘째는 **모델 설계**입니다.  **Deep & Narrow 아키텍처**를 통해 매개변수 수는 줄이면서도 성능을 유지하고, 하드웨어에 최적화된 디자인으로 추론 속도를 높였습니다. 특히, **Unpadding 기법**을 사용하여 패딩 토큰 처리에 드는 불필요한 연산을 제거함으로써 상당한 성능 향상을 이끌어냈습니다. 이러한 노력은 **GPU 사용 효율 증대**로 이어져, 기존 모델 대비 속도와 메모리 측면에서 모두 우수한 성능을 보여줍니다.  **FlexBERT**라는 모듈형 아키텍처 프레임워크를 통해 추가적인 실험과 연구를 용이하게 했습니다.

#### Downstream Tasks
논문에서 다운스트림 태스크에 대한 심층적인 분석은 **다양한 자연어 처리 작업에서 ModernBERT 모델의 성능을 평가하는 데 중점**을 둡니다.  GLUE 벤치마크를 사용한 자연어 이해(NLU) 작업, BEIR 벤치마크를 통한 정보 검색(IR) 작업, 그리고 CodeSearchNet 및 StackOverflow-QA를 이용한 코드 검색 작업 등의 성능을 측정합니다. 이러한 평가를 통해 ModernBERT가 **기존의 인코더 전용 모델보다 우수한 성능**을 보임을 보여주고, 특히 장문 컨텍스트 및 코드 관련 작업에서 두드러진 성능 향상을 입증합니다.  **ModernBERT의 효율성과 다양한 하위 작업에서의 뛰어난 성능은 여러 응용 분야에서의 실용성을 시사**하며, 추후 연구를 위한 기반을 마련하는 데 기여합니다.  **다양한 데이터셋과 작업에 대한 포괄적인 실험 결과는 ModernBERT의 견고성과 일반화 능력을 강조**합니다. 마지막으로, 장문 컨텍스트 처리에 대한 실험 결과는 특히 주목할 만하며,  이는 차세대 자연어 처리 시스템 구축에 중요한 의미를 지닙니다.

#### Long-Context Retrieval
본 논문에서 다룬 장문 맥락 검색(Long-Context Retrieval)은 **기존의 단순한 키워드 매칭 방식을 넘어, 문장이나 문서의 의미적 맥락까지 고려하여 정보를 검색하는 기술**입니다.  특히, **8192 토큰의 긴 문맥을 처리**할 수 있는 ModernBERT 모델의 성능을 평가하는 데 중점을 두고 있습니다.  단순한 단일 벡터 표현(Single-vector) 방식뿐 아니라, **문서의 각 토큰 벡터를 모두 활용하는 다중 벡터 검색(Multi-vector) 방식**의 성능도 함께 평가하여, ModernBERT의 다양한 검색 환경에서의 적용 가능성을 확인하고 있습니다.  **장문 맥락 검색은 최근 대규모 언어 모델(LLM)의 발전과 함께 더욱 중요해지고 있는 분야**이며, ModernBERT는 이러한 추세에 발맞춰, 효율적이고 정확한 장문 맥락 검색을 가능하게 하는 모델로 제시되고 있습니다.  **특히, 코드 데이터를 포함한 방대한 데이터셋으로 학습**되어, 코드 검색 등 다양한 분야에서의 응용 가능성을 높이고 있습니다.  결과적으로, ModernBERT는 **장문 맥락 검색 분야에서 뛰어난 성능과 효율성을 보이며, 기존 모델들을 능가하는 경쟁력을 확보**하고 있음을 보여줍니다. 

#### Future Research
본 논문은 ModernBERT라는 새로운 양방향 인코더 모델을 제시하며, 기존 인코더 모델들의 성능과 효율성을 능가하는 결과를 보여줍니다.  **미래 연구 방향**으로는 몇 가지 중요한 측면을 고려할 수 있습니다. 첫째, **다양한 언어**에 대한 ModernBERT의 적용성을 확장하는 연구가 필요합니다. 현재 영어에만 집중되어 있으므로, 다국어 데이터를 활용한 추가 학습 및 평가를 통해 성능을 검증해야 합니다. 둘째, **데이터 편향성** 문제를 해결하기 위한 연구가 중요합니다. 웹 데이터 기반 학습의 한계로 인해 발생할 수 있는 편향성을 최소화하기 위해, 다양하고 균형 잡힌 데이터셋을 구축하고, 편향성 완화 기법을 적용하는 연구가 필요합니다. 셋째, **장문 맥락 처리 성능 향상**을 위한 연구가 필요합니다. 본 논문에서 8192 토큰까지의 긴 문장 처리 성능을 보여주었지만, 더욱 긴 맥락을 효과적으로 처리하는 방법을 연구하여 모델의 활용성을 높여야 합니다. 마지막으로, **계산 효율성 향상**을 위한 연구가 필요합니다.  ModernBERT는 효율적인 모델이지만, 추론 속도를 더욱 개선하고, 메모리 사용량을 줄이기 위한 연구가 계속되어야 합니다. 이러한 연구들을 통해 ModernBERT의 실용성을 더욱 높이고, 자연어 처리 분야에 더 큰 기여를 할 수 있을 것입니다.


### More visual insights




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| MLDR<sub>OOD</sub> |
{{< /table-caption >}}
> 🔼 표 2는 NVIDIA RTX 4090에서 10번의 실행에 걸쳐 평균낸 메모리 사용량(최대 배치 크기, BS) 및 추론 속도(초당 수천 토큰) 효율성 결과를 보여줍니다. 지원되지 않는 구성에 대해서는 대시(-)로 표시되어 있습니다.  이 표는 다양한 모델의 메모리 효율성과 처리 속도를 비교하여 ModernBERT의 성능을 보여줍니다.  배치 크기가 클수록 더 많은 데이터를 동시에 처리할 수 있고, 초당 토큰 수가 클수록 추론이 더 빠릅니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Memory (max batch size, BS) and Inference (in thousands of tokens per second) efficiency results on an NVIDIA RTX 4090, averaged over 10 runs. Dashes indicate unsupported configurations.
> </details>

{{< table-caption >}}
| MLDR<sub>ID</sub>|
|---|---|{{< /table-caption >}}
> 🔼 표 3은 ModernBERT 모델의 학습 설정을 보여줍니다. Dropout 이후의 설정들은 모든 학습 단계에서 공유됩니다. 표에는 학습에 사용된 토큰 수, 최대 시퀀스 길이, 배치 크기, 워밍업 단계 토큰 수, 마이크로 배치 크기, 학습률, 학습률 스케줄, 가중치 감쇠, 총 학습 시간, 모델 초기화 방법 등의 정보가 포함되어 있습니다. 특히 학습률 스케줄은 ModernBERT의 성능에 중요한 역할을 하는 것으로 보이며, trapezoidal 스케줄과 1 sqrt 감쇠를 사용합니다. 모델 초기화는 Megatron 방식 또는 기존 ModernBERT-base 모델을 이용합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: ModernBERT training settings. Dropout and below are shared across all phases.
> </details>

{{< table-caption >}}
| GLUE |
|---|---|{{< /table-caption >}}
> 🔼 표 4는 논문의 2.1.1절 'Modern Transformer'에서 ModernBERT 모델의 설계에 대한 세부 정보를 제공합니다.  표에는 ModernBERT 기본 및 대형 모델 모두에 대한 아키텍처 구성 요소(예: 레이어 수, 은닉 크기, 활성화 함수, 정규화 방법 등)의 사양이 자세히 나와 있습니다.  이 표는 ModernBERT 모델의 주요 특징과 다른 모델과의 차이점을 이해하는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: ModernBERT model design
> </details>

{{< table-caption >}}
| CSN |
|---|---|{{< /table-caption >}}
> 🔼 표 5는 GLUE(General Language Understanding Evaluation) 벤치마크의 하위 작업에 대한 다양한 인코더 모델의 성능을 보여줍니다.  GLUE는 자연어 이해(NLU) 작업의 범위를 평가하는 데 사용되는 다중 작업 벤치마크입니다. 이 표는 ModernBERT 모델의 성능을 기존의 다른 인코더 모델(BERT, RoBERTa, DeBERTaV3, MosaicBERT, NomicBERT, GTE-en-MLM)과 비교하여 보여줍니다. 각 모델의 성능은 다양한 하위 작업(예: 문장 분류, 자연어 추론, 문장 짝 비교)에 대한 정확도 또는 F1 점수로 측정됩니다. 표에 제시된 다른 모델들의 결과는 Liu et al.(2019a), Portes et al.(2023), Nussbaum et al.(2024), Zhang et al.(2024), Qiang et al.(2024), He et al.(2023)의 연구에서 가져온 것입니다.
> <details>
> <summary>read the caption</summary>
> Table 5: GLUE Wang et al. (2018) dev set scores. α taken from Table 8 of Liu et al. (2019a), β taken from Table S3 of Portes et al. (2023), γ from Table 2 of Nussbaum et al. (2024), δ from Table 21 of Zhang et al. (2024), ϵ from Table 2 of Qiang et al. (2024) and ζ from Table 3 of He et al. (2023)
> </details>

{{< table-caption >}}
| SQA |
|---|---|{{< /table-caption >}}
> 🔼 표 6은 GLUE 작업에 대한 ModernBERT의 미세 조정 하이퍼파라미터를 보여줍니다.  LR은 학습률, WD는 가중치 감쇠, Ep는 에포크를 나타냅니다. 이 표는 ModernBERT 모델을 GLUE 벤치마크의 다양한 자연어 이해 작업에 적용할 때 사용된 학습률, 가중치 감쇠 및 에포크 수를 자세히 보여줍니다. 각 작업에 대한 최적의 하이퍼파라미터를 찾기 위해 실험적으로 결정된 값들을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Fine-tuning hyperparameters for ModernBERT on GLUE tasks. LR: Learning Rate, WD: Weight Decay, Ep: Epochs.
> </details>

{{< table-caption >}}
|   |   |   | Short |   |   | Long |   |   |
|---|---|---|---|---|---|---|---|---|
|   |   |   | BS | Fixed | Variable | BS | Fixed | Variable |
|---|---|---|---|---|---|---|---|---|
| Base | BERT | 110M | 1096 | **180.4** | 90.2 | – | – | – |
|   | RoBERTa | 125M | 664 | 179.9 | 89.9 | – | – | – |
|   | DeBERTaV3 | 183M | 236 | 70.2 | 35.1 | – | – | – |
|   | NomicBERT | 137M | 588 | 117.1 | 58.5 | 36 | 46.1 | 23.1 |
|   | GTE-en-MLM | 137M | 640 | 123.7 | 61.8 | 38 | 46.8 | 23.4 |
|   | GTE-en-MLM<sub>xformers</sub> | 137M | 640 | 122.5 | 128.6 | 38 | 47.5 | 67.3 |
|   | ModernBERT | 149M | **1604** | 148.1 | **147.3** | **98** | **123.7** | **133.8** |
| Large | BERT | 330M | **792** | **54.4** | 27.2 | – | – | – |
|   | RoBERTa | 355M | 460 | 42.0 | 21.0 | – | – | – |
|   | DeBERTaV3 | 434M | 134 | 24.6 | 12.3 | – | – | – |
|   | GTE-en-MLM | 435M | 472 | 38.7 | 19.3 | 28 | 16.2 | 8.1 |
|   | GTE-en-MLM<sub>xformers</sub> | 435M | 472 | 38.5 | 40.4 | 28 | 16.5 | 22.8 |
|   | ModernBERT | 395M | 770 | 52.3 | **52.9** | **48** | **46.8** | **49.8** |{{< /table-caption >}}
> 🔼 표 7은 BEIR 벤치마크(Thakur et al., 2021)의 단일 벡터 검색 결과를 보여줍니다.  BEIR은 다양한 질문응답 데이터셋을 포함하는 종합적인 정보 검색 벤치마크입니다. 표는 다양한 인코더 모델(BERT, RoBERTa, DeBERTa-v3, NomicBERT, GTE-en-MLM, ModernBERT)에 대한 nDCG@10 점수를 보여주며, 각 모델의 성능을 여러 정보 검색 데이터셋에서 비교합니다. nDCG@10은 상위 10개 검색 결과의 순위 정확도를 측정하는 지표입니다. 이 표는 ModernBERT 모델의 단일 벡터 검색 성능을 다른 모델들과 비교하여 ModernBERT의 효과를 보여주기 위해 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 7: BEIR Thakur et al. (2021) nDCG@10 scores for single-vector retrieval models.
> </details>

{{< table-caption >}}
|                | Pretraining Phase       |                      | Context Extension: Phase One |                        | Context Extension: Phase Two |                        |
|----------------|------------------------|----------------------|-----------------------------|-------------------------|-----------------------------|------------------------|
|                | Base                    | Large                 | Base                         | Large                     | Base                         | Large                     |
| Training Tokens | 1.719 trillion          |                      | 250 billion                 |                        | 50 billion                  |                        |
| Max Sequence Length | 1,024                  |                      | 8,192                        |                        | 8,192                        |                        |
| Batch Size      | 4,608                  | 4,928                 | 72                          | 77                        | 72                          | 78                        |
| Warmup (tokens) | 50 billion              | 10 billion             | -                            | -                         | -                            | -                         |
| Microbatch Size | 96                     | 56                    | 12                          | 7                         | 12                          | 6                         |
| Learning Rate   | 8e-4                   | 5e-4, 5e-5             | 3e-4                         | 5e-5                      | 3e-4                         | 5e-5                      |
| Schedule        | Trapezoidal             |                      | -                            | -                         | 1-sqrt                      |                        |
| Warmup (tokens) | 3 billion               | 2 billion              | -                            | -                         | -                            | -                         |
| Decay (tokens)  | -                       | -                      | -                            | -                         | 50 billion                 |                        |
| Weight Decay    | 1e-5                   | 1e-5, 1e-6             | 1e-5                         | 1e-6                      | 1e-5                         | 1e-6                      |
| Total Time (hours)| 194.2                  | 425.3                 | 39.9                         | 80.7                      | 11.5                         | 21.7                      |
| Training Time (hours) | 191.1                  | 420.4                 | 36.3                         | 75.1                      | 7.5                          | 15.3                      |
| Model Initialization | Megatron                | From Base              | -                            | -                         | -                            | -                         |
| Dropout (attn out)| 0.1                     |                      |                      |                        |                      |                        |
| Dropout (all other layers) | 0.0                     |                      |                      |                        |                      |                        |
| Optimizer       | StableAdamW             |                      |                      |                        |                      |                        |
| Betas           | (0.90, 0.98)           |                      |                      |                        |                      |                        |
| Epsilon         | 1e-06                  |                      |                      |                        |                      |                        |
| Training Hardware | 8x H100                 |                      |                      |                        |                      |                        |
| Training Strategy | Distributed DataParallel |                      |                      |                        |                      |                        |
| Software Libraries | PyTorch 2.4.0, Cuda 12.4.0, Composer 0.24.1, Flash Attention 2.6.3, FA3 commit 32792d3 |                      |                      |                        |                      |                        |{{< /table-caption >}}
> 🔼 표 8은 BEIR (Thakur et al., 2021) 벤치마크의 다중 벡터 검색 작업에서 다양한 인코더 모델의 성능을 nDCG@10 지표를 사용하여 비교한 결과를 보여줍니다.  각 모델은 다양한 데이터셋에서 평가되었으며,  다중 벡터 검색 방식을 사용하여 질의와 문서 간의 유사도를 측정했습니다.  이 표는 ModernBERT 모델이 다중 벡터 검색 작업에서도 우수한 성능을 보임을 보여주는 주요 결과 중 하나입니다.
> <details>
> <summary>read the caption</summary>
> Table 8: BEIR Thakur et al. (2021) nDCG@10 scores for multi-vector retrieval models.
> </details>

{{< table-caption >}}
| Feature | Base | Large |
|---|---|---|
| Vocabulary | 50,368 | 50,368 |
| Unused Tokens | 83 | 83 |
| Layers | 22 | 28 |
| Hidden Size | 768 | 1024 |
| Transformer Block | Pre-Norm | Pre-Norm |
| Activation Function | GeLU | GeLU |
| Linear Bias | False | False |
| Attention | Multi-head | Multi-head |
| Attention Heads | 12 | 16 |
| Global Attention | Every three layers | Every three layers |
| Local Attention Window | 128 | 128 |
| Intermediate Size | 1,152 | 2,624 |
| GLU Expansion | 2,304 | 5,248 |
| Normalization | LayerNorm | LayerNorm |
| Norm Epsilon | 1e-5 | 1e-5 |
| Norm Bias | False | False |
| RoPE theta | 160,000 | 160,000 |
| Local Attn RoPE theta | 10,000 | 10,000 |{{< /table-caption >}}
> 🔼 본 표는 BEIR 데이터셋(Thakur et al., 2021)을 사용하여 단일 벡터 검색과 다중 벡터 검색 모두에 대해 보고된 결과에 사용된 학습률을 보여줍니다.  단일 벡터 검색(DPR)과 다중 벡터 검색(ColBERT)에 대한 결과가 모두 포함되어 있으며, 각 모델 유형(기본 및 대규모)별로 최적의 학습률을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Learning rate used for reported results on BEIR Thakur et al. (2021) for both single and multi vector retrieval
> </details>

{{< table-caption >}}
|       | Model                     | Params | Seq. | CoLA | SST-2 | MRPC | STS-B | QQP  | MNLI | QNLI | RTE  |
| :---- | :------------------------- | :----- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| Base  | BERT<sup>β</sup>           | 110M   | 512   | 59.0 | 93.1 | 89.5 | 89.4 | 91.4 | 85.4 | 91.6 | 78.2 |
|       | RoBERTa<sup>α</sup>         | 125M   | 512   | 63.6 | 94.8 | 90.2 | 91.2 | 91.9 | 87.6 | 92.8 | 78.7 |
|       | DeBERTav3<sup>ϵ</sup>       | 183M   | 512   | **69.2** | 95.6 | 89.5 | 91.6 | **92.4** | **90.0** | **94.0** | 83.8 |
|       | MosaicBERT-128<sup>β</sup> | 137M   | 128   | 58.2 | 93.5 | 89.0 | 90.3 | 92.0 | 85.6 | 91.4 | 83.0 |
|       | NomicBERT-2048<sup>γ</sup>   | 137M   | 2048  | 50.0 | 93.0 | 88.0 | 90.0 | 92.0 | 86.0 | 92.0 | 82.0 |
|       | GTE-en-MLM<sup>δ</sup>     | 137M   | 8192  | 57.0 | 93.4 | 92.1 | 90.2 | 88.8 | 86.7 | 91.9 | 84.8 |
|       | ModernBERT                 | 149M   | 8192  | **96.0** | **92.2** | **91.8** | 92.1 | 89.1 | 93.9 | **87.4** | 65.1 |
| Large | BERT<sup>β</sup>           | 330M   | 512   | 56.2 | 93.3 | 87.8 | 90.6 | 90.9 | 86.3 | 92.8 | 83.8 |
|       | RoBERTa<sup>α</sup>         | 355M   | 512   | 68.0 | 96.4 | 90.9 | 92.4 | 92.2 | 90.2 | 94.7 | 86.6 |
|       | DeBERTav3<sup>ζ</sup>       | 434M   | 512   | **75.3** | 96.9 | 92.2 | **93.3** | **91.8** | **96.0** | **92.7** | 71.4 |
|       | GTE-en-MLM<sup>δ</sup>     | 434M   | 8192  | 60.4 | 95.1 | **93.5** | 89.2 | 89.2 | 93.9 | 88.1 | 71.4 |
|       | ModernBERT                 | 395M   | 8192  | **97.1** | 91.7 | 92.8 | 92.7 | 90.8 | 95.2 | 92.1 | 71.4 |{{< /table-caption >}}
> 🔼 이 표는 논문의 효율성 평가에 사용된 합성 데이터셋에 대한 토큰 통계를 보여줍니다.  'Fixed'는 고정 길이 토큰 시퀀스를, 'Variable'은 가변 길이 토큰 시퀀스를 나타냅니다.  각 데이터셋의 총 토큰 수, 표준편차, 평균 길이, 가장 긴 시퀀스 길이, 가장 짧은 시퀀스 길이, 시퀀스 수가 포함되어 있어, 효율성 평가 시 사용된 데이터의 특징을 상세하게 파악하는 데 도움을 줍니다.  'Short' 와 'Long' 은 각각 짧은 컨텍스트와 긴 컨텍스트를 나타내며,  각 컨텍스트 길이에 따른 데이터셋의 특징을 비교 분석하는 데 유용합니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Token statistics for the synthetic datasets used in efficiency evaluations.
> </details>

{{< table-caption >}}
Task|LR|WD|Ep|LR|WD|Ep
---|---|---|---:|:---:|:---:|---:
CoLA|8e-5|1e-6|5|3e-5|8e-6|5
MNLI|5e-5|5e-6|1|3e-5|1e-5|1
MRPC|5e-5|5e-6|10|8e-5|5e-6|2
QNLI|8e-5|5e-6|2|3e-5|5e-6|2
QQP|5e-5|5e-6|10|5e-5|8e-6|2
RTE|5e-5|1e-5|3|5e-5|8e-6|3
SST-2|8e-5|1e-5|2|1e-5|1e-6|3
STSB|8e-5|5e-6|10|8e-5|1e-5|10{{< /table-caption >}}
> 🔼 표 11은 다양한 모델에 대한 추론 시간을 보여줍니다.  각 모델의 크기(매개변수 수), 배치 크기, 그리고 고정 길이 및 가변 길이 시퀀스에 대한 결과가 나와 있습니다.  '고정 길이'는 모든 시퀀스가 같은 길이(512 또는 8192 토큰)임을 나타내고, '가변 길이'는 시퀀스 길이가 다양함을 나타냅니다. 표에서 굵게 표시된 값은 표준 편차 두 배 이내에서 가장 빠른 추론 시간을 가진 모델을 나타냅니다. 이는 모델의 추론 효율성을 비교하는 데 유용합니다.
> <details>
> <summary>read the caption</summary>
> Table 11: Inference runtime for all models. Bold indicates the best for the column within two SDs.
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