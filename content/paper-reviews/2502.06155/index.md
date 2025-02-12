---
title: "Efficient-vDiT: Efficient Video Diffusion Transformers With Attention Tile"
summary: "EFFICIENT-VDIT: 3D 어텐션 타일을 이용한 효율적인 비디오 확산 트랜스포머"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Video Understanding", "🏢 Tsinghua University",]
showSummary: true
date: 2025-02-10
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.06155 {{< /keyword >}}
{{< keyword icon="writer" >}} Hangliang Ding et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-11 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.06155" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.06155" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

현존하는 비디오 생성 모델들은 3D 풀 어텐션 기반의 확산 트랜스포머(Diffusion Transformer)를 사용하지만, 어텐션 연산의 복잡성과 많은 샘플링 단계로 인해 추론 속도가 매우 느리다는 문제점이 있습니다.  이 논문은 **비디오 데이터 내의 중복성을 줄이고 샘플링 과정을 단축**하는 두 가지 전략을 통해 이 문제를 해결하고자 합니다.  특히, 비디오 어텐션 맵에서 나타나는 반복적인 타일 패턴을 활용하여 새로운 스파스 어텐션 기법을 제안하며,  기존의 멀티스텝 일관성 증류 기법을 활용하여 샘플링 단계를 줄입니다. 

본 논문에서는 **새로운 스파스 3D 어텐션과 효율적인 샘플링 방법을 결합한 EFFICIENT-VDIT 프레임워크**를 제시합니다. 이 프레임워크는 세 단계의 학습 과정을 통해 저복잡도 어텐션과 소량의 샘플링 단계를 결합합니다.  실험 결과, 제한된 사전 학습 데이터를 사용하여 기존 모델보다 훨씬 빠른 속도로 비디오를 생성하면서도 성능 저하를 최소화함을 보였습니다.  **GPU 분산 처리를 통해 추가적인 속도 향상**을 달성하여 비디오 생성 모델의 실용성을 크게 높였습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 3D 어텐션 맵에서 반복적인 타일 패턴(Attention Tile)을 발견하고, 이를 이용해 선형 복잡도의 스파스 3D 어텐션을 제안 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 다단계 일관성 증류(MCD)를 통해 샘플링 과정을 단축시켜 비디오 생성 속도를 향상 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 0.1%의 사전 학습 데이터로도 기존 모델보다 7.4~7.8배 빠른 비디오 생성 속도를 달성하며, 4개의 GPU를 사용한 분산 추론을 통해 추가적인 속도 향상 달성 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **비디오 생성 분야의 효율성 문제**를 해결하기 위한 혁신적인 방법을 제시하여, 관련 연구자들에게 중요한 의미를 지닙니다. **3D 어텐션의 복잡성과 많은 샘플링 단계로 인한 비효율적인 추론 문제**를 효과적으로 해결하는 EFFICIENT-VDIT 프레임워크는 비디오 생성 모델의 속도와 성능을 크게 향상시킬 수 있는 잠재력을 보여줍니다.  또한, **새로운 스파스 3D 어텐션 기법과 효율적인 샘플링 방법**은 비디오 생성 분야의 지속적인 발전에 기여할 뿐만 아니라, **분산 추론에 대한 적용 가능성**까지 제시하여 향후 연구 방향에 대한 새로운 시각을 제공합니다. 이는 **비디오 생성 모델의 실용성과 효율성을 높이는 데 크게 기여**할 것으로 예상됩니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.06155/x1.png)

> 🔼 이 그림은 논문의 3D 확산 트랜스포머(DiT)에서 관찰되는 주목 패턴인 어텐션 타일(Attention Tile)을 보여줍니다. (a)는 어텐션 맵이 작고 반복적인 블록들로 나뉠 수 있음을 보여줍니다. (b)는 이러한 블록들을 대각선 블록과 대각선이 아닌 블록의 두 가지 유형으로 분류할 수 있으며, 대각선 블록의 어텐션 가중치가 대각선이 아닌 블록보다 현저히 크다는 것을 보여줍니다. (c)는 이러한 블록들이 지역성(locality)을 나타내며, 첫 번째 프레임과 나중 프레임 간의 어텐션 점수 차이가 점진적으로 증가함을 보여줍니다. (d)는 블록 구조가 서로 다른 데이터 포인트에서 안정적이지만 레이어 간에는 다름을 보여줍니다. 또한, 임의로 선택된 두 개의 프롬프트(풍경 및 인물 사진)에 대해 어텐션 맵에서 전체의 90%, 95%, 99%를 차지하는 중요한 위치들을 기록하고, 레이어 간 중요한 위치들의 안정적인 중복 비율을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: We observe the Attention Tile pattern in 3D DiTs. (a) the attention map can be broken down into smaller repetitive blocks. (b) These blocks can be classified into two types, where attention weights on the diagonal blocks are noticeably larger than on off-diagonal ones. (c) These blocks exhibit locality, where the attention score differences between the first frame and later frames gradually increases. (d) The block structure is stable across different data points, but varies across layers. We randomly select 2 prompts (one landscape and one portrait) and record the important positions in the attention map that accounted for 90% (95%, 99%) of the total. We printed the proportion of stable overlap of important positions across layers.
> </details>





{{< table-caption >}}
| Frames | Mask | Sparsity (%) | Time(ms) | Speedup |
|---|---|---|---|---|
| 29 | full | 0.00 | 58.36 | 1.00× |
| 29 | 4:4 | 17.60 | 46.52 | 1.25× |
| 29 | 3:5 | 29.88 | 40.08 | 1.46× |
| 29 | 2:6 | 45.47 | 31.35 | 1.86× |
| 29 | 1:7 | 64.38 | 20.65 | 2.83× |
| 93 | full | 0.00 | 523.61 | 1.00× |
| 93 | 12:12 | 21.51 | 397.72 | 1.32× |
| 93 | 8:16 | 40.30 | 303.90 | 1.72× |
| 93 | 6:18 | 51.88 | 244.13 | 2.14× |
| 93 | 4:20 | 64.98 | 179.74 | 2.91× |
| 93 | 3:21 | 72.05 | 142.77 | 3.67× |{{< /table-caption >}}

> 🔼 이 표는 서로 다른 마스크를 사용했을 때의 속도 향상을 보여줍니다.  'Frames' 열은 생성된 비디오의 프레임 수를 나타내고, 'Mask' 열은 사용된 스파스 어텐션 마스크의 유형을 나타냅니다.  'Sparsity (%)' 열은 마스크의 스파스 정도를 백분율로 나타내고, 'Time(ms)' 열은 비디오 생성에 걸린 시간을 밀리초 단위로 나타냅니다.  마지막으로 'Speedup' 열은 전체 마스크를 사용했을 때에 비해 속도 향상 배수를 보여줍니다. 이 표는 스파스 어텐션 마스크를 적용함으로써 비디오 생성 속도를 얼마나 향상시킬 수 있는지 보여주는 실험 결과를 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Speedup with different masks.
> </details>





### In-depth insights


#### Attention Tile
논문에서 제시된 "어텐션 타일(Attention Tile)" 개념은 비디오 데이터 내 3D 어텐션 맵의 반복적인 패턴을 나타냅니다. **이러한 타일 형태의 반복 패턴은 비디오 프레임 간의 중복성을 보여주는 강력한 증거**이며, 이를 통해 비디오 생성 모델의 효율성을 높일 수 있는 잠재력을 시사합니다.  연구진은 어텐션 타일 현상을 분석하여 기존의 3D 풀 어텐션 방식 대신 **선형 시간 복잡도를 갖는 새로운 스파스 3D 어텐션 메커니즘**을 제안합니다.  이는 각 프레임이 모든 프레임에 대해 어텐션을 계산하는 대신, 일부 프레임에만 어텐션을 집중함으로써 연산량을 크게 줄이는 것을 의미합니다.  **어텐션 타일은 특정 입력 데이터에 독립적**이므로, 추론 시 고정된 스파스 어텐션 마스크를 재사용할 수 있다는 점이 핵심입니다.  **이러한 접근 방식은 비디오 생성 속도를 획기적으로 향상시키는 동시에 성능 저하를 최소화**하는 데 기여하며,  **데이터 효율적인 학습**을 가능하게 합니다.  결론적으로, 어텐션 타일의 발견과 이를 활용한 스파스 어텐션 메커니즘은 비디오 생성 모델의 효율성을 극대화하는 중요한 전략임을 보여줍니다.

#### Sparsity in DiTs
본 논문에서 제시된 효율적인 비디오 확산 트랜스포머(DiTs)는 **주목할 만한 3D 어텐션 희소화 전략**을 통해 비디오 생성 속도를 크게 향상시킵니다.  기존 3D 풀 어텐션 방식의 계산 복잡도를 줄이기 위해 **어텐션 타일(Attention Tile)**이라는 패턴을 분석하여 **선형 시간 복잡도**를 갖는 새로운 희소 3D 어텐션을 제안합니다.  이는 비디오 데이터 내의 중복성을 제거하여 효율성을 높이는 핵심 전략입니다. 이러한 희소 어텐션과 멀티스텝 일관성 증류(MCD)를 결합하여 추론 속도를 개선하면서 비디오 품질을 유지하는 효과적인 모델을 구축합니다.  **데이터 효율적인 사전 훈련** 과정을 통해 제한된 데이터로도 우수한 성능을 달성하고, 분산 추론을 통해 추가적인 속도 향상을 이끌어냅니다.  **어텐션 희소화**는 DiTs의 계산 비용을 줄이는 데 매우 효과적이며, 향후 연구에서도 다양한 희소 어텐션 기법과의 조합을 통해 더욱 발전될 가능성을 보여줍니다.

#### MCD Distillation
본 논문에서 제시된 다단계 일관성 증류(MCD) 기법은 비디오 생성 모델의 샘플링 과정을 단축하여 효율성을 높이는 핵심 전략입니다. **기존의 확산 모델은 수많은 샘플링 단계를 거쳐 고품질의 비디오를 생성하지만, 이는 추론 속도를 크게 저하시키는 주요 원인**입니다. MCD는 이러한 문제를 해결하기 위해 전체 샘플링 경로를 여러 세그먼트로 나누고, 각 세그먼트 내에서 일관성 있는 증류를 수행합니다. 이를 통해 **소수의 샘플링 단계만으로도 고품질의 비디오 생성**을 가능하게 합니다.  **단계 수를 줄임으로써 얻는 속도 향상은 단순히 계산량 감소에 그치지 않고, 실제 추론 시간 단축**으로 이어집니다.  이는 모델의 실질적인 효율성 향상에 크게 기여하며, 특히 고해상도 장시간 비디오 생성과 같이 계산 비용이 높은 작업에서 그 효과가 더욱 두드러집니다.  **MCD는 단순히 속도만 개선하는 것이 아니라, 모델의 안정성과 훈련 효율성에도 긍정적인 영향**을 미치는 것으로 나타났습니다.  따라서 MCD는 고품질 비디오 생성과 효율적인 추론 사이에서 최적의 균형을 이루도록 하는 중요한 기술적 혁신으로 평가할 수 있습니다.

#### EFFICIENT-VDIT
**EFFICIENT-VDIT**는 비디오 생성을 위한 효율적인 확산 변환기 모델을 제시하는 연구의 핵심 내용입니다.  이 모델은 **3D 풀 어텐션 메커니즘의 비효율성**을 해결하기 위해 **어텐션 타일(Attention Tile)**이라는 새로운 패턴을 발견하고, 이를 기반으로 **스파스 어텐션(Sparse Attention)** 기법을 적용하여 연산 복잡도를 줄였습니다.  또한, **멀티-스텝 일관성 증류(Multi-step Consistency Distillation)**을 사용하여 샘플링 과정을 단축시킴으로써 추론 속도를 더욱 향상시켰습니다.  **세 단계의 학습 파이프라인**을 통해 스파스 어텐션과 멀티-스텝 일관성 증류를 결합하여 효율성과 성능을 동시에 확보하였으며, **제한된 데이터로도 효과적인 학습**이 가능함을 보여주었습니다.  **분산 추론 환경**에서도 성능 향상을 확인하였고, 기존 모델 대비 **상당한 속도 향상**을 달성하면서도 **비디오 품질 저하를 최소화**했습니다.  결과적으로 EFFICIENT-VDIT는 고품질 비디오 생성을 위한 효율적인 모델을 제시하여 비디오 생성 분야에 크게 기여할 것으로 예상됩니다.

#### Video Quality
논문에서 비디오 품질에 대한 분석은 **정량적 지표와 정성적 평가** 두 가지 측면에서 이루어졌습니다. 정량적으로는 VBench와 CD-FVD라는 두 가지 척도를 사용하여 생성된 비디오의 품질을 객관적으로 평가했습니다.  **VBench는 인간의 지각과 밀접하게 연관된 척도**이며, CD-FVD는 실제 비디오와 생성 비디오의 분포 간 거리를 측정하여 **시간적 사실성을 고려한 종합적 평가**를 제공합니다. 정성적 평가는 시각적 결과를 직접 비교 분석함으로써 **주관적인 품질 인식**을 확인했습니다.  **다양한 실험 결과**를 통해 제시된 방법이 비디오 품질 저하를 최소화하면서 추론 속도를 상당히 향상시켰음을 보여줍니다. 특히, **레이어별 스파스 어텐션 검색** 기법을 통해 비디오 품질을 유지하면서도 속도 향상 효과를 극대화할 수 있음을 확인하였습니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.06155/x2.png)

> 🔼 그림 2는 Efficient-VDIT의 세 단계 과정을 보여줍니다.  먼저, 기존의 3D 전 주의(Full Attention) 비디오 확산 트랜스포머(DiT) 모델을 입력받습니다. 이 모델은 높은 충실도를 가지지만 추론 속도가 느립니다. 1단계에서는 Heek et al.(2024)의 다단계 일관성 증류(Multi-step Consistency Distillation) 프레임워크를 비디오 영역에 맞춰 수정하여 DiT 모델을 안정적인 훈련이 가능한 CM 모델로 변환합니다. 2단계에서는 각 레이어에 대해 최적의 희소 주의 패턴을 찾는 알고리즘을 실행합니다. 마지막 3단계에서는 지식 증류(Knowledge Distillation)를 통해 희소 DiT의 충실도를 최적화합니다. 최종적으로 Efficient-VDIT는 선형 복잡도의 주의 메커니즘을 가지면서 높은 충실도와 빠른 추론 속도를 가진 DiT 모델을 출력합니다.
> <details>
> <summary>read the caption</summary>
> Figure 2:  Efficient-vDiT takes in a pre-trained 3D Full Attention video diffusion transformer(DiT), with slow inference speed and high fidelity. It then operates on three stages to greatly accelerate the inference while maintaining the fidelity. In Stage 1, we modify the multi-step consistency distillation framework from (Heek et al., 2024) to the video domain, which turned a DiT model to a CM model with stable training. In Stage 2, Efficient-vDiT performs a searching algorithm to find the best sparse attention pattern for each layer. In stage 3, Efficient-vDiT performs a knowledge distillation procedure to optimize the fidelity of the sparse DiT. At the end, Efficient-vDiT outputs a DiT with linear attention, high fidelity and fastest inference speed.
> </details>



![](https://arxiv.org/html/2502.06155/x3.png)

> 🔼 그림 3은 2:6 크기의 예시적인 어텐션 마스크를 보여줍니다. 이 마스크는 주대각선의 어텐션과 2개의 글로벌 참조잠재 프레임에 대한 어텐션을 유지합니다. 흰색 타일 블록은 계산되지 않습니다.  더 자세히 설명하자면, 이 그림은 논문에서 제안하는 희소 어텐션 메커니즘을 시각적으로 보여줍니다. 비디오 데이터의 3차원 어텐션 맵에서 반복적인 패턴(Attention Tile)을 발견하고, 이를 활용하여 계산량을 줄이는 희소 어텐션 마스크를 설계했습니다. 그림에서 볼 수 있듯이, 마스크는 주대각선 요소와 일부 특정 프레임들에 대한 어텐션만을 유지하고, 나머지 요소들은 0으로 설정되어 계산을 생략합니다. 이를 통해 계산 복잡도를 낮추면서도 비디오 생성 성능을 유지할 수 있습니다.  2:6은 각 프레임이 2개의 다른 프레임과만 어텐션을 계산한다는 의미입니다. 262:62 등은 다른 매개변수로 생성한 마스크의 예시입니다.  2개의 글로벌 참조 프레임을 사용하여  비디오 시퀀스 내의 장기적인 의존성을 유지하는 방법을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: Exemplar attention mask (2:6:262:62 : 6). It maintains the attention in the main diagonals and against 2 global reference latent frames. Tile blocks in white are not computed.
> </details>



![](https://arxiv.org/html/2502.06155/x4.png)

> 🔼 그림 4는 Open-Sora-Plan v1.2 모델(29프레임)에 대한 탐색 결과를 보여줍니다.  3D 비디오 DiT에서 각 레이어마다 스파스(sparse) 정도가 다르다는 것을 확인하기 위해 실험한 결과입니다.  즉, 모든 레이어가 동일한 수준의 스파스성을 갖는 것이 아니라, 레이어에 따라 스파스 패턴이 다르게 나타남을 보여줍니다. 이는 효율적인 비디오 생성을 위해 레이어별로 최적의 스파스성을 찾는 것이 중요하다는 것을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: Search results for Open-Sora-Plan v1.2 model (29 frames). We verify that different layers have different sparsity in 3D video DiTs.
> </details>



![](https://arxiv.org/html/2502.06155/extracted/6191047/figures/prompt_sample/ablation.jpg)

> 🔼 그림 5는 본 논문에서 제안하는 세 가지 모델(기본 모델, MLCD 모델, 지식 증류 후 모델)의 비디오 생성 품질을 비교한 것입니다. 각 모델에서 생성된 비디오의 균등하게 분포된 프레임들을 보여주고 있으며, 효율적인 VDIT 모델은 간단히 'E-vdit'로 표기했습니다. 보다 많은 생성 결과는 부록 F에서 확인할 수 있습니다. 그림은 다양한 시나리오에서의 비디오 생성 품질을 보여주어, 제안된 모델의 효과를 시각적으로 확인하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Qualitative samples of our models. We compare the generation quality between the base model, MLCD model, and after knowledge distillation. Frames shown are equally spaced samples from the generated video. Efficient-vDiT is shortened as ‘E-vdit’ for simplicity. More samples can be found in Appendix F.
> </details>



![](https://arxiv.org/html/2502.06155/extracted/6191047/figures/prompt_sample/cogvideo_batch.jpg)

> 🔼 그림 6은 증류 순서의 ablation study 결과를 보여주는 정성적 샘플들입니다. VBench 프롬프트에서 샘플들이 추출되었습니다. MLCD 모델과 Efficient-VDIT 모델 모두 유사한 화질을 보임을 보여줍니다. 두 개의 연속적인 비디오에서, 상단은 MLCD + CD 모델의 결과를, 하단은 KD + MLCD 모델의 결과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Qualitative samples of ablation of distillation order. sampled from VBench prompts. We show that both MLCD and Efficient-vDiT model can simliar quality on these samples. In two consecutive videos, the top shows results from MLCD + CD model followed by KD + MLCD model.
> </details>



![](https://arxiv.org/html/2502.06155/extracted/6191047/figures/prompt_sample/output_batch_1.jpg)

> 🔼 그림 7은 CogVideoX-5B 모델에 적용된 어텐션 증류의 정성적 결과를 보여줍니다.  CogVideoX-5B 모델은 MM-DiT 아키텍처를 기반으로 하며,  본 논문의 어텐션 증류 기법이 MM-DiT 아키텍처에도 적용 가능함을 보여줍니다. 두 개의 연속적인 비디오에서 위쪽은 기본 모델의 결과를, 아래쪽은 증류 모델의 결과를 보여줍니다.  다양한 비디오 예시를 통해 기본 모델과 증류 모델의 비디오 생성 품질을 시각적으로 비교하여 어텐션 증류의 효과를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Qualitative samples of CogvideoX-5B (Yang et al., 2024b) distillation from its sample prompts. We show that our attention distill is capable of MM-DiT model architecture. In two consecutive videos, the top shows results from the base model, followed by the distillation model.
> </details>



![](https://arxiv.org/html/2502.06155/extracted/6191047/figures/prompt_sample/output_batch_3.jpg)

> 🔼 그림 8은 Open-Sora의 예시(Zheng et al., 2024)를 바탕으로 제작되었으며, 중앙에서 폭발이 일어나고 에너지가 방사형으로 퍼져나가는 역동적인 프롬프트들을 선별하여 시각화했습니다. 이를 통해 초점 영역에서 넓은 환경으로의 극적인 변화와 대규모 움직임을 보여줍니다.  폭발이나 에너지 방출과 같은 역동적인 현상이 점 또는 초점에서 시작하여 주변 환경으로 넓게 퍼져나가는 모습을 보여주는 프롬프트들을 사용하여  대규모 운동 효과를 강조했습니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Based on Open-Sora’s examples (Zheng et al., 2024) , we selected dynamic prompts featuring centralized explosions and radiating energy, demonstrating dramatic transitions from focal points to expansive environmental transformations, emphasizing large-scale motion.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | Final Score ↑ | Aesthetic Quality | Motion Smoothness | Temporal Flickering | Object Class | Subject Consistency | CD-FVD ↓ | Sparsity (%) | Kernel Time(ms) | Kernel Speedup | Speedup |
|---|---|---|---|---|---|---|---|---|---|---|---| 
| Base | 76.12% | 58.34% | 99.43% | 99.28% | 64.72% | 98.45% | 172.64 | 0.00 | 58.36 | 1.00× | 1.00× |
| MLCD | 76.81% | 58.92% | 99.41% | 99.42% | 63.37% | 98.37% | 190.50 | 0.00 | 58.36 | 1.00× | 5.00× |
| Ours<sub>r=0.025</sub> | 76.14% | 57.21% | 99.37% | 99.49% | 60.36% | 98.26% | 186.84 | 23.51 | 43.50 | 1.34× | 5.85× |
| Ours<sub>r=0.050</sub> | 76.01% | 57.57% | 99.15% | 99.56% | 58.70% | 97.58% | 195.55 | 37.78 | 35.58 | 1.64× | 6.60× |
| Ours<sub>r=0.100</sub> | 76.00% | 56.59% | 99.13% | 99.54% | 57.12% | 97.73% | 204.13 | 45.08 | 31.54 | 1.85× | 7.05× |
| Ours<sub>r=0.200</sub> | 75.02% | 55.71% | 99.03% | 99.50% | 55.22% | 97.28% | 223.75 | 51.55 | 27.91 | 2.09× | 7.50× |
| Ours<sub>r=0.400</sub> | 75.30% | 55.79% | 98.93% | 99.46% | 54.98% | 97.71% | 231.68 | 55.07 | 25.96 | 2.25× | 7.80× |{{< /table-caption >}}
> 🔼 표 2는 29프레임, 720p 해상도의 Open-Sora-Plan 모델을 사용하여 VBench와 CD-FVD 지표 및 커널 속도 향상에 대한 평가 결과를 보여줍니다.  'r=0.1'은 알고리즘 1에서 설명된 계층별 검색 전략을 사용하여 임계값 r=0.1로 학습된 체크포인트를 나타냅니다. 분석을 위해 일부 차원만 선택했으며, 나머지 차원은 표 6에 제시되어 있습니다. 또한 임계값 r에 따른 커널 속도 향상 결과도 함께 제시합니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Open-Sora-Plan with 29 frames and 720p resolution results on VBench, CD-FVD metrics and kernel speedup evalutation. ‘r𝑟ritalic_r=0.1’ indicates that this checkpoint is trained using the layerwise search strategy described in Algorithm 1, with a threshold of r𝑟ritalic_r=0.1. We selects some dimensions for analysis, with the remaining dimensions provide in the Table 6. We also shows kernel different speedup with threshold r𝑟ritalic_r.
> </details>

{{< table-caption >}}
| Frames | # GPUs | Time (s) | Speedup |
|---|---|---|---| 
| 29 | 1 | 5.56 | 1.00× |
| 29 | 2 | 2.98 | 1.87× |
| 29 | 4 | 1.52 | 3.68× |
| 93 | 1 | 39.06 | 1.00× |
| 93 | 2 | 20.00 | 1.95× |
| 93 | 4 | 10.02 | 3.91× |{{< /table-caption >}}
> 🔼 표 3은 Open-Sora-Plan 모델에서 시퀀스 병렬 처리를 사용한 Efficient-vDiT의 성능을 보여줍니다.  각 스텝 당 벽시계 시간(wall-clock time)을 측정하여, 프레임 수(29 또는 93)와 GPU 개수(1, 2 또는 4)에 따른 속도 향상을 정량적으로 제시합니다.  이 표는 Efficient-vDiT가 분산 환경에서도 효율적인 처리 속도를 제공함을 보여주는 실험 결과를 요약하여 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Efficient-vDiT  with sequence parallelism on Open-Sora-Plan model. Time as wall-clock-time per step.
> </details>

{{< table-caption >}}
| Model | Final Score ↑ | Aesthetic Quality | Motion Smoothness | Temporal Flickering | Speedup |
|---|---|---|---|---|---| 
| Base | 77.91% | 57.91% | 97.83% | 97.34% | 1.00 × | 
| Ours<sub>r=5</sub> | 77.15% | 51.18% | 96.67% | 97.18% | 1.34 × |{{< /table-caption >}}
> 🔼 표 4는 CogVideoX-5B 모델을 사용하여 49프레임, 480p 해상도의 비디오를 생성한 결과를 VBench 벤치마크를 통해 평가한 것입니다. VBench는 비디오 생성 품질을 다양한 측면에서 종합적으로 평가하는 지표로, 최종 점수(Final Score), 미적 품질(Aesthetic Quality), 동작의 부드러움(Motion Smoothness), 시간적 일관성(Temporal Consistency) 등 여러 항목을 포함합니다. 이 표는 제안된 방법의 성능을 기존 모델과 비교하여 보여주는 데 사용됩니다.  CogVideoX-5B 모델은 MM-DiT 아키텍처를 기반으로 하며, 텍스트 토큰과 비디오 토큰을 결합하는 방식의 어텐션 메커니즘을 사용합니다. 따라서 이 표는 제안된 방법이 다양한 아키텍처에서도 효과적으로 적용될 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 4: CogVideoX-5B with 49 frames and 480p resolution results on VBench.
> </details>

{{< table-caption >}}
| Model | Final Score ↑ | Aesthetic Quality | Motion Smoothness | Temporal Flickering | CD-FVD ↓ |
|---|---|---|---|---|---| 
| MLCD + KD | 76.00% | 56.59% | 99.13% | 99.54% | 204.13 |
| KD + MLCD | 75.50% | 56.38% | 99.12% | 99.40% | 203.52 |{{< /table-caption >}}
> 🔼 이 표는 MLCD(Multi-Step Latent Consistency Distillation)와 계층별 지식 증류 순서에 따른 정량적 평가 결과를 보여줍니다.  MLCD를 먼저 적용한 후 지식 증류를 수행하거나, 그 반대 순서로 수행했을 때의 VBench 점수와 CD-FVD 점수를 비교하여, 두 방법의 성능 차이가 거의 없음을 보여줍니다. 이는 MLCD와 계층별 지식 증류가 서로 독립적인 과정임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Quantitative evaluation on distillation order for MLCD and layerwise knowledge distillation.
> </details>

{{< table-caption >}}
| Model | Multiple Objects | Human Action | Color | Dynamic Degree | Spatial Relationship | Scene | Appearance Style | Temporal Style | Overall Consistency | Background Consistency | Imaging Quality |
|---|---|---|---|---|---|---|---|---|---|---|---| 
| Base | 23.25% | 54.00% | 94.47% | 34.72% | 43.49% | 18.60% | 19.88% | 18.45% | 19.69% | 97.64% | 64.75% |
| MLCD | 19.21% | 56.00% | 94.12% | 41.67% | 40.57% | 22.67% | 20.46% | 18.21% | 19.77% | 97.98% | 65.55% |
| Ours<sub>r=0.025</sub> | 18.83% | 55.00% | 96.25% | 52.78% | 46.02% | 12.35% | 20.31% | 18.17% | 19.11% | 97.70% | 58.90% |
| Ours<sub>r=0.050</sub> | 11.74% | 58.00% | 92.11% | 58.33% | 39.81% | 22.31% | 20.25% | 17.71% | 19.45% | 97.71% | 56.86% |
| Ours<sub>r=0.100</sub> | 18.98% | 56.00% | 93.65% | 63.89% | 43.88% | 15.77% | 20.20% | 17.98% | 19.29% | 97.55% | 54.88% |
| Ours<sub>r=0.200</sub> | 17.99% | 53.00% | 51.82% | 59.72% | 36.14% | 13.88% | 20.29% | 17.97% | 18.97% | 97.62% | 54.07% |
| Ours<sub>r=0.400</sub> | 15.32% | 54.00% | 92.64% | 65.28% | 37.05% | 12.06% | 20.24% | 18.19% | 19.22% | 97.66% | 54.36% |{{< /table-caption >}}
> 🔼 표 6은 본 논문의 주요 결과에 대한 추가적인 VBench 평가 결과를 보여줍니다.  VBench는 비디오 생성 품질을 평가하는 종합적인 지표로, 여러 측면(예: 미적 품질, 동작의 부드러움, 시간적 일관성, 객체 식별, 주제 일관성, 배경 일관성, 영상 품질)을 고려합니다. 이 표는 기본 모델, MLCD 모델, 그리고 EFFICIENT-VDIT 모델의 다양한 변형에 대한 각 측면의 점수를 보여주어, 제안된 방법의 효율성과 품질 저하 여부를 비교 분석하는 데 도움이 됩니다.  각 모델의 변형은 다른 스파스 어텐션 마스크를 사용하여 얻어진 결과를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Supplemental VBench evaluation for main result.
> </details>

{{< table-caption >}}
| Model | Final Score ↑ | Aesthetic Quality | Motion Smoothness | Temporal Flickering | Object Class | Subject Consistency | Imaging Quality | CD-FVD ↓ | Speedup |
|---|---|---|---|---|---|---|---|---|---| 
| Base | 76.12% | 58.34% | 99.43% | 99.28% | 64.72% | 98.45% | 64.75% | 172.64 | 1.00× |
| Base<sub>4:4</sub> | 76.57% | 58.64% | 99.38% | 99.20% | 66.38% | 98.26% | 63.56% | 171.62 | 1.16× |
| Base<sub>3:5</sub> | 75.53% | 55.47% | 99.01% | 98.96% | 62.26% | 97.42% | 59.67% | 197.35 | 1.26× |
| Base<sub>2:6</sub> | 76.33% | 57.14% | 99.06% | 99.02% | 56.17% | 97.58% | 61.10% | 201.61 | 1.45× |
| Base<sub>1:7</sub> | 77.15% | 57.53% | 98.67% | 98.66% | 60.68% | 96.96% | 61.91% | 322.28 | 1.77× |
| MLCD | 76.81% | 58.92% | 99.41% | 99.42% | 63.37% | 98.37% | 65.55% | 190.50 | 5.00× |
| MLCD<sub>4:4</sub> | 75.90% | 57.84% | 99.38% | 99.50% | 63.03% | 98.21% | 58.47% | 175.47 | 5.80× |
| MLCD<sub>3:5</sub> | 75.41% | 57.19% | 99.36% | 99.50% | 57.04% | 98.12% | 58.84% | 190.92 | 6.30× |
| MLCD<sub>2:6</sub> | 75.23% | 57.45% | 99.29% | 99.48% | 54.59% | 98.37% | 57.35% | 213.72 | 7.25× |
| MLCD<sub>1:7</sub> | 75.84% | 56.83% | 98.99% | 99.23% | 52.77% | 97.54% | 56.42% | 294.09 | 8.85× |{{< /table-caption >}}
> 🔼 표 7은 논문의 실험 결과 중 MLCD(Multi-Step Consistency Distillation)의 효과를 보여주는 표입니다.  Base 모델과 MLCD 모델의 VBench 및 CD-FVD 지표를 비교 분석하여 MLCD가 성능 저하 없이 추론 속도를 향상시키는 효과를 확인합니다.  또한 어텐션 마스크와의 호환성을 검증하고,  다양한 스파스 어텐션 마스크를 적용한 MLCD 모델의 성능을 비교 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Ablation experiments on the effect of MLCD.
> </details>

{{< table-caption >}}
| Model | Multiple Objects | Human Action | Color | Dynamic Degree | Spatial Relationship | Scene | Appearance Style | Temporal Style | Overall Consistency | Background Consistency |
|---|---|---|---|---|---|---|---|---|---|---|
| Base | 23.25% | 54.00% | **94.47%** | 34.72% | 43.49% | 18.60% | 19.88% | **18.45%** | 19.69% | 97.64% |
| Base<sub>4:4</sub> | **32.01%** | 55.00% | 90.94% | 43.06% | **45.42%** | 17.30% | 20.21% | 18.41% | 19.48% | 97.17% |
| Base<sub>3:5</sub> | 15.85% | 53.00% | 88.88% | 58.33% | 44.38% | 14.53% | 20.13% | 17.46% | 18.43% | 97.28% |
| Base<sub>2:6</sub> | 21.65% | 56.00% | 93.27% | 56.94% | 49.90% | 18.31% | 19.87% | 18.23% | 18.94% | 97.27% |
| Base<sub>1:7</sub> | 17.76% | 54.00% | 93.02% | 75.00% | 44.75% | 19.99% | 19.95% | 18.25% | 19.41% | 97.30% |
| MLCD | 19.21% | **56.00%** | 94.12% | 41.67% | 40.57% | **22.67%** | **20.46%** | 18.21% | **19.77%** | **97.98%** |
| MLCD<sub>4:4</sub> | 22.79% | 53.00% | 92.69% | 50.00% | 39.80% | 17.51% | 19.89% | 18.32% | 19.06% | 97.30% |
| MLCD<sub>3:5</sub> | 22.10% | 50.00% | 90.82% | 43.06% | 43.48% | 21.44% | 19.97% | 17.68% | 19.75% | 97.47% |
| MLCD<sub>2:6</sub> | 18.60% | 53.00% | 92.52% | 44.44% | 43.36% | 16.21% | 19.89% | 17.84% | 20.12% | 97.70% |
| MLCD<sub>1:7</sub> | 16.92% | 53.00% | 91.92% | 63.89% | 43.27% | 17.22% | 19.94% | 18.56% | 19.85% | 97.45% |{{< /table-caption >}}
> 🔼 표 8은 논문에서 제안하는 계층별 탐색 알고리즘의 효과를 보여주는 실험 결과를 보여줍니다.  MLCD 모델을 기준으로, 모든 계층에 동일한 마스크를 적용하는 방법(예: 4:4, 3:5)과 알고리즘 1에서 제안하는 계층별 마스크를 비교합니다. 계층별 마스크는 각 계층의 특성에 맞춰 최적의 스파스 패턴을 찾는 방식으로,  VBench 점수와 CD-FVD 점수를 통해 성능을 평가합니다. 특히, 계층별 탐색 기법을 사용하지 않은 경우 스파스성이 증가함에 따라 비디오 생성 품질이 저하되는 현상이 나타나지만, 계층별 탐색 기법을 사용한 경우에는 생성 품질을 유지하면서도 속도 향상 효과를 얻을 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Ablation experiments on the effect of our layerwise searching algorithm.
> </details>

{{< table-caption >}}
| Model | Final Score ↑ | Aesthetic Quality | Motion Smoothness | Temporal Flickering | Object Class | Subject Consistency | Imaging Quality | CD-FVD ↓ | Speedup |
|---|---|---|---|---|---|---|---|---|---| 
| MLCD | **76.81%** | **58.92%** | **99.41%** | 99.42% | **63.37%** | **98.37%** | **65.55%** | 190.50 | 5.00 × |
| MLCD<sub>4:4</sub> | 75.90% | 57.84% | 99.38% | 99.50% | 63.03% | 98.21% | 58.47% | 175.47 | 5.80 × |
| MLCD<sub>3:5</sub> | 75.41% | 57.19% | 99.36% | 99.50% | 57.04% | 98.12% | 58.84% | 190.91 | 6.30 × |
| MLCD<sub>2:6</sub> | 75.23% | 57.45% | 99.29% | 99.48% | 54.59% | 98.37% | 57.35% | 213.71 | 7.25 × |
| MLCD<sub>1:7</sub> | 75.84% | 56.83% | 98.99% | 99.23% | 52.77% | 97.54% | 56.42% | 294.09 | **8.85 ×** |
| Ours<sub>r=0.025</sub> | 76.14% | 57.21% | 99.37% | 99.49% | 60.36% | 98.26% | 58.90% | 186.84 | 5.85 × |
| Ours<sub>r=0.050</sub> | 76.01% | 57.57% | 99.15% | **99.56%** | 58.70% | 97.58% | 56.86% | 195.55 | 6.60 × |
| Ours<sub>r=0.100</sub> | 76.00% | 56.59% | 99.13% | 99.54% | 57.12% | 97.73% | 54.88% | 204.13 | 7.05 × |
| Ours<sub>r=0.200</sub> | 75.02% | 55.71% | 99.03% | 99.50% | 55.22% | 97.28% | 54.07% | 223.75 | 7.50 × |
| Ours<sub>r=0.400</sub> | 75.30% | 55.79% | 98.93% | 99.46% | 54.98% | 97.71% | 54.36% | 231.68 | 7.80 × |{{< /table-caption >}}
> 🔼 표 9는 MLCD(다단계 일관성 증류)와 계층별 지식 증류의 증류 순서에 대한 추가 연구 결과를 보여주는 VBench 평가 결과표입니다.  MLCD를 먼저 적용한 후 지식 증류를 적용한 모델과 지식 증류를 먼저 적용한 후 MLCD를 적용한 모델의 결과를 비교하여 두 방법의 순서가 성능에 미치는 영향을 분석합니다.  다양한 화질 지표(예: 최종 점수, 미적 품질, 동작 부드러움 등)를 통해 모델 성능을 정량적으로 비교 분석합니다.
> <details>
> <summary>read the caption</summary>
> Table 9: VBench evaluation result for ablation study on distillation order for MLCD and layerwise knowledge distillation.
> </details>

{{< table-caption >}}
| Model | Multiple Objects | Human Action | Color | Dynamic Degree | Spatial Relationship | Scene | Appearance Style | Temporal Style | Overall Consistency | Background Consistency |
|---|---|---|---|---|---|---|---|---|---|---|
| MLCD | 19.21% | 56.00% | 94.12% | 41.67% | 40.57% | 22.67% | 20.46% | 18.21% | 19.77% | 97.98% |
| MLCD<sub>4:4</sub> | 22.79% | 53.00% | 92.69% | 50.00% | 39.80% | 17.51% | 19.89% | 18.32% | 19.06% | 97.30% |
| MLCD<sub>3:5</sub> | 22.10% | 50.00% | 90.82% | 43.06% | 43.48% | 21.44% | 19.97% | 17.68% | 19.75% | 97.47% |
| MLCD<sub>2:6</sub> | 18.60% | 53.00% | 92.52% | 44.44% | 43.36% | 16.21% | 19.89% | 17.84% | 20.12% | 97.70% |
| MLCD<sub>1:7</sub> | 16.92% | 53.00% | 91.92% | 63.89% | 43.27% | 17.22% | 19.94% | 18.56% | 19.85% | 97.45% |
| Ours<sub>r=0.025</sub> | 18.83% | 55.00% | 96.25% | 52.78% | 46.02% | 12.35% | 20.31% | 18.17% | 19.11% | 97.70% |
| Ours<sub>r=0.050</sub> | 11.74% | 58.00% | 92.11% | 58.33% | 39.81% | 22.31% | 20.25% | 17.71% | 19.45% | 97.71% |
| Ours<sub>r=0.100</sub> | 18.98% | 56.00% | 93.65% | 63.89% | 43.88% | 15.77% | 20.20% | 17.98% | 19.29% | 97.55% |
| Ours<sub>r=0.200</sub> | 17.99% | 53.00% | 51.82% | 59.72% | 36.14% | 13.88% | 20.29% | 17.97% | 18.97% | 97.62% |
| Ours<sub>r=0.400</sub> | 15.32% | 54.00% | 92.64% | 65.28% | 37.05% | 12.06% | 20.24% | 18.19% | 19.22% | 97.66% |{{< /table-caption >}}
> 🔼 표 10은 CogVideoX-5B 모델에서 다양한 마스크를 사용했을 때의 속도 향상을 보여줍니다.  각 마스크는 다른 수준의 스파스성(sparsity)을 가지고 있으며, 이는 어텐션 연산에서 계산되지 않는 요소의 비율을 나타냅니다.  표는 각 마스크에 대한 스파스성, 실행 시간(밀리초 단위), 그리고 기준 모델(full mask) 대비 속도 향상 배수를 보여줍니다. 스파스성이 높아질수록 실행 시간이 짧아지고 속도 향상 배수가 커지는 것을 확인할 수 있습니다. 이는 제안된 방법이 계산 비용을 줄이면서 성능 저하를 최소화한다는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 10: CogvideoX-5B model speedup with different masks.
> </details>

{{< table-caption >}}
| Model | Final Score ↑ | Aesthetic Quality | Dynamic Degree | Motion Smoothness | Temporal Flickering | Object Class | Subject Consistency | Imaging Quality | CD-FVD ↓ |
|---|---|---|---|---|---|---|---|---|---|
| MLCD + KD | 76.00% | 56.59% | 63.88% | 99.13% | 99.54% | 57.12% | 97.73% | 54.88% | 204.13 |
| KD + MLCD | 75.50% | 56.38% | 54.16% | 99.12% | 99.40% | 54.67% | 97.71% | 57.97% | 203.52 |{{< /table-caption >}}
> 🔼 표 11은 CogVideoX-5B 모델을 사용하여 49프레임, 480p 해상도의 비디오를 VBench 벤치마크로 평가한 결과를 보여줍니다.  'r=4.0'은 알고리즘 1에서 설명된 계층별 탐색 전략을 사용하여 임계값 r을 4.0으로 설정하여 학습된 체크포인트를 나타냅니다.  즉,  비디오 생성 품질을 평가하기 위해 다양한 계층에 대해 최적의 스파스 어텐션 마스크를 찾는 과정에서 사용된 임계값이 4.0임을 의미합니다. 이 표는 모델의 성능을 다양한 측면(미적 품질, 동작 부드러움, 일관성 등)에서 정량적으로 평가하여, 제안된 방법의 효율성과 성능을 확인하는 데 사용됩니다.
> <details>
> <summary>read the caption</summary>
> Table 11: CogVideoX-5B with 49 frames and 480p resolution results on VBench. ‘r𝑟ritalic_r=4.0’ indicates that this checkpoint was trained using the layerwise search strategy described in Algorithm 1, with a threshold of r𝑟ritalic_r=4.0.
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