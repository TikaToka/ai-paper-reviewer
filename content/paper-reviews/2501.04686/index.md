---
title: "URSA: Understanding and Verifying Chain-of-thought Reasoning in Multimodal Mathematics"
summary: "URSA-7B 모델은 다중 모드 수학 문제 풀이에서 최첨단 성능을 달성!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Tsinghua University",]
showSummary: true
date: 2025-01-08
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.04686 {{< /keyword >}}
{{< keyword icon="writer" >}} Ruilin Luo et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-09 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.04686" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.04686" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/ursa-understanding-and-verifying-chain-of" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)의 수학적 추론 능력 향상은 인공지능 분야의 주요 과제입니다. 특히, 다중 모드(텍스트와 이미지) 수학 문제 해결은 고품질 데이터 부족으로 어려움을 겪고 있습니다. 기존 모델들은 단순히 짧은 출력 패턴에 맞추는 경향이 있어, 복잡한 추론 과정을 제대로 학습하지 못하는 한계가 있습니다.

본 논문에서는 이러한 문제를 해결하기 위해, CoT(Chain-of-Thought) 증류, 경로 재작성, 형식 통합 등의 세 가지 모듈을 통합한 새로운 합성 전략을 제시합니다. 이를 통해 고품질의 다중 모드 수학 CoT 데이터셋인 MMathCoT-1M을 만들고, 이를 바탕으로 URSA-7B 모델을 학습시켰습니다. 또한, 테스트 시간 성능 향상을 위해, 이중 관점 프로세스 감독 데이터 합성 전략을 제안하고, URSA-RM-7B 검증 모델을 개발했습니다. 실험 결과, 제안된 모델은 다양한 벤치마크에서 최첨단 성능을 달성했으며, 특히 테스트 시간 확장성이 뛰어남을 보였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 고품질 다중 모드 수학 CoT 데이터셋인 MMathCoT-1M을 제작 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 테스트 시간 확장을 위한 이중 관점 프로세스 감독 데이터 합성 전략 제안 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 다중 모드 수학 벤치마크에서 최첨단 성능을 달성한 URSA-7B 및 URSA-RM-7B 모델 개발 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **다중 모드 수학 추론에서 Chain-of-Thought(CoT) 추론의 성능을 향상시키는 데 중점**을 두고 있으며, 고품질 CoT 데이터를 생성하고 테스트 시간 확장을 위한 검증 모델을 제안합니다. 이는 **현재 연구 동향과 밀접하게 관련**되어 있으며, **추후 연구를 위한 새로운 방향**을 제시합니다. 특히, **고품질 다중 모드 데이터 세트의 부족 문제를 해결**하고, **테스트 시간 확장 가능성을 입증**한 점에서 큰 의의를 가집니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.04686/x1.png)

> 🔼 그림 1은 MathVista와 MathVerse 데이터셋에서 다양한 유형의 수학 문제에 대해 URSA-7B와 다른 오픈소스 다중 모달 언어 모델(MLLM)의 추론 능력을 비교한 결과를 보여줍니다.  비교 대상에는 다양한 추론 유형(예: 통계적 추론, 과학적 추론, 기하학적 추론, 대수적 추론, 산술적 추론, 수치적 추론)이 포함되며, 각 모델이 모달 정보(텍스트, 이미지)의 양이 변화하는 상황에서도 안정적인 추론 성능을 유지하는지를 평가합니다.  즉, 텍스트만 있는 문제, 텍스트와 이미지가 모두 있는 문제, 이미지만 있는 문제 등 다양한 조건에서 각 모델의 성능을 비교 분석하여, 모델의 강점과 약점, 그리고 모달 정보 활용 능력을 종합적으로 평가합니다.  그래프는 각 모델의 성능을 레이더 차트 형태로 시각화하여 직관적인 비교를 가능하게 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: We compare the reasoning ability of URSA-7B and other open-source MLLMs across different topics on MathVista and MathVerse, as well as their reasoning stability when faced with changes in modal information content.
> </details>





{{< table-caption >}}
| Model | #Params | MathVista ALL | MathVista GPS | MathVista MWP | MathVista FQA | MathVista TQA | MathVista VQA | MathVerse ALL | MathVerse TD | MathVerse TL | MathVerse TO | MathVerse VI | MathVerse VD | MathVerse VO |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| *Baselines* |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| Random | - | 17.9 | 21.6 | 3.8 | 18.2 | 19.6 | 26.3 | 12.4 | 12.4 | 12.4 | 12.4 | 12.4 | 12.4 | 12.4 |
| Human | - | 60.3 | 48.4 | 73.0 | 59.7 | 63.2 | 55.9 | 64.9 | 71.2 | 70.9 | 41.7 | 61.4 | 68.3 | 66.7 |
| *Closed-Source MLLMs* |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| GPT-4o (OpenAI, 2024) | - | 63.8 | - | - | - | - | - | - | - | - | - | - | - | - |
| GPT-4V (OpenAI, 2023) | - | 49.9 | 50.5 | 57.5 | 43.1 | 65.2 | 38.0 | 54.4 | 63.1 | 56.6 | 60.3 | 51.4 | 32.8 | 50.3 |
| Gemini-1.5-002-Flash (Team et al., 2023) | - | 58.4 | - | - | - | - | - | - | - | - | - | - | - | - |
| Gemini-1.5-Pro (Team et al., 2023) | - | 63.9 | - | - | - | - | - | 35.3 | 39.8 | 34.7 | 44.5 | 32.0 | 36.8 | 33.3 |
| Claude-3.5-Sonnet (Anthropic, 2024) | - | 67.7 | - | - | - | - | - | - | - | - | - | - | - |  |
| Qwen-VL-Plus (Bai et al., 2023) | - | 43.3 | 35.5 | 31.2 | 54.6 | 48.1 | 51.4 | 21.3 | 26.0 | 21.2 | 25.2 | 18.5 | 19.1 | 21.8 |
| *Open-Source General MLLMs* |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| mPLUG-Owl2-7B (Ye et al., 2023) | 7B | 22.2 | 23.6 | 10.2 | 22.7 | 27.2 | 27.9 | 10.3 | 11.6 | 11.4 | 13.8 | 11.1 | 9.4 | 8.0 |
| MiniGPT4-7B (Zhu et al., 2023) | 7B | 23.1 | 26.0 | 13.4 | 18.6 | 30.4 | 30.2 | 12.2 | 12.3 | 12.9 | 13.4 | 12.5 | 14.8 | 8.7 |
| LLaVA-1.5-13B (Liu et al., 2024b) | 13B | 27.7 | 22.7 | 18.9 | 23.8 | 43.0 | 30.2 | 12.7 | 17.1 | 12.0 | 22.6 | 12.6 | 12.7 | 9.0 |
| SPHINX-V2-13B (Lin et al., 2023) | 13B | 36.7 | 16.4 | 23.1 | 54.6 | 41.8 | 43.0 | 16.1 | 20.8 | 14.1 | 14.0 | 16.4 | 15.6 | 16.2 |
| LLaVA-NeXT-34B (Liu et al., 2024c) | 34B | 46.5 | - | - | - | - | - | 34.6 | 49.0 | 37.6 | 30.1 | 35.2 | 28.9 | 22.4 |
| InternLM-XComposer2-VL (Dong et al., 2024a) | 7B | 57.6 | 63.0 | 73.7 | 55.0 | 56.3 | 39.7 | 25.9 | 36.9 | 28.3 | 42.5 | 20.1 | 24.4 | 19.8 |
| Deepseek-VL (Lu et al., 2024) | 7B | 34.9 | 28.4 | 55.9 | 26.8 | 32.9 | 34.6 | 19.3 | 23.0 | 23.2 | 23.1 | 20.2 | 18.4 | 11.8 |
| InternVL2-8B (Chen et al., 2024b) | 8B | 58.3 | 62.0 | 59.1 | 58.7 | 61.4 | 49.7 | 35.9 | 39.0 | 33.8 | 36.0 | 32.2 | 30.9 | 27.7 |
| Qwen2-VL (Wang et al., 2024a) | 7B | 58.9 | 40.9 | 64.0 | 69.1 | 60.1 | 58.1 | 33.6 | 37.4 | 33.5 | 35.0 | 31.3 | 30.3 | 28.1 |
| *Open-Source Math MLLMs* |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| G-LLaVA-7B (Gao et al., 2023) | 7B | 25.1 | 48.7 | 3.6 | 19.1 | 25.0 | 28.7 | 16.6 | 20.9 | 20.7 | 21.1 | 17.2 | 14.6 | 9.4 |
| Math-LLaVA-13B (Shi et al., 2024) | 13B | 46.6 | 57.7 | 56.5 | 37.2 | 51.3 | 33.5 | 22.9 | 27.3 | 24.9 | 27.0 | 24.5 | 21.7 | 16.1 |
| Math-PUMA-Qwen2-7B (Zhuang et al., 2024) | 7B | 47.9 | 48.1 | 68.3 | 46.5 | 46.2 | 30.2 | 33.6 | 42.1 | 35.0 | 39.8 | 33.4 | 31.6 | 26.0 |
| Math-PUMA-DeepSeek-Math (Zhuang et al., 2024) | 7B | 44.7 | 39.9 | 67.7 | 42.8 | 42.4 | 31.3 | 31.8 | 43.4 | 35.4 | 47.5 | 33.6 | 31.6 | 14.7 |
| MAVIS-7B (Zhang et al., 2024d) | 7B | - | 64.1 | - | - | - | - | 35.2 | 43.2 | 37.2 | - | 34.1 | 29.7 | 31.8 |
| InfiMM-Math (Han et al., 2024) | 7B | - | - | - | - | - | - | 34.5 | 46.7 | 32.4 | - | 38.1 | 32.4 | 15.8 |
| MultiMath-7B (Peng et al., 2024) | 7B | 50.0 | 66.8 | 61.8 | 40.1 | 50.0 | 33.0 | 27.7 | 34.8 | 30.8 | 35.3 | 28.1 | 25.9 | 15.0 |
| URSA-7B | 7B | 59.8 | 79.3 | 75.3 | 44.6 | 63.9 | 40.2 | 45.7 | 55.3 | 48.3 | 51.8 | 46.4 | 43.9 | 28.6 |
| Δ over SOTA *Open-Source Math MLLMs* | - | +9.8 | +12.5 | +7.0 | -1.9 | +12.6 | +6.7 | +10.5 | +8.6 | +11.1 | +4.3 | +8.3 | +11.5 | -3.2 |{{< /table-caption >}}

> 🔼 표 1은 MATHVISTA testmini 및 MATHVERSE testmini에 대한 closed-source 및 open-source 다중 모드 언어 모델(MLLM)의 성능 비교 결과를 보여줍니다.  Closed-source MLLM의 경우 최고 성능은 녹색으로, open-source MLLM의 경우 최고 및 두 번째로 높은 성능은 각각 빨간색과 파란색으로 강조 표시되어 있습니다.  각 모델의 매개변수 수와 다양한 하위 작업(예: 기하 문제 해결, 수학 단어 문제, 숫자 추론, 시각적 질문 응답 등)에 대한 성능이 제시되어 있습니다. 최고 성능은 굵게, 두 번째로 높은 성능은 밑줄로 표시됩니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparison with closed-source MLLMs and open-source MLLMs on MATHVISTA testmini and MATHVERSE testmini. The best is bold, and the runner-up is underline. The best results of Closed-source MLLMs are highlighted in green. The best and second-best results of Open-source MLLMs are highlighted in red and blue respectively.
> </details>





### In-depth insights


#### Multimodal CoT
멀티모달 체인 오브 써트(Multimodal CoT)는 **텍스트와 이미지와 같은 다양한 모달리티의 정보를 통합하여 추론 과정을 수행하는 기법**입니다. 기존의 텍스트 기반 CoT가 언어 모델의 추론 능력 향상에 기여한 것처럼, 멀티모달 CoT는 **이미지 이해 및 시각적 정보 처리 능력과 언어적 추론 능력을 결합하여 보다 복잡하고 다양한 문제 해결에 도움**을 줄 수 있습니다. 특히 수학, 과학 등 시각적 정보가 중요한 분야에서 탁월한 성능을 보일 가능성이 높습니다. 하지만, 멀티모달 CoT를 위한 고품질 학습 데이터 구축의 어려움, 다양한 모달리티 간의 정보 통합 및 일관성 유지의 어려움, 그리고 모달리티 간 상호작용에 대한 명확한 이해 부족 등의 **여전히 해결해야 할 과제**들이 있습니다.  향후 연구는 **고품질 멀티모달 데이터셋 구축, 효과적인 모달리티 융합 기술 개발, 그리고 멀티모달 추론 과정의 해석 및 평가 방법론 연구**에 집중되어야 할 것입니다.  **실제 응용 분야 확장 및 윤리적 고려**도 중요한 연구 방향이 될 것입니다.

#### URSA-7B Model
URSA-7B 모델은 **다중 모드 수학적 추론**을 위한 강력한 기반 모델로, **고품질의 CoT(Chain-of-Thought) 추론 데이터셋**인 MMathCoT-1M을 사용하여 학습되었습니다.  **CoT 증류, 경로 재작성, 형식 통일**이라는 세 가지 모듈을 통합한 독창적인 합성 전략을 통해 고품질의 데이터셋을 구축했습니다.  **MathVista 및 MathVerse와 같은 다양한 벤치마크에서 최첨단 성능**을 달성하며, 특히 기하 문제 해결과 같은 어려운 작업에서 뛰어난 능력을 보여줍니다.  더 나아가, **테스트 시간 확장을 위한 이중 관점 프로세스 감독 데이터 합성** 전략을 통해, URSA-RM-7B 검증자 모델과 함께 사용되어 테스트 시간에 강력한 성능을 보입니다.  **URSA-7B는 다양한 문제 유형에 대한 강력한 일반화 능력**을 입증하며, 특히 OOD(Out-of-Distribution) 검증에서 탁월한 성능을 보여줍니다. 따라서 URSA-7B는 **차세대 다중 모드 수학적 추론 모델**의 기반이 될 것으로 기대됩니다.

#### DualMath Dataset
DualMath 데이터셋은 **다중 모드 수학 추론에서의 오류를 해결하기 위한 혁신적인 접근법**을 제시합니다. 기존의 단순한 정답만 제공하는 방식에서 벗어나, **추론 과정 자체에 대한 이중적인 관점 (논리적 정확성과 시각적 정확성)**을 제시하여 보다 정교한 오류 수정을 가능하게 합니다.  **몬테 카를로 트리 탐색(MCTS) 기법**을 활용하여 추론 과정에서의 오류 단계를 정확하게 식별하고, **오류 주입 프롬프트**를 통해 모델의 시각 정보 이해 능력을 향상시키는 전략을 사용합니다. 이를 통해 **고품질의 다중 모드 수학 추론 데이터를 생성**하여, 모델의 성능 향상에 크게 기여할 것으로 기대됩니다. **실제 테스트 결과**에서도 DualMath 데이터셋을 활용한 모델의 우수성이 입증될 것으로 예상됩니다.

#### Test-time Scaling
본 논문에서 다룬 "Test-time Scaling"은 **추론 시 모델의 확장성**을 높이는 데 중점을 둡니다.  이는 고품질의 CoT(Chain-of-Thought) 학습 데이터 부족으로 인해 기존 모델들이 테스트 시간에 제한적인 추론 능력을 보이는 문제를 해결하기 위한 시도입니다.  **데이터 합성 전략**을 통해 추가적인 프로세스 주석 데이터셋을 생성하여 모델의 테스트 시간 추론 성능을 향상시키는 것이 핵심입니다.  **URSA-RM-7B 검증자 모델**을 도입하여 **추론 과정의 정확성을 검증**하고,  **오류를 탐지하여 수정**하는 기능을 추가함으로써,  **실제 추론 성능 개선**을 이끌어냅니다. 이러한 접근법은 다양한 벤치마크에서 우수한 성능을 보이며, 특히  **OOD(Out-of-Distribution) 검증**에서 뛰어난 일반화 능력을 보여줍니다.  결론적으로, 본 논문의 Test-time Scaling 전략은 **고품질 CoT 추론을 위한 효율적인 방법**임을 시사합니다.

#### Future of MLLMs
멀티모달 대규모 언어 모델(MLLM)의 미래는 **매우 밝지만, 동시에 도전 과제 또한 많습니다.**  향후 MLLM은 **더욱 정교한 추론 능력**을 갖추고, **다양한 모달리티를 원활하게 통합**하며 **실시간 응답 속도**를 개선할 것으로 예상됩니다. 이를 위해서는 **고품질의 멀티모달 학습 데이터** 확보가 필수적이며, **데이터 증강 및 합성 기술**의 발전도 중요합니다.  또한, **모델의 설명력 향상**과 **신뢰성 확보**를 위한 연구도 활발히 진행될 것으로 예상됩니다.  **윤리적 문제 및 편향성 해소**를 위한 노력 또한 매우 중요하며,  **사회적 책임감 있는 개발 및 배포**가 중요한 과제가 될 것입니다.  궁극적으로 MLLM은 인간과 같은 수준의 지능을 가진 **인공지능 시스템 개발**에 중요한 역할을 할 것으로 기대되지만, **기술적 한계와 사회적 영향**에 대한 심도있는 고찰이 필요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.04686/x2.png)

> 🔼 그림 2는 URSA-7B 모델의 학습에 사용된 데이터 소스를 보여줍니다.  VL-alignment 단계와 SFT(Supervised Fine-Tuning) 단계 모두에서 사용된 여러 데이터셋들이 포함되어 있습니다.  각 데이터셋의 유형과 크기가 함께 표시되어 URSA-7B 모델이 다양한 종류의 수학적 추론 데이터를 통해 학습되었음을 보여줍니다.  데이터셋에는 다양한 수학 문제 유형 (기하학, 대수학 등)과 표현 형식 (텍스트 기반, 텍스트와 이미지 결합)의 데이터가 포함되어 있어,  URSA-7B 모델의 강건하고 다양한 수학적 추론 능력을 향상시키는 데 기여했음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Data sources used by the URSA-7B model during the VL-alignment and SFT phases.
> </details>



![](https://arxiv.org/html/2501.04686/x3.png)

> 🔼 이 그림은 세 가지 유형의 소스(Answer-only, Analysis-formatted, CoT-formatted)로부터 얻은 다중 모드 수학 데이터에 대해 Gemini-1.5-Flash-002를 사용하여 CoT 증강 및 검증 과정을 보여줍니다. 각 유형의 데이터에 대해, Gemini-1.5-Flash-002는 질문과 답변을 사용하여 사고 과정을 생성하고, 이를 다시 작성하여 형식을 통일합니다.  최종적으로, 검증 단계를 거쳐 고품질의 CoT 추론 지침 미세 조정 데이터셋을 생성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: CoT augmentation and verifying for multimodal mathematical data from three type of sources using Gemini-1.5-Flash-002.
> </details>



![](https://arxiv.org/html/2501.04686/x4.png)

> 🔼 그림 4는 다중 모드 추론 과정에서 오류를 유발하는 오류 주입 엔진의 작동 과정을 보여줍니다.  잘못된 해석을 도입하여 모델이 잘못된 추론 경로를 생성하도록 유도하는 과정을 시각적으로 보여줍니다.  구체적으로, 이미지에서 정보를 추출하는 단계, 그 정보에 대한 오류를 도입하는 단계, 그리고 그 오류를 바탕으로 잘못된 최종 답을 도출하는 단계로 구성되어 있습니다.  각 단계는 시각적인 예시와 함께 설명되어 있어 오류 주입 엔진의 작동 원리를 명확하게 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Demonstration of Misinterpretation Insertion Engine.
> </details>



![](https://arxiv.org/html/2501.04686/x5.png)

> 🔼 그림 5는 URSA-7B 및 URSA-RM-7B에 대한 학습 과정을 보여줍니다. 세 단계의 데이터는 각각 URSA-alignment-960K, MMathCoT-1M 및 DualMath-1.1M에서 가져옵니다. 각 단계에서 고정된 모듈과 학습해야 하는 모듈이 구분되어 있습니다.  URSA-alignment-960K는 Vision-Language 정렬을 위한 데이터이고, MMathCoT-1M은 수학 관련 CoT(Chain-of-Thought) 추론 지침 미세 조정 데이터셋이며, DualMath-1.1M은 테스트 시간 확장을 위해 자동으로 생성된 프로세스 주석 데이터셋입니다. 그림은 각 단계의 데이터 흐름과 모델 구성을 시각적으로 나타내어 URSA 모델의 학습 과정을 명확히 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: An illustration of the training process for URSA-7B and URSA-RM-7B, with data from the three stages coming from URSA-alignment-960K, MMathCoT-1M, and DualMath-1.1M, respectively. The modules that are frozen and those that need to be trained are distinguished in each stage.
> </details>



![](https://arxiv.org/html/2501.04686/x8.png)

> 🔼 그림 6은 MathVerse와 MathVista-GPS 두 데이터셋에서 Pass@N과 Best-of-N 결과를 비교한 그래프입니다. Pass@N은 N번의 추론 시도 중 정답을 얻는 비율을 나타내고, Best-of-N은 N번의 추론 결과 중 가장 좋은 결과를 선택하는 방식을 의미합니다. 이 그래프는 다양한 샘플링 횟수(N)에 따른 모델의 성능 변화를 보여주어, 테스트 시간 확장(test-time scaling) 전략의 효과를 평가하는 데 사용됩니다. MathVerse와 MathVista-GPS는 서로 다른 특징을 가진 수학 추론 데이터셋으로, 이를 통해 모델의 일반화 성능을 다각적으로 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Pass@N and Best-of-N results comparison on MathVerse and MathVista-GPS.
> </details>



![](https://arxiv.org/html/2501.04686/x9.png)

> 🔼 그림 7은 MathVista testmini 집합에 대한 수학 SFT 단계에서 CoT 증강에 대한 절삭 연구를 보여줍니다. CoT 증강이 없는 경우와 비교하여 CoT 증강을 사용한 경우의 정확도를 다양한 하위 작업(ALL, GPS, MWP, FQA, TQA, VQA)에 대해 비교 분석합니다. 이를 통해 CoT 증강이 MathVista testmini 집합에 대한 모델의 전반적인 추론 능력 향상에 미치는 영향을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Ablation Study w.r.t CoT Augmentation during Math SFT Stage on the MathVista testmini Set.
> </details>



![](https://arxiv.org/html/2501.04686/x10.png)

> 🔼 그림 8은 MathVerse 벤치마크에서 수학 SFT 단계 중 CoT 증강에 대한 ablation 연구 결과를 보여줍니다. CoT 증강이 MathVerse 벤치마크의 다양한 하위 작업(ALL, TD, TL, TO, VI, VD, VO)에서 모델 성능에 미치는 영향을 정량적으로 분석한 결과를 나타냅니다.  각 막대는 특정 하위 작업에 대한 정확도를 나타내며, 'w/ Aug'는 CoT 증강을 적용한 경우, 'w/o Aug'는 CoT 증강을 적용하지 않은 경우를 나타냅니다. 이를 통해 CoT 증강이 MathVerse 벤치마크 전반에 걸쳐 모델 성능 향상에 기여하는지를 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Ablation Study w.r.t CoT Augmentation during Math SFT Stage on the MathVerse benchmark.
> </details>



![](https://arxiv.org/html/2501.04686/x11.png)

> 🔼 그림 9는 본 논문의 3.2절인 '다중 모드 수학에서의 CoT 증강' 섹션에 속하며, 'answer-only' 소스 데이터에 대한 CoT 증류에 사용된 프롬프트 𝒫C에 대한 자세한 설명을 제공합니다.  이 프롬프트는 모델이 주어진 정답을 기반으로 추론 과정을 생성하도록 유도하는 역할을 하며, 정답의 정확성을 신뢰하고 추가 정보 요청을 피하도록 지시합니다.  프롬프트는 질문, 정답, 그리고 재작성된 솔루션(단계별로 나열됨)을 포함하고, 최종적으로 '†Answer:' 다음에 정답을 입력하도록 안내합니다.  이는 모델이 단순히 암기 기반으로 답변하는 것이 아니라, 추론 과정을 거쳐 답변을 생성하도록 유도하는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Prompt 𝒫𝒞subscript𝒫𝒞\mathcal{P}_{\mathcal{C}}caligraphic_P start_POSTSUBSCRIPT caligraphic_C end_POSTSUBSCRIPT used for CoT distillation on answer-only source data.
> </details>



![](https://arxiv.org/html/2501.04686/x12.png)

> 🔼 그림 10은 분석 형식의 소스 데이터에 대한 CoT 솔루션 재작성에 사용된 프롬프트 𝒫ℛ에 대한 자세한 설명입니다.  이 프롬프트는 주어진 정답을 바탕으로 단계별 솔루션을 제공하도록 설계되었으며, 추가 정보 요청 없이 정답에 도달하는 솔루션을 생성해야 합니다.  예시를 통해 프롬프트의 사용 방법과 기대되는 응답 형식을 보여줍니다.  이는 논문의 모델 학습 과정에서 CoT 재작성 과정에 중요한 역할을 하는 부분입니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Prompt 𝒫ℛsubscript𝒫ℛ\mathcal{P}_{\mathcal{R}}caligraphic_P start_POSTSUBSCRIPT caligraphic_R end_POSTSUBSCRIPT used for CoT solution rewriting on analysis-formatted source data.
> </details>



![](https://arxiv.org/html/2501.04686/x13.png)

> 🔼 그림 11은 다양한 스타일의 소스 데이터에서 솔루션 형식을 통합하는 데 사용된 프롬프트 𝒫ℱ(P_F)를 보여줍니다.  본 논문에서는 수학적 추론 과정을 자연어 설명으로 변환하고, 각 단계를 'Step X:'로 구분하며, 공식적인 수학 기호는 최소한으로 사용하고, 설명이 명확하고 간결하며 최종 답변을 '†Answer: [최종 답변]'으로 표시하는 것을 포함하여, 다양한 형식의 수학적 솔루션을 통합하는 프롬프트의 구조와 내용을 자세하게 설명합니다.  이 프롬프트는 주어진 솔루션 단계와 최종 답변을 엄격하게 따라야 하며, 수정 또는 재해석해서는 안 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Prompt 𝒫ℱsubscript𝒫ℱ\mathcal{P}_{\mathcal{F}}caligraphic_P start_POSTSUBSCRIPT caligraphic_F end_POSTSUBSCRIPT used for unifying solution format across style-varied source data.
> </details>



![](https://arxiv.org/html/2501.04686/x14.png)

> 🔼 그림 12는 일관성 및 수정에 기반한 CoT 증강 응답을 확인하는 데 사용되는 프롬프트를 보여줍니다. 이 프롬프트는 주어진 표준 답변과 제시된 솔루션의 정합성을 평가하는 작업에 초점을 맞춥니다.  세부적으로는 솔루션의 신뢰성(모호하거나 추측적인 표현이 없는지 확인), 솔루션의 일관성(표준 답변과 결론이 정확히 일치하는지 확인), 그리고 평가 프로세스(솔루션의 논리적 단계 검토, 표준 답변과의 비교, 명확한 판단 제시)의 세 가지 기준을 제시합니다.  결론적으로, 이 프롬프트는 모델이 생성한 CoT 추론 과정의 정확성을 검증하는 데 사용되는 지침을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Prompt used for checking CoT augmentation response based on consistency and correction.
> </details>



![](https://arxiv.org/html/2501.04686/x15.png)

> 🔼 이 그림은 기하 문제 관련 샘플에 오류를 삽입하기 위해 사용되는 프롬프트를 보여줍니다.  이 프롬프트는 모델이 그림을 잘못 해석하여 답을 틀리게 유도하도록 설계되었습니다. 프롬프트는 세 단계로 구성됩니다. 1단계는 정답 솔루션의 분석, 2단계는 오류 삽입, 3단계는 잘못된 해석을 바탕으로 추론하는 과정입니다.  각 단계는 명확한 지침과 함께 제시되어 모델이 오류를 자연스럽게 삽입하고 부정확한 답을 도출하도록 유도합니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: Prompt used for inserting interpretation into geometry-related samples.
> </details>



![](https://arxiv.org/html/2501.04686/x16.png)

> 🔼 이 그림은 함수 및 통계 관련 문제에 대한 해석 오류를 삽입하기 위해 사용되는 프롬프트를 보여줍니다.  프롬프트는 좌표축이나 차트를 포함하는 수학 문제와 그 해법을 제시하고, 그림이나 차트를 잘못 해석하여 오류를 도입하고 잘못된 답을 생성하는 방식으로 수정된 해법을 만들도록 지시합니다.  이 과정은 세 단계로 나뉘는데, 첫째로 올바른 답변의 이미지 정보 추출 부분을 분석하고, 둘째로 잘못된 해석 시나리오를 도입하여 문제에 자연스럽게 통합하고, 셋째로 잘못된 해석을 기반으로 추론 과정을 계속하여 잘못된 최종 답변을 도출합니다.  프롬프트는 잘못된 해석에 대한 명시적인 언급을 피하고 일반적인 문제 해결 방식으로 응답하도록 지시합니다. <pos>와 <neg> 태그는 각 단계의 끝에만 표시되며, 한 단계가 여러 줄에 걸쳐 있는 경우에도 반복해서 사용하지 않습니다.  한 번 <neg>로 표시된 단계 이후 모든 단계는 <neg>로 간주됩니다. 잘못된 해석은 반드시 이루어져야 <neg> 태그가 사용될 수 있으며, 3단계의 잘못된 해석 동작은 2단계에서 계획된 내용과 일관성을 유지해야 합니다.  결론적으로 이 프롬프트는 모델이 시각적 정보를 잘못 해석하여 추론 과정에 오류를 발생시키는 방법을 학습하도록 유도하는 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: Prompt used for inserting interpretation into function and statistics-related samples.
> </details>



![](https://arxiv.org/html/2501.04686/x17.png)

> 🔼 그림 15는 MathVista-GPS 벤치마크의 한 문제에 대한 다양한 모델의 풀이 과정을 보여줍니다.  문제는 사다리꼴 ABCD에서 AD = 6, AB = 4, 각 ADC를 이등분하는 선분 DE가 BC와 점 E에서 만날 때 BE의 길이를 구하는 것입니다. 그림에는 GPT-4, Gemini-1.5-Flash-002, MultiMath-7B, Math-LLaVA-13B 그리고 URSA-7B의 풀이 과정이 제시되어 있으며, 각 모델의 풀이 방법과 정답의 정확성을 비교하여 보여줍니다. 특히 URSA-7B는 다른 모델들과는 다른 접근 방식으로 문제를 해결하고 정답을 제시하는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 15: Case on MathVista-GPS.
> </details>



![](https://arxiv.org/html/2501.04686/x18.png)

> 🔼 그림은 MathVerse 데이터셋의 한 문제를 보여줍니다. 문제는 원의 접선과 관련된 기하 문제이며, 그림에는 원과 접선, 그리고 각도 정보가 포함되어 있습니다. Gemini-1.5-Flash-002, Multimath-7B, 그리고 URSA-7B 세 가지 모델의 풀이 과정과 답변이 제시되어 있으며, URSA-7B의 풀이 과정이 다른 모델들보다 더 정확하고 논리적임을 보여줍니다. 각 모델의 풀이 방식과 최종 답변의 차이를 비교 분석하여, URSA-7B의 우수성을 강조합니다. 특히 URSA-7B는 삼각함수와 피타고라스 정리를 정확하게 활용하여 문제를 해결하는 반면, 다른 모델들은 오류를 포함하거나 비효율적인 방법을 사용합니다.
> <details>
> <summary>read the caption</summary>
> Figure 16: Case on MathVerse.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | #Params | Strict AVG ↑ | Strict IK ↓ | Strict IG ↓ | Strict CM ↑ | Strict RM ↓ | Loose AVG ↑ | Loose IK ↓ | Loose IG ↓ | Loose CM ↑ | Loose RM ↓ |
|---|---|---|---|---|---|---|---|---|---|---|---| 
|  Qwen-VL-Max (Bai et al., 2023) | - | 10.5 | 65.1 | 7.6 | 6.7 | 75.5 | 25.5 | 65.1 | 7.6 | 21.7 | 20.3 |
| Gemini-1.5-Pro (Team et al., 2023) | - | 26.4 | 42.9 | 11.2 | 20.8 | 54.8 | 46.0 | 42.9 | 11.2 | 40.4 | 12.0 |
| GPT-4V (OpenAI, 2023) | - | 31.1 | 39.8 | 14.5 | 23.8 | 47.9 | 51.4 | 39.8 | 14.5 | 44.2 | 3.3 |
| GPT-4o (OpenAI, 2024) | - | 42.9 | 31.2 | 15.2 | 35.2 | 34.2 | 60.6 | 31.2 | 15.2 | 53.0 | 1.1 |
| _Closed-source MLLMs_ |  |  |  |  |  |  |  |  |  |  |  |
| LLaVA-1.6 (Liu et al., 2024c) | 7B | 3.3 | 78.3 | 2.5 | 2.1 | 89.1 | 13.8 | 78.3 | 2.5 | 12.6 | 34.7 |
| LLaVA-1.6 (Liu et al., 2024c) | 13B | 5.2 | 69.1 | 3.2 | 3.6 | 86.9 | 22.0 | 69.1 | 3.2 | 20.4 | 26.2 |
| InternVL-Chat-V1.5 (Chen et al., 2024a) | 26B | 12.7 | 56.4 | 10.5 | 7.4 | 77.6 | 31.0 | 56.4 | 10.5 | 25.7 | 22.4 |
| LLaVA-NeXT (Liu et al., 2024c) | 72B | 13.4 | 58.9 | 7.1 | 9.9 | 71.0 | 31.5 | 58.9 | 7.1 | 28.0 | 17.9 |
| DeepSeek-VL (Lu et al., 2024) | 7B | 6.3 | 69.1 | 4.6 | 4.0 | 84.8 | 21.0 | 69.1 | 4.6 | 18.7 | 29.0 |
| Phi3-Vision (Abdin et al., 2024) | 4.2B | 10.6 | 58.9 | 9.0 | 6.1 | 81.1 | 29.8 | 58.9 | 9.0 | 25.3 | 21.3 |
| GLM-4V-9B (GLM et al., 2024) | 9B | 14.9 | 53.0 | 9.5 | 10.1 | 73.1 | 35.1 | 53.0 | 9.5 | 30.3 | 19.3 |
| InternLM-XComposer2-VL (Dong et al., 2024a) | 7B | 12.7 | 56.4 | 10.5 | 7.4 | 77.6 | 31.0 | 56.4 | 10.5 | 25.7 | 22.4 |
| InternVL2-8B (Chen et al., 2024b) | 8B | 26.6 | 45.5 | 13.5 | 19.8 | 51.6 | 44.9 | 45.5 | 13.5 | 38.1 | 7.0 |
| Qwen2-VL (Wang et al., 2024a) | 7B | 25.6 | 47.1 | 14.7 | 18.3 | 52.2 | 43.0 | 47.1 | 14.7 | 35.6 | 7.0 |
| _Open-source General MLLMs_ |  |  |  |  |  |  |  |  |  |  |  |
| G-LLaVA (Gao et al., 2023) | 13B | 6.5 | 64.2 | 4.6 | 4.2 | 86.6 | 22.3 | 64.2 | 4.6 | 20.0 | 36.0 |
| Math-LLaVA (Shi et al., 2024) | 13B | 11.1 | 62.1 | 3.6 | 9.3 | 72.8 | 31.3 | 62.1 | 3.6 | 29.5 | 13.9 |
| Math-PUMA-Qwen2-7B (Zhuang et al., 2024) | 7B | 19.2 | 47.8 | 13.7 | 12.4 | 67.8 | 41.0 | 47.8 | 13.7 | 34.1 | 11.4 |
| Math-PUMA-DeepSeek-Math-7B (Zhuang et al., 2024) | 7B | 15.6 | 56.0 | 7.2 | 12.0 | 67.4 | 35.8 | 56.0 | 7.2 | 32.2 | 12.4 |
| InfiMM-Math (Han et al., 2024) | 7B | 20.6 | 48.8 | 12.2 | 15.2 | 61.7 | - | - | - | - | - |
| URSA-7B | 7B | 32.2 | 37.5 | 10.7 | 26.9 | 48.2 | 53.5 | 37.5 | 10.7 | 48.2 | 7.0 |
| _Open-source Math MLLMs_ |  |  |  |  |  |  |  |  |  |  |  |
| Δ over SOTA Open-Source Math MLLMs | - | +11.6 | +10.3 | -7.1 | +11.7 | +13.5 | +12.5 | +10.3 | -7.1 | +14.1 | +4.4 |{{< /table-caption >}}
> 🔼 본 표는 WE-MATH 테스트 자료를 사용하여 폐쇄형 대규모 언어 모델(LLM)과 개방형 대규모 언어 모델(LLM)의 성능을 비교 분석한 결과를 보여줍니다.  평가는 WE-MATH에서 정의된 네 가지 차원(평균 정확도, 불완전한 지식, 부적절한 일반화, 완전한 숙달)을 기반으로 이루어졌습니다.  폐쇄형 LLM의 최고 성능은 녹색으로 강조 표시되었고, 개방형 LLM의 최고 및 차순위 성능은 각각 빨간색과 파란색으로 강조 표시되었습니다. 이를 통해 다양한 모델의 강점과 약점을 명확히 파악하고, 다차원적 평가 지표를 활용한 모델 성능 분석의 중요성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 2: The performance comparison with Closed-source MLLMs and Open-source MLLMs on four-dimensional metrics for WE-MATH testmini reasoning evaluation. The best results of Closed-source MLLMs are highlighted in green. The best and second-best results of Open-source MLLMs are highlighted in red and blue respectively.
> </details>

{{< table-caption >}}
| Model | ALL | PG | SG | AG | AL | PT | GT | AR |
|---|---|---|---|---|---|---|---|---|
| *Closed-source MLLMs* |  |  |  |  |  |  |  |  |
| GPT-4o | 63.7 | 56.8 | 52.0 | 61.0 | 76.9 | 51.8 | 58.1 | 61.5 |
| Claude-3.5-Sonnet | 64.8 | 49.9 | 49.3 | 55.3 | 81.0 | 44.1 | 69.4 | 61.2 |
| Geimini-1.5-Pro | 60.5 | 52.7 | 42.7 | 61.6 | 70.8 | 20.6 | 65.2 | 54.2 |
| *Open-source MLLMs* |  |  |  |  |  |  |  |  |
| Llava-v1.5-7B | 16.6 | 10.5 | 7.3 | 19.5 | 6.5 | 8.2 | 32.3 | 10.8 |
| Llava-v1.6-34B | 27.1 | 21.4 | 25.3 | 27.6 | 14.9 | 7.6 | 32.7 | 23.1 |
| Deepseek-VL-7B-chat | 21.5 | 16.0 | 13.3 | 26.5 | 12.9 | 4.7 | 32.3 | 12.7 |
| InternVL2-8B | 39.7 | 33.9 | 37.3 | 32.5 | 46.9 | 15.9 | 42.1 | 37.3 |
| Qwen2-VL | 42.1 | 40.3 | 38.7 | 39.9 | 37.1 | 8.2 | 44.8 | 39.2 |
| URSA-7B | 44.7 | 48.1 | 38.0 | 33.7 | 66.9 | 24.7 | 39.2 | 38.5 |{{< /table-caption >}}
> 🔼 본 표는 DYNAMATH 테스트 데이터 세트에서 오픈 소스 다중 모드 언어 모델(MLLM)과의 성능 비교를 보여줍니다.  각 모델의 전체 정확도와 기하학(PG), 입체기하(SG), 대수(AL), 퍼즐(PT), 그래프 이론(GT), 산술(AR), 과학 그림(SF), 통계(ST)와 같은 다양한 수학적 문제 유형에 대한 성능을 보여줍니다. 이 표는 URSA-7B 모델의 강점과 약점, 그리고 다른 오픈 소스 모델들과의 상대적 성능을 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Comparison with open-source MLLMs on DYNAMATH testmini dataset.
> </details>

{{< table-caption >}}
| Method | N=4 | N=8 | N=16 | N=32 | N=64 |
|---|---|---|---|---|---| 
| *MathVista-GPS* |  |  |  |  |  |
| Self-Consistency | 67.4 | 67.9 | 68.2 | 68.7 | 68.9 |
| URSA-RM-7B | **68.8** | **69.7** | **70.4** | **70.7** | **70.8** |
| *MathVerse* |  |  |  |  |  |
| Self-Consistency | 29.1 | 29.7 | 30.1 | 30.2 | 30.2 |
| URSA-RM-7B | **31.0** | **32.7** | **33.0** | **33.2** | **33.0** |{{< /table-caption >}}
> 🔼 표 4는 URSA-RM-7B 모델이 Multimath-7B 데이터셋에서 얼마나 잘 일반화(OOD, Out-of-Distribution)되는지 보여줍니다.  구체적으로, MathVista와 MathVerse 데이터셋의 GPS(Geometry Problem Solving) 과제에 대해 Self-Consistency 방법과 URSA-RM-7B의 성능을 비교하여, URSA-RM-7B가 테스트 시간 확장(test-time scaling)에 효과적임을 보여줍니다. 표는 서로 다른 샘플링 횟수(N)에 따른 정확도(Accuracy)를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 4: OOD performance when URSA-RM-7B works on Multimath-7B.
> </details>

{{< table-caption >}}
| Method | N=4 | N=8 | N=16 | N=32 | N=64 |
|---|---|---|---|---|---| 
| *MathVista-GPS* |  |  |  |  |  |
| URSA-RM-7B | **82.6** | **84.0** | **85.0** | **86.4** | **86.2** |
| URSA-RM-7B w/o \mathcal{S}_{BEL} | 80.1 | 81.7 | 82.2 | 83.1 | 83.0 |
| URSA-RM-7B w/o \mathcal{S}_{MIE} | 81.8 | 83.3 | 84.1 | 85.6 | 85.6 |
| *MathVerse* |  |  |  |  |  |
| URSA-RM-7B | **53.2** | **54.2** | **54.7** | **55.0** | **54.8** |
| URSA-RM-7B w/o \mathcal{S}_{BEL} | 49.9 | 50.7 | 51.8 | 52.0 | 52.1 |
| URSA-RM-7B w/o \mathcal{S}_{MIE} | 52.8 | 53.7 | 53.8 | 53.9 | 53.8 |{{< /table-caption >}}
> 🔼 표 5는 URSA-RM-7B 모델에 대한 ablation study 결과를 보여줍니다.  MathVista-GPS와 MathVerse 두 데이터셋에서  URSA-RM-7B 모델의 성능을 샘플링 횟수(N=4, 8, 16, 32, 64)를 변경하며 측정하고,  BinaryErrorLocating(SBEL)과 Misinterpretation Insertion Engine(SMIE)을 제거했을 때의 성능 변화를 비교 분석합니다.  각 샘플링 횟수에 따른 정확도 변화를 통해  SBEL과 SMIE의 효과를 정량적으로 평가하고 모델의 성능에 미치는 영향을 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Ablation study on URSA-RM-7B.
> </details>

{{< table-caption >}}
| Hyperparameters & Cost | Stage 1 | Stage 2 | Stage 3 |
|---|---|---|---| 
| Learning Rate | 1e-4 | 1e-5 | 5e-6 |
| Epoch | 1 | 2 | 2 |
| Warm-up Ratio | 0.02 | 0.02 | 0.02 |
| Weight Decay | 0.02 | 0.01 | 0.02 |
| Batch Size | 64 | 128 | 128 |
| Trainable Parts | Aligner | Vision Encoder, Aligner, Base LLM | Base LLM |
| Data Size | 960K | 1.0M | 1.1M |
| Time Cost | ~3.5h | ~11h | ~12h |{{< /table-caption >}}
> 🔼 표 6은 URSA-7B 모델 학습에 사용된 하이퍼파라미터 설정과 각 단계별 학습에 소요된 시간을 보여줍니다.  세 단계(Stage 1, Stage 2, Stage 3)의 학습 과정에서 사용된 학습률, 에포크 수, 웨이트 감쇠, 배치 크기, 학습 대상 파라미터, 데이터 크기, 학습 시간 등의 정보가 포함되어 있습니다. 이 표는 모델 학습 과정에 대한 세부적인 정보를 제공하여, 연구의 재현성을 높이는 데 기여합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Hyperparameter setting and training time cost.
> </details>

{{< table-caption >}}
| Model | #Params | ALL | ALG | ARI | GEO | LOG | NUM | SCI | STA |
|---|---|---|---|---|---|---|---|---|---| 
| *Baselines* |  |  |  |  |  |  |  |  |  |
| Random Choice | - | 17.9 | 25.8 | 13.8 | 22.7 | 13.4 | 8.8 | 15.8 | 14.3 |
| Human Performance | - | 60.3 | 50.9 | 59.2 | 51.4 | 40.7 | 53.8 | 64.9 | 63.9 |
| *Closed-source MLLMs* |  |  |  |  |  |  |  |  |  |
| Qwen-VL-Plus [2023] | - | 43.3 | 39.1 | 32.0 | 39.3 | 18.9 | 26.4 | 59.0 | 56.1 |
| GPT-4V [2023] | - | 49.9 | 53.0 | 49.0 | 51.0 | 21.6 | 20.1 | 63.1 | 55.8 |
| *Open-source Genreral MLLMs* |  |  |  |  |  |  |  |  |  |
| mPLUG-Owl2-7B [2023] | 7B | 22.2 | 23.6 | 19.2 | 23.9 | 13.5 | 12.7 | 26.3 | 21.4 |
| LLaVA-1.5-13B [2024c] | 13B | 25.7 | 19.6 | 28.6 | 17.6 | 10.8 | 27.8 | 33.6 | 22.9 |
| MiniGPT-v2 [2023] | 7B | 23.1 | 28.1 | 21.0 | 24.7 | 16.2 | 16.7 | 25.4 | 17.9 |
| InternLM-XComposer2-VL-7B [2024a] | 7B | 47.8 | 32.0 | 51.6 | 30.5 | 13.5 | 43.8 | 37.7 | 62.8 |
| SPHINX-MoE [2023] | 8x7B | 42.3 | 31.7 | 41.6 | 30.5 | 16.2 | 27.1 | 50.8 | 50.8 |
| DeepSeek-VL [2024] | 7B | 34.9 | 29.2 | 38.8 | 27.2 | 18.9 | 43.1 | 35.3 | 33.2 |
| InternVL2-8B [2024b] | 8B | 58.3 | 59.8 | 56.4 | 60.3 | 10.8 | 30.6 | 59.0 | 68.8 |
| Qwen2-VL [2024a] | 7B | 58.9 | 44.1 | 57.5 | 43.1 | 24.3 | 41.7 | 66.4 | 75.1 |
| *Open-source Math MLLMs* |  |  |  |  |  |  |  |  |  |
| G-LLaVA [2024] | 7B | 25.1 | 36.0 | 19.4 | 37.6 | 15.2 | 17.7 | 21.0 | 15.1 |
| Math-LLaVA [2024] | 7B | 46.6 | 51.5 | 40.7 | 56.2 | 23.3 | 34.7 | 47.7 | 42.3 |
| Multimath-7B [2024] | 7B | 50.0 | 61.9 | 42.2 | 64.9 | 23.3 | 32.6 | 42.6 | 49.2 |
| Math-PUMA-Qwen2-7B [2024] | 7B | 47.9 | 47.7 | 46.2 | 47.3 | 21.6 | 32.6 | 42.6 | 55.8 |
| URSA-7B | 7B | 59.8 | 74.0 | 53.5 | 77.4 | 21.6 | 35.4 | 58.2 | 57.1 |
| Δ over SOTA *Open-Source Math MLLMs* | - | +9.8 | +12.1 | +7.3 | +12.5 | -1.7 | +0.7 | +10.5 | +1.3 |{{< /table-caption >}}
> 🔼 표 7은 MATHVISTA 테스트 데이터셋을 기반으로 폐쇄형 및 개방형 다중모드 언어 모델(MLLM)의 수학적 능력을 비교한 표입니다.  'Close-source MLLMs' 와 'Open-source General MLLMs', 'Open-source Math MLLMs' 그룹으로 나뉘어 각 그룹 내 여러 모델들의 성능을 다양한 수학적 하위 과제(ALL, ALG, ARI, GEO, LOG, NUM, SCI, STA)별로 비교 분석합니다.  URSA-7B 모델의 성능이 다른 모델들에 비해 얼마나 우수한지, 특히 개방형 수학 MLLM들 중 최고 성능을 보이는 모델과 비교하여 얼마나 앞서는지를 명확히 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Comparison with close-source MLLMs open-source MLLMs on MATHVISTA testmini mathematics capabilities.
> </details>

{{< table-caption >}}
| Model | #Params | S1 | S2 | S3 | Mem UCU | Mem AL | PF CPF | PF UPF | SF CSF | SF USF | TMF BTF | TMF CCF | PD Dir | PD Pos | PD RoM | PD CCP |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| *Closed-source MLLMs* |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| GPT-4o (OpenAI, 2024) | - | 72.8 | 58.1 | 43.6 | 86.6 | 39.1 | 77.4 | 71.6 | 84.5 | 62.3 | 58.7 | 69.4 | 93.1 | 72.7 | 47.5 | 73.3 |
| GPT-4V (OpenAI, 2023) | - | 65.5 | 49.2 | 38.2 | 82.5 | 38.4 | 70.7 | 60.2 | 76.6 | 56.3 | 57.8 | 67.7 | 79.3 | 57.5 | 47.8 | 63.3 |
| Gemini-1.5-Pro (Team et al., 2023) | - | 56.1 | 51.4 | 33.9 | 51.0 | 31.2 | 61.8 | 45.0 | 70.0 | 57.5 | 39.2 | 62.7 | 68.8 | 54.1 | 40.7 | 60.0 |
| Qwen-VL-Max (Bai et al., 2023) | - | 40.8 | 30.3 | 20.6 | 19.4 | 25.3 | 39.8 | 41.4 | 43.6 | 48.0 | 43.8 | 43.4 | 41.4 | 35.1 | 40.7 | 26.7 |
| *Open-source General MLLMs* |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| InternVL-Chat-V1.5 (Chen et al., 2024a) | 26B | 49.4 | 30.6 | 28.5 | 44.0 | 29.8 | 52.2 | 52.1 | 44.2 | 48.2 | 47.1 | 65.7 | 50.5 | 36.5 | 36.7 |
| LLaVA-1.6 (Liu et al., 2024c) | 7B | 23.0 | 20.8 | 15.8 | 18.5 | 20.5 | 16.9 | 29.6 | 15.6 | 18.6 | 42.7 | 24.1 | 17.6 | 43.3 | 28.9 | 26.7 |
| LLaVA-1.6 (Liu et al., 2024c) | 13B | 29.4 | 25.3 | 32.7 | 21.7 | 23.2 | 23.4 | 34.7 | 25.3 | 26.4 | 37.5 | 41.7 | 26.9 | 28.9 | 37.1 | 30.0 |
| GLM-4V-9B (GLM et al., 2024) | 9B | 47.3 | 37.2 | 38.2 | 53.4 | 37.0 | 51.3 | 46.5 | 50.6 | 38.2 | 44.1 | 45.2 | 41.0 | 49.3 | 36.8 | 53.3 |
| MiniCPM-LLaMA3-V2.5 (Yao et al., 2024) | 8B | 39.8 | 31.1 | 29.7 | 28.6 | 37.0 | 40.8 | 39.8 | 41.0 | 38.6 | 32.0 | 42.7 | 41.0 | 42.7 | 44.0 | 43.3 |
| LongVA (Zhang et al., 2024c) | 7B | 43.5 | 30.6 | 28.5 | 24.5 | 39.8 | 45.1 | 40.8 | 51.9 | 42.5 | 45.6 | 44.6 | 44.5 | 40.7 | 47.5 | 20.0 |
| InternLM-XComposer2-VL (Dong et al., 2024a) | 7B | 47.0 | 33.1 | 33.3 | 31.3 | 46.5 | 47.7 | 42.6 | 51.4 | 43.9 | 41.1 | 50.6 | 65.5 | 53.9 | 55.2 | 40.0 |
| Phi3-Vision (Abdin et al., 2024) | 4.2B | 42.1 | 34.2 | 27.9 | 28.7 | 16.0 | 47.2 | 38.8 | 50.0 | 44.4 | 28.8 | 31.2 | 48.6 | 49.2 | 26.4 | 50.0 |
| DeepSeek-VL (Lu et al., 2024) | 7B | 32.6 | 26.7 | 25.5 | 16.6 | 35.1 | 27.3 | 38.0 | 24.2 | 38.7 | 50.0 | 23.3 | 24.5 | 41.0 | 51.7 | 23.3 |
| InternVL2-8B (Chen et al., 2024b) | 8B | 59.4 | 43.6 | 35.2 | 71.4 | 20.5 | 62.0 | 55.5 | 67.1 | 57.3 | 54.0 | 60.5 | 58.6 | 63.6 | 44.5 | 50.0 |
| Qwen2-VL (Wang et al., 2024a) | 7B | 59.1 | 43.6 | 26.7 | 62.7 | 37.2 | 62.6 | 60.8 | 65.7 | 49.2 | 52.5 | 49.2 | 48.1 | 68.2 | 55.0 | 56.7 |
| *Open-source Math MLLMs* |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |  |
| G-LLaVA (Gao et al., 2023) | 7B | 32.4 | 30.6 | 32.7 | 33.3 | 29.1 | 32.0 | 37.9 | 19.6 | 33.5 | 37.1 | 32.8 | 31.2 | 33.2 | 25.6 | 40.0 |
| Math-LLaVA (Shi et al., 2024) | 13B | 38.7 | 34.2 | 34.6 | 30.3 | 17.9 | 39.2 | 40.4 | 37.1 | 37.7 | 53.0 | 51.3 | 30.8 | 30.8 | 40.9 | 46.7 |
| Math-PUMA-Qwen2-7B (Zhuang et al., 2024) | 7B | 53.3 | 39.4 | 36.4 | 63.5 | 42.5 | 60.2 | 45.9 | 66.2 | 48.6 | 42.3 | 53.5 | 31.2 | 37.7 | 40.4 | 46.7 |
| MAVIS w/o DPO (Zhang et al., 2024d) | 7B | 56.9 | 37.1 | 33.2 | - | - | - | - | - | - | - | - | - | - | - | - |
| MAVIS (Zhang et al., 2024d) | 7B | 57.2 | 37.9 | 34.6 | - | - | - | - | - | - | - | - | - | - | - | - |
| URSA-7B | 7B | 63.1 | 56.4 | 41.8 | 59.1 | 32.5 | 72.3 | 60.3 | 70.9 | 66.0 | 51.4 | 59.8 | 58.3 | 39.5 | 58.8 | 53.3 |
| Δ over SOTA *Open-Source Math MLLMs* | - | +5.9 | +27.0 | +5.4 | -4.4 | -10.0 | +12.3 | +14.4 | +4.7 | +17.4 | -1.6 | +6.3 | +27.1 | +1.8 | +17.9 | +6.6 |{{< /table-caption >}}
> 🔼 표 8은 WE-MATH 테스트 데이터셋의 하위 집합에 대해 클로즈소스 및 오픈소스 MLLM의 정확도를 비교한 것입니다. 앞의 세 열은 각각 1단계, 2단계, 3단계 문제에 대한 전반적인 성능을 보여줍니다. 나머지 열들은 서로 다른 문제 해결 전략에서의 성능을 보여주기 위해 사용됩니다.  다양한 문제 유형과 난이도에 따른 모델의 성능을 자세히 분석하여, 모델의 강점과 약점을 파악하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Accuracy comparison with close-source MLLMs and open-source MLLMs on WE-MATH testmini subset. First 3 columns show the overall performance on one-step, two-step and three-step problems. The other columns are used to demonstrate the performance in different problem strategies.
> </details>

{{< table-caption >}}
| Model | #Params | ALL | Elementary School | High School | Undergraduate |
|---|---|---|---|---|---| 
| _Closed-source MLLMs_ |  |  |  |  |  |
| GPT-4o (OpenAI, 2024) | - | 63.7 | 68.6 | 61.8 | 36.8 |
| Claude-3.5-Sonnet (Anthropic, 2024) | - | 64.8 | 66.7 | 62.6 | 33.3 |
| Gemini-1.5-Pro (Team et al., 2023) | - | 60.5 | 62.9 | 59.2 | 37.1 |
| _Open-sourced MLLMs_ |  |  |  |  |  |
| Llava-v1.5-7B (Liu et al., 2024c) | 7B | 16.6 | 18.9 | 13.3 | 11.7 |
| Llava-v1.6-34B (Liu et al., 2024c) | 34B | 27.1 | 35.9 | 23.8 | 16.6 |
| Deepseek-VL-7B-Chat (Lu et al., 2024) | 7B | 21.5 | 28.3 | 19.0 | 16.0 |
| InternVL2-8B (Chen et al., 2024b) | 8B | 39.7 | 51.1 | 37.4 | 19.6 |
| Qwen2-VL (Wang et al., 2024a) | 7B | 42.1 | 47.6 | 42.2 | 24.4 |
| URSA-7B | 7B | 44.7 | 53.5 | 44.3 | 41.8 |{{< /table-caption >}}
> 🔼 표 9는 DYNAMATH 테스트 데이터셋을 기반으로, 지식 수준(초등, 중등, 고등)별로 다양한 크기의 언어 모델들의 성능을 비교 분석한 표입니다.  근접 비교 대상으로는 클로즈소스 대형 언어 모델과 오픈소스 대형 언어 모델이 포함되어 있으며, 각 지식 수준에서의 정확도를 종합적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Comparison with close-source MLLMs open-source MLLMs on DYNAMATH testmini based on knowledge level.
> </details>

{{< table-caption >}}
| Model | Size | Accuracy |
|---|---|---|
| **_Baselines_** |  |  |
| Random Choice | - | 17.1 |
| Human | - | 92.3 |
| UniMath (Liang et al., 2023) | - | 50.0 |
| **_Closed-source MLLMs_** |  |  |
| GPT-4V (OpenAI, 2023) | - | 45.2 |
| **_Open-source MLLMs_** |  |  |
| LLaVA-1.5 (Liu et al., 2024b) | 13B | 20.3 |
| G-LLaVA (Gao et al., 2023) | 7B | 64.2 |
| G-LLaVA (Gao et al., 2023) | 13B | 67.0 |
| Math-PUMA-DeepSeek-Math-7B (Zhuang et al., 2024) | 7B | 61.8 |
| Math-PUMA-Qwen2-7B (Zhuang et al., 2024) | 7B | 63.6 |
| Multimath (Peng et al., 2024) | 7B | 67.7 |
| MAVIS-7B w/o DPO (Zhang et al., 2024d) | 7B | 66.7 |
| MAVIS-7B (Zhang et al., 2024d) | 7B | 68.3 |
| URSA-7B | 7B | 73.5 |
| Δ over SOTA _Open-Source MLLMs_ | - | +5.2 |{{< /table-caption >}}
> 🔼 표 10은 GeoQA 벤치마크에서 다양한 다중 모달 대규모 언어 모델(MLLM)의 성능을 비교한 표입니다.  GeoQA는 기하학 문제 해결 능력을 평가하는 벤치마크이며, 표에는 다양한 MLLM의 정확도가 모델 크기별로 제시되어 있습니다.  이를 통해 다양한 MLLM의 기하학적 추론 능력을 상대적으로 비교하고, URSA-7B 모델의 성능을 다른 모델과 비교하여 그 우수성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Performance comparison of different MLLMs on GeoQA.
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