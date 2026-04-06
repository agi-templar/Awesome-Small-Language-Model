# Awesome Small Language Models 👼🏻

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

A curated list of open source **Small Language Models** (roughly ≤13B parameters, or small-active-parameter MoE variants).

> **Why small?** Small language models can run on consumer GPUs, edge devices, and even phones — making AI accessible without cloud dependencies.

## Quick Comparison

> Latest version of each model family. Click the model name to jump to details.

| Model | Org | Sizes | Context | Modality | License | Highlights |
|---|---|---|---|---|---|---|
| [OLMo 2](#ai2-olmo) | AI2 | 1B, 7B, 13B | 4K | Text | Apache 2.0 | Fully open (data + code + recipes) |
| [Qwen 3](#alibaba-qwen) | Alibaba | 0.6B–14B, 30B-A3B | 128K | Text | Apache 2.0 | Hybrid thinking; 119 languages; 36T tokens |
| [OpenELM](#apple) | Apple | 270M–3B | 2K | Text | Apple | Layer-wise scaling; MLX support |
| [Command R7B](#cohere) | Cohere | 7B | 128K | Text | CC-BY-NC | RAG & tool-use optimized; 23 languages |
| [DeepSeek-R1 Distill](#deepseek) | DeepSeek | 1.5B–14B | 128K | Text | MIT | Reasoning via RL; distilled from R1 |
| [Gemma 3](#google-gemma) | Google | 1B, 4B, 12B | 128K | Text + Vision | Gemma | 140+ languages; mobile-optimized 3n variants |
| [SmolLM2](#huggingface-smollm) | HuggingFace | 135M–1.7B | 8K | Text | Apache 2.0 | Ultra-small; beats Qwen2.5-1.5B at scale |
| [LLaMA 3.2](#meta-llama) | Meta | 1B, 3B, 11B | 128K | Text + Vision | Llama 3.2 | Edge/mobile optimized; SpinQuant |
| [Phi-4](#microsoft-phi) | Microsoft | 3.8B, 5.6B, 14B | 16K | Text + Vision + Audio | MIT | Surpasses GPT-4o on STEM QA |
| [Mistral Small 3.1](#mistral) | Mistral | 24B | 128K | Text + Vision | Apache 2.0 | Beats GPT-4o Mini; 150 tok/s |
| [RWKV-7](#rwkv) | RWKV | 0.4B–2.9B | Unlimited | Text | Apache 2.0 | RNN; O(1) memory; no KV cache |
| [StableLM 2](#stability-ai) | Stability AI | 1.6B, 12B | 4K | Text | Stability AI | Laptop-deployable; 7 languages |
| [Falcon 3](#tii-falcon) | TII | 1B–10B | 8K | Text | Apache 2.0 | 14T tokens; includes Mamba variant |

**See also:** [Techniques for Creating SLMs](#techniques-for-creating-slms) | [Deployment Tools](#deployment-tools) | [Contributing](#contributing)

---

## AI2 OLMo

[**AI2 OLMo 2**](https://allenai.org/blog/olmo2) (December 2024)

Models: [1B](https://huggingface.co/allenai/OLMo-2-0425-1B) | [7B-Instruct](https://huggingface.co/allenai/OLMo-2-1124-7B-Instruct) | [13B-Instruct](https://huggingface.co/allenai/OLMo-2-1124-13B-Instruct)

Features:
- Fully open: weights, training data, code, recipes, and intermediate checkpoints
- OLMo 2 7B outperforms LLaMA 3.1 8B; 13B outperforms Qwen 2.5 7B
- Two-stage curriculum pretraining on 3.9T tokens

[Paper](https://arxiv.org/abs/2501.00656)

---

## Alibaba Qwen

[**Alibaba Qwen 3**](https://qwenlm.github.io/blog/qwen3/) (April 2025)

Dense Models: [0.6B](https://huggingface.co/Qwen/Qwen3-0.6B) | [1.7B](https://huggingface.co/Qwen/Qwen3-1.7B) | [4B](https://huggingface.co/Qwen/Qwen3-4B) | [8B](https://huggingface.co/Qwen/Qwen3-8B) | [14B](https://huggingface.co/Qwen/Qwen3-14B)

MoE Models: [30B-A3B](https://huggingface.co/Qwen/Qwen3-30B-A3B)

Features:
- Hybrid thinking modes: fast responses + deep chain-of-thought reasoning
- 119 languages/dialects; trained on 36T tokens; Apache 2.0 license
- MoE variant (30B total, 3B active) for efficient deployment

[Paper](https://arxiv.org/abs/2505.09388)

---

[**Alibaba Qwen 2.5**](https://qwenlm.github.io/blog/qwen2.5/) (September 2024)

Models: [0.5B](https://huggingface.co/Qwen/Qwen2.5-0.5B) | [1.5B](https://huggingface.co/Qwen/Qwen2.5-1.5B) | [3B](https://huggingface.co/Qwen/Qwen2.5-3B) | [7B](https://huggingface.co/Qwen/Qwen2.5-7B) | [14B](https://huggingface.co/Qwen/Qwen2.5-14B)

Features:
- 18T token pretraining; strong on coding, math, and instruction following
- Specialized Coder and Math variants available
- 29 languages; long context up to 128K tokens

[Paper](https://arxiv.org/abs/2412.15115)

---

[**Alibaba Qwen 2**](https://qwenlm.github.io/blog/qwen2/) (June 2024)

Models: [0.5B](https://huggingface.co/Qwen/Qwen2-0.5B) | [1.5B](https://huggingface.co/Qwen/Qwen2-1.5B) | [7B](https://huggingface.co/Qwen/Qwen2-7B)

Features:
- Significant improvements in coding, math, and multilingual tasks
- GQA for efficient KV cache; 128K context for 7B model

[Paper](https://arxiv.org/abs/2407.10671)

---

## Apple

[**Apple OpenELM**](https://machinelearning.apple.com/research/openelm) (April 2024)

Pre-trained Models: [270M](https://huggingface.co/apple/OpenELM-270M) | [450M](https://huggingface.co/apple/OpenELM-450M) | [1.1B](https://huggingface.co/apple/OpenELM-1_1B) | [3B](https://huggingface.co/apple/OpenELM-3B)

Instruction-Tuned Models: [270M-Instruct](https://huggingface.co/apple/OpenELM-270M-Instruct) | [450M-Instruct](https://huggingface.co/apple/OpenELM-450M-Instruct) | [1.1B-Instruct](https://huggingface.co/apple/OpenELM-1_1B-Instruct) | [3B-Instruct](https://huggingface.co/apple/OpenELM-3B-Instruct)

Features:
- Layer-wise scaling strategy for efficient parameter allocation
- Fully open: training data, logs, checkpoints, and configurations released
- MLX support for inference/fine-tuning on Apple devices

[Paper](https://arxiv.org/abs/2404.14619)

---

## Cohere

[**Cohere Command R7B**](https://cohere.com/blog/command-r7b) (December 2024)

Models: [R7B](https://huggingface.co/CohereLabs/c4ai-command-r7b-12-2024)

Features:
- 7B parameter model optimized for RAG, tool use, and agentic workflows
- Multilingual (23 languages); 128K context length
- Strong performance among similar-sized models on HuggingFace Open LLM Leaderboard

---

## DeepSeek

[**DeepSeek-R1 Distilled Models**](https://huggingface.co/deepseek-ai/DeepSeek-R1) (January 2025)

Small Distilled Models: [Qwen-1.5B](https://huggingface.co/deepseek-ai/DeepSeek-R1-Distill-Qwen-1.5B) | [Qwen-7B](https://huggingface.co/deepseek-ai/DeepSeek-R1-Distill-Qwen-7B) | [Llama-8B](https://huggingface.co/deepseek-ai/DeepSeek-R1-Distill-Llama-8B) | [Qwen-14B](https://huggingface.co/deepseek-ai/DeepSeek-R1-Distill-Qwen-14B)

Features:
- Distilled from DeepSeek-R1 using 800K curated reasoning samples
- 8B distilled model matches larger models on MATH-500 and AIME 2024
- Reasoning via reinforcement learning without human-annotated reasoning data

[Paper](https://arxiv.org/abs/2501.12948)

---

## Google Gemma

[**Google Gemma 3**](https://blog.google/technology/developers/gemma-3/) (March 2025)

Pre-trained Models: [1B](https://huggingface.co/google/gemma-3-1b-pt) | [4B](https://huggingface.co/google/gemma-3-4b-pt) | [12B](https://huggingface.co/google/gemma-3-12b-pt)

Instruction-Tuned Models: [1B-IT](https://huggingface.co/google/gemma-3-1b-it) | [4B-IT](https://huggingface.co/google/gemma-3-4b-it) | [12B-IT](https://huggingface.co/google/gemma-3-12b-it)

Features:
- Multimodal (text + image input) with 128K context window
- Supports 140+ languages; knowledge distillation during training
- Gemma 3n variants optimized for mobile/edge devices

[Paper](https://arxiv.org/abs/2503.19786)

---

[**Google Gemma 2**](https://blog.google/technology/developers/google-gemma-2/) (June 2024)

Pre-trained Models: [2B](https://huggingface.co/google/gemma-2-2b) | [9B](https://huggingface.co/google/gemma-2-9b)

Instruction-Tuned Models: [2B-IT](https://huggingface.co/google/gemma-2-2b-it) | [9B-IT](https://huggingface.co/google/gemma-2-9b-it)

Features:
- Interleaved local-global attention and group-query attention
- Smaller models trained via knowledge distillation instead of next-token prediction
- 2B model trained on 2T tokens; 9B model trained on 8T tokens

[Paper](https://arxiv.org/abs/2408.00118)

---

[**Google Gemma**](https://blog.google/technology/developers/gemma-open-models/) (February 2024)

Pre-trained Models: [2B](https://huggingface.co/google/gemma-2b) | [7B](https://huggingface.co/google/gemma-7b)

Instruction-Tuned Models: [2B-IT](https://huggingface.co/google/gemma-2b-it) | [7B-IT](https://huggingface.co/google/gemma-7b-it)

Features:
- Built on research from Gemini; trained on 6T tokens
- Open-source code ([PyTorch](https://github.com/google/gemma_pytorch)) and inference framework ([C++](https://github.com/google/gemma.cpp))

[Paper](./papers/gemma.pdf) | [BibTex](./bibtex/gemma.bib)

---

## HuggingFace SmolLM

[**HuggingFace SmolLM2**](https://huggingface.co/blog/smollm2) (November 2024)

Models: [135M](https://huggingface.co/HuggingFaceTB/SmolLM2-135M) | [360M](https://huggingface.co/HuggingFaceTB/SmolLM2-360M) | [1.7B](https://huggingface.co/HuggingFaceTB/SmolLM2-1.7B) | [1.7B-Instruct](https://huggingface.co/HuggingFaceTB/SmolLM2-1.7B-Instruct)

Features:
- 1.7B model trained on 11T tokens with multi-stage curriculum
- Outperforms Qwen2.5-1.5B and LLaMA 3.2-1B at similar scale
- Apache 2.0 license; designed for on-device deployment

[Paper](https://arxiv.org/abs/2502.02737)

---

## Meta LLaMA

[**Meta LLaMA 3.2**](https://ai.meta.com/blog/llama-3-2-connect-2024-vision-edge-mobile-devices/) (September 2024)

Text Models: [1B](https://huggingface.co/meta-llama/Llama-3.2-1B) | [3B](https://huggingface.co/meta-llama/Llama-3.2-3B) | [1B-Instruct](https://huggingface.co/meta-llama/Llama-3.2-1B-Instruct) | [3B-Instruct](https://huggingface.co/meta-llama/Llama-3.2-3B-Instruct)

Vision Models: [11B-Vision-Instruct](https://huggingface.co/meta-llama/Llama-3.2-11B-Vision-Instruct)

Features:
- First multimodal LLaMA release; 1B/3B text models for edge/mobile
- 128K context length; trained on 9T tokens with knowledge distillation from LLaMA 3.1
- Optimized for on-device with SpinQuant and QLoRA support

[Paper](https://arxiv.org/abs/2407.21783)

---

[**Meta LLaMA 3.1**](https://ai.meta.com/blog/meta-llama-3-1/) (July 2024)

Models: [8B](https://huggingface.co/meta-llama/Llama-3.1-8B) | [8B-Instruct](https://huggingface.co/meta-llama/Llama-3.1-8B-Instruct)

Features:
- 128K context length; multilingual support for 8 languages
- Improved tool use and function calling capabilities

[Paper](https://arxiv.org/abs/2407.21783)

---

[**Meta LLaMA 3**](https://ai.meta.com/blog/meta-llama-3/) (April 2024)

Models: [8B](https://huggingface.co/meta-llama/Meta-Llama-3-8B) | [8B-Instruct](https://huggingface.co/meta-llama/Meta-Llama-3-8B-Instruct)

Features:
- New 128K vocabulary tokenizer (up from 32K in LLaMA 2)
- Grouped-Query Attention (GQA) for improved inference

[Paper](https://arxiv.org/abs/2407.21783)

---

[**Meta LLaMA 2**](https://llama.meta.com/llama2/) (July 2023)

Pre-trained Models: [7B](https://huggingface.co/meta-llama/Llama-2-7b-hf) | [13B](https://huggingface.co/meta-llama/Llama-2-13b-hf)

Chat Models: [7B-Chat](https://huggingface.co/meta-llama/Llama-2-7b-chat-hf) | [13B-Chat](https://huggingface.co/meta-llama/Llama-2-13b-chat-hf)

Features:
- Iterative RLHF for chat alignment; 4K context window
- Trained on 2T tokens; safety-tuned with red-teaming

[Paper](./papers/llama2.pdf) | [BibTex](./bibtex/llama2.bib)

---

[**Meta LLaMA**](https://ai.meta.com/blog/large-language-model-llama-meta-ai/) (February 2023)

Pre-trained Models: [7B](https://huggingface.co/baffo32/decapoda-research-llama-7B-hf)

Features:
- Trained on publicly available data only (1T–1.4T tokens)
- Demonstrated that smaller models trained on more data can match larger models

[Paper](./papers/llama.pdf) | [BibTex](./bibtex/llama.bib)

---

## Microsoft Phi

[**Microsoft Phi-4**](https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/introducing-phi-4-microsoft%E2%80%99s-newest-small-language-model-specializing-in-comple/4357090) (December 2024)

Models: [14B](https://huggingface.co/microsoft/phi-4) | [Mini 3.8B](https://huggingface.co/microsoft/Phi-4-mini-instruct) | [Multimodal 5.6B](https://huggingface.co/microsoft/Phi-4-multimodal-instruct)

Features:
- 14B model surpasses teacher model GPT-4o on STEM QA; trained on 9.8T tokens
- Strategic use of synthetic data throughout training; superior on math competition problems
- Phi-4-mini (3.8B) and Phi-4-multimodal (5.6B, handles text/images/audio) variants

[Paper](https://arxiv.org/abs/2412.08905)

---

[**Microsoft Phi-3.5**](https://azure.microsoft.com/en-us/products/phi) (August 2024)

Models: [Mini 3.8B](https://huggingface.co/microsoft/Phi-3.5-mini-instruct) | [MoE](https://huggingface.co/microsoft/Phi-3.5-MoE-instruct) | [Vision 4.2B](https://huggingface.co/microsoft/Phi-3.5-vision-instruct)

Features:
- Enhanced multilingual, multimodal, and long-context (128K) capabilities
- MoE variant for efficient inference; Vision variant for image understanding
- MIT licensed

[Paper](https://arxiv.org/abs/2404.14219)

---

[**Microsoft Phi-3**](https://news.microsoft.com/source/features/ai/the-phi-3-small-language-models-with-big-potential/) (April 2024)

Models: [Mini 3.8B](https://huggingface.co/microsoft/Phi-3-mini-4k-instruct) | [Small 7B](https://huggingface.co/microsoft/Phi-3-small-8k-instruct) | [Medium 14B](https://huggingface.co/microsoft/Phi-3-medium-4k-instruct)

Features:
- Phi-3-mini (3.8B) outperforms models twice its size
- Data quality over scale philosophy; high-quality curated + synthetic data
- Runs locally on phones

[Paper](https://arxiv.org/abs/2404.14219)

---

## Mistral

[**Mistral Small 3.1**](https://mistral.ai/news/mistral-small-3-1) (March 2025)

Models: [24B-Instruct](https://huggingface.co/mistralai/Mistral-Small-3.1-24B-Instruct-2503) | [24B-Base](https://huggingface.co/mistralai/Mistral-Small-3.1-24B-Base-2503)

Features:
- 24B parameter multimodal model with 128K context; Apache 2.0 license
- Outperforms GPT-4o Mini and Gemma 3; 150 tokens/s inference speed
- Built on Mistral Small 3 with added vision understanding

---

[**Mistral Small 3**](https://mistral.ai/news/mistral-small-3) (January 2025)

Models: [24B-Instruct](https://huggingface.co/mistralai/Mistral-Small-24B-Instruct-2501)

Features:
- 24B parameters competitive with LLaMA 3.3 70B at 3x faster speed
- Fits on single RTX 4090 or 32GB MacBook when quantized
- Apache 2.0 license

---

[**Ministral (les Ministraux)**](https://mistral.ai/news/ministraux/) (October 2024)

Models: [8B-Instruct](https://huggingface.co/mistralai/Ministral-8B-Instruct-2410)

Features:
- Ministral 3B and 8B for on-device and edge use cases
- 128K context support; interleaved sliding-window attention
- Priced at $0.04/M tokens (3B) and $0.1/M tokens (8B)

---

[**Mistral 7B v0.3**](https://mistral.ai/news/announcing-mistral-7b/) (May 2024)

Models: [Base](https://huggingface.co/mistralai/Mistral-7B-v0.3) | [Instruct](https://huggingface.co/mistralai/Mistral-7B-Instruct-v0.3)

Features:
- Extended vocabulary and improved function calling
- Sliding-window attention for efficient long-context inference

[Paper](https://arxiv.org/abs/2310.06825)

---

## RWKV

[**RWKV-7 "Goose"**](https://www.rwkv.com/) (March 2025)

Models: [421M](https://huggingface.co/RWKV/RWKV7-Goose-Pile-421M-HF) | [1.5B](https://huggingface.co/RWKV/RWKV7-Goose-World3-1.5B-HF) | [2.9B](https://huggingface.co/RWKV/RWKV7-Goose-World3-2.9B-HF)

Features:
- RNN architecture with constant memory and constant inference time per token (no KV cache)
- 2.9B model achieves new 3B SOTA on multilingual tasks
- Linear time complexity; infinite context length; Apache 2.0 license

[Paper](https://arxiv.org/abs/2503.14456)

---

## Stability AI

[**Stability AI StableLM 2**](https://stability.ai/news/introducing-stable-lm-2) (January 2024)

Models: [1.6B](https://huggingface.co/stabilityai/stablelm-2-1_6b) | [1.6B-Chat](https://huggingface.co/stabilityai/stablelm-2-1_6b-chat) | [12B](https://huggingface.co/stabilityai/stablelm-2-12b) | [12B-Chat](https://huggingface.co/stabilityai/stablelm-2-12b-chat)

Features:
- 1.6B model trained on 2T tokens across 7 languages
- 12B model trained on 2T tokens with DPO for chat alignment
- Compact enough for laptop deployment

[Paper](https://arxiv.org/abs/2402.17834)

---

## TII Falcon

[**TII Falcon 3**](https://huggingface.co/blog/falcon3) (December 2024)

Models: [1B](https://huggingface.co/tiiuae/Falcon3-1B-Base) | [3B](https://huggingface.co/tiiuae/Falcon3-3B-Base) | [7B](https://huggingface.co/tiiuae/Falcon3-7B-Base) | [7B-Instruct](https://huggingface.co/tiiuae/Falcon3-7B-Instruct) | [10B](https://huggingface.co/tiiuae/Falcon3-10B-Base) | [Mamba-7B](https://huggingface.co/tiiuae/Falcon3-Mamba-7B-Base)

Features:
- Trained on 14T tokens (2x Falcon 2); 1B to 10B parameter range
- Includes SSM-based Mamba variant alongside transformer models
- Compatible with Llama architecture; Apache 2.0-based license

---

[**TII Falcon 2**](https://falconllm.tii.ae/falcon-2.html) (May 2024)

Models: [11B](https://huggingface.co/tiiuae/falcon-11B) | [11B-VLM](https://huggingface.co/tiiuae/falcon-11B-VLM)

Features:
- 11B parameters trained on 5.5T tokens across 11 languages
- First Falcon with vision-language model (VLM) capability
- Deployable on single A10 GPU

[Paper](https://arxiv.org/abs/2407.14885)

---

## Techniques for Creating SLMs

### Knowledge Distillation
Training a smaller "student" model to mimic the behavior of a larger "teacher" model. The student learns from the teacher's output probability distributions rather than just ground-truth labels, capturing richer information about inter-class relationships.
- Used by: DeepSeek-R1 Distill, LLaMA 3.2 (1B/3B distilled from 3.1 70B), Gemma 2/3 smaller variants
- [Distilling the Knowledge in a Neural Network (Hinton et al., 2015)](https://arxiv.org/abs/1503.02531)

### Pruning
Removing redundant or less important parameters (weights, neurons, or entire layers) from a trained model to reduce size while preserving performance.
- **Unstructured pruning**: zeroes out individual weights (sparse matrices)
- **Structured pruning**: removes entire neurons, attention heads, or layers (directly reduces model dimensions)
- [A Survey on Model Compression for Large Language Models](https://arxiv.org/abs/2308.07633)

### Quantization
Reducing the numerical precision of model weights and activations (e.g., FP32 → INT8 or INT4), significantly reducing memory footprint and speeding up inference.
- **Post-Training Quantization (PTQ)**: quantize after training (GPTQ, AWQ, GGUF)
- **Quantization-Aware Training (QAT)**: train with quantization in the loop for better accuracy
- Popular tools: [llama.cpp](https://github.com/ggerganov/llama.cpp), [bitsandbytes](https://github.com/bitsandbytes-foundation/bitsandbytes), [AutoGPTQ](https://github.com/AutoGPTQ/AutoGPTQ)

---

## Deployment Tools

| Tool | Platform | Description | Link |
|---|---|---|---|
| [Ollama](https://ollama.com) | macOS, Linux, Windows | Run SLMs locally with a single command; supports GGUF models | [GitHub](https://github.com/ollama/ollama) |
| [llama.cpp](https://github.com/ggerganov/llama.cpp) | Cross-platform | High-performance C/C++ inference with quantization support | [GitHub](https://github.com/ggerganov/llama.cpp) |
| [vLLM](https://docs.vllm.ai) | Linux, Cloud | High-throughput serving with PagedAttention; production-grade | [GitHub](https://github.com/vllm-project/vllm) |
| [MLC LLM](https://llm.mlc.ai) | Mobile, Web, Desktop | Universal deployment across platforms including iOS/Android/WebGPU | [GitHub](https://github.com/mlc-ai/mlc-llm) |
| [PocketPal AI](https://github.com/a-ghorbani/pocketpal-ai) | iOS, Android | Mobile app for running SLMs on-device | [iOS](https://apps.apple.com/us/app/pocketpal-ai/id6502579498) / [Android](https://play.google.com/store/apps/details?id=com.pocketpalai) |

---

## Contributing

Contributions are welcome! Please open a pull request or issue to add a model, fix a link, or suggest improvements. When adding a new model, please follow the existing format and include:

- Official announcement/blog link
- HuggingFace model links
- 2–3 key features
- Paper link (arXiv preferred)
