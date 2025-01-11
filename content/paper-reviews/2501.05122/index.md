---
title: "Centurio: On Drivers of Multilingual Ability of Large Vision-Language Model"
summary: "Centurio: 100개 언어를 지원하는 최첨단 다국어 비전-언어 모델 개발 성공!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Vision-Language Models", "🏢 WüNLP",]
showSummary: true
date: 2025-01-09
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.05122 {{< /keyword >}}
{{< keyword icon="writer" >}} Gregor Geigle et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-10 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.05122" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.05122" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/centurio-on-drivers-of-multilingual-ability" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

최근 비전-언어 모델(VLM)은 주로 영어 데이터로 학습되어 **다국어 지원이 부족**하고, **다양한 언어의 입력에 대한 이해도가 낮고 원하는 언어로 출력 생성이 어려운 문제점**이 있습니다. 기존 연구들은 다국어 학습 데이터를 추가하는 방법을 제시했지만, 체계적인 연구는 부족했습니다. 

본 논문에서는 **대규모 다국어 VLM을 위한 훈련 전략**에 대한 포괄적인 연구를 수행했습니다. 13가지 하위 작업과 43개 언어를 사용하여 다양한 훈련 전략 (훈련 언어 수, 언어별 데이터 분포, 지시 튜닝 데이터)을 체계적으로 실험했습니다. 그 결과, 영어 성능 저하 없이 최대 100개 언어를 포함하여 다국어 성능을 크게 향상시킬 수 있다는 것을 발견했습니다. 또한, **영어 데이터 비율을 25~50%로 줄이면서 다국어 성능 향상**을 달성했으며, **다국어 OCR 데이터를 포함하면 이미지 내 다국어 텍스트 이해 능력을 향상시킬 수 있다는 것을 밝혔습니다.** 이러한 결과를 바탕으로 100개 언어를 지원하는 다국어 VLM인 Centurio를 개발하여 14개 작업과 56개 언어를 포함한 평가에서 최첨단 성능을 달성했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 100개 언어를 동시에 학습시켜도 영어 성능 저하 없이 다국어 성능을 크게 향상시킬 수 있음 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 다국어 데이터 비율을 25~50%로 제한해도 다국어 성능을 크게 향상시킬 수 있음 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} Centurio 모델은 14개의 하위 작업과 56개 언어를 포함한 평가에서 최첨단 성능을 달성함 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **다국어 비전-언어 모델의 훈련 전략에 대한 포괄적인 조사**를 제시하여 다국어 능력 향상에 대한 새로운 통찰력을 제공합니다. 이는 **대규모 다국어 데이터셋 구축의 어려움과 비용을 줄이는 효율적인 방법**을 제시하며, **비전-언어 모델의 다국어 성능 향상**에 크게 기여할 수 있습니다. 또한, 본 연구는 향후 다국어 모델 개발 및 연구 방향을 제시하여 연구자들에게 중요한 지침을 제공할 것입니다.  특히, **저자원 언어에 대한 성능 향상**은 다국어 자연어 처리 분야의 발전에 큰 영향을 미칠 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2501.05122/x1.png)

> 🔼 본 그림은 다국어 대규모 비전-언어 모델의 다국어 능력에 영향을 미치는 요인들을 보여줍니다.  (1)은 모델 학습에 사용된 언어들을 계층적으로 보여주는 그림입니다.  (2)는 학습 데이터에서 각 언어의 비율을 나타내는 그림이고,  (3)은 영어 이외의 언어로 작성된 이미지 내 텍스트를 이해하기 위해 다국어 OCR 샘플을 통합하는 방법을 보여줍니다. 이를 통해 다국어 모델 학습 전략에 대한 종합적인 연구를 수행했음을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  Exploring drivers of multilingual ability: (1) Languages in the training data; (2) Distribution of languages in the training data; (3) Incorporating multilingual OCR samples to understand non-English text in images.
> </details>





{{< table-caption >}}
| Train Lang. | T1 | T2 | T3 | T4 | T5 | en |
|---|---|---|---|---|---|---|
| **All tasks** |  |  |  |  |  |  |
| English | 14.4 | 30.4 | 24.4 | 23.6 | 28.5 | 53.6 |
| T5 | 16.5 | 31.0 | 26.3 | 26.7 | 34.0 | 53.7 |
| T5-4 | 17.4 | 30.6 | 27.9 | **29.6** | 33.5 | 51.5 |
| T5-3 | 17.7 | 31.4 | **32.1** | 29.0 | 34.1 | 52.7 |
| T5-2 | 17.0 | **34.5** | 30.0 | 28.2 | 33.4 | **54.1** |
| L100 | **19.3** | 32.6 | 30.7 | 28.9 | **34.4** | 52.6 |
| **Tasks unaffected by language fidelity** |  |  |  |  |  |  |
| English | 33.0 | 32.5 | 36.3 | 38.5 | **42.9** | 55.7 |
| T5 | 35.3 | 33.2 | 36.4 | 38.7 | 42.4 | 56.0 |
| T5-T4 | 35.8 | 32.6 | 37.8 | **40.1** | 42.2 | 55.7 |
| T5-T3 | 35.9 | 33.6 | **40.5** | 39.7 | 42.6 | **56.3** |
| T5-T2 | 35.2 | **36.5** | 38.5 | 39.5 | 42.8 | 55.5 |
| L100 | **36.1** | 34.3 | 39.1 | 39.8 | 42.7 | 54.6 |{{< /table-caption >}}

> 🔼 이 표는 다양한 언어 집합으로 훈련된 모델에 대한 결과를 보여줍니다.  점수는 언어 계층별로 그룹화된 모든 작업의 결과를 평균한 것입니다.  XM3600, MaXM, MTVQA 작업은 언어 충실도에 영향을 받습니다. 즉, 이러한 작업의 성능은 모델이 지정된 언어로 출력을 생성하는 능력에 따라 달라질 수 있습니다.  표는 다양한 언어 집합을 사용하여 학습된 대규모 비전-언어 모델의 다국어 능력을 평가한 결과를 제시합니다.
> <details>
> <summary>read the caption</summary>
> (a)  Scores are averaged over results from all tasks grouped by language tier. The performance on the following tasks is affected by language fidelity: XM3600, MaXM, MTVQA.
> </details>





### In-depth insights


#### Multilingual LVLM Training
다국어 LVLMs(대규모 비전-언어 모델) 학습은 영어 데이터에 편향된 기존 접근 방식의 한계를 극복하기 위한 중요한 연구 분야입니다. **본 논문에서는 다국어 LVLMs의 효과적인 학습 전략을 심층적으로 조사하여 다양한 언어의 데이터 분포가 모델 성능에 미치는 영향을 체계적으로 분석합니다.**  특히, 영어 데이터 비율과 비영어 데이터의 언어 분포 최적화를 통해 다국어 이해 능력을 향상시키는 방법을 제시합니다. **놀랍게도, 영어 데이터 비율이 25-50%만 되어도 영어 성능을 유지하면서 다국어 성능을 크게 향상시키는 것을 발견했습니다.**  또한, 다국어 OCR(광학 문자 인식) 데이터를 학습에 포함하면 다국어 이미지 내 텍스트 이해 능력이 향상됨을 보여줍니다. **본 연구는 다국어 LVLMs 학습에 대한 깊이 있는 통찰력을 제공하며, 효율적인 다국어 학습 전략을 수립하는 데 중요한 지침을 제공합니다.**  **100개 언어를 포함하는 대규모 다국어 LVLM인 Centurio를 학습하여 우수한 성능을 달성함으로써 이러한 발견의 실용적인 영향을 보여줍니다.**  이는 향후 다국어 LVLMs 개발 및 응용에 중요한 기여를 할 것으로 기대됩니다.

#### Optimal Data Mix
본 논문에서 다루는 

#### OCR Data Impact
본 논문에서 다룬 OCR 데이터의 영향에 대한 심층적인 분석은 **다국어 OCR 데이터를 사전 훈련 및 지시 튜닝에 포함시키는 것이 다국어 텍스트-이미지 이해 능력 향상에 매우 중요함**을 보여줍니다. 특히, **영문 데이터를 기계 번역한 저품질 데이터라도 상당한 성능 향상**을 가져온다는 점을 주목할 필요가 있습니다.  **라틴 문자 기반 언어에는 효과적이나 다른 문자 시스템을 사용하는 언어에는 효과가 제한적**이라는 점 또한 중요한 통찰력입니다. 이는 **다국어 OCR 데이터의 품질과 다양성이 다국어 LVLMs의 성능에 큰 영향**을 미침을 시사하며, 앞으로 고품질 다국어 OCR 데이터 구축 및 활용에 대한 연구가 더욱 필요함을 강조합니다.  **합성 데이터가 성능 향상에 효과적**임을 보여주는 부분은 **데이터 확보의 어려움을 해결**하는 실질적인 방안을 제시한다는 점에서 매우 고무적입니다.

#### Centurio: A Case Study
Centurio에 대한 심층 연구는 다양한 언어 및 비전-언어 모델의 능력을 향상시키기 위한 훈련 전략에 대한 통찰력 있는 분석을 제공합니다. **Centurio는 다양한 언어로 된 방대한 데이터셋을 사용하여 훈련되었으며, 영어 이외의 데이터 비중을 조정함으로써 다양한 언어에 대한 성능을 크게 향상시켰습니다.** 연구는 또한 이미지 내의 다국어 텍스트 이해도 향상을 위한 전략을 제시하며, 합성 다국어 OCR 데이터를 활용하는 방법을 보여줍니다. **이러한 접근법은 영어 성능을 유지하면서 다국어 성능을 크게 향상시킨다는 점에서 주목할 만합니다.** Centurio는 여러 비전-언어 작업에서 최첨단 성능을 달성하며, 다국어 모델의 효율성과 효과에 대한 중요한 시사점을 제공합니다. **특히, 저자들은 최적의 훈련 데이터 구성을 위한 지침을 제시함으로써 다국어 모델 개발의 실질적인 과제를 해결하는 데 기여합니다.**  이 연구는 다국어 및 다문화적 이해를 갖춘 강력한 비전-언어 모델 개발에 대한 귀중한 지식을 제공합니다.

#### Future Work
본 논문은 다국어 대규모 비전-언어 모델의 훈련 전략에 대한 포괄적인 조사를 제시합니다. **다국어 OCR 데이터를 사전 훈련 및 지시 튜닝에 포함하는 것이 다국어 이미지 내 텍스트 이해를 향상시키는 데 매우 중요하다는 것을 발견했습니다.** 또한, 영어 성능을 저하시키지 않으면서 다국어 성능을 크게 향상시키기 위해 비영어 데이터의 최소 25-50%를 사용하여 최대 100개의 훈련 언어를 동시에 포함할 수 있습니다.  미래 연구는 **기계 번역 데이터의 품질 문제를 해결하고 다양한 언어의 고품질 다국어 데이터를 확보하는 데 집중해야 합니다.**  또한, **문화적 다양성을 고려한 다문화적 훈련**을 통해 모델의 지식을 확장하고, **다양한 스크립트를 포함하는 이미지 내 다국어 텍스트 이해 능력을 개선**하기 위한 연구가 필요합니다.  마지막으로, **본 연구에서 얻은 결과들을 다양한 LLM 백본 및 추가 작업(예: 이미지 분류)에 적용**하는 것이 필요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2501.05122/extracted/6121021/img/smpqa/bar_plot_1_en.png)

> 🔼 그림 2는 본 논문의 실험에 사용된 다양한 데이터셋에 대한 프롬프트들을 보여줍니다. M3Exam과 xMMMU 데이터셋의 경우 질문에 이미지가 포함되어 있고, 선택지 또한 이미지일 수 있습니다. M3Exam의 경우 최대 8개의 이미지와 8개의 선택지, xMMMU의 경우 최대 4개의 이미지와 4개의 선택지가 포함될 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Prompts used for the different datasets of our test suite. For M3Exam and xMMMU, the questions contain images at individual positions, and also the options can consist of images. In total, a sample of M3Exam can contain up to 8 images and 8 options, and a sample of xMMMU can contain up to 4 images and 4 options.
> </details>



![](https://arxiv.org/html/2501.05122/extracted/6121021/img/smpqa/bar_plot_1_id.png)

> 🔼 이 그림은 논문의 SMPQA(Synthetic Multilingual Plot Question Answering) 데이터셋에 대한 설명 그림입니다. 영어로 된 막대 그래프를 보여주며, 이 그래프에 대한 두 가지 유형의 질문을 제시합니다. 첫 번째는 Grounding 질문으로, 특정 막대의 크기나 색상에 대한 질문입니다. 예를 들어, '보상(reward) 막대가 가장 큰가?' 와 같은 질문입니다. 두 번째는 Reading 질문으로, 막대의 레이블이나 색상에 대한 질문입니다. 예를 들어, '가장 큰 막대의 레이블은 무엇인가?' 와 같은 질문입니다.  이 그림은 다국어 이해 능력을 평가하기 위한 SMPQA 데이터셋의 구성과 질문 유형을 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> (a) Example of a bar plot in SMPQA for English.  Questions for Grounding: 'Is the bar with label ’reward’ the biggest?', 'Is the bar with label ’incredible’ the biggest?', 'Is the bar with label ’reverse’ the smallest?', 'Is the bar with label ’sunset’ the smallest?', 'Is the bar with label ’closed’ colored in yellow?', 'Is the bar with label ’closed’ colored in purple?', 'Is the bar with label ’twitter’ colored in purple?', 'Is the bar with label ’twitter’ colored in red?'  Questions for Reading: 'What is the label of the biggest bar?', 'What is the label of the smallest bar?', 'What is the label of the yellow bar?', 'What is the label of the red bar?', 'What is the label of the purple bar?'
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Train Lang. | T1 | T2 | T3 | T4 | T5 | en |
|---|---|---|---|---|---|---|
| English | 0.2 | 0.2 | 0.1 | 2.4 | 6.2 | 100.0 |
| T5 | 39.1 | 36.1 | 82.2 | 83.9 | **99.1** | 100.0 |
| T5-T4 | 61.8 | 84.6 | 87.5 | **99.2** | 98.4 | 100.0 |
| T5-T3 | **72.9** | 84.4 | **98.2** | 95.2 | 97.9 | 100.0 |
| T5-T2 | 68.5 | **99.0** | 97.9 | 98.4 | 98.1 | 100.0 |
| L100 | **72.9** | 98.2 | 95.4 | 97.8 | 98.2 | 100.0 |{{< /table-caption >}}
> 🔼 표 1b는 XM3600 데이터셋에 대한 각 언어 모델의 평균 언어 충실도를 백분율(%)로 나타낸 것입니다. 언어 충실도는 모델이 입력된 언어로 올바른 출력을 생성하는 능력을 측정하는 지표입니다.  즉, 이 표는 각 언어 모델이 지정된 언어로 얼마나 정확하게 답변을 생성하는지 보여줍니다.  수치가 높을수록 해당 언어에 대한 모델의 언어 충실도가 높다는 것을 의미합니다. 이 표는 다양한 언어 모델의 다국어 성능을 비교하는 데 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> (b) Average language fidelity on XM3600 in %.
> </details>

{{< table-caption >}}
| English % | T1 | T2 | T3 | T4 | T5 | en |
|---|---|---|---|---|---|---|
| 1 | 19.1 | 30.3 | 28.8 | 27.1 | 31.7 | 48.9 |
| 10 | 18.1 | 32.4 | 29.4 | 27.4 | 32.5 | 50.1 |
| 25 | 19.7 | 35.5 | 29.9 | 27.9 | 33.0 | 50.3 |
| 50 | 19.3 | 32.6 | 30.7 | 28.9 | 34.4 | 52.6 |
| 75 | 18.5 | 31.5 | 30.7 | 28.4 | 34.6 | 54.1 |
| 90 | 15.9 | 31.2 | 27.6 | 26.9 | 34.1 | 54.8 |{{< /table-caption >}}
> 🔼 표 1은 다양한 언어 집합으로 훈련된 모델에 대한 RQ1(§2.2) 결과를 보여줍니다. 이 표는 다양한 크기의 언어 집합으로 사전 훈련된 비전-언어 모델의 성능을 비교 분석한 것입니다. 각 열의 최고 및 차고 성능이 강조 표시되어 있습니다.  다시 말해, 이 표는 영어만 포함한 모델, 영어와 소수의 고자원 언어를 포함한 모델,  그리고 다양한 저자원 언어를 광범위하게 포함한 모델 등 다양한 훈련 데이터 조합으로 학습된 모델의 성능을 비교하여 최적의 다국어 모델 훈련 전략을 파악하기 위한 실험 결과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: RQ1 (§2.2) results for models trained with different sets of languages. We emphasize the best and second-best result in each column.
> </details>

{{< table-caption >}}
| English % | T1 | T2 | T3 | T4 | T5 | en |
|---|---|---|---|---|---|---|
| No pre-training | 19.3 | 32.6 | 30.7 | 28.9 | 34.4 | 52.6 |
| 100 | 19.3 | 33.3 | 32.1 | 29.4 | 34.5 | **55.2** |
| 50 | **22.8** | **39.5** | **33.8** | 30.8 | **35.7** | 54.9 |
| 1 | 22.7 | 38.9 | 33.7 | **31.2** | 35.4 | 55.1 |{{< /table-caption >}}
> 🔼 본 표는 instruction-tuning 단계에서 영어 데이터와 다국어 데이터의 비율을 다르게 하여 학습시킨 모델들의 결과를 보여줍니다.  각 언어 계층(language tier)별로 모든 과제(task)의 점수를 평균하여 제시합니다. 다국어 데이터의 비율을 조절함으로써 다양한 언어의 성능에 미치는 영향을 분석하는 데 사용됩니다.  RQ2는 다국어 능력에 대한 영향을 확인하기 위해,  Instruction-tuning 데이터 내 영어와 다국어 데이터의 비율이 모델의 성능에 미치는 영향을 조사하는 연구 질문입니다.
> <details>
> <summary>read the caption</summary>
> Table 2: RQ2 (§2.3) results for models trained with different ratios of English to multilingual data in the instruction-tuning phase. Scores are averaged over results from all tasks grouped by language tier.
> </details>

{{< table-caption >}}
| Setup | SMPQA Ground |  |  | SMPQA Read |  |  |
|---|---|---|---|---|---|---|
|  | en | Latin | other | en | Latin | other |
| No pre-training | 69.6 | 67.2 | 51.9 | 33.4 | 12.8 | 0.1 |
| No OCR | 76.1 | 73.0 | 55.3 | 41.8 | 23.1 | 0.2 |
| 100% Eng. | 78.4 | 74.7 | 57.9 | 55.8 | 39.9 | 3.9 |
| 50% Eng. | 81.2 | 76.7 | 60.0 | 53.8 | 41.8 | 7.1 |
| 50% (frozen) | 76.1 | 70.8 | 56.3 | 47.2 | 34.1 | 3.5 |
| 1% Eng. | 81.0 | 78.3 | 64.1 | 54.8 | 43.5 | 8.0 |
| Latin down | 78.9 | 74.2 | 59.5 | 54.6 | 41.0 | 9.9 |{{< /table-caption >}}
> 🔼 본 표는 논문의 2.4절에서 언급된, 다양한 영어-다국어 비율(L100)로 사전 학습을 수행했을 때의 결과를 보여줍니다. 모든 변형은 동일하게 지시어 미세 조정(L100, 50% 영어) 되었습니다.  표는 사전 학습 단계에서 영어 데이터 비율을 다르게 하여(1%, 50%, 100%) 다국어 능력에 미치는 영향을 분석한 것입니다.  즉, 사전 학습 데이터의 다국어 비율을 변경함으로써 최종 모델 성능에 어떤 영향을 주는지 실험한 결과를 보여줍니다.  이 표는 본 연구에서 제시하는 다국어 LVLMs 훈련 전략에 대한 주요 발견 중 하나를 뒷받침하는 증거입니다.
> <details>
> <summary>read the caption</summary>
> Table 3: RQ3 (§2.4) results with different English-to-multilingual ratios (L100) for pre-training. All variants are identically instruction-tuned (L100, 50% En.).
> </details>

{{< table-caption >}}
## Table 1:  Performance Comparison of Different LLMs on Various Visual Question Answering Benchmarks

| Model Name | AVG. | XM3600 en | XM3600 mul | XM3600 fid. | MT-VQA | SMPQA G. en | SMPQA G. mul | SMPQA N. en | SMPQA N. mul | M3Exam en | M3Exam mul | xMMMU en | xMMMU mul | C-VQA |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Parrot | 25.8 | 5.6 | 0.4 | 25.0 | 2.0 | 51.0 | 49.9 | 0.0 | 0.0 | 46.6 | 36.2 | 35.3 | 32.4 | 41.1 |
| PALO 7B | 28.7 | 65.9 | 13.5 | 72.0 | 5.8 | 55.5 | 52.8 | 22.4 | 2.7 | 41.0 | 29.1 | 31.8 | 30.9 | 37.1 |
| PALO 13B | 29.9 | 67.3 | 17.0 | 60.1 | 6.3 | 54.0 | 51.5 | 25.6 | 4.0 | 45.2 | 28.3 | 32.4 | 28.9 | 39.6 |
| Llama-Vision 3.2 11B | *32.3 | 35.9 | 7.2 | 33.3 | 15.2 | 91.1 | 84.8 | 58.4 | 22.8 | - | - | - | - | 38.8 |
| Maya | 33.4 | 55.9 | 14.6 | 65.7 | 5.3 | 51.4 | 50.9 | 14.6 | 1.8 | 49.2 | 36.3 | 37.9 | 33.3 | 39.8 |
| Pixtral 12B | 38.1 | 26.5 | 22.1 | 96.8 | 14.1 | 91.1 | 71.0 | 85.0 | 35.9 | 49.4 | 33.7 | 30.3 | 26.2 | 33.5 |
| Phi 3.5 Vision | 39.5 | 32.3 | 6.3 | 40.8 | 11.1 | 92.2 | 79.4 | 84.8 | 35.9 | 56.3 | 40.7 | 41.7 | 37.4 | 40.9 |
| Qwen2VL 2B | 41.2 | 68.8 | 5.2 | 13.2 | 19.0 | 85.0 | 83.5 | 68.8 | 47.4 | 47.9 | 40.5 | 36.8 | 35.5 | 33.6 |
| MiniCPM 2.6 | 41.7 | 87.5 | 14.2 | 92.3 | 16.1 | 89.0 | 74.3 | 80.8 | 39.3 | 55.0 | 48.2 | 39.1 | 36.5 | 34.1 |
| InternVL 2.5 4B | 45.3 | 38.9 | 17.5 | 91.0 | 25.1 | 87.0 | 78.3 | 77.8 | 47.5 | 63.2 | 50.3 | 49.2 | 42.7 | 48.1 |
| InternVL 2.5 8B | 47.4 | 38.3 | 15.7 | 91.1 | 25.0 | 91.0 | 79.2 | 80.6 | 48.2 | 67.0 | 53.3 | 50.7 | 45.2 | 48.6 |
| Qwen2VL 7B | 47.7 | 50.3 | 24.6 | 90.0 | 23.2 | 91.2 | 90.9 | 85.0 | 64.9 | 56.1 | 49.7 | 43.0 | 40.7 | 37.6 |
| Pangea | 48.2 | 70.1 | 34.6 | 87.9 | 19.3 | 87.2 | 72.2 | 72.0 | 23.8 | 58.0 | 45.5 | 43.1 | 42.0 | 55.2 |
| Centurio Aya | 48.5 | 78.4 | 39.2 | 95.7 | 11.1 | 83.1 | 74.2 | 60.0 | 30.1 | 53.0 | 41.2 | 37.6 | 37.2 | 49.4 |
| Centurio Qwen | 51.6 | 79.1 | 34.4 | 95.2 | 11.9 | 84.8 | 76.1 | 65.2 | 31.7 | 61.2 | 46.9 | 46.4 | 43.0 | 52.9 |

| Model Name | MAXM en | MAXM mul | xGQA en | xGQA mul | BIN-MC en | BIN-MC mul | XVNLI en | XVNLI mul | MaRVL en | MaRVL mul | VGR en | VGR mul | VLOD en | VLOD mul |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Parrot | 28.2 | 3.6 | 37.7 | 21.2 | 30.5 | 25.7 | 28.7 | 31.4 | 63.5 | 55.1 | 59.2 | 52.9 | 0.0 | 0.0 |
| PALO 7B | 54.0 | 22.5 | 59.1 | 36.6 | 58.7 | 38.6 | 58.0 | 53.4 | 62.7 | 24.1 | 48.3 | 25.6 | 5.8 | 6.8 |
| PALO 13B | 51.7 | 33.1 | 58.0 | 27.8 | 61.4 | 41.1 | 56.6 | 53.6 | 63.8 | 33.1 | 63.3 | 26.2 | 2.5 | 4.9 |
| Llama-Vision 3.2 11B | 0.0 | 4.7 | 39.3 | 27.6 | 75.6 | 50.8 | - | - | - | - | - | - | - | - |
| Maya | 55.4 | 17.3 | 58.2 | 49.1 | 54.0 | 43.2 | 50.1 | 43.9 | 60.3 | 56.3 | 46.7 | 42.3 | 20.0 | 20.1 |
| Pixtral 12B | 59.4 | 43.4 | 59.9 | 3.8 | 71.0 | 54.2 | 60.9 | 52.7 | 67.7 | 60.7 | 55.8 | 47.7 | 9.2 | 12.4 |
| Phi 3.5 Vision | 43.6 | 17.9 | 65.2 | 38.0 | 63.1 | 36.8 | 58.9 | 53.3 | 73.4 | 46.4 | 81.7 | 50.3 | 45.8 | 31.5 |
| Qwen2VL 2B | 53.7 | 26.5 | 60.5 | 38.2 | 78.2 | 47.2 | 61.9 | 56.2 | 67.9 | 55.9 | 61.7 | 50.5 | 22.5 | 20.4 |
| MiniCPM 2.6 | 53.4 | 22.3 | 57.9 | 45.7 | 72.6 | 47.4 | 71.9 | 65.4 | 70.2 | 57.9 | 52.5 | 49.1 | 9.2 | 14.6 |
| InternVL 2.5 4B | 46.0 | 42.5 | 63.6 | 28.0 | 68.4 | 45.4 | 69.0 | 58.7 | 74.9 | 59.0 | 72.5 | 49.7 | 24.2 | 21.0 |
| InternVL 2.5 8B | 45.6 | 38.2 | 63.4 | 32.0 | 70.3 | 44.2 | 73.5 | 66.4 | 83.0 | 63.3 | 87.5 | 51.6 | 57.5 | 29.0 |
| Qwen2VL 7B | 54.7 | 31.2 | 62.5 | 49.3 | 80.7 | 57.5 | 62.1 | 59.6 | 69.8 | 60.2 | 60.0 | 52.9 | 5.8 | 13.2 |
| Pangea | 61.4 | 55.0 | 64.6 | 60.4 | 70.3 | 52.1 | 69.0 | 65.2 | 75.8 | 70.5 | 69.2 | 58.9 | 0.0 | 6.7 |
| Centurio Aya | 55.7 | 49.3 | 59.1 | 53.2 | 69.7 | 54.7 | 65.0 | 62.4 | 85.0 | 77.9 | 82.5 | 66.8 | 12.5 | 20.7 |
| Centurio Qwen | 60.1 | 47.7 | 60.6 | 54.8 | 72.7 | 56.2 | 75.4 | 70.2 | 89.6 | 81.7 | 87.5 | 73.1 | 28.3 | 27.0 |
{{< /table-caption >}}
> 🔼 이 표는 합성 OCR 데이터를 추가하여 학습된 모델의 SMPQA(Synthetic Multilingual Plot Question Answering) 성능을 보여줍니다. 영어, 라틴 문자 언어, 기타 문자 언어로 나뉘어져 있으며, 사전 학습 없이, OCR 데이터 없이, 이미지 인코더 고정, OCR 데이터의 N%를 영어로 하고 나머지는 100개 언어에 균등하게 분배, 라틴 문자 언어는 2.5k개, 다른 언어는 10k개의 샘플 사용 등 다양한 설정에 따른 결과를 제시합니다. 표 2와 표 3의 결과와 비교 분석이 가능합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: RQ4 (§2.5) results of models trained with additional synthetic OCR data on SMPQA for English, Latin-script languages, and languages with other scripts. No pre-training: from Table 2; No OCR: from Table 3; frozen: image encoder frozen; N% Eng.: N%percent𝑁N\%italic_N % of OCR data is English, rest uniform distributed over L100 languages; Latin down: 2.5k samples for all Latin-script languages, 10k samples for others.
> </details>

{{< table-caption >}}
| Model | T1 | T2 | T3 | T4 | T5 | en |
|---|---|---|---|---|---|---|
| Centurio Aya | 35.1 | 46.4 | 47.0 | 46.7 | 48.3 | 60.6 |
| Centurio Qwen | 38.1 | 51.0 | 48.3 | 47.0 | 50.9 | 66.6 |
| InternVL 2.5 8B | 29.9 | 37.0 | 37.4 | 41.0 | 50.5 | 64.4 |
| Qwen2VL 7B | 30.6 | 36.8 | 40.5 | 46.2 | 48.0 | 56.8 |
| Pangea | 38.5 | 38.6 | 46.9 | 44.2 | 49.9 | 59.8 |
| **Without multi-image tasks (MaRVL, VGR, VLOD):** |  |  |  |  |  |  |
| Centurio Aya | 35.1 | 44.5 | 45.7 | 46.2 | 47.7 | 60.7 |
| Centurio Qwen | 38.1 | 49.5 | 45.6 | 45.8 | 49.6 | 66.0 |
| InternVL 2.5 8B | 29.9 | 40.4 | 35.2 | 39.4 | 49.7 | 62.3 |
| Qwen2VL 7B | 30.6 | 38.7 | 40.8 | 46.8 | 48.3 | 61.7 |
| Pangea | 38.5 | 46.5 | 47.7 | 44.4 | 49.9 | 64.9 |{{< /table-caption >}}
> 🔼 표 5는 Centurio와 다른 13개의 대규모 비전-언어 모델(LVLM)을 14가지 과제에 걸쳐 비교한 결과를 보여줍니다. 최고 및 차순위 결과가 강조 표시되어 있습니다. 점수는 정확도(XM3600의 경우 CIDEr)이며, en 및 mul은 각각 영어 및 평균 다국어 결과를 나타냅니다. XM3600 fid는 모든 언어에 대한 언어 충실도를 나타내고, SMPQA G.&N은 접지 및 명명을 나타냅니다. *는 단일 이미지 입력만 지원함을 의미합니다. AVG.는 모든 작업에 대한 평균입니다. 설정 및 모델에 대한 자세한 내용은 부록 C를 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Table 5: Comparison of Centurio and 13 other LVLMs across 14 tasks. We highlight the best and second-best results. Scores are accuracy (CIDEr for XM3600). en & mul are the English and averaged multilingual results. XM3600 fid. is the language fidelity over all languages; SMPQA G. & N are Grounding and Naming. *: supports only single-image input. AVG.: average over all tasks. Details on the setup and models are provided in Appendix C.
> </details>

{{< table-caption >}}
| Name | Script | ISO-639 | Flores-200 | Tier |
|---|---|---|---|---|
| Arabic | Arabic | `ar` | `arb_Arab` | 5 |
| Chinese | Trad. Han | `zh` | `zho_Hant` | 5 |
| English | Latin | `en` | `eng_Latn` | 5 |
| French | Latin | `fr` | `fra_Latn` | 5 |
| German | Latin | `de` | `deu_Latn` | 5 |
| Japanese | Japanese | `ja` | `jpn_Jpan` | 5 |
| Spanish | Latin | `es` | `spa_Latn` | 5 |
| Basque | Latin | `eu` | `eus_Latn` | 4 |
| Catalan | Latin | `ca` | `cat_Latn` | 4 |
| Croatian | Latin | `hr` | `hrv_Latn` | 4 |
| Czech | Latin | `cs` | `ces_Latn` | 4 |
| Dutch | Latin | `nl` | `nld_Latn` | 4 |
| Finnish | Latin | `fi` | `fin_Latn` | 4 |
| Hindi | Devanagari | `hi` | `hin_Deva` | 4 |
| Hungarian | Latin | `hu` | `hun_Latn` | 4 |
| Italian | Latin | `it` | `ita_Latn` | 4 |
| Korean | Hangul | `ko` | `kor_Hang` | 4 |
| Persian | Arabic | `fa` | `pes_Arab` | 4 |
| Polish | Latin | `pl` | `pol_Latn` | 4 |
| Portuguese | Latin | `pt` | `por_Latn` | 4 |
| Russian | Cyrillic | `ru` | `rus_Cyrl` | 4 |
| Serbian | Cyrillic | `sr` | `srp_Cyrl` | 4 |
| Swedish | Latin | `sv` | `swe_Latn` | 4 |
| Turkish | Latin | `tr` | `tur_Latn` | 4 |
| Vietnamese | Latin | `vi` | `vie_Latn` | 4 |
| Afrikaans | Latin | `af` | `afr_Latn` | 3 |
| Bangla | Bengali | `bn` | `ben_Beng` | 3 |
| Belarusian | Cyrillic | `be` | `bel_Cyrl` | 3 |
| Bosnian | Latin | `bs` | `bos_Latn` | 3 |
| Bulgarian | Cyrillic | `bg` | `bul_Cyrl` | 3 |
| Cebuano | Latin | `ceb` | `ceb_Latn` | 3 |
| Danish | Latin | `da` | `dan_Latn` | 3 |
| Egyptian Arabic | Arabic | `ar-eg` | `arz_Arab` | 3 |
| Estonian | Latin | `et` | `est_Latn` | 3 |
| Galician | Latin | `gl` | `glg_Latn` | 3 |
| Georgian | Georgian | `ka` | `kat_Geor` | 3 |
| Greek | Greek | `el` | `ell_Grek` | 3 |
| Indonesian | Latin | `id` | `ind_Latn` | 3 |
| Kazakh | Cyrillic | `kk` | `kaz_Cyrl` | 3 |
| Latin | Latin | `la` | `NO` | 3 |
| Latvian | Latin | `lv` | `lvs_Latn` | 3 |
| Lithuanian | Latin | `lt` | `lit_Latn` | 3 |
| Malay | Latin | `ms` | `zsm_Latn` | 3 |
| Romanian | Latin | `ro` | `ron_Latn` | 3 |
| Slovak | Latin | `sk` | `slk_Latn` | 3 |
| Slovenian | Latin | `sl` | `slv_Latn` | 3 |
| Tagalog | Latin | `tl` | `tgl_Latn` | 3 |
| Tamil | Tamil | `ta` | `tam_Taml` | 3 |
| Thai | Thai | `th` | `tha_Thai` | 3 |
| Ukrainian | Cyrillic | `uk` | `ukr_Cyrl` | 3 |{{< /table-caption >}}
> 🔼 표 6은 논문의 표 5에서 상위 3개 모델과 Centurio 모델의 성능을 비교한 표입니다. 14개의 과제에 대한 결과를 언어 계층별로 평균하여 나타낸 것입니다. 각 과제는 이진 분류, 다중 선택, 개방형 생성 등 다양한 유형으로 구성되어 있습니다. Centurio 모델은 다양한 언어 규모(단일 언어부터 다중 언어까지)로 훈련되었으며, 해당 언어 계층의 성능을 평가하여 다중 언어 모델의 능력을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Comparison between Centurio and the top-3 models of Table 5. Scores are averages over results from all 14 tasks grouped by language tier.
> </details>

{{< table-caption >}}
| Name | Script | ISO-639 | Flores-200 | Tier |
|---|---|---|---|---|
| Urdu | Arabic | `ur` | `urd_Arab` | 3 |
| Uzbek | Latin | `uz` | `uzn_Latn` | 3 |
| Hebrew | Hebrew | `iwhe` | `heb_Hebr` | 3 |
| Amharic | Ethiopic | `am` | `amh_Ethi` | 2 |
| Haitian | Latin | `ht` | `hat_Latn` | 2 |
| Hausa | Latin | `ha` | `hau_Latn` | 2 |
| Icelandic | Latin | `is` | `isl_Latn` | 2 |
| Irish | Latin | `ga` | `gle_Latn` | 2 |
| Lao | Lao | `lo` | `lao_Laoo` | 2 |
| Maltese | Latin | `mt` | `mlt_Latn` | 2 |
| Marathi | Devanagari | `mr` | `mar_Deva` | 2 |
| Punjabi | Gurmukhi | `pa` | `pan_Guru` | 2 |
| Sanskrit | Devanagari | `sa` | `san_Deva` | 2 |
| Swahili | Latin | `sw` | `swh_Latn` | 2 |
| Tigrinya | Ethiopic | `ti` | `tir_Ethi` | 2 |
| Tswana | Latin | `tn` | `tsn_Latn` | 2 |
| Wolof | Latin | `wo` | `wol_Latn` | 2 |
| Xhosa | Latin | `xh` | `xho_Latn` | 2 |
| Yoruba | Latin | `yo` | `yor_Latn` | 2 |
| Zulu | Latin | `zu` | `zul_Latn` | 2 |
| Albanian | Latin | `sq` | `als_Latn` | 1 |
| Assamese | Bengali | `as` | `asm_Beng` | 1 |
| Azerbaijani | Arabic | `azb` | `azb_Arab` | 1 |
| Bambara | Latin | `bm` | `bam_Latn` | 1 |
| Burmese | Myanmar | `my` | `mya_Mymr` | 1 |
| Esperanto | Latin | `eo` | `epo_Latn` | 1 |
| Igbo | Latin | `ig` | `ibo_Latn` | 1 |
| Javanese | Latin | `jv` | `jav_Latn` | 1 |
| Khmer | Khmer | `km` | `khm_Khmr` | 1 |
| Kikuyu | Latin | `ki` | `kik_Latn` | 1 |
| Lingala | Latin | `ln` | `lin_Latn` | 1 |
| Luxembourgish | Latin | `lb` | `ltz_Latn` | 1 |
| Maori | Latin | `mi` | `mri_Latn` | 1 |
| Norwegian | Latin | `no` | `nob_Latn` | 1 |
| Occitan | Latin | `oc` | `oci_Latn` | 1 |
| Quechua | Latin | `qu` | `quy_Latn` | 1 |
| Samoan | Latin | `sm` | `smo_Latn` | 1 |
| Sango | Latin | `sg` | `sag_Latn` | 1 |
| Sardinian | Latin | `sc` | `srd_Latn` | 1 |
| Scottish Gaelic | Latin | `gd` | `gla_Latn` | 1 |
| Sindhi | Arabic | `sd` | `snd_Arab` | 1 |
| Somali | Latin | `so` | `som_Latn` | 1 |
| Swati | Latin | `ss` | `ssw_Latn` | 1 |
| Telugu | Telugu | `te` | `tel_Telu` | 1 |
| Tibetan | Tibetan | `bo` | `bod_Tibt` | 1 |
| Tok Pisin | Latin | `tpi` | `tpi_Latn` | 1 |
| Tsonga | Latin | `ts` | `tso_Latn` | 1 |
| Twi | Latin | `tw` | `twi_Latn` | 1 |
| Waray | Latin | `war` | `war_Latn` | 1 |
| Welsh | Latin | `cy` | `cym_Latn` | 1 |{{< /table-caption >}}
> 🔼 표 7은 논문의 훈련 실험에 사용된 100개 언어 목록입니다. 'Tier' 열은 Joshi 등(2020)이 제안한 분류 체계에서 각 언어의 등급을 나타냅니다.  상위 티어일수록 해당 언어에 대해 더 많은 데이터 및 리소스가 있다는 것을 의미합니다.  즉, 표는 사용된 언어의 수와 각 언어에 대한 데이터 가용성의 정도를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 7: The list of 100 languages used in our training experiments. The ”Tier” column represents the tier in the taxonomy proposed by Joshi et al. (2020), where a higher tier indicates more available resources, i.e., data, in the respective language.
> </details>

{{< table-caption >}}
| Dataset | Size (Images) | Translated? |
|---|---|---|
| **Natural Image:** |  |  |
| LLaVA Instruct [Liu et al. (2023b)](https://arxiv.org/html/2501.05122/bib.bib69) | 160k | yes |
| VQAv2 [Goyal et al. (2017)](https://arxiv.org/html/2501.05122/bib.bib38) | 83k | yes |
| GQA [Hudson and Manning (2019)](https://arxiv.org/html/2501.05122/bib.bib45) | 72k | yes |
| OKVQA [Marino et al. (2019)](https://arxiv.org/html/2501.05122/bib.bib81) | 9k | yes |
| A-OKVQA [Schwenk et al. (2022)](https://arxiv.org/html/2501.05122/bib.bib93) | 30k | yes |
| RefCOCO [Kazemzadeh et al. (2014)](https://arxiv.org/html/2501.05122/bib.bib52); [Mao et al. (2016)](https://arxiv.org/html/2501.05122/bib.bib79) | 48k | yes |
| VG [Krishna et al. (2017)](https://arxiv.org/html/2501.05122/bib.bib58) | 86k | yes |
| MSCOCO [Lin et al. (2014)](https://arxiv.org/html/2501.05122/bib.bib63) | 50k (subset) | yes |
| **Multiple Images:** |  |  |
| NLVR [Suhr et al. (2019)](https://arxiv.org/html/2501.05122/bib.bib101) | 86k | yes |
| Spot-the-difference [Jhamtani and Berg-Kirkpatrick (2018)](https://arxiv.org/html/2501.05122/bib.bib46) | 8k | yes |
| **OCR:** |  |  |
| OCRVQA [Mishra et al. (2019)](https://arxiv.org/html/2501.05122/bib.bib85) | 50k (subset) | no |
| DocVQA [Mathew et al. (2021)](https://arxiv.org/html/2501.05122/bib.bib84) | 10k | no |
| AI2D [Kembhavi et al. (2016)](https://arxiv.org/html/2501.05122/bib.bib53) | 3k | no |
| ChartQA [Masry et al. (2022)](https://arxiv.org/html/2501.05122/bib.bib82) | 18k | no |
| DVQA [Kafle et al. (2018)](https://arxiv.org/html/2501.05122/bib.bib49) | 50k (subset) | no |
| ScienceQA [Lu et al. (2022)](https://arxiv.org/html/2501.05122/bib.bib74) | 6k | no |
| **Total** | 766k |  |{{< /table-caption >}}
> 🔼 본 표는 논문의 분석 실험에서 지시 조정 단계에 포함된 데이터 세트 목록을 보여줍니다. 모든 크기는 고유한 이미지를 기반으로 하며, 동일한 이미지에 대한 예시는 하나의 시퀀스로 묶여 있습니다.  자세히 살펴보면, 표에는 각 데이터 세트의 이름, 이미지 수, 번역 여부가 나와 있습니다.  자연 이미지와 여러 이미지를 사용한 데이터 세트와 OCR(광학 문자 인식) 데이터 세트로 나뉘어져 있으며, 각 데이터 세트 내의 이미지 수와 이러한 이미지들이 번역되었는지 여부를 나타냅니다. 이 표는 논문의 실험 설정에 대한 명확한 이해를 제공하며, 다양한 비전-언어 모델의 성능을 비교하는 데 사용되는 데이터의 범위와 다양성을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 8: List of datasets included in the instruct tuning phase in our analysis experiments. All sizes are based on unique images; examples about the same image are packed into one sequence.
> </details>

{{< table-caption >}}
| Dataset | Size (Images) | Translated? |
|---|---|---|
| **Natural Image:** |  |  |
| ALLaVA Instruct¹ [Chen et al. (2024a)](https://arxiv.org/html/2501.05122/bib.bib17) | 760k | yes |
| LVIS Instruct4V [Wang et al. (2023)](https://arxiv.org/html/2501.05122/bib.bib111) | 223k | yes |
| Visual7W [Zhu et al. (2016)](https://arxiv.org/html/2501.05122/bib.bib130) | 14k | no |
| VizWiz QA [Gurari et al. (2018)](https://arxiv.org/html/2501.05122/bib.bib39) | 21k | no |
| TallyQA [Acharya et al. (2019)](https://arxiv.org/html/2501.05122/bib.bib3) | 133k | yes |
| SketchyVQA [Tu et al. (2023)](https://arxiv.org/html/2501.05122/bib.bib109) | 4k | yes |
| OODVQA [Tu et al. (2023)](https://arxiv.org/html/2501.05122/bib.bib109) | 3k | no |
| **OCR:** |  |  |
| ScienceQA (Cambrian version) | 6k | no |
| AI2D (Cambrian version) | 4k | no |
| Rendered Text² | 10k | no |
| ScreenQA [Hsiao et al. (2022)](https://arxiv.org/html/2501.05122/bib.bib42) | 33k | no |
| LLaVAR [Zhang et al. (2023b)](https://arxiv.org/html/2501.05122/bib.bib127) | 20k | no |
| ArxivQA [Li et al. (2024)](https://arxiv.org/html/2501.05122/bib.bib62) | 54k | no |
| Chart2Text [Obeid and Hoque (2020)](https://arxiv.org/html/2501.05122/bib.bib87) | 25k | no |
| InfographicVQA [Mathew et al. (2022)](https://arxiv.org/html/2501.05122/bib.bib83) | 2k | no |
| VisText [Tang et al. (2023)](https://arxiv.org/html/2501.05122/bib.bib105) | 10k | no |
| TQA [Kembhavi et al. (2017)](https://arxiv.org/html/2501.05122/bib.bib54) | 1k | no |
| STVQA [Biten et al. (2019)](https://arxiv.org/html/2501.05122/bib.bib12) | 17k | no |
| TAT-QA [Zhu et al. (2021)](https://arxiv.org/html/2501.05122/bib.bib129) | 2k | no |
| TabMWP [Lu et al. (2023)](https://arxiv.org/html/2501.05122/bib.bib75) | 23k | no |
| HiTab [Cheng et al. (2022)](https://arxiv.org/html/2501.05122/bib.bib25) | 2k | no |
| IconQA [Lu et al. (2021b)](https://arxiv.org/html/2501.05122/bib.bib76) | 27k | no |
| VisualMRC [Tanaka et al. (2021)](https://arxiv.org/html/2501.05122/bib.bib104) | 3k | no |
| RobuT [Zhao et al. (2023)](https://arxiv.org/html/2501.05122/bib.bib128) | 113k | no |
| FinQA [Chen et al. (2021)](https://arxiv.org/html/2501.05122/bib.bib24) | 5k | no |
| **Math & Code:** |  |  |
| WebSight [Laurençon et al. (2024b)](https://arxiv.org/html/2501.05122/bib.bib60) | 10k | yes |
| Design2Code [Si et al. (2024)](https://arxiv.org/html/2501.05122/bib.bib97) | 0k | yes |
| DaTikz [Belouadi et al. (2024)](https://arxiv.org/html/2501.05122/bib.bib10) | 48k | no |
| CLEVR [Johnson et al. (2017)](https://arxiv.org/html/2501.05122/bib.bib47) | 70k | yes |
| CLEVR-Math [Lindström and Abraham (2022)](https://arxiv.org/html/2501.05122/bib.bib65) | 70k | yes |
| Geo170k [Gao et al. (2023)](https://arxiv.org/html/2501.05122/bib.bib32) | 9k | no |
| GeomVerse [Kazemi et al. (2023)](https://arxiv.org/html/2501.05122/bib.bib51) | 9k | no |
| Inter-GPS [Lu et al. (2021a)](https://arxiv.org/html/2501.05122/bib.bib73) | 1k | no |
| MathVision [Wang et al. (2024a)](https://arxiv.org/html/2501.05122/bib.bib112) | 3k | no |
| Raven [Zhang et al. (2019)](https://arxiv.org/html/2501.05122/bib.bib125) | 42k | no |
| **Text (no images):** |  |  |
| Aya Dataset [Singh et al. (2024)](https://arxiv.org/html/2501.05122/bib.bib98) | 202k | – |
| Tagengo-GPT4 [Devine (2024)](https://arxiv.org/html/2501.05122/bib.bib31) | 70k | – |
| Magpie² [Xu et al. (2024)](https://arxiv.org/html/2501.05122/bib.bib117) | 400k | – |
| **Total** | 2.47M |  |{{< /table-caption >}}
> 🔼 이 표는 Centurio 모델의 지시 조정 단계에 사용된 데이터셋 목록을 보여줍니다. 표 8에 나열된 데이터셋 외에 추가 데이터셋이 포함되어 있습니다.  첫 번째 추가 데이터셋에는 LAION (Schuhmann et al., 2022)에서 웹 스크래핑된 이미지가 포함되어 있으며, 이 이미지에는 텍스트 요소가 포함되어 있습니다. 두 번째 추가 데이터셋은 magpie-ultra-v0.1 (50,000개), Magpie-Qwen2-Pro-200K-English (200,000개), Magpie-Llama-3.1-Pro-MT-300K-Filtered (150,000개의 하위 집합)을 결합한 것입니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Datasets used on top of the datasets from Table 8 for the instruct tuning phase of Centurio. 1: also contains web-scraped images from LAION Schuhmann et al. (2022) which contain textual elements. 2222:%****␣A1_details.tex␣Line␣275␣****https://huggingface.co/datasets/wendlerc/RenderedText. 2: Combining magpie-ultra-v0.1 (50k), Magpie-Qwen2-Pro-200K-English (200k), Magpie-Llama-3.1-Pro-MT-300K-Filtered (150k subset).
> </details>

{{< table-caption >}}
| Dataset | Task | Visual Input | Textual Input | Target Output | Metric | #Lang. |
|---|---|---|---|---|---|---|
| MaXM | VQA | Single-Image | Question (TL) | WoP (TL) | E. Acc. | 6 |
| xGQA | VQA | Single-Image | Question (TL) | WoP (EN) | E. Acc. | 8 |
| XVNLI | VNLI | Single-Image | Hypothesis (TL) | 'yes' / 'no' / 'maybe' | E. Acc. | 5 |
| M5B-VLOD | VLOD | Multi-Image | Hypothesis (TL) | LoC | R. Acc. | 12 |
| M5B-VGR | VGR | Multi-Image | Hypothesis (TL) | 'yes' / 'no' | E. Acc. | 12 |
| MaRVL | VGR | Multi-Image | Hypothesis (TL) | 'yes' / 'no' | E. Acc. | 6 |
| MTVQA | TH VQA | Single-Image | Question (TL) | WoP (TL) | E. Acc. | 9 |
| SMPQA - Name | TH VQA | Single-Image | Question (TL) | WoP (TL) | E. Acc. | 11 |
| SMPQA - Ground | TH VGR | Single-Image | Question (TL) | 'yes' / 'no' | E. Acc. | 11 |
| M3Exam | TH MC VQA | Single or Multi-Image | Question (TL) | LoC | R. Acc. | 7 |
| MMMU | TH MC VQA | Single or Multi-Image | Question (EN) | LoC | R. Acc. | 1 |
| xMMMU | TH MC VQA | Single or Multi-Image | Question (TL) | LoC | R. Acc. | 7 |
| BabelImageNet-MC | MC VQA | Single-Image | Question (TL) | LoC | R. Acc. | 20 |
| CVQA | MC VQA | Single-Image | Question (TL) | LoC | R. Acc. | 39 |
| XM3600 | Captioning | Single-Image | Prompt (EN) | Caption (TL) | CIDEr | 36 |{{< /table-caption >}}
> 🔼 표 10은 본 논문의 실험에 사용된 데이터셋 목록입니다.  '작업' 열에는 시각적 질문 답변(VQA), 시각적 자연어 추론(VNLI), 시각적 이상치 감지(VLOD), 시각적 근거 추론(VGR), 텍스트 집약적(TH), 다중 선택(MC) 등의 약어를 사용했습니다. '텍스트 입력' 및 '대상 출력' 열에는 (단일) 단어 또는 구절(WoP), 정답의 문자(LoC), 대상 언어(TL), 영어(EN) 등의 약어를 사용했습니다.  'E. Acc.'는 정확도, 'R. Acc.'는 완화된 정확도를 나타냅니다. 제한된 제출로 인해 숨겨진 테스트 세트가 있는 CVQA는 2절에 사용되지 않았습니다.
> <details>
> <summary>read the caption</summary>
> Table 10: List of datasets contained in our test suite. In the Task column, ”VQA” ”VNLI”, ”VLOD”, ”VGR”, ”TH”, and ”MC” are acronyms for ”Visual Question Answering”, ”Visual Natural Language Inference”, ”Visio-Linguistic Outlier Detection”, ”Visually Grounded Reasoning”, ”Text-Heavy”, and ”Multiple-Choice”, respectively. In the ”Textual Input” and ”Target Output” columns, the acronyms ”WoP”, ”LoC”, ”TL”, and ”EN” stand for ”(Single) Word or Phrase”, ”Letter of the correct Choice”, ”Target Language”, and ”English”, respectively. Further, ”E. Acc.” is ”Exact Accuracy” and ”R. Acc.” is ”Relaxed Accuracy”. CVQA is not used in §2 due to its hidden test set with limited submissions.
> </details>

{{< table-caption >}}
| Name | Tier | ISO-639-3 | ISO-639-1 | Datasets |
|---|---|---|---|---|
| Afrikaans | 3 | afr | af | BabelImageNet-MC, M3Exam |
| Amharic | 2 | amh | am | BabelImageNet-MC, CVQA, M5B-VGR, M5B-VLOD |
| Arabic | 5 | ara | ar | MTVQA, SMPQA, XM3600, xMMMU, XVNLI |
| Bengali | 3 | ben | bn | CVQA, M5B-VGR, M5B-VLOD, xGQA, XM3600 |
| Berber (macrolanguage) | 0 | ber |  -  | M5B-VGR, M5B-VLOD |
| Breton | 1 | bre | br | CVQA |
| Bulgarian | 3 | bul | bg | CVQA |
| Chinese | 5 | zho | zh | CVQA, M3Exam, MaRVL, MaXM, SMPQA, xGQA, XM3600 |
| Croatian | 4 | hrv | hr | BabelImageNet-MC, XM3600 |
| Cusco Quechua | 1 | quz |  -  | XM3600 |
| Czech | 4 | ces | cs | BabelImageNet-MC, XM3600 |
| Danish | 3 | dan | da | XM3600 |
| Dutch | 4 | nld | nl | BabelImageNet-MC, XM3600 |
| Egyptian Arabic | 3 | arz |  -  | CVQA |
| English | 5 | eng | en | BabelImageNet-MC, M3Exam, M5B-VGR, M5B-VLOD, MaRVL, MaXM, MME, MMMU, SMPQA, xGQA, XM3600, xMMMU, XVNLI |
| Filipino | 3 | fil |  -  | CVQA, M5B-VGR, M5B-VLOD, XM3600 |
| Finnish | 4 | fin | fi | BabelImageNet-MC, XM3600 |
| French | 5 | fra | fr | MaXM, MTVQA, XM3600, xMMMU, XVNLI |
| German | 5 | deu | de | M5B-VGR, M5B-VLOD, MTVQA, SMPQA, xGQA, XM3600 |
| Hausa | 2 | hau | ha | BabelImageNet-MC, M5B-VGR, M5B-VLOD |
| Hebrew | 3 | heb | he | XM3600 |
| Hindi | 4 | hin | hi | M5B-VGR, M5B-VLOD, MaXM, SMPQA, XM3600, xMMMU |
| Hungarian | 4 | hun | hu | BabelImageNet-MC, XM3600 |
| Igbo | 1 | ibo | ig | CVQA |
| Indonesian | 3 | ind | id | CVQA, MaRVL, SMPQA, xGQA, XM3600, xMMMU |
| Irish | 2 | gle | ga | CVQA |
| Italian | 4 | ita | it | M3Exam, MTVQA, SMPQA, XM3600 |
| Japanese | 5 | jpn | ja | BabelImageNet-MC, CVQA, MTVQA, XM3600, xMMMU |
| Javanese | 1 | jav | jv | CVQA |
| Kanuri | 0 | kau | kr | CVQA |
| Kinyarwanda | 1 | kin | rw | CVQA |
| Korean | 4 | kor | ko | CVQA, SMPQA, xGQA, XM3600 |
| Malay (macrolanguage) | 3 | msa | ms | CVQA |
| Maori | 1 | mri | mi | BabelImageNet-MC, XM3600 |
| Mi-gkabau | 1 | min |  -  | CVQA |
| Modern Greek | 3 | ell | el | BabelImageNet-MC, XM3600 |
| Mongolian | 1 | mon | mn | CVQA |
| Norwegian | 1 | nor | no | BabelImageNet-MC, CVQA, XM3600 |
| Oromo | 1 | orm | om | CVQA |
| Persian | 4 | fas | fa | BabelImageNet-MC, XM3600 |
| Polish | 4 | pol | pl | BabelImageNet-MC, XM3600 |
| Portuguese | 4 | por | pt | CVQA, M3Exam, xGQA, XM3600, xMMMU |
| Romanian | 3 | ron | ro | BabelImageNet-MC, CVQA, MaXM, XM3600 |
| Russian | 4 | rus | ru | CVQA, M5B-VGR, M5B-VLOD, MTVQA, SMPQA, xGQA, XM3600, XVNLI |
| Sinhala | 0 | sin | si | CVQA |
| Spanish | 5 | spa | es | BabelImageNet-MC, CVQA, XM3600, XVNLI |
| Sundanese | 1 | sun | su | CVQA |
| Swahili (macrolanguage) | 2 | swa | sw | CVQA, M5B-VGR, M5B-VLOD, MaRVL, XM3600 |
| Swedish | 4 | swe | sv | XM3600 |
| Tamil | 3 | tam | ta | BabelImageNet-MC, CVQA, MaRVL |
| Telugu | 1 | tel | te | BabelImageNet-MC, CVQA, XM3600 |
| Thai | 3 | tha | th | M3Exam, M5B-VGR, M5B-VLOD, MaXM, MTVQA, SMPQA, XM3600 |
| Turkish | 4 | tur | tr | MaRVL, XM3600 |
| Ukrainian | 3 | ukr | uk | XM3600 |
| Urdu | 3 | urd | ur | CVQA |
| Vietnamese | 4 | vie | vi | M3Exam, MTVQA, XM3600 |
| Zulu | 2 | zul | zu | BabelImageNet-MC, M5B-VGR, M5B-VLOD, SMPQA |
| Unique Languages |  |  |  | 56 (43 without CVQA) |{{< /table-caption >}}
> 🔼 표 11은 논문의 테스트 세트에 포함된 데이터셋에 포함된 언어 목록입니다. 'Tier' 열은 Joshi 등(2020)이 제안한 분류 체계에서 언어의 계층을 나타냅니다. 상위 계층일수록 해당 언어에 더 많은 리소스(즉, 데이터)가 있다는 것을 의미합니다. CVQA는 제한된 제출 횟수로 인해 숨겨진 테스트 세트가 있으므로 2절에서는 사용되지 않습니다.
> <details>
> <summary>read the caption</summary>
> Table 11: List of languages covered in the datasets of our test suite. The ”Tier” column represents the tier in the taxonomy proposed by Joshi et al. (2020), where a higher tier indicates more available resources, i.e., data, in the respective language. CVQA is not used in §2 due to its hidden test set with limited submissions.
> </details>

{{< table-caption >}}
| HuggingFace Model ID | Params |
|---|---| 
| [Qwen/Qwen2-VL-2B-Instruct](https://www.huggingface.com/Qwen/Qwen2-VL-2B-Instruct) [Wang et al., 2024c](https://arxiv.org/html/2501.05122/bib.bib114) | 2B |
| [Qwen/Qwen2-VL-7B-Instruct](https://www.huggingface.com/Qwen/Qwen2-VL-7B-Instruct) [Wang et al., 2024c](https://arxiv.org/html/2501.05122/bib.bib114) | 7B |
| [microsoft/Phi-3.5-vision-instruct](https://www.huggingface.com/microsoft/Phi-3.5-vision-instruct) [Abdin et al., 2024a](https://arxiv.org/html/2501.05122/bib.bib1) | 4B |
| [neulab/Pangea-7B-hf](https://www.huggingface.com/neulab/Pangea-7B-hf) [Yue et al., 2024b](https://arxiv.org/html/2501.05122/bib.bib123) | 7B |
| [openbmb/MiniCPM-V-2_6](https://www.huggingface.com/openbmb/MiniCPM-V-2_6) [Yao et al., 2024b](https://arxiv.org/html/2501.05122/bib.bib120) | 8B |
| [meta-llama/Llama-3.2-11B-Vision-Instruct](https://www.huggingface.com/meta-llama/Llama-3.2-11B-Vision-Instruct) [AI@Meta, 2024](https://arxiv.org/html/2501.05122/bib.bib7) | 11B |
| [mistralai/Pixtral-12B-2409](https://www.huggingface.com/mistralai/Pixtral-12B-2409) [Agrawal et al., 2024](https://arxiv.org/html/2501.05122/bib.bib5) | 12B |
| [AIDC-AI/Parrot-7B](https://www.huggingface.com/AIDC-AI/Parrot-7B) [Sun et al., 2024b](https://arxiv.org/html/2501.05122/bib.bib103) | 7B |
| [MBZUAI/PALO-7B](https://www.huggingface.com/MBZUAI/PALO-7B) [Maaz et al., 2024a](https://arxiv.org/html/2501.05122/bib.bib77) | 7B |
| [MBZUAI/PALO-13B](https://www.huggingface.com/MBZUAI/PALO-13B) [Maaz et al., 2024a](https://arxiv.org/html/2501.05122/bib.bib77) | 13B |
| [OpenGVLab/InternVL2_5-4B](https://www.huggingface.com/OpenGVLab/InternVL2_5-4B) [Chen et al., 2024e](https://arxiv.org/html/2501.05122/bib.bib23) | 4B |
| [OpenGVLab/InternVL2_5-8B](https://www.huggingface.com/OpenGVLab/InternVL2_5-8B) [Chen et al., 2024e](https://arxiv.org/html/2501.05122/bib.bib23) | 8B |
| [maya-multimodal/maya](https://www.huggingface.com/maya-multimodal/maya) [Alam et al., 2024](https://arxiv.org/html/2501.05122/bib.bib8) | 8B |{{< /table-caption >}}
> 🔼 본 표는 논문의 평가 실험에서 고려된 언어 모델 목록을 보여줍니다.  각 모델의 이름과 매개변수 수를 나타내어, 실험에 사용된 다양한 모델의 규모와 복잡도를 비교할 수 있도록 합니다. 이 표는 실험 설계에 대한 이해를 돕고, 사용된 모델의 특징을 한눈에 파악하는 데 유용합니다.
> <details>
> <summary>read the caption</summary>
> Table 12: List of models considered in our evaluation experiments.
> </details>

{{< table-caption >}}
| Train Lang. | T1 | T2 | T3 | T4 | T5 | en |
|---|---|---|---|---|---|---|
| English | 16.1 | 34.7 | 26.3 | 24.3 | 26.2 | 56.4 |
| T5 | 19.1 | 32.5 | 29.3 | 27.2 | 35.5 | 54.3 |
| L100 | 31.1 | 43.0 | 39.4 | 35.9 | 36.4 | 56.6 |
| **Without tasks affected by language fidelity:** |  |  |  |  |  |  |
| English | 36.6 | 37.1 | 39.0 | 39.6 | 40.0 | 54.6 |
| T5 | 38.8 | 34.8 | 40.1 | 40.2 | 40.4 | 53.5 |
| L100 | 46.3 | 44.0 | 45.0 | 42.8 | 42.9 | 55.3 |{{< /table-caption >}}
> 🔼 본 표는 논문의 표 1을 Llama 3 모델을 사용하여 재현한 실험 결과를 보여줍니다.  영어만 사용한 경우, T5 언어만 사용한 경우, 그리고 100개 언어를 모두 사용한 경우의 세 가지 설정에 대한 결과를 비교하여 제시합니다. 표 1과 동일한 실험을 반복하여 각 언어 집합에 대한 다양한 하위 작업의 성능을 보여줍니다. 각 언어 등급(T1~T5)에 따른 평균 점수를 비교함으로써, 다양한 언어 조합이 모델의 성능에 미치는 영향을 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 13: Experimental setup of Table 1 repeated with Llama 3 and the setups: just English, T5 languages, and L100 languages.
> </details>

{{< table-caption >}}
| English % | T1 | T2 | T3 | T4 | T5 | en |
|---|---|---|---|---|---|---|
| 10 | **32.9** | **43.1** | **38.7** | **35.4** | 35.4 | 54.2 |
| 50 | **31.1** | **43.0** | **39.4** | **35.9** | **36.4** | **56.6** |
| 90 | 26.9 | 38.7 | 36.9 | 34.2 | **35.8** | **56.6** |{{< /table-caption >}}
> 🔼 본 표는 논문의 표 2를 Llama 3 모델을 사용하여 반복한 실험 결과를 보여줍니다.  표 2의 실험 설정을 그대로 따르되, instruction tuning 데이터셋에서 영어 데이터의 비율을 10%, 50%, 90%로 달리하여 실험했습니다.  각 설정에 따른 다양한 언어(Language Tier T1-T5)에 대한 성능 결과를 보여줍니다. 이를 통해 instruction tuning 데이터에서 영어 데이터의 비율이 다국어 능력에 미치는 영향을 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 14: Experimental setup of Table 2 repeated with Llama 3 and the setups: 10, 50, and 90% English instruct tune data.
> </details>

{{< table-caption >}}
| English % | T1 | T2 | T3 | T4 | T5 | en |
|---|---|---|---|---|---|---|
| No pretrain | 31.1 | 43.0 | 39.4 | 35.9 | 36.4 | 56.6 |
| 100 | 33.9 | 44.7 | 43.3 | 39.9 | 39.9 | 60.8 |
| 1 | **37.8** | **47.4** | **45.0** | **41.1** | **40.7** | **61.4** |{{< /table-caption >}}
> 🔼 표 15는 본 논문의 2.4절 RQ3 실험에서 Llama 3 모델을 사용하여 사전 학습 데이터의 영어 비율을 1%와 100%로 변화시켰을 때의 결과를 보여줍니다. 표 3의 실험 설정을 Llama 3에 적용하여 재현한 결과이며, 각 설정에서 다양한 언어 하위 집합에 대한 성능을 비교 분석합니다. 이를 통해 영어 중심의 사전 학습 데이터와 다국어 사전 학습 데이터의 효과를 비교하고 최적의 사전 학습 전략을 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 15: Results of Table 3 repeated with Llama 3 and the setups: 1 and 100% English pre-train data.
> </details>

{{< table-caption >}}
| Distribution | T1 | T2 | T3 | T4 | T5 | en |
|---|---|---|---|---|---|---|
| Uniform | 18.9 | 32.6 | 30.7 | 28.8 | 34.4 | 52.6 |
| Stratified-1 | 18.6 | 32.5 | 30.7 | 28.0 | 33.8 | 53.0 |
| Stratified-2 | 19.2 | 32.6 | 29.5 | 27.4 | 33.9 | 52.0 |{{< /table-caption >}}
> 🔼 본 표는 저자들이 제안한 대규모 다국어 비전-언어 모델 학습을 위한 언어 데이터 분포 전략에 대한 실험 결과를 보여줍니다.  균등 분포와 저자원 언어를 과대 표본 추출하는 두 가지 계층화된 분포를 비교하여,  다국어 모델 성능에 미치는 영향을 분석합니다.  단순히 언어 수를 늘리는 것보다 언어 데이터 분포 전략이 모델 성능에 중요한 영향을 미침을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 16: Comparison between our uniform allocation of data compared to two stratified allocations that upsample low-resource languages.
> </details>

{{< table-caption >}}
| LLM | T1 | T2 | T3 | T4 | T5 | en |
|---|---|---|---|---|---|---|
| Phi-3.5-mini-instruct | 18.9 | 32.6 | 30.7 | 28.8 | 34.4 | 52.6 |
| gemma-2-9b-it | 29.2 | 40.9 | 36.4 | 33.5 | 35.3 | 52.8 |
| Meta-Llama-3-8B-Instruct | 31.1 | 43.0 | 39.4 | 35.9 | 36.4 | 56.6 |
| Qwen2.5-7B-Instruct | 30.7 | 43.7 | 42.0 | 38.1 | 40.5 | 62.7 |
| aya-expanse-8b | 28.3 | 42.5 | 43.0 | 39.8 | 40.9 | 59.9 |{{< /table-caption >}}
> 🔼 표 17은 논문의 2.3절에서 설명하는 대로 100개 언어와 50% 영어를 사용하여 지시 조정 데이터로 학습된 다양한 LLM 백본 간의 비교를 보여줍니다. 이 표는 다양한 언어 계층(T1-T5)에 대한 성능을 보여주는 다양한 지표를 포함하여 여러 가지 측면에서 모델의 성능을 비교합니다. 각 언어 계층에 대한 평균 점수 외에도 영어 성능과 언어 충실도(Language Fidelity)를 별도로 제시합니다. 이를 통해 다양한 LLM 백본의 다국어 능력을 평가하고, 다국어 학습 전략의 효과를 분석하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 17: Comparison between different LLM backbones all trained with the instruct tuning data with L100 languages and 50% English (as in §2.3).
> </details>

{{< table-caption >}}
|             | en   | avg. | af   | am   | cs   | el   | es   | fa   | fi   | ha   | hr   | hu   | ja   | mi   | nl   | no   | pl   | ro   | ta   | te   | zu   |
|-------------|------|------|------|------|------|------|------|------|------|------|------|------|------|------|------|------|------|------|------|------|------|
| Phi 3.5 - English | 64.7 | 38.1 | 43.3 | 29.7 | 41.5 | 35.5 | 55.9 | 33.6 | 36.4 | 24.5 | 43.3 | 39.0 | 49.8 | 27.8 | 47.3 | 44.2 | 41.4 | 42.8 | 30.0 | 27.1 | 31.1 |
| Phi 3.5 - T5 50  | 66.0 | 39.6 | 46.0 | 30.3 | 43.1 | 36.3 | 56.3 | 33.4 | 36.5 | 35.1 | 45.1 | 40.7 | 50.9 | 30.1 | 48.4 | 46.2 | 41.1 | 43.1 | 31.0 | 29.6 | 29.1 |
| Phi 3.5 - T5-4 50 | 65.2 | 40.6 | 46.8 | 29.6 | 44.6 | 37.9 | 59.1 | 36.7 | 37.5 | 29.0 | 46.4 | 42.5 | 52.0 | 31.1 | 50.7 | 47.4 | 43.0 | 43.5 | 31.5 | 29.0 | 32.4 |
| Phi 3.5 - T5-3 50 | 65.5 | 40.6 | 50.0 | 28.8 | 43.3 | 37.4 | 58.6 | 34.4 | 38.4 | 33.0 | 46.1 | 41.4 | 50.9 | 31.2 | 49.7 | 47.0 | 41.9 | 43.8 | 32.5 | 29.6 | 32.7 |
| Phi 3.5 - T5-2 50 | 64.8 | 39.1 | 47.2 | 25.6 | 41.9 | 35.8 | 57.9 | 34.0 | 36.0 | 29.8 | 44.8 | 39.5 | 50.0 | 30.5 | 47.7 | 45.8 | 41.2 | 42.4 | 30.4 | 29.2 | 33.9 |
| Phi 3.5 - L100 50 | 64.7 | 39.9 | 48.1 | 28.2 | 42.8 | 36.8 | 57.2 | 34.7 | 37.0 | 28.2 | 44.7 | 40.4 | 51.2 | 31.6 | 47.8 | 46.4 | 40.9 | 43.8 | 30.6 | 30.1 | 37.5 |
| Llama 3 - English  | 65.4 | 40.9 | 44.0 | 28.2 | 46.9 | 42.2 | 53.0 | 42.4 | 38.7 | 31.1 | 47.6 | 46.3 | 48.6 | 30.1 | 48.2 | 47.4 | 44.0 | 44.9 | 31.6 | 32.5 | 29.3 |
| Llama 3 - T5 50   | 63.9 | 43.7 | 50.6 | 28.7 | 49.2 | 46.4 | 54.6 | 46.6 | 41.7 | 35.4 | 50.7 | 50.8 | 51.9 | 30.0 | 51.2 | 50.9 | 47.0 | 48.4 | 31.1 | 35.6 | 30.1 |
| Llama 3 - L100 50 | 66.2 | 48.8 | 55.3 | 35.1 | 54.2 | 51.2 | 56.2 | 47.6 | 46.2 | 37.2 | 56.1 | 54.1 | 53.3 | 33.7 | 54.6 | 54.3 | 50.8 | 51.9 | 43.6 | 50.9 | 40.8 |
| Phi 3.5 - L100 1  | 63.1 | 39.7 | 47.4 | 26.8 | 42.9 | 36.7 | 56.2 | 34.3 | 35.9 | 33.5 | 46.8 | 40.5 | 49.0 | 32.7 | 48.4 | 46.7 | 41.3 | 43.1 | 29.0 | 29.9 | 34.2 |
| Phi 3.5 - L100 10 | 62.7 | 39.4 | 47.1 | 27.1 | 43.1 | 36.8 | 56.5 | 34.4 | 36.5 | 29.3 | 43.8 | 40.9 | 49.8 | 29.8 | 47.2 | 48.2 | 41.4 | 43.6 | 30.2 | 28.0 | 34.4 |
| Phi 3.5 - L100 24 | 63.3 | 40.4 | 48.0 | 29.0 | 43.3 | 37.7 | 56.5 | 35.2 | 36.7 | 32.4 | 46.9 | 40.7 | 50.7 | 33.0 | 49.3 | 47.2 | 41.8 | 44.4 | 31.9 | 31.2 | 31.1 |
| Phi 3.5 - L100 50 | 64.7 | 39.9 | 48.1 | 28.2 | 42.8 | 36.8 | 57.2 | 34.7 | 37.0 | 28.2 | 44.7 | 40.4 | 51.2 | 31.6 | 47.8 | 46.4 | 40.9 | 43.8 | 30.6 | 30.1 | 37.5 |
| Phi 3.5 - L100 75 | 65.4 | 39.8 | 47.1 | 26.0 | 42.0 | 37.1 | 57.4 | 34.7 | 36.9 | 32.2 | 44.2 | 40.4 | 51.3 | 31.5 | 49.4 | 46.8 | 41.6 | 42.9 | 31.1 | 28.5 | 34.2 |
| Phi 3.5 - L100 90 | 64.7 | 37.5 | 43.8 | 24.1 | 40.3 | 35.8 | 57.1 | 31.8 | 35.7 | 25.0 | 43.1 | 39.2 | 49.1 | 24.9 | 47.9 | 44.4 | 39.3 | 42.8 | 28.7 | 27.7 | 31.9 |
| Llama 3 - L100 10 | 65.9 | 49.8 | 58.4 | 38.1 | 55.0 | 50.9 | 58.5 | 49.3 | 45.7 | 40.7 | 59.4 | 56.3 | 54.1 | 34.9 | 53.7 | 56.8 | 51.8 | 51.3 | 42.6 | 51.9 | 36.0 |
| Llama 3 - L100 50 | 66.2 | 48.8 | 55.3 | 35.1 | 54.2 | 51.2 | 56.2 | 47.6 | 46.2 | 37.2 | 56.1 | 54.1 | 53.3 | 33.7 | 54.6 | 54.3 | 50.8 | 51.9 | 43.6 | 50.9 | 40.8 |
| Llama 3 - L100 90 | 64.4 | 45.3 | 52.5 | 26.8 | 51.0 | 47.2 | 54.8 | 45.9 | 44.0 | 29.5 | 54.1 | 50.0 | 51.2 | 31.3 | 52.1 | 51.8 | 48.6 | 49.8 | 36.5 | 48.3 | 34.7 |
| Phi 3.5 - L100 50 | 64.7 | 39.9 | 48.1 | 28.2 | 42.8 | 36.8 | 57.2 | 34.7 | 37.0 | 28.2 | 44.7 | 40.4 | 51.2 | 31.6 | 47.8 | 46.4 | 40.9 | 43.8 | 30.6 | 30.1 | 37.5 |
| Phi 3.5 - PT 100  | 66.3 | 38.9 | 48.4 | 25.0 | 42.7 | 36.0 | 57.3 | 33.2 | 36.5 | 22.3 | 44.8 | 39.8 | 49.9 | 31.3 | 48.6 | 46.4 | 41.3 | 43.2 | 30.5 | 30.8 | 30.6 |
| Phi 3.5 - PT 50   | 65.7 | 42.2 | 50.0 | 37.8 | 44.2 | 40.0 | 57.8 | 36.0 | 36.5 | 33.0 | 45.2 | 41.8 | 49.3 | 35.0 | 49.0 | 48.1 | 42.0 | 44.1 | 33.7 | 37.7 | 40.6 |
| Phi 3.5 - PT 1   | 65.8 | 42.8 | 50.1 | 35.1 | 44.8 | 38.9 | 56.9 | 37.9 | 37.5 | 41.2 | 49.1 | 42.1 | 49.6 | 33.4 | 49.6 | 48.2 | 43.6 | 45.9 | 34.9 | 36.1 | 38.5 |
| Llama 3 - L100 50 | 66.2 | 48.8 | 55.3 | 35.1 | 54.2 | 51.2 | 56.2 | 47.6 | 46.2 | 37.2 | 56.1 | 54.1 | 53.3 | 33.7 | 54.6 | 54.3 | 50.8 | 51.9 | 43.6 | 50.9 | 40.8 |
| Llama 3 - PT 1   | 69.6 | 55.5 | 62.4 | 44.0 | 60.4 | 60.4 | 62.9 | 55.3 | 51.7 | 40.4 | 63.0 | 62.1 | 59.9 | 36.6 | 59.4 | 62.1 | 58.0 | 58.6 | 50.6 | 60.6 | 45.7 |
| Llama 3 - PT 100  | 68.7 | 53.6 | 63.4 | 36.8 | 59.6 | 58.1 | 62.5 | 54.1 | 50.8 | 37.5 | 63.1 | 61.6 | 60.7 | 36.9 | 59.9 | 61.0 | 58.0 | 58.0 | 46.5 | 54.0 | 34.9 |
| Gemma 2 - L100 50 | 60.5 | 44.8 | 49.1 | 42.5 | 47.5 | 45.3 | 52.0 | 44.8 | 41.6 | 30.9 | 50.7 | 47.6 | 51.4 | 32.8 | 49.8 | 51.1 | 47.2 | 47.5 | 41.8 | 45.1 | 32.1 |
| Llama 3 - L100 50 | 66.2 | 48.8 | 55.3 | 35.1 | 54.2 | 51.2 | 56.2 | 47.6 | 46.2 | 37.2 | 56.1 | 54.1 | 53.3 | 33.7 | 54.6 | 54.3 | 50.8 | 51.9 | 43.6 | 50.9 | 40.8 |
| Qwen 2.5 - L100 50| 68.2 | 50.6 | 62.4 | 37.1 | 57.9 | 50.8 | 63.4 | 49.6 | 42.6 | 28.7 | 61.0 | 48.3 | 63.1 | 33.5 | 58.8 | 58.2 | 57.2 | 55.4 | 36.8 | 55.6 | 40.6 |
| Aya-Expanse - L100 50| 67.6 | 52.0 | 62.2 | 31.0 | 65.3 | 65.5 | 63.2 | 58.9 | 39.8 | 33.2 | 60.8 | 46.3 | 65.1 | 33.1 | 61.3 | 55.5 | 60.2 | 61.9 | 43.5 | 43.2 | 37.2 |
| `Centurio` Aya     | 69.7 | 54.7 | 63.6 | 29.4 | 66.2 | 67.8 | 65.1 | 60.0 | 43.3 | 37.5 | 63.6 | 49.8 | 66.7 | 37.0 | 62.4 | 59.1 | 62.6 | 64.0 | 46.9 | 50.9 | 42.6 |
| `Centurio` Qwen    | 72.7 | 56.2 | 65.3 | 47.4 | 62.2 | 56.7 | 67.0 | 53.6 | 48.8 | 36.7 | 65.4 | 54.1 | 67.6 | 39.1 | 63.7 | 63.6 | 60.4 | 58.5 | 45.2 | 63.4 | 49.5 |{{< /table-caption >}}
> 🔼 표 18은 Babel ImageNet-MC 데이터셋에 대한 결과를 보여줍니다. Babel ImageNet-MC는 다양한 언어로 번역된 ImageNet 레이블을 사용하는 이미지 분류 작업입니다. 이 표는 다양한 언어와 다양한 훈련 전략(예: 영어 전용, 다국어 혼합)을 사용한 여러 모델의 성능을 보여줍니다. 각 행은 특정 모델과 훈련 전략에 대한 결과를 나타내며, 열은 언어별 정확도를 나타냅니다.  이 표를 통해 다국어 모델 훈련에 있어서 다양한 언어와 훈련 데이터 구성이 모델 성능에 미치는 영향을 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 18: BIN-MC
> </details>

{{< table-caption >}}
|             | en   | avg. | af   | zh   | it   | pt   | th   | vi   |
|-------------|------|------|------|------|------|------|------|------|
|Phi 3.5 - English| 52.9 | 32.7 | 32.5 | 37.0 | 49.6 | 39.7 | 25.4 | 12.2 |
|Phi 3.5 - T5 50  | 51.2 | 35.3 | 39.9 | 35.9 | 46.4 | 39.7 | 28.2 | 21.7 |
|Phi 3.5 - T5-4 50| 52.2 | 34.2 | 40.5 | 32.4 | 49.1 | 38.6 | 25.2 | 19.1 |
|Phi 3.5 - T5-3 50| 51.3 | 35.3 | 43.6 | 34.0 | 47.4 | 37.3 | 27.9 | 21.7 |
|Phi 3.5 - T5-2 50| 49.2 | 33.7 | 39.3 | 32.9 | 45.1 | 38.4 | 22.2 | 24.3 |
|Phi 3.5 - L100 50| 50.8 | 36.0 | 39.3 | 36.1 | 50.9 | 40.1 | 26.2 | 23.5 |
|Llama 3 - English| 46.1 | 32.5 | 38.6 | 32.6 | 41.6 | 35.0 | 25.9 | 20.9 |
|Llama 3 - T5 50  | 45.0 | 33.8 | 40.5 | 34.3 | 41.9 | 34.1 | 25.7 | 26.1 |
|Llama 3 - L100 50| 46.6 | 34.2 | 44.2 | 31.0 | 42.4 | 34.6 | 27.2 | 26.1 |
|Phi 3.5 - L100 1 | 50.3 | 35.1 | 39.9 | 35.4 | 46.6 | 39.2 | 23.9 | 25.2 |
|Phi 3.5 - L100 10| 48.8 | 33.9 | 35.0 | 33.6 | 48.1 | 36.1 | 24.7 | 26.1 |
|Phi 3.5 - L100 24| 50.8 | 36.5 | 41.7 | 37.0 | 51.6 | 35.9 | 27.7 | 25.2 |
|Phi 3.5 - L100 50| 50.8 | 36.0 | 39.3 | 36.1 | 50.9 | 40.1 | 26.2 | 23.5 |
|Phi 3.5 - L100 75| 48.0 | 36.1 | 44.2 | 35.9 | 47.1 | 38.4 | 26.7 | 24.3 |
|Phi 3.5 - L100 90| 51.7 | 35.1 | 36.8 | 38.0 | 48.1 | 36.8 | 26.4 | 24.3 |
|Llama 3 - L100 10| 43.7 | 33.6 | 41.7 | 29.4 | 44.9 | 35.3 | 23.7 | 27.0 |
|Llama 3 - L100 50| 46.6 | 34.2 | 44.2 | 31.0 | 42.4 | 34.6 | 27.2 | 26.1 |
|Llama 3 - L100 90| 43.3 | 34.6 | 37.4 | 32.2 | 44.9 | 35.3 | 30.2 | 27.8 |
|Phi 3.5 - L100 50| 50.8 | 36.0 | 39.3 | 36.1 | 50.9 | 40.1 | 26.2 | 23.5 |
|Phi 3.5 - PT 100 | 50.3 | 35.8 | 41.7 | 37.5 | 49.4 | 36.6 | 24.2 | 25.2 |
|Phi 3.5 - PT 50  | 49.7 | 33.1 | 41.1 | 36.1 | 44.4 | 35.0 | 21.7 | 20.0 |
|Phi 3.5 - PT 1  | 48.4 | 33.8 | 41.7 | 35.9 | 46.4 | 34.8 | 23.2 | 20.9 |
|Llama 3 - L100 50| 46.6 | 34.2 | 44.2 | 31.0 | 42.4 | 34.6 | 27.2 | 26.1 |
|Llama 3 - PT 1  | 50.2 | 37.9 | 44.8 | 34.7 | 48.1 | 40.6 | 31.4 | 27.8 |
|Llama 3 - PT 100 | 52.9 | 37.1 | 50.3 | 33.8 | 46.6 | 37.5 | 30.2 | 24.3 |
|Gemma 2 - L100 50| 42.5 | 33.4 | 43.6 | 33.6 | 41.6 | 30.4 | 27.7 | 23.5 |
|Llama 3 - L100 50| 46.6 | 34.2 | 44.2 | 31.0 | 42.4 | 34.6 | 27.2 | 26.1 |
|Qwen 2.5 - L100 50| 53.6 | 39.6 | 46.0 | 44.7 | 50.6 | 42.4 | 29.7 | 24.3 |
|Aya-Expanse - L100 50| 49.3 | 36.5 | 46.6 | 36.8 | 51.9 | 39.0 | 26.2 | 18.3 |
|`Centurio` Aya   | 53.0 | 41.2 | 52.8 | 40.3 | 51.4 | 47.7 | 27.4 | 27.8 |
|`Centurio` Qwen  | 61.2 | 46.9 | 50.9 | 64.1 | 55.6 | 49.0 | 31.9 | 29.6 |{{< /table-caption >}}
> 🔼 표 19는 다양한 언어 모델의 다국어 능력을 평가하기 위해 사용된 M3Exam 데이터셋에 대한 결과를 보여줍니다. M3Exam은 다양한 언어로 된 질문과 답변 쌍으로 구성된 시각적 질문 응답(VQA) 데이터셋입니다. 이 표에서는 다양한 모델에 대해 영어 및 다양한 언어의 정확도를 비교 분석합니다. 각 모델의 성능은 여러 언어에 걸쳐 평균 점수로 나타나며, 다양한 언어 모델의 다국어 성능을 비교하는 데 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 19: M3Exam
> </details>

{{< table-caption >}}
|               | en  | avg. | am  | ber | bn  | de  | fil | ha  | hi  | ru  | sw  | th  | zu  |
| :------------ | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| Phi 3.5 - English | 80.8 | 54.1 | 45.0 | 50.8 | 41.5 | 71.7 | 55.8 | 41.7 | 62.7 | 85.0 | 35.8 | 68.3 | 36.2 |
| Phi 3.5 - T5 50 | 75.8 | 50.9 | 49.2 | 49.2 | 40.7 | 72.5 | 55.0 | 42.5 | 54.2 | 60.8 | 37.5 | 60.8 | 37.9 |
| Phi 3.5 - T5-4 50 | 83.3 | 55.1 | 51.7 | 43.3 | 49.2 | 70.8 | 65.8 | 42.5 | 61.9 | 70.8 | 38.3 | 75.0 | 36.2 |
| Phi 3.5 - T5-3 50 | 83.3 | 56.6 | 43.3 | 50.8 | 50.8 | 74.2 | 69.2 | 42.5 | 57.6 | 76.7 | 43.3 | 71.7 | 42.2 |
| Phi 3.5 - T5-2 50 | 81.7 | 57.5 | 45.8 | 52.5 | 44.1 | 73.3 | 64.2 | 39.2 | 59.3 | 73.3 | 60.0 | 60.8 | 59.5 |
| Phi 3.5 - L100 50 | 76.7 | 56.4 | 46.7 | 46.7 | 54.2 | 71.7 | 60.0 | 45.0 | 57.6 | 70.8 | 57.5 | 65.8 | 44.0 |
| Llama 3 - English | 82.5 | 56.3 | 66.7 | 30.8 | 49.2 | 77.5 | 50.8 | 48.3 | 63.6 | 75.8 | 46.7 | 70.0 | 39.7 |
| Llama 3 - T5 50  | 77.5 | 55.9 | 47.5 | 49.2 | 49.2 | 71.7 | 63.3 | 42.5 | 62.7 | 73.3 | 45.8 | 70.8 | 38.8 |
| Llama 3 - L100 50 | 80.0 | 64.8 | 58.3 | 47.5 | 64.4 | 75.8 | 61.7 | 67.5 | 64.4 | 73.3 | 59.2 | 67.5 | 73.3 |
| Phi 3.5 - L100 1 | 65.0 | 47.5 | 42.5 | 50.0 | 38.1 | 65.0 | 58.3 | 40.0 | 45.8 | 58.3 | 39.2 | 42.5 | 42.2 |
| Phi 3.5 - L100 10 | 73.3 | 54.5 | 43.3 | 50.0 | 51.7 | 67.5 | 60.0 | 45.0 | 51.7 | 63.3 | 53.3 | 63.3 | 50.0 |
| Phi 3.5 - L100 24 | 73.3 | 60.3 | 54.2 | 47.5 | 58.5 | 72.5 | 55.0 | 58.3 | 60.2 | 72.5 | 64.2 | 59.2 | 61.2 |
| Phi 3.5 - L100 50 | 76.7 | 56.4 | 46.7 | 46.7 | 54.2 | 71.7 | 60.0 | 45.0 | 57.6 | 70.8 | 57.5 | 65.8 | 44.0 |
| Phi 3.5 - L100 75 | 80.0 | 56.7 | 51.7 | 53.3 | 55.1 | 70.8 | 67.5 | 41.7 | 63.6 | 75.8 | 38.3 | 69.2 | 36.2 |
| Phi 3.5 - L100 90 | 79.2 | 54.6 | 43.3 | 50.0 | 44.9 | 80.8 | 60.0 | 42.5 | 55.9 | 77.5 | 45.0 | 55.8 | 44.8 |
| Llama 3 - L100 10 | 77.5 | 65.4 | 65.0 | 45.0 | 63.6 | 76.7 | 58.3 | 70.8 | 64.4 | 74.2 | 63.3 | 69.2 | 69.0 |
| Llama 3 - L100 50 | 80.0 | 64.8 | 58.3 | 47.5 | 64.4 | 75.8 | 61.7 | 67.5 | 64.4 | 73.3 | 59.2 | 67.5 | 73.3 |
| Llama 3 - L100 90 | 82.5 | 63.0 | 45.8 | 39.2 | 66.1 | 80.8 | 58.3 | 68.3 | 61.9 | 75.0 | 63.3 | 75.0 | 59.5 |
| Phi 3.5 - L100 50 | 76.7 | 56.4 | 46.7 | 46.7 | 54.2 | 71.7 | 60.0 | 45.0 | 57.6 | 70.8 | 57.5 | 65.8 | 44.0 |
| Phi 3.5 - PT 100 | 80.8 | 58.6 | 44.2 | 49.2 | 56.8 | 78.3 | 56.7 | 47.5 | 65.3 | 75.0 | 47.5 | 73.3 | 50.9 |
| Phi 3.5 - PT 50  | 80.0 | 63.2 | 58.3 | 50.0 | 55.1 | 78.3 | 63.3 | 60.0 | 61.9 | 76.7 | 55.0 | 75.0 | 61.2 |
| Phi 3.5 - PT 1  | 80.0 | 62.0 | 55.8 | 50.0 | 51.7 | 81.7 | 62.5 | 60.0 | 66.1 | 75.0 | 50.0 | 66.7 | 62.1 |
| Llama 3 - L100 50 | 80.0 | 64.8 | 58.3 | 47.5 | 64.4 | 75.8 | 61.7 | 67.5 | 64.4 | 73.3 | 59.2 | 67.5 | 73.3 |
| Llama 3 - PT 1  | 87.5 | 71.2 | 70.0 | 50.8 | 65.3 | 79.2 | 63.3 | 83.3 | 68.6 | 82.5 | 66.7 | 85.8 | 68.1 |
| Llama 3 - PT 100 | 85.0 | 68.8 | 65.8 | 49.2 | 67.8 | 80.8 | 61.7 | 70.0 | 66.9 | 85.0 | 70.0 | 74.2 | 65.5 |
| Gemma 2 - L100 50 | 77.5 | 61.8 | 64.2 | 52.5 | 48.3 | 70.8 | 51.7 | 64.2 | 58.5 | 71.7 | 54.2 | 70.8 | 73.3 |
| Llama 3 - L100 50 | 80.0 | 64.8 | 58.3 | 47.5 | 64.4 | 75.8 | 61.7 | 67.5 | 64.4 | 73.3 | 59.2 | 67.5 | 73.3 |
| Qwen 2.5 - L100 50 | 91.7 | 71.2 | 76.7 | 50.0 | 69.5 | 81.7 | 77.5 | 57.5 | 72.9 | 83.3 | 71.7 | 80.8 | 62.1 |
| Aya-Expanse - L100 50 | 92.5 | 69.9 | 52.5 | 54.2 | 55.9 | 80.8 | 85.0 | 72.5 | 79.7 | 83.3 | 63.3 | 78.3 | 63.8 |
| `Centurio` Aya   | 82.5 | 66.8 | 71.7 | 54.2 | 59.3 | 73.3 | 59.2 | 65.0 | 71.2 | 75.8 | 67.5 | 72.5 | 65.5 |
| `Centurio` Qwen  | 87.5 | 73.1 | 77.5 | 49.2 | 62.7 | 80.8 | 78.3 | 76.7 | 72.9 | 85.0 | 70.0 | 81.7 | 69.0 |{{< /table-caption >}}
> 🔼 표 20는 다양한 언어와 비전-언어 모델의 성능을 비교한 VGR(Visual Grounded Reasoning) 작업에 대한 결과를 보여줍니다.  각 모델은 다양한 언어(예: 영어, 아랍어, 스페인어 등)와 다양한 하위 작업(예: 이미지 캡션 생성)에서 평가되었습니다. 표는 각 모델의 정확도와 다른 평가 지표를 보여주어, 다국어 능력과 비전-언어 모델의 성능을 비교 분석하는 데 도움이 됩니다. Centurio 모델이 여러 언어와 작업에서 우수한 성능을 보여주는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 20: VGR
> </details>

{{< table-caption >}}
|               | en   | avg. | am   | ber  | bn   | de   | fil  | ha   | hi   | ru   | sw   | th   | zu   |
| :------------- | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| Phi 3.5 - English | 16.7 | 21.3 | 20.8 | 20.8 | 19.2 | 16.7 | 25.8 | 28.3 | 17.0 | 12.5 | 25.0 | 26.7 | 22.0 |
| Phi 3.5 - T5 50  | 23.3 | 20.0 | 15.0 | 18.3 | 20.8 | 21.7 | 16.7 | 20.0 | 23.2 | 27.5 | 22.3 | 15.8 | 18.6 |
| Phi 3.5 - T5-4 50 | 17.5 | 18.2 | 19.2 | 20.8 | 13.3 | 20.8 | 17.5 | 16.7 | 21.4 | 26.7 | 16.1 | 10.0 | 17.8 |
| Phi 3.5 - T5-3 50 | 25.8 | 19.8 | 16.7 | 17.5 | 21.7 | 21.7 | 20.0 | 21.7 | 23.2 | 20.8 | 18.8 | 16.7 | 18.6 |
| Phi 3.5 - T5-2 50 | 21.7 | 20.5 | 21.7 | 18.3 | 16.7 | 22.5 | 27.5 | 27.5 | 17.9 | 21.7 | 17.0 | 13.3 | 21.2 |
| Phi 3.5 - L100 50 | 18.3 | 19.5 | 16.7 | 20.8 | 19.2 | 25.8 | 20.0 | 16.7 | 25.0 | 20.8 | 13.4 | 17.5 | 18.6 |
| Llama 3 - English | 12.5 | 20.8 | 18.3 | 21.7 | 20.0 | 10.8 | 24.2 | 29.2 | 15.2 | 12.5 | 28.6 | 29.2 | 19.5 |
| Llama 3 - T5 50  | 20.8 | 20.1 | 18.3 | 19.2 | 17.5 | 16.7 | 25.0 | 21.7 | 24.1 | 15.0 | 19.6 | 23.3 | 20.3 |
| Llama 3 - L100 50 | 12.5 | 20.6 | 19.2 | 20.8 | 20.0 | 10.8 | 24.2 | 30.0 | 15.2 | 10.8 | 28.6 | 27.5 | 19.5 |
| Phi 3.5 - L100 1 | 24.2 | 19.3 | 15.0 | 21.7 | 17.5 | 20.0 | 29.2 | 22.5 | 17.9 | 14.2 | 16.1 | 22.5 | 16.1 |
| Phi 3.5 - L100 10 | 23.3 | 19.2 | 23.3 | 15.0 | 16.7 | 21.7 | 20.8 | 20.8 | 20.5 | 24.2 | 10.7 | 15.8 | 22.0 |
| Phi 3.5 - L100 24 | 25.0 | 18.3 | 20.8 | 18.3 | 16.7 | 20.8 | 16.7 | 20.8 | 17.9 | 21.7 | 14.3 | 16.7 | 16.9 |
| Phi 3.5 - L100 50 | 18.3 | 19.5 | 16.7 | 20.8 | 19.2 | 25.8 | 20.0 | 16.7 | 25.0 | 20.8 | 13.4 | 17.5 | 18.6 |
| Phi 3.5 - L100 75 | 16.7 | 18.0 | 15.0 | 20.0 | 19.2 | 19.2 | 16.7 | 23.3 | 17.0 | 13.3 | 17.9 | 15.8 | 20.3 |
| Phi 3.5 - L100 90 | 22.5 | 19.0 | 20.0 | 16.7 | 15.8 | 20.0 | 16.7 | 23.3 | 21.4 | 23.3 | 16.1 | 15.8 | 19.5 |
| Llama 3 - L100 10 | 13.3 | 20.4 | 18.3 | 21.7 | 19.2 | 10.8 | 23.3 | 26.7 | 17.9 | 10.0 | 28.6 | 28.3 | 19.5 |
| Llama 3 - L100 50 | 12.5 | 20.6 | 19.2 | 20.8 | 20.0 | 10.8 | 24.2 | 30.0 | 15.2 | 10.8 | 28.6 | 27.5 | 19.5 |
| Llama 3 - L100 90 | 12.5 | 19.9 | 18.3 | 21.7 | 15.0 | 10.8 | 22.5 | 28.3 | 15.2 | 10.8 | 28.6 | 28.3 | 19.5 |
| Phi 3.5 - L100 50 | 18.3 | 19.5 | 16.7 | 20.8 | 19.2 | 25.8 | 20.0 | 16.7 | 25.0 | 20.8 | 13.4 | 17.5 | 18.6 |
| Phi 3.5 - PT 100 | 23.3 | 20.0 | 16.7 | 16.7 | 24.2 | 20.0 | 25.0 | 21.7 | 19.6 | 15.0 | 20.5 | 20.0 | 20.3 |
| Phi 3.5 - PT 50  | 20.0 | 18.6 | 18.3 | 17.5 | 15.0 | 15.8 | 14.2 | 21.7 | 17.9 | 23.3 | 20.5 | 20.8 | 19.5 |
| Phi 3.5 - PT 1  | 25.0 | 19.4 | 21.7 | 22.5 | 19.2 | 22.5 | 16.7 | 15.8 | 20.5 | 21.7 | 16.1 | 15.0 | 22.0 |
| Llama 3 - L100 50 | 12.5 | 20.6 | 19.2 | 20.8 | 20.0 | 10.8 | 24.2 | 30.0 | 15.2 | 10.8 | 28.6 | 27.5 | 19.5 |
| Llama 3 - PT 1  | 19.2 | 20.5 | 15.8 | 19.2 | 22.5 | 15.0 | 23.3 | 23.3 | 17.9 | 13.3 | 25.9 | 28.3 | 21.2 |
| Llama 3 - PT 100 | 13.3 | 20.8 | 18.3 | 21.7 | 20.0 | 12.5 | 23.3 | 29.2 | 17.0 | 10.8 | 28.6 | 28.3 | 19.5 |
| Gemma 2 - L100 50 | 14.2 | 21.1 | 18.3 | 22.5 | 20.8 | 10.8 | 25.0 | 28.3 | 16.1 | 11.7 | 27.7 | 30.0 | 20.3 |
| Llama 3 - L100 50 | 12.5 | 20.6 | 19.2 | 20.8 | 20.0 | 10.8 | 24.2 | 30.0 | 15.2 | 10.8 | 28.6 | 27.5 | 19.5 |
| Qwen 2.5 - L100 50 | 26.7 | 27.3 | 25.0 | 21.7 | 26.7 | 27.5 | 27.5 | 25.0 | 29.5 | 25.0 | 29.5 | 40.0 | 22.9 |
| Aya-Expanse - L100 50 | 12.5 | 20.7 | 18.3 | 21.7 | 20.0 | 10.8 | 24.2 | 29.2 | 15.2 | 10.8 | 28.6 | 29.2 | 19.5 |
| `Centurio` Aya     | 12.5 | 20.7 | 18.3 | 21.7 | 20.0 | 11.7 | 24.2 | 29.2 | 15.2 | 10.8 | 28.6 | 29.2 | 19.5 |
| `Centurio` Qwen    | 28.3 | 27.0 | 18.3 | 20.0 | 33.3 | 32.5 | 29.2 | 22.5 | 25.0 | 22.5 | 30.4 | 30.0 | 33.1 |{{< /table-caption >}}
> 🔼 표 21은 Visio-Linguistic Outlier Detection (VLOD) 데이터셋에 대한 결과를 보여줍니다. VLOD 데이터셋은 여러 언어로 된 텍스트 설명이 이미지와 일치하지 않는 다섯 개의 이미지를 포함하고, 모델은 이 설명과 일치하지 않는 이미지 하나를 찾아야 합니다. 표는 다양한 언어와 모델에 걸쳐 정확도를 보여주는 정량적 평가 결과를 요약한 것입니다.  각 열은 특정 언어 또는 모델의 평균 정확도를 나타내고, 각 행은 다양한 학습 전략과 모델 구성에 해당하는 결과를 보여줍니다. 영어와 다국어 모델 간의 성능 차이, 그리고 저자원 언어 대비 고자원 언어에서의 성능 차이를 비교 분석하는 데 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 21: VLOD
> </details>

{{< table-caption >}}
|               | en  | avg. | id  | sw  | ta  | tr  | zh  |
| :------------- | :-: | :-:  | :-: | :-: | :-: | :-: | :-: |
| Phi 3.5 - English | 82.1 | 61.4 | 65.6 | 50.8 | 53.3 | 63.8 | 73.2 |
| Phi 3.5 - T5 50  | 81.5 | 61.8 | 66.4 | 53.4 | 53.7 | 61.6 | 73.8 |
| Phi 3.5 - T5-4 50 | 81.2 | 64.3 | 68.7 | 52.3 | 54.3 | 70.2 | 76.2 |
| Phi 3.5 - T5-3 50 | 81.5 | 65.9 | 70.8 | 56.4 | 56.7 | 68.9 | 76.7 |
| Phi 3.5 - T5-2 50 | 79.7 | 66.4 | 70.2 | 62.2 | 57.5 | 66.7 | 75.4 |
| Phi 3.5 - L100 50 | 79.6 | 64.4 | 69.0 | 59.0 | 53.6 | 67.5 | 73.0 |
| Llama 3 - English | 85.2 | 65.0 | 68.8 | 52.5 | 54.3 | 69.7 | 79.8 |
| Llama 3 - T5 50  | 84.5 | 67.1 | 73.8 | 55.7 | 53.6 | 72.7 | 79.6 |
| Llama 3 - L100 50 | 83.7 | 74.2 | 75.3 | 71.4 | 68.4 | 79.8 | 76.0 |
| Phi 3.5 - L100 1  | 71.9 | 61.4 | 65.1 | 56.1 | 54.3 | 65.2 | 66.1 |
| Phi 3.5 - L100 10 | 74.1 | 63.4 | 66.8 | 58.1 | 57.2 | 65.1 | 70.0 |
| Phi 3.5 - L100 24 | 76.0 | 61.6 | 63.4 | 57.6 | 56.9 | 64.0 | 66.3 |
| Phi 3.5 - L100 50 | 79.6 | 64.4 | 69.0 | 59.0 | 53.6 | 67.5 | 73.0 |
| Phi 3.5 - L100 75 | 81.7 | 64.7 | 71.3 | 54.4 | 56.1 | 64.8 | 77.0 |
| Phi 3.5 - L100 90 | 83.1 | 64.3 | 70.7 | 56.3 | 53.8 | 62.8 | 77.8 |
| Llama 3 - L100 10 | 80.0 | 72.9 | 71.9 | 70.8 | 71.7 | 75.7 | 74.2 |
| Llama 3 - L100 50 | 83.7 | 74.2 | 75.3 | 71.4 | 68.4 | 79.8 | 76.0 |
| Llama 3 - L100 90 | 85.1 | 71.1 | 73.4 | 63.7 | 65.1 | 75.7 | 77.6 |
| Phi 3.5 - L100 50 | 79.6 | 64.4 | 69.0 | 59.0 | 53.6 | 67.5 | 73.0 |
| Phi 3.5 - PT 100 | 82.0 | 65.6 | 68.6 | 59.4 | 57.9 | 67.6 | 74.5 |
| Phi 3.5 - PT 50  | 82.5 | 69.9 | 75.2 | 64.0 | 64.1 | 71.1 | 74.9 |
| Phi 3.5 - PT 1   | 81.9 | 67.9 | 74.0 | 64.0 | 60.2 | 68.0 | 73.4 |
| Llama 3 - L100 50 | 83.7 | 74.2 | 75.3 | 71.4 | 68.4 | 79.8 | 76.0 |
| Llama 3 - PT 1   | 87.5 | 80.4 | 82.5 | 75.5 | 77.1 | 84.5 | 82.3 |
| Llama 3 - PT 100 | 86.5 | 78.9 | 81.3 | 73.0 | 75.1 | 83.4 | 81.5 |
| Gemma 2 - L100 50 | 82.5 | 73.0 | 72.6 | 71.4 | 68.3 | 76.4 | 76.2 |
| Llama 3 - L100 50 | 83.7 | 74.2 | 75.3 | 71.4 | 68.4 | 79.8 | 76.0 |
| Qwen 2.5 - L100 50 | 89.6 | 79.4 | 84.8 | 73.9 | 65.2 | 86.6 | 86.6 |
| Aya-Expanse - L100 50 | 87.0 | 80.2 | 83.9 | 75.6 | 71.7 | 86.9 | 83.0 |
| `Centurio` Aya  | 85.0 | 77.9 | 79.5 | 70.9 | 73.4 | 83.4 | 82.4 |
| `Centurio` Qwen | 89.6 | 81.7 | 85.0 | 76.8 | 76.0 | 84.2 | 86.7 |{{< /table-caption >}}
> 🔼 표 22는 논문의 MaRVL 섹션에 있는 표입니다. 이 표는 다양한 언어 모델의 다국어 이미지 이해 능력을 보여줍니다. 특히, MaRVL 데이터셋을 사용하여 이미지와 텍스트 간의 관계를 평가하는 다양한 작업의 정확도를 보여줍니다. 각 모델의 성능은 다양한 언어별로 구분되어 표시됩니다. 이는 다국어 능력이 모델의 성능에 미치는 영향을 분석하는 데 도움이 됩니다. Centurio 모델이 다른 모델에 비해 높은 정확도를 보이는 것을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 22: MaRVL
> </details>

{{< table-caption >}}
|                | en  | avg. | fr  | hi  | he  | ro  | th  | zh  |
|----------------|-----|------|-----|-----|-----|-----|-----|-----|
|Phi 3.5 - English | 53.0 | 9.2  | 14.3 | 11.9 | 7.9  | 7.2  | 7.0  | 7.2  |
|Phi 3.5 - T5 50  | 51.3 | 25.6 | 41.0 | 30.6 | 17.5 | 15.6 | 27.5 | 21.5 |
|Phi 3.5 - T5-4 50 | 51.0 | 33.1 | 45.4 | 50.7 | 27.0 | 23.7 | 32.5 | 19.5 |
|Phi 3.5 - T5-3 50 | 53.7 | 36.7 | 41.0 | 45.9 | 33.0 | 36.6 | 40.4 | 23.5 |
|Phi 3.5 - T5-2 50 | 53.4 | 35.9 | 42.3 | 48.0 | 33.3 | 35.1 | 32.8 | 23.8 |
|Phi 3.5 - L100 50 | 54.4 | 36.6 | 43.0 | 48.0 | 30.8 | 35.1 | 39.1 | 23.5 |
|Llama 3 - English | 55.4 | 7.7  | 9.2  | 10.9 | 6.7  | 4.5  | 8.3  | 6.8  |
|Llama 3 - T5 50  | 41.3 | 20.2 | 45.1 | 12.6 | 2.9  | 24.3 | 14.6 | 21.8 |
|Llama 3 - L100 50 | 52.7 | 42.3 | 42.3 | 54.4 | 40.6 | 40.5 | 52.6 | 23.1 |
|Phi 3.5 - L100 1  | 48.0 | 33.8 | 39.9 | 45.2 | 32.4 | 32.4 | 32.8 | 19.9 |
|Phi 3.5 - L100 10 | 52.0 | 35.4 | 44.7 | 45.6 | 34.6 | 36.0 | 29.5 | 22.1 |
|Phi 3.5 - L100 24 | 50.7 | 35.1 | 44.0 | 44.6 | 29.8 | 33.0 | 38.1 | 21.2 |
|Phi 3.5 - L100 50 | 54.4 | 36.6 | 43.0 | 48.0 | 30.8 | 35.1 | 39.1 | 23.5 |
|Phi 3.5 - L100 75 | 51.0 | 32.5 | 42.0 | 36.4 | 29.8 | 33.3 | 31.8 | 21.8 |
|Phi 3.5 - L100 90 | 54.7 | 29.7 | 41.6 | 28.2 | 27.3 | 28.5 | 30.5 | 21.8 |
|Llama 3 - L100 10 | 49.0 | 41.9 | 37.9 | 53.4 | 45.7 | 41.4 | 51.0 | 21.8 |
|Llama 3 - L100 50 | 52.7 | 42.3 | 42.3 | 54.4 | 40.6 | 40.5 | 52.6 | 23.1 |
|Llama 3 - L100 90 | 52.7 | 40.6 | 43.3 | 52.7 | 36.2 | 40.2 | 49.0 | 22.1 |
|Phi 3.5 - L100 50 | 54.4 | 36.6 | 43.0 | 48.0 | 30.8 | 35.1 | 39.1 | 23.5 |
|Phi 3.5 - PT 100 | 54.0 | 36.2 | 44.0 | 48.6 | 32.4 | 33.9 | 36.8 | 21.5 |
|Phi 3.5 - PT 50  | 53.4 | 39.0 | 45.7 | 49.3 | 39.4 | 36.6 | 40.7 | 22.1 |
|Phi 3.5 - PT 1   | 55.7 | 39.7 | 44.7 | 52.0 | 41.0 | 40.8 | 40.1 | 19.9 |
|Llama 3 - L100 50 | 52.7 | 42.3 | 42.3 | 54.4 | 40.6 | 40.5 | 52.6 | 23.1 |
|Llama 3 - PT 1   | 55.0 | 48.5 | 47.4 | 57.1 | 56.2 | 47.4 | 57.3 | 25.7 |
|Llama 3 - PT 100 | 58.1 | 47.4 | 44.7 | 54.8 | 54.0 | 47.1 | 57.3 | 26.4 |
|Gemma 2 - L100 50| 51.7 | 41.5 | 39.6 | 52.4 | 44.1 | 39.3 | 48.7 | 24.8 |
|Llama 3 - L100 50 | 52.7 | 42.3 | 42.3 | 54.4 | 40.6 | 40.5 | 52.6 | 23.1 |
|Qwen 2.5 - L100 50| 58.7 | 45.8 | 46.4 | 51.4 | 50.2 | 41.7 | 57.9 | 27.0 |
|Aya-Expanse - L100 50| 53.4 | 47.2 | 46.4 | 58.8 | 59.4 | 49.9 | 41.4 | 27.4 |
|Centurio Aya     | 55.7 | 49.3 | 45.1 | 62.9 | 58.7 | 51.1 | 46.7 | 31.6 |
|Centurio Qwen    | 60.1 | 47.7 | 47.1 | 56.8 | 45.1 | 47.7 | 57.0 | 32.2 |{{< /table-caption >}}
> 🔼 표 23은 논문의 2.3절 '지시어 미세조정에서의 언어 분포' 섹션에 속하며, 다양한 언어 비율로 학습된 모델의 MaXM(Massive Multi-lingual Plot Question Answering) 성능을 보여줍니다.  각 열은 영어(en) 또는 다국어(avg) 데이터 비율, 5가지 언어 계층(T1-T5) 및 개별 언어(fr, hi, he, ro, th, zh)별 평균 점수를 나타냅니다. 이 표는 다양한 언어 조합으로 모델을 훈련시킬 때의 성능 차이를 분석하는 데 도움이 됩니다.  특히 영어 데이터의 비율이 다국어 모델의 성능에 미치는 영향과 저자원 언어의 성능 향상에 대한 통찰력을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 23: MaXM
> </details>

{{< table-caption >}}
| Model | avg. | ar | de | fr | it | ja | ko | ru | th | vi |
|---|---|---|---|---|---|---|---|---|---|---|
| Phi 3.5 - English | 3.2 | 0.9 | 6.5 | 9.3 | 8.1 | 0.8 | 0.7 | 1.6 | 0.0 | 1.1 |
| Phi 3.5 - T5 50 | 5.7 | 1.7 | 12.0 | 15.9 | 10.1 | 2.4 | 3.8 | 2.6 | 0.9 | 1.8 |
| Phi 3.5 - T5-4 50 | 5.9 | 2.7 | 14.0 | 15.1 | 9.6 | 3.5 | 3.8 | 1.9 | 0.9 | 1.6 |
| Phi 3.5 - T5-3 50 | 5.8 | 2.0 | 13.5 | 14.6 | 9.4 | 3.9 | 3.8 | 2.4 | 0.9 | 2.0 |
| Phi 3.5 - T5-2 50 | 6.6 | 5.3 | 15.9 | 15.1 | 9.4 | 4.1 | 3.8 | 2.5 | 0.4 | 2.7 |
| Phi 3.5 - L100 50 | 6.3 | 2.8 | 15.8 | 16.8 | 8.9 | 3.9 | 2.7 | 2.8 | 0.4 | 2.9 |
| Llama 3 - English | 3.2 | 0.3 | 6.9 | 8.0 | 8.7 | 0.7 | 0.5 | 0.7 | 0.4 | 2.7 |
| Llama 3 - T5 50 | 5.6 | 2.0 | 14.2 | 15.0 | 9.1 | 1.9 | 1.4 | 2.6 | 1.3 | 2.8 |
| Llama 3 - L100 50 | 6.0 | 2.1 | 11.9 | 15.8 | 7.2 | 2.1 | 3.2 | 2.4 | 4.8 | 4.1 |
| Phi 3.5 - L100 1 | 4.7 | 2.0 | 12.0 | 9.4 | 7.5 | 3.4 | 3.4 | 1.9 | 0.9 | 2.3 |
| Phi 3.5 - L100 10 | 5.7 | 3.0 | 12.1 | 14.2 | 8.6 | 4.6 | 4.1 | 2.1 | 0.9 | 1.5 |
| Phi 3.5 - L100 24 | 6.2 | 3.6 | 14.0 | 15.8 | 8.7 | 3.1 | 3.8 | 3.3 | 0.9 | 2.5 |
| Phi 3.5 - L100 50 | 6.3 | 2.8 | 15.8 | 16.8 | 8.9 | 3.9 | 2.7 | 2.8 | 0.4 | 2.9 |
| Phi 3.5 - L100 75 | 6.3 | 2.6 | 13.8 | 18.3 | 8.7 | 4.3 | 2.9 | 2.8 | 0.9 | 2.8 |
| Phi 3.5 - L100 90 | 7.0 | 2.6 | 14.7 | 19.3 | 10.4 | 3.6 | 4.1 | 3.2 | 3.5 | 1.5 |
| Llama 3 - L100 10 | 5.3 | 1.6 | 11.3 | 13.8 | 7.5 | 2.9 | 3.4 | 2.6 | 0.9 | 3.5 |
| Llama 3 - L100 50 | 6.0 | 2.1 | 11.9 | 15.8 | 7.2 | 2.1 | 3.2 | 2.4 | 4.8 | 4.1 |
| Llama 3 - L100 90 | 6.5 | 2.1 | 14.0 | 17.8 | 9.7 | 2.5 | 3.8 | 2.8 | 2.2 | 3.5 |
| Phi 3.5 - L100 50 | 6.3 | 2.8 | 15.8 | 16.8 | 8.9 | 3.9 | 2.7 | 2.8 | 0.4 | 2.9 |
| Phi 3.5 - PT 100 | 6.9 | 3.7 | 16.0 | 15.9 | 11.3 | 3.4 | 3.2 | 2.9 | 2.2 | 3.5 |
| Phi 3.5 - PT 50 | 6.1 | 1.8 | 14.8 | 15.8 | 10.5 | 3.5 | 2.9 | 2.6 | 0.9 | 2.1 |
| Phi 3.5 - PT 1 | 6.2 | 1.6 | 14.9 | 15.9 | 11.1 | 3.7 | 3.0 | 1.7 | 0.9 | 2.7 |
| Llama 3 - L100 50 | 6.0 | 2.1 | 11.9 | 15.8 | 7.2 | 2.1 | 3.2 | 2.4 | 4.8 | 4.1 |
| Llama 3 - PT 1 | 6.9 | 2.4 | 17.1 | 16.6 | 9.1 | 3.4 | 4.5 | 2.5 | 1.7 | 5.2 |
| Llama 3 - PT 100 | 8.3 | 2.6 | 18.7 | 19.6 | 11.4 | 4.0 | 4.3 | 4.0 | 4.8 | 5.3 |
| Gemma 2 - L100 50 | 4.3 | 1.7 | 11.1 | 8.1 | 7.1 | 3.0 | 2.3 | 2.1 | 1.7 | 1.7 |
| Llama 3 - L100 50 | 6.0 | 2.1 | 11.9 | 15.8 | 7.2 | 2.1 | 3.2 | 2.4 | 4.8 | 4.1 |
| Qwen 2.5 - L100 50 | 6.4 | 5.5 | 12.0 | 13.0 | 10.3 | 3.0 | 3.2 | 2.9 | 2.2 | 5.2 |
| Aya-Expanse - L100 50 | 6.2 | 3.7 | 13.2 | 13.9 | 9.5 | 3.0 | 3.4 | 3.4 | 1.7 | 3.6 |
| Centurio Aya | 11.1 | 6.7 | 19.9 | 22.5 | 16.7 | 5.0 | 9.0 | 5.2 | 5.2 | 9.7 |
| Centurio Qwen | 11.9 | 4.6 | 22.7 | 26.5 | 18.6 | 5.9 | 9.9 | 5.0 | 5.2 | 8.9 |{{< /table-caption >}}
> 🔼 표 24는 다국어 시각적 질문 답변(MTVQA) 데이터셋에 대한 실험 결과를 보여줍니다.  각 언어별로 평균 정확도 점수를 보여주는 표이며, 다양한 사전 훈련 및 지시 조정 전략(예: 영어 데이터 비율 조정, 다국어 데이터 포함 여부 등)이 모델 성능에 미치는 영향을 분석하기 위한 것입니다.  표에서 확인할 수 있는 정보는 모델 이름, 사용된 언어, 그리고 각 언어에 대한 평균 정확도 점수입니다. 이를 통해 다국어 능력에 영향을 미치는 요인을 분석하고, 최적의 훈련 전략을 찾는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 24: MTVQA
> </details>

{{< table-caption >}}
|               | en   | avg. | bn   | de   | id   | ko   | pt   | ru   | zh   |
| :------------- | :--- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| Phi 3.5 - English | 59.7 | 37.2  | 4.9  | 47.8 | 33.2 | 38.2 | 47.1 | 42.1 | 47.2 |
| Phi 3.5 - T5 50  | 54.1 | 34.1  | 2.6  | 44.6 | 34.3 | 36.3 | 43.8 | 36.4 | 41.0 |
| Phi 3.5 - T5-4 50 | 52.0 | 37.4  | 5.7  | 45.6 | 38.7 | 40.4 | 45.2 | 43.4 | 42.7 |
| Phi 3.5 - T5-3 50 | 54.8 | 40.6  | 22.7 | 46.5 | 42.1 | 39.8 | 46.0 | 43.6 | 43.6 |
| Phi 3.5 - T5-2 50 | 57.8 | 45.3  | 27.4 | 50.3 | 46.0 | 46.4 | 48.6 | 49.5 | 48.9 |
| Phi 3.5 - L100 50 | 56.6 | 45.1  | 27.0 | 51.4 | 44.8 | 44.9 | 50.8 | 48.2 | 48.7 |
| Llama 3 - English | 61.9 | 39.2  | 13.2 | 49.0 | 35.6 | 39.1 | 44.9 | 44.1 | 48.4 |
| Llama 3 - T5 50  | 49.3 | 33.8  | 5.9  | 43.8 | 38.0 | 32.4 | 41.7 | 37.3 | 37.4 |
| Llama 3 - L100 50 | 60.6 | 51.0  | 46.7 | 54.1 | 51.2 | 49.4 | 53.4 | 51.2 | 51.3 |
| Phi 3.5 - L100 1  | 48.4 | 40.3  | 28.2 | 43.9 | 41.1 | 40.6 | 43.0 | 42.8 | 42.8 |
| Phi 3.5 - L100 10 | 51.8 | 42.2  | 27.6 | 46.3 | 43.0 | 42.2 | 45.7 | 44.8 | 45.6 |
| Phi 3.5 - L100 24 | 53.8 | 42.9  | 29.1 | 47.6 | 43.4 | 42.2 | 46.6 | 45.9 | 45.4 |
| Phi 3.5 - L100 50 | 56.6 | 45.1  | 27.0 | 51.4 | 44.8 | 44.9 | 50.8 | 48.2 | 48.7 |
| Phi 3.5 - L100 75 | 58.6 | 45.8  | 26.4 | 52.4 | 44.4 | 45.4 | 51.9 | 49.9 | 50.0 |
| Phi 3.5 - L100 90 | 58.5 | 42.1  | 14.2 | 53.0 | 39.8 | 43.3 | 51.4 | 45.7 | 47.7 |
| Llama 3 - L100 10 | 54.9 | 45.0  | 40.5 | 46.4 | 45.7 | 42.5 | 46.5 | 46.2 | 47.4 |
| Llama 3 - L100 50 | 60.6 | 51.0  | 46.7 | 54.1 | 51.2 | 49.4 | 53.4 | 51.2 | 51.3 |
| Llama 3 - L100 90 | 61.9 | 51.4  | 42.5 | 56.2 | 51.7 | 50.1 | 54.6 | 52.5 | 52.1 |
| Phi 3.5 - L100 50 | 56.6 | 45.1  | 27.0 | 51.4 | 44.8 | 44.9 | 50.8 | 48.2 | 48.7 |
| Phi 3.5 - PT 100  | 58.0 | 46.1  | 29.5 | 52.8 | 46.1 | 44.5 | 51.7 | 49.5 | 48.3 |
| Phi 3.5 - PT 50   | 58.3 | 47.6  | 35.4 | 52.8 | 48.7 | 45.5 | 52.5 | 49.6 | 48.6 |
| Phi 3.5 - PT 1   | 58.3 | 47.0  | 37.6 | 52.6 | 46.8 | 44.1 | 51.5 | 48.1 | 48.1 |
| Llama 3 - L100 50 | 60.6 | 51.0  | 46.7 | 54.1 | 51.2 | 49.4 | 53.4 | 51.2 | 51.3 |
| Llama 3 - PT 1   | 61.1 | 55.1  | 52.8 | 56.6 | 56.0 | 53.9 | 56.0 | 55.4 | 55.0 |
| Llama 3 - PT 100  | 61.6 | 53.0  | 50.4 | 54.9 | 53.6 | 52.4 | 53.0 | 53.1 | 53.4 |
| Gemma 2 - L100 50 | 56.5 | 47.5  | 43.9 | 51.6 | 47.6 | 44.2 | 50.1 | 47.5 | 47.5 |
| Llama 3 - L100 50 | 60.6 | 51.0  | 46.7 | 54.1 | 51.2 | 49.4 | 53.4 | 51.2 | 51.3 |
| Qwen 2.5 - L100 50| 60.3 | 51.9  | 44.2 | 54.8 | 53.1 | 51.3 | 54.3 | 53.2 | 52.8 |
| Aya-Expanse - L100 50| 60.5 | 52.5  | 45.2 | 54.6 | 53.8 | 51.7 | 54.7 | 53.9 | 53.4 |
| `Centurio` Aya   | 59.1 | 53.2  | 43.4 | 56.9 | 54.4 | 53.6 | 56.2 | 54.0 | 54.3 |
| `Centurio` Qwen  | 60.6 | 54.8  | 49.9 | 57.0 | 54.9 | 53.5 | 57.2 | 55.8 | 55.6 |{{< /table-caption >}}
> 🔼 표 25는 논문의 xGQA 결과를 보여줍니다. xGQA는 다국어 시각적 질의응답 데이터셋으로, 영어 이외의 다양한 언어로 된 질문과 답변 쌍을 포함하고 있습니다. 이 표는 다양한 언어 및 학습 전략(예: 영어 전용, 다국어, 사전 학습된 모델 등)에 따른 모델 성능을 비교 분석하여 다국어 기능에 대한 통찰력을 제공합니다. 각 행은 특정 언어와 학습 설정에 대한 모델 성능(정확도)을 나타내며, 다양한 언어에 대한 모델의 성능 차이를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 25: xGQA
> </details>

{{< table-caption >}}
Model|en|avg.|ar|bn|cs|da|de|el|es|fa|fi|fil|fr|he|hi|hr|hu|id|it|ja|ko|mi|nl|no|pl|pt|quz|ro|ru|sv|sw|te|th|tr|uk|vi|zh
---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---
Phi 3.5 - English|33.6|1.2|0.0|0.0|0.7|1.1|1.7|0.0|10.5|0.0|0.4|1.6|4.4|0.0|0.0|0.5|0.6|1.5|9.2|0.1|0.0|0.0|1.6|1.5|0.7|1.9|0.1|0.7|0.4|1.1|0.6|0.0|0.2|0.3|0.1|0.6|0.0
Phi 3.5 - T5 50|33.0|9.5|7.8|0.6|3.9|8.2|24.7|0.6|34.4|0.4|1.8|1.9|39.1|3.4|3.5|2.6|4.0|7.9|28.5|27.6|1.6|0.1|20.4|8.8|4.8|30.2|0.7|5.4|17.5|11.8|1.3|0.0|4.0|3.2|5.7|2.6|12.8
Phi 3.5 - T5-4 50|25.2|11.8|6.9|1.0|13.8|10.8|24.4|1.4|27.3|8.6|7.0|3.6|31.3|3.5|9.7|9.2|10.5|8.4|24.9|27.9|3.1|2.1|21.7|12.0|14.1|24.0|0.5|6.0|22.5|24.1|2.1|0.0|5.8|9.4|4.6|18.8|10.6
Phi 3.5 - T5-3 50|32.7|13.6|6.5|5.9|13.8|18.2|25.4|7.0|31.0|7.1|5.7|11.9|30.7|7.6|7.2|9.4|8.2|22.9|26.0|27.3|3.0|1.8|28.5|14.1|13.6|22.1|0.4|11.0|16.7|23.8|1.5|0.0|12.9|7.6|10.0|15.9|20.2
Phi 3.5 - T5-2 50|29.9|11.1|4.5|5.5|10.7|12.4|20.4|6.4|20.4|5.7|5.5|10.1|24.8|7.4|6.7|8.0|7.1|17.5|18.5|27.0|2.5|2.0|18.9|11.2|10.0|18.1|0.4|7.6|21.1|17.8|7.0|0.0|12.6|7.9|10.3|12.7|9.5
Phi 3.5 - L100 50|31.0|13.2|5.6|3.3|10.9|18.0|26.4|4.5|30.9|4.1|4.4|11.1|38.5|6.7|6.3|7.3|7.8|22.4|30.6|23.7|2.5|2.6|24.2|18.8|10.8|29.0|1.1|8.1|18.6|17.8|8.1|1.5|10.2|7.2|8.3|14.7|15.6
Llama 3 - English|75.6|1.1|0.1|0.0|1.3|2.3|1.6|0.1|2.1|0.1|0.8|2.9|3.4|0.0|0.0|0.7|1.3|2.1|1.5|0.2|0.0|0.2|3.0|1.8|1.1|2.6|0.8|1.2|0.7|2.0|0.8|0.0|0.4|0.5|0.3|0.5|0.3
Llama 3 - T5 50|76.1|12.6|27.9|0.5|1.6|20.7|29.2|0.6|61.6|0.4|1.1|2.9|58.2|0.0|0.4|0.9|1.6|19.6|26.8|35.8|0.1|0.2|34.9|15.7|11.3|12.5|1.3|5.4|12.8|18.3|0.6|0.0|4.4|6.1|0.2|10.1|17.2
Llama 3 - L100 50|72.6|28.5|25.6|14.0|30.5|38.1|27.6|23.3|56.0|24.3|13.8|29.0|50.9|15.5|22.5|19.7|18.0|39.9|44.1|33.8|13.4|24.9|50.1|41.5|26.9|45.1|1.3|22.6|23.5|42.7|28.9|11.0|27.7|21.8|21.9|49.7|16.9
Phi 3.5 - L100 1|43.3|13.3|5.2|4.3|11.1|15.3|24.5|5.3|25.4|5.4|6.1|13.3|37.1|7.0|7.2|7.9|6.7|22.6|28.1|25.4|2.1|4.0|22.3|17.7|12.0|24.9|1.4|10.7|21.4|17.8|11.1|1.4|12.6|7.6|8.2|17.2|16.9
Phi 3.5 - L100 10|38.9|12.7|4.7|4.1|11.4|12.5|23.6|5.9|28.1|4.8|5.3|14.2|33.3|8.5|8.6|8.2|6.3|22.6|23.3|25.2|2.4|3.0|23.0|15.6|12.0|25.8|0.7|8.2|20.0|15.9|9.9|1.8|11.8|6.7|11.9|14.7|11.8
Phi 3.5 - L100 24|31.5|13.2|5.2|5.0|11.6|15.1|22.6|6.9|30.9|4.9|6.1|12.0|39.2|8.2|7.7|8.2|5.1|22.4|24.7|25.8|3.3|4.8|24.8|18.5|13.6|17.7|0.7|9.1|17.8|17.5|9.3|2.3|13.3|6.5|9.6|15.4|14.4
Phi 3.5 - L100 50|31.0|13.2|5.6|3.3|10.9|18.0|26.4|4.5|30.9|4.1|4.4|11.1|38.5|6.7|6.3|7.3|7.8|22.4|30.6|23.7|2.5|2.6|24.2|18.8|10.8|29.0|1.1|8.1|18.6|17.8|8.1|1.5|10.2|7.2|8.3|14.7|15.6
Phi 3.5 - L100 75|36.5|12.0|4.4|2.5|9.1|13.6|25.0|3.0|25.7|3.4|3.8|7.1|33.6|6.3|5.2|5.9|7.0|20.2|29.7|24.8|2.0|3.3|23.0|17.1|9.8|27.8|0.8|6.2|19.6|15.2|5.0|1.4|10.9|5.7|8.9|13.0|18.5
Phi 3.5 - L100 90|34.2|9.4|4.0|1.9|6.7|9.2|21.8|2.8|23.4|2.0|3.8|4.1|26.2|4.4|3.7|4.7|4.9|12.5|21.3|21.3|2.0|1.2|12.7|11.8|7.3|22.5|0.8|5.9|16.3|16.1|5.6|0.6|7.5|3.9|7.8|8.8|20.3
Llama 3 - L100 10|74.8|28.9|23.0|11.9|25.8|43.6|26.0|24.6|53.7|24.9|16.0|30.2|52.6|17.1|20.1|20.5|18.5|43.3|40.3|35.0|13.9|29.4|53.4|41.9|25.6|44.8|1.6|19.8|25.3|44.0|30.3|13.8|28.8|22.1|21.1|47.4|20.2
Llama 3 - L100 50|72.6|28.5|25.6|14.0|30.5|38.1|27.6|23.3|56.0|24.3|13.8|29.0|50.9|15.5|22.5|19.7|18.0|39.9|44.1|33.8|13.4|24.9|50.1|41.5|26.9|45.1|1.3|22.6|23.5|42.7|28.9|11.0|27.7|21.8|21.9|49.7|16.9
Llama 3 - L100 90|73.6|23.0|18.2|7.8|24.1|36.7|23.0|19.5|54.2|17.6|10.5|24.0|51.9|9.7|20.2|15.4|15.3|33.0|38.0|25.6|10.4|17.5|46.1|33.1|19.8|41.2|0.2|17.1|20.6|38.1|14.6|5.8|23.2|16.3|0.3|43.9|13.3
Phi 3.5 - L100 50|31.0|13.2|5.6|3.3|10.9|18.0|26.4|4.5|30.9|4.1|4.4|11.1|38.5|6.7|6.3|7.3|7.8|22.4|30.6|23.7|2.5|2.6|24.2|18.8|10.8|29.0|1.1|8.1|18.6|17.8|8.1|1.5|10.2|7.2|8.3|14.7|15.6
Phi 3.5 - PT 100|35.9|13.5|5.3|5.0|13.9|15.7|26.5|5.9|29.6|5.4|4.1|9.1|33.5|8.3|6.9|8.8|7.1|22.3|30.3|25.7|2.7|3.9|21.6|20.1|12.0|21.8|0.9|9.5|19.5|18.9|8.5|1.4|13.6|7.5|8.5|14.9|23.9
Phi 3.5 - PT 50|37.1|17.3|7.7|9.0|16.5|21.2|27.8|9.3|38.0|8.2|7.0|15.2|42.4|10.9|10.4|11.8|9.7|28.5|33.9|26.2|3.2|7.2|30.0|24.7|16.1|29.1|2.5|14.7|21.3|24.1|15.3|4.3|18.6|8.0|9.8|19.4|22.3
Phi 3.5 - PT 1|33.1|17.4|6.3|9.3|17.2|22.1|26.9|8.2|37.5|9.1|7.2|13.9|40.6|12.2|9.1|11.5|11.1|28.9|34.8|30.5|2.9|7.9|27.7|26.4|14.9|31.2|2.3|14.4|22.4|23.8|14.7|4.4|18.4|10.8|10.5|18.8|21.1
Llama 3 - L100 50|72.6|28.5|25.6|14.0|30.5|38.1|27.6|23.3|56.0|24.3|13.8|29.0|50.9|15.5|22.5|19.7|18.0|39.9|44.1|33.8|13.4|24.9|50.1|41.5|26.9|45.1|1.3|22.6|23.5|42.7|28.9|11.0|27.7|21.8|21.9|49.7|16.9
Llama 3 - PT 1|80.8|35.3|30.6|15.4|35.5|51.3|34.0|28.2|65.4|32.3|17.9|36.3|62.5|24.6|27.4|26.9|24.7|49.2|51.6|38.7|15.2|35.9|59.1|49.2|32.5|51.1|2.9|30.7|32.3|51.8|38.0|17.4|36.2|29.3|26.4|58.1|16.5
Llama 3 - PT 100|77.9|31.8|26.1|14.4|35.4|43.5|33.4|27.0|60.7|23.0|14.6|31.7|58.9|18.2|24.6|22.2|22.6|45.2|49.2|35.9|14.0|26.5|55.3|45.8|32.3|51.6|0.9|25.2|30.7|47.7|29.3|12.4|32.0|27.0|25.2|56.0|15.2
Gemma 2 - L100 50|66.6|27.5|24.5|17.9|28.6|35.1|26.0|18.2|54.7|29.4|13.7|26.8|54.3|22.8|21.6|17.7|20.1|43.8|39.7|36.3|11.5|21.5|46.2|38.7|25.1|45.3|1.8|21.7|24.0|37.9|27.2|13.1|28.5|19.0|0.2|50.1|18.5
Llama 3 - L100 50|72.6|28.5|25.6|14.0|30.5|38.1|27.6|23.3|56.0|24.3|13.8|29.0|50.9|15.5|22.5|19.7|18.0|39.9|44.1|33.8|13.4|24.9|50.1|41.5|26.9|45.1|1.3|22.6|23.5|42.7|28.9|11.0|27.7|21.8|21.9|49.7|16.9
Qwen 2.5 - L100 50|74.8|27.8|28.6|13.9|26.1|35.4|29.6|11.6|58.7|17.1|10.2|26.0|55.6|22.2|16.3|19.8|11.7|40.3|43.8|39.0|13.4|21.8|48.9|36.6|25.0|52.3|0.9|16.9|33.6|36.7|18.9|8.0|38.1|17.4|18.1|59.5|19.9
Aya-Expanse - L100 50|75.6|33.4|40.4|12.2|39.4|37.7|32.7|31.9|69.2|41.6|8.4|26.2|67.6|42.5|24.5|19.1|12.5|50.3|53.6|39.5|18.4|20.1|59.6|36.3|35.5|50.6|0.7|31.3|31.9|34.9|21.3|9.2|19.0|29.8|27.7|68.2|26.1
Centurio Aya|78.4|39.2|40.4|18.5|33.9|40.0|38.6|35.3|69.7|55.8|11.0|34.0|71.3|47.1|26.3|24.9|19.6|58.3|60.4|49.1|21.3|33.7|61.7|42.5|37.9|59.3|1.7|34.6|38.0|45.9|29.9|15.1|26.0|30.6|30.6|72.7|56.9
Centurio Qwen|79.1|34.4|36.6|17.1|29.7|43.1|32.0|19.2|69.2|31.2|12.0|33.6|67.6|27.6|20.3|22.0|18.7|50.4|53.7|43.5|13.4|34.9|56.2|41.4|30.0|59.9|2.1|23.4|39.2|42.7|30.2|13.5|42.3|23.3|20.3|69.4|33.8{{< /table-caption >}}
> 🔼 표 26은 XM3600 데이터셋에 대한 결과를 보여줍니다.  XM3600은 다양한 언어(총 36개 언어)로 된 이미지 캡션 데이터셋입니다. 표는 다양한 언어 모델의 성능을 보여주며, 각 모델별로 영어(en)와 다국어(mul) 성능을 비교합니다.  또한, 각 언어별 정확도를 보여주는 세부적인 수치를 포함하고 있습니다.  이 표는 논문의 다국어 비전-언어 모델의 성능 평가 부분에서 사용되었습니다.
> <details>
> <summary>read the caption</summary>
> Table 26: XM3600
> </details>

{{< table-caption >}}
| | **ar** | **bn** | **cs** | **da** | **de** | **el** | **en** | **es** | **fa** | **fi** | **fil** | **fr** | **he** | **hi** | **hr** | **hu** | **id** | **it** | **ja** | **ko** | **mi** | **nl** | **no** | **pl** | **pt** | **quz** | **ro** | **ru** | **sv** | **sw** | **te** | **th** | **tr** | **uk** | **vi** | **zh** |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Phi 3.5 - L100 | 93.8 | 99.0 | 99.0 | 91.8 | 100.0 | 88.3 | 100.0 | 100.0 | 98.8 | 100.0 | 96.7 | 100.0 | 99.6 | 97.7 | 76.2 | 100.0 | 95.3 | 100.0 | 99.2 | 99.8 | 100.0 | 100.0 | 98.4 | 100.0 | 97.7 | 0.2 | 100.0 | 99.8 | 98.6 | 98.2 | 93.2 | 99.8 | 100.0 | 92.6 | 100.0 | 96.5 |
| Phi 3.5 - T5-2 | 94.7 | 100.0 | 99.4 | 98.4 | 100.0 | 99.8 | 100.0 | 100.0 | 100.0 | 100.0 | 99.6 | 100.0 | 100.0 | 98.8 | 79.1 | 100.0 | 88.5 | 100.0 | 99.8 | 100.0 | 97.3 | 100.0 | 85.7 | 100.0 | 99.2 | 27.5 | 100.0 | 99.8 | 99.6 | 99.0 | 63.5 | 100.0 | 100.0 | 96.9 | 100.0 | 93.9 |
| Phi 3.5 - T5-3 | 92.2 | 99.8 | 99.2 | 97.9 | 100.0 | 99.8 | 100.0 | 100.0 | 100.0 | 100.0 | 99.6 | 100.0 | 99.8 | 99.0 | 77.9 | 100.0 | 91.8 | 100.0 | 100.0 | 100.0 | 95.9 | 100.0 | 75.2 | 100.0 | 52.1 | 37.5 | 100.0 | 100.0 | 99.2 | 84.4 | 82.8 | 100.0 | 100.0 | 96.5 | 100.0 | 95.3 |
| Phi 3.5 - T5-4 | 96.5 | 96.1 | 99.2 | 78.3 | 100.0 | 98.4 | 100.0 | 100.0 | 100.0 | 100.0 | 99.6 | 100.0 | 99.4 | 98.6 | 89.8 | 100.0 | 98.0 | 100.0 | 100.0 | 100.0 | 95.7 | 100.0 | 71.5 | 100.0 | 100.0 | 12.7 | 100.0 | 100.0 | 100.0 | 84.6 | 67.2 | 99.0 | 100.0 | 30.9 | 100.0 | 94.1 |
| Phi 3.5 - T5 | 98.2 | 97.3 | 78.7 | 87.5 | 100.0 | 50.2 | 100.0 | 99.8 | 2.3 | 76.4 | 49.4 | 100.0 | 96.7 | 99.2 | 73.6 | 99.2 | 95.1 | 100.0 | 100.0 | 99.8 | 1.6 | 99.8 | 92.0 | 96.5 | 100.0 | 0.2 | 96.3 | 100.0 | 98.6 | 36.1 | 62.5 | 90.2 | 94.9 | 91.6 | 39.8 | 96.7 |{{< /table-caption >}}
> 🔼 표 27은 논문의 2.2절에서 언급된 다양한 언어 조합으로 학습된 모델들의 XM3600 데이터셋에 대한 언어 충실도(language fidelity)를 보여줍니다.  언어 충실도는 모델이 지시된 언어로 출력을 생성하는 능력을 측정한 지표입니다.  표는 다양한 언어 조합(단일 언어, 영어+다른 언어 조합, 모든 언어 조합)으로 사전 학습 및 지시 조정이 이루어진 모델들의 성능을 언어별로 보여주어,  다양한 학습 전략이 언어 충실도에 미치는 영향을 분석하는 데 도움을 줍니다.  구체적으로는 각 언어 조합에 대한 영어 데이터 비율을 달리하여 언어 충실도에 어떤 영향을 주는지 확인합니다.
> <details>
> <summary>read the caption</summary>
> Table 27: XM3600 language fidelity (§1(b))
> </details>

{{< table-caption >}}
|               | en   | avg. | ar   | es   | fr   | ru   |
|---------------|------|------|------|------|------|------|
|Phi 3.5 - English| 59.6 | 55.0 | 52.3 | 54.9 | 57.6 | 55.2 |
|Phi 3.5 - T5 50 | 59.9 | 51.8 | 49.7 | 51.3 | 55.2 | 51.0 |
|Phi 3.5 - T5-4 50| 58.9 | 48.3 | 47.7 | 47.1 | 51.2 | 47.3 |
|Phi 3.5 - T5-3 50| 58.6 | 50.5 | 46.6 | 51.3 | 52.6 | 51.3 |
|Phi 3.5 - T5-2 50| 58.5 | 53.6 | 50.7 | 54.7 | 55.1 | 54.0 |
|Phi 3.5 - L100 50| 59.6 | 53.3 | 49.9 | 53.7 | 56.8 | 52.6 |
|Llama 3 - English| 46.1 | 36.3 | 33.4 | 37.0 | 36.5 | 38.2 |
|Llama 3 - T5 50 | 45.4 | 37.5 | 36.6 | 36.1 | 38.7 | 38.7 |
|Llama 3 - L100 50| 59.7 | 54.8 | 53.0 | 54.7 | 56.3 | 55.4 |
|Phi 3.5 - L100 1 | 55.2 | 48.2 | 42.2 | 50.6 | 51.1 | 48.8 |
|Phi 3.5 - L100 10| 58.3 | 53.4 | 50.5 | 54.3 | 55.7 | 53.1 |
|Phi 3.5 - L100 24| 58.2 | 48.4 | 43.5 | 50.3 | 52.7 | 47.3 |
|Phi 3.5 - L100 50| 59.6 | 53.3 | 49.9 | 53.7 | 56.8 | 52.6 |
|Phi 3.5 - L100 75| 61.9 | 54.5 | 50.3 | 56.2 | 57.5 | 54.2 |
|Phi 3.5 - L100 90| 60.0 | 50.5 | 43.6 | 53.8 | 55.1 | 49.5 |
|Llama 3 - L100 10| 60.8 | 55.3 | 56.3 | 52.6 | 55.0 | 57.1 |
|Llama 3 - L100 50| 59.7 | 54.8 | 53.0 | 54.7 | 56.3 | 55.4 |
|Llama 3 - L100 90| 57.8 | 51.1 | 48.9 | 52.3 | 52.1 | 51.0 |
|Phi 3.5 - L100 50| 59.6 | 53.3 | 49.9 | 53.7 | 56.8 | 52.6 |
|Phi 3.5 - PT 100 | 54.3 | 45.4 | 40.1 | 47.8 | 49.4 | 44.4 |
|Phi 3.5 - PT 50 | 58.9 | 52.5 | 49.0 | 53.8 | 54.6 | 52.5 |
|Phi 3.5 - PT 1  | 56.8 | 49.7 | 46.8 | 49.6 | 53.9 | 48.6 |
|Llama 3 - L100 50| 59.7 | 54.8 | 53.0 | 54.7 | 56.3 | 55.4 |
|Llama 3 - PT 1  | 61.7 | 59.4 | 58.8 | 59.0 | 60.0 | 59.7 |
|Llama 3 - PT 100| 60.3 | 57.3 | 56.5 | 56.5 | 58.3 | 57.8 |
|Gemma 2 - L100 50| 59.9 | 55.0 | 53.1 | 54.6 | 57.1 | 55.1 |
|Llama 3 - L100 50| 59.7 | 54.8 | 53.0 | 54.7 | 56.3 | 55.4 |
|Qwen 2.5 - L100 50| 57.8 | 52.6 | 55.7 | 47.5 | 52.5 | 54.8 |
|Aya-Expanse - L100 50| 58.2 | 54.7 | 54.7 | 54.0 | 56.4 | 53.5 |
|Centurio Aya     | 65.0 | 62.4 | 61.7 | 61.0 | 64.3 | 62.7 |
|Centurio Qwen    | 75.4 | 70.2 | 68.8 | 70.9 | 70.5 | 70.8 |{{< /table-caption >}}
> 🔼 표 28은 XVNLI(Cross-lingual Visual Natural Language Inference) 데이터셋에 대한 다양한 언어 모델의 성능을 보여줍니다.  XVNLI는 이미지와 텍스트 가설을 입력받아 가설이 이미지를 묘사하는지 여부를 판단하는 과제입니다. 표는 다양한 모델(Centurio, Parrot, PALO, InternVL, Qwen2-VL, Maya, Phi-3.5 Vision, Pixtral, Pangea, MiniCPM 등)의 정확도를 다양한 언어(영어, 아랍어, 스페인어, 프랑스어, 러시아어 등)에 대해 비교합니다.  각 모델은 단일 언어 및 다중 언어 설정에서 평가되어 다국어 능력을 평가합니다. 이 표는 다양한 언어 모델 아키텍처와 학습 전략이 다국어 시각적 언어 추론 작업의 성능에 미치는 영향을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 28: XVNLI
> </details>

{{< table-caption >}}
|                   | en   | avg. | ar   | fr   | hi   | id   | ja   | pt   |
|-------------------|------|-------|------|------|------|------|------|------|
| Phi 3.5 - English | 38.4 | 36.2 | 36.2 | 41.9 | 29.9 | 35.4 | 34.2 | 39.7 |
| Phi 3.5 - T5 50   | 36.7 | 36.2 | 31.5 | 38.9 | 31.6 | 37.0 | 34.9 | 43.4 |
| Phi 3.5 - T5-4 50 | 37.0 | 33.9 | 33.2 | 39.9 | 29.2 | 32.3 | 31.2 | 37.7 |
| Phi 3.5 - T5-3 50 | 37.3 | 35.8 | 32.5 | 39.3 | 32.3 | 37.0 | 36.8 | 37.0 |
| Phi 3.5 - T5-2 50 | 37.6 | 35.1 | 32.2 | 40.3 | 32.6 | 34.7 | 32.3 | 38.7 |
| Phi 3.5 - L100 50 | 36.6 | 32.0 | 28.5 | 35.9 | 27.8 | 32.0 | 31.2 | 36.7 |
| Llama 3 - English | 33.2 | 32.4 | 30.9 | 34.2 | 30.6 | 32.7 | 30.5 | 35.7 |
| Llama 3 - T5 50   | 33.4 | 32.4 | 34.9 | 36.6 | 28.9 | 31.3 | 30.9 | 31.6 |
| Llama 3 - L100 50 | 33.0 | 31.7 | 31.5 | 34.6 | 34.0 | 31.6 | 27.9 | 30.6 |
| Phi 3.5 - L100 1  | 37.3 | 34.1 | 32.5 | 40.3 | 30.9 | 31.3 | 31.6 | 37.7 |
| Phi 3.5 - L100 10 | 36.1 | 30.9 | 27.5 | 33.9 | 28.2 | 28.6 | 32.7 | 34.7 |
| Phi 3.5 - L100 24 | 34.4 | 31.9 | 28.5 | 35.9 | 29.2 | 30.3 | 33.5 | 34.0 |
| Phi 3.5 - L100 50 | 36.6 | 32.0 | 28.5 | 35.9 | 27.8 | 32.0 | 31.2 | 36.7 |
| Phi 3.5 - L100 75 | 36.2 | 33.2 | 31.9 | 38.9 | 29.2 | 32.7 | 29.0 | 37.4 |
| Phi 3.5 - L100 90 | 37.1 | 31.9 | 30.5 | 35.6 | 25.8 | 31.0 | 33.8 | 34.7 |
| Llama 3 - L100 10 | 32.6 | 30.0 | 26.8 | 31.5 | 26.8 | 31.6 | 32.0 | 31.3 |
| Llama 3 - L100 50 | 33.0 | 31.7 | 31.5 | 34.6 | 34.0 | 31.6 | 27.9 | 30.6 |
| Llama 3 - L100 90 | 32.7 | 33.5 | 30.5 | 35.9 | 30.9 | 35.4 | 31.2 | 37.0 |
| Phi 3.5 - L100 50 | 36.6 | 32.0 | 28.5 | 35.9 | 27.8 | 32.0 | 31.2 | 36.7 |
| Phi 3.5 - PT 100  | 33.4 | 30.2 | 28.5 | 32.9 | 28.9 | 30.0 | 27.5 | 33.3 |
| Phi 3.5 - PT 50   | 35.0 | 33.4 | 30.9 | 39.3 | 33.7 | 31.0 | 30.5 | 35.0 |
| Phi 3.5 - PT 1   | 36.0 | 31.3 | 26.5 | 35.9 | 29.2 | 32.0 | 28.3 | 36.0 |
| Llama 3 - L100 50 | 33.0 | 31.7 | 31.5 | 34.6 | 34.0 | 31.6 | 27.9 | 30.6 |
| Llama 3 - PT 1   | 38.6 | 35.2 | 33.9 | 34.2 | 34.0 | 35.0 | 36.1 | 38.0 |
| Llama 3 - PT 100  | 36.9 | 36.1 | 34.6 | 36.2 | 36.8 | 36.7 | 36.1 | 36.0 |
| Gemma 2 - L100 50 | 32.8 | 32.0 | 32.5 | 30.9 | 33.0 | 30.6 | 32.7 | 32.0 |
| Llama 3 - L100 50 | 33.0 | 31.7 | 31.5 | 34.6 | 34.0 | 31.6 | 27.9 | 30.6 |
| Qwen 2.5 - L100 50| 39.8 | 39.7 | 38.6 | 40.3 | 34.4 | 40.7 | 38.7 | 45.5 |
| Aya-Expanse - L100 50| 36.8 | 35.4 | 34.9 | 35.2 | 37.5 | 36.4 | 34.6 | 33.7 |
| `Centurio` Aya   | 37.6 | 37.2 | 36.2 | 38.9 | 38.8 | 39.7 | 34.2 | 35.4 |
| `Centurio` Qwen  | 46.4 | 43.0 | 39.6 | 45.0 | 41.6 | 44.1 | 43.5 | 44.1 |{{< /table-caption >}}
> 🔼 표 29는 논문의 실험 결과 중 하나로, 다국어를 지원하는 비전-언어 모델의 성능을 평가하는 xMMMU 데이터셋에 대한 결과를 보여줍니다.  표에는 다양한 모델과 학습 전략(예: 영어 데이터만 사용, 다국어 데이터 사용, 다국어 지시 튜닝 등)에 따른 xMMMU 데이터셋에 대한 정확도(Accuracy) 점수가 언어별로 제시되어 있습니다. 이를 통해 다국어 학습 전략이 모델의 성능에 미치는 영향을 분석하고, 특히 저자원 언어에 대한 성능 향상 효과를 비교 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 29: xMMMU
> </details>

{{< table-caption >}}
|                | en   | avg. | avg. Latin | avg. other | ar   | de   | hi   | id   | it   | ko   | ru   | th   | zh   | zu   |
|----------------|------|------|------------|------------|------|------|------|------|------|------|------|------|------|------|
| Phi 3.5 - English | 65.8 | 55.8 | 62.3        | 51.5        | 50.2 | 63.5 | 58.5 | 61.4 | 64.0 | 49.0 | 52.1 | 49.1 | 49.8 | 60.2 |
| Phi 3.5 - T5 50  | 75.2 | 60.2 | 70.9        | 53.1        | 50.2 | 70.8 | 65.4 | 71.8 | 71.6 | 49.8 | 54.1 | 51.0 | 48.0 | 69.4 |
| Phi 3.5 - T5-4 50 | 74.2 | 60.8 | 71.4        | 53.7        | 52.2 | 71.5 | 65.5 | 72.8 | 73.1 | 51.1 | 53.9 | 49.6 | 49.6 | 68.4 |
| Phi 3.5 - T5-3 50 | 70.4 | 58.7 | 67.7        | 52.8        | 51.6 | 66.9 | 61.0 | 69.6 | 67.2 | 50.0 | 53.6 | 48.9 | 51.4 | 67.0 |
| Phi 3.5 - T5-2 50 | 68.4 | 56.2 | 64.2        | 50.8        | 49.5 | 64.5 | 58.4 | 65.4 | 64.9 | 50.0 | 50.5 | 48.8 | 47.9 | 62.0 |
| Phi 3.5 - L100 50 | 69.6 | 58.0 | 67.2        | 51.9        | 49.9 | 68.0 | 62.4 | 69.0 | 67.9 | 48.6 | 52.5 | 49.6 | 48.4 | 64.1 |
| Llama 3 - English | 72.0 | 60.5 | 69.6        | 54.4        | 53.5 | 69.9 | 67.2 | 71.1 | 70.9 | 48.9 | 57.5 | 50.1 | 49.4 | 66.5 |
| Llama 3 - T5 50  | 73.4 | 62.2 | 72.5        | 55.4        | 54.5 | 72.2 | 67.1 | 74.4 | 71.5 | 50.5 | 56.6 | 51.6 | 51.9 | 72.0 |
| Llama 3 - L100 50 | 72.0 | 58.4 | 67.9        | 52.1        | 51.6 | 69.6 | 62.0 | 65.9 | 70.4 | 49.9 | 52.0 | 48.8 | 48.4 | 65.6 |
| Phi 3.5 - L100 1  | 58.4 | 52.6 | 55.7        | 50.5        | 50.2 | 55.2 | 53.5 | 57.5 | 56.4 | 49.6 | 50.9 | 48.2 | 50.5 | 53.5 |
| Phi 3.5 - L100 10 | 56.9 | 51.6 | 54.9        | 49.4        | 48.5 | 54.8 | 49.6 | 55.1 | 56.8 | 50.5 | 48.2 | 49.6 | 50.0 | 52.9 |
| Phi 3.5 - L100 24 | 60.4 | 54.0 | 58.8        | 50.8        | 51.8 | 58.9 | 54.5 | 58.1 | 60.0 | 50.0 | 51.1 | 48.4 | 49.2 | 58.0 |
| Phi 3.5 - L100 50 | 69.6 | 58.0 | 67.2        | 51.9        | 49.9 | 68.0 | 62.4 | 69.0 | 67.9 | 48.6 | 52.5 | 49.6 | 48.4 | 64.1 |
| Phi 3.5 - L100 75 | 74.5 | 61.2 | 71.6        | 54.2        | 53.2 | 71.2 | 63.8 | 74.0 | 70.5 | 50.5 | 54.2 | 51.9 | 51.8 | 70.6 |
| Phi 3.5 - L100 90 | 71.6 | 59.4 | 69.2        | 52.9        | 51.0 | 70.2 | 60.5 | 69.4 | 71.2 | 49.6 | 54.1 | 50.4 | 51.8 | 66.1 |
| Llama 3 - L100 10 | 65.9 | 56.6 | 62.6        | 52.6        | 51.5 | 62.1 | 59.5 | 62.6 | 65.8 | 50.8 | 54.5 | 50.4 | 48.8 | 59.9 |
| Llama 3 - L100 50 | 72.0 | 58.4 | 67.9        | 52.1        | 51.6 | 69.6 | 62.0 | 65.9 | 70.4 | 49.9 | 52.0 | 48.8 | 48.4 | 65.6 |
| Llama 3 - L100 90 | 73.1 | 59.4 | 68.4        | 53.3        | 51.0 | 67.4 | 65.8 | 71.0 | 69.0 | 50.6 | 52.6 | 49.9 | 50.1 | 66.2 |
| Phi 3.5 - L100 50 | 69.6 | 58.0 | 67.2        | 51.9        | 49.9 | 68.0 | 62.4 | 69.0 | 67.9 | 48.6 | 52.5 | 49.6 | 48.4 | 64.1 |
| Phi 3.5 - PT 100  | 79.5 | 63.3 | 74.8        | 55.6        | 52.8 | 75.8 | 68.5 | 76.2 | 76.5 | 50.8 | 59.6 | 50.9 | 51.0 | 70.8 |
| Phi 3.5 - PT 50   | 76.1 | 62.4 | 73.0        | 55.3        | 52.4 | 72.2 | 69.6 | 73.6 | 73.8 | 49.2 | 59.9 | 50.0 | 50.6 | 72.2 |
| Phi 3.5 - PT 1   | 78.1 | 64.5 | 74.5        | 57.7        | 57.0 | 74.0 | 72.8 | 76.8 | 75.0 | 52.8 | 62.2 | 51.4 | 50.2 | 72.4 |
| Llama 3 - L100 50 | 72.0 | 58.4 | 67.9        | 52.1        | 51.6 | 69.6 | 62.0 | 65.9 | 70.4 | 49.9 | 52.0 | 48.8 | 48.4 | 65.6 |
| Llama 3 - PT 1   | 76.9 | 65.1 | 74.4        | 58.9        | 55.0 | 74.8 | 73.0 | 75.5 | 74.4 | 53.4 | 65.9 | 52.5 | 53.8 | 72.9 |
| Llama 3 - PT 100  | 79.9 | 65.2 | 77.4        | 57.0        | 52.6 | 77.6 | 73.4 | 78.1 | 78.2 | 51.0 | 64.0 | 49.1 | 51.8 | 75.8 |
| Phi 3.5 - OCR English | 78.4 | 64.6 | 74.7        | 57.9        | 59.1 | 77.1 | 70.9 | 73.6 | 74.5 | 50.6 | 66.5 | 51.1 | 49.0 | 73.6 |
| Phi 3.5 - OCR 50  | 81.2 | 66.7 | 76.7        | 60.0        | 61.4 | 78.6 | 72.1 | 76.0 | 77.1 | 51.5 | 71.5 | 52.1 | 51.6 | 75.0 |
| Phi 3.5 - OCR 1   | 81.0 | 69.8 | 78.3        | 64.1        | 66.8 | 78.0 | 76.8 | 78.5 | 79.1 | 56.9 | 73.2 | 58.6 | 52.4 | 77.6 |
| Phi 3.5 - OCR Latin-down | 78.9 | 65.4 | 74.2        | 59.5        | 57.8 | 75.5 | 67.6 | 75.0 | 75.0 | 56.4 | 67.8 | 55.0 | 52.5 | 71.1 |
| Phi 3.5 - OCR 50 (frozen) | 76.1 | 62.1 | 70.8        | 56.3        | 59.2 | 73.2 | 63.2 | 66.2 | 76.1 | 50.0 | 68.0 | 47.8 | 49.8 | 67.8 |
| Gemma 2 - L100 50 | 59.9 | 53.5 | 57.1        | 51.1        | 49.6 | 59.1 | 56.5 | 56.8 | 58.9 | 49.9 | 51.0 | 50.6 | 49.2 | 53.6 |
| Llama 3 - L100 50 | 72.0 | 58.4 | 67.9        | 52.1        | 51.6 | 69.6 | 62.0 | 65.9 | 70.4 | 49.9 | 52.0 | 48.8 | 48.4 | 65.6 |
| Qwen 2.5 - L100 50 | 82.8 | 62.5 | 75.1        | 54.0        | 51.5 | 76.4 | 66.5 | 76.5 | 76.5 | 50.1 | 55.2 | 51.0 | 49.8 | 71.1 |
| Aya-Expanse - L100 50 | 79.1 | 63.5 | 75.2        | 55.7        | 53.9 | 77.2 | 71.4 | 75.6 | 75.0 | 50.6 | 56.0 | 51.1 | 51.0 | 73.1 |
| modelname Aya      | 83.1 | 74.2 | 80.9        | 69.7        | 75.9 | 82.1 | 80.1 | 81.4 | 80.6 | 68.8 | 73.5 | 66.5 | 53.4 | 79.5 |
| modelname Qwen     | 84.8 | 76.1 | 82.7        | 71.8        | 76.9 | 83.5 | 82.4 | 83.8 | 83.1 | 72.4 | 75.6 | 64.4 | 58.9 | 80.2 |{{< /table-caption >}}
> 🔼 표 30은 합성 다국어 플롯 질의응답(SMPQA) 데이터셋의 Grounding 작업에 대한 결과를 보여줍니다.  Grounding 작업은 이미지 내 텍스트를 이해하고 질문에 답하는 능력을 평가하는 것입니다. 이 표는 다양한 언어와 훈련 전략에 따른 모델 성능을 보여줍니다.  각 열은 특정 언어(예: 영어, 아랍어, 독일어 등)에 대한 정확도를 나타내고, 각 행은 특정 훈련 설정(예: 영어 전용 훈련, 다국어 훈련 등)을 나타냅니다. 이 표를 통해 다양한 언어 및 훈련 전략이 모델의 Grounding 성능에 미치는 영향을 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 30: SMPQA Ground
> </details>

{{< table-caption >}}
Model|en|avg.|avg. Latin|avg. other|ar|de|hi|id|it|ko|ru|th|zh|zu
---|---|---|---|---|---|---|---|---|---|---|---|---|---|---
Phi 3.5 - English|36.2|5.0|12.4|0.0|0.0|17.4|0.0|12.6|15.2|0.0|0.0|0.0|0.0|4.4
Phi 3.5 - T5 50|36.4|5.4|13.6|0.0|0.0|21.2|0.0|13.2|16.0|0.0|0.0|0.0|0.0|3.8
Phi 3.5 - T5-4 50|35.0|5.8|14.4|0.0|0.0|20.0|0.0|14.6|16.6|0.0|0.0|0.0|0.0|6.4
Phi 3.5 - T5-3 50|34.6|5.8|14.4|0.0|0.0|16.0|0.0|16.6|20.4|0.0|0.0|0.0|0.0|4.8
Phi 3.5 - T5-2 50|35.8|5.8|14.5|0.0|0.0|18.0|0.0|14.8|19.6|0.0|0.0|0.0|0.0|5.6
Phi 3.5 - L100 50|33.4|5.2|12.8|0.1|0.0|17.4|0.0|14.0|14.6|0.0|0.2|0.2|0.0|5.2
Llama 3 - English|41.0|8.5|21.1|0.0|0.0|24.4|0.0|21.6|23.8|0.0|0.0|0.2|0.0|14.8
Llama 3 - T5 50|41.4|8.2|20.4|0.0|0.0|25.2|0.0|21.8|23.4|0.0|0.0|0.2|0.0|11.2
Llama 3 - L100 50|39.2|7.3|18.2|0.0|0.0|21.6|0.0|18.8|21.6|0.0|0.0|0.2|0.0|10.8
Phi 3.5 - L100 1|22.0|4.0|10.1|0.0|0.0|12.0|0.0|9.0|14.0|0.0|0.0|0.0|0.0|5.2
Phi 3.5 - L100 10|24.6|4.1|10.3|0.0|0.0|11.6|0.0|10.0|14.2|0.0|0.0|0.0|0.0|5.4
Phi 3.5 - L100 24|26.0|3.8|9.5|0.1|0.0|12.2|0.0|8.4|12.6|0.0|0.0|0.4|0.0|4.8
Phi 3.5 - L100 50|33.4|5.2|12.8|0.1|0.0|17.4|0.0|14.0|14.6|0.0|0.2|0.2|0.0|5.2
Phi 3.5 - L100 75|38.4|6.0|15.1|0.0|0.0|21.0|0.0|14.8|18.6|0.0|0.2|0.0|0.0|5.8
Phi 3.5 - L100 90|39.8|6.5|16.1|0.0|0.0|21.0|0.0|17.0|21.8|0.0|0.0|0.0|0.0|4.8
Llama 3 - L100 10|32.0|6.3|15.6|0.1|0.0|17.8|0.0|15.8|19.2|0.0|0.0|0.4|0.0|9.6
Llama 3 - L100 50|39.2|7.3|18.2|0.0|0.0|21.6|0.0|18.8|21.6|0.0|0.0|0.2|0.0|10.8
Llama 3 - L100 90|40.0|7.5|18.8|0.0|0.0|21.2|0.0|21.0|20.4|0.0|0.0|0.2|0.0|12.6
Phi 3.5 - L100 50|33.4|5.2|12.8|0.1|0.0|17.4|0.0|14.0|14.6|0.0|0.2|0.2|0.0|5.2
Phi 3.5 - PT 100|44.0|9.9|24.5|0.2|0.0|31.4|0.0|25.6|26.8|0.0|1.2|0.2|0.0|14.0
Phi 3.5 - PT 50|41.8|9.4|23.1|0.2|0.0|27.8|0.0|24.4|25.0|0.0|1.2|0.2|0.0|15.0
Phi 3.5 - PT 1|42.2|9.5|23.7|0.1|0.0|27.2|0.0|24.4|29.0|0.0|0.4|0.0|0.0|14.0
Llama 3 - L100 50|39.2|7.3|18.2|0.0|0.0|21.6|0.0|18.8|21.6|0.0|0.0|0.2|0.0|10.8
Llama 3 - PT 1|48.4|11.4|27.9|0.4|0.0|29.6|0.2|30.6|30.6|0.0|1.6|0.4|0.0|20.6
Llama 3 - PT 100|48.8|10.5|25.0|0.8|0.0|28.8|2.6|26.2|28.4|0.2|1.8|0.4|0.0|16.6
Phi 3.5 - OCR English|55.8|18.3|39.9|3.9|5.2|38.6|2.4|43.2|41.6|0.0|15.2|0.4|0.0|36.4
Phi 3.5 - OCR 50|53.8|21.0|41.8|7.1|14.4|42.2|6.4|45.8|42.6|0.2|21.2|0.6|0.0|36.4
Phi 3.5 - OCR 1|54.8|22.2|43.5|8.0|17.2|43.8|6.2|46.4|42.8|1.2|21.4|1.8|0.0|40.8
Phi 3.5 - OCR Latin-down|54.6|22.4|41.0|9.9|20.2|41.6|7.0|42.6|43.0|2.8|25.6|3.4|0.6|36.8
Phi 3.5 - OCR 50 (frozen)|47.2|15.7|34.1|3.5|5.2|36.4|3.8|37.2|33.0|0.0|11.8|0.2|0.0|29.6
Gemma 2 - L100 50|28.6|3.8|9.4|0.1|0.0|13.8|0.0|10.4|8.4|0.0|0.0|0.4|0.0|5.0
Llama 3 - L100 50|39.2|7.3|18.2|0.0|0.0|21.6|0.0|18.8|21.6|0.0|0.0|0.2|0.0|10.8
Qwen 2.5 - L100 50|48.8|10.1|25.1|0.1|0.0|32.0|0.0|23.8|29.0|0.0|0.2|0.2|0.0|15.6
Aya-Expanse - L100 50|46.6|10.2|25.4|0.1|0.0|27.4|0.0|28.8|27.4|0.0|0.0|0.4|0.0|18.0
modelname Aya|60.0|30.1|49.8|17.0|29.2|50.2|17.6|52.6|51.2|11.2|38.2|4.8|0.8|45.2
modelname Qwen|65.2|31.7|54.3|16.6|21.4|53.2|21.4|55.4|56.6|16.2|34.8|5.2|0.6|52.2{{< /table-caption >}}
> 🔼 표 31은 합성 다국어 플롯 질의응답(SMPQA) 데이터셋의 이름 인식 작업에 대한 결과를 보여줍니다. 이 표는 다양한 언어와 스크립트에 대한 모델의 성능을 보여주는 정확도 점수를 포함합니다. 특히, 이 표는 영어를 포함한 여러 언어의 합성 OCR 데이터를 사용하여 사전 훈련 및 지시 튜닝된 모델의 성능을 비교 분석합니다. 이를 통해 다국어 이미지 내 텍스트 이해력 향상에 대한 통찰력을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 31: SMPQA Name
> </details>

{{< table-caption >}}
|       | en   | avg. | af   | am   | cs   | el   | es   | fa   | fi   | ha   | hr   | hu   | ja   | mi   | nl   | no   | pl   | ro   | ta   | te   | zu   |
| :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| Centurio Aya | 69.7 | 54.7 | 63.6 | 29.4 | 66.2 | 67.8 | 65.1 | 60.0 | 43.3 | 37.5 | 63.6 | 49.8 | 66.7 | 37.0 | 62.4 | 59.1 | 62.6 | 64.0 | 46.9 | 50.9 | 42.6 |
| Centurio Qwen | 72.7 | 56.2 | 65.3 | 47.4 | 62.2 | 56.7 | 67.0 | 53.6 | 48.8 | 36.7 | 65.4 | 54.1 | 67.6 | 39.1 | 63.7 | 63.6 | 60.4 | 58.5 | 45.2 | 63.4 | 49.5 |
| Parrot | 30.5 | 25.7 | 26.0 | 22.8 | 26.1 | 25.5 | 27.3 | 25.9 | 26.4 | 23.7 | 25.3 | 25.6 | 26.7 | 25.4 | 28.0 | 26.6 | 26.5 | 26.8 | 25.5 | 23.9 | 24.0 |
| PALO 13B | 61.4 | 41.1 | 48.4 | 25.9 | 47.9 | 35.8 | 53.2 | 37.5 | 42.7 | 26.1 | 52.3 | 47.9 | 49.1 | 31.0 | 48.9 | 51.2 | 46.1 | 46.5 | 28.9 | 32.2 | 28.3 |
| PALO 7B | 58.7 | 38.6 | 44.2 | 28.4 | 43.6 | 33.5 | 49.9 | 36.9 | 39.1 | 24.5 | 49.6 | 45.4 | 48.8 | 27.8 | 45.1 | 45.8 | 42.0 | 44.0 | 26.7 | 30.1 | 28.3 |
| InternVL 2.5 4B | 68.4 | 45.4 | 53.2 | 31.3 | 53.2 | 42.3 | 60.8 | 45.4 | 38.3 | 26.3 | 55.2 | 42.1 | 60.5 | 29.5 | 56.6 | 53.7 | 53.1 | 49.7 | 35.3 | 50.1 | 26.5 |
| InternVL 2.5 8B | 70.3 | 44.2 | 54.4 | 29.1 | 52.8 | 43.3 | 57.8 | 40.5 | 41.3 | 25.8 | 55.6 | 44.9 | 57.3 | 30.0 | 51.8 | 54.8 | 50.3 | 48.9 | 33.2 | 41.2 | 27.3 |
| Qwen2-VL 2B | 78.2 | 47.2 | 56.6 | 30.3 | 56.7 | 47.2 | 64.0 | 48.7 | 41.7 | 26.1 | 57.1 | 48.0 | 62.2 | 30.0 | 59.2 | 57.8 | 54.6 | 54.5 | 31.9 | 43.4 | 27.6 |
| Qwen2-VL 7B | 80.7 | 57.5 | 68.9 | 37.2 | 68.5 | 62.2 | 72.6 | 59.8 | 55.1 | 27.1 | 72.2 | 61.8 | 71.8 | 29.5 | 69.5 | 69.6 | 67.5 | 65.6 | 42.7 | 62.3 | 29.3 |
| Maya | 54.0 | 43.2 | 50.6 | 27.1 | 53.3 | 53.6 | 52.7 | 48.7 | 35.3 | 23.7 | 50.5 | 39.3 | 55.2 | 28.6 | 51.4 | 46.4 | 50.0 | 51.3 | 31.9 | 36.9 | 33.4 |
| Llama-Vision | 75.6 | 50.8 | 65.1 | 30.6 | 61.3 | 42.9 | 65.1 | 49.9 | 51.5 | 31.1 | 60.9 | 65.0 | 46.3 | 32.8 | 61.5 | 61.8 | 55.7 | 57.3 | 42.0 | 51.6 | 31.9 |
| Phi 3.5 Vision | 63.1 | 36.8 | 40.9 | 28.7 | 41.0 | 34.7 | 52.7 | 33.5 | 34.9 | 27.1 | 40.5 | 36.8 | 45.9 | 28.2 | 43.6 | 44.4 | 38.5 | 39.8 | 30.9 | 28.1 | 28.1 |
| Pixtral 12B | 71.0 | 54.2 | 62.3 | 34.3 | 61.6 | 58.3 | 66.1 | 57.3 | 52.0 | 27.7 | 67.1 | 60.4 | 64.8 | 31.9 | 58.6 | 62.1 | 59.8 | 59.0 | 56.7 | 64.5 | 25.0 |
| Pangea | 70.3 | 52.1 | 61.4 | 34.3 | 59.6 | 54.2 | 64.4 | 54.9 | 45.4 | 27.9 | 63.0 | 49.8 | 65.5 | 29.6 | 61.0 | 64.1 | 59.5 | 60.6 | 42.4 | 62.7 | 29.3 |
| MiniCPM 2.6 | 72.6 | 47.4 | 56.0 | 29.9 | 55.1 | 46.6 | 62.1 | 48.5 | 41.8 | 22.9 | 59.5 | 44.9 | 62.9 | 29.0 | 57.8 | 55.2 | 54.7 | 52.7 | 34.5 | 53.9 | 33.4 |{{< /table-caption >}}
> 🔼 표 32는 Babel ImageNet-MC 데이터셋에 대한 결과를 보여줍니다. Babel ImageNet-MC 데이터셋은 ImageNet의 레이블을 여러 언어로 번역한 데이터셋으로, 모델이 다양한 언어로 된 레이블을 이미지의 개체와 정확하게 연결할 수 있는지 평가하는 데 사용됩니다. 이 표는 다양한 언어 모델의 성능을 다양한 언어별로 비교 분석한 결과를 나타냅니다.  각 행은 특정 언어 모델과 학습 전략(예: 영어만 사용, 다국어 사용, 다국어 OCR 데이터 포함 등)을 나타내고, 열은 여러 언어(af, am, cs, el, es 등)에 대한 정확도를 보여줍니다. 이 표를 통해 다양한 언어 모델의 다국어 이해 능력과 다양한 학습 전략의 효과를 비교 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 32: BIN-MC
> </details>

{{< table-caption >}}
|                | en  | avg. | af   | zh  | it  | pt  | th  | vi  |
|----------------|-----|------|------|-----|-----|-----|-----|-----|
|Centurio Aya    | 53.0 | 41.2 | 52.8 | 51.4 | 47.7 | 27.4 | 27.8 | 40.3 |
|Centurio Qwen   | 61.2 | 46.9 | 50.9 | 55.6 | 49.0 | 31.9 | 29.6 | 64.1 |
|Parrot          | 46.6 | 36.2 | 38.0 | 37.8 | 36.8 | 25.9 | 23.5 | 55.1 |
|PALO 13B        | 45.2 | 28.3 | 33.1 | 31.3 | 36.5 | 19.3 | 20.2 | 29.2 |
|PALO 7B         | 41.0 | 29.1 | 34.4 | 31.5 | 32.7 | 21.8 | 21.1 | 33.4 |
|InternVL 2.5 4B | 63.2 | 50.3 | 46.0 | 60.9 | 50.3 | 34.9 | 39.1 | 70.4 |
|InternVL 2.5 8B | 67.0 | 53.3 | 57.7 | 61.7 | 53.2 | 33.0 | 39.1 | 75.2 |
|Qwen2-VL 2B     | 47.9 | 40.5 | 38.0 | 51.6 | 36.4 | 36.2 | 26.1 | 54.9 |
|Qwen2-VL 7B     | 56.1 | 49.7 | 50.9 | 58.6 | 46.8 | 34.7 | 38.3 | 69.0 |
|Maya            | 49.2 | 36.3 | 48.5 | 46.4 | 36.6 | 25.9 | 20.0 | 40.3 |
|Phi 3.5 Vision  | 56.3 | 40.7 | 51.5 | 54.4 | 44.1 | 25.2 | 24.3 | 44.4 |
|Pixtral 12B     | 49.4 | 33.7 | 39.9 | 53.6 | 34.4 | 19.5 | 7.0  | 47.7 |
|Pangea          | 58.0 | 45.5 | 50.3 | 58.6 | 49.0 | 32.2 | 27.8 | 55.3 |
|MiniCPM 2.6     | 55.0 | 48.2 | 44.2 | 54.6 | 44.3 | 36.9 | 38.3 | 70.8 |{{< /table-caption >}}
> 🔼 표 33은 논문의 실험 결과를 보여주는 표이며, 다양한 언어 모델의 M3Exam 데이터셋에 대한 성능을 비교 분석한 내용을 담고 있습니다.  M3Exam은 다양한 언어와 이미지를 포함하는 객관식 시각적 질문 답변 데이터셋으로, 각 모델의 다국어 이해 및 이미지 해석 능력을 평가하기 위한 벤치마크로 사용되었습니다.  표에는 다양한 언어 모델과 훈련 방식에 따른 정확도(accuracy) 점수가 언어별 및 과업별로 제시되어 있습니다.  각 모델의 성능을 비교하여 최적의 다국어 언어 모델 훈련 전략을 제시하는 데 사용되었습니다.
> <details>
> <summary>read the caption</summary>
> Table 33: M3Exam
> </details>

{{< table-caption >}}
| Model | en | avg. | am | ber | bn | de | fil | ha | hi | ru | sw | th | zu |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Centurio Aya | 82.5 | 66.8 | 71.7 | 54.2 | 59.3 | 73.3 | 59.2 | 65.0 | 71.2 | 75.8 | 67.5 | 72.5 | 65.5 |
| Centurio Qwen | 87.5 | 73.1 | 77.5 | 49.2 | 62.7 | 80.8 | 78.3 | 76.7 | 72.9 | 85.0 | 70.0 | 81.7 | 69.0 |
| Parrot | 59.2 | 52.9 | 45.0 | 64.2 | 53.4 | 63.3 | 49.2 | 41.7 | 62.7 | 62.5 | 35.8 | 67.5 | 36.2 |
| PALO 13B | 63.3 | 26.2 | 25.0 | 55.0 | 0.8 | 44.2 | 47.5 | 40.0 | 0.0 | 5.8 | 32.5 | 0.0 | 37.1 |
| PALO 7B | 48.3 | 25.6 | 40.8 | 75.0 | 0.0 | 0.0 | 49.2 | 40.0 | 0.0 | 0.0 | 39.2 | 0.0 | 37.9 |
| InternVL 2.5 4B | 72.5 | 49.7 | 43.3 | 50.0 | 40.7 | 62.5 | 56.7 | 41.7 | 42.4 | 63.3 | 35.8 | 74.2 | 36.2 |
| InternVL 2.5 8B | 87.5 | 51.6 | 43.3 | 50.0 | 41.5 | 64.2 | 49.2 | 41.7 | 59.3 | 75.8 | 36.7 | 68.3 | 37.1 |
| Qwen2-VL 2B | 61.7 | 50.5 | 44.2 | 50.0 | 43.2 | 65.0 | 53.3 | 41.7 | 61.0 | 52.5 | 38.3 | 67.5 | 38.8 |
| Qwen2-VL 7B | 60.0 | 52.9 | 48.3 | 50.0 | 46.6 | 60.0 | 50.0 | 46.7 | 48.3 | 63.3 | 58.3 | 60.8 | 49.1 |
| Maya | 46.7 | 42.3 | 43.3 | 48.3 | 33.9 | 50.8 | 51.7 | 40.8 | 42.4 | 45.8 | 34.2 | 38.3 | 35.3 |
| Phi 3.5 Vision | 81.7 | 50.3 | 45.8 | 49.2 | 56.8 | 73.3 | 54.2 | 41.7 | 56.8 | 85.8 | 38.3 | 15.0 | 36.2 |
| Pixtral 12B | 55.8 | 47.7 | 51.7 | 32.5 | 47.5 | 63.3 | 51.7 | 44.2 | 16.1 | 54.2 | 65.8 | 53.3 | 44.0 |
| Pangea | 69.2 | 58.9 | 45.8 | 90.0 | 53.4 | 61.7 | 55.0 | 41.7 | 60.2 | 74.2 | 54.2 | 75.8 | 36.2 |
| MiniCPM 2.6 | 52.5 | 49.1 | 45.0 | 55.8 | 49.2 | 45.8 | 48.3 | 40.8 | 44.1 | 59.2 | 48.3 | 65.8 | 37.9 |{{< /table-caption >}}
> 🔼 표 34는 VGR(Visually Grounded Reasoning) 작업에 대한 다양한 대규모 비전-언어 모델(LLM)의 성능을 보여줍니다.  각 모델의 영어 및 다국어 성능을 평균 점수로 비교하며, 다양한 언어(예: 영어, 스페인어, 프랑스어, 독일어, 러시아어 등)에 대한 성능을 보여줍니다.  표는  모델의 다국어 능력을 평가하기 위해 사용된 다양한 지표(정확도, CIDEr 등)를 포함합니다. 이를 통해 다국어 LLM의 다국어 이해 능력과 다양한 언어에 대한 일반화 능력을 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 34: VGR
> </details>

{{< table-caption >}}
|               | en   | avg. | am   | ber  | bn   | de   | fil  | ha   | hi   | ru   | sw   | th   | zu   |
| :------------- | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| Centurio Aya  | 12.5 | 20.7 | 18.3 | 21.7 | 20.0 | 11.7 | 24.2 | 29.2 | 15.2 | 10.8 | 28.6 | 29.2 | 19.5 |
| Centurio Qwen | 28.3 | 27.0 | 18.3 | 20.0 | 33.3 | 32.5 | 29.2 | 22.5 | 25.0 | 22.5 | 30.4 | 30.0 | 33.1 |
| Parrot        | 0.0  | 0.0  | 0.0  | 0.0  | 0.0  | 0.0  | 0.0  | 0.0  | 0.0  | 0.0  | 0.0  | 0.0  | 0.0  |
| PALO 13B      | 2.5  | 4.9  | 6.7  | 5.0  | 6.7  | 5.0  | 5.8  | 2.5  | 3.6  | 4.2  | 5.4  | 5.0  | 4.2  |
| PALO 7B       | 5.8  | 6.8  | 8.3  | 9.2  | 10.0 | 5.8  | 6.7  | 4.2  | 9.8  | 5.0  | 4.5  | 5.8  | 5.1  |
| InternVL 2.5 4B | 24.2 | 21.0 | 18.3 | 26.7 | 17.5 | 20.8 | 20.0 | 23.3 | 22.3 | 20.0 | 23.2 | 20.0 | 18.6 |
| InternVL 2.5 8B | 57.5 | 29.0 | 25.0 | 22.5 | 25.8 | 38.3 | 36.7 | 25.8 | 41.1 | 35.8 | 15.2 | 30.0 | 22.9 |
| Qwen2-VL 2B   | 22.5 | 20.4 | 17.5 | 20.0 | 13.3 | 26.7 | 25.0 | 24.2 | 20.5 | 16.7 | 21.4 | 15.8 | 23.7 |
| Qwen2-VL 7B   | 5.8  | 13.2 | 14.2 | 15.8 | 13.3 | 11.7 | 10.0 | 15.0 | 12.5 | 12.5 | 13.4 | 13.3 | 13.6 |
| Maya          | 20.0 | 20.1 | 20.0 | 25.8 | 19.2 | 20.8 | 15.0 | 25.8 | 17.9 | 23.3 | 21.4 | 15.8 | 16.1 |
| Phi 3.5 Vision | 45.8 | 31.5 | 27.5 | 29.2 | 23.3 | 36.7 | 30.0 | 31.7 | 33.9 | 29.2 | 37.5 | 35.8 | 31.4 |
| Pixtral 12B   | 9.2  | 12.4 | 17.5 | 13.3 | 10.0 | 16.7 | 10.0 | 16.7 | 3.6  | 14.2 | 8.9  | 12.5 | 13.6 |
| Pangea        | 0.0  | 6.7  | 0.0  | 0.8  | 0.0  | 20.8 | 24.2 | 15.8 | 6.2  | 0.8  | 3.6  | 0.8  | 0.8  |
| MiniCPM 2.6   | 9.2  | 14.6 | 11.7 | 19.2 | 12.5 | 10.8 | 10.0 | 22.5 | 10.7 | 12.5 | 19.6 | 11.7 | 19.5 |{{< /table-caption >}}
> 🔼 표 35는 Visio-Linguistic Outlier Detection (VLOD) 데이터셋에 대한 결과를 보여줍니다.  VLOD 데이터셋은 여러 언어로 된 텍스트 설명과 다수의 이미지를 포함합니다. 각 이미지는 해당 설명에 맞는지 또는 벗어나는지를 판단하는 작업입니다.  표는 다양한 언어와 모델 구성에 따른 정확도를 보여주며, Centurio 모델의 성능을 비교 모델과 비교합니다.  다양한 언어 모델과 학습 전략에 따른 VLOD 작업의 성능을 보여주는 종합적인 비교 분석입니다.
> <details>
> <summary>read the caption</summary>
> Table 35: VLOD
> </details>

{{< table-caption >}}
|           | en   | avg. | id   | sw   | ta   | tr   | zh   |
|------------|------|------|------|------|------|------|------|
|Centurio Aya| 85.0 | 77.9 | 79.5 | 70.9 | 73.4 | 83.4 | 82.4 |
|Centurio Qwen| 89.6 | 81.7 | 85.0 | 76.8 | 76.0 | 84.2 | 86.7 |
|Parrot      | 63.5 | 55.1 | 56.6 | 51.2 | 50.7 | 58.6 | 58.2 |
|PALO 13B    | 63.8 | 33.1 | 58.7 | 50.9 | 2.6  | 53.1 | 0.2  |
|PALO 7B     | 62.7 | 24.1 | 33.6 | 47.8 | 0.4  | 38.5 | 0.0  |
|InternVL 2.5 4B| 74.9 | 59.0 | 65.7 | 50.7 | 50.9 | 64.2 | 63.5 |
|InternVL 2.5 8B| 83.0 | 63.3 | 63.2 | 51.4 | 54.6 | 67.2 | 79.9 |
|Qwen2-VL 2B | 67.9 | 55.9 | 60.9 | 51.8 | 52.2 | 59.0 | 55.8 |
|Qwen2-VL 7B | 69.8 | 60.2 | 61.1 | 53.1 | 60.9 | 65.3 | 60.7 |
|Maya        | 60.3 | 56.3 | 60.3 | 50.7 | 50.6 | 58.9 | 61.2 |
|Phi 3.5 Vision| 73.4 | 46.4 | 56.4 | 51.3 | 50.8 | 58.0 | 15.7 |
|Pixtral 12B | 67.7 | 60.7 | 62.5 | 54.4 | 61.8 | 65.5 | 59.1 |
|Pangea      | 75.8 | 70.5 | 74.3 | 70.9 | 66.6 | 71.1 | 69.6 |
|MiniCPM 2.6  | 70.2 | 57.9 | 57.8 | 54.2 | 57.2 | 63.3 | 57.2 |{{< /table-caption >}}
> 🔼 표 36은 MaRVL(Multilingual Reasoning over Vision and Language) 데이터셋에 대한 다양한 언어 모델의 성능을 비교한 표입니다.  각 모델은 영어(en)와 다양한 언어(avg.)에 대한 정확도 점수를 보여줍니다.  또한, 각 언어별 정확도 점수(id, sw, ta, tr, zh)가 포함되어 있어, 특정 언어에 대한 모델의 성능을 자세히 분석하는데 도움이 됩니다. 이 표는 본 논문의 실험 결과를 요약하여,  Centurio 모델을 포함한 다양한 대규모 언어 모델들의 다국어 이미지 이해 능력을 비교 평가하는 데 사용되었습니다.
> <details>
> <summary>read the caption</summary>
> Table 36: MaRVL
> </details>

{{< table-caption >}}
|           | en   | avg. | fr   | hi   | he   | ro   | th   | zh   |
| :--------- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| Centurio Aya | 55.7 | 49.3 | 45.1 | 58.7 | 62.9 | 51.1 | 46.7 | 31.6 |
| Centurio Qwen | 60.1 | 47.7 | 47.1 | 45.1 | 56.8 | 47.7 | 57.0 | 32.2 |
| Parrot       | 28.2 | 3.6  | 2.7  | 2.9  | 1.4  | 1.2  | 3.0  | 10.7 |
| PALO 13B     | 51.7 | 33.1 | 42.0 | 17.5 | 53.4 | 34.2 | 20.9 | 30.6 |
| PALO 7B      | 54.0 | 22.5 | 39.9 | 9.2  | 30.6 | 16.8 | 12.3 | 26.4 |
| InternVL 2.5 4B | 46.0 | 42.5 | 45.7 | 37.1 | 38.8 | 31.5 | 51.0 | 50.8 |
| InternVL 2.5 8B | 45.6 | 38.2 | 51.2 | 27.9 | 24.5 | 35.7 | 36.4 | 53.4 |
| Qwen2-VL 2B  | 53.7 | 26.5 | 40.3 | 10.8 | 9.5  | 15.6 | 38.1 | 44.6 |
| Qwen2-VL 7B  | 54.7 | 31.2 | 38.6 | 18.7 | 13.9 | 37.2 | 42.1 | 36.8 |
| Maya         | 55.4 | 17.3 | 19.1 | 13.0 | 21.1 | 18.0 | 11.6 | 20.8 |
| Llama-Vision | 0.0  | 4.7  | 0.0  | 0.6  | 2.4  | 0.3  | 24.8 | 0.0  |
| Phi 3.5 Vision | 43.6 | 17.9 | 23.5 | 12.1 | 16.3 | 7.8  | 20.9 | 27.0 |
| Pixtral 12B  | 59.4 | 43.4 | 46.8 | 31.7 | 54.4 | 44.1 | 44.4 | 39.1 |
| Pangea       | 61.4 | 55.0 | 47.4 | 61.0 | 53.7 | 52.9 | 67.2 | 47.9 |
| MiniCPM 2.6  | 53.4 | 22.3 | 14.3 | 12.1 | 5.1  | 19.5 | 53.6 | 29.3 |{{< /table-caption >}}
> 🔼 표 37은 MaXM 데이터셋에 대한 다양한 언어 모델의 성능을 보여줍니다. MaXM은 다국어 시각적 질의응답 데이터셋으로, 이미지와 질문, 그리고 해당 이미지에 대한 답변으로 구성됩니다. 이 표는 영어를 포함한 여러 언어에 대한 모델의 정확도를 보여주며, 다양한 모델의 성능을 비교 분석하는 데 유용합니다. 특히 다양한 언어 모델의 다국어 이해 능력을 평가하고 비교하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 37: MaXM
> </details>

{{< table-caption >}}
|           | avg. | ar  | de  | fr  | it  | ja  | ko  | ru  | th  | vi  |
| :--------- | :----: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| Centurio Aya |  11.1  | 6.7 | 19.9 | 22.5 | 16.7 | 5.0 | 9.0 | 5.2 | 5.2 | 9.7 |
| Centurio Qwen |  11.9  | 4.6 | 22.7 | 26.5 | 18.6 | 5.9 | 9.9 | 5.0 | 5.2 | 8.9 |
| Parrot      |  2.0   | 1.4 | 1.9 | 0.9 | 1.6 | 1.6 | 2.7 | 2.0 | 5.2 | 0.9 |
| PALO 13B    |  6.3   | 2.6 | 15.6 | 12.1 | 10.4 | 4.0 | 4.3 | 4.0 | 0.0 | 4.2 |
| PALO 7B     |  5.8   | 1.8 | 14.3 | 13.3 | 8.3  | 3.4 | 3.2 | 3.6 | 0.4 | 4.1 |
| InternVL 2.5 4B | 25.1  | 11.2 | 34.4 | 38.4 | 33.5 | 18.4 | 29.0 | 9.8 | 16.5 | 34.6 |
| InternVL 2.5 8B | 25.0  | 11.5 | 33.8 | 37.4 | 35.3 | 19.7 | 30.3 | 10.4 | 16.5 | 30.4 |
| Qwen2-VL 2B  |  19.0  | 6.1 | 26.8 | 30.9 | 30.7 | 13.5 | 21.1 | 9.3 | 10.0 | 22.4 |
| Qwen2-VL 7B  |  23.2  | 16.9 | 27.3 | 31.7 | 35.2 | 16.1 | 24.6 | 10.8 | 15.6 | 30.7 |
| Maya        |  5.3   | 2.8 | 13.1 | 12.2 | 6.6  | 2.8 | 4.8 | 2.9 | 0.4 | 2.3 |
| Llama-Vision |  15.2  | 7.4 | 24.0 | 18.7 | 25.3 | 9.4 | 14.5 | 6.1 | 15.2 | 15.8 |
| Phi 3.5 Vision | 11.1  | 3.3 | 18.2 | 20.2 | 25.2 | 5.6 | 8.8 | 5.4 | 3.0 | 10.5 |
| Pixtral 12B  |  14.1  | 4.3 | 25.7 | 27.3 | 25.2 | 5.9 | 9.1 | 7.5 | 5.2 | 16.6 |
| Pangea      |  19.3  | 8.3 | 29.5 | 35.2 | 29.2 | 9.3 | 14.5 | 7.4 | 10.8 | 29.2 |
| MiniCPM 2.6  |  16.1  | 2.3 | 23.9 | 27.5 | 32.7 | 11.7 | 12.7 | 7.3 | 10.0 | 16.5 |{{< /table-caption >}}
> 🔼 표 38은 다국어 시각적 질문 응답(MTVQA) 데이터셋에 대한 결과를 보여줍니다. 이 표는 다양한 언어와 다양한 학습 전략을 사용한 다양한 모델의 성능을 비교 분석합니다.  각 모델의 정확도는 다양한 언어 하위 집합에서 평가됩니다.  이 표를 통해 다국어 LLM의 성능에 영향을 미치는 요소를 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 38: MTVQA
> </details>

{{< table-caption >}}
|           | en   | avg. | bn   | de   | id   | ko   | pt   | ru   | zh   |
| :-------- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| Parrot    | 37.7  | 21.2  | 20.2  | 23.2  | 19.8  | 22.8  | 21.7  | 19.7  | 21.2  |
| PALO 13B  | 58.0  | 27.8  | 26.3  | 14.7  | 29.6  | 30.9  | 17.8  | 30.9  | 44.1  |
| PALO 7B   | 59.1  | 36.6  | 42.8  | 34.5  | 30.0  | 40.8  | 27.7  | 32.2  | 47.9  |
| InternVL 2.5 4B | 63.6  | 28.0  | 28.1  | 29.2  | 15.4  | 38.3  | 27.2  | 31.5  | 25.9  |
| InternVL 2.5 8B | 63.4  | 32.0  | 17.4  | 23.8  | 25.0  | 38.2  | 27.6  | 36.4  | 55.2  |
| Qwen2-VL 2B  | 60.5  | 38.2  | 18.6  | 43.2  | 32.6  | 39.0  | 39.9  | 44.1  | 50.3  |
| Qwen2-VL 7B  | 62.5  | 49.3  | 37.4  | 51.1  | 48.4  | 50.3  | 51.8  | 52.1  | 54.1  |
| Maya       | 58.2  | 49.1  | 40.1  | 53.2  | 49.7  | 47.2  | 52.5  | 50.6  | 50.1  |
| Llama-Vision | 39.3  | 27.6  | 26.0  | 29.2  | 26.8  | 24.9  | 27.9  | 30.7  | 27.9  |
| Phi 3.5 Vision | 65.2  | 38.0  | 5.0   | 51.9  | 37.3  | 35.6  | 50.6  | 45.9  | 39.5  |
| Pixtral 12B  | 59.9  | 3.8   | 0.7   | 5.4   | 14.0  | 0.3   | 3.6   | 0.4   | 1.9   |
| Pangea     | 64.6  | 60.4  | 59.1  | 61.6  | 60.7  | 58.8  | 62.1  | 60.7  | 59.6  |
| MiniCPM 2.6 | 57.9  | 45.7  | 33.9  | 49.0  | 46.3  | 42.1  | 51.0  | 48.7  | 48.6  |{{< /table-caption >}}
> 🔼 표 39는 다국어 비전-언어 모델의 성능을 평가하는 데 사용된 벤치마크 데이터셋 중 하나인 xGQA에 대한 결과를 보여줍니다. xGQA는 다양한 언어로 된 질문과 답변 쌍을 포함하고 있으며, 모델이 이미지 내의 시각적 정보와 텍스트 정보를 함께 이해할 수 있는 능력을 평가합니다. 표에는 다양한 모델들의 xGQA 성능이 언어별로 제시되어 있습니다. 각 모델의 정확도는 언어별로 나뉘어져 있으며, 다양한 학습 전략(예: 단일 언어, 다국어, 지시어 튜닝)에 따른 성능 차이를 비교 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 39: xGQA
> </details>

{{< table-caption >}}
Model Name|en|avg.|ar|bn|cs|da|de|el|es|fa|fi|fil|fr|he|hi|hr|hu|id|it|ja|ko|mi|nl|no|pl|pt|quz|ro|ru|sv|sw|te|th|tr|uk|vi|zh
---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---
Centurio Aya|78.4|**39.2**|**40.4**|18.5|**33.9**|**40.0**|**38.6**|**35.3**|**69.7**|**55.8**|**11.0**|**34.0**|**71.3**|**47.1**|**26.3**|**24.9**|**19.6**|**58.3**|**60.4**|**49.1**|**21.3**|**33.7**|**61.7**|**42.5**|**37.9**|59.3|**1.7**|**34.6**|38.0|**45.9**|29.9|**15.1**|26.0|**30.6**|**30.6**|**72.7**|**56.9**
Centurio Qwen|**79.1**|34.4|**36.6**|17.1|**29.7**|**43.1**|32.0|**19.2**|**69.2**|**31.2**|**12.0**|**33.6**|67.6|27.6|20.3|**22.0**|**18.7**|50.4|**53.7**|43.5|13.4|**34.9**|**56.2**|41.4|30.0|**59.9**|**2.1**|23.4|**39.2**|42.7|**30.2**|13.5|**42.3**|23.3|20.3|69.4|33.8
Parrot|5.6|0.4|0.6|0.0|0.2|0.0|0.0|0.0|3.3|2.3|0.0|0.0|0.3|0.0|0.0|0.0|0.0|0.0|0.2|0.0|0.0|0.0|1.6|0.0|0.0|4.0|0.2|0.4|0.4|0.0|0.0|0.8|0.0|1.0|0.0|0.0|0.0
PALO 13B|67.3|17.0|23.5|**22.9**|7.9|30.3|32.4|0.2|57.0|1.5|6.6|8.4|66.2|0.6|**25.0**|9.9|2.7|22.7|40.4|19.7|0.2|0.3|36.5|31.0|9.1|13.8|0.8|14.5|21.3|33.9|0.8|0.0|0.5|0.6|2.6|15.6|37.0
PALO 7B|65.9|13.5|17.3|18.8|5.8|18.5|23.3|0.1|48.3|1.5|4.0|2.7|59.1|0.2|21.2|2.8|6.3|20.2|31.0|29.8|2.4|0.3|29.8|16.5|8.4|8.9|0.5|2.6|19.7|23.3|0.0|0.0|0.0|0.5|0.1|17.4|29.7
InternVL 2.5 4B|38.9|17.5|12.1|3.7|9.4|13.6|28.0|2.0|39.7|10.1|2.6|6.2|49.2|8.5|5.4|5.6|3.8|39.9|33.1|33.1|8.9|0.8|29.3|14.2|12.9|39.0|0.2|9.9|23.4|17.1|0.6|1.1|27.9|7.8|7.1|61.3|44.1
InternVL 2.5 8B|38.3|15.7|7.9|4.0|10.7|19.2|27.8|2.9|35.0|8.7|5.0|10.9|47.0|8.2|8.3|7.9|5.3|24.7|27.5|22.0|6.7|0.9|26.8|16.6|12.0|35.0|0.8|12.0|22.6|20.5|1.0|2.6|7.2|9.3|4.7|46.2|40.1
Qwen2-VL 2B|68.8|5.2|0.8|0.0|1.7|7.2|7.0|0.2|5.1|9.0|1.2|2.9|9.4|0.4|0.0|1.4|2.1|8.9|5.9|8.4|1.0|0.3|2.9|5.2|1.5|21.0|1.0|3.7|1.1|13.0|1.1|0.0|1.3|0.9|0.6|7.9|49.5
Qwen2-VL 7B|50.3|24.6|17.9|11.5|23.8|32.3|36.1|13.5|38.9|23.6|8.0|8.3|50.6|13.7|6.7|11.6|15.5|45.4|38.7|32.0|9.1|0.9|39.1|35.7|**30.1**|48.8|0.9|19.0|37.9|**43.1**|2.4|3.9|31.2|15.8|16.6|55.6|41.8
Maya|55.9|14.6|20.6|18.4|11.4|10.6|23.6|10.7|38.2|1.5|0.5|2.1|47.3|18.9|15.0|2.0|0.9|19.4|34.4|26.3|8.9|0.3|28.8|9.4|15.8|16.4|0.6|22.0|19.9|11.4|0.5|0.0|0.2|13.5|1.5|31.8|26.9
Llama-Vision|35.9|7.2|0.0|0.0|0.9|15.5|22.4|0.5|14.7|0.0|4.0|13.1|32.1|0.0|0.0|2.9|13.2|2.2|33.5|0.2|0.1|0.8|30.1|2.8|2.4|15.7|0.2|23.4|0.3|11.2|6.8|0.0|1.2|0.6|0.1|0.8|0.0
Phi 3.5 Vision|32.3|6.3|2.8|0.0|0.6|10.5|21.3|0.1|21.9|0.1|0.9|2.5|32.5|1.0|0.1|1.5|2.6|4.2|23.6|8.0|0.3|0.2|19.8|10.7|1.7|25.8|0.4|3.0|0.5|10.2|0.5|0.0|1.0|1.7|0.1|2.6|8.1
Pixtral 12B|26.5|22.1|18.6|9.6|16.8|24.4|33.2|8.9|36.5|20.5|10.4|15.3|47.8|18.0|6.3|18.7|15.6|44.6|32.8|21.8|12.0|5.9|29.7|26.0|19.6|42.4|1.0|20.2|33.8|30.0|10.4|6.2|23.8|14.9|18.4|51.7|28.1
Pangea|70.1|**34.6**|33.3|**30.8**|19.4|25.2|**39.4**|13.0|61.4|25.4|4.2|6.7|**69.7**|**42.7**|21.5|9.5|3.6|**70.9**|53.5|**63.3**|**20.3**|0.3|44.9|**48.5**|24.1|**64.6**|1.7|**38.7**|**47.3**|20.1|**40.7**|**21.8**|**61.4**|**30.2**|**20.7**|**81.3**|**50.7**
MiniCPM 2.6|**87.5**|14.2|6.7|3.3|8.5|8.7|27.5|1.7|44.0|5.8|3.2|5.0|52.1|1.5|3.0|6.1|5.8|24.6|24.6|18.6|4.4|2.2|27.8|12.0|12.0|36.0|0.2|10.0|20.0|17.0|1.5|0.5|20.9|8.0|7.5|25.8|39.4{{< /table-caption >}}
> 🔼 표 40는 다양한 언어 모델의 XM3600 데이터셋에 대한 성능을 보여줍니다. XM3600 데이터셋은 36개 언어의 이미지 캡션 데이터로 구성되어 있습니다. 표는 다양한 모델의 정확도를 36개 언어 각각에 대해 보여주고, 각 언어별 성능을 평균 성능과 비교하여 보여줍니다.  여러가지 모델의 성능을 비교하여 Centurio 모델의 강점과 약점을 보여줍니다. 특히, 다양한 언어에 대한 모델의 일반화 능력과 각 언어의 데이터 양에 따른 성능 변화를 분석하는 데 유용합니다.
> <details>
> <summary>read the caption</summary>
> Table 40: XM3600
> </details>

{{< table-caption >}}
Model Name|en|avg.|ar|bn|cs|da|de|el|es|fa|fi|fil|fr|he|hi|hr|hu|id|it|ja|ko|mi|nl|no|pl|pt|quz|ro|ru|sv|sw|te|th|tr|uk|vi|zh|
---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---
Centurio Aya|100.0|95.7|93.6|100.0|97.7|96.7|100.0|100.0|99.8|100.0|99.8|100.0|100.0|99.8|99.6|84.6|99.8|99.2|99.6|98.8|100.0|98.8|100.0|97.3|99.8|100.0|1.8|100.0|99.6|98.8|90.6|100.0|99.6|100.0|99.8|100.0|89.6|
Centurio Qwen|99.8|95.2|95.1|100.0|98.6|93.9|100.0|100.0|99.4|100.0|100.0|100.0|100.0|98.8|99.0|80.9|100.0|96.7|99.8|98.8|100.0|100.0|100.0|95.7|99.6|99.4|3.7|100.0|99.4|98.2|86.5|100.0|99.8|99.6|99.2|100.0|86.5|
Parrot|100.0|25.0|100.0|0.0|0.0|0.0|0.0|0.0|0.0|100.0|100.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|0.0|100.0|0.0|0.0|100.0|0.0|0.0|0.0|100.0|0.0|0.0|100.0|0.0|100.0|0.0|0.0|0.0|
PALO 13B|100.0|60.1|98.6|93.9|47.1|87.5|100.0|60.7|99.6|0.0|74.0|71.5|99.8|35.4|98.2|70.1|9.0|66.4|99.2|61.5|9.8|0.0|99.8|92.2|41.2|27.5|0.0|95.5|68.2|94.9|1.6|26.4|68.0|9.4|11.3|54.7|88.9|
PALO 7B|100.0|72.0|99.6|98.8|47.5|93.4|100.0|58.2|99.8|0.0|91.8|52.7|100.0|30.7|98.8|27.0|90.8|96.9|99.4|99.2|91.6|0.0|99.4|95.1|95.5|27.0|0.0|69.1|100.0|96.9|0.0|56.8|91.6|84.4|0.0|99.6|99.8|
InternVL 2.5 4B|100.0|91.0|96.7|93.9|97.1|82.8|100.0|99.0|99.8|98.8|96.1|95.3|100.0|96.7|91.4|96.1|96.9|99.6|100.0|99.2|48.2|99.6|83.0|99.6|100.0|7.0|98.8|99.2|97.7|34.6|90.8|98.2|97.7|95.7|96.1|99.8|
InternVL 2.5 8B|100.0|91.1|99.4|95.3|97.7|82.8|100.0|100.0|99.4|97.9|98.2|96.3|100.0|98.4|95.1|83.2|98.2|96.7|100.0|99.8|99.2|66.8|99.2|86.5|99.6|99.8|1.2|99.8|99.8|98.2|54.7|99.4|99.2|98.4|40.6|100.0|99.8|
Qwen2-VL 2B|100.0|13.2|8.2|0.0|0.0|9.6|12.9|0.2|5.9|58.4|0.2|10.9|10.0|4.5|0.0|3.1|0.2|12.7|3.9|19.3|18.0|0.2|0.0|5.3|0.0|34.0|0.0|15.4|0.0|23.6|4.5|0.0|1.0|1.0|0.8|12.7|98.8|
Qwen2-VL 7B|100.0|90.0|96.5|98.2|93.9|86.1|99.8|99.4|99.2|99.2|95.7|96.3|98.2|98.2|60.2|79.1|75.4|86.9|99.0|98.8|99.0|64.5|99.2|94.1|95.7|95.3|0.2|98.2|99.4|97.9|72.1|95.1|98.8|89.8|83.2|98.2|99.0|
Maya|100.0|65.7|99.0|96.1|67.6|85.5|98.6|92.0|99.8|0.2|12.1|1.0|100.0|77.0|98.4|20.7|60.7|40.6|99.6|99.8|91.4|0.0|99.8|80.1|92.0|43.9|0.0|95.7|100.0|96.7|1.6|0.0|47.9|96.3|7.2|62.5|99.8|
Llama-Vision|100.0|33.3|0.0|0.0|4.9|68.8|95.5|7.0|52.7|0.0|35.0|80.7|88.3|0.0|0.0|17.0|91.0|1.6|94.7|0.0|0.0|93.0|99.6|9.0|9.2|48.2|0.8|92.6|0.2|33.8|73.6|0.0|2.3|0.2|0.0|0.2|0.0|
Phi 3.5 Vision|100.0|40.8|58.4|0.6|1.4|85.4|99.2|16.2|99.4|0.0|15.2|30.1|99.8|14.8|4.7|25.2|56.4|31.6|99.0|58.6|9.0|1.0|93.6|89.8|27.3|63.9|0.0|56.8|0.0|85.0|2.9|13.7|3.5|38.1|0.0|51.8|37.9|
Pixtral 12B|100.0|96.8|99.8|99.6|98.8|95.9|100.0|99.4|100.0|100.0|99.8|99.8|100.0|99.8|100.0|100.0|93.4|100.0|99.6|100.0|100.0|99.6|100.0|95.5|100.0|100.0|9.4|99.6|100.0|100.0|95.9|99.4|100.0|99.8|100.0|100.0|99.8|
Pangea|99.8|87.9|98.8|99.0|97.9|19.1|99.6|99.8|99.2|98.4|91.6|68.9|100.0|100.0|98.2|67.8|93.6|97.9|100.0|99.4|100.0|0.8|99.6|95.7|99.6|100.0|0.0|100.0|99.6|67.0|82.4|99.8|100.0|99.8|91.0|99.8|99.0|
MiniCPM 2.6|99.8|92.3|94.7|96.5|95.5|96.3|100.0|99.8|99.8|99.0|98.4|97.9|100.0|62.9|92.6|77.3|94.5|93.6|100.0|98.4|99.2|99.2|99.6|95.5|96.5|99.8|10.0|98.2|97.3|99.4|66.4|85.5|96.3|95.1|99.2|90.6|97.1|{{< /table-caption >}}
> 🔼 표 41은 XM3600 데이터셋에서 언어 충실도(language fidelity)를 보여줍니다. XM3600은 다양한 언어로 된 이미지 캡션 데이터셋입니다. 이 표는 다양한 사전 학습 및 미세 조정 전략(예: 사용된 언어의 수, 영어 데이터 비율, OCR 데이터 포함 여부)에 따른 각 언어의 캡션 생성 성능을 보여주는 상세한 결과를 담고 있습니다.  각 언어별로 정확도를 측정하여 다국어 모델의 언어별 성능을 정량적으로 평가합니다. 이를 통해 다국어 모델의 훈련 전략이 각 언어의 성능에 미치는 영향을 자세히 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 41: XM3600 Language Fidelity
> </details>

{{< table-caption >}}
| Model | en | avg. | ar | es | fr | ru |
|---|---|---|---|---|---|---|
|Centurio Aya | 65.0 | 62.4 | 61.7 | 61.0 | 64.3 | 62.7 |
|Centurio Qwen | 75.4 | 70.2 | 68.8 | 70.9 | 70.5 | 70.8 |
|Parrot | 28.7 | 31.4 | 34.0 | 24.3 | 30.0 | 37.4 |
|PALO 13B | 56.6 | 53.6 | 51.8 | 52.7 | 54.9 | 55.0 |
|PALO 7B | 58.0 | 53.4 | 52.5 | 52.3 | 53.7 | 55.1 |
|InternVL 2.5 4B | 69.0 | 58.7 | 55.7 | 58.8 | 61.4 | 59.0 |
|InternVL 2.5 8B | 73.5 | 66.4 | 61.8 | 68.0 | 68.4 | 67.3 |
|Qwen2-VL 2B | 61.9 | 56.2 | 52.9 | 55.3 | 58.6 | 57.9 |
|Qwen2-VL 7B | 62.1 | 59.6 | 59.2 | 58.9 | 60.0 | 60.3 |
|Maya | 50.1 | 43.9 | 45.3 | 42.7 | 45.8 | 41.8 |
|Phi 3.5 Vision | 58.9 | 53.3 | 49.7 | 52.7 | 56.4 | 54.3 |
|Pixtral 12B | 60.9 | 52.7 | 36.0 | 57.9 | 59.0 | 58.1 |
|Pangea | 69.0 | 65.2 | 64.5 | 64.3 | 66.3 | 65.7 |
|MiniCPM 2.6 | 71.9 | 65.4 | 61.1 | 67.5 | 67.0 | 66.1 |{{< /table-caption >}}
> 🔼 표 42는 XVNLI(Cross-lingual Visual Natural Language Inference) 데이터셋에 대한 다양한 대규모 언어 모델(LLM)의 성능을 보여줍니다.  각 모델의 영어 및 다국어 성능을 평가하여, 영어 전용 학습 모델과 다국어 학습 모델을 비교 분석합니다.  표에는 각 모델의 정확도(Accuracy)가 언급되어 있으며, 영어 데이터셋만을 사용한 모델과 다양한 언어 데이터셋을 사용한 모델 간의 성능 차이를 명확하게 보여줍니다. 다양한 언어를 지원하는 LLM의 성능 및 효율성을 평가하는 데 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 42: XVNLI
> </details>

{{< table-caption >}}
|       | en   | avg. | ar   | fr   | hi   | id   | ja   | pt   |
|-------|------|------|------|------|------|------|------|------|
|Centurio Aya | 37.6 | 37.2 | 36.2 | 38.9 | 38.8 | 39.7 | 34.2 | 35.4 |
|Centurio Qwen | 46.4 | 43.0 | 39.6 | 45.0 | 41.6 | 44.1 | 43.5 | 44.1 |
|Parrot      | 35.3 | 32.4 | 31.9 | 34.9 | 26.1 | 31.3 | 34.9 | 35.4 |
|PALO 13B    | 32.4 | 28.9 | 24.2 | 34.9 | 24.2 | 31.6 | 26.4 | 32.3 |
|PALO 7B     | 31.8 | 30.9 | 28.2 | 33.6 | 27.3 | 30.6 | 32.3 | 33.3 |
|InternVL 2.5 4B | 49.2 | 42.7 | 41.6 | 45.6 | 33.7 | 43.4 | 44.2 | 47.8 |
|InternVL 2.5 8B | 50.7 | 45.2 | 40.3 | 48.7 | 41.2 | 43.1 | 47.6 | 50.2 |
|Qwen2-VL 2B | 36.8 | 35.5 | 31.5 | 41.3 | 30.2 | 36.7 | 36.1 | 37.0 |
|Qwen2-VL 7B | 43.0 | 40.7 | 36.9 | 42.6 | 38.5 | 41.1 | 41.3 | 43.8 |
|Maya        | 37.9 | 33.3 | 32.6 | 36.6 | 31.3 | 31.6 | 32.0 | 36.0 |
|Phi 3.5 Vision | 41.7 | 37.4 | 34.9 | 44.3 | 29.2 | 37.7 | 35.7 | 42.4 |
|Pixtral 12B | 30.3 | 26.2 | 19.1 | 28.5 | 19.2 | 27.3 | 28.6 | 34.7 |
|Pangea      | 43.1 | 42.0 | 37.6 | 43.0 | 38.5 | 46.8 | 41.6 | 44.8 |
|MiniCPM 2.6 | 39.1 | 36.5 | 30.5 | 38.9 | 33.7 | 37.7 | 37.2 | 40.7 |{{< /table-caption >}}
> 🔼 표 43은 논문의 xMMMU 벤치마크 결과를 보여줍니다. xMMMU는 다중 이미지를 포함한 다양한 시각적 질문응답 과제를 평가하기 위해 설계된 벤치마크입니다. 표는 다양한 언어 모델의 성능을 보여주며, 영어(en)와 다양한 언어(avg)에 대한 평균 정확도 점수를 비롯하여 여러 언어에 대한 개별 정확도 점수를 제공합니다. 이를 통해 다국어 능력에 대한 각 모델의 강점과 약점을 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 43: xMMMU
> </details>

{{< table-caption >}}
Model|avg.|amh-ethiopia|arz-egypt|ben-india|bre-france|bul-bulgaria|fil-philippines|gle-ireland|hin-india|ibo-nigeria|ind-indonesia|jav-indonesia|jpn-japan|kin-rwanda|kor-south korea|mar-india|min-indonesia|mon-mongolia|msa-malaysia|nor-norway|orm-ethiopia|por-brazil|ron-romania|rus-russia|sin-sri lanka|spa-argentina|spa-chile|spa-colombia|spa-ecuador|spa-mexico|spa-spain|spa-uruguay|sun-indonesia|swa-kenya|tam-india|tel-india|urd-india|urd-pakistan|zho-china|zho-singapore
---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---
Centurio Aya|49.4|32.1|52.7|45.8|30.4|50.1|48.8|41.7|67.2|31.0|53.6|41.1|44.8|32.8|61.7|56.9|42.6|29.2|52.7|55.5|36.4|65.1|61.6|65.5|28.9|60.0|58.5|56.0|55.2|52.6|68.2|40.3|42.0|50.2|49.5|37.0|47.3|50.5|64.6|65.6
Centurio Qwen|52.9|38.0|52.7|54.9|30.6|49.6|51.7|48.5|65.7|30.5|54.9|46.1|44.8|42.1|66.2|55.9|41.8|33.3|55.9|58.2|35.0|70.8|57.0|67.5|42.7|63.8|66.2|59.8|58.8|61.9|70.4|42.5|41.5|56.4|43.0|50.5|52.7|56.9|71.1|73.1
Parrot|41.1|31.6|35.5|33.9|31.1|38.8|45.3|45.1|41.8|35.5|43.4|37.7|34.5|32.8|47.6|32.2|36.3|34.3|42.9|49.5|34.6|60.9|44.0|45.0|28.0|47.9|52.1|48.5|43.9|44.3|65.7|36.2|31.5|40.7|36.9|29.5|31.8|32.9|64.3|55.2
PALO 13B|39.6|26.1|31.5|33.9|31.6|35.3|45.3|41.1|40.3|32.5|41.0|35.4|33.0|28.9|42.8|37.6|37.8|26.3|44.1|54.5|29.4|53.9|52.6|44.0|24.9|47.5|50.0|47.3|47.8|44.9|63.2|39.4|37.5|39.6|31.3|29.5|35.9|40.3|46.6|39.6
PALO 7B|37.1|20.5|25.1|30.1|27.7|32.6|43.3|37.1|43.3|31.0|37.9|33.7|29.1|29.4|42.4|33.7|31.1|25.6|36.8|47.5|33.6|51.1|49.3|45.5|24.0|47.5|49.1|45.2|45.9|42.4|57.5|36.2|31.5|31.1|29.0|28.5|34.1|40.3|46.3|42.0
InternVL 2.5 4B|48.1|36.3|38.9|42.7|33.1|42.0|47.8|45.7|51.7|29.0|54.6|44.4|39.4|34.9|65.9|48.0|41.0|27.6|53.0|52.8|34.6|66.5|49.7|65.5|34.7|60.4|59.8|54.4|56.6|53.9|68.2|44.8|44.0|45.8|35.5|41.0|47.7|41.7|74.6|66.5
InternVL 2.5 8B|48.6|29.5|41.4|42.3|29.4|47.4|46.8|47.5|50.2|33.5|54.9|44.8|41.4|32.8|56.9|43.6|44.6|33.0|54.3|55.2|32.2|64.4|60.3|62.5|29.8|60.4|65.4|56.4|59.7|57.0|72.3|44.8|41.5|50.9|35.5|39.5|44.1|39.8|78.5|72.6
Qwen2-VL 2B|33.6|27.4|31.0|33.6|25.9|32.9|32.0|31.3|34.8|35.5|36.9|31.6|25.1|31.5|37.6|24.3|27.9|31.1|32.1|40.5|33.2|39.8|32.5|33.0|24.9|40.0|40.2|40.7|39.0|35.0|42.1|34.6|33.5|37.7|25.2|27.0|30.5|31.9|44.1|41.5
Qwen2-VL 7B|37.6|31.2|35.5|31.5|31.1|35.6|40.9|37.1|39.3|31.0|40.8|32.3|36.0|30.2|43.4|31.2|33.5|34.0|43.5|42.8|37.4|47.9|34.8|47.5|30.7|44.5|47.9|40.7|42.3|40.2|47.8|41.6|31.5|34.1|26.6|26.5|37.3|31.0|51.4|43.4
Maya|39.8|30.3|41.9|38.8|30.6|36.7|35.0|34.4|46.8|31.0|36.2|34.7|29.1|31.5|50.0|42.6|33.9|31.1|44.4|47.5|29.9|53.5|51.3|42.0|30.2|44.9|47.4|45.2|45.6|39.3|55.7|34.3|33.5|38.8|32.2|29.0|43.2|48.1|50.5|50.9
Llama-Vision|38.8|32.1|5.4|60.1|13.6|22.4|43.8|35.9|46.3|28.5|42.0|34.0|25.1|18.3|45.9|38.1|34.3|27.9|40.6|48.5|23.4|38.7|47.7|52.0|48.4|47.9|55.1|51.0|48.1|48.3|70.1|37.1|29.5|52.0|60.7|62.5|24.5|15.3|36.3|23.1
Phi 3.5 Vision|40.9|28.6|38.4|28.7|28.9|33.7|45.3|40.2|42.8|38.0|40.8|35.4|36.9|36.2|44.1|33.7|39.0|35.3|41.3|48.2|33.6|62.0|43.7|45.0|29.3|55.1|59.0|51.9|52.8|48.0|64.2|45.1|32.0|46.5|29.4|32.5|29.5|26.9|51.1|40.6
Pixtral 12B|33.5|22.6|27.1|21.7|24.9|30.5|35.5|38.7|41.3|26.5|36.9|32.3|27.6|25.1|39.7|24.3|28.3|24.7|36.8|32.1|21.5|41.2|28.8|40.5|23.6|49.1|54.3|43.6|48.3|40.6|48.4|40.3|27.0|42.1|22.9|19.0|27.7|23.6|47.3|39.6
Pangea|55.2|35.5|49.3|53.5|33.1|52.3|56.7|53.1|66.2|40.0|60.0|50.5|42.9|33.6|68.3|57.9|48.2|40.7|60.3|58.2|36.4|69.7|62.9|73.5|36.0|63.8|67.1|61.4|62.4|60.7|73.0|44.8|49.0|65.6|46.7|55.0|57.7|65.7|71.7|68.4
MiniCPM 2.6|34.1|26.9|31.5|27.6|25.9|32.6|31.5|37.1|32.3|36.0|36.2|31.6|33.5|30.6|31.0|32.2|29.9|29.2|34.6|40.5|36.0|45.1|33.4|37.0|26.7|37.7|44.4|40.7|38.7|35.9|42.5|36.2|29.0|34.1|24.3|28.5|32.7|22.7|48.2|46.2{{< /table-caption >}}
> 🔼 표 44는 CVQA(Culturally-diverse Visual Question Answering) 데이터셋에 대한 결과를 보여줍니다. 이 표는 다양한 언어와 문화적 배경을 가진 이미지에 대한 질문과 답변의 정확도를 측정한 결과를 제시합니다. Centurio 모델을 포함한 여러 다국어 비전-언어 모델의 성능을 비교 분석하여 각 모델의 강점과 약점을 파악할 수 있도록 합니다. 특히, 다양한 언어와 문화적 배경을 고려한 질문에 대한 모델의 적응력을 평가하는 데 초점을 맞춥니다.
> <details>
> <summary>read the caption</summary>
> Table 44: CVQA
> </details>

{{< table-caption >}}
|               | en  | avg. | avg. Latin | avg. other | ar  | de  | hi  | id  | it  | ko  | ru  | th  | zh  | zu  |
| :------------- | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| Centurio Aya   | 83.1 | 74.2 | 80.9       | 69.7       | 75.9 | 82.1 | 80.1 | 81.4 | 80.6 | 68.8 | 73.5 | 66.5 | 53.4 | 79.5 |
| Centurio Qwen  | 84.8 | 76.1 | 82.7       | 71.8       | 76.9 | 83.5 | 82.4 | 83.8 | 83.1 | 72.4 | 75.6 | 64.4 | 58.9 | 80.2 |
| Parrot         | 51.0 | 49.9 | 50.5       | 49.5       | 50.4 | 51.6 | 49.6 | 51.0 | 49.8 | 50.4 | 50.5 | 48.2 | 47.8 | 49.5 |
| PALO 13B       | 54.0 | 51.5 | 52.7       | 50.7       | 50.9 | 53.2 | 51.2 | 52.5 | 52.8 | 51.0 | 49.5 | 51.0 | 50.7 | 52.1 |
| PALO 7B        | 55.5 | 52.8 | 55.4       | 51.0       | 50.4 | 56.9 | 51.0 | 55.0 | 54.1 | 51.6 | 51.1 | 51.4 | 50.2 | 55.8 |
| InternVL 2.5 4B | 87.0 | 78.3 | 86.9       | 72.6       | 54.9 | 87.6 | 59.8 | 87.0 | 88.2 | 89.4 | 86.4 | 55.1 | 90.4 | 84.8 |
| InternVL 2.5 8B | 91.0 | 79.2 | 88.7       | 72.8       | 55.8 | 89.8 | 54.9 | 89.1 | 89.1 | 92.5 | 86.9 | 53.1 | 93.6 | 86.9 |
| Qwen2-VL 2B    | 85.0 | 83.5 | 83.4       | 83.5       | 70.6 | 84.4 | 86.5 | 84.1 | 83.5 | 88.1 | 78.8 | 86.4 | 90.4 | 81.8 |
| Qwen2-VL 7B    | 91.2 | 90.9 | 90.1       | 91.4       | 83.4 | 90.5 | 94.8 | 91.0 | 90.8 | 93.8 | 87.5 | 94.1 | 94.9 | 88.2 |
| Maya           | 51.4 | 50.9 | 51.6       | 50.4       | 50.4 | 53.4 | 50.1 | 51.5 | 50.0 | 49.9 | 49.5 | 51.1 | 51.6 | 51.6 |
| Llama-Vision   | 91.1 | 84.8 | 89.9       | 81.5       | 63.2 | 90.1 | 91.1 | 89.5 | 91.9 | 87.4 | 83.0 | 84.8 | 79.5 | 88.0 |
| Phi 3.5 Vision | 92.2 | 79.4 | 90.2       | 72.2       | 53.1 | 91.9 | 83.8 | 89.2 | 90.9 | 77.9 | 86.6 | 55.5 | 76.5 | 88.8 |
| Pixtral 12B    | 91.1 | 71.0 | 90.5       | 58.0       | 50.4 | 91.5 | 53.6 | 91.1 | 90.9 | 49.5 | 88.2 | 52.9 | 53.4 | 88.4 |
| Pangea         | 87.2 | 72.2 | 85.7       | 63.1       | 51.5 | 86.6 | 69.4 | 86.2 | 87.1 | 71.4 | 79.2 | 54.4 | 52.9 | 82.9 |
| MiniCPM 2.6    | 89.0 | 74.3 | 88.0       | 65.2       | 52.0 | 89.0 | 53.1 | 87.9 | 89.0 | 54.8 | 84.0 | 53.1 | 94.5 | 86.0 |{{< /table-caption >}}
> 🔼 표 45는 논문의 '2.5 RQ4: 다국어 텍스트-이미지 작업 개선' 섹션에 속하며, 다국어 광학 문자 인식(OCR) 기능을 평가하기 위한 합성 다국어 플롯 질의응답(SMPQA) 데이터셋의 '접지' 작업에 대한 결과를 보여줍니다.  이 표는 다양한 언어 및 모델에 대한 정확도를 보여주는  다양한 설정(예: 사전 훈련 유무, 다국어 데이터 비율, 이미지 인코더 고정 여부 등)에 따른 결과가 포함되어 있습니다.  각 행은 특정 설정과 언어에 대한 성능을 보여주고, 열은 특정 언어의 성능을 보여줍니다. 이 표는 다국어 OCR 데이터를 포함하여 다국어 텍스트-이미지 이해를 개선하는 방법에 대한 연구 결과를 요약하고 있습니다.  특히, 영어 데이터의 비율을 조정하거나 다국어 OCR 데이터를 포함하는 것의 영향을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 45: SMPQA Ground
> </details>

{{< table-caption >}}
|           | en    | avg.  | avg. Latin | avg. other | ar    | de    | hi    | id    | it    | ko    | ru    | th    | zh    | zu    |
| :-------- | :---- | :---- | :--------- | :--------- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- | :---- |
| Centurio Aya | 60.0  | 30.1  | 49.8       | 17.0       | **29.2** | 50.2  | 17.6  | 52.6  | 51.2  | 11.2  | 38.2  | 4.8   | 0.8   | 45.2  |
| Centurio Qwen | 65.2  | 31.7  | 54.3       | 16.6       | **21.4** | 53.2  | 21.4  | 55.4  | 56.6  | 16.2  | 34.8  | 5.2   | 0.6   | 52.2  |
| Parrot       | 0.0   | 0.0   | 0.0        | 0.1        | 0.0   | 0.0   | 0.0   | 0.0   | 0.0   | 0.4   | 0.0   | 0.0   | 0.0   | 0.0   |
| PALO 13B     | 25.6  | 4.0   | 9.9        | 0.1        | 0.0   | 12.0  | 0.0   | 10.2  | 12.4  | 0.4   | 0.0   | 0.0   | 0.0   | 5.0   |
| PALO 7B      | 22.4  | 2.7   | 6.7        | 0.1        | 0.0   | 8.4   | 0.0   | 7.0   | 7.0   | 0.4   | 0.0   | 0.0   | 0.0   | 4.4   |
| InternVL 2.5 4B | 77.8  | 47.5  | 67.7       | 34.0       | 0.0   | 71.0  | 0.0   | 69.8  | 69.6  | **69.0** | 54.4  | 0.2   | 80.2  | 60.4  |
| InternVL 2.5 8B | 80.6  | **48.2** | 68.1       | 34.9       | 0.0   | 69.2  | 0.0   | 70.4  | 70.8  | 67.2  | 61.2  | 0.2   | 80.8  | 62.2  |
| Qwen2-VL 2B   | 68.8  | 47.4  | 60.0       | **39.0**     | 0.2   | 61.2  | **24.8** | 59.4  | 61.2  | 66.0  | 46.8  | **24.0** | 72.0  | 58.2  |
| Qwen2-VL 7B   | **85.0** | **64.9** | **76.2**    | **57.4**    | 1.8   | **80.6** | **58.6** | **75.8** | **79.2** | **77.6** | **70.6** | **43.8** | **92.0** | **69.2** |
| Maya         | 14.6  | 1.8   | 4.3        | 0.1        | 0.0   | 8.2   | 0.0   | 3.6   | 4.6   | 0.4   | 0.0   | 0.0   | 0.0   | 0.8   |
| Llama-Vision  | 58.4  | 22.8  | 46.6       | 6.9        | 0.0   | 55.4  | 2.4   | 38.4  | 37.2  | 8.4   | 13.0  | 6.0   | 11.8  | 55.4  |
| Phi 3.5 Vision | 84.8  | 35.9  | 69.4       | 13.5       | 0.2   | 70.8  | 12.0  | 69.4  | 76.6  | 15.4  | 40.4  | 0.2   | 12.8  | 61.0  |
| Pixtral 12B   | **85.0** | 35.9  | **73.3**    | 10.9       | 0.0   | **71.8** | 0.0   | **75.4** | **81.6** | 0.4   | **64.6** | 0.4   | 0.0   | **64.6** |
| Pangea       | 72.0  | 23.8  | 54.4       | 3.4        | 0.0   | 58.6  | 0.2   | 57.2  | 64.4  | 0.4   | 19.2  | 0.4   | 0.0   | 37.4  |
| MiniCPM 2.6   | 80.8  | 39.3  | 67.5       | 20.6       | 0.0   | 67.2  | 0.0   | 69.8  | 71.4  | 1.0   | 38.4  | 0.4   | **83.6** | 61.6  |{{< /table-caption >}}
> 🔼 표 46은 합성 다국어 플롯 질의응답(SMPQA) 데이터셋의 이름 맞추기 작업에 대한 결과를 보여줍니다.  이 표는 다양한 언어와 모델 구성에 따른 성능을 비교 분석하여, 다국어 OCR(광학 문자 인식) 능력 평가를 위한 SMPQA 데이터셋의 유용성을 보여줍니다. 각 열은 특정 언어 또는 모델 설정에 대한 정확도를 나타내며, 행은 다양한 모델 및 학습 전략을 나타냅니다.  이 표를 통해 다국어 OCR 성능에 영향을 미치는 요인들을 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 46: SMPQA Name
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