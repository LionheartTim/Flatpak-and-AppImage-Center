# 📦 Flatpak and AppImage Center

**Flatpak and AppImage Center** is a user-friendly, lightweight graphical user interface (GUI) built with Python and PyQt6. Designed specifically for **Bazzite** (and other Linux distributions), this tool combines two essential system maintenance utilities into a single, cohesive dashboard using a clean tabbed layout.

With this application, you can effortlessly manage portable `.AppImage` programs and thoroughly uninstall `Flatpak` applications—including their hidden leftover configuration caches—without ever touching the terminal.

---

## ✨ Features

* **Dual-Utility Dashboard:** Switch seamlessly between managing AppImages and uninstallation of Flatpaks using a native native tab interface.
* **Effortless AppImage Integration:** Drag and drop any `.AppImage` file into the window to make it executable, safely move it to `~/Applications/`, and instantly generate an official Linux `.desktop` launcher file for your application menu.
* **Thorough Flatpak Uninstallation:** Select single or multiple Flatpaks to remove. The tool deeply erases apps along with their hidden user data caches inside `~/.var/app/` to free up valuable disk space.
* **Live Metadata Scanner:** Click on any installed Flatpak in the list to expand and view its version, license, package architectures, specific branch origin, and active commits live from your host system.
* **Smart Sandbox Escaping:** Built-in translation mechanisms safely bypass Flatpak restrictions (`flatpak-spawn --host`) to seamlessly interact with system package managers and launch your native web browser.
* **Multi-Language Engine:** Automatically detects your active system environment and dynamically shifts between English and Dutch layouts.

---

## 🛠️ Requirements & Prerequisites

The application builds inside a sandboxed environment using the official **KDE Software Development Kit**. Ensure you have the required runtimes installed before building:

```bash
flatpak install flathub org.kde.Platform//6.8 org.kde.Sdk//6.8 -y
```

---

## 🏗️ Compilation & Local Testing

To build the project files and install the application locally directly onto your user space, execute the following commands in your terminal:

```bash
# 1. Navigate to the project directory
cd "/home/Tim/Desktop/Bazzite Projects/Flatpak and Appimage Center/"

# 2. Compile and install the application locally for your user environment
flatpak-builder --user --install --force-clean build org.bazzite.FlatpakAndAppImageCenter.json

# 3. Launch the freshly compiled environment to test it live
flatpak run org.bazzite.FlatpakAndAppImageCenter
```

---

## 📦 Building a Standalone `.flatpak` Bundle

If you want to compile and export the entire project into a single, standalone offline installation bundle (`.flatpak`) to share with others or keep as a backup file on your Desktop, run these steps:

```bash
# 1. Compile the workspace into a local distribution repository
flatpak-builder --force-clean --repo=local-repo build_dir org.bazzite.FlatpakAndAppImageCenter.json

# 2. Export and compress the repository into a distributable installation bundle
flatpak build-bundle local-repo ~/Desktop/FlatpakAndAppImageCenter.flatpak org.bazzite.FlatpakAndAppImageCenter

# 3. Clean up the heavy temporary build directories to save storage space
rm -rf build_dir local-repo .flatpak-builder
```

---

## 🚀 How to Install the Standalone Bundle

Once the `FlatpakAndAppImageCenter.flatpak` file has been generated on your Desktop, you or any other Linux user can install it cleanly with a single command:

```bash
flatpak install --user ~/Desktop/FlatpakAndAppImageCenter.flatpak -y
```

---

## 📜 License & Credits

* **Developer:** [LionheartTim](https://github.com)
* **Version:** 1.0.0
* **License:** GPL-3.0 - Free to share, modify, and redistribute!
