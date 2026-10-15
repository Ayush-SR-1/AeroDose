# AeroDose 🎛️🔥

**Measure. Monitor. Understand. Control.**

AeroDose is an intelligent gas-cylinder monitoring and safety valve dashboard engineered for safer homes and smart industrial environments. It supports live telemetry via ESP32 polling, full local simulation, central safety gate interlocking, and dual editions (Home LPG and Pro CO₂).

🌐 **Live Website:** [https://ayush-sr-1.github.io/AeroDose/](https://ayush-sr-1.github.io/AeroDose/)

---

## 🌟 Key Features

- **Centralized Safety Interlock (`gate()`):**
  - Instant auto-closure upon leak detection (gas sensor ≥ 1000 PPM) or motor stall (> 2.1 A).
  - Safety re-arm checklist with 10-second dwell sensor stabilization.
  - Automatic shutoff when reserve reaches critical threshold (≤ 2%).
- **Dual Operating Modes:**
  - **Live Hardware (ESP32):** Real-time sensor polling, authoritative reported states, and command dispatch with acknowledgement.
  - **Simulator Mode:** Full realistic consumption and sensor dynamics with decay logic.
- **Home & Pro Editions:**
  - **Home Edition:** 14.2 kg LPG profile, daily consumption analytics, weekly comparisons, and refill forecasting.
  - **Pro Edition:** 22 kg CO₂ profile, mass-quota dosing with automatic valve shutoff.
- **Cross-Platform:**
  - Single-file standalone web dashboard (`index.html` / `AeroDose-Safe-Dashboard.html`).
  - Mobile application built with **Capacitor** for Android.

---

## 📁 Repository Structure

```text
├── index.html                    # Root entry point (hosted on GitHub Pages)
├── AeroDose-Safe-Dashboard.html  # Standalone single-file dashboard
├── www/
│   └── index.html               # Web app source for Capacitor
├── android/                     # Native Android Studio Capacitor project
├── capacitor.config.json        # Capacitor configuration
├── package.json                 # Project dependencies & scripts
└── README.md                    # Project documentation
```

---

## 🚀 Getting Started

### 1. Web Dashboard
- **Live Online:** [https://ayush-sr-1.github.io/AeroDose/](https://ayush-sr-1.github.io/AeroDose/)
- **Local:** Simply open `index.html` or `AeroDose-Safe-Dashboard.html` in any modern web browser. No web server or external dependencies required.

### 2. Android App (Capacitor)
To build or develop the Android app:

```bash
# Install dependencies
npm install

# Sync web assets to native Android project
npx cap sync

# Open in Android Studio
npx cap open android
```

To build the APK from the command line:
```bash
cd android
./gradlew assembleDebug
```
The output APK will be generated at:
`android/app/build/outputs/apk/debug/app-debug.apk`

---

## 🔒 Safety Architecture
- Valve operations adhere to strict multi-tab authoritative closing (`mergeRemote`).
- Commands are tri-state (`OPEN`, `CLOSED`, `UNKNOWN`) to prevent ghost activations.
- Uses Web Locks API with fallback heartbeat leader election to synchronize across multiple tabs.

---

## 📄 License
MIT License.
