---
title: "SeerAttention: Learning Intrinsic Sparse Attention in Your LLMs"
summary: "SeerAttention learns intrinsic attention sparsity, achieving significant speedups in LLMs without sacrificing accuracy, via a novel learnable gating mechanism and customized FlashAttention."
categories: ["AI Generated"]
tags: ["🔖 24-10-17", "🤗 24-10-21"]
showSummary: true
date: 2024-10-17
draft: false
---

### TL;DR


{{< lead >}}

Large Language Models (LLMs) rely heavily on attention mechanisms, but these are computationally expensive, especially for long contexts.  This paper introduces SeerAttention, a new method that leverages the inherent sparsity in attention maps.  Instead of using predefined sparsity patterns, SeerAttention learns the sparsity directly from the data, resulting in a more adaptable and efficient approach.  The authors developed a specialized FlashAttention implementation to facilitate the learning process. Experiments show SeerAttention outperforms existing sparse attention methods in both post-training and fine-tuning settings, achieving remarkable speedups (up to 5.67x) with minimal loss in accuracy, even at very high sparsity levels (90%).  This is achieved by using a learnable gate to select important blocks in the attention map, treating the rest as sparse.  The method shows adaptability to various context lengths and sparsity ratios.  Overall, SeerAttention offers a promising way to improve the efficiency and scalability of LLMs without significant sacrifices in performance.

{{< /lead >}}


{{< button href="https://arxiv.org/abs/2410.13276" target="_self" >}}
{{< icon "link" >}} &nbsp; read the paper on arXiv
{{< /button >}}
<br><br>
{{< button href="https://huggingface.co/papers/2410.13276" target="_self" >}}
{{< icon "hf-logo" >}} &nbsp; on Hugging Face
{{< /button >}}

#### Why does it matter?
This paper is crucial for researchers working on large language models (LLMs) and attention mechanisms.  It directly addresses the critical challenge of LLM scalability and efficiency, offering a novel solution to reduce computational complexity.  The introduction of a learnable sparsity approach opens new avenues for improving LLM performance and reducing resource consumption, impacting both theoretical advancements and practical applications.
#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} SeerAttention learns attention sparsity rather than relying on predefined patterns, leading to improved accuracy and adaptability. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} A customized FlashAttention kernel enables efficient training of SeerAttention, facilitating scalability and speedup. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} SeerAttention demonstrates significant speedups (up to 5.67x) and maintains near-lossless accuracy even with high sparsity ratios (90%) in both post-training and fine-tuning settings. {{< /typeit >}}
{{< /alert >}}

------
#### Visual Insights



![](figures/figures_4_0.png)

> 🔼 Figure 1 shows the results of SeerAttention on Llama-3-8B model, demonstrating near-lossless performance with high sparsity in both fine-tuning and post-training, along with significant speedup over FlashAttention-2.
> <details>
> <summary>read the caption</summary>
> Figure 1: SeerAttention uses a learning-based approach to exploit attention sparsity of LLMs, applicable in both post-training and fine-tuning stages. By incorporating SeerAttention with YaRN (Peng et al., 2024) to extend a Llama-3-8B model from 8k to 32k context length, the loss curves for 50% to 90% sparsity are nearly identical to the dense YaRN baseline (a); For test perplexity, 50% sparsity achieves near-lossless performance, and even at 90% sparsity, the loss remains minimal (b); SeerAttention achieves up to 5.67x inference speedup at 90% sparsity over FlashAttention-2 (Dao, 2023);
> </details>





![](charts/charts_1_0.png)

> 🔼 Figure 1 shows that SeerAttention, when used with YaRN to extend a Llama-3-8B model, achieves near-lossless performance with 50% sparsity and minimal loss even at 90% sparsity in both fine-tuning loss and test perplexity, while also offering significant inference speedup.
> <details>
> <summary>read the caption</summary>
> Figure 1: SeerAttention uses a learning-based approach to exploit attention sparsity of LLMs, applicable in both post-training and fine-tuning stages. By incorporating SeerAttention with YaRN (Peng et al., 2024) to extend a Llama-3-8B model from 8k to 32k context length, the loss curves for 50% to 90% sparsity are nearly identical to the dense YaRN baseline (a); For test perplexity, 50% sparsity achieves near-lossless performance, and even at 90% sparsity, the loss remains minimal (b); SeerAttention achieves up to 5.67x inference speedup at 90% sparsity over FlashAttention-2 (Dao, 2023);
> </details>





{{< table-caption >}}
<table id='2' style='font-size:14px'><tr><td rowspan="2"></td><td rowspan="2">Sparsity s</td><td rowspan="2">8k</td><td colspan="4">Evaluation Context Length</td></tr><tr><td>16k</td><td>32k</td><td>64k</td><td>128k</td></tr><tr><td>Original</td><td>0.0</td><td>10.03</td><td>9.88</td><td>9.92</td><td>9.97</td><td>10.03</td></tr><tr><td>MoA</td><td>0.35</td><td>10.07</td><td>9.97</td><td>10.02</td><td>10.13</td><td>OOM</td></tr><tr><td>MInference</td><td></td><td>10.12 s = 0.37</td><td>10.06 s = 0.55</td><td>10.24 s = 0.69</td><td>10.43 s = 0.80</td><td>10.89 s = 0.9</td></tr><tr><td rowspan="6">SeerAttention</td><td>0.4</td><td>10.06</td><td>9.92</td><td>9.96</td><td>10.10</td><td>10.29</td></tr><tr><td>0.5</td><td>10.08</td><td>9.94</td><td>9.99</td><td>10.15</td><td>10.38</td></tr><tr><td>0.6</td><td>10.12</td><td>9.96</td><td>10.04</td><td>10.21</td><td>10.50</td></tr><tr><td>0.7</td><td>10.18</td><td>10.01</td><td>10.10</td><td>10.29</td><td>10.71</td></tr><tr><td>0.8</td><td>10.30</td><td>10.07</td><td>10.18</td><td>10.39</td><td>11.18</td></tr><tr><td>0.9</td><td>10.75</td><td>10.24</td><td>10.30</td><td>10.56</td><td>13.20</td></tr></table>{{< /table-caption >}}

> 🔼 Table 1 compares the perplexity of SeerAttention at post-training with MoA and MInference, using the Llama-3.1-8B-Instruct model on the PG19 dataset across various sparsity levels and context lengths.
> <details>
> <summary>read the caption</summary>
> Table 1: Comparing the perplexity of SeerAttention at post-training with MoA and MInference, using the Llama-3.1-8B-Instruct model on the PG19 dataset.
> </details>



### More visual insights



<details>
<summary>More on charts
</summary>


![](charts/charts_6_0.png "🔼 Figure 4: Perplexity results on Proof-pile across various context lengths and sparsity ratios. Note that results on various sparsity ratios comes from the same trained AttnGates by only adjusting the Top-k ratios. Longer context sizes allow for higher sparsity with minimal performance loss.")

> 🔼 Figure 4 shows that SeerAttention only slightly increases perplexity as the sparsity ratio increases across different context lengths, compared to full attention for both Llama-3.1-8B and Mistral-7B-v0.3 models.
> <details>
> <summary>read the caption</summary>
> Figure 4: Perplexity results on Proof-pile across various context lengths and sparsity ratios. Note that results on various sparsity ratios comes from the same trained AttnGates by only adjusting the Top-k ratios. Longer context sizes allow for higher sparsity with minimal performance loss.
> </details>


![](charts/charts_8_0.png "🔼 Figure 5: SeerAttention time breakdown compared to FlashAttention-2. At sequence length 128k with 90% sparsity ratio, SeerAttention speeds up attention computation by 5.47x over FlashAttention-2.")

> 🔼 The chart shows the kernel-level latency breakdown of SeerAttention compared to FlashAttention-2 at different sequence lengths and sparsity levels, demonstrating minimal overhead from the AttnGate and Top-k operations and significant speedup from block-sparse FlashAttention.
> <details>
> <summary>read the caption</summary>
> Figure 5: SeerAttention time breakdown compared to FlashAttention-2. At sequence length 128k with 90% sparsity ratio, SeerAttention speeds up attention computation by 5.47x over FlashAttention-2.
> </details>


![](charts/charts_9_0.png "🔼 Figure 6: SeerAttention block sparse FlashAttention inference kernel speedup.")

> 🔼 The chart shows the speedup of SeerAttention's block-sparse FlashAttention kernel compared to FlashAttention-2 and other sparse attention methods (MoA and MInference) across various sparsity ratios and sequence lengths.
> <details>
> <summary>read the caption</summary>
> Figure 6: SeerAttention block sparse FlashAttention inference kernel speedup.
> </details>


![](charts/charts_9_1.png "🔼 Figure 1: SeerAttention uses a learning-based approach to exploit attention sparsity of LLMs, applicable in both post-training and fine-tuning stages. By incorporating SeerAttention with YaRN (Peng et al., 2024) to extend a Llama-3-8B model from 8k to 32k context length, the loss curves for 50% to 90% sparsity are nearly identical to the dense YaRN baseline (a); For test perplexity, 50% sparsity achieves near-lossless performance, and even at 90% sparsity, the loss remains minimal (b); SeerAttention achieves up to 5.67x inference speedup at 90% sparsity over FlashAttention-2 (Dao, 2023);")

> 🔼 The chart displays the fine-tuning loss, test perplexity, and kernel speedup of SeerAttention with YaRN in comparison to baselines, showcasing its effectiveness in exploiting attention sparsity at various sparsity levels.
> <details>
> <summary>read the caption</summary>
> Figure 1: SeerAttention uses a learning-based approach to exploit attention sparsity of LLMs, applicable in both post-training and fine-tuning stages. By incorporating SeerAttention with YaRN (Peng et al., 2024) to extend a Llama-3-8B model from 8k to 32k context length, the loss curves for 50% to 90% sparsity are nearly identical to the dense YaRN baseline (a); For test perplexity, 50% sparsity achieves near-lossless performance, and even at 90% sparsity, the loss remains minimal (b); SeerAttention achieves up to 5.67x inference speedup at 90% sparsity over FlashAttention-2 (Dao, 2023);
> </details>


![](charts/charts_10_0.png "🔼 Figure 8: Memory and latency of customized FlashAttention with max-pooling training kernel.")

> 🔼 The chart compares the GPU memory usage and latency of three different FlashAttention implementations: Flash-Attn-V2, a customized version with max-pooling, and a naive manual implementation using PyTorch, across various sequence lengths.
> <details>
> <summary>read the caption</summary>
> Figure 8: Memory and latency of customized FlashAttention with max-pooling training kernel.
> </details>


![](charts/charts_10_1.png "🔼 Figure 9: Perplexity with and without RoPE in AttnGate.")

> 🔼 The chart displays the perplexity results on the PG19 dataset for different sparsity ratios (0.5, 0.6, and 0.7) with and without using the RoPE module in the AttnGate across various context lengths.
> <details>
> <summary>read the caption</summary>
> Figure 9: Perplexity with and without RoPE in AttnGate.
> </details>


![](charts/charts_10_2.png "🔼 Figure 10: Perplexity of SeerAttention with different pooling methods.")

> 🔼 The chart displays the perplexity of SeerAttention on the PG19 dataset at varying sparsity levels (0.5 to 0.9) with different combinations of pooling methods for Q and K tensors (average, max, and min).
> <details>
> <summary>read the caption</summary>
> Figure 10: Perplexity of SeerAttention with different pooling methods.
> </details>


</details>



<details>
<summary>More on tables
</summary>


{{< table-caption >}}
<table id='5' style='font-size:14px'><tr><td rowspan="2">Model</td><td rowspan="2">Attention</td><td rowspan="2">Sparsity s</td><td colspan="3">LongBench</td></tr><tr><td>0-4k</td><td>4-8k</td><td>8k+</td></tr><tr><td rowspan="7">Llama-3.1-8B-Instruct</td><td>Original</td><td>0.0</td><td>55.32</td><td>53.98</td><td>52.90</td></tr><tr><td>MoA</td><td>0.35</td><td>50.74</td><td>49.84</td><td>51.89</td></tr><tr><td rowspan="2">MInference</td><td rowspan="2"></td><td>55.23</td><td>53.87</td><td>52.18</td></tr><tr><td>s = 0.06</td><td>s = 0.25</td><td>s = 0.45</td></tr><tr><td rowspan="3">SeerAttention</td><td>0.1</td><td>55.91</td><td>54.32</td><td>53.28</td></tr><tr><td>0.25</td><td>55.00</td><td>54.09</td><td>52.22</td></tr><tr><td>0.5</td><td>52.40</td><td>52.85</td><td>52.43</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> Table 2 compares the accuracy of SeerAttention against MoA and MInference on the LongBench benchmark at post-training, showing SeerAttention's consistent outperformance under similar or higher sparsity ratios.


{{< table-caption >}}
<table id='1' style='font-size:16px'><tr><td rowspan="2">Sparsity</td><td>YaRN</td><td colspan="5">Post-training SeerAttention after YaRN</td><td colspan="5">YaRN with SeerAttention</td></tr><tr><td>0.0</td><td>0.5</td><td>0.6</td><td>0.7</td><td>0.8</td><td>0.9</td><td>0.5</td><td>0.6</td><td>0.7</td><td>0.8</td><td>0.9</td></tr><tr><td>PG19</td><td>8.79</td><td>9.16</td><td>9.30</td><td>9.48</td><td>9.73</td><td>10.18</td><td>8.81</td><td>8.82</td><td>8.85</td><td>8.93</td><td>9.16</td></tr><tr><td>Proof-pile</td><td>2.46</td><td>2.53</td><td>2.57</td><td>2.61</td><td>2.68</td><td>2.85</td><td>2.47</td><td>2.47</td><td>2.48</td><td>2.51</td><td>2.60</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> Table 3 presents the perplexity scores of three different models: the YaRN baseline, SeerAttention applied after YaRN, and YaRN integrated with SeerAttention, across various sparsity levels on two datasets (PG19 and Proof-pile).


{{< table-caption >}}
<table id='3' style='font-size:16px'><tr><td rowspan="2">Latency (Sparsity)</td><td colspan="5">Evaluation Context Length</td></tr><tr><td>8k</td><td>16k</td><td>32k</td><td>64k</td><td>128k</td></tr><tr><td>FlashAttn-2</td><td>0.90 (0)</td><td>1.95 (0)</td><td>4.63 (0)</td><td>10.09 (0)</td><td>35.54 (0)</td></tr><tr><td>MoA</td><td>1.29 (0.35)</td><td>3.44 (0.35)</td><td>10.34 (0.35)</td><td>36.34 (0.35)</td><td>OOM</td></tr><tr><td>MInference</td><td>2.33 (0.37)</td><td>3.10 (0.65)</td><td>4.68 (0.77)</td><td>8.21 (0.86)</td><td>14.38 (0.95)</td></tr><tr><td>SeerAttention</td><td>0.78 (0.50)</td><td>1.65 (0.60)</td><td>3.60 (0.70)</td><td>7.69 (0.80)</td><td>13.37 (0.95)</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> Table 4 compares the time to first token (TTFT) in seconds across different models and sparsity levels, showing SeerAttention's latency advantage.


{{< table-caption >}}
<table id='1' style='font-size:14px'><tr><td></td><td>Algorithm 1: Customized FlashAttention with Max-pooling Kernel</td></tr><tr><td></td><td>Input: Matrices Q,K, V E RNxd in HBM, block sizes Bc, Br Output: Output 0, logsumexp L and attention map D</td></tr><tr><td>1</td><td>N Divide Q into Tr = blocks Q1, . . . , QTr, of size Br x d each Br</td></tr><tr><td>2</td><td>N Divide K, V into Tc blocks K1, . · . , KTc and V1, . · . , VTc, of size Bc x d each Bc</td></tr><tr><td>3</td><td>Divide the output 0 E RNxd into Tr blocks 01, . · · , OTr, of size Br X d each</td></tr><tr><td>4</td><td>Divide the logsumexp L into Tr blocks L1, . . ・ , LTr, of size Br each</td></tr><tr><td>5</td><td>Divide attention score D E RtrxTc into (Tr X Tc) blocks D(⌀) , · · · , D(T⌀ initialize D⌀  (0)1x1</td></tr><tr><td>6</td><td>for i = 1 to Tr do</td></tr><tr><td>7</td><td>Load Qi from HBM to on-chip SRAM</td></tr><tr><td>8</td><td>On chip, initialize 일이 = (0)Brxd, l(o) = (0)Br, mi = (-�)Br ri = (-�)Br</td></tr><tr><td>9</td><td>for j = 1 to Tc do</td></tr><tr><td>10</td><td>Load Kj, Vj from HBM to on-chip SRAM</td></tr><tr><td>11</td><td>On chip, compute S⌀ = QiKT E RBrxBc</td></tr><tr><td>12</td><td>On chip, compute m⌀ = max(m�-1) rowmax(S⌀⌀) ,</td></tr><tr><td>13</td><td>On chip, compute 户(ⓙ = exp( S⌀) - m⌀)</td></tr><tr><td>14</td><td>Update l(j) = l(j-1) + rowsum(P(1)</td></tr><tr><td>15</td><td>On chip, compute O(ⓙ = diag(exp(m.(i-1) - m(�))-10(3-1) + P(j) Vj</td></tr><tr><td>16</td><td>Store r Ⓙ = rowmax ( S⌀) )</td></tr><tr><td>17</td><td>for j = 1 to Tc do</td></tr><tr><td>18</td><td>Update 질㉧ = diag(l(Tc) ) -1 exp(r⌀)  m(Tc))</td></tr><tr><td>19</td><td>On chip, compute D(j) = colmax(r⌀)</td></tr><tr><td>20</td><td>Write D ⌀ to HBM as (i, j)-th block of D</td></tr><tr><td>21</td><td>On chip, compute Oi = diag(liTe) ) -1⌀(Tc)</td></tr><tr><td>22</td><td>On chip, compute Li = m(Ic) + log(l(Tc) )</td></tr><tr><td>23</td><td>Write Oi to HBM as the i-th block of 0</td></tr><tr><td>24</td><td>Write Li to HBM as the i-th block of L</td></tr><tr><td>25</td><td>return 0, L, D</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> Table 1 compares the perplexity results of SeerAttention against MoA and MInference on the Llama-3.1-8B-Instruct model at post-training, varying sparsity levels and context lengths.


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
{{< /gallery >}}