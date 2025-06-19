# UP Adventure Map

Interactive Android app showcasing destinations, activities and multi-day routes across Michigan’s Upper Peninsula.

---

## 1. Project Overview
* **Language**: Kotlin 1.9
* **Minimum Android version**: API 26 (Android 8.0)
* **Target Android version**: API 33
* **Build system**: Gradle Wrapper (`gradlew`) – no local Gradle install needed
* **CI/CD**: GitHub Actions workflow in `.github/workflows/android-build.yml`

## 2. Quick-start (local build & deploy)
### Prerequisites
1. **Android Studio Hedgehog | Flamingo or newer** – installs Android SDK & platform tools automatically.
2. **JDK 17** (bundled with latest Android Studio).
3. A physical Android device or an emulator (API 26+).

### Steps
```bash
# 1. Clone repository
$ git clone https://github.com/<your-account>/UPAdventureMap.git
$ cd UPAdventureMap

# 2. Sync & build from Android Studio (preferred)
#    File ▸ Open… ▸ select `UPAdventureMap` folder ▸ wait for Gradle sync.

# 3. Command-line alternative
$ ./gradlew assembleDebug   # Windows: gradlew.bat assembleDebug

# 4. Install on device (USB debugging enabled)
$ ./gradlew installDebug    # installs app-debug.apk on the first attached device
```
*Generated APK path*: `app/build/outputs/apk/debug/app-debug.apk`

## 3. Virtual Environment (Python optional)
The Android project itself is Kotlin-only.  A *Python* virtual-env is optional and can be useful for tooling (scripts, map data converters, docs generation):
```bash
# create venv (Python ≥3.10 required)
python -m venv .venv
source .venv/Scripts/activate  # Windows PowerShell
pip install -r requirements.txt
```
`requirements.txt` is currently empty – add Python packages as needed (e.g. `pillow`, `shapely`).

## 4. Repository Structure
```
UPAdventureMap/
 ├ app/                 # Android application module
 │  ├ src/main/
 │  │   ├ java/com/uptrip/adventuremap/  # Kotlin sources
 │  │   ├ res/                           # Layouts, drawables, mipmaps
 │  │   └ AndroidManifest.xml
 │  └ build.gradle
 ├ gradle/              # Gradle wrapper
 ├ .github/workflows/   # CI definitions
 ├ README.md            # ← you are here
 └ requirements.txt     # (optional) Python deps
```

## 5. Coding Conventions & Quality
* **Kotlin** – follow official [Kotlin Coding Conventions](https://kotlinlang.org/docs/coding-conventions.html) (equivalent of PEP-8).
* **KDoc** – document public classes & functions.  Use `/** … */` comments.
* **Android resources** – use `snake_case` names, prefer vectors over bitmaps.
* **Git** – 1 feature per branch, descriptive commit messages.  Don’t commit `build/`, `.gradle/`, `local.properties`.
* **Static analysis** – `./gradlew lint` (runs automatically in CI).

## 6. Contributing Workflow
1. Fork / branch from `main`.
2. Implement feature or bugfix.
3. Run `./gradlew lint test assembleDebug` locally.
4. Submit Pull Request – GitHub Actions will run the same checks.
5. At least one reviewer approval required before merge.

## 7. Security & Secrets
* **Do NOT hard-code API keys.** Use `local.properties` or encrypted secrets in CI.
* ProGuard / R8 is enabled in release builds.

## 8. Roadmap
- Integrate Google Maps SDK & KML/GeoJSON overlays.
- Add custom drawable map tiles & icons.
- Implement offline caching of tiles & assets.
- Day-by-day itinerary view with navigation links.

---
Happy adventuring! 🌲🗺️
