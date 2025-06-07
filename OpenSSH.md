# Windows
## Installing SFTP/SSH Server

Go to Settings > System > Optional features and click on View features.
Locate “OpenSSH server” feature, select it, click Next, and then click Add.

Binaries are installed to %WINDIR%\System32\OpenSSH. Configuration file (sshd_config) and host keys are installed to %ProgramData%\ssh (only after the server is started for the first time).

---
## Configuring SSH server

- Allow incoming connections to SSH server in Windows Firewall:
    
	- When installed as an optional feature, the firewall rule “OpenSSH SSH Server (sshd)” should have been created automatically. If not, proceed to create and enable the rule as follows.
    
	- Either run the following PowerShell command as the Administrator:  
      
    >	New-NetFirewallRule -Name sshd -DisplayName 'OpenSSH SSH Server' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22 -Program "C:\Windows\System32\OpenSSH\sshd.exe"  
    
    Replace C:\Windows\System32\OpenSSH\sshd.exe with the actual path to the sshd.exe (C:\Program Files\OpenSSH\ssh.exe, had you followed the manual installation instructions above).
	    
	- or go to Windows Security > Firewall & network protection[1](https://winscp.net/eng/docs/guide_windows_openssh_server#fn1) > Advanced Settings > Inbound Rules and add a new rule for port 22.
	    
- Start the service and/or configure automatic start:
	- Go to Control Panel > System and Security > Windows Tools (Administrative Tools on Windows 10 and older) and open Services. Locate OpenSSH SSH Server service.
	    
	- If you want the server to start automatically when your machine is started: Go to Action > Properties (or just double-click the service). In the Properties dialog, change Startup type to Automatic and confirm.
	    
	- Start the OpenSSH SSH Server service by clicking the Start the service link or Action > Start in the menu.
---

## Setting up SSH public key authentication

- Create the .ssh folder (for the authorized_keys file) in your Windows account profile folder (typically in C:\Users\username\.ssh).

- For permissions to the .ssh folder and the authorized_keys file, what matters are Windows ACL permissions, not simple *nix permissions. Set the ACL so that the respective Windows account is the owner of the folder and the file and is the only account that has a write access to them. The account that runs OpenSSH SSH Server service (typically SYSTEM or sshd) needs to have read access to the file.

- Though, with the default Win32-OpenSSH configuration there is an exception set in sshd_config for accounts in Administrators group. For these, the server uses a different location for the authorized keys file: %ALLUSERSPROFILE%\ssh\administrators_authorized_keys (i.e. typically C:\ProgramData\ssh\administrators_authorized_keys).
---
## Connecting to the server
### Finding Host Key

Before the first connection, find out the fingerprint of the server’s host key by using ssh-keygen.exe for each file.

In Windows command-prompt (run as Administrator), use:

>	for %f in (%ProgramData%\ssh\ssh_host_*_key) do @%WINDIR%\System32\OpenSSH\ssh-keygen.exe -l -f "%f"

Replace %WINDIR%\System32 with %ProgramFiles%, if appropriate.

In PowerShell (run as Administrator), use:

>	Get-ChildItem $env:ProgramData\ssh\ssh_host_*_key | ForEach-Object { . $env:WINDIR\System32\OpenSSH\ssh-keygen.exe -l -f $_ }
   
 *Replace $env:WINDIR\System32 with $env:ProgramFiles, if appropriate.*

You will get an output like this:

```
C:\Windows\System32\OpenSSH>for %f in (%ProgramData%\ssh\ssh_host_*_key) do @%WINDIR%\System32\OpenSSH\ssh-keygen.exe -l -f "%f"1024 SHA256:K1kYcE7GHAqHLNPBaGVLOYBQif04VLOQN9kDbiLW/eE martin@example (DSA)
256 SHA256:7pFXY/Ad3itb6+fLlNwU3zc6X6o/ZmV3/mfyRnE46xg martin@example (ECDSA)
256 SHA256:KFi18tCRGsQmxMPioKvg0flaFI9aI/ebXfIDIOgIVGU martin@example (ED25519)
2048 SHA256:z6YYzqGiAb1FN55jOf/f4fqR1IJvpXlKxaZXRtP2mX8 martin@example (RSA)  
```
### Connecting

Start WinSCP. [Login dialog](https://winscp.net/eng/docs/ui_login) will appear. On the dialog:

- Make sure New site node is selected.
- On New site node, make sure the SFTP protocol is selected.
- Enter your machine/server IP address (or a hostname) into the Host name box    
- Enter your Windows account name to the User name box. It might have to be entered in the format user@domain if running on a domain.
- For a public key authentication:
	- Press the Advanced button to open [Advanced site settings dialog](https://winscp.net/eng/docs/ui_login_advanced) and go to [SSH > Authentication page](https://winscp.net/eng/docs/ui_login_authentication).
	- In Private key file box select your private key file.
	- Submit Advanced site settings dialog with the OK button.
- For a password authentication:
	- Enter your Windows account password to the Password box.
	- If your Windows account does not have a password, you cannot authenticate with the password authentication (i.e. with an empty password), you need to use the public key authentication.
- Save your site settings using the Save button.
- Login using Login button.
- [Verify the host key](https://winscp.net/eng/docs/ssh_verifying_the_host_key) by comparing fingerprints with those collected before (see above).

If you cannot authenticate to the server and use Windows 10 _Developer mode_, make sure that your OpenSSH server does not conflict with an internal SSH server used by the _Developer mode_. You may need to turn off the _SSH Server Broker_ and _SSH Server Proxy_ Windows services. Or run your OpenSSH server on a different port than 22.

---