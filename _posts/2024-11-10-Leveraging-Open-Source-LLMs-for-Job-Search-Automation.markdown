---
layout: post
title:  "Leveraging Open Source LLMs for Job Search Automation"
date:   2024-11-18 16:57:26 -0400
categories: LLM, JobSearch
---

# Co-op Job Search: Bye-bye for Now!
It has been a while since I landed my co-op postion at the end of October, and it feels amazing to finally put that exhausting job hunt on pause until April next year.

At first, I tried to lean on the power of LLMs to spped things up. In fact, it wasn't some magical cure-all, but it did save me a good chunk of time here and there.

# Exploring LLMs for Resume Optimization
Before diving in, I did some research on how people use LLMs to optimize their resumes. The approach is pretty straightforward: you provide your existing resume and the target job description as inputs, then use prompts to guide the LLM in tailoring your resume to fit the specific postition.

Here are some interesting tools and findings I came across:
- [ResumeFlow: An LLM-facilitated Pipeline for Personalized Resume Generation and Refinement](https://arxiv.org/html/2402.06221v1)
> The team published a very practical demo paper showcasing how they use LLM to customize resumes based on job description.
- [ResuLLMe](https://github.com/IvanIsCoding/ResuLLMe)
> This GitHub repo provides tools to enhance your resume while avoiding common mistakes.
- [AI/LLM help with resume, cover letter and interview prep](https://www.reddit.com/r/recruitinghell/comments/1cy7jpm/aillm_help_with_resume_cover_letter_and_interview/)
> A reddit user said he created an AI chrome plugin to accelerate the job hunding. I think a resume tool built into chrome plugin offers best user experience. 
- [gpt-researcher](https://github.com/denisefan28/gpt-researcher)
> This tool uses multiple agents to perform research tasks, demonstrating a new agent design pattern. I believe tasks like resume tailoring could benefit from adapting this methodology as well.

# Basic Idea
It's not a groundbreaking idea any more, but I still wanted to try it out myself, for two reasons: 
1. To dive deeper into using LLMs, exploring prompt engineering, and experiment with Retrieval Augmented Generation (RAG).
2. I'm not entirely comfortable using web-based LLMs due to data privacy concerns.

So I used Llama 3.2 ran it locally on my MacBook. I set up agentes to analyze job descriptions, summarize my past work experience, and tailor my resume accordingly. Since I use LaTex to generate ,my resume, it felt natural to incorporate this into the process.

With the help of LLMs, I decided to generate a LaTex file and applied temlates I found on Overleaf to create the final version.

## Json or Txt?
Considering compatibility with existing systems and workflows, having LLMs generate data in json format appears to be a pragmatic solution. Notably, **Llama.cpp** suppports assigning a defined grammar to ensure the LLMs outputs data in json format.



# References
* [llama.cpp python grammar](https://til.simonwillison.net/llms/llama-cpp-python-grammars)
* [llama.cpp grammar json file](https://github.com/ggerganov/llama.cpp/blob/master/grammars/json.gbnf)
* [llama.cpp tool for grammar](https://github.com/ggerganov/llama.cpp/blob/master/examples/json_schema_to_grammar.py)