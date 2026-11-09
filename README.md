# Nyx

Navigateur web rapide et respectueux de la vie privée : moteur Chromium, interface
minimaliste, bloqueur de publicités et de traqueurs intégré, aucune télémétrie.

Ce dépôt contient uniquement les **versions publiées** (installateurs). Le code source
est dans un dépôt privé.

**Télécharger la dernière version : [Releases](https://github.com/ahilarion/nyx-releases/releases/latest)**

Une fois installé, Nyx se met à jour tout seul : il vérifie chaque jour la dernière
version publiée ici, la télécharge en arrière-plan, et propose de redémarrer pour
l'installer (désactivable dans `nyx://settings` > À propos).

## Windows

Windows 10 ou plus récent, 64 bits.

1. Télécharger `Nyx-<version>-installation.exe` depuis la
   [dernière version](https://github.com/ahilarion/nyx-releases/releases/latest).
2. Le lancer. Windows SmartScreen peut afficher « Windows a protégé votre ordinateur »
   (l'installateur n'est pas signé) : *Informations complémentaires* > *Exécuter quand
   même*.
3. Suivre l'assistant. Par défaut, l'installation se fait pour votre compte seulement,
   sans droits administrateur. Options :
   - raccourci sur le bureau ;
   - **proposer Nyx parmi les navigateurs**, pour pouvoir le choisir comme navigateur
     par défaut (*Paramètres* > *Applications* > *Applications par défaut* > Nyx).

**Désinstaller** : *Paramètres* > *Applications* > *Applications installées* > Nyx >
*Désinstaller*.

## Linux

x86_64, toute distribution récente (glibc 2.35 ou plus : Ubuntu 22.04, Debian 12,
Fedora 36, Arch…). Installation pour l'utilisateur courant, sans `sudo`.

```sh
# 1. Télécharger l'archive de la dernière version
curl -LO https://github.com/ahilarion/nyx-releases/releases/latest/download/Nyx-<version>-linux-x86_64.tar.gz

# 2. Décompresser et installer
tar -xzf Nyx-<version>-linux-x86_64.tar.gz
./nyx/installer.sh
```

L'installateur place Nyx dans `~/.local/lib/nyx`, ajoute la commande `nyx` dans
`~/.local/bin` et une entrée **Nyx** dans le menu des applications. Si `~/.local/bin`
n'est pas dans votre `PATH`, il l'indique (lancer alors Nyx depuis le menu, ou
`~/.local/bin/nyx`). Le dossier `nyx/` décompressé peut ensuite être supprimé.

Navigateur par défaut (facultatif) :

```sh
xdg-settings set default-web-browser nyx.desktop
```

**Mettre à jour** : automatique, au redémarrage proposé par Nyx. Réinstaller par-dessus
une ancienne version fonctionne aussi (`./nyx/installer.sh`).

**Désinstaller** :

```sh
~/.local/lib/nyx/installer.sh --desinstaller
```

Le profil (historique, favoris, cookies) est conservé dans `~/.local/share/nyx` ; le
supprimer à la main pour tout effacer. Les réglages sont dans `~/.config/nyx`.

## Vérifier un téléchargement

GitHub affiche l'empreinte SHA-256 de chaque fichier dans la page de la version. Pour
la comparer :

- Windows (PowerShell) : `Get-FileHash .\Nyx-<version>-installation.exe`
- Linux : `sha256sum Nyx-<version>-linux-x86_64.tar.gz`

Nyx fait cette vérification lui-même pour ses mises à jour automatiques.
