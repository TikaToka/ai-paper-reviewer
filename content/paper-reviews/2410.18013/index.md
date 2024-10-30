---
title: "Scalable Ranked Preference Optimization for Text-to-Image Generation"
summary: "Researchers created a scalable training method for text-to-image models using synthetic, ranked preference data, significantly improving both visual quality and prompt-following."
categories: ["AI Generated"]
tags: ["🔖 24-10-23", ]
showSummary: true
date: 2024-10-23
draft: false
---

{{< keyword >}} 2410.18013 {{< /keyword >}}

### TL;DR


{{< lead >}}

This research tackles the challenges of aligning text-to-image (T2I) models with human preferences, a process typically hindered by the high cost and time required for large-scale human annotation of image datasets.  The authors propose a novel approach using a synthetically generated preference dataset and a new optimization technique, RankDPO, to overcome these limitations.  Instead of relying on expensive human feedback, they generate images using multiple T2I models and rank them according to a pre-trained reward function.  This synthetic dataset is then used to train the models using RankDPO, which enhances DPO methods by incorporating richer information from the ranking feedback.  Experiments demonstrate that this approach improves both prompt-following and visual quality of the generated images, achieving state-of-the-art results with significantly lower computational costs compared to existing methods.  This work offers a scalable and cost-effective solution for improving T2I model performance.

{{< /lead >}}


{{< button href="https://arxiv.org/abs/2410.18013" target="_self" >}}
{{< icon "link" >}} &nbsp; read the paper on arXiv
{{< /button >}}
<br><br>
{{< button href="https://huggingface.co/papers/2410.18013" target="_self" >}}
{{< icon "hf-logo" >}} &nbsp; on Hugging Face
{{< /button >}}

#### Why does it matter?
This paper is crucial for researchers in text-to-image generation due to its introduction of a scalable and cost-effective method for training these models.  The use of synthetic data removes the bottleneck of expensive human annotation, and the proposed RankDPO method improves both prompt-following and visual quality, significantly advancing the field. This opens avenues for improved model safety and efficiency.
#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} Synthetically generated, ranked preference data can effectively train text-to-image models, eliminating costly human annotation. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} The RankDPO method, leveraging ranking feedback, outperforms existing preference optimization techniques in terms of both performance and efficiency. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} This approach offers a scalable solution for creating preference datasets that are both cost-effective and adaptable to rapidly evolving text-to-image model advancements. {{< /typeit >}}
{{< /alert >}}

------
#### Visual Insights



![](https://ai-paper-reviewer.com/2410.18013/figures_5_0.png)

> 🔼 The figure shows a schematic overview of the two main components of the proposed method: (A) a synthetically labeled preference dataset generation process (Syn-Pic) and (B) a ranking-based preference optimization method (RankDPO).
> <details>
> <summary>read the caption</summary>
> Figure 2: Overview of our two novel components: (A) Syn-Pic and (B) RankDPO. Left illustrates the pipeline to generate a synthetically ranked preference dataset. It starts by collecting prompts and generating images using the same prompt for different T2I models. Next, we calculate the overall preference score using Reward models (e.g., PickScore, ImageReward). Finally, we rank these images in the decreasing order of preference scores. Right: Given true preference rankings for generated images per prompt, we first obtain predicted ranking by current model checkpoint using scores si (see Eq. 5). In this instance, although the predicted ranking is inverse of the true rankings, the ranks (1, 4) obtains a larger penalty than the ranks (2, 3). This penalty is added to our ranking loss through DCG weights (see Eq. 6). Thus, by optimizing θ with Ranking Loss (see Eq. 7), the updated model addresses the incorrect rankings (1,4). This procedure is repeated over the training process, where the rankings induced by the model aligns with the labelled preferences.
> </details>





![](https://ai-paper-reviewer.com/2410.18013/charts_7_0.png)

> 🔼 The chart displays the win rates of RankDPO, DPO-SDXL, and SDXL in a user preference study, showing RankDPO's superior performance.
> <details>
> <summary>read the caption</summary>
> Figure 3: Win rates of our approach compared to DPO-SDXL and SDXL on human evaluation.
> </details>





{{< table-caption >}}
<br><table id='2' style='font-size:14px'><tr><td>Model</td><td>Mean ↑</td><td>Single ↑</td><td>Two ↑</td><td>Counting ↑</td><td>Colors ↑</td><td>Position ↑</td><td>Color Attribution ↑</td></tr><tr><td>SD v2.1</td><td>0.50</td><td>0.98</td><td>0.51</td><td>0.44</td><td>0.85</td><td>0.07</td><td>0.17</td></tr><tr><td>PixArt-�</td><td>0.48</td><td>0.98</td><td>0.50</td><td>0.44</td><td>0.80</td><td>0.08</td><td>0.07</td></tr><tr><td>PixArt-�</td><td>0.53</td><td>0.99</td><td>0.65</td><td>0.46</td><td>0.82</td><td>0.12</td><td>0.12</td></tr><tr><td>DALL-E 2</td><td>0.52</td><td>0.94</td><td>0.66</td><td>0.49</td><td>0.77</td><td>0.10</td><td>0.19</td></tr><tr><td>DALL-E 3</td><td>0.67</td><td>0.96</td><td>0.87</td><td>0.47</td><td>0.83</td><td>0.43</td><td>0.45</td></tr><tr><td>SDXL</td><td>0.55</td><td>0.98</td><td>0.74</td><td>0.39</td><td>0.85</td><td>0.15</td><td>0.23</td></tr><tr><td>SDXL (Ours)</td><td>0.61</td><td>1.00</td><td>0.86</td><td>0.46</td><td>0.90</td><td>0.14</td><td>0.29</td></tr><tr><td>SD3-Medium</td><td>0.70</td><td>1.00</td><td>0.87</td><td>0.63</td><td>0.84</td><td>0.28</td><td>0.58</td></tr><tr><td>SD3-Medium (Ours)</td><td>0.74</td><td>1.00</td><td>0.90</td><td>0.72</td><td>0.87</td><td>0.31</td><td>0.66</td></tr></table>{{< /table-caption >}}

> 🔼 Table 1 presents a quantitative comparison of different models' performance on the GenEval benchmark, highlighting the improvements achieved by RankDPO on several key categories.
> <details>
> <summary>read the caption</summary>
> Table 1: Quantitative Results on GenEval. RankDPO improves results on most categories, notably 'two objects', 'counting', and 'color attribution' for SDXL and SD3-Medium.
> </details>



### More visual insights

<details>
<summary>More on figures
</summary>


![](https://ai-paper-reviewer.com/2410.18013/figures_9_0.png)

> 🔼 The figure shows a qualitative comparison of images generated by different preference optimization methods for the same set of prompts, highlighting the superior prompt following and image quality achieved by the proposed RankDPO method.
> <details>
> <summary>read the caption</summary>
> Figure 4: Comparison among different preference optimization methods and RankDPO for SDXL. The results illustrate that we generate images with better prompt alignment and aesthetic quality.
> </details>



![](https://ai-paper-reviewer.com/2410.18013/figures_17_0.png)

> 🔼 The figure shows a qualitative comparison of image generation results from different models (SDXL and SD3) with and without the proposed approach, highlighting improvements in prompt following and visual quality.
> <details>
> <summary>read the caption</summary>
> Figure 1: Our approach, trained on a synthetic preference dataset with a ranking objective in the preference optimization, improves prompt following and visual quality for SDXL (Podell et al., 2023) and SD3-Medium (Esser et al., 2024), without requiring any manual annotations.
> </details>



![](https://ai-paper-reviewer.com/2410.18013/figures_19_0.png)

> 🔼 The figure shows a comparison of text-to-image generation results using different models (SDXL and SD3) with and without the proposed method, illustrating improved prompt following and visual quality.
> <details>
> <summary>read the caption</summary>
> Figure 1: Our approach, trained on a synthetic preference dataset with a ranking objective in the preference optimization, improves prompt following and visual quality for SDXL (Podell et al., 2023) and SD3-Medium (Esser et al., 2024), without requiring any manual annotations.
> </details>



![](https://ai-paper-reviewer.com/2410.18013/figures_19_1.png)

> 🔼 The figure shows image generation results from SDXL and SD3-Medium models before and after applying the proposed approach, highlighting improved prompt following and visual quality.
> <details>
> <summary>read the caption</summary>
> Figure 1: Our approach, trained on a synthetic preference dataset with a ranking objective in the preference optimization, improves prompt following and visual quality for SDXL (Podell et al., 2023) and SD3-Medium (Esser et al., 2024), without requiring any manual annotations.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
<br><table id='4' style='font-size:18px'><tr><td rowspan="2">Model</td><td colspan="3">Attribute Binding</td><td colspan="2">Object Relationship</td><td rowspan="2">Complex↑</td></tr><tr><td>Color ↑</td><td>Shape↑</td><td>Texture↑</td><td>Spatial↑</td><td>Non-Spatial↑</td></tr><tr><td>SD1.4</td><td>37.65</td><td>35.76</td><td>41.56</td><td>12.46</td><td>30.79</td><td>30.80</td></tr><tr><td>PixArt-a</td><td>68.86</td><td>55.82</td><td>70.44</td><td>20.82</td><td>31.79</td><td>41.17</td></tr><tr><td>DALL-E 2</td><td>57.50</td><td>54.64</td><td>63.74</td><td>12.83</td><td>30.43</td><td>36.96</td></tr><tr><td>SDXL</td><td>58.79</td><td>46.87</td><td>52.99</td><td>21.31</td><td>31.19</td><td>32.37</td></tr><tr><td>SDXL (Ours)</td><td>72.33</td><td>56.93</td><td>69.67</td><td>24.53</td><td>31.33</td><td>45.47</td></tr><tr><td>SD3-Medium</td><td>81.31</td><td>59.06</td><td>75.91</td><td>34.30</td><td>31.13</td><td>47.93</td></tr><tr><td>SD3-Medium (Ours)</td><td>83.26</td><td>63.45</td><td>78.72</td><td>36.49</td><td>31.25</td><td>48.65</td></tr></table>{{< /table-caption >}}
> 🔼 Table 2 presents a quantitative comparison of the performance of SDXL and SD3-Medium models, before and after applying RankDPO, across various attributes on the T2I-CompBench benchmark.
> <details>
> <summary>read the caption</summary>
> Table 2: Quantitative Results on T2I-CompBench. RankDPO provides consistent improvements on all categories for both SDXL and SD3-Medium.
> </details>

{{< table-caption >}}
<table id='2' style='font-size:14px'><tr><td>Model Name</td><td colspan="2">Prompt Alignment</td><td>Visual Quality</td></tr><tr><td></td><td>DSG Score</td><td>VQA Score</td><td>Q-Align Score</td></tr><tr><td>SD1.5</td><td>63.18</td><td>-</td><td>-</td></tr><tr><td>SD2.1</td><td>68.09</td><td>-</td><td>-</td></tr><tr><td>Pixart-�</td><td>71.11</td><td>-</td><td>-</td></tr><tr><td>Playgroundv2</td><td>74.54</td><td>-</td><td>-</td></tr><tr><td>DALL-E 3</td><td>83.50</td><td>-</td><td>-</td></tr><tr><td>SDXL</td><td>74.65</td><td>84.33</td><td>0.72</td></tr><tr><td>DPO-SDXL</td><td>76.74</td><td>85.67</td><td>0.74</td></tr><tr><td>MaPO-SDXL</td><td>74.53</td><td>84.54</td><td>0.80</td></tr><tr><td>SPO-SDXL</td><td>74.73</td><td>84.71</td><td>0.82</td></tr><tr><td>SDXL (Ours)</td><td>79.26</td><td>87.52</td><td>0.81</td></tr><tr><td>SD3-Medium</td><td>85.54</td><td>90.58</td><td>0.67</td></tr><tr><td>SD3-Medium (Ours)</td><td>86.78</td><td>90.99</td><td>0.68</td></tr></table>{{< /table-caption >}}
> 🔼 Table 3 presents a quantitative comparison of different models' performance on the DPG-Bench benchmark, evaluating both prompt alignment and visual quality using various metrics.
> <details>
> <summary>read the caption</summary>
> Table 3: Quantitative results on DPG-Bench. DSG (Cho et al., 2024) and VQAScore (Lin et al., 2024) measure prompt following using VQA models while Q-Align (Wu et al., 2024a) measures visual quality using multimodal LLMs.
> </details>

{{< table-caption >}}
<table id='4' style='font-size:14px'><tr><td>Model Name</td><td colspan="2">Prompt Alignment</td><td>Visual Quality</td></tr><tr><td></td><td>DSG Score</td><td>VQA Score</td><td>Q-Align Score</td></tr><tr><td>SDXL</td><td>74.65</td><td>84.33</td><td>0.72</td></tr><tr><td>DPO (Random Labelling)</td><td>75.66</td><td>84.42</td><td>0.74</td></tr><tr><td>DPO (HPSv2)</td><td>78.04</td><td>86.22</td><td>0.83</td></tr><tr><td>DPO (Pick-a-Picv2)</td><td>76.74</td><td>85.67</td><td>0.74</td></tr><tr><td>DPO (5 Rewards)</td><td>78.84</td><td>86.27</td><td>0.81</td></tr><tr><td>RankDPO (Only SDXL)</td><td>78.40</td><td>86.76</td><td>0.74</td></tr><tr><td>RankDPO</td><td>79.26</td><td>87.52</td><td>0.81</td></tr></table>{{< /table-caption >}}
> 🔼 Table 4 shows the impact of different preference labeling methods and data quality on the final model's performance, measured by prompt alignment and visual quality.
> <details>
> <summary>read the caption</summary>
> Table 4: Effect of the preference labelling and data quality on the final model.
> </details>

{{< table-caption >}}
<table id='6' style='font-size:14px'><tr><td>Model Name</td><td colspan="2">Prompt Alignment</td><td>Visual Quality</td></tr><tr><td></td><td>DSG Score</td><td>VQA Score</td><td>Q-Align Score</td></tr><tr><td>SDXL</td><td>74.65</td><td>84.33</td><td>0.72</td></tr><tr><td>Supervised Fine-Tuning</td><td>76.56</td><td>85.45</td><td>0.78</td></tr><tr><td>Weighted Fine-Tuning</td><td>77.02</td><td>85.55</td><td>0.79</td></tr><tr><td>DPO</td><td>78.84</td><td>86.27</td><td>0.81</td></tr><tr><td>DPO + Gain Weights</td><td>79.15</td><td>87.43</td><td>0.82</td></tr><tr><td>RankDPO (Ours)</td><td>79.26</td><td>87.52</td><td>0.81</td></tr></table>{{< /table-caption >}}
> 🔼 Table 3 presents a quantitative comparison of different models' performance on the DPG-Bench benchmark, evaluating both prompt alignment and visual quality.
> <details>
> <summary>read the caption</summary>
> Table 3: Quantitative results on DPG-Bench. DSG (Cho et al., 2024) and VQAScore (Lin et al., 2024) measure prompt following using VQA models while Q-Align (Wu et al., 2024a) measures visual quality using multimodal LLMs.
> </details>

{{< table-caption >}}
<table id='2' style='font-size:14px'><tr><td>" wombat. .. martini</td><td>" orange fruit ·</td><td>" 'hello' ·· colored ·</td><td>" bow raccoon...</td><td>" yellow rabbit...</td><td>" donkey. - clown</td></tr><tr><td>glass.. . open laptop...</td><td>donning... brown cowboy hat. "</td><td>fur... frame... fluffy material "</td><td>tie... wooden cane... dark garbage bag...</td><td>meadow.. . red-framed glasses... "</td><td>costume... stands... podium...</td></tr></table>{{< /table-caption >}}
> 🔼 Table 1 presents a quantitative comparison of different models' performance on the GenEval benchmark, highlighting the improvements achieved by RankDPO, especially in categories involving multiple objects, counting, and color attribution.
> <details>
> <summary>read the caption</summary>
> Table 1: Quantitative Results on GenEval. RankDPO improves results on most categories, notably 'two objects', 'counting', and 'color attribution' for SDXL and SD3-Medium.
> </details>

{{< table-caption >}}
<table id='1' style='font-size:16px'><tr><td>Jaemin Cho, Yushi Hu, Roopal Garg, Peter Anderson, Ranjay Krishna, Jason Baldridge, Mohit Bansal, Jordi Pont-Tuset, and Su Wang. Davidsonian scene graph: Improving reliability in fine- grained evaluation for text-image generation. In ICLR, 2024.</td></tr><tr><td>Paul F Christiano, Jan Leike, Tom Brown, Miljan Martic, Shane Legg, and Dario Amodei. Deep reinforcement learning from human preferences. NIPS, 2017.</td></tr><tr><td>Kevin Clark, Paul Vicol, Kevin Swersky, and David J Fleet. Directly fine-tuning diffusion models on differentiable rewards. In ICLR, 2024.</td></tr><tr><td>Thomas Coste, Usman Anwar, Robert Kirk, and David Krueger. Reward model ensembles help mitigate overoptimization. In ICLR, 2024.</td></tr><tr><td>Xiaoliang Dai, Ji Hou, Chih-Yao Ma, Sam Tsai, Jialiang Wang, Rui Wang, Peizhao Zhang, Simon Vandenhende, Xiaofang Wang, Abhimanyu Dubey, et al. Emu: Enhancing image generation models using photogenic needles in a haystack. arXiv preprint arXiv:2309.15807, 2023.</td></tr><tr><td>Fei Deng, Qifei Wang, Wei Wei, Matthias Grundmann, and Tingbo Hou. Prdp: Proximal reward difference prediction for large-scale reward finetuning of diffusion models. In CVPR, 2024.</td></tr><tr><td>Carles Domingo-Enrich, Michal Drozdzal, Brian Karrer, and Ricky TQ Chen. Adjoint matching: Fine-tuning flow and diffusion generative models with memoryless stochastic optimal control. arXiv preprint arXiv:2409.08861, 2024.</td></tr><tr><td>Patrick Esser, Sumith Kulal, Andreas Blattmann, Rahim Entezari, Jonas M�ller, Harry Saini, Yam Levi, Dominik Lorenz, Axel Sauer, Frederic Boesel, et al. Scaling rectified flow transformers for high-resolution image synthesis. arXiv preprint arXiv:2403.03206, 2024.</td></tr><tr><td>Kawin Ethayarajh, Winnie Xu, Niklas Muennighoff, Dan Jurafsky, and Douwe Kiela. Kto: Model alignment as prospect theoretic optimization. arXiv preprint arXiv:2402.01306, 2024.</td></tr><tr><td>Luca Eyring, Shyamgopal Karthik, Karsten Roth, Alexey Dosovitskiy, and Zeynep Akata. Reno: Enhancing one-step text-to-image models through reward-based noise optimization. In NeurIPS, 2024.</td></tr><tr><td>Ying Fan, Olivia Watkins, Yuqing Du, Hao Liu, Moonkyung Ryu, Craig Boutilier, Pieter Abbeel, Mohammad Ghavamzadeh, Kangwook Lee, and Kimin Lee. Reinforcement learning for fine- tuning text-to-image diffusion models. NeurIPS, 2023.</td></tr><tr><td>Samir Yitzhak Gadre, Gabriel Ilharco, Alex Fang, Jonathan Hayase, Georgios Smyrnis, Thao Nguyen, Ryan Marten, Mitchell Wortsman, Dhruba Ghosh, Jieyu Zhang, et al. Datacomp: In search of the next generation of multimodal datasets. NeurIPS, 2023.</td></tr><tr><td>Dhruba Ghosh, Hanna Hajishirzi, and Ludwig Schmidt. Geneval: An object-focused framework for evaluating text-to-image alignment. In NeurIPS, 2023.</td></tr><tr><td>Shane Griffith, Kaushik Subramanian, Jonathan Scholz, Charles L Isbell, and Andrea L Thomaz. Policy shaping: Integrating human feedback with reinforcement learning. NIPS, 2013.</td></tr><tr><td>Yi Gu, Zhendong Wang, Yueqin Yin, Yujia Xie, and Mingyuan Zhou. Diffusion-rpo: Aligning dif- fusion models through relative preference optimization. arXiv preprint arXiv:2406.06382, 2024.</td></tr><tr><td>Jack Hessel, Ari Holtzman, Maxwell Forbes, Ronan Le Bras, and Yejin Choi. Clipscore: A reference-free evaluation metric for image captioning. In EMNLP, 2021.</td></tr><tr><td>Jonathan Ho, Ajay Jain, and Pieter Abbeel. Denoising diffusion probabilistic models. In NeurIPS, 2020.</td></tr><tr><td>Jiwoo Hong, Noah Lee, and James Thorne. Reference-free monolithic preference optimization with odds ratio. arXiv preprint arXiv:2403.07691, 2024a.</td></tr><tr><td>Jiwoo Hong, Sayak Paul, Noah Lee, Kashif Rasul, James Thorne, and Jongheon Jeong. Margin- aware preference optimization for aligning diffusion models without reference. arXiv preprint arXiv:2406.06424, 2024b.</td></tr></table>{{< /table-caption >}}
> 🔼 Table 1 presents a quantitative comparison of different models' performance on the GenEval benchmark, highlighting the improvements achieved by the proposed RankDPO method.
> <details>
> <summary>read the caption</summary>
> Table 1: Quantitative Results on GenEval. RankDPO improves results on most categories, notably 'two objects', 'counting', and 'color attribution' for SDXL and SD3-Medium.
> </details>

{{< table-caption >}}
<table id='5' style='font-size:14px'><tr><td>Dataset</td><td>Color</td><td>Shape</td><td>Texture</td><td>Spatial</td><td>Non-Spatial</td><td>DPG Score</td><td>Train Time (A100 Days)</td><td>Training Data</td><td>Same Inference Time</td></tr><tr><td>SDXL</td><td>58.79</td><td>46.87</td><td>52.99</td><td>21.31</td><td>31.19</td><td>74.65</td><td></td><td></td><td></td></tr><tr><td>ELLA (SDXL)</td><td>72.60</td><td>56.34</td><td>66.86</td><td>22.14</td><td>30.69</td><td>80.23</td><td>112</td><td>34M</td><td>X</td></tr><tr><td>RankDPO (SDXL)</td><td>72.33</td><td>56.93</td><td>69.67</td><td>24.53</td><td>31.33</td><td>79.26</td><td>6</td><td>0.24M</td><td></td></tr></table>{{< /table-caption >}}
> 🔼 Table 6 compares the performance of different models on T2I-Compbench and DPG-bench datasets, showing training time, training data size, and inference time.
> <details>
> <summary>read the caption</summary>
> Table 6: Comparison of T2I-Compbench Dataset with DPG-Bench, including model attributes, training time, and inference time increases.
> </details>

{{< table-caption >}}
<table id='7' style='font-size:16px'><tr><td>Method</td><td>Training Images</td><td>A100 GPU days</td><td>Equal Inference Cost</td><td>DPG-Bench Score</td></tr><tr><td>DPO</td><td>1.0M</td><td>30</td><td></td><td>76.74</td></tr><tr><td>MaPO</td><td>1.0M</td><td>25</td><td></td><td>74.53</td></tr><tr><td>SPO</td><td>-</td><td>5</td><td>V</td><td>74.73</td></tr><tr><td>ELLA*</td><td>34M</td><td>112</td><td>X</td><td>80.23</td></tr><tr><td>Ours</td><td>0.24M</td><td>6</td><td>V</td><td>79.26</td></tr></table>{{< /table-caption >}}
> 🔼 Table 7 compares the proposed method against other baselines in terms of training images, GPU days, inference cost, and DPG-Bench score, highlighting its efficiency and effectiveness.
> <details>
> <summary>read the caption</summary>
> Table 7: Comparing features of our proposal against baselines that aim to improve T2I model quality post-training. ELLA* also replaces the CLIP text-encoders with T5-XL text-encoder and a 470M parameter adapter applied at each timestep, thereby increasing the inference cost.
> </details>

{{< table-caption >}}
<table id='6' style='font-size:16px'><tr><td>Item</td><td>Pick-a-Picv2</td><td>Syn-Pic</td></tr><tr><td>Number of prompts</td><td>58 000</td><td>58 000</td></tr><tr><td>Number of images</td><td>1 025 015</td><td>232 000</td></tr><tr><td>Number of preferences</td><td>959 000</td><td>N/A</td></tr><tr><td>Image generation cost</td><td>N/A</td><td>$185.60</td></tr><tr><td>Annotation/Labelling cost</td><td>$47 950.00</td><td>< $20.00</td></tr><tr><td>Total cost</td><td>$47 950.00</td><td>< $205.60</td></tr></table>{{< /table-caption >}}
> 🔼 Table 1 presents a quantitative comparison of the performance of different models on the GenEval benchmark, highlighting the improvements achieved by RankDPO on several key categories.
> <details>
> <summary>read the caption</summary>
> Table 1: Quantitative Results on GenEval. RankDPO improves results on most categories, notably 'two objects', 'counting', and 'color attribution' for SDXL and SD3-Medium.
> </details>

{{< table-caption >}}
<table id='1' style='font-size:18px'><tr><td>Algorithm 1 DataGen: Generate Synthetically Labeled Ranked Preference Dataset (Syn-Pic)</td></tr><tr><td>Input: N prompts (P = {ci}N=1), k T2I Models ({0i}(=1), n Reward Models ({Rv}"=1) Output: Ranked Preference Dataset D Initialize: Synthetic dataset D = ⌀ for cin P do Generate k images x1 x2 , · · . , xk = 01(c), 02(c), . . · , 0k(c) , Initialize preference counts Ci = 0; VA E {1,. . . , k} for each reward model Ri⌀ do Compute scores Ri = Ri⌀ (xi , c); Vi E {1,. . , k} for each pair (i, j) with i ≠ j do if Ri > Rij then Increment preference count Ci = Ci +1 Vi E {1, . · · , k} Compute probabilities ⌀(xi) = n.(ki-1) ; Store entry (c,x1, x2 , · . . , xk, ⌀(x1), ⌀(x2) , . . . , ⌀(xk ( ( ( ( ( ) in D return Ranked Preference Dataset D</td></tr><tr><td>Algorithm 2 RankDPO: Ranking-based Preference Optimization using Syn-Pic</td></tr><tr><td>Input: Ranked Preference Dataset D, Initial model ⌀init, Reference model Oref Input: Pre-defined signal-noise schedule {at, ot}�t=1 Hyper-parameters: # Optimization Steps (m), Learning Rate (7), Divergence Control B Initialize: 0 = ⌀init Output: Fine-tuned model ARankDPO for iter = 0 to m do Sample entry (c, x1 x2 , · · · , xk, ⌀(x1 ) , ⌀(x2), · , ⌀(xk ( ( ( ( ( ) ~ D , Sample timestep t ~ U(1, T), and noise E⌀ ~ N(0, I) Compute noisy image x2 = atxi + �t�i Compute model scores Si 스 s(xi , c,t, 0) = ||e⌀ - e⌀(xt, c)112 - ||�i - Eref(Xt, c)113 Determine ranking T by sorting images based on ⌀(x2) in descending order for each pair (i, j) with i > j in T do Compute pairwise gains: Gij = 2⌀(xi) - 2⌀(xi ) Compute discount factors: D(T(i)) = log(1 + �(i)) and D(T(j)) = log(1 + �(j)) Compute pairwise DCG weights: △ij = |Gij| · D(T(i)) - D(T(j)) Compute pairwise loss: Lij = △inj log o (�� (s(xi, c,t,0) - s(x) c,t,01)) Sum pairwise losses: LRankDPO = - Ei>j Lij Compute gradients graditer = V�LRankDPO Update model parameters: 0 = 0 - 7 · graditer Final ARankDPO = 0 return Fine-tuned model ARankDPO</td></tr><tr><td>Algorithm 3 Generate Syn-Pic and Train RankDPO</td></tr><tr><td>Input: N prompts (P = {ci}N1), k T2I Models ({0i}i=1), n Reward Models ({Rv}:=1) Input: Initial model ⌀init, Reference model ⌀ref, Pre-defined signal-noise schedule {at, ot}}t=1 Hyper-parameters: # Optimization Steps (m), Learning Rate (7), Divergence Control B Output: Fine-tuned model ARankDPO // Generate Synthetically Labeled Ranked Preference dataset D using Algorithm 1 D = DataGen(P, {⌀i}k=1, {Ri⌀}n=1) // Train 0 using Algorithm 2 ARankDPO = RankDPO(D, ⌀init, ⌀ref, {⌀t, ot}t=1,m,7,B)</td></tr></table>{{< /table-caption >}}
> 🔼 Table 1 presents a quantitative comparison of the performance of different models on the GenEval benchmark, highlighting the improvements achieved by RankDPO in various categories.
> <details>
> <summary>read the caption</summary>
> Table 1: Quantitative Results on GenEval. RankDPO improves results on most categories, notably 'two objects', 'counting', and 'color attribution' for SDXL and SD3-Medium.
> </details>

</details>


### Full paper

{{< gallery >}}
<img src="https://ai-paper-reviewer.com/2410.18013/1.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.18013/2.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.18013/3.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.18013/4.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.18013/5.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.18013/6.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.18013/7.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.18013/8.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.18013/9.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.18013/10.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.18013/11.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.18013/12.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.18013/13.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.18013/14.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.18013/15.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.18013/16.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.18013/17.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.18013/18.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.18013/19.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.18013/20.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.18013/21.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.18013/22.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.18013/23.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
{{< /gallery >}}