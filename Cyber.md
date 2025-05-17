# HyperV
## Installation
Copy the code, select "All files" and Save as hyperv.bat. Run as admin

```
pushd "%~dp0"

dir /b %SystemRoot%\servicing\Packages\*Hyper-V*.mum >hyper-v.txt

for /f %%i in ('findstr /i . hyper-v.txt 2^>nul') do dism /online /norestart /add-package:"%SystemRoot%\servicing\Packages\%%i"

del hyper-v.txt

Dism /online /enable-feature /featurename:Microsoft-Hyper-V -All /LimitAccess /ALL

pause
```

---
## VMCreate.exe.config
Save the code as "VMCreate.exe.config and save it in 
>	C:\Program Files\Hyper-V

to fix an error where you can't "quick create"
```
<configuration>
  <runtime>
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
      <dependentAssembly>
        <assemblyIdentity name="Newtonsoft.Json" publicKeyToken="30ad4fe6b2a6aeed" culture="neutral" />
        <bindingRedirect oldVersion="0.0.0.0-12.0.0.0" newVersion="13.0.0.0" />
      </dependentAssembly>
    </assemblyBinding>
  </runtime>
</configuration>
```

---
## Allocate more resources 
Type these commands into cmd(Admin):

>	$ bcdedit /set hypervisorschedulertype classic

>	$ bcdedit /enum

---
## Move Virtual Disk
- Press Ctrl+x on the folder containing the virtual disk -file(s)
	- Paste it in your desired folder
	-  Right click your virtual disk -file and click "copy as path"
- Go to Hyper V -manager
	- Right click the virtual machine > click "Settings.."
	- Go to "HardDive" > paste the full, new path of the virtual disk
	- Remove the """'s" > "Apply" > "OK" 

---
## Hotkeys
### Virtual Machine Connection Key Combinations
With Hyper-V we now have the "Virtual Machine Connection" to use when interacting with a virtual machine (unlike Virtual Server which used "VMRC").  The Virtual Machine Connection window wraps the standard Remote Desktop Client and uses this to connect to the virtual machine.  As such - we are now using the Remote Desktop key combinations.  Here is a brief summary of the key combinations that can be used with the Virtual Machine Connection:

| Standard Windows Key combination | Virtual Machine Connection Key Combination | Explanation                                                                       |
| -------------------------------- | ------------------------------------------ | --------------------------------------------------------------------------------- |
| CTRL + ALT + DEL                 | CTRL + ALT + END                           | Displays the Task Manager or Windows Security dialog box on Windows (or logs in). |
| ALT + TAB                        | ALT + PAGE UP                              | Switches between programs from left to right.                                     |
| ALT + ESC                        | ALT + INSERT                               | Cycles through the programs in the order they were started.                       |
| CTRL + ESC                       | ALT + HOME                                 | Displays the Windows Start menu.                                                  |
| N/A                              | CTRL + ALT + PAUSE                         | Changes the Virtual Machine Connection window to / from full screen mode.         |
| N/A                              | CTRL + ALT + LEFT ARROW                    | Releases mouse and keyboard focus from the Virtual Machine Connection window.     |

#### Some extra things to know about Virtual Machine Connection key combinations:

By default the standard Windows key combinations do not get sent to the virtual machine, unless you are in full screen mode.  You can change this so that they are always sent to the virtual machine (if the Virtual Machine Connection has focus) by going to the Hyper-V Manager and selecting Hyper-V Server Settings... and then Keyboard and selecting the Use on the virtual machine option.  I always enable this setting.

Note: CTRL + ALT + DEL will always go to the physical computer - so you need to use CTRL + ALT + END no matter what you select for a setting here.
You can change the release key combination (CTRL + ALT + LEFT ARROW) by going to the Hyper-V Manager and selecting Hyper-V Server Settings... and then Release Key and selecting one of the options from the drop down (I usually change my release key combination to be CTRL + ALT + SHIFT as I find it easier to type).

If you use the Virtual Machine Connection under an existing Remote Desktop Connection (not recommended - but I do it all the time) the Remote Desktop Connection will grab all of these key combinations before the Virtual Machine Connection gets to see them (even the release key combination).  To deal with this you will need to change the Hyper-V Server setting to allow Windows key combinations to go to the virtual machine, change the release key combination to something other than CTRL + ALT + LEFT ARROW, and use the toolbar button or Action menu of the Virtual Machine Connection to send CTRL + ALT + DEL to the virtual machine.

-------------------------------------------------------------------------
# GitHub

## Create a new repository on the command line:

>	git init 

>	git add < files >

>	git commit -m "first commit"

>	git branch -M main

>	git remote add origin https://github.com/AlexanderFur/obsidian_notes.git

>	git push -u origin main

---
## …or push an existing repository from the command line

Replace URL with the correct one
>	git remote add origin https://github.com/AlexanderFur/obsidian_notes.git 

>	git branch -M main

>	git push -u origin main

---
## Everyday use:
>	git status 

>	git pull

>	git add <filename (or type a quotationless '.' for all of the current dir)>

>	git commit -m < Message >

>	git push

To see and compare all changes:

>	 git diff HEAD

------------------------------------------------------
## SSH
### Checking for existing keys
1. Open Terminal.
2. Enter
>	ls -al ~/.ssh

3. Check the directory listing to see if you already have a public SSH key. By default, the filenames of supported public keys for GitHub are one of the following.
- id_rsa.pub
- id_ecdsa.pub
- id_ed25519.pub

4. Either generate a new SSH key or upload an existing key.
	- If you don't have a supported public and private key pair, or don't wish to use any that are available, generate a new SSH key.
	
	- If you see an existing public and private key pair listed (for example, id_rsa.pub and id_rsa) that you would like to use to connect to GitHub, you can add the key to the ssh-agent.
	
	- For more information about generation of a new SSH key or addition of an existing key to the ssh-agent, see Generating a new SSH key and adding it to the ssh-agent.

### Generate SSH key
1. Open Terminal
2. Paste the text below, replacing the email used in the example with your GitHub email address.
>	ssh-keygen -t ed25519 -C "your_email@example.com"

>[!NOTE]
>If you are using a legacy system that doesn't support the Ed25519 algorithm, use:
>
>	ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

This creates a new SSH key, using the provided email as a label.
>	> Generating public/private ALGORITHM key pair.

When you're prompted to "Enter a file in which to save the key", you can press Enter to accept the default file location. Please note that if you created SSH keys previously, ssh-keygen may ask you to rewrite another key, in which case we recommend creating a custom-named SSH key. To do so, type the default file location and replace id_ALGORITHM with your custom key name.
>	> Enter a file in which to save the key (/home/YOU/.ssh/id_ALGORITHM):[Press enter]

3. At the prompt, type a secure passphrase. For more information, see Working with SSH key passphrases.
> 	Enter passphrase (empty for no passphrase): [Type a passphrase]
> 	Enter same passphrase again: [Type passphrase again]



# Python
## ABC -Formelen

'''
```
# Dette programmet kan løse annengradslikninger ved å oppgi A, B, og C

  

import math

  

print("Programmet skal løse andregradslikningen ")

print("ax**2 + bx + c = 0 ved hjelp av abc-formelen.")

print("Skriv inn verdiene for a, b og c.")

  

a = float(input("a = "))

b = float(input("b = "))

c = float(input("c = "))

  

d = b**2 - 4*a*c  # diskriminanten

  

# Hvis diskriminanten er positiv, har vi to forskjellige løsninger

if d > 0:

    x1 = round((-b + math.sqrt(d)) / (2 * a), 2)

    x2 = round((-b - math.sqrt(d)) / (2 * a), 2)

    print("Løsningen på andregradslikningen er:")

    print(f"x1 = {x1} og x2 = {x2}")

  

# Hvis diskriminanten er null, har vi én løsning (to like løsninger)

elif d == 0:

    x1 = round(-b / (2 * a), 2)

    print("Det er én løsning (to like løsninger):")

    print(f"x1 = x2 = {x1}")

  

# Hvis diskriminanten er negativ, finnes det ingen reelle løsninger

else:

    # Vi kan beregne de komplekse løsningene ved hjelp av imaginære tall

    real_part = round(-b / (2 * a), 2)

    imaginary_part = round(math.sqrt(-d) / (2 * a), 2)

    print("Det finnes ingen reelle løsninger, men de komplekse løsningene er:")

    print(f"x1 = {real_part} + {imaginary_part}i")

    print(f"x2 = {real_part} - {imaginary_part}i")

```

----------------------------------------------

# Kali Linux
## General

### Shell Scripts
#### Connect to THM -VPN

	#!/bin/zsh
	
	# Run OpenVPN with the specified configuration file
	sudo openvpn /home/kali/Downloads/MorraDiStjeler.ovpn

---
#### Ultimate Update

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

---
### Uninstall a .deb -file
To uninstall a .deb file using the command line, you can use the "dpkg" command and the "--purge" option.

For example:

>	$ sudo dpkg --purge package_name 

This will remove the package and its configuration files. If you just want to remove the package, but keep its configuration files, you can use the "--remove" option instead of "--purge".

>	$ sudo dpkg --remove package_name 

If you want to remove the package and its dependencies that are no longer needed, you can use the "apt-get" command with the "remove" option.

>	$ sudo apt-get remove package_name 

This will remove the package, but it will keep the configuration files. If you want to remove the package and its configuration files, you can use the "purge" option instead of "remove".

>	$ sudo apt-get purge package_name 

---
### Make Executable
Make it runable for all users:

>	$ sudo chmod +x <filename.extention>

---
### Make .sh runable from anywhere
>	$ sudo mv '/Full/path/including/filename.sh' /usr/local/bin/

----
### Corrupt .zsh_history -Fix
- **Run these commands:**

>	$ cd ~

>	$ mv .zsh_history .zsh_history_bad

>	$ strings .zsh_history_bad > .zsh_history

>	$ fc -R .zsh_history

>	$ rm ~/.zsh_history_bad

---
### Commands - Chrome
 
- Install dependencies
>	$ sudo apt install wget ca-certificates curl

- Download Chrome
>	$ wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb

- Install
>	$ Sudo apt install ./google-chrome-stable_current_amd64.deb

- Run this if there's any problems*
>	$ Sudo apt install -f

- Any problems running Chrome; Run this
>	$ google-chrome --no-sandbox

- Run Chrome from terminal
>	$ google-chrome

- Run if there are any dependencies issues
>	$ sudo apt install libu2f-udev

- Run if there are any problems with installation*
>	$ sudo apt –fix-broken install

---
### Extract .tar
#### Extract '.tar.gz' -files

Type: 
>	man tar 

for more information, but this command should do the trick:

>	sudo tar -xvzf community_images.tar.gz

To explain a little further, tar collected all the files into one package, community_images.tar. The gzip program applied compression, hence the ".gz" extension. So the command does a couple things:

- f: this must be the last flag of the command, and the tar file must be immediately after. It tells tar the name and path of the compressed file.
- z: tells tar to decompress the archive using gzip
- x: tar can collect files or extract them. x does the latter.
- v: makes tar talk a lot. Verbose output shows you all the files being extracted.
- To extract into a custom folder, add the "-C" -option with a folder name of your choice:

>	tar -xvzf community_images.tar.gz -C some_custom_folder_name

---
#### Extract '.tar.xz' -files

Install "xz" using the 
>	dnf install xz

on a CentOS/RHEL/Fedora Linux.

Debian/Ubuntu Linux users
>	sudo apt install xz-utils 

To decompress filename. tar. xz file run: 
>	sudo xz -d -v 'filename'.tar.xz

---
#### Extract '.tar' -files
To untar a file in Linux, use the
>	sudo tar -xvf 'filename.tar'

This command extracts the contents of tar files, which are commonly used in Linux for file compression.

---
### Oh My Zsh!
#### Installation (Curl)

>	sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

#### Uninstallation
>	uninstall_oh_my_zsh
---
#### Plugins

##### zsh-auto-suggestions
1. Clone this repository into $ZSH_CUSTOM/plugins (by default ~/.oh-my-zsh/custom/plugins)
>	git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

2. Add the plugin to the list of plugins for Oh My Zsh to load (inside ~/.zshrc):

plugins=( 
    # other plugins...
    zsh-autosuggestions
)


3. Start a new terminal session. 

>[!tip] Tutorial
>	https://www.youtube.com/watch?v=DmpMgTL6R9A

---
##### zsh-synax-highlighting
1. Clone this repository in oh-my-zsh's plugins directory:
>	git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

2. Activate the plugin in ~/.zshrc:
```
plugins=( [plugins...] zsh-syntax-highlighting)
```

>[!TIP] Tutorial
>	https://www.youtube.com/watch?v=DmpMgTL6R9A

---

### Change username in Kali Linux

>[!NOTE] Has to be logged in as root. To be able to do this, set a password for root:
>	sudo passwd root
>	
> Then log out and back in with root username, and the password you have created

1. To get the use id of a user:
>	cat /etc/passwd | grep oldusername

Replace the ‘oldusername’ with the name of the user you want to use.

![[pic1.png]]

This will display us a few details of the user along with the userid.

2. To change the Username
To change the username of an existing user, use the usermod command with the "-l" option:
>	usermod -l newusername oldusername

Replace the ‘oldusername’ with the name of the user you want to change.
- oldusername: The current username you want to change.
- newusername: The new username you wish to assign to the user.

![[pic2.png]]

This command will change the username of the oldusername to the newusername but will not change the files and userID of the user.

3. To change the UserID
We use ‘usermod’ command along with ‘-u’ parameter in order to change the userid of a particular user.
>	usermod -u 1234 newusername

- Replace the newusername with the username you want to change the id of.
- Replace 1234 with the id you want to set for the user.
![[pic3.png]]

This command will change the userid of the user from the default one to 1234.

 4. Conclusion
Changing usernames and User IDs in Kali Linux using the usermod command is a straightforward process that provides flexibility in managing user accounts. By following the steps outlined in this guide, you can efficiently modify usernames and UIDs without disrupting system functionality. Always verify your changes and ensure proper file ownership to maintain system integrity.
## Hotkeys
### General Shortcuts
| Keyboard Shortcuts | Description                                               |
| ------------------ | --------------------------------------------------------- |
| Ctrl + Alt + T     | Open a new command line terminal.                         |
| Alt + F4           | Close current window                                      |
| Alt + F11          | Maximize current window.                                  |
| PrtSc              | Take a screenshot.                                        |
| Super + PrtSc      | Open Kazam (screenshot/screencast tool)                   |
| Alt + F3           | Open Application Finder                                   |
| Ctrl + N           | New                                                       |
| Ctrl + X           | Cut                                                       |
| Ctrl + C           | Copy                                                      |
| Ctrl + Z           | This shortcut is used to undo.                            |
| Ctrl + S           | Save                                                      |
| Ctrl + Q           | This shortcut is used to Quit.                            |
| F1                 | this shortcut is used to online help.                     |
| F10                | Left click menu or cursor.                                |
| Alt + F1           | Using this shortcut, we can open the window.              |
| Alt + F2           | Using this shortcut, we can open the command window.      |
| Alt + F7           | Using this shortcut, we can move the window.              |
| Alt + Space        | Using this shortcut, we can activate the window menu.     |
| Alt + F10          | Toggle maximization state.                                |
| Ctrl + Alt + D     | Using this shortcut, we can minimize all windows.         |
| Alt + F8           | With the help of this shortcut, we can resize the window. |

---
### Screenshot shortcuts

| Keyboard shortcut           | Description                                                                            |
| --------------------------- | -------------------------------------------------------------------------------------- |
| Print Screen                | Using this shortcut button, we can take a screenshot.                                  |
| Ctrl + Print Screen         | Screenshot to clipboard                                                                |
| Alt + Print Screen          | Using this shortcut, we can take a screenshot of a window.                             |
| Ctrl + Shift + Print Screen | With the help of this shortcut, we can take a screenshot of an area to the clipboard.  |
| Ctrl + Alt + Print Screen   | With the help of this shortcut, we can take a screenshot of a window to the clipboard. |
| Shift + Ctrl + Alt + R      | Using this shortcut, we can record a screencast.                                       |

---
### Terminal shortcuts
| Keyboard shortcut | Description                         |
| ----------------- | ----------------------------------- |
| Ctrl + D          | Close terminal window               |
| Ctrl + +          | This shortcut is used to Zoom in.   |
| Ctrl + -          | This shortcut is used to Zoom out.  |
| Ctrl + L          | Clear terminal                      |
| Ctrl + C          | Cancel currently running command.   |
| Ctrl + A          | Move cursor to beginning of line.   |
| Ctrl + B          | Move cursor backward one character. |
| Ctrl + E          | Move cursor to end of line.         |
| Ctrl + F          | Move cursor forward one character.  |
| Alt+Shift+S       | Name a tab                          |
| Ctrl + Tab        | Switch between Tabs                 |
| Ctrl + Shit + P   | Preferences...                      |
| Ctrl + u          | Empty line                          |

---
### Workspace shortcuts
| Keyboard shortcut      | Description                                                             |
| ---------------------- | ----------------------------------------------------------------------- |
| Shift + Ctrl + Alt + ← | Using this shortcut, we can move the window one workspace to the left.  |
| Shift + Ctrl + Alt + → | Using this shortcut, we can move the window one workspace to the right. |
| Shift + Ctrl + Alt + ↑ | Using this shortcut, we can move the window one workspace up.           |
| Shift + Ctrl + Alt +↓  | Using this shortcut, we can move the window one workspace down.         |

---
## Hydra
### Post Web Form
#### Flags

We can use Hydra to brute force web forms too. You must know which type of request it is making; GET or POST methods are commonly used. You can use your browser’s network tab (in developer tools) to see the request types or view the source code.

>	$ sudo hydra < username > < wordlist > 10.10.6.152 http-post-form "< path >:< login_credentials >:< invalid_response >"

| Flag                  | Description                                                                            |
| --------------------- | -------------------------------------------------------------------------------------- |
| -l(L)                 | the username for (web form) login                                                      |
| -P                    | the password list to use                                                               |
| http-post-form        | the type of the form is POST                                                           |
| < path >              | the login page URL, for example, login.php                                             |
| < login_credentials > | the username and password used to log in, for example, username=^USER^&password=^PASS^ |
| < invalid_response >  | part of the response when the login fails                                              |
| -V                    | verbose output for every attempt                                                       |

Below is a more concrete example Hydra command to brute force a POST login form:

>	$ sudo hydra -l < username > -P < wordlist > 10.10.6.152 http-post-form "/:username=^USER^&password=^PASS^:F=incorrect" -V

---
### SSH
#### Flags
| Flag   | Description                            |
| ------ | -------------------------------------- |
| -l (L) | Specifies the (SSH) username for login |
| -P     | Indicates a list of passwords          |
| -t     | Sets the number of threads to spawn    |

For example,
>	$ hydra -l root -P passwords.txt 10.10.63.161 -t 4 ssh

will run with the following arguments:  
  
- Hydra will use root as the username for ssh  
- It will try the passwords in the passwords.txt file  
- There will be four threads running in parallel as indicated by -t 4

---
## Nmap
### Scans
#### Full scan - TCP connect
For monitoring:
> 	$ sudo nmap -A -p- -T4 -sT -Pn

---
#### Full Scan - TCP SYN
For simulation/pentesting:
> 	$ sudo nmap -A -p- -T4 -sS -Pn

------------------------------------------------------------
## Mousepad
### Open files in separate windows
>	mousepad < file name1 > | mousepad < file name2 >

# Exploits and Vulnerabilities
## CVE-2025-29927 - Next.js

### Description.
Next.js is a React framework for building full-stack web applications. Prior to 14.2.25 and 15.2.3, it is possible to bypass authorization checks within a Next.js application, if the authorization check occurs in middleware. If patching to a safe version is infeasible, it is recommend that you prevent external user requests which contain the x-middleware-subrequest header from reaching your Next.js application. This vulnerability is fixed in 14.2.25 and 15.2.3.



Add header to get-request (right under "Host" in BurpSuite):
>	x-middleware-subrequest: middleware


### Patches:
- Next.js 15.x should upgrade to 15.2.3
- Next.js 14.x should upgrade to 14.2.25
- Next.js 13.x should upgrade to 13.5.9
- Next.js 12.x should upgrade to 12.3.5


>[!LINK] Link  
>	https://nvd.nist.gov/vuln/detail/CVE-2025-29927

------------------------------------------------------

# Logs 
## Type of Logs
>[!info]
>There can be various other types of logs depending on the different applications and the services they provide.

| Log Type         | Usage                                                                                                                                                                                            | Example                                                                                                                                           |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| System Logs      | The system logs can be helpful in troubleshooting running issues in the OS. These logs provide information on various operating system activities.                                               | - System Startup and shutdown events<br>- Driver Loading events<br>- System Error events<br>- Hardware events                                     |
| Security Logs    | The security logs help detect and investigate incidents. These logs provide information on the security-related activities in the system.                                                        | - Authentication events<br>- Authorization events<br>- Security Policy changes events<br>- User Account changes events - Abnormal Activity events |
| Application Logs | The application logs contain specific events related to the application. Any interactive or non-interactive activity happening inside the application will be logged here.                       | - User Interaction events<br>- Application Changes events<br>- Application Update events<br>- Application Error events                            |
| Audit Logs       | The Audit logs provide detailed information on the system changes and user events. These logs are helpful for compliance requirements and can play a vital role in security monitoring as well.  | - Data Access events<br>- System Change events<br>- User Activity events<br>- Policy Enforcement events                                           |
| Network Logs     | Network logs provide information on the network’s outgoing and incoming traffic. They play crucial roles in troubleshooting network issues and can also be handy during incident investigations. | - Incoming Network Traffic events<br>- Outgoing Network Traffic events<br>- Network Connection Logs - Network Firewall Logs                       |
| Access Logs      | The Access logs provide detailed information about the access to different resources. These resources can be of different types, providing us with information on their access.                  | - Webserver Access Logs<br>- Database Access Logs - Application Access Logs<br>- API Access Logs                                                  |

--------------------------------

# Visual Studio Code
## Hotkeys
### Debugging shortcuts

- Start Debugging: F5
    
- Stop Debugging: Shift+F5
    
- Step Over: F10
    
- Step Into: F11
    
- Step Out: Shift+F11
    
- Toggle Breakpoint: F9

---
### Editing shortcuts
- Cut Line: Ctrl+X
    
- Copy Line: Ctrl+C
    
- Move Line Up/Down: Alt+Up / Alt+Down
    
- Duplicate Line: Shift+Alt+Up / Shift+Alt+Down
    
- Delete Line: Ctrl+Shift+K
    
- Undo: Ctrl+Z
    
- Redo: Ctrl+Y
    
- Find: Ctrl+F
    
- Replace: Ctrl+H
    
- Find Next/Previous: F3 / Shift+F3
    
- Select All Occurrences: Ctrl+Shift+L
    
- Select Word: Ctrl+D

---
### Emmet shortcuts
- Expand Abbreviation: Ctrl+E / Tab
    
- Wrap with Abbreviation: Ctrl+Shift+A

---
### General shortcuts
- Command Palette: Ctrl+Shift+P / F1
    
- Open File: Ctrl+P
    
- New File: Ctrl+N
    
- Save: Ctrl+S
    
- Save As: Ctrl+Shift+S
    
- Close Editor: Ctrl+W
    
- Close Folder: Ctrl+K F
    
- Split Editor: Ctrl+\

---
### Integrated Git shortcuts
- Open Git: Ctrl+Shift+G
    
- Commit: Ctrl+Enter
    
- Stage Changes: Ctrl+Shift+U

---
### Multi-Cursor & Selection shortcuts
- Add Cursor Above/Below: Ctrl+Alt+Up / Ctrl+Alt+Down
    
- Add Cursor to Line Ends: Ctrl+Shift+L
    
- Select Next Occurrence: Ctrl+D
    
- Select All Occurrences: Ctrl+Shift+L
    
- Add Selection to Next Find Match: Ctrl+D
---
### Navigation Shortcuts
- Go to Line: Ctrl+G
    
- Go to File: Ctrl+P
    
- Go to Symbol: Ctrl+Shift+O
    
- Show All Symbols: Ctrl+T
    
- Go to Definition: F12
    
- Peek Definition: Alt+F12
    
- Go to References: Shift+F12
---
### Terminal shortcuts
- New Terminal: Ctrl+
    
- Focus Next Terminal: Ctrl+PageDown
    
- Focus Previous Terminal: Ctrl+PageUp
    
- Kill Terminal: Ctrl+Shift+ 
---
### View shortcuts
- Toggle Sidebar: Ctrl+B
    
- Toggle Terminal: Ctrl+`
    
- Toggle Full Screen: F11
    
- Zoom In/Out: Ctrl+= / Ctrl+-
    
- Toggle Zen Mode: Ctrl+K Z
    
- Open Settings: Ctrl+,
---
# HTTP Response status codes
## Client Error Responses
400 Bad Request
The server cannot or will not process the request due to something that is perceived to be a client error (e.g., malformed request syntax, invalid request message framing, or deceptive request routing).

401 Unauthorized
Although the HTTP standard specifies "unauthorized", semantically this response means "unauthenticated". That is, the client must authenticate itself to get the requested response.

402 Payment Required
The initial purpose of this code was for digital payment systems, however this status code is rarely used and no standard convention exists.

403 Forbidden
The client does not have access rights to the content; that is, it is unauthorized, so the server is refusing to give the requested resource. Unlike 401 Unauthorized, the client's identity is known to the server.

404 Not Found
The server cannot find the requested resource. In the browser, this means the URL is not recognized. In an API, this can also mean that the endpoint is valid but the resource itself does not exist. Servers may also send this response instead of 403 Forbidden to hide the existence of a resource from an unauthorized client. This response code is probably the most well known due to its frequent occurrence on the web.

405 Method Not Allowed
The request method is known by the server but is not supported by the target resource. For example, an API may not allow DELETE on a resource, or the TRACE method entirely.

406 Not Acceptable
This response is sent when the web server, after performing server-driven content negotiation, doesn't find any content that conforms to the criteria given by the user agent.

407 Proxy Authentication Required
This is similar to 401 Unauthorized but authentication is needed to be done by a proxy.

408 Request Timeout
This response is sent on an idle connection by some servers, even without any previous request by the client. It means that the server would like to shut down this unused connection. This response is used much more since some browsers use HTTP pre-connection mechanisms to speed up browsing. Some servers may shut down a connection without sending this message.

409 Conflict
This response is sent when a request conflicts with the current state of the server. In WebDAV remote web authoring, 409 responses are errors sent to the client so that a user might be able to resolve a conflict and resubmit the request.

410 Gone
This response is sent when the requested content has been permanently deleted from server, with no forwarding address. Clients are expected to remove their caches and links to the resource. The HTTP specification intends this status code to be used for "limited-time, promotional services". APIs should not feel compelled to indicate resources that have been deleted with this status code.

411 Length Required
Server rejected the request because the Content-Length header field is not defined and the server requires it.

412 Precondition Failed
In conditional requests, the client has indicated preconditions in its headers which the server does not meet.

413 Content Too Large
The request body is larger than limits defined by server. The server might close the connection or return an Retry-After header field.

414 URI Too Long
The URI requested by the client is longer than the server is willing to interpret.

415 Unsupported Media Type
The media format of the requested data is not supported by the server, so the server is rejecting the request.

416 Range Not Satisfiable
The ranges specified by the Range header field in the request cannot be fulfilled. It's possible that the range is outside the size of the target resource's data.

417 Expectation Failed
This response code means the expectation indicated by the Expect request header field cannot be met by the server.

418 I'm a teapot
The server refuses the attempt to brew coffee with a teapot.

421 Misdirected Request
The request was directed at a server that is not able to produce a response. This can be sent by a server that is not configured to produce responses for the combination of scheme and authority that are included in the request URI.

422 Unprocessable Content (WebDAV)
The request was well-formed but was unable to be followed due to semantic errors.

423 Locked (WebDAV)
The resource that is being accessed is locked.

424 Failed Dependency (WebDAV)
The request failed due to failure of a previous request.

425 Too Early Experimental
Indicates that the server is unwilling to risk processing a request that might be replayed.

426 Upgrade Required
The server refuses to perform the request using the current protocol but might be willing to do so after the client upgrades to a different protocol. The server sends an Upgrade header in a 426 response to indicate the required protocol(s).

428 Precondition Required
The origin server requires the request to be conditional. This response is intended to prevent the 'lost update' problem, where a client GETs a resource's state, modifies it and PUTs it back to the server, when meanwhile a third party has modified the state on the server, leading to a conflict.

429 Too Many Requests
The user has sent too many requests in a given amount of time (rate limiting).

431 Request Header Fields Too Large
The server is unwilling to process the request because its header fields are too large. The request may be resubmitted after reducing the size of the request header fields.

451 Unavailable For Legal Reasons
The user agent requested a resource that cannot legally be provided, such as a web page censored by a government.

---
## Informational Error Responses
100 Continue
This interim response indicates that the client should continue the request or ignore the response if the request is already finished.

101 Switching Protocols
This code is sent in response to an Upgrade request header from the client and indicates the protocol the server is switching to.

102 Processing Deprecated
This code was used in WebDAV contexts to indicate that a request has been received by the server, but no status was available at the time of the response.

103 Early Hints
This status code is primarily intended to be used with the Link header, letting the user agent start preloading resources while the server prepares a response or preconnect to an origin from which the page will need resources.

---
## Redirection Messages
300 Multiple Choices
In agent-driven content negotiation, the request has more than one possible response and the user agent or user should choose one of them. There is no standardized way for clients to automatically choose one of the responses, so this is rarely used.

301 Moved Permanently
The URL of the requested resource has been changed permanently. The new URL is given in the response.

302 Found
This response code means that the URI of requested resource has been changed temporarily. Further changes in the URI might be made in the future, so the same URI should be used by the client in future requests.

303 See Other
The server sent this response to direct the client to get the requested resource at another URI with a GET request.

304 Not Modified
This is used for caching purposes. It tells the client that the response has not been modified, so the client can continue to use the same cached version of the response.

305 Use Proxy Deprecated
Defined in a previous version of the HTTP specification to indicate that a requested response must be accessed by a proxy. It has been deprecated due to security concerns regarding in-band configuration of a proxy.

306 unused
This response code is no longer used; but is reserved. It was used in a previous version of the HTTP/1.1 specification.

307 Temporary Redirect
The server sends this response to direct the client to get the requested resource at another URI with the same method that was used in the prior request. This has the same semantics as the 302 Found response code, with the exception that the user agent must not change the HTTP method used: if a POST was used in the first request, a POST must be used in the redirected request.

308 Permanent Redirect
This means that the resource is now permanently located at another URI, specified by the Location response header. This has the same semantics as the 301 Moved Permanently HTTP response code, with the exception that the user agent must not change the HTTP method used: if a POST was used in the first request, a POST must be used in the second request.

---
## Server Error Response
500 Internal Server Error
The server has encountered a situation it does not know how to handle. This error is generic, indicating that the server cannot find a more appropriate 5XX status code to respond with.

501 Not Implemented
The request method is not supported by the server and cannot be handled. The only methods that servers are required to support (and therefore that must not return this code) are GET and HEAD.

502 Bad Gateway
This error response means that the server, while working as a gateway to get a response needed to handle the request, got an invalid response.

503 Service Unavailable
The server is not ready to handle the request. Common causes are a server that is down for maintenance or that is overloaded. Note that together with this response, a user-friendly page explaining the problem should be sent. This response should be used for temporary conditions and the Retry-After HTTP header should, if possible, contain the estimated time before the recovery of the service. The webmaster must also take care about the caching-related headers that are sent along with this response, as these temporary condition responses should usually not be cached.

504 Gateway Timeout
This error response is given when the server is acting as a gateway and cannot get a response in time.

505 HTTP Version Not Supported
The HTTP version used in the request is not supported by the server.

506 Variant Also Negotiates
The server has an internal configuration error: during content negotiation, the chosen variant is configured to engage in content negotiation itself, which results in circular references when creating responses.

507 Insufficient Storage (WebDAV)
The method could not be performed on the resource because the server is unable to store the representation needed to successfully complete the request.

508 Loop Detected (WebDAV)
The server detected an infinite loop while processing the request.

510 Not Extended
The client request declares an HTTP Extension (RFC 2774) that should be used to process the request, but the extension is not supported.

511 Network Authentication Required
Indicates that the client needs to authenticate to gain network access.

---
## Successful responses

200 OK
The request succeeded. The result and meaning of "success" depends on the HTTP method:

- GET: The resource has been fetched and transmitted in the message body.
- HEAD: Representation headers are included in the response without any message body.
- PUT or POST: The resource describing the result of the action is transmitted in the message body.
- TRACE: The message body contains the request as received by the server.

201 Created
The request succeeded, and a new resource was created as a result. This is typically the response sent after POST requests, or some PUT requests.

202 Accepted
The request has been received but not yet acted upon. It is noncommittal, since there is no way in HTTP to later send an asynchronous response indicating the outcome of the request. It is intended for cases where another process or server handles the request, or for batch processing.

203 Non-Authoritative Information
This response code means the returned metadata is not exactly the same as is available from the origin server, but is collected from a local or a third-party copy. This is mostly used for mirrors or backups of another resource. Except for that specific case, the 200 OK response is preferred to this status.

204 No Content
There is no content to send for this request, but the headers are useful. The user agent may update its cached headers for this resource with the new ones.

205 Reset Content
Tells the user agent to reset the document which sent this request.

206 Partial Content
This response code is used in response to a range request when the client has requested a part or parts of a resource.

207 Multi-Status (WebDAV)
Conveys information about multiple resources, for situations where multiple status codes might be appropriate.

208 Already Reported (WebDAV)
Used inside a <dav:propstat> response element to avoid repeatedly enumerating the internal members of multiple bindings to the same collection.

226 IM Used (HTTP Delta encoding)
The server has fulfilled a GET request for the resource, and the response is a representation of the result of one or more instance-manipulations applied to the current instance.

---

# Windows
## DISKUTIL
### Fix unallocated disk space
Follow this Video: 
>[!tip] How to add unallocated space to C when Extend Volume is grayed out
>>https://www.youtube.com/watch?v=TTuRDL-guog&ab_channel=TechGuyCharlie

You can also follow the steps below in CMD/Powershell (*admin privilege might be required*):

- Enter the Service
>	$ Diskpart

- List available disks
>	$ List disk

- Use the selected disk
>	$ Select disk number of disk

- Lists available partitions on the selected disk
>	$ List partition

- Selects the given available partition for further use
>	$ Select partition < number of recovery partition >

- Forces the deletion of diskpart
>	$ Delete partition override

---
### Resize removeable volume
   
Watch this Video: 
> [!tip] How to Resize USB Flash Drive (Pendrive) Partition
>> https://www.youtube.com/watch?v=qqlVpKXB6OQ

You can also follow the steps below in CMD/Powershell (*admin privilege might be required):

- Enters the Service
>	$ Diskpart

- Lists available volumes
>	$ List volume

- Selects which of the available
>	$ Select <volume_name>

- Cleans the volume
>	$ Clean

---

# OpenSSH
## Windows
### Installing SFTP/SSH Server

Go to Settings > System > Optional features and click on View features.
Locate “OpenSSH server” feature, select it, click Next, and then click Add.

Binaries are installed to %WINDIR%\System32\OpenSSH. Configuration file (sshd_config) and host keys are installed to %ProgramData%\ssh (only after the server is started for the first time).

---
### Configuring SSH server

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

### Setting up SSH public key authentication

- Create the .ssh folder (for the authorized_keys file) in your Windows account profile folder (typically in C:\Users\username\.ssh).

- For permissions to the .ssh folder and the authorized_keys file, what matters are Windows ACL permissions, not simple *nix permissions. Set the ACL so that the respective Windows account is the owner of the folder and the file and is the only account that has a write access to them. The account that runs OpenSSH SSH Server service (typically SYSTEM or sshd) needs to have read access to the file.

- Though, with the default Win32-OpenSSH configuration there is an exception set in sshd_config for accounts in Administrators group. For these, the server uses a different location for the authorized keys file: %ALLUSERSPROFILE%\ssh\administrators_authorized_keys (i.e. typically C:\ProgramData\ssh\administrators_authorized_keys).
---
### Connecting to the server
#### Finding Host Key

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
#### Connecting

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
# WordPress
## Fixes and how to's
### Korrupt database
Feilmeldingen sier at mySQL har blitt avsluttet på feil måte. Mest sannsynligvis at jeg har slått av pc med prosesser gående. 

>Hvis dere får dette problemet (lokalt, dette skjer ikke i prod) så må dere følge denne videoen:
> https://www.youtube.com/watch?v=84IOtc05TuA](https://www.youtube.com/watch?v=84IOtc05TuA)

---
### Make Cross
#### Step 1: Create the Basic Layout
 Open Elementor
	- Go to your WordPress Dashboard → Pages → Click Edit with Elementor on the page where you want the design.
- Add a Two-Column Section
	- Click the "+" button to add a new section
	- Choose the two-column structure
	- Adjust the left column width (e.g., 30%) and right column width (e.g., 70%) to match the design.
- Add Content to Each Column
	- In the left column add a Heading Widget (e.g., "OM") and Text Editor Widget (e.g., "Neal Ashley Contrad").
	- In the right column, add an Image Widget (for the eyes icon) and some Text Widgets for the description.
	- Below that, add a Contact Form Widget (if you are using a plugin like WPForms or Elementor Forms).

---
#### Step 2: Add the Horizontal Line
- Drag a Divider Widget
	- Find the Divider Widget in Elementor.
	- Drag it above the two-column section (at the top, spanning across both columns).
	- Style the Divider
- Go to the Content tab in the left panel:
	- Set Width to 100%.
	- Set Weight to 1px (or adjust for a thicker line).
	- Set Alignment to Center.
- Go to the Style tab:
	- Change Color to Black (#000000).
	- Change Gap to 0 (so it sticks to the section).
---
#### Step 3: Add the Vertical Line
- Drag Another Divider Widget
	- Add another Divider Widget but place it inside the left column (where the "OM" text is).
	- Make it Vertical Using Rotation
- In the Content tab:
	- Set Width to 2px (or adjust as needed).
	- Set Height to 100px (or more, depending on how tall you want the vertical line).
- In the Advanced tab → Custom Positioning
	- Set Position to Absolute
	- Set Vertical Orientation to Middle.
	- Adjust the left margin to position it correctly.
---
#### Step 4: Adjust Spacing for Proper Alignment
- Set Column Padding/Margin
- Click on the Left Column → Advanced Tab:
	- Add Padding on the right side (to create spacing from the vertical line).
- Click on the Right Column → Advanced Tab:
	- Add Padding on the left side (to ensure text doesn’t touch the vertical line).
- Check Mobile Responsiveness
	- Click the Responsive Mode icon at the bottom.
	- Switch between Tablet and Mobile views.
	- Adjust margins/padding if needed.
---
#### Step 5: Save and Publish
- Click Update to save changes.
- Preview the page to make sure the lines align correctly.
---
#### Optional: Alternative Adjustments
- If the vertical line is not long enough, increase its Height.
- If you want more control, use Custom CSS (see Method 3).
- For more styling, add a Box Shadow to the section for depth.
- Now, you should have a clean crossing line structure that looks like the design in your image!
---
### Make custom roles
Follow the video below:

> [!important] NOTE!
> It is important to check off "edit_theme_options" so the user can edit menus.


[![https://www.youtube.com/watch?v=_HE875kKo3k](https://www.youtube.com/watch?v=_HE875kKo3k "https://www.youtube.com/watch?v=_HE875kKo3k")]

---
### Migrate Website - phpMyAdmin
- Last ned /wp-content og we-config.php fra ønsket side
- Backup site files via File Manager
- Export the site database via phpMyAdmin
---
- Transfer site to new domain 
	- create a database for the new domain (if dont exist)
	- create a domain/subdomain (if dont exist)
	
	- Install Wordpress at new domain
	- Import site database via phpMyAdmin (edit database name and use if needed)
	- Go to {dbname}_options and change siteurl and home to correct address
	- Delete tables from default db (dev)
	
	- Upload/replace wp-content folder in File Manager
	- Update config.php file with correct details
	- Find and replace all image/file paths to new URL
---
### Migrate website to Hostinger
- Add website
	- Wordpress
- Credentials
	- use theme in stead
- Select default theme (2025)
	- Do not install plugins!
- Use temporary domain ("wp is installing")
- Select dashboard to new website in hostinger
- go to "databases"
	- Check info
- goto phpMyAdmin 
	- wp_options - Set correct "home" and "siteurl" (url of new website)
---
### The Blank Page Problem
- Delete default pages, create new ones and make sure to "edit with elementor" 
- Set the page template to "Elementor canvas" (can also be done from quick edit)  
	- Create: Home - slug = home - template = Elementor canvas 
	- Create: About - slug = about - template = Elementor canvas 
- Go to Settings
	- Click readings
	- Change your homepage displays from "Your latest post" to "A static page" and Choose your page
	- Choose which page you want to set as home page and save changes 
---
### The_Content
- First in order to fix the infamous "the_content" error you must download twenty nineteen theme, then go to wherever the theme is.
- When doing this locally it will be in "C:\xampp\htdocs\wordpress\wp-content\themes\twentynineteen"
- Here you can find the index.php file and on a line above <?php get_footer; ?> you must write: <?php the_content; ?>
---

[^1]: To find the correct url:
	- Go to github.com, click your profile picture and select "Your Profile".
	- Select "Repository" and hit the green "New" button
	- Set a repo -name, and set the desired settings and click "Create Repository"
	- Then, go to the new repository, click "Code..", select the "local" -tab, and select "Https" (or SSH, obviusly) - That's the correct URL 

[^2]: Add the '-u' -flag for comprehensive status

# Obsidian
## Windows and Linux shortcuts 
### Common Actions

|Action|Shortcut|
|---|---|
|Copy|`Ctrl+C`|
|Cut|`Ctrl+X`|
|Paste|`Ctrl+V`|
|Paste without formatting|`Ctrl+Shift+V`|
|Undo|`Ctrl+Z`|
|Redo|`Ctrl+Shift+Z` or `Ctrl+Y`|
|Copy paragraph|`Ctrl+C` (with no selection)|
|Cut paragraph|`Ctrl+X` (with no selection)|
### Text Editing
|Action|Shortcut|
|---|---|
|Insert new line|`Enter`|
|Delete previous character|`Backspace`|
|Delete next character|`Delete`|
|Delete previous word|`Ctrl+Backspace`|
|Delete next word|`Ctrl+Delete`|
|Delete current line|`Ctrl+Shift+K`|
### Text Navigation
|Action|Shortcut|
|---|---|
|Move cursor one character|`Left/Right Arrow`|
|Move to beginning of previous word|`Ctrl+Left Arrow`|
|Move to end of next word|`Ctrl+Right Arrow`|
|Move to beginning of current line|`Home`|
|Move to end of current line|`End`|
|Move to previous line|`Up Arrow`|
|Move to next line|`Down Arrow`|
|Move to beginning of note|`Ctrl+Home`|
|Move to end of note|`Ctrl+End`|
|Move up one page|`Page Up`|
|Move down one page|`Page Down`|
### Text Selection
|Action|Shortcut|
|---|---|
|Simplify selection|`Escape`|
|Select all|`Ctrl+A`|
|Extend selection one character|`Shift+Left/Right Arrow`|
|Extend selection to previous word|`Ctrl+Shift+Left Arrow`|
|Extend selection to next word|`Ctrl+Shift+Right Arrow`|
|Extend selection to beginning of line|`Shift+Home`|
|Extend selection to end of line|`Shift+End`|
|Extend selection to beginning of note|`Ctrl+Shift+Home`|
|Extend selection to end of note|`Ctrl+Shift+End`|
|Extend selection one page up|`Shift+Page Up`|
|Extend selection one page down|`Shift+Page Down`|
## Setup
### Plugins
#### heading-level-indent

# Termux
