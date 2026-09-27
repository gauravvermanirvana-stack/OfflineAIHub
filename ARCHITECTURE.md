# Offline AI Hub Architecture

## Goal

Turn the phone into a small personal AI workstation where different local models are treated as interchangeable engines.

### Core abstraction

`LocalAIEngine`

- `load(model)`
- `generate(prompt)`
- `generateMultimodal(input)`
- `unload()`
- `benchmark()`

### Runtime adapters

1. `LiteRtLmEngine`
   - `.litertlm`
   - CPU/GPU/NPU
2. `LlamaCppEngine` (next)
   - `.gguf`
   - broad open-model support
3. `VisionEngine` (next)
   - image understanding
4. `SpeechEngine` (next)
   - speech recognition / TTS

### Task router

Example:

"Summarize this PDF"
 -> document extractor
 -> local text model
 -> response

"Read this image"
 -> vision model
 -> text model if reasoning is needed

"Draft an email"
 -> writing model
 -> local template

"Find something in my documents"
 -> local embeddings/index
 -> retrieval
 -> reasoning model

## Offline guarantee

The app should provide an "Offline Lock" setting.

When enabled:
- no network permission is required for inference,
- all model files remain local,
- chats and documents remain local,
- the app never silently falls back to cloud AI.

If future cloud connectors are added, they should be visibly separated from the offline engines.
