---
title: "Token Assorted: Mixing Latent and Text Tokens for Improved Language Model Reasoning"
summary: "잠재 토큰과 텍스트 토큰을 혼합하여 언어 모델 추론 성능 향상!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Meta AI",]
showSummary: true
date: 2025-02-05
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.03275 {{< /keyword >}}
{{< keyword icon="writer" >}} DiJia Su et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-06 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.03275" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.03275" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

대규모 언어 모델(LLM)은 연쇄적 사고(CoT) 데이터로 훈련될 때 추론 및 계획 능력이 뛰어나지만, 긴 입력으로 인해 계산 비용이 많이 듭니다.  본 논문은 **텍스트 토큰 대신 잠재 이산 토큰을 사용하여 추론 과정을 효율적으로 압축**하는 새로운 방법을 제시합니다. 기존의 방법들은 다단계 훈련 절차를 사용하여 계산 비용이 많이 들고 성능이 떨어지는 한계를 가지고 있습니다.



본 연구에서는 VQ-VAE를 사용하여 잠재 토큰을 생성하고, **잠재 토큰과 텍스트 토큰을 무작위로 섞어서 LLM을 미세 조정**하는 훈련 절차를 제안합니다.  이를 통해 새로운 잠재 토큰에 대한 빠른 적응을 가능하게 하고, 수학 및 논리 추론 문제에서 **기존 방법보다 우수한 성능**을 달성했습니다.  **추론 과정의 길이를 평균 17% 단축**시키면서도 성능을 향상시킨 것은 본 연구의 주요 기여입니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} VQ-VAE를 사용한 잠재 토큰을 통해 **추론 과정의 길이를 단축**시켰습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} **잠재 토큰과 텍스트 토큰을 무작위로 혼합**하는 훈련 방식으로 새로운 잠재 토큰에 대한 빠른 적응을 가능하게 했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 다양한 벤치마크에서 **기존 방법보다 우수한 성능**을 보였습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **대규모 언어 모델의 추론 능력 향상**에 중요한 발견을 제시합니다.  **잠재 토큰을 활용한 추론 과정의 효율적인 압축**은 계산 비용을 절감하고 성능을 향상시키는 혁신적인 방법론을 제시하며, **다양한 분야의 추론 문제**에 적용 가능한 범용적인 접근 방식을 제시합니다.  이는 앞으로 **더욱 효율적이고 강력한 언어 모델 개발**에 중요한 영향을 미칠 것으로 예상됩니다. 특히, 잠재 토큰과 텍스트 토큰의 혼합 사용 및 무작위 치환 전략은 새로운 연구 방향을 제시하여, 추가적인 연구를 통해 더욱 발전시킬 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.03275/x1.png)

> 🔼  그림 3.1은 제안된 방법의 핵심인 토큰 교체 전략을 보여줍니다.  문맥 토큰(CoT)을 잠재적 이산 토큰으로 변환하는 과정을 시각적으로 설명합니다.  이 예시에서는 청크 크기(L)가 16이고 압축률(r)이 16일 때, 32개의 문맥 토큰이 왼쪽에서 오른쪽으로 2개의 잠재적 토큰으로 압축되는 것을 보여줍니다.  나머지 문맥 토큰은 원래 형태를 유지합니다. 즉, 일부 문맥 토큰은 잠재 토큰으로 변환하여 추론 과정을 요약하고, 나머지 토큰은 원래의 텍스트 토큰으로 유지함으로써 모델이 추론 과정의 상세한 텍스트 정보와 요약된 잠재 정보 모두를 학습할 수 있도록 하는 전략입니다.
> <details>
> <summary>read the caption</summary>
> Figure 3.1: An example illustrating our replacement strategy. With chunk size L=16𝐿16L=16italic_L = 16 and compression rate r=16𝑟16r=16italic_r = 16, we encode 32 textual CoT tokens into 2 discrete latent tokens from left to right. The other CoT tokens will remain in their original forms.
> </details>





{{< table-caption >}}
| Model | Keys-Finding Maze |  | ProntoQA |  | ProsQA |  |
|---|---|---|---|---|---|---|
|  | 1-Feasible-10 (%) | Num. Tokens | Accuracy | Num. Tokens | Accuracy | Num. Tokens |
|---|---|---|---|---|---|---|
| Sol-Only | 3 | 645 | 93.8 | 3.0 | 76.7 | 8.2 |
| CoT | 43 | 1312.0 | 98.8 | 92.5 | 77.5 | 49.4 |
| Latent (ours) | 62.8 (<span style="color:#008000;">↑+19.8</span>) | 374.6 | 100 (<span style="color:#008000;">↑+1.2</span>) | 7.7 | 96.2 (<span style="color:#008000;">↑+18.7</span>) | 10.9 |{{< /table-caption >}}

> 🔼 표 4.1은 제안된 잠재 토큰 접근 방식이 Keys-Finding Maze, ProntoQA, ProsQA 세 가지 벤치마크에서 다른 기준 모델들보다 훨씬 우수한 성능을 보임을 보여줍니다.  Keys-Finding Maze에는 top-k (k=10) 디코딩을, ProntoQA와 ProsQA에는 탐욕적 디코딩을 사용했습니다. 토큰 효율성 측면에서 제안된 방법은 CoT 기준 모델보다 훨씬 짧은 추론 트레이스를 생성하며, Sol-Only 접근 방식과 거의 비슷하거나 더 나은 성능을 보입니다.  굵은 글씨는 최고 성능, 밑줄은 두 번째로 좋은 성능을 나타냅니다.  화살표는 두 번째로 좋은 결과와 비교한 성능 향상을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 4.1: Our latent approach surpasses the other baselines on Keys-Finding Maze, ProntoQA and ProsQA with a large margin . We use top-k𝑘kitalic_k (k=10𝑘10k=10italic_k = 10) decoding for Keys-Finding Maze and greedy decoding for ProntoQA and ProsQA. In terms of token efficiency, our latent approach also generates much shorter reasoning traces than the CoT baseline, closely tracking or even outperforming the Sol-Only approach. Bold: best results. Underline: second best results. (↑↑\uparrow↑ +Performance gain compared with the second best result.)
> </details>





### In-depth insights


#### Latent Reasoning
잠재 추론(Latent Reasoning)은 **대규모 언어 모델(LLM)**이 텍스트로 명시적으로 설명되지 않은 암묵적인 추론 과정을 통해 문제 해결에 도달하는 능력을 의미합니다.  이는 **단순한 패턴 매칭이나 표면적인 단어 연관성을 넘어**, LLM이 내부적으로 복잡한 사고 과정을 거쳐 해답을 도출함을 시사합니다.  **잠재 공간(Latent Space)**을 활용하는 잠재 추론은 긴 추론 과정을 압축하여 효율성을 높이고, 계산 비용을 줄이는 데 기여할 수 있습니다.  그러나 **잠재 변수의 해석 및 투명성 확보**가 중요한 과제이며, 잠재 추론 과정의 이해를 돕는 추가적인 연구가 필요합니다.  **모델의 신뢰도 및 설명 가능성을 높이기** 위해서는 잠재 추론 과정을 직관적으로 시각화하거나, 추론 과정을 설명하는 메커니즘을 개발하는 노력이 필요합니다.  궁극적으로 잠재 추론에 대한 심층적인 이해는 더욱 강력하고 신뢰할 수 있는 LLM 개발을 위한 핵심이 될 것입니다.

#### VQ-VAE Encoding
본 논문에서 제시된 VQ-VAE 인코딩은 추론 과정의 텍스트 토큰을 압축된 잠재 이산 토큰으로 변환하는 핵심 기술입니다. **VQ-VAE(Vector Quantized Variational Autoencoder)**는 입력 시퀀스의 특징을 효율적으로 학습하고, 이를 잠재 공간에 매핑하여 낮은 차원의 표현으로 변환합니다. 이를 통해, **길고 복잡한 추론 과정을 효율적으로 압축**하고, 연산 비용을 절감할 수 있습니다.  **잠재 토큰의 도입은 메모리와 연산 효율성을 향상**시키는 동시에, 모델이 핵심적인 추론 정보에 집중할 수 있도록 합니다.  하지만, **새로운 잠재 토큰에 대한 모델의 적응력**을 높이는 것이 중요한 과제이며, 논문에서는 이를 위해 훈련 중 텍스트 토큰과 잠재 토큰을 무작위로 혼합하는 전략을 제시합니다. 이러한 전략은 새로운 토큰에 대한 빠른 적응을 가능하게 하여 성능 향상에 기여합니다.  결론적으로, VQ-VAE 인코딩은 **추론 효율성과 성능 향상을 동시에 달성**하기 위한 효과적인 방법론으로 평가될 수 있습니다.

#### Hybrid Training
하이브리드 학습이란 다양한 데이터 유형이나 학습 방법을 결합하여 강화된 모델을 만드는 훈련 전략입니다. **본 논문에서는 잠재적 이산 토큰과 텍스트 토큰을 혼합하여 언어 모델 추론 능력을 향상시키는 하이브리드 표현 방식**을 제시합니다. 이는 추론 과정을 효율적으로 축약하고, 계산 비용을 줄이는 효과를 가져옵니다. 하이브리드 데이터를 이용한 학습은 기존 방법보다 뛰어난 성능을 보여주는 반면, **새로운 잠재 토큰에 대한 빠른 적응**을 위해 무작위 대체 전략을 활용합니다. **잠재 토큰의 도입은 추론 과정의 표면적 세부 사항을 압축하고 핵심 정보에 집중**할 수 있게 해줍니다. 이러한 하이브리드 접근 방식은 다양한 벤치마크에서 일관되게 우수한 성능을 보이며, 추론 과정의 길이를 단축하는 데 효과적임을 보여줍니다.

#### Benchmark Results
본 논문의 벤치마크 결과는 제안된 방법의 우수성을 다각적으로 보여줍니다. **다양한 벤치마크 데이터셋에서 일관되게 최고 성능**을 달성하였으며, 특히 수학적 추론 문제에서 **기존 방법 대비 상당한 성능 향상**을 보였습니다.  이는 제안된 방법이 **추론 과정의 효율성을 높이면서 정확도를 개선**했음을 의미합니다.  단순히 성능 향상 뿐 아니라, **토큰 사용량 감소**를 통해 계산 비용 절감 효과도 확인되었는데, 이는 **실제 응용에 있어 중요한 실용적 이점**을 제공합니다.  **다양한 모델 크기와 아키텍쳐에 걸쳐 뛰어난 성능**을 유지한 점은 제안된 방법의 **범용성과 확장성**을 시사합니다.  결론적으로, 제시된 벤치마크 결과는 제안된 방법의 우수성과 실용성을 뒷받침하는 강력한 증거로 볼 수 있습니다.  **향후 연구**는 더욱 다양하고 복잡한 문제들에 대한 추가적인 평가를 통해 제안된 방법의 일반화 성능을 검증하는 데 집중할 수 있을 것입니다.

#### Future of LLMs
LLM의 미래는 **매우 밝지만 불확실성 또한 내포하고 있습니다.**  향후 연구는 더욱 강력하고 효율적인 모델 개발에 집중될 것입니다.  **데이터 효율성 개선**은 필수적이며, 소량의 데이터로도 높은 성능을 발휘하는 모델 개발이 중요해질 것입니다.  **추론 능력 향상**을 위해서는 지식 기반과의 통합 및 추론 과정의 투명성 확보가 중요하며, 이를 위해 **설명 가능한 AI** 기술이 중요한 역할을 할 것입니다. 또한, **윤리적 문제 해결**을 위한 연구도 필수적입니다. 편향성 제거, 악용 방지, 책임 있는 사용에 대한 규정 등이 중요하게 고려되어야 하며, 이를 위한 기술적, 사회적 노력이 병행되어야 합니다.  **다양한 분야와의 융합** 또한 주목할 만합니다.  LLM은 자연어 처리를 넘어 과학, 의료, 교육 등 다양한 분야에 적용될 가능성이 있으며, 이는 혁신적인 발전을 가져올 것입니다.  하지만 이러한 발전을 위한 **안전성 및 보안에 대한 고려**는 잊지 말아야 합니다.  **해킹 및 악용 가능성**, 개인정보 보호 문제 등의 위험성에 대한 철저한 대비가 필요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.03275/x2.png)

> 🔼 그림 3.2는 VQ-VAE의 작동 과정을 보여줍니다.  텍스트 토큰을 입력받아 잠재적 임베딩으로 인코딩하는 인코더(f_enc)와,  이 임베딩을 다시 텍스트 토큰으로 디코딩하는 디코더(f_dec)로 구성됩니다.  VQ-VAE는 코드북이라는 룩업 테이블을 사용하며, 인코딩 과정에서 가장 가까운 이웃을 찾아 코드북의 인덱스를 잠재 토큰(Z)으로 할당합니다.  즉, 잠재 토큰은 코드북 내 임베딩의 인덱스를 나타냅니다.  텍스트 토큰을 압축할 때, 잠재 토큰은 이러한 임베딩의 인덱스를 나타내는 이산형 표현으로 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 3.2: A graphical illustration of our VQ-VAE. fencsubscript𝑓enc{f_{\text{enc}}}italic_f start_POSTSUBSCRIPT enc end_POSTSUBSCRIPT encodes the text tokens into latent embeddings, which are quantized by checking the nearest neighbors in the codebook. fdecsubscript𝑓dec{f_{\text{dec}}}italic_f start_POSTSUBSCRIPT dec end_POSTSUBSCRIPT decodes those quantized embeddings back to text tokens. When applying the VQ-VAE to compress the text tokens, the discrete latent tokens Z𝑍Zitalic_Z are essentially the index of corresponding embeddings in the codebook.
> </details>



![](https://arxiv.org/html/2502.03275/extracted/6181144/plots/entry_1.png)

> 🔼 그림은 논문의 4.3절(어텐션 가중치 분석)에서 나온 것으로,  두 가지 수학 문제에 대한 모델의 어텐션 가중치를 시각적으로 보여줍니다. (a)는 '30의 120%와 20의 130%의 차이는 무엇입니까?'라는 문제에 대한 어텐션 가중치 분포를,  (b)는 마크가 은행 계좌에 50달러를 가지고 있고 하루에 10달러씩 벌어 300달러짜리 자전거를 사려면 며칠 동안 저축해야 하는지를 묻는 문제에 대한 어텐션 가중치 분포를 보여줍니다. 각 그래프는 모델이 문제를 푸는 과정에서 각 단어나 숫자에 얼마나 주의를 기울였는지 나타내며, 특히 숫자와 수학 연산 관련 단어에 대한 어텐션 가중치가 높은 것을 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> (a) Prompt: What is the positive difference between $120%$ of 30 and $130%$ of 20?
> </details>



![](https://arxiv.org/html/2502.03275/extracted/6181144/plots/entry_7746.png)

> 🔼 그림 4.1(b)는 질문과 답변에 대한 어텐션 가중치를 시각화한 것입니다. 질문은 '마크는 은행 계좌에 50달러가 있습니다. 그는 하루에 10달러를 벌어들입니다. 만약 그가 300달러짜리 자전거를 사고 싶다면, 마크는 돈을 얼마나 오래 모아야 합니까?'입니다.  이 그림은 제안된 모델과 기준 모델(CoT)의 어텐션 가중치를 보여줍니다.  특히 숫자(50, 10, 300)와 수학적 연산을 나타내는 단어들에 대한 어텐션 가중치가 제안된 모델에서 더 높다는 것을 보여줍니다. 이는 제안된 모델이 숫자와 연산에 더 집중하여 문제 해결에 효율적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> (b) Prompt: Mark has $50 in his bank account. He earns $10 per day at his work. If he wants to buy a bike that costs $300, how many days does Mark have to save his money?
> </details>



![](https://arxiv.org/html/2502.03275/extracted/6181144/plots/maze_env.png)

> 🔼 그림 4.1은 본 논문에서 제안하는 잠재 토큰 접근 방식과 기존의 CoT(Chain-of-Thought) 모델의 어텐션 가중치를 비교하여 보여줍니다.  특히 수학적 연산을 나타내는 숫자와 텍스트 토큰에 대한 어텐션 가중치가 본 논문의 접근 방식에서 더 높다는 것을 보여줍니다.  이는 잠재 토큰이 모델이 수학 문제 풀이에 중요한 부분에 집중할 수 있도록 도와주는 역할을 함을 시사합니다.  즉, 잠재 토큰을 사용함으로써 모델이 불필요한 정보에 대한 어텐션을 줄이고, 수학적 연산에 필요한 정보에 집중하여 정확도를 향상시킨다는 것을 보여주는 결과입니다.
> <details>
> <summary>read the caption</summary>
> Figure 4.1: Comparing with the CoT model, our latent approach have high attention weights on numbers and text tokens representing mathematical operations.
> </details>



![](https://arxiv.org/html/2502.03275/extracted/6181144/plots/maze_traj1.png)

> 🔼  그림 A.1은 논문에서 제시된 키 찾기 미로 환경의 한 예시를 보여줍니다.  3x3 크기의 방들이 연결되어 있으며, 각 방에는 키 또는 문이 배치되어 있습니다. 에이전트는 미로의 시작 위치에서 출발하여 특정 목표 위치에 도달해야 합니다.  목표 위치에 도달하기 위해서는, 각 방에 배치된 색깔별 키를 찾아 같은 색깔의 문을 열어야 합니다. 에이전트는 한 번에 하나의 키만 들고 이동할 수 있습니다. 따라서 에이전트는 키를 찾고 문을 여는 순서를 계획적으로 결정해야 목표에 도달할 수 있습니다. 이 미로 환경은 에이전트의 계획 및 추론 능력을 평가하기 위한 복잡한 퍼즐로, 단순한 경로 탐색 이상의 고차원적인 사고 능력을 요구합니다.
> <details>
> <summary>read the caption</summary>
> Figure A.1: An example of the keys-finding maze environment.
> </details>



![](https://arxiv.org/html/2502.03275/extracted/6181144/plots/maze_traj2.png)

> 🔼 그림 A.2는 키를 찾는 미로 환경에서 에이전트의 최적 경로를 보여줍니다. (a) 단계는 에이전트가 파란색 키를 줍는 것을 보여주고, (b) 단계는 파란색 문을 열어 빨간색 키를 얻는 것을 보여주며, (c) 단계는 에이전트가 빨간색 키를 들고 빨간색 문으로 이동하는 것을 보여주고, (d) 단계는 에이전트가 빨간색 문을 열고 목표에 도달하는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (a) Phase 1
> </details>



![](https://arxiv.org/html/2502.03275/extracted/6181144/plots/maze_traj3.png)

> 🔼 그림은 키 찾기 미로 환경의 두 번째 단계를 보여줍니다. 에이전트는 파란색 키를 획득하여 파란색 문을 열고 빨간색 키를 얻습니다. 에이전트는 미로에서 목표 지점까지 이동하는 최적의 경로를 찾기 위해 키를 수집하고 문을 여는 계획을 세웁니다.
> <details>
> <summary>read the caption</summary>
> (b) Phase 2
> </details>



![](https://arxiv.org/html/2502.03275/extracted/6181144/plots/maze_traj4.png)

> 🔼 그림은 키 찾기 미로 환경에서 에이전트의 최적 경로를 보여줍니다. 그림 (c)는 에이전트가 빨간색 키를 얻기 위해 파란색 문을 열고, 다음 단계에서 빨간색 문을 여는 단계를 보여줍니다. 이는 에이전트가 목표에 도달하기 위해 복잡한 계획을 수립하고 실행하는 능력을 평가하기 위한 합성 데이터셋의 일부입니다.
> <details>
> <summary>read the caption</summary>
> (c) Phase 3
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Parameter | Value |
|---|---| 
| Number of Layers (Transformer Blocks) | 12 |
| Hidden Size (Embedding Size) | 768 |
| Number of Attention Heads | 12 |
| Vocabulary Size | 50,257 |
| Total Number of Parameters | 117 million |{{< /table-caption >}}
> 🔼 표 4.2는 다양한 수학적 추론 벤치마크에서 제안된 잠재적 접근 방식이 기준 모델들을 능가함을 보여줍니다. 모델들은 MetaMathQA(Yu et al., 2023) 데이터셋으로 미세 조정되었습니다. Math와 GSM8K는 MetaMathQA를 생성하는 데 사용되었으므로 도메인 내 데이터셋이며, 다른 데이터셋들은 도메인 외부 데이터셋입니다. 굵은 글씨는 최고의 결과를, 밑줄은 두 번째로 좋은 결과를 나타냅니다. ↑↑+는 두 번째로 좋은 결과와 비교한 성능 향상을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 4.2:  Our latent approach outperforms the baselines on various types of mathematical reasoning benchmarks. The models are fine-tuned on the MetaMathQA (Yu et al., 2023) dataset. The Math and GSM8K are in-domain datasets since they are used to generate MetaMathQA, while the others are out-of-domain. Bold: best results. Underscore: second best results. ↑↑\uparrow↑ +:  Performance gain compared with the second best result.
> </details>

{{< table-caption >}}
X=P⊕C⊕S | input text sample where ⊕ means concatenation
---|---|---
P | prompt of length t<sub>p</sub>
p<sub>i</sub> | the i-th token of prompt (in text)
C | reasoning trace of length t<sub>c</sub>
c<sub>i</sub> | the i-th token of trace (in text)
S | solution of length t<sub>s</sub>
s<sub>i</sub> | the i-th token of solution (in text)
Z | the complete latent reasoning traces of length t<sub>z</sub>
z<sub>i</sub> | the i-th token of latent trace
r=t<sub>c</sub>/t<sub>z</sub> | compression rate
m | number of trace tokens to be replaced by latent tokens during training
̃X | modified input with mixed text and latent tokens
ℰ | codebook of VQ-VAE
e<sub>i</sub> | the i-th vector in the codebook, which corresponds to the i-th latent token
d | dimension of e<sub>i</sub>s
𝒱 | vocabulary of text tokens
L | chunk size
f<sub>enc</sub>(⋅) | encodes a chunk of L text tokens to L/r embedding vectors
X̄=x̄<sub>1</sub>,…,x̄<sub>L/r</sub> | embedding vectors of X outputted by f<sub>enc</sub>(⋅)
q(⋅) | quantization operator that replaces, e.g., x̄<sub>1</sub> by its nearest neighbor in ℰ:
g(⋅) | maps prompt to a d-dimensional embedding vector
f<sub>dec</sub>(⋅,⋅) | decodes L/r quantized embedding vectors in ℰ back to text tokens, conditioning on prompt embedding generated by g(⋅){{< /table-caption >}}
> 🔼 표 4.3은 각 모델이 생성한 응답의 토큰 수를 보여줍니다. 본 논문의 제안된 방법은 CoT 기준 대비 평균적으로 응답 길이가 17% 감소했으며, 표 4.2에서 확인할 수 있듯이 최종 성능 면에서도 CoT를 능가했습니다. iCoT는 제안된 방법보다 짧은 응답을 생성하지만, 표 4.2에서 알 수 있듯이 성능은 현저히 떨어집니다. ↓ 기호는 CoT 대비 토큰 길이 감소율을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 4.3: The average number of tokens in the generated responses. Compared with the CoT baseline, our latent approach achieves an 17%percent1717\%17 % reduction in response length on average, while surpassing it in final performance according to Table 4.2. The iCoT method generates shorter responses than our approach, yet performs significantly worse, see Table 4.2. ↓↓\downarrow↓ -: Trace length reduction rate compared with CoT.
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
{{< /gallery >}}