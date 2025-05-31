#!/bin/bash

# report.sh - Generate a detailed software report for macOS

OUTPUT="mac-installed-software.md"
DATE=$(date)

echo "# 📦 Mac Installed Software Report" > "$OUTPUT"
echo "_Generated on $DATE_" >> "$OUTPUT"
echo "" >> "$OUTPUT"

echo "## 🍺 Homebrew Packages" >> "$OUTPUT"
brew list >> "$OUTPUT"
echo "" >> "$OUTPUT"

echo "## 🧳 Homebrew Cask Applications" >> "$OUTPUT"
brew list --cask >> "$OUTPUT"
echo "" >> "$OUTPUT"

echo "## 🔄 Outdated Homebrew Packages" >> "$OUTPUT"
brew outdated >> "$OUTPUT"
echo "" >> "$OUTPUT"

echo "## 🐍 Python Packages (pip3)" >> "$OUTPUT"
pip3 list >> "$OUTPUT"
echo "" >> "$OUTPUT"

echo "## 🟩 Global Node.js Packages (npm)" >> "$OUTPUT"
npm list -g --depth=0 >> "$OUTPUT"
echo "" >> "$OUTPUT"

echo "## 🛍 Mac App Store Apps (mas)" >> "$OUTPUT"
mas list >> "$OUTPUT"
echo "" >> "$OUTPUT"

echo "## 🖥 System Applications (/Applications)" >> "$OUTPUT"
ls /Applications >> "$OUTPUT"
echo "" >> "$OUTPUT"

echo "## 🔧 Homebrew Package Versions" >> "$OUTPUT"
for pkg in $(brew list); do
    version=$(brew info "$pkg" | grep -m 1 'installed' | awk '{print $3}')
    echo "$pkg: $version" >> "$OUTPUT"
done
echo "" >> "$OUTPUT"

echo "## 🧳 Homebrew Cask Application Versions" >> "$OUTPUT"
brew list --cask --versions >> "$OUTPUT"
echo "" >> "$OUTPUT"

echo "✅ Report saved to: $OUTPUT"
