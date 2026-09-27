# Offline AI Hub — Phone-Only Build

You can build the APK without Android Studio by using GitHub Actions from your Android phone.

## 1. Create a GitHub repository

Open GitHub in your phone browser and create a new repository named:

OfflineAIHub

For privacy, choose **Private**.

## 2. Extract this ZIP

Extract `OfflineAIHub_PhoneBuild.zip` on your phone.

The repository root must contain:

- `.github/workflows/build-apk.yml`
- `app/`
- `build.gradle.kts`
- `settings.gradle.kts`
- `gradle.properties`

Do not upload the ZIP as the only repository file.

## 3. Upload the extracted files

In GitHub:

**Add file → Upload files**

Select the extracted files and folders, then commit them to `main`.

## 4. Start the build

Open:

**Actions → Build Offline AI Hub APK**

The workflow should run automatically after a push.

You can also open the workflow and select:

**Run workflow**

## 5. Get the APK

After the workflow finishes with a green check:

**Actions → Build Offline AI Hub APK → completed run → Artifacts**

Download:

**OfflineAIHub-debug**

Inside it is:

`app-debug.apk`

Tap the APK on your phone to install it.

Android may ask for permission to install apps from your browser/file manager. Only allow it for a source you trust.

## If the build fails

Open the failed GitHub Actions run and copy the final error section. Send it to me and I can patch the project.

## Important

The GitHub build machine needs internet access to download Android/Gradle dependencies. That is only the build process.

The AI application itself is designed so that local model inference can run without internet after the app and model are installed.

## Next version

After the APK builds successfully, the next upgrade should add:

- GGUF / llama.cpp models
- automatic model selection
- model benchmarking
- vision/image models
- OCR
- speech-to-text
- text-to-speech
- local PDF/document search
- RAG/local knowledge base
- personal AI agent
- Offline Lock
