---
tags: bypasses
---
# Removing MDM Restrictions

### Exploit Description
This exploit was found by @rsa16 in his attempt to remove restrictions off of his school ipad. It works on all major versions of iOS and has still not been reported to this day.

iOS allows you to create and restore backups of the system. If you've ever tried resetting your ipad with MDM, you may find that when your setting it up again the Remote Management screen pops up and registers your iPad with the MDM profile. This happens because the profile is embedded on your iPad, even in backups. 

Now, what if we restore a backup that doesn't have an MDM profile. The profile will go away! It's simple.

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
:::warning
**LOSING THE BACKUP FILE THAT ITUNES AUTOMATICALLY CREATES BEFORE A RESTORE WILL RESULT IN AN INABILITY TO PLACE MDM RESTRICTIONS BACK. DO THIS AT YOUR OWN RISK**
:::

#### Removing Restrictions
1. Install [iTunes](https://www.apple.com/itunes/download/win64) and [iBackupBot](http://www.icopybot.com/ibackupbot_setup.exe) on your computer.
2. On your iOS device's settings, turn off Find My Ipad. If it's already off, thats perfectly fine. If you don't want to turn it off, that is fine as well, however it is recommended that you turn it off as otherwise your device will be locked to your Apple ID. This, as you can imagine, isn't always a good thing. If you want to sign out of your Apple ID, turn this off.
3. Connect your device to your computer with the cable, preferably an official one. Bootlegs are not recommended as they will not always work as well.
4. Open iTunes and wait for it to recognize your device. Once it does, click on the tablet icon near the left corner and press backup now.
5. It will prompt you to enter your PIN to trust this computer on your device. Do so.
6. You now have a backup. Open iBackupBot and press OK on all errors; they don't matter. iTunes backups will automatically load.
7. Press plus on the most recently made backup.
8. Press on system files (not the plus, just press it) and search for `configuration`
9. Click on `SysSharedContainerDomain-systemgroup.com.apple.configurationprofiles`, click on `library`, and click on `configuration profiles`. This is where you will find your MDM Profile.
10. Delete all the files in this folder.
11. Press system files again and search for `managed`
12. Click on `ManagedPreferencesDomain`, click `mobile`, and delete `com.apple.SystemConfiguration.plist` and `com.apple.webcontentfilter.plist` if they exist. The first one may contain a proxy for the MDM, and the second as you may guess is the content filter for websites. We want to remove those.
13. Go back to itunes and click Restore Backup, and then press restore. At this point iTunes should only detect one backup. Please delete any other backups except this one for the sake of simplicity from `%appdata%\Apple Computer\MobileSync\Backup` on your PC.
14. Wait some time and all should work out fine! You *will* end up with another backup. Remember its date and time and note it down somewhere. This is the backup you will use to restore restrictions, if you ever need to.

#### Restoring Restrictions
1. Open iTunes
2. On your iOS device's settings, turn off Find My Ipad. If it's already off, thats perfectly fine. If you don't want to turn it off, that is fine as well, however it is recommended that you turn it off as otherwise your device will be locked to your Apple ID. This, as you can imagine, isn't always a good thing. If you want to sign out of your Apple ID, turn this off.
3. Connect your device to your computer with the cable, preferably an official one. Bootlegs are not recommended as they will not always work as well.
4. Open iTunes and wait for it to recognize your device. Once it does, click on the tablet icon near the left corner. Find the backup with the date and time from before you removed MDM, and click on it. Then press restore. 
5. It will prompt you to enter your PIN to trust this computer on your device. Do so.
6. Wait some time and all will be fine. From here we recommend deleting all backups from `%appdata%\Apple Computer\MobileSync\Backup` and just make a new backup for simplicity.

## End Note
That's everything! If you need more help, you can reach out to us on your [Discord](https://discord.gg/elude) server or on [Reddit](https://reddit.com/r/sneakersneet). We will likely respond faster on Discord, however please still be patient.