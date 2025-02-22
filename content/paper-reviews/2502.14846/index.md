---
title: "Scaling Text-Rich Image Understanding via Code-Guided Synthetic Multimodal Data Generation"
summary: "CoSyn: 코드 기반 합성 데이터 생성으로 텍스트 풍부 이미지 이해 혁신!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Vision-Language Models", "🏢 University of Pennsylvania",]
showSummary: true
date: 2025-02-20
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.14846 {{< /keyword >}}
{{< keyword icon="writer" >}} Yue Yang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-21 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.14846" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.14846" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/scaling-text-rich-image-understanding-via" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

텍스트가 풍부한 이미지(차트, 문서 등)를 이해하는 것은 컴퓨터 비전 분야의 중요한 과제입니다. 하지만, 이러한 유형의 데이터는 부족하고 다양성이 떨어져 기존의 비전-언어 모델(VLMs)은 성능 저하를 겪습니다. 이 논문은 이러한 문제를 해결하기 위해 **코드 기반 합성 데이터 생성 시스템인 CoSyn**을 제시합니다.



CoSyn은 **LLM(대규모 언어 모델)의 코드 생성 기능**을 이용해 다양한 도메인의 텍스트가 풍부한 이미지를 자동 생성합니다.  Python, HTML, LaTeX 등 다양한 언어를 지원하며, 생성된 코드는 이미지 렌더링과 VLMs 학습을 위한 텍스트 설명 생성에 활용됩니다.  실험 결과, CoSyn으로 생성된 데이터로 학습된 모델은 기존 최고 성능 모델들을 능가하며, 특히 새로운 도메인에서 뛰어난 제로샷 성능을 보였습니다.  **CoSyn은 데이터의 다양성과 품질을 높여 VLMs의 성능 향상과 새로운 응용 분야 개척에 기여**합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} CoSyn은 **LLM의 코드 생성 능력**을 활용, **다양한 텍스트가 풍부한 이미지 데이터셋**을 자동 생성합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 합성 데이터로 학습된 모델은 **기존 최첨단 모델들을 능가**하는 성능을 보이며, **새로운 영역(NutritionQA)에서도 우수한 제로샷 성능**을 달성했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} CoSyn은 **데이터 효율성이 높고 새로운 영역에 대한 적응력이 뛰어나** 실제 환경 적용 가능성을 제시합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **텍스트가 풍부한 이미지 이해를 위한 합성 데이터 생성 시스템인 CoSyn**을 제시하여, 기존의 제한된 데이터셋 문제를 해결하고 **최첨단 성능을 달성**함으로써 컴퓨터 비전 및 자연어 처리 분야 연구자들에게 중요한 의미를 가집니다. **CoSyn은 다양한 유형의 텍스트가 풍부한 이미지를 생성하고, 이를 활용한 모델 학습을 통해 실제 환경에서의 적용 가능성을 높였습니다.**  향후 연구로는 CoSyn의 확장성 및 다양한 응용 분야에 대한 추가 연구가 기대됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.14846/x1.png)

> 🔼 그림 1은 영양 정보에 대한 질문에 답하는 등의 새로운 작업이 주어지면 코드 기반 생성 시스템이 특정 작업에 대한 VLM의 성능을 향상시키기 위해 표적 합성 데이터를 생성할 수 있음을 보여줍니다. 이 시스템은 자연어 질의를 사용하여 영양 정보 레이블과 같이 텍스트가 풍부한 이미지를 생성하는 코드(예: Python, HTML, LaTeX)를 생성합니다. 생성된 코드는 합성 이미지의 텍스트 표현으로 사용되며, 이를 통해 VLM의 교육을 위한 고품질 지시 조정 데이터를 생성합니다. 이 그림은 코드 기반 합성 데이터 생성의 개념과 VLM 성능 향상에 미치는 영향을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Given a novel task (e.g., answering questions about nutrition facts), our code-guided generation system can produce targeted synthetic data to enhance the performance of VLMs on that specific task.
> </details>





{{< table-caption >}}
| Model | ChartQA | DocVQA | InfoVQA | TableVQA | AI2D | TextVQA | ScreenQA | Average |
|---|---|---|---|---|---|---|---|---|
| GPT-4V | 78.1 | 87.2 | 75.1 | 60.5 | 89.4 | 78.0 | 41.6 | 72.8 |
| Gemini 1.5 Flash | 85.4 | 89.9 | 75.3 | 72.6 | 91.7 | 78.7 | 40.1 | 76.2 |
| Claude-3 Opus | 80.8 | 89.3 | 55.6 | 70.0 | 88.1 | 67.5 | 39.8 | 70.2 |
| PaliGemma-3B<sup>†</sup> | 71.4 | 84.8 | 47.8 | 46.4 | 73.3 | 76.5 | 32.2 | 61.8 |
| BLIP-3-4B<sup>†</sup> | 60.0 | 61.4 | 31.5 | 24.3 | 74.2 | 71.0 | 26.2 | 49.8 |
| Cambrian-7B<sup>†</sup> | 73.3 | 77.8 | 41.6 | 40.6 | 73.0 | 71.7 | 44.4 | 64.2 |
| LLaVA-1.5-7B<sup>†</sup><sup>∗</sup> | 17.8 | 28.1 | 25.8 | 33.1 | 55.5 | 58.2 | 17.6 | 33.7 |
| LLaVA-Next-8B<sup>†</sup> | 69.5 | 78.2 | 43.8 | 43.9 | 71.6 | 65.3 | 34.2 | 58.1 |
| LLaVA-OneVision-7B<sup>†</sup> | 80.0 | 87.5 | 68.8 | 64.6 | 81.4 | 78.3 | 46.3 | 72.4 |
| Pixtral-12B | 81.8 | 90.7 | 50.8 | 67.0 | 79.0 | 75.7 | 39.4 | 69.2 |
| Llama 3.2 11B | 83.4 | 88.4 | 63.6 | 51.1 | 91.9 | 73.1 | 87.7 | 77.0 |
| Ours (7B)<sup>†</sup> | 86.3 | 90.0 | 70.5 | 65.8 | 91.9 | 82.0 | 80.1 | 80.9 |
| Ours (7B-zero-shot)<sup>†</sup><sup>∗</sup> | 80.8 | 82.9 | 59.8 | 64.9 | 83.9 | 72.7 | 78.1 | 74.7 |{{< /table-caption >}}

> 🔼 표 1은 7가지 텍스트가 풍부한 벤치마크에 대한 다양한 비전-언어 모델의 성능을 보여줍니다.  최고 성능의 오픈소스 모델 결과는 굵게 표시되었고, 두 번째로 좋은 성능은 밑줄이 그어져 있습니다.  † 표시는 다중 모드 학습을 위해 오픈 데이터 및 코드를 사용한 모델임을 나타내고, * 표시는 평가 데이터셋의 인스턴스로 학습되지 않은 제로샷 모델임을 의미합니다.  즉, 이 표는 제로샷 설정과 다양한 학습 데이터를 사용한 설정 모두에서 다양한 모델들의 성능을 비교 분석하여, 제안된 방법의 효과성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Results on 7 text-rich benchmarks. The result of the best-performing open-source model is bold, and the second-best is underlined. Models with † stand for open data and code for multimodal training. Models with ∗ are zero-shot models, which means the models are not trained on instances from any of the evaluation datasets.
> </details>





### In-depth insights


#### Synthetic Data Boost
본 논문에서 제시된 합성 데이터 증강(Synthetic Data Boost) 전략은 **기존의 제한된 실제 데이터셋의 한계를 극복**하기 위한 효과적인 방법으로 제시됩니다.  **다양한 유형의 시각적 데이터를 생성**하여 모델의 일반화 능력을 향상시키는 데 중점을 두고 있으며, 특히 **텍스트가 풍부한 이미지 이해**에 있어서 뛰어난 성능 향상을 보여줍니다.  실험 결과는 합성 데이터로 학습된 모델이 기존 오픈소스 모델은 물론, 상용 모델들보다도 우수한 성능을 보임을 보여줍니다.  이러한 결과는 **합성 데이터의 효율성과 질적 우수성**을 강조하며, **데이터 부족 문제를 해결**하는 실용적인 전략임을 시사합니다.  더 나아가, 이 방법은 **새로운 도메인에 대한 적응력 향상**에도 기여함으로써, **실제 환경에서의 활용 가능성**을 높이는 데 크게 기여할 수 있습니다.  결론적으로 합성 데이터 증강 전략은 **데이터 확보의 어려움을 해결하고 모델 성능을 개선**하는 데 있어서 매우 중요한 역할을 수행한다는 것을 알 수 있습니다.

#### CoSyn Framework
CoSyn 프레임워크는 **텍스트 기반의 거대 언어 모델(LLM)**을 활용하여 **합성 텍스트-이미지 데이터셋**을 생성하는 혁신적인 시스템입니다.  LLM의 코드 생성 능력을 활용, 다양한 도메인(예: 영양 정보 레이블, 책 표지)을 설명하는 텍스트 입력을 받아 Python, HTML, LaTeX 등 여러 언어로 이미지 렌더링 코드를 생성합니다. 생성된 코드는 이미지를 렌더링하는데 사용될 뿐만 아니라, **LLM을 이용한 텍스트 기반 지시 사항 생성**에도 활용됩니다. 이를 통해 CoSyn은 **다양하고 고품질의 지시 튜닝 데이터셋**을 생성하며, 기존의 텍스트-이미지 데이터셋의 한계를 극복하고 **시각적 언어 모델(VLM)**의 성능 향상에 크게 기여합니다.  특히, CoSyn은 단순한 VQA(Visual Question Answering) 뿐만 아니라, **포인팅 데이터 생성**까지 지원하여 실제 환경에서 작동하는 다중 모드 에이전트 개발의 가능성을 보여줍니다.  **데이터 효율성**과 **새로운 도메인에 대한 적응력** 또한 탁월하며, **편향 완화**에도 기여하는 점이 핵심적인 강점입니다.

#### Zero-Shot Learning
제로샷 학습은 모델이 훈련 중에 보지 못한 새로운 클래스의 데이터를 분류하거나 예측할 수 있는 능력을 말합니다. 이는 **데이터 부족** 문제를 해결하고 **모델의 일반화 능력**을 높이는 데 중요한 역할을 합니다.  본 논문에서 제시된 코드 기반 합성 데이터 생성 방법은 제로샷 학습 성능 향상에 기여할 수 있습니다. **합성 데이터**를 통해 다양하고 풍부한 데이터를 생성하여 모델이 다양한 상황에 적응하고 **과적합을 방지**할 수 있기 때문입니다.  특히, 텍스트와 이미지가 결합된 데이터셋에서 제로샷 성능은 **텍스트 이해 능력**과 **이미지 인식 능력**의 조화에 달려있으며, 본 논문의 방법은 이 두 가지 능력을 모두 향상시키는 데 도움이 됩니다.  **새로운 도메인이나 과제에 대한 적응력**을 높이는 데 효과적이며,  실제 환경에서 모델의 유용성을 높일 수 있는 **실용적인 측면**도 갖추고 있습니다.  하지만, 합성 데이터의 품질과 다양성이 제로샷 학습 성능에 큰 영향을 미치므로,  **데이터 생성 과정의 개선**은 지속적인 연구가 필요한 부분입니다.

#### Bias Mitigation
본 논문에서 다룬 바와 같이, **합성 데이터는 편향 완화에 중요한 역할**을 합니다. 기존의 학술 데이터셋은 종종 편향된 훈련 데이터에 과적합되어 템플릿이나 기계 생성 질문에서는 성능이 뛰어나지만, 보다 현실적인 사람이 질문한 질문에는 어려움을 겪는 경우가 많습니다. 반면, **CoSyn과 같은 합성 데이터 생성 시스템을 사용하면 이러한 편향을 완화**하고 모델의 일반화 능력을 향상시킬 수 있습니다. 특히, CoSyn은 다양한 질문 유형과 렌더링 파이프라인을 통해 다양한 합성 데이터를 생성하며, **특정 작업에 맞춘 데이터를 생성하여 모델의 성능을 크게 향상**시킬 수 있습니다.  **영양 정보 레이블 이해와 같은 새로운 작업에 대한 제로샷 일반화 능력 향상**에도 효과적임을 보여줍니다. 따라서, 합성 데이터의 적절한 활용을 통해 **보다 공정하고 정확하며 일반화 능력이 뛰어난 비전-언어 모델**을 개발할 수 있습니다.

#### Future Research
본 논문에서 제시된 코드 기반 합성 데이터 생성 시스템(CoSyn)은 텍스트가 풍부한 이미지에 대한 VLM의 성능을 향상시키는 데 효과적임을 보여주었습니다. 하지만, **합성 데이터의 품질은 프롬프트 엔지니어링과 렌더링 파이프라인에 크게 의존**하므로, 향후 연구는 **다양한 도메인에 대한 합성 데이터 생성의 어려움을 해결**하는 데 집중해야 합니다. 특히, **희귀하거나 과소 표현된 도메인**에 대한 합성 데이터 생성은 어려운 과제이며, 이를 위해서는 **프롬프트 엔지니어링 기술의 개선** 또는 **새로운 렌더링 도구의 개발**이 필요합니다. 또한, **실제 데이터의 복잡성을 완벽하게 포착**하지 못하는 합성 데이터의 한계를 극복하기 위해, **실제 데이터와 합성 데이터의 결합** 또는 **합성 데이터의 현실성을 높이는 기술 개발** 등에 대한 연구가 필요합니다.  마지막으로, 현재 영어에 한정된 합성 데이터를 **다국어 지원**하도록 확장하는 연구도 중요한 과제입니다.  **이러한 연구를 통해 CoSyn의 효율성과 일반화 능력을 더욱 향상**시킬 수 있을 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.14846/x2.png)

> 🔼 그림 2는 본 논문에서 제안하는 코드 기반 합성 데이터 생성 시스템(CoSyn)의 개요를 보여줍니다. CoSyn은 11가지 렌더링 도구를 기반으로 20가지 생성 파이프라인을 가지고 있습니다. 사용자의 질의(예: '책 표지')가 주어지면 CoSyn은 적절한 파이프라인을 선택하고 다양한 주제를 생성합니다. 이때 주제 생성은 여러 persona를 고려하여 이루어집니다. 그 후 코드 생성을 위한 세부 데이터를 합성하고, 생성된 코드를 사용하여 이미지를 렌더링합니다. 마지막으로 생성된 코드를 LLM에 입력하여 instruction-tuning 데이터를 생성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: The overview of our Code Guided Synthetic data generation system (CoSyn), which has 20 generation pipelines based on 11 render tools. Given a user query, e.g., “book cover,” CoSyn selects the appropriate pipelines and starts with generating diverse topics conditioned on personas, then synthesizes detailed data for code generation. The code renders the image and is also fed as context for an LLM to construct instruction-tuning data.
> </details>



![](https://arxiv.org/html/2502.14846/x3.png)

> 🔼 그림 3은 본 논문에서 제시하는 CoSyn-400K 데이터셋에 대한 개요를 보여줍니다. 이 데이터셋은 텍스트가 풍부한 이미지 9가지 종류(문서, 차트, 표, 다이어그램, 수학 문제, 벡터 그래픽, 악보, 회로도, 화학 구조)를 포함하며, 총 40만 장의 이미지와 270만 개의 instruction-tuning 데이터를 포함하고 있습니다. 그림에는 각 카테고리에 대한 이미지 예시가 포함되어 있으며, 부록 C의 그림 12-18에서 더 자세한 질의응답 예시를 확인할 수 있습니다.  즉, 다양한 유형의 텍스트가 포함된 이미지와 해당 이미지에 대한 질문과 답변의 쌍으로 구성된 대규모 합성 데이터셋임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Our CoSyn-400K dataset consists of 9 categories of text-rich images with 2.7M instruction-tuning data. More qualitative examples, along with question-answer annotations, are available in Figure 12 -18 in Appendix C.
> </details>



![](https://arxiv.org/html/2502.14846/x4.png)

> 🔼 그림 4는 다양한 학습 데이터 조합에 따른 모델 성능 변화를 보여줍니다.  Aux는 보조 데이터셋, Syn은 합성 데이터셋, Eval은 평가 데이터셋을 나타냅니다. 8가지 벤치마크에 대한 평균 점수를 제시하며, 각 벤치마크별 상세 성능 분석은 표 7에 수록되어 있습니다.  합성 데이터의 효과를 평가하기 위해, 보조 데이터셋만, 합성 데이터셋만, 보조 및 평가 데이터셋, 평가 및 보조 데이터셋, 평가 및 보조 데이터셋과 합성 데이터셋을 함께 사용한 네 가지 경우의 성능을 비교합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Ablation on training data selection. Aux, Syn, and Eval stand for auxiliary, synthetic, and evaluation datasets, respectively. We report the average score on eight benchmarks. The detailed performance breakdown on each benchmark is in Table 7.
> </details>



![](https://arxiv.org/html/2502.14846/x5.png)

> 🔼 그림 5는 NutritionQA 데이터셋에 대한 제로샷 성능을 보여줍니다. x축은 instruction-tuning 단계에서 사용된 훈련 예제의 수를 나타내고, y축은 정확도를 나타냅니다. 그림은 다양한 비전-언어 모델이 제로샷 환경에서 NutritionQA 데이터셋에 대해 얼마나 잘 일반화되는지 보여줍니다. 왼쪽 상단에 있는 모델들이 데이터 효율성이 더 높다는 것을 보여줍니다. 즉, 적은 양의 훈련 데이터로도 높은 성능을 달성할 수 있음을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Zero shot performance on NutritionQA. The x-axis denotes the number of training examples used for the instruction-tuning stage. The models on the upper left side demonstrate better data efficiency.
> </details>



![](https://arxiv.org/html/2502.14846/x6.png)

> 🔼 그림 6은 Chain-of-Thought(CoT) 추론 사용 여부에 따른 성능 변화를 보여줍니다.  'Short Answer'는 모델이 가능한 짧게 답변하도록 유도하는 프로 ンプ트 방식이고, '+ CoT'는 최종 답변을 제시하기 전에 CoT 추론 과정을 거치도록 하는 프로 ンプ트 방식입니다.  두 방식의 성능 비교는 다양한 데이터셋(ChartQA, TableVQA, NutritionQA 등)에서 이루어졌으며, 자세한 결과는 표 6에 제시되어 있습니다.  간단히 말해, 이 그림은  문제 해결 과정을 단계적으로 설명하는 CoT 방식과 간결한 답변만 요구하는 방식의 성능 차이를 다양한 데이터셋에서 비교 분석한 결과를 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Ablation of using Chain-of-Thought reasoning. Short Answer represents prompting model to output the answer as short as possible. +++ CoT stands for providing Chain-of-Thought reasoning before giving the final answer. Results on all datasets are in Table 6.
> </details>



![](https://arxiv.org/html/2502.14846/x8.png)

> 🔼 그림 7은 합성 데이터를 사용하여 VLMs(Vision-Language Models)이 이미지 내 특정 지점을 가리키도록 하는 방법을 보여줍니다. (a)는 LLM(Large Language Model)을 프롬프트하여 지점을 가리키는 질문을 생성하고, 코드를 수정하여 답변 지점을 명확하게 그리는 합성 지점 데이터 생성 과정을 보여줍니다. (b)는 합성 지점 데이터로 학습된 VLM이 실제 에이전트 작업으로 일반화될 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: The overview of enabling VLMs to point through synthetic data. (a) We synthesize pointing data by prompting an LLM to generate pointing questions and edit the code to draw the answer points explicitly. (b) We demonstrate that the VLM trained on synthetic pointing data can be generalized to real agentic tasks.
> </details>



![](https://arxiv.org/html/2502.14846/x9.png)

> 🔼 그림 8은 CoSyn 시스템의 HTML 문서 파이프라인에 사용된 프롬프트 템플릿을 보여줍니다. 이 그림은 데이터 생성의 네 가지 단계(주제, 데이터, 코드, 지침)를 모두 포함합니다. 각 단계마다 사용되는 프롬프트의 예시가 제시되어 있어, CoSyn이 어떻게 다양한 텍스트 기반 이미지를 생성하는지 이해하는 데 도움을 줍니다. 특히, 주제 생성 단계에서는 사용자의 페르소나를 고려한 다양한 주제를 생성하고, 데이터 생성 단계에서는 현실적인 데이터를 생성하며, 코드 생성 단계에서는 HTML 및 CSS를 사용하여 이미지를 렌더링하고, 마지막으로 지침 생성 단계에서는 이미지에 대한 다양한 질문과 답변을 생성하는 과정을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Prompt templates used for HTML Document Pipeline, including all four stages of generation: topic, data, code, and instruction.
> </details>



![](https://arxiv.org/html/2502.14846/x10.png)

> 🔼 이 그림은 합성 데이터의 크기가 ChartQA 작업에서 제로샷 성능에 미치는 영향을 보여줍니다.  여러 개의 합성 이미지로 미세 조정된 모델의 제로샷 ChartQA 성능을 평가하여 합성 데이터의 양이 증가함에 따라 성능이 향상됨을 보여줍니다. 이는 더 많은 양의 합성 데이터를 사용하면 모델의 일반화 능력이 향상될 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Scaling the Size of Synthetic Data. We evaluate the zero-shot performance on ChartQA of models fine-tuned on increasing numbers of synthetic images.
> </details>



![](https://arxiv.org/html/2502.14846/x11.png)

> 🔼 그림 10은 논문에서 새롭게 수집한 NutritionQA 데이터셋의 예시들을 보여줍니다.  영양 정보 라벨이 있는 식품 사진들과 이에 대한 질문과 답변 쌍으로 구성되어 있습니다. 각각의 예시는 실제 영양 정보 라벨 사진과, 그 사진에 대한 질문 (예: ‘콜레스테롤의 1일 권장 섭취량을 충족하려면 몇 회분을 먹어야 합니까?’), 그리고 그 질문에 대한 답변으로 이루어져 있습니다. 이는 비전-언어 모델이 실제 세계의 복잡한 시각적 정보를 이해하고 추론하는 능력을 평가하는 데 사용됩니다. 다양한 유형의 영양 정보 라벨과 질문 유형을 포함하여 모델의 일반화 능력을 테스트합니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Examples from our newly collected NutritionQA dataset.
> </details>



![](https://arxiv.org/html/2502.14846/x12.png)

> 🔼 그림 11은 본 논문에서 새롭게 수집한 DocPointQA 데이터셋의 예시들을 보여줍니다. DocPointQA는 문서 이미지에서 특정 요소를 가리키는 질문에 답하는 작업을 위한 데이터셋입니다. 그림에는 다양한 유형의 문서 이미지와 각 이미지에 대한 질문과 답변이 함께 제시되어 있습니다. 이를 통해 모델이 문서 이미지를 이해하고 특정 요소를 정확하게 지정할 수 있는 능력을 평가할 수 있습니다. 그림의 예시들은 질문에 대한 답변을 생성하는 데 필요한 시각적 및 언어적 추론 능력을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Examples from our newly collected DocPointQA dataset.
> </details>



![](https://arxiv.org/html/2502.14846/x13.png)

> 🔼 그림 12는 본 논문에서 제시하는 합성 차트 데이터의 무작위 예시들을 보여줍니다. 다양한 유형의 차트(막대형, 선형, 원형, 산점도 등)와 시각적 스타일, 그리고 다양한 데이터 값들을 포함하고 있습니다. 이 그림은 본 논문에서 제안하는 합성 데이터 생성 방법의 다양성과 질을 보여주는 데 목적이 있습니다. 각 차트는 질문과 답변 쌍과 함께 제공되어, 시각 언어 모델의 학습 및 평가에 활용될 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Randomly selected examples from our synthetic chart data.
> </details>



![](https://arxiv.org/html/2502.14846/x14.png)

> 🔼 그림 13은 본 논문에서 제시하는 합성 문서 데이터셋에서 무작위로 선택한 샘플들을 보여줍니다. 다양한 형태의 문서(예: 회의록, 마케팅 자료, 안전 점검표 등)가 포함되어 있으며, 각 문서는 실제 문서와 유사한 레이아웃과 내용을 가지고 있습니다. 이는 다양한 유형의 시각적 정보를 포함하는 문서에 대해서도 VLM(Vision-Language Model)이 효과적으로 작동할 수 있도록 하는 데 목적이 있습니다. 그림은 각 문서의 시각적 내용과 해당 내용에 대한 질문과 답변을 함께 제시하여, VLM이 시각 정보와 텍스트 정보를 통합적으로 이해할 수 있는지 확인하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 13: Randomly selected examples from our synthetic document data.
> </details>



![](https://arxiv.org/html/2502.14846/x15.png)

> 🔼 그림 14는 본 논문에서 제시하는 합성 표 데이터셋에서 무작위로 선택한 몇몇 예시들을 보여줍니다. 각 예시는 다양한 스타일과 내용을 가진 표를 보여주며, 이는 다양한 시각적 디자인과 텍스트 정보를 활용하여 생성되었습니다. 이러한 데이터는 시각 언어 모델이 표 데이터를 이해하고 추론하는 능력을 향상시키는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 14: Randomly selected examples from our synthetic table data.
> </details>



![](https://arxiv.org/html/2502.14846/x16.png)

> 🔼 그림 15는 본 논문에서 제시하는 합성 수학 데이터의 무작위 예시들을 보여줍니다.  다양한 수학 문제 유형과 난이도를 포함하며,  문제와 답변 쌍으로 구성되어 있습니다. 이러한 합성 데이터는 시각적 추론과 수학적 계산 능력을 평가하는 시각-언어 모델 학습에 활용됩니다. 각 예시는 문제와 함께, 수학적 개념이나 방정식을 시각적으로 표현하거나,  문제 해결을 위한 단계별 설명을 제공하는 등 다양한 형태를 갖고 있습니다. 이를 통해 모델이 다양한 유형의 수학 문제를 이해하고,  추론 능력을 향상시키는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 15: Randomly selected examples from our synthetic math data.
> </details>



![](https://arxiv.org/html/2502.14846/x17.png)

> 🔼 이 그림은 논문에서 합성적으로 생성된 다이어그램 데이터의 무작위 예시들을 보여줍니다. 다이어그램은 다양한 종류의 정보를 시각적으로 표현하는 데 사용되며, 각각의 다이어그램은 특정한 목적이나 과제를 가지고 있습니다. 이러한 다이어그램들은 자연어 처리 모델이 복잡한 정보를 이해하고 추론하는 능력을 평가하는 데 사용될 수 있습니다. 그림은 모델이 다이어그램의 구조와 내용을 얼마나 잘 이해하는지, 그리고 이를 바탕으로 질문에 정확하게 답변할 수 있는지를 보여주는 여러 예시들을 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 16: Randomly selected examples from our synthetic diagram data.
> </details>



![](https://arxiv.org/html/2502.14846/x18.png)

> 🔼 그림 17은 본 논문에서 제시하는 합성 벡터 그래픽 데이터의 무작위 예시들을 보여줍니다.  각 이미지는 다양한 벡터 그래픽 유형(원뿔, 좌표계, 그래프 등)을 나타내며, 각 이미지에 대한 질문과 답변 쌍이 함께 제공되어 시각적 추론 능력을 평가하는 데 사용됩니다. 이러한 합성 데이터는 다양한 유형의 시각적 질문에 대한 모델의 일반화 성능을 향상시키는 데 기여합니다.
> <details>
> <summary>read the caption</summary>
> Figure 17: Randomly selected examples from our synthetic vector graphic data.
> </details>



![](https://arxiv.org/html/2502.14846/x19.png)

> 🔼 그림 18은 CoSyn 시스템을 사용하여 생성된 합성 데이터셋에서 무작위로 선택된 악보, 회로도, 화학 구조식의 예시를 보여줍니다. 각 이미지는 해당 도메인의 특징을 잘 나타내는 다양한 시각적 요소와 텍스트를 포함하고 있습니다. 이 그림은 CoSyn이 다양한 유형의 텍스트가 풍부한 이미지를 생성할 수 있는 능력을 보여주는 증거이며, 다양한 응용 분야에서 시각적 언어 모델을 교육하는 데 사용될 수 있는 다양한 합성 데이터를 생성할 수 있음을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 18: Randomly selected examples from our synthetic sheet music, circuits and chemical structures.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| ChartQA | Average | Machine | Human | Δ↓ |
|---|---|---|---|---|
| PaliGemma-3B | 71.4 | 88.5 | 54.2 | 34.3 |
| ChartPali-5B | 77.3 | 93.7 | 60.9 | 32.8 |
| Ours (w/o Syn) | 81.4 | 92.2 | 70.4 | 21.8 |
| Ours (w/ Syn) | 86.3 | 93.4 | 79.1 | 14.2 |{{< /table-caption >}}
> 🔼 표 2는 ChartQA 데이터셋의 질문 유형을 사람이 작성한 질문과 기계가 생성한 질문으로 나누어 성능을 비교 분석한 결과를 보여줍니다. 위쪽의 원형 차트는 학습 및 테스트 데이터셋에서 두 가지 질문 유형의 비율을 보여줍니다.  Δ(작을수록 좋음)는 사람이 작성한 질문과 기계가 생성한 질문 간의 성능 차이를 나타냅니다. 이 표는 기계가 생성한 질문에 대해 모델이 얼마나 과적합되는지, 그리고 사람이 작성한 질문에 대한 일반화 능력은 어느 정도인지를 보여주는 데 중점을 둡니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Results on human and machine-generated questions of ChartQA. The pie charts above display the percentage distribution of two question types in training and testing. ΔΔ\Deltaroman_Δ (↓↓\downarrow↓ lower is better) denotes the performance gap between human and machine questions.
> </details>

{{< table-caption >}}
| **Model** | **Mobile** |  | **Desktop** |  | **Web** |  | **Avg** |
|---|---|---|---|---|---|---|---| 
|  | **Text** | **Icon** | **Text** | **Icon** | **Text** | **Icon** |  |
| GPT-4o | 20.2 | 24.9 | 21.1 | 23.6 | 12.2 | 7.8 | 18.3 |
| CogAgent | 67.0 | 24.0 | 74.2 | 20.0 | 70.4 | 28.6 | 47.4 |
| SeeClick | 78.0 | 52.0 | 72.2 | 30.0 | 55.7 | 32.5 | 53.4 |
| UGround | 82.8 | 60.3 | 82.5 | 63.6 | 80.4 | 70.4 | 73.3 |
| Synthetic | 90.8 | 53.3 | 78.4 | 58.6 | 80.0 | 47.1 | 68.0 |
| Human | 84.2 | 59.0 | 88.1 | 52.9 | 76.5 | 50.5 | 68.5 |
| Combined | 89.0 | 65.1 | 87.6 | 65.7 | 83.0 | 58.7 | 74.9 |{{< /table-caption >}}
> 🔼 표 3은 ScreenSpot 데이터셋에서의 클릭 정확도를 보여줍니다.  모델은 다양한 포인팅 데이터 (PixMo-point의 사람이 직접 주석을 단 데이터 포함)를 사용하여 학습되었으며, Human은 PixMo-point(Deitke et al., 2024)의 사람이 주석을 단 데이터를 사용한 결과를, Combined는 사람이 주석을 단 데이터와 합성 데이터를 함께 사용한 결과를 나타냅니다.  Human-annotated 데이터와 합성 데이터를 결합한 결과가 어떻게 성능 향상에 기여하는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Click accuracy on ScreenSpot. We report our models trained on different pointing data. Human stands for using the human-annotated data from PixMo-point Deitke et al. (2024). Combined means combining human-annotated data with our synthetic pointing data.
> </details>

{{< table-caption >}}
| Dataset | Image Diversity | Text Diversity |
|---|---|---|
| FigureQA | 0.268 | 0.567 |
| DVQA | 0.307 | 0.752 |
| PlotQA | 0.420 | 0.743 |
| ChartQA | 0.340 | 0.742 |
| Ours (Charts) | **0.596** | **0.823** |{{< /table-caption >}}
> 🔼 표 4는 서로 다른 차트 데이터셋에서 이미지와 텍스트 다양성을 비교한 결과를 보여줍니다. 각 데이터셋에서 무작위로 1만 개의 인스턴스를 샘플링하여 결과를 계산했습니다. 이미지 다양성은 CLIP을 사용하여 이미지 특징을 추출하고, 텍스트 다양성은 Sentence-BERT를 사용하여 질문과 답변 쌍의 임베딩을 얻어 계산되었습니다. 결과는 FigureQA, DVQA, PlotQA 및 ChartQA 데이터셋과 비교하여 제시됩니다. 이를 통해 본 연구에서 생성한 합성 차트 데이터의 이미지 및 텍스트 다양성이 기존 데이터셋보다 훨씬 높다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Compare image and text diversity across different chart datasets. We randomly sample 10K instances from each dataset to compute the results.
> </details>

{{< table-caption >}}
| n. of Tools | Diversity | ChartQA |  |  |
|---|---|---|---|---|
| Single | 0.572 | 73.9 | 66.5 | 81.5 |
| Multiple | **0.607** | **75.2** | **68.6** | **82.0** |{{< /table-caption >}}
> 🔼 표 5는 데이터 생성을 위한 단일 렌더링 도구와 다중 렌더링 도구 사용의 효과를 비교 분석한 결과를 보여줍니다. 각각의 경우 45,000개의 합성 이미지를 사용했습니다. 단일 도구 조건에서는 Matplotlib만을 사용했고, 다중 도구 조건에서는 HTML, LaTeX, Plotly, VegaLite를 추가적으로 사용했습니다. 이를 통해 다양한 시각적 표현 방식이 모델 성능에 미치는 영향을 파악하고, 다양한 도구 활용의 효과를 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Single vs. Multiple Rendering Tools for Data Generation. Each row uses the same number of 45K synthetic images. Single only uses Matplotlib, while Multiple involves four other rendering tools: HTML, LaTex, Plotly, and VegaLite.
> </details>

{{< table-caption >}}
| Prompt Type | ChartQA | DocVQA | InfoVQA | TableVQA | AI2D | TextVQA | ScreenQA | NutritionQA |
|---|---|---|---|---|---|---|---|---|
| CoT | **86.3** | 87.4 | 63.8 | **65.8** | 86.0 | 70.9 | 79.0 | **76.0** |
| Short Answer | 83.1 | **90.0** | **70.5** | 64.3 | **91.9** | **82.0** | **80.1** | 62.0 |{{< /table-caption >}}
> 🔼 표 6은 프롬프트에서 chain-of-thought (CoT) 추론을 사용했을 때의 영향을 보여줍니다. CoT는 모델이 최종 답변을 제공하기 전에 추론 단계를 제공하도록 하는 것을 의미합니다. 짧은 답변은 모델이 가능한 한 적은 단어로 답변하도록 하는 것을 의미합니다. 이 표는 두 가지 프롬프트 유형(CoT 및 짧은 답변)에 대한 7가지 텍스트 기반 벤치마크의 결과를 비교 분석하여 CoT 추론이 모델 성능에 미치는 영향을 평가합니다. 각 벤치마크에 대한 자세한 내용은 본문을 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Table 6: Alation of using chain-of-thought (CoT) in prompts. CoT means letting the model provide reasoning steps before giving the final answer. Short Answer prompts the model to answer with as few words as possible.
> </details>

{{< table-caption >}}
| FT Data | ChartQA | DocVQA | InfoVQA | TableVQA<sup>†</sup> | AI2D | TextVQA | ScreenQA<sup>†</sup> | Average |
|---|---|---|---|---|---|---|---|---|
| Aux only<sup>∗</sup> | 60.7 | 56.2 | 39.7 | 43.1 | 81.7 | 68.5 | 61.3 | 58.7 |
| Syn only<sup>∗</sup> | 79.4 | 80.5 | 60.1 | 64.4 | 68.6 | 63.6 | 76.6 | 70.5 |
| Aux + Syn<sup>∗</sup> | 80.8 | 82.9 | 59.8 | 64.9 | 83.9 | 72.7 | 78.1 | 74.7 |
| Eval only | 77.4 | 87.4 | 63.8 | 51.8 | 91.3 | 81.1 | 78.1 | 75.9 |
| Eval + Aux | 81.4 | 87.9 | 68.2 | 53.6 | 91.6 | 81.8 | 77.0 | 77.3 |
| Eval + Aux + Syn | **86.3** | **90.0** | **70.5** | **65.8** | **91.9** | **82.0** | **80.1** | **80.9** |{{< /table-caption >}}
> 🔼 표 7은 지도 학습 미세 조정을 위한 데이터 선택에 대한 절삭 연구 결과를 보여줍니다. Aux, Syn, Eval은 각각 보조, 합성, 평가 데이터셋을 나타냅니다. ∗ 표시가 있는 행은 평가 데이터셋의 학습 예시를 사용하지 않은 제로샷 모델을 나타냅니다. † 표시가 있는 데이터셋은 테스트 전용 데이터셋(학습 분할 없음)으로, 해당 데이터셋의 모든 수치는 제로샷 성능을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Alation of the data selection for supervised fine-tuning. Aux, Syn, and Eval stand for auxiliary, synthetic, and evaluation datasets, respectively. The rows with ∗ represent zero-shot models (without using any training examples from any of the evaluation datasets). The datasets with † are test-only datasets (no training splits), which means all numbers on these datasets are zero-shot performance.
> </details>

{{< table-caption >}}
| LLM for Data Generation | ChartQA | ChartQA | ChartQA |
|---|---|---|---|
|  | Average | Machine | Human |
| GPT-4o | 72.4 | 65.8 | 78.9 |
| Claude-3.5-sonnet | 77.2 | 71.0 | 83.8 |{{< /table-caption >}}
> 🔼 이 표는 합성 데이터 생성에 사용된 두 가지 대규모 언어 모델(LLM)인 GPT-40과 Claude-3.5-Sonnet의 성능을 비교 분석한 결과를 보여줍니다. 두 모델 모두 10만 개의 합성 차트를 생성하여 VLMs(Vision-Language Models)를 미세 조정하는 데 사용되었으며, ChartQA(Chart Question Answering) 벤치마크를 사용하여 제로샷(zero-shot) 평가 결과를 보고합니다.  제로샷 평가는 모델이 평가 데이터셋의 예시를 사전에 학습하지 않고 평가를 수행하는 방식입니다. 이를 통해 각 LLM이 생성한 합성 데이터의 질과 VLMs 성능 향상에 미치는 영향을 비교 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Compare the LLMs used for synthetic data generation. For both LLMs, we create 100K synthetic charts for fine-tuning the VLMs. We report the zero-shot evaluation results on ChartQA.
> </details>

{{< table-caption >}}
| Pointing Data | Precision | Recall | F1 | Distance ↓ |
|---|---|---|---|---|
| PixMo-point | 49.7 | 49.3 | 52.7 | 17.3 |
| Synthetic (Ours) | 63.8 | 66.1 | 62.8 | 9.2 |
| Combined (Ours) | **69.9** | **70.6** | **70.7** | **8.8** |{{< /table-caption >}}
> 🔼 표 9는 DocPointQA에 대한 제로샷 포인팅 결과를 보여줍니다. 서로 다른 포인팅 데이터로 학습된 모델들을 비교합니다. Combined는 Deitke et al.(2024)의 사람이 주석을 단 PixMo-point 데이터와 본 연구의 합성 데이터를 결합한 것을 의미합니다.  표는 각 모델의 정밀도, 재현율, F1 점수, 그리고 예측 지점과 실제 지점 간의 L2 거리를 보여줍니다. 낮은 L2 거리는 더 나은 성능을 나타냅니다. 이 표는 합성 포인팅 데이터가  포인팅 성능 향상에 효과적임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Zero-shot Pointing on DocPointQA. We compare the models trained on different pointing data. Combined stands for combining PixMo-point (human-annotated) Deitke et al. (2024) with our synthetic data.
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