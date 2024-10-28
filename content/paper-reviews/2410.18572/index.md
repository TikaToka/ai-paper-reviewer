---
title: "Taipan: Efficient and Expressive State Space Language Models with Selective Attention"
summary: "Taipan, a hybrid language model, efficiently handles long contexts (up to 1 million tokens) by selectively applying attention, outperforming existing models in both speed and accuracy."
categories: ["AI Generated"]
tags: ["🔖 24-10-24", "🤗 24-10-25"]
showSummary: true
date: 2024-10-24
draft: false
---

### TL;DR


{{< lead >}}

Taipan is a new language model designed to tackle the challenge of processing very long text sequences.  Current top models, like Transformers, struggle with this because their computational cost grows dramatically as the text gets longer.  Taipan solves this by using a clever combination of two techniques. First, it uses a highly efficient model called Mamba-2 that has constant memory usage, meaning its memory needs don't increase with longer texts.  Second, it adds 'Selective Attention Layers' that carefully focus on the most important words and relationships in the text, ignoring less important parts. This means Taipan is both fast and accurate even on incredibly long texts – up to a million words!  Experiments showed Taipan outperforming other state-of-the-art models, particularly on tasks requiring remembering information from earlier parts of a very long text. This is a significant step forward in the field of long-context language modeling.

{{< /lead >}}


{{< button href="https://arxiv.org/abs/2410.18572" target="_self" >}}
{{< icon "link" >}} &nbsp; read the paper on arXiv
{{< /button >}}

{{< button href="https://huggingface.co/papers/2410.18572" target="_self" >}}
{{< icon "hf-logo" >}} &nbsp; on Hugging Face
{{< /button >}}

#### Why does it matter?
This paper is crucial for researchers working on long-context language modeling.  It introduces a novel hybrid architecture that significantly advances the state-of-the-art in handling long sequences, addressing a major limitation of current transformer-based models. The efficient approach and superior performance on memory-intensive tasks open new avenues for research in various NLP applications.
#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} Taipan, a novel hybrid architecture combining Mamba-2 and Selective Attention Layers (SALs), achieves state-of-the-art performance in long-context language modeling. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} SALs efficiently identify and process only crucial tokens requiring long-range interactions, balancing efficiency and accuracy. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} Taipan demonstrates superior performance across various tasks, including memory-intensive ones, with context lengths up to 1 million tokens. {{< /typeit >}}
{{< /alert >}}

------
#### Visual Insights



![](figures/figures_4_0.png)

> 🔼 Figure 2 illustrates the Taipan architecture, a hybrid model combining Mamba-2 with Selective Attention Layers (SALs) for efficient long-context language modeling.
> <details>
> <summary>read the caption</summary>
> Figure 2: An overview of the Taipan architecture.
> </details>





![](charts/charts_2_0.png)

> 🔼 Figure 1 shows the perplexity and latency of Taipan compared to other models across different context lengths and generation lengths, demonstrating Taipan's superior performance and scaling.
> <details>
> <summary>read the caption</summary>
> Figure 1: Model Performance Comparison. a) Perplexity across different context lengths. Lower perplexity indicates better performance. b) Latency comparison of models at various generation lengths. Taipan exhibits significantly lower latency and superior scaling compared to other strong baselines for longer sequences.
> </details>





{{< table-caption >}}
<table id='7' style='font-size:14px'><tr><td>Params & Data</td><td>Model</td><td>Wino.</td><td>PIQA</td><td>Hella.</td><td>ARCE</td><td>ARC�</td><td>OB.</td><td>Truth.</td><td>RACE</td><td>BoolQ</td><td>Avg.</td></tr><tr><td rowspan="4">190M 27B</td><td>Transformer++</td><td>47.1</td><td>60.9</td><td>27.9</td><td>42.2</td><td>20.5</td><td>18.9</td><td>42.9</td><td>25.4</td><td>57.2</td><td>38.1</td></tr><tr><td>Mamba</td><td>49.6</td><td>60.7</td><td>29.3</td><td>45.3</td><td>21.8</td><td>20.6</td><td>40.8</td><td>27.2</td><td>59.3</td><td>39.4</td></tr><tr><td>Jamba</td><td>49.9</td><td>60.3</td><td>29.2</td><td>46.3</td><td>21.4</td><td>18.5</td><td>39.8</td><td>27.4</td><td>58.6</td><td>39.1</td></tr><tr><td>Taipan</td><td>51.0</td><td>62.6</td><td>29.4</td><td>46.7</td><td>20.7</td><td>21.8</td><td>41.1</td><td>26.6</td><td>58.7</td><td>39.9</td></tr><tr><td rowspan="4">450M 100B</td><td>Transformer++</td><td>51.5</td><td>67.6</td><td>42.3</td><td>60.8</td><td>27.7</td><td>33.4</td><td>39.2</td><td>30.5</td><td>54.7</td><td>45.3</td></tr><tr><td>Mamba</td><td>52.7</td><td>68.9</td><td>42.7</td><td>61.4</td><td>27.1</td><td>34.0</td><td>38.5</td><td>29.3</td><td>53.2</td><td>45.3</td></tr><tr><td>Jamba</td><td>53.1</td><td>69.3</td><td>44.3</td><td>62.6</td><td>28.7</td><td>34.4</td><td>37.5</td><td>31.3</td><td>55.7</td><td>46.3</td></tr><tr><td>Taipan</td><td>53.0</td><td>69.6</td><td>46.6</td><td>65.6</td><td>32.9</td><td>36.6</td><td>38.6</td><td>30.7</td><td>60.4</td><td>48.2</td></tr><tr><td rowspan="4">1.3B 100B</td><td>Transformer++</td><td>53.8</td><td>71.6</td><td>53.8</td><td>63.2</td><td>36.3</td><td>36.4</td><td>44.0</td><td>31.2</td><td>59.4</td><td>49.9</td></tr><tr><td>Mamba</td><td>55.2</td><td>73.0</td><td>55.6</td><td>70.7</td><td>38.0</td><td>39.0</td><td>39.9</td><td>32.0</td><td>61.8</td><td>51.7</td></tr><tr><td>Jamba</td><td>54.7</td><td>73.8</td><td>55.8</td><td>69.7</td><td>37.6</td><td>41.8</td><td>40.4</td><td>32.8</td><td>59.2</td><td>51.8</td></tr><tr><td>Taipan</td><td>57.0</td><td>74.9</td><td>57.9</td><td>71.2</td><td>39.3</td><td>40.4</td><td>43.0</td><td>34.4</td><td>61.5</td><td>53.3</td></tr></table>{{< /table-caption >}}

> 🔼 Table 1 presents the zero-shot performance of Taipan and three baseline models (Transformer++, Mamba-2, and Jamba) across various common-sense reasoning and question answering tasks, demonstrating Taipan's superior performance across different model sizes.
> <details>
> <summary>read the caption</summary>
> Table 1: Zero shot results of Taipan against baseline models.
> </details>



### More visual insights



<details>
<summary>More on charts
</summary>


![](charts/charts_2_1.png "🔼 Figure 1: Model Performance Comparison. a) Perplexity across different context lengths. Lower perplexity indicates better performance. b) Latency comparison of models at various generation lengths. Taipan exhibits significantly lower latency and superior scaling compared to other strong baselines for longer sequences.")

> 🔼 The chart compares the perplexity and latency of four different language models (Transformer, Jamba, Mamba, and Taipan) across varying context and generation lengths.
> <details>
> <summary>read the caption</summary>
> Figure 1: Model Performance Comparison. a) Perplexity across different context lengths. Lower perplexity indicates better performance. b) Latency comparison of models at various generation lengths. Taipan exhibits significantly lower latency and superior scaling compared to other strong baselines for longer sequences.
> </details>


![](charts/charts_5_0.png "🔼 Figure 3: Attention mechanisms in Taipan's Selective Attention Layers. White areas indicate no attention. (a) Full Causal Attention (b) Sliding Window Attention (w = 4) (c) Selective Attention (C = 0.3, w = 5)")

> 🔼 The chart compares three different attention mechanisms: full causal attention, sliding window attention, and Taipan's selective attention, showing their attention weight distributions.
> <details>
> <summary>read the caption</summary>
> Figure 3: Attention mechanisms in Taipan's Selective Attention Layers. White areas indicate no attention. (a) Full Causal Attention (b) Sliding Window Attention (w = 4) (c) Selective Attention (C = 0.3, w = 5)
> </details>


![](charts/charts_9_0.png "🔼 Figure 5: Effect of Attention Budget Capacity C on Taipan's Performance")

> 🔼 The chart displays Taipan's performance on SWDE and Hellaswag tasks at various attention budget capacities (C), showing optimal performance at C=0.15.
> <details>
> <summary>read the caption</summary>
> Figure 5: Effect of Attention Budget Capacity C on Taipan's Performance
> </details>


![](charts/charts_10_0.png "🔼 Figure 6: Perplexity comparison of Taipan variants with and without Positional Embeddings across different context lengths. Lower perplexity indicates better performance.")

> 🔼 The chart compares the perplexity of Taipan models with and without positional embeddings across various sequence lengths.
> <details>
> <summary>read the caption</summary>
> Figure 6: Perplexity comparison of Taipan variants with and without Positional Embeddings across different context lengths. Lower perplexity indicates better performance.
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
{{< /gallery >}}