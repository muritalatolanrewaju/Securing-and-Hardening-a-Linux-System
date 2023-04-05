# Securing the Boot Loader (GRUB)

This section demonstrates how to secure the boot loader. When a computer boots up, the BIOS executes the first code, which performs a Power-On Self-Test before executing the code in the Master Boot Record sector of the disk where the boot loader is located. The boot loader then loads the kernel, which initializes the entire system.

GRUB 2 is the default boot loader for major Linux distributions, and a hacker could exploit it to boot the system into Single User Mode or change its configuration. To prevent such security threats, it's essential to protect the GRUB bootloader password. Note that physical access to the computer can bypass GRUB's security measures.

Another potential security vulnerability is booting the system from another medium, such as a USB stick. To address this, set up a BIOS password and configure the system to boot automatically from the partition on which Linux is installed.

It's worth emphasizing that the first layer of security to consider is physical security.

1. To require a password for the GRUB boot loader to start the system, it is necessary to generate a hashed password.

```bash
grub-mkpasswd-pbkdf2
```

![Untitled](assets/images/securing-the-bool-loader-(GRUB)/Untitled.png)

1. After generating the hashed password, the next step is to add the hash to the GRUB main configuration file by editing it.  However, the file is not directly modified by the user It gets overwritten by certain GRUB updates whenever a kernel is added or removed or when the user runs the **`update-grub2`** command. This method ensures that the actual password is not visible in the GRUB scripts, which prevents a possible hacker from accessing it. The GRUB2 main configuration file is located at **`/boot/grub/grub.cfg`** To view the configuration files, use:

```bash
cat /boot/grub/grub.cfg
```

Instead, GRUB uses a series of scripts located in **`/etc/grub.d`** directory to build the configuration file. 

```bash
ls **/etc/grub.d**
```

![Untitled](assets/images/securing-the-bool-loader-(GRUB)/Untitled%201.png)

Modify the files in this directory, and then run the **`update-grub2`** command. Based on the contents of these files, **`update-grub2`** will generate the **`grub.cfg`** file. Alternatively, you can modify a custom file such as **`40_custom`**, which won't get overwritten even when the GRUB package is updated.

```bash
sudo vim /etc/grub.d/40_custom
```

Copy the generated hash password `grub.pbkdf2.sha512.10000.BF07F4A46F7504580CB5C702EDA775486C39A2D28F362B2321CD5760D50214C1EA0C56390D43CF9875D3A31FBD321827E68BFB789CC0239FB71E8655A8161380.58F1D7AE611189AC05E7D584BEBD768AE9CA38C6BB29B28A39C81C4760952315CEF892767F9078EC5B22F9BE774F5206705F1CFA57825A5EB81841C373F53609`

Add new lines to the `40_custom` file the save and exit:

```bash
set superusers="root"
password_pbkdf2 root grub.pbkdf2.sha512.10000.BF07F4A46F7504580CB5C702EDA775486C39A2D28F362B2321CD5760D50214C1EA0C56390D43CF9875D3A31FBD321827E68BFB789CC0239FB71E8655A8161380.58F1D7AE611189AC05E7D584BEBD768AE9CA38C6BB29B28A39C81C4760952315CEF892767F9078EC5B22F9BE774F5206705F1CFA57825A5EB81841C373F53609
```

![Untitled](assets/images/securing-the-bool-loader-(GRUB)/Untitled%202.png)

Update the grub configuration file.

```bash
sudo update-grub2
```

![Untitled](assets/images/securing-the-bool-loader-(GRUB)/Untitled%203.png)

View the content of `/boot/grub/grub.cfg`

```bash
ls /boot/grub/grub.cfg
```

Reboot the Linux system to verify grub is requesting a password to boot into the Linux OS. The username is `root`, and the password is `********`, the same as the one used to generate the GRUB hash. Physical access to the Linux server is required to input the password if a barebone metal is used as the server.

```bash
sudo reboot
```