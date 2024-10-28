---
title: "Should We Really Edit Language Models? On the Evaluation of Edited Language Models"
summary: "Contrary to popular belief, current language model editing techniques cause inevitable performance decline and safety issues when scaling edits, urging the need for more practical methods."
categories: ["AI Generated"]
tags: ["🔖 24-10-24", "🤗 24-10-25"]
showSummary: true
date: 2024-10-24
draft: false
---

### TL;DR


{{< lead >}}

This research comprehensively evaluates the effectiveness and safety of various language model editing methods.  The key finding is that, despite improvements in reliability, generalization, and locality,  existing methods cause unavoidable performance drops and safety compromises as the number of edits grows.  Instruction-tuned models and larger models proved more robust, but even they eventually suffer from decreased performance and safety risks at a large scale. The study concludes that current methods are insufficient for extensive knowledge updates, underscoring the need for further research into more practical and secure editing techniques.

{{< /lead >}}


{{< button href="https://arxiv.org/abs/2410.18785" target="_self" >}}
{{< icon "link" >}} &nbsp; read the paper on arXiv
{{< /button >}}
<br><br>
{{< button href="https://huggingface.co/papers/2410.18785" target="_self" >}}
{{< icon "hf-logo" >}} &nbsp; on Hugging Face
{{< /button >}}

#### Why does it matter?
This paper is crucial for AI researchers working on language models and model editing.  It reveals critical limitations of current editing methods, challenges existing assumptions, and highlights potential safety risks. This opens new avenues for research focusing on more robust and reliable editing techniques, especially concerning the preservation of general model capabilities and safety.
#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} Existing language model editing methods significantly reduce model performance and safety as the number of edits increases. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} Instruction-tuned models are more resistant to performance degradation from editing, while larger models show better robustness than smaller ones. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} Current editing methods are unsuitable for large-scale knowledge updates within language models. {{< /typeit >}}
{{< /alert >}}

------
#### Visual Insights



![](figures/figures_2_0.png)

> 🔼 The figure illustrates how model editing methods can efficiently update knowledge but also fail to retain this knowledge when scaled to a large number of edits.
> <details>
> <summary>read the caption</summary>
> Figure 1: Illustration about the model editing and its pitfalls in retaining edited knowledge. Left panel: model editing methods can efficiently update knowledge within language models; Right panel: when scaling editing to thousands, the model can't retain edited knowledge, see [16] for details.
> </details>





![](charts/charts_5_0.png)

> 🔼 The chart displays the performance trends of six different model editing methods on Llama2-7B base model across multiple benchmarks, showing the impact of the number of edits on the model's abilities.
> <details>
> <summary>read the caption</summary>
> Figure 2: Performance trends of evaluating edited Llama2-7B base model across different benchmarks using six editing methods. Results reveal that PMET and MEND can effectively preserve the model's abilities across all tasks. While KN drastically drops even less than ten edits.
> </details>





{{< table-caption >}}
<table id='4' style='font-size:14px'><tr><td rowspan="3">Method w/o Edit</td><td rowspan="2"># Edits</td><td colspan="4">GPT2-XL</td></tr><tr><td>MMLU</td><td>GSM8K</td><td>BBH</td><td>CSQA</td></tr><tr><td>0</td><td>0.2098</td><td>0.0144</td><td>0.0382</td><td>0.1941</td></tr><tr><td rowspan="6">PMET</td><td>10</td><td>0.2104</td><td>0.0159</td><td>0.0377</td><td>0.1941</td></tr><tr><td>20</td><td>0.1081</td><td>0.0144</td><td>0.0117</td><td>0.2048</td></tr><tr><td>50</td><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td>100</td><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td>500</td><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td>1000</td><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td rowspan="5">MEND</td><td>10</td><td>0.2096</td><td>0.0144</td><td>0.0377</td><td>0.1949</td></tr><tr><td>30</td><td>0.2094</td><td>0.0152</td><td>0.0388</td><td>0.1941</td></tr><tr><td>100</td><td>0.2098</td><td>0.0144</td><td>0.0380</td><td>0.1957</td></tr><tr><td>500</td><td>0.2100</td><td>0.0144</td><td>0.0382</td><td>0.1941</td></tr><tr><td>1000</td><td>0.2099</td><td>0.0144</td><td>0.0381</td><td>0.1933</td></tr><tr><td rowspan="2">KN</td><td>500</td><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td>1000</td><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td rowspan="2">MEMIT</td><td>500</td><td>0.2112</td><td>0.0159</td><td>0.0363</td><td>0.1957</td></tr><tr><td>1000</td><td>0.2097</td><td>0.0152</td><td>0.0193</td><td>0.199</td></tr></table>{{< /table-caption >}}

> 🔼 Table 1 presents the evaluation results of the GPT2-XL language model after editing using various methods and a different number of edits.
> <details>
> <summary>read the caption</summary>
> Table 1: Evaluation results of GPT2-XL. experiments are conducted on a sever with 8 RTX 4090 GPUs.
> </details>



### More visual insights



<details>
<summary>More on charts
</summary>


![](charts/charts_6_0.png "🔼 Figure 2: Performance trends of evaluating edited Llama2-7B base model across different benchmarks using six editing methods. Results reveal that PMET and MEND can effectively preserve the model's abilities across all tasks. While KN drastically drops even less than ten edits.")

> 🔼 The chart displays the performance trends of six different model editing methods on the Llama2-7B base model across various benchmark tasks, showing how the number of edits affects model performance.
> <details>
> <summary>read the caption</summary>
> Figure 2: Performance trends of evaluating edited Llama2-7B base model across different benchmarks using six editing methods. Results reveal that PMET and MEND can effectively preserve the model's abilities across all tasks. While KN drastically drops even less than ten edits.
> </details>


![](charts/charts_6_1.png "🔼 Figure 2: Performance trends of evaluating edited Llama2-7B base model across different benchmarks using six editing methods. Results reveal that PMET and MEND can effectively preserve the model's abilities across all tasks. While KN drastically drops even less than ten edits.")

> 🔼 The chart displays the performance trends of six different model editing methods on the Llama2-7B base model across various benchmarks, showing that PMET and MEND maintain model abilities better than others, especially KN.
> <details>
> <summary>read the caption</summary>
> Figure 2: Performance trends of evaluating edited Llama2-7B base model across different benchmarks using six editing methods. Results reveal that PMET and MEND can effectively preserve the model's abilities across all tasks. While KN drastically drops even less than ten edits.
> </details>


![](charts/charts_7_0.png "🔼 Figure 2: Performance trends of evaluating edited Llama2-7B base model across different benchmarks using six editing methods. Results reveal that PMET and MEND can effectively preserve the model’s abilities across all tasks. While KN drastically drops even less than ten edits.")

> 🔼 The chart displays the performance trends of six different model editing methods on Llama2-7B across five different benchmark tasks, showing how the number of edits affects model performance.
> <details>
> <summary>read the caption</summary>
> Figure 2: Performance trends of evaluating edited Llama2-7B base model across different benchmarks using six editing methods. Results reveal that PMET and MEND can effectively preserve the model’s abilities across all tasks. While KN drastically drops even less than ten edits.
> </details>


![](charts/charts_8_0.png "🔼 Figure 2: Performance trends of evaluating edited Llama2-7B base model across different benchmarks using six editing methods. Results reveal that PMET and MEND can effectively preserve the model’s abilities across all tasks. While KN drastically drops even less than ten edits.")

> 🔼 The chart displays the performance trends of six different model editing methods on the Llama2-7B base model across various benchmarks, showing that PMET and MEND effectively preserve model abilities while KN shows a significant performance drop.
> <details>
> <summary>read the caption</summary>
> Figure 2: Performance trends of evaluating edited Llama2-7B base model across different benchmarks using six editing methods. Results reveal that PMET and MEND can effectively preserve the model’s abilities across all tasks. While KN drastically drops even less than ten edits.
> </details>


![](charts/charts_21_0.png "🔼 Figure 2: Performance trends of evaluating edited Llama2-7B base model across different benchmarks using six editing methods. Results reveal that PMET and MEND can effectively preserve the model’s abilities across all tasks. While KN drastically drops even less than ten edits.")

> 🔼 The chart displays the performance trends of six different model editing methods on the Llama2-7B base model across multiple benchmark tasks, showing that PMET and MEND are more effective in preserving model abilities than other methods.
> <details>
> <summary>read the caption</summary>
> Figure 2: Performance trends of evaluating edited Llama2-7B base model across different benchmarks using six editing methods. Results reveal that PMET and MEND can effectively preserve the model’s abilities across all tasks. While KN drastically drops even less than ten edits.
> </details>


![](charts/charts_21_1.png "🔼 Figure 2: Performance trends of evaluating edited Llama2-7B base model across different benchmarks using six editing methods. Results reveal that PMET and MEND can effectively preserve the model’s abilities across all tasks. While KN drastically drops even less than ten edits.")

> 🔼 The chart displays performance trends of six different model editing methods on the Llama2-7B base model across multiple benchmark tasks, revealing that PMET and MEND are most effective at preserving model abilities while KN shows a significant drop in performance.
> <details>
> <summary>read the caption</summary>
> Figure 2: Performance trends of evaluating edited Llama2-7B base model across different benchmarks using six editing methods. Results reveal that PMET and MEND can effectively preserve the model’s abilities across all tasks. While KN drastically drops even less than ten edits.
> </details>


</details>



<details>
<summary>More on tables
</summary>


{{< table-caption >}}
<table id='0' style='font-size:14px'><tr><td rowspan="3">Method w/o Edit</td><td rowspan="2"># Edits</td><td colspan="4">Llama2-7B-Chat</td><td colspan="4">Mistral-7B-Instruct</td></tr><tr><td>MMLU</td><td>GSM8K</td><td>BBH</td><td>CSQA</td><td>MMLU</td><td>GSM8K</td><td>BBH</td><td>CSQA</td></tr><tr><td>0</td><td>0.4516</td><td>0.2032</td><td>0.3997</td><td>0.6134</td><td>0.5350</td><td>0.3450</td><td>0.4668</td><td>0.6601</td></tr><tr><td rowspan="6">ROME</td><td>1</td><td>0.4576</td><td>0.1531</td><td>0.3985</td><td>0.5938</td><td>0.5364</td><td>0.3442</td><td>0.4667</td><td>0.6699</td></tr><tr><td>5</td><td>0.4587</td><td>0.1425</td><td>0.3976</td><td>0.5839</td><td>0.5354</td><td>0.3442</td><td>0.4648</td><td>0.6618</td></tr><tr><td>10</td><td>0.4578</td><td>0.1471</td><td>0.3974</td><td>0.5864</td><td>0.5333</td><td>0.3366</td><td>0.4684</td><td>0.6634</td></tr><tr><td>20</td><td>0.4416</td><td>0.1471</td><td>0.3828</td><td>0.5602</td><td>0.5310</td><td>0.3397</td><td>0.4693</td><td>0.6519</td></tr><tr><td>50</td><td>0.2700</td><td>0.0409</td><td>0.2838</td><td>0.2048</td><td>0.4115</td><td>0.2517</td><td>0.3888</td><td>0.4636</td></tr><tr><td>100</td><td>0.0007</td><td>0.0152</td><td>0</td><td>0</td><td>0.1884</td><td>0.0190</td><td>0.1884</td><td>0.0026</td></tr><tr><td rowspan="6">MEMIT</td><td>1</td><td>0.4715</td><td>0.2085</td><td>0.4106</td><td>0.6143</td><td>0.5356</td><td>0.3450</td><td>0.4664</td><td>0.6683</td></tr><tr><td>5</td><td>0.4717</td><td>0.1895</td><td>0.4114</td><td>0.6233</td><td>0.5345</td><td>0.3419</td><td>0.4656</td><td>0.6675</td></tr><tr><td>10</td><td>0.4704</td><td>0.2047</td><td>0.4132</td><td>0.6151</td><td>0.5357</td><td>0.3434</td><td>0.4674</td><td>0.6716</td></tr><tr><td>20</td><td>0.4698</td><td>0.1956</td><td>0.4087</td><td>0.6405</td><td>0.5358</td><td>0.3465</td><td>0.4670</td><td>0.6667</td></tr><tr><td>50</td><td>0.4682</td><td>0.2039</td><td>0.4017</td><td>0.6405</td><td>0.5328</td><td>0.3487</td><td>0.4643</td><td>0.6536</td></tr><tr><td>100</td><td>0.4485</td><td>0.1850</td><td>0.3959</td><td>0.6044</td><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td rowspan="6">PMET</td><td>1</td><td>0.4583</td><td>0.1471</td><td>0.3988</td><td>0.5930</td><td>0.5357</td><td>0.3465</td><td>0.6658</td><td>0.4663</td></tr><tr><td>5</td><td>0.4586</td><td>0.1448</td><td>0.4001</td><td>0.5897</td><td>0.5356</td><td>0.3457</td><td>0.6691</td><td>0.4669</td></tr><tr><td>10</td><td>0.4593</td><td>0.1471</td><td>0.4017</td><td>0.5930</td><td>0.5348</td><td>0.3450</td><td>0.6691</td><td>0.4662</td></tr><tr><td>20</td><td>0.4588</td><td>0.1456</td><td>0.4010</td><td>0.5872</td><td>0.5360</td><td>0.3397</td><td>0.6618</td><td>0.4570</td></tr><tr><td>50</td><td>0.4584</td><td>0.1448</td><td>0.4019</td><td>0.5905</td><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td>100</td><td>0.4590</td><td>0.1448</td><td>0.3960</td><td>0.5930</td><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td rowspan="10">MEND KN</td><td>10</td><td>0.4731</td><td>0.2100</td><td>0.4097</td><td>0.6216</td><td>-</td><td></td><td>-</td><td></td></tr><tr><td>20</td><td>0.4729</td><td>0.2024</td><td>0.4057</td><td>0.6102</td><td>一</td><td>-</td><td>-</td><td>-</td></tr><tr><td>50</td><td>0.4728</td><td>0.2024</td><td>0.4101</td><td>0.6183</td><td>-</td><td>-</td><td>-</td><td>-</td></tr><tr><td>100</td><td>0.4731</td><td>0.2009</td><td>0.4093</td><td>0.6183</td><td>-</td><td>-</td><td>-</td><td>-</td></tr><tr><td>200</td><td>0.4738</td><td>0.2100</td><td>0.4030</td><td>0.6249</td><td>-</td><td>-</td><td>-</td><td></td></tr><tr><td>500</td><td>0.4732</td><td>0.2168</td><td>0.4089</td><td>0.6192</td><td>-</td><td>-</td><td>-</td><td>-</td></tr><tr><td>1000</td><td>0.4728</td><td>0.2138</td><td>0.4118</td><td>0.6224</td><td>-</td><td>-</td><td>-</td><td>-</td></tr><tr><td>10</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td>20</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td>50</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td><td>0</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> Table 2 presents a quantitative analysis of the impact of different editing methods and varying numbers of edits on the general abilities of base language models across four benchmark tasks.


{{< table-caption >}}
<table id='0' style='font-size:14px'><tr><td>Model</td><td>Method</td><td># Edits</td><td>MMLU↑</td><td>GSM8K↑</td><td>BBH↑</td><td>CSQA↑</td></tr><tr><td rowspan="7">Pythia-160M</td><td>w/o Edit</td><td>0</td><td>0.2435</td><td>0.0174</td><td>0.0742</td><td>0.1884</td></tr><tr><td rowspan="3">ROME</td><td>10</td><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td>50</td><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td>100</td><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td rowspan="3">MEMIT</td><td>10</td><td>0.2460</td><td>0.0212</td><td>0.0785</td><td>0.2056</td></tr><tr><td>50</td><td>0.2447</td><td>0.0227</td><td>0.0755</td><td>0.1982</td></tr><tr><td>100</td><td>0.2468</td><td>0.0235</td><td>0.0743</td><td>0.1990</td></tr><tr><td rowspan="7">Pythia-410M</td><td>w/o Edit</td><td>0</td><td>0.2614</td><td>0.0144</td><td>0.2497</td><td>0.2064</td></tr><tr><td rowspan="3">ROME</td><td>10</td><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td>50</td><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td>100</td><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td rowspan="3">MEMIT</td><td>10</td><td>0.2628</td><td>0.0182</td><td>0.2476</td><td>0.2015</td></tr><tr><td>50</td><td>0.2629</td><td>0.0144</td><td>0.2482</td><td>0.2080</td></tr><tr><td>100</td><td>0.2627</td><td>0.0190</td><td>0.2490</td><td>0.2048</td></tr><tr><td rowspan="7">Pythia-1B</td><td>w/o Edit</td><td>0</td><td>0.2552</td><td>0.0273</td><td>0.2535</td><td>0.1892</td></tr><tr><td rowspan="3">ROME</td><td>10</td><td>0.2547</td><td>0.0083</td><td>0.0052</td><td>0.2039</td></tr><tr><td>50</td><td>0.0017</td><td>0</td><td>0</td><td>0</td></tr><tr><td>100</td><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td rowspan="3">MEMIT</td><td>10</td><td>0.2562</td><td>0.0265</td><td>0.2545</td><td>0.1908</td></tr><tr><td>50</td><td>0.2539</td><td>0.0265</td><td>0.2544</td><td>0.2015</td></tr><tr><td>100</td><td>0.2547</td><td>0.0258</td><td>0.2532</td><td>0.2064</td></tr><tr><td rowspan="7">Pythia-2.8B</td><td>w/o Edit</td><td>0</td><td>0.2800</td><td>0.0364</td><td>0.2870</td><td>0.2146</td></tr><tr><td rowspan="3">ROME</td><td>10</td><td>0.2272</td><td>0.0008</td><td>0.0004</td><td>0.1990</td></tr><tr><td>50</td><td>0.0001</td><td>0.0191</td><td>0</td><td>0</td></tr><tr><td>100</td><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td rowspan="3">MEMIT</td><td>10</td><td>0.2547</td><td>0.0303</td><td>0.2774</td><td>0.2154</td></tr><tr><td>50</td><td>0.2554</td><td>0.0349</td><td>0.2758</td><td>0.2269</td></tr><tr><td>100</td><td>0.2559</td><td>0.0318</td><td>0.2749</td><td>0.2179</td></tr><tr><td rowspan="14">Pythia-6.9B Pythia-12B</td><td>w/o Edit</td><td>0</td><td>0.2565</td><td>0.0318</td><td>0.2762</td><td>0.2260</td></tr><tr><td rowspan="3">ROME</td><td>10</td><td>0.0189</td><td>0</td><td>0</td><td>0</td></tr><tr><td>50</td><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td>100</td><td>0</td><td>0</td><td>0</td><td>0</td></tr><tr><td rowspan="3">MEMIT</td><td>10</td><td>0.2547</td><td>0.0303</td><td>0.2774</td><td>0.2154</td></tr><tr><td>50</td><td>0.2554</td><td>0.0349</td><td>0.2758</td><td>0.2269</td></tr><tr><td>100</td><td>0.2559</td><td>0.0318</td><td>0.2749</td><td>0.2179</td></tr><tr><td rowspan="4">w/o Edit ROME</td><td>0</td><td>0.2621</td><td>0.0485</td><td>0.2868</td><td>0.2375</td></tr><tr><td>10</td><td>0.0263</td><td>0.0380</td><td>0</td><td>0</td></tr><tr><td></td><td>0</td><td>0.0380</td><td>0</td><td>0</td></tr><tr><td>50 100</td><td>0</td><td>0.0380</td><td>0</td><td>0</td></tr><tr><td rowspan="3">MEMIT</td><td>10</td><td>0.2615</td><td>0.0462</td><td>0.2878</td><td>0.2408</td></tr><tr><td>50</td><td>0.2633</td><td>0.0531</td><td>0.2916</td><td>0.2514</td></tr><tr><td>100</td><td>0.2587</td><td>0.0523</td><td>0.2925</td><td>0.2465</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> Table 2 presents a quantitative evaluation of the impact of various model editing methods and the number of edits on the general capabilities of base language models across different benchmarks.


{{< table-caption >}}
<table id='0' style='font-size:14px'><tr><td rowspan="2">Method</td><td rowspan="2"># Edits</td><td colspan="2">Llama2-7B</td><td colspan="2">Llama2-7B-chat</td><td colspan="2">Mixtral-7B</td><td colspan="2">Mixtral-7B-Instruct</td></tr><tr><td>TruthfulQA</td><td>Toxigen</td><td>TruthfulQA</td><td>Toxigen</td><td>TruthfulQA</td><td>Toxigen</td><td>TruthfulQA</td><td>Toxigen</td></tr><tr><td rowspan="2">w/o Edits</td><td>0</td><td>0.2521</td><td>0.4284</td><td>0.3023</td><td>0.5177</td><td>0.2815</td><td>0.4247</td><td>0.3917</td><td>0.4896</td></tr><tr><td>1</td><td>0.2521</td><td>0.4296</td><td>0.2921</td><td>0.5196</td><td>0.2815</td><td>0.4247</td><td>0.3941</td><td>0.4810</td></tr><tr><td rowspan="5">ROME</td><td>5</td><td>0.2497</td><td>0.4272</td><td>0.2997</td><td>0.5072</td><td>0.2815</td><td>0.4247</td><td>0.3929</td><td>0.4896</td></tr><tr><td>10</td><td>0.2485</td><td>0.4296</td><td>0.2962</td><td>0.5080</td><td>0.2742</td><td>0.4235</td><td>0.3892</td><td>0.4737</td></tr><tr><td>20</td><td>0.2411</td><td>0.4284</td><td>0.2913</td><td>0.4871</td><td>0.2742</td><td>0.4247</td><td>0.3868</td><td>0.4737</td></tr><tr><td>50</td><td>0.2411</td><td>0.4101</td><td>0.2497</td><td>0.4957</td><td>0.2350</td><td>0.4247</td><td>0.2644</td><td>0.4504</td></tr><tr><td>100</td><td>0.2729</td><td>0.4982</td><td>0.2974</td><td>0.5141</td><td>0.2509</td><td>0.5667</td><td>0.2827</td><td>0.5251</td></tr><tr><td rowspan="6">MEMIT</td><td>1</td><td>0.2509</td><td>0.4284</td><td>0.2999</td><td>0.5116</td><td>0.2815</td><td>0.4272</td><td>0.3905</td><td>0.4859</td></tr><tr><td>5</td><td>0.2497</td><td>0.4272</td><td>0.2950</td><td>0.5116</td><td>0.2803</td><td>0.4272</td><td>0.3929</td><td>0.4908</td></tr><tr><td>10</td><td>0.2497</td><td>0.4284</td><td>0.2925</td><td>0.5153</td><td>0.2815</td><td>0.4259</td><td>0.3929</td><td>0.4847</td></tr><tr><td>20</td><td>0.2460</td><td>0.4308</td><td>0.2999</td><td>0.5018</td><td>0.2791</td><td>0.4259</td><td>0.3917</td><td>0.4908</td></tr><tr><td>50</td><td>0.2399</td><td>0.4308</td><td>0.2815</td><td>0.5153</td><td>0.2668</td><td>0.4308</td><td>0.3807</td><td>0.4774</td></tr><tr><td>100</td><td>0.1922</td><td>0.4321</td><td>0.2472</td><td>0.4896</td><td>0.2375</td><td>0.4627</td><td>0.2350</td><td>0.5838</td></tr><tr><td rowspan="8">PMET</td><td>1</td><td>0.2521</td><td>0.4296</td><td>0.2974</td><td>0.5163</td><td>0.2815</td><td>0.4247</td><td>0.3917</td><td>0.4823</td></tr><tr><td>5</td><td>0.2497</td><td>0.4272</td><td>0.2988</td><td>0.5175</td><td>0.2815</td><td>0.4247</td><td>0.3917</td><td>0.4835</td></tr><tr><td>10</td><td>0.2485</td><td>0.4296</td><td>0.2964</td><td>0.5190</td><td>0.2840</td><td>0.4235</td><td>0.3929</td><td>0.4847</td></tr><tr><td>20</td><td>0.2411</td><td>0.4284</td><td>0.2974</td><td>0.5141</td><td>0.2740</td><td>0.4247</td><td>0.3905</td><td>0.4908</td></tr><tr><td>50</td><td>0.2411</td><td>0.4100</td><td>0.2962</td><td>0.5129</td><td>0.2350</td><td>0.4247</td><td>0.2375</td><td>0.4333</td></tr><tr><td>100</td><td>0.2729</td><td>0.4982</td><td>0.2962</td><td>0.5165</td><td>0.2509</td><td>0.5667</td><td>0.2350</td><td>0.4333</td></tr><tr><td>500</td><td>0.2350</td><td>0.4259</td><td>0.2362</td><td>0.5667</td><td>-</td><td>-</td><td>-</td><td>-</td></tr><tr><td>1000</td><td>0.2362</td><td>0.4308</td><td>0.2350</td><td>0.5667</td><td>-</td><td>-</td><td>-</td><td>-</td></tr><tr><td rowspan="6">MEND</td><td>10</td><td>0.2472</td><td>0.4308</td><td>0.2974</td><td>0.5141</td><td>-</td><td>-</td><td>-</td><td></td></tr><tr><td>20</td><td>0.2546</td><td>0.4296</td><td>0.2999</td><td>0.5104</td><td></td><td></td><td>-</td><td></td></tr><tr><td>50</td><td>0.2521</td><td>0.4296</td><td>0.2938</td><td>0.5153</td><td>-</td><td>、</td><td>-</td><td></td></tr><tr><td>100</td><td>0.2521</td><td>0.4296</td><td>0.3035</td><td>0.5153</td><td>、</td><td>-</td><td>-</td><td></td></tr><tr><td>500</td><td>0.2521</td><td>0.4308</td><td>0.3035</td><td>0.5080</td><td>-</td><td>-</td><td>-</td><td></td></tr><tr><td>1000</td><td>0.2485</td><td>0.4308</td><td>0.2950</td><td>0.5055</td><td>-</td><td>-</td><td>-</td><td>-</td></tr><tr><td rowspan="5">KN</td><td>10</td><td>0.2350</td><td>0.4333</td><td>0.2277</td><td>0.4333</td><td>0.2889</td><td>0.4308</td><td></td><td></td></tr><tr><td>50</td><td>0.2399</td><td>0.5667</td><td>0.2399</td><td>0.4590</td><td>0.2558</td><td>0.5667</td><td>-</td><td></td></tr><tr><td>100</td><td>0.2350</td><td>0.5667</td><td>0.2399</td><td>0.4590</td><td>0.2583</td><td>0.5667</td><td>-</td><td>-</td></tr><tr><td>500</td><td>0.2362</td><td>0.4333</td><td>0.2392</td><td>0.4590</td><td>0.2583</td><td>0.5667</td><td>-</td><td>-</td></tr><tr><td>1000</td><td>0.2313</td><td>0.4333</td><td>0.2399</td><td>0.4590</td><td>0.2583</td><td>0.5667</td><td>-</td><td></td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> Table 2 presents a quantitative evaluation of the impact of different model editing methods and varying numbers of edits on the general abilities of several base language models across four distinct benchmark tasks.


{{< table-caption >}}
<table id='3' style='font-size:14px'><tr><td>DATASET</td><td>TASK TYPE</td><td># FEW-SHOT</td><td># TEST</td><td>METRIC</td><td>EVALUATION METHOD</td></tr><tr><td>MMLU 27</td><td>World Knowledge</td><td>5</td><td>14,079</td><td>Accuracy</td><td>Generation-Based</td></tr><tr><td>BBH 28</td><td>World Knowledge</td><td>3</td><td>6,511</td><td>Accuracy</td><td>Generation-Based</td></tr><tr><td>GSM8K 39</td><td>Arithmetic</td><td>8</td><td>1,319</td><td>Exact match</td><td>Generation-Based</td></tr><tr><td>CSQA* 40</td><td>Commonsense</td><td>7</td><td>1,221</td><td>Accuracy</td><td>Generation-Based</td></tr><tr><td>TriviaQA 41</td><td>Reading Comprehension</td><td>0</td><td>17,900</td><td>Exact match</td><td>Generation-Based</td></tr><tr><td>TruthfulQA 42</td><td>Truthful</td><td>0</td><td>817</td><td>Accuracy</td><td>Sequence-Based</td></tr><tr><td>ToxiGen 43</td><td>Hate Speech</td><td>0</td><td>940</td><td>Accuracy</td><td>Sequence-Based</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> Table 2 presents the results of evaluating the impact of different model editing methods and various numbers of edits on the general abilities of base language models across four benchmark tasks.


{{< table-caption >}}
<table id='7' style='font-size:16px'><tr><td rowspan="2">Method</td><td colspan="3">With vLLM</td><td colspan="3">Without vLLM</td></tr><tr><td>MMLU</td><td>GSM8K</td><td>CSQA</td><td>MMLU</td><td>GSM8K</td><td>CSQA</td></tr><tr><td>Llama2-7B</td><td>103</td><td>5</td><td>26</td><td>840</td><td>7</td><td>42</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> Table 7 compares the time costs of running benchmarks with and without vLLM, demonstrating the significant time reduction achieved by using vLLM.


{{< table-caption >}}
<table id='2' style='font-size:16px'><tr><td rowspan="2">Method</td><td colspan="3">Llama2-7B</td><td colspan="3">GPT2-XL</td></tr><tr><td>10</td><td>50</td><td>100</td><td>10</td><td>50</td><td>100</td></tr><tr><td>ROME</td><td>2m1s</td><td>9m53s</td><td>16m31s</td><td>59s</td><td>4m4s</td><td>8mlls</td></tr><tr><td>MEMIT</td><td>4m30s</td><td>20m29s</td><td>40m14s</td><td>2m10s</td><td>8m24s</td><td>17m23s</td></tr><tr><td>GRACE</td><td>10s</td><td>1m3s</td><td>2mls</td><td>5s</td><td>31s</td><td>1m2s</td></tr><tr><td>MEND</td><td>24s</td><td>1m34s</td><td>2m17s</td><td>11s</td><td>52s</td><td>1m24s</td></tr><tr><td>SERAC</td><td>20s</td><td>1m7s</td><td>1m24s</td><td>14s</td><td>1m12s</td><td>2m15s</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> Table 2 presents the performance of different model editing methods on various language models (base models) with different numbers of edits, evaluated across multiple benchmarks.


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
<img src="paper_images/21.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/22.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/23.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/24.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/25.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/26.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/27.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/28.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/29.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/30.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/31.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/32.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/33.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/34.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/35.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="paper_images/36.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
{{< /gallery >}}