---
layout: post
title:  "Running Windows Legacy Programs On a Modern OS"
date:   2022-09-17 08:00:00 -0700
categories: retro
---

I'm going to go over all the ways you can run your legacy programs from MSDOS to 16-bit Windows applications. 

With each iteration of Windows, more and more features are either taken out or replaced by more modern ones. This causes many of your older legacy programs to stop working. For a time, Microsoft would continue support for these old programs by leaving libraries to run within what they would call a "compatibility layer". Now days, you will need to use third party tools to run these programs. Many businesses still rely on these legacy programs to run their business and as a result, refuse to upgrade critical machines from Windows XP or Windows 7, opening themselves up to many cyber attacks. Some IT teams will sometimes rely on containers and or virtualization to continue with support, and prevent internet access to these installations, but wouldn't it be better to run your legacy apps without having to do any of that? 

Here are all the ways you can run these programs without installing older versions of Windows. 

**Disclaimer:** I will avoid providing info from 32Bit versions of Windows 10 since this will soon be no longer supported, though that is an option by turning on the NTVDM Windows Feature. Most machines today run 64Bit operating systems and so I opted to not include it. I will also not be include anything that may not be legal. The WINE project for Linux, OSX, and BSD is also another one that works but not included in this since 16-bit apps require loss of security according to their documentation FAQ. 


# All OSs

## DOSBOX

DOSBOX is an emulator that runs all your MSDOS software. It is easily customizable to make sure that those programs work correctly including clock speeds. Your performance will vary here and will likely need to do your own research on how to get your specific program working. One problem you may have is getting the output to anywhere on your machine. It relies on you to configure mounts and mappings of specific folders which can be configured. 

DOSBOX is available for all major operating systems. 

- [Download and install DOSBOX](https://www.dosbox.com/download.php?main=1)
- [Video Tutorial](https://www.youtube.com/watch?v=5yBr-n_ee2E)

# Windows

## WINEVDM
WINEVDM is a compatibility layer for WIN16bit applications, it will run within 64Bit versions of Windows. It is an open source project and your mileage may vary but so far I have been able to run programs as far back as Windows 1.0.
- [Github: WINEVDM](https://github.com/otya128/winevdm)

# Other

## Installing 32-bit Programs With 16-bit Setup Launchers

Some old programs from about 1995 to 1998 were using generic 16-bit InstallShield launchers to install 32-bit programs. As you can imagine, these programs are still compatible with modern Windows, but won't install because of these generic InstallShield packages. You can simply download the 32-bit generic executable (usually named SETUP.EXE) and replace it with the 16-bit counterpart. You can read more [here in this forum post.](https://reactos.org/forum/viewtopic.php?p=90351)