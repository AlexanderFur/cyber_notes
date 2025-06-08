# 🔐 Connect to WSL Kali Linux from Samsung S24+ via JuiceSSH

  

## 🧰 Part 1: Set Up WSL Kali on Windows 11

  

### 1. Install WSL and Kali Linux

```bash

wsl --install -d kali-linux

```

  

### 2. Update Kali and Install SSH

```bash

sudo apt update && sudo apt install -y openssh-server

```

  

### 3. Configure SSH

```bash

sudo nano /etc/ssh/sshd_config

```

Ensure:

```

PermitRootLogin yes

PasswordAuthentication yes

```

  

### 4. Set a User Password

```bash

passwd

```

  

### 5. Start SSH Server

```bash

sudo service ssh start

```

  

---

  

## 🌐 Part 2: Make Kali Accessible from Network

  

### 6. Get Windows Host IP

```bash

ipconfig

```

  

Use the IPv4 address under your active adapter.

  

### 7. Forward Port to WSL

```powershell

netsh interface portproxy add v4tov4 listenport=2222 listenaddress=0.0.0.0 connectport=22 connectaddress=127.0.0.1

```

  

---

  

## 📱 Part 3: Connect from Samsung Galaxy S24+ with JuiceSSH

  

### 8. Install JuiceSSH on Your Phone

  

### 9. Add a New Connection

- **Nickname**: Kali WSL

- **Type**: SSH

- **Address**: (Your PC's IP, e.g. 192.168.1.100)

- **Port**: 2222

- **Username**: (Your Kali username)

- **Auth Type**: Password or Key

- **Password**: (if using password)

  

---

  

## 🧯 Troubleshooting Connection Error 1005

  

### ✅ Step-by-Step Troubleshooting Guide

  

#### 1. Ensure Same Network

Both PC and phone must be on the same Wi-Fi.

  

#### 2. Confirm Correct IP

Run:

```bash

ipconfig

```

Use the **IPv4 address** under your main adapter.

  

#### 3. Allow Port 2222 in Firewall

- Open `wf.msc`

- Create a new inbound rule for TCP port 2222 (and optionally outbound)

  

#### 4. Verify Port Forwarding

```powershell

netsh interface portproxy show all

```

Should show:

```

0.0.0.0:2222 -> 127.0.0.1:22

```

  

#### 5. Test Locally

From Windows:

```bash

ssh your-user@localhost -p 22

```

  

From another device:

```bash

ssh your-user@192.168.1.100 -p 2222

```

  

#### 6. Restart SSH in Kali

```bash

sudo service ssh restart

```

  

#### 7. Check Listening Port

```bash

netstat -an | find "2222"

```

  

Should show:

```

TCP 0.0.0.0:2222  0.0.0.0:0  LISTENING

```

  

#### 8. Temporarily Disable Windows Firewall (for testing)

Turn off **Private Network Firewall** to test.

  

---

  

✅ If all checks pass, you should now be able to connect via JuiceSSH from your Samsung Galaxy S24+ to Kali in WSL.