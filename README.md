# Cold Storage with TailsOS

### Description
The aim of this guide is to provide a possible, cheap and accessible from most of every computer, solution to create a cold storage environment.
The environment is designated to store keys for Cardano Stake Pools and to be able to create keys that need to remain offline. Other than that it can be used for other things but it is outside the scope of this guide. 
 
<em>This guide is a first version, if you have improvments to do or have questions about it, feel free to contact me, I am very happy to work on that.</em>

### Why Tails OS?
[Tails](https://tails.boum.org/) (The Amnesic Incognito Live System) is a security-focused, Debian based, portable Operating System. It is designed to protect users against surveillance and censorship, and it aims to preserve privacy and anonymity.  

This OS is used as a cold storage due to properties listed below:  
- Bootable from USB,
- The OS never writes anything to the hard disk, everything is done on RAM and every shutdown, memory is overwritten with random data,
- It incorporates defenses against [Cold Boot attacks](https://tails.boum.org/doc/advanced_topics/cold_boot_attacks/index.en.html),
- It supports an encrypted storage and have few extra tools for improve security already preinstalled,
- Network "Offlinee" option, shutdown any connection on boot

### Requirements
- 2x USBs of at least 8GB (active and backup storage) + 1x USB of at least 8GB for updates and files transmissions.
- 1x computer where to do the procedure

### Limitations
- Tails won’t work on Apple Mac’s that have M1 chip
- With the restrictions of this OS, I didn't find a way to build Cardano Tools, instead I have downloaded the prebuilt version of them.
<em>If you want to help me achieve this, contact me, I really would like to improve this solution.</em>

**<em>Chapters marked with \* need to be done on both USBs, Active and Backup</em>**

## Install Tails OS \*
To install Tails OS, follow the documentation on the [Official Website](https://tails.boum.org/install/index.en.html).
Follow this procedure for both USBs, active and backup.

## Cold Storage Configuration
### First boot \*
Once boot from USB is entered, Welcome screen will be shown.
1. Set your Language & Region options,
2. Enable the offline mode, click on the "**+**" button --> "**Offline Mode**" --> "**Disable all networking**" --> "**Add**",
3. Start Tails with the button on the right-top corner

<em>Don't add other options cause they will not be saved until the persistent memory is configured</em>

### Configure Persistent Encrypted Storage \*
Once the OS is booted, first thing to do is to configure a persisten encrypted storage to be able to store configurations and afterwards Stake Pool files.
To do so, go to "**Applications**" --> "**Tails**" --> "**Configure Persisten Volume**".
At this point the OS will ask for a password and its verification. Keep in mind that this password will be asked at every boot and will be necessary to access different configurations and files stored on the encrypted volume.

After volume is created, the wizzard will ask what kind of configurations and files need to be saved on it. Select "Personal Data" and "Welcome Screen", be free to select other options if needed. It is always possible to add those later.

Once options are select, click "**Save**" and reboot the OS as asked.

### Configure Persistent Cold Storage options \*
After the reboot, at the Welcome Screen, select Language & Region options, unlock the encrypted volume and add again the offline mode (as explained earlier) + an administrator password if you need to operate a sudo user, this time, everything will be saved over reboots, once done, boot into the OS.

At this point, cold storage will be ready.
Files need to be saved on persistent volume under "**Places**" --> "**Peristent**" or "**/home/amnesia/Persistent**". Everything else will be deleted on next reboot/shutdown.

## Install Cardano Tools
As said on limitations, for what regards the Cardano Tools. I don't have a way to build them inside this OS.
To be able to use the cli, download the prebuilt version from the [Official GitHub repository](https://github.com/input-output-hk/cardano-node#linux-executable)

## Backup encrypted storage
Once the Active USB is ready, files of the pool are copied and tools installed, backup everything on the Backup USB.
To Backup the Persistent Storage, follow the [Official Documentation](https://tails.boum.org/doc/first_steps/persistence/backup/index.en.html#update)
Keep in mind that it is best practice to have same version on both USBs

## Upgrade OS
To Upgrade the OS, follow the [Official Documentation](https://tails.boum.org/upgrade/tails-overview/index.en.html)
A temporary USB of at least 8GB is needed.

