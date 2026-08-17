# Noor repair notes

- Replaced the corrupted/truncated `quran_full.json` with a valid 6,236-ayah JSON dataset.
- Removed the invalid Gradle wrapper JAR and wrapper launchers; GitHub Actions now installs pinned Gradle 9.7.0 directly.
- Removed the custom debug keystore requirement so CI can use the Android Gradle Plugin managed debug signing key.
- Replaced `AppCompatButton` in the overlay XML with the platform `Button` to match the existing service cast and avoid an undeclared AppCompat dependency.
- Pinned Android compile SDK to API 36 for hosted-runner compatibility.
- Aligned Java source/target compatibility to JDK 17.
- Added a GitHub Actions build workflow using current Node 24-based action versions.
- Added `tools/verify_project.py` for static dataset/build-configuration validation.
