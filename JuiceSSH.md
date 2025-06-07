# Connect Samsung Galaxy S24+ to Windows 11 via SSH Using JuiceSSH

## ✅ Overview

You’ll be doing the following:

1. Enable SSH server on your Windows 11 PC.
2. Find your Windows PC's local IP address.
3. Set up Windows Firewall to allow SSH connections.
4. Install and configure JuiceSSH on your Galaxy S24+.
5. Connect to your PC from your phone.

---

## 🖥️ PART 1: Enable SSH on Your Windows 11 PC

### 🔹 Step 1.1: Install OpenSSH Server
1. Press `Win + I` to open **Settings**.
2. Go to **System > Optional Features**.
3. In the top, you see **Add an optional feature**: click **View Features**.
4. Search for **OpenSSH Server**.
5. Click **Next** > **Add**.

> 🕒 Wait for installation to finish.

### 🔹 Step 1.2: Start the SSH Server
1. Press `Win + S`, type **Services**, and open it.
2. Find **OpenSSH SSH Server** in the list.
3. Right-click it > **Properties**.
4. Set **Startup type** to **Automatic**.
5. Click **Start**, then **Apply** and **OK**.

---

## 🌐 PART 2: Find Your Windows IP Address

### 🔹 Step 2.1: Get Your Local IP
1. Press `Win + R`, type `cmd`, and press **Enter**.
2. In the Command Prompt, type:
   
   >	ipconfig

3. Look for **IPv4 Address** under your active network adapter.  
   Example: `192.168.1.100`

> 💡 Save this IP; you’ll use it in JuiceSSH.

---

## 🔥 PART 3: Allow SSH Through the Windows Firewall

### 🔹 Step 3.1: Add SSH Rule
1. Press `Win + S`, type **Windows Defender Firewall with Advanced Security**, and open it.
2. Click **Inbound Rules** (on the left).
3. In **Inbound Rules**, click **New Rule...**
4. Choose:
   - **Type**: Port
   - **Protocol**: TCP
   - **Port**: `22`
1. Click **Next** > **Allow the connection** > **Next**.
2. Apply to **Private** and **Domain** networks (not Public unless needed). Click **Next**.
3. Name the rule something like **SSH Server**.

---

## 📱 PART 4: Install and Configure JuiceSSH on Samsung Galaxy S24+

### 🔹 Step 4.1: Install JuiceSSH
1. Open **Google Play Store**.
2. Search for **JuiceSSH** and install it.

### 🔹 Step 4.2: Create an Identity (optional but recommended)
1. Open JuiceSSH.
2. Tap the **Manage Connections** > **Identities** > `+` (plus).
3. Fill in:
   - **Nickname**: Windows
   - **Username**: Your Windows account username  
     _(You can find it in `C:\Users\YourName`)_
   - **Password**: Your Windows password

> 🔐 You can also use private key authentication, but password is easier to start with.

---

## 🔗 PART 5: Create the SSH Connection in JuiceSSH

### 🔹 Step 5.1: Set Up a New Connection
1. Tap **Connections** > `+` (plus icon).
2. Fill in:
   - **Nickname**: My Windows PC
   - **Type**: SSH
   - **Address**: `192.168.x.x` (from earlier)
   - **Port**: `22` (default)
   - **Identity**: The one you created earlier

3. Tap **Save**.

---

## 🚀 PART 6: Connect!

1. Tap the saved connection in JuiceSSH.
2. If all goes well, you’ll connect to a command-line interface of your Windows 11 PC.
3. You can now run terminal commands on your PC from your phone!

---

## 🧩 Troubleshooting Tips

- **Connection refused?**
  - Double-check that the SSH server is **running** on your PC.
  - Confirm your PC and phone are on the **same Wi-Fi network**.
- **Timeout errors?**
  - Check firewall settings again.
  - Ensure port **22** is open and allowed.
- **Wrong credentials?**
  - Try logging into Windows to verify your username/password.

---

## 🔒 Optional: Improve Security

- Use **key-based authentication** instead of a password.
- Change the SSH port from 22 to a custom one in the SSH server config.
- Set up **fail2ban** equivalents for Windows (like IPBan).
