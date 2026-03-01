# ⛩️ Tokyo 2026 "Future-Proof" Concierge
*Fine-tuning Mistral-7B-v0.3 for the Mistral Worldwide Hackathon*

---

## 🚀 Overview

Standard LLMs have a knowledge cutoff that prevents them from knowing about upcoming infrastructure and events. This project fine-tunes **Mistral-7B-Instruct-v0.3** on a hyper-niche dataset of 2026-specific information.

From the upcoming **PokéPark Kanto** to the **Tokyo Dream Park**, this model acts as a **"Time-Traveler" concierge** that knows exactly what is happening in Japan tomorrow.

---

## 🛠️ Technical Details

### Model & Optimization

| Component | Details |
|-----------|---------|
| **Base Model** | unsloth/mistral-7b-instruct-v0.3-bnb-4bit |
| **Quantization** | 4-bit NormalFloat (NF4) via bitsandbytes |
| **Library** | Unsloth - optimized kernels with 2x speedup & 70% memory reduction |
| **GPU Support** | Google Colab T4/L4 GPU compatible |

### Fine-Tuning Method: LoRA

- **Target**: Train only **0.58%** of total model parameters
- **Rank (r)**: 16
- **Target Modules**: 
  - q_proj
  - k_proj
  - v_proj
  - o_proj
  - gate_proj
  - up_proj
  - down_proj
- **Optimizer**: adamw_8bit with cosine learning rate scheduler
- **Benefit**: Lightweight LoRA adapters, easy to share

---

## 📊 Dataset & Workflow

### 1. Data Loading

The model was trained on **NewPlaces2026_Japan_dataset.jsonl** using the **Alpaca prompt format**:

| Field | Description |
|-------|-------------|
| **Instruction** | Travel-related query |
| **Response** | "Future-proof" factual answer regarding 2026 Japan |

### 2. Steps Taken

| Step | Description |
|------|-------------|
| **Environment Setup** | Unsloth and Xformers in Google Colab |
| **Quantization** | Loaded Mistral model in 4-bit for VRAM optimization |
| **Training** | Supervised Fine-Tuning (SFT) session with SFTTrainer |
| **Logging** | Weights & Biases integration for monitoring training loss |
| **Export** | Saved LoRA adapters and pushed to Hugging Face Hackathon org |

---

## 📦 Model Repository

The fine-tuned LoRA adapters are available at:

👉 **[Trend-SpotterTokyo2026Model on Hugging Face](https://huggingface.co/mistral-hackaton-2026/Trend-SpotterTokyo2026Model/tree/main)**

---

## 🔮 Future Works

### Phase 2 Enhancements

- **Hugging Face Space**: Build a Gradio/Streamlit UI for web interface access
- **Multilingual Expansion**: Extend fine-tuning to Japanese and French tourism data
- **RAG Pipeline**: Connect to live 2026 booking APIs for real-time price checking

---

## 👥 Hackathon Submission

| Attribute | Value |
|-----------|-------|
| **Track** | Track 2 - Fine-tuning (Weights & Biases) |
| **Location** | Tokyo / Online |
| **Organization** | mistral-hackaton-2026 |
| **Goal** | Fine-tune Mistral model for 2026 Japan Tourism |

---

**Made with ❤️ for the Mistral Worldwide Hackathon 2026**
