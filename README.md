# ✨ Aura Launcher

A minimalist, ultra-lightweight (~8 MB RAM, ~40 KB binary) smoked-glass command & file launcher for Windows, summoned instantly via `Alt + Space`.

Built in pure native C# (WPF + Win32) with zero external dependencies—compiling in under a second using the built-in Windows .NET compiler (`csc.exe`).

---

<img width="724" height="223" alt="image" src="https://github.com/user-attachments/assets/72cf1a93-a32c-4e91-8647-92becb86210f" />
<img width="617" height="432" alt="image" src="https://github.com/user-attachments/assets/318463d0-4ca2-4f98-898b-16a5e1f062b7" />

## 🌟 Features

- **Minimalist Smoked-Glass Aesthetic:** Soft-cornered translucent glass bar with a living sapphire & ice-blue ambient glow. Shows **only** the search bar when summoned—no clutter, no ads, and no visual noise.
- **Kinetic Variable-Speed Outline:** Features a luminous ice-blue border highlight that spins rapidly when summoned and smoothly decelerates into an organic, non-uniform wave around the perimeter.
- **Cursor-Reactive Ambient Lighting:** Smoothly tracks your mouse cursor with spring-interpolated (`lerp`) radial lighting across both the search bar and the results panel.
- **Hardware VSync Animations:** Locked to your monitor's native refresh rate (`CompositionTarget.Rendering` + GPU `BitmapCache`) with zero-allocation window reveals, ensuring 0% CPU usage when idle/hidden.
- **Instant Whole-PC File & App Search:** Searches installed applications, folders, and files across your computer in under a millisecond using an in-memory background indexer and real-time `FileSystemWatcher`.
- **Inline Math Calculator:** Type any mathematical expression (`450 * 1.12`, `2^10`, `(1200 / 3) + 55`) for instant live evaluation; press `Enter` to copy the answer to your clipboard.
- **Ultra-Low Memory Footprint:** Automatically trims its working set via Win32 `EmptyWorkingSet` whenever hidden, idling at **~5–10 MB RAM**.

---

## ⌨️ Controls

| Shortcut / Action | Description |
| :--- | :--- |
| **`Alt + Space`** | Summon or hide Aura Launcher |
| **`↑` / `↓`** | Navigate search results (locks against stationary mouse cursor) |
| **`Enter`** | Open selected application, file, folder, or copy math result |
| **`Ctrl + Enter`** *(or Right-Click)* | Reveal selected file or folder in Windows File Explorer |
| **`Esc`** *(or Click Outside)* | Dismiss launcher and trim background memory |

---

## 🚀 Getting Started

### Option 1: Run Prebuilt Binary
1. Download or clone this repository.
2. Run **`AuraLauncher.exe`** (or double-click **`Launch-Aura.bat`**).
3. Press **`Alt + Space`** anywhere on your desktop.
4. *(Optional)* Right-click the **Aura** icon in your Windows System Tray and check **Start with Windows** to launch automatically on login.

### Option 2: Build from Source (Zero Dependencies)
No Visual Studio or SDK installation is required. Every Windows 10/11 PC includes the native .NET Framework C# compiler (`csc.exe`).

Double-click **`Build.bat`**, or run the following command in PowerShell / Command Prompt:

```bat
"C:\Windows\Microsoft.NET\Framework64\v4.0.30319\csc.exe" /target:winexe /optimize+ /out:"AuraLauncher.exe" ^
  /r:"C:\Windows\Microsoft.NET\Framework64\v4.0.30319\WPF\PresentationCore.dll" ^
  /r:"C:\Windows\Microsoft.NET\Framework64\v4.0.30319\WPF\PresentationFramework.dll" ^
  /r:"C:\Windows\Microsoft.NET\Framework64\v4.0.30319\WPF\WindowsBase.dll" ^
  /r:"C:\Windows\Microsoft.NET\Framework64\v4.0.30319\System.Xaml.dll" ^
  /r:"System.Windows.Forms.dll" /r:"System.Drawing.dll" /r:"System.Data.dll" ^
  "AuraLauncher.cs"
```

---

## 📁 Project Structure

```text
aura-launcher/
├── AuraLauncher.cs    # Complete single-file C# source code (UI, VSync engine, File Indexer, Win32 interop)
├── AuraLauncher.exe   # Compiled standalone executable (~40 KB)
├── Build.bat          # One-click native compiler script using built-in Windows csc.exe
├── Launch-Aura.bat    # Helper script to start Aura Launcher
├── Stop-Aura.bat      # Helper script to stop Aura Launcher
├── .gitignore         # Ignores local runtime cache and backup files
├── LICENSE            # MIT License
└── README.md          # Project documentation
```

---

## 📄 License

Distributed under the **MIT License**. See [`LICENSE`](LICENSE) for more information.
