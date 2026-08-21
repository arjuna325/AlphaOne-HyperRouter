# AlphaOne HyperRouter

**Multi-Provider AI Gateway for IDEs, Coding Agents & Local AI**

AlphaOne HyperRouter is a Windows-native AI gateway that connects compatible IDEs, coding assistants, CLIs, and agent harnesses to multiple cloud AI providers and Local GGUF models through a single local endpoint.

It provides unified **OpenAI Chat Completions**, **OpenAI Responses API**, and **Ollama-compatible** interfaces with automatic provider routing and failover.

> **Official public distribution repository for AlphaOne HyperRouter binaries and release notes.**
> The HyperRouter source code is proprietary and is not distributed through this repository.

---

## Download

### Latest Release

Download the latest official Windows release from:

[**Download AlphaOne HyperRouter**](https://github.com/arjuna325/AlphaOne-HyperRouter/releases/latest)

All published versions are available on the:

[**Releases Page**](https://github.com/arjuna325/AlphaOne-HyperRouter/releases)

Each release includes its own version notes and downloadable binary package.

---

## What is AlphaOne HyperRouter?

HyperRouter runs locally on Windows and provides one endpoint between your AI client and multiple AI providers.

```text
IDE / Coding Agent / CLI
          │
          │ OpenAI / Responses / Ollama Protocol
          ▼
   AlphaOne HyperRouter
          │
          ├── Local GGUF AI
          ├── OpenAI
          ├── Anthropic
          ├── Google Gemini
          ├── DeepSeek
          ├── Qwen
          ├── Kimi AI
          ├── Agnes AI
          └── Groq
```

Instead of configuring a separate provider connection in every compatible client, HyperRouter provides a stable local gateway and manages provider selection centrally.

---

## Key Features

### Multi-Provider AI Routing

Connect multiple supported cloud providers using your own API keys and manage them from one local HyperRouter installation.

Supported provider integrations include:

* OpenAI
* Anthropic
* Google Gemini
* DeepSeek
* Qwen
* Kimi AI
* Agnes AI
* Groq

### Auto RollOver

When an eligible provider or model encounters supported quota, rate-limit, or availability failures, HyperRouter can automatically continue routing through the next configured provider or cascade tier.

### Local GGUF AI

Run compatible `.gguf` models locally without requiring a cloud API.

HyperRouter supports local execution using available:

* NVIDIA CUDA acceleration
* Vulkan acceleration
* CPU fallback

Local AI remains optional and is managed separately from cloud provider routing.

### OpenAI-Compatible Gateway

Default OpenAI-compatible endpoint:

```text
http://127.0.0.1:11436/v1
```

Primary Chat Completions endpoint:

```text
POST /v1/chat/completions
```

OpenAI Responses API endpoint:

```text
POST /v1/responses
```

### Ollama-Compatible Gateway

For compatible clients using the Ollama protocol:

```text
http://127.0.0.1:11436
```

Supported compatibility routes include:

```text
/api/chat
/api/generate
/api/tags
```

### Agentic Continuity

HyperRouter maintains canonical conversation and tool-call history so compatible agent workflows can preserve task context across supported provider transitions.

Provider-native state is used where appropriate while canonical history remains the portability layer across providers.

### Lossless Token Saver

Optional conservative context optimization reduces unnecessary formatting overhead for supported cloud requests while prioritizing content integrity.

The feature can be disabled at any time if unusual tool behavior occurs.

### Token & Quota Diagnostics

HyperRouter provides local telemetry for:

* Input tokens
* Cached input tokens
* Output tokens
* Reasoning / thought tokens
* Tool-use tokens
* Total tokens
* Request latency
* Time to first token
* Provider and model
* HTTP status
* RPM / TPM / RPD quota classification

### Local Credential Protection

Provider API keys are managed locally by HyperRouter.

On supported Windows installations, provider credentials are protected at rest using Windows DPAPI under the current Windows user profile.

Existing provider credentials are not rendered back into the Settings page.

---

## Supported Clients

HyperRouter is designed for clients that support OpenAI-compatible, Responses API, or Ollama-compatible endpoints.

Validated integration patterns include:

* Visual Studio Code
* Visual Studio
* OpenAI Codex CLI
* OpenAI Codex IDE Extension
* Cline
* Roo Code
* Cursor
* Continue.dev
* Android Studio
* Compatible agent SDKs and harnesses

The IDE or coding client remains responsible for filesystem access, terminal execution, editing, approvals, and other local agent actions.

HyperRouter provides the AI routing, protocol translation, provider access, and continuity backend.

---

## Quick Start

### 1. Download HyperRouter

Go to:

[**Latest Release**](https://github.com/arjuna325/AlphaOne-HyperRouter/releases/latest)

Download the Windows package and extract it if required.

### 2. Start HyperRouter

Run:

```text
AlphaOne.AI.Bridge.exe
```

The default local server address is:

```text
http://127.0.0.1:11436
```

### 3. Open Settings

Open:

```text
http://127.0.0.1:11436/setting
```

Configure at least one cloud provider API key or enable a compatible Local GGUF model.

### 4. Configure Your AI Client

For OpenAI-compatible clients:

```text
Base URL : http://127.0.0.1:11436/v1
API Key  : sk-alphaone
Model ID : alphaone-hyperrouter
```

The API key shown above is only a placeholder for clients that require a non-empty credential field.

Actual upstream provider credentials remain configured inside HyperRouter.

For Ollama-compatible clients:

```text
Base URL : http://127.0.0.1:11436
Model    : alphaone-hyperrouter
```

---

## HyperRouter Model Profile

Compatible clients can use one stable public model ID:

```text
alphaone-hyperrouter
```

The actual provider model class is selected centrally from the HyperRouter Settings dashboard.

Available profiles:

| Profile    | Purpose                                                |
| ---------- | ------------------------------------------------------ |
| **High**   | Maximum-capability provider model class                |
| **Medium** | Balanced capability and efficiency                     |
| **Low**    | Faster / efficiency-oriented model class               |
| **Custom** | Uses individually configured provider model selections |

Provider priority and model profile are independent.

The selected provider order determines **where** HyperRouter routes the request, while the model profile determines **which model class** is selected for that provider.

---

## Release History

Every public release is published manually through GitHub Releases.

Release pages contain:

* Version number
* Release date
* Change summary
* Bug fixes
* Compatibility changes
* New features
* Downloadable Windows binary/package

See:

[**All Releases**](https://github.com/arjuna325/AlphaOne-HyperRouter/releases)

Older versions remain available for reference and rollback where applicable.

---

## Security

HyperRouter is designed primarily as a local single-user Windows gateway.

Default configuration:

```text
Address : 127.0.0.1
Port    : 11436
```

HyperRouter includes local browser-origin restrictions and network binding controls intended to prevent unintended remote access under the default configuration.

Users remain responsible for:

* Protecting their provider API credentials
* Downloading HyperRouter only from official AlphaOne AI distribution channels
* Keeping Windows and provider credentials secure
* Reviewing release notes before upgrading production environments

---

## System Requirements

* Windows
* Network access for cloud AI providers
* Provider API key(s) for cloud AI usage
* Optional compatible `.gguf` model for Local AI
* Compatible IDE, coding assistant, CLI, or API client

Actual Local AI performance depends on model size, available RAM, GPU VRAM, and hardware acceleration support.

---

## Official Website

**AlphaOne AI**

https://alphaone-ai.com

HyperRouter product information:

https://alphaone-ai.com/hyperrouter.html

---

## Support

For HyperRouter questions, beta testing, compatibility reports, or release-related issues:

**[support@alphaone-ai.com](mailto:support@alphaone-ai.com)**

When reporting an issue, please include where applicable:

* HyperRouter version
* Client / IDE name
* Protocol used
* Provider involved
* HTTP status code
* Relevant HyperRouter log information

Do **not** include API keys or other credentials in public GitHub issues.

---

## Binary Distribution Notice

This repository is intended for:

* Official AlphaOne HyperRouter release announcements
* Version history
* Release notes
* Documentation
* Public binary downloads

It is **not** the HyperRouter source-code repository.

Executable files published under the official **Releases** section are the intended public distribution artifacts.

---

## License & Intellectual Property

AlphaOne HyperRouter is proprietary software.

Copyright © 2026 AlphaOne AI. All rights reserved.

The availability of downloadable binaries through this repository does **not** grant permission to reproduce, redistribute, reverse engineer, modify, sublicense, or commercially exploit the software except where expressly authorized by AlphaOne AI.

Third-party product names, trademarks, APIs, and services referenced by HyperRouter remain the property of their respective owners.

AlphaOne AI is an independent third-party software provider and is not affiliated with, endorsed by, or sponsored by OpenAI, Anthropic, Alibaba Cloud, Moonshot AI, Google, Agnes AI, Groq, or other referenced AI providers.

---

**One Router. Multiple Providers. Local + Cloud AI.**

