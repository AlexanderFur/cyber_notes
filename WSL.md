# 🐧 Installing WSL Kali Linux on Windows 11 via PowerShell 7.5

  

This guide walks you through installing **WSL with Kali Linux** on **Windows 11** using **PowerShell 7.5**.

  

---

  

## ✅ Prerequisites

- Windows 11 (Build 22000 or later)

- PowerShell 7.5

- Administrator privileges

  

---

  

## 🧰 Step-by-Step Instructions

  

### 1. Open PowerShell as Administrator

- Right-click **PowerShell 7.5**

- Select **"Run as administrator"**

  

---

  

### 2. Enable WSL and Virtual Machine Platform

  

Run:

  

```powershell

wsl --install

```

  

If `wsl --install` is not recognized, run these instead:

  

```powershell

dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

```

  

---

  

### 3. Set WSL 2 as Default

  

```powershell

wsl --set-default-version 2

```

  

---

  

### 4. List Available Linux Distributions

  

```powershell

wsl --list --online

```

  

Look for Kali Linux in the list:

  

```

NAME            FRIENDLY NAME

kali-linux      Kali Linux Rolling

```

  

---

  

### 5. Install Kali Linux

  

```powershell

wsl --install -d kali-linux

```

  

Wait for the installation to complete.

  

---

  

### 6. Set Up Kali User

  

Create a **username** and **password** when prompted.

  

---

  

### 7. Launch Kali Linux

  

```powershell

wsl -d kali-linux

```

  

Or search **"Kali Linux"** in the Start Menu.

  

---

  

## ✅ Optional Commands

  

### Check Installed Distros

  

```powershell

wsl --list --verbose

```

  

### Remove Ubuntu (if installed by default)

  

```powershell

wsl --unregister Ubuntu

```

  

---


# Zsh

## Set zsh as default shell

>	chsh -s $(which zsh)

## Aliases

```
alias cls="clear"
alias la="ls -lashp --group-directories-first"
alias l="ls -lshp --group-directories-first"
alias lf="ls -lshp | grep -v /"
alias laf="ls -lashp | grep -v /"
alias lad="ls -lashp | grep /"
alias ld="ls -lshp | grep /"
```

Add these in the bottom of .zshrc

## Plugins
Autosuggestions
>	git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

Syntax Highlighting
>	git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

Edit in .zshrc
>	plugins=(git zsh-autosuggestions zsh-syntax-highlighting)


## Install Oh My Zsh (curl)
>	sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

## Install PowerLevel10k
>	git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/themes/powerlevel10k

Edit .zshrc: 
>	ZSH_THEME="powerlevel10k/powerlevel10k"

# .sh -files
## Update.sh
```.sh
#!/bin/zsh

# Ensure the script is run with superuser privileges
if [ "$EUID" -ne 0 ]; then
    echo "Please run this script as root or using sudo."
    exit 1
fi

# Update package lists
echo "Updating package lists..."
apt-get update

# Upgrade installed packages
echo "Upgrading installed packages..."
apt-get upgrade -y

# Perform a distribution upgrade
echo "Performing a distribution upgrade..."
apt-get dist-upgrade -y

# Perform a full upgrade
echo "Performing a full upgrade..."
apt full-upgrade -y

# Remove unnecessary packages
echo "Removing unnecessary packages..."
apt autoremove -y

echo "System update and upgrade complete!"
```

# Install Metasploit Framework
>	sudo apt install -y metasploit-framework