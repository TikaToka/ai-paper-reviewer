---
title: "WavePulse: Real-time Content Analytics of Radio Livestreams"
summary: "WavePulse: 실시간 라디오 방송 콘텐츠 분석 프레임워크가 정치적 담론, 미디어 유통, 여론 동향을 실시간 분석하여 정치 과학 및 미디어 연구에 새로운 가능성을 열었습니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Natural Language Processing", "Information Extraction", "🏢 New York University",]
showSummary: true
date: 2024-12-23
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.17998 {{< /keyword >}}
{{< keyword icon="writer" >}} Govind Mittal et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-26 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.17998" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.17998" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/wavepulse-real-time-content-analytics-of" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

현대 사회에서 라디오 방송은 여전히 중요한 정보원으로 자리매김하고 있지만, **방대한 양의 콘텐츠를 실시간으로 분석**하는 데 어려움이 있습니다. 기존의 연구들은 주로 소셜 미디어에 초점을 맞춰왔으며, 라디오 방송 콘텐츠 분석에 대한 연구는 부족한 실정입니다. 따라서, **정치적 견해 형성, 여론 형성, 미디어 유통 패턴 등을 효율적으로 분석할 수 있는 새로운 시스템**의 개발이 시급합니다.

본 연구는 이러한 문제를 해결하기 위해 **실시간 라디오 라이브스트림 콘텐츠 분석 프레임워크인 WavePulse**를 개발했습니다. WavePulse는 **자동화된 전사, 다이어리화, 분류 및 요약 기능**을 통해 방대한 양의 오디오 데이터를 처리하고 분석하며, 정치적 담론, 미디어 유통 패턴, 여론 동향 등을 실시간으로 분석할 수 있습니다. 본 연구는 WavePulse의 실효성을 검증하기 위해 **2024년 미국 대통령 선거 기간 동안 396개의 뉴스 라디오 방송을 모니터링**하는 사례 연구를 진행했습니다. 그 결과, 지역 문제와 국가적 동향 간의 상호작용에 대한 통찰력을 제공하는 등, WavePulse의 효과를 입증했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} WavePulse는 **방대한 라디오 라이브스트림 데이터를 실시간으로 분석**하는 능력을 보여주었습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 본 연구는 정치적 담론 분석, 미디어 콘텐츠 유통 패턴 분석, 정치적 동향 분석 등 **다양한 분야에서 WavePulse의 실효성**을 입증했습니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} WavePulse는 **미디어 연구 및 정치 과학 분야에 새로운 연구 방향**을 제시하며, 향후 연구에 중요한 기여를 할 것으로 예상됩니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **실시간 방송 콘텐츠 분석을 위한 혁신적인 프레임워크**인 WavePulse를 제시하여, 방송 콘텐츠 분석 분야의 새로운 지평을 열었습니다.  **방대한 양의 오디오 스트림을 실시간으로 처리하고 분석**하는 WavePulse의 역량은 정치 과학, 미디어 연구, 여론 조사 등 다양한 분야에서 폭넓은 활용 가능성을 제시하며, **향후 연구의 새로운 방향**을 제시합니다. 특히, 정치적 담론 분석, 미디어 콘텐츠 유통 패턴 분석, 정치적 동향 분석 등 다양한 사례 연구를 통해 WavePulse의 실효성을 입증하였습니다.  이는 **현대 사회의 주요 정보원인 라디오 방송**의 콘텐츠를 효율적으로 분석하고 활용하는데 중요한 의미를 지닙니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.17998/extracted/6086778/appendix_figures/whisperx.png)

> 🔼 그림 1은 WavePulse 시스템의 개요를 보여줍니다.  WavePulse는 라디오 방송을 실시간으로 스트리밍하고, 음성을 텍스트로 변환(전사), 화자를 구분(다이어라이제이션), 내용을 분류(정치적/비정치적, 광고 등), 시간 정보를 추가(타임스탬핑), 그리고 요약하는 기능을 수행합니다.  이를 통해 분석에 사용할 수 있는 정제된 데이터를 생성하며,  정치적 동향 분석 및 주장 검증 등에 활용될 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1. Overview of WavePulse. It streams radio, transcribes, diarizes, classifies, timestamps and summarizes content on the radio, making available for analytics. We derive political trends, match claims
> </details>





{{< table-caption >}}
| Model | RNN-T | MMS-1B | WhisperX |
|---|---|---|---| 
| WER (%) ↓ | 14.5±8.2 | 35.1±13.2 | **8.4±4.6** |
| Inference Time (s) ↓ | 15.0 | 17.8 | **9.5** |{{< /table-caption >}}

> 🔼 본 표는 논문의 대표 데이터셋에서 30분 분량의 오디오 클립을 사용하여 다양한 자동 음성 인식(ASR) 모델의 단어 오류율(WER)과 평균 추론 시간을 비교 분석한 결과를 보여줍니다.  WER은 모델의 정확도를 나타내는 지표이며, 추론 시간은 모델이 오디오를 처리하는 데 걸리는 시간을 의미합니다.  표를 통해 각 모델의 성능과 효율성을 비교하여 최적의 모델을 선택하는 데 유용한 정보를 제공합니다.  낮은 WER과 짧은 추론 시간을 가진 모델이 더 우수한 성능을 가진다고 할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 1. Word-error-rate and Avg. Inference Time for 30-min audio clips of ASR models, from our representative dataset.
> </details>





### In-depth insights


#### Radio's Enduring Power
라디오의 지속적인 영향력은 **디지털 매체의 급격한 성장에도 불구하고 여전히 많은 청취자를 확보하고 있다는 점**에서 확인됩니다. 이는 단순히 과거의 유산이 아닌, **현대 사회에서 라디오가 갖는 고유한 가치와 강점** 때문입니다.  **특히 지역 사회와의 밀접한 연관성, 즉각적이고 신뢰할 수 있는 정보 제공, 그리고 편리한 접근성**은 라디오만이 제공할 수 있는 독특한 강점입니다.  소셜 미디어와 달리 라디오는 일방향 소통 채널로, 청취자들이 수동적으로 정보를 흡수할 수 있는 환경을 제공합니다.  **정치적 담론에서 라디오의 역할은 특히 중요하며, 지역 사회에 대한 깊은 이해를 바탕으로 한 정보 전달은 대중의 정치적 태도 형성에 큰 영향**을 미칩니다. 따라서 라디오는 단순히 오락이나 정보 전달의 수단을 넘어, **지역 사회를 연결하고 공동체 의식을 형성하는 중요한 매체**로서의 역할을 지속하고 있습니다.  **미래에도 라디오는 이러한 강점을 바탕으로 변화하는 미디어 환경 속에서 꾸준히 존재감을 유지**할 것으로 예상됩니다.

#### WavePulse Framework
WavePulse 프레임워크는 **실시간으로 라디오 라이브 스트림의 콘텐츠를 분석**하기 위해 고안된 종합적인 시스템입니다.  **오디오 스트리밍, 전사, 화자 분리, 분류, 시계열화 및 요약**을 포함한 다단계 프로세스를 통해 실시간으로 방대한 양의 오디오 데이터를 처리합니다.  **대규모 언어 모델(LLM)**을 활용하여 빠르고 효율적인 콘텐츠 분석을 수행하며, 정치 뉴스 방송에 초점을 맞춘 파일럿 연구를 통해 그 효과가 입증되었습니다.  **정치적 트렌드 모니터링, 가짜 뉴스 추적, 콘텐츠 공유 패턴 분석** 등 다양한 용도로 활용 가능하며, **정치 과학 연구**와 같은 분야에 귀중한 통찰력을 제공합니다.  **데이터셋 공개**를 통해 연구 공동체의 활용과 발전에 기여할 수 있다는 점도 큰 장점입니다.  **여러 언어 지원**의 확장 가능성은 WavePulse의 글로벌 활용을 위한 잠재력을 시사합니다.

#### Real-time Analysis
본 논문에서 제시된 실시간 분석 시스템은 **방대한 양의 라디오 스트림 데이터를 효율적으로 처리 및 분석**하기 위해 설계되었습니다.  **음성 인식, 화자 분리, 내용 분류 등 다양한 AI 기반 기술**들을 활용하여 실시간으로 방송 내용을 텍스트로 변환하고, 정치적 주제, 광고, 뉴스 등으로 분류합니다.  **정치적 견해 분석, 가짜 뉴스 감지, 콘텐츠 유사성 비교 등의 고급 분석**을 통해 정치적 담론과 여론의 흐름을 추적하고, **지역적 차이를 파악**하는 데 도움을 줍니다.  **데이터 시각화 도구**를 통해 사용자는 분석 결과를 직관적으로 이해하고, 시계열 데이터를 통해 시간 변화에 따른 트렌드를 확인할 수 있습니다.  이 시스템은 **정치 과학 연구, 선거 분석, 미디어 모니터링 등 다양한 분야**에 적용될 수 있으며, **실시간 정보 분석의 새로운 가능성**을 보여줍니다. 특히, **대용량 데이터 처리 및 고급 분석**의 효율성을 높인 점이 주목할 만합니다.  **정확성과 신뢰성을 확보**하기 위한 다양한 노력 또한 돋보입니다.

#### Political Narrative Tracking
본 논문에서 제시된 정치적 담론 추적 시스템은 **실시간으로 라디오 방송의 내용을 분석**하여 정치적 주장, 괴담 및 여론의 흐름을 파악하는 데 초점을 맞춥니다.  **방대한 양의 오디오 데이터를 실시간으로 전사하고 분석**하는 기능은 정치적 담론 분석에 중요한 진전입니다. 특히, **미디어를 통한 정보 확산 양상을 정량적으로 분석**하고, **선거의 공정성에 대한 의혹과 같은 특정 주제에 대한 담론을 추적**하는 데 유용한 도구임을 시사합니다.  하지만, **알고리즘의 편향성**과 **데이터의 대표성**에 대한 고려가 필요하며, **지역적 특성을 고려한 분석**이 더욱 심도있는 연구를 위해 필요합니다.  **다양한 미디어 플랫폼을 아우르는 확장성**을 확보하고, **다국어 지원 기능을 강화**하는 것 또한 향후 연구 방향으로 제시됩니다.

#### Future Research
본 논문은 실시간 라디오 라이브 스트림 콘텐츠 분석을 위한 프레임워크인 WavePulse를 제시합니다.  미래 연구 방향으로는 **전 세계 라디오 방송국으로의 확장**과 **다국어 지원 강화**를 통해 시스템의 전 세계적 적용성을 높이는 것을 고려할 수 있습니다.  **다양한 언어 모델**을 활용한 분석 정확도 향상 및 **사용자 맞춤형 분석 기능** 추가를 통한 사용자 경험 개선도 중요한 과제입니다.  또한,  **데이터 품질 개선**을 위한 노력과 **다양한 분석 기법**의 추가적인 적용을 통한 심층적인 분석 결과 도출이 필요합니다.  **인구 통계 데이터**와의 연계를 통해 라디오 방송의 실제 영향력을 측정하고, **방송국 간 상호 작용 네트워크** 분석을 고도화하여 정보 전파 및 의견 형성 과정에 대한 깊이 있는 이해를 도모하는 연구도 필요합니다.  **윤리적 고려 사항**을 꾸준히 반영하여 책임감 있는 연구를 수행하는 것이 중요하며,  **새로운 기술 발전**을 지속적으로 모니터링하여 WavePulse를 개선하고 확장하는 노력이 필요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.17998/extracted/6086778/appendix_figures/rnnt.png)

> 🔼 그림 2는 미국 전역의 AM/FM 라디오 방송국의 위치를 보여줍니다.  뉴스/토크/비즈니스 뉴스 채널은 '뉴스/토크'로, 퍼블릭 라디오/대학/종교/기타 채널은 '기타'로 그룹핑하여 표시했습니다.  뉴스/토크 채널은 총 347개, 기타 채널은 49개입니다. 이 그림은 논문의 나머지 부분에서 각 주의 라디오 방송국 분포를 참고하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 2. Coverage of Radio Stations. Each marker is an AM / FM station. We clubbed News/Talk/Business-News into 'News/Talk', and Public-Radio/College/Religious/Others into 'Other'. Counts: 'News / Talk' : 347, 'Other': 49. For rest of the US plots, we will use above state labels as reference.
> </details>



![](https://arxiv.org/html/2412.17998/extracted/6086778/appendix_figures/mms_1b.png)

> 🔼 그림 3은 WavePulse 시스템의 출력물 예시를 보여줍니다. 왼쪽 상단에는 음성 녹음본의 시간 정보와 화자 정보를 포함한 JSON 세그먼트 형식의 데이터가, 오른쪽 상단에는 정치 뉴스 관련 대화 내용의 예시가, 왼쪽 하단에는 광고 내용의 예시가, 그리고 하단에는 요약본이 각각 표시되어 있습니다. 이 그림은 WavePulse가 실시간으로 라디오 방송 내용을 기록하고, 전사하고, 화자를 분리하고, 분류하고, 시간 정보를 추가하며, 요약하는 기능을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3. Samples of (Top left) JSON segments (Bottom Right) Corresponding Diarized Time-stamped Political News (Top right) Discussion, (Bottom Left) Advert., and (Bottom) Summary.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Call Sign | Location |
|---|---| 
| WACV | Coosada, AL |
| WAVH | Daphne, AL |
| WGSV | Guntersville, AL |
| WLBF | Montgomery, AL |
| WQSI | Union Springs, AL |
| WTLS | Tallassee, AL |
| KAGV | Big Lake, AK |
| KBKO | Kodiak, AK |
| KFAR | Fairbanks, AK |
| KFNP | North Pole, AK |
| KGSM | Saint Mary’s, AK |
| KSRM | Soldotna, AK |
| KVNT | Eagle River, AK |
| KAWC | Yuma, AZ |
| KDJI | Holbrook, AZ |
| KFNN | Mesa, AZ |
| KFNX | Cave Creek, AZ |
| KQNA | Prescott Valley, AZ |
| KVOI | Cortaro, AZ |
| KVWM | Show Low, AZ |
| KYCA | Presott, AZ |
| KARV | Russellville, AR |
| KBEU | Bearden, AR |
| KBTM | Jonesboro, AR |
| KOMT | Lakeview, AR |
| KRZP | Gassville, AR |
| KUAR | Little Rock, AR |
| KURM | Rogers, AR |
| KAHI | Auburn, CA |
| KBLA | Santa Monica, CA |
| KCAA | Loma Linda, CA |
| KCNR | Shasta, CA |
| KINS | Blue Lake, CA |
| KMET | Banning, CA |
| KMYC | Marysville, CA |
| KOMY | La Selva Beach, CA |
| KPAY | Chico, CA |
| KPRL | Paso Robles, CA |
| KQMS | Redding, CA |
| KSAC | Olivehurst, CA |
| KSCO | Santa Cruz, CA |
| KVTA | Ventura, CA |
| KYOS | Merced, CA |
| KDGO | Durango, CO |
| KFKA | Greeley, CO |
| KGLN | Glenwood Springs, CO |
| KLZ | Denver, CO |
| KNFO | Basalt, CO |
| KPPF | Monument, CO |
| KRDO | Colorado Springs, CO |
| KVFC | Cortez, CO |
| WDRC | Hartford, CT |
| WFOX | Southport, CT |
| WGCH | Greenwich, CT |
| WICC | Bridgeport, CT |
| WLAD | Danbury, CT |
| WSTC | Stamford, CT |
| WDEL | Wilmington, DE |
| WGMD | Reho. Beach, DE |
| WHMS | Pine Creek, DE |
| WIHW | Dover, DE |
| WVCW | Wilmington, DE |
| WCSP | Washington, DC |
| WFED | Washington, DC |
| WPFM | Washington, DC |
| WTOP | Washington, DC |
| PRNN | Pensacola, FL |
| WBOB | Jacksonville, FL |
| WDBO | Orlando, FL |
| WDCF | Dade City, FL |
| WELE | Ormond Beach, FL |
| WFSX | Estero, FL |
| WFTL | West Palm Beach, FL |
| WHBO | Pinellas Park, FL |
| WKEZ | Tavernier, FL |
| WNDB | Daytona Beach, FL |
| WNRP | Pensacola, FL |
| WNZF | Bunnell, FL |
| WPIK | Summerland Key, FL |
| WPSL | Port Saint Lucie, FL |
| WWBA | Largo, FL |
| WWPR | Bradenton, FL |
| WWTK | Lake Placid, FL |
| WXJB | Homosassa, FL |
| WYOO | Springfield, FL |
| WCHM | Clarkesville, GA |
| WDJY | Dallas, GA |
| WDUN | Gainesville, GA |
| WFOM | Marietta, GA |
| WGAC | Harlem, GA |
| WJRB | Young Harris, GA |
| WKWN | Trenton, GA |
| WLAQ | Rome, GA |
| WLBB | Carrollton, GA |
| WRGA | Rome, GA |
| WRWH | Cleveland, GA |
| WSBB | Doraville, GA |
| WVGA | Lakeland, GA |
| WVOP | Vidalia, GA |
| KANO | Hilo, HI |
| KHJC | Lihue, HI |
| KIHL | Hilo, HI |
| KKCR | Hanalei, HI |
| KAOX | Shelley, ID |
| KBOI | New Plymouth, ID |
| KIDG | Shelley, ID |
| KOUW | Island Park, ID |
| WBGZ | Alton, IL |
| WCGO | Evanston, IL |
| WCIL | Carbondale, IL |
| WCMY | Ottawa, IL |
| WCPT | Willow Springs, IL |
| WCRA | Effingham, IL |
| WDAN | Danville, IL |
| WDWS | Champaign, IL |
| WGGH | Marion, IL |
| WJPF | Herrin, IL |
| WLUW | Chicago, IL |
| WMAY | Taylorville, IL |
| WMBD | Peoria, IL |
| WRPW | Colfax, IL |
| WSDR | Sterling, IL |
| WSOY | Decatur, IL |
| WTAD | Quincy, IL |
| WTIM | Assumption, IL |
| WTRH | Ramsey, IL |
| WZUS | Macon, IL |
| WBIW | Bedford, IN |
| WFDM | Franklin, IN |
| WGCL | Bloomington, IN |
| WGL | Fort Wayne, IN |
| WIMS | Michigan City, IN |
| WTRC | Elkhart, IN |
| KBIZ | Ottumwa, IA |
| KFJB | Marshaltown, IA |
| KMA | Shenandoah, IA |
| KOKX | Keokuk, IA |
| KWBG | Boone, IA |
| KXEL | Waterloo, IA |
| KGGF | Coffeyville, KS |
| KINA | Salina, KS |
| KIUL | Garden City, KS |
| KLWN | Lawrence, KS |
| KQAM | Wichita, KS |
| KSAL | Salina, KS |
| KSCB | Liberal, KS |
| KVGB | Great Bend, KS |
| KWBW | Hutchinson, KS |
| KWKN | Wakeeney, KS |
| WDOC | Prestonsburg, KY |
| WHIR | Danville, KY |
| WKCT | Bowling Green, KY |
| WZXI | Lancaster, KY |
| KFXZ | Lafayette, LA |
| KSYL | Alexandria, LA |
| KWLA | Anacoco, LA |{{< /table-caption >}}
> 🔼 이 표는 논문에서 성공적으로 스트리밍된 라디오 방송국 목록과 해당 방송국의 위치 정보를 보여줍니다.  단순히 방송국 이름과 위치만 나열하는 것이 아니라, 논문에서 사용된 데이터의 출처와 범위를 명확히 보여주는 역할을 합니다.  연구의 신뢰성과 재현성을 높이기 위해 필수적인 정보를 제공합니다.
> <details>
> <summary>read the caption</summary>
> Table 2. List of successfully streamed Radio Stations along with their location.
> </details>

{{< table-caption >}}
| Call Sign | Location |
|---|---| 
| WBOK | New Orleans, LA |
| WEGP | Presque Isle, ME |
| WLOB | Portland, ME |
| WMEA | Portland, ME |
| WBAL | Baltimore, MD |
| WCBM | Baltimore, MD |
| WFMD | Frederick, MD |
| WBNW | Concord, MA |
| WGAW | Gardner, MA |
| WNBP | Newburyport, MA |
| WSAR | Fall River, MA |
| WAAM | Ann Arbor, MI |
| WBRN | Big Rapids, MI |
| WCXI | Fenton, MI |
| WIOS | Tawas City, MI |
| WKHM | Jackson, MI |
| WKNW | Sault Sainte Marie, MI |
| WLDN | Ludington, MI |
| WMIC | Sandusky, MI |
| WMPL | Hancock, MI |
| WPHM | Port Huron, MI |
| WSJM | Benton Harbor, MI |
| WTCM | Traverse City, MI |
| KBRF | Fergus Falls, MN |
| KKBJ | Bemidji, MN |
| KLTF | Little Falls, MN |
| KNSI | Saint Louis, MN |
| KROX | Crookston, MN |
| KTRF | Thief River Falls, MN |
| KXRA | Alexandria, MN |
| WZFG | Dilworth, MN |
| WMXI | Ellisville, MS |
| WVBG | Vicksburg, MS |
| WYAB | Pocahontas, MS |
| KFMO | Flat River, MO |
| KICK | Springfield, MO |
| KRMS | Osage Beach, MO |
| KRTK | Hermann, MO |
| KSIM | Sikeston, MO |
| KSWM | Aurora, MO |
| KTRS | Saint Louis, MO |
| KTTR | Saint James, MO |
| KTUI | Sullivan, MO |
| KWOC | Poplar Bluff, MO |
| KWPM | West Plains, MO |
| KZIM | Cape Girardeau, MO |
| KZRG | Joplin, MO |
| KZYM | Joplin, MO |
| KAFH | Great Falls, MT |
| KALS | Kalispell, MT |
| KAPC | Butte, MT |
| KBGA | Missoula, MT |
| KBMC | Bozeman, MT |
| KCAP | Helena, MT |
| KINX | Fairfield, MT |
| KJJR | Whitefish, MT |
| KGFW | Kearney, NE |
| KLIN | Lincoln, NE |
| KODY | North Platte, NE |
| KOIL | Omaha, NE |
| KOLT | Terrytown, NE |
| KRGI | Grand Island, NE |
| WJAG | Norfolk, NE |
| KAVB | Hawthorne, NV |
| KELY | Ely, NV |
| KKFT | Gardnerville-Minden, NV |
| KLNR | Panaca, NV |
| KNCC | Elko, NV |
| WEMJ | Laconia, NH |
| WNTK | New London, NH |
| WTSN | Dover, NH |
| WUVR | Lebanon, NH |
| WFJS | Trenton, NJ |
| WFMU | East Orange, NJ |
| WOND | Pleasantville, NJ |
| WVBV | Medford Lakes, NJ |
| KEND | Roswell, NM |
| KENN | Farmington, NM |
| KINN | Alamogordo, NM |
| KKOB | Albuquerque, NM |
| KOBE | Las Cruces, NM |
| KRSY | Alamogordo, NM |
| KSVP | Artesia, NM |
| KXKS | Albuquerque, NM |
| WATN | Watertown, NY |
| WAUB | Auburn, NY |
| WBAI | New York, NY |
| WFME | Garden City, NY |
| WGBB | Freeport, NY |
| WGDJ | Rensselaer, NY |
| WGVA | Geneva, NY |
| WJJF | Montauk, NY |
| WKCR | New York, NY |
| WLNL | Horseheads, NY |
| WLVL | Lockport, NY |
| WNYU | New York, NY |
| WRHU | Hempstead, NY |
| WTBQ | Warwick, NY |
| WUTQ | Utica, NY |
| WVBN | Bronxville, NY |
| WWSK | Smithtown, NY |
| WYSL | Avon, NY |
| WBT | Charlotte, NC |
| WEEB | Southern Pines, NC |
| WGNC | Gastonia, NC |
| WHKY | Hickory, NC |
| WNOS | New Bern, NC |
| WOBX | Wanchese, NC |
| WRHT | Morehead City, NC |
| WSJS | Winston-Salem, NC |
| WSPC | Albemarle, NC |
| WTIB | Willamston, NC |
| KNOX | Grand Forks, ND |
| KTGO | Tioga, ND |
| WDAY | Fargo, ND |
| WCBE | Columbus, OH |
| WDBZ | Cincinnati, OH |
| WHIO | Dayton, OH |
| WHTX | Warren, OH |
| WINT | Willoughby, OH |
| WLYV | Bellaire, OH |
| WNIR | Kent, OH |
| WYOH | Niles, OH |
| KCLI | Cordell, OK |
| KGWA | Enid, OK |
| KGYN | Guymon, OK |
| KQOB | Enid, OK |
| KRMG | Tulsa, OK |
| KTLR | Oklahoma City, OK |
| KWON | Bartlesville, OK |
| WBBZ | Ponca City, OK |
| KAGO | Klamath Falls, OR |
| KBND | Bend, OR |
| KBNP | Portland, OR |
| KFIR | Sweet Home, OR |
| KFLS | Klamath Falls, OR |
| KGAL | Lebanon, OR |
| KMED | Eagle Point, OR |
| KPNW | Eugene, OR |
| KSLM | Salem, OR |
| KUMA | Pendleton, OR |
| KVBL | Union, OR |
| KWRO | Coquille, OR |
| KYKN | Keizer, OR |
| WATS | Sayre, PA |
| WBVP | Beaver Falls, PA |
| WCED | Du Bois, PA |
| WEEU | Reading, PA |
| WFYL | King of Prussia, PA |
| WKHB | Irwin, PA |
| WPSN | Honesdale, PA |
| WRSC | Bellefonte, PA |
| WRTA | Altoona, PA |{{< /table-caption >}}
> 🔼 이 표는 논문의 데이터 수집 과정에서 성공적으로 스트리밍된 라디오 방송국 목록과 해당 방송국의 위치를 보여줍니다.  표 3은 이전 페이지에서 계속되는 표이며, 미국 전역에 있는 수많은 라디오 방송국들의 주(State)와 방송국 호출 부호(Call Sign)를 나열합니다. 이 정보는 논문에서 WavePulse 시스템의 광범위한 적용 범위를 보여주는 데 사용됩니다.  방송국 위치는 지역적인 뉴스나 정치적 담론의 다양성을 분석하는 데 중요한 역할을 합니다.
> <details>
> <summary>read the caption</summary>
> Table 3. List of successfully streamed Radio Stations along with their location (continued).
> </details>

{{< table-caption >}}
| Call Sign | Location |
|---|---| 
| WTRW | Carbondale, PA |
| WURD | Philadelphia, PA |
| WEAN | Wakefield-Peacedale, RI |
| WNPE | Narragansett Pier, RI |
| WSJW | Pawtucket, RI |
| WAIM | Anderson, SC |
| WCRS | Greenwoord, SC |
| WDXY | Sumter, SC |
| WFRK | Quinby, SC |
| WRHI | Rock Hill, SC |
| WRNN | Socastee, SC |
| WTKN | Murrells Inlet, SC |
| KAUR | Sioux Falls, SD |
| KELQ | Flandreau, SD |
| KOTA | Rapid City, SD |
| KWAM | Memphis, TN |
| WBFG | Parker’s Crossroads, TN |
| WCMT | Martin, TN |
| WENO | Nashville, TN |
| WGNS | Murfreesboro, TN |
| WHUB | Cookeville, TN |
| WUCT | Algood, TN |
| KBST | Big Spring, TX |
| KCRS | Midland, TX |
| KKSA | San Angelo, TX |
| KLVT | Levelland, TX |
| KRDY | San Antonio, TX |
| KRFE | Lubbock, TX |
| KWEL | Midland, TX |
| KXYL | Brownwood, TX |
| KZHN | Paris, TX |
| KZHN | Paris, TX |
| WTAW | College Station, TX |
| KBJA | Sandy, UT |
| KJJC | Murray, UT |
| KMXD | Monroe, UT |
| KOAL | Price, UT |
| KSGO | Saint George, UT |
| KSVC | Richfield, UT |
| KVNU | Logan, UT |
| WBTN | Bennington, VT |
| WCKJ | Saint Johnsbury, VT |
| WJPL | Barre, VT |
| WJSY | Newport, VT |
| WMTZ | Rutland, VT |
| WVMT | Burlington, VT |
| WCHV | Charlottesville, VA |
| WFJX | Roanoke, VA |
| WGMN | Roanoke, VA |
| WIQO | Forest, VA |
| WJFV | Portsmouth, VA |
| WLNI | Lynchburg, VA |
| WMNA | Gretna, VA |
| WNIS | Norfolk, VA |
| WRAD | Radford, VA |
| WRCW | Warrenton, VA |
| KEDO | Longview, WA |
| KELA | Centralia-Chehalis, WA |
| KGDC | Walla Walla, WA |
| KGTK | Olympia, WA |
| KITZ | Silverdale, WA |
| KKNW | Seattle, WA |
| KLCK | Goldendale, WA |
| KNWN | Seattle, WA |
| KODX | Seattle, WA |
| KONP | Port Angeles, WA |
| KOZI | Chelan, WA |
| KSBN | Spokane, WA |
| KTEL | Walla Walla, WA |
| KVI | Seattle, WA |
| KXLY | Spokane, WA |
| WMOV | Ravenswood, WV |
| WRNR | Martinsburg, WV |
| WSCW | South Charleston, WV |
| WWNR | Beckley, WV |
| KFIZ | Fond Du Lac, WI |
| WAUK | Jackson, WI |
| WCLO | Janesville, WI |
| WFHR | Wisconsin Rapids, WI |
| WISS | Berlin, WI |
| WLCX | La Crosse, WI |
| WMDX | Columbus, WI |
| WSAU | Rudolph, WI |
| WTAQ | Glenmore, WI |
| WXCO | Wausau, WI |
| KBUW | Buffalo, WY |
| KROE | Sheridan, WY |
| KVOW | Riverton, WY |{{< /table-caption >}}
> 🔼 이 표는 논문의 데이터 수집에 사용된 라디오 방송국 목록의 일부를 보여줍니다.  표에는 각 방송국의 호출 부호와 위치가 나열되어 있습니다.  논문에서는 미국 전역의 396개 라디오 방송국에서 스트리밍된 오디오 데이터를 분석했으며, 이 표는 그 방송국들의 목록을 보여줍니다.  계속되는 표는 논문의 부록에 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 4. List of successfully streamed Radio Stations along with their location (continued).
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