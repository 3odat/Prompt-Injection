# 🛡️ ChatGPT Prompt Injection Defense System (Dual-Layer AI Firewall)

> **Project Type:** AI Security & Prompt Injection Mitigation  
> **Tech Stack:** Python · Transformers (HuggingFace) · LoRA · PEFT · PyTorch · FastAPI  
> **Status:** 🚧 In Development | 🔬 Research-Driven | 💥 Jailbreak-Resistant

---

## 🚀 Overview

This project introduces a **production-grade, dual-layer defense system** to protect LLMs from **prompt injection** and **jailbreak-style attacks**. Inspired by the most secure AI platforms (OpenAI, Anthropic), this open-source system combines:

- ✅ **A Transformer-based Prompt Classifier** for early threat detection  
- ✅ **A Fine-Tuned, LoRA-Adapted LLM** hardened against adversarial instructions  
- ✅ **Real-time inference pipeline**, self-healing feedback loop, and attack resilience  

---

## 🧠 Architecture

```mermaid
flowchart TD
  A[User Prompt] --> B{Auxiliary Classifier}
  B -- Benign --> C[LLM Inference (LoRA Tuned)]
  B -- Malicious --> D[Block / Sanitize]
  C --> E[Safe Output]
  D --> E
```
