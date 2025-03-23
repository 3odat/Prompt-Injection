# 🛡️ Prompt Injection Defense Framework for LLMs  
> An advanced dual-layer safeguard system using AI classifiers + fine-tuned LLMs to stop prompt injection attacks in real time.

![Prompt Injection Defense Banner](https://yourdomain.com/assets/banner.png)

---

## 🚀 Overview

**Prompt Injection Attacks** are one of the most severe vulnerabilities in modern LLM-based applications. This repository presents a **novel, research-backed dual-layer architecture**:

- ✅ **Layer 1: Prompt Classifier** – A transformer-based model (e.g., DistilBERT or RoBERTa) pre-screens user input for injection attempts  
- ✅ **Layer 2: Hardened LLM** – A fine-tuned instruction-following LLM (e.g., LLaMA2-Chat / Mistral) using **LoRA adapters**, trained to resist injections and respond safely

**Real-time, modular, and continuously improving.** Ideal for deployment in LLM-based agents, chatbots, or any application involving natural language instructions.

---

## 🧠 Core Features

| Feature                         | Description                                                                 |
|--------------------------------|-----------------------------------------------------------------------------|
| 🔍 Prompt Injection Detection   | Pre-trained classifier flags malicious input using advanced NLP models     |
| 🧩 LoRA-based Fine-Tuning       | Efficient training with minimal GPU memory using PEFT & QLoRA              |
| 🔁 Continuous Learning Loop     | Self-healing feedback pipeline (human-in-the-loop + auto re-training)      |
| 📈 Benchmark & Evaluation Suite | Attack Success Rate (ASR), Precision/Recall, and real-world jailbreak tests|
| 🌐 Ready for Deployment         | Docker-ready REST API with FastAPI (or Flask)                              |

---

## 🧱 Architecture

```mermaid
flowchart TD
    User[🧑 User Prompt]
    Classifier[🧠 Prompt Classifier<br>(DistilBERT / DeBERTa)]
    Decision{Injection Detected?}
    Blocked[🚫 Refused or Sanitized]
    SafeLLM[🤖 Fine-Tuned LLM<br>(LoRA Adapter)]
    Response[📤 Output to User]
    Feedback[🔁 Feedback & Retraining]

    User --> Classifier --> Decision
    Decision -- Yes --> Blocked
    Decision -- No --> SafeLLM --> Response
    Blocked --> Feedback
    Response --> Feedback
