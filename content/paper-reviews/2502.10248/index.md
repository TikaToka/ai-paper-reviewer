---
title: "Step-Video-T2V Technical Report: The Practice, Challenges, and Future of Video Foundation Model"
summary: "Step-Video-T2V: 300억 개 매개변수를 가진 최첨단 텍스트-비디오 사전 훈련 모델"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Video Understanding", "🏢 Step-Video Team",]
showSummary: true
date: 2025-02-14
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.10248 {{< /keyword >}}
{{< keyword icon="writer" >}} Guoqing Ma et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-17 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.10248" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.10248" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/step-video-t2v-technical-report-the-practice" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

최근 몇 년 동안 대규모 언어 모델(LLM)의 발전이 눈부시지만, 동적인 시각 정보를 다루는 데는 한계가 있습니다. 이에 따라 고품질 비디오 생성 기술에 대한 요구가 높아지고 있으며, 이는 인공지능(AGI) 연구의 중요한 과제 중 하나입니다. 본 논문에서는 이러한 문제를 해결하기 위해 Step-Video-T2V라는 새로운 모델을 제시합니다.

Step-Video-T2V는 **300억 개의 매개변수**를 갖는 최첨단 텍스트-비디오 사전 훈련 모델로, **영상의 움직임 및 미적 요소를 정확하게 표현**하는 고품질 비디오를 생성할 수 있습니다. 또한, **중국어와 영어를 모두 지원**하며, 다양한 품질의 비디오 데이터셋을 효과적으로 활용하는 훈련 전략을 제시합니다.  본 논문에서는 **Step-Video-T2V-Eval이라는 새로운 벤치마크 데이터셋**도 공개하여, 모델의 성능을 객관적으로 평가할 수 있도록 하였습니다.  **비디오 압축 및 고품질 비디오 생성을 위한 다양한 기술**들도 소개하고, 향후 비디오 기반 모델 연구를 위한 방향을 제시합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 300억 개의 매개변수를 갖는 최첨단 텍스트-비디오 사전 훈련 모델 Step-Video-T2V를 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 비디오 생성을 위한 새로운 벤치마크 데이터셋 Step-Video-T2V-Eval을 공개 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 효율적인 비디오 압축 및 고품질 비디오 생성을 위한 혁신적인 기술들을 제시 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
이 논문은 **비디오 기반 모델의 발전에 중요한 기여**를 하며, **대규모 데이터셋 구축 및 훈련 전략**, **새로운 벤치마크 데이터셋 제시**, **고품질 비디오 생성을 위한 효율적인 방법** 등을 제시합니다. 이는 **비디오 생성 분야의 연구 동향을 반영**하며, 향후 연구의 새로운 방향을 제시하는 데 중요한 의미를 지닙니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.10248/extracted/6204622/figure/model_architecture.png)

> 🔼 그림 1은 Step-Video-T2V 모델의 전체 아키텍처를 보여줍니다. 비디오는 16x16 공간 및 8x 시간 압축률을 달성하는 고압축 Video-VAE로 표현됩니다. 사용자 프롬프트는 영어와 중국어를 모두 처리하기 위해 두 개의 이중 언어 사전 훈련된 텍스트 인코더를 사용하여 인코딩됩니다. 3D 전체 어텐션을 사용하는 DiT는 플로우 매칭을 사용하여 훈련되며, 텍스트 임베딩과 시간 단계를 조건화 요소로 사용하여 입력 노이즈를 잠재 프레임으로 제거하는 데 사용됩니다. 생성된 비디오의 시각적 품질을 더욱 향상시키기 위해 비디오 기반 DPO 방식이 적용되어 인공물을 효과적으로 줄이고 더욱 부드럽고 사실적인 비디오 출력을 보장합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Architecture overview of Step-Video-T2V. Videos are represented by a high-compression Video-VAE, achieving 16x16 spatial and 8x temporal compression ratios. User prompts are encoded using two bilingual pre-trained text encoders to handle both English and Chinese. A DiT with 3D full attention is trained using Flow Matching and is employed to denoise input noise into latent frames, with text embeddings and timesteps serving as conditioning factors. To further enhance the visual quality of the generated videos, a video-based DPO approach is applied, which effectively reduces artifacts and ensures smoother, more realistic video outputs.
> </details>





{{< table-caption >}}
| Layers | Attention Heads | Head Dim | FFN Dim | Cross-Attn Dim | Activation Function | Normalization |
|---|---|---|---|---|---|---|
| 48 | 48 | 128 | 24,576 | (6,144, 1,024) | GELU-approx | RMSNorm |{{< /table-caption >}}

> 🔼 Step-Video-T2V 모델의 하이퍼파라미터들을 보여주는 표입니다.  레이어 수, 어텐션 헤드 수, 헤드 차원, 피드포워드 네트워크 차원, 크로스 어텐션 차원, 활성화 함수, 그리고 정규화 기법 등 Step-Video-T2V 모델의 주요 구성 요소들의 세부적인 설정값들을 보여줍니다. 이를 통해 Step-Video-T2V 모델의 구조 및 성능에 대한 이해를 높일 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Hyper-parameters used in Step-Video-T2V.
> </details>





### In-depth insights


#### Video-VAE Compression
본 논문에서 제시된 Video-VAE 압축 기법은 **비디오 생성 모델의 계산 비용을 크게 줄이기 위한 핵심 전략**입니다.  기존의 낮은 해상도 전처리 방식과 달리, Video-VAE는 고해상도 비디오를 효율적으로 압축하여 모델 학습 및 추론 속도를 향상시킵니다. 이는 **16x16 공간 압축 및 8x 시간적 압축**이라는 인상적인 성과를 통해 입증됩니다.  단순한 압축 이상으로, Video-VAE는 **뛰어난 비디오 재구성 품질**을 유지하면서 이러한 높은 압축률을 달성하여, 압축으로 인한 정보 손실을 최소화합니다. 이는 고품질의 비디오 생성에 필수적입니다.  **VAE의 새로운 이중 경로 아키텍처**와 **3D 합성곱 모듈**은 압축 과정에서 중요한 역할을 합니다. 이를 통해 공간 및 시간적 중복성을 효과적으로 제거하여 압축 효율을 극대화하고, 고주파수 세부 정보와 저주파수 구조를 모두 보존하는 균형을 이룹니다.  결론적으로 Video-VAE 압축 기법은 **모델 크기 및 계산 비용 감소와 고품질 비디오 생성 사이의 균형을 성공적으로 맞춘 혁신적인 기술**이며,  향후 비디오 기반 기초 모델 개발에 중요한 영향을 미칠 것으로 예상됩니다.

#### DPO Refinement
본 논문에서 'DPO 개선'이라는 제목으로 다루어질 내용은, **Direct Preference Optimization (DPO)** 기법을 비디오 생성 모델에 적용하여 생성 결과물의 질적 향상을 도모하는 과정과 그에 대한 심층적인 고찰을 의미할 것입니다.  DPO는 인간의 선호도 피드백을 직접적으로 활용하여 모델을 개선하는 강화학습 방식으로, 사용자의 선호도에 따라 생성 결과물을 조정함으로써 보다 만족스러운 결과를 얻을 수 있습니다. 이 과정에서 중요한 점은, **신뢰할 수 있는 선호도 데이터를 확보하는 것**입니다.  이는 효율적인 데이터 수집 및 주석 방식, 그리고 잠재적 편향을 최소화하기 위한 엄격한 품질 관리 프로세스를 필요로 합니다.  **다양한 프롬프트와 그에 따른 여러 생성 결과물에 대한 인간의 평가를 수집**하여 모델의 정책을 개선하고, **저품질 또는 부적절한 결과물의 생성을 방지**해야 합니다.  여기에는 효율적인 평가 시스템 구축과, 평가자의 주관성을 최소화하기 위한 엄격한 평가 기준이 필요합니다.  또한, **DPO의 훈련 과정에서 발생할 수 있는 안정성 문제**를 해결하는 것도 중요합니다.  과도한 훈련으로 인한 과적합이나, 참조 모델로부터의 과도한 이탈을 방지하기 위한 방안 모색이 필요합니다.  **계산 비용 및 훈련 시간을 최소화**하기 위한 효율적인 알고리즘과 최적화 기법의 적용 또한 중요한 연구 과제입니다.  결론적으로, 'DPO 개선'은 단순한 기술적 문제 해결을 넘어, **인간의 미적 감각과 창의성을 반영한** 보다 자연스럽고 섬세한 비디오 생성을 위한 핵심적인 과정으로 볼 수 있습니다.

#### Training Strategies
본 논문에서 제시된 다양한 영상 생성 모델 학습 전략은 크게 **전이 학습(Transfer Learning)**, **단계적 학습(Cascaded Training)**, 그리고 **직접적 선호도 최적화(Direct Preference Optimization, DPO)**로 나눌 수 있습니다.  먼저, **텍스트-이미지(T2I) 전이 학습**을 통해 모델이 시각적 개념을 이해하도록 한 후, **텍스트-영상-이미지(T2VI) 전이 학습**을 통해 시간적 동작을 학습하고, 마지막으로 **텍스트-영상(T2V) 미세조정**을 거쳐 특정 작업에 대한 성능을 높입니다.  이러한 단계적 학습 방식은 각 단계에서 축적된 지식을 바탕으로 점진적으로 성능을 향상시키는 효과적인 전략입니다.  특히, **저해상도 영상을 이용한 초기 학습**을 통해 계산 비용을 절감하고 모델의 안정성을 확보하는 동시에 **고해상도 영상 학습**을 통해 세부적인 디테일을 학습하는 점이 인상적입니다.  **DPO 전략**은 사용자 피드백을 통해 생성 결과의 품질을 향상시키는 데 중요한 역할을 합니다.  **다양한 해상도 영상의 효율적인 병렬 처리를 위한 부하 분산 전략**도 함께 제시되어 있어, 대규모 학습 환경에서 효율성을 높이는 데 기여합니다.  **자동화된 모니터링 시스템**을 통해 학습 과정의 안정성을 확보하고 성능 저하 요인을 신속하게 파악하여 문제 해결에 도움을 줄 수 있다는 점도 중요한 특징입니다.

#### Model Architecture
본 논문에서 제시된 비디오 생성 모델의 아키텍처는 **트랜스포머 기반의 확산 모델**을 중심으로 구성되어 있습니다. 특히, **3D 풀 어텐션 메커니즘**을 사용하여 공간 및 시간적 정보를 효과적으로 모델링하는 점이 특징입니다. 이는 기존의 공간-시간적 어텐션에 비해 계산 비용이 증가하지만, 보다 **매끄럽고 일관성 있는 모션 다이내믹스**를 생성하는 데 효과적입니다.  **비디오 VAE(Variational Autoencoder)**를 통해 고차원의 비디오 데이터를 저차원의 잠재 공간으로 효율적으로 압축하고, 이를 통해 모델의 계산 복잡도를 낮추고 훈련 효율을 높였습니다.  **이중 언어(영어, 중국어) 텍스트 인코더**를 사용하여 다양한 언어의 프롬프트를 처리할 수 있습니다.  또한, **Video-DPO(Direct Preference Optimization)** 기법을 적용하여 생성된 비디오의 화질을 개선하고, 사용자의 선호도를 반영했습니다.  **전체적으로, 제안된 아키텍처는 대규모 비디오 데이터셋을 활용하여 훈련된 강력한 비디오 생성 모델을 구축하는 데 효과적인 방법론**을 보여줍니다. 하지만, 계산 비용 및 복잡도 측면에서 개선의 여지가 있으며, 물리 법칙 준수 및 복잡한 액션 시퀀스 생성과 같은 향후 연구 과제가 남아있습니다.

#### Future Directions
이 연구는 비디오 기반 모델의 현재 한계와 미래 방향에 대한 심도있는 논의를 제공합니다. **텍스트-비디오 생성 모델의 주요 과제는 물리 법칙 준수, 복잡한 동작 시퀀스 생성, 그리고 훈련 데이터의 부족**입니다.  **향상된 물리적 사실성을 위해서는 자기회귀 및 확산 모델을 통합하는 혼합 접근 방식이 필요**하며, 이는 보다 사실적이고 일관된 비디오 생성을 가능하게 합니다. 또한, **복잡한 동작을 표현하기 위해서는 인과 관계 모델링 메커니즘 도입이 필수적**입니다.  마지막으로, **고품질의 라벨링된 데이터 확보**는 모델 성능 향상에 중요한 요소이며, 이를 위해서는 **보다 효율적인 데이터 수집 및 주석 방식**이 요구됩니다.  미래 연구는 이러한 과제들을 해결하기 위한 새로운 모델 아키텍처, 훈련 전략, 그리고 데이터 관리 방식을 모색하는 데 집중해야 합니다.  **강화 학습 기반 최적화 기법은 사용자 피드백을 효과적으로 통합하여 모델의 생성 품질을 향상**시킬 수 있는 잠재력을 가지고 있습니다.  하지만, 비디오 생성 분야에서는 명확한 목표와 정답이 있는 자연어 처리와 달리, **보상 함수(reward function) 설계에 어려움이 있으므로 보다 심도있는 연구**가 필요합니다.  **다국어 지원 확대 및 긴 비디오 생성을 위한 모델 확장**도 중요한 미래 연구 방향입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.10248/x1.png)

> 🔼 그림 2는 논문의 4.1 Video-VAE 섹션에 있는 Video-VAE의 아키텍처를 개략적으로 보여줍니다. Video-VAE는 비디오 생성 모델에서 고해상도 비디오를 효율적으로 처리하기 위해 고안된 심층 압축 변이 오토인코더입니다. 이 그림은 인코더와 디코더의 주요 구성 요소와 이들이 비디오를 어떻게 압축하고 디코딩하는지 보여주는 단순화된 다이어그램입니다.  더 자세한 내용은 본문을 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Figure 2: Architecture overview of Video-VAE.
> </details>



![](https://arxiv.org/html/2502.10248/extracted/6204622/figure/dit-arch.png)

> 🔼 이 그림은 Step-Video-T2V 모델의 이중 언어 텍스트 인코더와 3D 어텐션을 사용하는 DiT(Diffusion Transformer)의 아키텍처를 보여줍니다.  이중 언어 텍스트 인코더는 영어와 중국어 프롬프트 모두를 처리하여,  Hunyuan-CLIP과 Step-LLM 두 가지 모델을 사용하여 텍스트 임베딩을 생성합니다. DiT는 3D 풀 어텐션을 사용하여 시공간적 정보를 모델링하고,  텍스트 임베딩을 조건으로 사용하여 노이즈가 있는 잠재 프레임을 디노이징합니다. 그림에는 각 구성 요소(이중 언어 텍스트 인코더, 게이트, FFN(Feed-Forward Network), 스케일/쉬프트, 크로스 어텐션, 셀프 어텐션, ROPE-3D, QK-정규화, AdaLN, 타임스텝 t)와 데이터 흐름이 자세히 표시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: The model architecture of our bilingual text encoder and DiT with 3D Attention.
> </details>



![](https://arxiv.org/html/2502.10248/x2.png)

> 🔼 본 논문의 그림 4는 사람의 피드백을 통합하는 전체 파이프라인을 보여줍니다. 사용자 프롬프트는 먼저 Step-Video-T2V 모델에 입력되어 비디오를 생성합니다. 생성된 비디오는 어노테이터에 의해 평가되고, 선호도(positive) 또는 비선호도(negative) 데이터로 분류됩니다. 이러한 선호도 데이터는 보상 모델을 훈련하는 데 사용되며, 이 보상 모델은 현재 정책(모델)을 업데이트하여 선호도 데이터와 더욱 일치하도록 조정하는 역할을 합니다. 참고 정책(기준 모델)은 현재 정책이 참고 정책에서 너무 벗어나는 것을 방지하기 위해 도입되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Overall pipeline of incorporating human feedback.
> </details>



![](https://arxiv.org/html/2502.10248/x3.png)

> 🔼 이 그림은 Step-Video-T2V 모델이 생성한 두 개의 발레리나 연습 영상을 보여줍니다. 두 영상 모두 동일한 프롬프트('발레리나가 무용실에서 연습하는 모습')를 사용하여 생성되었지만, 인간 평가자에 의해 선호도가 다르게 평가되었습니다. (a)는 비선호 영상, (b)는 선호 영상으로 분류되었으며, 이를 통해 인간의 미적 기준과 모델 출력 간의 차이를 보여줍니다. 이는 Step-Video-T2V 모델의 성능 향상을 위한 인간 피드백의 중요성을 시각적으로 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: We generate different samples with same prompt ('A ballet dancer practicing in the dance studio' in this case), and annotate these samples as non-preferred (a) or preferred (b).
> </details>



![](https://arxiv.org/html/2502.10248/x10.png)

> 🔼 그림 6은 Step-Video-T2V Turbo 모델을 사용하여 10회의 순전파(NFE)만으로 생성한 비디오 샘플들을 보여줍니다.  Step-Video-T2V Turbo는 추론 속도를 높이기 위해 설계된 모델 변형으로,  기존 모델보다 훨씬 적은 연산으로 고품질 비디오를 생성할 수 있습니다.  이 그림은 Step-Video-T2V Turbo의 효율성과 생성 품질을 시각적으로 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Generated samples with Step-Video-T2V Turbo with 10 NFE.
> </details>



![](https://arxiv.org/html/2502.10248/x11.png)

> 🔼 그림 7은 Step-Video-T2V 학습 시스템의 전체 워크플로우를 보여줍니다. 오프라인 단계에서는 자체 구축한 학습 에뮬레이터(Step Emulator)를 사용하여 최적의 자원 할당 및 학습 병렬화 전략을 결정합니다. 이후, 이론적으로 최적화된 자원 할당 계획을 바탕으로 학습 작업을 GPU가 할당된 학습 클러스터와 추론 클러스터에 배포합니다.  학습 클러스터는 비디오 DiT를 학습하며, 에뮬레이터에서 권장하는 병렬화 전략을 사용하여 모델 FLOP 활용도(MFU)를 극대화합니다. VAE와 텍스트 인코더는 추론 클러스터에서 실행되며, DiT 학습에 필요한 처리된 입력 데이터(이미지/비디오 잠재 벡터와 텍스트 임베딩 쌍)를 지속적으로 제공합니다. 클러스터 간 데이터 전송은 고성능 RPC 프레임워크인 StepRPC를 통해 수행됩니다. StepRPC는 TCP와 RDMA 프로토콜을 통합하여 효율적인 클러스터 간 통신을 가능하게 합니다. 대규모 학습 중 체계적인 모니터링 및 분석을 위해 StepTelemetry라는 2계층 모니터링 시스템을 구현했습니다. StepTelemetry는 추론 클러스터와 학습 클러스터에서 상세한 데이터 통계를 수집하여 다차원적인 통찰력을 제공하고 체계적인 성능 병목 현상 감지를 가능하게 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: The workflow of Step-Video-T2V training system.
> </details>



![](https://arxiv.org/html/2502.10248/x12.png)

> 🔼 그림 8은 다양한 해상도의 비디오와 이미지 데이터를 처리하는 동안 발생할 수 있는 계산 부하 불균형 문제를 해결하기 위한 하이브리드 입자 크기 기반 부하 분산 전략을 보여줍니다.  먼저, 서로 다른 해상도의 비디오에 대해 최적의 배치 크기를 계산하여 FLOP(Floating Point Operations)을 조정합니다.  그런 다음, 이미지 패딩을 사용하여 남은 FLOP 불균형을 미세 조정합니다. 이러한 두 단계를 통해 시스템은 비디오 및 이미지 데이터의 비율에 상관없이 효율적으로 부하를 분산할 수 있습니다. 이 그림은 하이브리드 방식을 통해 계산 자원 활용도를 높이는 방법을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Load balancing with hybrid granularity.
> </details>



![](https://arxiv.org/html/2502.10248/extracted/6204622/figure/v2_training_loss.png)

> 🔼 이 그림은 Step-Video-T2V 데이터 처리 과정을 보여줍니다. 비디오 분할, 비디오 품질 평가, 비디오 모션 평가, 비디오 자막 생성, 비디오 개념 균형 및 비디오-텍스트 정렬의 6단계로 구성됩니다. 각 단계는 고품질 비디오-텍스트 쌍을 생성하는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: The pipeline of Step-Video-T2V data process.
> </details>



![](https://arxiv.org/html/2502.10248/x13.png)

> 🔼 그림 10은 논문에서 제시된 Step-Video-T2V 모델의 다양한 훈련 단계에 대한 손실 곡선을 보여줍니다.  각 훈련 단계(t2i-256px-s1, t2i-256px-s2, t2vi-192px-s1, t2vi-192px-s2, t2vi-192px-s3 등)에서 사용된 데이터셋은  s<sub>i</sub> 로 표시됩니다. 여기서 i는 데이터셋의 순서를 나타냅니다. 이 그래프는 각 훈련 단계에서의 손실 감소 추세를 보여주어, 데이터셋의 품질 향상과 모델 성능 개선 사이의 상관관계를 시각적으로 보여줍니다.  즉, 데이터셋 품질이 향상될수록 훈련 손실이 감소하는 것을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Training curve of different training stages, where sisubscript𝑠𝑖s_{i}italic_s start_POSTSUBSCRIPT italic_i end_POSTSUBSCRIPT denotes the it⁢hsuperscript𝑖𝑡ℎi^{th}italic_i start_POSTSUPERSCRIPT italic_t italic_h end_POSTSUPERSCRIPT dataset used in the corresponding stage.
> </details>



![](https://arxiv.org/html/2502.10248/x14.png)

> 🔼 그림 11은 Step-Video-T2V 모델의 사전 훈련 및 후속 훈련 과정에서 계층적으로 적용된 데이터 필터링 과정을 보여줍니다.  각 단계별로 다양한 필터링 기법(해상도 필터, 지속 시간 필터, CLIP 점수 필터, 모션 필터, 채도 필터, 흐릿함 필터, 미적 필터, 블랙 보더 필터, NSFW 필터, 워터마크 필터, 자막 필터, 개념 균형 필터, 소스 필터, 수동 필터 등)이 적용되어 데이터 품질을 향상시키고, 특정 기준에 부합하지 않는 데이터를 제거합니다. 각 필터링 단계는 이전 단계의 결과를 바탕으로 순차적으로 진행되며, 최종적으로는 고품질의 SFT(Supervised Fine-Tuning) 데이터셋을 생성하게 됩니다. 그림은 각 필터링 단계에서 제거된 데이터량과 남은 데이터량을 시각적으로 나타내어, 데이터 필터링 과정의 효율성과 효과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Hierarchical data filtering for pre-training and post-training.
> </details>



![](https://arxiv.org/html/2502.10248/x20.png)

> 🔼 이 그림은 논문에서 제시된 프롬프트 '영상 속에서 우아하고 자신감 있는 표정을 짓는 중국 소녀가 정교한 전통 의상을 입고 있습니다. 그녀는 '우리는 오픈 소스로 공개할 것입니다'라고 적힌 종이를 들고 있습니다. 배경은 고풍스럽고 우아한 분위기를 자아내며 소녀의 태도를 보완합니다. 전체 장면은 선명하고 사실적인 스타일을 가지고 있습니다.'를 기반으로 생성된 비디오의 네 프레임을 보여줍니다.  소녀의 의상, 표정, 배경 등이 자세하게 묘사되어 있으며, 비디오의 사실적인 시각 효과를 보여줍니다. 이 그림은 Step-Video-T2V 모델의 성능을 보여주는 예시 중 하나입니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Four frames sampled from the video generated based on the prompt 'In the video, a Chinese girl is dressed in an exquisite traditional outfit, smiling with a confident and graceful expression. She holds a piece of paper with the words 'we will open source' clearly written on it. The background features an ancient and elegant setting, complementing the girl’s demeanor. The entire scene is clear and has a realistic style.'.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| TP | CP | PP | VPP | Checkpointing (%) | MFU |
|---|---|---|---|---|---|---|
| 4 | 1 | 2 | 24 | 93.75 | 35.90 |
| 4 | 1 | 4 | 24 | 93.75 | 35.71 |
| 8 | 1 | 1 | 1 | 83.33 | 35.59 |
| 8 | 1 | 2 | 24 | 72.91 | 36.06 |
| 8 | 1 | 4 | 12 | 72.91 | 35.76 |
| 8 | 2 | 1 | 1 | 62.50 | 31.79 |
| 8 | 2 | 4 | 12 | 31.25 | 35.11 |
| 3 | 1 | 1 | 31.25 | 33.41 |  |
| 3 | 4 | 12 | 11.53 | 36.47 |  |{{< /table-caption >}}
> 🔼 표 2는 Step-Video-T2V의 540P 비디오 사전 학습 단계에서 다양한 병렬화 전략에 따른 모델 연산량 활용도(MFU)를 Step Emulator(SEMU)를 사용하여 추정한 결과를 보여줍니다.  각 행은 TP(Tensor Parallelism), CP(Context Parallelism), PP(Pipeline Parallelism), VPP(Virtual Pipeline Parallelism)와 체크포인팅 비율을 나타내며, 이러한 전략들의 조합에 따른 MFU 값을 보여줍니다.  이는 540P 고해상도 비디오 학습에 최적의 병렬 전략을 설정하기 위한 시뮬레이션 결과입니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Estimated MFU from SEMU of different parallelism strategies under 540P video pre-training stage.
> </details>

{{< table-caption >}}
| Resolution (F, H, W) | TFLOPs per sample |
|---|---| 
| 204 × 256 × 256 | 1,717.20 |
| 204 × 192 × 320 | 1,592.61 |
| 136 × 256 × 256 | 1,079.85 |
| 136 × 192 × 320 | 1,004.89 |
| 68 × 256 × 256 | 509.31 |
| 68 × 192 × 320 | 475.87 |
| 1 × 256 × 256 | 44.99 |{{< /table-caption >}}
> 🔼 표 3은 비디오의 해상도에 따른 샘플당 FLOPs(Floating Point Operations) 수를 보여줍니다.  즉,  비디오 생성 모델이 특정 해상도의 비디오를 처리하는 데 필요한 계산량을 나타냅니다.  다양한 해상도의 비디오를 처리하는 데 필요한 계산량이 얼마나 차이가 나는지 보여주는 표이며,  이러한 계산량의 차이는 비디오 생성 모델의 효율성과 처리 속도에 영향을 미칩니다.
> <details>
> <summary>read the caption</summary>
> Table 3: FLOPs per sample of different resolutions.
> </details>

{{< table-caption >}}
| Fault | Category | Count |
|---|---|---|
| GPU_DBE_ERROR | GPU | 3 |
| GPU_LOCKED | GPU | 1 |
| LINK_DOWN | Network | 1 |
| NODE_SHUTDOWN | Host | 2 |
| SOFTWARE_FAULT | Software | 11 |
| CUDA_OOM | Software | 7 |
| NON_FATAL | Hardware | 4 |{{< /table-caption >}}
> 🔼 표 4는 Step-Video-T2V 모델의 한 달간의 학습 과정에서 발생한 치명적인 하드웨어 오류의 횟수를 보여줍니다. 총 7번의 치명적인 오류만 발생했음을 보여주는 이 표는 시스템의 안정성과 견고성을 강조합니다. 표에는 오류 유형(GPU, 네트워크, 호스트, 소프트웨어 등)과 각 유형별 발생 횟수가 자세히 나열되어 있습니다. 이를 통해 시스템 관리자는 문제 해결 및 시스템 개선을 위한 정보를 얻을 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Over a month of Step-Video-T2V training, fatal hardware failures occurred only 7 times.
> </details>

{{< table-caption >}}
| Cause of Restart | Step-Video-T2V |  | LLaMA3.1 |  |
|---|---|---|---|---|
| Hardware | Hardware | Total Unexpected | Hardware | Total Unexpected |
| Avg Daily Restarts/1k GPUs | **0.037** | 0.095 | **0.422** | 0.485 |{{< /table-caption >}}
> 🔼 표 5는 Step-Video-T2V와 LLaMA 3.1 모델의 학습 중 하드웨어 재시작 횟수 통계를 보여줍니다.  '하드웨어 재시작'이란 하드웨어 오류로 인해 학습 작업이 중단되고 다시 시작된 경우를 의미하며, 모델 학습 안정성 및 시스템 안정성 지표로 사용됩니다. 표는 하루 동안 1,000개의 GPU당 발생한 하드웨어 재시작 횟수와 예상치 못한 재시작 횟수를 Step-Video-T2V와 LLaMA 3.1 모델에 대해 각각 비교하여 보여줍니다.  이를 통해 Step-Video-T2V 모델의 시스템 안정성 및 효율성을 객관적으로 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Restart count statistics during training for Step-Video-T2V and LLaMA3.1 .
> </details>

{{< table-caption >}}
| training stage | dataset | bs/node | learning rate | #iters | #seen samples |
|---|---|---|---|---|---| 
| Step-1: T2I Pre-training (256px) | O(1)B images | 40 | 1e-4 | 53k | 0.8B |
|  | O(1)B images | 40 | 1e-4 | 200k | 3B |
| **Total** |  |  | **253k** | **3.8B** |
| Step-2: T2VI Pre-training (192px) | O(1)B video clips | 4 | 6e-5 | 171k | 256M |
|  | O(100)M video clips | 4 | 6e-5 | 101k | 151M |
|  | O(100)M video clips | 4 | 6e-5 | 158k | 237M |
| **Total** |  |  | **430k** | **644M** |
| Step-2: T2VI Pre-training (540px) | O(100)M video clips | 2 | 2e-5 | 23k | 17.3M |
|  | O(10)M video clips | 2 | 1e-5 | 17k | 8.5M |
|  | O(1)M video clips | 1 | 1e-5 | 6k | 1.5M |
| **Total** |  |  | **46k** | **27.3M** |{{< /table-caption >}}
> 🔼 표 6은 Step-Video-T2V의 사전 훈련 세부 정보를 보여줍니다.  256px, 192px, 540px는 각각 256x256, 192x320, 544x992 해상도를 나타냅니다.  표에는 각 사전 훈련 단계(T2I, T2VI)에서 사용된 데이터셋의 종류, 노드당 배치 크기(bs/node), 학습률, 반복 횟수, 처리된 샘플 수 등의 정보가 포함되어 있습니다. 이를 통해 Step-Video-T2V 모델의 훈련 과정에 대한 자세한 내용을 이해할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Pre-training details of Step-Video-T2V. 256px, 192px, and 540px denote resolutions of 256x256, 192x320, and 544x992, respectively.
> </details>

{{< table-caption >}}
| Step-Video-T2V vs. HunyuanVideo (Win-Tie-Loss) | Annotator-1 | Annotator-2 | Annotator-3 |
|---|---|---|---|
| Overall | 59-22-47 | 46-47-35 | 54-41-33 |
| Sports | 6-3-3 | 5-5-2 | 6-6-0 |
| Food | 5-2-4 | 5-4-2 | 3-7-1 |
| Scenery | 5-3-4 | 2-9-1 | 7-1-4 |
| Animals | 6-0-6 | 3-6-3 | 2-7-3 |
| Festivals | 4-4-3 | 5-2-4 | 4-5-2 |
| Combined Concepts | 5-2-5 | 6-3-3 | 8-1-3 |
| Surreal | 4-2-5 | 5-2-4 | 6-2-3 |
| People | 6-2-4 | 3-4-5 | 5-2-5 |
| 3D Animation | 7-1-4 | 4-5-3 | 6-3-3 |
| Cinematography | 5-1-5 | 2-5-4 | 1-4-6 |
| Style | 6-2-4 | 6-2-4 | 6-3-3 |{{< /table-caption >}}
> 🔼 본 표는 Step-Video-T2V 모델과 HunyuanVideo 모델의 성능을 Metric-1을 사용하여 비교한 결과를 보여줍니다. Metric-1은 두 모델이 생성한 비디오 쌍에 대해 인간 평가자가 Step-Video-T2V가 더 나은지, HunyuanVideo가 더 나은지, 아니면 비슷한지를 판단하는 방식입니다. 표에는 다양한 카테고리(예: 스포츠, 음식, 풍경 등)에 대한 각 모델의 승/무/패 횟수가 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Comparison with HunyuanVideo using Metric-1.
> </details>

{{< table-caption >}}
| Step-Video-T2V vs. HunyuanVideo | Instruction Following | Motion Smoothness | Physical Plausibility | Aesthetic Appeal |
|---|---|---|---|---|
| Overall | 1,273-1,221 | 1,407-1,327 | 1,417-1,238 | 1,312-1,238 |
| Sports | 130-111 | 120-104 | 113-99 | 110-98 |
| Food | 85-92 | 110-97 | 107-93 | 111-90 |
| Scenery | 130-129 | 139-126 | 134-120 | 125-122 |
| Animals | 104-106 | 123-114 | 110-107 | 99-108 |
| Festivals | 102-91 | 110-102 | 97-90 | 103-94 |
| Combined Concepts | 132-115 | 139-136 | 139-135 | 118-115 |
| Surreal | 99-101 | 138-139 | 135-134 | 125-126 |
| People | 115-117 | 129-129 | 148-150 | 115-112 |
| 3D Animation | 113-109 | 137-133 | 149-146 | 139-135 |
| Cinematography | 121-117 | 121-122 | 132-133 | 116-115 |
| Style | 142-133 | 141-125 | 153-134 | 151-123 |{{< /table-caption >}}
> 🔼 이 표는 Step-Video-T2V 모델과 HunyuanVideo 모델의 성능을 비교 분석한 결과를 보여줍니다. Metric-2 지표를 사용하여 Instruction Following, Motion Smoothness, Physical Plausibility, Aesthetic Appeal 네 가지 평가 기준으로 각 비디오를 평가했습니다. 세 명의 인간 평가자가 각 비디오에 점수를 매겼으며, 각 범주와 평가 기준에 대해 모든 평가자의 점수를 집계하여 표에 나타냈습니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Comparison with HunyuanVideo using Metric-2. We invited three human annotators to evaluate each video. For each category and evaluation dimension, we aggregated the scores given by all annotators across all prompts within the category for that dimension.
> </details>

{{< table-caption >}}
| Step-Video-T2V vs. T2VTopA (Win-Tie-Loss) | Annotator-1 | Annotator-2 | Annotator-3 |
|---|---|---|---|
| Overall | 44-13-69 | 41-13-72 | 46-25-55 |
| Sports | 6-2-4 | 7-0-5 | 7-3-2 |
| Food | 5-2-4 | 6-1-4 | 4-2-5 |
| Scenery | 1-0-10 | 4-0-7 | 1-2-8 |
| Animals | 1-3-8 | 1-3-8 | 3-1-8 |
| Festivals | 6-2-3 | 7-2-2 | 5-3-3 |
| Combined Concepts | 2-0-10 | 1-3-8 | 8-0-4 |
| Surreal | 4-1-6 | 3-2-6 | 4-2-5 |
| People | 2-1-8 | 2-1-8 | 6-1-4 |
| 3D Animation | 6-0-6 | 3-0-9 | 5-3-4 |
| Cinematography | 5-1-5 | 4-1-6 | 1-3-7 |
| Style | 6-1-5 | 3-0-9 | 2-5-5 |{{< /table-caption >}}
> 🔼 이 표는 Step-Video-T2V 모델의 성능을 평가하기 위해 사용된 벤치마크인 Step-Video-T2V-Eval 데이터셋을 기반으로, Step-Video-T2V와 중국 내 주요 두 개의 상용 텍스트-비디오 생성 엔진인 T2VTopA와 T2VTopB의 성능을 Metric-1을 사용하여 비교 분석한 결과를 보여줍니다. Metric-1은 인간 평가자들이 Step-Video-T2V와 비교 모델이 생성한 비디오 쌍에 대해 Step-Video-T2V가 더 우수한지, 동등한지, 또는 열등한지를 판단하는 방식입니다. 총 128개의 프롬프트 중 T2VTopA가 2개의 프롬프트를 처리하지 못하여 실제로는 126개의 프롬프트에 대한 평가 결과가 제시되어 있습니다. 각 프롬프트에 대한 비디오 비교 결과를 바탕으로 세 명의 인간 평가자의 의견을 종합하여 Step-Video-T2V의 상대적 성능을 측정합니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Comparison with T2VTopA using Metric-1. A total of 126 prompts were evaluated, rather than 128, as T2VTopA rejected 2 prompts.
> </details>

{{< table-caption >}}
| Step-Video-T2V vs. T2VTopB (Win-Tie-Loss) | Annotator-1 | Annotator-2 | Annotator-3 |
|---|---|---|---|
| Overall | 36-35-51 | 67-10-45 | 55-22-45 |
| Sports | 8-2-2 | 10-1-1 | 8-2-2 |
| Food | 3-4-3 | 7-1-2 | 7-2-1 |
| Scenery | 2-6-4 | 5-2-5 | 5-4-3 |
| Animals | 5-1-5 | 3-1-7 | 2-2-7 |
| Festivals | 6-1-4 | 6-0-5 | 2-4-5 |
| Combined Concepts | 1-4-7 | 6-1-5 | 4-2-6 |
| Surreal | 2-0-6 | 3-0-5 | 2-1-5 |
| People | 1-3-7 | 4-1-6 | 3-1-7 |
| 3D Animation | 5-3-4 | 11-0-1 | 11-0-1 |
| Cinematography | 3-3-5 | 4-2-5 | 3-1-7 |
| Style | 0-8-4 | 8-1-3 | 8-3-1 |{{< /table-caption >}}
> 🔼 표 10은 Step-Video-T2V 모델과 T2VTopB 모델의 성능을 Metric-1을 사용하여 비교한 결과를 보여줍니다.  총 128개의 프롬프트 중 T2VTopB가 6개의 프롬프트를 처리하지 못하여 실제로는 122개의 프롬프트에 대한 비교 분석이 수행되었음을 의미합니다.  각 평가자별 Step-Video-T2V 모델이 T2VTopB 모델보다 우수한(Win), 동등한(Tie), 열등한(Loss) 결과를 개수로 나타내어 모델 간의 성능 차이를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Comparison with T2VTopB using Metric-1. A total of 122 prompts were evaluated, rather than 128, as T2VTopB rejected 6 prompts.
> </details>

{{< table-caption >}}
| Annotator | Model | Instruction Following | Motion Smoothness | Physical Plausibility | Aesthetic Appeal |
|---|---|---|---|---|---| 
| Annotator-1 | Step-Video-T2V | 204 | 210 | 203 | 187 |
|  | T2VTopA | 211 | 200 | 198 | 196 |
|  | T2VTopB | 185 | 184 | 178 | 175 |
| Annotator-2 | Step-Video-T2V | 211 | 243 | 256 | 217 |
|  | T2VTopA | 241 | 243 | 242 | 228 |
|  | T2VTopB | 234 | 236 | 229 | 204 |
| Annotator-3 | Step-Video-T2V | 170 | 197 | 172 | 178 |
|  | T2VTopA | 177 | 177 | 153 | 171 |
|  | T2VTopB | 164 | 163 | 139 | 148 |
| Annotator-4 | Step-Video-T2V | 199 | 232 | 230 | 225 |
|  | T2VTopA | 217 | 221 | 201 | 199 |
|  | T2VTopB | 194 | 219 | 194 | 194 |
| Annotator-5 | Step-Video-T2V | 218 | 225 | 213 | 211 |
|  | T2VTopA | 221 | 220 | 213 | 212 |
|  | T2VTopB | 209 | 217 | 202 | 196 |
| Annotator-6 | Step-Video-T2V | 187 | 213 | 251 | 211 |
|  | T2VTopA | 193 | 201 | 259 | 197 |
|  | T2VTopB | 201 | 224 | 271 | 227 |{{< /table-caption >}}
> 🔼 표 11은 Step-Video-T2V 모델과 중국 내 두 개의 주요 상용 텍스트-비디오 생성 엔진인 T2VTopA와 T2VTopB의 성능을 비교한 것입니다. 6명의 인간 평가자가 각 비디오의 품질을 평가했고, 각 평가 차원(Instruction Following, Motion Smoothness, Physical Plausibility, Aesthetic Appeal)에 대한 점수를 집계하여 모델 간 성능을 비교했습니다. 어떤 모델에서도 거부된 프롬프트는 분석에서 제외했습니다.
> <details>
> <summary>read the caption</summary>
> Table 11: Comparison with T2VTopA and T2VTopB using Metric-2. We invited six human annotators to evaluate each video. For each evaluation dimension, we aggregated the scores given by each annotator across all prompts for that dimension. Prompts that were rejected by any model were excluded from the analysis for all models.
> </details>

{{< table-caption >}}
| Category | Step-Video-T2V vs. Movie Gen Video (Win-Tie-Loss) | Step-Video-T2V vs. HunyuanVideo (Win-Tie-Loss) | # of Prompts |
|---|---|---|---| 
| Overall | 485-315-489 | 615-313-361 | 1,289 |
| human | 123-58-160 | 181-64-96 | 341 |
| physics | 61-54-64 | 87-47-45 | 179 |
| unusual activity & subject | 110-74-108 | 136-75-81 | 292 |
| animal | 39-37-42 | 47-30-41 | 118 |
| scene | 84-53-63 | 91-58-51 | 200 |
| sequential motion | 9-2-2 | 6-2-5 | 13 |
| camera motion | 59-37-50 | 67-37-42 | 146 |{{< /table-caption >}}
> 🔼 표 12는 Movie Gen Video 벤치마크를 사용하여 Movie Gen Video와 HunyuanVideo의 성능을 비교한 결과를 보여줍니다.  일부 프롬프트가 여러 카테고리 태그를 가지고 있기 때문에 평가 횟수(1,289회)가 1,003회보다 많습니다. 이 평가에는 6명의 인간 평가자가 참여했습니다.  표는 각 카테고리별로 Movie Gen Video와 HunyuanVideo의 성능 차이를 Win/Tie/Loss 형태로 나타내고 있으며, 각 카테고리별 평가에 사용된 프롬프트 수도 함께 제시합니다.  이를 통해, 각 모델의 강점과 약점을 카테고리별로 비교 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 12: Comparison of Movie Gen Video and HunyuanVideo using the Movie Gen Video Bench. The total number of evaluations (1,289) is greater than 1,003 due to some prompts having multiple category tags. This evaluation involved six human annotators.
> </details>

{{< table-caption >}}
| Model | Downsample Factor | SSIM↑ | PSNR↑ | rFVD↓ |
|---|---|---|---|---|
| OpenSora-1.2 (Zheng et al. (2024)) | 4 × 8 × 8 | 0.9126 | 31.41 | 20.42 |
| CogvideoX-1.5 (Yang et al. (2024a)) | 4 × 8 × 8 | 0.9373 | 38.10 | 16.33 |
| HunyuanVideo (Kong et al. (2025)) | 4 × 8 × 8 | 0.9710 | 39.56 | 4.17 |
| Cosmos-VAE (Nvidia (2025)) | 4 × 8 × 8 | 0.9315 | 37.66 | 9.10 |
| Cosmos-VAE (Nvidia (2025)) | 8 × 16 × 16 | 0.8862 | 34.82 | 40.33 |
| Video-VAE (Ours) | 8 × 16 × 16 | 0.9776 | 39.37 | 3.61 |{{< /table-caption >}}
> 🔼 본 표는 Step-Video-T2V 모델에서 사용된 Video-VAE의 영상 재구성 성능을 보여줍니다. 다양한 비율로 다운샘플링된 여러 오픈소스 기반 모델들과 비교하여, Video-VAE가 압도적으로 높은 SSIM, PSNR 점수와 낮은 rFVD 점수를 기록함을 보여줍니다. 특히 8x16x16의 높은 압축률에서도 우수한 재구성 품질을 유지하는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 13: Comparison of reconstruction metrics.
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