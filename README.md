# Raman Quiz Challenge

An offline-first Android **MCQ Practice & CBT Exam Preparation** app built with **Kotlin** and **Jetpack Compose (Material 3)**.

---

## Download APK

The latest compiled Android `.apk` is automatically built and published on every push.

1. Open the **[Releases](../../releases)** tab on the right side of this GitHub repository.
2. Download the latest `.apk` file under **Assets**.
3. Install it on your Android device (Android 7.0 / API 24 or higher).

---

## Key Features

- **Practice Mode & Real CBT Exam Mode**
  - **Practice Mode:** Instant answer feedback, sound effects, per-question countdown timer, and wrong-answer review.
  - **Exam Mode:** Full Computer-Based Test (CBT) experience with Question Palette, Mark for Review, customizable positive/negative marking scheme, and detailed scorecard breakdown.
- **AI Quiz Generator (Bring Your Own Key)**
  - Generate customized MCQs from any topic or pasted study notes using Google Gemini (configurable question count, difficulty level, and Hinglish / Hindi / English language styles).
  - **100% Privacy & GitHub Safe:** No API key is bundled inside this repository or APK. On first launch, you can enter your own free Gemini API key from [Google AI Studio](https://aistudio.google.com/), which is stored strictly locally on your device (and excluded from cloud backups).
- **Rich LaTeX Math Rendering**
  - Cleanly renders fractions, roots, superscripts, subscripts, Greek symbols, matrices, and chemical formulas in both quizzes and exported PDFs.
- **Starred / Bookmarked Questions Bank**
  - Bookmark tricky questions during any quiz, practice them as a dedicated bank, or export them to PDF.
- **PDF Question Paper Generator**
  - Export saved quizzes or starred questions into clean, printable A4 PDF question papers with optional answer keys.
- **Offline Quiz Database & Backup**
  - Organize quizzes by category, search saved quizzes, and export/import your entire quiz library (including Starred Questions) as editable `.txt` files.
- **Audio & Accessibility**
  - Built-in Text-to-Speech (TTS) question narration, hardware keyboard shortcuts, and full Light/Dark theme support.

---

## Automated CI/CD (GitHub Actions)

Every push to `main` or `master` (or manual run via **Actions -> Build and Release Android APK -> Run workflow**) automatically:

1. Compiles the Android project using Gradle 9.3.1 & JDK 21 on `ubuntu-latest`.
2. Packages the `.apk` artifact.
3. Creates a tagged GitHub Release (`v1.0.<run_number>`) with the downloadable `.apk` attached.

### Optional: Signed Release APKs

Out of the box, the workflow builds an installable Debug APK with zero extra configuration. To publish signed Release APKs automatically, add these three Repository Secrets under **Settings -> Secrets and variables -> Actions**:

| Secret Name | Description |
| :--- | :--- |
| `RELEASE_KEYSTORE_BASE64` | Base64-encoded `.jks` upload keystore (`base64 -w 0 my-upload-key.jks`) |
| `STORE_PASSWORD` | Keystore password |
| `KEY_PASSWORD` | Key password (for alias `upload`) |

---

## Building Locally

### Prerequisites
- **Android Studio** (supporting AGP 9.1+) or **JDK 21** + **Android SDK** (`compileSdk 36.1`, `minSdk 24`)
- **Gradle 9.3.1**

### Build Command
```bash
# Prepare debug keystore (if not present)
base64 --decode debug.keystore.base64 > debug.keystore

# Compile Debug APK
gradle :app:assembleDebug
```

The output APK will be located at:
`app/build/outputs/apk/debug/app-debug.apk`
