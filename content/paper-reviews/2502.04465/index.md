---
title: "FocalCodec: Low-Bitrate Speech Coding via Focal Modulation Networks"
summary: "FocalCodec: 초저 비트율에서도 의미 및 음향 정보 손실 없이 고품질 음성 재생산 가능한 혁신적 음성 코덱"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Speech and Audio", "Speech Coding", "🏢 Concordia University",]
showSummary: true
date: 2025-02-06
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.04465 {{< /keyword >}}
{{< keyword icon="writer" >}} Luca Della Libera et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-12 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.04465" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.04465" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/focalcodec-low-bitrate-speech-coding-via" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

최근 대규모 언어 모델의 성공에 영감을 받아, 연구자들은 연속적인 오디오를 토큰으로 변환하는 신경망 오디오 코덱을 개발해 왔습니다. 하지만 기존의 접근 방식은 높은 비트율, 의미 또는 음향 정보의 손실, 그리고 두 가지 모두를 포착하기 위한 다중 코드북 설계의 복잡성 등의 한계를 가지고 있습니다.  본 논문은 이러한 문제점들을 해결하기 위해 FocalCodec을 제안합니다.

FocalCodec은 Focal Modulation 네트워크를 기반으로 하는 효율적인 저비트율 코덱으로, 단일 이진 코드북을 사용하여 음성을 압축합니다.  이는 0.16~0.65kbps의 초저 비트율에서도 경쟁력 있는 음성 재합성 및 음성 변환 성능을 제공하며, 다국어 음성과 잡음 환경에서도 효과적입니다.  하위 작업 평가 결과, FocalCodec은 의미와 음향 정보를 성공적으로 보존하며 생성 모델링에도 적합함을 보였습니다.  FocalCodec은 효율성과 성능 측면에서 우수한 성능을 보여주는 새로운 음성 코딩 기술입니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} FocalCodec은 **단일 이진 코드북**을 사용하여 0.16~0.65kbps의 초저 비트율로 음성을 압축합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} FocalCodec은 **다국어 음성 및 잡음 환경**에서도 우수한 성능을 보이며, **다운스트림 작업에서 의미 및 음향 정보**를 효과적으로 보존합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} FocalCodec은 **경쟁력 있는 재구성 품질**을 제공하며, **생성 모델링에 적합**합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **낮은 비트율에서도 고품질의 음성 재구성과 의미 정보 보존을 달성하는 새로운 음성 코덱인 FocalCodec**을 제시하여, 음성 처리 분야의 연구자들에게 중요한 의미를 지닙니다.  **다양한 하위 작업에서 경쟁력 있는 성능**을 보여줌으로써, **단일 코드북 기반의 효율적인 설계**에 대한 새로운 가능성을 제시하고, 후속 연구를 위한 새로운 방향을 제시합니다. 특히 **초저 비트율 음성 코딩**에 대한 관심이 증가하는 추세에 따라, 본 논문의 결과는 상당한 영향력을 가질 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.04465/x1.png)

> 🔼 그림 1은 FocalCodec의 아키텍처를 보여줍니다. 인코더는 음향 및 의미 정보를 모두 포함하는 특징을 추출합니다. 이러한 특징들은 압축기(compressor)에 의해 저차원 공간으로 매핑되고, 이진 양자화(binary quantization)를 거쳐 디압축기(decompressor)에 의해 다시 투영됩니다. 디코더는 이러한 특징들을 사용하여 파형을 재합성합니다. 즉, 인코더가 음성 신호의 음향적, 의미적 정보를 추출하고, 압축기가 이를 이진 코드로 효율적으로 압축하며, 디압축기가 이를 다시 원래의 특징으로 복원하고, 디코더가 이를 이용해 원래의 음성 신호를 재생성하는 과정을 보여주는 그림입니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: FocalCodec architecture. The encoder extracts features containing both acoustic and semantic information. These features are then mapped to a low-dimensional space by the compressor, binary quantized, and projected back by the decompressor. The decoder resynthesizes the waveform from these features.
> </details>





{{< table-caption >}}
| Codec | Bitrate (kbps) | Sample Rate (kHz) | Token Rate (Hz) | Codebooks | Code Size | Params (M) | MACs (G) |
|---|---|---|---|---|---|---|---| 
| EnCodec | 1.50 | 24 | 75.0 | 2 × 1024 | 128 | 15 | 2 |
| DAC | 1.00 | 16 | 50.0 | 2 × 1024 | 8 | 74 | 56 |
| WavLM6-KM | 0.45 | 16 | 50.0 | 1 × 512 | 1024 | 127 | 28 |
| SpeechTokenizer | 1.00 | 16 | 50.0 | 2 × 1024 | 1024 | 108 | 17 |
| SemantiCodec | 0.65 | 16 | 25.0 | 2 × 8192 | 1536 | 1033 | 1599 |
| Mimi | 0.69 | 24 | 12.5 | 5 × 2048 | 256 | 82 | 11 |
| WavTokenizer | 0.48 | 24 | 40.0 | 1 × 4096 | 512 | 85 | 3 |
| BigCodec | 1.04 | 16 | 80.0 | 1 × 8192 | 8 | 160 | 61 |
| Stable Codec | 0.70 | 16 | 25.0 | 2 × 15625 | 6 | 95 | 37 |
| **FocalCodec@50** | 0.65 | 16 | 50.0 | 1 × 8192 | 13 | 142 | 9 |
| **FocalCodec@25** | 0.33 | 16 | 25.0 | 1 × 8192 | 13 | 144 | 9 |
| **FocalCodec@12.5** | 0.16 | 16 | 12.5 | 1 × 8192 | 13 | 145 | 8 |{{< /table-caption >}}

> 🔼 표 1은 논문에서 비교한 저비트율 오디오 코덱들을 요약하여 보여줍니다.  각 코덱의 비트 전송률(kbps), 샘플링 레이트(kHz), 토큰 레이트(Hz), 사용된 코드북의 개수, 모델 크기(M), 연산량(G MACs) 등의 정보를 보여주어, 코덱들의 성능과 효율성을 비교하는 데 유용한 정보를 제공합니다.  FocalCodec의 세 가지 변형 모델(50Hz, 25Hz, 12.5Hz)의 사양과 비교 대상 코덱들의 사양을 한눈에 비교할 수 있도록 구성되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Compared codecs.
> </details>





### In-depth insights


#### Focal Modulation's Role
본 논문에서 제시된 FocalCodec은 **단일 이진 코드북**을 사용하여 음성을 압축하는 효율적인 저비트레이트 코덱입니다. 이는 기존의 다중 코드북 기반 코덱의 복잡성을 줄이고, 하위 작업에 대한 효과적인 표현을 위해 **음향 및 의미 정보 모두를 보존**하는 데 중점을 둡니다.  Focal Modulation 네트워크는 **단일 코드북 내에서도 다양한 세부 정보를 효과적으로 캡처**할 수 있도록 설계되어,  **저비트레이트에서도 높은 재구성 품질과 효율적인 하위 작업 성능**을 제공합니다.  Focal Modulation의 역할은 압축 과정에서 주요 특징들을 효율적으로 추출하고,  **세밀한 음향 정보와 의미 정보를 동시에 유지**하면서  **차원 축소**를 가능하게 하는 것입니다.  결과적으로 FocalCodec은 기존 코덱들보다 뛰어난 성능을 보이며,  **저비트레이트 음성 코딩 분야에 새로운 가능성**을 제시합니다.

#### Single Codebook Design
본 논문에서 다룬 단일 코드북 설계는 기존의 다중 코드북 기반 음성 코덱의 복잡성을 해결하기 위한 핵심적인 접근 방식입니다. **단일 코드북을 사용함으로써 모델의 구조적 복잡성을 줄이고 추론 속도를 높일 수 있다는 장점**이 있습니다.  이는 하류 작업을 위한 효율적인 토큰 표현을 생성하는 데 중요하며, 특히 제한된 자원 환경에서 유용합니다. 하지만, **단일 코드북 설계는 음성의 음향 및 의미 정보를 모두 효과적으로 포착해야 하는 과제**를 안고 있습니다.  이러한 과제를 해결하기 위해 본 논문에서는 focal modulation 기반의 효율적인 압축 및 양자화 기법을 제시합니다. **focal modulation은 단일 코드북 내에서도 세밀한 양자화를 가능하게 하여 음향 정보의 손실을 최소화**하는 데 기여합니다.  이는 저비트레이트 환경에서도 경쟁력 있는 성능을 달성하는 데 중요한 요소입니다.  **단일 코드북 설계의 성공 여부는 하류 작업에서의 성능에 직접적으로 영향**을 미치므로,  다양한 하류 작업(음성 재합성, 음성 변환, 음성 인식 등)에 대한 포괄적인 평가가 필수적입니다.  **본 논문의 연구는 단일 코드북 설계의 실용성과 효율성을 보여주는 중요한 사례**가 될 수 있습니다.

#### Low-Bitrate Speech
본 논문은 저비트레이트 음성 코덱에 대한 심층적인 고찰을 제공합니다. **FocalCodec**이라는 새로운 코덱을 제시하며, 기존의 고비트레이트, 의미 또는 음향 정보 손실, 다중 코드북 사용 등의 문제점을 해결합니다. **단일 이진 코드북**을 사용하여 0.16~0.65kbps의 낮은 비트레이트에서 경쟁력 있는 성능을 제공하며, 다국어 및 잡음 환경에서도 효과적입니다. **Focal Modulation 네트워크** 기반의 설계로 효율성을 높였고, 하향식 및 상향식 모델에서 모두 우수한 성능을 보였습니다.  **하향식 작업(예: 음성 인식)**에서 의미 및 음향 정보를 효과적으로 보존하고, **상향식 작업(예: 음성 생성)**에서도 적합하다는 것을 보여줍니다.  결론적으로, FocalCodec은 저비트레이트 음성 코딩 분야에 중요한 기여를 하며, 향후 연구 방향을 제시합니다.

#### Downstream Task
본 논문에서 다운스트림 작업은 **FocalCodec의 토큰 표현의 질을 평가**하기 위해 고안되었습니다.  **자동 음성 인식(ASR), 화자 인식(SI), 감정 인식(SER)**과 같은 다양한 작업에 대해 성능을 측정함으로써, FocalCodec이 의미 정보와 음향 정보 모두를 얼마나 잘 보존하는지 확인했습니다.  **단순한 BiLSTM 모델을 사용**하여,  모델 복잡성을 최소화하고 토큰 표현 자체의 우수성에 초점을 맞추었습니다.  **다운스트림 작업 결과는 FocalCodec이 ASR, SI 모두에서 경쟁력 있는 성능**을 보임을 보여주며, 특히 **SER 작업에서도 상당히 좋은 성능**을 나타냈습니다.  **단일 코드북 설계에도 불구하고 의미 정보와 음향 정보를 효과적으로 분리**하여 하위 작업에 유용한 표현을 제공하는 FocalCodec의 능력을 확인할 수 있습니다.  결과적으로, 다운스트림 작업 분석은 FocalCodec의 강점과 한계를 명확히 제시하며, 향후 연구 방향을 제시하는 중요한 부분입니다.

#### Future Work
본 논문의 "향후 연구 방향"에 대한 심도있는 고찰은 **인과관계(causality)** 문제 해결과 **데이터셋 확장**의 필요성에 초점을 맞춰야 합니다.  현재 비인과적 모델의 한계를 극복하고 실시간 응용에 적합한 인과적 모델 개발이 중요하며, 이를 위해서는 **새로운 아키텍처 설계** 및 **훈련 전략** 모색이 필수적입니다.  또한, 현재 영어 음성 데이터에 국한된 데이터셋을 다양한 언어, 잡음 환경, 음악 등의 다양한 오디오 유형으로 확장하여 모델의 **범용성 및 강건성**을 높여야 합니다.  **샘플링 레이트 향상** 역시 고려해야 할 중요한 요소이며, 이를 통해 더욱 높은 음질의 재생과 다양한 하위 작업에서의 성능 향상을 기대할 수 있습니다.  **다양한 하위 작업에 대한 모델 평가**를 통해 각 작업에 최적화된 모델 구성을 연구하는 것도 향후 연구의 중요한 부분입니다.


### More visual insights




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Codec | UTMOS ↑ | dWER ↓ | Sim ↑ | Code Usage ↑ | Norm Entropy ↑ | RTF ↑ | LibriSpeech test-clean | Multilingual LibriSpeech 700 |
|---|---|---|---|---|---|---|---|---|
| **Reference** | 4.09 | 0.00 | 100.0 | — | — | — | 4.09 | 0.00 |
| EnCodec | 1.58 | 8.08 | 93.8 | 93.4 | 82.1 | 109 | 1.33 | 29.60 |
| DAC | 1.29 | 20.04 | 89.2 | **100.0** | 91.7 | 89 | 1.24 | 56.08 |
| WavLM6-KM | 3.75 | 6.20 | 90.0 | 26.4 | 95.4 | 85 | 2.97 | 44.54 |
| SpeechTokenizer | 2.28 | 5.14 | 91.6 | 95.9 | 97.0 | 63 | 1.55 | 56.32 |
| SemantiCodec | 2.91 | 8.97 | 96.0 | 75.9 | 94.4 | 0.62 | 1.87 | 36.21 |
| Mimi | 3.29 | 5.73 | 96.0 | 95.6 | 91.8 | 137 | 2.08 | 30.96 |
| WavTokenizer | 3.78 | 11.55 | 95.4 | **100.0** | 96.7 | 181 | 2.64 | 49.73 |
| BigCodec | 4.11 | 2.55 | **98.5** | **100.0** | 98.6 | 22 | 2.86 | 15.24 |
| Stable Codec | **4.32** | 4.97 | 94.7 | 98.5 | 94.7 | 103 | 3.47 | 56.99 |
| **FocalCodec@50** | 4.05 | **2.18** | 97.4 | **100.0** | **98.9** | 185 | 2.96 | **12.57** |
| **FocalCodec@25** | 4.14 | 3.30 | 96.3 | 99.8 | 98.4 | 195 | 3.16 | 19.78 |
| **FocalCodec@12.5** | 4.22 | 7.94 | 93.9 | 98.2 | 97.4 | **208** | 3.37 | 54.15 |{{< /table-caption >}}
> 🔼 표 2는 깨끗한 음성 재합성 결과를 보여줍니다.  다양한 저비트율 코덱들의 성능을 비교 분석하며,  자연스러움(UTMOS), 단어 오류율(dWER), 화자 유사도(Sim), 실시간 비율(RTF) 등의 지표를 통해 객관적인 평가를 제시합니다.  영문 LibriSpeech 데이터셋의 test-clean 부분과 다국어 LibriSpeech 데이터셋의 7개 언어(네덜란드어, 프랑스어, 독일어, 이탈리아어, 폴란드어, 포르투갈어, 스페인어) 테스트 결과를 포함하여 다양한 조건에서의 코덱 성능을 비교 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Clean speech resynthesis.
> </details>

{{< table-caption >}}
| Codec | DNSMOS ↑ | dWER ↓ | Sim ↑ | Code Usage ↑ | Norm Entropy ↑ | RTF ↑ |  |
|---|---|---|---|---|---|---|---| 
| **Reference** | 3.56 | 0.00 | 100.0 | — | — | — | — |
| EnCodec | 2.76 | 28.16 | 87.7 | 77.5 | 78.1 | 44 |  |
| DAC | 2.72 | 63.90 | 79.8 | 98.7 | 88.4 | 48 |  |
| WavLM6-KM | 3.06 | 20.67 | 82.9 | 24.8 | 92.3 | 44 |  |
| SpeechTokenizer | 2.74 | 34.51 | 82.2 | 88.1 | 88.4 | 42 |  |
| SemantiCodec | 3.13 | 31.46 | 90.6 | 52.4 | 92.6 | 0.28 |  |
| Mimi | 3.01 | 28.00 | 87.8 | 78.6 | 85.5 | 47 |  |
| WavTokenizer | 3.09 | 42.12 | 89.8 | 94.8 | 94.0 | 63 |  |
| BigCodec | 3.19 | 20.67 | **92.3** | **99.8** | **96.8** | 17 |  |
| Stable Codec | **3.33** | 20.32 | 88.8 | 75.7 | 95.4 | 39 |  |
| **FocalCodec@50** | 3.16 | **8.08** | 91.3 | 98.0 | 96.2 | 80 |  |
| **FocalCodec@25** | 3.17 | 11.75 | 90.1 | 89.6 | 96.0 | **81** |  |
| **FocalCodec@12.5** | 3.22 | 27.97 | 84.7 | 77.3 | 95.5 | 79 |  |
|  |  | _VoiceBank test_ |  |  |  |  |  |
| **Reference** | 3.73 | 0.00 | 100.0 | — | — | — | — |
| EnCodec | 2.40 | 55.17 | 86.3 | 84.4 | 78.7 | 97 |  |
| DAC | 2.40 | 90.92 | 76.6 | 99.1 | 88.8 | 91 |  |
| WavLM6-KM | 2.87 | 36.60 | 85.9 | 26.8 | 95.5 | 65 |  |
| SpeechTokenizer | 2.58 | 57.26 | 82.8 | 93.5 | 96.5 | 63 |  |
| SemantiCodec | 2.67 | 51.18 | 89.9 | 64.7 | 90.8 | 91 |  |
| Mimi | 2.65 | 49.14 | 89.4 | 90.8 | 90.1 | 104 |  |
| WavTokenizer | 2.53 | 70.10 | 86.3 | 96.4 | 95.4 | **165** |  |
| BigCodec | 2.75 | 53.26 | 88.3 | **100.0** | 98.2 | 19 |  |
| Stable Codec | 2.91 | 43.52 | 90.0 | 95.8 | 93.4 | 68 |  |
| **FocalCodec@50** | **2.93** | **27.89** | **91.6** | **100.0** | **98.5** | 155 |  |
| **FocalCodec@25** | 2.91 | 34.27 | 90.7 | 99.6 | 97.9 | 161 |  |
| **FocalCodec@12.5** | 2.92 | 42.59 | 88.9 | 97.2 | 97.2 | 164 |  |
|  |  | _Libri1Mix test_ |  |  |  |  |  |{{< /table-caption >}}
> 🔼 표 3은 잡음이 포함된 음성 재합성 결과를 보여줍니다.  다양한 코덱의 성능을 잡음이 있는 음성(VoiceBank 및 LibriMix 데이터셋)에 대해 평가하여,  DNSMOS(음성 자연도), dWER(단어 오류율), Sim(화자 유사도), 사용률, 엔트로피, RTF(실시간 계수) 와 같은 지표들을 통해 저비트율 코덱의 잡음 내성 및 음성 재구성 품질을 분석합니다.  특히, FocalCodec이 잡음 환경에서도 경쟁력 있는 성능을 보이는지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Noisy speech resynthesis.
> </details>

{{< table-caption >}}
| Codec | UTMOS ↑ | dWER ↓ | Sim ↑ | RTF ↑ |
|---|---|---|---|---|
| **VCTK** |  |  |  |  |
| Reference | 4.09 | 0.00 | 100.0 | — |
| EnCodec | 1.24 | 86.52 | 72.2 | 57 |
| DAC | 1.25 | 104.00 | 67.2 | 60 |
| WavLM6-KM | 2.90 | 26.68 | 92.4 | 57 |
| SpeechTokenizer | 1.49 | **20.32** | 81.2 | 33 |
| SemantiCodec | 2.02 | 106.00 | 72.8 | 0.60 |
| Mimi | 2.40 | 110.00 | 89.7 | 71 |
| WavTokenizer | 3.13 | 43.15 | 73.4 | 89 |
| BigCodec | 1.31 | 99.96 | 68.9 | 13 |
| Stable Codec | **3.76** | 27.63 | 71.1 | 65 |
| **FocalCodec@50** | 3.38 | 21.27 | 92.2 | 116 |
| **FocalCodec@25** | 3.40 | 23.59 | **92.6** | **118** |
| **FocalCodec@12.5** | 3.43 | 29.93 | **92.6** | 117 |{{< /table-caption >}}
> 🔼 표 4는 음성 변환 실험 결과를 보여줍니다.  'One-shot voice conversion'이란 용어는 참조 음성을 사용하여 단 한 번의 과정으로 특정 화자의 음성을 다른 화자의 음성으로 변환하는 것을 의미합니다.  이 표는 다양한 코덱(FocalCodec, EnCodec, DAC, WavLM6-KM, SpeechTokenizer, SemantiCodec, Mimi, WavTokenizer, BigCodec, Stable Codec)을 사용한 실험 결과를 보여주며,  각 코덱에 대해  음성의 자연스러움(UTMOS),  오류율(dWER),  화자 유사도(Sim),  사용률(Usage),  엔트로피(Entropy) 그리고 실시간 처리 비율(RTF)을 나타냅니다.  VCTK 및 LibriSpeech 데이터셋을 사용한 결과가 제시됩니다.  다른 코덱들과 비교하여 FocalCodec의 성능을 평가하여, FocalCodec의 효율성과 음성 변환 능력을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 4: One-shot voice conversion.
> </details>

{{< table-caption >}}
| Codec | ASR (WER ↓) | SI (ER ↓) | SER (ER ↓) | SE (DNSMOS ↑) | SE (dWER ↓) | SS (Sim ↑) | SS (DNSMOS ↑) | SS (dWER ↓) | TTS (Sim ↑) | TTS (UTMOS ↑) | TTS (dWER ↓) | TTS (Sim ↑) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Reference | — | — | — | — | 3.56 | 0.00 | 100.0 | 3.77 | 0.00 | 100.0 | 4.09 | 0.00 | 100.0 |
| EnCodec | 27.89 | 3.00 | 47.00 | 3.11 | 37.10 | 85.9 | 3.11 | 78.51 | 87.3 | 1.69 | 74.07 | 79.1 |
| DAC | 35.89 | 3.27 | 45.90 | 3.03 | 67.65 | 81.7 | 2.76 | 106.00 | 83.3 | 1.36 | 61.11 | 84.1 |
| WavLM6-KM | 19.04 | 22.30 | 42.90 | 3.52 | 22.85 | 83.6 | 3.49 | 76.91 | 85.0 | 3.71 | 48.51 | 88.2 |
| SpeechTokenizer | **14.97** | 2.73 | **41.50** | 3.21 | 29.82 | 85.9 | 3.13 | 83.99 | 87.3 | 2.63 | 47.81 | 88.3 |
| SemantiCodec | 41.42 | 15.90 | 51.60 | **3.59** | 102.00 | 83.3 | 3.59 | 123.00 | 84.4 | 2.72 | 59.85 | 90.8 |
| Mimi | 22.98 | 5.43 | 44.70 | 3.30 | 53.98 | 84.6 | 3.41 | 93.23 | 88.1 | 3.05 | 39.50 | **93.3** |
| WavTokenizer | 35.62 | 2.44 | 49.80 | 3.41 | 51.75 | 88.6 | 3.54 | 105.00 | 86.4 | 3.65 | 59.22 | 89.6 |
| BigCodec | 26.41 | **2.34** | 47.50 | 3.52 | 26.68 | **93.2** | 3.54 | 89.24 | **89.4** | 3.24 | 63.83 | 87.8 |
| Stable Codec | 16.85 | 16.50 | 46.54 | 3.55 | 35.57 | 82.8 | 3.61 | 103.00 | 78.2 | 2.86 | 56.97 | 84.3 |
| **FocalCodec@50** | 17.63 | 4.48 | 45.60 | 3.47 | **10.93** | 91.4 | **3.71** | **73.87** | 89.0 | 4.05 | 39.58 | 92.9 |
| **FocalCodec@25** | 21.12 | 6.07 | 46.80 | 3.49 | 14.74 | 90.0 | 3.69 | 99.96 | 85.4 | 4.12 | 30.28 | 91.4 |
| **FocalCodec@12.5** | 33.24 | 11.69 | 46.30 | 3.58 | 36.98 | 86.9 | 3.57 | 116.00 | 80.8 | **4.16** | **29.91** | 91.5 |{{< /table-caption >}}
> 🔼 표 5는 음성 인식(ASR), 화자 식별(SI), 음성 감정 인식(SER)과 같은 다운스트림 작업과 음성 향상(SE), 음성 분리(SS), 음성 합성(TTS)과 같은 생성적 작업에 대한 FocalCodec 및 기준 모델의 성능 평가 결과를 보여줍니다.  각 작업에 대한 WER, ER, DNSMOS, Sim, UTMOS와 같은 다양한 지표들이 제시되어 있습니다.  이 표는 FocalCodec이 다운스트림 작업에서도 경쟁력 있는 성능을 보여줌을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Evaluation on downstream tasks.
> </details>

{{< table-caption >}}
| Compression/Decompression | Down/Upscale | Quantizer | Decoder | UTMOS ↑ | dWER ↓ | Sim ↑ |
|---|---|---|---|---|---|---|
| Focal modulation | Snake | BSQ | Vocos | **4.14** | **2.54** | 95.3 |
| Focal modulation | Snake | BSQ | HiFi-GAN | 3.73 | **2.54** | **95.7** |
| Focal modulation | Snake | LFQ | HiFi-GAN | 3.74 | 2.75 | 95.4 |
| Focal modulation | Leaky ReLU | LFQ | HiFi-GAN | 3.72 | 2.85 | 95.2 |
| **Conformer** | **Snake** | LFQ | HiFi-GAN | 3.74 | 3.58 | 94.3 |
| **AMP** | Snake | LFQ | HiFi-GAN | 3.70 | 4.52 | 94.3 |
| **Linear** | Snake | LFQ | HiFi-GAN | 2.55 | 9.37 | 82.5 |{{< /table-caption >}}
> 🔼 표 6은 FocalCodec 모델의 성능에 대한 ablation study 결과를 보여줍니다.  다양한 구성 요소(양자화, 디코더, 압축/압축 해제 블록, 활성화 함수)를 변경하여 각 요소가 전체 성능에 미치는 영향을 분석한 것입니다.  각 실험 설정에 따른 UTMOS 점수, dWER, Sim 값을 비교하여 어떤 구성이 최적의 성능을 내는지 확인합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Ablation studies.
> </details>

{{< table-caption >}}
| Codec | Causal | Training Datasets | Hours | Multilingual | Audio Domain | Checkpoint |
|---|---|---|---|---|---|---|
| EnCodec (Défossez et al., 2023) | Optional | DNS, CommonVoice, AudioSet, FSD50K, Jamendo | 17,000+ | Yes | General | https://huggingface.co/facebook/encodec_24khz |
| DAC (Kumar et al., 2023) | No | DAPS, DNS, CommonVoice, VCTK, MUSDB, Jamendo | 10,000+ | Yes | General | https://github.com/descriptinc/descript-audio-codec/releases/download/0.0.5/weights_16khz.pth |
| WavLM6-KM (Wang et al., 2024) | No | Subset of LibriSpeech (in addition to Libri-Light, GigaSpeech, and VoxPopuli English for WavLM pretraining) | 460 (+ 94,000) | No | Speech | https://huggingface.co/lucadellalib/discrete-wavlm-codec |
| SpeechTokenizer (Zhang et al., 2024) | No | LibriSpeech | 960 | No | Speech | https://huggingface.co/fnlp/SpeechTokenizer/speechtokenizer_hubert_avg |
| SemantiCodec (Liu et al., 2024) | No | GigaSpeech, subset of OpenSLR, Million Song Dataset, MedleyDB, MUSDB18, AudioSet, WavCaps, VGGSound | 20,000+ | Yes | General | https://huggingface.co/haoheliu/SemantiCodec/tree/main/semanticodec_tokenrate_50 |
| Mimi (Défossez et al., 2024) | Yes | Predominantly English speech (in addition to Libri-Light, GigaSpeech, and VoxPopuli English for WavLM pretraining) | 7,000,000 (+ 94,000) | Likely | Speech | https://huggingface.co/kyutai/mimi |
| WavTokenizer (Ji et al., 2024) | No | LibriTTS, VCTK, subset of CommonVoice, subset of AudioSet, Jamendo, MUSDB | 8000 | Yes | General | https://huggingface.co/novateur/WavTokenizer-large-unify-40token |
| BigCodec (Xin et al., 2024) | No | LibriSpeech | 960 | No | Speech | https://huggingface.co/Alethia/BigCodec/resolve/main/bigcodec.pt |
| Stable Codec (Parker et al., 2024) | Optional | Libri-Light, Multilingual LibriSpeech English | 105,000 | No | Speech | https://huggingface.co/stabilityai/stable-codec-speech-16k |{{< /table-caption >}}
> 🔼 표 7은 논문에서 비교 기준으로 사용된 최신 저비트율 음성 코덱들의 특징을 요약한 표입니다.  각 코덱의 인과성 여부, 학습에 사용된 데이터셋(크기 포함), 데이터셋의 다국어 지원 여부, 오디오 도메인, 그리고 체크포인트 접근 가능 여부를 보여줍니다.  이 표는 본 논문의 FocalCodec 모델의 성능을 기존 최고 성능 모델들과 비교 평가하는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Baseline codecs.
> </details>

{{< table-caption >}}
| Codec | Bitrate (kbps) | Sample Rate (kHz) | Token Rate (Hz) | Codebooks | Code Size | Params (M) | MACs (G) | UTMOS ↑ | dWER ↓ | Sim ↑ |
|---|---|---|---|---|---|---|---|---|---|---|
| Reference | — | — | — | — | — | — | — | 4.09 | 0.00 | 100.0 |
| TS3-Codec (X2) | 0.85 | 16 | 50.0 | 1 × 131072 | 16 | 204 | 8 | 3.84 | 4.51 | 97.1 |
| **FocalCodec@50** | 0.65 | 16 | 50.0 | 1 × 8192 | 13 | 142 | 9 | 4.05 | **2.18** | **97.4** |
| **FocalCodec@25** | 0.33 | 16 | 25.0 | 1 × 8192 | 13 | 144 | 9 | 4.14 | 3.30 | 96.3 |
| **FocalCodec@12.5** | 0.16 | 16 | 12.5 | 1 × 8192 | 13 | 145 | 8 | **4.22** | 7.94 | 93.9 |{{< /table-caption >}}
> 🔼 표 8은 LibriSpeech 테스트-클린 데이터셋을 사용하여 수행된 깨끗한 음성 재합성 결과를 보여줍니다.  비교 대상 코덱들의 비트 전송률, 표본화율, 토큰화율, 코드북 크기, 매개변수 수, MACs (초당 곱셈-누산 연산 수),  UTMOS(음질), dWER(단어 오류율), Sim(스피커 유사도) 점수를 비교 분석하여 FocalCodec의 성능을 평가합니다. 특히, FocalCodec의 저비트레이트에서도 우수한 성능을 보이는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Clean speech resynthesis on LibriSpeech test-clean.
> </details>

{{< table-caption >}}
| Codec | Chunk Size | UTMOS ↑ | dWER ↓ | Sim ↑ | 
|---|---|---|---|---| 
| **FocalCodec@50** | Inf | 4.05 | **2.18** | **97.4** | 
| **FocalCodec@25** | Inf | 4.14 | 3.30 | 96.3 | 
| **FocalCodec@12.5** | Inf | **4.22** | 7.94 | 93.9 | 
| **FocalCodec@50** | 2000 (125 ms) | 2.17 | 6.06 | 95.9 | 
| **FocalCodec@50** | 4000 (250 ms) | 2.71 | 4.62 | 96.6 | 
| **FocalCodec@50** | 8000 (500 ms) | 3.16 | 4.55 | 96.9 | 
| **FocalCodec@25** | 8000 (500 ms) | 2.95 | 12.17 | 95.6 | 
| **FocalCodec@12.5** | 8000 (500 ms) | 2.84 | 47.43 | 91.8 | {{< /table-caption >}}
> 🔼 표 9는 오프라인(전체 데이터를 한꺼번에 처리) 방식과 청크 단위 스트리밍 방식(데이터를 여러 청크로 나눠 처리) 추론 성능을 비교한 표입니다.  다양한 청크 크기(2000, 4000, 8000 샘플)에 따른 FocalCodec의 UTMOS, dWER, Sim 성능 변화를 보여줍니다.  청크 크기가 클수록 오프라인 방식과 유사한 성능을 보이지만,  특히 저 비트레이트 환경에서는 청크 크기가 작을 때 성능 저하가 발생하는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Offline vs chunk-wise streaming inference.
> </details>

{{< table-caption >}}
| Codec | Input Features | DNSMOS ↑ | dWER ↓ | Sim ↑ |
|---|---|---|---|---|
| **Libri2Mix** |
| Reference | — | 3.77 | 0.00 | 100.0 |
| WavLM6-KM | Discrete | 3.49 | 76.91 | 85.0 |
| WavLM6-KM | Continuous | 3.68 | 23.09 | 89.4 |
| **FocalCodec@50** | Discrete | 3.71 | 73.87 | 89.0 |
| **FocalCodec@50** | Continuous | **3.76** | **17.35** | **93.8** |{{< /table-caption >}}
> 🔼 표 10은 음성 분리 작업에 대한 불연속 및 연속 입력 특징을 비교 분석한 결과를 보여줍니다.  연속적인 특징(WavLM 인코더의 출력)을 사용했을 때, 불연속적인 특징(FocalCodec 및 WavLM-KM6 코덱의 양자화된 출력)을 사용했을 때보다 음성 분리 성능이 크게 향상됨을 보여줍니다.  이 표는 FocalCodec이  음성 분리 과업에 적합한 표현을 생성하는 능력을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Discrete vs continuous input features for speech separation.
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