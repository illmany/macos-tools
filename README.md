# macos-tools
Un aide-mémoire technique centralisant des commandes Terminal avancées, des configurations système et des raccourcis de dépannage pour optimiser et administrer macOS.

# Tools macOS

<aside>
🚨 ATTENTION : ces commandes sont très puissantes et peuvent endommager votre système, n'utilisez que des commandes que vous comprenez.

</aside>

# **RESSOURCES**

Liste de tous les modèles de Mac avec leurs différents identifiants : 

# **TERMINAL**

Optimisation totale 

`killall Finder && killall Dock && sudo purge`

Température CPU en temps réel 

`sudo powermetrics --samplers smc |grep -i "CPU die temperature"`

Afficher les fichiers cachés - **`CMD` + `SHIFT`+ `Fn`+ `;`** 

`defaults write com.apple.finder AppleShowAllFiles TRUE && killall Finder`

`defaults write com.apple.finder AppleShowAllFiles FALSE && killall Finder`

Gatekeeper

`sudo spctl --master-disable`  

`sudo spctl --master-enable` 

Installer Rosetta **(M1 min) 

`softwareupdate --install-rosetta`

Recherche sur tout le Mac

`mdfind "contenu"` 

Faire dire du texte à votre Mac 

`say "contenu"` 

Désactiver mise en veille 

`caffeinate`

Reconstruire Spotlight - [HT201716](https://support.apple.com/fr-fr/HT201716)

`sudo mdutil -E /Volumes/[volume]`

À activer après un passage de HDD à SSD 

`sudo trimforce enable`

Lister instatanés Time Machine 

`tmutil listlocalsnapshotdates`

Supprimer TM 

`tmutil deletelocalsnapshots [ref]`

Reconstruire Fusion Drive - [HT207584](https://support.apple.com/fr-fr/HT207584) - 10.14+ 

`diskutil resetFusion` 

Droits d’un user

`chown -R username [dossier depart]`

Reset permissions session - *depuis recovery* - 11.0+

`repairHomePermissions`

Modifier nom host 

`sudo scutil --set HostName [nom]`

Afficher logs SMC

`pmset -g log`

Infos Hardware 

`system_profiler SPHardwareDataType`

Signer App 

`xattr -cr [chemin local app]`

`codesign --force --deep --sign - / [chemin local app]`

Speedtest dans le terminal

`networkquality`

Ejecter CD/DVD 

`drutil tray eject`

Fix El Capitan 10.11 Install 

`date 010920002016`

## Gestion de fichiers

ditto 

`sudo ditto [source] [destination]`

Copie avec avancement par fichier et débit

`rsync -r --progress [source] [destination]`

## Brew

Installer Brew *(passer par le site officiel)* 

`/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`

Installer Cask

`brew install cask`

Rechercher apps Brew avec description 

`brew search --casks --desc ''`

Update 

`brew upgrade --greedy`

Stress test CPU 

`stress —cpu 8`

Stress yes

`yes > /dev/null & [dupliquer autant de fois que de cores]`

## Configuration macOS

Installer Xcode CLT (obligatoire pour Brew) 

`xcode-select --install`

Délai d'affichage du Dock à **`0`** 

`defaults write com.apple.dock autohide-delay -float **0** && killall Dock`

Darkmode High Sierra - 10.14+

`defaults write -g NSRequiresAquaSystemAppearance -bool Yes`

Masquer bulle rouge MAJ Préférences Système dans le Dock

`defaults write com.apple.systempreferences AttentionPrefBundleIDs 0 && killall Dock`

Supprimer l’indicateur de CAPSLOCK flottant 

`sudo mkdir -p /Library/Preferences/FeatureFlags/Domain && sudo /usr/libexec/PlistBuddy -c "Add 'redesigned_text_cursor:Enabled' bool false" /Library/Preferences/FeatureFlags/Domain/UIKit.plist`

Désactiver l’accélération de la souris 

`defaults write .GlobalPreferences com.apple.mouse.scaling -1`

Réduire les espaces entre les icones barre de menu (reboot requis) / **`Var`** en px, *exemple* **`10`**

`defaults -currentHost write -globalDomain NSStatusItemSpacing -int **10**` 

## Install macOS Big Sur

Renommer la partition à transformer "`install`" puis coller cette commande dans le Terminal : 

`sudo /Applications/Install\ macOS\ Big\ Sur.app/Contents/Resources/createinstallmedia --volume /install`

## Pro-tips :

Supprimer "`/var/db/.applesetupdone`" quand aucun admin, à faire depuis un OS fiable, attention à bien a bien sélectionner le disque 

`~` (**`ALT` + `N`**) vous permet de pointer vers le dossier de votre session par exemple `~/Desktop`

Vous pouvez lire ou édtier l’historique du terminal depuis le fichier `~/.zsh_history`

# RACCOURCIS CLAVIER

**Sur système :** 

**`CMD` + `SHIFT` + `;` + `Fn`** → Afficher les fichiers cachés du Finder

**`CMD` + (+ `Fn`) + `F1`** → Changer mode recopie vidéo (si écran HS par exemple)

**Au démarrage :** 

**`CMD` + `ALT` + `R`** → Redémarrer en recovery via internet vers la version la plus récente 

**`CMD` + `S`** → Redémarrer en mode invité de commande (Terminal limité, pas de diskutil)

**`SHIFT`** → Redémarrer en mode sans extensions (mode sans echec) 

**`CMD` + `ALT` + `P` + `R`** → PRAM : Maintenir au démarrage jusqu’au 3ème “bong” puis lâcher. 

- **SOURCES**
    
    [https://osxdaily.com/2020/11/09/how-copy-command-line-progress-speed-indicator/](https://osxdaily.com/2020/11/09/how-copy-command-line-progress-speed-indicator/)
    
    [https://www.macworld.co.uk/how-to/mac-terminal-projects-tutorial-3613813/](https://www.macworld.co.uk/how-to/mac-terminal-projects-tutorial-3613813/)
    

https://www.kernel.consulting/
