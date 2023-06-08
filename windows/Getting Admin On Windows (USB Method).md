---
tags: bypasses
---
# Getting Admin On Windows (USB Method)
### Exploit Description
Windows is vulnerable to a backdoor that allows you to access an admin command prompt at login. This exploit is rather minor as any backdoors on the device can be easily removed with the use of `sfc /scannow` or `dism /Online /Cleanup-Image /RestoreHealth`, although this is only if it is detected. Otherwise, it is undetectable.

The exploit is often done by replacing an executable or service that is available to you at login with a copy of the command prompt, such as the accessibility options (utilman.exe), or sticky keys (sethc.exe). This does however require you to have access to the file system, so if the drive is encrypted using Bitlocker or anything else, or anything is blocking you access to the drive after shutdown, this exploit is impossible to do.

## Instructions
#### What you need:
- A USB to boot
- A Linux Image (Any distribution works, we recommend Tails)
- The ability to boot a USB on  the desired computer (This might not be possible if your BIOS is locked)
- Friends (actually we're not joking)
- A single braincell (Please?)
- Common sense

If nothing is working, you can open a ticket on our discord server for help. The following guide is based on the TAILS operating system, but it should be adaptable to any Linux distribution. Unfortunately, in order to get a USB with a Linux, you need a friend who is willing to help you.


### Steps:
#### Part 1 (Creating a bootable flash drive)
:::warning
The following steps must be done on your friend's computer, **not** your own as Rufus requires admin priveleges to set the data partition of the USB as bootable. No imaging software can get around this without delivering a non-functioning install.
:::
1. First and foremost, we need to download an imager to actually flash a linux image to our USB. The one we often recommend, and the one we will use is Rufus. You can download the latest version from [here](https://github.com/pbatard/rufus/releases/). Click on `rufus-#.##.exe`
2. Next we need to get our Linux image. Download TAILS from [here](https://tails.boum.org/install/windows/index.en.html#download-img).
3. Open Rufus. You will be prompted admin priveleges, click yes. Once again this must be done on your friend's computer, **not** yours.
4. Click the dropdown underneath "Device" and select your USB. I recommend removing any other removeable mediums as to not be confused. 
5. Below the dropdown should be the Boot Selection. Press the button with "SELECT" in caps and navigate to the ISO file for TAILS.
6. Leave all other options as default and press the START button. This will take some time so I recommend you find something else to do in the mean time. 
7. Once your image has finally been written to the USB, you are ready to proceed on to the next part of the bypass.

#### Part 2 (Booting the USB)
:::warning
This guide must be done on the target computer you wish to perform the bypass on, **not** the one that you created your bootable USB on. If you successfully created the bootable USB, then using it on the same computer you created it on would be pointless as you already have admin.
:::
1. Before we boot the USB and mount our filesystem we need to make sure that Windows is **fully shutdown** and not in any other alternative state. If you do not successfully shudown Windows completely, the file system will be read-only and you will be unable to write to it.
2. In order to completely shutdown Windows, the best way to accomplish this is holding **SHIFT** while clicking the **SHUTDOWN** button in the start menu. You must keep holding shift, even during any other prompts that may happen afterwards. You can release shift once the screen is completely dark.
3. Next, you will have to enter you BIOS/UEFI menu on your compouter. Once again, you must be able to access it in order to boot your USB drive, unless somehow flash drives are already first in your computer's boot order. This step is machine specific, so you should google how to boot a USB for your particular manufacturer.
4. Once TAILS is booted, it will prompt you for root password set at the Welcome Screen. This may not be the same for other distros, but regardless make sure you are done with any other setup before you try to attempt the next few steps.
5. After you got that out of the way, open the TAILS menu and launch the `Root Terminal`
6. The next thing we have to do is mount the data partition of Windows. Some distributions automatically mount drives however this won't be the case for TAILS. In the terminal, run `lsblk` to show the physical drives, their partitions, and their mount locations—if there are any.
7. Windows will most likely be `/dev/sda`, though the data partition will be `/dev/sda1`. This might differ on certain systems but this is usually the case. The output from `lsblk` will have a column with the 'Mount Point'. If it's blank, then it's not mounted.
8. To mount the windows filesystem, we first need to create the folder that the filesystem will be mounted on. Traditionally, we use a subdirectory of `/mnt`. On your terminal, run  ```mkdir /mnt/windows``` to create a subdirectory named Windows.
9. Then to mount the partition, run `mount /dev/sda1 /mnt/windows`. 

#### Part 3 (Performing the exploit)
:::info    
Any commands that are run in the entire guide **must** be in lowercase, Linux is case sensitive. Spelling is important!
:::
1. Once you have finally mounted the partition, you can enter it with `cd /mnt/windows`.
2. If you hit `ls` you should see a typical Windows system, along with the Windows folder, which we need to modify.
3. Run `cd Windows/System32` to go to the  _System32_ folder. **Do not forget the forward slashes.**
4. Now in case you might want to get the old executable back and remove the backdoor, we recommend you keep a backup of it. The executable you replace depends on what you have. If you have the accessibility options (Ease of Access) on login, you will use that: `utilman`. If you do not, you should use sticky keys: `sethc`
5. To create the backup, run `cp [yourexecutable].exe [yourexecutable].exe.bak`. For example `cp sethc.exe sethc.exe.bak` or `cp utilman.exe utilman.exe.bak`
6. Next we will copy the command prompt as your executable. Run `cp cmd.exe [yourexecutable].exe` for example `cp cmd.exe sethc.exe` or `cp cmd.exe utilman.exe`
7. That's it! Now, all you need to do is reboot to your Windows system.
8. Once your at login, click the Ease of Access button or spam shift around 8 times (depending on whether you chose accesibility options or sticky keys)
9. A command prompt with admin priveleges will open up. In the command prompt, run `control userpasswords2`
10. Click on your user and press **Properties**. Go to Group Membership and you can press Administrator to become an admin. Press OK, and press OK again to become an admin.

## End Note
That's everything! If you need more help, you can reach out to us on your [Discord](https://discord.gg/elude) server or on [Reddit](https://reddit.com/r/sneakersneet). We will likely respond faster on Discord, however please still be patient.