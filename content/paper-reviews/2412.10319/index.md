---
title: "SCBench: A KV Cache-Centric Analysis of Long-Context Methods"
summary: "SCBench는 멀티턴 및 멀티리퀘스트 시나리오에서 장문 맥락 메서드를 평가하는 새로운 벤치마크입니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Microsoft Corporation",]
showSummary: true
date: 2024-12-13
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.10319 {{< /keyword >}}
{{< keyword icon="writer" >}} Yucheng Li et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-16 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.10319" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.10319" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/scbench-a-kv-cache-centric-analysis-of-long" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

**장문 맥락 LLM은 긴 텍스트를 처리하지만 추론에 필요한 계산 및 메모리 비용이 많이 듭니다.** 기존 벤치마크는 단일 요청에 중점을 두고 실제 애플리케이션에서의 KV 캐시 재사용을 무시하여 문제가 됩니다. **KV 캐시 재사용은 vLLM 및 SGLang과 같은 프레임워크와 OpenAI, Microsoft, Google, Anthropic과 같은 LLM 제공업체에서 널리 사용**됩니다. 기존 벤치마크는 멀티턴 및 멀티리퀘스트 시나리오에서 장문 맥락 메서드를 완전히 평가하지 못합니다. **멀티턴 대화 및 멀티단계 추론에서 컨텍스트가 여러 턴 또는 요청에 걸쳐 공유**될 때 KV 캐시 재사용이 중요해집니다. 하위 O(n) 메모리 방식은 이러한 시나리오에서 어려움을 겪습니다. 이러한 문제는 이전 정보의 압축으로 인해 후속 쿼리에 대한 응답이 어려워진다는 보고로 이어졌습니다. 이러한 한계를 해결하기 위해 **실제 장문 맥락 시나리오를 반영하는 포괄적인 벤치마크가 필요**합니다. 

SCBench는 **멀티라운드 및 멀티리퀘스트 시나리오를 포함하는 현실적인 KV 캐시 재사용**을 평가합니다. 이 벤치마크는 문자열 검색, 의미 검색, 전역 정보, 멀티태스킹과 같은 **네 가지 주요 장문 맥락 기능을 평가**합니다. 또한 두 가지 컨텍스트 공유 모드인 멀티턴 및 멀티리퀘스트를 통합합니다. SCBench는 Llama, Qwen, GLM과 같은 8개의 오픈 소스 장문 맥락 LLM과 Codestal Mamba, Jamba와 같은 게이트 선형 RNN을 포함하여 13개의 다른 장문 맥락 메서드를 평가합니다. **KV 캐시 생성, 압축, 검색 및 로드의 네 가지 핵심 단계로 분류**된 이러한 메서드를 분석합니다. SCBench를 통해 연구자들은 **다양한 희소성 기법, 작업 복잡성 및 멀티턴 상호 작용의 영향에 대한 중요한 통찰력**을 얻을 수 있습니다. 이는 궁극적으로 실제 애플리케이션에서 장문 맥락 LLM의 효율성을 개선하고 향후 아키텍처 설계에 대한 정보를 제공하는 것을 목표로 합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} O(n) 메모리 방식은 장문 디코딩에 필수적이며, 하위 O(n) 방식은 멀티턴 성능이 저하됩니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 희소 인코딩은 멀티리퀘스트 시나리오에서 효과적이며 동적 희소성이 고정 패턴보다 우수합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 장문 생성은 중요도 분포 변화로 인해 성능 저하가 발생할 수 있습니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**LLM 연구자들에게 SCBench는 장문 맥락 방법 평가를 위한 중요한 벤치마크를 제공**합니다. **멀티턴 및 멀티리퀘스트 시나리오에서 KV 캐시 재사용에 중점**을 두어 기존 벤치마크의 한계를 해결합니다. 이를 통해 현실적인 애플리케이션을 위한 장문 맥락 모델의 성능에 대한 **새로운 통찰력을 제공**하고, 장문 맥락 LLM의 **효율적인 개발 및 배포**를 위한 귀중한 도구가 됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.10319/x1.png)

> 🔼 이 그림은 KV 캐시의 수명 주기를 보여줍니다. 기존 벤치마크는 단일 요청에 중점을 두는 반면 실제 애플리케이션에서는 여러 요청에 걸쳐 KV 캐시를 재사용합니다. SCBench는 KV 캐시 생성, 압축, 검색 및 로드의 네 가지 단계로 장문 컨텍스트 메서드를 분류합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1:  KV Cache lifecycle. Prior benchmarks focus on single-request, while real-world applications reuse KV cache across requests. We propose SCBench and categorize long-context methods into KV Cache Generation, Compression, Retrieval, and Loading from a KV-cache-centric perspective.
> </details>





{{< table-caption >}}
| Methods | Taxonomy | Stage | P-stage Efficient | D-stage Efficient | KV Cache Size | Prefilling Complexity | Decoding Complexity | 
|---|---|---|---|---|---|---|---| 
| Codestral Mamba (team, 2024) | Gated Linear RNN | ❶ | ✓ | ✓ | O(k) | O(kn) | O(km) | 
| Jamba (Lieber et al., 2024) | Gated Linear RNN + Full Attention | ❶ | ✓ | ✓ | O(n) | O(n²) | O(nm) | 
| LLMLingua-2 (Pan et al., 2024) | Prompt Compression | ❶ | ✓ | ✗ | O(αn) | O(α²n²) | O(αnm) | 
| A-shape (Xiao et al., 2024b) | Sparse Attention | ❶ | ✓ | ✗ | O(n) | O(kn) | O(nm) | 
| Tri-shape | Sparse Attention | ❶ | ✓ | ✗ | O(n) | O(kn) | O(nm) | 
| MInference (Jiang et al., 2024) | Sparse Attention | ❶ | ✓ | ✗ | O(n) | O(kn) | O(nm) | 
| StreamingLLM (Xiao et al., 2024b) | KV Cache Dropping | ❷ | ✗ | ✓ | O(k) | O(n²) | O(km) | 
| SnapKV (Li et al., 2024c) | KV Cache Dropping | ❷ | ✗ | ✓ | O(k) | O(n²) | O(km) | 
| PyramidKV (Cai et al., 2024) | KV Cache Dropping | ❷ | ✗ | ✓ | O(k) | O(n²) | O(km) | 
| KIVI (Liu et al., 2024e) | KV Cache Quantitation | ❷ | ✗ | ✓ | O(n) | O(n²) | O(nm) | 
| CacheBlend (Yao et al., 2024a) | KV Cache Retrieval | ❸ | ✓ | ✗ | O(n) | O(n²) | O(nm) | 
| Quest (Tang et al., 2024) | KV Cache Loading | ❹ | ✗ | ✓ | O(n) | O(n²) | O(km) | 
| RetrievalAttention (Liu et al., 2024b) | KV Cache Loading | ❹ | ✗ | ✓ | O(n) | O(n²) | O(km) |{{< /table-caption >}}

> 🔼 이 표는 SCBench에서 평가된 다양한 장문 맥락(long-context) 메서드들을 보여줍니다. 입력 프롬프트의 토큰 크기를 *n*, 생성 토큰 크기를 *m*으로 표시하며, *n*은 *m*보다 훨씬 큽니다(*n* >> *m*). 표는 각 메서드의 분류, pre-filling 및 decoding 단계의 효율성, KV 캐시 크기, pre-filling 및 decoding 단계의 계산 복잡도, 그리고 pre-filling 및 decoding 단계에서 효율적인 연산 수행 여부를 보여줍니다. 게이트 선형 RNN, SSM-어텐션 하이브리드 모델, Sparse Attention, KV 캐시 삭제, KV 캐시 양자화, KV 캐시 검색, KV 캐시 로딩 등 다양한 메서드들이 포함되어 있습니다. 이 표는 논문의 섹션 2에서 다양한 장문 맥락 메서드에 대한 KV 캐시 중심적 관점을 소개하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 1: We evaluated long-context methods on SCBench, where n𝑛nitalic_n represents the token size of the input prompt and m𝑚mitalic_m represents the generation token size, with n≫mmuch-greater-than𝑛𝑚n\gg mitalic_n ≫ italic_m.
> </details>





### In-depth insights


#### KV Cache Focus
**KV 캐시**에 중점을 둔 접근 방식은 **긴 컨텍스트 LLM**의 성능과 효율성을 향상시키는 데 매우 중요합니다. KV 캐시는 이전 토큰의 표현을 저장하여 모델이 긴 텍스트를 효과적으로 처리할 수 있도록 합니다. **캐시 생성, 압축, 검색 및 로딩**을 포함한 KV 캐시 수명 주기의 각 단계를 최적화하면 LLM의 기능을 크게 향상시킬 수 있습니다. 예를 들어, 효율적인 캐시 생성 기술은 초기 처리 비용을 줄이는 반면 지능적인 압축 방법은 메모리 사용량을 최소화합니다. 또한 효과적인 검색 및 로딩 전략은 모델이 이전 정보에 빠르게 액세스하여 신속한 응답을 생성할 수 있도록 합니다. 이러한 모든 최적화는 전체적으로 더 빠른 추론, 더 긴 컨텍스트 처리 및 더 나은 성능으로 이어집니다.

#### SCBench Design
**SCBench**는 **KV 캐시** 중심의 롱 컨텍스트 메서드 평가를 위한 벤치마크입니다. **멀티 라운드 및 멀티 요청 시나리오**에서 KV 캐시 **재사용**에 중점을 두어 실제 애플리케이션을 더 잘 반영합니다. 문자열 검색, 의미 검색, 전역 정보 처리, 멀티태스킹 등 네 가지 주요 **롱 컨텍스트 기능**을 평가하는 12가지 작업을 포함합니다. 벤치마크는 **멀티 턴 모드와 멀티 요청 모드**의 두 가지 공유 컨텍스트 모드에서 이러한 작업을 평가합니다. 이 설계를 통해 SCBench는 다양한 시나리오에서 롱 컨텍스트 메서드의 강점과 약점에 대한 **포괄적인 분석**을 제공하여 실제 환경에서 성능을 보다 정확하게 평가할 수 있도록 합니다.

#### Long-Ctx Analysis
**긴 컨텍스트 분석(Long-Ctx Analysis)**은 대규모 언어 모델(LLM)에서 긴 입력 시퀀스를 처리하는 능력에 대한 심층적인 조사입니다. 이 분석은 **KV 캐시 사용 최적화**에 중점을 두어 컨텍스트 창을 확장하는 방법을 모색합니다. **핵심 과제**는 긴 시퀀스의 계산 및 메모리 비용 증가를 해결하는 것입니다. Long-Ctx Analysis는 **다양한 전략**을 평가합니다. 여기에는 **희소 주의 기법**과 KV 캐시 압축, 검색 및 로드와 같은 메모리 관리 전략이 포함됩니다. 또한 멀티턴 대화 및 다중 요청과 같은 **공유 컨텍스트**에서 이러한 방법의 성능을 분석하여 성능 저하 문제를 조사합니다. 목표는 서로 다른 긴 컨텍스트 방법을 비교하여 다양한 시나리오에서 **장점과 단점**을 강조하는 것입니다. 또한 이 분석은 모델이 긴 컨텍스트 내에서 **글로벌 정보를 효과적으로 처리**하는 능력을 고려합니다. 궁극적으로 Long-Ctx Analysis는 성능을 개선하고 메모리 효율적인 **긴 컨텍스트 LLM 설계를 위한 통찰력**을 제공하는 것을 목표로 합니다.

#### Multi-Turn Limits
**멀티턴 대화에서의 한계점**은 현재 LLM 연구의 중요한 과제입니다. 컨텍스트 창 크기 제한, 이전 대화 기억 유지 어려움, 누적되는 계산 비용 증가 등 여러 요인이 복합적으로 작용합니다. 특히, 긴 대화에서 **정보 손실**이 발생하고, **일관성 유지**가 어려워지며, **새로운 정보 통합** 능력도 저하됩니다. 또한, **대화 맥락에 따른 반응 생성** 능력과 **사용자 의도 파악** 능력 향상도 중요한 연구 주제입니다. 이러한 한계를 극복하기 위해 다양한 연구가 진행 중이며, 메모리 효율적인 아키텍처, 지식 증강 기법, 효과적인 컨텍스트 관리 전략 등이 활발히 개발되고 있습니다.

#### Sparsity Insights
**희소성**은 길고 복잡한 입력을 처리할 때 계산 및 메모리 효율성을 개선하는 데 중요한 역할을 합니다. **희소 인코딩**을 사용하면 전체 입력을 처리하지 않고도 중요한 정보를 포착할 수 있습니다. 디코딩 단계에서 **희소성**을 적용하면 생성된 텍스트의 품질과 일관성이 떨어질 수 있습니다. **동적 희소성**은 정적 패턴보다 유연성이 높으며 성능을 향상시키는 데 도움이 될 수 있습니다. 하이브리드 아키텍처에서 계층 수준 희소성을 사용하면 메모리 사용량을 줄이면서 성능을 향상시킬 수 있습니다. 다중 요청 시나리오의 경우 입력에서 중요한 정보를 추출하는 **희소 인코딩**이 유용할 수 있습니다. 하지만 **희소 디코딩**은 각 요청에 대해 중요한 토큰이 다를 수 있으므로 성능이 떨어질 수 있습니다. 따라서 희소성 기반 방법의 효율성과 효과를 최적화하려면 인코딩 및 디코딩 단계에서 **희소성 패턴**을 신중하게 설계하는 것이 중요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.10319/x2.png)

> 🔼 이 그림은 두 가지 일반적인 공유 컨텍스트 패턴, 즉 다중 턴 모드와 힌트된 KV 캐시 다중 요청 모드를 보여줍니다. 다중 턴 모드에서 컨텍스트는 단일 세션 내에 캐시되고, 힌트된 KV 캐시 다중 요청 모드에서는 여러 세션에 걸쳐 캐시됩니다. 각 모드는 공유 컨텍스트와 여러 후속 쿼리로 구성됩니다.
> <details>
> <summary>read the caption</summary>
> (a) Two Shared Context Modes
> </details>



![](https://arxiv.org/html/2412.10319/x3.png)

> 🔼 SCBench는 공유 컨텍스트와 다중 라운드 상호 작용에 중점을 둔 효율적인 긴 컨텍스트 방법을 평가하도록 설계된 벤치마크입니다. 그림 2b에서 볼 수 있듯이, SCBench는 공유 컨텍스트 모드 두 가지에서 12가지 작업에 대한 네 가지 주요 긴 컨텍스트 기능을 평가합니다. 각 테스트 예시에는 공유 컨텍스트와 여러 후속 쿼리가 포함됩니다. 네 가지 긴 컨텍스트 기능에는 문자열 검색 기능(NIAH 및 Multi-NIAH와 같은 이전 검색 작업을 확장하여 포괄적인 문자열 검색 작업 3가지를 도입), 의미 검색 기능(다양한 도메인에서 다양한 의미 검색 시나리오를 고려하여 네 가지 고유한 테스트 구축), 글로벌 정보 기능(다중 샷 인컨텍스트 학습, 요약 및 긴 배열 통계와 같은 세 가지 작업을 통해 긴 컨텍스트 LLM의 글로벌 정보 처리 및 집계 기능 평가), 다중 작업 기능(NIAH가 포함된 RepoQA 및 KV 검색이 포함된 요약이라는 두 가지 작업을 통해 공유 긴 컨텍스트 입력으로 여러 작업을 처리하는 LLM의 기능 평가)이 포함됩니다. 또한 벤치마크에는 다중 턴 모드와 다중 요청 모드라는 두 가지 일반적인 공유 컨텍스트 모드가 포함됩니다.
> <details>
> <summary>read the caption</summary>
> (b) Overview of SCBench
> </details>



![](https://arxiv.org/html/2412.10319/x4.png)

> 🔼 이 그림은 두 부분으로 구성되어 있습니다. (a)는 두 가지 일반적인 공유 컨텍스트 패턴, 즉 다중 턴 모드와 힌트된 KV 캐시 다중 요청 모드를 보여줍니다. 다중 턴 모드에서는 컨텍스트가 단일 세션 내에 캐시되고, 힌트된 KV 캐시 다중 요청 모드에서는 여러 세션에 걸쳐 캐시됩니다. (b)는 벤치마크에서 다루는 작업과 시나리오의 개요를 보여줍니다. 문자열 검색, 의미 검색, 전역 정보, 다중 작업의 네 가지 범주의 장문 컨텍스트 기능과 두 가지 공유 컨텍스트 모드(다중 턴 및 다중 요청)가 포함됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Long-context tasks often involve contexts sharing, e.g., multi-turn dialogues, multi-step reasoning, and repository-level tasks. (a) Illustration of two common shared-context patterns. (b) Overview of tasks and scenarios covered by our benchmark, encompassing four categories of long-context abilities and two shared-context modes.
> </details>



![](https://arxiv.org/html/2412.10319/x5.png)

> 🔼 이 그림은 다양한 장문 컨텍스트 기법들이 여러 요청에 걸쳐 어떤 성능 추세를 보이는지 나타냅니다. 디코딩 시 O(n) 메모리 비용이 드는 기법들은 요청이 증가함에 따라 성능이 향상되는 경향이 있습니다. 반대로, 디코딩 시 sub-O(n) KV 캐시를 사용하는 기법들, 예를 들어 KV 캐시 삭제 기법들은 첫 번째 요청에서만 좋은 성능을 보입니다.
> <details>
> <summary>read the caption</summary>
> (a) Performance Across Different Requests
> </details>



![](https://arxiv.org/html/2412.10319/x6.png)

> 🔼 이 그림은 다양한 롱 컨텍스트 메서드가 SCBench에서 여러 롱 컨텍스트 기능(문자열 검색, 의미 검색, 전역 정보, 멀티태스킹)에서 어떻게 수행되는지 보여줍니다. 모든 롱 컨텍스트 메서드는 검색 기능에서 어느 정도 성능 저하를 보이는 반면, 전역 정보 처리 기능에서는 성능을 대체로 유지합니다.
> <details>
> <summary>read the caption</summary>
> (b) Performance in Different Abilities
> </details>



![](https://arxiv.org/html/2412.10319/x7.png)

> 🔼 SCBench 성능 결과에 대한 개요입니다. (a)는 여러 요청에 걸친 다양한 장문 맥락 방식의 성능 추세를 보여줍니다. 디코딩 시 O(n) 메모리 비용이 드는 방식은 요청이 증가함에 따라 성능이 향상되는 것을 보여줍니다. 반대로, KV 캐시 삭제 방식과 같이 sub-O(n) KV 캐시를 디코딩에 사용하는 방식은 첫 번째 요청에서만 좋은 성능을 보입니다. (b)는 다양한 장문 맥락 기능 작업에서 서로 다른 장문 맥락 방식의 구체적인 성능을 보여줍니다. 평가된 모든 장문 맥락 방식은 검색 기능에서 약간의 손실을 보이지만, 전역 정보 처리 기능은 대체로 유지합니다.   sub-O(n) 방식은 여러 차례의 디코딩에서 비실용적이며, O(n) 메모리를 가진 희소 인코딩이 여러 쿼리에서 전체 어텐션 정확도에 근접할 수 있음을 보여줍니다.  O(n) 메모리 방식은 정확한 일치 검색 작업에 필수적입니다. 모든 장문 맥락 방식은 예산이 감소함에 따라 성능이 저하되지만, sub-O(n) 메모리 방식은 더 큰 성능 저하를 보입니다. 장문 생성 시나리오에서는 분포 변화 문제가 발생합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Overview of performance results for SCBench. (a) Performance trends of various long-context methods across multiple requests. Methods with O⁢(n)𝑂𝑛O(n)italic_O ( italic_n ) memory cost in decoding show improving performance as requests increase. In contrast, methods with sub-O⁢(n)𝑂𝑛O(n)italic_O ( italic_n ) KV cache in decoding, like KV cache dropping methods, perform well only in the first request. (b) Specific performance of different long-context methods across various long-context capability tasks. All evaluated long-context methods exhibit some loss in Retrieval capability while largely maintaining Global Information processing capability.
> </details>



![](https://arxiv.org/html/2412.10319/x8.png)

> 🔼 이 그림은 다양한 압축률에서 여러가지 Long-context 메서드의 성능을 Llama-3.1-8B 모델을 사용하여 SCBench에서 평가한 결과를 보여줍니다. 압축률이 낮을수록(예: 1/32) 메모리 사용량은 줄어들지만 성능 저하가 더 커집니다. 반대로, 압축률이 높을수록(예: 1) 성능은 좋아지지만 메모리 사용량은 늘어납니다. 이 그림은 압축률과 성능 사이의 trade-off 관계를 보여주며, MInference와 같이 더 정확한 sparse 메서드는 더 높은 압축률에서도 좋은 성능을 유지할 수 있음을 보여줍니다. 또한, RetreivalAttention 및 KIVI와 같은 O(n) 메모리를 유지하는 메서드는 높은 압축률에서도 상대적으로 높은 성능을 유지함을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Performance of various long-context methods at different compression rates on SCBench using Llama-3.1-8B (Dubey et al., 2024).
> </details>



![](https://arxiv.org/html/2412.10319/x9.png)

> 🔼 이 그림은 A-shape와 Tri-shape라는 두 가지희소 어텐션 방법의 프레임워크를 보여줍니다. A-shape는 싱크 토큰과 로컬 윈도우 영역을 유지하는 반면, Tri-shape는 마지막 윈도우 쿼리 영역도 유지하여 사전 채우기 단계에서 삼각형 패턴을 형성합니다. 이러한 추가는 첫 번째 턴 성능을 향상시키는 것으로 나타났습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: The sparse attention methods framework.
> </details>



![](https://arxiv.org/html/2412.10319/x10.png)

> 🔼 이 그림은 문자열 검색 능력에 대한 다양한 장문 맥락 메서드의 성능을 여러 턴에 걸쳐 보여줍니다. 결과는 테스트된 모든 기본 LLM에서 평균을 낸 값입니다. 다중 작업 작업에 대한 결과는 그림 10에 나와 있으며, 자세한 내용은 4절에 설명되어 있습니다. 이 그림은 다양한 장문 맥락 방법의 성능이 쿼리가 반복됨에 따라 어떻게 변화하는지, 특히 문자열 검색 작업에서 보여줍니다. O(n) 메모리 방법이 일반적으로 여러 턴에 걸쳐 더 나은 성능을 유지하는 반면, sub-O(n) 방법은 성능이 저하되는 경향이 있음을 알 수 있습니다. 이 그림은 장문 맥락 방법의 강점과 약점에 대한 추가적인 맥락을 제공하며, 특히 메모리 효율성과 다중 턴 성능 간의 균형을 맞추는 방법에 중점을 둡니다.
> <details>
> <summary>read the caption</summary>
> (a) String Retrieval
> </details>



![](https://arxiv.org/html/2412.10319/x11.png)

> 🔼 이 그림은 다양한 장문 맥락 메서드들이 시맨틱 검색 능력에서 여러 턴에 걸쳐 어떤 성능을 보이는지 비교하고 있습니다. 결과는 테스트된 모든 기본 LLM에 대해 평균화되었습니다.
> <details>
> <summary>read the caption</summary>
> (b) Semantic Retrieval
> </details>



![](https://arxiv.org/html/2412.10319/x12.png)

> 🔼 이 그림은 다양한 장문 컨텍스트 기법들이 전역 정보 처리 능력을 얼마나 잘 수행하는지 비교하고 있습니다. 여러 턴에 걸쳐 성능을 비교하여, 동적 희소 어텐션 기법(MInference)이 전역 정보를 잘 활용하는 작업에서 우수한 성능을 보이는 반면, KV 캐시 압축 기법(StreamingLLM, SnapKV)은 성능이 저하되는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> (c) Global Information
> </details>



![](https://arxiv.org/html/2412.10319/x13.png)

> 🔼 이 그림은 다양한 작업과 턴에 따른 여러 장문 컨텍스트 메서드의 성능을 보여줍니다. 문자열 검색, 의미 검색, 전역 정보와 같은 작업 유형별로 하위 그림이 나뉩니다. 각 하위 그림은 다양한 장문 컨텍스트 메서드(FullAttention, Tri-shape, MInference, A-shape, StreamingLLM, SnapKV, LLMLingua-2, Quest)의 5개 턴에 걸친 성능 변화를 보여줍니다. 결과는 테스트된 모든 기본 LLM에서 평균을 낸 것입니다. 멀티태스킹 작업의 결과는 그림 10에 나와 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Performance of different long-context methods across various tasks and turns. The results for multi-tasking tasks are shown in Fig. 10, and the results are averaged across all tested base LLMs.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Task | Description | Capability | Avg. Input Length | Avg. Output Length | #Sessions / #Turns |
|---|---|---|---|---|---| 
| Retr.KV | Key-value retrieval from many key-value pairs | String Retrieval | 125K | 943 | 100/500 |
| Retr.Prefix-Suffix | Find string with specific prefix and suffix in a dict | String Retrieval | 112K | 914 | 100/500 |
| Retr.MultiHop | Tracking variables assignment in a long input | String Retrieval | 124K | 410 | 90/450 |
| Code.RepoQA | Functions retrieval from a GitHub repo | Semantic Retrieval | 65K | 6,058 | 88/440 |
| En.QA | English Question Answering | Semantic Retrieval | 198K | 272 | 69/351 |
| Zh.QA | Chinese Question Answering | Semantic Retrieval | 1.5M | 322 | 35/189 |
| En.MultiChoice | English Multi-Choice Questions | Semantic Retrieval | 188K | 215 | 58/299 |
| Math.Find | Math computation tasks within long sequence arrays | Global Information | 120K | 172 | 100/240 |
| ICL.ManyShot | Hundreds-shot in-context learning | Global Information | 22K | 975 | 54/270 |
| En.Sum | Summarize a doc given multiple docs as input | Global Information | 104K | 1,170 | 79/350 |
| Mix.Sum+NIAH | Multi-tasking of En.Sum and Needle in A Haystack | Multi-tasking | 105K | 3,441 | 70/560 |
| Mix.RepoQA+KV | Multi-tasking of RepoQA and KV retrieval | Multi-tasking | 68K | 5,318 | 88/704 |
| **Total** | - | - | **227K** | **1,684** | **931/4,853** |{{< /table-caption >}}
> 🔼 SCBench 벤치마크에 포함된 작업들의 개요를 보여주는 표입니다. 각 작업에 대한 설명, 측정되는 능력, 평균 입력 길이, 평균 출력 길이, 세션 수 및 턴 수가 표시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Overview of SCBench tasks.
> </details>

{{< table-caption >}}
| Task | Source | Configuration | Example |
|---|---|---|---| 
| Retr.KV | Lost in the Middle <br> (Liu et al., 2024d) | num kv pairs = 2500 <br> len of key & value = 36 <br> metric = Accuracy | Input: {`<key #1>`: `<value #1>`, …, `<key #100>`: `<value #100>`} <br> Turn 1: The value of the `<key #1>` is? Answer 1: …`<value #1>`… <br> Turn 2: The value of the `&lt;key #20&gt;` is? Answer 2: …`&lt;value #20&gt;`… <br> Turn 3: The value of the `&lt;key #40&gt;` is? Answer 3: …`&lt;value #40&gt;`… | 
| Retr.Prefix-Suffix | Ours | size of dict = 6000 <br> len of string = [65, 123) <br> metric = Accuracy | Input: Dictionary = [`<str #1>`, `<str #2>`, …, `<str #100>`] <br> Turn 1: Prefix: `<px #1>`; Suffix: `<sx #1>`. The word with both prefix and suffix from the dict is? Answer: `<str>` <br> Turn 2: Prefix: `<px #2>`; Suffix: `<sx #2>`. Answer: `<str>` | 
| Retr.MultiHop | RULER <br> (Hsieh et al., 2024) | num chains = 2 <br> num hops = 2 <br> metric = Accuracy | Input: VAR `X1` = `12345` …… VAR Y1 = 54321 …..`<noise>` <br> VAR `X2` = X1 …… VAR Y2 = Y1 ……`<noise>` <br> VAR `X3` = X2 …… VAR Y3 = Y2 ……`<noise>` <br> Turn 1: Variables that are assigned to `12345`? Answer 1: `X1 X2 X3` <br> Turn 2: Variables that are assigned to 54321? Answer 1: Y1 Y2 Y3 | 
| Code.RepoQA | RepoQA <br> (Liu et al., 2024c) | func description from GPT-4 <br> metric = Pass@1 | Input: `<func 1>` + `<func 2>` + … + `<func 100>` <br> Turn 1: `<description of func 1>`. Answer 1: `<func 1>` <br> Turn 2: `<description of func 20>`. Answer 2: `<func 20>` | 
| En.QA <br> Zh.QA | InfiniteBench <br> (Zhang et al., 2024a) | ground_truth from human <br> metric = Accuracy | Input: Read the book below and answer a question. `<context>` <br> Turn 1: `<question>` Be very concise. Answer 1: …`<ans>`… <br> Turn 2: `<question>` Be very concise. Answer 2: …`<ans>`… | 
| En.MultiChoice | InfiniteBench <br> (Zhang et al., 2024a) | ground_truth from human <br> metric = Accuracy | Input: Read the book and answer the question. `<context>` <br> Turn 1: `<question>` + `<Option A,B,C,D>`. Answer 1: …`<ans>`… <br> Turn 2: `<question>` + `<Option A,B,C,D>`. Answer 2: …`<ans>`… | 
| Math.Find | Ours | len_array=30000 <br> num_digits=3 <br> metric = Accuracy | Input: `<a large array of number>` <br> Turn 1: The `max number` in the array is? Answer 1: …`<max number>`… <br> Turn 2: The `max number` in the array is? Answer 2: …`<max number>`… | 
| ICL.ManyShot | ManyShotICL <br> (Srivastava et al., 2023) | num_examples = ~150 <br> Tasks = date, salient, tracking7 <br> metric = Accuracy | Input: ICL Demo. 1 + Demo. 2 + ….. + Demo. 1000 <br> Turn 1: `<question>`. Answer 1: …`<ans>`… <br> Turn 2: `<question>`. Answer 2: …`<ans>`… | 
| En.Sum | Ours | Concatenated arXiv papers <br> ground_truth from GPT-4 <br> num document = ~8 <br> metric = ROUGE | Input: `Doc 1` + Doc 2 + Doc 3 + … + Doc 10. <br> Turn 1: Please summarize `Doc 1`. Answer 1: … `<summary of Doc 1>`… <br> Turn 2: Please summarize Doc 3. Answer 2: … `<summary of Doc 3>`… <br> Turn 3: Please summarize Doc 5. Answer 2: … `<summary of Doc 5>`… | 
| Mix.Sum+NIAH | Ours | num needle = 5 <br> num document = ~8 <br> metric = ROUGE + Acc | Input: `Doc 1` + `<Passkeys>` + Doc 2 + … + `<Passkeys>` + Doc 10. <br> Turn 1: Please summarize `Doc 1`. Answer 1: …`<summary of Doc 1>`… <br> Turn 2: What is the needle? Answer 2: ..`<needle>`… | 
| Mix.RepoQA+KV | Ours | num KV pairs = ~100 <br> metric = Pass@1 + Acc | Input: `<func 1>` + KV pairs + `<func 2>` + … + KV pairs + `<func 100>` <br> Turn 1: `<description of func 1>`. Answer 1: `<func 1>` <br> Turn 2: The value of the `<key #1>` is? Answer 2: …`<value #1>`.. |{{< /table-caption >}}
> 🔼 SCBench의 작업 예시와 설정을 보여주는 표입니다. 질문, 답변, 오답은 각각 다른 색깔로 강조되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Task examples and configurations in SCBench. We use different colors to highlight the questions, answers, and distractors in our examples.
> </details>

{{< table-caption >}}
|Retr.KV|
|---|{{< /table-caption >}}
> 🔼 이 표는 다양한 기본 모델과 두 가지 공유 컨텍스트 모드(멀티턴 및 멀티요청)에서 다양한 장문 컨텍스트 메서드의 SCBench에 대한 평균 성능을 보여줍니다. Llama-3.1-70B, Qwen2.5-32B 및 Llama-3-8B-262K와 같은 기본 모델에 대한 추가 결과는 §D의 표 10을 참조하십시오. 여기서 τ는 목표 압축률을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Average performance of various long-context methods across different base models in two shared context modes on SCBench. For additional results on base models such as Llama-3.1-70B, Qwen2.5-32B, and Llama-3-8B-262K, see Table 10 in §D. Here, τ𝜏\tauitalic_τ denotes the target compression rate.
> </details>

{{< table-caption >}}
| Lost in the Middle |
|---| 
| (Liu et al., 2024d) |{{< /table-caption >}}
> 🔼 이 표는 쿼리 인식 및 비인식 롱 컨텍스트 메서드(SnapKV, Tri-shape, MInference)의 성능 결과를 보여줍니다. 쿼리 인식은 첫 번째 결과에 해당하고, 쿼리 비인식은 두 번째 결과에 해당하며, 밑줄은 쿼리 부재 시 성능 저하를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Results of query-awareness long-context methods. w/ (first) and w/o (later) query.
> </details>

{{< table-caption >}}
| num kv pairs = 2500 |
| --- |
| len of key & value = 36 |
| metric = Accuracy |{{< /table-caption >}}
> 🔼 표 6은 다양한 롱 컨텍스트 벤치마크를 비교하고 있습니다. 평가되는 롱 컨텍스트 기능, 고려되는 요청 유형 및 구현된 사항에 따라 벤치마크를 비교합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Comparison of Long-Context Benchmarks.
> </details>

{{< table-caption >}}
| Retr.Prefix-Suffix |
|---|{{< /table-caption >}}
> 🔼 이 표는 요약 능력을 평가하는 다양한 벤치마크에서 효율적인 장문 컨텍스트 메서드의 성능을 비교합니다. 이전 벤치마크(InfiniteBench 및 LongBench)와 SCBench에서 Llama-3.1-8B-Inst 모델에 대해 A-Shape, Tri-shape, MInference, StreamingLLM, SnapKV, LLMLingua와 같은 여러 메서드의 성능을 비교하여 SCBench가 다중 요청 시나리오에서 장문 컨텍스트 메서드의 약점을 더 잘 식별할 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Comparing the summarization capability of efficient long-context methods on prior benchmarks and our SCBench.
> </details>

{{< table-caption >}}
| Ours |{{< /table-caption >}}
> 🔼 이 표는 다양한 효율적인 장문 맥락 메서드의 검색 능력을 기존 벤치마크(InfiniteBench, LongBench)와 SCBench에서 비교하여 보여줍니다. SCBench는 특히 다중 요청 및 다중 턴 시나리오에서 장문 맥락 방법의 약점을 더 잘 식별할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Comparing the retrieval capability of efficient long-context methods on prior benchmarks and our SCBench.
> </details>

{{< table-caption >}}
| size of dict = 6000 |
|---| 
| len of string = [65, 123) |
| metric = Accuracy |{{< /table-caption >}}
> 🔼 이 표는 SCBench에서 사용되는 다양한 장문 맥락 메서드에 대한 구성을 자세히 설명합니다. SSM(State Space Model), 하이브리드 모델, 희소 주의(Sparse Attention), KV 캐시 압축, 양자화, 검색 및 로딩, 프롬프트 압축을 포함한 여러 범주의 방법에 대한 특정 매개변수와 설정이 표에 요약되어 있습니다. 각 방법에 대한 구성 세부 정보에는 청크 크기, 커널 크기, 은닉 크기, 레이어 수, 주의 헤드 수, 희소성 예산, 로컬 및 초기 토큰 크기, 관측 창, 최대 용량, 커널 크기 등이 포함됩니다. 이 표는 다양한 장문 맥락 메서드의 구현과 평가에 사용되는 특정 설정에 대한 포괄적인 개요를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Configurations of long-context methods in SCBench.
> </details>

{{< table-caption >}}
| Retr.MultiHop |{{< /table-caption >}}
> 🔼 이 표는 Llama-3.1-70B, Qwen2.5-32B, Llama-3-8B-262K 모델에서 다양한 장문 맥락(long-context) 메서드의 SCBench에서의 평균 성능 결과를 보여줍니다. 두 가지 공유 맥락 모드(multi-turn 및 multi-request)에서 Retr.String, Retr.Semantic, Global, Multi-task 작업에 대한 각 메서드의 평균 정확도가 표시되어 있습니다. 이를 통해 서로 다른 모델과 작업에서 다양한 장문 맥락 메서드의 효과를 비교할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 10: The average results of various long-context methods on Llama-3.1-70B, Qwen2.5-32B, and Llama-3-8B-262K with two shared context modes on SCBench.
> </details>

{{< table-caption >}}
| RULER |
| -------- |
| [Hsieh et al. (2024)](https://arxiv.org/html/2412.10319/2412.10319v1#bib.bib34) |{{< /table-caption >}}
> 🔼 이 표는 다중 턴 모드에서 모든 하위 작업에 대한 SCBench의 세부 결과를 보여줍니다. 다양한 언어 모델과 효율적인 장문 컨텍스트 접근 방식에서 En.Sum 작업에 대한 사례 연구를 제시합니다. 요약의 품질은 모델 규모와 양의 상관관계가 있는 것으로 보입니다. 예를 들어 Llama-3.1-70B 및 Qwen2.5-72B는 다른 모델에 비해 더 포괄적이고 세분화된 요약을 제공합니다. 효율적인 장문 컨텍스트 접근 방식의 경우, Tri-Shape 및 MInference와 같은 고밀도 디코딩을 사용하는 희소 인코딩 방법은 세부적인 내용을 포착하는 데 탁월한 성능을 보입니다. 반대로 StreamingLLM과 같은 희소 디코딩 방법은 실패하여 임의적이고 일관성 없는 결과를 생성합니다.Retr.Prefix-Suffix 작업의 결과를 제시합니다. 흥미롭게도 Mamba-Attention 하이브리드 아키텍처 Jamba가 가장 정확한 성능을 달성했습니다. Retr.Prefix-Suffix 작업에는 상당히 큰 공간과 시간 복잡도가 필요하며 Mamba 레이어는 이러한 차원에서 성능이 좋지 않다고 보고되었기 때문에 이는 중요한 결과입니다. 반대로, Llama 및 Qwen 시리즈 모델과 같은 전체 주의 LLMs는 모두 이 작업에서 실패했습니다. 대부분의 모델은 여전히 가변 길이의 접두사를 기억할 수 있지만 종종 전체 문자열을 재현하지 못합니다. 예를 들어 MInference를 사용하는 Llama-70B는 거의 전체 문자열을 검색할 수 있지만 중간에 있는 여러 문자의 철자가 틀립니다. 이는 Transformer 어텐션 헤드에서 유도 헤드(Olsson et al., 2022)의 약점 때문일 수 있으며, 이러한 효율적인 장문 컨텍스트 방법에 대한 희소 입력으로 인해 발생할 수도 있습니다.또한, 다중 작업 테스트, 즉 표 16의 Mix.RepoQA+KV에 대한 일부 장문 컨텍스트 방법의 결과를 제시합니다. 정답은 KV 검색의 답변 하나와 reporqa의 답변 하나를 제공합니다. Llama-3.1-70B와 MInference를 사용하는 변형은 모두 값을 정확하게 검색하여 키-값 검색에서 좋은 성능을 보였습니다. 그러나 Python 함수를 재현한 결과는 흥미로운 차이점을 보여줍니다. 두 모델 모두 전반적인 구조와 들여쓰기를 유지하면서 함수 로직에 여러 수정 사항을 도입합니다. Llama-3.1-70B는 잘못된 함수 이름을 재현하고 새로운 알고리즘을 구현하지만 원래 요소는 제한적으로만 유지합니다. MInference 변형은 기본 모델의 출력과 매우 유사하며 Python 코드 블록 식별자 추가와 같은 사소한 차이점만 있습니다. 특히 두 모델 모두 정답 함수를 정확하게 복제하지 않아 정확한 함수 재현에 어려움이 있음을 시사합니다. 하지만 MInference의 결과는 인코딩 방식의 희소 특성보다는 기본 Llama 모델의 제한된 장문 컨텍스트 기능 때문이라고 생각합니다.표 17에서는 Retr.KV에서 A-shape 및 Tri-shape 모델의 성능을 강조합니다. 특히 Tri-shape는 첫 번째 턴에서도 강력한 성능을 보이며 모델의 지침 준수 기능을 효과적으로 유지합니다. 반대로 A-shape는 모델의 초기 응답을 방해하여 전반적인 작업 성능을 저하시키는 경향이 있습니다. 이러한 차이점은 Tri-shape가 처음부터 작업 구조와 이해를 유지하는 데 유리함을 보여줍니다. 마지막으로, 이러한 결과가 이전 벤치마크의 결과와 어떻게 다른지 설명하고, 희소 인코딩과 디코딩 방법의 성능 차이, 다양한 모델의 작업 적합성, 그리고 오류 전파 및 모델 생성의 영향과 같은 몇 가지 중요한 질문을 다룹니다.
> <details>
> <summary>read the caption</summary>
> Table 11: The results breakdown of SCBench for all sub-tasks in multi-turn mode.
> </details>

{{< table-caption >}}
| num chains = 2 |
| -------- |
| num hops = 2 |
| metric = Accuracy |{{< /table-caption >}}
> 🔼 이 테이블은 다양한 하위 작업에 대한 여러 효율적인 장문 컨텍스트 방법의 성능을 다중 요청 모드에서 비교하여 보여줍니다. Retr.KV 및 Retr.PS와 같은 검색 작업, En.QA 및 Zh.QA와 같은 QA, En.Sum과 같은 요약, RepoQA와 같은 코드 이해, 수학 및 ICL과 같은 문맥 내 학습을 포함합니다. 각 방법은 이러한 영역에서 다양한 강점과 약점을 보여줍니다. 특히 StreamingLLM 및 SnapKV와 같은 일부 방법은 여러 모드에서 검색 및 수학 작업에서 거의 또는 전혀 성능을 보이지 않는 반면 GLM-4-1M 및 MInference와 같은 다른 방법은 검색, QA 및 ICL에서 지속적으로 잘 수행됩니다.
> <details>
> <summary>read the caption</summary>
> Table 12: The results breakdown of SCBench for all sub-tasks in multi-requests mode.
> </details>

{{< table-caption >}}
| Code.RepoQA |{{< /table-caption >}}
> 🔼 이 표는 이전 질문에 대한 응답을 다음 질문의 컨텍스트로 사용하는 경우(즉, 정답을 컨텍스트로 사용하지 않는 경우)의 결과를 보여줍니다. 표의 두 번째 숫자는 정답을 컨텍스트로 사용하는 경우와 비교한 차이를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 13: Results when disabling golden answer as context. The later number indicate the gap compared to golden-answer-as-context.
> </details>

{{< table-caption >}}
| RepoQA |
| -------- |
| [Liu et al., 2024c](https://arxiv.org/html/2412.10319/bib.bib52) |{{< /table-caption >}}
> 🔼 이 표는 다양한 언어 모델과 장문 맥락 접근 방식을 사용한 En.Sum 과제에 대한 요약 사례 연구를 보여줍니다. 표에서 파란색은 정보가 누락되었음을 나타내고 주황색은 모델이 환각을 일으켰을 가능성이 있음을 나타냅니다. 요약의 품질은 모델 크기와 양의 상관관계가 있는 것으로 보입니다. 예를 들어 Llama-3.1-70B와 Qwen2.5-72B는 다른 모델에 비해 더 포괄적이고 세분화된 요약을 제공합니다. 효율적인 장문 맥락 접근 방식의 경우, Tri-Shape 및 MInference와 같은 dense 디코딩을 사용한 sparse 인코딩 방법은 세부적인 내용을 파악하는 데 뛰어난 성능을 보입니다. 반대로 StreamingLLM과 같은 sparse 디코딩 방법은 실패하여 무작위적이고 일관성 없는 출력을 생성합니다.
> <details>
> <summary>read the caption</summary>
> Table 14: Case Study of En.Sum. We use blue to indicate mising informaiton, and orange to mark potential hallucination.
> </details>

{{< table-caption >}}
| func description from GPT-4 |
| ------------------------- |
| metric = Pass@1 |{{< /table-caption >}}
> 🔼 이 표는 문자열 검색 능력을 평가하는 Retr.Prefix-Suffix 과제에 대한 다양한 모델의 성능을 보여주는 사례 연구입니다. 각 모델은 주어진 접두사와 접미사를 가진 문자열을 검색해야 하며, 예시 응답은 정답과 비교하여 다른 부분을 주황색으로 강조 표시합니다. 이를 통해 각 모델이 접두사와 접미사를 정확하게 일치시키는 능력과 문자열의 나머지 부분을 올바르게 재현하는 능력을 자세히 분석할 수 있습니다. 특히, Jamba-1.5-Mini 모델은 가장 정확한 성능을 보이는 반면, Llama 및 Qwen 시리즈와 같은 Full-attention LLM은 이 작업에 실패하는 것을 볼 수 있습니다. 또한, 효율적인 장문 컨텍스트 접근 방식 중에서 Sparse Encoding with Dense Decoding 방식인 Tri-Shape 및 MInference가 세부 정보를 잘 캡처하는 우수한 성능을 보이는 반면, StreamingLLM과 같은 Sparse Decoding 방식은 실패하여 무작위적이고 일관성 없는 결과를 생성하는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 15: Case Study of Retr.Prefix-Suffix. Orange is used to mark the difference of model response compared to the ground truth.
> </details>

{{< table-caption >}}
| En.QA |
| --- |
| Zh.QA |{{< /table-caption >}}
> 🔼 이 표는 Mix.RepoQA + KV 작업에 대한 사례 연구를 보여줍니다. 주황색은 모델의 잠재적 환각을 나타냅니다. Llama-3.1-70B와 MInference 변형 모두 KV 검색에서 정확하게 값을 검색하여 우수한 성능을 보여주지만, Python 함수를 재현할 때는 차이를 보입니다. 두 모델 모두 전체 구조와 들여쓰기를 유지하지만 함수 로직에 몇 가지 수정 사항을 도입합니다. Llama-3.1-70B는 잘못된 함수 이름을 재현하고 새로운 알고리즘을 구현하면서 원본 요소만 제한적으로 유지합니다. MInference 변형은 기본 모델의 출력과 거의 유사하며 Python 코드 블록 식별자 추가와 같은 사소한 차이만 있습니다. 특히 두 모델 모두 정확하게 함수를 복제하지 못하여 정확한 함수 재현에 어려움이 있음을 시사합니다. MInference 결과는 인코딩 접근 방식의 희소 특성이 아닌 기본 Llama 모델의 제한된 장기 문맥 기능 때문인 것으로 보입니다.
> <details>
> <summary>read the caption</summary>
> Table 16: Case Study of Mix.RepoQA + KV. Orange indicate the potential model hallucination.
> </details>

{{< table-caption >}}
| InfiniteBench |
| --- |
| [Zhang et al., 2024a](https://arxiv.org/html/2412.10319/2412.10319v1#bib.bib93) |{{< /table-caption >}}
> 🔼 이 표는 Retr.KV 작업에서 A-shape와 Tri-shape를 비교한 케이스 스터디를 보여줍니다. Tri-shape는 첫 번째 턴에서도 강력한 성능을 보여 모델의 지시 따르기 기능을 효과적으로 유지하는 반면, A-shape는 모델의 초기 응답을 방해하여 전반적인 작업 성능을 저하시키는 경향이 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 17: Case Study of Retr.KV to compare A-shape and Tri-shape.
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