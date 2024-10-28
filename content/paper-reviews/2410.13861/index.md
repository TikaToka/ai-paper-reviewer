---
title: "PUMA: Empowering Unified MLLM with Multi-granular Visual Generation"
summary: "PUMA: a unified multi-granular MLLM excels at diverse visual tasks by seamlessly integrating image generation and understanding, addressing varying granularity demands."
categories: ["AI Generated"]
tags: ["🔖 24-10-17", "🤗 24-10-22"]
showSummary: true
date: 2024-10-17
draft: false
---

### TL;DR


{{< lead >}}

The research paper introduces PUMA, a new multimodal large language model (MLLM) designed to improve visual content generation and understanding. Unlike previous models that often struggle to handle different levels of detail in images, PUMA uses a multi-granular approach. This means it can work with both coarse and fine-grained details, making it more versatile.  The paper shows that PUMA is effective at various tasks such as generating images from text, editing existing images, and understanding images. The key is a new architecture that uses an image encoder to extract different levels of detail (multi-granular features) from images, and then a special autoregressive language model (MLLM) to process these details and generate outputs.  The model is trained in two stages: pretraining on a large, diverse dataset to develop fundamental abilities, followed by instruction tuning on specific datasets for particular visual tasks.  The results demonstrate that PUMA's multi-granular approach leads to better performance in many visual tasks when compared to other state-of-the-art models.

{{< /lead >}}


{{< button href="https://arxiv.org/abs/2410.13861" target="_self" >}}
{{< icon "link" >}} &nbsp; read the paper on arXiv
{{< /button >}}
<br><br>
{{< button href="https://huggingface.co/papers/2410.13861" target="_self" >}}
{{< icon "hf-logo" >}} &nbsp; on Hugging Face
{{< /button >}}

#### Why does it matter?
This paper is significant because it introduces a novel approach to unifying multimodal understanding and generation in large language models (LLMs).  It addresses a critical challenge in the field by handling varying levels of detail in different visual tasks, something that existing LLMs struggle with.  The proposed method, PUMA, is shown to excel in various visual tasks, thus pushing the boundaries of MLLM capabilities and paving the way for more versatile and powerful AI.
#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} PUMA, a novel unified multimodal large language model (MLLM), effectively balances diversity and controllability across various visual generation tasks. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} PUMA processes and generates multi-granular visual representations, addressing the varying granularity requirements of different image generation tasks. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} PUMA demonstrates proficiency in a wide range of multimodal tasks, including image understanding, diverse text-to-image generation, editing, inpainting, colorization, and conditional image generation. {{< /typeit >}}
{{< /alert >}}

------
#### Visual Insights



![](figures/figures_1_0.png)

> 🔼 Figure 1 shows the diversity and controllability tradeoff in image generation tasks, and introduces PUMA, a unified multimodal large language model that balances diversity and controllability across various visual generation and understanding tasks.
> <details>
> <summary>read the caption</summary>
> Figure 1: a) Diversity and controllability tradeoff in image generation tasks: diverse text-to-image generation requires high diversity and fidelity, while tasks like conditional generation and manipulation require high controllability on the image. b) The introduced PUMA, a unified multimodal large language model that processes and generates multi-granular visual representations, balancing diversity and controllability across visual generation tasks. It excels in image understanding, diverse text-to-image generation, editing, inpainting, colorization, and conditional image generation.
> </details>







{{< table-caption >}}
<table id='4' style='font-size:14px'><tr><td>Model</td><td>Encoder foundation</td><td>Token num.</td><td>PSNRT↑</td><td>LPIPST↓</td><td>PSNRd↓</td><td>LPIPSd↑</td></tr><tr><td>SEED-LLaMA (2023</td><td>BLIP-2 ViT (0.3B)</td><td>32</td><td>9.73</td><td>0.6756</td><td>10.45</td><td>0.6189</td></tr><tr><td>SEED-X 2024b</td><td>Qwen-VL Encoder (4B)</td><td>64</td><td>10.86</td><td>0.5152</td><td>11.60</td><td>0.4292</td></tr><tr><td>Emu2 2024b</td><td>EVA02-CLIP-E-plus (4B)</td><td>64</td><td>15.72</td><td>0.2532</td><td>16.07</td><td>0.2101</td></tr><tr><td>PUMA (f4 scale)</td><td>CLIP-Large (0.3B)</td><td>1</td><td>10.76</td><td>0.6481</td><td>12.82</td><td>0.5751</td></tr><tr><td>PUMA (f3 scale)</td><td>CLIP-Large (0.3B)</td><td>4</td><td>11.04</td><td>0.5971</td><td>12.61</td><td>0.5329</td></tr><tr><td>PUMA (f2 scale)</td><td>CLIP-Large (0.3B)</td><td>16</td><td>12.35</td><td>0.4992</td><td>13.50</td><td>0.4354</td></tr><tr><td>PUMA (f1 scale)</td><td>CLIP-Large (0.3B)</td><td>64</td><td>13.26</td><td>0.4325</td><td>14.12</td><td>0.3631</td></tr><tr><td>PUMA (fo scale)</td><td>CLIP-Large (0.3B)</td><td>256</td><td>18.16</td><td>0.2215</td><td>19.36</td><td>0.1559</td></tr></table>{{< /table-caption >}}

> 🔼 Table 1 presents an evaluation of image decoding performance across different models and feature granularities, using PSNR and LPIPS to measure reconstruction quality and PSNRd and LPIPSd to assess reconstruction diversity.
> <details>
> <summary>read the caption</summary>
> Table 1: Image decoding evaluation using image encoder and decoder on the ImageNet validation set. PSNR and LPIPS measure the difference between reconstructed and ground truth images. PSNRd and LPIPSd measure the difference between two separate reconstructions of the same image, reflecting decoding diversity.
> </details>



### More visual insights

<details>
<summary>More on figures
</summary>


![](figures/figures_4_0.png)

> 🔼 The figure illustrates PUMA's architecture, a unified multi-granular autoregressive MLLM pipeline, and its versatility across various visual tasks.
> <details>
> <summary>read the caption</summary>
> Figure 2: Upper: PUMA's unified multi-granular autoregressive pipeline for processing and generating text and multi-granular visual features. Lower: Illustration of PUMA's versatility across various tasks: 1) diverse text-to-image generation, 2) image editing, 3) conditional image generation, and 4) image understanding, showcasing different input-output configurations.
> </details>



![](figures/figures_5_0.png)

> 🔼 The figure showcases the multi-granular visual decoding process, demonstrating how different levels of granularity in image features lead to varying degrees of image reconstruction and generation.
> <details>
> <summary>read the caption</summary>
> Figure 3: Multi-granular visual decoding from fine-grained to coarse-grained granularity.
> </details>



![](figures/figures_5_1.png)

> 🔼 The figure illustrates the multi-granular visual decoding process, showing how different granularities of image features are decoded to generate images with varying levels of detail and diversity.
> <details>
> <summary>read the caption</summary>
> Figure 3: Multi-granular visual decoding from fine-grained to coarse-grained granularity.
> </details>



![](figures/figures_7_0.png)

> 🔼 The figure compares the fine-grained image reconstruction performance of PUMA against other state-of-the-art models, showcasing PUMA's superior reconstruction quality.
> <details>
> <summary>read the caption</summary>
> Figure 5: Fine-grained image reconstruction of SEED-LLaMA (Ge et al., 2023), SEED-X (Ge et al., 2024b), Emu2 (Sun et al., 2024b) and PUMA (fo scale). High quality image reconstruction is the foundation of precise image manipulation tasks.
> </details>



![](figures/figures_8_0.png)

> 🔼 The figure shows the diversity of text-to-image generation results from different feature scales and models.
> <details>
> <summary>read the caption</summary>
> Figure 6: Diversity visualization of text-to-image generation results from PUMA feature scales f4 (1 visual token), f3 (4 visual tokens), and Emu2 (Sun et al., 2024b). The generated features are input to corresponding diffusion-based decoders with different random seeds.
> </details>



![](figures/figures_9_0.png)

> 🔼 Figure 1 shows the diversity and controllability tradeoff in image generation tasks and illustrates how the proposed PUMA model addresses this tradeoff by generating multi-granular visual representations.
> <details>
> <summary>read the caption</summary>
> Figure 1: a) Diversity and controllability tradeoff in image generation tasks: diverse text-to-image generation requires high diversity and fidelity, while tasks like conditional generation and manipulation require high controllability on the image. b) The introduced PUMA, a unified multimodal large language model that processes and generates multi-granular visual representations, balancing diversity and controllability across visual generation tasks. It excels in image understanding, diverse text-to-image generation, editing, inpainting, colorization, and conditional image generation.
> </details>



![](figures/figures_10_0.png)

> 🔼 The figure illustrates PUMA's unified multi-granular autoregressive pipeline and its versatility across diverse visual tasks, showcasing different input-output configurations.
> <details>
> <summary>read the caption</summary>
> Figure 2: Upper: PUMA's unified multi-granular autoregressive pipeline for processing and generating text and multi-granular visual features. Lower: Illustration of PUMA's versatility across various tasks: 1) diverse text-to-image generation, 2) image editing, 3) conditional image generation, and 4) image understanding, showcasing different input-output configurations.
> </details>



![](figures/figures_10_1.png)

> 🔼 Figure 1 shows the diversity and controllability tradeoff in image generation tasks and how PUMA, a unified multimodal large language model, balances these aspects across visual generation tasks.
> <details>
> <summary>read the caption</summary>
> Figure 1: a) Diversity and controllability tradeoff in image generation tasks: diverse text-to-image generation requires high diversity and fidelity, while tasks like conditional generation and manipulation require high controllability on the image. b) The introduced PUMA, a unified multimodal large language model that processes and generates multi-granular visual representations, balancing diversity and controllability across visual generation tasks. It excels in image understanding, diverse text-to-image generation, editing, inpainting, colorization, and conditional image generation.
> </details>



![](figures/figures_10_2.png)

> 🔼 The figure compares the image editing and colorization results using different feature scales (fo and f1) to show the impact of multi-granularity on the image quality.
> <details>
> <summary>read the caption</summary>
> Figure 9: Comparison of fo and f1 feature scales for tasks requiring precise controllability.
> </details>



![](figures/figures_18_0.png)

> 🔼 The figure displays diversity in text-to-image generation results from different feature scales and models.
> <details>
> <summary>read the caption</summary>
> Figure 6: Diversity visualization of text-to-image generation results from PUMA feature scales f4 (1 visual token), f3 (4 visual tokens), and Emu2 (Sun et al., 2024b). The generated features are input to corresponding diffusion-based decoders with different random seeds.
> </details>



![](figures/figures_18_1.png)

> 🔼 The figure shows a comparison of text-to-image generation results using different feature scales from PUMA and Emu2, highlighting the diversity of outputs.
> <details>
> <summary>read the caption</summary>
> Figure 6: Diversity visualization of text-to-image generation results from PUMA feature scales f4 (1 visual token), f3 (4 visual tokens), and Emu2 (Sun et al., 2024b). The generated features are input to corresponding diffusion-based decoders with different random seeds.
> </details>



![](figures/figures_18_2.png)

> 🔼 Figure 1 shows the diversity and controllability tradeoff in image generation tasks, and introduces PUMA, a unified multimodal large language model that balances diversity and controllability across visual generation tasks.
> <details>
> <summary>read the caption</summary>
> Figure 1: a) Diversity and controllability tradeoff in image generation tasks: diverse text-to-image generation requires high diversity and fidelity, while tasks like conditional generation and manipulation require high controllability on the image. b) The introduced PUMA, a unified multimodal large language model that processes and generates multi-granular visual representations, balancing diversity and controllability across visual generation tasks. It excels in image understanding, diverse text-to-image generation, editing, inpainting, colorization, and conditional image generation.
> </details>



![](figures/figures_18_3.png)

> 🔼 Figure 1 shows the diversity and controllability tradeoffs in various image generation tasks and introduces PUMA, a unified multimodal large language model that addresses these tradeoffs by generating multi-granular visual representations.
> <details>
> <summary>read the caption</summary>
> Figure 1: a) Diversity and controllability tradeoff in image generation tasks: diverse text-to-image generation requires high diversity and fidelity, while tasks like conditional generation and manipulation require high controllability on the image. b) The introduced PUMA, a unified multimodal large language model that processes and generates multi-granular visual representations, balancing diversity and controllability across visual generation tasks. It excels in image understanding, diverse text-to-image generation, editing, inpainting, colorization, and conditional image generation.
> </details>



![](figures/figures_18_4.png)

> 🔼 Figure 1 shows the diversity and controllability tradeoff in image generation tasks and introduces PUMA, a unified multimodal large language model that balances diversity and controllability across various visual generation tasks.
> <details>
> <summary>read the caption</summary>
> Figure 1: a) Diversity and controllability tradeoff in image generation tasks: diverse text-to-image generation requires high diversity and fidelity, while tasks like conditional generation and manipulation require high controllability on the image. b) The introduced PUMA, a unified multimodal large language model that processes and generates multi-granular visual representations, balancing diversity and controllability across visual generation tasks. It excels in image understanding, diverse text-to-image generation, editing, inpainting, colorization, and conditional image generation.
> </details>



![](figures/figures_18_5.png)

> 🔼 The figure illustrates the diversity and controllability tradeoff in image generation tasks and shows how the proposed PUMA model addresses this tradeoff by generating multi-granular visual representations.
> <details>
> <summary>read the caption</summary>
> Figure 1: a) Diversity and controllability tradeoff in image generation tasks: diverse text-to-image generation requires high diversity and fidelity, while tasks like conditional generation and manipulation require high controllability on the image. b) The introduced PUMA, a unified multimodal large language model that processes and generates multi-granular visual representations, balancing diversity and controllability across visual generation tasks. It excels in image understanding, diverse text-to-image generation, editing, inpainting, colorization, and conditional image generation.
> </details>



![](figures/figures_18_6.png)

> 🔼 Figure 1 shows the diversity and controllability tradeoff in image generation tasks and illustrates the proposed PUMA model's ability to balance these aspects across various visual tasks.
> <details>
> <summary>read the caption</summary>
> Figure 1: a) Diversity and controllability tradeoff in image generation tasks: diverse text-to-image generation requires high diversity and fidelity, while tasks like conditional generation and manipulation require high controllability on the image. b) The introduced PUMA, a unified multimodal large language model that processes and generates multi-granular visual representations, balancing diversity and controllability across visual generation tasks. It excels in image understanding, diverse text-to-image generation, editing, inpainting, colorization, and conditional image generation.
> </details>



![](figures/figures_18_7.png)

> 🔼 The figure illustrates the diversity and controllability tradeoffs in various image generation tasks and introduces PUMA, a unified multimodal large language model addressing these tradeoffs.
> <details>
> <summary>read the caption</summary>
> Figure 1: a) Diversity and controllability tradeoff in image generation tasks: diverse text-to-image generation requires high diversity and fidelity, while tasks like conditional generation and manipulation require high controllability on the image. b) The introduced PUMA, a unified multimodal large language model that processes and generates multi-granular visual representations, balancing diversity and controllability across visual generation tasks. It excels in image understanding, diverse text-to-image generation, editing, inpainting, colorization, and conditional image generation.
> </details>



![](figures/figures_19_0.png)

> 🔼 Figure 11 shows multiple visualizations of the multi-granular visual decoding process from fine-grained to coarse-grained image features.
> <details>
> <summary>read the caption</summary>
> Figure 11: More visualizations on multi-granular visual decoding from fine-grained to coarse-grained granularity.
> </details>



![](figures/figures_20_0.png)

> 🔼 Figure 1 shows the diversity and controllability tradeoff in image generation tasks, and illustrates the PUMA model's ability to balance these aspects across various visual generation tasks.
> <details>
> <summary>read the caption</summary>
> Figure 1: a) Diversity and controllability tradeoff in image generation tasks: diverse text-to-image generation requires high diversity and fidelity, while tasks like conditional generation and manipulation require high controllability on the image. b) The introduced PUMA, a unified multimodal large language model that processes and generates multi-granular visual representations, balancing diversity and controllability across visual generation tasks. It excels in image understanding, diverse text-to-image generation, editing, inpainting, colorization, and conditional image generation.
> </details>



![](figures/figures_21_0.png)

> 🔼 The figure illustrates the diversity and controllability trade-offs in various image generation tasks and introduces PUMA, a unified multimodal large language model addressing these challenges.
> <details>
> <summary>read the caption</summary>
> Figure 1: a) Diversity and controllability tradeoff in image generation tasks: diverse text-to-image generation requires high diversity and fidelity, while tasks like conditional generation and manipulation require high controllability on the image. b) The introduced PUMA, a unified multimodal large language model that processes and generates multi-granular visual representations, balancing diversity and controllability across visual generation tasks. It excels in image understanding, diverse text-to-image generation, editing, inpainting, colorization, and conditional image generation.
> </details>



![](figures/figures_21_1.png)

> 🔼 This figure illustrates the diversity and controllability trade-offs in various image generation tasks and introduces PUMA, a unified multimodal large language model that addresses these challenges.
> <details>
> <summary>read the caption</summary>
> Figure 1: a) Diversity and controllability tradeoff in image generation tasks: diverse text-to-image generation requires high diversity and fidelity, while tasks like conditional generation and manipulation require high controllability on the image. b) The introduced PUMA, a unified multimodal large language model that processes and generates multi-granular visual representations, balancing diversity and controllability across visual generation tasks. It excels in image understanding, diverse text-to-image generation, editing, inpainting, colorization, and conditional image generation.
> </details>



![](figures/figures_21_2.png)

> 🔼 This figure illustrates the diversity and controllability tradeoff in image generation tasks and introduces PUMA, a unified multimodal large language model that balances these factors across various visual generation and understanding tasks.
> <details>
> <summary>read the caption</summary>
> Figure 1: a) Diversity and controllability tradeoff in image generation tasks: diverse text-to-image generation requires high diversity and fidelity, while tasks like conditional generation and manipulation require high controllability on the image. b) The introduced PUMA, a unified multimodal large language model that processes and generates multi-granular visual representations, balancing diversity and controllability across visual generation tasks. It excels in image understanding, diverse text-to-image generation, editing, inpainting, colorization, and conditional image generation.
> </details>



![](figures/figures_21_3.png)

> 🔼 The figure illustrates the diversity and controllability tradeoff in image generation tasks and showcases the proposed PUMA model's ability to balance these aspects across various visual generation tasks.
> <details>
> <summary>read the caption</summary>
> Figure 1: a) Diversity and controllability tradeoff in image generation tasks: diverse text-to-image generation requires high diversity and fidelity, while tasks like conditional generation and manipulation require high controllability on the image. b) The introduced PUMA, a unified multimodal large language model that processes and generates multi-granular visual representations, balancing diversity and controllability across visual generation tasks. It excels in image understanding, diverse text-to-image generation, editing, inpainting, colorization, and conditional image generation.
> </details>



![](figures/figures_22_0.png)

> 🔼 This figure illustrates the diversity and controllability trade-offs in various image generation tasks and showcases PUMA's ability to balance these trade-offs using multi-granular visual representations.
> <details>
> <summary>read the caption</summary>
> Figure 1: a) Diversity and controllability tradeoff in image generation tasks: diverse text-to-image generation requires high diversity and fidelity, while tasks like conditional generation and manipulation require high controllability on the image. b) The introduced PUMA, a unified multimodal large language model that processes and generates multi-granular visual representations, balancing diversity and controllability across visual generation tasks. It excels in image understanding, diverse text-to-image generation, editing, inpainting, colorization, and conditional image generation.
> </details>



![](figures/figures_22_1.png)

> 🔼 Figure 1 demonstrates the diversity and controllability tradeoff in image generation tasks and introduces PUMA, a unified multimodal large language model that balances these tradeoffs.
> <details>
> <summary>read the caption</summary>
> Figure 1: a) Diversity and controllability tradeoff in image generation tasks: diverse text-to-image generation requires high diversity and fidelity, while tasks like conditional generation and manipulation require high controllability on the image. b) The introduced PUMA, a unified multimodal large language model that processes and generates multi-granular visual representations, balancing diversity and controllability across visual generation tasks. It excels in image understanding, diverse text-to-image generation, editing, inpainting, colorization, and conditional image generation.
> </details>



</details>




<details>
<summary>More on tables
</summary>


{{< table-caption >}}
<table id='5' style='font-size:14px'><tr><td>Model</td><td>Token num.</td><td>CLIP-I↑</td><td>CLIP-T↑</td><td>LPIPSd↑</td></tr><tr><td>SD-v1.5 (2022</td><td>-</td><td>0.667</td><td>0.302</td><td>0.692</td></tr><tr><td>DALL-E2 2022</td><td>-</td><td>-</td><td>0.314</td><td>-</td></tr><tr><td>SDXL 2023</td><td>-</td><td>0.674</td><td>0.310</td><td>0.600</td></tr><tr><td>DALL-E 3 2023</td><td>-</td><td>-</td><td>0.320</td><td>-</td></tr><tr><td>SEED-LLaMA 2023</td><td>32</td><td>0.682</td><td>-</td><td>0.652</td></tr><tr><td>Emu 2023</td><td>64</td><td>0.656</td><td>0.286</td><td>0.700</td></tr><tr><td>Emu2 (2024b</td><td>64</td><td>0.686</td><td>0.297</td><td>0.329</td></tr><tr><td>SEED-X (2024b</td><td>64</td><td>0.729</td><td>0.314</td><td>0.493</td></tr><tr><td>PUMA (f4 scale)</td><td>1</td><td>0.699</td><td>0.295</td><td>0.613</td></tr><tr><td>PUMA (f3 scale)</td><td>4</td><td>0.703</td><td>0.300</td><td>0.558</td></tr><tr><td>PUMA (5-scale Max)</td><td>-</td><td>0.736</td><td>0.317</td><td>-</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> Table 2 presents a quantitative comparison of diverse text-to-image generation performance across various models, evaluating consistency (CLIP-I, CLIP-T) and diversity (LPIPSd) of generated images.


{{< table-caption >}}
<table id='11' style='font-size:16px'><tr><td>Model</td><td>CLIP-I↑</td><td>CLIP-T↑</td><td>DINO↑</td></tr><tr><td>InstructPix2Pix  2023</td><td>0.834</td><td>0.219</td><td>0.762</td></tr><tr><td>MagicBrush 2024a</td><td>0.838</td><td>0.222</td><td>0.776</td></tr><tr><td>EMU-Edit 2024</td><td>0.859</td><td>0.231</td><td>0.819</td></tr><tr><td>OmniGen 2024</td><td>0.836</td><td>0.233</td><td>0.804</td></tr><tr><td>PUMA (f1 scale)</td><td>0.802</td><td>0.258</td><td>0.679</td></tr><tr><td>PUMA (fo scale)</td><td>0.840</td><td>0.264</td><td>0.784</td></tr><tr><td>PUMA (5-scale Max)</td><td>0.846</td><td>0.270</td><td>0.785</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> Table 3 presents a quantitative evaluation of PUMA's image editing capabilities against other state-of-the-art models using CLIP-I, CLIP-T, and DINO scores, indicating its performance relative to existing methods.


{{< table-caption >}}
<table id='12' style='font-size:18px'><tr><td>Type</td><td>Model</td><td># Params</td><td>MMB↑</td><td>MME↑</td><td>GQA↑</td><td>VQAv2(test)↑</td><td>POPE↑</td><td>Vizwiz↑</td></tr><tr><td rowspan="4">Und. Only</td><td>LLaVA-v1.5 2024a</td><td>7B</td><td>64.3</td><td>1510.7</td><td>62.0</td><td>78.5</td><td>85.9</td><td>50.0</td></tr><tr><td>InstructBLIP 2023</td><td>13B</td><td>-</td><td>1212.8</td><td>49.5</td><td>-</td><td>78.9</td><td>33.4</td></tr><tr><td>Qwen-VL-Chat 2023</td><td>7B</td><td>-</td><td>1487.5</td><td>57.5</td><td>78.2</td><td>-</td><td>38.9</td></tr><tr><td>mPLUG-Owl2 2024b</td><td>7B</td><td>64.5</td><td>1450.2</td><td>56.1</td><td>79.4</td><td>85.8</td><td>54.5</td></tr><tr><td rowspan="6">Und. and Gen.</td><td>Emu 2023</td><td>13B</td><td>-</td><td>-</td><td>-</td><td>57.2</td><td>-</td><td>-</td></tr><tr><td>NExT-GPT 023</td><td>7B</td><td>58.0</td><td>-</td><td>-</td><td>66.7</td><td>-</td><td>48.4</td></tr><tr><td>SEED-X 2024b</td><td>17B</td><td>75.4</td><td>1457.0</td><td>47.9</td><td>-</td><td>84.2</td><td>-</td></tr><tr><td>Chameleon 2024</td><td>34B</td><td>-</td><td>-</td><td>-</td><td>66.0</td><td>-</td><td>-</td></tr><tr><td>Emu2-Chat 2024b</td><td>40B</td><td>-</td><td>-</td><td>65.1</td><td>84.9</td><td>-</td><td>54.9</td></tr><tr><td>PUMA (Ours)</td><td>8B</td><td>68.9</td><td>1490.3</td><td>60.6</td><td>76.2</td><td>85.2</td><td>47.9</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> Table 4 presents the quantitative comparison of PUMA against other state-of-the-art models on several multimodal understanding benchmarks.


{{< table-caption >}}
<table id='1' style='font-size:16px'><tr><td>ILoshchilov. Decoupled weight decay regularization. arXiv preprint arXiv:1711.05101, 2017.</td></tr><tr><td>Anand Mishra, Shashank Shekhar, Ajeet Kumar Singh, and Anirban Chakraborty. Ocr-vqa: Visual question answering by reading text in images. In 2019 international conference on document analysis and recognition (ICDAR), pp. 947-952. IEEE, 2019.</td></tr><tr><td>Zhiliang Peng, Wenhui Wang, Li Dong, Yaru Hao, Shaohan Huang, Shuming Ma, and Furu Wei. Kosmos-2: Grounding multimodal large language models to the world. arXiv preprint arXiv:2306.14824, 2023.</td></tr><tr><td>Dustin Podell, Zion English, Kyle Lacey, Andreas Blattmann, Tim Dockhorn, Jonas M�ller, Joe Penna, and Robin Rombach. Sdxl: Improving latent diffusion models for high-resolution image synthesis. arXiv preprint arXiv:2307.01952, 2023.</td></tr><tr><td>Can Qin, Shu Zhang, Ning Yu, Yihao Feng, Xinyi Yang, Yingbo Zhou, Huan Wang, Juan Car- los Niebles, Caiming Xiong, Silvio Savarese, et al. Unicontrol: A unified diffusion model for controllable visual generation in the wild. arXiv preprint arXiv:2305.11147, 2023.</td></tr><tr><td>Alec Radford, Jong Wook Kim, Chris Hallacy, Aditya Ramesh, Gabriel Goh, Sandhini Agarwal, Girish Sastry, Amanda Askell, Pamela Mishkin, Jack Clark, et al. Learning transferable visual models from natural language supervision. In International conference on machine learning, pp. 8748-8763. PMLR, 2021.</td></tr><tr><td>Aditya Ramesh, Prafulla Dhariwal, Alex Nichol, Casey Chu, and Mark Chen. Hierarchical text- conditional image generation with clip latents. arXiv preprint arXiv:2204.06125, 1(2):3, 2022.</td></tr><tr><td>Robin Rombach, Andreas Blattmann, Dominik Lorenz, Patrick Esser, and Bjorn Ommer. High- resolution image synthesis with latent diffusion models. In Proceedings of the IEEE/CVF confer- ence on computer vision and pattern recognition, pp. 10684-10695, 2022.</td></tr><tr><td>Christoph Schuhmann, Romain Beaumont, Richard Vencu, Cade Gordon, Ross Wightman, Mehdi Cherti, Theo Coombes, Aarush Katta, Clayton Mullis, Mitchell Wortsman, et al. Laion-5b: An open large-scale dataset for training next generation image-text models. Advances in Neural Information Processing Systems, 35:25278-25294, 2022.</td></tr><tr><td>Shelly Sheynin, Adam Polyak, Uriel Singer, Yuval Kirstain, Amit Zohar, Oron Ashual, Devi Parikh, and Yaniv Taigman. Emu edit: Precise image editing via recognition and generation tasks. In Pro- ceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recognition, pp. 8871- 8879, 2024.</td></tr><tr><td>Keqiang Sun, Junting Pan, Yuying Ge, Hao Li, Haodong Duan, Xiaoshi Wu, Renrui Zhang, Aojun Zhou, Zipeng Qin, Yi Wang, et al. Journeydb: A benchmark for generative image understanding. Advances in Neural Information Processing Systems, 36, 2024a.</td></tr><tr><td>Quan Sun, Qiying Yu, Yufeng Cui, Fan Zhang, Xiaosong Zhang, Yueze Wang, Hongcheng Gao, Jingjing Liu, Tiejun Huang, and Xinlong Wang. Generative pretraining in multimodality. arXiv preprint arXiv:2307.05222, 2023.</td></tr><tr><td>Quan Sun, Yufeng Cui, Xiaosong Zhang, Fan Zhang, Qiying Yu, Yueze Wang, Yongming Rao, Jingjing Liu, Tiejun Huang, and Xinlong Wang. Generative multimodal models are in-context learners. In Proceedings of the IEEE/CVF Conference on Computer Vision and Pattern Recogni- tion, pp. 14398-14409, 2024b.</td></tr><tr><td>Zineng Tang, Ziyi Yang, Chenguang Zhu, Michael Zeng, and Mohit Bansal. Any-to-any generation via composable diffusion. Advances in Neural Information Processing Systems, 36, 2024.</td></tr><tr><td>Chameleon Team. Chameleon: Mixed-modal early-fusion foundation models. arXiv preprint arXiv:2405.09818, 2024.</td></tr><tr><td>Keyu Tian, Yi Jiang, Zehuan Yuan, Bingyue Peng, and Liwei Wang. Visual autoregressive modeling: Scalable image generation via next-scale prediction. arXiv preprint arXiv:2404.02905, 2024.</td></tr><tr><td>Shengbang Tong, Ellis Brown, Penghao Wu, Sanghyun Woo, Manoj Middepogu, Sai Charitha Akula, Jihan Yang, Shusheng Yang, Adithya Iyer, Xichen Pan, et al. Cambrian-1: A fully open, vision-centric exploration of multimodal llms. arXiv preprint arXiv:2406.16860, 2024.</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> Table 1 presents the quantitative results of image decoding evaluation using PSNR, LPIPS, PSNRd and LPIPSd on the ImageNet validation set, comparing different models and their decoding diversity.


{{< table-caption >}}
<br><table id='2' style='font-size:16px'><tr><td>Visual token type</td><td>Token number</td><td>MMB↑</td><td>MME↑</td><td>GQA↑</td><td>VQAv2(test) ↑</td></tr><tr><td>J4</td><td>1</td><td>56.8</td><td>1252.6</td><td>0.0</td><td>64.1</td></tr><tr><td>f3</td><td>4</td><td>58.3</td><td>1285.5</td><td>0.0</td><td>67.0</td></tr><tr><td>/ 2</td><td>16</td><td>61.5</td><td>1403.0</td><td>46.6</td><td>71.1</td></tr><tr><td>f1</td><td>64</td><td>63.6</td><td>1400.8</td><td>58.4</td><td>74.4</td></tr><tr><td>fo</td><td>256</td><td>65.4</td><td>1464.9</td><td>58.8</td><td>76.9</td></tr><tr><td>f4-fo</td><td>341</td><td>65.1</td><td>1445.5</td><td>61.0</td><td>76.9</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> Table 5 shows the ablation study of different visual token inputs on image understanding performance using LLaVA-v1.5 setting with CLIP-Large-224 visual encoder.


{{< table-caption >}}
<table id='16' style='font-size:18px'><tr><td colspan="4">Table 6: CLIP-I and CLIP-T scores on MSCOCO 30K validation set with different feature scales.</td></tr><tr><td>Model</td><td>Token num.</td><td>CLIP-I↑</td><td>CLIP-T↑</td></tr><tr><td>PUMA (f4 scale)</td><td>1</td><td>0.699</td><td>0.295</td></tr><tr><td>PUMA (f3 scale)</td><td>4</td><td>0.703</td><td>0.300</td></tr><tr><td>PUMA (f2 scale)</td><td>16</td><td>0.703</td><td>0.301</td></tr><tr><td>PUMA (f1 scale)</td><td>64</td><td>0.693</td><td>0.299</td></tr><tr><td>PUMA (fo scale)</td><td>256</td><td>0.621</td><td>0.280</td></tr><tr><td>PUMA (5-scale Max)</td><td>-</td><td>0.736</td><td>0.317</td></tr></table>{{< /table-caption >}}
> 🔼 {{ table.description }}
> <details>
> <summary>read the caption</summary>
> {{ table.caption }}
> </details>


> This table presents CLIP-I and CLIP-T scores on the MSCOCO 30K validation set, comparing the performance of PUMA's text-to-image generation across five different feature scales (f4 to fo).


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
{{< /gallery >}}