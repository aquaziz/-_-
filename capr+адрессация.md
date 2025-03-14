заходим сразу на cl-r3/cl-r2 делаем адрессацию
lan для cl-r3- 10.3
lan для cl2-r2-10.2
далее идем на mg-pc (ip10.11/шлюз 10.1)
заходив в Opnsense
открывает 10.2 и 10.3
10.2=
inteerfaces - virtul ips - +
mode capr 
interface lan
ip 10.1
peer 10.3
password P@sswor
group 2
adb 1
описание lan

Делаем еще один

nteerfaces - virtul ips - +
mode capr 
interface wan
ip 100.99.90.100/27
peer 10.3
password P@sswor
group 1
adb 1

ДРУГАЯ ТАЧКА
10.3=
inteerfaces - virtul ips - +
mode capr 
interface lan
ip 10.1
peer 10.2
password P@sswor
group 2
adb 1
описание lan

Делаем еще один

nteerfaces - virtul ips - +
mode capr 
interface wan
ip 100.99.90.100/28
peer 10.2
password P@sswor
group 1
adb 1