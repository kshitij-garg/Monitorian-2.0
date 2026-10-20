# Monitorian 2.0 — v2.3.0

![Monitorian 2.0 Banner](.github/social_preview.jpg)

[![GitHub Release](https://img.shields.io/github/v/release/kshitij-garg/Monitorian-2.0?style=for-the-badge&color=2ea44f)](https://github.com/kshitij-garg/Monitorian-2.0/releases/latest)
[![Platform](https://img.shields.io/badge/platform-Windows%2010%20%7C%2011-blue?style=for-the-badge)](#)
[![Main Contributor](https://img.shields.io/badge/main%20contributor-kshitij--garg-orange?style=for-the-badge)](https://github.com/kshitij-garg)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-garg--kshitij-0A66C2?style=for-the-badge&logo=linkedin)](https://in.linkedin.com/in/garg-kshitij)
[![License](https://img.shields.io/github/license/kshitij-garg/Monitorian-2.0?style=for-the-badge)](LICENSE.txt)
[![Windows CI](https://github.com/kshitij-garg/Monitorian-2.0/actions/workflows/ci.yml/badge.svg)](https://github.com/kshitij-garg/Monitorian-2.0/actions/workflows/ci.yml)
[![Source Version](https://img.shields.io/badge/source-v2.3.0-7b2cbf?style=for-the-badge)](CHANGELOG.md)

**Monitorian 2.0** is an open-source Windows desktop utility to adjust the brightness and contrast of multiple monitors with ease. Developed and maintained by **[kshitij-garg](https://github.com/kshitij-garg)** (Main Contributor) as an enhanced continuation and independent fork of Monitorian, version 2.0 introduces community-requested quality-of-life improvements with absolute zero friction: a free native CLI engine, tray scroll OSD, automatic brightness restore on wake, full localization across 28 languages (including top Indian languages), and true single-file portable execution.

---

## What's new in v2.3.0

- **Tray Menu Crash Resolved:** Corrected the WPF scrollbar target mismatch that caused 100% crashes when opening the right-click tray settings menu.
- **Instant Screen Blackout (Middle-Click):** Middle-clicking the notification area icon instantly blanks all connected displays pitch black for privacy or OLED resting. Moving the mouse, clicking, or pressing any key restores the screen without reconnect delays.
- **Global Keyboard Shortcuts:** System-wide shortcuts (`Win+Alt+Up`/`Down` for brightness with OSD feedback, `Win+Alt+B` for Instant Screen Blackout).
- **Day/Night Scheduled Brightness:** Energy-efficient background scheduler managing daytime and nighttime brightness transitions with zero continuous CPU overhead.
- **Competitive Benchmark & SWOT:** In-depth architectural evaluation against Twinkle Tray, ClickMonitorDDC, and upstream available in [docs/BENCHMARK_AND_SWOT.md](docs/BENCHMARK_AND_SWOT.md).
- **Application Error Recovery:** Added a global exception policy that logs and recovers from non-fatal Dispatcher and background task failures without terminating the process.
- **Safe Assembly Reflection:** Hardened `ProductInfo` with fallback mechanisms to prevent `NullReferenceException` when invoked from unmanaged hosts or test runners.
- **Language Switch Stability:** Eliminated window lifecycle race conditions when dynamically switching between any of the 28 languages.
- **Extended CLI Automation:** Added monitor-targeted commands by name or device ID, relative brightness steps (`+10`, `-10`), and contrast get/set support.
- **CI/CD & Security:** Added automated Windows CI (Debug/Release, 62 unit tests, localization verification, startup smoke tests), CodeQL security scanning, Dependabot, and reproducible release packaging.

The v2.3.0 release is now live and published on GitHub Releases. Direct download links below deliver the latest verified standalone executables.

---

## Latest Published Release Downloads

No installer or administrator privileges required. Download and run directly:

| Binary | Description | Direct Link |
| :--- | :--- | :--- |
| **`Monitorian.exe`** | **True Single-File Standalone Executable**<br>Self-contained with all dependencies bundled via Costura.Fody. | [Download `Monitorian.exe`](https://github.com/kshitij-garg/Monitorian-2.0/releases/latest/download/Monitorian.exe) |
| **`Monitorian-Portable.exe`** | **Zero-Config Portable Executable**<br>Automatically keeps all configuration files in its local folder without writing to `%LocalAppData%`. | [Download `Monitorian-Portable.exe`](https://github.com/kshitij-garg/Monitorian-2.0/releases/latest/download/Monitorian-Portable.exe) |
| **Versioned ZIP archive** | **Complete Release Archive**<br>Includes standalone executables, configurations, and all 28 localization satellite language packs. | [Open the latest release](https://github.com/kshitij-garg/Monitorian-2.0/releases/latest) |

---

## Monitorian 2.0 highlights

![Monitorian 2.0 Interface](Images/ui_main_window.jpg)

### Key Highlights

| Feature | Details |
| :--- | :--- |
| ⚡ **Free Native CLI Engine** | Unlocks free command-line brightness and contrast automation directly in the app. No paid store add-ons or subscriptions required. |
| 🎛️ **Tray Icon Scroll OSD** | Hover over the notification area icon and scroll your mouse wheel to adjust brightness. Features a Windows 11-style auto-theming On-Screen Display. |
| ⌨️ **Global Keyboard Shortcuts**| Adjust brightness (`Win+Alt+Up/Down`) or toggle instant blackout (`Win+Alt+B`) globally from anywhere in Windows. |
| 🌓 **Day/Night Scheduled Mode**| Automated day/night brightness transitions running on an ultra-lightweight timer with 0% background CPU burn. |
| 🌑 **Instant Screen Blackout** | Middle-click the tray icon to black out all monitors for privacy or OLED standby. Restores immediately on any mouse move, click, or key press. |
| 🔄 **Restore Brightness on Wake** | Resolves the common DDC/CI issue where external monitors reset to 100% or hardware defaults after waking from sleep, hibernation, or display timeout. |
| 🧳 **True Single-File Portable Mode** | All WPF dependencies (`StartupAgency`, `ScreenFrame`, `Microsoft.Xaml.Behaviors`) are embedded directly into the binary. Zero installation friction. |
| ⚙️ **Exposed UI Settings** | Frequently used power-user settings are now exposed directly as toggles in the GUI settings menu. |
| ✨ **Frictionless Defaults** | Scroll OSD and Wake Restoration are active by default so everything works immediately upon first launch. |

---

## Tray Icon Scroll & Windows 11 OSD

![Tray Icon Scroll OSD](Images/ui_scroll_osd.jpg)

Hover your cursor over the Monitorian notification area icon in the taskbar and scroll your mouse wheel to smoothly adjust brightness up or down. A floating translucent acrylic On-Screen Display (OSD) pill provides immediate visual feedback with your active brightness percentage and current theme styling.

---

## Command-Line Interface (CLI) Quick Reference

![Native CLI Engine Terminal](Images/ui_cli_terminal.jpg)

Monitorian 2.0 includes a free, fully open-source native command-line interface. Automate brightness profiles, integrate with Elgato Stream Deck, AutoHotkey, PowerShell scripts, or Windows Task Scheduler with zero friction.

### Common Commands

```powershell
# Get brightness of all connected monitors
Monitorian.exe /get

# Set brightness of all monitors to 50%
Monitorian.exe /set 50

# Set brightness of a specific monitor by name or device ID
Monitorian.exe /set "Dell U2720Q" 75

# Relative adjustments (increase or decrease by percentage)
Monitorian.exe /set +10
Monitorian.exe /set -15

# Get or adjust contrast
Monitorian.exe /get contrast
Monitorian.exe /set contrast 60
Monitorian.exe /set contrast "LG UltraGear" 55
```

### CLI Command Summary

| Action | Command Syntax |
| :--- | :--- |
| **Get All Brightness** | `Monitorian.exe /get` |
| **Get Single Monitor Brightness** | `Monitorian.exe /get "Monitor Name"` or `Monitorian.exe /get [DeviceID]` |
| **Set Global Brightness** | `Monitorian.exe /set [0-100]` |
| **Set Single Monitor Brightness** | `Monitorian.exe /set "Monitor Name" [0-100]` |
| **Relative Brightness Adjustment** | `Monitorian.exe /set +[Value]` or `Monitorian.exe /set -[Value]` |
| **Get Contrast** | `Monitorian.exe /get contrast` |
| **Set Contrast** | `Monitorian.exe /set contrast [0-100]` |

---

## Exposed UI Settings & Wake Restoration

![Settings Flyout Menu](Images/ui_settings_flyout.jpg)

Power-user settings previously tucked behind hidden command-line flags are now directly available via intuitive toggle switches in the Settings menu:

- **Restore brightness on display wake**: Automatically re-applies your chosen brightness levels after the system wakes from sleep or screen timeout.
- **Tray icon mouse wheel scroll**: Quickly enable or disable notification icon scrolling.
- **Middle-click tray icon to black out screen**: Instantly blank all displays on middle-click, dismissable on any mouse movement, click, or keystroke.
- **Enable global hotkeys**: System-wide `Win+Alt+Up`/`Down` for brightness adjustments and `Win+Alt+B` for blackout.
- **Enable day/night scheduled brightness**: Automatically switches brightness between customizable daytime and nighttime hours.

---

## Portable Mode Execution

![Zero-Config Portable Workflow](Images/ui_portable_workflow.jpg)

Monitorian 2.0 provides two convenient ways to run portably without leaving data in your user profile:

1. **Automatic Detection:** Simply run `Monitorian-Portable.exe`. It automatically detects its executable name and stores all settings in its local directory.
2. **Marker File:** Place an empty file named `portable.ini` alongside `Monitorian.exe` to redirect configuration storage to the application folder.

> [!NOTE]
> If the application directory is read-only (such as `C:\Program Files\`), Monitorian 2.0 automatically falls back to `%LocalAppData%\Monitorian` to ensure your settings are never lost.

---

## System Requirements

- **Operating System:** Windows 10 (version 1607 or newer) or Windows 11
- **Runtime:** .NET Framework 4.8 (pre-installed on modern Windows versions)
- **Display Hardware:** External monitors must support and enable **DDC/CI** in their hardware on-screen menu.

---

## Building from Source

You can build Monitorian 2.0 locally using Visual Studio 2022 or the standalone MSBuild Build Tools:

```powershell
# 1. Clone the repository
git clone https://github.com/kshitij-garg/Monitorian-2.0.git
cd Monitorian-2.0

# 2. Restore dependencies and compile the application
msbuild Source/Monitorian/Monitorian.csproj /restore /t:Rebuild /p:Configuration=Release /p:Platform=AnyCPU

# 3. Build and run the automated tests
msbuild Source/Monitorian.Test/Monitorian.Test.csproj /restore /t:Rebuild /p:Configuration=Release /p:Platform=AnyCPU
vstest.console.exe Source/Monitorian.Test/bin/Release/Monitorian.Test.dll
```

The output executables (`Monitorian.exe` and `Monitorian-Portable.exe`) will be generated in `Source/Monitorian/bin/Release/`.
Every push and pull request also runs the Windows CI workflow, which builds Debug and Release configurations, runs unit tests, validates every localization satellite assembly, and smoke-tests startup and CLI forwarding.

---

## Comparison: Why Monitorian 2.0?

If you are evaluating alternatives like **Twinkle Tray** or **ClickMonitorDDC**, here is how Monitorian 2.0 compares:

| Metric / Capability | Monitorian 2.0 | Twinkle Tray | ClickMonitorDDC | Upstream Monitorian |
| :--- | :--- | :--- | :--- | :--- |
| **Technology** | **Native .NET / WPF** | Electron / Node.js | Win32 C++ (Abandoned) | Native .NET / WPF |
| **Binary Footprint** | **~1.3 MB** (Single-file) | ~200 MB installer | ~1.5 MB | ~1.3 MB (MSI) |
| **Idle Memory** | **~35–45 MB** | ~140–280 MB | ~15 MB | ~40 MB |
| **Cold Startup Time** | **<250 ms** | 2.5–4.0 s | <150 ms | <250 ms |
| **Global Hotkeys** | ✅ (`Win+Alt+Up/Down/B`) | ⚠️ Limited | ✅ Win32 hotkeys | ❌ None |
| **Scheduled Transitions** | ✅ Minute-boundary (0% CPU) | ✅ Solar / time schedule | ❌ None | ❌ None |
| **Middle-Click Blackout**| ✅ Multi-monitor overlay | ❌ None | ❌ None | ❌ None |
| **CLI Automation** | ✅ **Free & Built-in** | ❌ None | ✅ Powerful CLI | 🔒 Paid Store Add-on |
| **Portable Mode** | ✅ **Zero-config single-file** | ❌ Installer required | ✅ Portable zip | ❌ MSI only |
| **Active Maintenance** | ✅ **Active (2026)** | ⚠️ Infrequent | ❌ Abandoned | ⚠️ Stalled |

Read the full competitive analysis and SWOT evaluation in [docs/BENCHMARK_AND_SWOT.md](docs/BENCHMARK_AND_SWOT.md).

---

## Community & Localization

Monitorian 2.0 includes localization translations across 28 languages provided by community contributors:

- **Arabic (ar)**: [@MohammadShughri](https://github.com/mohammadshughri)
- **Bengali (bn)**: [@kshitij-garg](https://github.com/kshitij-garg)
- **Catalan (ca)**: [@ericmp33](https://github.com/ericmp33)
- **German (de)**: [@uDEV2019](https://github.com/uDEV2019)
- **Greek (el-GR)**: [@NickMihal](https://github.com/NickMihal)
- **Spanish (es)**: [@josemirm](https://github.com/josemirm), [@ericmp33](https://github.com/ericmp33)
- **Persian (fa-IR)**: [@sinadalvand](https://github.com/sinadalvand)
- **French (fr)**: [@AlexZeGamer](https://github.com/AlexZeGamer), [@Rikiiiiiii](https://github.com/rikiiiiiii)
- **Hindi (hi)**: [@kshitij-garg](https://github.com/kshitij-garg)
- **Italian (it)**: [@GhostyJade](https://github.com/GhostyJade)
- **Japanese (ja-JP)**: [@emoacht](https://github.com/emoacht)
- **Korean (ko-KR)**: [@VenusGirl](https://github.com/VenusGirl)
- **Marathi (mr)**: [@kshitij-garg](https://github.com/kshitij-garg)
- **Dutch (nl-NL)**: [@JordyEGNL](https://github.com/JordyEGNL)
- **Polish (pl-PL)**: [@Daxxxis](https://github.com/Daxxxis), [@FakeMichau](https://github.com/FakeMichau)
- **Portuguese (pt-BR)**: [@guilhermgonzaga](https://github.com/guilhermgonzaga)
- **Romanian (ro)**: [@calini](https://github.com/calini)
- **Russian (ru-RU)**: [@SigmaTel71](https://github.com/SigmaTel71), [@San4es](https://github.com/San4es)
- **Slovenian (sl)**: [@anderlli0053](https://github.com/anderlli0053)
- **Albanian (sq)**: @RDN000
- **Swedish (sv-SE)**: [@Sopor](https://github.com/Sopor)
- **Tamil (ta)**: [@kshitij-garg](https://github.com/kshitij-garg)
- **Telugu (te)**: [@kshitij-garg](https://github.com/kshitij-garg)
- **Turkish (tr-TR)**: [@webbudesign](https://github.com/webbudesign)
- **Ukrainian (uk-UA)**: [@kaplun07](https://github.com/kaplun07)
- **Vietnamese (vi-VN)**: [@dongsinhho](https://github.com/dongsinhho)
- **Simplified Chinese (zh-Hans)**: [@ComMouse](https://github.com/ComMouse), [@zhujunsan](https://github.com/zhujunsan), [@XMuli](https://github.com/XMuli), [@FISHandCHEAP](https://github.com/Fishandcheap), [@FrzMtrsprt](https://github.com/FrzMtrsprt)
- **Traditional Chinese (zh-Hant)**: [@toto6038](https://github.com/toto6038), [@XMuli](https://github.com/XMuli)

---

## Credits & License

- **Main Contributor & Project Lead:** [Kshitij Garg (@kshitij-garg)](https://github.com/kshitij-garg) | [LinkedIn](https://in.linkedin.com/in/garg-kshitij).
- **Foundational Architecture:** Created by [emoacht](https://github.com/emoacht).
- **License:** Distributed under the [MIT License](LICENSE.txt).
- **Contributing:** See the [contribution guide](docs/CONTRIBUTING.md) and [code of conduct](CODE_OF_CONDUCT.md).
- **Security:** Report vulnerabilities through the process in [SECURITY.md](SECURITY.md).
- **Changes:** See [CHANGELOG.md](CHANGELOG.md).
- **Releasing:** See the [GitHub build and release guide](docs/RELEASING.md).
