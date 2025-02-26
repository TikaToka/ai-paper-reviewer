---
title: "Can Community Notes Replace Professional Fact-Checkers?"
summary: "소셜 미디어의 커뮤니티 검증 시스템은 전문가 팩트 체커에 크게 의존하며, 특히 복잡한 주장이나 음모론 관련 주장일 경우 더욱 그러하다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Text Classification", "🏢 University of Copenhagen",]
showSummary: true
date: 2025-02-19
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.14132 {{< /keyword >}}
{{< keyword icon="writer" >}} Nadav Borenstein et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-25 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.14132" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.14132" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/can-community-notes-replace-professional-fact" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

온라인 허위 정보 확산이 심각한 사회적 문제로 떠오르면서, 소셜 미디어 플랫폼들은 허위 정보를 퇴치하기 위해 전문적인 팩트 체킹 기관과 협력하거나, 플랫폼 이용자들의 커뮤니티 검증 시스템을 활용하는 두 가지 전략을 사용해 왔습니다. 하지만 최근 트위터/X 와 같은 플랫폼들은 팩트 체킹 기관과의 제휴를 축소하고, 커뮤니티 검증에 더 의존하는 경향을 보이고 있습니다.  이러한 변화 속에서 본 연구는 커뮤니티 검증과 전문가 팩트 체킹 사이의 관계를 명확히 밝히고, 커뮤니티 기반 검증의 효과적 운영에 대한 통찰력을 제공하는 것을 목표로 합니다.

본 연구는 트위터/X의 커뮤니티 노트 데이터를 분석하여 커뮤니티 노트가 팩트 체킹 출처를 얼마나 활용하는지, 어떤 유형의 게시물이 팩트 체킹 출처를 더 많이 인용하는지 등을 조사했습니다. 연구 결과, 커뮤니티 노트는 기존 연구에서 보고된 것보다 훨씬 더 많이 팩트 체킹 출처를 인용하고 있으며, **특히 복잡한 주장이나 음모론 관련 주장일 경우 더욱 그러하다**는 사실을 밝혔습니다. 이는 **커뮤니티 기반 검증 시스템이 전문가 팩트 체킹에 상당히 의존적이며**, 전문가 팩트 체킹의 부재는 커뮤니티 검증 시스템의 품질 저하로 이어질 수 있음을 시사합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 커뮤니티 검증은 전문가 팩트 체킹에 크게 의존한다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 건강, 과학, 사기 등 중요한 주제의 게시물일수록 팩트 체킹 출처를 더 많이 인용한다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 팩트 체킹 출처를 인용하는 커뮤니티 검증은 더 높은 품질로 평가된다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **소셜 미디어의 정보 생태계에서 전문가 검증과 커뮤니티 검증의 상호 의존성**을 밝히는 데 중요한 시사점을 제공합니다.  **플랫폼의 정책 변화**와 **팩트 체커의 재정적 불안정성**에 대한 우려 속에서, 본 연구는 커뮤니티 기반 검증 시스템의 효과적인 운영을 위한 중요한 통찰력을 제공하며, **미디어 리터러시 교육** 및 **플랫폼 정책 수립**에 대한 새로운 연구 방향을 제시합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.14132/extracted/6218171/Figures/note_pan.png)

> 🔼 트윗에 대한 커뮤니티 노트의 예시입니다. 팩트체크 링크와 평점을 확인할 수 있습니다.  이 이미지는 커뮤니티 노트가 어떻게 작성되고, 팩트체크 링크를 포함하여 정보의 정확성을 높이는지 보여줍니다.  또한, 사용자들이 노트의 유용성에 대해 평가할 수 있는 시스템을 보여줍니다. 이는 플랫폼의 신뢰도를 높이고 잘못된 정보 확산을 막는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: An example of a community note. Notice the fact-checking link and rating.
> </details>





{{< table-caption >}}
| Tweet | Note | misleadingUnverifiedClaimAsFact | misleadingOutdatedInformation | misleadingFactualError | misleadingSatire | Fact Checking source |
|---|---|---|---|---|---|---|
| The NASA War Document is absolutely terrifying https://t.co/... | misrepresenting a presentation by NASA scientist Dennis Bushnell, The lecture was not detailing plans by NASA to attack the world it was a lecture for defense industry professionals, and how defense tactics might rise to meet evolving threats in the future. https://leadstories.com/hoax-alert/2021/06/fact-check-the-future-is-now-is-not-a-nasa-war-document-plan-for-world-domination-and-phasing-out-of-humans.html | ✓ | ✗ | ✗ | ✗ | ✓ |
| BREAKING NEWS: International Criminal Investigation calls on every public citizen to recommend indictments for Bill Gates, Anthony Fauci, Pfizer, BlackRock, Tedros and Christian Drosten for pushing everyone to receive the ineffective highly dangerous lethal experimental vaccines… | Video has been fact-checked by USA Today, was found to be misleading, and promotes a conspiracy theory about COVID … https://ca.movies.yahoo.com/movies/fact-check-viral-video-promotes-204414488.html | ✓ | ✗ | ✗ | ✗ | ✓ |
| 1) California is RED. It is just because of the MASSIVE Election Fraud that stupid, brainwashed people believe Calif. is blue. Joe Biden won only in the SFO Bay area … | The map shows the results of Reagan’s reelection in 1984, not Biden’s election in 2020. https://en.wikipedia.org/wiki/1984_United_States_presidential_election_in_California | ✗ | ✓ | ✗ | ✗ | ✗ |
| Davis blows up $100,000 fireworks in Kai Cenat setup During the Mr Beast Stream … | The second photo is from a house fire in Atlanta in 2019. https://www.11alive.com/article/news/local/woodland-brook-drive-cause-of-house-fire/85-ecb7df9b-5f65-44e9-bf9d-8c162d36c334 | ✗ | ✓ | ✗ | ✗ | ✗ |
| @cnviolations I swear community notes are the only good thing Elon added since he bought Twitter. | Community notes was first launched under former Twitter CEO Jack Dorsey in 2021 under the name of “Birdwatch”. The only thing Elon Musk did was that he renamed the feature to community notes. https://blog.twitter.com/en_us/topics/product/2021/introducing-birdwatch-a-community-based-approach-to-misinformation https://www.reuters.com/article/factcheck-elon-birdwatch-idUSL1N31Z2VG/ | ✗ | ✗ | ✓ | ✗ | ✓ |
| Thailand will become the first country to make the contract null and void, meaning that Pfizer will become responsible for all vaccine injuries … | Thailand has no plans to void its Pfizer COVID vaccine contract, an official with the country’s National Vaccine Institute said. Thailand’s Department of Disease Control also rejected the claims as “fake news.” … https://apnews.com/article/fact-check-covid-vaccine-pfizer-thailand-203948163859 | ✗ | ✗ | ✓ | ✗ | ✓ |
| Hilarious tweets by footballers, A thread: 1. Virgil Van Dijk [Current Liverpool Captain] https://t.co/... | Virgil Van Dijk did not tweet this, the tweet was made by a fan account in his name. https://www.pinkvilla.com/sports/fact-check-did-virgil-van-dijk-really-root-for-man-u-because-no-one-likes-liverpool-in-resurfaced-viral-tweet-1287250 | ✗ | ✗ | ✗ | ✓ | ✓ |
| Rob Reiner announces he’s on the Epstein Client List and Epstein Flight logs. What a fool! When a lawyer tells me to STFU, I STFU! https://t.co/... | This is a digitally altered photo that might be misinterpreted even if used as a joke. The name Rob Reiner is misspelled, and the text is not on Reiner’s X timeline. https://twitter.com/robreiner?t=iqu43-NszIW5oOM_KqRSpw | ✗ | ✗ | ✗ | ✓ | ✗ |{{< /table-caption >}}

> 🔼 표 1은 트윗, 해당 트윗에 대한 커뮤니티의 설명, 그리고 해당 설명이 팩트체크 링크를 포함하는지 여부를 보여주는 표본 데이터를 제시합니다.  각 행은 트윗의 본문과 커뮤니티 사용자들이 작성한 설명(Community Notes), 설명에 대한 여러 속성(예: 잘못된 정보를 반박하기 위한 전략, 사용된 출처의 유형 등) 그리고 설명이 전문적인 팩트체크 사이트의 정보를 참조하는지 여부를 나타냅니다. 이는 팩트체크 정보가 커뮤니티 기반 검증 시스템에 어떻게 활용되는지를 보여주는 예시입니다.
> <details>
> <summary>read the caption</summary>
> Table 1: A sample of tweets, notes, and their community annotations, as well as whether the note contains a fact-checking link.
> </details>





### In-depth insights


#### Community Notes
본 논문에서 '커뮤니티 노트'는 **소셜 미디어 내 허위 정보 확산 방지**를 위한 플랫폼 사용자 기반의 커뮤니티 모더레이션 시스템으로 제시됩니다.  전문적인 팩트체커의 역할과 상호 보완적인 관계를 분석하며, **커뮤니티 노트가 팩트체크 소스를 예상보다 훨씬 많이 인용**한다는 점을 밝히고 있습니다.  특히, **사회적 영향력이 큰 주제**일수록 팩트체크 소스에 대한 의존도가 높아짐을 보여주며, 전문가 검증의 중요성을 강조합니다.  하지만 커뮤니티 노트의 효과성은 사용자 참여도와 신뢰성 확보에 달려있다는 점과,  **편향성 및 객관성 확보의 어려움** 등의 한계점 또한 제기합니다.  따라서, **커뮤니티 노트는 팩트체킹 시스템을 완전히 대체할 수 없고, 오히려 상호작용적이고 효율적인 정보 검증 시스템 구축을 위한 보완적 역할**을 수행할 수 있다는 결론을 도출합니다.

#### Fact-checking's Role
본 논문에서 다루는 "팩트체크의 역할"에 대한 심층적인 분석은 **전문적인 팩트체크 기관과 온라인 커뮤니티의 상호작용**에 초점을 맞춥니다. 단순히 정보의 진위 여부 판별을 넘어, **사회적 영향력이 큰 주장들에 대한 신뢰도 확보** 및 **대중의 오해 해소**에 중요한 역할을 한다는 점을 강조합니다. 특히 **소셜 미디어 상의 가짜뉴스 확산 방지**를 위해 두 주체 간의 협력이 필수적임을 시사하며, **플랫폼 정책의 변화**와 **팩트체커의 역할 축소**에 대한 우려를 제기합니다.  **커뮤니티 기반 팩트체크 시스템의 한계**와 함께 **전문성과 신뢰성 유지**를 위한 방안 모색의 필요성을 강조하는 결론을 제시합니다.  **알고리즘의 개입**과 **사용자 참여**가 팩트체크 과정에 미치는 영향을 고려하여, **더욱 효율적이고 공정한 정보 생태계 구축**을 위한 추가 연구의 필요성을 언급합니다.

#### Methodological Analysis
본 논문의 방법론적 분석 부분은 **데이터 수집 및 전처리 과정의 상세한 설명**과 더불어 **자연어 처리 기법 및 머신러닝 모델의 적용 방식**, 그리고 **모델 성능 평가 지표**를 제시하는 것으로 구성될 것입니다. 특히,  **사용된 데이터의 한계점 및 편향성**에 대한 논의는 필수적이며, 이를 통해 연구 결과의 신뢰성과 일반화 가능성을 높일 수 있습니다.  **사용된 기법의 타당성**을 뒷받침하는 이론적 근거 제시와 함께, **다른 방법론과의 비교 분석**을 통해 연구의 독창성을 보여주는 것 또한 중요합니다.  마지막으로 **결과 해석에 대한 엄밀성**을 확보하고, **미래 연구를 위한 제언**을 제시함으로써 논문의 완성도를 높여야 합니다.

#### Study Limitations
본 연구의 제한점은 크게 세 가지로 요약할 수 있습니다. 첫째, **영어로 작성된 트윗과 댓글만 분석**했기 때문에, 다른 언어로 작성된 정보의 분석은 제외되었습니다.  이는 영어권 국가의 정보 생태계에 대한 편향된 시각을 제공할 가능성이 있습니다. 둘째, **분석에 사용된 데이터의 양과 범위**에 제한이 있습니다. 전체 데이터셋의 일부만 분석되었으며, 특정 기간 동안의 데이터에만 집중되어 있어 시간적 범위가 제한적입니다. 이러한 제한은 연구 결과의 일반화 가능성에 영향을 미칠 수 있습니다. 셋째, **주관적인 인간의 판단**이 필요한 부분이 존재합니다. 즉, 댓글과 트윗의 주제 분류, 가짜 정보의 범주화, 자료 출처의 신뢰도 판정 등에 있어 연구자의 주관적인 판단이 개입될 여지가 있으므로, 객관성 확보에 어려움이 있을 수 있습니다. 따라서, 본 연구 결과는 이러한 제한점을 고려하여 해석해야 합니다.

#### Future Research
본 논문은 커뮤니티 노트가 전문적인 팩트체커를 대체할 수 있는지 여부를 조사했습니다. **미래 연구는 다양한 언어와 문화적 맥락에서의 커뮤니티 노트의 효과성을 평가**하고, **플랫폼의 알고리즘과 정책이 커뮤니티 노트의 질과 신뢰성에 미치는 영향**을 분석하는 데 초점을 맞춰야 합니다. 또한, **커뮤니티 노트 작성자의 동기, 편향, 전문성 수준**을 심층적으로 파악하고, **전문 팩트체커와의 상호 작용 및 의존성**에 대한 연구가 필요합니다.  **가짜 뉴스 확산 방지 전략으로서 커뮤니티 노트의 장단점을 비교 분석**하고, **최적의 정보 검증 시스템 구축을 위한 혼합 접근 방식**에 대한 연구도 중요합니다.  마지막으로, **AI 기술을 활용한 팩트체크 및 커뮤니티 노트의 자동화** 가능성을 탐색하고, 이러한 기술의 윤리적 함의에 대한 논의가 필요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.14132/extracted/6218171/Figures/link_types_tilt.png)

> 🔼 그림 2는 커뮤니티 노트 작성자가 소스로 사용한 링크의 범주를 보여줍니다.  각 범주는 특정 유형의 웹사이트나 자료 출처(뉴스, 소셜 미디어, 학술자료, 팩트체크 사이트 등)를 나타냅니다. 이는 커뮤니티 노트 작성자가 정보의 근거로 어떤 종류의 소스를 주로 활용하는지에 대한 통찰력을 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: The categories of links used by Community notes’ authors as a source.
> </details>



![](https://arxiv.org/html/2502.14132/extracted/6218171/Figures/annotations_of_notes_narrow.png)

> 🔼 그림 3은 커뮤니티 사용자들이 잘못된 게시물에 대해 어떻게 평가했는지 보여주는 막대 그래프입니다. 각 막대는 특정 유형의 잘못된 정보에 대한 평균 점수를 나타냅니다. 예를 들어, '오해의 소지가 있는 주장'은 평균 점수가 0.6인 반면, '조작된 미디어'는 평균 점수가 0.8입니다. 이 그래프는 커뮤니티 사용자들이 특정 유형의 잘못된 정보를 다른 유형보다 더 심각하게 받아들였다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Mean scores of community annotations of misleading posts.
> </details>



![](https://arxiv.org/html/2502.14132/extracted/6218171/Figures/manual_annotation.png)

> 🔼 그림 4는 허위 정보 주장에 대한 반박 전략을 보여줍니다. (a)는 더 넓은 맥락의 주장과 관련된 허위 정보를 반박하는 전략을, (b)는 사실 확인 출처를 사용하여 허위 정보를 반박하는 다양한 방법을 보여줍니다. (a)에서는 더 넓은 맥락의 이야기에 대한 반박 전략을, (b)에서는 사실 확인 출처를 사용하여 주장을 반박하는 방법을 보여줍니다.  두 이미지 모두 사실 확인의 중요성과 허위 정보에 효과적으로 대응하기 위한 다양한 접근 방식을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: (a) strategies in debunking claims related to broader narratives. (b) the different ways in which fact-checking sources are used to debunk claims.
> </details>



![](https://arxiv.org/html/2502.14132/extracted/6218171/Figures/Distribution_of_topics_vertical.png)

> 🔼 그림 5는 팩트체크 출처가 있는 경우와 없는 경우의 게시물 주제 분포를 보여줍니다.  팩트체크 출처가 있는 게시물과 없는 게시물의 주제 비율을 비교하여, 어떤 주제의 게시물이 팩트체크 출처에 더 많이 의존하는지 보여줍니다.  이를 통해 팩트체크가 특정 주제의 신뢰성 확보에 얼마나 중요한 역할을 하는지 이해할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Distribution of notes’ topics, with and without a fact-checking source.
> </details>



![](https://arxiv.org/html/2502.14132/extracted/6218171/Figures/notes_per_month.png)

> 🔼 그림 6은 2021년 1월부터 2025년 1월까지 매달 작성된 커뮤니티 노트의 수와 그 평가(도움됨, 도움 안됨, 추가 데이터 필요)를 나타내는 히스토그램입니다. 회색 수직선(2022년 12월)은 커뮤니티 노트가 전 세계적으로 공개된 시점을 나타냅니다. 이 히스토그램은 시간에 따른 커뮤니티 노트의 생성 추세와 사용자들의 평가 패턴을 보여주어, 커뮤니티 노트 시스템의 성장과 사용자 참여도를 분석하는 데 유용한 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: A histogram of the number of community notes written every month and their rating (helpful, not helpful, or needs more data. The grey vertical line (December 2022) indicates the date when the community notes became visible worldwide.
> </details>



![](https://arxiv.org/html/2502.14132/extracted/6218171/Figures/link_types_only_helpful.png)

> 🔼 도움이 된다고 평가받은 커뮤니티 노트에서 작성자가 사용한 링크의 범주를 보여주는 그림입니다. 각 범주는 사용된 링크 수의 비율을 나타내는 막대 그래프로 표시되어 있습니다. 여기에는 뉴스, 소셜 미디어, 기타 등 다양한 유형의 출처가 포함됩니다. 이 그림은 커뮤니티 노트에서 신뢰할 수 있는 정보 출처로 사용되는 다양한 유형의 링크를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: The categories of links used by Community notes’ authors as a source, filtering for notes rated as “helpful”.
> </details>



![](https://arxiv.org/html/2502.14132/extracted/6218171/Figures/link_types_only_not_helpful.png)

> 🔼 도움이 되지 않는 것으로 평가된 커뮤니티 노트에 대해 커뮤니티 노트 작성자가 소스로 사용한 링크의 범주를 보여주는 그림입니다. 각 범주는 소스 유형(뉴스, 소셜 미디어, 팩트 체킹 등)과 그 비율을 나타냅니다. 이 그림은 도움이 되지 않는 것으로 평가된 노트에서 어떤 유형의 소스가 더 많이 사용되는지, 그리고 이러한 소스가 노트의 유용성에 어떤 영향을 미치는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: The categories of links used by Community notes’ authors as a source, filtering for notes rated as “not helpful”.
> </details>



![](https://arxiv.org/html/2502.14132/extracted/6218171/Figures/ratings_of_notes_2.png)

> 🔼 그림 9는 팩트 체크 출처를 사용한 메모와 사용하지 않은 메모에 대한 커뮤니티 평점을 비교 분석한 결과를 보여줍니다. 팩트 체크 출처를 사용한 메모가 사용하지 않은 메모보다 평균적으로 더 높은 평점을 받았음을 시각적으로 보여줍니다. 이는 팩트 체크 출처를 참조하는 메모가 신뢰도 측면에서 더 높은 평가를 받는다는 것을 의미합니다.  각 평점 유형(예: 유용성, 신뢰도 등)에 대한 평균 점수를 비교하여 팩트 체크 정보의 영향을 자세히 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Community ratings of notes with and without fact-checking source.
> </details>



![](https://arxiv.org/html/2502.14132/extracted/6218171/Figures/annotation_setup.jpeg)

> 🔼 그림 10은 논문의 수동 주석 추가 설정을 보여줍니다.  표는 주석 작업에 사용된 12가지 이진 속성(예: 광범위한 내러티브, 주장의 출처 반박, 누락된 맥락 추가, AI 생성 강조, 편집된 미디어 강조, 직접 출처 링크, 공식 출처 링크, 과학적 출처 링크, 일반 지식 링크, 인용 주석 확인, 주석 내 사실 확인)과 각 속성에 대한 설명을 포함하고 있습니다.  각 속성은 트윗과 관련된 주석에 대해 'True' 또는 'False'로 표시될 수 있습니다. 표에는 트윗과 주석의 예시도 포함되어 있어 어떻게 주석을 추가하는지 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Our annotation setup.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
|   |   | FC source |  
|---|---|---|---|
|   |   | ✓ | ✗ |
| Conspiracy | ✓ | 22% | 11% |
|  | ✗ | 28% | 39% |{{< /table-caption >}}
> 🔼 표 2는 더 넓은 맥락이나 음모론과 관련된 샘플의 비율과 팩트체크 출처를 포함하는 샘플의 비율을 보여줍니다.  더 자세히 설명하자면, 이 표는 연구에서 분석한 데이터셋 내에서 특정 주제(더 넓은 맥락 또는 음모론 관련)를 다루는 게시물의 비율과 그러한 게시물에서 팩트체크 출처를 참조하는 게시물의 비율을 비교합니다. 이는 커뮤니티 노트에서 전문적인 팩트체킹의 역할을 이해하는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Percentage of samples related to a broader narrative or conspiracy vs. have a fact-checking source.
> </details>

{{< table-caption >}}
| Name | URL | Language | Region/domain |
|---|---|---|---|
| Lead stories | leadstories.com | English | Global |
| AFP Factuel | factuel.afp.com | French | Global |
| AAP FactCheck | aap.com.au/factcheck | English | Australia |
| Full Fact | fullfact.org | English | Global |
| Science Feedback | science.feedback.org | English | Science |
| Politifact | politifact.com | English, Spanish | USA |
| HoaxEye | hoaxeye.wordpress.com | English | Images |
| Logically Facts | logicallyfacts.com | Multiple | Europe/India |
| FactCheckNI | factcheckni.org | English | North Ireland |
| DFRLab | dfrlab.org | English | Global |
| FactReview | factreview.gr | Greek | Global |
| Lupa | lupa.uol.com.br/jornalismo | Portuguese | Global |
| Check your fact | checkyourfact.com | English | Global |
| Climate feedback | climatefeedback.org | English | Climate |
| Factcheck | factcheck.org | English | USA |
| Health feedback | healthfeedback.org | English | Health |
| Snopes | snopes.com | English | US |
| aosfatos | aosfatos.org | Portuguese | Global |
| Demagog | demagog.org.pl/fake_news | Polish | Poland |
| FakeReporter | fakereporter.net | Hebrew | Israel |
| litmus factcheck | litmus-factcheck.jp | Japanese | Japan |
| Climate Feedback | climatefeedback.org | English | Global |
| AFP | factcheck.afp.com | English | Global |
| USA Today | usatoday.com/story/news/factcheck | English | USA |
| Statesman | statesman.com | English | USA |
| Dallas News | dallasnews.com/news/politifact | English | USA |
| Google Fact Check | toolbox.google.com/factcheck | English | Global |
| MediaBias/FactCheck | mediabiasfactcheck.com | English | Global |
| MedDMO | meddmo.eu | English, Greek | Greece, Cyprus, Malta |
| Poynter | poynter.org/fact-checking | English | USA |
| Newsmeter | newsmeter.in/fact-check | English, Tamil | India |
| Africa Check | africacheck.org | English | Africa |
| Fact Crescendo India | english.factcrescendo.com | English | India |
| Factseeker | factseeker.lk | English | Sri Lanka |
| Fact Crescendo Thailand | thailand.factcrescendo.com | Thai | Thailand |
| Fact Crescendo Afghanistan | afghanistan.factcrescendo.com | Persian | Afghanistan |
| Only Fact | onlyfact.in | English | India |
| Factly | factly.in | English | India |
| Fact Crescendo Sri Lanka | srilanka.factcrescendo.com | Sinhala | Sri Lanka |
| Fact Crescendo Cambodia | cambodia.factcrescendo.com | Cambodian | Cambodia |
| Becid | becid.eu | Baltic langs | Baltic |
| Fact Hunt | facthunt.in | English | India |
| Tec Arp | getcharp.com | English | Global (based in Malaysia) |
| 10 news | 10news.com/news/fact-or-fiction | English | USA |
| RMIT Fact Check | rmit.edu.au | English | Australia |
| Gigafact | gigafact.org | English | USA |
| Ayupp | ayupp.com/fact-check | English | India |
| The Journal | thejournal.ie | English | Ireland |{{< /table-caption >}}
> 🔼 표 3은 전 세계적으로 활동하는 전문적인 팩트체크 단체들의 목록과 해당 단체들의 URL을 보여줍니다.  각 단체의 이름, URL, 언어, 활동 지역이 명시되어 있어, 연구 논문에서 언급된 팩트체크 정보의 출처를 확인하고 추가적인 정보를 찾는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: List of professional fact-checking organisations and their URLs.
> </details>

{{< table-caption >}}
| Domain | Category |
|---|---| 
| x.com | social media |
| twitter.com | social media |
| youtube.com | social media |
| youtu.be | social media |
| un.org | organisation |
| u.today | news |
| t.co | social media |
| snopes.com | fact checking |
| en.m.wikipedia.org | reference |
| en.wikipedia.org | reference |
| google.com | search engine |
| instagram.com | social media |
| britannica.com | reference |
| reuters.com | news |
| bbc.co.uk | news |
| apnews.com | news |
| bbc.com | news |
| nytimes.com | news |
| theguardian.com | news |
| vice.com | news |
| usatoday.com | news |
| factcheck.org | fact checking |
| cnn.com | news |
| washingtonpost.com | news |
| ncbi.nlm.nih.gov | academic |
| nbcnews.com | news |
| help.twitter.com | reference |
| cdc.gov | government |
| npr.org | news |
| forbes.com | news |
| newsweek.com | news |
| fullfact.org | fact checking |
| dailymail.co.uk | news |
| cbsnews.com | news |
| web3antivirus.io | database |
| timesofisrael.com | news |
| help.x.com | reference |
| nypost.com | news |
| aljazeera.com | news |
| reddit.com | social media |
| independent.co.uk | news |
| usgs.gov | academic |
| abcnews.go.com | news |
| nature.com | academic |
| gov.uk | government |
| web.archive.org | database |
| foxnews.com | news |
| tiktok.com | social media |
| edition.cnn.com | news |
| Domain | Category |
|---|---| 
| thehill.com | news |
| amp.theguardian.com | news |
| whitehouse.gov | government |
| news.sky.com | news |
| merriam-webster.com | reference |
| techarp.com | news |
| cbc.ca | news |
| politifact.com | fact checking |
| pbs.org | commercial |
| telegraph.co.uk | news |
| businessinsider.com | news |
| time.com | news |
| justice.gov | government |
| cnbc.com | news |
| wsj.com | news |
| sciencedirect.com | academic |
| msn.com | news |
| statista.com | reference |
| business.x.com | commercial |
| amp.cnn.com | news |
| congress.gov | government |
| factcheck.afp.com | fact checking |
| yahoo.com | search engine |
| timesofindia.indiatimes.com | news |
| thelancet.com | academic |
| hrw.org | organisation |
| healthfeedback.org | fact checking |
| fda.gov | government |
| m.youtube.com | social media |
| law.cornell.edu | academic |
| medium.com | blog post |
| healthfeedback.org | fact checking |
| who.int | organisation |
| haaretz.com | news |
| axios.com | news |
| mayoclinic.org | commercial |
| nejm.org | academic |
| scienceexchange.caltech.edu | academic |
| indiatoday.in | news |
| bloomberg.com | news |
| pewresearch.org | academic |
| jamanetwork.com | academic |
| leadstories.com | news |
| dictionary.cambridge.org | reference |
| jpost.com | news |
| archive.ph | database |
| healthline.com | commercial |
| abc.net.au | news |
| france24.com | news |{{< /table-caption >}}
> 🔼 본 논문의 표 4는 커뮤니티 노트 데이터셋에서 가장 많이 발견된 상위 100개 도메인과 각 도메인의 범주를 보여줍니다.  각 도메인은 소셜 미디어, 뉴스, 정부기관, 학술 자료, 블로그 게시물, 팩트체크, 데이터베이스, 상업, 참고자료, 기타 등의 범주 중 하나로 분류됩니다. 이 표는 커뮤니티 노트 작성자가 어떤 유형의 정보 출처를 주로 사용하는지 보여주는 통계적 개요를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 4: List of top 100 most common domains found in the community notes dataset, and their categorization.
> </details>

{{< table-caption >}}
| ID | summary |
|---|---| 
| 0 | This claim ruled mostly false. https://www.politifact.com/factchecks/2020/may/07/facebook-posts/facebook-post-cites-doctors-widely-disputed-calcul/ |
| 1 | The RedState article claims “the shots do not stop transmission of the virus. This is false. ”“Vaccines provide significant protection from ’getting it’ – infection – and ’spreading it’ – transmission – even against the delta variant.” Source: https://www.usatoday.com/story/news/factcheck/2021/11/17/fact-check-covid-19-vaccines-protect-against-infection-transmission/6403678001/ |
| 2 | There is no proof of this, the photo is real, it’s not the last photo of the child. But snoops say there is a tenuous link the parents used the same law firm to represent them as Maxwell https://www.snopes.com/fact-check/ghislaine-maxwell-jonbenet-ramsey/ |
| 3 | unfounded https://www.snopes.com/fact-check/ashley-biden-diary-afraid/ |
| 4 | The mRNA vaccine does not cause cancer: https://www.factcheck.org/2024/05/still-no-evidence-covid-19-vaccination-increases-cancer-risk-despite-posts/ |
| 5 | Many of the details in this popular essay are inaccurate and too numerous to list here. The essay was fact checked by Snopes in 2005: https://www.snopes.com/fact-check/the-price-they-paid/ |
| 6 | POLITIFACT - rates False. The report analysed a small sample of 128 temp stations out of several thousand volunteer-run stations, then extrapolated results. NOAA uses 2 programs to record daily temps. The report did not look at the 900 more sophisticated automated stations. https://www.politifact.com/factchecks/2022/aug/19/facebook-posts/fact-checking-talking-point-about-corrupted-climat/ |
| 7 | There is no verifiable evidence of campaign espionage in either the 2020 or the 2016 presidential elections. https://www.snopes.com/fact-check/obama-spying-trump-campaign/ https://www.washingtonpost.com/politics/2019/05/06/whats-evidence-spying-trumps-campaign-heres-your-guide/ |
| 8 | Ladapo did get caught altering COVID vaccine study findings. Ladapo replaced the language from an earlier study draft that found no significant risk from COVID vaccines, to then state there was a high risk https://healthfeedback.org/claimreview/analysis-florida-department-health-surgeon-general-joseph-ladopo-contains-multiple-methodological-problems-covid-19-mrna-vaccines/ https://healthexec.com/topics/clinical/COVID-19/florida-surgeon-general-altered-covid-19-study-findings |{{< /table-caption >}}
> 🔼 표 5는 사실 확인 링크가 포함된 커뮤니티 메모 중에서 '도움이 되지 않음: 누락되거나 신뢰할 수 없는 소스'로 평가된 예시들을 보여줍니다.  각각의 메모는 사실 확인 웹사이트의 링크와 함께 잘못된 주장에 대한 설명을 제공합니다. 하지만,  이러한 메모들은 추가적인 정보 또는 보다 폭넓은 맥락이 부족하거나 신뢰할 수 없는 출처를 참고하고 있어서, 유용성이 떨어지는 것으로 평가되었습니다. 이는 사실 확인 작업의 중요성을 강조하고, 효과적인 커뮤니티 검증을 위해서는 신뢰할 수 있는 출처와 충분한 정보가 필요함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Examples of community notes containing fact-checking sources that are rated as having notHelpfulSourcesMissingOrUnreliable.
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