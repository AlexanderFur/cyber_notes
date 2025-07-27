  

# 🪟 How to Create a Bootable Windows USB Drive

  

This guide will walk you through creating a bootable USB drive for installing or reinstalling Windows.

  

---

  

## 🔧 What You’ll Need:

- A **USB drive** (at least 8 GB, 16 GB recommended)

- A **Windows PC**

- An internet connection

- The **Windows ISO file** or use Microsoft’s **Media Creation Tool**

  

---

  

## Method 1: Using Media Creation Tool (Recommended for most users)

  

### Step 1: Download the Media Creation Tool

1. Visit Microsoft’s official download page:  

   - [Windows 10](https://www.microsoft.com/software-download/windows10)  

   - [Windows 11](https://www.microsoft.com/software-download/windows11)

2. Click **Download now** under *Create Windows installation media*.

  

### Step 2: Run the Tool

1. Insert your USB drive into the PC.

2. Open the downloaded `.exe` file (e.g., `MediaCreationTool.exe`).

3. Accept the license terms.

  

### Step 3: Create Installation Media

1. Select **Create installation media (USB flash drive, DVD, or ISO file)** and click **Next**.

2. Choose language, edition, and architecture.

3. Click **Next**.

4. Choose **USB flash drive**, click **Next**, and select your USB from the list.

5. Click **Next** again. The tool will download Windows and make the USB bootable.

  

---

  

## Method 2: Using Rufus + ISO (Advanced users)

  

### Step 1: Download ISO and Rufus

- Get the **Windows ISO** from Microsoft.

- Download **Rufus** from [https://rufus.ie](https://rufus.ie)

  

### Step 2: Prepare Rufus

1. Insert your USB drive.

2. Launch Rufus.

3. Under **Device**, select your USB.

4. Under **Boot selection**, choose your Windows ISO.

5. Set **Partition scheme**:

   - **GPT** for UEFI systems

   - **MBR** for BIOS/Legacy

6. Click **Start** and confirm data wipe.

7. Wait until Rufus completes the process.

  

---

  

## ✅ Final Step: Boot from USB

- Insert USB into the target PC.

- Restart and open the **Boot Menu** (usually F12, F10, ESC, or DEL).

- Select the USB device to begin Windows setup.

  

---


# 🔥 Create and Use a Live USB Kali Linux on Windows 11

  

This guide will walk you through creating a bootable **Live USB of Kali Linux** on a **Windows 11** system using **Rufus**.

  

---

  

## 🧰 Requirements

  

- USB Flash Drive (Minimum 8GB, 16GB+ recommended)

- Kali Linux ISO file  

  👉 [Download here](https://www.kali.org/get-kali/)

- Rufus (Tool to create bootable USBs)  

  👉 [Download here](https://rufus.ie)

  

---

  

## 📝 Step-by-Step Guide

  

### Step 1: Download the Kali Linux ISO

  

- Visit the [Kali Downloads Page](https://www.kali.org/get-kali/)

- Select the **Live ISO** (e.g., `kali-linux-2024.2-live-amd64.iso`)

- Download the file to your computer

  

---

  

### Step 2: Download and Launch Rufus

  

- Download **Rufus** from [https://rufus.ie](https://rufus.ie)

- Run Rufus (no installation required)

  

---

  

### Step 3: Plug in Your USB Drive

  

- Insert your USB stick (⚠️ This will erase all data on it)

  

---

  

### Step 4: Create Bootable Kali USB

  

1. In **Rufus**:

   - **Device**: Select your USB drive

   - **Boot selection**: Click *SELECT* and choose the Kali ISO

   - **Partition scheme**:

     - Choose **MBR** for legacy BIOS/UEFI

     - Choose **GPT** for UEFI (modern systems)

   - **File system**: Keep default (FAT32 or NTFS)

   - Optional: Set a volume label like "KaliLive"

  

2. Click **Start**:

   - Choose **"Write in ISO Image mode"** when prompted

   - Confirm data loss warning

  

---

  

### Step 5: Boot Into Kali Linux

  

1. **Restart your PC**

2. Enter the **boot menu** during startup (commonly F12, ESC, F2, DEL, F10)

3. Select your USB drive to boot from

4. Choose from the Kali boot menu:

   - **Live (amd64)** to run without installing

   - **Live with persistence** (if configured)

  

---

  

## 💾 Optional: Enable Persistence

  

To save changes/files across reboots:

- Rufus alone doesn't support persistence

- Use Kali's tools (via Linux) or tools like **Ventoy + persistence plugin**

- Ask for a guide if you want to set this up

  

---

  
 ## ✅ Done!

<!-- testing -->