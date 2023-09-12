---
title: 挂载mmcblk1磁盘分区
tags:
  - Linux
categories: 知识
abbrlink: mntDisk
sticky: 101
cover: https://s2.loli.net/2023/09/12/m4lSkpJeV18jMhy.webp
date: 2023-09-12 10:57:16
---

### 格式化mmcblk1
```bash
sudo mkfs.ext4 /dev/mmcblk1
```

### 创建挂载点目录
```bash
mkdir /mnt/sdcard
```

### 挂载分区到/mnt/sdcard
```bash
sudo mount /dev/mmcblk1 /mnt/sdcard
```
