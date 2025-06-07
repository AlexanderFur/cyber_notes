# 📥 Guide: Download Folder from Python HTTP Server using wget in Termux (Android)

## ✅ Prerequisites

📱 On Android (Termux):
1. Install Termux from F-Droid or trusted source.
2. Open Termux and run:
   >	pkg update && pkg upgrade
   
   >	pkg install wget


🌐 On the Host Computer (Server):

1. Start a simple HTTP server from the directory you want to share:
  > 	python3 -m http.server 8000

2. This shares the current folder via http://< host-ip >:8000/

3. Ensure your phone and computer are on the same Wi-Fi network.


##  📱 On Your Android Phone (Termux):

Step 1: Find the Server’s IP Address
- On the host computer, run:

>	ipconfig   (Windows CMD)

- Look for something like 192.168.x.x
- Test it on your phone’s browser: http://192.168.x.x:8000/

Step 2: Download All Contents with wget:

In Termux:
>	wget -r -np -nH --cut-dirs=0 http://192.168.x.x:8000/

Explanation:
- -r: recursively download files
- -np: no parent
- -nH: no host directory
- --cut-dirs=0: keep full path structure

Optional: Save to a Specific Folder
>	mkdir -p ~/downloads_from_server

>	cd ~/downloads_from_server

>	wget -r -np -nH --cut-dirs=0 http://192.168.x.x:8000/

To Resume Interrupted Download
>	wget -c -r -np -nH --cut-dirs=0 http://192.168.x.x:8000/

---

## 🔒 Troubleshooting
- 403 Forbidden → Check if directory listing is allowed.
- Connection refused → Ensure server is running and firewall allows port 8000.
- Make sure both devices are on the same network.

---


