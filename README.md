# Synthesizer V2: LLM-Based Multi-Agent Social Dynamics Simulator (Project Adam V2)

Synthesizer V2 is the official second iteration and massive upgrade of Project Adam. This multi-agent synthetic data framework is designed to simulate complex conversational interactions (both group and private channels) between 4 distinct AI actors built upon specific, operational MBTI personality profiles (INFP, ISTJ, ESFP, ENTJ). 

The project implements a hybrid Director-Actor Architecture, where a commercial cloud LLM manages the narrative arc, and a quantized local LLM handles natural dialogue generation.

---

## Key Features

* Project Adam V2 Evolution: Expanded from the original baseline to support deep socio-behavioral mechanics, including dynamic relationship tracking and automated back-channel plotting.
* Hybrid LLM Architecture (Director-Actor):
    * Director (Groq - Llama 3): Acts as the orchestrator. It monitors the social context and dictates who speaks, to whom, via which channel (group vs. private), and provides short topic directives in real-time.
    * Local Actor (Hugging Face - Llama 3.1 8B Instruct 4-bit): Executes the Director's commands locally on the GPU (optimized for a T4 GPU via bitsandbytes). It generates natural chat messages strictly adhering to each character's unique Spine Profile.
* Dynamic Social Matrix & Conflict Arcs: Features a fully automated timeline including a Social Conflict Trigger (where an actor commits a critical blunder, dropping their reputation and causing peer isolation) and a gradual Reconciliation Phase.
* Dual-Channel Generation: Automatically segments output logs into structured directories: group_chats/ for open discussions and private_chats/ for back-channel gossip and private confrontations.

---

## Tech Stack

* Language: Python
* LLM Frameworks & APIs: Groq API, Hugging Face Transformers, LangChain Community
* Model Optimization: BitsAndBytes (4-bit Quantization), Accelerate
* Environment: Google Colab / Jupyter Notebook (T4 GPU Recommended)

---

## Repository Structure & Data Output

Once the simulation completes, the framework populates your workspace with the following organized asset structure:

```text
data_syn_v2/
├── group_chats/
│   └── session_1_year_2026.json       # Synced logs of public group chat interactions
├── private_chats/
│   ├── A-B.json                       # Back-channel gossip logs between specific actor pairs
│   ├── A-C.json
│   └── ... (all operational pairs)
└── simulation_checkpoint.json         # Global simulation state & final affinity/reputation scores
