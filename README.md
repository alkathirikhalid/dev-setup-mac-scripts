# dev-setup-mac-scripts
Automate your macOS development environment setup and reporting

## 🧠 Pro Tips

- Customize the `Brewfile` to suit your needs before running.
- Schedule `report` via cron to maintain up-to-date audits.

<pre>dev-setup-mac-scripts/
│
├── Brewfile                 # Declarative list of all apps, CLI tools, casks, and Mac App Store apps
├── setup                    # Main bootstrap script (installs Homebrew, uses Brewfile, sets up paths and generates initial report)
├── report                   # Optional script to generate a markdown report of installed tools, can be rerun to check current development setup
├── .zprofile                # Custom PATH and ENV setup (e.g., JAVA_HOME, brew paths)
├── README.md                # Clear instructions on usage and purpose
└── reports/
    └── mac-installed-software.md   # Automatically generated software report in same folder via CLI or in home folder via double click to run</pre>


# 🛠️ Mac Setup Automation

This project automates the installation and configuration of essential development tools on a new Mac. It also generates a comprehensive software report that includes details of installed tools and any outdated versions.

## 📁 Contents

- `setup` – Installs Homebrew (if not already installed), taps into required repositories, installs packages from `Brewfile`, sets up Java paths, and runs the report generator.
- `Brewfile` – Lists all Homebrew, Cask, and Mac App Store apps to be installed.
- `report` – Generates a detailed report of installed software, packages, and versions into `mac-installed-software.md`.
- `.zprofile` – Configures environment variables such as `JAVA_HOME` and ensures brew paths are set correctly.

---

## 🚀 How to Use

### 1. Download and unzip

```bash
unzip mac-setup.zip
cd mac-setup
```

### 2. Make scripts executable

```bash
chmod +x setup report
```

### 3. Run the setup script

This will:
- Install Homebrew (if not already installed), which may require admin permissions
- Tap all necessary repositories
- Install packages and apps defined in `Brewfile`
- Set `JAVA_HOME` and PATH
- Generate the software report, including details about outdated packages and installed versions

```bash
./setup
```

### 4. Generate report only (optional)

To regenerate the report at any time (e.g., check if software is outdated) via CLI:

```bash
./report
```
or double click it to run.

---

## 🔧 What Gets Installed?

- **Homebrew Packages**: `git`, `node`, `openjdk`, `python`, `wget`, `zsh`, etc.
- **Cask Apps**: `android-studio`, `intellij-idea-ce`, `visual-studio-code`, `google-chrome`
- **Mac App Store**: Xcode via `mas`

### 📊 Software Versioning and Updates

- After the `setup` script runs, the software report (`mac-installed-software.md`) will list the installed software along with their versions.
- The report will also indicate if any of the installed software is outdated by using the `brew outdated` command.

---

## 🧩 Prerequisites

- macOS with Terminal access
- Internet connection

---

## 🔐 Permissions

Scripts may prompt for:
- Administrator password (for installations)
- App Store credentials (for MAS apps)

---

## 📄 Output

A markdown file `mac-installed-software.md` will be generated, summarizing all installed software and versions. This report will also flag any outdated software that requires updating.

--- 

### Example Report Output:
The `mac-installed-software.md` report will look something like this:

```markdown
# Installed Software Report

## Homebrew Packages
- git: 2.34.1
- node: 16.13.0 (Outdated: 16.14.0 available)
- openjdk: 17.0.1
- python: 3.9.7
- zsh: 5.8

## Cask Apps
- Android Studio: 2021.1
- IntelliJ IDEA Community Edition: 2021.3.2
- Visual Studio Code: 1.61.2
- Google Chrome: 94.0.4606.81

## Mac App Store Apps
- Xcode: 13.2.1
```

--- 

### Final Notes

- Feel free to modify the `Brewfile` to suit your personal or project-specific needs before running the setup.
- If you prefer only generating the software report without reinstalling or configuring anything, you can simply run the `report` script.

---
