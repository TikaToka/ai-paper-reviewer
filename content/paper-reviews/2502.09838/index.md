---
title: "HealthGPT: A Medical Large Vision-Language Model for Unifying Comprehension and Generation via Heterogeneous Knowledge Adaptation"
summary: "HealthGPT는 이종 지식 적응을 통한 의료 영상-언어 모델링의 통합을 구현, 의료 영상 이해 및 생성 성능을 크게 향상시켰습니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Vision-Language Models", "🏢 Peking University",]
showSummary: true
date: 2025-02-14
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.09838 {{< /keyword >}}
{{< keyword icon="writer" >}} Tianwei Lin et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-19 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.09838" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.09838" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/healthgpt-a-medical-large-vision-language" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

의료 분야는 방대한 양의 **비정형 데이터** (의료 영상, 텍스트 보고서 등)를 포함하고 있으며, 이를 효과적으로 처리하고 활용하는 기술이 중요합니다.  하지만, 기존의 의료 영상-언어 모델들은 데이터 부족과 이해와 생성 간의 상충 문제로 인해 성능이 제한적이었습니다. 이러한 문제는 **의료 영상 분석 및 진단 도구의 정확성과 효율성을 저해**하는 요인이 됩니다. 

본 논문은 **의료 영상 이해와 생성 작업을 통합**하는 새로운 의료 영상-언어 모델, HealthGPT를 제시합니다.  **이종 지식 적응 기법 (H-LORA)과 계층적 시각적 지각 방법론**을 통해 의료 영상 데이터의 제한을 극복하고 이해와 생성 간의 충돌을 완화했습니다. HealthGPT는 다양한 의료 영상 분석 작업에서 **기존 모델들을 능가하는 성능**을 보였으며, **새로운 의료 영상 분석 및 진단 도구 개발**에 기여할 수 있습니다.  또한, 본 연구는 **새로운 학습 데이터셋 VL-Health**도 공개하여, 후속 연구에 기여할 수 있습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} HealthGPT는 의료 영상 이해와 생성 작업을 통합하는 최초의 통합 프레임워크를 제시합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} H-LoRA는 데이터 충돌 문제를 효과적으로 완화하여 의료 영상 이해 및 생성 작업의 성능을 향상시킵니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} VL-Health 데이터셋은 의료 영상 이해와 생성 작업 모두에 대한 종합적인 학습 데이터를 제공합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**의료 영상-언어 모델링 분야의 연구자들에게 중요한 논문**입니다. 의료 데이터의 제한 및 이해와 생성 간의 상충 문제를 해결하기 위한 새로운 방법론을 제시하며, **의료 영상 분석 및 진단 도구 개발에 혁신적인 전기를 마련**할 수 있습니다. 특히, **의료 영상 데이터를 효과적으로 활용**하여 의료 서비스 질 향상 및 의료 혁신에 기여할 수 있는 가능성을 제시합니다. 또한, 본 연구에서 제시된 **새로운 방법론은 다른 의료 영상 분석 분야**에도 적용될 수 있으며, **추가적인 연구를 위한 새로운 가능성**을 제시합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.09838/x2.png)

> 🔼 그림 1은 HealthGPT가 다양한 의료 관련 과제에서 최첨단 통합 비주얼 모델 및 의료 특화 모델을 능가하는 의료 다중 모드 이해 및 생성 기능을 지원함을 보여줍니다. 복잡한 의료 관련 과제를 해결하는 HealthGPT의 뛰어난 능력을 강조합니다. Comp.Perf. 와 Gen.Perf. 는 각각 이해 및 생성 작업의 결과를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: HealthGPT enables medical multi-modal comprehension and generation, outperforming both state-of-the-art unified visual models and medical-specific models across various tasks. This highlights its superior capability in tackling complex tasks in healthcare applications. Comp.Perf. and Gen.Perf. denote the results of comprehension and generation.
> </details>





{{< table-caption >}}
| Type | Model | # Params | Medical LVLM | VQA-RAD ↑ |  | SLAKE ↑ |  | PathVQA ↑ |  | MMMU -Med ↑ | OMVQA ↑ | Avg. ↑ |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Comp. Only | Med-Flamingo | 8.3B | ✓ | 58.6 | 43.0 | 47.0 | 25.5 | 61.9 | 31.3 | 28.7 | 34.9 | 41.4 |
|  | LLaVA-Med | 7B | ✓ | 60.2 | 48.1 | 58.4 | 44.8 | 62.3 | 35.7 | 30.0 | 41.3 | 47.6 |
|  | HuatuoGPT-Vision | 7B | ✓ | 66.9 | 53.0 | 59.8 | 49.1 | 52.9 | 32.0 | 42.0 | 50.0 | 50.7 |
|  | BLIP-2 | 6.7B | ✗ | 43.4 | 36.8 | 41.6 | 35.3 | 48.5 | 28.8 | 27.3 | 26.9 | 36.1 |
|  | LLaVA-v1.5 | 7B | ✗ | 51.8 | 42.8 | 37.1 | 37.7 | 53.5 | 31.4 | 32.7 | 44.7 | 41.5 |
|  | InstructBLIP | 7B | ✗ | 61.0 | 44.8 | 66.8 | 43.3 | 56.0 | 32.3 | 25.3 | 29.0 | 44.8 |
|  | Yi-VL | 6B | ✗ | 52.6 | 42.1 | 52.4 | 38.4 | 54.9 | 30.9 | 38.0 | 50.2 | 44.9 |
|  | InternVL2 | 8B | ✗ | 64.9 | 49.0 | 66.6 | 50.1 | 60.0 | 31.9 | 43.3 | 54.5 | 52.5 |
|  | Llama-3.2 | 11B | ✗ | 68.9 | 45.5 | 72.4 | 52.1 | 62.8 | 33.6 | 39.3 | 63.2 | 54.7 |
| Comp. & Gen. | Show-o | 1.3B | ✗ | 50.6 | 33.9 | 31.5 | 17.9 | 52.9 | 28.2 | 22.7 | 45.7 | 42.6 |
|  | Unified-IO 2 | 7B | ✗ | 46.2 | 32.6 | 35.9 | 21.9 | 52.5 | 27.0 | 25.3 | 33.0 | 33.8 |
|  | Janus | 1.3B | ✗ | 70.9 | 52.8 | 34.7 | 26.9 | 51.9 | 27.9 | 30.0 | 26.8 | 33.5 |
|  | HealthGPT-M3 | 3.8B | ✓ | 73.7 | 55.9 | 74.6 | 56.4 | 78.7 | 39.7 | 43.3 | 68.5 | 61.3 |
|  | HealthGPT-L14 | 14B | ✓ | 77.7 | 58.3 | 76.4 | 64.5 | 85.9 | 44.4 | 49.2 | 74.4 | 66.4 |{{< /table-caption >}}

> 🔼 표 1은 의료 영상 이해 작업에서 HealthGPT의 성능을 다른 대규모 비전-언어 모델(LVLM) 및 통합 다중 모드 모델과 비교한 표입니다. 이 표는 다양한 의료 영상 이해 작업(VQA-RAD, SLAKE, PathVQA, MMMU-Med, OMVQA)에서 각 모델의 성능을 정량적으로 비교하여 HealthGPT의 우수성을 보여줍니다.  굵은 밑줄은 최고 성능과 두 번째로 높은 성능을 나타냅니다.  의료 영상 질문 답변, 의료 보고서 생성과 같은 특정 의료 영상 이해 과제에서 HealthGPT가 다른 모델보다 뛰어난 성능을 보이는지 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparison of HealthGPT with other LVLMs and unified multi-modal models on medical visual comprehension tasks. Bold and underlined text indicates the best performance and second-best performance, respectively.
> </details>





### In-depth insights


#### Med-LVLM Unification
의료 분야에서 대규모 비전-언어 모델(Med-LVLM)의 통합은 **의료 영상 이해와 생성을 하나의 프레임워크로 통합**함으로써 의료 서비스 향상에 획기적인 발전을 가져올 수 있습니다.  이를 통해 질병 진단의 정확도 향상, 효율적인 치료 계획 수립, 환자와 의료진 간의 소통 개선 등 다양한 이점을 기대할 수 있습니다.  **이미지 인식 및 자연어 처리 기술을 결합**하여 의료 영상 분석, 보고서 생성, 질의응답 등 다양한 작업을 수행할 수 있는 **다기능 모델 개발**이 중요하며, 이는 방대한 의료 데이터의 효율적인 활용과 새로운 의료 기술 발전으로 이어질 것입니다.  하지만 **데이터의 부족과 질적 편차, 그리고 모델의 해석 가능성 확보** 등 해결해야 할 과제도 있습니다.  **데이터 프라이버시 및 보안 문제** 또한 중요한 고려 사항이며, 이러한 어려움들을 극복하기 위한 노력이 필수적입니다.

#### H-LoRA Adaptation
본 논문에서 제시된 H-LoRA(Heterogeneous Low-Rank Adaptation)는 **이종의 지식을 효율적으로 적응시키는 새로운 매개변수 효율적인 미세 조정 기법**입니다. 기존의 LoRA가 단일 작업에 초점을 맞춘 반면, H-LORA는 **이해와 생성이라는 두 가지 상이한 작업을 동시에 처리**하도록 설계되었습니다. 이는 의료 영상 이해 및 생성 작업에서 발생하는 데이터 충돌 문제를 해결하기 위해 고안되었습니다. **각 작업에 특화된 하위 모듈을 독립적으로 학습**시켜 상호 간섭을 최소화하고, **저차원 어댑터 매트릭스를 사용**하여 매개변수 수를 줄이며 효율성을 높였습니다. 또한, **계층적 시각적 인식 기법**을 활용하여 작업의 특성에 맞는 시각적 정보를 선택적으로 사용합니다.  **다단계 학습 전략**을 통해 각 단계별로 최적화된 학습을 진행하며, **의료 영상 데이터의 제한적인 규모**를 고려하여 적은 양의 데이터로도 효과적인 학습을 가능하게 합니다.  결론적으로 H-LORA는 의료 분야의 다양한 시각 언어 모델에 적용 가능하며, **의료 영상 이해 및 생성 작업의 성능 향상**에 크게 기여할 것으로 기대됩니다.

#### Visual Perception
본 논문에서 시각적 지각(Visual Perception)에 대한 논의는 주로 **의료 영상 데이터를 효과적으로 처리하고 이해하는 방법**에 초점을 맞춥니다.  단순히 이미지를 입력받는 것을 넘어,  **계층적 시각적 지각(Hierarchical Visual Perception)**을 통해 다양한 해상도의 시각 정보를 추출하여, 이해(comprehension)와 생성(generation)이라는 상이한 과제에 적합한 정보를 제공하는 전략을 제시합니다.  **저해상도의 추상적인 정보는 이해 작업에, 고해상도의 구체적인 정보는 생성 작업에 각각 활용**됨으로써, 상충되는 요구사항을 효과적으로 해결합니다.  이러한 접근 방식은 **의료 영상의 다양한 특징을 고려하여**  정확하고 효율적인 모델 학습을 가능하게 합니다.  즉, 시각적 지각은 단순한 이미지 처리 단계를 넘어,  **의료 영상 분석의 핵심적인 구성 요소**로 자리매김하며,  HealthGPT 모델의 성능 향상에 중요한 역할을 수행합니다.  특히, **다양한 의료 영상 모드** (X-ray, CT, MRI 등) 에 대한 **일관된 표현 학습**을 가능하게 합니다.

#### Dataset & Training
본 논문에서 제시된 의료 영상-언어 모델(Med-LVLM)의 훈련을 위해 **VL-Health라는 대규모 데이터셋**을 구축했습니다. 이 데이터셋은 다양한 의료 영상 모달리티(X선, CT, MRI, 초음파 등)와 관련된 의료 문헌 및 보고서를 포함하여, **이미지 이해 및 생성 작업 모두를 위한 충분한 데이터**를 제공합니다.  **데이터셋의 다양성과 품질**은 모델의 성능에 큰 영향을 미치기 때문에, 다양한 질병 유형과 해상도의 이미지를 포함하고, 정확한 주석을 달아 신뢰성을 높였습니다.  **세 단계의 훈련 과정**을 통해 모델을 효율적으로 학습시켰습니다. 첫 번째 단계에서는 다양한 작업에 대한 지식을 통합하고, 두 번째 단계에서는 이질적인 지식을 효율적으로 활용하는 **H-LORA(Heterogeneous Low-Rank Adaptation)** 기법을 적용하여 개별 작업 간의 충돌을 완화했습니다. 마지막 단계에서는 미세 조정을 통해 하위 작업에 대한 모델의 성능을 향상시켰습니다.  **H-LORA의 효율성**은 데이터셋의 제약에도 불구하고, 뛰어난 성능을 달성하는데 크게 기여했습니다.

#### Future Med-LLMs
미래 의료 대규모 언어 모델(Med-LLMs)은 **의료 영상 분석 및 질병 진단의 정확성과 효율성을 크게 향상시킬 것**으로 예상됩니다.  **다양한 의료 데이터(영상, 텍스트, 생체 신호 등)를 통합적으로 학습**하여 질병 진단, 치료 계획 수립, 환자 관리 등에 활용될 수 있습니다.  그러나, **의료 데이터의 개인정보 보호 및 윤리적 문제**는 신중하게 고려되어야 하며, **모델의 설명 가능성 및 신뢰성 확보**를 위한 연구가 필수적입니다.  또한, **의료 전문가와의 협력**을 통해 실제 임상 환경에서 Med-LLMs의 유용성을 검증하고, 지속적인 개선을 위한 노력이 필요합니다.  **의료 분야의 특수성을 고려한 데이터셋 구축 및 모델 개발**이 중요하며, **다국어 지원 및 다양한 의료 시스템과의 호환성**을 확보하는 방향으로 발전해야 합니다.  궁극적으로, Med-LLMs는 **의료 서비스의 접근성과 질을 개선**하고, **의료 전문가의 업무 부담을 줄이며, 환자의 삶의 질 향상**에 기여할 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.09838/extracted/6211206/fig/HealthGPT_Framework.png)

> 🔼 이 그림은 이해(generation) 데이터의 양을 고정하고 다른 유형의 데이터 비율을 높일 경우 성능이 크게 저하됨을 보여줍니다.  즉,  이해와 생성 작업을 동시에 학습시키는 모델에서 한쪽 데이터만 많이 사용하면 다른 쪽 작업의 성능이 떨어진다는 것을 시각적으로 보여줍니다.  이러한 현상은 자동 회귀 방식의 다중 모드 학습에서 이해와 생성 작업 간의 불일치로 인해 발생합니다. 이해 작업은 시각적 세부 사항을 무시하고 추상적인 정보에 집중하는 반면, 생성 작업은 세부적인 시각 정보를 유지해야 하기 때문입니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: With a fixed amount of comprehension (generation) data, increasing the proportion of the other type leads to significant performance degradation.
> </details>



![](https://arxiv.org/html/2502.09838/x3.png)

> 🔼 그림 3은 HealthGPT의 아키텍처를 보여줍니다. HealthGPT는 계층적 시각적 지각(hierarchical visual perception)과 이종 저순위 적응(H-LORA)을 통합하여, 작업별 하드 라우터(task-specific hard router)를 사용하여 시각적 특징과 H-LORA 플러그인을 선택하고, 최종적으로 자기회귀 방식(autoregressive manner)으로 출력을 생성합니다.  계층적 시각적 지각은 ViT(Vision Transformer)를 사용하여 이미지를 여러 계층의 시각적 토큰(visual tokens)으로 변환하여, 이해(comprehension) 작업에는 추상적인 시각적 특징을, 생성(generation) 작업에는 구체적인 시각적 특징을 사용합니다.  H-LORA는 이해 및 생성 작업에 대한 지식을 별도의 모듈에 저장하고, 작업에 관련된 지식을 추출하기 위해 동적으로 라우팅합니다.  자동 회귀적 방식은 입력을 순차적으로 처리하여 출력을 생성하는 방식을 의미하며, 이미지 생성의 경우 VQGAN(Vector Quantized-GAN) 디코더가 사용됩니다. 이 그림은 HealthGPT의 주요 구성 요소와 그들의 상호작용을 시각적으로 보여주어, 모델의 작동 원리를 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: The HealthGPT architecture integrates hierarchical visual perception and H-LoRA, employing a task-specific hard router to select visual features and H-LoRA plugins, ultimately generating outputs with an autoregressive manner.
> </details>



![](https://arxiv.org/html/2502.09838/x4.png)

> 🔼 그림 4는 논문에서 사용된 VL-Health 데이터셋의 통계를 보여줍니다.  (a)는 다양한 의료 영상 유형 (예: 안저 사진, OCT, 엑스레이, 현미경 사진, 초음파, CT, MRI)별 데이터 수를 나타내는 막대 그래프입니다.  각 유형에 대해, 이해(comprehension)와 생성(generation) 작업에 사용된 데이터의 수량이 표시되어 있습니다. (b)는 각 작업 유형(이해 및 생성 작업)에 사용된 데이터셋의 원본을 보여주는 막대 그래프입니다. 데이터셋은 특정 작업에 초점을 맞춰 구성되었으며, VL-Health 데이터셋이 의료 영상 이해 및 생성 작업 모두를 위한 다양하고 포괄적인 데이터를 제공함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Data statistics of VL-Health.
> </details>



![](https://arxiv.org/html/2502.09838/x5.png)

> 🔼 그림 5는 다양한 순위 설정에서 LoRA, MoELoRA 및 H-LoRA의 성능을 비교한 것입니다. 서로 다른 순위 크기에서 세 가지 방법의 성능을 보여주는 여러 그래프가 포함되어 있을 것으로 예상됩니다. 이 그림은 H-LoRA가 다양한 작업에서 다른 두 방법보다 우수한 성능을 보여줌을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Performance comparison of LoRA, MoELoRA, and H-LoRA under different rank settings.
> </details>



![](https://arxiv.org/html/2502.09838/x6.png)

> 🔼 그림 6은 서로 다른 시각적 인식에 따른 손실 시각화(a)와 성능 비교(b)를 보여줍니다. (a)는 다양한 시각적 특징을 사용했을 때의 손실 변화를 보여주는 그래프이고, (b)는 해당 시각적 특징을 사용했을 때의 성능 변화를 보여주는 그래프입니다. 이를 통해, 과제(이해 또는 생성)에 따라 서로 다른 계층의 시각적 특징을 사용하는 것이 효율적임을 보여줍니다.  구체적으로, 추상적인 시각적 특징은 이해 과제에, 구체적인 시각적 특징은 생성 과제에 더 효과적임을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6:  The loss visualization (a) and performance comparison (b) with respect to different visual perceptions.
> </details>



![](https://arxiv.org/html/2502.09838/x7.png)

> 🔼 그림 7은 서로 다른 지시어에 따른 보고서-흉부 X선 사진 변환 결과를 보여줍니다. (a)는 정상적인 흉부 X선 사진을 비교를 위해 보여줍니다. (b)와 (c)는 심각도와 영향을 받는 부위가 다른 생성된 사례들을 보여줍니다. 낙서로 표시된 부분은 비정상적인 상태를 나타냅니다. 이 그림은 HealthGPT 모델이 다양한 수준의 폐렴을 가진 환자의 흉부 X선 사진을 생성할 수 있음을 보여줍니다. 생성된 이미지는 정상적인 흉부 X선 사진과 비교하여 폐렴의 심각도와 위치를 명확하게 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Case study of report-to-CXR under different instructions. (a) shows a normal CXR image for comparison. (b) and (c) illustrate generated cases with varying severity and affected regions. The graffiti areas indicate abnormal conditions.
> </details>



![](https://arxiv.org/html/2502.09838/x8.png)

> 🔼 그림 8은 논문에서 사용된 VL-Health 데이터셋의 구성을 보여줍니다. (a)는 다양한 의료 영상 질의응답(VQA) 데이터셋에서 수집된 이미지와 질문-답변 쌍의 개수를 보여주는 막대 그래프입니다.  여기에는 VQA-RAD, SLAKE, PathVQA, MIMIC-CXR-VQA, LLaVA-Med, PubMedVision 등 다양한 데이터셋이 포함됩니다. 각 막대는 특정 데이터셋에서 사용된 이미지 또는 질문-답변 쌍의 수를 나타냅니다. (b)는 초해상도, 변환, 재구성 작업을 위해 사용된 이미지 데이터의 수를 보여줍니다. IXI, MIMIC-CHEST-XRAY, LLaVA-558k, SynthRAD2023 등의 데이터셋이 사용되었으며, 각 막대는 특정 작업과 관련된 이미지 데이터의 수를 나타냅니다. 이 그림은 VL-Health 데이터셋이 다양한 의료 영상 데이터와 작업을 포괄적으로 다루고 있음을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: VL-Health dataset collection distribution.
> </details>



![](https://arxiv.org/html/2502.09838/x9.png)

> 🔼 그림 9는 HealthGPT 모델 학습의 세 단계 중 두 번째 단계(Heterogeneous H-LoRA Plugin Adaptation) 전후의 성능 변화를 보여줍니다.  두 번째 단계는 서로 다른 작업(이미지 이해 및 생성)을 위한 H-LORA 플러그인을 통합하여 모델의 기반을 강화하는 단계입니다.  그래프는 이미지 이해(Comp.) 및 이미지 생성(Gen.) 작업에 대한 성능 향상을 보여주며, 두 번째 단계를 거친 후 두 작업 모두에서 성능이 향상되었음을 나타냅니다.  특히,  이 단계는 작업 간의 충돌을 완화하여 안정적인 성능 향상을 가져온다는 점을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Performance changes before and after the stage-2.
> </details>



![](https://arxiv.org/html/2502.09838/extracted/6211206/fig/MT.png)

> 🔼 그림 10은 인간 평가자들이 각 모델의 응답 중 가장 우수한 응답으로 선택한 비율과, 인간 평가에 사용된 데이터셋을 보여줍니다. (a)는 다양한 모델들의 응답에 대한 인간 평가자들의 선호도를 보여주는 비율 그래프입니다.  각 모델의 응답에 대해 평가자들이 가장 우수한 응답으로 얼마나 자주 선택했는지를 백분율로 나타냅니다. (b)는 이러한 인간 평가에 사용된 데이터셋에 대한 설명입니다.  이를 통해 본 연구의 결과가 실제 의료 전문가들의 판단과 얼마나 일치하는지 확인하고, 모델 성능의 신뢰도를 높입니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: (a) Proportion of model responses selected as the best in human evaluation. (b) Human Evaluation Dataset.
> </details>



![](https://arxiv.org/html/2502.09838/extracted/6211206/fig/SR_CASE.png)

> 🔼 그림 11은 의료 영상 변환(modality transfer)의 사례를 보여줍니다.  CT 영상을 MRI 영상으로, MRI 영상을 CT 영상으로 변환하는 결과를 보여주는 여러 이미지 쌍이 나열되어 있습니다. 각 이미지 쌍에는 원본 영상(GT), HealthGPT 모델이 생성한 영상(Pred), 그리고 두 영상의 차이를 시각적으로 비교할 수 있도록 배치되어 있습니다. 이 그림은 HealthGPT 모델이 다양한 영역(뇌, 골반 등)에서  CT와 MRI 영상 간의 변환을 정확하게 수행할 수 있음을 보여주는 증거입니다.  각 영상의 세부적인 부분까지 정확하게 변환되는 것을 확인할 수 있으며, HealthGPT 모델의 우수한 성능을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Case of modality transfer.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | CT to MRI (Brain) |  |  | CT to MRI (Pelvis) |  |  | MRI to CT (Brain) |  |  | MRI to CT (Pelvis) |  |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|  | SSIM ↑ | PSNR ↑ | MSE ↓ | SSIM ↑ | PSNR ↑ | MSE ↓ | SSIM ↑ | PSNR ↑ | MSE ↓ | SSIM ↑ | PSNR ↑ | MSE ↓ |
| pix2pix | 71.09 | 32.65 | 36.85 | 59.17 | 31.02 | 51.91 | 78.79 | 33.85 | 28.33 | 72.31 | 32.98 | 36.19 |
| CycleGAN | 54.76 | 32.23 | 40.56 | 54.54 | 30.77 | 55.00 | 63.75 | 31.02 | 52.78 | 50.54 | 29.89 | 67.78 |
| BBDM | 71.69 | 32.91 | 34.44 | 57.37 | 31.37 | 48.06 | 86.40 | 34.12 | 26.61 | 79.26 | 33.15 | 33.60 |
| Vmanba | 69.54 | 32.67 | 36.42 | 63.01 | 31.47 | 46.99 | 79.63 | 34.12 | 26.49 | 77.45 | 33.53 | 31.85 |
| DiffMa | 71.47 | 32.74 | 35.77 | 62.56 | 31.43 | 47.38 | 79.00 | 34.13 | 26.45 | 78.53 | 33.68 | 30.51 |
| HealthGPT-M3 | 79.38 | 33.03 | 33.48 | 71.81 | 31.83 | 43.45 | 85.06 | 34.40 | 25.49 | 84.23 | 34.29 | 27.99 |
| HealthGPT-L14 | 79.73 | 33.10 | 32.96 | 71.92 | 31.87 | 43.09 | 85.31 | 34.29 | 26.20 | 84.96 | 34.14 | 28.13 |{{< /table-caption >}}
> 🔼 표 2는 논문에서 제시된 네 가지 의료 영상 변환 작업(CT에서 MRI로, MRI에서 CT로의 변환, 각각 뇌와 골반 영역)에 대한 실험 결과를 보여줍니다. 각 작업에 대해 SSIM, PSNR, MSE 지표가 제시되어 모델 성능을 평가합니다. 이 표는 다양한 영상 변환 모델들의 성능을 비교 분석하는 데 사용되며, HealthGPT 모델의 우수성을 보여주는 근거가 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 2: The experimental results for the four modality conversion tasks.
> </details>

{{< table-caption >}}
| Model | SSIM ↑ | PSNR ↑ | MSE ↓ | LPIPS ↓ |
|---|---|---|---|---|
| SRGAN | 71.34 | 32.01 | 41.27 | 24.50 |
| DASR | 71.57 | 32.34 | 38.25 | 19.17 |
| Real-ESRGAN | 67.30 | 31.87 | 42.57 | 20.64 |
| LIIF | 73.27 | 32.13 | 40.14 | 22.93 |
| BSRGAN | 69.97 | 31.97 | 41.52 | 28.72 |
| HealthGPT-M3 | 78.19 | 32.76 | 34.47 | 12.02 |
| HealthGPT-L14 | 77.94 | 32.71 | 35.19 | 12.43 |{{< /table-caption >}}
> 🔼 표 3은 초고해상도 작업에 대한 실험 결과를 보여줍니다.  SRGAN, DASR, Real-ESRGAN, LIIF, BSRGAN 및 HealthGPT 모델의 SSIM, PSNR, MSE 및 LPIPS 지표를 비교하여 HealthGPT 모델이 다른 모델들보다 우수한 성능을 보임을 보여줍니다. 특히, HealthGPT-M3 와 HealthGPT-L14 모델은 다른 모델들에 비해 MSE가 현저하게 낮고 SSIM과 PSNR이 높아 이미지 품질 개선에 효과적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Comparison results of super-resolution task.
> </details>

{{< table-caption >}}
| Model | VQA-RAD | VQA-RAD | SLAKE | SLAKE | PathVQA | PathVQA | MMMU-Med | OMVQA | RECOM | MTRANS | SR | Training Time |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| HealthGPT w/ +LoRA | 71.3 | **57.2** | **70.0** | **53.4** | **76.4** | **38.6** | **41.30** | **65.10** | 62.67 | **59.99** | 65.88 | **1.00 ×** |
| HealthGPT w/ +MoELoRA | **72.5** | **57.2** | 66.4 | 52.4 | 73.2 | 36.0 | 39.30 | 64.90 | **67.31** | 59.76 | **65.91** | **1.49 ×** |
| HealthGPT w/ +H-LoRA | **73.7** | **55.9** | **74.6** | **56.4** | **78.7** | **39.7** | **43.30** | **68.50** | 67.69 | **60.30** | **66.14** | **1.00 ×** |{{< /table-caption >}}
> 🔼 표 4는 의료 영상 이해 및 생성 작업에서 LoRA, MoELORA(n=4), H-LoRA(n=4)의 성능 및 속도 차이를 보여줍니다.  의료 영상 이해(VQA-RAD, SLAKE, PathVQA, OMVQA, MMMU)와 생성(RECOM, MTRANS, SR) 작업 모두에 대한 결과가 제시되어 있으며, 각 모델의 성능과 LoRA 기반 모델 학습에 필요한 시간이 비교되어 있습니다. 이 표를 통해 H-LoRA가 다른 LoRA 기반 방법들보다 효율적인 동시에 우수한 성능을 보임을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: We present the performance and speed differences of LoRA, MoELoRA (n=4), and H-LoRA (n=4) on medical visual comprehension and generation tasks.
> </details>

{{< table-caption >}}
| Training Strategy | VQA-RAD | VQA-RAD | SLAKE | SLAKE | PathVQA | PathVQA | Comp. | Gen. | CT | CT | MRI | MRI |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---| 
|  | close | all | close | all | close | all | MMMU-Med | OMVQA | Brain | Pelvis | Brain | Pelvis |
| Mixed-Training | 56.6 | 37.9 | 45.0 | 32.9 | 65.7 | 33.6 | **44.0** | 48.9 | 65.64 | 62.75 | 56.61 | 50.77 |
| HealthGPT w/ 3-stage-Training | **72.5** | **55.2** | **77.9** | **59.6** | **79.7** | **49.0** | 42.7 | **68.5** | **70.84** | **72.99** | **65.26** | **61.33** |{{< /table-caption >}}
> 🔼 이 표는 논문의 H-LoRA 기반 3단계 학습 전략과 혼합 학습 방식의 성능을 비교 분석한 결과를 보여줍니다.  구체적으로, 다양한 의료 영상 이해 및 생성 작업(VQA-RAD, SLAKE, PathVQA, MMMU-Med, OMVQA, CT, MRI 등)에 대한 두 가지 학습 방법의 성능 지표(예: 정확도, F1 점수 등)를 비교하여 각 방법의 효율성과 장단점을 제시합니다.  3단계 학습 전략이 혼합 학습 방식보다 더 나은 성능을 보이는지, 그리고 어떤 작업에서 더 큰 성능 향상을 보이는지 등을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Comparison between the H-LoRA-based Three-Stage Learning Strategy and the mixed-training approach.
> </details>

{{< table-caption >}}
| Model | ViT | Adapter | MLP-dims | Model dims | LLM | Params | Vocab Size | H-LoRA Rank |
|---|---|---|---|---|---|---|---|---|
| HealthGPT-M3 | CLIP-L/14 | 2-layer MLP | 1024 | 3072 | Phi-3-mini | 3.8B | 40206 | 16(Comp.), 64(Gen.) |
| HealthGPT-L14 | CLIP-L/14 | 2-layer MLP | 1024 | 5120 | Phi-4 | 14B | 108547 | 8(Comp.), 32(Gen.) |{{< /table-caption >}}
> 🔼 표 6은 HealthGPT 모델의 구성 요소에 대한 개요를 보여줍니다.  HealthGPT 모델은 크게 Vision Transformer (ViT), Adapter, Multi-Layer Perceptron (MLP), 그리고 Large Language Model (LLM) 의 네 가지 주요 구성 요소로 이루어져 있습니다.  각 구성 요소는 모델의 입력을 처리하고 최종 출력을 생성하는 데 중요한 역할을 합니다.  이 표에서는 각 구성 요소의 유형, 차원, 파라미터 수, 어휘 크기 등 세부 정보를 제공하여 HealthGPT 모델의 구조를 보다 명확하게 이해하는 데 도움을 줍니다. 특히 HealthGPT 모델의 두 가지 버전인 HealthGPT-M3과 HealthGPT-L14의 사양 차이를 비교하여 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Overview of the Components of HealthGPT.
> </details>

{{< table-caption >}}
|                       | HealthGPT-M3                      |                       | HealthGPT-L14                      |
| :-------------------- | :---------------------------------- | :-------------------- | :---------------------------------- |
|                       | Stage-1             | Stage-2             | Stage-3             | Stage-1             | Stage-2             | Stage-3             |
|                       | Comp. | Gen. | Comp. | Gen. | Comp. | Gen. | Comp. | Gen. | Comp. | Gen. | Comp. | Gen. |
| Hyperparameter         |                       |                       |                       |                       |                       |                       |
| Optimizer             | AdamW                 | AdamW                 | AdamW                 | AdamW                 | AdamW                 | AdamW                 |
| Adapter LR           | 1e-3                  | 2e-5                  | 2e-5                  | 2e-5                  | 2e-5                  | 2e-5                  |
| Learning Rate        | /                     | 2e-4                  | 2e-4                  | 2e-4                  | /                     | 1e-4                  | 2e-4                  | 2e-4                  |
| Global Batch Size    | 256                   | 64                    | 32                    | 128                   | 64                    | 256                   | 64                    | 32                    | 128                   | 64                    |
| Weight Decay         | 0                     | 0                     | 0                     | 0                     | 0                     | 0                     |
| Dropout Rate         | 0                     | 0.05                  | 0.05                  | 0.05                  | 0                     | 0.05                  | 0.05                  | 0.05                  |
| LR Scheduler         | Warm Up               | Constant               | Warm Up               | Warm Up               | Constant               | Warm Up               |
| Max Sequence Length   | 2048                  | 2048                  | 2048                  | 2048                  | 2048                  | 2048                  |{{< /table-caption >}}
> 🔼 표 7은 HealthGPT 모델의 세 가지 단계별 학습 과정에서 사용된 하이퍼파라미터 설정을 보여줍니다. 각 단계(1단계, 2단계, 3단계)별로 최적화 알고리즘, 어댑터 학습률, 학습률, 전역 배치 크기, 가중치 감쇠, 드롭아웃 비율, 학습률 스케줄러, 최대 시퀀스 길이, 웜업 단계 등의 하이퍼파라미터 값을 제시하여 모델 학습의 효율성과 최종 성능에 미치는 영향을 자세히 설명합니다. HealthGPT-M3과 HealthGPT-L14 모델에 대한 설정을 각각 구분하여 보여주는 것이 특징입니다.  특히, 각 단계별 하이퍼파라미터 설정이 다르게 제시된 이유도 함께 설명하고 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Overview of Hyperparameter Configurations.
> </details>

{{< table-caption >}}
| Medical Task | Stage-1 | Stage-2 |
|---|---|---|
| Comp. | LLaVA-558k, PubMedVision-PT | Mixed-47k |
| Gen. | LLaVA-558k | Mixed-47k |
| Medical Task | Stage-3 |
|---|---| 
| Comp. | LLaVA_Med, MIMIC_CXR_VQA, PubMedVision-FT, LLaVA-665k, PathVQA, SLAKE, VQA-RAD |
| Gen. | IXI, SynthRAD2023, MIMIC-CHEST-XRAY |{{< /table-caption >}}
> 🔼 표 8은 논문에서 제시된 VL-Health 데이터셋의 구성을 보여줍니다. 세 단계 학습 전략(three-stage learning strategy)에 따라 데이터셋이 어떻게 나뉘어 사용되는지 보여주는 표입니다.  1단계에서는 LLaVA-558k와 PubMedVision-PT 데이터셋이 모두 사용되고, 2단계에서는 LLaVA-558k가 생성 태스크에 사용됩니다. 3단계에서는 다양한 의료 영상 데이터셋(LLaVA Med, MIMIC-CXR-VQA, PubMedVision-FT, LLaVA-665k, PathVQA, SLAKE, VQA-RAD)이 이해(comprehension) 태스크에, IXI, SynthRAD2023, MIMIC-CHEST-XRAY 데이터셋이 생성(generation) 태스크에 사용됨을 보여줍니다.  즉, 각 단계별로 사용되는 데이터셋과 태스크(이해/생성) 유형을 명확히 제시하여 데이터셋의 구성과 학습 전략을 쉽게 이해하도록 돕습니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Data distribution of VL-Health in three-stage learning strategy.
> </details>

{{< table-caption >}}
| Type | Model | # Params | Medical LVLM | CT | X-ray | FDM | MiS | OCT | MRI | USS | Avg. |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Comp. Only | Med-Flamingo | 8.3B | ✓ | 30.1 | 33.9 | 25.5 | 37.0 | 60.0 | 27.6 | 30.4 | 34.9 |
|  | LLaVA-Med | 7B | ✓ | 28.4 | 32.8 | 42.7 | 31.6 | 55.3 | 45.0 | 53.6 | 41.3 |
|  | HuatuoGPT-Vision | 7B | ✓ | 35.3 | 41.5 | 51.4 | 62.3 | 59.3 | 40.4 | 60.1 | 50.0 |
|  | BLIP-2 | 6.7B | ✗ | 26.6 | 29.1 | 22.3 | 36.9 | 29.1 | 22.7 | 21.4 | 26.9 |
|  | LLaVA-v1.5 | 7B | ✗ | 28.0 | 55.7 | 35.5 | 42.1 | 49.2 | 52.9 | 49.7 | 44.7 |
|  | InstructBLIP | 7B | ✗ | 20.1 | 22.2 | 34.1 | 30.6 | 38.6 | 31.9 | 25.5 | 29.0 |
|  | Yi-VL | 6B | ✗ | 51.2 | 47.1 | 27.7 | 62.6 | 67.6 | 55.0 | 40.3 | 50.2 |
|  | InternVL2 | 8B | ✗ | 40.2 | 57.9 | 53.2 | 64.0 | 59.1 | 58.1 | 49.1 | 54.5 |
|  | Llama-3.2 | 11B | ✗ | 37.6 | 55.2 | 71.4 | 82.1 | 62.5 | 65.2 | 68.6 | 63.2 |
| Comp. & Gen. | Show-o | 1.3B | ✗ | 29.0 | 50.4 | 30.9 | 22.0 | 30.8 | 34.2 | 33.8 | 33.0 |
|  | Unified-IO 2 | 7B | ✗ | 10.8 | 37.7 | 12.3 | 25.3 | 32.6 | 30.9 | 37.7 | 26.8 |
|  | Janus | 1.3B | ✗ | 24.9 | 54.8 | 35.9 | 62.7 | 54.2 | 50.7 | 36.8 | 45.7 |
|  | HealthGPT-M3 | 3.8B | ✓ | 35.3 | 81.9 | 54.6 | 88.2 | 89.3 | 78.5 | 51.4 | 68.5 |
|  | HealthGPT-L14 | 14B | ✓ | 39.0 | 86.6 | 64.1 | 88.6 | 99.7 | 80.9 | 62.2 | 74.4 |{{< /table-caption >}}
> 🔼 표 9는 OmniMedVQA 벤치마크에 대한 성능 비교 결과를 보여줍니다.  OmniMedVQA는 다양한 의료 영상 데이터셋에서 수집된 다양한 유형의 의료 이미지와 질문 답변 쌍으로 구성된 대규모 의료 영상 질의응답 벤치마크입니다. 이 표는 다양한 모델(Med-Flamingo, LLaVA-Med, HuatuoGPT-Vision, BLIP-2, LLaVA-v1.5, InstructBLIP, Yi-VL, InternVL2, Llama-3.2, Show-o, Unified-IO 2, Janus, HealthGPT-M3, HealthGPT-L14)의 OmniMedVQA 벤치마크에서의 성능을 비교 분석하여 각 모델의 장단점과 우수성을 보여줍니다.  각 모델의 매개변수 수, 지원하는 의료 영상 모달리티(CT, X-ray, FDM, MIS, OCT, MRI, USS), 그리고 각 모달리티별 성능 점수(평균 점수 포함)를 비교하여 HealthGPT 모델의 우수성을 보여주는 표입니다. 특히, HealthGPT-M3과 HealthGPT-L14 모델의 높은 정확도가 강조됩니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Performance comparison of OmniMedVQA Benchmark.
> </details>

{{< table-caption >}}
| Model | Comp. | Gen. | Time (n=2) | Comp. | Gen. | Time (n=4) | Comp. | Gen. | Time (n=8) | Comp. | Gen. | Time (n=32) |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| +MoELoRA | 50.3 | 62.98 | 1.22× | 50.0 | 64.33 | 1.49× | 50.8 | 63.71 | 2.09× | / | / | 5.81× |
| HealthGPT w/ +H-LoRA | 51.5 | 63.48 | 0.99× | 52.8 | 64.71 | 1.00× | 53.6 | 64.98 | 0.99× | 53.5 | 64.74 | 1.01× |{{< /table-caption >}}
> 🔼 이 표는 다양한 수의 LoRA 전문가를 사용하여 MoELoRA와 H-LoRA의 성능을 비교 분석한 결과를 보여줍니다.  LoRA 전문가의 수(n)가 증가함에 따라 MoELoRA의 훈련 시간이 크게 증가하는 반면, H-LORA는 추가적인 훈련 시간 지연 없이 성능이 향상됨을 보여줍니다. 특히, n=32일 때 MoELoRA는 훈련을 완료할 수 없었던 반면, H-LORA는 훈련을 완료하고 성능 향상을 보였습니다. 이는 부록 B절에서 분석한 내용과 일치하며, 대규모 작업에서 H-LORA의 효율성을 입증합니다.
> <details>
> <summary>read the caption</summary>
> Table 10: We explored the performance of MoELoRA and H-LoRA with different numbers of LoRA experts. At n=32𝑛32n=32italic_n = 32, MoELoRA was unable to complete training.
> </details>

{{< table-caption >}}
| Model | CT(Brain) |  |  | CT(Pelvis) |  |  | MRI (Brain) |  |  | MRI(Pelvis) |  |  |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
|  | SSIM ↑ | PSNR ↑ | MSE ↓ | SSIM ↑ | PSNR ↑ | MSE ↓ | SSIM ↑ | PSNR ↑ | MSE ↓ | SSIM ↑ | PSNR ↑ | MSE ↓ |
| SEED-X | 20.18 | 27.66 | 112.11 | 21.53 | 28.02 | 102.87 | 4.90 | 27.62 | 112.86 | 6.31 | 27.89 | 106.21 |
| Unified-IO 2 | 83.93 | 36.09 | 17.95 | 85.36 | 35.10 | 25.46 | 87.50 | 34.25 | 25.47 | 86.31 | 33.53 | 29.80 |
| HealthGPT-M3 | 91.73 | 36.42 | 15.46 | 94.26 | 37.30 | 12.53 | 88.76 | 33.97 | 27.05 | 84.40 | 33.11 | 32.62 |{{< /table-caption >}}
> 🔼 표 11은 뇌와 골반 영역에 대한 CT에서 MRI로, MRI에서 CT로의 변환 작업을 포함한 네 가지 모달리티 변환 작업에 대한 실험 결과를 보여줍니다.  각 작업에 대해 SSIM, PSNR, MSE 지표가 제시되어 있으며, HealthGPT-M3 모델과 다른 기존 방법들의 성능을 비교 분석하여 HealthGPT 모델의 우수성을 보여줍니다.  뇌와 골반 영역을 구분하여 제시함으로써 해당 모델의 신체 부위별 성능 차이를 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 11: The experimental results for the four reconstruction tasks.
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