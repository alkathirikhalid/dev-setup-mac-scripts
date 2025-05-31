#!/bin/bash

# setup.sh
set -e

echo "🧰 Setting up your Mac development environment..."

# 1. Install Homebrew if needed
if ! command -v brew &> /dev/null; then
  echo "🍺 Installing Homebrew..."
  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
  echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
  eval "$(/opt/homebrew/bin/brew shellenv)"
else
  echo "✅ Homebrew already installed."
fi

# 2. Install everything from Brewfile
echo "📦 Installing packages from Brewfile..."
brew bundle --file=./Brewfile

# 3. Set up paths in ~/.zprofile
echo "🔧 Configuring shell paths..."
PROFILE=~/.zprofile

# Avoid duplicates
grep -qxF 'eval "$(/opt/homebrew/bin/brew shellenv)"' "$PROFILE" || echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> "$PROFILE"
grep -qxF 'export PATH="/opt/homebrew/opt/openjdk/bin:$PATH"' "$PROFILE" || echo 'export PATH="/opt/homebrew/opt/openjdk/bin:$PATH"' >> "$PROFILE"
grep -qxF 'export JAVA_HOME=/opt/homebrew/opt/openjdk/libexec/openjdk.jdk/Contents/Home' "$PROFILE" || echo 'export JAVA_HOME=/opt/homebrew/opt/openjdk/libexec/openjdk.jdk/Contents/Home' >> "$PROFILE"

# Reload shell config
source "$PROFILE"

# 4. Generate report
echo "📝 Generating installed software report..."
chmod +x report.sh
./report.sh

echo "✅ Setup complete! Please restart your terminal or run: source ~/.zprofile"
