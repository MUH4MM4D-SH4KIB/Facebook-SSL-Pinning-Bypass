# Facebook SSL Pinning Bypass for Android (2026) – Intercept & Capture HTTPS Traffic

[![Telegram](https://img.shields.io/badge/💬_Chat_on_Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white&labelColor=121212&color=26A5E4&logoWidth=20)](https://t.me/MUH4MM4DSH4KIB)
![Android](https://img.shields.io/badge/Android-3DDC84?style=for-the-badge&logo=android&logoColor=white)
![ARM64](https://img.shields.io/badge/ARM64--v8a-Supported-blue?style=for-the-badge)
![x86_64](https://img.shields.io/badge/x86__64-Supported-blue?style=for-the-badge)
![Last Updated](https://img.shields.io/badge/Updated-March_2026-brightgreen?style=for-the-badge)

> Bypass Facebook's native SSL/TLS certificate pinning on Android by patching `libcoldstart.so` — intercept, inspect, and analyze HTTPS network traffic on both **rooted** and **non-rooted** devices. Working as of **2026**.

---

## 📖 Overview


This project provides a **pre-patched `libcoldstart.so`** with the certificate verification logic disabled at the binary level, enabling security researchers, penetration testers, and developers to:

- **Capture and inspect** all Facebook HTTPS requests and responses in real time
- **Analyze API endpoints**, request parameters, headers, and authentication flows
- **Audit data transmission** for privacy and security research
- **Debug and test** integrations that interact with Facebook's mobile API


---

## 🎥 Proof of Concept

<img width="720" height="1640" alt="Facebook SSL Pinning Bypass PoC — HTTPS traffic captured via MITM proxy after patching libcoldstart.so" src="https://github.com/user-attachments/assets/a6413e59-0caf-40cc-ba6c-e0d9d66a2c36" />

▶️ [**Watch the Full Video Demonstration**](https://github.com/user-attachments/assets/1a30bf22-86b8-4e4b-9254-034178de654a)

---

## 📋 Supported Facebook Version

| App | Version | Patched Library | Architecture | Status |
|-----|---------|-----------------|--------------|--------|
| Facebook for Android | **551.1.0.58.63** | `libcoldstart.so` | `arm64-v8a` | ✅ Bypassed |
| Facebook for Android | **551.1.0.58.63** | `libcoldstart.so` | `x86_64` | ✅ Bypassed |

> **Need a newer version?** Facebook updates frequently. For the **latest patched `libcoldstart.so`** compatible with the current Facebook version, [contact me on Telegram](https://t.me/MUH4MM4DSH4KIB).

---

## ⚙️ Supported Architectures

| Architecture | Device Type | Support |
|---|---|---|
| `arm64-v8a` | Physical Android devices, ARM-based emulators | ✅ |
| `x86_64` | PC-based Android emulators (Nox, LDPlayer, etc.) | ✅ |

---

## 📱 Requirements

### Option A: Physical Android Device (Rooted or Non-Rooted)

- Android phone or tablet running a compatible Facebook version
- ADB access (USB debugging enabled, or wireless ADB)
- A traffic interception proxy:
  - [**Reqable**](https://reqable.com) — modern UI, excellent mobile support
  - [**Proxypin**](https://proxypin.com) — free, lightweight, no-root option

### Option B: Android Emulator (PC)

- Windows/macOS/Linux PC with an Android emulator:
  - [**Nox Player**](https://www.bignox.com/) — enable root access in settings
  - [**LDPlayer**](https://www.ldplayer.net/) — enable root access in settings
- A MITM proxy tool:
  - [**Burp Suite**](https://portswigger.net/burp) — industry-standard web security testing
  - [**mitmproxy**](https://mitmproxy.org/) — open-source, scriptable
  - [**Reqable**](https://reqable.com) — cross-platform, modern
  - [**Proxypin**](https://proxypin.com) — lightweight alternative

> **Note:** Root or elevated access is required.
---

## 🚀 Bypass Procedure

### Step 1 — Replace the Original Library

Push the patched `libcoldstart.so` into Facebook's lib directory using ADB:

```bash
adb push /path/to/patched/libcoldstart.so /data/data/com.facebook.katana/lib-compressed/libcoldstart.so
```

### Step 2 — Set Correct Permissions

Ensure the replaced library has the correct permissions so the app can load it:

```bash
adb shell chmod 755 /data/data/com.facebook.katana/lib-compressed/libcoldstart.so
```

### Step 3 — Configure Your MITM Proxy

1. Set up your preferred proxy tool and start listening on the designated port.
2. Install and trust the proxy's CA certificate on the Android device or emulator.
3. Configure the device's Wi-Fi proxy settings to route traffic through your proxy.

### Step 4 — Force-Stop, Launch & Capture

```bash
adb shell am force-stop com.facebook.katana
adb shell monkey -p com.facebook.katana -c android.intent.category.LAUNCHER 1
```

Open your proxy tool — you should now see Facebook's HTTPS traffic flowing through in cleartext.

> **Tip:** Always force-stop Facebook before relaunching to guarantee the patched library is loaded from disk rather than from a cached process.


---

## 📬 Contact & Latest Builds

For the **most up-to-date** patched libraries, version-specific support, or custom bypass requests:

[![Telegram](https://img.shields.io/badge/💬_Chat_on_Telegram-2CA5E0?style=for-the-badge&logo=telegram&logoColor=white&labelColor=121212&color=26A5E4&logoWidth=20)](https://t.me/MUH4MM4DSH4KIB)

---

## 🏷️ Keywords

`facebook ssl pinning bypass 2026` · `facebook certificate pinning bypass android` · `facebook mitm proxy 2026` · `facebook https traffic interception` · `facebook burp suite android` · `libcoldstart.so patch` · `facebook native ssl bypass` · `meta facebook security research` · `facebook api reverse engineering` · `android ssl pinning bypass no root` · `facebook fizz tls bypass` · `facebook proxy capture` · `facebook network traffic analysis` · `bypass ssl pinning android 2026` · `facebook pentesting android` · `mobile security research facebook` · `facebook certificate verification bypass` · `facebook arm64 binary patch`
