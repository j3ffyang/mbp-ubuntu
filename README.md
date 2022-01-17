## Install Ubuntu 20.04 on MacBook Pro 16,2 with Broadcom 4364 Chipset

My objective is simple: install Ubuntu 20.04 on MacBook 16,2. It's known this model has T2 security chip. I tried many methods to enable Broadcom 4364 for wireless, including instruction from https://wiki.t2linux.org/guides/wifi/, but no luck.

Here's my hardware

```sh
jeff@mbp:~$ lspci -vvnn | grep -i network
e5:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4364 802.11ac
    Wireless Network Adapter [14e4:4464] (rev 04)
    Subsystem: Apple Inc. BCM4364 802.11ac Wireless Network Adapter [106b:07bf]
jeff@mbp:~$
```

Manually placed Broadcom firmware. __Make sure you backup `/lib/firmwire/brcm`__ if existing

```sh
## Backup `/lib/firmware/brcm` if existing
wget https://github.com/j3ffyang/mbp-ubuntu/blob/master/files/brcm.tar.gz
cd /lib/firmware/; sudo tar -xzvf brcm.tar.gz
```

<img src="./images/20220116_ubuntu2004_mbp_t2.png">

I'm using the latest kernel up to date of writing this document

```sh
Linux mbp 5.16.0-t2 #2 SMP PREEMPT Wed Jan 12 11:25:28 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
```

Reference
- https://github.com/marcosfad/mbp-ubuntu
- https://github.com/AdityaGarg8/T2-Ubuntu-Kernel/
