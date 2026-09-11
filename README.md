# KabadiConnect 🌏♻️

> **Smart India Hackathon 2026** | Problem Statement: E-Waste Management for Informal Collectors

An offline-first, low-literacy, vernacular Android app connecting informal e-waste scrap collectors to authorized recyclers in India.

---

## 🚀 Quick Start

### Prerequisites

| Tool | Version |
|------|----------|
| Flutter SDK | 3.19+ |
| Dart | 3.3+ |
| Android SDK | API 21+ |
| Android device or emulator | |

### Steps to Run

```bash
# 1. Clone / unzip the project
cd kabadiconnect

# 2. Install dependencies
flutter pub get

# 3. Generate Hive type adapters
flutter pub run build_runner build --delete-conflicting-outputs

# 4. Run on device
flutter run

# 5. Build APK for demo
flutter build apk --release --target-platform android-arm64
# APK will be at: build/app/outputs/flutter-apk/app-release.apk
```

---

## 📁 Project Structure

```
kabadiconnect/
├── lib/
│   ├── main.dart                    # App entry point, Hive + localization init
│   ├── theme.dart                   # Material 3 high-contrast theme
│   ├── models/
│   │   ├── material_lot.dart         # Hive model: e-waste lot
│   │   ├── price_record.dart         # Hive model: price per category
│   │   ├── recycler.dart             # Hive model: authorized recycler
│   │   ├── transaction.dart          # Hive model: handover transaction
│   │   └── collector_profile.dart    # Hive model: user profile
│   ├── services/
│   │   ├── database_service.dart     # All Hive CRUD operations
│   │   └── seed_data.dart            # First-launch seed data
│   └── screens/
│       ├── language_selection_screen.dart
│       ├── onboarding_screen.dart
│       ├── main_nav_screen.dart      # Bottom nav shell
│       ├── home_screen.dart          # Price board
│       ├── create_lot_screen.dart    # Camera + category + weight
│       ├── recyclers_screen.dart     # Nearby recyclers list
│       ├── handover_screen.dart      # QR + photo + confirm
│       ├── earnings_screen.dart      # Ledger
│       └── safety_tips_screen.dart   # Audio safety cards
├── assets/
│   └── translations/
│       ├── hi.json                   # Hindi translations
│       └── mr.json                   # Marathi translations
├── android/app/src/main/
│   └── AndroidManifest.xml         # Camera, GPS, storage permissions
└── pubspec.yaml
```

---

## 📱 Key Features

### 1. 🌐 Language Selection
- First screen on fresh install
- Big buttons for Hindi / Marathi
- Preference saved offline (Hive)

### 2. 📊 Price Board (Home)
- Real-time display of prices per kg for all e-waste categories
- **TTS "Speak" button** — reads all prices aloud in Hindi/Marathi
- Last updated timestamp

### 3. 📦 Create Lot
- Camera capture with big tap target
- 8 category icons (PCB, Cable, Battery, CRT, LCD, Motor, Plastic, Other)
- Weight entry with large number pad
- Instant estimated value display
- Saves with unique ID: `KBC-YYYYMMDD-NNN` + GPS + timestamp

### 4. 📍 Nearby Recyclers
- Sorted by distance (mock GPS in prototype)
- Authorization badge (CPCB)
- Rate per kg, materials accepted, pickup availability
- One-tap to initiate handover

### 5. ✨ Digital Handover
- Step-by-step wizard (Select lot → Confirm → QR → Done)
- Unique reference code generated
- QR code display for recycler scanning
- Optional photo capture
- Transaction saved as "Pending"

### 6. 💰 Earnings Ledger
- Total earned + pending amounts
- Transaction history with status badges
- Swipe-to-refresh

### 7. 🛡️ Safety Tips
- 7 pictorial cards with high-contrast icons
- Audio playback per card (Hindi TTS)
- Topics: no burning cables, battery safety, CRT danger, gloves, masks, water pollution, authorized recycling

---

## 🎤 SIH Demo Script (5 minutes)

| Step | Screen | What to show |
|------|--------|--------------|
| 1 | Language | Select Hindi. App remembers it. |
| 2 | Onboarding | 3 quick slides. One tap “Start”. |
| 3 | Price Board | Show today’s prices. Tap “सुनें” — TTS reads prices aloud. |
| 4 | Create Lot | Take photo of any device/wire. Select “Cable”. Enter 2 kg. Show ₹70 value estimate. Save. |
| 5 | Recyclers | Show ranked list. CPCB badge. Pickup available. Tap “Handover”. |
| 6 | Handover | Step through wizard. Show QR code. Confirm. Success screen. |
| 7 | Earnings | Show ₹70 pending. Total earned amount. |
| 8 | Safety | Tap a card — audio plays in Hindi. |

**Key demo talking points:**
- “Works 100% offline — no internet needed”
- “Designed for users who cannot read well — icons + audio”
- “CPCB authorized recyclers only — fair prices, documented”
- “Digital trail prevents fraud and underpayment”

---

## 📦 Packages Used

| Package | Purpose |
|---------|---------|
| `hive` + `hive_flutter` | Offline database |
| `hive_generator` + `build_runner` | Code generation |
| `easy_localization` | Hindi / Marathi translations |
| `flutter_tts` | Text-to-Speech |
| `image_picker` | Camera capture |
| `geolocator` | GPS location |
| `qr_flutter` | QR code generation |
| `uuid` | Unique lot / transaction IDs |
| `path_provider` | File storage paths |

All packages are **free and open source**. No paid APIs.

---

## ⚠️ Troubleshooting

**`part` file errors**: Run `flutter pub run build_runner build --delete-conflicting-outputs`

**Camera permission denied on device**: Make sure `AndroidManifest.xml` is in place and run on a real device, not emulator, for camera.

**TTS not speaking**: Install a Hindi language pack on the Android device via Settings → Language & Input → Text-to-Speech.

---

## 👥 Team

Built for **Smart India Hackathon 2026** — Problem: E-Waste Collection & Management

---

*KabadiConnect — Connecting India’s informal recyclers to the formal economy, one lot at a time.*
