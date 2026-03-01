⛩️ Tokyo 2026 "Future-Proof" Concierge
Fine-tuning Mistral-7B-v0.3 for the Mistral Worldwide Hackathon
🚀 Overview
Standard LLMs have a knowledge cutoff that prevents them from knowing about upcoming infrastructure and events. This project fine-tunes Mistral-7B-Instruct-v0.3 on a hyper-niche dataset of 2026-specific Japanese tourism trends.

From the upcoming PokéPark Kanto to the Tokyo Dream Park, this model acts as a "Time-Traveler" concierge that knows exactly what is happening in Japan tomorrow.

🛠️ Technical Details
Model & Optimization
Base Model: unsloth/mistral-7b-instruct-v0.3-bnb-4bit

Quantization: 4-bit NormalFloat (NF4) via bitsandbytes.

Library: Unsloth. We utilized Unsloth's optimized kernels to achieve a 2x speedup in training and 70% memory reduction, enabling fine-tuning on a standard Google Colab T4/L4 GPU.

Fine-Tuning Method: LoRA
We used Low-Rank Adaptation (LoRA) to train only 0.58% of the total model parameters, making the final artifact (LoRA adapters) lightweight and easy to share.

Rank (r): 16

Target Modules: q_proj, k_proj, v_proj, o_proj, gate_proj, up_proj, down_proj.

Optimizer: adamw_8bit with a cosine learning rate scheduler.

📊 Dataset & Workflow
1. Data Loading
The model was trained on NewPlaces2026_Japan_dataset.jsonl loaded from a local environment. The data uses the Alpaca prompt format:

Instruction: The travel-related query.

Response: The "future-proof" factual answer regarding 2026 Japan.

2. Steps Taken
Environment: Set up Unsloth and Xformers in a Google Colab environment.

Quantization: Loaded the Mistral model in 4-bit to stay within VRAM limits.

Training: Ran a Supervised Fine-Tuning (SFT) session with SFTTrainer.

Logging: Connected to Weights & Biases to monitor training loss and satisfy the requirements for Track 2 (Fine-tuning).

Export: Saved the LoRA adapters and pushed to the official Hugging Face Hackathon organization.

📦 Model Repository
The fine-tuned LoRA adapters are available at:
👉 Trend-SpotterTokyo2026Model on Hugging Face

🔮 Future Works
Hugging Face Space: Build a Gradio/Streamlit UI to allow tourists to use the model via a web interface.

Multilingual Expansion: Extend the fine-tuning to Japanese and French tourism data.

RAG Pipeline: Connect the model to live 2026 booking APIs for real-time price checking.

👥 Hackathon Submission
Track: Track 2 - Fine-tuning (Weights & Biases)

Location: Tokyo / Online

Organization: mistral-hackaton-2026Fine tune Mistral model
