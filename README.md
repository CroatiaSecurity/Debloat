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

So, I'm gonna show you how to create custom windows iso, my way, using my presets.
You will require windows iso first, and there are several choices.
First, there is uupdump.net, which will download a script which will assemble your iso from uup packages.
Then there is uup adguard, which is same thing. Then there is media creation tool,
which will download stable current version directly from microsoft and verify the iso (extremely important).
You can also download store esd file, then use a tool like DISM++ to convert it to iso.
You can also use heidoc.net tool to download windows, or use archive.org to download iso.
Or, some other download source, like bob pony or getmyiso.com.
You likely don't want insider versions, because devs have direct access to your device if you install that.
Therefore, you should check media creation tool to see which current version is public, and download that exact version.
At the moment of this writing, it is 23H2. However, I noticed home versions, which fall under consumer editions,
have a ton of spying and telemetry built in, and pro version under consumer version has policies applied to your device
the moment you install it, so I recommend business editions, and just to be safe, download store esd version of it
and convert it to iso, via dism++. You can google "23H2 business pastebin" to find the link to it,
or simply check mydigitallife forum, to find the same thing. This will download it from windows update server,
so it should be untouched.

When you get the iso, you need another one, for the setup layout, as one of the debloat tools, winreducer, makes the boot.wim,
which is setup OS, unbootable. I recommend you go to archive.org, type "winreducer" into search, then click on user Macky Reddy,
and download any of his work. He has shit stripped down to the bone, so you may skip the whole debloat process and use his work.
I just need his iso for the setup layout, which is boot.wim and files it needs. I'd create one myself, but winreducer is bugged,
and ntlite really isn't a tool for debloat, mostly for configuration.

So, once you got macky reddy iso and store esd downloaded, convert the store esd to iso via dism++.
It's an option under it's file menu. Then, mount the iso, and use copy files from it to a new folder on your c drive.
Then, use official free current NTLite to navigate to that folder, mount it with ntlite,
and use my preset "ntlitenew install" on it. NTLite is bugged and doesn't install net 3.5, but you can use dism++ to add the package from sources/sxs folder.
When new ntlite is done, close it, and repeat the process in old ntlite, ver 1.5.
This old version has two important things. First, no restriction on windows you can use it on, and second,
security update backups cleanup. Run the same iso with my ntliteold install preset.
For the time being, you don't have to do any boot.wim debloating, as you will be using macky reddy boot.wim.

Then, use winreducer EX-110, current, to mount the same iso. Just navigate to to that folder on c drive.
And, of course, use my preset.

After that is done, you should mount macky reddy iso, copy files from it to a new folder in c drive,
delete install.esd if present in sources folder, then copy install.wim from your ntlite and winreducer debloated install.wim
to this 2nd folder sources subfolder.

Then, open any ntlite, open this 2nd folder for editing, and recompress the install.wim, then convert it to esd, and replace the
original. After that, you can delete first folder, and rename install.esd in 2nd folder sources subfolder to install.wim.
Refresh ntlite so it reads extension change to wim, then create iso.

And that's about it. You will end up with iso capable of running anything,
store, xbox, msft account, old apps, old games, new games, anything really, while you removed a lot of cycles from cpu,
making it work faster. The only thing that will fail is cumulative updates.

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
