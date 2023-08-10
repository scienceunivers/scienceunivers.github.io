---
type: posts
layout: splash
author_profile: true
title: How to Install Ubuntu in Another Partition with Windows XP Already in One Partition
---
## Table of Content
<!--https://stackoverflow.com/questions/11948245/markdown-to-create-pages-and-table-of-contents
-->
1. [Environment](#environment)
2. [Installation](#installation)
# How to Install Ubuntu in Another Partition with Windows XP Already in One Partition

In 2018, I needed installing a Ubuntu to implement a risk model. I'd like to mark it down for reference. 

Most blogs are about installing Ubuntu on a fresh computer (tutorial.ubuntu.com), restoring OS (wiki how), installing Ubuntu along with windows OS (to cram them into one partition or use windows 10's self contained mechanism, see lifiwire.com for an example), installing Ubuntu in a VM (linus.nci.nih.gov), etc. Few mentioned how to put Ubuntu and windows xp into two seperate partitions, which is today's theme.

## Environment 
<!---<a name="Environment"></a>-->
lenovo B460, window xp service package 3, intel core i3 380m, Ubuntu 18.04 lts(amd 64).
## Prepare:
1. figure out if your cpu is 32 bit or 64 bit, which decides which kind of release of Ubuntu you will use. To do this, refer to some how-to articles or those listing the whole series of intel cpus like wiki, i.e. the list of Intel Core i3 microprocessors. Of course the most authoritative way is to look it up in intel's product website, there is plenty information about intel core i3 380m( or yours), like whether it is intel 64 or has Physical Address Extensions. If it is intel 64, then march forward.
2. create a boot device. I am used to usb, so I utilize a kingston flash drive as my bootable device. As for how to create such a tool, there are massive references almost everywhere, you can refer to ubuntu forums to seek some help.
   - >[!NOTE]
     >Here's one thing worth marking, I had created a windows bootable usb stick using Laomaotao, which takes about 2 GB space, far smaller than the usb capacity, so I wonder if it can be partitioned, one for Laomaotao, the other for Ubuntu. Unfortunately, I failed in my specific situation(I have two computers, one is windows 10, the other is window xp, on which I will make a dual boot). With the windows bootable usb stick, windows 10's disk management tool can partition the usb properly, but the new partition can't be recognized by window xp. And what really weird is, that when I used disk management tool in window xp, window xp failed to give it a volume label and raised an error saying "Since the partition or volume is not activated......". Finally I gave up, and got two usbs, for two operating system respectively.
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
>[!NOTE]
>I advise enabling both Download updates and Install third-party software. Continue. Then in my case it took about 10 minutes to wait until it showed another screen. The screen you should pay attention to is Installation Type. Choose Something else, wrapped by green rectangle below.

![install ubuntu 1](/assets/images/install ubuntu 1.jpg){:style="display:block; margin-left:auto; margin-right:auto"}
3. Click on the desired partition and press the – to delete the partition. Create a Root, a Swap and a Home area.
![install ubuntu 2](/assets/images/install ubuntu 2.jpg){:style="display:block; margin-left:auto; margin-right:auto"}

Create a root partition first. Choose the free space available and click on +. Here, choose the size of root directory, choose ext4file system, and mount point as /.

As for the type of the partition, I have to admit that some rarely seen situations had come to me. When I first installed ubuntu on B460 at 201807, I can recall I had chosen primary for all of the three partitions, and it's ok, the number of these partitions are naturally sda8,sda9,sda10, following the windows partition whose name is sda7 (sda1 holds xp, sda5 holds programs, sda6 holds movies), holding my MATLAB installation. 

But when I reinstall ubuntu due to some fucking strange reasons at 201906, the linux partitions are no more 8,9,10, they are sda3(root) , sda4 (swap), and when I wanted to allocate some space for home, it says the leftover space is unusable, no matter which partition type I choose. 

I have no idea why. I know it has something to do with partition mechanism the hard disk uses, namely the number of primary partitions are at most four (for details , see 鸟哥linux私房菜), which explains why the leftover is unusable after the sda4 has been alloacated. But why did I make it at 201807? Of course there is a possibility that my memory went wrong, that is the installation wizard choose logical partition by default.
![install ubuntu 3](/assets/images/install ubuntu 3.png){:style="display:block; margin-left:auto; margin-right:auto"}
Next we will create swap. Click on the, use the file type as Swap area, suggestible size is RAM*2. To create Home, try to allocate the maximum space (in fact allocate it rest of the free space) to Home because this is where you'll be downloading and keeping files, I don't add the corresponding pictures here because it's basically similar as creating Root. 

4. Once you are ready with Root, Swap and Home, click on Install Now, on which I spent about half an hour. Rest is some trivial steps. You will be taken through screens to select time zone, login details, etc. 

If you run across any problems that haven't been covered during the above process, just google or bing it, never expect to solve a theoretical or practical puzzles racking your brain with Baidu.

Note: All the pictures are from the Internet, not my screen shot, so it may be somewhat out of date, but is enough to get a relatively well understanding of dual booting in a primitive OS.
