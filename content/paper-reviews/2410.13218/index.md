---
title: "CBT-Bench: Evaluating Large Language Models on Assisting Cognitive Behavior Therapy"
summary: "CBT-BENCH: a new benchmark reveals LLMs' potential and limitations in assisting Cognitive Behavioral Therapy, highlighting the need for further research in AI-driven mental healthcare."
categories: ["AI Generated"]
tags: ["🔖 24-10-17", ]
showSummary: true
date: 2024-10-17
draft: false
---

{{< keyword >}} 2410.13218 {{< /keyword >}}

### TL;DR


{{< lead >}}

This research introduces CBT-BENCH, a novel benchmark to assess Large Language Models' (LLMs) capabilities in assisting Cognitive Behavioral Therapy (CBT).  The benchmark comprises three levels of difficulty: basic CBT knowledge, cognitive model understanding, and therapeutic response generation.  Evaluation of several LLMs revealed that while they perform well on basic knowledge questions, they fall short on higher-level tasks requiring deep analysis of patient's cognitive structures and generating effective therapeutic responses.  This highlights the need for further research to improve LLMs' capabilities in complex real-world scenarios involving mental healthcare.

{{< /lead >}}


{{< button href="https://arxiv.org/abs/2410.13218" target="_self" >}}
{{< icon "link" >}} &nbsp; read the paper on arXiv
{{< /button >}}
<br><br>
{{< button href="https://huggingface.co/papers/2410.13218" target="_self" >}}
{{< icon "hf-logo" >}} &nbsp; on Hugging Face
{{< /button >}}

#### Why does it matter?
This paper is crucial for AI researchers working on mental healthcare applications.  CBT-BENCH offers a novel, comprehensive benchmark for evaluating LLMs, addressing limitations in existing research.  Its findings highlight current LLMs' strengths and weaknesses in assisting CBT, guiding future research directions and model development.
#### Key Takeaways

{{< alert "star" >}}
{{< typeit speed=10 lifeLike=true >}} CBT-BENCH, a three-level benchmark systematically evaluates LLMs' ability to assist CBT. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=1000 lifeLike=true >}} LLMs excel at basic CBT knowledge but struggle with complex tasks like cognitive model analysis and therapeutic response generation. {{< /typeit >}}
{{< /alert >}}

{{< alert "star" >}}
{{< typeit speed=10 startDelay=2000 lifeLike=true >}} The study reveals a significant gap between current LLM capabilities and the demands of real-world CBT, paving the way for future research. {{< /typeit >}}
{{< /alert >}}

------
#### Visual Insights



![](https://ai-paper-reviewer.com/2410.13218/figures_19_0.png)

> 🔼 The figure presents a diagram illustrating an example of a cognitive model used in Cognitive Behavioral Therapy (CBT).
> <details>
> <summary>read the caption</summary>
> Figure 3: An example cognitive model from (Beck, 2020).
> </details>





![](https://ai-paper-reviewer.com/2410.13218/charts_7_0.png)

> 🔼 The radar chart visualizes the detailed F1 scores of each label for CBT-CD and CBT-FC datasets across six different LLMs.
> <details>
> <summary>read the caption</summary>
> Figure 1: Detailed F1 scores of each label for CBT-CD and CBT-FC.
> </details>





{{< table-caption >}}
<table id='0' style='font-size:14px'><tr><td>Knowledge Types</td><td>Example QA Pairs from CBT-QA</td><td>Distributions (%)</td></tr><tr><td>Basic CBT knowledge and concepts</td><td>Albert Ellis' Cognitive Model includes which components? A. Activating Events - Behaviors - Cognitions, B. Antecedents - Beliefs - Consequences, C: Activating Events - Beliefs - Consequences, C. Antecedents - Behaviors - Consequences</td><td>41.82</td></tr><tr><td>Practical CBT knowledge</td><td>When helping clients evaluate automatic thoughts, therapists should generally help clients evaluate which aspects of those thoughts? A. Accuracy and/or intensity, B. Intensity and/or utility, C. Accuracy and/or utility</td><td>34.09</td></tr><tr><td>Case studies</td><td>The client has identified an automatic thought of "My partner is going to break up with me". The therapist asks the client, "If your thought is accurate and your partner does break up with you, what does that mean about you?". The therapist is most likely trying to identify: A. The client's intermediate belief, B. The client's core belief, C. The client's thinking error</td><td>18.18</td></tr><tr><td>Others</td><td>What are some ways that CBT therapists can engage in therapy from a multicultural perspective? (select all that apply) A. Not take clients from a different culture than their own, B. Ask clients about the strengths and challenges of their cultural, racial, and ethnic identity during intake, C. Being aware of their own cultural values and biases, D. Work together with the client to incorporate the client's core values</td><td>5.9</td></tr></table>{{< /table-caption >}}

> 🔼 Table 1 presents the different types of knowledge included in the CBT-QA dataset, example question-answer pairs for each type, and the percentage of each type in the test set.
> <details>
> <summary>read the caption</summary>
> Table 1: Knowledge types in CBT-QA, with example QA pairs and distributions in the test set.
> </details>



### More visual insights



<details>
<summary>More on charts
</summary>


![](https://ai-paper-reviewer.com/2410.13218/charts_7_1.png)

> 🔼 The radar chart visualizes the F1 scores achieved by six different LLMs across various labels for CBT-CD and CBT-FC datasets, showcasing their performance in cognitive model understanding tasks.
> <details>
> <summary>read the caption</summary>
> Figure 1: Detailed F1 scores of each label for CBT-CD and CBT-FC.
> </details>


![](https://ai-paper-reviewer.com/2410.13218/charts_8_0.png)

> 🔼 The chart displays the overall pairwise comparison of three different LLMs against human expert responses across three difficulty levels (beginner, intermediate, advanced) in a CBT therapeutic response generation task.
> <details>
> <summary>read the caption</summary>
> Figure 2: The overall pairwise comparison of different models vs. reference across difficulty level.
> </details>


![](https://ai-paper-reviewer.com/2410.13218/charts_24_0.png)

> 🔼 The radar chart visualizes the performance of six LLMs on different aspects of CBT knowledge acquisition and cognitive model understanding, showing varying levels of proficiency across different task types.
> <details>
> <summary>read the caption</summary>
> Figure 4: Detailed accuracies on different types of knowledge for CBT-QA and the F1 score of each label for CBT-PC.
> </details>


![](https://ai-paper-reviewer.com/2410.13218/charts_24_1.png)

> 🔼 The radar chart visualizes the performance of six large language models on two tasks: CBT knowledge acquisition (CBT-QA) and primary core belief classification (CBT-PC).
> <details>
> <summary>read the caption</summary>
> Figure 4: Detailed accuracies on different types of knowledge for CBT-QA and the F1 score of each label for CBT-PC.
> </details>


![](https://ai-paper-reviewer.com/2410.13218/charts_27_0.png)

> 🔼 The chart displays the win-tie-loss results for three LLMs (Llama-3.1-405B, Llama-3.1-8B, and GPT-40) across three difficulty levels (beginner, intermediate, and advanced) in the therapeutic response generation task.
> <details>
> <summary>read the caption</summary>
> Figure 5: The win-tie-loss comparison among different models on three difficulty levels.
> </details>


</details>



<details>
<summary>More on tables
</summary>


{{< table-caption >}}
<table id='0' style='font-size:14px'><tr><td>Datasets</td><td>Inputs</td><td>Labels</td></tr><tr><td>CBT-CD</td><td>Situation: Our wedding was put off because his parents asked him to build a house for them 2 months before our wedding! They had a perfectly good house at the time they just wanted their dream house. Thoughts: I am a victim with no power in this situation. I must accept this behavior. I am too scared to leave this situation. I am not worthy of better. His parents hate me. His parents do not want us to get married. He may not want to marry me either. He loves his parents more than me. I will always be second in his life. His parents had no need for a house, and I know this for sure. I am aware of every aspect of this situation.</td><td>all-or-nothing thinking; person- alization; mind reading</td></tr><tr><td>CBT-PC</td><td>Situation: I had an amazing childhood. When I was twelve in 2004, my father had to go to Iraq. My mother thought it would be best if she moved my brother and I back to the U.S., where we would have family support. I was very depressed because my dad was my hero and I blamed my mom for everything that went wrong. I felt like no one understood me... When my dad came back, he wanted a divorce from my mother. Thoughts: Everything was great until my mom messed everything up. Because of her, my brother and I had to leave our dad. We ended up living somewhere where no one liked me. It's her fault that I never felt like I fit in. Even when my dad came back, he didn't want us either - he wanted a divorce. I guess no one will ever want me in their life. I'll probably be alone forever.</td><td>helpless; unlovable</td></tr><tr><td>CBT-FC</td><td>Situation: My daughter was recently diagnosed as bipolar. If I say anything about seeking treatment, my daughter accuses me of not understanding her and what is happening to her. She is very paranoid and worries about her safety all the time. I need to know how to talk to her and what to do to get her into treatment. Thoughts: I am a bad mother. This is my fault. It is so shameful that my daughter has bipolar. If my daughter gets worse, then it will be my fault for not getting her into treatment. I need to do something. This is my responsibility.</td><td>I am incompetent; I am help- less; I am powerless, weak, vul- nerable; I am bad - dangerous, toxic, evil</td></tr></table>{{< /table-caption >}}
> 🔼 Table 1 presents the different types of knowledge covered in the CBT-QA dataset, along with example questions and answers, and their distribution in the test set.
> <details>
> <summary>read the caption</summary>
> Table 1: Knowledge types in CBT-QA, with example QA pairs and distributions in the test set.
> </details>

{{< table-caption >}}
<table id='2' style='font-size:14px'><tr><td></td><td>CBT-CD</td><td>CBT-PC</td><td>CBT-FC</td></tr><tr><td># of examples</td><td>146</td><td>184</td><td>112</td></tr><tr><td># of labels</td><td>10</td><td>3</td><td>19</td></tr><tr><td>Average situation length</td><td>232.9</td><td>240.7</td><td>233.4</td></tr><tr><td>Average thought length</td><td>258.8</td><td>256.9</td><td>248.4</td></tr><tr><td>Average ground truth labels</td><td>2.5</td><td>1.9</td><td>3.8</td></tr></table>{{< /table-caption >}}
> 🔼 The table presents the statistics of the three level II tasks in CBT-BENCH, including the number of examples, labels, and average lengths of situations and thoughts.
> <details>
> <summary>read the caption</summary>
> Table 3: Statistics of three level II tasks.
> </details>

{{< table-caption >}}
<table id='0' style='font-size:14px'><tr><td>Category</td><td>Difficulty Level</td><td>Patient Speech</td><td>Reference Response</td></tr><tr><td>Negotiating a session agenda</td><td>Beginner</td><td>[Nervous] I don't think I'm ready for working on this today.</td><td>OK. We can revisit and possibly modify our plan for today. How about we first take a step back and explore your thinking about this? What thoughts are you noticing as we discuss the agenda?</td></tr><tr><td>Negotiating a session agenda</td><td>Intermediate</td><td>[Agitated] Wow. You won't believe what happened this week. It's a really long story · ..</td><td>It sounds like there 's a lot on your mind, and I'd like to hear about it. Would it be OK to take a second to discuss our agenda for the day first, including where discussing this past week might fit in, as well as anything else you want to take up here today? I want to make sure that we budget our time accordingly. Shall we start with a homework check-in and then tackle the story?</td></tr><tr><td>Responding to therapeutic alliance ruptures</td><td>Advanced</td><td>[Anxious] I did the measure you asked me to fill out. Honestly, I think I might have rated you lower than usual, but I'm not sure I want to talk about it.</td><td>I was just noticing that your trust in me has gone down some. I wonder if you could help me appreciate what that's like for you? I'd far prefer persisting with our agenda when you may have diminishing that to just faith in it or me.</td></tr></table>{{< /table-caption >}}
> 🔼 The table shows the types of knowledge included in the CBT-QA dataset, example question-answer pairs for each type, and the percentage of each type in the test set.
> <details>
> <summary>read the caption</summary>
> Table 1: Knowledge types in CBT-QA, with example QA pairs and distributions in the test set.
> </details>

{{< table-caption >}}
<table id='0' style='font-size:16px'><tr><td></td><td>CBT-QA</td><td colspan="3">CBT-CD</td><td colspan="3">CBT-PC</td><td colspan="3">CBT-FC</td></tr><tr><td>Model</td><td>Accuracy</td><td>Precision</td><td>Recall</td><td>F1</td><td>Accuracy</td><td>Recall</td><td>F1</td><td>Accuracy</td><td>Recall</td><td>F1</td></tr><tr><td>Mistral-v0.3-7B</td><td>75.9</td><td>43.8</td><td>56.4</td><td>45.3</td><td>78.8</td><td>75.0</td><td>72.5</td><td>43.8</td><td>59.7</td><td>47.9</td></tr><tr><td>Gemma-2-9B</td><td>90.0</td><td>44.5</td><td>47.2</td><td>40.1</td><td>79.5</td><td>82.9</td><td>80.4</td><td>45.4</td><td>63.3</td><td>51.5</td></tr><tr><td>Llama-3.1-8B</td><td>78.2</td><td>39.7</td><td>59.9</td><td>44.1</td><td>75.2</td><td>93.9</td><td>82.5</td><td>37.0</td><td>62.8</td><td>44.8</td></tr><tr><td>Llama-3.1-70B</td><td>92.7</td><td>50.9</td><td>51.8</td><td>43.9</td><td>82.6</td><td>72.7</td><td>75.8</td><td>62.0</td><td>56.6</td><td>55.4</td></tr><tr><td>Llama-3.1-405B</td><td>95.0</td><td>49.4</td><td>44.2</td><td>43.3</td><td>85.3</td><td>70.1</td><td>75.3</td><td>53.1</td><td>68.7</td><td>58.2</td></tr><tr><td>GPT-4o</td><td>94.1</td><td>55.8</td><td>52.0</td><td>43.9</td><td>80.2</td><td>77.6</td><td>78.4</td><td>54.5</td><td>62.1</td><td>56.7</td></tr><tr><td>Human</td><td>90.7</td><td>51.1</td><td>48.1</td><td>49.1</td><td>76.0</td><td>79.4</td><td>77.6</td><td>53.0</td><td>57.3</td><td>54.6</td></tr></table>{{< /table-caption >}}
> 🔼 Table 5 presents the performance of six Large Language Models (LLMs) on tasks assessing basic CBT knowledge and cognitive model understanding, showing that larger models generally perform better on knowledge questions but not necessarily on more complex cognitive tasks.
> <details>
> <summary>read the caption</summary>
> Table 5: Performance of LLMs on basic CBT knowledge acquisition (CBT-QA) and cognitive model understanding (CBT-CD, CBT-PC, and CBT-FC). The precision, recall, and F1 are averaged by class portion.
> </details>

{{< table-caption >}}
<table id='7' style='font-size:14px'><tr><td>Exercise</td><td>1</td><td>2</td><td>3</td><td>4</td><td>5</td><td>6</td><td>7</td><td>8</td><td>9</td><td>10</td><td>Avg.</td></tr><tr><td>Llama-3.1-405B</td><td>0.07</td><td>0.06</td><td>0.21</td><td>-0.24</td><td>-0.19</td><td>0.00</td><td>0.18</td><td>-0.31</td><td>0.07</td><td>0.00</td><td>-0.01</td></tr><tr><td>Llama-3.1-8B</td><td>-0.21</td><td>-0.31</td><td>-0.47</td><td>-0.29</td><td>-0.13</td><td>0.00</td><td>-0.35</td><td>0.00</td><td>-0.13</td><td>-0.33</td><td>-0.22</td></tr><tr><td>GPT-4o</td><td>-0.50</td><td>-0.50</td><td>-0.13</td><td>-0.24</td><td>-0.31</td><td>-0.53</td><td>-0.06</td><td>-0.44</td><td>-0.13</td><td>-0.40</td><td>-0.32</td></tr></table>{{< /table-caption >}}
> 🔼 Table 5 presents the performance of six Large Language Models (LLMs) on tasks assessing basic CBT knowledge and cognitive model understanding, showing accuracy for CBT-QA and weighted precision, recall, and F1 score for other datasets.
> <details>
> <summary>read the caption</summary>
> Table 5: Performance of LLMs on basic CBT knowledge acquisition (CBT-QA) and cognitive model understanding (CBT-CD, CBT-PC, and CBT-FC). The precision, recall, and F1 are averaged by class portion.
> </details>

{{< table-caption >}}
<table id='0' style='font-size:14px'><tr><td>Statement</td><td>[Frustrated] I know I said I would go to the event and start a conversation with new people, but I only managed to say "hello" to one person.</td></tr><tr><td>Llama-3.1-405B</td><td>It sounds like you're feeling disappointed with yourself for not meeting your own expectations. Can we take a closer look at what held you back from starting more conversations? Was it anxiety, fear of rejection, or something else? Let's break it down and identify some smaller, achievable steps for next time.</td></tr><tr><td>Human Reference</td><td>It seems like you might be a bit disappointed by this, but I see this as significant progress. It was a big accomplishment to show up to the event in the first place and then say hello to someone you don't know. Let's talk about what that was like.</td></tr></table>{{< /table-caption >}}
> 🔼 Table 5 presents the performance of six large language models on tasks assessing basic CBT knowledge and cognitive model understanding, showing accuracy for CBT-QA and weighted precision, recall, and F1 scores for other datasets.
> <details>
> <summary>read the caption</summary>
> Table 5: Performance of LLMs on basic CBT knowledge acquisition (CBT-QA) and cognitive model understanding (CBT-CD, CBT-PC, and CBT-FC). The precision, recall, and F1 are averaged by class portion.
> </details>

{{< table-caption >}}
<br><table id='8' style='font-size:16px'><tr><td rowspan="2">#Exe.</td><td rowspan="2">Metric</td><td colspan="3">Model Results</td></tr><tr><td>Llama-3.1-405B</td><td>Llama-3.1-8B</td><td>GPT-4o</td></tr><tr><td rowspan="4">2</td><td>C1</td><td>0.34</td><td>-0.25</td><td>0.25</td></tr><tr><td>C2</td><td>0.06</td><td>0.13</td><td>-0.25</td></tr><tr><td>C3</td><td>-0.38</td><td>-0.13</td><td>-0.63</td></tr><tr><td>C4</td><td>0.56</td><td>0.13</td><td>0.81</td></tr></table>{{< /table-caption >}}
> 🔼 Table 8 presents a breakdown of model scores across four criteria for exercise 2, showing the average score for each model.
> <details>
> <summary>read the caption</summary>
> Table 8: Results breakdown of 4 criteria on questions from exercise 2, reported with the average score.
> </details>

{{< table-caption >}}
<table id='1' style='font-size:14px'><tr><td>Belief</td><td>#Label</td><td>Definition</td></tr><tr><td>all-or-nothing thinking</td><td>65</td><td>Also called black-and-white, polarized, or dichotomous thinking. You view a situation in only two categories instead of on a continuum.</td></tr><tr><td>mind reading</td><td>47</td><td>You believe you know what others are thinking, failing to consider other, more likely possibilities.</td></tr><tr><td>fortune-telling</td><td>44</td><td>Also called fortune-telling. You predict the future negatively without considering other, more likely outcomes.</td></tr><tr><td>personalization</td><td>42</td><td>You believe others are behaving negatively because of you, without considering more plausible explanations for their behavior.</td></tr><tr><td>emotional reasoning</td><td>36</td><td>You think something must be true because you "feel" (actually believe) it so strongly, ignoring or discounting evidence to the contrary.</td></tr><tr><td>overgeneralization</td><td>32</td><td>You make a sweeping negative conclusion that goes far beyond the current situation.</td></tr><tr><td>labeling</td><td>29</td><td>You put a fixed, global label on yourself or others without considering that the evidence might more reasonably lead to a less extreme conclusion.</td></tr><tr><td>should statements</td><td>28</td><td>Also called imperatives. You have a precise, fixed idea of how you or others should behave, and you overestimate how bad it is that these expectations are not met.</td></tr><tr><td>magnification</td><td>25</td><td>When you evaluate yourself, another person, or a situation, you unreasonably magnify the negative and/or minimize the positive.</td></tr><tr><td>mental filter</td><td>21</td><td>Also called selective abstraction. You pay undue attention to one negative detail instead of seeing the whole picture.</td></tr></table>{{< /table-caption >}}
> 🔼 The table presents the different types of knowledge assessed in the CBT-QA dataset, example question-answer pairs for each type, and the percentage distribution of each type in the test set.
> <details>
> <summary>read the caption</summary>
> Table 1: Knowledge types in CBT-QA, with example QA pairs and distributions in the test set.
> </details>

{{< table-caption >}}
<table id='4' style='font-size:16px'><tr><td>helpless</td><td>162</td><td>being ineffective-in getting things done, self-protection, and/or measuring up to others</td></tr><tr><td>unlovable</td><td>101</td><td>having personal qualities resulting in an inability to get or maintain love and intimacy from others</td></tr><tr><td>worthless</td><td>81</td><td>being an immoral sinner or dangerous to others</td></tr></table>{{< /table-caption >}}
> 🔼 The table presents the different types of knowledge assessed in the CBT-QA dataset, example questions for each type, and their distribution in the test set.
> <details>
> <summary>read the caption</summary>
> Table 1: Knowledge types in CBT-QA, with example QA pairs and distributions in the test set.
> </details>

{{< table-caption >}}
<table id='1' style='font-size:14px'><tr><td>Primary Core Belief</td><td>Fine-grained Core Belief</td><td>#Label</td></tr><tr><td rowspan="9">helpless</td><td>I am incompetent</td><td>16</td></tr><tr><td>I am helpless</td><td>36</td></tr><tr><td>I am powerless, weak, vulnerable</td><td>38</td></tr><tr><td>I am a victim</td><td>29</td></tr><tr><td>I am needy</td><td>5</td></tr><tr><td>I am trapped</td><td>28</td></tr><tr><td>I am out of control</td><td>22</td></tr><tr><td>I am a failure, loser</td><td>22</td></tr><tr><td>I am defective</td><td>31</td></tr><tr><td rowspan="6">unlovable</td><td>I am unlovable</td><td>25</td></tr><tr><td>I am unattractive</td><td>6</td></tr><tr><td>I am undesirable, unwanted</td><td>27</td></tr><tr><td>I am bound to be rejected</td><td>29</td></tr><tr><td>I am bound to be abandoned</td><td>24</td></tr><tr><td>I am bound to be alone</td><td>21</td></tr><tr><td rowspan="4">unlovable</td><td>I am worthless, waste</td><td>31</td></tr><tr><td>I am immoral</td><td>10</td></tr><tr><td>I am bad - dangerous, toxic, evil</td><td>14</td></tr><tr><td>I don't deserve to live</td><td>8</td></tr></table>{{< /table-caption >}}
> 🔼 Table 1 presents the different types of knowledge included in the CBT-QA dataset, provides example question-answer pairs for each type, and shows the distribution of each type in the test set.
> <details>
> <summary>read the caption</summary>
> Table 1: Knowledge types in CBT-QA, with example QA pairs and distributions in the test set.
> </details>

{{< table-caption >}}
<table id='1' style='font-size:14px'><tr><td>Category</td><td>#Exercise</td><td>#Beginner</td><td>#Intermediate</td><td>#Advanced</td></tr><tr><td>Explaining the Treatment Rationale for Cognitive Behavioral Therapy</td><td>14</td><td>4</td><td>6</td><td>4</td></tr><tr><td>Establishing Goals</td><td>16</td><td>5</td><td>6</td><td>5</td></tr><tr><td>Negotiating a Session Agenda</td><td>15</td><td>5</td><td>5</td><td>5</td></tr><tr><td>Assigning and Reviewing Between-Session Activities</td><td>15</td><td>5</td><td>7</td><td>5</td></tr><tr><td>Working With Cognitions</td><td>16</td><td>5</td><td>5</td><td>6</td></tr><tr><td>Working With Behaviors</td><td>15</td><td>5</td><td>5</td><td>5</td></tr><tr><td>Working With Emotions</td><td>17</td><td>5</td><td>5</td><td>7</td></tr><tr><td>Adherence Flexibility</td><td>16</td><td>5</td><td>6</td><td>5</td></tr><tr><td>Responding to Therapeutic Alliance Ruptures</td><td>15</td><td>5</td><td>5</td><td>5</td></tr><tr><td>Responding to Client Resistance</td><td>15</td><td>5</td><td>5</td><td>5</td></tr><tr><td>All</td><td>156</td><td>49</td><td>55</td><td>52</td></tr></table>{{< /table-caption >}}
> 🔼 The table presents the types of knowledge assessed in the CBT-QA dataset, example question-answer pairs for each type, and the percentage distribution of each type in the test set.
> <details>
> <summary>read the caption</summary>
> Table 1: Knowledge types in CBT-QA, with example QA pairs and distributions in the test set.
> </details>

{{< table-caption >}}
<table id='0' style='font-size:14px'><tr><td>Category</td><td>Criteria</td></tr><tr><td>Explaining the Treatment Rationale for Cognitive Behavioral Therapy</td><td>Criteria 1: Validate the client's experience, Criteria 2: Explain the logic of how CBT can be used to address concerns, Criteria 3: Instill hope for using CBT effectively, Criteria 4: Set appropriate expectations for the nature and impact of CBT</td></tr><tr><td>Establishing Goals</td><td>Criteria 1: Suggest CBT-consistent goals and tasks that align with an individualized CBT case formulation, Criteria 2: Invite the client's input on and agreement with the goals and tasks, Criteria 3: Demonstrate flexibility, Criteria 4: Emphasize concrete, actionable, and measurable goals</td></tr><tr><td>Negotiating a Session Agenda</td><td>Criteria 1: Suggest a CBT-consistent agenda that aligns with the CBT case formulation, Criteria 2: Invite the client's input on and agreement with the agenda, Criteria 3: Demonstrate flexibility, Criteria 4: Maintain some degree of frame or structure (i.e., the agenda can shift, but generally maintain a more or less explicit attempt to delineate expectations for session goals and tasks)</td></tr><tr><td>Assigning and Reviewing Between-Session Activities</td><td>Criteria 1: Provide a basic rationale for the homework assignment, Criteria 2: Tailor the homework assignment to the client's concerns and needs, Criteria 3: Ensure that there is adequate agreement on and understanding of the homework assignment, Criteria 4: Encourage and validate good-faith efforts</td></tr><tr><td>Working With Cognitions</td><td>Criteria 1: Encourage and facilitate client self-reflection on thoughts and beliefs, Criteria 2: Maintain an open, exploratory stance, Criteria 3: Orient the client's attention to thoughts or connections between thoughts and other experiences, Criteria 4: Emphasize cognitive flexibility, rather than simple thought replacement, and refrain from implying that a particular thought is "right or wrong"</td></tr><tr><td>Working With Behaviors</td><td>Criteria 1 : Maintain a collaborative and curious stance, Criteria 2: Be clear when suggesting a plan of action and expectations, Criteria 3: Be positive and supportive of both big and small positive changes, Criteria 4: Appeal to relevant core learning concepts, including conditioning, reinforcement, the importance of environment, antecedents, and consequences</td></tr><tr><td>Working With Emotions</td><td>Criteria 1: Empathically inquire about clients' emotional experience, Criteria 2: Actively listen and maintain a supportive tone to clients' emotional disclosures, Criteria 3: Model tolerance of affect and an approach orientation to clients' strong emotional experience, Criteria 4: Use psychoeducation to support the importance of clients experiencing versus avoiding their emotion and the maladaptive consequences of negative reinforcement</td></tr><tr><td>Adherence Flexibility</td><td>Criteria 1: Maintain a collaborative and transparent stance, Criteria 2: Demonstrate empathy, Criteria 3: Demonstrate openness to explore before determining if a modification is indeed warranted, Criteria 4: Maintain consistency with a broad CBT orientation</td></tr><tr><td>Responding to Therapeutic Alliance Ruptures</td><td>Criteria 1: Momentarily step away from the CBT change agenda, Criteria 2: Warmly invite the client to discuss their subjective experience, Criteria 3: Empathize with the client's thoughts and feelings and invite further disclosure of unhelpful or invalidating occurrences, Criteria 4: "Disarm" the client's negative affect toward you or CBT by finding some truth in their disclosures</td></tr><tr><td>Responding to Client Resistance</td><td>Criteria 1: Momentarily step away from the CBT change agenda, Criteria 2: Empathically explore the client's experience of treatment and you, Criteria 3: Validate clients' experience and "roll with" versus challenging their resistance, Criteria 4: Support clients' autonomy and elicit their motivation for pursuing valued directions</td></tr></table>{{< /table-caption >}}
> 🔼 The table shows the different types of knowledge included in the CBT-QA dataset, example question-answer pairs for each type, and the percentage of questions in the test set that belong to each type.
> <details>
> <summary>read the caption</summary>
> Table 1: Knowledge types in CBT-QA, with example QA pairs and distributions in the test set.
> </details>

{{< table-caption >}}
<table id='0' style='font-size:14px'><tr><td>Knowledge Types</td><td>Example QA Pairs from CBT-QA</td></tr><tr><td rowspan="5">Basic CBT knowledge and concepts</td><td>Intermediate beliefs consist of rules, attitudes, and conditional assumptions. Which of the following fits the best as an attitude? A. "Failing is bad", B. "I must not fail", C: "If I try, I will fail", D. "I am a failure"</td></tr><tr><td>What type of cognitive error involves shrinking something to make it seem less important? A. Selective Abstraction, B. Mental filtering, C. Overgeneralization, D. Self-defeated thinking</td></tr><tr><td>Which strategy should you employ the most often when you want a client to come to a new understanding? A. Guided discovery, B. Direct advice, C: Indirect advice, D. Disclosing what strategy works the best for you</td></tr><tr><td>In the assessment session, you should create a conceptualization/formulation of the client': s problem with them. When using CBT, which of the following is the most important for a conceptualization/formulation to include? A. How past developmental events impact the problem, B. How thoughts and behaviors relate to the problem, C: How current supports may limit the client's functioning, D. How genetic vulnerabilities result in current problems</td></tr><tr><td>CBT helps clients identify links between: A. Health, thoughts, B. Emotions, thoughts, decision-making, C: Thoughts, emotions, behavior, D. Antecedent, behavior, consequence</td></tr><tr><td rowspan="5">Practical CBT knowledge</td><td>How might a social worker use the principles of CBT approach when working with a client who is experiencing suicidal thoughts? A. By encouraging the client to suppress their thoughts and focus on positive affirmations, B. By providing temporary shelter and financial assistance to alleviate immediate stressors, C. By collaboratively identifying and challenging distorted thought patterns contributing to suicidal thoughts, D. No options align with any practices considered to be CBT</td></tr><tr><td>A primary concern during the final stages of a cognitive behavioral group is which of the following? A. promoting transfer of learning, B. developing a therapeutic contract, C. role-playing various situations D. establishing baseline data</td></tr><tr><td>Early in treatment you advise clients that the way to get better is? A. By making small changes in their thinking and behaviors each day, B. By making large changes to their core beliefs, C. By gaining insight regarding their developmental history D. By changing their emotions</td></tr><tr><td>When helping clients evaluate automatic thoughts, therapists should generally help clients evaluate which aspects of those thoughts? A. accuracy and/or intensity, B. intensity and/or utility, C. accuracy and/or utility</td></tr><tr><td>Which of the following typically improve depressive symptoms (select all that apply)? A. Interpersonal interactions, B. Activities that have the potential for pleasure, C. Activities that have the potential for a sense of mastery, D. Repeatedly thinking about the reasons one is depressed</td></tr><tr><td rowspan="2">Case studies</td><td>The client says "I feel like he doesn 't care about me". "I feel like he doesn't care about me" is a? A. Thought, B. Emotion, C. Physiological reaction/sensation, D. Feeling</td></tr><tr><td>A manager tells you (the therapist) that the new employee, who has been doing an excellent job, requested a meeting with him. The manager anticipates that the new employee plans to resign. Which is the best description of the manager's cognitive error? A. Thinking from an all-or-nothing perspective, B. Always thinking the worst will occur without considering positive outcomes, C. Viewing only selected negative evidence while editing out positive aspects, D. Undervaluing the positive significance of an event The client's mood has been improving since they've been attending treatment. They could attribute this improvement to many different things. Which of the below do you want them to attribute it to the most? A. The positive changes they have been making in their thinking and behaviors, B. The support their therapist has given them, C. Events in their environment that have changed, D. The randomness of their mood Ms. T. has a number of long-standing negative attitudes such as "I'II never succeed" and "I have to be perfect to be accepted.' No matter how hard she tries she always seems to think that she is "not measuring up. 행 What cognitive therapy procedures do you think might help her? A. Listing advantages and disadvantages, B. Breaking out, C. Listing schemas, D. Thought recording A client says, "I don t feel like I'm doing a good job at work" What question can you ask next to start the downward arrow technique to identify their core belief? A. "How did your parents give feedback when you were younger?", B. "That's not true, you're a great worker!", C. "What are you worried that might mean ?" D. "What is the evidence for and against this thought?"</td></tr><tr><td>A.</td><td>Among the following principles, which one does not align with the core values of social work practice? A. Respect for the inherent dignity and worth of every individual, B. Promotion of client self-determination and autonomy, C. Maintenance of strict neutrality and avoidance of taking sides, D. Commitment to social justice and advocacy for marginalized populations Which of the following best describes the collaborative nature of a client and a therapist in social work practice? The therapist provides solutions to the client's problems without considering the client's perspective, B. The therapist and client work together as partners to identify goals and develop strategies for change, Others C. The therapist imposes their own values and beliefs onto the client without</td></tr></table>{{< /table-caption >}}
> 🔼 The table presents the types of knowledge included in the CBT-QA dataset, example questions and answers, and the percentage distribution of each type in the test set.
> <details>
> <summary>read the caption</summary>
> Table 1: Knowledge types in CBT-QA, with example QA pairs and distributions in the test set.
> </details>

{{< table-caption >}}
<table id='0' style='font-size:14px'><tr><td>Inputs</td><td>Labels</td></tr><tr><td>Situation: I have been with my girlfriend for 5 years and we have a history of a strong sexual intimacy connection. This has been getting worse over time. Thoughts: It is my girlfriend's sex drive that is the problem.</td><td>overgeneralization; labeling</td></tr><tr><td>Situation: I am struggling at the moment and yet I am aware that I should be feeling good. Thoughts: What I am feeling and going through are unacceptable and wrong. There is a right and wrong way to go through this and I am doing it the wrong way.</td><td>should statements; emotional reasoning</td></tr><tr><td>Situation: The individual has recently discovered that their mom has cheated on their dad four times in the past. Each time, the parents attended counseling, where the mom initially denied her infidelity but eventually admitted to it, blaming their dad for not meeting her needs. Thoughts: I cannot trust anyone, why is everyone a liar. My mom has betrayed me. Of course something like this is happening to me, it only happens to me.</td><td>all-or-nothing thinking; overgeneraliza- tion; emotional reasoning</td></tr><tr><td>Situation: I experienced a recent setback with my OCD symptoms that had been in remission Thoughts: I have no longer won the battle against my OCD</td><td>all-or-nothing thinking; magnification</td></tr><tr><td>Situation: My anxiety used to be worse a couple of years ago, but now im just paranoid. Im always thinking that people think im a loser, and I wont leave the house without makeup, because i am horrified about what other people think about me. Thoughts: Because my anxiety felt worse before, this must be a normal level of anxiety and paranoia, so my conclusions make more sense. People do think I'm a loser or that I'm ugly. I at least wear makeup so they can't see how ugly I am, and ifI avoid people altogether, then they won't know how much of a loser I am or how boring I am. I don't like who I am, and whatever people think of me is probably way worse than I think it is.</td><td>overgeneralization; emotional reasoning; mind reading</td></tr></table>{{< /table-caption >}}
> 🔼 Table 1 presents the types of knowledge assessed in the CBT-QA dataset, provides example question-answer pairs for each type, and shows the distribution of each type in the test set.
> <details>
> <summary>read the caption</summary>
> Table 1: Knowledge types in CBT-QA, with example QA pairs and distributions in the test set.
> </details>

{{< table-caption >}}
<table id='0' style='font-size:14px'><tr><td>Inputs</td><td>Labels</td></tr><tr><td>Situation: I've been dating this guy for 2 years, and when things are good, they're great. We have deep conversations about various topics, share laughs, and seem to have a strong connection. However, every few months, he suddenly becomes distant. The usual daily communication slows down, his tone becomes cold, and there's a noticeable disconnect. After giving it some space and bringing it up gently, he admits to withdrawing and usually provides a reason for his behavior, such as feeling disrespected or abandoned. We address the issues, talk about feelings and needs, and find better ways to communicate. He has a therapist, and I encourage him to work on these issues, but the cycle repeats. Thoughts: I am not enough for him. Why do I always get hurt like this. I always get stuck in these endless cycles, and I am unlovable.</td><td>helpless; unlovable</td></tr><tr><td>Situation: I would move out, but I don't have the money for that nor do I have the job. Whenever I get I job, I take too many sick days out because of the bruises and scarring on my face are hard to hide. Thoughts: I can 't move out until I have a better financial situation. I must remain in this situation until I have more money. The only way out is to be more financially secure. I cannot let other people know or help me. I have to sick days to hide the bruising on my face. Other people can't find out what's happening. I must solve this all on my own.</td><td>helpless; unlovable</td></tr><tr><td>Situation: Ever since, I have known in the back of my mind that he still does this, helpless; unlovable; worthless and have gotten up in the middle of the night a few times to find him masturbating and video chatting publicly or with females who are at least scantily clad, if not nude and masturbating themselves. When I confront him about it, he says he has a public sex fetish and needs to fulfill it, believing that it helps keep him ,,faithful%o to me since I am no longer interested. Thoughts: He calls that faithful? It doesn't feel faithful. But I don't know ifI even have the right to feel the way I do about it - after all, that's pretty much how our relationship started. Am I even allowed to be upset? I'm the one that changed, so it feels like it's my fault. I shouldn't be blaming him. He tried to get me involved, but when I said I wasn 't into it, he didn't push, he just continued on doing what made him happy. Plus, he's not doing this to hurt me, so I shouldn't feel hurt by it. I should be happy for him that he is feeling fulfilled. But I feel sad, like he doesn't want me anymore.</td><td></td></tr><tr><td>Situation: Do Ihave schizophrenia or something Thoughts: I am scared and don't helpless know what is happening. I fear this could be something very serious. There is something wrong with me. I don't know what to do.</td><td></td></tr><tr><td>Situation: I was born with Attention Deficit Hyperactivity Disorder, O.C.D. and helpless; unlovable; worthless I am also transgendered. As a result, I was a very difficult child to raise. There was constant fighting between myself and my parents. At the age of ten, I was sent away to an institution for two years. While there, I was physically, emotionally, and sexually abused. I couldn't talk to anyone because I had no trust in adults. Thoughts: I was born defective and wrong, so that's why my parents had such a hard time raising me. I was hard to love because I was so different. It was my fault that they had to send me away; I needed to be fixed. Then, I was abused while I was away but I couldn't talk to anyone about it because I was scared that ifI said anything, I'd be sent even further away.</td><td></td></tr></table>{{< /table-caption >}}
> 🔼 This table presents the different types of knowledge included in the CBT-QA dataset, along with example questions and their distribution in the test set.
> <details>
> <summary>read the caption</summary>
> Table 1: Knowledge types in CBT-QA, with example QA pairs and distributions in the test set.
> </details>

{{< table-caption >}}
<table id='0' style='font-size:14px'><tr><td>Inputs</td><td>Labels</td></tr><tr><td>Situation: My relationship has always been in trouble because of my wife's suspicious nature. Thoughts: - This is all my wife's fault, not mine. If she stopped being suspicious, then all of our marital problems would be solved. There is nothing I can do about this; she is the one who needs to change.</td><td>I am incompetent; I am power- less, weak, vulnerable; I am a victim</td></tr><tr><td>Situation: My relationship with my mom has deteriorated due to a lie I told back in February. I took full responsibility for it, but I'm aware that my actions, such as hiding my depression from her and seeing a psychologist without her knowledge, were not acceptable. I felt that she wouldn't understand because she's always belittled my emotions, accusing me of exaggerating and seeking attention whenever I express myself emotionally. This led me to feel ashamed and afraid of facing her criticism, so I chose to keep my struggles hidden. Thoughts: I'm a failure for lying and hiding things from my mom. She'll never understand or accept me for who I am. I'm just seeking attention by expressing my feelings.</td><td>I am trapped; I am a failure, loser; I am unlovable; I am undesirable, unwanted; I am bound to be rejected; I am worthless, waste</td></tr><tr><td>Situation: ...although we all had a lovely day I noticed he was distant... Thoughts: I am confused by this situation, I do not know how to interpret this or respond. I cannot trust myself. I cannot trust my own thoughts about this.</td><td>I am incompetent; I am power- less, weak, vulnerable</td></tr><tr><td>Situation: Ihave been backwards... I was forced... Thoughts: My sleep habits are abnormal. I should feel conscientious and weird about my sleep patterns. I may be judged for being different. I regret or resent having been forced.</td><td>I am defective</td></tr><tr><td>Situation: I never told anyone the truth about it or should I say I never admitted it to anyone... I swore I would never cheat on my husband because I never forgave myself for cheating on him with the married guy... I hated myself for that. Thoughts: I feel guilt for what I did. I blame myself for what happened. I am a bad person. I regret what I did. I wanted to make amends for what I did. I am only worthy of love if I hide my past mistakes. I feel shame for what I did.</td><td>I am bound to be rejected; I am bound to be abandoned; I am immoral</td></tr></table>{{< /table-caption >}}
> 🔼 Table 5 presents the performance of six large language models (LLMs) across four different datasets assessing basic CBT knowledge and cognitive model understanding.
> <details>
> <summary>read the caption</summary>
> Table 5: Performance of LLMs on basic CBT knowledge acquisition (CBT-QA) and cognitive model understanding (CBT-CD, CBT-PC, and CBT-FC). The precision, recall, and F1 are averaged by class portion.
> </details>

{{< table-caption >}}
<table id='3' style='font-size:14px'><tr><td>You are a CBT therapist and now need to determine the cognitive distortions of a patient from his current situation and thoughts. Each patient may have **up to 3** distortions. Situation: I'm depressed but nobody knows it. I do not have any friends. This started at age 11. Thoughts: I cannot make friends and have no one to hang out with. Therefore, I am always going to be alone and depressed. what distortions this patient has?</td></tr><tr><td>Question: Choices: a: all-or-nothing thinking b: overgeneralization c: mental filter d: should statements e: labeling f: personalization g: magnification h: emotional reasoning 1: mind reading j: fortune-telling Answer: Please only output the letters corresponding to the choices. Multiple choices should be separated by a comma.</td></tr></table>{{< /table-caption >}}
> 🔼 Table 5 presents the performance of six large language models on tasks assessing basic CBT knowledge and cognitive model understanding, showing accuracy and F1 scores for each dataset.
> <details>
> <summary>read the caption</summary>
> Table 5: Performance of LLMs on basic CBT knowledge acquisition (CBT-QA) and cognitive model understanding (CBT-CD, CBT-PC, and CBT-FC). The precision, recall, and F1 are averaged by class portion.
> </details>

{{< table-caption >}}
<table id='0' style='font-size:14px'><tr><td>You are a CBT therapist and now need to determine the fine-grained beliefs of a patient from his current situation and thoughts. Each patient may have **up to 9** fine-grained beliefs. Now answer the following question:</td></tr><tr><td>Situation: The individual has recently discovered that their mom has cheated on their dad four times in the past. Each time, the parents attended counseling, where the mom initially denied her infidelity but eventually admitted to it, blaming their dad for not meeting her needs.</td></tr><tr><td>Thoughts: I cannot trust anyone, why is everyone a liar. My mom has betrayed me. Of course something like this is happening to it only</td></tr><tr><td>me, happens to me. Question: what fine-grained beliefs has?</td></tr><tr><td>this patient Choices:</td></tr><tr><td>a: I am incompetent</td></tr><tr><td>b: I am helpless</td></tr><tr><td>c: I am powerless, weak, vulnerable</td></tr><tr><td>d: I am a victim</td></tr><tr><td>e: I am needy</td></tr><tr><td>f: I am trapped</td></tr><tr><td>g: I am out of control</td></tr><tr><td>h: I am a failure, loser</td></tr><tr><td>i: I am defective</td></tr><tr><td>J: I am unlovable</td></tr><tr><td>k: I am unattractive</td></tr><tr><td>1: I am undesirable, unwanted</td></tr><tr><td>m: I am bound to be rejected</td></tr><tr><td>n: I am bound to be abandoned</td></tr><tr><td>O: I am bound to be alone</td></tr><tr><td>p: I am worthless, waste</td></tr><tr><td>q: I am immoral</td></tr><tr><td>r: I am bad - dangerous, toxic, evil</td></tr><tr><td>S: I don't deserve to live</td></tr><tr><td>Answer:</td></tr><tr><td>Please only output the letters corresponding to the choices. Multiple choices should be separated by a comma.</td></tr></table>{{< /table-caption >}}
> 🔼 The table presents the different types of knowledge included in the CBT-QA dataset, along with example question-answer pairs and their distributions.
> <details>
> <summary>read the caption</summary>
> Table 1: Knowledge types in CBT-QA, with example QA pairs and distributions in the test set.
> </details>

{{< table-caption >}}
<table id='2' style='font-size:18px'><tr><td>Exercise</td><td>Criteria</td><td>Llama-3.1-405B VS. ref</td><td>Llama-3.1-8B VS. ref</td><td>GPT-4o VS. ref</td></tr><tr><td rowspan="4">Exercise 1</td><td>Criteria 1</td><td>0.00</td><td>-0.36</td><td>-0.64</td></tr><tr><td>Criteria 2</td><td>0.64</td><td>0.79</td><td>0.93</td></tr><tr><td>Criteria 3</td><td>0.36</td><td>0.36</td><td>0.43</td></tr><tr><td>Criteria 4</td><td>0.50</td><td>0.43</td><td>0.29</td></tr><tr><td rowspan="4">Exercise 2</td><td>Criteria 1</td><td>0.34</td><td>-0.25</td><td>0.25</td></tr><tr><td>Criteria 2</td><td>0.06</td><td>0.13</td><td>-0.25</td></tr><tr><td>Criteria 3</td><td>-0.38</td><td>-0.13</td><td>-0.63</td></tr><tr><td>Criteria 4</td><td>0.56</td><td>0.13</td><td>0.81</td></tr><tr><td rowspan="4">Exercise 3</td><td>Criteria 1</td><td>0.00</td><td>-0.40</td><td>-0.53</td></tr><tr><td>Criteria 2</td><td>0.07</td><td>-0.27</td><td>-0.27</td></tr><tr><td>Criteria 3</td><td>0.07</td><td>-0.07</td><td>0.13</td></tr><tr><td>Criteria 4</td><td>-0.33</td><td>-0.33</td><td>-0.20</td></tr><tr><td rowspan="4">Exercise 4</td><td>Criteria 1</td><td>-0.06</td><td>-0.53</td><td>0.24</td></tr><tr><td>Criteria 2</td><td>-0.29</td><td>-0.47</td><td>0.12</td></tr><tr><td>Criteria 3</td><td>-0.18</td><td>-0.18</td><td>-0.41</td></tr><tr><td>Criteria 4</td><td>-0.12</td><td>-0.47</td><td>0.00</td></tr><tr><td rowspan="4">Exercise 5</td><td>Criteria 1</td><td>-0.06</td><td>0.00</td><td>-0.44</td></tr><tr><td>Criteria 2</td><td>-0.31</td><td>-0.44</td><td>-0.50</td></tr><tr><td>Criteria 3</td><td>0.25</td><td>0.63</td><td>0.00</td></tr><tr><td>Criteria 4</td><td>0.06</td><td>-0.19</td><td>0.06</td></tr><tr><td rowspan="4">Exercise 6</td><td>Criteria 1</td><td>0.13</td><td>0.33</td><td>-0.40</td></tr><tr><td>Criteria 2</td><td>0.20</td><td>-0.20</td><td>0.13</td></tr><tr><td>Criteria 3</td><td>-0.07</td><td>0.00</td><td>0.13</td></tr><tr><td>Criteria 4</td><td>-0.13</td><td>-0.33</td><td>-0.07</td></tr><tr><td rowspan="4">Exercise 7</td><td>Criteria 1</td><td>0.41</td><td>0.18</td><td>0.06</td></tr><tr><td>Criteria 2</td><td>-0.12</td><td>0.00</td><td>-0.18</td></tr><tr><td>Criteria 3</td><td>0.00</td><td>-0.35</td><td>-0.29</td></tr><tr><td>Criteria 4</td><td>-0.06</td><td>0.12</td><td>0.24</td></tr><tr><td rowspan="4">Exercise 8</td><td>Criteria 1</td><td>-0.06</td><td>0.06</td><td>-0.25</td></tr><tr><td>Criteria 2</td><td>-0.56</td><td>0.38</td><td>-0.06</td></tr><tr><td>Criteria 3</td><td>0.06</td><td>0.38</td><td>-0.25</td></tr><tr><td>Criteria 4</td><td>0.25</td><td>0.13</td><td>0.00</td></tr><tr><td rowspan="4">Exercise 9</td><td>Criteria 1</td><td>0.07</td><td>-0.53</td><td>-0.40</td></tr><tr><td>Criteria 2</td><td>0.07</td><td>0.13</td><td>-0.13</td></tr><tr><td>Criteria 3</td><td>-0.27</td><td>-0.13</td><td>-0.53</td></tr><tr><td>Criteria 4</td><td>-0.60</td><td>-0.73</td><td>-0.33</td></tr><tr><td rowspan="4">Exercise 10</td><td>Criteria 1</td><td>-0.27</td><td>-0.53</td><td>-0.60</td></tr><tr><td>Criteria 2</td><td>-0.20</td><td>-0.33</td><td>-0.60</td></tr><tr><td>Criteria 3</td><td>-0.07</td><td>-0.47</td><td>-0.47</td></tr><tr><td>Criteria 4</td><td>-0.07</td><td>-0.47</td><td>-0.33</td></tr></table>{{< /table-caption >}}
> 🔼 Table 5 presents the performance of six large language models on three levels of CBT tasks: basic knowledge acquisition, cognitive model understanding, and therapeutic response generation.
> <details>
> <summary>read the caption</summary>
> Table 5: Performance of LLMs on basic CBT knowledge acquisition (CBT-QA) and cognitive model understanding (CBT-CD, CBT-PC, and CBT-FC). The precision, recall, and F1 are averaged by class portion.
> </details>

{{< table-caption >}}
<table id='0' style='font-size:16px'><tr><td>Client Statement</td><td>[Agitated] Honestly, my main problem is my partner.</td></tr><tr><td>Llama-3.1-8B</td><td>Let's break that down. It sounds like you're feeling frustrated with your partner. Can you tell me more about what specifically is causing you distress in your relationship? What are some specific issues or behaviors that you'd like to work on or change?</td></tr><tr><td>Human Reference</td><td>I'd like to hear more details about that. If relationship issues are most concerning to you, we can focus our work on that area. In our individual work together, we'll need to focus on things that you can change. Part of our session today can be brainstorming what some of those things might be.</td></tr></table>{{< /table-caption >}}
> 🔼 This table presents the performance of six Large Language Models (LLMs) on three levels of CBT tasks: basic knowledge acquisition, cognitive model understanding, and therapeutic response generation, showing that large LLMs generally perform better on knowledge-based tasks but struggle with complex tasks requiring deeper understanding of cognitive models.
> <details>
> <summary>read the caption</summary>
> Table 5: Performance of LLMs on basic CBT knowledge acquisition (CBT-QA) and cognitive model understanding (CBT-CD, CBT-PC, and CBT-FC). The precision, recall, and F1 are averaged by class portion.
> </details>

{{< table-caption >}}
<table id='2' style='font-size:14px'><tr><td>Client Statement</td><td>[Frustrated] I don't like it when you ask me if I have "catastrophic thoughts.' , Aren't catastrophes reserved for wars and natural disasters? So, no, I don't think I catastrophize. Please don't ask again.</td><td>Score</td></tr><tr><td>Llama-3.1-8B</td><td>I understand your frustration, and it's valid to feel that way when we challenge your thoughts. However, catastrophizing isn't limited to wars and natural disas- ters; it's a thought pattern where we exaggerate the consequences of a situation, making it seem more severe or overwhelming than it actually is. Can we explore what makes you uncomfortable about this concept, and how it relates to your current concerns?</td><td>-</td></tr><tr><td>Human Reference</td><td>It seems like my words upset you, and I totally get it. Here I am using a CBT term that I assumed would be relevant you, when in fact it's not. I really should not have made that assumption, and I'll do better to check in. In fact, I wonder if you find any part of focusing on your cognitions to be useful?</td><td>-</td></tr><tr><td>Criteria I</td><td>Momentarily step away from the CBT change agenda</td><td>- 1</td></tr><tr><td>Criteria 2</td><td>Empathically explore the client's experience of treatment and you</td><td>- 1</td></tr><tr><td>Criteria 3</td><td>Validate clients experience and "roll with" versus challenging their resistance</td><td>0</td></tr><tr><td>Criteria 4</td><td>Support clients' autonomy and elicit their motivation for pursuing valued direc- tions</td><td>-1</td></tr></table>{{< /table-caption >}}
> 🔼 Table 5 presents the performance of six Large Language Models (LLMs) on tasks assessing basic CBT knowledge and cognitive model understanding, showing accuracy for CBT-QA and weighted precision, recall, and F1 scores for other datasets.
> <details>
> <summary>read the caption</summary>
> Table 5: Performance of LLMs on basic CBT knowledge acquisition (CBT-QA) and cognitive model understanding (CBT-CD, CBT-PC, and CBT-FC). The precision, recall, and F1 are averaged by class portion.
> </details>

{{< table-caption >}}
<table id='4' style='font-size:14px'><tr><td>Client Statement</td><td>[Defeated] You know, I've felt a lot better these past few weeks, and I honestly wonder if it's because I stopped doing those exercises you gave me. I mean, maybe writing down my thoughts and trying to relax is making me worse · · · maybe this is just who I am, and this is the best that I can feel, and I just need to learn to live with that.</td><td>Score</td></tr><tr><td>GPT-4o</td><td>It sounds like you're feeling quite discouraged right now. It's great that you've been feeling better, but it's also important to consider if avoiding the exercises might have short-term relief but long-term consequences. Sometimes, initial resistance to new techniques is a part of the process. Could we explore if there might be aspects of the exercises that could be adapted to better fit your needs? CBT works best with some trial and error, and finding what genuinely helps you long-term is our goal.</td><td>-</td></tr><tr><td>Human Reference</td><td>I can hear in your voice how painful it is to feel like this might be the best you can ever feel. And, it sounds like one of the major reasons you're feeling this way is that the exercises I've given you may be making things worse instead of better. So, I want to say that different strategies work for different people, and there are all kinds of strategies that we can try to help you get to where you would like to be. Can we discuss what that might look for you?</td><td>-</td></tr><tr><td>Criteria</td><td>Momentarily step away from the CBT change agenda</td><td>0</td></tr><tr><td>Criteria 2</td><td>Empathically explore the client's experience of treatment and you</td><td>-1</td></tr><tr><td>Criteria 3</td><td>Validate clients' experience and "roll with" versus challenging their resistance</td><td>-1</td></tr><tr><td>Criteria 4</td><td>Support clients' autonomy and elicit their motivation for pursuing valued direc- tions</td><td>- 1</td></tr></table>{{< /table-caption >}}
> 🔼 Table 5 presents the performance of six Large Language Models (LLMs) on tasks assessing basic CBT knowledge and cognitive model understanding, reporting accuracy, precision, recall, and F1 scores across different datasets.
> <details>
> <summary>read the caption</summary>
> Table 5: Performance of LLMs on basic CBT knowledge acquisition (CBT-QA) and cognitive model understanding (CBT-CD, CBT-PC, and CBT-FC). The precision, recall, and F1 are averaged by class portion.
> </details>

{{< table-caption >}}
<table id='0' style='font-size:14px'><tr><td>Case</td><td>Unrecognized Disorder</td><td>Reason</td></tr><tr><td>Situation: My anxiety used to be worse a couple of years ago, but now I'm just paranoid. I'm always thinking that people think I'm a loser, and I won't leave the house without makeup, because I am horrified about what other people think about me. Thoughts: Because my anxiety felt worse before, this must be a normal level of anxiety and paranoia, so my conclusions make more sense. People do think I'm a loser or that I'm ugly. I at least wear makeup so they can't see how ugly I am, and ifI avoid people altogether, then they won't know how much of a loser I am or how boring I am. I don't like who I am, and whatever people think of me is probably way worse than I think it is.</td><td>Overgeneralization</td><td>The model focuses on the client's fear of judgment and anxiety in social situations rather than recognizing the gen- eralized, negative self-beliefs in- dicated by "People do think I'm a loser or that I'm ugly".</td></tr><tr><td>Situation: It's all my fault most likely all I do is constantly worry about everything. Thoughts: I should be able to control others around me, and when I can't, I cope with it by worrying. If someone is making decisions I disagree with, I should worry. There is something wrong with me that I can't control others. I am doing everything wrong.</td><td>Should statements</td><td>The model fail to focus on the client's statement "I should be able to control others around me" , which is a clear indicator of "Should statements" disorder.</td></tr><tr><td>Situation: I have been recently dealing with weird behavior...I have also been getting angry over small issues that should have little effect on me. But lately, it's been having huge effects on me...It may sound like I'm a brat... Thoughts: I am con- fused about what is happening...I need an explanation for these changes to my mood...I feel out of control...I cannot control my behavior...my behavior and feelings are fused together... what I'm feeling is wrong...</td><td>Mental filter</td><td>The client is experiencing the complexity of emotional dis- tress, which may cause the fea- ture of "Mental filter" being overlooked.</td></tr><tr><td>Case</td><td>Wrongly Recognized Disorder</td><td>Reason</td></tr><tr><td>Situation: I have been with my girlfriend for 5 years and we have a history of a strong sexual intimacy connection. This has been getting worse over time. Thoughts: It is my girlfriend's sex drive that is the problem.</td><td>Personalization</td><td>This client attributes the issue solely to his girlfriend rather than examining internal or re- lational factors. The model's misidentification as "personal- ization" (taking excessive per- sonal responsibility) could stem from misinterpreting the client's statements.</td></tr><tr><td>Situation: I am struggling at the moment and yet I am aware that I should be feeling good. Thoughts: What I am feeling and going through is unacceptable and wrong. There is a right and wrong way to go through this and I am doing it the wrong way.</td><td>All-or-nothing thinking</td><td>The core issue lies more in self- judgment and difficulty accept- ing emotional experiences, not binary thinking. The misidentifi- cation by the model could occur because both patterns involve rigid judgments.</td></tr><tr><td>Situation: I am finding younger girls sexually arousing. Thoughts: I am worried about whether or not this will go away later in life, this is horrible, and I even feel guilty constantly, I cannot help it.</td><td>magnification</td><td>This patient is merely express- ing reasonable concerns based on their current situation; it is rational and not an unjustified exaggeration. The misidentifica- tion by the model may caused by solely concentrating on the client's negative statements.</td></tr></table>{{< /table-caption >}}
> 🔼 Table 5 presents the performance of six Large Language Models (LLMs) on tasks assessing basic CBT knowledge and cognitive model understanding, showing that large LLMs perform better on knowledge questions but struggle with complex cognitive tasks.
> <details>
> <summary>read the caption</summary>
> Table 5: Performance of LLMs on basic CBT knowledge acquisition (CBT-QA) and cognitive model understanding (CBT-CD, CBT-PC, and CBT-FC). The precision, recall, and F1 are averaged by class portion.
> </details>

{{< table-caption >}}
<table id='0' style='font-size:14px'><tr><td>Case</td><td>Unrecognized Core Belief</td><td>Reason</td></tr><tr><td>Situation: She is everything I ever wanted in a woman and I am so happy to have her in my life. Unfortunately, I am not her first in many things, if anything at all, and that is very hurtful and distressing to me. Thoughts: IfI'm not her first, she won't love me forever. She will leave me because I'm not special to her. She is everything to me. If she leaves me, I will be nothing. I won 't ever be able to find someone as amazing as she is. I think she's lying to me about her virginity, which just means she is probably lying about her feelings for me, too, and it's only a matter of time before she realizes it and leaves me.</td><td>I am needy</td><td>The model may have concen- trated on the client's suspicions about the partner's virginity and honesty, viewing the issue as in- security or control, rather than emotional dependency.</td></tr><tr><td>Situation: I met this guy a month ago, and we hung out and kissed, but in front of his sister, he told me I was too young for him and he only wanted to be friends. Now he supposedly has a girl that he spends all his time with after work and he doesn't text me anymore. Thoughts: I don't deserve love. There is something wrong with me. His new girl has something that I don't; that's why he is spending time with her and not me. I will be alone forever. I will always be rejected by everyone I care about. Nobody likes me.</td><td>I am needy</td><td>The model may have interpreted the client's thoughts as purely low self-esteem or fear of rejec- tion, rather than recognizing the underlying emotional need for constant validation.</td></tr><tr><td>Situation: I have recently recovered from cancer, gained weight, I and lack confidence in myself. I feel alone in my life. I still work but that is all there is. My wife and I get along but there is no emotional closeness between us. I have no close friends. Thoughts: I am a loser. I am a failure. Something is wrong with me. My wife deserves better than me. My wife doesn't love me anymore because I have gained weight. There is nothing enjoyable in my life, ever. There is absolutely nothing to look forward to. Me and my wife NEVER connect. I am all alone. Nobody loves me. This will never get any better. There is nothing I can do about it. The world is against me and it's out of my hands. I am a waste of space. Maybe cancer should have killed me.</td><td>don't deserve to live</td><td>The model might have missed the suicidal thoughts indicated by the statements like "There is nothing enjoyable in my life" and "Maybe cancer should have killed me".</td></tr><tr><td>Case</td><td>Wrongly Recognized Core Belief</td><td>Reason</td></tr><tr><td>Situation: For the past 3 months I've been feeling really down, having mood swings, irritability - I have no reason to be and I feel like I'm going crazy and that I can't talk to anybody about this because I'm being overly dramatic. Thoughts: Something is wrong with me. I am losing my mind. Nobody understands me. Everyone would reject me if they knew.</td><td>I am helpless</td><td>The client's thought, "Nobody understands me,' suggests a need for connection and vali- dation, which the model might have missed by emphasizing helplessness.</td></tr><tr><td>Situation: When I go to the store, I believe that I hear peo- ple talking about me in their heads, as though I can hear their thoughts. Thoughts: I am capable of hearing other people's thoughts. People are talking to me in their heads. I am telepathic. I am certain of these things. Because I hear voices, they must be coming from other people.</td><td>I am out of control</td><td>The client's thoughts reflect con- viction (e.g., "I am telepathic") rather than fear, indicating a be- lief in special abilities rather than being out of control. The model may not be very clear about the difference between the two.</td></tr><tr><td>Situation: I have a problem of automatically looking at things like shiny objects or body parts. I don't have any bad intentions but people misunderstand me. Thoughts: This is something to be ashamed of. I always do it. Something is wrong with me. I stop looking at these things. People will reject me because of this habit. This habit is out of my control.</td><td>I am immoral</td><td>The client explicitly states they have no bad intentions, indicat- ing the issue is about loss of con- trol, not morality. The model can't may have neglected this infor- mation.</td></tr></table>{{< /table-caption >}}
> 🔼 Table 5 presents the performance of six large language models on tasks assessing basic CBT knowledge and cognitive model understanding, showing accuracy and F1 scores across datasets.
> <details>
> <summary>read the caption</summary>
> Table 5: Performance of LLMs on basic CBT knowledge acquisition (CBT-QA) and cognitive model understanding (CBT-CD, CBT-PC, and CBT-FC). The precision, recall, and F1 are averaged by class portion.
> </details>

{{< table-caption >}}
<table id='0' style='font-size:14px'><tr><td>Project: CBT Dataset Annotation / Batch: test</td><td></td><td>□ Auto-accept next Task</td><td>Return Task</td><td></td><td>Skip Task</td><td>Expires in 23:58</td></tr><tr><td colspan="4">Step 2: Based on the situation and the automatic negative thoughts, select the type(s) of cognitive distortions involved. Aim for comprehensiveness but limit your selection to a maximum of three types. If there are more than three distortions present, prioritize the three most significant ones.</td><td></td><td></td><td></td></tr><tr><td colspan="4">Select up to 3 distortion types:</td><td></td><td></td><td></td></tr><tr><td colspan="4">□ All-or-nothing thinking</td><td></td><td></td><td></td></tr><tr><td colspan="4">□ Overgeneralization</td><td></td><td></td><td></td></tr><tr><td colspan="4">□ Mental filter</td><td></td><td></td><td></td></tr><tr><td colspan="4">□ Should statements</td><td></td><td></td><td></td></tr><tr><td colspan="4">□ Labeling</td><td></td><td></td><td></td></tr><tr><td colspan="4">□ Personalization</td><td></td><td></td><td></td></tr><tr><td colspan="4">□ Magnification</td><td></td><td></td><td></td></tr><tr><td colspan="4">□ Emotional Reasoning</td><td></td><td></td><td></td></tr><tr><td colspan="3">□ Mind Reading</td><td></td><td></td><td></td><td></td></tr><tr><td colspan="3">□ Fortune-telling</td><td></td><td></td><td></td><td></td></tr><tr><td colspan="4">Step 3: Select one or more major categories from {helpless, unloveable, and worthless}</td><td></td><td></td><td></td></tr><tr><td colspan="4">Select up to 3 major core belief types:</td><td></td><td></td><td></td></tr><tr><td colspan="3">□ Helpless</td><td></td><td></td><td></td><td></td></tr><tr><td colspan="3">□ Unloveable</td><td></td><td></td><td></td><td></td></tr><tr><td colspan="3">□ Worthless</td><td></td><td></td><td></td><td></td></tr><tr><td colspan="7"></td></tr><tr><td>Select up to 3 fine-grained core belief types for category Helpless:</td><td></td><td>Select up to 3 fine-grained core belief types for category Unloveable:</td><td>Select up to 3 fine-grained core belief types for category Worthless:</td><td></td><td></td><td></td></tr><tr><td>□  am incompetent.</td><td>□ I am unlovable.</td><td>□ I am worthless/waste.</td><td></td><td></td><td></td><td></td></tr><tr><td>□ I am helpless.</td><td></td><td>□ I am unattractive.</td><td>□ I am immoral.</td><td></td><td></td><td></td></tr><tr><td>□ I am powerless/weak/vulnerable.</td><td></td><td>□ I am undesirable/unwanted.</td><td>□ I am bad · dangerous/toxic/evil.</td><td></td><td></td><td></td></tr><tr><td>□ I am a victim.</td><td></td><td>□ I am bound to be rejected.</td><td>□ I don't deserve to live.</td><td></td><td></td><td></td></tr><tr><td>□ I am needy.</td><td></td><td>□ I am bound to be abandoned.</td><td></td><td></td><td></td><td></td></tr><tr><td>□ I am trapped.</td><td></td><td> I am bound to be alone.</td><td></td><td></td><td></td><td></td></tr><tr><td>□ I am out of control.</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>□ I am a failure/loser.</td><td></td><td></td><td></td><td></td><td></td><td></td></tr><tr><td>□ I am defective.</td><td></td><td></td><td></td><td></td><td></td><td></td></tr></table>{{< /table-caption >}}
> 🔼 The table shows the types of knowledge covered in the CBT-QA dataset, example question-answer pairs for each type, and the percentage of questions belonging to each type.
> <details>
> <summary>read the caption</summary>
> Table 1: Knowledge types in CBT-QA, with example QA pairs and distributions in the test set.
> </details>

</details>


### Full paper

{{< gallery >}}
<img src="https://ai-paper-reviewer.com/2410.13218/1.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/2.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/3.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/4.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/5.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/6.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/7.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/8.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/9.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/10.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/11.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/12.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/13.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/14.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/15.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/16.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/17.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/18.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/19.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/20.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/21.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/22.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/23.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/24.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/25.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/26.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/27.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/28.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/29.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/30.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/31.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/32.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/33.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/34.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
<img src="https://ai-paper-reviewer.com/2410.13218/35.png" class="grid-w50 md:grid-w33 xl:grid-w25" />
{{< /gallery >}}