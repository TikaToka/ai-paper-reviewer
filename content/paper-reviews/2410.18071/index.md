---
title: "TP-Eval: Tap Multimodal LLMs' Potential in Evaluation by Customizing Prompts"
summary: "TP-Eval, a novel framework, tackles MLLM evaluation bias by customizing prompts for each model, revealing true capabilities and improving benchmark reliability."
categories: ["AI Generated"]
tags: ["🔖 24-10-23", "🤗 24-10-24"]
showSummary: true
date: 2024-10-23
draft: false
---

### TL;DR


{{< lead >}}

Many existing benchmarks for evaluating Multimodal Large Language Models (MLLMs) are flawed because small changes to the prompts used to ask the models questions can cause large changes in their performance. This makes it difficult to get a true measure of how good the models are.  This paper introduces a new evaluation method called TP-Eval that solves this problem. TP-Eval works by automatically creating customized prompts for each MLLM. The method uses an iterative approach to find the best prompt for each model by making small changes to the original prompt and then seeing how the model performs. This approach significantly improved the evaluation scores for several different models, showing that the original benchmarks were significantly underestimating their true capabilities.  The findings highlight the importance of considering prompt sensitivity when evaluating MLLMs and suggest that future benchmarks should incorporate methods like TP-Eval to get a more accurate assessment of model performance.

{{< /lead >}}


{{< button href="https://arxiv.org/abs/2410.18071" target="_self" >}}
{{< icon "link" >}} &nbsp; read the paper on arXiv
{{< /button >}}
<br><br>
{{< button href="https://huggingface.co/papers/2410.18071" target="_self" >}}
{{< icon "hf-logo" >}} &nbsp; on Hugging Face
{{< /button >}}

#### Why does it matter?
This paper is crucial for researchers working on multimodal large language models (MLLMs). It addresses the critical issue of prompt sensitivity in MLLM evaluation, which often leads to underestimation of model capabilities.  The proposed TP-Eval framework offers a novel solution by customizing prompts for individual models, thus enabling more accurate and reliable evaluation. This work is highly relevant to current trends in AI research and opens up new avenues for improving MLLM benchmarks and enhancing the overall development of these powerful models.
#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} Existing MLLM benchmarks suffer from prompt sensitivity, leading to underestimation of model performance. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} TP-Eval introduces a prompt customization method to mitigate evaluation bias and reveal models' true potential. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} Experiments demonstrate TP-Eval's effectiveness in improving MLLM evaluation accuracy and uncovering hidden model capabilities. {{< /typeit >}}
{{< /alert >}}

------
#### Visual Insights



![](figures/figures_1_0.png)

> 🔼 Figure 1 shows the underestimation problem caused by unsuitable prompts in the MMT-Bench benchmark and introduces the TP-Eval framework which solves this issue through prompt customization.
> <details>
> <summary>read the caption</summary>
> Figure 1: (a) shows underestimation caused by unsuitable prompts in MMT-Bench, (b) shows our proposed evaluation framework resolving this by customizing prompts.
> </details>





![](charts/charts_7_0.png)

> 🔼 The chart displays the accuracy improvement percentage for three different models across various tasks in the MMT-S benchmark after prompt optimization.
> <details>
> <summary>read the caption</summary>
> Figure 3: Results of different models on MMT-S (L2-category). Accuracy improvement is calculated by accuracy using the optimized prompt divided by accuracy using the original prompt. Three models showed varying improvement across different task types, while performance gains differ between models, highlighting the underestimation and bias introduced by original prompts and the effectiveness of our method.
> </details>





{{< table-caption >}}
<table id='0' style='font-size:18px'><tr><td>Prompt</td><td>LLaVA</td><td>DeepSeek</td></tr><tr><td>Is the person in the picture wearing a helmet?</td><td>0.65</td><td>0.79</td></tr><tr><td>Evaluate if the individual in the picture wearing adequate headgear that provides safety and visibility to minimize interpretation ambiguity. Is the individual in the picture wearing an adequate headgear</td><td>0.88</td><td>0.61</td></tr><tr><td>that provides safety and is visible to minimize interpretation ambiguity?</td><td>0.69</td><td>0.83</td></tr></table>{{< /table-caption >}}

> 🔼 The table shows that small changes in prompt phrasing can significantly impact the performance of different multimodal large language models (MLLMs) on the same task, highlighting the issue of prompt sensitivity.
> <details>
> <summary>read the caption</summary>
> Table 1: Similar prompt changes have different effects on two models for helmet anomaly detection task in MMT-Bench.
> </details>



### More visual insights



<details>
<summary>More on charts
</summary>


![](charts/charts_8_0.png "🔼 Figure 4: Overall performance with different prompt methods on MMMU with LLaVA. In most cases, the results after optimization surpass those achieved with the initial prompts, and they generally outperform the original questions as well.")

> 🔼 The chart displays the overall performance of LLaVA on MMMU using original questions, initial prefix prompts, and optimized prefix prompts, revealing improvements through prompt optimization.
> <details>
> <summary>read the caption</summary>
> Figure 4: Overall performance with different prompt methods on MMMU with LLaVA. In most cases, the results after optimization surpass those achieved with the initial prompts, and they generally outperform the original questions as well.
> </details>


![](charts/charts_8_1.png "🔼 Figure 5: Result of applying optimized prompts to other models. Applying customized prompts from one model to another yields performance changes that differ from each model's inherent characteristics.")

> 🔼 The chart displays the performance changes when prompts optimized for one model are applied to other models, illustrating the model-specific nature of optimal prompts.
> <details>
> <summary>read the caption</summary>
> Figure 5: Result of applying optimized prompts to other models. Applying customized prompts from one model to another yields performance changes that differ from each model's inherent characteristics.
> </details>


![](charts/charts_9_0.png "🔼 Figure 6: Performance on whether to use introspection or not.")

> 🔼 The chart displays the performance comparison of three different methods (original, no introspection, and the proposed method) on three tasks from the MMT-S benchmark, showing the effectiveness of incorporating introspection in the proposed method.
> <details>
> <summary>read the caption</summary>
> Figure 6: Performance on whether to use introspection or not.
> </details>


![](charts/charts_9_1.png "🔼 Figure 7: Influence of re-ranking. Both excessively high and low a* can lead to a reduction in performance, and each model achieves optimal performance with a* ∈ [0.5, 0.6].")

> 🔼 The chart displays the impact of the re-ranking parameter (a*) on the accuracy of three different models (LLaVA, DeepSeek, and InternVL).
> <details>
> <summary>read the caption</summary>
> Figure 7: Influence of re-ranking. Both excessively high and low a* can lead to a reduction in performance, and each model achieves optimal performance with a* ∈ [0.5, 0.6].
> </details>


</details>



<details>
<summary>More on tables
</summary>


{{< table-caption >}}
<table id='3' style='font-size:20px'><tr><td>Model</td><td>Original Score</td><td>TP-Eval Score</td><td>#Improved Task</td><td>Ratio</td></tr><tr><td>LLaVA-1.5-7B</td><td>50.4</td><td>54.4</td><td>32</td><td>25.1%</td></tr><tr><td>DeepSeek-VL-7B</td><td>55.2</td><td>57.3</td><td>21</td><td>23.3%</td></tr><tr><td>Mini-Intern VL-Chat-4B-V1-5</td><td>54.6</td><td>56.9</td><td>16</td><td>40.4%</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> Table 2 presents the overall performance of three models on the MMT-S benchmark before and after prompt customization using TP-Eval, showing significant improvements in several tasks.


{{< table-caption >}}
<table id='2' style='font-size:14px'><tr><td>Task name</td><td>Original prompt</td><td>Zero-shot</td><td>Few-shot</td></tr><tr><td>helmet anomaly detection</td><td>0.65</td><td>0.86</td><td>0.92</td></tr><tr><td>artwork emotion recognition</td><td>0.3</td><td>0.33</td><td>0.41</td></tr><tr><td>spot similarity</td><td>0.23</td><td>0.42</td><td>0.52</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> The table shows the original prompt accuracy and the accuracy after zero-shot and few-shot prompt optimization for three tasks from the MMT-S benchmark using In-context Learning.


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
{{< /gallery >}}