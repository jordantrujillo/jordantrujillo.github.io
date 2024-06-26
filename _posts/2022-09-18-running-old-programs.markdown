---
layout: single
title:  "Running Windows Legacy Programs On a Modern OS"
date:   2022-09-17 08:00:00 -0700
tags: retro windows dos 16bit legacy software emulation dosbox winevdm installshield
---

I'll go over how to run legacy programs ranging from MSDOS to 16-bit Windows applications. 

With each new version of Windows, more features are either removed or replaced by more modern ones. As a result, many of your older legacy programs will no longer function. For a time, Microsoft would continue to support these old programs by allowing libraries to run within a "compatibility layer." To run these programs nowadays, you will need to use third-party tools. Many businesses continue to rely on legacy programs to run their operations and, as a result, refuse to upgrade critical machines from Windows XP or Windows 7, leaving them vulnerable to a variety of cyber attacks. Some IT teams will rely on containers or virtualization to continue support and prevent internet access to these installations, but wouldn't it be preferable to run your legacy apps without having to do any of that? 

Here are some methods for running these programs without having to install older versions of Windows. 

**Disclaimer:** I will avoid providing information from 32Bit versions of Windows 10 because they will soon be deprecated, though they can still be used by activating the NTVDM Windows Feature. Because most machines today run 64-bit operating systems, I chose not to include it.
I will also not include anything that may be illegal, such as stolen Microsoft code. The WINE project for Linux, OSX, and BSD also works, but according to their documentation FAQ, 16-bit apps require OS modifications that will result in security holes. For that reason I have also not included WINE. 

# All OSs

## DOSBOX

DOSBOX is an emulator that allows you to run all of your MSDOS software.
It is easily customizable to ensure that those programs, including clock speeds, work properly.
Your performance will vary here, and you will most likely need to conduct your own research to figure out how to get your specific program to work. One issue you may encounter is getting the output to appear anywhere on your machine.
It is up to you to configure mounts and mappings of specific folders that are configurable. 

DOSBOX is available for all major operating systems. 

- [Download and install DOSBOX](https://www.dosbox.com/download.php?main=1)

# Windows

## WINEVDM
WINEVDM is a compatibility layer for WIN16bit applications, it will run within 64Bit versions of Windows. It is an open source project, so your mileage may vary, but I have been able to run programs dating back to Windows 1.0 so far. 
- [Github: WINEVDM](https://github.com/otya128/winevdm)

# Other

## Installing 32-bit Programs With 16-bit Setup Launchers

Some old programs from about 1995 to 1998 were using generic 16-bit InstallShield launchers to install 32-bit programs. As you can imagine, these programs are still compatible with modern Windows, but won't install because of these generic InstallShield packages. You can simply download the 32-bit generic executable (usually named SETUP.EXE) and replace the 16-bit version of the executable file. You can read more [here in this forum post.](https://reactos.org/forum/viewtopic.php?p=90351)