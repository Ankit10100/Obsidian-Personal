
# 🎯 LLM & GenAI Learning Plan

> **Owner:** Ankit Agrawal
> **Created:** June 2026
> **Goal:** Build deep understanding of LLM internals + ship a private engineering knowledge base on local hardware (NVIDIA T500, 4GB VRAM)
> **Duration:** ~12 weeks @ ~7h/week (~85 hours total)
> **Philosophy:** Quality-first. No platform loyalty. Best resource per topic.

---

## 📋 Table of Contents

- [[#🎯 LLM & GenAI Learning Plan|Overview]]
- [[#📊 The Curated Stack|The Curated Stack]]
- [[#🗓️ Week-by-Week Plan|Week-by-Week Plan]]
- [[#🧰 Capstone Projects|Capstone Projects]]
- [[#🐦 Stay Current — People & Sources|People & Sources to Follow]]
- [[#🧭 Weekly Consumption Routine|Weekly Consumption Routine]]
- [[#❌ What I'm Skipping & Why|What to Skip]]

---

## 📊 The Curated Stack

Quality-first picks, ranked by topic. Each module picks the single highest-quality resource regardless of platform.

| # | Module | Best resource | Source | Hours |
|---|---|---|---|---|
| 1 | **Neural net + transformer internals** | Karpathy — Neural Networks: Zero to Hero (lectures 1, 7, 8) + 2024/25 follow-ups | YouTube (free) | ~15h |
| 2 | **Transformers, tokenizers, fine-tuning (applied)** | Hugging Face LLM Course (12 chapters) | huggingface.co/learn (free) | ~15–20h |
| 3 | **LLM application patterns** | DeepLearning.AI — LangChain for LLM Application Development | DeepLearning.AI (free) | 3h |
| 4 | **Production RAG** | DeepLearning.AI — Retrieval Augmented Generation (Zain Hasan) | DeepLearning.AI (free) | 24h |
| 5 | **Agent orchestration** | LangChain Academy — LangGraph + Deep Agents | academy.langchain.com (free) | 8h |
| 6 | **Reference book (deep dive)** | *Hands-On Large Language Models* — Alammar & Grootendorst | O'Reilly via Microsoft Library | reference |
| 7 | **Reference book (from scratch)** | *Build a Large Language Model From Scratch* — Sebastian Raschka | O'Reilly via Microsoft Library | reference |
| 8 | **Azure-side production** | Microsoft Learn — Generative AI for Beginners + Azure AI Foundry | learn.microsoft.com (free) | 10h |
| 9 | **Local LLM ops (Ollama, quantization)** | Sebastian Raschka blog + Ollama docs + Simon Willison's blog | Free | 6h |

---

## 🗓️ Week-by-Week Plan

### Phase 1 — Build the Mental Model (Weeks 1–4)

**Goal:** Stop treating LLMs as black boxes. Understand weights, training, attention.

#### Week 1 — Backprop & neural net fundamentals
- [ ] Watch **Karpathy Lecture 1: micrograd** (~2h25m) — backprop from scratch
- [ ] Re-implement micrograd in your own repo
- [ ] Read **Jay Alammar — "The Illustrated Transformer"** blog post
- [ ] **Deliverable:** Markdown note in vault explaining backprop in your own words

#### Week 2 — Build a transformer
- [ ] Watch **Karpathy Lecture 7: Let's build GPT** (~2h)
- [ ] Type along — actually train a nanoGPT-style model on your Obsidian notes
- [ ] Read Chapter 3 of *Hands-On LLMs* (Alammar) — "Looking inside Transformer LLMs"
- [ ] **Deliverable:** A toy GPT model trained on your own data, saved to repo

#### Week 3 — Tokenization & modern training
- [ ] Watch **Karpathy Lecture 8: GPT Tokenizer** (~2h15m)
- [ ] Watch **Karpathy 2024: "Let's reproduce GPT-2 (124M)"** (~4h) — modern training stack
- [ ] Read Chapter 2 of *Hands-On LLMs* — "Tokens and Embeddings"
- [ ] **Deliverable:** Build your own BPE tokenizer; benchmark vs `tiktoken`

#### Week 4 — Modern post-training landscape
- [ ] Watch **Karpathy 2025: "Deep Dive into LLMs like ChatGPT"** (~3h35m)
- [ ] Read **Lilian Weng — "RLHF" blog post** (lilianweng.github.io)
- [ ] Hugging Face LLM Course chapters 1–4
- [ ] **Deliverable:** Diagram (Mermaid) in vault: pretraining → SFT → RLHF/DPO → RLAIF pipeline

---

### Phase 2 — Production RAG = Your Engineering KB (Weeks 5–8)

**Goal:** Build a private, queryable knowledge base over Obsidian + code repos.

#### Week 5 — RAG fundamentals
- [ ] DeepLearning.AI RAG Course — Modules 1–3 (retrieval basics, embeddings, vector DBs)
- [ ] Hugging Face LLM Course chapters 5–6 (Datasets, Tokenizers in depth)
- [ ] **Deliverable:** Hello-world RAG against your Obsidian vault with ChromaDB + nomic-embed-text + Ollama

#### Week 6 — Advanced retrieval
- [ ] DeepLearning.AI RAG Course — Modules 4–6 (chunking, hybrid retrieval, query parsing)
- [ ] Read Chapter 8 of *Hands-On LLMs* — "Semantic Search and RAG"
- [ ] **Deliverable:** Add BM25 + vector hybrid retrieval; document chunking strategy in vault

#### Week 7 — Evaluation & prompt design
- [ ] DeepLearning.AI RAG Course — Modules 7–9 (prompt design, evaluation, deployment)
- [ ] Set up Phoenix/Arize for RAG evaluation
- [ ] Build a 50-question golden set from real engineering queries you'd ask
- [ ] **Deliverable:** Evaluation report with precision/recall on your golden set

#### Week 8 — Productionize the KB
- [ ] Add incremental indexing (only re-embed changed Markdown files)
- [ ] Wrap as Streamlit UI + expose as Copilot CLI tool
- [ ] Microsoft Learn — Azure AI Search RAG patterns (1 module, for day-job overlap)
- [ ] **Deliverable:** Production-grade KB you actually use daily

---

### Phase 3 — Multi-Agent Orchestration (Weeks 9–10)

**Goal:** Build master-orchestrator → per-repo specialist agents.

#### Week 9 — LangGraph fundamentals
- [ ] DeepLearning.AI — LangChain for LLM Application Development (~3h)
- [ ] LangChain Academy — Introduction to LangGraph (~6h)
- [ ] **Deliverable:** Single-repo agent with state machine, checkpointing, human-in-loop

#### Week 10 — Deep Agents & orchestration
- [ ] LangChain Academy — Project: Deep Agents
- [ ] DeepLearning.AI — Functions, Tools and Agents with LangChain (~3h)
- [ ] Read Chapter 7 of *Hands-On LLMs* — "Advanced Text Generation Techniques and Tools"
- [ ] **Deliverable:** Master agent routing to per-repo sub-agents, each with its own RAG index. Architecture diagram (Mermaid) in vault.

---

### Phase 4 — Fine-tuning + Capstone (Weeks 11–12)

**Goal:** LoRA-fine-tune a small model on your hardware; ship the side project.

#### Week 11 — Fine-tuning theory & practice
- [ ] Hugging Face LLM Course chapters 10–12 (advanced fine-tuning)
- [ ] Read Chapters 11–12 of *Hands-On LLMs* — fine-tuning generation models
- [ ] Read Raschka's blog series on LoRA + QLoRA
- [ ] **Deliverable:** QLoRA-fine-tune Phi-3-mini on a small dataset from your engineering docs

#### Week 12 — Capstone
Pick one (or split):
- [ ] **Engineering KB v2:** production-grade, source-attributed answers, integrated as Copilot CLI tool
- [ ] **Face-extraction video pipeline:** YOLO + face_recognition + ChromaDB (this is NOT an LLM problem — use the right tool)

---

## 🧰 Capstone Projects

### Project 1: Private Engineering Knowledge Base

**Architecture:**
```
Obsidian vault + Git repos
        ↓
Unstructured.io chunker (semantic-aware)
        ↓
nomic-embed-text via Ollama (local embeddings)
        ↓
ChromaDB (hybrid BM25 + vector)
        ↓
Qwen 2.5 7B Q4 via Ollama (fits in 4GB)
        ↓
LangGraph orchestrator (per-repo sub-agents)
        ↓
Streamlit UI + Copilot CLI tool integration
```

**Key decisions to document:**
- Why local vs cloud (privacy, latency, cost)
- Why ChromaDB vs Weaviate vs Qdrant
- Chunking strategy (markdown headers vs semantic)
- Eval framework (golden set + Phoenix)

### Project 2: Multi-Repo Agent Mesh
- Master orchestrator agent (LangGraph state machine)
- One specialist sub-agent per repo with dedicated RAG index
- Tool: `git_history`, `code_search`, `doc_search`, `run_tests`
- Human-in-loop checkpoints for destructive operations

---

## 🐦 Stay Current — People & Sources

### X / Twitter — Tier 1 (must-follow, ~10 accounts)

#### Researchers / model builders
| Handle | Why |
|---|---|
| **@karpathy** | Now at Anthropic pretraining. Highest-signal AI account, period. |
| **@sama** | OpenAI CEO. Signals product/model timing. |
| **@DarioAmodei** + **@AnthropicAI** | Claude updates, interpretability research |
| **@ylecun** | Counterweight to LLM-maximalist view |
| **@JeffDean** | Gemini + TPU/infra direct from Google |
| **@drjimfan** | NVIDIA — robotics + foundation models, great threads |
| **@_jasonwei** | Chain-of-thought paper author; reasoning models depth |

#### Practitioner-educators
| Handle | Why |
|---|---|
| **@rasbt** (Sebastian Raschka) | *Ahead of AI* newsletter — best practitioner summary weekly |
| **@JayAlammar** | Best visual explanations of LLM internals |
| **@simonw** (Simon Willison) | Daily "what actually works" with local LLMs — directly relevant to your Ollama setup |

#### Ecosystem / tooling
| Handle | Why |
|---|---|
| **@HarrisonChase** | LangChain/LangGraph updates first-hand |
| **@huggingface** + **@ClementDelangue** | OSS model releases same-day |
| **@ollama** | Local-runnable model releases |

### X — Tier 2 (follow as bandwidth allows)
- **@swyx** — *Latent Space* podcast/newsletter
- **@hwchase17** — LangChain co-founder
- **@sophiamyang** — Mistral
- **@arankomatsuzaki** — fastest arXiv summary account
- **@_philschmid** — fine-tuning, deployment, hands-on
- **@maximelabonne** — LLM fine-tuning + quantization
- **@reach_vb** — local LLM, MLX, Ollama ecosystem
- **@levelsio** — solo builder using AI in production

### Newsletters (the 5 worth your inbox)
| Newsletter | By | Frequency |
|---|---|---|
| **Ahead of AI** | Sebastian Raschka | Weekly — best AI newsletter for engineers |
| **The Batch** | Andrew Ng / DeepLearning.AI | Weekly, <10 min read |
| **Import AI** | Jack Clark (Anthropic co-founder) | Weekly, policy + frontier models |
| **Latent Space** | swyx + Alessio | Weekly + podcast — AI engineering perspective |
| **TLDR AI** | TLDR | Daily 5-min skim |

**Honorable mentions:** *Last Week in AI*, *Interconnects* (Nathan Lambert — RLHF depth)

### Podcasts
| Podcast | Why |
|---|---|
| **Dwarkesh Patel Podcast** | 2–4h interviews with frontier researchers. Highest signal. |
| **Latent Space** | Engineer-focused; RAG, agents, eval episodes directly applicable |
| **The Cognitive Revolution** | Nathan Labenz; balanced safety + capabilities + applications |

### Blogs to bookmark
- **karpathy.ai** — when he writes long-form, drop everything
- **sebastianraschka.com** — technical companion to *Ahead of AI*
- **simonwillison.net** — daily local LLM practice
- **jalammar.github.io** — Illustrated Transformer/GPT-2
- **lilianweng.github.io** — long-form surveys on agents, hallucination, RL
- **interconnects.ai** — Nathan Lambert; RLHF, post-training, open models

### Aggregators
- **r/LocalLLaMA** — best community for your T500/Ollama use case
- **Hacker News** — front page AI threads
- **huggingface.co/papers** — community-upvoted arXiv with discussion
- **Papers With Code** — research + implementation

### YouTube (beyond Karpathy)
- **Yannic Kilcher** — paper explanations, sharp takes
- **AI Coffee Break with Letitia** — 10–15 min explainers
- **Two Minute Papers** — vision/multimodal quick coverage

---

## 🧭 Weekly Consumption Routine

A sustainable rhythm — don't try to follow everything.

```
Daily   (5 min):  TLDR AI email skim
Daily   (10 min): X "AI Tier 1" list only (NOT home timeline)
Weekly  (45 min): Ahead of AI + The Batch + Import AI
Weekly  (60 min): One Dwarkesh OR Latent Space episode (commute)
Monthly (2 hrs):  One deep Raschka or Lilian Weng essay — actually study it
```

**Pro tip:** Create an X **List** called `AI-Tier1` with the 10 Tier 1 accounts. Check ONLY that list, not your home timeline. Single highest-impact change.

---

## ❌ What I'm Skipping & Why

| Skipped | Reason |
|---|---|
| Udemy "Complete GenAI Bootcamp" courses | Variable quality; DL.AI + HF combo is free and better |
| Packt videos (Harnessing Ollama etc.) | Quality below DL.AI/HF for the same topics |
| Generic Pluralsight LLM tracks | ~12 months behind frontier; lags DL.AI/HF |
| Karpathy lectures #2–#6 | The makemore series is great but #1, #7, #8 capture 80% of value |
| Coursera Generative AI Specialization | Good but redundant with HF Course + DL.AI free shorts |
| AI influencer X accounts ("@AIGuru_Daily") | Recycled content, no original signal |
| Generic VC AI commentary | Incentivized to hype |

---

## 📌 Quick Reference — Pre-Reqs Checklist

Before starting Phase 1, confirm you have:
- [x] Python 3.10+ environment
- [x] PyTorch installed (`pip install torch`)
- [x] Ollama installed and running
- [x] T500 GPU detected by CUDA (`nvidia-smi`)
- [x] At least 1 model pulled in Ollama (`ollama pull qwen2.5:7b-instruct-q4_K_M`)
- [x] Obsidian vault with some real notes (for RAG target)
- [x] Git repos cloned (for multi-agent target)
- [x] VS Code with Python + Jupyter extensions
- [x] Hugging Face account (for HF Course + model downloads)

---

## 🎯 Success Metrics (Self-Check at Week 12)

By the end of this plan, you should be able to:
- [ ] Explain attention, KV-cache, and quantization to a junior engineer without slides
- [ ] Train a tiny transformer from scratch in PyTorch without copy-paste
- [ ] Build a production-grade RAG system with evaluation
- [ ] Design and ship a multi-agent system with LangGraph
- [ ] Run a LoRA fine-tune end-to-end on consumer hardware
- [ ] Evaluate a vendor's model claims critically (cost/latency/accuracy tradeoffs)
- [ ] Make architecture decisions on when NOT to use an LLM (the face-extraction project)

---

## 📝 Notes & Reflection Log

> Use this section to track learnings, blockers, and "aha" moments per week.

### Week 1
- Started: _____
- Key insight:
- Blockers:

### Week 2
- ...

---

**Last updated:** 2026-06-23
**Next review:** End of Phase 1 (Week 4)
