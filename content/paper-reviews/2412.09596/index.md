---
title: "InternLM-XComposer2.5-OmniLive: A Comprehensive Multimodal System for Long-term Streaming Video and Audio Interactions"
summary: "InternLM-XComposer2.5-OmniLive: 실시간 스트리밍 비디오 및 오디오 상호작용을 위한 인간의 인지능력을 모방한 혁신적 다중 모드 AI 시스템"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Human-AI Interaction", "🏢 Shanghai Artificial Intelligence Laboratory",]
showSummary: true
date: 2024-12-12
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.09596 {{< /keyword >}}
{{< keyword icon="writer" >}} Pan Zhang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-13 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.09596" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.09596" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/internlm-xcomposer2-5-omnilive-a" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

현존하는 다중 모드 대규모 언어 모델(MLLM)은 순차적 구조로 인해 실시간 스트리밍 데이터 처리와 장기간 상호작용에 어려움을 겪습니다. 특히, 모든 정보를 장기간 유지하는 것은 비용과 효율성 측면에서 비실용적입니다. 이러한 문제를 해결하기 위해 본 연구는 Specialized Generalist AI의 개념에서 영감을 얻어, 실시간 스트리밍 비디오 및 오디오 데이터에 대한 실시간 상호작용을 가능하게 하는 새로운 시스템인 InternLM-XComposer2.5-OmniLive(IXC2.5-OL)을 제시합니다.

IXC2.5-OL은 스트리밍 지각, 다중 모드 장기 기억, 추론 모듈의 세 가지 주요 모듈로 구성됩니다. 스트리밍 지각 모듈은 실시간으로 다중 모드 정보를 처리하고 주요 정보를 기억에 저장하며, 사용자 질문에 따라 추론을 촉발합니다. 다중 모드 장기 기억 모듈은 단기 기억을 장기 기억으로 효율적으로 압축하여 검색 효율성과 정확성을 높입니다. 추론 모듈은 질문에 응답하고 추론 작업을 실행하며, 지각 및 기억 모듈과 협력합니다. IXC2.5-OL은 오픈소스로 공개되어 다른 연구자들의 연구에 기여할 수 있습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 실시간 스트리밍 비디오 및 오디오 입력에 대한 실시간 상호작용을 가능하게 하는 새로운 시스템을 제시합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 단기 기억을 장기 기억으로 효율적으로 압축하여 장기 상호작용에 대한 시스템의 용량과 효율성을 개선합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 인간의 인지와 유사하게 지각, 추론, 기억 메커니즘을 분리하여 동시 처리를 가능하게 하여 지속적이고 적응력 있는 서비스를 제공합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **장기간에 걸친 스트리밍 비디오 및 오디오 상호작용을 위한 포괄적인 다중 모드 시스템**을 제시함으로써 AI 연구자들에게 중요한 의미를 가집니다. **실시간 지각, 기억, 추론 메커니즘을 분리**하여 인간의 인지 능력을 모방하고, **지속적인 적응형 서비스**를 제공하는 시스템 설계는 AI 분야의 새로운 가능성을 열어줍니다. 또한, **오픈소스로 공개된 코드 및 모델**은 다른 연구자들이 이를 기반으로 더욱 발전된 연구를 수행하는 데 크게 기여할 것입니다. 특히, **장기간 상호작용에 대한 한계를 극복**하려는 시도는,  **지속적이고 적응력 있는 AI 시스템** 개발에 대한 중요한 발전 방향을 제시합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.09596/x1.png)

> 🔼 그림 1은 사람의 인지 능력과 전문화된 일반화 AI에서 영감을 얻어 개발된 InternLM-XComposer2.5-OmniLive (IXC2.5-OL) 시스템을 보여줍니다. 이 시스템은 실시간 상호 작용을 가능하게 하는 세 가지 주요 모듈로 구성됩니다. 첫째, 스트리밍 비디오 및 오디오 입력을 지원하는 스트리밍 인식 모듈입니다. 둘째, 단기 메모리를 장기 메모리로 압축하는 다중 모드 장기 메모리 모듈입니다.  셋째, 검색된 메모리를 기반으로 질문에 답하는 추론 모듈입니다.  각 모듈은 시스템의 연속적이고 적응적인 서비스 제공에 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Inspired by human-like cognition and Specialized Generalist AI, we introduce InternLM-XComposer2.5-OmniLive (IXC2.5-OL), a system that facilitates real-time interaction with: (1) a streaming perception module supports streaming video and audio inputs; (2) a multi-modal long memory module that compresses short-term memory into long-term memory; and (3) a reasoning module that answers queries based on retrieved memories.
> </details>





{{< table-caption >}}
| Stage | Task | Dataset | Data Num |
|---|---|---|---| 
| Pretrain | ASR | GigaSpeech [11] | 8,282,987 |
| SFT | ASR | WenetSpeech [140] | 17,821,017 |
|  |  | LibriSpeech [87] | 281,241 |
|  |  | VCTK [111] | 44,070 |
|  |  | AISHELL-1 [8] | 120,098 |
|  |  | AISHELL-4 [39] | 102,254 |
|  |  | MD-RAMC [129] | 219,325 |
|  |  | ASCEND [76] | 12,314 |
|  |  | KeSpeech [106] | 888,428 |
|  |  | DASR [27] | 190,732 |
|  |  | CommonVoice [2] | 2,813,852 |
|  | CLS | FSD50K [35] | 40,966 |
|  |  | AudioSet [53] | 18,683 |
|  |  | Silence | 475 |{{< /table-caption >}}

> 🔼 표 1은 논문의 오디오 번역 모듈에 대한 사전 훈련 및 지도 학습 미세 조정에 사용된 데이터셋에 대한 개요를 보여줍니다. 사전 훈련 단계는 GigaSpeech 및 WenetSpeech 데이터셋을 사용하여 자동 음성 인식(ASR) 작업에만 중점을 둡니다. 지도 학습 미세 조정 단계는 다양한 데이터셋을 활용하여 ASR 및 오디오 분류(CLS) 작업을 모두 포함합니다. Common Voice의 경우 영어 및 중국어 분할만 사용하며, CLS 작업에는 475개의 자체 제작된 '침묵' 샘플이 추가적으로 사용됩니다.  본 표는 데이터셋의 이름, 작업 종류, 데이터셋 크기 등의 정보를 제공하여 오디오 번역 모듈의 성능 향상에 기여한 다양한 데이터셋의 역할을 명확히 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Overview of datasets used in pretraining and supervised fine-tuning (SFT) for the Audio Translation Module. The pretraining stage focuses solely on the automatic speech recognition (ASR) task, utilizing the GigaSpeech and WenetSpeech datasets. The SFT stage includes both ASR and audio classification (CLS) tasks, leveraging diverse datasets. For CommonVoice, we only use the English and Chinese splits. Additionally, 475 self-constructed “Silence” samples are used for CLS tasks.
> </details>





### In-depth insights


#### Multimodal Streaming
본 논문은 **멀티모달 스트리밍**에 대한 심도있는 논의를 제공합니다. **실시간 비디오 및 오디오 데이터 처리**와 관련된 어려움을 강조하며, 기존의 시퀀스-투-시퀀스 아키텍처 기반 모델의 한계를 극복하기 위해 **분리된 스트리밍 인식, 추론 및 메모리 메커니즘**을 제안합니다. 이를 통해 지속적이고 적응적인 서비스 제공을 가능하게 하며, 장기간의 상호 작용에서도 효율성을 유지할 수 있습니다.  **단기 및 장기 메모리 통합**은 효과적인 정보 검색과 정확도 향상에 중요한 역할을 하며, **인간의 인지 능력 모방**을 시도하는 핵심 전략입니다.  특히, **비디오와 오디오 데이터의 동시 처리**를 위한 전략이 중요하게 다뤄지며, 이는 단순히 데이터를 처리하는 수준을 넘어서 **실시간으로 상황을 이해하고 반응하는 지능형 시스템** 구축으로 이어집니다.  **다양한 벤치마크 결과**는 제안된 시스템의 성능을 입증하며, 실제 서비스 적용 가능성을 높입니다.

#### Long-Term Memory
본 논문에서 제시된 장기 기억 메커니즘은 **단순히 과거 정보를 무한정 저장하는 것이 아니라, 효율적인 정보 압축 및 검색**에 초점을 맞추고 있습니다.  이는 인간의 뇌가 단기 기억을 장기 기억으로 압축하여 저장하는 방식에서 영감을 얻은 것으로, **제한된 용량 내에서 장기간에 걸친 상호작용을 가능하게** 합니다.  **단기 기억은 중요한 세부 정보만을 추출하여 압축**하고, 이를 장기 기억으로 통합하는 과정을 통해 **효율적인 메모리 관리**를 수행합니다.  **다양한 모달리티의 정보를 통합**하여 저장함으로써, 텍스트, 이미지, 오디오 등 다양한 정보들을 종합적으로 고려한 추론이 가능해집니다. 이러한 접근 방식은 기존의 긴 컨텍스트 창에 모든 정보를 저장하는 방식의 비효율성을 극복하고, **실시간 상호 작용이 필요한 시스템에 적합**합니다.  본 논문의 장기 기억 메커니즘은  **인간의 인지 과정을 모방**하여 **지속적이고 적응적인 AI 서비스 제공**에 기여하는 핵심 요소입니다.

#### Specialized Generalist
본 논문에서 제시된 "전문가 일반화" 개념은 **단일 거대 모델이 모든 작업을 수행하는 대신, 특정 기능에 특화된 여러 개의 모델을 통합하여 상호 작용하는 시스템**을 의미합니다.  이는 인간의 두뇌가 특정 영역(시각, 청각, 기억, 추론)을 담당하는 전문화된 영역으로 나뉘어 있으면서도, 이들 영역이 통합적으로 작용하여 복잡한 문제를 해결하는 방식에서 영감을 받았습니다.  **스트리밍 비디오 및 오디오 처리에 있어,  각 모듈(지각, 기억, 추론)의 전문화는 실시간 상호 작용의 효율성과 정확성을 높입니다.**  예를 들어, 실시간 지각 모듈은 영상과 음성 데이터를 동시에 처리하여 주요 정보만을 추출하고, 장기 기억 모듈은 단기 기억을 효율적으로 압축하여 장기 기억으로 전환합니다.  결과적으로, **전문화된 모듈 간의 효율적인 정보 교류를 통해 지속적이고 적응적인 서비스가 가능**해지며, **인간의 인지 능력에 가까운 AI 시스템 구현**에 한걸음 더 다가갈 수 있습니다.  이는 **단순한 거대 모델의 확장이 아닌, 시스템 설계 및 기능 분할을 통한 근본적인 접근 방식**의 변화를 의미하며, 앞으로의 AI 시스템 개발 방향에 중요한 시사점을 제공합니다.

#### Benchmark Results
본 논문의 벤치마크 결과는 **다양한 멀티모달 벤치마크에서 SOTA 성능을 달성**했다는 점을 보여줍니다. 특히, 오디오 인식과 비디오 이해 작업 모두에서 경쟁력 있는 결과를 제시하며, 특히 **제한된 매개변수 규모에도 불구하고 최첨단 성능**을 달성한 점이 인상적입니다.  이는 제안된 모델의 효율성과 강력한 성능을 시사합니다.  **스트리밍 벤치마크에서도 상당한 경쟁력**을 보여주어 실시간 상호작용에 대한 적합성을 입증합니다.  그러나, **비교 대상 모델의 종류 및 버전에 대한 명확한 정보**가 부족하여 결과 해석에 주의가 필요하며, **추가적인 벤치마크 및 분석**을 통해 모델의 일반화 능력과 한계를 보다 면밀하게 파악하는 것이 중요합니다.  결과적으로, 제시된 벤치마크 결과는 고무적이지만, 보다 폭넓은 평가와 심층적인 분석이 필요합니다.

#### Future Directions
본 논문에서 제시된 InternLM-XComposer2.5-OmniLive (IXC2.5-OL) 시스템은 장기간에 걸친 스트리밍 비디오 및 오디오 상호작용을 위한 획기적인 시도이나, **여전히 개선의 여지가 많은 분야가 존재**합니다.  **미래 연구 방향**으로는 첫째, **모듈 간의 더욱 효율적인 통합**을 고려해야 합니다.  현재 시스템은 모듈들이 비동기적으로 작동하는데, 이는 처리 속도 및 효율성 측면에서 개선될 필요가 있습니다.  둘째, **모델의 확장성 및 일반화 능력** 향상에 주력해야 합니다.  현재 모델은 특정 데이터셋에 대해 훈련되었으므로, 다양한 환경 및 데이터에 대한 적응력을 높이는 연구가 필요합니다.  셋째, **실시간 처리 성능**을 더욱 향상시켜야 합니다.  실제 응용 분야에서는 매우 빠른 응답 속도가 요구되므로, 연산 효율성을 높이는 알고리즘 및 하드웨어 가속화 기술 개발이 필수적입니다.  넷째, **다양한 언어 및 문화적 배경**에 대한 지원을 확대해야 합니다.  전 세계적으로 다양한 언어와 문화를 포괄하는 대규모 멀티모달 데이터셋을 구축하고, 이를 기반으로 모델을 훈련하는 것이 중요합니다.  마지막으로, **윤리적 및 사회적 책임**을 고려한 연구가 중요합니다.  AI 시스템의 편향성, 프라이버시, 안전성 등에 대한 철저한 검토 및 대비책 마련이 필요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.09596/x2.png)

> 🔼 그림 2는 InternLM-XComposer2.5-OmniLive (IXC2.5-OL) 시스템의 파이프라인을 보여줍니다. IXC2.5-OL은 실시간 상호작용 시스템으로, 동시에 작동하는 세 가지 모듈로 구성됩니다. 1) 스트리밍 인식 모듈: 실시간으로 시청각 정보를 처리하고 주요 세부 정보를 메모리에 저장하며 사용자 쿼리에 따라 추론을 활성화합니다. 2) 다중 모드 장기 메모리 모듈: 단기 및 장기 메모리를 통합하여 효율적인 검색과 정확도 향상을 위해 단기 메모리를 장기 메모리로 압축합니다. 3) 추론 모듈: 쿼리에 응답하고 추론 작업을 실행하며 인식 및 메모리 모듈과 조정합니다. 이 그림은 사용자의 질문에 대한 시스템의 응답을 생성하는 전체 과정을 보여줍니다. 사용자의 질문은 먼저 음성 인식을 통해 텍스트로 변환되고, 이후 스트리밍 인식 모듈과 다중 모드 장기 메모리 모듈을 통해 처리되어 추론 모듈에 전달됩니다. 추론 모듈은 관련 정보를 처리하고, 최종적으로 텍스트 응답을 생성합니다. 이 텍스트 응답은 TTS (텍스트 음성 변환) 모듈을 통해 음성으로 변환되어 사용자에게 전달됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Pipeline of the InternLM-XComposer2.5-OmniLive. (IXC2.5-OL). The IXC2.5-OL is a real-time interacting system that is constructed by three simultaneous modules: 1) the Streaming Perception Module, 2) the Multi-modal Long Memory Module, and 3) the Reasoning Module.
> </details>



![](https://arxiv.org/html/2412.09596/x3.png)

> 🔼 그림 3은 IXC2.5-OL 시스템의 파이프라인을 보여줍니다. 시스템은 프런트엔드, SRS 서버, 백엔드 서버의 세 부분으로 구성됩니다. 프런트엔드는 비디오 및 오디오 스트림을 캡처하고 백엔드 서버에서 오디오를 재생하는 역할을 합니다. SRS 서버는 라이브 스트림 관리를 담당하며, 백엔드 서버는 오디오와 비디오를 읽고, 메모리를 추출하고, 질문에 답하는 역할을 합니다. 그림에서 녹색 상자는 스레드 또는 프로세스를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: System pipeline of the IXC2.5-OL. The system comprises the Frontend, SRS Server, and Backend Server. The Frontend is utilized for capturing video and audio streams and for playing audio from the Backend Server. The SRS Server is employed for managing live streams. The Backend Server is responsible for reading audio and video, extracting memory, and answering questions. The green boxes in the figure represent a thread or a process.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | Dataset |
|---|---| 
| Memory Module | ShareGPT4Video [15], Ego4D [41], ActivityNet [32], Semantics Implicit QA, Reference Implicit QA |
| IXC2.5 | ShareGPT4Video [15], ActivityNet [32], FunQA [122], TrafficQA [125], VideoChat2-IT [61], LLaVA-Video [152] |{{< /table-caption >}}
> 🔼 표 2는 논문의 IXC2.5-OL 시스템에서 사용된 비디오 데이터셋 목록을 보여줍니다.  각 데이터셋은 다양한 종류의 비디오와 질의응답 쌍(question-answer pairs)을 포함하며, 시스템의 다양한 모듈(Streaming Perception Module, Multi-modal Long Memory Module, Reasoning Module) 학습에 사용되었습니다.  특히, 'Semantics Implicit Question' 및 'Reference Implicit Question'과 같이 간접적인 질문을 포함하는 데이터셋도 포함되어 시스템의 견고성 및 일반화 능력을 향상시키는 데 기여했습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Video Datasets used in IXC2.5-OL.
> </details>

{{< table-caption >}}
| Method |  | LLM |  | Wenetspeech (CN) |  | Librispeech (ENG) |
|---|---|---|---|---|---|---|
|  |  |  |  | Test_Net ↓ | Test_Meeting ↓ |  | Dev_clean ↓ | Dev_other ↓ | Test_clean ↓ | Test_other ↓ |
|---|---|---|---|---|---|---|---|---|---|---|
| Qwen2-Audio [26] |  | Qwen2-7B [128] |  | 7.8 | 8.4 |  | 1.3 | 3.4 | 1.6 | 3.6 |
| Mini-Omni [123] |  | Qwen2-0.5B [128] |  | - | - |  | 4.5 | 9.7 | 4.6 | 9.2 |
| VITA [38] |  | Mixtral-8x7B [47] |  | 12.2 | 16.5 |  | 7.6 | 16.6 | 8.1 | 18.4 |
| IXC2.5-OL |  | Qwen2-1.5B [128] |  | 9.0 | 9.2 |  | 2.5 | 5.7 | 2.6 | 5.8 |{{< /table-caption >}}
> 🔼 표 3은 자동 음성 인식(ASR) 작업에 대한 평가 결과를 보여줍니다. 'CN'은 중국어 음성을, 'ENG'는 영어 음성을 나타냅니다. 성능은 WER(단어 오류율)을 사용하여 측정됩니다. 이 표는 다양한 모델(Qwen2-Audio, Qwen2-7B, Mini-Omni, VITA, IXC2.5-OL)의 중국어 및 영어 음성 인식 성능을 WER 수치를 통해 비교 분석하여 각 모델의 정확도를 보여줍니다.  WER 값이 낮을수록 더 높은 정확도를 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Evaluation results on ASR tasks: ”CN” refers to Chinese speech, while ”ENG” refers to English speech. The performance is measured using WER ↓↓\downarrow↓ (Word Error Rate).
> </details>

{{< table-caption >}}
| Method | Params | Topic Rea. | Anomaly Recog. | Needle QA | Ego Rea. | Plot QA | Action Or. | Action Co. | M-Avg |
|---|---|---|---|---|---|---|---|---|---| 
| <br> *Closed-source APIs*. <br> |  |  |  |  |  |  |  |  |  |
| Claude-3-Opus | - | 67.2 | 43.5 | 21.6 | 40.2 | 47.8 | 18.2 | 16.7 | 36.5 |
| Qwen-VL-Max | - | 67.4 | 63.5 | 40.3 | 40.9 | 43.3 | 25.0 | 14.8 | 42.2 |
| GPT-4 Turbo | - | 79.5 | 68.0 | 45.9 | 47.4 | 60.6 | 26.5 | 16.1 | 49.2 |
| GPT-4o | - | 87.4 | 74.5 | 64.8 | 57.1 | 65.1 | 56.7 | 46.3 | 64.6 |
| <br> *Open-source models*. <br> |  |  |  |  |  |  |  |  |  |
| MovieChat [99] | 7B | 29.5 | 25.0 | 24.2 | 24.7 | 25.8 | 28.6 | 22.8 | 25.8 |
| LLaMA-VID [65] | 7B | 50.8 | 34.5 | 30.1 | 32.7 | 32.5 | 23.9 | 27.8 | 33.2 |
| LLaVA-1.6 [71] | 7B | 60.6 | 41.0 | 43.1 | 38.4 | 41.0 | 25.5 | 25.7 | 39.3 |
| ShareGPT4Video [15] | 7B | 75.8 | 51.5 | 47.6 | 43.2 | 48.4 | 34.0 | 23.3 | 46.4 |
| VideoLlaMA2 [23] | 7B | 74.6 | 64.5 | 49.9 | 43.8 | 45.1 | 34.0 | 27.4 | 48.5 |
| LongVA [149] | 7B | 83.3 | 58.5 | 69.3 | 50.0 | 67.2 | 38.6 | 27.2 | 56.3 |
| IXC2.5 [148] | 7B | - | - | - | - | - | - | - | 58.8 |
| InternVL2 [22] | 8B | - | - | - | - | - | - | - | 64.0 |
| LLaVA-OneVision [57] | 7B | - | - | - | - | - | - | - | 64.7 |
| Video-XL [97] | 7B | - | - | - | - | - | - | - | 64.9 |
| IXC2.5-OL | 7B | 84.1 | 68.5 | 76.6 | 60.8 | 75.1 | 57.1 | 41.3 | 66.2 |{{< /table-caption >}}
> 🔼 표 4는 MLVU 벤치마크에 대한 평가 결과를 보여줍니다. IXC2.5-OL 모델은 70억 개의 매개변수를 가진 모델 중에서 최고 성능(SOTA)을 달성했으며, 오픈소스 모델과 상용 API를 모두 능가하는 우수한 성능을 보여주었습니다.  다양한 비디오 이해 작업(주제 추론, 이상 감지, 질문 응답 등)에 대한 성능을 정량적으로 비교 분석하여 IXC2.5-OL의 우수성을 입증합니다.  표에는 각 작업에 대한 정확도와 전체 평균 성능이 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Evaluation results on MLVU benchmark. IXC2.5-OL has demonstrated excellent performance, surpassing both open-source models and closed-source APIs, achieving SOTA at the 7B model scale.
> </details>

{{< table-caption >}}
| Method | Params | Short | Medium | Long | Overall |
|---|---|---|---|---|---| 
| <em class="ltx_emph ltx_font_italic">Closed-source APIs.</em> |  |  |  |  |  |
| GPT-4V | - | 70.5 | 55.8 | 53.5 | 59.9 |
| Claude 3.5 Sonnet | - | 71.0 | 57.4 | 51.2 | 60.0 |
| GPT-4o mini | - | 72.5 | 63.1 | 58.6 | 64.8 |
| GPT-4o | - | 80.0 | 70.3 | 65.3 | 71.9 |
| Gemini 1.5 Pro | - | 81.7 | 74.3 | 67.4 | 75.0 |
| <em class="ltx_emph ltx_font_italic">Open-source models.</em> |  |  |  |  |  |
| ShareGPT4Video [15] | 7B | 48.3 | 36.3 | 35.0 | 39.9 |
| VideoLlaMA2 [23] | 7B | - | - | - | 47.9 |
| LongVA [149] | 7B | 61.1 | 50.4 | 46.2 | 52.6 |
| Video-XL [97] | 7B | 64.0 | 53.2 | 49.2 | 55.5 |
| VITA [38] | 8x7B | 65.9 | 52.9 | 48.6 | 55.8 |
| IXC2.5 [148] | 7B | - | - | - | 55.8 |
| InternVL2 [22] | 8B | - | - | - | 56.3 |
| LLaVA-OneVision [57] | 7B | - | - | - | 58.2 |
| mPLUG-Owl3 [131] | 7B | 70.0 | 57.7 | 50.1 | 59.3 |
| MiniCPM-V 2.6 [130] | 8B | - | - | - | 60.9 |
| IXC2.5-OL | 7B | 72.7 | 58.2 | 50.8 | 60.6 |{{< /table-caption >}}
> 🔼 표 5는 Video-MME 벤치마크에 대한 평가 결과를 보여줍니다.  Video-MME는 다양한 비디오 이해 작업을 평가하기 위해 고안된 종합적인 벤치마크입니다. 이 표는 IXC2.5-OL 모델의 성능을 오픈소스 최첨단(SOTA) 모델들과 비교하여 보여주며, IXC2.5-OL이 오픈소스 SOTA 모델들과 거의 비슷한 성능을 보임을 나타냅니다.  구체적으로는 여러 비디오 이해 과제에 대한 정확도(예: 주제 추론, 이상 감지, 질문 응답 등)를 수치로 제시하여 모델의 성능을 자세히 비교 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Evaluation results on Video-MME benchmark. IXC2.5-OL demonstrates performance close to that of the open-source SOTA.
> </details>

{{< table-caption >}}
| Method | Params | OP | CR | CS | ATP | EU | TR | PR | SU | ACP | CT | Overall |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Human | - | 89.47 | 92.00 | 93.60 | 91.47 | 95.65 | 92.52 | 88.00 | 88.75 | 89.74 | 91.30 | 91.46 |
| _Closed-source APIs._ |  |  |  |  |  |  |  |  |  |  |  |  |
| Claude 3.5 Sonnet | - | 80.49 | 77.34 | 82.02 | 81.73 | 72.33 | 75.39 | 61.11 | 61.79 | 69.32 | 43.09 | 72.44 |
| GPT-4o | - | 77.11 | 80.47 | 83.91 | 76.47 | 70.19 | 83.80 | 66.67 | 62.19 | 69.12 | 49.22 | 73.28 |
| Gemini 1.5 Pro | - | 79.02 | 80.47 | 83.54 | 79.67 | 80.00 | 84.74 | 77.78 | 64.23 | 71.95 | 48.70 | 75.69 |
| _Open-source models._ |  |  |  |  |  |  |  |  |  |  |  |  |
| VideoLLM-online [12] | 8B | 39.07 | 40.06 | 34.49 | 31.05 | 45.96 | 32.40 | 31.48 | 34.16 | 42.49 | 27.89 | 35.99 |
| VideoLLaMA2 [23] | 7B | 55.86 | 55.47 | 57.41 | 58.17 | 52.80 | 43.61 | 39.21 | 42.68 | 45.61 | 35.23 | 49.52 |
| VILA-1.5 [68] | 8B | 53.68 | 49.22 | 70.98 | 56.86 | 53.42 | 53.89 | 54.63 | 48.78 | 50.14 | 17.62 | 52.32 |
| LongVA [149] | 7B | 70.03 | 63.28 | 61.20 | 70.92 | 62.73 | 59.50 | 61.11 | 53.66 | 54.67 | 34.72 | 59.96 |
| InternVL2 [22] | 8B | 68.12 | 60.94 | 69.40 | 77.12 | 67.70 | 62.93 | 59.26 | 53.25 | 54.96 | 56.48 | 63.72 |
| Kangaroo [72] | 7B | 71.12 | 84.38 | 70.66 | 73.20 | 67.08 | 61.68 | 56.48 | 55.69 | 62.04 | 38.86 | 64.60 |
| MiniCPM-V 2.6 [130] | 8B | 71.93 | 71.09 | 77.92 | 75.82 | 64.60 | 65.73 | 70.37 | 56.10 | 62.32 | 53.37 | 67.44 |
| Qwen2-VL [113] | 7B | 75.20 | 82.81 | 73.19 | 77.45 | 68.32 | 71.03 | 72.22 | 61.19 | 69.04 | 46.11 | 69.04 |
| LLaVA-OneVision [57] | 7B | 80.38 | 74.22 | 76.03 | 80.72 | 72.67 | 71.65 | 67.59 | 65.45 | 65.72 | 45.08 | 71.12 |
| IXC2.5-OL | 7B | 82.83 | 73.77 | 78.66 | 82.95 | 72.50 | 76.01 | 61.11 | 60.67 | 71.59 | 58.85 | 73.79 |{{< /table-caption >}}
> 🔼 표 6은 실시간 시각적 이해를 위한 StreamingBench에 대한 평가 결과를 보여줍니다. 측정 지표는 객체 인식(OP), 인과 추론(CR), 클립 요약(CS), 속성 인식(ATP), 사건 이해(EU), 풍부한 텍스트 이해(TR), 전망적 추론(PR), 공간적 이해(SU), 동작 인식(ACP), 계산(CT)을 포함합니다. IXC2.5-OL은 모든 오픈소스 모델 중에서 가장 뛰어난 성능을 보이며, 클로즈드 소스 API인 Gemini 1.5 Pro에 근접한 성능을 보입니다.  표는 다양한 모델들의 실시간 시각적 이해 능력을 비교 분석하여 각 모델의 강점과 약점을 파악하는 데 도움을 줍니다. 특히,  객체 인식, 사건 이해, 동작 인식과 같은 다양한 시각적 이해 과제에서 각 모델의 성능 차이를 명확하게 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Evaluation results on StreamingBench for Real-Time Visual Understanding. Metrics include Object Perception (OP), Causal Reasoning (CR), Clips Summarization (CS), Attribute Perception (ATP), Event Understanding (EU), Text-Rich Understanding (TR), Prospective Reasoning (PR), Spatial Understanding (SU), Action Perception (ACP), and Counting (CT). IXC2.5-OL excels among all open-source models, and falling just short of the closed-source API, Gemini 1.5 Pro.
> </details>

{{< table-caption >}}
| Method | Params | CP | FP-S | FP-C | HL | Mean | LR | AR | RR | CSR | TP | Mean | Overall |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| *Closed-source APIs*. |  |  |  |  |  |  |  |  |  |  |  |  |  |
| Claude 3.5 Sonnet | - | 1.57 | 1.39 | 1.07 | 1.40 | 1.38 | 1.13 | 1.70 | 1.48 | 1.54 | 1.04 | 1.35 | 1.38 |
| Gemini 1.0 Pro | - | 1.61 | 1.56 | 1.30 | 0.65 | 1.50 | 1.15 | 1.57 | 1.55 | 1.36 | 1.33 | 1.39 | 1.48 |
| Gemini 1.5 Pro | - | 1.99 | 2.04 | 1.70 | 1.90 | 1.98 | 1.98 | 2.02 | 1.92 | 1.78 | 1.63 | 1.86 | 1.94 |
| GPT-4V | - | 1.83 | 1.65 | 1.40 | 1.76 | 1.66 | 1.45 | 1.91 | 1.86 | 1.83 | 1.53 | 1.69 | 1.68 |
| GPT-4o | - | 2.23 | 2.24 | 2.01 | 1.90 | 2.19 | 2.11 | 2.12 | 2.17 | 1.94 | 1.97 | 2.08 | 2.15 |
| *Open-source models*. |  |  |  |  |  |  |  |  |  |  |  |  |  |
| MovieLLM [101] | 7B | 0.95 | 0.82 | 0.70 | 0.15 | 0.81 | 0.52 | 1.12 | 1.22 | 0.54 | 1.05 | 0.97 | 0.87 |
| LLaVA-OneVision [57] | 72B | 1.22 | 1.07 | 0.90 | 0.21 | 1.03 | 0.76 | 0.96 | 0.55 | 0.81 | 0.48 | 0.70 | 0.94 |
| PLLaVA [126] | 7B | 1.08 | 1.06 | 0.86 | 0.52 | 1.02 | 0.64 | 1.25 | 1.17 | 0.98 | 1.01 | 1.03 | 1.03 |
| ShareGPT4Video [15] | 7B | 1.20 | 1.05 | 1.00 | 0.32 | 1.04 | 0.89 | 1.06 | 1.19 | 1.01 | 0.99 | 1.03 | 1.05 |
| VideoStreaming [89] | 7B | 1.38 | 1.13 | 0.8 | 0.32 | 1.13 | 0.77 | 1.27 | 1.11 | 1.01 | 1.10 | 1.09 | 1.12 |
| LLaVA-NeXT-Video [151] | 7B | 1.35 | 1.15 | 0.97 | 0.58 | 1.14 | 0.64 | 1.38 | 1.30 | 1.27 | 1.03 | 1.13 | 1.14 |
| VILA1.5 [68] | 13B | 1.51 | 1.45 | 1.26 | 0.24 | 1.39 | 0.80 | 1.52 | 1.30 | 1.40 | 1.28 | 1.28 | 1.36 |
| InternVL2 [22] | 8B | 1.41 | 1.37 | 1.15 | 0.19 | 1.30 | 0.90 | 1.34 | 1.38 | 1.14 | 1.00 | 1.16 | 1.26 |
| Qwen2-VL [113] | 7B | 1.63 | 1.51 | 1.19 | 0.55 | 1.46 | 1.16 | 1.56 | 1.49 | 1.37 | 1.21 | 1.35 | 1.44 |
| IXC2.5-OL | 7B | 1.53 | 1.61 | 1.20 | 0.15 | 1.49 | 0.93 | 1.44 | 1.57 | 1.30 | 1.08 | 1.25 | 1.42 |{{< /table-caption >}}
> 🔼 표 7은 MMBench-Video 벤치마크에 대한 평가 결과를 보여줍니다. MMBench-Video는 비디오 이해를 위한 다양한 과제를 포함하는 벤치마크입니다. 이 표에는 총 9가지 과제에 대한 성능이 제시되어 있습니다.  각 과제는 비디오 이해의 특정 측면을 평가합니다. 예를 들어, Coarse Perception(CP)은 비디오의 전반적인 내용 이해를 측정하고, Single-Instance Finegrained Perception(FP-S)과 Cross-Instance Finegrained Perception(FP-C)는 세부적인 객체 인식 능력을 평가합니다. Hallucination(HL)은 잘못된 정보를 생성하는 경향을 평가하고, Logic Reasoning(LR), Attribute Reasoning(AR), Relation Reasoning(RR), Commonsense Reasoning(CSR), Temporal Reasoning(TP)은 각각 논리적 추론, 속성 추론, 관계 추론, 상식적 추론, 시간적 추론 능력을 측정합니다.  표에는 다양한 모델의 성능이 제시되어 있으며, 모델의 파라미터 수와 각 과제에 대한 성능 점수가 포함되어 있습니다. 이를 통해 여러 모델의 비디오 이해 능력을 비교 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Evaluation results on MMBench-Video. Tasks include Coarse Perception (CP), Single-Instance Finegrained Perception (FP-S), Cross-Instance Finegrained Perception (FP-C), Hallucination (HL), Logic Reasoning (LR), Attribute Reasoning (AR), Relation Reasoning (RR), Commonsense Reasoning (CSR), and Temporal Reasoning (TP).
> </details>

{{< table-caption >}}
| Method | Params | AS | AP | AA | FA | UA | OE | OI | OS | MD | AL | ST | AC | MC | MA | SC | FP | CO | EN | ER | CI | Avg |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| GPT-4V | - | 55.5 | 63.5 | 72.0 | 46.5 | 73.5 | 18.5 | 59.0 | 29.5 | 12.0 | 40.5 | 83.5 | 39.0 | 12.0 | 22.5 | 45.0 | 47.5 | 52.0 | 31.0 | 59.0 | 11.0 | 43.5 |
| GPT-4o | - | 61.5 | 56.5 | 72.0 | 54.0 | 82.0 | 62.5 | 66.5 | 44.0 | 36.5 | 33.5 | 93.0 | 54.5 | 33.5 | 54.5 | 53.5 | 74.5 | 71.5 | 32.5 | 71.0 | 42.5 | 57.5 |
| _Closed-source APIs._ |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| VideoLLaMA [144] | 7B | 27.5 | 25.5 | 51.0 | 29.0 | 39.0 | 48.0 | 40.5 | 38.0 | 22.5 | 22.5 | 43.0 | 34.0 | 22.5 | 32.5 | 45.5 | 32.5 | 40.0 | 30.0 | 21.0 | 37.0 | 34.1 |
| VideoChat [60] | 7B | 33.5 | 26.5 | 56.0 | 33.5 | 40.5 | 53.0 | 40.5 | 30.0 | 25.5 | 27.0 | 48.5 | 35.0 | 20.5 | 42.5 | 46.0 | 26.5 | 41.0 | 23.5 | 23.5 | 36.0 | 35.5 |
| MiniCPM-V 2.6 [130] | 7B | 38.0 | 43.0 | 63.0 | 35.5 | 67.5 | 55.5 | 46.0 | 35.5 | 25.5 | 33.0 | 77.5 | 48.0 | 37.0 | 54.0 | 42.5 | 40.0 | 31.0 | 38.0 | 43.0 | 40.5 | 44.7 |
| VideoChat2 [62] | 7B | 66.0 | 47.5 | 83.5 | 49.5 | 60.0 | 58.0 | 71.5 | 42.5 | 23.0 | 23.0 | 88.5 | 39.0 | 42.0 | 58.5 | 44.0 | 49.0 | 36.5 | 35.0 | 40.5 | 65.5 | 51.1 |
| Qwen2-VL [113] | 7B | 51.0 | 58.0 | 77.5 | 47.0 | 64.0 | 63.0 | 65.5 | 40.0 | 25.5 | 35.5 | 77.0 | 43.5 | 47.0 | 62.0 | 42.0 | 61.5 | 49.5 | 41.5 | 47.5 | 41.5 | 52.0 |
| PLLaVA [126] | 34B | 65.0 | 53.0 | 83.5 | 45.0 | 77.5 | 70.0 | 64.5 | 38.5 | 37.5 | 49.0 | 89.5 | 41.5 | 43.5 | 70.0 | 53.0 | 52.5 | 65.0 | 39.5 | 60.5 | 58.0 | 57.8 |
| LLaVA-OneVision [57] | 72B | 63.0 | 58.0 | 84.5 | 46.5 | 85.5 | 64.0 | 73.5 | 41.5 | 37.0 | 69.0 | 95.0 | 47.5 | 47.5 | 75.5 | 53.5 | 52.0 | 70.5 | 34.0 | 64.0 | 54.5 | 60.8 |
| InternVL2 [22] | 8B | 75.0 | 62.0 | 83.5 | 40.5 | 69.5 | 96.0 | 72.0 | 29.5 | 58.0 | 53.0 | 88.5 | 39.5 | 83.0 | 97.0 | 51.0 | 78.5 | 65.0 | 33.0 | 48.0 | 67.0 | 64.5 |
| _Open-source models._ |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| IXC2.5-OL | 7B | 84.5 | 81.0 | 75.0 | 46.0 | 81.0 | 92.0 | 79.5 | 36.5 | 83.0 | 47.0 | 90.0 | 60.5 | 75.0 | 93.0 | 58.0 | 60.5 | 74.0 | 42.0 | 53.0 | 62.0 | 68.7 |{{< /table-caption >}}
> 🔼 표 8은 MVBench라는 비디오 벤치마크 데이터셋을 사용한 평가 결과를 보여줍니다. MVBench는 다양한 비디오 이해 작업을 평가하기 위해 설계되었으며,  액션 순서(AS), 액션 예측(AP), 액션 반의어(AA), 세분화된 액션(FA), 예상치 못한 액션(UA), 객체 존재(OE), 객체 상호작용(OI), 객체 섞기(OS), 이동 방향(MD), 액션 지역화(AL), 장면 전환(ST), 액션 개수(AC), 이동 개수(MC), 이동 속성(MA), 상태 변화(SC), 세분화된 포즈(FP), 캐릭터 순서(CO), 시점 탐색(EN), 에피소드 추론(ER), 반사실적 추론(CI) 등 20가지 작업에 대한 성능을 평가합니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Evaluatation results on MVBench. Tasks include Action Sequence (AS), Action Prediction (AP), Action Antonym (AA), Fine-grained Action (FA), Unexpected Action (UA), Object Existence (OE), Object Interaction (OI), Object Shuffle (OS), Moving Direction (MD), Action Localization (AL), Scene Transition (ST), Action Count (AC), Moving Count (MC), Moving Attribute (MA), State Change (SC), Fine-grained Pose (FP), Character Order (CO), Egocentric Navigation (EN), Episodic Reasoning (ER), and Counterfactual Inference (CI).
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
{{< /gallery >}}