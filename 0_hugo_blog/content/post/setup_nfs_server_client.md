---
title: "Detailed steps to setup nfs server(archlinux) and client(windows)"
date: 2021-12-05T22:33:28+08:00
draft: true
---


## 使用的系统
Arch Linux(Ubuntu) & Win10

## 操作步骤

### 1. Install NFS server on Linux OS
```
archlinux : yay -S nfs-utils
ubuntu : sudo apt-get install nfs-kernel-server
```

### 2. Edit config file(/etc/exports)
Add below line in /etc/exports
```
/home/mengbao/mnt	*(rw,sync,no_subtree_check)
```


### 3. Start NFS server
#### 1. Archlinux
```
systemctl restart nfs-server
systemctl status nfs-server
```
#### 2. Ubuntu
```
systemctl restart nfs-kernel-server
systemctl status nfs-kernel-server
```

### 4. Enable NFS client on Win10
Control Panel\Programs\Trun windowns feature on or off
Services for NFS -> checked


### 5. Check UID & GID of Linux OS
```
[mengbao@minitana mnt]$ id
uid=1000(mengbao) gid=1000(mengbao) groups=1000(mengbao),108(vboxusers),998(wheel)
```

### 6. Add AnonymousGid & AnonymousUid in regedit
```
Open regedit by searching "regedit"
Add 2 files(DWORD(32 bit)) named AnonymousGid & AnonymousUid under below path:
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ClientForNFS\CurrentVersion\Default
Value of AnonymousGid is 1000(Decimal)
Value of AnonymousUid is 1000(Decimal)
```

### 7. reboot windowns

### 8. Edit 'hosts' on win10
Add below line in C:\Windows\System32\drivers\etc\host
```
192.168.0.112	archlinux
```
PS: 192.168.0.112 is IP address of linux OS

### 9. flush DNS on win10
```
ipconfig /flushdns
```

### 10. mount linux share folder on win10
mount \\archlinux\home\mengbao\mnt F: