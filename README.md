# Coding Setup
*Windows // Python // Git // VSCode*

----------------------------------
## Windows Einstellungen
* App Execution Aliase für Python ausschalten
* Windows Explorer Ordnereinstellungen:
    * Show file extensions
    * Show hidden files
    * Show protected operating system files
    * Show the full path in the title bar

* Execution Policy anpassen: 
  * Powershell als Administrator ausführen
  * <code>Set-ExecutionPolicy Unrestricted</code>


## Grundlegende Software
### Chocolatey
[Chocolatey Docs](https://docs.chocolatey.org/en-us/choco/setup)
```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force; [System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))

choco install -y choco-protocol-support chocolateygui
```
### Weitere generelle Software:
* bulk-crap-uninstaller
* winaero-tweaker
* powershell-core
* 7zip
* git
* github-desktop
* vscode
* ...

## Terminal Setup
[Terminal Windows Store](https://www.microsoft.com/store/productId/9N0DX20HK701)
* Profile Datei erstellen: `ni -Force $PROFILE`
* Inhalt einfügen
### Powershell Modules:
* ZLocation
* Oh my posh
* Posh Git

#### ZLocation Setup
[ZLocation Github](https://github.com/vors/ZLocation)
```powershell
Install-Module ZLocation -Scope CurrentUser
```
Den Befehl `Import-Module ZLocation` zum Profile hinzufügen

#### Oh my posh Setup
[Oh my posh Docs](https://ohmyposh.dev/docs/installation/windows)
```powershell
choco install -y oh-my-posh
oh-my-posh font install # FiraMono NF
```
Im Windows Terminal `STRG` + `SHIFT` + `,` und Font in `settings.json` hinzufügen:
```json
{ 
    "profiles": {
        "defaults": {
            "font": {
                "face": "MesloLGM NF"
            }
        }
    }
}
```
Zur Profile Datei hinzufügen:
```powershell
oh-my-posh init pwsh --config ~/obause.omp.json | Invoke-Expression
```

#### Posh Git
[Poshgit Github](https://github.com/dahlbyk/posh-git)
```powershell
Install-Module posh-git
```

## Python Setup
* Pyenv
* Anaconda
* Python 

#### Pyenv
```powershell
# Pyenv installieren
choco install -y pyenv-win
# Python versionen laden 
pyenv update
# Python installieren 
pyenv install 3.10.6 3.9.12 --quiet
# Python version wechseln
pyenvn global 3.10.X 
```

### Anaconda
TODO

## Git + SSH Setup
#### Git installieren:
```powershell
# Git installieren
choco install -y git
# Configs setzen
git config --global user.name "Ole Bause"
git config --global user.email "ole@bause.me"
# SSH Key generieren
ssh-keygen -C "ole@bause.me"
# Public Key ausgeben
cat ~/.ssh/id_rsa.pub
```
#### SSH Key zu Github Account hinzufügen
1. Github.com -> Settings -> Manage SSH Keys 
2. Create SSH Key
3. Inhalt aus der letzten Ausgabe einfügen
4. Speicher

Verbindung testen mit: `ssh -T git@github.com`

## VSCode Setup