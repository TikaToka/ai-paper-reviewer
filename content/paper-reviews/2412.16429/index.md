---
title: "LearnLM: Improving Gemini for Learning"
summary: "LearnLM은 교육적 맥락에서 생성형 AI의 페다고지(Pedagogy)를 향상시킨 모델입니다.  **교사나 개발자가 원하는 페다고지적 특성을 모델에 주입하는 새로운 프레임워크**를 통해 기존 모델보다 학습 효과를 31% 향상시켰습니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["AI Applications", "Education", "🏢 Google DeepMind",]
showSummary: true
date: 2024-12-21
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.16429 {{< /keyword >}}
{{< keyword icon="writer" >}} LearnLM Team et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-24 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.16429" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.16429" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/learnlm-improving-gemini-for-learning" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

본 논문은 교육 분야에서 **생성형 AI 모델의 페다고지(Pedagogy) 개선**이라는 어려운 문제를 해결하기 위한 연구입니다. 기존 연구는 페다고지를 명확히 정의하고 모델에 적용하는 데 어려움을 겪었는데, 이 논문에서는 **페다고지적 지시사항 따르기**라는 새로운 프레임워크를 제안하여 이 문제를 해결했습니다.  이 프레임워크는 교사나 개발자가 원하는 페다고지적 특성을 명시적으로 모델에 전달하는 방식으로, 모델이 특정 페다고지에 국한되지 않고 다양한 교육적 상황에 적용될 수 있도록 합니다.



연구진은 제안된 방법론을 사용하여 LearnLM이라는 새로운 모델을 개발하였습니다.  LearnLM은 다양한 학습 시나리오에서 **기존 모델들(GPT-40, Claude 3.5, Gemini 1.5 Pro) 보다 훨씬 높은 선호도**를 보였습니다. 이는 LearnLM이 교육적 맥락에서 생성형 AI의 성능을 크게 향상시켰음을 보여줍니다. 본 연구는 교육 분야에서 생성형 AI의 활용 가능성을 높이는 데 기여하며, 향후 연구의 방향을 제시하는 데 중요한 의미를 가집니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} LearnLM은 **교육적 지시사항 따르기를 통해** 기존 모델보다 학습 효과를 크게 향상시켰다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} **다양한 교육적 맥락**에 적용 가능한 유연한 프레임워크를 제공한다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} **인간 피드백 강화 학습(RLHF)**을 통해 모델의 미묘한 페다고지적 지시사항 따르기를 개선했다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **교육적 상황에서 생성형 AI 모델의 성능을 향상시키는 새로운 방법론**을 제시하고, 이를 통해 교육 분야에서 생성형 AI 기술의 활용 가능성을 높이는 데 기여합니다.  **기존의 제한적인 방법론을 넘어**, 다양한 교육적 맥락에 적용 가능한 유연한 프레임워크를 제공하며, 향후 연구 방향을 제시하는 데 중요한 의미를 지닙니다.  **실제 교육 환경에 대한 깊이 있는 이해**를 바탕으로 한 평가 방법론 제시는 특히 주목할 만합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.16429/x1.png)

> 🔼 이 그림은 LearnLM을 다른 시스템들과 비교 평가한 3단계 인간 평가 과정과 결과를 보여줍니다. 먼저, 평가자들이 AI 튜터와 상호 작용하는 특정 학습자의 역할을 수행할 수 있도록 학습 시나리오를 개발합니다. 각 시나리오에 대한 배경 자료(에세이, 숙제 문제, 다이어그램 등)와 시스템 지침이 각 모델에 대한 컨텍스트로 제공됩니다. 그런 다음, 교육 전문가들이 각 모델을 개별적으로 평가하고 상대적 성능을 비교하기 위한 일련의 질문에 답합니다. 이러한 상대적 평가는 7점 척도(-3에서 +3까지)로 이루어지며, LearnLM이 GPT-40, Claude 3.5 및 Gemini 1.5 Pro보다 우수하다는 것을 보여주는 종합적인 선호도를 나타냅니다. 자세한 내용은 4절을 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Figure 1: An overview of our three-stage human evaluation pipeline and our results for comparing LearnLM with other systems. (1) Learning scenarios are developed that allow raters to role-play specific learners interacting with pairs of AI tutors (2). Grounding material (e.g. an essay, homework problem, diagram, etc.) and System Instructions specific to each scenario are passed as context to each model. The resulting conversation pairs are reviewed by pedagogy experts (3) who answer a range of questions assessing each model on its own as well as their comparative performance. These comparative ratings (on a seven-point -3 to +3 Likert scale) are aggregated (4) to show overall preference for LearnLM over GPT-4o, Claude 3.5, and Gemini 1.5 Pro. See Section 4 for more detailed results.
> </details>





{{< table-caption >}}
| System | Version | Avg Turns per Conversation | Avg Words per Turn |
|---|---|---|---| 
| LearnLM | 2024-11-19 | 11.0 | 174 |
| Gemini 1.5 Pro | 2024-09-24 | 10.3 | 130 |
| GPT-4o | 2024-08-06 | 10.1 | 137 |
| Claude 3.5 Sonnet | 2024-06-20 | 9.7 | 179 |{{< /table-caption >}}

> 🔼 이 표는 LearnLM을 선호하는 학습자의 설명에서 더 자주 나타나는 주제(상위 세 행)와 다른 모델을 선호하는 학습자의 설명에서 더 자주 나타나는 주제(하위 세 행)를 보여줍니다. 이 표에 제시된 주제는 표본 선호도 설명의 최소 10%에서 언급되었으며, LearnLM과 다른 모델을 선호하는 설명 간의 발생 비율이 극단적으로 높은 주제들입니다.  각 주제에 대한 설명과 LearnLM 또는 다른 모델을 선호하는 응답자 비율이 함께 제시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Themes which were more likely to appear in “learner” explanations of preferences favoring LearnLM (top three rows), or favoring other models (bottom three rows). This table displays themes (i) referenced by at least 10%percent1010\%10 % of all sampled preference explanations, and (ii) showing an extreme ratio of occurrence between explanations favoring LearnLM and explanations favoring other models.
> </details>





### In-depth insights


#### Pedagogical Instruction
본 논문에서 '교수학적 지시(Pedagogical Instruction)'는 생성 AI 모델이 교육적 맥락에서 학습자와 상호 작용하는 방식을 **제어**하고 **개선**하기 위한 핵심 전략으로 제시됩니다.  단순히 지식을 전달하는 것이 아니라, **학습자의 참여를 유도하고**, **학습 과정을 조율**하며, **학습 목표 달성을 지원**하는 데 초점을 맞춥니다.  이는 사전에 정의된 교수법에 모델을 제한하는 것이 아니라, **교사나 개발자가 원하는 특정 교수법적 속성을 지시**할 수 있도록 함으로써 다양한 교육적 요구사항을 충족할 수 있는 유연성을 제공합니다.  **강화학습(RLHF)** 및 **인간 피드백**을 활용하여 모델이 **세분화된 지시를 따르도록 훈련**하는 방식은, 단순한 지시 따르기를 넘어 **교수-학습 상호작용의 미묘한 측면까지 고려**하는 발전된 모델을 구축하는 데 중요한 역할을 합니다. 이러한 접근법은 **모델의 일반화 능력을 높이고**, 다양한 교육 환경에 적응력을 향상시키는 데 기여합니다.  **LearnLM 모델**은 이러한 '교수학적 지시' 개념을 기반으로 개발되어, 기존 모델들보다 우수한 평가를 받았다는 점에서 그 효용성이 입증되었습니다.

#### LearnLM Model Training
LearnLM 모델 훈련은 기존 Gemini 모델을 교육적 목표에 맞춰 개선하는 과정입니다. **기존의 지도 학습 방식(SFT)을 기반으로** 하되, **교육적 지시 사항을 따르는(pedagogical instruction following) 방식**으로 학습 데이터를 구성하여 모델의 반응을 제어합니다.  **강화 학습(RLHF)**를 통해 사람의 선호도를 반영하고, **Gemini 모델과의 공동 훈련(co-training)**을 통해 기존 기능을 유지하면서 교육적 기능을 향상시키는 점이 특징입니다.  이를 통해 다양한 학습 시나리오에서 전문가 평가자들로부터 높은 선호도를 얻었으며, 특히 **GPT-4, Claude 3.5, Gemini 1.5 Pro 모델 대비 유의미한 성능 향상**을 보였습니다.  **Google AI Studio에서 LearnLM 모델을 공개**하여 사용자 피드백을 수렴하고 지속적인 개선을 추진하는 점도 주목할 만합니다.  **다양한 교육적 문맥과 학습자 유형을 고려한 시나리오 기반 평가**를 통해 실제 교육 환경에서의 효과성을 검증하고자 노력한 점 또한 인상적입니다.

#### Human Evaluation Design
본 논문의 "Human Evaluation Design" 부분은 **인간 평가자를 활용한 엄격하고 신뢰할 수 있는 평가 체계**를 구축하는 데 중점을 둡니다.  이는 단순히 모델의 성능 측정을 넘어, **실제 교육 환경에서의 실용성과 교육적 효과**를 평가하고자 하는 의도를 보여줍니다.  세 단계의 평가 과정(시나리오 설계, 대화 수집, 교육적 평가)을 통해 **다양한 학습 상황과 학습자 유형을 포괄**하려는 노력이 돋보입니다.  특히, 전문적인 교육 경험을 가진 평가자들을 대거 활용하여 **객관적이고 전문적인 평가**를 확보하고자 한 점은 주목할 만합니다.  **베이지안 통계 기법**을 활용하여 불확실성까지 고려한 정량적 분석을 수행하고, 질적 분석을 병행하여 심층적인 이해를 도모하고자 한 시도 또한 인상적입니다.  이러한 다각적인 접근 방식은 **모델 개발의 개선 방향을 제시**하고, **실제 교육 현장에 적용 가능성을 높이는 데 기여**할 것으로 기대됩니다.  전반적으로, 본 논문의 "Human Evaluation Design"은 AI 교육 모델 평가의 새로운 기준을 제시하는 중요한 부분입니다.

#### Co-training Benefits
공동 학습의 이점은 **기존의 대규모 언어 모델(LLM)의 강점을 유지하면서 교육적 행동을 통합하는 데** 있습니다. 기존 LLM은 방대한 지식과 다양한 작업 수행 능력을 갖추고 있지만, 교육적 맥락에서의 사용성은 제한적입니다. 공동 학습을 통해 기존 LLM의 강점을 해치지 않고 **교육적 지시사항을 따르는 능력**을 향상시킬 수 있습니다. 이는 **교육 관련 데이터를 기존 LLM 학습 데이터와 혼합**하여 모델이 다양한 교육적 상황에 적응하고 학습 목표 달성을 위한 효과적인 전략을 개발하는 데 도움이 됩니다. 또한, 공동 학습은 모델의 **일관성 및 안정성 유지**에도 기여합니다.  **새로운 교육적 행동을 학습하는 과정에서 이전에 학습된 다른 능력을 훼손하지 않도록** 돕기 때문입니다. 따라서, 공동 학습은 **교육 분야에서의 LLM 활용도를 높이는 데 중요한 역할**을 할 것으로 예상됩니다.

#### Future Research
본 논문은 학습용 생성 AI 모델 개선에 대한 심도있는 연구를 제시하며, **교육적 지침 따르기(pedagogical instruction following)** 라는 새로운 프레임워크를 통해 사용자 참여를 유도하는 방식을 제안합니다.  향후 연구 방향으로는 **보편적인 교육 평가 프레임워크 구축**, **내재적 평가(intrinsic evaluation)에서 외재적 평가(extrinsic evaluation)로의 전환**, **다양한 교육 환경 및 과목 적용 확대** 등이 제시됩니다. 특히, **학습 성과 측정**을 통한 실질적 효과 검증과 더불어 **안전성 및 책임감 있는 AI 개발**에 대한 지속적인 노력이 강조되어야 할 것입니다.  **의료 교육 분야를 포함한 다양한 분야로의 확장 연구**는 AI 기반 교육 시스템의 활용 가능성을 더욱 넓힐 것입니다. 마지막으로, **교사 및 교육 개발자의 의견 수렴**을 통해 AI 기반 교육 시스템의 실제 적용 가능성을 높이는 것이 중요하다고 판단됩니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.16429/x3.png)

> 🔼 이 그림은 교육 시나리오를 기반으로 대화를 생성하는 워크플로우를 보여줍니다. 참가자는 시나리오에 정의된 프롬프트 모델과 대화를 나눕니다. 그리고 나서 참가자는 모델 간의 품질과 선호도를 파악하는 설문조사에 응답합니다. 설문조사 질문은 대화의 품질, 참여자의 학습 목표 달성 여부, 튜터의 유용성과 친근함 등에 관한 것들이 포함됩니다. 이 그림은 사용자에게 시나리오 기반 평가의 전체 과정과 그 결과를 이해하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Workflow to generate conversations based on educational scenarios. A participant enacts conversations with prompted models as defined by scenarios. The participant then fills out a survey capturing quality and preference between models.
> </details>



![](https://arxiv.org/html/2412.16429/x4.png)

> 🔼 그림 3은 (위쪽) 비교 대상이 된 대규모 언어 모델(LLM)과 수집된 모든 대화에 대한 통계(대화당 평균 모델 턴 수, 턴당 평균 단어 수)를 보여줍니다. (아래쪽) 각 모델이 턴당 사용한 단어 수에 대한 히스토그램을 나타냅니다.  이 그림은 각 모델의 응답 길이와 응답의 품질 간의 상관관계를 분석하는 데 사용되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: (Top) The specific LLMs compared, along with aggregate statistics across all conversations collected: average number of model turns per conversation and average number of words per turn; (Bottom) Histograms of the number of words used per turn by each model.
> </details>



![](https://arxiv.org/html/2412.16429/x7.png)

> 🔼 그림 4는 LearnLM과 다른 최신 시스템(Claude 3.5, GPT-40, Gemini 1.5 Pro)에 대한 전문가들의 선호도를 보여줍니다. 산점도는 7점 척도의 선호도 평가의 기본 분포를 나타냅니다. 수집된 많은 평가를 고려하여, 각 척도당 500개의 평가를 비례적으로 축소하고, 선호도 척도(짙은 보라색은 LearnLM에 대한 강한 선호도를 나타냄)에 따라 색상을 코딩하고, 가독성을 위해 각 정수 등급 주변에 무작위로 배치했습니다. 빨간색 점과 오차 막대는 추정 평균과 95% 신뢰 구간을 나타냅니다. 이 평균은 그림 1에도 표시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Pedagogy experts’ preferences over LearnLM and other contemporaneous systems (Claude 3.5, GPT-4o, and Gemini 1.5 Pro). The scatterplots represent the underlying distribution of seven-point preference ratings. Given the large number of ratings we collected, these scatterplots proportionally downsample to 500 ratings per measure, color-coded based on the preference scale (dark purple corresponds to strong preference for LearnLM), and randomly positioned around each integer rating for readability. The red points and error bars indicate the estimated mean and its 95% credible interval for each measure. These means are also shown in Figure 1.
> </details>



![](https://arxiv.org/html/2412.16429/x8.png)

> 🔼 그림 5는 7점 리커트 척도(매우 동의하지 않음~매우 동의함)를 사용하여 연구팀의 교육학적 평가 척도 각 항목에 대한 시스템 평가 결과를 보여줍니다. 오차 막대는 사후 분포의 평균에 대한 95% 신뢰 구간을 나타냅니다. 이 그림은 다양한 대규모 언어 모델이 제시하는 교육적 행동의 질적 차이를 정량적으로 비교 분석한 것입니다. 각 모델의 강점과 약점을 보여주는 다양한 교육적 특성을 비교하여, 모델 개선 및 교육 기술 향상에 대한 통찰력을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Evaluation of systems on each category of our pedagogy rubric from a 7-point Likert scale ('Strongly disagree' to 'Strongly agree'). Error bars reflect 95% credible intervals from the posterior distrubtion for the mean.
> </details>



![](https://arxiv.org/html/2412.16429/x11.png)

> 🔼 그림 6은 교육 전문가들이 학습자 역할을 수행하면서 경험한 인상을 보여줍니다. 오차 막대는 평균에 대한 사후 분포의 95% 신뢰 구간을 반영합니다. 왼쪽의 인상 질문에는 5점 척도(전혀 아님~매우 그렇다)가, 오른쪽의 경험 질문에는 7점 리커트 척도(매우 동의하지 않음~매우 동의함)가 사용되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Impressions shared by the pedagogy experts role-playing as learners in our pedagogical scenarios. Error bars reflect 95% credible intervals from the posterior distribution for the mean. The rating scales for impression questions (left) were 5-point extent scales (“Not at all” to “Extremely”), and 7-point Likert scales (“Strongly disagree” to “Strongly agree”) for experience questions (right).
> </details>



![](https://arxiv.org/html/2412.16429/x12.png)

> 🔼 그림 7은 학습자 역할을 수행하는 교육 전문가들이 LearnLM과 다른 최신 모델(Claude-3.5, GPT-4o, Gemini 1.5 Pro)을 선호하는 정도를 보여줍니다. 산점도는 7점 척도의 선호도 평가의 기저 분포를 나타냅니다. 수집된 평가 수가 많기 때문에, 산점도는 각 측정값에 대해 500개의 평가를 비례적으로 표본 추출하여 표시합니다. 빨간색 점과 오차 막대는 각 측정값에 대한 추정 평균과 95% 신뢰 구간을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Preferences over LearnLM and other contemporary models (Claude-3.5, GPT-4o, and Gemini 1.5 Pro) according to the pedagogical experts role-playing as learners. The scatterplots represent the underlying distribution of seven-point preference ratings. Given the large number of ratings we collected, these scatterplots proportionally downsample to 500 ratings per measure. The red points and error bars indicate the estimated mean and its 95% credible interval for each measure.
> </details>



![](https://arxiv.org/html/2412.16429/x13.png)

> 🔼 그림 8은 연구의 세 번째 단계인 교육적 평가 과정의 시작 부분에서, 전문가들에게 대화 기록에 참여한 사람들이 시나리오 지침을 얼마나 잘 따랐는지(즉, 시나리오에서 학습자 역할을 얼마나 효과적으로 수행했는지)를 7점 척도로 평가하도록 요청했던 과정을 보여줍니다. 이 그래프는 대화 기록별로 그룹화되고 평균화된 응답을 보여주며,  전반적으로 학습자들이 시나리오 지침을 93.4%의 대화 기록에서 따랐음을 나타냅니다. 이는 학습자들이 시나리오의 지침을 잘 따랐다는 것을 의미하며, 연구의 신뢰성을 높여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: At the beginning of the pedagogical assessment process, we asked experts to evaluate how closely the human participants in the conversation transcripts followed the scenario instructions (i.e., how effectively they role-played the learner in the scenario) on a seven-point scale. This plot shows the responses grouped and averaged by transcript. These aggregate ratings indicated that the “learner” followed the scenario instructions in 93.4% of conversation transcripts.
> </details>



![](https://arxiv.org/html/2412.16429/x14.png)

> 🔼 그림 9는 '인지 부하' 평가 척도의 세부 항목에 대한 교사 모델 평가 결과를 보여줍니다. 각 세부 항목에 대해, LearnLM, Gemini 1.5 Pro, GPT-40, Claude 3.5 모델의 평균 점수와 95% 신뢰 구간이 오차 막대로 표시되어 있습니다. 이는 다양한 측면에서 각 모델의 성능을 비교 분석하여, 어떤 모델이 학습 과정에서 인지적 부담을 줄이는 데 더 효과적인지 파악하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Evaluation of tutor models on specific subdimensions of the “Cognitive load” rubric category. Error bars reflect 95% credible intervals from the posterior distribution for the mean.
> </details>



![](https://arxiv.org/html/2412.16429/extracted/6084483/figures/student_sxs_preference_gemini_m6_medical.png)

> 🔼 그림 10은 논문의 '능동적 학습' 평가 척도에 대한 하위 측면별 튜터 모델 평가 결과를 보여줍니다. 각 하위 측면에 대한 평균 점수와 95% 신뢰 구간을 오차 막대로 표시하여, 각 모델의 강점과 약점을 보다 명확하게 비교 분석할 수 있도록 합니다.  '능동적 학습' 이라는 큰 주제 아래,  '적극적인 참여 유도', '질문', '소크라테스식 질문', '비소크라테스식 질문' 등 구체적인 측면들을 평가하여, 튜터 모델의 학습 참여 유도 능력의 다양한 측면들을 종합적으로 평가하고 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Evaluation of tutor models on specific subdimensions of the “Active learning” rubric category. Error bars reflect 95% credible intervals from the posterior distribution for the mean.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Theme | Appearances when participants preferred LearnLM (n=94) | Appearances when participants preferred other models (n=80) | Example responses |
|---|---|---|---| 
| keeps_on_topic | 20 (**21.2%**) | 8 (10%) | 
"[LearnLM] didn’t let me get away with distractions"
"[LearnLM] was much more able to keep things on track"
"[The other tutor] also did a much better job of getting me back on task" |
| challenges_learner | 31 (**33.0%**) | 13 (16.3%) | 
"obviously [LearnLM] was better [...] [the other tutor] clearly wasn’t pushing me to do well"
"I felt like [LearnLM] was trying to help me grow and learn, rather than just agreeing with what I said"
"[The other tutor] asked interesting questions that made me think deeper" |
| gives_away_answers | 32 (**34.0%**) | 15 (18.8%) | 
"[LearnLM] really engaged me in the steps to answer the question whereas [the other tutor] just gave me the answer"
"[LearnLM] was keen on how to get the answer rather than giving the answer"
"[LearnLM] was too reticent to help by giving answers when it was clear the student needed it" |
| clarity | 15 (16.0%) | 16 (**20.0%**) | 
"The structure of the support [for the other tutor] was a bit clearer for the student to follow"
"[The other tutor] started smaller and simpler"
"I just thought the answers [for LearnLM] were more clear" |
| info_amount | 19 (20.2%) | 20 (**25.0%**) | 
"[The other tutor] was [...] more succinct"
"[The other tutor] gave me everything I needed when I asked"
"[LearnLM] did a better job of breaking this "complex" topic into more digestible bites" |
| conversation_style | 30 (31.9%) | 29 (**36.3%**) | 
"I [...] felt that [LearnLM] was a bit patronizing"
"[The other tutor] seemed warmer and more engaging"
"[LearnLM] was warmer and more encouraging" |{{< /table-caption >}}
> 🔼 표 6은 대화 수집 연구에서 참가자들이 대화를 마친 후 작성한 설문지의 질문 내용과 응답 형식을 보여줍니다.  설문지는 AI 튜터와의 상호 작용에 대한 참가자들의 경험을 평가하기 위한 질문들로 구성되어 있습니다.  구체적으로, 학습 목표 달성 여부, 튜터에 대한 전반적인 인상, 튜터의 친절함, 유용성, 향후 사용 의향 등에 대한 질문들이 포함되어 있습니다.  각 질문에는 해당하는 척도(예: 7점 리커트 척도)가 제시되어 있으며, 일부 질문에는 자유 답변란이 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Conversation-level questions within the conversation collection study
> </details>

{{< table-caption >}}
| Scenario 1 |  | 
|---|---| 
| **Subject area** | Computer science | 
| **Subtopic** | Introduction to Python | 
| **Interaction setting** | Classroom | 
| **Learning goal** | Homework Help | 
| **Grounding materials** | [Google doc containing student code](https://storage.googleapis.com/arcade-external-pdfs/f421aaa1-f724-474a-bebf-3d50999ebd42/m6_eval_grounding/Python%20sample.pdf) | 
| **Learner persona** | - Rejects or unenthusiastically accepts tutor’s invitations without feedback 
- Provides relevant but minimal responses to questions 
- Follows most instructions but does not elaborate 
- Does not “show work” 
- Does not pose questions 
- Seeks to receive answers or solutions to topical questions (transactional) | 
| **Initial learner query** | ```python
def analyze_text(text):
  vowels = 0
  consonants = 0
  uppercase = 0
  lowercase = 0


  for char in text:
    if char in "aeiou":
      vowels += 1
    else:
      consonants += 1


    if char.isupper():
      uppercase += 1
    elif char.islower():
      lowercase += 1


  print("Vowels:", vowels)
  print("Consonants:", consonants)
  print("Uppercase:", uppercase)
  print("Lowercase:", lowercase)


# Get user input
text = input("Enter some text: ")


# Analyze the text
analyze_text(text)
``` | 
| **Conversation plan** | You are a student in an introduction to Python course. **You were recently assigned the task of writing a piece of code** that can elicit a text input then report back on the numbers of vowels, consonants, uppercase, and lowercase letters. When you run the code, you get no error messages. But when you input “Am I a better coder than Steve Jobs?”, the numbers in the output don’t seem correct. You simply don’t understand what went wrong, so you ask your AI tutor for help. You paste your code in with your initial query, seeking a quick fix without doing a lot of work.
<br>
<br>Your code does not have capital vowels in your in operator. See if the tutor helps you notice that your code is counting punctuation marks as letters and then give you hints to fix your code. | 
| **System instructions** | You are a helpful assistant serving as a teaching assistant in an intro programming course (in python). 
<br>You keep your answers brief and to the point, and instead of giving away answers directly you try to guide the student to the solution. Be encouraging and positive, and always try to help the student understand the concepts. 
<br>You should always respond as if you are messaging with the student. 
<br>Accordingly, make sure to pay attention to the context of the conversation and the student’s current understanding of the material.
Lastly, as I said before, keep it brief/concise to avoid overwhelmingly the student. 
<br>
<br>The student is generally working on a programming assignment (or assignments) where they need to take a string input from the user, and then loop over that inputted string to provide some metrics about the text (like how many vowels, consonants, upper case, lower case letters, etc.). 
<br>
<br>If they ask you about how to do this, you should guide them to a solution without giving away the answer and/or code directly.
<br>
<br>You must be very careful to NOT help the student cheat, or give them solutions directly. 
<br>
Again, if you give too much information to the student, and/or don’t help them learn for themselves, I’ll have to fire you, because you are being a bad tutor (and helping the student cheat). | {{< /table-caption >}}
> 🔼 이 표는 대화 수집 연구의 일환으로 참가자들이 두 튜터와의 상호작용을 비교한 후 작성한 설문지의 질문 내용과 응답 형식을 보여줍니다.  각 질문은 선호하는 튜터, 선호도 이유, 학습 목표 달성에 더 효과적이었던 대화, 학생의 요구와 능숙도에 더 잘 적응한 튜터, 전반적으로 더 나은 경험이었던 대화 등과 관련이 있습니다.  응답 옵션은 각 질문 유형에 따라 다릅니다. 예를 들어, 선호하는 튜터에 대한 질문에는 여러 수준의 선호도를 나타내는 옵션이 있고, 선호도 이유에 대한 질문은 서술형 답변을 허용합니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Comparative questions within the conversation collection study
> </details>

{{< table-caption >}}
| Scenario 2 |  | 
|---|---| 
| **Subject area** | English | 
| **Subtopic** | Literature | 
| **Interaction setting** | Classroom | 
| **Learning goal** | Teach me X | 
| **Grounding materials** | (none) | 
| **Learner persona** | • Poses multiple queries unrelated to the learning objective<br>• Steers conversation toward non-academic topics<br>• Challenges or debates the tutor in an adversarial manner<br>• Seeks to shift the topic (disinterested) | 
| **Initial learner query** | Explain the significance of Yorick’s skull in “Hamlet”. Be quick. | 
| **Conversation plan** | You are a high school student who had to read Hamlet for class and have a discussion about the significance of the skull for class tomorrow. **You want to be prepared for this discussion.** You are not intrinsically motivated and found Hamlet dry and hard to understand. | 
| **System instructions** | Tutor me at an appropriate level, adapting to my responses. Make a plan based on the learning goal of the conversation. Guide me through this plan and help me learn about the topic. Do not overwhelm me with too much information at once. Wrap up this conversation once I have shown evidence of understanding. | {{< /table-caption >}}
> 🔼 표 8은 대화 수준의 교육적 평가를 위한 측정 항목의 업데이트된 내용을 보여줍니다. 각 측정 항목(예: 인지 부하 관리, 적극적 학습 유도, 메타인지 심화 등)에 대한 질문과 함께 해당 항목에 대한 자세한 설명이 포함되어 있습니다. 이 표는 평가자들이 각 대화에 대한 교육적 측면을 보다 정확하고 포괄적으로 평가할 수 있도록 돕는 것을 목적으로 합니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Updated rubric dimensions for conversation-level pedagogical assessment.
> </details>

{{< table-caption >}}
| Scenario 3 |
|---|---| 
| **Subject area** | Math |
| **Subtopic** | Algebra |
| **Interaction setting** | Self-Taught |
| **Learning goal** | Practice |
| **Grounding materials** | (none) |
| **Learner persona** |  * Offers some direction regarding the learning, but generally takes the tutor’s lead
* Answers tutor’s questions with care
* “Shows work” when prompted
* Asks relevant but superficial questions (low “depth of knowledge”)
* Seeks to acquire and retain knowledge about the topic (instrumental) |
| **Initial learner query** | Given the polynomials:

* P(x) = 2x^3 - 5x^2 + 3x - 1
* Q(x) = x^2 + 4x - 2

Perform the following operations:

Addition: Find P(x) + Q(x)
Multiplication: Find P(x) * Q(x) |
| **Conversation plan** | You are a student who wishes to **practice solving math problems**. Your teacher often calls on students at random to solve problems in front of the whole class, and this makes you nervous. You aren’t certain about the concepts and processes, and **you’d like to learn so you won’t be embarrassed in class** because English is not your primary language. However, you are reluctant to ask questions in your math lessons, so you turn to an AI tutor. Still, your confidence is quite low. 

See if the tutor can recognize your emotional unsteadiness and offer encouragement, especially when you make mistakes, and if it adjusts its English level to meet yours. |
| **System instructions** | You are a tutor that excels in promoting active learning. Active learning occurs when learners do something beyond merely listening or reading to acquire and retain information. Rather, active learning requires students to think critically through a process of comparison, analysis, evaluation, etc. You encourage active learning by asking probing and guiding questions. 

Active learning also occurs when students work through complex questions and problems step by step. As such, you don’t solve problems for your students, but you offer scaffolds and hints as needed throughout the process. 

Active learning can be difficult, and students may get frustrated. Knowing this, you meet your student where they are in their development, celebrate their student’s successes, and share encouraging feedback when they make errors.|{{< /table-caption >}}
> 🔼 표 9는 비교 교육적 평가를 위한 평가 척도를 보여줍니다.  각 척도는 두 개의 대화형 튜터(LearnLM과 다른 모델)를 비교 평가하기 위한 질문을 제시하고 있습니다.  평가 척도는 교육적 측면(예: 더 나은 교육법, 더 나은 학습 지원)과 기술적 측면(예: 시스템 지침 준수 여부)을 모두 고려하고 있습니다. 이 표는 사용자가 두 튜터 중 어떤 튜터를 선호하는지, 어떤 튜터가 학습 목표 달성에 더 효과적인지 등을 평가할 수 있도록 설계되었습니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Rubric for comparative pedagogical assessment
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