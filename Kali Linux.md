# General

## Shell Scripts
### Connect to THM -VPN

	### #!/bin/zsh
	
	### Run OpenVPN with the specified configuration file
	### sudo openvpn /home/kali/Downloads/MorraDiStjeler.ovpn

 ---
### Ultimate Update

	### #!/bin/zsh
	
	### Ensure the script is run with superuser privileges
	### if [ "$EUID" -ne 0 ]; then
	    ### echo "Please run this script as root or using sudo."
	    ### exit 1
	### fi
	
	### Update package lists
	### echo "Updating package lists..."
	### apt-get update
	
	### Upgrade installed packages
	### echo "Upgrading installed packages..."
	### apt-get upgrade -y
	
	### Perform a distribution upgrade
	### echo "Performing a distribution upgrade..."
	### apt-get dist-upgrade -y
	
	### Perform a full upgrade
	### echo "Performing a full upgrade..."
	### apt full-upgrade -y
	
	### Remove unnecessary packages
	### echo "Removing unnecessary packages..."
	### apt autoremove -y
	
	### echo "System update and upgrade complete!"

 ---
## Uninstall a .deb -file
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
## Make Executable
Make it runable for all users:

>	$ sudo chmod +x <filename.extention>

---
## Make .sh runable from anywhere
>	$ sudo mv '/Full/path/including/filename.sh' /usr/local/bin/

----
## Corrupt .zsh_history -Fix
- **Run these commands:**

>	$ cd ~

>	$ mv .zsh_history .zsh_history_bad

>	$ strings .zsh_history_bad > .zsh_history

>	$ fc -R .zsh_history

>	$ rm ~/.zsh_history_bad

---
## Commands - Chrome
 
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
## Extract .tar
### Extract '.tar.gz' -files

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
### Extract '.tar.xz' -files

Install "xz" using the 
>	dnf install xz

on a CentOS/RHEL/Fedora Linux.

Debian/Ubuntu Linux users
>	sudo apt install xz-utils 

To decompress filename. tar. xz file run: 
>	sudo xz -d -v 'filename'.tar.xz

---
### Extract '.tar' -files
To untar a file in Linux, use the
>	sudo tar -xvf 'filename.tar'

This command extracts the contents of tar files, which are commonly used in Linux for file compression.

---
## Oh My Zsh!
### Installation (Curl)

>	sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

### Uninstallation
>	uninstall_oh_my_zsh
---
### Plugins

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

## Change username in Kali Linux

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
# Hotkeys
## General Shortcuts
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
## Screenshot shortcuts

| Keyboard shortcut           | Description                                                                            |
| --------------------------- | -------------------------------------------------------------------------------------- |
| Print Screen                | Using this shortcut button, we can take a screenshot.                                  |
| Ctrl + Print Screen         | Screenshot to clipboard                                                                |
| Alt + Print Screen          | Using this shortcut, we can take a screenshot of a window.                             |
| Ctrl + Shift + Print Screen | With the help of this shortcut, we can take a screenshot of an area to the clipboard.  |
| Ctrl + Alt + Print Screen   | With the help of this shortcut, we can take a screenshot of a window to the clipboard. |
| Shift + Ctrl + Alt + R      | Using this shortcut, we can record a screencast.                                       |

---
## Terminal shortcuts
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
## Workspace shortcuts
| Keyboard shortcut      | Description                                                             |
| ---------------------- | ----------------------------------------------------------------------- |
| Shift + Ctrl + Alt + ← | Using this shortcut, we can move the window one workspace to the left.  |
| Shift + Ctrl + Alt + → | Using this shortcut, we can move the window one workspace to the right. |
| Shift + Ctrl + Alt + ↑ | Using this shortcut, we can move the window one workspace up.           |
| Shift + Ctrl + Alt +↓  | Using this shortcut, we can move the window one workspace down.         |

---
# Hydra
## Post Web Form
### Flags

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
## SSH
### Flags
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
# Nmap
## Scans
### Full scan - TCP connect
For monitoring:
> 	$ sudo nmap -A -p- -T4 -sT -Pn

---
### Full Scan - TCP SYN
For simulation/pentesting:
> 	$ sudo nmap -A -p- -T4 -sS -Pn

------------------------------------------------------------
# Mousepad
## Open files in separate windows
>	mousepad < file name1 > | mousepad < file name2 >
