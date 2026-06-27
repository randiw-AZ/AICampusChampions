### Reading Guide

Complete readings BEFORE attempting tasks. Annotate as you read — your notes feed directly into the tasks below

### Reading 1: [Chain-of-Thought Prompting Elicits Reasoning in LLMs](https://proceedings.neurips.cc/paper_files/paper/2022/file/9d5609613524ecf4f15af0f7b31abca4-Paper-Conference.pdf) (Wei et al., 2022\)

What to look for as you read:

* The definition of chain-of-thought prompting in Section 2 — exactly what is added to the prompt and why.  
* Figure 1: the side-by-side comparison of standard prompting vs. CoT prompting on the same problem. Notice the quality difference.  
* The 'emergent' nature of CoT benefits — they appear only above a model scale threshold (\~100B parameters). This has implications for which tools you can expect CoT to help with.  
* The tasks where CoT helps most vs. least — does your professional task domain fall into the 'helps' category?

Guided reading questions (annotate answers as you go):

* Q1: What exactly is added to a prompt to make it a 'chain-of-thought' prompt? Reproduce the structure from Figure 1 in your own words.

An example of Q\&A reasoning is provided to the LLM so it can model the same type of reasoning to answer a new problem.

* Q2: Wei et al. report that CoT benefits are 'emergent' — they appear only in sufficiently large models. What does this imply for practitioners using smaller or older LLMs?

Smaller or older LLMs may not have sufficient training to do CoT. The CoT benefit is only observed for larger models, and this requirement was not created intentionally, but was only observed after trial and error with the larger models. 

* Q3: The paper tests CoT on arithmetic, symbolic reasoning, and commonsense reasoning tasks. Which of these task types is most analogous to tasks you perform professionally?

Commonsense reasoning

* Q4: What is the key limitation of the few-shot CoT approach identified by the authors? Does this concern apply to your planned Task 2 use case?

For me, the key limitation is coming up with examples to provide to the LLM. For the authors, the key limitation is a larger language model, presumably with more training data sets, to do reasoning steps. 

Key terms — write your own definition after reading:

| Term | Your definition (in your own words) |
| ----- | ----- |
| Chain-of-thought prompting | A series of intermediate natural language reasoning steps that “train” a sufficiently large LLM to arrive at the correct output. It basically asks the LLM to “show their work”. Established by using a prompt “triple”. |
| Zero-shot prompting | Standard prompting \- simply asking an LLM to perform a task (e.g.,. a complex question) without providing any examples of the answer and expecting the LLM to generate the correct answer.  |
| Few-shot prompting | Fine-tuning (e.g., providing in-context learning to) a model by giving it a few examples of inputs and outputs.  |
| Reasoning chain | Intermediate steps in the reasoning process; a step-by-step sequence of logical thoughts used to solve a problem |
| Emergent ability | An unintended consequence of training an LLM; unprogrammed, novel behaviors and skills that spontaneously appear in a LLM once the system reaches a certain threshold of scale, complexity, or parameter size |

### Reading 2: [Survey of Hallucination in Natural Language Generation](https://dl.acm.org/doi/full/10.1145/3571730) (Ji et al., 2023\)

What to look for as you read:

* The formal definition of hallucination in Section 2.1 — note that it distinguishes between faithful and factually grounded content.  
* The intrinsic vs. extrinsic hallucination distinction in Section 2.2 — which is more dangerous in professional document contexts?  
* The causes of hallucination listed in Section 2.3 — connect these to the LLM training process you learned about in Module 1\.  
* Any hallucination type that could specifically arise in the professional documents you produce (reports, emails, research summaries, student feedback).

Guided reading questions (annotate answers as you go):

* Q1: How does Ji et al. formally define hallucination in NLG? What is the relationship between 'faithfulness' and 'factuality' in their framework?

A hallucination in NLG is generated content that is nonsensical or unfaithful to the source content. 

* Q2: What is the difference between intrinsic and extrinsic hallucination? Give one example of each that could occur in an academic professional document.

Intrinsic hallucinations are not consistent (faithful) to the source material. An example would be a indicating that insulin is released by the pancreatic alpha cells when the source indicates insulin is released by the pancreatic beta cells. Extrinsic hallucinations are not verifiable from the source material. An example would be stating that a patient has diabetes without confirmation from lab results. 

* Q3: The paper identifies several causes of hallucination in the training process. Which cause do you think is hardest to mitigate through prompt engineering alone?

I think extrinsic would be harder to mitigate through prompt engineering alone. I think RAG is a way to minimize hallucinations that forces the LLM to check the source material to ensure faithfulness, although I’m not sure about this. 

* Q4: Based on the taxonomy in Section 2, what type of hallucination would you most need to guard against in the professional tasks you identified in your Module 1 reflection?

Looking back at my Module 1 reflection B, I think I may be more concerned about extrinsic hallucinations. It’s possible for generated content to be faithful to source material, but that source material may be mislabeled in the model. This could introduce misinformation or bias into the generated output. Therefore, it may be more important to make sure the generated output is factual, rather than faithful. 

Key terms — write your own definition after reading:

| Term | Your definition (in your own words) |
| ----- | ----- |
| Hallucinations (NLG) | Generated content that gives the impression of being correct, but is not.  |
| Intrinsic hallucination | Contradicts source content |
| Extrinsic hallucination | Cannot be verified from source content |
| Faithfulness | Staying consistent to the provided source (antonym of intrinsic hallucination) |
| Factually grounding | Based on fact (verifiiable) |

---

## Self-Paced Tasks

### Task 1: Structured Tool Comparison — Five-Task Protocol \[60 min\]

Step-by-step instructions:

1. Open Tool A and Tool B in separate browser windows. Use defaults — do not customize temperature, system prompts, or personas.  
2. Run Prompt P1 in Tool A verbatim. Record output summary and ratings. Then run P1 in Tool B verbatim. Record.  
3. Continue for P2–P5 in the same way — complete both tools for each prompt before moving to the next prompt.  
4. P1 (Factual): 'What year was the Transformer architecture first introduced in a peer-reviewed paper, and what was that paper's exact title? Please provide an APA citation.'  
5. P2 (Summarization): 'Summarize the following abstract in 100 words for a non-specialist audience: \[PASTE the abstract from Ouyang et al. 2022\. [Training language models to follow instructions with human feedback](https://proceedings.neurips.cc/paper_files/paper/2022/file/b1efde53be364a73914f58805a001731-Paper-Conference.pdf) — search 'InstructGPT abstract' or use the one in your course resources\]'  
6. P3 (Code): 'Write a Python function that accepts a list of numbers and returns a dictionary with keys mean, median, and standard\_deviation. Include a docstring and one usage example.'  
7. P4 (Professional writing): 'Draft a professional email declining a speaking invitation due to a scheduling conflict. The tone should be warm and leave the door open for future invitations. Length: 150–200 words.'  
8. P5 (Balanced argument): 'Write a two-sided argument — two sentences pro, two sentences con — on the following claim: Universities should require disclosure of all AI use in student assignments.'  
9. After completing all 10 cells, write your 3-sentence comparative synthesis at the bottom of the template.

Five-Task Comparison Matrix — complete all cells:

| Prompt | Tool A name | Output summary | Acc. (1-5) | Rel. (1-5) | Fmt. (1-5) | Tool B name | Output summary | Acc. (1-5) | Rel. (1-5) | Fmt. (1-5) |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
| P1 (Factual):  'What year was the Transformer architecture first introduced in a peer-reviewed paper, and what was that paper's exact title? Please provide an APA citation.' | Claude Sonnet 4.6 (free) | Vaswani, A., Shazeer, N., Parmar, N., Uszkoreit, J., Jones, L., Gomez, A. N., Kaiser, Ł., & Polosukhin, I. (2017). Attention is all you need. *Advances in Neural Information Processing Systems*, *30*. [https://arxiv.org/abs/1706.03762](https://arxiv.org/abs/1706.03762) Strange symbol for 1st initial in Kaiser’s 1st name arXiv is not peer-reviewed Correct APA format according to Zotero is, “Vaswani, A., Shazeer, N., Parmar, N., Uszkoreit, J., Jones, L., Gomez, A. N., Kaiser, L., & Polosukhin, I. (2017). *Attention Is All You Need* (Version 7). arXiv. https://doi.org/10.48550/ARXIV.1706.03762” | 4  | 4 | 4 | Gemini 3.1-Pro(U of A)  | Vaswani, A., Shazeer, N., Parmar, N., et al. (2017). Attention Is All You Need. *arXiv*. [https://doi.org/10.48550/arxiv.1706.03762](https://www.google.com/search?q=https://doi.org/10.48550/arxiv.1706.03762&authuser=1) arXiv is not peer-reviewed Correct APA format according to Zotero is, “Vaswani, A., Shazeer, N., Parmar, N., Uszkoreit, J., Jones, L., Gomez, A. N., Kaiser, L., & Polosukhin, I. (2017). *Attention Is All You Need* (Version 7). arXiv. https://doi.org/10.48550/ARXIV.1706.03762” | 4  | 4 | 4 |
| P2 (Summarization): 'Summarize the following abstract in 100 words for a non-specialist audience: \[PASTE the abstract from Ouyang et al. 2022\. [Training language models to follow instructions with human feedback](https://proceedings.neurips.cc/paper_files/paper/2022/file/b1efde53be364a73914f58805a001731-Paper-Conference.pdf) — search 'InstructGPT abstract' or use the one in your course resources\]' | Claude Sonnet 4.6 (free) | Reasonable summary pointing out that RLHF can post-train a smaller LLM to be more truthful and less toxic than a model that was 100X bigger.  104 words | 5 | 5 | 4 | Gemini 3.1-Pro(U of A) | Similar to Claude output; smaller version of InstructGPT vastly outperformed a much larger, standard AI model 100 words | 5 | 5 | 5 |
| P3 (Code): 'Write a Python function that accepts a list of numbers and returns a dictionary with keys mean, median, and standard\_deviation. Include a docstring and one usage example.' | Claude Sonnet 4.6 (free) | It wrote a Python function, but I don’t know how to test it. I asked Claude how to test it, and it gave me several options.  I then asked Claude how to test this in Colab.  Claude provided a test data set \[4, 8, 15, 16, 23, 42\]. When I checked it against MS Excel, the mean and median were the same, but the standard deviation was different (Claude 12.5; MS Excel 13.4) I ran Carlos’s test set \[4, 7, 13, 2,9\] and had the same problem with the standard deviation.  | 4 | 5 | 5 | Gemini 3.1-Pro(U of A) | It wrote a Python function, but I don’t know how to test it. I asked Gemini how to test it, and it gave me several options. I then asked Gemini how to test this in Colab.  The mean, median, and standard deviation were the same as what I got in MS Excel. | 5 | 5 | 5 |
| P4 (Professional writing): 'Draft a professional email declining a speaking invitation due to a scheduling conflict. The tone should be warm and leave the door open for future invitations. Length: 150–200 words.' | Claude Sonnet 4.6 (free) | Word count was 145 according to MS Word, but about 175 according to Claude.  It’s nice, but it doesn’t sound like me.  | 5 | 4 | 4 | Gemini 3.1-Pro(U of A) | Word count was 176 according to MS Word. It’s nice, but it doesn’t sound like me.  | 5 | 5 | 5 |
| P5 (Balanced argument): 'Write a two-sided argument — two sentences pro, two sentences con — on the following claim: Universities should require disclosure of all AI use in student assignments.' | Claude Sonnet 4.6 (free) | Sounds reasonable, and I agree with the overall message.  | 5 | 5 | 5 | Gemini 3.1-Pro(U of A) | Sounds reasonable, and I agree with the overall message.  | 5 | 5 | 5 |

where

* Acc. \= Accuracy (rated 1–5; factual correctness of claims you can independently verify)  
* Rel. \= Relevance (rated 1–5; how well the output addresses the prompt)  
* Fmt. \= Format (rated 1–5; appropriateness of structure, length, and presentation)

### 3-sentence comparative synthesis at the bottom of the template:

I am more willing to cognitively offload summarization, professional writing, or balancing arguments, but I would still need to verify and approve output.   
I am willing to use generative AI to gather factual information or to vibe code, but it requires more vigilance.   
Some hallucinations are more acceptable (too many or too few words) than others (factual errors). 

### Task 2: Prompt Engineering Lab \- Four-iteration refinement \[60 min\]

Step-by-step instructions:

1. Choose your target task: a real professional task that produces a document, communication, or structured content. Examples: drafting a course learning objective, writing a grant paragraph, summarizing research findings for a general audience, creating rubric criteria.  
2. Write your task in the 'My Target Task' box below before starting.  
3. VERSION 1 (Zero-shot): Write a single declarative sentence asking for the output. Nothing more.  
4. Record the V1 output summary and quality rating. Identify the two most significant weaknesses.  
5. VERSION 2 (+Role specification): Add a specific role persona before your V1 prompt. Be precise about the role (e.g., 'You are an experienced curriculum designer at a research-intensive university who specializes in writing learning objectives for interdisciplinary graduate courses.').  
6. VERSION 3 (+Few-shot example): Add one example of a high-quality output — ideally something you have actually written — before the task instruction.  
7. VERSION 4 (+Chain-of-thought): Add this instruction after your other instructions: 'Before writing, think step by step through: (1) Who is the audience? (2) What is the single most important point? (3) What tone is appropriate? Then produce the output.'  
8. Write your 150-word reflective note in the space below: What changed across iterations? Which technique produced the greatest single improvement?

Prompt Engineering Iteration Log:

| My target task (describe specifically — not 'emails' but the specific type, audience, and purpose): |
| ----- |
| I need to write an abstract for the upcoming Physiology Majors Interest Group conference. The abstract can be no more than 250 words. I am submitting my abstract for the category, “Generative AI in the classroom”. My presentation will either be a 5-minute presentation or a 15-minute workshop. The 15-minute workshops are limited to one per category. The description of the “Generative AI in the classroom” category is, “Share how you have used this technology to develop resources, in assignments, and/or addressed challenges with its use.” The abstract could include a description of the need, approach, and outcome(s) |

| VERSION 1 — Zero-shot prompt (write verbatim): |
| ----- |
| Prompt: Write an abstract for a presentation on the value of custom GPTs for the "Generative AI in the Classroom" session at the Physiology Majors Interest Group conference. |
| Model: Claude Sonnet 4.6 Low (free) |
| **Beyond the Chatbot: Leveraging Custom GPTs to Enhance Physiology Education** Generative AI tools are rapidly entering undergraduate science education, yet their default, general-purpose configurations often fall short of the precision and disciplinary depth that physiology instruction demands. Custom GPTs — purpose-built AI assistants trained on curated prompts, constraints, and domain-specific knowledge — offer a compelling alternative that transforms passive AI use into an active pedagogical tool. This presentation examines the practical value of custom GPTs in physiology coursework across three domains: concept scaffolding, active learning, and formative assessment. Drawing on implementation examples from undergraduate human physiology and pathophysiology courses, we demonstrate how instructor-designed GPTs can guide students through complex homeostatic mechanisms, generate case-based clinical scenarios on demand, and provide Socratic-style questioning that mirrors the reasoning processes expected in advanced study and professional settings. Critically, custom GPTs allow instructors to maintain curricular alignment — constraining the AI to course-relevant terminology, approved frameworks, and appropriate cognitive levels — while reducing the risk of misconceptions introduced by uncurated AI responses. We also address common faculty concerns, including academic integrity, equity of access, and the learning curve associated with GPT configuration, and offer a practical framework for designing, piloting, and iterating on custom tools within existing course structures. Attendees will leave with a clearer understanding of how custom GPTs differ from general AI assistants, concrete strategies for building their own course-specific tools, and a frank discussion of where these technologies succeed and where human instruction remains irreplaceable. No prior AI experience is required. |
| Summary: I didn’t provide enough information about what I want to focus on in my presentation and how much time I'll have. Claude did hit upon a general topics and specific topics I plan to include: 1\) case studies, 2\) Socratic tutors, and 3\) no prior coding experience needed.  |

| V1 output quality (1–5): \_\_\_. Two weaknesses I identified: |
| ----- |
| Quality: 1 Weakness 1: Whenever I see the word “leverage”, I automatically think the text is AI-generated. I also think “AI-generated” when I see em dashes. Weakness 2: The abstract is broad, but generic, and it doesn’t sound like me. |

| VERSION 2 — \+Role specification (write verbatim — include V1 plus new role addition): |
| ----- |
| Prompt: You are a senior lecturer at a major public university who specializes in using custom GPTs  for case study assignments in upper-division undergraduate physiology courses. Write an abstract for a presentation on the value of custom GPTs for the "Generative AI in the Classroom" session at the Physiology Majors Interest Group conference. |
| Model: Claude Sonnet 4.6 Low (free) |
| **Beyond the Black Box: Leveraging Custom GPTs as Scaffolded Learning Tools in Undergraduate Physiology** Generative AI tools have arrived in undergraduate classrooms whether faculty are ready or not, yet most course policies still treat student AI use as a binary problem to be permitted or prohibited. This presentation argues for a third path: the deliberate design of custom large language model (LLM) applications as pedagogical instruments embedded directly into course structure. Drawing on two years of iterative implementation in upper-division physiology courses at a major public research university, I describe a framework for deploying custom GPTs as case study facilitators that guide students through clinical reasoning without simply handing them answers. Custom GPTs differ meaningfully from general-purpose AI assistants in their capacity for constraint. By controlling the system prompt, instructors can define a persona, restrict scope, require students to articulate their reasoning before receiving feedback, and calibrate the level of scaffolding to match course learning objectives. In physiology case studies — where the goal is for students to connect molecular mechanisms to organ-system dysfunction to patient presentation — this scaffolding function is particularly well-suited to the format. A well-designed custom GPT can ask a struggling student the right Socratic question rather than generating a polished paragraph that forecloses their own thinking. I present assessment data comparing student performance on case study examinations before and after custom GPT integration, alongside qualitative findings from structured reflections in which students articulate how they used the tool and what they learned from the interaction. Results suggest that students who engaged with the custom GPT in iterative, dialogic ways — rather than as a one-shot answer generator — demonstrated stronger conceptual transfer on novel cases. I also address the practical dimensions of implementation, including prompt engineering strategies accessible to faculty without programming backgrounds, IRB considerations for collecting student interaction data, and common failure modes to anticipate. The broader argument is that faculty-designed AI tools give instructors something that blanket AI policies do not: visibility into the reasoning process. When a custom GPT is structured to require students to commit to a hypothesis before receiving any response, the transcript of that interaction becomes a new kind of learning artifact — one that reveals how students think, not just what they ultimately write. |
| Summary: This is way too long\! I didn’t provide information about length.  |

| V2 output quality (1–5): \_\_\_. What improved vs. V1: |
| ----- |
| Quality: 2 |
| What improved vs V1: This version does a better job of explaining why custom GPTs are useful for case studies and why faculty might want to incorporate them into their workflow. It also talks about how the tool promotes critical thinking for students.  |

| VERSION 3 — \+Few-shot example (paste or describe your example, then the prompt): |
| ----- |
| Prompt: You are a senior lecturer at a major public university who specializes in using custom GPTs for case study assignments in upper-division undergraduate physiology courses. Write an abstract for a presentation on the value of custom GPTs for the "Generative AI in the Classroom" session at the Physiology Majors Interest Group conference. Use the content of the uploaded file when writing the abstract. Uploaded title and abstract: **Unleash the power of custom GPTs to increase student engagement and teach AI skills** Custom GPTs are customized versions of Large Language Models (LLMs) trained to perform specific tasks. Creating custom GPTs doesn’t require any coding skills. I use custom GPTs to play the role of patients for case study assignments in my physiology courses. An example of a role-playing custom GPT is Joe, a patient whose chief complaint is a sore throat and a cough ([https://box.boodle.ai/a/@Joe\_R\_Interview](https://box.boodle.ai/a/@Joe_R_Interview)). Students interview Joe to create and refine a differential diagnosis. The custom GPT doesn’t do anything until it is prompted by the student, creating an opportunity to create meaningful engagement for students as they learn about differential diagnosis and clinical reasoning. A custom GPTs requires 3 main components: 1\) a profile indicating the role it will be playing, 2\) instructions about how to behave, and 3\) a base LLM to power the conversation. Feedback from students has been overwhelmingly positive, as they see the potential for AI to create immersive experiential learning. Honors and graduate students in my courses use AI build their own case studies and create their own role-playing custom GPTs. Students learn how to construct and test their own custom GPTs. Along the way, they learn about course content, real-world applications of physiology, and AI skills including meta-prompting and red-teaming. Students enjoy learning about the behind-the-scenes workings of AI-enhanced tools and the power of AI to bridge the gap between coding and software applications. Free custom GPT tools to explore in 2026 include BoodleBox (box.boodle.ai), Gemini Gems, Jotform.com, and Poe.com. |
| Model: Claude Sonnet 4.6 Low (free) |
| **Engaging Students and Building AI Literacy Through Custom GPTs in Undergraduate Physiology** As generative AI reshapes higher education, physiology instructors face both a challenge and an opportunity: how do we harness these tools to deepen disciplinary learning while preparing students for an AI-fluent world? This presentation describes a scalable, no-code approach to integrating custom large language models (LLMs) into upper-division undergraduate physiology courses through role-playing patient simulations. Custom GPTs are purpose-built versions of LLMs configured to perform specific tasks without requiring any programming expertise. In this course model, custom GPTs portray standardized patients with defined chief complaints — for example, a patient presenting with sore throat and cough — whom students must interview to construct and iteratively refine a differential diagnosis. Because the GPT remains passive until prompted, students must drive the clinical encounter, creating active, inquiry-based engagement with course content. Each custom GPT is built from three core components: a character profile defining the patient's role, a behavioral instruction set, and an underlying LLM to power the dialogue. Student response has been strongly positive, with many recognizing the potential of AI to support immersive, experiential learning. In honors and graduate sections, the model extends further: students design their own patient case studies and build their own role-playing custom GPTs, gaining hands-on experience with meta-prompting, red-teaming, and the iterative process of AI tool development. In doing so, they simultaneously deepen their understanding of physiology, explore real-world clinical applications, and develop transferable AI literacy skills. This presentation will discuss pedagogical design considerations, lessons learned from implementation, and freely available platforms that instructors can use to create their own custom GPTs in 2026\. Attendees will leave with a practical framework for incorporating patient simulation AI into their own physiology courses. |
| Summary: This version captures the essence of what I want to present at the conference. I recognize my own narrative in Claude’s output. Many phrases are reworded in a way that sounds better than what I wrote, but still retains my voice.  |

| V3 output quality (1–5): \_\_\_. What improved vs. V2: |
| ----- |
| Quality: 4 |
| Improvement vs V2: Claude reminded me of a principle I want to promote: AI is a double-edged sword. Claude phrased this as “both a challenge and an opportunity”. I forgot to add that to my abstract, and it works well here. I also like Claude’s title better than the one I wrote.  |

| VERSION 4 — \+Chain-of-thought instruction (write full verbatim V4 prompt): |
| ----- |
| Prompt:  |
| Model: Claude Sonnet 4.6 Low (free):  |
| **Step-by-step thinking before writing: 1\. Who is the audience?** Physiology educators at a disciplinary conference (PMIG) — likely a mix of faculty, instructors, and graduate teaching assistants who teach physiology at the undergraduate level. They understand the content domain but may range widely in AI fluency. They care about pedagogy, student outcomes, and practical implementation. **2\. What is the single most important point?** Custom GPTs can be built by anyone — no coding required — and when used as interactive patient role-play tools, they create active, student-driven learning experiences while also teaching transferable AI literacy skills. **3\. What tone is appropriate?** Professional but accessible. Conference abstracts in education sessions tend to be collegial and evidence-leaning without being heavily quantitative. The tone should convey enthusiasm grounded in classroom practice, not hype. Here is the abstract: **Unleashing the Power of Custom GPTs to Increase Student Engagement and Teach AI Skills** As generative AI becomes embedded in health professions and biomedical research, physiology educators face a dual imperative: teach disciplinary content rigorously while preparing students to work alongside AI tools thoughtfully. Custom GPTs — large language model (LLM)-based chatbots configured for specific roles and tasks — offer a practical, no-code solution that addresses both goals simultaneously. In my upper-division physiology courses, I deploy custom GPTs as interactive patient simulations for case study assignments. Students interview a virtual patient, such as Joe, a patient presenting with a sore throat and cough, to construct and iteratively refine a differential diagnosis. Because the GPT responds only when prompted, the student drives the clinical encounter, fostering active engagement and higher-order reasoning rather than passive consumption of AI-generated content. Student feedback has been consistently and strongly positive, with many citing the immersive, experiential quality of the interactions. Beyond their use as pedagogical tools, custom GPTs serve as a vehicle for teaching AI literacy. Honors and graduate students in my courses design and test their own patient simulations, gaining hands-on experience with meta-prompting, red-teaming, and the structural components that make an AI tool function effectively — namely, a defined role, behavioral instructions, and a base LLM. In building these tools, students integrate course content, explore real-world applications of physiology, and develop a nuanced understanding of how AI bridges the gap between complex software and practical use. Building a custom GPT requires no programming background. Free platforms available in 2026 — including BoodleBox, Gemini Gems, Jotform, and Poe — lower the barrier to entry for both instructors and students. This presentation will provide a practical framework for designing role-playing custom GPTs for physiology education and offer strategies for scaling their use across course levels. *Word count: \~270* |
| Summary: This version is similar to the one in V3, but with more jargon. I actually prefer the wording in V3.  |

| V4 output quality (1–5): \_\_\_. What improved vs. V3: |
| ----- |
| Quality: 4 |
| What improved vs V3: More technical language is included, which may be good for an education conference. I haven’t been to a conference, and I haven’t published a scientific article in about 20 years.  |

| 150-word reflective note — which technique produced the biggest jump? What remains unresolved? |
| ----- |
| Biggest jump: Few-shot prompting (providing my abstract draft) |
| Remains unresolved: I may still be over the word count limit (250). I sent my original draft to a colleague who went to the conference recently to get their feedback. There are just some things the generative AI doesn’t know, such as participant interest and comfort with AI-related topics.  |

### Task 3: Hallucination Detection Audit \[45 min\]

Step-by-step instructions:

1. Access the five Module 2 audit texts from the course platform (Texts A–E, one paragraph each).  
2. Before reading any text, set up your verification tools in separate tabs: Google Scholar, your institutional library database, and one specialist resource for your field.  
3. For Text A: read slowly. Extract EVERY discrete factual claim as a separate row (dates, names, statistics, causal relationships, paper titles, institutional facts). Verify each claim. Note the hallucination type using Ji et al.'s taxonomy.  
4. Repeat for Texts B–E. Take 8–9 minutes per text.  
5. After completing all five, calculate your detection rate: claims correctly identified as errors ÷ total actual errors (from answer key).  
6. Write 2–3 sentences on: What type of hallucination was hardest to detect, and why?

Hallucination Audit Log — add rows as needed for each claim:

| Text | Claim (verbatim or paraphrased) | Accurate?  Y/N/Uncertain | Verification Source | Hallucination type | Severity Low/Med/High |
| ----- | ----- | ----- | ----- | ----- | ----- |
| A | modern Olympic Games were revived in 1900 | N (1986) | 1\. The Modern Olympic Games–A Globalised Cultural and Sporting Event, Procedia \- Social and Behavioral Sciences, Volume 92, 2013, Pages 728-734, ISSN 1877-0428, https://doi.org/10.1016/j.sbspro.2013.08.746.  | Intrinsic | High |
|  | In Paris | U (revived in Paris, competition in Athens) | 1 | Intrinsic | Med  |
|  | French educator Pierre de Coubertin | U, I think he was an artist | 1 | Factual | Med |
|  | who believed sport could promote international peace and understanding | ? |  | Factual |  |
|  | 14 nations | Y | 1 | Intrinsic |  |
|  | 250 athletes | N (245) | 1 | Intrinsic | Low |
|  | athletics, cycling, and swimming | ? |  |  |  |
|  | Women were not permitted to compete until the 1920 Antwerp Games | 1900 in Paris  | 1 | Intrinsic | High |
|  | Olympic motto, *Citius, Altius, Fortius* | Y | 2\. The Journal of Philosophy, Science & Law  Volume 10, Issue 6, November 2010, pages 1-17   |  |  |
|  | meaning "Faster, Higher, Stronger" | Y | 2 |  |  |
|  | was adopted at the inaugural modern Games | ? |  | Factual |  |
| B | adults require between 7 and 9 hours of sleep per night for optimal cognitive function | Y | Molly E. Zimmerman, Giada Benasi, Christiane Hale, Lok-Kin Yeung, Justin Cochran, Adam M. Brickman, Marie-Pierre St-Onge, The effects of insufficient sleep and adequate sleep on cognitive function in healthy adults, Sleep Health, Volume 10, Issue 2, 2024, Pages 229-236, ISSN 2352-7218, https://doi.org/10.1016/j.sleh.2023.11.011. |  |  |
|  | During REM, body repairs muscle tissue and releases growth hormone | ? |  | Factual | Med |
|  | Chronic sleep deprivation of fewer than 6 hours per night has been linked to increased risk of cardiovascular disease, obesity, and impaired immune response | Y | Yang Q, Durmer JL, Wheaton AG, Jackson SL, Zhang Z. Sleep duration and excess heart age among US adults. Sleep Health. 2018 Oct;4(5):448-455. doi: 10.1016/j.sleh.2018.07.001. Epub 2018 Jul 30\. PMID: 30241660; PMCID: PMC10913064. |  |  |
|  | The average adult takes approximately 7 minutes to fall asleep under normal conditions | ? |  | Factual | Med  |
| C | Amazon rainforest spans approximately 5.5 million square kilometers | N (7 million sq km) | [https://en.wikipedia.org/wiki/Amazon\_rainforest](https://en.wikipedia.org/wiki/Amazon_rainforest) and [https://www.britannica.com/place/Amazon-River/Physical-features](https://www.britannica.com/place/Amazon-River/Physical-features)  | Intrinsic | Med  |
|  | nine South American countries | Y | https://en.wikipedia.org/wiki/Amazon\_rainforest |  |  |
|  | 400 billion individual trees representing more than 16,000 species | Y (390 billion; 16,000) | Fauset, S., Johnson, M., Gloor, M. *et al.* Hyperdominance in Amazonian forest carbon cycling. *Nat Commun* **6**, 6857 (2015). https://doi.org/10.1038/ncomms7857 |  | Low |
|  | 2019 report by the World Wildlife Fund found that 30% of the Amazon had been deforested since systematic monitoring began in 1970 | N (report published in 2022\) | [https://www.worldwildlife.org/](https://www.worldwildlife.org/) and chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/[https://wwfint.awsassets.panda.org/downloads/lar\_\_ingles\_23\_dic\_2022.pdf](https://wwfint.awsassets.panda.org/downloads/lar__ingles_23_dic_2022.pdf)  | Factual | Med  |
|  | Amazon River itself discharges approximately 20% of all fresh water that flows into the world's oceans | N (15%) | chrome-extension://efaidnbmnnnibpcajpcglclefindmkaj/[https://pubs.usgs.gov/unnumbered/70046378/report.pdf](https://pubs.usgs.gov/unnumbered/70046378/report.pdf)  | Factual | Med  |
| D | Marie Curie was a Polish-born | Y | https://en.wikipedia.org/wiki/Marie\_Curie |  |  |
|  | She was the first woman to win a Nobel Prize | Y | https://en.wikipedia.org/wiki/Marie\_Curie |  |  |
|  | receiving the Nobel Prize in Chemistry in 1903 for her discovery of polonium and radium | 1903 prize was for Physics (shared discovery) | https://en.wikipedia.org/wiki/Marie\_Curie | Intrinsic | Low  |
|  | first person to win Nobel Prizes in two different sciences, | 1911 prize for Chemistry | https://www.nobelprize.org/stories/women-who-changed-science/marie-curie/ | Intrisic | Low |
|  | second Nobel Prize in Physics in 1911 |  |  |  |  |
|  | first woman appointed as a professor at the University of Warsaw, where she taught for most of her career | Paris, not Warsaw | https://www.nobelprize.org/stories/women-who-changed-science/marie-curie/ | Intrinsic | Low |
| E | The Internet and the World Wide Web are the same technology,  | N (web runs on top of internet) | https://en.wikipedia.org/wiki/History\_of\_the\_World\_Wide\_Web | Intrinsic | Med |
|  | developed together in the late 1980s  | N (internet is from ARPANET, WWW is a more recent innovation) | https://medium.com/@fortune.nwuneke/beyond-the-surfing-distinguishing-between-the-internet-and-the-world-wide-web-7618be263cfe | Intrinsic | Med |
|  | by British computer scientist Tim Berners-Lee working at CERN in Switzerland | Y | Grech V. Publishing on the WWW. Part 5 \- A brief history of the Internet and the World Wide Web. Images Paediatr Cardiol. 2001 Jul;3(3):15-22. PMID: 22368602; PMCID: PMC3232505. |  |  |
|  | Berners-Lee designed the system to allow military and government networks to survive a nuclear attack by routing data through multiple pathways | N (ARPANET) | https://en.wikipedia.org/wiki/ARPANET | Intrinsic | High |
|  | a design goal that explains why the web has no central server. | U | https://en.wikipedia.org/wiki/History\_of\_the\_World\_Wide\_Web | Factual | Med |
|  | By 1995, an estimated 50 million people worldwide were using the web | N (closer to 40 million) | https://www.pingdom.com/blog/internet-1995/ | Intrinsic | Low |

**What type of hallucination was hardest to detect, and why?**

### I found it hardest to detect the factual (extrinsic) errors, where the generative AI just made up an answer that sounded reasonable. The faithfulness (intrinsic) errors were easier to spot. Some of the intrinsic errors may be due to discrepancies between sources of data collection. 

### Task 4: AI Tool Landscape Annotation \[15 min\]

Step-by-step instructions:

1. Open the Module 2 AI Tool Landscape Map from course resources (a visual grid of tools by modality: text, image, code, audio, multimodal).  
2. Select 4 tools from the map that are most relevant to your role — at least one from a modality other than text.  
3. For each selected tool, complete one row in the annotation table below.  
4. For Access Status: check your institution's IT/software portal before marking 'No Access' — many universities have enterprise agreements not widely advertised.  
5. Save or print your annotated map — you will update it in Module 3 after completing Task 1's Workflow Audit.

Tool Annotation Table:

| Tool name | Modality | Access status | Best use case for my role | Key institutional concern |
| ----- | ----- | ----- | ----- | ----- |
| Claude | Text, code | Free and through UofA GenAI | Summarizing, writing, vibe coding | Data for free tier used in training future models |
| NotebookLM | Text, Image, Audio | Free and through U of A | Summarizing, writing, audio summaries | FERPA-compliant |
| DALL-E | Image | Free | Creating and editing images | Copyright status |
| ElevenLabs | Audio | Free | Voice generation | Voice cloning raises consent and identity concerns |

Full landscape map provided by Carlos: 

| Tool | Modality | Developer | Access | Primary use case | Key institutional concern |
| ----- | ----- | ----- | ----- | ----- | ----- |
| ChatGPT | Text | OpenAI | Free / Paid tiers | Drafting, summarizing, brainstorming | Data entered may train future models on free tier |
| Claude | Text | Anthropic | Free / Paid tiers | Writing, analysis, document review | Review data retention policy per tier |
| Microsoft Copilot | Text | Microsoft | Free / Institutional | Email, documents, meetings via M365 | Often institutionally approved via Microsoft agreement |
| Gemini | Text | Google | Free / Paid tiers | Writing, research summaries | Check whether Google Workspace version is institutional |
| Perplexity AI | Text | Perplexity | Free / Paid tiers | Research with cited sources | Citations require independent verification |
| NotebookLM | Text | Google | Free | Summarizing uploaded documents | Only processes documents you upload; lower data risk |
| DALL-E | Image | OpenAI | Paid (via ChatGPT) | Generating illustrations, visual concepts | Copyright status of outputs is unsettled |
| Adobe Firefly | Image | Adobe | Free / Institutional | Image creation and editing | Often covered by institutional Adobe license |
| Midjourney | Image | Midjourney | Paid | High-quality image generation | Outputs are publicly visible on free plan |
| Canva AI | Image | Canva | Free / Paid tiers | Presentations, social media graphics | Check institutional Canva agreement |
| Stable Diffusion | Image | Stability AI | Free / Open source | Local image generation | Can be run locally; lower data exposure risk |
| GitHub Copilot | Code | GitHub/Microsoft | Paid / Institutional | Writing and completing code | May suggest code with licensing issues |
| Google Colab AI | Code | Google | Free | Running and explaining Python code | Good for learning; low data sensitivity |
| Replit AI | Code | Replit | Free / Paid | Writing and running code in browser | Code projects stored on Replit servers |
| Cursor | Code | Anysphere | Paid | Code editing with AI assistance | Codebase uploaded to external server |
| Otter.ai | Audio | Otter | Free / Paid tiers | Meeting transcription | Meeting content — including participant names — stored externally |
| Whisper | Audio | OpenAI | Free / Open source | Audio transcription | Can be run locally; strong privacy option |
| Adobe Podcast | Audio | Adobe | Free | Voice recording cleanup and enhancement | Check institutional Adobe agreement |
| Descript | Audio | Descript | Free / Paid | Podcast and video editing by transcript | Audio and video content stored on Descript servers |
| ElevenLabs | Audio | ElevenLabs | Free / Paid | Voice generation and cloning | Voice cloning raises consent and identity concerns |
| GPT-4o | Multimodal | OpenAI | Paid | Text, image, audio, and file input combined | Highest capability but highest data sensitivity risk |
| Gemini Ultra | Multimodal | Google | Paid | Text, image, and document tasks | Confirm whether institutional Google account governs use |
| Microsoft Copilot (M365) | Multimodal | Microsoft | Institutional | Email, documents, spreadsheets, meetings | Most likely to be institutionally approved and FERPA-aware |
| Runway ML | Multimodal | Runway | Free / Paid | Video and image generation from text | Video outputs raise copyright and consent questions |
| Claude (with files) | Multimodal | Anthropic | Free / Paid | Text plus document and image analysis | Review which plan governs data retention |

