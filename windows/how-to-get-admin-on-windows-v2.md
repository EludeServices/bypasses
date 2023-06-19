---
tags: bypasses
---
# Getting Admin on Windows V2

### Exploit Description
Description

## Instructions
#### What you need:
- Windows 10 USB stick (you can one [here](http://amzn.to/2v72Wzs))
- Braincells

### Steps
:::info
Instead of a Windows 10 USB stick, you can also use a general USB and flash a Windows 10 installation image onto it. Because it is so simple, we will not document the process on how to do this however you can find a guide with a little bit of googling.
:::
1.  First, insert your bootable flash drive having Windows 10 Or Windows 10 DVD.
2. Restart your computer. While restarting, you need to press the boot key on your keyboard. The Boot key differs from the computer manufacturer. For HP its F9 and for Dell its F2.You can also find it on Google (For custom build PC find the boot key for your motherboard).
3. After pressing the boot key you'll arrive at the boot menu. From there select your boot media.
4. Press any key to boot from your Windows 10 media.
5. Select your language and keyboard input method and hit Next.
6. Click "Repair your Computer.
7. Click Troubleshoot - Advanced Options - Command Prompt.
8. Navigate to Windows 10 installation drive.
9. Type `cd windows/system32` and hit Enter.
10. Type `ren utliman.exe utilman_bak.exe && copy cmd.exe utilman.exe` and hit Enter.
11. Restart your computer.
12. Click on ease of access icon and it will launch the command prompt.
13. Type control userpasswords2   hit Enter.
14. From the user account menu, Reset windows 10 password. Exit the command prompt and login to Windows.

#### Steps to revert the changes:
1. Navigate to the system32 folder and delete utilman file.
2. Rename utilman_bak to utilman after getting the permission.

## End Note
That's everything! If you need more help, you can reach out to us on your [Discord](https://discord.gg/elude) server or on [Reddit](https://reddit.com/r/sneakersneet). We will likely respond faster on Discord, however please still be patient.