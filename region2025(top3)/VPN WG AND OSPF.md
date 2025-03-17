
***VPN***
Выполняется на fw rnd и fw krd
Отключаем firewall
settings -- advenced -- Disable firewall ( ставим галочку) на fw rnd и fw krd
![image](https://github.com/user-attachments/assets/dfdb5e2c-de67-4c73-a571-27dabe5e3635)


подключаемся ко второй машине в нашем случае к fw-krd по его ip адресу
***конфигурация на fw rnd***

**instance**
![image](https://github.com/user-attachments/assets/f5a8d6ad-780e-42b1-8d54-3c8eda5ddb1e)

**peer**
![image](https://github.com/user-attachments/assets/e474eded-5001-4c8e-b527-02264fb26ebb)

***конфигурация на fw krd***

**instance**
![image](https://github.com/user-attachments/assets/cdac6ddd-388e-4123-afad-6d22ec09ebd2)


**peer**
![image](https://github.com/user-attachments/assets/498363cf-74d7-43fb-b741-e27552c4c27a)

**у вас будут другие ключи**
**на изображение мы можем заметить - public key из instance с fw rnd мы вставили в peer fw krd.
и тоже самое в зеркальном порядке , то есть public key из instance с fw krd мы вставили в peer fw rnd**
```
fw rnd является главный, а это значит что 
endpoint - (противоположный роутер (ip - fw krd))
endport - (6543) в peer мы ставим только на RND
```
Заходим в interface - assignmets 
создаем интерфейс wg0 
затем заходив в firewall - rules - wireguard groupe и даем полное разрешение
тоже самое с wg0
включаем firewall по тому же принципу
***данные действие делаем на двух тачках (fw rnd and fw krd) ***

проверяем пинги

#OSPF
обновляем opnsense, затем скачиваем пакет frr
у нас появляется вкладка Routing - заходим 

***конфигурация FW-RND***
**general**
![image](https://github.com/user-attachments/assets/539d60d7-1cfd-4fb3-bb86-17ea8c9f4470)

**networks**
![image](https://github.com/user-attachments/assets/28742428-dfd6-45c8-a904-a991d725b4b7)
![image](https://github.com/user-attachments/assets/12536410-0a89-4662-8133-ff9847108636)

затем идем в general - enable
Затем идем в firewall - rules - wg0 (правила на fw rnd)
![image](https://github.com/user-attachments/assets/167f2183-05d5-4cff-b629-8034e981ea6f)

***такие же действия идем делать на fw rnd (правила)***
![image](https://github.com/user-attachments/assets/b99d54f3-cae7-4249-aada-e36e6cdd45fb)

![image](https://github.com/user-attachments/assets/930f057a-7fcf-43b7-b685-9d9bbe9aa749)

затем делаем еще одно правила совместно
Это все..Удачи!
