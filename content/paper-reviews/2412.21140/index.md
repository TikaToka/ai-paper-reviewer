---
title: "Facilitating large language model Russian adaptation with Learned Embedding Propagation"
summary: "LEP(Learned Embedding Propagation)는 적은 양의 학습 데이터만으로도 다국어 대규모 언어 모델을 효율적으로 적응시키는 새로운 기법입니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Lomonosov Moscow State University",]
showSummary: true
date: 2024-12-30
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.21140 {{< /keyword >}}
{{< keyword icon="writer" >}} Mikhail Tikhomirov et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-31 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.21140" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.21140" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/facilitating-large-language-model-russian" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

최근 대규모 언어 모델(LLM)의 발전은 놀라운 성과를 가져왔지만, 특정 모델에만 접근 가능한 폐쇄적인 데이터셋과 높은 계산 비용이 연구 확산을 제한하는 문제점이 있었습니다.  **본 연구는 이러한 문제점을 해결하기 위해, 새로운 언어 지식을 기존의 LLM에 효율적으로 통합하는 LEP(Learned Embedding Propagation) 기법을 제안합니다.**



LEP는 기존 LLM의 지식을 최대한 활용하여 새로운 언어 데이터를 추가 학습하는 방식으로, 기존 LLM의 성능을 저하시키지 않고 언어 적응력을 향상시키는 데 중점을 둡니다.  **본 연구에서는 LEP를 LLaMa-3-8B와 Mistral-7B 모델에 적용하여 러시아어 적응을 시도하였고,  경쟁력 있는 성능을 달성함으로써 LEP의 효율성과 효과를 입증했습니다.** 또한, 러시아어 적응을 위한 새로운 평가 기준인 Darumeru 벤치마크를 개발하여 객관적인 평가를 가능하게 하였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} LEP는 기존의 언어 특화 지시어 미세 조정 방식보다 효율적인 대안을 제시합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} LEP는 경쟁력 있는 성능을 달성하여 기존의 대규모 언어 모델의 성능 기준을 유지하거나 능가합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} Darumeru 벤치마크는 러시아어 적응 평가를 위한 새로운 기준을 제공합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**본 논문은 저자원 언어 적응을 위한 효율적인 방법을 제시하여 연구자들이 다양한 언어 모델을 보다 쉽게 적용할 수 있도록 함으로써, 자연어 처리 분야의 연구 발전에 크게 기여할 수 있습니다.**  **특히, 제한된 양질의 데이터로 언어 모델을 빠르게 적응시키는 방법을 제시하여, 계산 비용을 절감하고 연구 효율성을 높일 수 있습니다.**  **또한, 제시된 방법은 기존의 언어 모델 지식을 최대한 활용하면서 새로운 언어 지식을 통합하는 방식으로, 기존 모델의 성능을 저해하지 않으면서 언어 적응력을 향상시킬 수 있습니다.**

------
#### Visual Insights



![](https://arxiv.org/html/2412.21140/extracted/6098179/image31.png)

> 🔼 그림 1은 제안된 러시아어 적응 방법의 성능을 Darumeru 벤치마크를 사용하여 비교한 것입니다.  각 막대는 특정 모델(LLaMa-3-8B 또는 Mistral-7B)과 러시아어 적응 방법(LEP, LEP + 보정, 지속적인 지시 미세 조정)을 사용한 결과를 보여줍니다.  비교 대상으로 OpenChat 3.5 및 기타 관련 모델의 결과도 함께 표시되어 제안된 방법의 성능을 평가하는 데 도움이 됩니다.  그림은 다양한 러시아어 어휘 적응 시나리오에서 LEP의 경쟁력 있는 성능을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Performance comparison of proposed adaptation method on Darumeru benchmark
> </details>





{{< table-caption >}}
| Model | Micro-Avg | DaruMMLU | DaruMERA | DaruSum | DaruCopy (EN) | DaruCopy (RU) |
|---|---|---|---|---|---|---|
| Openchat 3.5 (Mistral-7B) | 0,607 | 0,543 | 0,526 | 0,322 | 0,999 | 0,917 |
| LLaMa-3-8B (Instruct) | 0,610 | 0,571 | 0,510 | 0,322 | 1,000 | 0,972 |
| Saiga (LLaMa-3-8B) | 0,608 | 0,574 | 0,514 | 0,320 | 0,995 | 0,939 |
| Vikhr-5.2 (Mistral-7B) | 0,587 | 0,494 | 0,573 | 0,308 | 0,959 | 0,693 |
| Qwen-2 7B | 0,613 | 0,624 | 0,548 | 0,300 | 0,938 | 0,842 |
| Mistral Nemo (12B) | 0,639 | 0,592 | 0,576 | 0,320 | 0,998 | 0,924 |
| Ours |  |  |  |  |  |  |
| Openchat 3.5 + LEP-Extended + calibration (best) | 0,632<sup>↑</sup> | 0,541 | 0,563<sup>↑</sup> | 0,321 | 1,000 | 0,989<sup>↑</sup> |
| LLaMa-3-8B (Instruct) + LEP-Extended + calibration (best) | 0,618<sup>↑</sup> | 0,565<sup>↓</sup> | 0,521<sup>↑</sup> | 0,339<sup>↑</sup> | 1,000 | 0,984<sup>↑</sup> |{{< /table-caption >}}

> 🔼 표 1은 다양한 오픈소스 지시 조정형 대규모 언어 모델(LLM)에 대한 Darumeru 제로샷 평가 결과를 보여줍니다.  Darumeru는 러시아어 적응을 위해 특별히 고안된 새로운 벤치마크이며, 다양한 러시아어 데이터셋을 사용하여 모델의 텍스트 생성 강건성을 평가합니다. 표에는 Openchat 3.5, LLaMa-3-8B(Instruct), Saiga, Vikhr-5.2, Qwen-2 7B, Mistral Nemo 등 여러 모델의 Micro-Avg(평균 정확도), DaruMMLU, DaruMERA, DaruSum, DaruCopy(EN), DaruCopy(RU) 점수가 포함되어 있습니다. 이는 모델의 다양한 언어 이해 및 텍스트 생성 능력을 보여주는 다양한 지표입니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Darumeru zero-shot evaluation results for popular open-source instruct-tuned models.
> </details>





### In-depth insights


#### LEP for LLM Adaptation
이 논문은 **LEP(Learned Embedding Propagation)**라는 새로운 방법을 제시하여 대규모 언어 모델(LLM)의 언어 적응 비용을 줄이는 데 중점을 둡니다.  기존의 LLM 언어 적응 방법은 고품질의 지시 조정 데이터가 필요하지만, LEP는 기존 LLM의 지식을 최소한으로 방해하면서 새로운 언어 지식을 직접 통합하는 혁신적인 임베딩 전파 기술을 활용하여 이러한 한계를 극복합니다.  **LEP의 주요 장점은 훈련 데이터 요구 사항이 적고 기존 LLM 지식에 대한 영향이 최소화된다는 점**입니다.  연구 결과, LEP는 다양한 어휘 적응 시나리오에서 경쟁력 있는 성능을 달성하며, 추가적인 지시 조정 단계를 통해 성능이 더 향상될 수 있음을 보여줍니다.  **결론적으로, LEP는 전통적인 언어 특정 지시 조정에 비해 효율적인 대안**을 제공하여 언어 적응 비용을 크게 줄이는 동시에 동시대 LLM의 성능 기준을 유지하거나 뛰어넘는 성능을 달성할 수 있습니다.  **러시아어 적응을 위한 새로운 벤치마크인 Darumeru**를 개발하여 성능을 평가하고 그 결과를 제시한 점도 주목할 만합니다.

#### Russian LLM Benchmark
이 연구는 러시아어 LLM(대규모 언어 모델)의 성능을 벤치마킹하기 위한 새로운 벤치마크를 제시합니다. **기존 벤치마크의 한계를 극복**하기 위해, **개방형 질문뿐 아니라 폐쇄형 질문도 포함**하는 다양한 작업을 포함하여 보다 포괄적인 평가를 제공합니다. 특히, 텍스트 요약 및 토큰 생성과 같은 작업을 통해 모델의 텍스트 이해 및 생성 능력을 평가합니다. 또한, **러시아어 특유의 어휘 및 문법적 특징을 고려**하여 모델의 강점과 약점을 보다 정확하게 파악할 수 있도록 설계되었습니다. 본 벤치마크는 오픈소스 LLM의 러시아어 적응을 위한 **효과적인 평가 도구**로 활용될 수 있으며, **향후 러시아어 LLM 연구 및 개발에 중요한 기여**를 할 것으로 기대됩니다.  **특히 벤치마크 해킹 문제를 해결**하기 위해 노력한 점과, 오프라인 환경에서도 평가가 가능하도록 설계된 점 또한 주목할 만합니다.  본 연구는 **러시아어 LLM의 성능 평가에 대한 새로운 기준**을 제시함으로써, 향후 연구의 방향을 제시하고, 보다 나은 러시아어 LLM의 개발을 위한 토대를 마련할 것으로 예상됩니다.

#### Embedding Propagation
본 논문에서 제안하는 '임베딩 전파(Embedding Propagation)'는 **기존의 대규모 언어 모델(LLM)의 지식을 유지하면서 새로운 언어에 대한 지식을 효율적으로 통합하는 기술**입니다.  기존의 LLM 언어 적응 방법은 대량의 데이터와 높은 컴퓨팅 비용을 필요로 했지만, 본 연구에서 제시된 방법은 **훈련 데이터 요구량을 줄이고 기존 LLM의 지식을 최대한 활용**합니다. 이를 통해 **비용 효율적인 언어 적응 파이프라인**을 구축하여, 특히 고품질의 훈련 데이터 확보가 어려운 저자원 언어 환경에서 효과적입니다.  **학습된 임베딩을 활용하여 새로운 언어 정보를 직접 통합**하는 혁신적인 방법론을 제시하며, 다양한 어휘 적응 시나리오에 대한 실험 결과는 제시된 방법이 기존의 LLM 성능과 경쟁력을 갖추고 있음을 보여줍니다.  **자체 보정 및 추가 지시 튜닝**을 통해 모델 성능을 더욱 향상시킬 수 있는 가능성도 제시하고 있습니다.  결론적으로, 본 연구는 **LLM의 언어 적응 과정에 대한 새로운 패러다임을 제시**하며, 다양한 언어 지원이 필요한 응용 분야에 광범위하게 적용될 수 있을 것으로 기대됩니다.

#### Calibration & Fine-tuning
본 논문에서 제시된 LEP(Learned Embedding Propagation) 방법론의 핵심은 **기존의 instruction-tuned LLM에 새로운 언어 지식을 효율적으로 통합하는 것**입니다.  단순히 추가적인 instruction-tuning 데이터를 사용하는 대신, **기존 모델의 지식을 최대한 활용**하면서 새로운 언어에 대한 정보를 효과적으로 주입합니다. 이를 위해, LEP는 **embedding propagation 기법**을 활용하여, 최소한의 training 데이터와 연산 비용으로 새로운 언어에 대한 지식을 기존 모델에 적용합니다.  **자체 교정(Self-calibration)** 과정을 통해 생성된 데이터를 활용하여 LEP의 성능을 더욱 향상시키고,  **추가적인 instruction-tuning**을 통해 모델의 task-solving 능력을 개선합니다.  **결과적으로, LEP는 전통적인 language-specific instruction-tuning에 비해 비용 효율적인 대안을 제시하며**,  최신 LLM과 비교하여 성능 저하 없이, 또는 경우에 따라 더 나은 성능을 달성합니다. 이는 **다양한 언어 모델에 적용 가능**하며,  **계산 비용 및 데이터 소모량을 크게 절감**할 수 있는 장점을 가지고 있습니다.

#### LEP Limitations
LEP(Learned Embedding Propagation)의 제한점에 대한 심층적인 고찰은 **다국어 모델의 기반 모델 접근성 부족**, **계층 구조적 특징 표현의 부적절한 전이**, 그리고 **제한된 지식 전달 능력**이라는 세 가지 주요 측면을 중심으로 이루어져야 합니다.  **기반 모델의 접근성 부족**은 LEP의 적용 가능성에 제약을 가하며, 특히 폐쇄적인 환경에서 훈련된 모델에 대한 접근이 제한될 경우 LEP의 효용성이 크게 감소할 수 있습니다. **계층적 특징 표현의 전이 문제**는 LEP가 주로 임베딩 층에 집중하여 상위 층의 지식 전달에 대한 고려가 부족하다는 점을 시사합니다. 이는 모델의 전체적인 성능 향상에 제약이 될 수 있으며, 보다 포괄적인 접근 방식이 필요함을 의미합니다. 마지막으로, **제한된 지식 전달 능력**은 LEP가 기존 모델의 지식을 완전히 활용하지 못할 가능성을 보여줍니다. 이는 새로운 언어 지식의 효과적인 통합에 어려움을 초래할 수 있으며, 보다 정교한 지식 전달 메커니즘의 개발이 요구됨을 시사합니다.  결론적으로, LEP의 한계는 모델 접근성, 지식 전이, 그리고 지식 활용의 세 가지 핵심 영역에서의 개선을 통해 해결될 수 있습니다.  **더욱 포괄적인 연구**를 통해 이러한 제한점을 극복하고 LEP의 실용성을 높일 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.21140/extracted/6098179/image44.png)

> 🔼 그림 2는 다양한 토큰화 방법(BPE, Unigram, 확장, 최적화)을 사용하여 미스트랄 7B와 라마 3-8B 모델을 러시아어로 미세 조정하는 동안 평가 지표(Micro average)의 변화를 보여줍니다.  훈련 단계에 따른 평가 점수의 변화 추이를 통해 각 토큰화 전략의 효율성과 수렴 속도를 비교 분석할 수 있습니다.  각 선은 특정 모델과 토큰화 방법의 조합을 나타내며,  훈련 데이터셋 크기에 따른 성능 변화를 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Micro average benchmark score dynamic throughout training
> </details>



![](https://arxiv.org/html/2412.21140/extracted/6098179/image45.png)

> 🔼 그림 3은 OpenChat-3.5 모델과 해당 모델의 러시아어 적응 버전을 사용하여 생성된 텍스트의 예시를 보여줍니다.  원본 OpenChat-3.5 모델은 질문의 의미를 제대로 파악하지 못하고 부정확한 답변을 생성합니다.  러시아어 적응 버전(LEP-Extended)은 질문의 의미를 더 잘 이해하고 더 정확한 답변을 생성하지만, 여전히 관용구의 의미를 완전히 파악하지는 못합니다. 마지막으로, 보정된 모델(LEP-Extended + Calibration)은 질문의 의미를 정확하게 파악하고 관용구의 의미까지 고려하여 가장 정확한 답변을 생성합니다. 이 그림은 제안된 러시아어 적응 방법의 효과를 보여주는 대표적인 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: An example of generation using the OpenChat-3.5 model and its adapted versions.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | Vocab | Symbols per token | Micro-Avg | DaruMMLU | DaruMERA | DaruSum | DaruCopy (EN) | DaruCopy (RU) |
|---|---|---|---|---|---|---|---|---|
| Mistral-7B | Original | 2,44 | 0,604 | **0,545** | 0,504 | 0,307 | **1,000** | **1,000** |
|  | BPE | **3,76** | 0,616 | 0,528 | 0,537 | **0,316** | 0,995 | 0,984 |
|  | Unigram | **3,78** | 0,614 | **0,544** | 0,311 | 0,995 | 0,960 |
|  | Extended | **3,77** | **0,617** | 0,532 | **0,314** | **1,000** | 0,995 |
| LLaMa-3-8B | Original | 2,89 | **0,629** | **0,582** | **0,547** | **0,326** | 0,980 | 0,982 |
|  | BPE | **4,40** | 0,618 | 0,532 | 0,321 | **1,000** | 0,963 |
|  | Unigram | **4,35** | 0,609 | 0,517 | 0,316 | **1,000** | 0,951 |
|  | Extended | 3,78 | **0,627** | **0,550** | **0,325** | 0,980 | 0,983 |
|  | Optimized | 3,40 | 0,620 | 0,552 | 0,536 | 0,323 | 0,981 | **0,989** |{{< /table-caption >}}
> 🔼 본 표는 논문의 2.4.2절(Case Study: Self-Calibration)에서 언급된 최적의 언어 적응 검사점에 대한 Darumeru 벤치마크 결과를 보여줍니다.  각 모델(Mistral-7B, LLaMa-3-8B)과 토큰화 방법(BPE, Unigram, Extended, Optimized)에 따른 평균 점수(Micro-Avg), 그리고 각 하위 벤치마크(DaruMMLU, DaruMERA, DaruSum, DaruCopy (EN), DaruCopy (RU))에 대한 점수를 보여주어, 다양한 언어 적응 전략의 성능을 비교 분석하는 데 도움을 줍니다.  'Symbols per token' 열은 토큰당 평균 심볼 수를 나타내어, 토큰화 효율성을 함께 고려한 분석이 가능하도록 합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Darumeru few-shot evaluation results for best language-adaptation checkpoints.
> </details>

{{< table-caption >}}
| Vocab | LEP method | Micro-Avg | DaruMMLU | DaruMERA | DaruSum | DaruCopy (En) | DaruCopy (Ru) |
|---|---|---|---|---|---|---|---| 
| OpenChat-3.5 |  |  |  |  |  |  |  |
| BPE | Swap | **0,587** | **0,528** | **0,526** | 0,277 | 0,988 | **0,829** |
| BPE | Overlap | 0,584 | 0,525 | 0,523 | 0,281 | 0,986 | 0,818 |
| BPE | Conversion | 0,583 | 0,526 | 0,524 | **0,284** | **0,993** | 0,791 |
| Unigram | Swap | 0,556 | **0,517** | 0,517 | 0,282 | 0,985 | 0,614 |
| Unigram | Overlap | **0,572** | 0,514 | **0,534** | 0,297 | 0,981 | **0,680** |
| Unigram | Conversion | 0,565 | 0,515 | 0,519 | **0,301** | **0,999** | 0,651 |
| Extended | Swap | **0,608** | **0,535** | **0,540** | 0,298 | **0,999** | **0,907** |
| Extended | Overlap | **0,607** | **0,535** | **0,539** | **0,307** | **0,999** | 0,898 |
| Extended | Conversion | **0,609** | **0,535** | **0,541** | **0,306** | **0,999** | **0,909** |
| LLaMa-3-8B (instruct) |  |  |  |  |  |  |  |
| BPE | Swap | 0,565 | **0,544** | 0,486 | **0,317** | **0,999** | 0,729 |
| BPE | Overlap | **0,569** | **0,546** | **0,489** | 0,314 | **0,999** | **0,753** |
| BPE | Conversion | **0,570** | **0,546** | **0,490** | **0,318** | **0,999** | **0,754** |
| Unigram | Swap | **0,582** | **0,545** | **0,488** | **0,313** | **0,999** | 0,865 |
| Unigram | Overlap | 0,580 | **0,545** | 0,482 | **0,314** | **0,999** | 0,876 |
| Unigram | Conversion | **0,584** | **0,545** | **0,488** | **0,315** | 0,994 | **0,889** |
| Extended | Swap | 0,592 | **0,557** | 0,498 | **0,319** | 0,969 | 0,921 |
| Extended | Overlap | **0,597** | **0,556** | **0,504** | **0,321** | 0,964 | **0,936** |
| Extended | Conversion | **0,597** | **0,556** | 0,501 | 0,318 | **0,994** | 0,921 |
| Optimized | Swap | 0,594 | **0,554** | **0,499** | **0,327** | 0,970 | **0,928** |
| Optimized | Overlap | 0,586 | **0,553** | 0,495 | 0,323 | 0,925 | 0,925 |
| Optimized | Conversion | **0,598** | **0,555** | **0,500** | 0,324 | **0,995** | **0,928** |{{< /table-caption >}}
> 🔼 표 3은 제안된 학습 임베딩 전파(LEP) 방법의 성능을 다루메루 벤치마크를 사용하여 평가한 결과를 보여줍니다.  각 어휘 적응 방법(BPE, Unigram, Extended, Optimized)에 대해 세 가지 LEP 방법(직접 임베딩 교환, 겹치는 토큰 수정, 어휘 변환)의 다루메루 점수를 보여줍니다.  Mistral-7B와 LLaMa-3-8B 모델 모두에 대한 결과가 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Darumeru zero-shot evaluation results for Learned Embedding Propagation methods.
> </details>

{{< table-caption >}}
| Model | Fine-tuning data | Micro-Avg | DaruMMLU | DaruMERA | DaruSum | DaruCopy (EN) | DaruCopy (RU) |
|---|---|---|---|---|---|---|---| 
| OpenChat-3.5 |  |  |  |  |  |  |  |
| Original model | - | 0,607 | **0,543** | 0,526 | 0,322 | **0,999** | 0,917 |
|  | saiga d7 | 0,611 | 0,540 | **0,528** | **0,325** | **0,999** | 0,945 |
|  | +copy task | **0,615** | 0,541 | 0,524 | 0,324 | **1,000** | **0,995** |
| Unigram | - | 0,565 | 0,515 | 0,519 | 0,301 | **0,999** | 0,651 |
|  | saiga d7 | 0,599 | 0,556 | 0,316 | **0,999** | 0,754 |
|  | +copy task | **0,630** | **0,559** | **0,321** | **1,000** | **0,999** |
| Extended | - | 0,609 | 0,535 | 0,541 | 0,306 | **0,999** | 0,909 |
|  | saiga d7 | 0,616 | **0,543** | **0,566** | 0,319 | **0,999** | 0,845 |
|  | +copy task | **0,632** | 0,563 | **0,321** | **1,000** | **0,989** |
| LLaMa-3-8B (instruct) |  |  |  |  |  |  |  |
| Original model | - | 0,610 | 0,571 | 0,510 | 0,322 | **1,000** | 0,972 |
|  | saiga d7 | 0,615 | 0,512 | 0,329 | **1,000** | 0,983 |
|  | +copy task | **0,616** | **0,513** | **0,332** | **1,000** | **0,995** |
| Extended | - | 0,597 | 0,556 | 0,501 | 0,318 | 0,994 | 0,921 |
|  | self-calibration | 0,606 | 0,552 | 0,512 | 0,321 | **1,000** | 0,958 |
|  | saiga d7 | 0,614 | 0,519 | 0,338 | 0,995 | 0,961 |
|  | +copy task | **0,618** | 0,565 | **0,521** | **0,339** | **1,000** | **0,984** |
| Optimized | - | 0,598 | **0,555** | 0,500 | 0,324 | 0,995 | 0,928 |
|  | self-calibration | 0,601 | 0,550 | 0,501 | 0,325 | **1,000** | 0,950 |
|  | saiga d7 | 0,611 | 0,515 | 0,336 | **1,000** | 0,971 |
|  | +copy task | **0,617** | **0,555** | **0,522** | **0,339** | **1,000** | **0,989** |{{< /table-caption >}}
> 🔼 표 4는 변환 LEP 모델의 모델 보정 방식에 대한 벤치마크 결과를 보여줍니다.  이 표는 다양한 토큰화 방식(BPE, Unigram, Extended, Optimized)과 보정 기법(원본 모델, Saiga 데이터셋으로 추가 미세 조정, 자체 보정)을 사용한  OpenChat-3.5와 LLaMa-3-8B 모델의 성능을 DaruMMLU, DaruMERA, DaruSum, DaruCopy (EN), DaruCopy (RU) 등 다양한 벤치마크에서 비교 분석한 결과를 나타냅니다. 각 벤치마크는 특정 언어 이해 및 생성 능력을 평가하며, 보정 방법에 따른 모델 성능 향상 및 저하 여부를 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Benchmark results for model calibration schemes of Conversion LEP models
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
{{< /gallery >}}