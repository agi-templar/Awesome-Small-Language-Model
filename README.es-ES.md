

# Awesome Small Language Models 👼🏻

[![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

Una lista curada de **Modelos de Lenguaje Pequeños** de código abierto (aproximadamente ≤13B de parámetros, o variantes MoE de parámetros activos pequeños).

> **¿Por qué pequeños?** Los modelos de lenguaje pequeños pueden ejecutarse en GPUs de consumo, dispositivos de borde e incluso teléfonos, lo que hace que la IA sea accesible sin depender de la nube.

## Comparación Rápida

> Última versión de cada familia de modelos. Haz clic en el nombre del modelo para saltar a los detalles.

| Modelo | Organización | Tamaños | Contexto | Modalidad | Licencia | Destacados |
|---|---|---|---|---|---|---|
| [OLMo 2](#ai2-olmo) | AI2 | 1B, 7B, 13B | 4K | Texto | Apache 2.0 | Totalmente abierto (datos + código + recetas) |
| [Qwen 3](#alibaba-qwen) | Alibaba | 0.6B–14B, 30B-A3B | 128K | Texto | Apache 2.0 | Pensamiento híbrido; 119 idiomas; 36T tokens |
| [OpenELM](#apple) | Apple | 270M–3B | 2K | Texto | Apple | Escalado por capas; soporte MLX |
| [Command R7B](#cohere) | Cohere | 7B | 128K | Texto | CC-BY-NC | Optimizado para RAG y uso de herramientas; 23 idiomas |
| [DeepSeek-R1 Distill](#deepseek) | DeepSeek | 1.5B–14B | 128K | Texto | MIT | Razonamiento vía RL; destilado de R1 |
| [Gemma 4](#google-gemma) | Google | E2B, E4B, 26B-A4B, 31B | 128K–256K | Texto + Visión + Audio | Apache 2.0 | MoE + Denso; flujos de trabajo agénticos; 140+ idiomas |
| [SmolLM2](#huggingface-smollm) | HuggingFace | 135M–1.7B | 8K | Texto | Apache 2.0 | Ultra pequeño; supera a Qwen2.5-1.5B a escala similar |
| [LLaMA 3.2](#meta-llama) | Meta | 1B, 3B, 11B | 128K | Texto + Visión | Llama 3.2 | Optimizado para borde/móvil; SpinQuant |
| [Phi-4](#microsoft-phi) | Microsoft | 3.8B, 5.6B, 14B | 16K | Texto + Visión + Audio | MIT | Supera a GPT-4o en preguntas STEM |
| [Mistral Small 3.1](#mistral) | Mistral | 24B | 128K | Texto + Visión | Apache 2.0 | Supera a GPT-4o Mini; 150 tok/s |
| [RWKV-7](#rwkv) | RWKV | 0.4B–2.9B | Ilimitado | Texto | Apache 2.0 | RNN; memoria O(1); sin caché KV |
| [StableLM 2](#stability-ai) | Stability AI | 1.6B, 12B | 4K | Texto | Stability AI | Desplegable en portátil; 7 idiomas |
| [Falcon 3](#tii-falcon) | TII | 1B–10B | 8K | Texto | Apache 2.0 | 14T tokens; incluye variante Mamba |

**Ver también:** [Técnicas para crear SLMs](#tecnicas-para-crear-slms) | [Herramientas de despliegue](#herramientas-de-despliegue) | [Contribuir](#contribuir)

---

## AI2 OLMo

[**AI2 OLMo 2**](https://allenai.org/blog/olmo2) (diciembre de 2024)

Modelos: [1B](https://huggingface.co/allenai/OLMo-2-0425-1B) | [7B-Instruct](https://huggingface.co/allenai/OLMo-2-1124-7B-Instruct) | [13B-Instruct](https://huggingface.co/allenai/OLMo-2-1124-13B-Instruct)

Características:
- Totalmente abierto: pesos, datos de entrenamiento, código, recetas y puntos de control intermedios
- OLMo 2 7B supera a LLaMA 3.1 8B; 13B supera a Qwen 2.5 7B
- Preentrenamiento con currículo de dos etapas en 3.9T de tokens

[Artículo](https://arxiv.org/abs/2501.00656) | [BibTeX](./bibtex/olmo2.bib)

---

## Alibaba Qwen

[**Alibaba Qwen 3**](https://qwenlm.github.io/blog/qwen3/) (abril de 2025)

Modelos Densos: [0.6B](https://huggingface.co/Qwen/Qwen3-0.6B) | [1.7B](https://huggingface.co/Qwen/Qwen3-1.7B) | [4B](https://huggingface.co/Qwen/Qwen3-4B) | [8B](https://huggingface.co/Qwen/Qwen3-8B) | [14B](https://huggingface.co/Qwen/Qwen3-14B)

Modelos MoE: [30B-A3B](https://huggingface.co/Qwen/Qwen3-30B-A3B)

Características:
- Modos de pensamiento híbridos: respuestas rápidas + razonamiento profundo paso a paso (chain-of-thought)
- 119 idiomas/dialectos; entrenado con 36T de tokens; licencia Apache 2.0
- Variante MoE (30B totales, 3B activos) para despliegue eficiente

[Artículo](https://arxiv.org/abs/2505.09388) | [BibTeX](./bibtex/qwen3.bib)

---

[**Alibaba Qwen 2.5**](https://qwenlm.github.io/blog/qwen2.5/) (septiembre de 2024)

Modelos: [0.5B](https://huggingface.co/Qwen/Qwen2.5-0.5B) | [1.5B](https://huggingface.co/Qwen/Qwen2.5-1.5B) | [3B](https://huggingface.co/Qwen/Qwen2.5-3B) | [7B](https://huggingface.co/Qwen/Qwen2.5-7B) | [14B](https://huggingface.co/Qwen/Qwen2.5-14B)

Características:
- Preentrenamiento con 18T de tokens; fuerte en programación, matemáticas y seguimiento de instrucciones
- Variantes especializadas Coder y Math disponibles
- 29 idiomas; contexto largo de hasta 128K tokens

[Artículo](https://arxiv.org/abs/2412.15115) | [BibTeX](./bibtex/qwen2.5.bib)

---

[**Alibaba Qwen 2**](https://qwenlm.github.io/blog/qwen2/) (junio de 2024)

Modelos: [0.5B](https://huggingface.co/Qwen/Qwen2-0.5B) | [1.5B](https://huggingface.co/Qwen/Qwen2-1.5B) | [7B](https://huggingface.co/Qwen/Qwen2-7B)

Características:
- Mejoras significativas en programación, matemáticas y tareas multilingües
- GQA para caché KV eficiente; contexto de 128K para el modelo de 7B

[Artículo](https://arxiv.org/abs/2407.10671) | [BibTeX](./bibtex/qwen2.bib)

---

## Apple

[**Apple OpenELM**](https://machinelearning.apple.com/research/openelm) (abril de 2024)

Modelos Preentrenados: [270M](https://huggingface.co/apple/OpenELM-270M) | [450M](https://huggingface.co/apple/OpenELM-450M) | [1.1B](https://huggingface.co/apple/OpenELM-1_1B) | [3B](https://huggingface.co/apple/OpenELM-3B)

Modelos Ajustados por Instrucciones: [270M-Instruct](https://huggingface.co/apple/OpenELM-270M-Instruct) | [450M-Instruct](https://huggingface.co/apple/OpenELM-450M-Instruct) | [1.1B-Instruct](https://huggingface.co/apple/OpenELM-1_1B-Instruct) | [3B-Instruct](https://huggingface.co/apple/OpenELM-3B-Instruct)

Características:
- Estrategia de escalado por capas para asignación eficiente de parámetros
- Totalmente abierto: se publican datos de entrenamiento, registros, puntos de control y configuraciones
- Soporte MLX para inferencia/ajuste fino en dispositivos Apple

[Artículo](https://arxiv.org/abs/2404.14619) | [BibTeX](./bibtex/openelm.bib)

---

## Cohere

[**Cohere Command R7B**](https://cohere.com/blog/command-r7b) (diciembre de 2024)

Modelos: [R7B](https://huggingface.co/CohereLabs/c4ai-command-r7b-12-2024)

Características:
- Modelo de 7B optimizado para RAG, uso de herramientas y flujos de trabajo agénticos
- Multilingüe (23 idiomas); longitud de contexto de 128K
- Rendimiento destacado entre modelos de tamaño similar en el Open LLM Leaderboard de HuggingFace

---

## DeepSeek

[**DeepSeek-R1 Distilled Models**](https://huggingface.co/deepseek-ai/DeepSeek-R1) (enero de 2025)

Modelos Destilados Pequeños: [Qwen-1.5B](https://huggingface.co/deepseek-ai/DeepSeek-R1-Distill-Qwen-1.5B) | [Qwen-7B](https://huggingface.co/deepseek-ai/DeepSeek-R1-Distill-Qwen-7B) | [Llama-8B](https://huggingface.co/deepseek-ai/DeepSeek-R1-Distill-Llama-8B) | [Qwen-14B](https://huggingface.co/deepseek-ai/DeepSeek-R1-Distill-Qwen-14B)

Características:
- Destilados desde DeepSeek-R1 usando 800K muestras de razonamiento curadas
- El modelo destilado de 8B equipara a modelos más grandes en MATH-500 y AIME 2024
- Razonamiento mediante aprendizaje por refuerzo sin datos de razonamiento anotados por humanos

[Artículo](https://arxiv.org/abs/2501.12948) | [BibTeX](./bibtex/deepseek-r1.bib)

---

## Google Gemma

[**Google Gemma 4**](https://blog.google/innovation-and-ai/technology/developers-tools/gemma-4/) (abril de 2026)

Modelos Preentrenados: [E2B](https://huggingface.co/google/gemma-4-E2B) | [E4B](https://huggingface.co/google/gemma-4-E4B) | [26B-A4B](https://huggingface.co/google/gemma-4-26B-A4B) | [31B](https://huggingface.co/google/gemma-4-31B)

Modelos Ajustados por Instrucciones: [E2B-IT](https://huggingface.co/google/gemma-4-E2B-it) | [E4B-IT](https://huggingface.co/google/gemma-4-E4B-it) | [26B-A4B-IT](https://huggingface.co/google/gemma-4-26B-A4B-it) | [31B-IT](https://huggingface.co/google/gemma-4-31B-it)

Características:
- Arquitecturas densas (E2B/E4B/31B) y MoE (26B totales, 4B activos); licencia Apache 2.0
- Multimodal: entrada texto + imagen + video (31B/26B), texto + imagen + audio (E2B/E4B); contexto de 128K–256K
- Llamadas a funciones nativas, salida JSON estructurada y soporte para flujos de trabajo agénticos; 140+ idiomas

---

[**Google Gemma 3**](https://blog.google/technology/developers/gemma-3/) (marzo de 2025)

Modelos Preentrenados: [1B](https://huggingface.co/google/gemma-3-1b-pt) | [4B](https://huggingface.co/google/gemma-3-4b-pt) | [12B](https://huggingface.co/google/gemma-3-12b-pt)

Modelos Ajustados por Instrucciones: [1B-IT](https://huggingface.co/google/gemma-3-1b-it) | [4B-IT](https://huggingface.co/google/gemma-3-4b-it) | [12B-IT](https://huggingface.co/google/gemma-3-12b-it)

Características:
- Multimodal (entrada texto + imagen) con ventana de contexto de 128K
- Soporta 140+ idiomas; destilación de conocimiento durante el entrenamiento
- Variantes Gemma 3n optimizadas para dispositivos móviles/de borde

[Artículo](https://arxiv.org/abs/2503.19786) | [BibTeX](./bibtex/gemma3.bib)

---

[**Google Gemma 2**](https://blog.google/technology/developers/google-gemma-2/) (junio de 2024)

Modelos Preentrenados: [2B](https://huggingface.co/google/gemma-2-2b) | [9B](https://huggingface.co/google/gemma-2-9b)

Modelos Ajustados por Instrucciones: [2B-IT](https://huggingface.co/google/gemma-2-2b-it) | [9B-IT](https://huggingface.co/google/gemma-2-9b-it)

Características:
- Atención local-global entrelazada y atención por grupo de consultas (GQA)
- Modelos más pequeños entrenados mediante destilación de conocimiento en lugar de predicción de siguiente token
- Modelo de 2B entrenado con 2T de tokens; modelo de 9B entrenado con 8T de tokens

[Artículo](https://arxiv.org/abs/2408.00118) | [BibTeX](./bibtex/gemma2.bib)

---

[**Google Gemma**](https://blog.google/technology/developers/gemma-open-models/) (febrero de 2024)

Modelos Preentrenados: [2B](https://huggingface.co/google/gemma-2b) | [7B](https://huggingface.co/google/gemma-7b)

Modelos Ajustados por Instrucciones: [2B-IT](https://huggingface.co/google/gemma-2b-it) | [7B-IT](https://huggingface.co/google/gemma-7b-it)

Características:
- Construido sobre investigación de Gemini; entrenado con 6T de tokens
- Código de código abierto ([PyTorch](https://github.com/google/gemma_pytorch)) y marco de inferencia ([C++](https://github.com/google/gemma.cpp))

[Artículo](https://arxiv.org/abs/2403.08295) | [BibTeX](./bibtex/gemma.bib)

---

## HuggingFace SmolLM

[**HuggingFace SmolLM2**](https://huggingface.co/blog/smollm2) (noviembre de 2024)

Modelos: [135M](https://huggingface.co/HuggingFaceTB/SmolLM2-135M) | [360M](https://huggingface.co/HuggingFaceTB/SmolLM2-360M) | [1.7B](https://huggingface.co/HuggingFaceTB/SmolLM2-1.7B) | [1.7B-Instruct](https://huggingface.co/HuggingFaceTB/SmolLM2-1.7B-Instruct)

Características:
- Modelo de 1.7B entrenado con 11T de tokens y currículo de múltiples etapas
- Supera a Qwen2.5-1.5B y LLaMA 3.2-1B en escalas similares
- Licencia Apache 2.0; diseñado para despliegue en el dispositivo

[Artículo](https://arxiv.org/abs/2502.02737) | [BibTeX](./bibtex/smollm2.bib)

---

## Meta LLaMA

[**Meta LLaMA 3.2**](https://ai.meta.com/blog/llama-3-2-connect-2024-vision-edge-mobile-devices/) (septiembre de 2024)

Modelos de Texto: [1B](https://huggingface.co/meta-llama/Llama-3.2-1B) | [3B](https://huggingface.co/meta-llama/Llama-3.2-3B) | [1B-Instruct](https://huggingface.co/meta-llama/Llama-3.2-1B-Instruct) | [3B-Instruct](https://huggingface.co/meta-llama/Llama-3.2-3B-Instruct)

Modelos de Visión: [11B-Vision-Instruct](https://huggingface.co/meta-llama/Llama-3.2-11B-Vision-Instruct)

Características:
- Primer lanzamiento multimodal de LLaMA; modelos de texto de 1B/3B para borde/móviles
- Longitud de contexto de 128K; entrenado con 9T de tokens con destilación de conocimiento desde LLaMA 3.1
- Optimizado para ejecución en dispositivo con soporte para SpinQuant y QLoRA

[Artículo](https://arxiv.org/abs/2407.21783) | [BibTeX](./bibtex/llama3.bib)

---

[**Meta LLaMA 3.1**](https://ai.meta.com/blog/meta-llama-3-1/) (julio de 2024)

Modelos: [8B](https://huggingface.co/meta-llama/Llama-3.1-8B) | [8B-Instruct](https://huggingface.co/meta-llama/Llama-3.1-8B-Instruct)

Características:
- Longitud de contexto de 128K; soporte multilingüe para 8 idiomas
- Capacidades mejoradas de uso de herramientas y llamadas a funciones

[Artículo](https://arxiv.org/abs/2407.21783) | [BibTeX](./bibtex/llama3.bib)

---

[**Meta LLaMA 3**](https://ai.meta.com/blog/meta-llama-3/) (abril de 2024)

Modelos: [8B](https://huggingface.co/meta-llama/Meta-Llama-3-8B) | [8B-Instruct](https://huggingface.co/meta-llama/Meta-Llama-3-8B-Instruct)

Características:
- Nuevo tokenizador de vocabulario de 128K (subido de 32K en LLaMA 2)
- Atención por Consulta Agrupada (GQA) para inferencia mejorada

[Artículo](https://arxiv.org/abs/2407.21783) | [BibTeX](./bibtex/llama3.bib)

---

[**Meta LLaMA 2**](https://llama.meta.com/llama2/) (julio de 2023)

Modelos Preentrenados: [7B](https://huggingface.co/meta-llama/Llama-2-7b-hf) | [13B](https://huggingface.co/meta-llama/Llama-2-13b-hf)

Modelos de Chat: [7B-Chat](https://huggingface.co/meta-llama/Llama-2-7b-chat-hf) | [13B-Chat](https://huggingface.co/meta-llama/Llama-2-13b-chat-hf)

Características:
- RLHF iterativo para alineación en chat; ventana de contexto de 4K
- Entrenado con 2T de tokens; ajustado en seguridad con red-teaming

[Artículo](https://arxiv.org/abs/2307.09288) | [BibTeX](./bibtex/llama2.bib)

---

[**Meta LLaMA**](https://ai.meta.com/blog/large-language-model-llama-meta-ai/) (febrero de 2023)

Modelos Preentrenados: [7B](https://huggingface.co/baffo32/decapoda-research-llama-7B-hf)

Características:
- Entrenado únicamente con datos de acceso público (1T–1.4T de tokens)
- Demostró que los modelos más pequeños entrenados con más datos pueden equiparar a los más grandes

[Artículo](https://arxiv.org/abs/2302.13971) | [BibTeX](./bibtex/llama.bib)

---

## Microsoft Phi

[**Microsoft Phi-4**](https://techcommunity.microsoft.com/blog/azure-ai-foundry-blog/introducing-phi-4-microsoft%E2%80%99s-newest-small-language-model-specializing-in-comple/4357090) (diciembre de 2024)

Modelos: [14B](https://huggingface.co/microsoft/phi-4) | [Mini 3.8B](https://huggingface.co/microsoft/Phi-4-mini-instruct) | [Multimodal 5.6B](https://huggingface.co/microsoft/Phi-4-multimodal-instruct)

Características:
- El modelo de 14B supera al modelo maestro GPT-4o en preguntas STEM; entrenado con 9.8T de tokens
- Uso estratégico de datos sintéticos durante todo el entrenamiento; superior en problemas de competencias matemáticas
- Variantes Phi-4-mini (3.8B) y Phi-4-multimodal (5.6B, maneja texto/imágenes/audio)

[Artículo](https://arxiv.org/abs/2412.08905) | [BibTeX](./bibtex/phi4.bib)

---

[**Microsoft Phi-3.5**](https://azure.microsoft.com/en-us/products/phi) (agosto de 2024)

Modelos: [Mini 3.8B](https://huggingface.co/microsoft/Phi-3.5-mini-instruct) | [MoE](https://huggingface.co/microsoft/Phi-3.5-MoE-instruct) | [Vision 4.2B](https://huggingface.co/microsoft/Phi-3.5-vision-instruct)

Características:
- Capacidades mejoradas multilingües, multimodales y de contexto largo (128K)
- Variante MoE para inferencia eficiente; variante Vision para comprensión de imágenes
- Licencia MIT

[Artículo](https://arxiv.org/abs/2404.14219) | [BibTeX](./bibtex/phi3.bib)

---

[**Microsoft Phi-3**](https://news.microsoft.com/source/features/ai/the-phi-3-small-language-models-with-big-potential/) (abril de 2024)

Modelos: [Mini 3.8B](https://huggingface.co/microsoft/Phi-3-mini-4k-instruct) | [Small 7B](https://huggingface.co/microsoft/Phi-3-small-8k-instruct) | [Medium 14B](https://huggingface.co/microsoft/Phi-3-medium-4k-instruct)

Características:
- Phi-3-mini (3.8B) supera a modelos del doble de su tamaño
- Filosofía de calidad de datos por encima de la escala; datos de alta calidad curados y sintéticos
- Se ejecuta localmente en teléfonos

[Artículo](https://arxiv.org/abs/2404.14219) | [BibTeX](./bibtex/phi3.bib)

---

## Mistral

[**Mistral Small 3.1**](https://mistral.ai/news/mistral-small-3-1) (marzo de 2025)

Modelos: [24B-Instruct](https://huggingface.co/mistralai/Mistral-Small-3.1-24B-Instruct-2503) | [24B-Base](https://huggingface.co/mistralai/Mistral-Small-3.1-24B-Base-2503)

Características:
- Modelo multimodal de 24B de parámetros con contexto de 128K; licencia Apache 2.0
- Supera a GPT-4o Mini y Gemma 3; velocidad de inferencia de 150 tokens/s
- Construido sobre Mistral Small 3 con comprensión visual agregada

---

[**Mistral Small 3**](https://mistral.ai/news/mistral-small-3) (enero de 2025)

Modelos: [24B-Instruct](https://huggingface.co/mistralai/Mistral-Small-24B-Instruct-2501)

Características:
- 24B de parámetros competitivos con LLaMA 3.3 70B a 3x más velocidad
- Cabe en una RTX 4090 o un MacBook de 32GB cuando está cuantizado
- Licencia Apache 2.0

---

[**Ministral (les Ministraux)**](https://mistral.ai/news/ministraux/) (octubre de 2024)

Modelos: [8B-Instruct](https://huggingface.co/mistralai/Ministral-8B-Instruct-2410)

Características:
- Ministral 3B y 8B para casos de uso en dispositivo y de borde
- Soporte de contexto 128K; atención por ventana deslizante entrelazada
- Precio de $0.04/M tokens (3B) y $0.1/M tokens (8B)

---

[**Mistral 7B v0.3**](https://mistral.ai/news/announcing-mistral-7b/) (mayo de 2024)

Modelos: [Base](https://huggingface.co/mistralai/Mistral-7B-v0.3) | [Instruct](https://huggingface.co/mistralai/Mistral-7B-Instruct-v0.3)

Características:
- Vocabulario extendido y llamadas a funciones mejoradas
- Atención por ventana deslizante para inferencia eficiente de contexto largo

[Artículo](https://arxiv.org/abs/2310.06825) | [BibTeX](./bibtex/mistral7b.bib)

---

## RWKV

[**RWKV-7 "Goose"**](https://www.rwkv.com/) (marzo de 2025)

Modelos: [421M](https://huggingface.co/RWKV/RWKV7-Goose-Pile-421M-HF) | [1.5B](https://huggingface.co/RWKV/RWKV7-Goose-World3-1.5B-HF) | [2.9B](https://huggingface.co/RWKV/RWKV7-Goose-World3-2.9B-HF)

Características:
- Arquitectura RNN con memoria constante y tiempo de inferencia constante por token (sin caché KV)
- El modelo de 2.9B logra un nuevo SOTA de 3B en tareas multilingües
- Complejidad temporal lineal; longitud de contexto infinita; licencia Apache 2.0

[Artículo](https://arxiv.org/abs/2503.14456) | [BibTeX](./bibtex/rwkv7.bib)

---

## Stability AI

[**Stability AI StableLM 2**](https://stability.ai/news/introducing-stable-lm-2) (enero de 2024)

Modelos: [1.6B](https://huggingface.co/stabilityai/stablelm-2-1_6b) | [1.6B-Chat](https://huggingface.co/stabilityai/stablelm-2-1_6b-chat) | [12B](https://huggingface.co/stabilityai/stablelm-2-12b) | [12B-Chat](https://huggingface.co/stabilityai/stablelm-2-12b-chat)

Características:
- Modelo de 1.6B entrenado con 2T de tokens en 7 idiomas
- Modelo de 12B entrenado con 2T de tokens con DPO para alineación en chat
- Suficientemente compacto para despliegue en portátiles

[Artículo](https://arxiv.org/abs/2402.17834) | [BibTeX](./bibtex/stablelm2.bib)

---

## TII Falcon

[**TII Falcon 3**](https://huggingface.co/blog/falcon3) (diciembre de 2024)

Modelos: [1B](https://huggingface.co/tiiuae/Falcon3-1B-Base) | [3B](https://huggingface.co/tiiuae/Falcon3-3B-Base) | [7B](https://huggingface.co/tiiuae/Falcon3-7B-Base) | [7B-Instruct](https://huggingface.co/tiiuae/Falcon3-7B-Instruct) | [10B](https://huggingface.co/tiiuae/Falcon3-10B-Base) | [Mamba-7B](https://huggingface.co/tiiuae/Falcon3-Mamba-7B-Base)

Características:
- Entrenado con 14T de tokens (2x Falcon 2); rango de 1B a 10B parámetros
- Incluye variante Mamba basada en SSM junto a modelos transformer
- Compatible con la arquitectura Llama; licencia basada en Apache 2.0

---

[**TII Falcon 2**](https://falconllm.tii.ae/falcon-2.html) (mayo de 2024)

Modelos: [11B](https://huggingface.co/tiiuae/falcon-11B) | [11B-VLM](https://huggingface.co/tiiuae/falcon-11B-VLM)

Características:
- 11B de parámetros entrenados con 5.5T de tokens en 11 idiomas
- Primer Falcon con capacidad de modelo de visión-lenguaje (VLM)
- Desplegable en una sola GPU A10

[Artículo](https://arxiv.org/abs/2407.14885) | [BibTeX](./bibtex/falcon2.bib)

---

## Técnicas para crear SLMs

### Destilación de Conocimiento
Entrenar un modelo «estudiante» más pequeño para imitar el comportamiento de un modelo «maestro» más grande. El estudiante aprende de las distribuciones de probabilidad de salida del maestro en lugar de solo de las etiquetas de verdad fundamental, capturando información más rica sobre las relaciones interclase.
- Utilizado por: DeepSeek-R1 Distill, LLaMA 3.2 (1B/3B destilados de 3.1 70B), variantes más pequeñas de Gemma 2/3/4
- [Destilando el conocimiento en una red neuronal (Hinton et al., 2015)](https://arxiv.org/abs/1503.02531)

### Poda
Eliminación de parámetros redundantes o menos importantes (pesos, neuronas o capas completas) de un modelo entrenado para reducir su tamaño mientras se preserva el rendimiento.
- **Poda no estructurada**: anula pesos individuales (matrices dispersas)
- **Poda estructurada**: elimina neuronas completas, cabezas de atención o capas (reduce directamente las dimensiones del modelo)
- [Encuesta sobre compresión de modelos para grandes modelos de lenguaje](https://arxiv.org/abs/2308.07633)

### Cuantización

| [OneComp](https://github.com/FujitsuResearch/OneCompression) | Pipeline PTQ de Fujitsu, probado con Qwen3 0.6B-32B | [arXiv:2603.28845](https://arxiv.org/abs/2603.28845) | Apache-2.0 |
Reducción de la precisión numérica de los pesos y activaciones del modelo (por ejemplo, FP32 → INT8 o INT4), reduciendo significativamente la huella de memoria y acelerando la inferencia.
- **Cuantización posterior al entrenamiento (PTQ)**: cuantizar después del entrenamiento (GPTQ, AWQ, GGUF)
- **Entrenamiento consciente de la cuantización (QAT)**: entrenar con cuantización en el bucle para mayor precisión
- Herramientas populares: [llama.cpp](https://github.com/ggerganov/llama.cpp), [bitsandbytes](https://github.com/bitsandbytes-foundation/bitsandbytes), [AutoGPTQ](https://github.com/AutoGPTQ/AutoGPTQ)

---

## Herramientas de despliegue

| Herramienta | Plataforma | Descripción | Enlace |
|---|---|---|---|
| [Ollama](https://ollama.com) | macOS, Linux, Windows | Ejecuta SLMs localmente con un solo comando; soporta modelos GGUF | [GitHub](https://github.com/ollama/ollama) |
| [llama.cpp](https://github.com/ggerganov/llama.cpp) | Multiplataforma | Inferencia de alto rendimiento en C/C++ con soporte para cuantización | [GitHub](https://github.com/ggerganov/llama.cpp) |
| [vLLM](https://docs.vllm.ai) | Linux, Cloud | Servicio de alto rendimiento con PagedAttention; calidad de producción | [GitHub](https://github.com/vllm-project/vllm) |
| [MLC LLM](https://llm.mlc.ai) | Móvil, Web, Escritorio | Despliegue universal en múltiples plataformas, incluidas iOS/Android/WebGPU | [GitHub](https://github.com/mlc-ai/mlc-llm) |
| [PocketPal AI](https://github.com/a-ghorbani/pocketpal-ai) | iOS, Android | Aplicación móvil para ejecutar SLMs en el dispositivo | [iOS](https://apps.apple.com/us/app/pocketpal-ai/id6502579498) / [Android](https://play.google.com/store/apps/details?id=com.pocketpalai) |

---

## Contribuir

¡Las contribuciones son bienvenidas! Abre un pull request o un issue para agregar un modelo, corregir un enlace o sugerir mejoras. Al agregar un nuevo modelo, por favor sigue el formato existente e incluye:

- Enlace al anuncio/blog oficial
- Enlaces a los modelos en HuggingFace
- 2–3 características clave
- Enlace al artículo (se prefiere arXiv)
