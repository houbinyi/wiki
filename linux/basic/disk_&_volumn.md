#block device view 
sudo fdisk -l

#volumn
sudo fdisk /dev/sdb
sudo parted

#volumn info
sudo lsblk

#volumn format
sudo mkfs -t ext4 -c /dev/sdb1  (-c check broken partition)
sudo mkfs.ext4 /dev/sdb1  -E lazy_itable_init
sudo mkfs.ext3 -T largefile /dev/sdb1

#view 
sudo blkid

#mount
sudo mount -t ext4 /dev/sdb1 /home/chaihuasong/1T/ 
sudo vim /etc/fstab
sudo mount -a

#size
df -h
df -T


