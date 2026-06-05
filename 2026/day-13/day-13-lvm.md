# Day 13 – Linux Volume Management (LVM)


## Task

* Learn LVM to manage storage flexibly – create, extend, and mount volumes.

## Task 1: Check Current Storage

<img width="973" height="322" alt="image" src="https://github.com/user-attachments/assets/a450fed6-f76a-41a2-be76-860ecb14c825" />


## Switch to root user:

sudo -i

Run: lsblk, pvs, vgs, lvs, df -h



## Task 2: Create Physical Volume


<img width="790" height="326" alt="image" src="https://github.com/user-attachments/assets/3fd9c7ac-1db0-46d7-9f7b-7169555fc531" />



Run: lsblk, lvm

lvm> pvcreate /dev/nvme1n1 /dev/nvme2n1 /dev/nvme3n1

lvm> pvs

  PV           VG     Fmt  Attr PSize   PFree
  
  /dev/nvme1n1        lvm2 a--  <10.00g  10.00g
  
  /dev/nvme2n1        lvm2 a--  <12.00g  12.00g
  
  /dev/nvme3n1        lvm2 ---   14.00g  14.00g
  
lvm>



## Task 3: Create Volume Group

lvm> vgcreate tws_lg /dev/nvme1n1 /dev/nvme2n1 /dev/nvme3n1
lvm> vgs

root@ip-172-31-42-234:~# lvm

lvm> vgs

  VG     #PV #LV #SN Attr   VSize  VFree
  
  tws_lg   2   1   0 wz--n- 21.99g 11.99g
  
lvm>



## Task 4: Create Logical Volume


lvm> lvcreate -L 10G -n tws_lg tws_lv

lvm> lvs

lvm> lvs

  LV     VG     Attr       LSize  Pool Origin Data%  Meta%  Move Log Cpy%Sync Convert
  
  tws_lv tws_lg -wi-a----- 10.00g
  
lvm>


## Task 5: Format and Mount

root@ip-172-31-42-234:~# mkdir /mnt/tws_lv_mount

root@ip-172-31-42-234:~# mkfs.ext4 /dev/tws_lg/tws_lv

root@ip-172-31-42-234:~# mount /dev/tws_lg/tws_lv /mnt/tws_lv_mount

<img width="1091" height="751" alt="image" src="https://github.com/user-attachments/assets/cd68d8cd-90fa-4f72-af17-884e103fde95" />



<img width="800" height="449" alt="image" src="https://github.com/user-attachments/assets/76afcfe1-234a-4d6d-a1e8-d7044991b828" />


## Task 6: Extend the Volume

<img width="1207" height="483" alt="image" src="https://github.com/user-attachments/assets/946e6b0c-5068-4a56-9b8f-494064db0ffe" />


lvextend -L +2G /dev/tws_lg/tws_lv
resize2fs /dev/tws_lg/tws_lv

root@ip-172-31-42-234:~# resize2fs /dev/tws_lg/tws_lv

resize2fs 1.47.2 (1-Jan-2025)

Filesystem at /dev/tws_lg/tws_lv is mounted on /mnt/tws_lv_mount; on-line resizing required

old_desc_blocks = 2, new_desc_blocks = 2

The filesystem on /dev/tws_lg/tws_lv is now 3145728 (4k) blocks long.


root@ip-172-31-42-234:~# df -h | grep mnt

/dev/mapper/tws_lg-tws_lv   12G  2.1M   12G   1% /mnt/tws_lv_mount

/dev/nvme3n1                14G  2.1M   13G   1% /mnt/tws_disk_mount

root@ip-172-31-42-234:~#


## Task 7: Mount Physical Volume Directly


<img width="613" height="62" alt="image" src="https://github.com/user-attachments/assets/93a0ab91-8ebe-4c25-8a3c-0fc649b4179e" />


<img width="1045" height="305" alt="image" src="https://github.com/user-attachments/assets/6aa88df7-e4ba-4529-a19b-634947993370" />


<img width="1123" height="428" alt="image" src="https://github.com/user-attachments/assets/5d833df3-dde7-44ab-87d5-9c5e894e900b" />


## Learnings
* How to add storage to instance
  
* How to create Physical, Logical and Volume Groups
  
* How to mount the volume
  
* How to Format the Volume













