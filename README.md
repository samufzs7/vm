# Deprecation notice
I declare this script to now be deprecated. Parsec has made advancements recently to improve the streaming experience and quality to match that of Moonlight. Not only that but a combination of updates to Windows and NVIDIA's drivers have broken (intentionally or not) the method this script uses to enable GameStream on GeForce Experience. While I still have interest in this topic and may in the future research a way to enable GameStream on current versions of GeForce Experience, the methods used there will be totally different from the ones in this script, rendering this one outdated. If you are still interested in an alternative to Parsec for cloud gaming, consider using [tomgrice's script for Sunshine](https://github.com/tomgrice/cloudgamestream-sunshine). Thank you for the positive messages about this project.

# Cloud NVIDIA GameStream

## What is it?
A Powershell one-click solution to enable NVIDIA GeForce Experience GameStream on a cloud machine with a GRID supporting GPU. There was a [thread discussing this in the xda-developers forum](https://forum.xda-developers.com/showthread.php?t=2394478) but the whole process was unclear in which versions of the GRID drivers and GeForce Experience to use and required some tedious installation and workarounds since the GeForce Experience that supported it would automatically update to the newest one. This script will solve all the issues with one single script.  
&nbsp;  
&nbsp;  

## Installation
Copy and paste these commands in the machine's powershell prompt:
```
[Net.ServicePointManager]::SecurityProtocol = "tls12, tls11, tls";Set-ExecutionPolicy Unrestricted;Invoke-WebRequest -Uri https://github.com/acceleration3/cloudgamestream/releases/download/resolution-fix/cloudgamestream.zip -OutFile arch.zip;Add-Type -Assembly "System.IO.Compression.Filesystem";$dir = [string](Get-Location);rmdir -r cloudgamestream-master -ErrorAction Ignore;[System.IO.Compression.ZipFile]::ExtractToDirectory($dir + "\arch.zip", $dir);cd cloudgamestream;./Setup.ps1
```
Or you can download the script and binaries from [here](https://github.com/acceleration3/cloudgamestream/releases/download/resolution-fix/cloudgamestream.zip).  
&nbsp;  
&nbsp;  

## Compatibility
Tested and working on the following:

* OS:
	* Windows 10 Pro (**Windows 10 works, albeit only with some older NVIDIA driver versions. I will try to figure out if something can be done for newer drivers.**)
	* Windows Server 2019
	* Windows Server 2016
	
* Platforms:
	* Azure NV6_Promo Tesla M60
	* Amazon AWS EC2 g4dn.large Tesla T4
	* Google Cloud Platform Tesla T4
	* Google Cloud Platform Tesla P4
	
&nbsp;  
**WARNING: Machines provided by Shadow.tech supposedly have incompatibility with GeForce Experience and may brick your VM.**  
&nbsp;  
&nbsp;  
&nbsp;  
## FAQ
### Will this work on \<insert platform and instance name here\>?
I am building a list of platforms it currently supports, so if you've tested it yourself and it works, please message me on reddit `/u/acceleration3` with the information on your VM. If it doesn't work you can also message me with details and I will try and change the script to support your VM.

### The script didn't enable my GameStream at all.
  Remember that the feature **will not show up on GeForce Experience on a Microsoft Remote Desktop session**. I recommend using AnyDesk as an alternative. If it still doesn't work then the script doesn't currently support your machine. 

### I can't connect to my VM using Moonlight.
  You need to forward the ports on your machine. The ports you need to forward are 47984, 47989, 48010 TCP and 47998, 47999, 48000, 48010 UDP. If you're having more problems try downloading the [Moonlight Internet Streaming Tool](https://github.com/moonlight-stream/Internet-Hosting-Tool/releases) and troubleshooting it.

### GeForce Experience requires me to login. Do I have to create/use an NVIDIA account?
  Yes.

### This GeForce Experience version doesn't support my game. What do I do?
  You can stream your entire desktop with GeForce Experience. Just add `C:\windows\system32\mstsc.exe` to the applications list and launch that with Moonlight.

### Can I load custom EDID data?
  Yes, but the EDID files **need to be compatible with NVIDIA's EDID format**. You can try changing the EDID data by editing the `C:\ResFix\edid.txt` file. Create a backup of the original file in case it isn't compatible.
&nbsp;  
&nbsp;  
&nbsp;
## Some good tutorial videos
### Installing on AWS
  [Moonlight on AWS - DIY 4K Cloud Gaming Tutorial | Cloud Gaming](https://www.youtube.com/watch?v=u9N_vonzn8A) by TechGuru 
### Installing on GCP
  [Moonlight on Google Cloud Platform - Cloud Gaming Tutorial](https://www.youtube.com/watch?v=kNZ6NhPJYfA) by John Ragone
# vm
