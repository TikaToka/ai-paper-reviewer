---
title: "Are Vision Language Models Texture or Shape Biased and Can We Steer Them?"
summary: "VLMs의 텍스처-형태 편향성을 언어로 조절 가능"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Multimodal Learning", "Vision-Language Models", "🏢 Google DeepMind",]
showSummary: true
date: 2024-03-14
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2403.09193 {{< /keyword >}}
{{< keyword icon="writer" >}} Paul Gavrikov et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-01-28 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2403.09193" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2403.09193" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/are-vision-language-models-texture-or-shape" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

본 연구는 비전 언어 모델(VLMs)의 시각적 편향성, 특히 텍스처와 형태에 대한 편향성을 분석하고 이를 언어를 통해 조절하는 방법을 제시합니다. 기존 연구에서는 주로 순수 비전 모델의 시각적 편향성에 초점을 맞췄지만, 본 연구는 멀티모달 모델인 VLMs의 특성을 고려하여 언어적 요소가 시각적 편향성에 미치는 영향을 분석합니다.  이를 통해 VLMs가 인간의 시각적 편향성과 얼마나 일치하는지, 그리고 멀티모달 융합을 통해 어떻게 시각적 편향성이 형성되는지에 대한 이해를 높이고자 합니다.

연구진은 다양한 VLMs을 대상으로 텍스처-형태 편향성을 측정하고, 언어 프롬프트를 통해 편향성을 조절하는 실험을 진행했습니다. 그 결과, VLMs는 순수 비전 모델보다 형태에 더 치우친 편향성을 가지며, 언어 프롬프트를 통해 편향성을 어느 정도 조절할 수 있음을 확인했습니다. 하지만, 인간의 시각적 편향성과는 여전히 차이가 있음을 보였습니다. 이 연구는 VLMs의 시각적 편향성을 이해하고 제어하는 새로운 방법을 제시하며, 멀티모달 모델의 시각적 편향성 연구에 중요한 기여를 할 것으로 기대됩니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} VLMs는 기존의 순수 비전 모델보다 형태에 더 치우친 편향성을 가진다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 언어 프롬프트를 통해 VLMs의 텍스처-형태 편향성을 조절할 수 있다. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 인간의 시각적 편향성과 VLMs의 편향성 사이에는 여전히 차이가 존재한다. {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **비전 언어 모델(VLMs)**의 **텍스처 및 형태 편향성**을 연구하고 이를 **언어를 통해 조절**할 수 있는지를 조사하여, **다양한 VLMs에서의 편향성을 측정**하고 **언어 프롬프트를 통해 편향성을 조절하는 방법**을 제시합니다. 이는 **인간의 시각적 편향성과의 정렬**을 개선하고 **VLMs의 응용 가능성을 확장**하는 데 기여할 수 있으며, **멀티모달 모델의 편향성 이해 및 제어**에 대한 새로운 방향을 제시하는 중요한 연구입니다.  **특히, 언어 프롬프트를 통한 시각적 편향성 조절 가능성**은 컴퓨터 비전 분야의 새로운 연구 방향을 제시할 수 있습니다.

------
#### Visual Insights



![](https://arxiv.org/html/2403.09193/x1.png)

> 🔼 그림 1은 다양한 VLMs(Vision Language Models)의 질감-형태 편향(texture-shape bias)을 시각적으로 보여줍니다.  단일 모드 모델들과 달리 VLMs는 객체 인식 시 질감보다는 형태를 더 선호하지만, 인간의 수준에는 미치지 못합니다.  흥미롭게도, VLMs의 질감-형태 편향은 시각 정보뿐만 아니라 언어 프롬프트만으로도 조절 가능하며, 이는 InternVL-Chat 1.1의 예시를 통해 강조됩니다.  이 그림은 VLMs가 시각적 편향을 어떻게 처리하고 언어를 통해 조절할 수 있는지 보여주는 중요한 시각적 자료입니다.  각 VLM에 대한 질감 및 형태 편향의 정도가 막대 그래프로 표현되어 있고, InternVL-Chat 1.1의 경우 언어 조절을 통해 형태 편향을 어떻게 증가시킬 수 있는지 보여주는 추가 그래프가 포함되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Unlike many unimodal models, vision language models (VLMs) prefer shape over texture for object recognition, but not to the same extent as humans. Further, we find that the (visual) texture/shape bias [1] can be steered through language alone, albeit not to the extent as through vision. Here we visualize the texture/shape bias of some exemplary VLMs, and highlight the steerability of InternVL-Chat 1.1 [2].
> </details>





{{< table-caption >}}
| Model                     | Description                                                                                                                                                                                  |
|------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `Qwen-VL-Chat` [63]         | Adds vision capabilities to `Qwen-7B` [79]. We set a repetition penalty of 1.2 for this model.                                                                                              |
| `Qwen-VL Plus/Max` [26]     | Alibaba’s proprietary larger variants of `Qwen-VL-Chat`. Access only via API.                                                                                                                   |
| `CogAgent` [64]             | A special model for interaction with graphical user interfaces (GUIs) at high-resolution.                                                                                                       |
| `CogVLM` [65]               | Adds "trainable visual expert module" in LLM layers to combine vision and language.                                                                                                              |
| `Emu2` [66]                 | The 37B model claims "strong multimodal in-context learning abilities".                                                                                                                         |
| `InstructBLIP` [23]         | Connects frozen vision encoders and LLMs through a trainable Q-Former. Uses `Vicuna` or `FLAN-T5` as LLMs.                                                                                      |
| `LLaVA v1.5` [61]           | Improvements of `LLaVA` with modifications on the image encoder, the projector, and task-specific data. Uses `Vicuna-7/13B` as LLM.                                                                  |
| `LLaVA-NeXT` [62]           | Successor of `LLaVA v1.5` supporting higher resolutions through patching, and using better SFT training data for training, claiming “improved reasoning, OCR, and world knowledge” [62]. The 34B version switches from `Vicuna-7/13B` to `Nous Hermes 2 Yi 34B`. |
| `MoE-LLaVA v1.5` [67]       | Variants of `LLaVA v1.5` employing 4 sparsely activated Mixture-of-Experts (MoE), and smaller LLMs (`Qwen`, `Phi-2`, `StableLM`).                                                                     |
| `LLaVA-RLHF` [69]           | Variants of `LLaVA v1.5` aligned with Factually Augmented RLHF (Fact-RLHF) [69].                                                                                                                  |
| `UForm-Gen Chat` [68]       | A small (1.5B) model for VQA and image captioning finetuned for multimodal chat.                                                                                                                 |
| `Gemini 1.0 Pro Vision` [25] | Google’s proprietary multi-modal model based on the Gemini Pro LLM. Access only via API.                                                                                                           |
| `InternVL Chat 1.1/1.2+` [2] | An open-source effort to provide an alternative to `ViT-22B` [80]. V1.1 is based on a 6B ViT and `Vicuna-13B`, V1.2+ uses `Nous Hermes 2 Yi 34B` as LLM including additional SFT on 10x more data. |
| `GPT-4V (Preview)` [12]      | OpenAI’s proprietary multi-modal model based on the GPT-4 LLM. Access only via API. Often considered to be the most powerful model.                                                                    |{{< /table-caption >}}

> 🔼 표 2는 다양한 VLMs에 대한 VQA 분류 또는 이미지 설명 작업에서 큐 충돌 데이터 세트에 대한 형태 편향 및 해당 정확도를 보여줍니다. 이미지 설명 작업의 경우, 비쿠냐 토크나이저가 생성한 토큰의 평균 수와 별도의 LLM에 의해 판단된 단일 클래스만 포함하거나 일반적인(클래스를 언급하지 않음) 응답의 비율을 추가로 제공합니다.  '-'는 VQA에 대한 지시 사항을 따르지 않아 평가할 수 없는 모델을 나타냅니다.
> <details>
> <summary>read the caption</summary>
> Table 2: The shape bias and respective accuracy on the cue-conflict dataset for various VLMs in VQA classification or image description tasks. For the image description task, we additionally provide the average number of tokens generated by Vicuna’s tokenizer and the ratio of responses that only contain a single class or are generic (do not mention any class) as judged by a separate LLM. “-” indicates models that did not follow instructions on VQA and could, thus, not be evaluated.
> </details>





### In-depth insights


#### VLM Bias Study
본 논문은 **비전 언어 모델(VLM)**의 **텍스처 및 형태 편향성(texture vs. shape bias)**을 심도 있게 연구합니다.  특히, 인간의 시각적 편향성과 VLM의 편향성 간의 차이점과, 언어 프롬프트를 통해 VLM의 편향성을 조절할 수 있는지 여부에 초점을 맞춥니다. **흥미롭게도, VLM은 순수 비전 모델보다 형태에 더 치우친 경향**을 보이며, 이는 **텍스트가 시각적 편향성을 조절하는 역할**을 함을 시사합니다.  **실험 결과는 언어 프롬프트를 통해 형태 편향성을 조절할 수 있음**을 보여주지만, 인간의 강력한 형태 편향성에는 미치지 못함을 확인합니다.  **다양한 VLM과 프롬프트 엔지니어링 기법을 활용**하여 이러한 편향성의 원인과 조절 가능성을 탐구하는 포괄적인 연구입니다.  **결과는 멀티모달 모델에서 시각적 편향성이 단순히 비전 인코더에서 상속되는 것이 아니라, 언어와의 상호작용에 의해 조절됨**을 강조합니다.

#### Prompt Steering
본 논문에서 다룬 프롬프트 스티어링은 **비전 언어 모델(VLM)의 시각적 편향(texture/shape bias)을 언어적 개입을 통해 조절하는 기법**입니다.  단순히 시각 정보만으로 편향을 조정하는 것과 달리, **텍스트 프롬프트를 통해 모델의 시각적 해석 방식을 바꿀 수 있다는 점**이 핵심입니다.  실험 결과는 프롬프트에 따라 shape bias가 최대 72%까지 증가하고, texture bias는 49%까지 감소함을 보여줍니다.  **인간의 시각적 편향(shape bias 96%)을 완전히 재현하지는 못하지만**,  프롬프트 엔지니어링을 통해 VLM의 시각적 판단에 상당한 영향을 줄 수 있음을 시사합니다.  **자동화된 프롬프트 생성 기법**을 통해 더욱 효과적인 스티어링 가능성을 확인한 것도 중요한 결과입니다.  이러한 연구는 **향후 VLM 개발 및 응용에 있어서 시각적 편향을 제어하고 인간의 시각 인지와 더욱 일치시키는 데 중요한 전략적 의미**를 갖습니다.

#### Vision's Role
이 논문에서 '비전의 역할'에 대한 심층적인 고찰은 시각 언어 모델(VLMs)의 시각적 편향 형성에 있어서 비전 인코더의 중요성을 강조합니다.  **VLMs는 순수 시각 모델과 달리 언어를 통해 시각적 정보에 접근**하며, 이러한 다중 모달 특성으로 인해 시각적 편향이 단순히 비전 인코더에서 상속되는 것이 아니라 언어와의 상호작용을 통해 조절된다는 점이 핵심입니다.  **텍스처 대비 형태 편향**과 같은 시각적 편향은 비전 인코더의 영향을 받지만, 언어 프롬프트를 통해 조정 가능하다는 실험적 증거가 제시됩니다.  **프롬프트 엔지니어링을 통해 형태 편향을 49%에서 72%까지 조절**할 수 있다는 결과는 언어가 시각적 편향을 조정하는 데 중요한 역할을 한다는 것을 시사합니다.  **비전 인코더의 역할을 분리 분석**하는 실험을 통해 시각적 편향이 단순히 상속되는 것이 아니며, 다중 모달 융합을 통해 모델의 시각적 편향이 변화될 수 있음을 확인합니다.  **인간의 시각적 편향과의 비교**를 통해 VLMs의 시각적 편향이 인간의 편향과 완전히 일치하지 않음을 보여주지만, 언어 프롬프트를 통한 조정 가능성을 제시하며, **향후 인간 시각과의 조화를 위한 연구 방향**을 제시합니다. 따라서, 비전은 단순히 정보 입력의 수단을 넘어, 언어와 상호작용하여 모델의 시각적 이해와 판단에 영향을 미치는 핵심 요소임을 알 수 있습니다.

#### RLHF's Impact
본 논문에서는 RLHF(Reinforcement Learning from Human Feedback)가 비전 언어 모델(VLMs)의 텍스처-쉐이프 편향에 미치는 영향을 심층적으로 분석합니다.  **RLHF는 모델의 성능 향상에 기여하지만, 텍스처-쉐이프 편향 자체를 인간 수준으로 줄이지는 못한다는 점을 강조**합니다.  일부 모델에서 RLHF 적용 후 편향이 변화하거나, 변화하지 않거나, 심지어 오히려 감소하는 등 일관된 경향이 없다는 점을 보여주며, **RLHF가 꼭 시각적 선호도를 인간 수준으로 정렬하는 보장은 없음**을 시사합니다.  따라서 RLHF는 VLMs의 성능 개선에는 효과적이지만, 시각적 편향 조정에 대한 추가적인 연구와 전략이 필요함을 강조합니다.  **결론적으로, RLHF는 VLMs의 성능 향상에 도움이 되지만, 인간 수준의 시각적 편향 정렬에는 충분하지 않다는 점이 중요한 시사점**입니다.  추가 연구를 통해 RLHF의 한계와 개선 방향을 모색하여, 더욱 인간 친화적인 VLMs 개발에 기여해야 합니다.

#### Future Work
본 논문은 비전 언어 모델(VLMs)의 질감-형태 편향성을 조사하고, 이를 언어를 통해 제어할 수 있는지 여부를 탐구합니다.  **미래 연구는 몇 가지 중요한 방향**으로 나아갈 수 있습니다. 첫째, **더욱 다양한 VLMs과 다양한 비전 편향성**을 조사하여, 본 논문의 발견이 얼마나 일반적인지 확인해야 합니다. 둘째, **제어 가능한 매개변수들을 더욱 심층적으로 분석**하여 언어적 조작을 통한 편향성 제어의 메커니즘을 명확히 밝혀야 합니다.  셋째, **본 연구에서 사용된 프롬프트 엔지니어링 기법을 개선**하여, 인간 수준의 형태 편향성에 도달할 수 있는지 탐색해야 합니다.  마지막으로, **다른 종류의 비전 편향성에도 본 연구의 프레임워크를 적용**하여, 보다 포괄적인 비전 언어 모델의 편향성 이해 및 제어 방안을 모색해야 합니다. 이러한 추가 연구는 VLMs의 신뢰성 및 공정성 향상에 기여할 것입니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2403.09193/x2.png)

> 🔼 그림 2는 다양한 VLMs(Vision Language Models)의 질감-형태 편향(texture-shape bias)을 보여줍니다. VQA(Visual Question Answering) 작업과 이미지 설명 작업에서 VLMs의 형태 편향을 측정하여 비교 분석했습니다. 대부분의 VLMs는 약간 형태 중심적이지만, 이미지를 설명하라는 요청을 받았을 때 VQA와 비교하여 차이를 보이는 모델들도 있습니다.  비교를 위해 초기 질감-형태 편향 연구에서 사용된 ResNet-50 [59], 제로샷 분류(CLIP ViT-L/14 [11]), 그리고 10명의 사람의 평균 결과도 함께 제시했습니다. 이 그림은 VLMs가 형태 정보에 더 의존하는 경향을 보이지만, 사람의 형태 편향(96%)에는 미치지 못하며, 작업 유형에 따라 형태 편향이 달라질 수 있음을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Most VLMs are slightly shape-biased but some models show differences when asked to describe an image compared to VQA. We measure the shape bias on the cue-conflict dataset [1]. For reference, we also provide measurements on ResNet-50 [59] from the initial shape bias study [1], zero-shot classification (CLIP ViT-L/14 [11]), and a human average (over 10 subjects [1]).
> </details>



![](https://arxiv.org/html/2403.09193/x3.png)

> 🔼 그림 (a)는 다양한 모델의 예측 신뢰도에 따른 텍스처 및 모양 토큰의 분포를 보여줍니다. 모든 샘플에 대한 텍스처와 모양 토큰의 신뢰도 분포, 정답 예측(즉, 예측 레이블이 모양 또는 질감과 일치)에서의 신뢰도 분포, 신뢰도 임계값을 변경했을 때 모양 편향의 변화를 보여줍니다. 이는 모델이 어떻게 결정을 내리는지, 그리고 신뢰도가 결정에 미치는 영향을 시각적으로 보여줍니다. 특히, 가장 높은 신뢰도의 답변은 모양 단서에만 해당된다는 것을 보여주는 것이 중요합니다.
> <details>
> <summary>read the caption</summary>
> (a)
> </details>



![](https://arxiv.org/html/2403.09193/x4.png)

> 🔼 그림 (b)는 정확한 예측(즉, 예측 레이블이 모양 또는 질감과 일치)에 대한 신뢰도 분포를 보여줍니다.  모델이 응답에 사용한 단서에 대한 매우 높은 신뢰도를 보여주는 것이 특징입니다. 이는 다른 단서에서 나온 정보가 실제로 처리 과정에서 손실된다는 것을 시사합니다.  두 번째(상당히 신뢰도가 낮은) 예측 토큰은 종종(70.7%) 상반되는 단서에 속하지 않습니다.  상위 2개 쌍 중 17.7%만이 모양과 질감 모두를 포함합니다. 평균적으로 모델은 질감 결정에 대해 약간 덜 확신하는 경향이 있습니다(p=0.87 대 0.92). 신뢰도 임계값 이상의 응답만 분석할 때 이는 더욱 분명해집니다.  p=0.5까지는 측정에 큰 영향을 미치지 않지만, 그 이후에는 질감 결정의 비율이 감소하지 않고 모양 결정의 비율이 증가하여 모양 편향이 커집니다.  p=0.9를 넘어서면 모델은 모양 단서만을 사용하여 추론합니다. 이러한 결과가 다른 모델에도 일반화되는지는 불분명하지만, LLaVA는 현재 많은 후속 모델의 기본이 되므로 이러한 편향을 그대로 이어받을 가능성이 높습니다.
> <details>
> <summary>read the caption</summary>
> (b)
> </details>



![](https://arxiv.org/html/2403.09193/x5.png)

> 🔼 그림 3은 VLMs이 한 가지 특정 단서를 선호하고 다른 단서를 무시하는 테스트에서 높은 신뢰도의 답변을 제공함을 보여줍니다. 신뢰도는 단서에 따라 약간 다르지만, 가장 높은 신뢰도를 가진 답변은 전적으로 모양 단서에 속합니다. (a) 모든 샘플에 대한 모양 및 질감 토큰의 신뢰도 분포, (b) 정확한 예측(즉, 예측된 레이블이 모양 또는 질감과 일치하는 경우)의 신뢰도 분포, (c) 신뢰도를 필터링할 때 모양 편향의 변화를 보여줍니다. LLaVA-NeXT 7B의 VQA 작업에 대해 측정되었습니다.
> <details>
> <summary>read the caption</summary>
> (c)
> </details>



![](https://arxiv.org/html/2403.09193/x6.png)

> 🔼 그림 3은 시각 언어 모델(VLMs)이 높은 신뢰도로 답변을 제시하며 특정 단서를 선호하고 다른 단서를 무시하는 경향을 보여줍니다. 신뢰도는 단서에 따라 약간씩 다르지만, 가장 높은 신뢰도를 가진 답변은 모양 단서에만 국한됩니다. (a)는 모든 표본에 대한 모양 및 질감 토큰의 신뢰도 분포를, (b)는 올바른 예측(즉, 예측 레이블이 모양 또는 질감과 일치)에 대한 신뢰도 분포를 보여줍니다. (c)는 신뢰도를 필터링할 경우 모양 편향의 변화를 보여줍니다. LLaVA-NeXT 7B 모델의 VQA 작업을 기준으로 측정되었습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: VLMs provide high-confidence answers in our test that prefer one specific cue and ignore the other. Confidence only slightly differs by cue, but answers with the highest confidence exclusively belong to shape decisions. (a) Confidence distribution of shape and texture tokens for all samples, (b) Confidence distribution in correct predictions (i.e., the predicted label matches either shape or texture), (c) Evolution of shape bias if filtering for confidence. Measured on LLaVA-NeXT 7B for the VQA task.
> </details>



![](https://arxiv.org/html/2403.09193/x7.png)

> 🔼 그림 4는 다양한 비전 언어 모델(VLM), 이미지넷 기반 모델, 이미지넷 미세 조정 및 제로샷 분류를 거친 VLM 인코더, 그리고 10명의 사람의 응답을 보여줍니다.  각 모델의 응답은 VQA 작업에서 수행되었으며, 그림에서 '오류 일관성'(Error Consistency)이라는 지표를 통해 모델 간 오류의 유사성을 측정했습니다. 오류는 형태 클래스에 속하지 않는 모든 응답을 의미합니다. 이 그림은 VLM이 이미지넷 기반 모델보다 사람과 유사한 오류를 범한다는 것을 보여줍니다. 또한 VLM의 오류는 그들의 비전 인코더와 유사성을 공유함을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 4: VLMs make similar errors on the cue-conflict datasets and share similarities with their vision encoders. In terms of errors, VLMs are also more similar to humans than ImageNet-trained/finetuned models. We measure the pair-wise error consistency [71] between predictions. For this analysis, an error is any answer that does not belong to the shape class (analogous to [29]). Shown responses belong to LLM-based VLMs (under the VQA task), other selected models including ImageNet models, (some) VLM encoders under ImageNet-finetuning and zero-shot classification, and ten human subjects.
> </details>



![](https://arxiv.org/html/2403.09193/x8.png)

> 🔼 그림 5는 이미지 전처리가 질감-형태 편향에 큰 영향을 미칠 수 있음을 보여줍니다. 왼쪽 패널은 이미지 패치를 무작위로 섞고 패치 크기를 줄이면 질감 정보는 유지되지만 형태 정보가 손실되어 질감 편향이 강해짐을 보여줍니다. 오른쪽 패널은 가우시안 노이즈를 증가시키면 형태 정보는 유지되지만 질감 정보가 손실되어 형태 편향이 강해짐을 보여줍니다. 이 그림은 다양한 패치 크기와 가우시안 노이즈 강도에 따른 질감-형태 편향의 변화를 정량적으로 보여주는 그래프를 포함하고 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Image preprocessing can strongly steer texture/shape bias. Left: Shuffling image patches with decreasing patch size results in a strong texture bias, Right: Increasing Gaussian noise introduces a strong shape bias.
> </details>



![](https://arxiv.org/html/2403.09193/x9.png)

> 🔼 그림 6은 프롬프트가 질감/형태 편향을 어느 정도 조정할 수 있음을 보여줍니다. 여러 모델에서 동일한 질감/형태 편향 지시문을 테스트하여 일부 결정(주로 질감 쪽으로)을 이미 변경할 수 있음을 보여줍니다. InternVL 1.1 및 LLaVA-NeXT 7B의 경우 동의어를 사용하여 질감/형태에 대한 이해도를 추가로 테스트했습니다. 또한, LLM을 사용하여 어느 방향으로든 최적화할 특정 프롬프트를 자동으로 검색했습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Prompts can steer the texture/shape bias to some extent. We test the same texture/shape-biased instructions on multiple models, showing that these can already shift some decisions (usually in favor of texture). For InternVL 1.1 and LLaVA-NeXT 7B we additionally test the understanding of texture/shape by using synonyms. Furthermore, we use an LLM to automatically search for specific prompts to optimize in either direction.
> </details>



![](https://arxiv.org/html/2403.09193/x10.png)

> 🔼 그림 7은 편향된 VQA 프롬프트에 대한 동의어를 사용한 세부적인 형태 편향 측정 결과를 보여줍니다.  이 그림은 '질감' 또는 '형태'라는 단어 대신 동의어를 사용하여 질감 또는 형태에 대한 언급 방식을 바꾸었을 때, 모델의 형태 편향이 어떻게 변하는지 보여줍니다.  각 동의어에 대한 형태 편향의 변화를 정량적으로 제시하며,  특정 동의어가 형태 또는 질감 중 어느 쪽에 더 큰 영향을 미치는지 보여줍니다.  다양한 모델에서 형태 편향에 대한 동의어 사용의 효과를 보여줌으로써, 언어적 변화를 통한 시각적 편향 조정 가능성을 시각적으로 제시합니다.
> <details>
> <summary>read the caption</summary>
> Figure 7: Detailed shape bias measurements under synonyms for biased VQA prompts.
> </details>



![](https://arxiv.org/html/2403.09193/x11.png)

> 🔼 본 그림은 온도 조절이 VQA와 이미지 캡션 작업 모두에서 형태 편향에 유의미한 영향을 미치지 않지만, 높은 수준에서는 정확도를 떨어뜨린다는 것을 보여줍니다. LLaVA-NeXT 7B 모델을 사용하여 실험을 수행했으며, 이미지 캡션 작업의 온도가 0 또는 1인 경우를 제외하고는 3개의 시드를 사용했습니다. 온도가 높아짐에 따라 모델의 창의성이 증가하지만, 동시에 비현실적인 결과를 생성할 가능성도 커집니다. 그림은 온도 변화에 따른 형태 편향과 정확도 변화를 그래프로 나타내어, 온도 조절이 모델의 성능에 미치는 영향을 명확하게 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Temperature scaling has no significant effect on shape bias neither under VQA (left) nor Image Captioning (right) tasks but starts to decrease accuracy at higher levels. Experiments performed on LLaVA-NeXT 7B with 3 seeds (except Temperature = 0 and Temperature = 1 of Image Captioning where we use a single seed).
> </details>



![](https://arxiv.org/html/2403.09193/x12.png)

> 🔼 그림 9는 다양한 VLMs에 대한 질감 대 형태 편향을 VQA(왼쪽) 및 이미지 자막 생성(오른쪽) 작업에 대해 클래스별로 보여줍니다. 각 점은 특정 클래스의 질감 및 형태 결정 비율을 나타내며, 모델이 어떤 측면에 더 중점을 두는지 보여줍니다. 왼쪽 패널(VQA)에서는 질감 대 형태 결정 비율이 모델과 작업 간에 상당히 다르게 나타납니다. 일부 모델은 형태에 더 중점을 두고, 다른 모델은 질감에 더 중점을 둡니다. 오른쪽 패널(이미지 자막 생성)에서는 모델 간 일관성이 더 높으며, 대부분의 모델에서 형태에 대한 강한 편향을 보입니다. 이 그림은 서로 다른 모델의 결정 과정에서의 차이를 시각적으로 보여주며, VQA와 이미지 자막 생성 작업 간의 차이점을 강조합니다.
> <details>
> <summary>read the caption</summary>
> (a) VQA
> </details>



![](https://arxiv.org/html/2403.09193/x13.png)

> 🔼 그림 (b)는 논문의 4.1절 '주요 결과' 섹션에 있는 그림으로, 다양한 VLMs(Vision Language Models)의 텍스처-쉐이프 편향(texture-shape bias)을 이미지 캡셔닝 작업에서 측정한 결과를 보여줍니다.  x축은 쉐이프(shape) 결정 비율을, y축은 텍스처(texture) 결정 비율을 나타냅니다. 각 점은 특정 VLM 모델을 나타내며, 점의 위치는 해당 모델이 이미지를 캡셔닝할 때 쉐이프 정보와 텍스처 정보 중 어느 쪽에 더 의존하는지를 보여줍니다.  점이 x축에 가까울수록 쉐이프에 더 의존하고, y축에 가까울수록 텍스처에 더 의존함을 의미합니다.  이 그림은 다양한 VLM 모델들이 이미지 캡셔닝 작업에서 쉐이프에 대한 편향을 보이는 정도가 다름을 시각적으로 보여줍니다. 또한 인간의 쉐이프 편향(96%)과 비교하여 VLM 모델들의 편향 정도를 비교 분석하는 데에도 활용됩니다.
> <details>
> <summary>read the caption</summary>
> (b) Image Captioning
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Model | VQA |  | Image Captioning |  |  |  |  |
|---|---|---|---|---|---|---|---|---|
|  | Shape | Accuracy [%] | Shape | Accuracy [%] | Avg. Tokens | Single Class Ratio [%] | Generic Ratio [%] |
|---|---|---|---|---|---|---|---|---|
| Gemini 1.0 Pro Vision [25] | 64.1 | 82.33 | 63.2 | 68.00 | 18.9 | 63.0 | 32.3 |
| GPT-4V (Preview) [12] | 47.9 | 69.75 | 53.6 | 52.67 | 44.8 | 37.2 | 60.4 |
| Qwen-VL Plus [26] | 64.8 | 82.92 | 67.9 | 65.50 | 21.9 | 59.2 | 36.0 |
| Qwen-VL Max [26] | 62.4 | 85.50 | 69.7 | 68.50 | 151.9 | 52.1 | 41.0 |
| Qwen-VL Chat [63] | - | - | 38.2 | 67.42 | 27.3 | 59.1 | 33.2 |
| InternVL Chat 1.1 [2] | 68.3 | 89.33 | 73.2 | 75.58 | 16.9 | 74.9 | 19.4 |
| InternVL Chat 1.2+ [2] | 61.1 | 90.83 | 61.3 | 82.42 | 15.8 | 80.4 | 11.4 |
| LLaVA v1.5 7B [61] | 61.4 | 80.75 | 61.4 | 76.08 | 12.1 | 73.8 | 19.2 |
| LLaVA v1.5 13B [61] | 64.1 | 80.25 | 62.7 | 75.58 | 28.9 | 65.8 | 23.8 |
| LLaVA-RLHF 7B [69] | 61.7 | 68.08 | 63.0 | 71.83 | 47.9 | 65.1 | 24.7 |
| LLaVA-RLHF 13B [69] | 63.4 | 80.42 | 62.3 | 73.25 | 38.3 | 64.7 | 27.7 |
| LLaVA-NeXT 7B [62] | 59.2 | 82.58 | 64.0 | 65.08 | 20.2 | 55.5 | 39.5 |
| LLaVA-NeXT 13B [62] | 57.2 | 83.42 | 63.5 | 65.25 | 48.8 | 52.6 | 40.9 |
| LLaVA-NeXT 34B [62] | 56.0 | 73.83 | 66.2 | 57.50 | 93.4 | 36.2 | 59.1 |
| MoE-LLaVA-StableLM [67] | 59.1 | 80.08 | 63.0 | 73.92 | 24.1 | 67.4 | 21.6 |
| MoE-LLaVA-Qwen [67] | 62.9 | 59.50 | 63.2 | 75.33 | 13.3 | 69.4 | 20.7 |
| MoE-LLaVA-Phi2 [67] | 59.6 | 82.33 | 61.1 | 75.42 | 34.9 | 67.0 | 18.6 |
| InstructBLIP Flan-T5-xl [23] | 68.2 | 79.58 | 67.1 | 81.50 | 116.7 | 57.0 | 22.3 |
| InstructBLIP Vicuna-7B [23] | 73.8 | 72.25 | 67.7 | 80.67 | 94.0 | 60.9 | 28.0 |
| Emu2-Chat [66] | 52.9 | 75.08 | 59.6 | 65.00 | 13.6 | 63.0 | 34.0 |
| CogAgent Chat [64] | - | - | 67.4 | 60.33 | 40.1 | 49.6 | 47.7 |
| CogVLM Chat [65] | - | - | 57.6 | 66.58 | 35.8 | 53.2 | 40.1 |
| UForm Gen Chat [68] | - | - | 38.8 | 64.50 | 30.2 | 59.3 | 33.0 |{{< /table-caption >}}
> 🔼 표 3은 VQA(Visual Question Answering) 작업에서 사용된 다양한 프롬프트를 탐색한 결과를 보여줍니다.  기본 프롬프트를 비롯하여, CLIP 스타일의 옵션을 사용한 프롬프트, 이미지 내 객체에 대한 설명을 요청하는 프롬프트, CLIP 스타일 옵션과 함께 객체 설명을 요청하는 프롬프트, 그리고 지시사항 없이 옵션만 제공하는 프롬프트 등 다양한 변형이 시도되었습니다.  각 프롬프트에 대한 정확도와 형태 편향(shape bias)을 측정하여 비교 분석했습니다.  결과적으로 기본 프롬프트가 가장 좋은 정확도와 형태 편향의 균형을 이루는 것으로 나타났습니다.
> <details>
> <summary>read the caption</summary>
> Table 3: Exploration of alternative VQA prompts.
> </details>

{{< table-caption >}}
| Prompt | Bias [%] | Accuracy [%] |
|---|---|---|
| "Which option best describes the image? [...]" (default) | 59.2 | 82.58 |
| Default with CLIP-style options | 59.5 | 81.92 |
| "Describe the object in the image: [...]" | 60.2 | 81.33 |
| "Describe the object in the image: [...]" |  |  |
| with CLIP-style options | 59.4 | 80.17 |
| Empty instruction (just options) | 59.5 | 81.33 |{{< /table-caption >}}
> 🔼 이 표는 이미지 캡션 작업을 위한 여러 가지 프롬프트를 시험한 결과를 보여줍니다. 기본 프롬프트 외에도 프롬프트에 추가적인 설명을 넣거나,  짧게 응답하도록 요청하는 등 다양한 변형을 시도했습니다. 각 프롬프트에 대한 정확도와 형태 편향을 측정하여 비교 분석했습니다.  결과적으로 기본 프롬프트가 가장 좋은 성능을 보였으나, 추가적인 설명이나 지시어가 정확도와 형태 편향에 미치는 영향을 확인할 수 있었습니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Exploration of alternative Image Captioning prompts.
> </details>

{{< table-caption >}}
| Prompt | Bias [%] | Accuracy [%] | Avg. Tokens | Generic Ratio [%] |
|---|---|---|---|---|
| "Describe the image. Keep your response short." (default) | 64.0 | 65.08 | 55.5 | 39.5 |
| "Describe the image." | 63.6 | 68.25 | 202.9 | 46.8 |
| "Describe the image. Be precise." | 67.3 | 64.50 | 166.2 | 50.6 |{{< /table-caption >}}
> 🔼 표 5는 LLM 기반 프롬프트 검색을 위한 예시 대화를 보여줍니다.  별표(*)는 모의 대화임을 나타냅니다.  이 표는 사용자가 LLM에게 이미지 분류 프롬프트를 최적화하여 형태 편향을 최소화하고 정확도를 유지하는 방법을 요청하는 대화를 보여줍니다.  사용자는 LLM이 프롬프트를 생성하고, 정확도와 형태 편향을 반환하며, 이를 바탕으로 프롬프트를 개선해 나가는 과정을 보여줍니다.  대화는 여러 라운드로 진행되며, LLM은 다양한 기법(보상 제공, 문맥 내 예시 추가, 이전 시도 요약 등)을 사용하여 프롬프트를 개선합니다.  결과적으로,  LLM은 수동으로 작성한 프롬프트보다 형태 편향을 더 줄이는 프롬프트를 생성합니다.
> <details>
> <summary>read the caption</summary>
> Table 5: Example conversation for LLM-guided Prompt Search. *{}^{*}start_FLOATSUPERSCRIPT * end_FLOATSUPERSCRIPTMock conversation.
> </details>

{{< table-caption >}}
| User* | Assistant* |
|---|---| 
| Your task is to help me design an ideal image classification prompt for a vision/language model to MINIMIZE the shape bias without significantly hurting accuracy. The provided photos show natural objects modified to contain shape and texture of conflicting object classes. E.g., it could be a photo of an elephant (shape) with dog fur (texture). The model should classify the image as ’dog’ based on the texture of the object and ignore the shape. The model’s accuracy is the percentage of correctly classified images. The shape bias is the ratio of how often the model classified based on shape over texture. You can test your prompt by outputting a single new line starting with ’PROMPT: ’. Do not list options - the system will provide them automatically. Try to keep the prompt as short and simple as possible but be creative. It might be reasonable to summarize insights of previous attempts and to outline your goals before responding with a new prompt, but make sure that only the prompt starts with ’PROMPT:’. In response to the prompt you will be told the accuracy and shape bias. Then you will refine the prompt and we will continue until I say stop. Let’s go! | PROMPT: Which option best describes the image? |
| Prompt: […], Accuracy: 82.58 %, Shape Bias: 59.43 %. What is your next prompt? | To minimize the shape bias while maintaining accuracy, let’s encourage the model to focus more on textures than shapes. Here’s my next prompt: PROMPT: Based on the surface characteristics and patterns, which category does the image most resemble? |
| Prompt: […], Accuracy: 78.25 %, Shape Bias: 50.9 %. Can you improve this? | I have provided various prompts and explored different approaches to minimize the shape bias while maintaining high accuracy. The current optimal prompt is: […] Here are some additional suggestions for minimizing the shape bias: […] These methods may require more computational resources and time investment. If you have other questions or need guidance on different topics, please don’t hesitate to reach out. Wishing you the best in your continued efforts! At this point, I believe that we have explored various approaches, and the current prompt is the best-performing one among those tested. If you decide to pursue any of the mentioned alternatives, I am confident that you will find ways to improve the model’s performance and minimize the shape bias. Good luck with your continued work! As our conversation has concluded, I would like to thank you for engaging in this exercise, and I hope I have been helpful in providing prompts and suggestions. If you have other questions or need guidance on different topics in the future, please don’t hesitate to reach out. Wishing you the best in your projects and research! |{{< /table-caption >}}
> 🔼 표 6은 다양한 CLIP 유사 결합 임베딩 모델을 사용하여 큐 충돌 데이터셋에서 제로샷 분류를 수행한 결과를 보여줍니다.  세 가지 다른 프롬프트 전략(80개의 프롬프트, 'a photo of a {class}', '{class}')을 사용하여 각 모델의 성능을 평가했습니다.  이 표는 각 프롬프트 전략에 따른 각 모델의 형태 편향(Shape Bias)과 정확도(Accuracy)를 보여주어, 모델의 시각적 특징 인식 방식을 비교 분석하는 데 도움을 줍니다.  CLIP 모델의 형태 편향 및 정확도에 대한 자세한 분석 결과가 제시되어 있으며, 다양한 프롬프트 전략에 따른 결과 차이를 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Zero-shot classification on cue-conflict with different CLIP(-like) joint embedding models.
> </details>

{{< table-caption >}}
| Model | Prompt | Shape Bias [%] | Accuracy [%] |
|---|---|---|---|
| EVA01-CLIP-g/14 [17] | 80 Prompts [11] | 66.03 | 87.83 |
| EVA01-CLIP-g/14 [17] | "a photo of a {class}." | 66.03 | 87.08 |
| EVA01-CLIP-g/14 [17] | "{class}" | 66.44 | 86.67 |
| EVA02-CLIP-8B@448px [82] | 80 Prompts [11] | 58.26 | 91.83 |
| EVA02-CLIP-8B@448px [82] | "a photo of a {class}." | 57.58 | 89.00 |
| EVA02-CLIP-8B@448px [82] | "{class}" | 56.60 | 88.33 |
| EVA02-CLIP-E/14+ [17] | 80 Prompts [11] | 65.62 | 90.67 |
| EVA02-CLIP-E/14+ [17] | "a photo of a {class}." | 64.44 | 89.75 |
| EVA02-CLIP-E/14+ [17] | "{class}" | 62.48 | 86.17 |
| CLIP-ViT-L/14 [11] | 80 Prompts [11] | 60.95 | 84.08 |
| CLIP-ViT-L/14 [11] | "a photo of a {class}." | 60.20 | 84.17 |
| CLIP-ViT-L/14 [11] | "{class}" | 60.16 | 81.17 |
| CLIP-ViT-L/14@336px [11] | 80 Prompts [11] | 61.52 | 86.83 |
| CLIP-ViT-L/14@336px [11] | "a photo of a {class}." | 60.56 | 86.42 |
| CLIP-ViT-L/14@336px [11] | "{class}" | 59.80 | 83.75 |
| CLIP-ResNet-50 [11] | 80 Prompts [11] | 19.70 | 77.83 |
| CLIP-ResNet-50 [11] | "a photo of a {class}." | 20.96 | 72.75 |
| CLIP-ResNet-50 [11] | "{class}" | 20.77 | 71.83 |
| CLIP-ResNet-101 [11] | 80 Prompts [11] | 25.50 | 74.83 |
| CLIP-ResNet-101 [11] | "a photo of a {class}." | 25.23 | 71.00 |
| CLIP-ResNet-101 [11] | "{class}" | 25.41 | 70.83 |{{< /table-caption >}}
> 🔼 표 7은 VQA 작업에서 큐 충돌 데이터셋을 사용하여 VLMs(Vision Language Models)와 각각의 비전 인코더(CLIP zero-shot classification)의 형태 바이어스와 정확도 간의 정량적 비교를 보여줍니다.  각 VLM에 대해 형태 바이어스와 정확도의 변화율(백분율)이 표시됩니다.  이 표는 VLMs가 비전 인코더의 형태 바이어스를 단순히 상속하는 것이 아니라, 다중 모드 융합을 통해 형태 바이어스가 어떻게 변형될 수 있는지를 보여주는 실험 결과를 요약한 것입니다.  음수 값은 VLM이 인코더보다 형태 바이어스가 감소했음을, 양수 값은 증가했음을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Quantitative comparison between shape bias and accuracy of VLMs (VQA) and their respective vision encoders (CLIP zero-shot classification) on cue-conflict.
> </details>

{{< table-caption >}}
| VLM | Vision Encoder | Accuracy | Shape-Bias |
|---|---|---|---| 
| **LLaVA v1.5 7B** <a href="https://arxiv.org/html/2403.09193v1#bib.bib61">[61]</a> | ❄ CLIP ViT-L/14@336px <a href="https://arxiv.org/html/2403.09193v1#bib.bib11">[11]</a> | -3.50 | 4.2 |
| **LLaVA v1.5 13B** <a href="https://arxiv.org/html/2403.09193v1#bib.bib61">[61]</a> |  | -3.00 | 1.5 |
| **LLaVA-NeXT 7B** <a href="https://arxiv.org/html/2403.09193v1#bib.bib62">[62]</a> |  | -9.92 | -3.9 |
| **LLaVA-NeXT 13B** <a href="https://arxiv.org/html/2403.09193v1#bib.bib62">[62]</a> |  | -0.33 | -2.7 |
| **LLaVA-NeXT 34B** <a href="https://arxiv.org/html/2403.09193v1#bib.bib62">[62]</a> |  | -1.08 | -0.2 |
| **MoE-LLaVA v1.5 Phi2 x4** <a href="https://arxiv.org/html/2403.09193v1#bib.bib67">[67]</a> |  | -1.42 | -0.3 |
| **MoE-LLaVA v1.5 Qwen x4** <a href="https://arxiv.org/html/2403.09193v1#bib.bib67">[67]</a> |  | -24.25 | 3.0 |
| **MoE-LLaVA v1.5 StableLM x4** <a href="https://arxiv.org/html/2403.09193v1#bib.bib67">[67]</a> |  | -3.67 | -0.8 |
| **InstructBLIP FLAN-T5-XL** <a href="https://arxiv.org/html/2403.09193v1#bib.bib23">[23]</a> | ❄ EVA-01-CLIP ViT-g/14@224px <a href="https://arxiv.org/html/2403.09193v1#bib.bib17">[17]</a> | -6.83 | 1.8 |
| **InstructBLIP Vicuna-7B** <a href="https://arxiv.org/html/2403.09193v1#bib.bib23">[23]</a> |  | -14.42 | 7.4 |
| **Emu2-Chat** <a href="https://arxiv.org/html/2403.09193v1#bib.bib66">[66]</a> | ❄ EVA-02-CLIP-E/14+@448px <a href="https://arxiv.org/html/2403.09193v1#bib.bib17">[17]</a> | -11.08 | -9.5 |{{< /table-caption >}}
> 🔼 표 8은 ImageNet으로 학습되거나 미세 조정된 모델들에 대한 큐 충돌(cue-conflict) 데이터셋에서의 분류 결과를 보여줍니다.  'Shape Bias' 열은 모델이 형태(shape) 정보에 얼마나 치우쳐져 있는지를 나타내는 백분율이며, 'Accuracy' 열은 모델의 정확도를 나타내는 백분율입니다.  다양한 모델의 형태 편향과 정확도를 비교하여 ImageNet 학습의 영향을 분석하고자 합니다.
> <details>
> <summary>read the caption</summary>
> Table 8: Classification on cue-conflict with ImageNet-trained/finetuned models.
> </details>

{{< table-caption >}}
| Model | Shape Bias [%] | Accuracy [%] |
|---|---|---|
| ResNet-50 [59] | 22.3 | 67.33 |
| ResNet-50 (timm) [83] | 23.1 | 65.42 |
| ResNet-152 (timm) [83] | 28.6 | 65.83 |
| ViT-B/16 (ImageNet-21k pretraining) [32] | 45.4 | 63.67 |
| ImageNet-finetuned CLIP (ViT-L/14@336px) [83] | 32.1 | 82.75 |{{< /table-caption >}}
> 🔼 이 표는 이미지 캡션 작업에 대한 모든 응답과 LLM이 일반적이지 않다고 분류하지 않은 응답에 대해 형태 편향 및 정확도를 비교한 것입니다.  LLM이 일반적이지 않다고 분류한 응답은 즉, 모델이 이미지의 내용을 명확하게 묘사하지 못한 응답을 의미합니다. 표는 모든 응답을 고려한 결과와 일반적이지 않은 응답만 고려한 결과를 모두 보여주어, 일반적인 응답과 명확한 응답 사이의 형태 편향 및 정확도 차이를 비교 분석하는 데 도움을 줍니다.
> <details>
> <summary>read the caption</summary>
> Table 9: Comparison of shape bias and accuracy for the Image Captioning tasks for all responses and only responses which an LLM did not classify as generic.
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