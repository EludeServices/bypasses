---
tags: bypasses
---
# Getting Admin On Windows (Recovery Method)

### Exploit Description
Windows is vulnerable to a backdoor that allows you to access an admin command prompt at login. This exploit is rather minor as any backdoors on the device can be easily removed with the use of sfc /scannow or dism /Online /Cleanup-Image /RestoreHealth, although this is only if it is detected. Otherwise, it is undetectable.

The exploit is often done by replacing an executable or service that is available to you at login with a copy of the command prompt, such as the accessibility options (utilman.exe), or sticky keys (sethc.exe). This does however require you to have access to the file system, so if the drive is encrypted using Bitlocker or anything else, or anything is blocking you access to the drive after shutdown, this exploit is impossible to do.

## Instructions
#### What you need:
- Your PC
- Braincells

### Steps
:::warning
This only works on old computers. We are not sure how old, as at some point Windows started including admin passwords on the Recovery terminal. If you need to enter a password at the Terminal step, then this exploit will not work for you.
:::
1. First, you must get into Windows Recovery Mode. To do this, hold Shift while pressing the Restart button on your Start Menu. 
2. From Recovery Mode, press Troubleshoot -> Advanced -> Command Prompt 
3. From the command prompt, type the following commands:
```
C:\
cd windows\system32
ren sethc.exe sethc.exe.bak
copy cmd.exe sethc.exe
```
4. Then, you may restart your pc.
5. After you restart, press shift around 8 times at login and a terminal will open up. Type `control userpasswords2` to open up the control panel.
6. Click on your user and press **Properties**. Go to Group Membership and you can press Administrator to become an admin. Press OK, and press OK again to become an admin.



## End Note
That's everything! If you need more help, you can reach out to us on your [Discord](https://discord.gg/elude) server or on [Reddit](https://reddit.com/r/sneakersneet). We will likely respond faster on Discord, however please still be patient.