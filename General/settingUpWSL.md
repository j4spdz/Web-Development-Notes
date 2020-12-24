# Setting Up Windows Subsystem for Linux

## Requirements

- Window 10 (OS build 20262 or higher)
- Enable virtualisation on BIOS

## Setting up virtualisation

1. Go to Task Manager > Performance > CPU. Check if there is an option named virtualisation
2. If it is disabled, you will need to go to Recovery > Advanced startup > Troubleshoot > UEFI Settings.

   `For MSI Motherboard, go to OC. Under Advanced CPU configuration, turn on SVM`

## Setting up WSL

1. Enable the following Window features:
   - Virtual Machine Platform
   - Windows Subsystem for Linux.
2. Restart computer
3. Download the latest Linux Kernel
4. Set WSL2 as default version

   ```bash
   wsl --set-default-version 2
   ```

5. From the Microsoft Store, download Linux distro (Ubuntu) and Microsoft Terminal

## Setting up dev environment

1. Download git

   ```bash
   sudo apt-get install git
   ```

2. Download zsh and ohmyzsh, and set zsh as default terminal option

   ```bash
   sudo install apt install zsh
   sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
   ```

3. Download nvm

   ```bash
   command -v -nvm
   ```

   A valid installation will return **nvm**

4. Install node

   ```bash
   nvm install node
   ```
