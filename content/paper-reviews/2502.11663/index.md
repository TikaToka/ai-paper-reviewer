---
title: "MaskGWM: A Generalizable Driving World Model with Video Mask Reconstruction"
summary: "MaskGWM: 비디오 마스크 재구성을 통한 일반화 가능한 자율 주행 세계 모델"
categories: ["AI Generated", "🤗 Daily Papers"]
tags: ["Computer Vision", "Video Understanding", "🏢 SenseTime Research",]
showSummary: true
date: 2025-02-17
draft: false
---

<br>

{{< keywordList >}}
{{< keyword icon="fingerprint" >}} 2502.11663 {{< /keyword >}}
{{< keyword icon="writer" >}} Jingcheng Ni et el. {{< /keyword >}}
 
{{< keyword >}} 🤗 2025-02-24 {{< /keyword >}}
 
{{< /keywordList >}}

{{< button href="https://arxiv.org/abs/2502.11663" target="_self" >}}
↗ arXiv
{{< /button >}}
{{< button href="https://huggingface.co/papers/2502.11663" target="_self" >}}
↗ Hugging Face
{{< /button >}}
{{< button href="https://paperswithcode.com/paper/maskgwm-a-generalizable-driving-world-model" target="_self" >}}
↗ Papers with Code
{{< /button >}}




### TL;DR


{{< lead >}}

기존의 자율 주행 세계 모델은 예측 시간과 일반화 능력에 한계가 있었습니다. **비디오 예측 모델**은 고품질 영상 생성에 뛰어나지만, 예측 시간과 일반화에 제한이 있었습니다. 이러한 문제를 해결하기 위해 본 논문에서는 **MAE 방식의 특징 수준 문맥 학습**과 **생성 손실**을 결합하는 새로운 접근 방식을 제시합니다. 



본 논문에서 제안하는 MaskGWM은 **확장 가능한 DiT 구조**와 **마스크 재구성 작업**을 결합하여 이러한 문제를 해결합니다. **확산 관련 마스크 토큰**과 **공간-시간 도메인 마스크 생성**을 통해 마스크 재구성과 생성 확산 과정 간의 관계를 개선하고, **행 기반 마스크 및 교차 시각 모듈**을 활용하여 성능을 향상시킵니다. 다양한 실험 결과를 통해 MaskGWM이 기존 기술보다 우수한 성능을 보임을 확인했습니다.

{{< /lead >}}


#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} 비디오 마스크 재구성을 결합하여 장기 예측 및 제로샷 일반화 성능을 향상시킨 새로운 세계 모델 MaskGWM을 제시 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} 대규모 데이터셋과 확장 가능한 DiT 아키텍처를 활용하여 자율 주행 모델의 정확도와 일반화 능력 향상 {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} 공간 및 시간적 문맥 정보를 효과적으로 활용하는 새로운 마스크 재구성 전략으로 성능 개선 {{< /typeit >}}
{{< /alert >}}

#### Why does it matter?
본 논문은 **자율 주행 분야의 세계 모델링 연구에 중요한 기여**를 합니다. **장기 예측 및 제로샷 일반화 능력을 향상**시킨 새로운 방법론을 제시함으로써, 향후 연구 방향을 제시하고 **대규모 데이터셋 활용 및 확장성 있는 변환기 아키텍처**의 중요성을 강조합니다.  이는 자율 주행 시스템의 안전성과 신뢰성을 높이는 데 기여하며, **다양한 환경과 상황에 대한 적응력을 높이는 연구**에 중요한 영향을 미칠 것입니다. 또한, 제시된 방법론은 다른 영상 예측 분야에도 응용될 수 있어 **다양한 연구 분야에 파급 효과**를 가지는 중요한 연구 성과입니다.

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