# ai-syllabus
An full, self-directed curriculum for becoming a competitive AI research engineer candidate. 53 weeks of homework, every resource linked, no fluff.

## Why This Exists

Most "how to get into AI" guides are too shallow (take a MOOC and apply!) or too academic (get a PhD). The syllabus below is for people who want to do the work without going back to school and come out the other side with a portfolio that labs take seriously, not a collection of course certificates.

Every week produces an artifact: code pushed to a repo, a trained model, a paper summary, or a technical write-up. By month 13, you'll have a public body of work showing you can read papers, implement ideas, run experiments, and communicate results. That's what research engineers do every day.

## Who This Is For

**You're a good fit if you have:**
- A quantitative undergraduate degree (math, physics, statistics, CS, engineering, economics) or equivalent self-taught foundations
- Professional programming experience in any language (you don't need Python yet, but you need to know how to code)
- The ability to commit ~20 hours per week for 13 months
- Genuine curiosity about how AI systems work at a deep level

**Skip Phase 1 if you:**
- Already have strong linear algebra, calculus, probability, and optimization fundamentals
- Are comfortable writing Python and using NumPy/pandas/matplotlib
- Have trained neural networks in PyTorch before
- Can read an ML paper and follow the math

If that describes you, start at Phase 2 (month 4). Be honest, though. "I took a linear algebra class 8 years ago" is not the same as "I can derive gradient descent from first principles right now."

**Skip Phase 2 if you:**
- Already have hands-on implementation experience in at least one of: RL, language model training, or diffusion models
- Have a clear sense of which area you want to specialize in and why

**Not the right fit for:**
- Complete beginners with no programming experience (start with a CS fundamentals course first)
- People looking for a quick credential (this is 1,000+ hours of work)
- Those who want to become ML engineers focused on deployment/production systems (related but different path)

## How to Use This Syllabus

**Structure:** 5 phases, 13 months, 53 numbered weeks. Each week has a concrete assignment that builds on the previous one.

**Time commitment:** ~20 hours per week. Most people split this as 2–3 hours on weekdays and a longer block on weekends. Adjust to your life, but protect the hours. Consistency matters more than intensity.

**The `ml-foundations` repo:** In week 1, you'll create a GitHub repo called `ml-foundations`. The repo becomes the running record of everything you build. By month 13, it's a substantial body of work and the backbone of your portfolio.

**Budget:** Most of the curriculum uses free resources. You'll need GPU compute starting around month 5 (~$50–200/month on Vast.ai, Lambda, or RunPod depending on your projects). Weights & Biases is free for personal use.

**Going faster or slower:** The weekly cadence is a guide, not a prison. Some weeks you'll finish early. Others will take 10 days. What matters is completing each assignment before moving to the next. Don't skip the writing. It's tempting, but it's half the value.

---

## Phase 1: Foundations (Months 1–3)

**Goal:** Build (or rebuild) math fundamentals to research-grade and become fluent in the Python ML stack.

### Prerequisite: The AI Stack (Week 1)

Before touching math or code, build a mental model of the full AI infrastructure stack from raw materials to applications. Understanding how each layer enables and constrains the next is critical context for following real-time discourse around export controls, compute scaling, and why certain architectural decisions matter. Spend 3–5 days reading broadly here before moving on.

**The Stack:**

**1. Raw Materials:** Rare earths, copper, silicon, uranium
> The entire AI supply chain begins with physical materials. Gallium, germanium, neon, and ultra-pure silicon are essential and geographically concentrated.

| Resource | Type | Link |
|----------|------|------|
| IEA – "The Role of Critical Minerals in Clean Energy Transitions" | Report | [iea.org/reports](https://www.iea.org/reports/the-role-of-critical-minerals-in-clean-energy-transitions) |
| IEA – "Export Controls on Critical Minerals"                                       | Commentary | [iea.org/commentaries](https://www.iea.org/commentaries/with-new-export-controls-on-critical-minerals-supply-concentration-risks-become-reality)        |
| FP Analytics – "AI and the Critical Minerals Crunch"                               | Report     | [fpanalytics.foreignpolicy.com](https://fpanalytics.foreignpolicy.com/2025/07/18/artificial-intelligence-critical-minerals-supply-chains/) |
| Craig Tindale – "Critical Materials: A Strategic Analysis"                         | Thread     | [x.com](https://x.com/ctindale/status/1997471488514134481/?s=12&rw_tt_thread=True)                                                         |
| @howdymerry – "The New Space Race Is Seizing the Means of Intelligence Production" | Thread     | [x.com](https://x.com/howdymerry/status/2014818226572792082/?s=12&rw_tt_thread=True)                                                       |

**2. Semiconductor Equipment:** Lithography, deposition, etching
> ASML maintains a 100% monopoly on extreme ultraviolet (EUV) lithography machines, the only equipment capable of printing sub-7nm features required for advanced AI chips. Each machine costs $150–200M and takes 18 months to build. Under US pressure, the Netherlands restricted EUV exports to China, the most consequential export control in modern history. Without EUV, China cannot manufacture chips below ~7nm.

| Resource | Type | Link |
|----------|------|------|
| Chip War (Chris Miller) | Book | [amazon.com](https://www.amazon.com/Chip-War-Worlds-Critical-Technology/dp/1982172002) |
| Asianometry – YouTube Channel | Video Series | [youtube.com/@Asianometry](https://www.youtube.com/@Asianometry) |
| ASML Annual Report | Primary Source | [asml.com/en/investors](https://www.asml.com/en/investors) |

**3. Foundries:** Chip manufacturing
> TSMC fabricates an estimated 92% of the world's most advanced chips. That concentration is a significant geopolitical risk given the location and size of Taiwan.

| Resource | Type | Link |
|----------|------|------|
| Ben Thompson – "Chips and Geopolitics" | Analysis | [stratechery.com](https://stratechery.com/2020/chips-and-geopolitics/) |
| SemiAnalysis Newsletter | Industry Analysis | [semianalysis.com](https://www.semianalysis.com/) |

**4. Memory & Storage:** DRAM, NAND, HBM
> High Bandwidth Memory (HBM) is the critical bottleneck for training large models. SK Hynix and Samsung dominate, and HBM supply constraints directly impact GPU availability.

| Resource | Type | Link |
|----------|------|------|
| "The Memory Wall" – HBM Explainer | Analysis | [semianalysis.com](https://newsletter.semianalysis.com/p/the-memory-wall) |

**5. Processors:** GPUs, TPUs, AI accelerators
> NVIDIA holds over 94% share of the discrete GPU market. The moat rests on the CUDA software ecosystem (two decades of developer investment that makes switching costs enormous), not the hardware alone. Custom silicon from hyperscalers (Google TPUs, Amazon Inferentia/Trainium, Microsoft Azure Maia) represents ongoing efforts to reduce NVIDIA dependence.

| Resource | Type | Link |
|----------|------|------|
| NVIDIA CUDA Documentation | Reference | [docs.nvidia.com/cuda](https://docs.nvidia.com/cuda/) |
| Google TPU Research Papers | Papers | [cloud.google.com/tpu/docs/publications](https://cloud.google.com/tpu/docs/publications) |
| "Making Deep Learning Go Brrrr From First Principles" (Horace He) | Analysis | [horace.io](https://horace.io/brrr_intro.html) |

**6. Networking:** Data center interconnects
> InfiniBand (NVIDIA/Mellanox) and high-speed Ethernet fabrics determine how fast GPUs can communicate during distributed training. Networking bandwidth is often the real bottleneck at scale, not raw compute.

| Resource | Type | Link |
|----------|------|------|
| "Networking for Data Centers and the Era of AI" – NVIDIA | Analysis | [nvidia.com](https://developer.nvidia.com/blog/networking-for-data-centers-and-the-era-of-ai/) |

**7. Energy Infrastructure:** Power generation and transmission
> Deloitte projects US data center power capacity will grow from 33 GW in 2024 to 176 GW by 2035, and that may be too small an estimate. Power availability is becoming the binding constraint on AI scaling.

| Resource | Type | Link |
|----------|------|------|
| Deloitte – US Data Center Power Projections | Report | [deloitte.com](https://www.deloitte.com/us/en/insights/industry/power-and-utilities/nuclear-energy-powering-data-centers.html) |
| "Energy and AI" – IEA | Report | [iea.org/energy-system/buildings/data-centres-and-data-transmission-networks](https://www.iea.org/energy-system/buildings/data-centres-and-data-transmission-networks) |
| IAEA – "Data Centres Eye Advanced Nuclear"                        | Report | [iaea.org](https://www.iaea.org/bulletin/data-centres-artificial-intelligence-and-cryptocurrencies-eye-advanced-nuclear-to-meet-growing-power-needs)                   |
| Leopold Aschenbrenner – "Racing to the Trillion-Dollar Cluster"   | Essay  | [situational-awareness.ai](https://situational-awareness.ai/racing-to-the-trillion-dollar-cluster/)                                                                    |

**8. Data Centers:** Cloud compute facilities
> The three hyperscalers (AWS, Azure, GCP) dominate, but specialized AI cloud providers (CoreWeave, Lambda, Crusoe) are growing fast. Space-based data centers may be inevitable. If the US leads in establishing these, it could provide significant advantage in the AI competition.

| Resource | Type | Link |
|----------|------|------|
| CoreWeave | AI Cloud Provider | [coreweave.com](https://www.coreweave.com/) |
| Lambda | AI Cloud Provider | [lambdalabs.com](https://lambdalabs.com/) |

**9. Software & Models:** AI frameworks, foundation models, applications, agents
> You'll spend 95% of your time in this layer. PyTorch dominates research. JAX is preferred at Google DeepMind. The frontier model labs (Anthropic, OpenAI, Google, Meta) are the primary employers for research engineers.

| Resource | Type | Link |
|----------|------|------|
| Epoch AI – "Trends in Machine Learning" | Data & Analysis | [epochai.org](https://epochai.org/) |
| State of AI Report (Annual) | Full Report | [stateof.ai](https://www.stateof.ai/) |
| Situational Awareness (Leopold Aschenbrenner) | Essay Series | [situational-awareness.ai](https://situational-awareness.ai/) |
| Nathan Benaich & Ian Hogarth – State of AI | Annual Report | [stateof.ai](https://www.stateof.ai/) |

**Why this matters for research engineers:** Understanding the stack helps you reason about why certain architectural decisions happen (memory bandwidth → attention mechanisms), why certain companies have structural advantages, and what physical constraints shape the research frontier.

### Month 1: Math Refresh + Python for ML

| Resource | Type | Link |
|----------|------|------|
| 3Blue1Brown – Essence of Linear Algebra | Video Series | [youtube.com/playlist](https://www.youtube.com/playlist?list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab) |
| 3Blue1Brown – Essence of Calculus | Video Series | [youtube.com/playlist](https://www.youtube.com/playlist?list=PLZHQObOWTQDMsr9K-rj53DwVRMYO3t5Yr) |
| Boyd & Vandenberghe – Convex Optimization | Textbook (free) | [stanford.edu/~boyd/cvxbook](https://web.stanford.edu/~boyd/cvxbook/) |
| NumPy Documentation | Reference | [numpy.org/doc](https://numpy.org/doc/stable/) |
| Matplotlib Tutorials | Reference | [matplotlib.org/stable/tutorials](https://matplotlib.org/stable/tutorials/index.html) |
| Pandas Getting Started | Reference | [pandas.pydata.org/docs](https://pandas.pydata.org/docs/getting_started/index.html) |

**Deliverable:** Implement gradient descent from scratch in NumPy. Be comfortable reading Python ML codebases.

**Weekly Homework:**

| Week | Assignment |
|------|-----------|
| 1 | Complete 3Blue1Brown linear algebra series. Write 3 small data processing scripts in Python using NumPy and pandas (e.g., load a CSV, compute summary statistics, reshape and filter arrays). If you're coming from another language, focus on getting comfortable with NumPy's broadcasting and vectorized operations. Push to a new GitHub repo called `ml-foundations`. |
| 2 | Complete 3Blue1Brown calculus series. Implement matrix multiplication, eigenvalue decomposition, and SVD from scratch in NumPy (no `np.linalg` shortcuts). Write unit tests to verify against NumPy's built-in functions. |
| 3 | Read Boyd & Vandenberghe chapters 1–5 (convex sets, functions, optimization problems). Implement gradient descent for linear regression from scratch, computing the loss, gradient, and update step manually. Visualize the loss curve with matplotlib. |
| 4 | Implement logistic regression from scratch using only NumPy (no sklearn). Train it on a real dataset (e.g., sklearn's breast cancer dataset, loaded via pandas). Write a 500-word blog post explaining the math behind your implementation. Push everything to `ml-foundations`. |

### Month 2: Core ML Theory + PyTorch

| Resource | Type | Link |
|----------|------|------|
| Andrej Karpathy – Neural Networks: Zero to Hero | Video Series | [youtube.com/playlist](https://www.youtube.com/playlist?list=PLAqhIrjkxbuWI23v9cThsA9GvCAUhRvKZ) |
| Stanford CS229 – Machine Learning (Andrew Ng) | Lecture Videos | [youtube.com/playlist](https://www.youtube.com/playlist?list=PLoROMvodv4rMiGQp3WXShtMGgzqpfVfbU) |
| CS229 Course Materials | Notes & Problem Sets | [cs229.stanford.edu](https://cs229.stanford.edu/) |
| PyTorch Tutorials | Official Docs | [pytorch.org/tutorials](https://pytorch.org/tutorials/) |

**Deliverable:** Train a small neural network from scratch. Explain backpropagation mechanically.

**Weekly Homework:**

| Week | Assignment |
|------|-----------|
| 5 | Complete Karpathy's "micrograd" video. Build your own autograd engine from scratch, implementing `Value` class with `+`, `*`, `tanh`, `exp`, and `backward()`. Train a tiny MLP on a toy dataset using your engine. |
| 6 | Complete Karpathy's "makemore" parts 1–2 (bigram model + MLP). Watch CS229 lectures 1–4 (linear regression, gradient descent, logistic regression, generalized linear models). Implement a character-level bigram model from scratch in PyTorch. |
| 7 | Complete Karpathy's "makemore" parts 3–4 (BatchNorm, backprop ninja). Watch CS229 lectures 5–8 (GDA, naive Bayes, SVMs, neural networks). Implement a 3-layer MLP in raw PyTorch (no `nn.Module`), manually computing forward pass, loss, and gradients. |
| 8 | Refactor your MLP to use `nn.Module`, `nn.Linear`, and `optim.Adam`. Train it on CIFAR-10 and log training curves. Write a 1-page explanation of backpropagation as if explaining it to a smart colleague who doesn't know ML. Push to `ml-foundations`. |

### Month 3: Deep Learning Fundamentals

| Resource | Type | Link |
|----------|------|------|
| Karpathy – Let's build GPT from scratch | Video | [youtube.com/watch](https://www.youtube.com/watch?v=kCc8FmEb1nY) |
| Stanford CS231n – Convolutional Neural Networks | Lecture Videos | [youtube.com/playlist](https://www.youtube.com/playlist?list=PL3FW7Lu3i5JvHM8ljYj-zLfQRF3EO8sYv) |
| CS231n Course Materials | Notes & Assignments | [cs231n.stanford.edu](https://cs231n.stanford.edu/) |
| "Attention Is All You Need" (Vaswani et al., 2017) | Paper | [arxiv.org/abs/1706.03762](https://arxiv.org/abs/1706.03762) |
| The Illustrated Transformer (Jay Alammar) | Blog Post | [jalammar.github.io](https://jalammar.github.io/illustrated-transformer/) |
| Lilian Weng's Blog | Reference Blog | [lilianweng.github.io](https://lilianweng.github.io/) |

**Deliverable:** Implement a small transformer and train it on a toy task. Read 2–3 papers per week and write summaries.

**Weekly Homework:**

| Week | Assignment |
|------|-----------|
| 9 | Complete Karpathy's "Let's build GPT" video. Watch CS231n lectures 1–4 (image classification, loss functions, optimization, neural networks). Read "Attention Is All You Need" and Jay Alammar's Illustrated Transformer. Write a 1-page summary of the attention mechanism in your own words. |
| 10 | Implement multi-head self-attention from scratch in PyTorch. No copying from the video, reference the paper only. Verify your implementation produces the same outputs as `nn.MultiheadAttention` on the same inputs. Read 2 papers from the reading list and write paragraph summaries. |
| 11 | Build a complete mini-GPT: token embeddings, positional encoding, transformer blocks (attention + feedforward + layer norm), and a language modeling head. Train it on a small text corpus (Shakespeare or similar). Log loss curves with W&B or matplotlib. Read 2 more papers. |
| 12 | Experiment with your mini-GPT: try different hyperparameters (number of heads, layers, embedding dim), plot the results, and write up what you learned. Read 2 more papers. Create a "paper summaries" section in your `ml-foundations` repo with all summaries to date. |

### ✅ Phase 1 Milestone
> Can you read a recent ML paper and understand 70–80% on first pass? Can you implement the core ideas in PyTorch without copying code?

---

## Phase 2: Survey Sprint (Months 4–5)

**Goal:** Build working-level familiarity across all three major research areas through hands-on implementation, then make an informed decision about where to specialize.

Each area gets 3 weeks. The hard rule: every sprint must produce a working implementation (a trained model, not notes). By the end, you'll pick your specialization from experience, not guesswork.

### Sprint A: Reinforcement Learning & Alignment (Weeks 13–15)

| Resource | Type | Link |
|----------|------|------|
| Sutton & Barto – Reinforcement Learning: An Introduction (2nd ed.) | Textbook (free) | [incompleteideas.net/book](http://incompleteideas.net/book/the-book-2nd.html) |
| David Silver – RL Lecture Series | Video Series | [youtube.com/playlist](https://www.youtube.com/playlist?list=PLqYmG7hTraZDM-OYHWgPebj2MfCFzFObQ) |
| OpenAI Spinning Up in Deep RL | Tutorial + Code | [spinningup.openai.com](https://spinningup.openai.com/en/latest/) |
| Hugging Face Deep RL Course | Interactive Course | [huggingface.co/deep-rl-course](https://huggingface.co/learn/deep-rl-course/) |

**Weekly Homework:**

| Week | Assignment |
|------|-----------|
| 13 | Read Sutton & Barto chapters 1–6 (bandits, MDPs, dynamic programming, Monte Carlo, TD learning). Watch David Silver lectures 1–4. Implement tabular Q-learning from scratch and solve a grid world environment. Push to `ml-foundations/rl-sprint`. |
| 14 | Read Sutton & Barto chapters 9–10 (function approximation, policy gradient). Work through Spinning Up's key concepts and REINFORCE tutorial. Implement REINFORCE in PyTorch on CartPole. Log training curves. |
| 15 | **Sprint deliverable.** Implement PPO from scratch in PyTorch on LunarLander or CartPole. Compare against Stable Baselines3's PPO on the same task. Read the InstructGPT paper and write a 1-page analysis connecting PPO to RLHF. Push final code + write-up to `ml-foundations/rl-sprint`. |

### Sprint B: Language Model Training Pipeline (Weeks 16–18)

| Resource | Type | Link |
|----------|------|------|
| Hugging Face NLP Course | Interactive Course | [huggingface.co/course](https://huggingface.co/learn/nlp-course/) |
| "Training Language Models to Follow Instructions" (InstructGPT) | Paper | [arxiv.org/abs/2203.02155](https://arxiv.org/abs/2203.02155) |
| "Constitutional AI" (Bai et al., 2022) | Paper | [arxiv.org/abs/2212.08073](https://arxiv.org/abs/2212.08073) |
| "Direct Preference Optimization" (Rafailov et al., 2023) | Paper | [arxiv.org/abs/2305.18290](https://arxiv.org/abs/2305.18290) |
| Hugging Face TRL Library | RLHF Training | [github.com/huggingface/trl](https://github.com/huggingface/trl) |

**Weekly Homework:**

| Week | Assignment |
|------|-----------|
| 16 | Complete HuggingFace NLP Course chapters 1–4 (pipeline API, tokenizers, fine-tuning). Fine-tune a small pretrained model (e.g., DistilBERT or GPT-2 small) on a text classification task using HuggingFace Trainer. Push to `ml-foundations/lm-sprint`. |
| 17 | Read InstructGPT and Constitutional AI papers. Fine-tune a small language model using supervised fine-tuning (SFT) on an instruction-following dataset using TRL. Understand the full pipeline: base model → SFT → reward model → RLHF. |
| 18 | **Sprint deliverable.** Implement DPO fine-tuning on a small model using TRL. Compare the outputs of your base model, SFT model, and DPO model on the same prompts. Document the qualitative differences. Write a 1-page comparison of RLHF vs. DPO covering tradeoffs and when to use each. Push final code + write-up to `ml-foundations/lm-sprint`. |

### Sprint C: Diffusion Models, Pixel Prediction & World Models (Weeks 19–21)

Generative modeling, spatial reasoning, and learning physics from pixels converge in this area. Particularly relevant for labs working on video generation, robotics, and world simulation.

*Foundations, Diffusion Models:*

| Resource | Type | Link |
|----------|------|------|
| "Denoising Diffusion Probabilistic Models" (Ho et al., 2020) | Foundational Paper | [arxiv.org/abs/2006.11239](https://arxiv.org/abs/2006.11239) |
| "Denoising Diffusion Implicit Models" (Song et al., 2021) | Paper (DDIM) | [arxiv.org/abs/2010.02502](https://arxiv.org/abs/2010.02502) |
| "Score-Based Generative Modeling through SDEs" (Song et al., 2021) | Paper (Unified Framework) | [arxiv.org/abs/2011.13456](https://arxiv.org/abs/2011.13456) |
| Lilian Weng – "What Are Diffusion Models?" | Blog Post | [lilianweng.github.io](https://lilianweng.github.io/posts/2021-07-11-diffusion-models/) |
| Hugging Face Diffusion Models Course | Interactive Course | [github.com/huggingface/diffusion-models-class](https://github.com/huggingface/diffusion-models-class) |
| The Annotated Diffusion Model | Code Walkthrough | [huggingface.co/blog](https://huggingface.co/blog/annotated-diffusion) |

*Architecture, Latent Diffusion & Conditioning:*

| Resource | Type | Link |
|----------|------|------|
| "High-Resolution Image Synthesis with Latent Diffusion Models" (Rombach et al., 2022) | Paper (Stable Diffusion) | [arxiv.org/abs/2112.10752](https://arxiv.org/abs/2112.10752) |
| "Scalable Diffusion Models with Transformers" (Peebles & Xie, 2023) | Paper (DiT) | [arxiv.org/abs/2212.09748](https://arxiv.org/abs/2212.09748) |
| "Photorealistic Text-to-Image Diffusion Models with Deep Language Understanding" (Saharia et al., 2022) | Paper (Imagen) | [arxiv.org/abs/2205.11487](https://arxiv.org/abs/2205.11487) |
| Diffusers Library | Code & Docs | [github.com/huggingface/diffusers](https://github.com/huggingface/diffusers) |

*Video Generation & Temporal Modeling:*

| Resource | Type | Link |
|----------|------|------|
| "Video Diffusion Models" (Ho et al., 2022) | Paper | [arxiv.org/abs/2204.03458](https://arxiv.org/abs/2204.03458) |
| "Scalable Adaptive Computation for Iterative Generation" (Runway Gen-1) | Paper | [arxiv.org/abs/2210.02303](https://arxiv.org/abs/2210.02303) |
| "Sora: A Review on Background, Technology, Limitations, and Opportunities" | Survey Paper | [arxiv.org/abs/2402.17177](https://arxiv.org/abs/2402.17177) |
| "Scaling Rectified Flow Transformers for High-Resolution Image Synthesis" (Esser et al., 2024) | Paper (SD3 / Flow Matching) | [arxiv.org/abs/2403.03206](https://arxiv.org/abs/2403.03206) |

*World Models & Pixel Prediction:*

| Resource | Type | Link |
|----------|------|------|
| "World Models" (Ha & Schmidhuber, 2018) | Foundational Paper | [arxiv.org/abs/1803.10122](https://arxiv.org/abs/1803.10122) |
| World Models Interactive Site | Visual Explainer | [worldmodels.github.io](https://worldmodels.github.io/) |
| "Mastering Diverse Domains through World Models" (DreamerV3, Hafner et al., 2023) | Paper | [arxiv.org/abs/2301.04104](https://arxiv.org/abs/2301.04104) |
| "Learning Universal Policies via Text-Guided Video Generation" (UniPi, Du et al., 2023) | Paper | [arxiv.org/abs/2302.00111](https://arxiv.org/abs/2302.00111) |
| "Genie: Generative Interactive Environments" (Bruce et al., 2024) | Paper (DeepMind) | [arxiv.org/abs/2402.15391](https://arxiv.org/abs/2402.15391) |
| "Learning Interactive Real-World Simulators" (Yang et al., 2024) | Paper (UniSim) | [arxiv.org/abs/2310.06114](https://arxiv.org/abs/2310.06114) |

**Weekly Homework:**

| Week | Assignment |
|------|-----------|
| 19 | Read Lilian Weng's diffusion blog post and the DDPM paper. Complete the first 2 units of the HuggingFace Diffusion Models Course. Implement the forward diffusion process (noise scheduling) from scratch in PyTorch. Visualize an image being progressively noised. Push to `ml-foundations/diffusion-sprint`. |
| 20 | Read the latent diffusion and DiT papers. Implement a simple DDPM (unconditional, on MNIST or CIFAR-10) using the Annotated Diffusion Model walkthrough as a reference but writing your own code. Train it and generate samples. Read the World Models (Ha & Schmidhuber) paper and DreamerV3. |
| 21 | **Sprint deliverable.** Fine-tune a small Stable Diffusion model or train a conditional diffusion model on a custom dataset using the Diffusers library. Generate samples and evaluate quality. Write a 1-page synthesis: how do diffusion models, video generation, and world models connect? What's the path from DDPM to Sora? Push final code + write-up to `ml-foundations/diffusion-sprint`. |

### Specialization Decision

At the end of week 21, you've built working implementations in all three areas. Now choose. Write a 1-page memo to yourself answering:

- Which area did I find most intellectually engaging?
- Which sprint's implementation did I most want to keep working on?
- Which area best aligns with the labs and roles I'm drawn to?
- Where do I see the most open questions I'd want to investigate?

Commit to your answer and don't look back.

### ✅ Phase 2 Milestone
> You have 3 working implementations across RL, language models, and diffusion/world models. You've made an informed specialization decision backed by hands-on experience.

---

## Phase 3: Deep Specialization + Replication Project (Months 6–8)

**Goal:** Go deep in your chosen area and produce your most important portfolio artifact, a complete paper replication.

### Month 6: Go Deep on Your Chosen Area (Weeks 22–25)

Return to the sprint that won and go much deeper. Your 3-week survey gave you the map. Now explore the territory. The resources from Phase 2 are your starting points. Go beyond them.

**Weekly Homework:**

| Week | Assignment |
|------|-----------|
| 22 | **Deep reading week.** Read 5–6 papers in your area beyond the ones from the survey sprint. For each, write a paragraph summary and note what's novel, what extends prior work, and what open questions remain. Identify the 2–3 most active sub-areas. |
| 23 | **Intermediate implementation.** Build something more ambitious than your sprint project. For RL: implement SAC or TD3 and solve a harder continuous control task. For LM: implement a reward model and full RLHF pipeline from scratch (not using TRL). For diffusion: implement a classifier-free guidance system or a DiT from scratch. |
| 24 | **Push to frontier understanding.** Read 3–4 papers from the last 6 months in your area. These are the papers you might replicate. Start a shortlist of 5–8 replication candidates, papers that are impressive, tractable, and well-benchmarked. |
| 25 | **Paper selection + deep read.** Narrow to your top 3 candidates. For each, assess data availability, compute requirements, clarity of methodology, and availability of benchmarks. Pick your replication target. Read it 3 times. Write a 1-page implementation plan covering what you need to build, what you can reuse, and the biggest risks. |

### Months 7–8: Replication Project (Weeks 26–33)

The single most important deliverable of the entire 13 months. A well-executed replication study shows you can read a paper, understand it deeply, implement it correctly, run rigorous experiments, and communicate results clearly. That's the job description for research engineers.

| Resource | Type | Link |
|----------|------|------|
| Papers With Code | Paper + Code Discovery | [paperswithcode.com](https://paperswithcode.com/) |
| Weights & Biases | Experiment Tracking | [wandb.ai](https://wandb.ai/) |
| Lambda Cloud / Vast.ai / RunPod | GPU Compute | [lambdalabs.com](https://lambdalabs.com/service/gpu-cloud) / [vast.ai](https://vast.ai/) / [runpod.io](https://www.runpod.io/) |

**Weekly Homework:**

| Week | Assignment |
|------|-----------|
| 26 | **Infrastructure setup.** Create a new GitHub repo for the project. Set up your compute environment (GPU cloud account, W&B project, conda environment with pinned dependencies). Implement the data loading, preprocessing, and augmentation pipeline. Write unit tests to verify shapes, value ranges, and edge cases. |
| 27 | **Model architecture.** Implement the model architecture exactly as described in the paper. Don't optimize prematurely. Run a forward pass on dummy data and verify output shapes match what the paper describes. Write tests for each major component. |
| 28 | **Training loop + first runs.** Implement the full training loop with the paper's optimizer, learning rate schedule, and hyperparameters. Run your first real training run. It won't work. That's expected. Debug and iterate. Log everything to W&B. |
| 29 | **Debug and stabilize.** Most people underestimate this week. Systematically debug any discrepancies: compare loss curves to the paper's, check gradient norms, verify data augmentation is correct, test on smaller subsets. Get training to converge. |
| 30 | **Reproduce key results.** Run the main experiments from the paper. Track all metrics with W&B. Compare against the paper's reported numbers. Document where your results match and where they diverge. |
| 31 | **Ablations.** Run at least 3 ablation experiments: vary a key hyperparameter, remove a component, change the data distribution. Ablations are where you learn the most and where your write-up becomes interesting. Create publication-quality figures. |
| 32 | **Write the technical report.** Write a 2,000–4,000 word write-up covering what you replicated, your methodology, results vs. paper, ablation findings, and lessons learned. Structure it like a paper (abstract, intro, methods, results, discussion). |
| 33 | **Polish and publish.** Clean up the repo: clear README with reproduction instructions, requirements.txt, example outputs. Revise the write-up on a fresh read. Publish the blog post and share on Twitter/X. Push everything. |

### ✅ Phase 3 Milestone
> You have deep expertise in one area, a public GitHub repo with a completed replication study, and a well-written technical report.

---

## Phase 4: Build Credibility + Community (Months 9–11)

**Goal:** Establish a public presence through open-source contributions, a second (more original) research project, and community engagement.

### Month 9: Open-Source Contributions (Weeks 34–37)

Target 2–3 active repos. Start with docs/bug fixes, then work toward meaningful features.

| Project | Focus Area | Link |
|---------|-----------|------|
| Hugging Face Transformers | Model implementations, tokenizers | [github.com/huggingface/transformers](https://github.com/huggingface/transformers) |
| vLLM | Inference engine, serving | [github.com/vllm-project/vllm](https://github.com/vllm-project/vllm) |
| EleutherAI lm-evaluation-harness | Evaluation & benchmarking | [github.com/EleutherAI/lm-evaluation-harness](https://github.com/EleutherAI/lm-evaluation-harness) |
| trl (Transformer Reinforcement Learning) | RLHF training | [github.com/huggingface/trl](https://github.com/huggingface/trl) |

**Weekly Homework:**

| Week | Assignment |
|------|-----------|
| 34 | **Reconnaissance.** Clone 2–3 target repos. Read their CONTRIBUTING.md, browse open issues labeled "good first issue" or "help wanted." Build each project locally and run the test suite. Pick your primary repo. |
| 35 | **First PR.** Submit a small but real contribution: fix a documentation error, add a missing type hint, fix a linting issue, or improve an error message. The goal is to learn the PR workflow and get your name in the commit history. |
| 36 | **Second PR, more substantial.** Fix a real bug or add a small feature. Read the relevant source code deeply enough to understand the architecture around your change. Write tests for your contribution. |
| 37 | **Third PR or meaningful issue.** Either submit another PR that touches core logic, or write a detailed issue with a proposed solution for a non-trivial problem you've identified. Engage with maintainer feedback on all your PRs. Write a brief post about what you learned from reading production ML codebases. |

### Month 10: Second Research Project (Weeks 38–41)

Extend your replication work with a novel angle. The key differentiator: "I replicated paper X, noticed Y was underexplored, so I ran these experiments." Even negative results are valuable if well-documented.

**Weekly Homework:**

| Week | Assignment |
|------|-----------|
| 38 | **Research question formulation.** Review your replication project. What surprised you? Where did results diverge? What wasn't tested? Write 3 candidate research questions and pick the one that's most tractable in 4 weeks. Write a 1-page "mini-proposal" with hypothesis, method, and expected outcomes. |
| 39 | **Experiment design + baseline.** Design your experimental setup: what are your baselines, what metrics will you track, what constitutes a meaningful result? Adapt your replication codebase for the new experiments. Run baselines and sanity checks. |
| 40 | **Run core experiments.** Execute your planned experiments. Track everything in W&B. If early results are surprising (positive or negative), investigate why before moving on. Adjust your experimental plan if needed. Research is iterative. |
| 41 | **Analysis + preliminary write-up.** Analyze all results. Create figures and tables. Write a 1-page summary of findings. Decide whether the results are strong enough to extend into the Month 13 capstone or whether you'll pursue a different direction. |

### Month 11: Write-Up + Community Building (Weeks 42–45)

| Resource | Type | Link |
|----------|------|------|
| arXiv | Preprint Server | [arxiv.org](https://arxiv.org/) |
| Distill.pub (archived, but great format reference) | Research Communication | [distill.pub](https://distill.pub/) |
| ML Twitter/X Community | Networking | Key accounts: [@kaboroevich](https://x.com/kaboroevich), [@_jasonwei](https://x.com/_jasonwei), [@ylaboratory](https://x.com/ylaboratory) |

**Weekly Homework:**

| Week | Assignment |
|------|-----------|
| 42 | **Draft the technical report.** Write the full paper structure: abstract, introduction (motivation + related work), methods, experiments, results, discussion, conclusion. Aim for 4,000–6,000 words. Don't polish yet. Get the full structure down. |
| 43 | **Revise + create figures.** Rewrite the draft for clarity. Create all figures and tables to publication quality (use matplotlib with clean styling or LaTeX). Have someone technically literate read it and give feedback. Revise again. |
| 44 | **Publish + share.** Post to arXiv if quality warrants it, otherwise publish as a blog post. Clean up and publish the code repo. Share on Twitter/X with a concise thread summarizing the key findings. Engage with any responses. |
| 45 | **Community engagement sprint.** Write and post 3 paper summaries on Twitter/X for recent papers in your area. Comment thoughtfully on 5+ ML research threads. Follow and engage with researchers at labs you're interested in. The goal is to be a visible, contributing member of the community, not a lurker. |

### ✅ Phase 4 Milestone
> You have 2 substantial public projects (one replication, one with a novel angle), meaningful open-source contributions, and a real presence in the ML research community.

---

## Phase 5: Frontier Topics + Capstone (Months 12–13)

**Goal:** Develop fluency in cross-cutting frontier areas and produce a capstone project with an original contribution.

### Month 12: Frontier Topics (Weeks 46–49)

Go deep on 1–2 areas that represent where the field is heading. These topics cut across specializations. They're relevant regardless of what you chose in Phase 3.

**Mechanistic Interpretability:**

| Resource | Type | Link |
|----------|------|------|
| Neel Nanda – "A Mechanistic Interpretability Explainer" | Blog Series | [neelnanda.io](https://www.neelnanda.io/mechanistic-interpretability/glossary) |
| "Toy Models of Superposition" (Elhage et al., 2022) | Paper (Anthropic) | [transformer-circuits.pub](https://transformer-circuits.pub/2022/toy_model/index.html) |
| "Scaling Monosemanticity" (Templeton et al., 2024) | Paper (Anthropic) | [transformer-circuits.pub](https://transformer-circuits.pub/2024/scaling-monosemanticity/) |
| TransformerLens | Interpretability Library | [github.com/TransformerLensOrg/TransformerLens](https://github.com/TransformerLensOrg/TransformerLens) |
| ARENA (Alignment Research Engineer Accelerator) | Structured Curriculum | [arena3-chapter1-transformer-interp.streamlit.app](https://arena3-chapter1-transformer-interp.streamlit.app/) |

**Scaling Laws & Emergent Capabilities:**

| Resource | Type | Link |
|----------|------|------|
| "Scaling Laws for Neural Language Models" (Kaplan et al., 2020) | Paper | [arxiv.org/abs/2001.08361](https://arxiv.org/abs/2001.08361) |
| "Training Compute-Optimal Large Language Models" (Chinchilla) | Paper | [arxiv.org/abs/2203.15556](https://arxiv.org/abs/2203.15556) |
| "Scaling Data-Constrained Language Models" (Muennighoff et al., 2023) | Paper | [arxiv.org/abs/2305.16264](https://arxiv.org/abs/2305.16264) |
| "Are Emergent Abilities of Large Language Models a Mirage?" (Schaeffer et al., 2023) | Paper | [arxiv.org/abs/2304.15004](https://arxiv.org/abs/2304.15004) |

**AI Safety & Alignment Research:**

| Resource | Type | Link |
|----------|------|------|
| "Concrete Problems in AI Safety" (Amodei et al., 2016) | Foundational Paper | [arxiv.org/abs/1606.06565](https://arxiv.org/abs/1606.06565) |
| Anthropic Research Page | Research Papers | [anthropic.com/research](https://www.anthropic.com/research) |
| AI Safety Fundamentals Course | Structured Course | [aisafetyfundamentals.com](https://aisafetyfundamentals.com/) |
| "Sleeper Agents" (Hubinger et al., 2024) | Paper (Anthropic) | [arxiv.org/abs/2401.05566](https://arxiv.org/abs/2401.05566) |

**Targeted Skill Gaps:**

| Topic | Resource | Link |
|-------|----------|------|
| Distributed Training (DeepSpeed) | DeepSpeed Documentation | [deepspeed.ai](https://www.deepspeed.ai/) |
| Distributed Training (FSDP) | PyTorch FSDP Tutorial | [pytorch.org/tutorials](https://pytorch.org/tutorials/intermediate/FSDP_tutorial.html) |
| Experiment Tracking | Weights & Biases Docs | [docs.wandb.ai](https://docs.wandb.ai/) |
| Information Theory | Cover & Thomas Textbook + MIT OCW | [ocw.mit.edu](https://ocw.mit.edu/courses/6-441-information-theory-spring-2016/) |
| ML Systems Design | Chip Huyen – Designing ML Systems | [O'Reilly](https://www.oreilly.com/library/view/designing-machine-learning/9781098107956/) |

**Weekly Homework:**

| Week | Assignment |
|------|-----------|
| 46 | **Mechanistic interpretability deep read.** Read Neel Nanda's explainer and "Toy Models of Superposition." Install TransformerLens and run the introductory tutorials. Reproduce a basic finding: e.g., identify induction heads in a small GPT-2 model using TransformerLens. |
| 47 | **Interpretability hands-on + scaling laws.** Complete 2–3 exercises from the ARENA interpretability curriculum. Read "Scaling Monosemanticity." Read the Kaplan and Chinchilla scaling laws papers. Reproduce a simple scaling law: train models of 3–5 different sizes on the same dataset, plot loss vs. parameters, and check for power law relationships. |
| 48 | **Safety + alignment + skill gaps.** Read "Concrete Problems in AI Safety" and "Sleeper Agents." Complete the first module of the AI Safety Fundamentals course. Identify your top 2 remaining skill gaps and begin addressing the most critical one (e.g., convert your replication project to distributed training with FSDP). |
| 49 | **Synthesis + capstone planning.** Write a 1,500-word essay synthesizing what you've learned: how do interpretability, scaling laws, and alignment connect to your specialization? Post it publicly. Begin scoping your capstone project. |

### Month 13: Capstone Project (Weeks 50–53)

Your most ambitious project yet. It should combine technical depth with original thinking and span your chosen specialization. Unlike the replication in months 7–8, the capstone needs a novel contribution: a new experiment, a meaningful extension, or a cross-domain application that hasn't been explored.

**What "good" looks like:**
- Builds on your earlier replication and extension work from Phases 3–4
- Has a clear research question, not an implementation exercise
- Includes proper experimental methodology: baselines, ablations, statistical significance
- Results written up in full paper format (abstract, intro, methods, results, discussion)
- Code is clean, documented, and reproducible

**Infrastructure for serious experiments:**

| Resource | Type | Link |
|----------|------|------|
| Lambda Cloud | GPU Compute | [lambdalabs.com](https://lambdalabs.com/service/gpu-cloud) |
| Vast.ai | Cheap GPU Rentals | [vast.ai](https://vast.ai/) |
| RunPod | GPU Compute | [runpod.io](https://www.runpod.io/) |
| Weights & Biases | Experiment Tracking | [wandb.ai](https://wandb.ai/) |
| arXiv | Preprint Server | [arxiv.org](https://arxiv.org/) |

**Weekly Homework:**

| Week | Assignment |
|------|-----------|
| 50 | **Scope and plan.** Write a 2-page research proposal covering question, hypothesis, related work, method, experiments, and expected timeline. Set up the repo, compute, and experiment tracking. Get your data pipeline and baselines running by end of week. |
| 51 | **Core experiments.** Run your primary experiments. Track everything. Write up preliminary results as you go. Don't wait until the end. If something isn't working, diagnose and pivot early. |
| 52 | **Ablations + extended experiments.** Run ablations and any secondary experiments. Create all figures and tables. Begin writing the full paper: abstract, intro, methods, and results sections. |
| 53 | **Final write-up + publication.** Complete the paper (discussion, conclusion, references). Clean and document all code. Submit to arXiv or publish as a technical blog post. Share on Twitter/X with a summary thread. Update your `ml-foundations` repo README to link to all 13 months of work. |

**Deliverable:** A complete technical report suitable for arXiv submission, with accompanying code repository. The capstone becomes the centerpiece of your portfolio.

### ✅ Phase 5 Milestone
> You have deep knowledge in 1–2 frontier areas, a capstone project with an original contribution, and a portfolio showing the ability to independently conduct research.

## Logistics & Time Budget

| Phase | Months | Intensity | Notes |
|-------|--------|-----------|-------|
| Phase 1: Foundations | 1–3 | ~20 hrs/week | Heavy learning, moderate coding |
| Phase 2: Survey Sprint | 4–5 | ~20 hrs/week | Fast-paced, 3 implementations in 9 weeks |
| Phase 3: Deep Specialization + Replication | 6–8 | ~20–25 hrs/week | Most demanding phase. The replication project requires sustained focus. |
| Phase 4: Credibility + Community | 9–11 | ~20 hrs/week | Mix of coding, writing, and community engagement |
| Phase 5: Frontier + Capstone | 12–13 | ~20–25 hrs/week | Research-heavy, culminates in your best work |

**Common failure modes to avoid:**
- Taking "one more course" instead of building projects
- Perfectionism on code quality over research output
- Reading papers passively instead of implementing them
- Skipping the writing (the public artifacts are what get you hired)
- Comparing yourself to PhD students who've had 4+ years of mentored research experience

**On pacing:** Some weeks will take 10 hours. Others will take 30. The weekly structure is a guide, not a mandate. What matters is completing each assignment before moving to the next, and not skipping the hard parts (the writing, the debugging, the sharing publicly).

## Essential Reading List

A curated set of papers to read across the 13 months, roughly in order of when they become relevant:

1. [Attention Is All You Need](https://arxiv.org/abs/1706.03762), Vaswani et al., 2017
2. [BERT: Pre-training of Deep Bidirectional Transformers](https://arxiv.org/abs/1810.04805), Devlin et al., 2018
3. [Language Models are Few-Shot Learners (GPT-3)](https://arxiv.org/abs/2005.14165), Brown et al., 2020
4. [Training Language Models to Follow Instructions (InstructGPT)](https://arxiv.org/abs/2203.02155), Ouyang et al., 2022
5. [Constitutional AI](https://arxiv.org/abs/2212.08073), Bai et al., 2022
6. [Direct Preference Optimization (DPO)](https://arxiv.org/abs/2305.18290), Rafailov et al., 2023
7. [LLaMA: Open and Efficient Foundation Language Models](https://arxiv.org/abs/2302.13971), Touvron et al., 2023
8. [Scaling Laws for Neural Language Models](https://arxiv.org/abs/2001.08361), Kaplan et al., 2020
9. [Chinchilla: Training Compute-Optimal Large Language Models](https://arxiv.org/abs/2203.15556), Hoffmann et al., 2022
10. [Proximal Policy Optimization (PPO)](https://arxiv.org/abs/1707.06347), Schulman et al., 2017
11. [Denoising Diffusion Probabilistic Models (DDPM)](https://arxiv.org/abs/2006.11239), Ho et al., 2020
12. [High-Resolution Image Synthesis with Latent Diffusion Models](https://arxiv.org/abs/2112.10752), Rombach et al., 2022
13. [Scalable Diffusion Models with Transformers (DiT)](https://arxiv.org/abs/2212.09748), Peebles & Xie, 2023
14. [Mastering Diverse Domains through World Models (DreamerV3)](https://arxiv.org/abs/2301.04104), Hafner et al., 2023
15. [Concrete Problems in AI Safety](https://arxiv.org/abs/1606.06565), Amodei et al., 2016
16. [Toy Models of Superposition](https://transformer-circuits.pub/2022/toy_model/index.html), Elhage et al., 2022
17. [Scaling Monosemanticity](https://transformer-circuits.pub/2024/scaling-monosemanticity/), Templeton et al., 2024

## Contributing

Found a broken link? Have a better resource for a specific week? Open an issue or PR. The syllabus will need updates as the field moves. Contributions are welcome.

---

*Last updated: March 2026*
