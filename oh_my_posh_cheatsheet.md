---
aliases:
  - Windows
  - empty
authors: Ciro Bermudez
created: 2024-03-29T12:57
publish: false
tags: 
updated: 2024-04-26T10:20
---

# Windows

```bash
scoop install https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/oh-my-posh.json
```

Edit the `$PROFILE` file for Powershell, in my machine is located in `C:\Users\<username>\Documents\PowerShell\Microsoft.PowerShell_profile.ps1`

```
echo $PROFILE
nvim $PROFILE
```

```bash
scoop install https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/oh-my-posh.json
```

# Linux

```bash
# Install Oh my Posh
sudo wget https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/posh-linux-amd64 -O /usr/local/bin/oh-my-posh
sudo chmod +x /usr/local/bin/oh-my-posh
```

```bash
mkdir ~/.poshthemes
wget https://github.com/JanDeDobbeleer/oh-my-posh/releases/latest/download/themes.zip -O ~/.poshthemes/themes.zip
unzip ~/.poshthemes/themes.zip -d ~/.poshthemes
chmod u+rw ~/.poshthemes/*.json
rm ~/.poshthemes/themes.zip
```

In `.bashrc` or `.profile`, the difference is that if you are using more than one terminal, for example `bash` and `tcsh` it is better to put this in `.profile`, this way the script will run for both terminals. You can check your terminal with `cat /etc/shells`. Personally I put this in side `.profile`

```bash
# oh-my-posh
eval "$(oh-my-posh --init --shell bash --config ~/.poshthemes/robbyrussell.omp.json)"
```

other cool theme is `zash.omp.json`
