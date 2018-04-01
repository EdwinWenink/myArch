# The following setup was run in a VirtualBox with 20G allocated space - by Edwin Wenink www.edwinwenink.xyz

# Setup and disk partitioning

## Working internet connection is required
1) ping google.com

## Show available space
2) fdisk -l 
3) cfdisk
	3a) choose 'dos' label type || choose 'gpt' only for harddisks bigger than 2TB
	
## Partition disk before installation 
In my virtualBox setup, I created three partitions (partition Id:83 type:Linux) 

4) Create primary, bootable disk (10G).  Write after creation.
5) Create partition for swap disk (2G). Write.
6) Create partition for remaining 8G. Write.

## Disk formatting in ext4 format
7) mkfs.ext4 /dev/sda1
8) mkfs.ext4 /dev/sda3

## Make a swap disk, and activate the swap
9) mkswap /dev/sda2
10) swapon /dev/sda2

## Mount the primary partition
11) /dev/sda1 /mnt

## Create home directory and mount on the remaining partition
12) mkdir /mnt/home
13) mount /dev/sda3 /mnt/home

# Installation

## Bootstrap Arch Linux
14) pacstrap /mnt base base-devel

## Create genfstab file
15) genfstab /mnt>> /mnt/etc/fstab

## Change system locale and time

## Root into installation directory to configure settings
16) arch-chroot /mnt/bin/bash

## Language settings
17) nano /etc/locale.gen
18) uncomment en_US.UTF-8 UTF-8

## Activate system language by running the shell
19) locale-gen 

## Add the language to the system by creating configuration file
20) nano /etc/locale.conf
21) add language LANG=en_US.UTF-8

## Time zone configuration, stored in:
22) ls user/share/zoneinfo

## Created symbolic link to desired country, in my case by:
23) ln -s /usr/share/zoneinfo/Europe/Amsterdam /etc/localetime

## Set time standard
hwclock -systohc --utc

# Finalization

## set root password
24) passwd

## Add hostname and save
25) nano /etc/hostname

## Enable dhcp
26) systemctl enable dhcpcd

## Install bootloader, in this case GRUB
27) pacman -S grub os-rober

## Install GRUB to disk, and initialize configuration file
28) grub-install /dev/sd
29) grub-mkconfig -o /boot/grub/grub.cfg

## Exit chroot and reboot to finalize
30) exit
31) reboot








