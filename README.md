<div align="center">

<img width="160" alt="arc-control" src=".github/arc-control.png">

### Arc Control — the Arc and Arx app for DSM 7.x

Configure, update and monitor your loader straight from DSM.<br>
No reboot into Config Mode for most of what used to need one.

<a href="https://github.com/AuxXxilium/arc-control/releases/latest"><img alt="Download" src="https://img.shields.io/badge/download-red?style=for-the-badge&label=latest&color=%23FF0000"></a>
<a href="https://xpenology.tech/documentation/"><img alt="Documentation" src="https://img.shields.io/badge/read_first-blue?style=for-the-badge&label=docs&color=%230066CC"></a>
<a href="https://discord.auxxxilium.tech"><img alt="Discord" src="https://img.shields.io/badge/discord-5865F2?style=for-the-badge&label=chat&color=%235865F2"></a>

</div>

---

> [!IMPORTANT]
> * Arc Control is a DSM package for machines booted by [Arc](https://github.com/AuxXxilium/arc) or [arx](https://github.com/AuxXxilium/arx). It is not a loader.
> * **Commercial use is not permitted and strictly forbidden.**
> * DSM and all parts of it are under copyright / ownership by Synology Inc.
> * The app is free and will stay free forever. If you paid a suspicious person for it, I can't help you — I'm not connected to them.

> [!WARNING]
> Arc Control is for experienced users. It can change and rebuild your loader, tune kernel settings, patch DSM, restart your NAS and grant root privileges to packages, and it includes a root terminal. Loader changes are still best made in Config Mode where possible. Back up anything on the machine's disks first. I'm not liable for damage or loss of any kind.

---

## ✨ What Arc Control does

Arc Control installs from Package Center and adds an app and a desktop widget to DSM. It detects whether Arc or arx booted the machine and only shows the pages that loader supports.

**Loader**

* **Configuration** — edit Arc's settings as form fields: model, platform, PAT URL and checksum, serial, MACs, USB VID/PID, SataDOM, kernel options, module blacklist and boot screen, and download a backup *(Arc only)*
* **Addons** — browse, search, enable and disable Arc's or arx's addons, with descriptions and versions
* **Update & Rebuild** — update the loader and rebuild DSM's kernel and ramdisk from DSM while it keeps running. Every step shows its progress, and if a rebuild fails the previous build is put back. Choose latest or beta, and see what an update would install next to what is installed
* **Restart into a mode** — Rebuild, Update or Config Mode, each explained before you confirm
* **Update notice** — the Overview says when a newer loader is available and shows its release notes

**Monitoring**

* **Overview** — model, DSM and loader versions, CPU, memory, board, kernel, live clock speed and temperature, and a photo of your own mainboard if you add one
* **System Monitor** — utilisation, per-core clocks with the kernel's frequency-step statistics, temperatures, fans, storage controllers, NVMe, GPUs and network. Click any disk for its SMART report and serial
* **Resource Monitor** — live CPU, memory and swap, per-core load with P- and E-cores marked, and a searchable process list with details and kill
* **Network Monitor** — addressing, link state, speed, duplex, MTU, throughput, errors, link flaps, bonds and bridges
* **GPU Monitor** — usage, memory, clocks, power, temperature and fans for Intel (integrated and Arc), AMD and NVIDIA cards

**Tuning**

* **CPU Control** — online threads, governor, turbo, energy/performance preference, scaling rate and Dynamic Power Saving. On hybrid CPUs, pin services to P- or E-cores. Every setting survives a reboot
* **Fan Control** — three-point fan curves across Full, Cool and Quiet, per-fan curves, BIOS control, and a live graph with RPM *(needs the fancontrol addon)*

**Services and patches**

* **Arc Connect** *(beta)* — relayed, end-to-end encrypted remote access to DSM without port forwarding, with a QR code for your phone and optional statistics for [Arc Management](https://arc.xpenology.tech/)
* **Apps & Permissions** — grant or revoke root escalation per package or user, and start, stop or restart packages
* **Patches** — StoragePanel, HDD/SSD database (IronWolf Health Management, deduplication, silencing warnings), Sequential I/O, Surveillance Station local display, Synology Photos face recognition
* **LED control** — on UGREEN machines, LEDs on, off or automatic, and **Disk LED Mapping**, which flashes each disk's LED and lets you move it to the right bay
* **AppInstaller** — install and patch packages in an interactive terminal
* **VCRT** — the encoders, decoders and hardware acceleration of VCRT's FFmpeg, which you can make the system default *(appears when VCRT is installed)*

**Diagnostics**

* **Benchmark** — storage, CPU and GPU tests with results on the page, the newest Arc benchmark script fetched at each run, and optional submission to the public score database
* **Speedtest** — Ookla's official client, with automatic or manual server selection
* **Debug** — kernel command line, loaded modules, MACs, dmesg, a root terminal and a diagnostic report for support requests

Light and dark themes, a choice of highlight colours, a collapsible sidebar, and a **?** in the header that opens help for the page you are on.

---

## 🧭 How it works

```
Package Center → Arc Control (DSM app + desktop widget)
                 └─ CGI scripts, run by DSM's nginx on each request
                    → loader: VERSION from /usr/arc or /usr/arx, loader disk mounted per job
                    → monitoring: sysfs, SMART, nvidia-smi
                    → tuning: cpufreq settings, reapplied by a boot script after each reboot
```

No daemon runs in the background. Each page asks the system directly when you open or refresh it. Loader jobs such as Update & Rebuild mount the loader disk, run the loader's own scripts, and unmount it when they finish.

---

## 🖥️ Supported

| Loader | What Arc Control offers |
| :-- | :-- |
| [Arc](https://github.com/AuxXxilium/arc) | Everything: Configuration, Addons, restarts into Rebuild, Update and Config Mode. Update & Rebuild from Arc 4.1.0 |
| [arx](https://github.com/AuxXxilium/arx) | Addons, Update & Rebuild with arx's own jobs, restarts into Rebuild and Config Mode on releases that support them. arx is configured in its web UI, so there is no Configuration page |

Some pages depend on your hardware or an addon and are hidden when they don't apply: Fan Control, GPU Monitor, VCRT, StoragePanel, HDD/SSD Database and LED control.

---

## 📋 What you need

* DSM 7.x on a machine booted by Arc or arx
* An administrator account in DSM
* Internet, for loader updates, Arc Connect, Speedtest and the newest benchmark script

---

## 📦 Installation

1. Download the latest `.spk` from the [releases](https://github.com/AuxXxilium/arc-control/releases/latest)
2. In DSM, open **Package Center → Manual Install** and choose the file
3. Open **Arc Control** from the main menu, or add its widget to the desktop

To update Arc Control, install the newer `.spk` the same way.

---

## 📚 Documentation

* [Documentation](https://xpenology.tech/documentation/) — **read this first**
* Every page in the app has its own help behind the **?** in the header

---

## 🧰 More from the Arc Project

| Project | Description |
| :-- | :-- |
| [Arc Loader](https://github.com/AuxXxilium/arc) | Redpill loader for DSM 7.x, with guided setup for many platforms and models |
| [arx](https://github.com/AuxXxilium/arx) | The evolution of Arc — set up entirely from your browser |
| [Arc Utilities](https://github.com/AuxXxilium/arc-utils) | Tools to install, patch and activate DSM apps on Xpenology |
| [Arc Management](https://arc.xpenology.tech/) | Web management for Arc, with the sensor data Arc Connect reports |
| [AuxXxilium](https://github.com/AuxXxilium) | Everything else from the Arc Project |

---

### Developer

- <a href="https://github.com/AuxXxilium">AuxXxilium</a>
- <a href="https://github.com/FulcrumCode">Fulcrum</a>

### Thanks

* **TTG** and everyone who continued the original redpill-load project, which Arc and arx are based on
* **pocopico, jumkey, fbelavenuto, wjz304, PeterSuh-Q3, 007revad** and others, whose code and work are part of Arc, arx and their addons

<div align="center">

[![Stars](https://img.shields.io/github/stars/AuxXxilium/arc-control?style=for-the-badge&logo=github)](https://github.com/AuxXxilium/arc-control)
[![Discord](https://img.shields.io/discord/639072565155069962?style=for-the-badge&logo=discord&label=Discord)](https://discord.auxxxilium.tech)

</div>
