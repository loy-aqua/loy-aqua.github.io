---
title: "Arch Linux on a VPS"
categories: misc
---

### Convert your VPS to Archlinux
---
This script will convert a VPS, running another linux distro, to Arch Linux.

>The script will delete any data in your VPS!

```shell
$ wget http://tinyurl.com/vps2arch
$ chmod +x vps2arch
$ ./vps2arch
```

### Pacman Note
---
Clean up outdate and orphan packages.
```shell
$ pacman -Rsn $(pacman -Qdtq)
```

### Install an AUR Helper
---
Yay is based on the design of yaourt, apacman and pacaur. It is developed with these objectives in mind:

* Provide an interface for pacman
* Yaourt-style interactive search/install
* Minimal dependencies
* Minimize user input
* Know when git packages are due for upgrades

```shell
$ git clone https://aur.archlinux.org/yay.git
$ cd yay
$ makepkg -si
```

### Enable BBR
---
The BBR congestion control algorithm can help achieve higher bandwidths and lower latencies for internet traffic. First, load the tcp_bbr module.
```shell
$ net.core.default_qdisc = fq  
$ net.ipv4.tcp_congestion_control = bbr  
```
