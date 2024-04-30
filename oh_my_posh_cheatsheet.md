# oh_my_posh_setup

## Getting started

This is a simple guide on how to install and setup Oh My Posh.

## Installation

### Windows

Is recommended to use [Scoop](https://scoop.sh/) because it is easier to manage.

Install Scoop:

```bash
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
```

Install [Oh My Posh](https://ohmyposh.dev/docs):

```bash
scoop install https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/oh-my-posh.json
```

Create/Edit the `$PROFILE` file for Powershell with the following line, in my machine is located in `C:\Users\<username>\Documents\PowerShell\Microsoft.PowerShell_profile.ps1`, you can check the location with `echo $PROFILE`:

```bash
oh-my-posh init pwsh --config 'C:\Users\Username\AppData\Local\Programs\oh-my-posh\themes\robbyrussell.omp.json' | Invoke-Expression

```

### Linux

Install [Oh My Posh](https://ohmyposh.dev/docs):

```bash
sudo wget https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/posh-linux-amd64 -O /usr/local/bin/oh-my-posh
sudo chmod +x /usr/local/bin/oh-my-posh
```

Add themes:

```bash
mkdir ~/.poshthemes
wget https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/themes.zip -O ~/.poshthemes/themes.zip
unzip ~/.poshthemes/themes.zip -d ~/.poshthemes
chmod u+rw ~/.poshthemes/*.json
rm ~/.poshthemes/themes.zip
```

Finally add the following line to `.bashrc` or `.profile`, the difference is that if you are using more than one terminal, for example `bash` and `tcsh` it is better to put this in `.profile`, this way the script will run for both terminals. You can check your terminals with `cat /etc/shells` and the current terminal your are using with `echo $0`. Personally I put this inside `.profile`

```bash
# oh-my-posh
eval "$(oh-my-posh --init --shell bash --config ~/.poshthemes/robbyrussell.omp.json)"
```
other cool theme is `zash.omp.json`

## Fonts

[Nerd Fonts](https://www.nerdfonts.com/) is a very nice website to find good fonts. I personally like the `Hack Nerd Font Mono` font.

For Windows you can install the font with the following command:

```bash
scoop bucket add nerd-fonts
scoop install nerd-fonts/Hack-NF-Mono
```

For Linux you can do the following:

```bash
cd ~
mkdir .fonts
wget https://github.com/ryanoasis/nerd-fonts/releases/download/v3.1.1/Hack.zip -O ~/.fonts
unzip ~/.fonts/Hack.zip -d ~/.fonts
rm ~/.fonts/Hack.zip
```

In both cases you have to to select that you prefer in the Terminal settings.

> [!NOTE]  
> If you want to install the fonts manually there is a `fonts` directory in this repository containing a `Hack.zip` file. For Windows you can decompress and install the font as any other. For Linux you have to create a `~/.fonts` directory and put the fonts there and restart the terminal. 

## Project status

- [x] This configuration was tested on a Windows 10/11 machine using [Powershell](https://github.com/PowerShell/PowerShell) and [Terminal](https://github.com/microsoft/terminal).

- [x] This configuration was tested on a WSL Ubuntu 22.04.4 LTS using [Terminal](https://github.com/microsoft/terminal).

