# TempPi
pi@rpi3:~ $ mkdir apps
pi@rpi3:~ $ cd apps/
pi@rpi3:~/apps $ sudo nano temperatura

Pegar lo siguiente:

#!/bin/bash
# Shell script: temp.sh
# Autor: Santiago Crespo - Modificado por Bilal Jebari
cpu=$(cat /sys/class/thermal/thermal_zone0/temp)
echo "Equipo => $(hostname)"
echo "$(date)"
echo "------------------------------"
echo "Temp.CPU => $((cpu/1000))'Cº"
echo "Temp.GPU => $(/usr/bin/vcgencmd measure_temp)"
echo "------------------------------"
echo "CPU"
echo "$(vcgencmd measure_clock arm)Hz"
echo "$(vcgencmd measure_volts core)"
echo "Mem. del Sistema $(vcgencmd get_mem arm)"
echo "Mem. de la $(vcgencmd get_mem gpu)"
echo "------------------------------"
echo "Consumo de memoria"
echo "$(egrep --color 'Mem|Cache|Swap' /proc/meminfo)"

Guardar con Ctrl+O y Salir Ctrl+X

pi@rpi3:~/apps $ sudo chmod +x temperatura
pi@rpi3:~/apps $ sudo ln -s /home/pi/apps/temperatura /usr/bin
pi@rpi3:~/apps $

pi@rpi3:~/apps $ temperatura
Equipo => rpi3
Wed 19 Jan 16:12:34 CET 2022
------------------------------
Temp.CPU => 23'Cº
Temp.GPU => temp=23.4'C
------------------------------
CPU
frequency(48)=700000000Hz
volt=1.3125V
Mem. del Sistema arm=948M
Mem. de la gpu=76M
------------------------------
Consumo de memoria
MemTotal: 944984 kB
MemFree: 501192 kB
MemAvailable: 703460 kB
Cached: 243196 kB
SwapCached: 0 kB
SwapTotal: 102396 kB
SwapFree: 102396 kB
pi@rpi3:~/apps $

 

 

 
