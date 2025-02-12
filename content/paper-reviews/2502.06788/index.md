---
title: "EVEv2: Improved Baselines for Encoder-Free Vision-Language Models"
summary: "EVEv2.0: 인코더 없는 비전-언어 모델의 성능을 획기적으로 향상시킨 새로운 기준."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Vision-Language Models", "🏢 DLUT",]
showSummary: true
date: 2025-02-10
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.06788 {{< /keyword >}}
{{< keyword icon="writer" >}} Haiwen Diao et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-11 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.06788" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.06788" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 인코더 기반 비전-언어 모델(VLM)은 복잡한 구조와 높은 계산 비용으로 인해 효율적인 배포가 어렵다는 문제가 있습니다.  최근 인코더가 없는 VLM이 등장하여 이러한 문제를 해결하고자 하였으나, **인코더 기반 모델과의 성능 차이**를 줄이지 못했습니다.  



본 논문에서는 이러한 문제를 해결하기 위해 **모달 간 간섭 감소 전략**, **효율적인 학습 전략**, 그리고 **모듈 분리 아키텍처(Divide-and-Conquer)**를 적용한 EVEv2.0 모델을 제안합니다.  대규모 데이터셋을 사용한 실험 결과, EVEv2.0 모델은 기존 인코더 없는 VLM을 뛰어넘는 성능을 보였으며, 인코더 기반 모델과의 성능 차이를 상당히 줄였습니다.  **데이터 효율성**과 **비전 추론 능력**에서도 우수한 성능을 보여 향후 인코더 없는 VLM 연구에 새로운 방향을 제시합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 인코더 없는 VLM에서의 모달 간 간섭을 줄이는 효과적인 전략 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 향상된 학습 전략을 통한 인코더 없는 VLM 최적화 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 데이터 효율성과 강력한 비전 추론 능력을 갖춘 EVEv2.0 모델 개발 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **인코더가 없는 비전-언어 모델(VLM)**의 성능 향상에 중점을 두고 있으며, 효율적인 학습 전략과 모델 구조 개선을 통해 기존의 인코더 기반 VLM과의 성능 격차를 줄이는 데 기여합니다. 이는 **데이터 효율성**과 **비전 추론 능력**을 향상시켜 다양한 응용 분야에서의 활용 가능성을 높입니다. 또한, **새로운 벤치마크 결과**를 제시하여 향후 연구 방향을 제시하는 데 기여합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.06788/x1.png)

> 🔼 그림 1은 기존 비전-언어 모델(VLMs)에서 다양한 시각 정보 처리 방식과 인코더 없는 VLMs의 잠재적 아키텍처 변형을 보여줍니다. (1)에서는 기존 VLMs들이 시각적 의미를 추출하기 위해 사전 훈련된 비전 인코더, 이산 토큰화기, 최소한의 시각 레이어를 어떻게 사용하는지 보여주는 다양한 시각 정보 처리 방법을 설명합니다.  CLIP, ViT, VQGAN 등 여러 모델들이 비교 대상으로 제시되며 각 모델의 시각 정보 처리 방식의 차이점을 보여줍니다. (2)에서는 인코더 없는 VLMs의 설계를 위한 몇 가지 잠재적인 아키텍처 변형들을 제시합니다.  원형 아키텍처, 재매개변수화 아키텍처, 전문가 혼합(MoE) 아키텍처, 분할 정복 아키텍처 등이 포함되어 있으며,  각 아키텍처가 시각 정보 처리와 언어 정보 처리 간의 간섭을 줄이고, 효율적인 시각 인식을 구축하는 데 어떻게 접근하는지 보여줍니다.  이 그림은 인코더 없는 VLMs의 특징과 설계 방향을 이해하는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Overview of (1) diverse vision construction inside existing VLMs and (2) potential architecture variants of Encoder-Free VLMs.
> </details>





{{< table-caption >}}
| Stage | Dataset | #Num | Total |
|---|---|---|---| 
| 1 / 2.1 | Datacomp [24] | 44M | 77M |
|  | LAION [59] | 15M |  |
|  | SA-1B [34] | 11M |  |
|  | OpenImages [35] | 7M |  |
| 2.2 | Infinity-MM-GeneralQA [27] | 15M | 15M |
| 3 | LLaVA-onevision [38] | 3.5M | 7.3M |
|  | Infinity-MM-instruct [27] | 3.8M |  |{{< /table-caption >}}

> 🔼 이 표는 논문의 훈련 데이터셋에 대한 세부 정보를 보여줍니다.  총 4가지 단계(Stage)로 나뉘어 있으며, 각 단계별로 사용된 데이터셋의 종류와 개수를 보여줍니다. 특히, 웹 규모의 이미지-텍스트 데이터를 재캡션(re-caption)하기 위해 DenseFusion++라는 방법을 사용했다는 점을 강조하고 있습니다.  각 단계에서 사용된 데이터셋은 이미지 데이터셋(Datacomp, LAION, SA-1B, OpenImages 등)과 질문 답변(QA) 및 다중 모드 대화 데이터셋(LLaVA-onevision, Infinity-MM-instruct 등)으로 구성됩니다.  총 데이터 개수는 단계별로 다르며, 단계가 진행될수록 더 많은 데이터가 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Details of training datasets across all stages. Note that we construct DenseFusion++ to re-caption web-scale image-text data.
> </details>





### In-depth insights


#### Encoder-Free VLMs
본 논문에서 다룬 "Encoder-Free VLMs"는 기존의 Vision-Language Model(VLM)들이 사전 학습된 비전 인코더에 의존하는 것과 달리, **인코더 없이 순수하게 디코더만으로 이미지와 텍스트를 처리**하는 모델을 의미합니다. 이러한 접근 방식은 모델의 구조적 단순화 및 효율적인 배포를 가능하게 하여 통합 멀티모달 시스템의 잠재력을 보여줍니다.  **하지만, 비전 인코더 없이 직접적으로 시각적 정보를 처리하는 데 어려움**이 있으며,  **비전-언어 간의 간섭을 줄이고 효과적인 최적화 전략**이 필요하다는 점이 **중요한 과제**로 제기됩니다. 논문에서는 이러한 과제를 해결하기 위한 다양한 전략들을 제시하고,  **새로운 Encoder-Free VLM인 EVEv2.0**을 통해 기존의 인코더 기반 모델들과의 성능 격차를 줄이는 데 성공합니다.  **모듈 간의 독립성을 강화**하고 **데이터 확장성을 높이는 설계**를 통해 **데이터 효율성과 시각적 추론 성능**을 향상시킨 점이 주요 성과입니다.  이는 **단일 모델 내에서 시각적 인식 및 언어 이해의 통합**이라는 멀티모달 학습의 핵심 목표를 달성하기 위한 중요한 진전을 의미합니다.

#### Modular Design
모듈화 설계는 복잡한 시스템을 독립적인 모듈로 분해하여 개발, 유지보수 및 확장을 용이하게 하는 설계 원칙입니다.  **각 모듈은 특정 기능을 담당하며 다른 모듈과의 상호작용은 명확하게 정의됩니다.** 이를 통해 시스템의 복잡성을 줄이고, 개발 시간을 단축하며, 유지보수 비용을 절감할 수 있습니다.  **모듈 간의 인터페이스는 잘 정의되어야 하며, 모듈 내부의 변경이 다른 모듈에 영향을 미치지 않도록 설계해야 합니다.**  **재사용성 또한 모듈화 설계의 중요한 이점입니다.**  잘 설계된 모듈은 여러 프로젝트에서 재사용될 수 있으며, 이는 개발 시간 및 비용을 크게 절감할 수 있습니다.  **하지만 모듈화 설계는 과도한 모듈 분할로 인해 시스템 통합에 어려움을 초래할 수 있다는 점을 주의해야 합니다.** 따라서 **모듈의 크기와 기능은 신중하게 결정해야 하며, 모듈 간의 상호작용이 효율적으로 이루어지도록 설계되어야 합니다.**  결론적으로, 모듈화 설계는 복잡한 시스템 개발에 있어 효율성과 유지보수성을 높이는 데 필수적인 요소이지만,  **적절한 모듈 크기 및 인터페이스 설계가 중요하며, 과도한 모듈 분할은 피해야 합니다.**

#### Training Strategies
본 논문에서는 효과적인 **Vision-Language Model (VLM) 학습 전략**에 대해 심도있게 논의합니다.  특히, **인코더가 없는 VLM 아키텍처**를 중점적으로 다루며, 기존의 방식과 비교하여 성능 향상을 이끌어낸 핵심 전략들을 분석합니다.  **단계별 학습 방식**을 통해 모델의 안정성과 효율성을 높이고, **모듈 간 간섭을 최소화**하는 방법을 제시합니다.  **데이터 증강 및 다양한 데이터 소스 활용** 전략은 데이터 효율성을 극대화하고, 다양한 시각적 이해 능력을 향상시키는 데 기여합니다.  **모델의 구조적 분할**과 **모듈별 매개변수 분리**는 학습 과정의 안정성과 효율성을 높이는 중요한 요소입니다.  **사전 학습된 언어 모델의 활용**은 시각적 정보 처리 능력을 향상시키지만, 동시에 **모델 간 간섭을 최소화**하는 전략이 병행되어야 함을 강조합니다.  **초기 단계의 사전 학습**은 모델의 기초적인 시각적 이해 능력을 구축하고, 후속 단계의 학습을 위한 토대를 마련합니다.  이러한 다양한 전략의 조합을 통해, 본 연구는 **데이터 효율성**과 **성능**을 동시에 향상시키는 혁신적인 VLM 학습 방식을 제시합니다.

#### Data Efficiency
본 논문에서 다룬 EVEv2.0 모델은 **데이터 효율성** 측면에서 주목할 만한 특징을 보입니다. 기존의 인코더 기반 비전-언어 모델들과 비교했을 때, 훨씬 적은 양의 데이터로도 경쟁력 있는 성능을 달성합니다. 이는 **모델 구조의 효율적인 설계**와 **훈련 전략의 개선** 덕분입니다. 특히, **모듈 간의 간섭을 최소화하는 Divide-and-Conquer 아키텍처**와 **단계적 훈련 과정**을 통해 데이터 활용을 극대화합니다.  **저자들은 대규모 데이터셋을 이용한 사전 훈련** 대신, 효율적인 합성 데이터 생성 전략을 활용하여 데이터 부족 문제를 해결합니다.  이는 **비용 효율적이면서도 성능 저하 없이** 모델을 훈련할 수 있다는 것을 시사합니다.  **데이터 효율성의 향상은** 특히, 대규모 데이터셋 확보가 어려운 상황에서 매우 중요하며,  EVEv2.0 모델은 이러한 문제에 대한 실용적인 해결책을 제시합니다.  이는 향후 **비전-언어 모델 연구의 새로운 방향**을 제시하는 중요한 발견입니다.  **모델의 확장성**과 **실제 응용 가능성**을 높이는데 크게 기여할 것으로 예상됩니다.

#### Future VLMs
미래의 비전-언어 모델(VLMs)은 **모달 간의 간섭을 줄이고, 효율적인 시각적 지각 학습을 가능하게 하며, 확장성을 높이는 방향**으로 발전할 것입니다. 이는 **모달 특징을 분리하고 계층적으로 연결하는 설계**, **효율적인 훈련 전략**, 그리고 **대규모 고품질 데이터셋**의 사용을 통해 달성될 수 있습니다.  **데이터 효율성과 시각적 추론 능력을 향상**시키는 데 중점을 두어, 보다 적은 자원으로도 뛰어난 성능을 내는 모델 개발이 중요해질 것입니다.  또한, 다양한 모달(예: 오디오, 비디오)을 통합하고 실제 응용 분야에 적용 가능하도록 **범용성을 높이는 연구**가 활발해질 것입니다.  **모델의 구조적 단순화**를 통해 배포 및 사용의 용이성을 높이는 것 또한 중요한 발전 방향이 될 것입니다.  **모델의 확장성과 안정성을 확보하는 연구**도 지속될 것이며, 이를 통해 다양한 실제 응용 분야에서 더욱 효과적으로 활용될 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.06788/x2.png)

> 🔼 그림 2는 다양한 VLMs(Vision-Language Models)의 사전 훈련 또는 미세 조정 중 확장 효율성에 대한 예비 분석 결과를 보여줍니다.  자세한 내용은 부록 A를 참조하십시오. 특히, VE(Vision Encoder), DT(Discrete Tokenizer), EVE(Encoder-Free VLM)는 서로 다른 이미지 다운샘플링 비율(1/4, 1/8, 1/32)을 적용합니다. 공정한 비교를 위해, 상대적으로 균형 잡힌 토큰 수(576/1024/625)를 유지하는 약간 다른 해상도를 선택했습니다.  또한, 특정 계층 번호 또는 유형 내에서 절대값 변화의 평균을 통해 LLM(Large Language Model)과 VLM 간의 가중치 변화를 정량화했습니다. GQA [30], SEED [26], TextVQA [60], SQA [53]에 대한 정확도를 보고하여 일반적인 도메인 내, 오픈 도메인, OCR 관련, 텍스트 관련 지식 작업 전반에 걸친 VLM의 기능을 검토합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Preliminary analyses across various VLMs’ scaling efficiency during pre-training or fine-tuning (More details in Appendix A). Notably, VE / DT / EVE apply varying image downsampling rates (142 / 82 / 322). For fairness, we choose slightly different resolutions that yield relatively balanced token counts of 576 / 1024 / 625 tokens per image. Besides, we quantify weight changes between LLMs and VLMs by averaging absolute value variation within specific layer number or type. We report accuracy on GQA [30], SEED [26], TextVQA [60], and SQA [53] to examine VLMs’ capabilities across general in-domain, open-domain, OCR-related, and text-related knowledge tasks.
> </details>



![](https://arxiv.org/html/2502.06788/x3.png)

> 🔼 그림 3은 제안된 EVEv2.0 프레임워크의 개요를 보여줍니다. 먼저 이미지를 손실 없이 인코딩하기 위해 패치 임베딩 계층을 사용한 후, 시각 및 텍스트 토큰을 통합하여 디코더 전용 비전-언어 모델을 만듭니다. 이는 표준 자기 회귀 트랜스포머를 확장하여 다중 헤드 자기 주의 계층, 피드포워드 계층 및 레이어 정규화 각각에 대해 모달 특정 가중치를 통합합니다.  EVEv2.0은 모달 간의 간섭을 최소화하고 효율적인 학습을 가능하게 하도록 설계되었습니다.  패치 임베딩은 이미지 정보를 효율적으로 벡터화하고, 통합된 디코더는 시각 및 언어 정보를 효과적으로 처리합니다.  모달 특정 가중치는 각 모달의 특성을 고려하여 모델의 성능을 향상시키는 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Overview of our proposed EVEv2.0 framework. We first adopt a patch embedding layer to encode images losslessly, and then concatenate visual and textual tokens into a unified decoder-only vision-language model. Here, it extends the standard autoregressive transformer by incorporating modality-specific weights for each multi-head self-attention layer, feed-forward layer, and layer normalization.
> </details>



![](https://arxiv.org/html/2502.06788/x4.png)

> 🔼 본 그림은 논문의 훈련 과정을 보여줍니다. PEL/WEL은 패치/단어 임베딩 레이어를 나타냅니다. 먼저 패치 임베딩 레이어를 훈련하여 여러 모드 간의 초기 정렬을 확립합니다. 그런 다음 LLM 내의 비전 레이어만 업데이트하여 시각적 인식을 점진적으로 향상시킵니다. 특히 이미지 해상도를 800x800에서 1600x1600으로 점진적으로 높이고 원본 이미지 종횡비를 유지합니다. 마지막으로 QA 및 지시 데이터를 통해 전체 모델을 훈련하여 모드 간의 대응 관계와 복잡한 이해를 강화합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Overview of training procedure. PEL/WEL denotes patch/word embedding layer. We begin by training the patch embedding layer to establish initial alignment across modalities. Afterward, we only update vision layers within the LLM to enhance visual perception progressively. Notably, we gradually increase the image resolutions from 800×\times×800 to 1600×\times×1600 and keep the original image aspect ratio. Finally, we train the entire model via QA and instruction data to strengthen cross-modality correspondence and complex understanding.
> </details>



![](https://arxiv.org/html/2502.06788/x7.png)

> 🔼 그림 5는 논문의 실험 과정 중 2단계(Stage 2)에서 다양한 EVE 변형 모델의 학습 손실 곡선과 평가 결과를 보여줍니다. 기준 모델(baseline)로 Qwen-2.5 [70] 기반의 EVE 변형 모델을 사용했습니다. 먼저, 1단계(Stage 1)에서는 EVE-recap-10M 데이터셋을 사용하여 패치 임베딩 레이어를 학습시켰습니다. 그 후, 2단계에서는 LLM 레이어를 제외한 비전 레이어의 가중치를 해제하여 추가 학습을 진행했습니다. 그림은 각 모델의 손실 곡선과 여러 비전-언어 벤치마크에 대한 정확도를 보여주어, 다양한 학습 전략이 모델 성능에 미치는 영향을 분석합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Training loss curve and evaluation results in Stage 2. We adopt various EVE variants based on Qwen-2.5 [70] as the baseline. We first train the patch embedding layer using EVE-recap-10M in Stage 1, and further unfreeze vision layers except LLM layers in Stage 2.
> </details>



![](https://arxiv.org/html/2502.06788/x8.png)

> 🔼 그림 6은 서로 다른 데이터 소스와 캡션 엔진을 사용한 평가 결과를 보여줍니다. 비교 기준으로 Vicuna-7B를 기반으로 하는 EVEv1.0 모델을 사용했습니다.   '*-raw'는 잡음이 많은 웹 이미지 캡션을, '*-cap'는 LLaVA-1.5(13B)와 Emu2(17B) 모두에 의해 주석이 달린 샘플을, '*-recap'는 수정된 DenseFusion++(7B)에 의해 주석이 달린 샘플을 각각 나타냅니다. 'L.O.S.'는 LAION, OpenImages, SAM 데이터셋의 혼합을 의미합니다.  각 그래프는 서로 다른 데이터 소스와 캡션 엔진의 조합에 따른 성능 변화를 보여주며, 데이터 품질과 양이 모델 성능에 미치는 영향을 분석하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Evaluation results of different data sources and caption engines. We utilize EVEv1.0 based on Vicuna-7B [16] as the baseline. Here ”*-raw“, ”*-cap“, or ”*-recap“ denote noisy web image captions, the samples annotated by both LLaVA-1.5 (13B) and Emu2 (17B), or modified DenseFusion++ (7B), respectively. Note that ”L.O.S.“ represents the mixture of LAION [59], OpenImages [35], and SAM [34].
> </details>



![](https://arxiv.org/html/2502.06788/x9.png)

> 🔼 그림 7은 다양한 비율의 혼합 데이터셋을 사용하여 EVEv1.0 모델의 성능을 평가한 결과를 보여줍니다.  Vicuna-7B 언어 모델을 기반으로 EVEv1.0 모델을 검증했습니다. x:y:z는 합성 데이터, 언어 전용 데이터, 웹 데이터의 비율을 나타냅니다. 그래프는 각 데이터 유형의 비율 변화에 따른 모델 성능의 변화를 보여주어, 최적의 데이터 균형을 찾는 데 도움이 됩니다.  다양한 데이터 조합에 따른 모델 성능 변화를 통해, 최적의 데이터 균형을 유지하는 것이 모델 성능 향상에 중요함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Evaluation results of mixed data ratio. We adopt EVEv1.0 with Vicuna-7B [16] for validation. Note that x:y:z denote the proportion of synthesized data : language-only data : web data.
> </details>



![](https://arxiv.org/html/2502.06788/x10.png)

> 🔼 그림 8은 다양한 이미지 설정에 따른 평가 결과를 보여줍니다. Vicuna-7B 언어 모델과 EVEv1.0 비전 모델을 사용하여 네 가지 다른 이미지 처리 방식을 비교합니다.  'AnyRatio_maxL'은 가장 긴 이미지 변의 길이를 800픽셀로 고정하고, 'AnyRatio_LD'는 이미지 면적을 800²픽셀로 고정하며, 'AnyRatio_HD'는 이미지 면적을 1600²픽셀로 고정합니다.  마지막으로 'AnyResolution'은 임의의 해상도를 사용합니다. 각 설정에 따른 여러 비전-언어 벤치마크에서의 성능을 비교 분석하여 이미지 처리 방식이 모델 성능에 미치는 영향을 파악합니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Evaluation results of image settings. We use EVEv1.0 with Vicuna-7B [16]. “AnyRatio_maxL”: longest image edge as 800, “AnyRatio_LD”: fixed image area as 8002, “AnyRatio_HD”: fixed image area as 16002, “AnyResolution”: arbitrary resolution.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | #A-Param | #Data | #Vtoken | MMMU | MMB<sup>en</sup> | SEED<sup>I</sup> | MMV | MME | POPE | GQA | SQA<sup>I</sup> | TQA | CQA | AI2D | RWQA | OCRB |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| *Encoder-based Vision-Language Models:* |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| InternVL-1.5 | 2.2B | – / – | 3328 | 34.6 | 70.9 | 69.8 | 39.3 | 1902 | 88.3 | 61.6 | 84.9 | 70.5 | 74.8 | 69.8 | – | 654 |
| QwenVL-Chat | 7B | 7.2B / 50M | 256 | 35.9 | 60.6 | 58.2 | – | 1848 | – | 57.5 | 68.2 | 61.5 | 49.8 | 45.9 | 49.3 | 488 |
| LLaVA-1.5 | 7B | 0.4B+ / 665K | 576 | 35.3 | 64.3 | 64.3 | 30.5 | 1859 | 85.9 | 62.0 | 66.8 | 46.1 | 18.2 | 54.8 | 54.8 | 318 |
| LLaVA-1.6 | 7B | 0.4B+ / 760K | 2880 | 35.1 | 67.4 | 64.7 | 43.9 | 1842 | 86.4 | 64.2 | 70.2 | 64.9 | 54.8 | 66.6 | 57.8 | 532 |
| Cambrian | 7B | 10B+ / 7M | 576 | 42.7 | 75.9 | 74.7 | – | – | – | – | 64.6 | 80.4 | 71.7 | 73.3 | 73.0 | 64.2 | – |
| LLaVA-OV | 7B | 10B+ / 3.2M | 7290 | 47.3 | 81.7 | 74.8 | 58.8 | 1998 | – | – | 96.6 | – | 78.8 | 81.6 | 65.5 | – |
| *Encoder-free Vision-Language Models:* |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| Fuyu | 8B | – / – | – | 27.9 | 10.7 | – | 21.4 | – | – | – | – | – | – | – | 64.5 | – |
| Chameleon | 7B | 1.4B+ / 1.8M | 1024 | 25.4 | 31.1 | 30.6 | 8.3 | 170 | – | – | 47.2 | 4.8 | 2.9 | 46.0 | – | 7.0 |
| EVE | 7B | 33M / 1.8M | 2304 | 32.6 | 52.3 | 64.6 | 25.7 | 1628 | 85.0 | 62.6 | 64.9 | 56.8 | 59.1 | 61.0 | – | 398 |
| SOLO | 8B | 43.7M / 2M | 1024 | – | – | 64.4 | – | 1260 | – | – | 73.3 | – | – | 61.4 | – | – |
| Mono-InternVL | 1.8B | 1.3B / 7M | 6400 | 33.7 | 65.5 | 67.4 | 40.1 | 1875 | – | 59.5 | 93.6 | 72.6 | 73.7 | 68.6 | – | 767 |
| Emu3 | 8B | – / – | 16K | 31.6 | 58.5 | 68.2 | 37.2 | – | 85.2 | 60.3 | 89.2 | 64.7 | 68.6 | 70.0 | 57.4 | 687 |
| **EVEv2.0** | 7B | 92M / 7.3M | 2500 | **39.3** | **66.3** | **71.4** | **45.0** | 1709 | **87.6** | **62.9** | **96.2** | 71.1 | **73.9** | **74.8** | **62.4** | 702 |{{< /table-caption >}}
> 🔼 표 2는 MMMU [94], MMBench-EN [50], SEEDBench-Img [37], MMVet [93], MME [23], POPE [44], GQA [30], ScienceQA-Img [53], TextVQA [60], ChartQA [55], AI2D [32], RealWorldQA [84], OCRBench [51]를 포함한 다양한 비전-언어 벤치마크에서 기존 비전-언어 모델과의 성능 비교 결과를 보여줍니다.  #A-Param은 활성화된 매개변수의 수, #Data는 사전 훈련/미세 조정 데이터 양, #Vtoken은 최대 이미지 패치 토큰 수를 나타냅니다. MME의 경우 인식 및 인지 점수를 합산했습니다. 최고 성능을 기록한 상위 두 결과는 굵은 글씨체와 밑줄로 표시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Comparison with existing vision-language models on various vision-language benchmarks, including MMMU [94]; MMBenen{}^{\text{en}}start_FLOATSUPERSCRIPT en end_FLOATSUPERSCRIPT: MMBench-EN [50]; SEEDII{}^{\text{I}}start_FLOATSUPERSCRIPT I end_FLOATSUPERSCRIPT: SEEDBench-Img [37]; MMV: MMVet [93]; MME [23]; POPE [44]; GQA [30]; SQAII{}^{\text{I}}start_FLOATSUPERSCRIPT I end_FLOATSUPERSCRIPT: ScienceQA-Img [53]; TVQA: TextVQA [60]; CQA: ChartQA [55]; AI2D [32]; RWQA: RealWorldQA [84]; OCRB: OCRBench [51]. Note that #A-Param denotes the number of activated parameters; #Data represents the pre-training / fine-tuning data volume; #Vtoken indicates the maximum image patch tokens. For MME, we sum up the perception and cognition scores. The best two results are marked in bold and underline.
> </details>

{{< table-caption >}}
| Exp. | Model | LLM | Stage 1 Data | Stage 1 T.M. | Stage 2 Training Data | Stage 2 Trainable Module | Stage 3 Data | Stage 3 T.M. |
|---|---|---|---|---|---|---|---|---|
| Fig.2 (i) | EVEv1.0 | Vicuna-7B | EVE-cap-16M | PEL | EVE-cap-33M | PEL, LLM | LLaVA-mix-665k | PEL, LLM |
| Fig.5 | EVEv1.0 | Qwen2.5-7B | EVE-recap-10M | PEL | EVE-recap-8/29M | PEL | LLaVA-mix-665k | PEL, LLM |
|  | EVEv1.2 | Qwen2.5-7B | EVE-recap-10M | PEL | EVE-recap-8/29M | PEL, VLayers | LLaVA-mix-665k | PEL, LLM |
|  | EVEv1.5 | Qwen2.5-7B | EVE-recap-10M | PEL | EVE-recap-8/29M | PEL, VLayers | LLaVA-mix-665k | PEL, LLM |
|  | EVEv2.0 | Qwen2.5-7B | EVE-recap-10M | PEL | EVE-recap-8/29M | PEL, VLayers | LLaVA-mix-665k | PEL, LLM |
| Fig.6 | EVEv1.0 | Vicuna-7B | 10M varied data | PEL | 8M same data from Stage 1 | PEL, LLM | LLaVA-mix-665k | PEL, LLM |
| Fig.7 | EVEv1.0 | Vicuna-7B | 10M varied data | PEL | 8M same data from Stage 1 | PEL, LLM | LLaVA-mix-665k | PEL, LLM |
| Fig.8 | EVEv1.0 | Vicuna-7B | EVE-recap-10M | PEL | EVE-recap-8/29M | PEL, LLM | LLaVA-mix-665k | PEL, LLM |
| Fig.2 (ii) | EVEv1.0 | Qwen2-7B | EVE-recap-10M | PEL | EVE-recap-29M | PEL | EVE-recap-48M | PEL, LLM |
|  | EVEv1.2 | Qwen2-7B | EVE-recap-10M | PEL | EVE-recap-29M | PEL, VLayers | EVE-recap-48M | PEL, LLM |
| Tab.2 | EVEv2.0 | Qwen2.5-7B | EVE-recap-10M | PEL | EVE-recap-77M | PEL, VLayers | EVE-multi-task-15M | PEL, LLM |
| Fig.9 | EVEv2.0 | Qwen2.5-7B | EVE-recap-10M | PEL | EVE-recap-77M | PEL, VLayers | EVE-multi-task-15M | PEL, LLM |{{< /table-caption >}}
> 🔼 표 3은 논문의 본론에 있는 실험 세부 사항을 보여줍니다.  T.M.은 각 단계에서 훈련 가능한 모듈을 나타냅니다. PEL은 패치 임베딩 계층을, VLayers는 대규모 언어 모델에 새로 추가된 비전 계층을 나타냅니다. EVE-recap-8/29M은 29M 훈련 데이터의 8M 부분집합을 나타냅니다. 이 표는 각 실험 설정에서 사용된 언어 모델, 훈련 데이터, 훈련 가능한 모듈 및 각 단계의 세부 사항을 보여주어, 각 실험의 구성 요소와 데이터 사용 방식을 명확히 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Experiment Details in the main body. Note that T.M. denotes a trainable module in each stage. PEL and VLayers represent patch embedding layers and newly added vision layers in the large language model. EVE-recap-8/29M indicates a subset 8M of 29M training data.
> </details>

{{< table-caption >}}
| Stage | Dataset | #Data |
|---|---|---|
| 2.2 | Cambrian-FL [71], Infinity-Instruct-FL [27],  | 15M |
|  | LVIS-Instruct-FL [77], Sharegpt4v-FL [12], |  |
|  | ALLaVA-laion-FL [11], ALLaVA-vflan-FL [11], |  |
|  | LLaVA-Pretrain-FL [47], DocReason-FL [29], |  |
|  | DocDownstream-FL [29], DocStruct4M-FL [29]. |  |
| 3 | LLaVA-onevision [38], Infinity-MM-Synthesis [27], | 7.3M |
|  | Infinity-MM-Preference [27], Infinity-Instruct-FL [27], |  |
|  | DenseFusion [43], Cambrian-FL [71], Docmatix-FL [36], |  |
|  | LVIS-Instruct-FL [77], BLIP-OCR [17], LLaVA-mix [47]. |  |{{< /table-caption >}}
> 🔼 표 4는 EVEv2.0 미세 조정을 위한 2.2단계와 3단계의 데이터셋 세부 정보를 보여줍니다.  2.2단계는 다양한 질의응답(QA) 데이터셋과 다중 모드 대화 데이터셋을 포함하며, 3단계는 고품질의 다중 모드 지시 데이터셋을 추가로 포함합니다.  각 데이터셋의 이름과 크기가 표에 명시되어 있으며, ***-FL은 필터링된 훈련 데이터셋을 나타냅니다.  이 표는 EVEv2.0 모델의 훈련 과정에서 사용된 데이터셋의 구성과 규모를 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Dataset details in Stage 2.2, and 3 for fine-tuning EVEv2.0. Note that ***-FL denotes the filtered training dataset.
> </details>

{{< table-caption >}}
| Configuration | Stage 1 | Stage 2.1 | Stage 2.2 | Stage 3 |
|---|---|---|---|---|
| Maximum Patch Token | 625 | 625-2500 | 2500 | 2500 |
| Optimizer | AdamW | AdamW | AdamW | AdamW |
| Hyperparameters | $\beta_{1}=0.9,\beta_{2}=0.999,eps=1e^{-8}$ | $\beta_{1}=0.9,\beta_{2}=0.999,eps=1e^{-8}$ | $\beta_{1}=0.9,\beta_{2}=0.999,eps=1e^{-8}$ | $\beta_{1}=0.9,\beta_{2}=0.999,eps=1e^{-8}$ |
| Peak learning rate | $2e^{-4}$ | $1e^{-4}$ | $2e^{-5}$ | $1e^{-5}$ |
| LR schedule | cosine decay with warm-up | cosine decay with warm-up | cosine decay with warm-up | cosine decay with warm-up |
| Warm-up steps | 0.03 | 0.03 | 0.03 | 0.03 |
| Weight decay | 0.0 | 0.0 | 0.0 | 0.0 |
| Global batch size | 1024 | 1024 | 512 | 512 |
| Numerical precision | bfloat16 | bfloat16 | bfloat16 | bfloat16 |{{< /table-caption >}}
> 🔼 표 5는 EVEv2.0 모델을 훈련시키는 동안 1단계, 2단계, 3단계별 하이퍼파라미터 설정을 보여줍니다. 각 단계의 훈련 에폭은 1로 설정되어 있습니다.  표에는 최대 패치 토큰 수, 최적화 알고리즘, 학습률, 학습률 스케줄, 웜업 스텝, 가중치 감쇠, 글로벌 배치 크기, 그리고 수치적 정밀도 등의 하이퍼파라미터 값들이 포함되어 있습니다. 이 표는 모델 훈련의 세부적인 설정을 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Hyper-parameter configurations in Stage 1-3 for training EVEv2.0. Note that we set the training epoch in each stage as 1.
> </details>

{{< table-caption >}}
| User | EVEv2.0 |
|---|---| 
| ![MAR.jpg](https://arxiv.org/html/2502.06788/extracted/6191103/figures/examples/MAR.jpg) | Cornell University We gratefully acknowledge support member. arXiv:2406.11838 Computer Science > Computer Vision and Pattern Recognition Submitted on 17 Jun 2024 (v1), last revised 1 Nov 2024 (this version, v3) Autoregressive Image Generation without Vector Quantization Tianhong Li, Yonglong Tian, He Li, Mingyang Deng, Kaiming He Conventional wisdom holds that autoregressive models for image generation are typically accompanied by vector-quantized tokens. We observe that while a discrete-valued space can facilitate representing a categorical distribution, it is not a necessity for autoregressive modeling. In this work, we propose to model the per-token probability distribution using a diffusion procedure, which allows us to apply autoregressive models in a continuous-valued space. Rather than using categorical cross-entropy loss, we define a Diffusion Loss function to model the per-token probability. This approach eliminates the need for discrete-valued tokenizers. We evaluate its effectiveness across a wide range of cases, including standard autoregressive models and generalized masked autoregressive (MAR) variants. By removing vector quantization, our image generator achieves strong results while enjoying the speed advantage of sequence modeling. We hope this work will motivate the use of autoregressive generation in other continuous-valued domains and applications. Code is available at: this https URL Comments: Neurips 2024 (Spotlight); Code: this https URL Subjects: Computer Vision and Pattern Recognition (cs.CV) Cite as: arXiv:2406.11838 [cs.CV] (or arXiv:2406.11838v3 [cs.CV] for this version) Submission history From: Tianhong Li [view email] [v1] Mon, 17 Jun 2024 17:59:58 UTC (5,459 KB) [v2] Sun, 28 Jul 2024 05:30:08 UTC (5,447 KB) [v3] Fri, 1 Nov 2024 14:45:36 UTC (8,971 KB) |{{< /table-caption >}}
> 🔼 표 6은 EVEv2.0 모델이 웹페이지의 내용을 정확하게 인식하고 이해하는 능력, 특히 광학 문자 인식(OCR) 능력이 뛰어남을 보여주는 예시들을 제시합니다.  단순히 OCR 성능만을 보여주는 것이 아니라, 웹페이지의 레이아웃과 구조를 이해하고,  텍스트 정보를 정확하게 추출하여 보여주는 EVEv2.0 의 우수성을 다양한 예시를 통해 보여줍니다.  이는 단순한 문자 인식을 넘어, 복잡한 웹페이지 구조까지 이해하는 EVEv2.0 의 고급 시각적 이해 능력을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: EVEv2.0 exhibits excellent OCR recognition capabilities in understanding Webpage.
> </details>

{{< table-caption >}}
| User | Please describe the image in detail. |
|---|---| 
| **EVEv2.0** | The image is a promotional poster for ”Neanderthal,” which appears to be a documentary or film about Neanderthals. The title ”Neanderthal” is prominently displayed in large, bold yellow letters across the center of the image. Below the title, there is additional text that reads ”Years 7 and 8 Welcome of the Day,” suggesting that this event might be targeted towards students in those grade levels. The background of the poster features a close-up photograph of a man with a Neanderthal-like appearance. He has a long beard, a prominent forehead, and a strong jawline, which are characteristic features often associated with Neanderthals. The man is holding a wooden stick or pole, which adds to the prehistoric theme of the image. The background behind him is blurred, drawing focus to his face and upper body. At the bottom right corner of the poster, there is more text indicating the date of the event: ”Friday 23 January 2015.” This provides a specific time frame for when the event or release of the documentary/film would have taken place. Overall, the poster uses visual elements such as the Neanderthal figure and the title to convey information about the subject matter, while also providing essential details like the target audience and the date of the event. The design effectively captures attention and communicates key information to viewers. |
|  | ![ocr_beijing.jpg](https://arxiv.org/html/2502.06788/extracted/6191103/figures/examples/ocr_beijing.jpg) |{{< /table-caption >}}
> 🔼 표 7은 EVEv2.0 모델이 PowerPoint 문서 내의 텍스트 정보를 정확하게 인식하고 이해하는 능력, 즉 광학 문자 인식(OCR) 성능을 보여주는 예시들을 제시합니다.  PowerPoint 슬라이드 내의 다양한 텍스트 요소들에 대해 EVEv2.0이 얼마나 정확하게 문자를 인식하고, 이를 바탕으로 슬라이드의 내용을 이해하는지를 보여주는 여러 사례들이 포함되어 있습니다.  이를 통해 EVEv2.0의 강력한 OCR 기능을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: EVEv2.0 exhibits excellent OCR recognition capabilities in understanding PowerPoint.
> </details>

{{< table-caption >}}
| User | Please describe the image in detail. |
|---|---| 
| **EVEv2.0** | In the image, there is a man standing in front of a bathroom mirror, taking a selfie with his cell phone. He is wearing a purple shirt and leopard print pants. The man appears to be smiling as he captures the photo. In the background, there is a potted plant with white flowers placed on the counter near the sink. The sink is white and has a modern design. There is also a poster hanging on the wall next to the mirror. The poster features a silhouette of a person’s head with several circles on it. Below the silhouette, there is text that reads ”COME SETS,” followed by some additional information about Friday night events at Codame.com. The bathroom appears to be well-lit, likely due to natural light coming from a window or another source not visible in the image. The overall atmosphere seems casual and relaxed, with the man enjoying his time in the bathroom while capturing a moment through his phone camera. |
|  | ![background](https://arxiv.org/html/2502.06788/figures/examples/background.jpg) |{{< /table-caption >}}
> 🔼 표 8은 EVEv2.0 모델이 포스터의 내용을 얼마나 잘 이해하는지, 즉 시각적 인식 능력을 보여주는 예시입니다.  포스터의 이미지를 보고, EVEv2.0이 포스터의 제목, 내용, 이미지 속 인물의 특징, 날짜 등을 정확하게 파악하고 설명하는 능력을 보여줍니다.  이는 단순히 이미지를 인식하는 것을 넘어서, 이미지 안의 문맥과 의미까지 이해할 수 있음을 시사합니다.  따라서, 이 표는 EVEv2.0의 강력한 시각적 이해 능력을 보여주는 중요한 근거가 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 8: EVEv2.0 exhibits excellent visual recognition capabilities in understanding Poster.
> </details>

{{< table-caption >}}
| User | Description |
|---|---| 
| **EVEv2.0** | ![mac](https://arxiv.org/html/2502.06788/figures/examples/mac.jpg) The image depicts a well-organized workspace featuring a wooden desk with various items on it. At the center of the desk is a closed silver laptop computer, which has an Apple logo on its lid. This laptop is accompanied by a white keyboard placed directly in front of it, suggesting that the user might prefer using an external keyboard for typing. To the right of the laptop, there is a white wireless mouse, indicating that the user also utilizes a mouse for navigation and other tasks. On the left side of the desk, there is a glass containing a beverage, possibly water or another drink, which is positioned near the edge of the desk. In addition to these items, there are two cylindrical objects resembling speakers, one on each side of the desk. These speakers likely provide audio output for the user while working or listening to music. Behind the desk, there is a bookshelf filled with numerous books, suggesting that the user may have a keen interest in reading or research. The presence of multiple books indicates that this workspace could be used for studying, work, or leisure activities involving reading. Overall, the image portrays a functional and organized workspace designed for productivity and comfort, with essential computing equipment and additional accessories such as speakers and a beverage.|{{< /table-caption >}}
> 🔼 표 9는 EVEv2.0 모델이 실제 세상의 복잡한 시각 정보를 얼마나 잘 이해하는지 보여줍니다.  사진 속의 여러 물체들과 배경, 그리고 그들의 관계를 정확하게 인식하고 설명하는 능력을 평가합니다.  단순히 물체를 인식하는 것을 넘어서, 사진 속의 상황과 분위기까지도 이해하고 자연스럽게 묘사하는 EVEv2.0 의 뛰어난 시각적 이해 능력을 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Table 9: EVEv2.0 exhibits excellent recognition capabilities in the real-world scene.
> </details>

{{< table-caption >}}
| User | EVEv2.0 |
|---|---|---|
| <img src="https://arxiv.org/html/2502.06788/figures/examples/som.png" width="628" height="573"> | In the image, there are three objects marked with numbers: 9, 12, and 15.<br>Object 9: A laptop computer is placed on the desk. It appears to be open and ready for use.<br>Object 12: A lamp is situated near the desk, providing light for the workspace. It has a sleek design and complements the overall aesthetic of the room.<br>Object 15: A potted plant is located on the desk, adding a touch of greenery and life to the space. It contributes to creating a more pleasant and inviting atmosphere in the room. |{{< /table-caption >}}
> 🔼 표 10은 EVEv2.0 모델이 실제 세상의 사진을 얼마나 잘 이해하는지 보여줍니다.  사진 속 사물들을 정확하게 인식하고, 각 사물의 특징과 상호 관계를 자세하게 설명하여, 이미지에 대한 풍부한 이해도를 보여줍니다.  이를 통해 EVEv2.0 모델의 뛰어난 시각적 인식 능력을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 10: EVEv2.0 exhibits excellent recognition capabilities in the real-world scene.
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