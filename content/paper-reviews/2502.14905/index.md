---
title: "Think Inside the JSON: Reinforcement Strategy for Strict LLM Schema Adherence"
summary: "ThinkJSON: 제한된 리소스로도 엄격한 스키마 준수를 달성하는 효율적인 강화 학습 기반 LLM 스키마 준수 전략"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 MasterControl AI Research",]
showSummary: true
date: 2025-02-18
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.14905 {{< /keyword >}}
{{< keyword icon="writer" >}} Bhavik Agarwal et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-24 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.14905" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.14905" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

많은 최신 자연어 모델(LLM)은 구조화된 출력(예: JSON) 생성에 어려움을 겪습니다. 즉, 생성된 출력이 요구되는 스키마와 정확하게 일치하지 않을 수 있습니다. 이는 특히 규제가 엄격한 분야(예: 바이오 제조)에서 심각한 문제를 야기할 수 있습니다. 기존 방법(예: 감독 학습, 강화 학습)은 리소스 소모가 많거나 성능이 제한적입니다. 

본 논문에서는 **ThinkJSON이라는 새로운 접근 방식**을 제시합니다. ThinkJSON은 합성 데이터를 사용하여 LLM의 추론 능력을 향상시키는 강화 학습 기반 프레임워크입니다.  **소규모 모델(1.5B 매개변수)**을 사용하여 엄격한 스키마 준수를 달성하며, 기존 방법보다 효율적입니다. 실험 결과는 ThinkJSON이 기존 방법보다 **뛰어난 스키마 준수 성능**을 보임을 보여줍니다. 이는 특히 제한된 리소스 환경에서 **실용적인 스키마 기반 텍스트 생성**을 가능하게 합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 합성 데이터와 반복 LLM 추론을 활용한 새로운 스키마 준수 전략 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 제한된 리소스(1.5B 매개변수 모델)에서도 강력한 스키마 준수 성능 입증 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 실제 응용 프로그램에서의 효율성과 실용성을 보여주는 실험 결과 제시 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **제한된 리소스를 사용하여 엄격한 스키마 준수를 강화하는 효율적인 방법**을 제시함으로써, 규제가 엄격한 바이오 제조 분야를 포함한 다양한 분야의 연구자들에게 중요한 의미를 가집니다. **합성 데이터 생성 및 반복적인 LLM 추론을 활용하는 독창적인 접근 방식**은 스키마 기반 텍스트 생성에 대한 새로운 연구 방향을 제시하고, 향후 연구를 위한 다양한 가능성을 열어줍니다. 또한, 본 연구는 **실용적인 응용 프로그램**을 보여주는 실험 결과를 제시함으로써, 학계와 산업계 모두에 실질적인 영향을 미칠 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.14905/extracted/6211719/image3.png)

> 🔼 이 그림은 논문의 'Think Inside the JSON' 파이프라인을 보여줍니다. 합성 JSON 데이터 생성, R1-Zero 모델의 강화 학습, JSON 필드 매핑을 위한 추론, 그리고 추론을 활용한 SFT(Supervised Fine-Tuning) 향상 등의 단계를 시각적으로 나타냅니다.  각 단계는 데이터 생성에 사용된 모델(Qwen 14B/32B), 강화 학습에 사용된 모델과 보상(Qwen 2.5 1.5B, GRPO, 사용자 지정 보상), 추론 및 SFT 향상에 사용된 모델(DeepSeek R1 Qwen 32B) 등 세부 정보와 함께 제시됩니다. 최종적으로 성능이 향상된 R1 모델을 생성하는 과정을 한눈에 보여주는 흐름도입니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: ”Think inside the JSON” pipeline
> </details>







### In-depth insights


#### Strict Schema LLM
**엄격한 스키마 준수를 강조하는 대형 언어 모델(LLM)**은 구조화된 데이터 생성의 정확성과 신뢰성을 높이는 데 중점을 둡니다. 이는 특히 규제가 엄격한 바이오 제조와 같은 분야에서 필수적입니다. 이 논문에서는 **합성 데이터를 활용한 강화 학습 및 지도 학습 미세 조정 기법**을 통해 LLM이 엄격한 스키마를 준수하도록 하는 전략을 제시합니다. 이는 효율적인 리소스 활용과 실제 애플리케이션에서의 성능 향상에 기여하며, **생성된 출력의 신뢰성 및 규정 준수를 보장**합니다. 핵심은 모델의 추론 능력을 강화하여 스키마 일관성을 유지하는 데 있습니다.  **제약 기반 디코딩 및 프롬프트 엔지니어링 기법**과의 비교를 통해 이 접근 방식의 실용성을 입증하며, 특히 제한된 리소스 환경에서 효과적임을 보여줍니다.

#### RL & SFT Training
본 논문에서 제시된 강화학습(RL) 및 미세조정(SFT) 전략은 **정확하고 효율적인 구조화된 텍스트 생성**을 위한 핵심입니다. RL 단계는 합성 데이터셋을 사용하여 **모델의 추론 능력을 강화**하고, 사용자 정의 보상 함수를 통해 **스키마 준수에 대한 인식을 향상**시킵니다. 이는 제한된 자원으로도 **높은 수준의 스키마 준수 성능**을 달성하는 데 중요합니다.  SFT 단계에서는 **추론 데이터셋을 활용**하여 RL로 학습된 모델을 미세 조정함으로써, **실제 응용 분야에 대한 적합성을 높이고 스키마 준수 성능을 더욱 향상**시킵니다.  **소규모 기반 모델을 사용**하여 효율성을 높였으며, **다양한 보상 함수를 통합**하여 여러 측면(형식 정확성, 콘텐츠 정확성)을 동시에 최적화합니다. 이러한 접근 방식은 제약 산업과 같은 엄격한 규정 준수가 필요한 분야에서 특히 유용하며, **비용 효율적이고 견고한 구조화된 텍스트 생성**을 가능하게 합니다.

#### ThinkJSON Pipeline
ThinkJSON 파이프라인은 **구조화된 데이터 생성을 위한 강력한 솔루션**을 제시합니다.  기존의 LLM 방식의 한계를 극복하고자 **강화학습(RL)**과 **미세조정(SFT)**을 결합하여 **정확하고 효율적인 JSON 생성**을 목표로 합니다.  **합성 데이터셋을 활용**하여 RL 학습을 진행, 모델의 추론 능력을 향상시키고, 이후 SFT를 통해 실제 데이터에 대한 적응력을 높여 정확도를 개선합니다.  **사용자 정의 보상 함수**를 통해 구조적 일관성을 강화하고, **제약 기반 디코딩**을 통해 JSON 형식의 완벽한 준수를 보장합니다.  **자원 효율성**이 뛰어나 경량화된 모델에서도 효과적으로 작동하며, 까다로운 규제 산업 분야에서의 요구사항을 충족합니다.  전반적으로, ThinkJSON은 **실용적이고 효과적인 LLM 기반 구조화된 텍스트 생성 프레임워크**임을 시사합니다.

#### Reasoning Dataset
본 논문에서 제시된 추론 데이터셋은 **합성 데이터**를 사용하여 **비정형 텍스트를 JSON 스키마에 매핑하는 과정**을 설명하는 데 초점을 맞추고 있습니다.  이를 통해 LLM이 스키마에 정확하게 부합하는 구조화된 출력물을 생성하는 능력을 향상시키는 데 도움이 되는 **지도 학습 및 강화 학습**에 활용될 수 있습니다. 특히, **단계별 추론 과정을 명시적으로 설명**하도록 설계되어 있어 모델의 추론 과정을 이해하는 데 유용합니다.  **다양한 텍스트 형식과 레이아웃**을 포함하고 있으며, 이는 모델의 **일관성과 견고성**을 평가하는 데 도움이 됩니다.  **합성 데이터의 사용**은 실제 데이터셋 구축에 필요한 비용과 시간을 절약하고, **데이터 편향** 문제를 줄이는 데 기여할 수 있지만, **실제 데이터와의 차이**로 인한 성능 저하 가능성을 고려해야 합니다.  **다양한 복잡도**의 JSON 스키마를 포함하는 것이 중요하며, 이를 통해 모델의 일반화 능력을 향상시킬 수 있습니다.

#### Future Directions
본 연구는 제약 산업 규정 준수를 위한 구조적 데이터 생성에 초점을 맞춘 강화 학습 기반 접근 방식을 제시합니다. **향후 연구 방향으로는 대규모 언어 모델(LLM)의 용량 확장을 통한 더욱 풍부한 맥락 이해 및 드문 경우나 도메인 특유의 복잡성 처리 개선**을 고려할 수 있습니다.  또한, **다양한 리워드 함수를 통합하여 모델의 성능을 향상시키는 방안**도 있습니다. 특히, **실제 산업 환경에서의 적용성을 높이기 위해 다양한 데이터 유형 및 형식을 처리하는 모델의 확장성 및 일반화 능력 개선**에 중점을 둘 수 있습니다.  **규제 준수를 위한 감사 및 검증 프로세스와의 통합** 또한 중요한 과제입니다. 마지막으로, **본 연구에서 개발한 방법론의 효율성 및 확장성을 평가하기 위한 보다 광범위하고 포괄적인 실험적 연구**가 필요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.14905/extracted/6211719/image1.png)

> 🔼 이 그림은 GRPO(Group Relative Policy Optimization) 훈련 과정에서 네 가지 주요 지표(completion length, reward, equation reward function, format reward function)의 훈련 메트릭을 보여줍니다. 각 지표는 훈련 반복 횟수에 따른 변화를 그래프로 나타내어, GRPO 알고리즘이 모델의 성능 향상에 미치는 영향을 시각적으로 보여줍니다.  그래프의 형태는 각 지표의 변화 추세를 파악하는 데 도움을 주며, GRPO 알고리즘의 효과를 평가하는 데 사용될 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: GRPO Training Metrics
> </details>



![](https://arxiv.org/html/2502.14905/extracted/6211719/image4.png)

> 🔼 그림 3은 본 논문의 3.4절 '지도 학습 미세 조정(Supervised Fine-Tuning)' 파트에서 설명하는 내용을 보여주는 그래프입니다.  구체적으로, 미세 조정 과정에서의 손실(loss), 학습률(learning rate), 그래디언트 놈(grad norm), 에폭(epoch) 등의 지표 변화를 나타내는 네 개의 그래프가 포함되어 있으며,  SFT(Supervised Fine-Tuning) 모델 학습의 진행 상황과 성능을 시각적으로 보여줍니다.  각 그래프의 x축은 학습 단계(global step 또는 epoch)를, y축은 해당 지표의 값을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: SFT Training Metrics
> </details>



![](https://arxiv.org/html/2502.14905/extracted/6211719/image2.png)

> 🔼 그림 4는 다섯 가지 모델(ThinkJSON, 원본 DeepSeek R1, DeepSeek R1의 양자화 버전 두 가지, Gemini 2.0 Flash)의 성능을 비교한 표입니다.  각 모델은 구조화된 데이터 추출 벤치마크에서 6,500개의 행을 처리하여 유효한 JSON 객체를 생성했는지 평가되었습니다.  평가 지표는 JSON 객체가 생성되지 않은 행의 수, 구문적으로 유효한 JSON 객체의 수, 필드 매핑의 정확도 평균, 추출된 JSON 내의 추가 또는 잘못된 토큰의 평균 비율을 포함합니다. ThinkJSON은 가장 높은 필드 매핑 정확도와 가장 낮은 노이즈 비율을 보여주는 반면, 다른 모델들은 다양한 정도의 성능을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Performance Comparison
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
{{< /gallery >}}