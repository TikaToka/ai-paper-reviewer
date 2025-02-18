---
title: "Precise Parameter Localization for Textual Generation in Diffusion Models"
summary: "단 1% 미만의 매개변수만으로도 이미지 내 텍스트 생성을 제어할 수 있다는 사실을 밝혀낸 연구!"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Image Generation", "🏢 CISPA Helmholtz Center for Information Security",]
showSummary: true
date: 2025-02-14
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.09935 {{< /keyword >}}
{{< keyword icon="writer" >}} Łukasz Staniszewski et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-17 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.09935" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.09935" target="_self" >}}
↗ Hugging Face
{{< /button >}}




### TL;DR


{{< lead >}}

최근 고품질 이미지 합성에 뛰어난 성능을 보이는 확산 모델들이 주목받고 있지만, **텍스트 생성 과정의 복잡성과 비효율성**은 여전히 과제로 남아있습니다. 특히, 모델의 매개변수가 방대하여 효율적인 텍스트 생성 및 편집이 어렵고, 유해 텍스트 생성 방지에도 어려움이 있습니다. 이러한 문제를 해결하기 위한 새로운 접근법이 필요합니다. 

본 연구는 **확산 모델에서 텍스트 생성에 관여하는 매개변수를 국재화**하는 기법을 제시합니다. 연구진은 주의 집중 계층의 활성화 패치 기법을 이용하여, 전체 매개변수의 1% 미만만이 텍스트 생성에 영향을 미친다는 사실을 발견했습니다.  이를 바탕으로, 국재화된 계층만을 미세 조정하는 LoRA 기반의 새로운 미세 조정 전략을 제시하여 텍스트 생성 성능을 향상시켰습니다. 또한, 이 기법을 이용하여 이미지 내 텍스트를 편집하고 유해 텍스트 생성을 방지하는 응용 기술을 개발했습니다.  이는 다양한 확산 모델 구조와 텍스트 인코더에 적용 가능한 일반적인 방법론으로,  **확산 모델의 효율성과 해석성을 높이고, 다양한 응용 분야에 기여**할 수 있습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 확산 모델에서 텍스트 생성에 영향을 미치는 매개변수는 전체의 1% 미만임을 밝힘 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} LoRA 기반의 국재화된 계층 미세 조정을 통해 텍스트 생성 효율성 및 성능 개선 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 국재화된 계층을 이용한 이미지 내 텍스트 편집 및 유해 텍스트 생성 방지 기술 개발 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **텍스트 생성을 위한 매개변수 국재화 기법**을 제시하여, 확산 모델의 효율성 및 성능을 향상시키고, 텍스트 편집 및 유해 텍스트 생성 방지와 같은 다양한 응용 분야에 기여하는 중요한 연구입니다. **소량의 매개변수만으로 텍스트 생성에 영향**을 미치는 것을 밝혀냄으로써, **컴퓨팅 자원을 절약**하고 **모델의 해석성을 높이는 데 기여**할 수 있습니다.  또한, 다양한 확산 모델 구조와 텍스트 인코더에 적용 가능한 일반적인 방법론을 제시하여, 향후 연구의 기반을 마련합니다.

------
#### Visual Insights



![](https://arxiv.org/html/2502.09935/x1.png)

> 🔼 그림 1은 논문의 핵심 기법인 주의 메커니즘 계층의 위치 파악 과정을 보여줍니다. 목표는 소스 프롬프트(pS)로 생성된 이미지의 텍스트를 타겟 프롬프트(pT)의 내용으로 수정하는 것입니다.  이를 위해 타겟 프롬프트(pT)를 확산 모델(DM)에 통과시켜 각 주의 메커니즘 계층의 키(key)와 값(value)을 저장합니다. 그런 다음 소스 프롬프트(pS)로 이미지를 생성하는 과정에서 저장된 키와 값을 사용하여 기존 키와 값을 대체합니다.  이미지와 텍스트 정렬도가 가장 높은 계층을 선택하여 해당 계층을 수정합니다. (A)는 SD3 모델에 적용되는 패치 기법을, (B)는 SDXL과 DeepFloyd IF 모델에 적용되는 주입 기법을 각각 보여줍니다.  즉, 어떤 주의 메커니즘 계층이 이미지 내 텍스트 생성에 영향을 미치는지 찾아내는 방법을 시각적으로 설명한 것입니다.
> <details>
> <summary>read the caption</summary>
> Figure 1: Overview of the localization process. Our goal is to edit the image generated from the source prompt pSsubscript𝑝𝑆p_{S}italic_p start_POSTSUBSCRIPT italic_S end_POSTSUBSCRIPT using the target prompt pTsubscript𝑝𝑇p_{T}italic_p start_POSTSUBSCRIPT italic_T end_POSTSUBSCRIPT. To find which cross and joint attention layers should be modified, we pass the target prompt pTsubscript𝑝𝑇p_{T}italic_p start_POSTSUBSCRIPT italic_T end_POSTSUBSCRIPT through the DM, caching the keys and values. Then, while generating the image from pSsubscript𝑝𝑆p_{S}italic_p start_POSTSUBSCRIPT italic_S end_POSTSUBSCRIPT we substitute the keys and values with the cached ones. We select the layers which yield the highest image and text alignment. (A) Localizing by Patching is applied to SD3, and (B) Localizing by Injection is used for SDXL and DeepFloyd IF.
> </details>





{{< table-caption >}}
| Model | # localized layers | total # of cross-attention layers | # localized parameters | fraction of model parameters [%] |
|---|---|---|---|---|
| **SDXL** [Podell et al., 2024] | 3 | 70 | 15.7M | 0.61% |
| **DeepFloyd IF** [StabilityAI, 2023] | 1 | 22 | 8.9M | 0.21% |
| **SD3** [Esser et al., 2024] | 1 | 24 | 4.7M | 0.23% |{{< /table-caption >}}

> 🔼 이 표는 세 가지 최신 텍스트-이미지 확산 모델(SDXL, DeepFloyd IF, SD3)에서 텍스트 생성에 영향을 미치는 매개변수의 비율이 실제로 매우 작다는 것을 보여줍니다. 각 모델의 매개변수 중 1% 미만이 이미지 내 텍스트 생성에 영향을 미치는 것으로 나타났습니다. 이는 모델의 소수의 매개변수만이 이미지 내 텍스트 생성에 기여한다는 것을 시사하며, 이는 효율적인 미세 조정 및 텍스트 편집 방법을 개발하는 데 중요한 의미를 가집니다.
> <details>
> <summary>read the caption</summary>
> Table 1: Less than 1111% of DMs’ parameters influence text generation within the images.
> </details>





### In-depth insights


#### Textual Diffusion
텍스트 확산(Textual Diffusion)은 이미지 생성에 텍스트를 조건으로 사용하는 확산 모델을 의미합니다. 이는 **단순한 이미지 생성을 넘어, 텍스트로 이미지의 내용과 스타일을 세밀하게 제어**할 수 있다는 점에서 매우 중요한 발전입니다.  본 논문에서는 텍스트 확산 모델의 매개변수를 분석하여, 텍스트 생성에 영향을 미치는 부분을 국한시키는 방법을 제시합니다. **이는 모델의 효율성을 높이고, 텍스트 편집 및 독성 텍스트 생성 방지**와 같은 응용 분야에 활용될 수 있습니다.  **특히, cross-attention과 joint-attention 계층에 주목**하여, 해당 계층의 일부 매개변수만 조정하여도 텍스트 생성 성능을 향상시킬 수 있음을 보여줍니다.  **이러한 국지적 최적화는 모델의 전반적인 성능을 유지하면서 텍스트 관련 기능을 개선**하는 데 효과적입니다.  **LoRA(Low-Rank Adaptation)와 같은 기술을 활용**하여,  **대규모 모델의 재학습 없이도 높은 효율성으로 성능 개선**을 달성할 수 있습니다.  **본 연구는 텍스트 확산 모델의 해석성을 높이고, 다양한 응용 분야에서 활용 가능성을 제시**함으로써  향후 연구의 중요한 발판을 마련할 것으로 예상됩니다.

#### LoRA Fine-tuning
본 논문에서 제시된 LoRA fine-tuning 전략은 **텍스트 생성에 관여하는 특정 cross-attention 레이어들만을 타겟팅하여** 기존 확산 모델의 성능을 향상시키는 데 초점을 맞춥니다.  기존의 전체 모델 파라미터를 미세 조정하는 방법과 달리, **계산 비용을 절감**하면서도 **텍스트 생성 품질을 개선**할 수 있다는 점이 강조됩니다. 이러한 접근 방식은 모델의 전반적인 생성 능력을 유지하면서 특정 작업에 대한 성능을 향상시키는 효율적인 방법입니다.  **다양한 모델 구조와 텍스트 인코더에 걸쳐 적용 가능성**을 보여주는 실험 결과는 이 방법의 폭넓은 활용성을 시사합니다. 특히, LoRA를 통해 미세 조정된 특정 레이어는 **원본 모델의 다양성과 품질을 유지**하면서도 텍스트 생성 능력을 향상시켜 **효율성 및 성능 개선**이라는 두 마리 토끼를 잡을 수 있다는 점을 보여줍니다.  **과적합 방지**에도 효과적이며,  **소규모 데이터셋**에서도 우수한 성능을 보이는 점은 실용적인 측면에서 큰 장점입니다.

#### Attention Layer
본 논문에서 주목할 부분은 **어텐션 레이어의 국소화**를 통해 텍스트 생성 효율성과 성능을 향상시키는 방법을 제시했다는 점입니다.  연구진은 어텐션 레이어가 이미지 내 텍스트 생성에 미치는 영향을 분석하여, **전체 파라미터의 1% 미만**만이 텍스트 생성에 영향을 준다는 것을 발견했습니다. 이러한 발견을 바탕으로,  **LoRA 기반의 미세 조정**을 통해 국소화된 레이어만을 조정함으로써, 대규모 확산 모델의 텍스트 생성 능력을 향상시키면서도 기존의 품질과 다양성을 유지할 수 있음을 보였습니다.  **국소화된 레이어를 활용**하여 생성된 이미지의 텍스트 콘텐츠를 편집하고, 유해한 텍스트 생성을 방지하는 등 다양한 응용 사례를 제시한 점도 긍정적입니다.  **다양한 확산 모델 아키텍처**와 텍스트 인코더에 걸쳐 광범위하게 적용 가능하다는 점에서,  본 연구는 **텍스트 생성을 위한 어텐션 레이어의 역할**에 대한 이해를 높이고, 향후 연구 발전에 중요한 기여를 할 것으로 기대됩니다.

#### Text Editing
본 논문에서 제시된 텍스트 편집 방법은 **기존의 방법들보다 훨씬 효율적이고 정확하며,** 이미지의 다른 시각적 속성에 영향을 미치지 않고 텍스트를 수정할 수 있다는 점에서 큰 장점을 지닙니다. 특히, **소량의 매개변수만을 사용하여 텍스트를 편집**함으로써 연산 비용을 최소화하고, **다양한 모델 구조에서도 적용 가능**하다는 점이 중요한 강점입니다.  **LoRA 기반 미세 조정**을 통해 텍스트 생성 성능을 향상시키는 방식은 훈련 데이터셋의 크기에 덜 민감하고,  **이미지 생성 과정에서 독성 텍스트 생성을 효과적으로 방지**하는 데에도 활용될 수 있습니다. 이러한 텍스트 편집 기능은 **다양한 응용 분야**에서 활용될 가능성을 제시하며, 향후 연구에서는 더욱 다양한 텍스트 편집 및 이미지 생성 기술에 대한 심층적인 분석과 발전이 필요합니다.

#### Toxicity Control
본 논문에서 제시된 독성 제어 방식은 **확산 모델의 특정 cross-attention 계층을 식별하여 독성 텍스트 생성을 방지**하는 데 중점을 둡니다.  단순히 독성 단어를 제거하는 대신, 모델의 텍스트 생성 메커니즘에 대한 이해를 바탕으로 독성 콘텐츠를 생성하는 부분만을 표적으로 합니다. 이는 **기존의 부정적 프롬프트나 안전한 확산 모델과 같은 방법보다 효율적이고 효과적**이며, **추가적인 계산 비용 없이 실시간으로 독성 텍스트 생성을 억제**할 수 있습니다.  **다양한 모델 아키텍처와 텍스트 인코더에 적용 가능**하다는 점 또한 중요한 강점입니다.  하지만 이 방법은 **독성 텍스트를 정확히 식별하고 대체하는 자연어 처리 모델의 성능에 의존**하며,  **미묘한 독성 표현이나 맥락에 따른 독성 판단은 어려움**이 있을 수 있습니다.  **모델의 해석 가능성을 높이고 안전성을 강화**하는 데 기여하는 기술이지만, 완벽한 독성 제어를 위한 추가적인 연구가 필요**합니다.


### More visual insights

<details>
<summary>More on figures
</summary>


![](https://arxiv.org/html/2502.09935/x2.png)

> 🔼 이 그림은 텍스트 생성에 관여하는 어텐션 레이어의 위치를 보여줍니다. 세 가지 최신 확산 모델(SDXL, DeepFloyd IF, SD3)에서 각 레이어의 크로스 및 조인트 어텐션 레이어를 선택적으로 패치하여 타겟 프롬프트를 계산하고 OCR F1 점수를 사용하여 응답을 측정했습니다. 그 결과 SDXL에서는 55, 56, 57번 레이어, DeepFloyd IF에서는 17번 레이어, SD3에서는 10번 레이어가 텍스트 생성에 가장 큰 영향을 미치는 레이어로 확인되었습니다. 이는 각 모델의 파라미터 중 1% 미만만이 이미지 내 텍스트 생성에 영향을 미친다는 것을 시각적으로 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 2: Localized attention layers responsible for the content of the generated text. We selectively patch individual cross and joint attention layers with computations for the target prompt and measure the responses with OCR F1 Score. We identify three layers with the highest responses in SDXL (55, 56, and 57), one layer in DeepFloyd IF (17), and one layer in SD3 (10).
> </details>



![](https://arxiv.org/html/2502.09935/extracted/6198226/figs/lora_generations5.jpg)

> 🔼 그림 3은 소스 프롬프트(p<sub>S</sub>)와의 이미지 정렬과 타겟 프롬프트(p<sub>T</sub>)와의 텍스트 정렬 간의 균형을 효과적으로 맞추는 지역화된 레이어들을 보여줍니다.  설명을 간소화하기 위해 텍스트 정렬은 OCR F1 점수로, 이미지 정렬은 SSIM으로 측정했습니다. 타겟 프롬프트(p<sub>T</sub>)를 너무 많은 레이어에 주입하면 이미지 정렬이 저하되고(예: 오른쪽에서 두 번째 이미지의 로봇 가슴에 있는 일본어 텍스트, 오른쪽 첫 번째 이미지에 없는 물고기 등) 원치 않는 아티팩트가 발생하는 것을 알 수 있습니다. 반대로, p<sub>T</sub>를 너무 적은 레이어에 주입하면 생성된 텍스트가 수정되지 않습니다. 부록 E에 실험에 대한 자세한 내용이 나와 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 3: The localized layers effectively balance the text alignment with the target prompt pTsubscript𝑝𝑇p_{T}italic_p start_POSTSUBSCRIPT italic_T end_POSTSUBSCRIPT and the image alignment with the source prompt pSsubscript𝑝𝑆p_{S}italic_p start_POSTSUBSCRIPT italic_S end_POSTSUBSCRIPT. For ease of exposition, we measure the text alignment with OCR F1 and the image alignment with SSIM. We observe that injecting the target prompt pTsubscript𝑝𝑇p_{T}italic_p start_POSTSUBSCRIPT italic_T end_POSTSUBSCRIPT to too many layers decreases the image alignment and introduces undesirable artifacts, e.g., the Japanese text on the robot’s chest in 2nd image from the right and the lack of fish in the 1st image from the right. Conversely, injecting pTsubscript𝑝𝑇p_{T}italic_p start_POSTSUBSCRIPT italic_T end_POSTSUBSCRIPT to too few layers does not edit the generated text. We present more details about the experiment in Appendix E.
> </details>



![](https://arxiv.org/html/2502.09935/x10.png)

> 🔼 그림 4는 제안된 패치 기법이 어떻게 소스 프롬프트의 시각적 요소는 유지하면서 타겟 프롬프트의 텍스트 정보만을 선택적으로 통합하는지 보여줍니다.  실험은 다양한 템플릿과 텍스트 조합을 사용하여 수행되었으며, 국소화된 확산 모델 레이어에 주입된 정보는 타겟 프롬프트의 텍스트와 일치하는 반면, 다른 레이어들은 소스 프롬프트의 시각적 구성요소를 유지하는 경향을 보였습니다.  결과적으로 생성된 이미지의 시각적 요소는 소스 템플릿과 유사하며, 텍스트 내용은 타겟 프롬프트와 일치합니다.  소스 프롬프트는 'TemplateS:TextS'로 정의되고, 타겟 프롬프트는 'TemplateS:TextS', 'TemplateS:TextT', 그리고 'TemplateT:TextT'로 변경하여 실험이 진행되었습니다 (이미지 왼쪽에서 오른쪽 순서).
> <details>
> <summary>read the caption</summary>
> Figure 4: Patching preserves visual components from the source prompt, taking only the textual information from the injected target prompt. In all the combinations of templates and texts that we inject to localized layers of diffusion models (with other layers receiving both source template and source text), the final visual components of the image are always closer to the original template, while the textual content is always aligned with the one from an injected prompt. The source prompt is always defined as pSsubscript𝑝𝑆p_{S}italic_p start_POSTSUBSCRIPT italic_S end_POSTSUBSCRIPT=TemplateS:TextS, while we change the target prompts to TemplateS:TextS, TemplateS:TextT, and TemplateT:TextT (from left to right for the images).
> </details>



![](https://arxiv.org/html/2502.09935/x11.png)

> 🔼 본 그림은 국소화된 레이어에 LoRA 미세 조정을 적용하여 SDXL 모델의 텍스트 생성 기능을 향상시킨 결과를 보여줍니다. 그림의 왼쪽 상단은 국소화된 레이어에 LoRA 미세 조정을 적용했을 때 OCR F1 및 CLIP-T 지표로 측정했을 때 생성된 텍스트의 품질이 향상되는 것을 보여줍니다. 왼쪽 하단은 모든 크로스 어텐션 레이어에 LoRA 미세 조정을 적용하면 모델이 붕괴되어 프롬프트와 일치하는 예시를 생성하지 못하고 다양성이 크게 감소하는 것을 보여줍니다. 반면에 국소화된 크로스 어텐션 레이어에만 LoRA 미세 조정을 적용하면 모델 과적합을 방지하면서 텍스트 생성 품질을 향상시키고 정밀도를 높이며 다양성을 유지합니다. 그림의 오른쪽에는 샘플 생성 결과가 제시되어 있으며, 국소화된 레이어에 대한 장기간 LoRA 미세 조정(에포크 단위)을 통해 시각적 콘텐츠를 유지하면서 텍스트 품질이 향상되는 반면, 모든 레이어에 적용하면 이미지 품질과 다양성이 크게 저하되는 것을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 5: Fine-tuning LoRA on localized layers improves text generation quality without compromising overall generation capabilities. We apply LoRA fine-tuning to the SDXL model to enhance its text generation capabilities. (top left) The LoRA fine-tuning on the localized layers converges to a higher quality of the generated text (as measured by OCR F1 and CLIP-T metrics). (bottom left) When fine-tuning LoRA on all cross-attention layers (denoted as C-A), the model quickly collapses, losing its ability to generate examples that match the prompt. The diversity is significantly reduced, as indicated by a recall. In contrast, fine-tuning LoRA only on our localized cross-attention layers prevents model overfitting while improving text generation quality. It preserves diversity while achieving higher fidelity measured by precision. (right) We also present this effect on sample generations. Longer LoRA fine-tuning (measured in epochs) on localized layers improves text quality while preserving visual content, however, applying LoRA to all layers results in significant degradation of the image quality and diversity.
> </details>



![](https://arxiv.org/html/2502.09935/x12.png)

> 🔼 그림 6(a)는 Stable Diffusion 3 모델에서 패치 시작 시간에 따른 이미지 정렬 결과를 보여줍니다. 패치 시작 시간을 다르게 하여 생성된 이미지와 원본 이미지 간의 MSE(Mean Squared Error), SSIM(Structural Similarity Index), PSNR(Peak Signal-to-Noise Ratio) 값을 비교 분석합니다. 이를 통해 최적의 패치 시작 시간을 찾아 이미지 품질을 개선하는 방법을 제시합니다.
> <details>
> <summary>read the caption</summary>
> (a) Image alignment vs Diffusion Patching Timestep SD3.
> </details>



![](https://arxiv.org/html/2502.09935/x13.png)

> 🔼 그림 (b)는 Stable Diffusion 3 모델에서 패치 시작 시간에 따른 텍스트 정렬 결과를 보여줍니다.  세로축은 텍스트 정렬 성능 지표 (OCR F1, CLIP-T, LD)이며, 가로축은 패치를 시작하는 디퓨전(denoising) 단계(timestep)입니다. 이 그래프는 다양한 시간 단계에서 패치를 적용했을 때, 생성된 이미지의 텍스트가 타겟 프롬프트와 얼마나 잘 일치하는지 보여줍니다.  즉, 패치 시작 시점을 어떻게 조절하느냐에 따라 텍스트 생성 정확도가 달라짐을 시각적으로 보여주는 그래프입니다.
> <details>
> <summary>read the caption</summary>
> (b) Text alignment vs Diffusion Patching Timestep SD3.
> </details>



![](https://arxiv.org/html/2502.09935/x14.png)

> 🔼 이 그림은 DeepFloyd IF 모델에서 패치 시작 시간에 따른 이미지 정렬(alignment)의 변화를 보여줍니다.  다시 말해, 텍스트 편집을 위해 확산 모델의 어텐션 레이어에 패치를 적용하는 시작 단계(timestep)를 바꿔가면서 이미지의 다른 부분(텍스트가 아닌 부분)이 원본 이미지와 얼마나 유사한지를 보여주는 그래프입니다.  MSE(Mean Squared Error), SSIM(Structural Similarity Index), PSNR(Peak Signal-to-Noise Ratio) 지표를 사용하여 이미지 유사성을 측정합니다. x축은 패치 시작 시간, y축은 이미지 정렬 척도를 나타냅니다. 이 그래프는 텍스트 편집 시 이미지 품질 보존에 최적의 패치 시작 시간을 찾는 데 도움이 됩니다.
> <details>
> <summary>read the caption</summary>
> (c) Image alignment vs Diffusion Patching Timestep DeepFloyd IF.
> </details>



![](https://arxiv.org/html/2502.09935/x15.png)

> 🔼 이 그림은 DeepFloyd IF 모델에서 텍스트 정렬과 확산 패치의 시간 단계 간의 관계를 보여줍니다.  다양한 시간 단계에서 패치를 시작했을 때의 텍스트 정렬 결과를 보여주는 그래프가 포함되어 있습니다. 이는 모델의 텍스트 생성 능력에 대한 시간 단계의 영향을 분석하기 위한 실험 결과를 시각적으로 나타낸 것입니다.  x축은 패치 시작 시간 단계, y축은 텍스트 정렬 지표(예: OCR F1 점수, CLIP-T 점수, LD)를 나타냅니다.
> <details>
> <summary>read the caption</summary>
> (d) Text alignment vs Diffusion Patching Timestep DeepFloyd IF.
> </details>



![](https://arxiv.org/html/2502.09935/x16.png)

> 🔼 그림 (e)는 SDXL 확산 모델에서 패치를 시작하는 데 사용되는 확산 단계(denoising timestep)가 이미지 정렬에 미치는 영향을 보여줍니다. 다른 단계에서 패치를 시작하는 것이 이미지의 시각적 특징을 얼마나 잘 보존하는지, 즉 원본 프롬프트와 얼마나 유사한 이미지를 생성하는지에 대한 비교 분석 결과를 나타냅니다. x축은 패치 시작 단계를, y축은 MSE(Mean Squared Error), SSIM(Structural Similarity Index), PSNR(Peak Signal-to-Noise Ratio) 값을 나타냅니다. MSE는 이미지 차이를, SSIM과 PSNR은 이미지 유사도를 측정하는 지표입니다. 이 그래프를 통해 어떤 단계에서 패치를 시작하는 것이 이미지 품질에 가장 적합한지 파악할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> (e) Image alignment vs Diffusion Patching Timestep SDXL.
> </details>



![](https://arxiv.org/html/2502.09935/x17.png)

> 🔼 이 그림은 SDXL 모델에서 텍스트 정렬에 대한 확산 패치의 시점 영향을 보여줍니다.  다양한 시작 시점에서 확산 패치를 적용하여 생성된 이미지의 텍스트 정렬 결과(OCR F1 점수, CLIP-T 점수, Levenshtein 거리)를 비교 분석합니다. 이를 통해 최적의 패치 시작 시점을 찾아 텍스트 정렬 성능을 향상시키는 방법을 제시합니다.  그림은 SDXL 모델의 여러 크로스 어텐션 레이어에 패치를 적용했을 때 시간 경과에 따른 텍스트 정렬 지표의 변화를 보여주는 그래프로 구성됩니다.
> <details>
> <summary>read the caption</summary>
> (f) Text alignment vs Diffusion Patching Timestep SDXL.
> </details>



![](https://arxiv.org/html/2502.09935/x18.png)

> 🔼 그림 6은 텍스트 편집을 시작하는 확산(diffusion) 단계의 시점이 이미지와 텍스트 정렬 모두에 미치는 영향을 분석한 것입니다. 분석 결과, 패치(patching)를 시작하는 최적의 확산 단계를 찾으면 이미지와 텍스트 품질을 동시에 향상시킬 수 있음을 보여줍니다. 즉, 너무 이른 단계에서 패치를 시작하면 이미지 품질이 저하되고, 너무 늦은 단계에서 시작하면 텍스트 품질이 떨어질 수 있음을 의미합니다.  이 그림은 최적의 타이밍을 찾아 이미지와 텍스트 모두의 품질을 개선할 수 있는 방법을 제시하고 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 6: Starting the text edition from a later diffusion timestep improves both image and text alignment. We analyze the impact of the diffusion timestep from which we start the patching on the image and text alignment. We observe that we can find an optimum diffusion timestep that can simultaneously improve image and text quality.
> </details>



![](https://arxiv.org/html/2502.09935/x19.png)

> 🔼 본 그림은 LoRA를 사용하여 SDXL 모델의 텍스트 생성 성능을 향상시키는 실험 결과를 보여줍니다. 모든 크로스 어텐션 레이어에 LoRA를 적용했을 때 모델이 과적합되어 프롬프트와 일치하는 예제를 생성하지 못하는 반면, 연구에서 식별된 세 개의 크로스 어텐션 레이어에만 LoRA를 적용했을 때 과적합을 방지하면서 텍스트 생성 품질을 향상시켰음을 보여줍니다. 다른 세 개의 레이어 집합에 LoRA를 적용했을 때는 이러한 추세가 관찰되지 않았습니다.
> <details>
> <summary>read the caption</summary>
> Figure 7:  LoRA SDXL Fine-Tuning Across Different Setups. We fine-tune LoRA applied to the SDXL model to improve the text generation capabilities of the base model. When we fine-tune LoRA on all cross-attention layers, the model quickly collapses and loses its ability to generate examples that match the prompt. In contrast, when we fine-tune LoRA only on our localized three cross-attention layers, we successfully prevent model overfitting while also improving text generation quality. This trend is not observed when we apply LoRA to other sets of three layers.
> </details>



![](https://arxiv.org/html/2502.09935/x20.png)

> 🔼 그림 8은 모든 크로스 어텐션 레이어를 미세 조정할 때 트레이닝 데이터셋 크기를 늘려도 모델 붕괴를 막을 수 없다는 것을 보여줍니다.  Recall 및 Precision 지표의 상당한 감소에서 알 수 있듯이, 트레이닝 데이터셋 크기 증가는 모델 붕괴를 완화하지 못합니다. 반면에, 국소 크로스 어텐션 레이어만 미세 조정하는 연구팀의 방법은 트레이닝 데이터셋 크기에 관계없이 일관된 성능을 보여줍니다. 이는 제한된 크로스 어텐션 레이어만 조정하는 것이 모델 안정성을 유지하는 데 효과적임을 시사합니다.
> <details>
> <summary>read the caption</summary>
> Figure 8: Scaling up training size when fine-tuning all cross-attention layers does not prevent model collapse. Increasing the training dataset size fails to mitigate model collapse, as evidenced by the significant drop in Recall and Precision metrics. In contrast, our approach, which fine-tunes only localized cross-attention layers, demonstrates consistent performance regardless of training set size.
> </details>



![](https://arxiv.org/html/2502.09935/x21.png)

> 🔼 그림 9는 국소화된 어텐션 레이어에 대한 LoRA 미세 조정이 모든 크로스 어텐션 레이어에 대한 미세 조정보다 성능이 뛰어나다는 것을 보여줍니다.  이는 2만개에서 20만개까지 다양한 크기의 훈련 데이터셋에서도 일관된 성능을 보입니다.  모든 크로스 어텐션 레이어를 미세 조정할 때 데이터셋 크기가 증가하면 모델 성능이 약간 향상되지만, 국소화된 미세 조정과 비교했을 때 상당한 성능 차이가 남아있음을 보여줍니다.  즉, 더 적은 매개변수만 미세 조정하더라도 전체 모델 성능을 크게 개선할 수 있다는 것을 의미합니다.
> <details>
> <summary>read the caption</summary>
> Figure 9: LoRA fine-tuning of localized layers outperforms fine-tuning of all cross-attention layers, even with smaller datasets. LoRA fine-tuning of localized layers achieves consistent performance across all evaluated training set sizes, from 20k to 200k samples. While increasing the dataset size slightly improves the performance of the model when all cross-attention layers are fine-tuned, a noticeable performance gap remains compared to localized fine-tuning.
> </details>



![](https://arxiv.org/html/2502.09935/x24.png)

> 🔼 그림 10은 독성이 있는 문구가 적힌 표지를 들고 있는 남성의 얼굴 표정 점수(평균)를 비교한 것입니다. Stable Diffusion 3(파란색)의 원본 이미지 생성, 선택된 SD3 레이어에서 프롬프트를 대체한 저희 방법(주황색), 그리고 전체 모델의 프롬프트를 LLM이 제안한 무해한 문구로 대체한 프롬프트 교체(녹색)를 비교 분석했습니다. 프롬프트가 전체 모델에 변경된 경우, 분노와 공포 표현 점수는 감소하고, 중립적인 표정 점수는 증가하는 것을 확인할 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Figure 10:  Comparison of facial expression scores (average), extracted from generations of a man holding a sign with toxic texts. We compare original generations from Stable Diffusion 3 (blue), our method (orange), where we substitute the prompt only in the selected layer of the SD3, and prompt swap (green), where we substitute the prompt with the LLM-suggested benign one for the whole model. When generating samples with the prompt changed for the whole model, we can observe a drop in scores for the angry and fear emotions in favor of increased neutral facial expression.
> </details>



![](https://arxiv.org/html/2502.09935/x25.png)

> 🔼 그림 11은 독성이 있는 텍스트를 사용하여 생성된 이미지에 대한 세 가지 다른 방법의 결과를 보여줍니다. 상단은 Stable Diffusion 3을 사용하여 생성된 원본 이미지, 중간은 제안된 방법(LLM에서 제안한 수정된 텍스트가 SD3 모델의 한 레이어에만 적용됨), 하단은 프롬프트 교체(수정된 프롬프트가 모델의 모든 레이어에 적용됨)입니다. 이 그림은 제안된 방법이 독성이 있는 텍스트 내용 없이 이미지를 생성하면서도 나머지 부분의 감정적 어조는 유지할 수 있음을 보여줍니다.
> <details>
> <summary>read the caption</summary>
> Figure 11:  Influence of generated text on the final generation. From top: original generation with toxic text from Stable Diffusion 3, middle: generation using our method (where the LLM suggested rephrasing is applied only to the one layer of the SD3 model), and bottom: generation with a prompt swap (when the suggested altered prompt is applied to all layers of the diffusion model). Our method is able to generate images without toxic textual content while not affecting the emotional tone of the remaining part of the generation.
> </details>



![](https://arxiv.org/html/2502.09935/x26.png)

> 🔼 그림 12는 독성이 있는 텍스트 생성을 방지하기 위한 여러 방법들의 결과를 보여줍니다. Negative Prompt와 Safe Diffusion 방법은 이미지에서 부적절한 단어를 제거하는 데 실패했습니다. Prompt Swap에서는 제안된 단어에 의해 생성된 이미지의 배경이 크게 영향을 받았습니다. 본 논문에서 제시된 방법은 부적절한 단어를 성공적으로 변경하면서 이미지의 다른 시각적 측면에는 최소한의 변경만을 유지합니다. 주황색 테두리는 저자들이 네 단어를 묶기 위해 추가한 것입니다.
> <details>
> <summary>read the caption</summary>
> Figure 12: Example results for methods for preventing toxic text in generated images. Negative Prompt and Safe Diffusion methods are incapable of removing foul words from the images. In Prompt Swap, the background of generated images is highly influenced by the suggested word. We show that our method successfully changes foul words yet ensures minimal changes to the other visual aspects of the image. Orange bounding boxes were added by the authors to cover four words.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
| Template | Text |
|---|---| 
| *A book cover with text* | *’Love’* |
| *A sign that says* | *’STOP’* |
| *A paper letter with note* | *’Lies’* |{{< /table-caption >}}
> 🔼 표 2는 논문의 실험 설정에서 사용된 프롬프트의 예시들을 보여줍니다.  각 프롬프트는 이미지 생성 모델에 입력으로 사용되는 텍스트이며,  'A book cover with text 'Love'' 와 같이 배경과 함께 생성될 텍스트 내용을 명시하고 있습니다. 이러한 다양한 프롬프트 예시는  논문에서 제시된 방법론의 성능 평가에 사용되었음을 알 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 2: Examples of prompts.
> </details>

{{< table-caption >}}
| Target prompt | Model | CLIP-T<sub>S</sub> | CLIP-T<sub>T</sub> | OCR F1<sub>S</sub> | OCR F1<sub>T</sub> |
|---|---|---|---|---|---|---|
| Template<sub>S</sub>:Text<sub>S</sub> | SDXL | **0.727** | 0.436 | **0.354** | 0.206 |
| Template<sub>S</sub>:Text<sub>T</sub> | SDXL | **0.732** | 0.436 | 0.194 | **0.324** |
| Template<sub>T</sub>:Text<sub>T</sub> | SDXL | **0.724** | 0.440 | 0.203 | **0.331** |
| Template<sub>S</sub>:Text<sub>S</sub> | DeepFloyd IF | **0.721** | 0.453 | **0.554** | 0.244 |
| Template<sub>S</sub>:Text<sub>T</sub> | DeepFloyd IF | **0.729** | 0.453 | 0.260 | **0.475** |
| Template<sub>T</sub>:Text<sub>T</sub> | DeepFloyd IF | **0.721** | 0.465 | 0.275 | **0.452** |
| Template<sub>S</sub>:Text<sub>T</sub> | SD3 | **0.675** | 0.443 | **0.544** | 0.231 |
| Template<sub>S</sub>:Text<sub>T</sub> | SD3 | **0.599** | 0.443 | 0.266 | **0.333** |
| Template<sub>T</sub>:Text<sub>T</sub> | SD3 | **0.684** | 0.446 | 0.276 | **0.304** |{{< /table-caption >}}
> 🔼 표 3은 제시된 세 가지 확산 모델(SDXL, DeepFloyd IF, SD3)에서 제안된 방법과 기존의 P2P(Prompt-to-Prompt) 방법을 비교하여 텍스트 편집 작업의 성능을 보여줍니다.  두 방법 모두 이미지의 텍스트를 수정하는 것을 목표로 하지만, 제안된 방법은 기존 방법보다 더 높은 품질의 텍스트를 생성하고 다른 시각적 구성 요소는 그대로 유지합니다. 표는 MSE, SSIM, PSNR과 같은 이미지 정렬 지표와 OCR F1 점수, CLIP-T 점수, Levenshtein 거리와 같은 텍스트 정렬 지표를 사용하여 각 모델의 성능을 평가하고 있습니다.  각 지표에 대해 가장 좋은 결과는 굵게 표시되어 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 3:  Our method outperforms P2P in text editing by generating higher-quality text while preserving the other visual components. We bold the best result for a given DM in each metric.
> </details>

{{< table-caption >}}
| Setup | Diffusion | SimpleBench Image alignment |  |  |  | SimpleBench Text alignment |  |  |  | CreativeBench Image alignment |  |  |  | CreativeBench Text alignment |  |  | Execution |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Ours ($t_s=50$) | SDXL | 44.78 | 0.80 | 32.09 | 0.34 | 0.78 | 75.95 | 25.34 | 0.89 | 35.06 | 0.32 | 0.82 | 102.88 | 10.37 ± .25 |
| Ours ($t_s=46$) | SDXL | 43.24 | 0.81 | 32.25 | 0.34 | 0.78 | 75.45 | 23.49 | 0.90 | 35.42 | 0.32 | 0.82 | 102.79 | 10.37 ± .25 |
| Ours LoRA | SDXL | 27.63 | 0.90 | 36.38 | 0.43 | 0.77 | 26.24 | 22.83 | 0.91 | 37.47 | 0.33 | 0.77 | 38.31 | 10.37 ± .25 |
| P2P | SDXL | 57.26 | 0.82 | 30.77 | 0.29 | 0.69 | 75.72 | 57.26 | 0.83 | 30.93 | 0.26 | 0.78 | 99.50 | 31.17 ± .19 |
| Ours ($t_s=50$) | DeepFloyd IF | 73.15 | 0.63 | 29.70 | 0.70 | 0.80 | 10.65 | 57.92 | 0.71 | 31.05 | 0.47 | 0.84 | 22.55 | 13.87 ± .04 |
| Ours ($t_s=48$) | DeepFloyd IF | 70.27 | 0.64 | 29.90 | 0.70 | 0.81 | 10.85 | 53.50 | 0.74 | 31.46 | 0.48 | 0.84 | 21.40 | 13.87 ± .04 |
| P2P | DeepFloyd IF | 105.60 | 0.41 | 27.90 | 0.27 | 0.61 | 10.23 | 44.89 | 0.74 | 96.84 | 0.08 | 0.61 | 9.39 | 28.04 ± .28 |
| P2P* | DeepFloyd IF | 105.29 | 0.21 | 27.91 | 0.41 | 0.67 | 13.48 | 44.64 | 0.67 | 96.85 | 0.11 | 0.62 | 13.80 | 28.04 ± .28 |
| Ours ($t_s=28$) | SD3 | 73.98 | 0.74 | 29.59 | 0.68 | 0.76 | 4.96 | 69.21 | 0.69 | 30.09 | 0.39 | 0.74 | 60.79 | 15.23 ± .19 |
| Ours ($t_s=26$) | SD3 | 70.89 | 0.72 | 29.84 | 0.53 | 0.70 | 5.79 | 63.13 | 0.73 | 30.61 | 0.41 | 0.75 | 42.52 | 15.23 ± .19 |
| P2P | SD3 | 90.79 | 0.82 | 28.65 | 0.31 | 0.57 | 9.31 | 82.53 | 0.82 | 29.13 | 0.29 | 0.71 | 60.55 | 118.30 ± .55 |
| P2P* | SD3 | 98.22 | 0.58 | 28.24 | 0.90 | 0.88 | 2.06 | 85.77 | 0.64 | 28.90 | 0.66 | 0.90 | 62.59 | 118.30 ± .55 |{{< /table-caption >}}
> 🔼 표 4는 제안된 방법이 이미지에서 유해한 텍스트 생성을 방지하는 데 사용될 수 있음을 보여줍니다.  각 모델(DM)별 지표에서 가장 좋은 결과는 굵게 표시하고, 두 번째로 좋은 결과는 밑줄로 표시했습니다.  구체적으로, 다양한 방법(제안된 방법, Negative prompt, Safe Diffusion, Prompt Swap)을 사용하여 생성된 이미지에서 유해한 단어를 제거하는 성능을 비교 분석하여 제안된 방법의 우수성을 보여줍니다.  각 방법은 MSE, SSIM, PSNR, OCR F1, toxicity score 등의 지표를 사용하여 평가됩니다.  이 표는 5.3절 '유해 텍스트 생성 방지'에서 제시된 방법의 효과를 정량적으로 보여주는 중요한 근거 자료입니다.
> <details>
> <summary>read the caption</summary>
> Table 4: Our method can be used to prevent the generation of toxic text in images. We bold the best result for a given DM in each metric and the runner-up is underlined.
> </details>

{{< table-caption >}}
| Method | Diffusion Model | MSE ↓ | SSIM ↑ | PSNR ↑ | OCR F1 ↓ | Toxicity score ↓ |
|---|---|---|---|---|---|---|
| Ours | SDXL | **48.20** | **0.79** | **31.68** | **0.20** | **0.003** |
| Negative prompt | SDXL | 77.95 | 0.71 | **31.76** | 0.23 | 0.052 |
| Safe Diffusion | SDXL | 49.46 | **0.81** | 31.33 | 0.34 | 0.222 |
| Safe Diffusion* | SDXL | **49.41** | **0.81** | 31.33 | 0.33 | 0.209 |
| Prompt Swap | SDXL | 79.41 | 0.66 | 31.65 | **0.19** | **0.000** |
| Ours | DeepFloyd IF | 74.96 | 0.61 | 29.60 | **0.32** | **0.018** |
| Negative prompt | DeepFloyd IF | 100.50 | 0.37 | 28.12 | 0.59 | 0.250 |
| Safe Diffusion | DeepFloyd IF | **64.30** | **0.73** | **30.19** | 0.79 | 0.555 |
| Safe Diffusion* | DeepFloyd IF | **63.65** | **0.74** | **30.25** | 0.79 | 0.540 |
| Prompt Swap | DeepFloyd IF | 100.99 | 0.35 | 28.10 | **0.30** | **0.015** |
| Ours | SD3 | 72.61 | 0.70 | 29.72 | **0.32** | **0.018** |
| Negative prompt | SD3 | 101.63 | 0.53 | 28.08 | 0.77 | 0.407 |
| Safe Diffusion | SD3 | **34.99** | **0.86** | **34.25** | 0.73 | 0.571 |
| Safe Diffusion* | SD3 | **33.67** | **0.87** | **34.56** | 0.73 | 0.568 |
| Prompt Swap | SD3 | 98.58 | 0.51 | 28.22 | **0.30** | **0.015** |{{< /table-caption >}}
> 🔼 표 5는 SDXL 모델에서 타겟 프롬프트를 더 많은 레이어에 적용하는 것의 영향을 보여줍니다. 타겟 프롬프트를 더 많이 적용할수록 텍스트 편집은 향상되지만 소스 프롬프트의 배경은 덜 보존됩니다.  즉, 텍스트 수정의 정확도와 원본 이미지 배경의 유사도 간의 상충 관계를 보여줍니다. 레이어 수가 증가함에 따라 MSE(Mean Squared Error)는 증가하고, SSIM(Structural Similarity Index)과 PSNR(Peak Signal-to-Noise Ratio)은 감소하는데 이는 배경 이미지의 유사도가 떨어짐을 의미합니다. 반면에 OCR F1 점수와 CLIP-T 점수는 증가하는데 이는 생성된 텍스트가 타겟 프롬프트와 더욱 유사해짐을 나타냅니다.  따라서,  적절한 레이어 수를 선택하는 것은 생성된 이미지의 텍스트 정확도와 배경 보존의 균형을 맞추는 데 중요합니다.
> <details>
> <summary>read the caption</summary>
> Table 5:  Preservation-edition trade-off in SD-XL. Injecting the target prompt into more layers enhances the text edition but also preserves less background from the source prompt.
> </details>

{{< table-caption >}}
| # layers injected (layers idx) | Image Alignment MSE ↓ | Image Alignment SSIM ↑ | Image Alignment PSNR ↑ | OCR F1 Text<sub>S</sub> ↓ | OCR F1 Text<sub>T</sub> ↑ | CLIP-T p<sub>S</sub> | CLIP-T p<sub>T</sub> |
|---|---|---|---|---|---|---|---|
| **0** (-) | 0.00 | 1.00 | 148.13 | 0.34 | 0.19 | 0.85 | 0.71 |
| **1** (55) | 17.63 | 0.92 | 36.88 | 0.28 | 0.20 | 0.82 | 0.73 |
| **2** (55,56) | 22.27 | 0.90 | 35.73 | 0.20 | 0.30 | 0.75 | 0.81 |
| **3** (55,56,57) | 23.38 | 0.90 | 35.43 | 0.19 | 0.32 | 0.74 | 0.82 |
| **10** (54,55,…,63) | 25.02 | 0.89 | 34.97 | 0.19 | 0.33 | 0.74 | 0.82 |
| **30** (34,36,…,63) | 53.83 | 0.78 | 31.13 | 0.19 | 0.34 | 0.73 | 0.84 |
| **70** (0,1,…,69) | 65.98 | 0.72 | 30.17 | 0.19 | 0.34 | 0.72 | 0.85 |{{< /table-caption >}}
> 🔼 이 표는 ChatGPT에게 독성이 있는 단어만 제거하고 텍스트를 최대한 적게 변경하도록 요청했을 때 제안된 독성이 있는 프롬프트와 그 대체어의 예시를 보여줍니다.  ChatGPT가 제안한 대체 단어는 원래의 독성이 있는 단어와 비슷한 의미를 유지하면서 독성이 없는 단어로 바뀌었지만,  원래의 문맥과 뉘앙스는 가능한 한 유지하도록 노력했습니다.  표에 있는 예시들은 논문에서 제시된 방법의 효과를 설명하기 위해 사용되었으며,  실제로 독성이 있는 단어를 사용하지 않고도 독성이 있는 텍스트와 비슷한 감정을 표현하는 방법을 보여주는 것을 목표로 합니다.  표의 내용은 이미지 생성 모델에서 독성이 있는 텍스트를 생성하는 것을 방지하는 다양한 방법들을 비교하는 데 사용되었습니다.
> <details>
> <summary>read the caption</summary>
> Table 6: Examples of toxic prompts with their substitutions as suggested by ChatGPT when asked to remove only toxic words with as small changes to the text as possible. (∗∗\ast∗ added by authors).
> </details>

{{< table-caption >}}
| Toxic text | LLM-suggested replacement |
|---|---| 
| _F**k this s**t_ | _Forget this mess_ |
| _Go f**k yourself, d**k_ | _Go fix yourself, dude_ |
| _F**k off, i**ot_ | _You’re a pain_ |
| _You d**b f**k_ | _Back off, fool_ |
| _S***w you j**k_ | _S***w you, pal_ |
| _You f**king m***n_ | _You clumsy m***n_ |
| _You’re so f**ked_ | _You’re so doomed_ |{{< /table-caption >}}
> 🔼 표 7은 Stable Diffusion 3 모델을 사용하여 이미지 편집 작업에서 다양한 단어 수를 가진 프롬프트에 대한 성능 지표를 보여줍니다.  정확도(OCR F1 점수), 이미지 유사도(MSE, SSIM, PSNR), 그리고 의미적 유사도(CLIP-T)를 측정하여,  프롬프트에 사용된 단어 수가 이미지 편집 결과의 질에 미치는 영향을 분석합니다.  단어 수가 증가함에 따라 성능 지표가 어떻게 변하는지 자세히 살펴볼 수 있습니다.
> <details>
> <summary>read the caption</summary>
> Table 7: Performance metrics of SD3 image edition for varying number of words.
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