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
