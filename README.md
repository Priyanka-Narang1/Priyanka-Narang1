<div align="center">

<!-- Animated header -->
<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0F0524,50:2D1B4E,100:5B2A9E&height=220&section=header&text=Priyanka%20Narang&fontSize=52&fontColor=E9D8FD&animation=fadeIn&fontAlignY=38&desc=AI%20%2B%20Software%20Engineer&descAlignY=58&descSize=18" width="100%"/>

<!-- Typing SVG -->
<a href="#">
  <img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=500&size=22&duration=3200&pause=900&color=B794F4&center=true&vCenter=true&width=680&lines=Building+production-grade+AI+systems;Designing+scalable+backend+services;RAG+pipelines+%2B+LLM+evaluation+%2B+CI+gating;Software+Engineering+%C3%97+AI+Engineering" alt="Typing SVG" />
</a>

<br/>

<!-- Academic & engineering badges -->
<img src="https://img.shields.io/badge/B.Tech-AI%20%26%20ML-5B2A9E?style=for-the-badge&labelColor=0F0524" />
<img src="https://img.shields.io/badge/GGSIPU-HMRITM-5B2A9E?style=for-the-badge&labelColor=0F0524" />
<img src="https://img.shields.io/badge/Published-Springer%20LNCS-5B2A9E?style=for-the-badge&labelColor=0F0524" />
<img src="https://img.shields.io/badge/Focus-LLM%20Infrastructure-5B2A9E?style=for-the-badge&labelColor=0F0524" />

<br/><br/>

<!-- Social buttons -->
<a href="https://github.com/Priyanka-Narang1"><img src="https://img.shields.io/badge/GitHub-Priyanka--Narang1-5B2A9E?style=flat-square&logo=github&logoColor=E9D8FD&labelColor=0F0524" /></a>
<a href="https://leetcode.com/u/CodingPRos/"><img src="https://img.shields.io/badge/LeetCode-CodingPRos-5B2A9E?style=flat-square&logo=leetcode&logoColor=E9D8FD&labelColor=0F0524" /></a>

</div>

<br/>

## About

I build production-grade AI systems and the backend infrastructure that keeps them reliable — retrieval pipelines, evaluation harnesses, and services designed to be observed, tested, and shipped, not just prototyped in a notebook.

My interest sits at the intersection of:

- Software Engineering & System Design
- Backend & Distributed Systems
- AI / LLM Infrastructure
- Applied Machine Learning & NLP

I'm more interested in the engineering around a model — retrieval quality, latency, cost, regression gating, evaluation — than in training the model itself.

**Currently:** building out an observability and evaluation layer on top of a production RAG system, and deepening data structures & algorithms fundamentals through the Striver A2Z sheet.

<br/>

## Tech Stack

<div align="center">

**Languages**
<img src="https://skillicons.dev/icons?i=py,cpp,js,mysql&theme=dark" />

**AI / ML**
<img src="https://skillicons.dev/icons?i=sklearn,pytorch&theme=dark" />

**Backend**
<img src="https://skillicons.dev/icons?i=fastapi,py&theme=dark" />

**Frontend**
<img src="https://skillicons.dev/icons?i=react,nextjs,tailwind&theme=dark" />

**Infra & Cloud**
<img src="https://skillicons.dev/icons?i=docker,git,githubactions,aws&theme=dark" />

</div>

| Category | Tools |
|---|---|
| Languages | Python, C++, JavaScript, SQL |
| Core ML / NLP | XGBoost, scikit-learn, SBERT, spaCy, SHAP, TF-IDF |
| RAG / LLM | LangChain, ChromaDB, hybrid (dense + BM25) retrieval, cross-encoder reranking, Groq-served LLMs, LLM-as-judge evaluation |
| Backend | FastAPI, Docker, REST APIs |
| Frontend | React, Next.js, Framer Motion, Tailwind CSS |
| Cloud & Deployment | AWS, Hugging Face Spaces, Render, Vercel, Netlify |
| CI/CD | GitHub Actions (eval-gated regression checks) |

<br/>

## Featured Projects

<details>
<summary><b>RAG Research Studio</b> — production RAG system with CI-gated evaluation</summary>
<br/>

**Overview**
A retrieval-augmented question-answering system over a corpus of RAG research papers, built to behave like a real service rather than a demo: versioned prompts, an eval suite, and CI that blocks regressions.

**Stack**
FastAPI + Docker (backend) · Next.js + Framer Motion (frontend) · ChromaDB + BM25 hybrid retrieval · cross-encoder reranking · Groq API (Llama 3.1 8B Instant)

**Architecture**
Hybrid dense + sparse retrieval feeds a reranking stage before generation. Prompts enforce strict grounding and citation, with abstention on peripheral matches. Backend and frontend are deployed separately and communicate over a versioned API.

**Evaluation**
60-question golden dataset scored with an LLM-as-judge across faithfulness, context precision, and answer relevancy. Current baselines: faithfulness 0.91, context precision 0.76.

**Key Engineering Decisions**
- GitHub Actions CI gates merges on faithfulness (≥0.86) and context precision (≥0.71) — regressions fail the build, not just the demo
- Prompt versions are tracked and rolled forward deliberately (current: v2.2 — stricter grounding, mandatory citation gate)
- LLM provider chosen pragmatically around real constraints (regional API/billing limits), not by default preference

**Challenges**
Retrieval occasionally favors a broad survey chunk over the more specific target paper on close-topic queries — an open tuning problem, not hidden.

**Impact**
Backend and frontend both live in production; now extending into a dedicated observability layer (tracing, latency/cost/citation-coverage metrics, automated regression gating) on top of the existing pipeline.

**Repository:** [github.com/Priyanka-Narang1/Rag-on-Rag-Papers](https://github.com/Priyanka-Narang1/Rag-on-Rag-Papers)
**Live:** [rag-research-studio.netlify.app](https://rag-research-studio.netlify.app)

</details>

<details>
<summary><b>Hybrid Fake Job Detection System</b> — NLP + gradient boosting classifier</summary>
<br/>

**Overview**
A hybrid text-classification system to flag fraudulent job postings, combining classical NLP features with a gradient-boosted classifier.

**Stack**
XGBoost · TF-IDF · scikit-learn

**Scale**
Trained and evaluated on roughly 17,880 job posting records.

**Performance**
F1 score of 0.858 on the evaluation set.

**Impact**
Submitted to a peer-reviewed journal.

</details>

<br/>

## Research

**Springer LNCS Publication** — ICAMC-2026 (Paper ID 882), corresponding author.
The paper is built on a semantic resume analysis system: a 7-stage hybrid NLP pipeline (spaCy NER, SBERT embeddings, XGBoost, SHAP for explainability, TF-IDF, a logistic-regression section scorer, and a deterministic feedback layer), deployed full-stack — FastAPI on Render, React on Vercel.

Awarded **Best Presenter** at the same venue as a 2nd-year undergraduate.

<br/>

## Certifications

- Career Essentials in Generative AI — Microsoft & LinkedIn Learning (2026)
- AI Fundamentals — IBM SkillsBuild

<br/>

## Coding Profiles

<div align="center">
<a href="https://leetcode.com/u/CodingPRos/"><img src="https://img.shields.io/badge/LeetCode-Profile-5B2A9E?style=for-the-badge&logo=leetcode&logoColor=E9D8FD&labelColor=0F0524" /></a>
</div>

<br/>

## GitHub Analytics

<div align="center">

<img src="https://github-readme-stats.vercel.app/api?username=Priyanka-Narang1&show_icons=true&theme=dark&hide_border=true&bg_color=0F0524&title_color=B794F4&icon_color=B794F4&text_color=E9D8FD" width="49%" />
<img src="https://github-readme-stats.vercel.app/api/top-langs/?username=Priyanka-Narang1&layout=compact&theme=dark&hide_border=true&bg_color=0F0524&title_color=B794F4&text_color=E9D8FD" width="49%" />

<img src="https://streak-stats.demolab.com/?user=Priyanka-Narang1&theme=dark&hide_border=true&background=0F0524&ring=B794F4&fire=B794F4&currStreakLabel=E9D8FD" width="70%" />

<img src="https://github-profile-trophy.vercel.app/?username=Priyanka-Narang1&theme=algolia&no-frame=true&column=7&margin-w=10&margin-h=10" width="90%" />

<img src="https://github-readme-activity-graph.vercel.app/graph?username=Priyanka-Narang1&theme=react-dark&hide_border=true&bg_color=0F0524&color=B794F4&line=B794F4&point=E9D8FD" width="90%" />

</div>

<br/>

<!-- Contribution snake -- requires a repo action to generate github-contribution-grid-snake.svg -->
<div align="center">
<img src="https://raw.githubusercontent.com/Priyanka-Narang1/Priyanka-Narang1/output/github-contribution-grid-snake.svg" width="90%" />
</div>

<br/>

## Current Focus

```yaml
learning:
  - Distributed systems fundamentals
  - LLM serving & inference optimization
  - System design

building:
  - RAG evaluation & observability tooling
  - Production-ready backend services

exploring:
  - Agentic and multi-agent architectures
  - AI infrastructure

open_to:
  - AI Engineering internships
  - Software Engineering internships
  - Backend engineering roles
```

<br/>

## Contact

<div align="center">
<a href="https://github.com/Priyanka-Narang1"><img src="https://img.shields.io/badge/GitHub-Priyanka--Narang1-5B2A9E?style=for-the-badge&logo=github&logoColor=E9D8FD&labelColor=0F0524" /></a>
</div>

<br/>

<img src="https://capsule-render.vercel.app/api?type=waving&color=0:5B2A9E,100:0F0524&height=100&section=footer" width="100%"/>

</div>

