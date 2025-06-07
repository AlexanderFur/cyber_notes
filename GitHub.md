# Create a new repository on the command line:

>	git init 

>	git add < files >

>	git commit -m "first commit"

>	git branch -M main

>	git remote add origin https://github.com/AlexanderFur/obsidian_notes.git

>	git push -u origin main

---
# …or push an existing repository from the command line

Replace URL with the correct one
>	git remote add origin https://github.com/AlexanderFur/obsidian_notes.git 

>	git branch -M main

>	git push -u origin main

---
# Everyday use:
>	git status 

>	git pull

>	git add <filename (or type a quotationless '.' for all of the current dir)>

>	git commit -m < Message >

>	git push

To see and compare all changes:

>	 git diff HEAD

------------------------------------------------------
# SSH
## Checking for existing keys
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

## Generate SSH key
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



# Termux

## How to Clone and Synchronise a GitHub Repository on Android

*By Alan Bonnici*

*Published: February 12, 2024*

---

### Introduction

This guide describes how to synchronize a folder on GitHub with your Android device. The example focuses on syncing a LogSeq folder, but the steps can be adapted for other use cases. The synchronization process is manual: sync with the repository before opening the tool (e.g., LogSeq) and update the repository again when you're done.

---

### Prerequisites

* **Termux**: An open-source Android terminal emulator and Linux environment application.
* **F-Droid**: An app catalogue of FOSS (Free and Open Source Software) applications for the Android platform.
* **GitHub account**: For hosting your repository.

---

### Steps

##### 1. Install F-Droid

Termux can be found on the Google Play Store, but the version there may not be the latest. It's recommended to install the version from F-Droid. You need to sideload it.

##### 2. Install Termux via F-Droid

After installing F-Droid, search for and install Termux.

##### 3. Update Termux

Open Termux and run:

>	apt update

>	apt upgrade


When prompted to overwrite files during the upgrade process, press 'Y'.

##### 4. Install and Configure Git

In Termux, install Git and configure your user information:

>	pkg install git

>	git config --global user.name "< your name >"

>	git config --global user.email "< your email >"


##### 5. Allow Termux to Access Android Storage

Run the following command to grant Termux access to your device's storage:


>	termux-setup-storage


Your device's folders will be accessible under `~/storage/shared/`. Use the `ls` command to list directories and `mkdir` to create a new folder if needed. For example:


>	mkdir ~/storage/shared/Documents/termux_mapped


If your device has external storage and is rooted, you can access it via `~/storage/external-1/`.

>[!Note]
> 	For Android 11 and above, if you're unable to access external storage, refer to the Termux Wiki: Android 11.

##### 6. Install and Configure SSH Key for GitHub Authentication

Install OpenSSH:

>	pkg install openssh


Generate SSH keys:


>	ssh-keygen -t ed25519 -C "< your email >"


You can keep the default file name and enter a passphrase when prompted. Unless specified otherwise, the public key will be saved at `~/.ssh/id_ed25519.pub`.

##### 7. Load the Public Key to GitHub

Copy the public key to a folder accessible from your Android's file manager:


>	cp ~/.ssh/id_ed25519.pub ~/storage/shared/Documents/


Open the public key file (`id_ed25519.pub`) in a text editor to copy its contents. If you don't have a text editor on your Android device, you can:

* Transfer the file to a desktop computer and open it in a text editor like Notepad.
* Install a free text editor from F-Droid.

Go to your GitHub account:

* Navigate to **Settings** > **SSH and GPG keys**.
* Click on **New SSH key**.
* Label the key (e.g., "Android Device") and paste the contents of your public key into the **Key** field.
* Click **Add SSH key**.

##### 8. Clone the GitHub Repository

Change to the shared folder and clone your repository:

>	cd ~/storage/shared/Documents

>	git clone git@github.com:<your_username>/<your_repository>.git


Replace `<your_username>` and `<your_repository>` with your actual GitHub username and repository name.

Configure Git to recognize the directory as safe:

>	git config --global --add safe.directory ~/storage/shared/Documents/<your_repository>

After cloning, the folder on your Android device should contain the files from your GitHub repository.

##### 9. Automate Synchronization with Termux\:Widget (Optional)

Install Termux\:Widget from F-Droid. This app allows you to execute scripts stored in Termux from the home screen.

Follow the instructions at Termux\:Widget - Scripts Directories to set up the shortcut directories.

Download the synchronization scripts (`pull-graph.sh` and `push-graph.sh`) from the Logseq-Git-Sync-101 repository.

Assuming you've placed the scripts in the Documents folder on your Android device, move them to the `.shortcuts` directory in Termux:


>	mv ~/storage/shared/Documents/*.sh ~/.shortcuts


Ensure that the scripts are executable and modify them as needed. For example, in `pull-graph.sh`, you might have:

```
#!/usr/bin/bash
source source-ssh-agent
cd ~/storage/shared/Documents/<your_repository>
git pull
```

Replace `<your_repository>` with your actual repository name.

---

>[!Note]
>	For more detailed information and screenshots, refer to the original article by Alan Bonnici.


