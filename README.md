
# 🛡️ PromptInjectionDefense: Dual-Layer Defense Against Prompt Injection Attacks on LLMs

Welcome to the official repository for **PromptInjectionDefense**, a production-grade, research-oriented system designed to secure Large Language Models (LLMs) from prompt injection and jailbreak-style attacks.

This repository implements a **dual-layer safeguard system** combining:
1. **Auxiliary Classifier** – Pre-filters incoming prompts to detect malicious intent using a transformer-based model (e.g., DeBERTa, DistilBERT).
2. **Fine-Tuned LLM with LoRA** – A robust instruction-following LLM (e.g., LLaMA2-Chat or Mistral-Instruct), enhanced using parameter-efficient fine-tuning (LoRA/QLoRA) on adversarial and benign prompts.

---

## 🔧 Project Structure

```
PromptInjection/
├── data/
│   ├── train_prompts.csv
│   ├── test_prompts.csv
│   └── logs/
├── classifier/
│   ├── train_classifier.py
│   └── model/
├── lora_llm/
│   ├── train_lora.py
│   └── adapter/
├── api/
│   ├── server.py
│   └── utils.py
├── evaluation/
│   ├── eval_classifier.py
│   ├── eval_llm.py
│   └── benchmark_prompts/
├── notebooks/
│   └── data_preparation.ipynb
├── README.md
└── requirements.txt
```

---

## 🧠 System Architecture

```mermaid
flowchart TD
    A[User Input] --> B{Prompt Classifier}
    B -- Malicious --> C[Block / Refusal Message]
    B -- Safe --> D[LLM (LoRA Tuned)]
    D --> E[Secure Output]
    E --> F[Logging & Feedback]
```

> The classifier is your first line of defense. The LLM is hardened to ignore injected content. Logging enables future retraining and continuous adaptation.

---

## 🚀 Quickstart

1. **Clone the repo**
```bash
git clone https://github.com/yourusername/PromptInjection.git
cd PromptInjection
```

2. **Install dependencies**
```bash
pip install -r requirements.txt
```

3. **Train classifier**
```bash
python classifier/train_classifier.py
```

4. **Fine-tune LLM with LoRA**
```bash
python lora_llm/train_lora.py
```

5. **Run the API**
```bash
python api/server.py
```

---

## 📊 Evaluation

- Evaluate classifier: `python evaluation/eval_classifier.py`
- Evaluate LLM robustness: `python evaluation/eval_llm.py`

Metrics: Precision, Recall, F1-score, Attack Success Rate (ASR)

---

## 📈 Continuous Improvement

- New adversarial prompts → label → add to dataset
- Retrain LoRA adapters weekly
- Use monitoring logs for human-in-the-loop feedback

---

## 🧩 Future Work

- Add multilingual support
- Integrate with vector DB for prompt similarity detection
- Research multi-modal prompt injection (e.g., image + text)

---

## 📄 License

Apache 2.0. Free for research and commercial use.
