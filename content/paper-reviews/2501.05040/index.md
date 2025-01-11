---
title: "SWE-Fixer: Training Open-Source LLMs for Effective and Efficient GitHub Issue Resolution"
summary: "SWE-Fixer: 오픈소스 LLM로 GitHub 이슈 효율적 해결"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Large Language Models", "🏢 Shanghai AI Laboratory",]
showSummary: true
date: 2025-01-09
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2501.05040 {{< /keyword >}}
{{< keyword icon="writer" >}} Chengxing Xie et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-10 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2501.05040" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2501.05040" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/swe-fixer-training-open-source-llms-for" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

소프트웨어 엔지니어링 분야에서 **GitHub 이슈 해결**은 중요한 과제이며, 기존의 접근 방식들은 주로 **독점적인 LLM**에 의존하여 **재현성과 접근성**이 떨어지는 문제가 있었습니다.  본 연구는 이러한 문제를 해결하기 위해 **오픈소스 LLM 기반의 새로운 프레임워크인 SWE-Fixer**를 제시합니다. 



SWE-Fixer는 **코드 파일 검색 모듈과 코드 수정 모듈**로 구성되며, BM25와 경량 LLM을 활용하여 효율적인 파일 검색을 수행합니다.  **11만개의 GitHub 이슈 데이터셋**을 구축하여 두 모듈을 개별적으로 훈련시켰으며, SWE-Bench Lite와 Verified 벤치마크에서 **최첨단 성능**을 달성했습니다.  본 연구는 오픈소스 LLM을 활용한 소프트웨어 엔지니어링 문제 해결에 대한 새로운 가능성을 제시하며, **향후 연구의 방향**을 제시하는데 중요한 의미를 가집니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 오픈소스 LLM 기반의 효율적인 GitHub 이슈 해결 프레임워크인 SWE-Fixer 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 11만개의 GitHub 이슈 데이터셋을 활용한 훈련 및 최첨단 성능 달성 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 코드 파일 검색 및 코드 수정 모듈을 포함한 효율적인 파이프라인 방식 채택 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **오픈소스 LLM을 사용한 GitHub 이슈 해결의 효율성 및 효과성을 높이는 새로운 방법론**을 제시하여, 연구자들에게 **재현성 높은 연구 결과**를 제공하고 **소프트웨어 엔지니어링 분야의 발전**에 기여합니다. 또한,  **대규모 데이터셋 구축 및 체계적인 실험 분석**을 통해 오픈소스 모델의 성능 향상에 대한 통찰력을 제공하며, **향후 연구 방향**을 제시합니다. 특히,  **비용 효율적인 접근 방식**을 제시하여, 자원이 부족한 연구자들에게도 큰 도움을 줄 수 있습니다.

------
#### Visual Insights







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