
lsblk (показывает все диски какие у нас имеются)

			mdadm - -create /dev/md0 -l1 -n 2 /dev/sdb /dev/s 

/dev/md0 - название

-l - это level raid 

-n - количество дисков 

Continue creating array? Yes

mdadm  - -detail /dev/md0 проверка

mkdir /opt/data

mkfs.xfs /dev/md0 создание xfs 

blkid /dev/md0 для просмотра id диска

cp /etc/fstab /etc/fstab_bak резерв

blkid /dev/md0 >> /etc/fstab

nano /etc/fstab

UUID=asdas091432naffa  /opt/data xfs defaults 0 0

systemctl daemon-reload

mount -a

**