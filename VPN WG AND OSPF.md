
***VPN***
Выполняется на fw rnd и fw krd
Отключаем firewall
settings -- advenced -- Disable firewall ( ставим галочку) на fw rnd и fw krd
![[Pasted image 20250312011543.png]]

подключаемся ко второй машине в нашем случае к fw-krd по его ip адресу
***конфигурация на fw rnd***

**instance**
![[Pasted image 20250312011941.png]]
**peer**
![[Pasted image 20250312012022.png]]
***конфигурация на fw krd***

**instance**
![[Pasted image 20250312012251.png]]

**peer**
![[Pasted image 20250312012354.png]]
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
![[Pasted image 20250312013736.png]]

**networks**
![[Pasted image 20250312013824.png]]
![[Pasted image 20250312013839.png]]
затем идем в general - enable
Затем идем в firewall - rules - wg0 (правила на fw rnd)
![[Pasted image 20250312014119.png]]
***такие же действия идем делать на fw rnd (правила)***
![[Pasted image 20250312014320.png]]
![[Pasted image 20250312014449.png]]
затем делаем еще одно правила совместно
Это все..Удачи!