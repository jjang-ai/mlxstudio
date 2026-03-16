<p align="center">
  <img src="https://vmlx.net/logos/png/wordmark-transparent-600x150.png" alt="MLX Studio" width="400">
</p>

<h3 align="center">The native macOS desktop app for local AI on Apple Silicon</h3>

<p align="center">
  <a href="https://github.com/jjang-ai/mlxstudio/releases/latest"><img src="https://img.shields.io/github/v/release/jjang-ai/mlxstudio?style=flat-square&label=Latest%20Release&color=blue" alt="Latest Release"></a>
  <a href="https://github.com/jjang-ai/mlxstudio/releases"><img src="https://img.shields.io/github/downloads/jjang-ai/mlxstudio/total?style=flat-square&label=Downloads&color=green" alt="Downloads"></a>
  <img src="https://img.shields.io/badge/Platform-macOS%20ARM64-lightgrey?style=flat-square&logo=apple" alt="Platform">
  <a href="https://pypi.org/project/vmlx/"><img src="https://img.shields.io/pypi/v/vmlx?style=flat-square&label=PyPI&color=%234B8BBE&logo=python&logoColor=white" alt="PyPI"></a>
  <a href="https://github.com/jjang-ai/mlxstudio/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-Apache%202.0-orange?style=flat-square" alt="License"></a>
</p>

<p align="center">
  <a href="#download">Download</a> · <a href="#features">Features</a> · <a href="#api-server">API Server</a> · <a href="#jang-quantization">JANG</a> · <a href="#image-generation">Image Gen</a> · <a href="#build-from-source">Build</a>
</p>

---

MLX Studio is a complete desktop app for running LLMs, VLMs, and image generation models locally on your Mac. No cloud, no API keys, no data leaving your machine. Built on [vMLX Engine](https://github.com/jjang-ai/vmlx) and Apple's [MLX](https://github.com/ml-explore/mlx) framework.

---

## Screenshots

<table>
  <tr>
    <td align="center"><img src="assets/chat-tab.png" width="450"><br><b>Chat with JANG Model</b><br><em>Qwen 3.5 35B MoE at 2.4 bits with thinking mode</em></td>
    <td align="center"><img src="assets/agentic-chat.png" width="450"><br><b>Agentic Coding</b><br><em>Full tool calling with file I/O, shell, and search</em></td>
  </tr>
  <tr>
    <td align="center"><img src="assets/anthropic-api.png" width="450"><br><b>Anthropic API Compatible</b><br><em>Drop-in replacement for Claude — /v1/messages endpoint</em></td>
    <td align="center"><img src="assets/image-tab.png" width="450"><br><b>Image Generation</b><br><em>Flux Schnell, Dev, Z-Image Turbo, Klein models</em></td>
  </tr>
  <tr>
    <td align="center"><img src="assets/tools-tab.png" width="450"><br><b>Developer Tools</b><br><em>Convert models to MLX/JANG, inspect, diagnose</em></td>
    <td align="center"><img src="assets/gguf-to-mlx.png" width="450"><br><b>Model Conversion</b><br><em>GGUF to MLX, JANG mixed-precision quantization</em></td>
  </tr>
  <tr>
    <td align="center"><img src="assets/jangq-models.png" width="450"><br><b>JANGQ-AI Models</b><br><em>Pre-quantized JANG models on HuggingFace</em></td>
    <td align="center"><img src="assets/menu-bar.png" width="300"><br><b>Menu Bar</b><br><em>Quick controls always one click away</em></td>
  </tr>
</table>

---

## Download

> **[Download the latest DMG](https://github.com/jjang-ai/mlxstudio/releases/latest)**

1. Download `vMLX-X.Y.Z-arm64.dmg`
2. Open the DMG, drag to Applications
3. Launch — no Python, no terminal, no config files needed

All releases are signed and notarized for macOS Gatekeeper.

---

## Features

### Chat & Conversation
- Multi-turn streaming conversations with markdown + code highlighting
- **Reasoning mode** — collapsible thinking blocks for Qwen3, DeepSeek-R1, GLM-Z1, Phi-4
- **Image input** — send photos to vision models (Qwen-VL, Pixtral, LLaVA, Gemma 3)
- Per-chat settings: temperature, top-p, top-k, system prompt, max tokens
- Persistent chat history in SQLite

### Tool Calling & Agents
- **13 built-in tool parsers**: qwen, llama, mistral, hermes, deepseek, glm47, minimax, nemotron, granite, functionary, xlam, kimi, step3p5
- File I/O, shell execution, web search, image reading
- MCP (Model Context Protocol) server integration
- Auto-continue agent loops (up to 10 iterations)

### API Server
- **OpenAI compatible**: `/v1/chat/completions`, `/v1/responses`, `/v1/completions`
- **Anthropic compatible**: `/v1/messages` — use as a Claude replacement
- **Image generation**: `/v1/images/generations` — OpenAI format
- Embeddings, reranking, audio (TTS/STT)
- Copy-pasteable code snippets for curl, Python, JavaScript

### Image Generation
- Flux Schnell (4 steps, fast), Dev (20 steps, quality)
- Z-Image Turbo, Flux Klein 4B/9B
- Prompt → image in the app or via API
- Gallery with save, history, and settings

### 5-Layer Caching Engine
- **L1**: Memory-Aware Prefix Cache OR Paged KV Cache
- **L2**: Disk Cache (persistent) OR Block Disk Store
- **KV Quantization**: q4/q8 at storage boundary (2-4x memory savings)
- Hybrid SSM support (Mamba + Attention models)
- Automatic cache type selection based on model architecture

### JANG Quantization
- Adaptive mixed-precision: attention gets more bits, MLP gets fewer
- **2-bit JANG matches 4-bit uniform** on many models
- 73% MMLU on Qwen3.5-122B at 2.4 bits average
- Stays quantized in GPU memory (like GGUF for MLX)
- Convert in-app or via CLI: `vmlx convert model --jang-profile JANG_3M`
- Pre-quantized models: [JANGQ-AI on HuggingFace](https://huggingface.co/JANGQ-AI)

### Model Management
- HuggingFace browser — search, download, install models in-app
- Text/Image model filter in download search
- Model directory scanner with deduplication
- JANG model detection and badge display
- Session start/stop/configure from dashboard

### Desktop Experience
- 5 modes: Chat, Server, Image, Tools, API
- Menu bar tray with live server status
- Dock icon restore on click
- Close-to-tray support
- Multi-session: run multiple models on different ports

---

## System Requirements

| Requirement | Minimum |
|---|---|
| **macOS** | 14.0 Sonoma or later |
| **Chip** | Apple Silicon (M1/M2/M3/M4) |
| **RAM** | 8 GB (16 GB+ recommended) |
| **Disk** | ~500 MB for app; models 1-50 GB each |

---

## Also Available via pip

```bash
pip install vmlx
vmlx serve mlx-community/Qwen3-8B-4bit
```

The CLI gives you the same engine without the GUI. See [vMLX on PyPI](https://pypi.org/project/vmlx/).

---

## Build from Source

```bash
git clone https://github.com/jjang-ai/vmlx.git
cd vmlx

# Python engine
python3 -m venv .venv && source .venv/bin/activate
pip install -e ".[dev]"

# Electron app
cd panel && npm install && npm run build
npx electron-builder --mac --dir   # .app
npx electron-builder --mac dmg     # DMG
```

---

## Links

| Resource | Link |
|---|---|
| **Source Code** | [github.com/jjang-ai/vmlx](https://github.com/jjang-ai/vmlx) |
| **PyPI** | [pypi.org/project/vmlx](https://pypi.org/project/vmlx/) |
| **JANG Models** | [huggingface.co/JANGQ-AI](https://huggingface.co/JANGQ-AI) |
| **Website** | [vmlx.net](https://vmlx.net) |

---

## License

Apache License 2.0

---

<p align="center">
  Built by <a href="https://github.com/jjang-ai">Jinho Jang</a> · <a href="mailto:eric@jangq.ai">eric@jangq.ai</a> · <a href="https://github.com/jjang-ai">JANGQ AI</a>
</p>
