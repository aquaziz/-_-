Сначала надо обновить opnsense заходим в 
System>Firmware>status и нажимаем check for updates
1. скачиваем chrony System>Firmware>plugins пишем в поиске chrony и нажимаем +
2. заходим в services>network time>general и удаляем все сервера и сохраняем 
3. обновляем страницу и заходим в services> и выставляем все как у меня
4. ![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfMSnAPS-augE56WbeSq-7PqI0nuYWPvZ_PXFpgzSRUs_iXc_RAF3mpivlE6yKZE_x1kl5bWsfbwOwFSSUAOgTJq4cLTMSAFIXC7Yij5Qk-kJKolnM_sYx7JOR8yRZo93IjZmeXbA?key=aTEVEXtGsUTRRfL9fI--le_T)
5. **На клиенте** заходим в терминал и в файлик etc/chrony.conf
6. там мы удаляем все server и вводим server и айпи opnsense ( например у меня это: server 192.168.20.1)
7. сохраняем и выходим из файлика
8. пишем systemctl restart chronyd для перезагрузки chrony
9. проверяем командой chrony sources
10. если все работает правильно то Reach должен быть выше 1, если у вас 1 и выше значит все правильно