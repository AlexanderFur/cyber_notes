# Zsh

## Set zsh as default shell

>	chsh -s $(which zsh)

## Aliases

```
alias cls="clear"
alias la="ls -lashp --group-directories-first"
alias l="ls -lshp --group-directories-first"
alias lf="ls -lshp | grep -v /"
alias laf="ls -lashp | grep -v /"
alias lad="ls -lashp | grep /"
alias ld="ls -lshp | grep /"
```


Add these in the bottom of .zshrc

## Plugins
Autosuggestions
>	git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions

Syntax Highlighting
>	git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting

Edit in .zshrc
>	plugins=(git zsh-autosuggestions zsh-syntax-highlighting)


## Install Oh My Zsh (curl)
>	sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"

## Install PowerLevel10k
>	git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/themes/powerlevel10k

Edit .zshrc: 
>	ZSH_THEME="powerlevel10k/powerlevel10k"

# .sh -files
## Update.sh
```.sh
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
```

