sudo dnf install git
cd /opt
sudo git clone http://github.com/zammad/zammad-docker-compose 
sudo mv zammad-docker-compose/* .
mkdir -p zammad
nano /etc/docker-compose.yml
//идем в конец файла и ищем - 
volumes:
![image](https://github.com/user-attachments/assets/c2193025-72c9-4161-b374-8ceef416c554)

делаем так же как на скрине
sudo dnf install docker-ce docker-ce-cli docker-compose
systemctl start docker
sudo docker compose up -d 
systemctl enable docker
