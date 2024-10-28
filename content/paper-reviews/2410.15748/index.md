---
title: "Alchemy: Amplifying Theorem-Proving Capability through Symbolic Mutation"
summary: "Alchemy: A novel framework synthesizes formal theorems via symbolic mutation, boosting neural theorem-proving performance by significantly expanding the training dataset."
categories: ["AI Generated"]
tags: ["🔖 24-10-21", "🤗 24-10-22"]
showSummary: true
date: 2024-10-21
draft: false
---

### TL;DR


{{< lead >}}

The research tackles the data scarcity problem in Neural Theorem Proving (NTP) by introducing Alchemy, a novel data synthesis method. Alchemy generates new mathematical theorems by symbolically manipulating existing ones within the Lean theorem prover's Mathlib library. This significantly expands the training data, improving the performance of large language models (LLMs) on theorem-proving benchmarks by 5% absolutely on an in-distribution dataset and 2.5% absolutely on an out-of-distribution one. The effectiveness of the method is demonstrated through rigorous experimentation and analysis. The open-sourcing of both the synthetic data and code further enhances the impact of this work for the broader research community.

{{< /lead >}}


{{< button href="https://arxiv.org/abs/2410.15748" target="_self" >}}
{{< icon "link" >}} &nbsp; read the paper on arXiv
{{< /button >}}

{{< button href="https://huggingface.co/papers/2410.15748" target="_self" >}}
{{< icon "hf-logo" >}} &nbsp; on Hugging Face
{{< /button >}}

#### Why does it matter?
This paper is crucial for researchers in neural theorem proving and machine learning.  It addresses the critical issue of data scarcity by introducing a novel data synthesis method, significantly impacting model performance.  The open-sourced data and codebase facilitate further research and development in this burgeoning field, opening new avenues for creating stronger theorem provers.
#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} Alchemy, a data synthesis framework, generates new formal theorems through symbolic mutation, increasing the Mathlib dataset by an order of magnitude. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} Continual pre-training and fine-tuning on the expanded dataset improved model performance on both in-distribution and out-of-distribution benchmarks. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} The open-sourced synthetic data and code offer valuable resources for advancing research in neural theorem proving. {{< /typeit >}}
{{< /alert >}}

------
#### Visual Insights



![](figures/figures_3_0.png)

> 🔼 The figure illustrates the data synthesis pipeline that constructs new theorems through symbolic mutation at the theorem level and merges existing proof trees at the proof tree level.
> <details>
> <summary>read the caption</summary>
> Figure 1: The overview of our synthesis pipeline. At the theorem level, we find invocable theorems that can be used to rewrite or apply to the assumptions or assertion of the candidate statement, such as the iff and implication rules about the Coprime. Then, we construct the new statements by replacing the specific component with its equivalent form or antecedent. At the proof tree level, our method merges two existing proof trees.
> </details>





![](charts/charts_10_0.png)

> 🔼 The chart shows the impact of varying quantities of synthesized state-tactic pairs on the number of theorems proved by Llama-3-8b on the random split of the Leandojo benchmark.
> <details>
> <summary>read the caption</summary>
> Figure 4: Influence of the quantity of synthesized data points.
> </details>





{{< table-caption >}}
<table id='1' style='font-size:20px'><tr><td>Tactic</td><td>Candidate theorems</td><td>Stage one</td><td>Stage two</td><td>Expansion</td><td>Conversion Ratio</td></tr><tr><td>rw</td><td>110,657</td><td>5,081,544</td><td>2,830,817</td><td>x25</td><td>56%</td></tr><tr><td>apply</td><td>78,871</td><td>9,483,504</td><td>3,495,832</td><td>x44</td><td>37%</td></tr></table>{{< /table-caption >}}

> 🔼 The table shows the number of theorems at different stages of the data synthesis pipeline for the rw and apply tactics, indicating a significant increase in the number of theorems.
> <details>
> <summary>read the caption</summary>
> Table 2: Number of theorems. Stage one: the number of invocable instructions for all candidate theorems. Stage two: the number of theorems that pass the verification of the Lean theorem prover.
> </details>



### More visual insights

<details>
<summary>More on figures
</summary>


![](figures/figures_8_0.png)

> 🔼 The figure illustrates the data synthesis pipeline, showing how new theorems are constructed from existing theorems through symbolic mutation at both the theorem and proof tree levels.
> <details>
> <summary>read the caption</summary>
> Figure 1: The overview of our synthesis pipeline. At the theorem level, we find invocable theorems that can be used to rewrite or apply to the assumptions or assertion of the candidate statement, such as the iff and implication rules about the Coprime. Then, we construct the new statements by replacing the specific component with its equivalent form or antecedent. At the proof tree level, our method merges two existing proof trees.
> </details>



![](figures/figures_19_0.png)

> 🔼 The figure illustrates the data synthesis pipeline, showing how new theorems are constructed from existing ones through symbolic manipulation at both the theorem and proof tree levels.
> <details>
> <summary>read the caption</summary>
> Figure 1: The overview of our synthesis pipeline. At the theorem level, we find invocable theorems that can be used to rewrite or apply to the assumptions or assertion of the candidate statement, such as the iff and implication rules about the Coprime. Then, we construct the new statements by replacing the specific component with its equivalent form or antecedent. At the proof tree level, our method merges two existing proof trees.
> </details>



![](figures/figures_23_0.png)

> 🔼 The figure shows the distribution of the number of variants synthesized for each tactic (rw and apply).
> <details>
> <summary>read the caption</summary>
> Figure 6: The distribution of the number of variants (only 99% of the data are visualized).
> </details>



![](figures/figures_24_0.png)

> 🔼 The figure illustrates the data synthesis pipeline that constructs formal theorems through symbolic mutation by merging two existing proof trees.
> <details>
> <summary>read the caption</summary>
> Figure 1: The overview of our synthesis pipeline. At the theorem level, we find invocable theorems that can be used to rewrite or apply to the assumptions or assertion of the candidate statement, such as the iff and implication rules about the Coprime. Then, we construct the new statements by replacing the specific component with its equivalent form or antecedent. At the proof tree level, our method merges two existing proof trees.
> </details>



![](figures/figures_27_0.png)

> 🔼 This figure illustrates the Alchemy data synthesis pipeline, showing how it constructs new theorems by symbolically mutating existing ones at both the theorem and proof tree levels.
> <details>
> <summary>read the caption</summary>
> Figure 1: The overview of our synthesis pipeline. At the theorem level, we find invocable theorems that can be used to rewrite or apply to the assumptions or assertion of the candidate statement, such as the iff and implication rules about the Coprime. Then, we construct the new statements by replacing the specific component with its equivalent form or antecedent. At the proof tree level, our method merges two existing proof trees.
> </details>



![](figures/figures_29_0.png)

> 🔼 The figure illustrates the Alchemy data synthesis pipeline, showing how symbolic manipulation of existing theorems and proofs generates new theorems.
> <details>
> <summary>read the caption</summary>
> Figure 1: The overview of our synthesis pipeline. At the theorem level, we find invocable theorems that can be used to rewrite or apply to the assumptions or assertion of the candidate statement, such as the iff and implication rules about the Coprime. Then, we construct the new statements by replacing the specific component with its equivalent form or antecedent. At the proof tree level, our method merges two existing proof trees.
> </details>



![](figures/figures_31_0.png)

> 🔼 The figure illustrates the data synthesis pipeline, showing how new theorems are constructed from existing ones through symbolic manipulation at the theorem level and proof tree merging.
> <details>
> <summary>read the caption</summary>
> Figure 1: The overview of our synthesis pipeline. At the theorem level, we find invocable theorems that can be used to rewrite or apply to the assumptions or assertion of the candidate statement, such as the iff and implication rules about the Coprime. Then, we construct the new statements by replacing the specific component with its equivalent form or antecedent. At the proof tree level, our method merges two existing proof trees.
> </details>



</details>



<details>
<summary>More on charts
</summary>


![](charts/charts_10_1.png "🔼 Figure 4: Influence of the quantity of synthesized data points.")

> 🔼 The chart shows the relationship between the number of synthesized state-tactic pairs and the number of proved theorems on the novel_premises split of Leandojo benchmark.
> <details>
> <summary>read the caption</summary>
> Figure 4: Influence of the quantity of synthesized data points.
> </details>


![](charts/charts_31_0.png "🔼 Figure 13: The performance of models fine-tuned on different SFT datasets on novel_premises split. a) Mathlib-train; b) Mathlib-train + rw; c) Mathlib-train + apply; d) Mathlib-train + rw + apply.")

> 🔼 The chart displays the performance of models fine-tuned on different synthetic data sets on the novel premises split of the Leandojo benchmark.
> <details>
> <summary>read the caption</summary>
> Figure 13: The performance of models fine-tuned on different SFT datasets on novel_premises split. a) Mathlib-train; b) Mathlib-train + rw; c) Mathlib-train + apply; d) Mathlib-train + rw + apply.
> </details>


![](charts/charts_31_1.png "🔼 Figure 14: a) The distribution of theorems proved by different LLMs; b) The distribution of tactics used in the proved theorems.")

> 🔼 The chart displays the distribution of theorems solved by different LLMs and the distribution of tactics used in those solutions.
> <details>
> <summary>read the caption</summary>
> Figure 14: a) The distribution of theorems proved by different LLMs; b) The distribution of tactics used in the proved theorems.
> </details>


![](charts/charts_32_0.png "🔼 Figure 15: The distribution of used tactics for Llama-3-8b fine-tuned on different SFT datasets to prove miniF2F. a) Mathlib-train; b) Mathlib-train + rw; c) Mathlib-train + apply; d) Mathlib-train + rw + apply.")

> 🔼 The chart displays the distribution of tactics used by Llama-3-8b, fine-tuned with different combinations of training data (Mathlib-train, rw, apply) to solve miniF2F problems.
> <details>
> <summary>read the caption</summary>
> Figure 15: The distribution of used tactics for Llama-3-8b fine-tuned on different SFT datasets to prove miniF2F. a) Mathlib-train; b) Mathlib-train + rw; c) Mathlib-train + apply; d) Mathlib-train + rw + apply.
> </details>


![](charts/charts_32_1.png "🔼 Figure 14: a) The distribution of theorems proved by different LLMs; b) The distribution of tactics used in the proved theorems.")

> 🔼 The chart displays the distribution of theorems proved by different LLMs and the distribution of tactics used in those proved theorems.
> <details>
> <summary>read the caption</summary>
> Figure 14: a) The distribution of theorems proved by different LLMs; b) The distribution of tactics used in the proved theorems.
> </details>


![](charts/charts_32_2.png "🔼 Figure 14: a) The distribution of theorems proved by different LLMs; b) The distribution of tactics used in the proved theorems.")

> 🔼 The chart displays the distribution of theorems proven by different LLMs and the distribution of tactics used in those theorems.
> <details>
> <summary>read the caption</summary>
> Figure 14: a) The distribution of theorems proved by different LLMs; b) The distribution of tactics used in the proved theorems.
> </details>


![](charts/charts_32_3.png "🔼 Figure 14: a) The distribution of theorems proved by different LLMs; b) The distribution of tactics used in the proved theorems.")

> 🔼 Figure 14 shows the distribution of theorems solved by different LLMs and the distribution of tactics used in those solved theorems.
> <details>
> <summary>read the caption</summary>
> Figure 14: a) The distribution of theorems proved by different LLMs; b) The distribution of tactics used in the proved theorems.
> </details>


</details>



<details>
<summary>More on tables
</summary>


{{< table-caption >}}
<table id='1' style='font-size:14px'><tr><td>Methods</td><td>random</td><td>novel _premises</td><td>Search Budget</td></tr><tr><td>tidy</td><td>23.8</td><td>5.3</td><td>-</td></tr><tr><td>GPT-4</td><td>29.0</td><td>7.4</td><td>1 X 35</td></tr><tr><td>Reprover Yang et al. 2023</td><td>47.6</td><td>23.2</td><td>1 X 64</td></tr><tr><td>w/ retrieval</td><td>51.2</td><td>26.3</td><td>1 X 64</td></tr><tr><td>llmstep (Pythia 2.8b) Welleck & Saha 2023</td><td>47.6</td><td>-</td><td>1 X 32</td></tr><tr><td></td><td>50.1</td><td>-</td><td>2 X 32</td></tr><tr><td>Llama3-8b</td><td>58.22</td><td>38.52</td><td>1 X 32</td></tr><tr><td>Mathlib-train + rw</td><td>59.62 (+1.40)</td><td>42.13 (+3.62)</td><td>1 x 32</td></tr><tr><td>Mathlib-train + apply</td><td>58.84 (+0.62)</td><td>41.29 (+2.77)</td><td>1 x 32</td></tr><tr><td>Mathlib-train + rw + apply</td><td>59.82 (+1.60)</td><td>43.22 (+4.70)</td><td>1 x 32</td></tr><tr><td>deepseek-coder-7b-base-v1.5</td><td>57.7</td><td>39.24</td><td>1 x 32</td></tr><tr><td>Mathlib-train + rw</td><td>59.25 (+1.55)</td><td>42.98 (+3.74)</td><td>1 X 32</td></tr><tr><td>Mathlib-train + apply</td><td>58.68 (+0.98)</td><td>40.51 (+1.27)</td><td>1 X 32</td></tr><tr><td>Mathlib-train + rw + apply</td><td>60.39 (+2.69)</td><td>43.46 (+4.22)</td><td>1 X 32</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> Table 3 presents the results of the theorem proving experiments on the Mathlib benchmark, comparing the performance of models trained with different data combinations and search strategies.


{{< table-caption >}}
<table id='1' style='font-size:16px'><tr><td>Methods</td><td>random</td><td>novel_premises</td><td>random</td><td>novel_premises</td></tr><tr><td></td><td colspan="2">Llama3-8b</td><td colspan="2">deepseek-coder-base-7b-v1.5</td></tr><tr><td></td><td colspan="4">sft: mathlib-train</td></tr><tr><td>w/o cpt</td><td>58.22</td><td>38.52</td><td>57.70</td><td>39.24</td></tr><tr><td>rw</td><td>59.56 (+1.35)</td><td>42.56 (+4.04)</td><td>58.74 (+1.04)</td><td>40.69 (+1.45)</td></tr><tr><td>apply</td><td>58.42 (+0.21)</td><td>41.29 (+2.77)</td><td>58.58 (+0.88)</td><td>40.02 (+0.78)</td></tr><tr><td>rw + apply</td><td>59.72 (+1.50)</td><td>42.19 (+3.68)</td><td>59.67 (+1.97)</td><td>41.65 (+2.41)</td></tr><tr><td></td><td colspan="4">sft: mathlib-train + rw</td></tr><tr><td>w/o cpt</td><td>57.85</td><td>41.59</td><td>58.63</td><td>41.05</td></tr><tr><td>rw</td><td>59.62 (+1.76)</td><td>42.13 (+0.54)</td><td>59.25 (+0.62)</td><td>42.98 (+1.93)</td></tr><tr><td></td><td colspan="4">sft: mathlib-train + apply</td></tr><tr><td>w/o cpt</td><td>56.71</td><td>40.02</td><td>57.96</td><td>41.17</td></tr><tr><td>apply</td><td>58.84 (+2.13)</td><td>41.29 (+1.27)</td><td>58.68 (+0.73)</td><td>40.51 (-0.66)</td></tr><tr><td></td><td colspan="4">sft: mathlib-train + rw + apply</td></tr><tr><td>w/o cpt</td><td>58.53</td><td>41.95</td><td>58.37</td><td>42.92</td></tr><tr><td>rw + apply</td><td>59.82 (+1.30)</td><td>43.22 (+1.27)</td><td>60.39 (+2.02)</td><td>43.46 (+0.54)</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> This table shows the effectiveness of continual pre-training on the performance of LLMs across diverse supervised fine-tuning settings, demonstrating a positive influence of continual pre-training on the theorem-proving ability of LLMs.


{{< table-caption >}}
<table id='10' style='font-size:16px'><tr><td>Methods</td><td>miniF2F-test</td><td>Correct/Total</td><td>rw</td><td>apply</td><td>norm_num</td><td>linarith</td></tr><tr><td>Mathlib-train</td><td>34.01</td><td>83/244</td><td>16.10</td><td>0.00</td><td>27.12</td><td>16.95</td></tr><tr><td>Mathlib-train + rw</td><td>35.24</td><td>86/244</td><td>18.75</td><td>0.78</td><td>14.84</td><td>21.88</td></tr><tr><td>Mathlib-train + apply</td><td>36.07</td><td>88/244</td><td>8.87</td><td>2.42</td><td>20.16</td><td>15.63</td></tr><tr><td>Mathlib-train + rw + apply</td><td>36.48 (+2.47)</td><td>89/244</td><td>12.31</td><td>0.77</td><td>26.92</td><td>16.92</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> Table 5 presents the results of the miniF2F benchmark, showing the performance of different model variations and the proportion of specific tactics used in successful proofs.


{{< table-caption >}}
<table id='0' style='font-size:14px'><tr><td>24</td><td>"next_state" : next_state. error if isinstance (next_state, LeanError) else next_state.pp,</td></tr><tr><td>25</td><td>" rule" : inst</td></tr><tr><td>26</td><td>}</td></tr><tr><td>27</td><td>if isinstance (next_state, LeanError) :</td></tr><tr><td>28</td><td>if mode == " implication " \</td></tr><tr><td>29</td><td>and "unsolved goals" in next_state · error :</td></tr><tr><td>30</td><td>res · append (state_info)</td></tr><tr><td>31</td><td>elif isinstance (next_state, TacticState) :</td></tr><tr><td>32</td><td>res · append (state_info)</td></tr><tr><td>33</td><td>return res</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> Table 2 presents the number of theorems at different stages of the data synthesis pipeline, showing the expansion achieved by the method and the conversion ratio from potential to verified theorems.


{{< table-caption >}}
<table id='0' style='font-size:14px'><tr><td>Finset.multiplicativeEnergy_mono right</td></tr><tr><td>theorem multiplicativeEnergy mono right (ht : t1 드 t2) : multiplicativeEnergy s t1 ≤ multiplicativeEnergy s t2 := multiplicativeEnergy_ mono Subset.rfl ht</td></tr><tr><td>example (ht : t1 n t2 = t1) : multiplicativeEnergy s t1 ≤ multiplicativeEnergy s t2:= have ht : t1 드 t2 := by rw [Finset.inter_ eq_left] at ht;exact ht multiplicativeEnergy_ mono Subset.rfl ht</td></tr><tr><td>example (ht : t1.val n t2.val) : multiplicativeEnergy s t1 ≤ multiplicativeEnergy s t2:= have ht : t1 드 t2 := by rw [←Finset.subset def] at ht;exact ht multiplicativeEnergy_ mono Subset.rfl ht</td></tr><tr><td>example (ht : t1 드 t2) : max (multiplicativeEnergy s t2) (multiplicativeEnergy s t1) = multiplicativeEnergy s t := have : multiplicativeEnergy s t1 ≤ multiplicativeEnergy s t2 := multiplicativeEnergy mono Subset.rfl ht by rw [←max_eq_ left_ iff] at this;exact this</td></tr><tr><td>Multiset.card _le_ card</td></tr><tr><td>theorem card le card {s t : Multiset a} (h : s⌀t) : card s ≤ card t := leInductionOn h Sublist.length_le</td></tr><tr><td>example {s t : Multiset a} (h : s⌀t) : A {c : N}, card t<c → card s < c:= have : card s ≤ card t := leInductionOn h Sublist.length le by rw [←forall lt iff_ le'] at this;exact this</td></tr><tr><td>example {s t : Multiset a} (h : s≤t) : card s コ card t = card s:= have : card s ≤ card t := leInductionOn h Sublist.length_ le by rw [←inf_eq_ left] at this;exact this</td></tr><tr><td>example {s t : Multiset a} (h : s≤t) : card s = card t V card s < card t:= have : card s ≤ card t := leInductionOn h Sublist.length_le by rw [le iff eq_or lt] at this;exact this</td></tr><tr><td>Nat.one_ lt_pow'</td></tr><tr><td>theorem one lt_pow' (n m : N) : 1 < (m + 2)^(n+ 1) := one 1t _pow (n + 1) (m + 2) n.succ_ne zero (Nat.lt_ of_sub_eq_succ rfl)</td></tr><tr><td>example (n m : N) : (m +2) へ (n+1)#0A(m+2)^(n+1)#1= have : 1 < (m + 2) ^ (n + 1) := one lt_pow (n + 1) (m + 2) n.succ_ne zero (Nat.lt_of_sub eq_succ rfl) by rw [Natione_It iff_ne_zero_and ne_one] at this;exact this example (n m : N) : (m +2) ^(ⓝ+1)<(m+2)^(ⓝ+1) * (m+2)^(ⓝ+1)= have : 1 < (m + 2) 스 (n+ 1) := one lt_pow (n + 1) (m + 2) n.succ ne zero (Nat.lt_of_sub_eq_succ rfl) by rw [←Nat.lt_mul_self_ iff] at this;exact this</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> The table presents the number of theorems at different stages of the data synthesis process, showing a significant increase in the number of theorems after verification.


{{< table-caption >}}
<table id='0' style='font-size:16px'><tr><td>StrictMonoOn.mapsTo_Ioc</td></tr><tr><td>lemma StrictMonoOn.mapsTo_Ioc (h : StrictMonoOn f (Icc a b)) : MapsTo f (Ioc a b) (Ioc (fa) (fb)) := fun c hc → 〈h (left_ mem Icc.2 < hc.1.le.trans hc.2) (Ioc_subset Icc⌀ self hc) hc.1, h.monotoneOn (Ioc_subset_ Icc_self hc) (right_ mem Icc.2 V hc.1.le.trans hc.2) hc.2)</td></tr><tr><td>example (h : StrictMonoOn f (Icc a b) ↔ True) : MapsTo f (Ioc a b) (Ioc (fa) (fb)):= have h : StrictMonoOn f (Icc a b) := by apply of_iff_ true; assumption fun c hc → 〈h (left_ mem Icc.2 <| hc.1.le.trans hc.2) (Ioc_subset_ Icc_ self hc) hc.1, h.monotoneOn (Ioc_subset_Icc_self hc) (right_mem_Icc.2 ◁ hc.1.le.trans hc.2) hc.2)</td></tr><tr><td>example (H : � (b_1 : Prop), (StrictMonoOn f (Icc a b) → b_1)→ StrictMonoOn f (Icc a b)) : MapsTo f (Ioc ab) (Ioc (fa) (fb)):= have h : StrictMonoOn f (Icc a b) := by apply peirce'; assumption ... example (h : Icc a b E {x  StrictMonoOn fx}) : MapsTo f (Ioc a b) (Ioc (fa) (fb)):= have h : StrictMonoOn f (Icc a b) := by apply Membership.mem.out; assumption ...</td></tr><tr><td>PNat.XgcdType.reduce_ a</td></tr><tr><td>theorem reduce_a {u : XgcdType} (h : u.r = 0) : u.reduce = u.finish := by rw [reduce] exact if _pos h example {u : XgcdType} (h : 0|ru) : u.reduce = u.finish:= by have h : u.r = 0 := by apply Nat.eq_ zero_of_ zero_dvd; assumption rw [reduce] exact if_pos h</td></tr><tr><td>example {u : XgcdType} (H : u.bp + 1 I u.ap + 1) : u.reduce = u.finish:= by have h : u.r = 0 := by apply Nat.mod_eq_zero_of_dvd; assumption ... example {u : XgcdType} (n : N) (H : Nat.gcd (ru) n = 0) : u.reduce = u.finish:= by have h : u.r = 0 := by apply Nat.eq_ zero_ of_gcd_eq_zero_left<;> assumption</td></tr><tr><td>Ordnode.not le_ delta</td></tr><tr><td>theorem not le delta {s} (H : 1 ≤s) : �S ≤ delta * 0 := not le of gt H</td></tr><tr><td>example {s} (h : 0<s) (a : 1 ls) : js ≤ delta * 0:= have H : 1 ≤s := by apply Nat.le_of_dvd<;> assumption not_le_of_gt H example {s} (n : N) (H1 : s In) (H2 : 0<n) : ーs ≤ delta * 0:= have H : 1 ⌀s = by apply Nat.pos_of_dvd_of_pos<;> assumption ... example {s} (1 : List N) (p : List.Pairwise LE.le (1 :: 1)) (a : sE1) : �S ≤ delta * 0:= have H : 1 ⌀s = by apply List.rel of pairwise_cons<;> assumption</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> Table 2 presents the number of theorems at different stages of the data synthesis pipeline, showing a significant increase in the number of theorems after verification.


{{< table-caption >}}
<table id='1' style='font-size:14px'><tr><td>Methods</td><td>random</td><td>novel_premises</td><td>Search Budget</td></tr><tr><td>Llama3-8b</td><td></td><td></td><td></td></tr><tr><td>Mathlib-train</td><td>58.22</td><td>38.52</td><td>1 x 32</td></tr><tr><td>rw tactic</td><td></td><td></td><td></td></tr><tr><td>Mathlib-train + rw</td><td>57.85 (-0.37)</td><td>41.59 (+3.07)</td><td>1 x 32</td></tr><tr><td>Mathlib-train + have</td><td>58.27 (+0.05)</td><td>41.29 (+2.77)</td><td>1 x 32</td></tr><tr><td>Mathlib-train + rw + have</td><td>57.96 (-0.26)</td><td>41.53 (+3.01)</td><td>1 x 32</td></tr><tr><td>apply tactic</td><td></td><td></td><td></td></tr><tr><td>Mathlib-train + apply</td><td>56.71 (-1.51)</td><td>40.02 (+1.51)</td><td>1 x 32</td></tr><tr><td>Mathlib-train + have</td><td>57.44 (-0.78)</td><td>39.24 (+0.72)</td><td>1 x 32</td></tr><tr><td>Mathlib-train + apply + have</td><td>57.23 (-0.99)</td><td>38.34 (-0.18)</td><td>1 x 32</td></tr><tr><td>both tactic</td><td></td><td></td><td></td></tr><tr><td>mathlib-train + rw + apply</td><td>58.53 (+0.31)</td><td>41.95 (+3.44)</td><td>1 x 32</td></tr><tr><td>deepseek-coder-7b-base-v1.5</td><td></td><td></td><td></td></tr><tr><td>Mathlib-train</td><td>57.7</td><td>39.24</td><td>1 x 32</td></tr><tr><td>rw tactic</td><td></td><td></td><td></td></tr><tr><td>Mathlib-train + rw</td><td>58.63 (+0.93)</td><td>41.05 (+1.81)</td><td>1 x 32</td></tr><tr><td>Mathlib-train + have</td><td>58.11 (+0.41)</td><td>39.06 (-0.18)</td><td>1 x 32</td></tr><tr><td>Mathlib-train + rw + have</td><td>58.74 (+1.04)</td><td>40.57 (+1.33)</td><td>1 x 32</td></tr><tr><td>apply tactic</td><td></td><td></td><td></td></tr><tr><td>Mathlib-train + apply</td><td>57.96 (+0.26)</td><td>41.17 (+1.93)</td><td>1 x 32</td></tr><tr><td>Mathlib-train + have</td><td>57.02 (-0.68)</td><td>39.66 (+0.42)</td><td>1 x 32</td></tr><tr><td>Mathlib-train + apply + have</td><td>58.16 (+0.46)</td><td>39.78 (+0.54)</td><td>1 x 32</td></tr><tr><td>both tactic</td><td></td><td></td><td></td></tr><tr><td>Mathlib-train + rw + apply</td><td>58.37 (+0.67)</td><td>42.92 (+3.68)</td><td>1 x 32</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> Table 6 presents the performance of Llama-3-8b and deepseek-coder-7b-base-v1.5 models fine-tuned with different combinations of additional data (rw, apply, have tactics) on the random and novel premises splits of the Leandojo benchmark.


{{< table-caption >}}
<table id='3' style='font-size:20px'><tr><td>Methods</td><td>miniF2F-test</td></tr><tr><td>Llama-3-8b</td><td>34.01</td></tr><tr><td>deepseek-coder-base-7b-v1.5</td><td>37.70</td></tr><tr><td>deepseek-math-7b-base</td><td>34.42</td></tr><tr><td>llemma-7b</td><td>32.38</td></tr><tr><td>mistral-7b</td><td>32.38</td></tr><tr><td>internlm2-math-7b</td><td>36.06</td></tr><tr><td>Combination</td><td>40.98</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> Table 3 presents the performance of different models on the Mathlib benchmark, comparing models fine-tuned solely on Mathlib-train against those also pre-trained and fine-tuned with additional synthetic data generated using the rw and apply tactics.


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
{{< /gallery >}}