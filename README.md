# Offline AI Hub for Android

A starter Android application for running multiple local AI models from one private mobile hub.

## What this first version does

- Imports local `.litertlm` models.
- Keeps model files in the app's private storage.
- Lets you switch between installed models.
- Runs inference on-device through Google's LiteRT-LM Kotlin API.
- Starts with CPU inference for maximum compatibility.
- Is designed so GPU/NPU backends and other runtimes can be added later.
- No cloud API key is required for inference after the model is on the phone.

Google documents LiteRT-LM's Android Kotlin API and CPU/GPU/NPU backends here:
https://github.com/google-ai-edge/LiteRT-LM

## Build

Open this folder in the latest Android Studio.

1. Let Gradle sync.
2. Connect an Android phone with USB debugging enabled.
3. Build > Make Project.
4. Run the app.

The first build needs internet access to download Gradle and Maven dependencies.
After the application and models are installed, inference itself is designed to work offline.

## Model

Use a LiteRT-LM compatible `.litertlm` model. A small model is recommended for phones.

For a practical first device configuration:
- 1B–4B parameter model
- quantized model where available
- 4K context initially
- CPU first; GPU/NPU can be enabled after device testing

Do not copy a huge desktop model to the phone blindly: RAM usage, thermal limits and storage speed matter.

## Planned architecture

Offline AI Hub
├── Model Manager
│   ├── LiteRT-LM models
│   ├── Future GGUF/llama.cpp adapter
│   └── Model metadata/benchmarks
├── Task Router
│   ├── Writing
│   ├── Document analysis
│   ├── Coding
│   ├── OCR/vision
│   └── Speech
├── Local Agent
│   ├── Prompt templates
│   ├── Tool/function calls
│   └── Android actions
└── Privacy Layer
    ├── Offline-only mode
    ├── Local chat history
    └── No telemetry by default

## Important

This starter is the foundation, not yet a complete "AI operating system". The next engineering stage is to add:
1. multiple model runtimes,
2. image/vision models,
3. OCR,
4. speech-to-text and text-to-speech,
5. a task router/agent,
6. local document/RAG search,
7. optional Android automation with explicit user permissions,
8. model benchmarking and automatic model selection.


## Phone-only build
See `PHONE_BUILD_GUIDE.md`. GitHub Actions is configured in `.github/workflows/build-apk.yml` to build and upload the debug APK as an artifact.
