# Windows Terminal
Due to the fact that I use a mac at work, I wanted to set up a linux terminal on my personal machine. The Windows Terminal seemed like a great way to do this!

This repository is how I set up the Windows Terminal on my Windows 10 Machine. I still have a lot of stuff to figure out and expand on but here is the start!

Things I want to add/look into:
* Copy with Selected Text
* Paste with Control+v
* Check to see if I am using WSL 1 or WSL 2. The commands provided in guides do not work as is. (https://docs.microsoft.com/en-us/windows/wsl/wsl2-install) - It looks like you need to setup virtualization (Hyper-V) but with minimal testing it doesn't seem to work. Based on some research, you need a build version above 18917. I am currently on build 18362. I will look for a new version when it becomes available.
Run `systeminfo | Select-String "^OS Name", "^OS Version"` to get the current build number.
* I can't use the root user on Ubuntu - could be by design as root doesn't exist but I don't think so


## Setup
Update Windows to the latest distribution of Windows 10. Your Windows 10 version needs to be above 16215. You can install that here.

Once you have that, you can set up Ubuntu and `wsl`. I have chosen Ubuntu 18.04. Here are the instructions I followed for that.
https://docs.microsoft.com/en-us/windows/wsl/install-win10
Once you have installed and potentially restarted your computer, you should be able to open Ubuntu as an app and set-up a profile. You can also type `wsl` in a cmd.exe or powershell to open a terminal.


### Adding Ubuntu to Windows Terminal and Setting Default
Based on a comment on an article, I was able to find the `profiles.json` in this directory on my machine `C:/Users/<username>/AppData/Local/Packages/Microsoft.WindowsTerminal_8wekyb3d8bbwe/RoamingState/profiles.json`.

I have modified Windows Terminal to use Ubuntu as the default and added the logo from a directory I found.

### Adding Python aliases to your Linux Terminal
If you look at the `.bash_profile` in this directory you can see it is a simple alias to get python from your windows machine running (So you don't need to have two copies of Python - one Linux and one Windows - You could if you wanted to use `brew` or something).

Also, note that the directory is `/mnt/c/...`. This is referencing my `C:/` Drive based on the windows syntax! So if you want to add anything to your path, since you can't use colons, they have some symbolic linking I guess from that directory to your C Drive.

## Notes
* `C:/Program Files/WindowsApps/...` is a useful directory for everything Windows Terminal
* `C:/Users/<username>/AppData/Local/...` is a useful directory for if you enter `Packages` or `Microsoft/WindowsApps/`
* The bash prompt is taken from this great repo [.dotfiles](https://github.com/mathiasbynens/dotfiles/blob/master/.bash_prompt)
* If you run out of memory in your WSL then you need to expand the partition - https://docs.microsoft.com/en-us/windows/wsl/wsl2-ux-changes#understanding-wsl-2-uses-a-vhd-and-what-to-do-if-you-reach-its-max-size


## Other Useful Links
* [General Info about WT](https://devblogs.microsoft.com/commandline/windows-terminal-microsoft-store-preview-release/)
* [Windows Terminal Source Code](https://github.com/microsoft/terminal)
