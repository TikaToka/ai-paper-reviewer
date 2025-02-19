---
title: "Explorer: Scaling Exploration-driven Web Trajectory Synthesis for Multimodal Web Agents"
summary: "Explorer는 94,000개 이상의 다양한 웹 트래젝토리 데이터셋을 생성하여 웹 에이전트 성능을 크게 향상시킨 혁신적인 연구입니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Human-AI Interaction", "🏢 Ohio State University",]
showSummary: true
date: 2025-02-17
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.11357 {{< /keyword >}}
{{< keyword icon="writer" >}} Vardaan Pahuja et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-18 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.11357" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.11357" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/explorer-scaling-exploration-driven-web" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

최근 대규모 다중 모달 모델(LMM)의 발전으로 웹 상에서 자동화된 작업을 수행하는 에이전트에 대한 관심이 높아지고 있습니다. 하지만, 현실적인 온라인 환경에서의 성능은 아직 인간 수준에 미치지 못하며, 이는 **다양하고 대규모의 트래젝토리 수준 데이터셋 부족**이라는 주요한 문제점 때문입니다. 기존 데이터셋은 수동으로 주석을 달거나, 제한된 범위의 작업만 포함하는 등의 한계가 있습니다. 



본 논문에서는 이러한 문제를 해결하기 위해 **대규모 다양한 웹 트래젝토리 데이터셋을 생성하는 확장 가능한 방법론인 Explorer**를 제시합니다. Explorer는 웹 탐색 및 정제를 통해 다양한 작업 의도를 얻고, 94,000개 이상의 성공적인 웹 트래젝토리 데이터셋을 생성합니다. 이 데이터셋을 사용하여 훈련된 Explorer는 다양한 웹 에이전트 벤치마크에서 강력한 성능을 보였고, 데이터 규모의 중요성을 보여줍니다. **본 연구는 저렴한 비용으로 대규모의 고품질 웹 트래젝토리 데이터셋을 생성하는 방법**을 제시하여 웹 에이전트 연구의 발전에 크게 기여할 것으로 기대됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} Explorer는 **94,000개 이상의 다양한 웹 트래젝토리 데이터셋**을 생성하는 확장 가능한 방법을 제시합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} **합성 데이터를 사용한 웹 에이전트 학습**을 통해 기존 방식보다 우수한 성능을 달성하였습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 본 연구는 **웹 에이전트 연구의 진입장벽을 낮추고 연구 확장에 기여**할 것으로 기대됩니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대규모 다양한 웹 트래젝토리 데이터셋을 생성하는 확장 가능한 방법론**을 제시하여, **웹 에이전트 연구의 발전에 크게 기여**할 수 있습니다.  **합성 데이터의 효율성과 다양성**을 보여줌으로써, 기존의 고비용의 수동 데이터 수집 방식을 뛰어넘는 새로운 가능성을 제시합니다.  이를 통해 더욱 **강력하고 일반화된 웹 에이전트**를 개발하는 데 활용될 수 있으며, **웹 에이전트 연구의 진입 장벽을 낮추는 역할**도 할 것으로 예상됩니다. 향후 **웹 에이전트의 발전 및 관련 연구의 확장**에 중요한 역할을 할 것으로 기대됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.11357/x1.png)

> 🔼 그림 1은 웹 에이전트 훈련을 위한 웹 트래젝토리 데이터 생성 파이프라인을 보여줍니다. 먼저, 작업 제안 에이전트가 웹사이트의 홈페이지를 기반으로 초기 작업과 첫 번째 행동을 생성합니다. 그런 다음, 작업 개선 에이전트가 후속 단계에서 반복적으로 작업을 개선합니다. 마지막으로, 작업 요약 에이전트가 행동 순서로부터 전체 작업 설명을 구성하고, 작업 확인을 통해 정확성을 평가합니다. 이 파이프라인은 다양하고 고품질의 웹 트래젝토리를 생성하여 웹 에이전트의 성능을 향상시키는 데 기여합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Data Generation Pipeline. The task proposer agent generates an initial task and the first action based on the website homepage. The task is then iteratively refined in subsequent steps by the refiner agent. Finally, the task summarizer agent constructs an overall task description from the action sequence, followed by task verification to assess correctness.
> </details>





{{< table-caption >}}
| # Trajectories | # Websites | Modality |
|---|---|---| 
| RUSS Xu et al. (2021) | 80 | 22 | HTML |
| Mind2Web Deng et al. (2023) | 2350 | 137 | HTML + Screenshot |
| WebLINX Lu et al. (2024) | 969 | 155 | HTML + Screenshot |
| GUIAct Chen et al. (2024a) | 2482 | 121 | Screenshot |
| OpenWebVoyager He et al. (2024b) | 1165 | 48 | A11y tree + Screenshot |
| AgentTrek Xu et al. (2024a) | 10.4K | 127 | A11y tree + HTML + Screenshot |
| NNetnav Murty et al. (2024) | 6K | 4 | A11y tree + Screenshot |
| **Explorer** | **94K** | **49K** | **A11y tree + Screenshot (raw + SoM) + HTML** |{{< /table-caption >}}

> 🔼 표 1은 기존 웹 에이전트 벤치마크와 Explorer 모델의 비교를 보여줍니다.  트레이젝토리 수, 웹사이트 수, 그리고 사용된 모달리티(HTML, 스크린샷, 접근성 트리 등)를 비교하여 Explorer의 규모와 데이터 다양성을 강조합니다.  기존 벤치마크들이 상대적으로 작은 규모의 데이터셋을 사용한 반면, Explorer는 훨씬 더 크고 다양한 데이터셋을 활용하여 웹 에이전트 성능 향상에 기여함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparison to existing web agent benchmarks.
> </details>





### In-depth insights


#### WebAgent Synthesis
본 논문은 웹 환경에서 **자율적으로 작업을 수행하는 웹 에이전트를 합성하는 방법**에 대한 심층적인 논의를 제공합니다.  **다양한 웹 상호작용 데이터셋을 구축하는 과정**과 **이를 기반으로 웹 에이전트를 학습시키는 모델**에 대해 자세히 설명합니다.  특히, **대규모 다중 모드 언어 모델을 활용하여 웹 에이전트를 개발**하는 접근 방식은 주목할 만하며, **합성 데이터를 이용한 효율적인 학습 방식**은 실제 환경 적용에 중요한 의미를 지닙니다.  **탐색 기반의 웹 트래젝토리 합성**은 에이전트의 다양한 능력을 확보하는 데 기여하고, **데이터 확장성**을 고려한 설계는 실용적인 측면에서 높은 평가를 받습니다.  **다양한 평가 지표**를 사용한 실험 결과를 통해 웹 에이전트의 성능을 검증하고, 향후 연구 방향을 제시하는 것도 논문의 중요한 특징입니다.  **합성 데이터의 질과 양, 그리고 다양성**은 웹 에이전트 성능에 직접적인 영향을 미치므로, 본 논문에서 제시된 방법론은 웹 에이전트 기술 발전에 중요한 기여를 할 것으로 예상됩니다.

#### Explorer Pipeline
본 논문에서 제시된 Explorer 파이프라인은 **웹 상호작용의 다양성과 현실성을 확보하기 위한 핵심 구성 요소**입니다.  기존의 단순한 합성 데이터 생성 방식과 달리, **탐색 기반 접근법**을 통해 다양한 웹 페이지를 탐색하고, 사용자의 의도를 반영한 복잡한 작업들을 수행하는 다양한 경로를 생성합니다. 이를 위해 **여러 에이전트(Task Proposer, Task Refiner, Task Summarizer, Task Verifier)**가 단계적으로 협력하여 **웹 페이지의 콘텐츠를 깊이 있게 이해하고, 현실적인 사용자 행동 패턴을 모방**합니다.  각 에이전트는 LLM 기반으로 동작하여 웹 페이지의 시각적 요소와 텍스트 정보를 활용하며, **상호작용 과정의 현실성을 높이기 위해 다양한 제약 조건(예: 로봇 감지, CAPTCHA)**을 고려합니다.  **결과적으로, Explorer 파이프라인은 대규모이고 다양한 웹 상호작용 경로 데이터셋을 생성**하여, 실제 환경에서의 웹 에이전트 성능 향상에 크게 기여할 것으로 기대됩니다.  특히, **저렴한 비용으로 다양한 작업 시나리오를 생성**하는 점은 주목할 만합니다.

#### Data Scaling Impact
데이터 확장의 영향에 대한 심층적인 분석은 **모델 성능 향상에 있어 데이터 규모의 중요성을 강조**합니다.  일반적으로 더 많은 데이터는 더 나은 성능으로 이어지지만, 본 연구는 **데이터 양 증가에 따른 성능 향상의 한계점**과 **데이터 품질의 중요성**을 보여줍니다.  **적절한 데이터 전처리 및 특징 선택**은 모델의 일반화 능력과 효율성에 크게 영향을 미치며, 단순히 데이터 양만 늘리는 것보다 **데이터의 다양성과 품질**을 확보하는 것이 더 중요함을 시사합니다.  따라서 데이터 확장 전략은 **목표 모델과 작업의 특성에 맞춰** 신중하게 설계되어야 하며, **데이터 품질 관리 및 효율적인 데이터 활용 방안**에 대한 고려가 필수적입니다.  **비용 효율적인 데이터 확보 전략** 또한 중요한 고려 사항이며, 본 연구에서 제시된 합성 데이터 생성 기법은 이러한 측면에서 **실용적인 대안**이 될 수 있음을 보여줍니다.

#### Failure Modes
논문에서 'Failure Modes' 제목 아래 제시된 내용은 **웹 에이전트가 작업을 수행하는 과정에서 발생할 수 있는 오류 유형**을 분석한 부분으로 보입니다.  **예측 불가능한 웹 환경**의 특성상 다양한 오류가 발생할 수 있음을 시사하며, **데이터 수집 과정의 한계**와 **에이전트 설계의 미흡함**을 드러냅니다.  구체적으로, **잘못된 웹사이트 접근, 작업에서 벗어난 행동, 중요 단계 누락, 웹사이트 응답 지연, 잘못된 요소 인식** 등의 문제가 언급될 가능성이 높습니다. 이러한 오류 분석을 통해 **시스템 개선 방향**을 제시하고, **실제 웹 환경에서의 에이전트 성능 향상**에 대한 논의가 이어질 것으로 예상됩니다.  **데이터의 다양성 확보** 및 **에이전트의 강건성 확보**를 위한 후속 연구 방향을 제시하는 데 중요한 부분이 될 것입니다.  **오류 분석의 깊이와 정확성**은 시스템의 신뢰성과 실용성을 판단하는 중요한 지표가 될 것입니다.

#### Future Research
미래 연구 방향에 대한 심도있는 논의는 본 논문의 핵심 내용을 뛰어넘는 추가적인 연구를 제시합니다. **웹 환경 탐색의 자동화**를 위한 좀 더 정교한 방법론 개발이 중요하며, 이를 위해 **다양한 웹사이트 및 상호 작용 방식**에 대한 광범위한 데이터셋 구축이 필수적입니다.  또한, **복잡한 웹 작업의 자동 완료**를 목표로 하는 에이전트 개발에 있어, **장기적인 계획 수립 및 시각적 정보와의 연계**에 대한 연구가 필요합니다.  **합성 데이터의 품질 개선**을 위한 노력도 중요한데,  **실제 사용자의 행동 패턴**을 보다 정확히 반영하는 합성 데이터 생성 기법을 개발하여 모델의 일반화 성능을 높여야 합니다.  더 나아가, **윤리적 문제**에 대한 고려 또한 중요하며,  **개인 정보 보호 및 웹사이트 악용 방지**를 위한 체계적인 접근 방식을 마련하는 것이 필수적입니다. 마지막으로, **다양한 유형의 웹 에이전트**를 위한 일반화된 프레임워크 개발을 통해,  **더욱 광범위한 웹 애플리케이션에 대한 적용 가능성**을 확대하는 것이 미래 연구의 중요한 과제입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.11357/extracted/6205031/figures/hist_num_tok.png)

> 🔼 그림 2는 Explorer 데이터셋의 각 웹 경로(trajectory)에 포함된 토큰 수의 분포를 히스토그램으로 나타낸 것입니다. 가로축은 토큰 수, 세로축은 상대 빈도를 나타냅니다. 빨간색 수직선은 토큰 수 분포의 90번째 백분위수를 나타내며, 이는 데이터셋 내 웹 경로의 토큰 수의 대부분이 빨간색 선 이하에 집중되어 있음을 보여줍니다. 이는 데이터셋의 대부분의 경로가 상대적으로 짧다는 것을 의미합니다.  이 그림은 Explorer 데이터셋의 특징을 보여주는 중요한 통계 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Histogram of token distribution across trajectories in Explorer. The red vertical line shows the 90t⁢hsuperscript90𝑡ℎ{90}^{th}90 start_POSTSUPERSCRIPT italic_t italic_h end_POSTSUPERSCRIPT percentile of the distribution.
> </details>



![](https://arxiv.org/html/2502.11357/extracted/6205031/figures/treemap_4.png)

> 🔼 그림 3은 Explorer 데이터셋의 도메인 및 하위 도메인 분포를 보여줍니다. 다양한 웹사이트와 작업 유형을 포함하여, 다양한 종류의 웹 에이전트를 훈련시키는 데 사용될 수 있는 잠재력을 보여줍니다.  Explorer 데이터셋의 방대한 다양성은 일반적인 웹 에이전트의 훈련에 유용하며, 다양한 웹 상호 작용 시나리오를 처리할 수 있는 능력을 향상시킬 수 있습니다.  서비스, 엔터테인먼트, 쇼핑, 여행, 정보 등의 다양한 범주가 포함되어 실제 웹 사용 환경을 더 잘 반영합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Data composition for Explorer. Its extensive diversity showcases its potential to train end-to-end generalist web agents.
> </details>



![](https://arxiv.org/html/2502.11357/extracted/6205031/figures/perf_metrics.png)

> 🔼 그림 4는 Mind2Web-Live 벤치마크에서 데이터 크기 조정 실험을 보여줍니다. Explorer-4B 모델을 사용하여 전체(100%), 절반(50%), 그리고 1/4(25%)의 궤적 데이터로 실험을 수행했습니다. 모든 지표는 세 번의 실행에 걸쳐 평균을 냈습니다. 결과적으로, 데이터 크기가 증가함에 따라 모든 지표가 향상되는 것을 확인했습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Experiments with data scaling using Explorer-4B on Mind2Web-Live. We experiment with using 100%, 50%, and 25% of the trajectory data. All results are averaged over three runs. All metrics exhibit improvement with increase in data scale.
> </details>



![](https://arxiv.org/html/2502.11357/extracted/6205031/figures/perf_metrics_2.png)

> 🔼 그림 5는 Mind2Web-Live 평가에서 발생하는 다양한 오류 유형에 대한 통계를 보여줍니다.  각 오류 유형은 발생 빈도를 나타내는 막대 그래프로 표현됩니다.  가장 두드러진 오류 유형은 작업 편차(Task deviation)이며, 이는 에이전트가 지정된 작업과 관련 없는 동작을 수행하는 경우를 의미합니다.  다른 오류 유형으로는 웹사이트에 접근하지 못하는 경우, 주요 단계 누락, 웹사이트 응답 없음, 접지 오류 등이 있습니다. 이 그림은 웹 에이전트의 성능을 개선하기 위해 해결해야 할 중요한 오류 유형들을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Statistics for different error cases in Mind2Web-Live evaluation. Task deviation is the most prevalent error type.
> </details>



![](https://arxiv.org/html/2502.11357/extracted/6205031/figures/error_plot_2.png)

> 🔼 그림 E.1은 Explorer가 생성한 합성 웹 경로의 예시입니다. 각 단계는 GPT-4 에이전트가 수행한 접지된 액션과 함께 집합 마크 주석이 달린 스크린샷을 보여줍니다. 이 그림은 사용자가 웹사이트를 탐색하고 특정 작업(이 경우에는 3인용 패브릭 소파 찾기)을 완료하기 위해 수행하는 일련의 단계를 보여줍니다. 각 스크린샷은 사용자의 액션에 따라 웹사이트가 어떻게 변하는지 보여주는 시각적 맥락을 제공합니다. 접지된 액션은 모델이 웹사이트와 상호작용하는 방법, 즉 특정 요소를 클릭하거나 입력하는 방법을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure E.1: Example synthetic trajectory from Explorer. Each step shows the set-of-mark annotated screenshot along with the grounded action taken by the GPT-4 agent.
> </details>



![](https://arxiv.org/html/2502.11357/x2.png)

> 🔼 그림 E.2는 모델이 트래젝토리 생성, 모델 훈련 및 추론하는 동안 사용하는 입력의 시각화를 보여줍니다. 이 예시는 그림 1의 트래젝토리 2단계에 해당합니다. 그림에는 웹페이지의 스크린샷, 웹페이지의 접근성 트리를 보여주는 set-of-mark 주석이 달린 스크린샷이 포함되어 있습니다. 이러한 입력을 사용하여 모델은 다음에 수행할 작업을 예측합니다.
> <details>
> <summary>read the caption</summary>
> Figure E.2: Visualization of the model inputs during trajectory generation, model training, and inference. The example corresponds to step 2 of the trajectory in Figure 1.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Information | Service | Entertainment | Shopping | Travel |
|---|---|---|---|---|
| View the detailed 7-day weather forecast for Toronto, ON on The Weather Network website. | Research the French Bulldog breed on the American Kennel Club website, including its popularity and family life traits. | Find the Basscon presents: Darren Styles EDM event on Eventbrite, save it, and share it on Twitter. | Browse through the fall home decor section on the Target website to explore a variety of fall-themed home decor items. | Search for flights from Seattle to New York, select travel dates, and explore various flight options. |
| Analyze Tesla’s stock performance over various time periods on Yahoo Finance. | Find the nearest Penske truck rental location in Anaheim, California, and start the reservation process for a truck. | View the details of the Photography Competition Winners - Season X and share the article on Twitter. | Purchase a three-seat fabric sofa, specifically the UPPLAND Sofa, from IKEA’s website. | Find the weight of baggage allowance for economy class on qatarairways. |
| Convert 100 US Dollars to Euros using the XE currency converter. | Explore and purchase a subscription for the UpToDate Pro Suite on the Wolters Kluwer website. |  |  |  |
| Find directions from Seattle, WA to Bellevue, WA using Bing Maps. |  |  |  |  |{{< /table-caption >}}
> 🔼 표 2는 논문에서 제시된 Explorer 모델이 생성한 웹 상호작용 예시들을 보여줍니다. 각 예시는 사용자가 웹사이트에서 수행할 수 있는 다양한 유형의 작업(정보 탐색, 서비스 이용, 쇼핑, 여행 계획 등)을 설명하는 자연어 형태의 작업 설명을 포함합니다. 이 표는 Explorer 모델이 다양한 도메인과 작업 유형에 걸쳐 다양한 웹 상호작용을 생성할 수 있음을 보여주는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Example task descriptions from Explorer.
> </details>

{{< table-caption >}}
| Action Type | Description | Count |
|---|---|---|
| click [elem] | Click on elem. | 415K |
| type [elem] [text] | Type text. | 62K |
| select [elem] [text] | Select text from dropdown list. | 5K |
| goto [url] | Go to url. | 26K |
| search_google [query] | Search for query on Google. | 4K |
| scroll [up/down] | Scroll up or down. | 213K |{{< /table-caption >}}
> 🔼 표 3은 Explorer 웹 에이전트에서 웹 탐색을 위해 사용되는 행동 공간을 보여줍니다.  각 행동 유형(클릭, 입력, 선택, 스크롤)과 해당 설명, 그리고 각 행동 유형이 데이터셋에서 차지하는 비율을 나타냅니다.  이는 웹 에이전트가 웹 페이지와 상호 작용하는 방식을 이해하는 데 중요한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Action space for web navigation in Explorer.
> </details>

{{< table-caption >}}
| Metric | Value |
|---|---| 
| # Total trajectories | 175K |
| # Success trajectories | 94K |
| # Unique URLs | 49K |
| Average steps per trajectory | 7.7 |
| Average elements per image | 46.3 |
| # Tokens | 830M |
| # Elements | 33.3M |
| # Images | 720K |
| Cost per trajectory | $0.15 |
| Cost per successful trajectory | $0.28 |{{< /table-caption >}}
> 🔼 표 4는 Explorer 데이터셋의 통계를 보여줍니다. 성공적인 경로의 수, 고유 URL 수, 평균 경로 길이, 평균 이미지당 요소 수, 토큰 수, 요소 수, 이미지 수 등이 포함되어 있습니다.  특히, 고유 URL 수, 평균 경로 길이, 평균 이미지당 요소 수, 토큰 수, 요소 수, 이미지 수는 성공적인 경로에 대한 통계임을 명시하여, 실패한 경로는 제외되었음을 알 수 있습니다.  이를 통해 데이터셋의 규모, 다양성, 그리고 복잡도를 더욱 명확하게 이해할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Dataset statistics for Explorer. The number of unique URLs, average steps per trajectory, average elements per image, and number of tokens, elements, and images correspond to the successful trajectories.
> </details>

{{< table-caption >}}
| Model | Cost per trajectory |
|---|---| 
| Mind2Web <cite class="ltx_cite ltx_citemacro_cite">Deng et al. (<a class="ltx_ref" href="https://arxiv.org/html/2502.11357v1#bib.bib9" title="">2023</a>)</cite> | $0.85 |
| AgentTrek <cite class="ltx_cite ltx_citemacro_cite">Xu et al. (<a class="ltx_ref" href="https://arxiv.org/html/2502.11357v1#bib.bib44" title="">2024a</a>)</cite> | $0.55 |
| **Explorer** | $0.28 |{{< /table-caption >}}
> 🔼 본 표는 기존의 웹 경로 생성 방식들과 Explorer의 비용을 비교하여 보여줍니다.  Explorer는 기존 방식들보다 훨씬 저렴한 비용으로 다양하고 방대한 웹 경로 데이터셋을 생성할 수 있음을 보여주는 표입니다.  세 가지 모델(Mind2Web, AgentTrek, Explorer)의 경로 생성에 드는 비용을 비교하며, Explorer의 비용 효율성을 강조하고 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Cost comparison with other trajectory generation approaches.
> </details>

{{< table-caption >}}
| Model | Avg. Step SR (%) | Completion Rate (%) | Task SR (1) (%) | Full Task SR (%) |
|---|---|---|---|---|
| **API-based Models** |  |  |  |  |
| GPT-4o | 58.5 | 52.8 | 44.6 | 25.3 |
| GPT-3.5 | – | 36.5 | – | 15.4 |
| **Open-source Instructed Models** |  |  |  |  |
| Mistral-7B-Instr.-0.3 [Jiang et al. (2023)] | 32.8 | 29.5 | 24.1 | 9.6 |
| Qwen2-72B-Instruct [Bai et al. (2023)] | – | 40.9 | – | 15.4 |
| Qwen2-VL-7B [Wang et al. (2024a)] | 40.2 | 35.4 | 34.9 | 14.5 |
| Phi-3.5V [Abdin et al. (2024)] | 28.5 | 23.5 | 20.5 | 2.4 |
| **Supervised Fine-Tuning** |  |  |  |  |
| **Explorer-4B** | 44.0 | 39.4 | 31.3 | 18.1 |
| **Explorer-7B** | 45.3 | 40.2 | 34.9 | 19.3 |{{< /table-caption >}}
> 🔼 표 6는 Mind2Web-Live 벤치마크에 대한 결과를 보여줍니다.  결과는 평균 단계 성공률, 완료율, 작업 성공률(Task SR), 전체 작업 성공률(Full Task SR)로 나타냅니다. 누락된 값은 -로 표시됩니다. GPT-4와 Mistral-7B에 대한 결과는 Linux 서버에서 재현되었고, GPT-3.5와 Qwen2-72B-Instruct에 대한 결과는 Pan et al.(2024b)에서 가져왔습니다. 전체 작업 성공률은 주어진 작업에 대한 모든 주요 노드의 성공적인 완료를 나타내며, 평균 단계 성공률은 작업 전반에 걸쳐 완료된 주요 노드의 비율을 나타내고, 완료율은 작업 전반에 걸쳐 완료된 주요 노드의 비율을 나타냅니다. 작업 성공률(1)은 최대 하나의 오류/주요 노드를 허용하는 작업 성공률을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Results on Mind2Web-Live benchmark. Missing values are denoted by –. The results for GPT-4 and Mistral-7B have been reproduced on our Linux servers. The results for GPT-3.5 and Qwen2-72B-Instruct have been taken from Pan et al. (2024b). The full task success rate represents the successful completion of all key nodes for a given task. The average step success rate represents the proportion of completed key nodes, macro-averaged across tasks. The completion rate represents the proportion of completed key nodes, micro-averaged across tasks. Task SR (1) represents task SR with a tolerance of up to one error/key node.
> </details>

{{< table-caption >}}
| Task SR (1) (%) |
|---|---|{{< /table-caption >}}
> 🔼 표 7은 본 논문에서 제안하는 Explorer 모델을 미세 조정하여 얻은 결과를 보여줍니다. 미세 조정된 Explorer 모델은 사전 훈련된 모델보다 성능이 크게 향상되었으며, GPT-4o를 포함한 클로즈드소스 대규모 언어 모델(LLM)보다도 우수한 성능을 보였습니다. 이는 Explorer 모델의 성능이 데이터의 품질과 다양성에 크게 의존함을 시사합니다. 표에는 모델 이름, 사전 훈련된 모델, 미세 조정된 모델, 그리고 각 모델의 성능 지표가 포함되어 있습니다. 각 모델의 성능은 정확도, F1 점수, 단계별 성공률 등으로 측정됩니다.
> <details>
> <summary>read the caption</summary>
> Table 7: In-domain evaluation results. The fine-tuned Explorer models achieve significant improvements over their pre-trained counterparts and surpass closed-source LLMs, including GPT-4o.
> </details>

{{< table-caption >}}
| Model | Full Task SR (%) |
|---|---| 
| GPT-4o | 16.0 |
| Phi-3.5V | 1.0 |
| **Explorer-4B** | 17.0 |
| Qwen2-VL-7B | 6.0 |
| **Explorer-7B** | 18.0 |{{< /table-caption >}}
> 🔼 표 8은 MiniWob++ 벤치마크(Liu et al., 2018)의 제로샷 평가 설정에서의 결과를 보여줍니다.  Ou et al.(2024)의 기준선 수치와 비교하여 Explorer 모델의 성능이 훨씬 뛰어남을 보여줍니다.  특히, 훨씬 더 큰 모델들보다 상당한 차이로 성능이 우수함을 알 수 있습니다.  이는 Explorer 모델이 제한된 매개변수를 가지고도 우수한 성능을 달성할 수 있음을 시사합니다.  또한, 제로샷 평가는 사전 훈련된 모델의 일반화 능력을 평가하는 데 효과적인 방법임을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Results on MiniWob++ benchmark Liu et al. (2018) in zero-shot evaluation setting. The baseline numbers correspond to Ou et al. (2024). Explorer outperforms much larger models by a significant margin.
> </details>

{{< table-caption >}}
| Model | Accuracy (%) |
|---|---| 
| _API-based Models_ |  | 
| GPT-3.5 | 39.57 | 
| GPT-4 | 53.04 | 
| _Open-source Instructed Models_ |  | 
| Phi-3.5V | 35.87 | 
| Qwen2-VL-7B | 36.96 | 
| Llama3-chat-8B | 31.74 | 
| Llama3-chat-70B | 48.70 | 
| _Open-source Interactive Data Finetuned Models_ |  | 
| AgentLM-7B [Zeng et al. (2024)](https://arxiv.org/html/2502.11357v1#bib.bib51) | 15.65 | 
| CodeActAgent-7B [Wang et al. (2024b)](https://arxiv.org/html/2502.11357v1#bib.bib40) | 9.78 | 
| AgentFlan-7B [Chen et al. (2024c)](https://arxiv.org/html/2502.11357v1#bib.bib7) | 20.87 | 
| Lemur-chat-70B [Xu et al. (2024b)](https://arxiv.org/html/2502.11357v1#bib.bib45) | 21.30 | 
| AgentLM-70B [Zeng et al. (2024)](https://arxiv.org/html/2502.11357v1#bib.bib51) | 36.52 | 
| Synatra-CodeLlama-7B [Ou et al. (2024)](https://arxiv.org/html/2502.11357v1#bib.bib29) | 38.20 | 
| AgentTrek-7B [Xu et al. (2024a)](https://arxiv.org/html/2502.11357v1#bib.bib44) | 45.28 | 
| **Explorer-4B** | 46.74 | 
| **Explorer-7B** | 53.26 |{{< /table-caption >}}
> 🔼 표 9는 Multimodal-Mind2Web 벤치마크에 대한 실험 결과를 보여줍니다.  Explorer 모델의 성능을 기존의 GUI 에이전트 기법들과 비교 분석하여, Explorer가 다른 모델들에 비해 상당히 우수한 성능을 보임을 확인할 수 있습니다.  표에는 다양한 지표(평균 단계 성공률, 완료율, 작업 성공률 등)가 포함되어 있으며, 세 개의 테스트 분할에 대한 평균 단계 성공률도 제시되어 있습니다.  기존 모델들의 결과는 Zheng et al. (2024), Cheng et al. (2024), Chen et al. (2024b,a), Shen et al. (2024) 의 연구에서 가져왔습니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Multimodal-Mind2Web evaluation results. The baseline numbers have been taken from Zheng et al. (2024); Cheng et al. (2024); Chen et al. (2024b, a); Shen et al. (2024). The last column denotes the average step success rates over the three test splits. Explorer significantly outperforms existing GUI agent baselines.
> </details>

{{< table-caption >}}
Model|Train Data|Cross-Task Ele. Acc|Cross-Task Op. F1|Cross-Task Step SR|Cross-Website Ele. Acc|Cross-Website Op. F1|Cross-Website Step SR|Cross-Domain Ele. Acc|Cross-Domain Op. F1|Cross-Domain Step SR|Avg.|In-Context Learning|GPT-3.5||19.4|59.2|16.8|14.9|56.5|14.1|25.2|57.9|24.1|18.3|GPT-4||40.8|63.1|32.3|30.2|61.0|27.0|35.4|61.9|29.7|29.7|SeeAct [Zheng et al. (2024)]|||46.4|73.4|40.2|38|67.8|32.4|42.4|69.3|36.8|36.5|Supervised Fine-Tuning|SeeClick-9.6B|Syn. + M2W|26.3|86.2|23.7|21.9|82.9|18.8|22.1|84.1|20.2|20.9|EDGE-9.6B|Syn. + M2W|–|–|–|30.0|–|–|21.1|–|–|22.4|24.5|MiniCPM-GUI-3.1B|Syn. + M2W|23.8|86.8|20.8|20.3|81.7|17.3|17.9|74.5|14.6|17.6|Scribe-Agent-L.-32B|Syn. traj.|38.0|52.9|35.6|34.1|52.7|32.5|39.4|54.7|37.3|35.1|AgentTrek-7B|Syn. + M2W|60.8|88.9|55.7|57.6|88.1|51.4|56.0|87.5|52.6|53.2|Explorer-4B|Syn. traj.|36.5|82.9|33.2|44.1|87.7|39.3|42.5|86.3|39.8|37.4|Explorer-4B|M2W|48.1|88.0|44.8|49.1|87.2|45.0|46.9|87.7|44.6|44.8|Explorer-4B|Syn. + M2W|53.4|88.1|50.7|55.6|89.5|51.4|49.8|88.8|47.2|49.8|Explorer-7B|Syn. traj.|43.6|86.6|39.6|48.7|87.7|44.5|47.6|87.2|44.7|43.0|Explorer-7B|M2W|51.8|88.0|48.3|56.3|89.7|52.0|50.9|88.9|48.1|49.5|Explorer-7B|Syn. + M2W|56.5|90.3|53.2|60.5|90.7|56.7|55.7|90.4|53.0|54.3{{< /table-caption >}}
> 🔼 표 10은 Mind2Web-Live 벤치마크에서 미세 조정에 사용된 언어 모델에 대한 ablation 연구 결과를 보여줍니다.  다양한 언어 모델의 성능을 비교하여,  시각적 모달의 중요성과 모델 성능에 미치는 영향을 분석합니다.  구체적으로는,  텍스트 모달만 사용한 경우와 시각적 모달을 함께 사용한 경우의 성능 차이를 보여주고,  다양한 용량의 사전 훈련된 모델을 비교하여 최적의 모델 선택을 위한 근거를 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Ablation studies on language models used for fine-tuning (Mind2Web-Live).
> </details>

{{< table-caption >}}
| Model | Avg. Step SR (%) | Completion Rate (%) | Full Task SR (%) |
|---|---|---|---|
| LLaVA-Mistral-7B | 32.0 | 30.3 | 4.8 |
| Phi-3-mini (text-only) | 36.6 | 34.0 | 13.3 |
| Phi-3.5V | 44.0 | 39.4 | 18.1 |
| Qwen2-VL-7B | 45.3 | 40.2 | 19.3 |{{< /table-caption >}}
> 🔼 표 A.1은 Mind2Web-Live 벤치마크에 대한 결과를 보여줍니다. GPT-4, GPT-3.5, Mistral-7B에 대한 결과는 Linux 서버에서 재현되었습니다. 전체 작업 성공률(SR)은 주어진 작업에 대한 모든 주요 노드의 성공적인 완료를 나타냅니다. 평균 단계 성공률은 작업 전반에 걸쳐 완료된 주요 노드의 비율을 나타내며, 작업별로 매크로 평균을 낸 것입니다. 완료율은 작업 전반에 걸쳐 완료된 주요 노드의 비율을 나타내며, 작업별로 마이크로 평균을 낸 것입니다. Task SR(1)은 최대 하나의 오류/주요 노드를 허용하는 Task SR을 나타냅니다. Explorer의 합성 궤적 데이터로 미세 조정된 저희의 Phi-3.5V 모델은 Mistral-7B 및 Qwen2-72B-Instruct를 포함한 훨씬 더 큰 모델들을 상당한 차이로 능가하며, GPT-3.5와 비슷한 성능을 보입니다.
> <details>
> <summary>read the caption</summary>
> Table A.1: Results on Mind2Web-Live benchmark. The results for GPT-4, GPT-3.5, and Mistral-7B have been reproduced on our Linux servers. The full task success rate (SR) represents the successful completion of all key nodes for a given task. The average step success rate represents the proportion of completed key nodes, macro-averaged across tasks. The completion rate represents the proportion of completed key nodes, micro-averaged across tasks. Task SR (1) represents task SR with a tolerance of up to one error/key node. Our Phi-3.5V model, finetuned on synthetic trajectory data from Explorer, outperforms much larger models, including Mistral-7B and Qwen2-72B-Instruct, by a significant margin and is comparable to GPT-3.5.
> </details>

{{< table-caption >}}
| Model | Avg. Step SR (%) | Completion Rate (%) | Task SR (1) (%) | Full Task SR (%) |
|---|---|---|---|---|
| **API-based Models** |  |  |  |  |
| GPT-4o | 56.4 | 50.4 | 44.2 | 22.1 |
| GPT-3.5 | – | 36.5 | – | 15.4 |
| **Open-source Instructed Models** |  |  |  |  |
| Mistral-7B-Instruct-0.3 [Jiang et al. (2023)] | 33.0 | 28.6 | 25.0 | 11.5 |
| Qwen2-72B-Instruct [Bai et al. (2023)] | – | 40.9 | – | 15.4 |
| Qwen2-VL-7B [Wang et al. (2024a)] | 37.9 | 33.3 | 31.7 | 12.5 |
| Phi-3.5V [Abdin et al. (2024)] | 27.0 | 22.3 | 21.2 | 1.9 |
| **Supervised Fine-Tuning** |  |  |  |  |
| **Explorer-4B** | 41.6 | 36.7 | 30.8 | 16.4 |
| **Explorer-7B** | 42.0 | 36.9 | 32.7 | 16.4 |{{< /table-caption >}}
> 🔼 표 A.2는 본 논문의 실험에서 사용된 하이퍼파라미터들을 보여줍니다.  구체적으로, Mind2Web-Live와 Multimodal-Mind2Web 두 가지 벤치마크에 대한 실험에 사용된 모델(Qwen2-VL-7B, Phi-3.5V), 학습 데이터(합성 데이터, Mind2Web 데이터, 합성 데이터 + Mind2Web 데이터), 그리고 배치 크기, 에폭, 학습률 등의 하이퍼파라미터 설정값들을 상세히 제시합니다. 이 표는 실험 결과의 재현성을 확보하고, 다른 연구자들이 본 논문의 실험 설정을 이해하고 재현하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table A.2: Hyperparameters used in our experiments.
> </details>

{{< table-caption >}}
| Task SR (1) (%) |
|---|---|{{< /table-caption >}}
> 🔼 표 B.3는 웹 에이전트 경로 생성 파이프라인의 각 모듈별 비용을 세부적으로 보여줍니다.  비용은 GPT-4-turbo 모델의 토큰당 비용, 이미지당 비용 등을 고려하여 계산됩니다.  총 비용은 단계별 비용을 합산하여 계산되며, 성공적인 경로 생성에 대한 평균 비용도 제시됩니다. 이 표를 통해 웹 에이전트 경로 데이터셋 생성에 드는 비용을 효율적으로 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table B.3: Cost breakdown for different modules in the pipeline.
> </details>

{{< table-caption >}}
| Dataset | Model | Train Data | Hyperparamerters | Train time (hours) |
|---|---|---|---|---|
| M2W-Live | Qwen2-VL-7B | Syn. | batch_size: 64, epoch: 2, learning_rate: 1e-05 | 15 |
| M2W-Live | Qwen2-VL-7B | M2W | batch_size: 64, epoch: 2, learning_rate: 1e-05 | 1.5 |
| M2W-Live | Qwen2-VL-7B | Syn. + M2W | batch_size: 64, epoch: 2, learning_rate: 1e-05 | 15.5 |
| M2W-Live | Phi-3.5V | Syn. | batch_size: 64, epoch: 2, learning_rate: 4e-05 | 12.5 |
| M2W-Live | Phi-3.5V | M2W | batch_size: 64, epoch: 2, learning_rate: 1e-05 | 1 |
| M2W-Live | Phi-3.5V | Syn. + M2W | batch_size: 64, epoch: 2, learning_rate: 4e-05 | 12.5 |
| Multi.-M2W | Qwen2-VL-7B | Syn. | batch_size: 64, epoch: 10, learning_rate: 4e-05 | 17 |
| Multi.-M2W | Phi-3.5V | Syn. | batch_size: 64, epoch: 10, learning_rate: 4e-05 | 12 |{{< /table-caption >}}
> 🔼 표 D.5는 논문의 부록 D절에 있는, Task Proposer Agent(작업 제안 에이전트)를 위한 프롬프트(지시 사항)를 보여주는 표입니다.  이 에이전트는 웹사이트의 스크린샷과 접근성 트리를 분석하여 사용자가 해당 웹사이트에서 수행할 수 있는 다양한 작업들을 제안하고, 해당 작업을 시작하기 위한 첫 번째 행동을 제시하는 역할을 합니다.  프롬프트는 에이전트가 작업을 생성하고, 자연어로 된 행동과 접지된(grounded) 행동을 생성하는 방법에 대한 세부적인 지침을 담고 있습니다.  결과적으로, 이 표는 웹 에이전트가 사용자의 작업 의도를 파악하고 웹 페이지를 탐색하는 과정을 이해하는 데 매우 중요한 정보를 담고 있습니다.
> <details>
> <summary>read the caption</summary>
> Table D.5: Prompt for Task Proposer Agent.
> </details>

{{< table-caption >}}
| Phase | Cost per step | Total cost |
|---|---|---|
| Proposal | $0.0128 | $0.0128 |
| Refinement | $0.0128 | $0.0856 |
| Verification | $0.02381 | $0.02381 |
| Summarization | $0.02581 | $0.02581 |{{< /table-caption >}}
> 🔼 표 D.7은 논문의 부록 D절에 있는 '프롬프트 세부 정보' 섹션에 속하며, 작업 개선 에이전트를 위한 프롬프트를 보여줍니다. 이 프롬프트는 웹 에이전트가 이전 단계에서 수행한 작업 목록과 현재 웹페이지의 스크린샷 및 구문 분석된 HTML/접근성 트리를 기반으로 사용자의 다음 작업을 예측하도록 안내합니다.  에이전트는 자연어 형식의 작업과 접지된 작업을 생성해야 하며, 특정 규칙과 제약 조건을 따라야 합니다.  다음 작업을 생성하는 규칙은 단일 원자 작업 생성, 주어진 어휘 집합 사용, 각 작업의 인수를 대괄호 안에 넣기, 작업의 자연어 형식과 접지된 형식의 일관성 유지, 특정 유형의 작업에 대한 특정 규칙 준수, 웹 페이지 변경 없이 동일한 작업을 반복하지 않기 등이 있습니다.  작업 제안 규칙은 웹사이트와 관련된 작업 생성, 로그인을 요구하지 않는 작업 생성, 명확하고 구체적인 작업 생성, 작업 설명에 구체적인 정보 제공, 실제 사용자가 작업을 완료하는 데 필요한 모든 정보를 포함, 실현 가능한 작업 생성 등이 있습니다.
> <details>
> <summary>read the caption</summary>
> Table D.7: Prompt for Task Refiner Agent.
> </details>

{{< table-caption >}}
| System Role | User Role |
|---|---| 
| **System Role** | What does this webpage show? Imagine you are a real user on this webpage. Given the webpage screenshot and parsed HTML/accessibility tree, please provide a single task that a user might perform on this page and the corresponding first action towards completing that task. |
|  | <br> **Do the following step by step**: <br> 1. Generate a single task that a user might perform on this webpage. Be creative and come up with diverse tasks <br> 2. Given the webpage screenshot and parsed HTML/accessibility tree, generate the first action towards completing that task (in natural language form). <br> 3. Given the webpage screenshot, parsed HTML/accessibility tree, and the natural language action, generate the grounded version of that action. <br> **ACTION SPACE**: Your action space is: [`click [element ID]`, `type [element ID] [content]`, `select [element ID] [content of option to select]`, `scroll [up]`, `scroll [down]`, and `stop`]. <br> **Action output should follow the syntax as given below**: <br> `click [element ID]`: This action clicks on an element with a specific ID on the webpage. <br> `type [element ID] [content]`: Use this to type the content into the field with id. By default, the "Enter" key is pressed after typing. Both the content and the ID should be within square braces as per the syntax. <br> `select [element ID] [content of option to select]`: Select an option from a dropdown menu. The content of the option to select should be within square braces. When you get (select an option) tags from the accessibility tree, you need to select the serial number (element_id) corresponding to the select tag, not the option, and select the most likely content corresponding to the option as input. <br> `scroll [down]`: Scroll the page down. <br> `scroll [up]`: Scroll the page up. <br> **IMPORTANT**: To be successful, it is important to STRICTLY follow the below rules: <br> **Action generation rules**: <br> 1. You should generate a single atomic action at each step. <br> 2. The action should be an atomic action from the given vocabulary - click, type, select, scroll (up or down), or stop. <br> 3. The arguments to each action should be within square braces. For example, "click [127]", "type [43] [content to type]", "scroll [up]", "scroll [down]". <br> 4. The natural language form of action (corresponding to the field "action_in_natural_language") should be consistent with the grounded version of the action (corresponding to the field "grounded _action"). Do NOT add any additional information in the grounded action. For example, if a particular element ID is specified in the grounded action, a description of that element must be present in the natural language action. <br> 5. If the type action is selected, the natural language form of action ("action_in_natural_language") should always specify the actual text to be typed. <br> 6. You should issue a “stop” action if the current webpage asks to log in or for credit card information. <br> 7. To input text, there is NO need to click the textbox first, directly type content. After typing, the system automatically hits the ‘ENTER’ key. <br> 8. STRICTLY Avoid repeating the same action (click/type) if the webpage remains unchanged. You may have selected the wrong web element. <br> 9. Do NOT use quotation marks in the action generation. <br> **Task proposal rules**: <br> 1. You should propose tasks that are relevant to the website and can be completed using the website. <br> 2. You should only propose tasks that do not require login to execute the task. <br> 3. You should propose tasks that are clear and specific. <br> 4. For each task, provide concrete information or constraints, and use mock-up information (identifier, number, personal information, name, attributes, etc.) to make the task more specific and realistic. <br> 5. The task description should provide all the necessary information to complete the task. <br> 6. The task should be feasible to complete by a real user and should not require any additional information that is not available on the website. <br> **The output should be in below format**: <br> **OUTPUT FORMAT**: Please give a short analysis of the screenshot, parsed HTML/accessibility tree, then put your answer within ```  ```, for example, "In summary, the proposed task and the corresponding action is: ```<span class="ltx_text ltx_font_typewriter" id="A4.T4.1.32.2.1.1.2">{"task": &lt;TASK&gt;:str, "action_in_natural_language":&lt;ACTION_IN_NATURAL_LANGUAGE&gt;:str, "grounded_action": &lt;ACTION&gt;:str}</span>``` |
| **User Role** | Website URL: {INIT_URL}<br>Parsed HTML/Accessibility Tree: {A11Y_TREE}<br>{SCREENSHOT} |
{{< /table-caption >}}
> 🔼 표 D.8은 논문의 부록 D절에 있는, 작업 요약 에이전트를 위한 프롬프트를 보여주는 표입니다. 이 표는 웹 페이지에서 수행된 일련의 작업과 해당 스크린샷을 입력으로 받아 이 작업들을 수행하여 완료할 수 있는 하나의 작업 설명을 생성하는 작업 요약 에이전트의 프롬프트를 상세히 설명합니다. 프롬프트는 에이전트가 작업을 생성하기 위한 지침, 작업 설명 형식, 그리고 중요한 규칙들 (예: 거래/정보 검색 포함, 명확하고 구체적일 것, 추가 정보 없이 실행 가능할 것 등)을 포함하고 있습니다.
> <details>
> <summary>read the caption</summary>
> Table D.8: Prompt for Task Summarizer Agent.
> </details>

{{< table-caption >}}
| System Role | User Role |
|---|---| 
| **System Role** | What does this webpage show? Imagine you are a real user on this webpage, and your overall task is {OVERALL_TASK}. This is the list of actions you have performed that lead to the current page {PREV_ACTION_LIST}. You are also given the webpage screenshot and parsed HTML/accessibility tree. | 
|  |  <span class="ltx_text ltx_framed ltx_framed_underline">Do the following step by step</span>: | 
|  | 1. Please predict what action the user might perform next that is consistent with the previous action list in natural language. | 
|  | 2. Then based on the parsed HTML/accessibility tree of the webpage and the natural language action, generate the grounded action. | 
|  | 3. Update the overall task aligned with this set of actions. | 
|  | **ACTION SPACE**: Your action space is: [‘click [element ID]’, ‘type [element ID] [content]’, ‘select [element ID] [content of option to select]’, ‘scroll [up]’, ‘scroll [down]’, and ‘stop’]. | 
|  | <span class="ltx_text ltx_framed ltx_framed_underline">Action output should follow the syntax as given below</span>: | 
|  | ‘click [element ID]’: This action clicks on an element with a specific id on the webpage. | 
|  | ‘type [element ID] [content]’: Use this to type the content into the field with id. By default, the "Enter" key is pressed after typing. Both the content and the id should be within square braces as per the syntax. | 
|  | ‘select [element ID] [content of option to select]’: Select an option from a dropdown menu. The content of the option to select should be within square braces. When you get (select an option) tags from the accessibility tree, you need to select the serial number (element_id) corresponding to the select tag, not the option, and select the most likely content corresponding to the option as input. | 
|  | ‘scroll [down]’: Scroll the page down. | 
|  | ‘scroll [up]’: Scroll the page up. | 
|  | **IMPORTANT**: To be successful, it is important to STRICTLY follow the below rules: | 
|  | **Action generation rules**: | 
|  | 1. You should generate a single atomic action at each step. | 
|  | 2. The action should be an atomic action from the given vocabulary - click, type, select, scroll (up or down), or stop | 
|  | 3. The arguments to each action should be within square braces. For example, "click [127]", "type [43] [content to type]", "scroll [up]", "scroll [down]". | 
|  | 4. The natural language form of action (corresponding to the field "action_in_natural_language") should be consistent with the grounded version of the action (corresponding to the field "grounded _action"). Do NOT add any additional information in the grounded action. For example, if a particular element ID is specified in the grounded action, a description of that element must be present in the natural language action. | 
|  | 5. If the type action is selected, the natural language form of action ("action_in_natural_language") should always specify the actual text to be typed. | 
|  | 6. You should issue the “stop” action when the given list of input actions is sufficient for a web task. | 
|  | 7. You should issue a “stop” action if the current webpage asks to log in or for credit card information. | 
|  | 8. To input text, there is NO need to click the textbox first, directly type content. After typing, the system automatically hits the ‘ENTER‘ key. | 
|  | 9. STRICTLY Avoid repeating the same action (click/type) if the webpage remains unchanged. You may have selected the wrong web element. | 
|  | 10. Do NOT use quotation marks in the action generation. | 
|  | **Task proposal rules**: | 
|  | 1. You should propose tasks that are relevant to the website and can be completed using the website itself. | 
|  | 2. The overall task should be well-aligned to the entire set of actions in history plus the current generated action. It should not be focused just on the current action. | 
|  | 3. You should only propose tasks that do not require login to execute the task. | 
|  | 4. You should propose tasks that are clear and specific. | 
|  | 5. For each task, provide concrete information or constraints, and use mock-up information (identifier, number, personal information, name, attributes, etc.) to make the task more specific and realistic. | 
|  | 6. The task description should provide all the necessary information to complete the task. | 
|  | 7. The task should be feasible to complete by a real user and should not require any additional information that is not available on the website. | 
|  | <span class="ltx_text ltx_framed ltx_framed_underline">The output should be in below format</span>: | 
|  | **OUTPUT FORMAT**: Please give a short analysis of the screenshot, parsed HTML/accessibility tree, and history, then put your answer within ```  ```, for example, "In summary, the proposed task and the corresponding action is: ```<span class="ltx_text ltx_font_typewriter">{"task": <TASK>:str, "action_in_natural_language":<ACTION_IN_NATURAL_LANGUAGE>:str, "grounded_action": <ACTION>:str}</span>``` | 
| **User Role** | Website URL: {INIT_URL} | 
|  | Parsed HTML/Accessibility Tree: {A11Y_TREE} | 
|  | {SCREENSHOT} | {{< /table-caption >}}
> 🔼 표 D.9는 웹 페이지 탐색 에이전트의 성능을 평가하는 전문가를 위한 프롬프트를 보여줍니다.  Pan 등(2024a)의 작업을 바탕으로 합니다. 이 프롬프트는 사용자 의도, 에이전트의 작업 이력, 웹 페이지의 최종 상태, 사용자에 대한 에이전트의 응답을 제공하여 에이전트의 실행 성공 여부를 판단하는 데 사용됩니다.  프롬프트는 거래, 정보 검색, 사이트 탐색, 콘텐츠 수정 등 네 가지 작업 유형을 설명하며, 각 유형에 대한 성공 및 실패 조건을 자세히 설명합니다. 성공적인 작업 수행에 대한 기준이 명확하게 제시되어 있으며, 에이전트의 응답과 상관없이 웹 페이지의 최종 상태를 중심으로 평가가 이루어집니다.  또한, 에이전트가 장바구니에 상품을 추가하거나 결제 페이지를 표시하는 등의 작업을 완료한 경우 성공적인 실행으로 간주되는 예외적인 상황도 명시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table D.9: Prompt for Task Verifier Agent (adapted from Pan et al. (2024a)).
> </details>

{{< table-caption >}}
| System Role | Description |
|---|---| 
| **System Role** | Given a list of actions performed on the website {WEBSITE_URL} and the corresponding screenshots |
|  | List of actions: {ACTION_LIST} |
|  | Your task is to come up with a single task description that will be accomplished by performing these actions in the given sequence on the website. |
|  | **IMPORTANT**: |
|  | 1. The task must contain some actions: “Buy, Book, Find, Check, Choose, show me, search, browse, get, compare, view, give me, add to cart, …”, ideally involving transactions/finding information on a specific product or service. |
|  | 2. You should propose tasks that are clear and specific. |
|  | 3. The task description should provide all the necessary information to complete the task. |
|  | 4. The task description must indicate the domain of the website at the end of the task with the format: “… on task website”, for instance, “Purchase a laptop on Amazon”, “Book a hair appointment on Yelp”, etc. |
|  | 5. The task should be feasible to complete by a real user and should not require any additional information that is not specified in this input. |
|  | 6. The task description should specify constraints like given budget, product features, and other specifications that can narrow down the search to a particular item/product. |
|  | 7. Do NOT use any quotation marks (either single or double) in the task description. |
|  | **OUTPUT FORMAT**: Please first give some analysis of the actions and screenshots and then output the overall task description. put your answer within ```  ```, for example, “In summary, the answer is: ```<span class="ltx_text ltx_font_typewriter">&lt;TASK_DESCRIPTION&gt;:str</span>```”. |{{< /table-caption >}}
> 🔼 표 D.10은 웹 에이전트 훈련을 위한 프롬프트를 보여줍니다.  이 표는 웹 페이지의 스크린샷과 접근성 트리(Accessibility Tree)를 사용하여 웹 에이전트가 웹 페이지와 상호 작용하는 방법을 설명하는 지시 사항(프롬프트)을 제공합니다.  프롬프트는 에이전트가 웹 페이지의 이미지를 해석하고,  수행할 작업을 결정하고, 그에 따른 적절한 행동(액션)을 선택하는 방법을 안내합니다. 또한,  액션의 자연어 표현(action_natural_language)과 그에 해당하는 접근성 트리 상의 요소 식별자(element_idx) 등을 포함하여 에이전트의 출력 형식을 명확하게 지정합니다.  이러한 프롬프트를 통해 웹 에이전트는 다양한 웹 환경에서 사용자의 지시에 따라 효과적으로 작업을 수행하도록 학습될 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table D.10: Prompt for Web Agent Training.
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