---
title: "Baichuan-Omni-1.5 Technical Report"
summary: "Baichuan-Omni-1.5: 텍스트, 이미지, 비디오, 오디오를 통합 처리하는 최첨단 다중 모달 LLM"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Vision-Language Models", "🏢 Baichuan Inc.",]
showSummary: true
date: 2025-01-26
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.15368 {{< /keyword >}}
{{< keyword icon="writer" >}} Yadong Li et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-28 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.15368" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.15368" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/baichuan-omni-1-5-technical-report" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

최근 몇 년 동안 대규모 언어 모델(LLM)은 자연어 처리 분야에서 괄목할 만한 발전을 이루었지만, 다양한 모달리티(텍스트, 이미지, 오디오, 비디오)를 이해하고 생성하는 능력은 여전히 부족했습니다. 기존의 다중 모달 LLM들은 각 모달리티를 별도로 처리하거나, 모달리티 간 충돌로 인해 성능 저하를 겪는 경우가 많았습니다.  특히, 의료 영상 이해와 같은 전문 분야에서의 활용은 제한적이었습니다. 이러한 문제점들을 해결하기 위해, 본 연구에서는 Baichuan-Omni-1.5라는 새로운 다중 모달 LLM을 제안합니다. Baichuan-Omni-1.5는 텍스트, 이미지, 비디오, 오디오 데이터를 종합적으로 학습하여, 다양한 모달리티 간의 상호 작용과 이해 능력을 향상시켰습니다.  특히, 의료 영상 데이터를 활용한 학습을 통해 의료 분야에서 높은 정확도를 달성하였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 다양한 모달리티를 통합적으로 이해하고 생성하는 능력을 갖춘 최첨단 다중 모달 LLM인 Baichuan-Omni-1.5를 소개합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 의료 영상 이해를 포함한 다양한 벤치마크에서 최첨단 성능을 달성했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 모델 아키텍처, 고품질 데이터셋, 그리고 다단계 훈련 전략에 대한 자세한 정보를 제공합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **다양한 모달리티(텍스트, 이미지, 비디오, 오디오)를 통합적으로 처리하는 능력**을 갖춘 최첨단 다중 모달 대규모 언어 모델(MLLM)을 제시하여, **현재 연구 동향을 선도하고 미래 연구 방향을 제시**한다는 점에서 중요합니다.  특히, 의료 영상 이해 분야에서 우수한 성능을 보여주어 실제 의료 분야 응용 가능성을 높였으며, **오픈소스로 공개**되어 학계 및 산업계의 폭넓은 활용이 예상됩니다.  향후 다중 모달 모델 개발 및 응용 연구에 중요한 기준점을 제공할 것입니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.15368/extracted/6156374/figures/performance.png)

> 🔼 그림 1은 Baichuan-Omni-1.5 모델의 이미지, 비디오 및 오디오 모달리티 평가 결과를 보여줍니다. 왼쪽 그래프는 Baichuan-Omni-1.5가 Qwen2 VL [142] 및 기타 최첨단 다모달 모델(VITA-1.5 [45], MiniCPM-0 2.6 [165])보다 더 많은 모달리티를 다루고 성능이 우수함을 보여줍니다. 오른쪽 그래프는 모든 모달리티에 대한 벤치마크 평균 점수를 나타내며, 점수는 xnorm=(x−xmin+10)/(xmax−xmin+10) 공식으로 정규화되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Evaluation across image, video, and audio modalities. (Left) Baichuan-Omni-1.5 covers more modalities than Qwen2 VL [142] and outperforms the current leading omni-modal model, VITA-1.5 [45] and MiniCPM-o 2.6[165]. (Right) Average scores across benchmarks for all modalities. All the scores are normalized by xnorm=(x−xmin+10)/(xmax−xmin+10)subscript𝑥norm𝑥subscript𝑥min10subscript𝑥maxsubscript𝑥min10x_{\text{norm}}=(x-x_{\text{min}}+10)/(x_{\text{max}}-x_{\text{min}}+10)italic_x start_POSTSUBSCRIPT norm end_POSTSUBSCRIPT = ( italic_x - italic_x start_POSTSUBSCRIPT min end_POSTSUBSCRIPT + 10 ) / ( italic_x start_POSTSUBSCRIPT max end_POSTSUBSCRIPT - italic_x start_POSTSUBSCRIPT min end_POSTSUBSCRIPT + 10 ).
> </details>





{{< table-caption >}}
| Phase | Type | Public Datasets | Public | In-House |
|---|---|---|---|---|
| Pretrain | Pure-Text | - | - | 150.7M |
|  | Caption | [86][67][189][23] | 33.2M | 49.1M |
|  | Interleaved | [71] | 19.1M | 28.7M |
|  | OCR | [57] | 12.4M | 7.8M |
| Total | - | - | 71.3M | 238.2M |{{< /table-caption >}}

> 🔼 이 표는 논문의 이미지 사전 학습 데이터 통계를 자세히 보여줍니다.  'Phase', 'Type', 'Public Datasets', 'Public In-House', 'OCR', 'Total'의 열이 있으며, 각 열은 이미지 사전 학습 데이터의 세부 정보를 보여줍니다.  'Phase'는 데이터 수집 단계를 나타내고, 'Type'은 데이터 유형(Pure-Text, Caption, Interleaved)을 나타내며, 'Public Datasets'와 'Public In-House'는 각각 공개 데이터셋과 내부 데이터셋에서 사용된 데이터 양을 나타냅니다. 'OCR' 열은 광학 문자 인식(OCR) 데이터의 양을 보여주며, 'Total'열은 각 단계의 총 데이터 양을 보여줍니다. 이 표는 논문에서 사용된 이미지 데이터의 규모와 다양성을 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Detailed statistics of the training data of image pretrain.
> </details>





### In-depth insights


#### Omni-modal prowess
본 논문에서 제시된 옴니모달 모델은 텍스트, 이미지, 오디오, 비디오 등 다양한 모달리티를 통합하여 **매우 우수한 옴니모달 성능**을 보여줍니다. 특히, 기존의 옴니모달 모델들이 특정 모달리티에 치중하거나, 모달리티 간 충돌로 인해 성능 저하를 보이는 것과 달리, 본 논문의 모델은 **모든 모달리티에서 균형잡힌 성능**을 유지합니다.  **데이터 청소 및 합성 파이프라인**을 통해 고품질의 다모달 데이터를 확보하고, **멀티스테이지 학습 전략**을 통해 모달리티 간의 효율적인 상호작용을 구현한 것이 주요 성공 요인입니다.  **의료 영상 이해 분야**에서도 **뛰어난 성능**을 보임으로써, 실제 응용 가능성을 높였습니다.  하지만, 여전히 **모든 모달리티의 완벽한 조화**는 과제로 남아 있으며, 향후 연구를 통해 더욱 개선될 여지가 있습니다. 특히, 긴 비디오 프레임 이해나, 자연 환경 소리 인식 등의 분야는 지속적인 연구개발이 필요합니다.

#### Multimodal training
본 논문에서 제시된 다중 모드 학습 전략은 **단계적 통합**을 강조합니다. 먼저, 이미지와 텍스트 데이터를 사용하여 시각적 정보를 언어 모델에 통합하고, 다음 단계에서 오디오 데이터를 추가하여 다중 감각 정보 처리 능력을 향상시킵니다. 이러한 접근 방식은 각 모드의 특징을 효과적으로 결합하여 **모드 간 충돌을 최소화**하고, **모델의 전체 성능을 향상**시키는 데 기여합니다. 또한, 다양한 데이터 유형을 사용하고, 다양한 학습 단계를 거침으로써 **모델의 일반화 능력과 견고성**을 높일 수 있습니다. 이러한 **단계적 다중 모드 학습 전략**은 다중 모드 이해 및 생성 능력을 균형 있게 발전시키는 데 효과적이며, **차세대 다중 모드 언어 모델 개발**에 중요한 시사점을 제공합니다. 특히, **오디오 토크나이저**와 **플로우 매칭 기반 디코더**의 설계는 오디오 데이터 처리 능력을 향상시키는 데 중요한 역할을 하며, 향후 연구 방향에 대한 중요한 지침을 제공합니다.

#### Audio Branch
논문에서 '오디오 분기(Audio Branch)'는 오디오 데이터를 처리하고 생성하는 모델의 일부분으로, **말소리 인식(ASR), 음성 합성(TTS), 그리고 이들을 융합하는 다양한 작업**을 수행합니다. 이는 텍스트와 오디오 데이터 간의 원활한 상호 작용을 가능하게 하는 중요한 요소입니다.  **Baichuan-Audio-Tokenizer**는 오디오 신호를 이산 토큰으로 변환하는 역할을 하며, **흐름 일치 기반 디코더(flow matching based decoder)**는 오디오 토큰을 다시 음성 파형으로 변환합니다. **잔차 벡터 양자화(RVQ)**와 다목적 훈련을 통해 오디오 토큰화 및 디코더 성능을 최적화하고, **음성의 질을 향상**시키기 위해 다중 스케일 Mel 손실(Multi-scale Mel loss)을 활용합니다.  **텍스트와 오디오의 의미적 정렬**을 유지하기 위해 사전 훈련된 LLM 파라미터는 고정되어 있습니다. 전체적으로 오디오 분기는 **다양한 음성 데이터를 효율적으로 처리하고 고품질의 음성을 생성**하는 핵심 기능을 담당합니다.  **이러한 설계를 통해 모델은 텍스트와 오디오 간의 매끄러운 상호 작용을 실현하고, 다양한 음성 관련 작업에서 우수한 성능**을 보여줍니다.

#### Medical apps
의료 앱은 **모바일 기술을 활용하여 환자의 접근성을 높이고 건강 관리를 개선**할 수 있는 막대한 잠재력을 가지고 있습니다. **원격 진료, 건강 추적, 의료 정보 접근** 등 다양한 기능을 제공하며, 특히 만성 질환 관리 및 환자의 자가 관리 능력 향상에 큰 도움을 줄 수 있습니다. 하지만 개인정보보호, 보안, 정확성 및 신뢰성, 접근성과 관련된 문제점들을 해결해야 합니다. **개인 맞춤형 의료 서비스 제공, 의료 데이터 분석을 통한 예측 및 예방 시스템 구축** 등 의료 앱의 발전 방향은 무궁무진합니다. **규제 및 윤리적 문제**, 사용자 경험 개선, 의료진과의 협력 강화 등을 통해 의료 앱의 안전성과 효용성을 높이고, **의료 서비스의 질적 향상**에 기여할 수 있도록 해야 합니다.

#### Future work
본 논문의 "미래 연구" 부분에 대한 심도있는 고찰은 **다양한 모달 간의 상호작용 및 지식 통합을 개선**하는 데 초점을 맞춰야 합니다. 특히, **음성 및 영상 이해 능력 향상**, **장문의 비디오 프레임 이해**, **자연 환경 소리 인식** 등에 대한 연구가 필요합니다.  **의료 영상 이해 능력의 심화**는 물론, **모델의 설명 가능성 및 신뢰도 향상**에 대한 연구도 중요합니다.  **모델의 효율성 및 확장성을 높이는 연구**와 더불어 **다양한 응용 분야**에 대한 연구도 병행되어야 합니다. 이를 통해 **인간과의 자연스러운 상호작용**이 가능한 진정한 의미의 인공지능 시스템 개발에 한걸음 더 다가갈 수 있을 것입니다.  **윤리적, 사회적 함의에 대한 고려**도 중요한 미래 연구 과제입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.15368/x1.png)

> 🔼 그림 2는 Baichuan-Omni-1.5의 아키텍처를 보여줍니다. 이 모델은 순수 텍스트/오디오 입력과 텍스트/오디오가 포함된 비디오/이미지 조합 모두를 처리하도록 설계되었습니다. 오디오 생성 시 Baichuan-Omni-1.5 LLM 디코더는 텍스트 토큰과 오디오 토큰을 번갈아 예측합니다. 그런 다음 오디오 토큰은 오디오 디코더에 의해 디코딩되어 최종 오디오를 생성합니다.  Baichuan-Omni-1.5는 다양한 모달리티(텍스트, 이미지, 비디오, 오디오)를 통합하여 처리하고, 텍스트, 오디오, 그리고 비디오/이미지 출력을 모두 지원하는 통합 모델임을 보여줍니다.  특히 오디오 생성 과정에서 텍스트와 오디오 토큰의 교차 예측 방식을 통해 매끄러운 다중 모달리티 상호 작용을 가능하게 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Architecture of Baichuan-Omni-1.5 . Our model is designed to process both pure text/audio inputs and combinations of video/image with text/audio. When generating audio, the Baichuan-Omni-1.5 LLM Decoder alternately predicts text tokens and audio tokens. The audio tokens are then decoded by the Audio Decoder to produce the final audio.
> </details>



![](https://arxiv.org/html/2501.15368/extracted/6156374/figures/data_example.png)

> 🔼 그림 3은 Baichuan-Omni-1.5의 사전 학습 데이터 구성을 보여줍니다.  Baichuan-Omni-1.5는 텍스트, 이미지-텍스트, 비디오-텍스트, 오디오-텍스트 데이터와 이들의 조합을 포함한 방대한 옴니모달 데이터셋을 사용합니다.  여기에는 이미지-오디오-텍스트 및 비디오-오디오-텍스트 데이터가 포함되어 있어 다양한 모달리티 간의 상호작용을 포괄적으로 학습할 수 있도록 설계되었습니다.  각 모달리티의 데이터 유형과 크기를 보여주는 표가 함께 제시되어 이해를 돕습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Pretrain Data illustration of Baichuan-Omni-1.5 . We construct an extensive omni-modal dataset, including text, image-text, video-text, audio-text, and their interactions. Our collection also contains interleaved image-audio-text and video-audio-text data.
> </details>



![](https://arxiv.org/html/2501.15368/x2.png)

> 🔼 그림 4는 흐름 일치 모델을 기반으로 하는 오디오 토크나이저와 오디오 디코더의 구조를 보여줍니다. 오디오 토크나이저는 멜 스펙트로그램 특징에서 고차원 특징을 추출하고, 잔차 합성곱 신경망을 사용하여 저주파수 시퀀스 특징을 얻습니다. 그런 다음 8계층 잔차 벡터 양자화기를 사용하여 이러한 특징을 양자화하여 오디오 토큰을 생성합니다. 이러한 토큰은 오디오 디코더와 사전 훈련된 LLM 모두에 입력되어 멜 스펙트로그램 재구성과 전사 예측을 각각 수행합니다. 오디오 디코더는 Whisper 인코더와 대칭적인 구조를 채택하고 다중 스케일 멜 손실을 사용하여 음질 재구성을 향상시킵니다. 훈련 중에 사전 훈련된 LLM의 매개변수는 오디오 토크나이저와 텍스트 공간 간의 의미적 정렬을 보장하기 위해 고정됩니다. 추가적으로 ASR, AQA, S2TT와 같은 기존 작업 외에도 일부 텍스트-오디오 데이터가 통합되어 VQ 모듈이 복잡한 문맥 시나리오를 모델링하는 기능을 향상시킵니다. 합성 오디오의 품질과 지각 충실도를 더욱 향상시키기 위해 오디오 디코더 모듈은 흐름 일치 모델을 사용하여 미세 조정됩니다. U-Net은 단일 다운샘플링 블록, 단일 업샘플링 블록 및 12개의 중간 블록으로 구성됩니다. 흐름 일치 디코더는 24kHz 오디오 데이터로 훈련되어 대상 멜 스펙트로그램을 생성하고, HiFi-GAN 보코더를 사용하여 음성 파형으로 변환됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Audio tokenizer and audio decoder based on flow matching model.
> </details>



![](https://arxiv.org/html/2501.15368/x3.png)

> 🔼 본 그림은 Baichuan-Omni-1.5 모델의 학습 파이프라인을 보여줍니다.  총 4단계로 구성되며, 각 단계는 이미지, 오디오, 비디오 및 텍스트 데이터를 점진적으로 통합하여 모델의 다중 모달 이해 능력을 향상시키는 과정을 나타냅니다. 1단계는 이미지-텍스트 학습에 집중하여 LLM이 시각적 입력을 처리하고 이해하도록 합니다. 2단계는 시각적 데이터로 사전 훈련된 LLM에 Baichuan-Audio-Tokenizer, 새로운 오디오 임베딩 계층 및 독립적인 오디오 헤드를 통합하여 종단 간 오디오 입력을 이해하도록 확장합니다. 3단계는 고품질 다중 모달 상호 작용 데이터셋을 사용하여 Baichuan-Omni-1.5를 훈련하고 최대 시퀀스 길이를 64k로 확장하여 긴 오디오 및 비디오 스트림을 지원합니다. 4단계는 다중 모달 데이터를 사용한 지도 학습 미세 조정을 통해 모델의 지시 사항 따르기 및 오디오 기능을 향상시킵니다. 4.1단계에서는 다중 모달 이해 데이터를 사용하여 오디오 헤드를 고정하여 모달 상호 작용과 다중 작업 이해를 향상시키고, 4.2단계에서는 오디오 헤드와 오디오 임베딩 계층만 활성화하여 오디오 생성 데이터로 음성 생성 기능을 향상시킵니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Training Pipeline of Baichuan-Omni-1.5 . The pretraining phase is divided into three stages to incrementally incorporate vision and audio into the LLM while relieving modality conflicts. Stage 1 focuses on image-text training, which extends an LLM to process and understand visual input. Stage 2 extends an LLM pre-trained on visual data to understand audio input in end-to-end manner by incorporating our Baichuan-Audio-Tokenizer, a newly introduced audio embedding layers and an independent audio head. Stage 3 focuses on training Baichuan-Omni-1.5 using high-quality cross-modal interaction datasets encompassing image-audio-text and video-audio-text format, and extends the maximum sequence length to 64k to support long audio and video stream. Stage 4 enhances the model’s instruction following and audio capabilities through supervised fine-tuning with omni-modal data. Stage 4.1: Freeze the Audio Head using omni-modal understanding data to boost modality interactivity and multitasking comprehension. Stage 4.2: Activate only the Audio Head and Audio Embed layer, with audio generation data to improve speech generation capabilities.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| QA Type | Dataset Name | Public Datasets | Questions |
|---|---|---|---|
| Description | Synthetic Data | - | 300K |
|  | ShareGPT-4o | [29] | 2K |
|  | Koala | [150] | 30M |
| QA | Synthetic Data | [80], [82], [157] | 164K |
|  | VideoChatGPT-Plus | [107] | 318K |
|  | ShareGemini | [131] | 205K |
| Total | - | - | 31M |{{< /table-caption >}}
> 🔼 이 표는 Baichuan-Omni-1.5 모델의 비디오 사전 훈련 데이터셋에 대한 상세 통계를 보여줍니다.  비디오 데이터는 크게 비디오 캡션 데이터와 비디오 질문 답변(QA) 데이터 두 가지 유형으로 나뉩니다.  표에는 각 데이터 유형에 대한 데이터셋 이름, 데이터 유형(QA 또는 캡션), 데이터 원본(퍼블릭 또는 합성), 질문 수, 설명 수 등의 정보가 포함되어 있습니다.  전체 비디오 사전 훈련 데이터셋의 크기를 보여주는 합계 정보도 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Detailed statistics of the training data of video pretrain.
> </details>

{{< table-caption >}}
| Type | Task | Data Format | Hours (k) |
|---|---|---|---|
| Audio Understanding | Automatic Speech Recognition (ASR) | &lt;prompt, audio, transcript&gt; | 185 |
|  | Audio Query Answer (AQA) | &lt;prompt, audio, response&gt; | 21 |
|  | Speech-to-Text Translation (S2TT) | &lt;prompt, audio, translated_text&gt; | 15 |
|  | Audio-Text Interleaved (INTLV) | &lt;audio_1, text_2, audio_3, text_4, ...&gt; | 393 |
| Audio Generation | Text-to-Speech (TTS) | &lt;text, audio&gt; | 51 |
|  | Interleaved Text-to-Speech (ITTS) | &lt;text_1, audio_1, text_2, audio_2, ...&gt; | 142 |
|  | Pure Audio | &lt;audio&gt; | 80 |
| Total | - | - | 887 |{{< /table-caption >}}
> 🔼 본 표는 Baichuan-Omni-1.5 모델의 오디오 전처리 학습 데이터 통계를 자세히 보여줍니다.  데이터 유형(자동 음성 인식, 음성 질문 답변, 음성 텍스트 변환, 오디오 텍스트 삽입, 텍스트 음성 변환, 텍스트 음성 삽입, 순수 오디오), 데이터 형식, 및 각 데이터 유형에 해당하는 시간(시간)을 보여줍니다.  모델 학습에 사용된 다양한 오디오 데이터의 양과 유형을 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Detailed statistics of the training data of audio pretrain.
> </details>

{{< table-caption >}}
| Category | Text | Image | Video | Audio | Image-Audio |
|---|---|---|---|---|---| 
| Quantity | 400K | 16M | 100K | 282K | 60K |{{< /table-caption >}}
> 🔼 본 표는 Baichuan-Omni-1.5 모델의 다중 모드 지도 학습 미세 조정(Supervised Fine-Tuning, SFT) 데이터셋의 통계를 요약한 것입니다.  Baichuan-Omni-1.5 모델 학습에 사용된 다양한 유형의 데이터(텍스트, 이미지, 비디오, 오디오)와 각 유형별 데이터 수량을 보여줍니다.  이는 모델의 다중 모드 이해 능력 향상을 위한 다양한 데이터 소스의 활용을 보여주는 중요한 정보입니다. 표를 통해 모델이 텍스트뿐 아니라 이미지, 비디오, 오디오 데이터를 광범위하게 활용하여 훈련되었음을 알 수 있으며, 이는 범용적인 다중 모드 이해 능력을 갖추도록 하는 데 기여했음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Omni-modal SFT data statistics for Baichuan-Omni-1.5 . Here we summarize the category and quantities of our SFT dataset.
> </details>

{{< table-caption >}}
| Scene | Source | Proportion |
|---|---|---|
| GeneralQA | Leopard-Instruct [61], LLaVA-OneVision-Data [76], MMInstruct-GPT4V [99], the Cauldron [72], GeoGPT4V-1.0 [15], MMDU [102], Lova3 [188], CaD-Inst [14], VisionArena-Battle [25], Q-Instruct-DB [154], MultipanelVQA [41], ConMe [58], FABAInstruct [90], ScienceQA [128], MapQA [16], Others | 32.26% |
| OCR | MathWriting [48], WebSight [73], ST-VQA [11], GQA [60], HME100K [169], UberTextQA [10], OCR-VQA [117], TallyQA [2], SlideVQA [139], VizWiz [10], NorHand-v3 [140], LLaVAR [186], Textualization [40], PViT [182], Others | 26.51% |
| Graphical | DVQA [64], TinyChart [179], Chart2Text [66], ArxivQA [84], ChartLlama [52], InfographicVQA [112], FlowVQA [137], MultiChartQA [194], ChartGemma [111], UniChart [109], TAT-DQA [193], PlotQA [116], FigureQA [65], MMTab [191], Others | 9.04% |
| Mathematics | MathV-360K [132], Geo170k [46], R-COT [34], A-OKVQA [130], Super-CLEVR [94], CLEVR-Math [96], TabMWP [105], GeoQA+ [5], MAVIS [181], Iconqa [106], UniGeo [17], PUMA_VarsityTutors [195], Others | 10.31% |
| Spatiotemporal | CCTSDB2021 [177], SODA10M [51], EmbSpatial [36], LLaVA-VSD [62], SpatialSense [163], SpatialMM [133], Whatsup [12], VSR [180], SpatialSense [163], Others | 2.63% |
| Captioning | TextCaps [134], MMsci [92], Synthetic Data, Others | 8.23% |
| Medical | PubMed [113], HAM10000 [144], PMC-VQA [184], PathVQA [54], AIROGS [30], MedFMC [147], Kvasir-VQA [47], IU X-ray [33], VQA-RAD [70], DME VQA [141], and other specialized medical datasets | 11.02% |{{< /table-caption >}}
> 🔼 표 5는 Baichuan-Omni-1.5 모델의 이미지 SFT(Supervised Fine-Tuning) 데이터셋에 대한 정보를 요약하여 보여줍니다.  이미지 데이터셋은 다양한 작업(과업)에 따라 여러 범주로 나뉘며, 각 범주에 사용된 데이터셋의 출처와 전체 데이터셋에서 차지하는 비율을 보여줍니다.  즉, 각 작업 유형(예: 일반적인 질문응답, OCR, 그래프, 수학, 시공간적 이해, 자막 생성, 의료)에 대해 어떤 데이터셋들이 사용되었고, 각 데이터셋이 전체 이미지 데이터셋에서 얼마나 많은 비중을 차지하는지 나타내는 표입니다.  다양한 데이터 소스를 사용하여 포괄적인 이미지 이해 능력을 확보하기 위한 데이터 구성 전략을 보여주는 표라고 할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Image SFT data for Baichuan-Omni-1.5 . This table summarizes the image SFT dataset categories, their sources, and proportions for various tasks.
> </details>

{{< table-caption >}}
| Model | MMLU (Acc.) | CMMLU (Acc.) | AGIEval (Acc.) | C-Eval (Acc.) | GAOKAO (Acc.) |
|---|---|---|---|---|---| 
| **Comprehensive Tasks** |  |  |  |  |  |
| *Proprietary Models* |  |  |  |  |  |
| GPT-4o | **88.0**<sup>♢</sup> | **78.3**<sup>♢</sup> | **62.3**<sup>♢</sup> | **86.0**<sup>♢</sup> | - |
| GPT-4o-mini | 82.0 | 67.6 | 52.2 | 63.6 | 70.8 |
| *Open-source Models (Pure text)* |  |  |  |  |  |
| MAP-Neo (7B) | 58.2 | 55.1 | 33.9 | 57.5 | - |
| Qwen1.5-Chat (7B) | 61.5 | 68.0 | 39.3 | 68.8 | - |
| Llama3-Instruct (8B) | 67.1 | 51.7 | 38.4 | 50.7 | - |
| OLMo (7B) | 28.4 | 25.6 | 19.9 | 27.3 | - |
| *Open-source Models (Omni-modal)* |  |  |  |  |  |
| VITA (8x7B) | 71.0<sup>∗</sup> | 46.6 | 46.2<sup>∗</sup> | 56.7<sup>∗</sup> | - |
| VITA-1.5 (7B) | 71.0 | 75.1 | 47.9 | 65.6 | 57.4 |
| Baichuan-Omni (7B) | 65.3 | 72.2 | 47.7 | 68.9 | - |
| MiniCPM-o 2.6 (7B) | 65.3 | 63.3 | 50.9 | 61.5 | 56.3 |
| **Baichuan-Omni-1.5 (7B)** | **72.2** | **75.5** | **54.4** | **73.1** | **73.5** |{{< /table-caption >}}
> 🔼 표 6은 다양한 순수 텍스트 벤치마크(MMLU, CMMLU, AGIEval, C-Eval, GAOKAO)에서 여러 언어 모델들의 성능을 비교 분석한 결과를 보여줍니다.  표에는 독점적 모델(GPT-4, GPT-4-mini)과 오픈소스 일반 모델(MAP-Neo, Qwen1.5-Chat, Llama3-Instruct, OLMO), 그리고 오픈소스 다중 모드 모델(VITA, Baichuan-Omni, MiniCPM-0 2.6)의 성능이 포함되어 있습니다.  표에 표시된 괄호 안의 매개변수 수는 LLM의 매개변수 수를 나타내며, 별도로 명시되지 않는 한 모든 결과는 공정한 비교를 위해 동일한 설정으로 재현되었습니다.  표에 표시된 결과 중, ∗ 표시는 공식적으로 보고된 결과이며, ♢ 표시는 공식 리더보드 또는 최근 논문에서 가져온 결과입니다. 나머지 결과는 저자들이 직접 재현한 결과입니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Results on comprehensive pure text benchmarks. ∗*∗: Officially reported results. ♢♢\diamondsuit♢: Retrieved results from official leaderboard or recent papers. Other unlabeled results are reproduced by ourselves.
> </details>

{{< table-caption >}}
| MMLU |
|---|---| 
| (Acc.) |{{< /table-caption >}}
> 🔼 표 7은 다양한 벤치마크에서 다중 선택 및 예/아니오 질문에 대한 여러 다중 모드 및 단일 모드 언어 모델의 성능을 보여줍니다.  표에는 모델 이름, 매개변수 수, 그리고 MMBench-EN, MMBench-CN, SEED-IMG, MMMU(val), HallucinationBench와 같은 여러 벤치마크에서의 정확도(Acc.) 점수가 포함되어 있습니다. 공식적으로 보고된 결과는 별표(*)로, 공식 리더보드 또는 최근 논문에서 가져온 결과는 다이아몬드 기호(♢)로 표시되어 있으며, 나머지 결과는 연구팀이 직접 재현한 것입니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Results on Multi-choice benchmarks and Yes-or-No benchmarks. ∗*∗: Officially reported results. ♢♢\diamondsuit♢: Retrieved results from official leaderboard or recent papers. Other unlabeled results are reproduced by ourselves.
> </details>

{{< table-caption >}}
| CMMLU |
|---|---| 
| (Acc.) |{{< /table-caption >}}
> 🔼 표 8은 이미지 VQA(Visual Question Answering) 벤치마크에 대한 결과를 보여줍니다. 표에는 다양한 모델(독점 모델, 오픈소스 비전-언어 모델, 오픈소스 옴니모달 모델)의 성능이 여러 벤치마크(RealWorldQA, MathVista-mini, TextVQA, ChartQA, OCRBench)에 대해 정확도(Acc.)로 제시되어 있습니다.  * 표시는 공식적으로 보고된 결과를 나타내고, ♢ 표시는 공식 리더보드 또는 최근 논문에서 가져온 결과를 나타냅니다. 나머지 결과는 동일한 설정을 사용하여 재현한 것입니다. 이 표는 Baichuan-Omni-1.5 모델의 이미지 이해 능력을 다양한 최신 모델과 비교하여 보여주는 데 목적이 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Results on image VQA benchmarks. ∗*∗: Officially reported results. ♢♢\diamondsuit♢: Retrieved results from official leaderboard or recent papers. Other unlabeled results are reproduced by ourselves.
> </details>

{{< table-caption >}}
| AGIEval |
|---|---| 
|(Acc.)|{{< /table-caption >}}
> 🔼 표 9는 일반적인 비디오 VQA 벤치마크에 대한 결과를 보여줍니다. 이 표에는 여러 모델(독점 모델, 오픈소스 비전-언어 모델, 오픈소스 옴니모달 모델)의 비디오 이해 성능을 보여주는 다양한 벤치마크(MVBench, Egoschema, VideoMME, Perception Test)에 대한 결과가 포함되어 있습니다.  각 벤치마크에 대한 결과는 정확도(%)로 표시되며, 'max' 열은 비디오에서 샘플링된 최대 프레임 수를 나타냅니다.  '∗∗∗' 표시는 공식적으로 보고된 결과이며, '♢♢ diamonds♢'는 공식 리더보드나 최근 논문에서 가져온 결과이고, 나머지 결과는 본 논문 저자들이 동일한 설정으로 재현한 것입니다. VideoMME 벤치마크의 경우 '자막 없음' 설정을 사용했음을 유의해야 합니다. 이 표는 다양한 모델들의 비디오 이해 능력을 비교 분석하는 데 유용합니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Results on general video VQA benchmarks. max: Maximum number of sampling frames. ∗*∗: Officially reported results. ♢♢\diamondsuit♢: Retrieved results from official leaderboard or recent papers. Other unlabeled results are reproduced by ourselves. Note that we use the 'no subtitles' evaluation setting in VideoMME.
> </details>

{{< table-caption >}}
| C-Eval |
|---|---| 
| (Acc.) |{{< /table-caption >}}
> 🔼 표 10은 개방형 비디오 VQA 벤치마크에 대한 결과를 보여줍니다.  'max'는 샘플링 프레임의 최대 수를 나타내고, ∗ 표시는 공식적으로 보고된 결과를, 나머지는 본 논문에서 재현한 결과임을 나타냅니다. 이 표는 다양한 모델(독점 모델, 오픈소스 비전-언어 모델, 오픈소스 옴니모달 모델)의 비디오 이해 능력을 평가한 여러 개방형 비디오 질의응답 벤치마크(ActivityNet-QA, MSVD-QA)의 결과를 보여줍니다. 각 모델의 정확도(Acc.)와 점수(Score)가 프레임 수와 함께 제시됩니다.  이는 모델의 비디오 이해 능력, 특히 개방형 질문에 대한 응답 능력을 비교 분석하는 데 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Results on open-ended video VQA benchmarks. max: Maximum number of sampling frames. ∗*∗: Officially reported results. Other unlabeled results are reproduced by ourselves.
> </details>

{{< table-caption >}}
| GAOKAO |
|---|---| 
| (Acc.) |{{< /table-caption >}}
> 🔼 표 11은 오디오 이해 벤치마크 결과를 보여줍니다. 세 가지 출력 방식(텍스트 기반, 텍스트-오디오 병렬 출력, 캐스케이드 방식)에 따른 결과가 제시됩니다.  ∇∇∇∇는 모델의 모달리티 매개변수를 ['text', 'audio']로 설정하고, 출력 텍스트를 기반으로 평가한 결과입니다. ♢♢♢♢는 텍스트-오디오 병렬 출력만 지원하는 경우의 결과이고, □□□□는 캐스케이드 방식(텍스트와 오디오가 번갈아 생성되는 방식)을 사용하고, 마찬가지로 출력 텍스트를 기반으로 평가한 결과입니다.  각 벤치마크(Reasoning QA, Llama Questions, Web Questions, TriviaQA, AlpacaEval)에 대한 정확도 점수가 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 11: Results on audio understanding benchmarks. ∇∇\nabla∇: The modalities parameter is set to ['text', 'audio'], evaluation based on the output text. ♢♢\diamondsuit♢: Supports only text-audio interleaved output. □□\square□: Cascade output method, evaluation based on the output text.
> </details>

{{< table-caption >}}
| Model | MMBench-EN (Acc.) | MMBench-CN (Acc.) | SEED-IMG (Acc.) | MMMU (val) (Acc.) | HallusionBench (Acc.) |
|---|---|---|---|---|---| 
| **Multi-choice & Yes-or-No Question** |  |  |  |  |  |
| *Proprietary Models* |  |  |  |  |  |
| GPT-4o | 83.4<sup>♢</sup> | 82.1<sup>♢</sup> | - | **69.1**<sup>♢</sup> | **55.0**<sup>♢</sup> |
| GPT-4o-mini | 77.7 | 76.9 | 72.3 | 59.3 | 45.8 |
| *Open-source Models (Vision-language)* |  |  |  |  |  |
| Qwen2 VL (7B) | 81.7 | 81.9 | **76.5** | 52.7 | 50.6<sup>∗</sup> |
| MiniCPM-Llama3-V 2.5 (8B) | 76.7 | 73.3 | 72.4 | 45.8<sup>∗</sup> | 42.5 |
| *Open-source Models (Omni-modal)* |  |  |  |  |  |
| VITA (8x7B) | 74.7 | 71.4 | 72.6 | 45.3 | 39.7<sup>∗</sup> |
| VITA-1.5 (7B) | 80.8 | 80.2 | 74.2 | 50.8 | 44.8 |
| Baichuan-Omni (7B) | 76.2 | 74.9 | 74.1 | 47.3 | 47.8 |
| MiniCPM-o 2.6 (7B) | 83.6 | 81.8 | 75.4 | 51.1 | 50.1 |
| **Baichuan-Omni-1.5 (7B)** | **85.6** | **83.6** | 75.7 | 53.9 | 49.7 |{{< /table-caption >}}
> 🔼 표 12는 다양한 모달리티(이미지, 오디오, 텍스트)를 결합한 종합적인 이해 능력을 평가한 결과를 보여줍니다. GPT-4o-mini는 오디오 입력을 지원하지 않으므로, 오디오 API를 사용하여 오디오를 텍스트로 변환한 후 입력으로 사용했습니다.  각 열은 이미지와 오디오 또는 텍스트의 조합을 이용한 모델 성능을 나타내며, 이미지와 오디오 전사를 모두 사용했을 때의 결과도 포함되어 있습니다.  각 모델의 성능은 정확도(Acc.)로 측정되었습니다. 이 표는 Baichuan-Omni-1.5 모델의 다양한 모달리티 조합에 대한 강건한 성능을 보여주는 데 중점을 두고 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 12: Overall Omni-Undesratnding Results. All the results are reproduced by ourselves. GPT-4o-mini does not support audio input, we use its audio API and transcribe the audio and then input it.
> </details>

{{< table-caption >}}
| MMBench-EN |
|---|---| 
|(Acc.)|{{< /table-caption >}}
> 🔼 표 13은 의료 관련 벤치마크에서 Baichuan-Omni-1.5 모델의 성능을 보여줍니다.  GPT-4 mini, VITA-1.5, MiniCPM-o 2.6와 같은 다른 모델들과 비교하여 Baichuan-Omni-1.5 의 성능을 평가한 결과를 제시합니다.  GMAI-MMB-VAL 과 OpenMM-Medical 두 가지 벤치마크의 결과가 정확도(Accuracy)로 표시되어 있습니다.  모든 결과는 논문 저자들이 직접 재현한 것입니다.
> <details>
> <summary>read the caption</summary>
> Table 13: Results on medical benchmarks. All the results are reproduced by ourselves.
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