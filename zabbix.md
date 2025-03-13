dnf install httpd zabbix-apache-conf zabbix-sql-scripts

systemctl enable httpddnf install postgresql13 postgresql13-server

systemctl enable postgresql-13

/usr/bin/postgresql-13-setup initdb

systemctl start postgresql-13

dnf install zabbix-server-pgsql zabbix-web-pgsql zabbix-agent

nano /etc/php.ini

_date.timezone = Europe/Moscow #обязательно укажите свой часовой пояс

post_max_size = 16M

max_execution_time = 300

max_input_time = 300_

su postgres

psql

CREATE ROLE zabbix WITH NOSUPERUSER LOGIN PASSWORD 'zabbixpassword';

CREATE DATABASE zabbix WITH OWNER zabbix;

GRANT ALL PRIVILEGES ON DATABASE zabbix TO zabbix;

\l

\q

exit

nano /var/lib/pgsql/13/data/postgresql.conf

_listen_addresses = '*'

port = 5432_

nano /var/lib/pgsql/13/data/pg_hba.conf

local all all peer

#IPv4 local connections:
host all all 127.0.0.1/32 md5

#IPv6 local connections:
host all all ::1/128 md5

#Allow replication connections from localhost, by a user with the
#replication privilege.
local replication all peer

host zabbix zabbix 127.0.0.1/32 password

host replication all 127.0.0.1/32 md5

host replication all ::1/128 md5

systemctl restart postgresql-13

zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix

passwd postgres

nano /etc/zabbix/zabbix_server.conf

DBHost=localhost

DBName=zabbix

DBUser=zabbix

DBPassword=zabbixpassword

systemctl restart zabbix-server

systemctl enable zabbix-server

systemctl restart zabbix-agent

systemctl enable zabbix-agent

systemctl restart httpd

Nginx

nano /etc/nginx/nginx.conf

Перед конфигом надо будет поменять порт в nano /etc/httpd/httpd.conf на 82

Server {

Listen 80;

Server_name mon.jun.profi;

Location / {

Proxy_pass http://127.0.0.1:82

Proxy_set_header X-Real-IP $remote_addr;

Proxy_set_header X-Forwarded-For $reemote_addr;

Proxy_set_header Host $host;

Proxy_set_header X-Forwarded-Port $server_port; }

}