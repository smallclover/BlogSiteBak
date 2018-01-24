# LVM(Logical Volume Manager)逻辑卷管理器

## 名词

|中文名|英文简称及全称|作用|
|--------|-----------------|-----|
|物理卷|PV,Physical Volume|整个硬盘设备或者使用fdisk命令建立的硬盘分区|
|卷组|VG,Volume Group|由一个或多个物理卷（PV）组成的整体|
|逻辑卷|LV,Logical Volume|从卷组（VG）处切割出的空间用于创建文件系统，大小由PE的个数决定|
|本单元|PE,Physical Extent|默认为4MB的基本块|

## 命令

注：LVM相关的命令都是如下格式：
[英文简称]+[操作]
如：显示物理卷信息的命令是pvdisplay

|功能/命令|物理卷管理|卷组管理|逻辑卷管理|
|-----------|------------|-----------|------------|
|扫描|pvscan|vgscan|lvscan|
|建立|pvcreate|pvcreate|lvcreate|
|显示|pvdisplay|vgdisplay|lvdisplay|
|删除|pvremove|vgremove|lvremove|
|扩展|vgextend|lvextend||
