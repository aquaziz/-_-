dnf install nginx
nano /etc/nginx/nginx.conf
меняем конфиг по заданию 
в нашем случае 
![[Pasted image 20250305010720.png]]

сохраняем 
проверяем
_____________________________________________________________________________
другой пункт
adduser webdev (name по заданию)
dnf install lighttpd
nano /etc/lighttpd/ lighttpd.conf
![[Pasted image 20250305010957.png]]
server port - 81
![[Pasted image 20250305011030.png]]
Chmod -R 750 /opt/data
Chown -R lighttpd:lighttpd /opt/data
setenforce 0 
Restorecon -Rv
nano /etc/selinux/config
permissive
