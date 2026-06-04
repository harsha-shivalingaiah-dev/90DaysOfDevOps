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





