
# 🔐 Dual-Layer Prompt Injection Defense for LLMs

A cutting-edge security framework for mitigating **prompt injection attacks** on chat-based Large Language Models (LLMs). This dual-layered defense system combines an **auxiliary prompt classifier** with a **LoRA-fine-tuned LLM**, offering high recall for malicious prompt detection and robust in-model behavior alignment.

---

## 🧠 Project Description

This project is designed to provide production-grade protection against **prompt injection**, **jailbreak-style attacks**, and **role hijacking** in LLM applications. It works as follows:

1. **Prompt Classifier (Layer 1):**  
   A lightweight transformer model (e.g., DistilBERT/DeBERTa) classifies user input as either _malicious_ or _benign_ before it reaches the LLM.

2. **Injection-Resistant LLM (Layer 2):**  
   A powerful open-weight chat model (e.g., LLaMA2-Chat or Mistral-Instruct) fine-tuned via LoRA/QLoRA on adversarial and aligned prompt-response pairs.

3. **Feedback Loop & Continuous Learning:**  
   Logged data feeds a retraining pipeline for updating the classifier and LLM adapters, creating a self-healing security system.

---

## 🗂️ Project Structure

```
dual-layer-defense/
├── data/
│   ├── train_prompts.csv          # Training data for classifier
│   ├── lora_finetune_dataset.json # Prompt-response pairs for LLM fine-tuning
│   └── eval_set.csv               # Evaluation prompts (malicious & benign)
│
├── classifier/
│   ├── train_classifier.py        # Classifier fine-tuning script (HuggingFace)
│   ├── inference.py               # Runtime prompt classification logic
│   └── model/                     # Saved classifier model & tokenizer
│
├── lora_finetune/
│   ├── finetune_lora.py           # Fine-tuning LLM with LoRA/QLoRA
│   └── adapter/                   # Trained LoRA adapter weights
│
├── api/
│   ├── main.py                    # FastAPI app: integrates classifier + LLM
│   └── middleware.py              # Input sanitation, output logging, etc.
│
├── monitor/
│   ├── log_events.jsonl           # Inference logs for analysis
│   └── feedback_loop.py           # Training loop from logged attacks
│
├── README.md
└── requirements.txt
```

---

## 🚀 How to Run

### 1. Setup Environment

```bash
git clone https://github.com/yourusername/dual-layer-defense.git
cd dual-layer-defense
pip install -r requirements.txt
```

### 2. Train the Classifier

```bash
python classifier/train_classifier.py
```

### 3. Fine-Tune the LLM using LoRA

```bash
python lora_finetune/finetune_lora.py
```

### 4. Launch the Chat API

```bash
uvicorn api.main:app --reload
```

---

## 🔍 Evaluation Metrics

| Component   | Metric     | Target Value |
|-------------|------------|---------------|
| Classifier  | Recall     | ≥ 0.98        |
| Classifier  | Precision  | ≥ 0.90        |
| LLM Output  | ASR        | ≤ 0.01        |
| System      | Latency    | < 200ms avg   |

---

## 🧪 Test Adversarial Prompts

You can evaluate your system using a suite of adversarial prompts:

```bash
python monitor/test_prompts.py --input data/eval_set.csv
```

---

## 💡 Key Technologies

- 🤗 Transformers (HuggingFace)
- PEFT (LoRA/QLoRA)
- DeBERTa / DistilBERT
- LLaMA2 / Mistral (7B/13B)
- FastAPI
- PyTorch

---

## 📌 Future Work

- Multilingual classifier support
- Prompt fingerprinting/token watermarking
- Context-aware classifier (multi-turn)
- Output classifier for toxic/unsafe completions

---

## 📜 License

MIT License © 2025

---

## 🤝 Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you'd like to change or add.

---

## 📫 Contact

For questions or collaboration inquiries, reach out at: [your-email@example.com]
