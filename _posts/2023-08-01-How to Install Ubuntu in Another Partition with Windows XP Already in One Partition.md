---
type: posts
layout: splash
author_profile: true
title: How to Install Ubuntu in Another Partition with Windows XP Already in One Partition
---
# How to Install Ubuntu in Another Partition with Windows XP Already in One Partition

In 2018, I needed installing a Ubuntu to implement a risk model. I'd like to mark it down for reference. 

Most blogs are about installing Ubuntu on a fresh computer (tutorial.ubuntu.com), restoring OS (wiki how), installing Ubuntu along with windows OS (to cram them into one partition or use windows 10's self contained mechanism, see lifiwire.com for an example), installing Ubuntu in a VM (linus.nci.nih.gov), etc. Few mentioned how to put Ubuntu and windows xp into two seperate partitions, which is today's theme.

## Environment: 
lenovo B460, window xp service package 3, intel core i3 380m, Ubuntu 18.04 lts(amd 64).
## Prepare:
1. figure out if your cpu is 32 bit or 64 bit, which decides which kind of release of Ubuntu you will use. To do this, refer to some how-to articles or those listing the whole series of intel cpus like wiki, i.e. the list of Intel Core i3 microprocessors. Of course the most authoritative way is to look it up in intel's product website, there is plenty information about intel core i3 380m( or yours), like whether it is intel 64 or has Physical Address Extensions. If it is intel 64, then march forward.
2. create a boot device. I am used to usb, so I utilize a kingston flash drive as my bootable device. As for how to create such a tool, there are massive references almost everywhere, you can refer to ubuntu forums to seek some help.
   - Note: Here's one thing worth marking, I had created a windows bootable usb stick using Laomaotao, which takes about 2 GB space, far smaller than the usb capacity, so I wonder if it can be partitioned, one for Laomaotao, the other for Ubuntu. Unfortunately, I failed in my specific situation(I have two computers, one is windows 10, the other is window xp, on which I will make a dual boot). With the windows bootable usb stick, windows 10's disk management tool can partition the usb properly, but the new partition can't be recognized by window xp. And what really weird is, that when I used disk management tool in window xp, window xp failed to give it a volume label and raised an error saying "Since the partition or volume is not activated......". Finally I gave up, and got two usbs, for two operating system respectively.
   - Attention here, I bet that you will feel a pain in the neck and waste a lot more time trying to maintain a multiboot USB, by adding/removing new/obsolete images onto it, as well as tweaking boot settings to make it work, than you would spend simply recreating USB for the image you actually need right now. With a decent USB with 3.0 port, creating a bootable drive takes less than 5 minutes.
3. decide the tools when creating a bootable usb. I use rufus, who doesn't surpport window xp since release 2.18. And rufus 2.18 won't recognize extra partitions in usb either. Refer to the official website to take advantage of this tiny open source tool.
4. prepare a free space into which Ubuntu will be installed. This can be done in two ways. One is that you simply mentally pick one partition ensuring that important files have been cleaned, then just plunge into the linux world. The other way is to actually make a new free partition from an existing one before booting. The only differece between these two approaches is whether you have to press the – to delete the partition when creating a Root, a Swap and a Home area (see step 3 in install section below). Details of both ways can be found immediately using google or bing.
## Installation:
1. Plug the USB into the computer and restart it. While booting the computer press your function key (defers from computer to computer) to go to the boot menu. Then, choose the option to boot from USB, this is not time consuming if you are familiar with boot menu.
2. Once you set your computer to boot from usb and restart again, you will be presented with option to try or install Ubuntu. Click on install. You will be presented with a few screen options to choose the language and keyboard layout. It will then do some checks on available space, power and internet connection etc. Better choose to connect the Internet with Ubuntu 18.04 lts.
![prepare to install ubuntu](/assets/images/prepare to install ubuntu.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
<!---
https://stackoverflow.com/questions/15764242/is-it-possible-to-make-relative-link-to-image-in-a-markdown-file-in-a-gist, Relative paths to images do work, but when you're writing a markdown file directly from the github web app, the images don't show up in preview. Once you commit the file the images are visible as expected
-->