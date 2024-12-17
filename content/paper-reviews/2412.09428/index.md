---
title: "Multimodal Music Generation with Explicit Bridges and Retrieval Augmentation"
summary: "VMB는 텍스트 및 음악 브리지를 활용하여 멀티모달 음악 생성을 위한 새롭고 제어 가능한 프레임워크를 제시합니다."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Multimodal Generation", "🏢 University of Edinburgh",]
showSummary: true
date: 2024-12-12
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.09428 {{< /keyword >}}
{{< keyword icon="writer" >}} Baisen Wang et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-16 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.09428" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.09428" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/multimodal-music-generation-with-explicit" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

멀티모달 음악 생성은 텍스트, 비디오, 이미지와 같은 다양한 입력 양식에서 음악을 생성하는 것을 목표로 합니다. 기존 방법은 데이터 부족, 교차 양식 정렬 불량 및 제어 가능성 부족으로 어려움을 겪습니다. 이 논문에서는 멀티모달 정렬을 위한 텍스트 및 음악의 명시적 브리지 사용과 관련된 문제점을 해결합니다.텍스트 브리지는 시각적 입력을 상세한 음악적 설명으로 변환하고, 음악 브리지는 광범위한 주제 정렬과 대상 속성 제어를 통해 관련 음악을 검색합니다. 이러한 브리지를 활용하여 명시적으로 조건부 음악 생성 프레임워크가 구축되어 품질, 양식 및 사용자 정의 정렬이 향상됩니다. 제안된 VMB(Visuals Music Bridge) 프레임워크는 멀티모달 음악 설명 모델, 이중 트랙 음악 검색 모듈 및 명시적 조건부 음악 생성 모듈로 구성됩니다. 실험 결과는 VMB가 기존 방법에 비해 음악 품질, 양식 정렬 및 제어 가능성을 크게 향상시킨다는 것을 보여줍니다. VMB는 다양한 멀티미디어 분야에서 응용 가능성이 있는 해석 가능하고 표현력이 풍부한 멀티모달 음악 생성을 위한 새로운 표준을 제시합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} VMB는 멀티모달 음악 생성에서 텍스트와 음악을 명시적 브리지로 사용합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 이중 트랙 음악 검색 모듈은 광범위하고 대상이 지정된 검색 전략을 결합합니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 명시적 조건부 음악 생성 프레임워크는 향상된 품질과 제어 가능성을 제공합니다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**멀티모달 음악 생성은 텍스트, 이미지, 비디오와 같은 다양한 입력 양식에서 음악을 생성하는 것을 목표로 합니다.** 이 논문은 현재 연구 동향과 관련이 있으며, 생성된 음악의 품질과 입력 양식 간의 정렬을 개선하여 멀티미디어 분야의 연구자들에게 매우 중요합니다. **VMB는 교차 양식 정렬 문제를 해결하고 미세 조정 제어 기능을 제공하여 향후 멀티모달 음악 생성 연구를 위한 새로운 길을 열어줍니다.**

------
#### Visual Insights



![](https://arxiv.org/html/2412.09428/extracted/6065175/figs/framework.png)

> 🔼 VMB 프레임워크는 멀티모달 음악 생성을 위해 텍스트와 음악을 두 가지 명시적 브리지로 사용합니다. 멀티모달 음악 설명 모델은 텍스트 형식의 음악 설명을 생성하고, 듀얼 트랙 음악 검색 모듈은 참조 음악을 검색합니다. 이 두 브리지는 명시적 조건부 음악 생성 모듈에 입력되어 최종 음악을 생성합니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Overview of the VMB framework. We employ text and music as two explicit bridges for multimodal music generation. Text-form music description is obtained with the Multimodal Music Description model. Reference music is retrieved with the Dual-track Music Retrieval module. The two bridges are fed into the Explicitly Conditioned Music Generation module to generate output music.
> </details>





{{< table-caption >}}
| Method | Inference Time | KL<sub>passt</sub>↓ | FD<sub>openl3</sub>↓ | IB↑ | MP | EC | TC | RC |
|---|---|---|---|---|---|---|---|---| 
| CMT [13] | ~3 min | 52.76 | 269.63 | 8.54 | 3.19 | 2.81 | 2.79 | 3.10 |
| Video2music [26] | ~1 min | 103.56 | 533.46 | 5.26 | 3.05 | 2.58 | 2.64 | 2.67 |
| VidMuse [51] | ~13 min | 56.48 | 187.13 | **22.09** | 3.01 | 2.91 | 3.05 | 3.02 |
| M<sup>2</sup>UGen [34] | ~40 s | 60.41 | 180.72 | 15.58 | 2.84 | 2.32 | 2.37 | 2.71 |
| VMB (ours) | ~20 s | **48.84** | **105.84** | 21.62 | **3.85** | **3.36** | **3.38** | **3.62 |{{< /table-caption >}}

> 🔼 표 1은 SymMV 데이터셋에서 다양한 비디오-음악 생성 모델의 성능을 비교합니다. KLpasst, FDopenl3, IB는 객관적인 지표이고, MP, EC, TC, RC는 주관적인 지표입니다. 객관적인 지표는 생성된 음악의 품질과 실제 음악 데이터 분포와의 유사성을 측정하며, 주관적인 지표는 생성된 음악과 비디오 콘텐츠 간의 정서적, 주제적, 리듬적 일치성을 평가합니다. VMB는 대부분의 지표에서 기존 방법보다 우수한 성능을 보입니다. 특히, VMB는 객관적인 지표에서 가장 낮은 KLpasst와 FDopenl3 점수를 달성했으며, 이는 생성된 음악이 실제 음악 분포와 더 유사하고 높은 지각적 품질을 나타냄을 시사합니다. 또한 VMB는 VidMuse보다 추론 시간이 훨씬 짧습니다. 주관적인 평가 결과, VMB는 시각적 내용과 감정적으로나 주제적으로 일치하는 음악을 생성하는 능력이 뛰어남을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Video-to-music generation performance on SymMV dataset. Up/down arrows indicate the desired direction for improvement.
> </details>





### In-depth insights


#### Bridging Modalities
**멀티모달 음악 생성에서 텍스트와 음악을 명시적 다리로 활용하는 VMB 프레임워크를 제안합니다.** VMB는 멀티모달 정렬, 데이터 부족, 제한된 제어 가능성 문제를 해결합니다. 멀티모달 음악 설명 모델은 시각적 입력을 텍스트 설명으로 변환하여 텍스트 다리를 제공합니다. 듀얼 트랙 음악 검색 모듈은 광범위하고 구체적인 검색 전략을 결합하여 음악 다리를 제공하고 사용자 제어를 가능하게 합니다. **명시적 조건부 음악 생성 프레임워크는 두 다리를 기반으로 음악을 생성합니다.** VMB는 음악 품질, 양식 및 사용자 지정 정렬을 향상시킵니다. **이 프레임워크는 다양한 멀티미디어 분야에서 해석 가능하고 표현력이 풍부한 멀티모달 음악 생성을 위한 새로운 표준을 설정합니다.**

#### Dual Retrieval Power
**이중 검색 기능**은 다양한 방식으로 콘텐츠 생성을 향상시키는 강력한 도구입니다. 광범위한 검색은 입력과 의미적으로 일치하는 콘텐츠를 가져와 생성된 결과물의 전반적인 **관련성과 정확성**을 높입니다. 대상 검색을 통해 사용자는 특정 속성이나 스타일을 지정하여 생성 프로세스를 세밀하게 제어할 수 있습니다. 이러한 두 가지 검색 전략을 결합하면 생성된 콘텐츠의 **품질과 다양성**이 향상될 뿐만 아니라 사용자 의도와 **일치**하는 정도 또한 높아집니다. 이중 검색 기능을 사용하면 입력의 **핵심 요소**를 포착하여 풍부하고 매력적인 콘텐츠를 생성할 수 있습니다.

#### Explicit Music Control
**명시적 음악 제어**는 VMB 프레임워크의 핵심으로, 생성된 음악의 다양한 측면을 **정밀하게 조정**할 수 있도록 합니다. 이 기능을 통해 사용자는 장르, 악기, 분위기, 템포와 같은 속성을 **직접 수정**하여 원하는 음악적 결과를 얻을 수 있습니다. 이러한 제어 수준은 기존 방식과 비교했을 때 크게 향상된 것으로, 단순히 텍스트 프롬프트에 의존하는 대신 음악 제작 과정에 대한 **더 큰 영향력**을 제공합니다. 특히, 대상 검색 모듈을 통해 특정 음악적 특징을 가진 음악을 검색하고, 이를 생성 프로세스에 통합하여 원하는 스타일과 분위기를 **정확하게 반영**할 수 있습니다. 이러한 명시적 제어는 음악 생성에서 새로운 가능성을 열어주며, 사용자의 창의적 비전을 실현하는 데 **강력한 도구**를 제공합니다. 향후 연구에서는 더욱 세분화된 제어 기능을 통해 사용자 경험을 향상시키고 다양한 음악 스타일을 포괄적으로 지원하는 방향으로 발전할 것으로 예상됩니다.

#### Beyond Local Rhythm
**리듬 중심 접근 방식의 한계**: VMB는 국소 리듬에 집중하는 대신 더 넓은 관점을 강조하여 기존 방법보다 우수한 성능을 달성합니다. 이는 국소 리듬에 과도하게 집중하면 음악의 전체적인 일관성과 넓은 서사와의 조화가 어려워질 수 있음을 시사합니다. 균형 잡힌 접근 방식을 채택함으로써 VMB는 의도된 감정적 맥락과 밀접하게 일치하면서 리듬 흐름을 유지하여 향상된 시청각 경험을 제공합니다.

#### Dataset Diversity Limits
**데이터셋 다양성 제한**은 생성 음악 품질에 큰 영향을 미칩니다. 훈련 데이터의 다양성 부족은 **모델이 특정 스타일이나 장르에 과적합**되도록 하여 새로운 입력에 대한 일반화 능력을 저해합니다. 예를 들어 모델이 주로 팝 음악에 대해 훈련된 경우 록이나 클래식 음악을 생성하는 데 어려움을 겪을 수 있습니다. 마찬가지로 **문화적 다양성 부족**은 편향된 결과를 초래할 수 있습니다. 모델이 서양 음악에 대해 주로 훈련된 경우 비서양 음악의 뉘앙스를 포착하지 못할 수 있습니다. 따라서 다양한 음악 스타일, 장르 및 문화적 배경을 나타내는 **포괄적인 데이터셋**이 필수적입니다. **고품질 음악**을 생성하려면 훈련 데이터의 음악적 무결성 또한 중요합니다. 노이즈가 많거나 품질이 낮은 음악으로 훈련된 모델은 품질이 낮거나 원하지 않는 아티팩트가 있는 음악을 생성할 수 있습니다. 따라서 **세심하게 큐레이션되고 품질이 높은 데이터**를 사용하는 것이 중요합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.09428/extracted/6065175/figs/3.1.png)

> 🔼 다중 모드 음악 설명 모델(MMDM)의 파이프라인은 음악 비디오 수집으로 시작하여 CLAP 임베딩 유사성을 사용한 자동 태깅을 통해 오디오 주석을 개선합니다. 메타데이터와 주제 설명은 Llama 3.1 모델에 의해 합성되어 훈련 목표를 생성합니다. MMDM의 훈련은 LoRA 미세 조정을 활용하여 다중 모드 입력을 시각적 콘텐츠의 테마와 일치하는 대상 음악 설명으로 변환합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Pipeline of the Multimodal Music Description Model (MMDM). This process starts with the collection of music videos, followed by automated tagging to refine audio annotations using CLAP embedding similarities. Metadata and thematic descriptions are synthesized by the Llama 3.1 model to create training targets. The training utilizes LoRA fine-tuning in the MMDM to transform multimodal inputs into targeted music descriptions that align with the visual content’s themes.
> </details>



![](https://arxiv.org/html/2412.09428/extracted/6065175/figs/3.2.png)

> 🔼 이 그림은 이중 트랙 음악 검색 및 명시적 조건부 음악 생성 프레임워크를 보여줍니다. 왼쪽 부분은 광범위 검색과 대상 검색 전략을 모두 활용하는 이중 트랙 음악 검색 프로세스를 보여주고, 오른쪽 부분은 선택한 음악 브리지, 텍스트 브리지, 노이즈 입력에서 임베딩을 통합하는 ControlFormer 블록을 통해 음악이 생성되는 명시적 조건부 음악 생성 경로를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Framework of Dual-track Music Retrieval and Explicitly Conditioned Music Generation. The left part illustrates the Dual-track Music Retrieval process, which leverages our multimodal dataset to perform both broad and targeted retrieval. The right part shows the Explicitly Conditioned Music Generation pathway, where music is generated through a ControlFormer block integrating embeddings from selected music bridge, text bridge, and noisy inputs.
> </details>



![](https://arxiv.org/html/2412.09428/extracted/6065175/figs/Distribution_of_PAM_Scores.png)

> 🔼 이 표는 비디오-투-텍스트 생성 성능을 보여줍니다. GPT-4V, InternVL, MMDM 세 가지 모델의 성능을 비교하고 있습니다. CLAP 점수를 기준으로 평가했을 때, MMDM이 가장 높은 점수를 기록했습니다. 이는 MMDM이 비디오에서 음악 설명을 생성하는 데 가장 효과적임을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Video-to-Description Generation Performance.
> </details>



![](https://arxiv.org/html/2412.09428/extracted/6065175/figs/dataset_distributions.png)

> 🔼 이 표는 VMB 모델의 속성 제어 기능에 대한 평가 결과를 보여줍니다. 악기, 장르, 분위기와 같은 다양한 음악 속성을 변경하면서 생성된 음악의 변화를 CLAPScore의 평균 변화량(Δ)으로 측정했습니다. 표에서 Instrument는 악기 변경에 따른 CLAPScore의 평균 변화량이 가장 큰 것을 보여주는데, 이는 CLAP이 악기 특징에 민감하기 때문일 가능성이 높습니다. Genre와 Mood의 변화량은 상대적으로 작지만, VMB가 장르와 분위기를 조절할 수 있다는 것을 보여줍니다. 이러한 결과는 VMB가 다양한 입력에 적응하고 음악적 속성을 효과적으로 조절할 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Attribute control effectiveness measured by average change (ΔΔ\Deltaroman_Δ) in CLAPScore.
> </details>



![](https://arxiv.org/html/2412.09428/extracted/6065175/figs/dataset_distributions2.png)

> 🔼 훈련 데이터셋에 있는 원시 오디오의 PAM 점수 분포를 히스토그램으로 보여줍니다. 대부분의 PAM 점수가 0.8에서 1.0 사이에 집중되어 있어 데이터셋의 전반적인 품질이 높음을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Distribution of PAM Scores across the raw training dataset.
> </details>



![](https://arxiv.org/html/2412.09428/extracted/6065175/figs/mood_distribution.png)

> 🔼 훈련 데이터셋에 있는 음악 길이 분포를 히스토그램으로 보여줍니다. 대부분의 음악 길이가 100초에서 200초 사이에 집중되어 있음을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Histogram of music duration in the training dataset.
> </details>



![](https://arxiv.org/html/2412.09428/extracted/6065175/figs/genre_distribution.png)

> 🔼 훈련 데이터셋에 있는 텍스트 단어 수의 히스토그램입니다. 텍스트 설명의 길이 분포를 보여주며, 대부분의 텍스트가 중간 범위에 속하는 것을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Histogram of text word counts in the training dataset.
> </details>



![](https://arxiv.org/html/2412.09428/extracted/6065175/figs/instrument_distribution.png)

> 🔼 이 히스토그램은 검색 데이터셋에 있는 다양한 무드 태그의 분포를 보여줍니다. fun, energetic, romantic, emotional, holiday, positive, dream, calm, dark 등 다양한 무드 카테고리의 빈도를 보여주며, 데이터셋에 포함된 감정적 다양성을 보여줍니다. 이 다양한 무드 데이터는 다양한 감정을 표현하는 음악 생성 모델을 훈련하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Distribution of mood tags across the retrieval dataset. This histogram shows the frequency of various mood categories, illustrating the emotional diversity captured in our data.
> </details>



![](https://arxiv.org/html/2412.09428/extracted/6065175/figs/bpm_distribution.png)

> 🔼 이 막대 그래프는 검색 데이터셋에 포함된 다양한 음악 장르의 분포를 보여줍니다. 팝, 힙합 및 랩, 포크 및 컨트리, 라틴 음악, 일렉트로닉 음악 등 다양한 장르가 포함되어 있음을 알 수 있습니다. 이 다양성은 데이터셋이 장르별 검색 작업에 폭넓게 적용될 수 있음을 시사합니다. 즉, 특정 장르의 음악을 검색하고 생성하는 데 유용하게 활용될 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Genre distribution within the retrieval dataset. This bar graph reflects the variety of music genres represented, indicating the dataset’s broad applicability for genre-specific retrieval tasks.
> </details>



![](https://arxiv.org/html/2412.09428/extracted/6065175/figs/hist_audio_duration.png)

> 🔼 이 히스토그램은 검색 데이터셋에 있는 악기 태그의 범위를 보여줍니다. 데이터셋이 다양한 악기를 포괄적으로 포함하고 있음을 보여줍니다. 데이터셋에는 현악기, 건반악기, 관악기, 타악기, 기타 등 다양한 악기들이 포함됩니다. 이러한 다양성은 VMB 프레임워크의 검색 기능을 통해 다양한 장르와 스타일의 음악 생성을 가능하게 합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: Histogram of instrument tags in our retrieval dataset. This figure shows the range of musical instruments represented, underscoring the dataset’s comprehensive coverage of instrumental music.
> </details>



![](https://arxiv.org/html/2412.09428/extracted/6065175/figs/hist_text_word_count.png)

> 🔼 이 그래프는 검색 데이터셋에 있는 BPM(Beats Per Minute, 분당 박자 수)의 분포를 보여주는 밀도 곡선입니다. 곡의 템포 범위가 얼마나 다양한지 보여줍니다. 즉, 데이터셋에 다양한 템포의 음악이 포함되어 있음을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 10: Density curve of BPM across the retrieval dataset. This plot illustrates the distribution of Beats Per Minute, showcasing the tempo range covered in our collection.
> </details>



![](https://arxiv.org/html/2412.09428/extracted/6065175/figs/hist_lexical_diversity.png)

> 🔼 이 히스토그램은 검색 데이터 세트에 있는 오디오 길이 분포를 보여주며, 데이터 세트에 있는 노래 길이 분포를 나타냅니다. 대부분의 오디오 파일 길이는 특정 범위 내에 집중되어 있어 데이터 세트 전체에서 일관된 길이를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 11: Histogram of audio durations in retrieval dataset. This shows the distribution of song lengths in the dataset.
> </details>



![](https://arxiv.org/html/2412.09428/extracted/6065175/figs/survey.jpg)

> 🔼 이 히스토그램은 검색 데이터셋에 있는 텍스트 단어 수의 분포를 보여줍니다. 대부분의 텍스트는 중간 범위에 속하며, 다양한 텍스트 길이를 나타냅니다. 이는 연관된 텍스트 데이터의 단어 수 분포를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Histogram of text word counts in retrieval dataset. This represents the distribution of word counts in the associated text data.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Method | KL<sub>passt</sub>↓ | FD<sub>openl3</sub>↓ | CLAPScore↑ | IB↑ | MP | TMA | 
|---|---|---|---|---|---|---| 
| Stable Audio Open [17] | 42.89 | 183.09 | **40.92** | 24.67 | 3.41 | **3.52** | 
| MusicGen [8] | 46.89 | 181.59 | 33.95 | 22.46 | 3.11 | 3.35 | 
| AudioLDM [33] | 99.85 | 293.86 | 17.61 | 20.01 | 2.34 | 2.71 | 
| M<sup>2</sup>UGen [34] | 49.03 | 188.84 | 28.76 | 16.70 | 3.19 | 3.27 | 
| VMB (ours) | **37.43** | **132.16** | 39.66 | **29.36** | **3.78** | 3.48 |{{< /table-caption >}}
> 🔼 텍스트-음악 생성 모델들의 SongDescriber 데이터셋에서의 성능을 객관적 지표와 주관적 지표로 평가한 결과를 보여주는 표입니다. 객관적 지표에는 생성된 음악의 실제 음악 분포와의 유사성을 측정하는 KLpasst, 생성된 음악의 지각적 음질을 평가하는 FDopenl3, 생성된 음악 설명과 비디오 콘텐츠 간의 정렬을 측정하는 CLAPScore, 비디오 또는 이미지와 생성된 음악 간의 교차 모달 의미 정렬을 측정하는 IB가 포함됩니다. 주관적 지표에는 음악적 즐거움(MP)과 텍스트-음악 정렬(TMA)이 포함됩니다. 표에서 VMB는 대부분의 지표에서 다른 모델보다 우수한 성능을 보입니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Text-to-music generation performance on SongDescriber dataset.
> </details>

{{< table-caption >}}
| Method | KL<sub>*passt*</sub>↓ | FD<sub>*openl3*</sub>↓ | IB↑ |
|---|---|---|---| 
| CoDi [50] | 216.48 | 251.52 | 9.60 |
| M<sup>2</sup>UGen [34] | 128.33 | 247.42 | 2.28 |
| VMB (ours) | **105.60** | **119.76** | **11.88** |{{< /table-caption >}}
> 🔼 MUImage 데이터셋에서 이미지를 음악으로 변환하는 생성 성능을 객관적인 지표로 측정한 결과입니다. KLpasst, FDopenl3는 생성된 음악과 실제 음악 데이터 분포의 유사성 및 지각적 음질을 평가하고, IB(Inception-Based Score)는 이미지와 생성된 음악 간의 의미적 연관성을 측정합니다. 표에서 VMB는 다른 모델들에 비해 KLpasst와 FDopenl3 점수가 낮고 IB 점수가 높아, 실제 음악 분포와 유사하고 이미지 내용을 잘 반영한 고품질 음악을 생성함을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Image-to-music generation performance on MUImage dataset.
> </details>

{{< table-caption >}}
| Model | CLAPScore | 
|---|---| 
| GPT-4V [41] | 44.41 | 
| InternVL [6] | 44.21 | 
| MMDM | 50.88 |{{< /table-caption >}}
> 🔼 이 표는 SymMV 데이터셋을 사용한 비디오-투-뮤직 생성 작업에서 모델 구성 요소의 ablation study 결과를 보여줍니다. BR은 광범위 검색을, TR은 타겟 검색을 나타냅니다. 두 검색 전략을 모두 사용했을 때 모든 지표에서 최고의 성능을 보이는 것을 알 수 있습니다. 특히, 두 전략의 조합은 KL 발산과 FDopenl3 점수가 가장 낮아 주제 정렬 및 지각 품질이 향상되었음을 나타냅니다. BR은 입력 콘텐츠와의 정렬을 개선하는 반면 TR은 더 높은 IB 점수에서 반영된 것처럼 창의성을 향상시킵니다. 이러한 결과는 비디오-투-뮤직 작업에서 고품질의 관련성 있고 창의적인 음악을 생성하기 위해 BR과 TR이 모두 중요하다는 것을 보여줍니다. ablation study 결과는 BR과 TR이 상호 보완적인 역할을 하여 음악 생성을 개선함을 강조합니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Ablation of model components on video-to-music generation with SymMV dataset. BR, TR represent broad retrieval and target retrieval respectively.
> </details>

{{< table-caption >}}
| Attribute | Change (Δ) |
|---|---| 
| Instrument | +11.46 |
| Genre | +3.03 |
| Mood | +4.14 |{{< /table-caption >}}
> 🔼 이 표는 다양한 템포 조건(빠름, 중간, 느림)에서 생성된 음악의 평균 BPM(Beats Per Minute)을 보여줍니다. 이를 통해 VMB 모델이 음악 생성 시 템포 제어 기능이 어느 정도 효과적인지 평가할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Average BPM of music generated under varying tempo conditions.
> </details>

{{< table-caption >}}
| BR | TR | KL<sub>*passt*</sub>↓ | FD<sub>*openl3*</sub>↓ | IB↑ |
|---|---|---|---|---| 
| ✓ | ✓ | **75.29** | **177.27** | **24.70** |
| ✓ | × | 91.89 | 199.74 | 20.73 |
| × | ✓ | 91.07 | 387.14 | 20.51 |
| × | × | 96.42 | 360.29 | 14.67 |{{< /table-caption >}}
> 🔼 이 표는 다양한 이미지에 대한 음악 설명 생성 샘플을 보여줍니다. 각 이미지에는 GPT-4 평가 점수, 이유, 감정 매칭, 장면 연관성 및 결론과 함께 설명이 제공됩니다. 이 표는 모델의 시각적 입력을 음악적 설명으로 변환하는 능력을 보여주는 데 사용됩니다. 시각적-설명 생성 작업은 멀티모달 음악 생성 시스템의 핵심 구성 요소입니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Samples of visual-to-description generation.
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