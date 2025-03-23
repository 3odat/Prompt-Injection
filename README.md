# 🔐 Prompt Injection Defense Framework (PID-Guard)

**PID-Guard** is a production-ready, research-backed dual-layer defense system designed to protect Large Language Models (LLMs) from **Prompt Injection** and **Jailbreak-style attacks**.

This repository introduces a **novel two-layer architecture** combining:
- 🧠 A lightweight **Auxiliary Classifier** that pre-filters user prompts.
- 🛡️ A **LoRA-fine-tuned LLM** hardened against adversarial instructions.

Built for researchers, developers, and companies deploying LLMs in secure environments. Inspired by real-world attacks, red teaming efforts, and modern adversarial techniques.

---

## 📁 Project Structure

```bash
📦 pid-guard/
├── data/
│   ├── train_prompts.csv       # Labeled training data (benign + malicious)
│   └── test_prompts.csv        # Test set with adversarial examples
├── classifier/
│   ├── train_classifier.py     # Fine-tune DistilBERT/RoBERTa classifier
│   ├── model/                  # Trained classifier artifacts
│   └── utils.py                # Tokenizer, metrics, pre-processing
├── lora_finetune/
│   ├── train_lora_llm.py       # LoRA/QLoRA fine-tuning script for LLaMA2/Mistral
│   ├── config.json             # LoRA config
│   └── model_adapter/          # Saved LoRA adapter weights
├── api/
│   ├── main.py                 # FastAPI server with classifier + LLM routing
│   ├── handler.py              # Core logic: classify → route to LLM or block
│   └── templates/              # Optional: simple frontend chat UI
├── monitoring/
│   ├── logs/                   # Saved prompt/classifier/LLM logs
│   └── analyzer.py             # Review false positives, successes, trends
├── evaluation/
│   ├── robustness_tests.py     # Attack simulation, ASR evaluation
│   ├── metrics.py              # Precision, Recall, F1 computation
│   └── reports/                # Benchmarking results (PDF/CSV/Markdown)
├── README.md                   # You're here 🚀
└── requirements.txt            # All dependencies (HF, PEFT, etc.)
