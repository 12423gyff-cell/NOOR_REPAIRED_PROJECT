# Noor — Contextual Quran Intelligence

This repository contains the Android source project exported from Google AI Studio and repaired for deterministic GitHub Actions builds.

## Build in GitHub Actions

Push this project to a GitHub repository. The workflow at `.github/workflows/build-debug.yml` will:

1. Use JDK 17.
2. Install Android SDK 36 and Build Tools 36.0.0.
3. Install Gradle 9.7.0 directly.
4. Build `:app:assembleDebug`.
5. Upload `app-debug.apk` as the `noor-debug-apk` artifact.

This repaired project intentionally does **not** ship the corrupted Gradle Wrapper JAR from the AI Studio export. CI uses a pinned Gradle 9.7.0 distribution through `gradle/actions/setup-gradle`.

## Local build

Open the folder in Android Studio. Make sure the project uses JDK 17 and Gradle 9.7.0. If Android Studio asks you to select a Gradle distribution, use the local Gradle 9.7.0 installation or the configured Gradle toolchain.

The debug build uses the normal Android Gradle Plugin managed debug keystore; no `debug.keystore` file is required in the repository.

## Secrets

The app can read `GEMINI_API_KEY` from `.env` when Gemini-backed functionality is enabled. Do not commit real secrets.

## Dataset integrity

`app/src/main/res/raw/quran_full.json` is validated as a complete 6,236-ayah JSON array. The original export was truncated at Surah 26, Ayah 211; the missing tail was reconstructed from a complete Uthmani source available in the build environment, while the intact exported rows were preserved.
