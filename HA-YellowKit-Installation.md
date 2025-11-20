# Installation de Home Assistant Yellow Kit with CM5

![HA Yellow Kit CM5](https://www.home-assistant.io/images/blog/2024-11-cm5/art.jpg)

---

## Matériel nécessaire

- 1 Kit HA Yellow
- 1 module Raspberry CM5
- Ordinateur (Windows, macOS ou Linux)
- Connexion Internet
- 1 Cable Ethernet
- 1 Bloc Alim (12 V / 2 A) 
- 1 Cable USB-C 

---

## Ressources utiles

- [HA Yellow Kit](https://support.nabucasa.com/hc/en-us/categories/24734575925149)
- [Installation Yellow Kit + CM5](https://support.nabucasa.com/hc/en-us/articles/25606333033501-Home-Assistant-Yellow-Kit-with-CM5)
- [HA Yellow Kit + NVMe](https://support.nabucasa.com/hc/en-us/articles/25298668266269-Home-Assistant-Yellow-Kit-with-CM4-and-optional-NVMe)

---

# Installation de Home Assistant Yellow Kit avec CM5 et NVMe

## 1. Installer le CM5:
[Installation Yellow Kit + CM5](https://support.nabucasa.com/hc/en-us/articles/25606333033501-Home-Assistant-Yellow-Kit-with-CM5) 
pour le montage du CM5 
<font color='red'>Le NVMe a été monté en même temps (installation sur la mémoire interne du CM5 </font>

## 2. Installer le NVMe:
[HA Yellow Kit + NVMe](https://support.nabucasa.com/hc/en-us/articles/25298668266269-Home-Assistant-Yellow-Kit-with-CM4-and-optional-NVMe) 
pour le montage du NVMe
## 3. Installer le *rpiboot*:
[Installation Yellow Kit + CM5](https://support.nabucasa.com/hc/en-us/articles/25606333033501-Home-Assistant-Yellow-Kit-with-CM5) 
pour l'installation du **rpiboot**
## 4. Installer le Home Assistant OS à l'aide du Raspberry Pi Imager:
[Installation Yellow Kit + CM5](https://support.nabucasa.com/hc/en-us/articles/25606333033501-Home-Assistant-Yellow-Kit-with-CM5) 
pour l'installation du **Home Assistant OS**

---

## 1. Matériel nécessaire

- Carte ESP32-C6 DevKitC-1 V1
- Câble USB-C
- Ordinateur (Windows, macOS ou Linux)
- Connexion Internet

---

## 2. Installation de l’IDE et des outils

### a) Installer Visual Studio Code (recommandé)
- Télécharger depuis [code.visualstudio.com](https://code.visualstudio.com/)
- Installer l’extension **PlatformIO** ou **ESP-IDF** (Espressif)

### b) Installer l’ESP-IDF (Espressif IoT Development Framework)
- Suivre le guide officiel : [Getting Started ESP-IDF](https://docs.espressif.com/projects/esp-idf/en/latest/esp32c6/get-started/index.html)
- Téléchargez l’installateur pour Windows ou utilisez les scripts pour macOS/Linux :
  - Windows : [ESP-IDF Tools Installer](https://dl.espressif.com/dl/esp-idf/?idf=latest)
  - macOS/Linux :  
    ```bash
    git clone --recursive https://github.com/espressif/esp-idf.git
    cd esp-idf
    ./install.sh esp32c6
    ```

### c) Installer les pilotes USB (si besoin)
- Windows :  
  [Pilotes USB Espressif](https://www.silabs.com/developers/usb-to-uart-bridge-vcp-drivers)
- macOS/Linux : Généralement déjà pris en charge.

---

## 3. Connexion de la carte

- Connectez la carte ESP32-C6 à votre ordinateur via le câble USB-C.
- Vérifiez que la LED d’alimentation s’allume.
- Notez le port série attribué :
  - **Windows** : Gestionnaire de périphériques > Ports (COM)
  - **macOS/Linux** :  
    ```bash
    ls /dev/tty.*
    ls /dev/ttyUSB*
    ```

---

## 4. Compilation et flash d’un premier programme

### a) Cloner un projet d’exemple

```bash
git clone https://github.com/espressif/esp-idf-template.git
cd esp-idf-template
```

### b) Configurer l’environnement

- Sous Windows, lancez “ESP-IDF Command Prompt” (installé à l’étape 2).
- Sous macOS/Linux :
  ```bash
  source $HOME/esp/esp-idf/export.sh
  ```

### c) Configurer le projet

```bash
idf.py set-target esp32c6
idf.py menuconfig
```

### d) Compiler et flasher

```bash
idf.py build
idf.py -p <PORT> flash
```
Remplacez `<PORT>` par le port série détecté.

### e) Ouvrir le moniteur série

```bash
idf.py -p <PORT> monitor
```


