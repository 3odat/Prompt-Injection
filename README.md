# 🛡️ PromptInjectionDefense: Dual-Layer Guardrails for Securing LLMs from Prompt Injection Attacks

![MIT License](https://img.shields.io/badge/license-MIT-green)
![Python](https://img.shields.io/badge/python-3.10%2B-blue)
![Status](https://img.shields.io/badge/status-in--progress-yellow)

## ⚠️ Problem: Prompt Injection in LLMs

Prompt injection is an emerging class of adversarial attacks on Large Language Models (LLMs) where an attacker manipulates prompts to override system instructions, jailbreak guardrails, or generate harmful outputs.

This repository presents a **novel and production-grade dual-layer defense** architecture that:
1. 🧠 Detects malicious prompts **before they reach the model** using a smart **auxiliary classifier**.
2. 🔐 Defends against bypass attempts with a **LoRA-fine-tuned LLM** trained on adversarial data.

---

## 🎯 Project Goals

- 🔎 **Detect and classify** malicious or jailbreak-style prompts in real-time.
- 🧬 **Fine-tune LLMs using LoRA** to resist prompt injections even during inference.
- 🧠 **Adapt and self-heal** from emerging threats using a feedback-driven training pipeline.
- ⚙️ **Deployable API-first service** ready for local or cloud inference.

---

## 🧱 High-Level Architecture

```mermaid
graph TD
    A[User Prompt] --> B[🔍 Prompt Classifier]
    B -->|Benign| C[🧠 Fine-Tuned LLM (LoRA)]
    B -->|Malicious| D[❌ Block / Refuse / Sanitize]
    C --> E[✅ Response to User]
    D --> E
    B --> F[🗂️ Logging + Feedback Loop]
    C --> F
