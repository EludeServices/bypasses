---
tags: bypasses
---
# Removing ScreenTime

### Exploit Description
Read the description about Removing MDM Restrictions. Its basically the exact same, but instead of removing MDM your adding an MDM that restricts Screen Time. What happens when Screen Time is disabled? Well, you just won't have any!

## Instructions
#### What you need:
- A computer with admin privileges.
- [iBackupBot](http://www.icopybot.com/ibackupbot_setup.exe)
- [iTunes](https://www.apple.com/itunes/download/win64)
- A USB-A to Lighting Cable (there are a bunch of cheap ones on amazon, try to use an official one)
- Braincells
- Not common sense because who actually knows this shit
- The ability to read and write

### Steps
:::info
You **MUST** have a USB-A to Lightning cable that works reliably. Without it, the entire exploit falls apart.

Also, this works on all iOS and iPadOS devices.
:::
1. Install [iTunes](https://www.apple.com/itunes/download/win64) and [iBackupBot](http://www.icopybot.com/ibackupbot_setup.exe) on your computer.
2. Download [this](https://cdn.discordapp.com/attachments/731164883495944253/1091167187143753728/screentimebypass.zip) file.
3. Extract the zip you just downloaded. You will see several plist files in a folder.
4. Open itunes and wait for it to recognize your phone (must be plugged in with a usb-a to lightning cable)
5. Click the tablet/phone icon in iTunes near the left corner and press Backup Now (make sure to enter the pin to trust the computer)
6. You now have a backup. Open iBackupBot and press OK on all errors; they don't matter. iTunes backups will automatically load.
7. Press plus on the most recently made backup.
8. Press on system files (not the plus, just press it) and search for `configuration`
9. Click on `SysSharedContainerDomain-systemgroup.com.apple.configurationprofiles`, click on `library`, and click on `configuration profiles`. Delete any existing files in this folder.
10. Press import and navigate to the place the plist files are stored.
11. Select the first file in the folder, scroll all the way down and use shift to select the last file in the folder to select them all. Then press open.
12. iBackupBot may complain about it being "not a valid path". This is expected. Just check "do this for all conflicts" and press yes.
13. Go back to itunes and click Restore Backup, and then press restore. At this point iTunes should only detect one backup. Please delete any other backups except this one for the sake of simplicity from `%appdata%\Apple Computer\MobileSync\Backup` on your PC.
14. Wait some time and screen time will become restricted, so you literally won't be able to get screen time on your phone anymore unless you delete the mdm profile.

## End Note
That's everything! If you need more help, you can reach out to us on your [Discord](https://discord.gg/elude) server or on [Reddit](https://reddit.com/r/sneakersneet). We will likely respond faster on Discord, however please still be patient.