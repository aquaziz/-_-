dnf install nginx
nano /etc/nginx/nginx.conf
меняем конфиг по заданию 
в нашем случае 
![image](https://github.com/user-attachments/assets/009b44b8-1cf5-4cae-ae55-ac43d4d3ae18)


сохраняем 
проверяем
_____________________________________________________________________________
другой пункт
adduser webdev (name по заданию)
dnf install lighttpd
nano /etc/lighttpd/ lighttpd.conf
![image](https://github.com/user-attachments/assets/cbc186a4-e818-4a74-af5f-0aeb85241a5e)

server port - 81
там еще что то надо, не помню
![image](https://github.com/user-attachments/assets/5290f543-4914-4085-8f17-1552e5b1c0ce)

Chmod -R 750 /opt/data
Chown -R lighttpd:lighttpd /opt/data
setenforce 0 
Restorecon -Rv
nano /etc/selinux/config
permissive
