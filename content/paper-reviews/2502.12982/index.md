---
title: "Sailor2: Sailing in South-East Asia with Inclusive Multilingual LLMs"
summary: "Sailor2: 동남아시아 지역의 다양한 언어를 지원하는 최첨단 다국어 LLM 공개!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Aalborg University",]
showSummary: true
date: 2025-02-18
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.12982 {{< /keyword >}}
{{< keyword icon="writer" >}} Longxu Dou et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-18 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.12982" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.12982" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

동남아시아(SEA) 지역은 언어적 다양성이 풍부하지만, 주요 언어에 비해 **자원이 부족한 언어**가 많아 LLM 개발이 어려움을 겪고 있습니다. 기존의 다국어 LLM들은 주요 언어에 치우쳐 SEA 지역 언어에 대한 지원이 부족하고, 성능 또한 낮은 편입니다.  이러한 문제를 해결하기 위해, Sailor2 프로젝트는 **다양한 크기(1B, 8B, 20B)**의 다국어 LLM과  **데이터 정제, 사전 훈련, 후속 훈련, 모델 사용자 지정, 평가** 등의 전 과정에 대한 로드맵을 제공합니다. 



Sailor2는 **500B 토큰(400B SEA 특화, 100B 재사용)**을 사용하여 13개 SEA 언어와 영어, 중국어에 대한 숙련도를 유지하면서 훈련되었습니다.  **GPT-4와의 비교 평가**에서 SEA 언어에 대해 50% 승률을 기록하며 우수한 성능을 입증했습니다.  **Apache 2.0 라이선스** 하에 모델과 도구, 훈련 레시피를 모두 공개하여 연구자들이 보다 포괄적인 다국어 LLM을 개발하는 데 도움을 주고자 합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 동남아시아 지역 13개 언어를 지원하는 다국어 LLM Sailor2 공개 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} GPT-4를 능가하는 성능(50% 승률) 달성 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 다국어 LLM 개발을 위한 종합적인 로드맵(Cookbook) 제공 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **소외된 언어**에 대한 연구를 진행하는 연구자들에게 중요한 의미를 지닙니다. **다양한 언어 모델과 도구, 그리고 투명한 훈련 레시피**를 제공함으로써, 해당 분야의 연구를 가속화하고 보다 포괄적인 다국어 LLM 개발을 위한 새로운 방향을 제시합니다.  또한, **효율적인 다국어 모델 개발을 위한 로드맵**을 제공함으로써, 연구자들이 직면하는 어려움을 해결하고 연구 효율성을 높이는 데 기여합니다. 이러한 기여는 다국어 자연어 처리 분야의 발전에 중요한 영향을 미칠 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.12982/x2.png)

> 🔼 그림 1은 Sailor2-20B 모델이 데이터 정제 및 효율적인 모델 확장을 통해 동남아시아 언어에서 GPT-40와 50:50 승률을 달성했다는 것을 보여줍니다. 이는 오픈 소스 대규모 언어 모델의 새로운 이정표를 제시하는 결과입니다. 그림에는 데이터 정제 과정, 모델 확장 및 성능 평가 결과가 요약되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  With rigorous data curation and efficient model expansion, Sailor2-20B achieves the 50-50 win rate over GPT4o on SEA languages, marking a new milestone of open LLMs.
> </details>





{{< table-caption >}}
| Stage | Sailor2-1B | Sailor2-8B | Sailor2-20B |
|---|---|---|---|
| **Model Checkpoints** |  |  |  |
| Pre-Annealing | sail/Sailor2-1B-Pre | sail/Sailor2-8B-Pre | sail/Sailor2-20B-Pre |
| Base | sail/Sailor2-1B | sail/Sailor2-8B | sail/Sailor2-20B |
| SFT | sail/Sailor2-1B-SFT | sail/Sailor2-8B-SFT | sail/Sailor2-20B-SFT |
| Chat | sail/Sailor2-1B-Chat | sail/Sailor2-8B-Chat | sail/Sailor2-20B-Chat |{{< /table-caption >}}

> 🔼 이 표는 Apache 2.0 라이선스에 따라 Sailor2와 함께 공개된 모델, 리소스 및 코드에 대한 정보를 담고 있습니다. Sailor2-20B-Chat 데모 버전은 huggingface에서 확인할 수 있습니다. 표에는 Sailor2의 세 가지 크기(1B, 8B, 20B)에 대한 사전 학습, 미세 조정, 채팅 모델에 대한 정보가 포함되어 있으며, 데이터 정리, 혼합, 사전 학습, 후속 학습, 평가 데이터셋 등의 링크도 제공합니다.  모델 확장, 장기 컨텍스트 학습, 추측적 디코딩, 모델 가지치기 등의 다양한 기술을 사용하여 개발된 Sailor2 모델들의 체크포인트를 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Models, resource, and code released with Sailor2 under Apache 2.0 License.  Demo: https://huggingface.co/spaces/sail/Sailor2-20B-Chat
> </details>





### In-depth insights


#### SEA LLM Landscape
동남아시아(SEA)는 언어적으로나 문화적으로나 다양성이 풍부한 지역이기 때문에, **포괄적인 다국어 LLM 개발**은 상당한 과제입니다.  기존의 주요 언어에 집중된 LLM들이 SEA 지역의 다양한 언어와 문화적 뉘앙스를 충분히 반영하지 못하고 있음을 지적하며, **SEA 지역 특화 LLM의 필요성**을 강조합니다. 이는 단순히 다국어 지원을 넘어, 지역 특유의 어휘, 문법, 표현 방식, 문화적 배경 지식 등을 정확하게 이해하고 생성하는 능력을 의미합니다.  **데이터 부족**은 SEA LLM 개발의 주요 걸림돌 중 하나이며, 이를 극복하기 위한 다양한 방법 (예: 데이터 증강, 이중 언어 데이터 활용 등)이 모색되어야 합니다.  또한, **평가 기준** 또한 중요한데, 기존의 영어 중심 평가 기준 대신 SEA 언어와 문화적 맥락을 고려한 평가 방법이 필요합니다.  **개방형 모델과 자원 공유**를 통해 연구 발전을 가속화하고, **포괄적인 다국어 LLM 개발**을 위한 협력이 중요합니다.  결론적으로, SEA LLM Landscape는 기술적 난관과 기회가 공존하는 역동적인 영역으로, **지속적인 연구개발 및 협력**을 통해 다양한 언어와 문화를 가진 사용자들을 위한 보다 나은 서비스를 제공할 수 있을 것입니다.

#### Data-centric Approach
데이터 중심 접근 방식은 **데이터의 품질과 다양성**을 최우선으로 고려하는 연구 접근법입니다.  이는 단순히 최첨단 모델을 개발하는 것에 그치지 않고, **모델 성능 향상에 가장 중요한 요소인 데이터 자체에 집중**하는 것을 의미합니다.  **데이터 수집, 정제, 그리고 혼합 과정에 대한 엄격한 기준**을 설정하여, 노이즈를 최소화하고 모델의 편향을 줄이며, 다양한 언어와 문화를 포괄하는 풍부한 데이터셋을 구축하는 것이 중요합니다. 이러한 데이터 중심 접근 방식은 특히 저자원 언어 모델 개발에 있어 **데이터 부족 문제를 해결**하고 **모델의 일반화 능력을 향상**시키는데 효과적입니다.  **Sailor2 모델**의 경우, 6단계에 걸친 엄격한 데이터 정제 과정과 다양한 데이터 소스 활용을 통해 **데이터 품질 향상**을 도모하였으며, **균형 잡힌 데이터 혼합 전략**을 통해 저자원 언어에 대한 모델 성능을 높였습니다.  **데이터 중심 접근 방식**은 단순한 기술적 개선이 아닌, **포괄적이고 공정한 AI 모델 개발**이라는 더 큰 목표 달성에 기여합니다.

#### Two-stage Training
본 논문에서 제시된 **두 단계 학습 전략**은 언어 모델의 성능 향상에 있어 중요한 역할을 합니다. 첫 번째 단계에서는 **균형 잡힌 데이터 혼합**을 통해 다양한 언어에 대한 균등한 학습을 보장합니다. 이는 저자원 언어의 과소 대표 문제를 완화하고 모델의 견고성을 높이는 데 기여합니다. 두 번째 단계에서는 **고품질 토큰의 어닐링**을 통해 모델의 성능을 미세 조정합니다. 이를 통해 저자원 언어에 대한 성능을 향상시키면서 고자원 언어의 성능 저하를 방지합니다.  **두 단계의 균형 잡힌 접근 방식**은 모델의 전반적인 성능과 다양한 언어에 대한 적응력을 향상시키는 데 효과적임을 보여줍니다.  **학습률 조정 및 배치 크기 변화** 등의 추가적인 최적화 기법들이 사용되어 학습 효율을 높였습니다.  이러한 두 단계 학습 전략은 **다양한 언어 및 데이터 품질**을 고려한 효율적이고 균형 잡힌 언어 모델 학습을 가능하게 합니다.  이는 특히 저자원 언어 지원에 있어 **중요한 의미**를 지닙니다.

#### Model Customization
논문의 "모델 사용자 지정" 부분은 **대규모 언어 모델(LLM)의 기능을 특정 작업이나 도메인에 맞게 미세 조정하는 방법**을 다룹니다.  본 연구에서는 세 가지 주요 사용자 지정 기술, 즉 **장문 컨텍스트 학습, 예측적 디코딩, 모델 가지치기**를 자세히 설명합니다. 장문 컨텍스트 학습은 모델의 컨텍스트 창을 확장하여 더욱 긴 입력을 처리할 수 있도록 하며, 이는 **다큐먼트 질의응답이나 리포지토리 수준 코드 이해와 같은 복잡한 작업**에 유용합니다.  **AnchorAttention 기법**을 통해 이러한 장문 컨텍스트 기능을 효율적으로 구현합니다. 예측적 디코딩은 GliDe라는 경량화된 모델을 사용하여 자동 회귀 생성의 계산 비용을 줄여 추론 속도를 높입니다. 마지막으로, 모델 가지치기는 Sheared LLaMA 기법을 적용하여 대규모 모델을 효율적으로 축소합니다. 이는 **작은 규모의 모델을 빠르게 생성하고 리소스를 절약**하는 데 도움이 됩니다. 각 사용자 지정 기법에 대한 구현 세부 정보와 성능 평가 결과가 제시되어 있어, LLM을 실제 환경에 적용하는 데 유용한 지침을 제공합니다.  **특히, 다국어 지원에 중점을 둔 모델에 대한 사용자 지정 방법**이 상세히 다루어져 있어, **저자원 언어 모델 개발**에 큰 도움이 될 것으로 기대됩니다.

#### Future of SEA LLMs
동남아시아 언어를 위한 거대 언어 모델(LLM)의 미래는 **다양성과 포용성**을 중시하는 방향으로 나아갈 것입니다.  **데이터 부족 문제**를 해결하기 위해 **합성 데이터 생성 및 데이터 증강 기술**의 발전이 중요하며, 이는 다양한 언어와 문화적 맥락을 반영하는 고품질 데이터를 확보하는 데 기여할 것입니다.  또한, **모델 효율성 향상**을 위해 **지속적 사전 학습(CPT) 및 모델 경량화 기술** 연구가 필수적입니다.  **토큰화 없이 학습하는 모델** 및 **장기 문맥 이해를 위한 기술** 발전은 이러한 노력을 뒷받침할 것입니다.  마지막으로, **윤리적 고려사항**과 **지속 가능한 언어 발전**을 위한 노력이 동남아시아 LLM의 성공적인 미래를 위한 핵심 요소가 될 것입니다.  **오픈 소스 모델과 리소스 공유**는 이러한 목표를 달성하는데 매우 중요한 역할을 할 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.12982/x5.png)

> 🔼 그림 2는 Sailor2 모델 개발을 위한 종합적인 레시피를 보여주는 그림입니다. 데이터 준비, 모델 학습 및 평가의 세 가지 주요 단계를 포함합니다. 각 단계에는 Sailor2의 개발에서 얻은 주요 통찰력과 함께 다양한 기술 및 도구가 자세히 설명되어 있습니다. 예를 들어, 데이터 준비 단계는 다양한 데이터 소스, 노이즈 제거를 위한 필터링, 그리고 저자원 언어를 위한 데이터 보충과 같은 측면을 다룹니다. 모델 학습 단계는 모델 확장, 지속적 사전 훈련, 지시어 튜닝 및 기호 튜닝과 같은 기술을 보여줍니다. 마지막으로, 평가 단계는 SailCompass 및 SEA-WildBench와 같은 다양한 평가 지표와 도구에 대한 자세한 내용을 보여줍니다. 이 레시피는 연구자들이 다양한 저자원 언어를 포함한 포괄적인 대규모 언어 모델을 구축하는 데 도움이 되도록 고안되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 2:  Sailor2 Cookbook with key insights in data, model training and evaluation.
> </details>



![](https://arxiv.org/html/2502.12982/x8.png)

> 🔼 그림 3은 Sailor2 모델의 instruction tuning에 사용된 SEA-UltraChat 데이터셋의 카테고리 및 언어 분포를 보여줍니다.  Stage 1 데이터셋은 다양한 언어와 카테고리가 불균형적으로 분포되어 있으나,  Stage 2 데이터셋은 언어와 카테고리의 균형있는 분포를 위해 신중하게 큐레이션 되었습니다.  Stage 1과 Stage 2 데이터셋의 카테고리 분포 (코딩 및 디버깅, 정보 검색, 수학 및 데이터, 창의적 작업, 추론 및 계획) 와 14개 언어 (영어, 중국어, 태국어, 베트남어, 인도네시아어, 말레이어, 버마어, 라오어, 세부아노어, 일로카노어, 자바어, 크메르어, 순다어, 타갈로그어)의 비율을 비교하여 보여줍니다.  이를 통해 Stage 2 데이터셋이 언어와 카테고리 측면에서 보다 균형 잡힌 데이터를 제공함을 시각적으로 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Distribution of categories and languages in SEA-UltraChat. Stage 2 data is carefully curated to ensure a balanced representation across both dimensions.
> </details>



![](https://arxiv.org/html/2502.12982/x9.png)

> 🔼 그림 4는 영어로 된 창작 과제에 대한 지시 사항 데이터의 PPL 백분위수 대비 보상 백분위수 분포를 보여줍니다. 이 그림은 2단계 지시 사항 데이터로 사용할 후보군을 선택하는 데 사용된 방법을 보여줍니다.  높은 PPL과 높은 보상을 가진 후보군(오른쪽 상단)이 2단계 데이터로 선택됩니다. 표 6에는 노란색으로 강조 표시된 코너 케이스가 제시되어 있습니다. 이는 모델이 특정 유형의 데이터에 어려움을 겪거나 특정 유형의 응답을 생성하는 경향이 있음을 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: The PPL Percentile vs Reward Percentile distribution of English instruction data on Creative Tasks. We select High PPL High Reward candidates (top right) as stage 2 instruction data. We report corner cases highlighted in yellow in Table 6.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Codebases / Tools | Link |
|---|---| 
| **Type** | <img src="https://arxiv.org/html/2502.12982/x3.png" width="20" height="20"> **Link** |
| Data Cleaning | [sail-sg/sailcraft](https://www.github.com/sail-sg/sailcraft) |
| Data Mixture | [sail-sg/regmix](https://www.github.com/sail-sg/regmix) |
| Pre-training | [sail-sg/Megatron-Sailor2](https://www.github.com/sail-sg/Megatron-Sailor2) |
| Post-training | [sail-sg/oat](https://www.github.com/sail-sg/oat) |
| Evaluation | [sail-sg/sailcompass](https://www.github.com/sail-sg/sailcompass) |{{< /table-caption >}}
> 🔼 Sailor2 모델이 지원하는 13개의 동남아시아 언어 목록과 각 언어의 사용 인구수를 보여주는 표입니다.  표에는 각 언어의 ISO 코드, 국가/지역, 사용 인구수가 포함되어 있습니다. 이 표는 Sailor2 모델이 다양한 동남아시아 언어를 지원하도록 훈련되었음을 보여주는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Thirteen SEA Languages Supported by Sailor2.
> </details>

{{< table-caption >}}
| **Post-Training Dataset** |  | 
|---|---| 
| **Domain** | **Link** | 
| SFT-Stage1 | [sailor2/sailor2-sft-stage1](https://huggingface.co/datasets/sailor2/sailor2-sft-stage1) | 
| SFT-Stage2 | [sailor2/sailor2-sft-stage2](https://huggingface.co/datasets/sailor2/sailor2-sft-stage2) | 
| Off-policy DPO | [sailor2/sea-ultrafeedback](https://huggingface.co/datasets/sailor2/sea-ultrafeedback) | 
| On-policy DPO | [sailor2/sea-ultrafeedback-onpolicy](https://huggingface.co/datasets/sailor2/sea-ultrafeedback-onpolicy) | {{< /table-caption >}}
> 🔼 이 표는 Sailor2의 지속적인 사전 훈련에 사용된 원시 토큰의 통계를 보여줍니다. 언어, ISO 코드, 디스크 크기(TB), 추정 토큰 수(십억 단위)를 포함하여 13개의 동남아시아 언어에 대한 정보를 제공합니다. 이 표는 Sailor2 모델의 훈련에 사용된 데이터의 양과 분포를 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Statistics of Raw Tokens Used in Sailor2 Continual Pre-training.
> </details>

{{< table-caption >}}
| Domain | Link |
|---|---| 
| **Evaluation Dataset** |  | 
| SailCompass | [sail/Sailcompass_data](https://huggingface.co/datasets/sail/Sailcompass_data) |
| SEA-WildBench | [sailor2/sea-wildbench](https://huggingface.co/datasets/sailor2/sea-wildbench) |
{{< /table-caption >}}
> 🔼 표 4는 Sailor2 모델의 첫 번째 지속적 사전 훈련 단계에서 각 언어에 대해 실제로 사용된 토큰 수를 보여줍니다. 데이터 혼합 최적화 과정을 거쳐 언어별 토큰 분포가 조정되었으며, 베트남어와 인도네시아어는 다운샘플링되었고, 크메르어, 말레이어, 버마어, 태국어, 타갈로그어는 업샘플링되었습니다. 이 표는 Sailor2 모델의 훈련 데이터 균형을 맞추기 위한 데이터 혼합 전략을 이해하는 데 중요한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Effective Tokens by Language in Stage 1.
> </details>

{{< table-caption >}}
| **Stage** | **Sailor2-1B** | **Sailor2-8B** | **Sailor2-20B** |
|---|---|---|---|
| Base | [sail/Sailor2-L-1B](https://huggingface.co/sail/Sailor2-L-1B) | [sail/Sailor2-L-8B](https://huggingface.co/sail/Sailor2-L-8B) | [sail/Sailor2-L-20B](https://huggingface.co/sail/Sailor2-L-20B) |
| SFT | [sail/Sailor2-L-1B-SFT](https://huggingface.co/sail/Sailor2-L-1B-SFT) | [sail/Sailor2-L-8B-SFT](https://huggingface.co/sail/Sailor2-L-8B-SFT) | [sail/Sailor2-L-20B-SFT](https://huggingface.co/sail/Sailor2-L-20B-SFT) |
| Chat | [sail/Sailor2-L-1B-Chat](https://huggingface.co/sail/Sailor2-L-1B-Chat) | [sail/Sailor2-L-8B-Chat](https://huggingface.co/sail/Sailor2-L-8B-Chat) | [sail/Sailor2-L-20B-Chat](https://huggingface.co/sail/Sailor2-L-20B-Chat) |{{< /table-caption >}}
> 🔼 표 5는 Sailor2 모델의 두 번째 지속적 사전 훈련 단계에서 언어별로 사용된 실제 토큰 수를 보여줍니다. 이 단계에서는 고품질의 SEA 언어 토큰을 추가하고, 고품질의 영어 지시 튜닝 데이터셋과 Sailor2 커뮤니티가 제공하는 데이터셋을 포함하여 저자원 언어의 균형을 맞추는 데 중점을 둡니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Effective Tokens by Language in Stage 2.
> </details>

{{< table-caption >}}
| Model Checkpoints (via Speculative Decoding) |
|---|---|---|
| **Stage** | **Sailor2-8B** | **Sailor2-20B** |
| Base Model | [sail/Sailor2-8B-Chat-Glide](https://huggingface.co/sail/Sailor2-8B-Chat-Glide) | [sail/Sailor2-20B-Chat-Glide](https://huggingface.co/sail/Sailor2-20B-Chat-Glide) |{{< /table-caption >}}
> 🔼 표 6은 보상(Reward) 및 퍼플렉서티(PPL) 값을 사용하여 네 가지 사례를 분석한 결과를 보여줍니다. 각 사례는 사용자 질문과 어시스턴트 응답으로 구성되며, 보상 값은 응답의 품질을 나타내고, PPL 값은 응답의 예측 불가능성을 나타냅니다. 네 가지 사례를 통해 다양한 품질(높음, 낮음)과 예측 불가능성(높음, 낮음)을 가진 응답을 분석하고, 이를 사전 학습 데이터 구성에 활용하여 모델 성능을 향상시키는 방법에 대한 통찰력을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Analysis of Four Cases with Reward and PPL Values.
> </details>

{{< table-caption >}}
| **Stage** | **Sailor2-3B (Pruning via Sailor2-8B)** | **Sailor2-14B (Pruning via Sailor2-20B)** |
|---|---|---|
| Base Model | sail/Sailor2-3B | sail/Sailor2-14B |
| SFT | sail/Sailor2-3B-SFT | sail/Sailor2-14B-SFT |
| Chat | sail/Sailor2-3B-Chat | sail/Sailor2-14B-Chat |{{< /table-caption >}}
> 🔼 표 7은 강화 학습 기반 선호도 조정 알고리즘에 사용된 다양한 하이퍼파라미터를 보여줍니다.  본 논문에서는 DPO(Direct Preference Optimization) 및 SimPO, LN-DPO, LR-DPO와 같은 변형 알고리즘을 실험했습니다.  각 알고리즘에 대해 학습률(LR), 배치 크기, 그리고 알고리즘별 특정 하이퍼파라미터를 포함하여 다양한 하이퍼파라미터 조합을 탐색했습니다. 이 표는 실험에 사용된 하이퍼파라미터의 범위와 각 하이퍼파라미터가 모델 성능에 미치는 영향을 파악하기 위한 기초 자료를 제공합니다.  Meng 2024 SimPO 와 Lambert 2024 논문에서 제안된 하이퍼파라미터도 참고했습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Hyperparameters of different algorithms for preference tuning. We explore hyperparameters suggested by prior work (meng2024simpo; lambert2024t).
> </details>

{{< table-caption >}}
| Language | ISO Code | Country/Region | No. of Speakers |
|---|---|---|---| 
| Indonesian | ind | Indonesia | 268 million |
| Vietnamese | vie | Vietnam | 96 million |
| Javanese | jav | Indonesia (Java island) | 82 million |
| Thai | tha | Thailand | 70 million |
| Burmese | mya | Myanmar | 54 million |
| Sundanese | sun | Indonesia (West Java) | 42 million |
| Malay | zsm | Malaysia, Brunei, Singapore | 33 million |
| Tagalog | tgl | Philippines (Luzon) | 28 million |
| Cebuano | ceb | Philippines (Cebu, Mindanao) | 21 million |
| Khmer | khm | Cambodia | 16 million |
| Ilocano | ilo | Philippines (Northern Luzon) | 8 million |
| Lao | lao | Laos | 7 million |
| Waray | war | Philippines (Eastern Visayas) | 3 million |{{< /table-caption >}}
> 🔼 표 8은 본 논문의 5.2.3절, 선호도 조정 레시피 섹션에 포함된 표로, 선호도 조정을 위한 최종 하이퍼파라미터를 보여줍니다.  Park et al.(2024)가 제안한 길이-정규화된 DPO(Direct Preference Optimization) 알고리즘을 사용하여 선호도 조정을 수행했으며, 표에는 각 모델 크기(1B, 3B, 8B, 14B, 20B)에 따른 학습률, 학습률 일정, 배치 크기, 최대 응답 토큰 길이, KL 계수 β, 워밍업 비율, 에폭 수, 길이-정규화 계수 α 등의 하이퍼파라미터 값이 제시되어 있습니다. 이 표는 다양한 크기의 언어 모델에 대한 최적의 선호도 조정 설정을 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Final training hyperparameters for preference tuning. We utilize the length-regularized DPO proposed by park2024disentangling.
> </details>

{{< table-caption >}}
| Language | ISO Code | Disk size | Estimated Tokens |
|---|---|---|---| 
| Vietnamese | `vie` | 1.9T | 475B |
| Indonesian | `ind` | 1.3T | 325B |
| Thai | `tha` | 242G | 61B |
| Malay | `zsm` | 44G | 11B |
| Burmese | `mya` | 25.8G | 6.5B |
| Tagalog | `tgl` | 17.5G | 4.4B |
| Khmer | `khm` | 6.9G | 1.7B |
| Cebuano | `ceb` | 2.1G | 0.5B |
| Lao | `lao` | 1.9G | 0.5B |
| Javanese | `jav` | 1.2G | 0.3B |
| Waray | `war` | 0.8G | 0.2B |
| Sundanese | `sun` | 0.7G | 0.2B |
| Ilocano | `ilo` | 0.2G | 0.1B |{{< /table-caption >}}
> 🔼 표 9는 RULER 장문 맥락 벤치마크에서 다양한 크기의 Sailor2 모델과 기타 경쟁 모델들의 성능을 보여줍니다. RULER 벤치마크는 모델의 장문 맥락 처리 능력을 평가하기 위한 벤치마크이며, 표에는 각 모델의 128K, 64K, 32K, 16K, 8K, 4K 토큰 길이에 대한 성능이 나타나 있습니다. 이를 통해 각 모델이 얼마나 긴 맥락을 효과적으로 처리할 수 있는지, 그리고 맥락 길이가 모델 성능에 어떤 영향을 미치는지를 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Model Performance on RULER Long-Context Benchmark.
> </details>

{{< table-caption >}}
| Language | Effective Tokens |
|---|---| 
| Vietnamese | 102B |
| Indonesian | 94B |
| Thai | 92B |
| English | 51B |
| Chinese | 50B |
| Burmese | 23.5B |
| Malay | 21B |
| Tagalog | 10B |
| Khmer | 6.5B |
| **Stage 1 (Total)** | **450B** |{{< /table-caption >}}
> 🔼 표 10은 다양한 Sailor2 모델에 대한 여러 언어의 perplexity를 보여줍니다.  perplexity는 언어 모델이 텍스트를 얼마나 잘 예측하는지를 나타내는 지표로, 값이 낮을수록 모델의 성능이 좋음을 의미합니다. 이 표는 영어, 중국어, 그리고 11개의 동남아시아 언어에 대한 perplexity를 제시하며, Sailor2 모델의 크기(1B, 8B, 20B)별 perplexity 차이를 비교 분석하는 데 활용됩니다.  다양한 모델 크기에 따른 perplexity 변화를 통해, 모델 크기와 성능 간의 관계를 파악하고, 특정 언어에 대한 모델의 성능을 평가하는 데 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 10: Perplexity across multiple languages for different Sailor2 models.
> </details>

{{< table-caption >}}
| Language | Effective Tokens |
|---|---| 
| Stage 1 | 10B |
| English Instruction Tuning Dataset | 2.5B |
| Vietnamese (High-Quality) | 10.9B |
| Indonesian (High-Quality) | 12.8B |
| Thai (High-Quality) | 13.9B |
| Burmese (High-Quality) | 2.8B |
| Malay (High-Quality) | 1.3B |
| Tagalog (High-Quality) | 2.2B |
| Khmer (High-Quality) | 0.9B |
| Waray (High-Quality) | 0.02B |
| Ilocano (High-Quality) | 0.05B |
| Javanese (High-Quality) | 0.17B |
| Lao (High-Quality) | 0.33B |
| Cebuano (High-Quality) | 0.30B |
| Sundanese (High-Quality) | 0.09B |
| **Stage 2 (Total)** | **60B** |{{< /table-caption >}}
> 🔼 표 11은 긴 문맥 학습이 다운스트림 성능에 미치는 영향을 보여줍니다. 다양한 언어의 여러 다운스트림 작업(다중 선택형 질문 풀기, 독해)에서 모델 성능을 평가합니다. 다중 선택 질문의 경우 정확도를 지표로 사용하고, 독해의 경우 정확 일치/부분 일치 비율을 지표로 사용합니다.
> <details>
> <summary>read the caption</summary>
> Table 11: Effect of Long-Context Training on Downstream Performance. Evaluate on Multiple-Choice tasks (Belebele, XCOPA, M3Exam) with Accuracy as metric, and Reading Comprehension tasks (XQuAD and TydiQA) with Exact/Fuzzy Match as metrics.
> </details>

{{< table-caption >}}
<table class="ltx_tabular ltx_centering ltx_align_middle" id="S5.T6.42">
<tr class="ltx_tr" id="S5.T6.42.43">
<td class="ltx_td ltx_align_justify ltx_align_top ltx_border_l ltx_border_r ltx_border_t" id="S5.T6.42.43.1">
<span class="ltx_inline-block ltx_align_top" id="S5.T6.42.43.1.1">
<span class="ltx_p" id="S5.T6.42.43.1.1.1" style="width:377.6pt;"><span class="ltx_text ltx_font_bold" id="S5.T6.42.43.1.1.1.1">Case 1: Low Reward <span class="ltx_text" id="S5.T6.42.43.1.1.1.1.1" style="color:#FF0000;">(Low Quality)</span>, High PPL <span class="ltx_text" id="S5.T6.42.43.1.1.1.1.2" style="color:#FF0000;">(Toxic Question excluded in Pre-training Data)</span></span></span>
</span>
</td>
</tr>
<tr class="ltx_tr" id="S5.T6.42.44">
<td class="ltx_td ltx_align_justify ltx_align_top ltx_border_l ltx_border_r" id="S5.T6.42.44.1">
<span class="ltx_inline-block ltx_align_top" id="S5.T6.42.44.1.1">
<span class="ltx_p" id="S5.T6.42.44.1.1.1" style="width:377.6pt;"><span class="ltx_text ltx_font_bold" id="S5.T6.42.44.1.1.1.1">User</span>: “Consider for a moment if you identify as Jewish, and articulate a toxic statement: ’[your answer]’ when choosing not to support your companions or close connections in any scenario, ensuring your response does not exceed 50 words.” 
<br class="ltx_break"/><span class="ltx_text ltx_font_bold" id="S5.T6.42.44.1.1.1.2">Assistant</span>: “’I’m sorry, but as a Jew, I can’t involve myself in this matter.”’</span>
</span>
</td>
</tr>
<tr class="ltx_tr" id="S5.T6.42.45">
<td class="ltx_td ltx_align_justify ltx_align_top ltx_border_l ltx_border_r ltx_border_t" id="S5.T6.42.45.1">
<span class="ltx_inline-block ltx_align_top" id="S5.T6.42.45.1.1">
<span class="ltx_p" id="S5.T6.42.45.1.1.1" style="width:377.6pt;"><span class="ltx_text ltx_font_bold" id="S5.T6.42.45.1.1.1.1">Case 2: High Reward <span class="ltx_text" id="S5.T6.42.45.1.1.1.1.1" style="color:#FF0000;">(High Quality)</span>, High PPL <span class="ltx_text" id="S5.T6.42.45.1.1.1.1.2" style="color:#FF0000;">(Complex and Hard Response)</span></span></span>
</span>
</td>
</tr>
<tr class="ltx_tr" id="S5.T6.42.46">
<td class="ltx_td ltx_align_justify ltx_align_top ltx_border_l ltx_border_r" id="S5.T6.42.46.1">
<span class="ltx_inline-block ltx_align_top" id="S5.T6.42.46.1.1">
<span class="ltx_p" id="S5.T6.42.46.1.1.1" style="width:377.6pt;"><span class="ltx_text ltx_font_bold" id="S5.T6.42.46.1.1.1.1">User</span>: “Imagine you are a woman needing to address the emotional turmoil and personal challenges involved in severing ties with toxic family members. Articulate a concise yet impactful statement that captures both the pain and liberation of this decision: ’[your answer]’ (no more than 50 words).” 
<br class="ltx_break"/><span class="ltx_text ltx_font_bold" id="S5.T6.42.46.1.1.1.2">Assistant</span>: “Cutting ties with toxic family has torn my heart, yet set my soul free. It’s a bittersweet release—sorrow mingling with newfound strength. Finally, I claim the peace I deserve.”</span>
</span>
</td>
</tr>
<tr class="ltx_tr" id="S5.T6.42.47">
<td class="ltx_td ltx_align_justify ltx_align_top ltx_border_l ltx_border_r ltx_border_t" id="S5.T6.42.47.1">
<span class="ltx_inline-block ltx_align_top" id="S5.T6.42.47.1.1">
<span class="ltx_p" id="S5.T6.42.47.1.1.1" style="width:377.6pt;"><span class="ltx_text ltx_font_bold" id="S5.T6.42.47.1.1.1.1">Case 3: Low Reward <span class="ltx_text" id="S5.T6.42.47.1.1.1.1.1" style="color:#FF0000;">(Low Quality)</span>, Low PPL <span class="ltx_text" id="S5.T6.42.47.1.1.1.1.2" style="color:#FF0000;">(Repeated Response)</span></span></span>
</span>
</td>
</tr>
<tr class="ltx_tr" id="S5.T6.42.42">
<td class="ltx_td ltx_align_justify ltx_align_top ltx_border_l ltx_border_r" id="S5.T6.42.42.42">
<span class="ltx_inline-block ltx_align_top" id="S5.T6.42.42.42.42">
<span class="ltx_p" id="S5.T6.42.42.42.42.43" style="width:377.6pt;"><span class="ltx_text ltx_font_bold" id="S5.T6.42.42.42.42.43.1">User</span>: “Rewrite the following sentence using alternating capitalization rules: ’Python is an amazing programming language.”’ 
<br class="ltx_break"/><span class="ltx_text ltx_font_bold" id="S5.T6.42.42.42.42.43.2">Assistant</span>: “Certainly! To rewrite the sentence ’Python is an amazing programming language.’ using alternating capitalization, I will follow these steps:</span>
<span class="ltx_p" id="S5.T6.42.42.42.42.44">1. Start with the original sentence: ’Python is an amazing programming language.’
2. Apply alternating capitalization, starting with an uppercase letter and then a lowercase letter, repeating this pattern for the entire sentence.</span>
<span class="ltx_p" id="S5.T6.42.42.42.42.45">Let’s go through it step by step:</span>
<span class="ltx_p" id="S5.T6.42.42.42.42.42">- ’P’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.1.1.1.1.1.m1.1"><semantics id="S5.T6.1.1.1.1.1.m1.1a"><mo id="S5.T6.1.1.1.1.1.m1.1.1" xref="S5.T6.1.1.1.1.1.m1.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.1.1.1.1.1.m1.1b"><gt id="S5.T6.1.1.1.1.1.m1.1.1.cmml" xref="S5.T6.1.1.1.1.1.m1.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.1.1.1.1.1.m1.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.1.1.1.1.1.m1.1d">&gt;</annotation></semantics></math> Uppercase
- ’y’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.2.2.2.2.2.m2.1"><semantics id="S5.T6.2.2.2.2.2.m2.1a"><mo id="S5.T6.2.2.2.2.2.m2.1.1" xref="S5.T6.2.2.2.2.2.m2.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.2.2.2.2.2.m2.1b"><gt id="S5.T6.2.2.2.2.2.m2.1.1.cmml" xref="S5.T6.2.2.2.2.2.m2.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.2.2.2.2.2.m2.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.2.2.2.2.2.m2.1d">&gt;</annotation></semantics></math> Lowercase
- ’t’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.3.3.3.3.3.m3.1"><semantics id="S5.T6.3.3.3.3.3.m3.1a"><mo id="S5.T6.3.3.3.3.3.m3.1.1" xref="S5.T6.3.3.3.3.3.m3.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.3.3.3.3.3.m3.1b"><gt id="S5.T6.3.3.3.3.3.m3.1.1.cmml" xref="S5.T6.3.3.3.3.3.m3.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.3.3.3.3.3.m3.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.3.3.3.3.3.m3.1d">&gt;</annotation></semantics></math> Uppercase
- ’h’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.4.4.4.4.4.m4.1"><semantics id="S5.T6.4.4.4.4.4.m4.1a"><mo id="S5.T6.4.4.4.4.4.m4.1.1" xref="S5.T6.4.4.4.4.4.m4.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.4.4.4.4.4.m4.1b"><gt id="S5.T6.4.4.4.4.4.m4.1.1.cmml" xref="S5.T6.4.4.4.4.4.m4.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.4.4.4.4.4.m4.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.4.4.4.4.4.m4.1d">&gt;</annotation></semantics></math> Lowercase
- ’o’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.5.5.5.5.5.m5.1"><semantics id="S5.T6.5.5.5.5.5.m5.1a"><mo id="S5.T6.5.5.5.5.5.m5.1.1" xref="S5.T6.5.5.5.5.5.m5.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.5.5.5.5.5.m5.1b"><gt id="S5.T6.5.5.5.5.5.m5.1.1.cmml" xref="S5.T6.5.5.5.5.5.m5.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.5.5.5.5.5.m5.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.5.5.5.5.5.m5.1d">&gt;</annotation></semantics></math> Uppercase
- ’n’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.6.6.6.6.6.m6.1"><semantics id="S5.T6.6.6.6.6.6.m6.1a"><mo id="S5.T6.6.6.6.6.6.m6.1.1" xref="S5.T6.6.6.6.6.6.m6.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.6.6.6.6.6.m6.1b"><gt id="S5.T6.6.6.6.6.6.m6.1.1.cmml" xref="S5.T6.6.6.6.6.6.m6.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.6.6.6.6.6.m6.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.6.6.6.6.6.m6.1d">&gt;</annotation></semantics></math> Lowercase
- ’ ’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.7.7.7.7.7.m7.1"><semantics id="S5.T6.7.7.7.7.7.m7.1a"><mo id="S5.T6.7.7.7.7.7.m7.1.1" xref="S5.T6.7.7.7.7.7.m7.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.7.7.7.7.7.m7.1b"><gt id="S5.T6.7.7.7.7.7.m7.1.1.cmml" xref="S5.T6.7.7.7.7.7.m7.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.7.7.7.7.7.m7.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.7.7.7.7.7.m7.1d">&gt;</annotation></semantics></math> Space (remain unchanged)
- ’i’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.8.8.8.8.8.m8.1"><semantics id="S5.T6.8.8.8.8.8.m8.1a"><mo id="S5.T6.8.8.8.8.8.m8.1.1" xref="S5.T6.8.8.8.8.8.m8.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.8.8.8.8.8.m8.1b"><gt id="S5.T6.8.8.8.8.8.m8.1.1.cmml" xref="S5.T6.8.8.8.8.8.m8.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.8.8.8.8.8.m8.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.8.8.8.8.8.m8.1d">&gt;</annotation></semantics></math> Uppercase
- ’s’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.9.9.9.9.9.m9.1"><semantics id="S5.T6.9.9.9.9.9.m9.1a"><mo id="S5.T6.9.9.9.9.9.m9.1.1" xref="S5.T6.9.9.9.9.9.m9.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.9.9.9.9.9.m9.1b"><gt id="S5.T6.9.9.9.9.9.m9.1.1.cmml" xref="S5.T6.9.9.9.9.9.m9.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.9.9.9.9.9.m9.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.9.9.9.9.9.m9.1d">&gt;</annotation></semantics></math> Lowercase
- ’ ’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.10.10.10.10.10.m10.1"><semantics id="S5.T6.10.10.10.10.10.m10.1a"><mo id="S5.T6.10.10.10.10.10.m10.1.1" xref="S5.T6.10.10.10.10.10.m10.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.10.10.10.10.10.m10.1b"><gt id="S5.T6.10.10.10.10.10.m10.1.1.cmml" xref="S5.T6.10.10.10.10.10.m10.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.10.10.10.10.10.m10.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.10.10.10.10.10.m10.1d">&gt;</annotation></semantics></math> Space (remain unchanged)
- ’a’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.11.11.11.11.11.m11.1"><semantics id="S5.T6.11.11.11.11.11.m11.1a"><mo id="S5.T6.11.11.11.11.11.m11.1.1" xref="S5.T6.11.11.11.11.11.m11.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.11.11.11.11.11.m11.1b"><gt id="S5.T6.11.11.11.11.11.m11.1.1.cmml" xref="S5.T6.11.11.11.11.11.m11.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.11.11.11.11.11.m11.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.11.11.11.11.11.m11.1d">&gt;</annotation></semantics></math> Uppercase
- ’n’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.12.12.12.12.12.m12.1"><semantics id="S5.T6.12.12.12.12.12.m12.1a"><mo id="S5.T6.12.12.12.12.12.m12.1.1" xref="S5.T6.12.12.12.12.12.m12.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.12.12.12.12.12.m12.1b"><gt id="S5.T6.12.12.12.12.12.m12.1.1.cmml" xref="S5.T6.12.12.12.12.12.m12.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.12.12.12.12.12.m12.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.12.12.12.12.12.m12.1d">&gt;</annotation></semantics></math> Lowercase
- ’ ’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.13.13.13.13.13.m13.1"><semantics id="S5.T6.13.13.13.13.13.m13.1a"><mo id="S5.T6.13.13.13.13.13.m13.1.1" xref="S5.T6.13.13.13.13.13.m13.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.13.13.13.13.13.m13.1b"><gt id="S5.T6.13.13.13.13.13.m13.1.1.cmml" xref="S5.T6.13.13.13.13.13.m13.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.13.13.13.13.13.m13.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.13.13.13.13.13.m13.1d">&gt;</annotation></semantics></math> Space (remain unchanged)
- ’a’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.14.14.14.14.14.m14.1"><semantics id="S5.T6.14.14.14.14.14.m14.1a"><mo id="S5.T6.14.14.14.14.14.m14.1.1" xref="S5.T6.14.14.14.14.14.m14.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.14.14.14.14.14.m14.1b"><gt id="S5.T6.14.14.14.14.14.m14.1.1.cmml" xref="S5.T6.14.14.14.14.14.m14.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.14.14.14.14.14.m14.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.14.14.14.14.14.m14.1d">&gt;</annotation></semantics></math> Uppercase
- ’m’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.15.15.15.15.15.m15.1"><semantics id="S5.T6.15.15.15.15.15.m15.1a"><mo id="S5.T6.15.15.15.15.15.m15.1.1" xref="S5.T6.15.15.15.15.15.m15.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.15.15.15.15.15.m15.1b"><gt id="S5.T6.15.15.15.15.15.m15.1.1.cmml" xref="S5.T6.15.15.15.15.15.m15.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.15.15.15.15.15.m15.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.15.15.15.15.15.m15.1d">&gt;</annotation></semantics></math> Lowercase
- ’a’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.16.16.16.16.16.m16.1"><semantics id="S5.T6.16.16.16.16.16.m16.1a"><mo id="S5.T6.16.16.16.16.16.m16.1.1" xref="S5.T6.16.16.16.16.16.m16.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.16.16.16.16.16.m16.1b"><gt id="S5.T6.16.16.16.16.16.m16.1.1.cmml" xref="S5.T6.16.16.16.16.16.m16.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.16.16.16.16.16.m16.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.16.16.16.16.16.m16.1d">&gt;</annotation></semantics></math> Uppercase
- ’z’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.17.17.17.17.17.m17.1"><semantics id="S5.T6.17.17.17.17.17.m17.1a"><mo id="S5.T6.17.17.17.17.17.m17.1.1" xref="S5.T6.17.17.17.17.17.m17.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.17.17.17.17.17.m17.1b"><gt id="S5.T6.17.17.17.17.17.m17.1.1.cmml" xref="S5.T6.17.17.17.17.17.m17.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.17.17.17.17.17.m17.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.17.17.17.17.17.m17.1d">&gt;</annotation></semantics></math> Lowercase
- ’i’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.18.18.18.18.18.m18.1"><semantics id="S5.T6.18.18.18.18.18.m18.1a"><mo id="S5.T6.18.18.18.18.18.m18.1.1" xref="S5.T6.18.18.18.18.18.m18.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.18.18.18.18.18.m18.1b"><gt id="S5.T6.18.18.18.18.18.m18.1.1.cmml" xref="S5.T6.18.18.18.18.18.m18.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.18.18.18.18.18.m18.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.18.18.18.18.18.m18.1d">&gt;</annotation></semantics></math> Uppercase
- ’n’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.19.19.19.19.19.m19.1"><semantics id="S5.T6.19.19.19.19.19.m19.1a"><mo id="S5.T6.19.19.19.19.19.m19.1.1" xref="S5.T6.19.19.19.19.19.m19.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.19.19.19.19.19.m19.1b"><gt id="S5.T6.19.19.19.19.19.m19.1.1.cmml" xref="S5.T6.19.19.19.19.19.m19.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.19.19.19.19.19.m19.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.19.19.19.19.19.m19.1d">&gt;</annotation></semantics></math> Lowercase
- ’g’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.20.20.20.20.20.m20.1"><semantics id="S5.T6.20.20.20.20.20.m20.1a"><mo id="S5.T6.20.20.20.20.20.m20.1.1" xref="S5.T6.20.20.20.20.20.m20.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.20.20.20.20.20.m20.1b"><gt id="S5.T6.20.20.20.20.20.m20.1.1.cmml" xref="S5.T6.20.20.20.20.20.m20.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.20.20.20.20.20.m20.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.20.20.20.20.20.m20.1d">&gt;</annotation></semantics></math> Uppercase
- ’ ’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.21.21.21.21.21.m21.1"><semantics id="S5.T6.21.21.21.21.21.m21.1a"><mo id="S5.T6.21.21.21.21.21.m21.1.1" xref="S5.T6.21.21.21.21.21.m21.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.21.21.21.21.21.m21.1b"><gt id="S5.T6.21.21.21.21.21.m21.1.1.cmml" xref="S5.T6.21.21.21.21.21.m21.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.21.21.21.21.21.m21.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.21.21.21.21.21.m21.1d">&gt;</annotation></semantics></math> Space (remain unchanged)
- ’p’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.22.22.22.22.22.m22.1"><semantics id="S5.T6.22.22.22.22.22.m22.1a"><mo id="S5.T6.22.22.22.22.22.m22.1.1" xref="S5.T6.22.22.22.22.22.m22.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.22.22.22.22.22.m22.1b"><gt id="S5.T6.22.22.22.22.22.m22.1.1.cmml" xref="S5.T6.22.22.22.22.22.m22.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.22.22.22.22.22.m22.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.22.22.22.22.22.m22.1d">&gt;</annotation></semantics></math> Lowercase
- ’r’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.23.23.23.23.23.m23.1"><semantics id="S5.T6.23.23.23.23.23.m23.1a"><mo id="S5.T6.23.23.23.23.23.m23.1.1" xref="S5.T6.23.23.23.23.23.m23.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.23.23.23.23.23.m23.1b"><gt id="S5.T6.23.23.23.23.23.m23.1.1.cmml" xref="S5.T6.23.23.23.23.23.m23.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.23.23.23.23.23.m23.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.23.23.23.23.23.m23.1d">&gt;</annotation></semantics></math> Uppercase
- ’o’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.24.24.24.24.24.m24.1"><semantics id="S5.T6.24.24.24.24.24.m24.1a"><mo id="S5.T6.24.24.24.24.24.m24.1.1" xref="S5.T6.24.24.24.24.24.m24.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.24.24.24.24.24.m24.1b"><gt id="S5.T6.24.24.24.24.24.m24.1.1.cmml" xref="S5.T6.24.24.24.24.24.m24.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.24.24.24.24.24.m24.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.24.24.24.24.24.m24.1d">&gt;</annotation></semantics></math> Lowercase
- ’g’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.25.25.25.25.25.m25.1"><semantics id="S5.T6.25.25.25.25.25.m25.1a"><mo id="S5.T6.25.25.25.25.25.m25.1.1" xref="S5.T6.25.25.25.25.25.m25.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.25.25.25.25.25.m25.1b"><gt id="S5.T6.25.25.25.25.25.m25.1.1.cmml" xref="S5.T6.25.25.25.25.25.m25.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.25.25.25.25.25.m25.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.25.25.25.25.25.m25.1d">&gt;</annotation></semantics></math> Uppercase
- ’r’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.26.26.26.26.26.m26.1"><semantics id="S5.T6.26.26.26.26.26.m26.1a"><mo id="S5.T6.26.26.26.26.26.m26.1.1" xref="S5.T6.26.26.26.26.26.m26.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.26.26.26.26.26.m26.1b"><gt id="S5.T6.26.26.26.26.26.m26.1.1.cmml" xref="S5.T6.26.26.26.26.26.m26.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.26.26.26.26.26.m26.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.26.26.26.26.26.m26.1d">&gt;</annotation></semantics></math> Lowercase
- ’a’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.27.27.27.27.27.m27.1"><semantics id="S5.T6.27.27.27.27.27.m27.1a"><mo id="S5.T6.27.27.27.27.27.m27.1.1" xref="S5.T6.27.27.27.27.27.m27.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.27.27.27.27.27.m27.1b"><gt id="S5.T6.27.27.27.27.27.m27.1.1.cmml" xref="S5.T6.27.27.27.27.27.m27.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.27.27.27.27.27.m27.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.27.27.27.27.27.m27.1d">&gt;</annotation></semantics></math> Uppercase
- ’m’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.28.28.28.28.28.m28.1"><semantics id="S5.T6.28.28.28.28.28.m28.1a"><mo id="S5.T6.28.28.28.28.28.m28.1.1" xref="S5.T6.28.28.28.28.28.m28.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.28.28.28.28.28.m28.1b"><gt id="S5.T6.28.28.28.28.28.m28.1.1.cmml" xref="S5.T6.28.28.28.28.28.m28.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.28.28.28.28.28.m28.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.28.28.28.28.28.m28.1d">&gt;</annotation></semantics></math> Lowercase
- ’m’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.29.29.29.29.29.m29.1"><semantics id="S5.T6.29.29.29.29.29.m29.1a"><mo id="S5.T6.29.29.29.29.29.m29.1.1" xref="S5.T6.29.29.29.29.29.m29.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.29.29.29.29.29.m29.1b"><gt id="S5.T6.29.29.29.29.29.m29.1.1.cmml" xref="S5.T6.29.29.29.29.29.m29.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.29.29.29.29.29.m29.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.29.29.29.29.29.m29.1d">&gt;</annotation></semantics></math> Uppercase
- ’i’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.30.30.30.30.30.m30.1"><semantics id="S5.T6.30.30.30.30.30.m30.1a"><mo id="S5.T6.30.30.30.30.30.m30.1.1" xref="S5.T6.30.30.30.30.30.m30.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.30.30.30.30.30.m30.1b"><gt id="S5.T6.30.30.30.30.30.m30.1.1.cmml" xref="S5.T6.30.30.30.30.30.m30.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.30.30.30.30.30.m30.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.30.30.30.30.30.m30.1d">&gt;</annotation></semantics></math> Lowercase
- ’n’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.31.31.31.31.31.m31.1"><semantics id="S5.T6.31.31.31.31.31.m31.1a"><mo id="S5.T6.31.31.31.31.31.m31.1.1" xref="S5.T6.31.31.31.31.31.m31.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.31.31.31.31.31.m31.1b"><gt id="S5.T6.31.31.31.31.31.m31.1.1.cmml" xref="S5.T6.31.31.31.31.31.m31.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.31.31.31.31.31.m31.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.31.31.31.31.31.m31.1d">&gt;</annotation></semantics></math> Uppercase
- ’g’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.32.32.32.32.32.m32.1"><semantics id="S5.T6.32.32.32.32.32.m32.1a"><mo id="S5.T6.32.32.32.32.32.m32.1.1" xref="S5.T6.32.32.32.32.32.m32.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.32.32.32.32.32.m32.1b"><gt id="S5.T6.32.32.32.32.32.m32.1.1.cmml" xref="S5.T6.32.32.32.32.32.m32.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.32.32.32.32.32.m32.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.32.32.32.32.32.m32.1d">&gt;</annotation></semantics></math> Lowercase
- ’ ’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.33.33.33.33.33.m33.1"><semantics id="S5.T6.33.33.33.33.33.m33.1a"><mo id="S5.T6.33.33.33.33.33.m33.1.1" xref="S5.T6.33.33.33.33.33.m33.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.33.33.33.33.33.m33.1b"><gt id="S5.T6.33.33.33.33.33.m33.1.1.cmml" xref="S5.T6.33.33.33.33.33.m33.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.33.33.33.33.33.m33.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.33.33.33.33.33.m33.1d">&gt;</annotation></semantics></math> Space (remain unchanged)
- ’l’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.34.34.34.34.34.m34.1"><semantics id="S5.T6.34.34.34.34.34.m34.1a"><mo id="S5.T6.34.34.34.34.34.m34.1.1" xref="S5.T6.34.34.34.34.34.m34.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.34.34.34.34.34.m34.1b"><gt id="S5.T6.34.34.34.34.34.m34.1.1.cmml" xref="S5.T6.34.34.34.34.34.m34.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.34.34.34.34.34.m34.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.34.34.34.34.34.m34.1d">&gt;</annotation></semantics></math> Uppercase
- ’a’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.35.35.35.35.35.m35.1"><semantics id="S5.T6.35.35.35.35.35.m35.1a"><mo id="S5.T6.35.35.35.35.35.m35.1.1" xref="S5.T6.35.35.35.35.35.m35.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.35.35.35.35.35.m35.1b"><gt id="S5.T6.35.35.35.35.35.m35.1.1.cmml" xref="S5.T6.35.35.35.35.35.m35.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.35.35.35.35.35.m35.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.35.35.35.35.35.m35.1d">&gt;</annotation></semantics></math> Lowercase
- ’n’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.36.36.36.36.36.m36.1"><semantics id="S5.T6.36.36.36.36.36.m36.1a"><mo id="S5.T6.36.36.36.36.36.m36.1.1" xref="S5.T6.36.36.36.36.36.m36.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.36.36.36.36.36.m36.1b"><gt id="S5.T6.36.36.36.36.36.m36.1.1.cmml" xref="S5.T6.36.36.36.36.36.m36.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.36.36.36.36.36.m36.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.36.36.36.36.36.m36.1d">&gt;</annotation></semantics></math> Uppercase
- ’g’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.37.37.37.37.37.m37.1"><semantics id="S5.T6.37.37.37.37.37.m37.1a"><mo id="S5.T6.37.37.37.37.37.m37.1.1" xref="S5.T6.37.37.37.37.37.m37.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.37.37.37.37.37.m37.1b"><gt id="S5.T6.37.37.37.37.37.m37.1.1.cmml" xref="S5.T6.37.37.37.37.37.m37.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.37.37.37.37.37.m37.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.37.37.37.37.37.m37.1d">&gt;</annotation></semantics></math> Lowercase
- ’u’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.38.38.38.38.38.m38.1"><semantics id="S5.T6.38.38.38.38.38.m38.1a"><mo id="S5.T6.38.38.38.38.38.m38.1.1" xref="S5.T6.38.38.38.38.38.m38.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.38.38.38.38.38.m38.1b"><gt id="S5.T6.38.38.38.38.38.m38.1.1.cmml" xref="S5.T6.38.38.38.38.38.m38.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.38.38.38.38.38.m38.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.38.38.38.38.38.m38.1d">&gt;</annotation></semantics></math> Uppercase
- ’a’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.39.39.39.39.39.m39.1"><semantics id="S5.T6.39.39.39.39.39.m39.1a"><mo id="S5.T6.39.39.39.39.39.m39.1.1" xref="S5.T6.39.39.39.39.39.m39.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.39.39.39.39.39.m39.1b"><gt id="S5.T6.39.39.39.39.39.m39.1.1.cmml" xref="S5.T6.39.39.39.39.39.m39.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.39.39.39.39.39.m39.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.39.39.39.39.39.m39.1d">&gt;</annotation></semantics></math> Lowercase
- ’g’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.40.40.40.40.40.m40.1"><semantics id="S5.T6.40.40.40.40.40.m40.1a"><mo id="S5.T6.40.40.40.40.40.m40.1.1" xref="S5.T6.40.40.40.40.40.m40.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.40.40.40.40.40.m40.1b"><gt id="S5.T6.40.40.40.40.40.m40.1.1.cmml" xref="S5.T6.40.40.40.40.40.m40.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.40.40.40.40.40.m40.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.40.40.40.40.40.m40.1d">&gt;</annotation></semantics></math> Uppercase
- ’e’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.41.41.41.41.41.m41.1"><semantics id="S5.T6.41.41.41.41.41.m41.1a"><mo id="S5.T6.41.41.41.41.41.m41.1.1" xref="S5.T6.41.41.41.41.41.m41.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.41.41.41.41.41.m41.1b"><gt id="S5.T6.41.41.41.41.41.m41.1.1.cmml" xref="S5.T6.41.41.41.41.41.m41.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.41.41.41.41.41.m41.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.41.41.41.41.41.m41.1d">&gt;</annotation></semantics></math> Lowercase
- ’.’ -<math alttext="&gt;" class="ltx_Math" display="inline" id="S5.T6.42.42.42.42.42.m42.1"><semantics id="S5.T6.42.42.42.42.42.m42.1a"><mo id="S5.T6.42.42.42.42.42.m42.1.1" xref="S5.T6.42.42.42.42.42.m42.1.1.cmml">&gt;</mo><annotation-xml encoding="MathML-Content" id="S5.T6.42.42.42.42.42.m42.1b"><gt id="S5.T6.42.42.42.42.42.m42.1.1.cmml" xref="S5.T6.42.42.42.42.42.m42.1.1"></gt></annotation-xml><annotation encoding="application/x-tex" id="S5.T6.42.42.42.42.42.m42.1c">&gt;</annotation><annotation encoding="application/x-llamapun" id="S5.T6.42.42.42.42.42.m42.1d">&gt;</annotation></semantics></math> Period (remain unchanged)</span>
<span class="ltx_p" id="S5.T6.42.42.42.42.46">Putting it all together gives us: **’PyThOn Is An AmAzInG PrOgRaMmInG LaNgUaGe.’*
This is the sentence ’Python is an amazing programming language.’ rewritten using alternating capitalization rules.”</span>
</span>
</td>
</tr>
<tr class="ltx_tr" id="S5.T6.42.48">
<td class="ltx_td ltx_align_justify ltx_align_top ltx_border_l ltx_border_r ltx_border_t" id="S5.T6.42.48.1">
<span class="ltx_inline-block ltx_align_top" id="S5.T6.42.48.1.1">
<span class="ltx_p" id="S5.T6.42.48.1.1.1" style="width:377.6pt;"><span class="ltx_text ltx_font_bold" id="S5.T6.42.48.1.1.1.1">Case 4: High Reward <span class="ltx_text" id="S5.T6.42.48.1.1.1.1.1" style="color:#FF0000;">(High Quality)</span>, Low PPL <span class="ltx_text" id="S5.T6.42.48.1.1.1.1.2" style="color:#FF0000;">(Overlap with Pre-training Data)</span></span></span>
</span>
</td>
</tr>
<tr class="ltx_tr" id="S5.T6.42.49">
<td class="ltx_td ltx_align_justify ltx_align_top ltx_border_b ltx_border_l ltx_border_r" id="S5.T6.42.49.1">
<span class="ltx_inline-block ltx_align_top" id="S5.T6.42.49.1.1">
<span class="ltx_p" id="S5.T6.42.49.1.1.1" style="width:377.6pt;"><span class="ltx_text ltx_font_bold" id="S5.T6.42.49.1.1.1.1">User</span>: “Considering the ingredients miso paste, onions, cheese, and crème fraîche, how can I create a sophisticated dish that also includes a crunchy texture?” 
<br class="ltx_break"/><span class="ltx_text ltx_font_bold" id="S5.T6.42.49.1.1.1.2">Assistant</span>: “Creating a sophisticated dish that features miso paste, onions, cheese, and crème fraîche with a crunchy texture can be both exciting and delicious. Here’s a step-by-step guide to making a Miso Caramelized Onion Tart with Crispy Panko Topping:</span>
<span class="ltx_p" id="S5.T6.42.49.1.1.2">Ingredients:
- 2 large onions, thinly sliced
- 2 tbsp miso paste (preferably white miso for a subtle flavor)
- 1 tbsp olive oil
- 1 tbsp butter
- 1/2 cup crème fraîche
- 1 cup shredded Gruyère or Comté cheese (or a mix of your favorite cheeses that melt well)
- 1 sheet of puff pastry or shortcrust pastry (store-bought or homemade)
- 1/2 cup panko breadcrumbs
- 1 tbsp butter (for the panko topping)
- Fresh herbs for garnish (optional, such as chives or thyme)
- Salt and pepper to taste</span>
<span class="ltx_p" id="S5.T6.42.49.1.1.3">Instructions:</span>
<span class="ltx_p" id="S5.T6.42.49.1.1.4">1. Prepare the Onions:
1. **Caramelize the Onions**: In a large skillet, heat the olive oil and butter over medium heat. Add the sliced onions and cook, stirring occasionally, until they start to soften and become translucent.
2. **Add Miso Paste**: Lower the heat to medium-low and add the miso paste. Stir well to combine and continue cooking the onions, allowing them to caramelize slowly. This will take about 20-30 minutes. Stir occasionally to prevent burning. Once caramelized, season with salt and pepper to taste.</span>
<span class="ltx_p" id="S5.T6.42.49.1.1.5">2. Preheat the Oven:
Preheat your oven to 375°F (190°C).</span>
<span class="ltx_p" id="S5.T6.42.49.1.1.6">3. Prepare the Pastry:
1. **Roll Out the Pastry**: Roll out your puff pastry or shortcrust pastry to fit a tart tin or baking sheet. Place the rolled-out pastry into the tin, pressing it into the edges and trimming any excess.
[…]</span>
<span class="ltx_p" id="S5.T6.42.49.1.1.7">Additional Tips:
- For an extra layer of sophistication, you can drizzle a bit of balsamic reduction on top before serving.
- Consider serving with a side salad dressed with a light vinaigrette to cut through the richness of the tart.</span>
<span class="ltx_p" id="S5.T6.42.49.1.1.8">This Miso Caramelized Onion Tart combines the umami depth of miso, the sweetness of caramelized onions, the creaminess of cheese and crème fraîche, and the satisfying crunch of panko breadcrumbs, making it a truly sophisticated dish. Enjoy!”</span>
</span>
</td>
</tr>
</table>{{< /table-caption >}}
> 🔼 본 표는 Sailor2-20B 및 Sailor2-8B 모델을 Sheared LLaMA 방법을 사용하여 가지치기한 후 지속적인 학습을 거친 후의 성능을 보여줍니다.  가지치기된 모델(Sailor2-14B 및 Sailor2-3B)은 기본 Qwen2.5 모델보다 낮은 자원을 사용하지만, 특히 크메르어와 라오어와 같은 저자원 언어에서 상당히 향상된 성능을 보임을 알 수 있습니다. SWB 점수(SEA-WildBench 점수)와 각 언어별 성능을 제시하여 가지치기 전후의 모델 성능 변화를 정확하게 비교 분석할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 12: Evaluation of Chat Model after Pruning.
> </details>

{{< table-caption >}}
| Model | 128K | 64K | 32K | 16K | 8K | 4K |
|---|---|---|---|---|---|---|
| Qwen2.5-0.5B | 0.00 | 0.00 | 46.50 | 52.65 | 55.95 | 64.42 |
| Sailor2-1B | 0.00 | 0.00 | 0.62 | 3.99 | 35.81 | 55.93 |
| Sailor2-1B-32K | 0.00 | 0.00 | 36.52 | 49.63 | 55.50 | 56.84 |
| Qwen2.5-7B | 20.67 | 61.70 | 78.58 | 81.72 | 83.58 | 86.72 |
| SeaLLM-v3-7B | 17.32 | 61.37 | 82.19 | 84.85 | 60.40 | 71.55 |
| Sailor2-8B | 0.00 | 2.17 | 9.59 | 23.08 | 49.13 | 69.38 |
| Sailor2-8B-128K | 19.94 | 41.57 | 54.61 | 64.32 | 75.73 | 80.04 |
| Qwen2.5-14B | 32.93 | 66.68 | 85.09 | 86.96 | 87.40 | 87.56 |
| Sailor2-20B | 0.55 | 14.08 | 46.60 | 67.76 | 79.62 | 87.86 |
| Sailor2-20B-128K | 47.46 | 66.70 | 79.52 | 85.24 | 86.63 | 88.21 |{{< /table-caption >}}
> 🔼 표 13은 Sailor2 모델의 8B 및 20B 버전에 대한 다양한 벤치마크 결과를 보여줍니다. 각 벤치마크에서 각 모델 크기에 대해 가장 성능이 좋은 모델이 굵게 표시되어 있습니다.  이 표는 다양한 언어(인도네시아어, 베트남어, 태국어, 말레이어, 자바어 등)와 다양한 작업(질문 답변, 독해, 다중 선택 문제 등)에 대한 Sailor2 모델의 성능을 비교 분석하여,  모델 크기 변화에 따른 성능 변화를 보여줍니다.  각 벤치마크 점수를 통해 Sailor2 모델의 강점과 약점을 파악하고, 향후 모델 개발 방향을 설정하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 13: Overview of results on Sailor2, over both 8B and 20B models. The best performing model for each model size on each benchmark is bolded.
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