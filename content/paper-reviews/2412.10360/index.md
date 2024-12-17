---
title: "Apollo: An Exploration of Video Understanding in Large Multimodal Models"
summary: "Apollo: 대규모 멀티모달 모델의 비디오 이해를 위한 심층 탐구."
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Vision-Language Models", "🏢 Meta GenAI",]
showSummary: true
date: 2024-12-13
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2412.10360 {{< /keyword >}}
{{< keyword icon="writer" >}} Orr Zohar et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2024-12-16 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2412.10360" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2412.10360" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/apollo-an-exploration-of-video-understanding" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

비디오 LMM은 정적 이미지를 넘어 풍부하고 역동적인 정보를 제공하지만, 높은 계산 요구 사항과 복잡한 디자인 공간으로 인해 개발이 어려웠습니다. 기존 연구에서는 비디오 샘플링, 표현 학습, 토큰 리샘플링 및 통합과 같은 비디오 관련 설계 선택의 영향을 완전히 탐구하지 않았습니다. 이로 인해 많은 설계 결정이 제대로 된 정당성이나 분석 없이 이루어져 비디오 LMM의 발전이 더뎌졌습니다.

이 논문에서는 비디오 LMM의 디자인 공간에 대한 포괄적인 탐구를 제시합니다. Scaling Consistency를 소개하여 작은 모델에서 얻은 설계 통찰력이 더 큰 모델로 효과적으로 전달될 수 있음을 보여줍니다. 이를 통해 계산 비용이 절감되고 효율적인 실험이 가능합니다. 비디오 샘플링, 아키텍처, 데이터 구성, 훈련 일정 등 비디오 관련 측면을 광범위하게 연구합니다. 또한, 시간적 추론 및 지각 작업에 중점을 둔 새로운 벤치마크인 ApolloBench를 제안합니다. 마지막으로, 다양한 모델 크기에서 뛰어난 성능을 달성하는 최첨단 비디오 LMM 제품군인 Apollo를 소개합니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 비디오 LMM에서 설계 결정은 작은 모델과 데이터 세트에서 더 큰 모델로 효과적으로 전달됩니다(Scaling Consistency). {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 초당 프레임 샘플링은 균일 프레임 샘플링보다 성능이 뛰어납니다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} Apollo는 다양한 벤치마크에서 최첨단 성능을 달성하는 효율적이고 강력한 비디오 LMM 제품군입니다. 특히 Apollo-3B는 대부분의 기존 7B 모델을 능가하며 Apollo-7B는 30B 모델과 경쟁합니다 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
**대규모 멀티모달 모델(LMM)**에서 비디오 이해를 발전시키려는 연구자들에게 중요합니다. **Apollo는 비디오 LMM 디자인의 주요 측면을 체계적으로 탐구**하여 성능을 이끄는 중요한 요소에 대한 통찰력을 제공합니다. **확장 일관성**이라는 개념을 소개하고 **새로운 벤치마크인 ApolloBench**를 제안하며 **Apollo라는 최첨단 비디오 LMM 제품군**을 개발했습니다. 이러한 기여는 효율적이고 효과적인 비디오 LMM 개발에 상당한 영향을 미칩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2412.10360/x1.png)

> 🔼 이 그림은 비디오 이해를 위한 거대 멀티모달 모델(LMM) 설계 공간 탐색에 대한 개요를 보여줍니다. 비디오 샘플링, 모델 아키텍처, 훈련 일정 및 데이터 구성과 같은 비디오 관련 설계 선택 항목을 포괄적으로 탐구하는 아폴로 프레임워크를 보여줍니다. 예를 들어 SigLIP 인코더가 비디오 LMM에 가장 적합한 단일 인코더이지만 시간적 인식을 개선하기 위해 추가 인코더와 결합할 수 있고, 미세 조정 중 약 10%의 텍스트 데이터를 유지하는 것이 비디오 이해 성능에 중요하다는 것을 발견했습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Apollo exploration. Schematic illustrating our comprehensive exploration of video-specific design choices; critically evaluating the existing conceptions in the field, from video sampling and model architecture to training schedules and data compositions. For example, we found that the SigLIP encoder is the best single encoder for video-LMMs but can be combined with additional encoders to improve temporal perception, and that keeping a ∼10%similar-toabsentpercent10\sim 10\%∼ 10 % text data during fine-tuning is critical for video understanding performance. More insights can be found in Sec. 4 & LABEL:sec:training.
> </details>







### In-depth insights


#### Scaling Laws in LMMs
**LMM(대규모 멀티모달 모델)의 스케일링 법칙**은 모델 크기, 데이터셋 크기, 계산 리소스 간의 관계를 설명하며, 일반적으로 더 큰 모델과 더 많은 데이터가 더 나은 성능으로 이어진다고 주장합니다. 하지만 LMM은 사전 훈련된 여러 구성 요소(예: 비전 인코더, 언어 모델)를 통합하므로 개별 구성 요소를 독립적으로 확장하는 것은 현실적으로 어렵습니다. 따라서 **전통적인 스케일링 법칙을 LMM에 직접 적용하는 것은 어려우며**, 각 구성 요소의 상호 작용과 전체 성능에 미치는 영향을 고려해야 합니다. 이러한 복잡성 때문에 **스케일링 법칙을 완화하여 적용하는 방안**이 중요하며, **중간 규모 모델(약 20~40억 개 매개변수)에서 얻은 디자인 결정이 더 큰 모델에도 안정적으로 전달**될 수 있음을 보여주는 **'스케일링 일관성'** 개념이 제시되었습니다. 이는 대규모 모델 학습에 필요한 막대한 계산 비용을 줄이고 연구 속도를 높이는 데 중요한 역할을 합니다. 또한, 데이터셋 크기의 영향을 분석한 결과, 약 50만 개 샘플의 데이터셋 크기면 중간 규모 모델에서 얻은 디자인 통찰력을 더 큰 모델로 안정적으로 전달하는 데 충분하다는 것을 발견했습니다. 이는 **효율적인 모델 개발을 위한 중요한 지침**을 제공하며, LMM 연구에서 **계산 리소스를 효율적으로 활용**하는 데 도움이 될 수 있습니다.

#### Video-LMM Exploration
**비디오-LMM 탐구**는 대규모 멀티모달 모델(LMM)에서 비디오 이해의 핵심 요소를 탐구합니다. 이 연구는 비디오 샘플링, 아키텍처, 데이터 구성, 훈련 일정 등 비디오-LMM의 다양한 측면을 분석합니다. **스케일링 일관성**의 개념을 소개하여 소규모 모델과 데이터셋의 디자인 결정이 대규모 모델로 효과적으로 전달됨을 보여줍니다. 이를 통해 계산 비용이 절감되고 효율적인 실험이 가능해집니다. 또한 **ApolloBench**라는 효율적인 벤치마크 제품군을 소개하며 시간적 추론 및 인식 작업에 대한 자세한 통찰력을 제공합니다. 이 연구는 **Apollo**라는 최첨단 비디오-LMM 제품군을 개발하여 다양한 벤치마크에서 최첨단 결과를 달성했습니다. 특히 Apollo-3B는 대부분의 기존 7B 모델을 능가하고 Apollo-7B는 30B 모델과 경쟁합니다. 이 연구는 효율적이고 효과적인 비디오-LMM 개발을 위한 귀중한 지침과 리소스를 제공합니다.

#### Apollo Architecture
**Apollo 아키텍처**는 비디오 이해를 위해 대규모 멀티모달 모델(LMM)을 활용하는 방법을 중점적으로 다룹니다. InternVideo2와 SigLIP-SO400M을 포함한 이미지 및 비디오 인코더를 결합하여 시공간적 정보를 효과적으로 캡처합니다. 이러한 인코더의 출력은 연결 모듈로 전달되기 전에 채널 차원을 따라 보간 및 연결되어 LLM의 숨겨진 차원과 일치하도록 투영됩니다. 그런 다음 Perceiver Resampler를 사용하여 토큰을 클립당 미리 설정된 수의 토큰으로 리샘플링하여 효율적인 처리를 보장합니다. 이미지의 경우 클립 길이와 일치하도록 이미지를 복제하여 통합된 파이프라인을 사용합니다. 아폴로는 비디오 샘플링, 토큰 리샘플링 및 통합과 같은 다양한 설계 선택의 영향을 분석하여 성능에 미치는 영향을 평가합니다. 이 아키텍처는 긴 비디오를 일련의 독립적인 클립으로 샘플링하여 객체 속도와 같은 미세한 시간적 측면을 추론할 수 있도록 합니다. 비디오가 너무 길면 클립 샘플링 속도를 조정하는 대신 개별 클립을 균일하게 분산시켜 다양한 길이의 비디오에서 일관된 시간적 표현을 유지합니다.

#### ApolloBench
**ApolloBench는 영상 이해 벤치마크의 효율성과 효과를 모두 개선하기 위해 만들어졌습니다.** 기존 벤치마크들은 중복성이 높고, 텍스트 이해 능력이나 단일 프레임으로 풀 수 있는 문제가 많아 영상 인식 능력 평가에 부족했습니다. 또한, 3B 매개변수 모델을 기존 벤치마크에서 평가하는 데 184 A100 GPU 시간이 소요될 정도로 리소스 소모도 컸습니다. **ApolloBench는 객관적인 다지선다형 문제로만 구성되어 ChatGPT와 같은 외부 도구 없이 일관되고 효율적인 평가를 보장합니다.** 영상 인식에 불필요한 문제를 제거하고, 시간적 OCR, 자기 중심적, 공간적, 지각, 추론의 다섯 가지 범주로 분류했습니다. 각 범주에서 모델 간 변별력이 가장 높은 상위 400개 문제를 선택하여 ApolloBench를 구성했습니다. **그 결과 기존 벤치마크 대비 평가 시간을 41배 단축하면서도 높은 상관관계를 유지하고 영상 인식 능력 평가에 더욱 효과적입니다.**

#### Future Directions
**향후 연구 방향**으로, 본 논문에서 제시된 통합 아키텍처를 넘어 이미지와 비디오 인코더를 분리하는 **분할 아키텍처**를 탐구할 수 있습니다. 이를 통해 각 모달리티에 특화된 인코더를 사용하여 성능 향상을 기대할 수 있으며, 특히 SFT 과정에서 이미지 및 비디오 인코더를 각각 훈련하고 평가함으로써 최적의 훈련 전략을 도출할 수 있습니다. 또한, 메모리 기반 LMM 접근 방식(메모리 뱅크, Q-Former의 텍스트 조건부 풀링 등)을 평가하여 **멀티턴 대화**에서의 일반화 가능성을 검증하고, **대화 능력 평가**에 특화된 벤치마크를 개발하여 실제 환경에서의 성능을 정확하게 측정하고 향상시킬 필요가 있습니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2412.10360/x2.png)

> 🔼 이 그림은 비디오 질의응답 벤치마크에서 오픈소스 LMM의 정확도와 벤치마크 간의 상관관계를 분석한 것입니다. 왼쪽 그래프는 비디오, 단일 프레임, 텍스트 입력별 정확도를 보여주고, 비디오 인식이 텍스트 이해보다 얼마나 성능 향상에 기여하는지, 그리고 비디오의 시간적 정보가 정적 이미지 대비 얼마나 추가적인 이점을 제공하는지를 강조합니다. 오른쪽의 상관 행렬은 각 벤치마크에서 모델 성능 간의 상관 계수를 보여줌으로써 벤치마크 간의 중복성을 나타냅니다. 제안된 ApolloBench는 다른 벤치마크와 높은 상관관계를 보이며 효율적인 평가를 제공함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2:  Benchmark Analysis. (Left) Accuracy of the open-source LMMs on various video question-answering benchmarks when provided with different input modalities: full video (green bars), a single frame from the video (red bars), and text-only input without any visual content (blue bars). The light blue shaded areas represent the difference in accuracy between video and text inputs, highlighting the extent to which video perception enhances performance over text comprehension alone. The yellow shaded areas indicate the difference between video and image inputs, quantifying the additional benefit of temporal information from videos compared to static images. (Right) The correlation matrix shows the redundancy among benchmarks by illustrating the correlation coefficients between model performances on different benchmarks. Each cell in the matrix represents how closely the two benchmarks are related in terms of model performance. Our proposed benchmark, ApolloBench, is highly correlated with all tested benchmarks, suggesting that it offers an equally effective evaluation while being more computationally efficient.
> </details>



![](https://arxiv.org/html/2412.10360/x3.png)

> 🔼 이 그림은 LMM의 크기 및 데이터셋 크기에 따른 디자인 결정의 일관성을 보여줍니다. 왼쪽 그래프는 더 큰 LLM(7B)의 경우 더 작은 LLM과의 상관관계가 증가함을 보여주지만, 더 작은 LLM(0.5B)에서는 이러한 경향이 나타나지 않습니다. 오른쪽 그래프는 데이터셋 크기가 약 500K 샘플일 때 더 큰 모델(7B)과의 상관관계가 안정화됨을 보여줍니다. 즉, 특정 크기 이상의 모델과 데이터셋을 사용하면 디자인 결정이 일관되게 나타나므로, 더 작은 모델과 데이터셋으로 효율적인 실험 설계가 가능함을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 3:  Scaling Consistency. We discover Scaling Consistency, where design decisions made with smaller models on smaller datasets carry over to larger models on larger datasets. (Left) R2superscript𝑅2R^{2}italic_R start_POSTSUPERSCRIPT 2 end_POSTSUPERSCRIPT values of 7B and 0.5B versus other LLM sizes show an increasing correlation with larger LLM sizes for the 7B model. The same trend is not seen in the 0.50.50.50.5B model. Interestingly, while the Qwen1.51.51.51.5-4444B model variants have lower/similar performance to their smaller Qwen2−1.521.52-1.52 - 1.5B counterparts, the correlation to larger models is still higher (See App. Fig. LABEL:sup:fig:scaling_consistency). (Right) R2superscript𝑅2R^{2}italic_R start_POSTSUPERSCRIPT 2 end_POSTSUPERSCRIPT of 0.5/1.5/40.51.540.5/1.5/40.5 / 1.5 / 4B models to 7777B vs dataset size. R2superscript𝑅2R^{2}italic_R start_POSTSUPERSCRIPT 2 end_POSTSUPERSCRIPT to larger datasets starts to plateau at around 500500500500K samples.
> </details>



![](https://arxiv.org/html/2412.10360/x4.png)

> 🔼 이 그림은 비디오 샘플링 전략을 비교하고 LMM(Large Multimodal Model) 성능에 미치는 영향을 분석합니다. 왼쪽 그림은 균일 샘플링을 사용하여 훈련 및 테스트한 모델을 보여줍니다. 프레임 수를 늘리면 전반적인 성능이 향상되지만 FPS 샘플링 성능에는 미치지 못합니다. 가운데 그림은 균일 샘플링으로 훈련되었지만 FPS 샘플링으로 테스트된 모델을 나타냅니다. 테스트 시 샘플링된 프레임 수로는 성능 차이를 설명할 수 없습니다. 오른쪽 그림에서는 초당 프레임 수(FPS)와 초당 토큰 수(TPS)가 전반적인 성능에 미치는 영향을 분석합니다. 점선 빨간색 선은 프레임당 토큰 수를 나타냅니다. 자세한 분석은 부록 그림 LABEL:sup:fig:full_sampling을 참조하십시오.
> <details>
> <summary>read the caption</summary>
> Figure 4: Video sampling. We compare different sampling strategies and their effect on performance. (Left) Models were trained and tested using uniform sampling. Increasing the number of frames improves overall performance but does not reach fps sampling performance. (Middle) Models trained with uniform sampling but tested with fps sampling. Differences in performance are not explained by the number of frames sampled at test time. (Right) Analysis of the effect of frames per second (fps) and tokens per second (tps) on overall performance. The dotted red lines (- -) indicate the tokens per frame. For a per-metric breakdown, please see App. Fig. LABEL:sup:fig:full_sampling.
> </details>



![](https://arxiv.org/html/2412.10360/x5.png)

> 🔼 이 그림은 다양한 비전 인코더를 단독 또는 조합하여 사용했을 때의 성능을 비교합니다. 왼쪽 그래프는 단일 인코더를 사용한 결과이며, SigLIP-SO400M이 가장 좋은 성능을 보입니다. 또한 이미지 인코더는 시간적 인식 능력이 비디오 인코더보다 떨어지는 것을 알 수 있습니다. 오른쪽 그래프는 두 개의 인코더를 조합하여 사용한 결과이며, 언어 감독 방식으로 학습된 인코더가 자기 지도 학습 방식으로 학습된 인코더보다 성능이 우수합니다. 특히, InternVideo2와 SigLIP-SO400M을 결합했을 때 가장 좋은 성능을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Vision encoders. In our study, we tested InternVideo2 (internvideo2), LanguageBind-Image/Video (languagebind),V-JEPA (vjepa), Video-MAE (videomae), SigLIP-SO400400400400M (siglip), and DINOv2 (dinov2), and their combinations. (Left) SigLIP-SO-400400400400M emerges as the best overall among single encoders. We also find that image encoders underperform in temporal perception compared to video encoders. (Right) Performance of dual-encoder configurations. Language-supervised encoders outperformed their self-supervised counterparts. Combining InternVideo2 and SigLIP-SO-400400400400M leads to the best overall performance.
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