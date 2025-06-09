  

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

