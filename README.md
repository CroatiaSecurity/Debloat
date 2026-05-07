# 🧹 Debloat — Windows Image Debloating Presets

> **NTLite & WinReducer Presets for Windows 11** — Pre-configured profiles to strip unnecessary components, features, and bloatware from Windows installation images before deployment.

---

## 🗑️ Overview

This project contains two preset files for offline Windows image customization. They are designed to be used in sequence: first WinReducer to remove features and configure settings, then NTLite for deep component removal. Together they produce a lean, minimal Windows 11 installation.

### ✨ Key Features

- 🔧 **Two-Stage Debloat** — WinReducer handles features and settings, NTLite handles deep component removal
- 🎯 **Targeted for Windows 11 26H1** — Built and tested against Windows 11 Core 26H1 x64 (build 28000+)
- 🚫 **Aggressive Removal** — Strips telemetry, Bing search, Cortana, cloud features, legacy components, and much more
- 🛡️ **Security-Conscious** — Removes unnecessary attack surface while keeping core OS functionality

---

## 📁 Files

| File | Run Order | Tool | Description |
|------|-----------|------|-------------|
| `Gorstaks Winreducer Preset (Run 1st).wccf` | 1st | WinReducer EX-110 v3.9.8 | Feature removal and configuration |
| `Gorstaks NTLite Preset (Run 2nd).xml` | 2nd | NTLite 2026.3 | Deep component removal via DISM |

---

## 🚀 Usage

### Step 1 — WinReducer (Run First)

1. Open **WinReducer EX-110**
2. Mount your Windows 11 ISO/WIM
3. Load `Gorstaks Winreducer Preset (Run 1st).wccf`
4. Apply and save

**Features removed by WinReducer:**
- Hyper-V, Windows Sandbox, WSL
- Internet Explorer 11, Windows Media Player
- AD LDS, Data Center Bridging, Host Guardian
- IIS, MSMQ, MultiPoint Connector
- Telnet, TFTP, TIFF iFilter
- Windows Defender Application Guard
- Remote Differential Compression

### Step 2 — NTLite (Run Second)

1. Open **NTLite**
2. Load the modified image from Step 1
3. Import `Gorstaks NTLite Preset (Run 2nd).xml`
4. Apply and save

**Components removed by NTLite (partial list):**
- Telemetry Client (Asimov), CEIP/SQM
- Bing Search, Cortana, Cloud Desktop, Cloud Notifications
- Action Center, Accessibility tools (Narrator, Magnifier)
- Azure AD, Active Directory, Device Guard
- COM+ services, Containers/Application Guard
- Backup and Restore, AutoPlay
- Legacy File Explorer, File Picker
- Diagnostics and Troubleshooting
- Windows Update Delivery Optimization
- And 100+ more components

---

## ⚠️ Notes

- These presets are **aggressive** — test the resulting image in a VM before deploying to production hardware.
- Some removed components cannot be reinstalled without a fresh image.
- Preset versions are tied to specific NTLite/WinReducer versions; newer versions may require re-validation.

---

## ⚙️ Requirements

- **NTLite** 2026.3+ (Licensed edition recommended for full component removal)
- **WinReducer EX-110** v3.9.8+
- **Windows 11 ISO** (26H1 / build 28000+)

---

## 📜 License & Disclaimer

This project is intended for authorized defensive, administrative, research, or educational use only.

- Use only on systems, networks, and environments where you have explicit permission.
- Misuse may violate law, contracts, policy, or acceptable-use terms.
- Running security, hardening, monitoring, or response tooling can impact stability and may disrupt legitimate software.
- Validate all changes in a test environment before production use.
- This project is provided "AS IS", without warranties of any kind, including merchantability, fitness for a particular purpose, and non-infringement.
- Authors and contributors are not liable for direct or indirect damages, data loss, downtime, business interruption, legal exposure, or compliance impact.
- You are solely responsible for lawful operation, configuration choices, and compliance obligations in your jurisdiction.

---

<p align="center">
  <sub>Built with care by <strong>Gorstak</strong></sub>
</p>
